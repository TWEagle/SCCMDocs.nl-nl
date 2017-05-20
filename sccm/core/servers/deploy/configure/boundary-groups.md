---
title: "Grensgroepen definiëren | Microsoft-documenten"
description: Begrijp grensgroepen die een koppeling van clients naar sitesystemen in System Center Configuration Manager.
ms.custom: na
ms.date: 05/02/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: get-started-article
ms.assetid: 5db2926f-f03e-49c7-b44b-e89b1a5a6779
caps.latest.revision: 10
author: Brenduns
ms.author: brenduns
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: d940fd1bbf96767d44f8c55315e814be55a83897
ms.openlocfilehash: 5684fd4fbfd0ffb8f3ffbcfa122eef3dafd77327
ms.contentlocale: nl-nl
ms.lasthandoff: 05/17/2017


---
# <a name="configure-boundary-groups-for-system-center-configuration-manager"></a>Grensgroepen voor System Center Configuration Manager configureren


*Van toepassing op: System Center Configuration Manager (huidige vertakking)*

U kunt grensgroepen in System Center Configuration Manager logisch groep gerelateerde netwerklocaties ([grenzen](/sccm/core/servers/deploy/configure/boundaries)) om eenvoudiger om uw infrastructuur te beheren. U moet grenzen eerst toewijzen aan grensgroepen voordat u de grensgroep kunt gebruiken.

Standaard wordt een standaard sitegrensgroep in Configuration Manager gemaakt op elke site.

> [!IMPORTANT]  
>  **De informatie in deze sectie grens groepen en de onderliggende secties is van toepassing op 1610 of hoger.** Deze inhoud is bijgewerkt om specifiek zijn voor de ontwerpwijzigingen geïntroduceerd voor grensgroepen met deze updateversie.
>
> **Als u versies vóór 1610**, Zie [grensgroepen voor System Center Configuration Manager-versies 1511 1602 en 1606](/sccm/core/servers/deploy/configure/boundary-groups-for-1511-1602-and-1606) voor informatie over het gebruik en grensgroepen configureren met de versies van het product.

Grensgroepen configureren, koppelt u grenzen (netwerklocaties) en sitesysteemrollen, zoals distributiepunten aan de grensgroep. Hiermee wordt het koppelen van clients voor sitesysteemservers zoals distributiepunten die zich bevinden in de buurt van de clients op het netwerk.

Als u de dezelfde grens aan meerdere grensgroepen toewijst en systeemservers, zoals de distributiepunten voor dezelfde site toewijzen aan meerdere grensgroepen verhoogt u de beschikbaarheid van de site-systemen voor een groot aantal netwerklocaties.

Clients gebruiken een grensgroep voor:  

