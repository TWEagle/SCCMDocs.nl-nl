---
title: Clients toewijzen aan een site | Microsoft Docs
description: Clients toewijzen aan een site in System Center Configuration Manager.
ms.custom: na
ms.date: 04/23/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: configmgr-client
ms.tgt_pltfrm: na
ms.topic: get-started-article
ms.assetid: ba9b623f-6e86-4006-93f2-83d563de0cd0
caps.latest.revision: "10"
author: arob98
ms.author: angrobe
manager: angrobe
ms.openlocfilehash: fbac58f3745839d974f9ec865fee313dda211d0a
ms.sourcegitcommit: b438515490e04fb09c82a8af642d38e9a0605178
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 09/15/2017
---
# <a name="how-to-assign-clients-to-a-site-in-system-center-configuration-manager"></a>Clients toewijzen aan een site in System Center Configuration Manager

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*

Nadat een System Center Configuration Manager-client is geïnstalleerd, deze moet worden toegevoegd aan een primaire site van Configuration Manager voordat u hem kunt beheren. De site die een client lid heet de *toegewezen site*. Clients kunnen niet worden toegewezen aan een centrale beheersite of aan een secundaire site.  

Het toewijzingsproces treedt op nadat de client is geïnstalleerd en bepaalt welke site de clientcomputer wordt beheert. U kunt ofwel rechtstreeks de client toewijzen aan een site of kunt u automatische sitetoewijzing geval zoekt de client automatisch een geschikte site op basis van de actuele netwerklocatie of een fallback-site die is geconfigureerd voor de hiërarchie.

Wanneer u de client voor mobiele apparaten tijdens de registratie van de Configuration Manager installeert, wordt het apparaat altijd automatisch toegewezen aan een site. Wanneer u de client op een computer installeert, kunt u kiezen of de client toewijzen aan een site of niet. De client blijft niet-beheerd totdat de sitetoewijzing is voltooid als de client is geïnstalleerd, maar niet toegewezen.  
 

> [!NOTE]  
>  Wijs clients altijd toe aan sites met dezelfde versie van Configuration Manager. Vermijd een Configuration Manager-client met een nieuwere versie toewijst aan een site met een oudere versie.   Indien nodig werkt u de primaire site naar dezelfde versie van Configuration Manager die u voor de clients gebruikt.  

Nadat de client aan een site is toegewezen, blijft deze toegewezen aan die site, zelfs als de client zijn IP-adres verandert en naar een andere site roamt. Alleen een beheerder kan handmatig de client toewijzen aan een andere site of de clienttoewijzing verwijderen.  

> [!WARNING]  
>  Een uitzondering op een client die blijft toegewezen aan een site, geldt voor als u de client op een Windows Embedded-apparaat toewijst als de schrijffilters zijn ingeschakeld. Als u schrijffilters niet eerst uitschakelt voordat u de client toewijst, keert de sitetoewijzingsstatus van de client terug naar de oorspronkelijke status wanneer het apparaat de volgende keer opnieuw wordt opgestart.  
>   
>  Als de client bijvoorbeeld geconfigureerd is voor automatische sitetoewijzing, wordt er tijdens het opstarten een nieuwe toewijzing uitgevoerd en is het mogelijk dat de client aan een andere site wordt toegewezen. Als de client is niet geconfigureerd voor automatische sitetoewijzing maar handmatige sitetoewijzing vereist, moet u handmatig opnieuw toewijzen de client na het opstarten voordat u deze client opnieuw beheren kunt met Configuration Manager.  
>   
>  U kunt dit gedrag vermijden door de schrijffilters uit te schakelen voordat u de client op ingesloten apparaten toewijst. Nadat u hebt geverifieerd dat de sitetoewijzing is geslaagd, schakelt u de schrijffilters opnieuw in.  

Als de clienttoewijzing is mislukt, wordt de clientsoftware blijft geïnstalleerd, maar wordt niet beheerd. Een client wordt als niet-beheerd beschouwd als deze geïnstalleerd is, maar niet is toegewezen aan een site, of als deze aan een site is toegewezen, maar niet kan communiceren met een beheerpunt.  

##  <a name="using-manual-site-assignment-for-computers"></a>Handmatige sitetoewijzing gebruiken voor computers  
 U kunt clientcomputers handmatig toewijzen aan een site aan de hand van de volgende twee methoden:  

-   Gebruik een clientinstallatie-eigenschap die de sitecode specificeert.  

-   Geef de sitecode op in het Configuratiescherm, in **Configuration Manager**.  

> [!NOTE]  
>  Als u een clientcomputer handmatig aan een Configuration Manager-sitecode die niet bestaat toewijst, wordt de sitetoewijzing mislukt.   

