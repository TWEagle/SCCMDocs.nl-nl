---
title: Inleiding
titleSuffix: Configuration Manager
description: Algemene informatie als een inleiding op System Center Configuration Manager worden opgehaald.
ms.custom: na
ms.date: 10/06/2016
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 3343eccf-bf09-41cd-9e68-03e893c7f904
caps.latest.revision: "16"
author: aczechowski
ms.author: aaroncz
manager: angrobe
ms.openlocfilehash: 76dfa18cb7f794be9102bf045cd4212adc7ad56f
ms.sourcegitcommit: ca9d15dfb1c9eb47ee27ea9b5b39c9f8cdcc0748
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 01/04/2018
---
# <a name="introduction-to-system-center-configuration-manager"></a>Inleiding op System Center Configuration Manager

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*

Een product in de Microsoft System Center-suite van oplossingen voor System Center Configuration Manager kunt u beheren van apparaten en gebruikers zowel on-premises en in de cloud.  

**U kunt de Configuration Manager gebruiken om u te helpen:**   
-   Uw IT-productiviteit en efficiëntie door handmatige taken te verminderen zodat u zich concentreren op hoogwaardige projecten.  
-   Hardware en software-investeringen maximaliseren.  
-   Productiviteit van gebruiker door de juiste software op het juiste moment.  

**Configuration Manager kunt u efficiëntere IT-services leveren door in te schakelen:**  

-   Veilige en schaalbare software-implementatie.  
-   Beheer van compatibiliteitsinstellingen.  
-   Een uitgebreide asset management van servers, desktops, laptops en mobiele apparaten.  

**Configuration Manager uitbreidt en werkt goed samen met uw bestaande Microsoft-technologieën en -oplossingen.**  

Bijvoorbeeld, Configuration Manager geïntegreerd met:  

-   Microsoft Intune voor het beheren van een groot aantal verschillende platformen voor mobiele apparaten.  
-   Windows Server Update Services (WSUS) voor het beheren van software-updates.  
-   Certificaatservices.  
-   Exchange Server en Exchange Online.  
-   Windows-groepsbeleid.
-   DNS.   
-   Windows Automated Deployment Kit (Windows ADK) en User State Migration Tool (USMT).  
-   Windows Deployment Services (WDS).  
-   Extern bureaublad en hulp op afstand.  

Configuration Manager gebruikt ook:  

-   Active Directory Domain Services voor de beveiliging, servicelocatie, configuratie en voor de detectie van gebruikers en apparaten die u wilt beheren.  
-   Microsoft SQL Server als een database voor het beheer van gedistribueerde wijzigen — en integreert met SQL Server Reporting Services (SSRS) voor het produceren van rapporten uit om te bewaken en bijhouden van beheeractiviteiten.  
-   Sitesysteemrollen die de beheerfunctionaliteit uitbreiden en de webservices van Internet Information Services (IIS) gebruiken.
-   BITS (Background Intelligent Transfer Service) en BranchCache voor het beheren van de beschikbare netwerkbandbreedte.  

Als u geslaagde met Configuration Manager, moet u eerst grondig plannen en de beheerfuncties testen voordat u Configuration Manager in een productieomgeving gebruiken. Configuration Manager heeft een krachtige beheertoepassing kunnen invloed hebben op elke computer in uw organisatie. Wanneer u implementeren en beheren van Configuration Manager met een zorgvuldige planning en afweging van uw bedrijfsvereisten, kan Configuration Manager uw administratieve overhead en totale eigendomskosten verminderen.  

Gebruik de volgende onderwerpen en extra secties in dit onderwerp voor meer informatie over Configuration Manager.  


**Verwante onderwerpen in deze documentatiebibliotheek:**  

-   [Functies en mogelijkheden van System Center Configuration Manager](../../core/plan-design/changes/features-and-capabilities.md)  
-   [Kies een oplossing voor Apparaatbeheer voor System Center Configuration Manager](../../core/plan-design/choose-a-device-management-solution.md)  
-   [Wat er veranderd in System Center Configuration Manager van System Center 2012 Configuration Manager](../../core/plan-design/changes/what-has-changed-from-configuration-manager-2012.md)
-   [Basisprincipes van System Center Configuration Manager](../../core/understand/fundamentals.md)  
-   [System Center Configuration Manager evalueren door uw eigen testomgeving bouwen](/sccm/core/get-started/set-up-your-lab)
-   [Hulp zoeken voor het gebruik van System Center Configuration Manager](../../core/understand/find-help.md)  
-   [Verwijderde en afgeschafte functies voor System Center Configuration Manager](../../core/plan-design/changes/removed-and-deprecated-features.md)  

