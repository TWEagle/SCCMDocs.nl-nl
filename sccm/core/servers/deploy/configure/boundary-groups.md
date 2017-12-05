---
title: "Grensgroepen definiëren"
titleSuffix: Configuration Manager
description: Grensgroepen die een koppeling van clients naar sitesystemen in System Center Configuration Manager te begrijpen.
ms.custom: na
ms.date: 7/31/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: configmgr-other
ms.tgt_pltfrm: na
ms.topic: get-started-article
ms.assetid: 5db2926f-f03e-49c7-b44b-e89b1a5a6779
caps.latest.revision: "10"
author: mestew
ms.author: mstewart
manager: angrobe
ms.openlocfilehash: cccb59cfa4466234ef55a43b81333567f007b98e
ms.sourcegitcommit: daa080cf220835f157a23e8c8e2bd2781b869bb7
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/04/2017
---
# <a name="configure-boundary-groups-for-system-center-configuration-manager"></a>Grensgroepen configureren voor System Center Configuration Manager


*Van toepassing op: System Center Configuration Manager (huidige vertakking)*

U kunt grensgroepen in System Center Configuration Manager logisch groep gerelateerde netwerklocaties ([grenzen](/sccm/core/servers/deploy/configure/boundaries)) om het gemakkelijker om uw infrastructuur te beheren. Grenzen moeten worden toegewezen aan grensgroepen voordat u de grensgroep kunt gebruiken.

Configuration Manager maakt een standaard sitegrensgroep standaard op elke site.

> [!IMPORTANT]  
>  **De informatie in deze sectie van de groepen grens en de onderliggende secties geldt voor 1610 of hoger.** Deze inhoud is bijgewerkt om een specifiek zijn voor de ontwerpwijzigingen die is geïntroduceerd voor grensgroepen met deze versie van de update.
>
> **Als u eerdere versies 1610**, Zie [grensgroepen voor System Center Configuration Manager versie 1511, 1602 en 1606](/sccm/core/servers/deploy/configure/boundary-groups-for-1511-1602-and-1606) voor meer informatie over het gebruik en grensgroepen configureren met deze productversies.

Voor het configureren van grensgroepen, koppelt u grenzen (netwerklocaties) en sitesysteemrollen, zoals distributiepunten aan de grensgroep. Dit helpt het koppelen van clients met sitesysteemservers, zoals distributiepunten die zich bevinden in de buurt van de clients op het netwerk.

Als u dezelfde grens aan meerdere grensgroepen toewijzen, en dezelfde site systeemservers, zoals distributiepunten, toewijzen aan meerdere grensgroepen verhoogt u de beschikbaarheid van systemen voor een breder publiek netwerklocaties.

Clients gebruiken een grensgroep voor:  

