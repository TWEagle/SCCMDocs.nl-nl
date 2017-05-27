---
title: Maak een takenreeks om een besturingssysteem te upgraden | Microsoft-documenten
description: Takenreeksen in System Center Configuration Manager kunnen een besturingssysteem automatisch een upgrade van Windows 7 of hoger en Windows 10.
ms.custom: na
ms.date: 10/06/2016
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-osd
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 7591e386-a9ab-4640-8643-332dce5aa006
caps.latest.revision: 12
author: Dougeby
ms.author: dougeby
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: d7b13f3dea5a3ae413ca6b8150ec24e1632a4d4d
ms.openlocfilehash: e63b639836bc38a030a051e80db4b057ab75a0b0
ms.contentlocale: nl-nl
ms.lasthandoff: 05/17/2017


---
# <a name="create-a-task-sequence-to-upgrade-an-operating-system-in-system-center-configuration-manager"></a>Maak een takenreeks om een besturingssysteem in System Center Configuration Manager te upgraden

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*

Gebruik takenreeksen in System Center Configuration Manager automatisch bijwerken van een besturingssysteem van Windows 7 of hoger en Windows 10 op een doelcomputer. Maken van een takenreeks die verwijst naar de installatiekopie van het besturingssysteem die u wilt installeren op de doelcomputer en andere bijkomende inhoud, zoals toepassingen of software-updates die u wilt installeren. De takenreeks om een besturingssysteem te werken maakt deel uit van de [Windows upgraden naar de nieuwste versie](upgrade-windows-to-the-latest-version.md) scenario.  

##  <a name="BKMK_UpgradeOS"></a>Maak een takenreeks om een besturingssysteem te upgraden  
 Als u het besturingssysteem op computers bijwerken naar Windows 10, kunt u een takenreeks maken en selecteer **Upgrade van een besturingssysteem vanaf upgradepakket** in de Wizard Takenreeks maken. De wizard worden de stappen voor het werk het besturingssysteem, software-updates toepassen en installeren van toepassingen toevoegen. Voordat u de takenreeks maakt, moet het volgende worden voldaan:  

-   **Vereist**  

     - De Windows-10 [upgradepakket besturingssysteem](../get-started/manage-operating-system-upgrade-packages.md) moet beschikbaar zijn in de Configuration Manager-console.  

-   **Vereist (indien gebruikt)**  

    -   [Software-updates](../../sum/get-started/synchronize-software-updates.md) in de Configuration Manager-console moeten worden gesynchroniseerd.  

    -   [Toepassingen](../../apps/deploy-use/create-applications.md) moet worden toegevoegd aan de Configuration Manager-console.  

#### <a name="to-create-a-task-sequence-that-upgrades-an-operating-system"></a>Een takenreeks die een upgrade uitvoert van een besturingssysteem maken  

1.  Klik in de Configuration Manager-console op **Softwarebibliotheek**.  

2.  Vouw **Besturingssystemen** uit in de werkruimte **Softwarebibliotheek**en klik op **Takenreeksen**.  

3.  Klik op **Takenreeks maken** in het tabblad **Start** , in de groep **Maken** om de wizard Takenreeks maken te starten.  

4.  Op de **Maak een nieuwe Takenreeks** pagina, klikt u op **Upgrade van een besturingssysteem vanaf upgradepakket**, en klik vervolgens op **volgende**.  

5.  Configureer op de pagina **Takenreeksinformatie** de volgende instellingen en klik op **Volgende**.  

    -   **Takenreeksnaam**: Geef een naam die de takenreeks identificeert.  

    -   **Beschrijving**: Geef een beschrijving van de taak die door de takenreeks wordt uitgevoerd.  

6.  Op de **werk het besturingssysteem Windows** pagina, geef de volgende instellingen en klik vervolgens op **volgende**.  

    -   **Upgradepakket**: Geef het upgradepakket dat het bijwerken van de besturingssysteembestanden bevat. U kunt controleren of u de juiste upgradepakket hebt geselecteerd door te kijken naar de informatie in de **eigenschappen** deelvenster. Zie voor meer informatie [upgradepakketten besturingssysteem beheren](../get-started/manage-operating-system-upgrade-packages.md).  

    -   **Editie-index**: Als er meerdere besturingssysteem edition indexen in het pakket beschikbaar zijn, selecteert u de gewenste editie-index. Standaard wordt het eerste item geselecteerd.  

    -   **Productcode**: Geef de productcode voor de Windows-besturingssysteem te installeren. U kunt gecodeerde volumelicentiesleutels en standaardproductsleutels opgeven. Als u een niet-gecodeerde productcode gebruikt, moet elke groep van 5 tekens gescheiden worden door een streepje (-). Bijvoorbeeld: *XXXXX-XXXXX-XXXXX-XXXXX-XXXXX*. Als de upgrade voor een volume licentie-versie, is de productcode niet vereist. Een productcode hoeft u alleen wanneer de upgrade van een handelsversie van Windows.  

