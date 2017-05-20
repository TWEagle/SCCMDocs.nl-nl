---
title: Migratie bewaken | Microsoft-documenten
description: Informatie over het gebruik van de Configuration Manager-console voor het bewaken van de voortgang en het slagen van migratietaken.
ms.custom: na
ms.date: 10/06/2016
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: fc731d3f-edd7-4049-b17b-653d6693a564
caps.latest.revision: 4
caps.handback.revision: 0
author: Brenduns
ms.author: brenduns
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 5e3d3f4194b06442e34c10988a20fe9ca40ac5d7
ms.openlocfilehash: 896807ec2c4be2835094a27add59d4cc09e93add
ms.contentlocale: nl-nl
ms.lasthandoff: 05/17/2017


---
# <a name="planning-to-monitor-migration-activity-in-system-center-configuration-manager"></a>Planning voor het bewaken van migratieactiviteiten in System Center Configuration Manager

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*

Met System Center Configuration Manager u migratie bewaken in de Configuration Manager-console die verbinding met de doelhiërarchie maakt. In de Configuration Manager-console in de **beheer** werkruimte kunt u de **migratie** knooppunt voor het bewaken van de voortgang en het slagen van migratietaken. U kunt samenvattingsinformatie voor elke migratietaak waarin objecten die zijn gemigreerd, objecten die nog niet zijn gemigreerd, en het aantal objecten die zijn uitgesloten van een migratietaak weergeven. U ziet ook details van eventuele migratieproblemen.  

## <a name="view-migration-progress"></a>Voortgang van migratie weergeven  
 Om de voortgang van een migratietaak weergeven, gebruikt u een van de volgende acties:  

-   In de **beheer** werkruimte van de Configuration Manager-console, vouw de **migratietaken** knooppunt, selecteer een migratietaak en selecteer vervolgens de **objecten in taak** tabblad.  

-   De Configuration Manager-logboekbestanden gebruiken om de voortgang van de migratie te beoordelen of eventuele problemen vast te stellen. Migratiebeheer is het Configuration Manager-proces waarmee migratieacties worden bijgehouden en geregistreerd in het bestand migmctrl.log in de  **\&lt; Installatiepad\>\\LOGBOEKEN** map op de siteserver.  

    > [!NOTE]  
    >  Als een migratietaak mislukt, raadpleegt u de details in het bestand migmctrl.log zo snel mogelijk. De logboekvermeldingen voor migratie worden continu toegevoegd aan het bestand details worden hierbij overschreven oude. Als de vermeldingen worden overschreven, kunt u mogelijk niet bepalen of eventuele problemen met de gemigreerde objecten optreden verband met migratieproblemen houden. Migratieactiviteit wordt geregistreerd in de rechterbovenhoek\-site niveau van de hiërarchie, ongeacht de site de Configuration Manager-console verbinding maakt wanneer u migratie configureert.  

-   Gebruik de Configuration Manager-rapportage. Configuration Manager bevat diverse ingebouwde\-in rapporten voor migratie, of u kunt deze rapporten ook bewerken conform uw eigen vereisten. Zie voor meer informatie over Configuration Manager-rapporten, [rapportage in System Center Configuration Manager](../../core/servers/manage/reporting.md).  

