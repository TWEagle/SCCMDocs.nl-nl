---
title: Bij een clientmigratie plannen
titleSuffix: Configuration Manager
description: "Meer informatie over de taken die u clients vanuit een bronhiërarchie naar een doelhiërarchie van System Center Configuration Manager migreert."
ms.custom: na
ms.date: 12/30/2016
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 2e27b0b7-7bd3-45cd-bc99-9c991606c637
caps.latest.revision: "6"
author: Brenduns
ms.author: brenduns
manager: angrobe
ms.openlocfilehash: 8e41135266565890c793f7920482a4455f05fbde
ms.sourcegitcommit: c236214b2fcc13dae7bad96d7fb33f692868191d
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/12/2017
---
# <a name="plan-a-client-migration-strategy-in-system-center-configuration-manager"></a>Een strategie voor clientmigratie in System Center Configuration Manager plannen

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*

Migreren van clients van de bronhiërarchie naar een doelhiërarchie van System Center Configuration Manager, moet u twee taken uitvoeren. U dient de objecten te migreren die aan de client zijn gekoppeld en vervolgens de clients opnieuw installeren of toewijzen van de bronhiërarchie aan de doelhiërarchie. U migreert eerst de objecten zodat ze beschikbaar zijn wanneer de clients worden gemigreerd. De objecten die aan de client zijn gekoppeld worden gemigreerd met behulp van migratietaken. Zie voor meer informatie over het migreren van objecten die gekoppeld aan de client zijn [een strategie voor migratie in System Center Configuration Manager plannen](../../core/migration/planning-a-migration-job-strategy.md).  

 Gebruik de volgende rubrieken om de migratie van clients naar de doelhiërarchie te plannen.  