7.  Geef op de pagina **Inclusief updates** op of de vereiste software-updates, alle software-updates of geen software-updates moeten worden geïnstalleerd. Klik vervolgens op **Volgende**. Als u opgeeft om softwareupdates te installeren, installeert Configuration Manager alleen die softwareupdates die zijn gericht op de verzamelingen die de doelcomputer lid van is.  

8.  Geef op de pagina **Toepassingen installeren** de toepassingen op die moeten worden geïnstalleerd op de doelcomputer en klik op **Volgende**. Als u meerdere toepassingen opgeeft, kunt u opgeven dat de takenreeks wordt voortgezet als de installatie van een bepaalde toepassing mislukt.  

9. Voltooi de wizard.  



## <a name="configure-pre-cache-content"></a>Vooraf cache-inhoud configureren
Vanaf versie 1702, voor beschikbare implementaties van takenreeksen, kunt u de vooraf cache gebruiken om clients alleen relevante inhoud worden gedownload voordat een gebruiker de inhoud wordt geïnstalleerd.
> [!TIP]  
> Met versie 1702 geïntroduceerd, is de pre-cache een voorlopige versie-functie. Als u wilt inschakelen, Zie [gebruikmaken van de functies van updates pre-release](/sccm/core/servers/manage/pre-release-features).

Stel dat u wilt implementeren van een Windows-10 in-place upgrade takenreeks alleen een enkele takenreeks wilt gebruiken voor alle gebruikers en meerdere architecturen en/of talen. Voor versie 1702, als u een beschikbare installatie maakt en vervolgens de gebruiker **installeren** in Software Center, de inhoud gedownload op dat moment. Hiermee voegt u extra tijd voordat de installatie is gereed om te beginnen. Bovendien wordt alle inhoud waarnaar wordt verwezen in de takenreeks wordt gedownload. Dit omvat het upgradepakket voor besturingssysteem voor alle talen en -architecturen. Als elk ongeveer 3 GB groot zijn is, kan het downloadpakket behoorlijk groot zijn.

Vooraf cache-inhoud biedt u de optie om de client alleen de inhoud te downloaden van toepassing als de implementatie wordt ontvangen. Daarom wanneer de gebruiker **installeren** in Software Center, de inhoud gereed is en de installatie begint snel omdat de inhoud op de lokale vaste schijf.

### <a name="to-configure-the-pre-cache-feature"></a>De vooraf cachefunctie configureren

1. Upgradepakketten voor specifieke architecturen en talen voor besturingssysteem maken. Geef de architectuur en taal op de **gegevensbron** tabblad van het pakket. Gebruik de decimale conversie voor de taal (bijvoorbeeld 1033 is het decimaalteken voor Engels en 0x0409 is het hexadecimale equivalent). Zie voor meer informatie, [maken van een takenreeks om een besturingssysteem te upgraden](/sccm/osd/deploy-use/create-a-task-sequence-to-upgrade-an-operating-system).

    De architectuur en taal-waarden worden gebruikt om te voldoen aan de taak volgorde stap die u in de volgende stap om te bepalen maakt of het upgradepakket voor besturingssysteem vooraf moet worden opgeslagen.
2. Maak een takenreeks met voorwaardelijke stappen voor de verschillende talen en -architecturen. U kunt bijvoorbeeld een stap in de volgende notatie maken voor de Engelse versie:

    ![vooraf cache-eigenschappen](../media/precacheproperties2.png)

    ![vooraf cacheopties](../media/precacheoptions2.png)  

3. De takenreeks implementeert. Voor de functie cache voorafgaand aan het volgende configureren:
    - Op de **algemeen** tabblad **vooraf downloaden van inhoud voor deze takenreeks**.
    - Op de **implementatie-instellingen** tabblad, configureert u de takenreeks met de **beschikbaar** voor **doel**. Als u een **vereist** implementatie van de vooraf cache-functionaliteit werkt niet.
    - Op de **planning** tabblad voor de **plannen wanneer deze implementatie beschikbaar zal zijn** stellen, een tijdstip in de toekomst waarmee clients voldoende tijd om de inhoud vooraf in cache voordat de implementatie beschikbaar wordt gesteld aan gebruikers te kiezen. U kunt bijvoorbeeld de hoeveelheid tijd moet drie uur in de toekomst genoeg tijd bieden om de inhoud vooraf in cache opgeslagen instellen.  
    - Op de **distributiepunten** tabblad, configureert u de **implementatieopties** instellingen. Als de inhoud niet vooraf in cache op een client opgeslagen is voordat een gebruiker de installatie wordt gestart, worden deze instellingen gebruikt.


