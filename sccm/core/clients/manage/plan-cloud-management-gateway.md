---
title: Plannen voor de cloud management gateway | Microsoft-documenten
description: 
ms.date: 05/16/2017
ms.prod: configuration-manager
ms.technology:
- configmgr-client
ms.assetid: 2dc8c9f1-4176-4e35-9794-f44b15f4e55f
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: ae60eb25383f4bd07faaa1265185a471ee79b1e9
ms.openlocfilehash: b1295891a5567e64b901c79100c2971e526dc874
ms.contentlocale: nl-nl
ms.lasthandoff: 05/17/2017

---

# <a name="plan-for-the-cloud-management-gateway-in-configuration-manager"></a>Plan voor de gateway cloud management in Configuration Manager

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*

Vanaf versie 1610 wordt biedt cloud management gateway een eenvoudige manier voor het beheren van Configuration Manager-clients op het Internet. De cloud management gateway-service wordt geïmplementeerd op Microsoft Azure en vereist een Azure-abonnement. De clientcomputer verbindt met uw on-premises Configuration Manager-infrastructuur met behulp van een nieuwe rol met de naam van het cloud-gateway-connector wordt gemaakt. Zodra de geïmplementeerd en geconfigureerd, is clients zich op de lokale Configuration Manager sitesysteemrollen ongeacht of ze op de interne persoonlijke netwerk zijn of op het Internet toegang hebben tot.

Gebruik de Configuration Manager-console naar de service implementeren in Azure, de cloud gateway connector beheerpuntrol toevoegen en configureren van sitesysteemrollen voor cloud management gateway-verkeer. Cloud management gateway ondersteunt momenteel alleen de management point- and -software-update-punt rollen.

Clientcertificaten en Secure Socket Layer (SSL)-certificaten zijn vereist voor de verificatie van computers en het versleutelen van communicatie tussen de verschillende lagen van de service. Clientcomputers ontvangen doorgaans een clientcertificaat via beleidsafdwinging groep. Voor het versleutelen van het verkeer tussen clients en de sitesysteemserver die als host fungeert voor de functies, moet u een aangepaste SSL-certificaat maken vanuit de Certificeringsinstantie. U moet ook instellen van een beheercertificaat voor Azure waarmee Configuration Manager voor het implementeren van de cloud management gateway-service kan.

## <a name="requirements-for-cloud-management-gateway"></a>Vereisten voor cloud management gateway

-   Clientcomputers en de sitesysteemserver die het cloud-gateway-connector beheerpunt uitgevoerd.

-   Aangepaste SSL-certificaten van de interne Certificeringsinstantie - gebruikt voor het versleutelen van communicatie van clientcomputers en verifiëren van de identiteit van de cloud management gateway-service.

-   Azure-abonnement voor cloudservices.

-   Azure-beheercertificaat - gebruikt voor het verifiëren van Configuration Manager met Azure.

## <a name="specifications-for-cloud-management-gateway"></a>Specificaties voor cloud management gateway

- Elk exemplaar van cloud management gateway ondersteunt 4000 clients.
- Wij raden ten minste twee exemplaren van de cloud management gateway naar de beschikbaarheid te verbeteren.
- Cloud management gateway ondersteunt alleen de management point- and -software-update-punt rollen.
-   De volgende functies in Configuration Manager worden momenteel niet ondersteund voor cloud management gateway:

    -   Clientimplementatie
    -   Automatische sitetoewijzing
    -   Gebruikersbeleid
    -   Toepassingscatalogus (inclusief software goedkeuringsaanvragen)
    -   Implementatie van het volledige besturingssysteem (OSD)
    -   Configuration Manager-console
    -   Externe hulpprogramma 's
    -   Rapportage website
    -   Wake on LAN
    -   Mac, Linux en UNIX-clients
    -   Azure Resource Manager
    -   Peercache
    -   On-premises Mobile Device Management

## <a name="cost-of-cloud-management-gateway"></a>Kosten van cloud management gateway

>[!IMPORTANT]
>Hieronder vindt u kosteninformatie is bedoeld voor uitsluitend te schatten. Uw omgeving mogelijk andere variabelen die invloed hebben op de totale kosten van het gebruik van cloud management gateway.

