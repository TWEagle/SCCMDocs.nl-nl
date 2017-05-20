---
title: Configuration Manager op Azure | Microsoft-documenten
description: Informatie over het gebruik van Configuration Manager op een Azure-omgeving.
ms.custom: na
ms.date: 03/27/2017
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.prod: configuration-manager
ms.technology:
- configmgr-other
ms.topic: article
ms.assetid: d24257d8-8136-47f4-8e0d-34021356dc37
caps.latest.revision: 2
author: Brenduns
ms.author: brenduns
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: dab5da5a4b5dfb3606a8a6bd0c70a0b21923fff9
ms.openlocfilehash: 5276ad999fc871496d79e6efff34d5edc6335380
ms.contentlocale: nl-nl
ms.lasthandoff: 05/17/2017

---
# <a name="configuration-manager-on-azure---frequently-asked-questions"></a>Configuration Manager op Azure - Frequently Asked Questions
*Van toepassing op: System Center Configuration Manager (huidige vertakking)*

De volgende vragen en antwoorden kunt u leert wanneer te gebruiken en het configureren van Configuration Manager op Microsoft Azure.

## <a name="general-questions"></a>Algemene vragen
### <a name="my-company-is-trying-to-move-as-many-physical-servers-as-possible-to-microsoft-azure-can-i-move-configuration-manager-servers-to-azure"></a>Mijn bedrijf wilt verplaatsen zoals veel fysieke servers mogelijk naar Microsoft Azure, kan dat ik Configuration Manager-servers verplaatsen naar Azure?
Dit is gewoon, ondersteund scenario.  Zie [ondersteuning voor virtualisatieomgevingen voor System Center Configuration Manager](/sccm/core/plan-design/configs/support-for-virtualization-environments).

### <a name="great-my-environment-requires-multiple-sites-should-all-child-primary-sites-be-in-azure-with-the-central-administration-site-or-on-premises-what-about-secondary-sites"></a>Geweldige! Mijn omgeving vereist meerdere sites. Alle onderliggende primaire sites moet in Azure met de centrale beheersite of on-premises? Wat gebeurt er secundaire sites?
Site-naar-site-communicatie (op basis van bestanden en databasereplicatie) voordelen van de afstand van wordt gehost in Azure. Alle client gerelateerde echter verkeer zou worden niet op siteservers en sitesystemen. Als u een snelle en betrouwbare netwerkverbinding tussen Azure en het intranet met onbeperkt gebruiken, is die als host fungeert voor uw infrastructuur in Azure een optie.

Echter, als u een plan gemeten gegevens en beschikbare bandbreedte of kosten van belang is, of de netwerkverbinding tussen Azure en het intranet is niet snel of kan onbetrouwbare, vervolgens moet plaatsen specifieke sites (en site-systemen) on-premises en gebruik vervolgens de bandbreedte-besturingselementen in Configuration Manager gebouwd.

### <a name="is-having-configuration-manager-in-azure-a-saas-scenario-software-as-a-service"></a>Heeft Configuration Manager in Azure een SaaS-scenario (Software als een Service)?
Nee, is het een IaaS (infrastructuur als een Service) omdat u uw Configuration Manager-infrastructuurservers in virtuele machines in Azure hosten.

### <a name="what-areas-should-i-pay-attention-to-when-considering-a-move-of-my-configuration-manager-infrastructure-to-azure"></a>Welke gebieden moeten ik op letten wanneer u een verplaatsing van de Configuration Manager-infrastructuur naar Azure?
Geweldige vraag hier worden de gebieden die het belangrijkst zijn wanneer deze beslissing, elk is verkend in een aparte sectie van dit onderwerp:
1.    Netwerken
2.    Beschikbaarheid
3.    Prestatie
4.    Kosten
5.    Gebruikerservaring

