---
title: Site administration beveiliging en privacy
titleSuffix: Configuration Manager
description: Beveiliging en privacy voor sitebeheer in System Center Configuration Manager optimaliseren.
ms.custom: na
ms.date: 3/1/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 1d58176e-abc0-4087-8583-ce70deb4dcf5
caps.latest.revision: "8"
author: aczechowski
ms.author: aaroncz
manager: angrobe
ms.openlocfilehash: 2dd77a607e2ab87d9abf0ea46ca7c5565a8286b6
ms.sourcegitcommit: ca9d15dfb1c9eb47ee27ea9b5b39c9f8cdcc0748
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 01/04/2018
---
# <a name="security-and-privacy-for-site-administration-in-system-center-configuration-manager"></a>Beveiliging en privacy voor sitebeheer in System Center Configuration Manager

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*

Dit onderwerp bevat beveiligings- en privacy-informatie voor System Center Configuration Manager-sites en de hiërarchie.

##  <a name="BKMK_Security_Sites"></a>Aanbevolen beveiligingsprocedures voor sitebeheer  
 Gebruik de volgende aanbevolen beveiligingsprocedures om u te helpen beveiligen System Center Configuration Manager-sites en de hiërarchie.  

 **Installatieprogramma enkel uitvoeren vanuit een vertrouwde bron en Beveilig het communicatiekanaal tussen de setup-media en de siteserver.**  

 Om te voorkomen dat iemand knoeien met de bronbestanden bevat, moet u setup uitvoeren vanaf een vertrouwde bron. Slaat u bestanden op het netwerk op, dan beveiligt u de netwerklocatie.  

 Als u setup vanaf een netwerklocatie uitvoert, om te helpen te voorkomen dat kwaadwillende personen knoeien met de bestanden als ze worden verzonden via het netwerk, gebruikt u IPsec of Server Message Block (SMB) ondertekening tussen de bronlocatie van de setup-bestanden en de siteserver.  

 Bovendien, als u het Downloadprogramma voor het downloaden van de bestanden die voor installatie vereist zijn gebruikt, zorg dat u ook de locatie waar deze bestanden worden opgeslagen en Beveilig het communicatiekanaal voor deze locatie wanneer u setup uitvoert, beveiligt.  

 **Active Directory-schema uitbreiden voor System Center Configuration Manager en publiceer sites naar Active Directory Domain Services.**  

 Schema-uitbreidingen niet vereist zijn voor het uitvoeren van System Center Configuration Manager, maar ze een veiligere omgeving maken omdat Configuration Manager-clients en siteservers informatie van een vertrouwde bron ophalen kunnen.  

 Als clients zich in een niet-vertrouwd domein, moet u de volgende sitesysteemrollen in de clients domeinen implementeren:  

-   Beheerpunt  

-   Distributiepunt  

-   Application Catalog-websitepunt  

> [!NOTE]  
>  Een vertrouwd domein voor Configuration Manager vereist Kerberos-verificatie. Dit betekent dat als clients zich in een andere dat forest geen wederzijdse forestvertrouwensrelatie met de forest de siteserver, deze clients worden beschouwd als in niet-vertrouwd domein. Een externe vertrouwensrelatie is niet voldoende voor dit doel.  

 **Gebruik IPsec om communicaties tussen sitesysteemservers en sites te beveiligen.**  

 Hoewel Configuration Manager communicatie tussen de siteserver en de computer die SQL Server uitvoert beveiligt, wordt in Configuration Manager-communicatie tussen sitesysteemrollen en SQL Server niet beveiligen. Slechts enkele sitesystemen (het inschrijvingspunt en het Application Catalog-webservicepunt)  kunnen worden geconfigureerd voor HTTPS voor intrasitecommunicatie.  

 Gebruikt u geen bijkomende controles om deze server-to-server-kanalen te beveiligen, dan kunnen kwaadwillende personen verschillende adresvervalsingen (spoofing) en man-in-the-middle-aanvallen gebruiken tegen sitesystemen. Gebruik de SMB-ondertekening wanneer u IPsec niet kunt gebruiken.  

> [!NOTE]  
>  Het is van groot belang het communicatiekanaal tussen de siteserver en de bronserver te beveiligen. Deze communicatie maakt gebruik van SMB. Kunt u IPsec niet gebruiken om deze communicatie te beveiligen, dan gebruikt u SMB-ondertekening om te zorgen dat niet aan de bestanden wordt geknoeid voordat clients ze downloaden en uitvoeren.  

 **De beveiligingsgroepen die Configuration Manager maken en beheren voor sitesysteemcommunicatie niet wijzigen.**  

 Beveiligingsgroepen:  

-   **SMS_SiteSystemToSiteServerConnection_MP_&lt;SiteCode\>**  

-   **SMS_SiteSystemToSiteServerConnection_SMSProv_&lt;SiteCode\>**  

