---
title: Configuration Manager op Azure
description: Informatie over het gebruik van Configuration Manager op een Azure-omgeving.
ms.custom: na
ms.date: 03/27/2017
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.prod: configuration-manager
ms.technology: configmgr-other
ms.topic: article
ms.assetid: d24257d8-8136-47f4-8e0d-34021356dc37
caps.latest.revision: "2"
author: aczechowski
ms.author: aaroncz
manager: angrobe
ms.openlocfilehash: d73ab50e5fc9472a977951f6c2d5bbd3fd408c39
ms.sourcegitcommit: ca9d15dfb1c9eb47ee27ea9b5b39c9f8cdcc0748
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 01/04/2018
---
# <a name="configuration-manager-on-azure---frequently-asked-questions"></a>Configuration Manager in Azure: Frequently Asked Questions
*Van toepassing op: System Center Configuration Manager (huidige vertakking)*

De volgende vragen en antwoorden kunt u leert wanneer te gebruiken en het configureren van Configuration Manager op Microsoft Azure.

## <a name="general-questions"></a>Algemene vragen
### <a name="my-company-is-trying-to-move-as-many-physical-servers-as-possible-to-microsoft-azure-can-i-move-configuration-manager-servers-to-azure"></a>Mijn bedrijf wilt verplaatsen zoals veel fysieke servers mogelijk bij Microsoft Azure, kan dat ik Configuration Manager-servers verplaatsen naar Azure?
Zeker, dit is een ondersteund scenario.  Zie [ondersteuning voor virtualisatieomgevingen voor System Center Configuration Manager](/sccm/core/plan-design/configs/support-for-virtualization-environments).

### <a name="great-my-environment-requires-multiple-sites-should-all-child-primary-sites-be-in-azure-with-the-central-administration-site-or-on-premises-what-about-secondary-sites"></a>Goed gedaan. Mijn omgeving moet meerdere sites. Alle onderliggende primaire sites moet in Azure met de centrale beheersite of een on-premises? Hoe zit het met secundaire sites?
Site-naar-site-communicatie (op basis van bestanden en databasereplicatie) voordelen biedt voor in de buurt van wordt gehost in Azure. Echter clientgerelateerde alle verkeer extern van siteservers en sitesystemen zou zijn. Als u een snelle en betrouwbare netwerkverbinding tussen Azure en het intranet met een onbeperkte gegevens-plan gebruiken, is die als host fungeert voor uw infrastructuur in Azure een optie.

Echter, als u een plan datalimiet gebruiken en de beschikbare bandbreedte of kosten een probleem is of de netwerkverbinding tussen Azure en het intranet is geen snelle of onbetrouwbare kan worden, overweeg vervolgens te plaatsen specifieke sites (en sitesystemen) on-premises en gebruik vervolgens de bandbreedte besturingselementen in Configuration Manager gebouwd.

### <a name="is-having-configuration-manager-in-azure-a-saas-scenario-software-as-a-service"></a>Heeft Configuration Manager in Azure een SaaS-scenario (Software als een Service)?
Nee, is een IaaS (infrastructuur als een Service) omdat u uw Configuration Manager-infrastructuurservers in virtuele machines in Azure worden gehost.

### <a name="what-areas-should-i-pay-attention-to-when-considering-a-move-of-my-configuration-manager-infrastructure-to-azure"></a>Welke gebieden moet ik letten wanneer u overweegt een verplaatsing van mijn Configuration Manager-infrastructuur naar Azure?
Goede vraag hier worden de gebieden die het belangrijkst zijn wanneer deze beslissing, elk is verkend in een aparte sectie van dit onderwerp:
1.  Netwerken
2.  Beschikbaarheid
3.  Prestatie
4.  Kosten
5.  Gebruikerservaring

