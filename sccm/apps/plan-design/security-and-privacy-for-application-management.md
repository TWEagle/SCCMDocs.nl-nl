---
title: Beveiliging en privacy voor toepassingsbeheer | Microsoft-documenten
description: Beveiliging en privacy aanbevolen procedures voor Toepassingsbeheer in System Center Configuration Manager.
ms.custom: na
ms.date: 10/06/2016
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-app
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 4d26deed-3b16-4116-b640-f618f2c20f5a
caps.latest.revision: 8
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 521b90b9d497818a4c1e546fca38cd15d4cab487
ms.openlocfilehash: 6ee99fa0c07676f004e41a50bf16d0d17604e790
ms.contentlocale: nl-nl
ms.lasthandoff: 05/17/2017


---
# <a name="security-and-privacy-for-application-management-in-system-center-configuration-manager"></a>Beveiliging en privacy voor toepassingsbeheer in System Center Configuration Manager

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*


##  <a name="security-best-practices-for-application-management"></a>Aanbevolen beveiligingsprocedures voor toepassingsbeheer  

|Aanbevolen beveiligingsprocedure|Meer informatie|  
|----------------------------|----------------------|  
|Configureer de Application Catalog-punten om HTTPS-verbindingen te gebruiken en informeer gebruikers inzake de gevaren van schadelijke websites.|Configureer de Application Catalog-websitepunt en de Application Catalog-webservicepunt om HTTPS-verbindingen te aanvaarden zodat de server geverifieerd is voor gebruikers en de gegevens die overgedragen worden beveiligd zijn tegen knoeien en weergave. Voorkom aanvallen van sociale technieken door de gebruikers te leren dat ze enkel verbinding moeten maken met vertrouwde websites.<br /><br /> Gebruik niet de huisstijl configuratieopties die de naam van uw organisatie in de Application Catalog als identiteitsbewijs, weergeven wanneer u HTTPS niet gebruikt.|  
|Gebruik functiescheiding en installeer het Application Catalog-websitepunt en het Application Catalog-servicepunt op verschillende servers.|Als het Application Catalog-websitepunt is geknoeid, kunt u deze op een afzonderlijke server van het Application Catalog-websitepunt installeren. Dit helpt om de Configuration Manager-clients en de Configuration Manager-infrastructuur te beveiligen. Dit is vooral belangrijk als het Application Catalog-websitepunt clientverbindingen van het internet aanvaardt, want deze configuratie maakt de server kwetsbaar voor aanvallen.|  
|Leer gebruikers om het browservenster te sluiten wanneer ze klaar zijn met het gebruik van de Application Catalog.|Als gebruikers naar een externe website bladeren in hetzelfde browservenster dat ze gebruikten voor de Application Catalog, dan blijft de browser de beveiligingsinstellingen gebruiken die geschikt zijn voor vertrouwde sites in het intranet.|  
|Geef handmatig de gebruikersaffiniteit van apparaten in plaats van dat gebruikers hun primaire apparaat te identificeren. Geen op gebruik gebaseerde configuratie inschakelen.|Beschouw de informatie die verzameld wordt van gebruikers of van het apparaat niet als gezaghebbend. Als u software implementeert met behulp van de gebruikersaffiniteit apparaat die niet door een vertrouwde gebruiker met beheerdersrechten is opgegeven, is het mogelijk dat er software wordt geïnstalleerd op computers en naar gebruikers die geen machtigingen hebben om die software te ontvangen.|  
|Configureer altijd dat implementaties inhoud downloaden vanaf distributiepunten, in plaats van uitvoeren vanaf distributiepunten.|Wanneer u implementaties om inhoud te downloaden vanaf een distributiepunt configureren en lokaal, uitvoeren van de Configuration Manager controleert client de pakket-hash na het downloaden van de inhoud. Als de hash komt niet overeen met de hash in het beleid, verwijdert de client het pakket. Ter vergelijking: als u de implementatie uitgevoerd rechtstreeks vanaf een distributiepunt configureert de Configuration Manager-client controleert niet of de pakket-hash, wat betekent dat de Configuration Manager client software kan installeren waar is geknoeid.<br /><br /> Als u implementaties rechtstreeks vanaf distributiepunten uitvoeren moet, gebruikt machtigingen voor NFS op de pakketten op de distributiepunten en gebruikt u IP-beveiligingsbeleid (IPsec) om het kanaal tussen de client en de distributiepunten en tussen de distributiepunten en de siteserver te beveiligen.|  
|Kunnen niet communiceren met programma's als gebruikers de **uitvoeren met beheerdersrechten** optie is vereist.|Wanneer u een programma configureert, kunt u instellen de **gebruikers toestaan om te communiceren met dit programma** optie zodat gebruikers op alle vereiste prompts in de gebruikersinterface kunnen reageren. Als het programma ook is geconfigureerd voor **Uitvoeren met beheerdersrechten**, zou een kwaadwillende persoon op de computer die het programma uitvoert de gebruikersinterface kunnen gebruiken om privileges te escaleren op de clientcomputer.<br /><br /> Gebruik programma's die gebruikmaken van Windows Installer voor setup en per gebruiker verhoogde bevoegdheden voor software-implementaties die beheerdersreferenties vereisen. Setup moet worden uitgevoerd in de context van een gebruiker die geen beheerdersreferenties. Windows Installer met per gebruiker verhoogde bevoegdheden de veiligste manier om toepassingen met deze vereiste te implementeren.|  
|Beperk of gebruikers interactief software kunnen installeren met behulp van de clientinstelling **Installatiemachtigingen** .|Configureer de **Computeragent** clientapparaat **Installatiemachtigingen** instelling om te beperken welke gebruikers software installeren kunnen met behulp van de Application Catalog of Software Center. Maak bijvoorbeeld een aangepaste clientinstelling met **Installatiemachtigingen** ingesteld op **Alleen beheerders**. Vervolgens kunt toepassen apparaatclientinstelling op een verzameling servers om te voorkomen dat gebruikers zonder beheerdersrechten software op deze computers installeren.|  
|Implementeer voor mobiele apparaten alleen toepassingen die zijn ondertekend.|Implementeer mobiele apparaten enkel als de code is ondertekend door een certificeringsinstantie (CA) die wordt vertrouwd door het mobiele apparaat. Bijvoorbeeld:<br /><br /><ul><li>Een applicatie van een leverancier, ondertekend door een bekende Certificaatsinstantie, zoals VeriSign.</li><li>Een interne applicatie die u onafhankelijk van Configuration Manager ondertekent met behulp van uw interne Certificeringsinstantie.</li><li>Een interne applicatie die u ondertekent met behulp van Configuration Manager wanneer u het toepassingstype maakt en een handtekeningcertificaat gebruikt.</li></ul>|  
|Als u toepassingen voor mobiele apparaten met behulp van ondertekent de **Wizard toepassing maken** in Configuration Manager, Beveilig de locatie van het handtekeningcertificaatbestand en Beveilig het communicatiekanaal.|Ter beveiliging tegen verhoging van bevoegdheden en tegen man-in-the-middle-aanvallen, het handtekeningcertificaatbestand opslaan in een beveiligde map en IPsec of Server Message Block (SMB) tussen de volgende computers:<br /><br /><ul><li>De computer waarop de Configuration Manager-console</li><li>De computer waarop het handtekeningcertificaatbestand wordt opgeslagen</li><li>De computer die de toepassingsbronbestanden opslaat</li></ul> Ondertekenen ook de toepassing onafhankelijk van Configuration Manager voordat u de **Wizard toepassing maken**.|  
|Toegangsbeheer implementeren om referentiecomputers te beveiligen.|Wanneer een gebruiker met beheerdersrechten de detectiemethode in een implementatietype configureert door te bladeren naar een referentiecomputer, moet u er zeker van zijn dat de computer niet is aangetast.|  
|Beperk en controleer gebruikers met beheerdersrechten waaraan op rollen gebaseerde beveiligingsrollen wordt verleend die verband houden met toepassingsbeheer:<br /><br /><ul><li>**Toepassingsbeheerder**</li><li>**Toepassingsauteur**</li><li> **Beheerder Toepassingsimplementaties**</li></ul>|Zelfs wanneer u op rollen gebaseerd beheer configureert, is het mogelijk dat gebruikers met beheerdersrechten die toepassingen maken en implementeren meer machtigingen hebben dan u beseft. Gebruikers met beheerdersrechten die maken of wijzigen van een toepassing kunnen bijvoorbeeld selecteren dat afhankelijke toepassingen die niet onder het beveiligingsbereik vallen.|  
|Als u virtuele omgevingen Microsoft Application Virtualization (App-V) configureert, selecteert u toepassingen met hetzelfde vertrouwensniveau in de virtuele omgeving.|Omdat toepassingen in een App-V virtuele omgeving bronnen delen kunnen, zoals het Klembord, configureer de virtuele omgeving zodat de geselecteerde toepassingen hetzelfde vertrouwensniveau hebben.<br /><br /> Zie voor meer informatie [virtuele omgevingen van App-V maken](../../apps/deploy-use/create-app-v-virtual-environments.md).|  
|Zorg ervoor dat de bronbestanden afkomstig zijn van een betrouwbare bron als u toepassingen implementeert voor Mac-computers.|Het hulpprogramma CMAppUtil valideert de handtekening van het bronpakket niet, zorg daarom dat het afkomstig is van een bron die u vertrouwt. Het hulpprogramma CMAppUtil kan niet detecteren of de bestanden is geknoeid.|  
|Als u toepassingen voor Mac-computers implementeert, Beveilig de locatie van de **cmmac** bestand en Beveilig het communicatiekanaal wanneer u dit bestand naar Configuration Manager importeren.|De **cmmac** bestand dat het hulpprogramma CMAppUtil genereert en dat u importeert naar Configuration Manager is niet ondertekend of gevalideerd. Ter voorkoming van knoeien met dit bestand op te slaan in een beveiligde map en IPsec of SMB tussen de volgende computers gebruiken:<br /><br /><ul><li>De computer waarop de Configuration Manager-console</li><li>De computer die slaat de **cmmac** bestand</li></ul>.|  
|Als u een implementatietype voor webtoepassing configureert, gebruikt u HTTPS in plaats van HTTP voor een beveiligde verbinding.|Als u een webtoepassing implementeert met behulp van een HTTP-koppeling in plaats van een HTTPS-koppeling, kan het apparaat worden doorgestuurd naar een rogue server en kan worden geknoeid met gegevens die worden overgebracht tussen het apparaat en de server.|  

