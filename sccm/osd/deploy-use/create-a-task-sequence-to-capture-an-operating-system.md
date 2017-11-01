---
title: Maak een takenreeks voor het vastleggen van een besturingssysteem
titleSuffix: Configuration Manager
description: Een takenreeks voor samenstellen en vastleggen bouwt een referentiecomputer die specifieke stuurprogramma's en software-updates samen met het besturingssysteem kunt opnemen.
ms.custom: na
ms.date: 10/06/2016
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: configmgr-osd
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 25e4ac68-0e78-4bbe-b8fc-3898b372c4e8
caps.latest.revision: "19"
caps.handback.revision: "0"
author: Dougeby
ms.author: dougeby
manager: angrobe
ms.openlocfilehash: 98f9f44373b854b61714c21105a28b3240b4a7f7
ms.sourcegitcommit: c236214b2fcc13dae7bad96d7fb33f692868191d
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/12/2017
---
# <a name="create-a-task-sequence-to-capture-an-operating-system-in-system-center-configuration-manager"></a>Maak een takenreeks voor het vastleggen van een besturingssysteem in System Center Configuration Manager

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*

Wanneer u een takenreeks een besturingssysteem implementeren op een computer in System Center Configuration Manager gebruikt, wordt de installatiekopie die u in de takenreeks wordt uitgevoerd opgeeft door de computer geïnstalleerd. Als u de installatiekopie van het besturingssysteem zo wilt aanpassen dat hierin specifieke stuurprogramma's, toepassingen, software-updates enzovoort worden opgenomen, kunt u een takenreeks voor samenstellen en vastleggen gebruiken om een referentiecomputer te maken en vervolgens de installatiekopie van het besturingssysteem van deze referentiecomputer vastleggen. Als u al beschikt over een referentiecomputer die u kunt vastleggen, kunt u een aangepaste takenreeks maken om het besturingssysteem vast te leggen. In de volgende secties vindt u meer informatie over het vastleggen van een aangepast besturingssysteem.  

##  <a name="BKMK_BuildCaptureTS"></a> Een referentiecomputer bouwen en vastleggen met behulp van een takenreeks  
 De takenreeks voor samenstellen en vastleggen gepartitioneerd en indelingen van de referentiecomputer, het besturingssysteem, evenals de Configuration Manager-client, toepassingen en software-updates installeert en vervolgens het besturingssysteem van de referentiecomputer vastgelegd. De pakketten die zijn gekoppeld aan de takenreeks, zoals toepassingen, moeten beschikbaar zijn op distributiepunten voordat u de takenreeks voor bouwen en vastleggen maakt.  

###  <a name="BKMK_CreatePackages"></a> Implementaties van het besturingssysteem voorbereiden  
 Er zijn veel scenario's voor het implementeren van een besturingssysteem op computers in uw omgeving. In de meeste gevallen maakt u een takenreeks en selecteert u **Bestaand installatiekopiepakket installeren** in de Wizard Takenreeks maken om het besturingssysteem te installeren, gebruikersinstellingen te migreren, software-updates toe te passen en toepassingen te installeren. Voordat u een takenreeks maakt om een besturingssysteem te installeren, moet aan het volgende zijn voldaan:  

-   **Vereist**  

    -   De [opstartinstallatiekopie](../get-started/manage-boot-images.md) moet beschikbaar zijn in de Configuration Manager-console.  

    -   Een [besturingssysteeminstallatiekopie](../get-started/manage-operating-system-images.md) moet beschikbaar zijn in de Configuration Manager-console.  

