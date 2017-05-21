---
title: Beheer van netwerkbandbreedte voor inhoud | Microsoft-documenten
description: Configureer plant, beperking en voorbereide inhoud voor System Center Configuration Manager.
ms.custom: na
ms.date: 2/6/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: e80d1151-91db-4a27-8411-a957297b67d0
caps.latest.revision: 15
caps.handback.revision: 0
author: Brenduns
ms.author: brenduns
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 37e4f27fcea0bbdd39c9fd3ab38aa46e3059f73a
ms.openlocfilehash: d9dff97126c34a726677de60dd7647370c553b6e
ms.contentlocale: nl-nl
ms.lasthandoff: 05/17/2017


---

# <a name="manage-network-bandwidth-for-content"></a>Beheer van netwerkbandbreedte voor inhoud
U kunt de ingebouwde besturingselementen voor plannen en aanvraagbeperking gebruiken om u te helpen bij het beheren van netwerkbandbreedte die wordt gebruikt voor het inhoudsbeheerproces van System Center Configuration Manager. U kunt ook gebruik voorbereide inhoud. De volgende secties worden deze opties gedetailleerder beschreven.

##  <a name="BKMK_PlanningForThrottling"></a>Planning en beperking  

 Wanneer u een pakket maakt, het bronpad voor de inhoud wijzigt of inhoud op het distributiepunt bijwerken, worden de bestanden van het bronpad naar de Inhoudsbibliotheek op de siteserver gekopieerd. Vervolgens wordt is de inhoud van de Inhoudsbibliotheek op de siteserver gekopieerd naar de Inhoudsbibliotheek op de distributiepunten. Als de inhoudsbronbestanden worden bijgewerkt en de bronbestanden al werden gedistribueerd, Configuration Manager alleen de nieuwe of bijgewerkte bestanden kunnen worden opgehaald en zendt deze naar het distributiepunt.

 U kunt besturingselementen voor plannen en aanvraagbeperking voor site-naar-site-communicatie en voor communicatie tussen een siteserver en een extern distributiepunt. Als netwerkbandbreedte beperkt is zelfs nadat u de besturingselementen voor plannen en aanvraagbeperking instelt, kunt u overwegen de inhoud op het distributiepunt voor te bereiden.  

 In Configuration Manager, kunt u een planning instellen en instellingen voor bandbreedteregeling opgeven op externe distributiepunten die bepalen wanneer en hoe de distributie van inhoud wordt uitgevoerd. Elk extern distributiepunt kan verschillende configuraties hebben die adres netwerkbandbreedtebeperkingen van de siteserver naar het externe distributiepunt helpen. De besturingselementen voor plannen en aanvraagbeperking voor het externe distributiepunt zijn vergelijkbaar met de instellingen voor een standaardafzenderadres. In dit geval worden de instellingen gebruikt door een nieuwe-component die Package Transfer Manager heet.

 Package Transfer Manager distribueert inhoud vanaf een siteserver, als een primaire of secundaire site naar een distributiepunt dat is geïnstalleerd op een sitesysteem. De instellingen voor bandbreedteregeling zijn opgegeven op de **frequentielimieten** tabblad en de planningsinstellingen worden opgegeven op de **schema** tabblad voor een distributiepunt dat zich niet op een siteserver. De tijdsinstellingen zijn gebaseerd op de tijdzone van de verzendende site, niet het distributiepunt.  

> [!IMPORTANT]  
>  De **frequentielimieten** en **schema** tabbladen worden alleen weergegeven in de eigenschappen voor distributiepunten die niet zijn geïnstalleerd op een siteserver.  

Zie voor meer informatie [installeren en configureren van distributiepunten voor System Center Configuration Manager](/sccm/core/servers/deploy/configure/install-and-configure-distribution-points).  

##  <a name="BKMK_PrestagingContent"></a>Voorbereide inhoud  
 U kunt inhoud vooraf op de inhoudsbestanden toegevoegd aan de Inhoudsbibliotheek op een siteserver of distributiepunt, voordat u de inhoud distribueert. Omdat de inhoudsbestanden al in de Inhoudsbibliotheek staan, ze niet worden overgedragen via het netwerk wanneer u de inhoud distribueert. U kunt de inhoudsbestanden voor toepassingen en pakketten voorbereiden.  

Selecteer in de Configuration Manager-console de inhoud die u wilt voorbereiden en gebruik vervolgens de **maken Wizard voorbereid inhoudsbestand**. Dit maakt een gecomprimeerd, voorbereid inhoudsbestand dat de bestanden en gekoppelde metagegevens voor de inhoud bevat. Vervolgens kunt u de inhoud via een siteserver of distributiepunt handmatig importeren. Houd rekening met de volgende punten:  

-   Als u het voorbereide inhoudsbestand op een siteserver importeert, worden de inhoudsbestanden toegevoegd aan de Inhoudsbibliotheek op de siteserver en vervolgens geregistreerd in de siteserverdatabase.  

