---
title: Grensgroepen configureren
titleSuffix: Configuration Manager
description: Clients zoeken sitesystemen met behulp van grensgroepen te organiseren logisch gerelateerde netwerklocaties grenzen genoemd Help
ms.custom: na
ms.date: 03/22/2018
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: get-started-article
ms.assetid: 5db2926f-f03e-49c7-b44b-e89b1a5a6779
caps.latest.revision: ''
author: mestew
ms.author: mstewart
manager: dougeby
ms.openlocfilehash: 297f4a5ecb7650a4ea643fff00dd67b6580256de
ms.sourcegitcommit: 11bf4ed40ed0cbb10500cc58bbecbd23c92bfe20
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 03/23/2018
---
# <a name="configure-boundary-groups-for-system-center-configuration-manager"></a>Grensgroepen configureren voor System Center Configuration Manager


*Van toepassing op: System Center Configuration Manager (huidige vertakking)*

Grensgroepen gebruiken in Configuration Manager te organiseren logisch gerelateerde netwerklocaties ([grenzen](/sccm/core/servers/deploy/configure/boundaries)) om het gemakkelijker om uw infrastructuur te beheren. Grenzen eerst toewijzen aan grensgroepen voordat u de grensgroep.

Configuration Manager maakt een standaard sitegrensgroep standaard op elke site.

Voor het configureren van grensgroepen grenzen (netwerklocaties) en sitesysteemrollen, zoals distributiepunten aan de grensgroep te koppelen. Deze configuratie helpt om clients met sitesysteemservers koppelen zoals distributiepunten die zich bevinden in de buurt van de clients op het netwerk.

Voor een betere beschikbaarheid van sitesystemen worden in-servers, zoals distributiepunten voor een breed scala aan netwerklocaties, dezelfde grens en dezelfde server toewijzen aan meerdere grensgroepen.

Clients gebruiken een grensgroep voor:  

