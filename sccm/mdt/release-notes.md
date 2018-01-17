---
title: Release-opmerkingen
titleSuffix: MDT 2013 release notes
description: 'Vereisten en beperkingen van de Microsoft Deployment Toolkit 2013 begrijpen. '
ms.date: 09/09/2016
ms.prod: configuration-manager
ms.technology: configmgr-osd
ms.topic: article
ms.assetid: 6e32ce6d-585d-4801-a345-ff0f6f2d90ad
author: aczechowski
ms.author: aaroncz
manager: angrobe
ms.openlocfilehash: 11b3eb6ed778cca78823c58b606d98166ded9b55
ms.sourcegitcommit: 645cd5a324bdd299906efa27eaca5885eafc9e9c
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 01/16/2018
---
# <a name="microsoft-deployment-toolkit-2013-release-notes"></a>Opmerkingen bij de Release van de Microsoft Deployment Toolkit 2013  
 Welkom bij de release-opmerkingen voor Microsoft® Deployment Toolkit (MDT) 2013. Lees deze releaseopmerkingen zorgvuldig door voordat u MDT 2013 installeren als ze informatie die u nodig hebt bevatten voor een geslaagde installatie van de toolkit die niet betrekking op de help-documentatie voor MDT 2013 hebben kan.  

 Deze versie ondersteunt de implementatie van de Windows 8.1, Windows 8, Windows 7, Thin Windows-PC-, Windows Embedded POSReady 7 (POSReady 7), Windows Server 2012 R2, Windows Server 2012 en Windows Server 2008 R2-besturingssystemen. Zie de Microsoft Deployment Toolkit Documentatiebibliotheek, die meegeleverd met MDT 2013, voor de volledige documentatie voor deze release wordt.  

> [!NOTE]
>  In dit document, *Windows* geldt voor de besturingssystemen Windows 8.1, Windows 8, Windows 7, Windows Server 2012 R2, Windows Server 2012 en Windows Server 2008 R2, tenzij anders vermeld. MDT biedt geen ondersteuning voor ARM-processor gebaseerde versies van Windows. Op deze manier *MDT* verwijst naar MDT 2013, tenzij anders vermeld.  

## <a name="prerequisites"></a>Vereisten  
 Voor implementaties van Lite Touch Installation (LTI) moet MDT de volgende onderdelen:  

 MDT installeren op:  