## <a name="networking"></a>Netwerken
### <a name="what-about-networking-requirements-should-i-use-expressroute-or-an-azure-vpn-gateway"></a>Wat gebeurt er met het netwerk vereisten, moet ik ExpressRoute of een Azure VPN-Gateway gebruiken?
Netwerken is heel belangrijk. Netwerksnelheden en latentie kunnen functionaliteit tussen de siteserver en externe site-systemen en alle communicatie van clients naar de sitesystemen beïnvloeden. We bevelen is het gebruik van ExpressRoute. Maar er is geen beperking Configuration Manager om te voorkomen dat u met de Azure VPN-Gateway. Lees zorgvuldig de vereisten van uw (de prestaties, patches, softwaredistributie, implementatie van besturingssystemen) van deze infrastructuur en vervolgens besluiten. Enkele overwegingen voor elke oplossing zijn onder andere:

 - **ExpressRoute** (aanbevolen)
  - Natuurlijke extensie voor uw datacenter (kunnen met elkaar verbinden meerdere datacenters)
  - Persoonlijke verbindingen tussen Azure-datacenters en uw infrastructuur
  - Ga niet via het openbare Internet
  - Biedt betrouwbaarheid, hoge snelheden, lage latentie en hoge beveiliging
  - Aanbiedingen maximaal 10 Gbps verbindingssnelheden en de opties voor onbeperkte plan
 - **VPN-Gateway**
  - Site-naar-site/punt-naar-site VPN-verbindingen
  - Verkeer gaat over het openbare Internet
  - Maakt gebruik van IP-beveiligingsbeleid (IPsec) en Internet Key Exchange (IKE)

### <a name="expressroute-has-many-different-options-like-unlimited-vs-metered-different-speed-options-and-premium-add-on-which-should-i-choose"></a>ExpressRoute heeft tal van opties zoals onbeperkt versus snelheid van internetverbinding met, verschillende opties en premium-invoegtoepassing. Die mij het beste?
De opties die u selecteert, is afhankelijk van het scenario dat u implementeert en hoeveel gegevens die u wilt distribueren. Kan de overdracht van gegevens van Configuration Manager worden beheerd tussen siteservers en distributiepunten, maar de site server-naar-site server-communicatie kan niet worden beheerd.   Bij het gebruik van een plan gemeten gegevens plaatsen specifieke sites (en site-systemen) on-premises en met behulp van [van Configuration Manager ingebouwde bandbreedteregelingen](/sccm/core/plan-design/hierarchy/fundamental-concepts-for-content-management) kunt u de kosten van het gebruik van Azure regelen.

### <a name="what-about-installation-requirements-like-active-directory-domains-do-i-still-need-to-join-my-site-servers-to-an-active-directory-domain"></a>Wat u over de installatievereisten voor van Active Directory-domeinen leuk? Moet ik mijn siteservers toevoegen aan een Active Directory-domein?
Ja. Als u Azure, naar de [ondersteunde configuraties](/sccm/core/plan-design/configs/supported-configurations) blijven hetzelfde, met inbegrip van Active Directory-vereisten voor het installeren van Configuration Manager.

### <a name="i-understand-the-need-to-join-my-site-servers-to-an-active-directory-domain-but-can-i-use-azure-active-directory"></a>Ik begrijp dat moet mijn siteservers toevoegen aan een Active Directory-domein, maar kan ik de Azure Active Directory gebruiken?
Nee, Azure Active Directory wordt niet ondersteund op dit moment. Uw siteservers nog steeds moeten lid zijn van een [Windows Active Directory-domein](/sccm/core/plan-design/configs/support-for-active-directory-domains).



