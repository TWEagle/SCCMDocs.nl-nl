---
title: Client-Peer-Cache
titleSuffix: Configuration Manager
description: Gebruik voor de inhoudsbron clientlocaties Peer-Cache bij het implementeren van inhoud met System Center Configuration Manager.
ms.custom: na
ms.date: 12/07/2017
ms.reviewer: na
ms.suite: na
ms.prod: configuration-manager
ms.technology: configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 86cd5382-8b41-45db-a4f0-16265ae22657
caps.latest.revision: "3"
author: aczechowski
ms.author: aaroncz
manager: angrobe
ms.openlocfilehash: 424f4030f2dd2a337a29d48ca831fa3a791de610
ms.sourcegitcommit: e121d8d3dd82b9f2dde2cb5206cbee602ab8e107
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 01/17/2018
---
# <a name="peer-cache-for-configuration-manager-clients"></a>Peer-Cache voor Configuration Manager-clients

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*

U begint met System Center Configuration Manager versie 1610, kunt u **Peer-Cache** voor het beheer van de implementatie van inhoud voor clients op externe locaties. Peer-Cache is een ingebouwde Configuration Manager-oplossing waarmee clients inhoud te delen met andere clients rechtstreeks vanuit het lokale cachegeheugen.   

> [!TIP]  
> Deze functie is geïntroduceerd in versie 1610 als een [functie van de voorlopige versie](/sccm/core/servers/manage/pre-release-features). Vanaf versie 1710, deze functie is niet langer een voorlopige versie.

