---
title: Maak een takenreeks om een besturingssysteem te upgraden
titleSuffix: Configuration Manager
description: Een takenreeks gebruiken voor het automatisch upgrade uitvoeren in Windows 7 of hoger naar Windows 10
ms.custom: na
ms.date: 03/22/2018
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-osd
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 7591e386-a9ab-4640-8643-332dce5aa006
caps.latest.revision: ''
author: aczechowski
ms.author: aaroncz
manager: dougeby
ms.openlocfilehash: 91d3bf5b1488eb7eac52c7426e4bdeeb92ff43b8
ms.sourcegitcommit: 11bf4ed40ed0cbb10500cc58bbecbd23c92bfe20
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 03/23/2018
---
# <a name="create-a-task-sequence-to-upgrade-an-operating-system-in-system-center-configuration-manager"></a>Maak een takenreeks om een besturingssysteem in System Center Configuration Manager te upgraden

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*

Gebruik takenreeksen in Configuration Manager automatisch bijwerken van een besturingssysteem op een doelcomputer. Deze upgrade kan worden vanaf Windows 7 of hoger naar Windows 10 of van Windows Server 2012 of later naar Windows Server 2016. Maak een takenreeks die verwijst naar de OS-upgradepakket en andere inhoud, zoals toepassingen of software om updates te installeren. De takenreeks om een besturingssysteem te upgraden maakt deel uit van de [Windows upgraden naar de nieuwste versie](upgrade-windows-to-the-latest-version.md) scenario.  



##  <a name="BKMK_UpgradeOS"></a> Maak een takenreeks om een besturingssysteem te upgraden  
 Als u wilt het besturingssysteem op computers een upgrade uitvoert, kunt u een takenreeks maken en selecteren **Upgrade van een besturingssysteem vanaf upgradepakket** in de Wizard Takenreeks maken. De wizard voegt de takenreeksstappen werk het besturingssysteem en toepassingen installeren software-updates toepassen. Voordat u de takenreeks maakt, moet de volgende vereisten voldaan:    

-   **Vereist**  

     - De [upgradepakket voor besturingssysteem](../get-started/manage-operating-system-upgrade-packages.md) moet beschikbaar zijn in de Configuration Manager-console.
     - Wanneer u een upgrade naar Windows Server 2016, selecteert u de **dismissable compatibiliteit die kunnen worden genegeerd** instellen in de takenreeksstap besturingssysteem bijwerken. Anders mislukt de upgrade.

-   **Vereist (indien gebruikt)**  

    -   [Software-updates](../../sum/get-started/synchronize-software-updates.md) moeten worden gesynchroniseerd in de Configuration Manager-console.  

    -   [Toepassingen](../../apps/deploy-use/create-applications.md) moet worden toegevoegd aan de Configuration Manager-console.  

#### <a name="to-create-a-task-sequence-that-upgrades-an-operating-system"></a>Maken van een takenreeks die een besturingssysteem wordt bijgewerkt  

1.  Klik in de Configuration Manager-console op **Softwarebibliotheek**.  

2.  Vouw **Besturingssystemen** uit in de werkruimte **Softwarebibliotheek**en klik op **Takenreeksen**.  

3.  Klik op **Takenreeks maken** in het tabblad **Start** , in de groep **Maken** om de wizard Takenreeks maken te starten.  

4.  Op de **een nieuwe Takenreeks maken** pagina, klikt u op **Upgrade van een besturingssysteem vanaf upgradepakket**, en klik vervolgens op **volgende**.  

5.  Configureer op de pagina **Takenreeksinformatie** de volgende instellingen en klik op **Volgende**.  

    -   **Takenreeksnaam**: Geef een naam die de takenreeks identificeert.  

    -   **Beschrijving**: Geef een beschrijving van de taak die door de takenreeks wordt uitgevoerd.  

