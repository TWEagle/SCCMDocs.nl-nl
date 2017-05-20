---
title: Onderhoudstaken | Microsoft-documenten
description: "Begrijp wat onderhoud taken om uit te voeren voor Configuration Manager-sites en hiërarchieën en wanneer ze moeten uitvoeren."
ms.custom: na
ms.date: 10/06/2016
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 625bb787-6d16-47a0-8b0f-b129cd909ca3
caps.latest.revision: 7
caps.handback.revision: 0
author: Brenduns
ms.author: brenduns
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 3b56e84cbe9785e280fb02ede6644a8ed2769586
ms.openlocfilehash: 90b6e4434abc5573a364c769bd835e08e5dff16d
ms.contentlocale: nl-nl
ms.lasthandoff: 05/17/2017


---
# <a name="maintenance-tasks-for-system-center-configuration-manager"></a>Onderhoudstaken voor System Center Configuration Manager

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*

System Center Configuration Manager-sites en hiërarchieën vereisen regelmatig onderhoud en regelmatige controle om services te bieden doeltreffende en ononderbroken. Regelmatig onderhoud zorgt ervoor dat de hardware, software en Configuration Manager-database werken correct en doeltreffend blijven. Optimale prestaties reduceren het risico op uitval in verregaande mate.  

 Instellen van waarschuwingen en het gebruik van het statussysteem voor het bewaken van de status van Configuration Manager, Zie [waarschuwingen en het statussysteem voor System Center Configuration Manager gebruiken](../../../core/servers/manage/use-alerts-and-the-status-system.md).  

