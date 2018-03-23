---
title: 'Opstartinstallatiekopieën beheren '
titleSuffix: Configuration Manager
description: In Configuration Manager, informatie over het beheren van de Windows PE-opstartinstallatiekopieën die u tijdens de implementatie van een besturingssysteem gebruiken.
ms.custom: na
ms.date: 03/22/2018
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-osd
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 97f2d81a-2c58-442c-88bc-defd5a1cd48f
caps.latest.revision: ''
caps.handback.revision: ''
author: aczechowski
ms.author: aaroncz
manager: dougeby
ms.openlocfilehash: 8fd5510ec00cdcf6829778b264b759588a2323cb
ms.sourcegitcommit: 11bf4ed40ed0cbb10500cc58bbecbd23c92bfe20
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 03/23/2018
---
# <a name="manage-boot-images-with-system-center-configuration-manager"></a>Opstartinstallatiekopieën beheren met System Center Configuration Manager

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*

Een opstartinstallatiekopie in Configuration Manager is een [Windows PE](https://docs.microsoft.com/windows-hardware/manufacture/desktop/winpe-intro) installatiekopie (WinPE) die wordt gebruikt tijdens de implementatie van een besturingssysteem. Opstartinstallatiekopieën worden gebruikt voor een computer te starten in WinPE. Deze minimaal besturingssysteem bevat beperkte onderdelen en services. Configuration Manager gebruikt WinPE voor de doelcomputer voorbereidt voor Windows-installatie. Gebruik de volgende secties voor het beheren van opstartinstallatiekopieën.

## <a name="BKMK_BootImageDefault"></a> Standaardopstartinstallatiekopieën
Configuration Manager biedt twee standaardopstartinstallatiekopieën: Één ter ondersteuning van x86-platformen en één ter ondersteuning van x64 platforms. Deze installatiekopieën worden opgeslagen: \\ \\ *servername*> \SMS_ <*sitecode*> \osd\boot\\<*x64*> of <*i386*>. De standaardopstartinstallatiekopieën worden bijgewerkt of opnieuw worden gegenereerd, afhankelijk van de actie die u wilt uitvoeren.

Houd rekening met de volgende gedragsopties instelt voor een van de acties beschreven voor de standaardopstartinstallatiekopieën:
- De bronobjecten van het stuurprogramma moeten geldig zijn. Deze objecten bevatten de bronbestanden van het stuurprogramma. Als de objecten niet geldig zijn, toevoegen niet de site de stuurprogramma's aan de installatiekopieën.
- Installatiekopieën die niet zijn gebaseerd op de standaardopstartinstallatiekopieën, zelfs als ze dezelfde Windows PE-versie gebruiken worden niet gewijzigd.
- De gewijzigde opstartinstallatiekopieën naar distributiepunten distribueren.
- Maak de media die gebruikmaakt van de aangepaste opstartinstallatiekopieën opnieuw.
- Als u niet dat uw aangepaste/standaard opstartinstallatiekopieën automatisch bijgewerkt wilt, u deze niet opslaan in de standaardlocatie.

> [!NOTE]
> Het hulpprogramma Configuration Manager Trace Log (CMTrace) is toegevoegd aan alle opstartinstallatiekopieën in de **softwarebibliotheek**. Wanneer u zich in Windows PE, start u het hulpprogramma door te typen **CMTrace** vanaf de opdrachtprompt. Vanaf versie 1802, tijdens het starten van cmtrace.exe in Windows PE, wordt u niet langer gevraagd te kiezen of maken van dit programma van de standaard-viewer voor logboekbestanden.

### <a name="use-updates-and-servicing-to-install-the-latest-version-of-configuration-manager"></a>Updates en onderhoud voor het installeren van de meest recente versie van Configuration Manager gebruiken
Vanaf versie 1702, wanneer u de versie van Windows Assessment and Deployment Kit (ADK) niet bijwerken en vervolgens met updates en onderhoud voor het installeren van de meest recente versie van Configuration Manager, de site wordt opnieuw gegenereerd de standaardopstartinstallatiekopieën. Deze update bevat de nieuwe WinPE-versie van de bijgewerkte Windows ADK, de nieuwe versie van de Configuration Manager-client, stuurprogramma's en aanpassingen. De site geen aangepaste opstartinstallatiekopieën te wijzigen.

Voorafgaand aan versie 1702, Configuration Manager de bestaande opstartinstallatiekopie bijgewerkt met de clientonderdelen, de stuurprogramma's en de aanpassingen, maar geen gebruik maakt van de meest recente WinPE-versie van Windows ADK. Handmatig wijzigen van de opstartinstallatiekopie voor het gebruik van de nieuwe versie van Windows ADK.

### <a name="upgrade-from-configuration-manager-2012-to-configuration-manager-current-branch-cb"></a>Upgrade van Configuration Manager 2012 naar Configuration Manager Current Branch (CB)
Wanneer u Configuration Manager 2012 met Configuration Manager CB met behulp van het installatieproces bijwerkt, wordt de site de standaardopstartinstallatiekopieën opnieuw gegenereerd. Deze update bevat de nieuwe WinPE-versie van de bijgewerkte Windows ADK en de nieuwe versie van Configuration Manager-client. Alle aanpassingen in opstartinstallatiekopies blijven ongewijzigd. De site geen aangepaste opstartinstallatiekopieën te wijzigen.

### <a name="update-distribution-points-with-the-boot-image"></a>Bijwerken van distributiepunten met de installatiekopie
Wanneer u gebruikt de **distributiepunten bijwerken** actie van de **opstartinstallatiekopieën** knooppunt in de console, de site de doel-opstartinstallatiekopie bijgewerkt met de clientonderdelen, de stuurprogramma's en de aanpassingen.    

Met ingang van Configuration Manager versie 1706, opnieuw laden van de installatiekopie met de meest recente versie van WinPE vanuit de installatiemap van Windows ADK. De **algemene** pagina van de wizard distributiepunten bijwerken bevat de volgende informatie: 
 - De Windows ADK-versie die is geïnstalleerd op de siteserver
 - De Windows ADK-versie van WinPE in de opstartinstallatiekopie
 - De versie van Configuration Manager-client gebruiken deze informatie om te helpen beslissen of u de opstartinstallatiekopie opnieuw laden. De **opstartinstallatiekopieën** knooppunt bevat ook een nieuwe kolom voor (**clientversie**). Deze kolom wordt gebruikt om weer te geven snel de versie van de Configuration Manager-client in elke opstartinstallatiekopie.    


##  <a name="BKMK_BootImageCustom"></a> Een opstartinstallatiekopie aanpassen  
 Wanneer een opstartinstallatiekopie is gebaseerd op de WinPE-versie van de ondersteunde versie van Windows ADK, kunt u aanpassen of [een opstartinstallatiekopie wijzigen](#BKMK_ModifyBootImages) vanuit de console. Wanneer een site is bijgewerkt met een nieuwe versie en een nieuwe versie van Windows ADK is geïnstalleerd, worden aangepaste opstartinstallatiekopieën (niet in de standaardlocatie voor opstartinstallatiekopieën bevinden) niet zijn bijgewerkt met de nieuwe versie van Windows ADK. Wanneer dit gebeurt, kunt u de opstartinstallatiekopieën in de Configuration Manager-console niet aanpassen. Ze blijven echter werken zoals vóór de upgrade.  

 Wanneer een opstartinstallatiekopie is gebaseerd op een andere versie van Windows ADK is geïnstalleerd op een site, moet u de opstartinstallatiekopieën aanpassen. Gebruik een andere methode voor het aanpassen van deze installatiekopieën, zoals de Deployment Image Servicing and Management (DISM) opdrachtregeltool. DISM maakt deel uit van Windows ADK. Zie voor meer informatie [opstartinstallatiekopieën aanpassen](customize-boot-images.md).  

##  <a name="BKMK_AddBootImages"></a> Een opstartinstallatiekopie toevoegen  

 Tijdens site-installatie voegt Configuration Manager automatisch opstartinstallatiekopieën die zijn gebaseerd op een WinPE-versie van de ondersteunde versie van Windows ADK. Afhankelijk van de versie van Configuration Manager, is het mogelijk om toe te voegen op basis van een andere WinPE-versie van de ondersteunde versie van Windows ADK-opstartinstallatiekopieën. Er treedt een fout op wanneer u probeert toe te voegen van een installatiekopie die een niet-ondersteunde versie van WinPE bevat. De volgende lijst bevat de ondersteunde versies van Windows ADK en WinPE: 

-   **Windows ADK-versie**  

     Windows ADK voor Windows 10  

-   **Windows PE-versies voor installatiekopieën die aanpasbaar zijn via de Configuration Manager-console**  

     Windows PE 10  

-   **Ondersteunde Windows PE-versies voor installatiekopieën die niet aanpasbaar zijn via de Configuration Manager-console**  

     Windows PE 3.1<sup>1</sup> en Windows PE 5  

     <sup>1</sup> u kunt alleen een opstartinstallatiekopie toevoegen aan Configuration Manager wanneer deze is gebaseerd op Windows PE 3.1. Werk de Windows AIK voor Windows 7 (gebaseerd op Windows PE 3.0) met de Windows AIK Supplement voor Windows 7 SP1 (gebaseerd op Windows PE 3.1). Download de Windows AIK Supplement voor Windows 7 SP1 via het [Microsoft Download Center](https://www.microsoft.com/download/details.aspx?id=5188).  

     Bijvoorbeeld de Configuration Manager-console gebruiken om aan te passen, installatiekopieën gebaseerd op Windows PE 10 uit de Windows ADK voor Windows 10. Voor een opstartinstallatiekopie is gebaseerd op Windows PE 5, aan te passen vanaf een andere computer met de versie van DISM uit de Windows ADK voor Windows 8. Vervolgens moet u de aangepaste installatiekopie toevoegen aan de Configuration Manager-console. Zie voor meer informatie [opstartinstallatiekopieën aanpassen](customize-boot-images.md).

 Gebruik de volgende procedure om handmatig een opstartinstallatiekopie toe te voegen.  

#### <a name="to-add-a-boot-image"></a>Een opstartinstallatiekopie toevoegen  

1.  Klik in de Configuration Manager-console op **Softwarebibliotheek**.  

2.  Vouw **Besturingssystemen** uit in de werkruimte **Softwarebibliotheek** en klik vervolgens op **Installatiekopieën**.  

3.  Klik op **Installatiekopie toevoegen** in het tabblad **Start** in de groep **Maken** om de wizard Installatiekopie toevoegen te starten.  

4.  Geef op de pagina **Gegevensbron** de volgende opties op en klik op **Volgende**.  

    -   Geef in het vakje **Pad** het pad op naar het WIM-bestand van de opstartinstallatiekopie.  

         Het opgegeven pad moet een geldig netwerkpad zijn in UNC-indeling. For example: \\\\<*servername*\\<*sharename*>\\<*bootimagename*>.wim.  

    -   Selecteer de installatiekopie in de vervolgkeuzelijst **Installatiekopie**. Als het WIM-bestand meerdere installatiekopieën bevat, selecteert u de juiste installatiekopie.  

5.  Geef op de pagina **Algemeen** de volgende opties op en klik vervolgens op **Volgende**.  

    -   Geef in het venster **Naam** een unieke naam op voor de installatiekopie.  

    -   Geef in het venster **Versie** een uniek versienummer op voor de installatiekopie.  

    -   Geef in het veld **Opmerking** een korte beschrijving van hoe de installatiekopie wordt gebruikt.  

6.  Voltooi de wizard.  

 De opstartinstallatiekopie is nu opgenomen in de **opstartinstallatiekopie** knooppunt van de Configuration Manager-console. Voordat u de opstartinstallatiekopie gebruiken om een besturingssysteem te implementeren, moet u de opstartinstallatiekopie naar distributiepunten distribueren. 

> [!NOTE]  
>  In de **opstartinstallatiekopie** knooppunt van de console, de **grootte (KB)** kolom ziet u de gecomprimeerde grootte voor elke opstartinstallatiekopie. Wanneer de site een opstartinstallatiekopie via het netwerk verzendt, zendt het een gecomprimeerde kopie. Dit exemplaar is doorgaans kleiner is dan de grootte die worden vermeld in de **grootte (KB)** kolom.  

##  <a name="BKMK_DistributeBootImages"></a> Opstartinstallatiekopieën naar een distributiepunt distribueren  
 Opstartinstallatiekopieën worden op dezelfde manier naar distributiepunten gedistribueerd als bij het distribueren van andere inhoud. In de meeste gevallen moet u de opstartinstallatiekopie naar ten minste één distributiepunt distribueren voordat u een besturingssysteem implementeert en voordat u media maakt.   

> [!NOTE]  
> Houd rekening met de volgende punten om PXE gebruiken om een besturingssysteem te implementeren, voordat u de opstartinstallatiekopie distribueert:  
> - Configureer het distributiepunt om PXE-aanvragen te accepteren.  
> - Zowel een x86- en een x64 distribueren opstartinstallatiekopie met PXE-functionaliteit naar ten minste één distributiepunt met PXE-functionaliteit.  
> - Configuration Manager distribueert de opstartinstallatiekopieën naar de **RemoteInstall** map op het distributiepunt met PXE-functionaliteit.  
>   
> Zie voor meer informatie over het implementeren van besturingssystemen met PXE [PXE gebruiken om Windows te implementeren via het netwerk](../deploy-use/use-pxe-to-deploy-windows-over-the-network.md).  

 Zie [Distribute content](/sccm/core/servers/deploy/configure/deploy-and-manage-content#bkmk_distribute) (Inhoud distribueren) voor de stappen voor het distribueren van een opstartinstallatiekopie.  

##  <a name="BKMK_ModifyBootImages"></a> Een opstartinstallatiekopie wijzigen  
 U kunt apparaatstuurprogramma aan de installatiekopie toevoegen of verwijderen of de eigenschappen bewerken die aan de opstartinstallatiekopie zijn gekoppeld. De door u toegevoegde of verwijderde apparaatstuurprogramma's kunnen stuurprogramma's voor netwerkadapters of massaopslag zijn. Houd rekening met de volgende factoren wanneer u opstartinstallatiekopieën wijzigt:  

-   Importeren en inschakelen van de apparaatstuurprogramma's in de catalogus voor apparaatstuurprogramma voordat u deze toevoegt aan de installatiekopie.  

-   Wanneer u een opstartinstallatiekopie wijzigt, wijzigt de opstartinstallatiekopie geen van de gekoppelde pakketten waarnaar de opstartinstallatiekopie verwijst.  

-   Nadat u wijzigingen aan een opstartinstallatiekopie aanbrengt **bijwerken** de opstartinstallatiekopie op het distributiepunt wijst die al hebt. Dit proces maakt de meest recente versie van de opstartinstallatiekopie beschikbaar voor clients. Zie [Manage content you have distributed](/sccm/core/servers/deploy/configure/deploy-and-manage-content#bkmk_manage) (Inhoud beheren die u hebt gedistribueerd) voor meer informatie.  

 Gebruik de volgende procedure om een opstartinstallatiekopie te wijzigen.  

#### <a name="to-modify-the-properties-of-a-boot-image"></a>De eigenschappen van een opstartinstallatiekopie wijzigen  

1.  Klik in de Configuration Manager-console op **Softwarebibliotheek**.  

2.  Vouw **Besturingssystemen** uit in de werkruimte **Softwarebibliotheek** en klik vervolgens op **Installatiekopieën**.  

3.  Selecteer de opstartinstallatiekopie die u wilt wijzigen.  

4.  Klik op **Eigenschappen** op het tabblad **Start** in de groep **Eigenschappen**, om het dialoogvenster **Eigenschappen** voor de opstartinstallatiekopie te openen.  

5.  Stel één van de volgende instellingen in om het gedrag van de opstartinstallatiekopie te wijzigen:  

    -   Klik op **Opnieuw laden** op het tabblad **Installatiekopieën**, indien u de eigenschappen van de opstartinstallatiekopie hebt gewijzigd door gebruik te maken van een extern hulpprogramma.  

    -   Voeg op het tabblad **Stuurprogramma's** de Windows-apparaatstuurprogramma's toe, die vereist zijn om WinPE op te starten. Houd rekening met de volgende punten wanneer u apparaatstuurprogramma's toevoegt:  

        -   Selecteer **stuurprogramma's die niet overeenkomen met de architectuur van de installatiekopie verbergen** om alleen stuurprogramma's voor de architectuur van de opstartinstallatiekopie weer te geven. De architectuur is gebaseerd op de architectuur die wordt vermeld in het INF-bestand van de fabrikant.  

        -   Selecteer **stuurprogramma's die zich niet in een opslag- of netwerkklasse (voor installatiekopieën) verbergen** om alleen opslag- en netwerkstations weer te geven. Deze optie verbergt u ook andere stuurprogramma's die doorgaans niet nodig voor installatiekopieën, zoals een video- of modem stuurprogramma's zijn.  

        -   Selecteer **stuurprogramma's die niet digitaal zijn ondertekend verbergen** voor het verbergen van stuurprogramma's die u geen geldige digitale handtekening hebt.  

        -   Als een best practice toevoegen alleen netwerk- en stuurprogramma's voor massaopslag aan de opstartinstallatiekopie, tenzij er vereisten voor andere stuurprogramma's in WinPE.  

        -   Aangezien WinPE een groot aantal ingebouwde stuurprogramma's bevat, alleen netwerk- en mass storage stuurprogramma's toevoegen die niet door WinPE worden geleverd.  

        -   Zorg ervoor dat de stuurprogramma's die u aan de opstartinstallatiekopie toevoegt overeenkomen met de architectuur van de opstartinstallatiekopie.  

        > [!NOTE]  
        >  U moet apparaatstuurprogramma's importeren in de stuurprogrammacatalogies, vóór u ze toevoegt aan de opstartinstallatiekopie. Zie voor meer informatie over het importeren van apparaatstuurprogramma's [stuurprogramma's beheren](manage-drivers.md).  

    -   Selecteer op het tabblad **Aanpassen** één van de volgende instellingen:  

        -   Selecteer het selectievakje **Schakel prestart-opdrachten** om een uit te voeren opdracht op te geven vóór de takenreeks wordt uitgevoerd. Wanneer u deze optie inschakelt, ook de opdrachtregel om uit te voeren en ondersteuningsbestanden vereist door de opdracht opgeven.  

            > [!WARNING]  
            >  Voeg **cmd /c** toe aan het begin van de opdrachtregel. Als u geen opgeeft **cmd /c**, de opdracht niet gesloten nadat deze is uitgevoerd. De implementatie blijft wachten tot de opdracht is voltooid en geen andere geconfigureerde opdrachten of acties start niet.  

            > [!TIP]  
            >  Tijdens het maken van de media taak schrijft de wizard de pakket-ID en prestart-opdrachtregel, inclusief de waarde voor eventuele takenreeksvariabelen, naar het logboekbestand CreateTSMedia.log. Dit logboek is op de computer waarop de Configuration Manager-console. Bekijk dit logboekbestand om de waarde voor de takenreeksvariabelen te verifiëren.  

        -   Stel bij **Windows PE-achtergrond** in of u de standaardachtergrond van WindowsPE of een aangepaste achtergrond wilt gebruiken.  

        -   Schakel het selectievakje **Opdrachtondersteuning inschakelen (alleen testen)** in om tijdens het implementeren van de opstartinstallatiekopie een opdrachtprompt met toets **F8** te openen. Deze optie is nuttig voor de probleemoplossing als u uw implementatie test. Het gebruik van deze instelling in een productie-implementatie wordt niet aanbevolen.  

        -   Configureer de Windows PE-scratchruimte, die door Windows PE wordt gebruikt als tijdelijke opslag (RAM-station). Wanneer er bijvoorbeeld een toepassing wordt uitgevoerd in WinPE en er tijdelijke bestanden moet worden geschreven, stuurt WindPE de bestanden naar de scratchruimte in het geheugen om de aanwezigheid van een harde schijf te simuleren. Standaard wijst WinPE 32 megabytes (MB) aan beschrijfbaar geheugen toe.  

    -   Update één van de volgende instellingen op het tabblad **Gegevensbron**:  

        -   Als u wilt wijzigen van het bronbestand van de opstartinstallatiekopie, **installatiekopiepad** en **installatiekopie-index**.  

        -   Voor het maken van een planning voor wanneer de site de opstartinstallatiekopie werkt selecteert **Update distributiepunten volgens een schema**.  

        -   Als u niet dat de inhoud van dit pakket uit de clientcache om ruimte voor andere inhoud te maken wilt, selecteert u **inhoud in de clientcache behouden**.  

        -   U kunt opgeven dat de site de gewijzigde bestanden alleen verspreidt tijdens het bijwerken van het opstartinstallatiekopiepakket op het distributiepunt, **binaire differentiële replicatie inschakelen** (BDR). Deze instelling minimaliseert het netwerkverkeer tussen sites. BDR is vooral nuttig wanneer het opstartinstallatiekopie-pakket groot is en de wijzigingen relatief gering zijn.  

        -   Als u de installatiekopie in een implementatie met PXE-functionaliteit gebruikt, selecteert u **deze opstartinstallatiekopie implementeren vanaf het distributiepunt met PXE-functionaliteit**.  

            > [!NOTE]  
            >  Zie voor meer informatie [PXE gebruiken om Windows te implementeren via het netwerk](../deploy-use/use-pxe-to-deploy-windows-over-the-network.md).  

    -   Selecteer één van de volgende instellingen op het tabblad **Gegevenstoegang**:  

        -   Stel de **Instellingen van pakketshare** in als u wenst dat clients de inhoud in dit pakket installeren vanuit het netwerk.  

        -   Stel de **pakket update-instellingen** om op te geven hoe Configuration Manager gebruikers ontkoppelt van het distributiepunt. Configuration Manager kan het zijn de opstartinstallatiekopie bijwerken wanneer gebruikers gekoppeld zijn aan het distributiepunt.  

    -   Selecteer één van de volgende instellingen op het tabblad **Distributie-instellingen**:  

        -   In de **distributieprioriteit** lijst, geeft u het prioriteitsniveau op. Configuration Manager gebruikt deze prioriteitenlijst wanneer de site meerdere pakketten naar hetzelfde distributiepunt distribueert.  

        -   Als u inschakelen, distributie van inhoud op aanvraag naar voorkeursdistributiepunten wilt, selecteert u **Distribueer de inhoud voor dit pakket naar voorkeursdistributiepunten**. Wanneer u deze instelling inschakelt als een client de inhoud voor het pakket opvraagt en de inhoud niet beschikbaar is op voorkeursdistributiepunten, is en het beheerpunt de inhoud naar alle voorkeursdistributiepunten distribueert.  

        -   Wilt u opgeven hoe u wilt dat de site om de opstartinstallatiekopie naar distributiepunten die zijn ingeschakeld voor voorbereide inhoud te distribueren, stelt de **instellingen voorbereid distributiepunt**.  

            > [!NOTE]  
            >  Zie [Prestage content](/sccm/core/servers/deploy/configure/deploy-and-manage-content#bkmk_prestage) (Voorbereide inhoud) voor meer informatie over voorbereide inhoud.  

    -   Selecteer, op het tabblad **Content Locations**, het distributiepunt of distributiepuntgroep en voer één van de volgende acties uit:  

        -   Klik op **Herverdelen** om de opstartinstallatiekopie opnieuw te distribueren naar het geselecteerde distributiepunt of distributiepuntgroep.  

        -   Klik op **Valideer** om de integriteit te controleren van het opstartinstallatiekopiepakket op het geselecteerde distributiepunt of de geselecteerde distributiepuntgroep.  

    -   Op de **optionele onderdelen** tabblad, geeft u de onderdelen die zijn toegevoegd aan Windows PE voor gebruik met Configuration Manager. Zie voor meer informatie over beschikbare optionele onderdelen [WinPE: Pakketten (Optional Components Reference) toevoegen](https://docs.microsoft.com/windows-hardware/manufacture/desktop/winpe-add-packages--optional-components-reference).  

    -   Selecteer op het tabblad **Beveiliging** een gebruiker met beheerdersrechten en wijzig de operaties die ze kunnen uitvoeren.  

6.  Klik op **OK** nadat u de eigenschappen hebt geconfigureerd.  

##  <a name="BKMK_BootImagePXE"></a> Een opstartinstallatiekopie implementeren vanaf een distributiepunt met PXE-functionaliteit configureren  
 Voordat u een opstartinstallatiekopie voor de implementatie van een PXE-besturingssysteem kunt gebruiken, moet u de opstartinstallatiekopie configureren voor een implementatie vanaf een distributiepunt met PXE-functionaliteit.  

#### <a name="to-configure-a-boot-image-to-deploy-from-a-pxe-enabled-distribution-point"></a>Een opstartinstallatiekopie configureren voor de implementatie vanaf een distributiepunt met PXE-functionaliteit  

1.  Klik in de Configuration Manager-console op **Softwarebibliotheek**.  

2.  Vouw **Besturingssystemen** uit in de werkruimte **Softwarebibliotheek** en klik vervolgens op **Installatiekopieën**.  

3.  Selecteer de opstartinstallatiekopie die u wilt wijzigen.  

4.  Klik op **Eigenschappen** op het tabblad **Start** in de groep **Eigenschappen**, om het dialoogvenster **Eigenschappen** voor de opstartinstallatiekopie te openen.  

5.  Selecteer op het tabblad **Gegevensbron** de optie **Deze opstartinstallatiekopie implementeren vanaf het PXE-distributiepunt**.  

    > [!NOTE]  
    >  Zie voor meer informatie [PXE gebruiken om Windows te implementeren via het netwerk](../deploy-use/use-pxe-to-deploy-windows-over-the-network.md).  

6.  Klik op **OK** nadat u de eigenschappen hebt geconfigureerd.  

##  <a name="BKMK_BootImageLanguage"></a> Meerdere talen configureren voor implementatie van de opstartinstallatiekopie  
 Opstartinstallatiekopieën zijn taalonafhankelijk. Deze functie kunt u één opstartinstallatiekopie gebruiken om de tekst van de takenreeks in meerdere talen wanneer WinPE weer te geven. De toepasselijke taalondersteuning uit de opstartinstallatiekopie bevatten **optionele onderdelen** tabblad. Stel de toepasselijke takenreeksvariabele om aan te geven welke taal om weer te geven. De taal van het geïmplementeerde besturingssysteem is onafhankelijk van de taal in WinPE. De taal die WinPE voor de gebruiker wordt is als volgt bepaald:  

-   Wanneer een gebruiker de takenreeks wordt uitgevoerd vanuit een bestaand besturingssysteem wordt uitgevoerd, gebruikt Configuration Manager automatisch de taal die is geconfigureerd voor de gebruiker. Wanneer de takenreeks automatisch wordt uitgevoerd als gevolg van een verplichte implementatiedeadline, wordt in Configuration Manager maakt gebruik van de taal van het besturingssysteem.  

-   Voor implementaties van besturingssystemen die PXE of media gebruiken de waarde van de taal-ID in de **SMSTSLanguageFolder** variabele als onderdeel van een prestart-opdracht. Wanneer de computer wordt opgestart in WinPE, worden berichten weergegeven in de taal die u hebt opgegeven in de variabele. Als er een fout bij toegang tot het bronbestand in de opgegeven map, of u de variabele niet instelt, worden berichten weergegeven in de standaardtaal van WinPE.  

    > [!NOTE]  
    >  Wanneer de media met een wachtwoord zijn beschermd, wordt de tekst waarin de gebruiker naar het wachtwoord wordt gevraagd, altijd weergegeven in de WinPE-taal.  

 Gebruik de volgende procedure om de WinPE-taal in te stellen voor met PXE of media geïnitieerde besturingssysteemimplementaties.  

#### <a name="to-set-the-windows-pe-language-for-a-pxe-or-media-initiated-operating-system-deployment"></a>De Windows PE-taal instellen voor implementaties van door PXE of media geactiveerde besturingssystemen  

1.  Controleer of de juiste volgorde bronbestand (tsres.dll) in de betreffende taalmap op de siteserver voordat u de opstartinstallatiekopie bijwerkt. Bijvoorbeeld, het Engels bronbestand bevindt in de volgende locatie: <*ConfigMgrInstallationFolder*> \OSD\bin\x64\00000409\tsres.dll.  

2.  Als onderdeel van uw prestart-opdracht stelt u de variabele voor de SMSTSLanguageFolder-omgeving in op de juiste taal-id. De taal-id moet worden opgegeven met decimale tekens en geen hexadecimale tekens. Geef bijvoorbeeld de taal-ID op Engels wilt instellen, de decimale waarde 1033, niet de hexadecimale waarde 00000409 van de mapnaam.  
