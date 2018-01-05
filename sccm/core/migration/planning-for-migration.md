---
title: Plan voor migratie
titleSuffix: Configuration Manager
description: "Meer informatie over sites en hiërarchieën voordat u gegevens naar een doelhiërarchie van System Center Configuration Manager migreert."
ms.custom: na
ms.date: 1/12/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: b2bf493e-1e10-496f-a139-2646522703ed
caps.latest.revision: "7"
caps.handback.revision: "0"
author: aczechowski
ms.author: aaroncz
manager: angrobe
ms.openlocfilehash: 390211f13fb6bac6dab5b133744ec01ec589bc77
ms.sourcegitcommit: ca9d15dfb1c9eb47ee27ea9b5b39c9f8cdcc0748
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 01/04/2018
---
# <a name="plan-for-migration-to-system-center-configuration-manager"></a>Plan voor migratie naar System Center Configuration Manager

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*

Zorg voordat u gegevens naar een doelhiërarchie van System Center Configuration Manager migreert, dat u bekend met sites en hiërarchieën in Configuration Manager bent. Zie voor meer informatie over sites en hiërarchieën [basisprincipes van System Center Configuration Manager](../../core/understand/fundamentals.md).  

 Een System Center Configuration Manager-hiërarchie om te worden van de doelhiërarchie voordat u gegevens vanuit een ondersteunde bronhiërarchie migreert, moet u installeren.  

 Nadat u de doelhiërarchie, instellen van de beheerfuncties en -functies die u gebruiken in uw doelhiërarchie wilt voordat u begint met het migreren van gegevens.  

 U moet bovendien plannen overlapping tussen de bronhiërarchie en uw doelhiërarchie. Bijvoorbeeld, u kunt de bronhiërarchie instellen om te gebruiken dezelfde netwerklocaties of grenzen als uw doelhiërarchie en u vervolgens installeert u nieuwe clients naar uw doelhiërarchie en automatische sitetoewijzing gebruiken. In dit scenario, omdat een pas geïnstalleerde Configuration Manager-client een site vanaf beide hiërarchieën kunt selecteren de client mogelijk een onjuiste toewijzing naar uw bronhiërarchie. Plan daarom elke nieuwe client in de doelhiërarchie toewijzen aan een specifieke site in die hiërarchie in plaats van automatische sitetoewijzing gebruiken.  

 Zie voor meer informatie over sitetoewijzingen [overwegingen voor clientsitetoewijzing](../../core/plan-design/hierarchy/interoperability-between-different-versions.md#BKMK_SupConfigSiteAssignment) in [interoperabiliteit tussen verschillende versies van System Center Configuration Manager](../../core/plan-design/hierarchy/interoperability-between-different-versions.md).  

## <a name="plan-topics"></a>Onderwerpen plannen  
 Gebruik de volgende onderwerpen voor het migreren van een ondersteunde bronhiërarchie naar een doelhiërarchie van System Center Configuration Manager plannen:

-   [Vereisten voor migratie in System Center Configuration Manager](../../core/migration/prerequisites-for-migration.md)  

-   [Controlelijsten voor beheerders voor migratieplanning in System Center Configuration Manager](../../core/migration/administrator-checklists-for-migration-planning.md)  

-   [Bepalen of om gegevens te migreren naar System Center Configuration Manager](../../core/migration/determine-whether-to-migrate-data.md)  

-   [Een strategie voor een bronhiërarchie in System Center Configuration Manager plannen](../../core/migration/planning-a-source-hierarchy-strategy.md)  

-   [Controlelijsten voor beheerders voor migratieplanning in System Center Configuration Manager](../../core/migration/administrator-checklists-for-migration-planning.md)  

-   [Een strategie voor clientmigratie in System Center Configuration Manager plannen](../../core/migration/planning-a-client-migration-strategy.md)  

-   [Een migratiestrategie voor inhoudsimplementatie in System Center Configuration Manager plannen](../../core/migration/planning-a-content-deployment-migration-strategy.md)  

-   [Plan voor de migratie van Configuration Manager-objecten naar System Center Configuration Manager](../../core/migration/planning-for-the-migration-of-objects.md)  

-   [Plan voor het bewaken van migratieactiviteiten in System Center Configuration Manager](../../core/migration/planning-to-monitor-migration-activity.md)  

-   [Voltooiing van migratie in System Center Configuration Manager plannen](../../core/migration/planning-to-complete-migration.md)  
