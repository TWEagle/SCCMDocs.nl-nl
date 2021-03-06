---
title: Pull-distributiepunt
titleSuffix: Configuration Manager
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
caps.latest.revision: ''
author: aczechowski
ms.author: aaroncz
manager: angrobe
ms.openlocfilehash: 3ef93ae505c2af709a3bd1e6a0e7a278993a77ff
ms.sourcegitcommit: 27da4be015f1496b7b89ebddb517a2685f1ecf74
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 03/28/2018
---
# <a name="use-a-pull-distribution-point-with-system-center-configuration-manager"></a>Een pull-distributiepunt voor System Center Configuration Manager gebruiken

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*


Een pull-distributiepunt voor System Center Configuration Manager is een standaarddistributiepunt dat gedistribueerde inhoud ophaalt downloaden via een bronlocatie zoals een client, in plaats van de inhoud wordt gepusht vanaf de siteserver.  

 Wanneer u inhoud naar een groot aantal distributiepunten op een site implementeert, worden de pull-distributiepunten kunnen u de verwerkingsbelasting op de siteserver verminderen en versnellen van de overdracht van de inhoud naar elk distributiepunt. Deze efficiëntie wordt bereikt door het offloaden van het proces van het overdragen van de inhoud aan de afzonderlijke distributiepunten via het distributiebeheerproces op de siteserver.  

-   U kunt afzonderlijke distributiepunten als pull-distributiepunten configureren.  

-   Voor elk pull-distributiepunt, moet u een of meer brondistributiepunten waaruit implementaties (een pull-distributiepunt kan alleen inhoud ophalen van een distributiepunt dat is opgegeven als een brondistributiepunt) kunnen worden opgehaald.  

-   Wanneer u inhoud naar een pull-distributiepunt distribueert, verwittigt de server het pull-distributiepunt, vervolgens begint met het downloaden (transfer) van de inhoud vanaf een brondistributiepunt. Een pull-distributiepunt beheert de overdracht van inhoud afzonderlijk door inhoud te downloaden van een distributiepunt dat al over een kopie van de inhoud beschikt.  

Pull-distributiepunten ondersteunen dezelfde configuraties en functionaliteit als standaard Configuration Manager-distributiepunten. Een distributiepunt dat is geconfigureerd als een pull-distributiepunt ondersteunt bijvoorbeeld het gebruik van multicast- en PXE-configuraties, inhoudsvalidatie en distributie van inhoud op aanvraag. Een pull-distributiepunt ondersteunt HTTP- of HTTPS-communicatie van clients, ondersteunt dezelfde certificaatopties als andere distributiepunten en kan afzonderlijk of als een lid van een distributiepuntgroep worden beheerd.  

> [!IMPORTANT]
> Hoewel een pull-distributiepunt communicatie via HTTP en HTTPS, ondersteunt wanneer u Configuration Manager gebruikt, kunt u alleen brondistributiepunten die zijn geconfigureerd voor HTTP opgeven. U kunt de Configuration Manager-SDK gebruiken om op te geven van een brondistributiepunt dat is geconfigureerd voor HTTPS.  

 **De volgende reeks gebeurtenissen treedt op wanneer u inhoud distribueert naar een pull-distributiepunt:**  

-   Zodra inhoud naar een pull-distributiepunt is gedistribueerd, controleert de Package Transfer Manager op de siteserver de sitedatabase om te bevestigen of de inhoud beschikbaar is op het brondistributiepunt. Als dit niet kan bevestigen of de inhoud aanwezig is op het brondistributiepunt voor het pull-distributiepunt, wordt de controle om de 20 minuten herhaald, totdat de inhoud beschikbaar is.  

-   Wanneer door Package Transfer Manager wordt bevestigd dat de inhoud beschikbaar is, meldt dit aan het pull-distributiepunt dat de inhoud kan worden gedownload. Als deze melding mislukt Er wordt opnieuw geprobeerd op basis van het onderdeel Software distributie **instellingen voor opnieuw proberen** voor pull-distributiepunten. Wanneer het pull-distributiepunt deze melding ontvangt, probeert dit om de inhoud te downloaden vanaf de bijbehorende brondistributiepunten.  

-   Terwijl het pull-distributiepunt de inhoud downloadt de Package Transfer Manager de status op basis van het onderdeel Software-verdeling wordt pollen **Status van navraaginstellingen** voor pull-distributiepunten.  Wanneer het pull-distributiepunt is voltooid voor het downloaden van inhoud, verzendt dit deze status naar een beheerpunt.

**U kunt een pull-distributiepunt configureren** wanneer u het distributiepunt installeert of nadat dit is geïnstalleerd door de eigenschappen van de sitesysteemrol van het distributiepunt te bewerken.  

