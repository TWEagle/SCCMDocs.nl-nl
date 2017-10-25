---
title: Maak een takenreeks om een besturingssysteem te installeren | Microsoft Docs
description: Gebruik takenreeksen in System Center Configuration Manager automatisch te installeren installatiekopie van een besturingssysteem en andere inhoud op een doelcomputer.
ms.custom: na
ms.date: 10/06/2016
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: configmgr-osd
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 217c8a0e-5112-420e-a325-2a6d75326290
caps.latest.revision: "13"
author: Dougeby
ms.author: dougeby
manager: angrobe
ms.openlocfilehash: 41aa6cf69a746f0ab67d804f1ee0c70db05d65ee
ms.sourcegitcommit: 51fc48fb023f1e8d995c6c4eacfda7dbec4d0b2f
ms.translationtype: HT
ms.contentlocale: nl-NL
ms.lasthandoff: 08/07/2017
---
# <a name="create-a-task-sequence-to-install-an-operating-system-in-system-center-configuration-manager"></a>Een takenreeks maken voor het installeren van een besturingssysteem in System Center Configuration Manager

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*

Gebruik takenreeksen in System Center Configuration Manager automatisch de installatiekopie van een besturingssysteem installeren op een doelcomputer. U maakt een takenreeks die verwijst naar de opstartinstallatiekopie die wordt gebruikt om de doelcomputer op te starten, de installatiekopie van het besturingssysteem dat u wilt installeren op de doelcomputer en andere bijkomende inhoud, zoals andere toepassingen of software-updates die u wilt installeren. Vervolgens implementeert u de takenreeks voor de verzameling die de doelcomputer bevat.  

##  <a name="BKMK_InstallOS"></a> Een takenreeks maken voor het installeren van een besturingssysteem  
 Er zijn veel scenario's voor het implementeren van een besturingssysteem op computers in uw omgeving. In de meeste gevallen maakt u een takenreeks en selecteert u **Bestaand installatiekopiepakket installeren** in de Wizard Takenreeks maken om het besturingssysteem te installeren, gebruikersinstellingen te migreren, software-updates toe te passen en toepassingen te installeren. Voordat u een takenreeks maakt om een besturingssysteem te installeren, moet aan het volgende zijn voldaan:   

-   **Vereist**  

    -   De [opstartinstallatiekopie](../get-started/manage-boot-images.md) moet beschikbaar zijn in de Configuration Manager-console.  

    -   Een [besturingssysteeminstallatiekopie](../get-started/manage-operating-system-images.md) moet beschikbaar zijn in de Configuration Manager-console.  

-   **Vereist (indien gebruikt)**  

    -   [Software-updates](../../sum/get-started/synchronize-software-updates.md) moeten worden gesynchroniseerd in de Configuration Manager-console.  

    -   [Toepassingen](../../apps/deploy-use/create-applications.md) moet worden toegevoegd aan de Configuration Manager-console.  

#### <a name="to-create-a-task-sequence-that-installs-an-operating-system"></a>Een takenreeks maken waarmee een besturingssysteem wordt geïnstalleerd  

1.  Klik in de Configuration Manager-console op **Softwarebibliotheek**.  

2.  Vouw **Besturingssystemen** uit in de werkruimte **Softwarebibliotheek**en klik op **Takenreeksen**.  

3.  Klik op **Takenreeks maken** in het tabblad **Start** , in de groep **Maken** om de wizard Takenreeks maken te starten.  

4.  Klik op **Bestaand installatiekopiepakket installeren** op de pagina **Nieuwe takenreeks maken**en klik vervolgens op **Volgende**.  

