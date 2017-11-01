---
title: Beveiliging en privacy voor toepassingsbeheer
titleSuffix: Configuration Manager
description: Beveiliging en privacy aanbevolen procedures voor Toepassingsbeheer in System Center Configuration Manager.
ms.custom: na
ms.date: 10/06/2016
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: configmgr-app
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 4d26deed-3b16-4116-b640-f618f2c20f5a
caps.latest.revision: "8"
author: mattbriggs
ms.author: mabrigg
manager: angrobe
ms.openlocfilehash: 7ca91443af58fc342380b819ca53e42b75556090
ms.sourcegitcommit: c236214b2fcc13dae7bad96d7fb33f692868191d
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/12/2017
---
# <a name="security-and-privacy-for-application-management-in-system-center-configuration-manager"></a>Beveiliging en privacy voor toepassingsbeheer in System Center Configuration Manager

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*


##  <a name="security-best-practices-for-application-management"></a>Aanbevolen beveiligingsprocedures voor toepassingsbeheer  

|Aanbevolen beveiligingsprocedure|Meer informatie|  
|----------------------------|----------------------|  
|Configureer de Application Catalog-punten om HTTPS-verbindingen te gebruiken en informeer gebruikers inzake de gevaren van schadelijke websites.|Configureer de Application Catalog-websitepunt en de Application Catalog-webservicepunt om HTTPS-verbindingen te aanvaarden zodat de server geverifieerd is voor gebruikers en de gegevens die overgedragen worden beveiligd zijn tegen knoeien en weergave. Voorkom aanvallen van sociale technieken door de gebruikers te leren dat ze enkel verbinding moeten maken met vertrouwde websites.<br /><br /> Gebruik niet de huisstijl van de configuratieopties die de naam van uw organisatie in de Application Catalog als identiteitsbewijs, weergeven wanneer u HTTPS niet gebruikt.|  
|Gebruik functiescheiding en installeer het Application Catalog-websitepunt en het Application Catalog-servicepunt op verschillende servers.|Als de Application Catalog-websitepunt is geknoeid, kunt u deze op een afzonderlijke server van het Application Catalog-webservicepunt installeren. Dit helpt om de Configuration Manager-clients en de Configuration Manager-infrastructuur te beveiligen. Dit is vooral belangrijk als het Application Catalog-websitepunt clientverbindingen van het internet aanvaardt, want deze configuratie maakt de server kwetsbaar voor aanvallen.|  
|Leer gebruikers om het browservenster te sluiten wanneer ze klaar zijn met het gebruik van de Application Catalog.|Als gebruikers naar een externe website bladeren in hetzelfde browservenster dat ze gebruikten voor de Application Catalog, dan blijft de browser de beveiligingsinstellingen gebruiken die geschikt zijn voor vertrouwde sites in het intranet.|  
|Geef handmatig de gebruikersaffiniteit van apparaten in plaats van zodat gebruikers hun primaire apparaat te identificeren. Toch op gebruik gebaseerde configuratie niet inschakelt.|Beschouw de informatie die verzameld wordt van gebruikers of van het apparaat niet als gezaghebbend. Als u software implementeert met behulp van de gebruikersaffiniteit apparaat die niet door een vertrouwde gebruiker met beheerdersrechten is opgegeven, is het mogelijk dat er software wordt geïnstalleerd op computers en naar gebruikers die geen machtigingen hebben om die software te ontvangen.|  
|Configureer altijd dat implementaties inhoud downloaden vanaf distributiepunten, in plaats van uitvoeren vanaf distributiepunten.|Wanneer u implementaties om inhoud te downloaden vanaf een distributiepunt configureert en lokaal uitvoeren van de Configuration Manager client controleert of de pakket-hash na het downloaden van de inhoud. De client wordt het pakket verwijderd als de hash komt niet overeen met de hash in het beleid. Ter vergelijking: als u de implementatie om uit te voeren rechtstreeks vanaf een distributiepunt configureert Configuration Manager-client controleert niet of de pakket-hash, wat betekent dat de Configuration Manager client software kan installeren waar is geknoeid.<br /><br /> Als u implementaties rechtstreeks vanaf distributiepunten uitvoeren moet, gebruikt u NTFS minimale machtigingen op de pakketten op de distributiepunten en het gebruik Internet protocol security (IPsec) het kanaal tussen de client en de distributiepunten en tussen de distributiepunten en de siteserver te beveiligen.|  
|Kunnen niet communiceren met programma's als gebruikers de **uitvoeren met beheerdersrechten** optie is vereist.|Wanneer u een programma configureert, kunt u instellen de **gebruikers kunnen communiceren met dit programma** optie zodat gebruikers op de vereiste prompts in de gebruikersinterface kunnen reageren. Als het programma ook is geconfigureerd voor **Uitvoeren met beheerdersrechten**, zou een kwaadwillende persoon op de computer die het programma uitvoert de gebruikersinterface kunnen gebruiken om privileges te escaleren op de clientcomputer.<br /><br /> Gebruik programma's die gebruikmaken van Windows Installer voor installatie en per gebruiker verhoogde bevoegdheden voor software-implementaties die beheerdersreferenties vereisen. Het installatieprogramma moet worden uitgevoerd in de context van een gebruiker die geen beheerdersreferenties hebben. Windows Installer met per gebruiker verhoogde bevoegdheden bieden de veiligste manier om toepassingen met deze vereiste te implementeren.|  
|Beperk of gebruikers interactief software kunnen installeren met behulp van de clientinstelling **Installatiemachtigingen** .|Configureer de **Computeragent** clientapparaat **Installatiemachtigingen** instelling om te beperken welke gebruikers software installeren kunnen met behulp van de Application Catalog of Software Center. Maak bijvoorbeeld een aangepaste clientinstelling met **Installatiemachtigingen** ingesteld op **Alleen beheerders**. Vervolgens passen deze clientinstelling instelt op een verzameling van servers om te voorkomen dat gebruikers zonder beheerdersrechten software op deze computers installeren.|  
|Implementeer voor mobiele apparaten alleen toepassingen die zijn ondertekend.|Implementeer toepassingen voor mobiele apparaten alleen als deze code is ondertekend door een certificeringsinstantie (CA) die wordt vertrouwd door het mobiele apparaat. Bijvoorbeeld:<br /><br /><ul><li>Een toepassing van een leverancier, ondertekend met een bekende Certificaatsinstantie, zoals VeriSign.</li><li>Een interne applicatie die u onafhankelijk van Configuration Manager ondertekent met behulp van uw interne Certificeringsinstantie.</li><li>Een interne applicatie die u ondertekent met behulp van Configuration Manager wanneer u het toepassingstype maakt en een handtekeningcertificaat gebruikt.</li></ul>|  
|Als u toepassingen voor mobiele apparaten met behulp van ondertekent de **Wizard toepassing maken** in Configuration Manager, Beveilig de locatie van het handtekeningcertificaatbestand en Beveilig het communicatiekanaal.|Om te beschermen tegen verhoging van bevoegdheden en tegen man-in-the-middle-aanvallen, het handtekeningcertificaatbestand opslaan in een beveiligde map en IPsec of Server Message Block (SMB) tussen de volgende computers:<br /><br /><ul><li>De computer waarop de Configuration Manager-console</li><li>De computer waarop het handtekeningcertificaatbestand wordt opgeslagen</li><li>De computer die de toepassingsbronbestanden opslaat</li></ul> U kunt ook Meld u aan de toepassing onafhankelijk van Configuration Manager voordat u uitvoert het **Wizard toepassing maken**.|  
|Toegangsbeheer implementeren om referentiecomputers te beveiligen.|Wanneer een gebruiker met beheerdersrechten de detectiemethode in een implementatietype configureert door te bladeren naar een referentiecomputer, moet u er zeker van zijn dat de computer niet is aangetast.|  
|Beperk en controleer gebruikers met beheerdersrechten waaraan op rollen gebaseerde beveiligingsrollen wordt verleend die verband houden met toepassingsbeheer:<br /><br /><ul><li>**Toepassingsbeheerder**</li><li>**Toepassingsauteur**</li><li> **Beheerder Toepassingsimplementaties**</li></ul>|Zelfs wanneer u op rollen gebaseerd beheer configureert, is het mogelijk dat gebruikers met beheerdersrechten die toepassingen maken en implementeren meer machtigingen hebben dan u beseft. Gebruikers met beheerdersrechten die maken of wijzigen van een toepassing kunnen bijvoorbeeld selecteren dat afhankelijke toepassingen die zich niet in het beveiligingsbereik vallen.|  
|Als u virtuele omgevingen van Microsoft Application Virtualization (App-V) configureert, selecteert u toepassingen met hetzelfde vertrouwensniveau in de virtuele omgeving.|Omdat toepassingen in een virtuele App-V-omgeving bronnen delen kunnen, zoals het Klembord, de virtuele omgeving zodanig configureren dat de geselecteerde toepassingen hetzelfde vertrouwensniveau hebben.<br /><br /> Zie voor meer informatie [maken van App-V virtuele omgevingen](../../apps/deploy-use/create-app-v-virtual-environments.md).|  
|Zorg ervoor dat de bronbestanden afkomstig zijn van een betrouwbare bron als u toepassingen implementeert voor Mac-computers.|Het hulpprogramma CMAppUtil valideert de handtekening van het bronpakket niet, zorg daarom dat het afkomstig is van een bron die u vertrouwt. Het hulpprogramma cmapputil kan niet detecteren of de bestanden zijn gemanipuleerd.|  
|Als u toepassingen voor Mac-computers implementeert, Beveilig de locatie van de **cmmac** bestand en Beveilig het communicatiekanaal wanneer u dit bestand naar Configuration Manager importeren.|De **cmmac** bestand dat het hulpprogramma cmapputil genereert en dat u importeert naar Configuration Manager is niet ondertekend of gevalideerd. Ter voorkoming van knoeien met dit bestand opslaan in een beveiligde map en gebruikt u IPsec of SMB tussen de volgende computers:<br /><br /><ul><li>De computer waarop de Configuration Manager-console</li><li>De computer die slaat de **cmmac** bestand</li></ul>.|  
|Als u een implementatietype voor web-toepassing configureert, gebruikt u HTTPS in plaats van HTTP voor het beveiligen van de verbinding.|Als u een webtoepassing implementeert met behulp van een HTTP-koppeling in plaats van een HTTPS-koppeling, wordt het apparaat kan worden omgeleid naar een rogue server en gegevens die worden overgedragen tussen het apparaat en de server kan worden geknoeid met.|  

