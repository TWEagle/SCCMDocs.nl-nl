---
title: Installatiescenario&quot;s | Microsoft-documenten
description: "Informatie over technieken voor het installeren van een nieuwe Configuration Manager-hiërarchie wanneer u wilt bijwerken of bijwerken van een site."
ms.custom: na
ms.date: 10/06/2016
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 35586a85-4af9-4c8b-925a-0e32dc8b7346
caps.latest.revision: 6
author: Brenduns
ms.author: brenduns
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9dac6b3fa92c193e3c1a75dd804e0b72fb5394b9
ms.openlocfilehash: dbc303ea9df5a429cb2ef8bd89f372639a4ae2b2
ms.contentlocale: nl-nl
ms.lasthandoff: 05/17/2017


---
# <a name="scenarios-to-streamline-your-installation-of-system-center-configuration-manager"></a>Scenario's om de installatie van System Center Configuration Manager te stroomlijnen

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*

Er zijn nieuwe scenario's voor de installatie van een nieuwe hiërarchie een update-versie (zoals update 1610) te stroomlijnen en upgrade van Microsoft System Center 2012 Configuration Manager met de release van Updateversies voor de huidige vertakking System Center Configuration Manager.

Ondersteunde scenario's zijn onder meer:  

**Installeren van een nieuwe System Center Configuration Manager huidige vertakking hiërarchie** die een updateversie wordt uitgevoerd.  

-   Alleen de bovenste site installeren en installeer vervolgens onmiddellijk een update om te brengen van die site bijgewerkt met de versie van de update die u wilt gebruiken. Vervolgens kunt u aanvullende sites rechtstreeks naar deze updateversie installeren.  
-   In dit scenario slaat u het proces voor het installeren van extra sites naar een basisniveau en ze vervolgens bij te werken met de updateversie die u wilt gebruiken.  
-   In dit scenario moet u het proces voor het installeren van clients naar een versie van de basislijn en vervolgens opnieuw wanneer u naar een nieuwere versie bijwerkt overslaan.  

**Upgrade van een Microsoft System Center 2012 Configuration Manager** infrastructuur voor een update-versie van System Center Configuration Manager.  

-   Handmatig upgrade uw centrale beheersite en elke primaire site naar een versie van de basislijn (zoals versie 1606) voordat u een updateversie installeren (zoals versie 1610).  
-   Geen upgrade van secundaire sites van Microsoft System Center 2012 Configuration Manager totdat de primaire sites uitvoeren de updateversie die u wilt gebruiken.  
-   Geen clients upgraden van Microsoft System Center 2012 Configuration Manager totdat de primaire sites uitvoeren de updateversie die u wilt gebruiken.  

## <a name="scenario-install-a-new-hierarchy-to-an-update-version"></a>Scenario: Een nieuwe hiërarchie naar een updateversie installeren  
In dit voorbeeldscenario, installeert u de eerste site van een hiërarchie met behulp van een basislijn-versie van System Center Configuration Manager, zoals versie 1610. Vervolgens installeert u de update 1610 voordat u extra sites of clients implementeert.  

-   Omdat u van plan bent te gebruiken een updateversie (zoals versie 1610) en niet op een basislijn-versie (zoals versie 1606), hoeft u niet te installeren van extra sites en deze vervolgens bijwerken. Dit geldt ook voor clients.  
-   Geen secundaire sites met versie 1606 installeren en deze vervolgens een upgrade naar versie 1610. In plaats daarvan secundaire sites installeren nadat u uw primaire sites 1610 versie wordt uitgevoerd.  

Ga als volgt de volgorde:  

1.  **Installeren van een site op het hoogste niveau voor de nieuwe hiërarchie** met behulp van de basislijn-media.  

    -   U kunt media basislijn alleen de eerste site van een nieuwe hiërarchie installeren.  
    -   Bijvoorbeeld, een site op het hoogste niveau installeren met behulp van de basislijn-versie van 1606. Zie voor meer informatie [de Setup-Wizard gebruiken om sites te installeren](/sccm/core/servers/deploy/install/use-the-setup-wizard-to-install-sites).  

    Na deze stap is voor uw site op het hoogste niveau versie 1606 uitvoert.  