##  <a name="BKMK_AutomaticAssignment"></a> Automatische sitetoewijzing gebruiken voor computers  
 Automatische sitetoewijzing kan zich voordoen tijdens clientimplementatie of wanneer u klikt op **Site zoeken** in het tabblad **Geavanceerd** van de **Eigenschappen van Configuration Manager** in het Configuratiescherm. De Configuration Manager-client vergelijkt zijn eigen netwerklocatie met de grenzen die zijn geconfigureerd in de Configuration Manager-hiërarchie. Als de netwerklocatie van de client binnen een grensgroep valt die voor sitetoewijzing is ingeschakeld, of als de hiërarchie voor een terugvalsite is geconfigureerd, wordt de client automatisch toegewezen naar die site zonder dat u een sitecode moet opgeven.  

 U kunt grenzen configureren door een of meer van de volgende opties te gebruiken:  

-   IP-subnet  

-   Active Directory-site  

-   IPv6-voorvoegsel  

-   IP-adresbereik  

> [!NOTE]  
>  Als een Configuration Manager-client meerdere netwerkadapters heeft en daarom meerdere IP-adressen heeft, wordt het IP-adres gebruikt een client om sitetoewijzing te evalueren willekeurig toegewezen.  

 Zie [Sitegrenzen en grensgroepen definiëren voor System Center Configuration Manager](../../../core/servers/deploy/configure/define-site-boundaries-and-boundary-groups.md) voor informatie over het configureren van grensgroepen voor sitetoewijzing en het configureren van een terugvalsite voor automatische sitetoewijzing.  

 Configuration Manager-clients die automatische sitetoewijzing gebruiken proberen te vinden die zijn gepubliceerd naar Active Directory Domain Services. Als dit mislukt (bijvoorbeeld het Active Directory-schema is niet uitgebreid voor Configuration Manager of de clients werkgroepcomputers zijn), kunnen clients informatie over de grensgroep ophalen uit een beheerpunt.  

 U kunt een beheerpunt opgeven voor clientcomputers voor gebruik wanneer ze worden geïnstalleerd. Clients kunnen ook een beheerpunt zoeken door gebruik te maken van DNS-publishing of WINS.  

 Als de client geen site kan vinden die is gekoppeld met een grensgroep die de netwerklocatie ervan bevat en als de hiërarchie geen terugvalsite heeft, zal de client elke 10 minuten opnieuw zoeken totdat deze kan worden toegewezen aan een site.  

 Configuration Manager-clientcomputers kunnen niet automatisch worden toegewezen aan een site als een van de volgende van toepassing, en vervolgens zij moeten handmatig worden toegewezen:  

-   Ze zijn momenteel toegewezen aan een site.  

-   Ze zijn verbonden met het internet of geconfigureerd als clients met alleen internetverbinding.  

-   Hun netwerklocatie valt niet binnen één van de geconfigureerde grensgroepen in de Configuration Manager-hiërarchie en er is geen terugvalsite voor de hiërarchie.  

##  <a name="completing-site-assignment-by-checking-site-compatibility"></a>Sitetoewijzing voltooien door het controleren van de sitecompatibiliteit  
 Nadat een client zijn toegewezen site heeft gevonden, wordt de versie en het besturingssysteem van de client gecontroleerd om ervoor te zorgen dat een Configuration Manager-site kan beheren. Configuration Manager beheren niet bijvoorbeeld Configuration Manager 2007-clients, System Center 2012 Configuration Manager-clients of clients waarop Windows 2000.  

 Sitetoewijzing mislukt als u een client toewijst waar Windows 2000 wordt uitgevoerd met een Configuration Manager-site. Wanneer u een Configuration Manager 2007-client of een System Center 2012 Configuration Manager-client toewijst aan een site voor Configuration Manager (huidige vertakking), wel sitetoewijzing automatische Clientupgrade ondersteunen. Echter, totdat de oudere generatie clients worden bijgewerkt naar een client Configuration Manager (huidige vertakking), niet Configuration Manager deze client beheren door clientinstellingen, toepassingen of software-updates.  

> [!NOTE]  
>  U moet automatische Clientupgrade voor de hiërarchie configureren ter ondersteuning van de sitetoewijzing van een Configuration Manager 2007 of een System Center 2012 Configuration Manager-client aan een site voor Configuration Manager (huidige vertakking). Zie [How to upgrade clients for Windows computers in System Center Configuration Manager](../../../core/clients/manage/upgrade/upgrade-clients-for-windows-computers.md) (Clients voor Windows-computers bijwerken in System Center Configuration Manager) voor meer informatie.  

Configuration Manager controleert ook dat u de client Configuration Manager (huidige vertakking) hebt toegewezen aan een site die wordt ondersteund. De volgende scenario's kunnen optreden tijdens de migratie van eerdere versies van Configuration Manager.  

