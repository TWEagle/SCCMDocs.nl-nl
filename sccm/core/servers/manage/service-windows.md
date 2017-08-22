---
title: Windows-service | Microsoft Docs
description: Gebruik servicewindows om te bepalen wanneer de updates voor het installeren van System Center Configuration Manager-sites.
ms.custom: na
ms.date: 1/11/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: ca4886d4-7173-46be-8dcd-1657d5b0deb9
caps.latest.revision: "4"
caps.handback.revision: "0"
author: Dougeby
ms.author: dougeby
manager: angrobe
ms.openlocfilehash: d06a2a955ff59fa84bb844033fe31874fc735087
ms.sourcegitcommit: 51fc48fb023f1e8d995c6c4eacfda7dbec4d0b2f
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 08/07/2017
---
#  <a name="service-windows-for-site-servers"></a>Servicewindows voor siteservers

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*

U kunt servicewindows configureren op centrale beheersites en primaire sites om te bepalen wanneer updates in de console kunnen installeren.  U kunt meerdere vensters configureren met het venster dat is toegestaan voor het installeren van updates wordt bepaald door een combinatie van alle servicewindows voor die siteserver.

Wanneer er geen venster van de service is geconfigureerd:
- **Op de bovenste site** (een centrale beheersite of zelfstandige primaire site) u kiezen wanneer de update-installatie te starten.
- **Op een onderliggende primaire site**, de update wordt automatisch geïnstalleerd nadat de update is voltooid op de centrale beheersite te installeren.
- **Op een secundaire site**, updates nooit automatisch wordt gestart. In plaats daarvan moet u handmatig de update-installatie van de console starten nadat de bovenliggende primaire site de update is geïnstalleerd.

Wanneer een venster van de service is geconfigureerd:
- **Op de bovenste site**, u zich niet begint met de installatie van een nieuwe update uit in de Configuration Manager-console. Zelfs met een servicevenster geconfigureerd, downloadt de site automatisch updates zodat ze gereed om te installeren.  
- **Op een onderliggende primaire site**, updates die zijn geïnstalleerd op een centrale beheersite zal downloaden naar de primaire site, maar niet automatisch starten. U kunt de installatie van een update gedurende een periode die wordt geblokkeerd door gebruik van een venster van de service kan niet handmatig starten. De update installeren op een tijdstip wanneer de installatie voor het bijwerken van servicewindows niet langer blok, automatisch wordt gestart.
- **Secundaire sites** bieden geen ondersteuning voor servicewindows en -updates niet automatisch installeren. Nadat de primaire bovenliggende site van een secundaire site een update is geïnstalleerd, kunt u het bijwerken van de secundaire site vanuit de console starten.

## <a name="to-configure-a-service-window"></a>Een servicewindow configureren

1.  In Configuration Manager-console **beheer** > **siteconfiguratie** > **Sites**, en selecteer vervolgens de siteserver waar u een servicewindow configureren.  

2.  Bewerk vervolgens de waarden bij **Eigenschappen** voor de siteservers en selecteer het tabblad **Servicewindow** . Hier kunt u een of meer servicewindows voor de betreffende siteserver instellen.  
