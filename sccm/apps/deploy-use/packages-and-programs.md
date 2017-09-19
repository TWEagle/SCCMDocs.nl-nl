---
title: Pakketten en programma's | Microsoft Docs
description: Ondersteuning voor implementaties die pakketten en programma's of toepassingen met System Center Configuration Manager gebruiken.
ms.custom: na
ms.date: 10/06/2016
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: configmgr-app
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: caad0507-9913-415a-b13d-d36f8f0a1b80
caps.latest.revision: "8"
caps.handback.revision: "0"
author: mattbriggs
ms.author: mabrigg
manager: angrobe
ms.openlocfilehash: 05dd67bab32c4ac5adfb03b6dd149886955a32e1
ms.sourcegitcommit: b438515490e04fb09c82a8af642d38e9a0605178
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 09/15/2017
---
# <a name="packages-and-programs-in-system-center-configuration-manager"></a>Pakketten en programma's in System Center Configuration Manager

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*

System Center Configuration Manager blijft ondersteuning bieden voor pakketten en programma's die zijn gebruikt in Configuration Manager 2007. Een implementatie die pakketten en programma's gebruikt is mogelijk beter geschikt dan een implementatie die een toepassing gebruikt wanneer u het volgende implementeert:  

- Toepassingen voor Linux en UNIX-servers
- Scripts die niet worden gebruikt voor het installeren van een toepassing op een computer, zoals een script voor het defragmenteren van het schijfstation van de computer
- 'Eenmalige' scripts die niet voortdurend hoeven te worden bewaakt  
- Scripts die worden uitgevoerd volgens een herhaalde planning en die geen gebruik kunnen maken van globale evaluatie

Wanneer u pakketten vanaf een eerdere versie van Configuration Manager migreert, kunt u ze kunt implementeren in uw Configuration Manager-hiërarchie. Zodra de migratie is voltooid, worden de pakketten weergegeven onder het knooppunt **Pakketten** in de werkruimte **Softwarebibliotheek**.

U kunt wijzigen en implementeren van deze pakketten op dezelfde manier als die u dit hebt gedaan met behulp van softwaredistributie. De **definitie Wizard pakket importeren van** blijft in Configuration Manager om oudere pakketten te importeren. Aankondigingen worden geconverteerd naar implementaties als ze naar een Configuration Manager-hiërarchie van Configuration Manager 2007 worden gemigreerd.  

