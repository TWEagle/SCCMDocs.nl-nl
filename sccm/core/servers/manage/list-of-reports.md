---
title: Lijst met rapporten | Microsoft Docs
description: "Bekijk een lijst met rapporten die worden geleverd met Configuration Manager. De rapporten worden in verschillende categorieën weergegeven."
ms.custom: na
ms.date: 10/06/2016
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: b7332ed3-8003-454b-bb12-1fdf8721425c
caps.latest.revision: "10"
caps.handback.revision: "0"
author: Dougeby
ms.author: dougeby
manager: angrobe
ms.openlocfilehash: 1480c38a6a3afef76b2e8759eaafd47d28f978f4
ms.sourcegitcommit: 51fc48fb023f1e8d995c6c4eacfda7dbec4d0b2f
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 08/07/2017
---
# <a name="list-of-reports-in-system-center-configuration-manager"></a>Lijst met rapporten in System Center Configuration Manager

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*

Veel ingebouwde rapporten worden geleverd met System Center Configuration Manager, die betrekking hebben op veel van de reporting-taken die u wilt uitvoeren. U kunt ook de SQL-instructies in deze rapporten gebruiken om u te helpen uw eigen rapporten schrijven. Gebruik de informatie in dit onderwerp voor meer informatie over de rapporten die worden geleverd met Configuration Manager.  

## <a name="list-of-built-in-configuration-manager-reports"></a>Lijst van ingebouwde rapporten voor Configuration Manager  
 De volgende rapporten worden geleverd met Configuration Manager. De rapporten worden in verschillende categorieën weergegeven.  

### <a name="administrative-security"></a>Administratieve beveiliging  
 De volgende rapporten worden vermeld in de **administratieve beveiliging** categorie.  

|Rapportnaam|Beschrijving|  
|-----------------|-----------------|  
|**Activiteitenlogboek van beheer**|Geeft een record weer van administratieve wijzigingen voor beheergebruikers, beveiligingsrollen, beveiligingsbereiken en verzamelingen.|  
|**Beveiligingstaken van gebruikers met beheerdersrechten**|Geeft beheergebruikers, de bijbehorende beveiligingsrollen en de beveiligingsbereiken die zijn gekoppeld aan elke rol voor elke gebruiker weer.|  
|**Objecten die zijn beveiligd door een enkel beveiligingsbereik**|Bevat objecten die worden beveiligd door een opgegeven beveiligingsbereik en die alleen zijn toegewezen aan dat beveiligingsbereik. Dit rapport geeft geen objecten weer die zijn gekoppeld aan meer dan één beveiligingsbereik.|  
|**Beveiliging voor een of meerdere Configuration Manager-objecten**|Bevat objecten die kunnen worden beveiligd, de beveiligingsbereiken die aan deze objecten zijn gekoppeld en welke beheerdergebruikers rechten hebben voor de objecten.|  
|**Samenvatting beveiligingsrollen**|Geeft beveiligingsrollen en de Configuration Manager-beheerders die zijn gekoppeld aan elke rol.|  
|**Samenvatting beveiligingsbereiken**|Geeft beveiligingsbereiken en de gebruikers met beheerdersrechten Configuration Manager en de beveiligingsgroepen die zijn gekoppeld aan elk bereik.|  

### <a name="alerts"></a>Waarschuwingen  

|Rapportnaam|Beschrijving|  
|-----------------|-----------------|  
|**Waarschuwingsscorecard**|Geeft een samenvatting weer van alle uitgestelde waarschuwingen die zijn gegenereerd tussen de opgegeven begindatum en einddatum.|  
|**Meest gegenereerde waarschuwingen**|Geeft een samenvatting weer van de waarschuwingen die het meest zijn gegenereerd vanaf de opgegeven datum voor het opgegeven functiegebied tot dit moment.|  

### <a name="asset-intelligence"></a>Asset Intelligence  

|Rapportnaam|Beschrijving|  
|-----------------|-----------------|  
|**Hardware 01A - samenvatting van computers in een specifieke verzameling**|Geeft een Asset Intelligence-samenvatting weer van computers in een verzameling die u opgeeft.|  
|**Hardware 03A - primaire computergebruikers**|Geeft de gebruikers weer en het aantal computers waarop ze de primaire gebruiker zijn.|  
|**Hardware 03B - Computers voor een specifieke primaire consolegebruiker**|Geeft alle computers weer waarvoor een opgegeven gebruiker de primaire console-gebruikers is.|  
|**Hardware 04A - Computers met meerdere gebruikers (gedeeld)**|Geeft een lijst weer van computers die geen primaire gebruiker hebben omdat geen gebruiker een percentage console-aanmeldtijd heeft dat groter is dan 66%.|  
|**Hardware 05A - consolegebruikers op een specifieke computer**|Bevat alle consolegebruikers op een opgegeven computer.|  
|**Hardware 06A - Computers waarvoor consolegebruikers gebruikers kunnen niet worden vastgesteld**|Helpt beheerdergebruikers bij de identificatie van computers waarvoor het vastleggen van gebeurtenissen in het beveiligingslogboek moet worden ingeschakeld.|  
|**Hardware 07A - USB-apparaten op fabrikant**|Geeft de USB-apparaten weer, gegroepeerd op fabrikant.|  
|**Hardware 07B - USB-apparaten op fabrikant en beschrijving**|Geeft de USB-apparaten weer, gegroepeerd op fabrikant en omschrijving.|  
|**Hardware 07C - Computers met een specifiek USB-apparaat**|Geeft alle computers weer met een opgegeven USB-apparaat|  
|**Hardware 07D - USB-apparaten op een specifieke computer**|Geeft alle USB-apparaten op een opgegeven computer weer.|  
|**Hardware 08A - Hardware die is niet gereed voor een software-upgrade**|Hardware die niet voldoet aan de minimale hardwarevereisten.|  
|**Hardware 09A - zoeken naar computers**|Geeft een assetbeheersamenvatting weergegeven van computers die overeenkomen met sleutelwoordfilters op computernaam, Configuration Manager-site, domein, hoogste consolegebruiker, besturingssysteem, fabrikant of model.|  
|**Hardware 10A - Computers in een opgegeven verzameling die zijn gewijzigd tijdens een opgegeven periode**|Geeft een samenvatting weer van computers in een opgegeven collectie waarbij een hardwareklasse is gewijzigd gedurende een opgegeven periode.|  
|**Hardware 10B - wijzigingen op een opgegeven computer binnen een opgegeven periode**|Geeft de klassen weer die zijn gewijzigd op een opgegeven computer in een opgegeven periode.|  
|**Licentie 01A - Microsoft Volume License-grootboek voor Microsoft-Licentieverklaringen**|Geeft een inventarisatie weer van alle Microsoft-softwaretitels die beschikbaar zijn in het Microsoft Volume Licensing-programma|  
|**Licentie 01B - Microsoft Volume License-grootboekitem per verkoopkanaal**|Identificeert en toont verkoopkanaal voor geïnventariseerde Microsoft Volume License-software.|  
|**Licentie 01C - Computers met een specifiek Microsoft Volume License-grootboek en verkoopkanaal**|Identificeert en toont computers die een opgegeven item bevatten uit het Microsoft Volume License-grootboek.|  
|**Licentie 01D - Microsoft Volume License-grootboekproducten op een specifieke computer**|Identificeert en toont alle Microsoft-Volume License-grootboekitems op een opgegeven computer.|  
|**Licentie 02A - aantal licenties die binnenkort aflopen op tijdperiode**|Geeft het aantal licenties weer dat binnenkort verloopt op basis van een opgegeven tijdperiode. De weergegeven producten zijn producten waarvan de licenties worden beheerd door de Software Licensing-service.|  
|**Licentie 02B - Computers met licenties die bijna zijn verlopen**|Geeft de opgegeven computers weer met licenties die binnenkort verlopen.|  
|**Licentie 02C - licentiegegevens op een specifieke computer**|Geeft producten weer op een computer waarvan de licenties worden beheerd door de Software Licensing-service.|  
|**Licentie 03A - aantal licenties op licentiestatus**|Geeft producten weer, op licentiestatus, waarvan de licenties worden beheerd door de Software Licensing-service.|  
|**Licentie 03B - Computers met een specifieke licentiestatus**|Geeft producten weer, met een opgegeven licentiestatus, waarvan de licenties worden beheerd door de Software Licensing-service.|  
|**Licentie 04A - telling van producten die worden beheerd door softwarelicentieverlening**|Geeft het aantal producten weer waarvan de licenties worden beheerd door de Software Licensing-service.|  
|**Licentie 04B - Computers met een specifiek product beheerd door Software Licensing-Service**|Bevat computers die worden beheerd door de Software Licensing-service en die een opgegeven product bevatten.|  
|**Licentie 05A - Computers die Sleutelbeheerserver bieden**|Geeft computers weer die als sleutelbeheerserver fungeren.|  
|**Licentie 06A - Processortellingen telt voor producten per processor zijn gelicentieerd**|Geeft het aantal processoren weer op computers die Microsoft-producten gebruiken die licentieverlening per processor ondersteunen.|  
|**Licentie 06B - Computers met een specifiek product dat licentieverlening per processor ondersteunt**|Geeft een lijst weer van computers waarop een opgegeven Microsoft-product is geïnstalleerd dat licentieverlening per processor ondersteunt.|  
|**Licentie 14A - Microsoft Volume Licensing-afstemmingsrapport**|Geeft afstemming op softwarelicenties weer die zijn aangeschaft via Microsoft Volume License Agreement, en de werkelijke inventarisatietelling.|  
|**Licentie 14B - lijst van Microsoft software-inventarisatie is niet gevonden in MVLS**|Dit rapport geeft Microsoft-softwaretitels weer die in gebruik zijn en die niet zijn gevonden in de Microsoft Volume License Agreement.|  
|**Licentie 15A - rapport algemene licentie-afstemming**|Geeft afstemming weer op algemene softwarelicenties die zijn aangeschaft, en de werkelijke inventarisatietelling.|  
|**Licentie 15B - rapport van de algemene licentie-afstemming per computer**|Geeft computers weer waarop het gelicentieerde product is geïnstalleerd met een opgegeven versie.|  
|**Software 01A - samenvatting van geïnstalleerde software in een specifieke verzameling**|Geeft samenvatting weer van geïnstalleerde software die is besteld op het aantal exemplaren dat in de inventarisatie is gevonden.|  
|**Software 02A - productfamilies voor een specifieke verzameling**|Geeft de productfamilies en de telling van software in de familie voor een specifieke verzameling weer.|  
|**Software 02B - productcategorieën voor een specifieke productfamilie**|Geeft opsomming weer van de productcategorieën in een opgegeven productfamilie en de telling van software binnen de categorie.|  
|**Software 02C - Software in een specifieke productfamilie en -categorie**|Geeft alle software weer in een opgegeven productfamilie en -categorie.|  
|**Software 02D - Computers met specifieke geïnstalleerde software**|Geeft alle computers weer waarop opgegeven software is geïnstalleerd.|  
|**Software 02E - geïnstalleerde software op een specifieke computer**|Geeft alle software weer die op een opgegeven computer is geïnstalleerd.|  
|**Software 03A - niet-gecategoriseerde software**|Geeft de software weer die is ingedeeld als onbekend of die geen indeling heeft.|  
|**Software 04A - Software automatisch wordt uitgevoerd op computers geconfigureerd**|Geeft een lijst weer van software die is geconfigureerd om automatisch te worden uitgevoerd op computers.|  
|**Software 04B - Computers met specifieke software die is geconfigureerd voor het automatisch uitvoeren**|Geeft alle computers weer met opgegeven software die is geconfigureerd om automatisch te worden uitgevoerd|  
|**Software 04C - Software die is geconfigureerd voor het automatisch uitvoeren op een specifieke computer**|Geeft geïnstalleerde software weer die is geconfigureerd om automatisch te worden uitgevoerd op een opgegeven computer|  
|**Software 05A - browserhelperobjecten**|Geeft de browserhelperobjecten weer die zijn geïnstalleerd op computers in een opgegeven verzameling.|  
|**Software 05B - Computers met een specifiek browserhelperobject**|Geeft alle computers weer met een opgegeven browserhelperobject.|  
|**Software 05C - browserhelperobjecten op een specifieke computer**|Geeft alle browserhelperobjecten op de opgegeven computer weer.|  
|**Software 06A - zoeken naar geïnstalleerde software**|Dit rapport bevat een samenvatting van geïnstalleerde software die is besteld op het aantal exemplaren op basis van zoekcriteria voor de productnaam, leverancier of versie.|  
|**Software 06B - Software op productnaam**|Geeft een samenvatting weer van geïnstalleerde software die is besteld op het aantal exemplaren op basis van een opgegeven productnaam.|  
|**Software 07A - recent gebruikte uitvoerbare programma's op telling van computers**|Geeft uitvoerbare programma's weer die recent zijn gebruikt met een telling van computers waarop deze zijn gebruikt. Softwarelicentiecontrole moet zijn ingeschakeld voor deze site om dit rapport te kunnen weergeven.|  
|**Software 07B - Computers die recent een opgegeven uitvoerbaar programma hebben gebruikt**|Geeft de computers weer waarop een opgegeven uitvoerbaar programma recent is gebruikt wanneer u de clientinstelling voor het controleren van softwarelicenties inschakelt.|  
|**Software 07C - recent gebruikte uitvoerbare programma's op een opgegeven computer**|Geeft de uitvoerbare bestanden weer die recent zijn gebruikt op een opgegeven computer wanneer u de clientinstelling voor het controleren van softwarelicenties inschakelt.|  
|**Software 08A - recent gebruikte uitvoerbare programma's op telling van gebruikers**|Geeft de uitvoerbare programma's weer die recent zijn gebruikt met een telling van gebruikers die deze het meest recent hebben gebruikt wanneer u de clientinstelling voor softwarelicentiecontrole inschakelt.|  
|**Software 08B - gebruikers die recent een opgegeven uitvoerbaar programma gebruikt**|Geeft de gebruikers weer die het meest recent een opgegeven uitvoerbaar programma hebben gebruikt wanneer u de clientinstelling voor het controleren van softwarelicenties inschakelt.|  
|**Software 08C - recent gebruikte uitvoerbare programma's door een opgegeven gebruiker**|Geeft uitvoerbare programma's weer die recent zijn gebruikt door een opgegeven gebruiker wanneer u de clientinstelling voor softwarelicentiecontrole inschakelt.|  
|**Software 09A - zelden gebruikte software**|Geeft softwaretitels weer die gedurende een opgegeven periode niet zijn gebruikt.|  
|**Software 09B - Computers waarop zelden gebruikte software is geïnstalleerd**|Geeft computers weer waarop software is geïnstalleerd die gedurende een opgegeven periode niet is gebruikt. De opgegeven periode is gebaseerd op de waarde die is opgegeven in het rapport 'Software 09A - Zelden gebruikte software'.|  
|**Software 10A - softwaretitels waarvoor specifieke meerdere aangepaste etiketten zijn gedefinieerd**|Geeft softwaretitels weer op basis van overeenkomst met alle opgegeven criteria voor aangepaste etiketten. Er kunnen maximaal drie aangepaste etiketten worden geselecteerd om een softwaretitelzoekopdracht te verfijnen.|  
|**Software 10B - Computers met een specifiek aangepast etiket softwaretitel is geïnstalleerd**|Geeft alle computers in deze verzameling weer waarvoor de opgegeven softwaretitel met aangepast etiket is geïnstalleerd.|  
|**Software 11A - softwaretitels waarvoor een specifiek aangepast etiket is gedefinieerd**|Geeft softwaretitels weer op basis van overeenkomst met ten minste een van de opgegeven criteria voor aangepaste etiketten.|  
|**Software 12A - softwaretitels zonder aangepast etiket**|Geeft alle softwaretitels weer waarvoor geen aangepast etiket is gedefinieerd.|  
|**Software 14A - zoeken naar software waarbij een softwaretag is geactiveerd**|Geeft de telling weer van geïnstalleerde software waarbij een softwaretag is geactiveerd.|  
|**Software 14B - Computers met specifieke software-id-tag is geactiveerd geïnstalleerd**|Geeft een opsomming weer van alle computers die geïnstalleerde software hebben waarbij een opgegeven software-id-tag is geactiveerd.|  
|**Software 14C - geïnstalleerde software software-identificatielabel op een specifieke computer**|Geeft een opsomming weer van alle geïnstalleerde software waarbij een opgegeven software-id-tag is geactiveerd op een opgegeven computer.|  