## <a name="networking"></a>Netwerken
### <a name="what-about-networking-requirements-should-i-use-expressroute-or-an-azure-vpn-gateway"></a>Hoe zit het netwerkvereisten, moet ik ExpressRoute of een Azure VPN-Gateway gebruiken?
Netwerken wordt een zeer belangrijke beslissing. Netwerksnelheden en latentie kunnen functionaliteit tussen de siteserver en externe sitesystemen en alle clientcommunicatie naar de sitesystemen beïnvloeden. Onze aanbeveling is het gebruik van ExpressRoute. Maar er geldt geen beperking voor Configuration Manager om te voorkomen dat u met behulp van Azure VPN-Gateway. U moet zorgvuldig door uw vereisten (prestaties, patches, softwaredistributie, implementatie van besturingssystemen) van deze infrastructuur en breng vervolgens uw beslissing. Enkele overwegingen voor elke oplossing zijn onder andere:

 - **ExpressRoute** (aanbevolen)
  - Natuurlijke extensie voor uw datacenter (kunt met elkaar verbinden meerdere datacenters)
  - Particuliere verbindingen tussen Azure-datacenters en uw infrastructuur
  - Niet kan worden verstuurd via het openbare Internet
  - Biedt betrouwbaarheid, hoge snelheden, lagere latentie en hoge beveiliging
  - Aanbiedingen tot snelheden 10 Gbps en opties voor onbeperkte gegevens-plan
 - **VPN-Gateway**
  - Site-naar-site/punt-naar-site VPN-verbindingen
  - Verkeer wordt via het openbare Internet
  - Maakt gebruik van Internet Protocol Security (IPsec) en Internet Key Exchange (IKE)

### <a name="expressroute-has-many-different-options-like-unlimited-vs-metered-different-speed-options-and-premium-add-on-which-should-i-choose"></a>ExpressRoute heeft veel verschillende opties zoals onbeperkte versus snelheid gecontroleerde, verschillende opties en premium-invoegtoepassing. Waarmee moet ik kiezen?
De opties die u selecteert, is afhankelijk van het scenario dat u implementeert en hoeveel gegevens die u wilt distribueren. De overdracht van gegevens van Configuration Manager tussen siteservers en distributiepunten kan worden beheerd, maar site server-naar-site server-communicatie niet worden beheerd.   Wanneer u een plan datalimiet plaatsen specifieke sites (en sitesystemen) on-premises en met behulp van [van Configuration Manager ingebouwde bandbreedte besturingselementen](/sccm/core/plan-design/hierarchy/fundamental-concepts-for-content-management) kan helpen bij het beheren van de kosten van het gebruik van Azure.

### <a name="what-about-installation-requirements-like-active-directory-domains-do-i-still-need-to-join-my-site-servers-to-an-active-directory-domain"></a>Hoe zit het met vereisten voor de installatie, zoals Active Directory-domeinen? Moet ik mijn siteservers toevoegen aan een Active Directory-domein?
Ja. Wanneer u naar Azure verplaatst de [ondersteunde configuraties](/sccm/core/plan-design/configs/supported-configurations) hetzelfde blijven, met inbegrip van Active Directory-vereisten voor het installeren van Configuration Manager.

### <a name="i-understand-the-need-to-join-my-site-servers-to-an-active-directory-domain-but-can-i-use-azure-active-directory"></a>Ik begrijp de noodzaak mijn siteservers toevoegen aan een Active Directory-domein, maar kan ik Azure Active Directory gebruiken?
Nee, Azure Active Directory wordt niet ondersteund op dit moment. Uw siteservers nog steeds moeten lid zijn van een [Windows Active Directory-domein](/sccm/core/plan-design/configs/support-for-active-directory-domains).



