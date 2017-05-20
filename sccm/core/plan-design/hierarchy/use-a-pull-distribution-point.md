---
title: Pull-distributiepunt | Microsoft-documenten
description: Meer informatie over configuraties en beperkingen voor het gebruik van een pull-distributiepunt met System Center Configuration Manager.
ms.custom: na
ms.date: 2/14/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 7d8f530b-1a39-4a9d-a2f0-675b516da7e4
caps.latest.revision: 9
author: Brenduns
ms.author: brenduns
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9b366262ae59a8cb57c0f1760b961194d17bcf52
ms.openlocfilehash: db5039ff6cb93e3099b096196d49a1f06c315a6b
ms.contentlocale: nl-nl
ms.lasthandoff: 05/17/2017


---

# <a name="use-a-pull-distribution-point-with-system-center-configuration-manager"></a>Een pull-distributiepunt voor System Center Configuration Manager gebruiken

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*


Een pull-distributiepunt voor System Center Configuration Manager is een standaard distributiepunt die gedistribueerde inhoud verkrijgt downloaden van de bronlocatie, zoals een client, in plaats van de inhoud van de siteserver naar het gepusht.  

 Wanneer u inhoud naar een groot aantal distributiepunten op een site implementeert, worden de pull-distributiepunten kunnen u de verwerkingsbelasting op de siteserver verminderen en versnellen van de overdracht van de inhoud naar ieder distributiepunt. Deze efficiëntie wordt bereikt door het offloaden van het proces van het overdragen van de inhoud aan de afzonderlijke distributiepunten via het distributiebeheerproces op de siteserver.  

-   U individuele distributiepunten configureren als pull-distributiepunten.  

-   Voor elk pull-distributiepunt, moet u een of meer brondistributiepunten waaruit implementaties (een pull-distributiepunt kan alleen inhoud verkrijgen via een distributiepunt dat is opgegeven als een brondistributiepunt) kan worden opgehaald.  

-   Wanneer u inhoud naar een pull-distributiepunt distribueert, verwittigt de siteserver de pull-distributiepunt, start vervolgens de download (transfer) van de inhoud vanaf een brondistributiepunt. Een pull-distributiepunt beheert de overdracht van inhoud afzonderlijk door inhoud te downloaden van een distributiepunt dat al over een kopie van de inhoud beschikt.  

Pull-distributiepunten ondersteunen dezelfde configuraties en functionaliteit als standaard Configuration Manager-distributiepunten. Een distributiepunt dat is geconfigureerd als een pull-distributiepunt ondersteunt bijvoorbeeld het gebruik van multicast- en PXE-configuraties, inhoudsvalidatie en distributie van inhoud op aanvraag. Een pull-distributiepunt ondersteunt HTTP- of HTTPS-communicatie van clients, ondersteunt dezelfde certificaatopties als andere distributiepunten en kan afzonderlijk of als een lid van een distributiepuntgroep worden beheerd.  

> [!IMPORTANT]
> Hoewel wanneer u Configuration Manager, een pull-distributiepunt communicaties over HTTP en HTTPS ondersteunt, kunt u alleen de brondistributiepunten die zijn geconfigureerd voor HTTP opgeven. U kunt de Configuration Manager-SDK gebruiken om een brondistributiepunt dat is geconfigureerd voor HTTPS.  

 **De volgende reeks gebeurtenissen treedt op wanneer u inhoud distribueert naar een pull-distributiepunt:**  

-   Zodra inhoud naar een pull-distributiepunt is gedistribueerd, controleert de Package Transfer Manager op de siteserver de sitedatabase om te bevestigen of de inhoud beschikbaar is op het brondistributiepunt. Als dit niet kan bevestigen of de inhoud aanwezig is op het brondistributiepunt voor het pull-distributiepunt, wordt de controle om de 20 minuten herhaald, totdat de inhoud beschikbaar is.  

-   Wanneer door Package Transfer Manager wordt bevestigd dat de inhoud beschikbaar is, meldt dit aan het pull-distributiepunt dat de inhoud kan worden gedownload. Wanneer het pull-distributiepunt deze melding ontvangt, probeert dit om de inhoud te downloaden vanaf de bijbehorende brondistributiepunten.  

