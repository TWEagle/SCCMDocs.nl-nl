---
title: Zoeken naar sitebronnen | Microsoft-documenten
description: Informatie over hoe en wanneer System Center Configuration Manager-clients servicelocatie gebruiken om te zoeken naar sitebronnen.
ms.custom: na
ms.date: 2/7/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: ae72df4b-5f5d-4e19-9052-bda28edfbace
caps.latest.revision: 10
author: Brenduns
ms.author: brenduns
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: a181171cc1a92ec4519f4e4b34ca3274a0aa0440
ms.openlocfilehash: 1c9e7ada6a8aa228b30e58865baae0f6e529e6af
ms.contentlocale: nl-nl
ms.lasthandoff: 05/17/2017


---
# <a name="learn-how-clients-find-site-resources-and-services-for-system-center-configuration-manager"></a>Informatie over hoe clients vinden sitebronnen en services voor System Center Configuration Manager

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*

System Center Configuration Manager-clients gebruiken een proces dat genoemd *service locatie* vinden sitesysteem servers waar ze mee kunnen communiceren met en die services bieden clients omgeleid voor gebruik. Informatie over hoe en wanneer clients servicelocatie gebruiken om te zoeken naar sitebronnen, kunt u uw sites ter ondersteuning van met succes clienttaken configureren. Deze configuraties kunnen de site te communiceren met de domein- en netwerkconfiguraties zoals Active Directory Domain Services (AD DS) nodig en DNS. Of ze kunnen ertoe leiden dat u om complexere alternatieven te configureren.  

 Voorbeelden van sitesysteemrollen waarmee services zijn:

 - Het systeem hoofdsiteserver voor clients.
 - Het beheerpunt.
 - Extra sitesysteemservers die de client met, zoals distributiepunten en software communiceren kan-updatepunten.  



##  <a name="bkmk_fund"></a> Fundamentals of service location  
 Een client evalueert de huidige netwerklocatie, protocolvoorkeur communicatie en toegewezen site bij het gebruik van servicelocatiebepaling om een beheerpunt dat met communiceren kan te vinden.  

 **Een client communiceert met een beheerpunt:**  
-   Downloaden van informatie over andere beheerpunten voor de site, zodat deze een lijst met bekende beheerpunten samenstellen (ook wel de *MP-lijst*) voor toekomstige service locatie cycli.  
-   Upload configuratiedetails, zoals inventaris en status.  
-   Download een beleid dat configuraties ingesteld op de client en kan nuttig zijn als de client van de software die kan of moet installeren en andere gerelateerde taken.  
-   Aanvraag voor informatie over extra sitesysteemrollen die voorzien in services die de client is geconfigureerd om te gebruiken. Voorbeelden zijn onder meer distributiepunten voor software die de client kan installeren of een software-updatepunt waaruit om updates te downloaden.  

**Configuration Manager-client maakt een servicelocatie-aanvraag:**  
-   Elke 25 uur van doorlopende bewerking.  
-   De client detecteert wanneer een wijziging in de netwerkconfiguratie of de locatie.  
-   Wanneer de **ccmexec.exe** -service op de computer (de core client-service) wordt gestart.  
-   De client moet wanneer een sitesysteemrol die voorziet in een vereiste service vinden.  

**Wanneer een client probeert te vinden van servers die sitesysteemrollen hosten**, het gebruik van servicelocatiebepaling vinden van een sitesysteemrol die het clientprotocol (HTTP of HTTPS) ondersteunt. Standaard gebruiken clients de meest beveiligde methode die voor hen beschikbaar. Neem het volgende in overweging:  

-   U moet een PKI (Public Key Infrastructure) hebben en u moet PKI-certificaten installeren op clients en servers om HTTPS te gebruiken. Zie [PKI-certificaatvereisten voor System Center Configuration Manager](../../../core/plan-design/network/pki-certificate-requirements.md) voor informatie over het gebruik van certificaten.  

