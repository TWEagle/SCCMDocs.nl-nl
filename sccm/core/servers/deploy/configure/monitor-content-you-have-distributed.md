---
title: Inhoud controleren | Microsoft-documenten
description: Inzicht in de gedistribueerde inhoud bewaken met behulp van de Configuration Manager-console.
ms.custom: na
ms.date: 4/17/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 82e8a693-9adf-4ca3-8484-7e101c34c7c1
caps.latest.revision: 5
author: Brenduns
ms.author: brenduns
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: dda2f4c01078fbbd174cbcb30357554c24f6abeb
ms.openlocfilehash: 7659d5789b8ce4e9e0b585a331c8f68869c9492d
ms.contentlocale: nl-nl
ms.lasthandoff: 05/17/2017

---
# <a name="monitor-content-you-have-distributed-with-system-center-configuration-manager"></a>Inhoud die u hebt gedistribueerd met System Center Configuration Manager controleren

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*

De System Center Configuration Manager-console gebruiken om te controleren van inhoud van gedistribueerde, met inbegrip van:  

-   De status voor alle pakkettypen in relatie tot de gekoppelde distributiepunten.  
-   De status van de validatie van inhoud voor de inhoud van een pakket.  
-   De status van inhoud toegewezen aan een specifieke distributiepuntengroep.  
-   De status van inhoud toegewezen aan een distributiepunt.  
-   De status van optionele functies voor afzonderlijke distributiepunten (inhoudsvalidatie, PXE en multicast).  

> [!NOTE]  
>  Configuration Manager controleert alleen de inhoud op een distributiepunt dat zich in de Inhoudsbibliotheek. Inhoud die is opgeslagen op het distributiepunt in het pakket of op aangepaste shares, wordt niet gecontroleerd.  

##  <a name="BKMK_ContentStatus"></a> Controle van de status van inhoud  
 Het knooppunt **Status van inhoud** in de werkruimte **Controle** biedt informatie over inhoudspakketten. U kunt informatie, zoals weergeven in de Configuration Manager-console:  

-   De pakketnaam.  
-   Het type.  
-   Hoeveel distributiepunten van een pakket is verzonden naar.  
-   Het compatibiliteitspercentage.  
-   Wanneer het pakket is gemaakt.  
-   De pakket-ID.  
-   De versie van de gegevensbron.  

U ook gedetailleerde statusinformatie zoeken voor elk pakket, evenals de distributiestatus voor het pakket, met inbegrip van:  

-   Het aantal fouten.  
-   In behandeling distributies.  
-   Het aantal installaties.

U kunt ook om distributies te beheren die gaande naar een distributiepunt of waarbij het distribueren van inhoud naar een distributiepunt is mislukt:  

-   De optie om te annuleren of inhoud opnieuw distribueren is beschikbaar wanneer u het statusbericht voor de implementatie van een distributietaak voor een distributiepunt in de **activumgegevens** deelvenster. Dit deelvenster kunt u vinden in ofwel de **wordt uitgevoerd** tabblad of de **fout** tabblad van het **inhoudsstatus** knooppunt.  
-   Daarnaast de taakgegevens wordt het percentage van de taak dat is voltooid als u de details van een taak weergeven op de **In voortgang** tabblad. De taakgegevens ook wordt het aantal nieuwe pogingen blijven voor een taak, evenals hoeveelheid tijd tot de volgende poging plaatsvindt, wanneer u de details van een taak die beschikbaar is via de **fout** tabblad.  

Wanneer u een implementatie die nog niet is voltooid annuleert, wordt de distributietaak voor het overbrengen van deze inhoud gestopt:  

-   De status van de implementatie wordt vervolgens bijgewerkt om aan te geven dat de distributie is mislukt en dat deze via een gebruikersactie is geannuleerd.  
-   Deze nieuwe status wordt weergegeven de **fout** tabblad.  

> [!TIP]  
>  Wanneer een implementatie bijna voltooid is, is het mogelijk het annuleren van deze distributie niet plaatsvindt voordat de distributie naar het distributiepunt is voltooid. Wanneer dit gebeurt, wordt het annuleren van de implementatie genegeerd en geeft de status van de implementatie uitgevoerd.  

