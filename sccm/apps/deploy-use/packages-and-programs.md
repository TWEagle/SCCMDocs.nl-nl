---
title: Pakketten en programma&quot;s | Microsoft-documenten
description: Ondersteuning voor implementaties die pakketten en programma&quot;s of toepassingen met System Center Configuration Manager gebruiken.
ms.custom: na
ms.date: 10/06/2016
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-app
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: caad0507-9913-415a-b13d-d36f8f0a1b80
caps.latest.revision: 8
caps.handback.revision: 0
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 6c5b23270501c11ed5aba9a6045734c73095d1bf
ms.openlocfilehash: 6146bcf4e5aa9df6fe0b8cf71898e488ecf217cc
ms.contentlocale: nl-nl
ms.lasthandoff: 05/17/2017


---
# <a name="packages-and-programs-in-system-center-configuration-manager"></a>Pakketten en programma's in System Center Configuration Manager

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*

System Center Configuration Manager blijft ondersteuning bieden voor pakketten en programma's die werden gebruikt in Configuration Manager 2007. Een implementatie die pakketten en programma's gebruikt is mogelijk beter geschikt dan een implementatie die een toepassing gebruikt wanneer u het volgende implementeert:  

- Toepassingen voor Linux en UNIX-servers
- Scripts die niet worden gebruikt voor het installeren van een toepassing op een computer, zoals een script voor het defragmenteren van het schijfstation van de computer
- 'Eenmalige' scripts die niet voortdurend hoeven te worden bewaakt  
- Scripts die worden uitgevoerd volgens een herhaalde planning en die geen gebruik kunnen maken van globale evaluatie

Wanneer u pakketten vanaf een eerdere versie van Configuration Manager migreert, kunt u ze kunt implementeren in uw Configuration Manager-hiërarchie. Zodra de migratie is voltooid, worden de pakketten weergegeven onder het knooppunt **Pakketten** in de werkruimte **Softwarebibliotheek**.

U kunt wijzigen en implementeren van deze pakketten op dezelfde manier als die u dit hebt gedaan met behulp van softwaredistributie te gebruiken. De **importeren Wizard pakket van definitie** blijft in Configuration Manager te importeren van de oudere pakketten. Aankondigingen worden omgezet in implementaties wanneer ze worden gemigreerd van Configuration Manager 2007 naar een Configuration Manager-hiërarchie.  

