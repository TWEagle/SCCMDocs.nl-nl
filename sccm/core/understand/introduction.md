---
title: Inleiding | Microsoft-documenten
description: Algemene informatie als een inleiding tot System Center Configuration Manager opgehaald.
ms.custom: na
ms.date: 10/06/2016
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 3343eccf-bf09-41cd-9e68-03e893c7f904
caps.latest.revision: 16
author: Brenduns
ms.author: brenduns
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 916aac9a8f724e37044884cd73de5fea1f1a8f97
ms.openlocfilehash: 76f907b17df0dd2f102e34ca3cfb3ffc813c0004
ms.contentlocale: nl-nl
ms.lasthandoff: 05/17/2017


---
# <a name="introduction-to-system-center-configuration-manager"></a>Inleiding op System Center Configuration Manager

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*

Een product in de Microsoft System Center-pakket van beheeroplossingen voor System Center Configuration Manager kunt u apparaten en gebruikers beheren on-premises en in de cloud.  

**U kunt de Configuration Manager gebruiken om u te helpen:**   
-   IT-productiviteit en efficiëntie verhogen door handmatige taken te verminderen en zodat u zich concentreren op hoogwaardige projecten.  
-   Hardware en software-investeringen te maximaliseren.  
-   Mogelijkheden bieden aan productiviteit dankzij de juiste software op het juiste moment.  

**Configuration Manager kunt u efficiëntere IT-services leveren door in te schakelen:**  

-   Veilige en schaalbare software-implementatie.  
-   Beheer van compatibiliteitsinstellingen.  
-   Een uitgebreide asset management van servers, desktops, laptops en mobiele apparaten.  

**Configuration Manager uitbreiden en werkt goed samen met uw bestaande Microsoft-technologieën en -oplossingen.**  

Bijvoorbeeld, Configuration Manager wordt geïntegreerd met:  

-   Microsoft Intune voor het beheren van een groot aantal verschillende platformen voor mobiele apparaten.  
-   Windows Server Update Services (WSUS) voor het beheren van software-updates.  
-   Certificaatservices.  
-   Exchange Server en Exchange Online.  
-   Windows-groepsbeleid.
-   DNS.   
-   Automatische Deployment Kit (Windows ADK) en User State Migration Tool (USMT).  
-   Windows Deployment Services (WDS).  
-   Extern bureaublad en hulp op afstand.  

Configuration Manager ook gebruikt:  

-   Active Directory Domain Services voor de beveiliging, servicelocatie, configuratie en voor de detectie van gebruikers en apparaten die u wilt beheren.  
-   Microsoft SQL Server als een database voor het beheer van gedistribueerde wijzigen — en integreert met SQL Server Reporting Services (SSRS) voor het produceren van rapporten om te controleren en bijhouden beheeractiviteiten.  
-   Sitesysteemrollen die beheerfunctionaliteit uitbreiden en de webservices van Internet Information Services (IIS) gebruiken.
-   BITS (Background Intelligent Transfer Service) en BranchCache voor het beheren van de beschikbare netwerkbandbreedte.  

Om succesvol met Configuration Manager, moet u eerst grondig plannen en de beheerfuncties testen voordat u Configuration Manager in een productieomgeving gebruiken. Configuration Manager beschikt over een krachtige beheertoepassing kunnen invloed hebben op elke computer in uw organisatie. Wanneer u implementeren en beheren van Configuration Manager met een zorgvuldige planning en afweging van uw zakelijke vereisten, wordt Configuration Manager kunt reduceren uw administratieve overhead en totale eigendomskosten.  

Gebruik de volgende onderwerpen en extra secties in dit onderwerp voor meer informatie over Configuration Manager.  


**Verwante onderwerpen in deze documentatiebibliotheek:**  

-   [Functies en mogelijkheden van System Center Configuration Manager](../../core/plan-design/changes/features-and-capabilities.md)  
-   [Kies een oplossing voor Apparaatbeheer voor System Center Configuration Manager](../../core/plan-design/choose-a-device-management-solution.md)  
-   [Wat gewijzigd in System Center Configuration Manager van System Center 2012 Configuration Manager](../../core/plan-design/changes/what-has-changed-from-configuration-manager-2012.md)
-   [De grondbeginselen van System Center Configuration Manager](../../core/understand/fundamentals.md)  
-   [Evalueren van System Center Configuration Manager op uw eigen testomgeving bouwen](/sccm/core/get-started/set-up-your-lab)
-   [Help vinden voor het gebruik van System Center Configuration Manager](../../core/understand/find-help.md)  
-   [Verwijderde en afgeschafte functies voor System Center Configuration Manager](../../core/plan-design/changes/removed-and-deprecated-features.md)  

