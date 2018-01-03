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
author: aczechowski
ms.author: aaroncz
manager: angrobe
ms.openlocfilehash: 058b0710484a0452ddf19655bf2cabbb43f624ad
ms.sourcegitcommit: 92c3f916e6bbd35b6208463ff406e0247664543a
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 01/02/2018
---
# <a name="create-a-task-sequence-to-upgrade-an-operating-system-in-system-center-configuration-manager"></a>Maak een takenreeks om een besturingssysteem in System Center Configuration Manager te upgraden

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*

Gebruik takenreeksen in Configuration Manager automatisch bijwerken van een besturingssysteem op een doelcomputer. Deze upgrade kan worden vanaf Windows 7 of hoger naar Windows 10 of van Windows Server 2012 of later naar Windows Server 2016. U een takenreeks die verwijst naar het upgradepakket van het besturingssysteem en andere inhoud, zoals toepassingen of software om updates te installeren. De takenreeks om een besturingssysteem te upgraden maakt deel uit van de [Windows upgraden naar de nieuwste versie](upgrade-windows-to-the-latest-version.md) scenario.  

##  <a name="BKMK_UpgradeOS"></a>Maak een takenreeks om een besturingssysteem te upgraden  
 Als u wilt het besturingssysteem op computers een upgrade uitvoert, kunt u een takenreeks maken en selecteren **Upgrade van een besturingssysteem vanaf upgradepakket** in de Wizard Takenreeks maken. De wizard voegt de stappen voor het upgraden van het besturingssysteem, software-updates toepassen en toepassingen installeren. Voordat u de takenreeks maakt, moet de volgende vereisten voldaan:    

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

7.  Geef op de pagina **Inclusief updates** op of de vereiste software-updates, alle software-updates of geen software-updates moeten worden geïnstalleerd. Klik vervolgens op **Volgende**. Als u opgeeft om softwareupdates te installeren, installeert Configuration Manager alleen die softwareupdates die zijn gericht op de verzamelingen waarvan de doelcomputer lid is.  

8.  Geef op de pagina **Toepassingen installeren** de toepassingen op die moeten worden geïnstalleerd op de doelcomputer en klik op **Volgende**. Als u meerdere toepassingen opgeeft, kunt u opgeven dat de takenreeks wordt voortgezet als de installatie van een bepaalde toepassing mislukt.  

9. Voltooi de wizard.  



## <a name="configure-pre-cache-content"></a>Inhoud van de pre-cache configureren
Vanaf versie 1702, kan de vooraf cachefunctie voor beschikbare implementaties van takenreeksen clients met alleen relevante inhoud downloaden voordat een gebruiker de takenreeks wordt uitgevoerd installeert.
> [!TIP]  
> Deze functie is geïntroduceerd in versie 1702 als een [functie van de voorlopige versie](/sccm/core/servers/manage/pre-release-features). Vanaf versie 1706, deze functie is niet langer een voorlopige versie.

Stel dat u wilt implementeren van een takenreeks Windows 10 in-place upgrade slechts een enkele takenreeks voor alle gebruikers wilt en meerdere architecturen en/of talen. In eerdere versies begint de inhoud te downloaden wanneer de gebruiker een beschikbare takenreeksimplementatie vanuit Software Center installeert. Deze vertraging voegt meer tijd voordat de installatie is gereed om te starten. Ook wordt alle inhoud waarnaar wordt verwezen in de takenreeks gedownload. Deze inhoud bevat het upgradepakket voor besturingssysteem voor alle talen en -architecturen. Als u elke upgradepakket is ongeveer drie GB groot is, wordt de totale inhoud groot is.

Vooraf cache-inhoud biedt u de optie voor het toestaan van de client alleen de inhoud te downloaden van toepassing als de implementatie wordt ontvangen. Daarom wanneer de gebruiker klikt op **installeren** in Software Center, de inhoud gereed is en de installatie begint snel omdat de inhoud op de lokale vaste schijf.

### <a name="to-configure-the-pre-cache-feature"></a>De cachefunctie vooraf configureren

1. Upgradepakketten voor specifieke architecturen en talen voor besturingssysteem maken. Geef de architectuur en taal op de **gegevensbron** tabblad van het pakket. Gebruik de decimale conversie voor de taal (bijvoorbeeld 1033 is het decimaalteken voor Engels en 0x0409 is hetzelfde als hexadecimaal). Zie voor meer informatie [een takenreeks maken om een besturingssysteem te upgraden](/sccm/osd/deploy-use/create-a-task-sequence-to-upgrade-an-operating-system).

    De architectuur en taal overeenkomen met waarden voorwaarden voor de stappen van de takenreeks wordt uitgevoerd om te bepalen of het upgradepakket voor besturingssysteem vooraf in cache opgeslagen.
1. Maak een takenreeks met voorwaardelijke stappen voor de verschillende talen en -architecturen. De volgende stap gebruikt bijvoorbeeld de Engelse versie:

    ![Eigenschappen van de pre-cache](../media/precacheproperties2.png)

    ![vooraf cacheopties](../media/precacheoptions2.png)  

