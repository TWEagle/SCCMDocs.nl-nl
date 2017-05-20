---
title: Peer-clientcache | System Center Configuration Manager
description: Gebruik Peercache voor inhoudsbron clientlocaties bij het implementeren van inhoud met System Center Configuration Manager.
ms.custom: na
ms.date: 4/4/2017
ms.reviewer: na
ms.suite: na
ms.prod: configuration-manager
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 86cd5382-8b41-45db-a4f0-16265ae22657
caps.latest.revision: 3
author: Brenduns
ms.author: brenduns
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 26feb0b166beb7e48cb800a5077d00dbc3eec51a
ms.openlocfilehash: dcd05d7d120f8997562da7d92b38c8b52a512357
ms.contentlocale: nl-nl
ms.lasthandoff: 05/17/2017

---

# <a name="peer-cache-for-configuration-manager-clients"></a>Peercache voor Configuration Manager-clients

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*

Beginnen met System Center Configuration Manager versie 1610, kunt u **Peercache** voor het beheer van de implementatie van inhoud op clients op externe locaties. Peercache is een ingebouwde Configuration Manager-oplossing waarmee clients inhoud te delen met andere clients rechtstreeks vanuit de lokale cache.   

> [!TIP]  
> Met versie 1610 geïntroduceerd, zijn Peer-Cache en het dashboard van gegevensbronnen van de Client pre-release functies. Als u wilt inschakelen, Zie [gebruikmaken van de functies van updates pre-release](/sccm/core/servers/manage/pre-release-features).