##  <a name="BKMK_Console"></a> De Configuration Manager-console  
 Nadat u de Configuration Manager hebt geïnstalleerd, gebruikt u de Configuration Manager-console voor het configureren van sites en clients en voor het uitvoeren en controleren van beheertaken. Deze console is het belangrijkste beheerpunt, waarmee u meerdere sites kunt beheren.  

 U kunt met behulp van de console secundaire consoles uitvoeren ter ondersteuning van specifieke clientbeheertaken, zoals de volgende:  

-   **Resourceverkenner**, om software - en hardware-inventarisgegevens weer te geven.  
-   **Extern beheer**, om op afstand verbinding te maken met een clientcomputer voor de uitvoering van foutopsporingstaken.  

U kunt de Configuration Manager-console op extra computers installeren en de toegang beperken en beperken wat gebruikers met beheerdersrechten kunnen zien in de console met behulp van Configuration Manager op rollen gebaseerd beheer.  

Zie [System Center Configuration Manager-consoles installeren](../../core/servers/deploy/install/install-consoles.md) voor meer informatie.

##  <a name="BKMK_ApplicationCatalog"></a> De toepassingscatalogus, Software Center en de bedrijfsportal  
 De **Toepassingscatalogus** is een website waar gebruikers software voor hun Windows-pc's kunnen zoeken en aanvragen. Voor het gebruik van de toepassingscatalogus moet u het Application Catalog-webservicepunt en het Application Catalog-websitepunt voor de site installeren.  

 **Software Center** is een toepassing die wordt geïnstalleerd wanneer de Configuration Manager-client is geïnstalleerd op Windows gebaseerde computers. Gebruikers voeren deze toepassing software aanvragen en beheren van de software die Configuration Manager op deze implementeert. Met Software Center kunnen gebruikers het volgende doen:  

-   Zoeken naar en installeren van software uit de Application Catalog.  
-   De historie van softwareaanvragen weergeven.  
-   Configureren wanneer Configuration Manager software op hun apparaten installeren kan.  
-   Toegangsinstellingen voor extern beheer configureren als een gebruiker met beheerdersrechten beheer op afstand is ingeschakeld.  

**De bedrijfsportal** is een app of website die in gelijksoortige functies voorziet als de toepassingscatalogus, maar voor mobiele apparaten die zijn geregistreerd door Microsoft Intune.  

Zie voor meer informatie [aan de slag met Toepassingsbeheer in System Center Configuration Manager](../../apps/understand/introduction-to-application-management.md).  

###  <a name="BKMK_Client"></a>Eigenschappen van Configuration Manager (op Windows-pc's)  
 Wanneer de Configuration Manager-client is geïnstalleerd op Windows-computers, wordt Configuration Manager is geïnstalleerd in het Configuratiescherm. U hoeft normaal gesproken te configureren van deze toepassing omdat de configuratie van de client wordt uitgevoerd in de Configuration Manager-console. Deze toepassing is een hulpmiddel voor gebruikers met beheerdersrechten en helpdeskmedewerkers om problemen bij afzonderlijke clients op te sporen.  

 Zie [Clientinstallatiemethoden in System Center Configuration Manager](../../core/clients/deploy/plan/client-installation-methods.md) voor meer informatie over implementaties van clients.  

##  <a name="BKMK_ExampleScenarios"></a> Voorbeeldscenario's voor Configuration Manager  
 De volgende voorbeeldscenario's laten zien hoe een bedrijf, Trey Research System Center Configuration Manager gebruikt om te zorgen dat gebruikers:  

-   Wees productiever.  
-   Hun nalevingsbeheer voor apparaten voor een meer gestroomlijnde beheerervaring.
-   Beheer van apparaten om de operationele kosten verlagen IT vereenvoudigen.  

In alle scenario's is Active Directory-toepassingsmodus hoofdbeheerder voor Configuration Manager.  

