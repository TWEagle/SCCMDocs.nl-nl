---
title: Onderhoudstaken | Microsoft Docs
description: "Begrijpen wat onderhoud taken voor het uitvoeren voor Configuration Manager-sites en hiërarchieën en wanneer ze moeten uitvoeren."
ms.custom: na
ms.date: 10/06/2016
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 625bb787-6d16-47a0-8b0f-b129cd909ca3
caps.latest.revision: "7"
caps.handback.revision: "0"
author: Brenduns
ms.author: brenduns
manager: angrobe
ms.openlocfilehash: 90b6e4434abc5573a364c769bd835e08e5dff16d
ms.sourcegitcommit: 51fc48fb023f1e8d995c6c4eacfda7dbec4d0b2f
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 08/07/2017
---
# <a name="maintenance-tasks-for-system-center-configuration-manager"></a>Onderhoudstaken voor System Center Configuration Manager

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*

System Center Configuration Manager-sites en hiërarchieën vereisen regelmatig onderhoud en regelmatige controle services effectiever en continu. Regelmatig onderhoud zorgt ervoor dat de hardware, software en Configuration Manager-database blijven werken correct en doeltreffend. Optimale prestaties vermindert aanzienlijk het risico is mislukt.  

 Voor waarschuwingen instellen en het gebruik van het statussysteem voor het bewaken van de status van Configuration Manager, Zie [waarschuwingen en het statussysteem voor System Center Configuration Manager gebruiken](../../../core/servers/manage/use-alerts-and-the-status-system.md).  

