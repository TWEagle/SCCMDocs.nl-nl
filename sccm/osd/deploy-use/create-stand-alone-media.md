---
title: Zelfstandige media maken
titleSuffix: Configuration Manager
description: Zelfstandige media gebruiken om het besturingssysteem op een computer zonder een netwerkverbinding te implementeren.
ms.custom: na
ms.date: 02/09/2018
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-osd
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: c6b9ccd2-78d9-4f0e-b25a-70d0866300ba
caps.latest.revision: 
caps.handback.revision: 
author: aczechowski
ms.author: aaroncz
manager: dougeby
ms.openlocfilehash: 587804b026f01f25754a10f35967d18d0b8d471d
ms.sourcegitcommit: fbde417e3c3002898bd216a7e110e725ae269893
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 02/12/2018
---
# <a name="create-stand-alone-media-with-system-center-configuration-manager"></a>Zelfstandige media maken met System Center Configuration Manager

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*

Zelfstandige media in Configuration Manager bevat alles wat u nodig voor het implementeren van het besturingssysteem (OS) op een computer zonder een netwerkverbinding. Gebruik zelfstandige media met de volgende OS implementatiescenario's:  

-   [Een bestaande computer vernieuwen met een nieuwe versie van Windows](refresh-an-existing-computer-with-a-new-version-of-windows.md)  

-   [Een nieuwe versie van Windows op een nieuwe computer (bare-metal) installeren](install-new-windows-version-new-computer-bare-metal.md)  

-   [Windows bijwerken naar de laatste versie](upgrade-windows-to-the-latest-version.md)  

Zelfstandige media bevatten de takenreeks die de stappen voor het installeren van het besturingssysteem en alle andere vereiste inhoud worden geautomatiseerd. Deze inhoud omvat de opstartinstallatiekopie, de installatiekopie van besturingssysteem en de apparaatstuurprogramma's. Omdat de zelfstandige media alles opgeslagen voor het implementeren van het besturingssysteem, vereist meer schijfruimte dan nodig is voor andere typen media. Wanneer u zelfstandige media op een centrale beheersite maakt, wordt de client de toegewezen sitecode opgehaald uit Active Directory. Zelfstandige media automatisch gemaakt op onderliggende sites wordt toegewezen aan de client de sitecode voor die site.  

##  <a name="BKMK_CreateStandAloneMedia"></a>Zelfstandige media maken  
Voordat u zelfstandige media met behulp van de Wizard Takenreeks maken Media maakt, moet dat de volgende voorwaarden wordt voldaan:  

### <a name="create-a-task-sequence-to-deploy-an-operating-system"></a>Een takenreeks maken om een besturingssysteem te implementeren
Als onderdeel van de zelfstandige media moet u de takenreeks voor het implementeren van een besturingssysteem opgeven. Zie voor de stappen voor het maken van een nieuwe takenreeks [een takenreeks maken voor het installeren van een besturingssysteem in System Center Configuration Manager](create-a-task-sequence-to-install-an-operating-system.md).

De volgende acties worden niet ondersteund voor zelfstandige media:
- De **stuurprogramma's automatisch toepassen** stap in de takenreeks wordt uitgevoerd. Zelfstandige media biedt geen ondersteuning voor automatische toepassing van apparaatstuurprogramma's uit de stuurprogrammacatalogus. Gebruik de **stuurprogrammapakket toepassen** stap naar een opgegeven set met stuurprogramma's beschikbaar te maken voor Windows Setup.
- De **pakketinhoud downloaden** stap in de takenreeks wordt uitgevoerd. De gegevens van het herstelpunt is niet beschikbaar op zelfstandige media, dus de stap mislukt bij het opsommen van de locaties van inhoud.
- Installatie van software-updates.
- Installatie van software voordat u het besturingssysteem implementeert.
- Takenreeksen die gebruikmaken van niet - besturingssysteemimplementaties.
- Koppelen van gebruikers aan de doelcomputer ter ondersteuning van de gebruikersaffiniteit van apparaten.
- Dynamische pakket wordt geïnstalleerd via de **pakketten installeren** taak.
- Dynamische toepassing wordt geïnstalleerd via de **toepassing installeren** taak.