3. De takenreeks implementeert. Configureer de volgende instellingen voor de functie vooraf cache:
    - Op de **algemene** tabblad **vooraf downloaden van inhoud voor deze takenreeks**.
    - Op de **implementatie-instellingen** tabblad, configureer de takenreeks met de **beschikbaar** voor **doel**.
    - Op de **planning** tabblad voor de **plannen wanneer deze implementatie beschikbaar zal zijn** instelt, kiest u de geselecteerde tijd. Start de client vooraf inhoud opslaan in cache op de beschikbare tijd van de implementatie. Wanneer een bepaalde client ontvangt dit beleid, de beschikbare tijd is verstreken, dus vooraf cache downloaden meteen gestart. Als de client dit beleid ontvangt, maar de beschikbare tijd in de toekomst is, start de client niet vooraf inhoud in cache opslaan, totdat de beschikbare tijd optreedt. 
    - Op de **distributiepunten** tabblad, configureert de **implementatieopties** instellingen. Als de inhoud niet vooraf in cache op een client opgeslagen is voordat een gebruiker de installatie wordt gestart, worden deze instellingen gebruikt.


### <a name="user-experience"></a>Gebruikerservaring
- Wanneer de client het implementatiebeleid ontvangt, wordt gestart om de inhoud vooraf in cache na de implementatie beschikbaar komen. Dit materiaal bevat alle pakketten waarnaar wordt verwezen en alleen het upgradepakket voor besturingssysteem die overeenkomt met de client op basis van de voorwaarden die zijn ingesteld in de takenreeks.
- Wanneer de implementatie beschikbaar wordt gesteld aan gebruikers, een melding weergegeven om gebruikers te informeren over de nieuwe implementatie en de takenreeks in Software Center zichtbaar is. De gebruiker kan gaat u naar Software Center en klikt u op **installeren** om de installatie te starten.
- Als de inhoud niet volledig vooraf in cache opgeslagen is wanneer de gebruiker de takenreeks installeert, wordt de client de instellingen die u opgeeft op de **Implementatieoptie** tabblad van de implementatie. 



## <a name="download-package-content-task-sequence-step"></a>Takenreeksstap pakketinhoud downloaden  
 De [pakketinhoud downloaden](../understand/task-sequence-steps.md#BKMK_DownloadPackageContent) stap kan worden gebruikt voordat de **besturingssysteem bijwerken** stap in de volgende scenario's:  

-   U gebruikt een enkele takenreeks voor upgraden voor x86- en x64 platforms. Voegt u twee **pakketinhoud downloaden** stappen in de **voorbereiden voor Upgrade** groep. Voorwaarden instellen op elke stap voor het detecteren van de clientarchitectuur. Deze voorwaarde zorgt ervoor dat de stap voor het downloaden van alleen het geschikte upgradepakket voor besturingssysteem. Configureer elke **Pakketinhoud downloaden**-stap zodanig dat dezelfde variabele wordt gebruikt, en gebruik de variabele voor het mediumpad in de stap **Besturingssysteem bijwerken**.  

-   Als u een geschikt stuurprogrammapakket wilt downloaden, gebruikt u twee **Pakketinhoud downloaden**-stappen op voorwaarde dat het juiste hardwaretype wordt gedetecteerd voor elk stuurprogrammapakket. Configureer elke **pakketinhoud downloaden** stap dezelfde variabele te gebruiken. Vervolgens gebruikt deze variabele voor de **tijdelijke inhoud** waarde in de sectie met stuurprogramma's op de **besturingssysteem bijwerken** stap.  

   > [!NOTE]
   > Wanneer er meer dan één pakket, wordt een numeriek achtervoegsel aan de variabelenaam in Configuration Manager toegevoegd. Bijvoorbeeld, als u een variabele van % mycontent % als aangepaste variabele opgeeft, is deze locatie waar alle inhoud waarnaar wordt verwezen door de client worden opgeslagen. Als u verwijst naar de variabele in een latere stap, zoals **besturingssysteem bijwerken**, de variabele met een numeriek achtervoegsel gebruikt. In dit voorbeeld, mycontent01% of % mycontent02%, waarbij het nummer overeenkomt met de volgorde waarin de **pakketinhoud downloaden** stap geeft een lijst van deze specifieke inhoud.

## <a name="optional-post-processing-task-sequence-steps"></a>Optionele na verwerking takenreeksstappen  
 Nadat u de takenreeks hebt gemaakt, wordt indien nodig aanvullende stappen toevoegen. Voorbeeld: toepassingen met bekende compatibiliteitsproblemen verwijderen of toevoegen na verwerking acties uit te voeren nadat de computer opnieuw is opgestart en de upgrade naar Windows 10 is geslaagd. Deze aanvullende stappen toevoegen in de groep na verwerking van de takenreeks.  

> [!NOTE]  
>  Omdat deze takenreeks niet lineair is, er bepaalde voorwaarden voor stappen die invloed kunnen hebben op de resultaten van de takenreeks, afhankelijk van of deze de clientcomputer met succes wordt bijgewerkt of dat er terugdraaien van de clientcomputer naar de oorspronkelijke besturingssysteemversie.  

## <a name="optional-rollback-task-sequence-steps"></a>Terugdraaien van de optionele takenreeksstappen  
 Wanneer er iets mis met het upgradeproces gaat nadat de computer opnieuw is opgestart, Windows Setup wordt de upgrade terugdraaien naar het vorige besturingssysteem. De takenreeks wordt vervolgens verder met de stappen in de groep terugdraaien. Nadat u de takenreeks hebt gemaakt, kunt u optionele stappen toevoegen aan de groep terugdraaien.  

## <a name="folder-and-files-removed-after-computer-restart"></a>Map en bestanden verwijderd nadat de computer opnieuw opstarten  
 Wanneer de takenreeks voltooid is, wordt de client niet de scripts na verwerking en terugdraaien verwijderd totdat de computer opnieuw is opgestart. Deze scriptbestanden bevatten geen gevoelige informatie.  