## <a name="availability"></a>Beschikbaarheid
### <a name="one-of-the-reasons-i-am-moving-infrastructure-to-azure-is-the-promise-of-high-availability-can-i-take-advantage-of-high-availability-options-like-azure-vm-availability-sets-for-vms-that-i-will-use-for-configuration-manager"></a>Een van de redenen dat ik ben infrastructuur verplaatsen naar Azure is de CTP van hoge beschikbaarheid. Kan ik profiteren van maximale Beschikbaarheidsopties zoals Azure VM beschikbaarheidssets voor virtuele machines die ik gebruik voor Configuration Manager?
Ja! Azure VM beschikbaarheidssets kunnen worden gebruikt voor redundante sitesysteemrollen zoals de distributiepunten of beheerpunten.

U kunt ze ook gebruiken voor de Configuration Manager-siteservers. Bijvoorbeeld, zich centrale beheersites en primaire sites in de dezelfde beschikbaarheidsset die kunt u ervoor zorgen dat ze niet op hetzelfde moment opnieuw opgestart.

### <a name="how-can-i-make-my-database-highly-available-can-i-use-azure-sql-database-or-do-i-have-to-use-microsoft-sql-server-in-a-vm"></a>Hoe kan ik mijn database maximaal beschikbaar maken? Kan ik Azure SQL Database gebruiken? Of moet ik Microsoft SQL Server in een virtuele machine gebruiken?
U moet Microsoft SQL Server gebruiken in een virtuele machine. Configuration Manager biedt geen ondersteuning voor Azure SQL Server op dit moment. Maar u kunt functies zoals AlwaysOn Availability Groups voor de SQL-server. [AlwaysOn Availability Groups](/sccm/core/servers/deploy/configure/sql-server-alwayson-for-a-highly-available-site-database) worden aanbevolen en officiële vanaf versie 1602 van Configuration Manager worden ondersteund.

### <a name="can-i-use-azure-load-balancers-with-site-system-roles-like-management-points--or-software-update-points"></a>Kan ik Azure netwerktaakverdelers gebruiken met sitesysteemrollen zoals beheerpunten of software-updatepunten
Terwijl Configuration Manager niet met Azure netwerktaakverdelers getest is als de functionaliteit transparant voor de toepassing is, mag het geen negatieve gevolgen op normale bewerkingen.


