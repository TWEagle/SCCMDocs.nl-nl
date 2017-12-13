---
title: Stappen voor takenreeksen
titleSuffix: Configuration Manager
description: Meer informatie over de takenreeksstappen die u aan een takenreeks van Configuration Manager toevoegen kunt.
ms.custom: na
ms.date: 11/20/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: configmgr-osd
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 7c888a6f-8e37-4be5-8edb-832b218f266d
caps.latest.revision: "26"
caps.handback.revision: "0"
author: aczechowski
ms.author: aaroncz
manager: angrobe
ms.openlocfilehash: 3dce1f322936b38580c29459c1a4746b9b835d27
ms.sourcegitcommit: 08f9854fb6c6d21e1e923b13e38a64d0bc2bc9a4
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/12/2017
---
# <a name="task-sequence-steps-in-system-center-configuration-manager"></a>Stappen voor takenreeksen in System Center Configuration Manager

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*

De volgende takenreeksstappen kunnen worden toegevoegd aan een takenreeks van Configuration Manager. Zie [Edit a task sequence](../deploy-use/manage-task-sequences-to-automate-tasks.md#BKMK_ModifyTaskSequence) (Een takenreeks bewerken) voor meer informatie over het bewerken van een takenreeks.  

> [!TIP]  
> **Ondersteuning voor Windows 10 versie 1709 (ook wel bekend als de vallen auteurs Update)**.  Vanaf deze versie van Windows, bevat Windows media meerdere edities. Bij het configureren van een takenreeks om een upgradepakket voor besturingssysteem of de installatiekopie van besturingssysteem te gebruiken, moet u selecteren een [-editie die wordt ondersteund voor gebruik door Configuration Manager](/sccm/core/plan-design/configs/support-for-windows-10#windows-10-as-a-client).


##  <a name="BKMK_ApplyDataImage"></a>Takenreeksstap van gegevens gegevensinstallatiekopie toepassen  
 Gebruik de takenreeksstap **Gegevensinstallatiekopie toepassen** om de gegevensinstallatiekopie te kopiëren naar de opgegeven doelpartitie.  

 Deze stap kan alleen in Windows PE worden uitgevoerd. De taak kan niet worden uitgevoerd in een standaardbesturingssysteem. Zie voor meer informatie over de takenreeksvariabelen voor deze actie [Takenreeksacties](task-sequence-action-variables.md).  

### <a name="details"></a>Details  
 Op het tabblad **Eigenschappen** voor deze stap kunt u de instellingen configureren die in deze sectie worden beschreven.  

 Bovendien kunt u op het tabblad **Opties** de volgende acties uitvoeren:  

-   De stap uitschakelen.  

-   Opgeven of de takenreeks verder wordt uitgevoerd als er een fout optreedt tijdens het uitvoeren van de stap.  

-   Voorwaarden opgeven waaraan moet worden voldaan om de stap uit te voeren.  

 **Naam**  
 Een korte, door de gebruiker gedefinieerde naam opgeven die de uitgevoerde actie in deze stap beschrijft.  

 **Beschrijving**  
 Meer gedetailleerde informatie over de uitgevoerde actie in deze stap.  

 **Installatiekopiepakket**  
 Geef het **Installatiekopiepakket** op dat wordt gebruikt door deze takenreeksstap door te klikken op **Bladeren**. Selecteer het pakket dat u wilt installeren in het dialoogvenster **Pakket selecteren**. De bijbehorende eigenschapsinformatie voor elk bestaand installatiekopiepakket wordt weergegeven onder aan het dialoogvenster **Pakket selecteren**. Gebruik de vervolgkeuzelijst om de **Installatiekopie** te selecteren die u wilt installeren via het geselecteerde **Installatiekopiepakket**.  

> [!NOTE]  
>  Bij deze takenreeksactie wordt de installatiekopie beschouwd als een gegevensbestand en worden geen installatiestappen uitgevoerd om de installatiekopie op te starten als een besturingssysteem.  

 **Bestemming**  
 Hiermee geeft u een bestaande geformatteerde partitie en harde schijf, een specifieke logische stationsletter of de naam van een takenreeksvariabele met de logische stationsletter op.  

-   **Volgende beschikbare partitie** -de volgende sequentiële partitie gebruiken die niet eerder is geselecteerd door de actie besturingssysteem toepassen of gegevensinstallatiekopie toepassen in deze takenreeks.  

-   **Schijf en partitie opgeven** : Selecteer de **schijf** nummer (te beginnen met 0) en de **partitie** nummer (te beginnen met 1).  

-   **Logische stationsletter opgeven** -Geef de **stationsletter** die door Windows PE is toegewezen aan de partitie. Houd er rekening mee dat deze stationsletter kan afwijken van de stationsletter die door het zojuist geïmplementeerde besturingssysteem wordt toegewezen.  

-   **Logische stationsletter opgeslagen in een variabele** -Geef de takenreeksvariabele met de stationsletter die door Windows PE is toegewezen aan de partitie. Deze variabele wordt meestal ingesteld in de sectie Geavanceerd van het dialoogvenster **Partitie-eigenschappen** voor de takenreeksactie **Schijf formatteren en partitioneren**.  

 **Alle inhoud op de partitie verwijderen alvorens de installatiekopie toe te passen**  
 Hiermee geeft u op dat alle bestanden op de doelpartitie worden verwijderd voordat de installatiekopie wordt geïnstalleerd. Door de inhoud van de partitie niet te verwijderen, kan deze stap worden gebruikt om aanvullende inhoud toe te passen op een eerder gebruikte partitie.  

##  <a name="BKMK_ApplyDriverPackage"></a>Stuurprogrammapakket toepassen  
 Gebruik de takenreeksactie **Stuurprogrammapakket toepassen** om alle stuurprogramma's in het stuurprogrammapakket te downloaden en te installeren op het Windows-besturingssysteem.

 Met de takenreeksstap **Stuurprogrammapakket toepassen** worden alle apparaatstuurprogramma's in een stuurprogrammapakket beschikbaar gemaakt voor gebruik door Windows. Deze stap kan worden toegevoegd aan een takenreeks tussen de stap **Besturingssysteem toepassen** en de stap **Windows en ConfigMgr installeren** om de stuurprogramma's in het stuurprogrammapakket beschikbaar te maken voor Windows. Normaal gesproken wordt de stap **Stuurprogrammapakket toepassen** geplaatst na de takenreeksstap **Stuurprogramma's automatisch toepassen**. De takenreeksstap **Stuurprogrammapakket toepassen** is ook nuttig bij scenario's met implementatie van zelfstandige media.  

 Zorg dat vergelijkbare apparaatstuurprogramma's in een stuurprogrammapakket zijn geplaatst en distribueer deze naar de juiste distributiepunten. Nadat deze zijn gedistribueerd kunnen Configuration Manager-clientcomputers ze installeren. U kunt bijvoorbeeld alle apparaatstuurprogramma's van een fabrikant in een stuurprogrammapakket plaatsen en het pakket vervolgens distribueren naar distributiepunten waar de stuurprogramma's voor de bijbehorende computers toegankelijk zijn.

 Deze stap is nuttig voor zelfstandige media en voor beheerders die een specifieke set met stuurprogramma's willen installeren, inclusief stuurprogramma's voor apparaten die niet kunnen worden gedetecteerd tijdens een Plug en Play-scan (bijvoorbeeld netwerkprinters).  

 Deze takenreeksstap kan alleen in Windows PE worden uitgevoerd. De taak kan niet worden uitgevoerd in een standaardbesturingssysteem. Zie [Apply Driver Package Task Sequence Action Variables](task-sequence-action-variables.md#BKMK_ApplyDriverPackage) (Variabelen voor de takenreeksactie van een stuurprogrammapakket toepassen) voor meer informatie over de takenreeksvariabelen voor deze actie.  

### <a name="details"></a>Details  
 Op het tabblad **Eigenschappen** voor deze stap kunt u de instellingen configureren die in deze sectie worden beschreven.  

 Bovendien kunt u op het tabblad **Opties** de volgende acties uitvoeren:  

-   De stap uitschakelen.  

-   Opgeven of de takenreeks verder wordt uitgevoerd als er een fout optreedt tijdens het uitvoeren van de stap.  

-   Voorwaarden opgeven waaraan moet worden voldaan om de stap uit te voeren.  

 **Naam**  
 Een korte, door de gebruiker gedefinieerde naam opgeven die de uitgevoerde actie in deze stap beschrijft.  

 **Beschrijving**  
 Meer gedetailleerde informatie over de uitgevoerde actie in deze stap.  

 **Stuurprogrammapakket**  
 Geef het stuurprogrammapakket met de benodigde apparaatstuurprogramma's op door te klikken op **Bladeren** en het dialoogvenster **Pakket selecteren** te openen. Geef een bestaand pakket op dat u beschikbaar wilt maken. De eigenschappen van het bijbehorende pakket worden aan de onderkant van het dialoogvenster weergegeven.  

 **Selecteer het stuurprogramma voor massaopslag in het pakket dat moet worden geïnstalleerd vóór de installatie op besturingssystemen ouder dan Windows Vista.**  
 Geef eventuele apparaatstuurprogramma's voor massaopslag op die nodig zijn voor installaties op besturingssystemen ouder dan Windows Vista.  

 **Stuurprogramma**  
 Selecteer het apparaatstuurprogrammabestand voor massaopslag dat moet worden geïnstalleerd vóór de installatie in implementaties van besturingssystemen ouder dan Windows Vista. De vervolgkeuzelijst wordt op basis van het opgegeven pakket gevuld.  

 **Model**  
 Geef het voor opstarten essentiële apparaat op dat nodig is voor implementaties van besturingssystemen ouder dan Windows Vista.  

 **Installatie zonder toezicht van niet-ondertekende stuurprogramma's uitvoeren op versie van Windows wanneer dit is toegestaan**  
 Selecteer deze optie om stuurprogramma's in Windows te installeren die niet zijn ondertekend op de referentiecomputer.  

##  <a name="BKMK_ApplyNetworkSettings"></a>Stap netwerkinstellingen toepassen  
 Gebruik de takenreeksstap **Netwerkinstellingen toepassen** om de netwerk- of werkgroepconfiguratie-informatie op te geven voor de doelcomputer. De opgegeven waarden worden opgeslagen in de juiste antwoordbestandsindeling voor gebruik door Windows Setup wanneer de takenreeksstap **Windows en ConfigMgr installeren** wordt uitgevoerd.  

 Deze takenreeksstap kan in een standaardbesturingssysteem of in Windows PE worden uitgevoerd. Zie [Apply Network Settings Task Sequence Action Variables](task-sequence-action-variables.md#BKMK_ApplyNetworkSettings) (Variabelen voor de takenreeksacties van netwerkinstellingen toepassen) voor meer informatie over de takenreeksvariabelen voor deze actie.  

### <a name="details"></a>Details  
 Op het tabblad **Eigenschappen** voor deze stap kunt u de instellingen configureren die in deze sectie worden beschreven.  

 Bovendien kunt u op het tabblad **Opties** de volgende acties uitvoeren:  

-   De stap uitschakelen.  

-   Opgeven of de takenreeks verder wordt uitgevoerd als er een fout optreedt tijdens het uitvoeren van de stap.  

-   Voorwaarden opgeven waaraan moet worden voldaan om de stap uit te voeren.  

 **Naam**  
 Een korte, door de gebruiker gedefinieerde naam opgeven die de uitgevoerde actie in deze stap beschrijft.  

 **Beschrijving**  
 Meer gedetailleerde informatie over de uitgevoerde actie in deze stap.  

 **Lid worden van een werkgroep**  
 Selecteer deze optie om de doelcomputer toe te voegen aan de opgegeven werkgroep. Voer de naam van de werkgroep in op de regel **Werkgroep**. Deze waarde kan worden genegeerd door de waarde die is opgenomen door de takenreeksstap **Netwerkinstellingen vastleggen**.  

 **Lid worden van een domein**  
 Selecteer deze optie om de doelcomputer toe te voegen aan het opgegeven domein. Geef het domein op of blader hiernaartoe, zoals *fabricam.com*. Geef op of blader naar een Lightweight Directory Access Protocol (LDAP)-pad voor een organisatie-eenheid (dat wil zeggen LDAP / / OU = computers, DC=Fabricam.com, C = com).  

 **Account**  
 Klik op **Instellen** om een account op te geven met de vereiste machtigingen om de computer lid te laten worden van het domein. In de **Windows-gebruikersaccount** in het dialoogvenster kunt u de gebruikersnaam met de volgende notatie invoeren: **Domein\gebruiker** .  

 **Adapterinstellingen**  
 Netwerkconfiguraties opgeven voor elke netwerkadapter in de computer. Klik op **Nieuw** om het dialoogvenster **Netwerkinstellingen** te openen en geef vervolgens de netwerkinstellingen op. Als netwerkinstellingen zijn vastgelegd in een eerder exemplaar van de takenreeksstap **Netwerkinstellingen vastleggen**, worden de eerdere instellingen toegepast op de netwerkadapter en worden de opgegeven instellingen in deze stap niet toegepast. Als netwerkinstellingen niet eerder zijn vastgelegd, worden de opgegeven instellingen in de stap **Netwerkinstellingen toepassen** toegepast op netwerkadapters in volgorde van Windows-apparaatinventarisatie.  

##  <a name="BKMK_ApplyOperatingSystemImage"></a>Besturingssysteeminstallatiekopie toepassen  
 Gebruik de takenreeksstap **Besturingssysteeminstallatiekopie toepassen** om een besturingssysteem te installeren op de doelcomputer. Met deze takenreeksstap wordt een reeks acties uitgevoerd afhankelijk van of het besturingssysteem wordt geïnstalleerd via een besturingssysteeminstallatiekopie of een besturingssysteeminstallatiepakket.  

 Met de stap **Besturingssysteeminstallatiekopie toepassen** worden de volgende acties uitgevoerd als een installatiekopie van het besturingssysteem wordt gebruikt.  

1.  Hiermee verwijdert u alle inhoud op het betreffende volume, met uitzondering van de bestanden in de map die is opgegeven door de &#95; SMSTSUserStatePath takenreeksvariabele.  

2.  Hiermee wordt de inhoud van het opgegeven WIM-bestand uitgepakt naar de opgegeven doelpartitie.  

3.  Hiermee wordt het antwoordbestand voorbereid:  

    1.  Hiermee maakt u een nieuw standaard Windows Setup-antwoordbestand (sysprep.inf of unattend.xml) voor het besturingssysteem dat wordt geïmplementeerd.  

    2.  Hiermee worden alle waarden van het door de gebruiker opgegeven antwoordbestand samengevoegd.  

4.  Hiermee worden Windows-opstartlaadprogramma's gekopieerd naar de actieve partitie.  

5.  Hiermee wordt boot.ini of de Boot Configuration Database (BCD) ingesteld zodat deze naar het geïnstalleerde besturingssysteem verwijst.  

 Met de stap **Besturingssysteeminstallatiekopie toepassen** worden de volgende acties uitgevoerd als een installatiekopiepakket van het besturingssysteem wordt gebruikt.  

1.  Hiermee verwijdert u alle inhoud op het betreffende volume, met uitzondering van de bestanden in de map die is opgegeven door de &#95; SMSTSUserStatePath takenreeksvariabele.  

2.  Hiermee wordt het antwoordbestand voorbereid:  

    1.  Maakt een nieuw antwoordbestand met standaardwaarden gemaakt door Configuration Manager.  

    2.  Hiermee worden alle waarden van het door de gebruiker opgegeven antwoordbestand samengevoegd.  

> [!NOTE]  
>  De werkelijke installatie van Windows wordt gestart door de takenreeksstap **Windows en ConfigMgr installeren**. Nadat de takenreeksactie **Besturingssysteem toepassen** is uitgevoerd, wordt de takenreeksvariabele OSDTargetSystemDrive ingesteld op de stationsletter van de partitie met de besturingssysteembestanden.  

 Deze takenreeksstap kan alleen in Windows PE worden uitgevoerd. De taak kan niet worden uitgevoerd in een standaardbesturingssysteem. Zie [Apply Operating System Image Task Sequence Action Variables](task-sequence-action-variables.md#BKMK_ApplyOperatingSystem) (Variabelen voor de takenreeksactie van een installatiekopie van besturingssysteem toepassen) voor meer informatie over de takenreeksvariabelen voor deze actie.  

### <a name="details"></a>Details  
 Op het tabblad **Eigenschappen** voor deze stap kunt u de instellingen configureren die in deze sectie worden beschreven.  

 Bovendien kunt u op het tabblad **Opties** de volgende acties uitvoeren:  

-   De stap uitschakelen.  

-   **Rechtstreeks vanaf het distributiepunt toegang tot inhoud**:  

     Gebruik deze optie om op te geven of de takenreeks rechtstreeks vanuit het distributiepunt toegang heeft tot de installatiekopie van het besturingssysteem. Bijvoorbeeld: u kunt deze optie gebruiken bij het implementeren van besturingssystemen op ingesloten apparaten met beperkte opslagcapaciteit. Wanneer deze optie is geselecteerd, moet u ook de instellingen voor het delen van pakketten configureren op het tabblad **Gegevenstoegang** van de pakketeigenschappen.  

    > [!NOTE]  
    >  Met deze instelling wordt de geconfigureerde implementatieoptie op de pagina **Distributiepunten** van de **Wizard Software implementeren** alleen genegeerd voor de opgegeven installatiekopie van het besturingssysteem in deze takenreeksstap en niet alle inhoud voor de hele takenreeks.  

-   Opgeven of de takenreeks verder wordt uitgevoerd als er een fout optreedt tijdens het uitvoeren van de stap.  

-   Voorwaarden opgeven waaraan moet worden voldaan om de stap uit te voeren.  

 **Naam**  
 Een korte, door de gebruiker gedefinieerde naam opgeven die de uitgevoerde actie in deze stap beschrijft.  

 **Beschrijving**  
 Meer gedetailleerde informatie over de uitgevoerde actie in deze stap.  

 **Besturingssysteem toepassen vanuit een vastgelegd beeld**  
 Hiermee wordt een installatiekopie van een besturingssysteem geïnstalleerd die eerder is vastgelegd. Klik op **Bladeren** om het dialoogvenster **Pakket selecteren** te openen en selecteer vervolgens het bestaande installatiekopiepakket dat u wilt installeren. Als meerdere afbeeldingen zijn gekoppeld aan het opgegeven **installatiekopiepakket**, gebruikt u de vervolgkeuzelijst om de bijbehorende installatiekopie op te geven die wordt gebruikt voor deze implementatie. U kunt basisinformatie over elke bestaande installatiekopie weergeven door te klikken op de installatiekopie.  

 **Installatiekopie van besturingssysteem toepassen vanuit een originele installatiebron**  
 Hiermee wordt een besturingssysteem geïnstalleerd met behulp van een oorspronkelijke installatiebron. Klik op **Bladeren** om het dialoogvenster **Een installatiepakket voor besturingssysteem selecteren** te openen en selecteer vervolgens het bestaande besturingssysteeminstallatiepakket dat u wilt gebruiken. U kunt basisinformatie over elke bestaande installatiekopiebron weergeven door te klikken op de installatiekopiebron. De bijbehorende eigenschappen van de installatiekopie worden weergegeven in het resultatenvenster onder in het dialoogvenster. Als er meerdere edities zijn gekoppeld aan het opgegeven pakket, gebruikt u de vervolgkeuzelijst om de gebruikte bijbehorende **Editie** op te geven.  

 **Installatie zonder toezicht of sysprep-antwoordbestand gebruiken voor aangepaste installatie**  
 Gebruik deze optie om een Windows Setup-antwoordbestand op te geven (**unattend.xml**, **unattend.txt** of **sysprep.inf**), afhankelijk van de besturingssysteemversie en de installatiemethode. Het opgegeven bestand kan de standaardconfiguratieopties bevatten die worden ondersteund voor Windows-antwoordbestanden. Bijvoorbeeld: u kunt hiermee de standaardstartpagina voor Internet Explorer opgeven. U moet het pakket opgeven dat het antwoordbestand bevat en u moet het bijbehorende pad naar het bestand in het pakket opgeven.  

> [!NOTE]  
>  Het opgegeven Windows Setup-antwoordbestand kan ingesloten takenreeksvariabelen bevatten in de notatie %*varnaam*%, waarbij varnaam de naam van de variabele is. De tekenreeksen %*varnaam*% worden vervangen door de werkelijke waarden van de variabelen in de takenreeksactie **Windows en ConfigMgr installeren**. Let echter op dat dergelijke ingesloten takenreeksvariabelen niet kunnen worden gebruikt in velden die alleen numeriek zijn in het antwoordbestand unattend.xml.  

 Als u geen Windows Setup-antwoordbestand opgeeft, wordt met deze takenreeksactie een antwoordbestand automatisch gegenereerd.  

 **Bestemming**  
 Hiermee geeft u een bestaande geformatteerde partitie en harde schijf, een specifieke logische stationsletter of de naam van een takenreeksvariabele met de logische stationsletter op.  

-   **Volgende beschikbare partitie** -de volgende sequentiële partitie gebruiken die niet eerder is geselecteerd door de actie besturingssysteem toepassen of gegevensinstallatiekopie toepassen in deze takenreeks.  

-   **Schijf en partitie opgeven** : Selecteer de **schijf** nummer (te beginnen met 0) en de **partitie** nummer (te beginnen met 1).  

-   **Logische stationsletter opgeven** -Geef de **stationsletter** die door Windows PE is toegewezen aan de partitie. Houd er rekening mee dat deze stationsletter kan afwijken van de stationsletter die door het zojuist geïmplementeerde besturingssysteem wordt toegewezen.  

-   **Logische stationsletter opgeslagen in een variabele** -Geef de takenreeksvariabele met de stationsletter die door Windows PE is toegewezen aan de partitie. Deze variabele wordt meestal ingesteld in de sectie Geavanceerd van het dialoogvenster **Partitie-eigenschappen** voor de takenreeksactie **Schijf formatteren en partitioneren**.  

##  <a name="BKMK_ApplyWindowsSettings"></a>Windows-instellingen toepassen  
 Gebruik de takenreeksstap **Windows-instellingen toepassen** om de Windows-instellingen te configureren voor de doelcomputer. De opgegeven waarden worden opgeslagen in de juiste antwoordbestandsindeling voor gebruik door Windows Setup wanneer de takenreeksstap **Windows en ConfigMgr installeren** wordt uitgevoerd.  

 Deze takenreeksstap kan alleen in Windows PE worden uitgevoerd. De taak kan niet worden uitgevoerd in een standaardbesturingssysteem. Zie [Apply Windows Settings Task Sequence Action Variables](task-sequence-action-variables.md#BKMK_ApplyWindowsSettings) (Variabelen voor takenreeksacties van Windows-instellingen toepassen) voor meer informatie over de takenreeksvariabelen voor deze actie.  

### <a name="details"></a>Details  
 Op het tabblad **Eigenschappen** voor deze stap kunt u de instellingen configureren die in deze sectie worden beschreven.  

 Bovendien kunt u op het tabblad **Opties** de volgende acties uitvoeren:  

-   De stap uitschakelen.  

-   Opgeven of de takenreeks verder wordt uitgevoerd als er een fout optreedt tijdens het uitvoeren van de stap.  

-   Voorwaarden opgeven waaraan moet worden voldaan om de stap uit te voeren.  

 **Naam**  
 Een korte, door de gebruiker gedefinieerde naam opgeven die de uitgevoerde actie in deze stap beschrijft  

 **Beschrijving**  
 Meer gedetailleerde informatie over de uitgevoerde actie in deze stap.  

 **Gebruikersnaam**  
 Geef de naam op van de geregistreerde gebruikersnaam die is gekoppeld aan de doelcomputer. Deze waarde kan worden genegeerd door de waarde die is opgenomen door de takenreeksactie **Windows-instellingen vastleggen**.  

 **De naam van organisatie**  
 Geef de naam op van de geregistreerde organisatienaam die is gekoppeld aan de doelcomputer. Deze waarde kan worden genegeerd door de waarde die is opgenomen door de takenreeksactie **Windows-instellingen vastleggen**.  

 **Productcode**  
 Geef de productcode op die wordt gebruikt voor de installatie van Windows op de doelcomputer.  

 **Server-licentieverlening**  
 Geef de serverlicentiemodus op. U kunt **Per server** of **Per gebruiker** selecteren als licentiemodus. Als u Per server selecteert als licentiemodus, moet u ook het maximumaantal toegestane verbindingen conform uw licentieovereenkomst opgeven. Selecteer **Niet opgeven** als de doelcomputer geen server is of als u de licentiemodus niet wilt opgeven.  

 **Maximum aantal verbindingen**  
 Geef het maximumaantal beschikbare verbindingen voor deze computer op zoals vermeld in de gebruiksrechtovereenkomst.  

 **Willekeurig wachtwoord genereren voor lokale beheerder en het account uitschakelen op alle ondersteunde platforms (aanbevolen)**  
 Selecteer deze optie om een lokaal beheerderswachtwoord willekeurig te genereren. Hierdoor wordt een lokaal beheerderswachtwoord gemaakt en wordt het account uitgeschakeld op ondersteunde platforms.  

 **Het account inschakelen en lokaal beheerderswachtwoord instellen**  
 Selecteer deze optie om het lokale beheerdersaccount in te schakelen en het lokale beheerderswachtwoord te maken. Voer het wachtwoord in op de regel **Wachtwoord** en bevestig het wachtwoord op de regel **Wachtwoord bevestigen**.  

 **Tijdzone**  
 Geef de tijdzone op die u wilt configureren op de doelcomputer. Deze waarde kan worden genegeerd door de waarde die is opgenomen door de takenreeksstap **Windows-instellingen vastleggen**.  

##  <a name="BKMK_AutoApplyDrivers"></a>Stuurprogramma's automatisch toepassen  
 Gebruik de takenreeksstap **Stuurprogramma's automatisch toepassen** om stuurprogramma's te zoeken en installeren als onderdeel van de implementatie van het besturingssysteem.  

 Met de takenreeksactie **Stuurprogramma's automatisch toepassen** worden de volgende acties uitgevoerd:  

1.  Hiermee wordt de hardware gescand en worden de Plug en Play-id's gezocht voor alle aanwezige apparaten in het systeem.  

2.  Hiermee wordt de lijst met apparaten en hun Plug en Play-id's verzonden naar het beheerpunt. Met het beheerpunt wordt een lijst geretourneerd met compatibele stuurprogramma's van de stuurprogrammacatalogus voor elk apparaat. Het beheerpunt neemt alle stuurprogramma's in aanmerking, ongeacht het stuurprogrammapakket waartoe ze behoren. Alleen de stuurprogramma's die zijn gemarkeerd met de opgegeven stuurprogrammacategorie en de stuurprogramma's die niet zijn gemarkeerd als uitgeschakeld, worden in aanmerking genomen.  

3.  Voor elk apparaat kiest de client het beste stuurprogramma dat geschikt is voor het besturingssysteem waarop dit wordt geïmplementeerd en dat zich op een toegankelijk distributiepunt bevindt.  

4.  De geselecteerde stuurprogramma's worden gedownload vanaf een distributiepunt en voorgefaseerd op het doelbesturingssysteem.  

    1.  Voor installatiekopieën worden de stuurprogramma's in het stuurprogramma-archief van het besturingssysteem geplaatst.  

    2.  Voor installaties op basis van een installatie wordt Windows Setup geconfigureerd met waar de stuurprogramma's te vinden zijn.  

5.  Wanneer de takenreeksactie **Windows en ConfigMgr installeren** wordt uitgevoerd en Windows wordt opgestart, worden de stuurprogramma's gezocht die door deze actie zijn voorgefaseerd.  

> [!IMPORTANT]
>  De **stuurprogramma's automatisch toepassen** takenreeksstap kan niet worden gebruikt met zelfstandige media omdat Windows Setup dan geen verbinding met de Configuration Manager-site.

Deze takenreeksstap kan alleen in Windows PE worden uitgevoerd. De taak kan niet worden uitgevoerd in een standaardbesturingssysteem. Zie [Auto Apply Drivers Task Sequence Action Variables](task-sequence-action-variables.md#BKMK_AutoApplyDrivers) (Variabelen voor de takenreeksactie van een stuurprogramma automatisch toepassen) voor meer informatie over de takenreeksvariabelen voor deze actie.  

### <a name="details"></a>Details  
 Op het tabblad **Eigenschappen** voor deze stap kunt u de instellingen configureren die in deze sectie worden beschreven.  

 Bovendien kunt u op het tabblad **Opties** de volgende acties uitvoeren:  

-   De stap uitschakelen.  

-   Opgeven of de takenreeks verder wordt uitgevoerd als er een fout optreedt tijdens het uitvoeren van de stap.  

-   Voorwaarden opgeven waaraan moet worden voldaan om de stap uit te voeren.  

 **Naam**  
 Een korte, door de gebruiker gedefinieerde naam opgeven die de uitgevoerde actie in deze stap beschrijft.  

 **Beschrijving**  
 Meer gedetailleerde informatie over de uitgevoerde actie in deze stap.  

 **Installeer alleen de best overeenkomende compatibele stuurprogramma 's**  
 Hiermee geeft u aan dat met de takenreeksstap alleen het beste overeenkomende stuurprogramma voor elk gedetecteerd apparaat wordt geïnstalleerd.  

 **Alle compatibele stuurprogramma's installeren**  
 Hiermee geeft u aan dat met de takenreeksstap alle compatibele stuurprogramma's voor elk gedetecteerd apparaat worden geïnstalleerd en kiest Windows Setup het beste stuurprogramma. Deze optie vereist meer netwerkbandbreedte en schijfruimte omdat hierbij meer stuurprogramma's worden gedownload, maar deze optie kan er wel toe leiden dat een beter stuurprogramma wordt geselecteerd.  

 **Stuurprogramma's uit alle categorieën overwegen**  
 Hiermee geeft u aan dat met de takenreeksactie in alle beschikbare stuurprogrammacategorieën wordt gezocht naar de juiste apparaatstuurprogramma's.  

 **Zoeken naar passende stuurprogramma's tot bepaalde categorieën beperken**  
 Hiermee geeft u aan dat met de takenreeksactie in opgegeven stuurprogrammacategorieën naar de juiste apparaatstuurprogramma's wordt gezocht.  

 **Installatie zonder toezicht van niet-ondertekende stuurprogramma's op versies van Windows wanneer dit is toegestaan**  
 Hiermee kunnen met deze takenreeksactie niet-ondertekende apparaatstuurprogramma's van Windows worden geïnstalleerd.  

> [!IMPORTANT]  
>  Deze optie is niet van toepassing op besturingssystemen waarin beleid voor stuurprogramma-ondertekening niet kan worden geconfigureerd.  

##  <a name="BKMK_CaptureNetworkSettings"></a>Netwerkinstellingen vastleggen  
 Gebruik de takenreeksstap **Netwerkinstellingen vastleggen** om Microsoft-netwerkinstellingen vast te leggen van de computer waarop de takenreeks wordt uitgevoerd. De instellingen worden opgeslagen in takenreeksvariabelen die de standaardinstellingen negeren die u configureert in de takenreeksstap **Netwerkinstellingen toepassen**.  

 Deze takenreeksstap kan alleen in een standaardbesturingssysteem worden uitgevoerd. De stap kan niet worden uitgevoerd in Windows PE. Zie [Capture Network Settings Task Sequence Action Variables](task-sequence-action-variables.md#BKMK_CaptureNetworkSettings) (Variabelen voor takenreeksactie van netwerkinstellingen vastleggen) voor meer informatie over de takenreeksvariabelen voor deze actie.  

### <a name="details"></a>Details  
 Op het tabblad **Eigenschappen** voor deze stap kunt u de instellingen configureren die in deze sectie worden beschreven.  

 Bovendien kunt u op het tabblad **Opties** de volgende acties uitvoeren:  

-   De stap uitschakelen.  

-   Opgeven of de takenreeks verder wordt uitgevoerd als er een fout optreedt tijdens het uitvoeren van de stap.  

-   Voorwaarden opgeven waaraan moet worden voldaan om de stap uit te voeren.  

 **Naam**  
 Hiermee geeft u een korte, door de gebruiker gedefinieerde naam op die de uitgevoerde actie in deze stap beschrijft.  

 **Beschrijving**  
 Dit is meer gedetailleerde informatie over de uitgevoerde actie in deze stap.  

 **Lidmaatschap van domein en werkgroep migreren**  
 Hiermee worden de lidmaatschapsgegevens van het domein en de werkgroep van de doelcomputer vastgelegd.  

 **Netwerkadapterconfiguratie migreren**  
 Hiermee wordt de netwerkadapterconfiguratie van de doelcomputer vastgelegd. De vastgelegde informatie bevat de globale netwerkinstellingen, het aantal netwerkadapters en de netwerkinstellingen van elke adapter. Deze instellingen hebben betrekking op DNS, WINS, IP en poortfilters.  

##  <a name="BKMK_CaptureOperatingSystemImage"></a>Besturingssysteeminstallatiekopie vastleggen  
 Gebruik de takenreeksstap **Besturingssysteeminstallatiekopie vastleggen** om een of meer installatiekopieën van een referentiecomputer vast te leggen en op te slaan in een .wim-bestand op de opgegeven netwerkshare. Het besturingssysteem Wizard installatiekopie toevoegen kan vervolgens worden gebruikt te importeren. WIM-bestand naar Configuration Manager zodat deze kan worden gebruikt voor implementaties van besturingssystemen op basis van installatiekopieën.  

 Elk volume (station) op de referentiecomputer wordt vastgelegd als een afzonderlijke installatiekopie binnen het .wim-bestand. Als de computer waarnaar wordt verwezen meerdere volumes heeft, bevat het resulterende .wim-bestand een afzonderlijke installatiekopie voor elk volume. Alleen volumes die zijn geformatteerd als NTFS of FAT32 worden vastgelegd. Volumes met andere formatteringen en USB-volumes worden overgeslagen.  

 Het geïnstalleerde besturingssysteem op de referentiecomputer moet een versie van Windows die wordt ondersteund door Configuration Manager en moet met behulp van het hulpprogramma SysPrep zijn voorbereid. Het geïnstalleerde besturingssysteemvolume en het opstartvolume moeten hetzelfde volume zijn.  

 Bovendien moet u een Windows-account met schrijfmachtigingen invoeren voor de netwerkshare die u hebt geselecteerd.  

 Deze takenreeksstap kan alleen in Windows PE worden uitgevoerd. De taak kan niet worden uitgevoerd in een standaardbesturingssysteem. Zie [Capture Operating System Image Task Sequence Action Variables](task-sequence-action-variables.md#BKMK_CaptureOperatingSystemImage) (Variabelen voor de takenreeksactie van een installatiekopie van het besturingssysteem vastleggen) voor meer informatie over de takenreeksvariabelen voor deze actie.  

### <a name="details"></a>Details  
 Op het tabblad **Eigenschappen** voor deze stap kunt u de instellingen configureren die in deze sectie worden beschreven.  

 Bovendien kunt u op het tabblad **Opties** de volgende acties uitvoeren:  

-   De stap uitschakelen.  

-   Opgeven of de takenreeks verder wordt uitgevoerd als er een fout optreedt tijdens het uitvoeren van de stap.  

-   Voorwaarden opgeven waaraan moet worden voldaan om de stap uit te voeren.  

 **Naam**  
 Een korte, door de gebruiker gedefinieerde naam opgeven die de uitgevoerde actie in deze stap beschrijft.  

 **Beschrijving**  
 Meer gedetailleerde informatie over de uitgevoerde actie in deze stap.  

 **Doel**  
 Systeem bestandspad naar de locatie die Configuration Manager gebruikt bij het opslaan van de vastgelegde besturingssysteeminstallatiekopie.  

 **Beschrijving**  
 Een optionele, door de gebruiker gedefinieerde beschrijving van de vastgelegde besturingssysteeminstallatiekopie die is opgeslagen in het .wim-bestand.  

 **Versie**  
 Een optioneel, door de gebruiker gedefinieerd versienummer om toe te wijzen aan de vastgelegde besturingssysteeminstallatiekopie. Deze waarde kan een combinatie van letters en cijfers zijn en wordt opgeslagen in het .wim-bestand.  

 **Gemaakt door**  
 De optionele naam van de gebruiker die de installatiekopie van het besturingssysteem heeft gemaakt, die is opgeslagen in het .wim-bestand.  

 **Account besturingssysteeminstallatiekopie vastleggen**  
 U moet het Windows-account invoeren dat machtigingen heeft voor de netwerkshare die u hebt opgegeven. Klik op **Instellen** om de naam van het Windows-account op te geven.  

##  <a name="BKMK_CaptureUserState"></a>Gebruikersstatus vastleggen  
 Gebruik de takenreeksstap **Gebruikerstoestand vastleggen** om met het Hulpprogramma voor migratie van gebruikersstatus de gebruikersstatus en instellingen vast te leggen van de computer waarop de takenreeks wordt uitgevoerd. Deze takenreeksstap wordt gebruikt in combinatie met de takenreeksstap **Gebruikersstatus herstellen**. In USMT 3.0.1 en hoger wordt met deze optie altijd de USMT-Statusopslag versleuteld met een versleutelingssleutel die wordt gegenereerd en beheerd door Configuration Manager.  

 Zie voor meer informatie over het beheren van de gebruikersstatus bij het implementeren van besturingssystemen, [Gebruikersstatus beheren](../get-started/manage-user-state.md).  

 U kunt ook de **gebruikersstatus vastleggen** takenreeksstap met de **Statusopslag opvragen** en **Statusopslag vrijgeven** takenreeksstappen als u wilt de statusinstellingen opslaan in of herstellen uit een statusmigratiepunt punt in de Configuration Manager-site.  

 De takenreeksstap **Gebruikerstoestand vastleggen** biedt controle over een beperkte subset van de meest gebruikte USMT-opties. Aanvullende opdrachtregelopties kunnen worden opgegeven met de takenreeksvariabele OSDMigrateAdditionalCaptureOptions.  

 Deze takenreeksstap kan alleen in Windows PE worden uitgevoerd. De taak kan niet worden uitgevoerd in een standaardbesturingssysteem. Zie [Capture User State Task Sequence Action Variables](task-sequence-action-variables.md#BKMK_CaptureUserState) (Variabelen voor de takenreeksactie van gebruikersstatus vastleggen) voor meer informatie over de takenreeksvariabelen voor deze actie.  

### <a name="details"></a>Details  
 Op het tabblad **Eigenschappen** voor deze stap kunt u de instellingen configureren die in deze sectie worden beschreven.  

 Bovendien kunt u op het tabblad **Opties** de volgende acties uitvoeren:  

-   De stap uitschakelen.  

-   Opgeven of de takenreeks verder wordt uitgevoerd als er een fout optreedt tijdens het uitvoeren van de stap.  

-   Voorwaarden opgeven waaraan moet worden voldaan om de stap uit te voeren.  

 **Naam**  
 Een korte, door de gebruiker gedefinieerde naam opgeven die de uitgevoerde actie in deze stap beschrijft.  

 **Beschrijving**  
 Meer gedetailleerde informatie over de uitgevoerde actie in deze stap.  

 **Gebruiker pakket migratieprogramma gebruikersstatus**  
 Voer het Configuration Manager-pakket met de versie van USMT voor deze takenreeksstap te gebruiken bij het vastleggen van de gebruikersstatus en instellingen. Voor dit pakket is geen programma vereist. Wanneer de takenreeksstap wordt uitgevoerd, wordt de versie van USMT gebruikt in het pakket dat u opgeeft. Geef een pakket op met de 32-bits of x64-versie van USMT, afhankelijk van de architectuur van het besturingssysteem waarvan u de status vastlegt.  

 **Alle gebruikersprofielen vastleggen met standaardopties**  
 Selecteer deze optie alle gebruikersprofielinformatie te migreren. Deze optie is standaard geselecteerd.  

 Als u deze optie selecteert, maar niet de optie gebruikersprofielen lokale computer in de takenreeksstap gebruikersstatus herstellen selecteert, wordt de takenreeks mislukt omdat Configuration Manager de nieuwe accounts niet kan migreren zonder wachtwoorden toewijzen. Als u daarnaast de wizard **Nieuwe takenreeks maken** gebruikt en een takenreeks maakt van het type **Bestaand installatiekopiepakket installeren**, wordt de resulterende takenreeks standaard gebruikt als Alle gebruikersprofielen vastleggen met standaardopties, maar wordt de optie Gebruikersprofielen lokale computer herstellen (d.w.z. niet-domeinaccounts) niet geselecteerd.  

 Selecteer **Gebruikersprofielen lokale computer herstellen** en geef een wachtwoord op voor het account dat wordt gemigreerd. In een handmatig gemaakte takenreeks is deze instelling te vinden onder de stap Gebruikersstatus herstellen. In een takenreeks die is gemaakt door de wizard **Nieuwe takenreeks maken** is deze instelling te vinden op de wizardpagina voor de stap **Gebruikersbestanden en -instellingen herstellen**.  

 Dit is niet van toepassing als u geen lokale gebruikersaccounts hebt.  

 **Vastleggen van gebruikersprofielen aanpassen**  
 Selecteer deze optie om migratie van een aangepast profielbestand op te geven. Klik op **Bestanden** om de configuratiebestanden voor USMT te selecteren die u wilt gebruiken bij deze stap. U moet een aangepast .xml-bestand opgeven met de regels waarmee de te migreren gebruikersstatusbestanden worden gedefinieerd.  

 **Klik hier om configuratiebestanden te selecteren:**  
 Selecteer deze optie om de configuratiebestanden in het USMT-pakket te selecteren die u wilt gebruiken voor het vastleggen van gebruikersprofielen. Klik op de knop **Bestanden** om het dialoogvenster **Configuratiebestanden** te openen. Geef een configuratiebestand op door de naam van het bestand in te voeren op de regel **Bestandsnaam** en te klikken op de knop **Toevoegen**.  

 **Uitgebreide logboekregistratie inschakelen**  
 Schakel deze optie in om meer gedetailleerde informatie in het logboekbestand te genereren. Bij het vastleggen van status wordt het logboek Scanstate.log gegenereerd en standaard opgeslagen in de logboekmap voor de takenreeks in de map \windows\system32\ccm\logs.  

 **SKIP-bestanden met encrypted file system**  
 Schakel deze optie in als u het vastleggen wilt overslaan van bestanden die zijn versleuteld met Encrypted File System (EFS), met inbegrip van profielbestanden. Afhankelijk van het besturingssysteem en de USMT-versie zijn versleutelde bestanden mogelijk niet leesbaar na herstel. Zie de USMT-documentatie voor meer informatie.  

 **Kopiëren door toegang tot bestandssysteem**  
 Schakel deze optie in om een van de volgende instellingen op te geven:  

-   **Doorgaan als sommige bestanden niet kunnen worden vastgelegd**: Schakel deze instelling om door te gaan van het migratieproces, zelfs als sommige bestanden kunnen niet worden vastgelegd. De takenreeksstap mislukt als een bestand niet kan worden vastgelegd terwijl deze optie is uitgeschakeld. Deze optie is standaard ingeschakeld.  

-   **Lokaal vastleggen met koppelingen in plaats van door bestanden te kopiëren**: Schakel deze instelling om vaste NTFS-koppelingen te leggen van bestanden.  

     Voor meer informatie over het migreren van gegevens met vaste koppelingen raadpleegt u [Hard-Link Migration Store](http://go.microsoft.com/fwlink/p/?LinkId=240222)  

-   **Vastleggen in offline modus (alleen Windows PE)**: Schakel deze instelling om vast te leggen van de status van de gebruiker in Windows PE in plaats van het volledige besturingssysteem.  

 **Vastleggen met Volume Copy Shadow service (VSS)**  
 Met deze optie kunt u bestanden vastleggen, zelfs als deze door een andere toepassing voor bewerking zijn vergrendeld.  

##  <a name="BKMK_CaptureWindowsSettings"></a>Windows-instellingen vastleggen  
 Gebruik de takenreeksstap **Windows-instellingen vastleggen** om de Windows-instellingen vast te leggen van de computer waarop de takenreeks wordt uitgevoerd. De instellingen worden opgeslagen in takenreeksvariabelen die de standaardinstellingen negeren die u configureert in de takenreeksstap **Windows-instellingen toepassen**.  

 Deze takenreeksstap kan in Windows PE of een standaardbesturingssysteem worden uitgevoerd. Zie [Capture Windows Settings Task Sequence Action Variables](task-sequence-action-variables.md#BKMK_CaptureWindowsSettings) (Variabelen voor takenreeksacties van Windows-instellingen vastleggen) voor meer informatie over de takenreeksvariabelen voor deze actie.  

### <a name="details"></a>Details  
 Op het tabblad **Eigenschappen** voor deze stap kunt u de instellingen configureren die in deze sectie worden beschreven.  

 Bovendien kunt u op het tabblad **Opties** de volgende acties uitvoeren:  

-   De stap uitschakelen.  

-   Opgeven of de takenreeks verder wordt uitgevoerd als er een fout optreedt tijdens het uitvoeren van de stap.  

-   Voorwaarden opgeven waaraan moet worden voldaan om de stap uit te voeren.  

 **Naam**  
 Een korte, door de gebruiker gedefinieerde naam opgeven die de uitgevoerde actie in deze stap beschrijft.  

 **Beschrijving**  
 Meer gedetailleerde informatie over de uitgevoerde actie in deze stap.  

 **Computernaam migreren**  
 Selecteer deze optie om de NetBIOS-naam van de computer vast te leggen.  

 **Geregistreerde namen van gebruikers en organisaties migreren**  
 Selecteer deze optie om de geregistreerde namen van de gebruiker en organisatie vast te leggen van de computer.  

 **Tijdzone migreren**  
 Selecteer deze optie om de tijdzone-instelling op de computer vast te leggen.  

##  <a name="BKMK_CheckReadiness"></a>Gereedheid controleren  
 Gebruik de takenreeksstap **Gereedheid controleren** om te controleren of de doelcomputer voldoet aan de opgegeven voorwaarden voor de implementatievereisten.  

### <a name="details"></a>Details  
 Op het tabblad **Eigenschappen** voor deze stap kunt u de instellingen configureren die in deze sectie worden beschreven.  

 Bovendien kunt u op het tabblad **Opties** de volgende acties uitvoeren:  

-   De stap uitschakelen.  

-   Opgeven of de takenreeks verder wordt uitgevoerd als er een fout optreedt tijdens het uitvoeren van de stap. Selecteer deze instelling niet voor deze stap, anders worden alleen de gereedheidscontroles vastgelegd en wordt de takenreeks niet gestopt in geval van een mislukte controle.  

-   Voorwaarden opgeven waaraan moet worden voldaan om de stap uit te voeren.  

 **Naam**  
 Een korte, door de gebruiker gedefinieerde naam opgeven die de uitgevoerde actie in deze stap beschrijft.  

 **Beschrijving**  
 Meer gedetailleerde informatie over de uitgevoerde actie in deze stap.  

 **Minimumgeheugen garanderen (MB)**  
 Selecteer deze instelling om te controleren of de geïnstalleerde hoeveelheid geheugen (in megabytes) op de doelcomputer voldoet aan of hoger is dan de opgegeven waarde. Deze instelling is standaard geselecteerd.  

 **Minimale processorsnelheid garanderen (MHz)**  
 Selecteer deze instelling om te controleren of de snelheid (in megahertz) van de geïnstalleerde processor in de doelcomputer voldoet aan of hoger is dan de opgegeven waarde. Deze instelling is standaard geselecteerd.  

 **Zorg ervoor dat de minimale vrije schijfruimte (MB)**  
 Selecteer deze instelling om te controleren of de hoeveelheid vrije schijfruimte (in megabytes) op de doelcomputer voldoet aan of groter is dan de opgegeven waarde.  

 **Zorg ervoor dat de huidige OET worden vernieuwd**  
 Selecteer deze instelling om te controleren of het geïnstalleerde besturingssysteem op de doelcomputer voldoet aan de vereisten die u opgeeft. Deze instelling is standaard geselecteerd met de waarde **CLIENT**.  

##  <a name="BKMK_ConnectToNetworkFolder"></a>Verbinding maken met netwerkmap  
 Gebruik de takenreeksactie **Verbinding maken met netwerkmap** om een verbinding te maken met een gedeelde netwerkmap.  

 Deze takenreeksstap kan in een standaardbesturingssysteem of in Windows PE worden uitgevoerd. Zie [Connect to Network Folder Task Sequence Action Variables](task-sequence-action-variables.md#BKMK_ConnecttoNetworkFolder) (Variabelen voor takenreeksacties voor verbinden met netwerkmap) voor meer informatie over de takenreeksvariabelen voor deze actie.  

### <a name="details"></a>Details  
 Op het tabblad **Eigenschappen** voor deze stap kunt u de instellingen configureren die in deze sectie worden beschreven.  

 Bovendien kunt u op het tabblad **Opties** de volgende acties uitvoeren:  

-   De stap uitschakelen.  

-   Opgeven of de takenreeks verder wordt uitgevoerd als er een fout optreedt tijdens het uitvoeren van de stap.  

-   Voorwaarden opgeven waaraan moet worden voldaan om de stap uit te voeren.  

##  <a name="BKMK_DisableBitLocker"></a>BitLocker uitschakelen  
 Gebruik de takenreeksstap **BitLocker uitschakelen** om de BitLocker-versleuteling uit te schakelen op het huidige besturingssysteemstation of op een specifiek station. Met deze actie blijven de sleutelbeveiligingen in niet-versleutelde tekst achter op de harde schijf, maar wordt de inhoud van het station niet ontsleuteld. Deze actie wordt vervolgens bijna onmiddellijk voltooid.  

> [!NOTE]  
>  BitLocker-stationsversleuteling biedt versleuteling op laag niveau van de inhoud van een schijfvolume.  

 Als er meerdere stations zijn versleuteld, moet u BitLocker uitschakelen op alle gegevensstations voordat u BitLocker uitschakelt op het besturingssysteemstation.  

 Deze stap kan alleen in een standaardbesturingssysteem worden uitgevoerd. De stap kan niet worden uitgevoerd in Windows PE.  

### <a name="details"></a>Details  
 Op het tabblad **Eigenschappen** voor deze stap kunt u de instellingen configureren die in deze sectie worden beschreven.  

 Bovendien kunt u op het tabblad **Opties** de volgende acties uitvoeren:  

-   De stap uitschakelen.  

-   Opgeven of de takenreeks verder wordt uitgevoerd als er een fout optreedt tijdens het uitvoeren van de stap.  

-   Voorwaarden opgeven waaraan moet worden voldaan om de stap uit te voeren.  

 **Naam**  
 Hiermee geeft u een korte, door de gebruiker gedefinieerde naam op die de uitgevoerde actie in deze stap beschrijft.  

 **Beschrijving**  
 Dit is meer gedetailleerde informatie over de uitgevoerde actie in deze stap.  

 **Huidig besturingssysteemstation**  
 Hiermee wordt BitLocker uitgeschakeld op het huidige besturingssysteemstation.  

 **Specifiek station**  
 Hiermee wordt BitLocker uitgeschakeld op een specifiek station. Gebruik de vervolgkeuzelijst om het station op te geven waarop BitLocker wordt uitgeschakeld.  

##  <a name="BKMK_DownloadPackageContent"></a>Pakketinhoud downloaden  
 Gebruik de takenreeksstap **Pakketinhoud downloaden** om een van de volgende pakkettypen te downloaden:  

-   Installatiekopieën van besturingssysteem  

-   Upgradepakketten voor besturingssysteem  

-   Driverpakketten  

-   Pakketten  

 Deze stap werkt goed in een takenreeks om een besturingssysteem in de volgende scenario's te werken:  

-   Een enkele takenreeks gebruiken voor een upgrade die voor zowel x86- als x64-platforms werkt. Als u dit wilt doen, voegt u twee **Pakketinhoud downloaden**-stappen toe aan de groep **Upgrade voorbereiden** met de voorwaarden om de clientarchitectuur te detecteren en alleen het geschikte upgradepakket voor het besturingssystemen te downloaden. Configureer elke **Pakketinhoud downloaden**-stap zodanig dat dezelfde variabele wordt gebruikt, en gebruik de variabele voor het mediumpad in de stap **Besturingssysteem bijwerken**.  

-   Als u een geschikt stuurprogrammapakket wilt downloaden, gebruikt u twee **Pakketinhoud downloaden**-stappen op voorwaarde dat het juiste hardwaretype wordt gedetecteerd voor elk stuurprogrammapakket. Configureer elke **Pakketinhoud downloaden**-stap zodanig dat dezelfde variabele wordt gebruikt, en gebruik de variabele voor de waarde **Tijdelijke inhoud** in de sectie met stuurprogramma's in de stap **Besturingssysteem bijwerken**.  

> [!NOTE]    
> Wanneer u een takenreeks die de pakketinhoud downloaden stap bevat implementeert, schakel niet **alle inhoud lokaal downloaden voordat de takenreeks wordt gestart** voor **implementatieopties** op de **distributiepunten** pagina van de Wizard Software implementeren.  

Deze stap kan in een standaardbesturingssysteem of in Windows PE worden uitgevoerd. De optie voor het pakket opslaan in de Configuration Manager-clientcache wordt echter niet ondersteund in WinPE.

### <a name="details"></a>Details  
 Op het tabblad **Eigenschappen** voor deze stap kunt u de instellingen configureren die in deze sectie worden beschreven.  

 Bovendien kunt u op het tabblad **Opties** de volgende acties uitvoeren:  

-   De stap uitschakelen.  

-   Opgeven of de takenreeks verder wordt uitgevoerd als er een fout optreedt tijdens het uitvoeren van de stap.  

-   Voorwaarden opgeven waaraan moet worden voldaan om de stap uit te voeren.  

 **Naam**  
 Hiermee geeft u een korte, door de gebruiker gedefinieerde naam op die de uitgevoerde actie in deze stap beschrijft.  

 **Beschrijving**  
 Dit is meer gedetailleerde informatie over de uitgevoerde actie in deze stap.  

 Pictogram **Pakket selecteren**  
 Klik op het pictogram om het pakket te selecteren dat u wilt downloaden. Nadat u een pakket hebt geselecteerd, kunt u nog een keer op het pictogram klikken om een ander pakket te kiezen.  

 **De volgende locatie plaatsen**  
 U kunt het pakket op een van de volgende locaties opslaan:  

 -   **Werkmap voor takenreeksen**  

 -   **Configuration Manager-clientcache**: Deze optie kunt u de inhoud in de cache opslaan. Hierdoor kan de client als bron van een peer-cache voor andere peer-cacheclients fungeren. Zie voor meer informatie [voorbereiden Windows PE-peer-cache om WAN-verkeer te beperken](../get-started/prepare-windows-pe-peer-cache-to-reduce-wan-traffic.md).  

 -   **Aangepast pad**  

 **Pad opslaan als een variabele**  
 U kunt het pad opslaan als een variabele die u in een andere takenreeksstap kunt gebruiken. Configuration Manager voegt een numeriek achtervoegsel aan de variabelenaam toe. Bijvoorbeeld, als u een variabele van % opgeven*mycontent*% als aangepaste variabele, is de hoofdmap waarin alle inhoud waarnaar wordt verwezen is opgeslagen (dit kan meerdere pakketten zijn). Wanneer u naar de variabele verwijst, wordt u een numeriek achtervoegsel toevoegen aan de variabele. Bijvoorbeeld: voor het eerste pakket u wordt verwijzen naar %*mycontent01*% variabele. Wanneer u naar de variabele in een Vervolgstappen, zoals besturingssysteem bijwerken verwijst, gebruikt u %*mycontent02*% of %*mycontent03*%, waarbij het nummer overeenkomt met de volgorde waarin het pakket wordt vermeld in de stap.  

 **Als het downloaden van een pakket mislukt, doorgaan met downloaden van andere pakketten in de lijst**  
 Hiermee wordt aangegeven dat wanneer het downloaden van het pakket mislukt, er wordt doorgegaan naar het volgende pakket in de lijst en wordt dat gedownload.  

##  <a name="BKMK_EnableBitLocker"></a>BitLocker inschakelen  
 Gebruik de takenreeksstap **BitLocker inschakelen** om BitLocker-versleuteling in te schakelen op ten minste twee partities op de harde schijf. De eerste actieve partitie bevat de Windows-bootstrapcode. Een andere partitie bevat het besturingssysteem. De bootstrappartitie moet onversleuteld blijven.  

 Gebruik de takenreeksstap **BitLocker vooraf inrichten** om BitLocker in Windows PE in te schakelen op een station. Zie de sectie [BitLocker vooraf inrichten](#BKMK_PreProvisionBitLocker) in dit onderwerp voor meer informatie.  

> [!NOTE]  
>  BitLocker-stationsversleuteling biedt versleuteling op laag niveau van de inhoud van een schijfvolume.  

 De stap **BitLocker inschakelen** kan alleen in een standaardbesturingssysteem worden uitgevoerd. De stap kan niet worden uitgevoerd in Windows PE. Zie [Variabelen voor takenreeksacties van BitLocker inschakelen](task-sequence-action-variables.md#BKMK_EnableBitLocker) voor meer informatie over de takenreeksvariabelen voor deze actie.  

 Trusted Platform Module (Trusted) moet de volgende status hebben wanneer u **Alleen TPM**, **TPM en opstartsleutel op USB** of **TPM en pincode** opgeeft voordat u de stap **BitLocker inschakelen** kunt uitvoeren:  

-   Ingeschakeld  

-   Geactiveerd  

-   Eigendom toegestaan  

 Met de takenreeksstap kan elke resterende TPM-initialisatie worden voltooid omdat de resterende stappen geen fysieke aanwezigheid of herstarts vereisen. De resterende TPM-initialisatiestappen die transparant met **BitLocker inschakelen** (indien nodig) kunnen worden voltooid zijn als volgt:  

-   Goedkeuringssleutelpaar maken  

-   Eigenaarautorisatiewaarde en escrow maken voor Active Directory, dat moet zijn uitgebreid ter ondersteuning van deze waarde  

-   Eigenaar worden  

-   De opslaghoofdsleutel maken of opnieuw instellen als deze al aanwezig maar niet-compatibel is  

 Als u wilt dat tijdens de stap **BitLocker inschakelen** wordt gewacht totdat de stationsversleuteling is voltooid voordat de volgende stap in de takenreeks wordt verwerkt, schakelt u het selectievakje **Wachten** in. Als u het selectievakje **Wachten** niet inschakelt, wordt de stationsversleuteling uitgevoerd op de achtergrond en wordt de takenreeks onmiddellijk uitgevoerd tot de volgende stap.  

 BitLocker kan worden gebruikt voor het versleutelen van meerdere stations op een computersysteem (zowel het besturingssysteemstation als gegevensstations). Voor het versleutelen van een gegevensstation moet het besturingssysteem al zijn versleuteld en moet de versleuteling zijn voltooid, omdat de sleutelbeveiligingen voor de gegevensstations worden opgeslagen op het besturingssysteemstation. Hierdoor moet u, als u het besturingssysteemstation en het gegevensstation tijdens hetzelfde proces versleutelt, de optie Wachten selecteren voor de stap waarmee BitLocker wordt ingeschakeld voor het besturingssysteemstation.  

 Als de harde schijf al is versleuteld maar BitLocker is uitgeschakeld, wordt/worden met BitLocker inschakelen de sleutelbeveiliging(en) opnieuw ingeschakeld en vrijwel onmiddellijk voltooid. De harde schijf hoeft in dit geval niet nogmaals te worden versleuteld.  

 Zie [Variabelen voor takenreeksacties van BitLocker inschakelen](task-sequence-action-variables.md#BKMK_EnableBitLocker) voor meer informatie over de takenreeksvariabelen voor deze actie.  

### <a name="details"></a>Details  
 Op het tabblad **Eigenschappen** voor deze stap kunt u de instellingen configureren die in deze sectie worden beschreven.  

 Bovendien kunt u op het tabblad **Opties** de volgende acties uitvoeren:  

-   De stap uitschakelen.  

-   Opgeven of de takenreeks verder wordt uitgevoerd als er een fout optreedt tijdens het uitvoeren van de stap.  

-   Voorwaarden opgeven waaraan moet worden voldaan om de stap uit te voeren.  

 **Naam**  
 Hiermee geeft u een beschrijvende naam op voor deze takenreeksstap.  

 **Beschrijving**  
 Hiermee kunt u optioneel een beschrijving invoeren voor deze takenreeksstap.  

 **Kies het station om te versleutelen**  
 Hiermee geeft u het te versleutelen station op. Selecteer **Huidig besturingssysteemstation** om het huidige besturingssysteemstation te versleutelen en configureer vervolgens een van de volgende opties voor sleutelbeheer:  

-   **Alleen TPM**: Selecteer deze optie om alleen Trusted Platform Module (TPM) gebruiken.  

-   **Opstartsleutel op USB alleen**: Selecteer deze optie om een opstartsleutel die is opgeslagen op een USB-flashstation te gebruiken. Wanneer u deze optie selecteert, wordt de normale opstartprocedure door BitLocker vergrendeld totdat een USB-apparaat met een BitLocker-opstartsleutel wordt aangesloten op de computer.  

-   **TPM en opstartsleutel op USB**: Selecteer deze optie om TPM en een opstartsleutel die is opgeslagen op een USB-flashstation te gebruiken. Wanneer u deze optie selecteert, wordt de normale opstartprocedure door BitLocker vergrendeld totdat een USB-apparaat met een BitLocker-opstartsleutel wordt aangesloten op de computer.  

-   **TPM en PINCODE**:  Selecteer deze optie om TPM en pincode (PIN) te gebruiken. Wanneer u deze optie selecteert, wordt de normale opstartprocedure door BitLocker vergrendeld totdat de pincode is ingevoerd.  

 Selecteer **Specifiek station** om een specifiek gegevensstation (niet het besturingssysteemstation) te versleutelen en selecteer vervolgens het station in de lijst.  

 **Kies waar de herstelsleutel moet worden gemaakt**  
 U kunt opgeven waar het herstelwachtwoord wordt gemaakt door **In Active Directory** te selecteren zodat het wachtwoord in Active Directory wordt bewaard. Als u deze optie selecteert, moet u Active Directory voor de site uitbreiden zodat de bijbehorende BitLocker-herstelgegevens worden opgeslagen. U kunt ervoor kiezen geen wachtwoord te maken door **Geen herstelsleutel maken** te selecteren. Het wordt echter aanbevolen een wachtwoord te maken.  

 **Wacht totdat BitLocker het stationscoderingsproces op alle stations voordat de bewerking wordt voortgezet uitvoering van takenreeks voltooid**  
 Selecteer deze optie om de BitLocker-stationsversleuteling te voltooien voordat de volgende stap in de takenreeks wordt uitgevoerd. Als deze optie is geselecteerd, wordt het hele schijfvolume versleuteld voordat de gebruiker zich kan aanmelden op de computer.  

 De versleuteling kan uren duren wanneer een grote harde schijf wordt versleuteld. Als u deze optie niet selecteert, kan de takenreeks onmiddellijk worden voortgezet.  

##  <a name="BKMK_FormatandPartitionDisk"></a>Schijf formatteren en partitioneren  
 Gebruik de takenreeksstap **Schijf formatteren en partitioneren** om een opgegeven schijf op de doelcomputer te formatteren en partitioneren.  

> [!IMPORTANT]  
>  Elke instelling die u voor deze takenreeksstap opgeeft geldt voor één opgegeven schijf. Als u een andere schijf op de doelcomputer wilt formatteren en partitioneren, moet u een extra exemplaar van de takenreeksstap **Schijf formatteren en partitioneren** toevoegen aan de takenreeks.  

 Deze takenreeksstap kan alleen in Windows PE worden uitgevoerd. De taak kan niet worden uitgevoerd in een standaardbesturingssysteem. Zie [Format and Partition Disk Task Sequence Action Variables](task-sequence-action-variables.md#BKMK_FormatPartitionDisk) (Variabelen voor takenreeksacties voor schijfformattering en -partitionering) voor meer informatie over de takenreeksvariabelen voor deze actie.  

### <a name="details"></a>Details  
 Op het tabblad **Eigenschappen** voor deze stap kunt u de instellingen configureren die in deze sectie worden beschreven.  

 Bovendien kunt u op het tabblad **Opties** de volgende acties uitvoeren:  

-   De stap uitschakelen.  

-   Opgeven of de takenreeks verder wordt uitgevoerd als er een fout optreedt tijdens het uitvoeren van de stap.  

-   Voorwaarden opgeven waaraan moet worden voldaan om de stap uit te voeren.  

 **Naam**  
 Een korte, door de gebruiker gedefinieerde naam opgeven die de uitgevoerde actie in deze stap beschrijft.  

 **Beschrijving**  
 Meer gedetailleerde informatie over de uitgevoerde actie in deze stap.  

 **Schijfnummer**  
 Het fysieke schijfnummer van de schijf die wordt geformatteerd. Het nummer is gebaseerd op de rangschikking van Windows-schijfinventarisatie.  

 **Schijftype**  
 Het type van de schijf die wordt geformatteerd. Er zijn twee opties die u kunt selecteren in de vervolgkeuzelijst: 

-   Standaard(MBR) - Master Boot Record.  

-   GPT - GUID-partitietabel  

> [!NOTE]  
>  Als u het schijftype wijzigt van **Standaard (MBR)** in **GPT** terwijl de partitie-indeling een uitgebreide partitie bevat, worden alle uitgebreide en logische partities verwijderd uit de indeling. U wordt gevraagd om deze actie te bevestigen voordat u het schijftype kunt wijzigen.  

 **Volume**  
 Specifieke informatie over de partitie of het volume dat wordt gemaakt, met inbegrip van de volgende informatie:  

-   Naam  

-   Resterende schijfruimte  

 Klik op **Nieuw** om het dialoogvenster **Partitie-eigenschappen** te openen voor het maken van een nieuwe partitie. U kunt het partitietype en de grootte opgeven, en u kunt aangeven of de partitie een opstartpartitie is. Als u een bestaande partitie wilt wijzigen, klikt u op de te wijzigen partitie en klikt u vervolgens op de eigenschappenknop. Zie voor meer informatie over het configureren van hardeschijfpartities een van de volgende onderwerpen:  

-   [UEFI/GPT gebaseerde vaste schijfpartities configureren](http://go.microsoft.com/fwlink/?LinkID=272104)  

-   [BIOS/MBR-hardeschijfpartities configureren](http://go.microsoft.com/fwlink/?LinkId=272105)  

 Als u een partitie wilt verwijderen, selecteert u de gewenste partitie en klikt u vervolgens op **Verwijderen**.  

##  <a name="BKMK_InstallApplication"></a>Toepassing installeren  
 Gebruik de takenreeksstap **Toepassing installeren** om toepassingen te installeren als onderdeel van de takenreeks. Met deze stap kunt u een set toepassingen installeren die is gespecificeerd in de takenreeksstap of kunt u een set toepassingen installeren die is opgegeven via een dynamische lijst met takenreeksvariabelen. Als deze stap wordt uitgevoerd, begint de installatie van de toepassing onmiddellijk zonder te wachten op een polling-interval voor beleid.  

 De geïnstalleerde toepassingen moeten voldoen aan de volgende criteria:  

-   De toepassing moet een implementatietype van Windows Installer of Script Installer zijn. Implementatietypen voor Windows-app-pakket (appx-bestand) worden niet ondersteund.  

-   De software moet worden uitgevoerd onder het lokale systeemaccount en niet het gebruikersaccount.  

-   De toepassing mag geen interactie hebben met het bureaublad. Het programma moet stil of zonder toezicht worden uitgevoerd.  

-   De toepassing mag zelf geen herstart initiëren. De toepassing moet een herstart aanvragen via de standaardherstartcode, afsluitcode 3010. Hierdoor wordt ervoor gezorgd dat de herstart correct wordt afgehandeld tijdens de takenreeksstap. Als de toepassing afsluitcode 3010 retourneert, voert de onderliggende takenreeks-engine de herstart uit. Na het opnieuw opstarten wordt de takenreeks automatisch voortgezet.  

 Wanneer de stap **Toepassing installeren** wordt uitgevoerd, controleert de toepassing de toepasbaarheid van de vereisteregels en de detectiemethode voor de implementatietypen van de toepassing. Op basis van de resultaten van deze controle installeert de toepassing het toepasselijke implementatietype. Als een implementatietype afhankelijkheden bevat, wordt het afhankelijke implementatietype geëvalueerd en geïnstalleerd als onderdeel van de stap voor toepassingsinstallatie. Toepassingsafhankelijkheden worden niet ondersteund voor zelfstandige media.  

> [!NOTE]  
>  Voor het installeren van een toepassing die een andere toepassing vervangt, moeten de inhoudsbestanden voor de vervangen toepassing beschikbaar zijn, omdat de takenreeksstap anders mislukt. Bijvoorbeeld: Microsoft Visio 2010 is geïnstalleerd in een client of in een vastgelegde installatiekopie. Wanneer de takenreeksstap Toepassing installeren wordt uitgevoerd voor het installeren van Microsoft Visio 2013, moeten de inhoudsbestanden voor Microsoft Visio 2010 (de vervangen toepassing) beschikbaar zijn op een distributiepunt, omdat de takenreeks anders mislukt. Met een client of vastgelegde installatiekopie zonder geïnstalleerde versie van Microsoft Visio wordt de installatie van Microsoft Visio 2013 voltooid zonder te controleren of de Microsoft Visio 2010-inhoudsbestanden zijn gecontroleerd.  

> [!NOTE]
> U kunt de SMSTSMPListRequestTimeoutEnabled en ingebouwde variabelen voor de SMSTSMPListRequestTimeout inschakelen en Specificeer hoeveel milliseconden lang een takenreeks wacht voordat het opnieuw probeert te installeren van een toepassing of software-updatebestanden nadat deze is mislukt voor het opvragen van de beheerpuntlijst van locatieservices. Zie voor meer informatie [Task sequence ingebouwde varliables](task-sequence-built-in-variables.md).

 Deze takenreeksstap kan alleen in een standaardbesturingssysteem worden uitgevoerd. De stap kan niet worden uitgevoerd in Windows PE.  

### <a name="details"></a>Details  
 Op het tabblad **Eigenschappen** voor deze stap kunt u de instellingen configureren die in deze sectie worden beschreven.  

 Bovendien kunt u op het tabblad **Opties** de volgende acties uitvoeren:  

-   De stap uitschakelen.  

-   Geef op dat u deze stap opnieuw wilt uitvoeren als de computer onverwacht opnieuw wordt opgestart. U kunt ook opgeven hoe vaak u de stap na een herstart opnieuw wilt uitvoeren.  

-   Opgeven of de takenreeks verder wordt uitgevoerd als er een fout optreedt tijdens het uitvoeren van de stap.  

-   Voorwaarden opgeven waaraan moet worden voldaan om de stap uit te voeren.  

 **Naam**  
 Een korte, door de gebruiker gedefinieerde naam opgeven die de uitgevoerde actie in deze stap beschrijft.  

 **Beschrijving**  
 Meer gedetailleerde informatie over de uitgevoerde actie in deze stap.  

 **De volgende toepassingen installeren**  
 Met deze instelling geeft u de toepassingen op die worden geïnstalleerd in de volgorde waarin ze worden opgegeven.  

 Configuration Manager filtert alle uitgeschakelde toepassingen en alle toepassingen met de volgende instellingen. Deze toepassingen worden niet weergegeven in het dialoogvenster **Selecteer de te installeren toepassing**.  

-   Alleen als er een gebruiker is aangemeld  

-   Uitvoeren met gebruikersrechten  

 **Toepassingen installeren volgens dynamische variabelenlijst**  
 Deze instelling geeft de basisnaam aan voor een set takenreeksvariabelen die zijn gedefinieerd voor een verzameling of voor een computer. Met deze variabelen worden de toepassingen opgegeven die voor die verzameling of computer worden geïnstalleerd. De naam van elke variabele bestaat uit de gemeenschappelijke basisnaam plus een numeriek achtervoegsel dat begint bij 01. De waarde voor elke variabele moet de naam van de toepassing en niets anders bevatten.  

 Voor toepassingen die worden geïnstalleerd met behulp van een dynamische variabelenlijst, moet de volgende instelling zijn ingeschakeld op de **algemene** tabblad van de toepassing **eigenschappen** in het dialoogvenster: **Toestaan dat deze toepassing wordt geïnstalleerd door de toepassing installeren voor de takenreeksactie in plaats van handmatig implementeren**  

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

 De volgende voorwaarden zijn van invloed op wat wordt geïnstalleerd:  

-   Als de waarde van een variabele andere informatie bevat dan de naam van de toepassing, wordt de toepassing niet geïnstalleerd en wordt de takenreeks voortgezet.  

-   Als er geen variabele met de opgegeven basisnaam en het achtervoegsel '01' is gevonden, worden er geen toepassingen geïnstalleerd. Wanneer u selecteert **Doorgaan bij fout** op het tabblad Opties van de takenreeksstap de takenreeks verder wordt uitgevoerd wanneer een toepassing niet kan worden geïnstalleerd. Als u de instelling niet selecteert, mislukt de takenreeks en worden resterende toepassingen niet geïnstalleerd.  

 **Als een toepassing mislukt, doorgaan met installatie van andere toepassingen in de lijst**  
 Deze instelling geeft aan dat de stap wordt voorgezet als de installatie van een afzonderlijke toepassing mislukt. Als u deze instelling opgeeft, wordt de takenreeks voortgezet ongeacht eventuele installatiefouten die worden geretourneerd. Als u de instelling niet opgeeft, wordt de takenreeksstap onmiddellijk beëindigd wanneer een installatie mislukt.  

##  <a name="BKMK_InstallPackage"></a>Pakket installeren

 Gebruik de takenreeksstap **Pakket installeren** om software te installeren als onderdeel van de takenreeks. Als deze stap wordt uitgevoerd, begint de installatie onmiddellijk zonder te wachten op een polling-interval voor beleid.  

 De te installeren software moet voldoen aan de volgende criteria:  

-   De software moet worden uitgevoerd onder het lokale systeemaccount en niet het gebruikersaccount.  

-   De software mag geen interactie hebben met het bureaublad. Het programma moet stil of zonder toezicht worden uitgevoerd.  

-   De toepassing mag zelf geen herstart initiëren. De software moet een herstart aanvragen via de standaardherstartcode, afsluitcode 3010. Hierdoor wordt ervoor gezorgd dat de herstart correct wordt afgehandeld tijdens de takenreeksstap. Als de software afsluitcode 3010 retourneert, voert de onderliggende takenreeks-engine de herstart uit. Na het opnieuw opstarten wordt de takenreeks automatisch voortgezet.  

 Programma's die gebruikmaken van de optie **Eerst een ander programma uitvoeren** voor het installeren van een afhankelijk programma worden niet ondersteund bij het implementeren van een besturingssysteem. Als **Eerst een ander programma uitvoeren** is ingeschakeld voor de software en het afhankelijke programma al is uitgevoerd op de doelcomputer, wordt het afhankelijke programma uitgevoerd en wordt de takenreeks voortgezet. Als het afhankelijke programma echter nog niet is uitgevoerd op de doelcomputer, mislukt de takenreeksstap.  

> [!NOTE]  
>  De centrale beheersite beschikt niet over de benodigde beleidsregels voor clientconfiguratie om de agent voor softwaredistributie in te schakelen tijdens het uitvoeren van de takenreeks. Wanneer u op de centrale beheersite zelfstandige media maakt voor een takenreeks en de takenreeks de stap **Pakket installeren** bevat, wordt mogelijk de volgende fout weergegeven in het bestand CreateTsMedia.log:  
>   
>  `"WMI method SMS_TaskSequencePackage.GetClientConfigPolicies failed (0x80041001)"`  
>   
>  Bij zelfstandige media met de stap Pakket installeren moet u de zelfstandige media maken op een primaire site waarop de agent voor softwaredistributie is ingeschakeld, of moet u een stap **Opdrachtregel uitvoeren** toevoegen na de stap **Windows en ConfigMgr installeren** en voor de eerste stap **Pakket installeren**. Met de stap **Opdrachtregel uitvoeren** wordt een WMIC-opdracht uitgevoerd waarmee de agent voor softwaredistributie wordt ingeschakeld voordat de eerste stap Pakket installeren wordt uitgevoerd. U kunt de volgende opdracht gebruiken in de takenreeksstap **Opdrachtregel uitvoeren** :  
>   
>  **Opdrachtregel**: **WMIC/namespace:\\\root\ccm\policy\machine\requestedconfig path ccm_SoftwareDistributionClientConfig CREATE ComponentName = "Enable SWDist", Enabled = "true", LockSettings = "TRUE", PolicySource = "local", PolicyVersion = "1.0", SiteSettingsKey = "1" / NOINTERACTIVE**  
>   
>  Zie voor meer informatie over het maken van zelfstandige media [zelfstandige media maken](../deploy-use/create-stand-alone-media.md).  

 Deze takenreeksstap kan alleen in een standaardbesturingssysteem worden uitgevoerd. De stap kan niet worden uitgevoerd in Windows PE.  

### <a name="details"></a>Details  
 Op het tabblad **Eigenschappen** voor deze stap kunt u de instellingen configureren die in deze sectie worden beschreven.  

 Bovendien kunt u op het tabblad **Opties** de volgende acties uitvoeren:  

-   De stap uitschakelen.  

-   Opgeven of de takenreeks verder wordt uitgevoerd als er een fout optreedt tijdens het uitvoeren van de stap.  

-   Voorwaarden opgeven waaraan moet worden voldaan om de stap uit te voeren.  

 **Naam**  
 Een korte, door de gebruiker gedefinieerde naam opgeven die de uitgevoerde actie in deze stap beschrijft.  

 **Beschrijving**  
 Meer gedetailleerde informatie over de uitgevoerde actie in deze stap.  

 **Een enkel softwarepakket installeren**  
 Deze instelling geeft een Configuration Manager-softwarepakket. De stap wacht totdat de installatie is voltooid.  

 **Softwarepakketten installeren volgens dynamische variabelenlijst**  
 Deze instelling geeft de basisnaam aan voor een set takenreeksvariabelen die zijn gedefinieerd voor een verzameling of voor een computer. Met deze variabelen worden de pakketten opgegeven die voor die verzameling of computer worden geïnstalleerd. De naam van elke variabele bestaat uit de gemeenschappelijke basisnaam plus een numeriek achtervoegsel dat begint bij 001. De waarde voor elke variabele moet een pakket-id en de naam van de software bevatten en deze moeten zijn gescheiden door een dubbele punt.  

 Voor software die moet worden geïnstalleerd met behulp van een dynamische variabelenlijst, moet de volgende instelling zijn ingeschakeld op de **Geavanceerd** tabblad van het pakket **eigenschappen** in het dialoogvenster: **Toestaan dat dit programma wordt geïnstalleerd door de takenreeks pakket installeren zonder te worden geïmplementeerd**  

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

 De volgende voorwaarden zijn van invloed op wat wordt geïnstalleerd:  

-   Als de waarde van een variabele niet met de juiste notatie is gemaakt of geen geldige toepassings-id en -naam aangeeft, mislukt de installatie van de software.  

-   Als de pakket-id kleine letters bevat, mislukt de installatie van de software.  

-   Als er geen variabelen met de opgegeven basisnaam en het achtervoegsel '001' zijn gevonden, worden er geen pakketten geïnstalleerd en wordt de takenreeks voortgezet.  

 **Als de installatie van een softwarepakket mislukt, doorgaan met installatie van andere pakketten in de lijst**  
 Deze instelling geeft aan dat de stap wordt voorgezet als de installatie van een afzonderlijk softwarepakket mislukt. Als u deze instelling opgeeft, wordt de takenreeks voortgezet ongeacht eventuele installatiefouten die worden geretourneerd. Als u de instelling niet opgeeft, wordt de takenreeksstap onmiddellijk beëindigd wanneer een installatie mislukt.  

##  <a name="BKMK_InstallSoftwareUpdates"></a>Software-Updates installeren  
 Gebruik de takenreeksstap **Software-updates installeren** om software-updates te installeren op de doelcomputer. De doelcomputer wordt pas geëvalueerd voor toepasselijke software-updates als deze takenreeksstap wordt uitgevoerd. Op dat moment wordt de doelcomputer geëvalueerd voor software-updates zoals elke andere beheerd door Configuration Manager-client. Bij deze stap worden met name de software-updates geïnstalleerd die zijn gericht op verzamelingen waarvan de computer momenteel lid is.  
>  [!IMPORTANT]
>Het is raadzaam dat u de nieuwste versie van Windows Update Agent veel betere prestaties installeert wanneer u de takenreeksstap voor het Software-Updates installeren.
>* Zie [Knowledge base-artikel 3161647](https://support.microsoft.com/kb/3161647) voor Windows 7.
>* Zie [Knowledge base-artikel 3163023](https://support.microsoft.com/kb/3163023) voor Windows 8.

 Deze takenreeksstap kan alleen in een standaardbesturingssysteem worden uitgevoerd. De stap kan niet worden uitgevoerd in Windows PE. Zie [Install Software Updates Task Sequence Action Variables](task-sequence-action-variables.md#BKMK_InstallSoftwareUpdates) (Variabelen voor de takenreeksactie voor het installeren van software-updates) voor informatie over takenreeksvariabelen voor deze takenreeksactie.

 > [!NOTE]
 > U kunt de SMSTSMPListRequestTimeoutEnabled en ingebouwde variabelen voor de SMSTSMPListRequestTimeout inschakelen en Specificeer hoeveel milliseconden lang een takenreeks wacht voordat het opnieuw probeert te installeren van een toepassing of software-updatebestanden nadat deze is mislukt voor het opvragen van de beheerpuntlijst van locatieservices. Zie voor meer informatie [Takenreeksvariabelen ingebouwde](task-sequence-built-in-variables.md).

> [!NOTE]
>U kunt deze takenreeks configureren op het tabblad Opties, zodat de stap opnieuw wordt uitgevoerd als de computer onverwacht opnieuw wordt opgestart. Bijvoorbeeld bij de installatie van een software-update waarbij de computer automatisch opnieuw wordt opgestart. U kunt de variabele SMSTSWaitForSecondReboot om op te geven hoe lang (in seconden) de takenreeks moet worden onderbroken nadat de computer opnieuw is opgestart bij het installeren van software-updates vanaf Configuration Manager 1602 kan configureren. Zie voor meer informatie [Takenreeksvariabelen ingebouwde](task-sequence-built-in-variables.md).

### <a name="details"></a>Details  
 Op het tabblad **Eigenschappen** voor deze stap kunt u de instellingen configureren die in deze sectie worden beschreven.  

 Bovendien kunt u op het tabblad **Opties** de volgende acties uitvoeren:  

-   De stap uitschakelen.  

-   Geef op dat u deze stap opnieuw wilt uitvoeren als de computer onverwacht opnieuw wordt opgestart. U kunt ook opgeven hoe vaak u de stap na een herstart opnieuw wilt uitvoeren.  

-   Opgeven of de takenreeks verder wordt uitgevoerd als er een fout optreedt tijdens het uitvoeren van de stap.  

-   Voorwaarden opgeven waaraan moet worden voldaan om de stap uit te voeren.  

 **Naam**  
 Een korte, door de gebruiker gedefinieerde naam opgeven die de uitgevoerde actie in deze stap beschrijft.  

 **Beschrijving**  
 Meer gedetailleerde informatie over de uitgevoerde actie in deze stap.  

 **Vereist voor de installatie - alleen verplichte software-updates**  
 Selecteer deze optie voor het installeren van alle software-updates in Configuration Manager gemarkeerd als verplicht voor de doelcomputers die de takenreeks ontvangen. Voor vereiste software-updates gelden installatiedeadlines die door de beheerder zijn opgelegd.  

 **Beschikbaar voor installatie - alle software-updates**  
 Selecteer deze optie voor het installeren van alle beschikbare software-updates die gericht is op de Configuration Manager-verzameling die de takenreeks ontvangt. Alle beschikbare software-updates worden geïnstalleerd op de doelcomputers.  

 **Software-updates uit scanresultaten in het cachegeheugen evalueren**  
Vanaf Configuration Manager versie 1606 hebt u de optie een volledige scan voor software-updates uit te voeren, in plaats van de scanresultaten in het cachegeheugen te gebruiken. De takenreeks maakt standaard gebruik van resultaten in het cachegeheugen. U kunt het selectievakje uitschakelen zodat de client verbinding maakt met het software-updatepunt voor het verwerken en downloaden van de nieuwste software-updatecatalogus. Deze optie kunt u kiezen wanneer u een takenreeks gebruikt voor het [vastleggen en opbouwen van een installatiekopie van een besturingssysteem](../deploy-use/create-a-task-sequence-to-capture-an-operating-system.md), waarbij u al van tevoren weet dat er een groot aantal software-updates moet plaatsvinden, met name veel updates die afhankelijkheden hebben (u moet X installeren voordat Y wordt weergegeven als beschikbaar). Wanneer u deze instelling wist en de takenreeks op een groot aantal clients implementeren, verbindt ze alle met de software-updatepunt op hetzelfde moment. Dit kan tot prestatieproblemen leiden bij het verwerken en downloaden van de catalogus. In de meeste gevallen kunt u het beste de standaardinstelling gebruiken.

Er is een nieuwe takenreeksvariabele, SMSTSSoftwareUpdateScanTimeout, toegevoegd aan Configuration Manager versie 1606, waarmee u de time-out kunt instellen voor het scannen op software-updates gedurende de takenreeksstap voor het installeren van software-updates. De standaardwaarde is 30 minuten. Zie voor meer informatie [Takenreeksvariabelen ingebouwde](task-sequence-built-in-variables.md).


##  <a name="BKMK_JoinDomainorWorkgroup"></a>Lid worden van domein of werkgroep  
 Gebruik de takenreeksstap **Lid maken van domein of werkgroep** om de doelcomputer toe te voegen aan een werkgroep of domein.  

 Deze takenreeksstap kan alleen in een standaardbesturingssysteem worden uitgevoerd. De stap kan niet worden uitgevoerd in Windows PE. Zie [Join Domain or Workgroup Task Sequence Action Variables](task-sequence-action-variables.md#BKMK_JoinDomainWorkgroup) (Variabelen voor de takenreeksactie voor het lid worden van domein of werkgroep) voor informatie over takenreeksvariabelen voor deze takenreeksactie.  

### <a name="details"></a>Details  
 Op het tabblad **Eigenschappen** voor deze stap kunt u de instellingen configureren die in deze sectie worden beschreven.  

 Bovendien kunt u op het tabblad **Opties** de volgende acties uitvoeren:  

-   De stap uitschakelen.  

-   Opgeven of de takenreeks verder wordt uitgevoerd als er een fout optreedt tijdens het uitvoeren van de stap.  

-   Voorwaarden opgeven waaraan moet worden voldaan om de stap uit te voeren.  

 **Naam**  
 Een korte, door de gebruiker gedefinieerde naam opgeven die de uitgevoerde actie in deze stap beschrijft.  

 **Beschrijving**  
 Meer gedetailleerde informatie over de uitgevoerde actie in deze stap.  

 **Lid worden van een werkgroep**  
 Selecteer deze optie om de doelcomputer toe te voegen aan de opgegeven werkgroep. Als de computer momenteel lid van een domein is terwijl deze optie is geselecteerd, wordt de computer opnieuw opgestart.  

 **Lid worden van een domein**  
 Selecteer deze optie om de doelcomputer toe te voegen aan het opgegeven domein.  

 Typ optioneel een organisatie-eenheid (OE) of blader ernaartoe in het opgegeven domein waarvan u de computer lid wilt maken. Als de computer momenteel lid is van een ander domein of een werkgroep, wordt hierdoor de computer opnieuw opgestart. Als de computer al lid is van een andere organisatie-eenheid, mag u in Active Directory Domain Services de organisatie-eenheid niet wijzigen en wordt deze instelling genegeerd.  

 **Voer het account dat gemachtigd is aan het domein**  
 Klik op **Instellen** om een account met wachtwoord in te voeren dat is gemachtigd om lid te worden van het domein. Het account moet worden opgegeven in de volgende notatie:  

 *Domein\account*  

## <a name="BKMK_PrepareConfigMgrClientforCapture"></a>ConfigMgr-Client voorbereiden voor vastleggen  
Gebruik de **ConfigMgr-Client voorbereiden voor vastleggen** stap voor het verwijderen van Configuration Manager-client of de client op de referentiecomputer deze voorbereiden voor vastleggen als onderdeel van de installatiekopieprocedure configureren.

Vanaf Configuration Manager versie 1610, haalt de stap ConfigMgr-Client voorbereiden de Configuration Manager-client, in plaats van alleen het verwijderen van belangrijke gegevens. Wanneer de takenreeks wordt geïmplementeerd voor de vastgelegde besturingssysteeminstallatiekopie wordt deze elke keer dat een nieuwe Configuration Manager-client installeren.  

> [!Note]  
>  De client alleen wordt verwijderd tijdens de **samenstellen en vastleggen van een referentie-installatiekopie voor besturingssysteem** takenreeks. Andere methoden vastleggen, zoals vastleggende media of een aangepaste takenreeks worden niet verwijderd van de client.

Voorafgaand aan de Configuration Manager versie 1610 voert deze stap uit de volgende taken:  

-   Verwijdert de sectie met eigenschappen van de clientconfiguratie in het bestand smscfg.ini in de Windows-map. Deze eigenschappen zijn clientspecifieke informatie zoals de Configuration Manager-GUID en andere client-id.  

-   Verwijdert alle SMS of Configuration Manager-computercertificaten.  

-   Hiermee verwijdert u de Configuration Manager-clientcache.  

-   Wist de toegewezen sitevariabele voor de Configuration Manager-client.  

-   Hiermee verwijdert u alle lokale Configuration Manager-beleid.  

-   Hiermee verwijdert u de vertrouwde basissleutel voor de Configuration Manager-client.  

 Deze takenreeksstap kan alleen in een standaardbesturingssysteem worden uitgevoerd. De stap kan niet worden uitgevoerd in Windows PE.  

### <a name="details"></a>Details  
 Op het tabblad **Eigenschappen** voor deze stap kunt u de instellingen configureren die in deze sectie worden beschreven.  

 Bovendien kunt u op het tabblad **Opties** de volgende acties uitvoeren:  

-   De stap uitschakelen.  

-   Opgeven of de takenreeks verder wordt uitgevoerd als er een fout optreedt tijdens het uitvoeren van de stap.  

-   Voorwaarden opgeven waaraan moet worden voldaan om de stap uit te voeren.  

 **Naam**  
 Een korte, door de gebruiker gedefinieerde naam opgeven die de uitgevoerde actie in deze stap beschrijft.  

 **Beschrijving**  
 Meer gedetailleerde informatie over de uitgevoerde actie in deze stap.  

##  <a name="BKMK_PrepareWindowsforCapture"></a>Windows voorbereiden voor vastleggen  
 Gebruik de takenreeksstap **Windows voorbereiden voor vastleggen** om de Sysprep-opties op te geven die worden gebruikt bij het vastleggen van een installatiekopie van een besturingssysteem op de referentiecomputer. Met deze takenreeksactie wordt Sysprep uitgevoerd en wordt vervolgens de computer opnieuw opgestart naar de opstartinstallatiekopie voor Windows PE die is opgegeven voor de takenreeks. Deze actie kan alleen worden voltooid als de referentiecomputer niet lid is van een domein.  

 Deze takenreeksstap kan alleen in een standaardbesturingssysteem worden uitgevoerd. De stap kan niet worden uitgevoerd in Windows PE. Zie [Prepare Windows for Capture Task Sequence Action Variables](task-sequence-action-variables.md#BKMK_PrepareWindowsCapture) (Variabelen voor de takenreeksactie voor het voorbereiden van Windows op het vastleggen) voor informatie over takenreeksvariabelen voor deze takenreeksactie.  

### <a name="details"></a>Details  
 Op het tabblad **Eigenschappen** voor deze stap kunt u de instellingen configureren die in deze sectie worden beschreven.  

 Bovendien kunt u op het tabblad **Opties** de volgende acties uitvoeren:  

-   De stap uitschakelen.  

-   Opgeven of de takenreeks verder wordt uitgevoerd als er een fout optreedt tijdens het uitvoeren van de stap.  

-   Voorwaarden opgeven waaraan moet worden voldaan om de stap uit te voeren.  

 **Naam**  
 Een korte, door de gebruiker gedefinieerde naam opgeven die de uitgevoerde actie in deze stap beschrijft.  

 **Beschrijving**  
 Meer gedetailleerde informatie over de uitgevoerde actie in deze stap.  

 **Lijst van stuurprogramma's voor massaopslag automatisch samenstellen**  
 Selecteer deze optie om automatisch een lijst met stuurprogramma's voor massaopslag van de referentiecomputer te laten samenstellen door Sysprep. Met deze optie wordt de optie Build Mass Storage Drivers in het bestand sysprep.inf op de referentiecomputer ingeschakeld. Raadpleeg de documentatie van Sysprep voor meer informatie over deze instelling.  

 **Activatiemarkering niet resetten**  
 Selecteer deze optie om te voorkomen dat Sysprep de markering voor productactivering opnieuw instelt.  

##  <a name="BKMK_PreProvisionBitLocker"></a>BitLocker vooraf inrichten  
 Gebruik de takenreeksstap **BitLocker vooraf inrichten** om BitLocker in Windows PE in te schakelen op een station. Alleen de gebruikte schijfruimte is versleuteld. De versleutelingstijd is daarom veel sneller. Pas de sleutelbeheeropties toe met behulp van de takenreeksstap [BitLocker inschakelen](#BKMK_EnableBitLocker) nadat het besturingssysteem is geïnstalleerd. Deze stap kan alleen in Windows PE worden uitgevoerd. De taak kan niet worden uitgevoerd in een standaardbesturingssysteem.  

> [!IMPORTANT]  
>  Voor het vooraf inrichten van BitLocker moet u het besturingssysteem Windows 7 of hoger implementeren en moet TPM worden ondersteund en zijn ingeschakeld op de computer.  

### <a name="details"></a>Details  
 Op het tabblad **Eigenschappen** voor deze stap kunt u de instellingen configureren die in deze sectie worden beschreven.  

 Bovendien kunt u op het tabblad **Opties** de volgende acties uitvoeren:  

-   De stap uitschakelen.  

-   Opgeven of de takenreeks verder wordt uitgevoerd als er een fout optreedt tijdens het uitvoeren van de stap.  

-   Voorwaarden opgeven waaraan moet worden voldaan om de stap uit te voeren.  

 **Naam**  
 Geef een korte, door de gebruiker gedefinieerde naam op die de uitgevoerde actie in deze stap beschrijft.  

 **Beschrijving**  
 Geef meer gedetailleerde informatie op over de uitgevoerde actie in deze stap.  

 **BitLocker toepassen op het opgegeven station**  
 Geef het station op waarvoor u BitLocker wilt inschakelen. Alleen de gebruikte ruimte op het station wordt versleuteld.  

 **Deze stap overslaan voor computers die geen tmp hebben of wanneer tmp niet is ingeschakeld**  
 Selecteer deze optie om de stationsversleuteling over te slaan wanneer de computerhardware TPM niet ondersteunt of wanneer TPM niet is ingeschakeld. Bijvoorbeeld: u kunt deze optie gebruiken als u een besturingssysteem in een virtuele machine implementeert.  

##  <a name="BKMK_ReleaseStateStore"></a>Statusopslag vrijgeven  
 Gebruik de takenreeksstap **Statusopslag vrijgeven** om aan het statusmigratiepunt te communiceren dat het vastleggen of vrijgeven is voltooid. Deze stap wordt gebruikt in combinatie met de takenreeksstappen **Statusopslag opvragen**, **Gebruikerstoestand vastleggen** en **Gebruikersstatus herstellen** om statusgegevens van gebruikers te migreren met behulp van een statusmigratiepunt en het Hulpprogramma voor migratie van gebruikersstatus.  

 Zie voor meer informatie over het beheren van de gebruikersstatus bij het implementeren van besturingssystemen, [Gebruikersstatus beheren](../get-started/manage-user-state.md).  

 Als u toegang tot een statusmigratiepunt hebt aangevraagd om de gebruikersstatus vast te leggen in de takenreeksstap **Statusopslag opvragen**, wordt met deze stap aan het statusmigratiepunt gecommuniceerd dat het vastleggen is voltooid en dat de statusgegevens van de gebruiker kunnen worden hersteld. Het statusmigratiepunt stelt de toegangsbeheermachtigingen voor de vastgelegde status in zodat deze alleen toegankelijk is (als alleen-lezen) door de herstellende computer.  

 Als u toegang tot een statusmigratiepunt hebt aangevraagd om gebruikersstatus te herstellen in de takenreeksstap **Statusopslag opvragen**, wordt met deze takenreeksstap aan het statusmigratiepunt gecommuniceerd dat het herstellen is voltooid. Op dit moment worden bewaarinstellingen die u hebt geconfigureerd voor het statusmigratiepunt geactiveerd.  

> [!IMPORTANT]  
>  Het wordt aanbevolen **Doorgaan bij fout** in te stellen voor elke takenreeksstap tussen de stap **Statusopslag opvragen** en de stap **Statusopslag vrijgeven**, zodat elke takenreeksactie **Statusopslag opvragen** een overeenkomende takenreeksactie **Statusopslag vrijgeven** heeft.  

 Deze takenreeksstap kan alleen in een standaardbesturingssysteem worden uitgevoerd. De stap kan niet worden uitgevoerd in Windows PE. Zie [Variabelen voor de takenreeksactie voor vrijgeven van de statusopslag](task-sequence-action-variables.md#BKMK_ReleaseStateStore) voor informatie over takenreeksvariabelen voor deze takenreeksactie.  

### <a name="details"></a>Details  
 Op het tabblad **Eigenschappen** voor deze stap kunt u de instellingen configureren die in deze sectie worden beschreven.  

 Bovendien kunt u op het tabblad **Opties** de volgende acties uitvoeren:  

-   De stap uitschakelen.  

-   Opgeven of de takenreeks verder wordt uitgevoerd als er een fout optreedt tijdens het uitvoeren van de stap.  

-   Voorwaarden opgeven waaraan moet worden voldaan om de stap uit te voeren.  

 **Naam**  
 Een korte, door de gebruiker gedefinieerde naam opgeven die de uitgevoerde actie in deze stap beschrijft.  

 **Beschrijving**  
 Meer gedetailleerde informatie over de uitgevoerde actie in deze stap.  

##  <a name="BKMK_RequestStateStore"></a>Statusopslag opvragen  
 Gebruik de takenreeksstap **Statusopslag opvragen** om toegang aan te vragen tot een statusmigratiepunt bij het vastleggen van de status van een computer of het herstellen van de status naar een computer.  

 Zie voor meer informatie over het beheren van de gebruikersstatus bij het implementeren van besturingssystemen, [Gebruikersstatus beheren](../get-started/manage-user-state.md).  

 U kunt de takenreeksstap **Statusopslag opvragen** gebruiken in combinatie met de takenreeksstappen **Statusopslag vrijgeven**, **Gebruikerstoestand vastleggen** en **Gebruikersstatus herstellen** om computerstatus te migreren met behulp van een statusmigratiepunt en het Hulpprogramma voor migratie van gebruikersstatus.  

> [!NOTE]  
>  Als u een nieuwe siterol voor een statusmigratie hebt ingesteld, kan het tot één uur duren voordat de rol beschikbaar is voor gebruikerstatusopslag. U kunt de beschikbaarheid van het statusmigratiepunt versnellen door een willekeurige eigenschap van het statusmigratiepunt aan te passen om een update van het sitebesturingsbestand te activeren.  

 Deze takenreeksstap kan worden uitgevoerd in een standaardbesturingssysteem en in Windows PE voor offlinegebruik van het Hulpprogramma voor migratie van gebruikersstatus. Zie [Variabelen takenreeksactie Statusopslag opvragen](task-sequence-action-variables.md#BKMK_RequestState) voor informatie over de takenreeksvariabelen voor deze takenreeksactie.  

### <a name="details"></a>Details  
 Op het tabblad **Eigenschappen** voor deze stap kunt u de instellingen configureren die in deze sectie worden beschreven.  

 Bovendien kunt u op het tabblad **Opties** de volgende acties uitvoeren:  

-   De stap uitschakelen.  

-   Opgeven of de takenreeks verder wordt uitgevoerd als er een fout optreedt tijdens het uitvoeren van de stap.  

-   Voorwaarden opgeven waaraan moet worden voldaan om de stap uit te voeren.  

 **Naam**  
 Een korte, door de gebruiker gedefinieerde naam opgeven die de uitgevoerde actie in deze stap beschrijft.  

 **Beschrijving**  
 Meer gedetailleerde informatie over de uitgevoerde actie in deze stap.  

 **Status vastleggen vanaf de computer**  
 Hiermee zoekt u een statusmigratiepunt dat voldoet aan de minimumvereisten zoals geconfigureerd in de instellingen van het statusmigratiepunt (maximumaantal clients en minimale hoeveelheid vrije schijfruimte), maar er wordt niet gegarandeerd dat er voldoende ruimte beschikbaar is op het moment van de statusmigratie. Als u deze optie selecteert, wordt om toegang tot het statusmigratiepunt gevraagd om de gebruikersstatus en instellingen van een computer vast te leggen.  

 Als de Configuration Manager-site meerdere statusmigratiepunten zijn ingeschakeld heeft, zoekt deze takenreeksstap een statusmigratiepunt met beschikbare schijfruimte beheerpunt van de site voor een lijst met statusmigratiepunten op te zoeken en vervolgens elk statusmigratiepunt te evalueren totdat er een wordt gevonden dat voldoet aan de minimumvereisten.  

 **Status herstellen vanaf een andere computer**  
 Selecteer deze optie om toegang tot een statusmigratiepunt aan te vragen om eerder vastgelegde gebruikersstatus en instellingen op een doelcomputer te herstellen.  

 Als de Configuration Manager-site meerdere statusmigratiepunten heeft, zoekt deze takenreeksstap het statusmigratiepunt dat de computerstatus heeft die is opgeslagen voor de doelcomputer.  

 **Aantal nieuwe pogingen**  
 Het aantal pogingen dat met deze takenreeksstap wordt uitgevoerd om een geschikt statusmigratiepunt te zoeken voordat de stap mislukt.  

 **Wachttijd nieuwe poging (seconden)**  
 De hoeveelheid tijd in seconden dat de takenreeksstap moet wachten tussen nieuwe pogingen.  

 **Als het computeraccount geen verbinding maken met Statusopslag, gebruikt u het netwerktoegangsaccount.**  
 Hiermee geeft u op dat de accountreferenties voor toegang van Configuration Manager netwerk verbinding maken met het statusmigratiepunt als de Configuration Manager-client geen toegang tot de Statusopslag van SMP via het computeraccount wordt gebruikt. Deze optie is minder veilig, omdat het netwerktoegangsaccount op andere computers kan worden gebruikt om uw opgeslagen status op te vragen. De optie is mogelijk wel vereist als de doelcomputer niet lid is van een domein.  

##  <a name="BKMK_RestartComputer"></a>Computer opnieuw opstarten  
 Gebruik de takenreeksstap **Computer opnieuw opstarten** om de computer waarop de takenreeks wordt uitgevoerd opnieuw op te starten. Na het opnieuw opstarten gaat de computer automatisch door met de volgende stap in de takenreeks.  

 Deze stap kan in een standaardbesturingssysteem of in Windows PE worden uitgevoerd. Zie voor meer informatie over de takenreeksvariabelen voor deze takenreeksactie [opnieuw opstarten van computer takenreeksacties](task-sequence-action-variables.md#BKMK_RestartComputer).  

### <a name="details"></a>Details  
 Op het tabblad **Eigenschappen** voor deze stap kunt u de instellingen configureren die in deze sectie worden beschreven.  

 Bovendien kunt u op het tabblad **Opties** de volgende acties uitvoeren:  

-   De stap uitschakelen.  

-   Opgeven of de takenreeks verder wordt uitgevoerd als er een fout optreedt tijdens het uitvoeren van de stap.  

-   Voorwaarden opgeven waaraan moet worden voldaan om de stap uit te voeren.  

 **Naam**  
 Een korte, door de gebruiker gedefinieerde naam opgeven die de uitgevoerde actie in deze stap beschrijft.  

 **Beschrijving**  
 Meer gedetailleerde informatie over de uitgevoerde actie in deze stap.  

 **De opstartinstallatiekopie toegewezen aan deze takenreeks**  
 Selecteer deze optie voor de doelcomputer om de opstartinstallatiekopie te gebruiken die is toegewezen aan de takenreeks. De opstartinstallatiekopie wordt gebruikt voor het uitvoeren van volgende takenreeksstappen die worden uitgevoerd in Windows PE.  

 **Het momenteel geïnstalleerde standaardbesturingssysteem**  
 Selecteer deze optie voor de doelcomputer om deze opnieuw op te starten naar het geïnstalleerde besturingssysteem.  

 **De gebruiker waarschuwen voordat opnieuw wordt opgestart**  
 Selecteer deze optie om een melding te tonen aan de gebruiker dat de doelcomputer opnieuw wordt opgestart. Deze optie is standaard geselecteerd.  

 **Tekst van melding**  
 Geef een bericht op dat wordt getoond aan de gebruiker voordat de doelcomputer opnieuw wordt opgestart.  

 **Time-out voor weergave melding**  
 Geef de tijdsduur in seconden op dat een gebruiker krijgt voordat de doelcomputer opnieuw wordt opgestart. De standaardhoeveelheid tijd is zestig (60) seconden.  

##  <a name="BKMK_RestoreUserState"></a>Gebruikersstatus herstellen  
 Gebruik de takenreeksstap **Gebruikersstatus herstellen** om het Hulpprogramma voor migratie van gebruikersstatus te initiëren voor het herstellen van gebruikersstatus en instellingen op de doelcomputer. Deze takenreeksstap wordt gebruikt in combinatie met de takenreeksstap **Gebruikerstoestand vastleggen**.  

 Zie voor meer informatie over het beheren van de gebruikersstatus bij het implementeren van besturingssystemen, [Gebruikersstatus beheren](../get-started/manage-user-state.md).  

 U kunt ook de **gebruikersstatus herstellen** takenreeksstap met de **Statusopslag opvragen** en **Statusopslag vrijgeven** takenreeksstappen als u wilt de statusinstellingen opslaan in of herstellen uit een statusmigratiepunt punt in de Configuration Manager-site. In USMT 3.0 en hoger wordt met deze ontsleuteld optie altijd de USMT-Statusopslag met behulp van een versleutelingssleutel die wordt gegenereerd en beheerd door Configuration Manager.  

 De takenreeksstap **Gebruikersstatus herstellen** biedt controle over een beperkte subset van de meest gebruikte USMT-opties. Aanvullende opdrachtregelopties kunnen worden opgegeven met de takenreeksvariabele OSDMigrateAdditionalRestoreOptions.  

> [!IMPORTANT]  
>  Als u de takenreeksstap **Gebruikersstatus herstellen** gebruikt voor een doel dat geen verband houdt met een implementatiescenario van een besturingssysteem, voegt u de takenreeksstap [Computer opnieuw opstarten](#BKMK_RestartComputer) onmiddellijk toe na de takenreeksstap **Gebruikersstatus herstellen**.  

 Deze takenreeksstap kan alleen in een standaardbesturingssysteem worden uitgevoerd. De stap kan niet worden uitgevoerd in Windows PE. Zie [Restore User State Task Sequence Action Variables](task-sequence-action-variables.md#BKMK_RestoreUserState) (Variabelen voor de takenreeksactie voor het herstellen van de gebruikersstatus) voor informatie over de takenreeksvariabelen voor deze takenreeksactie.  

### <a name="details"></a>Details  
 Op het tabblad **Eigenschappen** voor deze stap kunt u de instellingen configureren die in deze sectie worden beschreven.  

 Bovendien kunt u op het tabblad **Opties** de volgende acties uitvoeren:  

-   De stap uitschakelen.  

-   Opgeven of de takenreeks verder wordt uitgevoerd als er een fout optreedt tijdens het uitvoeren van de stap.  

-   Voorwaarden opgeven waaraan moet worden voldaan om de stap uit te voeren.  

 **Naam**  
 Hiermee geeft u een korte, door de gebruiker gedefinieerde naam op die de uitgevoerde actie in deze stap beschrijft.  

 **Beschrijving**  
 Dit is meer gedetailleerde informatie over de uitgevoerde actie in deze stap.  

 **Gebruiker pakket migratieprogramma gebruikersstatus**  
 Voer het Configuration Manager-pakket met de versie van USMT voor deze stap moet worden gebruikt bij het herstellen van de gebruikersstatus en instellingen. Voor dit pakket is geen programma vereist. Wanneer de takenreeksstap wordt uitgevoerd, wordt de versie van USMT gebruikt in het pakket dat u opgeeft. Geef een pakket op met de 32-bits of x64-versie van USMT, afhankelijk van de architectuur van het besturingssysteem waarnaar u de status herstelt.  

 **Alle vastgelegde gebruikersprofielen met standaardopties herstellen**  
 Hiermee worden de vastgelegde gebruikersprofielen hersteld met de standaardopties. Selecteer **Vastlegging gebruikersprofiel aanpassen** om de opties aan te passen die worden hersteld.  

 **Herstellen van gebruikersprofielen aanpassen**  
 Hiermee kunt u de bestanden aanpassen die u wilt herstellen naar de doelcomputer. Klik op **Bestanden** om de configuratiebestanden in het USMT-pakket op te geven die u wilt gebruiken voor het herstellen van de gebruikersprofielen. Geef de naam van het bestand op in het vak **Bestandsnaam** en klik vervolgens op **Toevoegen** om een configuratiebestand toe te voegen. De gebruikte configuratiebestanden voor de bewerking worden vermeld in het deelvenster Bestanden. Het .xml-bestand dat u opgeeft definieert het gebruikersbestand dat wordt hersteld.  

 **Gebruikersprofielen lokale computer herstellen**  
 Hiermee worden de profielen van de lokale computergebruiker (d.w.z. niet domeingebruiker) hersteld. U moet nieuwe wachtwoorden toewijzen aan de herstelde lokale gebruikersaccounts, omdat de oorspronkelijke wachtwoorden voor lokale gebruikersaccounts niet kunnen worden gemigreerd. Voer het nieuwe wachtwoord in het vak **Wachtwoord** in en bevestig het wachtwoord in het vak **Wachtwoord bevestigen**.  

 **Doorgaan als sommige bestanden kunnen niet worden hersteld**  
 Hiermee wordt het herstellen van gebruikersstatus en instellingen voortgezet zelfs als bepaalde bestanden niet kunnen worden hersteld. Deze optie is standaard ingeschakeld. Als u deze optie uitschakelt terwijl er fouten zijn opgetreden tijdens het herstellen van bestanden, wordt de takenreeksstap onmiddellijk beëindigd met een fout en worden niet alle bestanden hersteld.  

 **Uitgebreide logboekregistratie inschakelen**  
 Schakel deze optie in om meer gedetailleerde informatie in het logboekbestand te genereren. Bij het herstellen van status wordt het logboek Loadstate.log gegenereerd en standaard opgeslagen in de logboekmap voor de takenreeks in de map \windows\system32\ccm\logs.  

##  <a name="BKMK_RunCommandLine"></a>Opdrachtregel uitvoeren  
 Gebruik de takenreeksstap **Opdrachtregel uitvoeren** om een opgegeven opdrachtregel uit te voeren.  

 Deze stap kan in een standaardbesturingssysteem of in Windows PE worden uitgevoerd. Zie [Run Command Line Task Sequence Action Variables](task-sequence-action-variables.md#BKMK_RunCommand) (Variabelen voor de takenreeksactie voor het uitvoeren van de opdrachtregel) voor informatie over takenreeksvariabelen voor deze takenreeksactie.  

### <a name="details"></a>Details  
 Op het tabblad **Eigenschappen** voor deze stap kunt u de instellingen configureren die in deze sectie worden beschreven.  

 Bovendien kunt u op het tabblad **Opties** de volgende acties uitvoeren:  

-   De stap uitschakelen.  

-   Opgeven of de takenreeks verder wordt uitgevoerd als er een fout optreedt tijdens het uitvoeren van de stap.  

-   Voorwaarden opgeven waaraan moet worden voldaan om de stap uit te voeren.  

 **Naam**  
 Hiermee geeft u een korte, door de gebruiker gedefinieerde naam op die de uitgevoerde opdrachtregel beschrijft.  

 **Beschrijving**  
 Hiermee geeft u meer gedetailleerde informatie op over de uitgevoerde opdrachtregel.  

 **Vanaf de opdrachtregel**  
 Hiermee geeft u de uitgevoerde opdrachtregel op. Dit veld is vereist. Inclusief bestandsnaamextensies wordt aanbevolen, bijvoorbeeld .vbs en .exe. Neem alle vereiste instellingenbestanden, opdrachtregelopties of schakelopties op.  

 Als de bestandsnaam geen een bestandsnaamextensie is opgegeven, Configuration Manager probeert .com, .exe en. bat. Als de bestandsnaam een extensie is niet een uitvoerbaar bestand heeft, Configuration Manager wordt geprobeerd een lokale koppeling toe te passen. Als de opdrachtregel readme.gif is, begint Configuration Manager de toepassing die is opgegeven op de doelcomputer voor het openen van .gif-bestanden.  

 Voorbeelden:  

 **Setup.exe /a**  

 **cmd.exe /c kopiëren Jan98.dat c:\sales\Jan98.dat**  

> [!NOTE]  
>  Opdrachtregelacties, zoals uitvoeromleiding, pipes of copy, zoals in het voorgaande voorbeeld moeten worden voorafgegaan door de **cmd.exe /c** opdracht uit om te worden uitgevoerd.  

 **64-bits bestandssysteemomleiding uitschakelen**  
 In een 64-bits besturingssysteem wordt het uitvoerbare bestand op de opdrachtregel standaard gezocht en uitgevoerd met behulp van de WOW64-bestandssysteemredirector, zodat 32-bits versies van uitvoerbare en .dll-bestanden van het besturingssysteem worden gevonden.  Als u deze optie selecteert, wordt het gebruik van de WOW64-bestandssysteemredirector uitgeschakeld, zodat de systeemeigen 64-bits versies van uitvoerbare en .dll-bestanden van het besturingssysteem kunnen worden gevonden.  Het selecteren van deze optie heeft geen effect wanneer u gebruikmaakt van een 32-bits besturingssysteem.  

 **Beginnen in**  
 Hiermee geeft u de uitvoerbare map op voor het programma, in maximaal 127 tekens. Deze map kan een absoluut pad op de doelcomputer betreffen of een relatief pad ten opzichte van de distributiepuntmap die het pakket bevat. Dit veld is optioneel.  

 Voorbeelden:  

 **c:\OfficeXP**  

 **i386**  

> [!NOTE]  
>  Met de knop **Bladeren** wordt op de lokale computer gezocht naar bestanden en mappen, zodat alles wat u op deze manier selecteert ook aanwezig moet zijn op de doelcomputer in dezelfde locatie en met dezelfde bestands- en mapnamen.  

 **Pakket**  
 Wanneer u bestanden of programma's op de opdrachtregel die nog niet aanwezig op de doelcomputer opgeeft, selecteert u deze optie om op te geven van de Configuration Manager-pakket dat de betreffende bestanden bevat. Voor het pakket is geen programma vereist. Deze optie is niet vereist als de opgegeven bestanden op de doelcomputer bestaan.  

 **Time-out**  
 Hiermee geeft u een waarde die hoe lang Configuration Manager aangeeft kan de opdrachtregel om uit te voeren. Deze waarde kan zijn van 1 minuut en 999 minuten liggen. De standaardwaarde is 15 minuten.  

 Deze optie is standaard uitgeschakeld.  

> [!IMPORTANT]  
>  Als u een waarde opgeeft die onvoldoende tijd biedt om de takenreeksstap Opdrachtregel uitvoeren te voltooien, mislukt de takenreeksstap en kan de gehele takenreeks mislukken afhankelijk van andere beheerinstellingen. Als de time-out is verlopen, beëindigt Configuration Manager het opdrachtregelproces.  

 **Deze stap uitvoeren als de volgende account**  
 Hiermee geeft u aan dat de opdrachtregel als een ander Windows-gebruikersaccount dan het lokale systeemaccount wordt uitgevoerd.  

> [!NOTE]  
>  Wanneer u een ander account voor deze stap opgeeft en deze stap plaatsvindt na een installatiestap van het besturingssysteem, moet het account worden toegevoegd aan de computer voordat u eenvoudige scripts of opdrachten kunt uitvoeren. Ook moet het profiel voor het Windows-gebruikersaccount worden hersteld voor het uitvoeren van complexere programma's, zoals een MSI.  

 **Account**  
 Hiermee geeft u het Windows-gebruikersaccount voor Uitvoeren als op voor de opdrachtregeltaak in de takenreeks die wordt uitgevoerd door deze actie. De opdrachtregel wordt uitgevoerd met de machtigingen van het opgegeven account. Klik op **Instellen** om het lokale gebruikersaccount of het domeinaccount op te geven.  

> [!IMPORTANT]  
>  Als de takenreeksactie **Opdrachtregel uitvoeren** met een gebruikersaccount wordt uitgevoerd in Windows PE, mislukt de actie omdat Windows PE niet lid kan zijn van een domein. De fout wordt geregistreerd in het bestand smsts.log.  

##  <a name="BKMK_RunPowerShellScript"></a>PowerShell-Script uitvoeren  
 Gebruik de takenreeksstap **PowerShell-Script uitvoeren** om een opgegeven PowerShell-script uit te voeren.  

 Deze stap kan in een standaardbesturingssysteem of in Windows PE worden uitgevoerd. Als u deze stap wilt uitvoeren in Windows PE, moet PowerShell zijn ingeschakeld in de opstartinstallatiekopie. U kunt Windows PowerShell (WinPE-PowerShell) inschakelen via het tabblad **Optionele onderdelen** in de eigenschappen van de opstartinstallatiekopie. Zie voor meer informatie over het wijzigen van een opstartinstallatiekopie [opstartinstallatiekopieën beheren](../get-started/manage-boot-images.md).  

> [!NOTE]  
>  PowerShell is standaard niet ingeschakeld op Windows Embedded-besturingssystemen.  

### <a name="details"></a>Details  
 Op het tabblad **Eigenschappen** voor deze stap kunt u de instellingen configureren die in deze sectie worden beschreven.  

 Bovendien kunt u op het tabblad **Opties** de volgende acties uitvoeren:  

-   De stap uitschakelen.  

-   Opgeven of de takenreeks verder wordt uitgevoerd als er een fout optreedt tijdens het uitvoeren van de stap.  

-   Voorwaarden opgeven waaraan moet worden voldaan om de stap uit te voeren.  

 **Naam**  
 Hiermee geeft u een korte, door de gebruiker gedefinieerde naam op die de uitgevoerde opdrachtregel beschrijft.  

 **Beschrijving**  
 Hiermee geeft u meer gedetailleerde informatie op over de uitgevoerde opdrachtregel.  

 **Pakket**  
 De Configuration Manager-pakket met het PowerShell-script opgeven. Eén pakket kan meerdere PowerShell-scripts bevatten.  

 **Scriptnaam**  
 Hiermee geeft u de naam van het uit te voeren PowerShell-script op. Dit veld is vereist.  

 **Parameters**  
 Hiermee geeft u de parameters op die worden doorgegeven aan het Windows PowerShell-script. Configureer de parameters alsof u deze toevoegt aan het Windows PowerShell-script vanaf een opdrachtregel.  

> [!IMPORTANT]  
>  Geef parameters op die worden gebruikt door het script, niet voor de Windows PowerShell-opdrachtregel.  
>   
>  Het volgende voorbeeld bevat geldige parameters:  
>   
>  **-Mijnparameter1 Mijnwaarde1-Mijnparameter2 Mijnwaarde2**  
>   
>  Het volgende voorbeeld bevat ongeldige parameters. De vette items zijn Windows PowerShell-opdrachtregelparameters (-nologo en -executionpolicy unrestricted) en worden niet gebruikt door het script.  
>   
>  **-nologo-executionpolicy unrestricted-File Mijnscript.ps1-Mijnparameter1 Mijnwaarde1-Mijnparameter2 Mijnwaarde2**  

 **PowerShell-uitvoeringsbeleid**  
 Met selectie van het PowerShell-uitvoeringsbeleid kunt u bepalen welke Windows PowerShell-scripts (indien van toepassing) kunnen worden uitgevoerd op de computer. Kies een van de volgende uitvoeringsbeleidsregels:  

-   **Alles ondertekend**: Alleen scripts die zijn ondertekend door een vertrouwde uitgever kunnen worden uitgevoerd.  

-   **Niet-gedefinieerde**: Er is geen uitvoeringsbeleid gedefinieerd. .  

-   **Bypass**: Alle configuratiebestanden laden en alle scripts uitvoeren. Als u een niet-ondertekend script uitvoert dat van internet is gedownload, wordt u niet om toestemming gevraagd voordat het script wordt uitgevoerd.  

> [!IMPORTANT]  
>  PowerShell 1.0 biedt geen ondersteuning voor de uitvoeringsbeleidsregels Undefined en Bypass.  

##  <a name="child-task-sequence"></a>Takenreeks uitvoeren

U kunt een nieuwe takenreeksstap waarop een andere takenreeks wordt uitgevoerd vanaf Configuration Manager versie 1710 kunt toevoegen. Hiermee maakt u een bovenliggende / onderliggende relatie tussen de takenreeksen. U kunt met een takenreeks onderliggende modulaire, herbruikbare takenreeksen maken.

Overweeg het volgende wanneer u een takenreeks onderliggende aan een takenreeks toevoegt:

 - De bovenliggende en onderliggende takenreeksen effectief gecombineerd tot een enkele beleidsregel die de client wordt uitgevoerd.
 - De omgeving is algemeen. Bijvoorbeeld, als een variabele is ingesteld door de takenreeks voor de bovenliggende en vervolgens worden gewijzigd door de onderliggende takenreeks wordt uitgevoerd, de variabele blijft gewijzigd zwevend doorsturen. Op dezelfde manier als de onderliggende takenreeks maakt u een nieuwe variabele, is de variabele beschikbaar voor de overige stappen in de takenreeks bovenliggende.
 - Statusberichten worden voor een enkele takenreeksbewerking per normaal verzonden.
 - De takenreeksen vermeldingen schrijven naar het bestand smsts.log met nieuwe logboekbestanden vermeldingen die duidelijk wanneer een onderliggende takenreeks wordt gestart.

### <a name="details"></a>Details

1. Klik in de takenreekseditor op **toevoegen**, selecteer **algemene**, en klik op **Takenreeks uitvoeren**.
2. Klik op **Bladeren** naar de onderliggende takenreeks selecteren.  

##  <a name="BKMK_SetDynamicVariables"></a>Dynamische variabelen instellen  
 Gebruik de takenreeksstap **Dynamische variabelen instellen** om de volgende handelingen uit te voeren:  

1.  Informatie verzamelen van de computer en de omgeving waarin de computer zich bevindt en vervolgens opgegeven takenreeksvariabelen instellen met de informatie.  

2.  Gedefinieerde regels evalueren en takenreeksvariabelen instellen op basis van de variabelen en waarden die zijn geconfigureerd voor regels die in waar resulteren.  

 De taakvolgorde stelt automatisch de volgende alleen-lezen takenreeksvariabelen in:  

 -   &#95; SMSTSMake  

 -   &#95; SMSTSModel  

 -   &#95; SMSTSMacAddresses  

 -   &#95; SMSTSIPAddresses  

 -   &#95; SMSTSSerialNumber  

 -   &#95; SMSTSAssetTag  

 -   &#95; SMSTSUUID  

 Deze stap kan in een standaardbesturingssysteem of in Windows PE worden uitgevoerd. Zie voor meer informatie over takenreeksvariabelen [Takenreeksacties](task-sequence-action-variables.md).  

### <a name="details"></a>Details  
 Op het tabblad **Eigenschappen** voor deze stap kunt u de instellingen configureren die in deze sectie worden beschreven.  

 Bovendien kunt u op het tabblad **Opties** de volgende acties uitvoeren:  

-   De stap uitschakelen.  

-   Opgeven of de takenreeks verder wordt uitgevoerd als er een fout optreedt tijdens het uitvoeren van de stap.  

-   Voorwaarden opgeven waaraan moet worden voldaan om de stap uit te voeren.  

**Naam**  
 Een korte, door de gebruiker gedefinieerde naam voor deze takenreeksstap.  

**Beschrijving**  
 Meer gedetailleerde informatie over de uitgevoerde actie in deze stap.  

**Dynamische regels en variabelen**  
 Voor het instellen van een dynamische variabele voor gebruik in de takenreeks kunt u een regel toevoegen en vervolgens een waarde opgeven voor elke variabele die u voor de regel opgeeft, of kunt u een of meer in te stellen variabelen toevoegen zonder een regel toe te voegen. Wanneer u een regel toevoegt, kunt u kiezen uit de volgende regelcategorieën:  

 -   **Computer**: Gebruik deze regelcategorie om waarden voor inventaristag, UUID, serienummer of mac-adres te beoordelen. U kunt meerdere waarden instellen en als een willekeurige waarde waar is, resulteert de regel in waar. Bijvoorbeeld: de volgende regel resulteert in waar als het serienummer 5892087 is, ongeacht of het MAC-adres gelijk is aan 26-78-13-5A-A4-22.  

     `IF Serial Number = 5892087 OR MAC address = 26-78-13-5A-A4-22 THEN`  

-   **Locatie**: Gebruik deze regelcategorie om waarden voor de standaardgateway te beoordelen.  

-   **Merk en Model**: Gebruik deze regelcategorie om waarden voor het merk en model van een computer te beoordelen. Zowel het merk als het model moet resulteren in waar om de regel te laten resulteren in waar.   

    U start in Configuration Manager versie 1610, kunt u een sterretje (*) en vraagtekens (**?**) als jokertekens, waarbij *** komt overeen met meerdere tekens en **?** komt overeen met een enkel teken. Bijvoorbeeld: de tekenreeks ' DELL * 900? ' komt overeen met ABC-DELL-9001 als DELL9009.

-   **Takenreeksvariabele**: Gebruik deze regelcategorie om toe te voegen een takenreeksvariabele, voorwaarde en waarde om te evalueren. Deze regel resulteert in waar wanneer de ingestelde waarde voor de variabele voldoet aan de opgegeven voorwaarde.  

U kunt een of meer variabelen opgeven die worden ingesteld voor een regel die resulteert in waar, of u kunt variabelen instellen zonder een regel te gebruiken. U kunt kiezen uit bestaande variabelen of u kunt een aangepaste variabele maken.  

 -   **Bestaande takenreeksvariabelen**: Gebruik deze instelling om te selecteren van een of meer variabelen in een lijst met bestaande takenreeksvariabelen. Matrixvariabelen kunnen niet worden geselecteerd.  

 -   **Aangepaste takenreeksvariabelen**: Gebruik deze instelling kunt u een aangepaste takenreeksvariabele te definiëren. U kunt ook een bestaande takenreeksvariabele opgeven. Dit is handig om een bestaande variabelenmatrix op te geven, zoals OSDAdapter, omdat variabelenmatrices niet voorkomen in de lijst met bestaande takenreeksvariabelen.  

Nadat u de variabelen voor een regel hebt geselecteerd, moet u een waarde opgeven voor elke variabele. De variabele wordt ingesteld op de opgegeven waarde wanneer de regel resulteert in waar. Voor elke variabele kunt u **Geheime waarde** selecteren om de waarde van de variabele te verbergen. Standaard worden de waarden van bepaalde bestaande variabelen verborgen, zoals de takenreeksvariabele OSDCaptureAccountPassword.  

> [!IMPORTANT]  
>  Wanneer u een takenreeks importeert met de stap Dynamische variabelen instellen terwijl **Geheime waarde** is geselecteerd voor de waarde van de variabele, wordt de waarde verwijderd wanneer u de takenreeks importeert. Daardoor moet u de waarde voor de dynamische variabele opnieuw invoeren nadat u de takenreeks hebt geïmporteerd.  

##  <a name="BKMK_SetTaskSequenceVariable"></a>Takenreeksvariabele instellen  
Gebruik de takenreeksstap **Takenreeksvariabele instellen** om de waarde in te stellen van een variabele die in de takenreeks wordt gebruikt.  

Deze stap kan in een standaardbesturingssysteem of in Windows PE worden uitgevoerd. Takenreeksvariabelen worden gelezen door takenreeksacties en bepalen het gedrag van deze acties. Zie voor meer informatie over specifieke takenreeksvariabelen [Takenreeksacties](task-sequence-action-variables.md).  

### <a name="details"></a>Details  
 Op het tabblad **Eigenschappen** voor deze stap kunt u de instellingen configureren die in deze sectie worden beschreven.  

 Bovendien kunt u op het tabblad **Opties** de volgende acties uitvoeren:  

-   De stap uitschakelen.  

-   Opgeven of de takenreeks verder wordt uitgevoerd als er een fout optreedt tijdens het uitvoeren van de stap.  

-   Voorwaarden opgeven waaraan moet worden voldaan om de stap uit te voeren.  

 **Naam**  
 Een korte, door de gebruiker gedefinieerde naam voor deze takenreeksstap.  

 **Beschrijving**  
 Meer gedetailleerde informatie over de uitgevoerde actie in deze stap.  

 **Takenreeksvariabele**  
 Een door de gebruiker gedefinieerde naam voor de takenreeksvariabele.  

 **Waarde**  
 De waarde die is gekoppeld aan de takenreeksvariabele. De waarde kan een andere takenreeksvariabele zijn met de syntaxis %<varname\>%.  

## <a name="hide-task-sequence-progress"></a>Voortgang van de takenreeks verbergen
<!-- 1354291 -->
U kunt bepalen wanneer voortgang van de takenreeks wordt weergegeven aan eindgebruikers met behulp van een nieuwe variabele met de release 1706. Gebruik in uw takenreeks de **Takenreeksvariabele instellen** stap voor het instellen van de waarde voor de **TSDisableProgressUI** variabele voortgang van de takenreeks weergeven of verbergen. U kunt de stap Takenreeksvariabele instellen meerdere keren in een takenreeks om de waarde voor de variabele te wijzigen. Hiermee kunt u de voortgang van de takenreeks in verschillende secties van de takenreeks weergeven of verbergen.

 - **Voortgang van de takenreeks verbergen**  
In de editor voor takenreeksen, gebruikt u de [Takenreeksvariabele instellen](#BKMK_SetTaskSequenceVariable) stap voor het instellen van de waarde van de **TSDisableProgressUI** variabele **True** voor het verbergen van de voortgang van de takenreeks.

 - **Voortgang van de takenreeks weergeven**  
In de editor voor takenreeksen, gebruikt u de [Takenreeksvariabele instellen](#BKMK_SetTaskSequenceVariable) stap voor het instellen van de waarde van de **TSDisableProgressUI** variabele **False** om weer te geven van de voortgang van de takenreeks.

##  <a name="BKMK_SetupWindowsandConfigMgr"></a>Windows en ConfigMgr installeren  
 Gebruik de takenreeksstap **Windows en ConfigMgr installeren** om de overgang van Windows PE naar het nieuwe besturingssysteem uit te voeren. Deze takenreeksstap is een vereist onderdeel van iedere besturingssysteemimplementatie. Deze Configuration Manager-client installeert in het nieuwe besturingssysteem en bereidt de takenreeks op uitvoering in het nieuwe besturingssysteem.  

 Deze stap kan alleen in Windows PE worden uitgevoerd. De taak kan niet worden uitgevoerd in een standaardbesturingssysteem. Zie voor meer informatie over takenreeksvariabelen voor deze takenreeksactie [Windows en ConfigMgr installeren takenreeksacties](task-sequence-action-variables.md#BKMK_SetupWindows).  

 De **Windows en ConfigMgr installeren** takenreeksactie sysprep.inf of unattend.xml directory variabelen, zoals % WINDIR % en % ProgramFiles %, vervangt door de Windows PE-installatiemap X:\Windows. Opgegeven takenreeksvariabelen met behulp van deze omgevingsvariabelen worden genegeerd.  

 Gebruik deze takenreeksstap om de volgende handelingen uit te voeren:  

1.  Voorbereidingen: Windows PE  

    1.  Voert takenreeksvariabelen in het bestand unattend.xml uit.  

    2.  Downloadt het pakket met de Configuration Manager-client en plaatst het in de geïmplementeerde installatiekopie.  

2.  Windows installeren  

    1.  Installatie op basis van een installatiekopie.  

        1.  Hiermee schakelt u de Configuration Manager-client in de installatiekopie (dat wil zeggen, wordt uitgeschakeld Autostart voor de Configuration Manager-client-service).  

        2.  Werkt het register in de geïmplementeerde installatiekopie bij zodat het geïmplementeerde besturingssysteem wordt gestart met dezelfde stationsletter als op de referentiecomputer.  

        3.  Start opnieuw op naar het geïmplementeerde besturingssysteem.  

        4.  Windows Mini-setup wordt uitgevoerd met behulp van het eerder opgegeven bestand sysprep.inf of unattend.xml, waarbij alle interactie door de eindgebruiker wordt onderdrukt. Opmerking: Als **netwerkinstellingen toepassen** opgegeven toevoegen aan een domein, bevindt die informatie zich in het bestand sysprep.inf of unattend.xml, en Windows Mini-Setup het domein.  

    2.  Installatie op basis van setup.exe.  Voert Setup.exe uit, die de standaard Windows-installatieprocedure volgt:  

        1.  Kopieert het installatiepakket voor het besturingssysteem dat is opgegeven in een eerdere takenreeks **Besturingssysteem toepassen** naar de harde schijf.  

        2.  Start opnieuw op naar het nieuw geïmplementeerde besturingssysteem.  

        3.  Windows Mini-setup wordt uitgevoerd met behulp van het eerder opgegeven bestand sysprep.inf of unattend.xml, waarbij alle gebruikersinterface-instellingen worden onderdrukt. Opmerking: Als **netwerkinstellingen toepassen** opgegeven toevoegen aan een domein, bevindt die informatie zich in het bestand sysprep.inf of unattend.xml, en Windows Mini-Setup het domein.  

3.  Instellen van de Configuration Manager-client  

    1.  Nadat Windows Mini-Setup is voltooid, wordt de takenreeks hervat met behulp van setupcomplete.cmd.  

    2.  Schakelt het lokale beheerdersaccount in of uit op basis van de geselecteerde optie in de stap **Windows-instellingen toepassen**.  

    3.  Configuration Manager-client installeert met behulp van het eerder gedownloade pakket (1.b) en installatie-eigenschappen die zijn opgegeven in de Takenreekseditor. De client is geïnstalleerd in 'inrichtingsmodus' om te voorkomen dat nieuwe beleidsaanvragen worden verwerkt totdat de takenreeks is voltooid.  

    4.  Wacht tot de client volledig operationeel is.  

    5.  Als de computer wordt uitgevoerd in een omgeving waarin Network Access Protection is ingeschakeld, controleert de client op vereiste updates en installeert de client deze, zodat alle vereiste updates aanwezig zijn voordat de uitvoering van de takenreeks wordt hervat.  

4.  De takenreeks wordt verder verwerkt bij de volgende stap.  

> [!NOTE]  
>  De takenreeksactie **Windows en ConfigMgr installeren** is verantwoordelijk voor het uitvoeren van Groepsbeleid op de nieuw geïnstalleerde computer. Het groepsbeleid wordt toegepast nadat de takenreeks is voltooid.  

### <a name="details"></a>Details  
 Op het tabblad **Eigenschappen** voor deze stap kunt u de instellingen configureren die in deze sectie worden beschreven.  

 Bovendien kunt u op het tabblad **Opties** de volgende acties uitvoeren:  

-   De stap uitschakelen.  

-   Selecteer deze optie niet als u wilt dat de takenreeks verder wordt uitgevoerd als er een fout optreedt tijdens het uitvoeren van de stap. Als er een fout optreedt, mislukt de takenreeks, ongeacht of u deze instelling selecteert.  

-   Voorwaarden opgeven waaraan moet worden voldaan om de stap uit te voeren.  

 **Naam**  
 Hiermee geeft u een korte, door de gebruiker gedefinieerde naam op die de uitgevoerde actie in deze stap beschrijft.  

 **Beschrijving**  
 Hiermee geeft u aanvullende informatie op over de uitgevoerde actie in deze stap.  

 **Clientpakket**  
 Hiermee geeft u de Configuration Manager-clientinstallatiepakket dat door deze takenreeksstap wordt gebruikt. Klik op **Bladeren** en selecteer het clientinstallatiepakket dat u wilt gebruiken om de Configuration Manager-client te installeren.  

 **Gebruik pre-productieclientpakket indien beschikbaar**  
 Hiermee wordt aangegeven dat als er een pre-productieclientpakket beschikbaar is, de takenreeksstap dit pakket gebruikt in plaats van het productieclientpakket. De pre-productieclient is meestal een nieuwere versie die wordt getest in de productieomgeving. Klik op **Bladeren** en selecteer het pre-productieclient-installatiepakket dat u wilt gebruiken om de Configuration Manager-client te installeren.  

 **Installatie-eigenschappen**  
 Sitetoewijzing en de standaardconfiguratie worden automatisch opgegeven door de takenreeksactie. U kunt dit veld gebruiken om eventuele aanvullende installatie-eigenschappen op te geven die worden gebruikt bij installatie van de client. Als u meerdere installatie-eigenschappen wilt invoeren, scheidt u deze met een spatie.  

 U kunt opdrachtregelopties opgeven voor gebruik tijdens de clientinstallatie. U kunt bijvoorbeeld **/skipprereq: silverlight.exe** invoeren om aan CCMSetup.exe te communiceren dat de Microsoft Silverlight-vereiste niet moet worden geïnstalleerd. Zie voor meer informatie over beschikbare opdrachtregelopties voor CCMSetup.exe [over clientinstallatie-eigenschappen](../../core/clients/deploy/about-client-installation-properties.md).  

##  <a name="BKMK_UpgradeOS"></a>Besturingssysteem bijwerken  
 Gebruik de takenreekstap **Besturingssysteem bijwerken** om een bestaand Windows 7-, Windows 8-, Windows 8.1- of Windows 10-besturingssysteem bij te werken naar Windows-10.  

 Deze takenreeksstap kan alleen in een standaardbesturingssysteem worden uitgevoerd. De stap kan niet worden uitgevoerd in Windows PE.  

### <a name="details"></a>Details  
 Op het tabblad **Eigenschappen** voor deze stap kunt u de instellingen configureren die in deze sectie worden beschreven.  

 Bovendien kunt u op het tabblad **Opties** de volgende acties uitvoeren:  

-   De stap uitschakelen.  

-   Opgeven of de takenreeks verder wordt uitgevoerd als er een fout optreedt tijdens het uitvoeren van de stap.  

-   Voorwaarden opgeven waaraan moet worden voldaan om de stap uit te voeren.  

 **Naam**  
 Een korte, door de gebruiker gedefinieerde naam opgeven die de uitgevoerde actie in deze stap beschrijft.  

 **Beschrijving**  
 Meer gedetailleerde informatie over de uitgevoerde actie in deze stap.  

 **Upgradepakket**  
 Selecteer deze optie om het Windows 10-upgradepakket op te geven dat moet worden gebruikt voor de upgrade.  

 **Bronpad**  
 Hiermee geeft u een lokaal pad of netwerkpad op naar het Windows-10-medium dat moet worden gebruikt (komt overeen met de opdrachtregeloptie /InstallFrom). U kunt ook een variabele opgeven, zoals %mycontentpath% of %DPC01%. Wanneer u een variabele voor het bronpad gebruikt, moet u deze eerder in de takenreeks opgeven. Als u bijvoorbeeld de stap [Pakketinhoud downloaden](#BKMK_DownloadPackageContent) in de takenreeks gebruikt, kunt u een variabele voor de locatie van het upgradepakket voor het besturingssysteem opgeven. Vervolgens gebruikt u deze variabele voor het bronpad voor deze stap.  

 **Editie**  
 Geef de editie in het besturingssysteemmedium op dat moet worden gebruikt voor de upgrade.  

 **Productcode**  
 Geef de productcode op om op het upgradeproces toe te passen  

 **Geef de volgende stuurprogramma-inhoud aan Windows Setup tijdens de upgrade**  
 Selecteer deze instelling om stuurprogramma's aan de doelcomputer toe te voegen tijdens het upgradeproces (komt overeen met de opdrachtregeloptie /InstallDriver). De stuurprogramma's moeten compatibel zijn met Windows 10. Geef een van de volgende mogelijkheden op:  

-   **Stuurprogrammapakket**: Klik op **Bladeren** en selecteer een bestaand stuurprogrammapakket in de lijst.  

-   **Tijdelijke inhoud**:  Selecteer deze optie om de locatie voor het stuurprogrammapakket te geven. U kunt een lokale map, netwerkpad of een takenreeksvariabele opgeven. Wanneer u een variabele voor het bronpad gebruikt, moet u deze eerder in de takenreeks opgeven. Bijvoorbeeld door de stap [Pakketinhoud downloaden](task-sequence-steps.md#BKMK_DownloadPackageContent) te gebruiken.  

 **Time-out (minuten)**  
 Hiermee geeft u het aantal minuten op dat Setup uit te voeren voordat Configuration Manager de takenreeksstap mislukt heeft.  

 **Windows-installatiecompatibiliteitsscan uitvoeren zonder de upgrade wordt gestart**  
 Hiermee geeft u aan dat de Windows-scan voor compatibiliteit moet worden uitgevoerd zonder het upgradeproces te starten (komt overeen met de opdrachtregeloptie /SCompat ScanOnly). Als u deze optie gebruikt, moet u nog steeds de gehele installatiebron implementeren. Setup retourneert een afsluitcode als resultaat van de scan. In de volgende tabel staan enkele veelvoorkomende afsluitcodes.  

|Afsluitcode|Details|  
|-|-|  
|MOSETUP_E_COMPAT_SCANONLY (0xC1900210)|Geen compatibiliteitsproblemen (gelukt).|  
|MOSETUP_E_COMPAT_INSTALLREQ_BLOCK (0xC1900208)|Compatibiliteitsproblemen waarop actie kan worden ondernomen.|  
|MOSETUP_E_COMPAT_MIGCHOICE_BLOCK (0xC1900204)|Geselecteerde migratiekeuze is niet beschikbaar. Bijvoorbeeld een upgrade van Enterprise naar Professional.|  
|MOSETUP_E_COMPAT_SYSREQ_BLOCK (0xC1900200)|Komt niet in aanmerking voor Windows 10.|  
|MOSETUP_E_COMPAT_INSTALLDISKSPACE_BLOCK (0xC190020E)|Onvoldoende vrije schijfruimte.|  

 Zie [Opdrachtregelopties voor Windows Setup](https://msdn.microsoft.com/library/windows/hardware/dn938368\(v=vs.85\).aspx) voor meer informatie over deze parameter  

 **Verwijder compatibiliteitsberichten die kunnen worden genegeerd**  
 Geeft aan dat de installatie is voltooid en negeert alle compatibiliteitsberichten die kunnen worden genegeerd (komt overeen met de opdrachtregeloptie /Compat IgnoreWarning).  

 **Installatie van Windows dynamisch bijwerken met Windows Update**  
 Geeft aan of Setup dynamische updatebewerkingen uitvoert, zoals zoeken, downloaden en installeren van updates (komt overeen met de opdrachtregeloptie /DynamicUpdate). Deze instelling is niet compatibel is met Configuration Manager software-updates, maar kan worden ingeschakeld wanneer u updates verwerkt met behulp van WSUS (zelfstandig) of Windows Update.  

 **Beleid negeren en standaard Microsoft Update gebruiken**: Selecteer deze instelling om het lokale beleid tijdelijk in negeren realtime dynamische updatebewerkingen uitvoert en de computer updates downloaden van Windows Update.  
