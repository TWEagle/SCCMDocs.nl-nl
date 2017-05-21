---
title: Implementatiestatus van client controleren | Microsoft-documenten
description: Implementatiestatus van de client in System Center Configuration Manager controleren.
ms.custom: na
ms.date: 04/23/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-client
ms.tgt_pltfrm: na
ms.topic: get-started-article
ms.assetid: 20a573b3-53cb-4ed5-bae1-7542f533ed20
caps.latest.revision: 11
caps.handback.revision: 0
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 690d03d9c8c49a815bd318df549d7401a855bc5d
ms.openlocfilehash: 3d9d02d8c56aea17e563112f92173c2b56781da6
ms.contentlocale: nl-nl
ms.lasthandoff: 05/17/2017


---
# <a name="how-to-monitor-client-deployment-status-in-system-center-configuration-manager"></a>De clientimplementatiestatus controleren in System Center Configuration Manager

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*

Het kost tijd om clients te implementeren op uw site en sommige installaties lukken de eerste keer niet direct. De System Center Configuration Manager-console biedt een manier gaten te houden op implementaties op de client binnen een verzameling door de status van de client-implementatie in realtime reporting.  

> [!NOTE]  
>  De beste en meest betrouwbare manier om te controleren van clientimplementatie is met de Configuration Manager-console (zoals wordt beschreven in dit artikel). De sectie **Clientstatus** van de werkruimte **Bewaking** in de console bevat nauwkeurige en realtime informatie over de clientimplementatiestatus. U kunt clientimplementaties ook met andere hulpprogramma’s bewaken, zoals Server Manager in Windows Server of System Center Operations Manager; mogelijk ontvangt u dan ook waarschuwingen over normale clientinstallatieactiviteiten. Omdat het clientinstallatieprogramma (CCMSetup.exe) anders wordt uitgevoerd in verschillende omgevingen, kan het zijn dat er onrechtmatig waarschuwingen worden gegeven die geen goed beeld vormen van de daadwerkelijke status van clientimplementaties.  

 In de werkruimte **Bewaking** van de console kunt u de volgende statussen bewaken van clientimplementaties die plaatsvinden binnen een verzameling die u opgeeft:  

-   Compliant  

-   Wordt uitgevoerd  

-   Niet compatibel  

-   Mislukt  

-   Onbekend  

 Configuration Manager rapporteert over implementaties van productieclients of pre-productieclients. De Configuration Manager-console biedt ook een overzicht van clientimplementaties die gedurende een bepaalde periode zijn mislukt zodat u kunt bepalen of de acties die u onderneemt om problemen met implementaties op te lossen, het aantal geslaagde implementaties na verloop van tijd verbetert.  

## <a name="to-monitor-client-deployments"></a>Clientimplementaties bewaken  

-   Klik in de Configuration Manager-console op **bewaking** > **clientstatus**.  

-   Klik op **Productieclientimplementatie** of **Pre-productieclientimplementatie**, afhankelijk van de versie van de client die u wilt bewaken.  

-   Bekijk de overzichten van de clientimplementatiestatussen en van het aantal mislukte clientimplementaties.  

-   Als u het bereik van het rapport wijzigen wilt, klikt u op **bladeren...**  en kies een andere verzameling.  

 Zie voor meer informatie over implementaties van pre-productieclient [clientupgrades testen in een pre-productieverzameling in System Center Configuration Manager](../../../core/clients/manage/upgrade/test-client-upgrades.md).

 > [!NOTE]
 > Kan de status van de implementatie op computers als host voor sitesysteemrollen in een pre-productieverzameling gerapporteerd als **niet compatibel zijn** zelfs wanneer de client met succes is geïmplementeerd. Wanneer u promoveert naar productie, wordt de status van de implementatie correct gerapporteerd.   

 Zie [Clients controleren in System Center Configuration Manager](../../../core/clients/manage/monitor-clients.md) voor informatie over het bewaken van de status van geïmplementeerde clients.  

 U kunt de Configuration Manager-rapporten gebruiken om na te gaan meer informatie over de status van clients in uw site. Zie [Rapportage in System Center Configuration Manager](../../../core/servers/manage/reporting.md) voor meer informatie over het uitvoeren van rapporten.  

