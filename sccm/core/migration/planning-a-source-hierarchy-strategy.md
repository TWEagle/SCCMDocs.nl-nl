---
title: "Een strategie voor bronhiërarchie"
titleSuffix: Configuration Manager
description: "Een bronhiërarchie configureren en verzamelen van gegevens van een bronsite voordat u een migratietaak voor System Center Configuration Manager configureren."
ms.custom: na
ms.date: 1/3/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 4800a800-66c8-4c35-aebe-e413a23790c1
caps.latest.revision: "6"
caps.handback.revision: "0"
author: Brenduns
ms.author: brenduns
manager: angrobe
ms.openlocfilehash: deebf706c885dfb1f0838c64df0d201274eee3d8
ms.sourcegitcommit: c236214b2fcc13dae7bad96d7fb33f692868191d
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/12/2017
---
# <a name="plan-a-source-hierarchy-strategy-in-system-center-configuration-manager"></a>Een strategie voor een bronhiërarchie in System Center Configuration Manager plannen

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*

Voordat u een migratietaak in uw omgeving voor System Center Configuration Manager instelt, moet u een bronhiërarchie configureren en gegevens uit minstens één bronsite in die hiërarchie verzamelen. Gebruik de volgende secties om te plannen voor de configuratie van bronhiërarchieën, bronsites configureren en te bepalen hoe Configuration Manager haalt informatie op van de bronsites in de bronhiërarchie. 

##  <a name="BKMK_Source_Hierarchies"></a> Bronhiërarchieën  
Een bronhiërarchie is een Configuration Manager-hiërarchie die gegevens bevat die u wilt migreren. Wanneer u migratie instellen en een bronhiërarchie opgeven, geeft u de site op het hoogste niveau van de bronhiërarchie. Deze site wordt ook een bronsite genoemd. Extra sites waaruit u gegevens in de bronhiërarchie kunt migreren worden ook bronsites genoemd.  

-   Wanneer u een migratietaak ingesteld om gegevens te migreren vanuit een Configuration Manager 2007-bronhiërarchie, configureert u het voor het migreren van gegevens uit een of meer specifieke bronsites in de bronhiërarchie.  

-   Wanneer u een migratietaak instellen om gegevens te migreren vanuit een bronhiërarchie waarop System Center 2012 Configuration Manager of hoger, u hoeft alleen te geven op het hoogste niveau.  

U kunt slechts één bronhiërarchie tegelijk instellen.  

-   Als u een nieuwe bronhiërarchie hebt ingesteld, wordt die hiërarchie automatisch de huidige bronhiërarchie de eerdere bronhiërarchie vervangen.  

-   Bij het instellen van een bronhiërarchie, moet u Geef de bovenste site van de bronhiërarchie en referenties voor Configuration Manager gebruiken om te koppelen aan de SMS-Provider en sitedatabase van die bronsite opgeven.  

-   Configuration Manager gebruikt deze referenties om gegevens te verzamelen over de objecten en distributiepunten van de bronsite.  

-   Als onderdeel van het proces voor gegevensverzameling worden onderliggende sites in de bronhiërarchie geïdentificeerd.  

-   Als de bronhiërarchie een Configuration Manager 2007-hiërarchie is, kunt u die aanvullende sites als bronsites met aparte referenties voor elke bronsite instellen.  

Hoewel u meerdere bronhiërarchieën achter elkaar instellen kunt, is migratie actief voor slechts één bronhiërarchie tegelijk.  

-   Als u een aanvullende bronhiërarchie instellen voordat u de migratie van de huidige bronhiërarchie voltooit, wordt Configuration Manager alle actieve migratietaken geannuleerd en worden geplande migratietaken voor de huidige bronhiërarchie.  

-   De meest recent geconfigureerde bronhiërarchie wordt vervolgens de huidige bronhiërarchie en de oorspronkelijke bronhiërarchie is nu niet actief.  

-   U kunt vervolgens instellen verbindingsreferenties, aanvullende bronsites en migratietaken voor de nieuwe bronhiërarchie.  

Als u een inactieve bronhiërarchie wilt herstellen en niet eerder hebt gebruikt **migratiegegevens**, kunt u de eerder geconfigureerde migratietaken voor die bronhiërarchie weergeven. Voordat u de migratie vanuit die hiërarchie kunt voortzetten, moet u de referenties opnieuw configureren om verbinding te maken met de betreffende bronsites in de hiërarchie. Plan vervolgens de migratietaken opnieuw die niet zijn voltooid.  