##  <a name="BKMK_Console"></a> De Configuration Manager-console  
 Nadat u de Configuration Manager hebt geïnstalleerd, kunt de Configuration Manager-console sites en clients configureren en uitvoeren en controleren van beheertaken. Deze console is het belangrijkste beheerpunt, waarmee u meerdere sites kunt beheren.  

 U kunt met behulp van de console secundaire consoles uitvoeren ter ondersteuning van specifieke clientbeheertaken, zoals de volgende:  

-   **Resourceverkenner**, om software - en hardware-inventarisgegevens weer te geven.  
-   **Extern beheer**, om op afstand verbinding te maken met een clientcomputer voor de uitvoering van foutopsporingstaken.  

U kunt de Configuration Manager-console installeren op extra computers toegang beperken en beperkingen opleggen wat gebruikers met beheerdersrechten kunnen zien in de console met behulp van Configuration Manager op rollen gebaseerd beheer.  

Zie [System Center Configuration Manager-consoles installeren](../../core/servers/deploy/install/install-consoles.md) voor meer informatie.

##  <a name="BKMK_ApplicationCatalog"></a> De toepassingscatalogus, Software Center en de bedrijfsportal  
 De **Toepassingscatalogus** is een website waar gebruikers software voor hun Windows-pc's kunnen zoeken en aanvragen. Voor het gebruik van de toepassingscatalogus moet u het Application Catalog-webservicepunt en het Application Catalog-websitepunt voor de site installeren.  

 **Software Center** is een toepassing die wordt geïnstalleerd wanneer de Configuration Manager-client is geïnstalleerd op Windows gebaseerde computers. Gebruikers voeren deze toepassing software kunnen aanvragen en de software die worden geïmplementeerd door Configuration Manager om ze te beheren. Met Software Center kunnen gebruikers het volgende doen:  

-   Zoeken en installeren van software uit de Application Catalog.  
-   De historie van softwareaanvragen weergeven.  
-   Wanneer Configuration Manager software op hun apparaten installeren kan configureren.  
-   Toegangsinstellingen voor extern beheer configureren als een gebruiker met beheerdersrechten beheer op afstand is ingeschakeld.  

**De bedrijfsportal** is een app of website die in gelijksoortige functies voorziet als de Toepassingscatalogus, maar dan voor mobiele apparaten die zijn geregistreerd door Microsoft Intune.  

Zie voor meer informatie [aan de slag met Toepassingsbeheer in System Center Configuration Manager](../../apps/understand/introduction-to-application-management.md).  

###  <a name="BKMK_Client"></a>Eigenschappen van Configuration Manager (op Windows-pc's)  
 Wanneer de Configuration Manager-client is geïnstalleerd op Windows-computers, wordt Configuration Manager is geïnstalleerd in het Configuratiescherm. U hoeft normaal gesproken te configureren van deze toepassing, omdat de configuratie van de client wordt uitgevoerd in de Configuration Manager-console. Deze toepassing is een hulpmiddel voor gebruikers met beheerdersrechten en helpdeskmedewerkers om problemen bij afzonderlijke clients op te sporen.  

 Zie [Clientinstallatiemethoden in System Center Configuration Manager](../../core/clients/deploy/plan/client-installation-methods.md) voor meer informatie over implementaties van clients.  

##  <a name="BKMK_ExampleScenarios"></a> Voorbeeldscenario's voor Configuration Manager  
 De volgende voorbeeldscenario's laten zien hoe een bedrijf met de naam Trey Research via System Center Configuration Manager mogelijkheden bieden aan gebruikers:  

-   Productiever.  
-   Hun compliancebeheer voor apparaten voor een meer gestroomlijnd beheer-ervaring.
-   Apparaatbeheer IT-kosten verminderen vereenvoudigen.  

