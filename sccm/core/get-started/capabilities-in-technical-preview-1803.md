---
title: Technische Preview 1803
titleSuffix: Configuration Manager
description: Meer informatie over nieuwe functies die beschikbaar zijn in de Configuration Manager Technical Preview-versie 1803.
ms.custom: na
ms.date: 03/27/2018
ms.prod: configuration-manager
ms.technology:
- configmgr-other
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 56dc4b07-5aa4-43e2-9be8-d26ae5ff5613
author: aczechowski
ms.author: aaroncz
manager: dougeby
ms.openlocfilehash: f3c200fe699f85c195e41fc2b395a3d710b1788a
ms.sourcegitcommit: d3863a9b34f9925515cabe9a290a6c733e10108b
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/04/2018
---
# <a name="capabilities-in-technical-preview-1803-for-system-center-configuration-manager"></a>Mogelijkheden van Technical Preview 1803 voor System Center Configuration Manager

*Van toepassing op: System Center Configuration Manager (Technical Preview)*

Dit artikel bevat de functies die beschikbaar in de Technical Preview voor Configuration Manager versie 1803 zijn. U kunt deze versie om te werken en nieuwe mogelijkheden toevoegen aan uw technical preview-site installeren. 

Controleer de [Technical Preview](/sccm/core/get-started/technical-preview) artikel voordat u deze update installeert. Dit artikel familiarizes u met de algemene vereisten en beperkingen voor het gebruik van een technical preview hoe tussen versies en hoe u feedback kunt bijwerken.     


<!--  Known Issues Template   
## Known Issues in this Technical Preview:
-   **Issue Name**. Details
    Workaround details.
-->


</br>

**Hier volgen nieuwe functies die u met deze versie kunt uitproberen.**  



 
## <a name="pull-distribution-points-support-cloud-distribution-points-as-source"></a>Pull-distributiepunt punten ondersteuning clouddistributiepunten als bron  
<!--1321554-->
Veel klanten gebruiken [pull-distributiepunten](/sccm/core/plan-design/hierarchy/use-a-pull-distribution-point) in externe of filialen die inhoud vanaf een brondistributiepunt via het WAN downloaden. Als uw externe kantoren betere verbinding met het internet hebben, of om de belasting van uw WAN-koppelingen te verminderen, kunt u nu gebruiken een [clouddistributiepunt](/sccm/core/plan-design/hierarchy/use-a-cloud-based-distribution-point) in Microsoft Azure als de bron. Wanneer u een bron toevoegen op de **Pull-distributiepunt** tabblad van de verdeling eigenschappen, wordt elk cloud-distributiepunt op de site wordt nu weergegeven als een beschikbaar distributiepunt. Het gedrag van beide sitesysteemrollen blijft hetzelfde anders. 

### <a name="prerequisites"></a>Vereisten
- Het pull-distributiepunt moet toegang tot het internet om te communiceren met Microsoft Azure.
- De inhoud moet worden gedistribueerd naar het brondistributiepunt voor de cloud.