##  <a name="security-issues-for-application-management"></a>Beveiligingsproblemen voor toepassingsbeheer  

-   Gebruikers met beperkte rechten kunnen bestanden van de clientcache naar de clientcomputer kopiëren .  

     Gebruikers kunnen de clientcache lezen, maar niet op schrijven. Met leesmachtigingen kan een gebruiker toepassingsinstallatiebestanden van een computer naar een andere computer kopiëren.  

-   Gebruikers met beperkte rechten kunnen bestanden die de geschiedenis van de software-implementatie op de clientcomputer opnemen wijzigen.  

     Omdat de informatie van toepassingsgeschiedenis is niet beveiligd, kan bestanden die rapporteren of een toepassing wordt geïnstalleerd door een gebruiker wijzigen.  

-   App-V-pakketten zijn niet ondertekend.  

     App-V-pakketten in Configuration Manager ondersteunen geen ondertekening om te controleren dat de inhoud van een vertrouwde bron afkomstig is en dat die niet is gewijzigd tijdens de overdracht. Er is geen beperking voor dit beveiligingsprobleem. Zorg ervoor dat u volgt de aanbevolen beveiligingsprocedure de inhoud te downloaden vanaf een vertrouwde bron en vanaf een veilige locatie.  

-   Gepubliceerde App-V-toepassingen kunnen door alle gebruikers op de computer worden geïnstalleerd.  

     Wanneer een App-V-toepassing wordt gepubliceerd op een computer, kunnen alle gebruikers die zich aanmeldt bij de computer die de toepassing te installeren. Dit betekent dat u de gebruikers die de toepassing installeren kunnen na de publicatie niet beperken.  

