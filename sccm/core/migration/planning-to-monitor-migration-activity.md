---
title: Migratie bewaken | Microsoft Docs
description: Informatie over het gebruik van de Configuration Manager-console voor het bewaken van de voortgang en het slagen van migratietaken.
ms.custom: na
ms.date: 10/06/2016
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: fc731d3f-edd7-4049-b17b-653d6693a564
caps.latest.revision: "4"
caps.handback.revision: "0"
author: Brenduns
ms.author: brenduns
manager: angrobe
ms.openlocfilehash: 896807ec2c4be2835094a27add59d4cc09e93add
ms.sourcegitcommit: 51fc48fb023f1e8d995c6c4eacfda7dbec4d0b2f
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 08/07/2017
---
# <a name="planning-to-monitor-migration-activity-in-system-center-configuration-manager"></a>Het bewaken van migratieactiviteiten in System Center Configuration Manager plannen

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*

Met System Center Configuration Manager u migratie bewaken in de Configuration Manager-console die verbinding met de doelhiërarchie maakt. In de Configuration Manager-console in de **beheer** werkruimte kunt u de **migratie** knooppunt voor het bewaken van de voortgang en het slagen van migratietaken. U kunt samenvattingsgegevens voor elke migratietaak die objecten die zijn gemigreerd, objecten die nog niet gemigreerd identificeert en het aantal objecten die zijn uitgesloten van een migratietaak weergeven. U ziet ook details van eventuele migratieproblemen.  

## <a name="view-migration-progress"></a>Voortgang van migratie weergeven  
 Om de voortgang van een migratietaak weergeven, gebruikt u een van de volgende acties:  

-   In de **beheer** werkruimte van de Configuration Manager-console, vouw de **migratietaken** knooppunt, selecteer een migratietaak en selecteer vervolgens de **objecten in taak** tabblad.  

-   De logboekbestanden van de Configuration Manager gebruiken om de voortgang van de migratie te beoordelen of eventuele problemen vast te stellen. Migratiebeheer is het Configuration Manager-proces waarmee migratieacties worden bijgehouden en geregistreerd in het bestand migmctrl.log in de  **\&lt; InstallationPath\>\\LOGBOEKEN** map op de siteserver.  

    > [!NOTE]  
    >  Als een migratietaak mislukt, Controleer u de details in het bestand migmctrl.log zo snel mogelijk. De logboekvermeldingen voor migratie worden continu toegevoegd aan het bestand en oude details overschrijven. Als de vermeldingen worden overschreven, kunt u mogelijk niet bepalen of eventuele problemen die met de gemigreerde objecten optreden kunnen verband met migratieproblemen houden. Migratieactiviteit wordt geregistreerd boven\-site niveau van de hiërarchie, ongeacht de site de Configuration Manager-console verbinding maakt wanneer u migratie configureert.  

-   Gebruik Configuration Manager-rapportage. Configuration Manager biedt diverse ingebouwde\-in rapporten voor migratie, of u kunt deze rapporten ook naar wens bewerken. Zie voor meer informatie over Configuration Manager-rapporten, [rapportage in System Center Configuration Manager](../../core/servers/manage/reporting.md).  
