---
title: Migreren van gegevens | Microsoft-documenten
description: "Informatie over het overzetten van gegevens van een bronhiërarchie naar een doelhiërarchie van System Center Configuration Manager."
ms.custom: na
ms.date: 12/29/2016
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: cf014eb0-f8c2-4d37-b8d7-368d63a10b89
caps.latest.revision: 11
caps.handback.revision: 0
author: Brenduns
ms.author: brenduns
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: a8959c72608a1531fb323176c33a848a4a669b1c
ms.openlocfilehash: dface33392c2a2a662522656eabf0936b52b28fc
ms.contentlocale: nl-nl
ms.lasthandoff: 05/17/2017


---
# <a name="migrate-data-between-hierarchies-in-system-center-configuration-manager"></a>Gegevens migreren tussen hiërarchieën in System Center Configuration Manager

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*

Migratie gebruiken om gegevens te brengen vanaf een ondersteunde bronhiërarchie naar uw doelhiërarchie System Center Configuration Manager.  Wanneer u gegevens migreert vanuit een Bronhiërarchie:  

-   U toegang tot gegevens uit de sitedatabases die u identificeert in de broninfrastructuur en brengt u die gegevens naar uw huidige omgeving.  

-   Migratie worden de gegevens in de bronhiërarchie niet gewijzigd, maar in plaats daarvan worden de gegevens gedetecteerd en wordt een kopie opgeslagen in de database van de doelhiërarchie.  

Houd rekening met het volgende wanneer u uw migratiestrategie plant:  

-   U kunt een bestaande Configuration Manager 2007 SP2-infrastructuur migreren naar System Center Configuration Manager.  

-   U kunt bepaalde of alle ondersteunde gegevens van een bronsite migreren.  

-   U kunt de gegevens van één bronsite migreren naar verschillende sites in de doelhiërarchie.  

-   U kunt gegevens van meerdere bronsites verplaatsen naar één site in de doelhiërarchie.  

##  <a name="BKMK_MigrationConcepts"></a> Concepten voor migratie  
 U kunt de volgende concepten en termen die bij het gebruik van migratie tegenkomen.  