## <a name="overview"></a>Overzicht
 -     Clientinstellingen kunt u clients toestaat te gebruiken van Peer-Cache.
 -     Om inhoud te delen, Peer Cache-clients beide moeten lid zijn van de huidige grensgroep van de client waarmee wordt geprobeerd de inhoud. Peer-Cache-clients in neighbor grensgroepen zijn niet opgenomen in de groep met beschikbare inhoudsbron locaties wanneer een client terugval gebruikt te zoeken naar inhoud van een neighbor-grensgroep. Zie voor meer informatie over de huidige en neighbor grensgroepen [grensgroepen](/sccm/core/servers/deploy/configure/define-site-boundaries-and-boundary-groups##a-namebkmkboundarygroupsa-boundary-groups).
 - Clients die niet zijn ingeschakeld voor Peer-Cache, maar zijn in de huidige grensgroep Peercache clients is ingeschakeld, inhoud kan worden opgehaald van de client Peer Cache ingeschakeld.  
 - Elk type inhoud dat is ingesloten in het cachegeheugen van de Configuration Manager-client kan worden geleverd aan andere clients via Peer-Cache.
 -    Peercache is geen vervanging voor het gebruik van andere oplossingen zoals BranchCache, maar in plaats daarvan werkt side-by-side ermee beschikt u over meer opties voor het uitbreiden van traditionele inhoudsdistributie in oplossingen zoals distributiepunten. Dit is een aangepaste oplossing met hebt niet afhankelijk van BranchCache, dus als u niet inschakelen of Windows BranchCache gebruiken, het nog steeds werkt.

### <a name="operations"></a>Bewerkingen

Nadat u clientinstellingen die Peer-Cache op een verzameling inschakelen hebt geïmplementeerd, kunnen leden van deze verzameling fungeren als een peer-inhoudsbron voor andere clients in dezelfde grensgroep:
 -    Een client die als een peer-inhoudsbron fungeert verzendt een lijst met beschikbare in de cache-inhoud naar het beheerpunt.
 -    Wanneer de volgende client in die grensgroep die inhoud aanvraagt, wordt elke bron voor peer-cache met de inhoud vervolgens geretourneerd als een mogelijke inhoudsbron samen met de distributiepunten en andere locaties inhoudsbron in die grensgroep.
 -    Per het normale operationele proces selecteert de client waarmee wordt geprobeerd de inhoud een inhoudsbron uit de groep van bronnen die is opgegeven en vervolgens proberen toegang te krijgen van de inhoud wordt voortgezet.

> [!NOTE]
> Als alternatief voor optreedt een neighbor-grensgroep voor inhoud, de Peer-Cache inhoudsbron locaties van de grensgroep neighbor niet worden toegevoegd aan de groep van de client van mogelijke locaties van de inhoudsbron.  


Hoewel u alle clients als een peer-cache-bron, de bijbehorende aanbevolen kiezen alleen clients die zich het beste geschikt is voor peer-bronnen van de cache wordt deelnemen aan.  De geschiktheid van clients kan worden geëvalueerd op basis van een client chassistype, schijfruimte en verbinding met het netwerk. Zie voor meer informatie waarmee u selecteert het beste clients moet worden gebruikt voor Peer-Cache, [deze blog door een Microsoft-consultant](https://blogs.technet.microsoft.com/setprice/2016/06/29/pe-peer-cache-custom-reporting-examples/).

**Beperkte toegang tot de bron van een peer-cache**  
Vanaf versie 1702 weigeren peer cache broncomputer een aanvraag voor inhoud wanneer de broncomputer peer cache voldoet aan de volgende omstandigheden:  
  -  In de modus voor laag accuvermogen is.
  -  CPU-belasting groter is dan 80% op het moment dat de inhoud wordt aangevraagd.
  -  Schijf-i/o heeft een *AvgDiskQueueLength* die groter is dan 10.
  -  Er zijn niet meer beschikbaar zijn verbindingen met de computer.   

U kunt deze instellingen met behulp van de configuratieserver client WMI-klasse voor de functie peer source configureren (*SMS_WinPEPeerCacheConfig*) wanneer u de System Center Configuration Manager-SDK gebruiken.

Als de computer een verzoek om de inhoud afwijst, blijft de aanvragende computer te zoeken naar inhoud vanaf een alternatieve bronnen in de groep met beschikbare inhoudsbron locaties.   



### <a name="monitoring"></a>Controleren   
U kunt het dashboard van gegevensbronnen van de Client weergeven waarmee u informatie over het gebruik van Peer-Cache. Zie [Client gegevensbronnen dashboard](/sccm/core/servers/deploy/configure/monitor-content-you-have-distributed#client-data-sources-dashboard).

Vanaf versie 1702, kunt u drie rapporten weergeven peer cache gebruiken. In de console, gaat u naar **bewaking** > **rapportage** > **rapporten**. Alle rapporten zijn een type **Software distribueren inhoud**:
1.  **Peer-cache bron inhoud afwijzing**:  
Gebruik dit rapport om te begrijpen hoe vaak de peer cache bronnen in een grensgroep een inhoudsaanvraag geweigerd.
 - **Bekende problemen:** Wanneer u inzoomen op resultaten zoals *MaxCPULoad* of *MaxDiskIO*, verschijnt er een fout die wordt voorgesteld het rapport of gegevens kunnen niet worden gevonden. Om dit te voorkomen, gebruik de volgende twee lijsten waarop de resultaten direct weergeven.

2. **Peer-cache bron inhoud afwijzing door voorwaarde**:  
Gebruik dit rapport om te begrijpen afwijzing details voor een opgegeven groep of afwijzing grenstype. U kunt opgeven

  - **Bekende problemen:** U kunt geen selecteren uit de beschikbare parameters en in plaats daarvan moet ze handmatig invoeren. Voer de waarden voor *grens groepsnaam* en *afwijzing Type* zoals gezien in het eerste rapport. Bijvoorbeeld: voor *afwijzing Type* u kunt invoeren *MaxCPULoad* of *MaxDiskIO*.

3. **Details van cache gegevensbron inhoud afwijzing peer**:   
  Gebruik dit rapport om te begrijpen van de inhoud die is wordt gevraagd wanneer het is geweigerd.

 - **Bekende problemen:** U kunt geen selecteren uit de beschikbare parameters en in plaats daarvan moet ze handmatig invoeren. Voer de waarde voor *afwijzing Type* zoals weergegeven de eerste rapporteren (Peer cache bron inhoud afwijzing) en voer vervolgens de *Resource-ID* voor de inhoudsbron die u wilt meer informatie over.  De bron-ID van de inhoudsbron zoeken:  

    1. Zoek de naam van de computer die wordt weergegeven als de *Peer cachebron* in de resultaten van de 2e rapport (Peer cache bron inhoud afwijzing door voorwaarde).  
    2. Ga vervolgens naar **activa en naleving** > **apparaten** en zoek vervolgens naar deze naam computers. Gebruik de waarde van de Resource-ID-kolom.  


## <a name="requirements-and-considerations-for-peer-cache"></a>Vereisten en overwegingen voor Peer-Cache
-   Peercache wordt ondersteund op een Windows-besturingssysteem wordt ondersteund als Configuration Manager-client. Niet-Windows-besturingssystemen worden niet ondersteund voor Peer-Cache.

-   Clients kunnen alleen overbrengen van inhoud van Peer-Cache-clients die zich in hun huidige grensgroep.

-   Elke site die clients gebruiken voor Peer-Cache moet worden geconfigureerd met een [netwerktoegangsaccount](/sccm/core/plan-design/hierarchy/manage-accounts-to-access-content#a-namebkmknaaa-network-access-account). De account wordt gebruikt door de broncomputer-Peercache voor verificatie van aanvragen voor het downloaden van peers en enkel domein gebruikersmachtigingen vereist voor dit doel.

-     Omdat de huidige grens van een Peer-Cache inhoudsbron wordt bepaald door de laatste verzending van hardware-inventaris van de client, een client naar een netwerklocatie roamt die zich in een andere grensgroep mogelijk nog steeds worden beschouwd als een lid van de vorige grensgroep voor de doeleinden van Peer-Cache. Dit kan resulteren in een client een Peer-Cache inhoudsbron die zich niet in de onmiddellijke netwerklocatie wordt aangeboden. U wordt aangeraden met uitzondering van clients die gevoelig zijn voor deze configuratie deel te nemen als de bron van een Peer-Cache.

## <a name="to-configure-client-peer-cache-client-settings"></a>Peer-clientcache clientinstellingen configureren
1.    Ga in de Configuration Manager-console naar **beheer** > **clientinstellingen**, en open vervolgens het apparaat een clientinstellingenobject die u wilt gebruiken. U kunt ook de Standaardclientinstellingen object wijzigen.
2.    Kies in de lijst met beschikbare instellingen **clientcache-instellingen**.
3.    Stel **inschakelen Configuration Manager-client in een volledig besturingssysteem inhoud te delen** naar **Ja**.
4.    Configureer de volgende instellingen voor het definiëren van de poorten die u wilt gebruiken voor Peer-Cache:  
  -  **Poort voor oorspronkelijke netwerk-broadcast**
  -  **HTTPS inschakelen voor clientpeercommunicatie**
  -  **Poort voor downloaden van inhoud van peer (HTTP/HTTPS)**

Op elke computer die ingeschakeld voor Peer-Cache, als de Windows Firewall gebruikt, Configuration Manager geconfigureerd zodat het gebruik van de poorten die u configureert toestaan.