-   U kunt Installatiemachtigingen voor de bedrijfsportal niet beperken.  

     Hoewel u een client-instelling om te beperken kunt configureren Installatiemachtigingen, bijvoorbeeld tot primaire gebruikers van een apparaat of tot lokale beheerders enkel, deze instelling werkt niet voor de bedrijfsportal. Dit kan leiden tot een verhoging van bevoegdheden omdat gebruikers kunnen installeren van een app die zij niet mogen installeren.  

##  <a name="BKMK_CertificatesSilverlight5"></a>Certificaten voor Microsoft Silverlight 5 en verhoogde vertrouwensmodus vereist voor de application catalog  
 Configuration Manager-clients vereisen Microsoft Silverlight 5, die moet worden uitgevoerd in verhoogde vertrouwensmodus voor gebruikers om software te installeren uit de Application Catalog. Silverlight-toepassingen worden standaard uitgevoerd in gedeeltelijke vertrouwensmodus om te voorkomen dat toepassingen toegang hebben tot gebruikersgegevens. Configuration Manager installeert automatisch Microsoft Silverlight 5 op clients, als deze nog niet is geïnstalleerd. Configuration Manager wordt standaard ingesteld van de Computer Agent **toestaan dat Silverlight-toepassingen worden uitgevoerd in verhoogde vertrouwensmodus** clientinstelling instelt op **Ja**. Deze instelling kunt ondertekende en vertrouwde Silverlight-toepassingen aanvraag verhoogde vertrouwensmodus.  

 Wanneer u de sitesysteemrol van Application Catalog-website-punt installeert, installeert de client eveneens een Microsoft-handtekeningcertificaat in het certificaatarchief van vertrouwde uitgevers computer op elke clientcomputer Configuration Manager. Dit certificaat kan Silverlight-toepassingen die zijn ondertekend door dit certificaat worden uitgevoerd in de verhoogde vertrouwensmodus die de computers vereisen om software te installeren uit de Application Catalog. Configuration Manager beheert automatisch dit handtekeningcertificaat. Dit Microsoft-handtekeningcertificaat niet handmatig verwijderen of verplaatsen om te zorgen voor de continuïteit van de service.  