In alle scenario's is Active Directory-toepassingsmodus hoofdbeheerder voor Configuration Manager.  

###  <a name="BKMK_ScenarioEmpower"></a>Voorbeeldscenario: Mogelijkheden bieden aan gebruikers door hen toegang te tot toepassingen vanaf elk apparaat  
 Trey Research wil om ervoor te zorgen dat werknemers toegang tot de toepassingen die ze nodig hebben hebben, zo efficiënt mogelijk. Jeroen wijst deze bedrijfsvereisten toe aan de volgende scenario's:  

|Vereiste|Huidige clientbeheerstatus|Toekomstige clientbeheerstatus|  
|-----------------|-------------------------------------|------------------------------------|  
|Nieuwe werknemers kunnen vanaf de allereerste dag efficiënt werken.|Wanneer werknemers bij het bedrijf komen werken, hebben ze wachten tot de toepassingen zijn geïnstalleerd als ze eerst aanmelden.|Wanneer werknemers bij het bedrijf komen werken, ze zich aanmelden en hun toepassingen zijn geïnstalleerd en gereed voor gebruik.|  
|Werknemers kunnen snel en gemakkelijk extra benodigde software aanvragen.|Wanneer werknemers extra toepassingen nodig, bestand ze een ticket met de helpdesk. Ze doorgaans Wacht twee dagen voor het ticket is verwerkt en voor de toepassingen zijn geïnstalleerd.|Wanneer werknemers extra toepassingen nodig, kunnen zij deze aanvragen op een website. Deze worden onmiddellijk geïnstalleerd als er geen licentiebeperkingen zijn. Als er licentiebeperkingen zijn, moeten gebruikers eerst om goedkeuring vragen voordat zij de toepassing kunnen installeren.<br /><br /> De website toont gebruikers alleen de toepassingen die ze je kunnen installeren.|  
|Werknemers kunnen hun mobiele apparaten bij hun werk gebruiken als de apparaten conform de gecontroleerde en gehandhaafde beleidsregels voor veiligheid zijn.<br /><br /> Deze beleidsregels houden onder meer het afdwingen van een sterk wachtwoord en op afstand wissen verloren of gestolen apparaten vergrendelen van een apparaat na een periode van inactiviteit.|Werknemers maken verbinding met hun mobiele apparaten Exchange-Server voor e-mailservice. Maar er is een beperkte rapportage ter bevestiging dat deze conform de beleidsregels voor veiligheid in de standaardbeleidsregels Exchange ActiveSync-postvakken. Het persoonlijke gebruik van mobiele apparaten loopt het risico te worden verboden, tenzij IT kan bevestigen dat het beleid in acht wordt genomen.|De IT-organisatie kan rapporteren dat de beveiliging van mobiele apparaten conform de vereiste instellingen zijn. Dankzij deze bevestiging kunnen gebruikers hun mobiele apparaten bij hun werk blijven gebruiken. Gebruikers kunnen hun mobiele apparaat op afstand wissen wanneer deze is vermist of gestolen en de helpdesk kan iedere gebruiker mobiel apparaat Wis dat is gerapporteerd als vermist of gestolen.<br /><br /> Voorzien in de inschrijving van mobiele apparaten in een PKI-omgeving voor extra beveiliging en controle.|  
|Werknemers kunnen productief zijn zelfs als zij niet achter hun bureau zitten.|Wanneer werknemers niet achter hun bureau zitten en niet over verplaatsbare computers beschikken, geen ze toegang tot hun toepassingen via de openbare computers die overal in het bedrijf beschikbaar zijn.|Werknemers kunnen openbare computers gebruiken om toegang te krijgen tot hun toepassingen en gegevens.|  
|Bedrijfscontinuïteit krijgt doorgaans voorrang op het installeren van vereiste toepassingen en software-updates.|Vereiste toepassingen en software-updates worden overdag geïnstalleerd. Dit stoort gebruikers vaak in hun werk, omdat hun computers vertragen of opnieuw moeten worden opgestart tijdens de installatie.|Gebruikers kunnen hun werkuren instellen om te voorkomen dat vereiste software wordt geïnstalleerd terwijl ze hun computer gebruiken.|  

 Jeroen gebruikt om te voldoen aan de vereisten, deze Configuration Manager-beheermogelijkheden en configuratieopties:  