-   Nadat het pull-distributiepunt het downloaden van inhoud heeft voltooid, verzendt dit deze status aan een beheerpunt. Echter, als deze status na 60 minuten geen activiteit ontvangen is, de Package Transfer Manager ontwaakt en controleert het pull-distributiepunt om te bevestigen of het pull-distributiepunt de inhoud heeft gedownload. Als het downloaden van de inhoud wordt uitgevoerd, sluimert de Package Transfer Manager gedurende 60 minuten voordat deze het pull-distributiepunt opnieuw controleert. De cyclus gaat door totdat het pull-distributiepunt de inhoudstransfer voltooit.  

**U kunt een pull-distributiepunt configureren** wanneer u het distributiepunt installeert of nadat dit is geïnstalleerd door de eigenschappen van de sitesysteemrol van het distributiepunt te bewerken.  

**U kunt de configuratie voor een pull-distributiepunt verwijderen** door de eigenschappen van het distributiepunt te bewerken. Wanneer u de configuratie van pull-distributiepunt, verwijdert het distributiepunt retourneert en normale bewerkingen, en de siteserver toekomstige inhoud beheert wordt verplaatst naar het distributiepunt.  

## <a name="limitations-for-pull-distribution-points"></a>Beperkingen voor pull-distributiepunten  

-   Een clouddistributiepunt kan niet worden geconfigureerd als een pull-distributiepunt.  

-   Een distributiepunt op siteserver kan niet worden geconfigureerd als een pull-distributiepunt.  

-   **De configuratie voor het pull-distributiepunt wordt door de configuratie voor voorbereide inhoud overschreven**. Een pull-distributiepunt dat is geconfigureerd voor voorbereide inhoud wacht op de inhoud. Deze haalt niet via pull inhoud van het distributiepunt van de bron en, zoals een standaarddistributiepunt met de voorbereide inhoud configuratie biedt ontvangt geen inhoud van de siteserver.  

-   **Een pull-distributiepunt gebruikt geen configuraties voor frequentielimieten** wanneer inhoud wordt overgedragen. Als u een eerder geïnstalleerd distributiepunt configureert als een pull-distributiepunt, worden configuraties voor frequentielimieten opgeslagen, maar niet gebruikt. Als u later de configuratie van pull-distributiepunt verwijdert, worden de frequentielimieten geïmplementeerd, zoals deze eerder zijn geconfigureerd.  

    > [!NOTE]  
    >  Wanneer een distributiepunt is geconfigureerd als een pull-distributiepunt, wordt het tabblad **Frequentielimieten** niet weergegeven in de eigenschappen van het distributiepunt.  

-   Een distributiepunt maakt geen gebruik van de optie **Instellingen voor opnieuw proberen** voor de distributie van inhoud. **Instellingen voor opnieuw proberen** kan worden geconfigureerd als onderdeel van **Eigenschappen van softwaredistributieonderdelen** van elke site. Weergeven of configureren van deze eigenschappen in de **beheer** werkruimte van de Configuration Manager-console, vouw **siteconfiguratie**, en selecteer vervolgens **Sites**. Selecteer vervolgens een site in het deelvenster met resultaten en klikt u op de **Start** tabblad **Siteonderdelen configureren**. Ten slotte selecteren **softwaredistributie**.  

-   Voor het overbrengen van inhoud vanaf een bron distributiepunt in een extern forest, de computer die als host fungeert de pull-distributiepunt moet een Configuration Manager-client is geïnstalleerd. Een netwerktoegangsaccount die toegang het brondistributiepunt tot moet worden geconfigureerd voor gebruik.  

-   Op een computer die is geconfigureerd als een pull-distributiepunt en die een Configuration Manager-client uitvoert, wordt de versie van de client moet dezelfde versie als de Configuration Manager-site die het pull-distributiepunt installeert. Dit is een vereiste voor het pull-distributiepunt voor het gebruik van CCMFramework die geldt voor het pull-distributiepunt en de Configuration Manager-client.  

## <a name="about-source-distribution-points"></a>Brondistributiepunten  
 Wanneer u een pull-distributiepunt configureert, moet u een of meer brondistributiepunten opgeven:  

