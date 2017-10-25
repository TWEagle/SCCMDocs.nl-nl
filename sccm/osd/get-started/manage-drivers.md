---
title: Stuurprogramma's beheren - Configuration Manager | Microsoft Docs
description: De stuurprogrammacatalogus Configuration Manager gebruiken voor het importeren van stuurprogramma's, groep-stuurprogramma's in pakketten, en die pakketten naar distributiepunten distribueren.
ms.custom: na
ms.date: 01/27/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: configmgr-osd
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 84802d55-112e-4f7f-9a48-74a80d91a0f4
caps.latest.revision: "10"
caps.handback.revision: "0"
author: Dougeby
ms.author: dougeby
manager: angrobe
ms.openlocfilehash: 87ab9925717a307cbda3cea1f2e470ae012fa067
ms.sourcegitcommit: 51fc48fb023f1e8d995c6c4eacfda7dbec4d0b2f
ms.translationtype: HT
ms.contentlocale: nl-NL
ms.lasthandoff: 08/07/2017
---
# <a name="manage-drivers-in-system-center-configuration-manager"></a>Stuurprogramma's beheren in System Center Configuration Manager

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*

System Center Configuration Manager bevat een stuurprogrammacatalogus die u gebruiken kunt voor het beheren van de Windows-apparaatstuurprogramma's in uw Configuration Manager-omgeving. U kunt de stuurprogrammacatalogus gebruiken voor het importeren van apparaatstuurprogramma's in Configuration Manager, ze in pakketten te groeperen en te distribueren die pakketten naar distributiepunten waar u er toegang toe wanneer u een besturingssysteem implementeert. Apparaatstuurprogramma's kunnen worden gebruikt wanneer u het volledige besturingssysteem op de doelcomputer installeert en wanneer u Windows PE installeert via een opstartinstallatiekopie. Windows-apparaatstuurprogramma's bestaan uit een Setup-informatiebestand (INF-bestand) en eventuele aanvullende bestanden die vereist zijn voor ondersteuning van het apparaat. Wanneer een besturingssysteem wordt geïmplementeerd, worden de gegevens hardware- en platforminformatie voor het apparaat in Configuration Manager opgehaald uit het bijbehorende INF-bestand. Gebruik de volgende stuurprogramma's in uw Configuration Manager-omgeving beheren.