##  <a name="security-issues-for-application-management"></a>Beveiligingsproblemen voor toepassingsbeheer  

-   Gebruikers met beperkte rechten kunnen bestanden van de clientcache naar de clientcomputer kopiëren .  

     Gebruikers kunnen de clientcache lezen, maar niet op schrijven. Met leesmachtigingen kan een gebruiker toepassingsinstallatiebestanden van een computer naar een andere computer kopiëren.  

-   Gebruikers met beperkte rechten kunnen bestanden die de geschiedenis van software-implementatie op de clientcomputer wijzigen.  

     De informatie van toepassingsgeschiedenis is niet beveiligd, kan een gebruiker bestanden waarin wordt aangegeven of een toepassing is geïnstalleerd kunt wijzigen.  

-   App-V-pakketten zijn niet ondertekend.  

     App-V-pakketten in Configuration Manager ondersteunen geen ondertekening om te controleren dat de inhoud van een vertrouwde bron is en dat die niet in overdracht zijn gewijzigd. Er is geen beperking op dit beveiligingsprobleem. Zorg ervoor dat u de beveiliging wordt aangeraden de inhoud te downloaden van een vertrouwde bron en van een veilige locatie volgen.  

-   Gepubliceerde App-V-toepassingen kunnen door alle gebruikers op de computer worden geïnstalleerd.  

     Als een App-V-toepassing op een computer is gepubliceerd, kunnen alle gebruikers die zich op deze computer aanmelden de toepassing installeren. Dit betekent dat u de gebruikers de toepassingen installeren kunnen na de publicatie niet beperken.  

