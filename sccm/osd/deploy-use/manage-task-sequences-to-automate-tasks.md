---
title: Beheren van takenreeksen om taken te automatiseren | Microsoft Docs
description: U kunt maken, bewerken, implementeren, importeren en exporteren van takenreeksen om ze in uw System Center Configuration Manager-omgeving te beheren.
ms.custom: na
ms.date: 03/24/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: configmgr-osd
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: a1f099f1-e9b5-4189-88b3-f53e3b4e4add
caps.latest.revision: "10"
author: Dougeby
ms.author: dougeby
manager: angrobe
ms.openlocfilehash: c9d94ffb61ed7a7fa40a01eedc763a16a8df30cb
ms.sourcegitcommit: 31c670a4bce74fd64a7d46ebf7702f65b80d4147
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 09/13/2017
---
# <a name="manage-task-sequences-to-automate-tasks-in-system-center-configuration-manager"></a>Takenreeksen beheren om taken te automatiseren in System Center Configuration Manager

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*

Gebruik takenreeksen stappen in uw omgeving voor System Center Configuration Manager automatiseren. Met deze stappen kunt u een installatiekopie van een besturingssysteem implementeren, een installatiekopie van een besturingssysteem samenstellen en vastleggen uit een aantal installatiebestanden van het besturingssysteem, en gebruikersstatusinformatie vastleggen en herstellen. Takenreeksen bevinden zich in de Configuration Manager-console op **softwarebibliotheek** > **besturingssystemen** > **Takenreeks**. De **Takenreeks** knooppunt, inclusief de submappen die u maakt, wordt gerepliceerd over de Configuration Manager-hiërarchie. Zie voor informatie over het plannen, [planningsoverwegingen voor het automatiseren van taken](../plan-design/planning-considerations-for-automating-tasks.md).  

 Gebruik de volgende secties om takenreeksen te beheren.

##  <a name="BKMK_CreateTaskSequence"></a> Takenreeksen maken  
 Maak takenreeksen via de wizard Takenreeks maken. Met deze wizard kunt u de volgende typen takenreeksen maken:  

|Takenreekstype|Meer informatie|  
|------------------------|----------------------|  
|[Takenreeks voor het installeren van een besturingssysteem](create-a-task-sequence-to-install-an-operating-system.md)|Met dit type takenreeks maakt u de stappen voor het installeren van een besturingssysteem, alsmede de optie voor het migreren van gebruikersgegevens, het opnemen van software-updates en het installeren van toepassingen.|  
|[De takenreeks om een besturingssysteem te upgraden](create-a-task-sequence-to-upgrade-an-operating-system.md)|Met dit type takenreeks maakt u de stappen voor het installeren van een besturingssysteem, alsmede de optie voor het opnemen van software-updates en het installeren van toepassingen.|  
|[Takenreeks voor het vastleggen van een besturingssysteem](create-a-task-sequence-to-capture-an-operating-system.md)|Met dit type takenreeks maakt u de stappen voor het bouwen en vastleggen van een besturingssysteem van een referentiecomputer. U kunt software-updates opnemen en toepassingen installeren op de referentiecomputer voordat de installatiekopie wordt vastgelegd.|  
|[Takenreeks voor het vastleggen en herstellen van gebruikersstatus](create-a-task-sequence-to-capture-and-restore-user-state.md)|Deze takenreeks bevat de stappen waarmee u een bestaande takenreeks kunt toevoegen om de gegevens van de gebruikersstatus vast te leggen en te herstellen.|  
|[Takenreeks voor het beheren van virtuele harde schijven](use-a-task-sequence-to-manage-virtual-hard-disks.md)|Dit takenreekstype bevat de stappen voor het maken van een VHD, waaronder om een besturingssysteem en toepassingen die u naar System Center Virtual Machine Manager (VMM) vanuit de Configuration Manager-console publiceren kunt te installeren.|  
|[Aangepaste takenreeks](create-a-custom-task-sequence.md)|Dit type takenreeks voegt geen stappen aan de takenreeks toe. U moet de takenreeks bewerken en stappen aan de takenreeks toevoegen nadat deze is gemaakt.|  

## <a name="return-to-previous-page-when-a-task-sequence-fails"></a>Terug naar vorige pagina wanneer een takenreeks mislukt
Vanaf Configuration Manager versie 1702, kunt u terugkeren naar een vorige pagina als u een takenreeks uitvoert en er een fout is. Vóór deze versie moest u de takenreeks opnieuw opstarten als er een fout is opgetreden. U kunt bijvoorbeeld de **vorige** knop in de volgende scenario's:

- Wanneer een computer wordt opgestart in Windows PE, wordt het dialoogvenster taak sequence bootstrap mogelijk weer voordat de takenreeks beschikbaar is. Wanneer u in dit scenario op Volgende klikt, wordt de laatste pagina van de takenreeks weergegeven met een bericht dat er geen takenreeksen beschikbaar zijn. Nu kunt u **vorige** opnieuw zoeken naar beschikbare takenreeksen. U kunt dit proces herhalen totdat de takenreeks beschikbaar is.
- Wanneer u een takenreeks uitvoert, maar de afhankelijke inhoud pakketten nog niet beschikbaar zijn op distributiepunten zijn, mislukt de takenreeks wordt uitgevoerd. U kunt nu de ontbrekende inhoud distribueren (indien deze nog niet is gedistribueerd) of wacht totdat de inhoud beschikbaar zijn op distributiepunten en klik op **vorige** het zoeken van de reeks taak opnieuw naar de inhoud hebben.

##  <a name="BKMK_ModifyTaskSequence"></a> Een takenreeks bewerken  
 U kunt een takenreeks wijzigen door takenreeksstappen toe te voegen of te verwijderen, door takenreeksgroepen toe te voegen of te verwijderen, of door het veranderen van de volgorde van de stappen. Gebruik de volgende procedure om een bestaande takenreeks te wijzigen.  

