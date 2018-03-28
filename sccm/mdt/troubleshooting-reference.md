---
title: MDT oplossen
titleSuffix: Microsoft Deployment Toolkit
description: 'Verwijzing voor probleemoplossing voor de Microsoft Deployment Toolkit '
ms.date: 09/09/2016
ms.prod: configuration-manager
ms.technology:
- configmgr-osd
ms.topic: article
ms.assetid: 91a7a69a-deac-4b0f-aac9-b7bd187c53fb
author: aczechowski
ms.author: aaroncz
manager: angrobe
ms.openlocfilehash: efb65086878a46bfb3485fdd8b0be6f613225261
ms.sourcegitcommit: 11bf4ed40ed0cbb10500cc58bbecbd23c92bfe20
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 03/27/2018
---
# <a name="troubleshooting-reference-for-the-microsoft-deployment-toolkit"></a>Verwijzing voor probleemoplossing voor de Microsoft Deployment Toolkit
 De implementatie van besturingssystemen en toepassingen, evenals de migratie van gebruikersstatus kan een lastig datacenterbeheer zijn zelfs wanneer u zijn uitgerust met de juiste hulpprogramma's en richtlijnen. Deze verwijzing die deel uitmaakt van Microsoft® Deployment Toolkit (MDT) 2013, voorziet in informatie over de huidige bekende problemen, mogelijke oplossingen voor die problemen en richtlijnen voor probleemoplossing.  

> [!NOTE]
>  In dit document, *Windows* geldt voor de besturingssystemen Windows 8.1, Windows 8, Windows 7, Windows Server 2012 R2, Windows Server 2012 en Windows Server 2008 R2, tenzij anders vermeld. MDT biedt geen ondersteuning voor ARM-processor gebaseerde versies van Windows. Op deze manier *MDT* verwijst naar MDT 2013, tenzij anders vermeld.  

> [!NOTE]
>  Microsoft Diagnostics and Recovery Toolset (DaRT) bevat krachtige hulpprogramma's voor het herstellen en het oplossen van clientcomputers die niet worden gestart of instabiel geworden. DaRT kunt u de oorzaak van een crash, verloren bestanden terugzetten, enzovoort. U kunt ook DaRT gebruiken als een hulpprogramma voor het oplossen van problemen bij het ontwikkelen en implementeren van een Windows-besturingssysteem. Als u een installatiekopie van het ingebouwde niet correct gestart, kunt u bijvoorbeeld de clientcomputer met de installatiekopie met behulp van ERD Commander starten: een diagnose omgeving. Vervolgens kunt u verkennen van de clientcomputer harde schijf, het gebeurtenislogboek weergeven, verwijderen van updates, besturingssysteeminstellingen wijzigen, enzovoort. DaRT maakt deel uit van Microsoft Desktop Optimization Pack voor Software Assurance. Zie voor meer informatie over DaRT, [ http://www.microsoft.com/windows/enterprise/products-and-technologies/mdop/dart.aspx ](http://www.microsoft.com/windows/enterprise/products-and-technologies/mdop/dart.aspx).  