## <a name="performance"></a>Prestatie
### <a name="what-factors-affect-performance-in-this-scenario"></a>Welke factoren van invloed op prestaties in dit scenario?
[Azure VM-grootte en het type](https://azure.microsoft.com/documentation/articles/virtual-machines-size-specs), virtuele machine van Azure-schijven (premium opslag wordt aanbevolen, met name voor SQL Server), netwerken latentie en snelheid zijn de belangrijkste gebieden.

### <a name="so-tell-me-more-about-azure-virtual-machines-what-size-vms-should-i-use"></a>Het is dus meer informatie over virtuele machines in Azure; de grootte van virtuele machines moet ik gebruiken?
In het algemeen uw computercapaciteit (CPU en geheugen) moet voldoen aan de [aanbevolen hardware voor System Center Configuration Manager](/sccm/core/plan-design/configs/recommended-hardware). Maar er zijn enkele verschillen tussen reguliere computerhardware en de virtuele Azure-machines, met name als het gaat om de schijven deze gebruik van virtuele machines.  Welke grootte van virtuele machines die u gebruikt, is afhankelijk van de grootte van uw omgeving, maar hier volgen enkele aanbevelingen:
- Voor implementaties met een grootte van alle belangrijke productie aangeraden "**S**" klasse virtuele Azure-machines. Dit is omdat ze van opslagschijven Premium gebruikmaken kunnen.  Niet "S" klasse VMs gebruik blob-opslag en in het algemeen niet voldoet aan de prestatievereisten nodig is voor een acceptabele productie-ervaring.
- Meerdere Premium opslagschijven moeten worden gebruikt voor hogere schaal en striped in de console Windows Schijfbeheer voor het maximumaantal IOPS.  
- Wordt u aangeraden beter of meerdere premium tijdens de implementatie van uw eerste site (zoals P30 in plaats van P20 en 2xP30 in een striped volume in plaats van 1xP30) schijven. Klik, als uw site later in VM-grootte vanwege de extra belasting als verschaffen moet, u kunt profiteren van de aanvullende CPU en geheugen dat voorziet in een grotere VM-grootte. U hebt dan ook schijven al in de plaats waar kan profiteren van de aanvullende IOPS doorvoer waarmee de grotere VM-grootte.



De volgende tabellen worden de eerste voorgestelde schijf tellingen gebruiken die op primaire en centrale beheersites voor installaties van verschillende grootte:

**CO-locaties sitedatabase** -primaire of centrale beheersite met de sitedatabase op de siteserver:

| Bureaublad-Clients    |Aanbevolen VM-grootte|Aanbevolen schijven|
|--------------------|-------------------|-----------------|
|**Maximaal 25k**       |   DS4_V2          |2xP30 (striped)  |
|**25k tot 50k**      |   DS13_V2         |2xP30 (striped)  |
|**50k tot 100k**     |   DS14_V2         |3xP30 (striped)  |


**Externe sitedatabase** -primaire of centrale beheersite met de sitedatabase op een externe server:

| Bureaublad-Clients    |Aanbevolen VM-grootte|Aanbevolen schijven |
|--------------------|-------------------|------------------|
|**Maximaal 25k**       | Siteserver: F4S </br>-Databaseserver: DS12_V2 | Siteserver: 1xP30 </br>-Databaseserver: 2xP30 (striped)  |
|**25k tot 50k**      | Siteserver: F4S </br>-Databaseserver: DS13_V2 | Siteserver: 1xP30 </br>-Databaseserver: 2xP30 (striped)   |
|**50k tot 100k**     | Siteserver: F8S </br>-Databaseserver: DS14_V2 | Siteserver: 2xP30 (striped)   </br>-Databaseserver: 3xP30 (striped)   |

De volgende toont een voorbeeldconfiguratie voor 50k tot 100k-clients op DS14_V2 met 3xP30 schijven in een striped volume afzonderlijke logische volumes voor de Configuration Manager installeren en databasebestanden:  ![VM)-schijven](media/vm_disks.png)  



## <a name="user-experience"></a>Gebruikerservaring
### <a name="you-mention-that-user-experience-is-one-of-the-main-areas-of-importance-why-is-that"></a>Gebruikerservaring is een van de belangrijkste gebieden van belang zijn, wordt vermeld waarom is dat?
De beslissingen die u maakt voor netwerken, beschikbaarheid, prestaties en waar u uw Configuration Manager-siteservers rechtstreeks uw gebruikers kunnen beïnvloeden. We ervan overtuigd dat een verplaatsen naar Azure moet transparant voor uw gebruikers zodat ze een wijziging in hun dagelijkse interacties met Configuration Manager niet optreden.

### <a name="ok-i-get-it-i-plan-to-install-a-single-stand-alone-primary-site-on-an-azure-virtual-machine-and-i-want-to-make-sure-my-costs-are-low-should-i-place-remote-site-systems-like-management-points-distribution-points-and-software-update-points-on-azure-virtual-machines-as-well-or-on-premises"></a>Oké, krijgen ik. Ik één enkele zelfstandige primaire site installeren op een virtuele machine van Azure plannen en ik wil dat mijn kosten laag zijn. Moet ik (extern) site-systemen (zoals beheerpunten, distributiepunten en software-updatepunten) op virtuele machines in Azure evenals of on-premises plaatsen?
Met uitzondering van de communicatie van de siteserver naar een distributiepunt kan deze server naar server-communicatie in een site op elk gewenst moment kan worden uitgevoerd en gebruik niet mechanismen voor het beheren van het gebruik van netwerkbandbreedte. U kunt de communicatie tussen sitesystemen controleren, eventuele kosten in verband met deze communicatie beschouwd.

