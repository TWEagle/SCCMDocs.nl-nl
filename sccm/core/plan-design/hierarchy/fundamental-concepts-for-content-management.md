---
title: Basisprincipes voor inhoudsbeheer
titleSuffix: Configuration Manager
description: Gebruik hulpprogramma's en opties in System Center Configuration Manager voor het beheren van de inhoud die u implementeert.
ms.custom: na
ms.date: 05/04/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: c201be2a-692c-4d67-ac95-0a3afa5320fe
caps.latest.revision: "28"
caps.handback.revision: "0"
author: aaroncz
ms.author: aaroncz
manager: angrobe
ms.openlocfilehash: 708543d7711dc1fe0c5c38f5b608eec0eec8df76
ms.sourcegitcommit: 7fe45ff75f05f7cc03ad021db8119791abe18049
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/01/2017
---
# <a name="fundamental-concepts-for-content-management-in-system-center-configuration-manager"></a>Basisconcepten voor inhoudsbeheer in System Center Configuration Manager

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*

System Center Configuration Manager ondersteunt een robuust systeem van hulpprogramma's en opties voor het beheren van de inhoud die u als toepassingen, pakketten, software-updates en implementaties van besturingssystemen implementeert.  

De inhoud die u implementeert, wordt opgeslagen op siteservers en op sitesysteemservers distributie. Deze inhoud kan een grote hoeveelheid bandbreedte vereisen wanneer deze wordt overgedragen tussen locaties. Voor effectief plannen en gebruik van infrastructuur voor inhoudsbeheer, het is raadzaam dat u de beschikbare opties en configuraties te begrijpen en vervolgens nadenken over hoe u met deze aan te passen aan uw netwerkomgeving en implementatie van inhoud.  

