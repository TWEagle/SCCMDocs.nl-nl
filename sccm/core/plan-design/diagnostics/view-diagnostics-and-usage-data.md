---
title: Diagnostische gegevens bekijken | Microsoft-documenten
description: "Weergave van diagnostische en gebruiksgegevens om te bevestigen dat de System Center Configuration Manager-hiërarchie geen gevoelige informatie bevat."
ms.custom: na
ms.date: 3/27/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 594eb284-0d93-4c5d-9ae6-f0f71203682a
caps.latest.revision: 8
author: Brenduns
ms.author: brenduns
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 199096db7a23fb14db98b95e75246ed254848ab7
ms.openlocfilehash: 0932e2b2a4f3e13c35d6b7b0446083f1c233ce03
ms.contentlocale: nl-nl
ms.lasthandoff: 05/17/2017


---
# <a name="how-to-view-diagnostics-and-usage-data-for-system-center-configuration-manager"></a>Diagnostische gegevens en gebruiksgegevens voor System Center Configuration Manager weergeven

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*

U kunt diagnostische en gebruiksgegevens bekijken vanop uw System Center Configuration Manager-hiërarchie om te bevestigen dat geen gevoelige of persoonlijke informatie opgenomen is. Telemetriegegevens worden samengevat en opgeslagen in de **TEL_TelemetryResults** tabel van de sitedatabase en programmatisch bruikbaar en efficiënt is opgemaakt. De volgende opties geven een overzicht van de exacte gegevens naar Microsoft verzonden, zijn deze niet bedoeld om te worden gebruikt voor andere doeleinden, zoals data-analyse.  

Gebruik de volgende SQL-opdracht om te bekijken van de inhoud van deze tabel en de exacte gegevens dat wordt verzonden. (U kunt ook deze gegevens exporteren naar een tekstbestand.):  

-   **Selecteer \* van TEL_TelemetryResults**  

> [!NOTE]  
>  Voordat u versie 1602 installeert, de tabel met telemetriegegevens is **TelemetryResults**.  

Wanneer de service connection point in offline modus, kunt u het hulpmiddel service verbinding met de huidige diagnostics- en gebruiksgegevens exporteren naar een bestand met door komma's gescheiden waarden (CSV). De service verbinding hulpprogramma uitvoeren op de service connection point met behulp van de **-exporteren** parameter.  

##  <a name="bkmk_hashes"></a>Eenzijdige hashes  
Sommige gegevens bestaat uit tekenreeksen van willekeurige alfanumerieke tekens bevatten. Configuration Manager gebruikt het algoritme SHA-256, waarbij eenzijdige hashes worden gebruikt om ervoor te zorgen dat er mogelijk gevoelige gegevens niet worden verzameld. De algoritme blijven gegevens in een status waar ze kan nog steeds worden gebruikt voor correlatie en vergelijkingsdoeleinden. In plaats van het verzamelen van de namen van tabellen in de sitedatabase, een onomkeerbare hash vastgelegd voor elke tabelnaam. Dit zorgt ervoor dat eventuele aangepaste tabelnamen dat u hebt gemaakt of product invoegtoepassingen van andere regels niet zichtbaar zijn. We kunnen dezelfde eenzijdige hash van de SQL-tabelnamen die standaard in het product verzenden en vergelijk de resultaten van de twee query's om te bepalen van de afwijking van uw databaseschema van de standaard product gaat u als volgt. Dit resultaat wordt vervolgens gebruikt om updates te verbeteren waarvoor wijzigingen in het SQL-schema zijn vereist.  

Als de onbewerkte gegevens worden bekeken, wordt een algemene hash-waarde weergegeven in elke rij gegevens. Dit is de hiërarchie-id. Deze hash-waarde wordt gebruikt om ervoor te zorgen dat gegevens wordt gecorreleerd met dezelfde hiërarchie zonder het identificeren van de klant of bron.  

#### <a name="to-see-how-the-one-way-hash-works"></a>Om te zien hoe de eenzijdige hash werkt  

1.  Ophalen van uw hiërarchie-ID door te voeren van de volgende SQL-instructie in SQL Management Studio op de Configuration Manager-database: **selecteren [dbo]. [ fnGetHierarchyID]\(\)**  

2.  Gebruik de volgende Windows PowerShell-script voor de eenzijdige hash van de GUID die wordt opgehaald uit de database. U kunt deze vervolgens vergelijken met de id van de hiërarchie in de onbewerkte gegevens om te zien hoe deze gegevens worden verborgen.  

    ```  
    Param( [Parameter(Mandatory=$True)] [string]$value )  
      $guid = [System.Guid]::NewGuid()  
      if( [System.Guid]::TryParse($value,[ref] $guid) -eq $true ) {  
      #many of the values we hash are Guids  
      $bytesToHash = $guid.ToByteArray()  
    } else {  
      #otherwise hash as string (unicode)  
      $ue = New-Object System.Text.UnicodeEncoding  
      $bytesToHash = $ue.GetBytes($value)   
    }  
      # Load Hash Provider (https://en.wikipedia.org/wiki/SHA-2)   
    $hashAlgorithm = [System.Security.Cryptography.SHA256Cng]::Create()    
    # Hash the input   
    $hashedBytes = $hashAlgorithm.ComputeHash($bytesToHash)              
    # Base64 encode the result for transport   
    $result = [Convert]::ToBase64String($hashedBytes)    
    return $result   
    ```  

