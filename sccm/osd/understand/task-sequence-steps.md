---
title: Stappen voor takenreeksen
titleSuffix: Configuration Manager
description: Meer informatie over de stappen die u aan een takenreeks van Configuration Manager toevoegen kunt.
ms.custom: na
ms.date: 03/30/2018
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-osd
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 7c888a6f-8e37-4be5-8edb-832b218f266d
caps.latest.revision: 26
caps.handback.revision: 0
author: aczechowski
ms.author: aaroncz
manager: dougeby
ms.openlocfilehash: 53929400b983a2191e60a7d42ae84062afd44e3a
ms.sourcegitcommit: d8a4a53630351b3d677bbdc5d203e7d330472cba
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/03/2018
---
# <a name="task-sequence-steps-in-system-center-configuration-manager"></a>Stappen voor takenreeksen in System Center Configuration Manager

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*

De volgende takenreeksstappen kunnen worden toegevoegd aan een takenreeks van Configuration Manager. Zie [Edit a task sequence](../deploy-use/manage-task-sequences-to-automate-tasks.md#BKMK_ModifyTaskSequence) (Een takenreeks bewerken) voor meer informatie over het bewerken van een takenreeks.  

Voor alle takenreeksstappen gelden de volgende instellingen:

Op de **eigenschappen** tabblad:
 - **Naam**: De editor voor takenreeksen is vereist dat u een korte naam voor het beschrijven van deze stap opgeeft. Wanneer u een nieuwe stap toevoegt, wordt de editor voor takenreeksen de naam met het Type standaard. De **naam** kan niet langer zijn dan 50 tekens.
 - **Beschrijving**: Geef desgewenst meer gedetailleerde informatie over deze stap. De **beschrijving** kan niet langer zijn dan 256 tekens.
De rest van dit artikel beschrijft de overige instellingen op de **eigenschappen** tabblad voor elke takenreeksstap.

Op de **opties** tabblad:  
-   **Deze stap uitschakelen**: Deze stap wordt overgeslagen wanneer deze wordt uitgevoerd op een computer in de takenreeks wordt uitgevoerd. Het pictogram voor deze stap wordt grijs weergegeven in de takenreekseditor. 
-   **Doorgaan bij fout**: De takenreeks verder wordt uitgevoerd als er een fout optreedt tijdens het uitvoeren van de stap.  
-   **Voorwaarde toevoegen**: De takenreeks, evalueert deze voorwaardelijke instructies om te bepalen of deze de stap wordt uitgevoerd.   
De secties voor specifieke takenreeksstappen beschrijven andere mogelijke instellingen op de **opties** tabblad.



##  <a name="BKMK_ApplyDataImage"></a> Gegevensinstallatiekopie toepassen   
 Deze stap gebruiken om te kopiëren van de gegevensinstallatiekopie naar de opgegeven doelpartitie.  

 Deze stap kan alleen in Windows PE worden uitgevoerd. De taak kan niet worden uitgevoerd in een standaardbesturingssysteem. Zie voor meer informatie over de takenreeksvariabelen [Takenreeksacties](task-sequence-action-variables.md).  

Klik in de takenreekseditor op **toevoegen**, selecteer **installatiekopieën**, en selecteer **gegevensinstallatiekopie toepassen** om toe te voegen in deze stap. 

### <a name="properties"></a>Eigenschappen  
 Op de **eigenschappen** tabblad voor deze stap, configureer de instellingen die in deze sectie beschreven.  

 **Installatiekopiepakket**  
 Klik op **Bladeren** om op te geven de **Installatiekopiepakket** die wordt gebruikt door deze takenreeks. Selecteer het pakket dat u wilt installeren in het dialoogvenster **Pakket selecteren**. De bijbehorende eigenschapsinformatie voor elk bestaand installatiekopiepakket wordt weergegeven onder aan het dialoogvenster **Pakket selecteren**. Gebruik de vervolgkeuzelijst om de **Installatiekopie** te selecteren die u wilt installeren via het geselecteerde **Installatiekopiepakket**.  

> [!NOTE]  
>  Deze takenreeksactie wordt de installatiekopie beschouwd als een gegevensbestand. Deze actie wordt niet elke instelling als u wilt de opstartinstallatiekopie als een besturingssysteem.  

 **Destination**  
 Configureer een van de volgende opties:

-   **Volgende beschikbare partitie**: De volgende sequentiële partitie gebruiken die een **besturingssysteem toepassen** of **gegevensinstallatiekopie toepassen** actie in deze takenreeks niet al is geselecteerd.  

-   **Schijf en partitie opgeven**: Selecteer de **schijf** nummer (te beginnen met 0) en de **partitie** nummer (te beginnen met 1).  

-   **Logische stationsletter opgeven**: Geef de **stationsletter** die door Windows PE is toegewezen aan de partitie. Deze stationsletter kan afwijken van de stationsletter die het geïmplementeerde besturingssysteem wordt toegewezen.  

-   **Logische stationsletter opgeslagen in een variabele**: Geef de takenreeksvariabele met de stationsletter die door Windows PE is toegewezen aan de partitie. Deze variabele wordt meestal ingesteld in de sectie Geavanceerd van het **partitie-eigenschappen** in het dialoogvenster voor de **schijf formatteren en partitioneren** takenreeksactie.  

**Alle inhoud op de partitie verwijderen alvorens de installatiekopie toe te passen**  
 Hiermee geeft u de takenreeks worden alle bestanden op de doelpartitie verwijderd voordat u de installatiekopie installeert. Door de inhoud van de partitie niet te verwijderen, kan deze stap worden gebruikt om aanvullende inhoud toe te passen op een eerder gebruikte partitie.  



##  <a name="BKMK_ApplyDriverPackage"></a> Stuurprogrammapakket toepassen  
 Deze stap gebruiken voor alle stuurprogramma's in het stuurprogrammapakket te downloaden en te installeren op het Windows-besturingssysteem.

 Met de takenreeksstap **Stuurprogrammapakket toepassen** worden alle apparaatstuurprogramma's in een stuurprogrammapakket beschikbaar gemaakt voor gebruik door Windows. Toevoegen van deze stap tussen de **besturingssysteem toepassen** en **Windows en ConfigMgr installeren** stappen om de stuurprogramma's in het pakket beschikbaar voor Windows. Normaal gesproken wordt de stap **Stuurprogrammapakket toepassen** geplaatst na de takenreeksstap **Stuurprogramma's automatisch toepassen**. De takenreeksstap **Stuurprogrammapakket toepassen** is ook nuttig bij scenario's met implementatie van zelfstandige media.  

 Zorg dat vergelijkbare apparaatstuurprogramma's in een stuurprogrammapakket zijn geplaatst en distribueer deze naar de juiste distributiepunten. Nadat deze zijn gedistribueerd, kunnen Configuration Manager-clientcomputers ze installeren. Bijvoorbeeld, alle stuurprogramma's uit één fabrikant in een stuurprogrammapakket plaatsen. Vervolgens distribueert het pakket naar distributiepunten waar de bijbehorende computers toegang toe.

 De **stuurprogrammapakket toepassen** stap is nuttig voor zelfstandige media. Deze stap is ook handig als u wilt een specifieke set met stuurprogramma's installeren. Deze typen stuurprogramma's opnemen apparaten die niet in een plug en play-scan, zoals netwerkprinters gedetecteerd.  

 Deze takenreeksstap kan alleen in Windows PE worden uitgevoerd. De taak kan niet worden uitgevoerd in een standaardbesturingssysteem. Zie [Apply Driver Package Task Sequence Action Variables](task-sequence-action-variables.md#BKMK_ApplyDriverPackage) (Variabelen voor de takenreeksactie van een stuurprogrammapakket toepassen) voor meer informatie over de takenreeksvariabelen voor deze actie.  

Klik in de takenreekseditor op **toevoegen**, selecteer **stuurprogramma's**, en selecteer **stuurprogrammapakket toepassen** om toe te voegen in deze stap. 

### <a name="properties"></a>Eigenschappen  
 Op de **eigenschappen** tabblad voor deze stap, configureer de instellingen die in deze sectie beschreven.  

 **Stuurprogrammapakket**  
 Geef het stuurprogrammapakket met de benodigde apparaatstuurprogramma's op door te klikken op **Bladeren** en het dialoogvenster **Pakket selecteren** te openen. Geef een bestaand pakket op dat u beschikbaar wilt maken. De eigenschappen van het bijbehorende pakket worden aan de onderkant van het dialoogvenster weergegeven.  

 **Selecteer het stuurprogramma voor massaopslag in het pakket dat moet worden geïnstalleerd vóór de installatie op besturingssystemen ouder dan Windows Vista.**  
 Geef alle stuurprogramma's voor massaopslag die nodig zijn om een klassieke besturingssysteem te installeren.  

 **Stuurprogramma**  
 Selecteer het stuurprogramma voor massaopslag dat installeren vóór de installatie van een klassieke besturingssysteem. De vervolgkeuzelijst wordt van het opgegeven pakket gevuld.  

 **Model**  
 Geef het voor opstarten essentiële apparaat op dat nodig is voor implementaties van besturingssystemen ouder dan Windows Vista.  

 **Installatie zonder toezicht van niet-ondertekende stuurprogramma's uitvoeren op versie van Windows wanneer dit is toegestaan**  
 Deze optie kunt Windows installeren van stuurprogramma's zonder een digitale handtekening.  



##  <a name="BKMK_ApplyNetworkSettings"></a> Netwerkinstellingen toepassen   
 Deze stap gebruiken om op te geven van de netwerk- of werkgroepconfiguratie configuratie-informatie voor de doelcomputer. Deze waarden worden opgeslagen in de juiste antwoordbestand van de takenreeks wordt uitgevoerd. Windows Setup gebruikmaakt van dit antwoordbestand tijdens de **Windows en ConfigMgr installeren** in te grijpen.  

 Deze takenreeksstap kan in een standaardbesturingssysteem of in Windows PE worden uitgevoerd. Zie [Apply Network Settings Task Sequence Action Variables](task-sequence-action-variables.md#BKMK_ApplyNetworkSettings) (Variabelen voor de takenreeksacties van netwerkinstellingen toepassen) voor meer informatie over de takenreeksvariabelen voor deze actie.  

 Klik in de takenreekseditor op **toevoegen**, selecteer **instellingen**, en selecteer **netwerkinstellingen toepassen** om toe te voegen in deze stap. 

### <a name="properties"></a>Eigenschappen  
 Op de **eigenschappen** tabblad voor deze stap, configureer de instellingen die in deze sectie beschreven.  

 **Lid worden van een werkgroep**  
 Selecteer deze optie om de doelcomputer toe te voegen aan de opgegeven werkgroep. Voer de naam van de werkgroep in op de regel **Werkgroep**. Deze waarde kan worden genegeerd door de waarde die is opgenomen door de takenreeksstap **Netwerkinstellingen vastleggen**.  

 **Lid worden van een domein**  
 Selecteer deze optie om de doelcomputer toe te voegen aan het opgegeven domein. Geef het domein op of blader hiernaartoe, zoals *fabricam.com*. Geef op of blader naar een Lightweight Directory Access Protocol (LDAP)-pad voor een organisatie-eenheid. Bijvoorbeeld: *LDAP//OU=computers, DC=Fabricam.com, C=com*  

 **Account**  
 Klik op **Instellen** om een account op te geven met de vereiste machtigingen om de computer lid te laten worden van het domein. In de **Windows-gebruikersaccount** in het dialoogvenster kunt u de gebruikersnaam met de volgende notatie invoeren: **Domain\User**.  

 **Adapterinstellingen**  
 Netwerkconfiguraties opgeven voor elke netwerkadapter in de computer. Klik op **Nieuw** om het dialoogvenster **Netwerkinstellingen** te openen en geef vervolgens de netwerkinstellingen op. Als u ook de **netwerkinstellingen vastleggen** stap, de takenreeks de eerder vastgelegde instellingen toegepast op de netwerkadapter. De takenreeks de instellingen die u in deze stap opgeeft is niet van toepassing. Als de takenreeks de netwerkinstellingen niet eerder vastlegt heeft, geldt deze de instellingen die zijn opgegeven de **netwerkinstellingen toepassen** stap. De takenreeks geldt deze instellingen voor netwerkadapters in volgorde van Windows-Apparaatinventarisatie.  



##  <a name="BKMK_ApplyOperatingSystemImage"></a> Besturingssysteeminstallatiekopie toepassen  

> [!TIP]  
> Windows 10 versie 1709, vanaf bevat media meerdere edities. Bij het configureren van een takenreeks een upgradepakket voor besturingssysteem of de installatiekopie van het besturingssysteem te gebruiken, moet u selecteren een [edition ondersteund](/sccm/core/plan-design/configs/support-for-windows-10#windows-10-as-a-client).

 Deze stap gebruiken voor het installeren van een besturingssysteem op de doelcomputer. Deze stap voert acties afhankelijk van of deze gebruikmaakt van een installatiekopie van het besturingssysteem of een upgradepakket voor het besturingssysteem.  

 De **Besturingssysteeminstallatiekopie toepassen** stap worden de volgende acties uitgevoerd wanneer u een installatiekopie van besturingssysteem:  

1.  Verwijder alle inhoud op het betreffende volume, met uitzondering van bestanden in de map de &#95;SMSTSUserStatePath variabele geeft.

2.  Pak de inhoud van het opgegeven WIM-bestand naar de opgegeven doelpartitie.  

3.  Bereid het antwoordbestand:  

    1.  Maak een nieuw standaard Windows Setup-antwoordbestand (sysprep.inf of unattend.xml) voor het besturingssysteem dat wordt geïmplementeerd.  

    2.  Alle waarden van de gebruiker opgegeven antwoordbestand samengevoegd.  

4.  Kopieer Windows opstart laadprogramma's in de actieve partitie.  

5.  Het bestand boot.ini of de Boot Configuration Database (BCD) om te verwijzen naar het geïnstalleerde besturingssysteem instellen.  

 De **Besturingssysteeminstallatiekopie toepassen** stap worden de volgende acties uitgevoerd wanneer u een upgradepakket voor besturingssysteem:  

1.  Verwijder alle inhoud op het betreffende volume, met uitzondering van bestanden in de map de &#95;SMSTSUserStatePath variabele geeft.  

2.  Bereid het antwoordbestand:  

    1.  Maak een nieuw antwoordbestand met standaardwaarden gemaakt door Configuration Manager.  

    2.  Alle waarden van de gebruiker opgegeven antwoordbestand samengevoegd.  

> [!NOTE]  
>  De **Windows en ConfigMgr installeren** stap de installatie van Windows wordt gestart. 

 Na de **besturingssysteem toepassen** actie wordt uitgevoerd, de OSDTargetSystemDrive variabele is ingesteld op de stationsletter van de partitie die de besturingssysteembestanden bevat.  

 Deze takenreeksstap kan alleen in Windows PE worden uitgevoerd. De taak kan niet worden uitgevoerd in een standaardbesturingssysteem. Zie [Apply Operating System Image Task Sequence Action Variables](task-sequence-action-variables.md#BKMK_ApplyOperatingSystem) (Variabelen voor de takenreeksactie van een installatiekopie van besturingssysteem toepassen) voor meer informatie over de takenreeksvariabelen voor deze actie.  

 Klik in de takenreekseditor op **toevoegen**, selecteer **installatiekopieën**, en selecteer **Besturingssysteeminstallatiekopie toepassen** om toe te voegen in deze stap. 

### <a name="properties"></a>Eigenschappen  
 Op de **eigenschappen** tabblad voor deze stap, configureer de instellingen die in deze sectie beschreven.  

 **Besturingssysteem toepassen vanuit een vastgelegd beeld**  
 Hiermee wordt een installatiekopie van een besturingssysteem geïnstalleerd die eerder is vastgelegd. Klik op **Bladeren** om het dialoogvenster **Pakket selecteren** te openen en selecteer vervolgens het bestaande installatiekopiepakket dat u wilt installeren. Als meerdere afbeeldingen gekoppeld aan het opgegeven zijn **installatiekopiepakket**, gebruikt u de vervolgkeuzelijst om op te geven van de bijbehorende installatiekopie moet worden gebruikt voor deze implementatie. U kunt basisinformatie over elke bestaande installatiekopie weergeven door te klikken op de installatiekopie.  

 **Installatiekopie van besturingssysteem toepassen vanuit een originele installatiebron**  
 Hiermee wordt een besturingssysteem geïnstalleerd met behulp van een oorspronkelijke installatiebron. Klik op **Bladeren** openen de **selecteren en voor het besturingssysteem installeren** in het dialoogvenster. Selecteer vervolgens het bestaande besturingssysteem upgradepakket u wilt gebruiken. U kunt basisinformatie over elke bestaande installatiekopiebron weergeven door te klikken op de installatiekopiebron. De bijbehorende eigenschappen van de installatiekopie worden weergegeven in het resultatenvenster onder in het dialoogvenster. Als er meerdere edities zijn gekoppeld aan het opgegeven pakket, gebruikt u de vervolgkeuzelijst om de gebruikte bijbehorende **Editie** op te geven.  

 **Installatie zonder toezicht of sysprep-antwoordbestand gebruiken voor aangepaste installatie**  
 Gebruik deze optie om een Windows Setup-antwoordbestand op te geven (**unattend.xml**, **unattend.txt** of **sysprep.inf**), afhankelijk van de besturingssysteemversie en de installatiemethode. Het opgegeven bestand kan de standaardconfiguratieopties bevatten die worden ondersteund voor Windows-antwoordbestanden. Bijvoorbeeld: u kunt hiermee de standaardstartpagina voor Internet Explorer opgeven. Geef het pakket dat het antwoordbestand en het bijbehorende pad naar het bestand in het pakket bevat.  

> [!NOTE]  
>  Het opgegeven Windows setup-antwoordbestand die u opgeeft kan bevatten ingesloten takenreeksvariabelen de notatie %*varnaam*%, waarbij *varnaam* is de naam van de variabele. De **Windows en ConfigMgr installeren** stap vervangt de %*varnaam*% tekenreeks voor de werkelijke waarden van variabelen. Deze ingesloten takenreeksvariabelen kunnen niet worden gebruikt in velden die alleen numeriek in het antwoordbestand Unattend.XML.  

 Als u geen Windows setup-antwoordbestand opgeeft, wordt een antwoordbestand automatisch gegenereerd door deze takenreeksactie.  

 **Destination**  
 Configureer een van de volgende opties:  

-   **Volgende beschikbare partitie**: De volgende sequentiële partitie gebruiken die een **besturingssysteem toepassen** of **gegevensinstallatiekopie toepassen** actie in deze takenreeks niet al is geselecteerd. 

-   **Schijf en partitie opgeven**: Selecteer de **schijf** nummer (te beginnen met 0) en de **partitie** nummer (te beginnen met 1).  

-   **Logische stationsletter opgeven**: Geef de **stationsletter** die door Windows PE is toegewezen aan de partitie. Deze stationsletter kan afwijken van de stationsletter die het geïmplementeerde besturingssysteem wordt toegewezen.  

-   **Logische stationsletter opgeslagen in een variabele**: Geef de takenreeksvariabele met de stationsletter die door Windows PE is toegewezen aan de partitie. Deze variabele wordt meestal ingesteld in de sectie Geavanceerd van het **partitie-eigenschappen** in het dialoogvenster voor de **schijf formatteren en partitioneren** takenreeksactie.  

### <a name="options"></a>Opties  
 Naast de standaardopties te gebruiken, kunt u de volgende aanvullende instellingen configureren op de **opties** tabblad van deze takenreeksstap:  

-   **Toegang tot inhoud rechtstreeks vanaf het distributiepunt.**  
     Configureer de takenreeks voor toegang tot de besturingssysteemkopie rechtstreeks vanaf het distributiepunt. Bijvoorbeeld: Gebruik deze optie wanneer u besturingssystemen implementeert op ingesloten apparaten met opslagcapaciteit beperkte. Als u deze optie selecteert, moet u ook de pakketshare-instellingen configureren op de **gegevenstoegang** tabblad van de pakketeigenschappen.  

    > [!NOTE]  
    >  Deze instelling overschrijft de implementatiemethode die u configureert op de **distributiepunten** pagina in de **Wizard Software implementeren**. Met deze onderdrukking wordt alleen gebruikt voor de OS-installatiekopie die in deze stap wordt opgegeven, niet voor alle inhoud van takenreeksen.  



##  <a name="BKMK_ApplyWindowsSettings"></a> Windows-instellingen toepassen  
 Deze stap gebruiken voor het configureren van de Windows-instellingen voor de doelcomputer. Deze waarden worden opgeslagen in de juiste antwoordbestand van de takenreeks wordt uitgevoerd. Windows Setup gebruikmaakt van dit antwoordbestand tijdens de **Windows en ConfigMgr installeren** in te grijpen.  

 Deze takenreeksstap kan alleen in Windows PE worden uitgevoerd. De taak kan niet worden uitgevoerd in een standaardbesturingssysteem. Zie [Apply Windows Settings Task Sequence Action Variables](task-sequence-action-variables.md#BKMK_ApplyWindowsSettings) (Variabelen voor takenreeksacties van Windows-instellingen toepassen) voor meer informatie over de takenreeksvariabelen voor deze actie.  

 Klik in de takenreekseditor op **toevoegen**, selecteer **instellingen**, en selecteer **Windows-instellingen toepassen** om toe te voegen in deze stap. 

### <a name="properties"></a>Eigenschappen  
 Op de **eigenschappen** tabblad voor deze stap, configureer de instellingen die in deze sectie beschreven.  

 **Gebruikersnaam**  
 Geef de naam op van de geregistreerde gebruikersnaam die is gekoppeld aan de doelcomputer. Deze waarde kan worden genegeerd door de waarde die is opgenomen door de takenreeksactie **Windows-instellingen vastleggen**.  

 **De naam van organisatie**  
 Geef de naam op van de geregistreerde organisatienaam die is gekoppeld aan de doelcomputer. Deze waarde kan worden genegeerd door de waarde die is opgenomen door de takenreeksactie **Windows-instellingen vastleggen**.  

 **Productcode**  
 Geef de productcode op die wordt gebruikt voor de installatie van Windows op de doelcomputer.  

 **Server-licentieverlening**  
 Geef de serverlicentiemodus op. U kunt **Per server** of **Per gebruiker** selecteren als licentiemodus. Als u selecteert **Per server**, ook het maximum aantal verbindingen dat wordt toegestaan conform uw licentieovereenkomst opgeven. Selecteer **Niet opgeven** als de doelcomputer geen server is of als u de licentiemodus niet wilt opgeven.  

 **Maximum aantal verbindingen**  
 Geef het maximumaantal beschikbare verbindingen voor deze computer op zoals vermeld in de gebruiksrechtovereenkomst.  

 **Willekeurig wachtwoord genereren voor lokale beheerder en het account uitschakelen op alle ondersteunde platforms (aanbevolen)**  
 Selecteer deze optie om het lokale administrator-wachtwoord instellen naar een willekeurig gegenereerde tekenreeks. Deze optie schakelt ook het lokale beheerdersaccount op platforms die ondersteuning bieden voor deze mogelijkheid.  

 **Het account inschakelen en lokaal beheerderswachtwoord instellen**  
 Selecteer deze optie om in te schakelen van het lokale administrator-account met het opgegeven wachtwoord. Voer het wachtwoord in op de regel **Wachtwoord** en bevestig het wachtwoord op de regel **Wachtwoord bevestigen**.  

 **Time Zone**  
 Geef de tijdzone op die u wilt configureren op de doelcomputer. Deze waarde kan worden genegeerd door de waarde die is opgenomen door de takenreeksstap **Windows-instellingen vastleggen**.  



##  <a name="BKMK_AutoApplyDrivers"></a> Stuurprogramma's automatisch toepassen  
 Deze stap gebruiken om te zoeken en installeren van stuurprogramma's als onderdeel van de implementatie van besturingssystemen.  

 Met de takenreeksactie **Stuurprogramma's automatisch toepassen** worden de volgende acties uitgevoerd:  

1.  Scan de hardware en het vinden van de plug en play-id's voor alle aanwezige apparaten in het systeem.  

2.  De lijst met apparaten en hun plug en play-id's naar het beheerpunt verzenden. Het beheerpunt wordt een lijst met compatibele stuurprogramma's uit de stuurprogrammacatalogus voor elk apparaat. De lijst bevat alle stuurprogramma's, ongeacht het stuurprogrammapakket waartoe ze, stuurprogramma's gemarkeerd met de opgegeven stuurprogrammacategorie en stuurprogramma's zijn niet uitgeschakeld.  

3.  Voor elk apparaat kiest de takenreeks het beste stuurprogramma. Dit stuurprogramma geschikt is voor het geïmplementeerde besturingssysteem en zich op een toegankelijk distributiepunt bevindt.  

4.  De takenreeks de geselecteerde stuurprogramma's worden gedownload vanaf een distributiepunt en bereidt de stuurprogramma's op het doelbesturingssysteem.  

    1.  Voor installaties op basis van een installatiekopie, wordt de takenreeks de stuurprogramma's in het stuurprogramma-archief van het besturingssysteem geplaatst.  

    2.  Voor installaties op basis van setup configureert de takenreeks Windows Setup met locatie van de stuurprogramma's.  

5.  Tijdens de **Windows en ConfigMgr installeren** stap in de takenreeks, wordt Windows Setup zoekt de stuurprogramma's gezocht die door deze actie voorgefaseerd.  

> [!IMPORTANT]
>  Zelfstandige media niet gebruiken de **stuurprogramma's automatisch toepassen** stap. Windows Setup heeft geen verbinding met de Configuration Manager-site in dit scenario.

Deze takenreeksstap kan alleen in Windows PE worden uitgevoerd. De taak kan niet worden uitgevoerd in een standaardbesturingssysteem. Zie [Auto Apply Drivers Task Sequence Action Variables](task-sequence-action-variables.md#BKMK_AutoApplyDrivers) (Variabelen voor de takenreeksactie van een stuurprogramma automatisch toepassen) voor meer informatie over de takenreeksvariabelen voor deze actie.  

 Klik in de takenreekseditor op **toevoegen**, selecteer **stuurprogramma's**, en selecteer **stuurprogramma's automatisch toepassen** om toe te voegen in deze stap. 

### <a name="properties"></a>Eigenschappen  
 Op de **eigenschappen** tabblad voor deze stap, configureer de instellingen die in deze sectie beschreven.  

 **Installeer alleen de best overeenkomende compatibele stuurprogramma 's**  
 Hiermee geeft u aan dat met de takenreeksstap alleen het beste overeenkomende stuurprogramma voor elk gedetecteerd apparaat wordt geïnstalleerd.  

 **Alle compatibele stuurprogramma's installeren**  
 Alle stuurprogramma's compatibel voor elk gedetecteerd hardwareapparaat wordt geïnstalleerd door de takenreeks wordt uitgevoerd. Windows Setup kiest het beste stuurprogramma. Deze optie vereist meer netwerkbandbreedte en schijfruimte ruimte. De takenreeks meer stuurprogramma's worden gedownload, maar Windows een beter stuurprogramma kunt selecteren.  

 **Stuurprogramma's uit alle categorieën overwegen**  
 De takenreeks doorzoekt alle beschikbare stuurprogrammacategorieën naar de juiste apparaatstuurprogramma's.  

 **Zoeken naar passende stuurprogramma's tot bepaalde categorieën beperken**  
 De takenreeks wordt gezocht in de opgegeven stuurprogrammacategorieën naar de juiste apparaatstuurprogramma's.  

 **Installatie zonder toezicht van niet-ondertekende stuurprogramma's op versies van Windows wanneer dit is toegestaan**  
 Deze optie kunt Windows installeren van stuurprogramma's zonder een digitale handtekening.   

  > [!IMPORTANT]  
  >  Deze optie is niet van toepassing op besturingssystemen waarin u beleid voor handtekeningverificatie niet configureren.  



##  <a name="BKMK_CaptureNetworkSettings"></a> Netwerkinstellingen vastleggen  
 Deze stap gebruiken om vast te leggen van de Microsoft-netwerkinstellingen van de computer waarop de takenreeks wordt uitgevoerd. De takenreeks worden deze instellingen opgeslagen in takenreeksvariabelen. Deze instellingen overschrijven de standaardinstellingen die u configureert op de **netwerkinstellingen toepassen** stap.  

 Deze takenreeksstap kan alleen in een standaardbesturingssysteem worden uitgevoerd. De stap kan niet worden uitgevoerd in Windows PE. Zie [Capture Network Settings Task Sequence Action Variables](task-sequence-action-variables.md#BKMK_CaptureNetworkSettings) (Variabelen voor takenreeksactie van netwerkinstellingen vastleggen) voor meer informatie over de takenreeksvariabelen voor deze actie.  

Klik in de takenreekseditor op **toevoegen**, selecteer **instellingen**, en selecteer **netwerkinstellingen vastleggen** om toe te voegen in deze stap. 

### <a name="properties"></a>Eigenschappen  
 Op de **eigenschappen** tabblad voor deze stap, configureer de instellingen die in deze sectie beschreven.  

 **Lidmaatschap van domein en werkgroep migreren**  
 Hiermee worden de lidmaatschapsgegevens van het domein en de werkgroep van de doelcomputer vastgelegd.  

 **Netwerkadapterconfiguratie migreren**  
 Hiermee wordt de netwerkadapterconfiguratie van de doelcomputer vastgelegd. De vastgelegde informatie bevat de globale netwerkinstellingen, het aantal netwerkadapters en de netwerkinstellingen van elke adapter. Deze instellingen hebben betrekking op DNS, WINS, IP en poortfilters.  



##  <a name="BKMK_CaptureOperatingSystemImage"></a> Besturingssysteeminstallatiekopie vastleggen  
 Deze stap legt een of meer installatiekopieën van een referentiecomputer vast. De takenreeks maakt een Windows-installatiekopiebestand (WIM)-bestand op de opgegeven netwerkshare. Gebruik vervolgens de **Installatiekopiepakket voor besturingssysteem toevoegen** wizard voor het importeren van deze installatiekopie in Configuration Manager voor implementaties van besturingssystemen op basis van installatiekopieën.  

 Configuration Manager wordt elk volume (station) van de referentiecomputer vastgelegd op een afzonderlijke installatiekopie binnen het .wim-bestand. Als de computer waarnaar wordt verwezen meerdere volumes heeft, bevat het resulterende .wim-bestand een afzonderlijke installatiekopie voor elk volume. Alleen volumes die zijn geformatteerd als NTFS of FAT32 worden vastgelegd. Volumes met andere formatteringen en USB-volumes worden overgeslagen.  

 Het geïnstalleerde besturingssysteem op de referentiecomputer moet een versie van Windows die ondersteuning biedt voor Configuration Manager. Gebruik het hulpprogramma SysPrep voor het voorbereiden van het besturingssysteem van de referentie-computer. Het geïnstalleerde besturingssysteemvolume en het opstartvolume moeten hetzelfde volume zijn.  

 Geef een account met schrijfmachtigingen in voor de geselecteerde netwerkshare.  

 Deze takenreeksstap kan alleen in Windows PE worden uitgevoerd. De taak kan niet worden uitgevoerd in een standaardbesturingssysteem. Zie [Capture Operating System Image Task Sequence Action Variables](task-sequence-action-variables.md#BKMK_CaptureOperatingSystemImage) (Variabelen voor de takenreeksactie van een installatiekopie van het besturingssysteem vastleggen) voor meer informatie over de takenreeksvariabelen voor deze actie.  

 Klik in de takenreekseditor op **toevoegen**, selecteer **installatiekopieën**, en selecteer **Besturingssysteeminstallatiekopie vastleggen** om toe te voegen in deze stap. 

### <a name="properties"></a>Eigenschappen  
 Op de **eigenschappen** tabblad voor deze stap, configureer de instellingen die in deze sectie beschreven.  

 **doel**  
 Systeem bestandspad naar de locatie die Configuration Manager gebruikt bij het opslaan van de vastgelegde besturingssysteeminstallatiekopie.  

 **Beschrijving**  
 Een optionele, door de gebruiker gedefinieerde beschrijving van de vastgelegde besturingssysteeminstallatiekopie die is opgeslagen in het .wim-bestand.  

 **Versie**  
 Een optioneel, door de gebruiker gedefinieerd versienummer om toe te wijzen aan de vastgelegde besturingssysteeminstallatiekopie. Deze waarde kan een combinatie van letters en cijfers zijn en wordt opgeslagen in het .wim-bestand.  

 **Gemaakt door**  
 De optionele naam van de gebruiker die de installatiekopie van het besturingssysteem heeft gemaakt, die is opgeslagen in het .wim-bestand.  

 **Account besturingssysteeminstallatiekopie vastleggen**  
 U moet het Windows-account invoeren dat machtigingen heeft voor de netwerkshare die u hebt opgegeven. Klik op **Instellen** om de naam van het Windows-account op te geven.  



##  <a name="BKMK_CaptureUserState"></a> Gebruikersstatus vastleggen  
 Gebruik deze stap User State Migration Tool (USMT) om vast te leggen van de gebruikersstatus en instellingen van de computer waarop de takenreeks wordt uitgevoerd. Deze takenreeksstap wordt gebruikt in combinatie met de takenreeksstap **Gebruikersstatus herstellen**. In USMT 3.0.1 en hoger wordt met deze optie altijd de USMT-Statusopslag versleuteld met een versleutelingssleutel die wordt gegenereerd en beheerd door Configuration Manager.  

 Zie voor meer informatie over het beheren van de gebruikersstatus bij het implementeren van besturingssystemen, [Gebruikersstatus beheren](../get-started/manage-user-state.md).  

 Als u wilt opslaan en herstellen van gebruikersinstellingen voor de status van een statusmigratiepunt, gebruikt de **gebruikersstatus vastleggen** stap met het **Statusopslag opvragen** en **Statusopslag vrijgeven** stappen.  

 De takenreeksstap **Gebruikerstoestand vastleggen** biedt controle over een beperkte subset van de meest gebruikte USMT-opties. Aanvullende opdrachtregelopties kunnen worden opgegeven met de takenreeksvariabele OSDMigrateAdditionalCaptureOptions.  

 Deze takenreeksstap kan alleen in Windows PE worden uitgevoerd. De taak kan niet worden uitgevoerd in een standaardbesturingssysteem. Zie [Capture User State Task Sequence Action Variables](task-sequence-action-variables.md#BKMK_CaptureUserState) (Variabelen voor de takenreeksactie van gebruikersstatus vastleggen) voor meer informatie over de takenreeksvariabelen voor deze actie.  

 Klik in de takenreekseditor op **toevoegen**, selecteer **gebruikersstatus**, en selecteer **gebruikersstatus vastleggen** om toe te voegen in deze stap. 

### <a name="properties"></a>Eigenschappen  
 Op de **eigenschappen** tabblad voor deze stap, configureer de instellingen die in deze sectie beschreven.  

 **Gebruiker pakket migratieprogramma gebruikersstatus**  
 Geef het pakket met User State Migration Tool (USMT). De takenreeks maakt gebruik van deze versie van USMT om vast te leggen van de gebruikersstatus en instellingen. Voor dit pakket is geen programma vereist. Geef een pakket op met de 32-bits of 64-bits versie van USMT. De architectuur van USMT is afhankelijk van de architectuur van het besturingssysteem waarvan de takenreeks status is vastlegt.  

 **Alle gebruikersprofielen vastleggen met standaardopties**  
 Alle gebruikersprofielgegevens worden gemigreerd. Dit is de standaardoptie.  

 Als u deze optie selecteert, maar niet selecteert **gebruikersprofielen lokale computer herstellen** in de **gebruikersstatus herstellen** stap, de takenreeks mislukt. Configuration Manager niet kan de nieuwe accounts migreren zonder wachtwoorden toewijzen. 

 Wanneer u gebruikt de **bestaand installatiekopiepakket installeren** optie van de **nieuwe Takenreeks** wizard de resulterende takenreeks standaard ingesteld op **alle gebruikersprofielen vastleggen met standaardopties**. Deze takenreeks standaard heeft niet de optie voor **gebruikersprofielen lokale computer herstellen**, met andere woorden, gebruikersaccounts niet van het domein.  

 Selecteer **Gebruikersprofielen lokale computer herstellen** en geef een wachtwoord op voor het account dat wordt gemigreerd. In een handmatig gemaakte takenreeks is deze instelling te vinden onder de stap Gebruikersstatus herstellen. In een takenreeks die is gemaakt door de wizard **Nieuwe takenreeks maken** is deze instelling te vinden op de wizardpagina voor de stap **Gebruikersbestanden en -instellingen herstellen**.  

 Als u geen lokale gebruikersaccounts hebt, is deze instelling niet van toepassing.  

 **Vastleggen van gebruikersprofielen aanpassen**  
 Selecteer deze optie om migratie van een aangepast profielbestand op te geven. Klik op **Bestanden** om de configuratiebestanden voor USMT te selecteren die u wilt gebruiken bij deze stap. Geef een aangepast .xml-bestand bevat regels waarmee de te migreren gebruikersstatusbestanden worden gedefinieerd.  

 **Klik hier om configuratiebestanden te selecteren:**  
 Selecteer deze optie om de configuratiebestanden in het USMT-pakket te selecteren die u wilt gebruiken voor het vastleggen van gebruikersprofielen. Klik op de knop **Bestanden** om het dialoogvenster **Configuratiebestanden** te openen. Geef een configuratiebestand op door de naam van het bestand in te voeren op de regel **Bestandsnaam** en te klikken op de knop **Toevoegen**.  

 **Uitgebreide logboekregistratie inschakelen**  
 Schakel deze optie in om meer gedetailleerde informatie in het logboekbestand te genereren. Bij het vastleggen van status, de takenreeks standaard ScanState.log gegenereerd in de logboekmap takenreeks, \windows\system32\ccm\logs.   

 **SKIP-bestanden met encrypted file system**  
 Schakel deze optie om over te slaan vastleggen bestanden versleuteld met de versleuteld File System (EFS). Deze bestanden bevatten Gebruikersprofielbestanden. Afhankelijk van het besturingssysteem en de USMT-versie zijn versleutelde bestanden mogelijk niet leesbaar na herstel. Zie de USMT-documentatie voor meer informatie.  

 **Kopiëren door toegang tot bestandssysteem**  
 Schakel deze optie in om een van de volgende instellingen op te geven:  

-   **Doorgaan als sommige bestanden niet kunnen worden vastgelegd**: Schakel deze instelling om door te gaan van het migratieproces, zelfs als sommige bestanden kunnen niet worden vastgelegd. Als u deze optie is uitgeschakeld als een bestand kan niet worden vastgelegd terwijl deze stap mislukt. Deze optie is standaard ingeschakeld.  

-   **Lokaal vastleggen met koppelingen in plaats van door bestanden te kopiëren**: Schakel deze instelling om vaste NTFS-koppelingen te leggen van bestanden.  

     Voor meer informatie over het migreren van gegevens met vaste koppelingen raadpleegt u [Hard-Link Migration Store](http://go.microsoft.com/fwlink/p/?LinkId=240222)  

-   **Vastleggen in offline modus (alleen Windows PE)**: Schakel deze instelling om vast te leggen van de status van de gebruiker in Windows PE in plaats van het volledige besturingssysteem.  
    
**Vastleggen met Volume Copy Shadow service (VSS)**  
 Met deze optie kunt u bestanden vastleggen, zelfs als deze door een andere toepassing voor bewerking zijn vergrendeld.  



##  <a name="BKMK_CaptureWindowsSettings"></a> Windows-instellingen vastleggen  
 Deze stap gebruiken om vast te leggen van de Windows-instellingen van de computer waarop de takenreeks wordt uitgevoerd. De takenreeks worden deze instellingen opgeslagen in takenreeksvariabelen. Deze vastgelegde instellingen overschrijven de standaardinstellingen die u configureert op de **Windows-instellingen toepassen** stap.  

 Deze takenreeksstap kan in Windows PE of een standaardbesturingssysteem worden uitgevoerd. Zie [Capture Windows Settings Task Sequence Action Variables](task-sequence-action-variables.md#BKMK_CaptureWindowsSettings) (Variabelen voor takenreeksacties van Windows-instellingen vastleggen) voor meer informatie over de takenreeksvariabelen voor deze actie.  

 Klik in de takenreekseditor op **toevoegen**, selecteer **instellingen**, en selecteer **Windows-instellingen vastleggen** om toe te voegen in deze stap. 

### <a name="properties"></a>Eigenschappen  
 Op de **eigenschappen** tabblad voor deze stap, configureer de instellingen die in deze sectie beschreven.  

 **Computernaam migreren**  
 De NetBIOS-computernaam van de computer vastleggen.  

 **Geregistreerde namen van gebruikers en organisaties migreren**  
 De geregistreerde gebruiker en organisatie van de namen van de computer vastleggen.  

 **Tijdzone migreren**  
 De tijdzone op de computer vastleggen.  



##  <a name="BKMK_CheckReadiness"></a> Gereedheid controleren  
 Deze stap gebruiken om te controleren of de doelcomputer voldoet aan de gespecificeerde implementatievereistevoorwaarden.  

Klik in de takenreekseditor op **toevoegen**, selecteer **algemene**, en selecteer **gereedheid controleren** om toe te voegen in deze stap. 

### <a name="properties"></a>Eigenschappen  
 Op de **eigenschappen** tabblad voor deze stap, configureer de instellingen die in deze sectie beschreven.  

 **Minimumgeheugen garanderen (MB)**  
 Controleer of de hoeveelheid geheugen in megabytes (MB), voldoet aan de opgegeven hoeveelheid. De stap kunt u deze instelling standaard ingeschakeld.  

 **Minimale processorsnelheid garanderen (MHz)**  
 Controleer of de snelheid van de processor, in megahertz (MHz), voldoet aan de opgegeven hoeveelheid. De stap kunt u deze instelling standaard ingeschakeld.  

 **Zorg ervoor dat de minimale vrije schijfruimte (MB)**  
 Controleer of de hoeveelheid vrije schijfruimte, in megabytes (MB) voldoet aan de opgegeven hoeveelheid.  

 **Zorg ervoor dat de huidige OET worden vernieuwd**  
 Controleer of het besturingssysteem geïnstalleerd op de doelcomputer voldoet aan de opgegeven vereisten. De stap wordt deze ingesteld op **CLIENT** standaard.  

### <a name="options"></a>Opties
 > [!NOTE]  
 > Als u inschakelt de **Doorgaan bij fout** instellen op de **opties** tabblad van deze stap wordt alleen de resultaten van de gereedheid van de gelogd. Als een controle mislukt, wordt de takenreeks niet gestopt.



##  <a name="BKMK_ConnectToNetworkFolder"></a> Verbinding maken met netwerkmap  
 Deze stap gebruiken voor het maken van een verbinding met een gedeelde netwerkmap.  

 Deze takenreeksstap kan in een standaardbesturingssysteem of in Windows PE worden uitgevoerd. Zie [Connect to Network Folder Task Sequence Action Variables](task-sequence-action-variables.md#BKMK_ConnecttoNetworkFolder) (Variabelen voor takenreeksacties voor verbinden met netwerkmap) voor meer informatie over de takenreeksvariabelen voor deze actie.  

 Klik in de takenreekseditor op **toevoegen**, selecteer **algemene**, en selecteer **netwerkmap verbinding** om toe te voegen in deze stap. 

### <a name="properties"></a>Eigenschappen  
 Op de **eigenschappen** tabblad voor deze stap, configureer de instellingen die in deze sectie beschreven.  

 **Path**  
 Klik op **Bladeren** het netwerkpad voor de map opgeven. Gebruik de notatie  *\\\server\share*.

 **Station**  
 Selecteer op de lokale stationsletter toe te wijzen voor deze verbinding. 

 **Account**  
 Klik op **ingesteld** om op te geven van het gebruikersaccount met machtigingen voor het verbinding maken met deze netwerkmap.



##  <a name="BKMK_DisableBitLocker"></a> Disable BitLocker  
 Deze stap uitschakelen van de BitLocker-versleuteling op het huidige besturingssysteemstation of op een specifiek station gebruiken. Met deze actie blijven de sleutelbeveiligingen in niet-versleutelde tekst achter op de harde schijf, maar wordt de inhoud van het station niet ontsleuteld. Deze actie wordt vervolgens bijna onmiddellijk voltooid.  

> [!NOTE]  
>  BitLocker-stationsversleuteling biedt versleuteling op laag niveau van de inhoud van een schijfvolume.  

 Als er meerdere stations zijn versleuteld, moet u BitLocker uitschakelen op alle gegevensstations voordat u BitLocker uitschakelt op het besturingssysteemstation.  

 Deze stap kan alleen in een standaardbesturingssysteem worden uitgevoerd. De stap kan niet worden uitgevoerd in Windows PE.  

 Klik in de takenreekseditor op **toevoegen**, selecteer **schijven**, en selecteer **BitLocker uitschakelen** om toe te voegen in deze stap. 

### <a name="properties"></a>Eigenschappen  
 Op de **eigenschappen** tabblad voor deze stap, configureer de instellingen die in deze sectie beschreven.  

 **Huidig besturingssysteemstation**  
 Hiermee wordt BitLocker uitgeschakeld op het huidige besturingssysteemstation.  

 **Specifiek station**  
 Hiermee wordt BitLocker uitgeschakeld op een specifiek station. Gebruik de vervolgkeuzelijst om het station op te geven waarop BitLocker wordt uitgeschakeld.  



##  <a name="BKMK_DownloadPackageContent"></a> Pakketinhoud downloaden  
 Deze stap gebruiken om een van de volgende pakkettypen te downloaden:  

-   Installatiekopieën van besturingssysteem  

-   Upgradepakketten voor besturingssysteem  

-   Driverpakketten  

-   Pakketten  

-   Installatiekopieën
    
Deze stap werkt goed in een takenreeks om een besturingssysteem in de volgende scenario's te werken:  

-   Een enkele takenreeks gebruiken voor een upgrade die voor zowel x86- als x64-platforms werkt. Voegt u twee **pakketinhoud downloaden** stappen in de **voorbereiden voor Upgrade** groep. Voorwaarden opgeven op de **opties** tabblad de clientarchitectuur te detecteren en alleen het geschikte OS-upgradepakket downloaden. Configureer elke **pakketinhoud downloaden** stap dezelfde variabele te gebruiken. Gebruik de variabele voor het mediumpad in de **besturingssysteem bijwerken** stap.  

-   Als u een geschikt stuurprogrammapakket wilt downloaden, gebruikt u twee **Pakketinhoud downloaden**-stappen op voorwaarde dat het juiste hardwaretype wordt gedetecteerd voor elk stuurprogrammapakket. Configureer elke **pakketinhoud downloaden** stap dezelfde variabele te gebruiken. Gebruik de variabele voor de **tijdelijke inhoud** waarde in de sectie met stuurprogramma's van de **besturingssysteem bijwerken** stap.  

> [!NOTE]    
> Wanneer u een takenreeks die de pakketinhoud downloaden stap bevat implementeert, schakel niet **alle inhoud lokaal downloaden voordat de takenreeks wordt gestart** of **rechtstreeks vanaf een distributiepunttoegangtotinhoud** voor **implementatieopties** op de **distributiepunten** pagina van de Wizard Software implementeren.  

Deze stap kan in een standaardbesturingssysteem of in Windows PE worden uitgevoerd. De optie voor het pakket opslaan in de Configuration Manager-clientcache wordt echter niet ondersteund in WinPE.

 Klik in de takenreekseditor op **toevoegen**, selecteer **Software**, en selecteer **pakketinhoud downloaden** om toe te voegen in deze stap. 

### <a name="properties"></a>Eigenschappen  
 Op de **eigenschappen** tabblad voor deze stap, configureer de instellingen die in deze sectie beschreven.  

 Pictogram **Pakket selecteren**  
 Klik op het pictogram om het pakket te selecteren dat u wilt downloaden. Nadat u een pakket hebt geselecteerd, kunt u nog een keer op het pictogram klikken om een ander pakket te kiezen.  

 **De volgende locatie plaatsen**  
 U kunt het pakket op een van de volgende locaties opslaan:  

 -   **Werkmap voor takenreeksen**  

 -   **Configuration Manager-clientcache**: Gebruik deze optie voor het opslaan van de inhoud in de clientcache. De client fungeert als peer-cachebron voor andere peer-cacheclients. Zie voor meer informatie [voorbereiden Windows PE-peer-cache om WAN-verkeer te beperken](../get-started/prepare-windows-pe-peer-cache-to-reduce-wan-traffic.md).  

 -    **Aangepast pad**: Met deze optie de engine voor takenreeksen eerst downloadt het pakket aan de takenreeks met de werkmap vervolgens verplaatst naar dit pad dat u opgeeft. De engine voor takenreeksen voegt het pad tussen de pakket-ID. 
   
**Pad opslaan als een variabele**  
 U kunt het pad opslaan als een variabele die u in een andere takenreeksstap kunt gebruiken. Configuration Manager voegt een numeriek achtervoegsel aan de variabelenaam toe. Bijvoorbeeld, als u een variabele van % opgeven*mycontent*% als aangepaste variabele, is de hoofdmap waar de inhoud alle waarnaar wordt verwezen door de takenreeks worden opgeslagen. Deze inhoud kan meerdere pakketten bevatten. Wanneer u naar de variabele verwijst, voegt u een numeriek achtervoegsel. Bijvoorbeeld: voor het eerste pakket verwijzen naar %*mycontent01*%. Als u verwijst naar de variabele in de volgende stappen zoals **besturingssysteem bijwerken**, gebruikt u %*mycontent02*% of %*mycontent03*%, waarbij het nummer overeenkomt met de volgorde die de **pakketinhoud downloaden** stap hier worden de pakketten.  

**Als het downloaden van een pakket mislukt, doorgaan met downloaden van andere pakketten in de lijst**  
 Als de takenreeks mislukt om een pakket te downloaden, begint het downloaden van het volgende pakket in de lijst.  



##  <a name="BKMK_EnableBitLocker"></a> Enable BitLocker  
Deze stap gebruiken om in te schakelen van BitLocker-versleuteling op ten minste twee partities op de harde schijf. De eerste actieve partitie bevat de Windows-bootstrapcode. Een andere partitie bevat het besturingssysteem. De bootstrappartitie moet onversleuteld blijven.  

Gebruik de takenreeksstap **BitLocker vooraf inrichten** om BitLocker in Windows PE in te schakelen op een station. Zie voor meer informatie de [BitLocker vooraf inrichten](#BKMK_PreProvisionBitLocker) sectie.  

> [!NOTE]  
>  BitLocker-stationsversleuteling biedt versleuteling op laag niveau van de inhoud van een schijfvolume.  

De stap **BitLocker inschakelen** kan alleen in een standaardbesturingssysteem worden uitgevoerd. De stap kan niet worden uitgevoerd in Windows PE. Zie [Variabelen voor takenreeksacties van BitLocker inschakelen](task-sequence-action-variables.md#BKMK_EnableBitLocker) voor meer informatie over de takenreeksvariabelen voor deze actie.  

Wanneer u opgeeft **alleen TPM**, **TPM en opstartsleutel op USB**, of **TPM en PINCODE**, Trusted Platform Module (TPM) moet in de volgende status voordat u kunt de uitvoeren **BitLocker inschakelen** stap:  

-   Ingeschakeld  
-   Geactiveerd  
-   Eigendom toegestaan  
   
Deze stap is voltooid voor elke resterende TPM-initialisatie. De resterende stappen geen fysieke aanwezigheid vereist of opnieuw wordt opgestart. De **BitLocker inschakelen** stap de resterende TPM-initialisatiestappen transparant is voltooid indien nodig:  

-   Goedkeuringssleutelpaar maken  
-   Eigenaarautorisatiewaarde en escrow maken voor Active Directory, dat moet zijn uitgebreid ter ondersteuning van deze waarde  
-   Eigenaar worden  
-   De opslaghoofdsleutel maken of opnieuw instellen als deze al aanwezig maar niet-compatibel is  
   
Als u wilt dat de takenreeks moet worden gewacht op de **BitLocker inschakelen** stap voor het voltooien van de stationsversleuteling en selecteer vervolgens de **wacht** optie. Als u geen selecteert de **wacht** optie, de stationsversleuteling wordt op de achtergrond. De takenreeks voortgezet onmiddellijk naar de volgende stap.  

BitLocker kan worden gebruikt voor het versleutelen van meerdere stations op een computersysteem (zowel het besturingssysteemstation als gegevensstations). Voor het versleutelen van een gegevensstation moet eerst het besturingssysteemstation te versleutelen en versleuteling te voltooien. Deze vereiste is omdat de sleutelbeveiligingen voor de gegevensstations worden opgeslagen door het besturingssysteemstation. Als u het besturingssysteem versleutelen en gegevensstations in dezelfde taakvolgorde, selecteert de **wacht** kiezen op de **BitLocker inschakelen** stap voor het besturingssysteemstation.  

Als de harde schijf al is versleuteld maar BitLocker is uitgeschakeld, wordt de **BitLocker inschakelen** stap schakelt de sleutelbeveiligingen en snel voltooien. De harde schijf hoeft in dit geval niet nogmaals te worden versleuteld.  

Zie [Variabelen voor takenreeksacties van BitLocker inschakelen](task-sequence-action-variables.md#BKMK_EnableBitLocker) voor meer informatie over de takenreeksvariabelen voor deze actie.  

Klik in de takenreekseditor op **toevoegen**, selecteer **schijven**, en selecteer **BitLocker inschakelen** om toe te voegen in deze stap. 

### <a name="properties"></a>Eigenschappen  
 Op de **eigenschappen** tabblad voor deze stap, configureer de instellingen die in deze sectie beschreven.  

 **Kies het station om te versleutelen**  
 Hiermee geeft u het te versleutelen station op. Selecteer **Huidig besturingssysteemstation** om het huidige besturingssysteemstation te versleutelen en configureer vervolgens een van de volgende opties voor sleutelbeheer:  

-   **Alleen TPM**: Selecteer deze optie om alleen Trusted Platform Module (TPM) gebruiken.  

-   **Opstartsleutel op USB alleen**: Selecteer deze optie om een opstartsleutel die is opgeslagen op een USB-flashstation te gebruiken. Wanneer u deze optie selecteert, wordt de normale opstartprocedure door BitLocker vergrendeld totdat een USB-apparaat met een BitLocker-opstartsleutel wordt aangesloten op de computer.  

-   **TPM en opstartsleutel op USB**: Selecteer deze optie om TPM en een opstartsleutel die is opgeslagen op een USB-flashstation te gebruiken. Wanneer u deze optie selecteert, wordt de normale opstartprocedure door BitLocker vergrendeld totdat een USB-apparaat met een BitLocker-opstartsleutel wordt aangesloten op de computer.  

-   **TPM en PINCODE**:  Selecteer deze optie om TPM en pincode (PIN) te gebruiken. Wanneer u deze optie selecteert, wordt de normale opstartprocedure door BitLocker vergrendeld totdat de pincode is ingevoerd.  
   
Selecteer **Specifiek station** om een specifiek gegevensstation (niet het besturingssysteemstation) te versleutelen en selecteer vervolgens het station in de lijst.  

**Kies waar de herstelsleutel moet worden gemaakt**  
 Selecteer om te geven waarop BitLocker maakt het herstelwachtwoord en selecteren zodat deze wordt bewaard in Active Directory, **In Active Directory**. Als u deze optie selecteert, moet u Active Directory voor de site uitbreiden. BitLocker kunt vervolgens de bijbehorende herstelgegevens opslaan in Active Directory. Selecteer **geen herstelsleutel maken** geen wachtwoord te maken. Het wordt aanbevolen een wachtwoord te maken.  

**Wacht totdat BitLocker het stationscoderingsproces op alle stations voordat de bewerking wordt voortgezet uitvoering van takenreeks voltooid**  
 Selecteer deze optie om de BitLocker-stationsversleuteling te voltooien voordat u de volgende stap in de takenreeks uitvoert. Als u deze optie selecteert, worden het hele schijfvolume versleuteld voordat de gebruiker zich kan aanmelden bij de computer.  

De versleuteling kan uren in beslag bij het versleutelen van een grote harde schijf duren. Als u deze optie niet selecteert, kunt de takenreeks onmiddellijk worden voortgezet.  



##  <a name="BKMK_FormatandPartitionDisk"></a> Schijf formatteren en partitioneren  
 Deze stap gebruiken om te formatteren en partitioneren van een opgegeven schijf op de doelcomputer.  

> [!IMPORTANT]  
>  Elke instelling die u voor deze takenreeksstap opgeeft geldt voor één opgegeven schijf. Als u wilt formatteren en partitioneren van een andere schijf op de doelcomputer, toevoegen van een extra **schijf formatteren en partitioneren** stap in de takenreeks wordt uitgevoerd.  

 Deze takenreeksstap kan alleen in Windows PE worden uitgevoerd. De taak kan niet worden uitgevoerd in een standaardbesturingssysteem. Zie [Format and Partition Disk Task Sequence Action Variables](task-sequence-action-variables.md#BKMK_FormatPartitionDisk) (Variabelen voor takenreeksacties voor schijfformattering en -partitionering) voor meer informatie over de takenreeksvariabelen voor deze actie.  

 Klik in de takenreekseditor op **toevoegen**, selecteer **schijven**, en selecteer **schijf formatteren en partitioneren** om toe te voegen in deze stap. 

### <a name="properties"></a>Eigenschappen  
 Op de **eigenschappen** tabblad voor deze stap, configureer de instellingen die in deze sectie beschreven.  

 **Schijfnummer**  
 Het fysieke schijfnummer van de schijf om te formatteren. Het nummer is gebaseerd op de rangschikking van Windows-schijfinventarisatie.  

 **Schijftype**  
 Het type van de schijf die wordt geformatteerd. Er zijn twee opties die u kunt selecteren in de vervolgkeuzelijst: 

-   Standaard(MBR) - Master Boot Record
-   GPT - GUID-partitietabel  

> [!NOTE]  
>  Als u het schijftype van wijzigt **standaard (MBR)** naar **GPT**, en de partitie-indeling een uitgebreide partitie bevat, worden de takenreeks alle uitgebreide en logische partities verwijderd uit de indeling. De editor voor takenreeksen wordt gevraagd deze actie voordat u het schijftype wijzigt te bevestigen.  
   
**Volume**  
 Specifieke informatie over de partitie of het volume dat de takenreeks, met inbegrip van de volgende kenmerken maakt:  

-   Name  
-   Resterende schijfruimte  
   
Klik op **Nieuw** om het dialoogvenster **Partitie-eigenschappen** te openen voor het maken van een nieuwe partitie. Geef het partitietype en de grootte, en als het een opstartpartitie is. Als u een bestaande partitie wilt wijzigen, klikt u op de te wijzigen partitie en klikt u vervolgens op de eigenschappenknop. Zie voor meer informatie over het configureren van hardeschijfpartities een van de volgende artikelen:  

-   [UEFI/GPT gebaseerde vaste schijfpartities configureren](http://go.microsoft.com/fwlink/?LinkID=272104)  
-   [BIOS/MBR-hardeschijfpartities configureren](http://go.microsoft.com/fwlink/?LinkId=272105)  

Als u een partitie wilt verwijderen, selecteert u de gewenste partitie en klikt u vervolgens op **Verwijderen**.  



##  <a name="BKMK_InstallApplication"></a> Toepassing installeren  
Deze stap worden geïnstalleerd voor de opgegeven toepassingen of een set toepassingen die zijn gedefinieerd door een dynamische lijst met takenreeksvariabelen. Als deze stap wordt uitgevoerd, begint de installatie van de toepassing onmiddellijk zonder te wachten op een polling-interval voor beleid.  

De geïnstalleerde toepassingen moeten voldoen aan de volgende criteria:  

-   De toepassing moet een implementatietype van Windows Installer of Script Installer zijn. Implementatietypen voor Windows-app-pakket (appx-bestand) worden niet ondersteund.  

-   De software moet worden uitgevoerd onder het lokale systeemaccount en niet het gebruikersaccount.  

-   De toepassing mag geen interactie hebben met het bureaublad. Het programma moet stil of zonder toezicht worden uitgevoerd.  

-   De toepassing mag zelf geen herstart initiëren. De toepassing moet een herstart aanvragen via de standaardherstartcode, afsluitcode 3010. Dit gedrag zorgt ervoor dat de takenreeksstap de herstart correct worden verwerkt. Als de toepassing afsluitcode 3010 retourneert, voert de onderliggende takenreeks-engine de herstart uit. Na het opnieuw opstarten wordt de takenreeks automatisch voortgezet.  

Wanneer de **toepassing installeren** stap wordt uitgevoerd, controleert de toepassing de toepasbaarheid van de vereisteregels en de detectiemethode voor de implementatietypen ervan. Op basis van de resultaten van deze controle installeert de toepassing het toepasselijke implementatietype. Als een implementatietype afhankelijkheden bevat, wordt het afhankelijke implementatietype geëvalueerd en geïnstalleerd als onderdeel van de stap voor toepassingsinstallatie. Toepassingsafhankelijkheden worden niet ondersteund voor zelfstandige media.  

> [!NOTE]  
>  Een toepassing te installeren die een andere toepassing vervangt, moeten de inhoudsbestanden voor de vervangen toepassing beschikbaar zijn. Anders wordt deze takenreeksstap mislukt. Bijvoorbeeld: Microsoft Visio 2010 is geïnstalleerd in een client of in een vastgelegde installatiekopie. Wanneer de **toepassing installeren** stap installeert Microsoft Visio 2013, de inhoudsbestanden voor Microsoft Visio 2010 (de vervangen toepassing) beschikbaar zijn op een distributiepunt. Als Microsoft Visio is niet geïnstalleerd op een client of installatiekopie vastgelegde, installeert de takenreeks Microsoft Visio 2013 zonder te controleren of de Microsoft Visio 2010-inhoudsbestanden.  

> [!NOTE]
> Als de client mislukt voor het ophalen van de beheerpuntlijst van locatieservices, kunt u de ingebouwde variabelen SMSTSMPListRequestTimeoutEnabled en SMSTSMPListRequestTimeout om op te geven hoeveel milliseconden lang een taak sequentiëren wacht voordat deze opnieuw installeren van een toepassingen of software-update. Zie voor meer informatie [Takenreeksvariabelen ingebouwde](task-sequence-built-in-variables.md).

 Deze takenreeksstap kan alleen in een standaardbesturingssysteem worden uitgevoerd. De stap kan niet worden uitgevoerd in Windows PE.  

 Klik in de takenreekseditor op **toevoegen**, selecteer **Software**, en selecteer **toepassing installeren** om toe te voegen in deze stap. 

### <a name="properties"></a>Eigenschappen  
 Op de **eigenschappen** tabblad voor deze stap, configureer de instellingen die in deze sectie worden beschreven.  

 **De volgende toepassingen installeren**  
 De takenreeks installeert deze toepassingen in de opgegeven volgorde.  

 Configuration Manager-filters een uitgeschakelde toepassingen en alle toepassingen met de volgende instellingen:  

-   Alleen als er een gebruiker is aangemeld  
-   Uitvoeren met gebruikersrechten  

Deze toepassingen worden niet weergegeven in de **Selecteer de te installeren toepassing** in het dialoogvenster.
  
**Toepassingen installeren volgens dynamische variabelenlijst**  
De takenreeks installeert met behulp van deze basisvariabelenaam in toepassingen. De variabele basisnaam is voor een set takenreeksvariabelen die zijn gedefinieerd voor een verzameling of computer. Deze variabelen worden de toepassingen die de takenreeks voor die verzameling of computer installeert opgegeven. De naam van elke variabele bestaat uit de gemeenschappelijke basisnaam plus een numeriek achtervoegsel dat begint bij 01. De waarde voor elke variabele moet de naam van de toepassing en niets anders bevatten.  

Voor de takenreeks om toepassingen te installeren met behulp van een dynamische variabelenlijst, schakelt u de volgende instelling op de **algemene** tabblad van de toepassing **eigenschappen**: **Toestaan dat deze toepassing wordt geïnstalleerd door de toepassing installeren voor de takenreeksactie in plaats van handmatig implementeren**  

> [!NOTE]  
>  U kunt toepassingen niet installeren met behulp van een dynamische variabelenlijst voor zelfstandige media-implementaties.  

Bijvoorbeeld: als u één toepassing wilt installeren met behulp van de takenreeksvariabele AA01, geeft u de volgende variabele op:  

|Naam variabele|Waarde variabele|  
|-------------------|--------------------|  
|AA01|Microsoft Office|  

Als u twee toepassingen wilt installeren, geeft u de volgende variabelen op:  

|Naam variabele|Waarde variabele|  
|-------------------|--------------------|  
|AA01|Microsoft Lync|  
|AA02|Microsoft Office|  

De volgende voorwaarden van invloed zijn op de toepassingen zijn geïnstalleerd door de takenreeks:  

-   Als de waarde van een variabele andere informatie bevat dan de naam van de toepassing, De takenreeks wordt niet geïnstalleerd voor de toepassing en de takenreeks voortgezet.  

-   Als de takenreeks een variabele met de opgegeven basisnaam en het achtervoegsel '01' niet gevonden, wordt de takenreeks alle toepassingen niet geïnstalleerd. 
    
> [!Important]  
> Deze waarden zijn hoofdlettergevoelig. Bijvoorbeeld, is het anders dan 'Install' 'installeren'. Als u moet de waarde te wijzigen, detecteert de takenreekseditor geen een wijziging van de aanvraag. U moet een andere bewerken op hetzelfde moment, bijvoorbeeld, de Stapbeschrijving van de aanpassen.<!--509714-->   

   
**Als een toepassing mislukt, doorgaan met installatie van andere toepassingen in de lijst**  
 Deze instelling geeft aan dat de stap wordt voorgezet als de installatie van een afzonderlijke toepassing mislukt. Als u deze instelling opgeeft, wordt de takenreeks voortgezet ongeacht eventuele installatiefouten. Als u deze instelling niet opgeeft en de installatie mislukt, wordt de stap onmiddellijk beëindigd.  

### <a name="options"></a>Opties
 > [!NOTE] 
 > Wanneer u selecteert **Doorgaan bij fout** op de **opties** tabblad van deze stap wordt de takenreeks voortgezet als een toepassing niet kan worden geïnstalleerd. Wanneer u deze optie niet inschakelt, wordt de takenreeks mislukt en resterende toepassingen niet installeren.  
 
Naast de standaardopties te gebruiken, kunt u de volgende aanvullende instellingen configureren op de **opties** tabblad van deze takenreeksstap:  

-   **Herhaal deze stap indien de computer onverwacht opnieuw wordt opgestart**  
    Als een van de installatie van toepassingen de computer onverwacht opnieuw opgestart, probeert u deze stap. De stap kunt deze instelling standaard met twee nieuwe pogingen. U kunt één tot vijf pogingen opgeven.  



##  <a name="BKMK_InstallPackage"></a> Pakket installeren
Deze stap gebruiken voor het installeren van een softwarepakket als onderdeel van de takenreeks wordt uitgevoerd. Wanneer deze stap wordt uitgevoerd, begint de installatie onmiddellijk zonder te wachten op een polling-interval voor beleid.  

Het pakket moet voldoen aan de volgende criteria:  

-   Het moet worden uitgevoerd onder het lokale systeemaccount en niet een gebruikersaccount.  

-   De software mag geen interactie hebben met het bureaublad. Het programma moet stil of zonder toezicht worden uitgevoerd.  

-   De toepassing mag zelf geen herstart initiëren. De software moet een herstart aanvragen via de standaardherstartcode, afsluitcode 3010. Dit gedrag zorgt ervoor dat de takenreeksstap op correcte wijze heeft het opnieuw opstarten. Als de software afsluitcode 3010 retourneert, start de computer opnieuw op de onderliggende takenreeks-engine. Na het opnieuw opstarten wordt de takenreeks automatisch voortgezet.  

Programma's die gebruikmaken van de optie **Eerst een ander programma uitvoeren** voor het installeren van een afhankelijk programma worden niet ondersteund bij het implementeren van een besturingssysteem. Als u de optie pakket inschakelen **rst een ander programma**, en het afhankelijke programma al hebt uitgevoerd op de doelcomputer, wordt het afhankelijke programma uitgevoerd en de takenreeks voortgezet. Echter, als het afhankelijke programma is niet uitgevoerd op de doelcomputer, mislukt de takenreeksstap.  

> [!NOTE]  
>  De centrale beheersite beschikt niet over de benodigde beleidsregels voor clientconfiguratie vereist voor het inschakelen van de agent voor softwaredistributie tijdens de takenreeks wordt uitgevoerd. Wanneer u op de centrale beheersite zelfstandige media maakt voor een takenreeks en de takenreeks de stap **Pakket installeren** bevat, wordt mogelijk de volgende fout weergegeven in het bestand CreateTsMedia.log:  
>   
>  `"WMI method SMS_TaskSequencePackage.GetClientConfigPolicies failed (0x80041001)"`  
>   
>  Voor zelfstandige media met een **pakket installeren** stap, de zelfstandige media maken op een primaire site die de agent voor softwaredistributie is ingeschakeld. U kunt ook toevoegen een **opdrachtregel uitvoeren** stap na de **Windows en ConfigMgr installeren** stap en voor de eerste **pakket installeren** stap. De **opdrachtregel uitvoeren** stap wordt uitgevoerd een WMIC-opdracht inschakelen van de agent voor softwaredistributie voordat de eerste **pakket installeren** stap. Gebruik de volgende opdracht in de **opdrachtregel uitvoeren** stap:  
>   
>  **Opdrachtregel**: `WMIC /namespace:\\\root\ccm\policy\machine\requestedconfig path ccm_SoftwareDistributionClientConfig CREATE ComponentName="Enable SWDist", Enabled="true", LockSettings="TRUE", PolicySource="local", PolicyVersion="1.0", SiteSettingsKey="1" /NOINTERACTIVE`  
>   
>  Zie voor meer informatie over het maken van zelfstandige media [zelfstandige media maken](../deploy-use/create-stand-alone-media.md).  

Deze takenreeksstap kan alleen in een standaardbesturingssysteem worden uitgevoerd. De stap kan niet worden uitgevoerd in Windows PE.  

Klik in de takenreekseditor op **toevoegen**, selecteer **Software**, en selecteer **pakket installeren** om toe te voegen in deze stap. 

### <a name="properties"></a>Eigenschappen  
 Op de **eigenschappen** tabblad voor deze stap, configureer de instellingen die in deze sectie beschreven.  

 **Een enkel softwarepakket installeren**  
 Deze instelling geeft een Configuration Manager-softwarepakket. De stap wacht totdat de installatie voltooid is.  

 **Softwarepakketten installeren volgens dynamische variabelenlijst**  
 De takenreeks installeert met behulp van deze basisvariabelenaam in pakketten. De variabele basisnaam is voor een set takenreeksvariabelen die zijn gedefinieerd voor een verzameling of computer. Deze variabelen de pakketten opgegeven die de takenreeks voor die verzameling of computer installeert. De naam van elke variabele bestaat uit de gemeenschappelijke basisnaam plus een numeriek achtervoegsel dat begint bij 001. De waarde voor elke variabele moet een pakket-id en de naam van de software bevatten en deze moeten zijn gescheiden door een dubbele punt.  

 Voor de takenreeks om software te installeren met behulp van een dynamische variabelenlijst, schakelt u de volgende instelling op de **Geavanceerd** tabblad van het pakket **eigenschappen**: **Toestaan dat dit programma wordt geïnstalleerd door de takenreeks pakket installeren zonder te worden geïmplementeerd**  

> [!NOTE]  
>  U kunt softwarepakketten niet installeren met behulp van een dynamische variabelenlijst voor zelfstandige media-implementaties.  

 Bijvoorbeeld: als u één softwarepakket wilt installeren met behulp van de takenreeksvariabele AA001, geeft u de volgende variabele op:  

|Naam variabele|Waarde variabele|  
|-------------------|--------------------|  
|AA001|CEN00054:Install|  

 Als u drie softwarepakketten wilt installeren, geeft u de volgende variabelen op:  

|Naam variabele|Waarde variabele|  
|-------------------|--------------------|  
|AA001|CEN00054:Install|  
|AA002|CEN00107:Install Silent|  
|AA003|CEN00031:Install|  

 De volgende voorwaarden van invloed zijn op de pakketten die zijn geïnstalleerd door de takenreeks:  

-   Als u niet de waarde van een variabele in de juiste indeling maakt of een geldige pakket-ID en de naam niet wordt aangegeven, mislukt de software-installatie.  

-   Als de pakket-ID kleine letters bevat, mislukt de software-installatie.  

-   Als de takenreeks een variabele met de opgegeven basisnaam en het achtervoegsel '001' niet gevonden, wordt de takenreeks alle pakketten niet geïnstalleerd. De takenreeks voortgezet.  
    
> [!Important]  
> Deze waarden zijn hoofdlettergevoelig. Bijvoorbeeld, is het anders dan 'Install' 'installeren'. Als u moet de waarde te wijzigen, detecteert de takenreekseditor geen een wijziging van de aanvraag. U moet een andere bewerken op hetzelfde moment, bijvoorbeeld, de Stapbeschrijving van de aanpassen.<!--509714-->   

   
**Als de installatie van een softwarepakket mislukt, doorgaan met installatie van andere pakketten in de lijst**  
 Deze instelling geeft aan dat de stap wordt voorgezet als de installatie van een afzonderlijk softwarepakket mislukt. Als u deze instelling opgeeft, wordt de takenreeks voortgezet ongeacht eventuele installatiefouten. Als u deze instelling niet opgeeft en de installatie mislukt, wordt de stap onmiddellijk beëindigd.  



##  <a name="BKMK_InstallSoftwareUpdates"></a> Software-Updates installeren  
Deze stap gebruiken voor het installeren van software-updates op de doelcomputer. De doelcomputer wordt pas geëvalueerd voor toepasselijke software-updates als deze takenreeksstap wordt uitgevoerd. Op dat moment wordt de doelcomputer geëvalueerd voor software-updates zoals elke andere Configuration Manager-client. Voor deze stap voor het installeren van software-updates, moet u eerst de updates implementeren voor een verzameling waarvan de doelcomputer lid is.  
>  [!IMPORTANT]
> Er is een best practice voor optimale prestaties voor het installeren van de nieuwste versie van Windows Update Agent. 
>* Zie [Knowledge base-artikel 3161647](https://support.microsoft.com/kb/3161647) voor Windows 7.
>* Zie [Knowledge base-artikel 3163023](https://support.microsoft.com/kb/3163023) voor Windows 8.

 Deze takenreeksstap kan alleen in een standaardbesturingssysteem worden uitgevoerd. De stap kan niet worden uitgevoerd in Windows PE. Zie [Install Software Updates Task Sequence Action Variables](task-sequence-action-variables.md#BKMK_InstallSoftwareUpdates) (Variabelen voor de takenreeksactie voor het installeren van software-updates) voor informatie over takenreeksvariabelen voor deze takenreeksactie.

 > [!NOTE]
 > Als de client mislukt voor het ophalen van de beheerpuntlijst van locatieservices, kunt u de ingebouwde variabelen SMSTSMPListRequestTimeoutEnabled en SMSTSMPListRequestTimeout om op te geven hoeveel milliseconden lang een taak sequentiëren wacht voordat deze opnieuw installeren van een toepassingen of software-update. Zie voor meer informatie [Takenreeksvariabelen ingebouwde](task-sequence-built-in-variables.md).

 Klik in de takenreekseditor op **toevoegen**, selecteer **Software**, en selecteer **Software-Updates installeren** om toe te voegen in deze stap. 

### <a name="properties"></a>Eigenschappen  
 Op de **eigenschappen** tabblad voor deze stap, configureer de instellingen die in deze sectie beschreven.  

 **Vereist voor de installatie - alleen verplichte software-updates**  
 Selecteer deze optie om alle verplichte software-updates installeren met de beheerder gedefinieerde installatie deadlines.  

 **Beschikbaar voor installatie - alle software-updates**  
 Selecteer deze optie om alle beschikbare software-updates te installeren. Eerst moet u deze updates implementeren voor een verzameling die de computer lid is. De takenreeks installeert alle beschikbare software-updates op de doelcomputers.  

 **Software-updates uit scanresultaten in het cachegeheugen evalueren**  
 De takenreeks maakt standaard gebruik van scanresultaten in het cachegeheugen van de Windows Update Agent. Schakel het selectievakje in zodat de Windows Update Agent downloaden van de meest recente catalogus van de software-update verwijzen. Deze optie hebt gekozen bij gebruik van een takenreeks voor het [vastleggen en opbouwen van een besturingssysteeminstallatiekopie](../deploy-use/create-a-task-sequence-to-capture-an-operating-system.md). In dit scenario is een groot aantal software-updates het waarschijnlijk. Veel van deze updates worden afhankelijkheden, bijvoorbeeld, hebben X installeren voordat Y wordt weergegeven als die van toepassing zijn. Wanneer u deze instelling wist en de takenreeks voor veel clients implementeren, ze alle verbinding maken met de software-updatepunt op hetzelfde moment. Dit gedrag leidt tot prestatieproblemen kunnen voordoen tijdens het verwerken en downloaden van de catalogus. De aanbevolen procedure is de standaardinstelling gebruiken scanresultaten in het cachegeheugen. 

De SMSTSSoftwareUpdateScanTimeout takenreeksvariabele Hiermee bepaalt u de software-updates scannen time-out tijdens deze stap. De standaardwaarde is 30 minuten. Zie voor meer informatie [Takenreeksvariabelen ingebouwde](task-sequence-built-in-variables.md).

### <a name="options"></a>Opties   
 Naast de standaardopties te gebruiken, kunt u de volgende aanvullende instellingen configureren op de **opties** tabblad van deze takenreeksstap:  

-   **Herhaal deze stap indien de computer onverwacht opnieuw wordt opgestart**  
    Als een van de updates de computer onverwacht opnieuw opgestart, probeert u deze stap. De stap kunt deze instelling standaard met twee nieuwe pogingen. U kunt één tot vijf pogingen opgeven.  

    > [!NOTE]
    > De variabele SMSTSWaitForSecondReboot configureren om op te geven hoeveel seconden de takenreeks pauzeert nadat de computer opnieuw is opgestart in dit scenario. Zie voor meer informatie [Takenreeksvariabelen ingebouwde](task-sequence-built-in-variables.md).



##  <a name="BKMK_JoinDomainorWorkgroup"></a> Lid worden van domein of werkgroep  
 Deze stap wordt de doelcomputer toevoegen aan een werkgroep of domein gebruiken.  

 Deze takenreeksstap kan alleen in een standaardbesturingssysteem worden uitgevoerd. De stap kan niet worden uitgevoerd in Windows PE. Zie [Join Domain or Workgroup Task Sequence Action Variables](task-sequence-action-variables.md#BKMK_JoinDomainWorkgroup) (Variabelen voor de takenreeksactie voor het lid worden van domein of werkgroep) voor informatie over takenreeksvariabelen voor deze takenreeksactie.  

 Klik in de takenreekseditor op **toevoegen**, selecteer **algemene**, en selecteer **lid worden van domein of werkgroep** om toe te voegen in deze stap. 

### <a name="properties"></a>Eigenschappen  
 Op de **eigenschappen** tabblad voor deze stap, configureer de instellingen die in deze sectie beschreven.  

 **Lid worden van een werkgroep**  
 Selecteer deze optie om de doelcomputer toe te voegen aan de opgegeven werkgroep. Als de computer momenteel lid is van een domein, met deze optie zorgt ervoor dat de computer opnieuw opgestart.  

 **Lid worden van een domein**  
 Selecteer deze optie om de doelcomputer toe te voegen aan het opgegeven domein.  

 Typ optioneel een organisatie-eenheid (OE) of blader ernaartoe in het opgegeven domein waarvan u de computer lid wilt maken. Als de computer momenteel lid is van een ander domein of werkgroep bevinden, is deze optie zorgt ervoor dat de computer opnieuw opgestart. Als de computer al lid is van een andere organisatie-eenheid, omdat het wijzigen van de organisatie-eenheid via deze methode niet wordt toegestaan door Active Directory Domain Services, Windows Setup deze instelling wordt genegeerd.  

 **Voer het account dat gemachtigd is aan het domein**  
 Klik op **ingesteld** gebruikersnaam en wachtwoord invoeren voor een account met machtigingen aan het domein. Voer het account in de indeling:  *Domain\account*  



## <a name="BKMK_PrepareConfigMgrClientforCapture"></a> ConfigMgr-Client voorbereiden voor vastleggen  
Deze stap gebruiken om te verwijderen of de Configuration Manager-client configureren op de referentiecomputer. Deze actie wordt de computer voorbereid voor vastleggen als onderdeel van de installatiekopieprocedure.

Configuration Manager versie 1610, vanaf de **ConfigMgr-Client voorbereiden** stap volledig verwijdert Configuration Manager-client, in plaats van alleen het verwijderen van belangrijke gegevens. Wanneer de takenreeks de vastgelegde besturingssysteeminstallatiekopie implementeert, wordt een nieuwe Configuration Manager-client elke keer.  

> [!Note]  
>  De engine voor takenreeksen alleen worden verwijderd van de client tijdens de **samenstellen en vastleggen van een referentie-installatiekopie voor besturingssysteem** takenreeks. De engine voor takenreeksen wordt niet verwijderd van de client tijdens de andere methoden vastleggen, zoals vastleggende media of een aangepaste takenreeks.

Voorafgaand aan de Configuration Manager versie 1610 voert deze stap uit de volgende taken:  

-   Verwijdert de sectie met eigenschappen van de clientconfiguratie in het bestand smscfg.ini in de Windows-map. Deze eigenschappen zijn clientspecifieke informatie zoals de Configuration Manager-GUID en andere client-id.  

-   Verwijdert alle SMS of Configuration Manager-computercertificaten.  

-   Hiermee verwijdert u de Configuration Manager-clientcache.  

-   Wist de toegewezen sitevariabele voor de Configuration Manager-client.  

-   Hiermee verwijdert u alle lokale Configuration Manager-beleid.  

-   Hiermee verwijdert u de vertrouwde basissleutel voor de Configuration Manager-client.  

Deze takenreeksstap kan alleen in een standaardbesturingssysteem worden uitgevoerd. De stap kan niet worden uitgevoerd in Windows PE.  

Klik in de takenreekseditor op **toevoegen**, selecteer **installatiekopieën**, en selecteer **ConfigMgr-Client voorbereiden voor vastleggen** om toe te voegen in deze stap. 

### <a name="properties"></a>Eigenschappen  
 Deze stap vereist geen instellingen op de **eigenschappen** tabblad.



##  <a name="BKMK_PrepareWindowsforCapture"></a> Windows voorbereiden voor vastleggen  
 Deze stap gebruiken om op te geven van de Sysprep-opties bij het vastleggen van de installatiekopie van een besturingssysteem op de referentiecomputer. Deze takenreeksactie wordt Sysprep uitgevoerd en vervolgens de computer opnieuw opgestart in de Windows PE-opstartinstallatiekopie die is opgegeven voor de takenreeks wordt uitgevoerd. Deze actie mislukt als de referentiecomputer is toegevoegd aan een domein.  

 Deze takenreeksstap kan alleen in een standaardbesturingssysteem worden uitgevoerd. De stap kan niet worden uitgevoerd in Windows PE. Zie [Prepare Windows for Capture Task Sequence Action Variables](task-sequence-action-variables.md#BKMK_PrepareWindowsCapture) (Variabelen voor de takenreeksactie voor het voorbereiden van Windows op het vastleggen) voor informatie over takenreeksvariabelen voor deze takenreeksactie.  

 Klik in de takenreekseditor op **toevoegen**, selecteer **installatiekopieën**, en selecteer **Windows voorbereiden voor vastleggen** om toe te voegen in deze stap. 

### <a name="properties"></a>Eigenschappen  
 Op de **eigenschappen** tabblad voor deze stap, configureer de instellingen die in deze sectie beschreven.  

 **Lijst van stuurprogramma's voor massaopslag automatisch samenstellen**  
 Selecteer deze optie om automatisch een lijst met stuurprogramma's voor massaopslag van de referentiecomputer te laten samenstellen door Sysprep. Met deze optie wordt de optie Build Mass Storage Drivers in het bestand sysprep.inf op de referentiecomputer ingeschakeld. Zie de documentatie van Sysprep voor meer informatie over deze instelling.  

 **Activatiemarkering niet resetten**  
 Selecteer deze optie om te voorkomen dat Sysprep de markering voor productactivering opnieuw instelt.  



##  <a name="BKMK_PreProvisionBitLocker"></a> BitLocker vooraf inrichten  
 Deze stap wordt BitLocker in te schakelen op een station in Windows PE gebruiken. Alleen de gebruikte schijfruimte is versleuteld. De versleutelingstijd is daarom veel sneller. Pas de sleutelbeheeropties toe met behulp van de takenreeksstap [BitLocker inschakelen](#BKMK_EnableBitLocker) nadat het besturingssysteem is geïnstalleerd. Deze stap kan alleen in Windows PE worden uitgevoerd. De taak kan niet worden uitgevoerd in een standaardbesturingssysteem.  

> [!IMPORTANT]  
>  Vooraf inrichten van BitLocker moet ten minste Windows 7. De computer moet ook een ondersteunde bevatten en Trusted Platform Module (TPM) ingeschakeld.  

 Klik in de takenreekseditor op **toevoegen**, selecteer **schijven**, en selecteer **BitLocker vooraf inrichten** om toe te voegen in deze stap. 

### <a name="properties"></a>Eigenschappen  
 Op de **eigenschappen** tabblad voor deze stap, configureer de instellingen die in deze sectie beschreven.  

 **BitLocker toepassen op het opgegeven station**  
 Geef het station op waarvoor u BitLocker wilt inschakelen. Alleen de gebruikte ruimte op het station wordt versleuteld.  

 **Deze stap overslaan voor computers die geen tmp hebben of wanneer tmp niet is ingeschakeld**  
 Selecteer deze optie om de stationsversleuteling overslaan op een computer die geen tmp ondersteund of ingeschakeld zoals vereist. Bijvoorbeeld: Gebruik deze optie wanneer u een besturingssysteem op een virtuele machine implementeert.  



##  <a name="BKMK_ReleaseStateStore"></a> Statusopslag vrijgeven  
 Deze stap gebruiken op de hoogte van de status wilt dat de actie vastleggen of vrijgeven is voltooid. Deze stap gebruiken in combinatie met de **Statusopslag opvragen**, **gebruikersstatus vastleggen**, en **gebruikersstatus herstellen** stappen. U Volg deze stappen voor het migreren van gegevens van de gebruikersstatus met behulp van een statusmigratiepunt en de gebruiker staat Migration Tool (USMT).  

 Zie voor meer informatie over het beheren van de gebruikersstatus bij het implementeren van besturingssystemen, [Gebruikersstatus beheren](../get-started/manage-user-state.md).  

 Als u de **Statusopslag opvragen** stap om aan te vragen toegang tot een statusmigratiepunt te *vastleggen* gebruiker staat, deze stap informeert het statusmigratiepunt gecommuniceerd dat het vastleggen is voltooid. Het statusmigratiepunt markeert vervolgens de gebruikersstatusgegevens als beschikbaar voor herstel. Het statusmigratiepunt stelt de toegangsbeheermachtigingen voor de gebruikersstatusgegevens zodat alleen de herstellende computer alleen-lezen toegang heeft.  

 Als u de **Statusopslag opvragen** stap om aan te vragen toegang tot een statusmigratiepunt te *herstellen* gebruiker staat, deze stap informeert het statusmigratiepunt gecommuniceerd dat het herstellen is voltooid. Het statusmigratiepunt wijs vervolgens de geconfigureerde instellingen voor Gegevensretentie wordt geactiveerd.  

> [!IMPORTANT]  
>  Er is een best practice om in te stellen de **Doorgaan bij fout** optie voor alle stappen tussen de **Statusopslag opvragen** en **Statusopslag vrijgeven** stappen. Elke **Statusopslag opvragen** stap moet beschikken over een overeenkomende **Statusopslag vrijgeven** stap.  

 Deze takenreeksstap kan alleen in een standaardbesturingssysteem worden uitgevoerd. De stap kan niet worden uitgevoerd in Windows PE. Zie [Variabelen voor de takenreeksactie voor vrijgeven van de statusopslag](task-sequence-action-variables.md#BKMK_ReleaseStateStore) voor informatie over takenreeksvariabelen voor deze takenreeksactie.  

 Klik in de takenreekseditor op **toevoegen**, selecteer **gebruikersstatus**, en selecteer **Statusopslag vrijgeven** om toe te voegen in deze stap. 

### <a name="properties"></a>Eigenschappen  
 Deze stap vereist geen instellingen op de **eigenschappen** tabblad.



##  <a name="BKMK_RequestStateStore"></a> Statusopslag opvragen  
 Deze stap gebruiken om toegang tot een statusmigratiepunt bij het vastleggen of terugzetten van de status te vragen.  

 Zie voor meer informatie over het beheren van de gebruikersstatus bij het implementeren van besturingssystemen, [Gebruikersstatus beheren](../get-started/manage-user-state.md).  

 Deze stap gebruiken in combinatie met de **Statusopslag vrijgeven**, **gebruikersstatus vastleggen**, en **gebruikersstatus herstellen** stappen. U Volg deze stappen voor het migreren van de status van de computer met behulp van een statusmigratiepunt en de gebruiker staat Migration Tool (USMT).  

> [!NOTE]  
>  Bij het maken van een statusmigratiepunt is gebruikerstatusopslag niet beschikbaar voor maximaal één uur. Sneller beschikbaarheid, een eigenschapsinstellingen aanpassen op het statusmigratiepunt om te activeren van een update-bestand.  

 Deze takenreeksstap kan worden uitgevoerd in een standaardbesturingssysteem en in Windows PE voor offlinegebruik van het Hulpprogramma voor migratie van gebruikersstatus. Zie [Variabelen takenreeksactie Statusopslag opvragen](task-sequence-action-variables.md#BKMK_RequestState) voor informatie over de takenreeksvariabelen voor deze takenreeksactie.  

Klik in de takenreekseditor op **toevoegen**, selecteer **gebruikersstatus**, en selecteer **Statusopslag opvragen** om toe te voegen in deze stap. 

### <a name="properties"></a>Eigenschappen  
 Op de **eigenschappen** tabblad voor deze stap, configureer de instellingen die in deze sectie beschreven.  

 **Status vastleggen vanaf de computer**  
 Een statusmigratiepunt dat voldoet aan de minimumvereisten zoals geconfigureerd in de instellingen van het statusmigratiepunt vinden. Bijvoorbeeld: **maximumaantal clients** en **minimale hoeveelheid vrije schijfruimte**. Deze optie wordt niet gegarandeerd dat voldoende ruimte beschikbaar is op het moment van de statusmigratie. Deze optie vraagt om toegang tot het statusmigratiepunt om vast te leggen van de gebruikersstatus en instellingen van een computer.  

 Als de Configuration Manager-site meerdere actieve statusmigratiepunten heeft, zoekt deze stap een statusmigratiepunt met beschikbare schijfruimte. De takenreeks het beheerpunt voor een lijst met statusmigratiepunten query's en elk totdat er een wordt gevonden dat voldoet aan de minimumvereisten evalueert.  

 **Status herstellen vanaf een andere computer**  
 Aanvragen van toegang tot een statusmigratiepunt om eerder vastgelegde gebruikersstatus te herstellen en instellingen op een doelcomputer.  

 Als er meerdere statusmigratiepunten zijn, wordt het statusmigratiepunt dat de status voor de doelcomputer is gevonden in deze stap.  

 **Aantal nieuwe pogingen**  
 Het aantal keren dat deze stap wordt gezocht naar een geschikt statusmigratiepunt voordat deze is mislukt.  

 **Wachttijd nieuwe poging (seconden)**  
 De hoeveelheid tijd in seconden dat de takenreeksstap moet wachten tussen nieuwe pogingen.  

 **Als het computeraccount geen verbinding maken met Statusopslag, gebruikt u het netwerktoegangsaccount.**  
 Als de takenreeks wordt uitgevoerd geen toegang het statusmigratiepunt via het computeraccount tot, wordt de referenties voor netwerktoegang account verbinding maken. Deze optie is minder veilig, omdat andere computers het netwerktoegangsaccount gebruiken kunnen voor toegang tot de opgeslagen status. Deze optie kan nodig zijn als de doelcomputer niet verbonden met het domein is.  



##  <a name="BKMK_RestartComputer"></a> Computer opnieuw opstarten  
 Deze stap gebruiken om de computer waarop de takenreeks wordt uitgevoerd. Na het opnieuw opstarten wordt voortgezet de computer automatisch met de volgende stap in de takenreeks.  

 Deze stap kan in een standaardbesturingssysteem of in Windows PE worden uitgevoerd. Zie voor meer informatie over de takenreeksvariabelen voor deze takenreeksactie [opnieuw opstarten van computer takenreeksacties](task-sequence-action-variables.md#BKMK_RestartComputer).  

 Klik in de takenreekseditor op **toevoegen**, selecteer **algemene**, en selecteer **Computer opnieuw opstarten** om toe te voegen in deze stap. 

### <a name="properties"></a>Eigenschappen  
 Op de **eigenschappen** tabblad voor deze stap, configureer de instellingen die in deze sectie beschreven.  

 **De opstartinstallatiekopie toegewezen aan deze takenreeks**  
 Selecteer deze optie voor de doelcomputer om de opstartinstallatiekopie toegewezen aan de takenreeks te gebruiken. De takenreeks maakt gebruik van de installatiekopie naar de volgende stappen uitvoeren in Windows PE.  

 **Het momenteel geïnstalleerde standaardbesturingssysteem**  
 Selecteer deze optie voor de doelcomputer om deze opnieuw op te starten naar het geïnstalleerde besturingssysteem.  

 **De gebruiker waarschuwen voordat opnieuw wordt opgestart**  
 Selecteer deze optie om een melding weergeven aan de gebruiker voordat de doel-computer opnieuw wordt opgestart. De stap wordt deze optie standaard geselecteerd.  

 **Tekst van melding**  
 Geef een bericht weer te geven voor de gebruiker voordat de doel-computer opnieuw wordt opgestart.  

 **Time-out voor weergave melding**  
 Geef de hoeveelheid tijd in seconden voordat de doel-computer opnieuw wordt opgestart. De standaardwaarde is 60 seconden.  



##  <a name="BKMK_RestoreUserState"></a> Gebruikersstatus herstellen  
 Deze stap gebruiken om de User State Migration Tool (USMT) voor het herstellen van gebruikersstatus en instellingen op de doelcomputer. U deze stap gebruiken in combinatie met de **gebruikersstatus vastleggen** stap.  

 Zie voor meer informatie over het beheren van de gebruikersstatus bij het implementeren van besturingssystemen, [Gebruikersstatus beheren](../get-started/manage-user-state.md).  

 Voer deze stap met het **Statusopslag opvragen** en **Statusopslag vrijgeven** stappen voor het opslaan of herstellen van de instellingen met een statusmigratiepunt. In USMT 3.0 en hoger wordt met deze ontsleuteld optie altijd de USMT-Statusopslag met behulp van een versleutelingssleutel die wordt gegenereerd en beheerd door Configuration Manager.  

 De **gebruikersstatus herstellen** stap biedt controle over een beperkte subset van de meest gebruikte USMT-opties. Aanvullende opdrachtregelopties opgeven met de takenreeksvariabele osdmigrateadditionalrestoreoptions.  

> [!IMPORTANT]  
>  Als u deze stap voor een doel dat geen verband houdt met een implementatiescenario van een besturingssysteem, voegt de [Computer opnieuw opstarten](#BKMK_RestartComputer) stap onmiddellijk toe na de **gebruikersstatus herstellen** stap.  

 Deze stap kan alleen in een standaardbesturingssysteem worden uitgevoerd. De stap kan niet worden uitgevoerd in Windows PE. Zie [Restore User State Task Sequence Action Variables](task-sequence-action-variables.md#BKMK_RestoreUserState) (Variabelen voor de takenreeksactie voor het herstellen van de gebruikersstatus) voor informatie over de takenreeksvariabelen voor deze takenreeksactie.  

 Klik in de takenreekseditor op **toevoegen**, selecteer **gebruikersstatus**, en selecteer **gebruikersstatus herstellen** om toe te voegen in deze stap. 

### <a name="properties"></a>Eigenschappen  
 Op de **eigenschappen** tabblad voor deze stap, configureer de instellingen die in deze sectie beschreven.  

 **Gebruiker pakket migratieprogramma gebruikersstatus**  
 Geef het pakket met de versie van USMT voor deze stap moet worden gebruikt. Voor dit pakket is geen programma vereist. Wanneer de stap wordt uitgevoerd, wordt de takenreeks de versie van USMT in het opgegeven pakket gebruikt. Geef een pakket op met de 32-bits of 64-bits versie van USMT. De architectuur van USMT is afhankelijk van de architectuur van het besturingssysteem waarop de takenreeks is herstelstatus. 

 **Alle vastgelegde gebruikersprofielen met standaardopties herstellen**  
 Hiermee worden de vastgelegde gebruikersprofielen hersteld met de standaardopties. Selecteer voor het aanpassen van de opties die USMT herstelt, **vastlegging gebruikersprofiel**.  

 **Herstellen van gebruikersprofielen aanpassen**  
 Hiermee kunt u de bestanden aanpassen die u wilt herstellen naar de doelcomputer. Klik op **Bestanden** om de configuratiebestanden in het USMT-pakket op te geven die u wilt gebruiken voor het herstellen van de gebruikersprofielen. Geef de naam van het bestand op in het vak **Bestandsnaam** en klik vervolgens op **Toevoegen** om een configuratiebestand toe te voegen. Het deelvenster bestanden bevat de configuratiebestanden die USMT gebruikt. Het .xml-bestand dat u opgeeft definieert gebruikersbestand dat USMT wordt hersteld.  

 **Gebruikersprofielen lokale computer herstellen**  
 Hiermee herstelt u de gebruikersprofielen lokale computer. Deze profielen zijn niet beschikbaar voor gebruikers van een domein. U moet nieuwe wachtwoorden toewijzen aan de herstelde lokale gebruikersaccounts. USMT migreren niet de oorspronkelijke wachtwoorden. Voer het nieuwe wachtwoord in het vak **Wachtwoord** in en bevestig het wachtwoord in het vak **Wachtwoord bevestigen**.  

 **Doorgaan als sommige bestanden kunnen niet worden hersteld**  
 Blijft het herstellen van gebruikersstatus en instellingen, zelfs als USMT niet kan sommige bestanden terug te zetten. De stap kunt u deze optie standaard ingeschakeld. Als u deze optie uitschakelt en USMT fouten optreden tijdens het herstellen van bestanden, wordt deze stap onmiddellijk mislukt. USMT hersteld niet alle bestanden.   

 **Uitgebreide logboekregistratie inschakelen**  
 Schakel deze optie in om meer gedetailleerde informatie in het logboekbestand te genereren. Bij het herstellen van status, de takenreeks standaard Loadstate.log gegenereerd in de logboekmap takenreeks, \windows\system32\ccm\logs.  



##  <a name="BKMK_RunCommandLine"></a> Opdrachtregel uitvoeren  
 Deze stap uitvoeren van de opgegeven opdrachtregel gebruiken.  

 Deze stap kan in een standaardbesturingssysteem of in Windows PE worden uitgevoerd. Zie [Run Command Line Task Sequence Action Variables](task-sequence-action-variables.md#BKMK_RunCommand) (Variabelen voor de takenreeksactie voor het uitvoeren van de opdrachtregel) voor informatie over takenreeksvariabelen voor deze takenreeksactie.  

 Klik in de takenreekseditor op **toevoegen**, selecteer **algemene**, en selecteer **opdrachtregel uitvoeren** om toe te voegen in deze stap. 

### <a name="properties"></a>Eigenschappen  
 Op de **eigenschappen** tabblad voor deze stap, configureer de instellingen die in deze sectie beschreven.  

 **Vanaf de opdrachtregel**  
 Hiermee geeft u de uitgevoerde opdrachtregel op. Dit veld is vereist. Inclusief bestandsnaamextensies wordt aanbevolen, bijvoorbeeld .vbs en .exe. Neem alle vereiste instellingenbestanden, opdrachtregelopties of schakelopties op.  

 Als de bestandsnaam geen een bestandsnaamextensie is opgegeven, Configuration Manager probeert .com, .exe en. bat. Als de bestandsnaam een extensie is niet een uitvoerbaar bestand heeft, Configuration Manager wordt geprobeerd een lokale koppeling toe te passen. Als de opdrachtregel readme.gif is, begint Configuration Manager de toepassing die is opgegeven op de doelcomputer voor het openen van .gif-bestanden.  

 Voorbeelden:  

 `setup.exe /a`  

 `cmd.exe /c copy Jan98.dat c:\sales\Jan98.dat`  

> [!NOTE]  
>  Om te worden uitgevoerd, worden voorafgegaan door een opdrachtregelacties met de **cmd.exe /c** opdracht. Voorbeeld van deze acties omvatten uitvoeromleiding, sluizen, en opdrachten kopiëren.  

 **64-bits bestandssysteemomleiding uitschakelen**  
 64-bits besturingssystemen maken gebruik van de WOW64-bestandssysteemredirector standaard naar opdrachtregels worden uitgevoerd. Dit gedrag is goed vinden 32-bits versies van het besturingssysteem uitvoerbare bestanden en bibliotheken. Selecteer deze optie om het gebruik van de WOW64-bestandssysteemredirector uitgeschakeld. Windows wordt uitgevoerd de opdracht die gebruikmaken van systeemeigen 64-bits versies van het besturingssysteem uitvoerbare bestanden en bibliotheken. Deze optie heeft geen effect wanneer op een 32-bits besturingssysteem wordt uitgevoerd.  

 **Beginnen in**  
 Hiermee geeft u de uitvoerbare map op voor het programma, in maximaal 127 tekens. Deze map kan een absoluut pad op de doelcomputer betreffen of een relatief pad ten opzichte van de distributiepuntmap die het pakket bevat. Dit veld is optioneel.  

 Voorbeelden:  

 **c:\officexp**  

 **i386**  

> [!NOTE]  
>  De **Bladeren** knop op de lokale computer voor bestanden en mappen gezocht. Alles wat die u selecteert moet ook aanwezig zijn op de doelcomputer in dezelfde locatie en met de dezelfde bestands- en mapnamen.  

 **Package**  
 Wanneer u bestanden of programma's op de opdrachtregel die nog niet aanwezig op de doelcomputer opgeeft, selecteert u deze optie om op te geven van de Configuration Manager-pakket dat de betreffende bestanden bevat. Voor het pakket is geen programma vereist. Deze optie is niet vereist als de opgegeven bestanden op de doelcomputer bestaan.  

 **Time-out**  
 Hiermee geeft u een waarde die aangeeft hoe lang Configuration Manager kan de opdrachtregel om uit te voeren. Deze waarde kan zijn van 1 minuut en 999 minuten liggen. De standaardwaarde is 15 minuten.  

 Deze optie is standaard uitgeschakeld.  

> [!IMPORTANT]  
>  Als u een waarde die niet in staat voldoende tijd voor de opgegeven opdracht is opgeeft voltooid, wordt deze stap mislukt. Er kan de gehele takenreeks mislukken afhankelijk van andere beheerinstellingen. Als de time-out is verlopen, beëindigt Configuration Manager het opdrachtregelproces.  

 **Deze stap uitvoeren als de volgende account**  
 Hiermee geeft u aan dat de opdrachtregel als een ander Windows-gebruikersaccount dan het lokale systeemaccount wordt uitgevoerd.  

> [!NOTE]  
>  U eenvoudige scripts of opdrachten uitvoeren met een ander account na de installatie van het besturingssysteem, moet u eerst de account toevoegen aan de computer. Bovendien moet u het Windows-account gebruikersprofiel als u wilt uitvoeren van complexere programma's, zoals een Windows Installer herstellen.  

 **Account**  
 Hiermee geeft u de Windows-gebruikersaccount die in deze stap gebruikt voor het uitvoeren vanaf de opdrachtregel. De opdrachtregel wordt uitgevoerd met de machtigingen van het opgegeven account. Klik op **Instellen** om het lokale gebruikersaccount of het domeinaccount op te geven.  

> [!IMPORTANT]  
>  Als deze stap geeft een gebruikersaccount wordt uitgevoerd in Windows PE, mislukt de actie. U kunt Windows PE niet koppelen aan een domein. Het bestand smsts.log registreert deze fout.  



##  <a name="BKMK_RunPowerShellScript"></a> PowerShell-Script uitvoeren  
 Deze stap gebruiken de opgegeven PowerShell-script uit te voeren.  

 Deze stap kan in een standaardbesturingssysteem of in Windows PE worden uitgevoerd. Als u deze stap wilt uitvoeren in Windows PE, moet PowerShell zijn ingeschakeld in de opstartinstallatiekopie. U kunt Windows PowerShell (WinPE-PowerShell) inschakelen via het tabblad **Optionele onderdelen** in de eigenschappen van de opstartinstallatiekopie. Zie voor meer informatie over het wijzigen van een opstartinstallatiekopie [opstartinstallatiekopieën beheren](../get-started/manage-boot-images.md).  

> [!NOTE]  
>  PowerShell is standaard niet ingeschakeld op Windows Embedded-besturingssystemen.  

Klik in de takenreekseditor op **toevoegen**, selecteer **algemene**, en selecteer **PowerShell-Script uitvoeren** om toe te voegen in deze stap. 

### <a name="properties"></a>Eigenschappen  
 Op de **eigenschappen** tabblad voor deze stap, configureer de instellingen die in deze sectie beschreven.  

 **Package**  
 De Configuration Manager-pakket met het PowerShell-script opgeven. Eén pakket kan meerdere PowerShell-scripts bevatten.  

 **Scriptnaam**  
 Hiermee geeft u de naam van het uit te voeren PowerShell-script op. Dit veld is vereist.  

 **Parameters**  
 Hiermee geeft u de parameters doorgegeven aan de Windows PowerShell-script. Deze parameters zijn hetzelfde als de parameters van de Windows PowerShell-script op de opdrachtregel.  

> [!IMPORTANT]  
>  Geef parameters op die worden gebruikt door het script, niet voor de Windows PowerShell-opdrachtregel.  
>   
>  Het volgende voorbeeld bevat geldige parameters:  
>   
>  `-MyParameter1 MyValue1 -MyParameter2 MyValue2`  
>   
>  Het volgende voorbeeld bevat ongeldige parameters. De eerste twee items zijn Windows PowerShell-opdrachtregelparameters (**- NoLogo** en **- ExecutionPolicy Unrestricted**). Het script verbruikt geen deze parameters.  
>   
>  `-NoLogo -ExecutionPolicy Unrestricted -File MyScript.ps1 -MyParameter1 MyValue1 -MyParameter2 MyValue2`  

 **PowerShell-uitvoeringsbeleid**  
 Bepalen welke Windows PowerShell-scripts (indien aanwezig) toestaan om uit te voeren op de computer. Kies een van de volgende uitvoeringsbeleidsregels:  

-   **Alles ondertekend**: Voer alleen scripts die zijn ondertekend door een vertrouwde uitgever  

-   **Niet-gedefinieerde**: Geen uitvoeringsbeleid gedefinieerd  

-   **Bypass**: Alle configuratiebestanden laden en alle scripts uitvoeren. Als u een niet-ondertekend script van Internet downloaden, vraagt Windows PowerShell niet om toestemming voordat het script wordt uitgevoerd.  

> [!IMPORTANT]  
>  PowerShell 1.0 biedt geen ondersteuning voor de uitvoeringsbeleidsregels Undefined en Bypass.  



##  <a name="child-task-sequence"></a> Takenreeks uitvoeren

U kunt een nieuwe stap waarop een andere takenreeks wordt uitgevoerd vanaf Configuration Manager versie 1710 kunt toevoegen. Deze stap maakt een bovenliggende / onderliggende relatie tussen de takenreeksen. Met onderliggende takenreeksen, kunt u meer modulaire, herbruikbare takenreeksen maken.

Overweeg de volgende instructies wanneer u een takenreeks onderliggende aan een takenreeks toevoegt:
 - De bovenliggende en onderliggende takenreeksen effectief gecombineerd tot een enkele beleidsregel die de client wordt uitgevoerd.
 - De omgeving is algemeen. Als de takenreeks bovenliggende een variabele stelt en de onderliggende takenreeks vervolgens die variabele wordt, behoudt de laatste waarde. Als de onderliggende takenreeks maakt u een nieuwe variabele, is het beschikbaar voor de rest van de bovenliggende takenreeks wordt uitgevoerd.
 - Statusberichten worden voor een enkele takenreeksbewerking per normaal verzonden.
 - De takenreeksen vermeldingen schrijven naar het bestand smsts.log met nieuwe logboekbestanden vermeldingen die duidelijk wanneer een onderliggende takenreeks wordt gestart.

Klik in de takenreekseditor op **toevoegen**, selecteer **algemene**, en selecteer **Takenreeks uitvoeren** om toe te voegen in deze stap. 

### <a name="properties"></a>Eigenschappen
 Op de **eigenschappen** tabblad voor deze stap, configureer de instellingen die in deze sectie beschreven.  

**Selecteer de takenreeks worden uitgevoerd**  
 Klik op **Bladeren** naar de onderliggende takenreeks selecteren. De **Selecteer een Takenreeks** in het dialoogvenster wordt niet weergegeven voor de bovenliggende takenreeks wordt uitgevoerd.



##  <a name="BKMK_SetDynamicVariables"></a> Dynamische variabelen instellen  
 Gebruik deze stap voor de volgende acties uitvoeren:  

1.  Informatie verzamelen van de computer en de omgeving waarin de computer zich bevindt en vervolgens opgegeven takenreeksvariabelen instellen met de informatie.  

2.  Gedefinieerde regels evalueren en takenreeksvariabelen instellen op basis van de variabelen en waarden die zijn geconfigureerd voor regels die in waar resulteren.  

De taakvolgorde stelt automatisch de volgende alleen-lezen takenreeksvariabelen in:  
 -   &#95;SMSTSMake  
 -   &#95;SMSTSModel  
 -   &#95;SMSTSMacAddresses  
 -   &#95;SMSTSIPAddresses  
 -   &#95;SMSTSSerialNumber  
 -   &#95;SMSTSAssetTag  
 -   &AMP;#95;SMSTSUUID  

Deze stap kan in een standaardbesturingssysteem of in Windows PE worden uitgevoerd. Zie voor meer informatie over takenreeksvariabelen [Takenreeksacties](task-sequence-action-variables.md).  

Klik in de takenreekseditor op **toevoegen**, selecteer **algemene**, en selecteer **dynamische variabelen instellen** om toe te voegen in deze stap. 

### <a name="properties"></a>Eigenschappen  
 Op de **eigenschappen** tabblad voor deze stap, configureer de instellingen die in deze sectie beschreven.  

**Dynamische regels en variabelen**  
 Een dynamische variabele voor gebruik in de takenreeks stelt u een regel toevoegen. Stel een waarde op voor elke variabele die is opgegeven in de regel. Bovendien een of meer variabelen toevoegen zonder een regel toe te voegen. Wanneer u een regel toevoegt, kunt u kiezen uit de volgende categorieën:  

 -   **Computer**: Evaluatie van waarden voor hardware-inventaristag, UUID, serienummer of MAC-adres. Meerdere waarden instellen als nodig. Als een willekeurige waarde waar is, klikt u vervolgens de regel geëvalueerd als waar. De volgende regel resulteert bijvoorbeeld als waar als het apparaat serienummer 5892087 is en het MAC-adres 22-A4-5A-13-78-26 is.  

     `IF Serial Number = 5892087 OR MAC address = 26-78-13-5A-A4-22 THEN`  

-   **Locatie**: De evaluatie van waarden voor de standaardgateway van het netwerk  

-   **Merk en Model**: Evaluatie van waarden voor het merk en model van een computer. Zowel het merk als het model moet resulteren in waar om de regel te laten resulteren in waar.   

    <!-- for future edits: an escape code must be used for the bolded asterisk character, but may be removed somewhere along the way. Instead of five asterisk, should be bold tags with &#42; in-between -->

    U start in Configuration Manager versie 1610, kunt u een sterretje (**&#42;**) en vraagtekens (**?**) als jokertekens, waarbij **&#42;** komt overeen met meerdere tekens en **?** komt overeen met een enkel teken. Bijvoorbeeld: de tekenreeks ' DELL * 900? ' komt overeen met ABC-DELL-9001 als DELL9009. 

    Geef een sterretje (**&#42;**) en vraagtekens (**?**) als jokertekens, waarbij **&#42;** komt overeen met meerdere tekens en **?** komt overeen met een enkel teken. Bijvoorbeeld: de tekenreeks ' DELL * 900? ' komt overeen met ABC-DELL-9001 en DELL9009.

-   **Takenreeksvariabele**: Toevoegen van een takenreeksvariabele, voorwaarde en waarde om te evalueren. Deze regel resulteert in waar wanneer de ingestelde waarde voor de variabele voldoet aan de opgegeven voorwaarde.  

    Geef een of meer variabelen worden ingesteld voor een regel die in waar resulteert of variabelen instellen zonder een regel. Selecteer een bestaande variabele of een aangepaste variabele maken.  

     -   **Bestaande takenreeksvariabelen**: Selecteer een of meer variabelen in een lijst met bestaande takenreeksvariabelen. Matrixvariabelen kunnen niet worden geselecteerd.  

     -   **Aangepaste takenreeksvariabelen**: Definieer een aangepaste takenreeksvariabele. U kunt ook een bestaande takenreeksvariabele opgeven. Deze instelling is nuttig om op te geven van een bestaande variabelenmatrix, zoals OSDAdapter, omdat variabelenmatrices niet in de lijst met bestaande takenreeksvariabelen.  

Nadat u de variabelen voor een regel hebt geselecteerd, moet u een waarde opgeven voor elke variabele. De variabele wordt ingesteld op de opgegeven waarde wanneer de regel resulteert in waar. Voor elke variabele kunt u **Geheime waarde** selecteren om de waarde van de variabele te verbergen. Standaard worden de waarden van bepaalde bestaande variabelen verborgen, zoals de takenreeksvariabele OSDCaptureAccountPassword.  

> [!IMPORTANT]  
>  Configuration Manager wordt verwijderd van alle waarden van variabelen gemarkeerd als een **geheime waarde** wanneer u een takenreeks importeert met de **dynamische variabelen instellen** stap. De waarde voor de dynamische variabele opnieuw invoeren nadat u de takenreeks hebt geïmporteerd.  



##  <a name="BKMK_SetTaskSequenceVariable"></a> Takenreeksvariabele instellen  
Deze stap gebruiken om in te stellen van de waarde van een variabele die wordt gebruikt met de takenreeks wordt uitgevoerd.  

Deze stap kan in een standaardbesturingssysteem of in Windows PE worden uitgevoerd. Takenreeksvariabelen worden gelezen door takenreeksacties en bepalen het gedrag van deze acties. Zie voor meer informatie over specifieke takenreeksacties [Takenreeksacties](task-sequence-action-variables.md). Zie voor meer informatie over specifieke ingebouwde takenreeksvariabelen [Takenreeksvariabelen ingebouwde](/sccm/osd/understand/task-sequence-built-in-variables).

Klik in de takenreekseditor op **toevoegen**, selecteer **algemene**, en selecteer **Takenreeksvariabele instellen** om toe te voegen in deze stap. 

### <a name="properties"></a>Eigenschappen  
 Op de **eigenschappen** tabblad voor deze stap, configureer de instellingen die in deze sectie beschreven.  

 **Takenreeksvariabele**  
 Geef de naam van een takenreeks ingebouwde of actie variabele of uw eigen door de gebruiker gedefinieerde variabele naam opgeven.  

 **Waarde**  
 De takenreeks stelt de variabele op deze waarde. Deze takenreeksvariabele instellen op de waarde van een andere takenreeksvariabele met de syntaxis % varnaam %.  



##  <a name="BKMK_SetupWindowsandConfigMgr"></a> Windows en ConfigMgr installeren  
 Deze stap uitvoert de overgang van Windows PE naar het nieuwe besturingssysteem gebruiken. Deze takenreeksstap is een vereist onderdeel van iedere besturingssysteemimplementatie. Deze Configuration Manager-client installeert in het nieuwe besturingssysteem en bereidt de takenreeks op uitvoering in het nieuwe besturingssysteem.  

 Deze stap kan alleen in Windows PE worden uitgevoerd. De taak kan niet worden uitgevoerd in een standaardbesturingssysteem. Zie voor meer informatie over takenreeksvariabelen voor deze takenreeksactie [Windows en ConfigMgr installeren takenreeksacties](task-sequence-action-variables.md#BKMK_SetupWindows).  

 Deze stap vervangt sysprep.inf of unattend.xml directory variabelen, zoals % WINDIR % en % ProgramFiles %, door de Windows PE-installatiemap X:\Windows. De takenreeks wordt opgegeven met behulp van deze omgevingsvariabelen variabelen genegeerd.  

 Gebruik deze takenreeksstap om de volgende handelingen uit te voeren:  

1.  Voorbereidingen: Windows PE  

    1.  Vervang takenreeksvariabelen in het bestand unattend.xml.  

    2.  Download het pakket met de Configuration Manager-client. Het pakket toevoegen aan de geïmplementeerde installatiekopie.  

2.  Windows installeren  

    1.  Installatie op basis van een installatiekopie  

        1.  Schakel Configuration Manager-client in de afbeelding als deze bestaat. Met andere woorden, Autostart uitschakelen voor de Configuration Manager-client-service.  

        2.  Bijwerken van het register in de geïmplementeerde installatiekopie bij het starten van het geïmplementeerde besturingssysteem met dezelfde stationsletter als de referentiecomputer.  

        3.  Start opnieuw op naar het geïmplementeerde besturingssysteem.  

        4.  Windows Mini-Setup wordt uitgevoerd met behulp van de eerder opgegeven bestand sysprep.inf of het antwoordbestand unattend.xml dat alle eindgebruikers interactie onderdrukt. Als u de **netwerkinstellingen toepassen** stap lid worden van een domein en die informatie zich in het antwoordbestand. Windows Mini-Setup wordt de computer aan het domein.  

    2.  Installatie op basis van setup.exe.  Voert Setup.exe uit, die de standaard Windows-installatieprocedure volgt:  

        1.  Upgradepakket voor kopiëren van het besturingssysteem, opgegeven in de **besturingssysteem toepassen** stap naar de harde schijf.  

        2.  Start opnieuw op het zojuist geïmplementeerde besturingssysteem.  

        3.  Windows Mini-Setup wordt uitgevoerd met behulp van de eerder opgegeven bestand sysprep.inf of Unattend.XML, antwoord waarbij alle gebruikersinterface-onderdrukt instellingen. Als u de **netwerkinstellingen toepassen** stap lid worden van een domein en die informatie zich in het antwoordbestand. Windows Mini-Setup wordt de computer aan het domein.  

3.  Instellen van de Configuration Manager-client  

    1.  Nadat Windows Mini-Setup is voltooid, wordt de takenreeks hervat met behulp van setupcomplete.cmd.  

    2.  In- of uitschakelen van de lokale administrator-account op basis van de geselecteerde optie in de **Windows-instellingen toepassen** stap.  

    3.  De Configuration Manager-client installeren met behulp van de eerder gedownloade pakket en installatie-eigenschappen die zijn opgegeven in deze stap. De client is geïnstalleerd in 'inrichtingsmodus' om te voorkomen dat nieuwe beleidsaanvragen worden verwerkt totdat de takenreeks is voltooid.  

    4.  Wacht totdat de client volledig operationeel.  

4.  De takenreeks blijft uitvoeren van de volgende stap.  

<!-- Engineering confirmed that the task sequence does nothing with respect to group policy processing.
> [!NOTE]  
>  The **Setup Windows and ConfigMgr** task sequence action is responsible for running Group Policy on the newly installed computer. The Group Policy is applied after the task sequence is finished.  
-->

Klik in de takenreekseditor op **toevoegen**, selecteer **installatiekopieën**, en selecteer **Windows en ConfigMgr installeren** om toe te voegen in deze stap. 

### <a name="properties"></a>Eigenschappen  
 Op de **eigenschappen** tabblad voor deze stap, configureer de instellingen die in deze sectie beschreven.  

 **Clientpakket**  
 Klik op **Bladeren**, schakelt u het clientinstallatiepakket voor Configuration Manager wilt gebruiken bij deze stap.  

 **Gebruik pre-productieclientpakket indien beschikbaar**  
 Als er een pre-productieclientpakket beschikbaar is en de computer lid van de testverzameling is, de takenreeks dit pakket gebruikt in plaats van het productieclientpakket. De pre-productieclient is een nieuwere versie voor het testen in de productieomgeving. Klik op **Bladeren**, selecteer vervolgens het installatiepakket van de pre-productieclient wilt gebruiken bij deze stap.  

 **Installatie-eigenschappen**  
 Sitetoewijzing en de standaardconfiguratie worden automatisch opgegeven door de takenreeksactie. U kunt dit veld gebruiken om eventuele aanvullende installatie-eigenschappen op te geven die worden gebruikt bij installatie van de client. Als u meerdere installatie-eigenschappen wilt invoeren, scheidt u deze met een spatie.  

 U kunt opdrachtregelopties opgeven voor gebruik tijdens de clientinstallatie. U kunt bijvoorbeeld **/skipprereq: silverlight.exe** invoeren om aan CCMSetup.exe te communiceren dat de Microsoft Silverlight-vereiste niet moet worden geïnstalleerd. Zie voor meer informatie over beschikbare opdrachtregelopties voor CCMSetup.exe [over clientinstallatie-eigenschappen](../../core/clients/deploy/about-client-installation-properties.md).  

### <a name="options"></a>Opties
> [!NOTE]
> Schakel geen **Doorgaan bij fout** op de **opties** tabblad. Als er een fout opgetreden tijdens deze stap, mislukt de takenreeks wordt uitgevoerd of u deze instelling inschakelt of niet.



##  <a name="BKMK_UpgradeOS"></a> Besturingssysteem bijwerken  
 > [!TIP]  
 > Windows 10 versie 1709, vanaf bevat media meerdere edities. Bij het configureren van een takenreeks een upgradepakket voor besturingssysteem of de installatiekopie van het besturingssysteem te gebruiken, moet u selecteren een [edition ondersteund](/sccm/core/plan-design/configs/support-for-windows-10#windows-10-as-a-client).

 Deze stap gebruiken om te werken van een oudere versie van Windows naar een nieuwere versie van Windows 10.  

 Deze takenreeksstap kan alleen in een standaardbesturingssysteem worden uitgevoerd. De stap kan niet worden uitgevoerd in Windows PE.  

Klik in de takenreekseditor op **toevoegen**, selecteer **installatiekopieën**, en selecteer **besturingssysteem bijwerken** om toe te voegen in deze stap. 

### <a name="properties"></a>Eigenschappen  
Op de **eigenschappen** tabblad voor deze stap, configureer de instellingen die in deze sectie beschreven.  

**Upgradepakket**  
 Selecteer deze optie om het Windows 10-upgradepakket op te geven dat moet worden gebruikt voor de upgrade.  

**Bronpad**  
 Hiermee geeft u een lokaal pad of netwerkpad naar de Windows 10-medium dat Windows Setup wordt gebruikt. Deze instelling komt overeen met de Windows Setup-opdrachtregeloptie **/InstallFrom**. U kunt ook een variabele opgeven, zoals %mycontentpath% of %DPC01%. Wanneer u een variabele voor het bronpad gebruikt, moet u deze eerder in de takenreeks opgeven. Als u bijvoorbeeld de stap [Pakketinhoud downloaden](#BKMK_DownloadPackageContent) in de takenreeks gebruikt, kunt u een variabele voor de locatie van het upgradepakket voor het besturingssysteem opgeven. Vervolgens gebruikt u deze variabele voor het bronpad voor deze stap.  

**Editie**  
 Geef de editie in het besturingssysteemmedium op dat moet worden gebruikt voor de upgrade.  

**Productcode**  
 Geef de productcode op om op het upgradeproces toe te passen  

**Geef de volgende stuurprogramma-inhoud aan Windows Setup tijdens de upgrade**  
 Stuurprogramma's toevoegen aan de doelcomputer tijdens de upgrade. Deze instelling komt overeen met de Windows Setup-opdrachtregeloptie **/InstallDriver**. De stuurprogramma's moeten compatibel zijn met Windows 10. Geef een van de volgende opties:  

-   **Stuurprogrammapakket**: Klik op **Bladeren** en selecteer een bestaand stuurprogrammapakket in de lijst.  

-   **Tijdelijke inhoud**:  Selecteer deze optie om de locatie voor het stuurprogrammapakket te geven. U kunt een lokale map, netwerkpad of een takenreeksvariabele opgeven. Wanneer u een variabele voor het bronpad gebruikt, moet u deze eerder in de takenreeks opgeven. Bijvoorbeeld door de stap [Pakketinhoud downloaden](task-sequence-steps.md#BKMK_DownloadPackageContent) te gebruiken.  

**Time-out (minuten)**  
 Hiermee geeft u het aantal minuten voordat Configuration Manager deze stap mislukt. Deze optie is handig als Windows Setup stopt met de verwerking, maar niet beëindigt.  

**Windows-installatiecompatibiliteitsscan uitvoeren zonder de upgrade wordt gestart**  
 De Windows-installatiecompatibiliteitsscan uitvoeren zonder het upgradeproces te starten. Deze instelling komt overeen met de Windows Setup-opdrachtregeloptie **Compat ScanOnly**. Als u deze optie gebruikt, moet u de gehele installatiebron implementeren. Setup retourneert een afsluitcode als resultaat van de scan. In de volgende tabel staan enkele veelvoorkomende afsluitcodes.  

|Afsluitcode|Details|  
|-|-|  
|MOSETUP_E_COMPAT_SCANONLY (0xC1900210)|Geen compatibiliteitsproblemen (gelukt).|  
|MOSETUP_E_COMPAT_INSTALLREQ_BLOCK (0xC1900208)|Compatibiliteitsproblemen waarop actie kan worden ondernomen.|  
|MOSETUP_E_COMPAT_MIGCHOICE_BLOCK (0xC1900204)|Geselecteerde migratiekeuze is niet beschikbaar. Bijvoorbeeld een upgrade van Enterprise naar Professional.|  
|MOSETUP_E_COMPAT_SYSREQ_BLOCK (0xC1900200)|Komt niet in aanmerking voor Windows 10.|  
|MOSETUP_E_COMPAT_INSTALLDISKSPACE_BLOCK (0xC190020E)|Onvoldoende vrije schijfruimte.|  

Zie [Opdrachtregelopties voor Windows Setup](https://msdn.microsoft.com/library/windows/hardware/dn938368\(v=vs.85\).aspx) voor meer informatie over deze parameter  

**Verwijder compatibiliteitsberichten die kunnen worden genegeerd**  
 Hiermee geeft u op dat de installatie is voltooid, negeert alle compatibiliteitsberichten. Deze instelling komt overeen met de Windows Setup-opdrachtregeloptie **Compat IgnoreWarning**.  

**Installatie van Windows dynamisch bijwerken met Windows Update**  
 Configuratie geschikt voor dynamische Update bewerkingen uitvoeren, zoals zoeken, downloaden en installeren van updates. Deze instelling komt overeen met de Windows Setup-opdrachtregeloptie **/DynamicUpdate**. Deze instelling is niet compatibel is met Configuration Manager software-updates. Schakel deze optie wanneer u updates met zelfstandige Windows Server Update Services (WSUS) of Windows Update voor bedrijven beheert.  

**Beleid negeren en standaard Microsoft Update gebruiken** tijdelijk op het lokale beleid in realtime dynamische updatebewerkingen uitvoert en de computer updates downloaden van Windows Update.
