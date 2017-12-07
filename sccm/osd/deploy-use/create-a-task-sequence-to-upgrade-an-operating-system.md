---
title: Maak een takenreeks om een besturingssysteem te upgraden
titleSuffix: Configuration Manager
description: Takenreeksen in System Center Configuration Manager kunnen een besturingssysteem automatisch een upgrade van Windows 7 of hoger naar Windows 10.
ms.custom: na
ms.date: 12/05/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: configmgr-osd
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 7591e386-a9ab-4640-8643-332dce5aa006
caps.latest.revision: "12"
author: Dougeby
ms.author: dougeby
manager: angrobe
ms.openlocfilehash: 002acbcff01105e612e8c090606a6aa5d45a014b
ms.sourcegitcommit: 52b956cfe32c3f06ae68d6ba6fc3244ce5a66325
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/06/2017
---
# <a name="create-a-task-sequence-to-upgrade-an-operating-system-in-system-center-configuration-manager"></a>Maak een takenreeks om een besturingssysteem in System Center Configuration Manager te upgraden

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*

Gebruik takenreeksen in System Center Configuration Manager automatisch bijwerken van een besturingssysteem van Windows 7 of hoger naar Windows 10 of Windows Server 2012 of later naar Windows Server 2016 op een doelcomputer. Maken van een takenreeks die verwijst naar de installatiekopie van het besturingssysteem die u wilt installeren op de doelcomputer en andere bijkomende inhoud, zoals toepassingen of software-updates die u wilt installeren. De takenreeks om een besturingssysteem te upgraden maakt deel uit van de [Windows upgraden naar de nieuwste versie](upgrade-windows-to-the-latest-version.md) scenario.  

##  <a name="BKMK_UpgradeOS"></a>Maak een takenreeks om een besturingssysteem te upgraden  
 Als u wilt het besturingssysteem op computers een upgrade uitvoert, kunt u een takenreeks maken en selecteren **Upgrade van een besturingssysteem vanaf upgradepakket** in de Wizard Takenreeks maken. De wizard voegt de stappen voor het upgraden van het besturingssysteem, software-updates toepassen en toepassingen installeren. Voordat u de takenreeks maakt, moet het volgende zijn voldaan:    

-   **Vereist**  

     - De [upgradepakket voor besturingssysteem](../get-started/manage-operating-system-upgrade-packages.md) moet beschikbaar zijn in de Configuration Manager-console.
     - Wanneer u een naar Windows Server 2016 upgrade, moet u de **dismissable compatibiliteit die kunnen worden genegeerd** instelling in de takenreeksstap besturingssysteem bijwerken of de upgrade mislukt.

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

7.  Geef op de pagina **Inclusief updates** op of de vereiste software-updates, alle software-updates of geen software-updates moeten worden geïnstalleerd. Klik vervolgens op **Volgende**. Als u opgeeft om softwareupdates te installeren, installeert Configuration Manager alleen die softwareupdates die zijn gericht op de verzamelingen waar de doelcomputer lid van is.  

8.  Geef op de pagina **Toepassingen installeren** de toepassingen op die moeten worden geïnstalleerd op de doelcomputer en klik op **Volgende**. Als u meerdere toepassingen opgeeft, kunt u opgeven dat de takenreeks wordt voortgezet als de installatie van een bepaalde toepassing mislukt.  

9. Voltooi de wizard.  



## <a name="configure-pre-cache-content"></a>Inhoud van de pre-cache configureren
Vanaf versie 1702, voor beschikbare implementaties van takenreeksen, kunt u de functie vooraf cache gebruiken om clients alleen relevante inhoud downloaden voordat een gebruiker de inhoud installeert hebben.
> [!TIP]  
> Deze functie is geïntroduceerd in versie 1702 als een [functie van de voorlopige versie](/sccm/core/servers/manage/pre-release-features). Vanaf versie 1706, deze functie is niet langer een voorlopige versie.

