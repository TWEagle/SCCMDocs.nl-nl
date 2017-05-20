---
title: Technische naslaginformatie voor cryptografische besturingselementen | Microsoft-documenten
description: Meer informatie over hoe ondertekening en versleuteling beschermen aanvallen helpen kunnen vanuit het lezen van gegevens in System Center Configuration Manager.
ms.custom: na
ms.date: 10/06/2016
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 0c63dcc5-a1bd-4037-959a-2e6ba0fd1b2c
caps.latest.revision: 6
author: arob98
ms.author: angrobe
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 2c723fe7137a95df271c3612c88805efd8fb9a77
ms.openlocfilehash: 09d319ce817c925ac002a27733d2ce35464eeca7
ms.contentlocale: nl-nl
ms.lasthandoff: 05/17/2017


---
# <a name="cryptographic-controls-technical-reference"></a>Technische naslaginformatie voor cryptografische besturingselementen

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*


System Center Configuration Manager gebruikt ondertekening en versleuteling voor het beheer van de apparaten in de Configuration Manager-hiërarchie te beschermen. Met het aanmelden, als gegevens is gewijzigd tijdens de verzending en wordt dit genegeerd. Versleuteling helpt voorkomen dat aanvallers lezen van de gegevens met behulp van een netwerkprotocolanalyse.  

 Het primaire hash-algoritme dat Configuration Manager voor ondertekening gebruikt is SHA-256. Wanneer twee Configuration Manager-sites met elkaar communiceren, ondertekenen ze hun communicatie met SHA-256. Primaire versleutelingsalgoritme dat is geïmplementeerd in Configuration Manager is 3DES. Dit wordt gebruikt voor het opslaan van gegevens in de Configuration Manager-database en voor HTTP-clientcommunicatie. Wanneer u clientcommunicatie via HTTPS gebruikt, kunt u uw openbare-sleutelinfrastructuur (PKI)-RSA-certificaten te gebruiken met het maximale aantal hash-algoritmen en sleutellengten die zijn gedocumenteerd in [PKI-certificaatvereisten voor System Center Configuration Manager](../../core/plan-design/network/pki-certificate-requirements.md).  

 Voor de meeste cryptografiebewerkingen voor op Windows gebaseerde besturingssystemen gebruikt Configuration Manager de algoritmen SHA-2, 3DES en AES, en RSA uit rsaenh.dll, de Windows CryptoAPI-bibliotheek.  

