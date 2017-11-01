---
title: Plan voor de cloud-management-gateway
titleSuffix: Configuration Manager
description: 
ms.date: 10/06/2017
ms.prod: configuration-manager
ms.technology: configmgr-client
ms.assetid: 2dc8c9f1-4176-4e35-9794-f44b15f4e55f
author: arob98
ms.author: angrobe
manager: angrobe
ms.openlocfilehash: ffe7b2aa025b20d5b1d1a718e0eaa045817a66ee
ms.sourcegitcommit: c236214b2fcc13dae7bad96d7fb33f692868191d
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/12/2017
---
# <a name="plan-for-the-cloud-management-gateway-in-configuration-manager"></a>Plan voor de cloudgateway management in Configuration Manager

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*

Vanaf versie 1610, biedt cloudgateway management een eenvoudige manier voor het beheren van Configuration Manager-clients op Internet. De cloud management gateway-service wordt geïmplementeerd voor Microsoft Azure en een Azure-abonnement vereist. Deze verbinding maakt met uw on-premises Configuration Manager-infrastructuur met behulp van een nieuwe rol met de naam van het cloud-gateway connector beheerpunt. Eenmaal geïmplementeerd en geconfigureerd, worden clients toegang kunnen krijgen tot de lokale Configuration Manager sitesysteemrollen ongeacht of ze zich op de interne particuliere netwerk of op het Internet.

> [!TIP]  
> De cloud management gateway is geïntroduceerd in versie 1610, is een voorlopige versie-functie. Als u wilt inschakelen, Zie [functies van evaluatieversies van updates gebruiken](/sccm/core/servers/manage/pre-release-features).

Gebruik de Configuration Manager-console de service implementeren in Azure, het toevoegen van de cloud gateway connector beheerpuntrol en het configureren van sitesysteemrollen voor cloud management gateway-verkeer. Cloud management gateway ondersteunt momenteel alleen de punt en software-update-punt beheerrollen.

Clientcertificaten en Secure Socket Layer (SSL)-certificaten zijn vereist voor het verifiëren van computers en het versleutelen van communicatie tussen de verschillende lagen van de service. Clientcomputers ontvangen meestal een certificaat via Groepsbeleid worden afgedwongen. Voor het versleutelen van het verkeer tussen clients en de sitesysteemserver die als host fungeert voor de functies die u wilt maken van een aangepaste SSL-certificaat van de CA. U moet ook instellen van een beheercertificaat in Azure waarmee Configuration Manager voor het implementeren van de cloud management gateway-service.

## <a name="requirements-for-cloud-management-gateway"></a>Vereisten voor cloud-management-gateway

-   Clientcomputers en de sitesysteemserver die het cloud-gateway connector beheerpunt uitgevoerd.

-   Aangepaste SSL-certificaten van de interne CA - gebruikt voor het versleutelen van communicatie van de clientcomputers en de identiteit van de cloud management gateway-service verifiëren.

-   Azure-abonnement voor cloudservices.

-   Azure-beheercertificaat - gebruikt voor het verifiëren van Configuration Manager met Azure.

## <a name="specifications-for-cloud-management-gateway"></a>Specificaties voor cloud management gateway

- Elk exemplaar van cloud management gateway ondersteunt 4.000 clients.
- U wordt aangeraden dat u ten minste twee exemplaren van de cloud management gateway naar Verbeter de beschikbaarheid van maken.
- Cloud management gateway ondersteunt alleen de punt en software-update-punt beheerrollen.
-   De volgende functies in Configuration Manager worden momenteel niet ondersteund voor cloud management gateway:

    -   Clientimplementatie
    -   Automatische sitetoewijzing
    -   Toepassingscatalogus (inclusief software goedkeuringsaanvragen)
    -   Implementatie van het volledige besturingssysteem (OSD)
    -   Takenreeksen (alle)
    -   Configuration Manager-console
    -   Externe hulpprogramma 's
    -   Website voor rapportage
    -   Wake on LAN
    -   Mac, Linux en UNIX-clients
    -   Azure Resource Manager
    -   Peer-cache
    -   On-premises Mobile Device Management

## <a name="cost-of-cloud-management-gateway"></a>Kosten van cloud management gateway

