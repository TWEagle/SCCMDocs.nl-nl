1.  Navigeer in de Configuration Manager-console naar **softwarebibliotheek** > **Software-Updates**.  

2.  Gebruik een van de volgende methoden om de gewenste software-update te kiezen:  

    -   Selecteer een of meer software-updategroepen bij **Software-updategroepen**en klik vervolgens op het tabblad **Start** in de groep **Updategroep** op **Downloaden**.  

    -   Selecteer een of meer software-updates bij **Alle software-updates**en klik vervolgens op het tabblad **Start** in de groep **Update** op **Downloaden**.  

        > [!NOTE]  
        >  Op de **alle Software-Updates** Configuration Manager-knooppunt geeft alleen software-updates met een **Kritiek** en **beveiliging** classificatie die in de afgelopen 30 dagen zijn uitgebracht.  

        > [!TIP]  
        >  Klik op **Criteria toevoegen** om de software-updates te filteren die in het knooppunt **Alle software-updates** worden weergegeven. Sla zoekcriteria die u vaak gebruikt op en beheer opgeslagen zoekopdrachten op het tabblad **Zoeken** .  

         De **wizard Software-updates downloaden** wordt geopend.  

3.  Configureer de volgende instellingen op de pagina **Implementatiepakket** :  

    1.  **Implementatiepakket selecteren**: Kies deze instelling om te selecteren van een bestaand implementatiepakket voor software-updates die in de implementatie.  

        > [!NOTE]  
        >  Software-updates die al naar het geselecteerde implementatiepakket zijn gedownload, worden niet opnieuw gedownload.  

    2.  **Maak een nieuw implementatiepakket**: Selecteer deze instelling om een nieuw implementatiepakket voor software-updates die in de implementatie te maken. Configureer de volgende instellingen:  

        -   **Naam**: Hiermee geeft u de naam van het implementatiepakket. Dit moet een unieke naam zijn die de pakketinhoud kort beschrijft.  Er kunnen maximaal 50 tekens worden ingevoerd.  

        -   **Beschrijving**: Hiermee geeft u de beschrijving van het implementatiepakket. De pakketbeschrijving biedt informatie over de pakketinhoud en kan maximaal 127 tekens lang zijn.  

        -   **Pakketbron**: Hiermee geeft u de locatie van de bronbestanden voor software-update. Typ een netwerkpad voor de bronlocatie, zoals **\\\\server\sharenaam\pad**, of klik op **Bladeren** en ga naar de netwerklocatie. U moet een gedeelde map maken voor de bronbestanden van het installatiepakket voordat u doorgaat naar de volgende pagina.  

            > [!NOTE]  
            >  De bronlocatie van het installatiepakket die u opgeeft, mag niet door een ander software-installatiepakket worden gebruikt.  

            > [!IMPORTANT]  
            >  Het computeraccount van de SMS-provider en de gebruiker die de wizard uitvoert voor het downloaden van de software-updates, moeten over NTFS-machtigingen voor **schrijven** op de downloadlocatie beschikken. U moet de toegang tot de downloadlocatie zorgvuldig beperken om het risico op kwaadwillenden die met bronbestanden van de software-update knoeien, te reduceren.  

            > [!IMPORTANT]  
            >  U kunt de pakketbronlocatie in de eigenschappen van het installatiepakket wijzigen nadat Configuration Manager het implementatiepakket maakt. Als u dit doet, moet u echter eerst de inhoud van de oorspronkelijke pakketbron kopiëren naar de nieuwe pakketbronlocatie.  

     Klik op **Volgende**.  

