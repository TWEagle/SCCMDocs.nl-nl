---
title: IOS-toepassingen maken | Microsoft Docs
description: Zie welke overwegingen u moet rekening account wanneer u maken en implementeren van toepassingen voor iOS-apparaten.
ms.custom: na
ms.date: 03/05/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: configmgr-hybrid
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: ff633013-5313-4cd3-949c-56d45e777280
caps.latest.revision: "10"
author: mattbriggs
ms.author: mabrigg
manager: angrobe
ms.openlocfilehash: af3479a75a1024bdcf9ce6c354c073ee5fb837b6
ms.sourcegitcommit: f6a428a8db7145affa388f59e0ad880bdfcf17b5
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 09/14/2017
---
# <a name="create-ios-applications-with-system-center-configuration-manager"></a>IOS-toepassingen maken met System Center Configuration Manager

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*

Een System Center Configuration Manager-toepassing heeft een of meer implementatietypen waaruit de installatiebestanden en informatie die nodig zijn voor het implementeren van software op een apparaat. Een implementatietype heeft ook regels die specificeren hoe en wanneer de software wordt geïmplementeerd.  

 U kunt toepassingen maken met behulp van de volgende methoden:  

-   De toepassing en implementatietype-typen automatisch maken door te lezen van de installatiebestanden van de toepassing.  

-   U kunt de toepassing handmatig maken en deze op een later tijdstip aan implementatietypen toevoegen.  

-   Een toepassing importeren uit een bestand.  

Zie [Start de wizard toepassing maken](../../apps/deploy-use/create-applications.md#start-the-create-application-wizard) voor de stappen die nodig zijn voor de Configuration Manager-toepassingen maken en implementatietypen. Houd er ook de volgende aandachtspunten in rekening wanneer u maken en implementeren van toepassingen voor iOS-apparaten.  

## <a name="general-considerations"></a>Algemene overwegingen  
 Configuration Manager ondersteunt de implementatie van de volgende typen Apps:  

|Apparaattype|Ondersteunde bestanden|  
|-----------------|---------------------|  
|iOS|*.ipa<br /><br /> In System Center Configuration Manager, u niet wilt opgeven van een eigenschappenlijstbestand (.plist) bij het importeren van een iOS-app.|  

 De volgende implementatieacties worden ondersteund:  

|Apparaattype|Ondersteunde bewerkingen|  
|-----------------|-----------------------|  
|iOS|**Beschikbare**, **vereist**. De gebruiker moet toestemming geven om te installeren en verwijderen van zowel.

> [!IMPORTANT]  
>  Op dit moment kunnen eindgebruikers geen zakelijke apps installeren vanuit de Intune-bedrijfsportal-app voor iOS. Dit komt doordat er gelden beperkingen die worden geplaatst op apps die zijn gepubliceerd in de iOS App Store (Zie Beoordelingsrichtlijnen voor App Store, sectie 2). Gebruikers kunnen zakelijke apps (zoals beheerde App Store-apps en bedrijfsapp-pakketten) installeren door op hun apparaat naar de Intune-webportal te gaan (portal.manage.microsoft.com). Zie voor meer informatie over de mogelijkheden van mobiel beheer die zijn ingeschakeld door de Intune-bedrijfsportal-app, [beheermogelijkheden voor apparaten in Microsoft Intune is ingeschreven](https://technet.microsoft.com/library/dn600287.aspx).  
