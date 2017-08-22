---
title: Softwareupdates automatisch implementeren | Microsoft Docs
description: Softwareupdates automatisch implementeren door nieuwe updates toe te voegen aan een updategroep die is gekoppeld aan een actieve implementatie of ADR's.
keywords: 
author: dougeby
ms.author: dougeby
manager: angrobe
ms.date: 12/07/2016
ms.topic: article
ms.prod: configuration-manager
ms.service: 
ms.technology: configmgr-sum
ms.assetid: b27682de-adf8-4edd-9572-54886af8f7fb
ms.openlocfilehash: 804a9d7a32cfbdb498c6748c5d99a1874261c231
ms.sourcegitcommit: 51fc48fb023f1e8d995c6c4eacfda7dbec4d0b2f
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 08/07/2017
---
#  <a name="BKMK_AutoDeploy"></a> Software-updates automatisch implementeren  

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*

 U kunt software-updates automatisch implementeren door nieuwe software-updates toe te voegen aan een updategroep die is gekoppeld aan een actieve implementatie of kunt u een regel voor automatische implementatie (ADR). Normaal gesproken u ADR's gebruikt voor maandelijkse software-updates (normaal gesproken bekend als updates van de Patch-dinsdag) implementeren en beheren van definitie-updates. Als u hulp nodig hebt om te bepalen welke implementatie methode is geschikt is voor u, raadpleegt u [software-updates implementeren](deploy-software-updates.md)

##  <a name="BKMK_AddUpdatesToExistingGroup"></a> Software-updates toevoegen aan een geïmplementeerde updategroep  
Nadat u maken en implementeren van software-updategroep, kunt u software-updates toevoegen aan de groep bijwerken en deze worden vervolgens automatisch geïmplementeerd.  

> [!IMPORTANT]  
>  Wanneer u software-updates toevoegt aan een bestaande software-updategroep die al is geïmplementeerd, duurt het mogelijk enkele minuten voordat de aanvullende software-updates aan de implementatie worden toegevoegd.  

Gebruik de volgende procedure om software-updates toe te voegen aan een bestaande updategroep.  

#### <a name="to-add-software-updates-to-an-existing-software-update-group"></a>Software-updates toevoegen aan een bestaande software-updategroep  

1.  Navigeer in de Configuration Manager-console naar **softwarebibliotheek** > **overzicht** > **Software-Updates**.  

2.  Selecteer de software-updates die aan de nieuwe software-updategroep moeten worden toegevoegd.  

3.  Klik in het tabblad **Start** in de groep **Update** op **Lidmaatschap bewerken**.  

4.  Selecteer de software-updategroep waaraan u de software-updates wilt toevoegen als leden.  

5.  Klik op het knooppunt **Software-updategroepen** om de software-updategroep weer te geven.  

6.  Klik op de software-updategroep en klik op het tabblad **Start** in de groep **Bijwerken** op **Leden weergeven** om een lijst met software-updates in de groep weer te geven.  

##  <a name="BKMK_CreateAutomaticDeploymentRule"></a> Een regel voor automatische implementatie (ADR) maken  
U kunt software-update automatisch goedkeuren en implementeren door gebruik te maken van een ADR. U kunt instellen dat met de regel software-updates worden toegevoegd aan een nieuwe software-updategroep elke keer dat de regel wordt uitgevoerd of u kunt software-updates laten toevoegen aan een bestaande groep. Wanneer een regel wordt uitgevoerd en software-updates worden toegevoegd aan een bestaande groep, worden met de regel alle software-updates verwijderd uit de groep en vervolgens de software-updates aan de groep toegevoegd die voldoen aan de criteria die u hebt gedefinieerd. Als u bijvoorbeeld een ADR wilt uitvoeren om elke dag nieuw uitgebrachte software-updates te zoeken en deze op clients te implementeren, moet u kiezen voor de optie om een nieuwe software-updategroep te maken in plaats van het toevoegen van de software-updates aan een bestaande groep.  

> [!WARNING]  
>  Voordat u voor het eerst een ADR maakt, moet u controleren of het synchroniseren van software-updates op de site is voltooid. Dit is vooral belangrijk wanneer u Configuration Manager met een niet-Engelse taal uitvoert omdat software-updateclassificaties voorafgaande aan de eerste synchronisatie in het Engels weergegeven en vervolgens in de gelokaliseerde taal weergegeven nadat de synchronisatie van software-update is voltooid. Regels die u maakt voordat u software-updates synchroniseert, werken mogelijk na het synchroniseren niet meer naar behoren omdat de teksttekenreeks niet langer overeenkomt.  

 Gebruik de volgende procedure om een ADR te maken.  

#### <a name="to-create-an-adr"></a>Een ADR maken  

1.  Navigeer in de Configuration Manager-console naar **softwarebibliotheek** **overzicht** > **Software-Updates** > **regels voor automatische implementatie**.  

2.  Klik op het tabblad **Start** in de groep **Maken** op **Regel voor automatische implementatie maken**. De wizard Regel voor automatische implementatie maken wordt geopend.  

