---
title: Software-updates handmatig implementeren
titleSuffix: Configuration Manager
description: Voor de implementatie updates handmatig updates selecteren in de Configuration Manager-console en handmatig implementeren, of -updates toevoegen aan een updategroep en de groep implementeren.
keywords: 
author: dougeby
ms.author: dougeby
manager: angrobe
ms.date: 12/07/2016
ms.topic: article
ms.prod: configuration-manager
ms.service: 
ms.technology: configmgr-sum
ms.assetid: 57184274-5fea-4d79-a2b4-22e08ed26daf
ms.openlocfilehash: becab57c5f04bb67512d665175038f6c477b65b1
ms.sourcegitcommit: e13bb2c86c40a88e5f4602beb1d31e4adc90e099
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 01/12/2018
---
#  <a name="BKMK_ManualDeploy"></a> Software-updates handmatig implementeren  

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*

 Een handmatige software-update-implementatie is het proces van het selecteren van software-updates in de Configuration Manager-console en het handmatig starten van het implementatieproces. Of u kunt geselecteerde software-updates toevoegen aan een updategroep en de updategroep vervolgens handmatig implementeren. Gewoonlijk gebruikt u handmatige implementatie om uw clientapparaten up-to-date te krijgen met vereiste software-updates voordat u ADR's maakt die lopende maandelijkse software-update-implementaties zullen beheren. U zult ook een handmatige methode gebruiken om buiten-bandsoftware-updates te implementeren. Als u hulp nodig hebt om te bepalen welke implementatie methode is geschikt is voor u, raadpleegt u [software-updates implementeren](deploy-software-updates.md).

 De volgende secties behandelen de stappen voor het software-updates handmatig implementeren.  

##  <a name="BKMK_1SearchCriteria"></a>Stap 1: Geef zoekcriteria voor software-updates  
 Er worden mogelijk duizenden software-updates weergegeven in de Configuration Manager-console. De eerste stap in de werkstroom voor het handmatig implementeren van software-updates is het identificeren van de software-updates die u wilt implementeren. U zou bijvoorbeeld criteria kunnen opgeven die alle software-updates ophalen die vereist zijn op meer dan 50 clientapparaten en die een software-updateclassificatie **Beveiliging** of **Kritiek** hebben.  

> [!IMPORTANT]  
>  Het maximum aantal software-updates dat in een enkele software-update-implementatie kan worden opgenomen, bedraagt 1000.  

#### <a name="to-specify-search-criteria-for-software-updates"></a>Zoekcriteria voor software-updates geven  

1.  Klik in de Configuration Manager-console op **Softwarebibliotheek**.  

2.  Vouw in de werkruimte Softwarebibliotheek het knooppunt **Software-updates**uit en klik op **Alle software-updates**. De gesynchroniseerde software-updates worden weergegeven.  

    > [!NOTE]  
    >  Op de **alle Software-Updates** Configuration Manager-knooppunt geeft alleen software-updates met een **Kritiek** en **beveiliging** classificatie en in de afgelopen 30 dagen zijn uitgebracht.  

3.  Filter in het zoekvenster om de software-updates te identificeren die u nodig hebt met behulp van een of beide van de volgende stappen:  

    -   Typ in het zoekvenster een zoekstring die de software-updates zal filteren. Typ bijvoorbeeld de artikel-id of bulletin-id voor een specifieke software-update, of geef een string in die in de titel voor verschillende software-updates zou voorkomen.  

    -   Klik op **Criteria toevoegen**, selecteer de criteria die u wilt gebruiken om software-updates te filteren, klik op **Toevoegen**en geef dan de waarden op voor de criteria.  

4.  Klik op **Zoeken** om de software-updates te filteren.  

    > [!TIP]  
    >  U hebt de optie de filtercriteria op te slaan op het tabblad **Zoeken** en in de groep **Opslaan** .  