-   Automatische sitetoewijzing  
-   Vinden van een sitesysteemserver die een service biedt, waaronder:
    - Distributiepunten voor de locatie van inhoud
    -   Software-updatepunten
    - Statusmigratiepunten
    - Voorkeursbeheerpunten (als u voorkeursbeheerpunten gebruikt, moet u deze optie voor de hiërarchie en niet vanuit inschakelen configuratie van de grensgroep. Zie [gebruik van voorkeursbeheerpunten inschakelen](#to-enable-use-of-preferred-management-points) in dit onderwerp.)

##  <a name="boundary-groups-and-relationships"></a>Grensgroepen en relaties
Voor elke grensgroep in uw hiërarchie, kunt u het volgende toewijzen:

-  Een of meer grenzen. Een client **huidige** grensgroep is een netwerklocatie die is gedefinieerd als een grens die is toegewezen aan een specifieke grensgroep. Een client kan meer dan één grensgroep huidige hebben.
- Een of meer sitesysteemrollen. Clients kunnen altijd gebruik van sitesysteemrollen die zijn gekoppeld aan hun huidige grensgroep. Afhankelijk van de aanvullende configuraties, is het mogelijk dat ze sitesysteemrollen in extra grensgroepen gebruiken.  

Voor elke grensgroep die u maakt, kunt u een eenzijdige koppeling naar een andere grensgroep configureren. De koppeling heet een **relatie**. De grensgroepen u een koppeling naar heten **neighbor** grensgroepen. Een grensgroep kan meerdere relaties, elk met een specifieke neighbor grensgroep hebben.

Wanneer een client niet kan vinden van een beschikbare sitesysteemserver in de huidige grensgroep, wordt de configuratie van elke relatie bepaalt wanneer deze begint met het zoeken van een neighbor grensgroep. Deze zoekopdracht van extra groepen heet **terugval**.

## <a name="fallback"></a>Terugval
Om problemen te voorkomen wanneer clients een beschikbare sitesysteem in hun huidige grensgroep niet kunnen vinden, de relatie tussen grensgroepen voor terugval gedrag te definiëren. Terugval kunt een client de zoekactie aan extra grensgroepen vinden van een systeem beschikbare site uitbreiden.

Relaties zijn geconfigureerd op de eigenschappen van een grensgroep **relaties** tabblad. Wanneer u een relatie configureert, moet u een koppeling aan een grensgroep neighbor definiëren. Voor elk type ondersteunde sitesysteemrol, onafhankelijke instellingen voor de grensgroep neighbor terugvallen te configureren. Bijvoorbeeld bij het configureren van een relatie met een specifieke grensgroep instellen voor distributiepunten om te worden uitgevoerd na 20 minuten in plaats van de standaardwaarde van 120 terugval. Zie voor een uitgebreider voorbeeld [voorbeeld van het gebruik van grensgroepen](#example-of-using-boundary-groups).

Als een client niet een beschikbare sitesysteemrol niet vinden in de huidige grensgroep, gebruikt de client de terugval tijd in minuten. Deze tijd terugval bepaalt wanneer de client om te zoeken naar een beschikbare sitesysteem die zijn gekoppeld aan de grensgroep neighbor begint.  

Wanneer een client een beschikbare sitesysteem niet vinden kan en begint met zoeken naar de locaties van neighbor grensgroepen, neemt de groep met beschikbare sitesystemen. De configuratie van grensgroepen en hun relaties definieert van de client gebruik van deze groep van beschikbare sitesystemen.

- Een grensgroep kan meer dan één relatie hebben. U kunt terugval voor elk type sitesysteem naar andere neighbors na verschillende perioden configureren met meerdere relaties.    
- Clients alleen terugval aan een grensgroep die een directe neighbor van hun huidige grensgroep.
- Wanneer een client lid is van meerdere grensgroepen, wordt de huidige grensgroep gedefinieerd als een samenvoeging van de grensgroepen van de client. De client schakelt terug naar neighbors van elk van de oorspronkelijke grensgroepen.

### <a name="the-default-site-boundary-group"></a>De standaardgroep voor de grens van site
Naast de grensgroepen die u maakt, heeft elke site een standaard sitegrensgroep die is gemaakt door Configuration Manager. Deze groep heet ***-Site-grens-standaardgroep&lt;sitecode >***. Bijvoorbeeld de naam van de groep voor site ABC zou worden *-Site-grens-standaardgroep&lt;ABC >.*

Voor elke grensgroep die u maakt, maakt Configuration Manager automatisch een impliciete koppelen aan elke grensgroep van standaard site in de hiërarchie.
-   De impliciete koppeling is een standaard terugvaloptie uit een huidige grensgroep toe aan de grensgroep voor sites standaard bevat een standaard terugval tijd van 120 minuten.
-   Voor clients niet in een grens die aan een grensgroep zijn gekoppeld: om te identificeren geldig sitesysteemrollen, gebruikt u de standaard sitegrensgroep van hun toegewezen site.

Terugvallen op de standaard sitegrensgroep beheren:
- Open de eigenschappen van de groep site standaard grens en wijzig de waarden op de **standaardgedrag** tabblad. Wijzigingen die u hier van toepassing aanbrengt op *alle* geïmpliceerde koppelingen naar deze grensgroep. Deze instellingen kunnen worden overschreven wanneer u de expliciete koppeling aan deze grensgroep van standaard site uit een andere grensgroep configureren.
- Open de eigenschappen van een aangepaste grensgroep. Wijzig de waarden voor de expliciete koppeling naar een standaard sitegrensgroep. Als u een nieuwe tijd in minuten voor terugval of blok terugval instelt, wordt die wijziging alleen de koppeling die u configureert. Configuratie van de expliciete koppeling overschrijft de instellingen op de **standaardgedrag** tabblad van een standaard sitegrensgroep.


## <a name="site-assignment"></a>Sitetoewijzing  
 U kunt iedere grensgroep configureren met een toegewezen site voor clients.  

-   Een nieuw geïnstalleerde client die automatische sitetoewijzing gebruikt, koppelt de toegewezen site van een grensgroep die de huidige netwerklocatie van de client bevat.  
-   Na toewijzing aan een site, wordt de sitetoewijzing van een client niet gewijzigd wanneer de netwerklocatie ervan wordt gewijzigd. Als de client naar een nieuwe netwerklocatie dat wordt vertegenwoordigd door een grens in een grensgroep met een andere sitetoewijzing roamt, wordt bijvoorbeeld de client toegewezen site blijven ongewijzigd.  
-   Wanneer door Active Directory-systeemdetectie een nieuwe bron wordt gedetecteerd, worden netwerkgegevens voor de gedetecteerde bron geëvalueerd op basis van de grenzen in grensgroepen. In dit proces wordt de nieuwe bron aan een toegewezen site gekoppeld voor de push-clientinstallatie.  
-   Wanneer een grens lid is van meerdere grensgroepen met verschillende toegewezen sites, selecteer clients willekeurig een van de sites.  
-   Wijzigingen in de toegewezen site van een grensgroep gelden alleen voor nieuwe toewijzingen aan de site. Clients die eerder zijn toegewezen aan een site kunnen niet Herzie hun site-toewijzing op basis van wijzigingen in de configuratie van een grensgroep (of hun eigen netwerklocatie).  

Zie voor meer informatie over clientsitetoewijzing [automatische sitetoewijzing gebruiken voor Computers](../../../../core/clients/deploy/assign-clients-to-a-site.md#BKMK_AutomaticAssignment) in [clients toewijzen aan een site in System Center Configuration Manager](../../../../core/clients/deploy/assign-clients-to-a-site.md).  

## <a name="distribution-points"></a>Distributiepunten

Wanneer een client de locatie van een distributiepunt aanvraagt, stuurt Configuration Manager de client een lijst met sitesystemen. Deze sitesystemen zijn van hetzelfde type die zijn gekoppeld aan elke grensgroep die de huidige netwerklocatie van clients omvat:

-   **Tijdens softwaredistributie**, vragen clients een locatie voor de implementatie-inhoud is beschikbaar vanuit een distributiepunt of andere geldige inhoudsbron (zoals een client die is geconfigureerd voor Peer-Cache).

-   **Tijdens de implementatie van besturingssysteem**, vragen clients een locatie te verzenden of ontvangen van hun migratiestatusinformatie.  

Tijdens de implementatie van inhoud als een client inhoud opvraagt die niet beschikbaar is van een bron in de huidige grensgroep van blijft de client die inhoud opvragen. De client probeert verschillende inhoudsbronnen in de huidige grensgroep totdat de terugval periode is bereikt voor de grensgroep van een neighbor of de standaard sitegrensgroep. Als de client de inhoud nog niet gevonden heeft, deze de zoekactie voor inhoudsbronnen om op te nemen van de grensgroepen neighbor vervolgens wordt uitgebreid.

Als de inhoud wordt gedistribueerd op aanvraag en niet beschikbaar is op een distributiepunt wanneer door een client wordt aangevraagd, wordt het proces voor de inhoud overbrengen naar het distributiepunt begint. Het is mogelijk dat de client zoekt die server als inhoudsbron voordat voor het gebruik van een neighbor grensgroep.

## <a name="software-update-points"></a>Software-updatepunten
Clients gebruiken grensgroepen voor het vinden van een nieuw software-updatepunt. Toevoegen om te bepalen welke servers die een client kunt vinden, afzonderlijke software-updatepunten aan andere grensgroepen.

Als u een van een eerdere versie dan 1702 update, wordt elke site alle bestaande software-updatepunten toegevoegd aan de standaardgroep voor de site-grens. De werking van deze site update onderhoudt het gedrag van de vorige client om te selecteren van software-updatepunt van de groep met beschikbare servers. Dit gedrag behouden totdat u afzonderlijke software-updatepunten toevoegen aan andere grensgroepen voor selectie van gecontroleerde en terugval gedrag kiest.

Als u een nieuwe site installeert, worden software-updatepunten niet toegevoegd aan de standaardgroep voor de site-grens. Software-updatepunten toewijzen aan een grensgroep, zodat clients kunnen vinden en ze gebruiken.

### <a name="fallback-for-software-update-points"></a>Opvang voor software-updatepunten
Opvang voor software-updatepunten is geconfigureerd zoals andere sitesysteemrollen, maar heeft het volgende voorbehoud:
- **Nieuwe clients gebruiken grensgroepen voor het selecteren van software-updatepunten.** Nieuwe clients die u installeert selecteren een software-updatepunt van de servers die zijn gekoppeld aan de grensgroepen die u configureert Dit gedrag vervangt de vorige gedrag waar clients selecteren een software-updatepunt willekeurig uit een lijst van de servers die delen van het forest van de client.

- **Laatst bekende goede software-updatepunt gebruiken totdat ze terugval vinden van een nieuwe blijven clients.** Clients die al een software-updatepunt blijven gebruiken totdat deze kan niet worden bereikt. Dit gedrag bevat blijvende gebruik van een software-updatepunt dat is niet gekoppeld aan de huidige grensgroep van de client.

  Het verder gebruiken van een bestaande software-updatepunt zelfs wanneer de server zich niet in de huidige grensgroep van de client is opzettelijk. Wanneer u de software-update wijzigingen, worden gegevens gesynchroniseerd met de nieuwe server, waardoor aanzienlijke netwerkgebruik van de client. Als alle clients naar een nieuwe server op hetzelfde moment overschakelen, wordt de vertraging in de overgangsfase helpt te voorkomen dat het netwerk overbelast raakt.

- **Een client altijd probeert te bereiken van de laatste bekende juiste software-updatepunt gedurende 120 minuten voordat terugval wordt gestart.** Na 120 minuten als de client niet tot stand contactpersoon gebracht is, begint klikt u vervolgens deze terugval. Wanneer terugval wordt gestart, wordt er door de client een lijst van alle software-updatepunten ontvangt van de huidige grensgroep. Aanvullende software-updatepunten uit neighbor en site standaard grens groepen beschikbaar zijn op basis van terugval configuraties.

### <a name="fallback-configurations-for-software-update-points"></a>Terugval configuraties voor software-updatepunten
#### <a name="beginning-with-version-1706"></a>Vanaf versie 1706   
U kunt configureren **terugval time-out (in minuten)** voor software-updatepunten als minder dan 120 minuten. Echter, probeert de client nog steeds de oorspronkelijke software-updatepunt bereiken gedurende 120 minuten. Vervolgens wordt de zoekactie aan extra servers uitgebreid. Grens groep terugval keren gestart wanneer de client eerst mislukt om de oorspronkelijke server te bereiken. Wanneer de client wordt de zoekopdracht uitgebreid, biedt de site grensgroepen geconfigureerd voor minder dan 120 minuten.

Als u wilt blokkeren opvang voor software-updatepunt aan een grensgroep neighbor, configureert u de instelling voor **nooit terugval**.

Lukt het bereiken van de oorspronkelijke server voor twee uur gebruikt de client vervolgens een kortere cyclus een verbinding maken met een nieuw software-updatepunt. Dit gedrag kan de client snel zoeken door een groeiende lijst met mogelijke software-updatepunten.

 -  **Voorbeeld van terugval:**  
    Huidige grensgroep van een client is een opvang voor software-updatepunten die is geconfigureerd als *10* minuten voor grensgroep *A*, en *130* minuten voor de grensgroep. *B*. Wanneer de client niet kan bereiken van de laatste bekende juiste software-updatepunt:
    -   De client probeert te bereiken alleen de oorspronkelijke server voor de volgende 120 minuten. Na 10 minuten de software-updatepunten uit grensgroep A zijn toegevoegd aan de groep met beschikbare servers. Echter, probeert de client kan geen verbinding maken met deze of een andere server als de eerste periode 120 minuten opnieuw verbinding maken met de oorspronkelijke server is verstreken.
    -   Nadat u hebt geprobeerd om te zoeken die oorspronkelijke software-updatepunt gedurende 120 minuten, uitbreiden de client vervolgens de zoekactie. Op dat moment wordt de client toegevoegd voor servers aan de groep beschikbare software-updatepunten in de huidige en de grensgroepen van een neighbor geconfigureerd voor 120 minuten of minder. Deze groep bevat de servers in grens groep A die eerder zijn toegevoegd aan de groep met beschikbare servers.
    -       Na 10 minuten (130 minuten totale tijd nadat de client eerst kan bereiken van de laatste bekende juiste software-updatepunt), breidt de client de zoekopdracht om op te nemen van software-updatepunten uit grensgroep B.  

#### <a name="prior-to-version-1706"></a>Voorafgaand aan versie 1706
Voorafgaand aan versie 1706 ondersteunen terugval configuraties voor software-updatepunten geen een configureerbare tijd in minuten. In plaats daarvan is terugval gedrag beperkt tot:

  - **Terugval tijden (in minuten):** Deze optie is niet beschikbaar voor software-updatepunten en kan niet worden geconfigureerd. Deze waarde is ingesteld op 120 minuten.
  -     **Nooit terugval:** Wanneer u deze configuratie gebruikt, kunt u opvang voor software-updatepunt aan een grensgroep neighbor blokkeren.

Als een client die een software-updatepunt is al verbinding is mislukt, valt de client vervolgens terug om te zoeken naar een andere. Wanneer u terugval, ontvangt de client een lijst met alle software-updatepunten uit de huidige grensgroep. Als dit een beschikbare server vinden voor 120 minuten mislukt, wordt vervolgens schakelt terug naar de grensgroepen neighbor en de standaard sitegrensgroep. Terugvallen op beide grensgroepen gebeurt op hetzelfde moment. De software-updatepunt terugval tijd neighbor groepen is ingesteld op 120 minuten. U kunt deze tijd terugval niet wijzigen. 120 minuten is ook de standaardperiode gebruikt voor terugval aan de standaardgroep voor de site-grens. Wanneer een client schakelt terug naar zowel een neighbor en standaard sitegrensgroep de client probeert contact opnemen met software-updatepunten uit de grensgroep neighbor voordat u een van de standaardgroep voor de site-grens te gebruiken.

### <a name="manually-switch-to-a-new-software-update-point"></a>Handmatig overschakelen naar een nieuw software-updatepunt
Naast het terugval gebruikt, kunt u *Clientmelding* om af te dwingen handmatig een apparaat overschakelen naar een nieuw software-updatepunt.

Wanneer u naar een nieuwe server overschakelt, met de apparaten terugval zoeken naar die nieuwe server. Controleer de configuratie van grensgroepen. Zorg ervoor dat uw software-updatepunten in de juiste grensgroepen voordat u deze wijziging.

Zie voor meer informatie [clients handmatig overschakelen naar een nieuwe software-updatepunt](/sccm/sum/plan-design/plan-for-software-updates#manually-switch-clients-to-a-new-software-update-point).



## <a name="management-points"></a>Beheerpunten
<!-- 1324594 -->
Vanaf versie 1802, terugval relaties voor beheerpunten tussen grensgroepen configureren. Dit gedrag biedt meer controle over de beheerpunten die clients gebruiken. Op de **relaties** tabblad van de eigenschappen van de grensgroep, is een kolom voor het beheerpunt. Wanneer u een nieuwe terugval grensgroep toevoegt, wordt de terugval tijd voor het beheerpunt is momenteel altijd nul (0). Dit gedrag is hetzelfde voor de **standaardgedrag** op de site-standaardgroep grens.

Voorheen een veelvoorkomend probleem treedt op wanneer er een beveiligde beheerpunt in een beveiligd netwerk. Clients op het bedrijfsnetwerk van de belangrijkste ontvangen beleidsregel met deze beveiligde beheerpunt, zelfs als ze niet kunnen met deze via een firewall communiceren. Om dit probleem op te lossen, gebruikt u de **nooit terugval** optie om ervoor te zorgen dat clients alleen terugval naar management verwijst met die ze kunnen communiceren.

Wanneer de site upgraden naar versie 1802, voegt Configuration Manager alle beheerpunten voor internet facing toe aan de groep site standaard grens. Deze upgrade gedrag zorgt ervoor dat oudere clientversies blijven communiceren met beheerpunten. Om volledig te profiteren van deze functie, uw beheerpunten naar de gewenste grensgroepen te verplaatsen.

Management-punt grens groep terugval verandert het gedrag niet tijdens de clientinstallatie (ccmsetup.exe). Als de opdrachtregel het initiële beheerpunt met de parameter /MP niet is opgegeven, ontvangt de nieuwe client de volledige lijst met beschikbare beheerpunten. De client gebruikt voor de eerste bootstrap-proces voor het eerste beheerpunt dat kunnen worden geopend. Nadat de client bij de site registreert, ontvangt de beheerpuntlijst correct gesorteerd met dit nieuwe gedrag. 

Inschakelen voor clients gebruiken deze mogelijkheid, de volgende instelling: **Clients gebruiken liever beheerpunten die zijn opgegeven in grensgroepen** in **hiërarchie-instellingen**. 

> [!Note]
> Besturingssysteem-implementatieprocessen zijn niet op de hoogte van grensgroepen.

### <a name="troubleshooting"></a>Probleemoplossing
Nieuwe gegevens worden weergegeven de **LocationServices.log**. De **plaats** kenmerk identificeert een van de volgende statussen:
- 0: Onbekend
- 1: Het opgegeven beheerpunt bevindt zich alleen in de groep site standaard grens voor terugval
- 2: Het opgegeven beheerpunt bevindt zich in een neighbor of externe grensgroep. Als het beheerpunt zowel een neighbor en de grensgroepen van de site-standaard is, is de plaats 2.
- 3: Het opgegeven beheerpunt bevindt zich in de grensgroep lokale of huidige. Wanneer het beheerpunt in de huidige grensgroep, evenals een neighbor of de groep site standaard grens is, is de plaats 3. Als u de voorkeursbeheerpunten instellen in de hiërarchie-instellingen niet inschakelt, is de plaats altijd 3 ongeacht welke grens groep het beheerpunt is in.

Clients gebruiken beheerpunten lokale eerste (plaats 3), externe tweede (locatie 2) en terugval (locatie 1). 

Wanneer een client vijf fouten in 10 minuten ontvangt en om te communiceren met een beheerpunt in de huidige grensgroep is mislukt, probeert het contact maken met een beheerpunt in een neighbor of de groep site standaard grens. Als het beheerpunt in de huidige grensgroep later weer online wordt gezet, wordt de client naar het lokale beheerpunt geretourneerd op de volgende vernieuwingscyclus. De vernieuwingscyclus is 24 uur, of wanneer de Configuration Manager-agent-service opnieuw wordt gestart.




## <a name="preferred-management-points"></a>Voorkeursbeheerpunten

 > [!Note]
 > Het gedrag van deze hiërarchie-instelling, **Clients gebruiken liever beheerpunten die zijn opgegeven in grensgroepen**, worden wijzigingen vanaf versie 1802. Wanneer u deze instelling inschakelt, gebruikt Configuration Manager de functionaliteit van de groep grens voor het toegewezen beheerpunt. Zie voor meer informatie [beheerpunten](#management-points). 

 Met voorkeursbeheerpunten kunnen clients een beheerpunt identificeren dat is gekoppeld aan de huidige netwerklocatie (grens).  

-   Een client probeert via een voorkeursbeheerpunt van de toegewezen site voordat u een niet is geconfigureerd als voorkeur van de toegewezen site.  
-   Voor het gebruik van deze optie inschakelen **Clients gebruiken liever beheerpunten die zijn opgegeven in grensgroepen** in **hiërarchie-instellingen**. Configureer vervolgens grensgroepen op afzonderlijke primaire sites. De beheerpunten die gekoppeld aan deze grensgroep gekoppelde grenzen worden moeten bevatten.
-   Wanneer u voorkeursbeheerpunten configureren en een client de lijst van beheerpunten ordent, plaatst de client de voorkeursbeheerpunten boven aan de lijst. Deze lijst bevat alle beheerpunten van de client toegewezen site.  

> [!NOTE]  
>  Roaming client betekent dat de netwerklocaties verandert. Bijvoorbeeld, wanneer een laptop op een externe locatie. Wanneer een client roamt, kan hij gebruikmaken van een beheerpunt of proxy beheerpunt van de lokale site op de nieuwe locatie voordat u probeert een server van de toegewezen site gebruiken. Deze lijst met servers van de toegewezen site bevat de voorkeursbeheerpunten. Zie voor meer informatie [begrijpen hoe clients siteresources en -services vinden](../../../../core/plan-design/hierarchy/understand-how-clients-find-site-resources-and-services.md).  

## <a name="overlapping-boundaries"></a>Overlappende grenzen  
 Configuration Manager ondersteunt configuraties met overlappende grenzen voor inhoudslocatie. Wanneer de clientnetwerklocatie behoort tot meerdere grensgroepen:

-   Wanneer een client inhoud opvraagt, stuurt Configuration Manager de client een lijst van alle distributiepunten die de inhoud bevatten.  
-   Als een server te verzenden of ontvangen van statusmigratie-informatie voor een client wordt aangevraagd, verzendt Configuration Manager de client een lijst met alle statusmigratiepunten die zijn gekoppeld aan een grensgroep die de huidige netwerklocatie van de client bevat.  

De client kan door dit gedrag de dichtstbijzijnde server selecteren vanwaar inhoud of statusmigratie-informatie wordt overgedragen.  



## <a name="example-of-using-boundary-groups"></a>Voorbeeld van het gebruik van grensgroepen
Het volgende voorbeeld wordt een client zoeken naar inhoud vanaf een distributiepunt. In dit voorbeeld kan worden toegepast op andere sitesysteemrollen die gebruikmaken van grensgroepen. Houd er rekening mee dat software-updatepunten geen ondersteuning voor configuratie van terugvallen op een groep neighbor en gebruik altijd een periode van 120 minuten.

U maakt drie grensgroepen die geen grenzen of sitesysteemservers delen:
-   Groep BG_A met distributiepunten DP_A1 en DP_A2 die zijn gekoppeld aan de groep
-   Groep BG_B met distributiepunten DP_B1 en DP_B2 die zijn gekoppeld aan de groep
-   Groep BG_C met distributiepunten DP_C1 en DP_C2 die zijn gekoppeld aan de groep

Voeg de netwerklocaties van uw clients als grenzen toe aan alleen de BG_A grensgroep. Relatie tussen de grensgroep aan de andere twee grensgroepen configureert:
-   Distributiepunten voor het eerst configureert *neighbor* groep (BG_B) moet worden gebruikt na 10 minuten. Deze groep bevat distributiepunten DP_B1 en DP_B2. Beide zijn goed verbonden zijn met de eerste groepen grenslocaties.
-   Configureren van de tweede *neighbor* groep (BG_C) moet worden gebruikt na 20 minuten. Deze groep bevat distributiepunten DP_C1 en DP_C2. Beide zijn via een WAN van de andere twee grensgroepen.
-   Ook toevoegen aan de grensgroep sites standaard site een ander distributiepunt dat zich op de siteserver. Deze server is de locatie van de minste voorkeur inhoudsbron, maar bevindt centraal aan uw grensgroepen.

    Voorbeeld van grensgroepen en terugval tijden:

     ![Voorbeeld van grensgroepen en de tijdstippen voor terugval](media/BG_Fallback.png)


Met deze configuratie:
-   De client begint met zoeken naar inhoud vanaf distributiepunten in de *huidige* grensgroep (BG_A). Deze twee minuten elk distributiepunt wordt gezocht en wordt vervolgens het volgende distributiepunt in de grensgroep. De groep clients met geldige inhoudsbron locaties bevat DP_A1 en DP_A2.
-   Als de client niet kan vinden van inhoud van de *huidige* grensgroep na 10 minuten zoekt, toegevoegd de distributiepunten van de grensgroep BG_B in de zoekopdracht. Vervolgens gaat door om te zoeken naar inhoud vanaf een distributiepunt in de gecombineerde servergroep. Deze groep bevat nu servers uit de BG_A en de BG_B grensgroepen. De client blijft contact op met elk distributiepunt voor twee minuten en vervolgens overschakelen naar de volgende server in de groep. De groep clients met geldige inhoudsbron locaties bevat DP_A1, DP_A2 DP_B1 en DP_B2.
-   Na een extra 10 minuten (totaal 20 minuten) als de client nog steeds niet een distributiepunt met inhoud gevonden is, deze wordt uitgebreid zijn groep met de beschikbare servers uit de tweede *neighbor* groeperen, grensgroep BG_C. De client heeft nu zes distributiepunten om te zoeken (DP_A1, DP_A2 DP_B2, DP_B2, DP_C1 en DP_C2). Wijzigen van elke twee minuten totdat deze inhoud is gevonden in een nieuw distributiepunt wordt herhaald.
-   Als de client niet voor inhoud na een totaal van 120 minuten gevonden is, vallen terug om op te nemen de *sitegrensgroep standaard* als onderdeel van de verder te zoeken. De groep bevat nu alle distributiepunten van de drie geconfigureerde grensgroepen en het laatste distributiepunt dat zich op de siteserver bevindt. De client blijft vervolgens de zoekactie voor inhoud, distributiepunten voor het wijzigen van elke twee minuten tot inhoud is gevonden.

U configureert de andere neighbor-groepen zijn beschikbaar op verschillende tijdstippen, beheren u wanneer specifieke distributiepunten worden toegevoegd als een bronlocatie voor inhoud. Gebruikt de client terugvallen op de standaard sitegrensgroep als veiligheidsnet voor inhoud die niet beschikbaar is van een andere locatie.





<!--
### Update existing boundary groups to the new model
When you update to version prior to 1610, the following configurations are automatically made. This behavior ensures your current fallback behavior remains available until you configure new boundary groups and relationships.

-   Each primary site creates a default site boundary group named ***Default-Site-Boundary-Group&lt;sitecode>***.
  - The primary site adds to the *Default-Site-Boundary-Group&lt;sitecode>* boundary group any state migration points and distribution points configured to **Allow fallback source location for content**.
  - The site adds software update points to the *Default-Site-Boundary-Group&lt;sitecode>* boundary group.
-   The site makes a copy of each existing boundary group that includes a site server configured with a slow connection. The name of the new group is ***&lt;original boundary group name>-&lt;original boundary group ID>***:  
    -   Site systems that have a fast connection are left in the original boundary group.
    -   A copy of site systems (distribution points, management points) that have a slow connection are added to the copy of the boundary group. The original site systems configured as slow remain in their original boundary groups for backward compatibility, but are not used from those boundary groups.
    - This boundary group copy does not have boundaries associated with it. However, A fallback link is created between the original group and the new boundary group copy that has the fallback time set to zero.  


- **Specific to secondary sites:**
  - If a secondary site has at least one state migration point or distribution point enabled to **Allow fallback source location for content**, Configuration Manager creates a boundary group named ***Secondary-Site-Neighbor--Tmp&lt;Sitecode>***. 
  - All distribution points enabled to **Allow fallback source location for content** and state migration points are added to this secondary site boundary group.
  - A fallback link is created between the original boundary group and the newly created neighbor boundary group. The fallback time is set to zero.


 The following table identifies the new fallback behavior you can expect from the combination the original deployment settings and distribution point configurations:

Original deployment configuration for “Do not run program” in slow network  |Original distribution point configuration for “Allow client to use a fallback source location for content”  |New fallback behavior  
---------|---------|---------
Selected     |  Selected    |  **No fallback** - Only use the distribution points in current boundary group       
Selected     |  Not selected|  **No fallback** - Only use the distribution points in current boundary group       
Not selected |  Not selected|  **Fallback to neighbor** - Use the distribution points in current boundary group, and then add the distribution points from the neighbor boundary group. Unless an explicit link to the default site boundary group is configured, clients do not fallback to that group.    
Not selected | Selected     |   **Normal fallback** - Use distribution points in current boundary group, then servers from the neighbor and site default boundary groups

 All other deployment configurations result in **Normal fallback**.  
-->



## <a name="changes-from-prior-versions"></a>Wijzigingen van vorige versies
Hier volgen de belangrijkste wijzigingen in grensgroepen en hoe clients inhoud in Configuration Manager Current Branch vinden. Veel van deze wijzigingen en concepten werken samen.


-   Configuraties voor het snel of traag worden verwijderd: U configureert niet langer afzonderlijke distributiepunten worden snel of traag. In plaats daarvan elk sitesysteem die zijn gekoppeld aan een grensgroep wordt behandeld hetzelfde. Vanwege deze wijziging de **verwijzingen** tabblad van de eigenschappen van de grensgroep biedt geen ondersteuning voor de configuratie van snel of traag.
- Nieuwe standaard grensgroep op elke site: Elke primaire site heeft een nieuwe grensgroep standaard is met de naam ***-Site-grens-standaardgroep&lt;sitecode >***. Wanneer een client zich niet op een netwerklocatie die is toegewezen aan een grensgroep, gebruikt de sitesystemen die zijn gekoppeld aan de standaardgroep van de toegewezen site. Wilt u deze grensgroep gebruiken als ter vervanging van het concept van locatie terugvalinhoudlocatie.   
 -  **Alternatieve bronlocaties voor inhoud toestaan** wordt verwijderd: U configureert niet langer expliciet een distributiepunt moet worden gebruikt voor terugval. De opties voor het configureren van deze instelling worden verwijderd van de console.

    Daarnaast het resultaat van de instelling **clients met een terugvalbronlocatie voor inhoud toestaan** op een implementatie van het type voor toepassingen is gewijzigd. Deze instelling op een implementatietype kan een client de standaard sitegrensgroep gebruiken als bronlocatie voor inhoud.

 -  Grens groepen relaties: Elke grensgroep kan worden gekoppeld aan een of meer extra grensgroepen. Deze koppelingen vormen relaties die zijn geconfigureerd op het nieuwe grens groep tabblad Eigenschappen met de naam **relaties**:
    -   Elke grensgroep die een client rechtstreeks is gekoppeld, heet een **huidige** grensgroep.  
    -   Elke grensgroep een client kan gebruiken als gevolg van een koppeling tussen die client *huidige* grensgroep en een andere groep, heet een **neighbor** grensgroep.
    -  Op de **relaties** tabblad toevoegen grensgroepen om te gebruiken als een *neighbor* grensgroep. Ook een tijd in minuten voor terugval configureren. Als een client niet te zoeken naar inhoud vanaf een distributiepunt in de *huidige* groep deze tijd is wanneer de client begint met zoeken naar inhoud locaties van *neighbor* grensgroepen.

        Wanneer u toevoegen of wijzigen van de configuratie van een grensgroep, hebt u de mogelijkheid aan Adresblok fallback naar specifieke grensgroep uit de huidige groep die u configureert.

    Definieer expliciete koppelingen (koppelingen) uit een grensgroep met een andere voor het gebruik van de nieuwe configuratie. Configureer alle distributiepunten in de bijbehorende groep met de dezelfde periode in minuten. Wanneer een client niet kan vinden van een bron van de inhoud van de *huidige* grensgroep, de tijd die u configureert bepaalt wanneer deze om te zoeken naar bronnen uit de grensgroep neighbor begint.

    Naast de grensgroepen die expliciet configureren, heeft elke grensgroep een impliciete koppeling aan de standaardgroep voor de site-grens. Deze koppeling wordt na 120 minuten actief. De standaardgroep voor de grens van site wordt vervolgens een neighbor grensgroep. Dit gedrag kunt de clients gebruiken als inhoudsbron locaties de distributiepunten die zijn gekoppeld aan de grensgroep.

    Dit gedrag vervangt wat eerder werd aangeduid als terugval voor inhoud. Dit standaardgedrag van 120 minuten door expliciet koppelen van de grensgroep voor standaard site naar een *huidige* groep. Een specifieke tijd in minuten ingesteld of blokkeren van terugval volledig om te voorkomen dat het gebruik ervan.


-   Clients proberen inhoud op te halen van elk distributiepunt tot twee minuten: Wanneer een client zoekt naar een inhoudsbronlocatie, probeert het toegang krijgen tot elk distributiepunt voor twee minuten voordat u vervolgens probeert een ander distributiepunt. Dit gedrag is een wijziging ten opzichte van vorige versies waar clients heeft geprobeerd verbinding maken met een distributiepunt voor maximaal twee uur.

    - Het eerste distributiepunt clients willekeurig selecteren van de groep met beschikbare servers in de client *huidige* grensgroep (of groepen).

    - Na twee minuten als de client niet voor de inhoud gevonden is het verandert in een nieuw distributiepunt en probeert inhoud op te halen van die server. Dit proces wordt herhaald voor elke twee minuten totdat de client de inhoud wordt gevonden of de laatste server in de groep van toepassingen is bereikt.

    - Als een client kan geen geldige inhoudsbronlocatie van vinden de *huidige* voordat het de periode voor terugvallen bereikt de opslaggroep een *neighbor* grensgroep, de client voegt vervolgens de distributiepunten van die *neighbor* aan het einde van de huidige lijst. Vervolgens zoekt de uitgevouwen groep bronlocaties die de distributiepunten van beide grensgroepen bevat.

        > [!TIP]  
        > Wanneer u een expliciete koppeling te van de huidige grensgroep aan de standaardgroep voor de grens van site maken en een fallback-tijd die kleiner is dan de terugval tijd voor een koppeling naar een grensgroep neighbor definiëren, beginnen clients bronlocaties van de standaardsite zoeken grensgroep voordat de groep neighbor.

    - Wanneer de client niet kan inhoud op te halen van de laatste server in de groep, begint het proces opnieuw.


## <a name="procedures-for-boundary-groups"></a>Procedures voor grensgroepen

### <a name="to-create-a-boundary-group"></a>Een grensgroep maken  
1.  Klik in de Configuration Manager-console op **beheer** > **Hiërarchieconfiguratie** >  **Grensgroepen**.  

2.  Klik op het tabblad **Start** in de groep **Maken** op **Grensgroep maken**.  

3.  In de **Grensgroep maken** selecteert u de **algemene** tabblad en geef een **naam** voor deze grensgroep.  

4.  Klik op **OK** om de nieuwe grensgroep op te slaan.  


### <a name="to-configure-a-boundary-group"></a>Een grensgroep configureren  
 1.  Klik in de Configuration Manager-console op **beheer** > **Hiërarchieconfiguratie** >  **Grensgroepen**.  

 2.  Selecteer de grensgroep die u wilt wijzigen.  

 3.  Klik op het tabblad **Start** in de groep **Eigenschappen** op **Eigenschappen**.  

 4.  Selecteer in het dialoogvenster **Eigenschappen** voor de grensgroep het tabblad **Algemeen** om de grenzen te wijzigen die lid zijn van deze grensgroep:  

     -   Als u grenzen wilt toevoegen, klikt u op **Toevoegen**, schakelt u het selectievakje voor een of meer grenzen in en klikt u op **OK**.  

     -   Als u grenzen wilt verwijderen, selecteert u de grens en klikt u op **Verwijderen**.  

 5.  Selecteer het tabblad **Verwijzingen** om de configuratie van sitetoewijzingen en de bijbehorende sitesysteemserver te wijzigen:  

     -   Als u deze grensgroep voor gebruik door clients voor sitetoewijzing, schakelt **deze grensgroep gebruiken voor sitetoewijzing**. Selecteer een site in de **toegewezen site** vervolgkeuzelijst.  

     -   Configureren welke beschikbare sitesysteemservers worden gekoppeld aan deze grensgroep:  

     1.  Klik op **Toevoegen**en schakel het selectievakje voor een of meer servers in. De servers worden als gekoppelde sitesysteemservers toegevoegd aan deze grensgroep. Alleen servers waarop ondersteunde sitesysteemrollen zijn geïnstalleerd, zijn beschikbaar.  

         > [!NOTE]  
         >  U kunt een combinatie van beschikbare sitesystemen van alle sites in de hiërarchie selecteren. Geselecteerde sitesystemen worden weergegeven op het tabblad **Sitesystemen** in de eigenschappen van elke grens die deel uitmaakt van deze grensgroep.  

     2.  Als u een server uit deze grensgroep wilt verwijderen, selecteert u de server en klikt u op **Verwijderen**.  

         > [!NOTE]  
         >  Als u wilt stoppen met gebruik van deze grensgroep voor het koppelen van sitesystemen, moet u alle servers die worden vermeld als gekoppelde sitesysteemservers verwijderen.  

 6.  Terugval om gedrag te configureren, selecteert u de **relaties** tabblad:  

     - Klik op **toevoegen**, en selecteer vervolgens de grensgroep die u wilt configureren.

     - Een fallback tijd instellen voor distributiepunten. Na deze periode, in de grensgroep die u relaties configureert, kunnen clients worden om te beginnen met zoeken naar inhoud uit de distributiepunten van de grensgroep die u wilt toevoegen.

     - Om te voorkomen dat terugval naar een specifieke grensgroep, met inbegrip van de *standaard sitegrensgroep* die standaard is geconfigureerd, selecteert u de grensgroep en klikt u vervolgens het selectievakje in voor **nooit terugval**.   

 7.  Klik op **OK** om de eigenschappen van de grensgroep te sluiten en de configuratie op te slaan.  

#### <a name="to-associate-a-site-system-server-with-a-boundary-group"></a>Een sitesysteemserver koppelen aan een grensgroep  
 1.  Klik in de Configuration Manager-console op **beheer** > **Hiërarchieconfiguratie** >  **Grensgroepen**.  

 2.  Selecteer de grensgroep die u wilt wijzigen.  

 3.  Klik op het tabblad **Start** in de groep **Eigenschappen** op **Eigenschappen**.  

 4.  In het dialoogvenster **Eigenschappen** voor de grensgroep selecteert u het tabblad **Verwijzingen** .  

 5.  Onder **sitesysteemservers selecteren**, klikt u op **toevoegen**. Selecteer de sitesysteemservers om te koppelen aan deze grensgroep en klik vervolgens op **OK**.  

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