Zijn andere factoren ook netwerksnelheden en latentie. Functionaliteit tussen de siteserver en externe sitesystemen als ook alle communicatie van clients naar de sitesystemen kunnen van invloed zijn trage of onbetrouwbare netwerken. Het aantal beheerde clients die gebruikmaken van een opgegeven sitesysteem, evenals de functies waarmee u actief moet ook worden overwogen.
In het algemeen kunt u het normale advies met betrekking tot WAN-koppelingen en site-systemen als uitgangspunt gebruikmaken. De netwerkdoorvoer die u selecteert en ontvangt tussen Azure en het intranet worden in het ideale geval consistent zijn met een WAN die goed is verbonden met een snel netwerk.

### <a name="what-about-content-distribution-and-content-management-should-standard-distribution-points-be-in-azure-or-on-premises-and-should-i-use-branchcache-or-pull-distribution-points-on-premises-or-should-i-make-exclusive-use-of-cloud-distribution-points"></a>Wat gebeurt er distributie van inhoud en inhoudsbeheer? Standaard distributiepunten moet in Azure of op locatie, en moet ik BranchCache gebruiken of lokale pull-distributiepunten? Of maak ik exclusief gebruik maken van Clouddistributiepunten?
De aanpak voor inhoudsbeheer is veel hetzelfde als die voor siteservers en sitesystemen.
- Als u een snelle en betrouwbare netwerkverbinding tussen Azure en het intranet met onbeperkt gebruiken, die als host fungeert standaarddistributiepunten in Azure mogelijk een optie.
-  Als u een abonnement en de bandbreedte kosten voor gemeten gegevens aan belangrijk is of de netwerkverbinding tussen Azure en het intranet is niet snel of mag onbetrouwbare, en vervolgens kunt u andere benaderingen overwegen. Hieronder vallen standard zoeken of pull-distributiepunten zowel lokale als BranchCache gebruiken. Het gebruik van cloud-gebaseerde distributiepunten is ook een optie, maar er zijn enkele beperkingen op de inhoudstypen die wordt ondersteund (bijvoorbeeld geen ondersteuning voor software-updatepakketten).