## <a name="understanding-logs"></a>Understanding Logboeken  
 Voordat u effectieve oplossen van problemen met MDT kunt beginnen, moet u een duidelijk beeld van de vele .log-bestanden die wordt gebruikt tijdens de implementatie van een besturingssysteem hebben. Als u welke logboekbestanden voor welke fouttoestand en welk tijdstip onderzoeken weet, vormen problemen die eenmaal waren mysterieuze en moeilijk te begrijpen duidelijke en begrijpen.  

 De indeling van logboekbestanden MDT is ontworpen om te worden gelezen door Trace32, dat deel uitmaakt van de System Center Configuration Manager 2007 Toolkit V2, downloaden van de [Microsoft Download Center](http://www.microsoft.com/download/details.aspx?id=9257). De logboeken kunnen ook worden gelezen door het hulpprogramma Configuration Manager Trace Log (CMTrace) die beschikbaar is in System Center 2012 Configuration Manager en latere versies. Gebruik deze hulpprogramma's waar mogelijk de logboekbestanden lezen omdat het zoeken naar fouten eenvoudiger maakt.  

 De rest van deze sectie worden de logboekbestanden worden gemaakt tijdens de implementatie, evenals tijdens Windows Setup. Deze sectie bevat ook voorbeelden van wanneer de bestanden te gebruiken voor het oplossen van problemen.  

### <a name="mdt-logs"></a>MDT-Logboeken  
 Logboekbestanden elk script MDT automatisch gemaakt wanneer wordt uitgevoerd. De namen van deze logboekbestanden overeenkomen met de naam van het script: maakt een logbestand met de naam bijvoorbeeld ZTIGather.wsf *ZTIGather.log*. Elk script wordt ook een algemene master logboekbestand (BDD.log) dat de inhoud van de logboekbestanden die MDT scripts maken aggregeert bijgewerkt. MDT-logboekbestanden bevinden zich in C:\MININT\SMSOSD\OSDLOGS tijdens de implementatie. Afhankelijk van het type van de implementatie wordt uitgevoerd van de logboekbestanden na het voltooien van de implementatie naar %WINDIR%\SMSOSD of % WINDIR%\TEMP\SMSOSD verplaatst. Voor implementaties van Lite Touch Installation (LTI) start u de logboeken in C:\MININT\SMSOSD\OSDLogs. Ze terechtkomen op %WINDIR%\TEMP\DeploymentLogs wanneer de taak sequence-verwerking voltooid is.  

 MDT maakt de volgende logboekbestanden:  

-   **BDD.log**. Dit is de geaggregeerde MDT logboekbestand wordt gekopieerd naar een netwerklocatie aan het einde van de implementatie als u opgeeft de **SLShare** eigenschap in het Customsettings.ini-bestand.  

-   **LiteTouch.log**. Dit bestand is gemaakt tijdens de LTI-implementaties. Deze bevindt zich in %WINDIR%\TEMP\DeploymentLogs tenzij u opgeeft de **/debug:true** optie.  

-   **Scriptname*.log**. Dit bestand wordt gemaakt door elk script MDT. *Scriptnaam* vertegenwoordigt de naam van het script in kwestie.  

-   **SMSTS.log**. Dit bestand is gemaakt door de Sequencer taak en beschrijft alle Taaksequencer transacties. Afhankelijk van het scenario van implementatie, kan deze zich in % TEMP %, % WINDIR%\System32\ccm\logs of C:\\\_SMSTaskSequence of C:\SMSTSLog.  

-   **Wizard.log**. De wizards implementatie maken en dit bestand bijwerken.  

-   **WPEinit.log**. Dit bestand is gemaakt tijdens het initialisatieproces van Windows PE en is handig voor het oplossen van fouten zijn opgetreden tijdens het starten van Windows PE.  

-   **DeploymentWorkbench_*id*.log**. Dit logboekbestand wordt gemaakt in de map % temp % wanneer u opgeeft **een/Debug** bij het starten van de implementatie-Workbench.  

### <a name="configuration-manager-operating-system-deployment-logs"></a>Logboeken Configuration Manager-besturingssysteem-implementatie  
 Zie voor informatie over welk besturingssysteem implementatie logboekbestanden worden gemaakt door Microsoft System Center 2012 R2 Configuration Manager [technische naslaginformatie voor logboekbestanden in Configuration Manager](http://technet.microsoft.com/library/hh427342.aspx).  

 Wanneer Windows User State Migration Tool (USMT) wordt uitgevoerd, voegt MDT automatisch de opties voor logboekregistratie opslaan van de USMT-logboekbestanden naar de locatie van de MDT-logboekbestanden. De logboekbestanden en wanneer ze zijn gemaakt zijn als volgt:  

-   **USMTEstimate.log**. Gemaakt wanneer het schatten van de USMT-vereisten  

-   **USMTCapture.log**. Gemaakt door de USMT bij het vastleggen van gegevens  

-   **USMTRestore.log**. Gemaakt door de USMT bij het herstellen van gegevens  

 Het script ZeroTouchInstallation.vbs scant automatisch het USMT voortgang van de logboekbestanden voor fouten en waarschuwingen. Het script genereert gebeurtenis-ID 41010 in Microsoft System Center Operations Manager met het volgende overzicht (waarbij *usmt_type* is **schatting**, **SCANSTATE**, of  **LOADSTATE**; *error_count* is het totale aantal fouten gevonden; en *warning_count* is het totale aantal waarschuwingen gevonden):  

```  
ZTI USMT <usmt_type> reported <error_count> errors and <warning_count> warnings  
```  

 Als het aantal fouten groter dan 0 is, wordt deze gebeurtenis een fouttype is. Als het aantal waarschuwingen groter dan 0 zonder fouten is, is een Waarschuwingstype met de gebeurtenis. Anders wordt is de gebeurtenis een informatief type.  

## <a name="identifying-error-codes"></a>Foutcodes identificeren  
Tabel 1 ziet u de foutcodes die de MDT-scripts maken en een beschrijving van elke foutcode. Deze foutcodes worden vastgelegd in het bestand BDD.log.  

### <a name="table-1-error-codes-and-their-description"></a>Tabel 1. Foutcodes en de bijbehorende beschrijvingen  

|**Foutcode**|**Beschrijving**|  
|-|-|  
|5201|Een verbinding met de implementatieshare kan niet worden gemaakt. De implementatie niet worden voortgezet.|  
|5203|Een verbinding met de implementatieshare kan niet worden gemaakt. De implementatie niet worden voortgezet.|  
|5205|Een verbinding met de implementatieshare kan niet worden gemaakt. De implementatie niet worden voortgezet.|  
|5206|De implementatiewizard is geannuleerd of is niet voltooid. De implementatie niet worden voortgezet.|  
|5207|Een verbinding met de implementatieshare kan niet worden gemaakt. De implementatie niet worden voortgezet.|  
|5208|**DeploymentType** is niet ingesteld. Moet een waarde instellen voor **SkipWizard**.|  
|5208|Kan de SMS-Taaksequencer vinden. De implementatie niet worden voortgezet.|  
|5400|-Object maken: **Stel *class_instance* = New *class_name***|  
|5490|MSXML2 maken. DOMDocument.|  
|5495|Create MSXML2.DOMDocument.ParseErr.ErrCode.|  
|5496|LoadControlFile.FindFile: *ConfigFile*|  
|5601|Controleer of de OS-guid: % OSGUID % bestaat.|  
|5602|XML met OSGUID openen: % OSGUID %.|  
|5610|Controleer of bestand.|  
|5630|Controleer of het bestand: *ImagePath*.|  
|5640|Controleer of het bestand: *ImagePath*.|  
|5641|FindFile: ImageX.exe.|  
|5643|BootSect.exe vinden.|  
|5650|Controleer of de map: *Bronpad*.|  
|5651|Controleer of de map: *SourcePath*\Platform.|  
|5652|FindFile: bootsect.exe.|  
|6001|Controleer of de schijf.|  
|6002|Controleer of de schijf.|  
|6010|Test voor TSGUID.|  
|6020|Robocopy waarde geretourneerd: *Waarde*.|  
|6021|Robocopy waarde geretourneerd: *Waarde*.|  
|6101|Controleer voor bestand: *DeployCab*.|  
|6102|Vouw de Sysprep-bestanden uit implementeren. CAB-BESTAND.|  
|6111|Sysprep.exe uitvoeren.|  
|6121|Voer Sysprep uit.|  
|6191|Test voor **CloneTag** in het register om te controleren of Sysprep is voltooid.|  
|6192|Test voor **SystemSetupInProgress** in het register om te controleren of Sysprep is voltooid.|  
|6401|Geautoriseerde DHCP-server.|  
|6501|Computer back-up niet mogelijk, geen netwerkpad (**BackupShare**, **BackupDir**) opgegeven.|  
|6502|FOUT - kan niet worden gevonden van IMAGEX, kan geen back-up.|  
|6601|GetObject (... root/wmi:BCDStore).|  
|6602|BCD. OpenStore (*BCDStore*).|  
|6701|Geconfigureerde beveiligingen.|  
|6702|Opstartbestanden verplaatst.|  
|6703|BDE partitie maken.|  
|6704|Station defragmenteren.|  
|6705|Schijf verkleinen.|  
|6706|Voor meer dan 1 partitie testen.|  
|6707|Opstartbestanden maken.|  
|6708|Versleutelen van de schijf.|  
|6709|Verbinding maken met MicrosoftVolumeEncryption WMI-provider.|  
|6710|Versleutelen van de schijf.|  
|6711|**ProtectKeyWithTPM**.|  
|6712|**ProtectKeyWithTPMAndPIN**.|  
|6713|**ProtectKeyWithTPMAndStartupKey**.|  
|6714|Externe sleutel opslaan in bestand.|  
|6715|Beveiligen met externe sleutel.|  
|6716|Externe sleutel opslaan in bestand.|  
|6717|Sleutel met numerieke wachtwoord te beschermen.|  
|6718|**GetKeyProtectorNumberialP@ssword.**|  
|6718|Wachtwoord opslaan in bestand.|  
|6719|Open *PasswordFile*.|  
|6720|Versleutelen van het station.|  
|6721|Open *DiskPartFile*.|  
|6722|Partitie maken.|  
|6723|Bestaande BDE station worden opgehaald.|  
|6724|Open *DiskPartFile*.|  
|6727|Probeert te openen *DiskPartFile*.|  
|6729|Maak tekstbestand *DiskPartFile*.|  
|6730|Execute **cmd /c DISKPART.EXE /s *DiskPartFile* >> *LogPath*\ZTIMarkActive_diskpart.log 2>&1**|  
|6731|Bcdboot.exe vinden.|  
|6732|Verbinding maken met Microsoft-TPM-provider.|  
|6733|Een TPM-exemplaar in de providerklasse ophalen.|  
|6734|TPM-exemplaar worden opgehaald.|  
|6735|Controleer of de TPM is ingeschakeld.|  
|6736|Controleer of de TPM is geactiveerd.|  
|6737|Controleer als TPM eigendom is.|  
|6738|Controleer of de TPM-eigenaar is toegestaan.|  
|6739|Controleer of de TPM is ingeschakeld.|  
|6740|Controleer of de TPM is geactiveerd.|  
|6741|Controleer als TPM is eigendom en eigendom is toegestaan.|  
|6741|TPM-beheerderswachtwoord instellen|  
|6742|TPM-eigenaar P@ssword ingesteld op **AdminP@ssword**.|  
|6743|TPM-eigenaar instellen P@ssword op waarde.|  
|6744|Controleer of de TPM is ingeschakeld.|  
|6745|Controleer op TPM-eigenaar.|  
|6746|Controle voor goedkeuringssleutelpaar.|  
|6747|Controleer of de TPM is geactiveerd.|  
|6748|Controleer of de TPM-eigenaar is toegestaan.|  
|6749|Converteren van eigenaar p@ssword voor verificatie van de eigenaar.|  
|6750|Goedkeuringssleutelpaar maken.|  
|6751|Verificatie van de eigenaar wijzigen.|  
|6752|Voer **Cmd**.|  
|6753|Valideer de TPM.|  
|6754|BDE instantie ophalen.|  
|6755|Sleutel met TPM te beschermen.|  
|6756|Controleren op verwisselbare media te configureren. **ProtectKeyWithTpmAndStartupKey**.|  
|6757|Sleutel met TPM en opstartsleutel beveiligen.|  
|6758|Zoek naar BDE pincode.|  
|6759|Sleutel met TPM en pincode te beschermen.|  
|6760|Zoeken naar verwisselbare media voor **BDEKeyLocation**.|  
|6761|Beveiligen met externe sleutel.|  
|6762|Herstel P@ssword worden opgeslagen in *PasswordFile*.|  
|6764|BitLocker-beleid configureren.|  
|7000|Kan niet worden gevonden ZTIConfigure.xml; wordt afgebroken.|  
|7001|Zoek naar antwoordbestand voor installatie zonder toezicht.|  
|7100|Fout: dit script moet alleen worden uitgevoerd in het volledige besturingssysteem.|  
|7101|Fout: Er is onvoldoende waarden opgegeven voor genereren DCPromo antwoordbestand.|  
|7102|Fout - verplichte eigenschappen voor het maken van een nieuwe replica van een DC zijn niet opgegeven.|  
|7103|Fout - verplichte eigenschappen voor het maken van een nieuw onderliggend domein zijn niet opgegeven.|  
|7104|Fout - verplichte eigenschappen voor het maken van een nieuw forest zijn niet opgegeven.|  
|7105|Fout - verplichte eigenschappen voor het maken van een nieuw forest zijn niet opgegeven.|  
|7200|Kan geen DHCP-server configureren, omdat de service niet is geïnstalleerd.|  
|7201|Kan niet lezen van de details van de scope; `GetScopeDetails()` is mislukt.|  
|7202|Er is onvoldoende waarden opgegeven voor het maken van het bereik.|  
|7203|Er is onvoldoende die zijn opgegeven voor het instellen van het IP-bereik voor deze scope.|  
|7204|Er is geen waarde opgegeven voor bereik uitgesloten bereik.|  
|7300|Kan geen DNS-opdrachten uitgeven.|  
|7700|Niet een nieuwe Computer scenario; schijfpartitie afgesloten.|  
|7701|Schijf is niet groot genoeg zijn voor systeem- en BDE partities vereist = 1,5 GB.|  
|7702|Schijf is niet groot genoeg zijn voor systeem- en WinRE partities vereist = 10 GB.|  
|7703|DeployRoot is op schijf # *DiskIndex*. OEM-Scenario uitgevoerd: Overslaan.|  
|7704|OEM-Scenario uitgevoerd: Overslaan.|  
|7704|Uitgebreide en logische partities zijn niet toegestaan met BitLocker.|  
|7712|Controleer of station /*Volume station* aanwezig is. de indeling.|  
|7900|FindFile: Microsoft.BDD.PnpEnum.exe.|  
|7901|**AllDrivers.Exists ('*GUID*').**|  
|7904|**AllDrivers.Exists ('*GUID*').**|  
|9200|Findfile(PkgMgr.exe).|  
|9601|Fout - ZTITatoo-statustaak voor het herstel moet worden uitgevoerd in het volledige besturingssysteem; wordt afgebroken.|  
|9701|Niet-nul retourcode van USMT schatting, rc = *fout*.|  
|9702|Gebruikersstatus niet mogelijk; Er is onvoldoende ruimte voor lokale en geen netwerkpad (UDShare, UDDir) opgegeven.|  
|9703|Niet-nul retourcode van USMT vastleggen, rc = *fout*.|  
|9704|Er is geen geldige opdrachtregel-optie is opgegeven.|  
|9801|FOUT - het implementeren van een clientbesturingssysteem op een machine met een serverbesturingssysteem.|  
|9802|Fout: het implementeren van een serverbesturingssysteem met een machine met een clientbesturingssysteem.|  
|9803|Fout - Machine is niet gemachtigd voor het upgraden van (OSInstall =*OSInstall*); wordt afgebroken.|  
|9804|FOUT - *geheugen* MB aan geheugen is onvoldoende. Ten minste *geheugen* MB aan geheugen is vereist.|  
|9805|Fout - Processor sneller van *ProcessorSpeed* MHz is onvoldoende.  Ten minste een *ProcessorSpeed* MHz-processor is vereist.|  
|9806|Fout: Er is onvoldoende ruimte beschikbaar is op *station*. Een extra *grootte* MB is vereist.|  
|9807|Fout: Er is onvoldoende ruimte beschikbaar is op *station*. Een extra *grootte* MB is vereist.|  
|9901|Het script ZTIWindowsUpdate moet niet worden uitgevoerd in Windows PE.|  
|9902|ZTIWindowsUpdate heeft uitgevoerd en is te vaak mislukt. Aantal = *aantal*.|  
|9903|Onverwachte probleem installeren de bijgewerkte versie van Windows Update Agent, rc = *fout*.|  
|9904|Kan object niet maken: **Microsoft.Update.Session**.|  
|9905|Kan object niet maken: **Microsoft.Update.UpdateColl**.|  
|9906|Kritieke bestand *bestand* is niet gevonden; wordt afgebroken.|  
|10000|-Object maken: **Stel oLTICleanup = nieuwe LTICleanup**.|  
|10201|Kan geen lid worden van domein *domein*. De installatie gestopt.|  
|10203|FindFile(LTISuspend.wsf).|  
|10204|Programma uitvoeren *LTISuspend*.|  
|41024|Uitvoeren van ImageX.|  
|52012|Alle parameters van de wizard zijn niet ingesteld.|  

 Aanbieding 1 biedt een fragment uit een logboekbestand dat laat zien hoe de foutcode vinden. In dit fragment is de foutcode gerapporteerd 5001.  

 **Aanbieding 1. Fragment uit een bestand Smsts.log met foutcode 5001**  

```  
.  
.  
.  
The operating system installation failed. Please contact your system administrator for assistance.  

The action "Zero Touch Installation - Validation" failed with exit code 5001  
.  
.  
.  

```  

### <a name="converting-error-codes"></a>Foutcodes converteren  
 Veel foutcodes die zijn gepresenteerd in de logboekbestanden lijken cryptisch en moeilijk te correleren met een werkelijke fout. Echter, is het volgende proces laat zien hoe een foutcode converteren en ophalen van betekenisvolle informatie die bij het oplossen van problemen helpen kan.  

 **Probleem**: Een installatiekopie vast te leggen is mislukt met foutcode 0x80070040.  

 **Mogelijke oplossing 1**: De foutcode die zijn gepresenteerd is hexadecimalen die u nodig hebt om te converteren naar de decimale notatie. Om dit te doen, moet u een wetenschappelijke rekenmachine en de Rekenmachine die deel uitmaakt van Windows-besturingssystemen is zeer geschikt voor deze taak.  

 **Een foutcode converteren**  

1.  Klik op **Start**, en wijs vervolgens **alle programma's**. Wijs **accessoires**, en klik vervolgens op **Rekenmachine**.  

2.  Van de **weergave** menu, klikt u op **wetenschappelijke**.  

3.  Selecteer **Hex**, en voer de laatste vier cijfers van de code: in dit geval **0040**, zoals wordt weergegeven in afbeelding 1.  

     ![TroubleshootingReference1](media/TroubleshootingReference1.jpg "TroubleshootingReference1")  
Afbeelding 1. Fout conversie  

     **Afbeelding 1. Fout conversie**  

     U ziet een nul wilt plaatsen worden niet weergegeven terwijl de Rekenmachine hexadecimale modus wordt.  

4.  Selecteer **december**.  

     De hexadecimale waarde *40* wordt geconverteerd naar een decimale waarde van *64*.  

5.  Open een opdrachtpromptvenster, typ **NET HELPMSG 64**, en druk op ENTER.  

     De **NET HELPMSG** opdracht op zijn beurt de numerieke foutcode zinvolle tekst. In het geval van de hieronder opgegeven foutcode vertaalt naar "de opgegeven naam is niet meer beschikbaar."  

 Deze informatie geeft aan dat een netwerkprobleem zijn kan op de doelcomputer of tussen de doelcomputer en de server waarop de implementatieshare zich bevindt. Deze problemen kunnen netwerkstuurprogramma's niet correct wordt geïnstalleerd of een discrepantie opnemen in de snelheid en duplex-instellingen.  

 **Mogelijke oplossing 2:** Gebruik het hulpprogramma Microsoft Exchange Server fout Code opzoeken. Dit opdrachtregelhulpprogramma is belangrijk te helpen met vertaling fout. Beschikbaar voor het downloaden van de [Microsoft Download Center](http://www.microsoft.com/download/details.aspx?id=985).  

### <a name="review-of-sample-logs"></a>Beoordeling van de voorbeeld-Logboeken  
 MDT logboekbestanden die u gebruiken kunt voor het oplossen van problemen in het implementatieproces MDT gemaakt. De volgende secties bevatten voorbeelden van hoe u de logboekbestanden van MDT gebruiken voor het oplossen van het implementatieproces:  

-   Problemen met betrekking tot fouten toegang tot de MDT-database (MDT DB), zoals beschreven in [toegang tot de Database is mislukt](#FailuretoAccesstheDatabase)  

####  <a name="FailuretoAccesstheDatabase"></a> Toegang tot de Database is mislukt  
 **Probleem:** Een fout optreedt terwijl een CustomSettings.ini-bestand met meerdere secties en geven, met een implementatie die worden gebruikt met de **prioriteit** eigenschap, de prioriteit van elke sectie moet worden verwerkt. BDD.log bevat de volgende foutberichten weergegeven:  

-   ```  
    ERROR - Opening Record Set (Error Number = -2147217911) (Error Description: The SELECT permission was denied on the object 'ComputerAdministrators', database 'AdminDB', schema 'dbo'.)  
    ```  

-   ```  
    ADO error: The SELECT permission was denied on the object 'ComputerAdministrators', database 'AdminDB', schema 'dbo'. (Error #-2147217911; Source: Microsoft OLE DB Provider for SQL Server; SQL State: 42000; NativeError: 229  
    ```  

-   ```  
    ERROR - Unhandled error returned by ZTIGather: Object required (424)  
    ```  

> [!NOTE]
>  Ter verduidelijking, bovenstaande inhoud van het logboekbestand hebt zijn vertegenwoordigd zoals ze worden weergegeven tijdens het wordt weergegeven met het programma Trace32.  

 **Mogelijke oplossing:** Het probleem, is zoals uiteengezet in de eerste regel van het voorbeeldbestand logboek dat de toegang tot de database is geweigerd. Daarom het script kan niet tot stand brengen een beveiligde verbinding met de database, mogelijk omdat een gebruikersnaam en wachtwoord niet beschikbaar waren. Toegang tot de database is als gevolg hiervan geprobeerd met het computeraccount. De eenvoudigste manier om dit probleem omzeilen is iedereen leestoegang tot de database verlenen.  

## <a name="troubleshooting"></a>Probleemoplossing  
 Voordat u\-diepte voor probleemoplossing processen, controleert u de volgende items en zorg ervoor dat de bijbehorende vereisten is voldaan:  

-   Problemen met de installatie kunnen leiden tot als alle vereisten voor software en hardware niet is voldaan.  

### <a name="application-installation"></a>Installatie van de toepassing  
 Controleer de problemen en oplossingen voor problemen met de installatie van de toepassing:  

-   Uit veiligheidsoverwegingen worden geblokkeerd, zoals beschreven in installatiebronbestanden [uitvoerbare bestanden geblokkeerd](#BlockedExecutables)  

-   Verlies van verbinding met het netwerk zoals beschreven in [netwerkverbindingen verbroken](#LostNetworkConnections)  

-   Fout tijdens installatie van 30029 tijdens het installeren van de Microsoft Office 2007 of gerelateerde bestanden, zoals beschreven in [2007 Microsoft Office-systeem](#MicrosoftOfficeSystem)  

####  <a name="BlockedExecutables"></a> Geblokkeerde uitvoerbare bestanden  
 **Probleem:** Als de bronbestanden voor installatie van het Internet worden gedownload, is het waarschijnlijk dat ze worden gemarkeerd met een of meer NTFS-bestand system gegevensstromen. Zie voor meer informatie over NTFS-gegevensstromen [bestand Streams](http://msdn2.microsoft.com/library/aa364404\(VS.85\).aspx). Het bestaan van NTFS-file system-gegevensstromen kan ertoe leiden dat een **geopend bestand – beveiligingswaarschuwing** prompt moet worden weergegeven. De installatie niet worden voortgezet totdat u klikt op **uitvoeren** bij de opdrachtprompt.  

 In afbeelding 2 ziet, vindt u NTFS-bestand system gegevensstromen met behulp van de **meer** opdracht en de [Streams hulpprogramma](http://technet.microsoft.com/sysinternals/bb897440.aspx).  

 ![TroubleshootingReference2](media/TroubleshootingReference2.jpg "TroubleshootingReference2")  
Afbeelding 2. NTFS-gegevensstromen  

 **Afbeelding 2. NTFS-gegevensstromen**  

 **Mogelijke oplossing 1:** Rechts\-klikt u op het installatiebestand van de bron en klik vervolgens op **eigenschappen**. Klik op **blokkering**, en klik vervolgens op **OK** de gegevensstromen van het NTFS-systeem te verwijderen uit het bestand. Herhaal dit proces voor elke installatie bron-bestand dat wordt geblokkeerd door de aanwezigheid van een of meer NTFS-bestand system gegevensstromen.  

 **Mogelijke oplossing 2:** Gebruik het hulpprogramma Streams als REF \_Ref308173670 \\h in afbeelding 2 ziet, te verwijderen van het NTFS-gegevensstromen system bestand uit het bronbestand van de installatie. Het hulpprogramma Streams kunt in één keer NTFS-file system-gegevensstromen van een of meer bestanden of mappen verwijderen.  

####  <a name="LostNetworkConnections"></a> Verbroken netwerkverbindingen  
 **Probleem:** Een installatie kan mislukken als de apparaatstuurprogramma's geïnstalleerd of wordt gewijzigd van apparaat- en netwerkconfiguraties. Deze wijzigingen mogelijk leiden tot een verval in verbinding met het netwerk zorgt ervoor dat de installatie mislukt.  

 **Mogelijke oplossing:** Het script ZTICacheUtil.vbs zodat downloaden en uitvoeren voor de installatie worden geïmplementeerd. Dit script is ontworpen voor het aanpassen van de aankondiging om te schakelen downloaden en uitvoeren. De download gebruikt Background Intelligent Transfer Service \(BITS\) als de Configuration Manager-distributiepunt Web\-op basis van Distributed Authoring en versiebeheer en BITS-functionaliteit. Configuration Manager het script ZTICache.vbs eerst uitgevoerd die zorgt ervoor dat het programma zelf niet worden verwijderd tijdens het implementatieproces wijzigt op hetzelfde moment.  

####  <a name="MicrosoftOfficeSystem"></a> Het 2007 Microsoft Office-systeem  
 **Probleem:** Tijdens het implementeren van het 2007 Office-systeem en een Windows Installer-patch, inclusief \(MSP\) -bestand, de installatie mislukken met foutcode 30029.  

 Verder onderzoek in de ZTIApplications.log ziet u de volgende berichten:  

-   ```  
    About to run command: \\Server\Deployment$\Tools\X86\bddrun.exe \\Server\Share\Microsoft\Office\2007\Professional\setup.exe /adminfile \\Server\Share\Microsoft\Office\2007\Professional\file.msp  
    ```  

-   ```  
    ZTI Heartbeat: command has been running for 12 minutes (process ID 1600) Return code from command = 30029  
    ```  

-   ```  
    Application Microsoft Office 2007 Professional returned an unexpected return code: 30029  
    ```  

 **Mogelijke oplossing 1:** Aan het MSP-bestand te verplaatsen naar de map Updates en voer setup.exe zonder op te geven de  **\/aanpassingspatch** optie. Zie voor meer informatie over het implementeren van updates tijdens de installatie [implementeren van het 2007 Office-systeem](http://technet.microsoft.com/library/cc303395\(v=Office.12\).aspx).  

 **Mogelijke oplossing 2:** Controleer of het MSP-bestand geen de **onderdrukken modale** selectievakje is ingeschakeld. Zie voor meer informatie over het configureren van deze instelling [overzicht van de implementatie van Office 2007](http://technet.microsoft.com/library/bb490141.aspx).  

### <a name="autologon"></a>AutoLogon  
 Controleer de problemen en oplossingen voor problemen met automatische aanmelding:  

-   Onderbreking van de LTI en de Zero Touch installatie \(ZTI\) implementatieprocessen vanwege aanmelding beveiliging banner zoals beschreven in [aanmelding beveiliging banner](#LogonSecutiryBanners)  

-   Onderbreking van de implementatie van LTI en ZTI verwerkt vanwege wordt u gevraagd om gebruikersreferenties, zoals beschreven in [gevraagd om gebruikersreferenties](#PromtedforUserCredentials)  

####  <a name="LogonSecutiryBanners"></a> Aanmelding beveiliging banner  
 **Probleem:** MDT takenreeksen worden verwerkt tijdens een interactieve gebruikerssessie hiervoor is dat de doelcomputer mogen aanmelden automatisch met een opgegeven Administrator-account. Als een groepsbeleidsobject \(GPO\) is aanwezig is die een aanmeldingsscherm van de beveiliging wordt afgedwongen, deze automatische aanmelding niet mag worden voortgezet, omdat de banner van de beveiliging het aanmeldingsproces stopt tijdens het wachten op een gebruiker accepteert van het opgegeven beleid.  

 **Mogelijke oplossing:** Zorg dat het groepsbeleidsobject wordt toegepast op specifieke organisatie-eenheden \(OE's\) en niet opgenomen in de standaarddomein-GPO. Wanneer u computers aan het domein toevoegen, moet u opgeven dat ze worden toegevoegd aan een organisatie-eenheid die wordt niet beïnvloed door een GPO dat u een aanmeldingsscherm van de beveiliging wordt afgedwongen. In de Takenreekseditor bevatten als een van de laatste takenreeksstappen een script dat het computeraccount voor de gewenste organisatie-eenheid verplaatst.  

> [!NOTE]
>  Als u bestaande Active Directory® Domain Services wilt hergebruiken \(AD DS\) accounts, zorg ervoor dat vóór implementatie naar de doelcomputer hebt u de doelcomputer account verplaatst naar een organisatie-eenheid die wordt niet beïnvloed door het groepsbeleidsobject dat wordt afgedwongen het aanmeldingsscherm van beveiliging.  

####  <a name="PromtedforUserCredentials"></a> U wordt gevraagd referenties van een gebruiker  
 **Probleem:** U hebt gemaakt met een installatiekopie van een computer die is gekoppeld aan het domein. Tijdens de implementatie van de nieuwe installatiekopie naar een doelcomputer, de implementatie verwerken stopt, omdat automatische\-aanmelding wordt niet uitgevoerd en de gebruiker wordt gevraagd naar de juiste referenties invoeren. Het implementatieproces hervatten wanneer de referenties zijn opgegeven en de gebruiker is aangemeld.  

 **Mogelijke oplossing:** Bij het vastleggen van installatiekopieën, moet u de broncomputer niet toegevoegd aan een domein. Als de computer is toegevoegd aan een domein, de computer toevoegen aan een werkgroep, re\-vastleggen van de installatiekopie en probeert u de implementatie naar een doelcomputer om te bepalen of het probleem opgelost is.  

### <a name="bios"></a>BIOS  
 **Probleem:** De implementatie mogelijk tijdens de implementatie op een doelcomputer die is uitgerust met Intel vPro-technologie, eindigen met een stop-fout. Hoewel alle bijgewerkte stuurprogramma's zijn opgenomen als uit\-van\-box stuurprogramma's in de Workbench-implementatie, de doelcomputer niet wordt gestart.  

 Mogelijke oplossing: Controleer de instellingen in de doelcomputer basic input\/system uitvoer \(BIOS\) om te bepalen of de standaardmodus Serial Advanced Technology Attachment is geconfigureerd als Advanced Host Controller Interface \( AHCI\). Helaas ondersteunen bepaalde Windows-besturingssystemen geen AHCI standaard.  

### <a name="database-problems"></a>Problemen met de database  
 Bekijk database\-verwante problemen en oplossingen:  

-   Fouten die worden gegenereerd als gevolg van onjuist de firewalls op database-server geconfigureerd zoals beschreven in [aanvragen van SQL Server Browser wordt geblokkeerd](#BlockedSQLServerBrowserRequests)  

-   Fouten die worden gegenereerd als gevolg van verbroken verbindingen met de databaseserver, zoals beschreven in [met de naam van de Pipe-verbindingen](#NamedPipeConnections)  

####  <a name="BlockedSQLServerBrowserRequests"></a> Geblokkeerde SQL Server Browser-aanvragen  
 **Probleem:** Tijdens de implementatie van MDT kunnen gegevens worden opgehaald uit Microsoft SQL Server® databases. Echter, fouten kunnen worden gegenereerd die betrekking op een onjuist geconfigureerde firewall op de databaseserver hebben.  

 **Mogelijke oplossing:** Windows Firewall in Windows Server kunt voorkomen dat onbevoegde toegang tot bronnen van computer. Als de firewall onjuist is geconfigureerd, kunnen u pogingen tot verbinding maken met een SQL Server-exemplaar geblokkeerd. Voor toegang tot een exemplaar van SQL Server die zich achter de firewall moet de firewall te configureren op de computer waarop SQL Server wordt uitgevoerd. Zie voor meer informatie over het configureren van de firewall-poorten voor SQL Server het Microsoft Support-artikel [hoe kan ik de firewallpoort openen voor SQL Server op Windows Server 2008?](http://support.microsoft.com/kb/968872)  

####  <a name="NamedPipeConnections"></a> Named Pipe-verbindingen  
 **Probleem:** Tijdens de implementatie van MDT kan gegevens uit SQL Server-databases worden opgehaald. Echter, fouten kunnen worden gegenereerd die betrekking op SQL Server-verbindingen verbroken hebben. Deze kunnen worden veroorzaakt door het named pipe-verbindingen in Microsoft SQL Server niet in te schakelen.  

 **Mogelijke oplossing:** Deze problemen oplossen, kunt u inschakelen named-pipes in SQL Server. Geef ook de **SQLShare** eigenschap die vereist is bij het maken van een verbinding met een externe database met behulp van named-pipes. Wanneer u verbinding maakt met behulp van named pipes, gebruikt u geïntegreerde beveiliging om de verbinding met de database te maken. In het geval van implementaties van LTI maakt de gebruikersaccount die u opgeeft de verbinding met de database. Voor implementaties van ZTI die gebruikmaken van Configuration Manager, verbindt het netwerktoegangsaccount met de database. Omdat Windows PE geen beveiligingscontext standaard is, moet u een netwerkverbinding met de database-server een beveiligingscontext voor de gebruiker die het maken van de verbinding tot stand brengen.  

 De netwerkshare die de **SQLShare** -eigenschap geeft op biedt een manier om verbinding te maken met de server voor een juiste beveiligingscontext krijgen. U moet beschikken over leestoegang tot de share. Wanneer de verbinding wordt gemaakt, kunt u de named pipe-verbinding met de database vervolgens tot stand brengen. De **SQLShare** eigenschap is niet nodig zijn en mag niet worden gebruikt bij het maken van een TCP\/IP-verbinding met de database.  

 Named pipe-verbindingen inschakelen door het uitvoeren van de volgende taken op basis van de versie van SQL Server die u gebruikt:  

-   Schakel named pipe-verbindingen voor SQL Server 2008 R2, zoals beschreven in [inschakelen met de naam Pipe-verbindingen in SQL Server 2008 R2](#EnableNamedPipeConnectionsinSQLServer).  

-   Schakel named pipe-verbindingen voor SQL Server 2005, zoals beschreven in [inschakelen met de naam Pipe-verbindingen in SQL Server 2005](#EnableNamedPipeConnectionsinSQL).  

#####  <a name="EnableNamedPipeConnectionsinSQLServer"></a> Named Pipe-verbindingen in SQL Server 2008 R2 inschakelen  
 Om in te schakelen named pipe-verbindingen in SQL Server 2008 R2, moet u de volgende stappen uitvoeren:  

1.  Klik op de computer met SQL Server 2008 R2 die als host fungeert voor de database moeten worden opgevraagd op **Start**, en wijs vervolgens **alle programma's**. Wijs **Microsoft SQL Server 2008 R2**, en klik vervolgens op **SQL Server Management Studio**.  

2.  In de **Microsoft SQL Server Management Studio** -console, in de **Object Explorer** rechts\-klikt u op ***sql\_server\_naam***, en klik vervolgens op **eigenschappen** \(waar *sql\_server\_naam* is de naam van de computer met SQL Server worden geconfigureerd\).  

3.  Eigenschappen van de Server \- ***sql\_server\_naam*** in het dialoogvenster wordt weergegeven.  

4.  In de **servereigenschappen** \- ***sql\_server\_naam*** het dialoogvenster **een pagina selecteren**, klikt u op  **Verbindingen**.  

5.  Op de **verbindingen** pagina, controleert u de **externe verbindingen met deze server toestaan** Schakel het selectievakje is ingeschakeld en klik op **OK**.  

6.  Sluit de console van Microsoft SQL Server Management Studio.  

7.  Klik op de computer met SQL Server 2008 R2 die als host fungeert voor de database moeten worden opgevraagd op **Start**, en wijs vervolgens **alle programma's**. Wijs **Microsoft SQL Server 2008 R2**, wijs **configuratiehulpprogramma's**, en klik vervolgens op **SQL Server Configuration Manager**.  

8.  In de **Sql Server Configuration Manager** -console, Ga naar SQL Server Configuration Manager \(lokale\) \/ SQL Server-netwerkconfiguratie \/ protocollen voor  *SQL\_exemplaar* \(waar *sql\_exemplaar* in de naam van de SQL Server-exemplaar moet worden geconfigureerd\).  

9. In het detaildeelvenster rechtermuisknop\-klikt u op **Named Pipes**, en klik vervolgens op **inschakelen**.  

     Het dialoogvenster waarschuwing wordt weergegeven dat aangeeft dat de wijzigingen worden opgeslagen, maar worden pas van kracht nadat de service wordt gestopt en opnieuw opgestart.  

10. In de **waarschuwing** in het dialoogvenster, klikt u op **OK**.  

11. In de **Sql Server Configuration Manager** -console, Ga naar SQL Server Configuration Manager \(lokale\) \/ SQL Server-Services.  

12. In het detaildeelvenster rechtermuisknop\-klikt u op **SQL Server*\(sql\_exemplaar\)***, en klik vervolgens op **opnieuw** \(waar *sql\_exemplaar* in de naam van exemplaar van SQL Server die u hebt geconfigureerd in stap 2\).  

     De SQL Server Configuration Manager-voortgangsbalk weergegeven dat de status toont van de services opnieuw te starten. Nadat de service opnieuw is opgestart, wordt de voortgangsbalk gesloten.  

13. Sluit de SQL Server Configuration Manager-console.  

 Voor meer informatie, [het inschakelen van externe verbindingen in SQL Server 2008](http://blogs.msdn.com/b/walzenbach/archive/2010/04/14/how-to-enable-remote-connections-in-sql-server-2008.aspx).  

#####  <a name="EnableNamedPipeConnectionsinSQL"></a> Named Pipe-verbindingen in SQL Server 2005 inschakelen  
 Om in te schakelen named pipe-verbindingen in SQL Server 2005, moet u de volgende stappen uitvoeren:  

1.  Klik op de computer met SQL Server 2005 die als host fungeert voor de database moeten worden opgevraagd op **Start**, en wijs vervolgens **alle programma's**. Wijs **Microsoft SQL Server 2005**, wijs **configuratiehulpprogramma's**, en klik vervolgens op **SQL Server Surface Area Configuration**.  

2.  In de **SQL Server 2005 Surface Area Configuration** in het dialoogvenster, klikt u op **Surface Area Configuration voor Services en verbindingen**.  

3.  In de **Surface Area Configuration voor Services en verbindingen – *server\_naam***  in het dialoogvenster \(waar *server\_naam*is de naam van de computer met SQL Server 2005\)in **een onderdeel selecteert en configureer vervolgens de services en verbindingen**, gaat u naar MSSQLSERVER\\Database-Engine, en klik vervolgens op  **Externe verbindingen**.  

4.  Klik op **lokale en externe verbindingen**, klikt u op **met beide TCP\/IP en named pipes**, en klik vervolgens op **toepassen**.  

5.  In de **Surface Area Configuration voor Services en verbindingen – *server\_naam***  in het dialoogvenster \(waar *server\_naam*is de naam van de computer met SQL Server 2005\)in **een onderdeel selecteert en configureer vervolgens de services en verbindingen**, gaat u naar MSSQLSERVER\\Database-Engine, en klik vervolgens op  **Service**.  

6.  Klik op **stoppen**.  

     De MSSQLSERVER-service stopt.  

7.  Klik op **Starten**.  

     De MSSQLSERVER-service wordt gestart.  

8.  Klik op **OK**.  

9. SQL Server 2005 Surface Area Configuration te sluiten.  

 Zie voor meer informatie het Microsoft Support-artikel [SQL Server 2005 voor externe verbindingen configureren](http://support.microsoft.com/kb/914277)  

### <a name="deployment-scripts"></a>De Implementatiescripts  
 Bekijk MDT\-verwante problemen en oplossingen:  

-   Gevraagd om de referenties van gebruiker en kan foutbericht 0x80070035 zoals beschreven in [Credentials_script](#Credentials_script)  

-   Foutbericht 'Wuredist.cab niet gevonden' wordt weergegeven zoals beschreven in [ZTIWindowsUpdate](#ZTIWindowsUpdate)  

####  <a name="Credentials_script"></a> Referenties\_script  
 **Probleem:** Tijdens het opstarten van de laatste\-van een geïmplementeerde computer, de gebruiker wordt gevraagd of u gebruikersreferenties moet opgeven en mogelijk fout 0x80070035, waarmee wordt aangegeven dat het netwerkpad niet is gevonden.  

 **Mogelijke oplossing:** Zorg ervoor dat het WIM-bestand bevat geen een MININT of \_SMSTaskSequence map. Het hulpprogramma ImageX koppelen van het WIM-bestand voor het eerst gebruiken deze om mappen te verwijderen, en verwijder vervolgens de mappen.  

> [!NOTE]
>  Als een toegang geweigerd-fout treedt op wanneer u probeert te verwijderen van de mappen uit het WIM-bestand, open een opdrachtpromptvenster, Ga naar de hoofdmap van de afbeelding in het WIM-bestand en voer vervolgens **RD MININT** en **RD \_ SMSTaskSequence**.  

####  <a name="ZTIWindowsUpdate"></a> ZTIWindowsUpdate  
 **Probleem:** Als u het script ZTIWindowsUpdate.wsf gebruiken voor het software-updates toepassen tijdens de implementatie, houd er rekening mee dat dit script kan communiceren rechtstreeks met de website Microsoft Update te downloaden en installeren van de vereiste Windows Update Agent-binaire bestanden, scannen naar toepasselijke software-updates downloaden van de binaire bestanden voor de toepasselijke software-updates en installeer vervolgens de gedownloade binaire bestanden. Dit proces vereist dat uw netwerkinfrastructuur worden geconfigureerd zodat de doelcomputer toegang te krijgen tot de website Microsoft Update.  

 Als de implementatieshare niet de installatiebestanden van Windows Update Agent bevat en de doelcomputer geen juiste toegang tot Internet heeft, wordt de fout 'wuredist.cab niet gevonden' gerapporteerd in de bestanden ZTIWindowsUpdate.log en BDD.log.  

 **Mogelijke oplossing:** Volg de stappen in de sectie 'ZTIWindowsUpdate.wsf' in het document MDT *Toolkit verwijzing*.  

### <a name="deployment-shares"></a>Implementatieshares  
 Controleer de implementatie-share – problemen en oplossingen:  

-   Bijwerken van de WIM bestanden mislukt bij het bijwerken van een share-implementatie, zoals beschreven in [Update WIM-bestanden mislukt](#FailuretoUpdateWIMFiles).  

####  <a name="FailuretoUpdateWIMFiles"></a> Fout bij bijwerken van de WIM-bestanden  
 In een omgeving met 'eenvoudige':  

-   MDT doorgaans neemt over WIMGAPI. DLL-bestand van C:\\Windows\\system32 \(altijd in het pad\). De versie van deze WIMGAPI. DLL-bestand dat moet overeenkomen met de versie \(bouwen\) van het besturingssysteem.  

-   Op een 64\--bits besturingssysteem, MDT gebruikt altijd de x64 WIMGAPI. DLL-bestand. alleen dit bestand moet in het systeem pad. Op een 32\--bits besturingssysteem, MDT gebruikt altijd de x86 WIMGAPI. DLL-bestand. alleen dit bestand moet in het systeem pad. \(Andere producten, zoals Configuration Manager, gebruikt u de 32\-bitsversie van WIMGAPI. DLL-bestand, zelfs op een 64\-bits besturingssysteem, maar ze beheren en installeren die versie.\)  

 **Probleem:** Wanneer u probeert een implementatieshare bijwerken, wordt de gebruiker geïnformeerd dat het koppelen van een of meer WIM-bestanden is mislukt.  

 **Mogelijke oplossing:** Open een opdrachtpromptvenster en voer **waar WIMGAPI. DLL-bestand**. Voor het eerste item in de lijst \(de eerste locatie vinden door te zoeken naar het pad\), zorg ervoor dat de **versie** eigenschap overeenkomt met de build van de Windows Assessment and Deployment Kit \(Windows ADK\) die is geïnstalleerd. Zorg er ook voor dat de eigenschap overeenkomt met het build-nummer van het besturingssysteem.  

### <a name="the-windows-deployment-wizard"></a>De Wizard Windows-implementatie  
 Wizard Windows Deployment gerelateerde problemen en oplossingen bekijken:  

-   Wizard Windows Deployment-pagina's worden weergegeven, zelfs wanneer LTI is geconfigureerd voor het overslaan van de wizardpagina's, zoals beschreven in [Wizard pagina's worden niet overgeslagen](#WizardPagesareNotSkipped).  

####  <a name="WizardPagesareNotSkipped"></a> Wizardpagina's worden niet overgeslagen.  
 **Probleem:** Een pagina van de wizard wordt weergegeven hoewel het MDT DB of CustomSettings.ini-bestand opgeven dat de wizard moet worden overgeslagen.  

 **Mogelijke oplossing:** Als u wilt een wizardpagina goed overslaan, omvatten alle eigenschappen die zouden worden opgegeven op die wizardpagina eventueel in het MDT DB of CustomSettings.ini-bestand samen met de juiste waarden. Als een eigenschap is niet goed geconfigureerd voor een overgeslagen wizardpagina, kunt u deze pagina wordt weergegeven. Zie de sectie 'Bieden eigenschappen voor overgeslagen implementatie wizardpagina's ', in de MDT-document voor meer informatie over welke eigenschappen vereist zijn om ervoor te zorgen dat een wizardpagina is overgeslagen, *Toolkit verwijzing*.  

### <a name="disks-and-partitioning"></a>Schijven en partitioneren  
 Schijf partitionering problemen en oplossingen bekijken:  

-   BitLocker® Drive Encryption problemen zoals beschreven in [BitLocker-stationsversleuteling](#BitLockerDriveEncryption)  

-   Schijf partitioneren fouten, zoals beschreven in de schijf partitioneren fouten  

-   Fouten tijdens Computer vernieuwen implementatiescenario's veroorzaakt door een logische of dynamische schijven, zoals beschreven in [ondersteuning voor logische en dynamische schijven](#SupportforLoogicalandDynamicDisks)  

####  <a name="BitLockerDriveEncryption"></a> BitLocker-stationsversleuteling  
 Implementatie van BitLocker, is een specifieke configuratie vereist voor een juiste implementatie. De volgende potentiële problemen mogelijk te wijten aan de configuratie van de doelcomputer:  

-   In implementaties van ZTI en UDI, ZTIBde.wsf Script mislukt met de fout ' kan niet worden geopend registersleutel ' HKEY\_huidige\_gebruiker\\Configuratiescherm\\International\\LocaleName' om te lezen ', als beschreven in [ZTIBde.wsf Script mislukt met de fout 'Kan niet worden geopend registersleutel 'HKEY_CURRENT_USER\Control Panel\International\LocaleName' om te lezen'](#ZTIBde.wsf).  

-   USB-apparaten, stations CD, DVD-stations of andere verwisselbare media-apparaten op de doelcomputer die worden weergegeven als een station, zoals beschreven in [apparaten weergegeven als een station](#DevicesAppearasMultipleDriveLetters)  

-   Verkleinen van station C op de doelcomputer om voldoende vrije schijfruimte zoals beschreven in [problemen met schijven verkleinen](#ProblemswithShrinkingDisks)  

#####  <a name="ZTIBde.wsf"></a> ZTIBde.wsf Script mislukt met de fout ' kan niet worden geopend registersleutel ' HKEY\_huidige\_gebruiker\\Configuratiescherm\\International\\LocaleName' om te lezen '  
 **Probleem:** Bij het implementeren van BitLocker op de doelcomputer in ZTI of UDI heeft het ZTIBde.wsf script mislukt met de fout ' kan niet worden geopend registersleutel ' HKEY\_huidige\_gebruiker\\Configuratiescherm\\International\\LocaleName' om te lezen. "  

 **Mogelijke oplossing:** Geef de landinstellingen in het **UILanguage** eigenschap. In ZTI en UDI, het ZTIBde.wsf script wordt uitgevoerd in het besturingselement system zodat een volledige gebruikersprofiel is niet geladen. Wanneer het script ZTIBde.wsf probeert te lezen van de landinstellingen-informatie zich niet in het register, omdat het register \(gebruikersprofiel\) is niet volledig geladen. Als tijdelijke oplossing, geef de landinstellingen in het **UILanguage** eigenschap.  

#####  <a name="DevicesAppearasMultipleDriveLetters"></a> Apparaten worden weergegeven als verschillende stationsletters  
 **Probleem:** Sommige apparaten kunnen voorkomen als meerdere logische stationsletter hebben, afhankelijk van hoe ze worden gepartitioneerd. In sommige gevallen kunnen ze worden geëmuleerd een 1,44\-megabyte \(MB\) diskettestation en een opslagschijf geheugen. Windows kan daarom dezelfde apparaat stationsletters A en B voor de diskette-emulatie en F voor de opslagschijf geheugen toewijzen. MDT-scripts gebruiken standaard de laagste stationsletter \(in dit voorbeeld wordt een\).  

 **Mogelijke oplossing:** De standaardinstelling wijzigen op de **opgeven van de BitLocker-herstelgegevens** pagina in de Wizard Windows-implementatie. De Wizard Windows Deployment-overzichtspagina verschijnt een waarschuwing om de gebruiker welke stationsaanduiding is geselecteerd voor het opslaan van BitLocker-herstelgegevens te informeren. De bestanden BDD.log en ZTIBDE.log vastleggen bovendien de verwisselbare media-apparaten gedetecteerd en welk apparaat is geselecteerd om de BitLocker-herstelgegevens opslaan.  

#####  <a name="ProblemswithShrinkingDisks"></a> Problemen met het verkleinen van schijven  
 **Probleem:** Er is onvoldoende vrije schijfruimte bestaat op de doelcomputer BitLocker in te schakelen. Voor het implementeren van BitLocker op een doelcomputer en ten minste 2 GB \(GB\) van niet-toegewezen schijfruimte ruimte is vereist voor het maken van het systeemvolume. De *systeemvolume* is het volume met de hardware\-specifieke bestanden die nodig zijn om Windows te laden nadat de computer is opgestart door het BIOS.  

 **Mogelijke oplossing 1:** Gebruik het hulpprogramma Diskpart op bestaande computers station C verkleinen zodat het systeemvolume kan worden gemaakt. In sommige gevallen, het hulpprogramma Diskpart mogelijk niet voor het verkleinen van station C voldoende om op te geven van 2 GB vrije schijfruimte, mogelijk vanwege gefragmenteerde schijfruimte op station C.  

 Een mogelijke oplossing voor dit probleem is voor het defragmenteren van station C. Voer de volgende stappen uit om dit te doen:  

1.  Voer de Diskpart **querymax verkleinen** opdracht voor het identificeren van de maximale hoeveelheid schijfruimte die niet toegewezen worden kan.  

2.  Als de waarde die werd verkregen in stap 1 minder dan 2 GB is, opschonen van station C van overbodige bestanden en vervolgens te defragmenteren.  

3.  Voer de Diskpart **querymax verkleinen** opdracht opnieuw uit om te controleren of dat meer dan 2 GB aan schijfruimte niet toegewezen worden kan.  

4.  Als de waarde die werd verkregen in stap 3 nog steeds minder dan 2 GB is, voert u een van de volgende taken:  

    -   Defragmenteren van station C meerdere keren om ervoor te zorgen dat het volledig is geoptimaliseerd.  

    -   Back-up van de gegevens op station C, verwijdert u de bestaande partitie, een nieuwe partitie maken en herstellen van de gegevens vervolgens naar de nieuwe partitie.  

 **Mogelijke oplossing 2:** Het script ZTIBDE.wsf wordt uitgevoerd het hulpprogramma voor systeemvoorbereiding schijf \(bdehdcfg.exe\) en system partitiegrootte van het volume tot 2 GB standaard configureert. U kunt het script ZTIBDE.wsf om de standaardinstelling te wijzigen indien nodig. Wijzigen van de MDT-scripts wordt echter niet aanbevolen.  

####  <a name="SupportforLoogicalandDynamicDisks"></a> Ondersteuning voor logische en dynamische schijven  
 **Probleem:** Bij het uitvoeren van een implementatiescenario Computer vernieuwen, mislukt het implementatieproces niet bij implementatie op een doelcomputer die van logische schijven of dynamische schijven gebruikmaakt.  

 **Mogelijke oplossing:** MDT biedt geen ondersteuning voor implementatie van besturingssystemen naar logische stations of dynamische schijven.  

### <a name="domain-join"></a>Aan domein toevoegen  
 **Probleem:** Tijdens de implementatie, kunt u de Wizard Windows-implementatie gebruiken voor alle benodigde gegevens voor de doelcomputer, inclusief referenties, gegevens voor domeindeelname en statische IP-configuratie. Wanneer Setup is voltooid, kunt u zien dat het systeem is niet toegevoegd aan het domein en nog steeds in een werkgroep is.  

 **Mogelijke oplossing:** Een implementatie van de MDT LTI configureert u de statische IP-informatie nadat het besturingssysteem actief is. Als de doelcomputer zich in een netwerksegment waarop geen Dynamic Host Configuration Protocol \(DHCP\), een geautomatiseerde domein dat is opgegeven in Unattend.xml mislukken wanneer er geen DHCP aanwezig is.  

 Configureer Unattend.xml voor een werkgroep. Vervolgens gebruikt u de ingebouwde\-in **herstellen uit domein** stap van de takenreeks een stap in de takenreeks aan het domein na het toepassen van het statische IP-adres toevoegen.  

### <a name="driver-installation"></a>De installatie van stuurprogramma  
 Installatie van de hardware en softwarestuurprogramma moet zodat de best mogelijke gebruikerservaring naadloos met weinig of geen tussenkomst van de gebruiker mogelijk uitgevoerd. Microsoft biedt hulpprogramma's en richtlijnen voor het maken van installatiepakketten die voldoen aan dit doel. Raadpleeg voor algemene informatie over de stuurprogramma-installatiebestand [apparaat en de stuurprogramma-installatiebestand](http://www.microsoft.com/whdc/driver/install/default.mspx).  

 Bekijk installatiefouten: problemen met stuurprogramma's en oplossingen:  

-   Problemen die optreden bij het gebruik van $OEM$ stuurprogramma's voor massaopslag met MDT zoals beschreven in combineren $OEM$ Mass Storage Drivers met MDT Mass Storage logica  

-   Problemen met het apparaat stuurprogramma installatie met behulp van de SetupAPI.log zoals beschreven in [Apparaatinstallatie oplossen met SetupAPI.log](#TroubleshootDeviceInstallationwithSetupAPI.log)  

####  <a name="TroubleshootDeviceInstallationwithSetupAPI.log"></a> Installatie van apparaten met SetupAPI.log oplossen  
 Het witboek [Apparaatinstallatie het oplossen van problemen met het logboekbestand SetupAPI](http://msdn.microsoft.com/windows/hardware/gg463393.aspx) bevat informatie over foutopsporing van de installatie van Windows-apparaten. In het bijzonder biedt het papier richtlijnen voor het stuurprogramma voor ontwikkelaars en testers het logboekbestand SetupAPI interpreteren.  

 Een van de handigste logboekbestanden voor de foutopsporing is het bestand SetupAPI.log. Deze zonder opmaak\-tekstbestand houdt de informatie die SetupAPI records over de installatie van service pack installatie en installatie van de update. Het bestand onderhoudt specifiek, een record van apparaat en het stuurprogramma wijzigingen, evenals wijzigingen in het primaire systeem beginnend vanaf de meest recente Windows-installatie. Dit artikel is gericht op het logboekbestand SetupAPI gebruiken bij het oplossen van de installatie van apparatuur; het logboek secties die zijn gekoppeld met servicepack en update-installaties wordt hier niet beschreven.  

### <a name="new-computer-deployments"></a>Nieuwe Computerimplementaties  
 Bekijk de problemen en oplossingen voor de nieuwe Computer implementatiescenario's:  

-   Problemen met het implementatieproces met behulp van vooraf starten\-opstartomgeving voor uitvoering \(PXE\) starten zoals beschreven in [PXE-opstartbewerking](#PXEBoot)  

####  <a name="PXEBoot"></a> PXE-opstartbewerking  
 In het kort werkt de PXE-protocol als volgt: De clientcomputer start het protocol door het uitzenden van een DHCP-detecteren pakket met een uitbreiding waarmee de aanvraag afkomstig is van een clientcomputer waarop de PXE-protocol is geïmplementeerd. Ervan uitgaande dat een implementatie van deze uitgebreide protocol boot-server beschikbaar is, verzendt de opstartserver een aanbieding met het IP-adres van de server die de service voor de client. Trivial File Transfer Protocol wordt gebruikt voor het downloaden van het uitvoerbare bestand van de opstartserver de client. Ten slotte het gedownloade bootstrap programma wordt uitgevoerd in de clientcomputer.  

 De eerste fase van dit protocol in een subset van de DHCP-berichten zodat de client voor het detecteren van een server voor opstarten piggybacks \(dat wil zeggen, een server die zorgt voor uitvoerbare bestanden voor setup van nieuwe\). De clientcomputer de mogelijkheid om op te halen van een IP-adres mag gebruiken \(dit is verwacht gedrag\) maar is niet vereist om dit te doen.  

 De tweede fase van dit protocol vindt plaats tussen de clientcomputer en een server voor opstarten en de DHCP-berichtindeling als een handige indeling gebruikt voor communicatie. Deze tweede fase is anders geen verband met de standaard DHCP-services. Overzicht van de volgende pagina's de stap\-door\-stap proces tijdens de initialisatie van PXE-client-computer.  

 Voor meer informatie over het oplossen van PXE opstarten\-verwante problemen in Windows Deployment Services in de modus Legacy of Mixed zijn, Zie het Microsoft Support-artikel [beschrijving van PXE interactie tussen PXE-Client, DHCP en RIS-Server ](http://support.microsoft.com/kb/244036).  

 Controleer de volgende oplossingen voor problemen die PXE opstarten:  

-   Windows PE-registratie in SetupAPI.log uitschakelen, zoals beschreven in [Windows PE logboekregistratie uitschakelen in Windows Deployment Services](#DisableWindowsPELogginginWindowsDeploymentServices).  

-   Zorg ervoor dat DHCP is geconfigureerd zoals beschreven in [Zorg ervoor dat de juiste DHCP-configuratie](#EnsuretheProperDHCPConfiguration).  

-   Verbetering van de responstijden voor het IP-adressen toewijzen aan PXE-clientcomputers, zoals beschreven in [verbeteren PXE IP-adres toewijzing reactietijd](#ImprovePXEIPAddressAssignmentResponseTime).  

#####  <a name="DisableWindowsPELogginginWindowsDeploymentServices"></a> Windows PE logboekregistratie in Windows Deployment Services uitschakelen  
 De eerste procedure aanbevolen wordt om ervoor te zorgen dat logboekregistratie naar setupapi.log is uitgeschakeld.  

#####  <a name="EnsuretheProperDHCPConfiguration"></a> Zorg ervoor dat de juiste DHCP-configuratie  
 Afhankelijk van de router-modellen in gebruik, de specifieke routerconfiguratie van uitgezonden DHCP-forwarding mogelijk wordt ondersteund met ofwel een subnet \(of -routerinterface\) of een specifieke host. Als de DHCP-servers en de computer waarop Windows Deployment Services afzonderlijke computers zijn, zorg ervoor dat de routers die door de DHCP-broadcasts zo ontworpen zijn dat de DHCP- en Windows Deployment Services servers de client verzendt ontvangt; anders, ontvangt de clientcomputer geen antwoord op de aanvraag voor opstarten op afstand.  

 Is er een router tussen de clientcomputer en de installatie op afstand-server die niet de DHCP toestaat\-op basis van aanvragen en antwoorden via? Wanneer de clientcomputer Windows Deployment Services en de Windows Deployment Services-server zich op afzonderlijke subnetten, moet u de router tussen de twee systemen voor het doorsturen van DHCP-pakketten naar de Windows Deployment Services-server configureren. Deze regeling is nodig omdat Windows Deployment Services-client-computers een Windows Deployment Services-server detecteren via een DHCP-broadcast-bericht. Zonder DHCP forwarding set up op een router, bereiken de clientcomputers DHCP broadcasts de Windows Deployment Services-server niet. Deze DHCP doorstuurproces wordt soms aangeduid als *DHCP Proxy* of *IP-helperadres* in router configuratie handleidingen. Raadpleeg de documentatie van de router voor meer informatie over het configureren van DHCP-forwarding op een specifieke router.  

#####  <a name="ImprovePXEIPAddressAssignmentResponseTime"></a> De reactietijd van PXE-IP-adres toewijzing verbeteren  
 Controleer de volgende elementen als lang duurt \(15-20 seconden\) voor de PXE-clientcomputer voor het ophalen van een IP-adres:  

-   De netwerkadapter op de doelcomputer en de switch of router die zijn ingesteld op dezelfde snelheid zijn \(automatische, duplex, volledig en enzovoort\)  

-   Is het IP-adres voor de Windows Deployment Services-server in het IP-Help-bestand op de router waarmee de verbinding wordt gemaakt? Als de lijst met IP-adressen in het IP-Help-bestand te lang is, kunt u het adres van de Windows Deployment Services-server aan de bovenkant verplaatsen  

### <a name="restarting-the-deployment-process"></a>Opnieuw opstarten van het implementatieproces  
 **Probleem:** Tijdens het testen en problemen oplossen van een nieuwe of gewijzigde takenreeks, moet u wellicht opnieuw opstarten van de doelcomputer, zodat het implementatieproces opnieuw vanaf het begin beginnen. Onverwachte resultaten optreden omdat MDT blijft de voortgang bijhouden van door het schrijven van gegevens naar de harde schijf; een opnieuw opstarten van de doelcomputer heeft MDT hervatten waar deze was gebleven op het vorige opnieuw opstarten.  

 **Mogelijke oplossing:** Verwijderen zodat het implementatieproces te starten vanaf het begin C:\\MININT en C:\\\_SMSTaskSequence mappen voordat de doelcomputer opnieuw wordt opgestart.  

### <a name="sysprep"></a>Sysprep  
 Bekijk Sysprep\-verwante problemen en oplossingen:  

-   De doelcomputer wordt niet weergegeven in de juiste AD DS organisatie-eenheid, zoals beschreven in [de Computer Account zich in de juiste organisatie-eenheid](#ComputerAccountisintheWrongOU).  

####  <a name="ComputerAccountisintheWrongOU"></a> De computeraccount Is in de juiste organisatie-eenheid  
 **Probleem:** De doelcomputer correct is gekoppeld aan het domein, maar het computeraccount is in de juiste organisatie-eenheid.  

 **Mogelijke oplossing 1:** Als een account vooraf\-bestaat voor de doelcomputer, blijft de account in de oorspronkelijke organisatie-eenheid. Toevoegen als het account naar de opgegeven organisatie-eenheid verplaatsen, een takenreeksstap die gebruikmaakt van een automation-hulpprogramma, zoals een Microsoft Visual Basic® Scripting Edition, verplaatst u het account.  

 **Mogelijke oplossing 2:** Controleer of de opgegeven organisatie-eenheid in de juiste indeling en deze bestaat. De juiste indeling van de organisatie-eenheid moet `OU=Reception,OU=NYC,DC=Woodgrovebank,DC=com`.  

### <a name="configuration-manager"></a>Configuration Manager  
 **Probleem:** Het foutbericht wordt weergegeven in REF \_Ref308174600 \\h afbeelding 3 wordt weergegeven wanneer u probeert te maken van een Configuration Manager PXE-service verwijzen met behulp van de **maken self\-PXE-certificaat heeft ondertekend** optie.  

 ![TroubleshootingReference3](media/TroubleshootingReference3.jpg "TroubleshootingReference3")  
Afbeelding SEQ afbeelding \\ \* ARABIC 3. Fout voor PXE-service-punt  

 **Afbeelding SEQ afbeelding \\ \* ARABIC 3. Fout voor PXE-service-punt**  

 **Mogelijke oplossing:** Als u een PXE-servicepunt eerder op de server die u configureert, het PXE-servicepunt kan niet hebt verwijderd de zelf\-certificaten gemaakt wanneer u het verwijderd. Verwijder de PXE-certificaat-map uit C:\\Documents and Settings\\*gebruiker\_naam*\\toepassingsgegevens\\Microsoft\\Crypto\\RSA, waarbij *gebruiker\_naam* is de naam van de gebruiker die de huidige configuratie wordt uitgevoerd of die de vorige configuratie uitgevoerd. De Wizard Nieuwe Siterol in de Configuration Manager-console voltooid is wanneer u de map hebt verwijderd.  

### <a name="task-sequences"></a>Takenreeksen  
 Controleer de taak reeks gerelateerde problemen en oplossingen:  

-   Takenreeks niet wordt voltooid of onvoorspelbaar gedrag heeft, zoals beschreven in [de taak reeks biedt niet voltooien met succes](#TaskSequenceDoesNotFinishSuccessfully).  

-   Original equipment manufacturer \(OEM\) takenreeksen in LTI, worden vermeld op de opstartinstallatiekopieën met de tegengestelde processorarchitectuur, zoals beschreven in [de OEM taak Sequence ten onrechte wordt weergegeven voor een opstartinstallatiekopie installatiekopie gemaakt voor een Andere processorarchitectuur](#OEMTaskSequenceIncorrectlyAppearsforBootImage).  

-   De Wizard Windows-implementatie wordt het foutbericht ' onjuiste volgorde taakitem \(ongeldige OS-GUID\)' zoals beschreven in [onjuiste taakitem-reeks (ongeldige GUID voor de OS)-bericht in de Wizard Windows Deployment](#BadTaskSequenceItem).  

-   Tijdens het configureren van de naam van een netwerkverbinding, het bericht 'Voer een geldige naam voor de netwerkadapter' wordt weergegeven zoals beschreven in [netwerkinstellingen toepassen](#ApplyNetworkSettings).  

-   Problemen die als gevolg van onjuiste configuratie van optreden kunnen doorgaan bij fout configuratie-instellingen voor takenreeksstappen zoals beschreven in [gebruik Doorgaan bij fout](#UseContinueonError).  

####  <a name="TaskSequenceDoesNotFinishSuccessfully"></a> De Takenreeks niet wordt voltooid  
 **Probleem:** Takenreeks kan niet met succes voltooid of onvoorspelbaar gedrag heeft.  

 **Mogelijke oplossing:** De **besturingssysteem installeren** takenreeksstap \(voor LTI\) of de **Besturingssysteeminstallatiekopie toepassen** takenreeksstap \(voor UDI en ZTI\)mogelijk zijn gewijzigd nadat het maken van de takenreeksstap tot onvoorspelbare resultaten leiden kan. Bijvoorbeeld, als een takenreeks is gemaakt voor het implementeren van een 32\-bit van de installatiekopie van Windows 8.1 en later de **besturingssysteem installeren** takenreeksstap of de **Besturingssysteeminstallatiekopie toepassen** taak stap is gewijzigd om te verwijzen naar een 64\-Windows 8.1-bits installatiekopie en de takenreeks kan niet worden uitgevoerd.  

 Het is raadzaam dat een nieuwe takenreeks is gemaakt voor het implementeren van de installatiekopie van een ander besturingssysteem.  

####  <a name="OEMTaskSequenceIncorrectlyAppearsforBootImage"></a> De OEM-Takenreeks is niet correct wordt weergegeven voor een installatiekopie gemaakt voor een andere processorarchitectuur  
 **Probleem:** Een takenreeks op basis van een sjabloon LTI OEM taak volgorde, wordt weergegeven voor een opstartinstallatiekopie met een andere processorarchitectuur. Bijvoorbeeld, een OEM-takenreeks die een 64 implementeert\-bits besturingssysteem dat wordt weergegeven op een 32\-bits opstartinstallatiekopie.  

 **Mogelijke oplossing:** Dit is verwacht gedrag zoals OEM-takenreeksen in LTI worden niet beschouwd als ' platform\-specifieke ' wordt altijd weergegeven, ongeacht de processorarchitectuur van de opstartinstallatiekopie.  

####  <a name="BadTaskSequenceItem"></a> Ongeldige taak Sequence Item \(ongeldige OS GUID\) bericht in de Wizard Windows-implementatie  
 **Probleem:** Wanneer de Wizard Windows-implementatie wordt uitgevoerd, wordt de wizard het foutbericht ' onjuiste volgorde taakitem \(ongeldige OS GUID\). " Het besturingssysteem wordt weergegeven in het bestand OperatingSystem.xml. het besturingssysteem wordt echter niet weergegeven in de implementatie-Workbench.  

 **Mogelijke oplossing:** Het oorspronkelijke besturingssysteem-bron heeft twee of meer WIM-bestanden die zijn gekoppeld. Een SKU die is gekoppeld aan een takenreeks wordt verwijderd. andere SKU's voor de bron van het besturingssysteem zijn echter nog steeds. Wanneer de takenreeks die verwijst naar de verwijderde SKU is geselecteerd op de **Selecteer een takenreeks uit te voeren op deze computer** wizardpagina in de Wizard Windows-implementatie van het foutbericht ' onjuiste volgorde taakitem \( Ongeldige GUID van het besturingssysteem\)' wordt weergegeven nadat u op **volgende** op de wizardpagina.  

 U lost dit probleem, moet u een van de volgende taken uitvoeren:  

-   Verwijder alle SKU's van de bron van het besturingssysteem. De Wizard Windows Deployment gedraagt zich weer normaal en het foutbericht wordt niet weergegeven.  

-   Wijzig de takenreeks voor het gebruik van de installatiekopie van een ander besturingssysteem.  

####  <a name="ApplyNetworkSettings"></a> Netwerkinstellingen toepassen  
 **Probleem:** Wanneer u de naam van de verbinding configureert in de Workbench-implementatie, vraagt u met een validatiefout opgetreden met het bericht, "Voer een geldige naam voor de netwerkadapter."  

 **Mogelijke oplossing:** Verwijder eventuele spaties en de ongeldige tekens uit de naam opgegeven verbinding.  

####  <a name="UseContinueonError"></a> Gebruik Doorgaan bij fout  
 Als u een takenreeks MDT is geconfigureerd niet als u wilt doorgaan bij fout en de takenreeks een foutmelding, worden alle resterende takenreeksen in die takenreeksgroep overgeslagen. Echter, de resterende takenreeksgroepen worden verwerkt. Neem het volgende in overweging:  

 Twee takenreeksgroepen zijn gemaakt en de groep bevat meer dan één stap in de takenreeks:  

-   -Groep A  

    -   Stap voor stap een  

    -   Stap B  

-   Groep B  

    -   Stap voor stap een  

    -   Stap B  

 Als groep A\\stap voor stap een is ingesteld niet doorgaan bij fout, klikt u vervolgens de groep A\\stap B wordt niet verwerkt. Alle takenreeksstappen in groep B wordt echter verwerkt.  

### <a name="the-user-state-migration-tool"></a>Het hulpprogramma voor migratie van gebruikersstatus  
 Bekijk USMT\-verwante problemen en oplossingen:  

-   Snelkoppelingen die naar documenten die zijn opgeslagen in gedeelde netwerkmappen verwijzen niet goed zoals beschreven in hersteld [bureaubladpictogrammen ontbreekt](#MissingDesktopShortcuts).  

####  <a name="MissingDesktopShortcuts"></a> Ontbrekende snelkoppelingen op het bureaublad  
 **Probleem:** Tijdens het gebruik van USMT om gebruikersgegevens te migreren, kunnen snelkoppelingen die naar de netwerk-documenten verwijzen niet te worden teruggezet. De snelkoppelingen zijn vastgelegd tijdens Scanstate; maar worden ze nooit teruggezet naar de doelcomputer tijdens Loadstate.  

 **Mogelijke oplossing:** Bewerk de MigUser.xml bestands- en uitcommentarieer de volgende regel:  

 Origineel:  

```  
<include> filter='MigXmlHelper.IgnoreIrrelevantLinks()'>  
```  

 Gewijzigd:  

```  
<include> <!-- filter='MigXmlHelper.IgnoreIrrelevantLinks()'> -->  
```  

### <a name="windows-imaging-format-files"></a>Windows Imaging Format-bestanden  
 Bekijk WIM\-verwante problemen en oplossingen:  

-   Implementaties van LTI en ZTI mislukken met WIM-bestandsfouten in het bestand BDD.log zoals beschreven in [WIM-bestand beschadigd](#CorruptWIMFile).  

####  <a name="CorruptWIMFile"></a> WIM-bestand beschadigd  
 **Probleem:** Bij het implementeren van een installatiekopie, mislukt de implementatie met de volgende vermeldingen in het bestand BDD.log:  

-   ```  
    The image \\Server\Deployment$\Operating Systems\Windows\version1.wim was not applied successfully by ImageX, rc = 2  
    ```  

-   ```  
    LTIApply COMPLETED.  Return Value = 2  
    ```  

-   ```  
    ZTI ERROR - Non-zero return code by LTIApply, rc = 2  
    ```  

 Onderzoek het probleem door het koppelen van het WIM-bestand met behulp van ImageX resultaten in de fout 'de gegevens is ongeldig." Verder onderzoek blijkt dat de datumstempel van het WIM-bestand jaren vóór de huidige datum is. Het is mogelijk dat een ander proces, zoals een virusscan is die het WIM-bestand openen nadat deze eerder aan het einde van een proces lees- of schrijfbewerking is gesloten.  

 **Mogelijke oplossing:** Het WIM-bestand terugzetten vanaf back-upmedium.  

### <a name="windows-pe"></a>Windows PE  
 Windows PE gerelateerde problemen en oplossingen bekijken:  

-   Het implementatieproces LTI of ZTI wordt niet gestart vanwege onvoldoende RAM of adapters voor draadloze netwerken, zoals beschreven in [implementatie proces is niet gestart: beperkte RAM of draadloze netwerkadapter](#LimitedRamorWirelessNetworkAdapter).  

-   Het implementatieproces LTI of ZTI is niet gestart vanwege het ontbreken van Windows PE-onderdelen, zoals beschreven in [implementatie proces is niet gestart: onderdelen ontbreekt](#MissingComponents).  

-   Het implementatieproces LTI of ZTI is niet gestart vanwege ontbrekende of onjuiste apparaatstuurprogramma's, zoals beschreven in [implementatie proces is niet gestart: ontbrekende of onjuiste stuurprogramma's](#MissingorIncorrectDrivers).  

####  <a name="LimitedRamorWirelessNetworkAdapter"></a> Implementatieproces niet gestart: beperkte RAM of draadloze netwerkadapter  
 **Probleem:** Bij het implementeren van een afbeelding met bepaalde doelcomputers, Windows PE wordt gestart, wordt uitgevoerd **wpeinit**, opent u een opdrachtpromptvenster, maar het implementatieproces niet daadwerkelijk wordt gestart. Het oplossen van problemen door een netwerkstation van de doelcomputer toe te wijzen, geeft de stuurprogramma's voor netwerkadapters zijn niet geladen.  

 **Mogelijke oplossing 1:**de implementatiewizard niet wordt gestart, omdat er onvoldoende RAM-geheugen. Controleren of de doelcomputer ten minste 512 MB RAM-geheugen en dat er geen gedeelde videogeheugen meer dan 64 MB 512 MB in beslag neemt.  

 De versies van Windows PE die ondersteuning biedt voor MDT kunnen niet worden uitgevoerd op een doelcomputer die kleiner zijn dan 512 MB RAM-geheugen heeft.  

 **Mogelijke oplossing 2:** De draadloze stuurprogramma's niet opnemen in de Windows PE-installatiekopie.  

####  <a name="MissingComponents"></a> Implementatieproces niet gestart: ontbrekende onderdelen  
 **Probleem:** Wanneer u problemen met een mislukte implementatie, bevat een overzicht van het bestand BDD.log de volgende vermelding:  

```  
ERROR - Unable to create ADODB.Connection object, impossible to query SQL Server: ActiveX component can't create object (429).  
```  

 **Mogelijke oplossing:** Deze fout kan wijzen dat de Windows PE-installatiekopie is niet gemaakt met MDT. Als u Configuration Manager gebruikt, gebruik niet een van de bestaande Windows PE-installatiekopieën die Configuration Manager is gemaakt. Maak in plaats daarvan een installatiekopie met de Microsoft-implementatiewizard Takenreeks importeren.  

> [!NOTE]
>  De Windows PE-installatiekopieën die Configuration Manager maakt bevatten onderdelen die ondersteuning bieden voor scripts, XML- en Windows Management Instrumentation (WMI), maar ze bevatten geen onderdelen die ondersteuning bieden voor Microsoft ActiveX® Data Objects (ADO).  

####  <a name="MissingorIncorrectDrivers"></a> Implementatieproces niet gestart: ontbrekende of onjuiste stuurprogramma's  
 **Probleem:** Bij het implementeren van bepaalde doelcomputers, Windows PE wordt gestart, wordt uitgevoerd **wpeinit**, opent u een opdrachtpromptvenster, maar het implementatieproces niet daadwerkelijk wordt gestart. Het oplossen van problemen door een netwerkstation van de doelcomputer toe te wijzen, geeft de stuurprogramma's voor netwerkadapters zijn niet geladen. Een overzicht van het bestand SetupAPI.log in *X*: \Windows\System32\Inf geeft aan dat de Windows PE fouten genereert wanneer dit is de netwerkadapter, waarvan er één is, het configureren van 'dit stuurprogramma is niet bedoeld voor dit platform." De stuurprogramma's in de **Out-of-Box stuurprogramma's** lijst zijn in de afbeelding is ingevoegd.  

 **Mogelijke oplossing:** Het is mogelijk dat Windows PE een conflict stuurprogramma met een ander stuurprogramma heeft. Bij het configureren van de instellingen voor de Windows PE-installatiekopie in de Workbench-implementatie, maakt u een groep voor het stuurprogramma's van Windows PE met alleen-netwerkadapter en stuurprogramma's voor opslag en configureer vervolgens de implementatieshare voor het gebruik van alleen de groep in de Windows PE-stuurprogramma.  

## <a name="deployment-process-flow-charts"></a>Stroomdiagrammen voor implementatie-proces  
 Deze sectie bevat twee sets met stroomdiagrammen MDT: één voor implementaties van LTI en één voor implementaties van ZTI met Configuration Manager. Elke stroomdiagram ziet u de taken die worden uitgevoerd tijdens het implementatietype.  

 Maak uzelf bekend met de implementatie proces stroomdiagrammen door:  

-   De LTI implementatie proces stroomdiagrammen bekijken, zoals beschreven in [LTI implementatie proces stroomdiagrammen](#LTIDeploymentProcessFlowcharts)  

-   De stroomdiagrammen ZTI implementatie proces controleren, zoals beschreven in [ZTI implementatie proces stroomdiagrammen](#ZTIDevelopmentProcessFlowcharts)  

###  <a name="LTIDeploymentProcessFlowcharts"></a> LTI implementatie proces stroomdiagrammen  
 Stroomdiagrammen zijn beschikbaar voor de volgende fasen:  

-   Validatie (afbeelding 4)  

-   Status vastleggen (afbeelding 5 en afbeelding 6)  

-   Preinstall (afbeelding 7, afbeelding 8 en afbeelding 9)  

-   Installeren (afbeelding 10)  

-   Postinstall (afbeelding 11 en afbeelding 12)  

-   Status herstellen (afbeelding 14 afbeelding 13 afbeelding 15 en afbeelding 16)  

 ![TroubleshootingReference4](media/TroubleshootingReference4.jpg "TroubleshootingReference4")  
Afbeelding 4: Stroomdiagram voor de Validatiefase  

 **Afbeelding 4. Stroomdiagram voor de Validatiefase**  

 ![TroubleshootingReference5](media/TroubleshootingReference5.jpg "TroubleshootingReference5")  
Afbeelding 5. Stroomdiagram voor de status vastleggen fase (1 van 2)  

 **Afbeelding 5. Stroomdiagram voor de status vastleggen fase (1 van 2)**  

 ![TroubleshootingReference6](media/TroubleshootingReference6.jpg "TroubleshootingReference6")  
Afbeelding 6. Stroomdiagram voor de status vastleggen fase (2 van 2)  

 **Afbeelding 6. Stroomdiagram voor de status vastleggen fase (2 van 2)**  

 ![TroubleshootingReference7](media/TroubleshootingReference7.jpg "TroubleshootingReference7")  
Afbeelding 7. Stroomdiagram voor de fase Preinstall (1 van 3)  

 **Afbeelding 7. Stroomdiagram voor de fase Preinstall (1 van 3)**  

 ![TroubleshootingReference8](media/TroubleshootingReference8.jpg "TroubleshootingReference8")  
Afbeelding 8. Stroomdiagram voor de fase Preinstall (2 van 3)  

 **Afbeelding 8. Stroomdiagram voor de fase Preinstall (2 van 3)**  

 ![TroubleshootingReference9](media/TroubleshootingReference9.jpg "TroubleshootingReference9")  
Afbeelding 9. Stroomdiagram voor de fase Preinstall (3 van 3)  

 **Afbeelding 9. Stroomdiagram voor de fase Preinstall (3 van 3)**  

 ![TroubleshootingReference10](media/TroubleshootingReference10.jpg "TroubleshootingReference10")  
Afbeelding 10. Stroomdiagram voor de fase installeren  

 **Afbeelding 10. Stroomdiagram voor de fase installeren**  

 ![TroubleshootingReference11](media/TroubleshootingReference11.jpg "TroubleshootingReference11")  
Afbeelding 11. Stroomdiagram voor de fase Postinstall (1 van 2)  

 **Afbeelding 11. Stroomdiagram voor de fase Postinstall (1 van 2)**  

 ![TroubleshootingReference12](media/TroubleshootingReference12.jpg "TroubleshootingReference12")  
Afbeelding 12 stroomdiagram voor de fase Postinstall (2 van 2)  

 **Afbeelding 12 stroomdiagram voor de fase Postinstall (2 van 2)**  

 ![TroubleshootingReference13](media/TroubleshootingReference13.jpg "TroubleshootingReference13")  
Afbeelding 13. Stroomdiagram voor de staat herstellen fase (1-4)  

 **Afbeelding 13. Stroomdiagram voor de staat herstellen fase (1-4)**  

 ![TroubleshootingReference14](media/TroubleshootingReference14.jpg "TroubleshootingReference14")  
Afbeelding 14. Stroomdiagram voor de staat herstellen fase (2 van 4)  

 **Afbeelding 14. Stroomdiagram voor de staat herstellen fase (2 van 4)**  

 ![TroubleshootingReference15](media/TroubleshootingReference15.jpg "TroubleshootingReference15")  
Afbeelding 15. Stroomdiagram voor de staat herstellen fase (3 van 4)  

 **Afbeelding 15. Stroomdiagram voor de staat herstellen fase (3 van 4)**  

 ![TroubleshootingReference16](media/TroubleshootingReference16.jpg "TroubleshootingReference16")  
Afbeelding 16. Stroomdiagram voor de staat herstellen fase (4 van 4)  

 **Afbeelding 16. Stroomdiagram voor de staat herstellen fase (4 van 4)**  

###  <a name="ZTIDevelopmentProcessFlowcharts"></a> ZTI implementatie proces stroomdiagrammen  
 Stroomdiagrammen zijn beschikbaar voor de volgende fasen van ZTI implementatie met Configuration Manager:  

-   Initialisatie (figuur 17)  

-   Validatie (figuur 18)  

-   Status vastleggen (figuur 19)  

-   Preinstall (afbeelding 20)  

-   (Afbeelding 21) installeren  

-   Postinstall (figuur 22)  

-   Status herstellen (figuur 23 en figuur 24)  

-   Vastleggen (afbeelding 25)  

 ![TroubleshootingReference17](media/TroubleshootingReference17.jpg "TroubleshootingReference17")  
Afbeelding 17. Stroomdiagram voor de initialisatiefase  

 **Afbeelding 17. Stroomdiagram voor de initialisatiefase**  

 ![TroubleshootingReference18](media/TroubleshootingReference18.jpg "TroubleshootingReference18")  
Afbeelding 18. Stroomdiagram voor de Validatiefase  

 **Afbeelding 18. Stroomdiagram voor de Validatiefase**  

 ![TroubleshootingReference19](media/TroubleshootingReference19.jpg "TroubleshootingReference19")  
Afbeelding 19. Stroomdiagram voor de fase voor het vastleggen van status  

 **Afbeelding 19. Stroomdiagram voor de fase voor het vastleggen van status**  

 ![TroubleshootingReference20](media/TroubleshootingReference20.jpg "TroubleshootingReference20")  
Afbeelding 20. Stroomdiagram voor de fase Preinstall  

 **Afbeelding 20. Stroomdiagram voor de fase Preinstall**  

 ![TroubleshootingReference21](media/TroubleshootingReference21.jpg "TroubleshootingReference21")  
Afbeelding 21. Stroomdiagram voor de fase installeren  

 **Afbeelding 21. Stroomdiagram voor de fase installeren**  

 ![TroubleshootingReference22](media/TroubleshootingReference22.jpg "TroubleshootingReference22")  
Afbeelding 22. Stroomdiagram voor de fase Postinstall  

 **Afbeelding 22. Stroomdiagram voor de fase Postinstall**  

 ![TroubleshootingReference23](media/TroubleshootingReference23.jpg "TroubleshootingReference23")  
Afbeelding 23. Stroomdiagram voor de staat herstellen fase (1 van 2)  

 **Afbeelding 23. Stroomdiagram voor de staat herstellen fase (1 van 2)**  

 ![TroubleshootingReference24](media/TroubleshootingReference24.jpg "TroubleshootingReference24")  
Afbeelding 24. Stroomdiagram voor de staat herstellen fase (2 van 2)  

 **Afbeelding 24. Stroomdiagram voor de staat herstellen fase (2 van 2)**  

 ![TroubleshootingReference25](media/TroubleshootingReference25.jpg "TroubleshootingReference25")  
Afbeelding 25. Stroomdiagram voor de fase voor het vastleggen  

 **Afbeelding 25. Stroomdiagram voor de fase voor het vastleggen**  

## <a name="finding-additional-help"></a>Aanvullende hulp zoeken  
 Extra hulp bij het oplossen van problemen met MDT-implementatie door te zoeken:  

-   Contact opnemen met Microsoft Support zoals beschreven in [Microsoft Support](#MicrosoftSupport)  

-   Het verkrijgen van aanvullende ondersteuning via blogs en andere internetbronnen, zoals beschreven in [ondersteuning voor Internet](#InternetSupport)  

###  <a name="MicrosoftSupport"></a> Microsoft-ondersteuning  
 Microsoft biedt Premier- of Professional-ondersteuning voor Microsoft Deployment Toolkit.  

 Professional-ondersteuning: [http://support.microsoft.com/](http://support.microsoft.com/)  

 Premier-ondersteuning: [https://premier.microsoft.com/](https://premier.microsoft.com/)  

> [!NOTE]
>  Wanneer u contact op met ondersteuning, worden het probleem is met MDT en de specifieke versie.  

###  <a name="InternetSupport"></a> Ondersteuning voor Internet  
 Veel online bronnen voor probleemoplossing assistentie voor MDT afgezien van wat wordt beschreven in deze verwijzing te voorzien. Deze bronnen online zijn onder andere:  

-   Blogs van Microsoft worden gehost  

    -   [MDT-teamblog](http://blogs.technet.com/b/msdeployment/)  

    -   [Configuration Manager-teamblog](http://blogs.technet.com/b/configmgrteam/)  

    -   [Blog van Michael Niehaus'](http://blogs.technet.com/b/mniehaus/) (Michael Niehaus schrijft op Windows en Microsoft Office-implementatie).  

-   Microsoft gehoste nieuwsgroepen en forums:  

     De volgende nieuwsgroepen en forums zijn beschikbaar met de ondersteuning van Microsoft-werknemers, bedrijfstak peers en gewaardeerd medewerkers van Microsoft:  

    -   [Configuration Manager - implementatie van het besturingssysteem](http://social.technet.microsoft.com/Forums/home?forum=configmanagerosd)  

    -   [Windows 8-installatie, installatie en implementatie](http://social.technet.microsoft.com/Forums/windows/home?forum=w8itproinstall)  

-   De informatiebronnen met betrekking tot implementatie van externe Microsoft:  

    -   [DeployVista.com](http://www.deployvista.com/)  

    -   [myITforum.com](http://www.myitforum.com/)