##  <a name="BKMK_DriverCategories"></a> Categorieën voor apparaatstuurprogramma's  
 Wanneer u apparaatstuurprogramma's importeert, kunt u ze toewijzen aan een categorie. Met categorieën voor apparaatstuurprogramma's kunnen apparaatstuurprogramma's die op vergelijkbare wijze worden gebruikt, samen worden gegroepeerd in de stuurprogrammacatalogus. U kunt bijvoorbeeld alle apparaatstuurprogramma's voor netwerkadapters toewijzen aan een specifieke categorie. Wanneer u vervolgens een takenreeks maakt die de stap [Stuurprogramma's automatisch toepassen](../understand/task-sequence-steps.md#BKMK_AutoApplyDrivers) bevat, kunt u een specifieke categorie apparaatstuurprogramma's opgeven. Configuration Manager scant vervolgens de hardware en selecteert de betreffende stuurprogramma's in die categorie die moeten worden geplaatst op het systeem voor Windows Setup kunnen worden gebruikt.  

##  <a name="BKMK_ManagingDriverPackages"></a> Driverpakketten  
 U kunt vergelijkbare apparaatstuurprogramma's groeperen in pakketten om de implementaties van besturingssystemen te stroomlijnen. U kunt bijvoorbeeld besluiten om voor iedere computerfabrikatn op uw netwerk een stuurprogrammapakket te maken. U kunt een stuurprogrammapakket maken op het knooppunt **Stuurprogrammapakketten** terwijl u stuurprogramma's rechtstreeks in de stuurprogrammacatalogus importeert. Nadat het stuurprogrammapakket is gemaakt, moet het worden gedistribueerd naar distributiepunten uit welke Configuration Manager-clientcomputers de stuurprogramma's installeren kunnen wanneer deze nodig zijn. Neem het volgende in overweging:  

-   Wanneer u een stuurprogrammapakket maakt, moet de bronlocatie van het pakket verwijzen naar een lege netwerkshare die door geen enkel ander stuurprogrammapakket wordt gebruikt. Bovendien moet de SMS-provider lees- en schrijfrechten voor die locatie hebben.  

-   Wanneer u apparaatstuurprogramma's aan een stuurprogrammapakket toevoegt, Configuration Manager het apparaatstuurprogramma gekopieerd naar de bronlocatie van het stuurprogramma-pakket. U kunt alleen apparaatstuurprogramma's aan een stuurprogrammapakket toevoegen die zijn geïmporteerd en ingeschakeld in de stuurprogrammacatalogus.  

-   Als u een subset van de apparaatstuurprogramma's wilt kopiëren uit een bestaand stuurprogrammapakket, maakt u een nieuw stuurprogrammapakket, voegt u de subset met apparaatstuurprogramma's toe aan het nieuwe pakket en distribueert u vervolgens het nieuwe pakket naar een distributiepunt.  

 Gebruik de volgende secties om stuurprogrammapakketten te maken en te beheren.  

###  <a name="CreatingDriverPackages"></a> Een stuurprogrammapakket maken  
 Gebruik de volgende procedure om een nieuw stuurprogrammapakket te maken.  

> [!IMPORTANT]  
>  U moet, om een stuurprogrammapakket te maken, een lege netwerkmap hebben die niet door een ander stuurprogrammapakket wordt gebruikt. In de meeste gevallen moet u een nieuwe map maken voordat u deze procedure start.  

> [!NOTE]  
>  Wanneer u takenreeksen gebruikt om stuurprogramma's te installeren, moet u stuurprogrammapakketten met minder dan 500 apparaatstuurprogramma's maken.  

 Gebruik de volgende procedure om een stuurprogrammapakket te maken.  

#### <a name="to-create-a-driver-package"></a>Een stuurprogrammapakket maken  

1.  Klik in de Configuration Manager-console op **Softwarebibliotheek**.  

2.  Vouw in de werkruimte **Softwarebibliotheek** de optie **Besturingssystemen**uit en klik vervolgens op **Stuurprogrammapakketten**.  

3.  Klik op het tabblad **Start** in de groep **Maken** op **Stuurprogrammapakket maken**.  

4.  Geef in het venster **Naam** een beschrijvende naam op voor het stuurprogrammapakket.  

5.  Geef in het venster **Opmerking** een optionele beschrijving op voor het stuurprogrammapakket. Zorg ervoor dat de beschrijving informatie geeft over de inhoud of het doel van het stuurprogrammapakket.  

6.  Geef in het vak **Pad** een lege bronmap op voor het stuurprogrammapakket. Geef het pad op van de bron map in de UNC-indeling (Universal Naming Convention). Elk stuurprogrammapakket moet een unieke map gebruiken.  

    > [!IMPORTANT]  
    >  Het siteserveraccount moet de machtigingen **Lezen** en **Schrijven** hebben voor de opgegeven bronmap.  

 Het nieuwe stuurprogrammapakket bevat geen stuurprogramma's. De volgende stap is het toevoegen van stuurprogramma's aan het pakket.  

 Als het knooppunt **Stuurprogrammapakketten** verschillende pakketten bevat, kunt u mappen toevoegen aan het knooppunt om de pakketten onder te verdelen in logische groepen.  

###  <a name="BKMK_PackageActions"></a> Aanvullende acties voor stuurprogrammapakketten  
 U kunt de volgende bewerkingen uitvoeren om stuurprogrammapakketten te beheren wanneer u een of meer stuurprogrammapakketten selecteert in het knooppunt **Stuurprogrammapakketten** . Deze acties omvatten het volgende:  

|Actie|Beschrijving|  
|------------|-----------------|  
|**Voorbereid inhoudsbestand maken**|Maakt bestanden die kunnen worden gebruikt om inhoud en de eraan gekoppelde metagegevens te importeren. Gebruik voorbereide inhoud wanneer u lage netwerkbandbreedte hebt tussen de siteserver en de distributiepunten waar het stuurprogrammapakket wordt opgeslagen.|  
|**Verwijderen**|Hiermee verwijdert u het stuurprogrammapakket uit het knooppunt **Stuurprogrammapakketten** .|  
|**Inhoud distribueren**|Distribueert het stuurprogrammapakket naar distributiepunten, distributiepuntgroepen en distributiepuntgroepen die zijn gekoppeld aan verzamelingen.|  
|**Toegangsaccounts beheren**|Hiermee worden toegangsaccounts voor het stuurprogrammapakket toegevoegd, gewijzigd of verwijderd.<br /><br /> Zie voor meer informatie over Pakkettoegangsaccounts [gebruikte Accounts in Configuration Manager](../../core/plan-design/hierarchy/accounts.md).|  
|**Verplaatsen**|Verplaatst het stuurprogrammapakket naar een andere map in het knooppunt **Stuurprogrammapakketten** .|  
|**Distributiepunten bijwerken**|Werkt het apparaatstuurprogrammapakket bij op alle distributiepunten waar het pakket wordt opgeslagen. Deze bewerking kopieert alleen de inhoud die is gewijzigd sinds de laatste keer het werd gedistribueerd.|  
|**Eigenschappen**|Opent het dialoogvenster **Eigenschappen** waar u de inhoud en eigenschappen van het apparaatstuurprogramma kunt controleren en wijzigen. U kunt bijvoorbeeld de naam en beschrijving wijzigen van het apparaatstuurprogramma, het apparaatstuurprogramma inschakelen en specificeren op welke platformen het apparaatstuurprogramma kan worden uitgevoerd.|  

##  <a name="BKMK_DeviceDrivers"></a> Apparaatstuurprogramma 's  
 U kunt apparaatstuurprogramma's installeren op doelcomputers zonder ze op te nemen in de installatiekopie van het besturingssysteem die wordt geïmplementeerd. Configuration Manager bevat een stuurprogrammacatalogus met verwijzingen naar alle apparaatstuurprogramma's die u in Configuration Manager importeert. De stuurprogrammacatalogus bevindt zich in de **softwarebibliotheek** werkruimte en bestaat uit twee knooppunten: **Stuurprogramma's** en **stuurprogrammapakketten**. Het knooppunt **Stuurprogramma's** geeft alle stuurprogramma's weer die u in de stuurprogrammacatalogus hebt geïmporteerd. Gebruik dit knooppunt om de details over elk geïmporteerd stuurprogramma te detecteren, het stuurprogrammapakket of de opstartinstallatiekopie van een stuurprogramma te wijzigen, een stuurprogramma in of uit te schakelen en meer.  

###  <a name="BKMK_ImportDrivers"></a> Apparaatstuurprogramma's in de stuurprogrammacatalogus importeren  
 U moet apparaatstuurprogramma's importeren in de stuurprogrammacatalogus voordat u ze kunt gebruiken bij het implementeren van een besturingssysteem. Voor een beter beheer van uw apparaatstuurprogramma's importeert u alleen die apparaatstuurprogramma's die u van plan bent te installeren als onderdeel van de besturingssysteemimplementatie. U kunt echter ook meerdere versies van apparaatstuurprogramma's opslaan in de stuurprogrammacatalogus, om zodoende gemakkelijk bestaande apparaatstuurprogramma's te kunnen bijwerken wanneer de apparaatvereisten voor hardware in uw netwerk veranderen.  

 Als onderdeel van het importeerproces voor het apparaatstuurprogramma, leest u de provider, klasse, versie, handtekening, Configuration Manager ondersteunde hardware en ondersteunde platforminformatie die is gekoppeld aan het apparaat. Standaard krijgt het stuurprogramma de naam van het eerste hardware-apparaat dat het ondersteunt. U kunt de naam van het apparaatstuurprogramma echter later nog wijzigen. De lijst met ondersteunde platformen is gebaseerd op de informatie in het INF-bestand van het stuurprogramma. Omdat de nauwkeurigheid van deze informatie kan variëren, dient u handmatig te verifiëren of het apparaatstuurprogramma wordt ondersteund nadat het is geïmporteerd in de stuurprogrammacatalogus.  

 Nadat u apparaatstuurprogramma's in de catalogus hebt geïmporteerd, kunt u de apparaatstuurprogramma's toevoegen aan stuurprogrammapakketten of aan opstartinstallatiekopiepakketten.  

> [!IMPORTANT]  
>  U kunt geen apparaatstuurprogramma's rechtstreeks importeren in een submap van het knooppunt **Stuurprogramma's** . U kunt een apparaatstuurprogramma importeren in een submap door het apparaatstuurprogramma eerst te importeren in het knooppunt **Stuurprogramma's** en het stuurprogramma vervolgens te verplaatsen naar de submap.  

 Gebruik de volgende procedure om Windows-apparaatstuurprogramma's te importeren.  

#### <a name="to-import-windows-device-drivers-into-the-driver-catalog"></a>Windows-apparaatstuurprogramma's importeren in de stuurprogrammacatalogus  

1.  Klik in de Configuration Manager-console op **Softwarebibliotheek**.  

2.  Vouw in de werkruimte **Softwarebibliotheek** de optie **Besturingssysteem**uit en klik vervolgens op **Stuurprogramma's**.  

3.  Klik op het tabblad **Start** in de groep **Maken** op **Stuurprogramma importeren** om de wizard **Nieuw stuurprogramma importeren**te openen.  

4.  Geef op de pagina **Stuurprogramma zoeken** de volgende opties op en klik op **Volgende**:  

    -   **Alle stuurprogramma's importeren in het volgende netwerkpad (UNC)**: Geef het netwerkpad naar de stuurprogrammamap voor het importeren van alle apparaatstuurprogramma's die zijn opgenomen in een specifieke map. Bijvoorbeeld:  **\\\servernaam\map**.  

        > [!NOTE]  
        >  Het proces voor het importeren van alle stuurprogramma's kan enige tijd in beslag nemen als er veel mappen en stuurprogrammabestanden (.inf) aanwezig zijn.  

    -   **Een specifiek stuurprogramma importeren**: Als u wilt een specifiek stuurprogramma importeren vanuit een map, geef het netwerkpad (UNC) naar het Windows-apparaatstuurprogramma. INF of mass storage bestand Txtsetup.oem van het stuurprogramma.  

    -   **Geef de optie voor dubbele stuurprogramma's**: Selecteer de gewenste Configuration Manager stuurprogrammacategorieën beheren wanneer er een gedupliceerd apparaatstuurprogramma wordt geïmporteerd.  

    > [!IMPORTANT]  
    >  Als u stuurprogramma's importeert, moet de siteserver over de machtiging **Lezen** beschikken voor de map. Het importeren mislukt als dit niet het geval is.  

5.  Geef op de pagina **Stuurprogrammagegevens** de volgende opties op en klik op **Volgende**:  

    -   **Stuurprogramma's die zich niet in een opslag- of netwerkklasse (voor installatiekopieën) verbergen**: Gebruik deze instelling om alleen opslag- en netwerkstations weer te geven en andere stuurprogramma's die doorgaans niet nodig voor installatiekopieën, zoals een video- of modemstuurprogramma zijn, te verbergen.  

    -   **Stuurprogramma's die niet digitaal zijn ondertekend verbergen**: Deze instelling gebruiken om de stuurprogramma's die niet digitaal zijn ondertekend verbergen.  

    -   Selecteer in de lijst met stuurprogramma's de stuurprogramma's die u wilt importeren naar de stuurprogrammacatalogus.  

    -   **Deze stuurprogramma's inschakelen en computers deze installeren toestaan**: Selecteer deze instelling om computers de apparaatstuurprogramma's te installeren. Standaard is dit selectievakje geselecteerd.  

        > [!IMPORTANT]  
        >  Als een apparaatstuurprogramma een probleem veroorzaakt of u wilt de installatie van een apparaatstuurprogramma uitstellen, dan kunt u het apparaatstuurprogramma uitschakelen door het selectievakje **Deze stuurprogramma's inschakelen en computers toestaan ze te installeren** uit te schakelen. U kunt ook stuurprogramma's uitschakelen nadat ze zijn geïmporteerd.  

    -   Klik op **Categorieën** en selecteer een bestaande categorie of maak een nieuwe categorie om de apparaatstuurprogramma's toe te wijzen aan een beheercategorie voor filterdoeleinden (bv. de categorieën Desktops of Notitieblokken). U kunt de categorietoewijzing ook gebruiken om te configureren welke apparaatstuurprogramma's er op de implementatie moeten worden toegepast met de takenreeksstap [Stuurprogramma's automatisch toepassen](../understand/task-sequence-steps.md#BKMK_AutoApplyDrivers).  

6.  Kies op de pagina **Stuurprogramma aan pakketten toevoegen** of u de stuurprogramma's aan een pakket wilt toevoegen en klik vervolgens op **Volgende**. Houd rekening met het volgende wanneer u de stuurprogramma's aan een pakket toevoegt:  

    -   Selecteer de stuurprogrammapakketten die worden gebruikt om de apparaatstuurprogramma's te distribueren.  

         U kunt eventueel ook op **Nieuw pakket** klikken om een nieuw stuurprogrammapakket te maken. Als u een nieuw stuurprogrammapakket maakt, moet u een netwerkshare opgeven dat niet wordt gebruikt door andere stuurprogrammapakketten.  

    -   Als het pakket al is gedistribueerd naar distributiepunten, klikt u in het dialoogvenster op **Ja** om de opstartinstallatiekopieën op distributiepunten bij te werken. U kunt geen apparaatstuurprogramma's gebruiken totdat ze naar distributiepunten worden gedistribueerd. Als u op **Nee****Distributiepunt bijwerken** uitvoeren voordat de opstartinstallatiekopie de bijgewerkte stuurprogramma's bevat. Als het stuurprogrammapakket nog nooit is gedistribueerd, klikt u op **Inhoud distribueren** in het knooppunt **Stuurprogrammapakketten**.  

7.  Kies op de pagina **Stuurprogramma aan installatiekopieën toevoegen** of u de apparaatstuurprogramma's aan bestaande opstartinstallatiekopieën wilt toevoegen en klik vervolgens op **Volgende**. Als u een opstartinstallatiekopie selecteert, moet u rekening houden met het volgende:  

    > [!NOTE]  
    >  Voeg, als best practice, alleen massaopslag- en netwerkapparaatstuurprogramma's toe aan de installatiekopieën voor implementatiescenario's van besturingssystemen.  

    -   Klik in het dialoogvenster op **Ja** om de opstartinstallatiekopieën op de distributiepunten bij te werken. U kunt geen apparaatstuurprogramma's gebruiken totdat ze naar distributiepunten worden gedistribueerd. Als u op **Nee****Distributiepunt bijwerken** uitvoeren voordat de opstartinstallatiekopie de bijgewerkte stuurprogramma's bevat. Als het stuurprogrammapakket nog nooit is gedistribueerd, klikt u op **Inhoud distribueren** in het knooppunt **Stuurprogrammapakketten** .  

    -   Configuration Manager waarschuwt u als de architectuur voor een of meer stuurprogramma's komt niet overeen met de architectuur van de opstartinstallatiekopieën die u hebt geselecteerd. Als ze niet overeenkomen, klikt u op **OK** en keert u terug naar de pagina **Stuurprogrammagegevens** om de stuurprogramma's te verwijderen die niet overeenkomen met de architectuur van de geselecteerde opstartinstallatiekopie. Als u bijvoorbeeld een x64- en x86-installatiekopie selecteert, moeten alle stuurprogramma's beide architecturen ondersteunen. Als u een x64-installatiekopie selecteert, moeten alle stuurprogramma's de x64-architectuur ondersteunen.  

        > [!NOTE]  
        >  -   De architectuur is gebaseerd op de architectuur die wordt vermeld in de .INF van de fabrikant.  
        > -   Als een stuurprogramma aangeeft dat beide architecturen worden ondersteund, kunt u het naar een van beide installatiekopieën importeren.  

    -   Configuration Manager waarschuwt u als u apparaatstuurprogramma's die geen netwerk- of opslagstuurprogramma's aan een opstartinstallatiekopie omdat in de meeste gevallen niet nodig zijn voor de installatiekopie toevoegen. Klik op **Ja** om de stuurprogramma's toe te voegen aan de opstartinstallatiekopie of op **Nee** om terug te keren en uw stuurprogrammaselectie te wijzigen.  

    -   Configuration Manager waarschuwt u als een of meer van de geselecteerde stuurprogramma's zijn niet goed zijn ondertekend. Klik op **Ja** om door te gaan en op **Nee** om terug te keren en wijzigingen aan te brengen in uw stuurprogrammaselectie.  

8.  Voltooi de wizard.  

###  <a name="BKMK_ModifyDriverPackage"></a> Beheren van apparaatstuurprogramma's in een stuurprogrammapakket  
 Gebruik de volgende procedures om de stuurprogrammapakketten en opstartinstallatiekopieën te wijzigen. Zoek de stuurprogramma's in het knooppunt **Stuurprogramma's** om apparaatstuurprogramma's toe te voegen of te verwijderen en bewerk vervolgens de pakketten of opstartinstallatiekopieën waarmee de geselecteerde stuurprogramma's zijn gekoppeld.  

#### <a name="to-modify-the-device-drivers-in-a-driver-package"></a>De apparaatstuurprogramma's in een stuurprogrammapakket wijzigen  

1.  Klik in de Configuration Manager-console op **Softwarebibliotheek**.  

2.  Vouw in de werkruimte **Softwarebibliotheek** de optie **Besturingssysteem**uit en klik vervolgens op **Stuurprogramma's**.  

3.  Selecteer de apparaatstuurprogramma's die u wilt toevoegen aan het stuurprogrammapakket in het knooppunt **Stuurprogramma's** .  

4.  Klik in de groep **Stuurprogramma** van het tabblad **Start** op **Bewerken**en klik vervolgens op **Stuurprogrammapakketten**.  

5.  Selecteer het selectievakje van de stuurprogrammapakketten waaraan u de apparaatstuurprogramma's wilt toevoegen om een apparaatstuurprogramma toe te voegen. Deselecteer het selectievakje van de stuurprogrammapakketten waaraan u de apparaatstuurprogramma's wilt toevoegen om een apparaatstuurprogramma te verwijderen.  

     Als u apparaatstuurprogramma's toevoegt die zijn gekoppeld met stuurprogrammapakketten, kunt u eventueel ook een nieuw pakket maken door te klikken op **Nieuw pakket**. Hiermee wordt het dialoogvenster **Nieuw stuurprogrammapakket** geopend.  

6.  Als het pakket al is gedistribueerd naar distributiepunten, klikt u in het dialoogvenster op **Ja** om de opstartinstallatiekopieën op distributiepunten bij te werken. U kunt geen apparaatstuurprogramma's gebruiken totdat ze naar distributiepunten worden gedistribueerd. Als u op **Nee****Distributiepunt bijwerken** uitvoeren voordat de opstartinstallatiekopie de bijgewerkte stuurprogramma's bevat. Als het stuurprogrammapakket nog nooit is gedistribueerd, klikt u op **Inhoud distribueren** in het knooppunt **Stuurprogrammapakketten**. Voordat de stuurprogramma's beschikbaar worden, moet u het stuurprogrammapakket op de distributiepunten bijwerken.  

     Klik op **OK**.  

###  <a name="BKMK_ManageDriversBootImage"></a> Apparaatstuurprogramma's in een opstartinstallatiekopie beheren  
 U kunt Windows-apparaatstuurprogramma's die zijn geïmporteerd in de stuurprogrammacatalogus, toevoegen aan opstartinstallatiekopieën. Gebruik de volgende richtlijnen wanneer u apparaatstuurprogramma's toevoegt aan een opstartinstallatiekopie:  

-   Voeg alleen apparaatstuurprogramma's voor massaopslag en netwerkadapters toe aan opstartinstallatiekopieën; andere typen stuurprogramma's zijn doorgaans namelijk niet vereist. Stuurprogramma's die niet vereist zijn, maken de opstartinstallatiekopie alleen maar onnodig groot.  

-   Voeg alleen apparaatstuurprogramma's voor Windows 10 aan een opstartinstallatiekopie toe. De vereiste versie van Windows PE is namelijk gebaseerd op Windows 10.  

-   Zorg dat u het juiste apparaatstuurprogramma gebruikt voor de architectuur van de opstartinstallatiekopie.  Voeg geen x86-apparaatstuurprogramma toe aan een x64-opstartinstallatiekopie.  

 Gebruik de volgende procedure als u apparaatstuurprogramma's aan een opstartinstallatiekopie wilt toevoegen of apparaatstuurprogramma's wilt verwijderen.  

#### <a name="to-modify-the--device-drivers-associated-with-a-boot-image"></a>Apparaatstuurprogramma's aanpassen die zijn gekoppeld aan een opstartinstallatiekopie  

1.  Klik in de Configuration Manager-console op **Softwarebibliotheek**.  

2.  Vouw in de werkruimte **Softwarebibliotheek** de optie **Besturingssysteem**uit en klik vervolgens op **Stuurprogramma's**.  

3.  Selecteer de apparaatstuurprogramma's die u wilt toevoegen aan het stuurprogrammapakket in het knooppunt **Stuurprogramma's** .  

4.  Klik in de groep **Stuurprogramma** op het tabblad **Start** op **Bewerken**en klik vervolgens op **Opstartinstallatiekopieën**.  

5.  Selecteer het selectievakje van de installatiekopie waaraan u de apparaatstuurprogramma's wilt toevoegen om een apparaatstuurprogramma toe te voegen. Deselecteer het selectievakje van de installatiekopie waaraan u de apparaatstuurprogramma's wilt toevoegen om een apparaatstuurprogramma te verwijderen.  

6.  Schakel het selectievakje **Distributiepunten bijwerken na voltooiing** uit als u de distributiepunten waar de installatiekopie wordt opgeslagen, niet wilt bijwerken. Standaard worden de distributiepunten bijgewerkt wanneer de installatiekopie wordt bijgewerkt.  

     Klik op **OK** en neem het volgende in overweging:  

    -   Klik in het dialoogvenster op **Ja** om de opstartinstallatiekopieën op de distributiepunten bij te werken. U kunt geen apparaatstuurprogramma's gebruiken totdat ze naar distributiepunten worden gedistribueerd. Als u op **Nee****Distributiepunt bijwerken** uitvoeren voordat de opstartinstallatiekopie de bijgewerkte stuurprogramma's bevat. Als het stuurprogrammapakket nog nooit is gedistribueerd, klikt u op **Inhoud distribueren** in het knooppunt **Stuurprogrammapakketten** .  

    -   Configuration Manager waarschuwt u als de architectuur voor een of meer stuurprogramma's komt niet overeen met de architectuur van de opstartinstallatiekopieën die u hebt geselecteerd. Als ze niet overeenkomen, klikt u op **OK** en keert u terug naar de pagina **Stuurprogrammagegevens** om de stuurprogramma's te verwijderen die niet overeenkomen met de architectuur van de geselecteerde opstartinstallatiekopie. Als u bijvoorbeeld een x64- en x86-installatiekopie selecteert, moeten alle stuurprogramma's beide architecturen ondersteunen. Als u een x64-installatiekopie selecteert, moeten alle stuurprogramma's de x64-architectuur ondersteunen.  

        > [!NOTE]  
        >  -   De architectuur is gebaseerd op de architectuur die wordt vermeld in de .INF van de fabrikant.  
        > -   Als een stuurprogramma aangeeft dat beide architecturen worden ondersteund, kunt u het naar een van beide installatiekopieën importeren.  

    -   Configuration Manager waarschuwt u als u apparaatstuurprogramma's die geen netwerk- of opslagstuurprogramma's aan een opstartinstallatiekopie omdat in de meeste gevallen niet nodig zijn voor de installatiekopie toevoegen. Klik op **Ja** om de stuurprogramma's toe te voegen aan de opstartinstallatiekopie of op **Nee** om terug te keren en uw stuurprogrammaselectie te wijzigen.  

    -   Configuration Manager waarschuwt u als een of meer van de geselecteerde stuurprogramma's zijn niet goed zijn ondertekend. Klik op **Ja** om door te gaan en op **Nee** om terug te keren en wijzigingen aan te brengen in uw stuurprogrammaselectie.  

7.  Klik op **OK**.  

###  <a name="BKMK_DriverActions"></a> Aanvullende acties voor apparaatstuurprogramma's  
 U kunt de volgende bewerkingen uitvoeren om apparaatstuurprogramma's te beheren wanneer u een of meer apparaatstuurprogramma's selecteert in het knooppunt **Stuurprogramma's** . Deze acties omvatten het volgende:  

|Actie|Beschrijving|  
|------------|-----------------|  
|**Categoriseren**|Wist, beheer of configureert een beheercategorie voor de geselecteerde apparaatstuurprogramma's.|  
|**Verwijderen**|Verwijdert het apparaatstuurprogramma uit het knooppunt **Stuurprogramma's** en verwijdert het stuurprogramma ook uit de gekoppelde distributiepunten.|  
|**Uitschakelen**|Zorgt ervoor dat het apparaatstuurprogramma niet kan worden geïnstalleerd. U kunt apparaatstuurprogramma's tijdelijk uitschakelen zodat Configuration Manager-clientcomputers en takenreeks ze niet kunnen installeren wanneer u besturingssystemen implementeert. **Opmerking:**  De actie uitschakelen alleen voorkomen dat stuurprogramma's worden geïnstalleerd via de takenreeksstap voor het automatisch toepassen van stuurprogramma.|  
|**Inschakelen**|Hiermee kunt Configuration Manager-clientcomputers en -takenreeksen het apparaatstuurprogramma installeren wanneer het besturingssysteem wordt geïmplementeerd.|  
|**Verplaatsen**|Verplaatst het apparaatstuurprogramma naar een andere map in het knooppunt **Stuurprogramma's** .|  
|**Eigenschappen**|Opent het dialoogvenster **Eigenschappen** waar u de eigenschappen van het apparaatstuurprogramma kunt controleren en wijzigen. U kunt bijvoorbeeld de naam en beschrijving wijzigen van het apparaatstuurprogramma, het apparaatstuurprogramma inschakelen en specificeren op welke platformen het apparaatstuurprogramma kan worden uitgevoerd.|  

##  <a name="BKMK_TSDrivers"></a> Takenreeksen gebruiken om apparaatstuurprogramma's te installeren  
 Gebruik takenreeksen om de manier waarop het besturingssysteem wordt geïmplementeerd, te automatiseren. Met elke stap in de takenreeks wordt een specifieke actie uitgevoerd, zoals de installatie van een apparaatstuurprogramma. U kunt de volgende twee stappen in een takenreeks gebruiken om apparaatstuurprogramma's te installeren terwijl u besturingssystemen implementeert:  

-   [Stuurprogramma's automatisch toepassen](../understand/task-sequence-steps.md#BKMK_AutoApplyDrivers): Deze stap kunt u automatisch vergelijken en installeren van apparaatstuurprogramma's als onderdeel van een besturingssysteem-implementatie. U kunt de stap in de takenreeks zodanig configureren dat alleen het meest overeenkomende stuurprogramma voor elk gedetecteerd hardwareapparaat wordt geïnstalleerd, of u kunt opgeven dat met de stap in de takenreeks alle compatibele stuurprogramma's voor elk gedetecteerd hardwareapparaat worden geïnstalleerd. Vervolgens laat u Windows Setup het beste stuurprogramma kiezen. Bovendien kunt u een categorie met apparaatstuurprogramma's opgeven om te beperken welke stuurprogramma's beschikbaar zijn voor deze stap.  

-   [Stuurprogrammapakket toepassen](../understand/task-sequence-steps.md#BKMK_ApplyDriverPackage): Deze stap kunt u alle apparaatstuurprogramma's in een specifiek stuurprogrammapakket beschikbaar maken voor Windows Setup. Windows Setup zoekt in de opgegeven stuurprogrammapakketten naar de vereiste apparaatstuurprogramma's. Wanneer u zelfstandige media maakt, moet u deze stap gebruiken om apparaatstuurprogramma's te installeren.  

 Wanneer u deze takenreeksstappen gebruikt, kunt u ook opgeven hoe de apparaatstuurprogramma's worden geïnstalleerd op de computer waarop u het besturingssysteem installeert. Zie voor meer informatie [beheren van takenreeksen om taken te automatiseren](../deploy-use/manage-task-sequences-to-automate-tasks.md).  

##  <a name="BKMK_InstallingDeviceDiriversTS"></a> Takenreeksen gebruiken om apparaatstuurprogramma's op computers te installeren  
 Gebruik de volgende procedure om apparaatstuurprogramma's te installeren als onderdeel van de implementatie van besturingssystemen.  

#### <a name="use-a-task-sequence-to-install-device-drivers"></a>Een takenreeks gebruiken om apparaatstuurprogramma's op computers te installeren  

1.  Klik in de Configuration Manager-console op **Softwarebibliotheek**.  

2.  Vouw **Besturingssystemen** uit in de werkruimte **Softwarebibliotheek**en klik op **Takenreeksen**.  

3.  Selecteer in het knooppunt **Takenreeksen** de takenreeks die u wilt wijzigen om het apparaatstuurprogramma te installeren. Klik vervolgens op **Bewerken**.  

4.  Ga naar de locatie waar u de stappen **Stuurprogramma** wilt toevoegen en klik op **Toevoegen**. Selecteer vervolgens **Stuurprogramma's**.  

5.  Voeg de stap **Stuurprogramma's automatisch toepassen** toe als u wilt dat de takenreeks alle apparaatstuurprogramma's of de specifieke opgegeven categorieën installeert. Geef de opties op voor de stap op het tabblad **Eigenschappen** en eventuele voorwaarden voor de stap op het tabblad **Opties** .  

     Voeg de stap **Stuurprogrammapakket toepassen** toe als u wilt dat de takenreeks alleen die apparaatstuurprogramma's van het opgegeven pakket installeert. Geef de opties op voor de stap op het tabblad **Eigenschappen** en eventuele voorwaarden voor de stap op het tabblad **Opties** .  

    > [!IMPORTANT]  
    >  U kunt op het tabblad **Opties** de optie **Deze stap uitschakelen** selecteren om de stap voor het oplossen van problemen met de takenreeks uit te schakelen.  

6.  Klik op **OK** om de takenreeks op te slaan.  

 Zie voor meer informatie over het maken van een takenreeks om een besturingssysteem te installeren, [een takenreeks maken om een besturingssysteem te installeren](../deploy-use/create-a-task-sequence-to-install-an-operating-system.md).  

##  <a name="BKMK_DriverReports"></a> Stuurprogrammabeheerrapporten  
 U kunt diverse rapporten in de rapportencategorie **Stuurprogrammabeheer** gebruiken om algemene informatie over de apparaatstuurprogramma's in de stuurprogrammacatalogus te bepalen. Zie voor meer informatie over rapporten [rapportage](../../core/servers/manage/reporting.md).
