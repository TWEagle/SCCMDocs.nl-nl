---
title: Inleiding tot software-updates | Microsoft Docs
description: Leer de basisbeginselen van software-updates in System Center Configuration Manager.
keywords: 
author: dougeby
ms.author: dougeby
manager: angrobe
ms.date: 10/06/2016
ms.topic: article
ms.prod: configuration-manager
ms.service: 
ms.technology: configmgr-sum
ms.assetid: e9778b13-c8a3-40eb-8655-34ac8ce9cdaa
ms.openlocfilehash: 2904b904bbaf155f016f55fbd36af80308a42d76
ms.sourcegitcommit: 51fc48fb023f1e8d995c6c4eacfda7dbec4d0b2f
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 08/07/2017
---
# <a name="introduction-to-software-updates-in-system-center-configuration-manager"></a>Inleiding tot software-updates in System Center Configuration Manager

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*

Software-updates in System Center Configuration Manager biedt een set hulpprogramma's en bronnen die kunnen helpen bij de complexe taak van tracking en toepassen van software-updates op clientcomputers in de onderneming beheren. Een effectief beheerproces van software-update is nodig om operationele efficiëntie te behouden, om beveiligingsproblemen te overwinnen en om de stabiliteit van de netwerkinfrastructuur te behouden. Wegens de veranderende aard van technologie en het permanent opduiken van nieuwe veiligheidsbedreigingen, vergt effectief beheer van software-updates consistente en continue aandacht.  

Zie voor een voorbeeldscenario dat toont hoe u software-updates in uw omgeving kunt implementeren, [voorbeeldscenario voor het implementeren van beveiligingsupdates](../deploy-use/example-scenario-deploy-monitor-monthly-security-updates.md).  

##  <a name="BKMK_Synchronization"></a> Synchronisatie van software-updates  
 Synchronisatie van software-updates in Configuration Manager maakt verbinding met Microsoft Update voor het ophalen van metagegevens van software-updates. Het hoogste niveau (centrale beheersite of zelfstandige primaire site) synchroniseert met Microsoft Update volgens een planning of wanneer u handmatig synchronisatie vanaf de Configuration Manager-console start. Als Configuration Manager synchronisatie van software-updates op het hoogste niveau, wordt synchronisatie software-updates gestart op onderliggende sites, indien aanwezig. Wanneer synchronisatie volledig is op de primaire site of secundaire site, wordt een beleid voor de hele site gemaakt, dat de clientcomputers de locatie van software-updatepunten levert.  

