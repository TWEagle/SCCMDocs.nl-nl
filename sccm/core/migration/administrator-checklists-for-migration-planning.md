---
title: Controlelijsten voor migratie
titleSuffix: Configuration Manager
description: Gebruik de controlelijsten voor het plannen van een migratiestrategie voor naar System Center Configuration Manager.
ms.custom: na
ms.date: 12/29/2016
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 295fdf07-93cc-490c-acdd-ce3ee88cb36f
caps.latest.revision: "7"
caps.handback.revision: "0"
author: Brenduns
ms.author: brenduns
manager: angrobe
ms.openlocfilehash: 3476709feb8524dda92694efb16af1569f490f62
ms.sourcegitcommit: c236214b2fcc13dae7bad96d7fb33f692868191d
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/12/2017
---
# <a name="administrator-checklists-for-migration-planning-in-system-center-configuration-manager"></a>Controlelijsten voor beheerders voor migratieplanning in System Center Configuration Manager

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*

Gebruik de volgende controlelijsten voor het plannen van uw strategie voor migratie naar System Center Configuration Manager.

##  <a name="Checklist_Migraiton_Planning"></a>Controlelijst voor beheerders voor migratieplanning  
 Gebruik de volgende controlelijst voor de planningsstappen die vóór de migratie.  

-   **Evalueer de huidige omgeving:**  

     Bepaal de bestaande bedrijfsvereisten waaraan de bronhiërarchie voldoet en stel plannen op om in de doelhiërarchie te blijven voldoen aan die vereisten.  

-   **Bestudeer de functionaliteit en wijzigingen die beschikbaar zijn met de versie van Configuration Manager die u gebruikt en gebruik deze informatie om u te helpen bij het ontwerpen van uw doelhiërarchie:**  

    Zie [Basisprincipes van System Center Configuration Manager](../../core/understand/fundamentals.md) en [Wat is er nieuw in System Center Configuration Manager](../../core/plan-design/changes/what-has-changed-from-configuration-manager-2012.md) voor meer informatie.  


-   **Bepaal het administratieve beveiligingsmodel dat moet worden gebruikt voor beheer op basis van rollen:**  

    Zie voor meer informatie [basisprincipes van beheer op basis van rollen voor System Center Configuration Manager](../../core/understand/fundamentals-of-role-based-administration.md).  

-   **Evalueer uw netwerk en Active Directory-topologie:** Bestudeer de bestaande domeinstructuur en netwerktopologie en bedenk hoe deze van invloed is op het hiërarchieontwerp en de migratietaken.  

-   **Ontwerp van de doelhiërarchie voltooien:**  

    Neem beslissingen over de plaatsing van een centrale beheersite, primaire sites, secundaire sites en opties voor inhoudsdistributie.  

-   **Wijs de hiërarchie op de computers die u voor sites en siteservers in de doelhiërarchie gebruikt:**  

    Bepaal welke computers sites en sitesysteemservers wordt gebruikt in de doelhiërarchie en controleer vervolgens of deze voldoende capaciteit hebben om te voldoen aan bestaande en toekomstige operationele vereisten.  

