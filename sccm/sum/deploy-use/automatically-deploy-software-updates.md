---
title: Software-updates automatisch implementeren
titleSuffix: Configuration Manager
description: Softwareupdates automatisch implementeren door nieuwe updates toe te voegen aan een updategroep die is gekoppeld aan een actieve implementatie of ADR's.
keywords: ''
author: mestew
ms.author: mstewart
manager: dougeby
ms.date: 03/22/2018
ms.topic: article
ms.prod: configuration-manager
ms.service: ''
ms.technology:
- configmgr-sum
ms.assetid: b27682de-adf8-4edd-9572-54886af8f7fb
ms.openlocfilehash: afa0bd21d23dc0be50d90452ad5dd5d909542279
ms.sourcegitcommit: 11bf4ed40ed0cbb10500cc58bbecbd23c92bfe20
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 03/23/2018
---
#  <a name="BKMK_AutoDeploy"></a> Software-updates automatisch implementeren  

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*

 U kunt een regel voor automatische implementatie (ADR) gebruiken in plaats van de nieuwe updates toe te voegen aan een bestaande software-updategroep. Normaal gesproken u ADR's gebruikt voor maandelijkse software-updates (bekend als updates van de Patch-dinsdag) implementeren en beheren van definitie-updates. Als u hulp nodig hebt om te bepalen welke implementatie methode is geschikt is voor u, raadpleegt u [software-updates implementeren](deploy-software-updates.md).

<!--##  <a name="BKMK_AddUpdatesToExistingGroup"></a> Add software updates to a deployed update group  
After you create and deploy a software update group, you can add software updates to the update group and they will be automatically deployed.  

> [!IMPORTANT]  
>  When you add software updates to an existing software update group that has already been deployed, it might take several minutes before the additional software updates are added to the deployment.  

Use the following procedure to add software updates to an existing update group.  

#### To add software updates to an existing software update group  

1.  In the Configuration Manager console, navigate to **Software Library** > **Overview** > **Software Updates**.  

2.  Select the software updates that are to be added to the new software update group.  

3.  On the **Home** tab, in the **Update** group, click **Edit Membership**.  

4.  Select the software update group to which you want to add the software updates as members.  

5.  Click the **Software Update Groups** node to display the software update group.  

6.  Click the software update group, and in the **Home** tab, in the **Update** group, click **Show Members** to display a list of the software updates in the group.  --mstewart this is already doc'd on the SUG page. -->

##  <a name="BKMK_CreateAutomaticDeploymentRule"></a> Een regel voor automatische implementatie (ADR) maken  
U kunt software-update automatisch goedkeuren en implementeren door gebruik te maken van een ADR. U kunt instellen dat met de regel software-updates worden toegevoegd aan een nieuwe software-updategroep elke keer dat de regel wordt uitgevoerd of u kunt software-updates laten toevoegen aan een bestaande groep. Wanneer een regel wordt uitgevoerd en software-updates worden toegevoegd aan een bestaande groep, wordt de regel alle updates verwijderd uit de groep en vervolgens de updates die voldoen aan de criteria die u aan de groep definieert toegevoegd. 

> [!WARNING]  
>  Voordat u voor het eerst een ADR maakt, moet u controleren of het synchroniseren van software-updates op de site is voltooid. Dit is belangrijk wanneer u Configuration Manager met een niet-Engelse taal uitvoert omdat software-updateclassificaties voorafgaande aan de eerste synchronisatie in het Engels weergegeven en worden weergegeven in de gelokaliseerde taal nadat software-update synchronisatie is voltooid. Regels die u maakt voordat u software-updates synchroniseert, werken mogelijk na het synchroniseren niet meer naar behoren omdat de teksttekenreeks niet langer overeenkomt.  

 Gebruik de volgende procedure om een ADR te maken.  

#### <a name="to-create-an-adr"></a>Een ADR maken  

1.  Navigeer in de Configuration Manager-console naar **softwarebibliotheek** **overzicht** > **Software-Updates** > **regels voor automatische implementatie**.  

2.  Klik op het tabblad **Start** in de groep **Maken** op **Regel voor automatische implementatie maken**. De wizard Regel voor automatische implementatie maken wordt geopend.  