> [!CAUTION]  
>  Als u gegevens uit meerdere bronhiërarchieën wilt migreren, moet elke aanvullende bronhiërarchie een unieke verzameling sitecodes bevatten.  

Zie voor meer informatie over het configureren van een bronhiërarchie [bronhiërarchieën en bronsites voor migratie naar System Center Configuration Manager configureren](../../core/migration/configuring-source-hierarchies-and-source-sites-for-migration.md)  

##  <a name="BKMK_Source_Sites"></a> Bronsites  
 Bronsites zijn de sites in de bronhiërarchie met de gegevens die u wilt migreren. De site op het hoogste niveau van de bronhiërarchie is altijd de eerste bronsite. Wanneer tijdens de migratie gegevens uit de eerste bronsite van een nieuwe bronhiërarchie worden verzameld, wordt er informatie over aanvullende sites in die hiërarchie gedetecteerd.  

 Welke acties u na het verzamelen van gegevens voor de oorspronkelijke bronsite kunt uitvoeren, is afhankelijk van de productversie van de bronhiërarchie.  

### <a name="source-sites-that-run-configuration-manager-2007-sp2"></a>Bronsites waarop Configuration Manager 2007 SP2 wordt uitgevoerd  
 Nadat gegevens zijn verzameld vanaf de oorspronkelijke bronsite van de Configuration Manager 2007 SP2-hiërarchie, hoeft u geen aanvullende bronsites instellen voordat u migratietaken maakt. Echter, voordat u gegevens van aanvullende sites migreren kunt, moet u aanvullende sites als bronsites instellen en System Center Configuration Manager gegevens worden verzameld van deze sites.  

 Om gegevens te verzamelen van aanvullende sites, instelt u afzonderlijk elke site als een bronsite. Hiervoor moet u de referenties voor System Center Configuration Manager verbinding maken met de SMS-Provider en sitedatabase van elke bronsite opgeven. Nadat u de referenties voor een bronsite hebt ingesteld, wordt het gegevensverzamelingsproces voor die site begint.  

 Wanneer u aanvullende bronsites in een Configuration Manager 2007 SP2-bronhiërarchie instelt, moet u instellen bronsites vanaf de bovenkant omlaag, wat betekent dat u de onderste laag sites op de laatste instellen. U kunt bronsites in een vertakking van de hiërarchie op elk gewenst moment configureren, maar moet u een site als een bronsite instellen voordat u een van de onderliggende sites als bronsites instellen.  

> [!NOTE]  
>  Alleen primaire sites in een Configuration Manager 2007 SP2-hiërarchie worden ondersteund voor migratie.  

### <a name="source-sites-that-run-system-center-2012-configuration-manager-or-later"></a>Bronsites waarop System Center 2012 Configuration Manager of hoger  
 Nadat gegevens zijn verzameld vanaf de oorspronkelijke bronsite van de System Center 2012 Configuration Manager of hoger hiërarchie, hoeft u geen aanvullende bronsites in die bronhiërarchie instellen. Dit komt doordat in tegenstelling tot Configuration Manager 2007, deze versies van Configuration Manager een gedeelde database gebruikt en de gedeelde database kunt u identificeren en vervolgens migreren alle beschikbare objecten van de oorspronkelijke bronsite.  

 Wanneer u de toegangsaccounts ingesteld om gegevens te verzamelen, moet u mogelijk verlenen de **SMS-Provider voor Bronsiteaccount** toegang tot meerdere computers in de bronhiërarchie. Dit kan nodig zijn wanneer de bronsite meerdere exemplaren van de SMS-provider ondersteunt, elk op een andere computer. Wanneer wordt begonnen met het verzamelen van gegevens, neemt de site op het hoogste niveau van de doelhiërarchie contact op met de site op het hoogste niveau in de bronhiërarchie om de locaties van de SMS-provider voor die site te identificeren. Alleen het eerste exemplaar van de SMS-provider wordt geïdentificeerd. Als het proces voor gegevensverzameling geen toegang tot de SMS-provider op de geïdentificeerde locatie krijgt, mislukt het proces en wordt er geen verbinding gemaakt met andere computers waarop een exemplaar van de SMS-provider voor die site wordt uitgevoerd.  