###  <a name="BKMK_ScenarioEmpower"></a>Voorbeeldscenario: Gebruikers mogelijkheden bieden door ervoor te zorgen toegang tot toepassingen vanaf elk apparaat  
 Trey Research wil om ervoor te zorgen dat werknemers toegang tot de toepassingen die ze nodig hebben hebben, zo efficiënt mogelijk. Jeroen wijst deze bedrijfsvereisten toe aan de volgende scenario's:  

|Vereiste|Huidige clientbeheerstatus|Toekomstige clientbeheerstatus|  
|-----------------|-------------------------------------|------------------------------------|  
|Nieuwe werknemers kunnen vanaf de allereerste dag efficiënt werken.|Wanneer werknemers bij het bedrijf, moeten wachten tot toepassingen die worden geïnstalleerd nadat ze zich voor het eerst aanmelden.|Wanneer werknemers bij het bedrijf, ze zich aanmelden en hun toepassingen zijn geïnstalleerd en gereed om te worden gebruikt.|  
|Werknemers kunnen snel en gemakkelijk extra benodigde software aanvragen.|Wanneer werknemers extra toepassingen nodig, dienen zij een ticket met de helpdesk. Ze doorgaans Wacht twee dagen voor het ticket is verwerkt en voor de toepassingen die worden geïnstalleerd.|Wanneer werknemers extra toepassingen nodig, kunnen zij deze aanvragen van een website. Deze worden onmiddellijk geïnstalleerd als er geen licentiebeperkingen zijn. Als er licentiebeperkingen zijn, moeten gebruikers eerst om goedkeuring vragen voordat zij de toepassing kunnen installeren.<br /><br /> De website toont gebruikers alleen de toepassingen die ze je kunnen installeren.|  
|Werknemers kunnen hun mobiele apparaten bij hun werk gebruiken als de apparaten conform de gecontroleerde en gehandhaafde beleidsregels voor veiligheid zijn.<br /><br /> Deze beleidsregels bevatten een sterk wachtwoord afdwingen en op afstand wissen van verloren of gestolen apparaten vergrendelen van een apparaat na een periode van inactiviteit.|Werknemers maken verbinding met hun mobiele apparaten Exchange-Server voor e-mailservice. Maar er is beperkte rapportage ter bevestiging dat deze voldoen aan het beveiligingsbeleid in de standaardbeleidsregels voor Exchange ActiveSync-postvak. Het persoonlijke gebruik van mobiele apparaten loopt het risico te worden verboden, tenzij IT kan bevestigen dat het beleid in acht wordt genomen.|De IT-organisatie kan rapporteren dat de beveiliging van mobiele apparaten conform de vereiste instellingen zijn. Dankzij deze bevestiging kunnen gebruikers hun mobiele apparaten bij hun werk blijven gebruiken. Gebruikers kunnen hun mobiele apparaat op afstand wissen als dit is zoekgeraakt of gestolen en de helpdesk van een gebruiker mobiele apparaat dat is gerapporteerd wissen kunt als zoekgeraakt of gestolen.<br /><br /> Voorzien in de inschrijving van mobiele apparaten in een PKI-omgeving voor extra beveiliging en controle.|  
|Werknemers kunnen productief zijn, zelfs als ze niet achter hun bureau zitten.|Wanneer werknemers niet achter hun bureau zitten en niet over verplaatsbare computers beschikken, geen ze toegang tot hun toepassingen met behulp van de openbare computers die in het hele bedrijf beschikbaar zijn.|Werknemers kunnen openbare computers gebruiken om toegang te krijgen tot hun toepassingen en gegevens.|  
|Bedrijfscontinuïteit krijgt doorgaans voorrang op het installeren van vereiste toepassingen en software-updates.|Vereiste toepassingen en software-updates worden overdag geïnstalleerd. Dit stoort gebruikers vaak in hun werk, omdat hun computers vertragen of opnieuw moeten worden opgestart tijdens de installatie.|Gebruikers kunnen hun werkuren om te voorkomen dat vereiste software installeren terwijl ze hun computer configureren.|  

 Jeroen gebruikt om te voldoen aan de vereisten, deze Configuration Manager-beheermogelijkheden en configuratieopties:  