-   U kunt Installatiemachtigingen voor de bedrijfsportal niet beperken.  

     Installatiemachtigingen kunt u een client-instelling om te beperken, bijvoorbeeld tot primaire gebruikers van een apparaat of tot lokale beheerders enkel, werkt deze instelling niet voor de bedrijfsportal. Dit kan leiden tot verhoging van bevoegdheden omdat gebruikers van een app die niet worden mogen installeren kunnen installeren.  

##  <a name="BKMK_CertificatesSilverlight5"></a>Certificaten voor Microsoft Silverlight 5 en verhoogde vertrouwensmodus vereist voor de application catalog  
 Configuration Manager-clients vereisen Microsoft Silverlight 5, die moet worden uitgevoerd in verhoogde vertrouwensmodus voor gebruikers om software te installeren uit de Application Catalog. Silverlight-toepassingen worden standaard uitgevoerd in gedeeltelijke vertrouwensmodus om te voorkomen dat toepassingen toegang hebben tot gebruikersgegevens. Configuration Manager installeert automatisch Microsoft Silverlight 5 op clients, als dit nog niet is geïnstalleerd. Configuration Manager wordt standaard ingesteld van de Computer Agent **toestaan dat Silverlight-toepassingen worden uitgevoerd in verhoogde vertrouwensmodus** clientinstelling voor **Ja**. Deze instelling kunt ondertekende en vertrouwde Silverlight-toepassingen aanvraag verhoogde vertrouwensmodus.  

 Wanneer u de sitesysteemrol van Application Catalog-website-punt installeert, installeert de client eveneens een Microsoft-handtekeningcertificaat in het certificaatarchief van vertrouwde uitgevers computer op elke clientcomputer Configuration Manager. Dit certificaat kan Silverlight-toepassingen die zijn ondertekend met dit certificaat worden uitgevoerd in de verhoogde vertrouwensmodus die de computers vereisen om software te installeren uit de Application Catalog. Configuration Manager beheert automatisch dit handtekeningcertificaat. Dit Microsoft-handtekeningcertificaat niet handmatig verwijderen of verplaatsen om te zorgen voor de continuïteit van de service.  