-   **SMS_SiteSystemToSiteServerConnection_Stat_&lt;SiteCode\>**  

Configuration Manager maakt en beheert deze beveiligingsgroepen automatisch. Dit omvat het verwijderen van computeraccounts wanneer een sitesysteemrol wordt verwijderd.  

Bewerk deze groepen niet handmatig om te zorgen voor de continuïteit van de service en de minimaal benodigde bevoegdheden.  

**Als clients kunnen geen query op de GC-server voor Configuration Manager-informatie uitvoeren, beheert u de vertrouwde basissleutel inrichtingsproces.**  

Als clients niet kunnen de globale catalogus voor gegevens van Configuration Manager, moeten ze vertrouwen op de vertrouwde basissleutel om geldige beheerpunten te verifiëren. De vertrouwde basissleutel is opgeslagen in het clientregister en kan worden ingesteld door groepsbeleid of handmatige configuratie te gebruiken.  

Heeft de client geen kopie van de vertrouwde basissleutel voordat een beheerpunt voor het eerst wordt gecontacteerd, dan wordt het eerste beheerpunt vertrouwd waarmee wordt gecommuniceerd. U kunt de clients vooraf inrichten door gebruik te maken van de vertrouwde basissleutel om het risico te verkleinen dat een aanvaller clients naar een niet-geautoriseerd beheerpunt omleidt. Zie voor meer informatie [Planning voor de vertrouwde basissleutel](../../../core/plan-design/security/plan-for-security.md#BKMK_PlanningForRTK).  

**Niet-standaardpoortnummers gebruiken.**  

Met behulp van niet-standaardpoortnummers kan bijkomende beveiliging bieden omdat ze het moeilijker voor aanvallers om te verkennen van de omgeving in voorbereiding voor een aanval. Als u besluit niet-standaardpoorten te gebruiken, ze te plannen voordat u Configuration Manager installeren en gebruik ze consequent doorheen alle sites in de hiërarchie. Client aangevraagde poorten en Wake On LAN zijn voorbeelden van het gebruik van niet-standaardpoortnummers.  

**Functiescheiding op sitesystemen gebruiken.**  

Hoewel u alle sitesysteemrollen op één enkele computer kunt installeren, wordt deze praktijk zelden gebruikt op productienetwerken aangezien één enkel storingspunt wordt gemaakt.  

**Verminder de kwetsbaarheid.**  

Elke sitesysteemrol op een andere server isoleren verkleint de kans dat een aanval tegen kwetsbaarheden op één sitesysteem kan worden gebruikt voor een andere site-systeem. Vele sitesysteemrollen vereisen de installatie van Internet Information Services (IIS) op het sitesysteem en dit verhoogt de kwetsbaarheid voor aanvallen. Moet u de sitesysteemrollen combineren om uitgaven aan hardware te beperken, combineer IIS-sitesysteemrollen enkel met andere sitesysteemrollen die IIS vereisen.  

> [!IMPORTANT]  
>  De rol van het fallbackstatuspunt is een uitzondering. Omdat deze sitesysteemrol niet-geverifieerde gegevens van clients accepteert, wordt u aangeraden dat u de rol van terugvalstatuspunt ooit niet aan een andere Configuration Manager sitesysteemrol toewijzen.  


**Volg de aanbevolen beveiligingsprocedures voor Windows Server en voer de Security Configuration Wizard op alle sitesystemen uit.**  

De Security Configuration Wizard (SCW) helpt u om een beveiligingsbeleid te maken dat u kunt toepassen op elke server van uw netwerk. Nadat u de System Center Configuration Manager-sjabloon hebt geïnstalleerd, herkent SCW Configuration Manager-sitesysteemrollen, services, poorten en toepassingen. Dan is de communicatie mogelijk die is vereist voor Configuration Manager en is geen vereiste communicatie geblokkeerd.  

De Wizard Beveiliging configureren is inbegrepen in de werkset voor System Center 2012 Configuration Manager, die u via het Microsoft Download Center downloaden kunt: [System Center 2012 – Configuration Manager-onderdeel-invoegtoepassingen en uitbreidingen voor](http://go.microsoft.com/fwlink/p/?LinkId=251931).  

**Statische IP-adressen voor sitesystemen configureren.**  

Statische IP-adressen zijn gemakkelijker te beschermen tegen aanvallen met naamomzetting.  

Statische IP-adressen maken ook de configuratie van IPsec gemakkelijker. Met behulp van IPsec is een aanbevolen beveiligingsprocedure voor het beveiligen van communicatie tussen sitesystemen in Configuration Manager.  

**Installeer geen andere toepassingen op sitesysteemservers.**  

Als u andere toepassingen op sitesysteemservers installeert, verhoogt u de kwetsbaarheid voor Configuration Manager en risico incompatibiliteitsproblemen.  

**Ondertekening vereisen en versleuteling inschakelen als een optie van de site.**  

Schakel de ondertekenings- en versleutelingsopties voor de site in. Zorg ervoor dat alle clients kunnen de hash-algoritme SHA-256 ondersteunen en schakel dan de optie **Vereis SHA-256**.  

**Beperken en gebruikers met beheerdersrechten Configuration Manager controleren en op rollen gebaseerd beheer gebruiken deze gebruikers de minimale om machtigingen te verlenen die ze nodig hebben.**  

Verleen beheerderstoegang tot Configuration Manager alleen voor gebruikers die u vertrouwt en hen minimale machtigingen Verleen met behulp van de ingebouwde beveiligingsrollen of door de beveiligingsrollen aanpassen. Gebruikers met beheerdersrechten die kunnen maken, wijzigen en implementeren van toepassingen, takenreeks, software-updates, configuratie-items en configuratiebasislijnen, kunnen mogelijk apparaten controleren in de Configuration Manager-hiërarchie.  

Controleer regelmatig de toewijzingen van gebruikers met beheerdersrechten en hun autorisatieniveau om de vereiste wijzigingen te verifiëren.  

Zie [Beheer op basis van rollen configureren voor System Center Configuration Manager](../../../core/servers/deploy/configure/configure-role-based-administration.md) voor meer informatie over het configureren van op rollen gebaseerd beheer.  

**Beveiligen van Configuration Manager back-ups en Beveilig het communicatiekanaal wanneer u een back-up en herstellen.**  

Wanneer u een back-up van Configuration Manager, omvat deze informatie certificaten en overige gevoelige gegevens die door een aanvaller kunnen worden aangewend voor imitatie.  

Gebruik SMB-ondertekening of IPsec wanneer u gegevens via het netwerk overdraagt en beveilig de locatie van back-up.  

**Wanneer u objecten exporteert of van de Configuration Manager-console naar een netwerklocatie importeert, Beveilig de locatie en Beveilig het netwerkkanaal.**  

Beperk wie toegang heeft tot de netwerkmap.  

Gebruik SMB-ondertekening of IPsec tussen de netwerklocatie en de siteserver en tussen de computer waarop de Configuration Manager-console en site server uitvoert, om te voorkomen dat een kwaadwillende persoon knoeit met de geëxporteerde gegevens. Gebruik IPsec om de gegevens op het netwerk te versleutelen om openbaarmaking van informatie te voorkomen.  

**Als een sitesysteem is niet correct verwijderd of niet meer werkt en kan niet worden hersteld, moet u handmatig de Configuration Manager-certificaten voor deze server verwijderen van andere Configuration Manager-servers.**  

Om de PeerTrust die aanvankelijk was ingesteld met het sitesysteem en sitesysteemrollen verwijderen, verwijdert u handmatig de Configuration Manager-certificaten voor de server in de **vertrouwde personen** certificaatarchief op andere sitesysteemservers. Dit is in het bijzonder belangrijk als u het doel van de server wijzigt maar hem niet opnieuw opmaakt.  

Zie de sectie voor meer informatie over deze certificaten **cryptografische besturingselementen voor servercommunicatie** in [cryptografische besturingselementen technische documentatie voor System Center Configuration Manager](../../../protect/deploy-use/cryptographic-controls-technical-reference.md).  

**Configureer geen sitesystemen op internet om het perimeternetwerk en het intranet te overbruggen.**  

Configureer geen sitesysteemservers worden multihomed zodat ze verbinding met het perimeternetwerk en het intranet maken. Hoewel deze configuratie het de sitesystemen op internet toestaat om clientverbindingen via internet en intranet te aanvaarden, wordt hierdoor een beveiligingsgrens tussen het perimeternetwerk en het intranet verwijderd.  

**Als de sitesysteemserver zich op een niet-vertrouwd netwerk bevindt (zoals een perimeternetwerk), configureert u de siteserver om verbindingen naar het sitesysteem te starten.**  

Standaard starten sitesystemen de verbindingen naar de siteserver om gegevens over te dragen; dit kan een veiligheidsrisico inhouden wanneer de initialisatie van de verbinding loopt van een niet-vertrouwd naar het vertrouwde netwerk. Wanneer sitesystemen verbindingen aanvaarden van het internet of zich bevinden in een niet-vertrouwd forest, configureert u de sitesysteemoptie **De siteserver moet verbindingen met dit sitesysteem initiëren** zodat na de installatie van het sitesysteem en sitesysteemrollen, alle verbindingen geïnitieerd worden vanuit het vertrouwde netwerk.  

**Als u een webproxyserver gebruikt voor clientbeheer via het internet, gebruikt u SSL-bridging naar SSL, door beëindiging met verificatie aan te wenden.**  

 Als u SSL-beëindiging aan de proxywebserver configureert, zijn pakketten van het internet onderhevig aan inspectie voordat ze worden doorgestuurd naar het interne netwerk. De proxywebserver verifieert de verbinding van de client, beëindigt deze, en opent vervolgens een nieuwe geverifieerde verbinding naar de sitesystemen op internet.  

 Wanneer Configuration Manager-clientcomputers een proxywebserver gebruikt verbinding maken met sitesystemen op Internet, wordt de clientidentiteit (client-GUID) veilig opgenomen in de pakketlading zodat het beheerpunt de proxywebserver de client niet beschouwt. Als uw proxywebserver de vereisten voor SSL-bridging niet kan ondersteunen, wordt ook SSL-tunneling ondersteund. Dit is een minder veilige optie omdat de SSL-pakketten van het internet worden doorgestuurd naar de sitesystemen zonder beëindiging. Op die manier kunnen ze niet worden geïnspecteerd op schadelijke inhoud.  

 Als uw proxywebserver de vereisten voor SSL-bridging niet kan ondersteunen, kunt u SSL-tunneling gebruiken. Dit is echter een minder veilige optie omdat de SSL-pakketten van het internet worden doorgestuurd naar de sitesystemen zonder beëindiging. Op die manier kunnen ze niet worden geïnspecteerd op schadelijke inhoud.  

> [!WARNING]  
>  Mobiele apparaten die zijn ingeschreven door Configuration Manager moeten kunnen SSL-bridging niet gebruiken en enkel SSL-tunneling.  

**Te gebruiken configuraties als u de site configureert om computers te activeren om software te installeren:**  

-   Als u traditionele ontwaakpakketten gebruikt, gebruikt u unicast in plaats van subnet gerichte broadcasts.  

-   Als u subnet gerichte broadcasts gebruiken moet, configureert u routers zodat IP gerichte broadcasts alleen vanaf de siteserver en alleen op een niet-standaard poortnummer.  

Zie voor meer informatie over de verschillende Wake On LAN-technologieën [plannen voor ontwaken van clients in System Center Configuration Manager](../../../core/clients/deploy/plan/plan-wake-up-clients.md).

**Configureer geverifieerde toegang naar de SMTP-mailserver als u e-mailmeldingen gebruikt.**  

Indien mogelijk gebruik van een e-mailserver die toegang ondersteunt geverifieerde en gebruik het computeraccount van de siteserver voor verificatie. Gebruik het account met de minste bevoegdheden als u een gebruikersaccount moet opgeven voor verificatie.  

##  <a name="BKMK_Security_SiteServer"></a>Aanbevolen beveiligingsprocedures voor de siteserver  
 Gebruik de volgende aanbevolen beveiligingsprocedures om te beschermen met de Configuration Manager-siteserver.  

 **Configuration Manager installeren op een lidserver in plaats van een domeincontroller.**  

 De Configuration Manager site server en sitesystemen hoeven niet installeren op een domeincontroller. Domeincontrollers hebben geen lokale SAM-database (Security Accounts Management) naast de domeindatabase. Wanneer u Configuration Manager op een lidserver installeert, kunt u Configuration Manager-accounts in de lokale SAM-database in plaats van de domeindatabase onderhouden.  

 Deze procedure verlaagt ook de kwetsbaarheid op uw domeincontrollers.  

 **Installeer secundaire sites door te vermijden om de bestanden te kopiëren naar de secundaire siteserver over het netwerk.**  

 Wanneer u setup uitvoert en maakt een secundaire site, selecteer de optie voor het kopiëren van de bestanden van de bovenliggende site naar de secundaire site niet en gebruik een netwerkbronlocatie niet. Wanneer u bestanden over het netwerk kopieert, zou een ervaren aanvaller het installatiepakket van de secundaire site kunnen overnemen en knoeien met de bestanden voordat ze worden geïnstalleerd. Het plannen van een dergelijke aanval is echter moeilijk. Deze aanval kan worden voorkomen door IPsec of SMB te gebruiken voor de bestandsoverdracht.  

 In plaats van het kopiëren van bestanden via het netwerk, klikt u op de secundaire siteserver de bronbestanden van media-map te kopiëren naar een lokale map. Wanneer u vervolgens setup uitvoert om te maken van een secundaire site op het **installatiebronbestanden** pagina **gebruik van de bronbestanden op de volgende locatie op de secundaire sitecomputer (veiligst)**, en geef deze map.  

 Zie voor meer informatie [Een secundaire site installeren](../../../core/servers/deploy/install/use-the-setup-wizard-to-install-sites.md#bkmk_secondary) in het onderwerp [De installatiewizard gebruiken om sites te installeren](../../../core/servers/deploy/install/use-the-setup-wizard-to-install-sites.md).  

##  <a name="BKMK_Security_SQLServer"></a>Aanbevolen beveiligingsprocedures voor SQL Server  
 Configuration Manager gebruikt SQL Server als de back-enddatabase. Als de database is aangetast, kunnen aanvallers overslaan van de Configuration Manager en toegang tot SQL Server om aanvallen via Configuration Manager rechtstreeks te. Houd rekening met aanvallen tegen de SQL-Server voor een zeer hoog risico en op de juiste wijze te verhelpen.  

 Gebruik de volgende aanbevolen beveiligingsprocedures om te beschermen, SQL Server voor Configuration Manager.  

 **Gebruik de Configuration Manager-Sitedatabaseserver geen andere SQL Server-toepassingen uit te voeren.**  

 Wanneer u de toegang tot de Configuration Manager-Sitedatabaseserver verhoogt, verhoogt dit de risico's voor uw Configuration Manager-gegevens. Als de Configuration Manager-sitedatabase is aangetast, worden andere toepassingen op dezelfde computer met SQL Server vervolgens ook risico plaatsen.  

 **SQL Server voor het gebruik van Windows-verificatie configureren.**  

 Hoewel Configuration Manager toegang heeft tot de sitedatabase met behulp van een Windows-account en de Windows-verificatie, is het nog steeds mogelijk om SQL Server gemengde modus van SQL Server te configureren. Gemengde modus van SQL Server kunnen aanvullende SQL aanmeldingen voor toegang tot de database, die is niet vereist en verhoogt de kwetsbaarheid voor aanvallen.  

 **Neem bijkomende stappen om ervoor te zorgen dat secundaire sites die SQL Server Express gebruiken, beschikken over de meest recente software-updates.**  

 Wanneer u een primaire site installeert, wordt Configuration Manager SQL Server Express kan downloaden vanaf het Microsoft Download Center en kopieert de bestanden naar de primaire siteserver. Wanneer u een secundaire site installeert en de optie selecteert om SQL Server Express installeert, wordt Configuration Manager installeert de eerder gedownloade versie en controleert niet of er nieuwe versies beschikbaar zijn. Om ervoor te zorgen dat de secundaire site de meest recente versies heeft, een van de volgende taken te doen:  

-   Nadat de secundaire site is geïnstalleerd, moet u Windows Update uitvoeren op de secundaire siteserver.  

-   Voordat u de secundaire site installeert, installeert u SQL Server Express handmatig op de computer waarop de secundaire siteserver zal worden uitgevoerd. Zorg er ook voor dat u de meest recente versie en eventuele software-updates installeert. Vervolgens de secundaire site installeert en selecteer de optie voor een bestaand exemplaar van SQL Server gebruiken.  

Voer Windows Update periodiek uit voor deze sites en alle geïnstalleerde versies van SQL Server om ervoor te zorgen dat ze beschikken over de meest recente software-updates.  

**Volg de aanbevolen procedures voor SQL Server.**  

Achterhaal en volg de aanbevolen procedures voor uw versie van SQL Server. Echter rekening met de volgende vereisten voor Configuration Manager:  

-   Het computeraccount van de siteserver moet lid zijn van de groep Beheerders op de computer waar SQL Server op wordt uitgevoerd. Als u de aanbeveling van SQL Server volgt 'beheerder principals expliciet inrichten', moet het account dat u gebruikt om uit te voeren setup op de siteserver moet lid zijn van de SQL-gebruikersgroep.  

-   Als u SQL Server installeert met een domeingebruikersaccount, zorg er dan voor dat het account van de siteservercomputer is geconfigureerd voor de principal-naam van de service (SPN-naam) die is gepubliceerd naar Active Directory Domain Services. Kerberos-verificatie is mislukt zonder de SPN-naam en mislukt de installatie van Configuration Manager.  

##  <a name="BKMK_Security_IIS"></a>Aanbevolen beveiligingsprocedures voor sitesystemen die IIS uitvoeren  
Verschillende sitesysteemrollen in Configuration Manager vereisen IIS. Het proces voor het beveiligen van IIS kunt Configuration Manager correct functioneren en vermindert het risico op beveiligingsaanvallen. Wanneer praktische, Beperk het aantal servers die IIS vereisen. Voer bijvoorbeeld alleen het aantal beheerpunten uit dat u nodig hebt om uw clients te ondersteunen en houdt rekening met de hoge beschikbaarheid en netwerkisolatie voor clientbeheer via het internet.  

 Gebruik de volgende aanbevolen beveiligingsprocedures om te helpen de sitesystemen die IIS uitvoeren, te beveiligen.  

 **Schakel IIS-functies die u niet nodig hebt.**  

 Installeer alleen de IIS-functies die u nodig hebt voor de sitesysteemrol die u installeert. Zie voor meer informatie [Site and site system prerequisites](../../../core/plan-design/configs/site-and-site-system-prerequisites.md) (Vereisten voor sites en sitesystemen).  

 **Configureer de sitesysteemrollen om HTTPS te gebruiken.**  

 Als clients verbinden met een sitesysteem via HTTP in plaats van HTTPS, gebruiken ze Windows-verificatie, en met deze methode is het mogelijk dat ze terugschakelen naar NTLM-verificatie in plaats van Kerberos-verificatie. Als NTLM-verificatie wordt gebruikt, is het mogelijk dat clients verbinden met een rogue server.  

 Distributiepunten zijn een mogelijke uitzondering op deze aanbevolen beveiligingsprocedure, omdat pakkettoegangsaccounts niet werken wanneer het distributiepunt is geconfigureerd voor HTTPS. Pakkettoegangsaccounts geven goedkeuring aan de inhoud; zo kunt u beperken welke gebruikers toegang hebben tot de inhoud. Zie voor meer informatie [aanbevolen beveiligingsprocedures voor inhoudsbeheer](../../../core/plan-design/hierarchy/security-and-privacy-for-content-management.md#BKMK_Security_ContentManagement).  

**Configureer een certificaatvertrouwenslijst (CTL) in IIS voor de sitesysteemrollen.**  

Sitesysteemrollen:  

-   Een distributiepunt dat is geconfigureerd voor HTTPS  

-   Een beheerpunt dat is geconfigureerd voor HTTPS en ingeschakeld voor de ondersteuning van mobiele apparaten

Een certificaatvertrouwenslijst (CTL) is een gedefinieerde lijst van vertrouwde basiscertificeringsinstanties. Wanneer u een CTL met Groepsbeleid en een openbare-sleutelinfrastructuur (PKI)-implementatie gebruikt, wordt er een CTL kunt u vormen een aanvulling op de bestaande vertrouwde basiscertificeringsinstanties die zijn geconfigureerd op uw netwerk, zoals systemen die automatisch worden geïnstalleerd met Microsoft Windows of met behulp van Windows enterprise basiscertificeringsinstanties toegevoegd. Als een CTL in IIS is geconfigureerd, definieert deze echter een subset van deze vertrouwde basiscertificeringsinstanties.  

Deze subset geeft u meer controle over beveiliging omdat CTL de clientcertificaten die worden geaccepteerd, beperkt tot alleen deze die worden verleend uit de lijst certificeringsinstanties in de CTL. Windows wordt bijvoorbeeld geleverd met een aantal certificaten van certificeringsinstanties van een bekende, van derden, zoals VeriSign en Thawte.

Standaard vertrouwt de computer die IIS uitvoert, certificaten die zijn gekoppeld aan deze bekende certificeringsinstanties. Als u IIS niet met een CTL voor de vermelde sitesysteemrollen configureert, wordt elk apparaat dat een clientcertificaat dat is uitgegeven door deze certificeringsinstanties heeft geaccepteerd als een geldige Configuration Manager-client. Als u IIS configureert met een CTL dat deze certificeringsinstanties niet bevat, worden clientverbindingen geweigerd als het certificaat aan deze certificeringsinstellingen is gekoppeld. Voor Configuration Manager-clients kunnen worden geaccepteerd voor de vermelde sitesysteemrollen, moet u IIS echter configureren met een CTL dat de certificeringsinstanties opgeven die worden gebruikt door Configuration Manager-clients.  

> [!NOTE]  
>  Alleen de vermelde sitesysteemrollen, moet u een CTL in IIS te configureren. De lijst met certificaatverleners die Configuration Manager voor beheerpunten gebruikt, bieden dezelfde functionaliteit voor clientcomputers wanneer ze met HTTPS-beheerpunten verbinden.  

Raadpleeg uw IIS-documentatie voor meer informatie over het configureren van een lijst met vertrouwde certificeringsinstanties in IIS.  

**Plaats de siteserver niet op een computer met IIS.**  

Functiescheiding helpt de kwetsbaarheid te verlagen en de herstelmogelijkheden te verbeteren. Bovendien heeft het computeraccount van de siteserver doorgaans beheerdersbevoegdheden op alle sitesysteemrollen (en mogelijk op Configuration Manager-clients, als u push-clientinstallatie gebruiken).  

**Gebruik toegewijde IIS-servers voor Configuration Manager.**  

Hoewel u meerdere webtoepassingen op de IIS-servers die ook door Configuration Manager gebruikt worden hosten kunt, kan deze praktijk uw kwetsbaarheid aanzienlijk verhogen. Een slecht geconfigureerde toepassing kan een aanvaller controle van een Configuration Manager-sitesysteem, waardoor een aanvaller controle krijgt over de hiërarchie kan krijgen.  

Als u andere webtoepassingen op Configuration Manager-sitesystemen uitvoeren moet, maakt u een aangepaste website voor Configuration Manager-sitesystemen.  

**Een aangepaste website gebruiken.**  

U kunt de Configuration Manager voor het gebruik van een aangepaste website in plaats van de standaardwebsite voor IIS configureren voor sitesystemen die IIS uitvoeren. Als u andere webtoepassingen op het sitesysteem uitvoeren, moet u een aangepaste website. Deze instelling is een gehele site-instelling in plaats van een instelling voor een specifiek sitesysteem.  

Naast het bieden van bijkomende beveiliging, moet u een aangepaste website gebruiken als u andere webtoepassingen op het sitesysteem uitvoert.  

**Verwijder de standaard virtuele mappen als u overschakelt van de standaardwebsite naar een aangepaste website na het installeren van distributiepunten.**  

Als u overschakelt van de standaardwebsite naar een aangepaste website, verwijdert Configuration Manager de oude virtuele mappen niet. Verwijder de virtuele mappen die oorspronkelijk door Configuration Manager zijn gemaakt voor de standaardwebsite.  

Dit zijn de virtuele mappen die u bijvoorbeeld moet verwijderen voor een distributiepunt:  

-   SMS_DP_SMSPKG$  

-   SMS_DP_SMSSIG$  

-   NOCERT_SMS_DP_SMSPKG$  

-   NOCERT_SMS_DP_SMSSIG$  

**Volg de aanbevolen procedures voor IIS Server.**  

Achterhaal en volg de aanbevolen procedures voor uw versie van IIS Server. Echter rekening met de vereisten die Configuration Manager voor specifieke sitesysteemrollen heeft. Zie voor meer informatie [Site and site system prerequisites](../../../core/plan-design/configs/site-and-site-system-prerequisites.md) (Vereisten voor sites en sitesystemen).  

##  <a name="BKMK_Security_ManagementPoint"></a>Aanbevolen beveiligingsprocedures voor het beheerpunt  
 Beheerpunten zijn de primaire interface tussen apparaten en Configuration Manager. Houd rekening met aanvallen tegen het beheerpunt en de server waarop deze wordt uitgevoerd op een zeer hoog risico en op de juiste wijze te verhelpen. Pas alle aanbevolen beveiligingsprocedures toe en controleer het systeem op ongewone activiteit.  

 Gebruik de volgende aanbevolen beveiligingsprocedures om te helpen beveiligen van een beheerpunt in Configuration Manager.  

**Wanneer u een Configuration Manager-client op het beheerpunt installeert, kunt u dit aan dat beheerpunt site toewijzen.**  

 Vermijd een scenario waarbij een Configuration Manager-client die zich op een sitesysteem voor beheerpunt bevindt is toegewezen aan een andere site dan de site van het beheerpunt.  

 Als u vanaf een eerdere versie naar System Center Configuration Manager migreert, migreren van de clientsoftware op het beheerpunt naar System Center Configuration Manager zo snel mogelijk.  

##  <a name="BKMK_Security_FSP"></a>Aanbevolen beveiligingsprocedures voor het terugvalstatuspunt  
 Gebruik de volgende aanbevolen beveiligingsprocedures als u een terugvalstatuspunt in Configuration Manager installeert.  

 Zie [Bepalen of u een terugvalstatuspunt](../../../core/clients/deploy/plan/determine-the-site-system-roles-for-clients.md#determine-if-you-need-a-fallback-status-point) nodig hebt voor meer informatie over de beveiligingsoverwegingen wanneer u een terugvalstatuspunt installeert.  


**Voer geen andere sitesysteemrollen op het sitesysteem en niet de status fallback-punt installeert op een domeincontroller.**  

 Omdat het terugvalstatuspunt is ontwikkeld om niet-geverifieerde communicatie van eender welke computer te accepteren, vormt het uitvoeren van deze sitesysteemrol met andere sitesysteemrollen of op een domeincontroller een aanzienlijk hoger risico voor die server.  

**Wanneer u PKI-certificaten voor clientcommunicatie in Configuration Manager gebruikt, installeert u het terugvalstatuspunt voordat u de clients installeert.**  

 Als Configuration Manager-sitesystemen geen HTTP-clientcommunicatie accepteren, kent u mogelijk niet dat clients niet-beheerd door aan PKI gerelateerde certificaatproblemen zijn. Echter, als clients zijn toegewezen aan een terugvalstatuspunt, deze certificaatproblemen worden gemeld door het terugvalstatuspunt.  

 Uit veiligheidsoverwegingen kunt u een terugvalstatuspunt toewijzen aan clients nadat ze zijn geïnstalleerd. In plaats daarvan kunt u deze rol alleen tijdens clientinstallatie toewijzen.  

**Vermijd het gebruik van het terugvalstatuspunt in het perimeternetwerk.**  

 Het terugvalstatuspunt is bedoeld om gegevens van elke client te accepteren. Hoewel een terugvalstatuspunt in het perimeternetwerk u hulp kan bieden bij foutopsporing voor clients op internet, moet u de voordelen voor foutopsporing afwegen tegen het risico van een sitesysteem dat niet-geverifieerde gegevens accepteert in een vrij toegankelijk netwerk.  

 Als u het terugvalstatuspunt in het perimeternetwerk of een niet-vertrouwd netwerk installeert, configureert u de siteserver om gegevensoverdrachten te initiëren in plaats van het terugvalstatuspunt een verbinding met de siteserver tot stand met behulp van de instelling die toestaat.  

##  <a name="BKMK_SecurityIssues_Clients"></a>Beveiligingsproblemen voor sitebeheer  
 Bekijk de volgende beveiligingsproblemen voor Configuration Manager:  

-   Configuration Manager bevat geen beveiliging tegen een geautoriseerde beheergebruiker die Configuration Manager gebruikt voor aanvallen op het netwerk. Niet-geautoriseerde gebruikers met beheerdersrechten kunnen vormen een hoog beveiligingsrisico en talrijke aanvallen doen, waaronder de volgende strategieën:  

    -   Software-implementatie gebruiken automatisch installeren en uitvoeren van schadelijke software op elke Configuration Manager-clientcomputer in de onderneming.  

    -   Gebruik extern beheer op afstand beheren van een Configuration Manager-client zonder toestemming.  

    -   Snelle pollingintervallen en buitensporige hoeveelheden inventaris configureren om DoS-aanvallen te doen tegen de clients en servers.  

    -   Eén site in de hiërarchie gebruiken om gegevens naar Active Directory-gegevens van een andere site te schrijven.  

    Hiërarchie van de site is de beveiligingsgrens. Bedenk dat sites alleen beheergrenzen.  

    Controleer de gehele activiteit van gebruikers met beheerdersrechten en controleer regelmatig de controlelogboeken. Vereist op alle Configuration Manager gebruikers met beheerdersrechten dat zij een achtergrondcontrole ondergaan voordat zij worden aangenomen en eis periodieke hercontroles als arbeidsvoorwaarde.  

-   Als het inschrijvingspunt in het geding komt, zou een kwaadwillend persoon certificaten voor verificatie kunnen verkrijgen en de referenties kunnen stelen van gebruikers die hun mobiele apparaten inschrijven.  

    Het inschrijvingspunt communiceert met een certificeringinstantie en kan Active Directory-objecten maken, aanpassen en verwijderen. Het inschrijvingspunt nooit installeren in het perimeternetwerk en altijd op ongewone activiteit controleren.  

-   Als u beleidsregels van gebruikers toestaat voor clientbeheer op internet of het Application Catalog-websitepunt voor gebruikers configureert wanneer zij op het internet zijn, vergroot u uw beveiligingsrisico voor een aanval.  

    Naast het gebruik van PKI-certificaten voor verbindingen tussen client en server vereisen deze configuraties Windows-verificatie, wat mogelijk erop neerkomt dat u NTLM-verificatie gebruikt in plaats van Kerberos. NTLM-verificatie is kwetsbaar voor imitatie- en replayaanvallen. Als u een gebruiker op het internet wilt verifiëren, moet u een verbinding toestaan van de sitesysteemserver op internet met een domeincontroller.  

-   De Admin$-share is vereist op sitesysteemservers.  

    De Configuration Manager-siteserver gebruikt de Admin$-share voor verbinding maken met en het uitvoeren van de servicebewerkingen op sitesystemen. U dient de Admin$-share niet uit te schakelen of te verwijderen.  

-   Configuration Manager maakt gebruik van naamomzettingsservices verbinding maken met andere computers en deze services zijn moeilijk te beveiligen tegen beveiligingsaanvallen zoals vervalsing, knoeien, ontkenning, openbaarmaking van informatie, DOS-aanval en bevoegdheden.  

    Stel de aanbevolen procedures voor beveiliging vast voor de DNS- en WINS-versie die u voor naamomzetting gebruikt.  

##  <a name="BKMK_Privacy_Cliients"></a>Privacyinformatie voor detectie  
 Detectie records gemaakt voor netwerkbronnen en slaat ze op in de System Center Configuration Manager-database. Records van detectiegegevens bevatten computergegevens zoals IP-adressen, besturingssystemen en computernamen. U kunt Active Directory-detectiemethoden tevens zodanig configureren, dat in Active Directory Domain Services opgeslagen informatie wordt gedetecteerd.  

 De enige detectiemethode die standaard is ingeschakeld is Heartbeat Discovery, maar deze methode detecteert alleen computers die al de System Center Configuration Manager-clientsoftware geïnstalleerd hebben.  

 Er wordt geen detectie-informatie naar Microsoft verzonden. Het item wordt opgeslagen in de Configuration Manager-database. Informatie wordt bewaard in de database tot deze om de 90 dagen wordt verwijderd door de siteonderhoudstaak **verouderde Detectiegegevens verwijderen**.  

 Bedenk goed wat uw privacyvereisten zijn, voordat u extra detectiemethoden configureert of de Active Directory-detectie uitbreidt,  
