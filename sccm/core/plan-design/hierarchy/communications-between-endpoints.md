---
title: De communicatie tussen de eindpunten
titleSuffix: Configuration Manager
description: Meer informatie over hoe System Center Configuration Manager-sitesystemen en -onderdelen via een netwerk communiceren.
ms.custom: na
ms.date: 10/06/2016
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 68fe0e7e-351e-4222-853a-877475adb589
caps.latest.revision: "10"
author: aczechowski
ms.author: aaroncz
manager: angrobe
ms.openlocfilehash: 1ad0c5855ce9855801eda66d78f7f60829f26fbf
ms.sourcegitcommit: ca9d15dfb1c9eb47ee27ea9b5b39c9f8cdcc0748
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 01/04/2018
---
# <a name="communications-between-endpoints-in-system-center-configuration-manager"></a>De communicatie tussen de eindpunten in System Center Configuration Manager

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*


##  <a name="Planning_Intra-site_Com"></a> Communicatie tussen sitesystemen in een site  
 Wanneer de Configuration Manager-sitesystemen of -onderdelen over het netwerk naar andere sitesystemen of Configuration Manager-onderdelen in de site communiceren, gebruiken ze een van de volgende protocollen, afhankelijk van hoe u de site configureert:  

-   Server Message Block (SMB)  

-   HTTP  

-   HTTPS  

Met uitzondering van de communicatie van de siteserver naar een distributiepunt kan er op elk moment communicatie tussen servers in een site plaatsvinden. Hierbij wordt geen gebruikgemaakt van mechanismen om de netwerkbandbreedte te controleren. U kunt de communicatie tussen sitesystemen controleren, zorg ervoor dat u sitesysteemservers installeert op locaties die snel en goed verbonden netwerken.  

Voor de overdracht van inhoud van de siteserver naar distributiepunten:  

-   Configureer netwerkbandbreedtebeheer en -planning op het distributiepunt. Deze besturingselementen zijn vergelijkbaar met de configuraties die worden gebruikt door intersite-adressen en vaak kunt u deze configuratie gebruiken in plaats van een andere Configuration Manager-site installeren wanneer de overdracht van inhoud naar externe netwerklocaties uw belangrijkste overweging inzake bandbreedte is.  

-   U kunt een distributiepunt installeren als een voorbereid distributiepunt. Een voorbereid distributiepunt laat u inhoud gebruiken die handmatig op de distributiepuntserver wordt geplaatst en verwijdert de vereiste om inhoudsbestanden over het netwerk over te dragen.  

Zie voor meer informatie [netwerkbandbreedte voor inhoudsbeheer beheren](manage-network-bandwidth.md).


##  <a name="Planning_Client_to_Site_System"></a> Communicatie van clients naar sitesystemen en services  
Clients starten communicatie met sitesysteemrollen, Active Directory Domain Services en onlineservices. Voor het inschakelen van deze communicatie moet in de firewalls het netwerkverkeer tussen clients en het eindpunt van de communicatie worden toegestaan. Eindpunten zijn:  

-   **Application Catalog-websitepunt**: Ondersteunt HTTP en HTTPS-communicatie

-   **Cloudresources**: Bevat de Microsoft Azure en Microsoft Intune  

-   **Configuration Manager-beleidsmodule (NDES)**: Ondersteunt HTTP en HTTPS-communicatie

-   **Distributiepunten**: Ondersteunt HTTP en HTTPS-communicatie en HTTPS is vereist voor cloud-gebaseerde distributiepunten  

-   **Terugvalstatuspunt**: Biedt ondersteuning voor HTTP-communicatie  

-   **Beheerpunt**: Ondersteunt HTTP en HTTPS-communicatie  

-   **Microsoft Update**  

-   **Software-updatepunten** : Ondersteunt HTTP en HTTPS-communicatie  

-   **Statusmigratiepunt**: Ondersteunt HTTP en HTTPS-communicatie  

-   **Verschillende domeinservices**  

Voordat een client met een sitesysteemrol communiceren kan, gebruikt de client servicelocatie vinden van een sitesysteemrol die het clientprotocol (HTTP of HTTPS) ondersteunt. Standaard gebruiken clients de meest beveiligde methode die voor hen beschikbaar is:  