> [!NOTE]    
> Kan een fout optreden als de takenreeks bevat de [pakket installeren](../../osd/understand/task-sequence-steps.md#BKMK_InstallPackage) stap en u de zelfstandige media maken op een centrale beheersite. De centrale beheersite beschikt niet over de benodigde beleidsregels voor clientconfiguratie. Deze beleidsregels zijn vereist voor het inschakelen van de agent voor softwaredistributie tijdens het uitvoeren van de takenreeks wordt uitgevoerd. Mogelijk wordt de volgende fout in het bestand CreateTsMedia.log weergegeven:    
>     
> `WMI method SMS_TaskSequencePackage.GetClientConfigPolicies failed (0x80041001)`    
> 
> Voor zelfstandige media met een **pakket installeren** stap, de zelfstandige media maken op een primaire site die de agent voor softwaredistributie is ingeschakeld. 
>
> U kunt ook toevoegen een [opdrachtregel uitvoeren](../understand/task-sequence-steps.md#BKMK_RunCommandLine) stap na de [Windows en ConfigMgr installeren](../understand/task-sequence-steps.md#BKMK_SetupWindowsandConfigMgr) stap en voor de eerste **pakket installeren** stap in de takenreeks wordt uitgevoerd. De **opdrachtregel uitvoeren** stap wordt uitgevoerd de volgende WMIC-opdracht voor het inschakelen van de agent voor softwaredistributie voordat de eerste stap pakket installeren:    
>    
> `WMIC /namespace:\\\root\ccm\policy\machine\requestedconfig path ccm_SoftwareDistributionClientConfig CREATE ComponentName="Enable SWDist", Enabled="true", LockSettings="TRUE", PolicySource="local", PolicyVersion="1.0", SiteSettingsKey="1" /NOINTERACTIVE`


> [!IMPORTANT]    
> Selecteer niet de **gebruik pre-productieclientpakket indien beschikbaar** instellen in de **Windows en ConfigMgr installeren** takenreeksstap voor zelfstandige media. Zelfstandige media biedt geen ondersteuning voor gebruik van deze instelling. Zie voor meer informatie over deze instelling [Windows en ConfigMgr installeren](/sccm/osd/understand/task-sequence-steps#BKMK_SetupWindowsandConfigMgr).


### <a name="distribute-all-content-associated-with-the-task-sequence"></a>Alle aan de takenreeks gekoppeld inhoud distribueren
Alle inhoud die is door de takenreeks naar ten minste één distributiepunt vereist distribueren. Deze inhoud omvat de opstartinstallatiekopie, de installatiekopie van het besturingssysteem en andere gekoppelde bestanden. De wizard haalt de informatie op van het distributiepunt wanneer het de zelfstandige media creëert. U moet over het toegangsrecht **Lezen** beschikken voor de inhoudsbibliotheek op het distributiepunt. Zie voor meer informatie [inhoud waarnaar wordt verwezen door de takenreeks distribueren](manage-task-sequences-to-automate-tasks.md#BKMK_DistributeTS).

### <a name="prepare-the-removable-usb-drive"></a>Het verwisselbare USB-station voorbereiden
*Voor een verwisselbaar USB-station:*

Als u van een USB-station gebruikmaakt, verbinding maken met het USB-station met de computer waarop de wizard wordt uitgevoerd. Het USB-station moet worden gedetecteerd door Windows als een verwisselbaar apparaat. De wizard schrijft rechtstreeks naar het USB-station wanneer deze het medium maakt. Zelfstandige media maakt gebruik van een FAT32-bestandssysteem. U kunt geen zelfstandige media maken op een USB-flashstation waarvan de inhoud een bestand bevat dat groter is dan 4 GB.

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

    -   Selecteer optioneel, indien u wenst toe te staan dat het besturingssysteem geïmplementeerd wordt zonder invoer van de gebruiker, de optie **Implementatie van het besturingssysteem zonder toezicht toestaan**. Wanneer u deze optie selecteert, wordt de gebruiker niet gevraagd naar informatie over netwerkconfiguratie of naar optionele takenreeksen. Als de media is geconfigureerd voor beveiliging met een wachtwoord, wordt de gebruiker nog steeds gevraagd om een wachtwoord.  

5.  Op de **mediatype** pagina, opgeven of de media een USB-station of een CD/DVD-set:  

    > [!IMPORTANT]  
    >  Zelfstandige media maakt standaard gebruik van een FAT32-bestandssysteem. U maken geen zelfstandige media op een verwisselbaar USB-station waarvan de inhoud een bestand meer dan 4 GB groot bevat.  

    -   Als u selecteert **verwisselbaar USB-station**, geef het station waar u wilt opslaan van de inhoud.  

        - **Formatteer verwisselbaar USB-station (FAT32) en opstartbaar**: Standaard kunt u Configuration Manager voorbereiden van het USB-station. Veel nieuwere UEFI-apparaten vereisen een opstartbare FAT32-partitie. Deze indeling beperkt echter ook de grootte van bestanden en de algehele capaciteit van het station. Als u hebt al geformatteerd en het verwisselbare-schijfstation geconfigureerd, moet u deze optie uitschakelen. 

    -   Indien u **cd-/dvdset selecteert**, geef dan de capaciteit van de media en de naam en het pad van de uitvoerbestanden op. De wizard schrijft de uitvoerbestanden naar deze locatie. Bijvoorbeeld:  **\\\servername\folder\outputfile.iso**  

         Als de capaciteit van de media te klein is om alle inhoud op te slaan, worden er meerdere bestanden gemaakt en moet u de inhoud op meerdere cd's of dvd's opslaan. Als meerdere media nodig zijn, wordt een volgnummer toegevoegd aan de naam van ieder uitvoerbestand dat wordt gemaakt van Configuration Manager. Bovendien, als u een toepassing tezamen met het besturingssysteem implementeert en de toepassing is te voor één media groot, slaat Configuration Manager de toepassing over verschillende media. Wanneer de zelfstandige media wordt uitgevoerd, wordt Configuration Manager de gebruiker naar de volgende media waar de toepassing wordt opgeslagen.   

         > [!IMPORTANT]  
         >  Als u een bestaande .iso-afbeelding selecteert, verwijdert de wizard voor het maken van takenreeksmedia die afbeelding uit het station of de share wanneer u doorgaat naar de volgende pagina van de wizard. De bestaande installatiekopie wordt gewist, zelfs als u de wizard annuleert.  

     Klik op **Volgende**.  

6.  Op de **beveiliging** pagina, kiezen uit de volgende instellingen en klik vervolgens op **volgende**:
    - **Media beveiligt met een wachtwoord**: Voer een sterk wachtwoord in om de media te beveiligen. Als u een wachtwoord opgeeft, is het wachtwoord vereist om de media te gebruiken.  

        > [!IMPORTANT]  
        >  Op zelfstandige media worden alleen de takenreeksstappen en hun variabelen versleuteld. De rest van de inhoud van de media is niet versleuteld, neem dus geen gevoelige informatie op in takenreeksscripts. U kunt alle gevoelige informatie opslaan en implementeren met behulp van takenreeksvariabelen.  

    - **Selecteer het datumbereik voor deze zelfstandige media geldig** (te beginnen in versie 1702): Optionele begin- en verloopdatum datums instellen op de media. Deze instellingen zijn standaard uitgeschakeld. De datums worden vergeleken met de systeemtijd op de computer voordat de zelfstandige media wordt uitgevoerd. Wanneer de systeemtijd ouder dan de begintijd of hoger is dan de verlooptijd is, worden de zelfstandige media is niet gestart. Deze opties zijn ook beschikbaar via de cmdlet New-CMStandaloneMedia PowerShell.
7.  Op de **zelfstandige CD/DVD** pagina, de takenreeks opgeven die het besturingssysteem implementeert en klik vervolgens op **volgende**. Om de inhoud toevoegen aan de zelfstandige media voor de afhankelijkheden voor toepassingen, kies **toepassingsafhankelijkheden detecteren en toevoegen aan deze media**.
    > [!TIP]
    > Als u verwachte toepassingsafhankelijkheden niet ziet, schakelt u en selecteert u vervolgens opnieuw de **toepassingsafhankelijkheden detecteren en toevoegen aan deze media** instelling om de lijst te vernieuwen.

    In de wizard kunt u alleen de takenreeksen selecteren die zijn gekoppeld aan een opstartinstallatiekopie.  

8. Op de **toepassing selecteren** pagina (beschikbaar vanaf versie 1702), geef toepassingsinhoud opnemen als onderdeel van het mediabestand en klik vervolgens op **volgende**.
9. Op de **pakket selecteren** pagina (beschikbaar vanaf versie 1702), geef de inhoud van het pakket opgenomen als onderdeel van het mediabestand en klik vervolgens op **volgende**.
10. Op de **stuurprogrammapakket selecteren** pagina (beschikbaar vanaf versie 1702), geef de inhoud van het stuurprogramma-pakket opnemen als onderdeel van het mediabestand en klik vervolgens op **volgende**.
11.  Op de **distributiepunten** pagina, geeft u de distributiepunten die vereiste inhoud bevatten, en klik vervolgens op **volgende**.  

     Configuration Manager alleen weergegeven distributiepunten die de inhoud. Alle inhoud die is gekoppeld aan de takenreeks naar ten minste één distributiepunt voordat u verder gaat distribueren. Nadat u de inhoud distribueert, vernieuw de lijst met distributiepunten. Verwijder alle distributiepunten die u al op deze pagina hebt geselecteerd gaat u naar de vorige pagina en vervolgens weer terug naar de **distributiepunten** pagina. U kunt ook de wizard opnieuw. Zie voor meer informatie [inhoud waarnaar wordt verwezen door de takenreeks distribueren](manage-task-sequences-to-automate-tasks.md#BKMK_DistributeTS) en [inhoud en infrastructuur beheren](../../core/servers/deploy/configure/manage-content-and-content-infrastructure.md).  

    > [!NOTE]  
    >  U moet hebben **lezen** toegangsrechten voor de Inhoudsbibliotheek op de distributiepunten.  

12. Geef op de pagina **Aanpassing** de volgende informatie op en klik vervolgens op **Volgende**.  

    -   Geef de variabelen op die de takenreeks gebruikt voor het implementeren van het besturingssyteem.  

    -   Geef eventuele prestart-opdrachten die u wilt uitvoeren voordat de takenreeks. Prestart-opdrachten zijn een script of een uitvoerbaar bestand dat wordt uitgevoerd in Windows PE voordat de takenreeks wordt gestart. Zie voor meer informatie [Prestart-opdrachten voor takenreeksmedia](../understand/prestart-commands-for-task-sequence-media.md).  

         Selecteer desgewenst **bestanden voor de prestart-opdracht** vereiste te nemen met de bestanden voor de prestart-opdracht.  

        > [!TIP]  
        >  Tijdens het maken van de media taak, Configuration Manager schrijft de pakket-ID en prestart-opdrachtregel naar de **CreateTSMedia.log** bestand op de computer waarop de Configuration Manager-console. Deze uitvoer bevat de waarde voor eventuele takenreeksvariabelen. Bekijk dit logboekbestand om de waarde voor de takenreeksvariabelen te verifiëren.  

13. Voltooi de wizard.  

 De bestanden voor de zelfstandige media (.iso) worden in de doelmap gemaakt. Als u **Zelfstandige cd/dvd** hebt geselecteerd, kunt u de uitvoerbestanden nu kopiëren naar een set cd's of dvd's.  

##  <a name="BKMK_StandAloneMediaTSExample"></a>Voorbeeld van takenreeks voor zelfstandige media  
 Gebruik de volgende tabel als richtlijn voor het maken van een takenreeks om een besturingssysteem met zelfstandige media te implementeren. De tabel kunt u de algemene volgorde voor uw takenreeksstappen bepalen. Het helpt tevens ordenen en structuur van de takenreeksstappen in logische groepen. De takenreeks die u maakt, kan afwijken van dit voorbeeld en kan meer of minder takenreeksstappen en groepen bevatten.  

> [!NOTE]  
>  U moet altijd de Wizard Takenreeksmedia maken van zelfstandige media gebruiken.  

|Takenreeksgroep of -stap|Beschrijving|  
|---------------------------------|-----------------|  
|Bestanden en instellingen - vastleggen **(nieuwe Takenreeksgroep)**|Een takenreeksgroep maken. In een takenreeksgroep houdt u vergelijkbare takenreeksstappen bij elkaar voor betere ordening en foutcontrole.|  
|Windows-instellingen vastleggen|Gebruik deze takenreeksstap om vast te leggen van de Windows-instellingen van de doelcomputer voordat de installatiekopie. Naam van de computer, gebruiker en organisatiegegevens en de instellingen van de tijdzone vastleggen.|  
|Netwerkinstellingen vastleggen|Gebruik deze takenreeksstap om de netwerkinstellingen vast te leggen van de computer die de takenreeks ontvangt. U kunt naast de netwerkadapterinstellingen het lidmaatschap van de computer van een domein of werkgroep vastleggen.|  
|Vastleggen van gebruikersbestanden en -instellingen - **(nieuwe taak Takenreeks subgroep)**|Maak een takenreeksgroep binnen een takenreeksgroep. Deze subgroep bevat de stappen voor het vastleggen van gegevens van de gebruikersstatus van de doelcomputer voordat de installatiekopie. Vergelijkbaar met de eerste groep die u hebt toegevoegd, is deze subgroep houdt vergelijkbare takenreeksstappen bij elkaar voor betere ordening en foutcontrole.|  
|Locatie van lokale status instellen|Gebruik deze takenreeksstap om een lokale locatie met de takenreeksvariabele voor een beveiligd pad op te geven. De gebruikersstatus wordt opgeslagen in een beveiligde map op de harde schijf.|  
|Gebruikersstatus vastleggen|Gebruik deze takenreeksstap om de gebruikersbestanden en -instellingen vast te leggen die u wilt migreren naar het nieuwe besturingssysteem.|  
|Besturingssysteem installeren - **(nieuwe Takenreeksgroep)**|Een andere taak sequence subgroep maken. Deze subgroep bevat de stappen die nodig zijn om het besturingssysteem te installeren.|  
|Opnieuw opstarten in Windows PE of harde schijf|In deze takenreeksstap geeft u de opties op voor het opnieuw opstarten van de doelcomputer die deze takenreeks ontvangt. Deze stap wordt een bericht voor de gebruiker die de computer opnieuw wordt opgestart om de installatie voort te.<br /><br /> Deze stap maakt gebruik van de alleen-lezen takenreeksvariabele **_SMSTSInWinPE** . Als de gekoppelde waarde gelijk is aan **false**, de takenreeksstap voortgezet.|  
|Besturingssysteem toepassen|Met deze takenreeksstap installeert u de installatiekopie van het besturingssysteem op de doelcomputer. Deze stap worden alle bestanden op dat volume, met uitzondering van Configuration Manager-specifieke besturingsbestanden verwijderd. Vervolgens wordt alle volume afbeeldingen in het WIM-bestand naar het overeenkomstige sequentiële schijfvolume toegepast. U kunt ook een **sysprep**-antwoordbestand opgeven om te configureren welke schijfpartitie voor de installatie moet worden gebruikt.|  
|Windows-instellingen toepassen|Met deze takenreeksstap configureert u de configuratiegegevens voor de Windows-instellingen voor de doelcomputer. Deze instellingen omvatten de gebruiker en organisatiegegevens, product-of Licentiecodegegevens, tijdzone en het lokale administrator-wachtwoord.|  
|Netwerkinstellingen toepassen|Met deze takenreeks geeft u de gegevens voor netwerk- of werkgroepconfiguratie op voor de doelcomputer. U kunt ook opgeven of de computer een DHCP-server gebruikt of u kunt de IP-adresgegevens statisch toewijzen.|  
|Stuurprogrammapakket toepassen|Gebruik deze takenreeksstap om alle apparaatstuurprogramma's in een stuurprogrammapakket beschikbaar te maken voor gebruik door Windows Setup. Alle benodigde apparaatstuurprogramma's moeten zijn opgenomen op de zelfstandige media.|  
|Besturingssysteem installeren - **(nieuwe Takenreeksgroep)**|Een andere taak sequence subgroep maken. Deze subgroep bevat de stappen die nodig zijn om de Configuration Manager-client te installeren.|  
|Windows en ConfigMgr installeren|Gebruik deze takenreeksstap om de Configuration Manager-clientsoftware te installeren. Configuration Manager installeert en registreert de GUID van de Configuration Manager-client. U kunt de vereiste installatieparameters toewijzen in het venster **Installatie-eigenschappen** .|  
|Herstellen van gebruikersbestanden en -instellingen - **(nieuwe Takenreeksgroep)**|Een andere taak sequence subgroep maken. Deze subgroep bevat de stappen die nodig zijn om de gebruikersstatus te herstellen.|  
|Gebruikersstatus herstellen|Gebruik deze takenreeksstap om te initiëren User State Migration Tool (USMT). USMT herstelt de gebruikersstatus en instellingen die eerder zijn vastgelegd met de stap gebruikersstatus vastleggen op de doelcomputer.|  
