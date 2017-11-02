---
title: Inleiding op rapportage
titleSuffix: Configuration Manager
description: Meer informatie over de set van hulpprogramma's en bronnen die beschikbaar zijn voor het beheren van rapportage in Configuration Manager.
ms.custom: na
ms.date: 10/06/2016
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: configmgr-other
ms.tgt_pltfrm: na
ms.topic: get-started-article
ms.assetid: 230be984-d2cd-4d53-bd7a-bc24dd93fc22
caps.latest.revision: "7"
author: Dougeby
ms.author: dougeby
manager: angrobe
ms.openlocfilehash: eab08e56ac133f412dd70386002eabb29ecb7115
ms.sourcegitcommit: c236214b2fcc13dae7bad96d7fb33f692868191d
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/12/2017
---
# <a name="introduction-to-reporting-in-system-center-configuration-manager"></a>Inleiding op rapportage in System Center Configuration Manager

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*

Rapportage in System Center Configuration Manager biedt een set hulpprogramma's en resources waarmee u de geavanceerde rapportagefuncties van SQL Server Reporting Services (SSRS) en de uitgebreide ervaring die voorziet in Reporting Services Report Builder gebruikt. Rapportage helpt u verzamelt, organiseert en presenteert informatie over gebruikers, hardware en software-inventaris, software-updates, toepassingen, sitestatus en andere Configuration Manager-bewerkingen in uw organisatie. Rapportage geeft u een aantal vooraf gedefinieerde rapporten die u kunt gebruiken zonder wijzigingen, of die u kunt aanpassen om te voldoen aan uw vereisten. U kunt ook aangepaste rapporten maken. Gebruik de volgende secties om u te helpen bij het beheren van rapportage in Configuration Manager.  

##  <a name="BKMK_SQLServerReportingServices"></a> SQL Server Reporting Services  
 SQL Server Reporting Services geeft u een volledig aanbod aan gebruiksklare hulpprogramma's en services om u te helpen bij het maken, implementeren en beheren van rapporten voor uw organisatie en bij het programmeren van functies die u helpen bij het uitbreiden en aanpassen van uw rapportagefunctionaliteit. Reporting Services is een servergebaseerd rapportageplatform dat uitgebreide rapportagefunctionaliteit biedt voor een waaier aan gegevensbronnen.  

 Configuration Manager gebruikt SQL Server Reporting Services als oplossing voor rapportage. Integratie met Reporting Services biedt de volgende voordelen:  

-   Maakt gebruik van een standaard rapportagesysteem van industrie om te zoeken in de Configuration Manager-database.  

-   Geeft rapporten weer met behulp van de Configuration Manager-rapportviewer of met Rapportbeheer, een Webverbinding naar het rapport.  

-   Biedt hoge prestaties, beschikbaarheid en schaalbaarheid.  

-   Verleent abonnementen aan rapporten waar gebruikers zich op kunnen abonneren. Zo zou een beheerder zich bijvoorbeeld kunnen abonneren om elke dag automatisch een e-mailrapport te ontvangen met informatie over de status van de rollout van een software-update.  

