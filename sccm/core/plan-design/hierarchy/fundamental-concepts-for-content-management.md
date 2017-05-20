---
title: Beheer de grondbeginselen van inhoud | Microsoft-documenten
description: Gebruik hulpprogramma&quot;s en in System Center Configuration Manager-opties voor het beheren van de inhoud die u implementeert.
ms.custom: na
ms.date: 05/04/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: c201be2a-692c-4d67-ac95-0a3afa5320fe
caps.latest.revision: 28
caps.handback.revision: 0
author: Brenduns
ms.author: brenduns
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 212628639300e9c361f7cee61b3df6b1cb6874ce
ms.openlocfilehash: f73dde64e0e8a0fc49f45b3afb3b8f00c926a820
ms.contentlocale: nl-nl
ms.lasthandoff: 05/17/2017


---
# <a name="fundamental-concepts-for-content-management-in-system-center-configuration-manager"></a>Basisconcepten voor inhoudsbeheer in System Center Configuration Manager

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*

System Center Configuration Manager biedt ondersteuning voor een systeem krachtige hulpprogramma's en opties voor het beheren van de inhoud die u zoals toepassingen, pakketten, software-updates en implementaties van besturingssystemen implementeert.  

De inhoud die u implementeert, wordt opgeslagen op beide siteservers en op distribution point-sitesysteemservers. Deze inhoud kan een grote hoeveelheid bandbreedte vereisen wanneer het wordt overgebracht tussen locaties. Effectief plannen en infrastructuur voor inhoudsbeheer gebruiken, wordt aangeraden dat u begrijpt de beschikbare opties en configuraties en vervolgens overwegen hoe gebruikt ze om aan te passen aan uw netwerkomgeving en implementatie van inhoud moet.  