### <a name="user-experience"></a>Gebruikerservaring
- Wanneer de client het implementatiebeleid ontvangt, start het vooraf om de inhoud in cache. Dit omvat alle inhoud waarnaar wordt verwezen (een andere pakkettypen) en alleen de upgradepakket besturingssysteem die overeenkomt met de client op basis van de voorwaarden in de takenreeks te stellen.
- Wanneer de implementatie beschikbaar wordt gesteld aan gebruikers (instellen op de **planning** tabblad van de implementatie), een melding wordt weergegeven om gebruikers te informeren over de nieuwe implementatie en de implementatie wordt weergegeven in Software Center. De gebruiker kan gaat u naar Software Center en klikt u op **installeren** om de installatie te starten.
- Als de inhoud niet volledig vooraf in cache opgeslagen is, worden de instellingen op de instellingen wilt gebruiken de **Implementatieoptie** tabblad van de implementatie. U wordt aangeraden dat er voldoende tijd tussen wanneer de implementatie wordt gemaakt en het tijdstip waarop de implementatie beschikbaar voor gebruikers wordt wilt toestaan dat clients voldoende tijd om de inhoud vooraf in cache is.



## <a name="download-package-content-task-sequence-step"></a>Pakketinhoud takenreeksstap downloaden  
 De [pakketinhoud downloaden](../understand/task-sequence-steps.md#BKMK_DownloadPackageContent) stap kan worden gebruikt voor de **besturingssysteem bijwerken** stap in de volgende scenario's:  

-   U een enkele upgrade takenreeks dat met x86 en x64-platforms werkt. Als u dit wilt doen, voegt u twee **Pakketinhoud downloaden**-stappen toe aan de groep **Upgrade voorbereiden** met de voorwaarden om de clientarchitectuur te detecteren en alleen het geschikte upgradepakket voor het besturingssystemen te downloaden. Configureer elke **Pakketinhoud downloaden**-stap zodanig dat dezelfde variabele wordt gebruikt, en gebruik de variabele voor het mediumpad in de stap **Besturingssysteem bijwerken**.  

-   Als u een geschikt stuurprogrammapakket wilt downloaden, gebruikt u twee **Pakketinhoud downloaden**-stappen op voorwaarde dat het juiste hardwaretype wordt gedetecteerd voor elk stuurprogrammapakket. Configureer elke **Pakketinhoud downloaden**-stap zodanig dat dezelfde variabele wordt gebruikt, en gebruik de variabele voor de waarde **Tijdelijke inhoud** in de sectie met stuurprogramma's in de stap **Besturingssysteem bijwerken**.  

   > [!NOTE]
   > Wanneer er meer dan één pakket, wordt een numeriek achtervoegsel in Configuration Manager toegevoegd aan de naam van de variabele. Bijvoorbeeld, als u een variabele van % mycontent % als een aangepaste variabele opgeeft, is dit de hoofdmap voor waarbij alle inhoud waarnaar wordt verwezen is opgeslagen (die meerdere pakketten). Wanneer u in een vervolgstap naar de variabele verwijst, zoals Besturingssysteem bijwerken, wordt deze met een numeriek achtervoegsel gebruikt. In dit voorbeeld % mycontent01% of mycontent02%, waarbij het nummer overeenkomt met de volgorde waarin het pakket wordt vermeld in deze stap.

## <a name="optional-post-processing-task-sequence-steps"></a>Optionele na verwerking takenreeksstappen  
 Nadat u de takenreeks hebt gemaakt, kunt u extra stappen voor het verwijderen van toepassingen met bekende compatibiliteitsproblemen toevoegen of toevoegen na verwerking acties uit te voeren nadat de computer opnieuw is opgestart en de upgrade naar Windows 10 voltooid is. Deze aanvullende stappen toevoegen in de groep na verwerking van de takenreeks.  

> [!NOTE]  
>  Omdat deze takenreeks niet lineaire is, op de stappen beschreven die kunnen invloed hebben op de resultaten van de takenreeks, afhankelijk van of deze is upgrade van de clientcomputer voorwaarden zijn of als er op de clientcomputer terugkeren naar de versie van het besturingssysteem wordt gestart met.  

## <a name="optional-rollback-task-sequence-steps"></a>Takenreeksstappen optionele terugdraaien  
 Wanneer er iets mis zijn met het upgradeproces gaat nadat de computer opnieuw is opgestart, Setup wordt de upgrade terugdraaien naar het vorige besturingssysteem en de takenreeks verder met de stappen in de groep terugdraaien. Nadat u de takenreeks hebt gemaakt, kunt u optioneel stappen toevoegen aan de groep terugdraaien.  

## <a name="folder-and-files-removed-after-computer-restart"></a>Mappen en bestanden verwijderd nadat de computer opnieuw opstarten  
 Wanneer de takenreeks een besturingssysteem upgraden naar Windows 10 en alle overige stappen in de takenreeks zijn voltooid, worden de scripts die na verwerking en terugdraaien niet verwijderd totdat de computer opnieuw is opgestart.  Deze scriptbestanden bevatten geen gevoelige informatie.  