> [!NOTE]  
>  Hoewel u de optie voor het annuleren van een distributie naar een distributiepunt dat zich op een siteserver selecteren kunt, heeft dit geen effect. Dit is omdat de siteserver en het distributiepunt op een servershare site dezelfde inhoud single instance store wijst. Er is geen daadwerkelijke distributietaak annuleren.  

Wanneer u inhoud die eerder mislukte overdracht naar een distributiepunt opnieuw distribueert, begint Configuration Manager onmiddellijk opnieuw distribueren van die inhoud naar het distributiepunt. Configuration Manager wordt de status van de implementatie bijgewerkt, zodat de actieve status van deze opnieuw installeren.  

Gebruik de volgende procedures om weer te geven van de status van inhoud en distributies beheren die gaande zijn of die zijn mislukt.  

### <a name="to-monitor-content-status"></a>De status van inhoud controleren  

1.  Klik in de Configuration Manager-console op **bewaking**.  

2.  In de **bewaking** werkruimte Vouw **distributiestatus**, en klik vervolgens op **inhoudsstatus**. De pakketten worden weergegeven.  

3.  Selecteer het pakket waarvoor u gedetailleerde statusinformatie wilt weergeven.  

4.  Klik op het tabblad **Start** op **Status weergeven**. De gedetailleerde statusinformatie voor het pakket wordt weergegeven.  

### <a name="to-cancel-a-distribution-that-remains-in-progress"></a>Een distributie annuleren die uitgevoerd wordt  

1.  Klik in de Configuration Manager-console op **bewaking**.  

2.  In de **bewaking** werkruimte Vouw **distributiestatus**, en klik vervolgens op **inhoudsstatus**. De pakketten worden weergegeven.  

3.  Selecteer het pakket dat u wilt beheren en klik vervolgens in het detailvenster op **Status weergeven**.  

4.  In de **activumgegevens** deelvenster van de **In voortgang** tabblad, met de rechtermuisknop op de vermelding voor de distributie die u wilt annuleren en selecteer **annuleren**.  

5.  Klik op **Ja** de actie te bevestigen en annuleer de distributietaak naar het distributiepunt.  

### <a name="to-redistribute-content-that-failed-to-distribute"></a>Inhoud die niet worden opnieuw distribueren  

1.  Klik in de Configuration Manager-console op **bewaking**.  

2.  In de **bewaking** werkruimte Vouw **distributiestatus**, en klik vervolgens op **inhoudsstatus**. De pakketten worden weergegeven.  

3.  Selecteer het pakket dat u wilt beheren en klik vervolgens in het detailvenster op **Status weergeven**.  

4.  In de **activumgegevens** deelvenster van de **fout** tabblad, met de rechtermuisknop op de vermelding voor de distributie die u wilt distribueren en selecteer **distribueren**.  

5.  Klik op **Ja** Bevestig de actie en start het opnieuw distribueren naar het distributiepunt.  

## <a name="distribution-point-group-status"></a>Status van distributiepuntengroep  
Het knooppunt **Status van distributiepuntengroep** in de werkruimte **Controle** biedt informatie over distributiepuntengroepen. U kunt informatie zoals bekijken:  

-   De naam van de distributiepuntengroep.  
-   De beschrijving.  
-   Hoeveel distributiepunten lid zijn van de distributie groep verwijzen.  
-   Hoeveel pakken aan de groep zijn toegewezen.  
-   De status van distributiepuntengroep.  
-   Het compatibiliteitspercentage.  

U ook bekijken gedetailleerde statusinformatie voor het volgende:  

-   Fouten voor de distributiepuntengroep.  
-   Hoeveel distributies gaande zijn.
-   Hoeveel zijn succes afgerond.  

### <a name="to-monitor-distribution-point-group-status"></a>De status van een distributiepuntengroep bewaken  

1.  Klik in de Configuration Manager-console op **bewaking**.  

2.  In de **bewaking** werkruimte Vouw **distributiestatus**, en klik vervolgens op **Distributiepuntengroep**. De distributiepuntengroepen worden weergegeven.  

3.  Selecteer de distributiepuntengroep waarvoor u gedetailleerde statusinformatie wilt.  