> [!TIP]    
> U kunt meer informatie over het proces voor het distribueren van inhoud en het vinden van help bij het opsporen en oplossen van problemen met algemene distributie van inhoud. Zie [te begrijpen en oplossen van problemen in Configuration Manager-distributiepunt inhoud](https://support.microsoft.com/help/4000401/content-distribution-in-mcm) op support.microsoft.com.

Hieronder vindt u belangrijke concepten voor inhoudsbeheer. Wanneer een concept aanvullende of complexe informatie vereist, worden er koppelingen naar de informatie weergegeven.

## <a name="accounts-used-for-content-management"></a>Accounts die worden gebruikt voor inhoudsbeheer  
 De volgende accounts kunnen worden gebruikt met inhoudsbeheer:  

-   **Account voor toegang tot het netwerk**: Gebruikt door clients verbinding maken met een distributiepunt en toegang tot inhoud. Standaard wordt het computeraccount eerst geprobeerd.  

     Dit account wordt ook gebruikt door pull-distributiepunten inhoud ophalen van een brondistributiepunt in een extern forest.  

-   **Account voor toegang tot het pakket**: Configuration Manager hebben standaard toegang tot inhoud op de algemene toegangsaccounts gebruikers en beheerders een distributiepunt. U kunt echter aanvullende machtigingen configureren om de toegang te beperken.   

-   **Multicastverbindingsaccount**: Gebruikt voor implementaties van besturingssystemen.  

Zie voor meer informatie over deze accounts [beheer van accounts voor toegang tot inhoud](../../../core/plan-design/hierarchy/manage-accounts-to-access-content.md).

## <a name="bandwidth-throttling-and-scheduling"></a>Bandbreedtebeperking en planning  
 Bandbreedtebeperking en planning zijn opties waarmee u kunt bepalen wanneer inhoud van een siteserver naar distributiepunten wordt gedistribueerd. Dit is vergelijkbaar met, maar niet direct gerelateerd aan, de bandbreedteregeling voor een bestandsreplicatie van site naar site.  

 Zie voor meer informatie [beheer van netwerkbandbreedte](/sccm/core/plan-design/hierarchy/manage-network-bandwidth).

## <a name="binary-differential-replication"></a>Binaire differentiële replicatie  
 Een vereiste voor distributiepunten, binaire differentiële replicatie (BDR) die wordt ook wel replicatie van verschillen genoemd, wordt automatisch gebruikt voor het gebruik van netwerkbandbreedte beperken wanneer u bij het distribueren van updates voor inhoud die u eerder hebt geïmplementeerd naar andere sites of naar externe distributiepunten.  

 BDR minimaliseert de netwerkbandbreedte die wordt gebruikt om updates te verzenden voor gedistribueerde inhoud door alleen de nieuwe of gewijzigde inhoud opnieuw te verzenden in plaats van de volledige set van inhoudsbestanden wanneer er een wijziging aan die bestanden wordt doorgevoerd.  

 Bij gebruik van binaire differentiële replicatie identificeert Configuration Manager de wijzigingen die zich voordoen aan bronbestanden voor elke set van inhoud die eerder is gedistribueerd.  

-   Wanneer bestanden in de broninhoud wijzigen, wordt Configuration Manager maakt een nieuwe incrementele versie van de inhoudsset en worden alleen de gewijzigde bestanden gerepliceerd naar doelsites en distributiepunten. Een bestand wordt beschouwd als gewijzigd als deze zijn gewijzigd of verplaatst, of als de inhoud van het bestand is gewijzigd. Als u bijvoorbeeld één stuurprogrammabestand vervangt voor een implementatiepakket van een besturingssysteem dat u eerder distribueerde naar verschillende sites, dan wordt alleen het gewijzigde stuurprogrammabestand gerepliceerd naar die doelsites.  

-   Configuration Manager ondersteunt tot vijf incrementele versies van een inhoudsset voordat het de volledige inhoudsset opnieuw verzendt. Na de vijfde update zorgt de volgende wijziging aan de inhoudsset ervoor zorgt dat Configuration Manager voor het maken van een nieuwe versie van de inhoudsset. Configuration Manager distribueert vervolgens de nieuwe versie van de inhoud die is ingesteld op de vorige set en alle incrementele versies ervan te vervangen. Nadat de nieuwe inhoudsset is gedistribueerd worden volgende incrementele wijzigingen aan de bronbestanden opnieuw gerepliceerd door binaire differentiële replicatie.  


BDR wordt ondersteund tussen elke bovenliggende en onderliggende site in een hiërarchie. Binnen een site BDR ondersteund tussen de siteserver en de normale distributiepunten. Echter, pull-distributiepunten en cloud-gebaseerde distributiepunten ondersteunen geen binaire differentiële replicatie om over te dragen van inhoud. Pull-distributiepunten ondersteunen bestandsniveau delta's, het overbrengen van nieuwe bestanden, maar niet blokken binnen een bestand.

Toepassingen gebruiken altijd binaire differentiële replicatie. Binaire differentiële replicatie is optioneel voor pakketten. Standaard is deze optie niet ingeschakeld. U moet deze functie inschakelen voor elk pakket om binaire differentiële replicatie voor pakketten te gebruiken. U kunt dit doen door de optie **Binaire differentiële replicatie inschakelen** te selecteren wanneer u een nieuw pakket maakt of wanneer u het tabblad **Gegevensbron** van de pakketeigenschappen bewerkt.  

## <a name="branchcache"></a>BranchCache  
 Een Windows-technologie waarmee clients bieden ondersteuning voor BranchCache en hebt gedownload van een implementatie die is geconfigureerd voor de vertakking uit de Cache fungeert als een inhoudsbron met andere clients BranchCache is ingeschakeld.  

 Als bijvoorbeeld de eerste clientcomputer met BranchCache inhoud aanvraagt bij een distributiepunt waarop Windows Server 2012 wordt uitgevoerd en is geconfigureerd als een BrancheCache-server, wordt de inhoud door de clientcomputer gedownload en opgeslagen in het cachegeheugen.  

-   Clientcomputer kunt vervolgens de inhoud beschikbaar maken voor extra BranchCache-clients in hetzelfde subnet die de inhoud wordt eveneens cache.  

-   Zo moeten volgende clients op hetzelfde subnet de inhoud niet van het distributiepunt downloaden en wordt de inhoud over meerdere clients voor toekomstige overdrachten gedistribueerd.  

## <a name="peer-cache"></a>Peercache
Client-Peercache kunt vanaf versie 1610, u de implementatie van inhoud naar clients op externe locaties beheren. Peercache is een ingebouwde Configuration Manager-oplossing waarmee clients inhoud te delen met andere clients rechtstreeks vanuit de lokale cache.

Nadat u clientinstellingen die Peer-Cache op een verzameling inschakelen hebt geïmplementeerd, kunnen leden van deze verzameling fungeren als een peer-inhoudsbron voor andere clients in dezelfde grensgroep.

Zie voor meer informatie [Peercache voor Configuration Manager-clients](/sccm/core/plan-design/hierarchy/client-peer-cache).


## <a name="windows-pe-peer-cache"></a>Windows PE-peer-cache
Wanneer u een nieuw besturingssysteem in System Center Configuration Manager implementeert, kunt computers waarop de takenreeks wordt uitgevoerd Windows PE-Peercache inhoud ophalen van een lokale peer (een peer-cachebron) in plaats van inhoud wordt gedownload van een distributiepunt. Dit helpt het Wide Area Network-verkeer (WAN) te beperken indien er sprake is van meerdere filialen terwijl er geen lokaal distributiepunt bestaat.

Zie voor meer informatie [Windows PE-peercache](../../../osd/get-started/prepare-windows-pe-peer-cache-to-reduce-wan-traffic.md).


## <a name="client-locations"></a>Clientlocaties  
 Op de volgende locaties wordt door clients inhoud opgehaald:  

-   **Intranet** (on-premises):  

    -   Distributiepunten kunnen HTTP of HTTPs gebruiken.  

    -   Alleen een cloud-gebaseerde distributiepunt gebruiken terugvaloptie als on-premises distributiepunten niet beschikbaar zijn.  

-   **Internet**:  

    -   Vereist distributiepunten HTTPS accepteren.  

    -   Kan een cloud-gebaseerde distributiepunt gebruiken als terugvaloptie.  

-   **Werkgroep**:  

    -   Vereist distributiepunten HTTPS accepteren.  

    -   Kan een cloud-gebaseerde distributiepunt gebruiken als terugvaloptie.  



## <a name="content-library"></a>Inhoudsbibliotheek  
 De Inhoudsbibliotheek is de single instance store van inhoud die Configuration Manager gebruikt om te beperken van de totale grootte van de gecombineerde hoofdtekst van de inhoud die u distribueert.  

- Meer informatie over de [Inhoudsbibliotheek](../../../core/plan-design/hierarchy/the-content-library.md).
- Gebruik de [Inhoudsbibliotheek hulpprogramma](/sccm/core/plan-design/hierarchy/content-library-cleanup-tool) inhoud die is niet meer gekoppeld aan een toepassing te verwijderen.  


## <a name="distribution-points"></a>Distributiepunten  
 Configuration Manager gebruikt distributiepunten voor het opslaan van bestanden die vereist zijn voor software uit te voeren op clientcomputers. Clients moeten toegang hebben tot minstens één distributiepunt waarvan ze de bestanden voor inhoud die u implementeert kunnen downloaden.  

 Het algemene (a-specifieke) distributiepunt is vaak een standaarddistributiepunt genoemd. Er zijn twee varianten van het standaarddistributiepunt die speciale aandacht krijgen:  

-   **Pull-distributiepunt**: Een variant van een distributiepunt waar het distributiepunt inhoud van een ander distributiepunt (een brondistributiepunt verkrijgt). Dit proces is vergelijkbaar met hoe clients inhoud vanaf distributiepunten downloaden. Pull-distributiepunten kunt u voorkomen dat netwerkbandbreedte knelpunten die optreden wanneer de siteserver rechtstreeks inhoud naar elk distributiepunt distribueren moet.  [Een pull-distributiepunt gebruiken met System Center Configuration Manager](/sccm/core/plan-design/hierarchy/use-a-pull-distribution-point).

-   **Cloud-gebaseerde distributiepunt**: Een variant van een distributiepunt dat geïnstalleerd op Microsoft Azure. [Informatie over het gebruik van een cloud-gebaseerde distributiepunt met System Center Configuration Manager](../../../core/plan-design/hierarchy/use-a-cloud-based-distribution-point.md).  


Standaard distributiepunten bieden ondersteuning voor een bereik van configuraties en functies, zoals bandbreedtebeperking en planning, PXE en Multicast, of voorbereide inhoud.  

-   U kunt besturingselementen zoals **planningen** of **bandbreedtebeperking** om u te helpen bij het beheren van deze overdracht.  

-   U kunt ook andere opties, waaronder **voorbereide inhoud**, en **pull-distributiepunten**. Bovendien kunt u gebruikmaken van **BranchCache** om de netwerkbandbreedte die wordt gebruikt wanneer u inhoud implementeert te beperken.  

-   Distributiepunten ondersteunen verschillende configuraties, zoals  **[PXE](../../../osd/get-started/prepare-site-system-roles-for-operating-system-deployments.md#BKMK_PXEDistributionPoint)**  en  **[Multicast](../../../osd/get-started/prepare-site-system-roles-for-operating-system-deployments.md#BKMK_DPMulticast)**  voor implementaties van besturingssystemen en configuraties voor de ondersteuning van **mobiele apparaten**.  

 Cloud-gebaseerde en pull-distributiepunten ondersteunen veel van deze configuraties dezelfde, maar hebben beperkingen die specifiek voor elke variatie distribution point zijn.  

## <a name="distribution-point-groups"></a>Distributiepuntgroepen  
 Distributiepuntengroepen zijn logische groeperingen van distributiepunten die distributie van inhoud kunnen vereenvoudigen.  

 Zie voor meer informatie [distributiepuntgroepen beheren](../../../core/servers/deploy/configure/install-and-configure-distribution-points.md#bkmk_manage).

## <a name="distribution-point-priority"></a>Prioriteit van het distributiepunt  
 De prioriteitswaarde voor het distributiepunt is gebaseerd op het tijdsbestek dat de overdracht van eerdere implementaties naar dat distributiepunt in beslag nam.  

-   Dit is een zelf zelfregulerende waarde die toegewezen aan een distributiepunt waarmee Configuration Manager overdracht inhoud bij meer distributiepunten in een kortere periode.  

-   Wanneer u inhoud distribueert naar meerdere distributiepunten tegelijkertijd of naar een distributiepunt punt groep, Configuration Manager de inhoud verzendt naar het distributiepunt met de hoogste prioriteit voordat het dezelfde inhoud verzendt naar een distributiepunt met een lagere prioriteit.  

-   Dit vervangt de distributieprioriteit voor pakketten die de beslissende factor in de volgorde blijft van wanneer verschillende distributies worden overgedragen.  


Bijvoorbeeld, als u inhoud met een hoge distributieprioriteit naar een distributiepunt met een lage distributiepuntprioriteit distribueert, draagt dit pakket met hoge prioriteit altijd vóór een pakket met een lagere distributieprioriteit overgedragen. De distributieprioriteit is ook van toepassing als pakketten met een lagere distributieprioriteit naar distributiepunten met hogere distributiepuntprioriteiten worden gedistribueerd.

De hoge distributieprioriteit van het pakket zorgt ervoor dat de Configuration Manager die inhoud naar de overeenkomstige distributiepunten distribueert voordat er pakketten met een lagere distributieprioriteit worden verzonden.  

> [!NOTE]  
>  Pull-distributiepunten maken ook gebruik van een prioriteitsconcept om de volgorde van de eigen brondistributiepunten vast te leggen.  
>   
>  -   De distributiepuntprioriteit voor inhoudsoverdrachten naar het distributiepunt is niet hetzelfde als de prioriteit die pull-distributiepunten gebruiken wanneer ze zoeken naar inhoud vanaf een brondistributiepunt.  
>  -   Zie voor meer informatie [een pull-distributiepunt gebruiken met System Center Configuration Manager](/sccm/core/plan-design/hierarchy/use-a-pull-distribution-point).  


## <a name="fallback"></a>Terugval  
 Vanaf versie 1610 worden zijn op verschillende manieren gewijzigd in de manier waarop dat clients een distributiepunt dat inhoud, inclusief terugval vinden. Gebruik de volgende gegevens met betrekking tot de versie die u gebruikt:

**Versie 1610 en hoger**   
Clients die inhoud van een distributiepunt dat is gekoppeld aan hun huidige grensgroep niet vinden kunnen voor het gebruik van de inhoudsbron locaties die gekoppeld aan grensgroepen neighbor zijn terugvallen. Om te worden gebruikt voor terugval, moet een grensgroep neighbor een gedefinieerde relatie hebben met de huidige grensgroep van de client. Deze relatie bevat een geconfigureerde periode die moet verstrijken voordat een client die inhoud in lokale inhoudsbronnen van de grensgroep neighbor kunt opnemen als onderdeel van de zoekopdracht kan niet worden gevonden.

De concepten van voorkeursdistributiepunten punten worden niet meer gebruikt en de instellingen voor **alternatieve bronlocaties voor inhoud toestaan** niet meer beschikbaar zijn of afgedwongen.

Zie voor meer informatie [grensgroepen](/sccm/core/servers/deploy/configure/define-site-boundaries-and-boundary-groups#boundary-groups).


**Versie 1511 1602 en 1606**   
Terugvalinstellingen betrekking hebben op het gebruik van **distributiepunten bij voorkeur** en inhoud bronlocaties die worden gebruikt door clients.

-   Standaard wordt alleen bij clients inhoud downloaden vanaf een voorkeursdistributiepunt (één dat is gekoppeld aan de client grensgroepen).  

-   Als een distributiepunt echter is geconfigureerd met **Clients toestaan om dit sitesysteem als een terugvalbronlocatie voor inhoud te gebruiken**, kan dat distributiepunt als een geldige inhoudsbron worden aangeboden aan elke client die geen implementatie kan ophalen bij een van de eigen voorkeursdistributiepunten.  


Zie voor meer informatie over de locatie van andere inhoud en terugvalscenario's [bron scenario's voor locatie van inhoud](../../../core/plan-design/hierarchy/content-source-location-scenarios.md). Zie voor meer informatie over grensgroepen [grensgroepen voor versies 1511,1602 en 1606](/sccm/core/servers/deploy/configure/boundary-groups-for-1511-1602-and-1606).

## <a name="network-bandwidth"></a>Netwerkbandbreedte  
 Om te helpen beheren van de hoeveelheid netwerkbandbreedte die wordt gebruikt wanneer u inhoud distribueert, kunt u de volgende opties:  

-   **Voorbereide inhoud**:  Een proces van het overdragen van inhoud naar een distributiepunt zonder op Configuration Manager de inhoud distribueren via het netwerk.  

-   **Planning en beperking**: Configuraties die u helpen bepalen wanneer en hoe inhoud wordt gedistribueerd naar distributiepunten.  

Zie voor meer informatie [beheer van netwerkbandbreedte](/sccm/core/plan-design/hierarchy/manage-network-bandwidth).

## <a name="network-connection-speed-to-content-source"></a>Netwerkverbindingssnelheid naar de inhoudsbron  
Vanaf versie 1610 worden zijn op verschillende manieren gewijzigd in de manier waarop dat clients een distributiepunt met inhoud, inclusief de netwerkverbindingssnelheid voor een inhoudsbron vinden. Gebruik de volgende gegevens met betrekking tot de versie die u gebruikt:

**Versie 1610 en hoger**   
Verbindingssnelheden netwerk die een distributiepunt definieert verwijzen als **snel** of **langzaam** worden niet meer gebruikt. In plaats daarvan elk sitesysteem dat is gekoppeld aan een grensgroep wordt behandeld hetzelfde.

Zie voor meer informatie [grensgroepen](/sccm/core/servers/deploy/configure/define-site-boundaries-and-boundary-groups#boundary-groups).


**Versie 1511 1602 en 1606**   
 U kunt de netwerkverbindingssnelheid van elk distributiepunt in een grensgroep configureren:  

-   Clients gebruiken deze waarde wanneer ze met het distributiepunt verbinden.

-   De netwerkverbindingssnelheid wordt standaard geconfigureerd als **snel**, maar kan ook worden ingesteld als **langzaam**.  

-   De **verbindingssnelheid van het netwerk**, samen met de configuratie van een implementatie bepalen als een client inhoud van een distributiepunt downloaden kan wanneer de client zich in een gekoppelde grensgroep  

Zie voor meer informatie over de locatie van andere inhoud en terugvalscenario's [bron scenario's voor locatie van inhoud](../../../core/plan-design/hierarchy/content-source-location-scenarios.md). Zie voor meer informatie over grensgroepen [grensgroepen voor versies 1511,1602 en 1606](/sccm/core/servers/deploy/configure/boundary-groups-for-1511-1602-and-1606).

## <a name="on-demand-content-distribution"></a>Inhoudsdistributie op aanvraag  
 Inhoudsdistributie op aanvraag is een optie die u voor afzonderlijke instellen kunt toepassingen en pakketten (implementaties) om in te schakelen op aanvraag inhoud distribueren naar voorkeursdistributiepunten.  

-   U kunt deze inschakelen voor een implementatie, inschakelen **Distribueer de inhoud van dit pakket naar voorkeursdistributiepunten**.  

-   Wanneer deze optie is ingeschakeld voor een implementatie en een client probeert die inhoud op te vragen, maar de inhoud niet beschikbaar is op een van de voorkeursdistributiepunten van de client is, wordt Configuration Manager automatisch gedistribueerd die inhoud naar de voorkeursdistributiepunten van de client.  

-   Hoewel dit Configuration Manager automatisch de om inhoud te distribueren naar voorkeursdistributiepunten van de client veroorzaakt, kan de client die inhoud van andere distributiepunten verkrijgen voordat de implementatie van de voorkeursdistributiepunten voor de client ontvangen. Wanneer dit het geval is, wordt de inhoud vervolgens aanwezig zijn op dat distributiepunt voor gebruik door de volgende client waarmee wordt geprobeerd deze implementatie.  

Als u 1610 of hoger gebruikt, Zie [grensgroepen](/sccm/core/servers/deploy/configure/define-site-boundaries-and-boundary-groups#boundary-groups).
Als u versie 1511, 1602 of 1606, Zie [bron scenario's voor locatie van inhoud](../../../core/plan-design/hierarchy/content-source-location-scenarios.md) voor informatie over de locatie van andere inhoud en terugvalscenario's.  



## <a name="package-transfer-manager"></a>Package Transfer Manager  
 Package Transfer Manager is de site server-onderdeel dat inhoud naar distributiepunten op andere computers overdraagt.  

 Meer informatie over de [Package Transfer Manager](../../../core/plan-design/hierarchy/package-transfer-manager.md).  

## <a name="preferred-distribution-point"></a>Voorkeursdistributiepunt  
 Een voorkeursdistributiepunt bevat distributiepunten die gekoppeld aan de huidige grensgroepen van de client zijn.  

 U kunt elk distributiepunt koppelen aan een of meer grensgroepen:  

-   Deze koppeling helpt de client identificeren distributiepunten waarvan deze inhoud kan downloaden.  
-   Standaard kunnen clients alleen inhoud downloaden vanaf een voorkeursdistributiepunt.  


Voor meer informatie:
 - Als u 1610 of hoger gebruikt, Zie [grensgroepen](/sccm/core/servers/deploy/configure/define-site-boundaries-and-boundary-groups#boundary-groups).
 - Als u versie 1511, 1602 of 1606, Zie [bron scenario's voor locatie van inhoud](../../../core/plan-design/hierarchy/content-source-location-scenarios.md).

## <a name="prestage-content"></a>Inhoud vooraf plaatsen  
 Inhoud voor te bereiden is een proces van het overdragen van inhoud naar een distributiepunt zonder op Configuration Manager de inhoud distribueren via het netwerk.  

 Zie voor meer informatie [beheer van netwerkbandbreedte](/sccm/core/plan-design/hierarchy/manage-network-bandwidth).