### <a name="client-push"></a>Clientpush  

|Rapportnaam|Beschrijving|  
|-----------------|-----------------|  
|**Details van status van clientpushinstallatie**|Geeft informatie weer over het clientpushinstallatieproces voor alle sites.|  
|**Statusdetails van de clientpushinstallatie voor een opgegeven site**|Geeft informatie weer over het clientpushinstallatieproces voor een opgegeven site.|  
|**Samenvatting van status van clientpushinstallatie**|Geeft samenvatting weer over het clientpushinstallatieproces voor alle sites.|  
|**Status van clientpushinstallatie voor een opgegeven site**|Geeft samenvatting weer over het clientpushinstallatieproces voor een opgegeven site.|  

### <a name="client-status"></a>Clientstatus  

|Rapportnaam|Beschrijving|  
|-----------------|-----------------|  
|**Clientherstel**|Geeft details weer over clientherstelacties voor een verzameling die u opgeeft.|  
|**Clientherstel**|Geeft een samenvatting weer over clientherstelacties voor een opgegeven verzameling.|  
|**Geschiedenis van clientstatus**|Geeft een historisch overzicht weer van de algemene clientstatus in de site.|  
|**Samenvatting van clientstatus**|Geeft de clientcontroleresultaten weer van actieve clients voor een opgegeven verzameling.|  
|**Clienttijd voor aanvraagbeleid**|Geeft het percentage clients weer dat in de afgelopen 30 dagen ten minste één maal beleid heeft gevraagd. Elke dag staat voor een percentage van het totaal aantal clients dat beleid heeft aangevraagd sinds de eerste dag in de cyclus.|  
|**Controleer de gegevens van clients met mislukte client**|Geeft details weer over clients waarbij de clientcontrole is mislukt voor een opgegeven verzameling.|  
|**Inactieve clients details**|Geeft een gedetailleerde lijst weer van inactieve clients voor een bepaalde verzameling.|  

### <a name="company-resource-access"></a>Toegang tot de bedrijfsresources  

|Rapportnaam|Beschrijving|  
|-----------------|-----------------|  
|**Geschiedenis van certificaatuitgifte**|Geeft de geschiedenis van certificaten weer die door het certificaatregistratiepunt voor het opgegeven datumbereik zijn uitgegeven aan gebruikers en apparaten.|  
|**Lijst met activa per certificaatuitgiftestatus**|Geeft een lijst weer van apparaten of gebruikers in een opgegeven certificaatuitgiftestatus na de evaluatie van een opgegeven certificaatprofiel.|  
|**Lijst met activa met certificaten die bijna verlopen**|Geeft de apparaten of gebruikers weer met certificaten die op of voor de opgegeven datum vervallen.|  

### <a name="compliance-and-settings-management"></a>Compatibiliteit en instellingen beheren  

|Rapportnaam|Beschrijving|  
|-----------------|-----------------|  
|**Compatibiliteitsgeschiedenis van een configuratiebasislijn**|Geeft de geschiedenis weer van de wijzigingen in compatibiliteit van een configuratiebasislijn voor het opgegeven datumbereik.|  
|**Compatibiliteitsgeschiedenis van een configuratie-item**|Geeft de geschiedenis weer van de wijzigingen in compatibiliteit van een configuratie-item voor het opgegeven datumbereik.|  
|**Details van compatibele regels van configuratie-items in een configuratiebasislijn voor een asset**|Geeft informatie weer over de regels die compatibel zijn bevonden voor een opgegeven configuratie-item voor een opgegeven apparaat of gebruiker.|  
|**Details van conflicterende regels van configuratie-items in een configuratiebasislijn voor een asset**|Geeft informatie weer over regels in een configuratie-item dat is geïmplementeerd voor een opgegeven gebruiker of apparaat en dat conflicteert met andere regels in hetzelfde of een ander geïmplementeerd configuratie-item.|  
|**Details van fouten van configuratie-items in een configuratiebasislijn voor een asset**|Geeft informatie weer over fouten die zijn gegenereerd door een opgegeven configuratie-item voor een opgegeven apparaat of gebruiker.|  
|**Details van niet-compatibele regels van configuratie-items in een configuratiebasislijn voor een asset**|Geeft informatie weer over regels die niet compatibel zijn bevonden voor een opgegeven configuratie-item voor een opgegeven apparaat of gebruiker.|  
|**Details van herstelde regels van configuratie-items in een configuratiebasislijn voor een asset**|Geeft informatie weer over regels die zijn hersteld door een opgegeven configuratie-item voor een opgegeven apparaat of gebruiker.|  
|**Lijst van assets op compatibiliteitsstatus voor een configuratie-item in een configuratiebasislijn**|Geeft de apparaten of gebruikers weer in een opgegeven compatibiliteitsstatus na de evaluatie van een opgegeven configuratie-item.|  
|**Lijst van assets op compatibiliteitsstatus voor een configuratiebasislijn**|Geeft de apparaten of gebruikers weer in een opgegeven compatibiliteitsstatus na de evaluatie van een opgegeven configuratiebasislijn.|  
|**Lijst met regels die conflicteren met een opgegeven regel voor een asset**|Geeft een lijst weer van regels die conflicteren met een opgegeven regel voor een configuratie-item dat is geïmplementeerd op een opgegeven apparaat.|  
|**Lijst met onbekende assets voor een configuratiebasislijn**|Geeft een lijst weer van apparaten of gebruikers die nog geen compatibiliteitsgegevens hebben gerapporteerd voor een opgegeven configuratiebasislijn.|  
|**Lijst met onbekende assets voor een configuratie-item**|Geeft een lijst weer van apparaten of gebruikers die nog geen compatibiliteitsgegevens hebben gerapporteerd voor een opgegeven configuratie-item.|  
|**Regels en fouten van configuratie-items in een configuratiebasislijn voor een asset**|Geeft een samenvatting weer van de compatibiliteitsstatus van regels, en eventuele instellingsfouten voor een opgegeven configuratie-item dat is geïmplementeerd voor een opgegeven apparaat of gebruiker.|  
|**Samenvatting van compatibiliteit op configuratiebasislijn**|Geeft een samenvatting weer van de algemene compatibiliteit van geïmplementeerde configuratiebasislijnen in de hiërarchie.|  
|**Samenvatting van compatibiliteit op configuratie-items voor een configuratiebasislijn**|Geeft een samenvatting weer van de compatibiliteit van configuratie-items in een opgegeven configuratiebasislijn.|  
|**Samenvatting van naleving per configuratiebeleid**|Geeft een samenvatting van de naleving van configuratiebeleid.|  
|**Samenvatting van compatibiliteit voor een configuratiebasislijn voor een verzameling**|Geeft een samenvatting weer van de algemene compatibiliteit van een opgegeven configuratiebasislijn die is geïmplementeerd op een opgegeven verzameling.|  
|**Lijst met niet-compatibele Apps en apparaten voor een opgegeven gebruiker**|Bevat informatie over gebruikers en apparaten die apps hebben geïnstalleerd die niet compatibel zijn met een beleid dat u hebt opgegeven.|  
|**Overzicht van gebruikers met niet-compatibele Apps**|Bevat informatie over gebruikers die apps hebben geïnstalleerd die niet compatibel zijn met een beleid dat u hebt opgegeven.|  
|**Acceptatie van voorwaarden**|Geeft de voorwaarden weer en de versie die door elke gebruiker is geaccepteerd.|  

### <a name="device-management"></a>Apparaatbeheer  