##  <a name="BKMK_Data_Gathering"></a> Gegevens verzamelen  
 Onmiddellijk nadat u een bronhiërarchie opgeven, van referenties voor elke extra bronsite in een bronhiërarchie instellen of de distributiepunten voor een bronsite deelt, wordt Configuration Manager begint met het verzamelen van gegevens van de bronsite.  

 Het proces voor gegevensverzameling wordt vervolgens herhaald op basis van een eenvoudig schema om ervoor te zorgen dat eventuele wijzigingen in de bronsite worden gesynchroniseerd. Standaard wordt het proces elke vier uur herhaald. U kunt het schema voor deze cyclus wijzigen door het bewerken van de **eigenschappen** van de bronsite. Het oorspronkelijke gegevensverzamelingsproces moeten alle objecten in de Configuration Manager-database en kan lang duren om te voltooien. Omdat tijdens volgende processen voor gegevensverzameling alleen wijzigingen in de gegevens worden geïdentificeerd, nemen deze minder tijd in beslag.  

 De site op het hoogste niveau in de doelhiërarchie maakt verbinding met de SMS-provider en de sitedatabase van de bronsite om een lijst met objecten en distributiepunten op te halen. Voor deze verbindingen worden de toegangsaccounts van de bronsite gebruikt. Zie voor meer informatie over vereiste configuraties voor het verzamelen van gegevens [vereisten voor migratie in System Center Configuration Manager](../../core/migration/prerequisites-for-migration.md).  

 U kunt starten en stoppen van het proces voor gegevensverzameling met behulp van **gegevens nu verzamelen** en **geen gegevens meer verzamelen** in de Configuration Manager-console.  

 Nadat u hebt gebruikt **geen gegevens meer verzamelen** voor een bronsite om welke reden, moet u referenties voor de site configureren voordat u gegevens van die site opnieuw verzamelen kunt. Totdat u de bronsite opnieuw hebt geconfigureerd, kan Configuration Manager niet identificeren nieuwe objecten of wijzigingen in eerder gemigreerde objecten op die site.  

> [!NOTE]  
>  Voordat u een zelfstandige primaire site naar een hiërarchie met een centrale beheersite uitbreiden, moet u alle gegevens verzamelen stoppen. U kunt opnieuw configureren nadat de site-uitbreiding is voltooid voor gegevensverzameling.  

### <a name="gather-data-now"></a>Gegevens nu verzamelen  
 Wanneer het oorspronkelijke gegevensverzamelingsproces voor een site is voltooid, wordt dit proces herhaald om objecten te identificeren die zijn bijgewerkt sinds de laatste gegevensverzamelingscyclus. U kunt ook de **gegevens nu verzamelen** actie in de Configuration Manager-console om te het proces direct te starten en de starttijd van de volgende cyclus opnieuw instellen.  

 Wanneer een proces voor gegevensverzameling is voltooid voor een bronsite, kunt u de distributiepunten delen vanaf de bronsite en migratietaken zo configureren dat gegevens via de site worden gemigreerd. Het verzamelen van gegevens is een herhalend proces voor migratie en wordt herhaald totdat u de bronhiërarchie wijzigt of **geen gegevens meer verzamelen** naar einde van het gegevensverzamelingsproces voor die site.  

### <a name="stop-gathering-data"></a>Geen gegevens meer verzamelen  
 U kunt **geen gegevens meer verzamelen** naar einde van het proces voor gegevensverzameling voor een bronsite als u niet langer wilt dat Configuration Manager om nieuwe of gewijzigde objecten van die site te identificeren. Deze actie voorkomt ook dat Configuration Manager aan clients in de doelhiërarchie gedeelde distributiepunten van de bron aanbiedt als inhoudslocaties voor de inhoud die u hebt gemigreerd.  

 U moet uitvoeren om te stoppen met het verzamelen van gegevens van elke bronsite, **geen gegevens meer verzamelen** op de onderste laag bronsites en vervolgens Herhaal het proces op elke bovenliggende site. De site op het hoogste niveau van de bronhiërarchie moet de laatste site zijn waarop u de gegevensverzameling beëindigt. U moet de gegevensverzameling voor elke onderliggende site beëindigen voordat u deze actie uitvoert voor een bovenliggende site. U kunt de gegevensverzameling alleen beëindigen wanneer u klaar bent om het migratieproces te voltooien.  

 Nadat u stopt met het verzamelen van gegevens voor een bronsite, eerder verzamelde gegevens over objecten en verzamelingen van die site beschikbaar blijven voor gebruik bij het instellen van nieuwe migratietaken. Echter geen nieuwe objecten of verzamelingen niet wordt weergegeven en ziet u de wijzigingen die zijn aangebracht aan bestaande objecten. Als u de bronsite opnieuw configureert en weer begint met het verzamelen van gegevens, worden de status en andere gegevens over eerder gemigreerde objecten weergegeven.  