-   Scenario: U hebt Automatische sitetoewijzing gebruikt en uw grenzen overlappen met die zijn gedefinieerd in een eerdere versie van Configuration Manager.  

     In dit geval probeert de client automatisch een Configuration Manager (huidige vertakking)-site te vinden.  

     Controleert de client eerst Active Directory Domain Services en als er een Configuration Manager (huidige vertakking)-site die is gepubliceerd, sitetoewijzing is voltooid. Als dit mislukt (bijvoorbeeld de Configuration Manager site niet is gepubliceerd of de computer een werkgroep-client is), controleert de client vervolgens voor site-informatie van de bijbehorende toegewezen beheerpunt.  

    > [!NOTE]  
    >  U kunt een beheerpunt naar de client tijdens de clientinstallatie toewijzen met behulp van de Client.msi-eigenschap **SMSMP =&lt;servernaam >**.  

     De sitetoewijzing mislukt als deze twee methoden mislukken. In dat geval moet u de client handmatig toewijzen.  

-   Scenario: U hebt de Configuration Manager (huidige vertakking)-client toegewezen met behulp van een specifieke sitecode in plaats van automatische sitetoewijzing en per ongeluk een sitecode opgegeven voor een versie van Configuration Manager ouder is dan System Center 2012 R2 Configuration Manager.  

     In dit geval mislukt de sitetoewijzing en u moet de site voor Configuration Manager (huidige vertakking)-client handmatig opnieuw toewijzen.  

 Voor de controle van de sitecompatibiliteit gelden de volgende voorwaarden:  

-   De client heeft toegang tot site-informatie die naar Active Directory Domain Services is gepubliceerd.  

-   De client kan communiceren met een beheerpunt in de site.  

 Als de controle van de sitecompatibiliteit niet met succes voltooid, wordt de sitetoewijzing mislukt en de client blijft niet-beheerd totdat de controle van de sitecompatibiliteit opnieuw uitgevoerd en is geslaagd.  

 De uitzondering op het uitvoeren van de controle van de sitecompatibiliteit doet zich voor wanneer een client voor een beheerpunt op internet is geconfigureerd. In dit geval wordt er geen controle van de sitecompatibiliteit uitgevoerd. Als u clients toewijst aan een site die sitesystemen op internet bevat en u geeft een beheerpunt op internet op, zorg er dan voor dat u de client aan de juiste site toewijst. Als u deze per ongeluk aan een Configuration Manager 2007-site, een System Center 2012 Configuration Manager-site toewijst, of aan een Configuration Manager-site die geen sitesysteemrollen op basis van het Internet, is de client worden niet-beheerd.  

##  <a name="locating-management-points"></a>Zoeken naar beheerpunten  
 Nadat een client is toegewezen aan een site, zoekt deze een beheerpunt in de site.  

 Clientcomputers downloaden een lijst met beheerpunten die ze verbinding in de site maken kunnen. Dat gebeurt telkens als de client opnieuw is opgestart, of elke 25 uur, of als de client een netwerkwijziging detecteert, bijvoorbeeld als de computer de verbinding verbreekt en opnieuw verbinding maken met het netwerk of het een nieuw IP-adres ontvangt. De lijst omvat beheerpunten op het intranet en of ze clientverbindingen via HTTP of HTTPS accepteren. De clientcomputer verbindt met het opgegeven beheerpunt op internet om een lijst met beheerpunten te downloaden als de clientcomputer is verbonden met het internet en de client nog geen lijst met beheerpunten heeft. Als de client een lijst beheerpunten heeft voor de toegewezen site, wordt er één geselecteerd om verbinding mee te maken:  

-   De client geeft de voorkeur aan HTTPS-beheerpunten boven HTTP-beheerpunten als de client is verbonden met het intranet en een geldig PKI-certificaat heeft dat het kan gebruiken. Vervolgens zoekt de client het dichtstbijzijnde beheerpunt op basis van het forest-lidmaatschap.  

-   Wanneer de client zich op Internet, kiest het willekeurig een van de Internet-gebaseerd beheerpunt punten.  

Mobiel apparaat-clients die zijn ingeschreven door Configuration Manager alleen verbinding maken met één beheerpunt in hun toegewezen site en nooit verbinding maken met beheerpunten in secundaire sites. Deze clients verbinden altijd via HTTPS en het beheerpunt moet worden geconfigureerd om clientverbindingen via het internet te accepteren. Wanneer er meer dan één beheerpunt voor clients van mobiele apparaten in de primaire site, kiest Configuration Manager willekeurig een van deze beheerpunten tijdens het toewijzingsproces de mobiele apparaatclient blijft hetzelfde beheerpunt gebruiken.  