|Rapportnaam|Beschrijving|  
|-----------------|-----------------|  
|**Alle clients van mobiele apparaten**|Geeft informatie weer over clients voor alle mobiele apparaten Apparaten die worden beheerd door de Exchange Server-connector, zijn niet opgenomen.|  
|**Certificaatproblemen op mobiele apparaten die worden beheerd door Configuration Manager-client voor Windows CE en die zijn beschadigd**|Geeft gedetailleerde informatie over certificaatproblemen op mobiele apparaten die worden beheerd door Configuration Manager-client voor Windows CE.|  
|**Mislukte clientimplementaties voor mobiele apparaten die worden beheerd door Configuration Manager-client voor Windows CE**|Geeft gedetailleerde informatie over mislukte implementaties voor mobiele apparaten die worden beheerd door Configuration Manager-client voor Windows CE.|  
|**Clientimplementatiestatus voor mobiele apparaten die worden beheerd door Configuration Manager-client voor Windows CE**|Geeft informatie weer over de status van mobiele apparaten die worden beheerd door Configuration Manager-client voor Windows CE.|  
|**Geslaagde clientimplementaties voor mobiele apparaten die worden beheerd door Configuration Manager-client voor Windows CE**|Geeft gedetailleerde informatie over geslaagde implementaties voor mobiele apparaten die worden beheerd door Configuration Manager-client voor Windows CE.|  
|**Communicatieproblemen op mobiele apparaten die worden beheerd door Configuration Manager-client voor Windows CE en die zijn beschadigd**|Dit rapport bevat gedetailleerde informatie over communicatieproblemen op mobiele apparaten die worden beheerd door Configuration Manager-client voor Windows CE.|  
|**Status van naleving voor mobiele apparaten die worden beheerd door de Exchange Server-connector**|Geeft een samenvatting weer van de compatibiliteitsstatus met het standaard Exchange ActiveSync-postvakbeleid voor de mobiele apparaten die worden beheerd door de Exchange Server-connector.|  
|**Telling van mobiele apparaten op weergave-instellingen**|Dit rapport bevat het aantal van mobiele apparaten op weergave-instellingen.|  
|**Telling van mobiele apparaten op besturingssysteem**|Geeft het aantal mobiele apparaten weer op het besturingssysteem.|  
|**Telling van mobiele apparaten op programmageheugen**|Geeft het aantal mobiele apparaten weer op programmageheugen.|  
|**Telling van mobiele apparaten op opslaggeheugenconfiguraties**|Aantal mobiele apparaten op opslaggeheugenconfiguraties|  
|**Statusinformatie voor mobiele apparaten die worden beheerd door Configuration Manager-client voor Windows CE**|Geeft gedetailleerde statusinformatie voor mobiele apparaten die worden beheerd door Configuration Manager-client voor Windows CE.|  
|**Statussamenvatting voor mobiele apparaten die worden beheerd door Configuration Manager-client voor Windows CE**|Geeft een samenvatting weer van de status voor mobiele apparaten die worden beheerd door Configuration Manager-client voor Windows CE.|  
|**Inactieve mobiele apparaten die worden beheerd door de Exchange Server-connector**|Geeft de mobiele apparaten weer die worden beheerd door de Exchange Server-connector en die een opgegeven aantal dagen geen verbinding hebben gemaakt met Exchange Server.|  
|**Lijst met apparaten die per gebruiker in Microsoft Intune zijn ingeschreven**|Geeft alle apparaten die per gebruiker zijn ingeschreven bij Microsoft Intune weer.|  
|**Lijst met apparaten op voorwaardelijke toegangsstatus**|Geeft informatie weer over de huidige naleving en de status van voorwaardelijke toegang van apparaten. U kunt dit rapport gebruiken met beleidsregels voor voorwaardelijke toegang. Dit rapport is beschikbaar vanaf versie 1602 van Configuration Manager.|  
|**Naleving van voorwaardelijke toegang voor gebruiker**|Biedt gedetailleerde compatibiliteitsinformatie voor voorwaardelijke toegang over een specifieke gebruiker, met inbegrip van de apparaatnaam en het platform, of het apparaat compatibel is, en wanneer het apparaat voor het laatst is geëvalueerd. Dit rapport is beschikbaar vanaf versie 1602 van Configuration Manager.|  
|**Lokale-clientproblemen op mobiele apparaten die worden beheerd door Configuration Manager-client voor Windows CE en die zijn beschadigd**|Dit rapport bevat gedetailleerde informatie over lokale-clientproblemen op mobiele apparaten die worden beheerd door Configuration Manager-client voor Windows CE.|  
|**Informatie over mobiele-apparaatclient**|Geeft informatie weer over de mobiele apparaten waarop de Configuration Manager-client geïnstalleerd is. U kunt dit rapport gebruiken om te controleren welke mobiele apparaten kunnen communiceren met een beheerpunt.|  
|**Compatibiliteitsdetails voor mobiele apparaten voor de Exchange Server-connector**|Geeft compatibiliteitsdetails voor mobiele apparaten voor een standaard Exchange ActiveSync-postvakbeleid dat is geconfigureerd met behulp van de Exchange Server-connector.|  
|**Mobiele apparaten op besturingssysteem**|Geeft de mobiele apparaten weer op besturingssysteem.|  
|**Mobiele apparaten die opengebroken of geroot zijn**|Geeft de mobiele apparaten weer die zijn opengebroken of geroot.|  
|**Mobiele apparaten die niet beheerd zijn omdat ze zijn geregistreerd maar niet toewijzen aan een site**|Geeft de mobiele apparaten die registratie bij Configuration Manager voltooid en een certificaat hebben, maar kan de sitetoewijzing voltooien.|  
|**Mobiele apparaten met een specifieke hoeveelheid vrij programmageheugen**|Geeft alle mobiele apparaten weer met een specifieke hoeveelheid vrij programmageheugen.|  
|**Mobiele apparaten met een specifieke hoeveelheid vrij verwijderbaar geheugen**|Geeft alle mobiele apparaten weer met een specifieke hoeveelheid vrij verwijderbaar geheugen.|  
|**Mobiele apparaten met problemen met de vernieuwing van certificaat**|Geeft de geregistreerde apparaten weer waarvan het verlengen van het certificaat is mislukt. Als het certificaat niet wordt verlengd vóór de verloopperiode, zijn de mobiele apparaten onbeheerd.|  
|**Mobiele apparaten met weinig vrij programmageheugen (minder dan opgegeven aantal KB vrij)**|Geeft de mobiele apparaten weer waarvoor het programmageheugen lager is dan een opgegeven grootte in KB.|  
|**Mobiele apparaten met weinig vrij verwijderbaar geheugen (minder dan opgegeven aantal KB vrij)**|Geeft de mobiele apparaten weer waarvoor het verwijderbare geheugen lager is dan een opgegeven grootte in KB.|  
|**Aantal apparaten dat per gebruiker in Windows Intune zijn ingeschreven**|Dit rapport bevat gebruikers voor de Microsoft Intune-abonnement en het totale aantal apparaten geregistreerd voor elke gebruiker.|  
|**Aanvraag voor wissen in behandeling voor mobiele apparaten**|Geeft de verzoeken om te wissen weer die in behandeling zijn voor mobiele apparaten.|  
|**Recent geregistreerde en toegewezen mobiele apparaten**|Hiermee geeft u mobiele apparaten die recent zijn geregistreerd met Configuration Manager en is toegewezen aan een site.|  
|**Recent gewiste mobiele apparaten**|Geeft de mobiele apparaten weer die zijn recent zijn gewist.|  
|**Samenvatting van instellingen voor mobiele apparaten die worden beheerd door de Exchange Server-connector**|Geeft het aantal mobiele apparaten weer dat de instellingen toepast voor elk standaard Exchange ActiveSync-postvakbeleid dat wordt beheerd door de Exchange Server-connector.|  
|**Gedetailleerde Status van Windows RT-Sideloading-codes**|Geeft gedetailleerde statusinformatie weer voor een opgegeven Windows RT-sideloading-code|  
|**Samenvatting van Windows RT-Sideloading-codes**|Geeft de status weer van Windows RT sideloading-codes.|  

### <a name="driver-management"></a>Stuurprogrammabeheer  

|Rapportnaam|Beschrijving|  
|-----------------|-----------------|  
|**Alle stuurprogramma 's**|Geeft een lijst van alle stuurprogramma’s weer.|  
|**Alle stuurprogramma's voor een specifiek platform**|Geeft alle stuurprogramma's voor een opgegeven platform weer.|  
|**Alle stuurprogramma's in een specifieke opstartinstallatiekopie**|Geeft alle stuurprogramma's in een opgegeven installatiekopie weer.|  
|**Alle stuurprogramma's in een specifieke categorie**|Geeft alle stuurprogramma's in een opgegeven categorie weer.|  
|**Alle stuurprogramma's in een specifiek pakket**|Geeft alle stuurprogramma's in een opgegeven pakket weer.|  
|**Categorieën voor een specifiek stuurprogramma**|Geeft de categorieën voor een opgegeven stuurprogramma weer.|  
|**Computers die niet zijn geslaagd voor het installeren van stuurprogramma's voor een specifieke verzameling**|Geeft computers weer waarop geen stuurprogramma's konden worden geïnstalleerd voor een opgegeven verzameling.|  
|**Stuurprogrammacatalogus die overeenkomt met een rapport voor een specifieke verzameling**|Geeft de stuurprogrammacatalogus weer die overeenkomt met een rapport voor een opgegeven verzameling.|  
|**Stuurprogrammacatalogus die overeenkomt met een rapport voor een specifieke computer**|Geeft de stuurprogrammacatalogus weer die overeenkomt met een rapport voor een opgegeven computer.|  
|**Stuurprogrammacatalogus die overeenkomt met een rapport voor een specifiek apparaat op een specifieke computer**|Geeft de stuurprogrammacatalogus weer die overeenkomt met een rapport voor een opgegeven apparaat op een opgegeven computer|  
|**Stuurprogrammacatalogus die overeenkomt met een rapport voor computers in een specifieke verzameling met een specifiek apparaat**|Geeft een stuurprogrammacatalogus weer die overeenkomt met een rapport voor computers in een specifieke verzameling met een specifiek apparaat.|  
|**Stuurprogramma's die niet konden worden geïnstalleerd op een specifieke computer**|Geeft de stuurprogramma's weer die niet konden worden geïnstalleerd op een opgegeven computer.|  
|**Ondersteunde platforms voor een specifiek stuurprogramma**|Geeft ondersteunde platforms weer voor een opgegeven stuurprogramma|  

### <a name="endpoint-protection"></a>Endpoint Protection  

|Rapportnaam|Beschrijving|  
|-----------------|-----------------|  
|**Activiteitenrapport tegen malware**|Geeft een overzicht van activiteit tegen malware.|  
|**Antimalware algemene status en geschiedenis**|Geeft de algemene status en geschiedenis weer van antimalware.|  
|**Details van de computer schadelijke software**|Geeft details weer over een opgegeven computer, en een lijst met de malware die erop is aangetroffen.|  
|**Geïnfecteerde computers**|Geeft een lijst weer van computers waarop een opgegeven bedreiging is gedetecteerd.|  
|**Meest voorkomende gebruikers op bedreigingen**|Geeft de lijst weer met de gebruikers met het hoogste aantal gedetecteerde bedreigingen.|  
|**Lijst met bedreigingen voor gebruiker**|Geeft een lijst met bedreigingen weer voor een opgegeven gebruikersaccount.|  

### <a name="hardware---cd-rom"></a>Hardware – CD-ROM  

|Rapportnaam|Beschrijving|  
|-----------------|-----------------|  
|**Cd-romstations voor een specifieke computer**|Geeft informatie weer over de cd-romstations op een opgegeven computer.|  
|**Computers voor een specifieke cd-romfabrikant**|Geeft een lijst weer met computers met een cd-romstation van een door u opgegeven fabrikant.|  
|**Aantal cd-romstations per fabrikant**|Geeft het aantal cd-romstations weer dat is geïnventariseerd per fabrikant.|  
|**Geschiedenis - cd-romgeschiedenis voor een specifieke computer**|Geeft de geïnventariseerde cd-romgeschiedenis voor een opgegeven computer weer.|  

### <a name="hardware---disk"></a>Hardware – schijf  

|Rapportnaam|Beschrijving|  
|-----------------|-----------------|  
|**Computers met a specifieke vasteschijfgrootte**|Geeft een lijst weer van computers met een opgegeven vasteschijfgrootte.|  
|**Computers met weinig vrije ruimte (minder dan opgegeven percentage vrij)**|Geeft een lijst weer van computers in een opgegeven verzameling die minder dan de opgegeven beschikbare schijfruimte hebben.|  
|**Computers met weinig vrije ruimte (minder dan opgegeven aantal MB vrij)**|Geeft een lijst weer van computers en schijven met weinig schijfruimte. De grootte van de te controleren vrije ruimte is opgegeven in MB.|  
|**Fysieke schijfconfiguraties tellen**|Geeft het aantal harde schijven weer dat is geïnventariseerd op schijfcapaciteit.|  
|**Schijfinformatie voor een specifieke computer - logische schijven**|Geeft een samenvatting weer van informatie over logische schijven op een opgegeven computer.|  
|**Schijfinformatie voor een specifieke computer - partities**|Geeft een samenvatting weer van informatie over schijfpartities op een opgegeven computer.|  
|**Schijfinformatie voor een specifieke computer - fysieke schijven**|Geeft een samenvatting weer van informatie over fysieke schijven op een opgegeven computer.|  
|**Geschiedenis - geschiedenis van logischeschijfruimte voor een specifieke computer**|Geeft de inventarisgeschiedenis weer voor logischeschijfstations op een opgegeven computer.|  

### <a name="hardware---general"></a>Hardware - algemeen  

|Rapportnaam|Beschrijving|  
|-----------------|-----------------|  
|**Computerinformatie voor een specifieke computer**|Geeft de computerinformatie weer voor een opgegeven computer|  
|**Computers in een specifieke werkgroep of domein**|Geeft een lijst weer van computers in een opgegeven werkgroep of domein.|  
|**Inventarisatieklassen die zijn toegewezen aan een specifieke verzameling**|Geeft een lijst weer van de inventarisatieklassen die zijn toegewezen aan een opgegeven verzameling.|  
|**Inventarisatieklassen die zijn ingeschakeld op een specifieke computer**|Geeft de inventarisatieklassen weer die zijn ingeschakeld op een opgegeven computer.|  