|Concept of term|Meer informatie|  
|---------------------|----------------------|  
|Bronhiërarchie|Een hiërarchie die een ondersteunde versie van Configuration Manager wordt uitgevoerd en gegevens die u wilt migreren. Wanneer u een migratie instelt, identificeert u de bronhiërarchie wanneer u de site op het hoogste niveau van een bronhiërarchie opgeeft. Nadat u een bronhiërarchie hebt opgegeven, verzamelt de site op het hoogste niveau van de doelhiërarchie gegevens uit de database van de opgegeven bronsite om te bepalen welke gegevens u kunt migreren.<br /><br /> Zie voor meer informatie [Bronhiërarchieën](../../core/migration/planning-a-source-hierarchy-strategy.md#BKMK_Source_Hierarchies) in [strategie in System Center Configuration Manager voor een bronhiërarchie plannen](../../core/migration/planning-a-source-hierarchy-strategy.md).|  
|Bronsites|De sites in de bronhiërarchie die gegevens bevatten die u kunt migreren naar uw doelhiërarchie.<br /><br /> Zie voor meer informatie [Bronsites](../../core/migration/planning-a-source-hierarchy-strategy.md#BKMK_Source_Sites) in [strategie in System Center Configuration Manager voor een bronhiërarchie plannen](../../core/migration/planning-a-source-hierarchy-strategy.md).|  
|Doelhiërarchie|Een System Center Configuration Manager-hiërarchie waarop migratie wordt uitgevoerd om gegevens te importeren vanuit een bronhiërarchie.|  
|Gegevens verzamelen|Het continue proces om te ontdekken welke informatie in de bronhiërarchie u kunt migreren naar de doelhiërarchie. Configuration Manager controleert de bronhiërarchie volgens een planning om eventuele wijzigingen aan informatie in de bronhiërarchie die u eerder hebt gemigreerd en die u mogelijk wilt bijwerken in de doelhiërarchie te bepalen.<br /><br /> Zie voor meer informatie [gegevensverzamelingsbewerkingen](../../core/migration/planning-a-source-hierarchy-strategy.md#BKMK_Data_Gathering) in [strategie in System Center Configuration Manager voor een bronhiërarchie plannen](../../core/migration/planning-a-source-hierarchy-strategy.md).|  
|Migratietaken|Het proces waarbij wordt geconfigureerd welke specifieke objecten moeten worden gemigreerd, gevolgd door het beheer van de migratie van die objecten naar de doelhiërarchie.<br /><br /> Zie voor meer informatie [een strategie voor migratie in System Center Configuration Manager plannen](../../core/migration/planning-a-migration-job-strategy.md)|  
|Clientmigratie|Het proces waarbij informatie die clients gebruiken, wordt overgedragen van de database van de bronsite naar de database van de doelhiërarchie. Deze migratie van gegevens wordt gevolgd door een upgrade van clientsoftware op apparaten naar de clientsoftwareversie van de doelhiërarchie.<br /><br /> Zie voor meer informatie [Een strategie voor clientmigratie plannen in System Center Configuration Manager](../../core/migration/planning-a-client-migration-strategy.md).|  
|Gedeelde distributiepunten|De distributiepunten van de bronhiërarchie die tijdens de migratieperiode worden gedeeld met de doelhiërarchie.<br /><br /> Tijdens de migratieperiode kunnen clients toegewezen aan sites in de doelhiërarchie inhoud opvragen van gedeelde distributiepunten.<br /><br /> Zie voor meer informatie [distributiepunten delen tussen de bron- en Doelhiërarchieën](../../core/migration/planning-a-content-deployment-migration-strategy.md#About_Shared_DPs_in_Migration) in [de strategie voor een implementatie van inhoud migratie in System Center Configuration Manager plannen](../../core/migration/planning-a-content-deployment-migration-strategy.md).|  
|Migratiebewaking|Het proces waarbij migratieactiviteiten worden bewaakt. U bewaakt de voortgang van migratie en het slagen van de **migratie** knooppunt in de **beheer** werkruimte.<br /><br /> Zie voor meer informatie [Planning voor het bewaken van migratieactiviteiten in System Center Configuration Manager](../../core/migration/planning-to-monitor-migration-activity.md).|  
|Gegevens verzamelen stoppen|Het proces waarbij het verzamelen van gegevens vanaf bronsites wordt gestopt. Wanneer u geen gegevens meer hoeft te migreren vanuit een bronhiërarchie of als u wilt onderbreken migratiegerelateerde activiteiten, kunt u de doelhiërarchie om het verzamelen van gegevens van de bronhiërarchie stoppen.<br /><br /> Zie voor meer informatie [gegevensverzamelingsbewerkingen](../../core/migration/planning-a-source-hierarchy-strategy.md#BKMK_Data_Gathering) in [strategie in System Center Configuration Manager voor een bronhiërarchie plannen](../../core/migration/planning-a-source-hierarchy-strategy.md).|  
|Migratiegegevens opruimen|Het proces waarbij de migratie vanuit een bronhiërarchie wordt voltooid door informatie over de migratie te verwijderen uit de database van de doelhiërarchie.<br /><br /> Zie [Planning voor het voltooien van de migratie in System Center Configuration Manager](../../core/migration/planning-to-complete-migration.md) voor meer informatie.|  

## <a name="typical-workflow-for-migration"></a>Typische werkstroom voor migratie  
Instellen van een werkstroom voor migratie:

1.  Geef een ondersteunde bronhiërarchie op.  

2.  Instellen van het verzamelen van gegevens. Het verzamelen van gegevens kan Configuration Manager voor het verzamelen van informatie over gegevens die kunnen worden gemigreerd van de bronhiërarchie.  

     Configuration Manager automatisch wordt herhaald is het proces voor het verzamelen van gegevens op een eenvoudige planning, totdat u het proces voor gegevensverzameling stopt. Standaard wordt het proces voor gegevensverzameling elke vier uur herhaald zodanig dat Configuration Manager wijzigingen kan herkennen aan gegevens in de bronhiërarchie die u wilt migreren. Het verzamelen van gegevens is ook nodig om distributiepunten van de bronhiërarchie te delen met de doelhiërarchie.  

3.  Maak migratietaken om gegevens te migreren tussen de bron- en doelhiërarchie.  

4.  U kunt het proces voor het verzamelen van gegevens op elk gewenst moment stoppen met de opdracht **Geen gegevens meer verzamelen** . Wanneer u het verzamelen van gegevens stopt, wordt Configuration Manager niet langer wijzigingen aan gegevens in de bronhiërarchie identificeert en kan niet langer distributiepunten delen tussen de bron- en Doelhiërarchieën. Meestal gebruikt u deze actie wanneer u niet langer van plan bent om gegevens te migreren of distributiepunten van de bronhiërarchie te delen.  

5.  Nadat het verzamelen van gegevens op alle sites is gestopt voor de bronhiërarchie, kunt u eventueel de migratiegegevens opruimen met de opdracht **Migratiegegevens opruimen** . Met deze opdracht worden historische gegevens over migratie vanuit een bronhiërarchie gewist uit de database van de doelhiërarchie.  

Nadat u gegevens vanuit een Configuration Manager-bronhiërarchie die u niet langer gebruikt om uw omgeving te beheren migreert, kunt u buiten gebruik stellen die bronhiërarchie en -infrastructuur.  

##  <a name="BKMK_MigrationScenarios"></a> Migratiescenario's  
 Configuration Manager ondersteunt de volgende migratiescenario's.  

> [!NOTE]  
>  De uitbreiding van een hiërarchie met een zelfstandige site in een hiërarchie met een centrale beheersite wordt niet gecategoriseerd als een migratie. Zie voor meer informatie over hiërarchie-uitbreiding [een zelfstandige primaire site uitbreidt](../../core/servers/deploy/install/use-the-setup-wizard-to-install-sites.md#bkmk_expand) in [de Setup-Wizard gebruiken om sites te installeren](../../core/servers/deploy/install/use-the-setup-wizard-to-install-sites.md).  

### <a name="migration-from-configuration-manager-2007-hierarchies"></a>Migreren vanuit Configuration Manager 2007-hiërarchieën  
 Wanneer u migratie gebruikt om gegevens te migreren van Configuration Manager 2007, kunt u uw investering in uw bestaande site-infrastructuur behouden en bovendien profiteren van de volgende voordelen:  

|Voordeel|Meer informatie|  
|-------------|----------------------|  
|Verbeteringen aan de sitedatabase|De System Center Configuration Manager-database biedt volledige ondersteuning voor Unicode.|  
|Databasereplicatie tussen sites|Replicatie in System Center Configuration Manager is gebaseerd op Microsoft SQL Server. Hierdoor worden de prestaties voor gegevensoverdracht tussen sites verbeterd.|  
|Op de gebruiker gericht beheer|Gebruikers kunnen de focus van beheertaken in System Center Configuration Manager. U kunt bijvoorbeeld software distribueren naar een gebruiker, zelfs als u de apparaatnaam voor die gebruiker niet weet. Daarnaast biedt System Center Configuration Manager gebruikers veel meer controle over welke software op hun apparaten wordt geïnstalleerd en wanneer die software wordt geïnstalleerd.|  
|Vereenvoudiging van de hiërarchie|In System Center Configuration Manager, het type centrale beheersite en wijzigingen aan het gedrag van primaire en secundaire sites kunnen u een eenvoudigere sitehiërarchie bouwen waarvoor minder netwerkbandbreedte wordt verbruikt en minder servers vereist.|  
|Op rollen gebaseerd beheer|Dit centrale beveiligingsmodel in System Center Configuration Manager biedt binnen de gehele hiërarchie beveiliging en beheer conform uw administratieve en zakelijke behoeften.|  

> [!NOTE]  
>  Wegens de ontwerpwijzigingen die zijn geïntroduceerd in System Center 2012 Configuration Manager, upgraden u niet Configuration Manager 2007-infrastructuur voor System Center Configuration Manager. Upgrade ter plaatse wordt ondersteund vanaf System Center 2012 Configuration Manager voor System Center Configuration Manager.  

### <a name="migration-from-configuration-manager-2012-or-another-system-center-configuration-manager-hierarchy"></a>Migratie vanuit Configuration Manager 2012 of een andere System Center Configuration Manager-hiërarchie  
 Het proces van het migreren van gegevens uit een System Center 2012 Configuration Manager of System Center Configuration Manager-hiërarchie hetzelfde is. Dit omvat migreren van gegevens vanuit meerdere bronhiërarchieën naar één enkele doelhiërarchie, bijvoorbeeld wanneer uw bedrijf aanvullende bronnen die al worden beheerd door Configuration Manager opgehaald. Daarnaast kunt u gegevens migreert uit een testomgeving naar uw productieomgeving Configuration Manager. Hiermee kunt u investeringen in de Configuration Manager-testomgeving behouden.  

## <a name="additional-topics-for-migration"></a>Aanvullende onderwerpen voor migratie:  

-   [Planning voor migratie naar System Center Configuration Manager](../../core/migration/planning-for-migration.md)  

-   [Bronhiërarchieën en bronsites voor migratie naar System Center Configuration Manager configureren](../../core/migration/configuring-source-hierarchies-and-source-sites-for-migration.md)  

-   [Bewerkingen voor migratie naar System Center Configuration Manager](../../core/migration/operations-for-migration.md)  

-   [Beveiliging en privacy voor migratie naar System Center Configuration Manager](../../core/migration/security-and-privacy-for-migration.md)  

## <a name="see-also"></a>Zie ook  
 [Start met behulp van System Center Configuration Manager](../../core/servers/deploy/start-using.md)

