---
title: Gegevensoverdracht
titleSuffix: Configuration Manager
description: Meer informatie over hoe worden gegevens in Configuration Manager worden verplaatst tussen sites en hoe u de overdracht van de gegevens in uw netwerk kunt beheren.
ms.custom: na
ms.date: 10/06/2016
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: dc526e8d-fac3-4bb5-b206-03ad29b0ae11
caps.latest.revision: "12"
author: Brenduns
ms.author: brenduns
manager: angrobe
ms.openlocfilehash: 29e15b9ebe01e9e266df24267bf402e3d07de095
ms.sourcegitcommit: c236214b2fcc13dae7bad96d7fb33f692868191d
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/12/2017
---
# <a name="data-transfers-between-sites-in-system-center-configuration-manager"></a>Gegevensoverdracht tussen sites in System Center Configuration Manager

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*

System Center Configuration Manager gebruikt **bestandsgebaseerde replicatie** en **databasereplicatie** om over te dragen van verschillende typen informatie tussen sites. Meer informatie over hoe worden gegevens in Configuration Manager worden verplaatst tussen sites en hoe u de overdracht van gegevens in uw netwerk kunt beheren.  


## <a name="bkmk_fileroute"></a> File-based replication  
Configuration Manager gebruikt bestandsgebaseerde replicatie voor het overbrengen van gegevens op basis van bestanden tussen sites in uw hiërarchie. Deze gegevens omvatten toepassingen en pakketten die u wilt distribueren naar distributiepunten in onderliggende sites en onverwerkte detectiegegevensrecords die naar bovenliggende sites overgedragen en vervolgens wordt verwerkt.  

Bestandsgebaseerde communicatie tussen sites maakt gebruik de **Server Message Block** protocol op TCP/IP-poort 445 (SMB). U kunt bandbreedte bandbreedtebeperking en pulse-modus voor het beheren van de hoeveelheid gegevens die via het netwerk wordt overgedragen opgeven en kunt u schema's om te bepalen wanneer gegevens worden verzonden via het netwerk.  

### <a name="bkmk_routes"></a> Bestandsreplicatieroutes  
De volgende informatie kunt u instellen en bestandsreplicatieroutes gebruiken.  

#### <a name="file-replication-route"></a>Route voor bestandsreplicatie

Elke bestandsreplicatieroute identificeert een doelsite waarnaar bestandsgebaseerde gegevens kunnen worden overgedragen. Elke site ondersteunt één bestandsreplicatieroute naar een specifieke doelsite.  

U kunt de volgende instellingen voor de routes voor bestandsreplicatie wijzigen:  

-  **Account voor bestandsreplicatie**. Dit account maakt verbinding met de doelsite en schrijft gegevens naar die site **SMS_Site** delen. Gegevens die naar deze share worden geschreven, worden verwerkt door de ontvangende site. Standaard, wanneer een site wordt toegevoegd aan de hiërarchie, wijst Configuration Manager het computeraccount van de siteserver van de nieuwe site als deze sites bestandsreplicatie-Account. Dit account wordt vervolgens toegevoegd aan de doelsite **SMS_SiteToSiteConnection_&lt;Sitecode\>**  groep, een lokale groep op de computer die toegang tot de SMS_Site-share verleent. U kunt dit account zodanig wijzigen, dat dit een Windows gebruikersaccount is. Als u het account wijzigt, zorg ervoor dat u de nieuwe account toevoegt aan de doelsite **SMS_SiteToSiteConnection_&lt;Sitecode\>**  groep.  

    > [!NOTE]  
    >  Secundaire sites gebruiken altijd het computeraccount van de secundaire siteserver als het **Account voor bestandsreplicatie**.  