-   Alleen distributiepunten die in aanmerking komen voor gebruik als brondistributiepunten, worden weergegeven.  

-   Een pull-distributiepunt kan worden opgegeven als een brondistributiepunt voor een ander pull-distributiepunt.  

-   Alleen distributiepunten die ondersteuning bieden voor HTTP kunnen worden opgegeven als brondistributiepunten wanneer u Configuration Manager.  

-   U kunt de Configuration Manager-SDK gebruiken om een brondistributiepunt dat is geconfigureerd voor HTTPS. Voor het gebruik van een brondistributiepunt dat is geconfigureerd voor HTTPS, moet het pull-distributiepunt worden geplaatst op een computer waarop de Configuration Manager-client uitvoert.  

Er kan aan elk distributiepunt in de lijst met brondistributiepunten van een pull-distributiepunt een prioriteit worden toegewezen:  

-   U kunt aan elk brondistributiepunt een afzonderlijke prioriteit toewijzen en u kunt een dezelfde prioriteit toewijzen aan meerdere distributiepunten.  

-   De prioriteit bepaalt in welke volgorde pull-distributiepunten inhoud aanvragen bij brondistributiepunten die bij het pull-distributiepunt horen.  

-   Pull-distributiepunten maken eerst contact met een brondistributiepunt met de laagste waarde voor de prioriteit.  Als er meerdere brondistributiepunten met dezelfde prioriteit zijn, selecteert het pull-distributiepunt een van de bron-distributiepunten die deze prioriteit delen.  

-   Als de inhoud niet beschikbaar is op een geselecteerde bron, probeert het pull-distributiepunt de inhoud te downloaden vanaf een ander distributiepunt met dezelfde prioriteit.  

-   Als de inhoud niet beschikbaar is op alle distributiepunten met een bepaalde prioriteit, probeert het pull-distributiepunt de inhoud te downloaden vanaf een distributiepunt waaraan de eerstvolgende hogere waarde is toegewezen, totdat de inhoud is gevonden of het pull-distributiepunt gedurende 30 minuten de inactieve modus inschakelt voordat het proces opnieuw begint.  

Wanneer een pull-distributiepunt inhoud downloadt vanaf een brondistributiepunt, wordt dat pull-distributiepunt in de kolom **Gebruikte (unieke) clients** van het rapport **Overzicht van gebruik van distributiepunten** geteld als een client.  

 Een pull-distributiepunt gebruikt standaard het eigen **computeraccount** om inhoud vanaf een brondistributiepunt over te dragen. Echter wanneer het pull-distributiepunt overbrengt inhoud vanaf een brondistributiepunt dat zich in een extern forest bevindt, gebruik het pull-distributiepunt altijd van het netwerktoegangsaccount. Dit proces vereist dat de computer de Configuration Manager-client is geïnstalleerd en dat een netwerktoegangsaccount is geconfigureerd voor gebruik en toegang tot het brondistributiepunt heeft.  

## <a name="about-content-transfers"></a>Inhoudsoverdracht  
 Voor het beheren van de overdracht van inhoud, pull-distributiepunten gebruiken de **CCMFramework** onderdeel van de Configuration Manager-clientsoftware.  

-   Cmmframework wordt geïnstalleerd door de **Pulldp.msi** wanneer u het distributiepunt een pull-distributiepunt configureert. Het framework nodig Configuration Manager-client niet.  

-   Nadat het pull-distributiepunt is geïnstalleerd, moet de service CCMExecio op de distributiepuntcomputer worden ingeschakeld omdat het pull-distributiepunt anders niet werkt.  

-   Wanneer het pull-distributiepunt inhoud overdraagt, wordt dit gedaan via **Background Intelligent Transfer Service** (BITS). De bewerkingen worden geregistreerd in het bestand **datatransferservice.log** en in het bestand **pulldp.log** op de distributiepuntcomputer.  

## <a name="see-also"></a>Zie tevens  
 [Basisconcepten voor content management in System Center Configuration Manager](/sccm/core/plan-design/hierarchy/fundamental-concepts-for-content-management)   