5.  Configureer op de pagina **Takenreeksinformatie** de volgende instellingen en klik op **Volgende**.  

    -   **Takenreeksnaam**: Geef een naam die de takenreeks identificeert.  

    -   **Beschrijving**: Geef een beschrijving van de taak die door de takenreeks wordt uitgevoerd.  

    -   **Opstartinstallatiekopie**: Geef de opstartinstallatiekopie die het besturingssysteem wordt geïnstalleerd op de doelcomputer. De opstartinstallatiekopie bevat een versie van Windows PE waarmee het besturingssysteem en eventuele benodigde apparaatstuurprogramma's worden geïnstalleerd. Zie voor informatie [opstartinstallatiekopieën beheren](../get-started/manage-boot-images.md).  

        > [!IMPORTANT]  
        >  De architectuur van de opstartinstallatiekopie moet compatibel zijn met de hardware-architectuur van de doelcomputer.  

6.  Geef op de pagina **Windows installeren** de volgende opties op en klik op **Volgende**.  

    -   **Installatiekopiepakket**: Geef het pakket met de installatiekopie van het besturingssysteem te installeren. Zie voor meer informatie [installatiekopieën van besturingssystemen beheren](../get-started/manage-operating-system-images.md).  

    -   **Afbeelding**: Als het installatiekopiepakket van het besturingssysteem meerdere installatiekopieën bevat, geeft u de index van de installatiekopie van het besturingssysteem te installeren.  

    -   **Partitioneren en formatteren van de doelcomputer die het besturingssysteem installeert**: Geef op of u wilt dat de takenreeks voor het partitioneren en formatteren van de doelcomputer voordat het besturingssysteem is geïnstalleerd.  

    -   **Productcode**: Geef de productcode voor het Windows-besturingssysteem te installeren. U kunt gecodeerde volumelicentiesleutels en standaardproductsleutels opgeven. Als u een niet-gecodeerde productcode gebruikt, moet elke groep van 5 tekens gescheiden worden door een streepje (-). Bijvoorbeeld: *XXXXX-XXXXX-XXXXX-XXXXX-XXXXX*  

    -   **Serverlicentiemodus**: Geef op of de serverlicentie **Per seat**, **Per server**, of dat er geen licentie is opgegeven. Als de serverlicentie **Per server**is, geef dan ook het maximum aantal serververbindingen op.  

    -   Geef op hoe het beheerdersaccount moet worden afgehandeld dat wordt gebruikt wanneer de installatiekopie van het besturingssysteem wordt geïmplementeerd.  

        -   **Lokale beheerdersaccount uitschakelen**: Geef op of het lokale beheerdersaccount wordt uitgeschakeld wanneer de installatiekopie van het besturingssysteem is geïmplementeerd.  

        -   **Gebruik altijd hetzelfde beheerderswachtwoord**: Geef op of hetzelfde wachtwoord wordt gebruikt voor het lokale beheerdersaccount op alle computers waarop de installatiekopie van het besturingssysteem wordt geïmplementeerd.  

7.  Geef op de pagina **Netwerk configureren** de volgende opties op en klik op **Volgende**.  

    -   **Lid worden van een werkgroep**: Geef op of de doelcomputer wordt toegevoegd aan een werkgroep.  

    -   **Lid worden van een domein**: Geef op of de doelcomputer aan een domein toevoegen. Geef in **Domein**de naam op van het domein.  

        > [!IMPORTANT]  
        >  U kunt bladeren om domeinen te zoeken in het lokaal forest, maar u moet de domeinnaam opgeven voor een extern forest.  

         U kunt ook een organisatie-eenheid (OE) opgeven. Dit is een optionele instelling die de LDAP X.500-DN-naam van de OE specificeert waarin het computeraccount moet worden aangemaakt als het nog niet bestaat.  

    -   **Account**: Geef de gebruikersnaam en wachtwoord voor het account met machtigingen die aan het opgegeven domein. Bijvoorbeeld: *domein\gebruiker* of *%variabele%*.  

        > [!IMPORTANT]  
        >  U moet de toepasselijke domeinreferenties invoeren als u van plan bent om de domeininstellingen of de werkgroepinstellingen te migreren.  

