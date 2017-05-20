---
title: De communicatie tussen de eindpunten | Microsoft-documenten
description: Meer informatie over hoe System Center Configuration Manager site-systemen en -onderdelen via een netwerk communiceren.
ms.custom: na
ms.date: 10/06/2016
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 68fe0e7e-351e-4222-853a-877475adb589
caps.latest.revision: 10
author: Brenduns
ms.author: brenduns
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 2ac9f98dc7b455d3b72d794d4311863186ed53ef
ms.openlocfilehash: cd94f9ccc7e196b30e5dc7ae9368d073b7cff5d2
ms.contentlocale: nl-nl
ms.lasthandoff: 05/17/2017


---
# <a name="communications-between-endpoints-in-system-center-configuration-manager"></a>De communicatie tussen de eindpunten in System Center Configuration Manager

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*


##  <a name="Planning_Intra-site_Com"></a> Communicatie tussen sitesystemen in een site  
 Als Configuration Manager site-systemen of -onderdelen over het netwerk naar andere sitesystemen of Configuration Manager-onderdelen in de site communiceren, gebruiken ze een van de volgende protocollen, afhankelijk van hoe u de site configureren:  

-   Server Message Block (SMB)  

-   HTTP  

-   HTTPS  

Met uitzondering van de communicatie van de siteserver naar een distributiepunt kan er op elk moment communicatie tussen servers in een site plaatsvinden. Hierbij wordt geen gebruikgemaakt van mechanismen om de netwerkbandbreedte te controleren. U kunt de communicatie tussen sitesystemen controleren, zorg ervoor dat u sitesysteemservers installeert op locaties die snel en goed verbonden netwerken.  

Voor de overdracht van inhoud van de siteserver naar distributiepunten:  

-   Configureer netwerkbandbreedtebeheer en -planning op het distributiepunt. Deze besturingselementen zijn vergelijkbaar met de configuraties die worden gebruikt door intersite-adressen en vaak kunt u deze configuratie gebruiken in plaats van een andere Configuration Manager-site installeren als de overdracht van inhoud naar externe netwerklocaties uw belangrijkste bandbreedte overweging is.  

-   U kunt een distributiepunt installeren als een voorbereid distributiepunt. Een voorbereid distributiepunt laat u inhoud gebruiken die handmatig op de distributiepuntserver wordt geplaatst en verwijdert de vereiste om inhoudsbestanden over het netwerk over te dragen.  

Zie voor meer informatie [beheer van netwerkbandbreedte voor inhoudsbeheer](manage-network-bandwidth.md).


##  <a name="Planning_Client_to_Site_System"></a> Communicatie van clients naar sitesystemen en services  
Clients starten communicatie met sitesysteemrollen, Active Directory Domain Services en onlineservices. Als u wilt dat deze communicatie wordt ingeschakeld, moeten firewalls het netwerkverkeer tussen clients en het eindpunt van de communicatie toestaan. Eindpunten zijn:  

-   **Application Catalog-websitepunt**: Biedt ondersteuning voor HTTP en HTTPS-communicatie

-   **Cloudresources**: Bevat de Microsoft Azure en Microsoft Intune  

-   **Configuration Manager beleidsmodule (NDES)**: Biedt ondersteuning voor HTTP en HTTPS-communicatie

-   **Distributiepunten**: Ondersteunt het HTTP en HTTPS-communicatie en HTTPS is vereist voor cloud-gebaseerde distributiepunten  

-   **Terugvalstatuspunt**: Biedt ondersteuning voor HTTP-communicatie  

-   **Beheerpunt**: Biedt ondersteuning voor HTTP en HTTPS-communicatie  

-   **Microsoft Update**  

-   **Software-updatepunten** : Biedt ondersteuning voor HTTP en HTTPS-communicatie  

-   **Statusmigratiepunt**: Biedt ondersteuning voor HTTP en HTTPS-communicatie  

-   **Verschillende domeinservices**  

Voordat een client met een sitesysteemrol wordt gehost communiceren kan, gebruikt de client servicelocatie vinden van een sitesysteemrol die het clientprotocol (HTTP of HTTPS) ondersteunt. Standaard gebruiken clients de meest beveiligde methode die voor hen beschikbaar is:  

-   U moet een PKI (Public Key Infrastructure) hebben en u moet PKI-certificaten installeren op clients en servers om HTTPS te gebruiken. Zie [PKI-certificaatvereisten voor System Center Configuration Manager](../../../core/plan-design/network/pki-certificate-requirements.md) voor informatie over het gebruik van certificaten.  