##  <a name="BKMK_2UpdateGroup"></a>Stap 2: Maken van een software-updategroep die de software-updates bevat  
 Software-updategroepen bieden u een doeltreffende methode om software-updates te organiseren die worden voorbereid voor implementatie. U kunt handmatig een software-updates aan een software-updategroep of Configuration Manager kunnen softwareupdates automatisch toevoegen aan een nieuwe of bestaande software-updategroep met behulp van een ADR toevoegen. Gebruik de volgende procedures om software-updates handmatig toe te voegen aan een nieuwe software-updategroep.  

#### <a name="to-manually-add-software-updates-to-a-new-software-update-group"></a>Software-updates handmatig toevoegen aan een nieuwe software-updategroep  

1.  Klik in de Configuration Manager-console op **Softwarebibliotheek**.  

2.  Klik in de werkruimte Softwarebibliotheek op **Software-updates**.  

3.  Selecteer de software-updates die aan de nieuwe software-updategroep moeten worden toegevoegd.  

4.  Klik op het tabblad **Start** in de groep **Update** op **Software-updategroep maken**.  

5.  Geef de naam voor de software-updategroep en geef optioneel een beschrijving. Gebruik een naam en beschrijving die voldoende informatie geven aan u om te bepalen welk type software-updates er in de software-updategroep zitten. Als u wilt doorgaan, klikt u op **Maken**.  

6.  Klik op het knooppunt **Software-updategroepen** om de nieuwe software-updategroep te tonen.  

7.  Selecteer de software-updategroep en klik op het tabblad **Start** in de groep **Update** op **Leden tonen** om een lijst van de software-updates te tonen die in de groep zijn opgenomen.  

##  <a name="BKMK_3DownloadContent"></a>Stap 3: De inhoud voor de software-updategroep downloaden  
 Voordat u de software-updates implementeert, kunt u optioneel de inhoud voor de software-updates downloaden die in de software-updategroep zijn opgenomen. U kunt ervoor kiezen dit te doen zodat u kunt controleren of de inhoud beschikbaar is op de distributiepunten voordat u de software-updates implementeert. Dit zal u helpen enige onverwachte problemen met de inhoudsbibliotheek te vermijden. U kunt deze stap overslaan en de inhoud zal worden gedownload en gekopieerd naar de distributiepunten als deel van het implementatieproces. Gebruik de volgende procedure om de inhoud voor software-updates in de software-updategroep te downloaden.  



#### <a name="to-download-content-for-the-software-update-group"></a>Inhoud voor de software-updategroep downloaden
[!INCLUDE[downloadupdates](..\includes\downloadupdates.md)]
<!--- 1.  In the Configuration Manager console, click **Software Library**.  

2.  In the Software Library workspace, expand **Software Updates**, and click **Software Update Groups**.  

3.  Select the software update group for which you want to download content.  

4.  On the **Home** tab, in the **Update Group** group, click **Download**. The **Download Software Updates Wizard** opens.  

5.  On the **Deployment Package** page, configure the following settings:  

    1.  **Select deployment package**: Select this setting to use an existing deployment package for the software updates in the deployment.  

        > [!NOTE]  
        >  Software updates that have already been downloaded to the selected deployment package are not downloaded again.  

    2.  **Create a new deployment package**: Select this setting to create a new deployment package for the software updates in the deployment. Configure the following settings:  

        -   **Name**: Specifies the name of the deployment package. This must be a unique name that describes the package content. It is limited to 50 characters.  

        -   **Description**: Specifies the description of the deployment package. The package description provides information about the package contents and is limited to 127 characters.  

        -   **Package source**: Specifies the location of the software update source files.  Type a network path for the source location, for example, **\\\server\sharename\path**, or click **Browse** to find the network location. You must create the shared folder for the deployment package source files before you proceed to the next page.  

            > [!NOTE]  
            >  The deployment package source location that you specify cannot be used by another software deployment package.  

            > [!IMPORTANT]  
            >  The SMS Provider computer account and the user that is running the wizard to download the software updates must both have **Write** NTFS permissions on the download location. You should carefully restrict access to the download location in order to reduce the risk of attackers tampering with the software update source files.  

            > [!IMPORTANT]  
            >  You can change the package source location in the deployment package properties after Configuration Manager creates the deployment package. But if you do so, you must first copy the content from the original package source to the new package source location.  

     Click **Next**.  