8.  Op de **Configuration Manager installeren** pagina, geeft u het clientpakket voor Configuration Manager om te installeren op de doelcomputer en klik vervolgens op **volgende**.  

9. Geef op de pagina **Statusmigratie** de volgende informatie op en klik vervolgens op **Volgende**.  

    -   **Gebruikersinstellingen vastleggen**: Geef op of de takenreeks de gebruikersstatus vastlegt. Zie voor meer informatie over het vastleggen en herstellen van de gebruikersstatus [Gebruikersstatus beheren](../get-started/manage-user-state.md).  

    -   **Netwerkinstellingen vastleggen**: Geef op of de takenreeks de netwerkinstellingen van de doelcomputer vastgelegd. U kunt, naast de netwerkadapterinstellingen, het lidmaatschap van het domein of de werkgroep vastleggen.  

    -   **Microsoft Windows-instellingen vastleggen**:  Geef op of de takenreeks Windows-instellingen van de doelcomputer vastlegt voordat de installatiekopie van het besturingssysteem is geïnstalleerd. U kunt de computernaam, de naam van de geregistreerde gebruiker en organisatie en de instellingen van de tijdzone vastleggen.  

10. Geef op de pagina **Inclusief updates** op of de vereiste software-updates, alle software-updates of geen software-updates moeten worden geïnstalleerd. Klik vervolgens op **Volgende**. Als u opgeeft om softwareupdates te installeren, installeert Configuration Manager alleen die softwareupdates die zijn gericht op de verzamelingen waar de doelcomputer lid van is.  

11. Geef op de pagina **Toepassingen installeren** de toepassingen op die moeten worden geïnstalleerd op de doelcomputer en klik op **Volgende**. Als u meerdere toepassingen opgeeft, kunt u opgeven dat de takenreeks wordt voortgezet als de installatie van een bepaalde toepassing mislukt.  

