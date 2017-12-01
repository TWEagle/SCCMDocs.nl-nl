---
title: Inhoud controleren
titleSuffix: Configuration Manager
description: Begrijpen hoe gedistribueerde inhoud controleren met behulp van de Configuration Manager-console.
ms.custom: na
ms.date: 4/17/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 82e8a693-9adf-4ca3-8484-7e101c34c7c1
caps.latest.revision: "5"
author: mstewart
ms.author: mstewart
manager: angrobe
ms.openlocfilehash: 108f3e7ae61bb720c765675530258db6c1628792
ms.sourcegitcommit: 7fe45ff75f05f7cc03ad021db8119791abe18049
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/01/2017
---
# <a name="monitor-content-you-have-distributed-with-system-center-configuration-manager"></a>Inhoud die u hebt gedistribueerd met System Center Configuration Manager controleren

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*

De System Center Configuration Manager-console gebruiken om te controleren van gedistribueerde inhoud, met inbegrip van:  

-   De status voor alle pakkettypen in relatie tot de gekoppelde distributiepunten.  
-   De status van de validatie van inhoud voor de inhoud van een pakket.  
-   De status van inhoud toegewezen aan een specifieke distributiepuntengroep.  
-   De status van inhoud toegewezen aan een distributiepunt.  
-   De status van optionele functies voor elk distributiepunt (inhoudsvalidatie, PXE en multicast).  

> [!NOTE]  
>  Configuration Manager controleert alleen de inhoud op een distributiepunt dat zich in de Inhoudsbibliotheek bevindt. Inhoud die is opgeslagen op het distributiepunt in het pakket of op aangepaste shares wordt niet gecontroleerd.  

##  <a name="BKMK_ContentStatus"></a> Controle van de status van inhoud  
 Het knooppunt **Status van inhoud** in de werkruimte **Controle** biedt informatie over inhoudspakketten. In de Configuration Manager-console kunt u informatie, zoals bekijken:  

-   De naam van het pakket.  
-   Het type.  
-   Hoeveel distributiepunten een pakket is verzonden naar.  
-   Het compatibiliteitspercentage.  
-   Wanneer het pakket is gemaakt.  
-   De pakket-ID.  
-   De versie van de gegevensbron.  

U ook gedetailleerde statusinformatie zoeken voor elk pakket, evenals de distributiestatus voor het pakket, met inbegrip van:  

-   Het aantal fouten.  
-   In behandeling distributies.  
-   Het aantal installaties.

U kunt ook distributies die worden uitgevoerd naar een distributiepunt, of die is mislukt voor het distribueren van inhoud naar een distributiepunt beheren:  

-   De optie om te annuleren of inhoud opnieuw distribueren is beschikbaar wanneer u het statusbericht voor de implementatie van een distributietaak voor een distributiepunt in de **activumgegevens** deelvenster. Dit deelvenster kunt u vinden in ofwel de **In uitvoering** tabblad of de **fout** tabblad van de **inhoudsstatus** knooppunt.  
-   Bovendien de taakgegevens wordt het percentage van de taak die is voltooid wanneer u de details van een taak weergeven op de **In uitvoering** tabblad. De taakgegevens ook wordt het aantal nieuwe pogingen die voor een taak, blijven ook hoe lang voordat de volgende poging plaatsvindt, wanneer u de details van een taak die beschikbaar is via de **fout** tabblad.  

Wanneer u een implementatie die nog niet voltooid annuleert, wordt de distributietaak naar het overbrengen van deze inhoud gestopt:  

-   De status van de implementatie wordt vervolgens bijgewerkt om aan te geven dat de distributie is mislukt en via een gebruikersactie is geannuleerd.  
-   Deze nieuwe status wordt weergegeven de **fout** tabblad.  

> [!TIP]  
>  Wanneer een implementatie bijna is voltooid, is het mogelijk de actie te annuleren die distributie niet plaatsvindt voordat de distributie naar het distributiepunt is voltooid. Wanneer dit gebeurt, wordt de actie voor annuleren van de implementatie genegeerd en wordt de status voor de implementatie wordt weergegeven als geslaagd.  

> [!NOTE]  
>  Hoewel u de optie voor het annuleren van een distributie naar een distributiepunt dat zich op een siteserver bevindt selecteren kunt, heeft dit geen effect. Dit is omdat de siteserver en de distributie op een servershare site dezelfde single instance content store wijst. Er is geen daadwerkelijke distributietaak te annuleren.  

Wanneer u inhoud opnieuw die eerder mislukte overdracht naar een distributiepunt distribueren, onmiddellijk Configuration Manager opnieuw distribueren van die inhoud naar het distributiepunt. Configuration Manager-updates de status van de implementatie in overeenstemming met de actieve status van deze opnieuw installeren.  

Gebruik de volgende procedures om weer te geven van de status van inhoud en distributies beheren die worden uitgevoerd of die is mislukt.  

### <a name="to-monitor-content-status"></a>De status van inhoud controleren  

1.  Klik in de Configuration Manager-console op **bewaking**.  

2.  In de **bewaking** werkruimte Vouw **distributiestatus**, en klik vervolgens op **inhoudsstatus**. De pakketten worden weergegeven.  

3.  Selecteer het pakket waarvoor u gedetailleerde statusinformatie wilt.  

4.  Klik op het tabblad **Start** op **Status weergeven**. De gedetailleerde statusinformatie voor het pakket wordt weergegeven.  

### <a name="to-cancel-a-distribution-that-remains-in-progress"></a>Een distributiepunt dat nog in voortgang annuleren  

1.  Klik in de Configuration Manager-console op **bewaking**.  

