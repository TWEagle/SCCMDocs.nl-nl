---
title: Windows service | Microsoft-documenten
description: Windows service gebruiken om te bepalen wanneer de System Center Configuration Manager-sites updates installeert.
ms.custom: na
ms.date: 1/11/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: ca4886d4-7173-46be-8dcd-1657d5b0deb9
caps.latest.revision: 4
caps.handback.revision: 0
author: Dougeby
ms.author: dougeby
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 0d0735c170820259ac8bb6706aac7cc5569a1628
ms.openlocfilehash: d06a2a955ff59fa84bb844033fe31874fc735087
ms.contentlocale: nl-nl
ms.lasthandoff: 05/17/2017


---
#  <a name="service-windows-for-site-servers"></a>Windows service voor siteservers

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*

U kunt windows service configureren op centrale beheersites en primaire sites om te bepalen wanneer in de console-updates kunnen installeren.  U kunt meerdere vensters configureren met het venster toegestaan voor het installeren van updates wordt bepaald door een combinatie van alle service-windows voor die siteserver.

Wanneer er geen venster van de service is geconfigureerd:
- **Op de bovenste site** (een centrale beheersite of zelfstandige primaire site) u aangeven wanneer de update-installatie te starten.
- **Op een onderliggende primaire site**, de update automatisch wordt geïnstalleerd nadat de installatie is voltooid op de centrale beheersite te installeren.
- **Op een secundaire site**, updates nooit automatisch wordt gestart. In plaats daarvan moet u handmatig de update-installatie van de console starten nadat de bovenliggende primaire site heeft de update is geïnstalleerd.

Wanneer een venster van de service is geconfigureerd:
- **Op de bovenste site**, u niet mogelijk om de installatie van een nieuwe update uit in de Configuration Manager-console te starten. Zelfs met een servicevenster geconfigureerd, downloadt de site automatisch updates zodat ze zijn gereed om te installeren.  
- **Op een onderliggende primaire site**, updates die zijn geïnstalleerd op een centrale beheersite wordt gedownload naar de primaire site, maar niet automatisch start. U kunt de installatie van een update gedurende een periode die wordt geblokkeerd door gebruik van een venster van de service niet handmatig starten. De update installeren op een tijdstip waarop windows service niet langer blok installatie van update automatisch wordt gestart.
- **Secundaire sites** bieden geen ondersteuning voor windows service en -updates niet automatisch installeren. Nadat de primaire bovenliggende site van een secundaire site een update is geïnstalleerd, kunt u het bijwerken van de secundaire site vanuit de console te starten.

## <a name="to-configure-a-service-window"></a>Configureren van een servicevenster

1.  In Configuration Manager-console **beheer** > **siteconfiguratie** > **Sites**, en selecteer vervolgens de siteserver waar u wilt een servicevenster configureren.  

2.  Bewerk vervolgens de waarden bij **Eigenschappen** voor de siteservers en selecteer het tabblad **Servicewindow** . Hier kunt u een of meer servicewindows voor de betreffende siteserver instellen.  