## <a name="availability"></a>Beschikbaarheid
### <a name="one-of-the-reasons-i-am-moving-infrastructure-to-azure-is-the-promise-of-high-availability-can-i-take-advantage-of-high-availability-options-like-azure-vm-availability-sets-for-vms-that-i-will-use-for-configuration-manager"></a>Een van de redenen dat ik ben infrastructuur verplaatsen naar Azure is de belofte van hoge beschikbaarheid. Kan ik profiteren van de opties voor hoge beschikbaarheid zoals Azure VM beschikbaarheidssets voor virtuele machines die ik gebruik voor Configuration Manager?
Ja! Beschikbaarheidssets van Azure VM kunnen worden gebruikt voor redundante sitesysteemrollen zoals distributiepunten of beheerpunten.

U kunt ze ook gebruiken voor de Configuration Manager-siteservers. Bijvoorbeeld: centrale beheersites en primaire sites kunnen worden in dezelfde beschikbaarheidsset die u ervoor zorgen kunt dat ze niet op hetzelfde moment opnieuw opgestart.

### <a name="how-can-i-make-my-database-highly-available-can-i-use-azure-sql-database-or-do-i-have-to-use-microsoft-sql-server-in-a-vm"></a>Hoe kan ik mijn database maximaal beschikbaar maken? Kan ik Azure SQL Database gebruiken? Of heb ik Microsoft SQL Server op een virtuele machine gebruiken?
U moet Microsoft SQL Server gebruiken in een virtuele machine. Configuration Manager biedt geen ondersteuning voor Azure SQL Server op dit moment. Maar u kunt functies zoals AlwaysOn-beschikbaarheidsgroepen gebruiken voor uw SQL-server. [AlwaysOn Availability Groups](/sccm/core/servers/deploy/configure/sql-server-alwayson-for-a-highly-available-site-database) worden aanbevolen en officieel ondersteund vanaf versie 1602 van Configuration Manager.

### <a name="can-i-use-azure-load-balancers-with-site-system-roles-like-management-points--or-software-update-points"></a>Kan ik Azure load balancers met sitesysteemrollen zoals beheerpunten of software-updatepunten gebruiken?
Terwijl Configuration Manager niet met Azure load balancers geldt getest is als de functionaliteit transparant voor de toepassing is, mag het geen negatieve gevolgen op normale bewerkingen.