Stel dat u wilt implementeren van een takenreeks Windows 10 in-place upgrade slechts een enkele takenreeks voor alle gebruikers wilt en meerdere architecturen en/of talen. Voorafgaand aan versie 1702, als u een beschikbare installatie maakt, en vervolgens klikt de gebruiker op **installeren** in Software Center, de inhoud gedownload op dat moment. Hiermee voegt u extra tijd voordat de installatie is gereed om te starten. Ook wordt alle inhoud waarnaar wordt verwezen in de takenreeks gedownload. Dit omvat het upgradepakket voor besturingssysteem voor alle talen en -architecturen. Als elk ongeveer drie GB groot, kan het downloadpakket behoorlijk groot zijn.

Vooraf cache-inhoud biedt u de optie voor het toestaan van de client alleen de inhoud te downloaden van toepassing als de implementatie wordt ontvangen. Daarom wanneer de gebruiker klikt op **installeren** in Software Center, de inhoud gereed is en de installatie begint snel omdat de inhoud op de lokale vaste schijf.

### <a name="to-configure-the-pre-cache-feature"></a>De cachefunctie vooraf configureren

1. Upgradepakketten voor specifieke architecturen en talen voor besturingssysteem maken. Geef de architectuur en taal op de **gegevensbron** tabblad van het pakket. Gebruik de decimale conversie voor de taal (bijvoorbeeld 1033 is het decimaalteken voor Engels en 0x0409 is hetzelfde als hexadecimaal). Zie voor meer informatie [een takenreeks maken om een besturingssysteem te upgraden](/sccm/osd/deploy-use/create-a-task-sequence-to-upgrade-an-operating-system).

    De architectuur en taal-waarden worden gebruikt om te voldoen aan de taak sequence stap die u in de volgende stap om te bepalen maakt of het upgradepakket voor besturingssysteem vooraf moet worden opgeslagen.
2. Maak een takenreeks met voorwaardelijke stappen voor de verschillende talen en -architecturen. U kunt bijvoorbeeld een stap als volgt maken voor de Engelse versie:

    ![Eigenschappen van de pre-cache](../media/precacheproperties2.png)

    ![vooraf cacheopties](../media/precacheoptions2.png)  

3. De takenreeks implementeert. Voor de functie vooraf cache, het volgende configureren:
    - Op de **algemene** tabblad **vooraf downloaden van inhoud voor deze takenreeks**.
    - Op de **implementatie-instellingen** tabblad, configureer de takenreeks met de **beschikbaar** voor **doel**. Als u maakt een **vereist** implementatie van de pre-cache-functionaliteit werkt niet.
    - Op de **planning** tabblad voor de **plannen wanneer deze implementatie beschikbaar zal zijn** instelt, kiest u een tijd in de toekomst waarmee clients voldoende tijd is voor de inhoud vooraf in cache voordat de implementatie beschikbaar wordt gesteld aan gebruikers. U kunt bijvoorbeeld instellen dat de beschikbare tijd worden drie uur in de toekomst genoeg tijd bieden om de inhoud vooraf in cache opgeslagen.  
    - Op de **distributiepunten** tabblad, configureert de **implementatieopties** instellingen. Als de inhoud niet vooraf in cache op een client opgeslagen is voordat een gebruiker de installatie wordt gestart, worden deze instellingen gebruikt.


### <a name="user-experience"></a>Gebruikerservaring
- Wanneer de client het implementatiebeleid ontvangt, wordt gestart om de inhoud vooraf in cache. Dit omvat alle inhoud waarnaar wordt verwezen (een andere typen) en alleen het upgradepakket voor besturingssysteem die overeenkomt met de client op basis van de voorwaarden die u in de takenreeks instelt.
- Wanneer de implementatie wordt beschikbaar gesteld aan gebruikers (instellen op de **planning** tabblad van de implementatie), een melding weergegeven om gebruikers te informeren over de nieuwe implementatie en de implementatie zichtbaar in Software Center. De gebruiker kan gaat u naar Software Center en klikt u op **installeren** om de installatie te starten.
- Als de inhoud niet volledig vooraf in cache opgeslagen is, wordt dit de instellingen gebruikt van de **Implementatieoptie** tabblad van de implementatie. U wordt aangeraden dat er voldoende tijd tussen wanneer de implementatie wordt gemaakt en het tijdstip waarop de implementatie beschikbaar voor gebruikers wordt wilt toestaan dat clients voldoende tijd is voor de inhoud vooraf in cache is.