**U kunt de configuratie voor een pull-distributiepunt verwijderen** door de eigenschappen van het distributiepunt te bewerken. Wanneer u de pull-distributiepuntconfiguratie, verwijdert het distributiepunt weer normaal functioneert en beheert de siteserver toekomstige inhoud worden overgebracht naar het distributiepunt.  

## <a name="to-configure-software-distribution-component-for-pull-distribution-points"></a>Softwareonderdeel van het distributiepunt configureren voor pull-distributiepunten

1.  Kies in de Configuration Manager-console **beheer** > **Sites**.  

2.  Selecteer de gewenste site en selecteer **Siteonderdelen configureren** > **softwaredistributie**

3. Selecteer de **Pull-distributiepunt** tabblad.  

4.  In de **instellingen voor opnieuw proberen** lijst, configureer de volgende waarden:  

    -   **Aantal nieuwe pogingen** -het aantal keren dat de Package Transfer Manager probeert het pull-distributiepunt de inhoud te downloaden melden.  Als dit aantal is overschreden. de Package Transfer Manager de overdracht wordt geannuleerd.

    -   **Vertraging optreden voordat het opnieuw proberen (minuten)** -het aantal minuten dat de Package Transfer Manager tussen pogingen wachten moet. 

5.  In de **Status van navraaginstellingen** lijst, configureer de volgende waarden:  

    -   **Aantal polls** -het aantal keren dat de Package Transfer Manager neemt contact op met de pull-distributiepunt voor het ophalen van de status van de taak.  Als dit aantal wordt overschreden, voordat de taak is voltooid de Package Transfer Manager de overdracht wordt geannuleerd.

    -   **Vertraging optreden voordat het opnieuw proberen (minuten)** -het aantal minuten dat de Package Transfer Manager tussen pogingen wachten moet. 
    
    > [!NOTE]  
    >  Wanneer de Package Transfer Manager een taak annuleert, omdat het aantal Status polling nieuwe pogingen is overschreden blijven het pull-distributiepunt de inhoud te downloaden.  Wanneer deze is voltooid, wordt het juiste statusbericht worden verzonden naar de Package Transfer Manager en de-console geeft de nieuwe status.
    
## <a name="limitations-for-pull-distribution-points"></a>Beperkingen voor pull-distributiepunten  

-   Een clouddistributiepunt kan niet worden geconfigureerd als een pull-distributiepunt.  

-   Een distributiepunt op siteserver kan niet worden geconfigureerd als een pull-distributiepunt.  

-   **De configuratie voor het pull-distributiepunt wordt door de configuratie voor voorbereide inhoud overschreven**. Een pull-distributiepunt dat is geconfigureerd voor voorbereide inhoud wacht op de inhoud. Dit komt niet haalt inhoud binnen vanuit het brondistributiepunt en, zoals een standaarddistributiepunt punt met de configuratie van het voorbereide inhoud, ontvangt geen inhoud van de siteserver.  

-   **Een pull-distributiepunt gebruikt geen configuraties voor schema- of snelheid limieten** wanneer inhoud wordt overgedragen. Als u een eerder geïnstalleerd distributiepunt configureert als een pull-distributiepunt, zijn configuraties voor planning en frequentie grenzen opgeslagen, maar niet gebruikt. Als u later de pull-distributiepuntconfiguratie verwijdert, worden de configuratie van de planning en frequentie limiet geïmplementeerd zoals eerder is geconfigureerd.  

    > [!NOTE]  
    >  Wanneer een distributiepunt is geconfigureerd als een pull-distributiepunt, de **planning** en **frequentielimieten** tabbladen zijn niet zichtbaar in de eigenschappen van het distributiepunt.  

-   Pull-distributiepunten gebruik niet de instellingen op de **algemene** tabblad van de **eigenschappen van Softwaredistributieonderdelen** voor elke site.  Dit omvat de **gelijktijdige distributie** en **Multicast opnieuw** instelling.  Gebruik de **Pull-distributiepunt** tabblad instellingen configureren voor pull-distributiepunten.

-   Om over te dragen van inhoud van een bron distributiepunt in een extern forest, de computer die als host fungeert de pull-distributiepunt moet een Configuration Manager-client geïnstalleerd hebben. Een netwerktoegangsaccount die toegang heeft tot het brondistributiepunt moet worden geconfigureerd voor gebruik.  

-   Op een computer die is geconfigureerd als een pull-distributiepunt en die een Configuration Manager-client wordt uitgevoerd, wordt de versie van de client moet dezelfde versie als de Configuration Manager-site die het pull-distributiepunt installeert. Dit is een vereiste voor het pull-distributiepunt voor het gebruik van CCMFramework die geldt voor zowel het pull-distributiepunt en de Configuration Manager-client.  