-   Wanneer u een sitesysteemrol implementeert die gebruikmaakt van Internet Information Services (IIS) en communicatie van clients ondersteunt, moet u opgeven of clients verbinding met het sitesysteem maken via HTTP of HTTPS. Als u HTTP gebruikt, dient u ook opties voor ondertekening en versleuteling te overwegen. Zie voor meer informatie [Planning voor ondertekening en versleuteling](../../../core/plan-design/security/plan-for-security.md#BKMK_PlanningForSigningEncryption) in de [plannen van beveiliging in System Center Configuration Manager](../../../core/plan-design/security/plan-for-security.md).  

##  <a name="BKMK_Plan_Service_Location"></a>Servicelocatiebepaling en hoe het toegewezen beheerpunt voor clients wordt bepaald  
Als een client eerst wordt toegewezen aan een primaire site, selecteert het een standaardbeheerpunt voor die site. Primaire sites ondersteunen meerdere beheerpunten, en elke client een beheerpunt als de standaardbeheerpunt onafhankelijk identificeert. Deze standaardbeheerpunt wordt vervolgens van de client toegewezen beheerpunt. (U kunt ook installatieopdrachten client gebruiken om in te stellen het toegewezen beheerpunt voor een client wordt geïnstalleerd.)  

Een client selecteert een beheerpunt om te communiceren met op basis van de client huidige locatie en grens groep netwerkconfiguraties. Zelfs als het een toegewezen beheerpunt heeft, kan dit niet het beheerpunt dat gebruikmaakt van de client zijn.  

    > [!NOTE]  
    >  A client always uses the assigned management point for registration messages and certain policy messages, even when other communications are sent to a proxy or local management point.  

U kunt voorkeursbeheerpunten gebruiken. Voorkeursbeheerpunten zijn beheerpunten van een client toegewezen site die gekoppeld aan een grensgroep die het gebruik van de client zijn naar site systeemservers. Een voorkeur beheerpunt koppeling met een grens van een groep als een sitesysteemserver is vergelijkbaar met hoe distributiepunten of statusmigratiepunten gekoppeld aan een grensgroep zijn. Als u voorkeursbeheerpunten voor de hiërarchie inschakelt, zal een client die een beheerpunt van de toegewezen site gebruikt, proberen eerst een voorkeursbeheerpunt te gebruiken voordat andere beheerpunten worden gebruikt.  

U kunt ook de informatie in de [beheerpuntaffiniteit](http://blogs.technet.com/b/jchalfant/archive/2014/09/22/management-point-affinity-added-in-configmgr-2012-r2-cu3.aspx) blog over TechNet.com management-punt affiniteit configureren. Management-punt affiniteit overschrijvingen het standaardgedrag voor het beheer van toegewezen verwijst en kiest, kan de client gebruikt een of meer specifieke beheerpunten.  

Telkens wanneer die een client moet contact maken met een beheerpunt wordt gecontroleerd de MP-lijst, die lokaal wordt opgeslagen in de Windows Management Instrumentation (WMI). De client maakt een initiële MP-lijst wanneer deze geïnstalleerd. De client vervolgens de lijst periodiek bijgewerkt met informatie over elk beheerpunt in de hiërarchie.  

Wanneer de client geen geldig beheerpunt in de MP-lijst vinden kan, het zoekt in de volgende bronnen voor servicelocatiebepaling in volgorde, totdat een bruikbaar beheerpunt is gevonden:  

1.  Beheerpunt  
2.  AD DS  
3.  DNS  
4.  WINS  

Nadat een client zoekt is en een beheerpunt, het downloaden van de huidige lijst met beheerpunten die beschikbaar in de hiërarchie zijn en wordt de lokale MP-lijst bijgewerkt. Dit geldt ook voor clients die lid zijn van een domein en voor clients die dat niet zijn.  

Bijvoorbeeld, wanneer een Configuration Manager-client die is verbonden met het Internet verbinding met een Internet-gebaseerd beheerpunt maakt, het beheerpunt verzonden naar de client een lijst met beschikbare internetgebaseerde beheerpunten in de site. Op deze manier ontvangen clients in een domein of werkgroep ook de lijst met beheerpunten die mogelijk kunnen worden gebruikt.  

Een client die niet is geconfigureerd voor het Internet is niet opgegeven voor Internet-only facing beheerpunten. Werkgroepclients die zijn geconfigureerd voor Internet communiceren alleen met beheerpunten verbonden met Internet.  

##  <a name="BKMK_MPList"></a> De MP-lijst  
De MP-lijst is de beste bron voor servicelocatiebepaling voor een client, omdat deze een geprioriteerde lijst met beheerpunten die eerder is geïdentificeerd door de client. Deze lijst wordt door elke client gesorteerd op basis van de netwerklocatie wanneer de client de lijst bijgewerkt, en de lijst wordt vervolgens lokaal opgeslagen op de client in WMI.  

### <a name="building-the-initial-mp-list"></a>Samenstellen van de initiële MP-lijst  
Tijdens de installatie van de client de volgende regels gebruikt voor het samenstellen van de initiële MP-lijst van de client:  

-   De initiële lijst bevat beheerpunten die zijn opgegeven tijdens de clientinstallatie (wanneer u gebruikt de **SMSMP**= of **/MP** optie).  
-   De client vraagt AD DS voor gepubliceerde beheerpunten. Om te worden geïdentificeerd vanuit AD DS, moet het beheerpunt van de client toegewezen site en deze moet dezelfde productversie is als de client.  
-   Als er geen beheerpunt is opgegeven tijdens de clientinstallatie en het Active Directory-schema niet is uitgebreid, de client controleert DNS en WINS op gepubliceerde beheerpunten.  
-   Wanneer de client wordt gemaakt van de oorspronkelijke lijst, wordt informatie over een aantal beheerpunten in de hiërarchie mogelijk niet bekend.  

### <a name="organizing-the-mp-list"></a>De MP-lijst ordenen  
Clients ordenen hun lijst met beheerpunten met behulp van de volgende classificaties:  

-   **Proxy**: Een beheerpunt op een secundaire site.  
-   **Lokale**: Elk beheerpunt dat is gekoppeld aan de huidige netwerklocatie van de client, zoals gedefinieerd door de sitegrenzen van de. Houd rekening met de volgende informatie over grenzen:
    -   Wanneer een client tot meer dan een grensgroep behoort, wordt de lijst met lokale beheerpunten bepaald door de samenvoeging van alle grenzen die de huidige netwerklocatie van de client bevatten.  
    -   Lokale beheerpunten zijn meestal naar dat een subset van een client toegewezen beheerpunten, tenzij de client zich op een netwerklocatie die is gekoppeld aan een andere site met beheerpunten die diens grensgroepen onderhoudt.   


-   **Toegewezen**: Elk beheerpunt dat een sitesysteem voor de client toegewezen site.  

U kunt voorkeursbeheerpunten gebruiken. Beheerpunten op een site die niet zijn gekoppeld aan een grensgroep bevinden, of die niet in een grensgroep die is gekoppeld aan de huidige netwerklocatie van een client, worden niet meegenomen voorkeur. Ze worden gebruikt wanneer de client kan een beschikbaar voorkeursbeheerpunt niet identificeren.  

### <a name="selecting-a-management-point-to-use"></a>Een te gebruiken beheerpunt selecteren  
Voor de gebruikelijke communicatie probeert een client te gebruiken een beheerpunt uit de classificaties in de volgende volgorde, op basis van de netwerklocatie van de client:  

1.  Proxy  
2.  Lokaal  
3.  toegewezen  

De client gebruikt het toegewezen beheerpunt echter altijd voor registratieberichten en bepaalde beleidsberichten, zelfs wanneer andere berichten worden verzonden naar een proxy of lokaal beheerpunt.  

In elke classificatie (proxy, lokaal of toegewezen) probeert de client een beheerpunt op basis van voorkeuren in de volgende volgorde:  

1.  Met HTTPS-ondersteuning in een vertrouwd of lokaal forest (wanneer de client is geconfigureerd voor HTTPS-communicatie)  
2.  HTTPS-ondersteuning maar niet in een vertrouwd of lokaal forest (wanneer de client is geconfigureerd voor HTTPS-communicatie)  
3.  HTTP-ondersteuning in een vertrouwd of lokaal forest  
4.  HTTP-ondersteuning maar niet in een vertrouwd of lokaal forest  

Van de set gesorteerd op Voorkeuren beheerpunten, probeert de client het eerste beheerpunt gebruiken in de lijst. Deze gesorteerde lijst beheerpunten is willekeurig en kan niet worden gerangschikt. De volgorde van de lijst kan telkens worden gewijzigd wanneer de MP-lijst wordt bijgewerkt door de client.  

Als een client geen contact met het eerste beheerpunt kan maken, probeert het elke opeenvolgende beheerpunt in de lijst. Er wordt geprobeerd voorkeursbeheerpunt in de classificatie voordat u probeert de niet-voorkeursbeheerpunten. Als een client met een beheerpunt in de classificatie communiceren kan, probeert ze te maken met een voorkeursbeheerpunt in de volgende classificatie enzovoort, totdat een bruikbaar beheerpunt is gevonden.  

Nadat een client communicatie met een beheerpunt tot stand brengt, blijft hetzelfde beheerpunt gebruiken totdat:  

-   25 uur zijn verstreken.  
-   De client is niet kan communiceren met het beheerpunt tot vijf keer gedurende een periode van tien minuten.

De client vervolgens selecteert willekeurig een nieuw beheerpunt te gebruiken.  

##  <a name="bkmk_ad"></a> Active Directory  
Clients die lid zijn van een domein kunnen AD DS gebruiken voor servicelocatiebepaling. Hiervoor moeten sites [gegevens publiceren naar Active Directory](http://technet.microsoft.com/library/hh696543.aspx).  

Een client kan AD DS gebruiken voor servicelocatie wanneer alle volgende voorwaarden voldaan wordt:  

-   De Active Directory [schema is uitgebreid](https://technet.microsoft.com/library/mt345589.aspx) of is uitgebreid voor System Center 2012 Configuration Manager.  
-   De [Active Directory-forest is geconfigureerd voor publicatie](http://technet.microsoft.com/library/hh696542.aspx), en Configuration Manager-sites zijn geconfigureerd voor publicatie.  
-   De clientcomputer is lid van een Active Directory-domein en heeft toegang tot een algemene-catalogusserver.  

Als een client een beheerpunt te gebruiken voor servicelocatie uit AD DS vinden kunt, wordt geprobeerd DNS te gebruiken.  

##  <a name="bkmk_dns"></a> DNS  
Clients op intranet kunnen DNS gebruiken voor servicelocatiebepaling. Hiervoor moet ten minste één site in een hiërarchie informatie over beheerpunten publiceren naar DNS.  

Overweeg het gebruik van DNS voor servicelocatiebepaling als aan de volgende voorwaarden wordt voldaan:
-   Het AD DS-schema is niet uitgebreid ter ondersteuning van Configuration Manager.
-   Clients op het intranet bevinden zich in een forest dat niet is ingeschakeld voor publicatie van de Configuration Manager.  
-   Clients bevinden zich op werkgroepcomputers en ze zijn niet geconfigureerd voor clientbeheer alleen op internet. (Een werkgroepclient die is geconfigureerd voor Internet communiceert alleen met beheerpunten voor Internet facing en maakt geen gebruik van DNS voor servicelocatiebepaling.)  
-   U kunt [clients configureren voor het zoeken van beheerpunten via DNS](http://technet.microsoft.com/library/gg682055).  

Wanneer een website records voor servicelocatiebepaling van beheerpunten publiceert naar DNS:  

-   Is de publicatie alleen van toepassing op beheerpunten die clientverbindingen van intranet accepteren.  
-   Wordt bij de publicatie een Service Location Resource Record (SRV RR) toegevoegd aan de DNS-zone van de beheerpuntcomputer. Er moet een overeenkomende hostvermelding in DNS staan voor de computer.  

Standaard zoeken clients domein in DNS naar beheerpuntrecords vanuit het lokale domein van de client. U kunt een clienteigenschap configureren met een domeinachtervoegsel voor een domein dat is gepubliceerd naar DNS.  

Zie voor meer informatie over het configureren van de clienteigenschap van DNS-achtervoegsel [hoe clientcomputers te vinden van beheerpunten via DNS-publishing in System Center Configuration Manager configureren](../../../core/clients/deploy/configure-client-computers-to-find-management-points-by-using-dns-publishing.md).  

Als een client een beheerpunt te gebruiken voor servicelocatie via DNS vinden kan, wordt geprobeerd WINS te gebruiken.  

### <a name="publish-management-points-to-dns"></a>Beheerpunten publiceren naar DNS  
De volgende voorwaarden moeten waar zijn om beheerpunten te publiceren naar DNS:  

-   Uw DNS-servers ondersteunen servicelocatiebronrecords door minstens versie 8.1.2 van BIND te gebruiken.  
-   De opgegeven intranet-FQDN's voor de beheerpunten in Configuration Manager hebben hostvermeldingen (bv, bronnen) in DNS.  

> [!IMPORTANT]  
>  Configuration Manager voor DNS-publicaties biedt geen ondersteuning voor een niet-aaneengesloten naamruimte. Als u een niet-aaneengesloten naamruimte hebt, kunt u handmatig beheerpunten publiceren naar DNS of gebruik een van de andere servicelocatiemethoden gebruiken die zijn beschreven in deze sectie.  

**Als uw DNS-servers automatische updates ondersteunen**, kunt u Configuration Manager automatisch om beheerpunten te publiceren op het intranet naar DNS configureren of u kunt deze records ook handmatig publiceren naar DNS. Als beheerpunten naar DNS worden gepubliceerd, worden hun intranet-FQDN en poortnummer gepubliceerd in het servicelocatierecord (SRV-record). Op een site in de eigenschappen van Beheerpuntonderdeel van de site configureert u DNS-publishing. Zie voor meer informatie [onderdelen voor System Center Configuration Manager Site](../../../core/servers/deploy/configure/site-components.md).  

**Als uw DNS-zone is ingesteld op "Alleen Secure" voor dynamische updates**, alleen het eerste beheerpunt te publiceren naar DNS is dus met standaardmachtigingen kunt doen.

Als er slechts één beheerpunt kunt kunnen publiceren en de DNS-record wijzigen en de beheerpuntserver is in orde, clients de volledige MP-lijst van dat management wijst en krijgt vervolgens hun voorkeur beheerpunt te vinden.


**U kunt beheerpunten handmatig naar DNS publiceren als uw DNS-servers geen automatische updates**, maar wel servicelocatierecords ondersteunen. Hiervoor moet u handmatig het servicelocatiebronrecord (SRV RR) in DNS opgeven.  

Configuration Manager ondersteunt RFC 2782 voor servicelocatierecords. Deze records hebben de volgende indeling: *_service._proto.naam TTL klasse SRV prioriteit gewicht poort doel*  

Geef voor het publiceren van een beheerpunt naar Configuration Manager, de volgende waarden:  

-   **_Service**: Voer **_mssms_mp**_&lt;sitecode\>, waarbij &lt;sitecode\> sitecode van het beheerpunt.  
-   **._Proto**: Geef **._tcp**.  
-   **. Naam**: Voer bijvoorbeeld het DNS-achtervoegsel van het beheerpunt **contoso.com**.  
-   **TTL**: Voer **14400**, dit is gelijk aan vier uur.  
-   **Klasse**: Geef **IN** (in overeenstemming met RFC 1035).  
-   **Prioriteit**: Dit veld niet wordt gebruikt door Configuration Manager.
-   **Gewicht**: Dit veld niet wordt gebruikt door Configuration Manager.  
-   **Poort**: Voer het poortnummer dat het beheerpunt, bijvoorbeeld gebruikt **80** voor HTTP en **443** voor HTTPS.  

    > [!NOTE]  
    >  De poort voor de SRV-record moet overeenkomen met de communicatiepoort die gebruikmaakt van het beheerpunt. Dit is standaard **80** voor HTTP-communicatie en **443** voor HTTPS-communicatie.  

-   **Doel**: Voer het intranet FQDN-naam die is opgegeven voor het sitesysteem dat is geconfigureerd met de rol beheerpunt site.  

Als u Windows Server DNS gebruikt, kunt u de volgende procedure gebruiken om dit DNS-record in te voeren voor intranet-beheerpunten. Als u een verschillende implementatie voor DNS gebruikt, dient u de informatie in deze sectie over de veldwaarden te gebruiken en de DNS-documentatie te raadplegen om deze procedure aan te passen.  

##### <a name="to-configure-automatic-publishing"></a>Automatische publicatie configureren:  

1.  Vouw in de Configuration Manager-console **beheer** > **siteconfiguratie** > **Sites**.  

2.  Selecteer uw site en kies vervolgens **Siteonderdelen configureren**.  

3.  Kies **beheerpunt**.  

4.  Selecteer de beheerpunten die u wilt publiceren. (Deze selectie geldt voor publicatie naar AD DS en DNS.)  

5.  Schakel het selectievakje in om te publiceren naar DNS. Dit vak:  

    -   Hiermee kunt u selecteren welke beheerpunten publiceren naar DNS.  

    -   Niet configureren publicatie naar AD DS.  

##### <a name="to-manually-publish-management-points-to-dns-on-windows-server"></a>Handmatig beheerpunten publiceren naar DNS op Windows Server  

1.  Geef de intranet-FQDN's van sitesystemen in de Configuration Manager-console.  

2.  Selecteer de DNS-zone voor de beheerpuntcomputer in de DNS-beheerconsole.  

3.  Verifieer of er een hostrecord is (A of AAAA) voor de intranet-FQDN van het sitesysteem. Maak dit record als het niet bestaat.  

4.  Met behulp van de **nieuwe andere Records** optie, kiest u **servicelocatie (SRV)** in de **bronrecordtype** dialoogvenster Kies **Record maken**, voer de volgende informatie en kies vervolgens **gedaan**:  

    -   **Domein**: Voer indien nodig, de DNS-achtervoegsel van het beheerpunt, bijvoorbeeld **contoso.com**.  
    -   **Service**: Type **_mssms_mp**_&lt;sitecode\>, waarbij &lt;sitecode\> sitecode van het beheerpunt.  
    -   **Protocol**: Type **_tcp**.  
    -   **Prioriteit**: Dit veld niet wordt gebruikt door Configuration Manager.  
    -   **Gewicht**: Dit veld niet wordt gebruikt door Configuration Manager.  
    -   **Poort**: Voer het poortnummer dat het beheerpunt, bijvoorbeeld gebruikt **80** voor HTTP en **443** voor HTTPS.  

        > [!NOTE]  
        >  De poort voor de SRV-record moet overeenkomen met de communicatiepoort die gebruikmaakt van het beheerpunt. Dit is standaard **80** voor HTTP-communicatie en **443** voor HTTPS-communicatie.  

    -   **Host die deze service aanbiedt**: Voer het intranet FQDN-naam die is opgegeven voor het sitesysteem dat is geconfigureerd met de rol beheerpunt site.  

Herhaal deze stappen voor elk beheerpunt op het intranet dat u wilt publiceren naar DNS.  

##  <a name="bkmk_wins"></a> WINS  
Als andere servicelocatiemechanismen mislukken, kunnen clients een initieel beheerpunt vinden door WINS te controleren.  

Standaard publiceert een primaire site naar WINS het eerste beheerpunt op de site die is geconfigureerd voor HTTP en het eerste beheerpunt dat is geconfigureerd voor HTTPS.  

Als u niet wilt dat clients een HTTP-beheerpunt in WINS vinden, kunt u clients configureren met de Client.msi-eigenschap **SMSDIRECTORYLOOKUP=NOWINS**van CCMSetup.exe.  