-   [Onderhoudstaken](#bkmk_MTs)  

##  <a name="bkmk_MTs"></a>Onderhoudstaken  
 Regelmatig onderhoud is van belang om correcte sitebewerkingen te waarborgen. Houd een Onderhoudslogboek document onderhoud einddatums, die dit onderhoud en eventuele onderhoud gerelateerde opmerkingen over de taken heeft.  

### <a name="when-to-do-common-maintenance-tasks"></a>Wanneer u bent van algemene onderhoudstaken  
 U kunt uw site dagelijkse of wekelijkse onderhoud te houden. Sommige taken mogelijk een ander schema. Algemeen onderhoud kan zowel de ingebouwde onderhoudstaken als andere taken, zoals accountonderhoud voor het behouden van compatibiliteit met uw bedrijfsbeleid inzake omvatten.  

 Gebruik de volgende informatie als richtlijn voor het plannen wanneer verschillende onderhoudstaken doen. Gebruik deze lijsten als een beginpunt en voeg toe taken die u nodig hebt.  

**Dagelijkse taken**   
De volgende zijn onderhoudstaken die u voor op een dagelijks schema overwegen kunt:  

-   Controleer of de vooraf gedefinieerde onderhoudstaken die dagelijks zijn gepland met succes zijn uitgevoerd.  

-   Controleer de databasestatus van de Configuration Manager.  

-   Site-Serverstatus controleren.  

-   Controleer de Configuration Manager site postvakken van de afzonderlijke achterstanden met bestanden.  

-   Status van sitesystemen controleren.  

-   Controleer de gebeurtenislogboeken van het besturingssysteem op de site-systemen.  

-   Raadpleeg het foutenlogboek van SQL Server op de computer van de sitedatabase.  

-   De systeemprestaties controleren.  

-   Controleer de Configuration Manager-waarschuwingen.  

**Wekelijks taken**   
De volgende zijn onderhoudstaken die u kunt overwegen om voor een wekelijks schema:  

-   Controleer of de vooraf gedefinieerde onderhoudstaken die zijn gepland wekelijks met succes zijn uitgevoerd.  

-   Onnodige bestanden van sitesystemen verwijderen.  

-   Het produceren en distribueren van eindgebruikersrapporten, indien nodig.  

-   Back-up van toepassing, beveiligings en gebeurtenislogboeken en deze wissen.  

-   Controleer de grootte van de sitedatabase en controleer of er voldoende schijfruimte beschikbaar op de siteserver van de database zodat de sitedatabase kan groeien.  

-   Voer SQL Server-Databaseonderhoud op de sitedatabase op basis van uw SQL Server-onderhoudsplan.  

-   Beschikbare hoeveelheid schijfruimte op alle sitesystemen controleren.  

-   Hulpprogramma's voor schijfdefragmentaties uitvoeren op alle sitesystemen.  

**Periodieke taken**   
Sommige taken waarvoor geen dagelijkse of wekelijkse onderhoud zijn belangrijk om ervoor te zorgen algehele sitestatus. Deze taken Zorg er ook voor dat de beveiliging en noodherstel herstelplannen up-to-date zijn. De volgende zijn onderhoudstaken die u kunt overwegen om voor een andere periodieke schema dan dagelijks of wekelijks taken:  

-   Wijzigen van accounts en wachtwoorden, indien nodig, volgens uw beveiligingsplan.  

-   Bekijk het onderhoudsplan om te controleren of geplande onderhoudstaken juist en doeltreffend zijn gepland, afhankelijk van geconfigureerde site-instellingen.  

-   Controleer de Configuration Manager-hiërarchie-ontwerp voor alle benodigde wijzigingen aan.  

-   De netwerkprestaties controleren om ervoor te zorgen dat wijzigingen zijn aangebracht die van invloed zijn op sitebewerkingen.  

-   Controleer of Active Directory-instellingen die van invloed zijn op sitebewerkingen zijn gewijzigd. Bijvoorbeeld controleren of subnetten die aan Active Directory-sites zijn toegewezen en die worden gebruikt als grenzen voor Configuration Manager-site zijn gewijzigd.  

-   Controleer uw noodherstelplan voor alle benodigde wijzigingen aan.  

-   Doen siteherstel op basis van het noodherstelplan in een testlaboratorium met behulp van een back-up van de meest recente back-up die de onderhoudstaak back-upserver van Site gemaakt.

-   Controleer de hardware op fouten of voor de beschikbare hardware-updates.  

-   De algemene status van de site controleren.  

###  <a name="BKMK_UseMTs"></a>De operationele status van uw sitedatabase onderhouden  
 Terwijl u uw Configuration Manager-site en hiërarchie de taken die u hebt gepland en instellen doet, toevoegen Siteonderdelen voortdurend gegevens aan de Configuration Manager-database. Naarmate de hoeveelheid gegevens toeneemt, nemen de databaseprestaties en de beschikbare opslagruimte in de database worden geweigerd. U kunt siteonderhoudstaken instellen om te verwijderen van verouderde gegevens die u niet langer nodig hebt.  

 Configuration Manager biedt vooraf gedefinieerde onderhoudstaken die u gebruiken kunt voor het onderhouden van de Configuration Manager-database. Niet alle onderhoudstaken zijn beschikbaar op elke site standaard. Verschillende taken zijn ingeschakeld en sommige niet, daarnaast ondersteuning voor een planning die u kunt instellen.  

 De meeste onderhoudstaken verwijderen periodiek verouderde gegevens uit de Configuration Manager-database. De grootte van de database beperken door het verwijderen van onnodige gegevens verbetert de prestaties en de integriteit van de database, verhoogt de efficiëntie van de site en hiërarchie. Andere taken, zoals **indexen opnieuw samenstellen**, de database-efficiëntie te handhaven. Andere taken, zoals de **back-upserver van Site** taak, kan u helpen voorbereiden op herstel na noodgevallen.  

> [!IMPORTANT]  
>  Wanneer u het schema van een taak die gegevens verwijdert plant, houd rekening met het gebruik van die gegevens binnen de hiërarchie. Wanneer een taak die gegevens verwijdert, wordt uitgevoerd op een site, worden de gegevens verwijderd uit de Configuration Manager-database en deze wijziging gerepliceerd naar alle sites in de hiërarchie. Deze verwijdering kan andere taken die afhankelijk van die gegevens zijn beïnvloeden. Bijvoorbeeld op de centrale beheersite, kunt u detectie om uit te voeren één keer per maand niet-clientcomputers te identificeren instellen. U van plan bent de Configuration Manager-client binnen twee weken na hun detectie op deze computers installeren. Echter op één site in de hiërarchie heeft een beheerder heeft ingesteld de taak verouderde Detectiegegevens verwijderen om uit te voeren om de zeven dagen. Het resultaat is dat zeven dagen nadat de niet-clientcomputers zijn gedetecteerd, ze zijn verwijderd uit de Configuration Manager-database. Terug op de centrale beheersite, hebt u voorbereid push Configuration Manager-client installeren op deze nieuwe computers op dag 10. Is echter, omdat de taak verouderde Detectiegegevens verwijderen onlangs is uitgevoerd en verwijderde gegevens die zeven dagen of ouder zijn, de pas gedetecteerde computers niet meer beschikbaar zijn in de database.  

Nadat u een Configuration Manager-site installeert, wordt de beschikbare onderhoudstaken en schakel de taken die uw bewerkingen zijn vereist. Controleer de standaardplanning van de afzonderlijke taken en indien nodig, de planning opstellen af te stemmen de onderhoudstaak zodat deze past bij uw hiërarchie en omgeving. Hoewel de standaardplanning van elke taak is voor de meeste omgevingen geschikt moet, de prestaties van uw sites en database controleren en verwacht af te stemmen taken uitvoeren om de efficiëntie van uw implementatie. Plannen voor het periodiek de prestaties van de site en database controleren en stel onderhoudstaken en hun planningen om de efficiëntie te handhaven opnieuw.  

#### <a name="set-up-maintenance-tasks"></a>Onderhoudstaken instellen  
 Elke Configuration Manager-site ondersteunt onderhoudstaken die de operationele efficiëntie van de sitedatabase te handhaven. Standaard verschillende onderhoudstaken zijn ingeschakeld voor elke site en alle taken ondersteunen onafhankelijke schema's. Onderhoudstaken afzonderlijk worden ingesteld voor elke site en van toepassing zijn op de database op die site. Evenwel sommige taken, zoals **verouderde Detectiegegevens verwijderen**, invloed zijn op informatie die beschikbaar is in alle sites in een hiërarchie.  

 Alleen de onderhoudstaken die u op een site instellen kunt worden weergegeven in de Configuration Manager-console. Zie voor een volledige lijst van onderhoudstaken door sitetype [verwijzing voor het onderhoud van taken voor System Center Configuration Manager](../../../core/servers/manage/reference-for-maintenance-tasks.md).  

 Gebruik de volgende procedure om u te helpen bij het instellen van de algemene instellingen van onderhoudstaken.  

###### <a name="to-set-up-maintenance-tasks-for-configuration-manager"></a>Voor het instellen van onderhoudstaken voor Configuration Manager  

1.  Ga in de Configuration Manager-console naar **beheer** > **siteconfiguratie** >**Sites**.  

2.  Kies de site met de onderhoudstaak die u wilt instellen.  

3.  Op de **Start** tabblad, in de **instellingen** groep, kiest u **siteonderhoud**, en selecteer vervolgens de onderhoudstaak die u wilt instellen.  

    > [!TIP]  
    >  Alleen de taken die beschikbaar op de geselecteerde site zijn worden weergegeven.  

4.  Om de taak, kies **bewerken**, zorg ervoor dat de **deze taak inschakelen** selectievakje is ingeschakeld en stelt u een schema voor wanneer de taak wordt uitgevoerd. Als de taak worden verouderde gegevens ook verwijderd, stelt u de leeftijd van gegevens die uit de database worden verwijderd wanneer de taak wordt uitgevoerd. Kies **OK** te sluiten van de taak **eigenschappen**.  

    > [!NOTE]  
    >  Voor **verouderde statusberichten verwijderen**, instellen van de leeftijd van gegevens te verwijderen bij het instellen van statusfilterregels.  

5.  Als u wilt in- of uitschakelen van de taak zonder de taakeigenschappen te bewerken, kies de **inschakelen** of **uitschakelen** knop. De knop label wordt aangepast, afhankelijk van de huidige configuratie van de taak.  

6.  Als u klaar bent met de onderhoudstaken configureren, kiest u **OK** naar de procedure te voltooien.

