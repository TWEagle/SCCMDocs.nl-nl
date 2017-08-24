---
title: Privacyverklaring voor System Center Configuration Manager - Configuratiebeheer cmdletlLibrary | Microsoft Docs
description: Meer informatie over hoe Microsoft verzamelt en maakt gebruik van gegevens met betrekking tot de System Center Configuration Manager cmdlet library.
ms.custom: na
ms.date: 1/3/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: bec00fb4-1ac0-4e49-b330-0871b3722459
caps.latest.revision: "5"
caps.handback.revision: "0"
author: Brenduns
ms.author: brenduns
manager: angrobe
ms.openlocfilehash: 3936075555cc0bb370ea6e42c7e720b864d565f7
ms.sourcegitcommit: 51fc48fb023f1e8d995c6c4eacfda7dbec4d0b2f
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 08/07/2017
---
# <a name="system-center-configuration-manager-privacy-statement---configuration-manager-cmdlet-library"></a>Privacyverklaring voor System Center Configuration Manager - Configuration Manager cmdlet library

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*

Deze privacyverklaring is van toepassing op de functies van de Configuration Manager Cmdlet Library.  

## <a name="usage-data"></a>Gebruiksgegevens  
 **Wat doet deze functie:**   
De System Center Configuration Manager cmdlet library kunt u een Configuration Manager-hiërarchie beheren met behulp van Windows PowerShell-cmdlets en scripts. De cmdlet-bibliotheek verzamelt informatie over hoe u de cmdlets in de bibliotheek gebruiken om trends en gebruikspatronen te identificeren. De cmdlet-bibliotheek verzamelt ook de typen en aantallen fouten die optreden wanneer u de cmdlets gebruiken.  

 **Informatie verzameld, verwerkt of verzonden:**   
De verzamelde gebruiksgegevens omvat starten, stoppen en beëindigen van cmdlets, uitvoeren van afgeschafte cmdlets en metrische gegevens van activiteiten voor bewerkingen van de Systems Management Server (SMS)-provider die gerelateerd zijn aan de cmdlets. Deze gegevens zijn niet persoonlijk identificeerbaar.  Informatie verzameld over de fout bevat fouten die cmdlets retourneren en foutdetails voor uitzonderingsfouten. Sommige rapporten met foutdetails bevatten mogelijk per ongeluk individuele id's, zoals een serienummer voor een apparaat dat is verbonden met uw computer. De cmdlet-bibliotheek gefilterd en anoniem gemaakt informatie die in de foutrapporten individuele id's voor verzending naar Microsoft te verwijderen.  

 **Gebruik van informatie:**   
We gebruiken deze informatie voor het verbeteren van de kwaliteit, beveiliging en integriteit van de producten en services die wij bieden.  

 **Keuze/controle:**   
Deze functie gebruik gegevens is standaard ingeschakeld. De System Center Configuration Manager cmdlet library bevat twee registersleutels waarmee deze functionaliteit.  

 Als u deze functie volledig wilt uitschakelen, moet u deze twee registersleutelwaarden instellen, één voor elk van de ETW-providers (Event Tracing for Windows):  

-   HKLM\Software\Microsoft\ConfigMgr10\PowerShell\Microsoft.ConfigurationManagement.PowerShell.Provider:CeipLevel=0 (gebruiksgegevens voor de schijfprovider uitschakelen)  

-   HKLM\Software\Microsoft\ConfigMgr10\PowerShell\Microsoft.ConfigurationManagement.PowerShell.Cmdlets:CeipLevel=0 (gebruiksgegevens voor de cmdlets uitschakelen)  

 Wijzigingen in de instellingen voor gebruiksgegevens zijn specifiek voor de computer waarop ze worden ingesteld.  

 Zie voor meer informatie over het configureren van gebruiksgegevens (verzameling) de [documentatie voor System Center Configuration Manager Cmdlet Library](https://technet.microsoft.com/en-us/library/dn958404.aspx).   