6.  On the Distribution Points page, select the distribution points or distribution point groups that are used to host the software update files defined in the new deployment package, and then click **Next**.  

7.  On the Distribution Settings page, specify the following settings:  

    -   **Distribution priority**: Use this setting to specify the distribution priority for the deployment package. The distribution priority applies when the deployment package is sent to distribution points at child sites. Distribution packages are sent in priority order: **High**, **Medium**, or **Low**. Packages with identical priorities are sent in the order in which they were created. If there is no backlog, the package will process immediately regardless of its priority. By default, packages are sent using **Medium** priority.  

    -   **Distribute the content for this package to preferred distribution points**: Use this setting to enable on-demand content distribution to preferred distribution points. When this setting is enabled, the management point creates a trigger for the distribution manager to distribute the content to all preferred distribution points when a client requests the content for the package and the content is not available on any preferred distribution points. For more information about preferred distribution points and on-demand content, see [Content source location scenarios](../../core/plan-design/hierarchy/fundamental-concepts-for-content-management.md#bkmk_CSLscenarios).  

    -   **Prestaged distribution point settings**: Use this setting to specify how you want to distribute content to prestaged distribution points. Choose one of the following options:  

        -   **Automatically download content when packages are assigned to distribution points**: Use this setting to ignore the prestage settings and distribute content to the distribution point.  

        -   **Download only content changes to the distribution point**: Use this setting to prestage the initial content to the distribution point, and then distribute content changes to the distribution point.  

        -   **Manually copy the content in this package to the distribution point**: Use this setting to always prestage content on the distribution point. This is the default setting.  

         For more information about prestaging content to distribution points, see [Use Prestaged content](../../core/servers/deploy/configure/deploy-and-manage-content.md#bkmk_prestage).  

     Click **Next**.  

8.  On the Download Location page, specify location that Configuration Manager will use to download the software update source files. As needed, use the following options:  

    -   **Download software updates from the Internet**: Select this setting to download the software updates from the location on the Internet. This is the default setting.  

    -   **Download software updates from a location on the local network**: Select this setting to download software updates from a local folder or shared network folder. Use this setting when the computer running the wizard does not have Internet access.  

        > [!NOTE]  
        >  When you use this setting, download the software updates from any computer with Internet access, and then copy the software updates to a location on the local network that is accessible from the computer running the wizard.  

     Click **Next**.  

9. On the Language Selection page, specify the languages for which the selected software updates are to be downloaded, and then click **Next**. Configuration Manager downloads the software updates only if they are available in the selected languages. Software updates that are not language-specific are always downloaded.  

10. On the Summary page, verify the settings that you selected in the wizard, and then click **Next** to download the software updates.  

11. On the Completion page, verify that the software updates were successfully downloaded, and then click **Close**. --->

#### <a name="to-monitor-content-status"></a>De status van inhoud controleren
1. Voor het bewaken van de status van inhoud voor de software-updates, klikt u op **bewaking** in de Configuration Manager-console.  

2. Vouw in de werkruimte Controle het knooppunt **Distributiestatus**uit en klik vervolgens op **Inhoudsstatus**.  

3. Selecteer het software-updatepakket dat u eerder voor het downloaden van software-updates hebt geïdentificeerd in de software-updategroep.  

4. Klik op het tabblad **Start** in de groep **Inhoud** op **Status weergeven**.  

##  <a name="BKMK_4DeployUpdateGroup"></a>Stap 4: De software-updategroep implementeren  
 Nadat u hebt bepaald welke software-updates u wilt implementeren en u deze software-updates aan een software-updategroep hebt toegevoegd, kunt u de software-updates in deze software-updategroep handmatig implementeren. Gebruik de volgende procedure om de software-updates in een software-updategroep handmatig te implementeren.  

#### <a name="to-manually-deploy-the-software-updates-in-a-software-update-group"></a>De software-updates in een software-updategroep handmatig implementeren  

1.  Klik in de Configuration Manager-console op **Softwarebibliotheek**.  

2.  Vouw in de werkruimte Softwarebibliotheek het knooppunt **Software-updates**uit en klik op **Software-updategroepen**.  

3.  Selecteer de software-updategroep die u wilt implementeren.  

4.  Klik op het tabblad **Start** in de groep **Implementatie** op **Implementeren**. De **wizard Software-updates implementeren** wordt geopend.  

5.  Configureer de volgende instellingen op de pagina Algemeen:  

    -   **Naam**: Geef de naam voor de implementatie. De implementatie moet een unieke naam zijn die het doel van de implementatie beschrijft en deze onderscheidt van andere implementaties in de Configuration Manager-site hebben. Configuration Manager biedt standaard automatisch een naam voor de implementatie in de volgende indeling: **Microsoft-Software-Updates -** <*datum*><*tijd*>  

    -   **Beschrijving**: Geef een beschrijving voor de implementatie. De beschrijving biedt een overzicht van de implementatie en eventuele andere relevante informatie die helpt om te identificeren en te onderscheiden van de implementatie van andere implementaties in Configuration Manager-site. Het beschrijvingsveld is optioneel en kent een limiet van 256 tekens. Het veld is standaard leeg.  

    -   **Software Update/Software-Updategroep**: Controleer of de weergegeven software-updategroep of software-update juist is.  

    -   **Implementatiesjabloon selecteren**: Geef op of een eerder opgeslagen implementatiesjabloon moet worden toegepast. U kunt een implementatiesjabloon zo configureren dat deze meerdere algemene eigenschappen voor software-update-implementatie bevat en de sjabloon vervolgens toepassen wanneer u daaropvolgende software-updates implementeert om consistentie met soortgelijke implementaties te garanderen en tijd te besparen.  

    -   **Verzameling**: Geef de verzameling voor de implementatie, indien van toepassing. Leden van de verzameling ontvangen de software-updates die in de implementatie zijn gedefinieerd.  

6.  Configureer de volgende instellingen op de pagina Implementatie-instellingen:  

    -   **Type implementatie**: Geef het implementatietype voor de implementatie van de software-update. Selecteer **Vereist** om een verplichte software-update-implementatie te maken waarin de software-updates voor een configureerde installatiedeadline automatisch op de clients worden geïnstalleerd. Selecteer **Beschikbaar** om een optionele software-update-implementatie te maken die voor gebruikers beschikbaar is in Software Center.  

        > [!IMPORTANT]  
        >  Nadat u de software update-implementatie hebt gemaakt, kan het type implementatie niet meer worden gewijzigd.  

        > [!NOTE]  
        >  Een software-updategroep die wordt geïmplementeerd als **Vereist** , wordt gedownload op de achtergrond waarbij BITS-instellingen worden gehandhaafd, indien geconfigureerd.  
        > Software-updategroepen die worden geïmplementeerd als **Beschikbaar** , worden echter gedownload op de voorgrond waarbij BITS-instellingen worden genegeerd.  

    -   **Wake-on-LAN gebruiken om clients voor vereiste implementaties te laten ontwaken**: Geef op of Wake On LAN tegen de deadline voor het verzenden van ontwaakpakketten naar computers waarvoor een of meer software-updates in de implementatie. Computers die zich op het tijdstip van de installatiedeadline in de slaapstandmodus bevinden, worden uit deze stand gehaald, zodat de installatie van de software-update kan worden gestart. Clients die zich in de slaapstandmodus bevinden en geen software-updates nodig hebben, worden niet gestart. Deze instelling is standaard uitgeschakeld en is alleen beschikbaar wanneer **Type implementatie** is ingesteld op **Vereist**.  

        > [!WARNING]  
        >  Voordat u deze optie kunt gebruiken, moeten computers en netwerken zijn geconfigureerd voor Wake On LAN.  

    -   **Detailniveau**: Geef het detailniveau voor de statusberichten die zijn gerapporteerd door clientcomputers.  

7.  Configureer de volgende instellingen op de pagina Planning:  

    -   **Evaluatie van planning**: Geef op of de beschikbare tijd en de tijdstippen voor de installatiedeadline worden geëvalueerd op basis van UTC of de lokale tijd van de computer waarop de Configuration Manager-console wordt uitgevoerd.  

        > [!NOTE]  
        >  Als u lokale tijd selecteert en selecteer vervolgens **zo snel mogelijk** voor de **tijd Software beschikbaar** of **installatiedeadline**, de huidige tijd op de computer die de Configuration Manager-console wordt gebruikt om te evalueren wanneer updates beschikbaar zijn of wanneer ze worden geïnstalleerd op een client wordt uitgevoerd. Als de client zich in een andere tijdzone bevindt, worden deze acties uitgevoerd wanneer de tijd van de client de evaluatietijd heeft bereikt.  

    -   **Tijd software beschikbaar**: Selecteer een van de volgende instellingen om op te geven wanneer de software-updates beschikbaar zijn voor clients:  

        -   **Zo spoedig mogelijk**: Selecteer deze instelling om de software-updates in de implementatie beschikbaar voor clients zo snel mogelijk. Wanneer de implementatie wordt gemaakt, wordt het clientbeleid bijgewerkt en worden de clients via hun volgende pollingcyclus voor het clientbeleid in kennis gesteld van de implementatie, waarna de software-updates beschikbaar zijn voor installatie.  

        -   **Specifiek tijdstip**: Selecteer deze instelling om de software-updates in de implementatie beschikbaar voor clients op een specifieke datum en tijd. Wanneer de implementatie wordt gemaakt, wordt het clientbeleid bijgewerkt en worden de clients via hun volgende pollingcyclus voor het clientbeleid in kennis gesteld van de implementatie. De software-updates in de implementatie zijn echter pas na de opgegeven datum en het opgegeven tijdstip beschikbaar voor installatie.  

    -   **Installatiedeadline**: Selecteer een van de volgende instellingen om op te geven van de installatiedeadline voor de software-updates in de implementatie.  

        > [!NOTE]  
        >  U kunt de instelling voor de installatiedeadline alleen configureren wanneer **Type implementatie** op de pagina Implementatie-instellingen is ingesteld op **Vereist** .  

        -   **Zo spoedig mogelijk**: Selecteer deze instelling om de software-updates in de implementatie zo spoedig mogelijk automatisch worden geïnstalleerd.  

        -   **Specifiek tijdstip**: Selecteer deze instelling om de software-updates in de implementatie op een specifieke datum en tijd automatisch worden geïnstalleerd.  

        > [!NOTE]  
        >  Het daadwerkelijke tijdstip van de installatiedeadline is het opgegeven deadlinetijdstip plus een willekeurige hoeveelheid tijd die maximaal twee uur bedraagt. Hierdoor wordt de mogelijke invloed op alle clientcomputers in de doelverzameling waarop de software-updates in de implementatie gelijktijdig worden geïnstalleerd, gereduceerd.  
        >   
        >  U kunt de **Computeragent** -clientinstelling **Willekeurig toepassen van deadline uitschakelen** configureren om de willekeurige vertraging voor de installatie van de vereiste software-updates uit te schakelen. Zie [Computeragent](../../core/clients/deploy/about-client-settings.md#computer-agent) voor meer informatie.  

8.  Configureer de volgende instellingen op de pagina Gebruikerservaring:  

    -   **Meldingen voor gebruikers**: Geef op of meldingen van de software-updates weergeven in Software Center op de clientcomputer op de geconfigureerde **tijd Software beschikbaar** en of meldingen voor gebruikers weergegeven op de clientcomputers. Wanneer **Type implementatie** op de pagina Implementatie-instellingen is ingesteld op **Beschikbaar** , kunt u **Verbergen in Software Center en alle meldingen verbergen**niet selecteren.  

    -   **Deadlinegedrag**: Alleen beschikbaar wanneer **Type implementatie** is ingesteld op **vereist** op de pagina implementatie-instellingen.   
    Geef het gedrag op dat moet worden vertoond als de deadline voor de implementatie van de software-update wordt bereikt. Geef op of de software-updates in de implementatie moeten worden geïnstalleerd. Geef ook op of het systeem na het installeren van software-updates opnieuw moet worden opgestart, ongeacht het geconfigureerde onderhoudsvenster. Zie voor meer informatie over onderhoudsvensters [het gebruik van onderhoudsvensters](../../core/clients/manage/collections/use-maintenance-windows.md).  

    -   **Gedrag voor opnieuw opstarten apparaat**: Alleen beschikbaar wanneer **Type implementatie** is ingesteld op **vereist** op de pagina implementatie-instellingen.    
    Geef op of het onderdrukken van opnieuw opstarten van servers en werkstations nadat software-updates zijn geïnstalleerd en opnieuw opstarten is vereist om de installatie te voltooien.  

        > [!IMPORTANT]  
        >  Het onderdrukken van het opnieuw opstarten van het systeem kan nuttig zijn in serveromgevingen of in gevallen waarin u wilt dat de computers die de software-updates installeren, niet standaard opnieuw worden opgestart. Dit kan er echter toe leiden dat computers zich in een onbeveiligde toestand bevinden. Het toestaan van afgedwongen opnieuw opstarten garandeert onmiddellijke voltooiing van de installatie van software-updates.

    -   **Schrijffilters voor Windows Embedded-apparaten**: Wanneer u software-updates op Windows Embedded-apparaten waarvoor schrijffilters ingeschakeld implementeren zijn, kunt u opgeven om de software-update op een tijdelijke overlay en de wijzigingen later installeren of de wijzigingen doorvoert tegen de installatiedeadline of tijdens een onderhoudsvenster. Wanneer u wijzigingen doorvoert tegen de installatiedeadline of tijdens een onderhoudsvenster, moet er opnieuw worden opgestart, zodat de wijzigingen behouden blijven op het apparaat.  

        > [!NOTE]  
        >  Wanneer u een software-update implementeert op een Windows Embedded-apparaat, moet u ervoor zorgen dat het apparaat lid is van een verzameling met een geconfigureerd onderhoudsvenster.  

    - **Implementatiegedrag voor nieuwe evaluatie bij het opnieuw opstarten van software-updates**: Vanaf Configuration Manager versie 1606, selecteer deze instelling om software-updates implementaties configureren zodat clients op een nalevingsscan voor software-updates onmiddellijk nadat een client software installeert-updates en opnieuw gestart. Hierdoor kan de client controleren op aanvullende beschikbare software-updates nadat de client opnieuw is opgestart, en deze installeren (en zorgen voor naleving) tijdens datzelfde onderhoudsvenster.

9. Configureer op de pagina waarschuwingen hoe Configuration Manager en System Center Operations Manager waarschuwingen voor deze implementatie genereren moeten. U kunt de waarschuwingen alleen configureren wanneer **Type implementatie** op de pagina Implementatie-instellingen is ingesteld op **Vereist** .  

    > [!NOTE]  
    >  U kunt recente waarschuwingen met betrekking tot software-updates weergegeven in het knooppunt **Software-updates** in de werkruimte **Softwarebibliotheek** .  

10. Configureer de volgende instellingen op de pagina Downloadinstellingen:  

    - Geef op of de client de software-updates moet downloaden en installeren wanneer een client is verbonden met een langzaam netwerk of wanneer deze gebruikmaakt van een locatie terugvalinhoudlocatie.  

    - Geef op of de client de software-updates moet downloaden en installeren vanaf een terugvaldistributiepunt wanneer de inhoud voor de software-updates niet beschikbaar is op een voorkeursdistributiepunt.  

    - **Toestaan dat clients inhoud te delen met andere clients in hetzelfde subnet**: Geef op of het gebruik van BranchCache voor inhouddownloads inschakelen. Zie voor meer informatie over BranchCache [basisconcepten voor inhoudsbeheer](../../core/plan-design/hierarchy/fundamental-concepts-for-content-management.md#branchcache).  

    - **Als software-updates niet beschikbaar is op het distributiepunt in de huidige, neighbor of site groepen, inhoud downloaden van Microsoft Updates**: Selecteer deze instelling clients die zijn verbonden met het intranet software-updates voor downloaden vanaf Microsoft Update als software-updates niet beschikbaar zijn op distributiepunten hebben. Clients op Internet gaat altijd u naar Microsoft Update voor de inhoud van software-updates.

    - Geef op of clients mogen downloaden na een installatiedeadline wanneer deze internetverbindingen met een datalimiet gebruiken. Internetproviders brengen soms de hoeveelheid gegevens die u verzendt en ontvangt in rekening wanneer u gebruikmaakt van een internetverbinding naar gebruik.  

    > [!NOTE]  
    >  Clients vragen de inhoudlocatie aan bij het beheerpunt voor de software-updates in een implementatie. Het downloadgedrag is afhankelijk van hoe u het distributiepunt, het implementatiepakket en de instellingen op deze pagina hebt geconfigureerd. Zie [Scenario's voor de locatie van inhoudsbronnen](../../core/plan-design/hierarchy/content-source-location-scenarios.md) voor meer informatie.  

11. Als u hebt uitgevoerd [stap 3: De inhoud voor de software-updategroep downloaden](#BKMK_3DownloadContent), worden de pagina's implementatiepakket, distributiepunten en taal selecteren niet weergegeven en kunt u doorgaan met stap 15 van de wizard.  

    > [!IMPORTANT]  
    >  Software-updates die eerder naar de inhoudsbibliotheek op de siteserver zijn gedownload, worden niet opnieuw gedownload. Dit geldt ook wanneer u een nieuw implementatiepakket voor de software-updates maakt. Als alle software-updates al eerder zijn gedownload, slaat de wizard de pagina **Taal selecteren** (stap 15) over.  

12. Selecteer op de pagina Implementatiepakket een bestaand implementatiepakket of configureer de volgende instellingen voor het opgeven van een nieuw implementatiepakket:  

    1.  **Naam**: Geef de naam van het implementatiepakket. Dit moet een unieke naam zijn die de pakketinhoud beschrijft. Er kunnen maximaal 50 tekens worden ingevoerd.  

    2.  **Beschrijving**: Geef een beschrijving die informatie over het implementatiepakket biedt. De beschrijving mag niet langer zijn dan 127 tekens.  

    3.  **Pakketbron**: Geef de locatie van de bronbestanden van de software-update.  Typ een netwerkpad voor de bronlocatie, zoals **\\\\server\sharenaam\pad**, of klik op **Bladeren** en ga naar de netwerklocatie. U moet een gedeelde map maken voor de bronbestanden van het installatiepakket voordat u doorgaat naar de volgende pagina.  

        > [!NOTE]  
        >  De bronlocatie van het installatiepakket die u opgeeft, mag niet door een ander software-installatiepakket worden gebruikt.  

        > [!IMPORTANT]  
        >  Het computeraccount van de SMS-provider en de gebruiker die de wizard uitvoert voor het downloaden van de software-updates, moeten over NTFS-machtigingen voor **schrijven** op de downloadlocatie beschikken. U moet de toegang tot de downloadlocatie zorgvuldig beperken om het risico op kwaadwillenden die met bronbestanden van de software-update knoeien, te reduceren.  

        > [!IMPORTANT]  
        >  U kunt de pakketbronlocatie in de eigenschappen van het installatiepakket wijzigen nadat Configuration Manager het implementatiepakket maakt. Als u dit doet, moet u echter eerst de inhoud van de oorspronkelijke pakketbron kopiëren naar de nieuwe pakketbronlocatie.  

    4.  **Prioriteit voor verzenden**: Geef de prioriteit voor verzenden voor het implementatiepakket. Configuration Manager gebruikt de prioriteit voor verzenden voor het implementatiepakket wanneer het pakket naar distributiepunten wordt verzonden. Installatiepakketten worden in volgorde van prioriteit verzonden: Hoog, Gemiddeld of laag. Pakketten met een identieke prioriteit worden verzonden in de volgorde waarin deze zijn gemaakt. Als er geen achterstand is, wordt het pakket onmiddellijk verwerkt, ongeacht de prioriteit van het pakket.  

13. Geef op de pagina Distributiepunten de distributiepunten of distributiepuntgroepen op die als host zullen fungeren voor de software-updatebestanden. Zie [Configuraties van het distributiepunt](../../core/servers/deploy/configure/install-and-configure-distribution-points.md#bkmk_configs) voor meer informatie over distributiepunten.  

14. Geef op de pagina Downloadlocatie op of de software-updatebestanden moeten worden gedownload vanaf internet of vanaf uw lokale netwerk. Configureer de volgende instellingen:  

    -   **Software-updates downloaden vanaf Internet**: Selecteer deze instelling om de software-updates downloaden vanaf een opgegeven locatie op Internet. Deze instelling is standaard ingeschakeld.  

    -   **Software-updates downloaden vanaf een locatie op het lokale netwerk**: Selecteer deze instelling om de softwareupdates downloaden vanaf een lokale map of een gedeelde netwerkmap. Deze instelling is nuttig wanneer de computer waarop de wizard wordt uitgevoerd, geen toegang tot internet heeft. De software-updates kunnen voorlopig worden gedownload vanaf een computer met internettoegang en worden opgeslagen op een locatie op het lokale netwerk voor daaropvolgende toegang voor installatiedoeleinden.  

15. Selecteer de talen waarvoor de geselecteerde software-updates worden gedownload op de pagina Taal selecteren. De software-updates worden alleen gedownload als deze beschikbaar zijn in de geselecteerde talen. Software-updates die niet aan een specifieke taal zijn gebonden, worden altijd gedownload. De wizard selecteert standaard de talen die u hebt geconfigureerd in de eigenschappen van het software-updatepunt. Er moet ten minste één taal worden geselecteerd voordat u doorgaat naar de volgende pagina. Wanneer u alleen talen selecteert die niet door een software-update worden ondersteund, mislukt het downloaden van de software-update.  

16. Controleer de instellingen op de pagina Overzicht. Klik, als u de instellingen wilt opslaan naar een implementatiesjabloon, op **Opslaan als sjabloon**, voer een naam in, selecteer de instellingen die u in de sjabloon wilt opnemen en klik op **Opslaan**. Als u een geconfigureerde instelling wilt wijzigen, klikt u op de gekoppelde wizardpagina en wijzigt u de instelling.  

    > [!WARNING]  
    >  De sjabloonnaam mag alfanumerieke ASCII-tekens en de tekens **\\** (backslash) en **‘** (apostrof) bevatten.  

17. Klik op **Volgende** om de software-update te implementeren.  

 Nadat u de wizard hebt voltooid, heeft Configuration Manager downloadt de software-updates aan de Inhoudsbibliotheek op de siteserver, distribueert de software-updates naar de geconfigureerde distributiepunten en implementeert vervolgens de software updategroep voor clients in de doelverzameling. Zie [Implementatieproces voor software-updates](../understand/software-updates-introduction.md#BKMK_DeploymentProcess) voor meer informatie over het implementatieproces.

## <a name="next-steps"></a>Volgende stappen
[Software-updates controleren](monitor-software-updates.md)
