---
title: Privacyverklaring voor Configuration Manager cmdletlLibrary
description: Meer informatie over hoe Microsoft verzamelt en maakt gebruik van gegevens met betrekking tot de System Center Configuration Manager cmdlet library.
ms.custom: na
ms.date: 1/3/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: bec00fb4-1ac0-4e49-b330-0871b3722459
caps.latest.revision: ''
caps.handback.revision: ''
author: aczechowski
ms.author: aaroncz
manager: angrobe
ms.openlocfilehash: 0ed94de1fc4782539baed0f1589cebf69c0f2219
ms.sourcegitcommit: a19e12d5c3198764901d44f4df7c60eb542e765f
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 03/28/2018
---
# <a name="system-center-configuration-manager-privacy-statement---configuration-manager-cmdlet-library"></a>Privacyverklaring voor System Center Configuration Manager - Configuration Manager cmdlet library

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*

Deze privacyverklaring is van toepassing op de functies van de Configuration Manager Cmdlet Library.  

## <a name="usage-data"></a>Gebruiksgegevens  

#### <a name="what-this-feature-does"></a>Wat doet deze functie   

De System Center Configuration Manager cmdlet library kunt u een Configuration Manager-hiërarchie beheren met behulp van Windows PowerShell-cmdlets en scripts. De cmdlet-bibliotheek verzamelt informatie over hoe u de cmdlets in de bibliotheek gebruiken om trends en gebruikspatronen te identificeren. De cmdlet-bibliotheek verzamelt ook de typen en het aantal fouten dat wordt weergegeven wanneer u de cmdlets gebruiken.  

#### <a name="information-collected-processed-or-transmitted"></a>Verzamelde, verwerkte of verzonden informatie
   
De verzamelde gebruiksgegevens omvat starten, stoppen en beëindigen van cmdlets, uitvoeren van afgeschafte cmdlets en metrische gegevens van activiteiten voor bewerkingen van SMS-Provider die gerelateerd zijn aan de cmdlets. Deze informatie niet persoonlijk identificeerbaar. Informatie verzameld over de fout bevat fouten die cmdlets retourneren en foutdetails voor uitzonderingsfouten. Sommige rapporten met foutdetails mogelijk per ongeluk individuele id's, zoals een serienummer voor een apparaat dat is verbonden met uw computer bevatten. De cmdlet-bibliotheek gefilterd en anoniem gemaakt informatie die in de foutrapporten individuele id's voor verzending naar Microsoft te verwijderen.  

#### <a name="use-of-information"></a>Gebruik van informatie
   
Microsoft gebruikt deze informatie voor het verbeteren van de kwaliteit, beveiliging en integriteit van de producten en services die ze bieden.  

#### <a name="choicecontrol"></a>Keuze/controle   

Deze functie gebruik gegevens is standaard ingeschakeld. De System Center Configuration Manager cmdlet library bevat twee registersleutels waarmee deze functionaliteit.  

 Om volledig opt-out, deze twee registersleutelwaarden instellen Ze zijn voor elk van de providers Event Tracing voor Windows (ETW):  

-   HKLM\Software\Microsoft\ConfigMgr10\PowerShell\Microsoft.ConfigurationManagement.PowerShell.provider:CeipLevel=0 (kiest buiten gebruiksgegevens voor de schijfprovider)  

-   HKLM\Software\Microsoft\ConfigMgr10\PowerShell\Microsoft.ConfigurationManagement.PowerShell.cmdlets:CeipLevel=0 (kiest buiten gebruiksgegevens voor de cmdlets)  

 Wijzigingen in de instellingen voor informatie over het gebruik van gegevens zijn specifiek voor de computer waar ze zijn gemaakt.  


## <a name="next-steps"></a>Volgende stappen

[Documentatie voor System Center Configuration Manager Cmdlet Library](https://docs.microsoft.com/powershell/sccm/configurationmanager/).   