## <a name="performance"></a>Prestatie
### <a name="what-factors-affect-performance-in-this-scenario"></a>Welke factoren van invloed op prestaties in dit scenario?
[Azure VM-grootte en het type](https://azure.microsoft.com/documentation/articles/virtual-machines-size-specs), Azure VM-schijven (premium-opslag wordt aanbevolen, met name voor SQL Server), netwerken latentie en snelheid zijn de belangrijkste gebieden.

### <a name="so-tell-me-more-about-azure-virtual-machines-what-size-vms-should-i-use"></a>Dus meer informatie over virtuele machines in Azure; welke de grootte van virtuele machines moet ik gebruiken?
In het algemeen de rekencapaciteit (CPU en geheugen) moet voldoen aan de [aanbevolen hardware voor System Center Configuration Manager](/sccm/core/plan-design/configs/recommended-hardware). Maar er zijn een aantal verschillen tussen reguliere computerhardware en de Azure VM's, vooral wanneer het gaat om de schijven het gebruik van deze virtuele machines.  Welke grootte van virtuele machines die u gebruikt, is afhankelijk van de grootte van uw omgeving, maar hier volgen enkele aanbevelingen:
- Voor de productie-implementaties van elke grootte aanzienlijke aangeraden '**S**' klasse virtuele Azure-machines. Dit is omdat ze van Premium-opslag-schijven gebruikmaken kunnen.  Niet "S" klasse VMs gebruik blob-opslag en in het algemeen niet voldoet aan de prestatie-eisen die nodig zijn voor een acceptabele productie-ervaring.
- Meerdere schijven met Premium-opslag moeten worden gebruikt voor een hogere schaal en striped opgeslagen in de console Windows Schijfbeheer bij maximumaantal IOPS.  
- Wordt u aangeraden beter of meerdere premium-schijven tijdens de implementatie van uw eerste site (zoals P30 in plaats van P20 en 2xP30 in striped volumes in plaats van 1xP30). Klik, als uw site later mogelijk uitbreiden in VM-grootte vanwege de extra belasting moet, kunt u profiteren van de aanvullende CPU en geheugen dat voorziet in een grotere VM-grootte. Ook hebt u schijven al in de locatie die u kunt profiteren van de aanvullende IOPS doorvoer waarmee de grotere VM-grootte.



De volgende tabellen worden de eerste voorgestelde schijf tellingen gebruikmaken van op primaire en centrale beheersites voor installaties van verschillende grootte:

**CO-locaties sitedatabase** -primaire of centrale beheersite met de sitedatabase op de siteserver:

| Bureaublad-Clients    |Aanbevolen VM-grootte|Aanbevolen schijven|
|--------------------|-------------------|-----------------|
|**Maximaal 25k**       |   DS4_V2          |2xP30 (striped)  |
|**25-k tot 50k**      |   DS13_V2         |2xP30 (striped)  |
|**k van 50-100 kB**     |   DS14_V2         |3xP30 (striped)  |


**Externe sitedatabase** -primaire of centrale beheersite met de sitedatabase op een externe server:

| Bureaublad-Clients    |Aanbevolen VM-grootte|Aanbevolen schijven |
|--------------------|-------------------|------------------|
|**Maximaal 25k**       | Siteserver: F4S </br>Database-server: DS12_V2 | Siteserver: 1xP30 </br>Database-server: 2xP30 (striped)  |
|**25-k tot 50k**      | Siteserver: F4S </br>Database-server: DS13_V2 | Siteserver: 1xP30 </br>Database-server: 2xP30 (striped)   |
|**k van 50-100 kB**     | Siteserver: F8S </br>Database-server: DS14_V2 | Siteserver: 2xP30 (striped)   </br>Database-server: 3xP30 (striped)   |

Hieronder ziet u een van de voorbeeldconfiguratie voor clients van 50-k tot 100k op DS14_V2 met 3xP30 schijven in een striped volume afzonderlijke logische volumes voor de Configuration Manager installeren en databasebestanden: ![VM)-schijven](media/vm_disks.png)  



## <a name="user-experience"></a>Gebruikerservaring
### <a name="you-mention-that-user-experience-is-one-of-the-main-areas-of-importance-why-is-that"></a>U aangeven dat gebruikerservaring een van de belangrijkste gebieden van belang is is, waarom is dat?
De beslissingen die u maakt voor netwerken, beschikbaarheid, prestaties en waar u uw Configuration Manager-siteservers rechtstreeks uw gebruikers kunnen beïnvloeden. We zijn ervan overtuigd dat verplaatsen naar Azure moet transparant voor uw gebruikers zodat er is geen sprake van een wijziging in hun dagelijkse interacties met Configuration Manager.

### <a name="ok-i-get-it-i-plan-to-install-a-single-stand-alone-primary-site-on-an-azure-virtual-machine-and-i-want-to-make-sure-my-costs-are-low-should-i-place-remote-site-systems-like-management-points-distribution-points-and-software-update-points-on-azure-virtual-machines-as-well-or-on-premises"></a>OK klikt, verschijnt het. Ik wil een enkele zelfstandige primaire site installeren op een virtuele machine van Azure en ik wil ervoor zorgen dat mijn kosten laag zijn. Moet ik (extern) sitesystemen (zoals beheerpunten, distributiepunten en software-updatepunten) op virtuele machines in Azure ook of on-premises plaatsen?
Met uitzondering van de communicatie van de siteserver naar een distributiepunt, is deze server naar server-communicatie in een site op elk gewenst moment kan optreden, en geen gebruikgemaakt van mechanismen voor het beheren van het gebruik van netwerkbandbreedte. U kunt de communicatie tussen sitesystemen controleren, eventuele kosten die zijn gekoppeld aan deze communicatie beschouwd.

