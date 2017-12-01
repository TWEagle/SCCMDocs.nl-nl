---
title: Kies wat u wilt migreren
titleSuffix: Configuration Manager
description: Informatie over welke gegevens u kunt migreren, en welke gegevens u kunt naar System Center Configuration Manager niet migreren.
ms.custom: na
ms.date: 12/29/2016
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 99222dc8-0e1e-4513-8302-7a1acf671e9b
caps.latest.revision: "6"
caps.handback.revision: "0"
author: aaroncz
ms.author: aaroncz
manager: angrobe
ms.openlocfilehash: 76d2c34cf701e17ade0a11ec0c95f99f321996a3
ms.sourcegitcommit: 7fe45ff75f05f7cc03ad021db8119791abe18049
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/01/2017
---
# <a name="determine-whether-to-migrate-data-to-system-center-configuration-manager"></a>Bepalen of er gegevens naar System Center Configuration Manager worden gemigreerd

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*

In System Center Configuration Manager biedt migratie de mogelijkheid voor het overbrengen van gegevens en configuraties die u hebt gemaakt op basis van ondersteunde versies van Configuration Manager naar uw nieuwe hiërarchie.  U kunt hiermee het volgende doen:  

-   Meerdere hiërarchieën combineren tot één.  

-   Gegevens en configuraties verplaatsen van een testimplementatie naar uw productie-implementatie.

-   Gegevens en configuratie verplaatsen van een eerdere versie van Configuration Manager, zoals de Configuration Manager 2007, dat geen upgradepad naar System Center Configuration Manager heeft, of van System Center 2012 Configuration Manager (die ondersteuning biedt voor een upgradepad naar System Center Configuration Manager).  

Met uitzondering van de sitesysteemrol van het distributiepunt en de computers waarop distributiepunten worden gehost, kan er geen infrastructuur (die bestaat uit sites, sitesysteemrollen of computers waarop een sitesysteemrol wordt gehost) worden gemigreerd, overgedragen of gedeeld tussen hiërarchieën.  

 Hoewel u een serverinfrastructuur niet kunt migreren, kunt u Configuration Manager-clients tussen hiërarchieën migreren. Bij een clientmigratie worden de gegevens die clients gebruiken, gemigreerd van de bronhiërarchie naar de doelhiërarchie. Vervolgens wordt de clientsoftware geïnstalleerd of opnieuw toegewezen, zodat de client vervolgens verslag uitbrengt aan de nieuwe hiërarchie.

Nadat u een client naar de nieuwe hiërarchie installeert en de client de gegevens verzendt, kunt u de unieke ID van de Configuration Manager Configuration Manager om de gegevens die u eerder migreerde te koppelen aan elke clientcomputer.  

 De functionaliteit die wordt geleverd door de migratie kunt u uw eerdere investeringen in configuraties en implementaties bij zodat u kunt profiteren van de belangrijkste wijzigingen in het product eerste (die is geïntroduceerd in System Center 2012 Configuration Manager en klik vervolgens nog steeds in System Center Configuration Manager) die zijn aangebracht behouden. Deze wijzigingen omvatten een vereenvoudigde Configuration Manager-hiërarchie waarin minder sites en bronnen en verbeterde verwerking die afkomstig zijn uit met behulp van systeemeigen 64-bits code die wordt uitgevoerd op 64-bits hardware.  

 Zie voor meer informatie over de versies van Configuration Manager die ondersteuning biedt voor migratie [vereisten voor migratie in System Center Configuration Manager](../../core/migration/prerequisites-for-migration.md).  

 De volgende secties helpen u bij het plannen voor gegevens die u wel of niet migreren:  

-   [Gegevens die u naar System Center Configuration Manager migreren kunt](#Can_Migrate)  

-   [Gegevens die u niet kunt naar System Center Configuration Manager migreren](#Cannot_migrate)  

##  <a name="Can_Migrate"></a>Gegevens die u naar System Center Configuration Manager migreren kunt  
 Migratie kunnen de meeste objecten tussen hiërarchieën van ondersteunde Configuration Manager worden gemigreerd. De gemigreerde exemplaren van sommige objecten van een ondersteunde versie van Configuration Manager 2007 moeten worden gewijzigd om te voldoen aan de System Center 2012 Configuration Manager-schema en object-indeling.

Deze wijzigingen hebben geen invloed op de gegevens in de database van de bronsite. Objecten die zijn gemigreerd vanuit een ondersteunde versie van System Center 2012 Configuration Manager of System Center Configuration Manager hoeven niet worden gewijzigd.  

 Hieronder vindt u objecten die kunnen worden gemigreerd op basis van de versie van Configuration Manager in de bronhiërarchie. Sommige objecten, zoals query's, kunnen niet worden gemigreerd. Als u deze objecten die niet kunnen worden gemigreerd, wilt blijven gebruiken, moet u ze opnieuw maken in de nieuwe hiërarchie. Andere objecten, waaronder bepaalde clientgegevens, worden automatisch opnieuw gemaakt in de nieuwe hiërarchie wanneer u clients in die hiërarchie beheert.  

### <a name="objects-that-you-can-migrate-from-system-center-2012-configuration-manager-or-system-center-configuration-manager-current-branch"></a>Objecten die u vanuit System Center 2012 Configuration Manager of System Center Configuration Manager current branche migreren kunt

-   Aankondigingen  

-   Toepassingen voor System Center 2012 Configuration Manager en latere versies  

-   Virtuele App-V-omgeving van System Center 2012 Configuration Manager en latere versies  

-   Asset Intelligence-aanpassingen  

-   Grenzen  

-   Verzamelingen: Als u migreert verzamelingen vanuit een ondersteunde versie van System Center 2012 Configuration Manager of System Center Configuration Manager, wilt u een objectmigratietaak.  

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

### <a name="objects-that-you-can-migrate-from-configuration-manager-2007-sp2"></a>Objecten die u vanaf Configuration Manager 2007 SP2 migreren kunt

-   Aankondigingen  

-   Toepassingen voor System Center 2012 Configuration Manager en latere versies  

-   Virtuele App-V-omgeving van System Center 2012 Configuration Manager en latere versies  

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

-   Configuration Manager 2007-beveiligingsrechten en -exemplaren voor de site en objecten  

-   Configuration Manager 2007-rapporten van SQL Server Reporting Services  

-   Configuration Manager 2007-webrapporten  

-   System Center 2012 Configuration Manager en System Center Configuration Manager-rapporten  

-   System Center 2012 Configuration Manager en System Center Configuration Manager op rollen gebaseerd beheer:  

    -   Beveiligingsrollen  

    -   Beveiligingsbereiken  