-   Toepassingsbeheer  
-   Beheer van mobiele apparaten  

Hij implementeert ze met behulp van de configuratiestappen in de volgende tabel:  

|Configuratiestappen|Resultaat|  
|-------------------------|-------------|  
|Jeroen zorgt ervoor dat nieuwe gebruikers gebruikersaccounts hebben in Active Directory en maakt u een nieuwe query's gebaseerde verzameling in Configuration Manager voor deze gebruikers. Vervolgens definieert hij gebruikersaffiniteit apparaat door een bestand te maken dat de gebruikersaccounts koppelt aan de primaire computers die ze zullen gebruiken. Dit bestand wordt vervolgens in Configuration Manager geladen.<br /><br /> De toepassingen die nieuwe gebruikers moeten hebben zijn reeds in Configuration Manager gemaakt. Vervolgens implementeert hij de toepassingen die het doel van hebben vereist voor de verzameling die de nieuwe gebruikers bevat.|Vanwege de informatie van affiniteit gebruikerapparaat, worden de toepassingen geïnstalleerd op de primaire computer of de computers van elke gebruiker voordat de gebruiker zich aanmeldt.<br /><br /> De toepassingen zijn klaar voor gebruik als de gebruiker heeft zich aanmeldt.|  
|Jeroen installeert en configureert de Application Catalog-sitesysteemrollen zodat gebruikers kunnen bladeren door toepassingen die ze kunnen installeren. Vervolgens implementeert hij deze toepassingen die Vereist als doel hebben, aan de verzameling die de nieuwe gebruikers bevat.<br /><br /> Voor toepassingen met een beperkt aantal licenties configureert Jeroen een goedkeuringsprocedure.|Gebruikers kunnen nu de Application Catalog gebruiken om te bladeren door de toepassingen die ze je kunnen installeren. Gebruikers kunnen vervolgens de toepassingen onmiddellijk installeren of goedkeuring aanvragen en Ga terug naar de Application Catalog ze te installeren nadat de helpdesk hun aanvraag goedkeurt.|  
|Jeroen maakt een Exchange Server-connector in Configuration Manager voor het beheren van mobiele apparaten die verbinding met lokale Exchange-Server van het bedrijf maken. Hij configureert deze connector met beveiligingsinstellingen de vereiste omvatten voor het instellen van een sterk wachtwoord en het mobiele apparaat vergrendeld na een periode van inactiviteit.<br /><br /> Ties krijgt voor aanvullend beheer voor apparaten met Windows Phone 8, Windows RT en iOS een Microsoft Intune-abonnement. Vervolgens installeert hij de service connection point-sitesysteemrol. Deze beheeroplossing voor mobiele apparaten geeft het bedrijf meer beheerondersteuning voor deze apparaten. Dit omvat toepassingen beschikbaar maken voor gebruikers om te installeren op deze apparaten en uitgebreid Instellingenbeheer. Bovendien worden mobiele apparaatverbindingen beveiligd met behulp van PKI-certificaten die automatisch worden gemaakt en geïmplementeerd door Intune.<br /><br /> Na het configureren van het serviceverbindingspunt en het abonnement voor gebruik met Configuration Manager, stuurt Jeroen een e-mailbericht naar de gebruikers die eigenaar van deze mobiele apparaten om op een koppeling klikken om het inschrijvingsproces te starten.<br /><br /> Voor de mobiele apparaten worden geregistreerd door Microsoft Intune, gebruikt Jeroen compatibiliteitsinstellingen om de beveiligingsinstellingen voor deze mobiele apparaten te configureren. Deze instellingen omvatten de vereiste voor het instellen van een sterk wachtwoord en het mobiele apparaat vergrendeld na een periode van inactiviteit.|Met deze twee beheeroplossingen voor mobiele apparaten kan de IT-organisatie nu rapportinformatie geven over de mobiele apparaten die op het bedrijfsnetwerk worden gebruikt, en over hun compatibiliteit met de geconfigureerde beveiligingsinstellingen.<br /><br /> Gebruikers weergegeven hoe hun mobiele apparaat op afstand wissen via de Application Catalog of de bedrijfsportal, als hun mobiele apparaat is zoekgeraakt of gestolen. De helpdesk wordt ook geïnstrueerd hoe op een mobiel apparaat voor gebruikers op afstand wissen via de Configuration Manager-console.<br /><br /> Bovendien voor de mobiele apparaten die zijn geregistreerd door Microsoft Intune, Adam kan mobiele toepassingen implementeren voor gebruikers installeren, meer inventarisgegevens verzamelen van deze apparaten en betere Beheercontrole hebben over deze apparaten door toegang kunnen krijgen tot meer instellingen.|  
|Trey Research heeft verschillende openbare computers die worden gebruikt door werknemers die het kantoor bezoeken. De werknemers willen hun toepassingen die voor hen beschikbaar zijn, waar ze zich aanmelden. Adam wilt niet echter alle toepassingen lokaal op elke computer installeren.<br /><br /> Jeroen maakt, om dit te doen, de vereiste toepassingen die twee implementatietypes hebben:<br /><br /> **De eerste:** Een volledige, lokale installatie van de toepassing die een vereiste dat deze alleen kan worden geïnstalleerd op het primaire apparaat van een gebruiker heeft.<br /><br /> **De tweede:** Een virtuele versie van de toepassing die de vereiste dat niet moet worden geïnstalleerd op het primaire apparaat van de gebruiker heeft.|Als bezoekende werknemers zich aanmelden voor een openbare computer, zien ze de toepassingen die ze nodig hebben, weergegeven als pictogrammen op het bureaublad van de computer van de kioskmodus. Wanneer ze de toepassing uitvoert, wordt deze als een virtuele toepassing gestreamd. Deze manier kunnen ze productief kunnen zijn als alsof ze op hun bureaublad zit.|  
|ADAM kiest, kunnen gebruikers weten dat ze hun werkuren in Software Center configureren kunnen en opties selecteren kunnen om te voorkomen dat de software-implementatieactiviteiten tijdens deze periode en wanneer de computer zich in presentatiemodus bevindt.|Omdat gebruikers wanneer Configuration Manager software implementeert naar hun computer bepalen kunnen, is gebruikers blijven productiever tijdens hun werkdag.|  

 Deze configuratiestappen en resultaten zorgen ervoor dat Trey Research werknemers beter kan ondersteunen door toegang tot toepassingen te verzekeren vanaf elk apparaat.  

