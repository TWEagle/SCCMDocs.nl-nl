---
title: Plan voor cloud-beheergateway
titleSuffix: Configuration Manager
description: Plannen en ontwerpen van de cloud management gateway (CMG) voor het vereenvoudigen van beheer van clients op internet.
ms.date: 03/22/2018
ms.prod: configuration-manager
ms.technology:
- configmgr-client
ms.assetid: 2dc8c9f1-4176-4e35-9794-f44b15f4e55f
author: aczechowski
ms.author: aaroncz
manager: dougeby
ms.openlocfilehash: dabc248c1788ecad4d7b25c0a1f592e0ddeef826
ms.sourcegitcommit: a19e12d5c3198764901d44f4df7c60eb542e765f
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 03/28/2018
---
# <a name="plan-for-the-cloud-management-gateway-in-configuration-manager"></a>Plan voor de cloudgateway management in Configuration Manager

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*

De cloud management gateway (CMG) biedt een eenvoudige manier voor het beheren van Configuration Manager-clients op internet. De CMG als een cloudservice in Microsoft Azure implementeert, kunt u traditionele clients die op internet zonder aanvullende infrastructuur roamen te beheren. Ook moet niet u uw on-premises infrastructuur met het internet zichtbaar. 

> [!Tip]  
> Deze functie is geïntroduceerd in versie 1610 als een [functie van de voorlopige versie](/sccm/core/servers/manage/pre-release-features). Vanaf versie 1802, deze functie is niet langer een voorlopige versie.

Nadat de vereiste onderdelen, bestaat het maken van de CMG uit de volgende drie stappen in de Configuration Manager-console:
1. De cloudservice CMG implementeren in Azure.
2. De rol serviceaansluitpunt CMG toevoegen. 
3. Configureer de site en de rollen voor de service. Eenmaal geïmplementeerd en geconfigureerd, clients naadloos toegang krijgen tot lokale siterollen ongeacht of ze zich op het intranet of internet.

Dit artikel bevat de fundamentele kennis om meer informatie over de CMG, hoe deze in uw omgeving past ontwerpen en plannen en implementeren. 



## <a name="scenarios"></a>Scenario's 

Er zijn verschillende scenario's waarvoor een CMG nuttig is. De volgende scenario's worden een aantal veelgebruikte:  

- Traditionele Windows-clients met Active Directory-domein identiteit beheren. Deze clients zijn Windows 7, Windows 8.1 en Windows 10. Deze PKI-certificaten gebruikt voor het communicatiekanaal te beveiligen. Activiteiten omvatten:  
    - Software-updates en endpoint protection
    - Inventaris- en client-status
    - Instellingen voor naleving
    - Softwaredistributie naar het apparaat
    - Takenreeks Windows 10 in-place upgrade (vanaf versie 1802)

- Traditionele Windows 10-clients beheren met de identiteit van de moderne, hybride of pure cloud domein met Azure Active Directory (Azure AD). Azure AD-clients gebruiken om te verifiëren in plaats van PKI-certificaten. Met behulp van Azure AD is het eenvoudiger is ingesteld, te configureren en te onderhouden dan complexere PKI-systemen. Activiteiten zijn hetzelfde als het eerste scenario, evenals:  
    - Softwaredistributie naar de gebruiker  

- De Configuration Manager-client installeren op Windows 10-apparaten via internet. Met behulp van Azure AD, kunt het apparaat te verifiëren bij de CMG voor clientregistratie en -toewijzing. U kunt de client handmatig installeert of met een andere software distributiemethode, zoals Microsoft Intune.  

- Nieuw apparaat inrichten met CO-management. CMG is niet vereist voor CO-beheer. Het voltooien van een end-to-end-scenario voor nieuwe apparaten met betrekking tot Windows Automatische piloot, Azure AD, helpt Microsoft Intune en Configuration Manager.  

