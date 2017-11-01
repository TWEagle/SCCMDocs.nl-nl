---
title: Site-informatie vinden
titleSuffix: Configuration Manager
description: Meer informatie over hoe en wanneer de System Center Configuration Manager-clients servicelocatie zoeken naar sitebronnen gebruiken.
ms.custom: na
ms.date: 2/7/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: ae72df4b-5f5d-4e19-9052-bda28edfbace
caps.latest.revision: "10"
author: Brenduns
ms.author: brenduns
manager: angrobe
ms.openlocfilehash: e64b2c4242903143b677189e3bd4c8f32ebace20
ms.sourcegitcommit: c236214b2fcc13dae7bad96d7fb33f692868191d
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/12/2017
---
# <a name="learn-how-clients-find-site-resources-and-services-for-system-center-configuration-manager"></a>Meer informatie over hoe clients siteresources en -services voor System Center Configuration Manager vinden

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*

System Center Configuration Manager-clients gebruiken een proces genaamd *service locatie* om sitesysteemservers te vinden servers die ze kunnen communiceren en die services bieden die clients moeten gebruiken. Begrijpen hoe en wanneer clients de servicelocatie gebruiken sitebronnen te vinden, kunt u uw sites voor de ondersteuning van clienttaken configureren. Deze netwerkconfiguraties vereisen mogelijk dat de site om te communiceren met de domein- en netwerkconfiguraties als Active Directory Domain Services (AD DS) en DNS. Of ze kunnen u complexere alternatieven te configureren.  

 Voorbeelden van sitesysteemrollen die services leveren zijn:

 - De belangrijkste sitesysteemserver voor clients.
 - Het beheerpunt.
 - Extra sitesysteemservers waarmee de client, zoals distributiepunten en software communiceren kan-updatepunten.  



##  <a name="bkmk_fund"></a> Fundamentals of service location  
 Een client evalueert de huidige netwerklocatie, protocolvoorkeur communicatie en toegewezen site bij het gebruik van servicelocatiebepaling om een beheerpunt dat met communiceren kan te vinden.  

 **Een client communiceert met een beheerpunt:**  
-   Downloaden van informatie over andere beheerpunten voor de site, zodat deze voor een lijst met bekende beheerpunten samen kan (ook wel de *MP-lijst*) voor toekomstige service locatie cycli.  
-   Configuratiegegevens, zoals inventaris- en statusgegevens uploaden.  
-   Download een beleid dat configuraties ingesteld op de client en de client van de software die kan of moet installeren en andere gerelateerde taken kan informeren.  
-   Aanvraag voor informatie over extra sitesysteemrollen die services leveren die de client is geconfigureerd om te gebruiken. Voorbeelden zijn onder meer distributiepunten voor software die de client kan installeren, of een software-updatepunt uit waarvoor u updates wilt weergeven.  

**Een Configuration Manager-client maakt een servicelocatie-aanvraag:**  
-   Elke 25 uur continu uitvoeren.  
-   De client detecteert wanneer een wijziging in de netwerkconfiguratie of de locatie.  
-   Wanneer de **ccmexec.exe** -service op de computer (de core client-service) wordt gestart.  
-   Wanneer de client moet een sitesysteemrol waarmee een vereiste service kunnen vinden.  

**Wanneer een client probeert te vinden van servers die sitesysteemrollen hosten**, het gebruik van servicelocatiebepaling vinden van een sitesysteemrol die het clientprotocol (HTTP of HTTPS) ondersteunt. Standaard gebruiken clients de meest beveiligde methode die voor hen beschikbaar. Neem het volgende in overweging:  

-   U moet een PKI (Public Key Infrastructure) hebben en u moet PKI-certificaten installeren op clients en servers om HTTPS te gebruiken. Zie [PKI-certificaatvereisten voor System Center Configuration Manager](../../../core/plan-design/network/pki-certificate-requirements.md) voor informatie over het gebruik van certificaten.  