-   Toepassingsbeheer  
-   Beheer van mobiele apparaten  

Hij implementeert ze met behulp van de configuratiestappen in de volgende tabel:  

|Configuratiestappen|Resultaat|  
|-------------------------|-------------|  
|Jeroen zorgt ervoor dat nieuwe gebruikers gebruikersaccounts hebben in Active Directory en maakt u een nieuwe query's gebaseerde verzameling in Configuration Manager voor deze gebruikers. Vervolgens definieert hij gebruikersaffiniteit apparaat door een bestand te maken dat de gebruikersaccounts koppelt aan de primaire computers die ze zullen gebruiken. Dit bestand wordt vervolgens in Configuration Manager geladen.<br /><br /> De toepassingen die nieuwe gebruikers moeten hebben zijn reeds aangemaakt in Configuration Manager. Vervolgens implementeert hij de toepassingen die als doel hebben, vereist voor de verzameling die de nieuwe gebruikers bevat.|Vanwege de informatie van affiniteit gebruikerapparaat, worden de toepassingen geïnstalleerd op de primaire computer of de computers van de gebruiker voordat de gebruiker zich aanmeldt.<br /><br /> De toepassingen zijn klaar voor gebruik als de gebruiker heeft zich aanmeldt.|  
|Jeroen installeert en configureert de Application Catalog-sitesysteemrollen zodat gebruikers kunnen bladeren door toepassingen die ze kunnen installeren. Vervolgens implementeert hij deze toepassingen die Vereist als doel hebben, aan de verzameling die de nieuwe gebruikers bevat.<br /><br /> Voor toepassingen met een beperkt aantal licenties configureert Jeroen een goedkeuringsprocedure.|Gebruikers kunnen de Application Catalog nu gebruiken om te bladeren door de toepassingen die ze je kunnen installeren. Gebruikers kunnen vervolgens de toepassingen onmiddellijk installeren of goedkeuring aanvragen terug naar de Application Catalog ze te installeren nadat de helpdesk hun aanvraag goedkeurt.|  
|Ties maakt een Exchange Server-connector in Configuration Manager voor het beheren van mobiele apparaten die verbinding met lokale Exchange-Server van het bedrijf maken. Hij configureert deze connector met beveiligingsinstellingen, waaronder de vereiste voor het instellen van een sterk wachtwoord en het mobiele apparaat na een periode van inactiviteit worden vergrendeld.<br /><br /> Voor bijkomend beheer voor apparaten met Windows Phone 8, Windows RT en iOS verkrijgt Adam Microsoft Intune-abonnement. Vervolgens installeert hij de service connection point-sitesysteemrol. Deze beheeroplossing voor mobiele apparaten geeft het bedrijf meer beheerondersteuning voor deze apparaten. Dit omvat het maken van toepassingen beschikbaar voor gebruikers om te installeren op deze apparaten en uitgebreid Instellingenbeheer. Bovendien worden mobiele apparaatverbindingen beveiligd met behulp van PKI-certificaten die automatisch worden gemaakt en geïmplementeerd door Intune.<br /><br /> Na het configureren van het serviceverbindingspunt en een abonnement voor gebruik met Configuration Manager, stuurt Jeroen een e-mailbericht naar de gebruikers die eigenaar van deze mobiele apparaten om op een koppeling te het registratieproces te starten.<br /><br /> Jeroen gebruikt compatibiliteitsinstellingen beveiligingsinstellingen voor deze mobiele apparaten te configureren voor mobiele apparaten moeten worden geregistreerd door Microsoft Intune. Deze instellingen omvatten de vereiste voor het instellen van een sterk wachtwoord en het mobiele apparaat na een periode van inactiviteit worden vergrendeld.|Met deze twee beheeroplossingen voor mobiele apparaten kan de IT-organisatie nu rapportinformatie geven over de mobiele apparaten die op het bedrijfsnetwerk worden gebruikt, en over hun compatibiliteit met de geconfigureerde beveiligingsinstellingen.<br /><br /> Gebruikers wordt getoond hoe aan hun mobiele apparaat op afstand te wissen met behulp van de Application Catalog of de bedrijfsportal als hun mobiele apparaat is vermist of gestolen. De helpdesk wordt ook geïnstrueerd hoe een mobiel apparaat voor gebruikers met behulp van de Configuration Manager-console op afstand.<br /><br /> Bovendien voor de mobiele apparaten die zijn geregistreerd door Microsoft Intune, Active Directory-toepassingsmodus kan mobiele toepassingen implementeren voor gebruikers om te installeren, meer inventarisgegevens verzamelen van deze apparaten en betere Beheercontrole hebben over deze apparaten door toegang tot meer instellingen.|  
|Trey Research heeft verschillende openbare computers die worden gebruikt door werknemers die het kantoor bezoeken. De werknemers willen hun toepassingen die voor hen beschikbaar zijn, waar ze zich aanmelden. Adam wilt niet echter alle toepassingen lokaal op elke computer installeren.<br /><br /> Jeroen maakt, om dit te doen, de vereiste toepassingen die twee implementatietypes hebben:<br /><br /> **De eerste:** Een volledige, lokale installatie van de toepassing die een vereiste dat deze alleen kan worden geïnstalleerd op het primaire apparaat van de gebruiker heeft.<br /><br /> **De tweede:** Een virtuele versie van de toepassing die de vereiste dat niet moet worden geïnstalleerd op het primaire apparaat van de gebruiker heeft.|Als bezoekende werknemers zich aanmelden op een openbare computer, zien ze de toepassingen die ze nodig hebben, weergegeven als pictogrammen op het bureaublad van de computer van de kioskmodus. Het uitvoeren van de toepassing, met deze methode gestreamd als virtuele toepassingen. Op deze manier ze kunnen worden productief alsof ze op hun bureaublad zit.|  
|ADAM kiest, kunnen gebruikers weten dat ze hun werkuren in Software Center configureren kunnen, en opties om te voorkomen dat de implementatieactiviteiten software tijdens deze periode en wanneer de computer zich in de presentatiemodus bevindt kunnen selecteren.|Omdat gebruikers wanneer software op hun computers Configuration Manager implementeert controleren kunnen, is gebruikers blijven productiever tijdens hun werkdag.|  

 Deze configuratiestappen en resultaten zorgen ervoor dat Trey Research werknemers beter kan ondersteunen door toegang tot toepassingen te verzekeren vanaf elk apparaat.  