> [!NOTE]  
>  Software-updates zijn in de clientinstellingen standaard ingeschakeld. Indien u evenwel de clientinstelling **Software-updates inschakelen op clients** instelt op **Nee** om software-updates uit te schakelen op een verzameling of in de standaardinstellingen, worden de locaties van software-updatepunten niet gezonden naar gekoppelde clients. Zie voor meer informatie [clientinstellingen van software-updates](../../core/clients/deploy/about-client-settings.md#software-updates).  

 Nadat de client het beleid ontvangt, start de client een scan voor naleving van software-updates en schrijft de informatie naar Windows Management Instrumentation (WMI). De informatie over naleving wordt dan gezonden naar het beheerpunt dat dan de informatie naar de siteserver zendt. Zie de sectie [Software updates compliance assessment](#BKMK_SUMCompliance) van dit onderwerp voor meer informatie over nalevingsbeoordeling.  

 U kunt meerdere software-updatepunten installeren in een primaire site. Het eerste software-updatepunt dat u installeert is geconfigureerd als de synchronisatiebron. Dit synchroniseert vanaf Microsoft Update of een WSUS-server niet in uw Configuration Manager-hiërarchie. De andere software-updatepunten op de site gebruiken het eerste software-updatepunt als de synchronisatiebron.  

> [!NOTE]  
>  Wanneer het proces van synchronisatie van software-updates volledig is op de site van het hoogste niveau, worden de metagegevens van software-updates gerepliceerd naar onderliggende sites door gebruik te maken van databasereplicatie. Wanneer u een Configuration Manager-console verbinding met de onderliggende site, wordt in Configuration Manager de metagegevens van software-updates weergegeven. Echter, totdat u installeert en configureert een software-updatepunt op de site, zullen clients niet scannen voor naleving van software-updates, clients wordt geen informatie over naleving rapporteren aan Configuration Manager en u niet met succes software-updates implementeren.  

### <a name="synchronization-on-the-top-level-site"></a>Synchronisatie in de site op het hoogste niveau  
 Het proces van synchronisatie van software-updates op de site van het hoogste niveau, onttrekt de metagegevens voor software-updates van Microsoft Update, die voldoen aan de criteria die u opgeeft in de eigenschappen van onderdeel software-updatepunt U kunt de criteria alleen op de site het hoogste niveau configureren.  

> [!NOTE]  
>  U kunt een bestaande WSUS-server die zich niet in de Configuration Manager-hiërarchie in plaats van Microsoft-Updates als de synchronisatiebron opgeven.  

 De volgende lijst beschrijft de basisstappen voor het synchronisatieproces op de site van het hoogste niveau:  

1.  Synchronisatie van software-updates wordt gestart.  

2.  WSUS Synchronization Manager zendt een verzoek naar WSUS dat uitgevoerd wordt op het software-updatepunt, om synchronisatie te starten met Microsoft Update.  

3.  De metagegevens van software-updates worden gesynchroniseerd door Microsoft Update, en wijzigingen worden toegevoegd of geüpdatet in de WSUS-database.  

4.  Wanneer WSUS synchronisatie heeft beëindigd, synchroniseert WSUS Synchronization Manager de metagegevens van de software-updates vanaf de WSUS-database met de Configuration Manager-database en eventuele wijzigingen na de laatste synchronisatie worden ingevoegd of geüpdatet in de sitedatabase. De metagegevens van de software-updates worden opgeslagen in de site-database als een configuratie-item.  

5.  De configuratie-items van software-updates worden gezonden naar onderliggende sites door gebruik te maken van databasereplicatie.  

6.  Wanneer synchronisatie is voltooid, maakt de WSUS Synchronization Manager een statusbericht 6702.  

7.  WSUS Synchronization Manager zendt een synchronisatieverzoek naar alle onderliggende sites.  

8.  WSUS Synchronization Manager zendt één verzoek per keer naar WSUS die uitgevoerd wordt op andere software-updatepunten op de site. De WSUS-servers op de andere software-updatepunten zijn geconfigureerd om replica's te zijn van WSUS, die uitgevoerd wordt op het standaard-updatepunt op de site.  

### <a name="synchronization-on-child-primary-and-secondary-sites"></a>Synchronisatie in de onderliggende primaire en secundaire sites  
 Wanneer het proces van synchronisatie van software-updates volledig is op de site van het hoogste niveau, worden de configuratie-items van de software-updates gerepliceerd naar onderliggende sites door gebruik te maken van databasereplicatie. Op het einde van het proces zendt de site op het hoogste niveau een synchronisatieverzoek naar de onderliggende site en de onderliggende site start de WSUS-synchronisatie. De volgende lijst beschrijft de basisstappen voor het synchronisatieproces op een onderliggende primaire site of op een secundaire site:  

1.  WSUS Synchronization Manager zendt een synchronisatieverzoek vanaf de site van het hoogste niveau.  

2.  Synchronisatie van software-updates wordt gestart.  

3.  WSUS Synchronization Manager zendt een verzoek naar WSUS die uitgevoerd wordt op het software-updatepunt, om synchronisatie te starten.  

4.  WSUS die uitgevoerd wordt op het software-updatepunt op de onderliggende site synchroniseert metagegevens van software-updates vanaf WSUS die uitgevoerd wordt op het software-updatepunt op de bovenliggende site.  

5.  Wanneer synchronisatie is voltooid, maakt de WSUS Synchronization Manager een statusbericht 6702.  

6.  Vanaf een primaire site zendt WSUS Synchronization Manager een synchronisatieverzoek naar alle onderliggende, secundaire sites. De secundaire site start de synchronisatie van software-updates met de bovenliggende primaire site. De secundaire site is geconfigureerd als een replica van WSUS die uitgevoerd wordt op de bovenliggende site.  

7.  WSUS Synchronization Manager zendt één verzoek per keer naar WSUS die uitgevoerd wordt op andere software-updatepunten op de site. De WSUS-servers op de andere software-updatepunten zijn geconfigureerd om replica's te zijn van WSUS, die uitgevoerd wordt op het standaard-updatepunt op de site.  

##  <a name="BKMK_SUMCompliance"></a> Software updates compliance assessment  
 Voordat u software-updates naar clientcomputers in Configuration Manager implementeert, start u een scan voor naleving van software-updates op clientcomputers. Voor elke software-update wordt een statusbericht gemaakt dat de nalevingsstatus bevat voor de update. De statusberichten worden in bulk gezonden naar het beheerpunt en dan naar de siteserver, waar de nalevingstatus ingevoegd wordt in de sitedatabase. De nalevingsstatus voor software-updates wordt weergegeven in de Configuration Manager-console. U kunt software-updates implementeren en installeren op computers die de updates nodig hebben. De volgende secties geven informatie over de nalevingsstatussen en beschrijven het proces van scannen voor naleving van software-updates  

### <a name="software-updates-compliance-states"></a>Nalevingsstatussen voor software-updates  
 De volgende lijsten en beschrijft elke nalevingsstatus die wordt weergegeven in de Configuration Manager-console voor software-updates.  

-   **Vereist**  

     Specificeert dat de software-update toepasselijk is en nodig op de clientcomputer Eén van de volgende condities kan waar zijn wanneer de software-updatestatus **Vereist**is:  

    -   De software-update is niet geïmplementeerd op de clientcomputer.  

    -   De software-update is geïnstalleerd op de clientcomputer. Evenwel is het meest recente statusbericht nog niet ingevoegd in de database op de siteserver. De clientcomputer scant opnieuw voor de update nadat de installatie voltooid is. Er kan een vertraging zijn tot twee minuten vóór de client de geüpdate toestand zendt naar het beheerpunt dat dan de geüpdate toestand doorstuurt naar de siteserver.  

    -   De software-update is geïnstalleerd op de clientcomputer. De software-update-installatie vereist evenwel een opnieuw opstarten van de computer vóór de update voltooid is.  

    -   De software-update werd geïmplementeerd naar de clientcomputer maar werd nog niet geïnstalleerd.  

-   **Niet vereist**  

     Geeft op dat de software-update niet toepasselijk is op de clientcomputer. De software-update is daarom niet vereist.  

-   **Geïnstalleerd**  

     Geeft op dat de software-update toepasselijk is op de clientcomputer en dat de clientcomputer de software-update reeds geïnstalleerd heeft.  

-   **Onbekend**  

     Geeft op dat de siteserver geen statusbericht heeft ontvangen van de clientcomputer, typisch wegens één van de volgende redenen:  

    -   De clientcomputer heeft niet met succes gescand op naleving van software-updates.  

    -   De scan is voltooid op de clientcomputer. Het statusbericht werd nog niet verwerkt op de siteserver, eventueel omwille van een achterstand van de statusberichten.  

    -   De scan werd voltooid op de clientcomputer, maar het statusbericht werd nog niet ontvangen van de onderliggende site.  

    -   De scan werd voltooid op de clientcomputer, maar het statusberichtenbestand werd op één of andere manier beschadigd en kon niet verwerkt worden.  

### <a name="scan-for-software-updates-compliance-process"></a>Het scannen op de naleving voor software-updates  
 Wanneer de software-updatepunt is geïnstalleerd en gesynchroniseerd, wordt een computerbeleid voor de hele site gemaakt die de clientcomputers informeert dat de Configuration Manager software-updates is ingeschakeld voor de site. Wanneer een client een computerbeleid ontvangt, wordt een scan gepland, die willekeurig binnen de komende twee uren kan beginnen, om de naleving te beoordelen. Wanneer de scan is gestart, wist een clientagent-proces voor software updates de geschiedenis van de scan, verzendt een verzoek om de WSUS-server te vinden die moet gebruikt worden voor de scan, en werkt het beleid van de lokale groep bij met de WSUS-serverlocatie.  

> [!NOTE]  
>  Internetclients moeten zich verbinden met de WSUS-server door gebruik te maken van SSL.  

 Een scanaanvraag wordt doorgegeven aan de Windows Update Agent (WUA). De WUA verbindt vervolgens met de WSUS-serverlocatie die wordt vermeld in het lokale beleid, haalt de metagegevens van de software-updates op die zijn gesynchroniseerd op de WSUS-server en scant de clientcomputer voor de updates. Een clientagentproces voor software-updates detecteert dat de compatibiliteitsscan is voltooid en maakt de statusberichten voor elke software-update waarvan de compatibiliteitsstatus is gewijzigd na de laatste scan. De statusberichten worden elke 15 minuten in bulk naar het beheerpunt verzonden. Het beheerpunt stuurt vervolgens de statusberichten naar de siteserver door; daar worden de statusberichten toegevoegd aan de siteserverdatabase.  

 Na de initiële scan voor compatibiliteit van software-updates, wordt de scan gestart volgens het geconfigureerde schema voor scannen. Als de client echter gescand heeft naar de compatibiliteit van software-updates binnen de door Time to Live (TTL) aangeduide tijdspanne, dan gebruikt deze de metagegevens van de software-updates die lokaal worden opgeslagen. Als de laatste scan zich buiten de TTL bevindt, moet de client verbinding maken met WSUS dat wordt uitgevoerd op het software-updatepunt en de metagegevens bijwerken van de software-updates die zijn opgeslagen op de clients.  

 Met inbegrip van het scanschema kan de scan voor compatibiliteit van de software-updates op de volgende manieren starten:  

-   **Schema voor scan van software-updates**: De scan voor software-updates naleving begint bij het geconfigureerde scanschema dat is geconfigureerd in de instellingen voor Clientagent voor Software-Updates. Zie voor meer informatie over het configureren van de clientinstellingen voor Software-Updates [clientinstellingen van software-updates](../../core/clients/deploy/about-client-settings.md#software-updates).  

-   **Eigenschappen van Configuration Manager-actie**: Kan worden gestart door de gebruiker de **Scancyclus voor Software-Updates** of **evaluatiecyclus voor installatie van Software-Updates** actie op de **actie** tabblad de **eigenschappen van Configuration Manager** in het dialoogvenster op de clientcomputer.  

-   **Implementatie voor nieuwe evaluaties**: De evaluatie van implementaties en de scan voor software-updates naleving begint bij het geconfigureerde herevaluatie schema, dat is geconfigureerd in de instellingen van de Clientagent voor Software-Updates. Zie voor meer informatie over de clientinstellingen voor Software-Updates [clientinstellingen van software-updates](../../core/clients/deploy/about-client-settings.md#software-updates).  

-   **Vóór het downloaden van updatebestanden**: De Clientagent voor Software-Updates downloadt de software-updatebestanden naar de lokale clientcache wanneer een clientcomputer een toewijzingsbeleid voor een nieuwe vereiste implementatie ontvangt. De clientagent start, vóór het downloaden van de software-updatebestanden, een scan om te verifiëren dat de software-update nog steeds vereist is.  

-   **Vóór software-update installatie**: Net voordat de installatie van de software-update Start de Clientagent voor Software-Updates een scan om te controleren of de software-updates nog steeds vereist.  

-   **Na software-update installatie**: Nadat de installatie van een software-update voltooid is, start de Clientagent voor Software-Updates een scan om te controleren dat de software-updates niet langer vereist zijn, en maakt u een nieuw statusbericht waarin wordt aangegeven dat de software-update is geïnstalleerd. Als het na het voltooien van de installatie nodig is om opnieuw op te starten, geeft het statusbericht aan dat de clientcomputer wacht om opnieuw te worden opgestart.  

-   **Nadat het systeem opnieuw opstarten**: Wanneer een clientcomputer is in afwachting van opnieuw opstarten voor de software-updatepunten installatie is voltooid, de Clientagent voor Software-Updates een scan wordt gestart nadat het opnieuw opstarten om te controleren dat de software-update niet langer vereist is en maakt een statusbericht waarin wordt vermeld dat de software-update is geïnstalleerd.  

#### <a name="time-to-live-value"></a>De waarde Time to Live  
 De metagegevens van software-updates die zijn vereist voor de scan naar compatibiliteit van software-updates, worden opgeslagen op de lokale clientcomputer en zijn standaard tot 24 uur geldig. Deze waarde wordt aangeduid als de Time to Live (TTL).  

#### <a name="scan-for-software-updates-compliance-types"></a>Typen scans voor software-updatenaleving  
 De client scant naar de compatibiliteit van software-updates via een online of offline scan en een geforceerde of niet-geforceerde scan, afhankelijk van de manier waarop de scan voor software-updatecompatibiliteit wordt gestart. Hieronder wordt beschreven welke methoden voor het starten van de scan online of offline zijn en of de scan geforceerd of niet-geforceerde.  

-   **Schema voor scan van software-updates** (niet-geforceerde online scan)  

     Volgens het geconfigureerde scanschema verbindt de client met WSUS dat wordt uitgevoerd op het software-updatepunt om de metagegevens van de software-updates op te halen, alleen wanneer de laatste scan buiten de TTL werd uitgevoerd.  

-   **Scancyclus voor Software-Updates** of **evaluatiecyclus voor installatie van Software-Updates** (geforceerde online scan)  

     De clientcomputer maakt steeds verbinding met WSUS dat wordt uitgevoerd op het software-updatepunt voor het ophalen van de metagegevens van software-updates voordat de clientcomputer scant naar de compatibiliteit van software-updates. Nadat de scan is voltooid, wordt de TTL-teller opnieuw ingesteld. Als de TTL bijvoorbeeld 24 uur is, wordt de TTL opnieuw ingesteld op 24 uur nadat een gebruiker een scan start van de compatibiliteit van software-updates.  

-   **Implementatie voor nieuwe evaluaties** (niet-geforceerde online scan)  

     Volgens het geconfigureerde implementatieschema voor nieuwe evaluaties verbindt de client met WSUS dat wordt uitgevoerd op het software-updatepunt om de metagegevens van de software-updates op te halen, alleen wanneer de laatste scan buiten de TTL werd uitgevoerd.  

-   **Vóór het downloaden van updatebestanden** (niet-geforceerde online scan)  

     Voordat de client updatebestanden in de vereiste implementaties kan downloaden, verbindt de client met WSUS dat wordt uitgevoerd op het software-updatepunt om de metagegevens van de software-updates op te halen, alleen wanneer de laatste scan buiten de TTL werd uitgevoerd.  

-   **Vóór software-update installatie** (niet-geforceerde online scan)  

     Voordat de client software-update installeert in de vereiste implementaties, verbindt de client met WSUS dat wordt uitgevoerd op het software-updatepunt om de metagegevens van de software-updates op te halen, alleen wanneer de laatste scan buiten de TTL werd uitgevoerd.  

-   **Na software-update installatie** (geforceerde offline scan)  

     Na het installeren van een software-update, start de clientagent van software-updates een scan door gebruik te maken van de lokale metagegevens. De client maakt nooit verbinding met WSUS dat wordt uitgevoerd op het software-updatepunt om de metagegevens van software-updates op te halen.  

-   **Nadat het systeem opnieuw opstarten** (geforceerde offline scan)  

     Na het installeren van een software-update en het opnieuw opstarten van de computer, start de clientagent van software-updates een scan door gebruik te maken van de lokale metagegevens. De client maakt nooit verbinding met WSUS dat wordt uitgevoerd op het software-updatepunt om de metagegevens van software-updates op te halen.  

##  <a name="BKMK_DeploymentPackages"></a> Implementatiepakketten voor software-updates  
 Een implementatiepakket van een software-updatepunt is de drager die wordt gebruikt om software-updates naar een gedeelde netwerkmap te downloaden, en om de bronbestanden van de software-update te kopiëren naar de inhoudsbibliotheek op siteservers en op distributiepunten die in de implementatie worden gedefinieerd. Door de wizard Updates downloaden te gebruiken, kunt u software-updates downloaden en deze toevoegen aan implementatiepakketten voordat u ze implementeert. Met deze wizard kunt u software-updates inrichten op distributiepunten en verifiëren dat dit onderdeel van het implementatieproces succesvol is voordat u de software-updates naar clients implementeert.  

 De implementatie gebruikt automatisch het implementatiepakket dat de software-updates bevat als u gedownloade software-updates implementeert door gebruik te maken van de wizard Software-updates implementeren. Wanneer er software-updates worden geïmplementeerd die nog niet zijn gedownload, dient u een nieuw of bestaand implementatiepakket op te geven in de wizard Software-updates implementeren. De software-updates worden gedownload wanneer de wizard is voltooid.  

> [!IMPORTANT]  
>  U moet de gedeelde netwerkmap handmatig maken voor de bronbestanden van het installatiepakket voordat u het opgeeft in de wizard. Elk implementatiepakket moet een andere gedeelde netwerkmap gebruiken.  

> [!IMPORTANT]  
>  Het computeraccount van de SMS-provider en de gebruiker met beheerdersrechten die de software-updates effectief downloadt, hebben beide **Schrijf** machtigingen nodig voor de pakketbron. Beperk de toegang tot de pakketbron om het risico te beperken dat kwaadwillende personen knoeien met de bronbestanden van software-updates in de pakketbron.  

 Wanneer er een nieuw implementatiepakket wordt gemaakt, wordt de inhoudsversie op 1 ingesteld voordat er software-updates worden gedownload. Wanneer de software-updatebestanden worden gedownload met het pakket, wordt de inhoudsversie verhoogd naar 2. Daarom beginnen alle nieuwe implementatiepakketten met de inhoudsversie 2. Telkens wanneer de inhoud in een implementatiepakket wordt gewijzigd, wordt de inhoudsversie met 1 verhoogd. Zie voor meer informatie [basisconcepten voor inhoudsbeheer](../../core/plan-design/hierarchy/fundamental-concepts-for-content-management.md).  

 Clients installeren software-updates in een implementatie door gebruik te maken van een distributiepunt waarvan de software-updates beschikbaar zijn, onafhankelijk van het implementatiepakket. Zelfs als een implementatiepakket wordt verwijderd voor een actieve implementatie, kunnen clients nog steeds de software-updates installeren in de implementatie, zolang dat elke update naar minstens één ander implementatiepakket is gedownload en beschikbaar is op een distributiepunt dat kan worden bereikt vanaf de client. Wanneer het laatste implementatiepakket dat een software-update bevat, wordt verwijderd, kunnen clientcomputers de software-update niet ophalen totdat de update opnieuw wordt gedownload naar een implementatiepakket. Software-updates worden weergegeven met een rode pijl in de Configuration Manager-console wanneer de updatebestanden zich niet in implementatiepakketten bevinden. Implementaties worden weergegeven met een dubbele rode pijl als ze updates in deze toestand bevatten.  

##  <a name="BKMK_DeploymentWorkflows"></a> Werkstromen voor de implementatie van software-updates  
 Er zijn twee hoofdscenario's voor het implementeren van software-updates in uw omgeving: handmatige implementatie en automatische implementatie. Doorgaans kunt u software-updates handmatig implementeren om een basislijn voor clientcomputers te maken. Vervolgens beheert u software-updates op clients via automatische implementatie. De volgende secties bevatten een samenvatting van de werkstroom voor handmatige en automatische implementatie voor software-updates.  

###  <a name="BKMK_ManualDeployment"></a> Handmatige implementatie van software-updates  
 Handmatige implementatie van software-updates is het proces van het selecteren van software-updates in de Configuration Manager-console en het handmatig starten van het implementatieproces. Doorgaans gebruikt u deze methode van implementatie om de clientcomputers up-to-date te krijgen met de vereiste software-updates voordat u automatische implementatieregels kunt maken die de lopende maandelijkse implementaties van software-updates beheren, en om buiten-bandvereisten van software-updates te implementeren. De volgende lijst geeft de algemene werkstroom voor handmatige implementatie van software-updates:  

1.  Filter voor software-updates die gebruikmaken van specifieke vereisten. U kunt bijvoorbeeld criteria opgeven die alle beveiligingsupdates of kritieke software-updates ophalen die op meer dan 50 clientcomputers zijn vereist.  

2.  Maak een software-updategroep die de software-updates bevat.  

3.  Downloadt de inhoud voor software-updates in de software-updategroep.  

4.  De software-updategroep handmatig implementeren.  

###  <a name="BKMK_AutomaticDeployment"></a> Automatische implementatie van software-updates  
 De automatische implementatie van software-updates wordt geconfigureerd met een regel voor automatische implementatie (ADR). Doorgaans gebruikt u deze methode voor uw maandelijkse software-updates (ook wel bekend als 'patchdinsdag') en voor het beheren van definitie-updates. Wanneer de regel wordt uitgevoerd, worden software-updates verwijderd van de software-updategroep (als u een bestaande groep gebruikt). De software-updates die voldoen aan een bepaald criterium (bijvoorbeeld alle softwarebeveiligingsupdates van de afgelopen week) worden toegevoegd aan een software-updategroep. De inhoudsbestanden voor de software-updates worden gedownload en gekopieerd naar de distributiepunten en de software-updates worden geïmplementeerd op clientcomputers in de doelverzameling. De volgende lijst geeft de algemene werkstroom voor automatische implementatie van software-updates:  

1.  Maak een regel voor automatische implementatie waarmee implementatie-instellingen als de volgende worden opgegeven:  

    -   Doelverzameling  

    -   Bepaal of u de implementatie of rapportage over compatibiliteit van software-updates wilt inschakelen voor de clientcomputers in de doelverzameling.  

    -   Criteria voor software-updates  

    -   Evaluatie- en implementatieschema's  

    -   Gebruikerservaring  

    -   Downloadeigenschappen  

2.  De software-updates worden toegevoegd aan een software-updategroep.  

3.  De software-updategroep wordt geïmplementeerd naar de clientcomputers in de doelverzameling, als deze is opgegeven.  

 U moet bepalen welke implementatiestrategie er moet worden gebruikt in uw omgeving. U kunt bijvoorbeeld een regel voor automatische implementatie maken en een verzameling van testclients als doel nemen. Nadat u hebt gecontroleerd of de software-updates op de testgroep zijn geïnstalleerd, kunt u een nieuwe implementatie aan de regel toevoegen of de verzameling in de bestaande implementatie wijzigen in een doelverzameling die een grotere set van clients bevat. De software-updateobjecten die door de regels voor automatische implementatie worden gemaakt, zijn interactief.  

-   Software-updates die zijn geïmplementeerd met een regel voor automatische implementatie worden automatisch geïmplementeerd voor nieuwe clients die aan de doelverzameling zijn toegevoegd.  

-   Nieuwe software-updates die zijn toegevoegd aan een software-updategroep, worden automatisch geïmplementeerd naar de clients in de doelverzameling.  

-   U kunt implementaties voor de regel voor automatische implementatie op elk gewenst moment in- of uitschakelen.  

 Nadat u een regel voor automatische implementatie hebt gemaakt, kunt u aanvullende implementaties aan de regel toevoegen. Dit kan helpen bij het beheren van de complexiteit van het implementeren van verschillende updates voor verschillende verzamelingen. Elke nieuwe implementatie beschikt over de volledige functionaliteit en implementatiecontrole, en elke implementatie die u toevoegt:  

-   Gebruikt dezelfde bijwerkgroep en hetzelfde bijwerkpakket die worden gemaakt wanneer de ADR voor het eerst wordt uitgevoerd  

-   U kunt een andere verzameling opgeven  

-   Ondersteunt unieke implementatie-eigenschappen, waaronder:  

    -   Activeringstijd  

    -   Deadline  

    -   Ervaringen van eindgebruikers weergeven of verbergen  

    -   Afzonderlijke waarschuwingen voor deze implementatie  

##  <a name="BKMK_DeploymentProcess"></a> Het implementatieproces voor software-updates  
 Nadat u software-updates implementeert of wanneer er een automatische implementatieregel wordt uitgevoerd en software-updates implementeert, wordt er een implementatietoewijzingsbeleid toegevoegd aan het machinebeleid voor de site. De software-updates worden naar de pakketbron gedownload vanaf de downloadlocatie, het internet of de gedeelde netwerkmap. De software-updates worden gekopieerd van de pakketbron naar de inhoudsbibliotheek op de siteserver en vervolgens gekopieerd naar de inhoudsbibliotheek op het distributiepunt.  

 Wanneer een clientcomputer in de doelverzameling voor de implementatie het machinebeleid ontvangt, start de clientagent voor software-updates een evaluatiescan. De clientagent downloadt de vereiste inhoud voor software-updates vanaf een distributiepunt naar de lokale clientcache zodra de implementatie wordt ontvangen, maar wacht tot na de waarde van de instelling **Tijd waarop de software beschikbaar is** voor de implementatie is bereikt voordat de software-updates beschikbaar zijn voor installatie. De software-updates in optionele implementaties (implementaties zonder installatiedeadline) worden pas gedownload wanneer een gebruiker de installatie handmatig start.  

 Wanneer de geconfigureerde deadline verstrijkt, voert de clientagent voor software-updates een scan uit om te controleren of de software-updates nog steeds vereist zijn. Vervolgens wordt de lokale cache op de clientcomputer gecontroleerd en wordt er nagegaan of de bronbestanden voor de software-update nog steeds beschikbaar zijn. Tot slot installeert de client de software-updates. Als de inhoud uit de clientcache is verwijderd om ruimte vrij te maken voor een andere implementatie, downloadt de client de software-updates opnieuw vanaf het distributiepunt naar de clientcache. Software-updates worden altijd naar de clientcache gedownload, ongeacht de maximale grootte van de clientcache. Wanneer de installatie is voltooid, controleert de clientagent of de software-updates nog vereist zijn en vervolgens wordt er een statusbericht naar het beheerpunt verzonden om aan te geven dat de software-updates nu op de client zijn geïnstalleerd.  

### <a name="required-system-restart"></a>Het systeem verplicht opnieuw opstarten  
 Standaard wordt het opnieuw starten van het systeem geïnitieerd wanneer software-updates voor een vereiste implementatie op een clientcomputer worden geïnstalleerd en het opnieuw opstarten van het systeem is vereist. Voor software-updates die voor de deadline zijn geïnstalleerd, wordt het automatisch opnieuw starten van het systeem uitgesteld, totdat de deadline is bereikt, tenzij de computer voordat tijdstip om een andere reden opnieuw wordt opgestart. Het opnieuw starten van het systeem kan worden onderdrukt voor servers en werkstations. Deze instellingen worden geconfigureerd op de pagina **Gebruikerservaring** van de wizard Software-updates toepassen of de wizard voor het maken van regels voor automatische updates.  

### <a name="deployment-reevaluation-cycle"></a>Cyclus voor het opnieuw evalueren van implementaties  
 Clientcomputers starten standaard om de zeven dagen een cyclus voor het opnieuw evalueren van implementaties. Tijdens deze evaluatiecyclus controleert de clientcomputer of er software-updates aanwezig zijn die eerder zijn geïmplementeerd en geïnstalleerd. Als er software-updates ontbreken, worden de software-updates opnieuw geïnstalleerd vanuit de lokale cache. Als een software-updates niet langer beschikbaar is in de lokale cache, kan deze vanaf een distributiepunt worden gedownload en vervolgens worden geïnstalleerd. U kunt de planning voor opnieuw evalueren configureren op de pagina **Software-updates** in de clientinstellingen.  

##  <a name="BKMK_EmbeddedDevices"></a> Ondersteuning voor Windows Embedded-apparaten die gebruikmaken van schrijffilters  
 Wanneer u software-updates implementeert voor Windows Embedded-apparaten waarvoor een schrijffilter is ingeschakeld, kunt u opgeven of het schrijffilter op het apparaat tijdens de implementatie moet worden uitgeschakeld en of het apparaat vervolgens na de implementatie opnieuw moet worden opgestart. Als het schrijffilter niet wordt uitgeschakeld, wordt de software geïmplementeerd op een tijdelijke overlay en wordt de software niet meer geïnstalleerd wanneer het apparaat opnieuw start, tenzij een andere implementatie afdwingt dat wijzigingen blijvend zijn.  

> [!NOTE]  
>  Wanneer u een software-update implementeert op een Windows Embedded-apparaat, moet u ervoor zorgen dat het apparaat lid is van een verzameling met een geconfigureerd onderhoudsvenster. U kunt op deze manier beheren wanneer het schrijffilter is uitgeschakeld en ingeschakeld en wanneer het apparaat opnieuw wordt gestart.  

 De gebruikerservaringinstelling die het gedrag van het schrijffilter bepaalt, is het selectievakje **Wijzigingen doorvoeren bij deadline of tijdens onderhoud (opnieuw opstarten noodzakelijk)**.  

 Zie voor meer informatie over hoe Configuration Manager ingesloten apparaten beheert die schrijffilters gebruiken [Planning voor clientimplementatie op Windows Embedded-apparaten](../../core/clients/deploy/plan/planning-for-client-deployment-to-windows-embedded-devices.md).  

##  <a name="BKMK_ExtendSoftwareUpdates"></a> Software-updates uitbreiden in Configuration Manager  
 System Center Updates Publisher gebruiken voor het beheren van software-updates die niet beschikbaar via Microsoft Update zijn. Nadat u de software-updates naar de updateserver publiceert en synchroniseren van de software-updates in Configuration Manager, kunt u de software-updates implementeren naar Configuration Manager-clients. Zie voor meer informatie over Updates Publisher [Updates Publisher 2011](http://go.microsoft.com/fwlink/p/?LinkId=252947).  

## <a name="next-steps"></a>Volgende stappen
[Software-updates plannen](../plan-design/plan-for-software-updates.md)