-   Wanneer u een sitesysteemrol implementeert die gebruikmaakt van Internet Information Services (IIS) en communicatie van clients ondersteunt, moet u opgeven of clients verbinding met het sitesysteem maken via HTTP of HTTPS. Als u HTTP gebruikt, dient u ook opties voor ondertekening en versleuteling te overwegen. Zie voor meer informatie [Planning voor ondertekening en versleuteling](../../../core/plan-design/security/plan-for-security.md#BKMK_PlanningForSigningEncryption) in de [beveiliging in System Center Configuration Manager plannen](../../../core/plan-design/security/plan-for-security.md).  

##  <a name="BKMK_Plan_Service_Location"></a>Servicelocatiebepaling en hoe het toegewezen beheerpunt voor clients wordt bepaald  
Als een client eerst wordt toegewezen aan een primaire site, selecteert u een standaardbeheerpunt voor die site. Primaire sites ondersteunen meerdere beheerpunten en elke client bepaalt onafhankelijk een beheerpunt als het standaardbeheerpunt. Dit standaardbeheerpunt wordt vervolgens een van de client toegewezen beheerpunt. (U kunt ook clientinstallatieopdrachten gebruiken om in te stellen het toegewezen beheerpunt voor een client wanneer deze geïnstalleerd.)  

Een client selecteert een beheerpunt om te communiceren met op basis van de client huidige locatie en grens groep netwerkconfiguraties. Hoewel dit een toegewezen beheerpunt heeft, kan dit niet het beheerpunt dat gebruikmaakt van de client zijn.  

    > [!NOTE]  
    >  A client always uses the assigned management point for registration messages and certain policy messages, even when other communications are sent to a proxy or local management point.  

U kunt voorkeursbeheerpunten gebruiken. Voorkeursbeheerpunten zijn beheerpunten van een client toegewezen site die zijn gekoppeld aan een grensgroep die site systeemservers vinden op de client wordt gebruikt. Een voorkeursbeheerpunt van koppeling met een grens van een groep als een sitesysteemserver is vergelijkbaar met hoe distributiepunten of statusmigratiepunten gekoppeld aan een grensgroep zijn. Als u voorkeursbeheerpunten voor de hiërarchie inschakelt, zal een client die een beheerpunt van de toegewezen site gebruikt, proberen eerst een voorkeursbeheerpunt te gebruiken voordat andere beheerpunten worden gebruikt.  

U kunt ook de informatie in de [beheerpuntaffiniteit](http://blogs.technet.com/b/jchalfant/archive/2014/09/22/management-point-affinity-added-in-configmgr-2012-r2-cu3.aspx) blog op TechNet.com voor het configureren van de affiniteit met het beheerpunt. Management-punt affiniteit onderdrukkingen het standaardgedrag voor toegewezen beheerpunten en kunt de client gebruiken een of meer specifieke beheerpunten.  

Telkens wanneer die een client moet contact maken met een beheerpunt, controleert deze de MP-lijst, die lokaal wordt opgeslagen in de Windows Management Instrumentation (WMI). De client maakt een initiële MP-lijst wanneer deze geïnstalleerd. De client vervolgens de lijst periodiek bijgewerkt met informatie over elk beheerpunt in de hiërarchie.  

Als de client een geldig beheerpunt in de MP-lijst vinden kan, doorzocht het de volgende bronnen voor servicelocatiebepaling in volgorde, totdat er een beheerpunt dat kan worden gebruikt:  

1.  Beheerpunt  
2.  AD DS  
3.  DNS  
4.  WINS  

Nadat een client met succes zoekt en neemt contact op met een beheerpunt, het downloaden van de huidige lijst met beheerpunten die beschikbaar in de hiërarchie zijn en wordt de lokale MP-lijst bijgewerkt. Dit geldt ook voor clients die lid zijn van een domein en voor clients die dat niet zijn.  

Bijvoorbeeld, wanneer een Configuration Manager-client die zich op het Internet verbinding met een Internet-gebaseerd beheerpunt maakt, het beheerpunt verzonden naar de client een lijst met beschikbare internetgebaseerde beheerpunten in de site. Op deze manier ontvangen clients in een domein of werkgroep ook de lijst met beheerpunten die mogelijk kunnen worden gebruikt.  

Een client die niet is geconfigureerd voor het Internet is niet opgegeven voor Internet-facing-only-beheerpunten. Werkgroepclients die zijn geconfigureerd voor Internet communiceren alleen met internetverbinding beheerpunten.  

##  <a name="BKMK_MPList"></a> De MP-lijst  
De MP-lijst is de bron van de locatie voorkeur service voor een client, omdat deze een geprioriteerde lijst met beheerpunten die de client eerder hebt geïdentificeerd. Deze lijst wordt door elke client gesorteerd op basis van de netwerklocatie wanneer de client de lijst bijgewerkt, en de lijst wordt vervolgens lokaal opgeslagen op de client in WMI.  

### <a name="building-the-initial-mp-list"></a>Samenstellen van de initiële MP-lijst  
Tijdens de installatie van de client de volgende regels gebruikt voor het samenstellen van de initiële MP-lijst van de client:  

-   De initiële lijst bevat beheerpunten die zijn opgegeven tijdens de clientinstallatie (wanneer u gebruikt de **SMSMP**= of **/MP** optie).  
-   De client vraagt gepubliceerde beheerpunten AD DS. Als u wilt worden geïdentificeerd vanuit AD DS, moet het beheerpunt van de client toegewezen site en deze moet dezelfde versie van het product als de client.  
-   Als er geen beheerpunt is opgegeven tijdens de clientinstallatie en het Active Directory-schema niet is uitgebreid, controleert de client DNS en WINS op gepubliceerde beheerpunten.  
-   Wanneer de client wordt gemaakt van de initiële lijst, wordt informatie over een aantal beheerpunten in de hiërarchie mogelijk niet bekend.  

### <a name="organizing-the-mp-list"></a>De MP-lijst ordenen  
Clients ordenen hun lijst met beheerpunten met behulp van de volgende classificaties:  

-   **Proxy**: Een beheerpunt op een secundaire site.  
-   **Lokale**: Elk beheerpunt dat is gekoppeld aan de huidige netwerklocatie van de client, zoals gedefinieerd door de sitegrenzen. Houd rekening met de volgende informatie over de grenzen van:
    -   Wanneer een client tot meer dan een grensgroep behoort, wordt de lijst met lokale beheerpunten bepaald door de samenvoeging van alle grenzen die de huidige netwerklocatie van de client bevatten.  
    -   Lokale beheerpunten zijn meestal naar dat een subset van een client toegewezen beheerpunten, tenzij de client zich op een netwerklocatie die is gekoppeld aan een andere site met beheerpunten die diens grensgroepen onderhoudt.   


-   **Toegewezen**: Elk beheerpunt dat een sitesysteem voor de client toegewezen site.  

U kunt voorkeursbeheerpunten gebruiken. Beheerpunten op een site die niet zijn gekoppeld aan een grensgroep, of die niet zijn opgenomen in een grensgroep die is gekoppeld aan de huidige netwerklocatie van de client, worden niet beschouwd als voorkeur. Ze worden gebruikt wanneer de client kan een beschikbaar voorkeursbeheerpunt niet identificeren.  

### <a name="selecting-a-management-point-to-use"></a>Een te gebruiken beheerpunt selecteren  
Voor de gebruikelijke communicatie probeert een client te gebruiken een beheerpunt op van de classificaties in de volgende volgorde, op basis van de netwerklocatie van de client:  

1.  Proxy  
2.  Lokaal  
3.  toegewezen  

De client gebruikt het toegewezen beheerpunt echter altijd voor registratieberichten en bepaalde beleidsberichten, zelfs wanneer andere berichten worden verzonden naar een proxy of lokaal beheerpunt.  

In elke classificatie (proxy, lokaal of toegewezen) probeert de client een beheerpunt op basis van voorkeuren in de volgende volgorde:  

1.  Met HTTPS-ondersteuning in een vertrouwd of lokaal forest (wanneer de client is geconfigureerd voor HTTPS-communicatie)  
2.  HTTPS-ondersteuning maar niet in een vertrouwd of lokaal forest (wanneer de client is geconfigureerd voor HTTPS-communicatie)  
3.  HTTP-ondersteuning in een vertrouwd of lokaal forest  
4.  HTTP-ondersteuning maar niet in een vertrouwd of lokaal forest  

Uit de set met beheerpunten, gesorteerd op Voorkeuren, probeert de client het eerste beheerpunt gebruiken op de lijst. Deze gesorteerde lijst beheerpunten is willekeurig en kan niet worden gerangschikt. De volgorde van de lijst kan telkens wanneer de MP-lijst bijgewerkt door de client kunt wijzigen.  

Wanneer een client kan geen contact is gelegd met het eerste beheerpunt, wordt geprobeerd elk opeenvolgende beheerpunt in de lijst. Elke voorkeursbeheerpunt in de classificatie probeert voordat u probeert de niet-voorkeursbeheerpunten. Als een client kan niet met een beheerpunt in de classificatie communiceren, probeert het contact opnemen met een voorkeursbeheerpunt in de volgende classificatie enzovoort, totdat een bruikbaar beheerpunt is gevonden.  

Nadat een client tot stand communicatie met een beheerpunt brengt, blijft hetzelfde beheerpunt tot gebruiken:  

-   25 uur zijn verstreken.  
-   De client is kan niet communiceren met het beheerpunt voor vijf pogingen gedurende een periode van tien minuten.

De client selecteert vervolgens willekeurig een nieuw beheerpunt te gebruiken.  

##  <a name="bkmk_ad"></a> Active Directory  
Clients die lid zijn van een domein kunnen AD DS gebruiken voor servicelocatiebepaling. Hiervoor moeten sites [gegevens publiceren naar Active Directory](http://technet.microsoft.com/library/hh696543.aspx).  

Een client kan AD DS gebruiken voor servicelocatie wanneer alle volgende voorwaarden voldaan wordt:  

-   De Active Directory [schema is uitgebreid](https://technet.microsoft.com/library/mt345589.aspx) of is uitgebreid voor System Center 2012 Configuration Manager.  
-   De [Active Directory-forest is geconfigureerd voor publicatie](http://technet.microsoft.com/library/hh696542.aspx), en Configuration Manager-sites zijn geconfigureerd voor publicatie.  
-   De clientcomputer is lid van een Active Directory-domein en heeft toegang tot een algemene-catalogusserver.  

Als een client een beheerpunt om te gebruiken voor servicelocatie uit AD DS niet wordt gevonden, wordt geprobeerd om DNS te gebruiken.  

##  <a name="bkmk_dns"></a> DNS  
Clients op intranet kunnen DNS gebruiken voor servicelocatiebepaling. Hiervoor moet ten minste één site in een hiërarchie informatie over beheerpunten publiceren naar DNS.  

Overweeg het gebruik van DNS voor servicelocatiebepaling als aan de volgende voorwaarden wordt voldaan:
-   De AD DS-schema is niet uitgebreid ter ondersteuning van Configuration Manager.
-   Clients op het intranet bevinden zich in een forest dat niet is ingeschakeld voor publicatie van de Configuration Manager.  
-   Clients bevinden zich op werkgroepcomputers en ze zijn niet geconfigureerd voor clientbeheer alleen op internet. (Een werkgroepclient die is geconfigureerd voor Internet communiceert alleen met beheerpunten internetgerichte en maakt geen gebruik van DNS voor servicelocatiebepaling.)  
-   U kunt [clients configureren voor het zoeken van beheerpunten via DNS](http://technet.microsoft.com/library/gg682055).  

Wanneer een website records voor servicelocatiebepaling van beheerpunten publiceert naar DNS:  

-   Is de publicatie alleen van toepassing op beheerpunten die clientverbindingen van intranet accepteren.  
-   Wordt bij de publicatie een Service Location Resource Record (SRV RR) toegevoegd aan de DNS-zone van de beheerpuntcomputer. Er moet een overeenkomende hostvermelding in DNS staan voor de computer.  

Standaard zoeken clients domein beheerpuntrecords vanuit het lokale domein van de client naar DNS. U kunt een clienteigenschap die een domeinachtervoegsel voor een domein dat is gepubliceerd naar DNS configureren.  

Zie voor meer informatie over het configureren van de clienteigenschap van DNS-achtervoegsel [configureren om beheerpunten te vinden met DNS-publishing in System Center Configuration Manager-clientcomputers](../../../core/clients/deploy/configure-client-computers-to-find-management-points-by-using-dns-publishing.md).  

Als een client een beheerpunt te gebruiken voor servicelocatie via DNS vinden kan, wordt geprobeerd WINS te gebruiken.  

### <a name="publish-management-points-to-dns"></a>Beheerpunten publiceren naar DNS  
De volgende voorwaarden moeten waar zijn om beheerpunten te publiceren naar DNS:  

-   Uw DNS-servers ondersteunen servicelocatiebronrecords door minstens versie 8.1.2 van BIND te gebruiken.  
-   De opgegeven intranet-FQDN's voor de beheerpunten in Configuration Manager hebben hostvermeldingen (bijvoorbeeld een records) in DNS.  

> [!IMPORTANT]  
>  Configuration Manager DNS publiceren biedt geen ondersteuning voor een niet-aaneengesloten naamruimte. Als u een niet-aaneengesloten naamruimte hebt, kunt u handmatig beheerpunten publiceren naar DNS of gebruik een van de andere servicelocatiemethoden gebruiken die worden beschreven in deze sectie.  

**Als uw DNS-servers automatische updates ondersteunen**, kunt u Configuration Manager automatisch publiceren van beheerpunten op het intranet naar DNS configureren of u kunt deze records ook handmatig publiceren naar DNS. Als beheerpunten naar DNS worden gepubliceerd, worden hun intranet-FQDN en poortnummer gepubliceerd in het servicelocatierecord (SRV-record). U kunt DNS-publishing configureren op een site in de eigenschappen van Beheerpuntonderdeel van de site. Zie voor meer informatie [Siteonderdelen voor System Center Configuration Manager](../../../core/servers/deploy/configure/site-components.md).  

**Als uw DNS-zone is ingesteld op 'Alleen Secure' voor dynamische updates**, alleen het eerste beheerpunt te publiceren naar DNS is dus met standaardmachtigingen kunt doen.

Als er slechts één beheerpunt kan publiceren en de DNS-record wijzigen en de beheerpuntserver is in orde, ophalen clients de volledige MP-lijst van dat management wijst en gaat u naar hun voorkeursbeheerpunt.


**U kunt beheerpunten handmatig naar DNS publiceren als uw DNS-servers geen automatische updates**, maar wel servicelocatierecords ondersteunen. Hiervoor moet u handmatig het servicelocatiebronrecord (SRV RR) in DNS opgeven.  

Configuration Manager ondersteunt RFC 2782 voor servicelocatierecords. Deze records hebben de volgende indeling: *_service._proto.naam TTL klasse SRV prioriteit gewicht poort doel*  

Geef voor het publiceren van een beheerpunt naar Configuration Manager, de volgende waarden:  

-   **_Service**: Voer **_mssms_mp**_&lt;sitecode\>, waarbij &lt;sitecode\> sitecode van het beheerpunt.  
-   **._Proto**: Geef **._tcp**.  
-   **. Naam**: Voer het DNS-achtervoegsel van het beheerpunt, bijvoorbeeld **contoso.com**.  
-   **TTL**: Voer **14400**, dit is vier uur.  
-   **Klasse**: Geef **IN** (in overeenstemming met RFC 1035).  
-   **Prioriteit**: Configuration Manager maakt geen gebruik van dit veld.
-   **Gewicht**: Configuration Manager maakt geen gebruik van dit veld.  
-   **Poort**: Voer het poortnummer dat het beheerpunt, bijvoorbeeld gebruikt **80** voor HTTP en **443** voor HTTPS.  

    > [!NOTE]  
    >  De poort SRV-record moet overeenkomen met de communicatiepoort die gebruikmaakt van het beheerpunt. Dit is standaard **80** voor HTTP-communicatie en **443** voor HTTPS-communicatie.  

-   **Doel**: Voer de intranet-FQDN die is opgegeven voor het sitesysteem dat is geconfigureerd met de rol beheerpunt site.  

Als u Windows Server DNS gebruikt, kunt u de volgende procedure gebruiken om dit DNS-record in te voeren voor intranet-beheerpunten. Als u een verschillende implementatie voor DNS gebruikt, dient u de informatie in deze sectie over de veldwaarden te gebruiken en de DNS-documentatie te raadplegen om deze procedure aan te passen.  

##### <a name="to-configure-automatic-publishing"></a>Automatische publicatie configureren:  

1.  Vouw in de Configuration Manager-console **beheer** > **siteconfiguratie** > **Sites**.  

2.  Selecteer uw site en kies vervolgens **Siteonderdelen configureren**.  

3.  Kies **beheerpunt**.  

4.  Selecteer de beheerpunten die u wilt publiceren. (Deze selectie geldt voor publicatie naar AD DS en DNS.)  

5.  Schakel het selectievakje in om te publiceren naar DNS. Dit vak:  

    -   Kunt u selecteren welke beheerpunten publiceren naar DNS.  

    -   Configureert geen publicatie naar AD DS.  

##### <a name="to-manually-publish-management-points-to-dns-on-windows-server"></a>Handmatig beheerpunten publiceren naar DNS op Windows Server  

1.  Geef de intranet-FQDN's van sitesystemen in de Configuration Manager-console.  

2.  Selecteer de DNS-zone voor de beheerpuntcomputer in de DNS-beheerconsole.  

3.  Verifieer of er een hostrecord is (A of AAAA) voor de intranet-FQDN van het sitesysteem. Maak dit record als het niet bestaat.  

4.  Met behulp van de **nieuwe andere Records** optie, kiest u **servicelocatie (SRV)** in de **bronrecordtype** dialoogvenster Kies **-Record maken**, voer de volgende informatie en kies vervolgens **gedaan**:  

    -   **Domein**: Voer, indien nodig de DNS-achtervoegsel van het beheerpunt, bijvoorbeeld **contoso.com**.  
    -   **Service**: Type **_mssms_mp**_&lt;sitecode\>, waarbij &lt;sitecode\> sitecode van het beheerpunt.  
    -   **Protocol**: Type **_tcp**.  
    -   **Prioriteit**: Configuration Manager maakt geen gebruik van dit veld.  
    -   **Gewicht**: Configuration Manager maakt geen gebruik van dit veld.  
    -   **Poort**: Voer het poortnummer dat het beheerpunt, bijvoorbeeld gebruikt **80** voor HTTP en **443** voor HTTPS.  

        > [!NOTE]  
        >  De poort SRV-record moet overeenkomen met de communicatiepoort die gebruikmaakt van het beheerpunt. Dit is standaard **80** voor HTTP-communicatie en **443** voor HTTPS-communicatie.  

    -   **Host die deze service aanbiedt**: Voer de intranet-FQDN die is opgegeven voor het sitesysteem dat is geconfigureerd met de rol beheerpunt site.  

Herhaal deze stappen voor elk beheerpunt op het intranet dat u wilt publiceren naar DNS.  

##  <a name="bkmk_wins"></a> WINS  
Als andere servicelocatiemechanismen mislukken, kunnen clients een initieel beheerpunt vinden door WINS te controleren.  

Standaard publiceert een primaire site naar WINS het eerste beheerpunt op de site die is geconfigureerd voor HTTP en het eerste beheerpunt dat is geconfigureerd voor HTTPS.  

Als u niet wilt dat clients een HTTP-beheerpunt in WINS vinden, kunt u clients configureren met de Client.msi-eigenschap **SMSDIRECTORYLOOKUP=NOWINS**van CCMSetup.exe.  