> [!WARNING]  
>  Wanneer dit is ingeschakeld, de **toestaan dat Silverlight-toepassingen worden uitgevoerd in verhoogde vertrouwensmodus** client-instelling kiest, kunnen alle Silverlight-toepassingen die zijn ondertekend door certificaten in het certificaat vertrouwde uitgevers opslaan in het computerarchief of gebruikersarchief uitgevoerd in verhoogde vertrouwensmodus. De clientinstelling kan verhoogde vertrouwensmodus niet inschakelen, specifiek voor de Configuration Manager Application Catalog of voor het certificaatarchief Vertrouwde uitgevers in het computerarchief. Als malware een rogue certificaat toevoegt aan het Vertrouwde uitgeversarchief, bijvoorbeeld in het gebruikersarchief, kan malware met eigen Silverlight-toepassing nu ook in verhoogde vertrouwensmodus uitgevoerd worden.  

 Als u de **toestaan dat Silverlight-toepassingen worden uitgevoerd in verhoogde vertrouwensmodus** clientinstelling instelt op **Nee**, wordt de Microsoft-handtekeningcertificaat niet van clients verwijderd.  

 Zie voor meer informatie inzake vertrouwde toepassingen in Silverlight [vertrouwde toepassingen](http://go.microsoft.com/fwlink/p/?LinkId=252842).  

##  <a name="privacy-information-for-application-management"></a>Privacy-informatie voor toepassingsbeheer  
 Toepassingsbeheer kunt u een toepassing, programma of script uitvoeren op elke clientcomputer of client mobiel apparaat in de hiërarchie. Configuration Manager heeft geen controle over de typen toepassingen, programma's of scripts die u uitvoert of het type informatie die ze verzenden. Configuration Manager kan informatie over het apparaat en het e-mailaccounts tussen clients en servers verzenden tijdens de implementatie van toepassing.  

 Configuration Manager houdt de statusinformatie over de software-implementatieproces. De statusinformatie van de software-implementatie wordt tijdens de verzending niet versleuteld, tenzij de client via HTTPS communiceert. De statusinformatie wordt niet in een versleutelde vorm opgeslagen in de database.  

 Het gebruik van de installatie van de toepassing Configuration Manager op afstand, interactief of op de achtergrond om software te installeren op clients mogelijk onderworpen aan softwarelicentievoorwaarden voor die software. Dit is gescheiden van de gebruiksrechtovereenkomst voor System Center Configuration Manager. Controleer altijd of met de licentievoorwaarden voor Software kunt instemmen voor u software implementeert met behulp van Configuration Manager.  

 Toepassingsimplementatie gebeurt niet standaard en vereist verschillende configuratiestappen.  

 De twee optionele functies die een hulpmiddel zijn voor een efficiënte software-implementatie zijn apparaataffiniteit van gebruikers en de toepassingscatalogus:  

-   Apparaataffiniteit van gebruikers wijst een gebruiker op apparaten, zodat een Configuration Manager-beheerder software op een gebruiker implementeren kan en de software wordt automatisch geïnstalleerd op een of meer computers waarop de gebruiker het meest gebruikt.  

-   De Application Catalog is een website waarmee gebruikers aanvraag software te installeren.  

 Bekijk de volgende secties voor privacyinformatie over apparaataffiniteit van gebruikers en de toepassingscatalogus.  

 Bedenk wat uw privacyvereisten zijn voordat u toepassingsbeheer configureert.  

##  <a name="user-device-affinity"></a>Gebruikersaffiniteit apparaat  
-  Configuration Manager kan informatie verzenden tussen clients en beheerpuntsitesystemen. De gegevens mogelijk de computer en meld u account en het samengevatte gebruik van e-mailaccounts identificeren.  
-  De informatie die wordt verzonden tussen client en server is niet versleuteld, tenzij het beheerpunt is geconfigureerd dat clients kunnen communiceren via HTTPS.  
-  De computer en meld u gebruiksgegevens die wordt gebruikt voor een gebruiker toewijzen aan een apparaat is opgeslagen op clientcomputers, verzonden naar beheerpunten en vervolgens worden opgeslagen in de Configuration Manager-database. De oude informatie wordt standaard na 90 dagen van de database verwijderd. U kunt het verwijderingsgedrag configureren door de siteonderhoudstaak **Verouderde gegevens apparaataffiniteit voor gebruikers verwijderen** in te stellen.
-  Configuration Manager houdt de statusinformatie bij over apparaataffiniteit van gebruikers. De statusinformatie is tijdens de verzending niet versleuteld, tenzij client zijn geconfigureerd om via HTTPS met beheerpunten te communiceren. De statusinformatie wordt niet in een versleutelde vorm opgeslagen in de database.  
-  Computer, informatie over het gebruik van de aanmeldingsaccount en statusinformatie worden niet naar Microsoft verzonden.  
-  Computer en meld u informatie over het gebruik dat wordt gebruikt voor het tot stand brengen van affiniteit van gebruiker en apparaat is altijd ingeschakeld. Bovendien kunnen gebruikers en gebruikers met beheerdersrechten voorzien in informatie over apparaataffiniteit van gebruikers.  

##  <a name="application-catalog"></a>Application Catalog  
-  De Application Catalog kunt de Configuration Manager-beheerder voor het publiceren van toepassingen of programma of script voor gebruikers om uit te voeren. Configuration Manager heeft geen controle over de typen programma's of scripts die zijn gepubliceerd in de catalogus of het type informatie die ze verzenden.    
-  Configuration Manager kan informatie verzenden tussen clients en de Application Catalog-sitesysteemrollen. De gegevens mogelijk de computer en meld u accounts te identificeren. De informatie die tussen de client en server wordt verzonden, is niet versleuteld, tenzij deze sitesysteemrollen worden geconfigureerd om clients verplicht verbinding te laten maken via HTTPS.  
-  De informatie over de goedkeuringsaanvraag voor toepassingen wordt opgeslagen in de Configuration Manager-database. Aanvragen die worden geannuleerd of geweigerd en de daarmee samenhangende geschiedenisvermeldingen worden standaard na 30 dagen verwijderd. U kunt het verwijderingsgedrag configureren door de siteonderhoudstaak **Verouderde gegevens toepassingsaanvraag verwijderen** in te stellen. Goedkeuringsaanvragen voor toepassingen die zijn goedgekeurd en in in behandeling zijnde statussen worden nooit verwijderd.  
-  Informatie die is verzonden van of naar de toepassingscatalogus wordt niet naar Microsoft verzonden.  
-  De toepassingscatalogus is niet standaard geïnstalleerd. Deze installatie vereist verschillende configuratiestappen.  