###  <a name="BKMK_ScenarioUnify"></a>Voorbeeldscenario: Conformiteitsbeheer bundelen voor apparaten  
 Trey Research wil een geïntegreerde oplossing voor clientbeheer die ervoor zorgt dat hun computers antivirussoftware uitvoeren die automatisch wordt bijgewerkt. Oftewel:  

-   Windows Firewall is ingeschakeld.  
-   Kritieke software-updates worden geïnstalleerd.  
-   Specifieke registersleutels worden ingesteld.  
-   Beheerde mobiele apparaten kunnen installeren of uitvoeren van niet-ondertekende toepassingen.  

Het bedrijf wil deze beveiliging ook uitbreiden naar het internet voor laptops die overschakelen van het intranet naar het internet.  

Jeroen wijst deze bedrijfsvereisten toe aan de volgende scenario's:  

|Vereiste|Huidige clientbeheerstatus|Toekomstige clientbeheerstatus|  
|-----------------|-------------------------------------|------------------------------------|  
|Alle computers voeren antimalwaresoftware uit met bijgewerkte definitiebestanden en ingeschakelde Windows Firewall.|Verschillende computers worden verschillende antimalwareoplossingen die zijn niet altijd up-to-date worden gehouden uitgevoerd. Hoewel Windows Firewall is standaard ingeschakeld, schakelen gebruikers soms uit deze.<br /><br /> Er wordt aan gebruikers gevraagd om contact op te nemen met de helpdesk als er malware op hun computer wordt gedetecteerd.|Alle computers voeren dezelfde antimalwareoplossing uit die automatisch de meest recente definitiebestanden downloadt en automatisch Windows Firewall opnieuw inschakelt als gebruikers deze uitschakelen.<br /><br /> De helpdesk wordt automatisch per e-mail verwittigd als er malware wordt gedetecteerd.|  
|Alle computers installeren kritieke software-updates binnen de eerste maand na de release.|Hoewel software-updates zijn geïnstalleerd op computers, installeren niet veel computers automatisch kritieke software-updates pas twee of drie maanden nadat ze zijn vrijgegeven. Dit maakt ze kwetsbaar voor aanvallen tijdens deze periode.<br /><br /> Voor computers die de kritieke software-updates niet installeren, stuurt de helpdesk eerst naar e-mailberichten aan gebruikers vragen de updates te installeren. Supportengineers verbinden op afstand met computers die niet-compatibel blijven om de ontbrekende software-updates handmatig te installeren.|De huidige compatibiliteitsgraad binnen de opgegeven maand tot boven 95% wordt verbeterd zonder te moeten sturen e-mailberichten of vragen van de helpdesk handmatig te installeren.|  
|De veiligheidsinstellingen voor specifieke toepassingen worden regelmatig gecontroleerd en hersteld als dit nodig is.|Computers voeren complexe opstartscripts uit die afhankelijk zijn van groepslidmaatschap van de computer om registerwaarden te resetten voor specifieke toepassingen.<br /><br /> Omdat deze scripts alleen tijdens het opstarten worden uitgevoerd en sommige computers zijn dagen aan blijven, wordt de helpdesk niet op regelmatige basis configuratieafwijkingen controleren.|Registerwaarden worden gecontroleerd en automatisch hersteld zonder afhankelijk te zijn van groepslidmaatschap van de computer of van het opnieuw opstarten van de computer.|  
|Mobiele apparaten kunnen installeren of uitvoeren onveilige toepassingen.|Gebruikers worden gevraagd geen te downloaden en uitvoeren van mogelijk onveilige toepassingen van het Internet. Er zijn echter geen controles beschikbaar om te controleren of dit afdwingen.|Mobiele apparaten die worden beheerd met Microsoft Intune of Configuration Manager automatisch te voorkomen dat niet-ondertekende toepassingen installeren of uitvoeren.|  
|Laptops die overschakelen van het intranet naar het internet, moeten worden beveiligd.|Voor reizende gebruikers ze vaak kunnen geen verbinding maken via de VPN-verbinding dagelijks. Deze laptops voldoen niet conform beveiligingsvereisten.|Een internetverbinding is het enige dat is vereist voor laptops om te blijven voldoen aan de geldende beveiligingsvereisten. Gebruikers hebben geen aanmelden of de VPN-verbinding gebruiken.|  

 Jeroen gebruikt om te voldoen aan de vereisten, deze Configuration Manager-beheermogelijkheden en configuratieopties:  