4.  Klik op het tabblad **Start** op **Status weergeven**. Er wordt gedetailleerde statusinformatie voor de distributiepuntengroep weergegeven.  

## <a name="distribution-point-configuration-status"></a>Configuratiestatus van distributiepunt  
 Het knooppunt **Configuratiestatus van distributiepunt** in de werkruimte **Controle** biedt informatie over de distributiepuntengroep. U kunt weergeven welke kenmerken zijn ingeschakeld voor het distributiepunt, zoals PXE, multicast, inhoud validatie en de distributiestatus voor het distributiepunt. U kunt tevens gedetailleerde statusinformatie voor het distributiepunt weergeven.  

> [!WARNING]  
>  Configuratiestatus van distributiepunt is relatief naar de laatste 24 uur. Als het distributiepunt een fout en dit wordt hersteld is, wordt de foutstatus mogelijk weergegeven tot 24 uur na het herstellen van het distributiepunt weergegeven.  

Gebruik de volgende procedure om de configuratiestatus van een distributiepuntengroep weer te geven.  

### <a name="to-monitor-distribution-point-configuration-status"></a>Bewaken van de configuratiestatus van distributiepunten  

1.  Klik in de Configuration Manager-console op **bewaking**.  

2.  In de **bewaking** werkruimte Vouw **distributiestatus**, en klik vervolgens op **Distributiepuntconfiguraties**. De distributiepunten worden weergegeven.  

3.  Selecteer het distributiepunt waarvoor u gedetailleerde statusinformatie wilt.  

4.  Klik op het tabblad **Details** in het resultatenvenster. De statusinformatie voor het distributiepunt wordt weergegeven.  

## <a name="client-data-sources-dashboard"></a>Client-gegevensbronnen dashboard
Vanaf versie 1610, kunt u de **Client gegevensbronnen** dashboard om te begrijpen wat het gebruik van [Peercache](/sccm/core/plan-design/hierarchy/client-peer-cache) in uw omgeving. Het dashboard wordt gestart nadat clients downloaden inhoud en rapport die informatie teruggestuurd naar de site zodat gegevens worden weergegeven. Dit kan tot 24 uur duren.

> [!TIP]  
> **Peer-clientcache** en de **Client gegevensbronnen** dashboard zijn geïntroduceerd in versie 1610 pre-release-functies. U moet Peer clientcache inschakelen voordat het dashboard van gegevensbronnen van de Client weergegeven in de console wordt. Zie inschakelen Peer clientcache [gebruikmaken van de functies van updates pre-release](/sccm/core/servers/manage/install-in-console-updates#bkmk_prerelease). Het kan tot 24 uur nadat u het inschakelen om te beginnen met het weergeven van gegevens duren.

In de console, gaat u naar **bewaking** > **distributiestatus** > **Client gegevensbronnen**. Hier kunt u een bepaalde periode te kunnen toepassen op het dashboard. Klik in de weergave kunt u de grensgroep of het pakket waarvoor u wilt weergeven. Wanneer informatie bekijkt, kunt u de muis de muisaanwijzer op het oppervlak voor meer informatie over de verschillende inhoud of bronnen van beleid.

Deze gegevens omvatten het volgende:  
- **Client inhoudsbronnen**: Hiermee wordt de bron waarvan clients inhoud heeft.
- **Distributiepunten**: Geeft het aantal distributiepunten die deel van de geselecteerde Grensgroep uitmaken.
- **Clients die een distributiepunt gebruikt**: Het aantal clients die zich in de geselecteerde Grensgroep, dit wordt weergegeven hoeveel gebruikt een distributiepunt inhoud op te halen.
- **Peer-Cache bronnen**: Voor de geselecteerde Grensgroep leert hierbij u hoeveel peer cache bronnen downloadgeschiedenis hebben gerapporteerd.
- **Clients die u een peer gebruikt**: Het aantal clients die zich in de geselecteerde Grensgroep, dit wordt weergegeven hoeveel gebruikt een peer-cachebron inhoud op te halen.



U kunt ook een nieuw rapport **gegevensbronnen voor Client - samenvatting**om weer te geven een overzicht van de client-gegevensbronnen voor elke grensgroep.