-   [De migratie van clients naar de doelhiërarchie plannen](#Planning_for_Client_Agent_Migration)  

-   [De verwerking van gegevens die op de clients achterblijven tijdens de migratie plannen](#Planning_for_Client_Data_Migration)  

-   [Plan de inventaris- en compatibiliteitsgegevens tijdens de migratie](#Planning_for_Inventory_data_migration)  

##  <a name="Planning_for_Client_Agent_Migration"></a> De migratie van clients naar de doelhiërarchie plannen  
 Wanneer u clients migreert vanuit een bronhiërarchie, wordt de clientsoftware op de computer clientupgrades overeenkomen met de versie van het product van de doelhiërarchie.  

-   **Een Configuration Manager 2007-Bronhiërarchie:** Wanneer u clients migreert vanuit een bronhiërarchie waarop een ondersteunde versie van Configuration Manager, de clientsoftware bijgewerkt naar de clientversie voor de doelhiërarchie.  

-   **Een System Center 2012 Configuration Manager of hoger Bronhiërarchie:** Wanneer u clients tussen hiërarchieën die dezelfde productversie migreert, de clientsoftware niet wijzigen of bijwerken. In plaats daarvan gebeurt toewijzing van de client van de bronhiërarchie naar een site in de doelhiërarchie.  

    > [!NOTE]  
    >  Als de productversie van een hiërarchie niet wordt ondersteund voor migratie naar uw doelhiërarchie, upgrade alle sites en clients in de bronhiërarchie naar een compatibele productversie. Na het upgraden van de doelhiërarchie naar een ondersteunde productversie, kunt u tussen de hiërarchieën migreren. Zie voor meer informatie [versies van Configuration Manager die worden ondersteund voor migratie](../../core/migration/prerequisites-for-migration.md#BKMK_SupportedMigrationVersions) in [vereisten voor migratie in System Center Configuration Manager](../../core/migration/prerequisites-for-migration.md).  

Gebruik de volgende informatie bij het plannen van de clientmigratie:  

-   Voor het upgraden of opnieuw toewijzen van clients van een bronsite naar een doelsite, kunt u iedere implementatiemethode voor clients gebruiken die wordt ondersteund voor het implementeren van clients in de doelhiërarchie. Typische implementatiemethodes voor clients zijn onder andere clientpushinstallaties, softwaredistributie, groepsbeleid en clientinstallaties gebaseerd op softwareupdates. Zie voor meer informatie [clientinstallatiemethoden in System Center Configuration Manager](../../core/clients/deploy/plan/client-installation-methods.md).  

-   Zorg ervoor dat het apparaat dat de clientsoftware in de bronhiërarchie uitvoert voldoet aan de minimale hardwarevereisten en draait op een besturingssysteem dat wordt ondersteund door de versie van Configuration Manager in de doelhiërarchie.  

-   Voordat u een client migreert, voert u een migratietaak voor het migreren van de informatie die de client wordt gebruikt in de doelhiërarchie.  

-   Clients die upgraden behouden hun uitvoeringsgeschiedenis voor implementaties. Dit voorkomt dat implementaties onnodig opnieuw in de doelhiërarchie.  

    -   Voor Configuration Manager 2007-clients, advertentie-uitvoeringsgeschiedenis bewaard.  

    -   Voor clients van System Center 2012 Configuration Manager of System Center Configuration Manager blijft de uitvoeringsgeschiedenis voor implementaties.  

-   U kunt clients migreren van sites in de bronhiërarchie in iedere gewenste volgorde. Overweeg echter beperkt aantal clients gefaseerd te migreren in plaats van grote aantallen clients tegelijk migreren. Een gefaseerde migratie legt minder beslag op de netwerkbandbreedte en serververwerking wanneer iedere pas bijgewerkte client zijn initiële inventaris- en compatibiliteitsgegevens naar de toegewezen site verzendt.  

-   Wanneer u Configuration Manager 2007-clients migreert, wordt de clientsoftware is verwijderd van de clientcomputer en de nieuwe clientsoftware wordt geïnstalleerd.  

-   Configuration Manager kan niet migreren van een Configuration Manager 2007-client die de App-V-client is geïnstalleerd, tenzij de App-V-clientversie 4.6 SP1 of hoger.  

U kunt het clientmigratieproces in bewaken de **migratie** knooppunt van de **beheer** werkruimte in de Configuration Manager-console.  

Nadat u de client naar de doelhiërarchie hebt gemigreerd, kunt u dat het apparaat niet meer beheren met behulp van uw bronhiërarchie en kunt u overwegen de client verwijderen uit de bronhiërarchie. Hoewel het niet vereist is bij het migreren van hiërarchieën, kan dit helpen bij het voorkomen van de identificatie van een gemigreerde client in een bronhiërarchierapport of een onjuiste telling van bronnen tussen de twee hiërarchieën tijdens de migratie. Wanneer bijvoorbeeld een gemigreerde client achterblijft in de database van de bronsite, kunt u een softwareupdaterapport uitvoeren dat de computer mogelijk onjuist identificeert als een onbeheerde bron wanneer het nu wordt beheerd door de doelhiërarchie.  

##  <a name="Planning_for_Client_Data_Migration"></a> De verwerking van gegevens die op de clients achterblijven tijdens de migratie plannen  
Bij de migratie van een client van de bronhiërarchie naar de doelhiërarchie, blijven er sommige gegevens achter op het apparaat, terwijl andere informatie niet beschikbaar is op het apparaat na migratie.  

De volgende informatie wordt behouden op het clientapparaat:  

-   De unieke id (GUID) die een client aan de betreffende informatie in de Configuration Manager-database koppelt.  

-   De advertentie- of implementatiegeschiedenis, die voorkomt dat clients onnodig advertenties of implementaties opnieuw uitvoeren in de doelhiërarchie.  

De volgende informatie wordt niet behouden op het clientapparaat:  

-   De bestanden in de clientcache. Als de client deze bestanden nodig heeft om software te installeren, downloadt de client deze nogmaals vanaf de doelhiërarchie.  

-   Informatie van de bronhiërarchie over eventuele advertenties of implementaties die nog niet zijn uitgevoerd. Als u wilt dat de client de advertenties of implementaties uitvoert na de migratie, moet u deze opnieuw implementeren op de client in de doelhiërarchie.  

-   Informatie over de inventarisatie. De client zendt deze informatie naar de toegewezen site in de doelhiërarchie opnieuw nadat de client migreert en de nieuwe clientgegevens zijn gegenereerd.  

-   Compatibiliteitsgegevens. De client zendt deze informatie naar de toegewezen site in de doelhiërarchie opnieuw nadat de client migreert en de nieuwe clientgegevens zijn gegenereerd.  

Wanneer een client migreert, wordt de informatie die is opgeslagen in de Configuration Manager client clientregister en het bestandspad niet behouden. Pas na de migratie deze instellingen opnieuw toe. Standaardinstellingen zijn onder andere:  

-   Energiebeheerschema's  

-   Instellingen voor logboekregistratie  

-   Lokale beleidsinstellingen  

Mogelijk moet u bovendien sommige toepassingen opnieuw installeren.  

##  <a name="Planning_for_Inventory_data_migration"></a> Planning maken voor de inventaris- en compatibiliteitsgegevens tijdens de migratie  
Clientinventaris- en compatibiliteitsgegevens worden niet opgeslagen wanneer u een client migreert naar de doelhiërarchie. Deze informatie wordt opnieuw gemaakt in de doelhiërarchie wanneer een client zijn informatie voor de eerste keer verzendt naar de toegewezen site. Voor minder belasting op de netwerkbandbreedte en serververwerking is het aan te raden een beperkt aantal clients gefaseerd te migreren in plaats van een groot aantal clients tegelijkertijd.  

 U kunt bovendien geen aanpassingen migreren voor hardware-inventaris van een bronhiërarchie. U moet deze apart van de migratie aanbrengen in de doelhiërarchie. Zie voor meer informatie over het uitbreiden van hardware-inventaris [hardware-inventaris configureren in System Center Configuration Manager](../../core/clients/manage/inventory/configure-hardware-inventory.md).  