6.  Op de **werk het besturingssysteem Windows** pagina, geef de volgende instellingen en klik vervolgens op **volgende**.  

    -   **Upgradepakket**: Geef het upgradepakket dat het bijwerken van de besturingssysteembestanden bevat. U kunt controleren of u het juiste upgradepakket hebt geselecteerd door te kijken naar de informatie in de **eigenschappen** deelvenster. Zie voor meer informatie [upgradepakketten voor besturingssysteem beheren](../get-started/manage-operating-system-upgrade-packages.md).  

    -   **Editie-index**: Als er meerdere editie-indexen van besturingssysteem in het pakket beschikbaar zijn, selecteert u de gewenste editie-index. Standaard wordt het eerste item geselecteerd.  

    -   **Productcode**: Geef de productcode voor het Windows-besturingssysteem te installeren. U kunt gecodeerde volumelicentiesleutels en standaardproductsleutels opgeven. Als u een niet-gecodeerde productcode gebruikt, moet elke groep van vijf tekens worden gescheiden door een streepje (-). Bijvoorbeeld: *XXXXX-XXXXX-XXXXX-XXXXX-XXXXX*. Wanneer de upgrade voor een volumelicentie-editie is, is de productcode niet vereist. Een productcode hoeft u alleen wanneer de upgrade voor een verkoopeditie van Windows is.  

    -   **Negeer eventuele berichten dismissable compatibiliteit**: Selecteer deze instelling als u naar Windows Server 2016 upgraden wilt. Als u deze instelling niet selecteert, mislukt de takenreeks worden uitgevoerd omdat Windows Setup wacht tot de gebruiker op **bevestigen** in een dialoogvenster Windows-app-compatibiliteit.   

7.  Op de **Updates opnemen** pagina, opgeven of er nodig om te installeren, alle of geen software-updates. Klik op **Volgende**. Als u opgeeft om softwareupdates te installeren, installeert Configuration Manager alleen die softwareupdates die zijn gericht op de verzamelingen waarvan de doelcomputer lid is.  

8.  Geef op de pagina **Toepassingen installeren** de toepassingen op die moeten worden geïnstalleerd op de doelcomputer en klik op **Volgende**. Als u meerdere toepassingen opgeeft, kunt u opgeven dat de takenreeks wordt voortgezet als de installatie van een bepaalde toepassing mislukt.  

