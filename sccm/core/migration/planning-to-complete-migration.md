---
title: Migratie voltooien | Microsoft-documenten
description: "Informatie over het migreren naar een doelhiërarchie van System Center Configuration Manager voltooien nadat een bronhiërarchie niet langer gegevens heeft."
ms.custom: na
ms.date: 1/12/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: f4854b50-2e8c-414c-a872-9579554dca98
caps.latest.revision: 5
caps.handback.revision: 0
author: Brenduns
ms.author: brenduns
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 0f4a10ba7bbe397f05d724141b562b6cd8b78ea8
ms.openlocfilehash: eb1d2e320df02b26423ed4341d5bd1568b9444ad
ms.contentlocale: nl-nl
ms.lasthandoff: 05/17/2017


---
# <a name="plan-to-complete-migration-in-system-center-configuration-manager"></a>Voltooiing van migratie in System Center Configuration Manager plannen

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*

Met System Center Configuration Manager, u kunt het migratieproces voltooien wanneer een bronhiërarchie niet langer gegevens bevat die u wilt migreren naar uw doelhiërarchie. Voltooiing van de migratie bevat de volgende algemene stappen:  

-   Zorg ervoor dat gegevens die u nodig hebt zijn gemigreerd. Zorg voordat u de migratie vanuit een bronhiërarchie voltooit, dat u hebt gemigreerd alle bronnen van de bronhiërarchie die u nodig in de doelhiërarchie hebt. Dit kan ook gegevens en clients.  

-   Verzamelen van gegevens van bronsites stoppen. Als u wilt migreren vanuit een bronhiërarchie voltooit, moet u eerst het verzamelen van gegevens van bronsites stoppen.  

-   Migratiegegevens opruimen. Nadat u stopt met het verzamelen van gegevens van alle bronsites in een bronhiërarchie, kunt u gegevens over de migratie en de bronhiërarchie verwijderen uit de database van de doelhiërarchie.  

-   De bronhiërarchie buiten gebruik stellen. Nadat u de migratie vanuit een bronhiërarchie voltooit, en die hiërarchie is niet meer bronnen die u beheert, kunt u de sites in de bronhiërarchie buiten gebruik stellen en de bijbehorende infrastructuur verwijderen uit uw omgeving. Raadpleeg de documentatie voor die versie van Configuration Manager voor meer informatie over het buiten gebruik stellen van sites en bronhiërarchieën.  

Gebruik de volgende secties om te helpen plannen voor het voltooien van de migratie vanuit een bronhiërarchie door het verzamelen van gegevens en het opschonen van migratiegegevens stoppen:  

-   [Plannen om te stoppen met het verzamelen van gegevens](#Plan_to_Stop_Data_Gath)  

-   [Opschonen van migratiegegevens plannen](#Plan_to_clean_up)  

##  <a name="Plan_to_Stop_Data_Gath"></a>Plannen om te stoppen met het verzamelen van gegevens  
 Voordat u de migratie hebt voltooid en van migratiegegevens opschonen, moet u het verzamelen van gegevens van iedere bronsite in de bronhiërarchie stoppen. U moet uitvoeren om het verzamelen van gegevens van iedere bronsite te stoppen, de **geen gegevens meer verzamelen** opdracht op de onderliggende bronsites en vervolgens het proces herhalen bij iedere bovenliggende site. De site op het hoogste niveau van de bronhiërarchie moet de laatste site zijn waarop u de gegevensverzameling beëindigt. U moet gegevensverzameling stopzetten bij iedere onderliggende site voordat u deze opdracht uitvoert op een bovenliggende site. U kunt alleen beëindigen verzamelen van gegevens wanneer u klaar bent met het migratieproces voltooien.  

 Nadat u stopt met het verzamelen van gegevens van een bronsite, zijn gedeelde distributiepunten van die site niet meer beschikbaar als inhoudlocaties voor clients in de doelhiërarchie. Zorg daarom dat alle gemigreerde inhoud waartoe de clients in de doelhiërarchie nodig toegang tot, beschikbaar blijven hebben door een van de volgende opties:  

-   Distribueer de inhoud naar ten minste één distributiepunt in de doelhiërarchie.  

-   Voordat u het verzamelen van gegevens van een bronsite stopt, bijwerken of opnieuw toewijzen van gedeelde distributiepunten die vereiste inhoud hebben. Voor meer informatie over het upgraden of opnieuw toewijzen van distributiepunten gedeelde, Zie de betreffende gedeelten in [de strategie voor een implementatie van inhoud migratie in System Center Configuration Manager plannen](../../core/migration/planning-a-content-deployment-migration-strategy.md).  

Nadat u stopt met het verzamelen van gegevens van iedere bronsite in de bronhiërarchie, kunt u migratiegegevens opschoont. Totdat u migratiegegevens opschoont, blijft elke migratietaak die is uitgevoerd of die is gepland toegankelijk in de Configuration Manager-console.  

Zie voor meer informatie over bronsites en het verzamelen van gegevens, [strategie in System Center Configuration Manager voor een bronhiërarchie plannen](../../core/migration/planning-a-source-hierarchy-strategy.md).  

##  <a name="Plan_to_clean_up"></a>Opschonen van migratiegegevens plannen  
 De laatste stap is nodig voor het voltooien van de migratie is het opschonen van migratiegegevens. U kunt de **migratiegegevens opruimen** opdracht nadat u het verzamelen van gegevens voor elke bronsite in de bronhiërarchie hebt gestopt. Met deze optionele bewerking verwijdert u gegevens over de huidige bronhiërarchie uit de database van de doelhiërarchie.  

 Wanneer u migratiegegevens opruimt, wordt de meeste gegevens over de migratie verwijderd uit de database van de doelhiërarchie. Details over gemigreerde objecten blijven echter behouden. Met deze details kunt u de **migratie** werkruimte opnieuw configureren van de bronhiërarchie met de gegevens die zijn gemigreerd voor migratie van die bronhiërarchie te hervatten of voor de objecten bekijken en site-eigendom van de eerder gemigreerde objecten.  