### <a name="hardware---memory"></a>Hardware – geheugen  

|Rapportnaam|Beschrijving|  
|-----------------|-----------------|  
|**Computers waarbij het fysieke geheugen is gewijzigd**|Geeft een lijst met computers weer waarbij de hoeveelheid RAM is gewijzigd sinds de laatste inventarisatiecyclus.|  
|**Computers met een specifieke hoeveelheid geheugen**|Geeft een lijst weer met computers met een opgegeven hoeveelheid RAM (totaal fysiek geheugen afgerond naar het dichtstbijzijnde aantal MB).|  
|**Computers met weinig geheugen (minder dan of gelijk aan opgegeven aantal MB)**|Geeft een lijst met computers weer die weinig geheugen hebben  De hoeveelheid te controleren geheugen is opgegeven in MB.|  
|**Geheugenconfiguraties tellen**|Geeft het aantal computers weer dat is geïnventariseerd op hoeveelheid RAM.|  
|**Geheugeninformatie voor een specifieke computer**|Geeft een samenvatting weer van informatie over het geheugen op een opgegeven computer.|  

### <a name="hardware---modem"></a>Hardware – Modem  

|Rapportnaam|Beschrijving|  
|-----------------|-----------------|  
|**Computers voor een specifieke modemfabrikant**|Geeft een lijst weer van computers met een modem van een opgegeven fabrikant.|  
|**Modems tellen op fabrikant**|Geeft het aantal modems weer dat is geïnventariseerd voor elke modemfabrikant.|  
|**Modeminformatie voor een specifieke computer**|Geeft samenvattingsinformatie weer over het modem op een opgegeven computer.|  

### <a name="hardware---network-adapter"></a>Hardware – netwerkadapter  

|Rapportnaam|Beschrijving|  
|-----------------|-----------------|  
|**Computers met een specifieke netwerkadapter**|Geeft een lijst weer van computers met een opgegeven netwerkadapter.|  
|**Netwerkadapters tellen op type**|Geeft het aantal geïnventariseerde netwerkadapterkaarten weer van elk type.|  
|**Netwerkadapterinformatie voor een specifieke computer**|Geeft informatie weer over de netwerkadapters die zijn geïnstalleerd op een opgegeven computer.|  

### <a name="hardware---processor"></a>Hardware – Processor  

|Rapportnaam|Beschrijving|  
|-----------------|-----------------|  
|**Computers voor een specifieke processorsnelheid**|Geeft een lijst weer van computers met een processor met een opgegeven snelheid.|  
|**Computers met een snelle processor (groter dan of gelijk zijn aan een opgegeven kloksnelheid)**|Geeft een lijst weer met computers met een processor die sneller is dan de opgegeven snelheid.|  
|**Computers met een trage processor (kleiner dan of gelijk zijn aan een opgegeven kloksnelheid)**|Geeft een lijst weer van computers met een processor die even snel als of trager dan een opgegeven kloksnelheid zijn.|  
|**Processorsnelheden tellen**|Geeft het aantal computers weer dat is geïnventariseerd op processorsnelheid.|  
|**Processorinformatie voor een specifieke computer**|Geeft informatie weer over de processors die zijn geïnstalleerd op een opgegeven computer.|  

### <a name="hardware---scsi"></a>Hardware – SCSI  

|Rapportnaam|Beschrijving|  
|-----------------|-----------------|  
|**Computers met een specifieke SCSI-kaart type**|Geeft een lijst weer van computers met een opgegeven type SCSI-kaart.|  
|**Aantal SCSI-kaarttypen**|Geeft het aantal geïnventariseerde SCSI-kaarten weer op kaarttype.|  
|**SCSI-kaartinformatie voor een specifieke computer**|Geeft informatie weer over de SCSI-kaarten die zijn geïnstalleerd op een opgegeven computer.|  

### <a name="hardware---sound-card"></a>Hardware – geluidskaart  

|Rapportnaam|Beschrijving|  
|-----------------|-----------------|  
|**Computers met een specifieke geluidskaart**|Geeft een lijst weer van computers met een opgegeven geluidskaart.|  
|**Geluidskaarten tellen**|Geeft het aantal computers weer dat is geïnventariseerd op elk type geluidskaart.|  
|**Geluidskaarten op een specifieke computer**|Geeft samenvattingsinformatie weer over de geluidskaarten op een opgegeven computer.|  

### <a name="hardware---video-card"></a>Hardware – videokaart  

|Rapportnaam|Beschrijving|  
|-----------------|-----------------|  
|**Computers met een specifieke videokaart**|Geeft een lijst weer van computers met een opgegeven videokaart.|  
|**Videokaarten op type tellen**|Geeft een lijst weer met alle videokaarten die op computers zijn geïnstalleerd, samen met het aantal van elk type videokaart.|  
|**Videokaartinformatie voor een specifieke computer**|Geeft samenvattingsinformatie weer over de videokaarten die zijn geïnstalleerd op een opgegeven computer.|  

### <a name="migration"></a>Migratie  

|Rapportnaam|Beschrijving|  
|-----------------|-----------------|  
|**Clients in uitsluitingslijst**|Geeft clients weer die zijn uitgesloten van migratie.|  
|**Afhankelijkheid van een Configuration manager-verzameling**|Geeft de objecten weer die afhankelijk zijn van een verzameling van de bronhiërarchie|  
|**Eigenschappen migratietaak**|In dit rapport wordt de inhoud weer van de opgegeven migratietaak weergegeven.|  
|**Migratietaken**|In dit rapport wordt de lijst met migratietaken weergegeven.|  
|**Objecten die niet konden migreren**|Geeft een lijst weer met objecten die niet konden migreren tijdens de laatste poging.|  

### <a name="network"></a>Netwerk  

|Rapportnaam|Beschrijving|  
|-----------------|-----------------|  
|**Aantal IP-addressen per subnet**|Geeft het aantal IP-adressen weer dat voor elk IP-subnet is geïnventariseerd.|  
|**IP - alle subnetten op subnetmasker**|Geeft een lijst weer met IP-subnetten en subnetmaskers.|  
|**IP - Computers in een specifiek subnet**|Geeft een lijst weer van computers en IP-informatie voor een opgegeven IP-subnet.|  
|**IP - informatie voor een specifieke computer**|Geeft samenvattingsinformatie weer over het IP op een opgegeven computer.|  
|**IP - informatie voor een specifiek IP-adres**|Geeft samenvattingsinformatie weer over een opgegeven IP-adres.|  
|**MAC - Computers voor een specifiek MAC-adres**|Geeft de computernaam en het IP-adres weer van computers dat het opgegeven MAC-adres hebben.|  

### <a name="network-access-protection"></a>Network Access Protection  

|Rapportnaam|Beschrijving|  
|-----------------|-----------------|  
|**Vergelijking van software-updates geïnstalleerd door software-update-implementaties en NAP-herbemiddeling.**|Geeft een vergelijkingssamenvatting weer van software-updates die zijn geïnstalleerd door software-update-implementaties en NAP-herbemiddeling|  
|**Frequentie een computer is in herbemiddeling binnen een opgegeven periode**|Dit rapport geeft weer hoe vaak een computer is hersteld binnen een opgegeven periode.|  
|**Lijst met computers waarop geïnstalleerd via herbemiddeling gedurende een bepaalde periode een specifieke software-update**|Geeft een lijst weer met computers waarop tijdens een opgegeven periode (dagen) een opgegeven software-update is geïnstalleerd via herbemiddeling.|  
|**Lijst met computers die niet-compatibel op basis van geselecteerde software-updates**|Geef een lijst weer voor elke computer die niet compatibel is op basis van de geselecteerde software-updates.|  
|**Lijst met computers waarop NAP-service niet kan worden gedetecteerd**|Geeft een lijst weer met computers waarop NAP-service niet is gedetecteerd.|  
|**Lijst met computers waarvoor NAP**|Geeft een lijst weer van computers waarop de NAP-service niet wordt uitgevoerd of de status onbekend is.|  
|**Lijst met beleidsregels voor Network Access Protection**|Geeft een lijst weer van beleidsregels voor netwerktoegangsbeveiliging met de bijbehorende ingangsdatums.|  
|**Lijst met niet-compatibele computers in herbemiddeling vanaf laatste polling-interval**|Geeft een lijst weer van niet-compatibele computers in herbemiddeling met de laatste bekende evaluatietijden.|  
|**Lijst met niet-compatibele computers in herbemiddeling binnen een opgegeven periode**|Geeft de lijst weer met niet-compatibele computers in herbemiddeling binnen een opgegeven tijdsduur.|  
|**Lijst met herbemiddelingen voor een opgegeven periode**|Geeft een lijst weer met mislukte herbemiddelingen voor een opgegeven aantal dagen.|  
|**Lijst met software-updates die zijn geïnstalleerd via herbemiddeling**|Geeft de lijst weer met software-updates die zijn geïnstalleerd via herbemiddeling voor een opgegeven periode.|  
|**Samenvatting van niet-compatibele computers in herbemiddeling vanaf laatste polling-interval**|Geeft een samenvatting weer van niet-compatibele computers in herbemiddeling vanaf laatste polling-interval.|  
|**Samenvatting van niet-compatibele computers in herbemiddeling binnen een opgegeven periode**|Geeft een samenvatting weer van niet-compatibele computers in herbemiddeling binnen een opgegeven tijdsduur.|  

### <a name="operating-system"></a>Besturingssysteem  

|Rapportnaam|Beschrijving|  
|-----------------|-----------------|  
|**Versiegeschiedenis van computer-besturingssysteem**|Geeft de inventarisgeschiedenis weer voor het besturingssysteem op een opgegeven computer.|  
|**Computers met een specifiek besturingssysteem**|Geeft computers weer met een opgegeven besturingssysteem.|  
|**Computers met een specifiek besturingssysteem en servicepack**|Geeft computers weer met een specifiek besturingssysteem en servicepack.|  
|**Versies besturingssystemen tellen**|Geeft het aantal computers weer dat is geïnventariseerd op besturingssysteem.|  
|**Besturingssystemen en servicepakketten tellen**|Geeft het aantal computers weer dat is geïnventariseerd op combinaties van besturingssysteem en service pack.|  
|**Services - Computers waarop een specifieke service wordt uitgevoerd**|Geeft een lijst weer van computers waarop een opgegeven service wordt uitgevoerd.|  
|**Services - Computers waarop Remote Access Server wordt uitgevoerd**|Geeft een lijst weer van computers waarop Remote Access Server wordt uitgevoerd.|  
|**Service - Services voor een specifieke computer**|Geeft samenvattingsinformatie weer over de services op een opgegeven computer.|  
|**Windows Server-computers**|Geeft een lijst met computers weer waarop Windows Server-besturingssystemen worden uitgevoerd.|  

### <a name="out-of-band-management"></a>Buiten-bandbeheer  

|Rapportnaam|Beschrijving|  
|-----------------|-----------------|  
|**Computers met buiten-bandbeheercontrollers**|Geeft een lijst weer van computers met buiten-bandbeheercontrollers.|  
|**Buiten-band management console-activiteit**|Geeft een lijst weer van statusberichten die console-activiteit in out-of-boundbeheer identificeren.|  
|**Status van client buiten-bandinrichting management**|Geeft een lijst weer met computers die zijn ingericht voor buiten-bandbeheer.|  

### <a name="power-management"></a>Energiebeheer  