3.  Configureer de volgende instellingen op de pagina **Algemeen** :  

    -   **Naam**: Geef de naam voor de ADR. De naam moet uniek zijn, het doel van de regel beschrijven en onderscheiden van andere gebruikers in de Configuration Manager-site.  

    -   **Beschrijving**: Geef een beschrijving voor de ADR. De beschrijving moet bieden een overzicht van de regel voor implementatie en eventuele andere relevante informatie die helpt om te bepalen en te onderscheiden van andere gebruikers in de Configuration Manager-site. Het beschrijvingsveld is optioneel en kent een limiet van 256 tekens. Het veld is standaard leeg.  

    -   **Implementatiesjabloon selecteren**: Geef op of een eerder opgeslagen implementatiesjabloon moet worden toegepast. U kunt een implementatiesjabloon zo configureren dat deze meerdere algemene eigenschappen voor software-update-implementatie bevat. Deze kan vervolgens worden gebruikt wanneer u ADR's maakt. Deze sjablonen helpen de consistentie met soortgelijke implementaties te garanderen en besparen tijd.  

         U kunt via de wizard Regel voor automatische implementatie kiezen uit de ingebouwde implementatiesjablonen voor software-updates. De sjabloon **Definitie-updates** biedt algemene instellingen die u kunt gebruiken wanneer u definitiesoftware-updates implementeert. De sjabloon **Patch Tuesday** biedt algemene instellingen die u kunt gebruiken wanneer u software-updates implementeert op basis van een maandelijkse cyclus.  

    -   **Verzameling**: Hiermee geeft u de doelverzameling op die moet worden gebruikt voor de implementatie. Leden van de verzameling ontvangen de software-updates die in de implementatie zijn gedefinieerd.  

    -   Bepaal of u software-updates toevoegt aan een nieuwe of een bestaande software-updategroep. In de meeste gevallen kiest u waarschijnlijk voor het maken van een nieuwe software-updategroep wanneer de ADR wordt uitgevoerd. U kunt er echter voor kiezen om een bestaande groep uit te voeren als de regel wordt uitgevoerd volgens een agressievere planning. Als u de regel bijvoorbeeld dagelijks uitvoert voor definitie-updates, zou u de software-updates aan een bestaande software-updategroep kunnen toevoegen.  

    -   **De implementatie inschakelen nadat deze regel is uitgevoerd**: Geef op of de software-update-implementatie inschakelen nadat de ADR wordt uitgevoerd. Overweeg met betrekking tot deze specificatie het volgende:  

        -   Wanneer u de implementatie inschakelt, worden de software-updates die voldoen aan de gedefinieerde criteria in de regel, toegevoegd aan een software-updategroep, de inhoud van software-updates wordt, wanneer nodig, gedownload, de inhoud wordt gekopieerd naar de opgegeven distributiepunten en de software-updates worden geïmplementeerd op de clients in de doelverzameling.  

        -   Wanneer u de implementatie niet inschakelt, worden de software-updates die voldoen aan de gedefinieerde criteria in de regel, toegevoegd aan een software-updategroep en wordt het software-updatebeleid geconfigureerd, maar worden de software-updates niet gedownload of op clients geïmplementeerd. Deze situatie biedt u, wanneer nodig, tijd om het implementeren van de software-updates voor te bereiden, om te controleren of de software-updates die aan de criteria voldoen, toereikend zijn en om vervolgens de implementatie op een later tijdstip in te schakelen.  

4.  Configureer de volgende instellingen op de pagina Implementatie-instellingen:  

    -   **Wake-on-LAN gebruiken om clients voor vereiste implementaties te laten ontwaken**: Hiermee geeft u op of Wake On LAN tegen de deadline voor het verzenden van ontwaakpakketten naar computers waarvoor een of meer software-updates in de implementatie. Computers die zich op het tijdstip van de installatiedeadline in de slaapstandmodus bevinden, worden uit deze stand gehaald, zodat de installatie van de software-update kan worden gestart. Clients die zich in de slaapstandmodus bevinden en geen software-updates nodig hebben, worden niet gestart. Deze instelling is standaard uitgeschakeld.  

        > [!WARNING]  
        >  Voordat u deze optie kunt gebruiken, moeten computers en netwerken worden geconfigureerd voor Wake On LAN.  

    -   **Detailniveau**: Geef het detailniveau voor de statusberichten die zijn gerapporteerd door clientcomputers.  

        > [!IMPORTANT]  
        >  Stel, wanneer u definitie-updates implementeert, het detailniveau in op **Alleen fouten** als u wilt dat clients alleen statusberichten rapporteren wanneer een definitie-update niet bij de client wordt bezorgd. Als u dat niet doet, rapporteert de client mogelijk een groot aantal statusberichten dat van invloed kan zijn op de prestaties van de site server.  

    -   **Instelling voor licentiebepalingen**: Geef op of voor de automatische implementatie van software-updates waaraan licentiebepalingen zijn gekoppeld. Sommige software-updates bevatten licentiebepalingen. Dit is bijvoorbeeld het geval bij een servicepack. Wanneer u software-updates automatisch implementeert, worden de licentiebepalingen niet weergegeven en wordt er geen mogelijkheid geboden om de licentiebepalingen te accepteren. U kunt ervoor kiezen om alle software-updates automatisch te implementeren, ongeacht bijbehorende licentiebepalingen of om software-updates alleen te implementeren als er geen licentiebepalingen aan deze updates zijn gekoppeld.  

        > [!NOTE]  
        >  Als u de licentiebepalingen voor een software-update wilt weergeven, selecteert u de software in het knooppunt **Alle software-updates** van de werkruimte **Softwarebibliotheek** en vervolgens klikt u op het tabblad **Start** in de groep **Update** op **Licentie weergeven**.  
        >   
        >  Als u wilt zoeken naar software-updates waaraan licentiebepalingen zijn gekoppeld, kunt u de kolom **Licentiebepalingen** toevoegen aan het deelvenster met resultaten in het knooppunt **Alle software-updates** en vervolgens op de kolomkop klikken om de kolom te sorteren op software-updates met licentiebepalingen.  