2.  In de **bewaking** werkruimte Vouw **distributiestatus**, en klik vervolgens op **inhoudsstatus**. De pakketten worden weergegeven.  

3.  Selecteer het pakket dat u wilt beheren en klik vervolgens in het detailvenster op **Status weergeven**.  

4.  In de **activumgegevens** deelvenster van de **In uitvoering** tabblad, met de rechtermuisknop op de vermelding voor de distributie die u wilt annuleren en selecteer **annuleren**.  

5.  Klik op **Ja** voor de actie te bevestigen en annuleer de distributietaak naar het distributiepunt.  

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
-   Hoeveel pakketten aan de groep zijn toegewezen.  
-   De status van distributiepuntengroep.  
-   Het compatibiliteitspercentage.  

U ook bekijken gedetailleerde statusinformatie voor het volgende:  

-   Fouten voor de distributiepuntengroep.  
-   Hoeveel distributies gaande zijn.
-   Hoeveel distributies er zijn uitgevoerd.  

### <a name="to-monitor-distribution-point-group-status"></a>De status van een distributiepuntengroep bewaken  

1.  Klik in de Configuration Manager-console op **bewaking**.  

2.  In de **bewaking** werkruimte Vouw **distributiestatus**, en klik vervolgens op **Status van Distributiepuntengroep**. De distributiepuntengroepen worden weergegeven.  

3.  Selecteer de distributiepuntengroep waarvoor u gedetailleerde statusinformatie wilt.  

4.  Klik op het tabblad **Start** op **Status weergeven**. Er wordt gedetailleerde statusinformatie voor de distributiepuntengroep weergegeven.  

## <a name="distribution-point-configuration-status"></a>Configuratiestatus van distributiepunt  
 Het knooppunt **Configuratiestatus van distributiepunt** in de werkruimte **Controle** biedt informatie over de distributiepuntengroep. U kunt weergeven welke kenmerken zijn ingeschakeld voor het distributiepunt, zoals PXE, multicast, inhoud validatie en de distributiestatus voor het distributiepunt. U kunt tevens gedetailleerde statusinformatie voor het distributiepunt weergeven.  

> [!WARNING]  
>  Configuratiestatus van distributiepunt is relatief naar de laatste 24 uur. Als het distributiepunt een fout en dit wordt hersteld heeft, wordt de foutstatus mogelijk weergegeven tot 24 uur nadat het distributiepunt wordt hersteld.  

Gebruik de volgende procedure om de configuratiestatus van een distributiepuntengroep weer te geven.  

### <a name="to-monitor-distribution-point-configuration-status"></a>Bewaken van de configuratiestatus van distributiepunten  

1.  Klik in de Configuration Manager-console op **bewaking**.  

2.  In de **bewaking** werkruimte Vouw **distributiestatus**, en klik vervolgens op **configuratiestatus van distributiepunt**. De distributiepunten worden weergegeven.  

3.  Selecteer het distributiepunt waarvoor u wilt dat statusgegevens distributiepunt.  

4.  Klik op het tabblad **Details** in het resultatenvenster. De statusinformatie voor het distributiepunt wordt weergegeven.  

## <a name="client-data-sources-dashboard"></a>Client gegevensbronnen dashboard
Vanaf versie 1610, kunt u de **Clientgegevensbronnen** dashboard voor meer informatie over het gebruik van [Peer-Cache](/sccm/core/plan-design/hierarchy/client-peer-cache) in uw omgeving. Het dashboard wordt gestart om gegevens weer te geven nadat clients downloaden inhoud en het rapport informatie teruggestuurd naar de site. Dit kan tot 24 uur duren.

> [!TIP]  
> **Client-Peer-Cache** en de **Clientgegevensbronnen** dashboard zijn functies van evaluatieversies geïntroduceerd in versie 1610. U moet de Client-Peer-Cache inschakelen voordat het dashboard van gegevensbronnen van de Client weergegeven in de console wordt. Zie voor het inschakelen van Client-Peer-Cache [functies van evaluatieversies van updates gebruiken](/sccm/core/servers/manage/install-in-console-updates#bkmk_prerelease). Het kan tot 24 uur nadat u het inschakelen en starten om gegevens weer te geven duren.

Ga in de console naar **bewaking** > **distributiestatus** > **Clientgegevensbronnen**. Hier kunt u een bepaalde periode moeten worden toegepast op het dashboard. Klik in de weergave kunt u de grensgroep of het pakket waarvoor u wilt weergeven. Wanneer u informatie bekijkt, kunt u de muisaanwijzer over het oppervlak voor meer informatie over de verschillende inhoud of het beleid bronnen.

Deze gegevens omvatten het volgende:  
- **Client inhoudsbronnen**: Geeft de bron van waaruit clients inhoud heeft.
- **Distributiepunten**: Geeft het aantal distributiepunten die deel van de geselecteerde Grensgroep uitmaken.
- **Clients die een distributiepunt gebruikt**: Het aantal clients die zich in de geselecteerde Grensgroep, dit wordt weergegeven hoeveel gebruikt een distributiepunt inhoud op te halen.
- **Peer-Cache-bronnen**: Dit betekent hoeveel bronnen voor peer-cache downloadgeschiedenis hebben gerapporteerd voor de geselecteerde Grensgroep.
- **Clients die u een peer gebruikt**: Het aantal clients die zich in de geselecteerde Grensgroep, dit wordt weergegeven hoeveel gebruikt een peer-cachebron inhoud op te halen.



U kunt ook een nieuw rapport **Clientgegevensbronnen - samenvatting**om een samenvatting van de clientgegevensbronnen van elke grensgroep weer te geven.