> [!IMPORTANT]  
>  Informatie over aanbevolen wijzigingen in reactie op SSL beveiligingslekken in [over SSL beveiligingslekken](#about-ssl-vulnerabilities).  

##  <a name="cryptographic-controls-for-configuration-manager-operations"></a>Cryptografische besturingselementen voor Configuration Manager-bewerkingen  
 Gegevens in Configuration Manager kan worden ondertekend en versleuteld, of u PKI-certificaten gebruikt met Configuration Manager of niet.  

### <a name="policy-signing-and-encryption"></a>Beleid voor ondertekening en versleuteling  
 Toewijzingen van clientbeleid worden ondertekend door het zelfondertekende handtekeningcertificaat van de siteserver om het risico te helpen voorkomen op een aangetast verzendbeleid van een beheerpunt waarmee is geknoeid. Dit is belangrijk als u clientbeheer via Internet omdat deze omgeving een beheerpunt vereist die wordt blootgesteld aan internetcommunicatie.  

 Beleid wordt versleuteld met 3DES als het gevoelige gegevens bevat. Beleid dat gevoelige gegevens bevat, wordt alleen verzonden naar geautoriseerde clients. Beleid dat geen gevoelige gegevens bevat, wordt niet versleuteld.  

 Wanneer beleid op de clients wordt opgeslagen, wordt het versleuteld met Data Protection application programming interface (DPAPI).  

### <a name="policy-hashing"></a>Hashing van beleid  
 Wanneer Configuration Manager-clients beleid aanvragen, krijgen ze eerst een beleidtoewijzing zodat ze weten welk beleid op hen van toepassing is. vervolgens worden ze alleen die beleidhoofdteksten aangevraagd. Elke beleidtoewijzing bevat de berekende hash voor de overeenkomstige beleidhoofdtekst. De client haalt de van toepassing zijnde beleidhoofdteksten op en berekent vervolgens de hash op die hoofdtekst. Als de hash op de gedownloade beleidhoofdtekst niet overeenkomt met de hash in de beleidtoewijzing, verwijdert de client de beleidhoofdtekst.  

 Het hash-algoritme voor beleid is SHA-1 en SHA-256.  

### <a name="content-hashing"></a>Hashing van inhoud  
 De distributiebeheerservice op de siteserver hasht de inhoudsbestanden voor alle pakketten. De beleidsprovider neemt de hash op in het softwaredistributiebeleid. Wanneer de Configuration Manager-client de inhoud downloadt, wordt de client genereert de hash lokaal opnieuw en vergelijkt deze met de hash van het beleid. Als de hashes overeenkomen, werd de inhoud niet gewijzigd en zal de client het installeren. Zodra er één enkele byte is gewijzigd, komen de hashes niet overeen en zal de software niet worden geïnstalleerd. Deze controle helpt om te garanderen dat de correcte software wordt geïnstalleerd, omdat de werkelijke inhoud aan het beleid wordt getoetst.  

 Het standaard hash-algoritme voor inhoud is SHA-256. Deze standaardwaarde, Zie de documentatie voor de Configuration Manager Software Development Kit (SDK).  

 Niet alle apparaten kunnen inhoud-hashing ondersteunen. De uitzonderingen omvatten:  

-   Windows-clients wanneer ze App-V-inhoud streamen.  

-   Windows Phone-clients, hoewel deze clients verifiëren van de handtekening van een toepassing die is ondertekend door een vertrouwde bron.  

-   Windows RT-client, hoewel deze clients verifiëren van de handtekening van een toepassing die is ondertekend door een vertrouwde bron en ook volledige (PFN) validatie van pakketnaam gebruiken.  

-   voor iOS, hoewel deze apparaten verifiëren van de handtekening van een toepassing die is ondertekend door eender welk ontwikkelaarscertificaat van een vertrouwde bron.  

-   Nokia-client, maar deze clients verifiëren de handtekening van een toepassing die een zelfondertekend certificaat gebruikt. De handtekening van een certificaat van een vertrouwde bron en het certificaat kunnen toepassingen van Nokia Symbian Installation Source (SIS) ondertekenen.  

-   Android. Deze apparaten gebruiken bovendien geen handtekeningvalidatie voor het installeren van toepassingen.  

-   Clients met Linux- of UNIX-versies die SHA-256 niet ondersteunen. Zie voor meer informatie [Planning voor clientimplementatie op Linux en UNIX-computers in System Center Configuration Manager](../../core/clients/deploy/plan/planning-for-client-deployment-to-linux-and-unix-computers.md).  

### <a name="inventory-signing-and-encryption"></a>Inventaris ondertekening en versleuteling  
 Inventaris die clients verzenden naar beheerpunten wordt altijd ondertekend door apparaten, ongeacht of ze communiceren met beheerpunten via HTTP of HTTPS. Als ze HTTP gebruiken, kunt u kiezen om deze gegevens te versleutelen, wat een aanbevolen beveiligingsprocedure is.  

### <a name="state-migration-encryption"></a>Statusmigratieversleuteling  
 Gegevens die zijn opgeslagen op statusmigratiepunten voor besturingssysteemimplementatie wordt altijd versleuteld door het hulpprogramma voor migratie van gebruikersstatus (USMT) door 3DES te gebruiken.  

### <a name="encryption-for-multicast-packages-to-deploy-operating-systems"></a>Versleuteling voor multicast-pakketten om besturingssystemen te implementeren  
 Voor elk pakket voor besturingssysteemimplementatie kunt u versleuteling inschakelen wanneer het pakket wordt verzonden naar computers door gebruik te maken van multicast. De versleuteling gebruikt Advanced Encryption Standard (AES). Als u versleuteling inschakelt, is er geen aanvullende certificaatconfiguratie vereist. Het multicast-distributiepunt genereert automatisch symmetrische sleutels voor het versleutelen van het pakket. Elk pakket heeft een andere versleutelingssleutel. De sleutel wordt opgeslagen op het multicast-distributiepunt met standaard Windows-API's. Wanneer de client verbinding maakt met de multicast-sessie, gebeurt de uitwisseling van de sleutel over een kanaal dat is versleuteld met het door PKI uitgegeven certificaat voor clientverificatie (als de client HTTPS gebruikt) of met het zelfondertekende certificaat (als de client HTTP gebruikt). De client slaat de sleutel alleen op in het geheugen voor de duur van de multicast-sessie.  

### <a name="encryption-for-media-to-deploy-operating-systems"></a>Versleuteling voor media om besturingssystemen te implementeren  
 Als u media gebruikt om besturingssystemen te implementeren en een wachtwoord opgeeft om de media te beveiligen, worden de omgevingsvariabelen versleuteld met Advanced Encryption Standard (AES). Andere gegevens op de media, waaronder pakketten en inhoud voor toepassingen, worden niet versleuteld.  

### <a name="encryption-for-content-that-is-hosted-on-cloud-based-distribution-points"></a>Versleuteling voor inhoud die wordt gehost op cloud-gebaseerde distributiepunten  
 Beginnen met System Center 2012 Configuration Manager SP1, wanneer u cloud-gebaseerde distributiepunten gebruikt, is de inhoud die u naar deze distributiepunten uploadt versleuteld met Advanced Encryption Standard (AES) met een 256-bits sleutelgrootte. De inhoud wordt opnieuw versleuteld wanneer u die bijwerkt. Als clients de inhoud downloaden, wordt deze versleuteld en beveiligd door de HTTPS-verbinding.  

### <a name="signing-in-software-updates"></a>Aanmelden van softwareupdates  
 Alle software-updates moeten worden aangemeld door een vertrouwde uitgever om te beveiligen tegen knoeien. Op clientcomputers scant de Windows Update Agent (WUA) naar de updates uit de catalogus, maar de update zal niet worden geïnstalleerd als het digitale certificaat niet kan worden gevonden in het archief Vertrouwde uitgevers op de lokale computer. Als er een zelfondertekend certificaat werd gebruikt voor het publiceren van de updatecatalogus, zoals WSUS Publishers Self-signed, moet het certificaat ook in het certificaatarchief van de Vertrouwde basiscertificeringsinstanties op de lokale computer aanwezig zijn om de geldigheid van het certificaat te verifiëren. WUA controleert ook of de instelling **Ondertekende inhoud van groepsbeleid van Microsoft-updateservicelocatie via intranet toestaan** is ingeschakeld op de lokale computer. Deze beleidsinstelling moet worden ingeschakeld voor WUA om te scannen naar de updates die zijn gemaakt en gepubliceerd met Updates Publisher.  

 Als software-updates in System Center Updates Publisher zijn gepubliceerd, ondertekent een digitaal certificaat de software-updates wanneer ze naar een updateserver zijn gepubliceerd. U kunt een PKI-certificaat opgeven of de Updates Publisher configureren om een zelfondertekend certificaat te genereren om de software-update te ondertekenen.  

### <a name="signed-configuration-data-for-compliance-settings"></a>Ondertekende configuratiegegevens voor compatibiliteitsinstellingen  
 Wanneer u configuratiegegevens importeert, verifieert Configuration Manager de digitale handtekening van het bestand. Als de bestanden niet zijn ondertekend of als de verificatiecontrole van de digitale handtekening mislukt, ontvangt u een waarschuwing en wordt u gevraagd of u wilt doorgaan met importeren. Blijf de configuratiegegevens alleen importeren als u de uitgever en de integriteit van de bestanden expliciet vertrouwt.  

### <a name="encryption-and-hashing-for-client-notification"></a>Versleuteling en hashing voor clientmeldingen  
 Als u gebruik maakt van clientmeldingen, zal alle communicatie TLS en de meeste geavanceerde versleuteling gebruiken die de server en de clientbesturingssystemen kunnen onderhandelen. Een clientcomputer waarop bijvoorbeeld Windows 7 wordt uitgevoerd en een beheerpunt waarop Windows Server 2008 R2 wordt uitgevoerd, kunnen 128-bits AES-versleuteling ondersteunen, hoewel een clientcomputer waarop Vista wordt uitgevoerd naar hetzelfde beheerpunt, zal onderhandelen naar 3DES-versleuteling. Dezelfde onderhandeling doet zich voor bij hashing voor pakketten die worden overgedragen tijdens clientmeldingen, waarvoor SHA-1 of SHA-2 wordt gebruikt.  

##  <a name="certificates-used-by-configuration-manager"></a>Certificaten die worden gebruikt door Configuration Manager  
 Voor een lijst van de openbare-sleutelinfrastructuur (PKI)-certificaten die kunnen worden gebruikt door Configuration Manager, eventuele speciale vereisten of beperkingen, en hoe u de certificaten worden gebruikt, Zie [PKI-certificaatvereisten voor System Center Configuration Manager](../../core/plan-design/network/pki-certificate-requirements.md). Deze lijst bevat de ondersteunde hash-algoritmen en sleutellengten. De meeste certificaten ondersteunen sleutellengten van SHA-256 en 2048 bits.  

> [!NOTE]  
>  Alle certificaten die Configuration Manager gebruikt mogen alleen enkel-byte tekens bevatten in de onderwerpnaam of alternatieve naam voor onderwerp.  

 PKI-certificaten zijn vereist voor de volgende scenario's:  

-   Als u Configuration Manager-clients op het Internet beheert.  

-   Als u Configuration Manager-clients op mobiele apparaten beheert.  

-   Als u Mac-computers beheert.  

-   Als u cloud-gebaseerde distributiepunten gebruikt.  

-   Als u buiten-band op Intel AMT gebaseerde computers beheert.  

 Voor de meeste andere Configuration Manager-communicaties die certificaten voor verificatie vereisen, ondertekening of versleuteling, gebruikt Configuration Manager automatisch PKI-certificaten indien ze beschikbaar zijn. Als ze niet beschikbaar zijn, wordt in Configuration Manager zelfondertekende certificaten genereert.  

 Configuration Manager gebruikt geen PKI-certificaten wanneer het mobiele apparaten beheert via de Exchange Server-connector.  

### <a name="mobile-device-management-and-pki-certificates"></a>Beheer van mobiele apparaten en PKI-certificaten  
 Als het mobiele apparaat niet is vergrendeld door de mobiele operator, kunt u Configuration Manager of Microsoft Intune aanvragen en installeren van een clientcertificaat. Dit certificaat biedt wederzijdse verificatie tussen de client op het mobiele apparaat en de sitesystemen van Configuration Manager of de Microsoft Intune-services. Als uw mobiele apparaat is vergrendeld, kunt u Configuration Manager of Intune niet gebruiken om certificaten te implementeren.  

 Als u hardware-inventaris voor mobiele apparaten inschakelt, inventariseert Configuration Manager of Intune ook de certificaten die zijn geïnstalleerd op het mobiele apparaat.  

### <a name="out-of-band-management-and-pki-certificates"></a>Buiten-bandbeheer en PKI-certificaten  
 Buiten-bandbeheer voor op Intel AMT gebaseerde computers gebruikt minstens twee soorten door PKI verleende certificaten: een AMT-inrichtingscertificaat en een webservercertificaat.  

 Het buiten-band-servicepunt gebruikt een AMT-inrichtingscertificaat om computers voor te bereiden op buiten-bandbeheer. De op AMT gebaseerde computers die zullen worden ingericht, moeten het certificaat vertrouwen dat wordt aangeboden door het buiten-bandbeheerpunt. Standaard worden op AMT gebaseerde computers geconfigureerd door de computerfabrikant om gebruik te maken van externe certificeringsinstanties (CA's) als VeriSign Go Daddy, Comodo en Starfield. Als u een inrichtingscertificaat van een van de externe CA's koopt en configureren van Configuration Manager om dit inrichtingscertificaat te gebruiken, zullen AMT-gebaseerde computers de CA van het inrichtingscertificaat vertrouwen en de inrichting kan worden voltooid. Het is echter een aanbevolen beveiligingsprocedure om uw eigen interne CA te gebruiken om het AMT-inrichtingscertificaat te verlenen.  

 Op de op AMT gebaseerde computers wordt een webserveronderdeel uitgevoerd binnen hun firmware en dit webserveronderdeel versleutelt het communicatiekanaal met het buiten-bandservicepunt door gebruik te maken van Transport Layer Security (TLS). Er is geen gebruikersinterface in het AMT BIOS om een certificaat handmatig te configureren. U moet een Microsoft-bedrijfscertificeringsinstantie hebben die automatisch certificaataanvragen van aanvragende op AMT gebaseerde computers goedkeurt. De aanvraag gebruikt PKCS#10 voor de aanvraagindeling. Deze gebruikt op zijn beurt PKCS#7 voor het overdragen van de certificaatinformatie naar de op AMT gebaseerde computer.  

 Hoewel de op AMT gebaseerde computer wordt geverifieerd naar de computer die deze beheert, is er geen overeenkomstig PKI-clientcertificaat. In plaats daarvan gebruikt dergelijke communicatie Kerberos- of HTTP Digest-verificatie. Als HTTP Digest wordt gebruikt, wordt er TLS-versleuteling gebruikt.  

 Een bijkomende certificaattype kan vereist zijn voor het buiten-bandbeheer van op AMT gebaseerde computers: een optioneel clientcertificaat voor 802.1X-geverifieerde bekabelde en draadloze netwerken. Het clientcertificaat kan vereist zijn door de op AMT gebaseerde computer voor verificatie naar de RADIUS-server. Er is altijd een clientcertificaat vereist als de RADIUS-server voor EAP-TLS-verificatie is geconfigureerd. Als de RADIUS-server voor EAP-TTLS/MSCHAPv2 of PEAPv0/EAP-MSCHAPv2 geconfigureerd is, specificeert de RADIUS-configuratie of een clientcertificaat vereist is of niet. Dit certificaat wordt gevraagd door de op AMT gebaseerde computer door gebruik te maken van dezelfde processen als de certificaataanvraag van de webserver.  

### <a name="operating-system-deployment-and-pki-certificates"></a>Implementatie van besturingssystemen en PKI-certificaten  
 Wanneer u Configuration Manager gebruiken om besturingssystemen te implementeren en een beheerpunt HTTPS-clientverbinding vereist, de clientcomputer moet ook een certificaat hebben om te communiceren met het beheerpunt, zelfs al het in een overgangsfase is is zoals opstarten vanaf takenreeksmedia of een distributiepunt met PXE-functionaliteit. Om dit scenario de ondersteunen, moet u een PKI-clientverificatiecertificaat maken en met de persoonlijke sleutel exporteren en vervolgens importeren naar de siteservereigenschappen en ook toevoegen de management pointâ€™ s vertrouwde basis-CA-certificaat.  

 Als u opstartbare media maakt, importeert u het certificaat voor clientverificatie wanneer u de opstartbare media maakt. Configureer een wachtwoord op de opstartbare media om te helpen de persoonlijke sleutel en andere gevoelige gegevens te beschermen die in de takenreeks zijn geconfigureerd. Elke computer die opstart vanaf de opstartbare media, zal hetzelfde certificaat tonen aan het beheerpunt zoals vereist voor clientfuncties zoals het aanvragen van het clientbeleid.  

 Als u een PXE-opstartapparaat gebruikt, importeert u het certificaat voor clientverificatie naar het distributiepunt met PXE-functionaliteit en het gebruikt hetzelfde certificaat voor elke client die opstart vanuit dat distributiepunt met PXE-functionaliteit. Uit veiligheidsoverwegingen wordt het aanbevolen dat gebruikers die hun computers aansluiten op een PXE-service een wachtwoord moeten ingeven om te helpen de persoonlijke sleutel en andere gevoelige gegevens in de takenreeksen te beschermen.  

 Blokkeer de certificaten voor clientverificatie, als ermee is geknoeid, in het knooppunt **Certificaten** in de werkruimte **Beheer,** knooppunt **Beveiliging** . Om deze certificaten te beheren, moet u het recht **Implementatiecertificaat van het besturingssysteem beheren** .  

 Nadat het besturingssysteem is geïmplementeerd en de Configuration Manager is geïnstalleerd, moet de client haar eigen PKI-clientverificatiecertificaat voor HTTPS-clientcommunicatie.  

### <a name="isv-proxy-solutions-and-pki-certificates"></a>ISV-proxyoplossingen en PKI-certificaten  
 Onafhankelijke softwareleveranciers (ISV's) kunnen toepassen maken die Configuration Manager uitbreiden. Een ISV zou bijvoorbeeld extensies kunnen maken om niet-Windows clientplatforms zoals Macintosh of UNIX-computers te ondersteunen. Als de sitesystemen echter HTTPS-clientverbindingen vereisen, moeten de clients ook PKI-certificaten gebruiken voor communicatie met de site. Configuration Manager biedt de mogelijkheid een certificaat toewijzen aan de ISV-proxy die communicatie mogelijk tussen de ISV-proxyclients en het beheerpunt maakt. Als u extensies gebruikt die ISV-proxycertificaten vereisen, raadpleeg dan de documentatie voor dat product. Zie voor meer informatie over hoe u ISV-proxycertificaten maakt, de Configuration Manager Software Developer Kit (SDK).  

 Blokkeer het ISV-certificaat, als ermee is geknoeid, in het knooppunt **Certificaten** van de werkruimte **Beheer** in het knooppunt **Beveiliging** .  

### <a name="asset-intelligence-and-certificates"></a>Asset intelligence en certificaten  
 Configuration Manager installeert met een X.509-certificaat dat het Asset Intelligence-synchronisatiepunt wordt gebruikt voor verbinding met Microsoft. Dit certificaat wordt gebruikt om een certificaat voor clientverificatie vragen van de Microsoft-certificaatservice Configuration Manager. Het certificaat voor clientverificatie wordt geïnstalleerd op de sitesysteemserver van het Asset Intelligence-synchronisatiepunt en het wordt gebruikt om de server met Microsoft te verifiëren. Configuration Manager gebruikt het certificaat voor clientverificatie om de Asset Intelligence-catalogus te downloaden en softwaretitels te uploaden.  

 Dit certificaat heeft een sleutellengte van 1024 bits.  

### <a name="cloud-based-distribution-points-and-certificates"></a>Cloud-gebaseerde distributiepunten en certificaten  
 Beginnen met System Center 2012 Configuration Manager SP1, cloud-gebaseerde distributiepunten vereisen een beheercertificaat (zelfondertekend of PKI) dat u uploadt naar Microsoft Azure. Dit beheercertificaat vereist een functionaliteit voor serververificatie en een sleutellengte van het certificaat van 2048 bits. Daarnaast moet u een servicecertificaat configureren voor elk distributiepunt in de cloud, dat niet zelfondertekend kan zijn, maar ook de functionaliteit voor serververificatie en een minimum sleutellengte van het certificaat van 2048 bits heeft.  

> [!NOTE]  
>  Het zelfondertekende beheercertificaat dient uitsluitend voor tests en niet voor gebruik op productienetwerken.  

 Clients vereisen geen PKI-certificaat van de client om distributiepunten in de cloud te gebruiken; ze verifiëren naar het beheer met behulp van hetzij een zelfondertekend certificaat hetzij een PKI-certificaat van de client. Het beheerpunt verstuurt vervolgens een toegangstoken van Configuration Manager naar de client, hetgeen de client aan het cloud-gebaseerde distributiepunt toont. Het token is 8 uur lang geldig.  

### <a name="the-microsoft-intune-connector-and-certificates"></a>De Connector voor Microsoft Intune en certificaten  
 Wanneer Microsoft Intune mobiele apparaten inschrijft, kunt u deze mobiele apparaten in Configuration Manager beheren door een Microsoft Intune-connector te maken. De connector gebruikt een PKI-certificaat met mogelijkheid tot clientverificatie voor het verifiëren van Configuration Manager naar Microsoft Intune en alle informatie te brengen tussen deze met behulp van SSL. De sleutelgrootte van het certificaat is 2048 bits en gebruikt het hash-algoritme SHA-1.  

 Wanneer u de connector installeert, wordt een handtekeningcertificaat gemaakt en opgeslagen op de siteserver voor het extern laden van sleutels, en wordt er een versleutelingscertificaat gemaakt en opgeslagen op het certificaatregistratiepunt om de Simple Certificate Enrollment Protocol (SCEP)-vraag te versleutelen. Deze certificaten hebben ook een sleutelgrootte van 2048 bits en gebruiken het hash-algoritme SHA-1.  

 Wanneer Intune mobiele apparaten inschrijft, installeert het een PKI-certificaat op het mobiele apparaat. Dit certificaat heeft ook een mogelijkheid voor clientverificatie, gebruikt een sleutelgrootte van 2048 bits en gebruikt het hash-algoritme SHA-1.  

 Deze PKI-certificaten worden automatisch aangevraagd, gegenereerd en geïnstalleerd door Microsoft Intune.  

### <a name="crl-checking-for-pki-certificates"></a>CRL-controle voor PKI-certificaten  
 Een PKI-certificaatintrekkingslijst (CRL) verhoogt de administratieve en verwerkingsoverhead, maar het is veiliger. Als CRL-controle echter is ingeschakeld, maar de CRL niet beschikbaar is, mislukt de PKI-verbinding. Zie voor meer informatie [beveiliging en privacy voor System Center Configuration Manager](../../core/plan-design/security/security-and-privacy.md).  

 (Certificaatintrekkingslijst) certificaatintrekkingscontrole is standaard ingeschakeld in IIS, dus als u een CRL met uw PKI-implementatie, er niets extra's worden configureren op de meeste Configuration Manager-sitesystemen die IIS uitvoeren. Een uitzondering hierop zijn de software-updates, die een handmatige stap vereisen om CRL-controle in te schakelen om de handtekeningen op software-updatebestanden te controleren.  

 CRL-controle wordt standaard ingeschakeld voor clientcomputers wanneer ze HTTPS-clientverbindingen gebruiken. CRL-controle is standaard niet ingeschakeld wanneer u de buiten-bandbeheerconsole uitvoert om een verbinding te maken met een op AMT gebaseerde computer, en u kunt deze optie inschakelen. U kunt CRL-controle voor clients op Mac-computers in Configuration Manager SP1 of hoger niet uitschakelen.  

 CRL-controle wordt niet ondersteund voor de volgende verbindingen in Configuration Manager:  

-   Server-naar-server-verbindingen.  

-   Mobiele apparaten die zijn ingeschreven door Configuration Manager.  

-   Mobiele apparaten die zijn geregistreerd door Microsoft Intune.  

##  <a name="cryptographic-controls-for-server-communication"></a>Cryptografische besturingselementen voor servercommunicatie  
 Configuration Manager maakt gebruik van de volgende cryptografische besturingselementen voor servercommunicatie.  

### <a name="server-communication-within-a-site"></a>Servercommunicatie binnen een site  
 Elke sitesysteemserver gebruikt een certificaat gegevens overdraagt naar andere sitesystemen in dezelfde Configuration Manager-site. Sommige sitesysteemrollen gebruiken ook certificaten voor verificatie. Als u het inschrijvingsproxypunt bijvoorbeeld op een server installeert en het inschrijvingspunt op een andere server, kunnen ze elkaar verifiëren met behulp van dit identiteitscertificaat. Wanneer een certificaat voor deze communicatie gebruikt, wordt alleen gebruikt voor Configuration Manager als er een PKI-certificaat beschikbaar die de mogelijkheid voor serververificatie heeft, Configuration Manager automatisch gebruikt. Als dat niet het geval is, Configuration Manager genereert een zelfondertekend certificaat. Dit zelfondertekende certificaat heeft een mogelijkheid voor serververificatie, gebruikt SHA-256 en heeft een sleutellengte van 2048 bits. Configuration Manager kopieert het certificaat naar het archief Vertrouwde personen op andere sitesysteemservers die mogelijk moeten vertrouwen van het sitesysteem. Sitesystemen kunnen elkaar dan vertrouwen met behulp van deze certificaten en PeerTrust.  

 Naast dit certificaat voor elke sitesysteemserver genereert Configuration Manager een zelfondertekend certificaat voor de meeste sitesysteemrollen. Wanneer er meer dan één exemplaar van de sitesysteemrol in dezelfde site is, delen ze hetzelfde certificaat. U kunt bijvoorbeeld meerdere beheerpunten of meerdere inschrijvingspunten in dezelfde site hebben. Dit zelfondertekende certificaat gebruikt ook SHA-256 en heeft een sleutellengte van 2048 bits. Het wordt ook gekopieerd naar het archief Vertrouwde personen op sitesysteemservers die het mogelijk moeten  vertrouwen. De volgende sitesysteemrollen genereren dit certificaat:  

-   Application Catalog-webservicepunt  

-   Application Catalog-websitepunt  

-   Asset Intelligence-synchronisatiepunt  

-   Certificaatregistratiepunt  

-   Endpoint Protection-punt  

-   Inschrijvingspunt  

-   Terugvalstatuspunt  

-   Beheerpunt  

-   Multicast-distributiepunt  

-   Buiten-bandservicepunt  

-   Reporting Services-punt  

-   Software-updatepunt  

-   Statusmigratiepunt  

-   Systeemstatuscontrolepunt  

-   Microsoft Intune-connector  

 Deze certificaten worden automatisch beheerd door Configuration Manager en wanneer noodzakelijk, automatisch gegenereerd.  

 Configuration Manager gebruikt ook een certificaat voor clientverificatie om statusberichten te zenden van het distributiepunt naar het beheerpunt. Wanneer het beheerpunt enkel is geconfigureerd voor HTTPS-clientverbindingen, moet u een PKI-certificaat gebruiken. Als het beheerpunt HTTP-verbindingen aanvaardt, kunt u een PKI-certificaat gebruiken of de optie selecteren om een zelfondertekend certificaat te gebruiken dat de mogelijkheid voor clientverificatie heeft, SHA-256 gebruikt en een sleutellengte van 2048 bits heeft.  

### <a name="server-communication-between-sites"></a>Servercommunicatie tussen sites  
 Configuration Manager draagt gegevens over tussen sites door zowel databasereplicatie als replicatie op basis van bestanden. Zie voor meer informatie [communicatie tussen eindpunten in System Center Configuration Manager](../../core/plan-design/hierarchy/communications-between-endpoints.md).  

 Configuration Manager automatisch configureert het databasereplicatie tussen sites en gebruikt PKI-certificaten die de functionaliteit voor serververificatie hebben als deze beschikbaar zijn; Als dat niet het geval is, maakt Configuration Manager zelfondertekende certificaten voor serververificatie. In beide gevallen wordt verificatie tussen sites tot stand gebracht met behulp van certificaten in het archief Vertrouwde Personen dat PeerTrust gebruikt. Dit certificaatarchief wordt gebruikt om ervoor te zorgen dat de SQL Server-computers die worden gebruikt door de Configuration Manager-hiërarchie, deelnemen aan replicatie tussen sites. Terwijl primaire sites en de centrale beheersite configuratiewijzigingen kunnen repliceren naar alle sites in de hiërarchie, kunnen secundaire sites configuratiewijzigingen enkel repliceren naar de bovenliggende site ervan.  

 Siteservers brengen communicatie van site naar site tot stand met behulp van de beveiligde sleuteluitwisseling die automatisch plaatsvindt. De verzendende siteserver genereert een hash en tekent het met zijn persoonlijke sleutel. De ontvangende siteserver controleert de handtekening met behulp van de publieke sleutel en vergelijkt de hash met een lokaal gegenereerde waarde. Als ze overeenkomen, worden de gerepliceerde gegevens in de ontvangende site aanvaard. Als de waarden niet overeenkomen, verwerpt Configuration Manager de replicatiegegevens.  

 Databasereplicatie in Configuration Manager maakt gebruik van de SQL Server Service Broker voor gegevensoverdracht tussen sites met behulp van de volgende mechanismen:  

-   SQL Server naar SQL Server-verbinding: Dit maakt gebruik van Windows-referenties voor serververificatie en zelfondertekende certificaten met 1024 bits om te ondertekenen en versleutelen van de gegevens met behulp van Advanced Encryption Standard (AES). Als er PKI-certificaten met de functionaliteit voor serververificatie beschikbaar zijn, zullen deze worden gebruikt. Het certificaat moet zich in het persoonlijke archief voor het certificaatarchief van de computer bevinden.  

-   SQL Service Broker: Dit maakt gebruik van zelfondertekende certificaten met 2048 bits voor verificatie en om het te ondertekenen en versleutelen van de gegevens met behulp van Advanced Encryption Standard (AES). Het certificaat moet zich in de hoofddatabase van de SQL Server bevinden.  

 Replicatie op basis van een bestand gebruikt het SMB-protocol (Server Message Block) en gebruikt SHA-256 om de gegevens te ondertekenen die niet zijn versleuteld, maar geen gevoelige gegevens bevatten. Als u wilt dat deze gegevens te versleutelen, kunt u IPsec gebruiken en moet worden geïmplementeerd dit onafhankelijk van Configuration Manager.  

##  <a name="cryptographic-controls-for-clients-that-use-https-communication-to-site-systems"></a>Cryptografische besturingselementen voor clients die HTTPS-communicatie naar sitesystemen gebruiken  
 Wanneer sitesysteemrollen clientverbindingen aanvaarden, kunt u ze configureren om HTTPS- en HTTP-verbindingen, of enkel HTTPS-verbindingen te aanvaarden. Sitesysteemrollen die verbindingen van het internet aanvaarden, aanvaarden enkel clientverbindingen over HTTPS.  

 Clientverbindingen over HTTPS bieden een hogere veiligheidsgraad door integratie met een PKI (Public Key Infrastructure) om communicatie van de client naar de server te helpen beschermen. HTTPS-clientverbindingen configureren zonder een grondig begrip van PKI-planning, implementatie en bewerkingen kan u echter nog in een kwetsbare positie plaatsen. Als u uw basiscertificeringsinstantie bijvoorbeeld niet beveiligt, kunnen aanvallers knoeien met het vertrouwen van uw volledige PKI-infrastructuur. Als u er niet in slaagt de PKI-certificaten te implementeren en beheren met behulp van gecontroleerde en beveiligde processen, kan dit leiden tot onbeheerde clients die geen kritische software-updates of pakketten kunnen ontvangen.  

> [!IMPORTANT]  
>  De PKI-certificaten die worden gebruikt voor clientcommunicatie beschermen enkel de communicatie tussen de client en sommige sitesystemen. Ze beschermen niet het communicatiekanaal tussen de siteserver en sitesystemen of tussen siteservers.  

### <a name="communication-that-is-unencrypted-when-clients-use-https-communication"></a>Communicatie die niet versleuteld is wanneer clients HTTPS-communicatie gebruiken  
 Wanneer clients communiceren met sitesystemen met behulp van HTTPS, worden communicaties gewoonlijk versleuteld over SSL. In de volgende situaties communiceren clients echter met sitesystemen zonder het gebruik van versleuteling:  

-   Clients slagen er niet in een HTTPS-verbinding tot stand te brengen op het intranet en vallen terug op het gebruik van HTTP wanneer sitesystemen deze configuratie toestaan.  

-   Communicatie met de volgende sitesysteemrollen:  

    -   Client stuurt statusberichten naar het terugvalstatuspunt  

    -   Client stuurt PXE-aanvragen naar een distributiepunt met PXE-functionaliteit  

    -   Client stuurt meldinggegevens naar een beheerpunt  

 Reporting services-punten zijn geconfigureerd om HTTP of HTTPS te gebruiken onafhankelijk van de communicatiemodus van de client.  

##  <a name="cryptographic-controls-for-clients-chat-use-http-communication-to-site-systems"></a>Cryptografische besturingselementen voor clients chat HTTP-communicatie naar sitesystemen gebruiken  
 Wanneer clients HTTP-communicatie naar sitesysteemrollen gebruiken, kunnen ze PKI-certificaten gebruiken voor clientverificatie en zelfondertekende certificaten die Configuration Manager genereert. Wanneer Configuration Manager zelfondertekende certificaten genereert, hebben ze een aangepaste object-id voor ondertekening en versleuteling, en deze certificaten worden gebruikt als unieke identificatie van de client. Voor alle ondersteunde besturingssystemen behalve Windows Server 2003 gebruiken deze zelfondertekende certificaten SHA-256 en hebben ze een sleutellengte van 2048 bits. Voor Windows Server 2003 wordt SHA1 gebruikt met een sleutellengte van 1024 bits.  

### <a name="operating-system-deployment-and-self-signed-certificates"></a>Implementatie van besturingssysteem en zelfondertekende certificaten  
 Wanneer u Configuration Manager gebruikt om besturingssystemen met zelfondertekende certificaten te implementeren, moet een clientcomputer ook een certificaat om te communiceren met het beheerpunt hebben zelfs als de computer zich in een overgangsfase is zoals opstarten vanaf takenreeksmedia of een distributiepunt met PXE-functionaliteit. Om dit scenario de ondersteunen voor HTTP-clientverbindingen, genereert de Configuration Manager zelfondertekende certificaten die een aangepast object-id voor ondertekening en versleuteling, en deze certificaten worden gebruikt als unieke identificatie van de client. Voor alle ondersteunde besturingssystemen behalve Windows Server 2003 gebruiken deze zelfondertekende certificaten SHA-256 en hebben ze een sleutellengte van 2048 bits. Voor Windows Server 2003 wordt SHA1 gebruikt met een sleutellengte van 1024 bits. Als deze zelfondertekende certificaten verdacht zijn, blokkeer dan, om kwaadwillende personen te beletten om ze te gebruiken om vertrouwde clients te imiteren, de certificaten in het knooppunt **Certificaten** in de werkruimte **Beheer** , knooppunt **Veiligheid** .  

### <a name="client-and-server-authentication"></a>Client en server-verificatie  
 Wanneer clients verbinding via HTTP maken, verifiëren ze de beheerpunten door ofwel Active Directory Domain Services of met behulp van de vertrouwde basissleutel van Configuration Manager. Clients verifiëren geen andere systeemsite-functies, zoals statusmigratiepunten of software-updatepunten.  

 Indien een beheerpunt eerst een client verifieert door de zelfondertekende client-certificaten te gebruiken, voorziet dit mechanisme minimale veiligheid omdat elke computer zelfondertekende certificaten kan genereren. In dit scenario moet het client-identificatieproces versterkt worden door goedkeuring. Enkel vertrouwde computers moeten goedgekeurd worden, hetzij automatisch door Configuration Manager, hetzij handmatig, door een gebruiker met beheerdersrechten. Zie voor meer informatie, de goedkeuringssectie in [communicatie tussen eindpunten in System Center Configuration Manager](../../core/plan-design/hierarchy/communications-between-endpoints.md).  

##  <a name="about-ssl-vulnerabilities"></a>Over SSL-problemen  
 Het wordt aangeraden SSL 3.0 uit te schakelen, TLS 1.1, 1.2 en het vastleggen van aan TLS gerelateerde coderingssuites in te schakelen om de beveiliging van uw Configuration Manager-servers te verbeteren. In [KB-artikel](https://support.microsoft.com/en-us/kb/245030/)leert u hoe u deze maatregelen doorvoert. Deze maatregelen hebben geen invloed op de functionaliteit van de Configuration Manager.  