Zijn andere factoren ook netwerksnelheden en latentie. Functionaliteit tussen de siteserver en externe sitesystemen als ook alle clientcommunicatie naar de sitesystemen kunnen van invloed zijn trage of onbetrouwbare netwerken. Het aantal beheerde clients die gebruikmaken van een opgegeven sitesysteem, evenals de functies die u actief gebruikt moet ook worden overwogen.
In het algemeen kunt u de normale richtlijnen met betrekking tot WAN-verbindingen en sitesystemen als uitgangspunt gebruikmaken. De netwerkdoorvoer die u selecteert en ontvangt tussen Azure en het intranet worden in het ideale geval consistent zijn met een WAN die goed is verbonden met een snel netwerk.

### <a name="what-about-content-distribution-and-content-management-should-standard-distribution-points-be-in-azure-or-on-premises-and-should-i-use-branchcache-or-pull-distribution-points-on-premises-or-should-i-make-exclusive-use-of-cloud-distribution-points"></a>Hoe zit het distribueren van inhoud en inhoudbeheer? Standaard distributiepunten moet in Azure of on-premises, en moet ik gebruiken BranchCache of lokale pull-distributiepunten? Of moet ik ervoor exclusief gebruik maken van Clouddistributiepunten?
De benadering voor inhoudsbeheer is grotendeels hetzelfde als voor siteservers en sitesystemen.
- Als u een snelle en betrouwbare netwerkverbinding tussen Azure en het intranet met een onbeperkte gegevens-plan gebruiken, kan die als host fungeert voor standaarddistributiepunten in Azure een optie worden.
-  Als u een datalimiet plannings- en bandbreedte kosten is een probleem of de netwerkverbinding tussen Azure en uw intranet is niet snel of onbetrouwbare, kan worden en vervolgens u andere methoden kunt. Deze omvatten zoeken naar standard of pull-distributiepunten zowel lokale als met behulp van BranchCache. Het gebruik van cloud-gebaseerde distributiepunten is ook een optie, maar er zijn enkele beperkingen op de inhoudstypen die wordt ondersteund (bijvoorbeeld geen ondersteuning voor software-updatepakketten).

