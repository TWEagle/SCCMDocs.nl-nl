---
title: Volledige migratie
titleSuffix: Configuration Manager
description: "Informatie over het voltooien van migratie naar een doelhiërarchie van System Center Configuration Manager nadat een bronhiërarchie niet meer gegevens is."
ms.custom: na
ms.date: 1/12/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: f4854b50-2e8c-414c-a872-9579554dca98
caps.latest.revision: "5"
caps.handback.revision: "0"
author: aaroncz
ms.author: aaroncz
manager: angrobe
ms.openlocfilehash: f2e260a9ae046ed3a6ba1d234d1afe84a6976ff7
ms.sourcegitcommit: 7fe45ff75f05f7cc03ad021db8119791abe18049
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/01/2017
---
# <a name="plan-to-complete-migration-in-system-center-configuration-manager"></a>Voltooiing van migratie in System Center Configuration Manager plannen

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*

Met System Center Configuration Manager u het proces kunt voltooien van de migratie wanneer een bronhiërarchie niet langer gegevens bevat die u wilt migreren naar uw doelhiërarchie. Migratie is voltooid, bevat de volgende algemene stappen:  

-   Zorg ervoor dat gegevens die u nodig hebt zijn gemigreerd. Voordat u de migratie vanuit een bronhiërarchie voltooit, ervoor zorgen dat u hebt gemigreerd alle resources van de bronhiërarchie die u nodig in de doelhiërarchie hebt. Dit kunnen bijvoorbeeld gegevens en clients.  

-   Verzamelen van gegevens van bronsites stoppen. Als u wilt migreren vanuit een bronhiërarchie hebt voltooid, moet u eerst het verzamelen van gegevens van bronsites stoppen.  

-   Migratiegegevens opschoont. Nadat u stopt met het verzamelen van gegevens van alle bronsites in een bronhiërarchie, kunt u gegevens over de migratie en de bronhiërarchie kunt verwijderen uit de database van de doelhiërarchie.  

-   Buiten gebruik stellen in de bronhiërarchie. Nadat u de migratie vanuit een bronhiërarchie voltooit en die hiërarchie is niet meer bronnen die u beheert, kunt u de sites in de bronhiërarchie buiten gebruik stellen en de bijbehorende infrastructuur uit uw omgeving verwijderen. Raadpleeg de documentatie voor die versie van Configuration Manager voor meer informatie over het buiten gebruik stellen van sites en bronhiërarchieën.  

Gebruik de volgende secties om te plannen voor het uitvoeren van de migratie vanuit een bronhiërarchie door te verzamelen van gegevens en ruimt migratiegegevens stoppen:  

-   [Wilt u gegevens verzamelen stoppen](#Plan_to_Stop_Data_Gath)  

-   [Opschonen van migratiegegevens plannen](#Plan_to_clean_up)  

##  <a name="Plan_to_Stop_Data_Gath"></a>Wilt u gegevens verzamelen stoppen  
 Voordat u de migratie voltooit en van migratiegegevens opschonen, moet u stoppen met het verzamelen van gegevens van elke bronsite in de bronhiërarchie. U moet uitvoeren om te stoppen met het verzamelen van gegevens van elke bronsite, de **geen gegevens meer verzamelen** opdracht op de onderliggende bronsites en vervolgens het proces herhalen bij iedere bovenliggende site. De site op het hoogste niveau van de bronhiërarchie moet de laatste site zijn waarop u de gegevensverzameling beëindigt. Verzamelen van gegevens op elke onderliggende site voordat u deze opdracht uitvoert op een bovenliggende site, moet u stoppen. Normaal gesproken beëindigen u gegevensverzameling alleen wanneer u klaar bent voor het voltooien van het migratieproces.  

 Nadat u stopt met het verzamelen van gegevens van een bronsite, zijn gedeelde distributiepunten van die site niet meer beschikbaar als inhoudslocaties voor clients in de doelhiërarchie. Zorg daarom dat alle gemigreerde inhoud waartoe de clients in de doelhiërarchie nodig toegang tot beschikbaar blijven hebben door een van de volgende opties:  

-   Distribueer de inhoud naar ten minste één distributiepunt in de doelhiërarchie.  

-   Voordat u stopt met het verzamelen van gegevens van een bronsite, upgraden of opnieuw toewijzen van gedeelde distributiepunten die vereiste inhoud hebben. Voor meer informatie over het upgraden of opnieuw toewijzen van distributiepunten gedeelde, Zie de betreffende gedeelten in [een migratiestrategie voor inhoudsimplementatie in System Center Configuration Manager plannen](../../core/migration/planning-a-content-deployment-migration-strategy.md).  

Nadat u stopt met het verzamelen van gegevens van elke bronsite in de bronhiërarchie, kunt u de migratiegegevens opschoont. Totdat u migratiegegevens opruimt, blijft elke migratietaak die is uitgevoerd of die is gepland voor uitvoering toegankelijk in de Configuration Manager-console.  

Zie voor meer informatie over bronsites en het verzamelen van gegevens, [strategie in System Center Configuration Manager voor een bronhiërarchie plannen](../../core/migration/planning-a-source-hierarchy-strategy.md).  

##  <a name="Plan_to_clean_up"></a>Opschonen van migratiegegevens plannen  
 De laatste stap vereist voor het voltooien van de migratie is migratiegegevens opschoont. U kunt de **migratiegegevens opruimen** opdracht nadat u het verzamelen van gegevens voor elke bronsite in de bronhiërarchie hebt gestopt. Met deze optionele actie worden gegevens over de huidige bronhiërarchie verwijderd uit de database van de doelhiërarchie.  

 Wanneer u migratiegegevens opruimt, wordt de meeste gegevens over de migratie verwijderd uit de database van de doelhiërarchie. Details over gemigreerde objecten blijven echter behouden. Met deze details kunt u de **migratie** werkruimte opnieuw configureren van de bronhiërarchie die de gegevens die de migratie van die bronhiërarchie te hervatten bevat of als u wilt de objecten bekijken en site-eigendom van de eerder gemigreerde objecten is gemigreerd.  