-  **Planning**. U kunt het schema voor elke bestandsreplicatieroute naar het type gegevens en de tijd waarop gegevens naar de doelsite kunnen worden overgedragen, beperkt instellen.  
-  **Frequentielimieten**. U kunt opgeven voor elke bestandsreplicatieroute om te bepalen van de netwerkbandbreedte die wordt gebruikt wanneer de site gegevens naar de doelsite overdraagt snelheidslimieten:  

    -  Gebruik **Pulsmodus** om de grootte van de gegevensblokken die naar de doelsite worden verzonden, te specificeren. U kunt ook een vertraging tussen het verzenden van de afzonderlijke gegevensblokken opgeven. Gebruik deze optie wanneer u gegevens via een netwerkverbinding met zeer lage bandbreedte naar de doelsite verzendt. U kunt bijvoorbeeld beperkingen instellen om elke vijf seconden 1 kB aan gegevens te verzenden, maar niet elke drie seconden, ongeacht de snelheid van de koppeling of het gebruik ervan op een bepaald moment.
    -  Gebruik **Beperkt tot maximale overdrachtssnelheid per uur** om een site gegevens te laten sturen naar een doelsite door alleen het percentage tijd te gebruiken dat u opgeeft. Als u deze optie gebruikt, wordt Configuration Manager geeft niet de beschikbare bandbreedte van het netwerk, maar verdeelt het de tijd die het gegevens in stukken tijd verzenden kan. Gegevens worden vervolgens verzonden in een kort tijdsblok, gevolgd door tijdsblokken waarin geen gegevens worden verzonden. Bijvoorbeeld, als de maximale snelheid wordt ingesteld op **50%**, Configuration Manager brengt gegevens over een bepaalde tijd, gevolgd door een even lange periode waarin geen gegevens worden verzonden. De werkelijke hoeveelheid gegevens of de grootte van het gegevensblok, wordt niet beheerd. Alleen de hoeveelheid tijd waarin gegevens worden verzonden, wordt beheerd.  

        > [!CAUTION]  
        > Standaard kan een site maximaal drie **gelijktijdige verzendingen** gebruiken om gegevens naar een doelsite over te dragen. Wanneer u snelheidslimieten voor een bestandsreplicatieroute inschakelt, zijn de **gelijktijdige verzendingen** voor het verzenden van gegevens naar die site beperkt tot één. Dit geldt ook wanneer de **Limiet beschikbare bandbreedte (%)** is ingesteld op **100%**. Bijvoorbeeld, als u de standaardinstellingen voor de afzender gebruikt, reduceert dit de overdrachtssnelheid naar de doelsite tot één derde van de standaardcapaciteit.  

-  U kunt een bestandsreplicatieroute tussen twee secundaire sites configureren om bestandsgebaseerde content tussen die sites te routeren.  

Voor het beheren van een route voor bestandsreplicatie, in de **beheer** werkruimte, vouw de **Hiërarchieconfiguratie** knooppunt en selecteer vervolgens **bestandsreplicatie**.  

#### <a name="sender"></a>Afzender

Elke site heeft één afzender. De afzender beheert de netwerkverbinding van één site met een doelsite, en kan verbindingen naar meerdere sites op hetzelfde moment tot stand brengen. Om verbinding met een site te maken, gebruikt de afzender de bestandsreplicatieroute naar de site om het account te identificeren dat gebruikt wordt om de netwerkverbinding tot stand te brengen. De afzender gebruikt dit account ook om gegevens te schrijven naar de SMS_Site-share van de doelsite.  

Standaard schrijft de afzender gegevens naar een doelsite door meerdere **gelijktijdige verzendingen**te gebruiken, meestal thread genoemd. Elke gelijktijdige verzending, of thread, kan een verschillend bestandsgebaseerd object naar de doelsite overdragen. Wanneer de afzender begint met het verzenden van een object, gaat de afzender standaard door met het schrijven van gegevensblokken voor dat object totdat het gehele object verzonden is. Nadat alle gegevens voor het object verzonden zijn, kan een nieuw object beginnen met verzenden op die thread.  

U kunt de volgende instellingen voor een afzender wijzigen:  

-  **Maximum aantal gelijktijdige verzendingen**. Elke site maakt standaard gebruik van vijf gelijktijdige verzendingen, waarvan er drie beschikbaar zijn voor gebruik wanneer het gegevens naar eender welke één bestemmingssite verzendt. Als u dit aantal verhoogt, kunt u de verwerkingscapaciteit van gegevens tussen sites verhogen omdat Configuration Manager meer bestanden tegelijkertijd kunnen worden overgedragen. Door dit aantal te verhogen wordt de vraag voor netwerkbandbreedte tussen sites ook verhoogd.  