12. Voltooi de wizard.  

 U kunt nu de takenreeks implementeren voor een verzameling van computers.  Zie [Een takenreeks implementeren](manage-task-sequences-to-automate-tasks.md#BKMK_DeployTS) voor meer informatie.  

##  <a name="BKMK_InstallExistingOSImageTSExample"></a> Voorbeeld van een takenreeks voor het installeren van een bestaande installatiekopie van een besturingssysteem  
 Gebruik de volgende tabel als richtlijn bij het maken van een takenreeks voor de implementatie van een besturingssysteem met een bestaande installatiekopie van het besturingssysteem. De tabel helpt u om de algemene volgorde te bepalen voor de takenreeksstappen en deze in te delen en te structureren in logische groepen. De takenreeks die u maakt, kan afwijken van dit voorbeeld en kan meer of minder takenreeksstappen en groepen bevatten.  

> [!IMPORTANT]  
>  Gebruik altijd de wizard Takenreeks maken om deze takenreeks te maken.  

 Als u de wizard Nieuwe takenreeks maken gebruikt om deze nieuwe takenreeks te maken, zijn enkele van de namen van de takenreeksstappen anders dan wanneer u ze handmatig toevoegt aan een bestaande takenreeks. In de volgende tabel worden de verschillen in naamgeving vermeld:  

|Takenreeksstapnamen in de wizard Takenreeksstap maken|Gelijkwaardige naam van de stap in de Takenreekseditor|  
|---------------------------------------------------------|-----------------------------------------------|  
|Opslag gebruikersstatus aanvragen|Statusopslag opvragen|  
|Gebruikersbestanden en -instellingen vastleggen|Gebruikersstatus vastleggen|  
|Opslag gebruikersstatus vrijgeven|Statusopslag vrijgeven|  
|Opnieuw opstarten in Windows PE|Opnieuw opstarten in Windows PE of harde schijf|  
|Schijf 0 partitioneren|Schijf formatteren en partitioneren|  
|Gebruikersbestanden en -instellingen herstellen|Gebruikersstatus herstellen|  

|Takenreeksgroep of -stap|Beschrijving|  
|---------------------------------|-----------------|  
|Bestanden en instellingen - vastleggen **(nieuwe Takenreeksgroep)**|Een takenreeksgroep maken. In een takenreeksgroep houdt u vergelijkbare takenreeksstappen bij elkaar voor betere ordening en foutcontrole.<br /><br /> Deze groep bevat de stappen die nodig zijn voor het vastleggen van bestanden en instellingen van het besturingssysteem van een referentiecomputer.|  
|Windows-instellingen vastleggen|Gebruik deze takenreeksstap om de Microsoft Windows-instellingen op de referentiecomputer te identificeren die moeten worden vastgelegd. U kunt de computernaam, gebruikers- en organisatiegegevens en de instellingen voor de tijdzone vastleggen.|  
|Netwerkinstellingen vastleggen|Gebruik deze takenreeksstap om de netwerkinstellingen van de referentiecomputer vast te leggen. U kunt naast de netwerkadapterinstellingen het lidmaatschap van de referentiecomputer van een domein of werkgroep vastleggen.|  
|Vastleggen van gebruikersbestanden en -instellingen - **(nieuwe Takenreekssubgroep)**|Maak een takenreeksgroep binnen een takenreeksgroep. Deze subgroep bevat de stappen die nodig zijn voor het vastleggen van gegevens van de gebruikersstatus. Deze subgroep houdt op een soortgelijke manier als de eerste groep die u hebt toegevoegd, vergelijkbare takenreeksstappen bij elkaar voor een betere ordening en foutcontrole.|  
|Opslag gebruikersstatus aanvragen|Gebruik deze takenreeksstap om toegang aan te vragen tot een statusmigratiepunt waar de gebruikersgegevens worden opgeslagen. U kunt deze takenreeksstap configureren om informatie over de gebruikersstatus vast te leggen of te herstellen.|  
|Gebruikersbestanden en -instellingen vastleggen|Gebruik deze takenreeksstap User State Migration Tool (USMT) om vast te leggen van de gebruikersstatus en instellingen van de referentiecomputer die de takenreeks die is gekoppeld aan deze taakstap ontvangt. U kunt de standaardopties vastleggen of configureren welke opties u wilt vastleggen.|  
|Opslag gebruikersstatus vrijgeven|Gebruik deze takenreeksstap om het statusmigratiepunt te informeren dat de vastleg- of herstelactie is voltooid.|  
|Besturingssysteem installeren - **(nieuwe Takenreeksgroep)**|Maak een nieuwe takenreekssubgroep. Deze subgroep bevat de stappen die nodig zijn voor het installeren en configureren van de Windows PE-omgeving.|  
|Opnieuw opstarten in Windows PE|In deze takenreeksstap geeft u de opties op voor het opnieuw opstarten van de doelcomputer die deze takenreeks ontvangt. Bij deze stap wordt een bericht voor de gebruiker weergegeven dat de computer opnieuw wordt opgestart zodat de installatie kan doorgaan.<br /><br /> Deze stap maakt gebruik van de alleen-lezen takenreeksvariabele **_SMSTSInWinPE** . Als de gekoppelde waarde gelijk is aan **false** , wordt de takenreeksstap voortgezet.|  
|Schijf 0 partitioneren|Met deze takenreeksstap geeft u de acties op die nodig zijn om de harde schijf op de doelcomputer te formatteren. Het standaardnummer van de schijf is **0**.<br /><br /> Deze stap maakt gebruik van de alleen-lezen takenreeksvariabele **_SMSTSClientCache** . Deze stap wordt uitgevoerd als de Configuration Manager-clientcache niet bestaat.|  
|Besturingssysteem toepassen|Met deze takenreeksstap installeert u de installatiekopie van het besturingssysteem op de doelcomputer. Deze stap geldt voor alle volume afbeeldingen in het WIM-bestand naar het overeenkomstige sequentiële schijfvolume op de doelcomputer na het eerste verwijderen van alle bestanden op dat volume (met uitzondering van Configuration Manager-specifieke besturingsbestanden). U kunt een **sysprep** -antwoordbestand opgeven en ook configureren welke schijfpartitie voor de installatie moet worden gebruikt.|  
|Windows-instellingen toepassen|Met deze takenreeksstap configureert u de configuratiegegevens voor de Windows-instellingen voor de doelcomputer. De Windows-instellingen die u kunt toepassen zijn gebruikers- en organisatiegegevens, product- of licentiecodegegevens, de tijdzone en het wachtwoord voor de lokale beheerder.|  
|Netwerkinstellingen toepassen|Met deze takenreeks geeft u de gegevens voor netwerk- of werkgroepconfiguratie op voor de doelcomputer. U kunt ook opgeven of de computer een DHCP-server gebruikt of u kunt de IP-adresgegevens statisch toewijzen.|  
|Apparaatstuurprogramma's toepassen|Met deze takenreeksstap installeert u stuurprogramma's als onderdeel van de implementatie van een besturingssysteem. U kunt Windows Setup toestaan om in alle bestaande categorieën stuurprogramma's te zoeken door **stuurprogramma's uit alle categorieën overwegen** te selecteren of de stuurprogrammacategorieën waarin Windows Setup zoekt beperken door **Zoeken naar passende stuurprogramma's beperken tot bepaalde categorieën**te selecteren.<br /><br /> Deze stap maakt gebruik van de alleen-lezen takenreeksvariabele **_SMSTSMediaType** . Deze takenreeksstap wordt alleen uitgevoerd als de waarde van de variabele niet gelijk is aan **FullMedia**.|  
|Stuurprogrammapakket toepassen|Gebruik deze takenreeksstap om alle apparaatstuurprogramma's in een stuurprogrammapakket beschikbaar te maken voor gebruik door Windows Setup.|  
|Besturingssysteem installeren - **(nieuwe Takenreeksgroep)**|Maak een nieuwe takenreekssubgroep. Deze subgroep bevat de stappen die nodig zijn voor het instellen van het geïnstalleerde besturingssysteem.|  
|Windows en ConfigMgr installeren|Gebruik deze takenreeksstap om de Configuration Manager-clientsoftware te installeren. Configuration Manager installeert en registreert de GUID van de Configuration Manager-client. U kunt de vereiste installatieparameters toewijzen in het venster **Installatie-eigenschappen** .|  
|Updates installeren|Met deze takenreeksstap geeft u op hoe software-updates worden geïnstalleerd op de doelcomputer. De doelcomputer wordt pas geëvalueerd voor toepasselijke software-updates als deze takenreeksstap wordt uitgevoerd. Op dat moment wordt de doelcomputer geëvalueerd voor software-updates is vergelijkbaar met een andere beheerd door Configuration Manager-client.<br /><br /> Deze stap maakt gebruik van de alleen-lezen takenreeksvariabele **_SMSTSMediaType** . Deze takenreeksstap wordt alleen uitgevoerd als de waarde van de variabele niet gelijk is aan **FullMedia**.|  
|Herstellen van gebruikersbestanden en -instellingen - **(nieuwe Takenreekssubgroep)**|Maak een nieuwe takenreekssubgroep. Deze subgroep bevat de stappen die nodig zijn voor de gebruikersbestanden en -instellingen herstellen.|  
|Opslag gebruikersstatus aanvragen|Gebruik deze takenreeksstap om toegang aan te vragen tot een statusmigratiepunt waar de gebruikersgegevens worden opgeslagen.|  
|Gebruikersbestanden en -instellingen herstellen|Gebruik deze takenreeksstap om te starten van de gebruiker State Migration Tool (USMT) voor het herstellen van gebruikersstatus en instellingen op een doelcomputer.|  
|Opslag gebruikersstatus vrijgeven|Gebruik deze takenreeksstap om het statusmigratiepunt te informeren dat de gebruikersstatusgegevens niet langer nodig zijn.|  