> [!NOTE]
>  Als u PXE-ondersteuning is vereist, moet u on-premises distributiepunten (standard of pull) gebruiken om te reageren op aanvragen voor het starten. [WDS wordt momenteel niet ondersteund als u wilt uitvoeren op Azure Virtual machines](https://technet.microsoft.com/library/hh831764(v=ws.11).aspx).


### <a name="while-i-am-ok-with-the-limitations-of-cloud-based-distribution-points-i-dont-want-to-put-my-management-point-into-a-dmz-even-though-that-is-needed-to-support-my-internet-based-clients-do-i-have-any-other-options"></a>Terwijl ik OK met de beperkingen van cloud-gebaseerde distributiepunten ben, wil ik mijn beheerpunt in een Perimeternetwerk geplaatst, zelfs als die nodig zijn ter ondersteuning van mijn clients op Internet. Heb ik andere opties?
Ja! Met de Configuration Manager versie-1610 geïntroduceerd we de [Cloud Management Gateway](/sccm/core/clients/manage/manage-clients-internet#cloud-management-gateway) als een functie van de voorlopige versie. (Deze functie komt eerst in de Technical Preview-versie 1606 als de [Cloudproxyservice](/sccm/core/get-started/capabilities-in-technical-preview-1606#a-namecloudproxyacloud-proxy-service-for-managing-clients-on-the-internet)).

De **Cloud Management Gateway** biedt een eenvoudige manier voor het beheren van Configuration Manager-clients op Internet. De service, die wordt geïmplementeerd voor Microsoft Azure en een Azure-abonnement is vereist, maakt verbinding met uw on-premises Configuration Manager-infrastructuur met behulp van een nieuwe rol met de naam van het cloud-gateway connector beheerpunt. Nadat deze is geïmplementeerd en geconfigureerd, clients toegang lokale sitesysteemrollen van Configuration Manager ongeacht tot hebben of ze bent verbonden met het interne particuliere netwerk of op het Internet.

U kunt aan de slag met de cloud-management-gateway in uw omgeving en feedback te dit beter te maken. Zie voor meer informatie over de functies van evaluatieversies [functies van evaluatieversies van updates gebruiken](/sccm/core/servers/manage/install-in-console-updates#a-namebkmkprereleasea-use-pre-release-features-from-updates).

### <a name="i-also-heard-that-you-have-another-new-feature-called-peer-cache-introduced-as-a-pre-release-feature-in-version-1610-is-that-different-than-branchcache-which-one-should-i-choose"></a>Ik ook gehoord dat er een andere nieuwe functie geïntroduceerd als onderdeel van de voorlopige versie 1610-Peer-Cache. Verschilt van die BranchCache? Welk account moet ik kiezen?
Ja, compleet andere. [Peer-Cache](/sccm/core/plan-design/hierarchy/client-peer-cache) is een systeemeigen Configuration Manager-technologie van 100% waarop BranchCache een functie van Windows is. Beide kunnen nuttig zijn voor u; BranchCache maakt gebruik van een uitzending vereiste inhoud vinden dat Configuration Managers-normale distributie werkstroom en grens groepsinstellingen maakt gebruik van Peer-Cache.

U kunt een client configureren voor een Peer-Cache-bron. Vervolgens wanneer beheerpunten clients informatie over de locatie van de inhoudsbron, ze bieden informatie over de distributiepunten en een Peer-Cache-bronnen die de inhoud bevatten die client vereist.


## <a name="cost"></a>Kosten
### <a name="ok-tell-me-a-bit-about-the-cost-will-this-be-a-cost-effective-solution-for-me"></a>OK meer iets over de kosten. Is dit een rendabele oplossing voor mij?
Moeilijk te spreken sinds elke omgeving verschilt. De beste is aan de kosten van uw omgeving met Microsoft Azure prijscalculator: https://azure.microsoft.com/pricing/calculator/

## <a name="additional-resources"></a>Aanvullende bronnen
**Grondbeginselen:** http://azure.microsoft.com/documentation/articles/fundamentals-introduction-to-azure/

**Typen Azure VM-machines:**
 - Azure Machine grootten: https://azure.microsoft.com/documentation/articles/virtual-machines-size-specs/  
 - VM-prijzen: http://azure.microsoft.com/pricing/details/virtual-machines/  
 - Prijzen voor Storage: http://azure.microsoft.com/pricing/details/storage/

**Aandachtspunten voor prestaties bij schijf:**    
 - Premium schijf intro: http://azure.microsoft.com/blog/2014/12/11/introducing-premium-storage-high-performance-storage-for-azure-virtual-machine-workloads/  
 - Premium Schijfinfo diepere: http://azure.microsoft.com/documentation/articles/storage-premium-storage-preview-portal/   
 - Handige verzameling grafieken voor maximale grootten en Perf gericht voor opslag: https://azure.microsoft.com/documentation/articles/storage-scalability-targets/  
 - Een andere Intro + sommige cool uber-zo'n expert gegevens over de werking van Premium-opslag achter de schermen: http://azure.microsoft.com/blog/2015/04/16/azure-premium-storage-now-generally-available-2/

**Beschikbaarheid:**
 - Azure IaaS bedrijfstijd SLA van: https://azure.microsoft.com/support/legal/sla/virtual-machines/v1_0/  
 - Beschikbaarheidssets uitgelegd: https://azure.microsoft.com/documentation/articles/virtual-machines-manage-availability/

**Verbinding:**
 - Express route-tegenover. Azure VPN: http://azure.microsoft.com/blog/2014/06/10/expressroute-or-virtual-network-vpn-whats-right-for-me/
 - Express Route prijzen: http://azure.microsoft.com/pricing/details/expressroute/
 - Meer informatie over Express Route: http://azure.microsoft.com/documentation/articles/expressroute-introduction/

 