-  **Instellingen voor opnieuw proberen**. Standaard elke site opnieuw probeert een probleemverbinding tweemaal met een vertraging van één minuut tussen de verbindingspogingen. U kunt het aantal verbindingspogingen is de site doet, wijzigen en hoe lang er moet worden gewacht tussen pogingen.  

Voor het beheren van de verzender voor een site in de **beheer** werkruimte, vouw de **siteconfiguratie** knooppunt, selecteer de **Sites** knooppunt en selecteer vervolgens **eigenschappen** voor de site die u wilt beheren. Selecteer de **afzender** tabblad om de instellingen van de afzender te wijzigen.  

## <a name="bkmk_dbrep"></a> Database replication  
Configuration Manager-databasereplicatie gebruikt SQL Server om gegevens te dragen en wijzigingen die zijn aangebracht in een sitedatabase met de informatie opgeslagen in de database op andere sites in de hiërarchie. Houd rekening met het volgende over databasereplicatie:

-  Alle sites delen dezelfde informatie.  
-  Wanneer u een site in een hiërarchie installeert, wordt databasereplicatie automatisch geconfigureerd tussen de nieuwe site en de aangeduide bovenliggende site.  
-  Als de site-installatie is voltooid, wordt databasereplicatie automatisch gestart.  

Wanneer u een nieuwe site aan een hiërarchie toevoegt, maakt Configuration Manager een algemene database op de nieuwe site. Vervolgens de bovenliggende site een momentopname van de relevante gegevens in de database maakt en vervolgens de momentopname overbrengt naar de nieuwe site door replicatie op basis van een bestand. De nieuwe site gebruikt dan de SQL Server-programma bulksgewijs kopiëren (BCP) om te laden van de informatie in de lokale kopie ervan van de Configuration Manager-database. Nadat de momentopname is geladen, voert elke site databasereplicatie uit met de andere site.  

Configuration Manager gebruikt om gegevens te repliceren tussen sites, haar eigen databasereplicatieservice. De databasereplicatieservice gebruikt SQL Server-bijhouden om te controleren van de lokale sitedatabase voor wijzigingen en worden de wijzigingen naar andere sites gerepliceerd met behulp van SQL Server Service Broker (SSB). Dit proces maakt standaard gebruik van TCP/IP-poort 4022.  

Configuration Manager groepeert gegevens die door databasereplicatie in verschillende replicatiegroepen zijn gerepliceerd. Houd rekening met de volgende replicatiegroepen:

-  Elke replicatiegroep heeft een afzonderlijk, vast replicatieschema dat bepaalt hoe vaak wijzigingen aan de gegevens in de groep worden gerepliceerd naar andere sites.  

     Een wijziging in een op rollen gebaseerde beheerconfiguratie repliceert bijvoorbeeld snel naar andere sites om ervoor te zorgen dat deze wijzigingen zo snel mogelijk worden doorgevoerd. Ondertussen repliceert een configuratiewijziging van lagere prioriteit, zoals een aanvraag voor het installeren van een nieuwe secundaire site, met minder urgentie. Het kan enkele minuten duren voordat een nieuwe site-aanvraag naar de primaire bestemmingssite bereikt.  

