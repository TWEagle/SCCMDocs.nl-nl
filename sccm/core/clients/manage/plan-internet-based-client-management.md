---
title: Internet-gebaseerd clientbeheer | Microsoft Docs
description: Maak een plan voor het beheren van clients op Internet in System Center Configuration Manager.
ms.custom: na
ms.date: 05/16/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: configmgr-client
ms.tgt_pltfrm: na
ms.topic: get-started-article
ms.assetid: 83a7c934-3b11-435d-ba22-cbc274951e83
caps.latest.revision: "7"
caps.handback.revision: "0"
author: arob98
ms.author: angrobe
manager: angrobe
ms.openlocfilehash: be250e9056d1fad0e01a4ef4c8072d4c0faee692
ms.sourcegitcommit: f6a428a8db7145affa388f59e0ad880bdfcf17b5
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 09/14/2017
---
# <a name="plan-for-internet-based-client-management-in-system-center-configuration-manager"></a>Plan voor Internet-gebaseerd clientbeheer in System Center Configuration Manager

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*

Clientbeheer via Internet management (ook wel aangeduid als IBCM) kunt die u beheren met System Center Configuration Manager-clients wanneer ze niet zijn verbonden met uw bedrijf maar u beschikt over een standaardinternetverbinding. Deze regeling heeft verschillende voordelen, met inbegrip van verlaagde kosten want virtuele particuliere netwerken (VPN's) moeten niet worden uitgevoerd en software-updates kunnen tijdig worden geïmplementeerd.  

 Wegens de hogere beveiligingsvereisten voor het beheren van clientcomputers op een openbaar netwerk, is voor clientbeheer via internet het gebruik van PKI-certificaten vereist voor clients en sitesysteemservers waarmee de clients zijn verbonden. Dit zorgt dat de verbindingen worden geverifieerd door een onafhankelijke instantie en dat de gegevens naar en van deze sitesystemen zijn versleuteld met Secure Sockets Layer (SSL).  

 Gebruik de volgende secties voor het plannen van clientbeheer via internet.  

##  <a name="features-that-are-not-supported-on-the-internet"></a>Functies die niet worden ondersteund op het internet  
 Niet alle clientbeheerfunctionaliteiten zijn geschikt voor het internet; daarom worden ze niet ondersteund wanneer clients op het internet worden beheerd. De functies die niet worden ondersteund voor internetbeheer vertrouwen doorgaans op Active Directory domeinservices of zijn niet geschikt voor een openbaar netwerk, zoals netwerkdetectie en Wake-on-LAN (WOL).  

 Onderstaande functies worden niet ondersteund wanneer clients op het internet worden beheerd:  

-   Clientimplementatie via internet, zoals clientpush en clientimplementatie gebaseerd op software-update. Gebruik in plaats daarvan handmatige clientinstallatie.  

-   Automatische sitetoewijzing.  

-   Wake-on-LAN.  

-   Implementatie van besturingssysteem. U kunt niettemin takenreeksen implementeren die geen besturingssysteem implementeren, bijvoorbeeld takenreeksen die scripts en onderhoudstaken op clients uitvoeren.  

-   Extern beheer.  

-   Software-implementatie op gebruikers tenzij het beheerpunt op internet de gebruiker kan verifiëren in Active Directory Domain Services met behulp van Windows-verificatie (Kerberos of NTLM). Dit is mogelijk wanneer het beheerpunt op internet de forest vertrouwt waar het gebruikersaccount is opgeslagen.  

 Clientbeheer via internet biedt bovendien geen ondersteuning voor roaming. Roaming maakt het clients mogelijk altijd de dichtstbijzijnde distributiepunten te vinden om inhoud te downloaden. Clients die worden beheerd via internet communiceren met sitesystemen van hun toegewezen site wanneer deze sitesystemen zijn geconfigureerd om internet-FQDN te gebruiken en de sitesysteemrollen de clientverbindingen op het internet toestaan. Clients selecteren op niet-deterministische wijze een van de sitesystemen op internet, ongeacht de bandbreedte of fysieke locatie.  

 Als u een softwareupdate-punt hebt dat is geconfigureerd om verbindingen vanuit het internet te accepteren, zullen Configuration Manager-clients op internet altijd scannen ten opzichte van dit updatepunt om te bepalen welke software-updates vereist zijn. Als deze clients niettemin met het internet zijn verbonden, proberen ze eerst de software-updates te downloaden van Microsoft Update, in plaats van vanaf een internet-gebaseerd distributiepunt. Alleen als dit mislukt, wordt geprobeerd om de vereiste software-updates te downloaden vanaf een op internet gebaseerd distributiepunt. Clients die niet zijn geconfigureerd voor clientbeheer via Internet trachten nooit de software-updates downloaden vanaf Microsoft Update, maar gebruiken altijd Configuration Manager-distributiepunten.  

##  <a name="considerations-for-client-communications-from-the-internet-or-untrusted-forest"></a>Overwegingen voor clientcommunicatie via internet of een niet-vertrouwd forest  
 De volgende geïnstalleerde sitesysteemrollen op primaire sites ondersteunen verbindingen van clients in niet-vertrouwde locaties, zoals internet of een niet-vertrouwd forest (secundaire sites ondersteunen geen clientverbindingen van niet-vertrouwde locaties):  

-   Application Catalog-websitepunt  

-   Configuration Manager-beleidsmodule  

-   Distributiepunt (HTTPS is vereist voor cloudgebaseerde distributiepunten)  

-   Proxypunt voor inschrijving  

-   Terugvalstatuspunt  

-   Beheerpunt  

-   Software-updatepunt  

 **Over internetgerichte sitesystemen:**   
Hoewel er geen vereiste is om een vertrouwensrelatie tussen de forest van de client en die van de sitesysteemserver als het forest met een Internetgericht sitesysteem het forest waarin de gebruikersaccounts vertrouwt, ondersteunt deze configuratie gebruikersbeleid voor apparaten op Internet wanneer u inschakelt de **clientbeleid** clientinstelling **Gebruikersbeleidsaanvragen van internetclients toestaan**.  

 De volgende configuraties illustreren bijvoorbeeld wanneer clientbeheer via internet het gebruikersbeleid voor apparaten op internet ondersteunt:  

-   Het internet-gebaseerd beheerpunt bevindt zich in het perimeternetwerk waar een alleen-lezen domeincontroller bestaat om de gebruiker te verifiëren en een tussenkomende firewall Active Directory-pakketten toestaat.  

-   Het gebruikersaccount bevindt zich in Forest A (intranet) en het internet-gebaseerd beheerpunt bevindt zich in Forest B (perimeternetwerk). Forest B vertrouwt Forest A en een tussenkomende firewall staat verificatiepakketten toe.  

-   Het gebruikersaccount en het internet-gebaseerde beheerpunt bevinden zich in Forest A (intranet). Het beheerpunt is gepubliceerd op internet met behulp van een webproxyserver (zoals Forefront Threat Management Gateway).  

> [!NOTE]  
>  Als Kerberos-verificatie is mislukt, wordt vervolgens automatisch de NTLM-verificatie geprobeerd.  

 Zoals het vorige voorbeeld toont, kunt u internet-gebaseerde sitesystemen op het intranet plaatsen wanneer ze op het internet worden gepubliceerd met behulp van een webproxyserver, zoals ISA Server en Forefront Threat Management Gateway. Deze sitesystemen kunnen worden geconfigureerd voor clientverbinding van enkel internet of clientverbindingen van internet en intranet. Als u een webproxyserver gebruikt, dan kunt u deze configureren voor Secure Sockets Layer (SSL) bridging naar SSL (veiliger) of SSL-tunneling:  

-   **SSL-bridging naar SSL:**   
    De aanbevolen configuratie wanneer u proxy-webservers gebruikt voor clientbeheer op internet is SSL-bridging naar SSL. Dit maakt gebruik van SSL-beëindiging met verificatie. Clientcomputers moeten worden geverifieerd door gebruik te maken van computerverificatie en verouderde clients voor mobiele apparaten worden geverifieerd via gebruikersverificatie. Mobiele apparaten die zijn ingeschreven door Configuration Manager bieden geen ondersteuning voor SSL-bridging.  

     Het voordeel van SSL-beëindiging aan de proxywebserver is dat pakketten van het internet onderhevig zijn aan inspectie voordat ze worden doorgestuurd naar het interne netwerk. De proxywebserver verifieert de verbinding van de client, beëindigt deze, en opent vervolgens een nieuwe geverifieerde verbinding naar de sitesystemen op internet. Wanneer Configuration Manager-clients een proxywebserver gebruikt, wordt de clientidentiteit (client-GUID) veilig opgenomen in de pakketlading zodat het beheerpunt de proxywebserver de client niet beschouwt. Bridging wordt niet ondersteund voor in Configuration Manager met HTTP naar HTTPS of van HTTPS naar HTTP.  

-   **Tunneling**:   
    Als uw proxywebserver de vereisten voor SSL-bridging niet kan ondersteunen, of u wilt configureren, Internet-ondersteuning voor mobiele apparaten die zijn ingeschreven door Configuration Manager, wordt SSL-tunneling ook ondersteund. Het is een minder veilige optie omdat de SSL-pakketten van het internet worden doorgestuurd naar de sitesystemen zonder SSL-beëindiging. Op die manier kunnen ze niet worden geïnspecteerd op schadelijke inhoud. Als u SSL-tunneling gebruikt, zijn er geen certificaatvereisten voor de proxywebserver.  

##  <a name="planning-for-internet-based-clients"></a>Planning voor clients op internet  
 U moet beslissen of de clientcomputers die via het internet zullen worden beheerd, geconfigureerd zullen zijn voor beheer op het intranet en het internet, of alleen voor clientbeheer op internet. U kunt de clientbeheeroptie alleen configureren tijdens de installatie van een clientcomputer. Als u later van gedachten verandert, moet u de client opnieuw installeren.  

> [!NOTE]  
>  Als u een beheerpunt met internetmogelijkheden configureert, worden clients die verbinding met het beheerpunt maken geschikt voor internet wanneer ze vervolgens hun lijst met beschikbare beheerpunten vernieuwen.  

> [!TIP]  
>  U hoeft de configuratie van clientbeheer alleen via het internet niet beperken tot het internet en u kunt deze ook op het intranet gebruiken.  

 Clients die worden geconfigureerd voor clientbeheer alleen op internet communiceren alleen met de sitesystemen die zijn geconfigureerd voor clientverbindingen van het internet. Deze configuratie is geschikt voor computers waarvan u weet dat ze nooit verbinding maken met het bedrijfsintranet, zoals point of sale-computers in externe locaties. Het ook mogelijk geschikt wanneer u wilt beperken tot clientcommunicatie HTTPS alleen (bijvoorbeeld ondersteuning firewall en beperkt beveiligingsbeleid), en wanneer u sitesystemen op Internet installeert in een perimeternetwerk en u wilt dat deze servers beheren met Configuration Manager-client.  

 Als u werkgroepclients op het internet wilt beheren, moet u deze installeren als alleen met internetverbinding.  

> [!NOTE]  
>  Clients van mobiele apparaten worden automatisch geconfigureerd als alleen met internetverbinding wanneer ze zijn geconfigureerd om een beheerpunt op internet te gebruiken.  

 Andere clientcomputers kunnen worden geconfigureerd voor clientbeheer op internet en intranet. Ze kunnen automatisch schakelen tussen clientbeheer op internet en clientbeheer op intranet wanneer ze een netwerkwijziging detecteren. Als deze clients kunnen vinden en verbinden om een beheerpunt dat is geconfigureerd voor clientverbindingen op het intranet, worden deze clients beheerd als intranetclients met volledige beheerfunctionaliteit van Configuration Manager. Als de clients geen beheerpunt kunnen vinden of er geen verbinding mee maken als het beheerpunt voor clientverbindingen op het intranet is geconfigureerd, proberen ze te verbinden met een beheerpunt op internet. Als dit lukt, worden deze clients vervolgens beheerd door de sitesystemen op internet in hun toegewezen site.  

 Het voordeel van automatisch overschakelen tussen clientbeheer op Internet en clientbeheer op intranet, is dat clientcomputers automatisch alle Configuration Manager-functies gebruiken kunnen wanneer ze zijn verbonden met het intranet en beheerd betreft essentiële beheerfuncties blijven wanneer ze op het Internet. Bovendien kan een download die begon op het internet probleemloos verder worden gedownload op het intranet, en vice versa.  

##  <a name="prerequisites-for-internet-based-client-management"></a>Vereisten voor clientbeheer op internet  
 Internet-gebaseerd clientbeheer in Configuration Manager heeft de volgende externe afhankelijkheden:  

-   Clients die zullen worden beheerd op het internet, moeten een internetverbinding hebben.  

     Configuration Manager gebruikt bestaande Internetproviderverbindingen (ISP)-verbindingen met het Internet; dit kunnen zowel permanente als tijdelijke verbindingen. Mobiele apparaten van clients moeten een rechtstreekse internetverbinding hebben, maar clientcomputers kunnen een rechtstreekse internetverbinding hebben of verbinden via een proxywebserver.  

-   Sitesystemen die clientbeheer op internet ondersteunen moeten verbonden zijn met het internet en moeten zich in een Active Directory-domein bevinden.  

     De sitesystemen op internet hebben geen vertrouwensrelatie nodig met het Active Directory-forest van de siteserver. Gebruikersbeleid wordt echter ondersteund wanneer het beheerpunt op internet de gebruiker kan verifiëren met behulp van Windows-verificatie. Als Windows-verificatie is mislukt, wordt alleen computerbeleid ondersteund.  

    > [!NOTE]  
    >  U moet, om gebruikersbeleid te ondersteunen, de twee clientinstellingen van **Clientbeleid** ook instellingen op **True**:  
    >   
    >  -   **Polling voor gebruikersbeleid inschakelen op clients**  
    > -   **Gebruikersbeleidsaanvragen van internetclients inschakelen**  

     Een Application Catalog-websitepunt op internet vereist ook Windows-verificatie om gebruikers te verifiëren wanneer hun computer is verbonden met het internet. Deze vereiste is onafhankelijk van het gebruikersbeleid.  

-   U moet een ondersteunende PKI (Public Key Infrastructure) hebben dat de implementatie en het beheer kan uitvoeren van certificaten die de clients nodig hebben en die worden beheerd op het internet en op de sitesysteemservers op internet.  

     Zie [PKI-certificaatvereisten voor System Center Configuration Manager](/sccm/core/plan-design/network/pki-certificate-requirements) voor meer informatie over de PKI-certificaten.  

-   Het internet-FQDN van sitesystemen die clientbeheer op internet ondersteunen, moeten als hostvermeldingen op openbare DNS-servers zijn geregistreerd.  

-   Tussenkomende firewalls of proxyservers moeten clientcommunicatie toestaan die wordt geassocieerd met sitesystemen op internet.  

     Vereisten voor clientcommunicatie:  

    -   Ondersteuning voor HTTP 1.1  

    -   Sta HTTP-inhoudstype van meerdelige MIME-bijlage toe (meerdelig/gemengd en toepassing/octet-stream)  

    -   Sta de volgende bewerkingen toe voor het beheerpunt op internet:  

        -   HEAD  

        -   CCM_POST  

        -   BITS_POST  

        -   GET  

        -   PROPFIND  

    -   Sta de volgende bewerkingen toe voor het distributiepunt op internet:  

        -   HEAD  

        -   GET  

        -   PROPFIND  

    -   Sta de volgende bewerkingen toe voor het terugvalstatuspunt op internet:  

        -   POST  

    -   Sta de volgende bewerkingen toe voor het Application Catalog-websitepunt op internet:  

        -   POST  

        -   GET  

    -   Sta de volgende HTTP-headers toe voor het beheerpunt op internet:  

        -   Bereik:  

        -   CCMClientID:  

        -   CCMClientIDSignature:  

        -   CCMClientTimestamp:  

        -   CCMClientTimestampsSignature:  

    -   Sta de volgende HTTP-header toe voor het distributiepunt op internet:  

        -   Bereik:  

     Raadpleeg de documentatie van uw firewall of proxyserver voor configuratie-informatie om deze vereisten te ondersteunen.  

     Zie de documentatie voor Windows Server Update Services (WSUS) voor vergelijkbare communicatievereisten wanneer u het software-updatepunt voor clientverbindingen van het internet gebruikt. Bijvoorbeeld: voor WSUS op Windows Server 2003, Zie [Appendix D: Beveiligingsinstellingen](http://go.microsoft.com/fwlink/p/?LinkId=143368), de implementatie-bijlage voor beveiligingsinstellingen.
