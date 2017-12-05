---
title: Installatiescenario 's
titleSuffix: Configuration Manager
description: "Meer informatie over technieken voor het installeren van een nieuwe Configuration Manager-hiërarchie wanneer u bijwerken of bijwerken van een site."
ms.custom: na
ms.date: 10/06/2016
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 35586a85-4af9-4c8b-925a-0e32dc8b7346
caps.latest.revision: "6"
author: mestew
ms.author: mstewart
manager: angrobe
ms.openlocfilehash: c9fc7c502acca95ea19b6d7ba55f2aee79a929cd
ms.sourcegitcommit: daa080cf220835f157a23e8c8e2bd2781b869bb7
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/04/2017
---
# <a name="scenarios-to-streamline-your-installation-of-system-center-configuration-manager"></a>Scenario's om de installatie van System Center Configuration Manager te stroomlijnen

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*

Met de release van Updateversies voor de huidige vertakking van System Center Configuration Manager zijn er nieuwe scenario's voor het stroomlijnen van de installatie van een nieuwe hiërarchie naar een updateversie (zoals update 1610) en voor upgrade van Microsoft System Center 2012 Configuration Manager.

Ondersteunde scenario's zijn onder meer:  

**Installeren van een nieuwe System Center Configuration Manager huidige vertakking hiërarchie** die een updateversie wordt uitgevoerd.  

-   Installeer alleen de bovenste site en installeer vervolgens onmiddellijk een update voor het maken van die site met de updateversie die u wilt gebruiken. Vervolgens kunt u aanvullende sites direct naar deze updateversie installeren.  
-   In dit scenario moet u het proces van aanvullende sites naar een basisniveau installeert en ze vervolgens bij te werken naar de updateversie die u wilt gebruiken overslaan.  
-   In dit scenario moet u het proces van clients naar een basislijnversie installeren en vervolgens opnieuw wanneer u naar een nieuwere versie bijwerkt overslaan.  

**Upgrade van een Microsoft System Center 2012 Configuration Manager** infrastructuur naar een updateversie van System Center Configuration Manager.  

-   Handmatig upgrade uw centrale beheersite en elke primaire site naar een basislijnversie (zoals versie 1606) voordat u installeert een updateversie (zoals versie 1610).  
-   Geen upgrade van secundaire sites van Microsoft System Center 2012 Configuration Manager totdat de updateversie die u wilt gebruiken voor uw primaire sites uitgevoerd.  
-   Geen clients upgraden van Microsoft System Center 2012 Configuration Manager totdat de updateversie die u wilt gebruiken voor uw primaire sites uitgevoerd.  

## <a name="scenario-install-a-new-hierarchy-to-an-update-version"></a>Scenario: Een nieuwe hiërarchie naar een updateversie installeren  
In dit voorbeeldscenario installeert u de eerste site van een hiërarchie met behulp van een basislijnversie van System Center Configuration Manager, zoals versie 1610. Vervolgens installeert u de update 1610 voordat u extra sites of clients implementeert.  

-   Omdat u van plan bent een updateversie (zoals versie 1610) gebruiken en niet op een basislijnversie (zoals versie 1606), moet u geen aanvullende sites installeren en deze bijwerken. Dit geldt ook voor clients.  
-   Geen secundaire sites installeren met versie 1606 en ze vervolgens een upgrade naar versie 1610. In plaats daarvan secundaire sites installeren nadat u uw primaire sites versie 1610 wordt uitgevoerd.  

Volg deze reeks:  

1.  **Installeren van een site op het hoogste niveau voor de nieuwe hiërarchie** met behulp van de basislijnmedia.  

    -   U kunt basislijnmedia alleen de eerste site van een nieuwe hiërarchie installeren.  
    -   Installeer bijvoorbeeld een site op het hoogste niveau met behulp van de basislijnversie van 1606. Zie voor meer informatie [gebruik van de installatiewizard om sites te installeren](/sccm/core/servers/deploy/install/use-the-setup-wizard-to-install-sites).  

    Na deze stap wordt op de site op het hoogste niveau versie 1606 uitgevoerd.  