|Rapportnaam|Beschrijving|  
|-----------------|-----------------|  
|**Energiebeheer - computeractiviteit**|Geeft een grafiek weer met monitor-, computer- en gebruikersactiviteit voor een opgegeven verzameling gedurende een opgegeven periode.|  
|**Energiebeheer - computeractiviteit per computer**|Geeft een grafiek weer met monitor-, computer- en gebruikersactiviteit voor een opgegeven computer op een opgegeven datum.|  
|**Energiebeheer - details van computeractiviteit**|Geeft een lijst weer van de slaapstandmogelijkheden van computers in de opgegeven verzameling voor een opgegeven datum en tijd.|  
|**Energiebeheer - details van de Computer**|Geeft gedetailleerde informatie weer over de energiemogelijkheden, energie-instellingen en energiebeheerschema's die worden toegepast op een opgegeven computer.|  
|**Energiebeheer - Computer geeft geen details**|Geeft een lijst weer van computers waar waarvoor op een opgegeven datum en tijdstip geen stroomactiviteit is gerapporteerd.|  
|**Energiebeheer - Computers die zijn uitgesloten**|Geef een lijst weer van computers die zijn uitgesloten van het energiebeheerschema.|  
|**Energiebeheer - Computers met meerdere energiebeheerschema 's**|Geeft een lijst weer van computers waarop meerdere, conflicterende energiebeheerschema’s zijn toegepast.|  
|**Energiebeheer - energieverbruik**|Geeft het totale maandelijkse energieverbruik weer (in kWh) voor een opgegeven verzameling gedurende een opgegeven periode.|  
|**Energiebeheer - energieverbruik per dag**|Geeft het totale energieverbruik weer (in kWh) voor de afgelopen 31 dagen voor een opgegeven verzameling.|  
|**Energiebeheer - energiekosten**|Geeft de kosten van het totale maandelijkse energieverbruik weer voor een opgegeven verzameling gedurende een opgegeven periode.|  
|**Energiebeheer - energiekosten per dag**|Geeft de kosten van het totale energieverbruik weer voor een opgegeven verzameling gedurende de afgelopen 31 dagen.|  
|**Energiebeheer - gevolgen voor het milieu**|Geeft een grafiek weer met CO2-uitstoot die wordt gegenereerd door een specifieke verzameling gedurende een specifieke periode.|  
|**Energiebeheer - uitwerking op milieu op dag**|Geeft een grafiek weer met CO2-uitstoot die wordt gegenereerd door een specifieke verzameling gedurende de afgelopen 31 dagen.|  
|**Energiebeheer - details van Slapeloosheid computer**|Geeft detailleerde informatie weer over computers die niet in de slaap- of sluimerstand staan binnen een opgegeven periode.|  
|**Energiebeheer - slapeloosheidsrapport**|Geeft een lijst met algemene oorzaken aan waardoor de slaap- of sluimerstand niet kan worden ingeschakeld, en het aantal computers waarop elke oorzaak van toepassing is voor een opgegeven periode.|  
|**Energiebeheer - energiemogelijkheden**|Geeft de mogelijkheden voor energiebeheer weer van computers in de opgegeven verzameling.|  
|**Energiebeheer - energie-instellingen**|Geeft een samengevoegde lijst energie-instellingen weer die worden gebruikt door computers in een opgegeven verzameling.|  
|**Energiebeheer - details van energie-instellingen**|Gebruikt voor verdere informatie weer over computers die zijn opgegeven in de **energiebeheer - energie-instellingen** rapport.|  

### <a name="replication-traffic"></a>Replicatieverkeer  

|Rapportnaam|Beschrijving|  
|-----------------|-----------------|  
|**Replicatieverkeer van globale gegevens Per koppeling (lijndiagram)**|Geeft het totale replicatieverkeer van globale gegevens weer voor een opgegeven koppeling gedurende een opgegeven aantal dagen|  
|**Replicatieverkeer van globale gegevens Per koppeling (cirkeldiagram)**|Geeft het totale replicatieverkeer van globale gegevens weer voor een opgegeven koppeling gedurende een opgegeven aantal dagen|  
|**Hiërarchie van replicatieverkeer per koppeling**|Geeft het totale replicatieverkeer weer voor elke koppeling in de hiërarchie gedurende een opgegeven aantal dagen.|  
|**Hiërarchie Top tien replicatieverkeer groepen Per koppeling (cirkeldiagram)**|Geeft het replicatieverkeer weer voor de top tien van de replicatiegroepen in de gehele hiërarchie, aangegeven door een koppeling.|  
|**Replicatiekoppelingsverkeer**|Geeft het totale replicatieverkeer weer voor alle gegevens gedurende een opgegeven aantal dagen.|  
|**Verkeer van de replicatiegroep per koppeling**|Geeft het netwerkverkeer van de replicatiegroep weer via een opgegeven replicatiekoppeling in de database, gedurende een opgegeven aantal dagen.|  
|**Site gegevens replicatieverkeer Per koppeling (lijndiagram)**|Geeft het totale replicatieverkeer van sitegegevens weer voor een opgegeven koppeling gedurende een opgegeven aantal dagen|  
|**Site gegevens replicatieverkeer Per koppeling (cirkeldiagram)**|Geeft het totale replicatieverkeer van sitegegevens weer voor een opgegeven koppeling gedurende een opgegeven aantal dagen|  
|**Totale hiërarchie van replicatieverkeer (lijndiagram)**|Geeft de verzamelde globale gegevens in de hiërarchie en gegevensreplicatie van de site weer voor elke richting van elke koppeling gedurende een opgegeven aantal dagen.|  
|**Totale hiërarchie van replicatieverkeer (cirkeldiagram)**|Geeft de verzamelde globale gegevens in de hiërarchie en gegevensreplicatie van de site weer voor elke richting van elke koppeling gedurende een opgegeven aantal dagen.|  

### <a name="site---client-information"></a>Site - clientinformatie  

|Rapportnaam|Beschrijving|  
|-----------------|-----------------|  
|**Gedetailleerd rapport van clienttoewijzing**|Geeft gedetailleerde informatie weer over de status van clienttoewijzingen.|  
|**Foutdetails van clienttoewijzing**|Geeft gedetailleerde informatie weer over mislukte clienttoewijzingen.|  
|**Details van status van clienttoewijzing**|Geeft overzichtsinformatie weer over de status van clienttoewijzingen.|  
|**Details van slagen van clienttoewijzing**|Geeft gedetailleerde informatie weer over geslaagde clienttoewijzingen.|  
|**Rapport over fouten clientimplementatie**|Geeft gedetailleerde informatie weer voor clients die niet kunnen worden geïmplementeerd.|  
|**Statusdetails clientimplementatie**|Geeft samenvattingsinformatie weer voor de status van clientinstallaties.|  
|**Rapport over geslaagde clientimplementatie**|Geeft gedetailleerde informatie weer voor clients waarvan de implementatie is geslaagd.|  
|**Clients waarvoor HTTPS-communicatie niet**|Geeft gedetailleerde informatie weer over elke client in een site die de HTTPS Communication Readiness Tool heeft uitgevoerd en waarvan is aangegeven dat deze niet kan communiceren via HTTPS.|  
|**Computers die zijn toegewezen maar niet geïnstalleerd voor een bepaalde site**|Geeft een lijst weer van computers die zijn toegewezen aan een opgegeven site, maar die niet rapporteren aan deze site.|  
|**Computers met een specifieke clientversie van de Configuration Manager**|Geeft een lijst van computers waarop een opgegeven versie van de Configuration Manager-clientsoftware wordt uitgevoerd.|  
|**Telling van clients en protocol gebruikt voor communicatie**|Geeft een samenvatting weer van de communicatiemethoden die door clients worden gebruikt (HTTP of HTTPS).|  
|**Telling van clients toegewezen en geïnstalleerd voor elke site**|Geeft het aantal computers weer dat is toegewezen en geïnstalleerd voor elke site Clients met een netwerklocatie die is gekoppeld aan meerdere sites, worden alleen geteld als geïnstalleerd als ze aan die site rapporteren.|  
|**Telling van clients waarvoor HTTPS-communicatie mogelijk**|Geeft gedetailleerde informatie weer over elke client in een site die de HTTPS Communication Readiness Tool heeft uitgevoerd en waarvan is aangegeven dat deze wel of niet kan communiceren via HTTPS.|  
|**Telling van clients voor elke site**|Geeft het aantal Configuration Manager-clients die zijn geïnstalleerd op sitecode.|  
|**Telling van Configuration Manager-clients op clientversies**|Geeft het aantal computers dat is gedetecteerd door Configuration Manager-clientversie.|  
|**Details van probleem gerapporteerd aan het terugvalstatuspunt voor een opgegeven verzameling**|Geeft gedetailleerde informatie weer voor problemen die worden gerapporteerd door clients in een opgegeven verzameling als aan deze een terugvalstatuspunt is toegewezen.|  
|**Details van probleem gerapporteerd aan het terugvalstatuspunt voor een opgegeven site**|Geeft gedetailleerde informatie weer over problemen die worden gerapporteerd door clients in een opgegeven site als aan deze een terugvalstatuspunt is toegewezen.|  
|**Samenvatting van problemen die zijn gerapporteerd aan het terugvalstatuspunt**|Geeft informatie weer over alle problemen die zijn gerapporteerd door clients als aan deze een terugvalstatuspunt is toegewezen.|  
|**Samenvatting van problemen die zijn gerapporteerd aan het terugvalstatuspunt voor een specifieke verzameling**|Geeft samenvattingsinformatie weer voor problemen die worden gerapporteerd door clients in een opgegeven verzameling als aan deze een terugvalstatuspunt is toegewezen.|  

### <a name="site---discovery-and-inventory-information"></a>Site - detectie en inventarisatie-informatie  

|Rapportnaam|Beschrijving|  
|-----------------|-----------------|  
|**Clients die niet recent hebben gerapporteerd (gedurende een opgegeven aantal dagen)**|Geeft een lijst weer van clients waarvan geen detectiegegevens, hardware-inventarisatie of software-inventarisatie is gerapporteerd gedurende een opgegeven aantal dagen.|  
|**Computers die zijn gedetecteerd door een specifieke site**|Geeft een lijst weer van alle computers die door een specifieke site zijn gedetecteerd en de datum van de recentste detectie.|  
|**Computers die zijn gedetecteerd op detectiemethode**|Geeft een lijst weer met computers die zijn gedetecteerd binnen het opgegeven aantal dagen, en een lijst van de agenten die ze hebben gedetecteerd. Een computer kan meer dan eens in de lijst voorkomen als deze is gedetecteerd door meerdere agents.|  
|**Computers niet recent gedetecteerd (in een opgegeven aantal dagen)**|Geeft een lijst weer met computers die niet recent zijn ontdekt, en geeft weer hoeveel dagen geleden deze zijn ontdekt.|  
|**Computers niet recent zijn geïnventariseerd (in een opgegeven aantal dagen)**|Geeft een lijst met computers weer die niet recent zijn geïnventariseerd, en geeft de laatste keer weer dat deze zijn geïnventariseerd.|  
|**Computers die mogelijk dezelfde unieke Configuration Manager id delen**|Geeft een lijst weer van computers waarvan de naam is veranderd. Een wijziging van naam is kan erop duiden dat een computer een unieke Configuration Manager-id met een andere computer deelt.|  
|**Computers met dubbele MAC-adressen**|Geeft computers weer die een MAC-adres delen.|  
|**Computers in resourcedomeinen of werkgroepen tellen**|Geeft het aantal computers in elk resourcedomein of elke werkgroep weer|  
|**Detectie-informatie voor een specifieke computer**|Geeft een lijst weer van de agents en sites die een opgegeven computer hebben gedetecteerd.|  
|**Inventarisatiedatums voor een specifieke computer**|Geeft de datum en tijd weer waarop voor het laatst een inventarisatie op een opgegeven computer is uitgevoerd.|  

### <a name="site---general"></a>Site - Algemeen  

|Rapportnaam|Beschrijving|  
|-----------------|-----------------|  
|**Computers in een specifieke site**|Geeft een lijst weer van clientcomputers in een opgegeven site.|  
|**Sitestatus voor de hiërarchie**|Geeft de lijst weer van sites in de hiërarchie met siteversie en informatie over de sitestatus.|  
|**Status van Configuration Manager-update in de hiërarchie**|Geeft informatie weer over updates van Configuration Manager-site voor de hiërarchie.|  

### <a name="site---server-information"></a>Site - serverinformatie  

|Rapportnaam|Beschrijving|  
|-----------------|-----------------|  
|**Sitesysteemrollen en sitesysteemservers voor een specifieke site**|Geeft een lijst weer voor de sitesysteemserver en de bijbehorende sitesysteemrollen voor een opgegeven site.|  

### <a name="software---companies-and-products"></a>Software - bedrijven en producten  