-   **Plan de strategie voor objectmigratie:**  

    Wilt u de beschikbare migratietaken gebruiken voor het migreren van andere objecten, waaronder sitegrenzen, verzamelingen, advertenties en implementaties. Zie voor meer informatie [typen van migratietaken](../../core/migration/planning-a-migration-job-strategy.md#Types_of_Migration) in [een strategie voor migratie in System Center Configuration Manager plannen](../../core/migration/planning-a-migration-job-strategy.md)  

    Configuration Manager alleen de objecten die u selecteert, worden gemigreerd. Alle objecten die niet worden gemigreerd en die vereist zijn in de doelhiërarchie moet opnieuw worden gemaakt in de doelhiërarchie.  

    Objecten die kunnen worden gemigreerd worden weergegeven wanneer u migratietaken configureert.  

-   **Plan de strategie voor clientmigratie:**  

    Plan de migratie van clients aan de hand van een gecontroleerde benadering waarmee de netwerkbandbreedte en serververwerkingsvereisten worden beperkt wanneer u clients migreert naar de doelhiërarchie. Zie voor meer informatie over het plannen van een strategie voor clientmigratie [een strategie voor clientmigratie in System Center Configuration Manager plannen](../../core/migration/planning-a-client-migration-strategy.md).  

-   **Plan de inventaris- en compatibiliteitsgegevens:**  

    Configuration Manager biedt geen ondersteuning migreren voor hardware-inventarisatie, software-inventaris of compatibiliteitsgegevens gewenst Configuratiebeheer voor software-updates of clients.  

    Nadat de client is gemigreerd naar de nieuwe site in de doelhiërarchie en een beleid heeft ontvangen voor deze configuraties, verzendt de client deze informatie naar de toegewezen site. Door deze actie wordt de database van de doelsite gevuld met actuele inventaris- en compatibiliteitsgegevens.  

-   **Plan de voltooiing van de migratie van de bronhiërarchie:**  

    Beslis wanneer objecten en clients worden gemigreerd. Nadat de migratie is voltooid, kunt u een planning maken om de siteservers in de bronhiërarchie buiten gebruik te stellen.  

##  <a name="Checklist_Hierarchy_for_migration"></a>Controlelijst voor beheerders voor hiërarchiemigratie  
Gebruik de volgende controlelijst om een doelhiërarchie te plannen voordat u de migratie start.  

-   **Bepaal welke computers moet worden gebruikt in de doelhiërarchie:**  

    Configuration Manager biedt geen ondersteuning voor een in-place upgrade van Configuration Manager 2007-infrastructuur. U kunt in plaats daarvan migratie gebruiken om gegevens te verplaatsen van Configuration Manager 2007 naar System Center Configuration Manager. Hiervoor moet u een implementatie naast elkaar gebruiken en System Center Configuration Manager installeren op nieuwe computers.  

    Wanneer u vanaf een andere System Center Configuration Manager-hiërarchie migreert, moet u ook een nieuwe doelhiërarchie die een side-by-side-implementatie naar uw bronhiërarchie installeren.  

-   **Maak de doelhiërarchie:**  

    Als u wilt voorbereiden voor migratie installeren en configureren van een System Center Configuration Manager-doelhiërarchie die een primaire site bevat. Bijvoorbeeld:  

    -   Een centrale beheersite installeert en vervolgens ten minste één onderliggende primaire.  

    -   Installeer een zelfstandige primaire als u niet wilt gebruiken van een centrale beheersite.  

-   **Als u informatie migreren die gerelateerd is aan software-updates wilt, software-updatepunt in de doelhiërarchie configureren en synchroniseren van software-updates:**  

    U moet software-updates in de doelhiërarchie configureren en synchroniseren voordat u informatie over software-updates kunt migreren vanaf de bronhiërarchie.  


-   **Installeer en configureer aanvullende sitesysteemrollen in de doelhiërarchie:**  

    Configureer aanvullende sitesysteemrollen en sitesystemen die u nodig hebt.  

-   **Controleer de operationele functionaliteit in de doelhiërarchie:**  

    Controleer het volgende:  

    -   Als de doelhiërarchie bestaat uit meerdere sites, bevestigt u dat databasereplicatie tussen de sites werkt. Databasereplicatie is niet van toepassing op zelfstandige primaire sites.  

    -   Controleer of alle geïnstalleerde sitesysteemrollen operationeel zijn.  

    -   Controleer de Configuration Manager-clients installeren met de doelhiërarchie, correct kan communiceren met hun toegewezen site.  


##  <a name="Checklisit_Migration"></a>Controlelijst voor beheerders voor migratie  
Gebruik de volgende controlelijsten om gegevens te migreren van de bronhiërarchie naar de doelhiërarchie.  

-   **Schakel migratie in de doelhiërarchie:**  

    Een bronhiërarchie configureren door te geven van het hoogste niveau van de bronhiërarchie. Zie voor meer informatie over het opgeven van de bronsite [strategie in System Center Configuration Manager voor een bronhiërarchie plannen](../../core/migration/planning-a-source-hierarchy-strategy.md).  

-   **Wanneer de bronhiërarchie Configuration Manager 2007 SP2 wordt uitgevoerd, selecteert en configureert u aanvullende sites in de bronhiërarchie:**  

    Voor elke aanvullende site in de Configuration Manager 2007 SP2-bronhiërarchie die u wenst te verzamelen van gegevens uit, moet u referenties voor het verzamelen van gegevens configureren. Wanneer u elke bronsite configureert, wordt het proces van het verzamelen van gegevens begint onmiddellijk en blijft gedurende de migratieperiode totdat u het verzamelen van gegevens voor die site stopt. Het verzamelen van gegevens zorgt ervoor dat u objecten kunt migreren vanaf de bronhiërarchie die na een eerdere gegevensverzamelingsproces toegevoegd of bijgewerkt.

    > [!NOTE]  
    >  Wanneer de bronhiërarchie wordt uitgevoerd voor System Center 2012 Configuration Manager of hoger, niet hoeft u aanvullende bronsites te configureren.  

-   **Configureer het delen van distributiepunten:**  

    U kunt distributiepunten delen tussen de twee hiërarchieën om zodoende inhoudt voor objecten die u migreert, beschikbaar te stellen voor clients in de doelhiërarchie. Dit zorgt ervoor dat dezelfde inhoud beschikbaar voor clients in beide hiërarchieën blijft en dat u deze inhoud onderhouden kunt totdat u stopt met het verzamelen van gegevens en de migratie te voltooien.  

    Zie voor meer informatie over gedeelde distributiepunten [distributiepunten delen tussen de bron- en Doelhiërarchieën](../../core/migration/planning-a-content-deployment-migration-strategy.md#About_Shared_DPs_in_Migration) in [een migratiestrategie voor inhoudsimplementatie in System Center Configuration Manager plannen](../../core/migration/planning-a-content-deployment-migration-strategy.md).  

-   **Maak migratietaken en voer voor het migreren van objecten die zijn gekoppeld aan de clients in de bronhiërarchie:**  

    Maak migratietaken om objecten te migreren tussen hiërarchieën. De vereiste configuraties voor elke migratietaak kunnen verschillen, afhankelijk van de gegevens die met de taak worden gemigreerd.  

    Wanneer u bijvoorbeeld inhoud migreert (ongeacht de migratietaak die u gebruikt), moet u een site in de doelhiërarchie toewijzen om die inhoud te kunnen beheren. De toegewezen site krijgt toegang tot de locatie van het originele bronbestand voor de inhoud en is verantwoordelijk voor het distribueren van die inhoud naar distributiepunten in de doelhiërarchie.  

    Zie voor meer informatie [migratietaken maken en bewerken voor system center configuration manager](../../core/migration/operations-for-migration.md#Create_Edit_migration_Jobs) in [bewerkingen voor de migratie naar System Center Configuration Manager](../../core/migration/operations-for-migration.md).  

-   **Migratie van clients naar de doelhiërarchie:**  

    Het proces voor het migreren van clients is afhankelijk van het migratiescenario:  

    -   Wanneer u clients met een clientversie die niet gelijk zijn aan de doelhiërarchie migreert, moet u de clientsoftware upgraden. Upgrade is vereist voor het verwijderen van de huidige Configuration Manager-client, gevolgd door de installatie van de nieuwe clientversie die overeenkomt met de doelsite.  

    -   Wanneer u clients migreert met een clientversie die overeenkomt met de versie van de doelhiërarchie, hoeft de client niet te worden bijgewerkt of opnieuw geïnstalleerd. In plaats daarvan wordt de client opnieuw toegewezen aan een primaire site in de doelhiërarchie.  

    Wanneer u een client migreert naar de doelhiërarchie, wordt de client gekoppeld aan de bijbehorende gegevens die u eerder hebt gemigreerd naar die doelhiërarchie.  

    Zie voor meer informatie [Een strategie voor clientmigratie plannen in System Center Configuration Manager](../../core/migration/planning-a-client-migration-strategy.md).  

-   **Bijwerken of opnieuw toewijzen van gedeelde distributiepunten:**  

    Wanneer u niet langer hebt ter ondersteuning van clients in de bronhiërarchie, kunt u gedeelde distributiepunten van een Configuration Manager 2007-bronsite bijwerken of gedeelde distributiepunten van een System Center 2012 Configuration Manager of System Center Configuration Manager-bronsite opnieuw toewijzen. Wanneer u een distributiepunt bijwerkt of opnieuw toewijst, wordt de sitesysteemrol overgedragen naar een primaire site in de doelhiërarchie en wordt het distributiepunt verwijderd van de bronsite in de bronhiërarchie. Wanneer u een upgrade of een gedeeld distributiepunt opnieuw toewijst, wordt de inhoud blijft op de distributiepuntcomputer en hoeft u geen inhouden naar nieuwe distributiepunten in de doelhiërarchie.  

    U kunt ook een distributiepunt dat zich op een secundaire Configuration Manager 2007-siteserver bijwerken. Hierbij worden de secundaire site en resultaten alleen verwijderd van een distributiepunt in de doelhiërarchie.  

    Zie voor meer informatie over gedeelde distributiepunten [distributiepunten delen tussen de bron- en Doelhiërarchieën](../../core/migration/planning-a-content-deployment-migration-strategy.md#About_Shared_DPs_in_Migration) in [een migratiestrategie voor inhoudsimplementatie in System Center Configuration Manager plannen](../../core/migration/planning-a-content-deployment-migration-strategy.md).  

-   **Migratie voltooien:**  

    Nadat u gegevens en clients hebt gemigreerd van alle sites in de bronhiërarchie en u de toepasselijke distributiepunten hebt bijgewerkt, kunt u de migratie voltooien. Voor het voltooien van de migratie kunt u stoppen verzamelen van gegevens voor elke bronsite in de bronhiërarchie. Daarna kunt u migratiegegevens verwijderen die u niet nodig hebt, en de infrastructuur van de bronhiërarchie buiten bedrijf stellen. Zie [Planning voor het voltooien van de migratie in System Center Configuration Manager](../../core/migration/planning-to-complete-migration.md) voor meer informatie.  