-   Als u het voorbereide inhoudsbestand op een distributiepunt importeert, worden de inhoudsbestanden toegevoegd aan de Inhoudsbibliotheek op het distributiepunt. Een statusbericht verzonden naar de siteserver die de site informeert dat de inhoud beschikbaar op het distributiepunt is.  

Eventueel kunt u het distributiepunt als **voorbereid** voor het beheer van de distributie van inhoud. Klik, wanneer u inhoud distribueert, kunt u kiezen of u wilt:  

-   De inhoud op het distributiepunt altijd voor te bereiden.  

-   De initiële inhoud voor het pakket voor te bereiden en vervolgens het normale inhoudsdistributieproces gebruiken wanneer er updates beschikbaar voor de inhoud zijn.  

-   Gebruik altijd het normale inhoudsdistributieproces voor de inhoud van het pakket.  

###  <a name="BKMK_DetermineToPrestageContent"></a>Bepalen of inhoud moet worden voorbereid  
 Overweeg het voorbereiden van inhoud voor toepassingen en pakketten in de volgende scenario's:  

-   **Om het probleem van beperkte netwerkbandbreedte vanaf de siteserver naar een distributiepunt.** Als u de planning en aanvraagbeperking niet voldoende om te voldoen aan uw opmerkingen over de bandbreedte, houd rekening met de inhoud op het distributiepunt voor te bereiden. Elk distributiepunt heeft de **dit distributiepunt inschakelen voor voorbereide inhoud** instelling die u in de eigenschappen van het distributiepunt kiezen kunt. Wanneer u deze optie inschakelt, wordt het distributiepunt wordt geïdentificeerd als een voorbereid distributiepunt en kunt u kiezen hoe de inhoud per pakket wilt beheren.  

    De volgende instellingen zijn beschikbaar in de eigenschappen voor een toepassing, pakket, stuurprogrammapakket, opstartinstallatiekopie, installatieprogramma besturingssysteem en de installatiekopie. Deze instellingen kunnen u kiezen hoe distributie van inhoud wordt beheerd op externe distributiepunten die zijn geïdentificeerd als voorbereid:  

    -   **Automatisch inhoud downloaden wanneer pakketten worden toegewezen aan distributiepunten**: Gebruik deze optie wanneer u kleinere pakketten hebt en de instellingen voor plannen en aanvraagbeperking voldoende voor inhoudsdistributie beheersen.  

    -   **Alleen inhoudswijzigingen downloaden naar het distributiepunt**: Gebruik deze optie wanneer u verwacht dat toekomstige updates voor de inhoud in het pakket over het algemeen kleiner is dan het oorspronkelijke pakket. U kunt bijvoorbeeld een toepassing zoals Microsoft Office vooraf plaatsen omdat de initiële pakketgrootte meer dan 700 MB is en is te groot om te verzenden via het netwerk. Echter, updates van inhoud voor dit pakket mogelijk minder dan 10 MB en zijn aanvaardbaar voor distributie over het netwerk. Een ander voorbeeld is stuurprogrammapakketten waarbij de initiële pakketgrootte omvangrijk is, maar het pakket stapsgewijze stuurprogrammatoevoegingen mogelijk klein mogelijk.  

    -   **De inhoud in dit pakket handmatig kopiëren naar het distributiepunt**: Gebruik deze optie wanneer u grote pakketten met inhoud, zoals een besturingssysteem hebt, en u nooit het netwerk gebruiken om de inhoud naar het distributiepunt te distribueren. Wanneer u deze optie selecteert, moet u de inhoud vooraf op het distributiepunt.  

    > [!IMPORTANT]  
    >  De hiervoor vermelde opties zijn van toepassing per pakket en worden alleen gebruikt wanneer een distributiepunt wordt geïdentificeerd als voorbereid. Distributiepunten die niet zijn geïdentificeerd als voorbereid, negeren deze instellingen. In dit geval wordt inhoud altijd gedistribueerd via het netwerk van de siteserver naar de distributiepunten.  

-   **Aan de Inhoudsbibliotheek terugzetten op een siteserver.** Wanneer een siteserver uitvalt, wordt informatie over pakketten en toepassingen die is opgenomen in de Inhoudsbibliotheek als onderdeel van het herstelproces naar de sitedatabase is hersteld, maar de inhoudsbibliotheekbestanden worden niet teruggezet als onderdeel van het proces. Als u een bestandssysteemback-up naar de Inhoudsbibliotheek terugzetten niet hebt, kunt u een voorbereid inhoudsbestand maken van een andere site die de pakketten en toepassingen bevat die u nodig hebt. Vervolgens kunt u het voorbereide inhoudsbestand op de herstelde siteserver uitpakken. Zie voor meer informatie over site-server back-up en herstel [back-up en herstel voor System Center Configuration Manager](/sccm/protect/understand/backup-and-recovery).  