> [!NOTE]
>  Als de PXE-ondersteuning is vereist, moet u on-premises distributiepunten (standard of pull) gebruiken om te reageren op aanvragen voor het starten. [WDS is momenteel niet ondersteund als u wilt uitvoeren op virtuele Azure-machines](https://technet.microsoft.com/library/hh831764(v=ws.11).aspx).


### <a name="while-i-am-ok-with-the-limitations-of-cloud-based-distribution-points-i-dont-want-to-put-my-management-point-into-a-dmz-even-though-that-is-needed-to-support-my-internet-based-clients-do-i-have-any-other-options"></a>Terwijl ik OK met de beperkingen van cloud-gebaseerde distributiepunten ben, wil ik mijn beheerpunt in een DMZ geplaatst, zelfs als dat nodig is voor de Internet-gebaseerde clients ondersteunt. Heb ik andere opties?
Ja! Met de Configuration Manager versie-1610 geïntroduceerd we de [Cloud Management Gateway](/sccm/core/clients/manage/manage-clients-internet#cloud-management-gateway) als een functie voorlopige versie. (Deze functie komt eerst in de technische voorbeeldversie 1606 als de [Cloud proxyservice](/sccm/core/get-started/capabilities-in-technical-preview-1606#a-namecloudproxyacloud-proxy-service-for-managing-clients-on-the-internet)).

De **Cloud Management Gateway** biedt een eenvoudige manier voor het beheren van Configuration Manager-clients op het Internet. De service die wordt geïmplementeerd op Microsoft Azure en een Azure-abonnement vereist, maakt verbinding met uw on-premises Configuration Manager-infrastructuur met behulp van een nieuwe rol met de naam van het cloud-gateway-connector wordt gemaakt. Nadat deze is geïmplementeerd en geconfigureerd, clients toegang lokale sitesysteemfuncties van Configuration Manager ongeacht tot of ze zijn verbonden met de interne particulier netwerk of op het Internet.

U kunt beginnen met behulp van de cloud management gateway in uw omgeving en stuur ons feedback voor dit verbeteren. Zie voor meer informatie over de functies voor voorlopige [gebruikmaken van de functies van updates pre-release](/sccm/core/servers/manage/install-in-console-updates#a-namebkmkprereleasea-use-pre-release-features-from-updates).

### <a name="i-also-heard-that-you-have-another-new-feature-called-peer-cache-introduced-as-a-pre-release-feature-in-version-1610-is-that-different-than-branchcache-which-one-should-i-choose"></a>Ik gehoord ook dat er een andere nieuwe functie geïntroduceerd als een functie voorlopige versie 1610 Peer-Cache. Verschilt van die BranchCache? Welke mij het beste?
Ja, volledig verschillende. [Peer-Cache](/sccm/core/plan-design/hierarchy/client-peer-cache) is een native Configuration Manager-technologie van 100% waarop BranchCache een functie van Windows is. Beide kunnen nuttig zijn voor u; Een broadcast BranchCache gebruikt om de vereiste inhoud vinden dat Peer Cache maakt gebruik van Configuration Managers normale verdeling werkstroom en de rand van de instellingen.

U kunt een client een Peer-Cache-bron worden configureren. Klik, wanneer beheerpunten clients informatie over de locatie van de inhoudsbron, ze vindt u informatie over de distributiepunten en enkele Peer Cache-bron met de inhoud die client vereist.


## <a name="cost"></a>Kosten
### <a name="ok-tell-me-a-bit-about-the-cost-will-this-be-a-cost-effective-solution-for-me"></a>OK laat me weten iets over de kosten. Is dit een kostenbesparende oplossing voor mij?
Moeilijk te zeggen sinds elke omgeving verschilt. De beste aan uw omgeving met Microsoft Azure prijzen Rekenmachine is: https://azure.microsoft.com/pricing/calculator/

## <a name="additional-resources"></a>Aanvullende bronnen
**Grondbeginselen:** http://azure.microsoft.com/documentation/articles/fundamentals-introduction-to-azure/

**Typen Azure VM-Machine:**
 - Azure Machine grootten: https://azure.microsoft.com/documentation/articles/virtual-machines-size-specs/  
 - VM prijzen: http://azure.microsoft.com/pricing/details/virtual-machines/  
 - Prijzen voor opslag: http://azure.microsoft.com/pricing/details/storage/

**Prestatieoverwegingen schijf:**    
 - Premium schijf Inleiding: http://azure.microsoft.com/blog/2014/12/11/introducing-premium-storage-high-performance-storage-for-azure-virtual-machine-workloads/  
 - Dieper Premium Schijfinfo: http://azure.microsoft.com/documentation/articles/storage-premium-storage-preview-portal/   
 - Handige verzameling grafieken voor maximale grootten en die gericht is op voor opslag: https://azure.microsoft.com/documentation/articles/storage-scalability-targets/  
 - Een andere inleiding + sommige leuk uber nerd-gegevens op de werking van Premium opslag achter de behandelt: http://azure.microsoft.com/blog/2015/04/16/azure-premium-storage-now-generally-available-2/

**Beschikbaarheid:**
 - Azure IaaS bedrijfstijd SLA van: https://azure.microsoft.com/support/legal/sla/virtual-machines/v1_0/  
 - Beschikbaarheidssets uitgelegd: https://azure.microsoft.com/documentation/articles/virtual-machines-manage-availability/

**Verbinding:**
 - Snelle route vs. Azure VPN: http://azure.microsoft.com/blog/2014/06/10/expressroute-or-virtual-network-vpn-whats-right-for-me/
 - Snelle Route prijzen: http://azure.microsoft.com/pricing/details/expressroute/
 - Meer informatie over snelle Route: http://azure.microsoft.com/documentation/articles/expressroute-introduction/

 

