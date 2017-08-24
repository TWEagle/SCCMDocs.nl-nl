---
title: Netwerkbandbreedte beheren voor inhoud | Microsoft Docs
description: Planning, beperking en voorbereide inhoud voor System Center Configuration Manager configureren.
ms.custom: na
ms.date: 2/6/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: e80d1151-91db-4a27-8411-a957297b67d0
caps.latest.revision: "15"
caps.handback.revision: "0"
author: Brenduns
ms.author: brenduns
manager: angrobe
ms.openlocfilehash: d9dff97126c34a726677de60dd7647370c553b6e
ms.sourcegitcommit: 51fc48fb023f1e8d995c6c4eacfda7dbec4d0b2f
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 08/07/2017
---
# <a name="manage-network-bandwidth-for-content"></a>Netwerkbandbreedte voor inhoud beheren
Om u te helpen bij het beheren van netwerkbandbreedte die wordt gebruikt voor het inhoudsbeheer van System Center Configuration Manager, kunt u ingebouwde besturingselementen voor plannen en aanvraagbeperking. U kunt ook vooraf geplaatste inhoud gebruiken. De volgende secties worden deze opties in meer detail.

##  <a name="BKMK_PlanningForThrottling"></a>Planning en bandbreedtebeperking  

 Wanneer u een pakket maken, wijzigen van het bronpad voor de inhoud of inhoud op het distributiepunt bijwerken, worden de bestanden van het bronpad gekopieerd naar de Inhoudsbibliotheek op de siteserver. De inhoud wordt vervolgens naar de Inhoudsbibliotheek op de distributiepunten gekopieerd uit de Inhoudsbibliotheek op de siteserver. Als de inhoudsbronbestanden worden bijgewerkt en de bronbestanden al werden gedistribueerd, Configuration Manager alleen de nieuwe of bijgewerkte bestanden kunnen worden opgehaald en zendt deze naar het distributiepunt.

 U kunt besturingselementen voor plannen en aanvraagbeperking voor site-naar-site-communicatie en voor communicatie tussen een siteserver en een extern distributiepunt. Als de netwerkbandbreedte wordt beperkt, zelfs na het instellen van de besturingselementen voor plannen en aanvraagbeperking, kunt u overwegen om de inhoud op het distributiepunt.  

 In Configuration Manager kunt u een planning instellen en instellingen voor bandbreedteregeling opgeven op externe distributiepunten die bepalen wanneer en hoe de distributie van inhoud wordt uitgevoerd. Elk extern distributiepunt kan verschillende configuraties hebben die adres netwerkbandbreedtebeperkingen van de siteserver naar het externe distributiepunt helpen. De besturingselementen voor plannen en aanvraagbeperking voor het externe distributiepunt zijn vergelijkbaar met de instellingen voor een standaardafzenderadres. In dit geval worden de instellingen gebruikt door een nieuw onderdeel, Package Transfer Manager genoemd.

 Package Transfer Manager distribueert inhoud vanaf een siteserver, als een primaire site of secundaire site naar een distributiepunt dat is geïnstalleerd op een sitesysteem. De instellingen voor bandbreedteregeling zijn opgegeven in de **frequentielimieten** tabblad en de schema-instellingen zijn opgegeven op de **planning** tabblad voor een distributiepunt dat zich niet op een siteserver. De tijdsinstellingen zijn gebaseerd op de tijdzone van de verzendende site, niet het distributiepunt.  

> [!IMPORTANT]  
>  De **frequentielimieten** en **planning** tabbladen worden alleen weergegeven in de eigenschappen van distributiepunten die niet zijn geïnstalleerd op een siteserver.  

Zie voor meer informatie [installeren en configureren van distributiepunten voor System Center Configuration Manager](/sccm/core/servers/deploy/configure/install-and-configure-distribution-points).  

##  <a name="BKMK_PrestagingContent"></a>Voorbereide inhoud  
 U kunt inhoud vooraf op de inhoudsbestanden toevoegen aan de Inhoudsbibliotheek op een siteserver of distributiepunt, voordat u de inhoud distribueert. Omdat de inhoudsbestanden al in de Inhoudsbibliotheek staan, moeten ze niet overbrengen via het netwerk wanneer u de inhoud distribueert. U kunt de inhoudsbestanden voor toepassingen en pakketten voorbereiden.  

Selecteer in de Configuration Manager-console de inhoud die u wilt voorbereiden en gebruik vervolgens de **maken Wizard voorbereid inhoudsbestand**. Hiermee maakt u een gecomprimeerd, voorbereid inhoudsbestand dat de bestanden en gekoppelde metagegevens voor de inhoud bevat. Vervolgens kunt u de inhoud op een site of distributiepunt handmatig importeren. Houd rekening met de volgende punten:  

-   Wanneer u het voorbereide inhoudsbestand op een siteserver importeert, worden de inhoudsbestanden toegevoegd aan de Inhoudsbibliotheek op de siteserver en vervolgens geregistreerd in de site server-database.  