###  <a name="BKMK_ScenarioUnify"></a>Voorbeeldscenario: Nalevingsbeheer voor apparaten  
 Trey Research wil een geïntegreerde oplossing voor clientbeheer die ervoor zorgt dat hun computers antivirussoftware uitvoeren die automatisch wordt bijgewerkt. Oftewel:  

-   Windows Firewall is ingeschakeld.  
-   Kritieke software-updates zijn geïnstalleerd.  
-   Er zijn specifieke registersleutels ingesteld.  
-   Beheerde mobiele apparaten kunnen installeren of uitvoeren van niet-ondertekende toepassingen.  

Het bedrijf wil deze beveiliging ook uitbreiden naar het internet voor laptops die overschakelen van het intranet naar het internet.  

Jeroen wijst deze bedrijfsvereisten toe aan de volgende scenario's:  

|Vereiste|Huidige clientbeheerstatus|Toekomstige clientbeheerstatus|  
|-----------------|-------------------------------------|------------------------------------|  
|Alle computers voeren antimalwaresoftware uit met bijgewerkte definitiebestanden en ingeschakelde Windows Firewall.|Verschillende computers worden verschillende antimalwareoplossingen die niet zijn altijd up-to-date gehouden uitgevoerd. Hoewel Windows Firewall standaard is ingeschakeld, uitschakelen gebruikers soms.<br /><br /> Er wordt aan gebruikers gevraagd om contact op te nemen met de helpdesk als er malware op hun computer wordt gedetecteerd.|Alle computers voeren dezelfde antimalwareoplossing uit die automatisch de meest recente definitiebestanden downloadt en automatisch Windows Firewall opnieuw inschakelt als gebruikers deze uitschakelen.<br /><br /> De helpdesk wordt automatisch per e-mail verwittigd als er malware wordt gedetecteerd.|  
|Alle computers installeren kritieke software-updates binnen de eerste maand na de release.|Hoewel software-updates zijn geïnstalleerd op computers, installeer veel computers niet automatisch kritieke software-updates pas twee of drie maanden nadat ze zijn vrijgegeven. Dit maakt ze kwetsbaar voor aanvallen tijdens deze periode.<br /><br /> Voor de computers die de kritieke software-updates niet installeren, stuurt de helpdesk eerst e-mails gebruikers vragen om de updates te installeren. Supportengineers verbinden op afstand met computers die niet-compatibel blijven om de ontbrekende software-updates handmatig te installeren.|De huidige compatibiliteitsgraad binnen de opgegeven maand tot boven 95% is verbeterd zonder het verzenden van e-mailberichten of vraag de helpdesk handmatig ze te installeren.|  
|Beveiligingsinstellingen voor specifieke toepassingen worden regelmatig gecontroleerd en hersteld als dit nodig is.|Computers voeren complexe opstartscripts uit die afhankelijk zijn van groepslidmaatschap van de computer om registerwaarden te resetten voor specifieke toepassingen.<br /><br /> Omdat deze scripts alleen tijdens het opstarten worden uitgevoerd en sommige computers zijn dagen aan blijven, kan de helpdesk niet op regelmatige basis configuratieafwijkingen controleren.|Registerwaarden worden gecontroleerd en automatisch hersteld zonder afhankelijk te zijn van groepslidmaatschap van de computer of van het opnieuw opstarten van de computer.|  
|Mobiele apparaten kunnen installeren of onveilige toepassingen worden uitgevoerd.|Gebruikers worden gevraagd niet te downloaden en uitvoeren van mogelijk onveilige toepassingen van Internet. Maar er zijn geen besturingselementen om te controleren of dit afdwingen.|Mobiele apparaten die worden beheerd met Microsoft Intune of Configuration Manager automatisch te voorkomen dat niet-ondertekende toepassingen installeren of uitvoeren.|  
|Laptops die overschakelen van het intranet naar het internet, moeten worden beveiligd.|Voor reizende gebruikers ze vaak geen verbinding maken via de VPN-verbinding per dag. Deze laptops voldoen niet voldaan aan de beveiligingsvereisten.|Een internetverbinding is het enige dat is vereist voor laptops om te blijven voldoen aan de geldende beveiligingsvereisten. Gebruikers hebben geen aanmelden of de VPN-verbinding gebruiken.|  

 Jeroen gebruikt om te voldoen aan de vereisten, deze Configuration Manager-beheermogelijkheden en configuratieopties:  

