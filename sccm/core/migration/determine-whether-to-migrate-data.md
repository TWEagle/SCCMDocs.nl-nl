---
title: Wat wilt u migreren | Microsoft-documenten
description: Informatie over welke gegevens u kunt migreren en welke gegevens u kunt voor System Center Configuration Manager niet migreren.
ms.custom: na
ms.date: 12/29/2016
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 99222dc8-0e1e-4513-8302-7a1acf671e9b
caps.latest.revision: 6
caps.handback.revision: 0
author: Brenduns
ms.author: brenduns
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: d37261c03fddc3d576fcef73fabd7189e4c46d38
ms.openlocfilehash: 9dc5f6c9f58e1fc33b2dc9dd76737ae23af81993
ms.contentlocale: nl-nl
ms.lasthandoff: 05/17/2017


---
# <a name="determine-whether-to-migrate-data-to-system-center-configuration-manager"></a>Bepalen of er gegevens naar System Center Configuration Manager worden gemigreerd

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*

In System Center Configuration Manager biedt een proces voor het overdragen van gegevens en configuraties die u hebt gemaakt op basis van de ondersteunde versies van Configuration Manager naar de nieuwe hiërarchie.  U kunt hiermee het volgende doen:  

-   Meerdere hiërarchieën combineren tot één.  

-   Gegevens en configuraties van een testomgeving naar uw productie-implementatie verplaatsen.

-   Verplaats gegevens en configuratie van een eerdere versie van Configuration Manager, zoals de Configuration Manager 2007, die geen upgrade naar System Center Configuration Manager-pad heeft, of van System Center 2012 Configuration Manager (die ondersteuning biedt voor een upgrade naar System Center Configuration Manager-pad).  

Met uitzondering van de sitesysteemrol van het distributiepunt en de computers waarop distributiepunten worden gehost, kan er geen infrastructuur (die bestaat uit sites, sitesysteemrollen of computers waarop een sitesysteemrol wordt gehost) worden gemigreerd, overgedragen of gedeeld tussen hiërarchieën.  

 Hoewel u een serverinfrastructuur niet kunt migreren, kunt u Configuration Manager-clients tussen hiërarchieën migreren. Bij een clientmigratie worden de gegevens die clients gebruiken, gemigreerd van de bronhiërarchie naar de doelhiërarchie. Vervolgens wordt de clientsoftware geïnstalleerd of opnieuw toegewezen, zodat de client vervolgens verslag uitbrengt aan de nieuwe hiërarchie.

Nadat u een client op de nieuwe hiërarchie installeren en verzendt de gegevens van de client, helpt de unieke ID van Configuration Manager Configuration Manager de gegevens die u eerder hebt gemigreerd koppelen aan elke clientcomputer.  

 De functionaliteit die opgegeven door de migratie kunt u investeringen die u hebt gemaakt in configuraties en implementaties bij zodat u kunt profiteren van fundamentele productwijzigingen eerste (dat werd geïntroduceerd in System Center 2012 Configuration Manager en vervolgens vervolg in System Center Configuration Manager) wordt onderhouden. Deze wijzigingen omvatten een vereenvoudigde Configuration Manager-hiërarchie waarin minder sites en bronnen en verbeterde verwerking die afkomstig zijn uit met behulp van systeemeigen 64-bits code die wordt uitgevoerd op 64-bits hardware.  

 Zie voor meer informatie over de versies van Configuration Manager die worden ondersteund door de migratie [vereisten voor migratie in System Center Configuration Manager](../../core/migration/prerequisites-for-migration.md).  

 De volgende secties helpen u bij het plannen voor gegevens die u wel of niet migreren:  

