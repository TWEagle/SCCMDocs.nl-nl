---
title: Privacyverklaring voor System Center Configuration Manager - Configuratiebeheer cmdletlLibrary | Microsoft-documenten
description: Meer informatie over hoe Microsoft verzamelt en maakt gebruik van gegevens met betrekking tot de cmdlet-bibliotheek van System Center Configuration Manager.
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
caps.latest.revision: 5
caps.handback.revision: 0
author: Brenduns
ms.author: brenduns
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 3d6799ad46e0fe69333aba0662f18c9153c17bda
ms.openlocfilehash: 3936075555cc0bb370ea6e42c7e720b864d565f7
ms.contentlocale: nl-nl
ms.lasthandoff: 05/17/2017


---
# <a name="system-center-configuration-manager-privacy-statement---configuration-manager-cmdlet-library"></a>Privacyverklaring voor System Center Configuration Manager - bibliotheek van Configuration Manager-cmdlet

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*

Deze privacyverklaring is van toepassing op de functies van de Configuration Manager Cmdlet Library.  

## <a name="usage-data"></a>Gebruiksgegevens  
 **Wat doet deze functie:**   
De cmdlet-bibliotheek van System Center Configuration Manager kunt u een Configuration Manager-hiërarchie beheren met behulp van Windows PowerShell-cmdlets en scripts. De cmdlet-bibliotheek verzamelt informatie over hoe u de cmdlets in de bibliotheek gebruiken om trends en gebruikspatronen identificeren. De cmdlet-bibliotheek verzamelt tevens informatie over de soorten en aantallen fouten die optreden wanneer u de cmdlets.  

 **Verzamelde, verwerkte of verzonden gegevens:**   
De verzamelde gebruiksgegevens omvatten starten, stoppen en beëindigen van cmdlets, afgeschaft-cmdlets en activiteit metrische gegevens voor Systems Management Server (SMS) provider bewerkingen die zijn gekoppeld aan de cmdlets worden uitgevoerd. Deze gegevens zijn niet persoonlijk identificeerbaar.  Gegevens van de verzamelde fout bevat fouten die cmdlets retourneren en foutdetails voor uitzonderingsfouten. Sommige details foutenrapporten kunnen onbedoeld afzonderlijke id's, zoals een serienummer voor een apparaat dat is verbonden met uw computer bevatten. De cmdlet-bibliotheek worden gefilterd en anonymizes informatie in de foutrapporten verwijderen van afzonderlijke id's voor verzending naar Microsoft.  

 **Gebruik van informatie:**   
We gebruiken deze gegevens voor het verbeteren van de kwaliteit, beveiliging en integriteit van de producten en services die wij bieden.  

 **Keuze/controle:**   
Deze gegevens gebruik functie is standaard ingeschakeld. De cmdlet-bibliotheek van System Center Configuration Manager heeft twee registersleutels waarmee deze functionaliteit.  

 Als u deze functie volledig wilt uitschakelen, moet u deze twee registersleutelwaarden instellen, één voor elk van de ETW-providers (Event Tracing for Windows):  

-   HKLM\Software\Microsoft\ConfigMgr10\PowerShell\Microsoft.ConfigurationManagement.PowerShell.Provider:CeipLevel=0 (gebruiksgegevens voor de schijfprovider uitschakelen)  

-   HKLM\Software\Microsoft\ConfigMgr10\PowerShell\Microsoft.ConfigurationManagement.PowerShell.Cmdlets:CeipLevel=0 (gebruiksgegevens voor de cmdlets uitschakelen)  

 Wijzigingen in de instellingen voor gebruiksgegevens zijn specifiek voor de computer waarop ze worden ingesteld.  

 Zie voor meer informatie over het configureren van gebruiksgegevens (verzameling), de [Cmdlet-bibliotheek van System Center Configuration Manager-documentatie](https://technet.microsoft.com/en-us/library/dn958404.aspx).   