-   Endpoint Protection  
-   Software-updates  
-   Instellingen voor naleving  
-   Beheer van mobiele apparaten  
-   Clientbeheer via internet  

Hij implementeert ze met behulp van de configuratiestappen in de volgende tabel:  

|Configuratiestappen|Resultaat|  
|-------------------------|-------------|  
|ADAM configureert u Endpoint Protection. Hij schakelt de clientinstelling voor het verwijderen van andere antimalware-oplossingen en schakelt Windows Firewall. Hij configureert automatische implementatieregels, zodat computers regelmatig de nieuwste definitie-updates ontvangen en installeren.|De antimalwareoplossing helpt om alle computers te beschermen met een minimale administratieve verwerkingstijd. Omdat de helpdesk wordt automatisch op de hoogte met een e-mailbericht als malware wordt gedetecteerd, kunnen problemen snel worden opgelost. Dit helpt aanvallen op andere computers te voorkomen.|  
|Definieert onderhoudsvensters voor servers en onderzoekt de voordelen en nadelen van het gebruik van Wake on LAN voor computers die de sluimerstand om te helpen verhogen compatibiliteitspercentage, Adam maakt gebruik van regels voor automatische implementatie.|Compatibiliteit voor kritieke software-updates verhoogt de beveiliging en zorgt er minder voor dat gebruikers of de helpdesk software-updates handmatig moeten installeren.|  
|Jeroen gebruikt compatibiliteitsinstellingen om de aanwezigheid van de opgegeven toepassingen te controleren. Wanneer de toepassingen worden gedetecteerd, worden de configuratie-items vervolgens de registerwaarden te controleren en automatisch hersteld als ze niet compatibel.|Met behulp van configuratie-items en configuratiebasislijnen die zijn geïmplementeerd op alle computers en Controleer voor elke dag de compatibiliteit, moet u niet langer afzonderlijke scripts die afhankelijk van computerlidmaatschap en opnieuw opstarten zijn vereist.|  
|Jeroen gebruikt compatibiliteitsinstellingen voor geregistreerde mobiele apparaten en configureert de Exchange Server-connector zodat niet-ondertekende toepassingen niet kunnen worden geïnstalleerd en uitgevoerd op mobiele apparaten.|Omdat niet-ondertekende toepassingen zijn niet toegestaan, worden mobiele apparaten automatisch beveiligd tegen mogelijk schadelijke toepassingen.|  
|Jeroen zorgt ervoor dat sitesysteemservers en computers beschikken over de PKI-certificaten die Configuration Manager voor HTTPS-verbindingen vereist. Vervolgens installeert hij bijkomende sitesysteemrollen in het perimeternetwerk die clientverbindingen via Internet accepteren.|Computers die overschakelen van het intranet naar het internet, blijven beheerd door Configuration Manager als ze verbonden zijn met het internet. Deze computers niet zijn afhankelijk van de gebruikers op hun computer aanmelden of verbinding maken met de VPN-verbinding.<br /><br /> Die computers blijven beheerd voor antimalware en Windows Firewall, software-updates en configuratie-items. Als gevolg daarvan vergroot de compatibiliteitsgraad automatisch.|  

 Deze configuratiestappen en -resultaten zorgen ervoor dat Trey Research hun compatibiliteitsbeheer voor apparaten kan samenvoegen.  