9. Voltooi de wizard.  


 > [!Important] 
 > Wanneer de takenreeks voltooid is, wordt de client niet de scripts na verwerking en terugdraaien verwijderd totdat de computer opnieuw is opgestart. Deze scriptbestanden bevatten geen gevoelige informatie.  


 > [!Note]
 > Vanaf versie 1802, bevat de standaard taak sequence-sjabloon voor Windows 10 in-place upgrade extra groepen met aanbevolen acties om toe te voegen voor en na het upgradeproces. Deze acties gelden veel klanten die met succes apparaten naar Windows 10 upgraden. Zie voor meer informatie, aanbevolen takenreeksstappen [voorbereiden voor upgrade](#recommended-task-sequence-steps-to-prepare-for-upgrade) en [voor naverwerking](#recommended-task-sequence-steps-for-post-processing).



## <a name="configure-pre-cache-content"></a>Inhoud van de pre-cache configureren
De vooraf cachefunctie voor beschikbare implementaties van takenreeksen kan clients relevante OS-upgradepakket inhoud downloaden voordat een gebruiker de takenreeks wordt uitgevoerd installeert.
> [!TIP]  
> Deze functie is geïntroduceerd in versie 1702 als een [functie van de voorlopige versie](/sccm/core/servers/manage/pre-release-features). Vanaf versie 1706, deze functie is niet langer een voorlopige versie.

Bijvoorbeeld, u alleen een enkele in-place upgrade takenreeks wilt gebruiken voor alle gebruikers en vele architecturen en talen. In eerdere versies begint de inhoud te downloaden wanneer de gebruiker een beschikbare takenreeksimplementatie vanuit Software Center installeert. Deze vertraging voegt meer tijd voordat de installatie is gereed om te starten. Alle inhoud waarnaar wordt verwezen in de takenreeks wordt gedownload. Deze inhoud bevat het upgradepakket voor besturingssysteem voor alle talen en -architecturen. Als u elke upgradepakket is ongeveer drie GB groot is, wordt de totale inhoud groot is.

Pre-cache-inhoud geeft u de optie om te laten de client downloaden alleen de toepasselijke OS upgraden pakket, evenals alle andere inhoud waarnaar wordt verwezen als de implementatie wordt ontvangen. Wanneer de gebruiker klikt op **installeren** in Software Center, de inhoud gereed is en de installatie begint snel omdat de inhoud op de lokale vaste schijf.

 > [!NOTE]
 > Dit gedrag momenteel alleen van toepassing op het updatepakket van het besturingssysteem. Dit pakket is de enige inhoud waarvoor u de overeenkomende architectuur of de taal opgeven. Bijvoorbeeld, als de takenreeks verwijst ook naar meerdere stuurprogrammapakketten, downloadt de client op dit moment ze allemaal. De engine voor takenreeksen evalueert de voorwaarden voor de stappen wanneer de takenreeks wordt uitgevoerd, niet van tevoren. De client gebruikt de labels in de pakketeigenschappen om te bepalen welke inhoud in de cache vooraf.

### <a name="to-configure-the-pre-cache-feature"></a>De cachefunctie vooraf configureren

1. Upgradepakketten voor besturingssysteem voor specifieke architecturen en talen maken. Geef de architectuur en taal op de **gegevensbron** tabblad van het pakket. Gebruik de decimale conversie voor de taal. Bijvoorbeeld 1033 is de decimale waarde voor Engels en 0x0409 hexadecimale equivalent is.

    De client evalueert de architectuur en taal-waarden om te bepalen welke OS-upgradepakket die wordt gedownload tijdens het vooraf opslaan in cache.

1. Maak een takenreeks met voorwaardelijke stappen voor de verschillende talen en -architecturen. De volgende stap gebruikt bijvoorbeeld de Engelse versie:

    ![Editor voor takenreeksen met meerdere stappen van het besturingssysteem upgraden voor Nederlands, DEU en JPN](../media/precacheproperties2.png)

    ![Editor voor takenreeksen, tabblad Opties, de WMI WQL-query voor de landinstelling en OSArchitecture weergeven](../media/precacheoptions2.png)  

3. De takenreeks implementeert. Configureer de volgende instellingen voor de functie vooraf cache:
    - Op de **algemene** tabblad **vooraf downloaden van inhoud voor deze takenreeks**.
    - Op de **implementatie-instellingen** tabblad, configureer de takenreeks met de **beschikbaar** voor **doel**.
    - Op de **planning** tabblad voor de **plannen wanneer deze implementatie beschikbaar zal zijn** instelt, kiest u de geselecteerde tijd. Start de client vooraf inhoud opslaan in cache op de beschikbare tijd van de implementatie. Wanneer een bepaalde client ontvangt dit beleid, de beschikbare tijd is verstreken, dus vooraf cache downloaden meteen gestart. Als de client dit beleid ontvangt, maar de beschikbare tijd in de toekomst is, start de client niet vooraf inhoud in cache opslaan, totdat de beschikbare tijd optreedt. 
    - Op de **distributiepunten** tabblad, configureert de **implementatieopties** instellingen. Als de inhoud niet vooraf in cache opgeslagen is voordat een gebruiker de installatie wordt gestart, gebruikt de client deze instellingen.
  

### <a name="user-experience"></a>Gebruikerservaring
- Wanneer de client het implementatiebeleid ontvangt, wordt er gestart vóór de inhoud in cache na de implementatie beschikbaar komen. Deze inhoud bevat pakketten van alle waarnaar wordt verwezen, maar alleen het OS-upgradepakket die overeenkomt met de architectuur en taal kenmerken op het pakket.
- Wanneer de client de implementatie beschikbaar voor gebruikers, wordt een melding weergegeven om gebruikers te informeren over de nieuwe implementatie. De takenreeks is nu zichtbaar in Software Center. De gebruiker kan gaat u naar Software Center en klikt u op **installeren** om de installatie te starten.
- Als de inhoud niet volledig vooraf in cache opgeslagen is wanneer de gebruiker de takenreeks installeert, wordt de client de instellingen die u opgeeft op de **Implementatieoptie** tabblad van de implementatie. 



## <a name="recommended-task-sequence-steps-to-prepare-for-upgrade"></a>Aanbevolen takenreeksstappen voorbereiden voor upgrade

Vanaf versie 1802, bevat de standaard taak sequence-sjabloon voor Windows 10 in-place upgrade extra groepen met aanbevolen acties om toe te voegen voor de upgrade. Deze acties in de **voorbereiden voor Upgrade** groep gelden veel klanten die met succes apparaten naar Windows 10 upgraden. Voor sites op eerdere versies 1802 handmatig deze acties toevoegen aan uw takenreeks in de **voorbereiden voor Upgrade** groep.
- **Accu controleert**: Stappen in deze groep om te controleren of de computer met behulp van de accu of power bekabelde toevoegen. Deze actie is vereist voor een aangepast script of het hulpprogramma voor het uitvoeren van deze controle.
- **Netwerk/bekabelde verbinding controles**: Voeg stappen toe in deze groep om te controleren of de computer is verbonden met een netwerk en is niet via een draadloze verbinding. Deze actie is vereist voor een aangepast script of het hulpprogramma voor het uitvoeren van deze controle.
- **Niet-compatibele toepassingen verwijderen**: Voeg stappen toe in deze groep te verwijderen van alle toepassingen die niet compatibel met deze versie van Windows 10 zijn. De methode voor het verwijderen van een toepassing verschilt. Als de toepassing gebruikmaakt van Windows Installer, kopieert u de **programma voor verwijderen** vanaf de opdrachtregel van de **programma's** tabblad op Windows Installer eigenschappen van het implementatietype van de toepassing. Voeg vervolgens een **opdrachtregel uitvoeren** stap in deze groep met de opdrachtregel voor verwijdering programma. Bijvoorbeeld: </br>`msiexec /x {150031D8-1234-4BA8-9F52-D6E5190D1CBA} /q`</br> 
- **Verwijderen van niet-compatibele stuurprogramma's**: Voeg stappen toe in deze groep te verwijderen van stuurprogramma's die niet compatibel met deze versie van Windows 10 zijn.
- **Beveiliging van derden verwijderen/onderbreken**: Stappen in deze groep te verwijderen of onderbreken van derden beveiligingsprogramma's, zoals antivirus toevoegen.
   - Als u van een derde schijf versleuteling programma gebruikmaakt, geeft u bijbehorende stuurprogramma versleuteling voor Windows Setup uit met de **/ReflectDrivers** [opdrachtregeloptie](/windows-hardware/manufacture/desktop/windows-setup-command-line-options). Voeg een [Takenreeksvariabele instellen](/sccm/osd/understand/task-sequence-steps#BKMK_SetTaskSequenceVariable) stap in de takenreeks wordt uitgevoerd in deze groep. De takenreeksvariabele ingesteld op **OSDSetupAdditionalUpgradeOptions**. De waarde instelt op **/ReflectDriver** met het pad naar het stuurprogramma. Dit [actie takenreeksvariabele](/sccm/osd/understand/task-sequence-action-variables#upgrade-operating-system) voegt u de Windows Setup vanaf de opdrachtregel die wordt gebruikt door de takenreeks wordt uitgevoerd. Neem contact op met de softwareleverancier voor elke extra hulp bij dit proces.

### <a name="download-package-content-task-sequence-step"></a>Takenreeksstap pakketinhoud downloaden  
 De [pakketinhoud downloaden](../understand/task-sequence-steps.md#BKMK_DownloadPackageContent) stap kan worden gebruikt voordat de **besturingssysteem bijwerken** stap in de volgende scenario's:  

-   U gebruikt een enkele takenreeks voor upgraden voor x86- en x64 platforms. Voegt u twee **pakketinhoud downloaden** stappen in de **voorbereiden voor Upgrade** groep. Voorwaarden instellen op elke stap voor het detecteren van de clientarchitectuur. Deze voorwaarde zorgt ervoor dat de stap voor het downloaden van alleen het geschikte upgradepakket voor besturingssysteem. Configureer elke **Pakketinhoud downloaden**-stap zodanig dat dezelfde variabele wordt gebruikt, en gebruik de variabele voor het mediumpad in de stap **Besturingssysteem bijwerken**.  

-   Als u een geschikt stuurprogrammapakket wilt downloaden, gebruikt u twee **Pakketinhoud downloaden**-stappen op voorwaarde dat het juiste hardwaretype wordt gedetecteerd voor elk stuurprogrammapakket. Configureer elke **pakketinhoud downloaden** stap dezelfde variabele te gebruiken. Vervolgens gebruikt deze variabele voor de **tijdelijke inhoud** waarde in de sectie met stuurprogramma's op de **besturingssysteem bijwerken** stap.  

   > [!NOTE]
   > Wanneer er meer dan één pakket, wordt een numeriek achtervoegsel aan de variabelenaam in Configuration Manager toegevoegd. Bijvoorbeeld, als u een variabele van % mycontent % als aangepaste variabele opgeeft, is deze locatie waar alle inhoud waarnaar wordt verwezen door de client worden opgeslagen. Als u verwijst naar de variabele in een latere stap, zoals **besturingssysteem bijwerken**, de variabele met een numeriek achtervoegsel gebruikt. In dit voorbeeld, mycontent01% of % mycontent02%, waarbij het nummer overeenkomt met de volgorde waarin de **pakketinhoud downloaden** stap geeft een lijst van deze specifieke inhoud.



## <a name="recommended-task-sequence-steps-for-post-processing"></a>Aanbevolen takenreeksstappen na verwerking   
 Nadat u de takenreeks hebt gemaakt, voeg extra stappen in de **naverwerking** groep van de takenreeks.  

> [!NOTE]  
>  Deze takenreeks is niet lineair. Er bepaalde voorwaarden voor stappen die kunnen invloed hebben op de resultaten van de takenreeks wordt uitgevoerd. Dit gedrag hangt af van of deze de clientcomputer met succes wordt bijgewerkt, of als het terugdraaien van de clientcomputer naar het oorspronkelijke besturingssysteem.  

Vanaf versie 1802, bevat de standaard taak sequence-sjabloon voor Windows 10 in-place upgrade extra groepen met aanbevolen acties moeten worden toegevoegd na het upgradeproces. Deze acties in de **naverwerking** groep gelden veel klanten die met succes apparaten naar Windows 10 upgraden. Voor sites op eerdere versies 1802 handmatig deze acties toevoegen aan uw takenreeks in de **naverwerking** groep.
- **Stuurprogramma's op basis van setup toepassen**: Voeg stappen toe in deze groep setup-stuurprogramma's (.exe) van pakketten installeren.
- **Beveiliging van derden installeren of inschakelen**: Voeg stappen toe in deze groep te installeren of programma's van derden, beveiliging, zoals antivirus inschakelen. 
- **Standaard-Windows-apps en koppelingen instellen**: Voeg stappen toe in deze groep Windows standaard-apps en bestandskoppelingen instellen. Een referentiecomputer met de gewenste app koppelingen eerst voorbereiden. Voer vervolgens de volgende opdrachtregel om te exporteren: </br>`dism /online /Export-DefaultAppAssociations:"%UserProfile%\Desktop\DefaultAppAssociations.xml"`</br>Het XML-bestand aan een pakket toevoegt. Voeg vervolgens een [opdrachtregel uitvoeren](/sccm/osd/understand/task-sequence-steps#BKMK_RunCommandLine) stap in deze groep. Geef het pakket met het XML-bestand en geef vervolgens de volgende opdrachtregel: </br>`dism /online /Import-DefaultAppAssociations:DefaultAppAssocations.xml`</br> Zie voor meer informatie [exporteren of importeren koppelingen standaard](/windows-hardware/manufacture/desktop/export-or-import-default-application-associations).
- **Aanpassingen en persoonlijke instellingen toepassen**: Voeg stappen toe in deze groep toe te passen Start menu-aanpassingen, zoals programmagroepen indelen. Zie voor meer informatie [aanpassen van het startscherm](/windows-hardware/manufacture/desktop/customize-the-start-screen).



## <a name="optional-task-sequence-steps-for-rollback"></a>Optionele takenreeksstappen voor terugdraaien  
 Wanneer er iets mis met het upgradeproces gaat nadat de computer opnieuw is opgestart, Windows Setup wordt de upgrade terugdraaien naar het vorige besturingssysteem. De takenreeks wordt vervolgens doorgaat met de stappen in de **terugdraaien** groep. Nadat u de takenreeks hebt gemaakt, kunt u optionele stappen toevoegen in de groep terugdraaien. Wijzigingen in het systeem in het voorbereiden voor Upgrade groep, zoals het verwijderen van niet-compatibele software bijvoorbeeld omkeren.



## <a name="additional-recommendations"></a>Extra aanbevelingen
- Windows-documentatie te lezen [upgrade fouten kunt oplossen door Windows 10](/windows/deployment/upgrade/resolve-windows-10-upgrade-errors). In dit artikel bevat ook gedetailleerde informatie over het bijwerkproces.
- Op de standaard **gereedheid controleren** stap, schakelt u **minimale vrije schijfruimte (MB) garanderen**. De waarde instelt op ten minste **16384** (16 GB) voor een 32-bits besturingssysteem upgradepakket of **20480** (20 GB) voor 64-bits. 
- Gebruik de **SMSTSDownloadRetryCount** [ingebouwde takenreeksvariabele](/sccm/osd/understand/task-sequence-built-in-variables) te downloaden beleid voor opnieuw proberen. Momenteel standaard zal de client opnieuw tweemaal te gebruiken. Deze variabele is ingesteld op twee (2). Als uw clients zich niet op een bekabeld bedrijfsnetwerk verbinding, helpen extra pogingen de client beleid verkrijgen. Met deze variabele zorgt ervoor dat er geen negatieve neveneffect dan vertraagde fout als het beleid niet kan downloaden.<!-- 501016 --> Verhoogt ook de **SMSTSDownloadRetryDelay** variabele van de standaardwaarde van 15 seconden.
- Voer een beoordeling inline-compatibiliteit. 
   - Toevoegen van een tweede **besturingssysteem bijwerken** stap vroeg in de **voorbereiden voor Upgrade** groep. Naam *Upgradebeoordeling*. Geef het upgradepakket voor dezelfde en schakelt u de optie voor het **uitvoeren van Windows-installatiecompatibiliteitsscan zonder dat de upgrade gestart**. Schakel **Doorgaan bij fout** op het tabblad Opties. 
   - Volg deze onmiddellijk *Upgradebeoordeling* stap, het toevoegen van een **opdrachtregel uitvoeren** stap. Geef de volgende opdrachtregel:</br> `cmd /c exit %_SMSTSOSUpgradeActionReturnCode%`</br>Op de **opties** tabblad, voeg de volgende voorwaarde toe: </br>`Task Sequence Variable _SMSTSOSUpgradeActionReturnCode not equals 3247440400` </br>Deze retourcode is het decimale equivalent van MOSETUP_E_COMPAT_SCANONLY (0xC1900210), een scan voor compatibiliteit van geslaagde zonder problemen. Als de *Upgradebeoordeling* stap kan worden uitgevoerd en deze code retourneert, wordt deze stap overgeslagen. Als de stap assessment een retourcode retourneert, mislukt deze stap met de takenreeks wordt uitgevoerd met de retourcode van de Windows-installatiecompatibiliteitsscan.
   - Zie voor meer informatie [besturingssysteem bijwerken](/sccm/osd/understand/task-sequence-steps#BKMK_UpgradeOS).
- Als u wijzigen van het apparaat van de BIOS in UEFI tijdens deze takenreeks wilt, Zie [BIOS converteren naar UEFI tijdens een upgrade ter plekke](/sccm/osd/deploy-use/task-sequence-steps-to-manage-bios-to-uefi-conversion#convert-from-bios-to-uefi-during-an-in-place-upgrade).
