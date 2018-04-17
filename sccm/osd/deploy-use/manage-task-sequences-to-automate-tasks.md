---
title: Takenreeksen beheren
titleSuffix: Configuration Manager
description: Maken, bewerken, implementeren, importeren en exporteren van takenreeksen voor ze beheren en het automatiseren van taken in uw omgeving.
ms.custom: na
ms.date: 04/10/2018
ms.prod: configuration-manager
ms.reviewer: nac
ms.suite: na
ms.technology:
- configmgr-osd
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: a1f099f1-e9b5-4189-88b3-f53e3b4e4add
caps.latest.revision: 10
author: aczechowski
ms.author: aaroncz
manager: dougeby
ms.openlocfilehash: 9ed5a94d644aa0bdb7d63c3b976da7dd566dfedd
ms.sourcegitcommit: fb84bcb31d825f454785e3d9d8be669e00fe2b27
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/16/2018
---
# <a name="manage-task-sequences-to-automate-tasks-in-system-center-configuration-manager"></a>Takenreeksen beheren om taken te automatiseren in System Center Configuration Manager

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*

Takenreeksen gebruiken voor het automatiseren van de stappen in uw Configuration Manager-omgeving. Deze stappen kunnen een installatiekopie van besturingssysteem implementeren op een doelcomputer, bouwen en vastleggen van een installatiekopie van het besturingssysteem van een set van installatiebestanden van het besturingssysteem en vastleggen en herstellen informatie over de status van de gebruiker. Takenreeksen bevinden zich in de Configuration Manager-console. In de **softwarebibliotheek** werkruimte Vouw **besturingssystemen** en selecteer **Takenreeksen**. De **Takenreeksen** knooppunt, inclusief de submappen die u maakt, wordt gerepliceerd over de Configuration Manager-hiërarchie. Zie voor informatie over het plannen, [planningsoverwegingen voor het automatiseren van taken](../plan-design/planning-considerations-for-automating-tasks.md).  

 Gebruik de volgende secties om takenreeksen te beheren.

##  <a name="BKMK_CreateTaskSequence"></a> Takenreeksen maken  
 Maak takenreeksen via de wizard Takenreeks maken. Met deze wizard kunt u de volgende typen takenreeksen maken:  

|Takenreekstype|Meer informatie|  
|------------------------|----------------------|  
|[Takenreeks voor het installeren van een besturingssysteem](create-a-task-sequence-to-install-an-operating-system.md)|Dit takenreekstype maakt u de stappen voor het installeren van een besturingssysteem, alsmede de optie om te migreren van gebruikersgegevens, omvatten software-updates en toepassingen te installeren.|  
|[De takenreeks om een besturingssysteem te upgraden](create-a-task-sequence-to-upgrade-an-operating-system.md)|Dit takenreekstype maakt de stappen voor het upgraden van een besturingssysteem, alsmede de optie voor opname van software-updates en toepassingen installeren.|  
|[Takenreeks voor het vastleggen van een besturingssysteem](create-a-task-sequence-to-capture-an-operating-system.md)|Dit takenreekstype maakt u de stappen voor het bouwen en vastleggen van een besturingssysteem vanaf een referentiecomputer. U kunt software-updates opnemen en toepassingen installeren op de referentiecomputer voordat de installatiekopie wordt vastgelegd.|  
|[Takenreeks voor het vastleggen en herstellen van gebruikersstatus](create-a-task-sequence-to-capture-and-restore-user-state.md)|Deze takenreeks bevat de stappen waarmee u een bestaande takenreeks kunt toevoegen om de gegevens van de gebruikersstatus vast te leggen en te herstellen.|  
|[Aangepaste takenreeks](create-a-custom-task-sequence.md)|Dit type takenreeks voegt geen stappen aan de takenreeks toe. Een takenreeks bewerken en stappen aan de takenreeks toevoegen nadat deze is gemaakt.|  



## <a name="return-to-previous-page-when-a-task-sequence-fails"></a>Terug naar vorige pagina wanneer een takenreeks mislukt
Wanneer u een takenreeks uitvoert en er een fout is kunt u terugkeren naar een vorige pagina. In eerdere versies van Configuration Manager moest u de takenreeks opnieuw opstarten als er een fout is. Gebruik de **vorige** knop in de volgende scenario's:

- Wanneer een computer wordt opgestart in Windows PE, wordt het dialoogvenster taak sequence bootstrap mogelijk weer voordat de takenreeks beschikbaar is. Wanneer u in dit scenario op Volgende klikt, wordt de laatste pagina van de takenreeks weergegeven met een bericht dat er geen takenreeksen beschikbaar zijn. Nu kunt u **vorige** opnieuw zoeken naar beschikbare takenreeksen. U kunt dit proces herhalen totdat de takenreeks beschikbaar is.
- Wanneer u een takenreeks uitvoert, maar de afhankelijke inhoud pakketten nog niet beschikbaar zijn op distributiepunten zijn, mislukt de takenreeks wordt uitgevoerd. Als de ontbrekende inhoud nog niet is gedistribueerd, moet u deze nu distribueren. Of wacht totdat de inhoud beschikbaar zijn op distributiepunten. Klik vervolgens op **vorige** het zoeken van de reeks taak opnieuw naar de inhoud hebben.

##  <a name="BKMK_ModifyTaskSequence"></a> Een takenreeks bewerken  
 U kunt een takenreeks wijzigen door het toevoegen of verwijderen van de stappen, groepen toevoegen of verwijderen, of door de volgorde van de stappen te wijzigen. Gebruik de volgende procedure om een bestaande takenreeks te wijzigen:  