> [!IMPORTANT]  
>  Als u een takenreeks bewerkt die werd gemaakt met de wizard Takenreeks maken, kan de naam van de stap de bewerking of het type ervan zijn. U kunt bijvoorbeeld zien dat een stap met de naam 'Partitieschijf 0', de actie voor een stap van het type is [schijf formatteren en partitioneren](../understand/task-sequence-steps.md#BKMK_FormatandPartitionDisk). Alle takenreeksstappen worden gedocumenteerd volgens hun type, niet door de naam van de stap die wordt weergegeven in de Editor.  

#### <a name="to-edit-a-task-sequence"></a>Een takenreeks bewerken  

1.  Klik in de Configuration Manager-console op **Softwarebibliotheek**.  

2.  Vouw **Besturingssystemen** uit in de werkruimte **Softwarebibliotheek**en klik op **Takenreeksen**.  

3.  Selecteer in de lijst **Takenreeks** de takenreeks die u wilt bewerken.  

4.  Klik in de groep **Takenreeks** in het tabblad **Start** op **Bewerken**en klik vervolgens op een van de volgende bewerkingen:  

    -   Als u een takenreeksstap wilt toevoegen, klikt u op **Toevoegen**, selecteert u het type stap en klikt u vervolgens op de takenreeksstap die u wilt toevoegen. Als u bijvoorbeeld de stap voor het uitvoeren van de opdrachtregel wilt toevoegen, klikt u op **Toevoegen**, selecteert u **Algemeen**en klikt u vervolgens op **Opdrachtregel uitvoeren**.  

         Zie de tabel die volgt op deze procedure voor een lijst met alle takenreeksstappen en hun type.  

    -   Klik op **Toevoegen**en klik op **Nieuwe groep**om een groep aan de takenreeks toe te voegen. Nadat u een groep toevoegt, kunt u stappen eraan toevoegen.  

    -   Ga als volgt te werk om de volgorde van de stappen en groepen in de takenreeks te wijzigen: selecteer de stap of groep waarvan u de volgorde wilt wijzigen en gebruik de pictogrammen **Item omhoog verplaatsen** of **Item omlaag verplaatsen** . U kunt slechts één stap of groep op hetzelfde moment verplaatsen.  

    -   Selecteer een stap of groep en klik op **Verwijderen**als u een stap of groep wilt verwijderen.  

5.  Klik op **OK** om de wijzigingen op te slaan.  

 Zie voor een lijst van de beschikbare takenreeksstappen [Takenreeksstappen](../understand/task-sequence-steps.md).  

## <a name="configure-software-center-properties"></a>Eigenschappen van Software Center configureren
Gebruik de volgende procedure om de gegevens voor de takenreeks weergegeven in Software Center te configureren. Deze gegevens zijn alleen ter informatie.  
1. Ga in de Configuration Manager-console naar **softwarebibliotheek** > **besturingssystemen** > **Takenreeksen**.
2. Selecteer de takenreeks bewerken en klik op **eigenschappen**.
3. Op de **algemene** tabblad en de volgende instellingen voor Software Center zijn beschikbaar:
  - **Opnieuw opstarten vereist**: Kan de gebruiker weet of opnieuw opstarten vereist tijdens de installatie is.
  - **Grootte (MB) downloaden**: Hiermee geeft u op hoeveel megabytes wordt weergegeven in Software Center voor de takenreeks.  
  - **Geschatte uitvoeringstijd (minuten)**: Hiermee geeft u dat de geschatte tijd in minuten die wordt weergegeven in Software Center voor de takenreeks wordt uitgevoerd.

## <a name="configure-advanced-task-sequence-settings"></a>Geavanceerde taak reeks instellingen configureren
Gebruik de volgende procedure om de gegevens voor de takenreeks weergegeven in Software Center te configureren. Deze gegevens zijn alleen ter informatie.  
1. Ga in de Configuration Manager-console naar **softwarebibliotheek** > **besturingssystemen** > **Takenreeksen**.
2. Selecteer de takenreeks bewerken en klik op **eigenschappen**.
3. Op de **Geavanceerd** tabblad en de volgende instellingen zijn beschikbaar:

    - **Eerst een ander programma uitvoeren**    
    Schakel dit selectievakje in om uit te voeren op een ander programma (in een ander pakket) voordat de takenreeks wordt uitgevoerd. Standaard is dit selectievakje niet geselecteerd. Het programma dat u opgeeft om uit te voeren eerst hoeft niet te worden afzonderlijk aangekondigd.

        > [!IMPORTANT]     
        Deze instelling geldt alleen voor takenreeksen die in het volledige besturingssysteem worden uitgevoerd. Configuration Manager negeert deze instelling als de takenreeks wordt gestart via PXE of opstartmedia.

    - **Pakket**     
        Wanneer u selecteert **rst een ander programma**Typ of blader naar het pakket met het programma dat moet worden uitgevoerd voordat deze takenreeks.

    - **Programma**     
    Wanneer u selecteert **rst een ander programma**, selecteer het programma dat moet worden uitgevoerd vóór deze takenreeks van de **programma** vervolgkeuzelijst.

        > [!NOTE]    
        > Als het geselecteerde programma niet uitgevoerd op een client, wordt de takenreeks niet uitgevoerd. Als het geselecteerde programma voltooid wordt, wordt deze niet uitgevoerd, zelfs als de takenreeks opnieuw op dezelfde client wordt uitgevoerd.
 
    - **Deze takenreeks uitschakelen op computers waarop deze is geïmplementeerd**    
    Als u deze optie selecteert, worden alle implementaties die deze takenreeks bevatten tijdelijk uitgeschakeld. De takenreeks wordt verwijderd uit de lijst met beschikbare advertenties uitgevoerd en wordt niet uitgevoerd totdat deze is opnieuw worden ingeschakeld. Deze optie is standaard uitgeschakeld.

    - **Maximale toegestane uitvoeringstijd**    
    Hiermee geeft u de maximale tijd (in minuten) die wordt verwacht dat de takenreeks wordt uitgevoerd op de doelcomputer. U moet een geheel getal gelijk is aan of groter zijn dan nul. Deze waarde is standaard ingesteld op 120 minuten.

        > [!IMPORTANT]    
        > Als u onderhoudsvensters voor de verzameling waarop deze takenreeks wordt uitgevoerd gebruikt, een conflict optreden als de **maximale toegestane uitvoeringstijd** langer is dan het geplande onderhoudsvenster. Als de maximum uitvoeringstijd is ingesteld op **0**, de takenreeks wordt gestart tijdens het onderhoudsvenster en verder worden uitgevoerd tot het voltooid of mislukt is nadat het onderhoudsvenster is gesloten. Als gevolg hiervan takenreeksen met een maximum uitvoeringstijd is ingesteld op **0** voorbij het einde van de onderhoudsvensters mogelijk uitgevoerd. Als u de maximale uitvoeringstijd voor een bepaalde periode is ingesteld (dat wil zeggen, niet is ingesteld op **0**) die langer is dan de lengte van welk beschikbaar onderhoudsvenster en vervolgens de takenreeks wordt niet uitgevoerd. Zie voor meer informatie [het gebruik van onderhoudsvensters](/sccm/core/clients/manage/collections/use-maintenance-windows).
 
        Als de waarde is ingesteld als **0**, Configuration Manager beoordeelt de maximale toegestane uitvoeringstijd als **12** uur (720 minuten) voor de voortgang controleren. Echter, de takenreeks wordt gestart zolang de duur van het aftellen niet langer zijn dan de waarde van onderhoud-venster.

    > [!NOTE]    
    > Als de maximum uitvoeringstijd is bereikt, stopt Configuration Manager de takenreeks als deze is ingesteld op uitvoeren met beheerdersrechten en de gebruikers toestaan om te communiceren met deze instelling wordt niet is ingeschakeld. Als de takenreeks zelf niet is gestopt, stopt de bewaking van de takenreeks na de maximaal toegestane uitvoeringstijd Configuration Manager is bereikt. 

    - **Een opstartinstallatiekopie gebruiken**   
        Schakel deze optie in de geselecteerde opstartinstallatiekopie gebruiken wanneer de takenreeks wordt uitgevoerd. 

        Klik op **Bladeren** naar een andere opstartinstallatiekopie selecteren. Schakel deze optie voor het gebruik van de geselecteerde opstartinstallatiekopie uitschakelen wanneer de takenreeks wordt uitgevoerd.

    - **Deze takenreeks kan worden uitgevoerd op elk platform**     
        Als u deze optie selecteert, wordt Configuration Manager het platformtype van de doelcomputer niet gecontroleerd wanneer de takenreeks wordt geïmplementeerd. Deze optie is standaard geselecteerd.

    - **Deze takenreeks kan alleen worden uitgevoerd op de gespecificeerde clientplatforms**    
        Deze optie geeft u de processors, besturingssystemen en servicepacks die deze takenreeks kan worden uitgevoerd. Wanneer u deze optie selecteert, moet u ten minste één platform ook geselecteerd in de lijst. Er is geen platforms zijn standaard ingeschakeld. Configuration Manager gebruikt deze informatie wanneer is evalueert welke doelcomputers in een verzameling ontvangen de geïmplementeerde takenreeks.

        > [!NOTE]    
        > Wanneer een takenreeks wordt uitgevoerd vanaf opstartmedia of door PXE-opstartbewerking, deze optie wordt genegeerd en de takenreeks wordt uitgevoerd alsof de optie **dit programma kan worden uitgevoerd op elk platform** is geselecteerd.

## <a name="configure-high-impact-task-sequence-settings"></a>Hoge impact taak reeks instellingen configureren
Vanaf Configuration Manager versie 1702, kunt u een takenreeks als hoge impact en aanpassen van de berichten die gebruikers ontvangen wanneer ze de takenreeks worden uitgevoerd.

### <a name="set-a-task-sequence-as-a-high-impact-task-sequence"></a>Een takenreeks ingesteld als een takenreeks met hoge impact
Gebruik de volgende procedure in te stellen van een takenreeks als hoge impact.
> [!NOTE]    
> Elke takenreeks die voldoet aan bepaalde voorwaarden wordt automatisch gedefinieerd als hoge impact. Zie voor meer informatie [beheren van implementaties met een hoog risico](http://docs.microsoft.com/sccm/protect/understand/settings-to-manage-high-risk-deployments).

1. Ga in de Configuration Manager-console naar **softwarebibliotheek** > **besturingssystemen** > **Takenreeksen**.
2. Selecteer de takenreeks bewerken en klik op **eigenschappen**.
3. Op de **gebruikersmelding** tabblad **dit is een grote impact takenreeks**.

### <a name="create-a-custom-notification-for-high-risk-deployments"></a>Een aangepaste melding voor implementaties met een hoog risico maken
Gebruik de volgende procedure voor het maken van een aangepaste melding voor implementaties met hoge impact.
1. Ga in de Configuration Manager-console naar **softwarebibliotheek** > **besturingssystemen** > **Takenreeksen**.
2. Selecteer de takenreeks bewerken en klik op **eigenschappen**.
3. Op de **gebruikersmelding** tabblad **u aangepaste tekst**.
>  [!NOTE]    
>  U kunt alleen de berichttekst gebruiker instellen wanneer de **dit is een grote impact takenreeks** is geselecteerd.

4. Configureer de volgende instellingen (maximaal 255 tekens bestaan voor elk tekstvak):

  **Gebruiker melding kopregel**: Hiermee geeft u de blauwe tekst die wordt weergegeven op de melding voor gebruikers van Software Center. Bijvoorbeeld, in de gebruikersmelding standaard bevat in deze sectie ongeveer 'Bevestigen voor het bijwerken van het besturingssysteem op deze computer'.

  **Gebruiker melding berichttekst**: Er zijn drie tekstvakken waarmee de hoofdtekst van de aangepaste melding. Alle tekstvakken vereisen dat u tekst toevoegen.
  - 1e tekstvak: Hiermee geeft u de hoofdtekst van tekst, meestal met instructies voor de gebruiker. In de gebruikersmelding standaard bevat in deze sectie bijvoorbeeld iets zoals 'besturingssysteem upgraden tijd kost en de computer enkele keren opnieuw opstarten.'
  - tekstvak voor 2e: Hiermee geeft u de vetgedrukte onder de hoofdtekst. In de gebruikersmelding standaard bevat in deze sectie bijvoorbeeld iets zoals 'deze in-place upgrade wordt het nieuwe besturingssysteem geïnstalleerd en worden uw apps, gegevens en instellingen automatisch gemigreerd.'
  - tekstvak voor 3e: Hiermee geeft u de laatste regel van de tekst onder de vetgedrukte. Bijvoorbeeld, in de gebruikersmelding standaard in deze sectie bevat dat lijkt op ' Klik op installeren om te beginnen. Klik anders op Annuleren."   
    
Stel dat u de volgende aangepaste melding in de eigenschappen configureren.

![Aangepaste melding voor een takenreeks](..\media\user-notification.png)

Het volgende bericht wordt weergegeven wanneer de eindgebruiker opent de installatie van Software Center.

![Aangepaste melding voor een takenreeks](..\media\user-notification-enduser.png)


##  <a name="BKMK_DistributeTS"></a> Inhoud distribueren waarnaar wordt verwezen door een specifieke takenreeks  
 Voordat clients een takenreeks uitvoeren die naar inhoud verwijst, moet u deze inhoud distribueren naar distributiepunten. U kunt op elk gewenst moment de takenreeks selecteren en de bijbehorende inhoud distribueren om een nieuwe lijst met referentiepakketten voor distributie te bouwen. Als u wijzigingen aanbrengt in de takenreeks met bijgewerkte inhoud, moet u de inhoud herverdelen voordat deze beschikbaar is voor clients. Gebruik de volgende procedure om de inhoud te distribueren waarnaar een takenreeks verwijst.  

#### <a name="to-distribute-referenced-content-to-distribution-points"></a>Inhoud waarnaar wordt verwezen, distribueren naar distributiepunten  

1.  Klik in de Configuration Manager-console op **Softwarebibliotheek**.  

2.  Vouw **Besturingssystemen** uit in de werkruimte **Softwarebibliotheek**en klik op **Takenreeksen**.  

3.  Selecteer in de lijst **Takenreeks** de takenreeks die u wilt distribueren.  

4.  Klik op het tabblad **Start** in de groep **Implementatie** op **Inhoud distribueren** om de wizard Inhoud distribueren te starten.  

5.  Controleer op de pagina **Algemeen** of de juiste takenreeks is geselecteerd voor distributie en klik vervolgens op **Volgende**.  

6.  Controleer de te distribueren inhoud op de pagina **Inhoud** , zoals een installatiekopie waarnaar de takenreeks verwijst, en klik vervolgens op **Volgende**.  

7.  Geef op de pagina **Doel van inhoud** de verzamelingen, het distributiepunt of de doelpuntgroep op waarnaar u de takenreeksinhoud wilt distribueren en klik vervolgens op **Volgende**.  

    > [!IMPORTANT]  
    >  Als de takenreeks die u hebt geselecteerd, verwijst naar inhoud die al is gedistribueerd naar een specifiek distributiepunt, wordt dat distributiepunt niet vermeld in de wizard.  

8.  Voltooi de wizard.  

 U kunt de inhoud voorbereiden waarnaar in de takenreeks wordt verwezen. Configuration Manager maakt een gecomprimeerd, voorbereid inhoudsbestand dat de bestanden, gekoppelde afhankelijkheden, en gekoppelde metagegevens bevat voor de inhoud die u selecteert. U kunt vervolgens de inhoud handmatig importeren via een siteserver, secundaire site of distributiepunt. Zie voor meer informatie over het voorbereiden van inhoudsbestanden [inhoud voorbereiden](../../core/servers/deploy/configure/deploy-and-manage-content.md#bkmk_prestage).  

##  <a name="BKMK_DeployTS"></a> Een takenreeks implementeren  
 Gebruik de volgende procedure om een takenreeks te implementeren voor de computers in een verzameling.  

> [!WARNING]  
>  U kunt het gedrag voor de implementatie van takenreeksen met een hoge risico beheren. Een implementatie met een hoog risico is een implementatie die automatisch wordt geïnstalleerd en de potentie heeft om ongewenste resultaten te veroorzaken. Een takenreeks met het doel **Vereist** en die een besturingssysteem implementeert, wordt beschouwd als een implementatie met een hoog risico. Zie voor meer informatie [instellingen voor het beheren van implementaties met een hoog risico](../../protect/understand/settings-to-manage-high-risk-deployments.md).  

> [!NOTE]  
>  De statusberichten voor de takenreeksimplementatie worden wel weergegeven in het venster Bericht op een primaire site, maar niet op een centrale beheersite.  

#### <a name="to-deploy-a-task-sequence"></a>Een takenreeks implementeren  

1.  Klik in de Configuration Manager-console op **Softwarebibliotheek**.  

2.  Vouw **Besturingssystemen** uit in de werkruimte **Softwarebibliotheek**en klik op **Takenreeksen**.  

3.  Selecteer in de lijst **Takenreeks** de takenreeks die u wilt implementeren.  

4.  Klik op het tabblad **Start** in de groep **Implementatie** op **Implementeren**.  

    > [!NOTE]  
    >  Als **Implementeren** niet beschikbaar is, beschikt de takenreeks over een ongeldige verwijzing.  Corrigeer de verwijzing en probeer vervolgens opnieuw of u de takenreeks kunt implementeren.  

5.  Geef op de pagina **Algemeen** de volgende informatie op en klik op **Volgende**.  

    -   **Takenreeks**: Geef de takenreeks die u wilt implementeren. In dit vak wordt standaard de takenreeks weergegeven die u hebt geselecteerd.  

    -   **Verzameling**: Geef de verzameling die de computers bevat waarop de takenreeks wordt uitgevoerd.  

         Implementeer geen takenreeksen die besturingssystemen installeren naar ongeschikte verzamelingen, zoals de verzameling **Alle systemen** . Zorg ervoor dat de verzameling die u selecteert alleen de computers bevat waarop u de takenreeks wilt uitvoeren.  

        > [!NOTE]  
        >  Wanneer u een implementatie met hoog risico, zoals een besturingssysteem implementeert de **verzameling selecteren** venster geeft alleen de aangepaste verzamelingen die voldoen aan de implementatie van de verificatie-instellingen die zijn geconfigureerd in de site eigenschappen. Implementaties met een hoog risico zijn altijd beperkt tot aangepaste verzamelingen, verzamelingen die u zelf maakt en de ingebouwde verzameling **Onbekende computers** . Wanneer u een implementatie met een hoog risico maakt, kunt u geen ingebouwde verzameling selecteren, zoals **Alle systemen**. Schakel het selectievakje **lid zamelingen verbergen groter is dan de minimale configuratiegrootte** voor een overzicht van alle aangepaste verzamelingen die minder clients dan het geconfigureerde maximum bevatten. Zie voor meer informatie [instellingen voor het beheren van implementaties met een hoog risico](../../protect/understand/settings-to-manage-high-risk-deployments.md).  
        >   
        >  De instellingen voor het verifiëren van de implementatie zijn gebaseerd op het huidige lidmaatschap van de verzameling. Nadat u een takenreeks hebt geïmplementeerd, wordt het lidmaatschap van de verzameling niet opnieuw geëvalueerd voor de instellingen van de implementatie met een hoog risico.  
        >   
        >  Bijvoorbeeld, Stel dat u **standaardgrootte** en 100 en de **maximumgrootte** tot en met 1000. Wanneer u een implementatie met een hoog risico maakt, worden in het venster **Verzameling selecteren** alleen verzamelingen weergegeven die minder dan 100 clients bevatten. Als u het selectievakje de **lid zamelingen verbergen groter is dan de minimale configuratiegrootte** uitschakelt, het venster verzamelingen weergegeven die minder dan 1000 clients bevatten.  
        >   
        >  Wanneer u een verzameling met een siterol selecteert, geldt het volgende:  
        >   
        >  -   Als de verzameling een sitesysteemserver bevat en u in de instellingen voor het verifiëren van de implementatie opgeeft dat verzamelingen met sitesysteemservers moeten worden geblokkeerd, wordt er een fout weergegeven en kunt u niet doorgaan.  
        > -   Als de verzameling een sitesysteemserver bevat en u in de instellingen voor het verifiëren van de implementatie opgeeft dat u moet worden gewaarschuwd als verzamelingen sitesysteemservers bevatten, de verzameling de standaardgrootte overschrijdt of als de verzameling een server bevat, wordt er in de wizard Software implementeren een waarschuwing voor een hoog risico weergegeven. U moet akkoord gaan met het maken van een implementatie met een hoog risico en er wordt een controlestatusbericht gegenereerd.  

    -   **Commentaren (optioneel)**: Geef aanvullende informatie die deze implementatie van de takenreeks beschrijft.  

6.  Geef op de pagina **Implementatie-instellingen** de volgende informatie op en klik vervolgens op **Volgende**.  

    -   **Doel**: Kies een van de volgende opties in de vervolgkeuzelijst:  

        -   **Beschikbare**: Als de takenreeks wordt geïmplementeerd voor een gebruiker, wordt de gebruiker wordt de gepubliceerde takenreeks weergegeven in de Application Catalog en kan deze op aanvraag opvragen. Als de takenreeks wordt geïmplementeerd voor een apparaat, wordt deze weergegeven in Software Center en kan de gebruiker deze op aanvraag installeren.  

        -   **Vereist**: De takenreeks wordt automatisch geïmplementeerd volgens de geconfigureerde planning. Een gebruiker kan de implementatiestatus van de takenreeks (als deze niet is verborgen) bijhouden en de takenreeks installeren via Software Center voordat de deadline wordt bereikt.  

    -   **Automatisch implementeren volgens schema of een gebruiker is aangemeld of niet**: Deze optie is niet beschikbaar wanneer u een takenreeks implementeert.  

    -   **Verzenden van ontwaakpakketten**: Als het implementatiedoel is ingesteld op **vereist** en deze optie is geselecteerd, wordt een ontwaakpakket verzonden naar computers voordat de implementatie wordt geïnstalleerd om de computer uit de slaapstand deadline van de installatie te halen. Voordat u deze optie kunt gebruiken, moeten computers en netwerken zijn geconfigureerd voor Wake On LAN.  

    -   **Laat clients toe op een internetverbinding naar gebruik om inhoud te downloaden na de installatiedeadline, waarvoor extra kosten in rekening kan worden**: Wanneer u een takenreeks die een toepassing installeert, maar implementeert geen besturingssysteem hebt, kunt u opgeven of wilt toestaan dat clients inhoud downloaden na een installatiedeadline wanneer ze internetverbindingen. Internetproviders brengen soms de hoeveelheid gegevens die u verzendt en ontvangt in rekening wanneer u gebruikmaakt van een internetverbinding naar gebruik.  

        > [!NOTE]  
        >  Hoewel het gebruik van internetverbindingen met een datalimiet mogelijk kan worden toegepast voor takenreeksen die geen besturingssystemen implementeren, wordt dit niet ondersteund.  

    -   **Goedkeuring door beheerder vereisen als gebruikers deze toepassing aanvragen**: Deze optie is niet beschikbaar wanneer u een takenreeks implementeert.  

    -   **Toegankelijk maken voor de volgende**: Opgeven of de takenreeks beschikbaar is voor Configuration Manager-clients, media of PXE.  

        > [!IMPORTANT]  
        >  Gebruik de instelling **Alleen media en PXE (verborgen)** voor geautomatiseerde implementaties van takenreeksen. Selecteer **Implementatie van besturingssysteem zonder toezicht toestaan** en stel de variabele SMSTSPreferredAdvertID in als onderdeel van de media als u de computer automatisch naar de implementatie wilt opstarten zonder tussenkomst van de gebruiker. Zie voor meer informatie over takenreeksvariabelen [ingebouwde variabelen voor takenreeksen](../understand/task-sequence-built-in-variables.md)  

7.  Geef op de pagina **Planning** de volgende informatie op en klik vervolgens op **Volgende**.  

    > [!IMPORTANT]  
    >  Wanneer een Windows PE-client wordt gestart vanaf PXE- of opstartmedium, evalueert de client geen implementatieschema's (starten, verlopen of deadlinetijden). Alleen schema's configureren in implementaties van clients die vanuit het volledige Windows-besturingssysteem starten. Overweeg het gebruik van andere methoden, zoals onderhoudvensters, waarmee reeksen actieve taken worden beheerd die geïmplementeerd zijn op clients die starten vanaf Windows PE.  

    -   **Plannen wanneer deze implementatie beschikbaar zal worden**: Geef de datum en tijd waarop de takenreeks beschikbaar is voor uitvoeren op de doelcomputer. Wanneer u het selectievakje **UTC** inschakelt, zorgt deze instelling ervoor dat de takenreeks voor meerdere doelcomputers tegelijk beschikbaar is in plaats van op verschillende tijdstippen, op basis van de lokale tijd op de doelcomputers.  

         Als de begintijdstip eerder is dan het vereiste tijdstip, downloadt de client de takenreeks op het begintijdstip dat u opgeeft.  

    -   **Plannen wanneer deze implementatie zal verlopen**: Geef de datum en tijd waarop de takenreeks verloopt op de doelcomputer. Wanneer u het selectievakje **UTC** inschakelt, zorgt deze instelling ervoor dat de takenreeks op meerdere doelcomputers tegelijk verloopt is in plaats van op verschillende tijdstippen, op basis van de lokale tijd op de doelcomputers.  

    -   **Toewijzingsplanning**: Geef op wanneer de vereiste takenreeks wordt uitgevoerd op de doelcomputer. U kunt meerdere planningen toevoegen.  

         U kunt de datum en het tijdstip opgeven waarop de planning begint, of taken wekelijks, maandelijks of op basis van een aangepast interval moeten worden uitgevoerd en of de takenreeks moet worden uitgevoerd na een gebeurtenis, zoals het aanmelden of afmelden van de computer.  

        > [!NOTE]  
        >  Als u plant een begintijd voor een vereiste takenreeks dat eerder is dan de datum en tijd waarop de takenreeks beschikbaar is, downloadt de Configuration Manager-client de takenreeks op het geplande begintijdstip, ondanks dat de takenreeks wordt uitgevoerd op een eerder tijdstip beschikbaar is.  

    -   **Gedrag voor opnieuw uitvoeren**: Geef op wanneer de takenreeks opnieuw wordt uitgevoerd. U kunt een van de volgende opties opgeven.  

        -   **Geïmplementeerd programma nooit opnieuw uitvoeren**: De takenreeks wordt niet opnieuw uitgevoerd op de client als de takenreeks al eerder is uitgevoerd op de client. De takenreeks wordt niet opnieuw uitgevoerd, zelfs als deze is mislukt of als de takenreeksbestanden zijn gewijzigd.  

        -   **Programma altijd opnieuw uitvoeren**: De takenreeks wordt altijd opnieuw uitgevoerd op de client wanneer de implementatie is gepland, zelfs als de takenreeks al eerder met succes uitgevoerd. Deze instelling is bijzonder nuttig wanneer u herhaalde implementaties gebruikt waarbij de takenreeks regelmatig wordt bijgewerkt.  

            > [!IMPORTANT]  
            >  Hoewel deze optie standaard is ingesteld, is deze niet van invloed, totdat u een vereiste implementatie toewijst. Beschikbare implementaties kunnen door een gebruiker altijd opnieuw worden uitgevoerd.  

        -   **Opnieuw uitvoeren als de vorige poging is mislukt**: De takenreeks wordt opnieuw uitgevoerd wanneer de implementatie alleen is gepland als de takenreeks uitvoeren eerder is mislukt. Deze taak is bijzonder nuttig voor vereiste implementaties, zodat automatisch opnieuw wordt geprobeerd om deze uit te voeren op basis van de toegewezen planning als de laatste poging tot uitvoeren is mislukt.  

        -   Opnieuw uitvoeren als de vorige poging is gelukt: De takenreeks wordt alleen opnieuw uitgevoerd als deze eerder is uitgevoerd op de client. Deze instelling is bijzonder nuttig wanneer u herhaalde implementaties gebruikt waarbij de takenreeks regelmatig wordt bijgewerkt en waarbij het voor elke update vereist is dat de vorige update is geïnstalleerd.  

        > [!NOTE]  
        >  Omdat een gebruiker een beschikbare takenreeksimplementatie opnieuw kan uitvoeren, moet u; voordat u een beschikbare takenreeks implementeert in een productomgeving, ervoor zorgen dat u zorgvuldig beoordeelt wat er gebeurt als een gebruiker de takenreeks meerdere keren uitvoert.  

8.  Geef op de pagina **Gebruikerservaring** de volgende informatie op en klik op **Volgende**.  

    -   **Toestaan dat gebruikers het programma onafhankelijk van toewijzingen uit te voeren**: Geef op of de gebruiker kan een vereiste takenreeks onafhankelijk van de implementatietoewijzingen uitvoeren.  

    -   **Voortgang van Takenreeks weergeven**: Geef aan of Configuration Manager-client de voortgang van de takenreeks weergeeft.  

    -   **Software-installatie**: Geef op of de gebruiker is toegestaan voor het installeren van software buiten een geconfigureerd onderhoudsvenster na de geplande tijd.  

    -   **Systeem opnieuw opstarten (indien nodig om de installatie te voltooien)**: Geef op of de gebruiker mag de computer opnieuw opstarten na een software-installatie buiten een geconfigureerd onderhoudsvenster na de toegewezen periode.  

    -   **Takenreeks mag worden uitgevoerd voor de client op Internet**: Geef op of de takenreeks mag worden uitgevoerd op een client met Internet die door Configuration Manager is gedetecteerd op Internet. Bewerkingen waarbij er software wordt geïnstalleerd, zoals een besturingssysteem, worden bij het gebruik van deze instelling niet ondersteund. Gebruik deze optie alleen voor algemene op scripts gebaseerde takenreeksen die bewerkingen uitvoeren onder het standaardbesturingssysteem.  

9. Geef op de pagina **Waarschuwingen** de waarschuwingsinstelling die u wilt voor de implementatie van deze takenreeks en klik vervolgens op **Volgende**.  

10. Geef op de pagina **Distributiepunten** de volgende informatie op en klik vervolgens op **Volgende**.  

    -   **Implementatieopties**: Geef een van de volgende opties:  

        > [!NOTE]  
        >  Wanneer u multicast gebruikt voor het implementeren van een besturingssysteem moet de inhoud, voordat deze nodig is of voor het uitvoeren van de takenreeks, worden gedownload naar de doelcomputers.  

        -   Geef op dat clients inhoud wanneer dat voor de takenreeks nodig is, vanaf het distributiepunt downloaden naar de doelcomputer.  

        -   Geef op dat de clients alle inhoud vanaf het distributiepunt naar de doelcomputer downloaden voordat de takenreeks wordt uitgevoerd. Deze optie wordt niet weergegeven als u hebt opgegeven dat de takenreeks beschikbaar is voor PXE- en opstartmedia-implementaties (zie de pagina **Implementatie-instellingen** ).  

        -   Geef op dat clients de inhoud uitvoeren vanaf het distributiepunt. Deze optie is alleen beschikbaar wanneer alle pakketten die aan de takenreeks zijn gekoppeld, zijn ingeschakeld voor het gebruik van een pakketshare op het distributiepunt. Zie het tabblad **Gegevenstoegang** in de **eigenschappen** van de afzonderlijke pakketten voor informatie over het inschakelen van inhoud voor het gebruik van een pakketshare.  

    -   **Een extern distributiepunt gebruiken wanneer geen lokaal distributiepunt beschikbaar is,**: Specificeer of clients distributiepunten die zich op trage en onbetrouwbare netwerken voor het downloaden van de inhoud die is door de takenreeks vereist kunnen gebruiken.  

11. Voltooi de wizard.  

##  <a name="BKMK_ExportImport"></a> Takenreeksen exporteren en importeren  
 U kunt takenreeksen exporteren en importeren met en zonder hun bijbehorende objecten, zoals een installatiekopie van een besturingssysteem, een opstartinstallatiekopie, een clientagentpakket, een stuurprogrammapakket en toepassingen met afhankelijkheden.  

 Houd rekening met het volgende als u takenreeksen exporteert en importeert.  

-   Wachtwoorden die in de takenreeks zijn opgeslagen, worden niet geëxporteerd. Als u een takenreeks exporteert en importeert die wachtwoorden bevat, moet u de geïmporteerde takenreeks bewerken en moet u opnieuw wachtwoorden opgeven. Zorg ervoor dat u wachtwoorden opgeeft voor [lid worden van domein of werkgroep](../understand/task-sequence-steps.md#BKMK_JoinDomainorWorkgroup), [netwerkmap verbinding](../understand/task-sequence-steps.md#BKMK_ConnectToNetworkFolder), en [opdrachtregel uitvoeren](../understand/task-sequence-steps.md#BKMK_RunCommandLine) acties.  

- Tijdens het exporteren van een takenreeks met de **Dynanmic variabelen instellen** stap geen waarden worden geëxporteerd voor variabelen die zijn geconfigureerd met de **geheime waarde** instelling. Nadat u de takenreeks hebt geïmporteerd, moet u de waarden voor deze variabelen opnieuw invoeren.

-   Het is een aanbevolen procedure om takenreeksen via de centrale beheersite te importeren wanneer u meerdere primaire sites hebt.  

 Gebruik de volgende procedures voor het exporteren en importeren van een takenreeks.  

#### <a name="to-export-task-sequences"></a>Takenreeksen exporteren  

1.  Klik in de Configuration Manager-console op **Softwarebibliotheek**.  

2.  Vouw **Besturingssystemen** uit in de werkruimte **Softwarebibliotheek**en klik op **Takenreeksen**.  

3.  Selecteer in de lijst **Takenreeks** de takenreeks die u wilt exporteren. Als u meer dan één takenreeks selecteert, worden de takenreeksen opgeslagen in één exportbestand.  

4.  Klik op tabblad **Start** in de groep **Takenreeks** op **Exporteren** om de wizard Takenreeks exporteren te starten.  

5.  Stel op de pagina **Algemeen** de volgende instellingen in en klik op **Volgende**.  

    -   Geef in het vak **Bestand** de locatie en de naam van het exportbestand op. Als u de bestandsnaam rechtstreeks invoert, moet u de extensie (.zip) opnemen in de bestandsnaam. Als u naar het exportbestand bladert, wordt de extensie door de wizard automatisch aan deze bestandsnaam toegevoegd.  

    -   Schakel het selectievakje **Alle afhankelijkheden van takenreeksen exporteren** uit als u de afhankelijkheden van de takenreeks niet wilt exporteren. De wizard scant standaard op alle bijbehorende objecten en exporteert deze met de takenreeks. Dit geldt ook voor eventuele afhankelijkheden voor toepassingen.  

    -   Schakel het selectievakje **Alle inhoud voor de geselecteerde takenreeksen en afhankelijkheden exporteren** uit als u de inhoud uit het bronpakket niet naar de exportlocatie wilt kopiëren. Als dit selectievakje is ingeschakeld, gebruikt de wizard Takenreeks importeren het importpad als de nieuwe pakketbronlocatie.  

    -   Voeg in het vak **Opmerkingen beheerder** een beschrijving toe van de takenreeksen die moeten worden geëxporteerd.  

6.  Voltooi de wizard.  

 De wizard maakt de volgende uitvoerbestanden:  

-   Als u geen inhoud exporteert: een ZIP-bestand.  

-   Als u inhoud exporteert: een ZIP-bestand en een map met de naam *export*_files, waarbij *export* de naam is van het ZIP-bestand dat de geëxporteerde inhoud bevat.  

 Zorg ervoor dat, als u inhoud opneemt wanneer u een takenreeks exporteert, u het ZIP-bestand en de map *export*_files kopieert; anders kunt u niet importeren.  

#### <a name="to-import-task-sequences"></a>Takenreeksen importeren  

1.  Klik in de Configuration Manager-console op **Softwarebibliotheek**.  

2.  Vouw **Besturingssystemen** uit in de werkruimte **Softwarebibliotheek**en klik op **Takenreeksen**.  

3.  Klik op het tabblad **Start** in de groep **Maken** op **Takenreeks importeren** om de wizard Takenreeks importeren te starten.  

4.  Specificeer op de pagina **Algemeen** het geëxporteerde ZIP-bestand en klik daarna op **Volgende**.  

5.  Selecteer op de pagina **Bestandsinhoud** de actie die u nodig hebt voor elk object dat u importeert. Deze pagina bevat alle objecten die Configuration Manager worden geïmporteerd.  

    -   Selecteer **Nieuw**, als het object nog nooit is geïmporteerd.  

    -   Selecteer een van de volgende acties, als het object al eerder is geïmporteerd:  

        -   **Dubbele negeren** (standaard): Deze actie wordt het object niet geïmporteerd. In plaats daarvan koppelt de wizard het bestaande object aan de takenreeks.  

        -   **Overschrijven**: Deze actie wordt het bestaande object overschreven door het geïmporteerde object. Voor toepassingen kunt u een revisie toevoegen om de bestaande toepassing bij te werken of een nieuwe toepassing te maken.  

6.  Voltooi de wizard.  

 Wanneer u de takenreeks hebt geïmporteerd, bewerkt u de takenreeks zo, dat deze wachtwoorden opgeeft die geldig waren in de oorspronkelijke takenreeks. Uit veiligheidsoverwegingen zijn wachtwoorden niet geëxporteerd.  

##  <a name="BKMK_CreateTSVariables"></a> Takenreeksvariabelen voor computers en verzamelingen maken  
U kunt takenreeksvariabelen definiëren voor computers en verzamelingen. Naar variabelen die voor een computer zijn gedefinieerd, wordt verwezen als computertakenreeksvariabelen. Naar variabelen die voor een verzameling zijn gedefinieerd, wordt verwezen als verzamelingtakenreeksvariabelen. Bij een conflict gaan computervariabelen boven verzamelingsvariabelen. Dit wil zeggen dat takenreeksvariabelen die aan een specifieke computer zijn toegewezen automatisch een hogere prioriteit hebben dan variabelen die aan de verzameling zijn toegewezen waartoe de computer behoort.  

Als bijvoorbeeld verzameling ABC een variabele krijgt toegewezen en computer XYZ, die lid is van verzameling ABC, een variabele met dezelfde naam krijgt toegewezen, heeft de aan computer XYZ toegewezen variabele een hogere prioriteit dan de aan verzameling ABC toegewezen variabele.  

U kunt computer- en per-verzameling verzamelingsvariabelen verbergen, zodat ze niet zichtbaar in de Configuration Manager-console. Als u deze variabelen niet meer verborgen wilt houden, moet u deze verwijderen en opnieuw definiëren, zonder de optie te selecteren om deze te verbergen. Wanneer u de optie gebruikt **deze waarde niet weergeven in de Configuration Manager-console**, de waarde van de variabele niet wordt weergegeven in de console, maar kan nog steeds worden gebruikt door de takenreeks wanneer deze wordt uitgevoerd.  

> [!WARNING]    
> De **deze waarde niet weergeven in de Configuration Manager-console** instelling geldt voor de Configuration Manager-console, maar de waarden voor de variabelen nog steeds worden weergegeven in het logboekbestand van taak sequence (SMSTS. LOGBOEK). 

U kunt per computer variabelen op een primaire site of op een centrale beheersite beheren. Configuration Manager biedt geen ondersteuning voor meer dan 1000 toegewezen variabelen voor een computer.  

> [!IMPORTANT]  
>  Wanneer u verzamelingsvariabelen gebruikt voor takenreeksen, dient u het volgende te bedenken:  
>   
> - Omdat wijzigingen in verzamelingen altijd door de gehele hiërarchie heen worden gerepliceerd, zijn door u aangebrachte wijzigingen in verzamelingvariabelen niet alleen van toepassing op leden van de huidige site, maar op alle leden van de verzameling door de gehele hiërarchie heen.  
> - Wanneer u een verzameling verwijdert, wordt door deze actie tevens de takenreeksvariabelen verwijderd die voor de verzameling zijn geconfigureerd.  

 U kunt met behulp van de volgende procedures takenreeksvariabelen maken voor een computer of verzameling.  

#### <a name="to-create-task-sequence-variables-for-a-computer"></a>Takenreeksvariabelen voor een computer maken  

1.  Klik op **Activa en naleving**op de Configuration Manager-console.  

2.  Vouw in de werkruimte **Activa en naleving** de verzameling uit waartoe de computer behoort waaraan u de variabele wilt toevoegen.  

3.  Selecteer de computer en klik op **Eigenschappen**.  

4.  Klik in het dialoogvenster **Eigenschappen** op het tabblad **Variabelen** .  

5.  Voor elke variabele die u wilt maken, klikt u op de **nieuw** pictogram in de **< nieuw\> variabele** dialoogvenster en geef de naam en de waarde van de takenreeksvariabele. Schakel de **deze waarde niet weergeven in de Configuration Manager-console** selectievakje in als u de verzamelingsvariabelen verbergen wilt, zodat ze niet zichtbaar in de Configuration Manager-console.  

6.  Wanneer u alle variabelen aan de computer hebt toegevoegd, klikt u op **OK**.  

#### <a name="to-create-task-sequence-variables-for-a-collection"></a>Takenreeksvariabelen voor een verzameling maken  

1.  Klik op **Activa en naleving**op de Configuration Manager-console.  

2.  Selecteer in de werkruimte **Activa en naleving** de verzameling waaraan u de variabele wilt toevoegen en klik op **Eigenschappen**.  

3.  Klik in het dialoogvenster **Eigenschappen** op het tabblad **Verzamelingsvariabelen** .  

4.  Voor elke variabele die u wilt maken, klikt u op de **nieuw** pictogram In de **< nieuw\> variabele** dialoogvenster en geef de naam en de waarde van de takenreeksvariabele. Schakel de **deze waarde niet weergeven in de Configuration Manager-console** selectievakje in als u de verzamelingsvariabelen verbergen wilt, zodat ze niet zichtbaar in de Configuration Manager-console.  

5.  Geef eventueel de prioriteit voor Configuration Manager moet worden gebruikt wanneer de takenreeksvariabelen worden beoordeeld.  

6.  Wanneer u alle variabelen aan de verzameling hebt toegevoegd, klikt u op **OK**.  

##  <a name="BKMK_AdditionalActionsTS"></a> Aanvullende acties voor het beheren van takenreeksen  
 U kunt takenreeksen beheren door middel van extra acties wanneer u een takenreeks selecteert.  

#### <a name="to-select-a-task-sequence-to-manage"></a>Een takenreeks selecteren die u wilt beheren  

1.  Klik in de Configuration Manager-console op **Softwarebibliotheek**.  

2.  Vouw in de werkruimte **Softwarebibliotheek** **Besturingssystemen** uit en klik daarna op **Takenreeksen**.  

3.  Selecteer in de lijst **Takenreeks** de takenreeks die u wilt beheren, en selecteer daarna een van de beschikbare opties.  

 Gebruik de volgende tabel voor meer informatie over enkele extra acties om takenreeksen te beheren.  

|Actie|Beschrijving|  
|------------|-----------------|  
|**Kopiëren**|Hiermee wordt een kopie gemaakt van de geselecteerde takenreeks. Mogelijk vindt u deze actie handig wanneer u een nieuwe takenreeks wilt maken die is gebaseerd op een bestaande takenreeks.<br /><br /> Wanneer u een kopie maakt van een takenreeks in een map, wordt de kopie in die map vermeld tot u het takenreeksknooppunt vernieuwt.  Na het vernieuwen, wordt de kopie weergegeven in de hoofdmap.|  
|**Uitschakelen**|Hiermee wordt de takenreeks uitgeschakeld, zodat deze niet op computers kan worden uitgevoerd. Uitgeschakelde takenreeksen kunnen op computers worden geïmplementeerd, maar wordt niet uitgevoerd zolang deze zijn uitgeschakeld.|  
|**Inschakelen**|Hiermee wordt de takenreeks ingeschakeld, zodat deze kan worden uitgevoerd. U hoeft een geïmplementeerde takenreeks na inschakeling niet opnieuw te implementeren.|  
|**Voorbereid inhoudsbestand maken**|Hiermee wordt de wizard Voorbereid inhoudsbestand maken gestart om de inhoud van de takenreeks voor te bereiden. Zie voor meer informatie over het maken van een voorbereid inhoudsbestand [inhoud voorbereiden](../../core/servers/deploy/configure/deploy-and-manage-content.md#bkmk_prestage).|  
|**Verplaatsen**|Hiermee wordt de geselecteerde takenreeks verplaatst naar een andere map.|  

## <a name="next-steps"></a>Volgende stappen
[Scenario's voor het implementeren van enterprise-besturingssystemen](scenarios-to-deploy-enterprise-operating-systems.md)