4.  Op de **distributiepunten** pagina, geeft u de distributiepunten of distributiepuntgroepen die de software-updatebestanden te hosten en klik vervolgens op **volgende**. Zie [Configuraties van het distributiepunt](../../core/servers/deploy/configure/install-and-configure-distribution-points.md#bkmk_configs) voor meer informatie over distributiepunten.  

    > [!NOTE]  
    >  Deze pagina is alleen beschikbaar wanneer u een nieuw implementatiepakket voor software-updates maakt.  

6.  Op de **distributie-instellingen** pagina, geeft u de volgende instellingen:  

    -   **Distributieprioriteit**: Gebruik deze instelling geeft de distributieprioriteit voor het implementatiepakket. De distributieprioriteit is van toepassing wanneer het implementatiepakket naar distributiepunten op onderliggende sites wordt verzonden. Installatiepakketten worden in volgorde van prioriteit verzonden: **Hoge**, **gemiddeld**, of **laag**. Pakketten met een identieke prioriteit worden verzonden in de volgorde waarin deze zijn gemaakt. Als er geen achterstand is, wordt het pakket onmiddellijk verwerkt, ongeacht de prioriteit van het pakket. Pakketten worden standaard verzonden met de prioriteit **Gemiddeld** .  

    -   **Distribueer de inhoud voor dit pakket naar voorkeursdistributiepunten**: Gebruik deze instelling om in te schakelen inhoudsdistributie op aanvraag naar voorkeursdistributiepunten. Wanneer deze instelling is ingeschakeld, maakt het beheerpunt een trigger voor de distributiebeheerder om de inhoud naar alle voorkeursdistributiepunten te distribueren wanneer een client de inhoud van een pakket aanvraagt en de inhoud op geen van de voorkeursdistributiepunten beschikbaar is. Zie [Scenario's voor de locatie van inhoudsbronnen](../../core/plan-design/hierarchy/content-source-location-scenarios.md) voor meer informatie over voorkeursdistributiepunten en inhoud op aanvraag.  

    -   **Instellingen voorbereid distributiepunt**: Gebruik deze instelling om op te geven hoe u wilt distribueren van inhoud naar voorbereide distributiepunten. Kies een van de volgende opties:  

        -   **Automatisch inhoud downloaden wanneer pakketten worden toegewezen aan distributiepunten**: Gebruik deze instelling negeert u de voorbereide instellingen en inhoud distribueert naar het distributiepunt.  

        -   **Alleen inhoudswijzigingen downloaden naar het distributiepunt**: Gebruik deze instelling om de initiële inhoud voor het distributiepunt voor te bereiden en vervolgens inhoudswijzigingen naar het distributiepunt distribueren.  

        -   **De inhoud in dit pakket handmatig kopiëren naar het distributiepunt**: Gebruik deze instelling om inhoud op het distributiepunt altijd voor te bereiden. Dit is de standaardinstelling.  

         Zie [Vooraf geplaatste inhoud gebruiken](../../core/servers/deploy/configure/deploy-and-manage-content.md#bkmk_prestage) voor meer informatie over het vooraf plaatsen van inhoud op distributiepunten.  

     Klik op **Volgende**.  

6.  Op de **downloadlocatie** pagina, geeft u de locatie die Configuration Manager gebruiken zal voor het downloaden van de bronbestanden voor software-update. Gebruik, indien nodig, de volgende opties:  

    -   **Software-updates downloaden vanaf Internet**: Selecteer deze instelling om de softwareupdates downloaden vanaf de locatie op Internet. Dit is de standaardinstelling.  

    -   **Software-updates downloaden vanaf een locatie op het lokale netwerk**: Selecteer deze instelling om software-updates downloaden vanaf een lokale map of een gedeelde netwerkmap. Gebruik deze instelling wanneer de computer waarop de wizard wordt uitgevoerd, niet over internettoegang beschikt.  

        > [!NOTE]  
        >  Wanneer u deze instelling gebruikt, downloadt u de software-updates via een computer met internettoegang en vervolgens kopieert u de software-updates naar een locatie op het lokale netwerk die toegankelijk is vanaf de computer waarop de wizard wordt uitgevoerd.  

     Klik op **Volgende**.  

7.  Op de **taalselectie** pagina, geeft u de talen waarvoor de geselecteerde software-updates moeten worden gedownload en klik vervolgens op **volgende**. Configuration Manager downloadt de software-updates alleen als ze beschikbaar in de geselecteerde talen zijn. Software-updates die niet aan een specifieke taal zijn gebonden, worden altijd gedownload.  

8. Op de **samenvatting** pagina, Controleer de instellingen die u in de wizard hebt geselecteerd en klik vervolgens op **volgende** download de software-updates.  

9. Op de **voltooiing** pagina, controleert u of de software-updates zijn gedownload, en klik vervolgens op **sluiten**.  
