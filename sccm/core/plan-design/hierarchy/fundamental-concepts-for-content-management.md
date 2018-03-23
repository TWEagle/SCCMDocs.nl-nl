---
title: Basisprincipes voor inhoudsbeheer
titleSuffix: Configuration Manager
description: Hulpprogramma's en opties in Configuration Manager gebruiken voor het beheren van de inhoud die u implementeert.
ms.custom: na
ms.date: 03/22/2018
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: c201be2a-692c-4d67-ac95-0a3afa5320fe
caps.latest.revision: ''
caps.handback.revision: ''
author: aczechowski
ms.author: aaroncz
manager: dougeby
ms.openlocfilehash: 0595e34d096b2d7f6450b3255bae03ae3aa57862
ms.sourcegitcommit: 11bf4ed40ed0cbb10500cc58bbecbd23c92bfe20
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 03/23/2018
---
# <a name="fundamental-concepts-for-content-management-in-system-center-configuration-manager"></a>Basisconcepten voor inhoudsbeheer in System Center Configuration Manager

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*

Configuration Manager ondersteunt een robuust systeem van hulpprogramma's en opties voor het beheren van de inhoud die u als toepassingen, pakketten, software-updates en implementaties van een besturingssysteem implementeert. Configuration Manager slaat de inhoud op siteservers en distributiepunten. Deze inhoud is een grote hoeveelheid netwerkbandbreedte vereist wanneer deze wordt overgedragen tussen locaties. Voor het effectief plannen en de infrastructuur voor inhoudsbeheer gebruiken, is het raadzaam dat u de beschikbare opties en configuraties begrijpt. Overweeg vervolgens hoe ze te gebruiken om te aan te passen aan uw netwerkomgeving en de behoeften van de implementatie van inhoud.  