-   Wanneer u het voorbereide inhoudsbestand op een distributiepunt importeert, worden de inhoudsbestanden toegevoegd aan de Inhoudsbibliotheek op het distributiepunt. Een statusbericht verzonden naar de siteserver die de site informeert dat de inhoud beschikbaar op het distributiepunt is.  

U kunt desgewenst het distributiepunt als **voorbereid** voor het beheer van de distributie van inhoud. Klik, wanneer u inhoud distribueert, kunt u kiezen of u wilt:  

-   De inhoud op het distributiepunt altijd voor te bereiden.  

-   De initiële inhoud voor het pakket voor te bereiden en vervolgens het normale inhoudsdistributieproces gebruiken wanneer er updates voor de inhoud.  

-   Gebruik altijd de standaardinhoudsdistributie voor de inhoud van het pakket.  

###  <a name="BKMK_DetermineToPrestageContent"></a>Bepalen of inhoud vooraf plaatsen  
 Overweeg het voorbereiden van inhoud voor toepassingen en pakketten in de volgende scenario's:  

-   **Voor het oplossen van het probleem van beperkte netwerkbandbreedte vanaf de siteserver naar een distributiepunt.** Planning en bandbreedtebeperking is niet genoeg om te voldoen aan uw opmerkingen over bandbreedte, dan kunt u de inhoud op het distributiepunt voorbereiden. Elk distributiepunt heeft de **dit distributiepunt inschakelen voor voorbereide inhoud** instelling die u in de eigenschappen van het distributiepunt kiezen kunt. Wanneer u deze optie inschakelt, wordt het distributiepunt wordt geïdentificeerd als een voorbereid distributiepunt en kunt u kiezen hoe de inhoud per pakket te beheren.  

    De volgende instellingen zijn beschikbaar in de eigenschappen voor een toepassing, pakket, stuurprogrammapakket, opstartinstallatiekopie, installatieprogramma besturingssysteem en de installatiekopie. Deze instellingen kunnen u kiezen hoe inhoud distributiepunt wordt beheerd op externe distributiepunten die zijn geïdentificeerd als voorbereid:  

    -   **Automatisch inhoud downloaden wanneer pakketten worden toegewezen aan distributiepunten**: Gebruik deze optie wanneer u kleinere pakketten hebt en de instellingen voor plannen en aanvraagbeperking voldoende controle voor inhoudsdistributie bieden.  

    -   **Alleen inhoudswijzigingen downloaden naar het distributiepunt**: Gebruik deze optie als u verwacht dat toekomstige updates voor de inhoud in het pakket over het algemeen kleiner is dan het oorspronkelijke pakket. U kunt bijvoorbeeld een toepassing zoals Microsoft Office voorbereiden omdat de initiële pakketgrootte meer dan 700 MB is en is te groot om te verzenden via het netwerk. Echter updates van inhoud aan dit pakket is mogelijk minder dan 10 MB en zijn aanvaardbaar voor distributie via het netwerk. Een ander voorbeeld is stuurprogrammapakketten waarbij de initiële pakketgrootte omvangrijk is, maar het pakket stapsgewijze stuurprogrammatoevoegingen mogelijk klein mogelijk.  

    -   **De inhoud in dit pakket handmatig kopiëren naar het distributiepunt**: Gebruik deze optie wanneer u grote pakketten met inhoud, zoals een besturingssysteem hebt en u nooit het netwerk gebruiken om de inhoud naar het distributiepunt te distribueren. Wanneer u deze optie selecteert, moet u de inhoud op het distributiepunt voorbereiden.  

    > [!IMPORTANT]  
    >  De voorgaande opties zijn van toepassing op basis van de pakket- en worden alleen gebruikt wanneer een distributiepunt wordt geïdentificeerd als voorbereid. Distributiepunten die niet zijn geïdentificeerd als voorbereid, negeren deze instellingen. In dit geval wordt inhoud altijd gedistribueerd via het netwerk van de siteserver naar de distributiepunten.  

-   **De Inhoudsbibliotheek op een siteserver herstellen.** Wanneer een siteserver uitvalt, wordt informatie over pakketten en toepassingen die is opgenomen in de Inhoudsbibliotheek als onderdeel van het herstelproces teruggezet naar de sitedatabase, maar de inhoudsbibliotheekbestanden worden niet teruggezet als onderdeel van het proces. Als u een bestandssysteemback-up naar de Inhoudsbibliotheek terugzetten niet hebt, kunt u een voorbereid inhoudsbestand maken van een andere site met de pakketten en toepassingen die u nodig hebt. Vervolgens kunt u het voorbereide inhoudsbestand op de herstelde siteserver uitpakken. Zie voor meer informatie over de site server-back-up en herstel [back-up en herstel voor System Center Configuration Manager](/sccm/protect/understand/backup-and-recovery).  