-   Automatische sitetoewijzing  
-   Vinden van een sitesysteemserver die een service biedt, waaronder:
    - Distributiepunten voor de locatie van inhoud
    -   Software-updatepunten (begin met versie 1702)
    - Statusmigratiepunten
    - Voorkeursbeheerpunten (als u voorkeursbeheerpunten gebruikt, moet u deze optie voor de hiërarchie en niet vanuit inschakelen configuratie van de grensgroep. Zie [gebruik van voorkeursbeheerpunten inschakelen](#to-enable-use-of-preferred-management-points) in dit onderwerp.)

##  <a name="boundary-groups-and-relationships"></a>Grensgroepen en relaties
Voor elke grensgroep in uw hiërarchie, kunt u het volgende toewijzen:

-  Een of meer grenzen. Wanneer een client zich op een netwerklocatie bevindt die is gedefinieerd als een grens die is toegewezen aan een specifieke grensgroep, die wordt aangeroepen de **huidige** grensgroep. Een client kan meer dan één grensgroep huidige hebben.
- Een of meer sitesysteemrollen.  Clients kunnen altijd gebruik van sitesysteemrollen die zijn gekoppeld aan hun huidige grensgroep. Afhankelijk van de aanvullende configuraties, is het mogelijk dat ze sitesysteemrollen in extra grensgroepen gebruiken.  

Voor elke grensgroep die u maakt, kunt u een eenzijdige koppeling naar een andere grensgroep configureren. De koppeling heet een **relatie**. De grensgroepen u een koppeling naar heten **neighbor** grensgroepen. Een grensgroep kan meerdere relaties, elk met een specifieke neighbor grensgroep hebben.

De configuratie van elke relatie bepaalt wanneer een client die niet kan vinden op dat een sitesysteemserver beschikbaar in de huidige grensgroep kunt beginnen met het zoeken van een neighbor grensgroep om te zoeken naar een beschikbare sitesysteem. Deze zoekopdracht van extra groepen heet **terugval**.

## <a name="fallback"></a>Terugval
Om problemen te voorkomen voor clients wanneer ze een beschikbare sitesysteem in hun huidige grensgroep kunnen vinden, kunt u de relatie tussen grensgroepen die terugval gedrag definieert definiëren. Terugval kunt een client de zoekactie aan extra grensgroepen vinden van een systeem beschikbare site uitbreiden.

Relaties zijn geconfigureerd op de eigenschappen van een grensgroep **relaties** tabblad. Wanneer u een relatie configureert, moet u een koppeling aan een grensgroep neighbor definiëren. Voor elk type sitesysteemrol die wordt ondersteund, kunt u onafhankelijke instellingen voor terugvallen neighbor van de grensgroep configureren. Als u bijvoorbeeld bij het configureren van een relatie met een specifieke grensgroep kunt u instellen voor distributiepunten om te worden uitgevoerd na 20 minuten in plaats van de standaardwaarde van 120 terugval. Zie [voorbeeld van het gebruik van grensgroepen](#example-of-using-boundary-groups) voor een uitgebreider voorbeeld.

Als een client niet een beschikbare sitesysteemrol niet vinden in de huidige grensgroep, gebruikt de client de terugval tijd in minuten na hoe lang deze beginnen kan met zoeken naar een beschikbare sitesysteem dat is gekoppeld aan de grensgroep neighbor bepalen.  

Wanneer een client een beschikbare sitesysteem niet vinden kan en begint met zoeken naar de locaties van neighbor grensgroepen, neemt de groep met beschikbare sitesystemen die kan worden gebruikt op een manier die is gedefinieerd door uw configuratie van grensgroepen en hun relaties.

- Een grensgroep kan meer dan één relatie hebben. U kunt meerdere relaties terugval voor elk type sitesysteem naar andere neighbors na verschillende perioden configureren.    
- Clients alleen terugval aan een grensgroep die een directe neighbor van hun huidige grensgroep.
- Wanneer een client lid is van meerdere grensgroepen, wordt de huidige grensgroep gedefinieerd als een samenvoeging van die grensgroepen van de client. Client kan vervolgens terugval naar neighbors van elk van de oorspronkelijke grensgroepen.

### <a name="the-default-site-boundary-group"></a>De standaardgroep voor de grens van site
Naast de grensgroepen die u maakt, heeft elke site een standaard sitegrensgroep die is gemaakt door Configuration Manager. Deze groep heet ***-Site-grens-standaardgroep&lt;sitecode >***. Bijvoorbeeld de naam van de groep voor site ABC zou worden *-Site-grens-standaardgroep&lt;ABC >.*

Voor elke grensgroep die u maakt, maakt Configuration Manager automatisch een impliciete koppelen aan elke grensgroep van standaard site in de hiërarchie.
-   De impliciete koppeling is een standaard terugvaloptie uit een huidige grensgroep toe aan de grensgroep voor sites standaard bevat een standaard terugval tijd van 120 minuten.
-   Clients die zich niet op een grens die zijn gekoppeld aan elke grensgroep in uw hiërarchie gebruiken de standaard sitegrensgroep van hun toegewezen site identificeren geldig sitesysteemrollen die kan worden gebruikt.

Terugvallen op de standaard sitegrensgroep beheren:
- U kunt gaat u naar de site standaard grensgroep eigenschappen en wijzig de waarden op de **standaardgedrag** tabblad. Wijzigingen die u hier van toepassing aanbrengt op *alle* geïmpliceerde koppelingen naar deze grensgroep. Deze instellingen kunnen worden overschreven wanneer u de expliciete koppeling aan deze grensgroep van standaard site uit een andere grensgroep configureren.
- U kunt gaat u naar de eigenschappen van een grensgroep die u hebt gemaakt en de waarden voor de expliciete koppeling naar een standaard sitegrensgroep wijzigen. Als u een nieuwe tijd in minuten voor terugval of blok terugval instelt, wordt die wijziging alleen de koppeling die u configureert. Configuraties van de expliciete koppeling overschrijven die op de **standaardgedrag** tabblad van een standaard sitegrensgroep.


## <a name="site-assignment"></a>Sitetoewijzing  
 U kunt iedere grensgroep configureren met een toegewezen site voor clients.  

-   Een nieuw geïnstalleerde client die automatische sitetoewijzing gebruikt, koppelt de toegewezen site van een grensgroep die de huidige netwerklocatie van de client bevat.  
-   Na toewijzing aan een site, wordt de sitetoewijzing van een client niet gewijzigd wanneer de netwerklocatie ervan wordt gewijzigd. Als de client naar een netwerklocatie die wordt vertegenwoordigd door een grens in een grensgroep met een andere sitetoewijzing roamt, wordt bijvoorbeeld de client toegewezen site blijven ongewijzigd.  
-   Wanneer door Active Directory-systeemdetectie een nieuwe bron wordt gedetecteerd, worden netwerkgegevens voor de gedetecteerde bron geëvalueerd op basis van de grenzen in grensgroepen. In dit proces wordt de nieuwe bron aan een toegewezen site gekoppeld voor de push-clientinstallatie.  
-   Wanneer een grens lid is van meerdere grensgroepen met verschillende toegewezen sites, selecteer clients willekeurig een van de sites.  
-   Wijzigingen in de toegewezen site van een grensgroep gelden alleen voor nieuwe toewijzingen aan de site. Clients die eerder zijn toegewezen aan een site, komen niet Herzie hun site-toewijzing op basis van wijzigingen in de configuratie van een grensgroep (of hun eigen netwerklocatie).  

Zie voor meer informatie over clientsitetoewijzing [automatische sitetoewijzing gebruiken voor Computers](../../../../core/clients/deploy/assign-clients-to-a-site.md#BKMK_AutomaticAssignment) in [clients toewijzen aan een site in System Center Configuration Manager](../../../../core/clients/deploy/assign-clients-to-a-site.md).  

## <a name="distribution-points"></a>Distributiepunten

Als een client de locatie van een distributiepunt wordt aangevraagd, verzendt Configuration Manager de client een lijst met de sitesystemen van het juiste type die zijn gekoppeld aan elke grensgroep die de huidige netwerklocatie van clients omvat:

-   **Tijdens softwaredistributie**, vragen clients een locatie voor de implementatie-inhoud is beschikbaar vanuit een distributiepunt of andere geldige inhoudsbron (zoals een client die is geconfigureerd voor Peer-Cache).

-   **Tijdens de implementatie van besturingssysteem**, vragen clients een locatie te verzenden of ontvangen van hun migratiestatusinformatie.  

Tijdens de implementatie van inhoud, als een client inhoud die niet beschikbaar is van een bron in de huidige grensgroep vraagt de client blijft om aan te vragen die inhoud probeert verschillende inhoudsbronnen in de huidige grensgroep totdat de terugval periode voor een grensgroep neighbor of de standaard sitegrensgroep is bereikt. Als de client de inhoud nog niet gevonden heeft, deze de zoekactie voor inhoudsbronnen om op te nemen van de grensgroepen neighbor vervolgens wordt uitgebreid.

Echter, als de inhoud wordt gedistribueerd op aanvraag en die niet beschikbaar is op een distributiepunt wanneer door een client wordt aangevraagd, het proces voor de inhoud overbrengen naar het distributiepunt begint en is het mogelijk dat de client die server vindt als inhoudsbron voordat voor het gebruik van een neighbor grensgroep.

## <a name="software-update-points"></a>Software-updatepunten
Vanaf versie 1702, clients gebruiken grensgroepen vinden van een nieuw software-updatepunt. U kunt afzonderlijke software-updatepunten toevoegen aan verschillende grensgroepen om te bepalen welke servers een client kunt vinden.

Als u een van een eerdere versie dan 1702 update, worden alle bestaande software-updatepunten toegevoegd aan de standaard sitegrensgroep op elke site. Dit houdt de werking van de vooraf update waar clients software-updatepunt van de groep met beschikbare software-updatepunten die u hebt geconfigureerd voor uw hiërarchie selecteren.  Dit gedrag behouden totdat u afzonderlijke software-updatepunten toevoegen aan andere grensgroepen voor selectie van gecontroleerde en terugval gedrag kiest.

Als u een nieuwe site installeert die versie 1702 wordt uitgevoerd of later, software-updatepunten niet worden toegevoegd aan de standaardgroep voor de site-grens. Software-updatepunten toewijzen aan een grensgroep, zodat clients kunnen vinden en ze gebruiken.

### <a name="fallback-for-software-update-points"></a>Opvang voor software-updatepunten
Opvang voor software-updatepunten is geconfigureerd zoals andere sitesysteemrollen, maar heeft het volgende voorbehoud:
- **Nieuwe clients gebruiken grensgroepen voor het selecteren van software-updatepunten.** Nadat u versie 1702 hebt geïnstalleerd, selecteer nieuwe clients die u installeert een software-updatepunt in die zijn verbonden met de grensgroepen die u hebt geconfigureerd. Dit vervangt de vorige gedrag waar clients selecteren een software-updatepunt willekeurig uit een lijst met toepassingen die delen van het forest van de client.

- **Laatst bekende goede software-updatepunt gebruiken totdat ze terugval vinden van een nieuwe blijven clients.** Clients die u hebt al een software-updatepunt blijven gebruiken die software-updatepunt tot deze server kan niet worden bereikt.  Dit omvat software-updatepunt dat niet is gekoppeld aan de huidige grensgroep van de client blijven gebruiken.

  Het verder gebruiken van een bestaande software-updatepunt zelfs wanneer de server zich niet in de huidige grensgroep van de client is opzettelijk. Dit is omdat een wijziging van de software-updatepunt tot een grote gebruik van netwerkbandbreedte leiden kan als de client worden gegevens gesynchroniseerd met het nieuwe software-updatepunt. De vertraging in de overgangsfase kunt u voorkomen dat het netwerk overbelast raakt als al uw clients naar een nieuw software overschakelen-op hetzelfde moment updatepunt.

- **Een client altijd probeert te bereiken van de laatste bekende juiste software-updatepunt gedurende 120 minuten voordat terugval wordt gestart.** Na 120 minuten als de client niet tot stand contactpersoon gebracht is, begint klikt u vervolgens deze terugval. Wanneer terugval wordt gestart, wordt er door de client een lijst van alle software-updatepunten ontvangt van de huidige grensgroep. Aanvullende software-updatepunten van neighbor grensgroepen en sitegrensgroep standaard zijn beschikbaar op basis van terugval configuraties.

### <a name="fallback-configurations-for-software-update-points"></a>Terugval configuraties voor software-updatepunten
#### <a name="beginning-with-version-1706"></a>Vanaf versie 1706   
U kunt configureren **terugval time-out (in minuten)** voor software-updatepunten als minder dan 120 minuten. De client moet echter nog steeds probeert te krijgen tot de oorspronkelijke software-updatepunt gedurende 120 minuten voordat deze wordt uitgebreid zoeken tot extra servers. Omdat grens groep terugval keer starten wanneer de client eerst mislukt om de oorspronkelijke server te bereiken, worden alle grensgroepen die zijn geconfigureerd voor minder dan 120 minuten zijn bedoeld om de client wanneer deze de zoekactie te bereiken van de oorspronkelijke server gedurende 120 minuten lukt wordt uitgebreid.

U kunt configureren **nooit terugval** op blok terugval voor een software-updatepunt aan een grensgroep neighbor.

Lukt het bereiken van de oorspronkelijke server voor twee uur gebruikt de client vervolgens een kortere cyclus een verbinding maken met een nieuw software-updatepunt. Hiermee kan de client snel zoeken door een groeiende lijst met mogelijke software-updatepunten.

 -  **Voorbeeld van terugval:**  
    Huidige grensgroep van een client is een opvang voor software-updatepunten die is geconfigureerd als *10* minuten voor grensgroep *A*, en *130* minuten voor grensgroep *B*. Wanneer de client niet kan bereiken van de laatste bekende juiste software-updatepunt:
    -   De client probeert te bereiken alleen de oorspronkelijke server voor de volgende 120 minuten.  Na 10 minuten de software-updatepunten uit grensgroep A zijn toegevoegd aan de groep met beschikbare servers. Echter, probeert de client kan geen verbinding maken met deze of een andere server als de eerste periode 120 minuten opnieuw verbinding maken met de oorspronkelijke server is verstreken.
    -   Nadat u hebt geprobeerd om te zoeken die oorspronkelijke software-updatepunt gedurende 120 minuten, uitbreiden de client vervolgens de zoekactie. Op dat moment worden servers in de huidige grensgroep van de client en de grensgroepen van een neighbor die geconfigureerd voor 120 minuten of minder zijn, toegevoegd aan de beschikbare groep met software-updatepunten. Dit omvat de servers in een grens groep A die eerder zijn toegevoegd aan de groep met beschikbare servers.
    -       Na 10 minuten (130 minuten totale tijd nadat de client eerst kan bereiken van de laatste bekende juiste software-updatepunt), breidt de client de zoekopdracht om op te nemen van software-updatepunten uit grensgroep B.  

#### <a name="prior-to-version-1706"></a>Voorafgaand aan versie 1706
Voorafgaand aan versie 1706 ondersteunen terugval configuraties voor software-updatepunten geen een configureerbare tijd in minuten. In plaats daarvan is terugval gedrag beperkt tot:

  - **Terugval tijden (in minuten):**  Deze optie is niet beschikbaar voor software-updatepunten en kan niet worden geconfigureerd. Deze waarde is ingesteld op 120 minuten.
  -     **Nooit terugval:** Wanneer u deze configuratie gebruikt, kunt u opvang voor software-updatepunt aan een grensgroep neighbor blokkeren.

Als een client die een software-updatepunt is al verbinding is mislukt, kan de client vervolgens terugvallen op een andere vinden. Wanneer u terugval, ontvangt de client een lijst met alle software-updatepunten uit de huidige grensgroep. Als dit een beschikbare server vinden voor 120 minuten mislukt, wordt de grensgroepen neighbor en de standaard sitegrensgroep vervolgens terugval. Terugvallen op beide grensgroepen gebeurt op hetzelfde moment omdat de software-updatepunten terugval tijd neighbor groepen is ingesteld op 120 minuten en kan niet worden gewijzigd. 120 minuten is ook de standaardperiode gebruikt voor terugval aan de standaardgroep voor de site-grens. Wanneer een client schakelt terug naar zowel een neighbor en standaard sitegrensgroep de client probeert contact opnemen met software-updatepunten uit de grensgroep neighbor voordat u een van de standaardgroep voor de site-grens te gebruiken.

### <a name="manually-switch-to-a-new-software-update-point"></a>Handmatig overschakelen naar een nieuw software-updatepunt
Naast het terugval gebruikt, kunt u *Clientmelding* om af te dwingen handmatig een apparaat overschakelen naar een nieuw software-updatepunt.

Wanneer u naar een nieuwe server overschakelt, met de apparaten terugval zoeken naar die nieuwe server. Daarom Controleer uw configuratie van grensgroepen en zorg ervoor dat uw software-updatepunten in de juiste grensgroepen voordat u deze wijziging.

Zie voor meer informatie [clients handmatig overschakelen naar een nieuwe software-updatepunt](/sccm/sum/plan-design/plan-for-software-updates#manually-switch-clients-to-a-new-software-update-point).


## <a name="preferred-management-points"></a>Voorkeursbeheerpunten

 Met voorkeursbeheerpunten kunnen clients een beheerpunt identificeren dat is gekoppeld aan de huidige netwerklocatie (grens).  

-   Probeert een client via een voorkeursbeheerpunt van de toegewezen site voordat u een beheerpunt vanuit zijn toegewezen site die niet is geconfigureerd als voorkeursbeheerpunt.  
-   Om deze optie gebruikt, moet u voor de hiërarchie inschakelen en configureer vervolgens grensgroepen op afzonderlijke primaire sites zodat de beheerpunten die gekoppeld aan deze grensgroep gekoppelde grenzen worden moeten.  
-   Wanneer voorkeursbeheerpunten zijn geconfigureerd en een client de lijst van beheerpunten ordent, plaatst de client de voorkeursbeheerpunten boven aan de lijst met toegewezen beheerpunten (waaronder alle beheerpunten van de client toegewezen site).  

> [!NOTE]  
>  Wanneer een client roamt (dat wil zeggen dat de client van netwerklocatie verandert, bijvoorbeeld wanneer een laptop op een externe locatie wordt gebruikt) maakt deze mogelijk gebruik van een beheerpunt (of proxybeheerpunt) van de lokale site op de nieuwe locatie voordat de client probeert een beheerpunt te gebruiken vanuit de toegewezen site (inclusief de voorkeursbeheerpunten).  Zie [begrijpen hoe clients siteresources en -services voor System Center Configuration Manager vinden](../../../../core/plan-design/hierarchy/understand-how-clients-find-site-resources-and-services.md) voor meer informatie.  

### <a name="overlapping-boundaries"></a>Overlappende grenzen  
 Configuration Manager ondersteunt configuraties met overlappende grenzen voor Inhoudslocatie:  

-   **Wanneer een client inhoud aanvraagt**, en de clientnetwerklocatie tot meerdere grensgroepen behoort, Configuration Manager stuurt de client een lijst van alle distributiepunten die de inhoud bevatten.  
-   **Wanneer een client een server te verzenden of ontvangen van statusmigratie-informatie opvraagt**, en de clientnetwerklocatie tot meerdere grensgroepen behoort, Configuration Manager stuurt de client een lijst met alle statusmigratiepunten die zijn gekoppeld aan een grensgroep die de huidige netwerklocatie van de client bevat.  

De client kan door dit gedrag de dichtstbijzijnde server selecteren vanwaar inhoud of statusmigratie-informatie wordt overgedragen.  



## <a name="example-of-using-boundary-groups"></a>Voorbeeld van het gebruik van grensgroepen
Het volgende voorbeeld wordt een client zoeken naar inhoud vanaf een distributiepunt. In dit voorbeeld kan worden toegepast op andere sitesysteemrollen die gebruikmaken van grensgroepen. Echter, zoals wordt toegepast op software-updatepunten, houd er rekening mee dat software-updatepunten geen ondersteuning voor configuratie van een tijd in minuten voor het terugvallen op een groep neighbor en gebruik altijd een periode van 120 minuten.

U maakt drie grensgroepen die geen grenzen of sitesysteemservers delen:
-   Groep BG_A met distributiepunten DP_A1 en DP_A2 die zijn gekoppeld aan de groep
-   Groep BG_B met distributiepunten DP_B1 en DP_B2 die zijn gekoppeld aan de groep
-   Groep BG_C met distributiepunten DP_C1 en DP_C2 die zijn gekoppeld aan de groep

U de netwerklocaties van uw clients toevoegen als grenzen alleen de grensgroep BG_A, en u vervolgens relaties uit die grensgroep aan de andere twee grensgroepen configureren:
-   Configureren van distributiepunten voor de eerste *neighbor* groep (BG_B) moet worden gebruikt na 10 minuten. Deze groep bevat distributiepunten DP_B1 en DP_B2. Beide zijn goed verbonden zijn met de eerste groepen grenslocaties.
-   Configureren van de tweede *neighbor* groep (BG_C) moet worden gebruikt na 20 minuten. Deze groep bevat distributiepunten DP_C1 en DP_C2. Beide zijn via een WAN van de andere twee grensgroepen.
-   U ook toevoegen een extra distributiepunt dat zich bevindt op de siteserver aan de grensgroep sites standaard site. Dit is de locatie van de minste voorkeur inhoudsbron, maar bevindt centraal aan uw grensgroepen.

    Voorbeeld van grensgroepen en terugval tijden:

     ![BG_Fallack](media/BG_Fallback.png)


Met deze configuratie:
-   De client begint met zoeken naar inhoud vanaf distributiepunten in de *huidige* grensgroep (BG_A), zoeken naar elk distributiepunt wijst twee minuten voordat u overschakelt naar het volgende distributiepunt in de grensgroep. De groep clients met geldige inhoudsbron locaties bevat DP_A1 en DP_A2.
-   Als de client niet kan vinden van inhoud van de *huidige* grensgroep na 10 minuten zoekt, toegevoegd de distributiepunten van de grensgroep BG_B in de zoekopdracht. Vervolgens gaat door om te zoeken naar inhoud vanaf een distributiepunt in de gecombineerde van toepassingen van distributiepunten nu met die van de BG_A en de BG_B grensgroepen. De client blijft contact opnemen met elk distributiepunt voor twee minuten voordat u overschakelt naar het volgende distributiepunt uit de groep. De groep clients met geldige inhoudsbron locaties bevat DP_A1, DP_A2 DP_B1 en DP_B2.
-   Na een extra 10 minuten (totaal 20 minuten) als de client nog steeds niet een distributiepunt met inhoud gevonden is, deze wordt uitgebreid de groep van de beschikbare distributiepunten om op te nemen die uit de tweede *neighbor* groeperen, grensgroep BG_C. 6 distributiepunten om te zoeken (DP_A1, DP_A2 DP_B2, DP_B2, DP_C1 en DP_C2) heeft nu de client en deze blijft wijzigen in een nieuw distributiepunt elke twee minuten tot inhoud is gevonden.
-   Als de client niet voor inhoud na een totaal van 120 minuten gevonden is, vallen terug om op te nemen de *sitegrensgroep standaard* als onderdeel van de verder te zoeken. Distributiepunten in de groep bevat nu alle distributiepunten van de drie geconfigureerde grensgroepen en het laatste distributiepunt dat zich op de siteservercomputer.  De client blijft vervolgens de zoekactie voor inhoud, distributiepunten voor het wijzigen van elke twee minuten tot inhoud is gevonden.

U beheren wanneer specifieke distributiepunten worden toegevoegd als een inhoudsbronlocatie en wanneer, of als de client terugvallen op de standaard sitegrensgroep als veiligheidsnet voor inhoud die niet beschikbaar is van een andere locatie worden gebruikt door de verschillende neighbor-groepen zijn beschikbaar op verschillende tijdstippen configureren.






### <a name="update-existing-boundary-groups-to-the-new-model"></a>Bijwerken van bestaande grensgroepen naar het nieuwe model
Wanneer u naar een eerdere versie dan 1610 bijwerkt, worden de volgende configuraties automatisch gemaakt. Deze zijn bedoeld om te controleren of dat uw huidige terugval gedrag beschikbaar blijft totdat u een nieuwe grensgroepen en relaties configureert.

-   Een standaard sitegrensgroep is gemaakt voor elke primaire site, de naam is ***-Site-grens-standaardgroep&lt;sitecode >.***
  - Distributiepunten met *terugvalbronlocatie voor inhoud toestaan* gecontroleerd en statusmigratiepunten op primaire sites worden toegevoegd aan de *-Site-grens-standaardgroep&lt;sitecode >* grensgroep van die site.
  - Vanaf versie 1702, software-updatepunten zijn toegevoegd aan elke sites *-Site-grens-standaardgroep&lt;sitecode >*.
-   Er wordt een kopie gemaakt van elke bestaande grensgroep die een siteserver die is geconfigureerd met een trage verbinding. De naam van de nieuwe groep is  ***&lt;oorspronkelijke grens groepsnaam >-&lt;oorspronkelijke grens groeps-ID >***:  
    -   Sitesystemen waarop een snelle verbinding blijven de oorspronkelijke grensgroep.
    -   Een kopie van de site-systemen (distributiepunten, beheerpunten) die een trage verbinding hebt worden toegevoegd aan de kopie van de grensgroep. De oorspronkelijke sitesystemen die zijn geconfigureerd als langzaam blijven in hun oorspronkelijke grensgroepen voor compatibiliteit met eerdere versies, maar worden niet gebruikt van die grensgroepen.
    - Dit exemplaar van de groep grens heeft geen grenzen die zijn gekoppeld. Echter, een fallback koppeling wordt gemaakt tussen de oorspronkelijke groep en de nieuwe grens groep kopie bevat de terugval tijd is ingesteld op nul.  


- **Specifiek voor secundaire sites:**
  - Een grensgroep wordt gemaakt als een secundaire site ten minste één distributiepunt is met *terugvalbronlocatie voor inhoud toestaan* migratiepunt van ingeschakelde of status. De naam van de grensgroep is ***secundaire-Site-Neighbor--Tmp&lt;Sitecode >.***
  - Alle distributiepunten met *terugvalbronlocatie voor inhoud toestaan* gecontroleerd en statusmigratiepunten worden toegevoegd aan deze grensgroep nieuwe secundaire site.
  - Een fallback koppeling wordt gemaakt tussen de oorspronkelijke grensgroep en de zojuist gemaakte neighbor grensgroep en de alternatieve tijd is ingesteld op nul.


 De volgende tabel bevat de nieuwe terugval gedrag u kunt verwachten van de combinatie van de oorspronkelijke implementatie-instellingen en distributie wijst configuraties:

De configuratie van het oorspronkelijke implementatie voor 'Programma niet uitvoeren' in een langzaam netwerk  |Oorspronkelijke distributiepunt in de configuratie voor 'Client toestaan een terugvalbronlocatie voor inhoud te gebruiken'  |Nieuwe terugval gedrag  
---------|---------|---------
Geselecteerd     |  Geselecteerd    |  **Er geen terugval** -gebruik alleen de distributiepunten in de huidige grensgroep.       
Geselecteerd     |  Geen geselecteerd|  **Er geen terugval** -gebruik alleen de distributiepunten in de huidige grensgroep.       
Geen geselecteerd |  Geen geselecteerd|  **Terugval naar aan neighbor** - gebruik van de distributiepunten in de huidige grensgroep en voeg vervolgens de distributiepunten van de grensgroep neighbor. Tenzij een expliciete koppeling aan de standaardgroep voor de grens van site is geconfigureerd, clients niet wordt terugval naar aan die groep.    
Geen geselecteerd | Geselecteerd     |   **Fallback normale** -distributiepunten gebruiken in de huidige grensgroep, en vervolgens die van de site en neighbor standaard grensgroepen

 Alle andere implementatieconfiguraties leiden tot **fallback normale**.  




## <a name="changes-from-prior-versions-for-ui-and-behavior-for-content-locations"></a>Wijzigingen van eerdere versies voor de gebruikersinterface en het gedrag voor inhoudslocaties
Hier volgen de belangrijkste wijzigingen in grensgroepen en hoe clients inhoud vinden. Deze wijzigingen zijn aangebracht met versie 1610. Veel van deze wijzigingen en concepten werken samen.


-   **Configuraties voor het snel of traag worden verwijderd:** U configureert niet langer afzonderlijke distributiepunten worden snel of traag.  In plaats daarvan elk sitesysteem die zijn gekoppeld aan een grensgroep wordt behandeld hetzelfde. Vanwege deze wijziging de **verwijzingen** tabblad van de eigenschappen van de grensgroep biedt geen ondersteuning voor de configuratie van snel of traag.
-   **Nieuwe standaard grensgroep op elke site:**  Elke primaire site heeft een nieuwe grensgroep standaard is met de naam ***-Site-grens-standaardgroep&lt;sitecode >***.  Wanneer een client zich niet op een netwerklocatie bevindt die is toegewezen aan een grensgroep, wordt die client de sitesystemen die zijn gekoppeld aan de standaardgroep van de toegewezen site gebruiken. Wilt u deze grensgroep gebruiken als ter vervanging van het concept van locatie terugvalinhoudlocatie.      
 -  **'Alternatieve bronlocaties voor inhoud toestaan'** wordt verwijderd: U configureert niet langer expliciet een distributiepunt moet worden gebruikt voor terugval en de opties in te stellen dat deze worden verwijderd uit de gebruikersinterface.

    Daarnaast het resultaat van de instelling **clients met een terugvalbronlocatie voor inhoud toestaan** op een implementatie van het type voor toepassingen is gewijzigd. Deze instelling op een implementatietype kan een client de standaard sitegrensgroep gebruiken als bronlocatie voor inhoud.

 -  **Grens groepen relaties:** Elke grensgroep kan worden gekoppeld aan een of meer extra grensgroepen. Deze koppelingen vormen relaties die zijn geconfigureerd op het nieuwe grens groep tabblad Eigenschappen met de naam **relaties**:
    -   Elke grensgroep die een client rechtstreeks is gekoppeld, heet een **huidige** grensgroep.  
    -   Elke grensgroep een client kan gebruiken als gevolg van een koppeling tussen die client *huidige* grensgroep en een andere groep, heet een **neighbor** grensgroep.
    -  Deze zich op de **relaties** tabblad die u grensgroepen die kunnen worden gebruikt toevoegt als een *neighbor* grensgroep. U kunt ook een tijd in minuten die bepaalt wanneer een client die niet kunnen vinden van inhoud vanaf een distributiepunt in de *huidige* begint om te zoeken naar inhoud locaties van die groep *neighbor* grensgroepen.

        Wanneer u toevoegen of wijzigen van de configuratie van een grensgroep, hebt u de mogelijkheid om te blokkeren fallback naar specifieke grensgroep uit de huidige groep die u configureert.

    Expliciete koppelingen (koppelingen) uit een grensgroep naar een andere definiëren voor het gebruik van de nieuwe configuratie, en alle distributiepunten configureren in de bijbehorende groep met de dezelfde periode in minuten. De tijd die u configureert, bepaalt wanneer een client die niet kunnen vinden van een bron van de inhoud van de *huidige* grensgroep kunt beginnen met zoeken naar inhoudsbronnen van neighbor van de grensgroep.

    Naast de grensgroepen die expliciet configureren, heeft elke grensgroep een impliciete koppeling aan de standaardgroep voor de site-grens. Deze koppeling wordt na 120 minuten op dat moment wordt de standaardgroep voor de site-grens van een neighbor grensgroep waarmee de clients gebruiken de distributiepunten die zijn gekoppeld aan de grensgroep als inhoudsbron locaties actief.

    Dit gedrag vervangt wat eerder werd aangeduid als terugval voor inhoud.  U kunt dit standaardgedrag van 120 minuten overschrijven expliciet koppelen van de grensgroep voor standaard site naar een *huidige* groep, en het instellen van een bepaalde tijd in minuten of terugval blokkeren volledig om te voorkomen dat het gebruik ervan.


-   **Clients proberen inhoud op te halen van elk distributiepunt maximaal 2 minuten:** Wanneer een client zoekt naar een inhoudsbronlocatie, probeert het toegang krijgen tot elk distributiepunt voor 2 minuten voordat u vervolgens probeert een ander distributiepunt. Dit is een wijziging ten opzichte van vorige versies waar clients heeft geprobeerd verbinding maken met een distributiepunt voor maximaal twee uur.

    - Het eerste distributiepunt dat een client probeert te gebruiken is willekeurig geselecteerd uit de groep met beschikbare distributiepunten in de client *huidige* grensgroep (of groepen).

    - Na twee minuten als de client niet voor de inhoud gevonden is het verandert in een nieuw distributiepunt en probeert inhoud op te halen van die server. Dit proces wordt herhaald voor elke twee minuten totdat de client de inhoud wordt gevonden of de laatste server in de groep van toepassingen is bereikt.

    - Als een client kan geen geldige inhoudsbronlocatie van vinden de *huidige* van toepassingen voordat u de periode voor terugvallen op een *neighbor* grensgroep is bereikt, de client worden de distributiepunten uit de die *neighbor* groeperen met het einde van de huidige lijst en zoek vervolgens de uitgevouwen groep bronlocaties die de distributiepunten van beide grensgroepen bevat.

        > [!TIP]  
        > Wanneer u een expliciete koppeling te van de huidige grensgroep aan de standaardgroep voor de grens van site maken en een fallback-tijd die kleiner is dan de terugval tijd voor een koppeling naar een grensgroep neighbor definiëren, beginnen clients bronlocaties uit de grensgroep standaard site voordat de groep neighbor zoeken.

    - Wanneer de client niet kan inhoud op te halen van de laatste server in de groep, begint het proces opnieuw.


## <a name="procedures-for-boundary-groups"></a>Procedures voor grensgroepen
De volgende procedures gelden voor 1610 of hoger. Als u een eerdere versie dan 1610 gebruikt, raadpleegt u de procedures in [grensgroepen voor System Center Configuration Manager versie 1511, 1602 en 1606](/sccm/core/servers/deploy/configure/boundary-groups-for-1511-1602-and-1606).


### <a name="to-create-a-boundary-group"></a>Een grensgroep maken  
1.  Klik in de Configuration Manager-console op **beheer** > **Hiërarchieconfiguratie** >  **Grensgroepen**.  

2.  Klik op het tabblad **Start** in de groep **Maken** op **Grensgroep maken**.  

3.  Selecteer in het dialoogvenster **Grensgroep maken** het tabblad **Algemeen** en geef een naam voor deze grensgroep op bij **Naam** .  

4.  Klik op **OK** om de nieuwe grensgroep op te slaan.  


### <a name="to-configure-a-boundary-group"></a>Een grensgroep configureren  
 1.  Klik in de Configuration Manager-console op **beheer** > **Hiërarchieconfiguratie** >  **Grensgroepen**.  

 2.  Selecteer de grensgroep die u wilt wijzigen.  

 3.  Klik op **Eigenschappen** in het tabblad **Start** , in de groep **Eigenschappen**.  

 4.  Selecteer in het dialoogvenster **Eigenschappen** voor de grensgroep het tabblad **Algemeen** om de grenzen te wijzigen die lid zijn van deze grensgroep:  

     -   Als u grenzen wilt toevoegen, klikt u op **Toevoegen**, schakelt u het selectievakje voor een of meer grenzen in en klikt u op **OK**.  

     -   Als u grenzen wilt verwijderen, selecteert u de grens en klikt u op **Verwijderen**.  

 5.  Selecteer het tabblad **Verwijzingen** om de configuratie van sitetoewijzingen en de bijbehorende sitesysteemserver te wijzigen:  

     -   Als u deze grensgroep wilt inschakelen voor gebruik door clients voor sitetoewijzing, schakelt u het selectievakje **Deze grensgroep gebruiken voor sitetoewijzing**in en selecteert u een site in de vervolgkeuzelijst **Toegewezen site** .  

     -   Configureren welke beschikbare sitesysteemservers worden gekoppeld aan deze grensgroep:  

     1.  Klik op **Toevoegen**en schakel het selectievakje voor een of meer servers in. De servers worden als gekoppelde sitesysteemservers toegevoegd aan deze grensgroep. Alleen servers waarop ondersteunde sitesysteemrollen zijn geïnstalleerd, zijn beschikbaar.  

         > [!NOTE]  
         >  U kunt een combinatie van beschikbare sitesystemen van alle sites in de hiërarchie selecteren. Geselecteerde sitesystemen worden weergegeven op het tabblad **Sitesystemen** in de eigenschappen van elke grens die deel uitmaakt van deze grensgroep.  

     2.  Als u een server uit deze grensgroep wilt verwijderen, selecteert u de server en klikt u op **Verwijderen**.  

         > [!NOTE]  
         >  Als u deze grensgroep niet meer wilt gebruiken voor het koppelen van sitesystemen, moet u alle servers die worden vermeld als gekoppelde sitesysteemservers verwijderen.  

 6.  Selecteer de **relaties** tabblad om terugval gedrag te configureren:  

     - Klik op **toevoegen**, en selecteer vervolgens de grensgroep die u wilt configureren.

     - Een fallback tijd instellen voor distributiepunten. Na deze periode, in de grensgroep die u relaties configureert, kunnen clients worden om te beginnen met zoeken naar inhoud uit de distributiepunten van de grensgroep die u wilt toevoegen.

     - Om te voorkomen dat terugval naar een specifieke grensgroep, met inbegrip van de *standaard sitegrensgroep* die standaard is geconfigureerd, selecteert u de grensgroep en klikt u vervolgens het selectievakje in voor **nooit terugval**.   

 7.  Klik op **OK** om de eigenschappen van de grensgroep te sluiten en de configuratie op te slaan.  

#### <a name="to-associate-a-site-systme-server-with-a-boundary-group"></a>Een sitesysteemserver die als koppelen aan een grensgroep  
 1.  Klik in de Configuration Manager-console op **beheer** > **Hiërarchieconfiguratie** >  **Grensgroepen**.  

 2.  Selecteer de grensgroep die u wilt wijzigen.  

 3.  Klik op **Eigenschappen** in het tabblad **Start** , in de groep **Eigenschappen**.  

 4.  In het dialoogvenster **Eigenschappen** voor de grensgroep selecteert u het tabblad **Verwijzingen** .  

 5.  Klik onder **Sitesysteemservers selecteren**op **Toevoegen**, schakel de selectievakjes in voor de sitesysteemservers die u wilt koppelen aan deze grensgroep en klik vervolgens op **OK**.  

 6.  Klik op **OK** om het dialoogvenster te sluiten en de configuratie van de grensgroep op te slaan.  


#### <a name="to-configure-a-fallback-site-for-automatic-site-assignment"></a>Een terugvalsite voor automatische sitetoewijzing configureren  

  1.  Klik in de Configuration Manager-console op **beheer** > **siteconfiguratie** >  **Sites**.  

  2.  Klik op **Hiërarchie-instellingen** op het tabblad **Start** , in de groep **Sites**.  

  3.  Schakel op het tabblad **Algemeen** het selectievakje **Een terugvalsite gebruiken**in en selecteer een site in de vervolgkeuzelijst **Terugvalsite** .  

  4.  Klik op **OK** om de configuratie op te slaan.  

#### <a name="to-enable-use-of-preferred-management-points"></a>Gebruik van voorkeursbeheerpunten inschakelen  

 1.  Klik in de Configuration Manager-console op **beheer** > **siteconfiguratie** > **Sites**, en klik vervolgens op de **Start** tabblad Selecteer **hiërarchie-instellingen**.  

 2.  Selecteer op het tabblad **Algemeen** van de hiërarchie-instellingen de optie **Clients gebruiken liever beheerpunten die zijn opgegeven in grensgroepen**.  

 3.  Klik op **OK** om het dialoogvenster te sluiten en de configuratie op te slaan.  