De client is een beheerde client als deze clientbeleid heeft gedownload van een beheerpunt in de site.  

##  <a name="downloading-site-settings"></a>Site-instellingen downloaden  
 Nadat de sitetoewijzing is voltooid en de client een beheerpunt heeft gevonden, downloadt een clientcomputer die Active Directory Domain Services voor de controle van de sitecompatibiliteit gebruikt, clientgerelateerde site-instellingen voor de toegewezen site. Deze instellingen omvatten de selectiecriteria van het clientcertificaat, of er een certificaatintrekkingslijst wordt gebruikt, en de door de client aangevraagde poortnummers. De client blijft deze instellingen periodiek controleren.  

 Als clientcomputers geen site-instellingen kunnen verkrijgen van Active Directory Domain Services, downloaden ze deze van hun beheerpunt. Clientcomputers kunnen de site-instellingen ook verkrijgen wanneer ze met clientpush worden geïnstalleerd, of u handmatig opgeven kunt met behulp van CCMSetup.exe en de clientinstallatie-eigenschappen. Zie [Over de eigenschappen van clientinstallatie in System Center Configuration Manager](../../../core/clients/deploy/about-client-installation-properties.md) voor meer informatie over de eigenschappen van een clientinstallatie.  

##  <a name="downloading-client-settings"></a>Clientinstellingen downloaden  
 Alle clients downloaden het standaard clientinstellingenbeleid en elk ander aangepast clientinstellingenbeleid dat van toepassing is. Software Center is afhankelijk van dit clientconfiguratiebeleid voor Windows-computers en gebruikers zullen een melding ontvangen dat Software Center niet kan worden uitgevoerd totdat deze configuratie-informatie is gedownload. Afhankelijk van de geconfigureerde clientinstellingen kan het initiële downloaden van de clientinstellingen enige tijd duren. Sommige clientbeheertaken kunnen mogelijk niet worden uitgevoerd totdat dit proces is voltooid.  

##  <a name="verifying-site-assignment"></a>Sitetoewijzing controleren  
 U kunt site-toewijzing geslaagd verifiëren door een van de volgende methoden:  

-   Voor clients op Windows-computers, Configuration Manager gebruiken in het Configuratiescherm en controleer of dat de sitecode juist wordt weergegeven op de **Site** tabblad.  

-   Voor clientcomputers in de **activa en naleving** werkruimte > **apparaten** knooppunt, Controleer of de computer bevat **Ja** voor de **Client** kolom en de juiste primaire site code van de **sitecode** kolom.  

-   Voor mobiele apparaatclients kunt u in de werkruimte **Activa en naleving** via de verzameling **Alle mobiele apparaten** controleren of voor het mobiele apparaat **Ja** in de kolom **Client** wordt weergegeven en of de juiste code van de primaire site wordt weergegeven in de kolom **Sitecode** .  

-   Gebruik de rapporten voor de clienttoewijzing en de inschrijving van mobiele apparaten.  

-   Voor clientcomputers gebruikt u het bestand LocationServices.log op de client.  

##  <a name="roaming-to-other-sites"></a>Roaming naar andere sites  
 Wanneer clientcomputers op het intranet aan een primaire site worden toegewezen maar binnen een grensgroep vallen die voor een andere site is geconfigureerd vanwege een gewijzigde netwerklocatie, hebben deze naar een andere site gezworven. Wanneer deze site een secundaire site is van de hun toegewezen site, kunnen clients met behulp van een beheerpunt in de secundaire site clientbeleid downloaden en clientgegevens uploaden, waardoor wordt voorkomen dat deze gegevens via een mogelijk traag netwerk worden verzonden. Als deze clients echter tot binnen de grenzen zwerven van een andere primaire site of een secundaire site die geen onderliggende site is van de aan hen toegewezen site, gebruiken deze clients altijd een beheerpunt in de aan hen toegewezen site om clientbeleid te downloaden en gegevens naar hun site te uploaden.  

 Deze naar andere sites (alle primaire en secundaire sites) zwervende clientcomputers kunnen altijd gebruik maken van beheerpunten in andere sites voor verzoeken om de locatie van inhoud. Beheerpunten in de actuele site kunnen clients een lijst met distributiepunten geven die over de inhoud beschikken waarom clients verzoeken.  

 Voor clientcomputers die zijn geconfigureerd voor clientbeheer alleen op Internet en voor mobiele apparaten en Mac-computers die zijn ingeschreven door Configuration Manager, worden deze clients alleen communiceren met beheerpunten in hun toegewezen site. Deze clients communiceren nooit met beheerpunten in secundaire sites of andere primaire sites.  
