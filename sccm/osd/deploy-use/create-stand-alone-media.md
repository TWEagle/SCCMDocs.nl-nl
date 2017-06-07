---
title: Zelfstandige media maken met System Center Configuration Manager | Microsoft-documenten
description: Zelfstandige media gebruiken voor het implementeren van het besturingssysteem op een computer zonder een verbinding met een Configuration Manager-site of het netwerk.
ms.custom: na
ms.date: 03/24/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-osd
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: c6b9ccd2-78d9-4f0e-b25a-70d0866300ba
caps.latest.revision: 21
caps.handback.revision: 0
author: Dougeby
ms.author: dougeby
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: dab5da5a4b5dfb3606a8a6bd0c70a0b21923fff9
ms.openlocfilehash: d4689545ce2be5c16a65b24489f30028a0f90f94
ms.contentlocale: nl-nl
ms.lasthandoff: 05/17/2017


---
# <a name="create-stand-alone-media-with-system-center-configuration-manager"></a>Zelfstandige media maken met System Center Configuration Manager

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*

Zelfstandige media in Configuration Manager bevatten alles wat is vereist voor het implementeren van het besturingssysteem op een computer zonder een verbinding met een Configuration Manager-site of via het netwerk. Gebruik zelfstandige media met de volgende besturingssysteem implementatiescenario's beschreven:  

-   [Vernieuwen van een bestaande computer met een nieuwe versie van Windows](refresh-an-existing-computer-with-a-new-version-of-windows.md)  

-   [Een nieuwe versie van Windows installeren op een nieuwe computer (bare metal)](install-new-windows-version-new-computer-bare-metal.md)  

-   [Upgrade van Windows voor de nieuwste versie](upgrade-windows-to-the-latest-version.md)  

 Zelfstandige media bevat de takenreeks waarmee de stappen om het besturingssysteem en alle andere vereiste inhoud, met inbegrip van de opstartinstallatiekopie, de installatiekopie van besturingssysteem en de apparaatstuurprogramma's te installeren. Omdat alles wat nodig is voor het implementeren van het besturingssysteem op de zelfstandige media is opgeslagen, is de benodigde schijfruimte voor zelfstandige media aanzienlijk groter dan de benodigde schijfruimte voor andere mediatypen. Wanneer u op een centrale beheersite zelfstandige media maakt, haalt de client de toegewezen sitecode op uit Active Directory. Zelfstandige media die worden gemaakt op onderliggende sites, wijzen automatisch de sitecode van die site toe aan de client.  

##  <a name="BKMK_CreateStandAloneMedia"></a>Zelfstandige media maken  
 Voordat u zelfstandige media met behulp van de Wizard Takenreeks maken Media maakt, worden ervoor dat de volgende voorwaarden wordt voldaan:  

### <a name="create-a-task-sequence-to-deploy-an-operating-system"></a>Een takenreeks maken om een besturingssysteem te implementeren
Als onderdeel van de zelfstandige media moet u de takenreeks voor het implementeren van een besturingssysteem opgeven. Zie voor de stappen voor het maken van een nieuwe takenreeks [maken van een takenreeks voor het installeren van een besturingssysteem in System Center Configuration Manager](create-a-task-sequence-to-install-an-operating-system.md).

De volgende acties worden niet ondersteund voor zelfstandige media:
- De stap Stuurprogramma's automatisch toepassen in de takenreeks. Automatische toepassing van apparaatstuurprogramma's uit de stuurprogrammacatalogus wordt niet ondersteund, maar u kunt de stap Stuurprogramma's automatisch toepassen kiezen om een specifieke reeks stuurprogramma's beschikbaar te maken voor Windows Setup.
- Het downloaden van pakketinhoud stap in de takenreeks. De management-punt informatie is niet beschikbaar op zelfstandige media, daarom dat de stap mislukt bij het opsommen van de locatie van inhoud.
- Installatie van software-updates.
- Installatie van software voordat het besturingssysteem wordt geïmplementeerd.
- Takenreeksen voor implementaties van niet-besturingssystemen.
- Koppelen van gebruikers aan de doelcomputer ter ondersteuning van de gebruikersaffiniteit van apparaten.
- Dynamische pakket wordt geïnstalleerd via de taak Pakketten installeren.
- Dynamische toepassing wordt geïnstalleerd via de toepassing Taak installeren.