## <a name="download-package-content-task-sequence-step"></a>Takenreeksstap pakketinhoud downloaden  
 De [pakketinhoud downloaden](../understand/task-sequence-steps.md#BKMK_DownloadPackageContent) stap kan worden gebruikt voordat de **besturingssysteem bijwerken** stap in de volgende scenario's:  

-   U een takenreeks voor het één upgrade die x86- en x64-platforms werkt. Als u dit wilt doen, voegt u twee **Pakketinhoud downloaden**-stappen toe aan de groep **Upgrade voorbereiden** met de voorwaarden om de clientarchitectuur te detecteren en alleen het geschikte upgradepakket voor het besturingssystemen te downloaden. Configureer elke **Pakketinhoud downloaden**-stap zodanig dat dezelfde variabele wordt gebruikt, en gebruik de variabele voor het mediumpad in de stap **Besturingssysteem bijwerken**.  

-   Als u een geschikt stuurprogrammapakket wilt downloaden, gebruikt u twee **Pakketinhoud downloaden**-stappen op voorwaarde dat het juiste hardwaretype wordt gedetecteerd voor elk stuurprogrammapakket. Configureer elke **Pakketinhoud downloaden**-stap zodanig dat dezelfde variabele wordt gebruikt, en gebruik de variabele voor de waarde **Tijdelijke inhoud** in de sectie met stuurprogramma's in de stap **Besturingssysteem bijwerken**.  

   > [!NOTE]
   > Wanneer er meer dan één pakket, wordt een numeriek achtervoegsel aan de variabelenaam in Configuration Manager toegevoegd. Bijvoorbeeld, als u een variabele van % mycontent % als aangepaste variabele opgeeft, is dit de hoofdmap waarin alle inhoud waarnaar wordt verwezen is opgeslagen (dit kan meerdere pakketten zijn). Wanneer u in een vervolgstap naar de variabele verwijst, zoals Besturingssysteem bijwerken, wordt deze met een numeriek achtervoegsel gebruikt. In dit voorbeeld % mycontent01% of % mycontent02%, waarbij het nummer overeenkomt met de volgorde waarin het pakket in deze stap wordt vermeld.

## <a name="optional-post-processing-task-sequence-steps"></a>Optionele na verwerking takenreeksstappen  
 Nadat u de takenreeks hebt gemaakt, kunt u aanvullende stappen toevoegen voor het verwijderen van toepassingen met bekende compatibiliteitsproblemen, of u kunt toevoegen na verwerking acties uit te voeren nadat de computer opnieuw is opgestart en de upgrade naar Windows 10 geslaagd is. Deze aanvullende stappen toevoegen in de groep na verwerking van de takenreeks.  

> [!NOTE]  
>  Omdat deze takenreeks niet lineair is, er bepaalde voorwaarden voor stappen die invloed kunnen hebben op de resultaten van de takenreeks, afhankelijk van of deze de clientcomputer met succes wordt bijgewerkt of dat er terugdraaien van de clientcomputer naar de oorspronkelijke besturingssysteemversie.  

## <a name="optional-rollback-task-sequence-steps"></a>Terugdraaien van de optionele takenreeksstappen  
 Wanneer er iets mis met het upgradeproces gaat nadat de computer opnieuw is opgestart, Setup wordt de upgrade terugdraaien naar het vorige besturingssysteem en de takenreeks wordt verder met de stappen in de groep terugdraaien. Nadat u de takenreeks hebt gemaakt, kunt u optionele stappen toevoegen aan de groep terugdraaien.  

## <a name="folder-and-files-removed-after-computer-restart"></a>Map en bestanden verwijderd nadat de computer opnieuw opstarten  
 Wanneer de takenreeks een besturingssysteem upgraden naar Windows 10 en alle overige stappen in de takenreeks zijn voltooid, worden de scripts na verwerking en terugdraaien niet verwijderd totdat de computer opnieuw is opgestart.  Deze scriptbestanden bevatten geen gevoelige informatie.  