-   [Onderhoudstaken](#bkmk_MTs)  

##  <a name="bkmk_MTs"></a>Onderhoudstaken  
 Regelmatig onderhoud is het belangrijk om ervoor te zorgen correcte sitebewerkingen. Houd een Onderhoudslogboek naar het document onderhoudsdatums die dit onderhoud en onderhoud gerelateerde opmerkingen over de taken heeft.  

### <a name="when-to-do-common-maintenance-tasks"></a>Wanneer algemene onderhoudstaken uitvoeren  
 U kunt uw site dagelijkse of wekelijkse onderhoud te houden. Sommige taken mogelijk een ander schema. Algemeen onderhoud kan zowel de ingebouwde onderhoudstaken als andere taken, zoals accountonderhoud voor het handhaven van compatibiliteit met uw bedrijfsbeleid bevatten.  

 Gebruik de volgende informatie als richtlijn bij het plannen wanneer verschillende onderhoudstaken uitvoeren. Gebruik deze lijsten als een beginpunt en voeg de taken die u nodig hebt.  

**Dagelijkse taken**   
De volgende zijn onderhoudstaken die u voor op een dagelijks schema overwegen kunt:  

-   Controleer of de vooraf gedefinieerde onderhoudstaken die dagelijks zijn gepland met succes zijn uitgevoerd.  

-   Controleer de databasestatus van de Configuration Manager.  

-   Controleer de status van de server.  

-   Controleer de Configuration Manager site postvakken van achterstanden met bestanden.  

-   Status van sitesystemen controleren.  

-   Controleer de gebeurtenislogboeken van het besturingssysteem op sitesystemen.  

-   Raadpleeg het foutenlogboek van SQL Server op de computer van de sitedatabase.  

-   De systeemprestaties controleren.  

-   Controleren op waarschuwingen van Configuration Manager.  

**Wekelijkse taken**   
De volgende zijn onderhoudstaken die u kunt overwegen om voor een wekelijks schema:  

-   Controleer of de vooraf gedefinieerde onderhoudstaken die wekelijks moeten worden uitgevoerd zijn gepland met succes zijn uitgevoerd.  

-   Onnodige bestanden van sitesystemen verwijderen.  

-   Produceren en distribueren van eindgebruikersrapporten, indien nodig.  

-   Back-ups van toepassings-, beveiligings- en gebeurtenislogboeken en deze wissen.  

-   De grootte van de sitedatabase controleren en controleer of er voldoende schijfruimte beschikbaar op de siteserver van de database zodat de sitedatabase kan groeien.  

-   SQL Server-Databaseonderhoud op de sitedatabase op basis van uw SQL Server-onderhoudsplan doen.  

-   Beschikbare hoeveelheid schijfruimte op alle sitesystemen controleren.  

-   Schijf-hulpprogramma's voor schijfdefragmentaties uitvoeren op alle sitesystemen.  

**Periodieke taken**   
Sommige taken die niet nodig voor dagelijkse of wekelijkse onderhoud hebt zijn belangrijk om te controleren of de algehele sitestatus. Deze taken ook voor zorgen dat de beveiliging en noodherstel herstelplannen up-to-date zijn. De volgende zijn onderhoudstaken die u kunt overwegen om voor een andere periodieke schema dan dagelijks of wekelijks taken:  

-   Accounts en wachtwoorden wijzigen, indien nodig, afhankelijk van uw beveiligingsplan.  

-   Bekijk het onderhoudsplan om te controleren of geplande onderhoudstaken juist en doeltreffend zijn gepland, afhankelijk van geconfigureerde site-instellingen.  

-   Bekijk het hiërarchieontwerp van de Configuration Manager-voor de vereiste wijzigingen.  

-   De netwerkprestaties controleren om ervoor te zorgen dat wijzigingen zijn aangebracht die van invloed zijn op sitebewerkingen.  

-   Controleer of Active Directory-instellingen die van invloed zijn op sitebewerkingen niet zijn gewijzigd. Controleer bijvoorbeeld de subnetten die aan Active Directory-sites zijn toegewezen en die worden gebruikt als grenzen voor Configuration Manager-site zijn niet gewijzigd.  

-   Bekijk het noodherstelplan voor eventuele vereiste wijzigingen.  

-   Siteherstel op basis van het noodherstelplan in een testomgeving doen met behulp van een back-up van de meest recente back-up die de onderhoudstaak back-upserver van Site gemaakt.

-   Controleer de hardware op fouten of voor de beschikbare hardware-updates.  

-   Controleer de algemene status van de site.  

###  <a name="BKMK_UseMTs"></a>De operationele status van uw sitedatabase onderhouden  
 Terwijl u uw Configuration Manager-site en hiërarchie de taken die u plant en doet configureert, toevoegen Siteonderdelen voortdurend gegevens aan de Configuration Manager-database. Naarmate de hoeveelheid gegevens toeneemt, nemen de databaseprestaties en de beschikbare opslagruimte in de database af te wijzen. U kunt siteonderhoudstaken instellen om te verwijderen van verouderde gegevens die u niet langer nodig hebt.  

 Configuration Manager biedt vooraf gedefinieerde onderhoudstaken die u gebruiken kunt voor het onderhouden van de Configuration Manager-database. Niet alle onderhoudstaken zijn beschikbaar op elke site standaard. Verschillende taken die zijn ingeschakeld, terwijl sommige niet zijn en ondersteuning voor een planning die u kunt instellen.  

 De meeste onderhoudstaken verwijderen periodiek verouderde gegevens uit de Configuration Manager-database. De grootte van de database beperken door het verwijderen van onnodige gegevens verbetert de prestaties en de integriteit van de database, waardoor de efficiëntie van de site en hiërarchie. Andere taken, zoals **indexen opnieuw samenstellen**, helpen de database-efficiëntie te handhaven. Andere taken, zoals de **back-upserver van Site** taak, kan u helpen op herstel na noodgevallen voorbereiden.  

> [!IMPORTANT]  
>  Wanneer u de planning van een taak die gegevens verwijdert plant, kunt u het gebruik van die gegevens in de hiërarchie. Wanneer een taak die gegevens verwijdert, wordt uitgevoerd op een site, worden de gegevens verwijderd uit de Configuration Manager-database en deze wijziging gerepliceerd naar alle sites in de hiërarchie. Deze verwijdering kan invloed hebben op andere taken die afhankelijk van die gegevens zijn. Bijvoorbeeld: op de centrale beheersite mogelijk u detectie één keer per maand voor het identificeren van niet-clientcomputers uitvoeren instellen. U van plan bent de Configuration Manager-client installeren op deze computers binnen twee weken na hun detectie. Echter op één site in de hiërarchie stelt een beheerder de taak verouderde Detectiegegevens verwijderen om uit te voeren om de zeven dagen. Het resultaat is dat zeven dagen nadat niet-clientcomputers worden gedetecteerd, worden deze verwijderd uit de Configuration Manager-database. Op de centrale beheersite u voorbereiden voor de push-installatie van Configuration Manager-client op deze nieuwe computers op dag 10. Echter, omdat de taak verouderde Detectiegegevens verwijderen onlangs uitgevoerd en verwijderde gegevens heeft die is zeven dagen of ouder, de pas gedetecteerde computers niet langer beschikbaar is in de database zijn.  

Nadat u een Configuration Manager-site installeert, de beschikbare onderhoudstaken en schakel de taken in die uw bewerkingen zijn vereist. Controleer de standaardplanning van elke taak en indien nodig, de planning opstellen om te verfijnen van de onderhoudstaak aanpassen aan uw hiërarchie en omgeving. Hoewel de standaardplanning van elke taak moet aan de behoeften van de meeste omgevingen, de prestaties van uw sites en database controleren en verwacht af te stemmen taken voor een verhoging van de efficiëntie van uw implementatie. Plan periodiek de prestaties van de site en database controleren en onderhoudstaken en bijbehorende planningen efficiëntie onderhouden, configureren.  

#### <a name="set-up-maintenance-tasks"></a>Onderhoudstaken instellen  
 Elke Configuration Manager-site ondersteunt onderhoudstaken waarmee de operationele efficiëntie van de sitedatabase onderhouden. Standaard verschillende onderhoudstaken zijn ingeschakeld voor elke site en alle taken ondersteunen onafhankelijke schema's. Onderhoudstaken afzonderlijk worden ingesteld voor elke site en toepassing op de database op die site. Echter, sommige taken, zoals **verouderde Detectiegegevens verwijderen**, van invloed zijn op informatie die beschikbaar is in alle sites in een hiërarchie.  

 Alleen de onderhoudstaken die u op een site instellen kunt worden weergegeven in de Configuration Manager-console. Zie voor een volledige lijst met onderhoudstaken per sitetype [verwijzing voor het onderhoud van taken voor System Center Configuration Manager](../../../core/servers/manage/reference-for-maintenance-tasks.md).  

 Gebruik de volgende procedure om u te helpen bij het instellen van de algemene instellingen van onderhoudstaken.  

###### <a name="to-set-up-maintenance-tasks-for-configuration-manager"></a>Voor het instellen van onderhoudstaken voor Configuration Manager  

1.  Ga in de Configuration Manager-console naar **beheer** > **siteconfiguratie** >**Sites**.  

2.  Kies de site met de onderhoudstaak die u wilt instellen.  

3.  Op de **Start** tabblad, in de **instellingen** groep, kiest u **siteonderhoud**, en kies vervolgens de onderhoudstaak die u wilt instellen.  

    > [!TIP]  
    >  Alleen taken die beschikbaar op de geselecteerde site zijn worden weergegeven.  

4.  Als u de taak instelt, kies **bewerken**, zorg ervoor dat de **deze taak inschakelen** selectievakje is ingeschakeld en instellen van een planning voor wanneer de taak wordt uitgevoerd. Als de taak ook verouderde gegevens verwijdert, stelt u de leeftijd van de gegevens die uit de database worden verwijderd wanneer de taak wordt uitgevoerd. Kies **OK** te sluiten van de taak **eigenschappen**.  

    > [!NOTE]  
    >  Voor **verouderde statusberichten verwijderen**, instellen van de leeftijd van de gegevens te verwijderen bij het instellen van de statusfilterregels.  

5.  Als u wilt in- of uitschakelen van de taak zonder de taakeigenschappen te bewerken, kiest u de **inschakelen** of **uitschakelen** knop. De knop label wordt aangepast, afhankelijk van de huidige configuratie van de taak.  

6.  Als u klaar bent met de onderhoudstaken configureren, kiest u **OK** naar de procedure hebt voltooid.