-   U moet een PKI (Public Key Infrastructure) hebben en u moet PKI-certificaten installeren op clients en servers om HTTPS te gebruiken. Zie [PKI-certificaatvereisten voor System Center Configuration Manager](../../../core/plan-design/network/pki-certificate-requirements.md) voor informatie over het gebruik van certificaten.  

-   Wanneer u een sitesysteemrol implementeert die gebruikmaakt van Internet Information Services (IIS) en communicatie van clients ondersteunt, moet u opgeven of clients verbinding met het sitesysteem maken via HTTP of HTTPS. Als u HTTP gebruikt, dient u ook opties voor ondertekening en versleuteling te overwegen. Zie voor meer informatie [Planning voor ondertekening en versleuteling](../../../core/plan-design/security/plan-for-security.md#BKMK_PlanningForSigningEncryption) in [beveiliging in System Center Configuration Manager plannen](../../../core/plan-design/security/plan-for-security.md).  

Zie [Begrijpen hoe clients siteresources en -services vinden voor System Center Configuration Manager](../../../core/plan-design/hierarchy/understand-how-clients-find-site-resources-and-services.md) voor informatie over servicelocatie door clients.  

Zie voor meer informatie over de poorten en protocollen die door clients wordt gebruikt wanneer ze met eindpunten communiceren [poorten die worden gebruikt in System Center Configuration Manager](../../../core/plan-design/hierarchy/ports.md).  

###  <a name="BKMK_clientspan"></a> Overwegingen voor clientcommunicatie via internet of een niet-vertrouwd forest  
De volgende geïnstalleerde sitesysteemrollen op primaire sites ondersteunen verbindingen van clients die zich in niet-vertrouwde locaties, zoals Internet of een niet-vertrouwd forest. (Secundaire sites ondersteunen geen clientverbindingen van niet-vertrouwde locaties):  

-   Application Catalog-websitepunt  

-   Configuration Manager-beleidsmodule  

-   Distributiepunt (HTTPS is vereist voor cloudgebaseerde distributiepunten)  

-   Proxypunt voor inschrijving  

-   Terugvalstatuspunt  

-   Beheerpunt  

-   Sitesysteemrollen toevoegen  

**Over internetgerichte sitesystemen:**   
Er is geen vereiste om een vertrouwensrelatie tussen de forest van de client en die van de sitesysteemserver. Als de forest met een internetgericht sitesysteem het forest waarin de gebruikersaccounts vertrouwt, deze configuratie ondersteunt echter gebruikersbeleid voor apparaten op Internet wanneer u inschakelt de **clientbeleid** clientinstelling **Gebruikersbeleidsaanvragen van internetclients toestaan**.  

De volgende configuraties illustreren bijvoorbeeld wanneer clientbeheer via internet het gebruikersbeleid voor apparaten op internet ondersteunt:  

-   Het internet-gebaseerd beheerpunt bevindt zich in het perimeternetwerk waar een alleen-lezen domeincontroller bestaat om de gebruiker te verifiëren en een tussenkomende firewall Active Directory-pakketten toestaat.  

-   Het gebruikersaccount bevindt zich in Forest A (intranet) en het internet-gebaseerd beheerpunt bevindt zich in Forest B (perimeternetwerk). Forest B vertrouwt Forest A en een tussenkomende firewall staat verificatiepakketten toe.  

-   Het gebruikersaccount en het internet-gebaseerde beheerpunt bevinden zich in Forest A (intranet). Het beheerpunt is gepubliceerd op internet met behulp van een webproxyserver (zoals Forefront Threat Management Gateway).  

> [!NOTE]  
>  Als Kerberos-verificatie is mislukt, wordt vervolgens automatisch de NTLM-verificatie geprobeerd.  

Zoals het vorige voorbeeld toont, kunt u internet-gebaseerde sitesystemen op het intranet plaatsen wanneer ze op het internet worden gepubliceerd met behulp van een webproxyserver, zoals ISA Server en Forefront Threat Management Gateway. Deze sitesystemen kunnen worden geconfigureerd voor clientverbinding van het Internet, of voor alleen clientverbindingen van Internet en intranet. Wanneer u een webproxyserver gebruikt, kunt u deze configureren voor Secure Sockets Layer (SSL) bridging naar SSL (veiliger) of SSL-tunneling als volgt:  

-   **SSL-bridging naar SSL:**   
    De aanbevolen configuratie wanneer u proxy-webservers gebruikt voor clientbeheer op internet is SSL-bridging naar SSL. Dit maakt gebruik van SSL-beëindiging met verificatie. Clientcomputers moeten worden geverifieerd door gebruik te maken van computerverificatie en verouderde clients voor mobiele apparaten worden geverifieerd via gebruikersverificatie. Mobiele apparaten die zijn ingeschreven door Configuration Manager bieden geen ondersteuning voor SSL-bridging.  

     Het voordeel van SSL-beëindiging aan de proxywebserver is dat pakketten van het internet onderhevig zijn aan inspectie voordat ze worden doorgestuurd naar het interne netwerk. De proxywebserver verifieert de verbinding van de client, beëindigt deze, en opent vervolgens een nieuwe geverifieerde verbinding naar de sitesystemen op internet. Wanneer Configuration Manager-clients een proxywebserver gebruikt, wordt de clientidentiteit (client-GUID) veilig opgenomen in de pakketlading zodat het beheerpunt de proxywebserver de client niet beschouwt. Bridging wordt niet ondersteund voor in Configuration Manager met HTTP naar HTTPS of van HTTPS naar HTTP.  

-   **Tunneling**:   
    Als uw proxywebserver de vereisten voor SSL-bridging niet kan ondersteunen, of u wilt configureren, Internet-ondersteuning voor mobiele apparaten die zijn ingeschreven door Configuration Manager, wordt SSL-tunneling ook ondersteund. Het is een minder veilige optie omdat de SSL-pakketten van het internet worden doorgestuurd naar de sitesystemen zonder SSL-beëindiging. Op die manier kunnen ze niet worden geïnspecteerd op schadelijke inhoud. Als u SSL-tunneling gebruikt, zijn er geen certificaatvereisten voor de proxywebserver.  

##  <a name="Plan_Com_X-Forest"></a> Communicatie tussen Active Directory-forests  
System Center Configuration Manager biedt ondersteuning voor sites en hiërarchieën die Active Directory-forests omvatten.  

Configuration Manager biedt ook ondersteuning voor domeincomputers die zich niet in hetzelfde Active Directory-forest als de siteserver en computers die zich in werkgroepen bevinden:  

-   **Ter ondersteuning van computers in het domein in een forest dat niet wordt vertrouwd door het forest van uw siteserver**, kunt u:  

    -   Sitesysteemrollen in het niet-vertrouwde forest installeren met de optie om sitegegevens naar het desbetreffende Active Directory-forest te publiceren.  

    -   Deze computers beheren alsof het werkgroepcomputers betreft.  

  Wanneer u sitesysteemservers installeert in een niet-vertrouwd Active Directory-forest, de client-naar-server-communicatie van clients in dat forest blijft aanwezig in dat forest en Configuration Manager de computer verifiëren kan via Kerberos. Wanneer u site-informatie naar het forest van de client publiceert, kunnen clients baat hebben bij het ophalen van site-informatie, zoals een lijst met beschikbare beheerpunten, vanuit hun Active Directory-forest in plaats van deze informatie te downloaden via hun toegewezen beheerpunt.  

  > [!NOTE]  
  >  Als u apparaten wilt beheren die zich op internet bevinden, kunt u op internet gebaseerde sitesysteemrollen installeren in uw perimeternetwerk wanneer de sitesysteemservers zich in een Active Directory-forest bevinden. Dit scenario vereist geen wederzijdse vertrouwensrelatie tussen het perimeternetwerk en het forest van de siteserver.  

-   **Als u computers in een werkgroep wilt ondersteunen**, moet u het volgende doen:  

    -   Werkgroepcomputers handmatig goedkeuren wanneer ze HTTP-clientverbindingen met sitesysteemrollen gebruiken. Dit is omdat Configuration Manager deze computers niet kan verifiëren via Kerberos.  

    -   Werkgroepclients configureren voor het gebruik van het netwerktoegangsaccounts, zodat deze computers inhoud kunnen ophalen van distributiepunten.  

    -   Een alternatief mechanisme voor werkgroepclients verschaffen om beheerpunten te zoeken. U kunt publiceren in DNS, WINS gebruiken of u kunt een beheerpunt rechtstreeks toewijzen. Dit is omdat deze clients geen site-informatie uit Active Directory Domain Services kunnen ophalen.  

    Verwante resources in deze inhoudsbibliotheek:  

    -   [Conflicterende records voor Configuration Manager-Clients beheren](../../../core/clients/manage/manage-clients.md#BKMK_ConflictingRecords)  

    -   [Netwerktoegangsaccount](../../../core/plan-design/hierarchy/fundamental-concepts-for-content-management.md#accounts-used-for-content-management)  

    -   [Het installeren van Configuration Manager-Clients op Computers in werkgroepen](../../../core/clients/deploy/deploy-clients-to-windows-computers.md#BKMK_ClientWorkgroup)  

###  <a name="bkmk_span"></a> Scenario’s voor ondersteuning van een site of hiërarchie die meerdere domeinen en forests omvat  

#### <a name="communication-between-sites-in-a-hierarchy-that-spans-forests"></a>Communicatie tussen sites in een hiërarchie die forests omvat  
Dit scenario is een wederzijdse forestvertrouwensrelatie, die ondersteuning biedt voor Kerberos-verificatie vereist.  Als er geen wederzijdse forestvertrouwensrelatie, die ondersteuning biedt voor Kerberos-verificatie, biedt vervolgens Configuration Manager geen ondersteuning voor een onderliggende site in het externe forest.  

 **Configuration Manager ondersteunt de installatie van een onderliggende site in een extern forest dat de vereiste tweerichtingsrelatie met het forest van de bovenliggende site**  

-   U kunt bijvoorbeeld een secundaire site in een ander forest van de primaire bovenliggende site plaatsen, zolang de vereiste vertrouwensrelatie bestaat.  

> [!NOTE]  
>  Een onderliggende site is de primaire site (waarbij de centrale beheersite de bovenliggende site is) of een secundaire site.  

Intersitecommunicatie in Configuration Manager maakt gebruik van databasereplicatie en overdrachten op basis van bestanden. Wanneer u een site installeert, moet u een account waarmee u de site op de aangewezen server opgeven. Dit account brengt ook communicatie tot stand tussen sites en onderhoudt de communicatie.  

Nadat de site de overdrachten op basis van bestanden en databasereplicatie heeft geïnstalleerd en geïnitieerd, zijn voor communicatie naar de site geen verdere configuraties vereist.  

**Als er een wederzijdse forestvertrouwensrelatie bestaat, maakt Configuration Manager vereist geen aanvullende configuratiestappen.**  

Standaard, wanneer u een nieuwe site als een onderliggend element van een andere site installeert, Configuration Manager configureert u het volgende:  

-   Een intersite replicatieroute op basis van bestanden op elke site gebruikmaakt van het siteservercomputeraccount. Configuration Manager voegt de computeraccount van elke computer toe aan de **SMS_SiteToSiteConnection_&lt;sitecode\>**  groep op de doelcomputer.  

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

-   Geef een **Installatieaccount**, dat wordt gebruikt voor het installeren van de sitesysteemrol. (Dit account moet lokale beheerdersreferenties verbinding maken met hebben). Installeer vervolgens sitesysteemrollen op de opgegeven computer.  

-   U moet de sitesysteemoptie **De siteserver moet verbinding met dit sitesysteem initiëren**selecteren. Hiervoor moet de siteserver verbindingen instellen met de sitesysteemserver om gegevens over te dragen. Dit voorkomt dat de computer in de niet-vertrouwde locatie verbinding maakt met de siteserver die in uw vertrouwde netwerk. Voor deze verbindingen wordt het **Installatieaccount sitesysteem**gebruikt.  

**Als u een sitesysteemrol gebruikt in een niet-vertrouwd forest** , moeten firewalls het netwerkverkeer toestaan, zelfs wanneer de siteserver de overdracht van gegevens initieert.  

Bovendien moeten de volgende sitesysteemrollen directe toegang tot de sitedatabase hebben. Daarom moeten firewalls toepasselijk verkeer van de niet-vertrouwd forest naar de siteserver SQL toestaan:  

-   Asset Intelligence-synchronisatiepunt  

-   Endpoint Protection-punt  

-   Inschrijvingspunt  

-   Beheerpunt  

-   Reporting Service-punt  

-   Statusmigratiepunt  

Zie voor meer informatie [poorten die worden gebruikt in System Center Configuration Manager](../../../core/plan-design/hierarchy/ports.md).  

**Mogelijk moet u de toegang van de sitesysteemrol tot de sitedatabase configureren:**  

Het beheerpunt en het inschrijvingspunt van de sitesysteemrollen maken verbinding met de sitedatabase.  

-   Standaard, als deze sitesysteemrollen worden geïnstalleerd, Configuration Manager configureert u het computeraccount van de nieuwe sitesysteemserver als het verbindingsaccount voor de sitesysteemrol en voegt u het account vervolgens toe aan de geschikte SQL Server-databaserol.  

-   Als u deze sitesysteemrollen op een niet-vertrouwd domein installeert, moet u het verbindingsaccount van de sitesysteemrol configureren om het de sitesysteemrol mogelijk te maken informatie in te winnen van de database.  

Als u een domeingebruikersaccount configureert als verbindingsaccount voor deze sitesysteemrollen, moet u ervoor zorgen dat de domeingebruiker de juiste toegang heeft tot de SQL Serve-database op die site:  

-   Beheerpunt: **Verbindingsaccount voor Beheerpuntdatabase**  

-   Inschrijvingspunt: **Verbindingsaccount voor inschrijvingspunt**  

Houd rekening met de volgende aanvullende informatie om sitesysteemrollen in andere forests te plannen:  

-   Als u Windows Firewall uitvoert, configureert u de toepasselijke firewallprofielen om uitwisselt tussen de Sitedatabaseserver en computers die zijn geïnstalleerd met externe sitesysteemrollen. Zie voor meer informatie inzake firewallprofielen [firewallprofielen](http://go.microsoft.com/fwlink/p/?LinkId=233629).  

-   Als het beheerpunt op internet de forests vertrouwt die de gebruikersaccounts bevat, dan wordt het gebruikersbeleid ondersteund. Als er geen vertrouwensrelatie bestaat, wordt alleen computerbeleid ondersteund.  

#### <a name="communication-between-clients-and-site-system-roles-when-the-clients-are-not-in-the-same-active-directory-forest-as-their-site-server"></a>Communicatie tussen clients en sitesysteemrollen wanneer de clients zich niet in hetzelfde Active Directory-forest bevinden als hun siteserver.  
Configuration Manager ondersteunt de volgende scenario's voor clients die zich niet in hetzelfde forest als hun siteserver:  

-   Er is een wederzijdse vertrouwensrelatie tussen de forest van de client en het forest van de siteserver.  

-   De server van de sitesysteemrol bevindt zich in hetzelfde forest als de client.  

-   De client is een domeincomputer geen een tweerichtingsrelatie tussen forests vertrouwen met de siteserver en heeft-site sitesysteemrollen zijn niet geïnstalleerd in het forest van de client.  

-   De client zich op een werkgroepcomputer is geworden.  

Clients op een computer lid van een domein kunnen Active Directory Domain Services voor de servicelocatie gebruiken wanneer hun site gepubliceerd is naar hun Active Directory-forest.  

Als u site-informatie naar een ander Active Directory-forest wilt publiceren, moet u het volgende doen:  

-   Het forest opgeven en vervolgens publiceren naar dit forest inschakelen in het knooppunt **Active Directory-forests** van de werkruimte **Beheer** .  

-   Elke site configureren om de bijbehorende gegevens te publiceren naar Active Directory-domeinservices. Deze configuratie maakt het clients in deze forest mogelijk site-informatie op te halen en beheerpunten te vinden. Voor clients die Active Directory Domain Services voor de servicelocatie van de niet gebruiken, kunt u DNS, WINS of de client toegewezen beheerpunt.  

###  <a name="bkmk_xchange"></a> De Exchange Server-connector in een extern forest plaatsen  
Als u dit scenario wilt ondersteunen, moet u ervoor zorgen dat de naamomzetting tussen de forests werkt (configureer bijvoorbeeld DNS-forwards) en geeft u de intranet-FQDN voor Exchange Server op wanneer u de Exchange Server-connector configureert. Zie [Mobiele apparaten beheren met System Center Configuration Manager en Exchange](../../../mdm/deploy-use/manage-mobile-devices-with-exchange-activesync.md) voor meer informatie.  