> [!WARNING]  
>  Wanneer dit is ingeschakeld, de **toestaan dat Silverlight-toepassingen worden uitgevoerd in verhoogde vertrouwensmodus** client instelling kiest, kunnen alle Silverlight-toepassingen die zijn ondertekend door certificaten in het certificaat van vertrouwde uitgevers in het computerarchief of gebruikersarchief opslaan in verhoogde vertrouwensmodus uitgevoerd. De clientinstelling kan verhoogde vertrouwensmodus niet inschakelen specifiek is voor de Configuration Manager Application Catalog of voor het certificaatarchief Vertrouwde uitgevers in het computerarchief. Als malware een rogue certificaat toevoegt aan het Vertrouwde uitgeversarchief, bijvoorbeeld in het gebruikersarchief, kan malware met eigen Silverlight-toepassing nu ook in verhoogde vertrouwensmodus uitgevoerd worden.  

 Als u de **toestaan dat Silverlight-toepassingen worden uitgevoerd in verhoogde vertrouwensmodus** clientinstelling voor **Nee**, wordt de Microsoft-handtekeningcertificaat niet van clients verwijderd.  

 Zie voor meer informatie inzake vertrouwde toepassingen in Silverlight [vertrouwde toepassingen](http://go.microsoft.com/fwlink/p/?LinkId=252842).  

##  <a name="privacy-information-for-application-management"></a>Privacyinformatie voor toepassingsbeheer  
 Toepassingsbeheer kunt u een toepassing, programma of script uitvoeren op elke clientcomputer of client mobiel apparaat in de hiërarchie. Configuration Manager heeft geen controle over de typen toepassingen, programma's of scripts die u uitvoert of het type informatie die deze overdragen. Configuration Manager kan gegevens voor identificatie van het apparaat en de e-mailaccounts tussen clients en servers verzenden tijdens de implementatie van toepassing.  

 Configuration Manager houdt de statusinformatie over de software-implementatieproces. De statusinformatie van de software-implementatie wordt tijdens de verzending niet versleuteld, tenzij de client via HTTPS communiceert. De statusinformatie wordt niet in een versleutelde vorm opgeslagen in de database.  

 Het gebruik van Configuration Manager installatie om de toepassingsinstallatie op afstand, interactief of op de achtergrond op clients mogelijk onderworpen aan softwarelicentievoorwaarden voor die software. Deze toepassing is gescheiden van de gebruiksrechtovereenkomst voor System Center Configuration Manager. Controleer altijd of u de licentievoorwaarden accepteren voordat u software implementeert met behulp van Configuration Manager.  

 Toepassingsimplementatie vindt niet standaard plaats en vereist verschillende configuratiestappen.  

 De twee optionele functies die een hulpmiddel zijn voor een efficiënte software-implementatie zijn apparaataffiniteit van gebruikers en de toepassingscatalogus:  

-   Apparaataffiniteit van gebruikers wijst een gebruiker toe aan apparaten, zodat een Configuration Manager-beheerder software voor een gebruiker implementeren kunt en de software wordt automatisch geïnstalleerd op een of meer computers die de gebruiker het meest gebruikt.  

-   De Toepassingscatalogus is een website waarmee gebruikers aanvraag software te installeren.  

 Bekijk de volgende secties voor privacyinformatie over apparaataffiniteit van gebruikers en de toepassingscatalogus.  

 Bedenk wat uw privacyvereisten zijn voordat u toepassingsbeheer configureert.  

##  <a name="user-device-affinity"></a>Gebruikersaffiniteit apparaat  
-  Configuration Manager kan informatie verzenden tussen clients en beheerpuntsitesystemen. De informatie kan account voor de computer en aanmelden en het samengevatte gebruik van e-mailaccounts identificeren.  
-  De informatie die wordt verzonden tussen de client en server is niet versleuteld, tenzij het beheerpunt is geconfigureerd om clients te communiceren via HTTPS.  
-  De computer en meld u gebruiksgegevens dat wordt gebruikt voor een gebruiker toewijzen aan een apparaat is opgeslagen op clientcomputers, verzonden naar beheerpunten en vervolgens opgeslagen in de Configuration Manager-database. De oude informatie wordt standaard na 90 dagen van de database verwijderd. U kunt het verwijderingsgedrag configureren door de siteonderhoudstaak **Verouderde gegevens apparaataffiniteit voor gebruikers verwijderen** in te stellen.
-  Configuration Manager houdt de statusinformatie over apparaataffiniteit van gebruikers. De statusinformatie is tijdens de verzending niet versleuteld, tenzij client zijn geconfigureerd om via HTTPS met beheerpunten te communiceren. De statusinformatie wordt niet in een versleutelde vorm opgeslagen in de database.  
-  Computer, informatie over het gebruik van de aanmeldingsaccount en statusinformatie worden niet naar Microsoft verzonden.  
-  Computer en meld u informatie over het gebruik dat wordt gebruikt voor het tot stand brengen affiniteit tussen gebruiker en apparaat is altijd ingeschakeld. Bovendien kunnen gebruikers en gebruikers met beheerdersrechten voorzien in informatie over apparaataffiniteit van gebruikers.  

##  <a name="application-catalog"></a>Application Catalog  
-  De Application Catalog kunnen de Configuration Manager-beheerder publiceren van toepassingen of programma of script voor gebruikers om uit te voeren. Configuration Manager heeft geen controle over de typen van programma's of scripts die in de catalogus worden gepubliceerd of het type informatie die deze overdragen.    
-  Configuration Manager kan informatie verzenden tussen clients en de Application Catalog-sitesysteemrollen. De informatie kan de computer en aanmelding identificeren. De informatie die tussen de client en server wordt verzonden, is niet versleuteld, tenzij deze sitesysteemrollen worden geconfigureerd om clients verplicht verbinding te laten maken via HTTPS.  
-  De informatie over de goedkeuringsaanvraag voor toepassingen wordt opgeslagen in de Configuration Manager-database. Aanvragen die zijn geannuleerd of geweigerd en de daarmee samenhangende geschiedenisvermeldingen worden standaard na 30 dagen verwijderd. U kunt het verwijderingsgedrag configureren door de siteonderhoudstaak **Verouderde gegevens toepassingsaanvraag verwijderen** in te stellen. Goedkeuringsaanvragen voor toepassingen die zijn goedgekeurd en in behandeling hebben, worden nooit verwijderd.  
-  Informatie die is verzonden van of naar de toepassingscatalogus wordt niet naar Microsoft verzonden.  
-  De toepassingscatalogus is niet standaard geïnstalleerd. Deze installatie vereist verschillende configuratiestappen.  

