---
title: Monitor voor replicatie
titleSuffix: Configuration Manager
description: Informatie over het bewaken van de infrastructuur en bewerkingen in Configuration Manager met behulp van de werkruimte bewaking in de console.
ms.custom: na
ms.date: 10/06/2016
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 3fab4d67-8d2a-45ce-8b06-471280102cf6
caps.latest.revision: "11"
caps.handback.revision: "0"
author: mestew
ms.author: mstewart
manager: angrobe
ms.openlocfilehash: 459a619d08a5d38c51301e2f6cff23a5d46a9464
ms.sourcegitcommit: daa080cf220835f157a23e8c8e2bd2781b869bb7
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/04/2017
---
# <a name="monitor-hierarchy-and-replication-infrastructure-in-system-center-configuration-manager"></a>Hiërarchie- en replicatie-infrastructuur bewaken in System Center Configuration Manager

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*

Voor het bewaken van de infrastructuur en bewerkingen in System Center Configuration Manager, gebruikt u de **bewaking** werkruimte in de Configuration Manager-console.  

> [!NOTE]  
>  De uitzondering op deze locatie is Migratie, die direct gecontroleerd wordt in knooppunt **Migratie** in de werkruimte **Beheer** . Voor meer informatie, zie [Bewerkingen voor de migratie naar System Center Configuration Manager](../../../core/migration/operations-for-migration.md).  

 Naast het gebruik van de Configuration Manager-console voor bewaking, kunt u de Configuration Manager-rapporten gebruiken of Configuration Manager-logboekbestanden voor Configuration Manager-onderdelen. Zie [Rapportage in System Center Configuration Manager](../../../core/servers/manage/reporting.md) voor meer informatie over rapporten. Zie [Logbestanden in System Center Configuration Manager](../../../core/plan-design/hierarchy/log-files.md) voor meer informatie over logbestanden.  

 Als u sites controleert, zoekt u tekens die duiden op problemen waarvoor u actie moet ondernemen. Bijvoorbeeld:  

-   Achterstand van bestanden op siteservers en sitesystemen.  

-   Statusberichten die wijzen op een fout of een probleem.  

-   Intrasitecommunicatie mislukt.  

-   Fout- en waarschuwingsberichten in het logboek voor systeemgebeurtenissen op servers.  

-   Fout- en waarschuwingsberichten in het foutenlogboek van Microsoft SQL Server.  

-   Sites of clients die lange tijd niet hebben gerapporteerd.  

-   Trage reactie van de SQL Server-database.  

-   Tekenen van hardwarefout.  

Als de controletaken tekenen van problemen vertonen, onderzoekt u om het risico op uitvallen een site te minimaliseren, de oorzaak van het probleem en herstelt u het zo snel mogelijk.  