-   [Gegevens die u naar System Center Configuration Manager migreren kunt](#Can_Migrate)  

-   [Gegevens die u niet kunt naar System Center Configuration Manager migreren](#Cannot_migrate)  

##  <a name="Can_Migrate"></a>Gegevens die u naar System Center Configuration Manager migreren kunt  
 Migratie van kunt de meeste objecten tussen ondersteunde Configuration Manager-hiërarchieën migreren. De gemigreerde exemplaren van sommige objecten van een ondersteunde versie van Configuration Manager 2007 moeten worden gewijzigd om te voldoen aan de System Center 2012 Configuration Manager-schema en object-indeling.

Deze wijzigingen hebben geen invloed op de gegevens in de database van de bronsite. Objecten die zijn gemigreerd vanuit een ondersteunde versie van System Center 2012 Configuration Manager of System Center Configuration Manager vereisen geen wijziging.  

 Hier volgen de objecten die kunnen worden gemigreerd op basis van de versie van Configuration Manager in de bronhiërarchie. Sommige objecten, zoals query's, kunnen niet worden gemigreerd. Als u deze objecten die niet kunnen worden gemigreerd, wilt blijven gebruiken, moet u ze opnieuw maken in de nieuwe hiërarchie. Andere objecten, waaronder bepaalde clientgegevens, worden automatisch opnieuw gemaakt in de nieuwe hiërarchie wanneer u clients in die hiërarchie beheert.  

### <a name="objects-that-you-can-migrate-from-system-center-2012-configuration-manager-or-system-center-configuration-manager-current-branch"></a>Objecten die u vanaf de huidige vertakking voor System Center 2012 Configuration Manager of System Center Configuration Manager migreren kunt

-   Aankondigingen  

-   Toepassingen voor System Center 2012 Configuration Manager en latere versies  

-   Virtuele App-V-omgeving van System Center 2012 Configuration Manager en hoger  

-   Asset Intelligence-aanpassingen  

-   Grenzen  

-   Verzamelingen: Als u migreert verzamelingen vanuit een ondersteunde versie van System Center 2012 Configuration Manager of System Center Configuration Manager, wilt u een migratietaak voor objecten.  

-   Compatibiliteitsinstellingen:  

    -   Configuratiebasislijn  

    -   Configuratie-items  

-   Implementatie van besturingssysteem:  

    -   Installatiekopieën  

    -   Driverpakketten  

    -   Stuurprogramma 's  

    -   Installatiekopieën  

    -   Pakketten  

    -   Takenreeksen  

-   Zoekresultaten: Opgeslagen zoekcriteria  

-   Software-updates:  

    -   Implementaties  

    -   Implementatiepakketten  

    -   Sjablonen  

    -   Lijsten met software-updates  

-   Softwaredistributiepakketten  

-   Regels voor softwarelicentiecontrole  

-   Virtuele toepassingspakketten  

### <a name="objects-that-you-can-migrate-from-configuration-manager-2007-sp2"></a>Objecten die u van Configuration Manager 2007 SP2 migreren kunt

-   Aankondigingen  

-   Toepassingen voor System Center 2012 Configuration Manager en latere versies  

-   Virtuele App-V-omgeving van System Center 2012 Configuration Manager en hoger  

-   Asset Intelligence-aanpassingen  

-   Grenzen  

-   Verzamelingen: U migreert verzamelingen vanuit een ondersteunde versie van Configuration Manager 2007 met behulp van een verzamelingmigratietaak.  

-   Instellingen voor naleving (Desired Configuration Management genoemd in Configuration Manager 2007):  

    -   Configuratiebasislijn  

    -   Configuratie-items  

-   Implementatie van besturingssysteem:  

    -   Installatiekopieën  

    -   Driverpakketten  

    -   Stuurprogramma 's  

    -   Installatiekopieën  

    -   Pakketten  

    -   Takenreeksen  

-   Zoekresultaten: Zoekmappen  

-   Software-updates:  

    -   Implementaties  

    -   Implementatiepakketten  

    -   Sjablonen  

    -   Lijsten met software-updates  

-   Softwaredistributiepakketten  

-   Regels voor softwarelicentiecontrole  

-   Virtuele toepassingspakketten  

##  <a name="Cannot_migrate"></a>Gegevens die u niet kunt naar System Center Configuration Manager migreren  
 U kunt de volgende typen objecten niet migreren:  

-   Inrichtingsgegevens voor een AMT-client  

-   Bestanden op clients, waaronder:  

    -   Inventaris- en geschiedenisgegevens van een client  

    -   Bestanden in de clientcache  

-   Query's  

-   Configuration Manager 2007-beveiligngsrechten en -exemplaren voor de site en objecten  

-   Rapporten van SQL Server Reporting Services Configuration Manager 2007  

-   Configuration Manager 2007-webrapporten  

-   System Center 2012 Configuration Manager en System Center Configuration Manager-rapporten  

-   System Center 2012 Configuration Manager en System Center Configuration Manager op rollen gebaseerd beheer:  

    -   Beveiligingsrollen  

    -   Beveiligingsbereiken  