> [!TIP]    
> Zie voor meer informatie over het proces van de distributie van inhoud en voor hulp bij het opsporen en oplossen van algemene inhoudsdistributie [begrip en inhoudsdistributie oplossen in Microsoft Configuration Manager ](https://support.microsoft.com/help/4000401/content-distribution-in-mcm).

De volgende onderwerpen worden belangrijke concepten voor inhoudsbeheer. Wanneer een concept aanvullende of complexe informatie vereist, worden er koppelingen naar de informatie weergegeven.



## <a name="accounts-used-for-content-management"></a>Accounts die worden gebruikt voor inhoudsbeheer  
 De volgende accounts kunnen worden gebruikt met inhoudsbeheer:  

-   **Netwerktoegangsaccount**: Verbinding maken met een distributiepunt en toegang tot inhoud door clients gebruikt. Standaard wordt het computeraccount eerst geprobeerd.  

     Dit account wordt ook gebruikt door pull-distributiepunten om inhoud te downloaden vanaf een brondistributiepunt in een extern forest.  

-   **Pakkettoegangsaccount**: Configuration Manager verleent standaard toegang tot inhoud op een distributiepunt aan de algemene toegangsaccounts gebruikers en beheerders. U kunt echter aanvullende machtigingen configureren om de toegang te beperken.   

-   **Multicastverbindingsaccount**: Gebruikt voor implementaties van het besturingssysteem.  

Zie voor meer informatie over deze accounts [accounts voor toegang tot inhoud beheren](../../../core/plan-design/hierarchy/manage-accounts-to-access-content.md).



## <a name="bandwidth-throttling-and-scheduling"></a>Bandbreedtebeperking en planning  
 Bandbreedtebeperking en planning zijn opties waarmee u kunt bepalen wanneer inhoud van een siteserver naar distributiepunten wordt gedistribueerd. Deze mogelijkheden zijn vergelijkbaar met, maar niet direct gerelateerd aan de bandbreedteregeling voor een bestandsreplicatie van site-naar-site.  

 Zie voor meer informatie [netwerkbandbreedte beheren](/sccm/core/plan-design/hierarchy/manage-network-bandwidth).



## <a name="binary-differential-replication"></a>Binaire differentiële replicatie  
 Binaire differentiële replicatie (BDR) is een vereiste voor distributiepunten. Dit wordt soms ook wel replicatie van verschillen. Wanneer u updates voor inhoud die u eerder hebt geïmplementeerd naar andere sites of naar externe distributiepunten distribueert, wordt automatisch BDR gebruikt om te beperken van de bandbreedte.  

 BDR minimaliseert de netwerkbandbreedte die wordt gebruikt voor het verzenden van updates voor gedistribueerde inhoud. Het opnieuw verzendt alleen de nieuwe of gewijzigde inhoud in plaats van het verzenden van de volledige set van inhoudsbestanden telkens wanneer die u deze bestanden wijzigen.  

 Als BDR wordt gebruikt, wordt in Configuration Manager de wijzigingen die zich voordoen aan bronbestanden voor elke set van inhoud die u eerder distribueerde identificeert.  

-   Wanneer bestanden in de broninhoud wijzigen, maakt de site een nieuwe incrementele versie van de inhoudsset. Vervolgens worden alleen de gewijzigde bestanden gerepliceerd naar de doelsites en distributiepunten. Een bestand wordt beschouwd als gewijzigd als u hernoemd of verplaatst, of als u de inhoud van het bestand gewijzigd. Als u een één stuurprogrammabestand voor een stuurprogrammapakket dat u eerder naar verschillende sites vervangt distribueerde, wordt bijvoorbeeld alleen het gewijzigde stuurprogrammabestand gerepliceerd.  

-   Configuration Manager ondersteunt tot vijf incrementele versies van een inhoudsset voordat het de volledige inhoudsset opnieuw verzendt. De volgende wijziging in de inhoudsset na de vijfde update zorgt ervoor dat de site voor het maken van een nieuwe versie van de inhoudsset. Configuration Manager verdeelt vervolgens de nieuwe versie van de inhoud die is ingesteld op de voorgaande set en eventuele aanvullende versies vervangt. Nadat de nieuwe inhoudsset is gedistribueerd, worden volgende incrementele wijzigingen aan de bronbestanden opnieuw gerepliceerd door BDR.  

BDR wordt ondersteund tussen elke bovenliggende en onderliggende site in een hiërarchie. BDR wordt ondersteund binnen een site tussen de siteserver en de normale distributiepunten. Echter, pull-distributiepunten en cloud-gebaseerde distributiepunten ondersteunen niet BDR om over te dragen van inhoud. Pull-distributiepunten ondersteunen bestandsniveau delta's, het overbrengen van nieuwe bestanden, maar niet blokken binnen een bestand.

Toepassingen gebruiken altijd binaire differentiële replicatie. BDR is optioneel voor pakketten en is niet standaard ingeschakeld. Als u wilt gebruiken BDR voor pakketten, deze functie inschakelen voor elk pakket. Selecteer de optie **binaire differentiële replicatie inschakelen** als u maakt of een pakket bewerken.   



## <a name="branchcache"></a>BranchCache  
 [BranchCache](/windows-server/networking/branchcache/branchcache) is een technologie voor Windows. Clients die BranchCache ondersteunen en een implementatie die u voor Vertakkingscache configureert, hebben gedownload fungeren als inhoudsbron voor andere clients BranchCache is ingeschakeld.  

 U hebt bijvoorbeeld een distributiepunt waarop WindowsServer 2012 of hoger wordt uitgevoerd en is geconfigureerd als een BranchCache-server. Wanneer de eerste BranchCache-clients inhoud van deze server aanvraagt, wordt de client die inhoud wordt gedownload en opgeslagen in het cachegeheugen.  

- Deze client vervolgens maakt de inhoud beschikbaar voor aanvullende BranchCache-clients in hetzelfde subnet die ook de inhoud in cache.  
- Andere clients in hetzelfde subnet hoeft te downloaden van inhoud van het distributiepunt.  
- De inhoud wordt gedistribueerd over meerdere clients voor toekomstige overdrachten.  



## <a name="delivery-optimization"></a>Leveringsoptimalisatie
<!-- 1324696 -->
U grensgroepen Configuration Manager gebruiken om te definiëren en inhoudsdistributie regelen tussen het bedrijfsnetwerk en naar externe kantoren. [Windows leveringsoptimalisatie](/windows/deployment/update/waas-delivery-optimization) is een cloud-gebaseerde, peer-to-peer-technologie voor het delen van inhoud tussen Windows 10-apparaten. Vanaf versie 1802, leveringsoptimalisatie voor het gebruik van uw grensgroepen bij het delen van inhoud tussen peers configureren. Clientinstellingen toepassen de grens groeps-id als de levering van optimalisatie-id op de client. Wanneer de client met de cloudservice leveringsoptimalisatie communiceert, gebruikt deze id peers met de gewenste inhoud vinden. Zie voor meer informatie [leveringsoptimalisatie](/sccm/core/clients/deploy/about-client-settings#delivery-optimization) clientinstellingen.



## <a name="peer-cache"></a>Peer-Cache
Client-peer-cache helpt u bij het beheren van de implementatie van inhoud voor clients op externe locaties. Peer-cache is een ingebouwde Configuration Manager-oplossing waarmee clients inhoud te delen met andere clients rechtstreeks vanuit het lokale cachegeheugen.

Nadat u clientinstellingen waarmee peer-cache voor een verzameling implementeert, fungeren leden van deze verzameling als een peer-inhoudsbron voor andere clients in dezelfde grensgroep.

Zie voor meer informatie [Peer-Cache voor Configuration Manager-clients](/sccm/core/plan-design/hierarchy/client-peer-cache).



## <a name="windows-pe-peer-cache"></a>Windows PE-peer-cache
Wanneer u een nieuw besturingssysteem met Configuration Manager implementeert, kunnen computers waarop de takenreeks Windows PE-peer-cache gebruiken. Ze downloaden inhoud vanaf een peer-cachebron in plaats van vanaf een distributiepunt. Dit gedrag helpt te beperken van WAN-verkeer in filiaalscenario's waarin er geen lokaal distributiepunt.

Zie voor meer informatie [Windows PE-peer-cache](../../../osd/get-started/prepare-windows-pe-peer-cache-to-reduce-wan-traffic.md).



## <a name="client-locations"></a>Clientlocaties  
 Op de volgende locaties wordt door clients inhoud opgehaald:  

-   **Intranet** (on-premises):  

    -   Distributiepunten kunnen HTTP of HTTPs gebruiken.  

    -   Gebruik alleen een clouddistributiepunt voor terugval wanneer on-premises distributiepunten niet beschikbaar zijn.  

-   **Internet**:  

    -   Vereist dat distributiepunten HTTPS accepteren.  

    -   Kan een cloud-gebaseerde distributiepunt gebruiken als terugval.  

-   **Werkgroep**:  

    -   Vereist dat distributiepunten HTTPS accepteren.  

    -   Kan een cloud-gebaseerde distributiepunt gebruiken als terugval.  



## <a name="content-library"></a>Inhoudsbibliotheek  
 De Inhoudsbibliotheek is de single instance store van inhoud in Configuration Manager. Deze bibliotheek vermindert de grootte van inhoud die u distribueert.  

- Meer informatie over de [Inhoudsbibliotheek](../../../core/plan-design/hierarchy/the-content-library.md).
- Gebruik de [Inhoudsbibliotheek opschoonprogramma](/sccm/core/plan-design/hierarchy/content-library-cleanup-tool) inhoud die niet meer gekoppeld aan een toepassing te verwijderen.  



## <a name="distribution-points"></a>Distributiepunten  
 Configuration Manager gebruikt distributiepunten voor het opslaan van bestanden die vereist zijn voor software uit te voeren op clientcomputers. Clients moeten toegang hebben tot ten minste één distributiepunt waarvan ze de bestanden voor inhoud die u implementeert kunnen downloaden.  

 Het algemene (niet-specifieke) distributiepunt wordt doorgaans een standaarddistributiepunt genoemd. Er zijn twee varianten van het standaarddistributiepunt die speciale aandacht krijgen:  

-   **Pull-distributiepunt**: Een variant van een distributiepunt waar het distributiepunt die inhoud bij een ander distributiepunt (een brondistributiepunt ophaalt). Dit proces is vergelijkbaar met de wijze waarop clients inhoud vanaf distributiepunten downloaden. Pull-distributiepunten kunt u problemen met de netwerkbandbreedte die zich voordoen wanneer de siteserver rechtstreeks inhoud naar elk distributiepunt distribueren moet voorkomen. [Een pull-distributiepunt](/sccm/core/plan-design/hierarchy/use-a-pull-distribution-point).

-   **Cloud-gebaseerde distributiepunt**: Een variant van een distributiepunt dat geïnstalleerd op Microsoft Azure. [Informatie over het gebruik van een cloud-gebaseerde distributiepunt](../../../core/plan-design/hierarchy/use-a-cloud-based-distribution-point.md).  


Standaarddistributiepunten bieden ondersteuning voor een bereik van configuraties en functies:  

- Gebruik beveiligingsmaatregelen zoals **planningen** of **bandbreedtebeperking** om u te helpen bij het beheren van deze overdracht.  
- Gebruik van andere opties, waaronder **vooraf geplaatste inhoud**, en **pull-distributiepunten** beperken en het verbruik van het netwerk beheren. 
- **BranchCache**, **peer-cache**, en **leveringsoptimalisatie** peer-to-peer-technologieën om de netwerkbandbreedte die wordt gebruikt wanneer u inhoud implementeert te beperken.  
- Er zijn verschillende configuraties voor OS-implementaties, zoals **[PXE](../../../osd/get-started/prepare-site-system-roles-for-operating-system-deployments.md#BKMK_PXEDistributionPoint)** en  **[Multicast](../../../osd/get-started/prepare-site-system-roles-for-operating-system-deployments.md#BKMK_DPMulticast)**
- Opties voor **mobiele apparaten**   
  
  
Cloud-gebaseerde en pull-distributiepunten ondersteunen veel van dezelfde configuraties, maar hebben beperkingen die specifiek voor elke distributiepuntvariant zijn.  



## <a name="distribution-point-groups"></a>Distributiepuntgroepen  
 Distributiepuntengroepen zijn logische groeperingen van distributiepunten die de inhoudsdistributie kunnen vereenvoudigen.  

 Zie voor meer informatie [distributiepuntgroepen beheren](../../../core/servers/deploy/configure/install-and-configure-distribution-points.md#bkmk_manage).



## <a name="distribution-point-priority"></a>Prioriteit van het distributiepunt  
 De prioriteitswaarde voor het distributiepunt is gebaseerd op het tijdsbestek dat de overdracht van eerdere implementaties naar dat distributiepunt in beslag nam.  

-   Deze waarde is een zelfregulerende. Het ingesteld op elk distributiepunt bij Configuration Manager meer inhoud snel naar meer distributiepunten kan overdragen.  

-   Wanneer u inhoud naar meerdere distributiepunten tegelijkertijd of naar een distributiepuntgroep distribueert, verzendt de site de inhoud eerst naar de server met de hoogste prioriteit. Vervolgens verzendt het dezelfde inhoud naar een distributiepunt met een lagere prioriteit.  

-   Prioriteit van het distributiepunt is geen vervanging voor de distributieprioriteit voor pakketten. Pakket prioriteit blijft de beslissende factor van wanneer de site verschillende inhoud verzendt.  

U hebt bijvoorbeeld een pakket met een pakket met hoge prioriteit. U distribueren deze naar een server met een lage distributiepuntprioriteit. Dit pakket met hoge prioriteit draagt altijd vóór een pakket met een lagere prioriteit. De prioriteit van het pakket geldt ook als de site lagere prioriteit pakketten naar servers met hogere distribution point prioriteiten distribueert.

De hoge prioriteit van het pakket zorgt ervoor dat de Configuration Manager die inhoud naar distributiepunten distribueert voordat er pakketten met een lagere prioriteit worden verzonden.  

> [!NOTE]  
>  Pull-distributiepunten maken ook gebruik van een prioriteitsconcept om de volgorde van de eigen brondistributiepunten vast te leggen.  
>   
>  -   De distributiepuntprioriteit voor inhoudsoverdrachten naar de server is verschillend van de prioriteit die pull-distributiepunten gebruiken. Pull-distributiepunten gebruiken hun prioriteit wanneer ze naar inhoud vanaf een brondistributiepunt zoeken.  
>  -   Zie voor meer informatie [een pull-distributiepunt](/sccm/core/plan-design/hierarchy/use-a-pull-distribution-point).  



## <a name="fallback"></a>Terugval  
 Verschillende dingen zijn gewijzigd met Configuration Manager Current Branch in de manier waarop dat clients een distributiepunt die inhoud, inclusief terugval is gevonden. 

Clients die niet kunnen vinden van inhoud vanaf een distributiepunt dat is gekoppeld aan hun huidige grensgroep terugvallen voor het gebruik van de inhoudsbron locaties die zijn gekoppeld aan de grensgroepen neighbor. Om te worden gebruikt voor terugval, moet een neighbor grensgroep een gedefinieerde relatie hebben met de huidige grensgroep van de client. Deze relatie bevat een geconfigureerde tijd dat moet worden gewacht voordat een client die lokaal inhoud niet kan vinden inhoudsbronnen van de grensgroep neighbor als deel van de zoekactie bevat.

De concepten van voorkeursdistributiepunten punten worden niet meer gebruikt en de instellingen voor **alternatieve bronlocaties voor inhoud toestaan** zijn niet langer beschikbaar of afgedwongen.

Zie voor meer informatie [grensgroepen](/sccm/core/servers/deploy/configure/define-site-boundaries-and-boundary-groups#boundary-groups).

<!--
**Version 1511, 1602, and 1606**   
Fallback settings are related to the use of **preferred distribution points** and to content source locations that are used by clients.

-   By default, clients only download content from a preferred distribution point (one that is associated with the client's boundary groups).  

-   However, when a distribution point is configured with **Allow clients to use this site system as a fallback source location for content**, that distribution point is only offered as a valid content source to any client that can't get a deployment from one of its preferred distribution points.  

For information about the different content location and fallback scenarios, see [Content source location scenarios](../../../core/plan-design/hierarchy/content-source-location-scenarios.md). For information about boundary groups, see [Boundary groups for versions 1511,1602, and 1606](/sccm/core/servers/deploy/configure/boundary-groups-for-1511-1602-and-1606).
-->



## <a name="network-bandwidth"></a>Netwerkbandbreedte  
 Om te beheren, de hoeveelheid netwerkbandbreedte die wordt gebruikt wanneer u inhoud distribueert, kunt u de volgende opties:  

-   **Vooraf geplaatste inhoud**: Overgebracht inhoud naar een distributiepunt zonder de inhoud distribueren via het netwerk.  

-   **Planning en bandbreedtebeperking**: Configuraties die u helpen bepalen wanneer en hoe inhoud wordt gedistribueerd naar distributiepunten.  

Zie voor meer informatie [netwerkbandbreedte beheren](/sccm/core/plan-design/hierarchy/manage-network-bandwidth).



## <a name="network-connection-speed-to-content-source"></a>Netwerkverbindingssnelheid naar de inhoudsbron  
 Verschillende dingen zijn gewijzigd met Configuration Manager Current Branch in de manier waarop dat clients een distributiepunt die inhoud vinden. Deze wijzigingen omvatten de netwerksnelheid naar de inhoudsbron. 

Verbindingssnelheden netwerk die een distributiepunt definieert verwijst als **snel** of **langzaam** niet meer worden gebruikt. In plaats daarvan elk sitesysteem dat is gekoppeld aan een grensgroep wordt behandeld hetzelfde.

Zie voor meer informatie [grensgroepen](/sccm/core/servers/deploy/configure/define-site-boundaries-and-boundary-groups#boundary-groups).

<!--
**Version 1511, 1602, and 1606**   
 You can configure the network connection speed of each distribution point in a boundary group:  

-   Clients use this value when they connect to the distribution point.

-   By default, the network connection speed is configured as **Fast**, but it can also be set as **Slow**.  

-   The **network connection speed**, along with the configuration of a deployment, determine if a client can download content from a distribution point when the client is in an associated boundary group  

For information about the different content location and fallback scenarios, see [Content source location scenarios](../../../core/plan-design/hierarchy/content-source-location-scenarios.md). For information about boundary groups, see [Boundary groups for versions 1511,1602, and 1606](/sccm/core/servers/deploy/configure/boundary-groups-for-1511-1602-and-1606).
-->



## <a name="on-demand-content-distribution"></a>Inhoudsdistributie op aanvraag  
 Inhoudsdistributie op aanvraag is een optie voor afzonderlijke toepassingen en pakketten implementaties. Deze optie kunt inhoudsdistributie op aanvraag naar voorkeurs servers.  

-   Schakel deze instelling voor een implementatie door inschakelen: **Distribueer de inhoud voor dit pakket naar voorkeursdistributiepunten**.  

-   Wanneer deze optie is ingeschakeld voor een implementatie en een client probeert die inhoud op te vragen, maar de inhoud niet beschikbaar is op een van de voorkeursdistributiepunten van de client is, distribueert Configuration Manager automatisch die inhoud naar de voorkeursdistributiepunten van de client.  

-   Hoewel dit Configuration Manager automatisch de om inhoud te distribueren naar voorkeursdistributiepunten van die client activeert, kan de client die inhoud van andere distributiepunten verkrijgen voordat de voorkeursdistributiepunten voor de client de implementatie ontvangen. Wanneer dit gebeurt, kan de inhoud vervolgens meer aanwezig zijn op dat distributiepunt voor gebruik door de volgende client die deze implementatie zoekt.  

Zie voor meer informatie [grensgroepen](/sccm/core/servers/deploy/configure/define-site-boundaries-and-boundary-groups#boundary-groups).

<!--
If you use version 1511, 1602, or 1606, see  [Content source location scenarios](../../../core/plan-design/hierarchy/content-source-location-scenarios.md) for information about the different content location and fallback scenarios.
-->



## <a name="package-transfer-manager"></a>Package transfer manager  
 Package transfer manager is het siteserveronderdeel dat inhoud naar distributiepunten op andere computers overdraagt.  

 Zie voor meer informatie [Package transfer manager](../../../core/plan-design/hierarchy/package-transfer-manager.md).  



<!--
## Preferred distribution point  
 A preferred distribution point includes any distribution points that are associated with a client's current boundary groups.  

 You have the option to associate each distribution point with one or more boundary groups:  

-   This association helps the client identify distribution points from which it can download content.  
-   By default, clients can only download content from a preferred distribution point.  


For more information:
 - If you use version 1610 or later, see [Boundary groups](/sccm/core/servers/deploy/configure/define-site-boundaries-and-boundary-groups#boundary-groups).
 - If you use version 1511, 1602, or 1606, see [Content source location scenarios](../../../core/plan-design/hierarchy/content-source-location-scenarios.md).
-->



## <a name="prestage-content"></a>Inhoud vooraf plaatsen  
 Voorbereiden van inhoud is een proces waarbij inhoud naar een distributiepunt wordt overgedragen zonder het distribueren van de inhoud via het netwerk.  

 Zie voor meer informatie [netwerkbandbreedte beheren](/sccm/core/plan-design/hierarchy/manage-network-bandwidth).