|Rapportnaam|Beschrijving|  
|-----------------|-----------------|  
|**Alle geïnventariseerde producten voor een specifieke softwarebedrijf**|Geeft een lijst weer met de geïnventariseerde softwareproducten en versies van een opgegeven bedrijf.|  
|**Alle softwarebedrijven**|Geeft een lijst weer van alle bedrijven die geïnventariseerde software produceren.|  
|**Alle Windows-apps**|Geeft een samenvatting weer van geïnstalleerde Windows-apps, gesorteerd op het aantal exemplaren op basis van zoekcriteria voor de toepassingsnaam, de architectuur of de uitgever.|  
|**Computers met een specifiek product**|Geeft een lijst weer van de computers waarop een opgegeven product is geïnventariseerd, en van de versies van dat product.|  
|**Computers met een specifieke productnaam en versie**|Geeft een lijst weer van de computers waarop een opgegeven versie van een product is geïnventariseerd.|  
|**Computers met specifieke software die is geregistreerd in software**|Geeft een samenvatting weer van alle computers met opgegeven software die is geregistreerd in Software of Programma’s en onderdelen.|  
|**Alle geïnventariseerde producten en versies tellen**|Geeft een lijst weer van de geïnventariseerde softwareproducten en versies en van het aantal computers waar deze op zijn geïnstalleerd.|  
|**Geïnventariseerde producten en versies voor een specifiek product**|Geeft een lijst weer van de geïnventariseerde versies van een opgegeven product en van het aantal computers waar deze op zijn geïnstalleerd.|  
|**Telling van alle exemplaren van software die is geregistreerd met software**|Geeft een samenvatting weer van alle exemplaren van software die is geïnstalleerd en geregistreerd met Software of Programma’s en onderdelen op computers binnen de opgegeven verzameling.|  
|**Telling van exemplaren van specifieke software die is geregistreerd met software**|Geeft een telling weer van exemplaren voor opgegeven softwarepakketten die zijn geïnstalleerd en geregistreerd in Software of Programma’s en onderdelen.|  
|**Installaties van opgegeven Windows-apps**|Dit rapport geeft een lijst weer van alle computers met een opgegeven Windows-app.|  
|**Producten op een specifieke computer**|Geeft een samenvatting weer van de geïnventariseerde softwareproducten en de fabrikanten daarvan op een opgegeven computer.|  
|**Software die is geregistreerd in software op een specifieke computer**|Geeft een samenvatting weer van de software die is geïnstalleerd op een opgegeven computer en die is geregistreerd in Software of Programma’s en onderdelen.|  
|**Windows-apps geïnstalleerd voor de opgegeven gebruiker**|Bevat alle Windows-apps die zijn geïnstalleerd voor de opgegeven gebruiker|  

### <a name="software---files"></a>Software - Bestanden  

|Rapportnaam|Beschrijving|  
|-----------------|-----------------|  
|**Alle geïnventariseerde bestanden voor een specifiek product**|Geeft een samenvatting weer van de geïnventariseerde bestanden die zijn gekoppeld aan een opgegeven softwareproduct.|  
|**Alle geïnventariseerde bestanden op een specifieke computer**|Geeft een samenvatting weer van alle bestanden die zijn geïnventariseerd op een opgegeven computer.|  
|**Software-inventarisatie op twee computers**|Geeft de verschillen weer tussen de software-inventarisatie die is gerapporteerd op twee opgegeven computers.|  
|**Computers met een specifiek bestand**|Geeft een lijst weer van computers met een verzamelde software-inventarisatie voor een opgegeven bestandsnaam. Een computer kan meer dan één keer in de lijst verschijnen als deze meerdere exemplaren van het bestand bevat.|  
|**Computers met een specifieke bestandsnaam tellen**|Geeft het aantal computers weer met een verzamelde software-inventarisatie voor een opgegeven bestand.|  

### <a name="software-distribution---application-monitoring"></a>Softwaredistributie - toepassingscontrole  

|Rapportnaam|Beschrijving|  
|-----------------|-----------------|  
|**Alle toepassingsimplementaties (Geavanceerd)**|Geeft gedetailleerde samenvattingsinformatie weer voor alle software-implementaties.|  
|**Alle toepassingsimplementaties (basis)**|Geeft samenvattingsinformatie weer voor alle software-implementaties.|  
|**Toepassingscompatibiliteit**|Geeft gedetailleerde informatie weer over de compatibiliteit van de opgegeven toepassing binnen de opgegeven verzameling.|  
|**Toepassingsimplementaties per asset**|Geeft toepassingen weer die zijn geïmplementeerd naar een opgegeven apparaat of gebruiker.|  
|**Fouten in toepassingsinfrastructuur**|Geeft de fouten in de toepassingsinfrastructuur weer.  Dit kunnen interne infrastructuurfouten zijn, maar ook fouten als gevolg van ongeldige vereisteregels.|  
|**Gedetailleerde Status toepassingsgebruik**|Geeft gebruiksdetails weer voor geïnstalleerde toepassingen.|  
|**Samenvatting Status toepassingsgebruik**|Geeft een gebruikssamenvatting weer voor geïnstalleerde toepassingen.|  
|**Implementaties van takenreeksen met toepassingen**|Geeft de takenreeksimplementaties weer die een opgegeven toepassing installeren.|  
|**Gebruikersaanvragen voor Android-toepassing**|Geeft de gebruikers weer die hebben gevraagd om installatie van een Android-toepassing.|  
|**iOS-apps met mislukte implementatie (app al geïnstalleerd)**|Hiermee wordt nalevingsinformatie weergegeven voor de geselecteerde iOS-app die u hebt geïmplementeerd als een 'App-pakket voor iOS vanuit de App Store', die is gekoppeld aan een beleid voor het beheer van mobiele toepassingen. Dit rapport wordt gebruikt om gebruikers en apparaten weer te geven waarvoor de app niet kan worden geïnstalleerd omdat deze al handmatig is geïnstalleerd door de gebruiker.|  

### <a name="software-distribution---collections"></a>Softwaredistributie - Verzamelingen  

|Rapportnaam|Beschrijving|  
|-----------------|-----------------|  
|**Alle verzamelingen**|Geeft alle verzamelingen in de hiërarchie weer.|  
|**Alle resources in een specifieke verzameling**|Geeft resources weer in een opgegeven verzameling.|  
|**Onderhoudsvensters die beschikbaar zijn voor een opgegeven client**|Geeft alle onderhoudsvensters weer die van toepassing zijn voor een opgegeven client.|  

### <a name="software-distribution---content"></a>Softwaredistributie - Inhoud  

|Rapportnaam|Beschrijving|  
|-----------------|-----------------|  
|**Alle actieve inhoudsdistributies**|Geeft alle distributiepunten weer waarop op dit moment inhoud wordt geïnstalleerd of verwijderd.|  
|**Alle inhoud**|Geeft alle toepassingen en pakketten op een site weer.|  
|**Alle inhoud op een specifiek distributiepunt**|Geeft alle inhoud weer die momenteel is geïnstalleerd op een opgegeven distributiepunt.|  
|**Alle distributiepunten**|Geeft informatie weer over de distributiepunten voor elke site.|  
|**Alle statusberichten voor een specifiek pakket op een specifiek distributiepunt**|Geeft alle statusberichten weer voor een opgegeven pakket op een opgegeven distributiepunt.|  
|**Distributiestatus van toepassingsinhoud**|Geeft informatie weer over de distributiestatus voor de toepassingsinhoud.|  
|**Toepassingen die zijn gericht aan distributiepuntengroep**|Geeft informatie weer over de toepassingsinhoud die is geïmplementeerd naar een opgegeven distributiepuntengroep.|  
|**Toepassingen die niet gesynchroniseerd op een opgegeven distributiepuntengroep zijn**|Geeft de toepassingen weer waarvoor gekoppelde inhoudsbestanden niet zijn bijgewerkt met de laatste versie op een opgegeven distributiepuntengroep.|  
|**Distributiepuntengroep**|Geeft informatie weer over een opgegeven distributiepuntengroep.|  
|**Distributiepuntgebruik**|Geeft een samenvatting weer van het distributiepuntgebruik per distributiepunt.|  
|**Distributiestatus van specifiek pakket**|Geeft de distributiestatus weer voor opgegeven pakketinhoud op elk distributiepunt.|  
|**Pakketten die gericht zijn op de distributiepuntengroep**|Geeft informatie weer over pakketten die zijn gericht op een opgegeven distributiepuntengroep.|  
|**Pakketten die niet gesynchroniseerd op een opgegeven distributiepuntengroep zijn**|Geeft de pakketten weer waarvoor gekoppelde inhoudsbestanden niet zijn bijgewerkt met de laatste versie op een opgegeven distributiepuntengroep.|  

### <a name="software-distribution---package-and-program-deployment"></a>Softwaredistributie - pakket en programma-implementaties  

|Rapportnaam|Beschrijving|  
|-----------------|-----------------|  
|**Alle implementaties voor een specifiek pakket en programma**|Geeft informatie weer over alle implementaties van een opgegeven pakket en programma.|  
|**Alle pakket- en programma-implementaties**|Geeft alle pakket- en programma-implementaties op deze site weer.|  
|**Alle pakket- en programma-implementaties voor een opgegeven verzameling**|Geeft alle pakket- en programma-implementaties weer voor een opgeven verzameling.|  
|**Alle pakket- en programma-implementaties voor een opgegeven computer**|Geeft alle pakket- en programma-implementaties weer die van toepassing zijn op een opgegeven computer.|  
|**Alle pakket- en programma-implementaties voor een opgegeven gebruiker**|Geeft alle pakket- en programma-implementaties weer voor een opgegeven gebruiker.|  

### <a name="software-distribution---package-and-program-deployment-status"></a>Softwaredistributie - pakket en programma-Implementatiestatus  

|Rapportnaam|Beschrijving|  
|-----------------|-----------------|  
|**Alle pakket- en programma-implementaties met status**|Geeft alle pakket- en programma-implementaties voor de site weer met een samenvattingsstatus van elke implementatie.|  
|**Alle systeemresources voor een opgegeven pakket en programma-implementatie in een opgegeven status**|Geeft een lijst weer van alle resources die een opgegeven status hebben voor een opgegeven pakket- en programma-implementatie.|  
|**Grafiek - pakket en programma voltooiingsstatus implementatie**|Geeft het percentage computers weer waarop het pakket is geïnstalleerd voor elk uur sinds het pakket- en de programma-implementatie is gemaakt. Dit kan worden gebruikt om de gemiddelde tijd bij te houden voor een implementatie van pakket en programma.|  
|**Implementatiestatus van pakket en programma voor een opgegeven client en implementatie**|Geeft de statusberichten weer die zijn gerapporteerd voor een opgegeven computer en pakket- en programma-implementatie.|  
|**Status van een opgegeven pakket en programma-implementatie**|Geeft een samenvatting weer voor een opgegeven pakket- en programma-implementatie.|  

### <a name="software-metering"></a>Softwaremeter  

|Rapportnaam|Beschrijving|  
|-----------------|-----------------|  
|**Alle software-licentiecontroleregels die worden toegepast op deze site**|Geeft een lijst weer met alle regels voor softwarelicentiecontrole op de site.|  
|**Computers waarop een programma met gecontroleerde licentie is geïnstalleerd, maar het programma sinds een opgegeven datum niet hebben uitgevoerd**|Geeft alle computers weer waarop een programma met gecontroleerde licentie is geïnstalleerd, zoals gerapporteerd door de software-inventarisatie, maar die het programma sinds een opgegeven datum niet hebben uitgevoerd.|  
|**Computers waarop een programma met specifieke gecontroleerde licenties is uitgevoerd**|Geeft een lijst weer van computers waarop programma’s zijn uitgevoerd die overeenkomen met de opgegeven softwaremeterregel binnen de opgegeven maand en het opgegeven jaar.|  
|**Gelijktijdig gebruik voor alle programma's met gecontroleerde licenties**|Geeft het maximum aantal gebruikers weer die elk programma met gecontroleerde licenties tegelijkertijd hebben uitgevoerd tijdens de opgegeven maand en het opgegeven jaar.|  
|**Trendgrafiek van gelijktijdig gebruik van een programma met gecontroleerde licenties specifieke**|Geeft het maximum aantal gebruikers weer die het opgegeven programma met gecontroleerde licenties tegelijkertijd hebben uitgevoerd gedurende elke maand van het afgelopen jaar.|  
|**Installatiebasis voor alle programma's met gecontroleerde licenties**|Geeft het aantal computers weer waarop programma's met gecontroleerde licenties zijn geïnstalleerd, zoals gerapporteerd door de software-inventarisatie. Dit rapport vereist dat software-inventarisatie wordt uitgevoerd op de computers met gecontroleerde licenties.|  
|**Voortgang van samenvatting softwarelicentiecontrole**|Geeft de tijd weer waarop de recentst samengevatte licentiecontrolegegevens zijn verwerkt op de siteserver.  Alleen licentiecontrolegegevens die zijn verwerkt vóór deze datums, worden weergegeven in de softwarelicentiecontrolerapporten.|  
|**Samenvatting van gebruik op tijdstip voor een bepaald softwareprogramma van gecontroleerde**|Geeft het gemiddelde gebruik van een bepaald programma weer in de afgelopen negentig dagen, opgedeeld per uur en dag.|  
|**Totaal gebruik voor alle programma's met gecontroleerde licenties**|Geeft het aantal gebruikers weer die programma's hebben uitgevoerd die lokaal overeenkomen met elke softwarelicentiecontroleregel, of met behulp van Terminal Services binnen de opgegeven maand en het opgegeven jaar.|  
|**Totaal gebruik voor alle programma's met gecontroleerde licenties op Windows Terminal Servers**|Geeft het aantal gebruikers weer die programma's hebben uitgevoerd die overeenkomen met elke softwarelicentiecontroleregel met behulp van Terminal Services binnen de opgegeven maand en het opgegeven jaar.|  
|**Analyse van totaal gebruik voor een programma met gecontroleerde licenties specifieke**|Geeft het aantal gebruikers weer die programma's hebben uitgevoerd die lokaal overeenkomen met de opgegeven softwarelicentiecontroleregel, of met behulp van Terminal Services gedurende elke maand van het afgelopen jaar.|  
|**Analyse van totaal gebruik voor een programma met gecontroleerde licenties specifieke op Windows Terminal Servers**|Geeft het aantal gebruikers weer die programma's hebben uitgevoerd die overeenkomen met de opgegeven softwarelicentiecontroleregel met behulp van Terminal Services gedurende elke maand van het afgelopen jaar.|  
|**Gebruikers die een bepaald softwareprogramma licenties hebben uitgevoerd**|Geeft een lijst weer van gebruikers die programma’s hebben uitgevoerd die overeenkomen met de opgegeven softwaremeterregel binnen de opgegeven maand en het opgegeven jaar.|  