## <a name="overview"></a>Overzicht
Een client-Peer-Cache is een Configuration Manager-client die is ingeschakeld voor Peer-Cache gebruiken. Een client die deze inhoud met extra clients delen kunt Peer-Cache is een Peer-Cache-bron.
 -  U kunt clientinstellingen gebruiken zodat clients kunnen Peer-Cache gebruiken.
 -  Inhoud te delen als Peer-Cache-bron, een client-Peer-Cache:
    -  Worden moet lid van een domein. Echter, Peer-Cache-bron lid zijn van een client die niet is verbonden met het domein kan inhoud ophalen van een domein.
    -  Moet een lid van de huidige grensgroep van de client waarmee wordt geprobeerd de inhoud. Wanneer een client terugval gebruikt te zoeken naar inhoud uit een grensgroep neighbor, bevatten de lijst met inhoudsbron locaties een client-Peer-Cache niet in een grensgroep neighbor. Zie voor meer informatie over de huidige en neighbor grensgroepen [grensgroepen](/sccm/core/servers/deploy/configure/define-site-boundaries-and-boundary-groups##a-namebkmkboundarygroupsa-boundary-groups).
 - Configuration Manager-client dient elke type inhoud in de cache met andere clients met behulp van Peer-Cache. Deze inhoud bevat Office 365-bestanden en drukt bestanden voor installatie.<!--SMS.500850-->
 -  Het gebruik van andere oplossingen zoals BranchCache vervangen-peer-Cache niet. Peer-Cache werkt samen met andere oplossingen voor beschikt u over meer opties voor het uitbreiden van traditionele implementatieoplossingen voor inhoud zoals distributiepunten. Peer-Cache is een aangepaste oplossing met een niet afhankelijk van BranchCache.  Als u niet inschakelen of Windows BranchCache gebruiken, werkt nog altijd Peer-Cache.

### <a name="operations"></a>Bewerkingen

Om peer-cache, moet u de clientinstellingen implementeren naar een verzameling. Leden van de verzameling fungeert als een peer-inhoudsbron voor andere clients in dezelfde grensgroep.
 -  Een client die wordt uitgevoerd als de bron van de inhoud van een peer verzendt een lijst met beschikbare in de cache inhoud naar het beheerpunt.
 -  Wanneer de volgende client in die grensgroep die inhoud aanvraagt, wordt elke peer-cachebron, die de inhoud en online is, in de lijst met mogelijke inhoudsbronnen geretourneerd. Deze lijst bevat ook de distributiepunten en andere locaties inhoudsbron grensgroep.
 -  Per het normale proces selecteert de client waarmee wordt geprobeerd de inhoud één bron uit de opgegeven lijst. Vervolgens probeert de client de inhoud ophalen.

> [!NOTE]
> Als de client terug aan een grensgroep neighbor voor inhoud valt, komt deze niet de locaties van de inhoudsbron Peer-Cache van de grensgroep neighbor toevoegen aan de lijst met mogelijke locaties van de inhoudsbron.  


De aanbevolen procedure is alleen de clients die het meest geschikt als peer-cache-bron kiezen. Evalueer client geschiktheid op basis van kenmerken zoals chassistype, schijfruimte en netwerkverbinding. Zie voor meer informatie kunt u selecteert de beste clients gebruiken voor Peer-Cache, [deze blog door een Microsoft-consultant](https://blogs.technet.microsoft.com/setprice/2016/06/29/pe-peer-cache-custom-reporting-examples/).

**Beperkte toegang tot de bron van een peer-cache**  
Vanaf versie 1702, weigert een peer-cache-broncomputer aanvragen voor inhoud wanneer de peer-cache-bron-computer voldoet aan een van de volgende voorwaarden:  
  -  In de modus voor laag accuvermogen is.
  -  CPU-belasting groter is dan 80% op het moment dat de inhoud wordt aangevraagd.
  -  Schijf-i/o heeft een *AvgDiskQueueLength* die groter is dan 10.
  -  Er zijn niet meer beschikbaar zijn verbindingen met de computer.   

Deze instellingen configureren met de configuratieserver client WMI-klasse voor de functie voor peer-source (*SMS_WinPEPeerCacheConfig*) in de Configuration Manager-SDK.

Als de computer een aanvraag voor de inhoud afwijst, blijft de aanvragende computer te zoeken naar inhoud in de lijst met beschikbare inhoudsbron locaties.   



### <a name="monitoring"></a>Controleren   
U helpen bij het gebruik van Peer-Cache, kunt u het dashboard van gegevensbronnen van de Client weergeven. Zie [Clientgegevensbronnen dashboard](/sccm/core/servers/deploy/configure/monitor-content-you-have-distributed#client-data-sources-dashboard).

Vanaf versie 1702, kunt u drie rapporten gebruiken om weer te geven van peer-cache gebruiken. Ga in de console naar **bewaking** > **rapportage** > **rapporten**. Een type hebben als de alle rapporten **Software distributiepunt inhoud**:
1.  **Peer-cache-bron inhoud afwijzing**:  
Gebruik dit rapport om te begrijpen hoe vaak de peer-cache-bronnen in een grensgroep een inhoudsaanvraag afwijzen.
 - **Bekende problemen:** Wanneer u inzoomen op resultaten, zoals *MaxCPULoad* of *MaxDiskIO*, verschijnt er een fout die wordt voorgesteld het rapport of details kunnen niet worden gevonden. Gebruik de volgende twee rapporten die rechtstreeks de resultaten weer te geven om dit probleem omzeilen.

2. **Peer-cache-bron inhoud afwijzing door voorwaarde**:  
Gebruik dit rapport om te begrijpen afwijzing details voor een opgegeven groep of afwijzing grenstype. U kunt opgeven

  - **Bekende problemen:** U kan niet kiezen uit de beschikbare parameters en in plaats daarvan moet ze handmatig invoeren. Voer de waarden voor *grens groepsnaam* en *afwijzing Type* zoals in het eerste rapport. Bijvoorbeeld: voor *afwijzing Type* mogelijk ingevoerd *MaxCPULoad* of *MaxDiskIO*.

3. **Peer-cache-bron inhoud afwijzing details**:   
  Gebruik dit rapport dat u begrijpt de inhoud die de client is aangevraagd wanneer afgewezen.

 - **Bekende problemen:** U kan niet kiezen uit de beschikbare parameters en in plaats daarvan moet ze handmatig invoeren. Voer de waarde voor *afwijzing Type* zoals weergegeven de **Peer-cache-bron inhoud afwijzing** rapport. Voer vervolgens de *Resource-ID* voor de inhoudsbron waarover u meer informatie wilt.  De Resource-ID van de inhoudsbron zoeken:  

    1. Zoek de naam van de computer die wordt weergegeven als de *Peer-cachebron* in de resultaten van de **Peer-cache-bron inhoud afwijzing door voorwaarde** rapport.  
    2. Ga vervolgens naar **activa en naleving** > **apparaten** en zoek vervolgens naar die naam computers. Gebruik de waarde van de Resource-ID-kolom.  


## <a name="requirements-and-considerations-for-peer-cache"></a>Vereisten en overwegingen voor Peer-Cache
-   Peer-Cache wordt ondersteund op een Windows-besturingssysteem dat wordt ondersteund als Configuration Manager-client. Niet-Windows-besturingssystemen worden niet ondersteund voor Peer-Cache.

-   Clients kunnen alleen inhoud overdragen van Peer-Cache-clients die zich in hun huidige grensgroep bevinden.

-   Voorafgaand aan versie 1706, elke site waar clients gebruiken voor Peer-Cache moet worden geconfigureerd met een [netwerktoegangsaccount](/sccm/core/plan-design/hierarchy/manage-accounts-to-access-content#a-namebkmknaaa-network-access-account). Vanaf versie 1706, account is niet langer vereist met één uitzondering.  Het scenario uitzondering is wanneer een peer-cache-clients een takenreeks vanuit het Software Center uitvoert en dat de takenreeks opnieuw wordt opgestart in een opstartinstallatiekopie. In dit scenario wordt vereist de client nog steeds voor het netwerktoegangsaccount. Wanneer de client in Windows PE is, gebruikt het netwerktoegangsaccount inhoud op te halen uit de peer-cachebron.

    Indien vereist, wordt in de Peer-Cache-bron-computer het netwerktoegangsaccount voor aanvragen voor het downloaden van peers verificatie gebruikt. Deze account vereist alleen domeingebruikersmachtigingen nodig voor dit doel.

-   Laatste verzending van hardware-inventaris van de client bepaalt de huidige grens van een Peer-Cache-inhoudsbron. Een client naar een andere grensgroep roamt mogelijk nog steeds een lid van de voormalige grensgroep voor de doeleinden van Peer-Cache. Dit gedrag resulteert in een client een Peer-Cache-inhoudsbron die zich niet in de onmiddellijke netwerklocatie wordt aangeboden. U wordt aangeraden met uitzondering van clients die gevoelig zijn voor deze configuratie deel te nemen als Peer-Cache-bron.
-    Vanaf versie 1706, de peer-cacheclient eerst wordt gecontroleerd of de bron van een peer-cache online voordat u probeert om inhoud te downloaden. <!--sms.498675-->

## <a name="to-configure-client-peer-cache-client-settings"></a>Client-Peer-Cache-clientinstellingen configureren
Zie voor meer informatie over het configureren van instellingen voor de client [clientcache-instellingen](/sccm/core/clients/deploy/about-client-settings#client-cache-settings). Zie voor meer informatie [het configureren van clientinstellingen](/sccm/core/clients/deploy/configure-client-settings).

Op peer-cache ingeschakeld clients die Windows Firewall gebruikt, configureert Configuration Manager de firewall-poorten die u in de clientinstellingen opgeeft.