-   Endpoint Protection  
-   Software-updates  
-   Instellingen voor naleving  
-   Beheer van mobiele apparaten  
-   Clientbeheer via internet  

Hij implementeert ze met behulp van de configuratiestappen in de volgende tabel:  

|Configuratiestappen|Resultaat|  
|-------------------------|-------------|  
|Jeroen configureert Endpoint Protection. Hij schakelt de clientinstelling in om andere antimalwareoplossingen te verwijderen en schakelt Windows Firewall. Hij configureert automatische implementatieregels, zodat computers regelmatig de nieuwste definitie-updates ontvangen en installeren.|De antimalwareoplossing helpt om alle computers te beschermen met een minimale administratieve verwerkingstijd. Omdat de helpdesk wordt automatisch een e-mailbericht als er malware wordt gedetecteerd, kan problemen kunnen snel worden opgelost. Dit helpt aanvallen op andere computers te voorkomen.|  
|Definieert onderhoudsvensters voor servers en onderzoekt de voordelen en nadelen van Wake on LAN voor computers in sluimerstand om te helpen verhogen compatibiliteitspercentage, Jeroen gebruikt Automatische implementatieregels.|Compatibiliteit voor kritieke software-updates verhoogt de beveiliging en zorgt er minder voor dat gebruikers of de helpdesk software-updates handmatig moeten installeren.|  
|Jeroen gebruikt compatibiliteitsinstellingen om de aanwezigheid van de opgegeven toepassingen te controleren. Wanneer de toepassingen worden gedetecteerd, configuratie-items vervolgens de registerwaarden controleren en automatisch hersteld als ze niet-compatibel.|Met configuratie-items en configuratiebasislijnen die zijn geïmplementeerd op alle computers en controleer of elke dag de compatibiliteit kunt vereist u niet langer afzonderlijke scripts die afhankelijk van computerlidmaatschap en de computer opnieuw opstarten zijn.|  
|Jeroen gebruikt compatibiliteitsinstellingen voor geregistreerde mobiele apparaten en configureert de Exchange Server-connector zodat niet-ondertekende toepassingen niet kunnen worden geïnstalleerd en uitgevoerd op mobiele apparaten.|Omdat het niet-ondertekende toepassingen zijn niet toegestaan, mobiele apparaten automatisch beveiligd tegen mogelijk schadelijke toepassingen.|  
|Jeroen zorgt ervoor dat sitesysteemservers en computers beschikken over de PKI-certificaten die Configuration Manager voor HTTPS-verbindingen vereist. Vervolgens installeert hij bijkomende sitesysteemrollen in het perimeternetwerk die clientverbindingen via Internet accepteren.|Computers die overschakelen van het intranet naar het internet, blijven beheerd door Configuration Manager als ze verbonden zijn met het internet. Deze computers afhankelijk niet van gebruikers aangemeld bij hun computer of verbinding maken met de VPN-verbinding.<br /><br /> Die computers blijven beheerd voor antimalware en Windows Firewall, software-updates en configuratie-items. Als gevolg daarvan vergroot de compatibiliteitsgraad automatisch.|  

 Deze configuratiestappen en -resultaten zorgen ervoor dat Trey Research hun compatibiliteitsbeheer voor apparaten kan samenvoegen.  