2.  **Gebruik in de console-updates bij te werken van uw site op het hoogste niveau naar een latere versie.**  

    -   Voordat u alle onderliggende sites of clients hebt geïnstalleerd, werkt u uw site op het hoogste niveau naar de updateversie die u wilt gebruiken.  
    -   U kunt bijvoorbeeld uw site op het hoogste site waarop versie 1606 naar versie 1610 bijwerken. Zie [Updates voor System Center Configuration Manager](../../../../core/servers/manage/updates.md) voor meer informatie.  

    Na deze stap is voor uw site op het hoogste niveau versie 1610 uitvoert.  

3.  **Installeer nieuwe onderliggende primaire sites onder een centrale beheersite.**  

    -   Installeer nieuwe onderliggende primaire sites met behulp van de installatiemedia in de map CD.Latest op de server van de centrale beheersite. Zie [De map CD.Latest voor System Center Configuration Manager](../../../../core/servers/manage/the-cd.latest-folder.md) voor meer informatie.  

      Deze bronmedia zijn vereist om te zorgen dat de versie van de nieuwe onderliggende primaire sites overeenkomt met de versie van de centrale beheersite.  

    Na deze stap Voer uw nieuwe onderliggende primaire sites versie 1610.  

4.  **Gebruik de optie console om nieuwe secundaire sites te installeren op elke primaire site.**  

    -   Omdat u secundaire sites terwijl primaire sites versie 1606 waren niet geïnstalleerd, hoeft u geen upgrade van secundaire sites.  
    -   In plaats daarvan nieuwe secundaire sites waarop versie 1610 installeren. Zie voor meer informatie [Een secundaire site installeren](/sccm/core/servers/deploy/install/use-the-setup-wizard-to-install-sites#bkmk_secondary) in het onderwerp [De installatiewizard gebruiken om sites te installeren](/sccm/core/servers/deploy/install/use-the-setup-wizard-to-install-sites).  

    Nieuwe secundaire sites zijn geïnstalleerd en uitgevoerd versie 1610 na deze stap.  

5.  **Nieuwe clients op de primaire site installeren.**  

    -   Omdat u geen clients hebt geïnstalleerd terwijl primaire sites versie 1606 waren, hoeft u geen clients versie 1606 bijwerken naar versie 1610.  
    -   In plaats daarvan installeert u nieuwe clients die versie 1610 uitvoeren. Zie voor meer informatie [implementeren in System Center Configuration Manager clients](../../../clients/deploy/deploy-clients-to-windows-computers.md).  

    Na deze stap worden nieuwe clients die worden uitgevoerd versie 1610 geïnstalleerd.  

## <a name="scenario-upgrade-system-center-2012-configuration-manager-to-an-update-version-of-system-center-configuration-manager-current-branch"></a>Scenario: Upgrade van System Center 2012 Configuration Manager naar een updateversie van System Center Configuration Manager, huidige vertakking  
In dit voorbeeldscenario uw Microsoft System Center 2012 Configuration Manager-infrastructuur naar een update-versie van System Center Configuration Manager, zoals versie 1610 te upgraden.  

-   De centrale beheersite en elke primaire site moeten een upgrade uitvoeren naar de basisversie 1606 voordat u de update voor versie 1610 installeert.  
-   Secundaire sites en clients geen upgrade uitvoeren of 1606 versie installeren. In plaats daarvan verplaatsen ze rechtstreeks vanuit de Microsoft System Center 2012 Configuration Manager voor System Center Configuration Manager versie 1610.  

Ga als volgt de volgorde:  

1.  **Upgrade van uw site op het hoogste Microsoft System Center 2012 Configuration Manager-site** naar een basislijn-versie van de huidige vertakking via bronmedia voor System Center Configuration Manager (zoals versie 1606). Zie voor meer informatie [upgraden naar System Center Configuration Manager](../../../../core/servers/deploy/install/upgrade-to-configuration-manager.md).  

    -   Zoals traditionele upgradescenario's altijd eerst de site op het hoogste niveau van een hiërarchie bijwerken en vervolgens een upgrade onderliggende sites.  

    Na deze stap is voor uw site op het hoogste niveau versie 1606 uitvoert.  

2.  **Voer een upgrade uit van alle onderliggende primaire sites in uw hiërarchie** naar dezelfde basislijnversie.  

    -   Wanneer u een van Microsoft System Center 2012 Configuration Manager upgrade, moet u handmatig elke primaire site bijwerken naar een basislijn-versie van de huidige vertakking.  
    -   U wordt secundaire sites op dit moment niet bijwerken.  

    Na deze stap worden met elke primaire site versie 1606 uitvoert.  

3.  **Onderhoudsvensters instellen op onderliggende primaire sites.** Na de upgrade van alle primaire sites aan de basislijn-versie, plant u onderhoudsvensters om te bepalen wanneer de infrastructuurupdates voor het installeren van die sites te configureren. Zie voor meer informatie [het gebruik van onderhoudsvensters in System Center Configuration Manager](../../../../core/clients/manage/collections/use-maintenance-windows.md).  (Onderhoudsvensters heten *windows service* in versie 1606.)  

    -   Met een onderliggende primaire site worden automatisch dezelfde updates geïnstalleerd die u op een centrale beheersite installeert.  
    -   Secundaire sties installeren automatisch nieuwe versies. U moet deze handmatig uit in de console upgraden.  

  Als u na deze stap updates op de centrale beheersite installeert, wordt deze update alleen op onderliggende primaire sites geïnstalleerd als het onderhoudsvenster voor een site dat toestaat.  

4.  **Installeer de updateversie op uw site op het hoogste niveau.** Hiermee wordt de site op het hoogste niveau. Nadat u een centrale beheersite installeert de updateversie, elke onderliggende primaire site wordt de update geïnstalleerd tenzij u de installatie wordt geblokkeerd door een onderhoudsvenster.  

    -   U kunt bijvoorbeeld het hoogste niveau van versie 1606 naar versie 1610 bijwerken. Zie [Updates voor System Center Configuration Manager](../../../../core/servers/manage/updates.md) voor meer informatie.  

    Uw centrale beheersite en elke primaire site wordt versie 1610 uitgevoerd na deze stap.  

5.  **Voer een upgrade van de secundaire sites uit.** Nadat een primaire site de update installeert en versie 1610 uitvoert, moet u de optie console gebruiken om secundaire sites te upgraden.  

    -   Dit bijwerken secundaire sites rechtstreeks vanuit de Microsoft System Center 2012 Configuration Manager naar de versie van de update die u hebt geïnstalleerd op de primaire site.  
    -   Zie voor meer informatie over het upgraden van een secundaire site [sites bijwerken](../../../../core/servers/deploy/install/upgrade-to-configuration-manager.md#bkmk_upgrade) in de [upgraden naar System Center Configuration Manager](../../../../core/servers/deploy/install/upgrade-to-configuration-manager.md) onderwerp.  

6.  **Clients upgraden.** Gebruik de informatie in om clients te upgraden, [clients voor Windows-computers in System Center Configuration Manager bijwerken](../../../../core/clients/manage/upgrade/upgrade-clients-for-windows-computers.md).  

    -   Dit werkt clients bij rechtstreeks vanuit de Microsoft System Center 2012 Configuration Manager naar de versie van de update die u hebt geïnstalleerd op de primaire site.  

    Na deze stap worden clients bijgewerkt naar versie 1610 zonder eerst een upgrade naar versie 1606.