## <a name="about-source-distribution-points"></a>Brondistributiepunten  
 Wanneer u een pull-distributiepunt configureert, moet u een of meer brondistributiepunten opgeven:  

-   Alleen distributiepunten die in aanmerking komen voor gebruik als brondistributiepunten, worden weergegeven.  

-   Een pull-distributiepunt kan worden opgegeven als een brondistributiepunt voor een ander pull-distributiepunt.  

-   Alleen distributiepunten die ondersteuning bieden voor HTTP kunnen worden opgegeven als brondistributiepunten wanneer u Configuration Manager gebruiken.  

-   U kunt de Configuration Manager-SDK gebruiken om op te geven van een brondistributiepunt dat is geconfigureerd voor HTTPS. Voor het gebruik van een brondistributiepunt dat is geconfigureerd voor HTTPS, moet het pull-distributiepunt worden geplaatst op een computer waarop de Configuration Manager-client wordt uitgevoerd.  

Er kan aan elk distributiepunt in de lijst met brondistributiepunten van een pull-distributiepunt een prioriteit worden toegewezen:  

-   U kunt aan elk brondistributiepunt een afzonderlijke prioriteit toewijzen en u kunt een dezelfde prioriteit toewijzen aan meerdere distributiepunten.  

-   De prioriteit bepaalt in welke volgorde pull-distributiepunten inhoud aanvragen bij brondistributiepunten die bij het pull-distributiepunt horen.  

-   Pull-distributiepunten maken eerst contact met een brondistributiepunt met de laagste waarde voor de prioriteit.  Als er meerdere brondistributiepunten met dezelfde prioriteit zijn, selecteert het pull-distributiepunt een van de bron-distributiepunten die deze prioriteit delen.  

-   Als de inhoud niet beschikbaar is op een geselecteerde bron, probeert het pull-distributiepunt de inhoud te downloaden vanaf een ander distributiepunt met dezelfde prioriteit.  

-   Als de inhoud niet beschikbaar is op alle distributiepunten met een bepaalde prioriteit, probeert het pull-distributiepunt de inhoud te downloaden vanaf een distributiepunt waaraan de eerstvolgende hogere waarde is toegewezen, totdat de inhoud is gevonden of het pull-distributiepunt gedurende 30 minuten de inactieve modus inschakelt voordat het proces opnieuw begint.  

Wanneer een pull-distributiepunt inhoud downloadt vanaf een brondistributiepunt, wordt dat pull-distributiepunt in de kolom **Gebruikte (unieke) clients** van het rapport **Overzicht van gebruik van distributiepunten** geteld als een client.  

 Een pull-distributiepunt gebruikt standaard het eigen **computeraccount** om inhoud vanaf een brondistributiepunt over te dragen. Echter, wanneer het pull-distributiepunt overbrengt inhoud vanaf een brondistributiepunt dat zich in een extern forest, het pull-distributiepunt gebruikt altijd de account voor netwerktoegang. Dit proces vereist dat de computer de Configuration Manager-client is geïnstalleerd heeft en dat een netwerktoegangsaccount is geconfigureerd voor gebruik en toegang tot het brondistributiepunt heeft.  

## <a name="about-content-transfers"></a>Inhoudsoverdracht  
 Als u wilt beheren de overdracht van inhoud, pull-distributiepunten gebruiken de **CCMFramework** onderdeel van de Configuration Manager-clientsoftware.  

-   Dit framework wordt geïnstalleerd door de **Pulldp.msi** wanneer u het distributiepunt naar een pull-distributiepunt configureert. Het framework vereist geen Configuration Manager-client.  

-   Nadat het pull-distributiepunt is geïnstalleerd, moet de service CCMExecio op de distributiepuntcomputer worden ingeschakeld omdat het pull-distributiepunt anders niet werkt.  
<!--sms.503672 -Clarified BITS use-->
-   Wanneer het pull-distributiepunt inhoud overdraagt, wordt dit gedaan met behulp van de **Background Intelligent Transfer Service** (BITS) is ingebouwd in de Windows-besturingssysteem. Een pull-distributiepunt nodig niet de optionele functie BITS IIS-serveruitbreiding moet worden geïnstalleerd.

-  Het pull-distributiepunt de werking ervan wordt geregistreerd in de **datatransferservice.log** en de **pulldp.log** op de distributiepuntcomputer.

## <a name="see-also"></a>Zie tevens  
 [Basisconcepten voor inhoudsbeheer in System Center Configuration Manager](/sccm/core/plan-design/hierarchy/fundamental-concepts-for-content-management)   