2.  **In de console-updates gebruiken voor het bijwerken van uw site op het hoogste niveau naar een nieuwere versie.**  

    -   Voordat u onderliggende sites of clients installeert, moet u uw site op het hoogste niveau bijwerken naar de updateversie die u wilt gebruiken.  
    -   U kunt bijvoorbeeld uw hoogste niveau waarop versie 1606 naar versie 1610 bijwerken. Zie [Updates voor System Center Configuration Manager](../../../../core/servers/manage/updates.md) voor meer informatie.  

    Na deze stap wordt op de site op het hoogste niveau versie 1610 uitgevoerd.  

3.  **Installeer nieuwe onderliggende primaire sites onder een centrale beheersite.**  

    -   Installeer nieuwe onderliggende primaire sites met behulp van de installatiemedia in de map CD.Latest op de server van de centrale beheersite. Zie [De map CD.Latest voor System Center Configuration Manager](../../../../core/servers/manage/the-cd.latest-folder.md) voor meer informatie.  

      Deze bronmedia zijn vereist om te zorgen dat de versie van de nieuwe onderliggende primaire sites overeenkomt met de versie van de centrale beheersite.  

    Na deze stap is voor uw nieuwe onderliggende primaire sites versie 1610 uitvoeren.  

4.  **Gebruik de optie in de console om nieuwe secundaire sites te installeren op elke primaire site.**  

    -   Omdat u geen secundaire sites hebt geïnstalleerd terwijl primaire sites versie 1606 waren, hoeft u niet upgraden van secundaire sites.  
    -   In plaats daarvan installeert u nieuwe secundaire sites waarop versie 1610 wordt uitgevoerd. Zie voor meer informatie [Een secundaire site installeren](/sccm/core/servers/deploy/install/use-the-setup-wizard-to-install-sites#bkmk_secondary) in het onderwerp [De installatiewizard gebruiken om sites te installeren](/sccm/core/servers/deploy/install/use-the-setup-wizard-to-install-sites).  

    Na deze stap worden nieuwe secundaire sites geïnstalleerd en 1610 versie wordt uitgevoerd.  

5.  **Installeer nieuwe clients op de primaire site.**  

    -   Omdat u geen clients hebt geïnstalleerd terwijl primaire sites versie 1606 waren, hoeft u geen upgrade van clients vanaf versie 1606 naar versie 1610.  
    -   In plaats daarvan installeert u nieuwe clients waarop versie 1610 wordt uitgevoerd. Zie voor meer informatie [in System Center Configuration Manager-clients implementeren](../../../clients/deploy/deploy-clients-to-windows-computers.md).  

    Na deze stap worden nieuwe clients geïnstalleerd waarop versie 1610 wordt uitgevoerd.  

## <a name="scenario-upgrade-system-center-2012-configuration-manager-to-an-update-version-of-system-center-configuration-manager-current-branch"></a>Scenario: Upgrade van System Center 2012 Configuration Manager naar een updateversie van System Center Configuration Manager, huidige vertakking  
In dit voorbeeldscenario uw Microsoft System Center 2012 Configuration Manager-infrastructuur te upgraden naar een updateversie van System Center Configuration Manager, zoals versie 1610.  

-   De centrale beheersite en elke primaire site moeten een upgrade uitvoeren naar de basislijnversie 1606 voordat u de update voor versie 1610 installeert.  
-   Secundaire sites en clients geen upgrade uitvoeren of versie 1606 installeert. In plaats daarvan verplaatsen ze rechtstreeks vanuit de Microsoft System Center 2012 Configuration Manager naar System Center Configuration Manager versie 1610.  

Volg deze reeks:  

1.  **Upgrade van uw site op het hoogste Microsoft System Center 2012 Configuration Manager-site** naar een basislijnversie van de huidige vertakking met behulp van bronmedia voor System Center Configuration Manager (zoals versie 1606). Zie voor meer informatie [upgraden naar System Center Configuration Manager](../../../../core/servers/deploy/install/upgrade-to-configuration-manager.md).  

    -   Zoals traditionele upgradescenario's moet u altijd eerst een upgrade uitvoert het hoogste niveau van een hiërarchie en werk vervolgens de onderliggende sites.  

    Na deze stap wordt op de site op het hoogste niveau versie 1606 uitgevoerd.  

2.  **Voer een upgrade uit van alle onderliggende primaire sites in uw hiërarchie** naar dezelfde basislijnversie.  

    -   Wanneer u een van Microsoft System Center 2012 Configuration Manager upgrade, moet u handmatig elke primaire site upgraden naar een basislijnversie van de huidige vertakking.  
    -   U wordt geen upgrade van secundaire sites op dit moment.  

    Na deze stap wordt elke primaire site versie 1606 wordt uitgevoerd.  

3.  **Stel de onderhoudsvensters op onderliggende primaire sites.** Na de upgrade van alle primaire sites naar de basislijnversie plan voor het configureren van onderhoudsvensters om te bepalen wanneer infrastructuurupdates worden geïnstalleerd in deze sites. Zie voor meer informatie [het gebruik van onderhoudsvensters in System Center Configuration Manager](../../../../core/clients/manage/collections/use-maintenance-windows.md).  (Onderhoudsvensters worden genoemd *windows service* in versie 1606.)  

    -   Met een onderliggende primaire site worden automatisch dezelfde updates geïnstalleerd die u op een centrale beheersite installeert.  
    -   Secundaire sites als Installeer niet automatisch nieuwe versies. U moet deze handmatig van upgraden binnen de console.  

  Als u na deze stap updates op de centrale beheersite installeert, wordt deze update alleen op onderliggende primaire sites geïnstalleerd als het onderhoudsvenster voor een site dat toestaat.  

4.  **Installeer de updateversie op uw site op het hoogste niveau.** Hiermee vernieuwt u de site op het hoogste niveau. Nadat een centrale beheersite de versie van de update is geïnstalleerd, elke onderliggende primaire site de update automatisch geïnstalleerd als de installatie wordt geblokkeerd door een onderhoudsvenster.  

    -   U kunt bijvoorbeeld uw site op het hoogste site van versie 1606 naar versie 1610 bijwerken. Zie [Updates voor System Center Configuration Manager](../../../../core/servers/manage/updates.md) voor meer informatie.  

    Na deze stap wordt versie 1610 uitgevoerd door uw centrale beheersite en elke primaire site.  

5.  **Voer een upgrade van de secundaire sites uit.** Nadat een primaire site de update is geïnstalleerd en 1610 versie wordt uitgevoerd, gebruikt u de optie in de console voor het upgraden van secundaire sites.  

    -   Deze secundaire sites rechtstreeks vanuit de Microsoft System Center 2012 Configuration Manager bijgewerkt naar de updateversie die u hebt geïnstalleerd op de primaire site.  
    -   Zie voor meer informatie over het upgraden van een secundaire site [upgraden van sites](../../../../core/servers/deploy/install/upgrade-to-configuration-manager.md#bkmk_upgrade) in de [upgraden naar System Center Configuration Manager](../../../../core/servers/deploy/install/upgrade-to-configuration-manager.md) onderwerp.  

6.  **Clients upgraden.** Gebruik de informatie in om clients te upgraden, [clients voor Windows-computers in System Center Configuration Manager bijwerken](../../../../core/clients/manage/upgrade/upgrade-clients-for-windows-computers.md).  

    -   Dit werkt clients rechtstreeks vanuit de Microsoft System Center 2012 Configuration Manager naar de updateversie die u hebt geïnstalleerd op de primaire site.  

    Clients worden na deze stap wordt bijgewerkt naar versie 1610 zonder eerst een upgrade naar versie 1606.
