---
title: "Opstartinstallatiekopieën - Configuration Manager beheren | Microsoft Docs"
description: "In Configuration Manager, informatie over het beheren van de Windows PE-opstartinstallatiekopieën die u tijdens de implementatie van een besturingssysteem gebruiken."
ms.custom: na
ms.date: 01/23/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: configmgr-osd
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 97f2d81a-2c58-442c-88bc-defd5a1cd48f
caps.latest.revision: "23"
caps.handback.revision: "0"
author: Dougeby
ms.author: dougeby
manager: angrobe
ms.openlocfilehash: cc678c1133b1944f55bcad309cf9ede9f0660b57
ms.sourcegitcommit: 51fc48fb023f1e8d995c6c4eacfda7dbec4d0b2f
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 08/07/2017
---
# <a name="manage-boot-images-with-system-center-configuration-manager"></a>Opstartinstallatiekopieën beheren met System Center Configuration Manager

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*

Een opstartinstallatiekopie in Configuration Manager is een [Windows PE (WinPE)](https://msdn.microsoft.com/library/windows/hardware/dn938389%28v=vs.85%29.aspx) afbeelding die wordt gebruikt tijdens de implementatie van een besturingssysteem. Opstartinstallatiekopieën worden gebruikt om een computer op te starten in WinPE. Dit is een minimaal besturingssysteem met beperkte onderdelen en services dat de doelcomputer voorbereidt voor een Windows-installatie.  Gebruik de volgende secties voor het beheren van opstartinstallatiekopieën.

## <a name="BKMK_BootImageDefault"></a>Standaardopstartinstallatiekopieën
Configuration Manager biedt twee standaardopstartinstallatiekopieën: Één ter ondersteuning van x86-platformen en één ter ondersteuning van x64 platforms. Deze installatiekopieën worden opgeslagen: \\ \\ *servername*> \SMS_ <*sitecode*> \osd\boot\\<*x64*> of <*i386*>. De standaardopstartinstallatiekopieën worden bijgewerkt of opnieuw worden gegenereerd, afhankelijk van de actie die u wilt uitvoeren.

Overweeg het volgende voor elk van de acties beschreven in de volgende secties:
- De bronobjecten van het stuurprogramma moeten geldig zijn, inclusief de bronbestanden van het stuurprogramma of de stuurprogramma's wordt niet toegevoegd aan de opstartinstallatiekopieën op de site zijn.
- Installatiekopieën die niet zijn gebaseerd op de standaardopstartinstallatiekopieën, zelfs als ze dezelfde Windows PE-versie gebruiken worden niet gewijzigd.
- U moet de gewijzigde opstartinstallatiekopieën naar distributiepunten opnieuw distribueren.
- U moet alle media die gebruikmaakt van de aangepaste opstartinstallatiekopieën opnieuw maken.
- Als u niet dat uw aangepaste/standaard opstartinstallatiekopieën automatisch bijgewerkt wilt, u deze niet opslaan in de standaardlocatie.

> [!NOTE]
> Het hulpprogramma Configuration Manager Trace Log wordt toegevoegd aan alle opstartinstallatiekopieën die u toevoegt aan de **softwarebibliotheek**. Wanneer u zich in Windows PE, kunt u het hulpprogramma Configuration Manager Trace Log beginnen door te typen **CMTrace** vanaf een opdrachtprompt.  

### <a name="use-updates-and-servicing-to-install-the-latest-version-of-configuration-manager"></a>Updates en onderhoud voor het installeren van de meest recente versie van Configuration Manager gebruiken
Vanaf versie 1702, wanneer u de Windows ADK-versie bijwerken en vervolgens met updates en onderhoud voor het installeren van de meest recente versie van Configuration Manager, Configuration Manager genereert de standaardopstartinstallatiekopieën. Dit omvat het nieuwe venster PE-versie van de bijgewerkte Windows ADK, de nieuwe versie van de Configuration Manager-client, stuurprogramma's, aanpassingen, enzovoort. Aangepaste opstartinstallatiekopieën worden niet gewijzigd.

Voorafgaand aan versie 1702, Configuration Manager de bestaande installatiekopie (boot.wim) bijgewerkt met de clientonderdelen, de stuurprogramma's, de aanpassingen, enz. maar maakt geen gebruik van de meest recente Windows PE-versie van Windows ADK. De opstartinstallatiekopie voor het gebruik van de nieuwe versie van Windows ADK, moet u handmatig wijzigen.

### <a name="upgrade-from-configuration-manager-2012-to-configuration-manager-current-branch-cb"></a>Upgrade van Configuration Manager 2012 naar Configuration Manager Current Branch (CB)
Wanneer u Configuration Manager 2012 met Configuration Manager CB met behulp van het installatieproces bijwerkt, wordt de standaardopstartinstallatiekopieën opnieuw gegenereerd Configuration Manager. Dit omvat het nieuwe venster PE-versie van de bijgewerkte Windows ADK, de nieuwe versie van de Configuration Manager-client, en alle aanpassingen blijven ongewijzigd. Aangepaste opstartinstallatiekopieën worden niet gewijzigd.

### <a name="update-distribution-points-with-the-boot-image"></a>Bijwerken van distributiepunten met de installatiekopie
Wanneer u gebruikt de **distributiepunten bijwerken** actie van de **opstartinstallatiekopieën** knooppunt in de Configuration Manager-console Configuration Manager de standaardopstartinstallatiekopieën bijgewerkt met de clientonderdelen, de stuurprogramma's, de aanpassingen, enzovoort.    

Vanaf Configuration Manager versie 1706, kunt u de nieuwste versie van Windows PE (van de installatiemap van Windows ADK) in de opstartinstallatiekopie opnieuw laden. De **algemene** pagina van de wizard distributiepunten bijwerken bevat informatie over de Windows ADK-versie die is geïnstalleerd op de siteserver, de Windows ADK-versie waarin Windows PE wordt gebruikt in de opstartinstallatiekopie en de versie van Configuration Manager-client. U kunt deze informatie gebruiken om te beslissen of u wilt de opstartinstallatiekopie opnieuw laden. Ook een nieuwe kolom (**clientversie**) is toegevoegd wanneer u opstartinstallatiekopieën in de **opstartinstallatiekopieën** knooppunt zodat u weet welke versie van Configuration Manager-client elke opstartinstallatiekopie wordt gebruikt.    

Aangepaste opstartinstallatiekopieën worden niet gewijzigd.

##  <a name="BKMK_BootImageCustom"></a>Een opstartinstallatiekopie aanpassen  
 U kunt een opstartinstallatiekopie aanpassen of [een opstartinstallatiekopie wijzigen](#BKMK_ModifyBootImages), vanuit de Configuration Manager-console wanneer deze is gebaseerd op een Windows PE-versie van de ondersteunde versie van Windows ADK. Wanneer een site is bijgewerkt met een nieuwe versie en een nieuwe versie van Windows ADK is geïnstalleerd, worden aangepaste opstartinstallatiekopieën (die zich niet op de standaardlocatie voor opstartinstallatiekopieën bevinden) niet bijgewerkt met de nieuwe versie van Windows ADK. Wanneer dit gebeurt, kunt u zich niet langer de opstartinstallatiekopieën in de Configuration Manager-console aanpassen. Ze blijven echter werken zoals voor de upgrade.  

 Wanneer een opstartinstallatiekopie is gebaseerd op een andere versie van Windows ADK die op de site is geïnstalleerd, moet u de opstartinstallatiekopieën aanpassen met een andere methode, zoals de Deployment Image Servicing and Management (DISM) opdrachtregeltool welke deel uitmaakt van Windows AIK en Windows ADK. Zie voor meer informatie [opstartinstallatiekopieën aanpassen](customize-boot-images.md).  

##  <a name="BKMK_AddBootImages"></a>Een opstartinstallatiekopie toevoegen  

 Tijdens site-installatie voegt Configuration Manager automatisch opstartinstallatiekopieën die zijn gebaseerd op een WinPE-versie van de ondersteunde versie van Windows ADK. Afhankelijk van de versie van Configuration Manager, is het mogelijk om toe te voegen op basis van een andere WinPE-versie van de ondersteunde versie van Windows ADK-opstartinstallatiekopieën.  Er treedt een fout op wanneer u een opstartinstallatiekopie probeert toe te voegen die een niet-ondersteunde versie van WinPE bevat.  

 Hieronder vindt u de ondersteunde versie van Windows ADK, de Windows PE-versie die op waarop de opstartinstallatiekopie is gebaseerd die kan worden aangepast via de Configuration Manager-console en de Windows PE-versies waarop de opstartinstallatiekopie is gebaseerd, u kunt aanpassen met behulp van DISM en vervolgens de installatiekopie toevoegen aan Configuration Manager.  

-   **Windows ADK-versie**  

     Windows ADK voor Windows 10  

-   **Windows PE-versies voor installatiekopieën die aanpasbaar zijn via de Configuration Manager-console**  

     Windows PE 10  

-   **Ondersteunde Windows PE-versies voor installatiekopieën die niet aanpasbaar zijn via de Configuration Manager-console**  

     Windows PE 3.1<sup>1</sup> en Windows PE 5  

     <sup>1</sup> u kunt alleen een opstartinstallatiekopie toevoegen aan Configuration Manager wanneer deze is gebaseerd op Windows PE 3.1. Installeer Windows AIK Supplement voor Windows 7 SP1 om een upgrade van Windows AIK voor Windows 7 (gebaseerd op Windows PE 3) naar Windows AIK Supplement voor Windows 7 SP1 (gebaseerd op Windows PE 3.1) uit te voeren. U kunt Windows AIK Supplement voor Windows 7 SP1 downloaden via het [Microsoft Downloadcentrum](http://www.microsoft.com/download/details.aspx?id=5188).  

     Bijvoorbeeld, wanneer u Configuration Manager hebt, kunt u opstartinstallatiekopieën uit Windows ADK voor Windows 10 (gebaseerd op Windows PE 10) aanpassen via de Configuration Manager-console. Hoewel installatiekopieën die zijn gebaseerd op Windows PE 5 wel worden wel ondersteund, moet u ze aanpassen op een andere computer en moet u die versie van DISM gebruiken die is geïnstalleerd met Windows ADK voor Windows 8. Vervolgens kunt u de installatiekopie toevoegen aan de Configuration Manager-console. Voor meer informatie over de stappen voor het aanpassen van een installatiekopie (toevoegen van optionele componenten en stuurprogramma's), inschakelen van opdrachtondersteuning aan de opstartinstallatiekopie, de installatiekopie toevoegen aan de Configuration Manager-console en distributiepunten bijwerken met de installatiekopie, Zie [opstartinstallatiekopieën aanpassen](customize-boot-images.md).

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

 De opstartinstallatiekopie is nu opgenomen in de **opstartinstallatiekopie** knooppunt van de Configuration Manager-console. Vóór u evenwel de opstartinstallatiekopie kunt gebruiken om een besturingssysteem te implementeren, moet u de opstartinstallatiekopie verdelen naar distributiepuntgroepen of naar verzamelingen die gekoppeld zijn met distributiepuntgroepen.  

> [!NOTE]  
>  Wanneer u selecteert de **opstartinstallatiekopie** knooppunt in de Configuration Manager-console de **grootte (KB)** kolom ziet u de gecomprimeerde grootte voor elke opstartinstallatiekopie. Echter als Configuration Manager stuurt een opstartinstallatiekopie via het netwerk, zendt het een gecomprimeerde kopie van de installatiekopie, die typisch veel kleiner is dan de grootte die worden vermeld in de **grootte (KB)** kolom.  

##  <a name="BKMK_DistributeBootImages"></a>Opstartinstallatiekopieën naar een distributiepunt distribueren  
 Opstartinstallatiekopieën worden op dezelfde manier naar distributiepunten gedistribueerd als bij het distribueren van andere inhoud. In de meeste gevallen moet u de opstartinstallatiekopie naar ten minste één distributiepunt distribueren voordat u een besturingssysteem implementeert en voordat u media maakt.  

> [!NOTE]  
>  Als u PXE voor de implementatie van een besturingssysteem wilt gebruiken, moet u, voordat u de opstartinstallatiekopie distribueert, rekening houden met het volgende:  
>   
>  -   Het distributiepunt moet worden geconfigureerd om PXE-aanvragen te accepteren.  
> -   U moet zowel een x86- als x64-opstartinstallatiekopie met PXE-functionaliteit naar ten minste één distributiepunt met PXE-functionaliteit distribueren.  
> -   Configuration Manager distribueert de opstartinstallatiekopieën naar de **RemoteInstall** map op het distributiepunt met PXE-functionaliteit.  
>   
>  Zie voor meer informatie over het implementeren van besturingssystemen met PXE [PXE gebruiken om Windows te implementeren via het netwerk](../deploy-use/use-pxe-to-deploy-windows-over-the-network.md).  

 Zie [Distribute content](/sccm/core/servers/deploy/configure/deploy-and-manage-content#bkmk_distribute) (Inhoud distribueren) voor de stappen voor het distribueren van een opstartinstallatiekopie.  

##  <a name="BKMK_ModifyBootImages"></a>Een opstartinstallatiekopie wijzigen  
 U kunt apparaatstuurprogramma aan de installatiekopie toevoegen of verwijderen of de eigenschappen bewerken die aan de opstartinstallatiekopie zijn gekoppeld. De door u toegevoegde of verwijderde apparaatstuurprogramma's kunnen stuurprogramma's voor netwerkadapters of massaopslag zijn. Houd rekening met de volgende factoren wanneer u opstartinstallatiekopieën wijzigt:  

-   U moet de apparaatstuurprogramma's importeren en inschakelen in de catalogus voor apparaatstuurprogramma voordat u ze kunt toevoegen aan de opstartinstallatiekopie.  

-   Wanneer u een opstartinstallatiekopie wijzigt, wijzigt de opstartinstallatiekopie geen van de gekoppelde pakketten waarnaar de opstartinstallatiekopie verwijst.  

-   Nadat u een opstartinstallatiekopie hebt gewijzigd, moet u de distributiepunten **bijwerken** die een versie van de opstartinstallatiekopie bevatten, zodat de meest recente versie van de opstartinstallatiekopie beschikbaar is. Zie [Manage content you have distributed](/sccm/core/servers/deploy/configure/deploy-and-manage-content#bkmk_manage) (Inhoud beheren die u hebt gedistribueerd) voor meer informatie.  

 Gebruik de volgende procedure om een opstartinstallatiekopie te wijzigen.  

#### <a name="to-modify-the-properties-of-a-boot-image"></a>De eigenschappen van een opstartinstallatiekopie wijzigen  

1.  Klik in de Configuration Manager-console op **Softwarebibliotheek**.  

2.  Vouw **Besturingssystemen** uit in de werkruimte **Softwarebibliotheek** en klik vervolgens op **Installatiekopieën**.  

3.  Selecteer de opstartinstallatiekopie die u wilt wijzigen.  

4.  Klik op **Eigenschappen** op het tabblad **Start** in de groep **Eigenschappen**, om het dialoogvenster **Eigenschappen** voor de opstartinstallatiekopie te openen.  

5.  Stel één van de volgende instellingen in om het gedrag van de opstartinstallatiekopie te wijzigen:  

    -   Klik op **Opnieuw laden** op het tabblad **Installatiekopieën**, indien u de eigenschappen van de opstartinstallatiekopie hebt gewijzigd door gebruik te maken van een extern hulpprogramma.  

    -   Voeg op het tabblad **Stuurprogramma's** de Windows-apparaatstuurprogramma's toe, die vereist zijn om WinPE op te starten. Overweeg het volgende wanneer u apparaatstuurprogramma's toevoegt:  

        -   Selecteer **stuurprogramma's die niet overeenkomen met de architectuur van de installatiekopie verbergen** om alleen stuurprogramma's voor de architectuur van de opstartinstallatiekopie weer te geven. De architectuur is gebaseerd op de architectuur die wordt vermeld in de .INF van de fabrikant.  

        -   Selecteer **Stuurprogramma’s buiten een opslag- of netwerkklasse verbergen (voor installatiekopieën)** om alleen opslag- en netwerkstations weer te geven en andere stuurprogramma's die doorgaans niet nodig zijn voor installatiekopieën, zoals een video- of modemstuurprogramma, te verbergen.  

        -   Selecteer **Stuurprogramma's die niet digitaal zijn ondertekend verbergen** om stuurprogramma's die niet digitaal zijn ondertekend, te verbergen.  

        -   Voeg als best practice uitsluitend NIC-stuurprogramma's en stuurprogramma's voor massaopslag aan de opstartinstallatiekopie toe, tenzij er vereisten zijn dat andere stuurprogramma's deel uitmaken van WinPE.  

        -   Aangezien WinPE een groot aantal ingebouwde stuurprogramma's bevat, kunt u het beste uitsluitend NIC-stuurprogramma's en stuurprogramma's voor massaopslag toevoegen die niet door WinPE worden geleverd.  

        -   Zorg ervoor dat de stuurprogramma's die u toevoegt aan de opstartinstallatiekopie overeenkomen met de architectuur van de opstartinstallatiekopie.  

        > [!NOTE]  
        >  U moet apparaatstuurprogramma's importeren in de stuurprogrammacatalogies, vóór u ze toevoegt aan de opstartinstallatiekopie. Zie voor meer informatie over het importeren van apparaatstuurprogramma's [stuurprogramma's beheren](manage-drivers.md).  

    -   Selecteer op het tabblad **Aanpassen** één van de volgende instellingen:  

        -   Selecteer het selectievakje **Schakel prestart-opdrachten** om een uit te voeren opdracht op te geven vóór de takenreeks wordt uitgevoerd. Wanneer prestart-opdrachten ingeschakeld zijn, kunt u de opdrachtregel opgeven die uitgevoerd wordt, opgeven of er ondersteuningsbestanden nodig zijn om de opdracht uit te voeren en de bronlocatie van deze ondersteuningsbestanden.  

            > [!WARNING]  
            >  U moet **cmd /c** toevoegen aan het begin van de opdrachtregel. Als u geen **cmd /c** opgeeft, wordt de opdracht niet afgesloten nadat deze is uitgevoerd. De implementatie blijft wachten tot de opdracht is voltooid en er worden geen andere geconfigureerde opdrachten of acties gestart.  

            > [!TIP]  
            >  Tijdens het maken van taak de media schrijft de takenreeks de pakket-ID en prestart-opdrachtregel, inclusief de waarde voor eventuele takenreeksvariabelen, naar het logboekbestand CreateTSMedia.log op de computer waarop de Configuration Manager-console. U kunt dit logboekbestand controleren om de waarde voor de takenreeksvariabelen te verifiëren.  

        -   Stel bij **Windows PE-achtergrond** in of u de standaardachtergrond van WindowsPE of een aangepaste achtergrond wilt gebruiken.  

        -   Schakel het selectievakje **Opdrachtondersteuning inschakelen (alleen testen)** in om tijdens het implementeren van de opstartinstallatiekopie een opdrachtprompt met toets **F8** te openen. Dit is nuttig voor de probleemoplossing als u uw implementatie test. Het gebruik van deze instelling in een productie-implementatie wordt niet aanbevolen.  

        -   Configureer de Windows PE-scratchruimte, die door Windows PE wordt gebruikt als tijdelijke opslag (RAM-station). Wanneer er bijvoorbeeld een toepassing wordt uitgevoerd in WinPE en er tijdelijke bestanden moet worden geschreven, stuurt WindPE de bestanden naar de scratchruimte in het geheugen om de aanwezigheid van een harde schijf te simuleren. Standaard wijst WinPE 32 megabytes (MB) aan beschrijfbaar geheugen toe.  

    -   Update één van de volgende instellingen op het tabblad **Gegevensbron**:  

        -   Stel **Pad voor installatiekopie** en **Installatiekopie-index** in om het bronbestand van de opstartinstallatiekopie te wijzigen.  

        -   Selecteer **Distributiepunten bijwerken op basis van een planning** om een planning te maken voor wanneer de opstartinstallatiekopie is bijgewerkt.  

        -   Selecteer **Inhoud in clientcache permanent behouden** als u niet wilt dat de inhoud van dit pakket uit de clientcache wordt verwijderd om ruimte te maken voor andere inhoud.  

        -   Selecteer **Binaire differentiële replicatie inschakelen** om te aan te geven dat alleen gewijzigde bestanden worden gedistribueerd wanneer het pakket met de opstartinstallatiekopie op het distributiepunt is bijgewerkt. Deze instelling minimaliseert het netwerkverkeer tussen sites, in het bijzonder wanneer het opstartinstallatiekopie-pakket groot is en de wijzigingen relatief gering zijn.  

        -   Selecteer **Deze opstartinstallatiekopie implementeren vanaf het PXE-distibutiepunt** als de opstartinstallatiekopie wordt gebruikt in een implementatie met PXE-functionaliteit.  

            > [!NOTE]  
            >  Zie voor meer informatie [PXE gebruiken om Windows te implementeren via het netwerk](../deploy-use/use-pxe-to-deploy-windows-over-the-network.md).  

    -   Selecteer één van de volgende instellingen op het tabblad **Gegevenstoegang**:  

        -   Stel de **Instellingen van pakketshare** in als u wenst dat clients de inhoud in dit pakket installeren vanuit het netwerk.  

        -   Stel de **pakket update-instellingen** om op te geven hoe Configuration Manager gebruikers ontkoppelt van het distributiepunt. Configuration Manager kan het zijn de opstartinstallatiekopie bijwerken wanneer gebruikers gekoppeld zijn aan het distributiepunt.  

    -   Selecteer één van de volgende instellingen op het tabblad **Distributie-instellingen**:  

        -   In de **distributieprioriteit** lijst, geeft u het prioriteitsniveau op dat u wilt dat Configuration Manager moet worden gebruikt wanneer meerdere pakketten worden gedistribueerd naar hetzelfde distributiepunt.  

        -   Selecteer **De inhoud voor dit pakket distribueren naar voorkeursdistributiepunten** als u inhouddistributie op aanvraag naar voorkeursdistributiepunten wilt inschakelen. Wanneer deze instelling ingeschakeld is, distribueert het beheerpunt de inhoud naar alle voorkeurdistributiepunten wanneer een client de inhoud voor het pakket opvraagt en de inhoud niet beschikbaar is op om het even welk voorkeursdistributiepunt.  

        -   Stel de **Instellingen voorbereid distributiepunt** in om op te geven hoe u wilt de opstartinstallatiekopie gedistribueerd zien naar distributiepunten die ingeschakeld zijn voor voorbereide inhoud.  

            > [!NOTE]  
            >  Zie [Prestage content](/sccm/core/servers/deploy/configure/deploy-and-manage-content#bkmk_prestage) (Voorbereide inhoud) voor meer informatie over voorbereide inhoud.  

    -   Selecteer, op het tabblad **Content Locations**, het distributiepunt of distributiepuntgroep en voer één van de volgende acties uit:  

        -   Klik op **Herverdelen** om de opstartinstallatiekopie opnieuw te distribueren naar het geselecteerde distributiepunt of distributiepuntgroep.  

        -   Klik op **Valideer** om de integriteit te controleren van het opstartinstallatiekopiepakket op het geselecteerde distributiepunt of de geselecteerde distributiepuntgroep.  

    -   Op de **optionele onderdelen** tabblad, geeft u de onderdelen die zijn toegevoegd aan Windows PE voor gebruik met Configuration Manager. Zie voor meer informatie over beschikbare optionele onderdelen [WinPE: Pakketten (Optional Components Reference) toevoegen](https://msdn.microsoft.com/library/windows/hardware/dn938382\(v=vs.85\).aspx).  

    -   Selecteer op het tabblad **Beveiliging** een gebruiker met beheerdersrechten en wijzig de operaties die ze kunnen uitvoeren.  

6.  Klik op **OK** nadat u de eigenschappen hebt geconfigureerd.  

##  <a name="BKMK_BootImagePXE"></a>Een opstartinstallatiekopie implementeren vanaf een distributiepunt met PXE-functionaliteit configureren  
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

##  <a name="BKMK_BootImageLanguage"></a>Meerdere talen configureren voor implementatie van de opstartinstallatiekopie  
 Opstartinstallatiekopieën zijn taalonafhankelijk. Hierdoor kunt u één opstartinstallatiekopie gebruiken die de tekst van de takenreeks in meerdere talen weergeeft wanneer WinPE wordt gebruikt, als u de toepasselijke taalondersteuning uit optionele onderdelen van WinPE opneemt en de toepasselijke takenreeksvariabele zo instelt, dat deze aangeeft welke taal kan worden weergegeven. De taal van het besturingssysteem die u implementeert, is onafhankelijk van de taal die wordt weergegeven in WinPE, ongeacht de versie van Configuration Manager. De aan de gebruiker weergegeven taal wordt als volgt bepaald:  

-   Wanneer een gebruiker de takenreeks wordt uitgevoerd vanuit een bestaand besturingssysteem wordt uitgevoerd, gebruikt Configuration Manager automatisch de taal die is geconfigureerd voor de gebruiker. Wanneer de takenreeks automatisch wordt uitgevoerd als gevolg van een verplichte implementatiedeadline, wordt in Configuration Manager maakt gebruik van de taal van het besturingssysteem.  

-   U kunt voor implementaties van besturingssystemen die PXE of media gebruiken de id-waarde van de taal instellen in de variabele SMSTSLanguageFolder als onderdeel van een prestart-opdracht. Wanneer de computer wordt opgestart in WinPE, worden berichten weergegeven in de taal die u hebt opgegeven in de variabele. Als er een fout optreedt bij het openen van het bronbestand voor de taal in de opgegeven map of als u de variabele niet instelt, worden berichten in de WinPE-taal weergegeven.  

    > [!NOTE]  
    >  Wanneer de media met een wachtwoord zijn beschermd, wordt de tekst waarin de gebruiker naar het wachtwoord wordt gevraagd, altijd weergegeven in de WinPE-taal.  

 Gebruik de volgende procedure om de WinPE-taal in te stellen voor met PXE of media geïnitieerde besturingssysteemimplementaties.  

#### <a name="to-set-the-windows-pe-language-for-a-pxe-or-media-initiated-operating-system-deployment"></a>De Windows PE-taal instellen voor implementaties van door PXE of media geactiveerde besturingssystemen  

1.  Controleer of het toepasselijke bronbestand (tsres.dll) voor de takenreeks zich in de betreffende taalmap op de siteserver bevindt, voordat u de opstartinstallatiekopie bijwerkt. Het Engels bronbestand bevindt zich bijvoorbeeld op de volgende locatie:  <*ConfigMgrInstallationFolder*>\OSD\bin\x64\00000409\tsres.dll.  

2.  Als onderdeel van uw prestart-opdracht stelt u de variabele voor de SMSTSLanguageFolder-omgeving in op de juiste taal-id. De taal-id moet worden opgegeven met decimale tekens en geen hexadecimale tekens. Als u bijvoorbeeld de taal-id op Engels wilt instellen, zou u een decimale waarde 1033 moeten opgeven in plaats van de hexadecimale waarde 00000409 die wordt gebruikt voor de mapnaam.  
