---
title: IOS-toepassingen maken | Microsoft-documenten
description: Zie welke overwegingen die u moet ondernemen in rekening wanneer u toepassingen maken en voor iOS-apparaten implementeren.
ms.custom: na
ms.date: 03/05/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-hybrid
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: ff633013-5313-4cd3-949c-56d45e777280
caps.latest.revision: 10
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 6424fb07802b62820b4dc78a58ab30d3b956abef
ms.openlocfilehash: 349fcf335e7faddbcbd2ffe0ece7e711465f28df
ms.contentlocale: nl-nl
ms.lasthandoff: 05/17/2017


---
# <a name="create-ios-applications-with-system-center-configuration-manager"></a>IOS-toepassingen maken met System Center Configuration Manager

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*

Een System Center Configuration Manager-toepassing heeft een of meer implementatietypen die deel uitmaken van de installatiebestanden en informatie die nodig zijn voor het implementeren van software voor een apparaat. Een implementatietype bevat ook regels die specificeren waar en hoe de software wordt geïmplementeerd.  

 U kunt toepassingen maken met behulp van de volgende methoden:  

-   De implementatie van toepassingen en -typen automatisch maken via het lezen van de installatiebestanden van de toepassing.  

-   U kunt de toepassing handmatig maken en deze op een later tijdstip aan implementatietypen toevoegen.  

-   Een toepassing importeren uit een bestand.  

Zie [Start de wizard toepassing](../../apps/deploy-use/create-applications.md#start-the-create-application-wizard) voor de stappen die nodig zijn voor create Configuration Manager-toepassingen en implementatietypen. Houd ook rekening met het volgende in gedachten wanneer u toepassingen maken en voor iOS-apparaten implementeren.  

## <a name="general-considerations"></a>Algemene overwegingen  
 Configuration Manager ondersteunt de implementatie van de volgende typen app:  

|Apparaattype|Ondersteunde bestanden|  
|-----------------|---------------------|  
|iOS|*.ipa<br /><br /> In System Center Configuration Manager niet hoeft op te geven van een bestand eigenschappenlijst (.plist) bij het importeren van een iOS-app.|  

 De volgende implementatieacties worden ondersteund:  

|Apparaattype|Ondersteunde bewerkingen|  
|-----------------|-----------------------|  
|iOS|**Beschikbare**, **vereist**. De gebruiker moet toestemming geven om te installeren en verwijderen.

> [!IMPORTANT]  
>  Op dit moment kunnen eindgebruikers geen zakelijke apps installeren vanuit de Intune-bedrijfsportal-app voor iOS. Dit komt doordat er gelden beperkingen die worden geplaatst op apps die zijn gepubliceerd in de iOS App Store (Zie Beoordelingsrichtlijnen voor App Store, sectie 2). Gebruikers kunnen zakelijke apps (zoals beheerde App Store-apps en bedrijfsapp-pakketten) installeren door op hun apparaat naar de Intune-webportal te gaan (portal.manage.microsoft.com). Zie voor meer informatie over de mogelijkheden van mobiel beheer die zijn ingeschakeld door de Intune-bedrijfsportal-app [ingeschreven apparaatbeheermogelijkheden voor Computerbeheer in Microsoft Intune](https://technet.microsoft.com/library/dn600287.aspx).  