Als u uw takenreeks voor het implementeren van een besturingssysteem bevat de [pakket installeren](../../osd/understand/task-sequence-steps.md#BKMK_InstallPackage) stap en u de zelfstandige media maken op een centrale beheersite, een fout optreden. De centrale beheersite beschikt niet over de benodigde beleidsregels voor clientconfiguratie om de agent voor softwaredistributie in te schakelen tijdens het uitvoeren van de takenreeks. Mogelijk wordt de volgende fout in het bestand CreateTsMedia.log weergegeven:<br /><br /> "De WMI-methode SMS_TaskSequencePackage.GetClientConfigPolicies mislukt (0x80041001)"<br /><br /> Voor zelfstandige media met een **pakket installeren** stap, die u moet de zelfstandige media maken op een primaire site die de agent voor softwaredistributie is ingeschakeld of Voeg een [opdrachtregel uitvoeren](../understand/task-sequence-steps.md#BKMK_RunCommandLine) stap na de [Windows en ConfigMgr installeren](../understand/task-sequence-steps.md#BKMK_SetupWindowsandConfigMgr) stap en voor de eerste **pakket installeren** stap in de takenreeks. Met de stap **Opdrachtregel uitvoeren** wordt een WMIC-opdracht uitgevoerd waarmee de agent voor softwaredistributie wordt ingeschakeld voordat de eerste stap Pakket installeren wordt uitgevoerd. U kunt de volgende opdracht gebruiken in de takenreeksstap **Opdrachtregel uitvoeren** :<br /><br />
```
WMIC /namespace:\\\root\ccm\policy\machine\requestedconfig path ccm_SoftwareDistributionClientConfig CREATE ComponentName="Enable SWDist", Enabled="true", LockSettings="TRUE", PolicySource="local", PolicyVersion="1.0", SiteSettingsKey="1" /NOINTERACTIVE
```

### <a name="distribute-all-content-associated-with-the-task-sequence"></a>Alle aan de takenreeks gekoppeld inhoud distribueren
U moet alle inhoud die vereist is voor de takenreeks distribueren naar ten minste één distributiepunt. Dit omvat de opstartinstallatiekopie, de installatiekopie van het besturingssysteem en andere gekoppelde bestanden. De wizard haalt de informatie op van het distributiepunt wanneer het de zelfstandige media creëert. U moet over het toegangsrecht **Lezen** beschikken voor de inhoudsbibliotheek op het distributiepunt.  Zie [Inhoud distribueren waarnaar wordt verwezen door een specifieke takenreeks](manage-task-sequences-to-automate-tasks.md#BKMK_DistributeTS) voor meer informatie.

### <a name="prepare-the-removable-usb-drive"></a>Het verwisselbare USB-station voorbereiden
*Voor een verwisselbaar USB-station:*

Wanneer u een verwisselbaar USB-station wilt gebruiken, moet het USB-station zijn aangesloten op de computer waarop de wizard wordt uitgevoerd. Daarnaast moet het USB-station door Windows gedetecteerd kunnen worden als een verwisselbaar apparaat. De wizard schrijft rechtstreeks naar het USB-station wanneer deze het medium maakt. Zelfstandige media maakt gebruik van een FAT32-bestandssysteem. U kunt geen zelfstandige media maken op een USB-flashstation waarvan de inhoud een bestand bevat dat groter is dan 4 GB.

### <a name="create-an-output-folder"></a>Een uitvoermap maken
*Voor een CD/DVD-set:*

Voordat u de wizard Takenreeksmedia maken uitvoert voor het maken van media voor een cd- of dvd-set, moet u een map maken voor de uitvoerbestanden die door de wizard worden gemaakt. Media die worden gemaakt voor een cd- of dvdset worden als .iso-bestanden direct naar de map geschreven.


 Gebruik de volgende procedure om zelfstandige media te maken voor een USB-station of een cd/dvd-set.  

## <a name="to-create-stand-alone-media"></a>Zelfstandige media maken  

1.  Klik in de Configuration Manager-console op **Softwarebibliotheek**.  

2.  Vouw **Besturingssystemen** uit in de werkruimte **Softwarebibliotheek**en klik op **Takenreeksen**.  

3.  Klik op het tabblad **Start** in de groep **Maken** op **Takenreeksmedia maken** om de wizard Takenreeksmedia maken te starten.  

4.  Geef op de pagina **Mediatype selecteren** de volgende opties op en klik op **Volgende**.  

    -   Selecteer **Zelfstandige media**.  

    -   Selecteer optioneel, indien u wenst toe te staan dat het besturingssysteem geïmplementeerd wordt zonder invoer van de gebruiker, de optie **Implementatie van het besturingssysteem zonder toezicht toestaan**. Wanneer u deze optie selecteert, wordt de gebruiker niet gevraagd naar informatie over netwerkconfiguratie of naar optionele takenreeksen. De gebruiker wordt wel nog steeds gevraagd om een wachtwoord als de media hiervoor is geconfigureerd.  

5.  Geef op de pagina **Mediumtype** op of het medium een flashstation of een cd/dvd-set is en klik vervolgens om het volgende te configureren:  

    > [!IMPORTANT]  
    >  Zelfstandige media maakt gebruik van een FAT32-bestandssysteem. U kunt geen zelfstandige media maken op een USB-flashstation waarvan de inhoud een bestand bevat dat groter is dan 4 GB.  

    -   Als u **USB-flashstation**selecteert, moet u het station opgeven waarop u de inhoud wilt opslaan.  

    -   Indien u **cd-/dvdset selecteert**, geef dan de capaciteit van de media en de naam en het pad van de uitvoerbestanden op. De wizard schrijft de uitvoerbestanden naar deze locatie. Bijvoorbeeld:  **\\\servername\folder\outputfile.iso**  

         Als de capaciteit van de media te klein is om alle inhoud op te slaan, worden er meerdere bestanden gemaakt en moet u de inhoud op meerdere cd's of dvd's opslaan. Als meerdere media nodig zijn, voegt Configuration Manager een volgnummer toe aan de naam van ieder uitvoerbestand dat wordt gemaakt. Bovendien, als u een toepassing tezamen met het besturingssysteem implementeert en de toepassing is voor één media groot te, slaat Configuration Manager de toepassing over verschillende media. Als de zelfstandige media wordt uitgevoerd, wordt Configuration Manager de gebruiker voor de volgende media waar de toepassing wordt opgeslagen.   

         > [!IMPORTANT]  
         >  Als u een bestaande .iso-afbeelding selecteert, verwijdert de wizard voor het maken van takenreeksmedia die afbeelding uit het station of de share wanneer u doorgaat naar de volgende pagina van de wizard. De bestaande installatiekopie wordt gewist, zelfs als u de wizard annuleert.  

     Klik op **Volgende**.  

6.  Op de **beveiliging** pagina, kiezen uit de volgende instellingen en klik vervolgens op **volgende**:
    - **Media beveiligen met een wachtwoord**: Voer een sterk wachtwoord in om de media te beveiligen. Als u een wachtwoord opgeeft, is het wachtwoord vereist om de media te gebruiken.  

        > [!IMPORTANT]  
        >  Op zelfstandige media zijn enkel de takenreeksstappen en hun variabelen versleuteld. De rest van de inhoud van de media is niet versleuteld, neem dus geen gevoelige informatie op in takenreeksscripts. U kunt alle gevoelige informatie opslaan en implementeren met behulp van takenreeksvariabelen.  

    - **Selecteer het datumbereik voor deze zelfstandige media geldig** (te beginnen in versie 1702): Optionele begin- en verloopdatum datums instellen op de media. Deze instellingen zijn standaard uitgeschakeld. De datums worden vergeleken met de systeemtijd op de computer voordat de zelfstandige media wordt uitgevoerd. Wanneer de systeemtijd ouder is dan de begintijd of hoger is dan de verlooptijd is, wordt de zelfstandige media niet gestart. Deze opties zijn ook beschikbaar via de cmdlet New-CMStandaloneMedia PowerShell.
7.  Op de **zelfstandige CD/DVD** pagina, de takenreeks opgeven die het besturingssysteem implementeert en klik vervolgens op **volgende**. Kies **toepassingsafhankelijkheden detecteren en toevoegen aan deze media** inhoud toevoegen aan de zelfstandige media voor toepassingsafhankelijkheden.
    > [!TIP]
    > Als er geen verwachte toepassingsafhankelijkheden, hef de selectie en selecteert u vervolgens opnieuw de **toepassingsafhankelijkheden detecteren en toevoegen aan deze media** instelling om de lijst te vernieuwen.

    In de wizard kunt u alleen de takenreeksen selecteren die zijn gekoppeld aan een opstartinstallatiekopie.  

8. Op de **toepassing selecteren** pagina (beschikbaar vanaf versie 1702), geef de toepassingsinhoud opgeven voor opname als onderdeel van het mediabestand en klikken op **volgende**.
9. Op de **pakket selecteren** pagina (beschikbaar vanaf versie 1702), geef de inhoud van het pakket opgenomen als onderdeel van het mediabestand en klik vervolgens op **volgende**.
10. Op de **stuurprogrammapakket selecteren** pagina (beschikbaar vanaf versie 1702), geef de stuurprogramma-inhoud opgeven voor opname als onderdeel van het mediabestand en klik vervolgens op **volgende**.
11.  Op de **distributiepunten** pagina en klik vervolgens op de distributiepunten die de inhoud vereist is door de takenreeks opgeven **volgende**.  

     Configuration Manager alleen weergegeven distributiepunten die de inhoud. U moet alle inhoud die is gekoppeld aan de takenreeks (opstartinstallatiekopie, installatiekopie van het besturingssysteem, enzovoort) distribueren naar minimaal één distributiepunt voordat u verder kunt gaan. Nadat u de inhoud distribueert, u kunt de wizard opnieuw starten of distributiepunten die u al op deze pagina hebt geselecteerd gaat u naar de vorige pagina verwijderen, en vervolgens weer in de **distributiepunten** pagina vernieuwen van de lijst van distributiepunten. Voor meer informatie over het distribueren van inhoud raadpleegt u [Inhoud distribueren waarnaar wordt verwezen door een specifieke takenreeks](manage-task-sequences-to-automate-tasks.md#BKMK_DistributeTS). Zie voor meer informatie over distributiepunten en inhoudsbeheer [inhoud en -infrastructuur voor System Center Configuration Manager beheert](../../core/servers/deploy/configure/manage-content-and-content-infrastructure.md).  

    > [!NOTE]  
    >  U moet hebben **lezen** toegangsrechten voor de Inhoudsbibliotheek op de distributiepunten.  

12. Geef op de pagina **Aanpassing** de volgende informatie op en klik vervolgens op **Volgende**.  

    -   Geef de variabelen op die de takenreeks gebruikt voor het implementeren van het besturingssyteem.  

    -   Geef eventuele prestart-opdrachten die u wilt uitvoeren voordat de takenreeks wordt uitgevoerd. Prestart-opdrachten bestaan uit een script of een uitvoerbaar bestand dat kan communiceren met de gebruiker in Windows PE voordat de takenreeks wordt uitgevoerd om het besturingssysteem te installeren. Zie voor meer informatie over prestart-opdrachten voor media [Prestart-opdrachten voor takenreeksmedia in System Center Configuration Manager](../understand/prestart-commands-for-task-sequence-media.md).  

         Schakel optioneel **bestanden voor de prestart-opdracht** te nemen vereiste bestanden voor de prestart-opdracht.  

        > [!TIP]  
        >  Tijdens het maken van de media taak schrijft de takenreeks de pakket-ID en prestart-opdrachtregel, inclusief de waarde voor eventuele takenreeksvariabelen, naar het logboekbestand CreateTSMedia.log op de computer waarop de Configuration Manager-console. U kunt dit logboekbestand controleren om de waarde voor de takenreeksvariabelen te verifiëren.  

13. Voltooi de wizard.  

 De bestanden voor de zelfstandige media (.iso) worden in de doelmap gemaakt. Als u **Zelfstandige cd/dvd** hebt geselecteerd, kunt u de uitvoerbestanden nu kopiëren naar een set cd's of dvd's.  

##  <a name="BKMK_StandAloneMediaTSExample"></a>Voorbeeld van de takenreeks voor zelfstandige media  
 Gebruik de volgende tabel als richtlijn wanneer u een takenreeks voor het implementeren van een besturingssysteem met zelfstandige media maakt. De tabel helpt u om de algemene volgorde te bepalen voor de takenreeksstappen en deze in te delen en te structureren in logische groepen. De takenreeks die u maakt, kan afwijken van dit voorbeeld en kan meer of minder takenreeksstappen en groepen bevatten.  

> [!NOTE]  
>  U moet altijd de Wizard Takenreeksmedia maken van zelfstandige media gebruiken.  

|Takenreeksgroep of -stap|Beschrijving|  
|---------------------------------|-----------------|  
|Vastleggen van bestanden en instellingen - **(nieuwe Takenreeksgroep)**|Een takenreeksgroep maken. In een takenreeksgroep houdt u vergelijkbare takenreeksstappen bij elkaar voor betere ordening en foutcontrole.|  
|Windows-instellingen vastleggen|Gebruik deze takenreeksstap om de Microsoft Windows-instellingen te identificeren die zijn vastgelegd van het bestaande besturingssysteem op de doelcomputer voordat de installatiekopie werd teruggezet. U kunt de computernaam, gebruikers- en organisatiegegevens en de instellingen voor de tijdzone vastleggen.|  
|Netwerkinstellingen vastleggen|Gebruik deze takenreeksstap om de netwerkinstellingen vast te leggen van de computer die de takenreeks ontvangt. U kunt naast de netwerkadapterinstellingen het lidmaatschap van de computer van een domein of werkgroep vastleggen.|  
|Vastleggen van gebruikersbestanden en -instellingen - **(nieuwe submap Takenreeksgroep)**|Maak een takenreeksgroep binnen een takenreeksgroep. Deze subgroep bevat de stappen die nodig zijn voor het vastleggen van de gegevens van de gebruikersstatus van het bestaande besturingssysteem op de doelcomputer voordat de installatiekopie werd teruggezet. Deze subgroep houdt op een soortgelijke manier als de eerste groep die u hebt toegevoegd, vergelijkbare takenreeksstappen bij elkaar voor een betere ordening en foutcontrole.|  
|Locatie van lokale status instellen|Gebruik deze takenreeksstap om een lokale locatie met de takenreeksvariabele voor een beveiligd pad op te geven. De gebruikersstatus wordt opgeslagen in een beveiligde map op de harde schijf.|  
|Gebruikersstatus vastleggen|Gebruik deze takenreeksstap om de gebruikersbestanden en -instellingen vast te leggen die u wilt migreren naar het nieuwe besturingssysteem.|  
|Installatie van besturingssysteem - **(nieuwe Takenreeksgroep)**|Maak een nieuwe takenreekssubgroep. Deze subgroep bevat de stappen die nodig zijn om het besturingssysteem te installeren.|  
|Opnieuw opstarten in Windows PE of harde schijf|In deze takenreeksstap geeft u de opties op voor het opnieuw opstarten van de doelcomputer die deze takenreeks ontvangt. Bij deze stap wordt een bericht voor de gebruiker weergegeven dat de computer opnieuw wordt opgestart zodat de installatie kan doorgaan.<br /><br /> Deze stap maakt gebruik van de alleen-lezen takenreeksvariabele **_SMSTSInWinPE** . Als de gekoppelde waarde gelijk is aan **false** , wordt de takenreeksstap voortgezet.|  
|Besturingssysteem toepassen|Met deze takenreeksstap installeert u de installatiekopie van het besturingssysteem op de doelcomputer. Deze stap verwijdert alle bestanden op het desbetreffende volume (met uitzondering van de Configuration Manager-besturingselement bestanden) en vervolgens alle volume afbeeldingen in het WIM-bestand naar het overeenkomstige sequentiële schijfvolume worden toegepast. U kunt ook een **sysprep**-antwoordbestand opgeven om te configureren welke schijfpartitie voor de installatie moet worden gebruikt.|  
|Windows-instellingen toepassen|Met deze takenreeksstap configureert u de configuratiegegevens voor de Windows-instellingen voor de doelcomputer. De Windows-instellingen die u kunt toepassen zijn gebruikers- en organisatiegegevens, product- of licentiecodegegevens, de tijdzone en het wachtwoord voor de lokale beheerder.|  
|Netwerkinstellingen toepassen|Met deze takenreeks geeft u de gegevens voor netwerk- of werkgroepconfiguratie op voor de doelcomputer. U kunt ook opgeven of de computer een DHCP-server gebruikt of u kunt de IP-adresgegevens statisch toewijzen.|  
|Stuurprogrammapakket toepassen|Gebruik deze takenreeksstap om alle apparaatstuurprogramma's in een stuurprogrammapakket beschikbaar te maken voor gebruik door Windows Setup. Alle benodigde apparaatstuurprogramma's moeten zijn opgenomen op de zelfstandige media.|  
|Besturingssysteem - Setup **(nieuwe Takenreeksgroep)**|Maak een nieuwe takenreekssubgroep. Deze subgroep bevat de stappen die nodig zijn om de Configuration Manager-client te installeren.|  
|Windows en ConfigMgr installeren|Gebruik deze takenreeksstap om de Configuration Manager-clientsoftware te installeren. Configuration Manager installeert en registreert de GUID van de Configuration Manager-client. U kunt de vereiste installatieparameters toewijzen in het venster **Installatie-eigenschappen** .|  
|Herstellen van gebruikersbestanden en -instellingen - **(nieuwe Takenreeksgroep)**|Maak een nieuwe takenreekssubgroep. Deze subgroep bevat de stappen die nodig zijn om de gebruikersstatus te herstellen.|  
|Gebruikersstatus herstellen|Gebruik deze takenreeksstap om het Hulpprogramma voor migratie van gebruikersstatus (USMT) te starten en de gebruikersstatus en -instellingen te herstellen die met de actie Gebruikerstoestand vastleggen zijn vastgelegd op de doelcomputer.|  
