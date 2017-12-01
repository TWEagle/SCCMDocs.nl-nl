---
title: Client-Peer-Cache
titleSuffix: Configuration Manager
description: Gebruik voor de inhoudsbron clientlocaties Peer-Cache bij het implementeren van inhoud met System Center Configuration Manager.
ms.custom: na
ms.date: 11/20/2017
ms.reviewer: na
ms.suite: na
ms.prod: configuration-manager
ms.technology: configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 86cd5382-8b41-45db-a4f0-16265ae22657
caps.latest.revision: "3"
author: aaroncz
ms.author: aaroncz
manager: angrobe
ms.openlocfilehash: 60f70d3e24f6290fb022b9bd8ca1512b0ed3d719
ms.sourcegitcommit: 7fe45ff75f05f7cc03ad021db8119791abe18049
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/01/2017
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
    -  Moet een lid van de huidige grensgroep van de client waarmee wordt geprobeerd de inhoud. Een client-Peer-Cache in een grensgroep neighbor is niet opgenomen in de groep met beschikbare inhoud bronlocaties wanneer een client terugval gebruikt te zoeken naar inhoud van een neighbor grensgroep. Zie voor meer informatie over de huidige en neighbor grensgroepen [grensgroepen](/sccm/core/servers/deploy/configure/define-site-boundaries-and-boundary-groups##a-namebkmkboundarygroupsa-boundary-groups).
 - Elk type inhoud dat wordt bewaard in de cache van een Configuration Manager-client kan worden geleverd met andere clients met behulp van Peer-Cache.
 -  Peer-Cache niet vervangen en het gebruik van andere oplossingen zoals BranchCache, maar in plaats daarvan werkt side-by-side ermee beschikt u over meer opties voor het uitbreiden van traditionele implementatieoplossingen voor inhoud zoals distributiepunten. Dit is een aangepaste oplossing met een niet afhankelijk van BranchCache, dus als u niet inschakelen of Windows BranchCache gebruiken, het nog steeds werkt.

### <a name="operations"></a>Bewerkingen

Nadat u de clientinstellingen die Peer-Cache voor een verzameling inschakelen hebt geïmplementeerd, kunnen leden van de verzameling fungeren als een peer-inhoudsbron voor andere clients in dezelfde grensgroep:
 -  Een client die wordt uitgevoerd als de bron van de inhoud van een peer verzendt een lijst met beschikbare in de cache inhoud naar het beheerpunt.
 -  Wanneer de volgende client in die grensgroep die inhoud aanvraagt, wordt elke peer-cachebron die de inhoud vervolgens geretourneerd als een mogelijke inhoudsbron samen met de distributiepunten en andere locaties inhoudsbron in de grensgroep.
 -  Per de normale operationele proces selecteert de client waarmee wordt geprobeerd de inhoud één inhoudsbron uit de groep van bronnen is opgegeven en vervolgens moet proberen de inhoud wordt voortgezet.

> [!NOTE]
> Als terugval naar aan optreedt een grensgroep neighbor voor inhoud, de inhoudsbron locaties van de grensgroep neighbor zijn niet toegevoegd aan de groep van mogelijke inhoudsbron locaties van de client-Peer-Cache.  


Hoewel kunt u alle clients als peer-cachebron, het beste kiezen alleen clients die het beste geschikt voor peer-cache-bronnen worden deelnemen aan.  De geschiktheid van clients kan worden geëvalueerd op basis van een client chassistype, schijfruimte en netwerkverbinding. Zie voor meer informatie kunt u selecteert de beste clients gebruiken voor Peer-Cache, [deze blog door een Microsoft-consultant](https://blogs.technet.microsoft.com/setprice/2016/06/29/pe-peer-cache-custom-reporting-examples/).

**Beperkte toegang tot de bron van een peer-cache**  
Vanaf versie 1702, weigert een peer-cache-broncomputer een aanvraag voor inhoud wanneer de peer-cache-bron-computer voldoet aan een van de volgende voorwaarden:  
  -  In de modus voor laag accuvermogen is.
  -  CPU-belasting groter is dan 80% op het moment dat de inhoud wordt aangevraagd.
  -  Schijf-i/o heeft een *AvgDiskQueueLength* die groter is dan 10.
  -  Er zijn niet meer beschikbaar zijn verbindingen met de computer.   

U kunt deze instellingen met behulp van de configuratieserver client WMI-klasse voor de functie voor peer-source configureren (*SMS_WinPEPeerCacheConfig*) wanneer u System Center Configuration Manager SDK gebruiken.

Als de computer een aanvraag voor de inhoud afwijst, blijft de aanvragende computer te zoeken naar inhoud vanaf een alternatieve bronnen in de groep met beschikbare inhoudsbron locaties.   



### <a name="monitoring"></a>Controleren   
U helpen bij het gebruik van Peer-Cache, kunt u het dashboard van gegevensbronnen van de Client weergeven. Zie [Clientgegevensbronnen dashboard](/sccm/core/servers/deploy/configure/monitor-content-you-have-distributed#client-data-sources-dashboard).

Vanaf versie 1702, kunt u drie rapporten gebruiken om weer te geven van peer-cache gebruiken. Ga in de console naar **bewaking** > **rapportage** > **rapporten**. Een type hebben als de alle rapporten **Software distributiepunt inhoud**:
1.  **Peer-cache-bron inhoud afwijzing**:  
Gebruik dit rapport om te begrijpen hoe vaak de peer-cache-bronnen in een grensgroep een inhoudsaanvraag geweigerd.
 - **Bekende problemen:** Wanneer u inzoomen op resultaten, zoals *MaxCPULoad* of *MaxDiskIO*, verschijnt er een fout die wordt voorgesteld het rapport of details kunnen niet worden gevonden. Gebruik de volgende twee rapporten waarin de resultaten rechtstreeks om dit probleem omzeilen.

2. **Peer-cache-bron inhoud afwijzing door voorwaarde**:  
Gebruik dit rapport om te begrijpen afwijzing details voor een opgegeven groep of afwijzing grenstype. U kunt opgeven

  - **Bekende problemen:** U kan niet kiezen uit de beschikbare parameters en in plaats daarvan moet ze handmatig invoeren. Voer de waarden voor *grens groepsnaam* en *afwijzing Type* zoals in het eerste rapport. Bijvoorbeeld: voor *afwijzing Type* mogelijk ingevoerd *MaxCPULoad* of *MaxDiskIO*.

3. **Peer-cache-bron inhoud afwijzing details**:   
  Gebruik dit rapport dat u begrijpt de inhoud die worden aangevraagd wanneer het is geweigerd.

 - **Bekende problemen:** U kan niet kiezen uit de beschikbare parameters en in plaats daarvan moet ze handmatig invoeren. Voer de waarde voor *afwijzing Type* zoals weergegeven de eerste rapporteren (Peer-cache-bron inhoud afwijzing) en voer vervolgens de *Resource-ID* voor de inhoudsbron waarover u meer informatie weergeven wilt.  De Resource-ID van de inhoudsbron zoeken:  

    1. Zoek de naam van de computer die wordt weergegeven als de *Peer-cachebron* in de resultaten van de 2e rapport (Peer-cache-bron inhoud afwijzing door voorwaarde).  
    2. Ga vervolgens naar **activa en naleving** > **apparaten** en zoek vervolgens naar die naam computers. Gebruik de waarde van de Resource-ID-kolom.  


## <a name="requirements-and-considerations-for-peer-cache"></a>Vereisten en overwegingen voor Peer-Cache
-   Peer-Cache wordt ondersteund op een Windows-besturingssysteem dat wordt ondersteund als Configuration Manager-client. Niet-Windows-besturingssystemen worden niet ondersteund voor Peer-Cache.

-   Clients kunnen alleen inhoud overdragen van Peer-Cache-clients die zich in hun huidige grensgroep bevinden.

-   Voorafgaand aan versie 1706, elke site waar clients gebruiken voor Peer-Cache moet worden geconfigureerd met een [netwerktoegangsaccount](/sccm/core/plan-design/hierarchy/manage-accounts-to-access-content#a-namebkmknaaa-network-access-account). Vanaf versie 1706, account is niet langer vereist met één uitzondering.  De uitzondering is wanneer een client-peer-cache wordt gebruikt om te halen en een takenreeks uitvoert vanuit het Software Center en de takenreeks, wordt de client opnieuw in WinPE opgestart.  In dit scenario wordt de client nog steeds vereist het netwerktoegangsaccount wanneer het zich in WinPE, zodat deze toegang heeft tot de peer-cachebron inhoud op te halen.

    Wanneer dit is verplicht, het netwerktoegangsaccount wordt gebruikt door de broncomputer Peer-Cache voor verificatie van aanvragen voor het downloaden van peers en alleen domeingebruikersmachtigingen nodig voor dit doel vereist.

-   Omdat de huidige grens van een Peer-Cache-inhoudsbron wordt bepaald door de verzending van die client laatste hardware-inventaris, een client die naar een netwerklocatie roamt en bevindt zich in een andere grensgroep mogelijk nog steeds worden beschouwd als een lid van de voormalige grensgroep voor de doeleinden van Peer-Cache. Dit kan resulteren in een client een Peer-Cache-inhoudsbron die zich niet in de onmiddellijke netwerklocatie wordt aangeboden. U wordt aangeraden met uitzondering van clients die gevoelig zijn voor deze configuratie deel te nemen als Peer-Cache-bron.

## <a name="to-configure-client-peer-cache-client-settings"></a>Client-Peer-Cache-clientinstellingen configureren
1.  Ga in de Configuration Manager-console naar **beheer** > **clientinstellingen**, en open vervolgens het apparaat een clientinstellingenobject die u wilt gebruiken. U kunt ook de Standaardclientinstellingen object wijzigen.
2.  Kies in de lijst met beschikbare instellingen **clientcache-instellingen**.
3.  Stel **inschakelen Configuration Manager-client in volledige OS in staat om inhoud te delen** naar **Ja**.
4.  Configureer de volgende instellingen voor het definiëren van de poorten die u wilt gebruiken voor Peer-Cache:  
  -  **Poort voor oorspronkelijke netwerk-broadcast**
  -  **HTTPS inschakelen voor clientpeercommunicatie**
  -  **Poort voor downloaden van inhoud van peer (HTTP/HTTPS)**

Op elke computer die ingeschakeld voor Peer-Cache, als Windows Firewall gebruikt wordt, Configuration Manager, configureert u het gebruik van de poorten die u configureert.