> [!IMPORTANT]  
>  Wanneer u een takenreeks die is gemaakt met de Wizard Takenreeks maken hebt bewerkt, wordt de naam van de stap kan worden de actie of het type van de stap. U kunt bijvoorbeeld zien dat een stap met de naam 'Partitieschijf 0', de actie voor een stap van het type is [schijf formatteren en partitioneren](../understand/task-sequence-steps.md#BKMK_FormatandPartitionDisk). Alle takenreeksstappen worden gedocumenteerd volgens hun type, niet noodzakelijkerwijs door de naam van de stap die wordt weergegeven in de editor.  

#### <a name="to-edit-a-task-sequence"></a>Een takenreeks bewerken  

1.  Klik in de Configuration Manager-console op **Softwarebibliotheek**.  

2.  Vouw **Besturingssystemen** uit in de werkruimte **Softwarebibliotheek**en klik op **Takenreeksen**.  

3.  Selecteer in de lijst **Takenreeks** de takenreeks die u wilt bewerken.  

4.  Klik in de groep **Takenreeks** in het tabblad **Start** op **Bewerken**en klik vervolgens op een van de volgende bewerkingen:  

    -   Klik op als u een takenreeksstap **toevoegen**, selecteer het type van de stap en klik op de stap om toe te voegen. Als u bijvoorbeeld de stap voor het uitvoeren van de opdrachtregel wilt toevoegen, klikt u op **Toevoegen**, selecteert u **Algemeen**en klikt u vervolgens op **Opdrachtregel uitvoeren**.  

         Zie de tabel die volgt op deze procedure voor een lijst met alle takenreeksstappen en hun type.  

    -   Klik op **Toevoegen**en klik op **Nieuwe groep**om een groep aan de takenreeks toe te voegen. Nadat u een groep toevoegt, kunt u vervolgens stappen toevoegen aan de groep.  

    -   Als de volgorde van de stappen en groepen in de takenreeks wijzigen, selecteert u de stap of groep die u wilt rangschikken en gebruik vervolgens de **Item omhoog verplaatsen** of **Item omlaag verplaatsen** pictogrammen. U kunt slechts één stap of groep op hetzelfde moment verplaatsen.  

    -   Selecteer een stap of groep en klik op **Verwijderen**als u een stap of groep wilt verwijderen.  

5.  Klik op **OK** om de wijzigingen op te slaan.  

 Zie voor een lijst van de beschikbare takenreeksstappen [Takenreeksstappen](../understand/task-sequence-steps.md).  

## <a name="configure-software-center-properties"></a>Eigenschappen van Software Center configureren
Gebruik de volgende procedure om de gegevens voor de takenreeks weergegeven in Software Center te configureren. Deze gegevens zijn alleen ter informatie.  
1. Ga in de Configuration Manager-console naar de **softwarebibliotheek** werkruimte Vouw **besturingssystemen**, en selecteer **Takenreeksen**.
2. Selecteer de takenreeks bewerken en klik op **eigenschappen**.
3. Op de **algemene** tabblad en de volgende instellingen voor Software Center zijn beschikbaar:
  - **Opnieuw opstarten vereist**: Kan de gebruiker weet of opnieuw opstarten vereist tijdens de installatie is.
  - **Grootte (MB) downloaden**: Hiermee geeft u op hoeveel megabytes worden weergegeven in Software Center voor de takenreeks.  
  - **Geschatte uitvoeringstijd (minuten)**: Hiermee geeft u dat de geschatte tijd in minuten die wordt weergegeven in Software Center voor de takenreeks wordt uitgevoerd.

## <a name="configure-advanced-task-sequence-settings"></a>Geavanceerde taak reeks instellingen configureren
Gebruik de volgende procedure om de gegevens voor de takenreeks weergegeven in Software Center te configureren. Deze gegevens zijn alleen ter informatie.  
1. Ga in de Configuration Manager-console naar de **softwarebibliotheek** werkruimte Vouw **besturingssystemen**, en selecteer **Takenreeksen**.
2. Selecteer de takenreeks bewerken en klik op **eigenschappen**.
3. Op de **Geavanceerd** tabblad en de volgende instellingen zijn beschikbaar:

    - **Eerst een ander programma uitvoeren**    
    Schakel dit selectievakje in om uit te voeren op een ander programma (in een ander pakket) voordat de takenreeks wordt uitgevoerd. Standaard is dit selectievakje niet geselecteerd. Het programma dat u opgeeft om uit te voeren eerst hoeft niet te worden afzonderlijk aangekondigd.

        > [!IMPORTANT]     
        Deze instelling geldt alleen voor takenreeksen die in het volledige besturingssysteem worden uitgevoerd. Configuration Manager negeert deze instelling als de takenreeks wordt gestart via PXE of opstartmedia.

    - **Pakket**     
        Wanneer u selecteert **rst een ander programma**, blader naar het pakket met het programma dat moet worden uitgevoerd voordat deze takenreeks.

    - **Programma**     
    Wanneer u selecteert **rst een ander programma**, selecteer het programma dat moet worden uitgevoerd vóór deze takenreeks van de **programma** vervolgkeuzelijst.

        > [!NOTE]    
        > Als het geselecteerde programma niet uitgevoerd op een client, wordt de takenreeks niet uitgevoerd. Als het geselecteerde programma is uitgevoerd, niet wordt opnieuw uitgevoerd zelfs als de takenreeks wordt opnieuw uitgevoerd op dezelfde client.
 
    - **Deze takenreeks uitschakelen op computers waarop deze is geïmplementeerd**    
    Als u deze optie selecteert, worden alle implementaties die deze takenreeks bevatten tijdelijk uitgeschakeld. De takenreeks wordt verwijderd uit de lijst met implementaties die beschikbaar zijn om uit te voeren. Deze wordt niet uitgevoerd totdat deze opnieuw inschakelen. Deze optie is standaard uitgeschakeld.

    - **Maximale toegestane uitvoeringstijd**    
    Hiermee geeft u de maximale tijd (in minuten) die wordt verwacht dat de takenreeks wordt uitgevoerd op de doelcomputer. Gebruik een geheel getal gelijk is aan of groter zijn dan nul. Deze waarde is standaard ingesteld op 120 minuten.

        > [!IMPORTANT]    
        > Als u onderhoudsvensters voor de verzameling waarop deze takenreeks wordt uitgevoerd gebruikt, een conflict optreden als de **maximale toegestane uitvoeringstijd** langer is dan het geplande onderhoudsvenster. Als de maximum uitvoeringstijd is ingesteld op **0**, de takenreeks wordt gestart tijdens het onderhoudsvenster. Gaat door totdat dit is voltooid of mislukt is nadat het onderhoudsvenster is gesloten. Als gevolg hiervan takenreeksen met een maximum uitvoeringstijd is ingesteld op **0** voorbij het einde van de onderhoudsvensters mogelijk uitgevoerd. Als u de maximale uitvoeringstijd voor een bepaalde periode is ingesteld (geen **0**) die langer is dan de lengte van welk beschikbaar onderhoudsvenster en vervolgens de takenreeks kan niet worden uitgevoerd. Zie voor meer informatie [het gebruik van onderhoudsvensters](/sccm/core/clients/manage/collections/use-maintenance-windows).
 
        Als de waarde is ingesteld als **0**, Configuration Manager beoordeelt de maximale toegestane uitvoeringstijd als **12** uur (720 minuten) voor de voortgang controleren. De takenreeks start, zolang de duur van het aftellen niet groter zijn dan de waarde van onderhoud-venster.

    > [!NOTE]    
    > Als de maximum uitvoeringstijd is bereikt, stopt Configuration Manager de takenreeks als deze is ingesteld op uitvoeren met beheerdersrechten en de gebruikers toestaan om te communiceren met deze instelling wordt niet is ingeschakeld. Als de takenreeks zelf niet is gestopt, stopt de bewaking van de takenreeks na de maximaal toegestane uitvoeringstijd Configuration Manager is bereikt. 

    - **Een opstartinstallatiekopie gebruiken**   
        Schakel deze optie in de geselecteerde opstartinstallatiekopie gebruiken wanneer de takenreeks wordt uitgevoerd. 

        Klik op **Bladeren** naar een andere opstartinstallatiekopie selecteren. Schakel deze optie voor het gebruik van de geselecteerde opstartinstallatiekopie uitschakelen wanneer de takenreeks wordt uitgevoerd.

    - **Deze takenreeks kan worden uitgevoerd op elk platform**     
        Als u deze optie selecteert, wordt Configuration Manager het platformtype van de doelcomputer niet gecontroleerd wanneer de takenreeks wordt geïmplementeerd. Deze optie is standaard geselecteerd.

    - **Deze takenreeks kan alleen worden uitgevoerd op de gespecificeerde clientplatforms**    
        Deze optie geeft u de processors, besturingssysteemversies en servicepacks die deze takenreeks kan worden uitgevoerd. Wanneer u deze optie selecteert, moet u ten minste één platform ook geselecteerd in de lijst. Er is geen platforms zijn standaard ingeschakeld. Configuration Manager gebruikt deze informatie wanneer is evalueert welke doelcomputers in een verzameling ontvangen de geïmplementeerde takenreeks.

        > [!NOTE]    
        > Wanneer een takenreeks wordt uitgevoerd vanaf opstartmedia of door PXE-opstartbewerking, deze optie wordt genegeerd en de takenreeks wordt uitgevoerd alsof de optie **dit programma kan worden uitgevoerd op elk platform** is geselecteerd.



## <a name="configure-high-impact-task-sequence-settings"></a>Hoge impact taak reeks instellingen configureren
U kunt een takenreeks als hoge impact instellen en aanpassen van de berichten die gebruikers ontvangen wanneer ze de takenreeks worden uitgevoerd.

### <a name="set-a-task-sequence-as-a-high-impact-task-sequence"></a>Een takenreeks ingesteld als een takenreeks met hoge impact
Gebruik de volgende procedure in te stellen van een takenreeks als hoge impact.
> [!NOTE]    
> Elke takenreeks die voldoet aan bepaalde voorwaarden wordt automatisch gedefinieerd als hoge impact. Zie voor meer informatie [beheren van implementaties met een hoog risico](/sccm/protect/understand/settings-to-manage-high-risk-deployments).

1. Ga in de Configuration Manager-console naar de **softwarebibliotheek** werkruimte Vouw **besturingssystemen**, en selecteer **Takenreeksen**.
2. Selecteer de takenreeks bewerken en klik op **eigenschappen**.
3. Op de **gebruikersmelding** tabblad **dit is een grote impact takenreeks**.

### <a name="create-a-custom-notification-for-high-risk-deployments"></a>Een aangepaste melding voor implementaties met een hoog risico maken
Gebruik de volgende procedure voor het maken van een aangepaste melding voor implementaties met hoge impact.
1. Ga in de Configuration Manager-console naar de **softwarebibliotheek** werkruimte Vouw **besturingssystemen**, en selecteer **Takenreeksen**.
2. Selecteer de takenreeks bewerken en klik op **eigenschappen**.
3. Op de **gebruikersmelding** tabblad **u aangepaste tekst**.
>  [!NOTE]    
>  U kunt alleen de berichttekst gebruiker instellen wanneer de **dit is een grote impact takenreeks** is geselecteerd.

4. Configureer de volgende instellingen (maximaal 255 tekens bestaan voor elk tekstvak):

  **Gebruiker melding kopregel**: Hiermee geeft u de blauwe tekst die wordt weergegeven op de melding voor gebruikers van Software Center. In de gebruikersmelding standaard bevat in deze sectie bijvoorbeeld "Bevestigen voor het bijwerken van het besturingssysteem op deze computer."

  **Gebruiker melding berichttekst**: Er zijn drie tekstvakken waarmee de hoofdtekst van de aangepaste melding. Alle tekstvakken vereisen dat u tekst toevoegen.
  - Eerste tekstvak: Hiermee geeft u de hoofdtekst van tekst, meestal met instructies voor de gebruiker. In de gebruikersmelding standaard bevat in deze sectie bijvoorbeeld 'duurt een upgrade van het besturingssysteem en de computer enkele keren opnieuw opstarten.'
  - Tweede tekstvak: Hiermee geeft u de vetgedrukte onder de hoofdtekst. In de gebruikersmelding standaard bevat in deze sectie bijvoorbeeld 'deze in-place upgrade wordt het nieuwe besturingssysteem geïnstalleerd en worden uw apps, gegevens en instellingen automatisch gemigreerd.'
  - Derde tekstvak: Hiermee geeft u de laatste regel van de tekst onder de vetgedrukte. In de gebruikersmelding standaard in deze sectie bevat bijvoorbeeld "klikt u op installeren om te beginnen. Klik anders op Annuleren."   
    
Stel dat u de volgende aangepaste melding in de eigenschappen configureren.

![Aangepaste gebruikersmelding tabblad van de eigenschappen van takenreeks](..\media\user-notification.png)

Het volgende bericht wordt weergegeven wanneer de gebruiker de installatie van Software Center opent.

![Aangepaste taak sequence melding voor de eindgebruiker vanuit Software Center](..\media\user-notification-enduser.png)


##  <a name="BKMK_DistributeTS"></a> Inhoud distribueren waarnaar wordt verwezen door een specifieke takenreeks  
 Voordat clients een takenreeks uitvoeren die naar inhoud verwijst, moet u deze inhoud distribueren naar distributiepunten. U kunt op elk gewenst moment de takenreeks selecteren en de bijbehorende inhoud distribueren om een nieuwe lijst met referentiepakketten voor distributie te bouwen. Als u wijzigingen aanbrengt in de takenreeks met bijgewerkte inhoud, moet u de inhoud herverdelen voordat deze beschikbaar is voor clients. Gebruik de volgende procedure om de inhoud te distribueren waarnaar een takenreeks verwijst.  

#### <a name="to-distribute-referenced-content-to-distribution-points"></a>Inhoud waarnaar wordt verwezen, distribueren naar distributiepunten  

1.  Klik in de Configuration Manager-console op **Softwarebibliotheek**.  

2.  Vouw **Besturingssystemen** uit in de werkruimte **Softwarebibliotheek**en klik op **Takenreeksen**.  

3.  Selecteer in de lijst **Takenreeks** de takenreeks die u wilt distribueren.  

4.  Klik op het tabblad **Start** in de groep **Implementatie** op **Inhoud distribueren** om de wizard Inhoud distribueren te starten.  

5.  Op de **algemene** pagina, controleert u of dat de juiste takenreeks is geselecteerd voor distributie. Klik op **Volgende**.  

6.  Controleer de te distribueren inhoud op de pagina **Inhoud** , zoals een installatiekopie waarnaar de takenreeks verwijst, en klik vervolgens op **Volgende**.  

7.  Op de **doel van inhoud** pagina, geeft u de verzamelingen, distributiepunt of distributiepuntgroep waar u de takenreeksinhoud distribueren. Klik op **Volgende**.  

    > [!IMPORTANT]  
    >  Als de takenreeks die u hebt geselecteerd, verwijst naar inhoud die al is gedistribueerd naar een specifiek distributiepunt, wordt dat distributiepunt niet vermeld in de wizard.  

8.  Voltooi de wizard.  

 U kunt de inhoud voorbereiden waarnaar in de takenreeks wordt verwezen. Configuration Manager maakt een gecomprimeerd, voorbereid inhoudsbestand dat de bestanden, gekoppelde afhankelijkheden, en gekoppelde metagegevens bevat voor de inhoud die u selecteert. U kunt vervolgens de inhoud handmatig importeren via een siteserver, secundaire site of distributiepunt. Zie voor meer informatie over het voorbereiden van inhoudsbestanden [inhoud voorbereiden](../../core/servers/deploy/configure/deploy-and-manage-content.md#bkmk_prestage).  



##  <a name="BKMK_DeployTS"></a> Een takenreeks implementeren  
 Gebruik de volgende procedure om een takenreeks te implementeren voor de computers in een verzameling.  

> [!WARNING]  
>  U kunt het gedrag voor de implementatie van takenreeksen met een hoge risico beheren. Een implementatie met een hoog risico is een implementatie die automatisch wordt geïnstalleerd en de potentie heeft om ongewenste resultaten te veroorzaken. Bijvoorbeeld een takenreeks met het doel van **vereist** die een besturingssysteem implementeert wordt beschouwd als een implementatie met hoog risico. Zie voor meer informatie [instellingen voor het beheren van implementaties met een hoog risico](../../protect/understand/settings-to-manage-high-risk-deployments.md).  

> [!NOTE]  
>  De statusberichten voor de takenreeksimplementatie worden wel weergegeven in het venster Bericht op een primaire site, maar niet op een centrale beheersite.  

#### <a name="to-deploy-a-task-sequence"></a>Een takenreeks implementeren    

1.  Klik in de Configuration Manager-console op **Softwarebibliotheek**.  

2.  Vouw **Besturingssystemen** uit in de werkruimte **Softwarebibliotheek**en klik op **Takenreeksen**.  

3.  Selecteer in de lijst **Takenreeks** de takenreeks die u wilt implementeren.  

4.  Klik op het tabblad **Start** in de groep **Implementatie** op **Implementeren**.  

    > [!NOTE]  
    >  Als **Implementeren** niet beschikbaar is, beschikt de takenreeks over een ongeldige verwijzing. Corrigeer de verwijzing en probeer vervolgens opnieuw of u de takenreeks kunt implementeren.  

5.  Geef op de pagina **Algemeen** de volgende informatie op en klik op **Volgende**.  

    -   **Takenreeks**: Geef de takenreeks die u wilt implementeren. In dit vak wordt standaard de takenreeks weergegeven die u hebt geselecteerd.  

    -   **Verzameling**: Geef de verzameling waartoe de computers om te worden uitgevoerd van de takenreeks wordt uitgevoerd.  

         Implementeer geen takenreeks waarin installeert van een besturingssysteem naar ongeschikte verzamelingen, zoals de **alle systemen** verzameling. Zorg ervoor dat de verzameling die u selecteert alleen de computers bevat waarop u de takenreeks wilt uitvoeren.  

        > [!NOTE]  
        >  Wanneer u een implementatie met hoog risico, zoals een besturingssysteem implementeert de **verzameling selecteren** venster geeft alleen de aangepaste verzamelingen die voldoen aan de implementatie van de verificatie-instellingen die zijn geconfigureerd in de site eigenschappen. Implementaties met een hoog risico zijn altijd beperkt tot aangepaste verzamelingen, verzamelingen die u zelf maakt en de ingebouwde verzameling **Onbekende computers** . Wanneer u een implementatie met een hoog risico maakt, kunt u geen ingebouwde verzameling selecteren, zoals **Alle systemen**. Schakel het selectievakje **lid zamelingen verbergen groter is dan de minimale configuratiegrootte** voor een overzicht van alle aangepaste verzamelingen die minder clients dan het geconfigureerde maximum bevatten. Zie voor meer informatie [instellingen voor het beheren van implementaties met een hoog risico](../../protect/understand/settings-to-manage-high-risk-deployments.md).  
        >   
        >  De instellingen voor het verifiëren van de implementatie zijn gebaseerd op het huidige lidmaatschap van de verzameling. Nadat u een takenreeks hebt geïmplementeerd, wordt het lidmaatschap van de verzameling niet opnieuw geëvalueerd voor de instellingen van de implementatie met een hoog risico.  
        >   
        >  Bijvoorbeeld, Stel dat u **standaardgrootte** en 100 en de **maximumgrootte** tot en met 1000. Wanneer u een implementatie met hoog risico maakt de **verzameling selecteren** venster verzamelingen weergegeven die minder dan 100 clients bevatten alleen weergegeven. Als u het selectievakje de **lid zamelingen verbergen groter is dan de minimale configuratiegrootte** instelt, het venster worden verzamelingen weergegeven die minder dan 1000 clients bevatten.  
        >   
        >  Wanneer u een verzameling met een siterol selecteert, geldt het volgende gedrag:  
        >   
        >  -   Als de verzameling een sitesysteemserver bevat en u de verificatie-instellingen voor de implementatie verzamelingen moeten worden geblokkeerd geconfigureerd met sitesysteemservers, optreedt een fout. U kunt niet doorgaan met het maken van de implementatie.  
        > -   Als een van de volgende criteria van toepassing is, geeft de Wizard Software implementeren een waarschuwing voor een hoog risico. Als u wilt doorgaan, moet u akkoord gaat met de implementatie van een hoog risico maakt. De site wordt een controlestatusbericht gegenereerd.
        >     - Als de verzameling een sitesysteemserver bevat en u de verificatie-instellingen voor de implementatie om u te waarschuwen bij verzamelingen met sitesysteemservers geconfigureerd
        >     - Als de verzameling de standaardgrootte overschrijdt
        >     - Als de verzameling een server bevat  

    -   **Commentaren (optioneel)**: Geef aanvullende informatie die deze implementatie van de takenreeks beschrijft.  
    - **Implementatiesjabloon selecteren**: Vanaf Configuration Manager versie 1802,<!--1357391--> u kunt opslaan en een implementatiesjabloon-voor een takenreeks opgeven.     

         > [!IMPORTANT]
         > In Configuration Manager versie 1802, worden sommige items niet opgeslagen in de sjabloon.  <!--510610--> Zorg ervoor dat u de volgende items toepassen wanneer u de implementatiewizard uitvoert:
         > - Software-installatie 
         > - Plannen 
         > - Inhoud vooraf downloaden
 
6.  Geef op de pagina **Implementatie-instellingen** de volgende informatie op en klik vervolgens op **Volgende**.  

    -   **Doel**: Kies een van de volgende opties in de vervolgkeuzelijst:  

        -   **Beschikbare**: Als de takenreeks wordt geïmplementeerd voor een gebruiker, wordt de gebruiker wordt de gepubliceerde takenreeks weergegeven in de Application Catalog en kan deze op aanvraag opvragen. Als de takenreeks wordt geïmplementeerd op een apparaat, wordt de gebruiker ziet het in Software Center en kan deze op verzoek installeren.  

        -   **Vereist**: De takenreeks wordt automatisch geïmplementeerd volgens de geconfigureerde planning. Als de takenreeks niet verborgen is, kan een gebruiker nog steeds de implementatiestatus bijhouden. Ze kunnen ook de takenreeks wordt uitgevoerd vóór de deadline installeren met behulp van het Software Center.  

    -   **Automatisch implementeren volgens schema of een gebruiker is aangemeld of niet**: Deze optie is niet beschikbaar wanneer u een takenreeks implementeert.  

    -   **Verzenden van ontwaakpakketten**: Als het implementatiedoel is ingesteld op **vereist** en deze optie is geselecteerd, stuurt de site een ontwaakpakket naar computers voordat de implementatie wordt uitgevoerd. Dit pakket uit de slaapstand wordt de computer uit de slaapstand deadline van de installatie. Voordat u deze optie kunt gebruiken, moeten computers en netwerken zijn geconfigureerd voor Wake On LAN.  

    -   **Laat clients toe op een internetverbinding naar gebruik om inhoud te downloaden na de installatiedeadline, waarvoor extra kosten in rekening kan worden**: Wanneer u een takenreeks die een toepassing installeert, maar implementeert een besturingssysteem niet hebt, kunt u opgeven of clients inhoud downloaden na een installatiedeadline wanneer ze internetverbindingen naar gebruik. Internetproviders brengen soms de hoeveelheid gegevens die u verzendt en ontvangt in rekening wanneer u gebruikmaakt van een internetverbinding naar gebruik.  

        > [!NOTE]  
        >  Tijdens het gebruik van een internetverbinding kan werken voor takenreeksen die geen een besturingssysteem implementeren, wordt niet ondersteund.  

    -   **Goedkeuring door beheerder vereisen als gebruikers deze toepassing aanvragen**: Deze optie is niet beschikbaar wanneer u een takenreeks implementeert.  

    -   **Toegankelijk maken voor de volgende**: Opgeven of de takenreeks beschikbaar is voor Configuration Manager-clients, media of PXE.  

        > [!IMPORTANT]  
        >  Gebruik de instelling **Alleen media en PXE (verborgen)** voor geautomatiseerde implementaties van takenreeksen. Als de computer automatisch opstarten naar de implementatie zonder gebruikersinteractie, schakelt u **implementatie van besturingssysteem zonder toezicht toestaan** en stel de SMSTSPreferredAdvertID-variabele als onderdeel van de media. Zie voor meer informatie over takenreeksvariabelen [ingebouwde variabelen voor takenreeksen](../understand/task-sequence-built-in-variables.md)  

7.  Geef op de pagina **Planning** de volgende informatie op en klik vervolgens op **Volgende**.  

    > [!IMPORTANT]  
    >  Wanneer een Windows PE-client wordt gestart vanaf PXE- of opstartmedium, evalueert de client geen implementatieschema's (starten, verlopen of deadlinetijden). Alleen schema's configureren in implementaties van clients die vanaf het volledige Windows-besturingssysteem starten. Overweeg het gebruik van andere methoden, zoals onderhoudvensters, waarmee reeksen actieve taken worden beheerd die geïmplementeerd zijn op clients die starten vanaf Windows PE.  

    -   **Plannen wanneer deze implementatie beschikbaar zal worden**: Geef de datum en tijd waarop de takenreeks beschikbaar is voor uitvoeren op de doelcomputer. Wanneer u het selectievakje **UTC** inschakelt, zorgt deze instelling ervoor dat de takenreeks voor meerdere doelcomputers tegelijk beschikbaar is in plaats van op verschillende tijdstippen, op basis van de lokale tijd op de doelcomputers.  

         Als de begintijdstip eerder is dan het vereiste tijdstip, downloadt de client de takenreeks op het begintijdstip dat u opgeeft.  

    -   **Plannen wanneer deze implementatie zal verlopen**: Geef de datum en tijd waarop de takenreeks verloopt op de doelcomputer. Wanneer u het selectievakje **UTC** inschakelt, zorgt deze instelling ervoor dat de takenreeks op meerdere doelcomputers tegelijk verloopt is in plaats van op verschillende tijdstippen, op basis van de lokale tijd op de doelcomputers.  

    -   **Toewijzingsplanning**: Geef op wanneer de vereiste takenreeks wordt uitgevoerd op de doelcomputer. U kunt meerdere planningen toevoegen.  

         U kunt de datum en het tijdstip opgeven waarop de planning begint, of taken wekelijks, maandelijks of op basis van een aangepast interval moeten worden uitgevoerd en of de takenreeks moet worden uitgevoerd na een gebeurtenis, zoals het aanmelden of afmelden van de computer.  

        > [!NOTE]  
        >  Als u plant een begintijd voor een vereiste takenreeks dat eerder is dan de datum en tijd waarop de takenreeks beschikbaar is, downloadt de Configuration Manager-client de takenreeks op het geplande begintijdstip, ondanks dat de takenreeks wordt uitgevoerd op een eerder tijdstip beschikbaar is.  

    -   **Gedrag voor opnieuw uitvoeren**: Geef op wanneer de takenreeks opnieuw wordt uitgevoerd. U kunt een van de volgende opties opgeven:  

        -   **Geïmplementeerd programma nooit opnieuw uitvoeren**: Als de client de takenreeks eerder is uitgevoerd, niet de opnieuw uitvoeren. De takenreeks niet opnieuw uitgevoerd zelfs als deze is mislukt of de takenreeksbestanden zijn gewijzigd.  

        -   **Programma altijd opnieuw uitvoeren**: De takenreeks wordt altijd opnieuw uitgevoerd op de client wanneer de implementatie is gepland, zelfs als de takenreeks al eerder met succes uitgevoerd. Deze instelling is nuttig wanneer u herhaalde implementaties waarin de takenreeks regelmatig wordt bijgewerkt.  

            > [!IMPORTANT]  
            >  Hoewel deze optie is standaard ingesteld, heeft geen effect totdat u een vereiste implementatie toewijst. Beschikbare implementaties kunnen door een gebruiker altijd opnieuw worden uitgevoerd.  

        -   **Opnieuw uitvoeren als de vorige poging is mislukt**: De takenreeks wordt opnieuw uitgevoerd wanneer de implementatie alleen is gepland als de takenreeks uitvoeren eerder is mislukt. Deze instelling is nuttig voor vereiste implementaties. Als de laatste poging tot uitvoeren mislukt is, proberen ze automatisch opnieuw uitgevoerd volgens de toewijzingsplanning op.  

        -   Opnieuw uitvoeren als de vorige poging is gelukt: De takenreeks wordt alleen opnieuw uitgevoerd als deze eerder is uitgevoerd op de client. Deze instelling is bijzonder nuttig wanneer u herhaalde implementaties gebruikt waarbij de takenreeks regelmatig wordt bijgewerkt en waarbij het voor elke update vereist is dat de vorige update is geïnstalleerd.  

        > [!NOTE]  
        >  Omdat een gebruiker kan een beschikbare takenreeksimplementatie opnieuw, zorg dat voordat u een beschikbare takenreeks in een productieomgeving implementeert, zorgvuldig beoordelen en testen van wat er gebeurt als een gebruiker de takenreeks meerdere keren.  

8.  Geef op de pagina **Gebruikerservaring** de volgende informatie op en klik op **Volgende**.  

    -   **Toestaan dat gebruikers het programma onafhankelijk van toewijzingen uit te voeren**: Geef op of de gebruiker kan een vereiste takenreeks onafhankelijk van de implementatietoewijzingen uitvoeren.  

    -   **Voortgang van Takenreeks weergeven**: Geef aan of Configuration Manager-client de voortgang van de takenreeks weergeeft.  

    -   **Software-installatie**: Geef op of de gebruiker is toegestaan voor het installeren van software buiten een geconfigureerd onderhoudsvenster na de geplande tijd.  

    -   **Systeem opnieuw opstarten (indien nodig om de installatie te voltooien)**: Geef op of de gebruiker mag de computer opnieuw opstarten na een software-installatie buiten een geconfigureerd onderhoudsvenster na de toegewezen periode.  

    -   **Takenreeks mag worden uitgevoerd voor de client op Internet**: Geef op of de takenreeks mag worden uitgevoerd op een client met internet. Bewerkingen die software, zoals een besturingssysteem installeert, worden niet ondersteund met deze instelling. Gebruik deze optie alleen voor algemene scripts gebaseerde takenreeksen die bewerkingen in de standaard OS uitvoeren.  

         - Vanaf versie 1802, wordt deze instelling ondersteund voor implementaties van een takenreeks Windows 10 in-place upgrade op internet gebaseerde clients via de cloud management gateway. Zie voor meer informatie [Windows 10 implementeren in-place upgrade via CMG](#deploy-windows-10-in-place-upgrade-via-cmg).    

9. Geef op de pagina **Waarschuwingen** de waarschuwingsinstelling die u wilt voor de implementatie van deze takenreeks en klik vervolgens op **Volgende**.  

10. Geef op de pagina **Distributiepunten** de volgende informatie op en klik vervolgens op **Volgende**.  

    -   **Implementatieopties**: Geef een van de volgende opties:  

        > [!NOTE]  
        >  Wanneer u multicast gebruikt voor het implementeren van een besturingssysteem, moet de inhoud worden gedownload naar de doelcomputers nodig is of voordat de takenreeks wordt uitgevoerd.  

        -   Geef op dat clients inhoud wanneer dat voor de takenreeks nodig is, vanaf het distributiepunt downloaden naar de doelcomputer.  

        -   Geef op dat de clients alle inhoud vanaf het distributiepunt naar de doelcomputer downloaden voordat de takenreeks wordt uitgevoerd. Deze optie niet wordt weergegeven als u hebt opgegeven dat de takenreeks beschikbaar is voor PXE en opstartmedia-implementaties op de **implementatie-instellingen** pagina.  

        -   Geef op dat clients de inhoud uitvoeren vanaf het distributiepunt. Deze optie is beschikbaar, alleen wanneer alle pakketten die zijn gekoppeld aan de takenreeks zijn ingeschakeld voor het gebruik van een pakketshare op het distributiepunt. Zie het tabblad **Gegevenstoegang** in de **eigenschappen** van de afzonderlijke pakketten voor informatie over het inschakelen van inhoud voor het gebruik van een pakketshare.  

    -   **Een extern distributiepunt gebruiken wanneer geen lokaal distributiepunt beschikbaar is,**: Specificeer of clients distributiepunten die zich op trage en onbetrouwbare netwerken voor het downloaden van de inhoud die is door de takenreeks vereist kunnen gebruiken.  
11. Vanaf Configuration Manager 1802, op de **samenvatting** tabblad, klikt u op **opslaan als sjabloon** als u wilt opslaan van de instellingen opnieuw te gebruiken. Geef een naam voor de sjabloon en selecteer de instellingen wilt opslaan. 

 
12. Voltooi de wizard.  


### <a name="deploy-windows-10-in-place-upgrade-via-cmg"></a>In-place upgrade van Windows 10 via CMG implementeren
<!-- 1357149 -->

Vanaf versie 1802, de takenreeks Windows 10 in-place upgrade ondersteunt de implementatie op internet gebaseerde clients beheerd via de [management cloudgateway](/sccm/core/clients/manage/plan-cloud-management-gateway) (CMG). Deze mogelijkheid kunnen externe gebruikers gemakkelijker upgraden naar Windows 10 zonder verbinding maken met het intranet. 

Zorg ervoor dat alle inhoud waarnaar wordt verwezen door de takenreeks in-place upgrade wordt gedistribueerd naar een [clouddistributiepunt](/sccm/core/plan-design/hierarchy/use-a-cloud-based-distribution-point). Apparaten kunnen de takenreeks anders niet uitvoeren.

Wanneer u een takenreeks voor upgraden implementeert, gebruikt u de volgende instellingen:
- **Takenreeks mag worden uitgevoerd voor de client op Internet**, op het tabblad gebruikerservaring van de implementatie.
- **Alle inhoud lokaal downloaden voordat de takenreeks wordt gestart**, op het tabblad distributiepunten van de implementatie. Andere opties zoals **inhoud lokaal downloaden wanneer nodig is voor de actieve takenreeks** werken niet in dit scenario. De engine voor takenreeksen is momenteel niet mogelijk om inhoud te verkrijgen van een cloud-distributiepunt. Configuration Manager-client moet de inhoud van het cloud-distributiepunt downloaden voordat de takenreeks wordt gestart.
- (*Optioneel*) **vooraf downloaden van inhoud voor deze takenreeks**, op het tabblad Algemeen van de implementatie. Zie voor meer informatie [vooraf cache-inhoud configureren](/sccm/osd/deploy-use/create-a-task-sequence-to-upgrade-an-operating-system#configure-pre-cache-content).



##  <a name="BKMK_ExportImport"></a> Takenreeksen exporteren en importeren  
 U kunt exporteren en importeren van takenreeksen met of zonder de bijbehorende objecten. Deze inhoud waarnaar wordt verwezen bevat een installatiekopie van het besturingssysteem, een opstartinstallatiekopie, een clientagentpakket, een stuurprogrammapakket en toepassingen met afhankelijkheden.  

 Houd rekening met het volgende als u takenreeksen exporteert en importeert.  

-   Wachtwoorden die in de takenreeks zijn opgeslagen, worden niet geëxporteerd. Als u exporteren en importeren van een takenreeks die wachtwoorden bevat, moet u de geïmporteerde takenreeks bewerken en voer de wachtwoorden opnieuw in. Zorg ervoor dat u wachtwoorden opgeeft voor [lid worden van domein of werkgroep](../understand/task-sequence-steps.md#BKMK_JoinDomainorWorkgroup), [netwerkmap verbinding](../understand/task-sequence-steps.md#BKMK_ConnectToNetworkFolder), en [opdrachtregel uitvoeren](../understand/task-sequence-steps.md#BKMK_RunCommandLine) acties.  

- Tijdens het exporteren van een takenreeks met de **dynamische variabelen instellen** stap geen waarden worden geëxporteerd voor variabelen die zijn geconfigureerd met de **geheime waarde** instelling. Geef de waarden voor deze variabelen opnieuw nadat u de takenreeks hebt geïmporteerd.

-   Het is een aanbevolen procedure om takenreeksen via de centrale beheersite te importeren wanneer u meerdere primaire sites hebt.  

 Gebruik de volgende procedures voor het exporteren en importeren van een takenreeks.  

#### <a name="to-export-task-sequences"></a>Takenreeksen exporteren  

1.  Klik in de Configuration Manager-console op **Softwarebibliotheek**.  

2.  Vouw **Besturingssystemen** uit in de werkruimte **Softwarebibliotheek**en klik op **Takenreeksen**.  

3.  Selecteer in de lijst **Takenreeks** de takenreeks die u wilt exporteren. Als u meer dan één takenreeks selecteert, worden de takenreeksen opgeslagen in één exportbestand.  

4.  Klik op tabblad **Start** in de groep **Takenreeks** op **Exporteren** om de wizard Takenreeks exporteren te starten.  

5.  Stel op de pagina **Algemeen** de volgende instellingen in en klik op **Volgende**.  

    -   Geef in het vak **Bestand** de locatie en de naam van het exportbestand op. Als u de bestandsnaam rechtstreeks invoert, moet u de extensie (.zip) opnemen in de bestandsnaam. Als u naar het exportbestand bladert, wordt de extensie door de wizard automatisch aan deze bestandsnaam toegevoegd.  

    -   Schakel het selectievakje **Alle afhankelijkheden van takenreeksen exporteren** uit als u de afhankelijkheden van de takenreeks niet wilt exporteren. De wizard scant standaard op alle bijbehorende objecten en exporteert deze met de takenreeks. Deze afhankelijkheden bevatten voor toepassingen.  

    -   Schakel het selectievakje **Alle inhoud voor de geselecteerde takenreeksen en afhankelijkheden exporteren** uit als u de inhoud uit het bronpakket niet naar de exportlocatie wilt kopiëren. Als dit selectievakje is ingeschakeld, gebruikt de wizard Takenreeks importeren het importpad als de nieuwe pakketbronlocatie.  

    -   Voeg in het vak **Opmerkingen beheerder** een beschrijving toe van de takenreeksen die moeten worden geëxporteerd.  

6.  Voltooi de wizard.  

 De wizard maakt de volgende uitvoerbestanden:  

-   Als u geen inhoud exporteert: een ZIP-bestand.  

-   Als u inhoud exporteert: een ZIP-bestand en een map met de naam *export*_files, waarbij *export* de naam is van het ZIP-bestand dat de geëxporteerde inhoud bevat.  

 Als u inhoud opneemt wanneer u een takenreeks exporteert, zorgt u ervoor dat u het ZIP-bestand kopiëren en de *exporteren*_files map of het importeren is mislukt.  

#### <a name="to-import-task-sequences"></a>Takenreeksen importeren  

1.  Klik in de Configuration Manager-console op **Softwarebibliotheek**.  

2.  Vouw **Besturingssystemen** uit in de werkruimte **Softwarebibliotheek**en klik op **Takenreeksen**.  

3.  Klik op het tabblad **Start** in de groep **Maken** op **Takenreeks importeren** om de wizard Takenreeks importeren te starten.  

4.  Specificeer op de pagina **Algemeen** het geëxporteerde ZIP-bestand en klik daarna op **Volgende**.  

5.  Selecteer op de pagina **Bestandsinhoud** de actie die u nodig hebt voor elk object dat u importeert. Deze pagina bevat alle objecten die Configuration Manager vinden om te importeren.  

    -   Selecteer **Nieuw**, als het object nog nooit is geïmporteerd.  

    -   Selecteer een van de volgende acties, als het object al eerder is geïmporteerd:  

        -   **Dubbele negeren** (standaard): Deze actie wordt het object niet geïmporteerd. In plaats daarvan koppelt de wizard het bestaande object aan de takenreeks.  

        -   **Overschrijven**: Deze actie wordt het bestaande object overschreven door het geïmporteerde object. Voor toepassingen kunt u een revisie toevoegen om de bestaande toepassing bij te werken of een nieuwe toepassing te maken.  

6.  Voltooi de wizard.  

 Wanneer u de takenreeks hebt geïmporteerd, bewerkt u de takenreeks zo, dat deze wachtwoorden opgeeft die geldig waren in de oorspronkelijke takenreeks. Uit veiligheidsoverwegingen zijn wachtwoorden niet geëxporteerd.  

##  <a name="BKMK_CreateTSVariables"></a> Takenreeksvariabelen voor computers en verzamelingen maken  
U kunt takenreeksvariabelen definiëren voor computers en verzamelingen. Naar variabelen die voor een computer zijn gedefinieerd, wordt verwezen als computertakenreeksvariabelen. Naar variabelen die voor een verzameling zijn gedefinieerd, wordt verwezen als verzamelingtakenreeksvariabelen. Bij een conflict gaan computervariabelen boven verzamelingsvariabelen. Dit gedrag betekent dat takenreeksvariabelen die zijn toegewezen aan een specifieke computer automatisch een hogere prioriteit dan variabelen die zijn toegewezen aan de verzameling die de computer bevat.  

Als bijvoorbeeld verzameling ABC een variabele krijgt toegewezen en computer XYZ, die lid is van verzameling ABC, een variabele met dezelfde naam krijgt toegewezen, heeft de aan computer XYZ toegewezen variabele een hogere prioriteit dan de aan verzameling ABC toegewezen variabele.  

U kunt computer- en per-verzameling verzamelingsvariabelen verbergen, zodat ze niet zichtbaar in de Configuration Manager-console. Als u deze variabelen niet meer verborgen wilt houden, moet u deze verwijderen en opnieuw definiëren, zonder de optie te selecteren om deze te verbergen. Wanneer u de optie gebruikt **deze waarde niet weergeven in de Configuration Manager-console**, de waarde van de variabele niet wordt weergegeven in de console. De variabele kan nog steeds worden gebruikt door de takenreeks wanneer deze wordt uitgevoerd.  

> [!WARNING]    
> De **deze waarde niet weergeven in de Configuration Manager-console** instelling geldt alleen voor de Configuration Manager-console. De waarden voor de variabelen nog steeds worden weergegeven in het logboekbestand van taak sequence (SMSTS. LOGBOEK). 

U kunt per computer variabelen op een primaire site of op een centrale beheersite beheren. Configuration Manager biedt geen ondersteuning voor meer dan 1000 toegewezen variabelen voor een computer.  

> [!IMPORTANT]  
>  Wanneer u verzamelingsvariabelen voor takenreeksen gebruikt, houd rekening met de volgende problemen:  
>   
> - Wijzigingen in verzamelingen worden altijd gerepliceerd in de gehele hiërarchie. Eventuele wijzigingen die u in de verzameling-variabelen aanbrengt gelden niet alleen voor leden van de huidige site, maar op alle leden van de verzameling in de gehele hiërarchie.  
> - Wanneer u een verzameling verwijdert, wordt door deze actie tevens de takenreeksvariabelen verwijderd die voor de verzameling zijn geconfigureerd.  

 U kunt met behulp van de volgende procedures takenreeksvariabelen maken voor een computer of verzameling.  

#### <a name="to-create-task-sequence-variables-for-a-computer"></a>Takenreeksvariabelen voor een computer maken  

1.  Klik op **Activa en naleving**op de Configuration Manager-console.  

2.  Vouw in de werkruimte **Activa en naleving** de verzameling uit waartoe de computer behoort waaraan u de variabele wilt toevoegen.  

3.  Selecteer de computer en klik op **Eigenschappen**.  

4.  Klik in het dialoogvenster **Eigenschappen** op het tabblad **Variabelen** .  

5.  Voor elke variabele die u wilt maken, klikt u op de **nieuw** pictogram in de **< nieuw\> variabele** in het dialoogvenster. Geef de naam en de waarde van de takenreeksvariabele. Schakel de **deze waarde niet weergeven in de Configuration Manager-console** selectievakje in als u de verzamelingsvariabelen verbergen wilt, zodat ze niet zichtbaar in de Configuration Manager-console.  

6.  Wanneer u alle variabelen aan de computer hebt toegevoegd, klikt u op **OK**.  

#### <a name="to-create-task-sequence-variables-for-a-collection"></a>Takenreeksvariabelen voor een verzameling maken  

1.  Klik op **Activa en naleving**op de Configuration Manager-console.  

2.  Selecteer in de werkruimte **Activa en naleving** de verzameling waaraan u de variabele wilt toevoegen en klik op **Eigenschappen**.  

3.  Klik in het dialoogvenster **Eigenschappen** op het tabblad **Verzamelingsvariabelen** .  

4.  Voor elke variabele die u wilt maken, klikt u op de **nieuw** pictogram in de **< nieuw\> variabele** in het dialoogvenster. Geef de naam en de waarde van de takenreeksvariabele. Schakel de **deze waarde niet weergeven in de Configuration Manager-console** selectievakje in als u de verzamelingsvariabelen verbergen wilt, zodat ze niet zichtbaar in de Configuration Manager-console.  

5.  Geef eventueel de prioriteit voor Configuration Manager moet worden gebruikt wanneer de takenreeksvariabelen worden beoordeeld.  

6.  Wanneer u alle variabelen aan de verzameling hebt toegevoegd, klikt u op **OK**.  

## <a name="add-child-task-sequences-to-a-task-sequence"></a>Takenreeksen onderliggende toevoegen aan een takenreeks
<!--1261338-->
U kunt een nieuwe takenreeksstap waarop een andere takenreeks wordt uitgevoerd vanaf Configuration Manager versie 1710 kunt toevoegen. Deze stap maakt een bovenliggende / onderliggende relatie tussen de takenreeksen. Met behulp van deze stap kunt u meer modulaire takenreeksen maken die u kunt hergebruiken.  

> [!Note]  
> Configuration Manager deze optionele functie standaard niet ingeschakeld. Voordat u deze gebruikt, moet u deze functie inschakelen. Zie voor meer informatie [optionele functies van updates inschakelen](/sccm/core/servers/manage/install-in-console-updates#bkmk_options).<!--505213-->  


Overweeg het volgende wanneer u een takenreeks onderliggende aan een takenreeks toevoegt:

 - De bovenliggende en onderliggende takenreeksen effectief gecombineerd tot een enkele beleidsregel die de client wordt uitgevoerd.
 - De omgeving is algemeen. Bijvoorbeeld, als een variabele is ingesteld door de takenreeks voor de bovenliggende en vervolgens gewijzigd door de onderliggende takenreeks wordt uitgevoerd, blijft deze gewijzigde. Op dezelfde manier als de onderliggende takenreeks maakt u een nieuwe variabele, is beschikbaar voor de overige stappen in de bovenliggende takenreeks wordt uitgevoerd.
 - Statusberichten worden voor een enkele takenreeksbewerking per normaal verzonden.
 - De takenreeksen vermeldingen schrijven naar het bestand smsts.log met nieuwe logboekbestanden vermeldingen die duidelijk wanneer een onderliggende takenreeks wordt gestart.

### <a name="to-add-a-child-task-sequence-to-a-task-sequence"></a>Een takenreeks onderliggende toevoegen aan een takenreeks

1. Klik in de takenreekseditor op **toevoegen**, selecteer **algemene**, en klik op **Takenreeks uitvoeren**.
2. Klik op **Bladeren** naar de onderliggende takenreeks selecteren.  

##  <a name="BKMK_AdditionalActionsTS"></a> Aanvullende acties voor het beheren van takenreeksen  
 U kunt takenreeksen beheren door middel van extra acties wanneer u een takenreeks selecteert.  

#### <a name="to-select-a-task-sequence-to-manage"></a>Een takenreeks selecteren die u wilt beheren  

1.  Klik in de Configuration Manager-console op **Softwarebibliotheek**.  

2.  Vouw in de werkruimte **Softwarebibliotheek** **Besturingssystemen** uit en klik daarna op **Takenreeksen**.  

3.  Selecteer in de lijst **Takenreeks** de takenreeks die u wilt beheren, en selecteer daarna een van de beschikbare opties.  

 Gebruik de volgende tabel voor meer informatie over enkele extra acties om takenreeksen te beheren.  

|Actie|Beschrijving|  
|------------|-----------------|  
|**Kopiëren**|Hiermee wordt een kopie gemaakt van de geselecteerde takenreeks. Deze actie is nuttig om een nieuwe takenreeks die is gebaseerd op een bestaande takenreeks te maken.<br /><br /> Wanneer u een kopie maakt van een takenreeks in een map, wordt de kopie in die map vermeld tot u het takenreeksknooppunt vernieuwt. Na het vernieuwen, wordt de kopie weergegeven in de hoofdmap.|  
|**Uitschakelen**|Hiermee wordt de takenreeks uitgeschakeld, zodat deze niet op computers kan worden uitgevoerd. U kunt een uitgeschakelde takenreeks implementeren, maar computers de takenreeks niet uitgevoerd tenzij u deze inschakelt.|  
|**Inschakelen**|Hiermee wordt de takenreeks ingeschakeld, zodat deze kan worden uitgevoerd. U hoeft een geïmplementeerde takenreeks na inschakeling niet opnieuw te implementeren.|  
|**Voorbereid inhoudsbestand maken**|Hiermee wordt de wizard Voorbereid inhoudsbestand maken gestart om de inhoud van de takenreeks voor te bereiden. Zie voor meer informatie over het maken van een voorbereid inhoudsbestand [inhoud voorbereiden](../../core/servers/deploy/configure/deploy-and-manage-content.md#bkmk_prestage).|  
|**Verplaatsen**|Hiermee wordt de geselecteerde takenreeks verplaatst naar een andere map.|  

## <a name="next-steps"></a>Volgende stappen
[Scenario's voor het implementeren van enterprise-besturingssystemen](scenarios-to-deploy-enterprise-operating-systems.md)