### <a name="software-updates---a-compliance"></a>Software-Updates - een compatibiliteitsstatus  

|Rapportnaam|Beschrijving|  
|-----------------|-----------------|  
|**Compatibiliteit 1 - algemene compatibiliteit**|Geeft de algemene compatibiliteitsgegevens weer voor een software-updategroep.|  
|**Compatibiliteit 2 - specifieke software-update**|Geeft de compatibiliteitsgegevens weer voor een opgegeven software-update.|  
|**Compatibiliteit 3 - updategroep (per update)**|Geeft de compatibiliteitsgegevens weer voor software-updates die zijn gedefinieerd in een software-updategroep.|  
|**Compatibiliteit 4 - Updates per leverancier maand jaar**|Geeft de compatibiliteitsgegevens weer voor software-updates die gedurende een specifieke maand en een specifiek jaar zijn uitgegeven door een leverancier.|  
|**Compatibiliteit 5 - specifieke computer**|Dit rapport retourneert de compatibiliteitgegevens van een software-update voor een opgegeven computer.  Als u de hoeveelheid geretourneerde informatie wilt beperken, kunt u de leverancier en software-updateclassificatie opgeven.|  
|**Compatibiliteit 6 - specifieke software-updatestatussen (secundair)**|Geeft de telling en het percentage computers weer in elke compatibiliteitsstatus voor de opgegeven software-update.|  
|**Compatibiliteit 7 - Computers in een specifieke compatibiliteitsstatus voor een updategroep (secundair)**|Geeft alle computers weer in een verzameling die een opgegeven algemene compatibiliteitsstatus hebben ten opzichte van een software-updategroep.|  
|**Compatibiliteit 8 - Computers in een specifieke compatibiliteitsstatus status voor een update (secundair)**|Geeft alle computers weer in een verzameling die een opgegeven compatibiliteitsstatus hebben voor een software-update.|  

### <a name="software-updates---b-deployment-management"></a>Software-Updates - B implementatiebeheer  

|Rapportnaam|Beschrijving|  
|-----------------|-----------------|  
|**Beheer 1 - implementaties van een updategroep**|Geeft alle implementaties weer die alle software-updates bevatten die zijn gedefinieerd binnen een specifieke software-updategroep.|  
|**Beheer 2 - Updates vereist maar niet geïmplementeerd**|Geeft alle leverancierspecifieke software-updates weer die zijn gedetecteerd als vereist op clients, maar die niet zijn geïmplementeerd op een opgegeven verzameling.|  
|**Beheer 3 - Updates in een implementatie**|Geeft de software-updates weer die zijn opgenomen in een opgegeven implementatie.|  
|**Beheer 4 - implementaties die zijn gericht op een verzameling**|Geeft alle software-update-implementaties weer die zijn gericht op een opgegeven verzameling.|  
|**Beheer 5 - implementaties die zijn gericht op een computer**|Geeft alle software-update-implementaties weer die zijn geïmplementeerd op een opgegeven computer.|  
|**Beheer 6 - implementaties die een specifieke update bevatten**|Geeft alle implementaties weer die een opgegeven software-update en de gekoppelde doelverzameling voor de implementatie bevatten.|  
|**Beheer 7 - Updates in een implementatie waarbij inhoud ontbreekt**|Geeft de software-updates in een opgegeven implementatie weer waarvoor niet alle gekoppelde inhoud is opgehaald, waardoor clients de update niet kunnen installeren en geen volledige compatibiliteit kunnen bereiken voor de implementatie.|  
|**Beheer 8 - Computers waarbij inhoud ontbreekt (secundair)**|Geeft alle computers weer die een opgegeven software-update vereisen die is opgenomen in een opgegeven implementatie die niet is ingericht op een distributiepunt.|  

### <a name="software-updates---c-deployment-states"></a>Software-Updates - C Implementatiestatussen  

|Rapportnaam|Beschrijving|  
|-----------------|-----------------|  
|**Statussen 1 - afdwingingsstatussen voor een implementatie**|Geeft de afdwingingsstatussen weer voor een opgegeven software-update-implementatie, die normaal gesproken de tweede fase vormt in een implementatie-evaluatie.|  
|**Statussen 2 - evaluatiestatussen voor een implementatie**|Geeft de evaluatiestatus weer voor een opgegeven software-update-implementatie, die normaal gesproken de eerste fase vormt in een implementatie-evaluatie.|  
|**Statussen 3 - statussen voor een implementatie en computer**|Geeft de statussen weer voor alle software-updates in de opgegeven implementatie voor een opgegeven computer.|  
|**Statussen 4 - Computers in een specifieke status voor een implementatie (secundair)**|Geeft alle computers weer in een opgegeven status voor een software-update-implementatie.|  
|**Statussen 5 - statussen voor een update in een implementatie (secundair)**|Geeft een samenvatting weer van statussen voor een opgegeven software-update waarop een opgegeven implementatie is gericht.|  
|**Statussen 6 - Computers in een specifieke afdwingingsstatus voor een update (secundair)**|Geeft alle computers weer in een opgegeven afdwingingsstatus voor een opgegeven software-update.|  

### <a name="software-updates---d-scan"></a>Software-Updates - D scannen  

|Rapportnaam|Beschrijving|  
|-----------------|-----------------|  
|**Controle 1 - laatste controlestatussen op verzameling**|Geeft de telling van computers weer voor een opgegeven verzameling in elke compatibiliteitscontrolestatus die is geretourneerd door clients tijdens de laatste compatibiliteitscontrole.|  
|**Controle 2 - laatste controlestatussen op site**|Geeft de telling weer van computers die zijn toegewezen aan een opgegeven site in elke compatibiliteitscontrolestatus die is geretourneerd door clients tijdens de laatste compatibiliteitscontrole.|  
|**Controle 3 - Clients van een verzameling die een specifieke status (secundair) rapporteren**|Geeft alle computers weer voor een opgegeven verzameling en een opgegeven compatibiliteitscontrolestatus hebben geretourneerd tijdens de laatste compatibiliteitscontrole.|  
|**Controle 4 - Clients van een site die rapporteert een specifieke status (secundair)**|Geeft alle computers weer die aan een opgegeven site zijn toegewezen en een opgegeven compatibiliteitscontrolestatus hebben geretourneerd tijdens de laatste compatibiliteitscontrole.|  

### <a name="software-updates---e-troubleshooting"></a>Software-Updates - E problemen oplossen  

|Rapportnaam|Beschrijving|  
|-----------------|-----------------|  
|**Problemen oplossen 1 - controlefouten**|Geeft controlefouten op de site en een telling van de computers waarbij elke fout optreedt weer.|  
|**Problemen oplossen 2 - implementatiefouten**|Geeft de implementatiefouten op de site en een telling van de computers waarbij elke fout optreedt weer.|  
|**Problemen oplossen 3 - Computers waarbij een specifieke Controlefout optreedt (secundair)**|Geeft een lijst weer van de computers die niet konden worden gescand vanwege een opgegeven fout.|  
|**Problemen oplossen 4 - Computers waarbij een specifieke implementatiefout optreedt (secundair)**|Geeft een lijst weer van de computers waarop de implementatie van een update mislukt vanwege een opgegeven fout.|  

### <a name="state-migration"></a>Statusmigratie  

|Rapportnaam|Beschrijving|  
|-----------------|-----------------|  
|**Statusmigratie-informatie voor een specifieke broncomputer**|Geeft de statusmigratie-informatie weer voor een opgegeven broncomputer.|  
|**Statusmigratie-informatie voor een specifiek statusmigratiepunt**|Geeft de statusmigratie-informatie weer voor een opgegeven migratiepunt.|  
|**Statusmigratiepunten voor een specifieke site**|Geeft de statusmigratiepunten weer voor een opgegeven site.|  

### <a name="status-messages"></a>Statusberichten  

|Rapportnaam|Beschrijving|  
|-----------------|-----------------|  
|**Alle berichten voor een specifieke bericht-ID**|Geeft een lijst weer van statusberichten met een opgegeven bericht-id|  
|**Clients die fouten rapporteren, in de afgelopen 12 uur voor een specifieke site**|Geeft een lijst weer van computers aan onderdelen die de afgelopen 12 uur fouten hebben gerapporteerd, en het aantal gerapporteerde fouten.|  
|**Onderdeelberichten voor de afgelopen 12 uur**|Geeft een lijst weer van onderdelenberichten voor de afgelopen 12 uur voor een opgegeven sitecode, computer en onderdeel.|  
|**Onderdeelberichten voor het afgelopen uur**|Geeft een lijst van de statusberichten die het afgelopen uur zijn gemaakt door een opgegeven onderdeel op een opgegeven computer in een opgegeven Configuration Manager-site.|  
|**Onderdeelberichten voor het afgelopen uur voor een specifieke site**|Geeft het aantal en de ernst weer van statusberichten die zijn gerapporteerd in het afgelopen uur op een opgegeven site, per onderdeel.|  
|**Fouten in de afgelopen 12 uur tellen**|Geeft het aantal serveronderdeelberichten in de afgelopen 12 uur weer.|  
|**Fatale fouten (per onderdeel)**|Geeft een lijst weer met computers die fatale fouten rapporteren, per onderdeel.|  
|**Fatale fouten (per computernaam)**|Geeft een lijst weer met computers die fatale fouten rapporteren, per computernaam.|  
|**Laatste 1000 berichten voor een specifieke computer (fouten en waarschuwingen)**|Geeft een samenvatting weer van de laatste 1000 fout- en waarschuwingsberichten voor onderdeelstatus voor een opgegeven computer.|  
|**Laatste 1000 berichten voor een specifieke computer (fouten waarschuwingen en informatie)**|Geeft een samenvatting weer van de laatste 1000 fout-, waarschuwings- en informatieberichten voor onderdeelstatus voor een opgegeven computer.|  
|**Laatste 1000 berichten voor een specifieke computer (fouten)**|Geeft een samenvatting weer van de laatste 1000 foutstatusberichten voor serveronderdeel voor een opgegeven computer.|  
|**Laatste 1000 berichten voor een specifiek serveronderdeel**|Geeft een samenvatting weer van de recentste 1000 statusberichten voor een opgegeven serveronderdeel.|  

### <a name="status-messages---audit"></a>Statusberichten - Audit  

|Rapportnaam|Beschrijving|  
|-----------------|-----------------|  
|**Alle controleberichten voor een specifieke gebruiker**|Geeft een samenvatting weer van alle controlestatusberichten voor een opgegeven gebruiker. Controleberichten beschrijven acties die worden uitgevoerd in de Configuration Manager-console die toevoegen, wijzigen of verwijderen van objecten in Configuration Manager.|  
|**Extern beheer - alle computers die extern worden beheerd door een specifieke gebruiker**|Geeft een samenvatting weer van statusberichten die extern beheer van clientcomputers door een opgegeven gebruiker aangeven.|  
|**Extern beheer - alle informatie over extern beheer**|Geeft een samenvatting weer van statusberichten die zijn gerelateerd aan het beheer op afstand van clientcomputers.|  

### <a name="task-sequence---deployment-status"></a>Takenreeks - Implementatiestatus  