-   U kunt de volgende instellingen voor databasereplicatie wijzigen:  

    -  **Koppelingen voor databasereplicatie**. Bepalen wanneer specifiek verkeer over het netwerk gaat.  
    -  **Gedistribueerde weergaven**. Instellingen voor replicatiekoppelingen waarmee aanvragen die aan een centrale beheersite voor geselecteerde sitegegevens zijn gedaan toegang die sitegegevens rechtstreeks uit de database op een onderliggende primaire site tot wijzigen.  
    -  **Planningen**. Geef op wanneer een replicatiekoppeling wordt gebruikt en wanneer verschillende types sitegegevens worden gerepliceerd.  
    -  **Samenvatting**. Instellingen wijzigen voor gegevenssamenvatting over het netwerkverkeer dat koppelingen voor databasereplicatie passeert. Samenvatting gebeurt elke 15 minuten, standaard en wordt gebruikt in rapporten voor databasereplicatie.  
    -  **Drempelwaarden voor databasereplicatie**. Gedefinieerd wanneer koppelingen worden gerapporteerd als gedegradeerd of mislukt. U kunt ook configureren wanneer Configuration Manager waarschuwingen geeft over replicatiekoppelingen die een gedegradeerde of mislukte status.  

Configuration Manager deelt de gegevens die het repliceert door databasereplicatie als hetzij **globale gegevens** of **sitegegevens**. Wanneer databasereplicatie plaatsvindt, worden wijzigingen aan algemene gegevens en sitegegevens overgebracht over de databasereplicatiekoppeling. Globale gegevens kunnen repliceren naar een bovenliggende of onderliggende site. Sitegegevens repliceert enkel naar een bovenliggende site. Een derde gegevenstype lokale gegevens wordt niet gerepliceerd naar andere sites. Lokale gegevens is informatie die niet is vereist voor andere sites. Houd rekening met de volgende gegevenstypen:  

-  **Globale gegevens**. Algemene gegevens verwijst naar objecten beheerder zijn gemaakt die naar alle sites in de gehele hiërarchie repliceren, hoewel secundaire sites alleen een subset van globale gegevens, als algemene proxygegevens ontvangen. Algemene gegevens omvatten software-implementaties, software-updates, verzamelingdefinities en op rollen gebaseerde beheerbeveiligingsbereiken. Beheerders kunnen algemene gegevens aanmaken op centrale beheersites en primaire sites.  
-  **Sitegegevens**. Sitegegevens verwijzen naar operationele informatie die primaire site van Configuration Manager en de clients die rapport naar primaire sites maken. Sitegegevens worden gerepliceerd naar de centrale beheersite, maar niet naar andere primaire sites. Sitegegevens omvat hardware-inventarisgegevens, statusberichten, waarschuwingen en de resultaten van query's gebaseerde verzamelingen. Sitegegevens zijn alleen zichtbaar op de centrale beheersite en op de primaire site waarvan de gegevens afkomstig is. Sitegegevens kunnen enkel worden gewijzigd op de primaire site waar ze werden gemaakt.  

     Alle sitegegevens worden gerepliceerd naar de centrale beheersite. De centrale beheersite voert beheer en rapportage voor de hele sitehiërarchie.  

De volgende secties detailleren de instellingen die u wijzigen kunt voor het beheren van databasereplicatie.  

### <a name="bkmk_Dblinks"></a> Koppelingen voor databasereplicatie  
Wanneer u een nieuwe site in een hiërarchie installeert, maakt Configuration Manager automatisch een databasereplicatiekoppeling tussen de bovenliggende site en de nieuwe site. Een enkele koppeling wordt gemaakt om de twee sites verbinding te maken.  

U kunt instellingen voor elke databasereplicatiekoppeling om te bepalen van de overdracht van gegevens via de replicatiekoppeling wijzigen. Elke replicatiekoppeling ondersteunt afzonderlijke configuraties. De besturingselementen voor databasereplicatiekoppelingen omvatten het volgende:  

-  Stop de replicatie van geselecteerde sitegegevens van een primaire site naar de centrale beheersite, zodat de centrale beheersite toegang deze gegevens rechtstreeks vanuit de database van de primaire site tot.  
-  Plannen van geselecteerde sitegegevens overzetten van een onderliggende primaire site naar de centrale beheersite.
-  Definieer de instellingen die bepalen wanneer een databasereplicatiekoppeling een gedegradeerde status heeft of is mislukt.
-  Geef op wanneer waarschuwingen worden gegeven voor een mislukte replicatiekoppeling.
-  Geef op hoe vaak Configuration Manager bevat een overzicht van gegevens over het replicatieverkeer dat de replicatiekoppeling gebruikt. Deze gegevens worden in rapporten gebruikt.