3.  Configureer de volgende instellingen op de pagina **Algemeen** :  

    -   **Naam**: Geef de naam voor de ADR. De naam moet uniek zijn, het doel van de regel beschrijven en onderscheiden van andere gebruikers in de Configuration Manager-site.  

    -   **Beschrijving**: Geef een beschrijving voor de ADR. De beschrijving moet een overzicht van de implementatie en andere relevante informatie waarmee u kunt de regel onderscheiden van andere bieden. Het beschrijvingsveld is optioneel en kent een limiet van 256 tekens. Het veld is standaard leeg.  

    -   **Implementatiesjabloon selecteren**: Geef op of een eerder opgeslagen implementatiesjabloon moet worden toegepast. U kunt een implementatiesjabloon met meerdere algemene eigenschappen update-implementatie die kunnen worden gebruikt wanneer u ADR's maakt. Deze sjablonen helpen de consistentie met soortgelijke implementaties te garanderen en besparen tijd.  

         - U kunt via de wizard Regel voor automatische implementatie kiezen uit de ingebouwde implementatiesjablonen voor software-updates. De sjabloon **Definitie-updates** biedt algemene instellingen die u kunt gebruiken wanneer u definitiesoftware-updates implementeert. De sjabloon **Patch Tuesday** biedt algemene instellingen die u kunt gebruiken wanneer u software-updates implementeert op basis van een maandelijkse cyclus.  

    -   **Verzameling**: Hiermee geeft u de doelverzameling op die moet worden gebruikt voor de implementatie. Leden van de verzameling ontvangen de software-updates die in de implementatie zijn gedefinieerd.  

    -   Bepaal of u software-updates toevoegt aan een nieuwe of een bestaande software-updategroep. In de meeste gevallen kiest u waarschijnlijk voor het maken van een nieuwe software-updategroep wanneer de ADR wordt uitgevoerd. U kunt er echter voor kiezen om een bestaande groep uit te voeren als de regel wordt uitgevoerd volgens een agressievere planning. Als u de regel bijvoorbeeld dagelijks uitvoert voor definitie-updates, zou u de software-updates aan een bestaande software-updategroep kunnen toevoegen.  

    -   **De implementatie inschakelen nadat deze regel is uitgevoerd**: Geef op of de software-update-implementatie inschakelen nadat de ADR wordt uitgevoerd. Overweeg de volgende zaken met betrekking tot deze specificatie:  

        -   Wanneer u de implementatie inschakelt, worden de updates die voldoen aan de gedefinieerde criteria van de regel toegevoegd aan een software-updategroep. De inhoud van de software-update wordt gedownload zo nodig. De inhoud wordt gekopieerd naar de opgegeven distributiepunten en de updates worden geïmplementeerd op de clients in de doelverzameling.  

        -   Wanneer u de implementatie niet inschakelt, worden de updates die voldoen aan de gedefinieerde criteria van de regel toegevoegd aan een software-updategroep. Het beleid voor implementatie van software-updates is geconfigureerd. De updates worden echter niet gedownload of op clients geïmplementeerd. Deze situatie zorgt voor te bereiden op de updates implementeren, controleert u of de updates die voldoen aan de criteria toereikend zijn en schakel vervolgens de implementatie op een later tijdstip.  

4.  Configureer de volgende instellingen op de pagina Implementatie-instellingen:  

    -   **Wake-on-LAN gebruiken om clients voor vereiste implementaties te laten ontwaken**: Hiermee geeft u op of Wake On LAN tegen de deadline voor het verzenden van ontwaakpakketten naar computers waarvoor een of meer software-updates in de implementatie. Computers die zich in de slaapstandmodus deadline van de installatie zal worden geactiveerd, zodat de installatie kan worden gestart. Clients die zich in de slaapstandmodus bevinden en geen software-updates nodig hebben, worden niet gestart. Deze instelling is standaard uitgeschakeld. Voordat u deze optie kunt gebruiken, moeten computers en netwerken worden geconfigureerd voor Wake On LAN. 

    -   **Detailniveau**: Geef het detailniveau voor de statusberichten die zijn gerapporteerd door clientcomputers.  

        > [!IMPORTANT]  
        >  Wanneer u definitie-updates implementeert, stel het detailniveau op **alleen fouten** de client een statusbericht alleen rapporteren wanneer een definitie-update niet. Als u dat niet doet, rapporteert de client mogelijk een groot aantal statusberichten dat van invloed kan zijn op de prestaties van de site server.  

    -   **Instelling voor licentiebepalingen**: Geef op of voor de automatische implementatie van software-updates waaraan licentiebepalingen zijn gekoppeld. Sommige software-updates bevatten licentiebepalingen. Dit is bijvoorbeeld het geval bij een servicepack. Wanneer u software-updates automatisch implementeert, worden de licentiebepalingen niet weergegeven en wordt er geen mogelijkheid geboden om de licentiebepalingen te accepteren. U kunt automatisch implementeren alle software-updates, ongeacht bijbehorende licentiebepalingen of alleen updates implementeren die geen bijbehorende licentiebepalingen.  
        - Als u wilt de licentievoorwaarden voor software-update bekijken, kunt u de software-update in de **alle Software-Updates** knooppunt van de **softwarebibliotheek** werkruimte. Op de **Start** tabblad, in de **Update** groep, klikt u op **revisie licentie**.    
        - Als u wilt zoeken naar software-updates waaraan licentiebepalingen zijn gekoppeld, kunt u toevoegen de **licentievoorwaarden** kolom naar het deelvenster met resultaten in de **alle Software-Updates** knooppunt. Klik op de kolomkop klikken om de kolom te sorteren op de software-updates met licentiebepalingen.  