Cloud management gateway maakt gebruik van de volgende Microsoft Azure-functionaliteit die vinden er kosten aan het account Azure-abonnement:

-   Virtuele machine

    -   Een standaard die momenteel zijn vereist voor cloud management gateway\_A2 virtuele machine. Bij het maken van de service, kunt u bepalen hoeveel virtuele machines voor de ondersteuning van de service (een is de standaardinstelling).

    -   Bij het schatten van uitsluitend, verwacht een enkele Azure Standard\_A2 virtuele machine kunt ongeveer 2.000 gelijktijdige Internet-gebaseerde clients ondersteunt.

    -   Zie de [Azure prijscategorie Rekenmachine](https://azure.microsoft.com/en-us/pricing/calculator/) bij het bepalen van de mogelijke kosten.

      >[!NOTE]
      >Virtuele machinekosten verschillen per regio.

-   Uitgaande gegevensoverdracht

    -   Kosten in rekening worden gebracht voor gegevens die buiten de service... Zie de [Azure bandbreedte pricing details](https://azure.microsoft.com/en-us/pricing/details/bandwidth/) bij het bepalen van de mogelijke kosten.

    -   Bij het schatten van uitsluitend, verwacht ongeveer 100 MB per client per maand voor clients op Internet is tijdens het vernieuwen van beleid elk uur doorzoeken.

    >[!NOTE]
    > Andere bewerkingen ondersteund via de cloud management gateway (bijvoorbeeld, het implementeren van software-updates of toepassingen) uitvoert, wordt de hoeveelheid uitgaande gegevensoverdracht vanuit Azure verhoogd.

-   Inhoudsopslag

    -   Gratis ontvangen clients via Internet worden beheerd met cloud management gateway inhoud van software-updates via Windows Update.

    -   Alle andere vereiste inhoud (bijvoorbeeld toepassingen) moet worden gedistribueerd naar een cloud-gebaseerde distributiepunt. De cloud management gateway ondersteunt op dit moment kunnen alleen Clouddistributiepunt voor inhoud te verzenden naar clients.

    - Zie de kosten van het gebruik van een [clouddistributiepunt](/sccm/core/plan-design/hierarchy/use-a-cloud-based-distribution-point#cost-of-using-cloud-based-distribution) voor meer informatie.

## <a name="next-steps"></a>Volgende stappen

[Beheergateway cloud instellen](setup-cloud-management-gateway.md)


## <a name="frequently-asked-questions-about-the-cloud-management-gateway-cmg"></a>Veelgestelde vragen over de Cloud Management Gateway (CMG)

### <a name="why-use-the-cloud-management-gateway"></a>Waarom gebruikt de cloud management gateway?

Gebruik deze rol voor het vereenvoudigen van Internet-gebaseerd clientbeheer in drie stappen van de Configuration Manager-console.

1. De CMG implementeren op Azure worden verkregen met de [maken Cloud Management Gateway](/sccm/core/clients/manage/setup-cloud-management-gateway) wizard.
2. Configureer de [cloud-gateway verbinding beheerpunt](/sccm/core/servers/deploy/configure/install-site-system-roles) sitesysteemrol.
3. [Rollen configureert voor cloud-gateway beheerverkeer](/sccm/core/clients/manage/setup-cloud-management-gateway#step-7-configure-roles-for-cloud-management-gateway-traffic), zoals beheer- en software-updatepunt.

### <a name="how-does-the-cloud-management-gateway-work"></a>Hoe werkt de cloud management gateway?

- Cloud-gateway verbinding beheerpunt maakt een verbinding consistent en hoge prestaties van het Internet naar de cloud management gateway.
- Configuration Manager publiceert instellingen in de CMG met inbegrip van gegevens en beveiliging verbindingsinstellingen.
- De CMG worden geverifieerd en verzendt de Configuration Manager-clientaanvragen naar de cloud-gateway verbinding beheerpunt. Deze aanvragen worden doorgestuurd naar de rollen in het bedrijfsnetwerk volgens URL-toewijzingen.

### <a name="how-is-the-cloud-management-gateway-deployed"></a>Hoe wordt de cloud management gateway geïmplementeerd?

Het onderdeel cloud service manager op de service connection point verwerkt alle CMG implementatietaken. Daarnaast bewaakt en informatie over service-status en logboekregistratie doorgegeven vanuit Azure AD.

#### <a name="certificate-requirements"></a>Certificaatvereisten

U moet de volgende certificaten voor het beveiligen van de CMG:

- **Beheercertificaat** -dit is geen certificaat met inbegrip van zelfondertekende certificaten. U kunt een openbaar certificaat geüpload naar Azure AD of een [PFX met persoonlijke sleutel](/sccm/mdm/deploy-use/create-pfx-certificate-profiles) geïmporteerd in Configuration Manager om te verifiëren met Azure AD. 
- **Certificaat voor Web-service** -raden wij aan dat u een openbare CA-certificaat te krijgen van systeemeigen vertrouwensrelatie door clients. De CName moet worden gemaakt in de openbare DNS-registar. Jokertekens certificaten worden niet ondersteund.
- **Hoofdmap/SubCA certificaten uploaden naar CMG** -de CMG moet volledige validatie van certificaatketen op client-PKI-certificaten. Als u een ondernemings-CA voor PKI-clientcertificaten en hun basis- of onderliggende CA niet beschikbaar is op het internet is, moet u uploaden naar de CMG.

#### <a name="deployment-process"></a>Implementatieproces

Er zijn twee fasen aan de implementatie:

- De cloudservice implementeren
    - Upload uw [Azure Service definitie Schema](https://msdn.microsoft.com/library/azure/ee758711.aspx) (csdef)-bestand
    - Upload uw [Azure Service configuratieschema](https://msdn.microsoft.com/library/azure/ee758710.aspx) (cscfg)-bestand.
- Het onderdeel CMG op uw Azure AD-server instellen en configureren van eindpunten, HTTP-handlers en services in Internet Information Services (IIS)

Als u de configuratie van de CMG wijzigt, wordt de implementatie van een configuratie voor de CMG gestart.

### <a name="how-does-the-cloud-management-gateway-help-ensure-security"></a>Hoe de cloud management gateway te helpen zorgen beveiliging?

De CMG helpt zorgen voor beveiliging op de volgende manieren:

- Accepteert en verbindingen van CMG verbindingspunten inclusief wederzijdse SSL-verificatie met behulp van interne certificaten en verbinding id's beheert.
- Heeft geaccepteerd en verzendt aanvragen van client
    - Vooraf verifieert verbindingen met behulp van wederzijdse SSL op de client PKI-certificaat.
    - Lijst met vertrouwde certificaten controleert de hoofdmap van de PKI-clientcertificaat. U kunt deze instelling in de client communicatie-instellingen in de site-eigenschappen opgeven. Ook voert dezelfde validatie uit als het beheerpunt voor de client.
    - Ontvangen URL's worden gevalideerd
    - Filters URL's om te controleren als een verbindingspunt CMG verbinding services aan de URL-aanvraag ontvangen.  
    - Controleert de lengte van de inhoud uit voor elk eindpunt publiceren.
    - Maakt gebruik van round-robin verdelen tussen CMG verbindingspunten van dezelfde site.

- Het verbindingspunt CMG beveiligt
    - Consistente HTTP/TCP-verbindingen met alle virtuele instanties van de verbindende CMG bouwt. Controleert en onderhoudt verbindingen per minuut.
    - Wederzijds autheticates SSL-verificatie met CMG interne certificaten gebruiken.
    - Stuurt HTTP-aanvragen op basis van URL-toewijzingen.
    - Verbindingsstatus rapporten om admin-service de status weer te geven.
    - Rapporten endpoint verkeer rapport per eindpunt om de 5 minuten.

- Beveilig publishing endpoint Configuration Manager-client rollen zoals de beheer- en software-update-punt host-eindpunten in IIS met serviceclientaanvragen gericht. Elke gepubliceerd naar de CMG eindpunt heeft een URL-toewijzing.
De externe URL is de client gebruikt om te communiceren met de CMG.
De interne URL is het verbindingspunt CMG gebruikt voor het doorsturen van aanvragen naar de interne server. 

#### <a name="example"></a>Voorbeeld:
Wanneer u CMG verkeer op een beheerpunt inschakelt, wordt een reeks URL-toewijzingen voor elke beheerserver punt, zoals ccm_system, ccm_incoming en sms_mp intern gemaakt door Configuration Manager.
De externe URL voor het eindpunt van de punt ccm_system beheer als volgt uitzien **https://<CMG service name>/CCM_Proxy_MutualAuth/<MP Role ID>/CCM_System**. De URL is uniek voor elk beheerpunt. De Configuration Manager-client en plaatst de CMG ingeschakeld naam Management Pack zoals vervolgens  **<CMG service name>/CCM_Proxy_MutualAuth/<MP Role ID>**  in de beheerpuntlijst van internet. Alle gepubliceerde externe URL's worden geüpload naar de CMG automatisch is CMG kunnen doen URL filteren. Alle URL-toewijzing wordt gerepliceerd naar CMG verbindingspunt zodat kunnen worden doorgestuurd naar interne servers volgens client externe URL aanvragen.

### <a name="what-ports-are-used-by-the-cloud-management-gateway"></a>Welke poorten worden gebruikt door de cloud management gateway? 

- Er is geen inkomende poorten die nodig zijn op het lokale netwerk. Implementatie van CMG wordt automatisch een bunch op CMG maken. 
- Behalve 443, zijn sommige uitgaande poorten die door het verbindingspunt CMG vereist.

|||||
|-|-|-|-|
|Gegevensstroom|Server|Server-poorten|Client|
|CMG-implementatie|Azure|443|Verbindingspunt van Configuration Manager-service|
|CMG channel maken|CMG|VM-exemplaar: 1-poort: 443<br>VM-exemplaar: N (N > = 2 en N < = 16) poorten: 10124 ~ N 10140 ~ N|Verbindingspunt CMG|
|Client naar CMG|CMG|443|Client|
|CMG-connector voor siterol (momenteel beheerpunten en software-updatepunten)|Siterol|Protocol/poorten die zijn geconfigureerd op de siterol|Verbindingspunt CMG|

### <a name="how-can-you-improve-performance-of-the-cloud-management-gateway"></a>Hoe kunt u de prestaties van de cloud management gateway verbeteren?

- Configureer, indien mogelijk, de CMG CMG verbindingspunt en de Configuration Manager-siteserver in dezelfde regio te verminderen latentie netwerk.
- De verbinding tussen de Configuration Manager-client en de CMG is momenteel niet regio-ondersteuning.
- Om toegang te krijgen van hoge beschikbaarheid, wordt aangeraden ten minste 2 virtuele instanties van de CMG en twee verbindingspunten CMG per site 
- U kunt de CMG meer om clients te ondersteunen door toe te voegen meer exemplaren van de VM schalen. Taakverdeling door de Azure AD load balancer zijn.
- Maak meer CMG verbindingspunten voor het distribueren van de belasting ertussen. De CMG wordt round-robin het verkeer naar de verbindende CMG verbindingspunten.
- Client ondersteuningsnummer per CMG VM-exemplaar is 6k in de release 1702. Wanneer het kanaal CMG zwaar belast is, wordt de aanvraag wordt nog steeds verwerkt maar langer duren dan normaal.

### <a name="how-can-you-monitor-the-cloud-management-gateway"></a>Hoe kunt u de cloud management gateway controleren?

Gebruiken voor het oplossen van implementatie **CloudMgr.log** en **CMGSetup.log**.
Gebruiken voor het oplossen van servicestatus **CMGService.log** en **SMS_CLOUD_PROXYCONNECTOR.log**.
Gebruik voor het oplossen van problemen clientverkeer **CMGHttpHandler.log**, **CMGService.Log**, en **SMS_CLOUD_PROXYCONNECTOR.log**.

Zie voor een lijst van alle CMG productspecifieke logboekbestanden, [in Configuration Manager-logboekbestanden](https://docs.microsoft.com/sccm/core/plan-design/hierarchy/log-files#cloud-management-gateway)