-   **Vereist (indien gebruikt)**  

    -   [Stuurprogrammapakketten](../get-started/manage-drivers.md) die bevatten de benodigde Windows-stuurprogramma's voor de ondersteuning van hardware op de referentiecomputer moet beschikbaar zijn in de Configuration Manager-console. Zie voor meer informatie over de takenreeksstappen voor het beheren van stuurprogramma's, [takenreeksen gebruiken voor het installeren van apparaatstuurprogramma's](../get-started/manage-drivers.md#BKMK_TSDrivers).  

    -   [Software-updates](../../sum/get-started/synchronize-software-updates.md) moeten worden gesynchroniseerd in de Configuration Manager-console.  

    -   [Toepassingen](../../apps/deploy-use/create-applications.md) moet worden toegevoegd aan de Configuration Manager-console.  

###  <a name="BKMK_CreateBuildCaptureTS"></a> Een takenreeks voor bouwen en vastleggen maken  
 Voer de volgende procedure uit om met behulp van een takenreeks een referentiecomputer te bouwen en het besturingssysteem vast te leggen.  

#### <a name="to-create-a-task-sequence-that-builds-and-captures-an-operating-system-image"></a>Maken van een takenreeks die een installatiekopie van een besturingssysteem samenstelt en vastlegt  

1.  Klik in de Configuration Manager-console op **Softwarebibliotheek**.  

2.  Vouw **Besturingssystemen** uit in de werkruimte **Softwarebibliotheek**en klik op **Takenreeksen**.  

3.  Klik op **Takenreeks maken** in het tabblad **Start** , in de groep **Maken** om de wizard Takenreeks maken te starten.  

4.  Selecteer **Referentie-installatiekopie voor besturingssysteem samenstellen** op de pagina **Nieuwe takenreeks maken**.  

5.  Configureer op de pagina **Takenreeksinformatie** de volgende instellingen en klik op **Volgende**.  

    -   **Takenreeksnaam**: Geef een naam die de takenreeks identificeert.  

    -   **Beschrijving**: Geef een beschrijving van de taak die door de takenreeks, zoals een beschrijving van het besturingssysteem dat wordt gemaakt door de takenreeks wordt uitgevoerd.  

    -   **Opstartinstallatiekopie**: Geef de opstartinstallatiekopie die de installatiekopie van het besturingssysteem installeert.  

        > [!IMPORTANT]  
        >  De architectuur van de opstartinstallatiekopie moet compatibel zijn met de hardware-architectuur van de doelcomputer.  

6.  Geef op de pagina **Windows installeren** de volgende opties op en klik op **Volgende**.  

    -   **Installatiekopiepakket**: Geef het installatiekopiepakket van besturingssysteem, waarin de bestanden die nodig zijn voor het besturingssysteem installeren.  

    -   **Installatiekopie-index**: Geef het besturingssysteem te installeren. Als de installatiekopie van het besturingssysteem meerdere versies bevat, selecteert u de versie die u wilt installeren.  

    -   **Productcode**: Geef de productcode voor het Windows-besturingssysteem te installeren. U kunt gecodeerde volumelicentiesleutels en standaardproductsleutels opgeven. Als u een niet-gecodeerde productcode gebruikt, moet elke groep van 5 tekens gescheiden worden door een streepje (-). Bijvoorbeeld: *XXXXX-XXXXX-XXXXX-XXXXX-XXXXX*  

    -   **Serverlicentiemodus**: Geef op of de serverlicentie **Per seat**, **Per server**, of dat er geen licentie is opgegeven. Als de serverlicentie **Per server**is, geef dan ook het maximum aantal serververbindingen op.  

    -   Geef op hoe het Administrator-account moet worden afgehandeld dat wordt gebruikt wanneer het besturingssysteem wordt geïmplementeerd.  

        -   **Willekeurig wachtwoord genereren voor lokale beheerder en het account uitschakelen op alle ondersteunde platforms**: Geef op of Configuration Manager maken van een willekeurig wachtwoord voor het lokale beheerdersaccount en het account uitschakelen wanneer het besturingssysteem wordt geïmplementeerd.  

        -   **Het account inschakelen en geef het lokale beheerderswachtwoord**: Geef op of hetzelfde wachtwoord wordt gebruikt voor het lokale beheerdersaccount op alle computers waarop het besturingssysteem wordt geïmplementeerd.  

7.  Geef op de pagina **Netwerk configureren** de volgende opties op en klik op **Volgende**.  

    -   **Lid worden van een werkgroep**: Geef op of de doelcomputer wordt toegevoegd aan een werkgroep wanneer het besturingssysteem wordt geïmplementeerd.  

    -   **Lid worden van een domein**: Geef op of de doelcomputer aan een domein toevoegen wanneer het besturingssysteem wordt geïmplementeerd. Geef in **Domein**de naam op van het domein.  

        > [!IMPORTANT]  
        >  U kunt bladeren om domeinen te zoeken in het lokaal forest, maar u moet de domeinnaam opgeven voor een extern forest.  

         U kunt ook een organisatie-eenheid (OE) opgeven. Dit is een optionele instelling die de LDAP X.500-DN-naam van de OE specificeert waarin het computeraccount moet worden aangemaakt als het nog niet bestaat.  

    -   **Account**: Geef de gebruikersnaam en wachtwoord voor het account met machtigingen die aan het opgegeven domein. Bijvoorbeeld: *domein\gebruiker* of *%variabele%*.  

        > [!IMPORTANT]  
        >  U moet de toepasselijke domeinreferenties invoeren als u van plan bent om de domeininstellingen of de werkgroepinstellingen te migreren.  

8.  Op de **Configuration Manager installeren** pagina, geeft u de Configuration Manager-clientpakket waarin de bronbestanden voor de Configuration Manager-client installeren, voeg eventuele aanvullende eigenschappen voor de client installeren en klik vervolgens op **volgende**.  

     Zie voor meer informatie over de eigenschappen die kunnen worden gebruikt voor het installeren van een client [over clientinstallatie-eigenschappen](../../core/clients/deploy/about-client-installation-properties.md).  

9. Geef op de pagina **Inclusief updates** op of de vereiste software-updates, alle software-updates of geen software-updates moeten worden geïnstalleerd. Klik vervolgens op **Volgende**. Als u opgeeft om softwareupdates te installeren, installeert Configuration Manager alleen die softwareupdates die zijn gericht op de verzamelingen waar de doelcomputer lid van is.  

10. Geef op de pagina **Toepassingen installeren** de toepassingen op die moeten worden geïnstalleerd op de doelcomputer en klik op **Volgende**. Als u meerdere toepassingen opgeeft, kunt u opgeven dat de takenreeks wordt voortgezet als de installatie van een bepaalde toepassing mislukt.  

11. Geef op de pagina **Systeemvoorbereiding** de volgende opties op en klik op **Volgende**.  

    -   **Pakket**: Geef de Configuration Manager-pakket met de juiste versie van Sysprep te gebruiken om vast te leggen van de instellingen van de referentiecomputer.  

         Als u Windows Vista of hoger als besturingssysteem gebruikt, is Sysprep automatisch geïnstalleerd op de computer en hoeft u geen pakket op te geven.  

12. Configureer de volgende instellingen voor de installatiekopie van het besturingssysteem op de pagina **Eigenschappen van de installatiekopie** en klik vervolgens op **Volgende**.  

    -   **Gemaakt door**: Geef de naam van de gebruiker die de installatiekopie van het besturingssysteem gemaakt.  

    -   **Versie**: Geef een gebruiker gedefinieerd versienummer dat is gekoppeld aan de installatiekopie van het besturingssysteem.  

    -   **Beschrijving**: Geef een door de gebruiker gedefinieerde beschrijving van de computer besturingssysteeminstallatiekopie.  

13. Geef op de pagina **Installatiekopie vastleggen** de volgende opties op en klik op **Volgende**.  

    -   **Pad**: Geef een gedeelde netwerkmap waarin de uitvoer. WIM-bestand wordt opgeslagen. Dit bestand bevat de installatiekopie van het besturingssysteem dat is gebaseerd op de instellingen die u opgeeft door deze wizard te gebruiken. Als u een map opgeeft die een bestaand WIM-bestand bevat, wordt het bestaande bestand overschreven.  

    -   **Account**: Geef de Windows-account met machtigingen voor de netwerkshare waarop de installatiekopie is opgeslagen.  

14. Voltooi de wizard.  

15. Selecteer, om deze bijkomende stappen toe te voegen aan de takenreeks, de takenreeks die u hebt gecreëerd en klik op **Bewerken**. Zie voor meer informatie over het bewerken van een takenreeks [een takenreeks bewerken](manage-task-sequences-to-automate-tasks.md#BKMK_ModifyTaskSequence).  

 Implementeer op een van de volgende manieren de takenreeks op een referentiecomputer:  

-   Als de referentiecomputer een Configuration Manager-client is, kunt u de build te implementeren en vast te leggen takenreeks voor de verzameling die de referentiecomputer bevat. Zie voor meer informatie over het implementeren van de besturingssysteemkopie [een takenreeks maken om een besturingssysteem te installeren](create-a-task-sequence-to-install-an-operating-system.md).  

    > [!NOTE]  
    >  Indien de takenreeks een stap schijfpartitionering heeft, selecteer dan niet de optie **Programma downloaden** wanneer u de takenreeks implementeert.  

-   Als de referentiecomputer geen Configuration Manager-client is of als u wilt dat de takenreeks handmatig uitvoeren op de referentiecomputer uitvoeren de **maken Wizard Takenreeksmedia** om opstartbare media te maken. Zie voor meer informatie over het maken van opstartbare media [opstartbare media maakt](create-bootable-media.md).  

##  <a name="BKMK_CaptureExistingRefComputer"></a> Een installatiekopie van een besturingssysteem vastleggen vanaf een bestaande referentiecomputer  
 Als u al een referentiecomputer hebt die gereed is voor vastleggen, kunt u een takenreeks maken waarmee het besturingssysteem van de referentiecomputer wordt vastgelegd. U gebruikt de takenreeksstap **Besturingssysteeminstallatiekopie vastleggen** om een of meer installatiekopieën van een referentiecomputer vast te leggen en op te slaan in een installatiekopiebestand (.wim) op de opgegeven netwerkshare. De referentiecomputer wordt in Windows PE gestart met behulp van een opstartinstallatiekopie en elke harde schijf op de referentiecomputer wordt vastgelegd als een afzonderlijke installatiekopie binnen het .wim-bestand. Als de computer waarnaar wordt verwezen meerdere stations heeft, bevat het resulterende .wim-bestand een afzonderlijke installatiekopie voor elk station. Alleen volumes die zijn geformatteerd als NTFS of FAT32 worden vastgelegd. Volumes met andere formatteringen en USB-volumes worden overgeslagen.  

 Voer de volgende procedure uit om een installatiekopie vanaf een bestaande referentiecomputer vast te leggen.  

#### <a name="to-capture-an-operating-system-from-an-existing-reference-computer"></a>Een installatiekopie vastleggen vanaf een bestaande referentiecomputer  

1.  Klik in de Configuration Manager-console op **Softwarebibliotheek**.  

2.  Vouw **Besturingssystemen** uit in de werkruimte **Softwarebibliotheek**en klik op **Takenreeksen**.  

3.  Klik op **Takenreeks maken** in het tabblad **Start** , in de groep **Maken** om de wizard Takenreeks maken te starten.  

4.  Selecteer **Nieuwe aangepaste takenreeks maken** op de pagina **Nieuwe takenreeks maken**.  

5.  Geef op de pagina **Takenreeksinformatie** een naam en een beschrijving op voor de takenreeks.  

6.  Geef een opstartinstallatiekopie op voor de takenreeks. Deze opstartinstallatiekopie wordt gebruikt om de referentiecomputer te starten met Windows PE.  Zie voor meer informatie [opstartinstallatiekopieën beheren](../get-started/manage-boot-images.md).  

7.  Voltooi de wizard.  

8.  Selecteer de aangepaste takenreeks in **Takenreeksen**en klik vervolgens op het tabblad **Start** in de groep **Takenreeks** op **Bewerken** om de takenreekseditor te openen.  

9. Deze stap alleen gebruiken als Configuration Manager-client is geïnstalleerd op de referentiecomputer.  

     Klik op **toevoegen**, klikt u op **installatiekopieën**, en klik vervolgens op [ConfigMgr-Client voorbereiden voor vastleggen](../understand/task-sequence-steps.md#BKMK_PrepareConfigMgrClientforCapture). Deze takenreeksstap neemt de Configuration Manager-client op de referentiecomputer en voorbereid voor vastleggen als onderdeel van de installatiekopieprocedure.  

10. Klik op **toevoegen**, klikt u op **installatiekopieën**, en klik vervolgens op [Windows voorbereiden voor vastleggen](../understand/task-sequence-steps.md#BKMK_PrepareWindowsforCapture). Met deze takenreeksactie wordt Sysprep uitgevoerd en wordt vervolgens de computer opnieuw opgestart naar de opstartinstallatiekopie voor Windows PE die is opgegeven voor de takenreeks. Deze actie kan alleen worden voltooid als de referentiecomputer niet lid is van een domein.  

11. Klik op **toevoegen**, klikt u op **installatiekopieën**, en klik vervolgens op [Besturingssysteeminstallatiekopie vastleggen](../understand/task-sequence-steps.md#BKMK_CaptureOperatingSystemImage).  Deze takenreeksstap kan alleen vanuit Windows PE worden uitgevoerd om de vaste schijven op de referentiecomputer vast te leggen. Configureer de volgende instellingen voor de takenreeksstap.  

    -   **Naam** en **beschrijving**: U kunt desgewenst de naam van de takenreeksstap wijzigen en geef een beschrijving op.  

    -   **Bestemming**: Geef een gedeelde netwerkmap waarin de uitvoer. WIM-bestand wordt opgeslagen. Dit bestand bevat de installatiekopie van het besturingssysteem dat is gebaseerd op de instellingen die u opgeeft door deze wizard te gebruiken. Als u een map opgeeft die een bestaand WIM-bestand bevat, wordt het bestaande bestand overschreven.  

    -   **Beschrijving**, **versie**, en **gemaakt door**: Geef desgewenst details op over de installatiekopie die u vastlegt.  

    -   **Account besturingssysteeminstallatiekopie vastleggen**: Geef de Windows-account met machtigingen voor het netwerk die u hebt opgegeven. Klik op **Instellen** om de naam van het Windows-account op te geven.  

     Klik op **OK** om de takenreekseditor te sluiten.  

 Implementeer op een van de volgende manieren de takenreeks op een referentiecomputer:  

-   Als de referentiecomputer een Configuration Manager-client is, kunt u de takenreeks implementeren voor de verzameling die de referentiecomputer bevat. Zie voor meer informatie over het implementeren van de besturingssysteemkopie [een takenreeks maken om een besturingssysteem te installeren](create-a-task-sequence-to-install-an-operating-system.md).  

-   Als de referentiecomputer geen Configuration Manager-client is of als u wilt dat de takenreeks handmatig uitvoeren op de referentiecomputer uitvoeren de **maken Wizard Takenreeksmedia** om opstartbare media te maken. Zie voor meer informatie over het maken van opstartbare media [opstartbare media maakt](create-bootable-media.md).  

##  <a name="BKMK_BuildandCaptureTSExample"></a> Voorbeeld van een takenreeks om een installatiekopie van een besturingssysteem te bouwen en vast te leggen  
 Gebruik de volgende tabel als richtlijn bij het maken van een takenreeks die een installatiekopie van een besturingssysteem bouwt en vastlegt. De tabel helpt u om de algemene volgorde te bepalen voor de takenreeksstappen en deze in te delen en te structureren in logische groepen. De takenreeks die u maakt, kan afwijken van dit voorbeeld en kan meer of minder takenreeksstappen en groepen bevatten.  

> [!IMPORTANT]  
>  Gebruik altijd de wizard Takenreeks maken om een takenreeks van dit type te maken.  

 Als u **Nieuwe takenreeks** gebruikt om deze nieuwe takenreeks te maken, zijn enkele van de namen van de takenreeksstappen anders dan wanneer u ze handmatig toevoegt aan een bestaande takenreeks. In de volgende tabel worden de verschillen in naamgeving vermeld:  

|Nieuwe naam van de takenreeksstap in de wizard Takenreeksstap|Gelijkwaardige naam van de stap in de Takenreekseditor|  
|------------------------------------------------------|-----------------------------------------------|  
|Opnieuw opstarten in Windows PE|Opnieuw opstarten in Windows PE of harde schijf|  
|Schijf 0 partitioneren|Schijf formatteren en partitioneren|  
|Apparaatstuurprogramma's toepassen|Stuurprogramma's automatisch toepassen|  
|Updates installeren|Software-updates installeren|  
|Lid worden van werkgroep|Lid worden van domein of werkgroep|  
|ConfigMgr-client voorbereiden|Prepare ConfigMgr Client for Capture|  
|Besturingssysteem voorbereiden|Prepare Windows for Capture|  
|Referentiecomputer vastleggen|Besturingssysteeminstallatiekopie vastleggen|  

|Takenreeksgroep/-stap|Verwijzing|  
|-------------------------------|---------------|  
|Referentiecomputer bouwen - **(nieuwe takenreeksgroep)**|Een takenreeksgroep maken. In een takenreeksgroep houdt u vergelijkbare takenreeksstappen bij elkaar voor betere ordening en foutcontrole.<br /><br /> Deze groep bevat de acties die nodig zijn om een referentiecomputer te bouwen.|  
|Opnieuw opstarten in Windows PE|In deze takenreeksstap geeft u de opties op voor het opnieuw opstarten van de doelcomputer. Bij deze stap wordt een bericht voor de gebruiker weergegeven dat de computer opnieuw wordt opgestart zodat de installatie kan doorgaan.<br /><br /> Deze stap maakt gebruik van de alleen-lezen takenreeksvariabele **_SMSTSInWinPE** . Als de gekoppelde waarde gelijk is aan **false** , wordt de takenreeksstap voortgezet.|  
|Schijf 0 partitioneren|Met deze takenreeksstap geeft u de acties op die nodig zijn om de harde schijf op de doelcomputer te formatteren. Het standaardnummer van de schijf is **0**.<br /><br /> Deze stap maakt gebruik van de alleen-lezen takenreeksvariabele **_SMSTSClientCache** . Deze stap wordt uitgevoerd als de Configuration Manager-clientcache niet bestaat.|  
|Besturingssysteem toepassen|Met deze takenreeksstap installeert u de opgegeven installatiekopie van een besturingssysteem op de doelcomputer. Deze stap geldt voor alle volume afbeeldingen in het WIM-bestand naar het overeenkomstige sequentiële schijfvolume op de doelcomputer na het eerste verwijderen van alle bestanden op dat volume (met uitzondering van Configuration Manager-specifieke besturingsbestanden).|  
|Windows-instellingen toepassen|Met deze takenreeksstap configureert u de configuratiegegevens voor de Windows-instellingen voor de doelcomputer.|  
|Netwerkinstellingen toepassen|Met deze takenreeks geeft u de gegevens voor netwerk- of werkgroepconfiguratie op voor de doelcomputer.|  
|Apparaatstuurprogramma's toepassen|Met deze takenreeksstap zoekt en installeert u stuurprogramma's als onderdeel van de implementatie van een besturingssysteem. U kunt Windows Setup toestaan om in alle bestaande categorieën stuurprogramma's te zoeken door **stuurprogramma's uit alle categorieën overwegen** te selecteren of de stuurprogrammacategorieën waarin Windows Setup zoekt beperken door **Zoeken naar passende stuurprogramma's beperken tot bepaalde categorieën**te selecteren.<br /><br /> Deze stap maakt gebruik van de alleen-lezen takenreeksvariabele **_SMSTSMediaType** . Als de gekoppelde waarde niet gelijk is aan **FullMedia** , wordt deze takenreeksstap uitgevoerd.|  
|Windows en ConfigMgr installeren|Gebruik deze takenreeksstap om de Configuration Manager-clientsoftware te installeren. Configuration Manager installeert en registreert de GUID van de Configuration Manager-client. U kunt de vereiste installatieparameters toewijzen in het venster **Installatie-eigenschappen** .|  
|Updates installeren|Met deze takenreeksstap geeft u op hoe software-updates worden geïnstalleerd op de doelcomputer. De doelcomputer wordt pas geëvalueerd voor toepasselijke software-updates als deze takenreeksstap wordt uitgevoerd. Op dat moment wordt de doelcomputer geëvalueerd voor software-updates is vergelijkbaar met een andere beheerd door Configuration Manager-client.<br /><br /> Deze stap maakt gebruik van de alleen-lezen takenreeksvariabele **_SMSTSMediaType** . Als de gekoppelde waarde niet gelijk is aan **FullMedia** , wordt deze takenreeksstap uitgevoerd.|  
|Referentiecomputer vastleggen - **(nieuwe takenreeksgroep)**|Maak een nieuwe takenreeksgroep. Deze groep bevat de benodigde stappen om een referentiecomputer voor te bereiden en vast te leggen.|  
|Lid worden van werkgroep|Met deze takenreeksstap geeft u de gegevens op die nodig zijn om de doelcomputer lid te maken van een werkgroep.|  
|Prepare ConfigMgr Client for Capture|Deze stap gebruiken om de Configuration Manager-client op de referentiecomputer en voorbereid voor vastleggen als onderdeel van de installatiekopieprocedure|  
|Besturingssysteem voorbereiden|Met deze takenreeksstap geeft u de Sysprep-opties op die moeten worden gebruikt bij het vastleggen van Windows-instellingen van de referentiecomputer. In deze takenreeksstap wordt Sysprep uitgevoerd en wordt vervolgens de computer opnieuw opgestart naar de opstartinstallatiekopie voor Windows PE die is opgegeven voor de takenreeks.|  
|Besturingssysteeminstallatiekopie vastleggen|Met deze takenreeksstap voert u een specifieke bestaande netwerkshare en het WIM-bestand in die moeten worden gebruikt bij het opslaan van de installatiekopie. Deze locatie wordt als bronlocatie van het pakket gebruikt als een installatiekopiepakket van een besturingssysteem wordt toegevoegd met de wizard **Installatiekopiepakket van besturingssysteem toevoegen**.|  

 Sla, nadat u een installatiekopie hebt gemaakt van een referentiecomputer, geen andere installatiekopie op van het besturingssysteem, omdat de registervermeldingen worden gemaakt tijdens de initiële configuratie. Creëer een nieuwe referentiecomputer telkens u een installatiekopie van het besturingssysteem maakt. Als u van plan bent om dezelfde referentiecomputer te maken van installatiekopieën van besturingssystemen voor toekomstige, Configuration Manager-client eerst verwijderen en opnieuw installeren van Configuration Manager-client.  

## <a name="next-steps"></a>Volgende stappen  
[Methoden om enterprise-besturingssystemen te implementeren](methods-to-deploy-enterprise-operating-systems.md)