5.  Configureer op de pagina Software-updates de criteria voor de software-updates die via de ADR worden opgehaald en toegevoegd aan de software-updategroep. De limiet voor software-updates in de ADR is 1000 software-updates. Indien nodig, kunt u filteren op de grootte van de inhoud voor software-updates in de regels voor automatische implementatie. Zie voor meer informatie [Configuration Manager en vereenvoudigd onderhoud van Windows op omlaag niveau besturingssystemen](https://blogs.technet.microsoft.com/enterprisemobility/2016/10/07/configuration-manager-and-simplified-windows-servicing-on-down-level-operating-systems/).


6.  Geef op de pagina Evaluatieplanning op of de ADR moet worden ingeschakeld voor uitvoeren op basis van een planning. Wanneer dit is ingeschakeld, klikt u op **Aanpassen** om de terugkerende planning in te schakelen. De begintijdconfiguratie voor de planning is gebaseerd op de lokale tijd van de computer waarop de Configuration Manager-console.
    - De begintijdconfiguratie voor de planning is gebaseerd op de lokale tijd van de computer waarop de Configuration Manager-console.
    - De ADR-evaluatie kan twee tot drie keer per dag worden uitgevoerd.
    - De evaluatieplanning met een frequentie die langer is dan de synchronisatieplanning voor software-updates nooit zo worden ingesteld. De planning voor synchronisatie van software-update wordt weergegeven als u wilt bepalen van de frequentie van evaluatie van het schema. 
    - Als u de ADR handmatig wilt uitvoeren, selecteert u de regel en klikt u vervolgens op **Nu uitvoeren** op het tabblad **Start** in de groep **Regel voor automatische implementatie** .
    
       > [!NOTE]  
       >Vanaf Configuration Manager versie 1802, worden ADR's gepland om te evalueren verschuiving ten opzichte van een base dag. Dit betekent dat als patch dinsdag daadwerkelijk op woensdag voor u valt, worden de evaluatieplanning ingesteld voor de tweede dinsdag van de verschuiving van de maand op één dag. <!--1357133-->
       > - Bij het plannen van de evaluatie om te worden uitgevoerd met een offset tijdens de laatste week van de maand wordt de evaluatie gepland voor de laatste dag van de maand als de verschuiving van de gekozen loopt over in de volgende maand. <!--506731-->

       > ![ADR evaluatie van de aangepaste planning offset van base dag](./media/ADR-evaluation-schedule-offset.PNG)

   
7.  Configureer de volgende instellingen op de pagina Implementatieplanning:  

    -   **Evaluatie van planning**: Geef aan of Configuration Manager de beschikbare tijd en de tijdstippen voor de installatiedeadline evalueert op basis van UTC of van de lokale tijd van de computer waarop de Configuration Manager-console.  
         - Als u lokale tijd selecteert en selecteer vervolgens **zo snel mogelijk** voor de **tijd Software beschikbaar** of **installatiedeadline**, de huidige tijd op de computer die de Configuration Manager-console wordt gebruikt om te evalueren wanneer updates beschikbaar zijn of wanneer ze worden geïnstalleerd op een client wordt uitgevoerd. Als de client zich in een andere tijdzone bevindt, worden deze acties uitgevoerd wanneer de tijd van de client de evaluatietijd heeft bereikt.  

    -   **Tijd software beschikbaar**: Selecteer een van de volgende instellingen op te geven wanneer de software-updates beschikbaar voor clients zijn:  

        -   **Zo spoedig mogelijk**: De software-updates die zijn opgenomen in de implementatie beschikbaar voor de clientcomputers zo snel mogelijk maakt. Wanneer u de implementatie met deze instelling is ingeschakeld maakt, wordt in Configuration Manager het clientbeleid bijgewerkt. Op het volgende clientbeleid pollingcyclus clients zich bewust zijn van de implementatie en de beschikbare updates voor de installatie kunnen verkrijgen.  

        -   **Specifiek tijdstip**: Hiermee kunt u software-updates die zijn opgenomen in de implementatie op een specifieke datum en tijd beschikbaar is op clientcomputers. Wanneer u de implementatie met deze instelling is ingeschakeld maakt, wordt in Configuration Manager het clientbeleid bijgewerkt. Clients detecteren de implementatie vervolgens gedurende de volgende pollingcyclus van het clientbeleid. De software-updates in de implementatie zijn echter pas na de geconfigureerde datum en het geconfigureerde tijdstip beschikbaar voor installatie.  

    -   **Installatiedeadline**: Selecteer een van de volgende instellingen om op te geven van de installatiedeadline voor de software-updates in de implementatie:  

        -   **Zo spoedig mogelijk**: Selecteer deze instelling om de software-updates in de implementatie zo spoedig mogelijk automatisch worden geïnstalleerd.  

        -   **Specifiek tijdstip**: Selecteer deze instelling om de software-updates in de implementatie op een specifieke datum en tijd automatisch worden geïnstalleerd. Configuration Manager bepaalt de deadline voor het installeren van software-updates door het geconfigureerde **specifiek tijdstip** interval voor de **tijd Software beschikbaar**.  

            - Het daadwerkelijke deadlinetijdstip is het weergegeven deadlinetijdstip plus een willekeurige hoeveelheid tijd tot twee uur. De willekeurige worden de mogelijke gevolgen van clientcomputers in de verzameling voor het installeren van updates in de implementatie op hetzelfde moment.  
          
             - U kunt de **Computeragent** -clientinstelling **Willekeurig toepassen van deadline uitschakelen** configureren om de willekeurige installaties voor vereiste software-updates uit te schakelen. Zie [Computeragent](../../core/clients/deploy/about-client-settings.md#computer-agent) voor meer informatie.  

8. Configureer de volgende instellingen op de pagina Gebruikerservaring:  

    -   **Meldingen voor gebruikers**: Geef op of meldingen van de software-updates weergeven in Software Center op de clientcomputer op de geconfigureerde **tijd Software beschikbaar** en of meldingen voor gebruikers weergegeven op de clientcomputers.  

    -   **Deadlinegedrag**: Geef het gedrag op dat moet worden vertoond als de deadline voor de implementatie van de software-update wordt bereikt. Geef op of de software-updates in de implementatie moeten worden geïnstalleerd. Geef ook op of het systeem na het installeren van software-updates opnieuw moet worden opgestart, ongeacht het geconfigureerde onderhoudsvenster. Zie voor meer informatie over onderhoudsvensters [het gebruik van onderhoudsvensters](../../core/clients/manage/collections/use-maintenance-windows.md).  

    -   **Gedrag voor opnieuw opstarten apparaat**: Geef op of onderdrukken van opnieuw opstarten van servers en werkstations als een herstart vereist is om update-installatie te voltooien.  

        > [!WARNING]  
        >  Het onderdrukken van het opnieuw opstarten van het systeem kan nuttig zijn in serveromgevingen of in andere gevallen waarin u wilt dat de computers die de software-updates installeren, niet standaard opnieuw worden opgestart. Dit kan er echter toe leiden dat computers zich in een onbeveiligde toestand bevinden. Het toestaan van afgedwongen opnieuw opstarten garandeert onmiddellijke voltooiing van de installatie van software-updates.  

    -   **Schrijffilters voor Windows Embedded-apparaten**: Wanneer u software-updates op Windows Embedded-apparaten waarvoor schrijffilters ingeschakeld implementeren zijn, kunt u opgeven om de software-update op een tijdelijke overlay en de wijzigingen later installeren of de wijzigingen doorvoert tegen de installatiedeadline of tijdens een onderhoudsvenster. Wanneer u wijzigingen doorvoert tegen de installatiedeadline of tijdens een onderhoudsvenster, moet er opnieuw worden opgestart, zodat de wijzigingen behouden blijven op het apparaat.  

           -  Wanneer u een software-update op een Windows Embedded-apparaat implementeert, zorg er dan voor dat het apparaat is lid van een verzameling met een geconfigureerd onderhoudsvenster.  

    - **Implementatiegedrag voor nieuwe evaluatie bij het opnieuw opstarten van software-updates**: Selecteer deze instelling om software-updates implementaties configureren zodat clients software-updates zijn geïnstalleerd en opnieuw opgestart een nalevingsscan voor software-updates uitvoeren onmiddellijk na een client. Deze instelling schakelt u de client om te controleren op aanvullende updates de client opnieuw is opgestart nadat, installeert u ze tijdens datzelfde onderhoudsvenster.

9. Configureer op de pagina waarschuwingen hoe Configuration Manager en System Center Operations Manager waarschuwingen voor deze implementatie genereren moeten. U kunt recente waarschuwingen met betrekking tot software-updates weergegeven in het knooppunt **Software-updates** in de werkruimte **Softwarebibliotheek** .  

10. Configureer de volgende instellingen op de pagina Downloadinstellingen:  

    - Opgeven of clients moeten downloaden en installeren van de updates wanneer ze zijn verbonden met een traag netwerk of met behulp van een locatie terugvalinhoudlocatie.  

    - Geef op of clients downloaden en installeren van de software-updates van een terugvaldistributiepunt wanneer de inhoud voor de software-updates niet beschikbaar op een voorkeursdistributiepunt is.  

    - **Toestaan dat clients inhoud te delen met andere clients in hetzelfde subnet**: Geef op of het gebruik van BranchCache voor inhouddownloads inschakelen. Zie [Concepten voor inhoudsbeheer](../../core/plan-design/hierarchy/fundamental-concepts-for-content-management.md#branchcache) voor meer informatie over BranchCache.  

    - **Als software-updates niet beschikbaar is op het distributiepunt in de huidige, neighbor of site groepen, inhoud downloaden van Microsoft Updates**: Selecteer deze instelling intranet verbonden clients software-updates downloaden vanaf Microsoft Update als er updates zijn niet beschikbaar zijn op distributiepunten hebben. Clients op Internet gaat altijd u naar Microsoft Update voor de inhoud van software-updates.

    - Geef op of clients mogen downloaden na een installatiedeadline wanneer deze internetverbindingen met een datalimiet gebruiken. Internetproviders brengen soms de hoeveelheid gegevens die u verzendt en ontvangt in rekening wanneer u gebruikmaakt van een internetverbinding naar gebruik.  

    > [!NOTE]  
    >  Clients vragen de inhoudlocatie aan bij het beheerpunt voor de software-updates in een implementatie. Het downloadgedrag is afhankelijk van hoe u het distributiepunt, implementatiepakket en de instellingen op deze pagina hebt geconfigureerd. Zie [Scenario's voor de locatie van inhoudsbronnen](../../core/plan-design/hierarchy/content-source-location-scenarios.md) voor meer informatie.  

11. Selecteer op de pagina Implementatiepakket een bestaand implementatiepakket of configureer de volgende instellingen voor het maken van een nieuw implementatiepakket:  

    1.  **Naam**: Geef de naam van het implementatiepakket. Gebruik een unieke naam zijn die de pakketinhoud beschrijft. Er kunnen maximaal 50 tekens worden ingevoerd.  

    2.  **Beschrijving**: Geef een beschrijving die informatie over het implementatiepakket biedt. De beschrijving mag niet langer zijn dan 127 tekens.  

    3.  **Pakketbron**: Hiermee geeft u de locatie van de bronbestanden voor software-update.  Typ een netwerkpad voor de bronlocatie, zoals **\\\\server\sharenaam\pad**, of klik op **Bladeren** en ga naar de netwerklocatie. De gedeelde map maken voor bronbestanden van het installatiepakket voordat u naar de volgende pagina doorgaat.  

        - De bronlocatie van de implementatie van pakket opgegeven kan niet worden gebruikt door een ander software-installatiepakket.
        - U kunt de pakketbronlocatie in de eigenschappen van het installatiepakket wijzigen nadat Configuration Manager het implementatiepakket maakt. Maar als u dit doet, moet u eerst de inhoud van de oorspronkelijke pakketbron kopiëren naar de nieuwe pakketbronlocatie  
        -  Het computeraccount van de SMS-provider en de gebruiker die de wizard uitvoert voor het downloaden van de software-updates, moeten over NTFS-machtigingen voor **schrijven** op de downloadlocatie beschikken. U moet de toegang tot de downloadlocatie zorgvuldig beperken om het risico op kwaadwillenden die met bronbestanden van de software-update knoeien, te reduceren.  
       

    4.  **Prioriteit voor verzenden**: Geef de prioriteit voor verzenden voor het implementatiepakket. Configuration Manager gebruikt de prioriteit voor verzenden voor het implementatiepakket wanneer het pakket naar distributiepunten wordt verzonden. Installatiepakketten worden in volgorde van prioriteit verzonden: Hoog, Gemiddeld of laag. Pakketten met een identieke prioriteit worden verzonden in de volgorde waarin deze zijn gemaakt. Als er geen achterstand is, wordt het pakket onmiddellijk verwerkt, ongeacht de prioriteit van het pakket.  

12. Geef op de pagina Distributiepunten de distributiepunten of distributiepuntgroepen op die als host zullen fungeren voor de software-updatebestanden. Zie [Configuraties van het distributiepunt](../../core/servers/deploy/configure/install-and-configure-distribution-points.md#bkmk_configs) voor meer informatie over distributiepunten. Deze pagina is alleen beschikbaar wanneer u een nieuw implementatiepakket voor software-updates maakt.
  

13. Geef op de pagina Downloadlocatie op of de software-updatebestanden moeten worden gedownload vanaf internet of vanaf uw lokale netwerk. Configureer de volgende instellingen:  

    -   **Software-updates downloaden vanaf Internet**: Selecteer deze instelling om de software-updates downloaden vanaf een opgegeven locatie op Internet. Deze instelling is standaard ingeschakeld.  

    -   **Software-updates downloaden vanaf een locatie op het lokale netwerk**: Selecteer deze instelling om de softwareupdates downloaden vanaf een lokale map of gedeelde map. Deze instelling is nuttig wanneer de computer waarop de wizard wordt uitgevoerd, geen toegang tot internet heeft. Computers met internettoegang kunnen software-updates voortijdig downloaden en deze opslaan op een locatie op het lokale netwerk die toegankelijk is vanaf de computer waarop de wizard wordt uitgevoerd.  

14. Selecteer de talen waarvoor de geselecteerde software-updates worden gedownload op de pagina Taal selecteren. De software-updates worden alleen gedownload als deze beschikbaar zijn in de geselecteerde talen. Software-updates die niet aan een specifieke taal zijn gebonden, worden altijd gedownload. De wizard selecteert standaard de talen die u hebt geconfigureerd in de eigenschappen van het software-updatepunt. Er moet ten minste één taal worden geselecteerd voordat u doorgaat naar de volgende pagina. Wanneer u alleen talen selecteert die niet worden ondersteund door een software-update, mislukt het downloaden van de update.  

15. Controleer de instellingen op de pagina Overzicht. U kunt de instellingen opslaan naar een implementatiesjabloon, op **opslaan als sjabloon**. Voer een naam in en selecteer de instellingen die u wilt opnemen in de sjabloon en klik vervolgens op **opslaan**. Als u een geconfigureerde instelling wilt wijzigen, klikt u op de gekoppelde wizardpagina en wijzigt u de instelling.  
    -  De sjabloonnaam mag alfanumerieke ASCII-tekens en de tekens **\\** (backslash) en **‘** (apostrof) bevatten.  

16. Klik op **Volgende** om de ADR te maken.  

 Nadat u de wizard hebt voltooid, wordt de ADR uitgevoerd. Dit wordt de software-updates die voldoen aan de opgegeven criteria voor een software-updategroep toevoegen. Vervolgens wordt de ADR downloadt de updates naar de Inhoudsbibliotheek op de siteserver en distribueert ze naar de geconfigureerde distributiepunten. De ADR implementeert vervolgens de software-updategroep voor clients in de doelverzameling.  

##  <a name="BKMK_AddDeploymentToADR"></a> Nieuwe implementaties aan een bestaande ADR toevoegen  
 Nadat u een regel voor automatische implementatie hebt gemaakt, kunt u aanvullende implementaties aan de regel toevoegen. Dit kan helpen bij het beheren van de complexiteit van het implementeren van verschillende updates voor verschillende verzamelingen. Elke nieuwe implementatie heeft alle functionaliteit en biedt de volledige implementatiebewakingservaring.  

#### <a name="to-add-a-new-deployment-to-an-existing-adr"></a>Een nieuwe implementatie aan een bestaande ADR toevoegen  

1.  Navigeer in de Configuration Manager-console naar **softwarebibliotheek** > **overzicht** > **Software-Updates** > **regels voor automatische implementatie**, en selecteer vervolgens de gewenste regel.  

2.  Klik op het tabblad **Start** in de groep **Regels voor automatische implementatie** op **Implementatie toevoegen**. De wizard Implementatie toevoegen wordt geopend.  

3.  Configureer op het tabblad **Verzameling** de volgende instellingen:  

    -   **Verzameling**: Hiermee geeft u de doelverzameling op die moet worden gebruikt voor de implementatie. Leden van de verzameling ontvangen de software-updates die in de implementatie zijn gedefinieerd.  

    -   **De implementatie inschakelen nadat deze regel is uitgevoerd**: Geef op of de software-update-implementatie inschakelen nadat de ADR wordt uitgevoerd. Overweeg de volgende zaken met betrekking tot deze specificatie:  

        -   Wanneer u de implementatie inschakelt, worden de updates die voldoen aan de gedefinieerde criteria van de regel toegevoegd aan een software-updategroep. De inhoud van de software-update wordt gedownload zo nodig. De inhoud wordt gekopieerd naar de opgegeven distributiepunten en de updates worden geïmplementeerd op de clients in de doelverzameling.  

        -  Wanneer u de implementatie niet inschakelt, worden de updates die voldoen aan de gedefinieerde criteria van de regel toegevoegd aan een software-updategroep. Het beleid voor implementatie van software-updates is geconfigureerd. De updates worden echter niet gedownload of op clients geïmplementeerd. Deze situatie zorgt voor te bereiden op de updates implementeren, controleert u of de updates die voldoen aan de criteria toereikend zijn en schakel vervolgens de implementatie op een later tijdstip.  

4.  Configureer de volgende instellingen op de pagina Implementatie-instellingen:  

    -   **Wake-on-LAN gebruiken om clients voor vereiste implementaties te laten ontwaken**: Hiermee geeft u op of Wake On LAN tegen de deadline voor het verzenden van ontwaakpakketten naar computers waarvoor een of meer software-updates in de implementatie. Computers die zich in de slaapstandmodus deadline van de installatie zal worden geactiveerd, zodat de installatie kan worden gestart. Clients die zich in de slaapstandmodus bevinden en geen software-updates nodig hebben, worden niet gestart. Deze instelling is standaard uitgeschakeld. Voordat u deze optie kunt gebruiken, moeten computers en netwerken worden geconfigureerd voor Wake On LAN.  

    -   **Detailniveau**: Geef het detailniveau voor de statusberichten die zijn gerapporteerd door clientcomputers.  

        > [!IMPORTANT]  
        >  Stel, wanneer u definitie-updates implementeert, het detailniveau in op **Alleen fouten** als u wilt dat clients alleen statusberichten rapporteren wanneer een definitie-update niet bij de client wordt bezorgd. Als u dat niet doet, rapporteert de client mogelijk een groot aantal statusberichten dat van invloed kan zijn op de prestaties van de site server.  

5.  Configureer de volgende instellingen op de pagina Implementatieplanning:  

    -   **Evaluatie van planning**: Geef aan of Configuration Manager de beschikbare tijd en de tijdstippen voor de installatiedeadline evalueert op basis van UTC of van de lokale tijd van de computer waarop de Configuration Manager-console.  

           -  Als u lokale tijd selecteert en selecteer vervolgens **zo snel mogelijk** voor de **tijd Software beschikbaar** of **installatiedeadline**, de huidige tijd op de computer die de Configuration Manager-console wordt gebruikt om te evalueren wanneer updates beschikbaar zijn of wanneer ze worden geïnstalleerd op een client wordt uitgevoerd. Als de client zich in een andere tijdzone bevindt, worden deze acties uitgevoerd wanneer de tijd van de client de evaluatietijd heeft bereikt.  

    -   **Tijd software beschikbaar**: Selecteer een van de volgende instellingen op te geven wanneer de software-updates beschikbaar voor clients zijn:  

        -   **Zo spoedig mogelijk**: Selecteer deze instelling om de softwareupdates die zijn opgenomen in de implementatie beschikbaar voor de clientcomputers zo snel mogelijk. Wanneer u de implementatie met deze instelling is ingeschakeld maakt, wordt in Configuration Manager het clientbeleid bijgewerkt. Op het volgende clientbeleid pollingcyclus clients zich bewust zijn van de implementatie en de beschikbare updates voor de installatie kunnen verkrijgen.  

        -   **Specifiek tijdstip**: Hiermee kunt u software-updates die zijn opgenomen in de implementatie op een specifieke datum en tijd beschikbaar is op clientcomputers. Wanneer u de implementatie met deze instelling is ingeschakeld maakt, wordt in Configuration Manager het clientbeleid bijgewerkt. Clients detecteren de implementatie vervolgens gedurende de volgende pollingcyclus van het clientbeleid. De software-updates in de implementatie zijn echter pas na de geconfigureerde datum en het geconfigureerde tijdstip beschikbaar voor installatie. 

    -   **Installatiedeadline**: Selecteer een van de volgende instellingen om op te geven van de installatiedeadline voor de software-updates in de implementatie:  

        -   **Zo spoedig mogelijk**: Selecteer deze instelling om de software-updates in de implementatie zo spoedig mogelijk automatisch worden geïnstalleerd.  

        -   **Specifiek tijdstip**: Selecteer deze instelling om de software-updates in de implementatie op een specifieke datum en tijd automatisch worden geïnstalleerd. Configuration Manager bepaalt de deadline voor het installeren van software-updates door het geconfigureerde **specifiek tijdstip** interval voor de **tijd Software beschikbaar**.  

               - Het daadwerkelijke deadlinetijdstip is het weergegeven deadlinetijdstip plus een willekeurige hoeveelheid tijd tot twee uur. Hierdoor worden de mogelijke gevolgen van clientcomputers in de verzameling voor het installeren van updates in de implementatie op hetzelfde moment.  
              - U kunt de **Computeragent** -clientinstelling **Willekeurig toepassen van deadline uitschakelen** configureren om de willekeurige installaties voor vereiste software-updates uit te schakelen. Zie [Computeragent](../../core/clients/deploy/about-client-settings.md#computer-agent) voor meer informatie.  

6.  Configureer de volgende instellingen op de pagina Gebruikerservaring:  

    -   **Meldingen voor gebruikers**: Geef op of meldingen van de software-updates weergeven in Software Center op de clientcomputer op de geconfigureerde **tijd Software beschikbaar** en of meldingen voor gebruikers weergegeven op de clientcomputers.  

    -   **Deadlinegedrag**: Geef het gedrag op dat moet worden vertoond als de deadline voor de implementatie van de software-update wordt bereikt. Geef op of de software-updates in de implementatie moeten worden geïnstalleerd. Geef ook op of het systeem na het installeren van software-updates opnieuw moet worden opgestart, ongeacht het geconfigureerde onderhoudsvenster. Zie voor meer informatie over onderhoudsvensters [het gebruik van onderhoudsvensters](../../core/clients/manage/collections/use-maintenance-windows.md).  

    -   **Gedrag voor opnieuw opstarten apparaat**: Geef op of onderdrukken van opnieuw opstarten van servers en werkstations als een herstart vereist is om update-installatie te voltooien.  
 
           > [!WARNING]  
           >  Het onderdrukken van het opnieuw opstarten van het systeem kan nuttig zijn in serveromgevingen of in andere gevallen waarin u wilt dat de computers die de software-updates installeren, niet standaard opnieuw worden opgestart. Dit kan er echter toe leiden dat computers zich in een onbeveiligde toestand bevinden. Het toestaan van afgedwongen opnieuw opstarten garandeert onmiddellijke voltooiing van de installatie van software-updates.  

    - **Schrijffilters voor Windows Embedded-apparaten**: Wanneer u software-updates op Windows Embedded-apparaten waarvoor schrijffilters ingeschakeld implementeren zijn, kunt u opgeven om de software-update op een tijdelijke overlay en de wijzigingen later installeren of de wijzigingen doorvoert tegen de installatiedeadline of tijdens een onderhoudsvenster. Wanneer u wijzigingen doorvoert tegen de installatiedeadline of tijdens een onderhoudsvenster, moet er opnieuw worden opgestart, zodat de wijzigingen behouden blijven op het apparaat.  

        - Wanneer u een software-update implementeert op een Windows Embedded-apparaat, moet u ervoor zorgen dat het apparaat lid is van een verzameling met een geconfigureerd onderhoudsvenster.  

7.  Configureer op de pagina waarschuwingen hoe Configuration Manager en System Center Operations Manager waarschuwingen voor deze implementatie genereren moeten. U kunt recente waarschuwingen met betrekking tot software-updates weergegeven in het knooppunt **Software-updates** in de werkruimte **Softwarebibliotheek** .  

8. Configureer de volgende instellingen op de pagina Downloadinstellingen:  

    - Opgeven of clients moeten downloaden en installeren van de software-updates wanneer ze zijn verbonden met een traag netwerk of met behulp van een locatie terugvalinhoudlocatie.  

    - Geef op of de client de software-updates moet downloaden en installeren vanaf een terugvaldistributiepunt wanneer de inhoud voor de software-updates niet beschikbaar is op een voorkeursdistributiepunt.  

    - **Toestaan dat clients inhoud te delen met andere clients in hetzelfde subnet**: Geef op of het gebruik van BranchCache voor inhouddownloads inschakelen. Zie [Concepten voor inhoudsbeheer](../../core/plan-design/hierarchy/fundamental-concepts-for-content-management.md#branchcache) voor meer informatie over BranchCache.  

    - **Als software-updates niet beschikbaar is op het distributiepunt in de huidige, neighbor of site groepen, inhoud downloaden van Microsoft Updates**: Selecteer deze instelling intranet verbonden clients software-updates downloaden vanaf Microsoft Update als er updates zijn niet beschikbaar zijn op distributiepunten hebben. Clients op Internet gaat altijd u naar Microsoft Update voor de inhoud van software-updates.

    - Geef op of clients mogen downloaden na een installatiedeadline wanneer deze internetverbindingen met een datalimiet gebruiken. Internetproviders brengen soms de hoeveelheid gegevens die u verzendt en ontvangt in rekening wanneer u gebruikmaakt van een internetverbinding naar gebruik.  

    > [!NOTE]  
    > Clients vragen de inhoudlocatie aan bij het beheerpunt voor de software-updates in een implementatie. Het downloadgedrag is afhankelijk van hoe u het distributiepunt, implementatiepakket en de instellingen op deze pagina hebt geconfigureerd. Zie [Scenario's voor de locatie van inhoudsbronnen](../../core/plan-design/hierarchy/content-source-location-scenarios.md) voor meer informatie.  

Zie [Implementatieproces voor software-updates](../../sum/understand/software-updates-introduction.md#BKMK_DeploymentProcess) voor meer informatie over het implementatieproces.

## <a name="next-steps"></a>Volgende stappen
[Software-updates controleren](monitor-software-updates.md)