###  <a name="BKMK_ScenarioSimplify"></a>Voorbeeldscenario: Clientbeheer vereenvoudigen voor apparaten  
 Trey Research wil dat alle nieuwe computers automatisch te installeren van hun bedrijf installatiekopie van Windows 7 wordt uitgevoerd. Nadat de installatiekopie van het besturingssysteem op deze computers is geïnstalleerd, moeten ze worden beheerd en gecontroleerd op aanvullende software die gebruikers installeren. Computers die zeer vertrouwelijke gegevens opslaan, vereisen een meer beperkend beheerbeleid dan andere computers. Voor deze computers kan het nodig zijn om in te stellen dat helpdeskengineers er niet op afstand mee kunnen verbinden, dat invoer van de BitLocker-pincode vereist is voor het opnieuw opstarten, of dat alleen beheerders software kunnen installeren.  

 Jeroen wijst deze bedrijfsvereisten toe aan de volgende scenario's:  

|Vereiste|Huidige clientbeheerstatus|Toekomstige clientbeheerstatus|  
|-----------------|-------------------------------------|------------------------------------|  
|Op nieuwe computers is Windows 7 geïnstalleerd.|De helpdesk installeert en configureert Windows 7 voor gebruikers en stuurt de computer vervolgens naar de respectieve locatie.|Nieuwe computers dan direct door naar de uiteindelijke bestemming, zijn aangesloten op het netwerk en automatisch installeren en configureren van Windows 7.|  
|Computers moeten worden beheerd en bewaakt. Dit omvat het verzamelen van hardware en software-inventarisgegevens om te bepalen wat licentievereisten.|Configuration Manager-client wordt geïmplementeerd met behulp van automatische push-clientinstallatie. De helpdesk onderzoekt mislukte installaties en clients die geen inventarisgegevens versturen wanneer er wordt verwacht.<br /><br /> Fouten zich vaak voor omdat de van installatieafhankelijkheden die niet zijn voldaan en WMI-beschadiging op de client.|Clientinstallatie- en inventarisgegevens die worden verzameld van computers, zijn betrouwbaarder en vereisen bovendien minder interventie van de helpdesk. Rapporten geven informatie weer over softwaregebruik voor licenties.|  
|Sommige computers vereisen een strenger beheerbeleid.|Door het strengere beheerbeleid deze computers op dit moment niet worden beheerd door Configuration Manager.|Deze computers worden beheerd met behulp van Configuration Manager om uitzonderingen zonder bijkomende administratieve verwerkingstijd te behandelen.|  

 Jeroen gebruikt om te voldoen aan de vereisten, deze Configuration Manager-beheermogelijkheden en configuratieopties:  