Voor het configureren van een databasereplicatiekoppeling in de Configuration Manager-console op de **databasereplicatie** knooppunt, bewerk de eigenschappen voor de koppeling. Dit knooppunt verschijnt in de **bewaking** werkruimte en in de **beheer** werkruimte op het **Hiërarchieconfiguratie** knooppunt. U kunt een replicatiekoppeling bewerken vanuit hetzij de bovenliggende site hetzij de onderliggende site van de replicatiekoppeling.  

> [!TIP]  
> U kunt databasereplicatiekoppelingen bewerken vanuit het knooppunt **Databasereplicatie** in beide werkruimten. Wanneer u echter gebruiken de **databasereplicatie** knooppunt in de **bewaking** werkruimte u ook kunt de status van databasereplicatie voor replicatiekoppelingen bekijken en het hulpprogramma Replication Link Analyzer openen om u te helpen bij het onderzoeken van problemen met databasereplicatie.  

Zie [Besturingselementen voor de replicatie van sitedatabases](#BKMK_DBRepControls)voor meer informatie over de configuratie van replicatiekoppelingen. Zie voor meer informatie over het controleren van replicatie [database databasereplicatiekoppelingen en de replicatiestatus replicatiestatus controleren](../../../core/servers/manage/monitor-hierarchy-and-replication-infrastructure.md#BKMK_MonitorRepLinksAndStatuss) in de [hiërarchie- en replicatie-infrastructuur bewaken in System Center Configuration Manager](../../../core/servers/manage/monitor-hierarchy-and-replication-infrastructure.md) onderwerp.  

Gebruik de informatie in de volgende secties om te plannen voor databasereplicatiekoppelingen.  

### <a name="bkmk_distviews"></a> Gedistribueerde weergaven  
Door middel van gedistribueerde weergaven geselecteerd die zijn ingediend op een centrale beheersite voor toegang tot de gegevens van de site sitegegevens rechtstreeks uit de database op een onderliggende primaire site. De rechtstreekse toegang vervangt de noodzaak die om sitegegevens te repliceren van de primaire site naar de centrale beheersite. Omdat elke replicatiekoppeling onafhankelijk is van andere replicatiekoppelingen, kunt u gedistribueerde weergaven op enkel de replicatiekoppelingen die u kiest. U gedistribueerde weergaven tussen een primaire site en een secundaire site niet gebruiken.  

Gedistribueerde weergaven kunnen de volgende voordelen bieden:  

-  Verminderen de CPU-belasting om databasewijzigingen op de centrale beheersite en primaire sites te verwerken
-  Verklein de hoeveelheid gegevens die worden verstuurd via het netwerk naar de centrale beheersite
-  De prestaties van de SQL server die als host fungeert voor de centrale beheersite database verbeteren
-  Ze verminderen de schijfruimte die wordt gebruikt door de database op de centrale beheersite

Overweeg het gebruik van gedistribueerde weergaven wanneer een primaire site dicht in de centrale beheersite op het netwerk is en de twee sites steeds zijn ingeschakeld en steeds zijn verbonden. Dit is omdat gedistribueerde weergaven de replicatie van de geselecteerde gegevens tussen de sites met rechtstreekse verbindingen tussen de SQL-servers op elke site vervangen. Een rechtstreekse verbinding wordt gemaakt telkens die een aanvraag voor deze gegevens wordt gedaan aan de centrale beheersite. Aanvragen voor gegevens die u voor gedistribueerde weergaven inschakelt mogelijk worden gewoonlijk gedaan wanneer u rapporten of query's uitvoert wanneer u informatie bekijken in Resource Explorer en door verzamelingevaluatie voor verzamelingen die regels omvatten die zijn gebaseerd op de sitegegevens.  

Gedistribueerde weergaven zijn standaard uitgeschakeld voor elke replicatiekoppeling. Wanneer u gedistribueerde weergaven voor een replicatiekoppeling inschakelt, selecteert u sitegegevens die niet wordt gerepliceerd naar de centrale beheersite over die koppeling. De centrale beheersite heeft toegang tot deze gegevens rechtstreeks vanuit de database van de onderliggende primaire site die de koppeling deelt. U kunt de volgende types van sitegegevens voor gedistribueerde weergaven configureren:  

-  Hardware-inventarisgegevens van clients
-  Software-inventarisatie en licentiecontrolegegevens van clients
-  Statusberichten van clients, de primaire site en alle secundaire sites

Werking zijn gedistribueerde weergaven onzichtbaar voor een gebruiker met beheerdersrechten die gegevens in de Configuration Manager-console of in rapporten. Wanneer een aanvraag wordt gedaan voor gegevens die zijn ingeschakeld voor gedistribueerde weergaven, heeft de SQL-server waarop de database voor de centrale beheersite rechtstreeks toegang tot de SQL server van de onderliggende primaire site de informatie op te halen. Bijvoorbeeld, gebruik van een Configuration Manager-console op de centrale beheersite om informatie te vragen over hardware-inventaris van twee sites, en slechts één site hardware-inventaris heeft ingeschakeld voor een gedistribueerde weergave. De inventarisinformatie voor clients van de site die niet is geconfigureerd voor gedistribueerde weergaven, wordt opgehaald uit de database op de centrale beheersite. De Inventarisinformatie voor clients van de site die is geconfigureerd voor gedistribueerde weergaven wordt uit de database op de onderliggende primaire site geopend. Deze informatie verschijnt in de Configuration Manager-console of in een rapport zonder te identificeren van de bron.  

Zoals een replicatiekoppeling een type gegevens ingeschakeld voor gedistribueerde weergaven, repliceert de onderliggende primaire site de gegevens niet naar de centrale beheersite. Zodra u gedistribueerde weergaven voor een type gegevens, de onderliggende primaire uitschakelt site de hervat de replicatie van de gegevens naar de centrale beheersite als onderdeel van de normale gegevensreplicatie. Echter, voordat deze gegevens beschikbaar op de centrale beheersite zijn, de replicatiegroepen die deze gegevens moeten opnieuw worden geïnitialiseerd tussen de primaire site en de centrale beheersite. Zo ook, nadat u een primaire site die gedistribueerde weergaven ingeschakeld heeft verwijderd, de centrale beheersite moet voltooien herinitialisatie van de gegevens voordat u toegang hebt tot gegevens die waren ingeschakeld voor gedistribueerde weergaven op de centrale beheersite.  

> [!IMPORTANT]  
> Wanneer u gedistribueerde weergaven gebruikt op eender welke replicatiekoppeling in de sitehiërarchie gebruikt, moet u gedistribueerde weergaven voor alle replicatiekoppelingen uitschakelen voordat u een primaire site verwijdert. Zie [Een primaire site verwijderen die is geconfigureerd met gedistribueerde weergaven](../../../core/servers/deploy/install/uninstall-sites-and-hierarchies.md#BKMK_UninstallPrimaryDistViews) voor meer informatie.  

#### <a name="prerequisites-and-limitations-for-distributed-views"></a>Vereisten en beperkingen voor gedistribueerde weergaven  

-  Hier kunt u gedistribueerde weergaven alleen op replicatiekoppelingen tussen een centrale beheersite en een primaire site.
- De centrale beheersite moet een Enterprise-editie van SQL Server gebruiken. De primaire site beschikt niet over deze vereiste.
-  Er kan slechts één instantie van de SMS-provider op de centrale beheersite worden geïnstalleerd en die instantie moet zijn geïnstalleerd op de sitedatabaseserver. Dit is vereist voor de ondersteuning van de Kerberos-verificatie vereist zodat de SQL server op de centrale beheersite toegang heeft tot de SQL server op de onderliggende primaire site. Er zijn geen beperkingen met betrekking tot de SMS-provider op de onderliggende primaire site.
-  Er kan slechts één SQL Server Reporting Services-punt op de centrale beheersite worden geïnstalleerd en dat punt moet zich op sitedatabaseserver bevinden. Dit is vereist voor de ondersteuning van de Kerberos-verificatie vereist voor het inschakelen van de SQL server op de centrale beheersite voor toegang tot de SQL server op de onderliggende primaire site.
-  De sitedatabase kan niet worden gehost op een SQL Server-cluster.
-  De sitedatabase kan niet worden gehost op een SQL Server Always On-beschikbaarheidsgroep.
-  Het computeraccount van de databaseserver van de centrale beheersite heeft leesrechten nodig voor de sitedatabase van de primaire site.

> [!IMPORTANT]  
>  Gedistribueerde weergaven en schema's voor wanneer gegeven kunnen repliceren zijn sluiten elkaar wederzijds uit instellingen voor een databasereplicatiekoppeling.  

### <a name="BKMK_schedules"></a> De overdracht van sitegegevens voor databasereplicatiekoppelingen plannen  
U kunt plannen wanneer een replicatiekoppeling wordt gebruikt en opgeven wanneer verschillende types sitegegevens worden gerepliceerd om u te helpen bij het controleren van de netwerkbandbreedte die wordt gebruikt om sitegegevens te repliceren van een onderliggende primaire site naar zijn centrale beheersite. U kunt controleren wanneer de primaire site statusberichten, inventarissen en metergegevens repliceert. Databasereplicatiekoppelingen van secundaire sites ondersteunen geen schema's voor sitegegevens. De overdracht van globale gegevens kan niet worden gepland.  

Wanneer u een schema van databasereplicatiekoppelingen configureert, kunt u de overdracht van geselecteerde sitegegevens vanaf de primaire site naar de centrale beheersite beperken, en kunt u de verschillende tijdstippen configureren waarop de verschillende typen sitegegevens moeten worden gerepliceerd.  

> [!IMPORTANT]  
> Gedistribueerde weergaven en schema's voor wanneer gegeven kunnen repliceren, zijn onderling exclusieve configuraties voor een databasereplicatiekoppeling.  

### <a name="BKMK_SummarizeDBReplication"></a> Samenvatting van het databasereplicatieverkeer  
Elke site wordt periodiek een gegevensoverzicht gegevens over het netwerkverkeer dat voor de site databasereplicatiekoppelingen. Samengevatte gegevens worden gebruikt in rapporten voor databasereplicatie. Beide sites op een replicatiekoppeling vatten het netwerkverkeer samen dat de replicatiekoppeling passeert. De samenvatting van gegevens wordt uitgevoerd door de SQL Server waarop de sitedatabase wordt gehost. Nadat de gegevens worden samengevat, wordt de informatie naar andere sites repliceert als globale gegevens.  

De samenvatting wordt standaard om de 15 minuten uitgevoerd. Als u wilt wijzigen van de samenvattingsfrequentie voor netwerkverkeer, in de eigenschappen van de databasereplicatiekoppeling bewerken de **samenvattingsinterval**. De samenvattingsfrequentie heeft invloed op de informatie die u in rapporten over databasereplicatie ziet. U kunt een interval van 5 minuten tot 60 minuten. Als u de samenvattingsfrequentie verhoogt, verhoogt u de verwerkingsbelasting op de SQL server op elke site op de replicatiekoppeling.  

### <a name="BKMK_DBRepThresholds"></a>Drempelwaarden voor databasereplicatie  
Drempelwaarden voor databasereplicatie definiëren wanneer de status van een databasereplicatiekoppeling als gedegradeerd of mislukt wordt gerapporteerd. Een koppeling is standaard ingesteld op gedegradeerde status wanneer een replicatiegroep is mislukt om de replicatie voor een periode van 12 opeenvolgende pogingen te voltooien. De koppeling is ingesteld op de status mislukt wanneer een replicatiegroep geen replicatie van 24 opeenvolgende pogingen kan.  

U kunt aangepaste waarden af te stemmen wanneer Configuration Manager een replicatiekoppeling als gedegradeerd of mislukt rapporteert. Aanpassen wanneer Configuration Manager-rapporten elke status voor uw databasereplicatiekoppelingen kan u helpen bij controleren van de status van de databasereplicatie voor uw databasereplicatiekoppelingen.  

Omdat het is mogelijk dat één of een aantal replicatiegroepen niet kunnen repliceren terwijl andere replicatiegroepen zijn gerepliceerd, dient u te controleren van de replicatiestatus van een replicatiekoppeling als eerst een gedegradeerde status rapporteert. Als er herhaalde vertragingen zijn voor specifieke replicatiegroepen en hun vertraging geen probleem veroorzaakt, of wanneer de netwerkkoppeling tussen sites een lage beschikbare bandbreedte heeft, overweeg dan om de waarden aan te passen voor een nieuwe poging voor de gedegradeerde of mislukte status van de koppeling. Als u het aantal nieuwe pogingen verhoogt voordat de koppeling wordt ingesteld op gedegradeerd of mislukt, kunt u valse waarschuwingen voor bekende problemen elimineren en de status van de koppeling nauwkeuriger te volgen.  

Houd ook rekening met de synchronisatie-interval voor replicatie voor elke replicatiegroep om te begrijpen hoe vaak de replicatie van die groep zich voordoet. Om weer te geven de **synchronisatie-Interval** voor replicatiegroepen, in de **bewaking** werkruimte op het **databasereplicatie** knooppunt, selecteer de **Replicatiedetails** tabblad van een replicatiekoppeling.  

Zie voor meer informatie over het bewaken van databasereplicatie, inclusief het weergeven van de replicatiestatus [database databasereplicatiekoppelingen en de replicatiestatus replicatiestatus controleren](../../../core/servers/manage/monitor-hierarchy-and-replication-infrastructure.md#BKMK_MonitorRepLinksAndStatuss) in de [hiërarchie- en replicatie-infrastructuur bewaken in System Center Configuration Manager](../../../core/servers/manage/monitor-hierarchy-and-replication-infrastructure.md) onderwerp.  

Zie voor meer informatie over het configureren van drempelwaarden voor databasereplicatie [Sitedatabasereplicatie](#BKMK_DBRepControls).  

## <a name="BKMK_DBRepControls"></a> Besturingselementen voor de sitedatabasereplicatie  
U kunt de instellingen voor de database van elke site om te bepalen van de netwerkbandbreedte die wordt gebruikt voor databasereplicatie kunt wijzigen. De instellingen gelden alleen voor de database van de site waarin u de instellingen configureren. De instellingen worden altijd gebruikt wanneer de site gegevens repliceert door databasereplicatie naar een andere site.  

Besturingselementen voor replicatie die u voor elke sitedatabase aanpassen kunt zijn:  

-  Wijzig de SSB-poort.  
-  Configureer de wachttijd voordat replicatiefouten activeren van de site om opnieuw te initialiseren van de kopie van de sitedatabase.  
-  Configureer een sitedatabase om de gegevens te comprimeren die deze repliceert door databasereplicatie. De gegevens worden alleen gecomprimeerd voor overdracht tussen sites en niet voor opslag in de sitedatabase van iedere site.  

De instellingen te wijzigen voor de besturingselementen voor replicatie voor de database van een site in de Configuration Manager-console op de **databasereplicatie** knooppunt, bewerk de eigenschappen van de sitedatabase. Dit knooppunt verschijnt in het knooppunt **Hiërarchieconfiguratie** in de werkruimte **Beheer** en ook in de werkruimte **Bewaking**. Als u wilt bewerken in de eigenschappen van de sitedatabase, selecteer de replicatiekoppeling tussen de sites en open vervolgens ofwel **eigenschappen bovenliggende Database** of **eigenschappen onderliggende Database**.  

> [!TIP]  
> U kunt de besturingselementen voor databasereplicatie configureren in het knooppunt **Databasereplicatie** in beide werkruimten. Wanneer u echter gebruiken de **databasereplicatie** knooppunt in de **bewaking** werkruimte u ook kunt zien die de status van databasereplicatie voor een replicatiekoppeling en het hulpprogramma Replication Link Analyzer openen om u te helpen bij het onderzoeken van replicatieproblemen.  