### <a name="specific-use-cases"></a>Specifieke gebruiksvoorbeelden
In deze scenario's kunnen de volgende gevallen specifiek apparaat toepassen:

- Apparaten zoals laptops roaming  

- Extern/branch office-apparaten die minder dure en efficiënter beheren via het internet dan via een WAN of via een VPN.  

- Fusies en aankopen, waar mogelijk eenvoudigste apparaten toevoegen aan Azure AD en beheren via een CMG.  

> [!Important]
> Standaard worden alle clients beleid ontvangen voor een CMG en deze gaan gebruiken zodra ze op basis van het internet. Afhankelijk van het scenario en gebruik geval die van toepassing voor uw organisatie is, u moet mogelijk gebruik van de CMG bereik. Zie voor meer informatie de [inschakelen voor clients gebruiken een cloud management gateway](/sccm/core/clients/deploy/about-client-settings#enable-clients-to-use-a-cloud-management-gateway) client-instelling.


## <a name="topology-design"></a>Topologie ontwerpen

### <a name="cmg-components"></a>CMG onderdelen
Implementatie en werking van de CMG omvat de volgende onderdelen:  

- De **CMG cloudservice** in Azure worden geverifieerd en aanvragen van de Configuration Manager-client met het verbindingspunt CMG stuurt.  
 
- De **CMG verbindingspunt** sitesysteemrol biedt een consistente en hoge prestaties verbinding van de on-premises netwerk naar de service CMG in Azure. Ook worden instellingen in de CMG met inbegrip van gegevens en beveiliging verbindingsinstellingen gepubliceerd. Het verbindingspunt CMG worden aanvragen van clients van de CMG doorstuurt naar lokale rollen in overeenstemming met URL-toewijzingen.

- De [ **serviceaansluitpunt** ](/sccm/core/servers/deploy/configure/about-the-service-connection-point) sitesysteemrol wordt uitgevoerd voor de cloud service manager-onderdeel dat alle CMG implementatietaken verwerkt. Bovendien wordt bewaakt en rapporten service-status en logboekregistratie van Azure AD. Zorg dat uw serviceverbindingspunt zich in [onlinemodus](/sccm/core/servers/deploy/configure/about-the-service-connection-point#bkmk_modes).  

- De **beheerpunt** sitesysteemrol services clientaanvragen per normaal.  

- De **software-updatepunt** sitesysteemrol services clientaanvragen per normaal.  

- **Clients op Internet** verbinding maken met de CMG voor toegang tot on-premises Configuration Manager-onderdelen.

- Maakt gebruik van de CMG een **HTTPS op basis van certificaten** webservice om te helpen beveiligen netwerkcommunicatie met clients.  

- Gebruik voor clients op Internet **PKI-certificaten of Azure AD** voor identiteits- en -verificatie.  

- Een [ **clouddistributiepunt** ](/sccm/core/plan-design/hierarchy/use-a-cloud-based-distribution-point) levert u inhoud op internet gebaseerde clients, indien nodig.  


### <a name="azure-resource-manager"></a>Azure Resource Manager
<!-- 1324735 -->
Vanaf versie 1802, kunt u de CMG met behulp van een **Azure Resource Manager-implementatie**. [Azure Resource Manager](/azure/azure-resource-manager/resource-group-overview) is een moderne platform voor het beheren van alle resources van de oplossing als één entiteit aangeroepen een [resourcegroep](/azure/azure-resource-manager/resource-group-overview#resource-groups). Bij het implementeren van CMG met Azure Resource Manager, de site maakt gebruik van Azure Active Directory (Azure AD) om te verifiëren en het maken van de benodigde cloud-bronnen. Deze gemoderniseerde implementatie is niet vereist voor de klassieke Azure-beheercertificaat.  

De wizard CMG biedt nog steeds de optie voor een **klassieke service-implementatie** met behulp van een Azure-beheercertificaat. Om te vereenvoudigen de implementatie en beheer van bronnen, wordt met het Azure Resource Manager-implementatiemodel aanbevolen voor alle nieuwe CMG exemplaren. Indien mogelijk, implementeer de bestaande CMG exemplaren via Resource Manager opnieuw. Zie voor meer informatie [wijzigen van een CMG](/sccm/core/clients/manage/cmg/setup-cloud-management-gateway#modify-a-cmg).

> [!IMPORTANT]  
> Deze mogelijkheid biedt ondersteuning voor Azure Cloud Service Providers (CSP) niet inschakelen. De implementatie CMG met Azure Resource Manager blijft de klassieke cloud-service biedt geen ondersteuning voor de CSP. Zie voor meer informatie [beschikbare Azure-services in Azure CSP](/azure/cloud-solution-provider/overview/azure-csp-available-services). 


### <a name="hierarchy-design"></a>Hiërarchie-ontwerp

Maak de CMG op de bovenste site van uw hiërarchie. Maak de verbindingspunten CMG op onderliggende primaire sites als die van een centrale beheersite. Het onderdeel cloud service manager is op het serviceverbindingspunt ook op de centrale beheersite is. Dit ontwerp kan de service delen tussen verschillende primaire sites, indien nodig.

U kunt meerdere CMG services in Azure maken en kunt u meerdere CMG verbindingspunten maken. Meerdere CMG verbindingspunten bieden taakverdeling voor clientverkeer van de CMG op de lokale rollen. Om te beperken netwerklatentie, wijst u de bijbehorende CMG toe aan dezelfde geografische regio als de primaire site.

 > [!Note]  
 > Internet-clients en de CMG vallen niet in een grensgroep.

Andere factoren, zoals het aantal clients te beheren, ook invloed op uw ontwerp CMG. Zie voor meer informatie [prestaties en schaalbaarheid](#performance-and-scale).

#### <a name="example-1-standalone-primary-site"></a>Voorbeeld 1: zelfstandige primaire site

Contoso heeft een zelfstandige primaire site in een on-premises datacenter op het hoofdkantoor in New York City. 
- Ze maken een CMG in het gebied Oost ons Azure netwerklatentie te verminderen. 
- Maken van twee CMG verbindingspunten, beide gekoppeld zijn aan de service voor eenmalige CMG.  

Wanneer clients naar het internet roamen, ze communiceren met de CMG in Oost ons Azure-regio. De CMG verzendt deze communicatie via beide van de verbindingspunten CMG.

#### <a name="example-2-hierarchy-with-site-specific-cmg"></a>Voorbeeld 2: hiërarchie met sitespecifieke CMG

Een centrale beheersite in een on-premises datacenter heeft vierde koffie op het hoofdkantoor in Haarlem. Een primaire site bevindt zich in hetzelfde datacenter en de primaire site bevindt zich in hun Europese hoofdkantoor in Parijs. 
- Ze Maak twee CMG services op de centrale beheersite:
     - Een CMG in de regio West ons Azure.
     - Een CMG in de regio West-Europa Azure.
- Op de primaire site Seattle gebaseerde maken ze een CMG verbindingspunt is gekoppeld aan de CMG van West ons.
- Op de primaire site op basis van Parijs maken ze een CMG verbindingspunt is gekoppeld aan de West-Europa CMG.

Wanneer clients op basis van Seattle naar het internet roamen, ze communiceren met de CMG in de regio West ons Azure. De CMG verzendt deze communicatie met het verbindingspunt Seattle gebaseerde CMG.

Op deze manier wanneer clients op basis van Parijs naar het internet roamen, communiceren ze met de CMG in de regio West-Europa Azure. De CMG verzendt deze communicatie met het verbindingspunt Parijs gebaseerde CMG. Wanneer gebruikers op basis van Parijs naar het hoofdkantoor in Seattle reizen, blijven hun computers om te communiceren met de CMG in de regio West-Europa Azure. 

 > [!Note]  
 > Vierde koffie beschouwd als een andere CMG verbindingspunt maken op de gekoppeld aan de CMG van West ons Parijs op basis van een primaire site. Parijs-clients zou vervolgens gebruiken voor beide CMGs, ongeacht hun locatie. Terwijl deze configuratie helpt om taken te verdelen voor verkeer en redundantie van de service, kan dit ook vertragingen veroorzaken wanneer Parijs gebaseerde clients met de VS gebaseerde CMG communiceren. Configuration Manager-clients zijn niet op de hoogte gesteld van de geografische regio, dus niet een CMG die geografisch dichter hebt voorkeur. Clients gebruiken willekeurig een CMG beschikbaar.



## <a name="requirements"></a>Vereisten

- Een **Azure-abonnement** voor het hosten van de CMG.  

    - Een **Azure beheerder** moet deelnemen aan het maken van een bepaalde onderdelen, afhankelijk van uw ontwerp. Deze persona vereist geen machtigingen in Configuration Manager.  

- Ten minste één lokale WindowsServer naar de host de **CMG verbindingspunt**. U kunt deze rol met andere sitesysteemrollen van Configuration Manager dezelfde plaatsen.  

- De **serviceaansluitpunt** moet [onlinemodus](/sccm/core/servers/deploy/configure/about-the-service-connection-point#bkmk_modes).   

- Een [ **serverauthenticatiecertificaat** ](/sccm/core/clients/manage/cmg/certificates-for-cloud-management-gateway#cmg-server-authentication-certificate) voor de CMG.  

- Als u de klassieke Azure-implementatie gebruikt, moet u een [ **Azure-beheercertificaat**](/sccm/core/clients/manage/cmg/certificates-for-cloud-management-gateway#azure-management-certificate).  

    > [!TIP]  
    > Beginnen met Configuration Manager versie 1802, met behulp van de **Azure Resource Manager** implementatiemodel wordt aanbevolen. Er is geen dit beheercertificaat vereist.  

- **Andere certificaten** mogelijk vereist zijn, afhankelijk van uw client-OS-versie en verificatie model. Zie voor meer informatie [CMG certificaten](/sccm/core/clients/manage/cmg/certificates-for-cloud-management-gateway).  

    - Vanaf versie 1802, moet u alle CMG ingeschakeld [ **beheerpunten voor gebruik van HTTPS**](/sccm/core/clients/manage/cmg/certificates-for-cloud-management-gateway#enable-management-point-for-https).  

- Integratie met **Azure AD** mogelijk zijn vereist voor Windows 10-clients. Zie voor meer informatie [configureren Azure-services](/sccm/core/servers/deploy/configure/azure-services-wizard).  

- Clients moeten gebruiken **IPv4**.  



## <a name="specifications"></a>Specificaties

- Alle Windows-versies die worden vermeld in [ondersteunde besturingssystemen voor clients en apparaten](/sccm/core/plan-design/configs/supported-operating-systems-for-clients-and-devices) worden ondersteund voor CMG.  

- CMG ondersteunt alleen de punt en software-update-punt beheerrollen.  

- CMG biedt geen ondersteuning voor clients die alleen met IPv6-adressen communiceren.<!--495606-->  

- Software-updatepunten met behulp van een network load balancer werkt niet met CMG. <!--505311-->  

- Vanaf versie 1802, schakel CMG implementaties met het Model van Azure Resource geen ondersteuning voor Azure Cloud Service Providers (CSP). De implementatie CMG met Azure Resource Manager blijft de klassieke cloud-service biedt geen ondersteuning voor de CSP. Zie voor meer informatie [beschikbare Azure-services in Azure CSP](/azure/cloud-solution-provider/overview/azure-csp-available-services)  


### <a name="support-for-configuration-manager-features"></a>Ondersteuning voor Configuration Manager-functies
De volgende tabel bevat CMG ondersteuning voor Configuration Manager-functies:


|Onderdeel  |Ondersteuning  |
|---------|---------|
| Software-updates     | ![Ondersteund](media/green_check.png) |
| Endpoint protection     | ![Ondersteund](media/green_check.png) |
| Hardware en software-inventaris     | ![Ondersteund](media/green_check.png) |
| Status van de client en meldingen     | ![Ondersteund](media/green_check.png) |
| Instellingen voor naleving     | ![Ondersteund](media/green_check.png) |
| Client installeren</br>(met Azure AD-integratie)     | ![Ondersteund](media/green_check.png)  (1706) |
| Softwaredistributie (gericht op apparaat)     | ![Ondersteund](media/green_check.png) |
| Softwaredistributie (gebruiker gerichte, vereist)</br>(met Azure AD-integratie)     | ![Ondersteund](media/green_check.png)  (1710) |
| Softwaredistributie (gebruiker gerichte, beschikbaar)</br>([alle vereisten](/sccm/apps/deploy-use/deploy-applications#deploy-user-available-applications-on-azure-ad-joined-devices)) | ![Ondersteund](media/green_check.png)  (1802) |
| Takenreeks Windows 10 in-place upgrade     | ![Ondersteund](media/green_check.png)  (1802) |
| Een andere taak sequence-scenario     | ![Niet ondersteund](media/Red_X.png) |
| Client-push     | ![Niet ondersteund](media/Red_X.png) |
| Automatische sitetoewijzing     | ![Niet ondersteund](media/Red_X.png) |
| Toepassingscatalogus     | ![Niet ondersteund](media/Red_X.png) |
| Goedkeuringsaanvragen voor software     | ![Niet ondersteund](media/Red_X.png) |
| Configuration Manager-console     | ![Niet ondersteund](media/Red_X.png) |
| Externe hulpprogramma 's     | ![Niet ondersteund](media/Red_X.png) |
| Website voor rapportage     | ![Niet ondersteund](media/Red_X.png) |
| Wake on LAN     | ![Niet ondersteund](media/Red_X.png) |
| Mac, Linux en UNIX-clients     | ![Niet ondersteund](media/Red_X.png) |
| Peer-cache     | ![Niet ondersteund](media/Red_X.png) |
| On-premises MDM     | ![Niet ondersteund](media/Red_X.png) |


|Sleutel|
|--|
|![Ondersteund](media/green_check.png) = Dit onderdeel wordt ondersteund met CMG door alle ondersteunde versies van Configuration Manager  |
|![Ondersteund](media/green_check.png) (*jjmm*) = dit onderdeel wordt ondersteund met CMG vanaf versie *jjmm* van Configuration Manager  |
|![Niet ondersteund](media/Red_X.png) = Dit onderdeel wordt niet ondersteund met CMG |



## <a name="cost"></a>Kosten

>[!IMPORTANT]  
>De volgende kostengegevens is voor het schatten van alleen bedoeld. Uw omgeving misschien andere variabelen die invloed hebben op de totale kosten van het gebruik van CMG.

CMG maakt gebruik van de volgende Azure onderdelen die aan het account Azure-abonnement kosten:

#### <a name="virtual-machine"></a>Virtuele machine

- Azure Cloud Services CMG gebruikt als platform als een service (PaaS). Deze service maakt gebruik van virtuele machines (VM's) die compute-kosten in rekening worden.  

- CMG gebruikt in Configuration Manager versie 1706, een standaard A2-VM.  

- U start in Configuration Manager versie 1710, CMG maakt gebruik van een standaard A2 V2 VM.  

- Selecteert u het aantal VM-exemplaren de CMG ondersteunen. Een is de standaardinstelling en 16 is het maximum. Dit nummer wordt ingesteld wanneer de CMG maken en daarna om de service te schalen zo nodig kan worden gewijzigd.

- Zie voor meer informatie over hoeveel virtuele machines die u nodig hebt om uw clients te ondersteunen [prestaties en schaalbaarheid](#performance-and-scale).

- Zie de [Azure prijscategorie Rekenmachine](https://azure.microsoft.com/pricing/calculator/) om te bepalen, potentiële kosten.

    > [!NOTE]  
    > Virtuele machinekosten verschillen per regio.

#### <a name="outbound-data-transfer"></a>Uitgaande gegevensoverdracht

- Kosten zijn gebaseerd op gegevens die buiten Azure (uitgaande of downloaden). Alle gegevensstromen in Azure beschikbaar zijn (inkomend of uploaden). CMG gegevensoverdrachten buiten Azure omvatten beleid bij de client, clientmeldingen en clientantwoorden doorgestuurd door de CMG naar de site. Deze antwoorden zijn inventarisrapporten, statusberichten en status van naleving.  

- Sommige communicatie achtergrond zelfs zonder alle clients die communiceren met een CMG, zorgt ervoor dat netwerkverkeer tussen de CMG en de lokale site.  

- Weergave de **uitgaande gegevensoverdracht (GB)** in de Configuration Manager-console. Zie voor meer informatie [clients op CMG controleren](/sccm/core/clients/manage/cmg/monitor-clients-cloud-management-gateway).  

- Zie de [Azure bandbreedte prijsinformatie](https://azure.microsoft.com/pricing/details/bandwidth/) om te bepalen, potentiële kosten. Prijzen voor gegevens is overdracht gelaagd. Hoe meer u gebruikt, hoe minder u betaalt per GB.  

- *Voor het schatten van uitsluitend*, ongeveer 100 300 MB per client per maand verwachten voor clients op internet. De schatting van het onderste is voor een standaardconfiguratie. De schatting van het bovenste is voor de configuratie van een agressievere client. Het werkelijke gebruik kan variëren afhankelijk van hoe het configureren van clientinstellingen.  

   > [!NOTE]  
   > Andere acties uitvoeren, zoals het implementeren van software-updates of toepassingen, neemt de hoeveelheid uitgaande gegevensoverdracht van Azure.

#### <a name="content-storage"></a>Inhoudsopslag

- Clients op Internet voor het ophalen van Microsoft software-update-inhoud via Windows Update zonder kosten. Niet-updatepakketten met Microsoft update-inhoud naar een cloud-distributiepunt distribueren, worden kosten anders de kosten voor opslag- en uitgaand.  

- Voor alle andere vereiste inhoud, zoals toepassingen of software van derden is bijgewerkt, moet u naar een cloud-gebaseerde distributiepunt distribueren. De CMG ondersteunt momenteel alleen het cloud-gebaseerde distributiepunt voor het verzenden van inhoud aan clients.  

- Zie voor meer informatie de kosten van het gebruik van [clouddistributiepunt](/sccm/core/plan-design/hierarchy/use-a-cloud-based-distribution-point#cost-of-using-cloud-based-distribution).  

#### <a name="other-costs"></a>Overige kosten

- Elke cloudservice heeft een dynamisch IP-adres. Elke afzonderlijke CMG maakt gebruik van een nieuwe dynamische IP-adres. Toevoegen van extra virtuele machines per CMG toeneemt niet deze adressen.  



## <a name="performance-and-scale"></a>Prestaties en schaalbaarheid

Zie voor meer informatie over CMG scale [grootte en schaalgetallen](/sccm/core/plan-design/configs/size-and-scale-numbers#bkmk_cmg).

Aan de hand van de volgende aanbevelingen kunnen u de CMG prestaties verbeteren:

- Configureer indien mogelijk de CMG, CMG connection point en de Configuration Manager-siteserver in dezelfde regio netwerk de latentie te verminderen.  

- De verbinding tussen de Configuration Manager-client en de CMG is momenteel niet bekend is met regio.  

- Maak ten minste twee CMG services en twee verbindingspunten CMG per site voor hoge beschikbaarheid van de service.  

- Schaal de CMG meer clients te ondersteunen door meer VM-exemplaren toe te voegen. De Azure load balancer bepaalt clientverbindingen met de service.  

- Maak meer CMG verbindingspunten verdelen over de lagen. De CMG distribueert het verkeer naar de verbindende CMG verbindingspunten round-robin toewijst.  

- Wanneer de CMG onder hoge belasting als gevolg van meer dan het aantal ondersteunde clients, nog steeds aanvragen worden verwerkt, maar er vertraging optreden.  


> [!Note]  
> Terwijl Configuration Manager geen vaste limiet van het aantal clients voor een verbindingspunt CMG heeft, beschikt Windows Server over een standaard maximale TCP dynamisch poortbereik van 16.384. Als u een Configuration Manager-site meer dan 16.384 clients met een enkele CMG verbindingspunt beheert, moet u de Windows Server-limiet verhogen. Alle clients onderhouden een kanaal voor clientmeldingen, waarin een poort geopend zijn op het verbindingspunt CMG. Zie voor meer informatie over het gebruik van de opdracht netsh om deze limiet te verhogen [Microsoft Support-artikel 929851](https://support.microsoft.com/help/929851).



## <a name="ports-and-data-flow"></a>Poorten en gegevensstroom

U hoeft niet te openen van poorten voor inkomend verkeer naar uw on-premises netwerk. Het serviceverbindingspunt en het verbindingspunt CMG initiëren alle communicatie met Azure en de CMG. Deze twee sitesysteemrollen moet verbinding kunnen maken van uitgaande verbindingen met de Microsoft cloud. Het service connection point implementeert en controleert de service in Azure, dus moet onlinemodus. Het verbindingspunt CMG verbindt met de CMG voor het beheren van communicatie tussen de sitesysteemrollen CMG en on-premises.

Het volgende diagram wordt een eenvoudige, conceptuele gegevensstroom voor de CMG: ![De gegevensstroom CMG](media/cmg-data-flow.png)
   1. Het service connection point maakt verbinding met Azure via HTTPS-poort 443. Hiermee verifieert met behulp van Azure AD of het Azure-beheercertificaat. Het service connection point implementeert de CMG in Azure. De CMG maakt de HTTPS-cloudservice met behulp van het certificaat voor serververificatie.  

   2. Het verbindingspunt CMG maakt verbinding met de CMG in Azure via TCP-TLS- of HTTPS. Deze de verbinding geopend houdt en maakt het kanaal voor toekomstige communicatie in twee richtingen.   

   3. De client verbinding maakt met de CMG via HTTPS-poort 443. Hiermee verifieert met behulp van Azure AD of het certificaat voor clientverificatie.  

   4. De CMG stuurt de clientcommunicatie via de bestaande verbinding met het verbindingspunt van de lokale CMG. U hoeft niet te openen van een binnenkomende firewall-poorten.  

   5. Het verbindingspunt CMG stuurt de clientcommunicatie naar het beheerpunt voor lokale en de software-updatepunt.  

### <a name="required-ports"></a>Vereiste poorten
Deze tabel bevat de vereiste netwerkpoorten en protocollen. De *Client* is het apparaat verbinding tot stand brengen, vereisen een uitgaande poort. De *Server* is het apparaat dat de verbinding van het vereisen van een binnenkomende poort accepteren. 

| Client  | Protocol | Poort  | Server  | Beschrijving  |
|---------|---------|---------|---------|---------|
| Serviceverbindingspunt     | HTTPS | 443        | Azure        | CMG-implementatie |
| Verbindingspunt CMG     |  TCP-TLS | 10140-10155        | CMG-service        | Protocol voor het bouwen van CMG kanaal voorkeur <sup>1</sup> |
| Verbindingspunt CMG     | HTTPS | 443        | CMG-service       | Terugvallen op het bouwen van CMG communicatiekanaal met slechts één VM-instantie<sup>2</sup> |
| Verbindingspunt CMG     |  HTTPS   | 10124-10139     | CMG-service       | Terugvallen op het bouwen van CMG communicatiekanaal met twee of meer VM-exemplaren<sup>3</sup> |
| Client     |  HTTPS | 443         | CMG        | Algemene clientcommunicatie |
| Verbindingspunt CMG      | HTTPS of HTTP | 443 of 80         | Beheerpunt</br>(versie 1706 of 1710) | Verkeer van de lokale poort is afhankelijk van de configuratie management |
| Verbindingspunt CMG      | HTTPS | 443      | Beheerpunt</br>(versie 1802) | Lokale verkeer moet HTTPS |
| Verbindingspunt CMG      | HTTPS of HTTP | 443 of 80         | Sitesysteemrollen toevoegen | Verkeer van de lokale poort is afhankelijk van de software-update-punt-configuratie |

<sup>1</sup> verbindingspunt van de CMG de eerste keer probeert een lange levensduur TCP-TLS verbinding maken met elke CMG VM-instantie. Deze verbinding maakt met het eerste exemplaar van de VM op poort 10140. De tweede VM-instantie gebruikt poort 10141, tot aan het zestiende op poort 10155. TCP-TLS-verbinding voert het beste, maar het ondersteunt niet de InternetProxy. Als het verbindingspunt CMG kan geen verbinding via TCP-TLS maken, dan terug naar HTTPS valt<sup>2</sup>.  

<sup>2</sup> als het verbindingspunt CMG kan geen verbinding met de CMG via TCP-TLS<sup>1</sup>, deze verbinding maakt met de load balancer van Azure-netwerk via HTTPS 443 slechts voor één VM-instantie.  

<sup>3</sup> als er twee of meer VM-instanties, het verbindingspunt CMG maakt gebruik van HTTPS 10124 de eerste VM-instantie niet HTTPS 443. Deze verbinding maakt met de tweede VM-instantie op HTTPS 10125, tot aan het zestiende op HTTPS-poort 10139.


### <a name="internet-access-requirements"></a>Vereisten voor internettoegang

CMG verbinding sitesysteem van het ondersteunt het gebruik van een webproxy. Zie voor meer informatie over het configureren van deze rol voor een proxy [ondersteuning voor proxyserver](/sccm/core/plan-design/network/proxy-server-support#to-set-up-the-proxy-server-for-a-site-system-server). Het verbindingspunt CMG is de verbinding met de volgende eindpunten vereist:  

- Specifieke Azure-eindpunten verschillen per omgeving afhankelijk van de configuratie. Configuration Manager slaat deze eindpunten in de sitedatabase. Query de **AzureEnvironments** tabel in SQL Server voor een overzicht van Azure-eindpunten.  

- ServiceManagementEndpoint (https://management.core.windows.net/)  

- StorageEndpoint (core.windows.net)  

- Token ophalen door de Configuration Manager-console en de client voor Azure AD: ActiveDirectoryEndpoint (https://login.microsoftonline.com/)  

- Voor Azure AD-gebruikersdetectie: AAD-grafiek eindpunt (https://graph.windows.net/)  



## <a name="next-steps"></a>Volgende stappen

- [Certificaten voor cloudbeheergateway](/sccm/core/clients/manage/cmg/certificates-for-cloud-management-gateway)
- [Beveiliging en privacy voor cloudbeheergateway](/sccm/core/clients/manage/cmg/security-and-privacy-for-cloud-management-gateway)
- [De cloud management gateway-grootte en schaal cijfers](/sccm/core/plan-design/configs/size-and-scale-numbers#bkmk_cmg)
- [Veelgestelde vragen over de cloud-management-gateway](/sccm/core/clients/manage/cmg/cloud-management-gateway-faq)
- [Een cloudbeheergateway instellen](/sccm/core/clients/manage/cmg/setup-cloud-management-gateway)
