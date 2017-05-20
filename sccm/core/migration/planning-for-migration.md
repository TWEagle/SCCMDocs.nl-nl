---
title: Plannen voor migratie | Microsoft-documenten
description: "Meer informatie over sites en hiërarchieën voordat u gegevens naar een doelhiërarchie van System Center Configuration Manager migreert."
ms.custom: na
ms.date: 1/12/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: b2bf493e-1e10-496f-a139-2646522703ed
caps.latest.revision: 7
caps.handback.revision: 0
author: Brenduns
ms.author: brenduns
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: a2405bc04889bd6ae46069fe447228149bbaf468
ms.openlocfilehash: fffef1e95e1dfa03971f140a6e5a7fff9bfe5e27
ms.contentlocale: nl-nl
ms.lasthandoff: 05/17/2017


---
# <a name="plan-for-migration-to-system-center-configuration-manager"></a>Plannen voor migratie naar System Center Configuration Manager

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*

Zorg voordat u gegevens naar een doelhiërarchie van System Center Configuration Manager migreert, dat u bekend met sites en hiërarchieën in Configuration Manager bent. Zie voor meer informatie over sites en hiërarchieën, [grondbeginselen van System Center Configuration Manager](../../core/understand/fundamentals.md).  

 U moet een System Center Configuration Manager-hiërarchie naar de doelhiërarchie voordat u gegevens vanuit een ondersteunde bronhiërarchie migreert installeren.  

 Nadat u de doelhiërarchie installeert, instellen van de beheerfuncties en -functies die u gebruiken in uw doelhiërarchie wilt voordat u begint met het migreren van gegevens.  

 Bovendien moet u wellicht plannen overlapping tussen de bronhiërarchie en uw doelhiërarchie. Bijvoorbeeld, u de bronhiërarchie kunt instellen voor het gebruik van dezelfde netwerklocaties of grenzen als uw doelhiërarchie en u vervolgens installeert u nieuwe clients naar uw doelhiërarchie en automatische sitetoewijzing gebruiken. In dit scenario, omdat een pas geïnstalleerde Configuration Manager-client kan een site vanaf beide hiërarchieën selecteren de client mogelijk een onjuiste toewijzing naar uw bronhiërarchie. Plan daarom elke nieuwe client in de doelhiërarchie toewijzen aan een specifieke site in die hiërarchie in plaats van met automatische sitetoewijzing.  

 Zie voor meer informatie over sitetoewijzingen [overwegingen voor clientsitetoewijzing](../../core/plan-design/hierarchy/interoperability-between-different-versions.md#BKMK_SupConfigSiteAssignment) in [interoperabiliteit tussen verschillende versies van System Center Configuration Manager](../../core/plan-design/hierarchy/interoperability-between-different-versions.md).  

## <a name="plan-topics"></a>Onderwerpen plannen  
 Gebruik de volgende onderwerpen om te plannen hoe u een ondersteunde bronhiërarchie migreert naar een doelhiërarchie van System Center Configuration Manager:

-   [Vereisten voor migratie in System Center Configuration Manager](../../core/migration/prerequisites-for-migration.md)  

-   [Controlelijsten voor beheerders voor migratieplanning in System Center Configuration Manager](../../core/migration/administrator-checklists-for-migration-planning.md)  

-   [Bepalen of om gegevens te migreren naar System Center Configuration Manager](../../core/migration/determine-whether-to-migrate-data.md)  

-   [Een strategie voor een bronhiërarchie in System Center Configuration Manager plannen](../../core/migration/planning-a-source-hierarchy-strategy.md)  

-   [Controlelijsten voor beheerders voor migratieplanning in System Center Configuration Manager](../../core/migration/administrator-checklists-for-migration-planning.md)  

-   [Een strategie voor clientmigratie in System Center Configuration Manager plannen](../../core/migration/planning-a-client-migration-strategy.md)  

-   [Plan de strategie voor een implementatie van inhoud migratie in System Center Configuration Manager](../../core/migration/planning-a-content-deployment-migration-strategy.md)  

-   [Plannen voor de migratie van Configuration Manager-objecten naar System Center Configuration Manager](../../core/migration/planning-for-the-migration-of-objects.md)  

-   [Plannen voor het bewaken van migratieactiviteiten in System Center Configuration Manager](../../core/migration/planning-to-monitor-migration-activity.md)  

-   [Voltooiing van migratie in System Center Configuration Manager plannen](../../core/migration/planning-to-complete-migration.md)  