-   Automatische sitetoewijzing  
-   Vinden van een sitesysteemserver waarmee een service, waaronder:
    - Distributiepunten voor de locatie van inhoud
    -    Software-updatepunten (begin met versie 1702)
    - Statusmigratiepunten
    - Beheerpunten bij voorkeur (als u voorkeursbeheerpunten gebruiken wilt, moet u deze optie voor de hiërarchie en niet vanuit inschakelen configuratie van de grensgroep. Zie [gebruik van voorkeursbeheerpunten inschakelen](#to-enable-use-of-preferred-management-points) in dit onderwerp.)

##  <a name="boundary-groups-and-relationships"></a>Grensgroepen en relaties
U kunt voor elke grensgroep in uw hiërarchie toewijzen:

-  Een of meer grenzen. Een client zich op een netwerklocatie bevindt die is gedefinieerd als een grens van een toegewezen aan een specifieke grensgroep, die wordt aangeroepen wanneer de **huidige** grensgroep. Een client kan meer dan één grensgroep huidige hebben.
- Een of meer sitesysteemrollen.  Clients kunnen altijd gebruik van sitesysteemrollen die zijn gekoppeld aan hun huidige grensgroep. Afhankelijk van extra configuraties ze mogelijk gebruik van sitesysteemrollen in extra grensgroepen.  

Voor elke grensgroep die u maakt, kunt u een eenzijdige koppeling naar een andere grensgroep configureren. De koppeling wordt aangeroepen een **relatie**. De grensgroepen u een koppeling naar heten **neighbor** grensgroepen. Een grensgroep kan meerdere relaties, elk met een specifieke neighbor grensgroep hebben.

De configuratie van elke relatie bepaalt wanneer een client die geen een beschikbaar sitesysteemserver in de huidige grensgroep kunt beginnen met zoeken in een grensgroep neighbor om te zoeken naar een beschikbare site-systeem gevonden. Deze zoekopdracht van extra groepen heet **alternatieve**.

## <a name="fallback"></a>Terugval
Om problemen te voorkomen voor clients wanneer ze een beschikbare site-systeem kunnen niet in de huidige grensgroep vinden, definieert u relaties tussen die alternatieve gedrag definieert. Terugval kiest, kan een client de zoekopdracht uitvouwen tot extra grensgroepen voor het zoeken naar een beschikbare site-systeem.

Relaties worden geconfigureerd op de eigenschappen van een grensgroep **relaties** tabblad. Wanneer u een relatie configureert, moet u een koppeling aan een grensgroep neighbor definiëren. U kunt onafhankelijke instellingen voor terugval aan deze grensgroep neighbor configureren voor elk type van de sitesysteemrol die wordt ondersteund. Als u bijvoorbeeld bij het configureren van een relatie met een specifieke grensgroep kunt u instellen fallback voor distributiepunten te ruimen na 20 minuten in plaats van de standaardwaarde van 120. Zie [voorbeeld van het gebruik van grensgroepen](#example-of-using-boundary-groups) voor een uitgebreider voorbeeld.

Als een client een beschikbare sitesysteemrol niet vinden in de huidige grensgroep mislukt, gebruikt de client de alternatieve tijd in minuten na hoe lang deze beginnen kan met zoeken naar een beschikbare sitesysteem dat is gekoppeld aan deze grensgroep neighbor bepalen.  

Wanneer een client een sitesysteem beschikbaar is niet gevonden en begint met zoeken naar locaties van neighbor grensgroepen, neemt de groep met beschikbare sitesystemen die op een manier die is gedefinieerd door de configuratie van grensgroepen en hun relaties kan worden gebruikt.

- Een grensgroep kan meer dan één relatie hebben. Hiermee kunt u voor elk type sitesysteem naar andere neighbors na verschillende perioden terugval configureren.    
- Clients worden alleen terugval aan een grensgroep die een directe neighbor van hun huidige grensgroep.
- Wanneer een client lid is van meerdere grensgroepen behoort, wordt de huidige grensgroep gedefinieerd als een samenvoeging van die grensgroepen zijn van de client. Client kan vervolgens terugval naar neighbors van elk van de oorspronkelijke grensgroepen.

### <a name="the-default-site-boundary-group"></a>De standaardgroep voor de grens van site
Naast de grensgroepen die u maakt, heeft elke site een standaard sitegrensgroep die is gemaakt door Configuration Manager. Deze groep heet ***standaard---Sitegrensgroep&lt;sitecode >***. Bijvoorbeeld, de groep voor site ABC naam *standaard---Sitegrensgroep&lt;ABC >.*

Voor elke grensgroep die u maakt, maakt Configuration Manager automatisch een impliciete koppelen aan elke grensgroep standaard site in de hiërarchie.
-    De impliciete koppeling is een standaard terugvaloptie uit een huidige grensgroep toe aan de grensgroep voor sites standaard waarvoor een alternatieve standaardtijd van 120 minuten.
-    Clients die zich niet op een grens die is gekoppeld aan andere grensgroepen die in uw hiërarchie voor het gebruik van de standaard sitegrensgroep van hun toegewezen site om te identificeren geldig sitesysteemrollen die kan worden gebruikt.

Terugval toe aan de grensgroep standaard site beheren:
- U kunt gaat u naar de site standaard grensgroep eigenschappen en wijzigt u de waarden op de **standaardgedrag** tabblad. Wijzigingen die u hier van toepassing aanbrengt op *alle* geïmpliceerde koppelingen naar deze grensgroep. Deze instellingen kunnen worden overschreven als u de expliciete koppeling voor deze grensgroep standaard site uit een andere grensgroep configureren.
- U kunt gaat u naar de eigenschappen van een grensgroep die u hebt gemaakt en de waarden voor de expliciete koppeling naar een standaard sitegrensgroep wijzigen. Als u een nieuwe tijd in minuten voor terugval of blok terugval instelt, wordt die wijziging alleen de koppeling die u configureert. Configuraties van de expliciete koppeling overschrijven die op de **standaardgedrag** tabblad van een standaard sitegrensgroep.


## <a name="site-assignment"></a>Site-toewijzing  
 U kunt iedere grensgroep configureren met een toegewezen site voor clients.  

-   Een geïnstalleerde client die automatische sitetoewijzing gebruikt doet u mee aan de toegewezen site van een grensgroep die de huidige netwerklocatie van de client bevat.  
-   Na toewijzing aan een site, wordt de sitetoewijzing van een client niet gewijzigd wanneer de netwerklocatie ervan wordt gewijzigd. Bijvoorbeeld als de client naar een nieuwe netwerklocatie dat wordt vertegenwoordigd door een grens in een grensgroep met een andere sitetoewijzing roamt, blijft van de client toegewezen site ongewijzigd.  
-   Wanneer door Active Directory-systeemdetectie een nieuwe bron wordt gedetecteerd, worden netwerkgegevens voor de gedetecteerde bron geëvalueerd op basis van de grenzen in grensgroepen. In dit proces wordt de nieuwe bron aan een toegewezen site gekoppeld voor de push-clientinstallatie.  
-   Wanneer een grens lid is van meerdere grensgroepen met verschillende toegewezen sites, selecteren de clients willekeurig een van de sites.  
-   Wijzigingen in de toegewezen site van een grensgroep gelden alleen voor nieuwe toewijzingen aan de site. Clients die eerder aan een site zijn toegewezen, evalueren hun sitetoewijzing niet opnieuw op basis van de wijzigingen in de configuratie van een grensgroep (of hun eigen netwerklocatie).  

Zie voor meer informatie over clientsitetoewijzing [automatische sitetoewijzing gebruiken voor Computers](../../../../core/clients/deploy/assign-clients-to-a-site.md#BKMK_AutomaticAssignment) in [clients toewijzen aan een site in System Center Configuration Manager](../../../../core/clients/deploy/assign-clients-to-a-site.md).  

## <a name="distribution-points"></a>Distributiepunten

Wanneer een client de locatie van een distributiepunt vraagt, stuurt Configuration Manager de client een lijst met de sitesystemen van het juiste type die zijn gekoppeld aan elke grensgroep die de huidige netwerklocatie van clients:

-   **Tijdens softwaredistributie**, vragen clients een locatie voor de implementatie-inhoud is beschikbaar vanuit een distributiepunt of andere geldige inhoudsbron (zoals een client die is geconfigureerd voor Peer-Cache).

-   **Tijdens de implementatie van besturingssysteem**, vragen clients een locatie verzenden of ontvangen van hun statusmigratie-informatie.  

Tijdens de implementatie van inhoud, als een client inhoud die niet beschikbaar is van een bron in de huidige grensgroep aanvraagt blijft de client om aan te vragen die inhoud probeert verschillende inhoudsbronnen in de huidige grensgroep totdat de alternatieve periode voor een grensgroep neighbor of de standaard-sitegrensgroep is bereikt. Als de client nog niet voor inhoud gevonden heeft, het de zoekactie voor inhoudsbronnen op te nemen van de grensgroepen neighbor vervolgens wordt uitgebreid.

Echter als de inhoud wordt gedistribueerd op aanvraag en niet beschikbaar is op een distributiepunt op verzoek van een client, begint het proces voor het overbrengen van de inhoud naar het distributiepunt en het is mogelijk dat de client die server vindt als inhoudsbron voordat voor het gebruik van een neighbor-grensgroep.

## <a name="software-update-points"></a>Software-updatepunten
Vanaf versie 1702 clients grensgroepen gebruiken om te zoeken naar een nieuw software-updatepunt. U kunt afzonderlijke software-updatepunten toevoegen aan andere grensgroepen om te bepalen welke servers die een client kunt vinden.

Wanneer u een van een eerdere versie dan 1702 update, worden alle bestaande software-updatepunten toegevoegd aan de standaard sitegrensgroep op elke site. Dit houdt de werking van de vooraf update waarmee clients een software-updatepunt selecteren uit de groep met beschikbare software-updatepunten die u hebt geconfigureerd voor uw hiërarchie.  Dit gedrag wordt gehandhaafd totdat u afzonderlijke software-updatepunten toevoegen aan andere grensgroepen voor selectie van gecontroleerde en alternatieve gedrag.

Als u een nieuwe site installeert die versie 1702 uitvoert of hoger, moet u software-updatepunten aan een grensgroep voordat clients kunnen zoeken en ze gebruiken.


Terugval voor software-updatepunten is geconfigureerd als andere sitesysteemrollen, maar heeft de volgende voorbehouden:
- **Nieuwe clients gebruiken grensgroepen voor het selecteren van software-updatepunten.** Nadat u versie 1702 hebt geïnstalleerd, selecteer nieuwe clients die u installeert een software-updatepunt degene die zijn gekoppeld aan de grensgroepen die u hebt geconfigureerd.

  Dit vervangt het gedrag van het vorige waar clients selecteren op een software-updatepunt willekeurig uit een lijst met computers die delen van het forest van de client.

- **Eerder blijven geïnstalleerde clients met hun huidige software-updatepunt pas nadat deze alternatieve zoeken naar een nieuwe.** Clients die eerder zijn geïnstalleerd en die al een software-updatepunt blijft dat software-updatepunt gebruiken tot deze server kan niet worden bereikt. Dit omvat een software-updatepunt is niet gekoppeld aan de huidige grensgroep van de client kunnen blijven gebruiken.

  Wanneer een client die al heeft een software-updatepunt niet kan bereiken deze, kan de client vervolgens terugval om te zoeken naar een andere. Wanneer u terugval, ontvangt de client een lijst met alle software-updatepunten uit de huidige grensgroep. Als het mislukt om te zoeken naar een beschikbare server gedurende 120 minuten, wordt deze vervolgens terugval diens grensgroepen onderhoudt van neighbor en de standaard sitegrensgroep. Terugval aan beide grensgroepen komt op hetzelfde moment doordat de software-updatepunten fallback tijd neighbor groepen is ingesteld op 120 minuten en kan niet worden gewijzigd. 120 minuten is ook de standaardperiode voor terugval toe aan de grensgroep standaard site gebruikt. Wanneer een client terugvalt op beide neighbor en standaard-sitegrensgroep, de client probeert contact te maken met software-updatepunten uit de grensgroep neighbor voordat u probeert een van de standaard sitegrensgroep te gebruiken.

  De te kunnen blijven gebruiken van een bestaande software-updatepunt zelfs wanneer deze server niet in de huidige grensgroep van de client is is opzettelijke. Dit komt doordat een wijziging van de software-updatepunt tot een grote gebruik van netwerkbandbreedte leiden kan als de client worden gegevens gesynchroniseerd met de nieuwe software-updatepunt. De vertraging in de overgangsfase kan helpen voorkomen overbelasting van uw netwerk moet al uw clients naar een nieuwe software overschakelen-updatepunt op hetzelfde moment.

- **Configuraties voor alternatieve tijd:**  In tegenstelling tot alternatieve configuraties voor andere sitesysteemrollen ondersteunen software-updatepunten niet een configureerbare tijd in minuten. In plaats daarvan is fallback gedrag beperkt tot het volgende:  
  - **Alternatieve tijden (in minuten):**  Deze optie is niet beschikbaar voor software-updatepunten en kan niet worden geconfigureerd. Dit is ingesteld op 120 minuten.
  -     **Nooit fallback:** Wanneer u deze configuratie gebruikt, kunt u terugval voor een software-updatepunt aan een grensgroep neighbor blokkeren.

## <a name="preferred-management-points"></a>Voorkeursbeheerpunten

 Met voorkeursbeheerpunten kunnen clients een beheerpunt identificeren dat is gekoppeld aan de huidige netwerklocatie (grens).  

-   Een client probeert te gebruiken een voorkeursbeheerpunt in de toegewezen site voordat u een beheerpunt vanuit zijn toegewezen site die niet is geconfigureerd als voorkeur.  
-   U moet voor het gebruik van deze optie inschakelen voor de hiërarchie en vervolgens grensgroepen configureren op afzonderlijke primaire sites om inclusief de beheerpunten die gekoppeld aan deze grensgroep gekoppelde grenzen worden moeten.  
-   Wanneer voorkeursbeheerpunten zijn geconfigureerd en een client, de lijst met beheerpunten ordent, wordt de client de voorkeur beheerpunten boven aan de lijst met beheerpunten toegewezen (waarbij alle beheerpunten van de client toegewezen site).  

> [!NOTE]  
>  Wanneer een client roamt (dat wil zeggen dat de client van netwerklocatie verandert, bijvoorbeeld wanneer een laptop op een externe locatie wordt gebruikt) maakt deze mogelijk gebruik van een beheerpunt (of proxybeheerpunt) van de lokale site op de nieuwe locatie voordat de client probeert een beheerpunt te gebruiken vanuit de toegewezen site (inclusief de voorkeursbeheerpunten).  Zie [begrijpen hoe clients vinden sitebronnen en services voor System Center Configuration Manager](../../../../core/plan-design/hierarchy/understand-how-clients-find-site-resources-and-services.md) voor meer informatie.  

### <a name="overlapping-boundaries"></a>Overlappende grenzen  
 Configuration Manager ondersteunt configuraties met overlappende grenzen voor Inhoudslocatie:  

-   **Wanneer een client inhoud aanvraagt**, en de clientnetwerklocatie behoort tot meerdere grensgroepen, Configuration Manager stuurt de client een lijst van alle distributiepunten die de inhoud bevatten.  
-   **Wanneer een client een aanvraag een server te verzenden of ontvangen van statusmigratie-informatie**, en de clientnetwerklocatie behoort tot meerdere grensgroepen, Configuration Manager stuurt de client een lijst met statusmigratiepunten die zijn gekoppeld aan een grensgroep die de huidige netwerklocatie van de client.  

De client kan door dit gedrag de dichtstbijzijnde server selecteren vanwaar inhoud of statusmigratie-informatie wordt overgedragen.  



## <a name="example-of-using-boundary-groups"></a>Voorbeeld van het gebruik van grensgroepen
Het volgende voorbeeld wordt een client zoeken naar inhoud vanaf een distributiepunt. In dit voorbeeld kan worden toegepast op andere systeemsite-functies die gebruikmaken van grensgroepen. Echter, zoals wordt toegepast op software-updatepunten, houd in gedachten dat software-updatepunten geen ondersteuning voor configuratie van een tijd in minuten voor terugval naar een neighbor-groep en gebruik altijd een periode van 120 minuten.

U maken drie grensgroepen die niet grenzen of sitesysteemservers delen:
-    Groep BG_A met distributiepunten DP_A1 en DP_A2 die zijn gekoppeld aan de groep
-    Groep BG_B met distributiepunten DP_B1 en DP_B2 die zijn gekoppeld aan de groep
-    Groep BG_C met distributiepunten DP_C1 en DP_C2 die zijn gekoppeld aan de groep

U de netwerklocaties van uw clients toevoegen als grenzen tot aan de grensgroep BG_A en u vervolgens relaties uit die grensgroep aan de andere twee grensgroepen configureren:
-    Configureren van distributiepunten voor de eerste *neighbor* groep (BG_B) moet worden gebruikt na 10 minuten. Deze groep bevat distributiepunten DP_B1 en DP_B2. Beide zijn goed verbonden zijn met de eerste groepen grenslocaties.
-    Configureren van de tweede *neighbor* groep (BG_C) moet worden gebruikt na 20 minuten. Deze groep bevat distributiepunten DP_C1 en DP_C2. Beide worden via een WAN van de andere twee grensgroepen.
-    U ook toevoegen een extra distributiepunt dat zich bevindt op de siteserver aan de grensgroep sites standaard site. Dit is de locatie van de minste voorkeur inhoudsbron, maar het is centraal bevindt aan alle grensgroepen.

    Voorbeeld van grensgroepen en alternatieve tijden:

     ![BG_Fallack](media/BG_Fallback.png)


Met deze configuratie:
-    De client begint met zoeken naar inhoud vanaf distributiepunten in de *huidige* grensgroep (BG_A), zoeken naar elk distributiepunt wijst twee minuten voordat u overschakelt naar het volgende distributiepunt in de grensgroep. De groep clients geldige inhoud bronlocaties omvat DP_A1 en DP_A2.
-    Als de client niet kan vinden van inhoud van de *huidige* grensgroep na 10 minuten zoekt, vervolgens wordt toegevoegd de distributiepunten van de grensgroep BG_B de zoekopdracht. Vervolgens gaat door om te zoeken naar inhoud vanaf een distributiepunt in de gecombineerde toepassingen van distributiepunten die bevat nu informatie over de objecten uit de BG_A en de BG_B grensgroepen. Neem contact op met elk distributiepunt twee minuten voordat u overschakelt naar het volgende distributiepunt uit de groep blijft de client. De groep clients geldige inhoud bronlocaties omvat DP_A1, DP_A2 DP_B1 en DP_B2.
-    Na nog 10 minuten zijn verstreken (totaal 20 minuten) als de client nog steeds niet een distributiepunt met inhoud gevonden is, het breidt de adresgroep van beschikbare distributiepunten op te nemen die uit de tweede *neighbor* groeperen, grensgroep BG_C. De client 6 distributiepunten om te zoeken (DP_A1, DP_A2 DP_B2, DP_B2, DP_C1 en DP_C2) is nu en blijft het wijzigen van een nieuw distributiepunt om twee minuten tot inhoud is gevonden.
-    Als de client niet voor inhoud na een totaal van 120 minuten gevonden is, vallen terug zodat de *sitegrensgroep standaard* als onderdeel van de verder te zoeken. Distributiepunten in de groep bevat nu alle distributiepunten van de drie geconfigureerde grensgroepen en het laatste distributiepunt zich op de site server-computer.  Vervolgens blijft de client de zoekopdracht voor inhoud, distributiepunten wijzigen om twee minuten tot inhoud is gevonden.

U bepaalt wanneer specifieke distributiepunten worden toegevoegd als een inhoudsbronlocatie en wanneer, of als de client voor inhoud die niet beschikbaar is van een andere locatie veiligheidsredenen terugval toe aan de grensgroep standaard site gebruikt door het configureren van de verschillende neighbor groepen zijn beschikbaar op verschillende tijdstippen.






### <a name="update-existing-boundary-groups-to-the-new-model"></a>Bestaande grensgroepen in het nieuwe model bijwerken
Wanneer u naar versie vóór 1610 bijwerkt, worden de volgende configuraties automatisch gemaakt. Deze zijn bedoeld om ervoor te zorgen dat uw huidige alternatieve gedrag blijft beschikbaar totdat u een nieuwe grensgroepen en relaties configureren.

-    Een standaard sitegrensgroep is gemaakt voor elke primaire site, de naam is ***standaard---Sitegrensgroep&lt;sitecode >.***
  -    Distributiepunten met *terugvalbronlocatie voor inhoud toestaan* gecontroleerd en statusmigratiepunten op primaire sites worden toegevoegd aan de *standaard---Sitegrensgroep&lt;sitecode >* grensgroep van die site.
  -    Vanaf versie 1702, software-updatepunten zijn toegevoegd aan elke sites *standaard---Sitegrensgroep&lt;sitecode >*.
-    Een kopie wordt van elke bestaande grensgroep die een siteserver die is geconfigureerd met een langzame verbinding gemaakt. De naam van de nieuwe groep is *** &lt;oorspronkelijke grens groepsnaam >-&lt;oorspronkelijke grens groeps-ID >***:  
    -    Sitesystemen waarop een snelle verbinding blijven in de oorspronkelijke grensgroep.
    -    Een kopie van de site-systemen (distributiepunten, beheerpunten) die een trage verbinding hebt worden toegevoegd aan de kopie van de grensgroep. De oorspronkelijke sitesystemen zijn geconfigureerd als langzaam blijven in de oorspronkelijke grensgroepen voor achterwaartse compatibiliteit, maar niet van die grensgroepen zijn gebruikt.
    - Deze kopie van de groep grens heeft geen grenzen die ermee verbonden zijn. Echter wordt een alternatieve koppeling gemaakt tussen de oorspronkelijke groep en de nieuwe grens groep kopie bevat de alternatieve tijd ingesteld op nul.  


- **Specifiek zijn voor secundaire sites:**
  - Een grensgroep wordt gemaakt als een secundaire site ten minste één distributiepunt is met *terugvalbronlocatie voor inhoud toestaan* statusmigratiepunten ingeschakeld of status. De naam van de grensgroep is ***secundaire-Site-Neighbor--Tmp&lt;Sitecode >.***
  - Alle distributiepunten met *terugvalbronlocatie voor inhoud toestaan* gecontroleerd en statusmigratiepunten worden toegevoegd aan deze grensgroep nieuwe secundaire site.
  - Een fallback-koppeling wordt gemaakt tussen de oorspronkelijke grensgroep en de zojuist gemaakte neighbor grensgroep en de alternatieve tijd is ingesteld op nul.


 De volgende tabel bevat de nieuwe alternatieve gedrag u kunt verwachten van de combinatie van de oorspronkelijke implementatie-instellingen en distributie wijst configuraties:

Oorspronkelijke implementatieconfiguratie voor "Programma niet uitvoeren" in langzaam netwerk  |Configuratie voor 'Client toestaan een terugvalbronlocatie voor inhoud te gebruiken' oorspronkelijke distributiepunt  |Nieuw alternatief gedrag  
---------|---------|---------
Geselecteerd     |  Geselecteerd    |  **Er is geen terugval** -enkel de distributiepunten in de huidige grensgroep gebruiken       
Geselecteerd     |  Niet ingeschakeld|  **Er is geen terugval** -enkel de distributiepunten in de huidige grensgroep gebruiken       
Niet ingeschakeld |  Niet ingeschakeld|  **Fallback naar neighbor** - gebruik van de distributiepunten in de huidige grensgroep en klikt u vervolgens de distributiepunten toevoegen van de grensgroep neighbor. Tenzij een expliciete koppeling naar de standaardgroep voor de grens van site is geconfigureerd, clients zal nalaten fallback naar die groep.    
Niet ingeschakeld | Geselecteerd        |   **Normale terugval** -distributiepunten in de huidige grensgroep gebruiken, dan die van de site en neighbor standaard grensgroepen

 Alle andere configuraties voor de implementatie leiden tot **normale terugval**.  




## <a name="changes-from-prior-versions-for-ui-and-behavior-for-content-locations"></a>Wijzigingen van eerdere versies van automatische updates-UI en gedrag voor locatie van inhoud
Hier volgen de belangrijkste wijzigingen in grensgroepen en hoe clients inhoud vinden. Deze wijzigingen zijn aangebracht met versie 1610. Veel van deze wijzigingen en concepten samenwerken.


-    **Configuraties voor snel of traag zijn verwijderd:** U configureert niet langer individuele distributiepunten om snel of traag.  In plaats daarvan elk sitesysteem dat is gekoppeld aan een grensgroep wordt behandeld hetzelfde. Vanwege deze wijziging, de **verwijzingen** tabblad van eigenschappen van de grensgroep biedt geen ondersteuning voor de configuratie van snel of traag.
-     **Nieuwe standaard grensgroep op elke site:**  Elke primaire site heeft een nieuwe standaard grensgroep met de naam ***standaard---Sitegrensgroep&lt;sitecode >***.  Wanneer een client zich niet op een netwerklocatie bevindt die is toegewezen aan een grensgroep bevindt, dat de client de sitesystemen die zijn gekoppeld aan de standaardgroep van de toegewezen site gebruiken. Wilt u deze grensgroep gebruiken als een vervangende met het concept van een locatie terugvalinhoudlocatie.      
 -    **'Alternatieve bronlocaties voor inhoud toestaan'** wordt verwijderd: U configureert niet langer expliciet een distributiepunt moet worden gebruikt voor terugval en de opties in te stellen dit worden verwijderd uit de gebruikersinterface.

    Daarnaast het resultaat van de instelling **clients met een terugvalbronlocatie voor inhoud toestaan** op een implementatie van het type voor toepassingen is gewijzigd. Deze instelling op een implementatietype te detecteren, kunnen clients de standaard sitegrensgroep gebruiken als bronlocatie voor inhoud.

 -    **Grens groepen relaties:** Elke grensgroep kan worden gekoppeld aan een of meer extra grensgroepen. Deze koppelingen vormen relaties die zijn geconfigureerd op de nieuwe grens groep tabblad Eigenschappen met de naam **relaties**:
     -    Elke grensgroep die een client rechtstreeks is gekoppeld aan heet een **huidige** grensgroep.  
    -     Andere grensgroepen die een client kan gebruiken als gevolg van een koppeling tussen die client *huidige* grensgroep en een andere groep heet een **neighbor** grensgroep.
    -  Deze zich op de **relaties** tabblad dat u die kunnen worden gebruikt toevoegt als een *neighbor* grensgroep. U kunt ook een tijd in minuten dat bepaalt wanneer een client die niet kunnen zoeken naar inhoud vanaf een distributiepunt in de *huidige* begint om te zoeken naar de locatie van inhoud van die groep *neighbor* grensgroepen.

        Wanneer u toevoegen of wijzigen van de configuratie van een grensgroep, hebt u de optie naar blok fallback naar die grensgroep specifieke van de huidige groep die u configureert.

    Expliciete koppelingen (koppelingen) uit een grensgroep definiëren voor het gebruik van de nieuwe configuratie en alle distributiepunten configureren in de gekoppelde groep met dezelfde tijd in minuten. De tijd die u configureert bepaalt wanneer een client die niet kunnen vinden van een inhoudsbron van de *huidige* grensgroep kunt beginnen met zoeken naar inhoudsbronnen uit die groep neighbor grens.

    Naast de grensgroepen die uitdrukkelijk configureren, heeft elke grensgroep een impliciete koppeling naar de standaard sitegrensgroep. Deze koppeling wordt geactiveerd nadat 120 minuten op dat moment wordt de standaardgroep van de site-grens van een neighbor-grensgroep waarmee de clients om de distributiepunten die zijn gekoppeld aan deze grensgroep als bronlocatie voor inhoud te gebruiken.

    Dit gedrag vervangt wat eerder is aangeduid als terugval voor inhoud.  U kunt dit standaardgedrag van 120 minuten door expliciet koppelen van de grensgroep standaard website naar een *huidige* groep, en het instellen van een bepaalde tijd in minuten of blokkeren terugval volledig om te voorkomen dat het gebruik ervan.


-     **Clients proberen inhoud op te halen van elk distributiepunt tot 2 minuten:** Wanneer een client zoekt naar een locatie van de inhoudsbron, probeert ze toegang krijgen tot elk distributiepunt 2 minuten en probeer het vervolgens een ander distributiepunt. Dit is een wijziging ten opzichte van eerdere versies waar clients heeft geprobeerd verbinding maken met een distributiepunt maximaal 2 uur.

    - Het eerste distributiepunt dat u een client probeert te gebruiken is willekeurig hebt geselecteerd in de groep met beschikbare distributiepunten in de client *huidige* grensgroep (of groepen).

    - Na twee minuten als de client niet voor de inhoud gevonden is deze verandert in een nieuw distributiepunt en probeert inhoud op te halen van die server. Dit proces wordt herhaald voor elke twee minuten totdat de client de inhoud is gevonden of de laatste server in de groep van toepassingen is bereikt.

    - Als een client een geldig inhoudsbronlocatie uit niet vinden de *huidige* groep voordat u de periode voor terugval naar een *neighbor* grensgroep is bereikt, wordt de client worden de distributiepunten uit die *neighbor* groeperen met het einde van de huidige lijst en zoek vervolgens de uitgevouwen groep bronlocaties die de distributiepunten van beide grensgroepen bevat.

        > [!TIP]  
        > Wanneer u een expliciete koppeling te van de huidige grensgroep toe aan de grensgroep standaard site maken en een alternatief tijd die kleiner is dan de alternatieve tijd voor een koppeling naar een grensgroep neighbor definiëren, zullen clients begint met zoeken bronlocaties van de standaard sitegrensgroep voordat de neighbor-groep.

    - Wanneer de client niet kan inhoud op te halen uit de laatste server in de groep, begint het proces opnieuw.


## <a name="procedures-for-boundary-groups"></a>Procedures voor grensgroepen
De volgende procedures gelden voor 1610 of hoger. Als u gebruikmaakt van versie vóór 1610, Zie de procedures in [grensgroepen voor System Center Configuration Manager-versies 1511 1602 en 1606](/sccm/core/servers/deploy/configure/boundary-groups-for-1511-1602-and-1606).


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

 6.  Selecteer de **relaties** tabblad om alternatieve gedrag te configureren:  

     - Klik op **toevoegen**, en selecteer vervolgens de grensgroep die u wilt configureren.

     - Een fallback tijd instellen voor distributiepunten. Na deze periode, is clients in de grensgroep die u relaties configureert, mogelijk om te beginnen met zoeken naar inhoud vanaf distributiepunten van de grensgroep die u wilt toevoegen.

     - Om te voorkomen dat terugval naar een specifieke grens, met inbegrip van de *standaard sitegrensgroep* die standaard is geconfigureerd, selecteer de grensgroep en klikt u vervolgens het selectievakje in voor **nooit alternatieve**.   

 7.  Klik op **OK** om de eigenschappen van de grensgroep te sluiten en de configuratie op te slaan.  

#### <a name="to-associate-a-site-systme-server-with-a-boundary-group"></a>Een siteserver systme koppelen aan een grensgroep  
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

 1.  Klik in de Configuration Manager-console op **beheer** > **siteconfiguratie** > **Sites**, en klik vervolgens op de **Start** Selecteer tabblad **hiërarchie-instellingen**.  

 2.  Selecteer op het tabblad **Algemeen** van de hiërarchie-instellingen de optie **Clients gebruiken liever beheerpunten die zijn opgegeven in grensgroepen**.  

 3.  Klik op **OK** om het dialoogvenster te sluiten en de configuratie op te slaan.  