##  <a name="BKMK_MonintorMgmtTasks"></a> Algemene beheertaken voor Configuration Manager bewaken  
 Configuration Manager voorziet ingevouwde bewaking in de Configuration Manager-console. U kunt vele taken bewaken, inclusief deze met betrekking tot software-updates, energiebeheer en de implementatie van inhoud via uw hiërarchie.  

 Gebruik de volgende informatie om u te helpen bij het bewaken van algemene taken voor Configuration Manager:  

 **Waarschuwingen**  
   Zie [Waarschuwingen controleren](../../../core/servers/manage/use-alerts-and-the-status-system.md#BKMK_MonitorAlerts) in [Waarschuwingen en het statussysteem voor System Center Configuration Manager gebruiken](../../../core/servers/manage/use-alerts-and-the-status-system.md).  

 **Compatibiliteitsinstellingen**  
   Zie [Instellingen voor naleving bewaken in System Center Configuration Manager](../../../compliance/deploy-use/monitor-compliance-settings.md).  

 **Implementatie van inhoud**  
   Voor algemene informatie over het bewaken van inhoud, zie [Inhoud en infrastructuur voor inhoud beheren voor System Center Configuration Manager](../../../core/servers/deploy/configure/manage-content-and-content-infrastructure.md).  

Voor informatie over het controleren van bepaalde typen implementatie van inhoud:
-   Voor het controleren van toepassingen, zie [Toepassingen controleren met System Center Configuration Manager](/sccm/apps/deploy-use/monitor-applications-from-the-console).  

-   Voor het controleren van pakketten en programma's zie Pakketten en programma's beheren in [Pakketten en programma's in System Center Configuration Manager](../../../apps/deploy-use/packages-and-programs.md).  

**Endpoint Protection**  
   Zie [Endpoint Protection controleren in System Center Configuration Manager](../../../protect/deploy-use/monitor-endpoint-protection.md).  

**Bewaak energiebeheer**  
 Zie [Energiebeheer bewaken en plannen in System Center Configuration Manager](../../../core/clients/manage/power/monitor-and-plan-for-power-management.md).  

**Bewaak softwarelicentiecontrole**  
Zie [Het app-gebruik in System Center Configuration Manager controleren met softwaremeter](../../../apps/deploy-use/monitor-app-usage-with-software-metering.md).  

**Software-updates controleren**  
 Zie [software-updates in System Center Configuration Manager controleren](../../../sum/deploy-use/monitor-software-updates.md).  


##  <a name="BKMK_MonitorInfrastructure"></a> De hiërarchie-infrastructuur voor Configuration Manager controleren  
Configuration Manager biedt verschillende methoden om de status en bewerkingen van uw hiërarchie te controleren. U kunt de sitesysteemstatus door de hiërarchie verifiëren, intersitereplicatie van een sitehiërarchie of geografische weergave controleren, replicatiekoppelingen tussen sites voor databasereplicatie controleren en het Replication Link Analyser-hulpprogramma gebruiken voor het oplossen van replicatieproblemen.  

###  <a name="BKMK_SH_Node"></a> Over het knooppunt Sitehiërarchie  
De **sitehiërarchie** knooppunt van de **bewaking** werkruimte biedt u een overzicht van de Configuration Manager-hiërarchie en intersitelinks. U kunt twee weergaven gebruiken:  

-   **Diagram van hiërarchie**: Deze weergave toont uw hiërarchie als een vereenvoudigde topologiekaart alleen essentiële informatie.  

-   **Geografische weergave**: Deze weergave bevat uw sites op een geografische kaart weergegeven met sitelocaties die u configureert.  

Gebruik het knooppunt **Sitehiërarchie** voor het controleren van de gezondheid van elke site en de intersitereplicatiekoppelingen en hun relatie tot externe factoren, zoals een geografische locatie.  

Omdat sitestatus en intersite status repliceren als sitegegevens en niet als algemene gegevens koppelen wanneer u uw Configuration Manager-console met een onderliggende primaire site verbindt, kunt u de status van site of de koppelingsstatus voor andere primaire sites of hun onderliggende secundaire sites niet weergeven. Bijvoorbeeld in een multiprimaire sitehiërarchie, wanneer uw Configuration Manager-console verbinding met een primaire site maakt, kunt u de status van onderliggende secundaire sites, de primaire site en de centrale beheersite weergeven, maar u kunt de status van andere knooppunten van de hiërarchie onder de centrale beheersite niet zien.  

 Gebruik de opdracht **Instellingen configureren** om te controleren hoe de weergave van de sitehiërarchie uitgevoerd is. Configuraties voor de **sitehiërarchie** knooppunt die u maakt wanneer uw Configuration Manager-console is verbonden met één site worden gerepliceerd naar alle andere sites.  

#### <a name="hierarchy-diagram"></a>Diagram van hiërarchie  
 Het hiërarchiediagram geeft uw sites in een topologiekaart weer. U kunt in deze weergave een site selecteren en een samenvattend statusbericht van deze site weergeven, detailanalyse om statusberichten weer te geven en u krijgt toegang tot het dialoogvenster **Eigenschappen** van de sites.  

 Bovendien kunt u de muisaanwijzer op de koppeling van een site of replicatiekoppeling tussen sites om de statuswaarde op hoog niveau voor dat object weer te onderbreken. Omdat de status replicatiekoppeling niet algemeen repliceert in een hiërarchie met meervoudige primaire sites, moet u uw Configuration Manager-console verbinden met de centrale beheersite om de details van replicatiekoppeling tussen alle sites weer te geven.  

 De volgende opties wijzigen het hiërarchiediagram:  

-   **Groepen**: U kunt het aantal primaire sites en secundaire sites die een wijziging activeren in de hiërarchiediagramweergave waarin de sites in een enkel object combineert kunt configureren. Als sites worden gecombineerd tot een enkel object, ziet u het totale aantal sites en een hoge rollup van statusberichten en sitestatus. Groepsconfiguraties hebben geen invloed op de geografische weergave.  

-   **Favoriete sites**: U kunt afzonderlijke sites opgeven als favoriete site. Een ster-icoontje identificeert een favoriete site in het hiërarchiediagram. Favoriete sites worden niet gecombineerd met andere sites wanneer u groepen gebruikt en worden altijd afzonderlijk weergegeven.  

#### <a name="geographical-view"></a>Geografische weergave  
 De geografische weergave toont de locatie van elke site op een geografische kaart. Alleen de sites die u met een locatie configureert worden weergegeven. Als u een site in deze weergave selecteert, worden de replicatiekoppelingen naar bovenliggende of onderliggende sites getoond. Anders dan bij de weergave van het hiërarchiediagram, kunt u het sitestatusbericht of details van replicatiekoppelingen niet tonen in deze weergave.  

> [!NOTE]  
>  Voor het gebruik van de geografische weergave wordt de computer waarop de Configuration Manager-console verbinding maakt moet Internet Explorer hebben geïnstalleerd en hebben toegang tot Bing-kaarten met HTTP-protocol.  

De volgende optie wijzigt de geografische weergave.  

-   **Sitelocatie**: U kunt een geografische locatie voor elke site opgeven. U kunt de locatie opgeven als een straatadres, een plaatsnaam zoals de naam van een stad of aan de hand van coördinaten voor de breedte- en lengtegraad. U geeft **N 47 40 26.3572 W 122 7 17.4432** op als de sitelocatie, om bijvoorbeeld de breedte- en lengtegraad van Redmond Washington te gebruiken. De symbolen voor de graden, minuten of seconden van lengte of breedte moet u niet opgeven. Configuration Manager gebruikt Bing-kaarten om de locatie op de geografische weergave weer te geven. Dit biedt u de optie om uw hiërarchie weer te geven met betrekking tot een geografische locatie, die inzicht kan geven in regionale problemen en die mogelijk specifieke sites of intersitereplicatie kunnen betreffen.  

     Wanneer u een locatie opgeeft, kunt u het vak **Locatie** gebruiken om naar een specifieke site in uw hiërarchie te zoeken. Als de site is geselecteerd is, voert u de locatie in als stadsnaam of straatadres in de kolom **Locatie** . Configuration Manager gebruikt Bing-kaarten om op te lossen de locatie.  

###  <a name="BKMK_MonitorRepLinksAndStatuss"></a> Databasereplicatiekoppelingen en de replicatiestatus bewaken  
 Via het knooppunt **Sitehiërarchie** in de werkruimte **Bewaking** zijn zeer gedetailleerde gegevens beschikbaar. Daarnaast kunt u details voor databasereplicatie bewaken wanneer u het knooppunt **Databasereplicatie** in de werkruimte **Bewaking** gebruikt. Van de **databasereplicatie** kunt u de status van replicatiekoppelingen tussen sites, en de initialisatiedetails en replicatiedetails voor replicatiegroepen op de site waarmee de Configuration Manager-console is verbonden bewaken.  

> [!TIP]  
>  Hoewel knooppunt **Databasereplicatie** ook wordt weergegeven onder knooppunt **Hiërarchieconfiguratie** in werkruimte **Beheer** , kunt u de replicatiestatus voor databasereplicatiekoppelingen vanuit deze locatie niet weergeven.  

####  <a name="BKMK_MonitorReplicationLinks"></a> Status replicatiekoppeling  
Databasereplicatie tussen sites omvat de replicatie van verschillende informatiesets, replicatiegroepen genoemd. Elke replicatiegroep repliceert met verschillende replicatieprioriteiten. De gegevens van een replicatiegroep en de frequentie van replicatie kunnen standaard niet worden gewijzigd.  

 Als een replicatiekoppeling actief is en geen status heeft van mislukt of gedegradeerd, repliceren alle replicatiegroepen tijdig. Wanneer een of meerdere replicatiegroepen geen replicatie kan uitvoeren in de verwachte periode, dan wordt de koppeling als gedegradeerd weergegeven. Gedegradeerde koppelingen kunnen nog steeds werken, maar u moet ze controleren om te waarborgen dat ze terugkeren naar de actieve status of ze onderzoeken om te zorgen dat geen bijkomende degradatie of replicatiefouten optreden.  

 Voor elke replicatiekoppeling kunt u opgeven na hoeveel mislukte replicatiepogingen van een replicatiegroep de status van de koppeling wordt ingesteld op Gedegradeerd of Mislukt. Zelfs wanneer op een na alle replicatiegroepen lukken, wordt de status van de link ingesteld op gedegradeerd of mislukt omdat een replicatiegroep de replicatie niet kan uitvoeren in het opgegeven aantal pogingen. Voor meer informatie over drempelwaarden voor replicatie, zie de sectie [Drempelwaarden voor databasereplicatie](../../../core/servers/manage/data-transfers-between-sites.md#BKMK_DBRepThresholds) in [Gegevensoverdracht tussen sites in System Center Configuration Manager](../../../core/servers/manage/data-transfers-between-sites.md).  

 Gebruik de informatie in onderstaande tabel om de status van replicatiekoppelingen te begrijpen die mogelijk verder onderzocht moeten worden.  

|Koppelingsbeschrijving|Meer informatie|  
|----------------------|----------------------|  
|**Koppeling is actief**|Er zijn geen problemen gedetecteerd en de communicatie via de koppeling is actueel.|  
|**Koppeling is gedegradeerd**|Replicatie is functioneel maar minstens een replicatieobject of -groep is vertraagd. Koppelingen in deze status controleren en informatie van beide sites op de koppeling nakijken op aanwijzingen van mislukken van de koppeling.<br /><br /> Een koppeling kan de status van gedegradeerd ook weergeven wanneer de site die gerepliceerde gegevens ontvangt de gegevens niet snel naar de database kan doorvoeren. Dit kan gebeuren wanneer een grote hoeveelheid gegevens repliceren. Als u bijvoorbeeld een software-update implementeert naar een groot aantal computers, dan kan het enige tijd duren om het volume gerepliceerde gegevens door de bovenliggende site op de koppeling te verwerken. De vertraagde verwerking op de bovenliggende site kan ertoe leiden dat de status van de koppeling gedegradeerd wordt tot de bovenliggende site erin slaagt de achterstand van gegevens te verwerken.|  
|**Koppeling is mislukt**|Replicatie is niet functioneel. Een replicatiekoppeling kan mogelijk zonder verdere acties te ondernemen herstellen. U kunt de  Replication Link Analyzer gebruiken om te onderzoeken en om replicatie op deze koppeling op te lossen.<br /><br /> Deze status kan ook duiden op een probleem met het fysieke netwerk tussen de bovenliggende en onderliggende site op de replicatiekoppeling.|  

 Terwijl een bovenliggende site wordt bijgewerkt naar een nieuw servicepack en u de status van de koppeling van de onderliggende site ziet, wordt de status van de koppeling als actief weergegeven. Na het bijwerken, tot de onderliggende site zich ook in hetzelfde servicepack bevindt als de bovenliggende site, wordt de status van de koppeling als actief weergegeven wanneer deze wordt bekeken vanaf de bovenliggende koppeling en als wordt geconfigureerd wanneer deze wordt bekeken vanaf de onderliggende site.  

####  <a name="BKMK_MonitorReplicationStatus"></a> Replicatiestatus  
 U kunt het knooppunt **Databasereplicatie** in de werkruimte **Bewaking** gebruiken om de status van replicatie weer te geven van een replicatiekoppeling en details weer te geven over de sitedatabase op elke site op de replicatiekoppeling. U kunt ook details over replicatiegroepen weergeven. Selecteer, om details weer te geven een replicatiekoppeling en selecteer vervolgens het geschikte tabblad voor de replicatiestatus die u wilt weergeven. Hieronder volgen details met betrekking tot de verschillende tabbladen voor replicatiestatus.  

 **Samenvatting**  
 Informatie van hoog niveau weergeven over de replicatie van sitegegevens en algemene gegevens tussen de twee sites op een koppeling.  

 U kunt ook klikken op **Rapporten voor historische verkeersgegevens weergeven** om een rapport weer te geven dat details toont over de netwerkbandbreedte gebruikt door replicatie via de replicatiekoppeling.  

 **Bovenliggende site**  
 Voor de bovenliggende site op een replicatiekoppeling, gegevens inzake de database weergeven, met inbegrip van:  

-   Firewallpoorten voor de SQL Server  

-   Vrije schijfruimte  

-   Databasebestandslocaties  

-   Certificaten  

**Onderliggende Site**  
 Voor de onderliggende site op een replicatiekoppeling, gegevens inzake de database weergeven, met inbegrip van:  

-   Firewallpoorten voor de SQL Server  

-   Vrije schijfruimte  

-   Databasebestandslocaties  

-   Certificaten  

**Initialisatiedetails**    
 De initialisatiestatus voor replicatiegroepen weergeven die repliceren via de replicatiekoppeling. Deze informatie kan u helpen bij het identificeren wanneer initialisatie van replicatiegegevens uitgevoerd wordt of mislukt is.  

 U kunt deze informatie bovendien gebruiken om te identificeren wanneer een site zich mogelijk in een interoperabiliteitsmodus bevindt. Interoperabiliteitsmodus treedt op wanneer de onderliggende site kan niet dezelfde versie van Configuration Manager worden uitgevoerd als de bovenliggende site.  

**Replicatiedetails**    
 Raadpleeg de replicatiestatus voor elke replicatiegroep die via de link repliceert. Gebruik deze informatie om te helpen problemen of vertragingen te identificeren voor de replicatie van specifieke gegevens en om te helpen de geschikte databsereplicatiedrempels te bepalen voor deze link. Voor meer informatie over drempelwaarden voor databasereplicatie, zie de sectie [Drempelwaarden voor databasereplicatie](../../../core/servers/manage/data-transfers-between-sites.md#BKMK_DBRepThresholds) in [Gegevensoverdracht tussen sites in System Center Configuration Manager](../../../core/servers/manage/data-transfers-between-sites.md).  

> [!TIP]  
>  Replicatiegroepen voor sitegegevens worden enkel gezonden vanaf de onderliggende site naar de bovenliggende site. Replicatiegroepen voor globale gegevens worden gerepliceerd in beide richtingen.  

###  <a name="BKMK_RLA"></a> Over de Replication Link Analyzer  
 Configuration Manager bevat **Replication Link Analyzer** waarmee u kunt analyseren en herstellen van replicatieproblemen. U kunt Replication Link Analyzer gebruiken om fouten in de replicatielink te herstellen wanneer replicatie gefaald heeft en wanneer replicatie stopt met werken maar nog niet gemeld werd als gefaald. Replication Link Analyzer kunnen worden gebruikt voor het oplossen van replicatieproblemen tussen de volgende computers in de Configuration Manager-hiërarchie (de richting van de Replicatiefout doet niet terzake):  

-   Tussen een siteserver en de sitedatabaseserver.  

-   Tussen een databaseserver voor sites en een andere sites sitedatabasecomputer (intersite-replicatie).  

U kunt Replication Link Analyzer uitvoeren in de Configuration Manager-console of achter de opdrachtprompt:  

-   Uitvoeren in de Configuration Manager-console: In de **bewaking** werkruimte, klikt u op de **databasereplicatie** knooppunt, selecteer de replicatiekoppeling die u analyseren wilt, en klik vervolgens in de **databasereplicatie** groep op de **Start** tabblad **Replication Link Analyzer**.  

-   Als u wilt uitvoeren bij een opdrachtprompt, typ de volgende opdracht: **%path%\Microsoft Configuration Manager\AdminConsole\bin\Microsoft.ConfigurationManager.ReplicationLinkAnalyzer.Wizard.exe &lt;bronsiteserver FQDN\> &lt;doelsiteserver FQDN\>**  

Wanneer u Replication Link Analyzer uitvoert, detecteert hij problemen door gebruik te maken van een reeks diagnostische regels en controles. Wanneer het hulpprogramma uitgevoerd wordt, kunt u de problemen zien die het hulpprogramma identificeert. Wanneer instructies om een probleem op te lossen gekend zijn, worden ze weergegeven. Indien Replication Link Analyzer automatisch een probleem kan oplossen, wordt u deze optie aangeboden. Wanneer Replication Link Analyzer is voltooid, worden de resultaten opgeslagen in de volgende XML-rapport en een logboekbestand op het bureaublad van de gebruiker die het hulpprogramma uitvoert:  

-   ReplicationAnalysis.xml  

-   ReplicationLinkAnalysis.log  

Wanneer Replication Link Analyzer uitgevoerd wordt, stopt hij de volgende services terwijl hij sommige problemen herstelt, en herstelt hij deze services wanneer herstel volledig is:  

-   SMS SITE COMPONENT MANAGER  

-   SMS EXECUTIVE  

Controleer, indien Replication Link Analyzer faalt om herstel te vervolledigen, de siteserver en start deze services opnieuw indien ze gestopt zijn.  

Succesvolle en onsuccesvolle onderzoeks- en herstelacties worden in het logboek geregistreerd om bijkomende gegevens te leveren die niet getoond worden in de interface van het hulpprogramma.  

**Vereisten voor het gebruik van Replication Link Analyzer**  

-   De account die u gebruikt om de Replication Link Analyzer uit te voeren, moet machtigingen als lokale beheerder hebben op elke computer die betrokken is bij de replicatielink. Het account is niet vereist voor een specifieke op rollen gebaseerde beheerbeveiligingsrol. Daarom een gebruiker met beheerdersrechten met toegang tot de **databasereplicatie** knooppunt kunt het hulpprogramma uitvoeren in de Configuration Manager-console of een systeembeheerder met voldoende machtigingen voor elke computer kan het hulpprogramma uitvoeren aan een opdrachtprompt.  

-   De account die u gebruikt om de Replication Link Analyzer uit te voeren, moet systeembeheerdersrechten hebben op elke SQL Server-database die betrokken is bij de replicatielink.  

**Bekende problemen voor Replication Link Analyzer**  

-   Met de release van System Center Configuration Manager versie 1511 genereert de replication link analyzer SQL Server Service Broker-certificaatfouten voor primaire sites die een upgrade uitgevoerd van System Center 2012 Configuration Manager. Dit komt door wijzigingen in de namen van de certificaten die zijn geïntroduceerd in versie 1511 waarvoor Replication Link Analyzer nog niet is bijgewerkt. Deze fouten kunnen worden genegeerd.  

###  <a name="BKMK_ProcsforMonitoringReplication"></a> Procedures voor het bewaken van databasereplicatie  

##### <a name="to-monitor-high-level-site-to-site-database-replication-status"></a>Voor het bewaken van de replicatiestatus op hoog niveau site-naar-site-database    
1.  Klik in de Configuration Manager-console op **bewaking**.  

2.  Klik, in de werkruimte **Controle** op **Sitehiërarchie** om de weergave **Hiërarchiediagram** te openen.  

3.  Pauzeer kort met de muisaanwijzer op de lijn tussen de twee sites om de status te zien van globale en sitegegevensreplicatie voor deze sites.  

##### <a name="to-monitor-the-replication-status-for-a-replication-link"></a>Voor het bewaken van de replicatiestatus voor een replicatiekoppeling    
1.  Klik in de Configuration Manager-console op **bewaking**.  

2.  Klik in de werkruimte **Controle** op **Databasereplicatie**en selecteer dan de replicatielink voor de link die u wenst te bewaken. Selecteer dan in de werktuimte het geschikte tabblad om verschillende gegevens te zijn over de replicatiestatus voor deze link.  