-   Windows 7 of Windows Server 2008 R2 installeren en inschakelen van de volgende onderdelen op de computer waarop u MDT installeren:  

    -   Versie van Microsoft Management Console 3.0  

    -   Microsoft .NET Framework 3.5 met servicepack 1 (SP1)  

    -   Windows PowerShell™ versie 2.0  

    -   Windows Assessment and Deployment Kit (ADK) voor Windows 8.1 (componenten-hulpprogramma's voor Windows PE en User State Migration Tool)  

-   Windows 8.1, Windows 8, Windows Server 2012 R2 of Windows Server 2012 installeren of inschakelen van de volgende onderdelen op de computer waarop u MDT installeren:  

    -   Windows ADK voor Windows 8.1 (componenten-hulpprogramma's voor Windows PE en User State Migration Tool)  

    -   Microsoft .NET Framework 4.0 (dat is opgenomen in het besturingssysteem)  

    -   Windows PowerShell versie 3.0 (die is opgenomen in het besturingssysteem)  

 Voor implementaties van Zero Touch installatie (ZTI) moet MDT de volgende onderdelen:  

-   Microsoft System Center 2012 R2 Configuration Manager  

> [!NOTE]
>  Zie de productdocumentatie van Configuration Manager voor aanvullende vereisten.  

 Voor implementaties van UDI (User Driven installatie) moet MDT de volgende onderdelen:  

-   Microsoft System Center 2012 R2 Configuration Manager  

-   Microsoft System Center 2012 Configuration Manager  

-   Microsoft System Center Configuration Manager 2007 R3  

> [!NOTE]
>  Zie de productdocumentatie van Configuration Manager voor aanvullende vereisten.  

 Voor het initiëren van Microsoft System Center 2012 R2 Orchestrator-runbooks met MDT, installeert u de [ADO.NET Data Services Update voor .NET Framework 3.5 SP1 voor Windows 7 en Windows Server 2008 R2](http://www.microsoft.com/download/details.aspx?displaylang=en&id=2343).  

## <a name="installing-mdt"></a>MDT installeren  
 Zorg ervoor dat u een volledige back-up van uw server hebt voordat u MDT installeert op een computer met een bestaande installatie van MDT.  

 Het installatieproces MDT verwijdert alle bestaande exemplaren van MDT is geïnstalleerd op dezelfde computer. Bestaande implementatieshares, distributiepunten en databases die behouden blijven tijdens dit proces maar moeten worden bijgewerkt wanneer de installatie voltooid is.  

### <a name="support-for-upgrading-from-previous-versions-of-mdt"></a>Ondersteuning voor het upgraden van eerdere versies van MDT  
 MDT 2013 ondersteunt de upgrade van de volgende versies van MDT:  

-   MDT 2012 Update 1  

> [!NOTE]
>  Maak een back-up van de bestaande infrastructuur van de MDT voordat u probeert een upgrade.  

### <a name="usmt-download-requirements"></a>Vereisten voor USMT downloaden  
 U moet niet meer afzonderlijk Windows User State Migration Tool (USMT) te downloaden. USMT versie 6 is een onderdeel van de Windows ADK voor Windows 8.1. USMT 6 ondersteunt vastleggen Gebruikersstatus van alle versies van Windows 8.1, Windows 8 en Windows 7.  

### <a name="the-lti-upgrade-process"></a>Het upgradeproces LTI  
 Nadat MDT is geïnstalleerd, kunt u een bestaande implementatieshare bijwerken door het uitvoeren van de Open wizard implementatietype maken vanuit de node Implementatieshares in de implementatie-Workbench. Geef het pad naar de bestaande implementatie gedeelde map, en selecteer vervolgens de **Upgrade** selectievakje. Houd er rekening mee dat in dat geval ook upgrades bestaande implementatie netwerkshares en media implementatieshares, zodat deze toegankelijk moeten zijn. Deze upgrade tijdens het uitvoeren van implementaties, niet uitvoeren omdat de bestanden in gebruik upgrade problemen kunnen veroorzaken.  

### <a name="the-zti-upgrade-process"></a>Het upgradeproces ZTI  
 Bestaande MDT takenreeksen aanwezig is in System Center 2012 Configuration Manager niet worden gewijzigd tijdens het installatieproces van MDT en moeten blijven werken zonder eventuele problemen. Er is geen mechanisme geleverd voor de upgrade van deze takenreeksen. Als u gebruiken een van de nieuwe MDT-mogelijkheden wilt, maakt u nieuwe takenreeksen.  

 Wanneer het upgradeproces is voltooid:  

-   **Voer de Wizard Configuration Manager-integratie te configureren.** U moet deze wizard uitvoeren na de upgrade naar de nieuwe onderdelen registreren en installeer de bijgewerkte ZTI taak reeks sjablonen.  

-   **Zorg ervoor dat u maakt een nieuw pakket Microsoft Deployment Toolkit-bestanden voor alle nieuwe ZTI-takenreeksen die u maakt.** U kunt het bestaande pakket van Microsoft Deployment Toolkit-bestanden gebruiken voor takenreeksen ZTI gemaakt vóór de upgrade, maar moet u een nieuw pakket Microsoft Deployment Toolkit-bestanden voor de nieuwe ZTI takenreeksen maken.  

## <a name="known-issues"></a>Bekende problemen  
 De bekende problemen met MDT 2013 worden als volgt ingedeeld:  

-   Voor algemene problemen, zoals beschreven in [bekende algemene problemen](#KnownIssue)  

-   Voor implementaties van LTI, zoals beschreven in [bekende problemen voor alleen implementaties van LTI](#KnownIssuesLTI)  

-   Voor LTI en ZTI implementaties, zoals beschreven in [bekende problemen voor LTI en implementaties van ZTI](#KnownIssuesLTIZTI)  

-   Voor UDI implementaties, zoals beschreven in [bekende problemen voor UDI implementaties](#KnownIssuesUDI)  

###  <a name="KnownIssue"></a>Algemene problemen  
 De volgende problemen zijn niet specifiek zijn voor een implementatiemethode.  

#### <a name="compiled-html-help-files-are-not-up-to-date"></a>Gecompileerde HTML help-bestanden zijn niet actueel  
 Alle gecompileerd HTML help-bestanden (. CHM) opgenomen met MDT 2013, met inbegrip van 'Microsoft Deployment Toolkit documentatie Library.chm' en 'Notes.chm Release' huidige vanaf de release van MDT 2012 Update 1 zijn. Alle 'Help' koppelingen in de implementatie-Workbench wordt inhoud in deze bestanden zijn geopend.  

 TIJDELIJKE OPLOSSING: Dit document bevat de releaseopmerkingen voor MDT 2013 en vervangt 'Release Notes.chm' in de installatiemap.  

 Een bijgewerkte MDT Documentatiebibliotheek in Microsoft Word-indeling is alleen beschikbaar vanuit het Microsoft Download Center gepland.  

#### <a name="modifying-key-task-sequence-steps-can-lead-to-unpredictable-results"></a>Wijzigen van de belangrijkste takenreeksstappen kan leiden tot onvoorspelbare resultaten  
 Wijzigen van de **besturingssysteem installeren** takenreeksstap of de **Besturingssysteeminstallatiekopie toepassen** takenreeksstap nadat het maken van de takenreeksstap tot onvoorspelbare resultaten leiden kan. Bijvoorbeeld, als u een takenreeks maken om te implementeren installatiekopie van 32-bits Windows 7 en later wijzigen de **besturingssysteem installeren** takenreeksstap of de **Besturingssysteeminstallatiekopie toepassen** takenreeksstap om te verwijzen naar een 64-bits Windows 7-installatiekopie, is het mogelijk dat de takenreeks niet is uitgevoerd.  

 TIJDELIJKE OPLOSSING: Een nieuwe takenreeks maken voor het implementeren van de installatiekopie van een ander besturingssysteem.  

#### <a name="domain-join-fails-when-an-organizational-unit-ou-contains-special-characters"></a>Lid van domein mislukt als een organisatie-eenheid (OE), speciale tekens bevat  
 Lid van domein mislukt als een organisatie-eenheid (OE), speciale tekens in Unicode-indeling bevat. Als de naam van de organisatie-eenheid spaties bevat, moeten de methoden die hieronder worden beschreven correct functioneren. Als de organisatie-eenheid andere tekens heeft, zoals taalspecifieke tekens vervangen door de tekens hun equivalente ANSI-teken. U zou bijvoorbeeld Cońtoso wijzigen naar Contoso.  

 TIJDELIJKE OPLOSSING: Selecteer een van de volgende methoden om dit probleem te verhelpen:  

-   Gebruik de **MachineObjectOU** eigenschap, zoals in het volgende voorbeeld om op te geven van de organisatie-eenheid voor de computer in het bestand CustomSettings.ini of in de database van de MDT (MDT DB).  

    ```  
    [Settings]   
    Priority=MacAddress, Default   
    Properties=MyCustomProperty   

    [Default]   
    OSinstall=Y  

    [00:15:1d:ee:2a:aa]   
    OSDComputername=WDG-CLI-01   
    MachineObjectOU=OU=HelpDesk,OU=Corp,DC=Woodgrovebank,DC=com  
    ```  

-   Gebruik de **DomainOUs** zoals weergegeven in het volgende voorbeeld wordt een lijst van organisatie-eenheden maken in het CustomSettings.ini-bestand of de MDT-DB die kunnen worden geselecteerd in de Wizard implementatie-eigenschap.  

    ```  
    [Settings]   
    Priority=MacAddress, Default   
    Properties=MyCustomProperty   

    [Default]  
    OSInstall=Y  
    SkipAppsOnUpgrade=YES  
    SkipCapture=YES  
    SkipAdminPassword=NO  
    SkipProductKey=YES  
    DoCapture=YES  
    DomainOUs1=OU=Users,OU=Corp,DC=Woodgrovebank,DC=com   
    DomainOUs2=OU=HelpDesk,OU=corp,DC=Woodgrovebank,DC=com  
    ```  

-   Gebruik het bestand DomainOUList.xml zoals weergegeven in het volgende voorbeeld om een lijst van OE's die kunnen worden geselecteerd in de Wizard implementatie te maken.  

    ```  
    <?xml version="1.0" encoding="utf-8"?>   
    <DomainOUs>   
       <DomainOU>   
          OU=Users,OU=Corp,DC=Woodgrovebank,DC=com  
       </DomainOU>   
       <DomainOU>   
         OU=HelpDesk,OU=corp,DC=Woodgrovebank,DC=com  
       </DomainOU>   
    </DomainOUs>  
    ```  

     U kunt het DomainOUList.xml-bestand met een XML-editor te maken. Plaats het bestand DomainOUList.xml in de map Scripts in een implementatieshare voor LTI of in het pakket MDT-bestanden voor ZTI en UDI.  

#### <a name="configure-adds-step-does-not-have-an-option-for-windows-server-2012-domain-and-forest-functional-levels"></a>Configureer ADDS stap geen optie voor Windows Server 2012-domein- en forestfunctionaliteitsniveaus  
 Bij het configureren van geavanceerde opties voor de stap 'VOEGT configureren' hoeft in de lijsten met het functionaliteitsniveau van Forest en het functionele domeinniveau geen een optie voor Windows Server 2012.  

 TIJDELIJKE OPLOSSING: Stel DomainLevel = 5 en/of ForestLevel = 5 in CustomSettings.ini. Zie de Toolkit-verwijzing voor meer informatie over deze instellingen.  

#### <a name="gpo-packs-do-not-exist"></a>Groepsbeleidsobject Packs bestaat niet  
 De GPO-Packs Security naleving Manager (SCM) zijn niet opgenomen in MDT 2013. De stap 'Lokale pakket groepsbeleidsobject toepassen' (ZTIApplyGPOPack.wsf) wordt een vermelding die lijkt op een van de volgende vastleggen:  

 'Het pad GPO Pack – Templates\GPOPacks\ is niet geldig. Het GPO is niet toegepast."  

 "Standaard MDT GPO Pack niet aanwezig is voor dit besturingssysteem."  

 TIJDELIJKE OPLOSSING: De submap GPOPacks onder sjablonen maken in de implementatieshare (bijvoorbeeld C:\DeploymentShare\Templates\GPOPacks). Een groepsbeleidsobject back-up van SCM of GPMC exporteren en vervolgens de volgende bestanden van SCM toevoegen:  

-   GPOPack.wsf  

-   LocalPol.exe  

-   LocalSecurityDB.sdb  

 Maak een submap onder GPOPacks en kopieer deze inhoud. Geef vervolgens de naam van de map in de eigenschap GPOPackPath in CustomSettings.ini.  

#### <a name="the-configuration-manager-console-will-crash-if-mdt-is-uninstalled-without-removing-the-console-extensions"></a>De Configuration Manager-console wordt vastlopen als MDT zonder te verwijderen van de uitbreidingen van de console wordt verwijderd.  
 Bij het uitvoeren van **Configuration Manager-integratie configureren**, als u de optie uitschakelen **verwijderen van de MDT-uitbreidingen voor Configuration Manager 2012**, het volgende foutbericht weergegeven wanneer u bij het starten van de Configuration Manager-console:  

```  
Couldn’t load sqmapi.dll from bin\x86\sqmapi.dll. Last Error = (126)  
```  

 TIJDELIJKE OPLOSSING: Geen  

#### <a name="oobe-settings-missing-from-windows-81-unattendxml-template"></a>OOBE-instellingen van Windows 8.1 Unattend.xml sjabloon ontbreekt  
 Windows 8.1-takenreeksen gebruiken een oudere Unattend.xml-sjabloon die geen enkele eigenschappen in de < OOBE\> secties, zoals HideWirelessSetupInOOBE waarvoor handmatige interactie met implementaties op systemen met draadloze kunt netwerkadapters.  

 TIJDELIJKE OPLOSSING: De volgende items aan de < OOBE\> sectie van de takenreeksen Unattend.xml voor Windows 8.1.  

```  
<OOBE>  
    <HideEULAPage>true</HideEULAPage>  
    <NetworkLocation>Work</NetworkLocation>  
    <ProtectYourPC>1</ProtectYourPC>  
    <HideLocalAccountScreen>true</HideLocalAccountScreen>  
    <HideOnlineAccountScreens>true</HideOnlineAccountScreens>  
    <HideWirelessSetupInOOBE>true</HideWirelessSetupInOOBE>  
</OOBE>  
```  

#### <a name="some-features-are-listed-incorrectly-for-windows-81"></a>Sommige functies worden niet correct vermeld voor Windows 8.1  
 Wanneer u de **Installeer functies en onderdelen** of **verwijderen van functies en onderdelen** stappen en het selecteren van Windows 8.1-toepassing van de volgende problemen:  

-   **Internet Explorer 10 (x86)**, die verwijst naar de functie Internet-Explorer-optioneel-x86 en **Internet Explorer 10 (amd64)**, die verwijst naar de functie Internet-Explorer-optioneel-amd64 wordt weergegeven in Windows 8.1 gebruikt als "Internet Explorer 11."  

-   De **werk mappen Client** (WorkFolders-Client) is niet opgenomen in de lijst.  

 TIJDELIJKE OPLOSSING: De Internet Explorer 10... selecties nog kunnen worden gebruikt, maar wordt in- of uitschakelen in plaats van Internet Explorer 10 van Internet Explorer 11 zoals vermeld. De mappen werk Client moet worden ingeschakeld of uitgeschakeld in een afzonderlijke **opdrachtregel uitvoeren** stap met behulp van DISM, bijvoorbeeld:  

```  
Dism /online /Enable-Feature /FeatureName:WorkFolders-Client  
```  

###  <a name="KnownIssuesLTI"></a>Bekende problemen voor alleen implementaties van LTI  
 Hier volgt een lijst met bekende problemen die betrekking op alleen implementaties van LTI hebben.  

#### <a name="check-for-updates-downloads-an-older-list-of-components"></a>Controleren op Updates die zijn gedownload van een oudere lijst van onderdelen  
 In de Implementatieworkbench, Information Center onderdelen knooppunt selecteren **controleren op Updates** van de **actie** menu wordt een oudere versie van bddmanifest.cab, waarbij het onderdeel downloaden manifest (componentlist.xml terugschakelt) naar een oudere versie.  

 TIJDELIJKE OPLOSSING: Gebruik geen **controleren op Updates**; deze functie is afgeschaft en wordt in de toekomst verwijderd.  

#### <a name="windows-81-appx-cleanup-maintenance-task-can-affect-sysprep"></a>Windows 8.1 AppX-onderhoudstaak voor opschoning kan van invloed zijn op Sysprep  
 Na de installatie van Windows 8.1 een ingebouwde onderhoudstaak voorbereide App-opschoning uitvoeren na 60 minuten over het gebruik van de machine, gevolgd door 15 minuten van inactiviteit machine. Als Sysprep wordt uitgevoerd na voltooiing van deze onderhoudstaak, genereert het waarschuwingen in het bestand setupact.log voor Sysprep. Als u deze installatiekopie vervolgens worden vastgelegd en is geïmplementeerd, kan de eindgebruikerservaring nadelig worden beïnvloed. Specifiek resource packs op basis van taal, schaal en DXFL die niet werden geïnstalleerd voor de huidige gebruikersaccounts worden verwijderd. Als u deze installatiekopie wordt geïmplementeerd op een machine indien deze bronpakketten van toepassing zijn, moeten ze worden geïnstalleerd als een update via de Store of via een enterprise-sideloading-mechanisme.  

 TIJDELIJKE OPLOSSING: Er zijn twee opties voor dit probleem te verhelpen. Eerst voor zorgen dat Sysprep wordt uitgevoerd binnen 75 minuten na voltooiing van de installatie van Windows 8.1. Ten tweede uitschakelen als u niet garanderen kan dat Sysprep wordt uitgevoerd binnen 75 minuten na voltooiing van de installatie van Windows 8.1, de onderhoudstaak.  

 Automatisch de onderhoudstaak uitschakelt als onderdeel van de MDT-build en vast te leggen takenreeks, direct na de **verzamelen alleen lokale** stap in de **11statusherstelfase** groep invoegen in een nieuwe **Opdrachtregel uitvoeren** stap met de volgende opdrachtregel:  

```  
Schtasks.exe /change /disable /tn "\Microsoft\Windows\AppxDeploymentClient\Pre-staged app cleanup"  
```  

 Bijvoorbeeld:  

 ![MDT 2013 Release Notes Image 1](media/MDT2013ReleaseNotesImage1.jpg "MDT2013ReleaseNotesImage1")  

 Deze stap moet alleen worden toegevoegd aan takenreeksen waarmee Sysprep wordt uitgevoerd op Windows 8.1. Windows automatisch opnieuw toe te voegen onderhoud tijdens de Sysprep generalize-fase.  

#### <a name="existing-databases-will-retain-50-character-application-names-when-upgrading-to-mdt-2013"></a>Bestaande databases, 50 teken toepassingsnamen behouden bij een upgrade naar MDT 2013  
 MDT 2013 bevat een wijziging in de database uit te breiden veld voor de toepassingsnaam van 50 tot 255 tekens. Een nieuwe database in MDT 2013 maakt gebruik van het veld van 255 tekens. Een bestaande database is bijgewerkt van MDT 2012 Update 1 voor MDT 2013, behouden die het veld van 50 tekens.  

 TIJDELIJKE OPLOSSING: Na de upgrade handmatig naar MDT 2013 alter database-tabel met de volgende SQL-opdrachten:  

```  
ALTER TABLE [dbo].[Settings_Applications]   
ALTER COLUMN [Applications] [nvarchar] (256)  
```  

#### <a name="the-deployment-will-fail-on-a-legacy-bios-system-if-bitlocker-is-enabled-and-a-data-partition-is-created"></a>Mislukt de implementatie op een verouderde BIOS-systeem als BitLocker is ingeschakeld en een partitie is gemaakt  
 Als de implementatie van BitLocker wordt ingeschakeld, de standaardwaarde 'Indeling en Partitieschijf' stap in de takenreeks is toegevoegd, zodat een partitie aanvullende gegevens (bijvoorbeeld OSDisk [primaire] 60%, gegevens [primaire] 100%), en de takenreeks wordt geïmplementeerd op een verouderd BIOS systeem, mislukt de implementatie op te starten in Windows met de fout:  

```  
Boot Device Not Found  
Please install an OS on your hard disk  
Hard Disk - (3F0)  
```  

 TIJDELIJKE OPLOSSING: Geen  

#### <a name="provisioning-of-windows-store-applications-does-not-include-dependencies"></a>Het inrichten van Windows Store-toepassingen bevat geen afhankelijkheden  
 Afhankelijkheden zijn geconfigureerd voor een Windows Store-toepassing (.appx) wordt niet geïnstalleerd wanneer de takenreeks wordt toepassingen geïnstalleerd.  

 TIJDELIJKE OPLOSSING: Installeer de afhankelijkheden voor toepassingen rechtstreeks in de takenreeks.  

#### <a name="gpt-drives-are-partitioned-as-mbr"></a>GPT-schijven worden gepartitioneerd als MBR-schijven  
 Een station is geconfigureerd voor gebruik van de GPT (GUID Partition Table) schijfpartitionering systeem in de **schijf formatteren en partitioneren** takenreeksstap, maar wordt geïmplementeerd met behulp van de Master Boot Record (MBR) schijfpartitionering systeem, in plaats daarvan. Dit probleem kan worden veroorzaakt op computers met BIOS die tweede stations zijn die groter zijn dan 2 GB en een GPT-partitionering systeem vereist.  

 Tijdelijke oplossing: Voer de volgende stappen uit:  

1.  In de takenreeks die u wilt wijzigen, in de **Preinstall** groep in de **nieuwe Computer alleen** groep direct vóór de **schijf formatteren en partitioneren** takenreeksstap voor de desbetreffende schijf maken van een takenreeksstap op basis van de **Takenreeksvariabele instellen** task sequence type om af te dwingen het gebruik van het systeem GPT-schijf partitie met de volgende gegevens.

    |Voor deze instelling|Deze waarde wordt gebruikt|  
    |-|-|  
    |Name|Gebruik van GPT-partitie schijfsysteem forceren|  
    |Beschrijving|De volgende schijf formatteren en partitioneren takenreeksstap voor het systeem GPT-schijf partitie te forceren.|  
    |Takenreeksvariabele|OSDDiskType|  
    |Waarde|GPT|  

2.  Direct na de **schijf formatteren en partitioneren** takenreeksstap in de vorige stap hebt geïdentificeerd maken van een takenreeksstap op basis van de **Takenreeksvariabele instellen** type takenreeks opnieuw instellen van de taak de het gebruik van het systeem GPT-schijf partitie met de volgende gegevens.

    |Voor deze instelling|Deze waarde wordt gebruikt|  
    |-|-|  
    |Name|Gebruik van GPT-partitie schijfsysteem opnieuw instellen|  
    |Beschrijving|Toestaan dat alle daaropvolgende schijf formatteren en partitioneren taak reeks stappen voor het gebruik van de partitie schijfsysteem opgegeven door de BIOS.|  
    |Takenreeksvariabele|OSDDiskType|  
    |Waarde||  

    > [!NOTE]
    >  Laat de waarde voor de **OSDDiskType** ingevoerd in de eigenschap **waarde** leeg.  

#### <a name="domain-join-fails-due-to-default-variable-values"></a>Aan domein toevoegen is mislukt vanwege de standaardwaarden voor variabelen  
 Wanneer de invoer van het lidmaatschap van een domein wordt overgeslagen waarden op de **Computerdetails** pagina in de Wizard implementatie van de wizard (met behulp van de **SkipDomainMembership** eigenschap), de waarden voor de  **DomainAdminDomain**, **DomainAdminUser**, en **DomainAdminPassword** eigenschappen worden ingesteld op standaardwaarden en de doelcomputer kan geen eigenschap deelnemen aan het domein is. Dit probleem kan worden veroorzaakt door niet toe te voegen waarden voor deze eigenschappen in het CustomSettings.ini-bestand of de MDT-database.  

 TIJDELIJKE OPLOSSING: Geef ten minste één van de volgende eigenschappen in het CustomSettings.ini-bestand of de MDT-DB:  

-   **DomainAdminDomain**  

-   **DomainAdminUser**  

-   **DomainAdminPassword**  

 Neem bijvoorbeeld het volgende fragment van een CustomSettings.ini-bestand:  

```  
SkipDomainMembership=YES  
DomainAdminDomain=Contoso  
JoinDomain=Contoso.com  
```  

 Een van deze eigenschappen opgeven, krijgt de gebruiker voor het invoeren van waarden voor domein-lidmaatschap op de **Computerdetails** pagina in de Wizard implementatie van de wizard.  

> [!NOTE]
>  U kunt ook volledig overslaan de **Computerdetails** wizardpagina door te geven van alle eigenschappen die hierboven worden genoemd in het CustomSettings.ini-bestand of de MDT-database. Zie voor meer informatie de sectie 'Bieden eigenschappen voor overgeslagen implementatie wizardpagina's ' in het document MDT *Toolkit verwijzing*.  

#### <a name="user-data-may-not-be-restored-from-usb"></a>Gebruikersgegevens kan niet worden hersteld vanaf een USB  
 Migratie van gebruikersstatusgegevens kan niet worden hersteld bij het opslaan van de migratie van gebruikersstatusgegevens op een USB-station. Dit wordt veroorzaakt door een wijziging in de stationsletter van het USB-station tijdens de implementatie.  

 TIJDELIJKE OPLOSSING: Geen  

#### <a name="user-mapped-network-drive-z-is-not-restored"></a>Gebruiker toegewezen netwerkstation die z: is niet hersteld.  
 Gebruiker bureaubladachtergrond en geen netwerkstations zijn hersteld in het implementatiescenario Computer vernieuwen. Dit kan worden veroorzaakt wanneer de gebruiker een netwerkstation toegewezen aan het station Z heeft. Na het voltooien van de **implementatieoverzicht** in het dialoogvenster gebruiker bureaubladachtergrond wordt hersteld. De gebruiker moet echter mogelijk om de toewijzing aan het station Z opnieuw te maken.  

 TIJDELIJKE OPLOSSING: Geen  

#### <a name="bare-metal-deployment-fails-with-fixed-disk-usb-flash-drive-on-uefi-system"></a>Bare-metal implementatie mislukt met 'vaste schijf' USB-flashstation op UEFI-systeem  
 Bij het uitvoeren van een bare-metal en media gebaseerde implementatie op een Unified Extensible Firmware Interface (UEFI) systeem met een nieuwere USB-flashstation (UFD) dat wordt gedetecteerd als een 'vaste schijf' wordt de USB-Flashstation gedetecteerd als schijf 1 (in eerste instantie de stationsletter C toegewezen) en de interne harde schijf is schijf 0. Nadat de interne harde schijf is gepartitioneerd en geformatteerd, is het station letters zijn toegewezen, zodat de OSDisk C en het USB-Flashstation is W. De implementatie mislukt bij de stap Script kopiëren.  

 TIJDELIJKE OPLOSSING: Het systeem opnieuw op en start een nieuwe implementatie. Het OSDisk wordt de stationsletter C worden toegewezen, het USB-Flashstation wordt D worden toegewezen en de implementatie wordt voortgezet met succes.  

#### <a name="lti-progress-on-the-windows-81-desktop-is-not-visible-from-the-start-screen"></a>Voortgang van de LTI op het bureaublad van Windows 8.1 is niet zichtbaar vanuit het startscherm  
 Een lite-touch installation (LTI) wordt automatisch aanmelden als lokale beheerder om door te gaan van de takenreeks, maar Windows 8.1 wordt, standaard, meld u aan bij het startscherm. LTI kan worden gestart tijdens de aanmelding zoals verwacht, maar de voortgangsindicator wordt alleen weergegeven op het bureaublad.  

 TIJDELIJKE OPLOSSING: Er zijn twee mogelijke oplossingen. Een gebruiker op de console Klik eerst het bureaubladpictogram op het startscherm om de voortgang van de LTI weer te geven.  

 Ten tweede de volgende opdracht kan worden toegevoegd aan de sectie Unattend.xml FirstLogonCommands tijdelijk inschakelen de groepsbeleidsinstelling **gaat u naar het bureaublad in plaats van starten tijdens het aanmelden**.  

```  
<FirstLogonCommands>  
  <SynchronousCommand wcm:action="add">  
    <CommandLine>wscript.exe %SystemDrive%\LTIBootstrap.vbs</CommandLine>  
    <Description>Lite Touch new OS</Description>  
    <Order>1</Order>  
  </SynchronousCommand>  
  <SynchronousCommand wcm:action="add">  
    <CommandLine>cmd /c reg add "HKEY_LOCAL_MACHINE\SOFTWARE\Policies\Microsoft\Windows\Explorer" /v GoToDesktopOnSignIn /t REG_DWORD /d 00000001 /f </CommandLine>  
    <Description>GoToDesktopOnSignIn</Description>  
    <Order>2</Order>  
  </SynchronousCommand>   </FirstLogonCommands>  
```  

> [!NOTE]
>  alleen de **tweede** SynchronousCommand element is toegevoegd; het eerste wordt al bestaan in de sjabloon Unattend.xml  

 Een ander mechanisme moet ook worden gebruikt voor later verwijdert deze tijdelijke instelling, zoals Active Directory-groepsbeleid of door het verwijderen van de registersleutel verderop in de takenreeks wordt uitgevoerd. Bijvoorbeeld:  

 ![MDT 2013 Release Notes Image 2](media/MDT2013ReleaseNotesImage2.png "MDT2013ReleaseNotesImage2")  

### <a name="known-issues-for-all-configuration-manager-deployments"></a>Bekende problemen voor alle Configuration Manager-implementaties  
 Hier volgt een lijst met bekende problemen die betrekking hebben op ZTI of UDI implementaties die gebruikmaken van System Center 2012 R2 Configuration Manager:  

#### <a name="default-os-image-installed-to-d-drive"></a>Standaard OS-installatiekopie op D: schijf geïnstalleerd  
 De standaard-installatiekopie van het besturingssysteem (install.wim) importeren en implementeren met een takenreeks ZTI, wordt Windows worden geïnstalleerd op het station D: in plaats van de standaard station C:.  

 TIJDELIJKE OPLOSSING: De takenreeksvariabele OSDPreserveDriveLetter ingesteld op een lege waarde in plaats van de standaard False.  

#### <a name="bitlocker-tasks-fails-during-zti"></a>BitLocker taken mislukt tijdens ZTI  
 De **UILanguage** takenreeksvariabele moet worden ingesteld wanneer ZTIBde.wsf in een takenreeks ZTI. Anders mislukt ZTIBde.wsf.  

 TIJDELIJKE OPLOSSING: Geen  

#### <a name="the-task-sequence-fails-when-local-administrator-accounts-exist"></a>De takenreeks niet als lokale administrator-accounts bestaan  
 Een computer met behulp van ZTI en UDI takenreeksen vernieuwen mislukt wanneer lokale beheerdersaccounts aanwezig op de computer zijn. Takenreeksen mislukken wanneer de standaard **gebruikersstatus vastleggen** stap heeft **alle gebruikersprofielen met standaardopties vastleggen** geselecteerd maar de standaardwaarde **gebruikersstatus herstellen** stap heeft de **gebruikersprofielen lokale computer herstellen** selectievakje uitgeschakeld en Configuration Manager de nieuwe accounts niet kan migreren zonder wachtwoorden toewijzen.  

 TIJDELIJKE OPLOSSING: Handmatig wijzigen van de takenreeks, de optie voor het migreren van lokale accounts, en geef een wachtwoord moet worden gebruikt met het lokale account. Zie voor meer informatie [gebruikersstatus vastleggen](http://technet.microsoft.com/library/bb680924.aspx).  

### <a name="known-issues-for-zti-deployments-only"></a>Bekende problemen voor alleen implementaties van ZTI  
 Hier volgt een lijst met bekende problemen die betrekking op alleen implementaties van ZTI hebben.  

#### <a name="installing-chinese-windows-7-prompts-for-user-input"></a>Chinees Windows 7 installeren vraagt om invoer van gebruiker  
 Bij het implementeren van Windows 7 met Chinees, stopt het installatieproces wachten op invoer van gebruiker. Dit wordt veroorzaakt door een fout in het bestand Lang.ini in Windows 7.  

 TIJDELIJKE OPLOSSING: Werk het bestand Lang.ini zoals hieronder weergegeven.  

 Oorspronkelijke Lang.ini-bestand:  

```  
[Available UI Languages]  
zh-CN = 3  

[Fallback Languages]  
zh-CN = en-us  
```  

 Het bestand lang.ini na wijziging:  

```  
zh-CN = 2  
en-us = 3  

[Fallback Languages]  
zh-CN = en-us  
```  

#### <a name="restore-user-state-step-is-skipped-during-replace-scenario"></a>Stap gebruikersstatus herstellen is overgeslagen tijdens het vervangingsscenario  
 In een implementatiescenario Computer vervangen de **gebruikersstatus herstellen** takenreeksstap wordt overgeslagen als de **OSDStateStorePath** eigenschap is ingesteld op een geldige landinstelling of Universal Naming Convention pad.  

 TIJDELIJKE OPLOSSING: Stel de **USMTLocal** eigenschap op TRUE. In dat geval forceert ZTI UserState.wsf voor het herkennen van het pad in de **OSDStateStorePath** eigenschap. Dit wordt veroorzaakt door de Statusopslag opvragen takenreeksstap wordt overgeslagen en de vorige waarde in de **OSDStateStorePath** eigenschap te bewaren.  

#### <a name="the-task-sequence-may-fail-with-separate-system-or-active-partitions"></a>De takenreeks kan mislukken met een afzonderlijk systeem of actieve partities  
 Windows wordt niet een stationsletter toewijzen aan het systeem of de actieve partitie als dat station verschilt van het station waarop het besturingssysteem zich bevindt. Als de grootste partitie ook het systeem of actieve partitie is, wordt de takenreeks mislukken hervatten in het nieuwe besturingssysteem.  

 TIJDELIJKE OPLOSSING: Zorg ervoor dat de systeem- of actieve partitie niet groter zijn dan de besturingssysteempartitie als meerdere partities.  

#### <a name="usmt-targetwindows7-switch-fails-in-offline-scenario"></a>USMT /TargetWindows7 switch is mislukt in offline scenario  
 De volgende fout is opgetreden in de scanstate.log bij het uitvoeren van het implementatiescenario voor vernieuwen Computer MDT ZTI tijdens het vastleggen van status van gebruikersgegevens met de functie offlinemigratie van USMT met:  

```  
USMT error code 27: [gle=0x00000006]  
```  

 TIJDELIJKE OPLOSSING: Geen; Dit is een bekend probleem met de USMT.  

#### <a name="configure-adds-step-does-not-save-correctly"></a>Configureer ADDS stap worden niet correct opgeslagen  
 Met behulp van de **configureren VOEGT** stap, geavanceerde eigenschappen voor het Forest en het functionele domeinniveaus ingesteld op Windows Server 2003 of Windows Server 2008 R2 leidt ertoe dat de functionaliteitsniveaus ingesteld op Windows Server 2008.  

 TIJDELIJKE OPLOSSING: Stel DomainLevel = 5 en/of ForestLevel = 5 in CustomSettings.ini. Zie de Toolkit-verwijzing voor meer informatie over deze instellingen.  

#### <a name="server-task-sequence-template-fails-on-uefi-system"></a>Server taak sequence sjabloon mislukt op UEFI-systeem  
 Indien geïntegreerd met de sjabloon voor de taak reeks van MDT 2013-server in System Center 2012 R2 Configuration Manager, zullen de implementaties mislukken op sommige systemen Unified Extensible Firmware Interface (UEFI) bij het uitvoeren van de **indeling en partitie schijf (UEFI)**  stap met een toepassing een fout in de volgende strekking OsdDiskPart.exe: 'De instructie op 0x6e2c8374 verwijst naar geheugen op 0x00000120. Het geheugen kan niet worden gelezen. Klik op OK om het programma te beëindigen."  

 TIJDELIJKE OPLOSSING: Geen met ZTI scenario. LTI of alleen Configuration Manager-scenario's werken.  

###  <a name="KnownIssuesLTIZTI"></a>Bekende problemen voor LTI en implementaties van ZTI  
 Hier volgt een lijst met bekende problemen die betrekking op de LTI- en ZTI-implementaties hebben.  

#### <a name="roles-and-features-requiring-multiple-restarts-cause-problems-for-task-sequences"></a>Functies en onderdelen vereisen van meerdere opnieuw wordt opgestart oorzaak problemen voor takenreeksen  
 Installeren van functies of onderdelen, zoals **MICROSOFT-HYPER-V-ALL** of **RDS-extern bureaublad-SERVER** die meerdere opnieuw opstarten vereist of zijn afhankelijk van deze rollen of functies kunnen problemen veroorzaken tijdens de taak sequentiëren en moeten worden vermeden.  

 TIJDELIJKE OPLOSSING: De gewenste rol of functie installeren op een referentiecomputer en een installatiekopie met de gewenste rol of functie is al geïnstalleerd.  

#### <a name="multiple-logs-created-during-deployment"></a>Meerdere logboeken die zijn gemaakt tijdens de implementatie  
 Tijdens het Scanstate en Loadstate, kunnen meerdere exemplaren van de logboekbestanden worden gemaakt, bijvoorbeeld, BDD.log, BDD .log (1), ZTIUserstate.log en ZTIUserstate .log (1).  

 TIJDELIJKE OPLOSSING: Met uitzondering van de logboekbestanden of mappen logboek tijdens het uitvoeren van Scanstate en Loadstate.  

###  <a name="KnownIssuesUDI"></a>Bekende problemen voor UDI implementaties  
 Hier volgt een lijst met bekende problemen die betrekking op UDI implementaties hebben.  

#### <a name="udi-wizard-hides-no-data-option-on-user-state-page-in-capture-mode"></a>De Wizard UDI verbergt optie geen gegevens op de pagina status van gebruiker in de modus voor vastleggen  
 De pagina UserState kan niet worden aangepast met het keuzerondje 'Geen gegevens' wanneer deze zich in de modus voor vastleggen.  

 TIJDELIJKE OPLOSSING: Open het configuratiebestand van de wizard in Kladblok en de volgende eigenschap toevoegen aan de sectie 'Select Target' page, die wordt uitgevoerd in de modus voor vastleggen:  

```  
<Setter Property="DisplayNoDataInCaptureMode">true</Setter>  
```  

 Bijvoorbeeld:  

```  
<Setter Property="DataSourceText">Please select a location where user data will be captured.</Setter>  
<Setter Property="Format">disable</Setter>  
<Setter Property="FormatPrompt">disable</Setter>  
<Setter Property="MinimumDriveSize">10</Setter>  
<Setter Property="State">Capture</Setter>  
<Setter Property="NetworkDrive">n:</Setter>  
<Setter Property="DisplayNoDataInCaptureMode">true</Setter>  
```  

 Voor het verbergen van de gegevens' Nee' is keuzerondje de bovenstaande waarde ingesteld op false of verwijder de vermelding.  

#### <a name="the-time-and-currency-language-format-is-not-configured"></a>De tijd en valuta language-indeling is niet geconfigureerd  
 De tijd en valuta language-indeling is niet juist geconfigureerd op een doelcomputer, zelfs als de juiste taal is geselecteerd de **tijd en valuta-indeling (landinstelling)** lijst op de **taal** UDI Wizardpagina. Dit probleem kan worden veroorzaakt door een fout in het bestand UDIWizard.wsf. Het bestand UDIWizard.wsf bevindt zich de *mdt_files*\Scripts map (waarbij *mdt_files* is de map die als bron voor de MDT-pakket dat de takenreeks maakt gebruik van bestanden).  

 TIJDELIJKE OPLOSSING: Voer de volgende stappen uit om de fout is verholpen in het bestand UDIWizard.wsf:  

1.  Bewerk het bestand UDIWizard.wsf, dat zich bevindt in de *mdt_files*\Scripts map (waarbij *mdt_files* is de map die als bron voor de MDT-pakket dat de takenreeks maakt gebruik van bestanden).  

2.  De volgende regel verwijderen uit het bestand UDIWizard.wsf:  

    ```  
    oEnvironment.Item("UserLocale") = oEnvironment.Item("InputLocale")  
    ```  

    > [!NOTE]
    >  De tekst die hierboven worden genoemd is één regel in het bestand UDIWizard.wsf. Alle tekstomloop wordt veroorzaakt door de opmaak beperkingen van het document.  

3.  Sla het bestand UDIWizard.wsf.  

4.  De distributiepunten bijwerkt met de gewijzigde versie van het pakket van de MDT-bestanden die het bijgewerkte UDIWizard.wsf-bestand bevat.  

#### <a name="applications-do-not-appear-after-added"></a>Toepassingen worden niet weergegeven nadat toegevoegd  
 Toepassingen worden niet weergegeven in de ontwerpfunctie voor UDI of de Wizard UDI na te zijn toegevoegd in de ontwerpfunctie voor UDI. Dit probleem kan optreden, omdat de doelgroep van de toepassing niet is ingeschakeld voordat u een toepassing toevoegt.  

 TIJDELIJKE OPLOSSING: Selecteer de doelgroep van de toepassing voordat u een toepassing toevoegt.  

#### <a name="applications-may-not-be-installed"></a>Toepassingen mogelijk niet geïnstalleerd  
 Het installatieprogramma van toepassing (AppInstall.exe) kan toepassingen die worden geïmplementeerd voor gebruikers niet correct geïnstalleerd. Dit probleem kan worden veroorzaakt door **gebruiker toestaan hun primaire apparaten definiëren** wordt ingesteld op **Nee**.  

 TIJDELIJKE OPLOSSING: Stel de waarde van **gebruiker toestaan hun primaire apparaten definiëren** naar **Ja**. De **gebruiker toestaan hun primaire apparaten definiëren** besturingselement is gevonden in de **gebruiker en Apparaataffiniteit** sectie in het **standaardinstellingen** in de Overview\Client van het dialoogvenster Settings-knooppunt in de **beheer** navigatiedeelvenster in de Configuration Manager-Console.  

#### <a name="deployment-time-is-not-correct-during-stand-alone-media-deployment"></a>Implementatietijd is niet correct tijdens de implementatie van zelfstandige media  
 Als u zelfstandige media gebruikt, wordt de waarde weergegeven voor **implementatietijd** door **OSDResults** aan het einde van de implementatie kan niet worden gegarandeerd juist is, omdat er een netwerkverbinding wordt niet uitgegaan beschikbaar zijn wanneer u zelfstandige media. Daarom kan niet klok van de machine basic input/output system (BIOS) worden gesynchroniseerd op een juiste tijd. In sommige gevallen kan de implementatietijd een negatief tonen. cijfer, als deze gebeurtenis treedt op wanneer de tijd die beschikbaar zijn vanuit Windows PE aan het begin is onjuist ingesteld met een waarde die daadwerkelijk later is dan de tijd waarop de implementatie is voltooid.  

 TIJDELIJKE OPLOSSING: Geen  

#### <a name="osddomainname-variable-does-not-work-as-expected"></a>De variabele OSDDomainName werkt niet zoals verwacht  
 In het geval van UDI, de **OSDDomainName** takenreeksvariabele is hoofdlettergevoelig.  

 TIJDELIJKE OPLOSSING: Bij het instellen van de **OSDDomainName** waarde via een takenreeksstap of CS.ini, deze moet een exacte overeenkomst voor de domeinwaarde in het configuratiebestand UDI instelt.