>[!IMPORTANT]
>De volgende kostengegevens is voor het schatten van alleen bedoeld. Uw omgeving misschien andere variabelen die invloed hebben op de totale kosten van het gebruik van cloud management gateway.

Beheergateway cloud maakt gebruik van de volgende Microsoft Azure-functionaliteit die leidt ertoe dat de kosten voor het account Azure-abonnement:

-   Virtuele machine

    -   Cloud-management-gateway vereist momenteel een standaard\_A2 virtuele machine. Wanneer u de service maakt, kunt u hoeveel virtuele machines voor de ondersteuning van de service (een is de standaardinstelling).

    -   Voor het schatten van uitsluitend verwacht een enkele Azure Standard\_A2 virtuele machine kan ongeveer 2.000 gelijktijdige clients op Internet ondersteunen.

    -   Zie de [Azure prijscategorie Rekenmachine](https://azure.microsoft.com/en-us/pricing/calculator/) om te bepalen, potentiële kosten.

      >[!NOTE]
      >Virtuele machinekosten verschillen per regio.

-   Uitgaande gegevensoverdracht

    -   Kosten verbonden zijn voor gegevens die buiten de service. Zie de [Azure bandbreedte prijsinformatie](https://azure.microsoft.com/pricing/details/bandwidth/) om te bepalen, potentiële kosten.

    -   Voor het schatten van dient alleen te verwachten dat ongeveer 100 MB per client per maand voor Internet-clients voeren vernieuwen van beleid om het uur.

    >[!NOTE]
    > Uitvoeren van andere acties ondersteund via de cloud management gateway (bijvoorbeeld, het implementeren van software-updates of toepassingen) wordt verhoogd, de hoeveelheid uitgaande gegevensoverdracht van Azure.

-   Inhoudsopslag

    -   Clients op Internet die worden beheerd door de cloudgateway management krijgt de inhoud van de software-update via Windows Update zonder kosten.

    -   Alle andere vereiste inhoud (bijvoorbeeld toepassingen) moet worden gedistribueerd naar een cloud-gebaseerd distributiepunt. De cloud management gateway ondersteunt momenteel alleen Cloud-distributiepunt voor het verzenden van inhoud aan clients.

    - Zie de kosten van het gebruik van een [clouddistributiepunt](/sccm/core/plan-design/hierarchy/use-a-cloud-based-distribution-point#cost-of-using-cloud-based-distribution) voor meer informatie.

## <a name="frequently-asked-questions-about-the-cloud-management-gateway-cmg"></a>Veelgestelde vragen over de cloud management gateway (CMG)

### <a name="why-use-the-cloud-management-gateway"></a>Waarom de cloud-management-gateway gebruiken?

Deze functie gebruiken voor het vereenvoudigen van Internet-gebaseerd clientbeheer in drie stappen uit de Configuration Manager-console.

1. De CMG implementeren voor het gebruik van Azure de [Cloud Management-Gateway maken](/sccm/core/clients/manage/setup-cloud-management-gateway) wizard.
2. Configureer de [cloudverbindingspunt management gateway](/sccm/core/servers/deploy/configure/install-site-system-roles) sitesysteemrol.
3. [Rollen configureert voor verkeer van de cloud management gateway](/sccm/core/clients/manage/setup-cloud-management-gateway#step-7-configure-roles-for-cloud-management-gateway-traffic), zoals het beheerpunt en de software-updatepunt.

### <a name="how-does-the-cloud-management-gateway-work"></a>Hoe werkt de cloud management gateway?

- De cloudverbindingspunt management gateway biedt een consistente en hoge prestaties verbinding van Internet naar de cloud management gateway.
- Instellingen voor publiceert Configuration Manager naar de CMG met inbegrip van gegevens en beveiliging verbindingsinstellingen.
- De CMG worden geverifieerd en verzendt de Configuration Manager-clientaanvragen met het verbindingspunt cloud management gateway. Deze aanvragen worden doorgestuurd naar de rollen in het bedrijfsnetwerk volgens URL-toewijzingen.

### <a name="how-is-the-cloud-management-gateway-deployed"></a>Hoe wordt de cloudgateway management geïmplementeerd?

Het onderdeel cloud service manager op het service connection point verwerkt alle CMG implementatietaken. Bovendien wordt bewaakt en rapporten service-status en logboekregistratie van Azure AD. Zorg dat uw serviceverbindingspunt zich in [onlinemodus](/sccm/core/servers/deploy/configure/about-the-service-connection-point#bkmk_modes).

#### <a name="certificate-requirements"></a>Certificaatvereisten

U moet de volgende certificaten voor het beveiligen van de CMG:

- **Beheercertificaat** -dit is geen certificaat met inbegrip van zelfondertekende certificaten. U kunt een openbaar certificaat dat is geüpload naar Azure AD of een [PFX met persoonlijke sleutel](/sccm/mdm/deploy-use/create-pfx-certificate-profiles) geïmporteerd in Configuration Manager om te verifiëren met Azure AD.
- **Certificaat voor Web service** -het is raadzaam dat u een openbare CA-certificaat te krijgen van systeemeigen vertrouwensrelatie door clients. De CName maken in de openbare DNS-registratieservice. Met wild card certificaten worden niet ondersteund.
- **Hoofdmap/SubCA certificaten uploaden naar CMG** -de CMG moet volledige validatie van certificaatketen op PKI-clientcertificaten. Als u een ondernemings-CA gebruikt voor het uitgeven van PKI-clientcertificaten en hun basis- of onderliggende CA niet beschikbaar op het internet is, moet klikt u deze uploaden naar de CMG.

#### <a name="deployment-process"></a>Implementatieproces

Er zijn twee fasen voor de implementatie:

- De cloudservice implementeren
    - Upload uw [Azure Service definitie Schema](https://msdn.microsoft.com/library/azure/ee758711.aspx) (csdef)-bestand
    - Upload uw [Azure Service configuratieschema](https://msdn.microsoft.com/library/azure/ee758710.aspx) (cscfg)-bestand.
- Het onderdeel CMG op de server van uw Azure AD instellen en configureren van eindpunten, HTTP-handlers en -services in Internet Information Services (IIS)

Als u de configuratie van de CMG wijzigt, wordt de implementatie van een configuratie voor de CMG gestart.

### <a name="where-do-i-set-up-the-cloud-management-gateway"></a>Waar kan ik de cloudgateway management instellen?
U kunt de cloud-management-gateway maken op de bovenste site van uw hiërarchie. Als die een centrale beheersite, kunt u CMG verbindingspunten op onderliggende primaire sites maken.

### <a name="how-does-the-cloud-management-gateway-help-ensure-security"></a>Hoe de cloudgateway management helpen beveiligen

De CMG gezorgd beveiliging op de volgende manieren:

- Accepteert en beheert verbindingen van CMG verbindingspunten inclusief wederzijdse SSL-verificatie met behulp van interne certificaten en verbinding id's.
- Accepteert en stuurt de aanvragen van clients
    - Vooraf authenticatie uitvoert voor verbindingen met wederzijdse SSL op de PKI-clientcertificaat.
    - Lijst met vertrouwde certificaten controleert de hoofdmap van de PKI-clientcertificaat. U kunt deze instelling in de client-instellingen in de eigenschappen van de site communiceren. Ook voert dezelfde validatie uit als het beheerpunt voor de client.
    - Ontvangen URL's worden gevalideerd
    - Filters URL's om te controleren als een verbindingspunt CMG verbinding services aan de URL-aanvraag ontvangen.  
    - Controleert de lengte van de inhoud controleren op elk eindpunt publishing.
    - Maakt gebruik van round-robin om taken te verdelen tussen CMG verbindingspunten van dezelfde site.

- Het verbindingspunt CMG beveiligt
    - Consistente HTTP/TCP-verbindingen met alle virtuele instanties van de verbindende CMG is gebaseerd. Controleert en onderhoudt verbindingen elke minuut.
    - Verifieert wederzijds SSL-verificatie met CMG interne certificaten gebruiken.
    - Doorsturen HTTP-aanvragen op basis van de URL-toewijzingen.
    - Verbindingsstatus van rapporten om weer te geven gezondheidsstatus admin-service.
    - Rapporten eindpunt verkeer rapport per eindpunt om de vijf minuten.

- Beveilig publishing eindpunt Configuration Manager-client geconfronteerd met functies zoals het beheerpunt en de software-update-punt host eindpunten in IIS met serviceclientaanvragen. Elk eindpunt dat is gepubliceerd naar de CMG heeft een URL-toewijzing.
De externe URL is de client gebruikt om te communiceren met de CMG.
De interne URL wordt gebruikt voor het doorsturen van aanvragen naar de interne server CMG verbindingspunt.

#### <a name="example"></a>Voorbeeld:
Wanneer u verkeer op een beheerpunt CMG inschakelt, wordt een reeks URL-toewijzingen intern voor elke beheerserver punt, zoals ccm_system, ccm_incoming en sms_mp gemaakt door Configuration Manager.
De externe URL voor het eindpunt van de punt ccm_system management als volgt uitzien **https://<CMG service name>/CCM_Proxy_MutualAuth/<MP Role ID>/CCM_System**.
De URL is uniek voor elk beheerpunt. De Configuration Manager-client vervolgens de CMG ingeschakeld MP naam zoals puts  **<CMG service name>/CCM_Proxy_MutualAuth/<MP Role ID>**  in de internet MP-lijst.
Alle gepubliceerde externe URL's worden geüpload naar de CMG automatisch CMG kunnen doen URL-filtering is. Alle URL-toewijzing wordt gerepliceerd naar CMG verbindingspunt zodat kunnen worden doorgestuurd naar interne servers volgens client aanvragen van de externe URL.

### <a name="what-ports-are-used-by-the-cloud-management-gateway"></a>Welke poorten worden gebruikt door de cloud management gateway?

- Er zijn geen poorten voor inkomend verkeer zijn vereist voor de on-premises netwerk. Implementatie van CMG wordt automatisch een bunch op CMG maken.
- Naast 443, zijn een aantal uitgaande poorten het verbindingspunt CMG vereist.

|||||
|-|-|-|-|
|Gegevensstroom|Server|Server-poorten|Client|
|CMG-implementatie|Azure|443|Serviceverbindingspunt Configuration Manager|
|CMG kanaal maken|CMG|VM-instantie: 1-poort: 443<br>VM-instantie: N (N > = 2 en N < = 16) poorten: 10124 ~ N 10140 ~ N|CMG verbindingspunt|
|Client CMG|CMG|443|Client|
|CMG connector siterol (momenteel beheerpunten en software-updatepunten)|Siterol|Protocol/poorten zijn geconfigureerd op de siterol|Verbindingspunt CMG|

### <a name="how-can-you-improve-performance-of-the-cloud-management-gateway"></a>Hoe kunt u de prestaties van de cloud management gateway verbeteren?

- Configureer indien mogelijk de CMG, CMG connection point en de Configuration Manager-siteserver in dezelfde regio netwerk de latentie te verminderen.
- De verbinding tussen de Configuration Manager-client en de CMG is momenteel niet bekend is met regio.
- Voor het verkrijgen van hoge beschikbaarheid, wordt aangeraden ten minste twee virtuele instanties van de CMG en twee verbindingspunten CMG per site
- U kunt de CMG meer om clients te ondersteunen door toe te voegen meer VM-instanties schalen. Taakverdeling door de load balancer van Azure AD zijn.
- Maak meer CMG verbindingspunten verdelen over de lagen. De CMG wordt round-robin het verkeer naar de verbindingspunten CMG verbinding.
- Client ondersteuningsnummer per CMG VM-instantie is 6 kB in de release 1702. Wanneer het kanaal CMG onder hoge belasting, wordt de aanvraag wordt nog steeds verwerkt maar duurt mogelijk langer dan normaal.

### <a name="how-can-you-monitor-the-cloud-management-gateway"></a>Hoe kunt u de cloud management gateway bewaken?

Gebruik voor problemen met implementatie, **CloudMgr.log** en **CMGSetup.log**.
Gebruik om problemen op servicestatus **CMGService.log** en **SMS_CLOUD_PROXYCONNECTOR.log**.
Gebruik voor het oplossen van problemen clientverkeer **CMGHttpHandler.log**, **CMGService.Log**, en **SMS_CLOUD_PROXYCONNECTOR.log**.

Zie voor een lijst van alle CMG-gerelateerde logboekbestanden [logboekbestanden in Configuration Manager](https://docs.microsoft.com/sccm/core/plan-design/hierarchy/log-files#cloud-management-gateway)

## <a name="next-steps"></a>Volgende stappen

[Een cloudbeheergateway instellen](setup-cloud-management-gateway.md)