-   Exporteert rapporten die gebruikers kunnen selecteren in een aantal veelgebruikte bestandsindelingen.  

 Zie [SQL Server Reporting Services](http://go.microsoft.com/fwlink/p/?LinkID=212032) in de SQL Server 2008 Books Online voor meer informatie over Reporting Services.  

##  <a name="BKMK_ReportingServicesPoint"></a> Reporting Services-punt  
 Het Reporting Services-punt is een sitesysteemrol die is geïnstalleerd op een server waarop Microsoft SQL Server Reporting Services wordt uitgevoerd. Het reporting services punt kopieert de Configuration Manager rapporteren definities naar Reporting Services, maakt rapportmappen aan op basis van rapportcategorieën, en stelt veiligheidsbeleid in op de rapportmappen en rapporten op basis van op rollen gebaseerde machtigingen voor gebruikers met beheerdersrechten Configuration Manager. In een internval van 10 minuten maakt het Reporting Services-punt verbinding met Reporting Services om het veiligheidsbeleid opnieuw toe te passen als dit werd gewijzigd, bijvoorbeeld door het gebruik van Report Manager. Raadpleeg de volgend documentatie voor meer informatie over het plannen en installeren van een Reporting Services-punt:  

-   [Rapportage in System Center Configuration Manager plannen](planning-for-reporting.md)  

-   [Rapportage in System Center Configuration Manager configureren](configuring-reporting.md)  

##  <a name="BKMK_ConfigurationManagerReports"></a> Configuration Manager-rapporten  
 Configuration Manager geeft rapportdefinities voor meer dan 400 rapporten in meer dan 50 rapportmappen, deze worden gekopieerd naar de basisrapportmap in SQL Server Reporting Services tijdens het installatieproces van reporting services-punt. De rapporten worden weergegeven in de Configuration Manager-console en georganiseerd in submappen op basis van de rapportcategorie. Rapporten worden niet doorgegeven omhoog of omlaag in de Configuration Manager-hiërarchie; ze alleen uitgevoerd voor de database van de site waarin ze zijn gemaakt. Omdat Configuration Manager globale gegevens in de gehele hiërarchie repliceert, hebt u toegang tot informatie van de hele hiërarchie. Wanneer een rapport gegevens ophaalt van een sitedatabase, heeft het toegang tot sitegegevens voor de actuele site en onderliggende sites, en tot globale gegevens voor elke site in de hiërarchie. Net als andere Configuration Manager-objecten, moet een gebruiker met beheerdersrechten hebben de juiste machtigingen voor uitvoeren of wijzigen van rapporten. Een gebruiker met beheerdersrechten moet, om een rapport uit te voeren, beschikken over de machtiging **Rapport uitvoeren** voor het object. Een gebruiker met beheerdersrechten moet, om een rapport te maken of te wijzigen, beschikken over de machtiging **Rapport wijzigen** voor het object.  

###  <a name="BKMK_CreatingReports"></a> Rapporten maken en wijzigen  
 Configuration Manager gebruikt Microsoft SQL Server Report Builder als exclusief ontwerp- en bewerkingsprogramma voor rapporten op basis van modellen en op basis van SQL. Wanneer u maken of bewerken van een rapport in de Configuration Manager-console, wordt Report Builder wordt geopend. Zie [Bewerkingen en onderhoud voor rapportage in System Center Configuration Manager](operations-and-maintenance-for-reporting.md) voor meer informatie over het beheren van rapporten.  

###  <a name="BKMK_RunningReports"></a> Rapporten uitvoeren  
 Wanneer u een rapport in de Configuration Manager-console uitvoert, worden de rapportviewer geopend en verbinding met Reporting Services. Als u vereiste rapportparameters opgeeft, haalt Reporting Services deze gegevens op en geeft de resultaten weer in de viewer. U kunt ook verbinding maken met de SQL Services Reporting Services, verbinden met de gegevensbron voor de site en rapporten uitvoeren.  

###  <a name="BKMK_ReportPrompts"></a> Rapportprompts  
 Een rapportprompt of rapportparameter in Configuration Manager is een rapporteigenschap die u configureren kunt wanneer u een rapport wordt gemaakt of gewijzigd. Rapportprompts worden gemaakt om de gegevens die een rapport ophaalt te beperken of gerichter op te halen. Een rapport kan meer dan één prompt bevatten, op voorwaarde dat de promptnamen uniek zijn en alleen alfanumerieke tekens bevatten die overeenstemmen met de SQL Server-regels voor id's.  

 Als u een rapport uitvoert, vraagt de prompt een waarde voor een vereiste parameter en haalt, op basis van die waarde, de rapportgegevens op. Het rapport **Computerinformatie voor een specifieke computer** haalt de computerinformatie op voor een specifieke computer en vraagt de gebruiker met beheerdersrechten om een computernaam. Reporting Services geeft de opgegeven waarde door aan een variabele die in de SQL-verklaring voor het rapport is gedefinieerd.  

###  <a name="BKMK_ReportLinks"></a> Rapportkoppelingen  
 Rapportkoppelingen in Configuration Manager worden gebruikt in een bronrapport om gebruikers met beheerdersrechten met eenvoudige toegang tot bijkomende gegevens, zoals meer gedetailleerde informatie over elk van de items in het bronrapport bieden. Als er voor het doelrapport één of meer prompts nodig zijn om uit te voeren, moet het bronrapport een kolom bevatten met de juiste waarden voor elke prompt. U moet het kolomnummer specificeren dat de waarde voor de prompt geeft. U kunt bijvoorbeeld een rapport met een lijst met recent gedetecteerde computers koppelen aan een rapport met de meest recente berichten die zijn ontvangen voor een specifieke computer. Als de koppeling is gemaakt, kunt u opgeven dat kolom 2 in het bronrapport computernamen bevat, wat een vereiste prompt is voor het doelrapport. Er verschijnen koppelingspictogram links van elke rij gegevens wanneer het bronrapport wordt uitgevoerd. Als u klikt op het pictogram op een rij, gebruikt de rapportviewer de waarde in de opgegeven kolom voor die rij als de promptwaarde die is vereist om het doelrapport weer te geven. Een rapport kan met slechts één koppeling worden geconfigureerd en die koppeling kan alleen verbinding maken met één enkele doelbron.  

> [!WARNING]  
>  Als u de doelmap naar een andere rapportmap verplaatst, verandert de locatie voor het doelrapport. De rapportkoppeling in het bronrapport wordt niet automatisch bijgewerkt met de nieuwe locatie en de rapportkoppeling zal niet werken in het bronrapport.  

##  <a name="BKMK_ReportFolders"></a> Rapportmappen  
 Rapportmappen in System Center Configuration Manager bieden een methode om te sorteren en filteren rapporten die zijn opgeslagen in Reporting Services. Rapportmappen zijn met name handig wanneer er veel rapporten zijn om te beheren. Wanneer u een Reporting Services-punt installeert, worden rapporten gekopieerd naar Reporting Services en georganiseerd in meer dan 50 rapportmappen. De rapportmappen zijn alleen-lezen. U kunt ze niet wijzigen in de Configuration Manager-console.  

##  <a name="BKMK_ReportSubscriptions"></a> Rapportabonnementen  
 Een rapportabonnement in Reporting Services is een terugkerende aanvraag om een rapport te leveren op een specifieke moment of als reactie op een gebeurtenis en in de bestandsindeling die u opgeeft in het abonnement. Abonnementen bevatten een alternatief voor het uitvoeren van een rapport op aanvraag. Voor rapporten op aanvraag dient u het rapport actief te selecteren telkens u het wilt weergeven. Abonnementen kunnen daarentegen worden gebruikt om de levering van een rapport te plannen en vervolgens te automatiseren.  

 U kunt rapportabonnementen beheren in de Configuration Manager-console. Ze worden verwerkt op de rapportserver. De abonnementen worden gedistribueerd door gebruik te maken van de leveringsextensies die op de server worden geïmplementeerd. Standaard kunt u abonnementen maken die rapporten verzenden naar een gedeelde map of naar een e-mailadres. Zie [Bewerkingen en onderhoud voor rapportage in System Center Configuration Manager](operations-and-maintenance-for-reporting.md) voor meer informatie over het beheren van rapportabonnementen.  

##  <a name="BKMK_ReportBuilder"></a> Report Builder  
 Configuration Manager gebruikt Microsoft SQL Server Reporting Services Report Builder als exclusief ontwerp- en bewerkingsprogramma voor op basis van modellen en op basis van SQL-rapporten. Wanneer u de actie te maken of bewerken van een rapport in de Configuration Manager-console start, wordt Report Builder wordt geopend. Report Builder wordt automatisch geïnstalleerd als u een rapport voor de eerste keer maakt of wijzigt. De versie van Report Builder die aan de geïnstalleerde versie van SQL Server is gekoppeld, wordt geopend wanneer u rapporten uitvoert of bewerkt.  

 De installatie van de Report Builder voegt ondersteuning toe voor meer dan 20 talen. Als Report Builder wordt uitgevoerd, worden de gegevens weergegeven in de taal van het besturingssysteem dat wordt uitgevoerd op de lokale computer. Als Report Builder de taal niet ondersteunt, worden de gegevens in het Engels weergegeven. Report Builder ondersteunt alle functies van SQL Server 2008 Reporting Services, waaronder deze:  

-   Beschikt over een intuïtieve ontwerpomgeving voor rapporten met een uitzicht dat vergelijkbaar is aan Microsoft Office.  

-   Maakt gebruik van de flexibele rapportindeling van SQL Server 2008 Report Definition Language (RDL).  

-   Biedt verschillende vormen van gegevensvisualisatie waaronder grafieken en meters.  

-   Biedt tekstvakken met opmaak.  

-   Exporteert naar Microsoft Word-indeling.  

 U kunt ook Report Builder openen vanuit SQL Server Reporting Services.  

##  <a name="BKMK_ReportModels"></a> Rapportmodellen in SQL Server Reporting Services  
 SQL Reporting Services in Configuration Manager gebruikt rapportmodellen om gebruikers met beheerdersrechten selecteren van items uit de database voor opname in rapporten op basis van model te. Rapportmodellen tonen alleen gespecificeerde weergaven en items om uit te kiezen aan de gebruiker met beheerdersrechten die het rapport maakt. Er moet er minstens één rapportmodel beschikbaar zijn om op modellen gebaseerde rapporten te maken. Rapportmodellen hebben de volgende functies:  

-   U kunt databasevelden en -weergaven logische bedrijfsnamen geven om het produceren van rapporten te vereenvoudigen. Kennis van de databasestructuur is niet vereist voor het produceren van rapporten.  

-   U kunt items logisch groeperen.  

-   U kunt de relaties tussen items definiëren.  

-   U kunt modelelementen zo beveiligen dat gebruikers met beheerdersrechten alleen de gegevens zien waarvoor ze machtigingen hebben.  

 Maar Configuration Manager voorbeelden van rapportmodellen biedt, kunt u ook rapportmodellen om te voldoen aan uw eigen zakelijke behoeften definiëren. Zie [Aangepaste rapportmodellen voor System Center Configuration Manager maken in SQL Server Reporting Services](creating-custom-report-models-in-sql-server-reporting-services.md) voor meer informatie over het maken van rapportmodellen.  

## <a name="next-steps"></a>Volgende stappen
[Rapportage plannen](planning-for-reporting.md)