> [!NOTE]  
>  U kunt Microsoft System Center Configuration Manager Package Conversion Manager gebruiken om te converteren van pakketten en programma's naar Configuration Manager-toepassingen.  
>   
>  Zie [Configuration Manager Package Conversion Manager](https://technet.microsoft.com/library/hh531519.aspx) voor meer informatie.  

Pakketten kunnen enkele nieuwe functies van Configuration Manager, waaronder distributiepuntengroepen en bewaking gebruiken. Microsoft Application Virtualization (App-V)-toepassingen kunnen niet worden gedistribueerd met behulp van pakketten en programma's in Configuration Manager. Voor het distribueren van virtuele toepassingen, moet u ze als Configuration Manager-toepassingen maken.  

##  <a name="create-a-package-and-program"></a>Een pakket en programma maken  
 Gebruik een van deze procedures bij het maken of importeren van pakketten en programma's.  

### <a name="create-a-package-and-program-using-the-create-package-and-program-wizard"></a>Een pakket en programma maken met behulp van de wizard Pakket en Programma maken  

1.  Kies in de Configuration Manager-console **softwarebibliotheek** > **Toepassingsbeheer** > **pakketten**.  

3.  In de **Start** tabblad, in de **maken** groep, kiest u **pakket maken**.  

4.  Op de **pakket** pagina van de **Wizard pakket maken en programma**, geef de volgende informatie:  

    -   **Naam**: Geef een naam voor het pakket met een maximum van 50 tekens.  

    -   **Beschrijving**: Geef een beschrijving voor dit pakket met een maximum van 128 tekens.  

    -   **Fabrikant** (optioneel): Geef een fabrikant op om het pakket in de Configuration Manager-console te herkennen. Deze naam mag maximaal 32 tekens lang zijn.

    -   **Taal** (optioneel): Geef de taalversie van het pakket met een maximum van 32 tekens.  

    -   **Versie** (optioneel):  Geef een uniek versienummer op voor het pakket met een maximum van 32 tekens.

    -   **Dit pakket bevat bronbestanden**: Deze instelling geeft aan of het pakket bronbestanden aanwezig zijn op clientapparaten vereist. Standaard is dit selectievakje uitgeschakeld en Configuration Manager gebruikt geen distributiepunten voor het pakket. Als dit selectievakje is ingeschakeld, worden distributiepunten gebruikt.  

    -   **Bronmap**: Als het pakket bronbestanden bevat, kiest u **Bladeren** openen de **bronmap instellen** dialoogvenster vak en geef vervolgens de locatie van de bronbestanden voor het pakket.  

        > [!NOTE]  
        >  Het computeraccount van de siteserver moet leesrechten voor de door u opgegeven bronmap hebben.  

5.  Op de **programmatype** pagina van de **Wizard pakket maken en programma**, selecteer het type programma maken en kies vervolgens **volgende**. U kunt een programma voor een computer of apparaat maken of u kunt deze stap overslaan en later een programma maken.  

    > [!TIP]  
    >  Als u wilt een nieuw programma voor een bestaand pakket wilt maken, moet u eerst het pakket selecteren. Klik in de **Start** tabblad, in de **pakket** groep, kiest u **programma maken** openen de **Wizard programma maken**.  

6.  Gebruik een van de volgende procedures om een standaardprogramma of een apparaatprogramma te maken.  

    #### <a name="create-a-standard-program"></a>Een standaardprogramma maken  

  1.  Op de **programmatype** pagina van de **Wizard pakket maken en programma**, kies **standaardprogramma**, en kies vervolgens **volgende**.     

    2.  Op de **standaardprogramma** pagina, geeft u de volgende informatie:  

        -   **Naam:** Geef een naam voor het programma met een maximum van 50 tekens.  

            > [!NOTE]  
            >  De naam van het programma moet uniek zijn binnen een pakket. Nadat u een programma hebt gemaakt, kunt u de naam niet wijzigen.  

        -   **Opdrachtregel**: Geef de opdrachtregel gebruiken met dit programma te starten of kies een **Bladeren** om naar de locatie van het bestand te bladeren.  

            Als een bestandsnaam geen extensie die opgegeven, probeert Configuration Manager .com, .exe en .bat te gebruiken als mogelijke extensies.  

             Wanneer het programma wordt uitgevoerd op een client, Configuration Manager zoekt eerst de naam van de opdrachtregel in het pakket, wordt vervolgens in het lokale Windows-map en wordt vervolgens gezocht in lokale *% path %*. Als het bestand niet kan worden gevonden, treedt een fout op in het programma.  

        -   **Opstartmap** (optioneel): Geef de map waarin het programma wordt uitgevoerd, maximaal 127 tekens. Deze map kan zich een absoluut pad op de client of een pad dat ten opzichte van de distributiepuntmap die het pakket bevat.

        -   **Uitvoeren**: Geef de modus waarin het programma wordt uitgevoerd op clientcomputers. Selecteer vervolgens een van de volgende opties:  

            -   **Normaal**: Het programma wordt uitgevoerd in de normale modus op basis van systeem en standaardprogramma. Dit is de standaardmodus.  

            -   **Geminimaliseerd**: Het programma wordt geminimaliseerd uitgevoerd op clientapparaten. Gebruikers zien de installatieactiviteit in het systeemvak of op de taakbalk mogelijk.  

            -   **Gemaximaliseerd**: Het programma wordt gemaximaliseerd uitgevoerd op clientapparaten. Gebruikers zien de installatieactiviteit.  

            -   **Verborgen**: Het programma wordt verborgen uitgevoerd op clientapparaten. Gebruikers zien niet de installatieactiviteit.  

        -   **Programma kan worden uitgevoerd**: Geef op of het programma wordt alleen uitgevoerd als een gebruiker is aangemeld, alleen wanneer er geen gebruiker is aangemeld in, of ongeacht of een gebruiker is aangemeld bij de clientcomputer.  

        -   **Uitvoermodus**: Geef op of het programma wordt uitgevoerd met beheerdersmachtigingen of met de machtigingen van de gebruiker die momenteel aangemeld.  

        -   **Toestaan dat gebruikers de programma-installatie kunnen zien en**: Gebruik deze instelling, indien beschikbaar, kunt u opgeven of gebruikers kunnen communiceren met de programma-installatie. Dit selectievakje is alleen beschikbaar wanneer **alleen wanneer er geen gebruiker is aangemeld** of **al dan niet een gebruiker is aangemeld** is geselecteerd voor **programma kan worden uitgevoerd** en wanneer **uitvoeren met beheerdersrechten** is geselecteerd voor **uitvoermodus**.  

        -   **Stationsmodus**: Geef informatie op over hoe dit programma wordt uitgevoerd op het netwerk. Kies een van de volgende opties:  

            -   **Wordt uitgevoerd met UNC-naam**: Geef op dat het programma wordt uitgevoerd met de naam van een Universal Naming Convention (UNC). Dit is de standaardinstelling.  

            -   **Vereist stationsletter**: Geef op dat het programma een stationsletter voor de locatie volledig te kwalificeren vereist. Voor deze instelling kunt de Configuration Manager alle beschikbare stationsletters gebruiken op de client.  

            -   **Vereist specifieke stationsletter** : Opgeven dat het programma een specifieke stationsletter die u opgeeft om de locatie volledig te kwalificeren vereist (bijvoorbeeld **Z:**). Als de opgegeven stationsletter al op een client gebruikt wordt, wordt het programma niet uitgevoerd.  

        -   **Opnieuw verbinding maken met distributiepunt bij aanmelding op**: Gebruik dit selectievakje in om aan te geven of de clientcomputer opnieuw verbinding met het distributiepunt maakt wanneer de gebruiker zich aanmeldt. Standaard is dit selectievakje niet geselecteerd.  

  3.  Op de **vereisten** pagina van de **maken Wizard pakket en programma,** Geef de volgende informatie:  

        -   **Eerst een ander programma uitvoeren**: Gebruik deze instelling om te identificeren van een pakket en programma dat wordt uitgevoerd voordat dit pakket en programma wordt uitgevoerd.  

        -   **Platformvereisten**: Selecteer **dit programma kan worden uitgevoerd op elk platform** of **dit programma kan alleen op specifieke platforms worden uitgevoerd**, en kies vervolgens de besturingssystemen die door clients moeten worden uitgevoerd om te kunnen installeren van het pakket en programma.  

        -   **Geschatte schijfruimte**: Geef de hoeveelheid schijfruimte die het programma nodig heeft om uit te voeren op de computer. Dit kan worden opgegeven als **Onbekend** (de standaardinstelling) of als een geheel getal groter dan of gelijk aan nul. Als een waarde is opgegeven, moeten er ook eenheden voor de waarde worden opgegeven.  

        -   **Maximale toegestane uitvoeringstijd (minuten)**: Geef de maximale tijd die het programma uit te voeren op de clientcomputer wordt verwacht. Dit kan worden opgegeven als **Onbekend** (de standaardinstelling) of als een geheel getal groter dan nul.  

             Deze waarde is standaard ingesteld op 120 minuten.  

            > [!IMPORTANT]  
            >  Als u onderhoudsvensters gebruikt voor de verzameling waarop dit programma wordt uitgevoerd, een conflict kan optreden als de **maximale toegestane uitvoeringstijd** langer is dan het geplande onderhoudsvenster. Als de maximum uitvoeringstijd echter is ingesteld op **onbekende**, het programma wordt uitgevoerd tijdens het onderhoudsvenster en blijft uitvoeren indien nodig nadat het onderhoudsvenster is gesloten. Als de maximale uitvoeringstijd op een specifieke periode die langer is dan de lengte van welk beschikbaar onderhoudsvenster instelt, wordt het programma niet uitgevoerd.  

             Als de waarde is ingesteld op **onbekende**, Configuration Manager stelt de maximale toegestane uitvoeringstijd 12 uur (720 minuten).  

            > [!NOTE]  
            >  Als de maximum uitvoeringstijd (hetzij ingesteld door de gebruiker hetzij als de standaardwaarde) overschreden is, wordt in Configuration Manager wordt gestopt als **uitvoeren met beheerdersrechten** is geselecteerd en **toestaan dat gebruikers de programma-installatie kunnen zien en** niet is ingeschakeld.  

  4.  Kies **volgende**.  

    #### <a name="create-a-device-program"></a>Een apparaatprogramma maken  

  1.  Op de **programmatype** pagina van de **Wizard pakket maken en programma**, selecteer **programma voor apparaat**, en kies vervolgens **volgende**.  

  2.  Op de **programma voor apparaat** pagina, geeft u het volgende:  

        -   **Naam**: Geef een naam voor het programma met een maximum van 50 tekens.  

            > [!NOTE]  
            >  De naam van het programma moet uniek zijn binnen een pakket. Nadat u een programma hebt gemaakt, kunt u de naam niet wijzigen.  

        -   **Opmerking** (optioneel): Geef een opmerking voor dit apparaatprogramma op met maximaal 127 tekens.  

        -   **Downloadmap**: Geef de naam van de map op het Windows CE-apparaat waarop de bronbestanden van het pakket wordt opgeslagen. De standaardwaarde is **\Temp\\**.  

        -   **Opdrachtregel**: Geef de opdrachtregel gebruiken met dit programma te starten of kies een **Bladeren** om naar de locatie van het bestand te bladeren.  

        -   **Opdrachtregel uitvoeren in downloadmap**: Selecteer deze optie om het programma uitvoeren vanaf de eerder opgegeven downloadmap.  

        -   **Opdrachtregel uitvoeren vanuit deze map**: Selecteer deze optie om op te geven van een andere map van waaruit het programma uit te voeren.  

    3.  Op de **vereisten** pagina, geeft u het volgende:  

        -   **Geschatte schijfruimte**: Geef de hoeveelheid schijfruimte die zijn voor de software vereist. Deze is zichtbaar voor gebruikers van mobiele apparaten alvorens het programma te installeren.  

        -   **Programma downloaden**: Informatie over wanneer dit programma kan worden gedownload op mobiele apparaten opgeven. U kunt **Zo snel mogelijk**, **Alleen via een snel netwerk** of **Alleen wanneer het apparaat is vastgezet** opgeven.  

        -   **Aanvullende vereisten**: Geef eventuele bijkomende vereisten voor dit programma. Deze worden getoond aan gebruikers voordat ze de software installeren. U kunt gebruikers bijvoorbeeld waarschuwen dat ze alle andere toepassingen moeten sluiten voordat ze het programma uitvoeren.  

  4.  Kies **volgende**.  

  7.  Op de **samenvatting** controleert u de acties die moeten worden ondernomen en voltooi de wizard.  

 Zorg dat het nieuwe pakket en programma worden weergegeven de **pakketten** knooppunt van de **softwarebibliotheek** werkruimte.  

## <a name="create-a-package-and-program-from-a-package-definition-file"></a>Een pakket en programma maken van een pakketdefinitiebestand  

1.  Kies in de Configuration Manager-console **softwarebibliotheek** > **Toepassingsbeheer** > **pakketten**.  

3.  Op de **Start** tabblad, in de **maken** groep, kiest u **pakket maken vanuit definitie**.  

4.  Op de **pakketdefinitie** pagina van de **pakket maken vanuit definitie Wizard**, kies een bestaand pakketdefinitiebestand of kies **Bladeren** een nieuw pakketdefinitiebestand te openen. Nadat u een nieuw pakketdefinitiebestand hebt opgegeven, selecteert u deze uit de **pakketdefinitie** lijst en kies vervolgens **volgende**.  

5.  Op de **bronbestanden** pagina, informatie over de vereiste bronbestanden voor het pakket en programma opgeven en kies vervolgens **volgende**.  

6.  Als het pakket bronbestanden bevat, op de **bronmap** pagina, geeft u de locatie van waaruit de bronbestanden kunnen worden verkregen en kies vervolgens **volgende**.  

7.  Op de **samenvatting** controleert u de acties die moeten worden ondernomen en voltooi de wizard. Het nieuwe pakket en programma worden weergegeven in de **pakketten** knooppunt van de **softwarebibliotheek** werkruimte.  

 Zie voor meer informatie over pakketdefinitiebestanden [over de bestandsindeling van pakketdefinities](/sccm/apps/deploy-use/packages-and-programs#about-the-package-definition-file-format) in dit onderwerp.  

##  <a name="deploy-packages-and-programs"></a>Pakketten en programma's implementeren  

1.  Kies in de Configuration Manager-console **softwarebibliotheek** > **Toepassingsbeheer** > **pakketten**.  

2.  Selecteer het pakket dat u implementeren wilt, en klik vervolgens in de **Start** tabblad de **implementatie** groep, kiest u **implementeren**.  

3.  Op de **algemene** pagina van de **Wizard Software implementeren**, geef de naam van het pakket en programma dat u implementeren wilt, de verzameling waarnaar u wilt implementeren van het pakket en programma en optionele opmerkingen voor de implementatie.  

     Selecteer **Standaarddistributiepuntengroepen gebruiken die aan deze verzameling zijn gekoppeld** als u de pakketinhoud wilt opslaan op de standaarddistributiepuntengroep van de verzameling. Als u de geselecteerde verzameling niet hebt gekoppeld aan een distributiepuntgroep, is deze optie niet beschikbaar.  

4.  Op de **inhoud** pagina **toevoegen**, en selecteer vervolgens de distributiepunten of distributiepuntengroepen waarop u wilt de inhoud die is gekoppeld aan dit pakket en programma implementeert.  

5.  Op de **implementatie-instellingen** pagina, kiest u een doel voor deze implementatie en geef opties op voor ontwaakpakketten en verbindingen met datalimiet:  

    -   **Doel**: U kunt kiezen uit:  

        -   **Beschikbare**: Als de toepassing wordt geïmplementeerd voor een gebruiker, wordt de gebruiker ziet het gepubliceerde pakket en programma in de Application Catalog en kan deze op aanvraag opvragen. Als het pakket en programma wordt geïmplementeerd op een apparaat, wordt de gebruiker ziet het in Software Center en kan deze op verzoek installeren.  

        -   **Vereist**: Het pakket en programma wordt automatisch geïmplementeerd volgens de geconfigureerde planning. Een gebruiker kan echter de implementatiestatus van het pakket en programma volgen en deze installeren vóór de deadline door het gebruik van het Software Center.  

    -   **Verzenden van ontwaakpakketten**: Als het implementatiedoel is ingesteld op **vereist** en deze optie is geselecteerd, wordt een ontwaakpakket verzonden naar computers voordat de implementatie wordt geïnstalleerd om de computer uit de slaapstand deadline van de installatie te halen. Voordat u deze optie kunt gebruiken, moeten computers zijn geconfigureerd voor Wake On LAN.  

    -  **Laat clients toe op een internetverbinding naar gebruik om inhoud te downloaden na de installatiedeadline, waarvoor extra kosten in rekening kan worden**: Selecteer deze optie als dit is verplicht.  

    > [!NOTE]  
    >  De optie **Software implementeren op het primaire apparaat van de gebruiker** is niet beschikbaar wanneer u een pakket en programma implementeert.  

6.  Op de **planning** pagina, configureren wanneer dit pakket en programma worden geïmplementeerd of beschikbaar gesteld voor clientapparaten.  

     De opties op deze pagina verschillen afhankelijk van of de implementatieactie ingesteld is op **beschikbaar** of **vereist**.  

7.  Als het implementatiedoel is ingesteld op **vereist**, configureert u het gedrag voor opnieuw uitvoeren voor het programma in de **gedrag voor opnieuw uitvoeren** vervolgkeuzelijst. Kies uit de volgende opties:  

    |Gedrag voor opnieuw uitvoeren|Meer informatie|  
    |--------------------|----------------------|  
    |Geïmplementeerd programma nooit opnieuw uitvoeren|Het programma won't opnieuw uitgevoerd op de client, zelfs als het programma oorspronkelijk is mislukt of als de programmabestanden worden gewijzigd.|  
    |Programma altijd opnieuw uitvoeren|Het programma wordt altijd opnieuw uitgevoerd op de client wanneer de implementatie is gepland, zelfs als het programma al is uitgevoerd. Dit kan nuttig zijn wanneer u herhaalde implementaties gebruikt waarin het programma wordt bijgewerkt, bijvoorbeeld met antivirussoftware.|  
    |Opnieuw uitvoeren als de vorige poging is mislukt|Het programma wordt opnieuw uitgevoerd wanneer de implementatie is gepland als de vorige uitvoeringspoging is mislukt.|  
    |Opnieuw uitvoeren als de vorige poging is gelukt|Het programma wordt alleen opnieuw uitgevoerd als het eerder is uitgevoerd op de client. Dit is nuttig wanneer u herhaalde aankondigingen gebruikt waarbij het programma regelmatig wordt bijgewerkt en waarbij het voor elke update vereist is dat de vorige update is geïnstalleerd.|  

8. Geef op de pagina **Gebruikerservaring** de volgende informatie:  

    -   **Toestaan dat gebruikers het programma onafhankelijk van toewijzingen uit te voeren**: Bij inschakeling kunnen gebruikers deze software installeren vanuit Software Center ongeacht een eventueel gepland installatietijdstip.  

    -   **Software-installatie**: Hierdoor kan de software worden geïnstalleerd buiten de geconfigureerde onderhoudsvensters.  

    -   **Systeem opnieuw opstarten (indien nodig om de installatie te voltooien)**: Als de software-installatie een herstart van het apparaat vereist te voltooien, kunt u dit mag gebeuren buiten de geconfigureerde onderhoudsvensters.  

    -   **Embedded-apparaten**: Wanneer u pakketten en programma's op Windows Embedded-apparaten die write filter is ingeschakeld implementeert zijn, kunt u opgeven dat pakketten en programma's worden geïnstalleerd op de tijdelijke overlay en doorvoeren wijzigingen later. U kunt doorvoeren u de wijzigingen op de installatiedeadline of tijdens een onderhoudsvenster. Wanneer u wijzigingen op de installatiedeadline of tijdens een onderhoudsvenster doorvoert, moet worden opgestart en de wijzigingen behouden blijven op het apparaat.  

        > [!NOTE]  
        >  Wanneer u een pakket of programma implementeert op een Windows Embedded-apparaat, moet u ervoor zorgen dat het apparaat lid is van een verzameling met een geconfigureerd onderhoudsvenster. Zie voor meer informatie over hoe onderhoudvensters worden gebruikt wanneer u pakketten en programma's voor Windows Embedded-apparaten implementeert, [maken van Windows Embedded-toepassingen](../../apps/get-started/creating-windows-embedded-applications.md).  

9. Geef op de pagina **Distributiepunten** de volgende informatie:  

    -   **Implementatieopties**: Geef de acties die een client ondernemen moet voor het uitvoeren van programma-inhoud. U kunt gedrag opgeven wanneer de client zich in een snelle netwerkgrens bevindt of in een trage of onbetrouwbare netwerkgrens bevindt.  

    -   **Toestaan dat clients inhoud te delen met andere clients in hetzelfde subnet**: Selecteer deze optie om de belasting op het netwerk te verminderen door clients inhoud downloaden van andere clients op het netwerk die reeds zijn gedownload en gecached. Deze optie gebruikt Windows BranchCache en kan worden gebruikt op computers met Windows Vista SP2 of hoger.  

    -   **Clients gebruiken een terugvalbronlocatie voor inhoud toestaan**:  

        -  **Oudere versies dan 1610**: U kunt selecteren de **terugvalbronlocatie voor inhoud selectievakje toestaan** inschakelen voor clients buiten deze grensgroepen groepen terug te vallen en het gebruik van de distributie verwijzen als bronlocatie voor inhoud wanneer er geen andere distributiepunten beschikbaar zijn.

        - **Versie 1610 en hoger**: U kunt niet meer configureren **terugvalbronlocatie voor inhoud toestaan**.  In plaats daarvan configureert u de relaties tussen grensgroepen om te bepalen wanneer een client beginnen kunt met het extra grensgroepen voor de locatie van een geldige inhoudsbron zoeken.

10. Op de **samenvatting** controleert u de acties die moeten worden ondernomen en voltooi de wizard.  

     U ziet de implementatie in het knooppunt **Implementaties** van de werkruimte **Bewaking** en in het detailvenster van het tabblad voor de pakketimplementatie wanneer u de implementatie selecteert. Zie voor meer informatie [pakketten en programma's bewaken](/sccm/apps/deploy-use/packages-and-programs#monitor-packages-and-programs) in dit onderwerp.  

> [!IMPORTANT]  
>  Als u de optie geconfigureerd **programma uitvoeren vanaf distributiepunt** op de **distributiepunten** pagina van de **Wizard Software implementeren**, schakel de optie niet uit **de inhoud in dit pakket kopiëren naar een pakketshare op distributiepunten** omdat hierdoor het pakket niet beschikbaar voor uitvoering vanaf distributiepunten.  

##  <a name="monitor-packages-and-programs"></a>Monitor voor pakketten en programma 's  
 Voor het bewaken van pakket en programma-implementaties, gebruikt u dezelfde procedures die u gebruikt voor het bewaken van toepassingen, zoals beschreven in [toepassingen bewaken](/sccm/apps/deploy-use/monitor-applications-from-the-console).  

 Pakketten en programma's bevatten ook een aantal van ingebouwde rapporten waarmee u informatie kunt controleren over de implementatiestatus van pakketten en programma's. Deze rapporten hebben de rapportcategorie **Softwaredistributie – Pakketten en programma's** en **Softwaredistributie – Status van pakket- en programma-implementatie**.  

 Zie voor meer informatie over het configureren van rapportage in Configuration Manager [rapportage in System Center Configuration Manager](../../core/servers/manage/reporting.md).  

##  <a name="manage-packages-and-programs"></a>Pakketten en programma's beheren  
 In de **softwarebibliotheek** werkruimte Vouw **Toepassingsbeheer**, kies **pakketten**, kiest u het pakket dat u wilt beheren en kies vervolgens een beheertaak in de volgende tabel:  

|Taak|Meer informatie|  
|----------|----------------------|  
|**Voorbereid inhoudsbestand maken**|Hiermee opent u de **maken Wizard voorbereid inhoudsbestand**, waarmee u een bestand met de inhoud van het pakket kan niet handmatig worden geïmporteerd in een andere site te maken. Dit is nuttig in situaties met lage netwerkbandbreedte tussen de siteserver en het distributiepunt.|  
|**Programma maken**|Hiermee opent u de **Wizard programma maken**, waarmee u een nieuw programma voor dit pakket maken.|  
|**Exportereneren**|Hiermee opent u de **Wizard pakket exporteren**, waarmee u het geselecteerde pakket en de inhoud naar een bestand exporteren.<br /><br /> Zie voor meer informatie over het importeren van pakketten en programma's [pakketten en programma's maken](/sccm/apps/deploy-use/packages-and-programs#create-packages-and-programs) in dit onderwerp.|  
|**Implementeren**|Hiermee opent u de **Wizard Software implementeren**, waarmee u het geselecteerde pakket en programma implementeren in een verzameling. Zie voor meer informatie [pakketten en programma's implementeren](/sccm/apps/deploy-use/packages-and-programs#deploy-packages-and-programs) in dit onderwerp.|  
|**Inhoud distribueren**|Hiermee opent u de **Wizard inhoud distribueren**, waarmee u de inhoud die is gekoppeld aan het pakket en programma naar geselecteerde distributiepunten of distributiepuntengroepen verzenden.|  
|**Distributiepunten bijwerken**|Hiermee worden distributiepunten bijwerkt met de meest recente inhoud voor het geselecteerde pakket en programma.|  

##  <a name="about-the-package-definition-file-format"></a>Over de bestandsindeling van pakketdefinities  
 Pakketdefinitiebestanden zijn scripts die u gebruiken kunt voor het automatiseren van pakket en programma maken met Configuration Manager. Ze bieden alle de informatie die Configuration Manager moet maken van een pakket en programma, met uitzondering van de locatie van pakketbronbestanden. Elke pakketdefinitiebestand is een ASCII- of UTF-8-tekstbestand die gebruikmaakt van het ini-bestandsindeling en waarin de volgende secties:  

###  <a name="pdf"></a>[PDF]  
 Deze sectie geeft het bestand aan als een pakketdefinitiebestand. De sectie bevat de volgende informatie:  

-   **Versie**: Geef de versie van de bestandsindeling van pakketdefinities die wordt gebruikt door het bestand. Dit komt overeen met de versie van System Management Server (SMS) of Configuration Manager waarvoor het bestand is geschreven. Dit item is vereist.  

###  <a name="package-definition"></a>[Package Definition]  
 De eigenschappen van het pakket en programma opgeven. De sectie bevat de volgende informatie:  

-   **Naam**: De naam van het pakket, maximaal 50 tekens.  

-   **Versie** (optioneel): De versie van het pakket, maximaal 32 tekens.  

-   **Pictogram** (optioneel): Het bestand dat het pictogram moet worden gebruikt voor dit pakket bevat. Indien opgegeven, vervangt dit pictogram het standaardpakketpictogram in de Configuration Manager-console.

-   **Publisher**: De uitgever van het pakket, maximaal 32 tekens.

-   **Taal**: De taalversie van het pakket, maximaal 32 tekens.

-   **Opmerking** (optioneel): Een opmerking over het pakket, maximaal 127 tekens.

-   **ContainsNoFiles**: Deze vermelding geeft aan of een bron gekoppeld aan het pakket is.  

-   **Programma's**: De programma's die zijn gedefinieerd voor dit pakket. Elke programmanaam komt overeen met een sectie **[Program]** in dit pakketdefinitiebestand.  

     Voorbeeld:  

     `Programs=Typical, Custom, Uninstall`  

-   **MIFFileName**: De naam van het Management Information Format (MIF)-bestand dat de pakketstatus, maximaal 50 tekens bevat.  

-   **MIFName**: De naam van het pakket (voor MIF-koppeling), maximaal 50 tekens.  

-   **MIFVersion**: Het versienummer van het pakket (voor MIF-koppeling), maximaal 32 tekens.  

-   **MIFPublisher**: De software-uitgever van het pakket (voor MIF-koppeling), maximaal 32 tekens.  

###  <a name="program"></a>[Program]  
 Voor elk programma dat opgegeven in de **programma's** vermelding in de **[Package Definition]** sectie, het pakketdefinitiebestand moet [Program] sectie bevatten waarmee dat programma wordt gedefinieerd. Elke sectie Program bevat de volgende informatie:  

-   **Naam**: De naam van het programma, maximaal 50 tekens. Dit item moet uniek zijn binnen een pakket. Deze naam wordt gebruikt bij het definiëren van advertenties. Op clientcomputers wordt de naam van het programma weergegeven in **Aangekondigde programma's uitvoeren** in het Configuratiescherm.  

-   **Pictogram** (optioneel): Geef het bestand dat het pictogram moet worden gebruikt voor dit programma bevat. Indien opgegeven, wordt dit pictogram het standaardprogrammapictogram in de Configuration Manager-console vervangt en op clientcomputers wordt weergegeven wanneer het programma wordt aangekondigd.

-   **Opmerking** (optioneel): Een opmerking over het programma, maximaal 127 tekens.

-   **CommandLine**: Geef de opdrachtregel voor het programma, maximaal 127 tekens. De opdracht is relatief ten opzichte van de pakketbronmap.

-   **StartIn**: Geef de werkmap voor het programma, maximaal 127 tekens. Dit item kan een absoluut pad op de clientcomputer of een pad dat ten opzichte van de pakketbronmap zijn.

-   **Uitvoeren**: Geef de programmamodus op waarin het programma wordt uitgevoerd. U kunt **Minimized** (Geminimaliseerd), **Maximized** (Gemaximaliseerd) of **Hidden** (Verborgen) opgeven. Als dit item niet opgenomen is, wordt het programma wordt uitgevoerd in de normale modus.  

-   **AfterRunning**: Geef een speciale actie op die plaatsvindt nadat het programma is voltooid. Beschikbare opties zijn **SMSRestart**, **ProgramRestart** en **SMSLogoff**. Als dit item niet opgenomen is, niet het programma een speciale actie uitgevoerd.  

-   **EstimatedDiskSpace**: Geef de hoeveelheid schijfruimte die het programma nodig heeft om uit te voeren op de computer. Dit kan worden opgegeven als **Onbekend** (de standaardinstelling) of als een geheel getal groter dan of gelijk aan nul. Als een waarde is opgegeven, moeten ook de eenheden voor de waarde worden opgegeven.  

     Voorbeeld:  

     `EstimatedDiskSpace=38MB`  

-   **EstimatedRunTime**: Geef de geschatte duur (in minuten) die het programma uit te voeren op de clientcomputer wordt verwacht. Dit kan worden opgegeven als **Onbekend** (de standaardinstelling) of als een geheel getal groter dan nul.  

     Voorbeeld:  

     `EstimatedRunTime=25`  

-   **SupportedClients**: Geef de processors en besturingssystemen op waarop dit programma wordt uitgevoerd. De opgegeven platforms moeten van elkaar worden gescheiden door komma's. Als dit item niet opgenomen is, wordt de controle van ondersteunde platforms uitgeschakeld voor dit programma.  

-   **SupportedClientMinVersionX**, **SupportedClientMaxVersionX**: Geef de begin-tot eindbereik op voor versienummers voor de besturingssystemen die zijn opgegeven in de **SupportedClients** vermelding.  

     Voorbeeld:  

    ```  
    SupportedClients=Win NT (I386),Win NT (IA64),Win NT (x64)  
    Win NT (I386) MinVersion1=5.00.2195.4  
    Win NT (I386) MaxVersion1=5.00.2195.4  
    Win NT (I386) MinVersion2=5.10.2600.2  
    Win NT (I386) MaxVersion2=5.10.2600.2  
    Win NT (I386) MinVersion3=5.20.0000.0  
    Win NT (I386) MaxVersion3=5.20.9999.9999  
    Win NT (I386) MinVersion4=5.20.3790.0  
    Win NT (I386) MaxVersion4=5.20.3790.2  
    Win NT (I386) MinVersion5=6.00.0000.0  
    Win NT (I386) MaxVersion5=6.00.9999.9999  
    Win NT (IA64) MinVersion1=5.20.0000.0  
    Win NT (IA64) MaxVersion1=5.20.9999.9999  
    Win NT (x64) MinVersion1=5.20.0000.0  
    Win NT (x64) MaxVersion1=5.20.9999.9999  
    Win NT (x64) MinVersion2=5.20.3790.0  
    Win NT (x64) MaxVersion2=5.20.9999.9999  
    Win NT (x64) MinVersion3=5.20.3790.0  
    Win NT (x64) MaxVersion3=5.20.3790.2  
    Win NT (x64) MinVersion4=6.00.0000.0  
    Win NT (x64) MaxVersion4=6.00.9999.9999   
    ```  

-   **AdditionalProgramRequirements** (optioneel): Geef alle overige informatie of vereisten voor clientcomputers, maximaal 127 tekens.

-   **CanRunWhen**: Geef de status van de gebruiker die het programma nodig heeft om uit te voeren op de clientcomputer. Beschikbare waarden zijn **UserLoggedOn**, **NoUserLoggedOn** en **AnyUserStatus**. De standaardwaarde is **UserLoggedOn**.  

-   **UserInputRequired**: Geef op of het programma interactie met de gebruiker vereist. Beschikbare waarden zijn **True** (Waar) of **False** (Onwaar). De standaardwaarde is **True** (Waar). Dit item wordt ingesteld op **False** (Onwaar) als **CanRunWhen** niet is ingesteld op **UserLoggedOn**.  

-   **AdminRightsRequired**: Geef op of het programma beheerdersreferenties op de computer vereist. Beschikbare waarden zijn **True** (Waar) of **False** (Onwaar). De standaardwaarde is **False**. Dit item wordt ingesteld op **True** (Waar) als **CanRunWhen** niet is ingesteld op **UserLoggedOn**.  

-   **UseInstallAccount**: Geef op of het programma het installatie-Account voor clientsoftware gebruikt wanneer deze wordt uitgevoerd op clientcomputers. Deze waarde is standaard **False** (Onwaar). Deze waarde is ook **False** (Onwaar) als **CanRunWhen** is ingesteld op **UserLoggedOn**.  

-   **DriveLetterConnection**: Geef op of het programma vereist dat een stationsletter aan de pakketbestanden die zich op het distributiepunt bevinden. U kunt **True** (Waar) of **False** (Onwaar) opgeven. De standaardwaarde is **False**, waardoor het programma een Universal Naming Convention (UNC)-verbinding gebruiken. Als deze waarde is ingesteld op **True**, de eerstvolgende beschikbare stationsletter wordt gebruikt (vanaf Z: en in teruglopende volgorde).  

-   **SpecifyDrive** (optioneel): Geef een stationsletter op die het programma nodig heeft om verbinding maken met de pakketbestanden op het distributiepunt. Deze specificatie dwingt het gebruik van de opgegeven stationsletter af voor clientverbindingen met distributiepunten.

-   **ReconnectDriveAtLogon**: Geef op of de computer opnieuw verbinding met het distributiepunt maakt wanneer de gebruiker zich aanmeldt. Beschikbare waarden zijn **True** (Waar) of **False** (Onwaar). De standaardwaarde is **False**.  

-   **DependentProgram**: Geef een programma in dit pakket op dat moet worden uitgevoerd vóór het huidige programma. Voor item wordt de indeling **DependentProgram**=<**ProgramName>** gebruikt, waarbij **<ProgramName\>** de vermelding in de pakketdefinitie voor dat programma bij **Name** is. Als er geen afhankelijke programma's zijn, laat u dit item leeg.  

     Voorbeeld:  

     DependentProgram=Admin  
    DependentProgram=  

-   **Toewijzing**: Geef op hoe het programma wordt toegewezen aan gebruikers. Deze waarde kan zijn: **FirstUser** (alleen de eerste gebruiker die zich bij de client aanmeldt het programma voert) of **EveryUser** (elke gebruiker die zich aanmeldt voert het programma). Wanneer **CanRunWhen** niet is ingesteld op **UserLoggedOn**, wordt dit item ingesteld op **FirstUser**.  

-   **Uitgeschakelde**: Geef op of dit programma kan worden aangekondigd aan clients. Beschikbare waarden zijn **True** (Waar) of **False** (Onwaar). De standaardwaarde is **False**.  
