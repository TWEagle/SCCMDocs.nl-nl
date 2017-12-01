---
title: De diagnostics-gegevens weergeven
titleSuffix: Configuration Manager
description: "Diagnostische gegevens en gebruiksgegevens om te bevestigen dat de System Center Configuration Manager-hiërarchie geen gevoelige informatie bevat weergeven."
ms.custom: na
ms.date: 3/27/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 594eb284-0d93-4c5d-9ae6-f0f71203682a
caps.latest.revision: "8"
author: aaroncz
ms.author: aaroncz
manager: angrobe
ms.openlocfilehash: fb6e5d1e19dbb86d8c2106e0246986734f598853
ms.sourcegitcommit: 7fe45ff75f05f7cc03ad021db8119791abe18049
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/01/2017
---
# <a name="how-to-view-diagnostics-and-usage-data-for-system-center-configuration-manager"></a>Diagnostische gegevens en gebruiksgegevens voor System Center Configuration Manager weergeven

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*

U kunt diagnostische gegevens en gebruiksgegevens weergeven vanuit uw System Center Configuration Manager-hiërarchie om te bevestigen dat er geen gevoelige of persoonlijke informatie opgenomen is. Telemetriegegevens worden samengevat en opgeslagen de **TEL_TelemetryResults** tabel van de sitedatabase en is zodanig ingedeeld dat deze programmatisch bruikbaar en efficiënt. De volgende opties een overzicht geven van de exacte gegevens naar Microsoft verzonden, zijn ze niet bedoeld om te worden gebruikt voor andere doeleinden, zoals gegevensanalyse.  

Gebruik de volgende SQL-opdracht om te bekijken van de inhoud van deze tabel en de exacte gegevens die worden verzonden. (U kunt ook deze gegevens exporteren naar een tekstbestand.):  

-   **Selecteer \* van TEL_TelemetryResults**  

> [!NOTE]  
>  Voordat u versie 1602 installeert, is het in de tabel met telemetriegegevens **TelemetryResults**.  

Wanneer het service connection point in de offlinemodus bevindt, kunt u het hulpprogramma voor serviceverbindingen de huidige diagnostische gegevens en gebruiksgegevens exporteren naar een bestand met door komma's gescheiden waarden (CSV). Het hulpprogramma voor serviceverbindingen voeren op het serviceverbindingspunt wordt gehost door de **-exporteren** parameter.  

##  <a name="bkmk_hashes"></a>One-Way hashes  
Sommige gegevens bestaat uit tekenreeksen van willekeurige alfanumerieke tekens. Configuration Manager gebruikt de SHA-256-algoritme, die one-way hashes gebruikt om ervoor te zorgen dat er geen potentieel gevoelige gegevens verzamelen. Het algoritme blijven gegevens in een staat waarin deze nog kunnen worden gebruikt voor correlatie- en vergelijkingsdoeleinden. In plaats van het verzamelen van de namen van tabellen in de sitedatabase, een one-way hash vastgelegd voor elke tabelnaam. Dit zorgt ervoor dat eventuele aangepaste tabelnamen dat u hebt gemaakt of product invoegtoepassingen van andere regels niet zichtbaar zijn. We kunt vervolgens dezelfde one-way hash van de SQL-tabelnamen die standaard in het product verzenden en vergelijk de resultaten van de twee query's om te bepalen van de afwijking van uw databaseschema vanuit de standaardwaarde van het product doen. Dit resultaat wordt vervolgens gebruikt om updates te verbeteren waarvoor wijzigingen in het SQL-schema zijn vereist.  

Als de onbewerkte gegevens worden bekeken, wordt een algemene hash-waarde weergegeven in elke rij gegevens. Dit is de hiërarchie-id. Deze hash-waarde wordt gebruikt om ervoor te zorgen dat gegevens worden gecorreleerd met dezelfde hiërarchie zonder te identificeren van de klant of de bron.  

#### <a name="to-see-how-the-one-way-hash-works"></a>Om te zien hoe een one-way hash werkt  

1.  Uw hiërarchie-ID ophalen door de volgende SQL-instructie in SQL Management Studio op de Configuration Manager-database: **selecteren [dbo]. [ fnGetHierarchyID]\(\)**  

2.  Gebruik de volgende Windows PowerShell-script voor de one-way hash van de GUID die wordt opgehaald uit de database. U kunt deze vervolgens vergelijken met de id van de hiërarchie in de onbewerkte gegevens om te zien hoe deze gegevens worden verborgen.  

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