> [!Note]  
> Deze functie de kosten voor uw Azure-abonnement voor de opslag- en netwerkstations uitgaande gegevens. Zie voor meer informatie de [kosten van het gebruik van cloud-gebaseerd distributiepunt](/sccm/core/plan-design/hierarchy/use-a-cloud-based-distribution-point#BKMK_CloudDPCost).



## <a name="partial-download-support-in-client-peer-cache-to-reduce-wan-utilization"></a>Ondersteuning voor gedeeltelijke downloaden in client-peer-cache te reduceren het verbruik van WAN-
<!--1357346-->
Client-peer-cache bronnen kunnen nu inhoud verdelen in delen. Deze onderdelen minimaliseert de netwerkoverdracht om het verbruik van de WAN. Het beheerpunt geeft meer gedetailleerde tracering van de inhoud delen. Er wordt geprobeerd meer dan één downloaden van het dezelfde inhoud per grensgroep elimineren. 

### <a name="example-scenario"></a>Voorbeeldscenario 's
Contoso heeft een enkele primaire site met twee grensgroepen: Hoofdkantoor (hoofdkantoor) en het filiaal. Er is een 30 minuten terugval relatie tussen de grensgroepen. Het beheerpunt en distributiepunt voor de site zijn alleen in de grens van het hoofdkantoor. De locatie van de office vertakking is geen lokaal distributiepunt. Twee van de vier clients in het filiaal zijn geconfigureerd als peer-cache-bronnen. 

![Diagram van de netwerkconfiguratie zoals beschreven voor het voorbeeldscenario](media/1357346-peer-cache-source-parts.png)

1. U richt een implementatie met de inhoud naar alle vier clients in het filiaal. U alleen de inhoud naar het distributiepunt gedistribueerd.
2. Client3 en Client4 beschikt niet over van een lokale bron voor de implementatie. Clients kunnen 30 minuten wachten voordat teruggevallen op de externe grensgroep Hiermee geeft u het beheerpunt.
3. CLIENT1 (PCS1) is de eerste peer-cachebron vernieuwen van beleid met het beheerpunt. Omdat deze client is ingeschakeld als peer-cache-bron, het beheerpunt Hiermee geeft u het onmiddellijk starten deel A downloaden vanaf het distributiepunt.  
4. Wanneer Client2 (PCS2) neemt contact op met het beheerpunt, zoals deel A al uitgevoerd wordt, maar niet nog klaar is, het beheerpunt Hiermee geeft u het onmiddellijk starten deel B downloaden vanaf het distributiepunt.
5. PCS1 klaar is met het downloaden van deel A en onmiddellijk een melding van het beheerpunt. Als onderdeel B al wordt uitgevoerd, maar niet nog klaar is, het beheerpunt geeft de instructie om te beginnen met het onderdeel C downloaden vanaf het distributiepunt.
6. PCS2 klaar is met het downloaden van deel B en onmiddellijk een melding van het beheerpunt. Het beheerpunt geïnstrueerd om te beginnen met het onderdeel D downloaden vanaf het distributiepunt. 
7. PCS1 is voltooid deel C downloaden en onmiddellijk een melding van het beheerpunt. Het beheerpunt informeert het dat er geen meer onderdelen die beschikbaar van het externe distributiepunt zijn. Het deel B downloaden van de lokale peer, PCS2 Hiermee geeft u het beheerpunt.
8. Dit proces wordt voortgezet tot zowel client-peer-cache-bronnen alle onderdelen van elkaar hebben. Het beheerpunt bepaalt de volgorde van onderdelen van het externe distributiepunt voordat de instructie van de peer-cache-bronnen voor het downloaden van delen van lokale peers. 
9. Client3 is de eerste beleid vernieuwen nadat de 30 minuten fallback is verlopen. Er wordt nu gecontroleerd op het beheerpunt dat informeert het de client van een nieuwe lokale bronnen. In plaats van de inhoud van de volledige vanaf het distributiepunt downloaden via het WAN, downloaden het van de inhoud volledig uit een van de client-peer-cache-bronnen. Clients prioriteren lokale peer-bronnen. 

> [!Note]  
> Als het aantal client-peer-cache bronnen groter dan het aantal inhoud delen is, klikt u vervolgens met het beheerpunt de bronnen van de aanvullende peer-cache moet worden gewacht voor terugval als een normale client opdracht. 


### <a name="try-it-out"></a>Probeer het nu!
 Probeer de taken uitvoeren. Verzend **Feedback** van de **Start** tabblad van het lint laat ons weten hoe het is gegaan.

1. Instellen van [grensgroepen](/sccm/core/servers/deploy/configure/boundary-groups) en [peer-cache-bronnen](/sccm/core/plan-design/hierarchy/client-peer-cache) per normaal.
2. Ga in de Configuration Manager-console naar de **beheer** werkruimte Vouw **siteconfiguratie**, en selecteer **Sites**. Klik op **hiërarchie-instellingen** in het lint. 
3. Op de **algemene** tabblad, schakelt u de optie voor het **client-peer-cache bronnen om inhoud te verdelen in delen configureren**. 
4. Een vereiste implementatie maken met inhoud.  

   > [!Note]  
   > Deze functie werkt alleen wanneer de client de inhoud op de achtergrond, zoals met een vereiste implementatie downloadt. Op aanvraag downloads, zoals wanneer de gebruiker een beschikbare installatie installeert in Software Center gedraagt zich gewoon.  

1. Om ze te bekijken voor het verwerken van het downloaden van inhoud in delen, onderzoekt de **ContentTransferManager.log** op de client-peer-cache-bron en de **MP_Location.log** op het beheerpunt.  
 



## <a name="maintenance-windows-in-software-center"></a>Onderhoudsvensters in Software Center
<!--1358131-->
De volgende geplande onderhoudsvenster wordt nu weergegeven in software Center. Overschakelen op het tabblad Status van de installatie de weergave van alle te verzenden. Het tijdsbereik en een lijst met implementaties die zijn gepland wordt weergegeven. De lijst is leeg als er geen onderhoudsvensters toekomstig. 

![Software Center waarin de lijst met toekomstige implementaties op het tabblad installatiestatus](media/1358131-software-center-maintenance-windows.png)


## <a name="custom-tab-for-webpage-in-software-center"></a>Aangepaste tabblad voor de webpagina in Software Center
<!--1358132-->
Nu kunt u een aangepaste tabblad als u wilt openen van een webpagina in Software Center. Deze functie kunt u inhoud weergeven aan uw eindgebruikers op een consistente en betrouwbare manier. De volgende lijst bevat enkele voorbeelden:
- Contact opnemen met IT: informatie over het contact op met uw organisatie IT-afdeling
- IT-ondersteuning: IT selfservice acties zoals het zoeken van een knowledge base of een ondersteuningsticket openen.
- Documentatie voor eindgebruikers: artikelen voor gebruikers in uw organisatie op de diverse IT-onderwerpen, zoals toepassingen of het upgraden naar Windows 10.


### <a name="try-it-out"></a>Probeer het nu!
 Probeer de taken uitvoeren. Verzend **Feedback** van de **Start** tabblad van het lint laat ons weten hoe het is gegaan.

1. In de Configuration Manager-console **beheer** werkruimte **clientinstellingen** knooppunt, open de **Standaardclientinstellingen** beleid.
2. Selecteer de **Software Center** groep.
3. Voor **instellingen van Software Center**, klikt u op **aanpassen**.
4. Overschakelen naar de **tabbladen** tabblad.
5. De optie **opgeven van een aangepast tabblad voor Software Center**.
    1. Voer een naam in de **tabbladnaam** tekstveld. Deze naam is wat wordt weergegeven in Software Center aan de gebruiker.
    2. Geef een geldige URL in de **inhoud URL** tekstveld. Deze URL is de inhoud die Software Center wordt weergegeven wanneer gebruikers op dit tabblad.

> [!Tip]  
> Software Center gebruikmaakt van Internet Explorer-onderdelen voor het opbouwen van de webpagina.

## <a name="enable-third-party-software-update-support-on-clients"></a>Ondersteuning voor software-update van derden op clients inschakelen

Nu kunt u de configuratie van Configuration Manager-clients voor software-updates van derden. Wanneer u **van derden software-updates inschakelen** voor de onderdeeleigenschappen SUP de SUP het handtekeningcertificaat dat wordt gebruikt door WSUS voor updates van derden wordt gedownload. <!--1357605-->

Selecteren **van derden software-updates inschakelen** in de clientinstellingen doet het volgende: 
- Op de client wordt het beleid voor 'Toestaan updates voor een intranet-locatie van Microsoft-updateservice ondertekende' 
- Het handtekeningcertificaat in het archief met vertrouwde uitgevers op de client geïnstalleerd. 

### <a name="try-it-out"></a>Probeer het nu!
 Probeer de taken uitvoeren. Verzend **Feedback** van de **Start** tabblad van het lint laat ons weten hoe het is gegaan.

1. Op de bovenste site in de Configuration Manager-hiërarchie, gaat u naar de **beheer** knooppunt uitvouwen **siteconfiguratie**, klikt u vervolgens **Sites**.
2. Met de rechtermuisknop op de bovenste siteserver en selecteer **Siteonderdelen configureren** vervolgens **Software-updatepunt**.
3. Klik op de **Updates van derden** tabblad en Controleer **van derden software-updates inschakelen**.
4. Open **clientinstellingen** en Ga naar de instellingen voor **Software-Updates**.
5. Zorg ervoor dat **van derden software-updates inschakelen** is ingesteld op **Ja**.

## <a name="enable-copypaste-of-asset-details-from-monitoring-views"></a>Kopiëren en plakken van activumgegevens van weergaven bewaking inschakelen
Als gevolg van uw [feedback van gebruikers stem](https://configurationmanager.uservoice.com/forums/300492-ideas/suggestions/20234866-allow-us-to-copy-information-out-of-the-asset-det) kunt u nu kopiëren/plakken in het deelvenster details van activa in de implementatie en distributie status monitoring-weergaven inschakelen.  <!--1357552-->

## <a name="scap-extensions"></a>SCAP-extensies
De voorlopige versie van de SCAP-extensies is beschikbaar in de map Cd.latest onder SMSSETUP\TOOLS\ConfigMgrSCAPExtension\ConfigMgrExtensionsForSCAP.msi. Deze voorlopige versie van de SCAP-extensies kan worden geïnstalleerd op alle ondersteunde versies van de huidige vertakking van Configuration Manager en LTSB 1606. Zie voor meer informatie [over de Security Content Automation Protocol (SCAP) extensies](/sccm/compliance/plan-design/scap/about-scap).



## <a name="next-steps"></a>Volgende stappen
Zie voor meer informatie over het installeren of bijwerken van de technical preview vertakking [Technical Preview voor System Center Configuration Manager](/sccm/core/get-started/technical-preview).    