-   Wanneer u een sitesysteemrol implementeert die gebruikmaakt van Internet Information Services (IIS) en communicatie van clients ondersteunt, moet u opgeven of clients verbinding met het sitesysteem maken via HTTP of HTTPS. Als u HTTP gebruikt, dient u ook opties voor ondertekening en versleuteling te overwegen. Zie voor meer informatie [plannen voor ondertekening en versleuteling](../../../core/plan-design/security/plan-for-security.md#BKMK_PlanningForSigningEncryption) in [plannen van beveiliging in System Center Configuration Manager](../../../core/plan-design/security/plan-for-security.md).  

Zie [Begrijpen hoe clients siteresources en -services vinden voor System Center Configuration Manager](../../../core/plan-design/hierarchy/understand-how-clients-find-site-resources-and-services.md) voor informatie over servicelocatie door clients.  

Zie voor meer informatie over de poorten en protocollen die worden gebruikt door clients wanneer ze met eindpunten communiceren [poorten die worden gebruikt in System Center Configuration Manager](../../../core/plan-design/hierarchy/ports.md).  

###  <a name="BKMK_clientspan"></a> Overwegingen voor clientcommunicatie via internet of een niet-vertrouwd forest  
De volgende geïnstalleerde sitesysteemrollen op primaire sites ondersteunen verbindingen van clients die zich in niet-vertrouwde locaties, zoals het Internet of een niet-vertrouwd forest. (Secundaire sites ondersteunen geen clientverbindingen van niet-vertrouwde locaties):  

-   Application Catalog-websitepunt  

-   Configuration Manager-beleidsmodule  

-   Distributiepunt (HTTPS is vereist voor cloudgebaseerde distributiepunten)  

-   Proxypunt voor inschrijving  

-   Terugvalstatuspunt  

-   Beheerpunt  

-   Software-updatepunt  

**Over internetgerichte sitesystemen:**   
Er is een vertrouwensrelatie tussen de forest van de client en van de sitesysteemserver is niet vereist. Echter, als het forest met een internetgericht sitesysteem de forests vertrouwt die de gebruikersaccounts bevat, ondersteunt deze configuratie gebruikersbeleid voor apparaten op het Internet wanneer u de **clientbeleid** clientinstelling **Gebruikersbeleidsaanvragen van internetclients toestaan**.  

De volgende configuraties illustreren bijvoorbeeld wanneer clientbeheer via internet het gebruikersbeleid voor apparaten op internet ondersteunt:  

-   Het internet-gebaseerd beheerpunt bevindt zich in het perimeternetwerk waar een alleen-lezen domeincontroller bestaat om de gebruiker te verifiëren en een tussenkomende firewall Active Directory-pakketten toestaat.  

-   Het gebruikersaccount bevindt zich in Forest A (intranet) en het internet-gebaseerd beheerpunt bevindt zich in Forest B (perimeternetwerk). Forest B vertrouwt Forest A en een tussenkomende firewall staat verificatiepakketten toe.  

-   Het gebruikersaccount en het internet-gebaseerde beheerpunt bevinden zich in Forest A (intranet). Het beheerpunt is gepubliceerd op internet met behulp van een webproxyserver (zoals Forefront Threat Management Gateway).  

> [!NOTE]  
>  Als Kerberos-verificatie is mislukt, wordt vervolgens automatisch de NTLM-verificatie geprobeerd.  

Zoals het vorige voorbeeld toont, kunt u internet-gebaseerde sitesystemen op het intranet plaatsen wanneer ze op het internet worden gepubliceerd met behulp van een webproxyserver, zoals ISA Server en Forefront Threat Management Gateway. Deze sitesystemen kunnen worden geconfigureerd voor clientverbinding via Internet, of voor alleen clientverbindingen via Internet en intranet. Wanneer u een webproxyserver gebruikt, kunt u deze configureren voor Secure Sockets Layer (SSL) bridging naar SSL (veiliger) of SSL-tunneling als volgt:  

-   **SSL-bridging naar SSL:**   
    De aanbevolen configuratie wanneer u proxy-webservers gebruikt voor clientbeheer op internet is SSL-bridging naar SSL. Dit maakt gebruik van SSL-beëindiging met verificatie. Clientcomputers moeten worden geverifieerd door gebruik te maken van computerverificatie en verouderde clients voor mobiele apparaten worden geverifieerd via gebruikersverificatie. Mobiele apparaten die zijn ingeschreven door Configuration Manager bieden geen ondersteuning voor SSL-bridging.  

     Het voordeel van SSL-beëindiging aan de proxywebserver is dat pakketten van het internet onderhevig zijn aan inspectie voordat ze worden doorgestuurd naar het interne netwerk. De proxywebserver verifieert de verbinding van de client, beëindigt deze, en opent vervolgens een nieuwe geverifieerde verbinding naar de sitesystemen op internet. Wanneer Configuration Manager-clients een proxywebserver gebruikt, wordt de clientidentiteit (client-GUID) veilig opgenomen in de pakketlading zodat het beheerpunt de proxywebserver de client niet beschouwt. Bridging wordt niet ondersteund voor in Configuration Manager met HTTP naar HTTPS of van HTTPS naar HTTP.  

-   **Tunneling**:   
    Als uw proxywebserver de vereisten voor SSL-bridging niet kan ondersteunen, of u wilt configureren, Internet-ondersteuning voor mobiele apparaten die zijn ingeschreven door Configuration Manager, wordt SSL-tunneling ook ondersteund. Het is een minder veilige optie omdat de SSL-pakketten van het internet worden doorgestuurd naar de sitesystemen zonder SSL-beëindiging. Op die manier kunnen ze niet worden geïnspecteerd op schadelijke inhoud. Als u SSL-tunneling gebruikt, zijn er geen certificaatvereisten voor de proxywebserver.  

##  <a name="Plan_Com_X-Forest"></a> Communicatie tussen Active Directory-forests  
System Center Configuration Manager biedt ondersteuning voor sites en hiërarchieën die Active Directory-forests omvatten.  

Configuration Manager biedt ook ondersteuning voor domeincomputers die zich niet in hetzelfde Active Directory-forest als de siteserver en computers die zich in werkgroepen bevinden:  

-   **Voor het ondersteunen van Domeincomputers in een forest dat niet wordt vertrouwd door het forest de siteserver**, kunt u:  

    -   Sitesysteemrollen in het niet-vertrouwde forest installeren met de optie om sitegegevens naar het desbetreffende Active Directory-forest te publiceren.  

    -   Deze computers beheren als computers in werkgroepen.  

  Wanneer u sitesysteemservers installeert in een niet-vertrouwd Active Directory-forest, de client-naar-server-communicatie van clients in dat forest wordt in dat forest, en Configuration Manager de computer verifiëren kan via Kerberos. Wanneer u site-informatie naar het forest van de client publiceert, kunnen clients baat hebben bij het ophalen van site-informatie, zoals een lijst met beschikbare beheerpunten, vanuit hun Active Directory-forest in plaats van deze informatie te downloaden via hun toegewezen beheerpunt.  

  > [!NOTE]  
  >  Als u apparaten wilt beheren die zich op internet bevinden, kunt u op internet gebaseerde sitesysteemrollen installeren in uw perimeternetwerk wanneer de sitesysteemservers zich in een Active Directory-forest bevinden. Dit scenario vereist geen wederzijdse vertrouwensrelatie tussen het perimeternetwerk en het forest de siteserver.  

-   **Als u computers in een werkgroep wilt ondersteunen**, moet u het volgende doen:  

    -   Werkgroepcomputers handmatig goedkeuren wanneer ze HTTP-clientverbindingen met sitesysteemrollen gebruiken. Dit komt doordat de Configuration Manager deze computers niet kan verifiëren via Kerberos.  

    -   Werkgroepclients configureren voor het gebruik van het netwerktoegangsaccounts, zodat deze computers inhoud kunnen ophalen van distributiepunten.  

    -   Een alternatief mechanisme voor werkgroepclients verschaffen om beheerpunten te zoeken. U kunt publiceren in DNS, WINS gebruiken of u kunt een beheerpunt rechtstreeks toewijzen. Dit is omdat deze clients geen site-informatie uit Active Directory Domain Services kunnen ophalen.  

    Verwante resources in deze inhoudsbibliotheek:  

    -   [Conflicterende records voor Configuration Manager-Clients beheren](../../../core/clients/manage/manage-clients.md#BKMK_ConflictingRecords)  

    -   [Netwerktoegangsaccount](../../../core/plan-design/hierarchy/fundamental-concepts-for-content-management.md#accounts-used-for-content-management)  

    -   [Configuration Manager-Clients installeren op Computers in werkgroepen](../../../core/clients/deploy/deploy-clients-to-windows-computers.md#BKMK_ClientWorkgroup)  

###  <a name="bkmk_span"></a> Scenario’s voor ondersteuning van een site of hiërarchie die meerdere domeinen en forests omvat  

#### <a name="communication-between-sites-in-a-hierarchy-that-spans-forests"></a>Communicatie tussen sites in een hiërarchie die forests omvat  
In dit scenario moet een wederzijdse forestvertrouwensrelatie die ondersteuning biedt voor Kerberos-verificatie.  Als u een wederzijdse forestvertrouwensrelatie die ondersteuning biedt voor Kerberos-verificatie niet hebt, biedt klikt u vervolgens Configuration Manager geen ondersteuning een onderliggende site in de externe forest.  

 **Configuration Manager ondersteunt de installatie van een onderliggende site in een extern forest dat de vereiste tweerichtingsvertrouwensrelatie heeft met het forest van de bovenliggende site**  

-   U kunt bijvoorbeeld een secundaire site plaatsen in een ander forest van de bovenliggende primaire site, zolang de vereiste vertrouwensrelatie bestaat.  

> [!NOTE]  
>  Een onderliggende site kan worden primaire site (waarbij de centrale beheersite de bovenliggende site) of een secundaire site.  

Communicatie tussen sites in Configuration Manager maakt gebruik van databasereplicatie en overdrachten op basis van bestanden. Wanneer u een site installeert, moet u een account waarmee u de site te installeren op de aangewezen server opgeven. Dit account brengt ook communicatie tot stand tussen sites en onderhoudt de communicatie.  

Nadat de site de overdrachten op basis van bestanden en databasereplicatie heeft geïnstalleerd en geïnitieerd, zijn voor communicatie naar de site geen verdere configuraties vereist.  

**Wanneer een bidirectionele forestvertrouwensrelatie bestaat, is geen aanvullende configuratiestappen vereist in Configuration Manager.**  

Standaard als u een nieuwe site als onderliggende site van een andere site installeert Configuration Manager configureert u het volgende:  

-   Een intersite replicatieroute op basis van bestanden op elke site gebruikmaakt van het siteservercomputeraccount. Configuration Manager voegt het computeraccount van elke computer toe aan de **SMS_SiteToSiteConnection_&lt;sitecode\>**  groep op de doelcomputer.  

-   Databasereplicatie tussen de SQL Server op elke site.  

De volgende configuraties moeten ook worden ingesteld:  

-   Tussenkomende firewalls en netwerkapparaten moeten de netwerkpakketten die Configuration Manager vereist toestaan.  

-   Naamomzetting moet tussen de forests werken.  

-   Als u een site of sitesysteemrol wilt installeren, moet u een account opgeven die lokale beheerdersmachtigingen heeft op de opgegeven computer.  

#### <a name="communication-in-a-site-that-spans-forests"></a>Communicatie in een site die forests omvat  
Voor dit scenario is een tweerichtingsrelatie tussen forests niet vereist.  

**Primaire sites ondersteunen de installatie van sitesysteemrollen op computers in externe forests**.  

-   Het Application Catalog-webservicepunt is de enige uitzondering.  Het punt wordt alleen ondersteund in hetzelfde forest als de siteserver.  

-   Als een sitesysteemrol verbindingen aanvaardt van internet, installeer dan, als best practice voor beveiliging, de sitesysteemrollen in een locatie waarin de grens van het forest de siteserver beveiligt (bijvoorbeeld in een perimeternetwerk).  

**Een sitesysteemrol installeren op een computer in een niet-vertrouwd forest:**  

-   U dient een **Installatieaccount**, die wordt gebruikt voor het installeren van de sitesysteemrol. (Dit account moet lokale beheerdersreferenties verbinding maken met hebben). Installeer vervolgens sitesysteemrollen op de opgegeven computer.  

-   U moet de sitesysteemoptie **De siteserver moet verbinding met dit sitesysteem initiëren**selecteren. Hiervoor moet de siteserver verbindingen instellen met de sitesysteemserver om gegevens over te dragen. Dit voorkomt dat de computer in de niet-vertrouwde locatie contact maakt met de siteserver in uw vertrouwde netwerk. Voor deze verbindingen wordt het **Installatieaccount sitesysteem**gebruikt.  

**Als u een sitesysteemrol gebruikt in een niet-vertrouwd forest** , moeten firewalls het netwerkverkeer toestaan, zelfs wanneer de siteserver de overdracht van gegevens initieert.  

Bovendien moeten de volgende sitesysteemrollen directe toegang tot de sitedatabase hebben. Daarom moeten firewalls toepasselijk verkeer van de niet-vertrouwd forest SQL-Server van de site toestaan:  

-   Asset Intelligence-synchronisatiepunt  

-   Endpoint Protection-punt  

-   Inschrijvingspunt  

-   Beheerpunt  

-   Reporting Service-punt  

-   Statusmigratiepunt  

Zie voor meer informatie [poorten die worden gebruikt in System Center Configuration Manager](../../../core/plan-design/hierarchy/ports.md).  

**Mogelijk moet u de toegang van de sitesysteemrol tot de sitedatabase configureren:**  

Het beheerpunt en het inschrijvingspunt van de sitesysteemrollen maken verbinding met de sitedatabase.  

-   Standaard, wanneer deze sitesysteemrollen worden geïnstalleerd, Configuration Manager configureert het computeraccount van de systeemserver van de nieuwe site als het verbindingsaccount voor de sitesysteemrol en vervolgens het account toegevoegd aan de juiste rol voor SQL Server-database.  

-   Als u deze sitesysteemrollen op een niet-vertrouwd domein installeert, moet u het verbindingsaccount van de sitesysteemrol configureren om het de sitesysteemrol mogelijk te maken informatie in te winnen van de database.  

Als u een domeingebruikersaccount configureert als verbindingsaccount voor deze sitesysteemrollen, moet u ervoor zorgen dat de domeingebruiker de juiste toegang heeft tot de SQL Serve-database op die site:  

-   Beheerpunt: **Verbindingsaccount voor Beheerpuntdatabase**  

-   Inschrijvingspunt: **Verbindingsaccount voor inschrijvingspunt**  

Houd rekening met de volgende aanvullende informatie om sitesysteemrollen in andere forests te plannen:  

-   Als u Windows Firewall uitvoert, configureert u de toepasselijke firewallprofielen om door te geven van communicatie tussen de Sitedatabaseserver en computers die zijn geïnstalleerd met externe sitesysteemrollen. Zie voor meer informatie inzake firewallprofielen [firewallprofielen](http://go.microsoft.com/fwlink/p/?LinkId=233629).  

-   Als het beheerpunt op internet de forests vertrouwt die de gebruikersaccounts bevat, dan wordt het gebruikersbeleid ondersteund. Als er geen vertrouwensrelatie bestaat, wordt alleen computerbeleid ondersteund.  

#### <a name="communication-between-clients-and-site-system-roles-when-the-clients-are-not-in-the-same-active-directory-forest-as-their-site-server"></a>Communicatie tussen clients en sitesysteemrollen wanneer de clients zich niet in hetzelfde Active Directory-forest bevinden als hun siteserver.  
Configuration Manager ondersteunt de volgende scenario's voor clients die zich niet in hetzelfde forest als de siteserver:  

-   Er is een wederzijdse vertrouwensrelatie tussen de forest van de client en het forest van de siteserver.  

-   De server van de sitesysteemrol bevindt zich in hetzelfde forest als de client.  

-   De client zich op een domeincomputer heeft geen een wederzijdse forestvertrouwensrelatie vertrouwen met de siteserver en site-functies zijn niet geïnstalleerd in het forest van de client.  

-   De client zich op een werkgroepcomputer.  

Clients op een computer lid van een domein kunnen Active Directory Domain Services voor de servicelocatie gebruiken wanneer hun site gepubliceerd is naar hun Active Directory-forest.  

Als u site-informatie naar een ander Active Directory-forest wilt publiceren, moet u het volgende doen:  

-   Het forest opgeven en vervolgens publiceren naar dit forest inschakelen in het knooppunt **Active Directory-forests** van de werkruimte **Beheer** .  

-   Elke site configureren om de bijbehorende gegevens te publiceren naar Active Directory-domeinservices. Deze configuratie maakt het clients in deze forest mogelijk site-informatie op te halen en beheerpunten te vinden. Voor clients die Active Directory Domain Services voor de servicelocatie niet kunnen gebruiken, kunt u DNS, WINS of de client toegewezen beheerpunt.  

###  <a name="bkmk_xchange"></a> De Exchange Server-connector in een extern forest plaatsen  
Als u dit scenario wilt ondersteunen, moet u ervoor zorgen dat de naamomzetting tussen de forests werkt (configureer bijvoorbeeld DNS-forwards) en geeft u de intranet-FQDN voor Exchange Server op wanneer u de Exchange Server-connector configureert. Zie [Mobiele apparaten beheren met System Center Configuration Manager en Exchange](../../../mdm/deploy-use/manage-mobile-devices-with-exchange-activesync.md) voor meer informatie.  