###  <a name="BKMK_ScenarioSimplify"></a>Voorbeeldscenario: Clientbeheer voor apparaten vereenvoudigen  
 Trey Research wil dat alle nieuwe computers automatisch installeren van hun bedrijf installatiekopie van Windows 7 draait. Nadat de installatiekopie van het besturingssysteem op deze computers is geïnstalleerd, moeten deze worden beheerd en bewaakt bijkomende software die gebruikers installeren. Computers die zeer vertrouwelijke gegevens opslaan, vereisen een meer beperkend beheerbeleid dan andere computers. Voor deze computers kan het nodig zijn om in te stellen dat helpdeskengineers er niet op afstand mee kunnen verbinden, dat invoer van de BitLocker-pincode vereist is voor het opnieuw opstarten, of dat alleen beheerders software kunnen installeren.  

 Jeroen wijst deze bedrijfsvereisten toe aan de volgende scenario's:  

|Vereiste|Huidige clientbeheerstatus|Toekomstige clientbeheerstatus|  
|-----------------|-------------------------------------|------------------------------------|  
|Op nieuwe computers is Windows 7 geïnstalleerd.|De helpdesk installeert en configureert Windows 7 voor gebruikers en stuurt de computer vervolgens naar de respectieve locatie.|Nieuwe computers gaan direct naar de eindbestemming, aangesloten op het netwerk en automatisch installeren en configureert Windows 7.|  
|Computers moeten worden beheerd en bewaakt. Dit omvat de verzameling van inventarisgegevens voor hardware en software om te helpen bepalen licentievereisten.|De Configuration Manager-client wordt geïmplementeerd met behulp van automatische push-clientinstallatie. De helpdesk onderzoekt mislukte installaties en clients die geen inventarisgegevens versturen wanneer het wordt verwacht.<br /><br /> Mislukte installaties doen zich vaak vanwege zijn niet voldaan aan de installatieafhankelijkheden en WMI-beschadiging is opgetreden op de client.|Clientinstallatie- en inventarisgegevens die worden verzameld van computers, zijn betrouwbaarder en vereisen bovendien minder interventie van de helpdesk. Rapporten geven informatie weer over softwaregebruik voor licenties.|  
|Sommige computers vereisen een strenger beheerbeleid.|Door het strengere beheerbeleid deze computers op dit moment niet worden beheerd door Configuration Manager.|Deze computers worden beheerd met behulp van Configuration Manager om zonder bijkomende administratieve verwerkingstijd uitzonderingen te behandelen.|  

 Jeroen gebruikt om te voldoen aan de vereisten, deze Configuration Manager-beheermogelijkheden en configuratieopties:  

-   Implementatie van besturingssystemen  
-   Clientimplementatie en clientstatus  
-   Instellingen voor naleving  
-   Clientinstellingen  
-   Inventarisatiemethoden en Asset Intelligence  
-   Op rollen gebaseerd beheer  