> [!NOTE]  
>  U kunt Microsoft System Center Configuration Manager Package Conversion Manager gebruiken om te converteren van pakketten en programma's naar Configuration Manager-toepassingen.  
>   
>  Zie [Configuration Manager Package Conversion Manager](https://technet.microsoft.com/library/hh531519.aspx) voor meer informatie.  

Pakketten kunnen enkele nieuwe kenmerken van Configuration Manager, waaronder distributiepuntgroepen en bewaking gebruiken. Microsoft Application Virtualization (App-V) toepassingen kunnen niet met behulp van pakketten en programma's in Configuration Manager worden gedistribueerd. Virtuele toepassingen distribueren, moet u ze als Configuration Manager-toepassingen.  

##  <a name="create-a-package-and-program"></a>Een pakket en programma maken  
 Gebruik een van deze procedures bij het maken of importeren van pakketten en programma's.  

### <a name="create-a-package-and-program-using-the-create-package-and-program-wizard"></a>Een pakket en programma maken met behulp van de wizard Pakket en Programma maken  

1.  Kies in de Configuration Manager-console **softwarebibliotheek** > **Toepassingsbeheer** > **pakketten**.  

3.  In de **Start** tabblad, in de **maken** groep, kiest u **pakket maken**.  

4.  Op de **pakket** pagina van de **programma Wizard pakket en**, geef de volgende informatie:  

    -   **Naam**: Geef een naam voor het pakket met een maximum van 50 tekens.  

    -   **Beschrijving**: Geef een beschrijving voor dit pakket met maximaal 128 tekens.  

    -   **Fabrikant** (optioneel): Geef een naam van de fabrikant om te achterhalen welk pakket in de Configuration Manager-console. Deze naam mag maximaal 32 tekens lang zijn.

    -   **Taal** (optioneel): Geef de taalversie van het pakket met een maximum van 32 tekens.  

    -   **Versie** (optioneel):  Geef een uniek versienummer op voor het pakket met een maximum van 32 tekens.

    -   **Dit pakket bevat bronbestanden**: Deze instelling geeft aan of het pakket bronbestanden moet aanwezig zijn op clientapparaten vereist. Standaard is dit selectievakje uitgeschakeld en Configuration Manager gebruikt geen distributiepunten voor het pakket. Als dit selectievakje is ingeschakeld, worden distributiepunten gebruikt.  

    -   **Bronmap**: Als het pakket bronbestanden bevat, kiest u **Bladeren** openen van de **bronmap ingesteld** dialoogvenster vak en geeft u de locatie van de bronbestanden voor het pakket.  

        > [!NOTE]  
        >  Het computeraccount van de siteserver moet leesrechten voor de door u opgegeven bronmap hebben.  

5.  Op de **programmatype** pagina van de **programma Wizard pakket en**, selecteer het type programma maken en kies vervolgens **volgende**. U kunt een programma voor een computer of apparaat maken of u kunt deze stap overslaan en later een programma maken.  

    > [!TIP]  
    >  Als u een nieuw programma voor een bestaand pakket maakt, selecteert u eerst het pakket. Klik in de **Start** tabblad, in de **pakket** groep, kiest u **programma maken** openen de **Wizard programma maken**.  

6.  Gebruik een van de volgende procedures om een standaardprogramma of een apparaatprogramma te maken.  

    #### <a name="create-a-standard-program"></a>Maak een standaard programma  

  1.  Op de **programmatype** pagina van de **programma Wizard pakket en**, kies **standaardprogramma**, en kies vervolgens **volgende**.     

    2.  Op de **standaardprogramma** pagina, geeft u de volgende informatie:  

        -   **Naam:** Geef een naam voor het programma met maximaal 50 tekens.  

            > [!NOTE]  
            >  De naam van het programma moet uniek zijn binnen een pakket. Nadat u een programma hebt gemaakt, kunt u de naam niet wijzigen.  

        -   **Opdrachtregel**: Voer de opdrachtregel om te gebruiken voor het starten van dit programma of kies **Bladeren** om naar de locatie van het bestand te bladeren.  

            Als een bestandsnaam geen extensie die opgegeven heeft, wordt Configuration Manager probeert te gebruiken .com, .exe en .bat als mogelijke uitbreidingen.  

             Als het programma wordt uitgevoerd op een client, Configuration Manager eerst gezocht naar de opdrachtregel bestandsnaam in het pakket, zoekopdrachten vooraan in de lokale Windows-map en vervolgens in de lokale gezocht *% path %*. Als het bestand niet kan worden gevonden, treedt een fout op in het programma.  

        -   **Opstartmap** (optioneel): Geef de installatiemap van waaruit het programma wordt uitgevoerd, maximaal 127 tekens. Deze map kan een absoluut pad op de client of een pad ten opzichte van de distributiepuntmap die het pakket bevat zijn.

        -   **Uitvoeren**: Geef de modus waarin het programma wordt uitgevoerd op clientcomputers. Selecteer vervolgens een van de volgende opties:  

            -   **Normaal**: Het programma wordt uitgevoerd in de normale modus op basis van het systeem en standaardprogramma. Dit is de standaardmodus.  

            -   **Geminimaliseerd**: Het programma wordt geminimaliseerd uitgevoerd op clientapparaten. Gebruikers zien de installatieactiviteit in het systeemvak klikt of op de taakbalk.  

            -   **Gemaximaliseerd**: Het programma wordt gemaximaliseerd uitgevoerd op clientapparaten. Gebruikers zien de installatieactiviteit.  

            -   **Verborgen**: Het programma wordt op clientapparaten verborgen. Gebruikers weergegeven niet installatieactiviteit.  

        -   **Programma kan worden uitgevoerd**: Geef op of het programma wordt alleen uitgevoerd als een gebruiker is aangemeld, alleen als er geen gebruiker is aangemeld in of ongeacht of een gebruiker is aangemeld op de clientcomputer.  

        -   **Uitvoermodus**: Geef op of het programma wordt uitgevoerd met beheerdersmachtigingen of met de machtigingen van de gebruiker die momenteel aangemeld.  

        -   **Gebruikers toestaan om te zien en gebruiken met de programma-installatie**: Gebruik deze instelling, indien beschikbaar om op te geven of u wilt toestaan dat gebruikers om te communiceren met de programma-installatie. Dit selectievakje is alleen beschikbaar wanneer **alleen wanneer er geen gebruiker is aangemeld** of **al dan niet een gebruiker is aangemeld** is geselecteerd voor **programma kan worden uitgevoerd** en wanneer **uitvoeren met beheerdersrechten** is geselecteerd voor **uitvoermodus**.  

        -   **Stationsmodus**: Geef informatie over hoe dit programma wordt uitgevoerd op het netwerk. Kies een van de volgende opties:  

            -   **Wordt uitgevoerd met UNC-naam**: Geef op dat het programma wordt uitgevoerd met de naam van een Universal Naming Convention (UNC). Dit is de standaardinstelling.  

            -   **Moet een stationsletter**: Geef op dat het programma een stationsletter vereist om de locatie volledig te kwalificeren. Voor deze instelling kunt Configuration Manager alle beschikbare stationsletter gebruiken op de client.  

            -   **Vereist specifieke stationsletter** : Dat het programma vereist dat een specifieke stationsletter die u opgeeft om te kwalificeren volledig de locatie opgeven (bijvoorbeeld **Z:**). Als de opgegeven stationsletter al op een client gebruikt wordt, wordt het programma niet uitgevoerd.  

        -   **Opnieuw verbinding maken met distributiepunt bij aanmelding op**: Gebruik dit selectievakje in om aan te geven of de clientcomputer opnieuw verbinding met het distributiepunt maakt wanneer de gebruiker zich aanmeldt. Standaard is dit selectievakje niet geselecteerd.  

  3.  Op de **vereisten** pagina van de **maken Wizard pakket en programma,** opgeven van de volgende informatie:  

        -   **Eerst een ander programma uitvoeren**: Gebruik deze instelling om te identificeren van een pakket en programma dat wordt uitgevoerd voordat dit pakket en programma wordt uitgevoerd.  

        -   **Platformvereisten**: Selecteer **dit programma kan worden uitgevoerd op elk platform** of **dit programma kan worden uitgevoerd alleen op specifieke platforms**, en selecteer vervolgens de besturingssystemen die door clients moeten worden uitgevoerd om te kunnen installeren van het pakket en programma.  

        -   **Geschatte schijfruimte**: Geef de hoeveelheid schijfruimte die het programma uit te voeren op de computer vereist. Dit kan worden opgegeven als **Onbekend** (de standaardinstelling) of als een geheel getal groter dan of gelijk aan nul. Als een waarde is opgegeven, moeten er ook eenheden voor de waarde worden opgegeven.  

        -   **Maximale toegestane uitvoeringstijd (minuten)**: Geef de maximale tijd die het programma uit te voeren op de clientcomputer wordt verwacht. Dit kan worden opgegeven als **Onbekend** (de standaardinstelling) of als een geheel getal groter dan nul.  

             Deze waarde is standaard ingesteld op 120 minuten.  

            > [!IMPORTANT]  
            >  Als u onderhoudsvensters gebruikt voor de verzameling waarop dit programma wordt uitgevoerd, een conflict kan optreden als de **maximale toegestane uitvoeringstijd** langer is dan het geplande onderhoudsvenster. Echter, als de maximale uitvoeringstijd is ingesteld op **onbekende**, het programma wordt uitgevoerd tijdens het onderhoudsvenster en gaat door met uitvoeren naar behoefte nadat het onderhoudsvenster is gesloten. Als de gebruiker de maximale uitvoeringstijd op een specifieke periode die langer is dan de lengte van enig beschikbaar onderhoudsvenster instelt, klikt u vervolgens het programma kan niet worden uitgevoerd.  

             Als de waarde is ingesteld op **onbekende**, Configuration Manager stelt de maximaal toegestane uitvoeringstijd als 12 uur (720 minuten).  

            > [!NOTE]  
            >  Als de maximum uitvoeringstijd (hetzij ingesteld door de gebruiker hetzij als de standaardwaarde) overschreden is, Configuration Manager wordt beëindigd als **uitvoeren met beheerdersrechten** is geselecteerd en **gebruikers toestaan om te zien en gebruiken met de programma-installatie** niet is ingeschakeld.  

  4.  Kies **volgende**.  

    #### <a name="create-a-device-program"></a>Maak een apparaatprogramma  

  1.  Op de **programmatype** pagina van de **programma Wizard pakket en**, selecteer **programma voor apparaat**, en kies vervolgens **volgende**.  

  2.  Op de **programma voor apparaat** pagina, geeft u de volgende:  

        -   **Naam**: Geef een naam voor het programma met maximaal 50 tekens.  

            > [!NOTE]  
            >  De naam van het programma moet uniek zijn binnen een pakket. Nadat u een programma hebt gemaakt, kunt u de naam niet wijzigen.  

        -   **Opmerking** (optioneel): Geef een opmerking voor dit apparaatprogramma met maximaal 127 tekens.  

        -   **Downloadmap**: Geef de naam van de map op het Windows CE-apparaat waarop de bronbestanden van het pakket wordt opgeslagen. De standaardwaarde is **\Temp\\**.  

        -   **Opdrachtregel**: Voer de opdrachtregel om te gebruiken voor het starten van dit programma of kies **Bladeren** om naar de locatie van het bestand te bladeren.  

        -   **Opdrachtregel uitvoeren in downloadmap**: Selecteer deze optie om het programma uitvoeren vanaf het eerder opgegeven downloadmap.  

        -   **Opdrachtregel uitvoeren vanuit deze map**: Selecteer deze optie om op te geven van een andere map waaruit u het programma uit te voeren.  

    3.  Op de **vereisten** pagina, geeft u de volgende:  

        -   **Geschatte schijfruimte**: Geef de hoeveelheid schijfruimte die zijn voor de software vereist. Deze is zichtbaar voor gebruikers van mobiele apparaten alvorens het programma te installeren.  

        -   **Programma downloaden**: Informatie over wanneer dit programma kan worden gedownload op mobiele apparaten opgeven. U kunt **Zo snel mogelijk**, **Alleen via een snel netwerk** of **Alleen wanneer het apparaat is vastgezet** opgeven.  

        -   **Aanvullende vereisten**: Geef zonder bijkomende vereisten voor dit programma. Deze worden weergegeven voor gebruikers voordat ze de software installeren. U kunt gebruikers bijvoorbeeld waarschuwen dat ze alle andere toepassingen moeten sluiten voordat ze het programma uitvoeren.  

  4.  Kies **volgende**.  

  7.  Op de **samenvatting** pagina, de acties die zullen worden uitgevoerd en voltooi de wizard.  

 Zorg dat het nieuwe pakket en programma worden weergegeven de **pakketten** knooppunt van de **softwarebibliotheek** werkruimte.  

## <a name="create-a-package-and-program-from-a-package-definition-file"></a>Een pakket en programma maken van een pakketdefinitiebestand  

1.  Kies in de Configuration Manager-console **softwarebibliotheek** > **Toepassingsbeheer** > **pakketten**.  

3.  Op de **Start** tabblad, in de **maken** groep, kiest u **pakket maken vanuit definitie**.  

4.  Op de **pakketdefinitie** pagina van de **definitie Wizard pakket maken van**, een bestaande pakketdefinitiebestand of geef **Bladeren** openen van een nieuwe pakketdefinitiebestand. Nadat u een nieuwe pakketdefinitiebestand hebt opgegeven, selecteert u deze uit de **definitie van het pakket** lijst en kies vervolgens **volgende**.  

5.  Op de **bronbestanden** pagina, informatie over de vereiste bronbestanden voor het pakket en programma opgeven en kies vervolgens **volgende**.  

6.  Als het pakket bronbestanden, vereist op de **bronmap** pagina, geef de locatie waar de bronbestanden kunnen worden verkregen en kies vervolgens **volgende**.  

7.  Op de **samenvatting** pagina, de acties die zullen worden uitgevoerd en voltooi de wizard. Het nieuwe pakket en programma worden weergegeven in de **pakketten** knooppunt van de **softwarebibliotheek** werkruimte.  

 Zie voor meer informatie over pakketdefinitiebestanden [over de bestandsindeling pakket definitie](/sccm/apps/deploy-use/packages-and-programs#about-the-package-definition-file-format) in dit onderwerp.  

##  <a name="deploy-packages-and-programs"></a>Implementeren van pakketten en programma 's  

1.  Kies in de Configuration Manager-console **softwarebibliotheek** > **Toepassingsbeheer** > **pakketten**.  

2.  Selecteer het pakket dat u implementeren wilt, en klik vervolgens in de **Start** tabblad de **implementatie** groep, kiest u **implementeren**.  

3.  Op de **algemeen** pagina van de **Wizard Software implementeren**, geef de naam van het pakket en programma dat u implementeren wilt, de verzameling waarnaar u wilt implementeren de pakket- en programma- en optionele opmerkingen in voor de implementatie.  

     Selecteer **Standaarddistributiepuntengroepen gebruiken die aan deze verzameling zijn gekoppeld** als u de pakketinhoud wilt opslaan op de standaarddistributiepuntengroep van de verzameling. Als u hebt de geselecteerde verzameling niet gekoppeld aan een distributiepuntgroep, is deze optie niet beschikbaar.  

4.  Op de **inhoud** pagina, kiest u **toevoegen**, en selecteer vervolgens de distributiepunten of distributiepuntgroepen waarop u wilt implementeren van de inhoud die is gekoppeld aan dit pakket en programma.  

5.  Op de **implementatie-instellingen** pagina, kies een doel voor deze implementatie, en opties opgeven voor wake-uppakketten en verbindingen naar gebruik:  

    -   **Doel**: U kunt kiezen uit:  

        -   **Beschikbare**: Als de toepassing wordt geïmplementeerd voor een gebruiker, wordt de gebruiker ziet het gepubliceerd pakket en programma in de Application Catalog en kan hij deze op aanvraag. Als het pakket en programma op een apparaat is geïmplementeerd, wordt de gebruiker ziet het in Software Center en kan deze op aanvraag installeren.  

        -   **Vereist**: Het pakket en programma is automatisch geïmplementeerd volgens de geconfigureerde planning. Een gebruiker kan echter de implementatiestatus van het pakket en programma volgen en deze installeren vóór de deadline door het gebruik van het Software Center.  

    -   **Ontwaakpakketten verzenden**: Als het implementatiedoel is ingesteld op **vereist** en deze optie is geselecteerd, wordt een ontwaakpakket verzonden naar computers vóór de implementatie wordt geïnstalleerd om de computer uit de slaapstand deadline van de installatie te halen. Voordat u deze optie kunt gebruiken, moeten computers zijn geconfigureerd voor Wake On LAN.  

    -  **Laat clients toe op een internetverbinding inhoud te downloaden na de installatiedeadline, waarvoor extra kosten in rekening kan worden**: Selecteer deze optie als het is vereist.  

    > [!NOTE]  
    >  De optie **Software implementeren op het primaire apparaat van de gebruiker** is niet beschikbaar wanneer u een pakket en programma implementeert.  

6.  Op de **planning** pagina, wanneer dit pakket en programma zullen worden geïmplementeerd of beschikbaar gesteld voor apparaten van clients configureren.  

     De opties op deze pagina variëren afhankelijk van of de implementatieactie ingesteld is op **beschikbaar** of **vereist**.  

7.  Als het implementatiedoel is ingesteld op **vereist**, het opnieuw downloaden voor het programma van de **gedrag voor opnieuw uitvoeren** vervolgkeuzelijst. Kies uit de volgende opties:  

    |Gedrag voor opnieuw uitvoeren|Meer informatie|  
    |--------------------|----------------------|  
    |Geïmplementeerd programma nooit opnieuw uitvoeren|Het programma won't opnieuw uitgevoerd op de client, zelfs als het programma is mislukt of als de programmabestanden zijn gewijzigd.|  
    |Programma altijd opnieuw uitvoeren|Het programma wordt altijd opnieuw uitgevoerd op de client wanneer de implementatie is gepland, zelfs als het programma al is uitgevoerd. Dit kan nuttig zijn wanneer u herhaalde implementaties gebruikt waarin het programma wordt bijgewerkt, bijvoorbeeld met antivirussoftware.|  
    |Opnieuw uitvoeren als de vorige poging is mislukt|Het programma wordt opnieuw uitgevoerd wanneer de implementatie alleen is gepland als de vorige poging uitvoeren is mislukt.|  
    |Opnieuw uitvoeren als de vorige poging is gelukt|Het programma wordt alleen opnieuw uitgevoerd als het eerder is uitgevoerd op de client. Dit is nuttig wanneer u herhaalde aankondigingen gebruikt waarbij het programma regelmatig wordt bijgewerkt en waarbij het voor elke update vereist is dat de vorige update is geïnstalleerd.|  

8. Geef op de pagina **Gebruikerservaring** de volgende informatie:  

    -   **Toestaan dat gebruikers het programma onafhankelijk van toewijzingen uit te voeren**: Als ingeschakeld, kunnen gebruikers deze software installeren vanuit Software Center ongeacht eventuele geplande installatietijdstip.  

    -   **Software-installatie**: Laat de software installeren buiten de geconfigureerde onderhoudsvensters.  

    -   **Systeem opnieuw opstarten (indien nodig om de installatie te voltooien)**: Als de software-installatie een herstart van het apparaat vereist te voltooien, toestaan dat dit gebeurt buiten de geconfigureerde onderhoudsvensters.  

    -   **Embedded-apparaten**: Wanneer u pakketten en programma's voor Windows Embedded-apparaten waarvoor write filter is ingeschakeld implementeert, kunt u opgeven dat pakketten en programma's worden geïnstalleerd op de tijdelijke overlay en commit wijzigingen later. U kunt ook u de wijzigingen worden doorgevoerd op de installatiedeadline of tijdens onderhoud. Wanneer u wijzigingen op de installatiedeadline of tijdens onderhoud doorvoert, een herstart is vereist en de wijzigingen behouden blijven op het apparaat.  

        > [!NOTE]  
        >  Wanneer u een pakket of programma implementeert op een Windows Embedded-apparaat, moet u ervoor zorgen dat het apparaat lid is van een verzameling met een geconfigureerd onderhoudsvenster. Zie voor meer informatie over hoe onderhoudvensters worden gebruikt wanneer u pakketten en programma's op Windows Embedded-apparaten implementeert, [Windows Embedded maken van toepassingen](../../apps/get-started/creating-windows-embedded-applications.md).  

9. Geef op de pagina **Distributiepunten** de volgende informatie:  

    -   **Implementatie-opties**: Geef de acties die een client rekening houden met moet programma inhoud moet worden uitgevoerd. U kunt gedrag opgeven wanneer de client zich in een snelle netwerkgrens bevindt of in een trage of onbetrouwbare netwerkgrens bevindt.  

    -   **Clients toestaan om inhoud te delen met andere clients in hetzelfde subnet**: Selecteer deze optie om de belasting van het netwerk te verminderen doordat clients inhoud kunnen downloaden van andere clients op het netwerk die reeds zijn gedownload en gecached. Deze optie gebruikt Windows BranchCache en kan worden gebruikt op computers met Windows Vista SP2 of hoger.  

    -   **Clients met een terugvalbronlocatie voor inhoud toestaan**:  

        -  **Oudere versies dan 1610**: Kunt u de **terugvalbronlocatie voor inhoud selectievakje toestaan** waarmee clients buiten deze grensgroepen terug te vallen en het gebruik van de distributie groepen wijst u als bronlocatie voor inhoud wanneer er geen andere distributiepunten beschikbaar zijn.

        - **Versie 1610 en hoger**: U kunt niet meer configureren **terugvalbronlocatie voor inhoud toestaan**.  In plaats daarvan kunt configureren u relaties tussen grensgroepen om te bepalen wanneer een client beginnen kunt met zoeken naar aanvullende grensgroepen voor de locatie van een geldige inhoudsbron.

10. Op de **samenvatting** pagina, de acties die zullen worden uitgevoerd en voltooi de wizard.  

     U ziet de implementatie in het knooppunt **Implementaties** van de werkruimte **Bewaking** en in het detailvenster van het tabblad voor de pakketimplementatie wanneer u de implementatie selecteert. Zie voor meer informatie [pakketten en programma's bewaken](/sccm/apps/deploy-use/packages-and-programs#monitor-packages-and-programs) in dit onderwerp.  

> [!IMPORTANT]  
>  Als u de optie geconfigureerd **programma uitvoeren vanaf distributiepunt** op de **distributiepunten** pagina van de **Wizard Software implementeren**, verwijder de optie **de inhoud in dit pakket kopiëren naar een pakketshare op distributiepunten** omdat hierdoor het pakket niet beschikbaar voor uitvoeren vanaf distributiepunten.  

##  <a name="monitor-packages-and-programs"></a>Monitor voor pakketten en programma 's  
 Als u wilt bewaken pakket en programma-implementaties, gebruikt u dezelfde procedures die u gebruikt voor het bewaken van toepassingen zoals beschreven in [-toepassingen bewaken](/sccm/apps/deploy-use/monitor-applications-from-the-console).  

 Pakketten en programma's bevatten ook een aantal van ingebouwde rapporten waarmee u informatie over de implementatiestatus van pakketten en programma's bewaken. Deze rapporten hebben de rapportcategorie **Softwaredistributie – Pakketten en programma's** en **Softwaredistributie – Status van pakket- en programma-implementatie**.  

 Zie voor meer informatie over het configureren van rapportage in Configuration Manager [rapportage in System Center Configuration Manager](../../core/servers/manage/reporting.md).  

##  <a name="manage-packages-and-programs"></a>Pakketten en programma's beheren  
 In de **softwarebibliotheek** werkruimte Vouw **Toepassingsbeheer**, kies **pakketten**, kiest u het pakket dat u wilt beheren, en kies vervolgens een beheertaak uit de volgende tabel:  

|Taak|Meer informatie|  
|----------|----------------------|  
|**Voorbereid inhoudsbestand maken**|Hiermee opent u de **maken Wizard voorbereid inhoudsbestand**, waarmee u een bestand met de inhoud van het pakket die handmatig geïmporteerd naar een andere site worden kan te maken. Dit is nuttig in situaties met lage netwerkbandbreedte tussen de siteserver en het distributiepunt.|  
|**Programma maken**|Hiermee opent u de **Wizard programma maken**, waarmee u een nieuw programma voor dit pakket maken.|  
|**Exportereneren**|Hiermee opent u de **pakket Wizard exporteren**, waarmee u het geselecteerde pakket en de inhoud naar een bestand exporteren.<br /><br /> Zie voor meer informatie over het importeren van pakketten en programma's [pakketten en programma's maken](/sccm/apps/deploy-use/packages-and-programs#create-packages-and-programs) in dit onderwerp.|  
|**Implementeren**|Hiermee opent u de **Wizard Software implementeren**, waarmee u het geselecteerde pakket en programma te implementeren op een verzameling. Zie voor meer informatie [implementeren van pakketten en programma's](/sccm/apps/deploy-use/packages-and-programs#deploy-packages-and-programs) in dit onderwerp.|  
|**Inhoud distribueren**|Hiermee opent u de **Wizard inhoud distribueren**, waarmee u de inhoud die is gekoppeld aan het pakket en programma naar geselecteerde distributiepunten of distributiepuntgroepen te verzenden.|  
|**Distributiepunten bijwerken**|Hiermee worden distributiepunten bijwerkt met de meest recente inhoud voor het geselecteerde pakket en programma.|  

##  <a name="about-the-package-definition-file-format"></a>Over de bestandsindeling voor pakket-definitie  
 Pakketdefinitiebestanden zijn scripts die u gebruiken kunt voor het automatiseren van pakket en programma maken met Configuration Manager. Ze bevatten alle informatie die Configuration Manager moet maken van een pakket en programma, met uitzondering van de locatie van de pakketbronbestanden. Elke pakketdefinitiebestand is een ASCII- of UTF-8-tekstbestand dat de indeling van ini-bestand gebruikt en die bevat de volgende secties:  

###  <a name="pdf"></a>[PDF]  
 Deze sectie geeft het bestand aan als een pakketdefinitiebestand. De sectie bevat de volgende informatie:  

-   **Versie**: Geef de versie van het pakket Definitie bestandsindeling die wordt gebruikt door het bestand. Dit komt overeen met de versie van de System Management Server (SMS) of Configuration Manager waarvoor deze is geschreven. Dit item is vereist.  

###  <a name="package-definition"></a>[Package Definition]  
 De eigenschappen van het pakket en programma opgeven. De sectie bevat de volgende informatie:  

-   **Naam**: De naam van het pakket, maximaal 50 tekens.  

-   **Versie** (optioneel): De versie van het pakket, maximaal 32 tekens.  

-   **Pictogram** (optioneel): Het bestand dat het pictogram moet worden gebruikt voor dit pakket bevat. Indien opgegeven, vervangt dit pictogram het standaardpictogram pakket in de Configuration Manager-console.

-   **Uitgever**: De uitgever van het pakket, maximaal 32 tekens.

-   **Taal**: De taalversie van het pakket, maximaal 32 tekens.

-   **Opmerking** (optioneel): Een opmerking over het pakket, maximaal 127 tekens.

-   **ContainsNoFiles**: Dit item geeft aan of een bron gekoppeld aan het pakket is.  

-   **Programma's**: De programma's die zijn gedefinieerd voor dit pakket. Elke programmanaam komt overeen met een sectie **[Program]** in dit pakketdefinitiebestand.  

     Voorbeeld:  

     `Programs=Typical, Custom, Uninstall`  

-   **MIFFileName**: De naam van het Management Information Format (MIF)-bestand dat de pakketstatus maximaal 50 tekens bevat.  

-   **MIFName**: De naam van het pakket (voor het MIF-koppeling), met maximaal 50 tekens.  

-   **MIFVersion**: Het versienummer van het pakket (voor het MIF-koppeling), maximaal 32 tekens.  

-   **MIFPublisher**: De software-uitgever van het pakket (voor het MIF-koppeling), maximaal 32 tekens.  

###  <a name="program"></a>[Program]  
 Voor elk programma dat opgegeven in de **programma's** vermelding in de **[pakketdefinitie]** sectie bestand met de pakketdefinitie moet bevatten een sectie [programma] waarmee wordt gedefinieerd dat programma. Elke sectie Program bevat de volgende informatie:  

-   **Naam**: De naam van het programma, maximaal 50 tekens. Dit item moet uniek zijn binnen een pakket. Deze naam wordt gebruikt bij het definiëren van advertenties. Op clientcomputers wordt de naam van het programma weergegeven in **Aangekondigde programma's uitvoeren** in het Configuratiescherm.  

-   **Pictogram** (optioneel): Geef het bestand met het pictogram voor dit programma te gebruiken. Indien opgegeven, wordt dit pictogram vervangt het standaardpictogram programma in de Configuration Manager-console en wordt weergegeven op clientcomputers wordt geïnstalleerd wanneer het programma is aangekondigd.

-   **Opmerking** (optioneel): Een opmerking over het programma, in maximaal 127 tekens.

-   **Voor verwijdering**: Geef op de opdrachtregel voor het programma, in maximaal 127 tekens. De opdracht is relatief ten opzichte van de pakketbronmap.

-   **StartIn**: Geef de map voor het programma, in maximaal 127 tekens. Dit item kan een absoluut pad op de clientcomputer of een pad ten opzichte van de pakketbronmap zijn.

-   **Uitvoeren**: Geef de programma-modus waarin het programma wordt uitgevoerd. U kunt **Minimized** (Geminimaliseerd), **Maximized** (Gemaximaliseerd) of **Hidden** (Verborgen) opgeven. Als dit item niet opgenomen is, wordt het programma in de normale modus uitgevoerd.  

-   **AfterRunning**: Geef geen speciale actie die plaatsvindt nadat het programma is voltooid. Beschikbare opties zijn **SMSRestart**, **ProgramRestart** en **SMSLogoff**. Als dit item niet opgenomen is, kan het programma een speciale bewerking wordt niet uitgevoerd.  

-   **EstimatedDiskSpace**: Geef de hoeveelheid schijfruimte die het programma uit te voeren op de computer vereist. Dit kan worden opgegeven als **Onbekend** (de standaardinstelling) of als een geheel getal groter dan of gelijk aan nul. Als een waarde is opgegeven, moeten ook de eenheden voor de waarde worden opgegeven.  

     Voorbeeld:  

     `EstimatedDiskSpace=38MB`  

-   **EstimatedRunTime**: Geef de geschatte duur (in minuten) die het programma uit te voeren op de clientcomputer wordt verwacht. Dit kan worden opgegeven als **Onbekend** (de standaardinstelling) of als een geheel getal groter dan nul.  

     Voorbeeld:  

     `EstimatedRunTime=25`  

-   **SupportedClients**: Geef de processors en de besturingssystemen waarop dit programma wordt uitgevoerd. De opgegeven platforms moeten van elkaar worden gescheiden door komma's. Als dit item niet opgenomen is, ondersteund platform-controle voor dit programma is uitgeschakeld.  

-   **SupportedClientMinVersionX**, **SupportedClientMaxVersionX**: Geef het bereik begin te beëindigen voor versienummers voor de besturingssystemen die zijn opgegeven in de **SupportedClients** vermelding.  

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

-   **AdditionalProgramRequirements** (optioneel): Geef een andere informatie of vereisten voor clientcomputers maximaal 127 tekens.

-   **CanRunWhen**: Geef de status van de gebruiker die het programma uit te voeren op de clientcomputer is vereist. Beschikbare waarden zijn **UserLoggedOn**, **NoUserLoggedOn** en **AnyUserStatus**. De standaardwaarde is **UserLoggedOn**.  

-   **UserInputRequired**: Geef op of het programma interactie met de gebruiker vereist. Beschikbare waarden zijn **True** (Waar) of **False** (Onwaar). De standaardwaarde is **True** (Waar). Dit item wordt ingesteld op **False** (Onwaar) als **CanRunWhen** niet is ingesteld op **UserLoggedOn**.  

-   **AdminRightsRequired**: Geef op of het programma vereist dat de beheerdersreferenties op de computer om uit te voeren. Beschikbare waarden zijn **True** (Waar) of **False** (Onwaar). De standaardwaarde is **False**. Dit item wordt ingesteld op **True** (Waar) als **CanRunWhen** niet is ingesteld op **UserLoggedOn**.  

-   **UseInstallAccount**: Geef op of het programma Software Account voor de clientinstallatie gebruikt als deze wordt uitgevoerd op clientcomputers. Deze waarde is standaard **False** (Onwaar). Deze waarde is ook **False** (Onwaar) als **CanRunWhen** is ingesteld op **UserLoggedOn**.  

-   **DriveLetterConnection**: Geef op of het programma vereist dat een stationsletter verbinding met het pakketbestanden die op het distributiepunt bevinden zich. U kunt **True** (Waar) of **False** (Onwaar) opgeven. De standaardwaarde is **False**, zodat het programma een Universal Naming Convention (UNC)-verbinding gebruiken. Als deze waarde is ingesteld op **waar**, de eerstvolgende beschikbare stationsletter (vanaf Z: en u achteruit) wordt gebruikt.  

-   **SpecifyDrive** (optioneel): Geef een stationsletter die het programma nodig heeft om verbinding maken met het pakketbestanden op het distributiepunt. Deze specificatie dwingt het gebruik van de opgegeven stationsletter af voor clientverbindingen met distributiepunten.

-   **ReconnectDriveAtLogon**: Geef op of de computer opnieuw verbinding met het distributiepunt maakt wanneer de gebruiker zich aanmeldt. Beschikbare waarden zijn **True** (Waar) of **False** (Onwaar). De standaardwaarde is **False**.  

-   **DependentProgram**: Geef een programma in dit pakket dat moet worden uitgevoerd voordat het huidige programma. Voor item wordt de indeling **DependentProgram**=<**ProgramName>** gebruikt, waarbij **<ProgramName\>** de vermelding in de pakketdefinitie voor dat programma bij **Name** is. Als er geen afhankelijke programma's zijn, laat u dit item leeg.  

     Voorbeeld:  

     DependentProgram=Admin  
    DependentProgram=  

-   **Toewijzing**: Geef op hoe het programma wordt toegewezen aan gebruikers. Deze waarde kan zijn: **FirstUser** (alleen de eerste gebruiker die zich bij de client aanmeldt het programma wordt uitgevoerd) of **EveryUser** (alle gebruikers die zich aanmeldt voert het programma). Wanneer **CanRunWhen** niet is ingesteld op **UserLoggedOn**, wordt dit item ingesteld op **FirstUser**.  

-   **Uitgeschakelde**: Geef op of dit programma kan worden aangekondigd aan clients. Beschikbare waarden zijn **True** (Waar) of **False** (Onwaar). De standaardwaarde is **False**.  