5.  Configureer op de pagina Software-updates de criteria voor de software-updates die via de ADR worden opgehaald en toegevoegd aan de software-updategroep.  

    > [!IMPORTANT]  
    >  De limiet voor software-updates in de ADR is 1000 software-updates. Als u er zeker van wilt zijn dat de criteria die u op deze pagina opgeeft, ertoe leiden dat er minder dan 1000 software-updates worden opgehaald, kunt u overwegen om dezelfde criteria in te stellen in het knooppunt **Alle software-updates** in de werkruimte **Softwarebibliotheek** .  

    > [!NOTE]
    > U start in Configuration Manager versie 1610, kunt u filteren op de grootte van de inhoud voor software-updates in de regels voor automatische implementatie. U kunt bijvoorbeeld instellen de **inhoud grootte (KB)** filteren op **< 2048** alleen softwareupdates te downloaden die kleiner dan 2 MB zijn. Met dit filter voorkomt dat grote software-updates automatisch downloaden naar betere ondersteuning vereenvoudigd Windows downlevel-onderhoud als de netwerkbandbreedte beperkt is. Zie voor meer informatie [Configuration Manager en vereenvoudigd onderhoud van Windows op omlaag niveau besturingssystemen](https://blogs.technet.microsoft.com/enterprisemobility/2016/10/07/configuration-manager-and-simplified-windows-servicing-on-down-level-operating-systems/).

6.  Geef op de pagina Evaluatieplanning op of de ADR moet worden ingeschakeld voor uitvoeren op basis van een planning. Wanneer dit is ingeschakeld, klikt u op **Aanpassen** om de terugkerende planning in te schakelen.  

    > [!IMPORTANT]  
    >  De synchronisatieplanning voor het software-updatepunt wordt weergegeven om u te helpen bij het vaststellen van de frequentie van de evaluatieplanning. De evaluatieplanning mag nooit zo worden ingesteld dat de frequentie hoger is dan de synchronisatieplanning voor software-updates. De begintijdconfiguratie voor de planning is gebaseerd op de lokale tijd van de computer waarop de Configuration Manager-console.  

    > [!NOTE]  
    >  Als u de ADR handmatig wilt uitvoeren, selecteert u de regel en klikt u vervolgens op **Nu uitvoeren** op het tabblad **Start** in de groep **Regel voor automatische implementatie** . Controleer of de synchronisatie voor software-updates is uitgevoerd sinds u de regel voor het laatst hebt uitgevoerd voordat u de ADR handmatig uitvoert.  

    > [!IMPORTANT]  
    >  De ADR-evaluatie kan twee tot drie keer per dag worden uitgevoerd.  

7.  Configureer de volgende instellingen op de pagina Implementatieplanning:  

    -   **Evaluatie van planning**: Geef aan of Configuration Manager de beschikbare tijd en de tijdstippen voor de installatiedeadline evalueert op basis van UTC of van de lokale tijd van de computer waarop de Configuration Manager-console.  

        > [!NOTE]  
        >  Als u lokale tijd selecteert en selecteer vervolgens **zo snel mogelijk** voor de **tijd Software beschikbaar** of **installatiedeadline**, de huidige tijd op de computer die de Configuration Manager-console wordt gebruikt om te evalueren wanneer updates beschikbaar zijn of wanneer ze worden geïnstalleerd op een client wordt uitgevoerd. Als de client zich in een andere tijdzone bevindt, worden deze acties uitgevoerd wanneer de tijd van de client de evaluatietijd heeft bereikt.  

    -   **Tijd software beschikbaar**: Selecteer een van de volgende instellingen op te geven wanneer de software-updates beschikbaar voor clients zijn:  

        -   **Zo spoedig mogelijk**: Selecteer deze instelling om de softwareupdates die zijn opgenomen in de implementatie beschikbaar voor de clientcomputers zo snel mogelijk. Wanneer u de implementatie met deze instelling is ingeschakeld maakt, wordt in Configuration Manager het clientbeleid bijgewerkt. Clients detecteren de implementatie vervolgens gedurende de volgende pollingcyclus van het clientbeleid en kunnen de updates verkrijgen die beschikbaar zijn voor installatie.  

        -   **Specifiek tijdstip**: Selecteer deze instelling om de softwareupdates die zijn opgenomen in de implementatie op een specifieke datum en tijd beschikbaar is voor de clientcomputers. Wanneer u de implementatie met deze instelling is ingeschakeld maakt, wordt in Configuration Manager het clientbeleid bijgewerkt. Clients detecteren de implementatie vervolgens gedurende de volgende pollingcyclus van het clientbeleid. De software-updates in de implementatie zijn echter pas na de geconfigureerde datum en het geconfigureerde tijdstip beschikbaar voor installatie.  

    -   **Installatiedeadline**: Selecteer een van de volgende instellingen om op te geven van de installatiedeadline voor de software-updates in de implementatie:  

        -   **Zo spoedig mogelijk**: Selecteer deze instelling om de software-updates in de implementatie zo spoedig mogelijk automatisch worden geïnstalleerd.  

        -   **Specifiek tijdstip**: Selecteer deze instelling om de software-updates in de implementatie op een specifieke datum en tijd automatisch worden geïnstalleerd. Configuration Manager bepaalt de deadline voor het installeren van software-updates door het geconfigureerde **specifiek tijdstip** interval voor de **tijd Software beschikbaar**.  

        > [!NOTE]  
        >  Het daadwerkelijke tijdstip van de installatiedeadline is het weergegeven deadlinetijdstip plus een willekeurige hoeveelheid die maximaal twee uur is. Hierdoor wordt de mogelijke invloed op alle clientcomputers in de doelverzameling waarop de software-updates in de implementatie gelijktijdig worden geïnstalleerd, gereduceerd.  
        >   
        >  U kunt de **Computeragent** -clientinstelling **Willekeurig toepassen van deadline uitschakelen** configureren om de willekeurige installaties voor vereiste software-updates uit te schakelen. Zie [Computeragent](../../core/clients/deploy/about-client-settings.md#computer-agent) voor meer informatie.  

8. Configureer de volgende instellingen op de pagina Gebruikerservaring:  

    -   **Meldingen voor gebruikers**: Geef op of meldingen van de software-updates weergeven in Software Center op de clientcomputer op de geconfigureerde **tijd Software beschikbaar** en of meldingen voor gebruikers weergegeven op de clientcomputers.  

    -   **Deadlinegedrag**: Geef het gedrag op dat moet worden vertoond als de deadline voor de implementatie van de software-update wordt bereikt. Geef op of de software-updates in de implementatie moeten worden geïnstalleerd. Geef ook op of het systeem na het installeren van software-updates opnieuw moet worden opgestart, ongeacht het geconfigureerde onderhoudsvenster. Zie voor meer informatie over onderhoudsvensters [het gebruik van onderhoudsvensters](../../core/clients/manage/collections/use-maintenance-windows.md).  

    -   **Gedrag voor opnieuw opstarten apparaat**: Geef op of het onderdrukken van opnieuw opstarten van servers en werkstations nadat software-updates zijn geïnstalleerd en opnieuw opstarten is vereist om de installatie te voltooien.  

        > [!IMPORTANT]  
        >  Het onderdrukken van het opnieuw opstarten van het systeem kan nuttig zijn in serveromgevingen of in andere gevallen waarin u wilt dat de computers die de software-updates installeren, niet standaard opnieuw worden opgestart. Dit kan er echter toe leiden dat computers zich in een onbeveiligde toestand bevinden. Het toestaan van afgedwongen opnieuw opstarten garandeert onmiddellijke voltooiing van de installatie van software-updates.  

    -   **Schrijffilters voor Windows Embedded-apparaten**: Wanneer u software-updates op Windows Embedded-apparaten waarvoor schrijffilters ingeschakeld implementeren zijn, kunt u opgeven om de software-update op een tijdelijke overlay en de wijzigingen later installeren of de wijzigingen doorvoert tegen de installatiedeadline of tijdens een onderhoudsvenster. Wanneer u wijzigingen doorvoert tegen de installatiedeadline of tijdens een onderhoudsvenster, moet er opnieuw worden opgestart, zodat de wijzigingen behouden blijven op het apparaat.  

        > [!NOTE]  
        >  Wanneer u een software-update implementeert op een Windows Embedded-apparaat, moet u ervoor zorgen dat het apparaat lid is van een verzameling met een geconfigureerd onderhoudsvenster.  

    - **Implementatiegedrag voor nieuwe evaluatie bij het opnieuw opstarten van software-updates**: Vanaf Configuration Manager versie 1606, selecteer deze instelling om software-updates implementaties configureren zodat clients op een nalevingsscan voor software-updates onmiddellijk nadat een client software installeert-updates en opnieuw gestart. Hierdoor kan de client controleren op aanvullende beschikbare software-updates nadat de client opnieuw is opgestart, en deze installeren (en zorgen voor naleving) tijdens datzelfde onderhoudsvenster.

9. Configureer op de pagina waarschuwingen hoe Configuration Manager en System Center Operations Manager waarschuwingen voor deze implementatie genereren moeten.  

    > [!NOTE]  
    >  U kunt recente waarschuwingen met betrekking tot software-updates weergegeven in het knooppunt **Software-updates** in de werkruimte **Softwarebibliotheek** .  

10. Configureer de volgende instellingen op de pagina Downloadinstellingen:  

    - Geef op of de client de software-updates moet downloaden en installeren wanneer een client is verbonden met een langzaam netwerk of wanneer deze gebruikmaakt van een locatie terugvalinhoudlocatie.  

    - Geef op of de client de software-updates moet downloaden en installeren vanaf een terugvaldistributiepunt wanneer de inhoud voor de software-updates niet beschikbaar is op een voorkeursdistributiepunt.  

    - **Toestaan dat clients inhoud te delen met andere clients in hetzelfde subnet**: Geef op of het gebruik van BranchCache voor inhouddownloads inschakelen. Zie [Concepten voor inhoudsbeheer](../../core/plan-design/hierarchy/fundamental-concepts-for-content-management.md#branchcache) voor meer informatie over BranchCache.  

    - **Als software-updates niet beschikbaar is op het distributiepunt in de huidige, neighbor of site groepen, inhoud downloaden van Microsoft Updates**: Selecteer deze instelling clients die zijn verbonden met het intranet software-updates voor downloaden vanaf Microsoft Update als software-updates niet beschikbaar zijn op distributiepunten hebben. Clients op Internet gaat altijd u naar Microsoft Update voor de inhoud van software-updates.

    - Geef op of clients mogen downloaden na een installatiedeadline wanneer deze internetverbindingen met een datalimiet gebruiken. Internetproviders brengen soms de hoeveelheid gegevens die u verzendt en ontvangt in rekening wanneer u gebruikmaakt van een internetverbinding naar gebruik.  

    > [!NOTE]  
    >  Clients vragen de inhoudlocatie aan bij het beheerpunt voor de software-updates in een implementatie. Het downloadgedrag is afhankelijk van hoe u het distributiepunt, implementatiepakket en de instellingen op deze pagina hebt geconfigureerd. Zie [Scenario's voor de locatie van inhoudsbronnen](../../core/plan-design/hierarchy/content-source-location-scenarios.md) voor meer informatie.  

11. Selecteer op de pagina Implementatiepakket een bestaand implementatiepakket of configureer de volgende instellingen voor het maken van een nieuw implementatiepakket:  

    1.  **Naam**: Geef de naam van het implementatiepakket. Dit moet een unieke naam zijn die de pakketinhoud beschrijft. Er kunnen maximaal 50 tekens worden ingevoerd.  

    2.  **Beschrijving**: Geef een beschrijving die informatie over het implementatiepakket biedt. De beschrijving mag niet langer zijn dan 127 tekens.  

    3.  **Pakketbron**: Hiermee geeft u de locatie van de bronbestanden voor software-update.  Typ een netwerkpad voor de bronlocatie, zoals **\\\\server\sharenaam\pad**, of klik op **Bladeren** en ga naar de netwerklocatie. U moet een gedeelde map maken voor de bronbestanden van het installatiepakket voordat u doorgaat naar de volgende pagina.  

        > [!NOTE]  
        >  De bronlocatie van het installatiepakket die u opgeeft, mag niet door een ander software-installatiepakket worden gebruikt.  

        > [!IMPORTANT]  
        >  Het computeraccount van de SMS-provider en de gebruiker die de wizard uitvoert voor het downloaden van de software-updates, moeten over NTFS-machtigingen voor **schrijven** op de downloadlocatie beschikken. U moet de toegang tot de downloadlocatie zorgvuldig beperken om het risico op kwaadwillenden die met bronbestanden van de software-update knoeien, te reduceren.  

        > [!IMPORTANT]  
        >  U kunt de pakketbronlocatie in de eigenschappen van het installatiepakket wijzigen nadat Configuration Manager het implementatiepakket maakt. Als u dit doet, moet u echter eerst de inhoud van de oorspronkelijke pakketbron kopiëren naar de nieuwe pakketbronlocatie.  

    4.  **Prioriteit voor verzenden**: Geef de prioriteit voor verzenden voor het implementatiepakket. Configuration Manager gebruikt de prioriteit voor verzenden voor het implementatiepakket wanneer het pakket naar distributiepunten wordt verzonden. Installatiepakketten worden in volgorde van prioriteit verzonden: Hoog, Gemiddeld of laag. Pakketten met een identieke prioriteit worden verzonden in de volgorde waarin deze zijn gemaakt. Als er geen achterstand is, wordt het pakket onmiddellijk verwerkt, ongeacht de prioriteit van het pakket.  

12. Geef op de pagina Distributiepunten de distributiepunten of distributiepuntgroepen op die als host zullen fungeren voor de software-updatebestanden. Zie [Configuraties van het distributiepunt](../../core/servers/deploy/configure/install-and-configure-distribution-points.md#bkmk_configs) voor meer informatie over distributiepunten.  

    > [!NOTE]  
    >  Deze pagina is alleen beschikbaar wanneer u een nieuw implementatiepakket voor software-updates maakt.  

13. Geef op de pagina Downloadlocatie op of de software-updatebestanden moeten worden gedownload vanaf internet of vanaf uw lokale netwerk. Configureer de volgende instellingen:  

    -   **Software-updates downloaden vanaf Internet**: Selecteer deze instelling om de software-updates downloaden vanaf een opgegeven locatie op Internet. Deze instelling is standaard ingeschakeld.  

    -   **Software-updates downloaden vanaf een locatie op het lokale netwerk**: Selecteer deze instelling om de softwareupdates downloaden vanaf een lokale map of gedeelde map. Deze instelling is nuttig wanneer de computer waarop de wizard wordt uitgevoerd, geen toegang tot internet heeft. Computers met internettoegang kunnen software-updates voortijdig downloaden en deze opslaan op een locatie op het lokale netwerk die toegankelijk is vanaf de computer waarop de wizard wordt uitgevoerd.  

14. Selecteer de talen waarvoor de geselecteerde software-updates worden gedownload op de pagina Taal selecteren. De software-updates worden alleen gedownload als deze beschikbaar zijn in de geselecteerde talen. Software-updates die niet aan een specifieke taal zijn gebonden, worden altijd gedownload. De wizard selecteert standaard de talen die u hebt geconfigureerd in de eigenschappen van het software-updatepunt. Er moet ten minste één taal worden geselecteerd voordat u doorgaat naar de volgende pagina. Wanneer u alleen talen selecteert die niet door een software-update worden ondersteund, mislukt het downloaden van de software-update.  

15. Controleer de instellingen op de pagina Overzicht. Klik, als u de instellingen wilt opslaan naar een implementatiesjabloon, op **Opslaan als sjabloon**, voer een naam in, selecteer de instellingen die u in de sjabloon wilt opnemen en klik op **Opslaan**. Als u een geconfigureerde instelling wilt wijzigen, klikt u op de gekoppelde wizardpagina en wijzigt u de instelling.  

    > [!NOTE]  
    >  De sjabloonnaam mag alfanumerieke ASCII-tekens en de tekens **\\** (backslash) en **‘** (apostrof) bevatten.  

16. Klik op **Volgende** om de ADR te maken.  

 Nadat u de wizard hebt voltooid, wordt de ADR uitgevoerd. Deze voegt software-updates toe die voldoen aan de opgegeven criteria voor een software-updategroep, downloadt de software-updates naar de inhoudsbibliotheek op de site server, distribueert de software-updates naar de geconfigureerde distributiepunten en implementeert de software-updategroep voor clients op de doellocatie.  

##  <a name="BKMK_AddDeploymentToADR"></a> Nieuwe implementaties aan een bestaande ADR toevoegen  
 Nadat u een regel voor automatische implementatie hebt gemaakt, kunt u aanvullende implementaties aan de regel toevoegen. Dit kan helpen bij het beheren van de complexiteit van het implementeren van verschillende updates voor verschillende verzamelingen. Elke nieuwe implementatie heeft alle functionaliteit en biedt de volledige implementatiebewakingservaring.  

#### <a name="to-add-a-new-deployment-to-an-existing-adr"></a>Een nieuwe implementatie aan een bestaande ADR toevoegen  

1.  Navigeer in de Configuration Manager-console naar **softwarebibliotheek** > **overzicht** > **Software-Updates** > **regels voor automatische implementatie**, en selecteer vervolgens de gewenste regel.  

2.  Klik op het tabblad **Start** in de groep **Regels voor automatische implementatie** op **Implementatie toevoegen**. De wizard Implementatie toevoegen wordt geopend.  

3.  Configureer op het tabblad **Verzameling** de volgende instellingen:  

    -   **Verzameling**: Hiermee geeft u de doelverzameling op die moet worden gebruikt voor de implementatie. Leden van de verzameling ontvangen de software-updates die in de implementatie zijn gedefinieerd.  

    -   **De implementatie inschakelen nadat deze regel is uitgevoerd**: Geef op of de software-update-implementatie inschakelen nadat de ADR wordt uitgevoerd. Overweeg met betrekking tot deze specificatie het volgende:  

        -   Wanneer u de implementatie inschakelt, worden de software-updates die voldoen aan de gedefinieerde criteria in de regel, toegevoegd aan een software-updategroep, de inhoud van software-updates wordt, wanneer nodig, gedownload, de inhoud wordt gekopieerd naar de opgegeven distributiepunten en de software-updates worden geïmplementeerd op de clients in de doelverzameling.  

        -   Wanneer u de implementatie niet inschakelt, worden de software-updates die voldoen aan de gedefinieerde criteria in de regel, toegevoegd aan een software-updategroep en wordt het software-updatebeleid geconfigureerd, maar worden de software-updates niet gedownload of op clients geïmplementeerd. Deze situatie biedt u, wanneer nodig, tijd om het implementeren van de software-updates voor te bereiden, om te controleren of de software-updates die aan de criteria voldoen, toereikend zijn en om vervolgens de implementatie op een later tijdstip in te schakelen.  

4.  Configureer de volgende instellingen op de pagina Implementatie-instellingen:  

    -   **Wake-on-LAN gebruiken om clients voor vereiste implementaties te laten ontwaken**: Hiermee geeft u op of Wake On LAN tegen de deadline voor het verzenden van ontwaakpakketten naar computers waarvoor een of meer software-updates in de implementatie. Computers die zich op het tijdstip van de installatiedeadline in de slaapstandmodus bevinden, worden uit deze stand gehaald, zodat de installatie van de software-update kan worden gestart. Clients die zich in de slaapstandmodus bevinden en geen software-updates nodig hebben, worden niet gestart. Deze instelling is standaard uitgeschakeld.  

        > [!WARNING]  
        >  Voordat u deze optie kunt gebruiken, moeten computers en netwerken worden geconfigureerd voor Wake On LAN.  

    -   **Detailniveau**: Geef het detailniveau voor de statusberichten die zijn gerapporteerd door clientcomputers.  

        > [!IMPORTANT]  
        >  Stel, wanneer u definitie-updates implementeert, het detailniveau in op **Alleen fouten** als u wilt dat clients alleen statusberichten rapporteren wanneer een definitie-update niet bij de client wordt bezorgd. Als u dat niet doet, rapporteert de client mogelijk een groot aantal statusberichten dat van invloed kan zijn op de prestaties van de site server.  

5.  Configureer de volgende instellingen op de pagina Implementatieplanning:  

    -   **Evaluatie van planning**: Geef aan of Configuration Manager de beschikbare tijd en de tijdstippen voor de installatiedeadline evalueert op basis van UTC of van de lokale tijd van de computer waarop de Configuration Manager-console.  

        > [!NOTE]  
        >  Als u lokale tijd selecteert en selecteer vervolgens **zo snel mogelijk** voor de **tijd Software beschikbaar** of **installatiedeadline**, de huidige tijd op de computer die de Configuration Manager-console wordt gebruikt om te evalueren wanneer updates beschikbaar zijn of wanneer ze worden geïnstalleerd op een client wordt uitgevoerd. Als de client zich in een andere tijdzone bevindt, worden deze acties uitgevoerd wanneer de tijd van de client de evaluatietijd heeft bereikt.  

    -   **Tijd software beschikbaar**: Selecteer een van de volgende instellingen op te geven wanneer de software-updates beschikbaar voor clients zijn:  

        -   **Zo spoedig mogelijk**: Selecteer deze instelling om de softwareupdates die zijn opgenomen in de implementatie beschikbaar voor de clientcomputers zo snel mogelijk. Wanneer u de implementatie met deze instelling is ingeschakeld maakt, wordt in Configuration Manager het clientbeleid bijgewerkt. Clients detecteren de implementatie vervolgens gedurende de volgende pollingcyclus van het clientbeleid en kunnen de updates verkrijgen die beschikbaar zijn voor installatie.  

        -   **Specifiek tijdstip**: Selecteer deze instelling om de softwareupdates die zijn opgenomen in de implementatie op een specifieke datum en tijd beschikbaar is voor de clientcomputers. Wanneer u de implementatie met deze instelling is ingeschakeld maakt, wordt in Configuration Manager het clientbeleid bijgewerkt. Clients detecteren de implementatie vervolgens gedurende de volgende pollingcyclus van het clientbeleid. De software-updates in de implementatie zijn echter pas na de geconfigureerde datum en het geconfigureerde tijdstip beschikbaar voor installatie.  

    -   **Installatiedeadline**: Selecteer een van de volgende instellingen om op te geven van de installatiedeadline voor de software-updates in de implementatie:  

        -   **Zo spoedig mogelijk**: Selecteer deze instelling om de software-updates in de implementatie zo spoedig mogelijk automatisch worden geïnstalleerd.  

        -   **Specifiek tijdstip**: Selecteer deze instelling om de software-updates in de implementatie op een specifieke datum en tijd automatisch worden geïnstalleerd. Configuration Manager bepaalt de deadline voor het installeren van software-updates door het geconfigureerde **specifiek tijdstip** interval voor de **tijd Software beschikbaar**.  

        > [!NOTE]  
        >  Het daadwerkelijke tijdstip van de installatiedeadline is het weergegeven deadlinetijdstip plus een willekeurige hoeveelheid die maximaal twee uur is. Hierdoor wordt de mogelijke invloed op alle clientcomputers in de doelverzameling waarop de software-updates in de implementatie gelijktijdig worden geïnstalleerd, gereduceerd.  
        >   
        >  U kunt de **Computeragent** -clientinstelling **Willekeurig toepassen van deadline uitschakelen** configureren om de willekeurige installaties voor vereiste software-updates uit te schakelen. Zie [Computeragent](../../core/clients/deploy/about-client-settings.md#computer-agent) voor meer informatie.  

6.  Configureer de volgende instellingen op de pagina Gebruikerservaring:  

    -   **Meldingen voor gebruikers**: Geef op of meldingen van de software-updates weergeven in Software Center op de clientcomputer op de geconfigureerde **tijd Software beschikbaar** en of meldingen voor gebruikers weergegeven op de clientcomputers.  

    -   **Deadlinegedrag**: Geef het gedrag op dat moet worden vertoond als de deadline voor de implementatie van de software-update wordt bereikt. Geef op of de software-updates in de implementatie moeten worden geïnstalleerd. Geef ook op of het systeem na het installeren van software-updates opnieuw moet worden opgestart, ongeacht het geconfigureerde onderhoudsvenster. Zie voor meer informatie over onderhoudsvensters [het gebruik van onderhoudsvensters](../../core/clients/manage/collections/use-maintenance-windows.md).  

    -   **Gedrag voor opnieuw opstarten apparaat**: Geef op of het onderdrukken van opnieuw opstarten van servers en werkstations nadat software-updates zijn geïnstalleerd en opnieuw opstarten is vereist om de installatie te voltooien.  

        > [!IMPORTANT]  
        >  Het onderdrukken van het opnieuw opstarten van het systeem kan nuttig zijn in serveromgevingen of in andere gevallen waarin u wilt dat de computers die de software-updates installeren, niet standaard opnieuw worden opgestart. Dit kan er echter toe leiden dat computers zich in een onbeveiligde toestand bevinden. Het toestaan van afgedwongen opnieuw opstarten garandeert onmiddellijke voltooiing van de installatie van software-updates.  

    -   **Schrijffilters voor Windows Embedded-apparaten**: Wanneer u software-updates op Windows Embedded-apparaten waarvoor schrijffilters ingeschakeld implementeren zijn, kunt u opgeven om de software-update op een tijdelijke overlay en de wijzigingen later installeren of de wijzigingen doorvoert tegen de installatiedeadline of tijdens een onderhoudsvenster. Wanneer u wijzigingen doorvoert tegen de installatiedeadline of tijdens een onderhoudsvenster, moet er opnieuw worden opgestart, zodat de wijzigingen behouden blijven op het apparaat.  

        > [!NOTE]  
        >  Wanneer u een software-update implementeert op een Windows Embedded-apparaat, moet u ervoor zorgen dat het apparaat lid is van een verzameling met een geconfigureerd onderhoudsvenster.  

7.  Configureer op de pagina waarschuwingen hoe Configuration Manager en System Center Operations Manager waarschuwingen voor deze implementatie genereren moeten.  

    > [!WARNING]  
    >  U kunt recente waarschuwingen met betrekking tot software-updates weergegeven in het knooppunt **Software-updates** in de werkruimte **Softwarebibliotheek** .  

8. Configureer de volgende instellingen op de pagina Downloadinstellingen:  

    - Geef op of de client de software-updates moet downloaden en installeren wanneer een client is verbonden met een langzaam netwerk of wanneer deze gebruikmaakt van een locatie terugvalinhoudlocatie.  

    - Geef op of de client de software-updates moet downloaden en installeren vanaf een terugvaldistributiepunt wanneer de inhoud voor de software-updates niet beschikbaar is op een voorkeursdistributiepunt.  

    - **Toestaan dat clients inhoud te delen met andere clients in hetzelfde subnet**: Geef op of het gebruik van BranchCache voor inhouddownloads inschakelen. Zie [Concepten voor inhoudsbeheer](../../core/plan-design/hierarchy/fundamental-concepts-for-content-management.md#branchcache) voor meer informatie over BranchCache.  

    - **Als software-updates niet beschikbaar is op het distributiepunt in de huidige, neighbor of site groepen, inhoud downloaden van Microsoft Updates**: Selecteer deze instelling clients die zijn verbonden met het intranet software-updates voor downloaden vanaf Microsoft Update als software-updates niet beschikbaar zijn op distributiepunten hebben. Clients op Internet gaat altijd u naar Microsoft Update voor de inhoud van software-updates.

    - Geef op of clients mogen downloaden na een installatiedeadline wanneer deze internetverbindingen met een datalimiet gebruiken. Internetproviders brengen soms de hoeveelheid gegevens die u verzendt en ontvangt in rekening wanneer u gebruikmaakt van een internetverbinding naar gebruik.  

    > [!NOTE]  
    > Clients vragen de inhoudlocatie aan bij het beheerpunt voor de software-updates in een implementatie. Het downloadgedrag is afhankelijk van hoe u het distributiepunt, implementatiepakket en de instellingen op deze pagina hebt geconfigureerd. Zie [Scenario's voor de locatie van inhoudsbronnen](../../core/plan-design/hierarchy/content-source-location-scenarios.md) voor meer informatie.  

Zie [Implementatieproces voor software-updates](../../sum/understand/software-updates-introduction.md#BKMK_DeploymentProcess) voor meer informatie over het implementatieproces.

## <a name="next-steps"></a>Volgende stappen
[Software-updates controleren](monitor-software-updates.md)