Hij implementeert ze met behulp van de configuratiestappen in de volgende tabel:  

|Configuratiestappen|Resultaat|  
|-------------------------|-------------|  
|ADAM vastgelegd van de installatiekopie van een besturingssysteem vanaf een computer waarop Windows 7 is geïnstalleerd en is geconfigureerd volgens de specificaties van het bedrijf. Vervolgens implementeert hij het besturingssysteem op de nieuwe computers door gebruik te maken van onbekende computerondersteuning en PXE. Hij installeert tevens de Configuration Manager-client als onderdeel van de implementatie van besturingssystemen.|Nieuwe computers zijn sneller actief en werkend zonder tussenkomst vanuit de helpdesk.|  
|ADAM configureert een automatische site-brede clientpushinstallatie voor de installatie van de Configuration Manager-client op computers die zijn gedetecteerd. Dit zorgt ervoor dat computers zonder installatiekopie van de client de client nog steeds geïnstalleerd zodat de computer wordt beheerd door Configuration Manager.<br /><br /> Adam configureert de clientstatus zo, dat deze eventuele gedetecteerde clientproblemen automatisch herstelt. Hij configureert tevens de clientinstellingen waarmee de verzameling van inventarisgegevens is vereist en configureert Asset Intelligence.|Installatie van de client samen met het besturingssysteem is sneller en betrouwbaarder dan bij wachten op Configuration Manager kan de computer te detecteren en vervolgens probeert te installeren van de clientbronbestanden op de computer. Door de automatische clientpushopties verlaten optie is ingeschakeld, bieden u een back-upmethode voor een computer waarop het besturingssysteem is geïnstalleerd voor de installatie van de client wanneer de computer verbinding met het netwerk maakt.<br /><br /> Clientinstellingen zorgen ervoor dat clients hun inventarisgegevens regelmatig naar de site verzenden. Naast de tests client status Hierdoor blijven de client die wordt uitgevoerd met zo weinig mogelijk tussenkomst van de helpdesk. Zo worden WMI-beschadigingen gedetecteerd en automatisch hersteld.<br /><br /> De Asset Intelligence-rapporten helpen bij de controle van softwaregebruik en -licenties.|  
|ADAM maakt een verzameling van de computers die strengere beleidsinstellingen moeten beschikken. Vervolgens maakt hij een aangepaste clientapparaatinstelling voor deze verzameling die extern beheer wordt uitgeschakeld, BitLocker PIN-vermelding inschakelt en kan alleen lokale beheerders software installeren.<br /><br /> ADAM configureert op rollen gebaseerd beheer, zodat helpdesktechnici deze verzameling computers niet zichtbaar. Dit zorgt ervoor dat deze computers worden niet per ongeluk als Standaardcomputers worden beheerd.|Deze computers worden nu beheerd door Configuration Manager, maar met specifieke instellingen, waardoor geen nieuwe site nodig.<br /><br /> De verzameling van deze computers niet zichtbaar voor helpdesktechnici. Dit reduceert de hoeveelheid de mogelijkheid van de computers die zijn verstuurd per ongeluk implementaties en scripts voor Standaardcomputers opgestuurd.|  

 Deze configuratiestappen en -resultaten hebben tot gevolg dat Trey Research met succes clientbeheer voor apparaten vereenvoudigt.  

##  <a name="BKMK_NextSteps"></a> Volgende stappen  
 Voordat u Configuration Manager installeert, kunt u meer vertrouwd raken met enkele basisbeginselen en -termen die specifiek zijn voor Configuration Manager.  

-   Als u vertrouwd met System Center 2012 Configuration Manager bent, raadpleegt u [wat gewijzigd in System Center Configuration Manager van System Center 2012 Configuration Manager](../../core/plan-design/changes/what-has-changed-from-configuration-manager-2012.md) om te begrijpen van de nieuwe mogelijkheden.  
-   Zie voor een hoogwaardig technisch overzicht van System Center Configuration Manager, [grondbeginselen van System Center Configuration Manager](../../core/understand/fundamentals.md).  

Wanneer u vertrouwd met de basisbeginselen bent, gebruikt u de System Center Configuration Manager-documentatie bij het succes implementeren en gebruiken van Configuration Manager.  