-   Implementatie van besturingssystemen  
-   Clientimplementatie en clientstatus  
-   Instellingen voor naleving  
-   Clientinstellingen  
-   Inventarisatiemethoden voor en Asset Intelligence  
-   Op rollen gebaseerd beheer  

Hij implementeert ze met behulp van de configuratiestappen in de volgende tabel:  

|Configuratiestappen|Resultaat|  
|-------------------------|-------------|  
|ADAM vastgelegd van de installatiekopie van een besturingssysteem vanaf een computer met Windows 7 is geïnstalleerd en is geconfigureerd voor de specificaties van het bedrijf. Vervolgens implementeert hij het besturingssysteem op de nieuwe computers door gebruik te maken van onbekende computerondersteuning en PXE. Hij installeert tevens de Configuration Manager-client als onderdeel van de implementatie van besturingssystemen.|Nieuwe computers zijn sneller actief en werkend zonder tussenkomst vanuit de helpdesk.|  
|ADAM configureert een automatische gehele site push-clientinstallatie voor de installatie van Configuration Manager-client op computers die zijn gedetecteerd. Dit zorgt ervoor dat computers zonder installatiekopie van de client nog steeds geïnstalleerd, de client zodat de computer wordt beheerd door Configuration Manager.<br /><br /> Adam configureert de clientstatus zo, dat deze eventuele gedetecteerde clientproblemen automatisch herstelt. Hij configureert ook clientinstellingen waarmee de verzameling van inventarisgegevens die is vereist en configureert Asset Intelligence.|Installatie van de client samen met het besturingssysteem is sneller en betrouwbaarder dan wachten voor Configuration Manager voor het detecteren van de computer en vervolgens probeert de clientbronbestanden op de computer installeren. Echter, door de automatische clientpushopties optie is ingeschakeld, bieden u een back-upmethode voor een computer waarop het besturingssysteem is geïnstalleerd voor de installatie van de client wanneer de computer verbinding met het netwerk maakt.<br /><br /> Clientinstellingen zorgen ervoor dat clients hun inventarisgegevens regelmatig naar de site verzenden. Naast de tests van de status van client Hierdoor blijven de client met minimale tussenkomst van de helpdesk. Zo worden WMI-beschadigingen gedetecteerd en automatisch hersteld.<br /><br /> De Asset Intelligence-rapporten helpen bij de controle van softwaregebruik en -licenties.|  
|Ties maakt een verzameling voor de computers die strengere beleidsinstellingen moeten hebben. Hij maakt vervolgens een aangepaste clientapparaatinstelling voor deze verzameling die extern beheer uitgeschakeld, kunt BitLocker-pincode en kan alleen lokale beheerders software installeren.<br /><br /> ADAM configureert op rollen gebaseerd beheer zodat helpdesktechnici deze verzameling van computers niet ziet. Dit zorgt ervoor dat deze computers niet per ongeluk als standaard computers worden beheerd.|Deze computers worden nu beheerd door Configuration Manager, maar met specifieke instellingen, waardoor geen nieuwe site nodig.<br /><br /> De verzameling van deze computers niet zichtbaar voor helpdesktechnici. Dit helpt het risico te verkleinen van de computers verstuurd per ongeluk implementaties en scripts voor Standaardcomputers opgestuurd.|  

 Deze configuratiestappen en -resultaten hebben tot gevolg dat Trey Research met succes clientbeheer voor apparaten vereenvoudigt.  

##  <a name="BKMK_NextSteps"></a> Volgende stappen  
 Voordat u Configuration Manager installeert, kunt u meer vertrouwd raken met enkele basisbeginselen en termen die specifiek is voor Configuration Manager zijn.  

-   Als u bekend met System Center 2012 Configuration Manager bent, raadpleegt u [wat er veranderd in System Center Configuration Manager van System Center 2012 Configuration Manager](../../core/plan-design/changes/what-has-changed-from-configuration-manager-2012.md) om te begrijpen van de nieuwe mogelijkheden.  
-   Zie voor een hoogwaardig technisch overzicht van System Center Configuration Manager, [basisprincipes van System Center Configuration Manager](../../core/understand/fundamentals.md).  

Als u bekend met de basisconcepten bent, gebruikt u de System Center Configuration Manager-documentatie voor hulp bij het succes implementeren en gebruiken van Configuration Manager.  