> [!TIP]    
> U kunt meer informatie over het proces voor de distributie van inhoud en het vinden van help bij het opsporen en oplossen van algemene distributie van inhoud. Zie [basisbegrippen en probleemoplossing voor inhoudsdistributie in Configuration Manager](https://support.microsoft.com/help/4000401/content-distribution-in-mcm) op support.microsoft.com.

Hieronder vindt u belangrijke concepten voor inhoudsbeheer. Wanneer een concept aanvullende of complexe informatie vereist, worden er koppelingen naar de informatie weergegeven.

## <a name="accounts-used-for-content-management"></a>Accounts die worden gebruikt voor inhoudsbeheer  
 De volgende accounts kunnen worden gebruikt met inhoudsbeheer:  

-   **Netwerktoegangsaccount**: Verbinding maken met een distributiepunt en toegang tot inhoud door clients gebruikt. Standaard wordt het computeraccount eerst geprobeerd.  

     Dit account wordt ook gebruikt door pull-distributiepunten om inhoud te verkrijgen van een brondistributiepunt in een extern forest.  

-   **Pakkettoegangsaccount**: Configuration Manager verleent standaard toegang tot inhoud op een distributiepunt aan de algemene toegangsaccounts gebruikers en beheerders. U kunt echter aanvullende machtigingen configureren om de toegang te beperken.   

-   **Multicastverbindingsaccount**: Gebruikt voor implementaties van besturingssystemen.  

Zie voor meer informatie over deze accounts [accounts voor toegang tot inhoud beheren](../../../core/plan-design/hierarchy/manage-accounts-to-access-content.md).

## <a name="bandwidth-throttling-and-scheduling"></a>Bandbreedtebeperking en planning  
 Bandbreedtebeperking en planning zijn opties waarmee u kunt bepalen wanneer inhoud van een siteserver naar distributiepunten wordt gedistribueerd. Dit is vergelijkbaar met, maar niet direct gerelateerd aan, de bandbreedteregeling voor een bestandsreplicatie van site naar site.  

 Zie voor meer informatie [netwerkbandbreedte beheren](/sccm/core/plan-design/hierarchy/manage-network-bandwidth).

## <a name="binary-differential-replication"></a>Binaire differentiële replicatie  
 Een vereiste voor distributiepunten, binaire differentiële replicatie (BDR), wordt ook wel aangeduid als de replicatie van verschillen, wordt automatisch gebruikt voor het gebruik van netwerkbandbreedte te verlagen wanneer u bij het distribueren van updates voor inhoud die u eerder hebt geïmplementeerd naar andere sites of naar externe distributiepunten.  

 BDR minimaliseert de netwerkbandbreedte die wordt gebruikt om updates te verzenden voor gedistribueerde inhoud door alleen de nieuwe of gewijzigde inhoud opnieuw te verzenden in plaats van de volledige set van inhoudsbestanden wanneer er een wijziging aan die bestanden wordt doorgevoerd.  

 Bij gebruik van binaire differentiële replicatie identificeert Configuration Manager de wijzigingen die zich voordoen aan bronbestanden voor elke set van inhoud die eerder is gedistribueerd.  

-   Wanneer bestanden in de broninhoud wijzigen, wordt Configuration Manager maakt een nieuwe incrementele versie van de inhoudsset en worden alleen de gewijzigde bestanden gerepliceerd naar de doelsites en distributiepunten. Een bestand wordt beschouwd als gewijzigd als is hernoemd of verplaatst, of als de inhoud van het bestand is gewijzigd. Als u bijvoorbeeld één stuurprogrammabestand vervangt voor een implementatiepakket van een besturingssysteem dat u eerder distribueerde naar verschillende sites, dan wordt alleen het gewijzigde stuurprogrammabestand gerepliceerd naar die doelsites.  

-   Configuration Manager ondersteunt tot vijf incrementele versies van een inhoudsset voordat het de volledige inhoudsset opnieuw verzendt. De volgende wijziging in de inhoudsset na de vijfde update zorgt ervoor dat Configuration Manager voor het maken van een nieuwe versie van de inhoudsset. Configuration Manager verdeelt vervolgens de nieuwe versie van de inhoud die is ingesteld op de voorgaande set en eventuele aanvullende versies vervangt. Nadat de nieuwe inhoudsset is gedistribueerd worden volgende incrementele wijzigingen aan de bronbestanden opnieuw gerepliceerd door binaire differentiële replicatie.  


BDR wordt ondersteund tussen elke bovenliggende en onderliggende site in een hiërarchie. Binnen een site wordt BDR ondersteund tussen de siteserver en de normale distributiepunten. Echter, pull-distributiepunten en cloud-gebaseerde distributiepunten ondersteunen geen binaire differentiële replicatie om over te dragen van inhoud. Pull-distributiepunten ondersteunen bestandsniveau delta's, het overbrengen van nieuwe bestanden, maar niet blokken binnen een bestand.

Toepassingen gebruiken altijd binaire differentiële replicatie. Binaire differentiële replicatie is optioneel voor pakketten. Standaard is deze optie niet ingeschakeld. U moet deze functie inschakelen voor elk pakket om binaire differentiële replicatie voor pakketten te gebruiken. U kunt dit doen door de optie **Binaire differentiële replicatie inschakelen** te selecteren wanneer u een nieuw pakket maakt of wanneer u het tabblad **Gegevensbron** van de pakketeigenschappen bewerkt.  

## <a name="branchcache"></a>BranchCache  
 Een Windows-technologie waarmee clients die BranchCache ondersteunen en een implementatie die is geconfigureerd voor BranchCache in staat te fungeren als inhoudsbron voor andere clients BranchCache-functionaliteit hebben gedownload.  

 Als bijvoorbeeld de eerste clientcomputer met BranchCache inhoud aanvraagt bij een distributiepunt waarop Windows Server 2012 wordt uitgevoerd en is geconfigureerd als een BrancheCache-server, wordt de inhoud door de clientcomputer gedownload en opgeslagen in het cachegeheugen.  

-   Die clientcomputer kan de inhoud vervolgens maken beschikbaar voor aanvullende BranchCache-clients in hetzelfde subnet die ook de inhoud in cache.  

-   Zo moeten volgende clients op hetzelfde subnet de inhoud niet van het distributiepunt downloaden en wordt de inhoud over meerdere clients voor toekomstige overdrachten gedistribueerd.  

## <a name="peer-cache"></a>Peer-Cache
Vanaf versie 1610, kunt client-Peer-Cache u beheren implementatie van inhoud voor clients op externe locaties. Peer-Cache is een ingebouwde Configuration Manager-oplossing waarmee clients inhoud te delen met andere clients rechtstreeks vanuit het lokale cachegeheugen.

Nadat u clientinstellingen waarmee Peer-Cache op een verzameling implementeert, fungeren leden van deze verzameling als een peer-inhoudsbron voor andere clients in dezelfde grensgroep.

Zie voor meer informatie [Peer-Cache voor Configuration Manager-clients](/sccm/core/plan-design/hierarchy/client-peer-cache).


## <a name="windows-pe-peer-cache"></a>Windows PE-peer-cache
Wanneer u een nieuw besturingssysteem in System Center Configuration Manager implementeert, kunnen computers waarop de takenreeks wordt uitgevoerd Windows PE-Peer-Cache gebruiken om inhoud te verkrijgen van een lokale peer (een peer-cachebron) in plaats van de inhoud van een distributiepunt wordt gedownload. Dit helpt het Wide Area Network-verkeer (WAN) te beperken indien er sprake is van meerdere filialen terwijl er geen lokaal distributiepunt bestaat.

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
 De Inhoudsbibliotheek is de single instance store van inhoud die Configuration Manager gebruikt om te beperken van de totale grootte van alle inhoud die u distribueert.  

- Meer informatie over de [Inhoudsbibliotheek](../../../core/plan-design/hierarchy/the-content-library.md).
- Gebruik de [Inhoudsbibliotheek opschoonprogramma](/sccm/core/plan-design/hierarchy/content-library-cleanup-tool) inhoud die niet meer gekoppeld aan een toepassing te verwijderen.  


## <a name="distribution-points"></a>Distributiepunten  
 Configuration Manager gebruikt distributiepunten voor het opslaan van bestanden die vereist zijn voor software uit te voeren op clientcomputers. Clients moeten toegang hebben tot ten minste één distributiepunt waarvan ze de bestanden voor inhoud die u implementeert kunnen downloaden.  

 Het algemene (niet-specifieke) distributiepunt wordt doorgaans een standaarddistributiepunt genoemd. Er zijn twee varianten van het standaarddistributiepunt die speciale aandacht krijgen:  

-   **Pull-distributiepunt**: Een variant van een distributiepunt waar het distributiepunt die inhoud bij een ander distributiepunt (een brondistributiepunt ophaalt). Dit proces is vergelijkbaar met de wijze waarop clients inhoud vanaf distributiepunten downloaden. Pull-distributiepunten kunt u problemen met de netwerkbandbreedte die zich voordoen wanneer de siteserver rechtstreeks inhoud naar elk distributiepunt distribueren moet voorkomen.  [Een pull-distributiepunt gebruiken met System Center Configuration Manager](/sccm/core/plan-design/hierarchy/use-a-pull-distribution-point).

-   **Cloud-gebaseerde distributiepunt**: Een variant van een distributiepunt dat geïnstalleerd op Microsoft Azure. [Informatie over het gebruik van een cloud-gebaseerde distributiepunt met System Center Configuration Manager](../../../core/plan-design/hierarchy/use-a-cloud-based-distribution-point.md).  


Standaarddistributiepunten bieden ondersteuning voor een bereik van configuraties en functies, zoals bandbreedtebeperking en planning, PXE en Multicast of voorbereide inhoud.  

-   U kunt besturingselementen zoals **planningen** of **bandbreedtebeperking** om u te helpen bij het beheren van deze overdracht.  

-   U kunt ook andere opties, waaronder **vooraf geplaatste inhoud**, en **pull-distributiepunten**. Bovendien kunt u gebruikmaken van **BranchCache** om de netwerkbandbreedte die wordt gebruikt wanneer u inhoud implementeert te beperken.  

-   Distributiepunten bieden ondersteuning voor verschillende configuraties, zoals  **[PXE](../../../osd/get-started/prepare-site-system-roles-for-operating-system-deployments.md#BKMK_PXEDistributionPoint)**  en  **[Multicast](../../../osd/get-started/prepare-site-system-roles-for-operating-system-deployments.md#BKMK_DPMulticast)**  voor implementaties van besturingssystemen of configuraties ter ondersteuning van **mobiele apparaten**.  

 Cloud-gebaseerde en pull-distributiepunten ondersteunen veel van dezelfde configuraties, maar hebben beperkingen die specifiek voor elke distributiepuntvariant zijn.  

## <a name="distribution-point-groups"></a>Distributiepuntgroepen  
 Distributiepuntengroepen zijn logische groeperingen van distributiepunten die de inhoudsdistributie kunnen vereenvoudigen.  

 Zie voor meer informatie [distributiepuntgroepen beheren](../../../core/servers/deploy/configure/install-and-configure-distribution-points.md#bkmk_manage).

## <a name="distribution-point-priority"></a>Prioriteit van het distributiepunt  
 De prioriteitswaarde voor het distributiepunt is gebaseerd op het tijdsbestek dat de overdracht van eerdere implementaties naar dat distributiepunt in beslag nam.  

-   Dit is een zelfregulerende waarde die toegewezen aan een distributiepunt die inhoud van Configuration Manager-overdracht kunt u meer distributiepunten in een kortere periode.  

-   Wanneer u inhoud distribueert naar meerdere distributiepunten tegelijkertijd of naar een distributiepunt groep, wordt Configuration Manager verzendt de inhoud naar het distributiepunt met de hoogste prioriteit voordat het dezelfde inhoud verzendt naar een distributiepunt met een lagere prioriteit.  

-   De distributieprioriteit voor pakketten die blijft de beslissende factor in de volgorde waarin verschillende distributies worden overgedragen vervangen niet.  


Bijvoorbeeld, als u inhoud met een hoge distributieprioriteit naar een distributiepunt met een lage distributiepuntprioriteit distribueert, dit pakket met hoge distributieprioriteit altijd worden verplaatst vóór een pakket met een lagere distributieprioriteit overgedragen. De distributieprioriteit is ook van toepassing als pakketten met een lagere distributieprioriteit naar distributiepunten met hogere distributiepuntprioriteiten worden gedistribueerd.

De hoge distributieprioriteit van het pakket zorgt ervoor dat de Configuration Manager die inhoud naar de overeenkomstige distributiepunten distribueert voordat er pakketten met een lagere distributieprioriteit worden verzonden.  

> [!NOTE]  
>  Pull-distributiepunten maken ook gebruik van een prioriteitsconcept om de volgorde van de eigen brondistributiepunten vast te leggen.  
>   
>  -   De distributiepuntprioriteit voor inhoudsoverdrachten naar het distributiepunt is verschillend van de prioriteit die pull-distributiepunten gebruiken wanneer ze zoeken naar inhoud vanaf een brondistributiepunt.  
>  -   Zie voor meer informatie [een pull-distributiepunt gebruiken met System Center Configuration Manager](/sccm/core/plan-design/hierarchy/use-a-pull-distribution-point).  


## <a name="fallback"></a>Terugval  
 Vanaf versie 1610, zijn verschillende dingen gewijzigd in de manier waarop dat clients een distributiepunt die inhoud, inclusief terugval is gevonden. Gebruik de volgende gegevens met betrekking tot de versie die u gebruikt:

**Versie 1610 en hoger**   
Clients die niet kunnen vinden van inhoud vanaf een distributiepunt dat is gekoppeld aan hun huidige grensgroep kunnen terugvallen voor het gebruik van de inhoudsbron locaties die gekoppeld aan de grensgroepen neighbor zijn. Om te worden gebruikt voor terugval, moet een neighbor grensgroep een gedefinieerde relatie hebben met de huidige grensgroep van de client. Deze relatie bevat een geconfigureerde periode die moet verstrijken voordat een client die inhoud in lokale inhoudsbronnen van de grensgroep neighbor kunt opnemen als onderdeel van de zoekopdracht kan niet worden gevonden.

De concepten van voorkeursdistributiepunten punten worden niet meer gebruikt en de instellingen voor **alternatieve bronlocaties voor inhoud toestaan** zijn niet langer beschikbaar of afgedwongen.

Zie voor meer informatie [grensgroepen](/sccm/core/servers/deploy/configure/define-site-boundaries-and-boundary-groups#boundary-groups).


**Versie 1511, 1602 en 1606**   
Terugvalinstellingen zijn gerelateerd aan het gebruik van **voorkeursdistributiepunten** en voor inhoudsbron locaties die worden gebruikt door clients.

-   Standaard downloaden clients alleen inhoud van een voorkeursdistributiepunt (een die is gekoppeld aan de grensgroepen van de client).  

-   Als een distributiepunt echter is geconfigureerd met **Clients toestaan om dit sitesysteem als een terugvalbronlocatie voor inhoud te gebruiken**, kan dat distributiepunt als een geldige inhoudsbron worden aangeboden aan elke client die geen implementatie kan ophalen bij een van de eigen voorkeursdistributiepunten.  


Zie voor meer informatie over de locatie van andere inhoud en terugvalscenario's [locatie van inhoudsbronnen](../../../core/plan-design/hierarchy/content-source-location-scenarios.md). Zie voor meer informatie over grensgroepen [grensgroepen voor versies 1511,1602 en 1606](/sccm/core/servers/deploy/configure/boundary-groups-for-1511-1602-and-1606).

## <a name="network-bandwidth"></a>Netwerkbandbreedte  
 Om te beheren, de hoeveelheid netwerkbandbreedte die wordt gebruikt wanneer u inhoud distribueert, kunt u de volgende opties:  

-   **Vooraf geplaatste inhoud**:  Een proces waarbij inhoud naar een distributiepunt wordt overgedragen zonder afhankelijk te zijn in Configuration Manager de inhoud te distribueren via het netwerk.  

-   **Planning en bandbreedtebeperking**: Configuraties die u helpen bepalen wanneer en hoe inhoud wordt gedistribueerd naar distributiepunten.  

Zie voor meer informatie [netwerkbandbreedte beheren](/sccm/core/plan-design/hierarchy/manage-network-bandwidth).

## <a name="network-connection-speed-to-content-source"></a>Netwerkverbindingssnelheid naar de inhoudsbron  
Vanaf versie 1610, zijn verschillende dingen gewijzigd in de manier waarop dat clients een distributiepunt die inhoud, inclusief de netwerkverbindingssnelheid voor een inhoudsbron is gevonden. Gebruik de volgende gegevens met betrekking tot de versie die u gebruikt:

**Versie 1610 en hoger**   
Verbindingssnelheden netwerk die een distributiepunt definieert verwijst als **snel** of **langzaam** niet meer worden gebruikt. In plaats daarvan elk sitesysteem dat is gekoppeld aan een grensgroep wordt behandeld hetzelfde.

Zie voor meer informatie [grensgroepen](/sccm/core/servers/deploy/configure/define-site-boundaries-and-boundary-groups#boundary-groups).


**Versie 1511, 1602 en 1606**   
 U kunt de netwerkverbindingssnelheid van elk distributiepunt in een grensgroep configureren:  

-   Clients gebruiken deze waarde wanneer ze verbinding met het distributiepunt maken.

-   De netwerkverbindingssnelheid wordt standaard geconfigureerd als **snel**, maar kan ook worden ingesteld als **langzaam**.  

-   De **netwerkverbindingssnelheid**, samen met de configuratie van een implementatie bepalen als een client inhoud vanaf een distributiepunt downloaden kan wanneer de client zich in een gekoppelde grensgroep.  

Zie voor meer informatie over de locatie van andere inhoud en terugvalscenario's [locatie van inhoudsbronnen](../../../core/plan-design/hierarchy/content-source-location-scenarios.md). Zie voor meer informatie over grensgroepen [grensgroepen voor versies 1511,1602 en 1606](/sccm/core/servers/deploy/configure/boundary-groups-for-1511-1602-and-1606).

## <a name="on-demand-content-distribution"></a>Inhoudsdistributie op aanvraag  
 Inhoudsdistributie op aanvraag is een optie die u voor afzonderlijke instellen kunt toepassingen en pakketten (implementaties) om in te schakelen op aanvraag inhoudsdistributie naar voorkeursdistributiepunten.  

-   Schakel voor een implementatie als wilt toestaan **Distribueer de inhoud voor dit pakket naar voorkeursdistributiepunten**.  

-   Wanneer deze optie is ingeschakeld voor een implementatie en een client probeert die inhoud op te vragen, maar de inhoud niet beschikbaar is op een van de voorkeursdistributiepunten van de client is, distribueert Configuration Manager automatisch die inhoud naar de voorkeursdistributiepunten van de client.  

-   Hoewel dit Configuration Manager automatisch de om inhoud te distribueren naar voorkeursdistributiepunten van die client activeert, kan de client die inhoud van andere distributiepunten verkrijgen voordat de voorkeursdistributiepunten voor de client de implementatie ontvangen. Wanneer dit gebeurt, kan de inhoud vervolgens meer aanwezig zijn op dat distributiepunt voor gebruik door de volgende client die deze implementatie zoekt.  

Als u versie 1610 of hoger gebruikt, Zie [grensgroepen](/sccm/core/servers/deploy/configure/define-site-boundaries-and-boundary-groups#boundary-groups).
Als u versie 1511 of 1602 1606 gebruikt, Zie [locatie van inhoudsbronnen](../../../core/plan-design/hierarchy/content-source-location-scenarios.md) voor meer informatie over de verschillende Inhoudslocatie en terugval scenario's.  



## <a name="package-transfer-manager"></a>Package Transfer Manager  
 Package Transfer Manager is het siteserveronderdeel dat inhoud naar distributiepunten op andere computers overdraagt.  

 Meer informatie over de [Package Transfer Manager](../../../core/plan-design/hierarchy/package-transfer-manager.md).  

## <a name="preferred-distribution-point"></a>Voorkeursdistributiepunt  
 Een voorkeursdistributiepunt bevat alle distributiepunten die gekoppeld aan de huidige grensgroepen van een client zijn.  

 U kunt elk distributiepunt koppelen aan een of meer grensgroepen:  

-   Deze koppeling wordt de client van welke distributiepunten het downloaden van inhoud.  
-   Standaard kunnen clients alleen inhoud downloaden uit een voorkeursdistributiepunt.  


Voor meer informatie:
 - Als u versie 1610 of hoger gebruikt, Zie [grensgroepen](/sccm/core/servers/deploy/configure/define-site-boundaries-and-boundary-groups#boundary-groups).
 - Als u versie 1511 of 1602 1606 gebruikt, Zie [locatie van inhoudsbronnen](../../../core/plan-design/hierarchy/content-source-location-scenarios.md).

## <a name="prestage-content"></a>Inhoud vooraf plaatsen  
 Voorbereiden van inhoud is een proces waarbij inhoud naar een distributiepunt wordt overgedragen zonder afhankelijk te zijn in Configuration Manager de inhoud te distribueren via het netwerk.  

 Zie voor meer informatie [netwerkbandbreedte beheren](/sccm/core/plan-design/hierarchy/manage-network-bandwidth).