|Rapportnaam|Beschrijving|  
|-----------------|-----------------|  
|**Alle systeemresources voor een takenreeksimplementatie in een specifieke status**|Geeft een lijst weer van de doelcomputers voor de opgegeven takenreeksimplementatie in de opgegeven implementatiestatus.|  
|**Alle systeemresources voor een takenreeksimplementatie in een specifieke status en die beschikbaar is voor onbekende computers**|Geeft een lijst weer van de doelcomputers voor de opgegeven takenreeksimplementatie in de opgegeven implementatiestatus.|  
|**Telling van systeemresources waaraan takenreeksimplementaties zijn toegewezen maar die nog niet uitgevoerd**|Geeft het aantal computers weer dat takenreeksen hebben geaccepteerd, maar deze nog niet hebben uitgevoerd.|  
|**Geschiedenis van een takenreeksimplementatie op een computer**|Geeft de status weer van elke stap van de opgegeven takenreeksimplementatie op de opgegeven doelcomputer. Als er geen record wordt geretourneerd, is de takenreeks niet gestart op de computer.|  
|**Lijst van computers die een specifieke tijdsduur voor het uitvoeren van een takenreeksimplementatie overschreden**|Geeft de lijst weer van doelcomputers die de opgegeven tijdsduur hebben overschreden voor het uitvoeren van een takenreeks.|  
|**Uitvoeringstijd voor een specifieke takenreeksimplementatie op een specifieke doelcomputer**|Geeft de totale tijdsduur weer die nodig was voor het voltooien van een opgegeven takenreeks op een opgegeven computer.|  
|**Uitvoeringstijd voor elke stap van een takenreeksimplementatie op een specifieke doelcomputer**|Geeft de tijdsduur weer die nodig was voor het voltooien van elke stap van de opgegeven takenreeksimplementatie op een opgegeven doelcomputer.|  
|**Status van een specifieke takenreeksimplementatie voor een specifieke computer**|Geeft de statussamenvatting weer voor een opgegeven takenreeksimplementatie op een opgegeven computer.|  
|**Status van een takenreeksimplementatie op een onbekende doelcomputer**|Geeft de status weer van de opgegeven takenreeksimplementatie op de opgegeven onbekende doelcomputer.|  
|**Statussamenvatting van een specifieke takenreeksimplementatie**|Geeft een statussamenvatting weer van alle resources waarop een implementatie is gericht.|  
|**Statussamenvatting van een specifieke takenreeksimplementatie op onbekende computers**|Geeft de statussamenvatting weer van alle resources waarop een opgegeven implementatie is gericht die beschikbaar is voor een verzameling die onbekende computers bevat.|  

### <a name="task-sequence---deployments"></a>Takenreeks - Implementaties  

|Rapportnaam|Beschrijving|  
|-----------------|-----------------|  
|**Alle systeemresources die momenteel in een specifieke groep of fase van een specifieke takenreeksimplementatie**|Geeft een lijst weer van computers die zich momenteel in een opgegeven groep of fase van een opgegeven takenreeksimplementatie bevinden.|  
|**Alle systeemresources waarbij een takenreeksimplementatie is mislukt binnen een specifieke groep of fase**|Geeft een lijst weer van computers waarbij een fout is opgetreden binnen een opgegeven groep of fase van de opgegeven takenreeksimplementatie.|  
|**Alle takenreeksimplementaties**|Geeft details weer van alle takenreeksimplementaties die vanaf deze site zijn gestart.|  
|**Alle takenreeksimplementaties die beschikbaar zijn voor onbekende computers**|Geeft details weer van alle takenreeksimplementaties die vanaf deze site zijn gestart en die zijn geïmplementeerd op verzamelingen die onbekende computers bevatten.|  
|**Telling van fouten in elke fase of groep van een specifieke takenreeks**|Geeft het aantal fouten weer in elke fase of groep van een opgegeven takenreeks.|  
|**Telling van fouten in elke fase of groep van een specifieke takenreeksimplementatie**|Geeft het aantal fouten weer in elke fase of groep van een opgegeven takenreeksimplementatie.|  
|**Implementatiestatus van alle takenreeksimplementaties**|Geeft de algemene voortgang weer van alle takenreeksimplementaties.|  
|**Voortgang van een opgegeven takenreeks**|Geeft de voortgang weer van de opgegeven takenreeks.|  
|**Voortgang van een actieve takenreeksimplementatie**|Geeft de samenvattingsinformatie weer voor de opgegeven takenreeksimplementatie.|  
|**Voortgang van alle implementaties voor een specifieke takenreeks**|Geeft de voortgang weer van alle implementaties voor de opgegeven takenreeks.|  
|**Samenvattingsrapport voor een takenreeksimplementatie**|Geeft de samenvattingsinformatie weer voor de opgegeven takenreeksimplementatie.|  

### <a name="task-sequence---progress"></a>Takenreeks - Voortgang  

|Rapportnaam|Beschrijving|  
|-----------------|-----------------|  
|**Grafiek - wekelijkse voortgang van een takenreeks**|Geeft de wekelijkse voortgang weer van een takenreeks vanaf de datum van implementatie.|  
|**Voortgang van een takenreeks**|Geeft de voortgang weer van de opgegeven takenreeks.|  
|**Voortgang van alle takenreeksen**|Geeft een samenvatting weer van de voortgang van alle takenreeksen.|  
|**Voortgang van takenreeksen voor besturingssysteemimplementaties**|Geeft de voortgang weer van alle takenreeksen die besturingssystemen implementeren.|  
|**Status van alle onbekende computers**|Geeft een lijst weer van de computers die onbekend waren toen deze een takenreeksimplementatie uitvoerden, en geeft weer of deze nu bekende computers zijn.|  

### <a name="task-sequences---references"></a>Takenreeksen - Verwijzingen  

|Rapportnaam|Beschrijving|  
|-----------------|-----------------|  
|**Inhoud waarnaar wordt verwezen door een specifieke takenreeks**|Geeft inhoud weer waarnaar wordt verwezen door een opgegeven takenreeks.|  

### <a name="upgrade-assessment"></a>Upgradebeoordeling  

|Rapportnaam|Beschrijving|  
|-----------------|-----------------|  
|**Toepassingsstatus voor een specifieke computer**|Geeft de compatibiliteit weer van toepassingen die op een computer zijn geïnstalleerd voor een opgegeven besturingssysteem.|  
|**Toepassingsstatus voor computers in een specifieke verzameling**|Geeft de algemene status weer voor computers in een verzameling, zodat u er toegang toe hebt voor het upgraden naar een opgegeven besturingssysteem op basis van de toepassingen op elke computer. Gebruik dit rapport om vast te stellen welke computers over compatibele toepassingen beschikken voordat u een besturingssysteem implementeert.|  
|**Samenvatting van toepassingsstatus**|Geeft een samenvatting weer van de toepassingsstatus voor een opgegeven besturingssysteem. Gebruik dit rapport om de compatibiliteit van de toepassing vast te stellen voordat u een besturingssysteem implementeert.|  
|**Computers met een bepaalde toepassing is geïnstalleerd**|Geeft computers weer waarop een opgegeven toepassing is geïnstalleerd.|  
|**Computers met een bepaald hardwareapparaat**|Geeft computers weer dat een bepaald hardwareapparaat hebben.|  
|**Status van hardwareapparaten voor een specifieke computer**|Geeft de compatibiliteitsstatus weer van hardwareapparaten voor een opgegeven besturingssysteem die op een opgegeven computer zijn gevonden.|  
|**Status van hardwareapparaten voor computers in een specifieke verzameling**|Geeft de algemene status weer voor hardwareapparaten voor een opgegeven besturingssysteem in een opgegeven verzameling. Gebruik dit rapport om de compatibiliteit van hardwareapparaten vast te stellen voordat u een besturingssysteem implementeert.|  
|**Samenvatting van status hardwareapparaten**|Geeft een samenvatting weer van de status van hardwareapparaten voor een opgegeven besturingssysteem. Gebruik dit rapport om de compatibiliteit van hardwareapparaten vast te stellen voordat u een besturingssysteem implementeert.|  
|**Hardwarevereisten voor besturingssysteem**|Geeft de minimale en aanbevolen hardwarecriteria voor besturingssystemen weer.|  
|**Status van besturingssysteemvereisten voor computers in een specifieke verzameling**|Geeft de status weer van de besturingssysteemvereisten voor het opgegeven besturingssysteem voor computers in een opgegeven verzameling. Gebruik dit rapport om vast te stellen of een computer aan de opgegeven besturingssysteemvereisten voldoen voor CPU-processorsnelheid, geheugengrootte en harde-schrijfruimte.|  
|**Samenvatting van upgradebeoordeling**|Geeft de samenvatting weer van de upgradebeoordeling. Gebruik dit rapport om de algemene status voor upgradecompatibiliteit te beoordelen.|  

### <a name="user---device-affinity"></a>Gebruiker - affiniteit  

|Rapportnaam|Beschrijving|  
|-----------------|-----------------|  
|**In behandeling zijnde apparaat affiniteitskoppelingen per verzameling**|Geeft alle in behandeling zijnde gebruikersapparaat-affiniteit-toewijzingen op basis van gebruiksgegevens weer voor leden van een verzameling.|  
|**Affiniteitskoppelingen gebruikersapparaat per verzameling**|Geeft alle associaties voor gebruikersapparaten voor de geselecteerd verzameling weer. De resultaten worden op verzamelingstype ingedeeld (bijvoorbeeld gebruiker of apparaat).|  

### <a name="user-data-and-profiles-health"></a>Status van gebruikersgegevens en -profielen  

|Rapportnaam|Beschrijving|  
|-----------------|-----------------|  
|**Statusrapport Mapomleiding - Details**|Geeft de details weer van de status voor mapomleiding voor elk van de omgeleide mappen voor een opgegeven gebruiker.|  
|**Roaming statusrapport van gebruikersprofielen - Details**|Geeft de details weer van de status van het gebruikersprofiel voor roaming voor een opgegeven gebruiker.|  
|**Gebruikersgegevens en -statusrapport van gebruikersprofielen - Details**|Geeft de details weer van de fout of waarschuwing voor mapomleiding of gebruikersprofiel voor roaming wanneer deze zijn opgenomen in de telling van het samenvattingsrapport.|  
|**Gebruikersgegevens en -statusrapport van gebruikersprofielen - overzicht**|Geeft de samenvatting weer van de status van mapomleiding en gebruikersprofielen voor roaming.|  

### <a name="users"></a>Gebruikers  

|Rapportnaam|Beschrijving|  
|-----------------|-----------------|  
|**Computers voor een specifieke gebruikersnaam**|Geeft een lijst weer van de computers die zijn gebruikt door een opgegeven gebruiker.|  
|**Gebruikers per domein tellen**|Geeft het aantal gebruikers weer in elk domein.|  
|**Gebruikers in een specifiek domein**|Geeft een overzicht van gebruikers en hun computers in een opgegeven domein.|  

### <a name="virtual-applications"></a>Virtuele toepassingen  

|Rapportnaam|Beschrijving|  
|-----------------|-----------------|  
|**Resultaten virtuele omgeving App-V**|Geeft informatie weer over een opgegeven virtuele omgeving met een opgegeven status voor een opgegeven verzameling.|  
|**Resultaten van de virtuele omgeving App-V voor activa**|Geeft informatie weer over een opgegeven virtuele omgeving voor een opgegeven asset en implementatietypen voor de opgegeven virtuele omgeving.|  
|**Status van de virtuele omgeving App-V**|Geeft compatibiliteitsinformatie weer voor een opgegeven virtuele omgeving voor een opgegeven verzameling.|  
|**Computers met een specifieke virtuele toepassing**|Geeft een samenvatting weer van computers die de opgegeven App-V-toepassingssnelkoppeling hebben zoals gemaakt met behulp van de Application Virtualization Management Sequencer.|  
|**Computers met een specifiek virtuele-toepassingspakket**|Geeft een samenvatting weer van computers die het opgegeven App-V-toepassingspakket hebben.|  
|**Telling van alle exemplaren van virtuele toepassingspakketten**|Geef een telling weer van aantal gedetecteerde App-V-toepassingspakketten.|  
|**Telling van alle exemplaren van virtuele toepassingen**|Geef een telling weer van gedetecteerde App-V-toepassingen.|  

### <a name="wake-on-lan"></a>Wake on LAN  

|Rapportnaam|Beschrijving|  
|-----------------|-----------------|  
|**Alle computers waarop Wake On LAN-activiteit is gericht**|Geeft een lijst weer van alle computers waarop Wake On LAN-activiteit is gericht gedurende een implementatie van het type dat u opgeeft.|  
|**Alle objecten in afwachting van ontwaakactiviteit**|Geeft objecten weer die zijn ingepland voor ontwaken.|  
|**Alle sites die zijn ingeschakeld voor Wake On LAN**|Geeft een lijst met alle sites in de hiërarchie weer die beschikbaar zijn voor Wake On LAN.|  
|**Fouten die zijn ontvangen tijdens het verzenden van ontwaakpakketten voor een opgegeven periode**|Geeft de fouten weer die zijn ontvangen tijdens het verzenden van ontwaakpakketten naar computers voor een opgegeven periode|  
|**Geschiedenis van Wake On LAN-activiteit**|Geeft een geschiedenis weer van de ontwaakactiviteit sinds een bepaalde periode.|  
|**Details van implementatiestatus van Wake-Up Proxy**|Geeft informatie weer over de implementatiestatus van Wake-up proxy voor elk apparaat in een opgegeven verzameling.|  
|**Samenvatting van implementatiestatus van Wake-Up Proxy**|Geeft een samenvatting weer van de implementatiestatus van Wake-up proxy voor een opgegeven verzameling.|  
