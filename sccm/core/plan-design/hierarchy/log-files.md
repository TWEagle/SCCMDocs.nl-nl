---
title: Logboekbestanden voor Configuration Manager | Microsoft-documenten
description: "Logboekbestanden gebruiken voor het oplossen van problemen in een System Center Configuration Manager-hiërarchie."
ms.custom: na
ms.date: 3/28/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: c1ff371e-b0ad-4048-aeda-02a9ff08889e
caps.latest.revision: 9
caps.handback.revision: 0
author: Brenduns
ms.author: brenduns
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: dab5da5a4b5dfb3606a8a6bd0c70a0b21923fff9
ms.openlocfilehash: b991b4ea27e66c233b04f8e65a412404521d89a6
ms.contentlocale: nl-nl
ms.lasthandoff: 05/17/2017


---
# <a name="log-files-in-system-center-configuration-manager"></a>Logbestanden in System Center Configuration Manager

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*

In System Center Configuration Manager-client en site siteserveronderdelen procesinformatie in afzonderlijke logboekbestanden. Gebruik de informatie in de logboekbestanden kan u helpen bij het oplossen van problemen die in uw Configuration Manager-hiërarchie optreden kunnen. Standaard is logboekregistratie voor client- en serveronderdelen ingeschakeld in Configuration Manager.   

 De volgende secties vindt informatie over de verschillende logboekbestanden beschikbaar voor u. U kunt deze informatie te raadplegen en te bewaken Configuration Manager-client en server-logboeken inzake operationele details en om te identificeren fout informatie die u kan helpen oplossen van problemen.  

-   [Logboekbestanden over Configuration Manager](#BKMK_AboutLogs)  

    -   [Opties voor logboekregistratie configureren met behulp van Configuration Manager-servicebeheer](#BKMK_LogOptions)  

    -   [Zoeken naar Logboeken Configuration Manager](#BKMK_LogLocation)  

-   [Logboeken Configuration Manager-client](#BKMK_ClientLogs)  

    -   [Clientbewerkingen](#BKMK_ClientOpLogs)  

    -   [Logboekbestanden van client-installatie](#BKMK_ClientInstallLog)  

    -   [Client voor Linux en UNIX](#BKMK_LogFilesforLnU)  

    -   [Client voor Mac-computers](#BKMK_LogfilesforMac)  

-   [Configuration Manager site server-logboekbestanden](#BKMK_ServerLogs)  

    -   [Server en de site siteserversystemen](#BKMK_SiteSiteServerLog)  

    -   [Logboekbestanden van siteserverinstallatie site](#BKMK_SiteInstallLog)  

    -   [Logboekbestanden voor terugvalstatuspunt-punt](#BKMK_FSPLog)  

    -   [Management-punt-logboekbestanden](#BKMK_MPLog)  

    -   [Logboekbestanden voor software-update-punt](#BKMK_SUPLog)  

-   [Logboekbestanden voor Configuration Manager-functionaliteit](#BKMK_FunctionLogs)  

    -   [Toepassingsbeheer](#BKMK_AppManageLog)  

    -   [Asset intelligence](#BKMK_AILog)  

    -   [Back-up en herstel](#BKMK_BnRLog)  

    -   [Certificaatinschrijving](#BKMK_CertificateEnrollment)

    -   [Clientmeldingen](#BKMK_BGB)

    -   [Cloud management gateway](#cloud-management-gateway)

    -   [Compatibiliteitsinstellingen en toegang tot bedrijfsbronnen](#BKMK_CompSettingsLog)  

    -   [Configuration Manager-console](#BKMK_ConsoleLog)  

    -   [Inhoudsbeheer](#BKMK_ContentLog)  

    -   [Detectie](#BKMK_DiscoveryLog)  

    -   [Endpoint Protection](#BKMK_EPLog)  

    -   [Uitbreidingen](#BKMK_Extensions)  

    -   [Inventarisatie](#BKMK_InventoryLog)  

    -   [Softwarelicentiecontrole](#BKMK_MeteringLog)  

    -   [Migratie](#BKMK_MigrationLog)  

    -   [Mobiele apparaten](#BKMK_MDMLog)  

    -   [Implementatie van besturingssysteem](#BKMK_OSDLog)  

    -   [Energiebeheer](#BKMK_PowerMgmtLog)  

    -   [Beheer op afstand](#BKMK_RCLog)  

    -   [Rapportage](#BKMK_ReportLog)  

    -   [Op rollen gebaseerd beheer](#BKMK_RBALog)  

    -   [Het service connection point](#BKMK_WITLog)  

    -   [Software-updates](#BKMK_SU_NAPLog)  

    -   [Wake On LAN](#BKMK_WOLLog)  

    -   [Onderhoud van Windows 10](#BKMK_WindowsServicingLog)

    -   [Windows Update Agent](#BKMK_WULog)  

    -   [WSUS-server](#BKMK_WSUSLog)  

##  <a name="BKMK_AboutLogs"></a>Logboekbestanden over Configuration Manager  
 De meeste processen in Configuration Manager schrijven operationele gegevens naar een logboekbestand dat is aan dat proces toegewezen. De logboekbestanden worden aangegeven met **.log** of **.lo_** bestandsextensies. Configuration Manager schrijft naar een .log-bestand totdat het logboek zijn maximum grootte bereikt. Wanneer het logboek vol is, wordt het .log-bestand wordt gekopieerd naar een bestand met dezelfde naam, maar met de .lo_-extensie en het proces of het onderdeel wordt nu geschreven naar het .log-bestand. Wanneer het .log-bestand opnieuw zijn maximum grootte bereikt, wordt het .log-bestand overschreven en het proces wordt herhaald. Sommige onderdelen leggen een door een datum en een tijdstempel aan de naam van het logboekbestand toe te voegen en door de .log-extensie te behouden. Een uitzondering op de maximale grootte en het gebruik van het .log-bestand is de client voor Linux en UNIX. Zie voor informatie over hoe de client voor Linux en UNIX logboekbestanden gebruikt, [logboekbestanden in de client voor Linux en UNIX beheren](#BKMK_ManageLinuxLogs) in dit onderwerp.  

 Gebruik de Configuration Manager hulpprogramma voor logboekweergave CMTrace, zich in de om Logboeken te raadplegen, de \\SMSSetup\\map hulpprogramma's van de Configuration Manager-bronmedia. Het CMTrace, hulpprogramma wordt toegevoegd aan alle opstartinstallatiekopieën die zijn toegevoegd aan de softwarebibliotheek.  

###  <a name="BKMK_LogOptions"></a>Opties voor logboekregistratie configureren met behulp van Configuration Manager-servicebeheer  
 In Configuration Manager, die u kunt wijzigen waar logboekbestanden worden opgeslagen en u kunt de logboekgrootte wijzigen.  

 Als u wilt wijzigen van de grootte van logboekbestanden, de naam en locatie van het logboekbestand wijzigen of om meerdere onderdelen om te schrijven naar één enkel logboekbestand te dwingen, komen de volgende stappen uit.  

#### <a name="to-modify-logging-for-a-component"></a>Logboekregistratie voor een onderdeel wijzigen  

1.  Selecteer in de Configuration Manager-console **bewaking**, selecteer **systeemstatus**, en selecteer vervolgens **Sitestatus** of **Onderdeelstatus**.  
2.  Op de **Start** tabblad, in de **onderdeel** selecteren groep **Start**, en selecteer vervolgens **Configuration Manager-servicebeheer**.  
3.  Als Configuration Manager-servicebeheer wordt geopend, verbinding maken met de site die u wilt beheren. Als de site die u wilt beheren niet weergegeven, selecteer **Site**, selecteer **Connect**, en voer de naam van de siteserver voor de juiste site.  
4.  Vouw de site en Ga naar **onderdelen** of **Servers**, afhankelijk van waar de onderdelen die u wilt beheren zich bevinden.  
5.  Selecteer één of meer onderdelen in het rechterpaneel.  
6.  Op de **onderdeel** selecteert u **logboekregistratie**.  
7.  Voltooi in het dialoogvenster **Logboekregistratie Configuration Manager-onderdeel** de beschikbare configuratieopties voor uw selectie.  
8.  Selecteer **OK** aan de configuratie op te slaan.  

###  <a name="BKMK_LogLocation"></a>Zoeken naar Logboeken Configuration Manager  
Configuration Manager-logboekbestanden worden opgeslagen in verschillende plaatsen die afhangen van het proces dat het logboekbestand maakt en op de configuratie van uw sitesystemen. Omdat de locatie van het logboek op een computer verschillen kan, gebruikt u de zoekfunctie zoeken naar de relevante logboekbestanden op uw Configuration Manager-computers als u moet een specifiek scenario oplossen.  

##  <a name="BKMK_ClientLogs"></a>Logboeken Configuration Manager-client  
De volgende gedeelten worden de logboekbestanden gerelateerd aan clientbewerkingen en clientinstallatie.  

###  <a name="BKMK_ClientOpLogs"></a>Clientbewerkingen  
De volgende tabel bevat de logboekbestanden die zich op de Configuration Manager-client.  

|Logboeknaam|Beschrijving|  
|--------------|-----------------|  
|CAS.log|De inhoud Access-service. Behoudt de cache van het lokale pakket op de client.|  
|Ccm32BitLauncher.log|Registreert acties voor het starten van toepassingen op de client, gemarkeerd met "uitgevoerd als 32-bits".|  
|CcmEval.log|Registreert Configuration Manager client activiteiten voor de evaluatie en details voor onderdelen die voor de Configuration Manager-client vereist zijn.|  
|CcmEvalTask.log|Registreert de Configuration Manager client activiteiten voor de evaluatie die geïnitieerd zijn door de geplande taak voor evaluatie.|  
|CcmExec.log|Registreert activiteiten van de client en de SMS Agent Host-service. Dit logboekbestand bevat informatie over het in- en uitschakelen van wake-up proxy.|  
|CcmMessaging.log|Registreert activiteiten met betrekking tot communicatie tussen de client en beheerpunten.|  
|CCMNotificationAgent.log|Registreert activiteiten die betrekking hebben op de bewerkingen van clientmelding.|  
|Ccmperf.log|Registreert activiteiten die betrekking hebben op het onderhoud en vastleggen van gegeven met betrekking tot clientprestatietellers.|  
|CcmRestart.log|Registreert herstartactiviteit van de client-service.|  
|CCMSDKProvider.log|Registreert activiteiten voor de client SDK-interfaces.|  
|CertificateMaintenance.log|Onderhoudt certificaten voor Active Directory Domain Services en beheerpunten.|  
|CIDownloader.log|Registreert details over downloads van configuratie-itemdefinitie.|  
|CITaskMgr.log|Registreert taken die geïnitieerd worden voor elk toepassings- en implementatietype, zoals inhoud downloaden en installeren of verwijderen van acties.|  
|ClientAuth.log|Registreert ondertekenen en activiteit van de verificatie voor de client.|  
|ClientIDManagerStartup.log|Maakt en onderhoudt de client-GUID en identificeert taken uitgevoerd tijdens clientregistratie en -toewijzing.|  
|ClientLocation.log|Registreert taken die aan de sitetoewijzing van de client gerelateerd zijn.|  
|CMHttpsReadiness.log|Registreert de resultaten van het uitvoeren van de Configuration Manager HTTPS Readiness Assessment Tool. Dit hulpprogramma controleert of computers een openbare-sleutelinfrastructuur (PKI)-certificaat voor clientverificatie dat kan worden gebruikt met Configuration Manager hebben.|  
|CmRcService.log|Registreert informatie voor de control-service op afstand.|  
|ContentTransferManager.log|Plant de Background Intelligent Transfer Service (BITS) of het Server Message Block (SMB) om te downloaden of toegang tot pakketten.|  
|DataTransferService.log|Registreert alle BITS-communicatie voor beleids- of pakkettoegang.|  
|EndpointProtectionAgent|Registreert informatie over de installatie van de System Center Endpoint Protection-client en de toepassing van anti malwarebeleid voor deze client.|  
|execmgr.log|Registreert details over pakketten en takenreeksen die worden uitgevoerd op de client.|  
|ExpressionSolver.log|Registreert gegevens over verbeterde detectiemethodes die gebruikt worden wanneer uitgebreide modus en het logboek voor foutopsporing is ingeschakeld.|  
|ExternalEventAgent.log|Registreert de geschiedenis van de Endpoint Protection-malware-detectie en gebeurtenissen met betrekking tot clientstatus.|  
|FileBITS.log|Registreert alle SMB-pakket-toegangstaken.|  
|FileSystemFile.log|Registreert de activiteit van de Windows Management Instrumentation (WMI) aanbieder voor software-inventaris en bestandsverzameling.|  
|FSPStateMessage.log|Registreert de activiteit voor statusberichten die gezonden worden naar het terugvalstatuspunt door de client.|  
|InternetProxy.log|Registreert de netwerkproxyconfiguratie configuratie en het gebruik van de client.|  
|InventoryAgent.log|Registreert activiteiten van hardware-inventaris, software-inventaris en heartbeat-detectieacties op de client.|  
|LocationCache.log|Registreert de activiteit voor locatie cache gebruik en onderhoud voor de client.|  
|LocationServices.log|Registreert de activiteit van de client voor het lokaliseren van beheerpunten, software-updatepunten en distributiepunten.|  
|MaintenanceCoordinator.log|Registreert de activiteit voor algemene onderhoudstaken voor de client.|  
|Mifprovider.log|Registreert de activiteit van de WMI-provider voor Management Information Format (MIF)-bestanden.|  
|mtrmgr.log|Bewaakt alle softwarelicentiecontroleprocessen.|  
|PolicyAgent.log|Registreert verzoeken voor beleidslijnen gemaakt met behulp van de Service voor gegevensoverdracht.|  
|PolicyAgentProvider.log|Registreert beleidswijzigingen.|  
|PolicyEvaluator.log|Registreert gegevens over de beoordeling van beleid op clientcomputer, met inbegrip van beleid vanaf software-updates.|  
|PolicyPlatformClient.log|Registreert het proces van herstel en naleving voor alle providers die zich in \Program Files\Microsoft Policy Platform, behalve de bestandsprovider.|  
|PolicySdk.log|Registreert activiteiten voor beleidsysteem SDK interfaces.|  
|Pwrmgmt.log|Registreert informatie over in- en schakelen en configureren van de wake-up proxy clientinstellingen.|  
|PwrProvider.log|Registreert de activiteiten van de energiebeheeraanbieder (PWRInvProvider) gehost in de WMI-service. Op alle ondersteunde versies van Windows somt de provider de huidige instellingen op de computers tijdens hardware-inventaris op en past de energiebeheerinstellingen toe.|  
|SCClient_&lt;*domain*\>@&lt;*username*\>_1.log|Registreert de activiteit in Software Center voor de opgegeven gebruiker op de clientcomputer.|  
|SCClient_&lt;*domain*\>@&lt;*username*\>_2.log|Registreert de historische activiteit in Software Center voor de gespecificeerde gebruiker op de clientcomputer.|  
|Scheduler.log|Registreert activiteiten van geplande taken voor alle clientbewerkingen.|  
|SCNotify_&lt;*domain*\>@&lt;*username*\>_1.log|Registreert de activiteit voor het verwittigen van gebruikers met betrekking tot software voor de opgegeven gebruiker.|  
|SCNotify_&lt;*domain*\>@&lt;*username*\>_1-&lt;*date_time*>.log|Registreert de historische activiteit voor het verwittigen van gebruikers met betrekking tot software voor de opgegeven gebruiker.|  
|setuppolicyevaluator.log|Registreert configuratie- en inventarisbeleid maken in WMI.|  
|SleepAgent_&lt;*domein*\>@SYSTEM_0.log|Het voornaamste logboekbestand voor wake-up proxy.|  
|smscliui.log|Registreert gebruik van de Configuration Manager-client in het Configuratiescherm.|  
|SrcUpdateMgr.log|Registreert activiteit voor geïnstalleerde Windows installertoepassingen die geüpdatet zijn met de huidige bronlocaties van distributiepunten.|  
|StatusAgent.log|Registreert statusberichten die zijn gemaakt door de clientonderdelen.|  
|SWMTRReportGen.log|Genereert een rapport gebruiken die is verzameld door de controleagent. Deze gegevens worden geregistreerd in Mtrmgr.log.|  
|UserAffinity.log|Registreert gegevens over gebruikersaffiniteit apparaat.|  
|VirtualApp.log|Registreert specifieke informatie voor de evaluatie van de implementatietypen van Application Virtualization (App-V).|  
|Wedmtrace.log|Registreert bewerkingen die betrekking hebben op het schrijven van filters op Windows Embedded-clients.|  
|wakeprxy-install.log|Registreert installatie-informatie wanneer clients de optie wake-up proxy inschakelen voor clientinstelling ontvangen.|  
|wakeprxy-uninstall.log|Registreert informatie over het verwijderen van wake-up proxy wanneer clients de clientinstelling optie voor het uitschakelen van wake-up proxy, ontvangen indien wake-up proxy eerder is ingeschakeld.|  

###  <a name="BKMK_ClientInstallLog"></a>Logboekbestanden van client-installatie  
 De volgende tabel bevat de logboekbestanden die informatie bevatten met betrekking tot de installatie van de Configuration Manager-client.  

|Logboeknaam|Beschrijving|  
|--------------|-----------------|  
|ccmsetup.log|Registreert ccmsetup.exe taken voor clientinstallatie, Clientupgrade en clientverwijdering. Kan worden gebruikt voor het oplossen van problemen tijdens de installatie van de client.|  
|ccmsetup-ccmeval.log|Registreert ccmsetup.exe taken voor clientstatus en -herstel.|  
|CcmRepair.log|Registreert de herstelactiviteiten van de clientagent.|  
|client.msi.log|Registreert installatietaken uitgevoerd door client.msi. Kan worden gebruikt voor het oplossen van problemen tijdens de installatie van de client.|  

###  <a name="BKMK_LogFilesforLnU"></a>Client voor Linux en UNIX  
 De Configuration Manager-client voor Linux en UNIX registreert informatie in de volgende logboekbestanden.  

> [!TIP]  
>  Beginnend met clients voor Linux en UNIX vanaf cumulatieve Update 1, kunt u CMTrace gebruiken om weer te geven van de logboekbestanden voor de client voor Linux en UNIX.  

> [!NOTE]  
>  Vervang de volgende referenties voor elk bestand of elk proces, wanneer u de initiële versie van de client voor Linux en UNIX gebruikt en een referentie maakt naar de documentatie in deze sectie:  
>   
>  -   Vervang **omiserver.bin** door **nwserver.bin**  
> -   Vervang **omi** door **nanowbem**  

|Logboeknaam|Details|  
|--------------|-------------|  
|Scxcm.log|Het logboekbestand voor de Kernservice van de Configuration Manager-client voor Linux en UNIX (ccmexec.bin). Dit logboekbestand bevat informatie over de installatie en voortgaande operaties van ccmexec.bin.<br /><br /> Standaard dit logboekbestand bevindt zich in **/var/opt/microsoft/scxcm.log**<br /><br /> Bewerk **/opt/microsoft/configmgr/etc/scxcm.conf** en wijzig het veld **PAD** om de locatie van het logboekbestand te wijzigen. U hoeft de clientcomputer of -service niet te herstarten om de wijziging door te voeren.<br /><br /> U kunt het Logniveau instellen op een van de vier verschillende instellingen.|  
|Scxcmprovider.log|Het logboekbestand voor de CIM-service van Configuration Manager-client voor Linux en UNIX (omiserver.bin). Dit logboekbestand bevat informatie over de lopende processen van nwserver.bin.<br /><br /> Dit logboekbestand bevindt zich in**/var/opt/microsoft/configmgr/scxcmprovider.log**<br /><br /> Als u de locatie van het logboekbestand wilt wijzigen, bewerkt u **/opt/microsoft/omi/etc/scxcmprovider.conf** en wijzigt u het veld **PAD**. U hoeft de clientcomputer of -service niet te herstarten om de wijziging door te voeren.<br /><br /> U kunt het Logniveau instellen op drie instellingen.|  

 Beide logboekbestanden bieden ondersteuning voor verschillende niveaus van logboekregistratie:  

-   **scxcm.log**. Om te wijzigen van het logboek-niveau, bewerkt **/opt/microsoft/configmgr/etc/scxcm.conf** en wijzig elke instantie van de **MODULE** tag naar het gewenste logboekniveau, om:  

    -   FOUT: Geeft de problemen die aandacht nodig hebben  

    -   WAARSCHUWING: Geeft mogelijke problemen voor de bewerkingen van client  

    -   INFO: Gedetailleerdere logboekregistratie die de status van diverse gebeurtenissen op de client aangeeft  

    -   VAN TRACEERBESTAND: Uitgebreide logboekregistratie die meestal wordt gebruikt voor het vaststellen van problemen  

-   **scxcmprovider.log**. Om te wijzigen van het logboek-niveau, bewerkt **/opt/microsoft/omi/etc/scxcmprovider.conf** en wijzig elke instantie van de **MODULE** tag naar het gewenste logboekniveau, om:  

    -   FOUT: Geeft de problemen die aandacht nodig hebben  

    -   WAARSCHUWING: Geeft mogelijke problemen voor de bewerkingen van client

    -   INFO: Gedetailleerdere logboekregistratie die de status van diverse gebeurtenissen op de client aangeeft  

Gebruik het Logniveau fout onder normale omstandigheden. Dit logboekniveau maakt het kleinste logboekbestand. Als het Logniveau van fout naar waarschuwing naar INFO en vervolgens naar TRACE, wordt er een groter logboekbestand omdat er meer gegevens worden geschreven naar het bestand gemaakt.  

####  <a name="BKMK_ManageLinuxLogs"></a>Logboekbestanden voor de client voor Linux en UNIX beheren  
De client voor Linux en UNIX beperkt de maximale grootte van de Clientlogboekbestanden niet, noch heeft de client automatisch Kopieer de inhoud van de .log-bestanden naar een ander bestand zoals naar een .log-bestand. Als u de maximumgrootte van logboekbestanden beheren wilt, implementeer dan een proces voor het beheren van de logboekbestanden dat onafhankelijk van de Configuration Manager-client voor Linux en UNIX.  

Bijvoorbeeld, kunt u de standaard Linux en UNIX-opdracht **logrotate** voor het beheren van de grootte en rotatie van de logboekbestanden van de client. De Configuration Manager-client voor Linux en UNIX heeft een interface waarmee **logrotate** vanwege de client wanneer de logrotatie voltooid is, zodat de client kan worden hervat registreren in het logboekbestand.  

Zie de documentatie voor de Linux- en UNIX-distributies die u gebruikt voor meer informatie over **logrotate**.  

###  <a name="BKMK_LogfilesforMac"></a>Client voor Mac-computers  
De Configuration Manager-client voor Mac-computers registreert informatie in de volgende logboekbestanden.  

|Logboeknaam|Details|  
|--------------|-------------|  
|CCMClient -&lt;*date_time*> .log|Registreert activiteiten die gerelateerd zijn aan de bewerkingen Mac-client, waaronder toepassingsbeheer, inventaris en foutenregistratie.<br /><br /> Dit logboekbestand bevindt zich in de map/Library/Application Support/Microsoft/CCM/Logs op de Mac-computer.|  
|CCMAgent -&lt;*date_time*> .log|Registreert informatie gerelateerd aan clientbewerkingen, waaronder gebruikersaanmelding en afmelden operations en activiteiten van Mac-computer.<br /><br /> Dit logboekbestand is in de map ~/Library/Logs op de Mac-computer.|  
|CCMNotifications -&lt;*date_time*> .log|Registreert activiteiten die gerelateerd zijn aan Configuration Manager-meldingen weergegeven op de Mac-computer.<br /><br /> Dit logboekbestand bevindt zich in de map ~/Library/Logs op de Mac-computer.|  
|CCMPrefPane -&lt;*date_time*> .log|Registreert activiteiten met betrekking tot de Configuration Manager-dialoogvenster Voorkeuren op Mac-computer, waaronder algemene status- en foutenregistratie.<br /><br /> Dit logboekbestand bevindt zich in de map ~/Library/Logs op de Mac-computer.|  

M registreert het logboekbestand SMS_DM.log op de sitesysteemserver ook communicatie tussen Mac-computers en het beheerpunt dat is ingesteld voor mobiele apparaten en Mac-computers.  

##  <a name="BKMK_ServerLogs"></a>Configuration Manager site server-logboekbestanden  
 De volgende gedeelten worden de logboekbestanden die op de siteserver zijn of die gerelateerd zijn aan specifieke sitesysteemrollen.  

###  <a name="BKMK_SiteSiteServerLog"></a>Server en de site siteserversystemen  
 De volgende tabel bevat de logboekbestanden die op de Configuration Manager-siteserver en sitesysteemservers.  

|Logboeknaam|Beschrijving|Computer met logboekbestand|  
|--------------|-----------------|----------------------------|  
|adctrl.log|Registreert de activiteit van de inschrijvingsverwerking|Siteserver|  
|ADForestDisc.log|Registreert detectieacties Active Directory-forest.|Siteserver|  
|ADService.log|Registreert details van accountaanmaking en beveiligingsgroepen in Active Directory.|Siteserver|  
|adsgdis.log|Registreert detectie-acties van Active Directory-groepen.|Siteserver|  
|adsysdis.log|Registreert detectieacties Active Directory-systeem.|Siteserver|  
|adusrdis.log|Registreert detectieacties Active Directory-gebruiker.|Siteserver|  
|ccm.log|Registreert installatieactiviteiten voor clientpush.|Siteserver|  
|CertMgr.log|Registreert activiteiten voor intrasite-communicatie van het certificaat.|Sitesysteemserver|  
|chmgr.log|Registreert activiteiten van de client health manager.|Siteserver|  
|Cidm.log|Registreert wijzigingen aan de clientinstellingen door de Client Install Data Manager (CIDM).|Siteserver|  
|colleval.log|Registreert gegevens over wanneer verzamelingen worden gemaakt, gewijzigd en verwijderd door de Verzamelingevaluator.|Siteserver|  
|compmon.log|Registreert de status van component-threads die worden bewaakt voor de siteserver.|Sitesysteemserver|  
|compsumm.log|Registreert taken van het component-statussamenvattingsprogramma.|Siteserver|  
|ComRegSetup.log|Registreert de initiële installatie van COM-registratieresultaten voor een siteserver.|Sitesysteemserver|  
|dataldr.log|Registreert informatie over de verwerking van MIF-bestanden en hardware-inventaris in Configuration Manager-database.|Siteserver|  
|ddm.log|Registreert activiteiten van de Discovery Data Manager.|Siteserver|  
|despool.log|Registreert inkomende overdrachten van communicatie tussen sites.|Siteserver|  
|distmgr.log|Registreert details over pakketcreatie, compressie, deltareplicatie en informatie-updates.|Siteserver|  
|EPCtrlMgr.log|Registreert informatie over het synchroniseren van informatie over malware-bedreiging van de Endpoint Protection-rol sitesysteemserver met de Configuration Manager-database.|Siteserver|  
|EPMgr.log|Registreert de status van de Endpoint Protection-sitesysteemrol.|Sitesysteemserver|  
|EPSetup.log|Geeft informatie over de installatie van de Endpoint Protection-sitesysteemrol.|Sitesysteemserver|  
|EnrollSrv.log|Registreert activiteiten van het proces van de inschrijvingsservice.|Sitesysteemserver|  
|EnrollWeb.log|Registreert activiteiten van het proces van de inschrijvingswebsite.|Sitesysteemserver|  
|fspmgr.log|Registreert activiteiten van de sitesysteemrol terugvalstatuspunt.|Sitesysteemserver|  
|hman.log|Registreert informatie over siteconfiguratiewijzigingen en het publiceren van site-informatie in Active Directory Domain Services.|Siteserver|  
|Inboxast.log|Registreert de bestanden die verplaatst worden van het beheerpunt naar de corresponderende POSTVAKKEN IN-map op de siteserver.|Siteserver|  
|inboxmgr.log|Registreert activiteiten van bestandsoverdracht tussen Postvak in-mappen.|Siteserver|  
|inboxmon.log|Registreert de verwerking van updates van Postvak in-bestanden en prestatiemeteritems.|Siteserver|  
|invproc.log|Registreert het doorsturen van MIF-bestanden van een secundaire site naar de daarboven liggende site.|Siteserver|  
|migmctrl.log|Registreert informatie voor migratieacties die migratietaken, gedeelde distributiepunten en distributiepuntupdates bevatten.|Het hoogste niveau in de Configuration Manager-hiërarchie, en elke onderliggende primaire site.<br /><br /> Gebruik het logboekbestand dat wordt gemaakt op de centrale beheersite in een hiërarchie met meerdere primaire sites.|  
|mpcontrol.log|Registreert de registratie van het beheerpunt met Windows Internet Name Service (WINS). Registreert elke 10 minuten de beschikbaarheid van het beheerpunt.|Sitesysteemserver|  
|mpfdm.log|Registreert de acties van de beheerpuntcomponent die clientbestanden verplaatst naar de corresponderende POSTVAKKEN IN-map op de siteserver.|Sitesysteemserver|  
|mpMSI.log|Registreert gegevens over het beheer van de installatie van beheerpunt.|Siteserver|  
|MPSetup.log|Registreert het wrapperproces van de beheerpuntinstallatie.|Siteserver|  
|netdisc.log|Registreert netwerkdetectieacties.|Siteserver|  
|ntsvrdis.log|Registreert de detectie-activiteit van sitesysteemservers.|Siteserver|  
|Objreplmgr|Registreert de verwerking van objectwijzigingsmeldingen voor replicatie.|Siteserver|  
|offermgr.log|Registreert advertentie-updates.|Siteserver|  
|offersum.log|Registreert de samenvatting van statusberichten voor implementatie.|Siteserver|  
|OfflineServicingMgr.log|Registreert de activiteiten van het toepassen van updates in afbeeldingsbestanden van het besturingssysteem.|Siteserver|  
|outboxmon.log|Registreert de verwerking van updates van Postvak uit-bestanden en prestatiemeteritems.|Siteserver|  
|PerfSetup.log|Registreert de resultaten van de installatie van prestatiemeteritems.|Sitesysteemserver|  
|PkgXferMgr.log|Registreert de acties van de SMS Executive-component die verantwoordelijk is voor de verzending van content van een primaire site naar een extern distributiepunt.|Siteserver|  
|policypv.log|Registreert updates van de clientbeleidsregels die nodig zijn na wijzigingen aan clientinstellingen of implementaties.|Primaire siteserver|  
|rcmctrl.log|Registreert de activiteiten van databasereplicatie tussen sites binnen de hiërarchie.|Siteserver|  
|replmgr.log|Registreert de replicatie van bestanden tussen de siteservercomponenten en de Scheduler-component.|Siteserver|  
|ResourceExplorer.log|Registreert fouten, waarschuwingen en informatie over het uitvoeren van de Resource Explorer.|Computer waarop de Configuration Manager-console|  
|ruleengine.log|Registreert details over automatische implementatieregels voor de identificatie, het downloaden van software, en maken van software-updategroepen en implementaties.|Siteserver|  
|schedule.log|Registreert details over de replicatie tussen sites van taken en bestanden.|Siteserver|  
|sender.log|Registreert de bestanden die worden overgezet door middel van bestandsgebaseerde replicatie tussen sites.|Siteserver|  
|sinvproc.log|Registreert informatie over het verwerking van software-inventarisgegevens naar de sitedatabase.|Siteserver|  
|sitecomp.log|Registreert details over het onderhoud van de geïnstalleerde sitecomponenten op alle sitesysteemservers in de site.|Siteserver|  
|sitectrl.log|Registreert site-instellingswijzigingen die zijn aangebracht aan site-controleobjecten in de database.|Siteserver|  
|sitestat.log|Registreert het bewakingsproces van beschikbaarheid en schijfruimte voor alle sitesystemen.|Siteserver|  
|SmsAdminUI.log|Registreert Configuration Manager-console-activiteit.|Computer waarop de Configuration Manager-console|  
|SMSAWEBSVCSetup.log|Registreert de installatieactiviteiten van de Application Catalog-webservice.|Sitesysteemserver|  
|smsbkup.log|Registreert output van het back-upproces van de site.|Siteserver|  
|smsdbmon.log|Registreert wijzigingen van de database.|Siteserver|  
|SMSENROLLSRVSetup.log|Registreert de installatieactiviteiten van de inschrijvingswebservice.|Sitesysteemserver|  
|SMSENROLLWEBSetup.log|Registreert de installatieactiviteiten van de inschrijvingswebsite.|Sitesysteemserver|  
|smsexec.log|Registreert de verwerking van alle component-threads van siteservers.|Siteserver of sitesysteemserver|  
|SMSFSPSetup.log|Registreert berichten die gegenereerd worden door de installatie van een terugvalstatuspunt.|Sitesysteemserver|  
|SMSPORTALWEBSetup.log|Registreert de installatieactiviteiten van de Application Catalog-website.|Sitesysteemserver|  
|SMSProv.log|Registreert toegang van de WMI-provider tot de sitedatabase.|Computer met de SMS-provider|  
|srsrpMSI.log|Registreert gedetailleerde resultaten van het installatieproces van het rapportagepunt uit de MSI-output.|Sitesysteemserver|  
|srsrpsetup.log|Registreert resultaten van het installatieproces van het rapportagepunt.|Sitesysteemserver|  
|statesys.log|Registreert de verwerking van statussysteemberichten.|Siteserver|  
|statmgr.log|Registreert het schrijven van alle statusberichten naar de database.|Siteserver|  
|swmproc.log|Registreert de verwerking van meterbestanden en instellingen.|Siteserver|  

###  <a name="BKMK_SiteInstallLog"></a>Logboekbestanden van siteserverinstallatie site  
 De volgende tabel bevat de logboekbestanden die informatie bevatten over de site-installatie.  

|Logboeknaam|Beschrijving|Computer met logboekbestand|  
|--------------|-----------------|----------------------------|  
|ConfigMgrPrereq.log|Registreert vereiste component evaluatie en installatie activiteiten.|Siteserver|  
|ConfigMgrSetup.log|Registreert gedetailleerde output van de installatie van de site.|Siteserver|  
|ConfigMgrSetupWizard.log|Registreert informatie met betrekking tot de activiteit in de Wizard Setup.|Siteserver|  
|SMS_BOOTSTRAP.log|Registreert informatie over de voortgang van de lancering van het installatieproces voor de secundaire site. Details van het werkelijke installatieproces zijn opgenomen in ConfigMgrSetup.log.|Siteserver|  
|smstsvc.log|Registreert informatie over het installeren, gebruiken en verwijderen van een Windows-service die wordt gebruikt voor het testen van de netwerkverbinding en machtigingen tussen servers, via het computeraccount van de server die de verbinding initieert.|Siteserver en sitesysteemserver|  

###  <a name="BKMK_FSPLog"></a>Logboekbestanden voor terugvalstatuspunt-punt  
 De volgende tabel bevat de logboekbestanden die informatie bevatten over het terugvalstatuspunt.  

|Logboeknaam|Beschrijving|Computer met logboekbestand|  
|--------------|-----------------|----------------------------|  
|FspIsapi|Registreert gegevens over communicatie naar een terugvalstatuspunt van verouderde clients van mobiele apparaten en clientcomputers.|Sitesysteemserver|  
|fspMSI.log|Registreert berichten die gegenereerd worden door de installatie van een terugvalstatuspunt.|Sitesysteemserver|  
|fspmgr.log|Registreert activiteiten van de sitesysteemrol terugvalstatuspunt.|Sitesysteemserver|  

###  <a name="BKMK_MPLog"></a>Management-punt-logboekbestanden  
 De volgende tabel bevat de logboekbestanden die informatie bevatten over het beheerpunt.  

|Logboeknaam|Beschrijving|Computer met logboekbestand|  
|--------------|-----------------|----------------------------|  
|CcmIsapi.log|Registreert activiteiten met betrekking tot clientberichten op het eindpunt.|Sitesysteemserver|  
|MP_CliReg.log|Registreert activiteiten met betrekking tot clientregistratie, verwerkt door het beheerpunt.|Sitesysteemserver|  
|MP_Ddr.log|Registreert de conversie van XML.ddr records van clients en kopieert ze naar de siteserver.|Sitesysteemserver|  
|MP_Framework.log|Registreert de activiteiten van het kernbeheerpunt en componenten van het clientframework.|Sitesysteemserver|  
|MP_GetAuth.log|Registreert activiteiten met betrekking tot clientautorisatie.|Sitesysteemserver|  
|MP_GetPolicy.log|Registreert activiteiten met betrekking tot beleidsaanvragen van clientcomputers.|Sitesysteemserver|  
|MP_Hinv.log|Registreert details over de conversie van XML hardware-inventarisrecords van clients en de kopie van die bestanden naar de siteserver.|Sitesysteemserver|  
|MP_Location.log|Registreert activiteiten met betrekking tot locatieaanvragen en antwoorden van clients.|Sitesysteemserver|  
|MP_OOBMgr.log|Registreert de beheerpuntactiviteiten met betrekking tot het ontvangen van een OTP van een client.|Sitesysteemserver|  
|MP_Policy.log|Registreert beleidcommunicatie.|Sitesysteemserver|  
|MP_Relay.log|Registreert het overdragen van bestanden die worden opgehaald van de client.|Sitesysteemserver|  
|MP_Retry.log|Registreert hardware-inventaris retry-processen.|Sitesysteemserver|  
|MP_Sinv.log|Registreert details over de conversie van XML software-inventarisrecords van clients en de kopie van die bestanden naar de siteserver.|Sitesysteemserver|  
|MP_SinvCollFile.log|Registreert details over bestandsverzameling.|Sitesysteemserver|  
|MP_Status.log|Registreert details over de conversie van XML.svf statusberichtbestanden van clients en de kopie van die bestanden naar de siteserver.|Sitesysteemserver|  
|mpcontrol.log|Registreert de registratie van het beheerpunt met WINS. Registreert elke 10 minuten de beschikbaarheid van het beheerpunt.|Siteserver|  
|mpfdm.log|Registreert de acties van de beheerpuntcomponent die clientbestanden verplaatst naar de corresponderende POSTVAKKEN IN-map op de siteserver.|Sitesysteemserver|  
|mpMSI.log|Registreert gegevens over het beheer van de installatie van beheerpunt.|Siteserver|  
|MPSetup.log|Registreert het wrapperproces van de beheerpuntinstallatie.|Siteserver|  

###  <a name="BKMK_SUPLog"></a>Logboekbestanden voor software-update-punt  
 De volgende tabel bevat de logboekbestanden die informatie over de software-updatepunt bevatten.  

|Logboeknaam|Beschrijving|Computer met logboekbestand|  
|--------------|-----------------|----------------------------|  
|objreplmgr.log|Registreert gegevens over de replicatie van software-updates melding bestanden van een bovenliggende site naar onderliggende sites.|Siteserver|  
|PatchDownloader.log|Registreert gegevens over het proces van downloaden van software-updates van de updatebron naar de downloadbestemming op de siteserver.|Computer die als host fungeert voor de Configuration Manager-console van waaruit de downloads worden geïnitieerd|  
|ruleengine.log|Registreert details over automatische implementatieregels voor de identificatie, het downloaden van software, en maken van software-updategroepen en implementaties.|Siteserver|  
|SUPSetup.log|Registreert gegevens over de installatie van het software-updatepunt. Wanneer de installatie van het software-updatepunt is voltooid, wordt **Installatie is geslaagd** geschreven naar dit logboekbestand.|Sitesysteemserver|  
|WCM.log|Registreert details over de software-update beheerpunt configuratie en verbindingen met de WSUS-server voor geabonneerde updatecategorieën, classificaties en talen.|Siteserver die verbinding met de WSUS-server maakt|  
|WSUSCtrl.log|Registreert gegevens over de configuratie, databaseconnectiviteit en status van de WUS-server voor de site.|Sitesysteemserver|  
|wsyncmgr.log|Registreert gegevens over het synchronisatieproces van software-updates.|Sitesysteemserver|  
|WUSSyncXML.log|Registreert gegevens over het Inventarisatiehulpprogramma voor Microsoft-Updates synchroniseren proces.|Clientcomputer geconfigureerd als de synchronisatie-host voor het Inventarisatiehulpprogramma voor Microsoft-Updates|  

##  <a name="BKMK_FunctionLogs"></a>Logboekbestanden voor Configuration Manager-functionaliteit  
 De volgende secties lijst logboekbestanden gerelateerd aan Configuration Manager-functies.  

###  <a name="BKMK_AppManageLog"></a>Toepassingsbeheer  
 De volgende tabel bevat de logboekbestanden die informatie bevatten met betrekking tot Toepassingsbeheer.  

|Logboeknaam|Beschrijving|Computer met logboekbestand|  
|--------------|-----------------|----------------------------|  
|AppIntentEval.log|Registreert gegevens over de huidige en beoogde status van toepassingen, hun toepasbaarheid, of voldaan werd aan de vereisten, implementatietypes en afhankelijkheden.|Client|  
|AppDiscovery.log|Registreert de gegevens over de gevonden of gedetecteerde toepassingen op clientcomputers.|Client|  
|AppEnforce.log|Registreert gegevens over afdwingacties (installeren en verwijderen) die genomen werden voor toepassingen op de client.|Client|  
|awebsctl.log|Registreert de bewakingsactiviteiten voor de Application Catalog-webservice beheerpunt sitesysteemrol.|Sitesysteemserver|  
|awebsvcMSI.log|Registreert gedetailleerde informatie voor de sitesysteemrol van het Application Catalog-webservicepunt.|Sitesysteemserver|  
|Ccmsdkprovider.log|Registreert de activiteiten van het toepassingsbeheer SDK.|Client|  
|colleval.log|Registreert gegevens over wanneer verzamelingen worden gemaakt, gewijzigd en verwijderd door de Verzamelingevaluator.|Sitesysteemserver|  
|ConfigMgrSoftwareCatalog.log|Registreert de activiteit van de Application Catalog, wat zijn gebruik van Silverlight bevat.|Client|  
|portlctl.log|Registreert de bewakingsactiviteiten voor de sitesysteemrol van het Application Catalog-websitepunt.|Sitesysteemserver|  
|portlwebMSI.log|Registreert de MSI installatieactiviteit voor de Application Catalog-website.|Sitesysteemserver|  
|PrestageContent.log|Registreert gegevens over het gebruik van het hulpprogramma ExtractContent.exe op een externe, voorbereid distributiepunt. Dit hulpprogramma extraheert inhoud die werd geëxporteerd naar een bestand.|Sitesysteemserver|  
|ServicePortalWebService.log|Registreert de activiteit van de Application Catalog-webservice.|Sitesysteemserver|  
|ServicePortalWebSite.log|Registreert de activiteit van de Application Catalog-website.|Sitesysteemserver|  
|SMSdpmon.log|Registreert gegevens over de geplande taak van statusbewaking van het distributiepunt, dat op een distributiepunt geconfigureerd is.|Siteserver|  
|SoftwareCatalogUpdateEndpoint.log|Registreert activiteiten voor het beheren van de URL voor de Application Catalog getoond in Software Center.|Client|  
|SoftwareCenterSystemTasks.log|Registreert activiteiten met betrekking tot de validatie van de vereiste component Software Center.|Client|  

 De volgende tabel geeft een lijst van de logboekbestanden die informatie bevatten met betrekking tot het implementeren van pakketten en programma's.  

|Logboeknaam|Beschrijving|Computer met logboekbestand|  
|--------------|-----------------|----------------------------|  
|colleval.log|Registreert gegevens over wanneer verzamelingen worden gemaakt, gewijzigd en verwijderd door de Verzamelingevaluator.|Siteserver|  
|execmgr.log|Registreert gegevens over pakketten en takenreeksen die worden uitgevoerd.|Client|  

###  <a name="BKMK_AILog"></a>Asset intelligence  
 De volgende tabel geeft een lijst van de logboekbestanden die informatie bevatten met betrekking tot asset intelligence.  

|Logboeknaam|Beschrijving|Computer met logboekbestand|  
|--------------|-----------------|----------------------------|  
|AssetAdvisor.log|Registreert de activiteiten van Asset Intelligence-inventarisatie-acties.|Client|  
|aikbmgr.log|Registreert gegevens over de verwerking van XML-bestanden van het postvak IN voor het updaten van de asset intelligence-catalogus.|Siteserver|  
|AIUpdateSvc.log|Registreert de interactie van de Asset Intelligence-synchronisatie beheerpunt met System Center Online (SCO), de online webservice.|Sitesysteemserver|  
|AIUSMSI.log|Registreert gegevens over de installatie van de synchronisatie van Asset Intelligence punt sitesysteemrol.|Sitesysteemserver|  
|AIUSSetup.log|Registreert gegevens over de installatie van de synchronisatie van Asset Intelligence punt sitesysteemrol.|Sitesysteemserver|  
|ManagedProvider.log|Registreert gegevens over detectie van software met een gekoppelde software-identificatietag. Registreert ook activiteiten met betrekking tot de hardware-inventaris.|Sitesysteemserver|  
|MVLSImport.log|Registreert gegevens over de verwerking van de geïmporteerde licentiegegevens bestanden.|Sitesysteemserver|  

###  <a name="BKMK_BnRLog"></a>Back-up en herstel  
 De volgende tabel geeft een lijst van de logboekbestanden die informatie bevatten met betrekking tot back-up en herstelacties, met inbegrip van siteresets en wijzigingen aan de SMS-Provider.  

|Logboeknaam|Beschrijving|Computer met logboekbestand|  
|--------------|-----------------|----------------------------|  
|ConfigMgrSetup.log|Registreert informatie over installatie- en hersteltaken taken wanneer de Configuration Manager een herstel vanuit backup herstelt.|Siteserver|  
|Smsbkup.log|Registreert gegevens over de site back-up van de activiteit.|Siteserver|  
|smssqlbkup.log|Registreert output van de back-upproces database wanneer SQL Server is geïnstalleerd op een andere server dan de siteserver.|Sitedatabaseserver|  
|Smswriter.log|Registreert informatie over de status van de Configuration Manager VSS writer die wordt gebruikt door de back-up.|Siteserver|  

###  <a name="BKMK_CertificateEnrollment"></a>Certificaatinschrijving  
 De volgende tabel geeft een lijst van de Configuration Manager-logboekbestanden die informatie bevatten met betrekking tot certificaatregistratie. Certificaatinschrijving maakt gebruik van het certificaatregistratiepunt en de Configuration Manager-beleidsmodule op de server waarop de Network Device Enrollment Service wordt uitgevoerd.  

|Logboeknaam|Beschrijving|Computer met logboekbestand|  
|--------------|-----------------|----------------------------|  
|CRP.log|Registreert activiteiten van de inschrijving.|Certificaatregistratiepunt|  
|Crpctrl.log|Registreert de operationele status van het registratiepunt van het certificaat.|Certificaatregistratiepunt|  
|Crpsetup.log|Registreert gegevens over de installatie en configuratie van het certificaatregistratiepunt.|Certificaatregistratiepunt|  
|Crpmsi.log|Registreert gegevens over de installatie en configuratie van het certificaatregistratiepunt.|Certificaatregistratiepunt|  
|NDESPlugin.log|Registreert uitdaging verificatie en certificaat-registratieactiviteiten.|Configuration Manager-beleidsmodule en de Network Device Enrollment Service|  

 Controleer de Windows-Logboeken in Logboekinzage op de server waarop de Network Device Enrollment Service wordt uitgevoerd en de server die als host fungeert voor het certificaatregistratiepunt naast de Configuration Manager-logboekbestanden. Zoek bijvoorbeeld naar berichten van de bron **NetworkDeviceEnrollmentService**. U kunt ook de volgende logboekbestanden gebruiken:  

-   IIS-logboek bestanden voor Network Device Enrollment Service:  **&lt;pad\>\inetpub\logs\LogFiles\W3SVC1**  

-   IIS-logboek bestanden voor het certificaatregistratiepunt:  **&lt;pad\>\inetpub\logs\LogFiles\W3SVC1**  

-   Logboekbestand voor Registratiebeleid voor netwerkapparaten: **mscep.log**  

    > [!NOTE]  
    >  Dit bestand bevindt zich in de map voor het accountprofiel voor registratieservice voor netwerkapparaten, bijvoorbeeld in C:\Users\SCEPSvc. Zie de sectie [Enable Logging](http://go.microsoft.com/fwlink/?LinkId=320576) (Logboekregistratie inschakelen) in het artikel Network Device Enrollment Service (NDES) in Active Directory Certificate Services (AD CS) in het TechNet-wiki voor meer informatie over het inschakelen van logboekregistratie voor de Registratieservice voor netwerkapparaten.  

###  <a name="BKMK_BGB"></a>Clientmeldingen  
 De volgende tabel geeft een lijst van de logboekbestanden die informatie bevatten met betrekking tot clientmelding.  

|Logboeknaam|Beschrijving|Computer met logboekbestand|  
|--------------|-----------------|----------------------------|  
|bgbmgr.log|Registreert gegevens over de site serveractiviteiten met betrekking tot clientmeldingstaken en online verwerking en statusbestanden.|Siteserver|  
|BGBServer.log|Registreert de activiteiten van de meldingsserver zoals client-servercommunicatie en het pushen van taken naar clients. Registreert ook informatie over de generatie van online en statusbestanden moet worden verzonden naar de siteserver.|Beheerpunt|  
|BgbSetup.log|Registreert de activiteiten van de notification server de beheerpuntinstallatie tijdens de installatie en verwijdering.|Beheerpunt|  
|bgbisapiMSI.log|Registreert gegevens over de notification server installeren en verwijderen.|Beheerpunt|  
|BgbHttpProxy.log|Registreert de activiteiten van de HTTP-meldingsproxy zoals het de berichten van clients die HTTP gebruiken, overdraagt naar en van de meldingsserver.|Client|  
|CcmNotificationAgent.log|Registreert de activiteiten van de meldingsagent zoals client-servercommunicatie en informatie over taken ontvangen en verzonden naar andere clientagents.|Client|  

### <a name="cloud-management-gateway"></a>Cloud management gateway

De volgende tabel bevat de logboekbestanden die informatie over de cloud management gateway bevatten.

||||
|-|-|-|
|Logboeknaam|Beschrijving|Computer met logboekbestand|
|CloudMgr.log|Registreert gegevens over het implementeren van de cloud management gateway-service, de status van actieve service en gegevens gebruiken die zijn gekoppeld aan de service.<br>U kunt het niveau van logboekregistratie voor het register bewerken **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\SMS\COMPONENTS\SMS_CLOUD_SERVICES_MANAGER\Logging niveau**|De **SMS/Logs** map op de sitesysteemserver|
|CMGSetup.log of CMG -*RoleInstanceID*-CMGSetup.log<sup>1</sup>|Registreert gegevens over de 2e fase van de implementatie van cloud management gateway (lokale implementatie in Azure)<br>Kunt u het niveau voor logboekregistratie met behulp van de instelling **traceerniveau** (**informatie** (standaard), **uitgebreid**, **fout**) op de **Azure portal\Cloud services configuration** tabblad.|De **%approot%\logs** op uw Azure-server of de map SMS/logboeken op de sitesysteemserver|
|CMGHttpHandler.log of CMG -*RoleInstanceID*-CMGHttpHandler.log<sup>1</sup>|Registreert gegevens over de cloud management gateway HTTP-handler binding met Internet Information Services in Azure<br>Kunt u het niveau voor logboekregistratie met behulp van de instelling **traceerniveau** (**informatie** (standaard), **uitgebreid**, **fout**) op de **Azure portal\Cloud services configuration** tabblad.|De **%approot%\logs** op uw Azure-server of de map SMS/logboeken op de sitesysteemserver|
|CMGService.log of CMG -*RoleInstanceID*-CMGService.log<sup>1</sup>|Registreert gegevens over de cloud management gateway-service core-component in Azure<br>Kunt u het niveau voor logboekregistratie met behulp van de instelling **traceerniveau** (**informatie** (standaard), **uitgebreid**, **fout**) op de **Azure portal\Cloud services configuration** tabblad.|De **%approot%\logs** op uw Azure-server of de map SMS/logboeken op de sitesysteemserver|
|SMS_Cloud_ProxyConnector.log|Registreert details over het instellen van de verbindingen tussen de cloud management gateway-service en de cloud management gatewayverbinding beheerpunt.|Sitesysteemserver|

<sup>1</sup> dit zijn lokale Configuration Manager-logboekbestanden die cloud service manager synchroniseren van Azure-opslag om de 5 minuten. De cloud management gateway zendt de logboeken met Azure-opslag om de 5 minuten. waardoor de maximale vertraging 10 minuten. Uitgebreide switches heeft invloed op de lokale en externe logboeken.

- Gebruiken voor het oplossen van implementaties, **CloudMgr.log** en **CMGSetup.log**
- Gebruiken voor het oplossen van servicestatus **CMGService.log** en **SMS_Cloud_ProxyConnector.log**.
- Gebruik voor het oplossen van problemen clientverkeer **CMGHttpHandler.log**, **CMGService.log**, en **SMS_Cloud_ProxyConnector.log**.

###  <a name="BKMK_CompSettingsLog"></a>Compatibiliteitsinstellingen en toegang tot bedrijfsbronnen  
 De volgende tabel geeft een lijst van de logboekbestanden die informatie bevatten met betrekking tot nalevingsinstellingen en toegang tot bedrijfsbronnen.  

|Logboeknaam|Beschrijving|Computer met logboekbestand|  
|--------------|-----------------|----------------------------|  
|CIAgent.log|Registreert gegevens over het proces van herstel en naleving voor nalevingsinstellingen, software-updates en replicatiebeheer.|Client|  
|CITaskManager.log|Registreert informatie over de taakplanning voor configuratie-item.|Client|  
|DCMAgent.log|Registreert informatie op hoog niveau over de beoordeling, rapportage van conflicten en herstel van configuratie-items en -toepassingen.|Client|  
|DCMReporting.log|Registreert informatie over rapportagebeleid van platformresultaten in statusberichten voor configuratie-items.|Client|  
|DcmWmiProvider.log|Registreert informatie over het lezen van configuratie-item-synclets van WMI.|Client|  

###  <a name="BKMK_ConsoleLog"></a>Configuration Manager-console  
 De volgende tabel bevat de logboekbestanden die informatie over de Configuration Manager-console bevatten.  

|Logboeknaam|Beschrijving|Computer met logboekbestand|  
|--------------|-----------------|----------------------------|  
|ConfigMgrAdminUISetup.log|Registreert de installatie van de Configuration Manager-console.|Computer waarop de Configuration Manager-console|  
|SmsAdminUI.log|Registreert informatie over de werking van de Configuration Manager-console.|Computer waarop de Configuration Manager-console|  
|Smsprov.log|Registreert activiteiten uitgevoerd door de aanbieder van SMS. Configuration Manager-consoleactiviteiten gebruiken de SMS-Provider.|Siteserver of sitesysteemserver|  

###  <a name="BKMK_ContentLog"></a>Inhoudsbeheer  
 De volgende tabel geeft een lijst van de logboekbestanden die informatie bevatten met betrekking tot inhoudbeheer.  

|Logboeknaam|Beschrijving|Computer met logboekbestand|  
|--------------|-----------------|----------------------------|  
|CloudDP -&lt;guid\>.log|Registreert gegevens voor een specifiek clouddistributiepunt, inclusief informatie over opslag en toegang tot inhoud.|Sitesysteemserver|  
|CloudMgr.log|Registreert gegevens over inhoud inrichten verzamelen van opslag en bandbreedtestatistieken en acties beheerder geïnitieerde de cloudservice die wordt uitgevoerd een cloud-gebaseerde distributiepunt starten of stoppen.|Sitesysteemserver|  
|DataTransferService.log|Registreert alle BITS-communicatie voor beleids- of pakkettoegang. Dit logboek wordt ook gebruikt voor inhoudbeheer door pull-distributiepunten.|Computer die is geconfigureerd als een pull-distributiepunt|  
|PullDP.log|Registreert gegevens over inhoud die het pull-distributiepunt overdraagt van brondistributiepunten.|Computer die is geconfigureerd als een pull-distributiepunt|  
|PrestageContent.log|Registreert informatie over het gebruik van de ExtractContent.exe hulpprogramma op een externe, voorbereid distributiepunt. Dit hulpprogramma extraheert inhoud die werd geëxporteerd naar een bestand.|Sitesysteemrol|  
|SMSdpmon.log|Registreert gegevens over distribution point voor health monitoring geplande taken die zijn geconfigureerd op een distributiepunt.|Sitesysteemrol|  
|smsdpprov.log|Registreert gegevens over de extractie van gecomprimeerde bestanden die ontvangen worden van een primaire site. Dit logboek is gegenereerd door de WMI-provider van het externe distributiepunt.|Distributiepuntcomputer die niet is geplaatst als de siteserver|  


###  <a name="BKMK_DiscoveryLog"></a>Detectie  
De volgende tabel bevat de logboekbestanden die informatie bevatten met betrekking tot detectie.  

|Logboeknaam|Beschrijving|Computer met logboekbestand|  
|--------------|-----------------|----------------------------|  
|adsgdis.log|Registreert detectieacties Active Directory-beveiligingsgroep.|Siteserver|  
|adsysdis.log|Registreert detectieacties Active Directory-systeem.|Siteserver|  
|adusrdis.log|Registreert detectieacties Active Directory-gebruiker.|Siteserver|  
|ADForestDisc.Log|Registreert detectieacties Active Directory-forest.|Siteserver|  
|ddm.log|Registreert activiteiten van de Discovery Data Manager.|Siteserver|  
|InventoryAgent.log|Registreert activiteiten van hardware-inventaris, software-inventaris en heartbeat-detectieacties op de client.|Client|  
|netdisc.log|Registreert netwerkdetectieacties.|Siteserver|  

###  <a name="BKMK_EPLog"></a>Endpoint Protection  
 De volgende tabel geeft een lijst van de logboekbestanden die informatie bevatten met betrekking tot Endpoint Protection.  

|Logboeknaam|Beschrijving|Computer met logboekbestand|  
|--------------|-----------------|----------------------------|  
|EndpointProtectionAgent.log|Registreert gegevens over de installatie van de Endpoint Protection-client en de toepassing van anti-malware-beleid voor deze client.|Client|  
|EPCtrlMgr.log|Registreert gegevens over het synchroniseren van informatie over malware-bedreiging van de Endpoint Protection-rolserver met de Configuration Manager-database.|Sitesysteemserver|  
|EPMgr.log|Bewaakt de status van de Endpoint Protection-sitesysteemrol.|Sitesysteemserver|  
|EPSetup.log|Geeft informatie over de installatie van de Endpoint Protection-sitesysteemrol.|Sitesysteemserver|  

###  <a name="BKMK_Extensions"></a>Uitbreidingen  
 De volgende tabel bevat de logboekbestanden die informatie bevatten met betrekking tot uitbreidingen.  

|Logboeknaam|Beschrijving|Computer met logboekbestand|  
|--------------|-----------------|----------------------------|  
|AdminUI.ExtensionInstaller.log|Registreert informatie over het downloaden van uitbreidingen van Microsoft en de installatie en verwijdering van alle uitbreidingen.|Computer waarop de Configuration Manager-console|  
|FeatureExtensionInstaller.log|Registreert informatie over het installeren en verwijderen van afzonderlijke uitbreidingen als ze zijn ingeschakeld of uitgeschakeld in de Configuration Manager-console.|Computer waarop de Configuration Manager-console|  
|SmsAdminUI.log|Registreert Configuration Manager-console-activiteit.|Computer waarop de Configuration Manager-console|  

###  <a name="BKMK_InventoryLog"></a>Inventarisatie  
 De volgende tabel geeft een lijst van de logboekbestanden die informatie bevatten met betrekking tot het verwerken van inventarisgegevens.  

|Logboeknaam|Beschrijving|Computer met logboekbestand|  
|--------------|-----------------|----------------------------|  
|dataldr.log|Registreert informatie over de verwerking van MIF-bestanden en hardware-inventaris in Configuration Manager-database.|Siteserver|  
|invproc.log|Registreert het doorsturen van MIF-bestanden van een secundaire site naar de daarboven liggende site.|Secundaire siteserver|  
|sinvproc.log|Registreert informatie over het verwerking van software-inventarisgegevens naar de sitedatabase.|Siteserver|  

###  <a name="BKMK_MeteringLog"></a>Softwarelicentiecontrole  
 De volgende tabel geeft een lijst van de logboekbestanden die informatie bevatten met betrekking tot meting.  

|Logboeknaam|Beschrijving|Computer met logboekbestand|  
|--------------|-----------------|----------------------------|  
|mtrmgr.log|Bewaakt alle softwarelicentiecontroleprocessen.|Siteserver|  

###  <a name="BKMK_MigrationLog"></a>Migratie  
 De volgende tabel geeft een lijst van de logboekbestanden die informatie bevatten met betrekking tot migratie.  

|Logboeknaam|Beschrijving|Computer met logboekbestand|  
|--------------|-----------------|----------------------------|  
|migmctrl.log|Registreert informatie over migratieacties die migratietaken, gedeelde distributiepunten en distributiepuntupdates bevatten.|Het hoogste niveau in de Configuration Manager-hiërarchie, en elke onderliggende primaire site.<br /><br /> Gebruik, in een sitehiërarchie met meerdere primaire sites, het logboekbestand gemaakt in de centrale beheersite.|  

###  <a name="BKMK_MDMLog"></a>Mobiele apparaten  
 De volgende gedeelten worden de logboekbestanden die informatie bevatten met betrekking tot het beheren van mobiele apparaten.  

####  <a name="BKMK_EnrollmentLog"></a>Inschrijving  
 De volgende tabel geeft een lijst van de logboekbestanden die informatie bevatten met betrekking tot registratie van mobiele apparaten.  

|Logboeknaam|Beschrijving|Computer met logboekbestand|  
|--------------|-----------------|----------------------------|  
|DMPRP.log|Registreert communicatie tussen beheerpunten die ingeschakeld zijn voor mobiele apparaten en de eindpunten van beheerpunten.|Sitesysteemserver|  
|dmpmsi.log|Registreert de Windows installergegevens voor de configuratie van een beheerpunt dat is ingeschakeld voor mobiele apparaten.|Sitesysteemserver|  
|DMPSetup.log|Registreert de configuratie van het beheerpunt dat is ingeschakeld voor mobiele apparaten.|Sitesysteemserver|  
|enrollsrvMSI.log|Registreert de Windows Installer-gegevens voor de configuratie van een registratiepunt.|Sitesysteemserver|  
|enrollmentweb.log|Registreert communicatie tussen mobiele apparaten en het proxypunt voor registratie.|Sitesysteemserver|  
|enrollwebMSI.log|Registreert de Windows Installer-gegevens voor de configuratie van een registratieproxypunt.|Sitesysteemserver|  
|enrollmentservice.log|Registreert communicatie tussen het registratieproxypunt en het registratiepunt.|Sitesysteemserver|  
|SMS_DM.log|Registreert communicatie tussen mobiele apparaten, Mac-computers en het beheerpunt dat is ingeschakeld voor mobiele apparaten en Mac-computers.|Sitesysteemserver|  

####  <a name="BKMK_ExchSrvLog"></a>Exchange Server-Connector  
 De logboeken van de volgende bevatten informatie met betrekking tot de Exchange Server-Connector.  

|Logboeknaam|Beschrijving|Computer met logboekbestand|  
|--------------|-----------------|----------------------------|  
|easdisc.log|Registreert de activiteiten en de status van de Exchange Server-connector.|Siteserver|  

####  <a name="BKMK_MDLegLog"></a>Verouderde mobiele apparaten  
 De volgende tabel geeft een lijst van de logboekbestanden die informatie bevatten met betrekking tot verouderde clients van mobiele apparaten.  

|Logboeknaam|Beschrijving|Computer met logboekbestand|  
|--------------|-----------------|----------------------------|  
|DmCertEnroll.log|Registreert gegevens over certificaatregistratiegegevens op verouderde clients van mobiele apparaten.|Client|  
|DMCertResp.htm|Registreert het HTML-antwoord van de certificaatserver wanneer het enroller-programma van de verouderde client van mobiele apparaten een PKI-certificaat vraagt.|Client|  
|DmClientHealth.log|Registreert de GUID's van alle verouderde clients van mobiele apparaten die communiceren met het beheerpunt dat is ingeschakeld voor mobiele apparaten.|Sitesysteemserver|  
|DmClientRegistration.log|Registreert registratieverzoeken en antwoorden naar en van verouderde clients van mobiele apparaten.|Sitesysteemserver|  
|DmClientSetup.log|Registreert clientinstellingsgegevens voor verouderde clients voor mobiele apparaten.|Client|  
|DmClientXfer.log|Registreert overdrachtgegevens voor verouderde clients van mobiele apparaten en ActiveSync-implementaties.|Client|  
|DmCommonInstaller.log|Registreert installatie van overdrachtsbestand van client voor het configureren van overdrachtsbestanden voor verouderde clients van mobiele apparaten.|Client|  
|DmInstaller.log|Registreert of DMInstaller een juiste oproep dat naar DmClientSetup en of DmClientSetup met succes afsluit of integendeel faalt voor verouderde clients van mobiele apparaten.|Client|  
|DmpDatastore.log|Registreert alle databaseverbindingen en -query's die gemaakt worden door het distributiepunt dat ingeschakeld is voor mobiele apparaten.|Sitesysteemserver|  
|DmpDiscovery.log|Registreert alle detectiegegevens van de verouderde clients van mobiele apparaten op het beheerpunt dat ingeschakeld is voor mobiele apparaten.|Sitesysteemserver|  
|DmpHardware.log|Registreert hardware-inventarisgegevens van verouderde clients van mobiele apparaten op het beheerpunt dat voor mobiele apparaten is ingeschakeld.|Sitesysteemserver|  
|DmpIsapi.log|Registreert communicatie van verouderde clients van mobiele met een beheerpunt dat is ingeschakeld voor mobiele apparaten.|Sitesysteemserver|  
|dmpmsi.log|Registreert de Windows installergegevens voor de configuratie van een beheerpunt dat is ingeschakeld voor mobiele apparaten.|Sitesysteemserver|  
|DMPSetup.log|Registreert de configuratie van het beheerpunt dat is ingeschakeld voor mobiele apparaten.|Sitesysteemserver|  
|DmpSoftware.log|Registreert software-distributiegegevens van verouderde clients van mobiele apparaten op een beheerpunt dat voor mobiele apparaten is ingeschakeld.|Sitesysteemserver|  
|DmpStatus.log|Registreert statusberichten van clients van mobiele apparaten op een beheerpunt dat voor mobiele apparaten is ingeschakeld.|Sitesysteemserver|  
|DmSvc.log|Registreert clientcommunicatie van verouderde clients van mobiele apparaten met een beheerpunt dat is ingeschakeld voor mobiele apparaten.|Client|  
|FspIsapi.log|Registreert gegevens over communicatie naar een terugvalstatuspunt van verouderde clients van mobiele apparaten en clientcomputers.|Sitesysteemserver|  

###  <a name="BKMK_OSDLog"></a>Implementatie van besturingssysteem  
 De volgende tabel geeft een lijst van de logboekbestanden die informatie bevatten met betrekking tot implementatie van besturingssystemen.  

|Logboeknaam|Beschrijving|Computer met logboekbestand|  
|--------------|-----------------|----------------------------|  
|CAS.log|Registreert gegevens van de records wanneer distributiepunten zijn gevonden voor inhoud waarnaar wordt verwezen.|Client|  
|ccmsetup.log|Registreert ccmsetup taken voor clientinstallatie, Clientupgrade en clientverwijdering. Kan worden gebruikt voor het oplossen van problemen tijdens de installatie van de client.|Client|  
|CreateTSMedia.log|Registreert gegevens voor de taak mediacreatie sequentiëren.|Computer waarop de Configuration Manager-console|  
|DeployToVhd.log|Registreert gegevens over het maken en de wijzigingsopties proces voor virtuele harde schijf (VHD).|Computer waarop de Configuration Manager-console|  
|DISM.log|Registreert Installatieacties of toepassing updatebewerkingen voor offline-installatie.|Sitesysteemserver|  
|Distmgr.log|Registreert gegevens over de configuratie van een distributiepunt inschakelen voor Preboot Execution Environment (PXE).|Sitesysteemserver|  
|DriverCatalog.log|Registreert gegevens over stuurprogramma's voor apparaten die in de stuurprogrammacatalogus werden geïmporteerd.|Sitesysteemserver|  
|mcsisapi.log|Legt Informatie vast voor multicast-pakketoverdracht en antwoorden op client-vragen.|Sitesysteemserver|  
|mcsexec.log|Controleer de acties statuscontrole records, naamruimte, maken sessies en certificaat.|Sitesysteemserver|  
|mcsmgr.log|Registreert wijzigingen aan de configuratie, beveiligingsmodus en beschikbaarheid.|Sitesysteemserver|  
|mcsprv.log|Legt multicast-provider interactie vast met Windows Deployment Services (WDS).|Sitesysteemserver|  
|MCSSetup.log|Registreert gegevens over de installatie van de rol multicastserver.|Sitesysteemserver|  
|MCSMSI.log|Registreert gegevens over de installatie van de rol multicastserver.|Sitesysteemserver|  
|Mcsperf.log|Registreert gegevens over de prestaties van multicast-prestatiemeter-updates.|Sitesysteemserver|  
|MP_ClientIDManager.log|Registreert beheerpuntantwoorden op de takenreeksen voor vragen naar client-ID die geïnitieerd worden door PXE of opstartmedia.|Sitesysteemserver|  
|MP_DriverManager.log|Registreert beheerpuntantwoorden op actieverzoeken van automatisch toepassen-takenreeksen.|Sitesysteemserver|  
|OfflineServicingMgr.log|Registreert gegevens van offline schema's voor onderhoud en update acties van toepassing op Windows Imaging Format (WIM) besturingssysteembestanden.|Sitesysteemserver|  
|Setupact.log|Registreert gegevens over Windows Sysprep en installatielogboeken.|Client|  
|Setupapi.log|Registreert gegevens over Windows Sysprep en installatielogboeken.|Client|  
|Setuperr.log|Registreert gegevens over Windows Sysprep en installatielogboeken.|Client|  
|smpisapi.log|Registreert gegevens over de acties van vastleggen en herstellen van de clientstatus en drempelinformatie.|Client|  
|Smpmgr.log|Registreert gegevens over de resultaten van statuscontroles van statusmigratiepunt en configuratiewijzigingen.|Sitesysteemserver|  
|smpmsi.log|Registreert installatie- en configuratiegegevens over het statusmigratiepunt.|Sitesysteemserver|  
|smpperf.log|Registreert de tellerupdates van de prestatie van het statusmigratiepunt.|Sitesysteemserver|  
|smspxe.log|Registreert gegevens over de antwoorden aan clients die PXE opstarten en gegevens over de uitbreiding van opstartinstallatiekopieën en opstartbestanden.|Sitesysteemserver|  
|smssmpsetup.log|Registreert installatie- en configuratiegegevens over het statusmigratiepunt.|Sitesysteemserver|  
|Smsts.log|Registreert takenreeksactiviteiten.|Client|  
|TSAgent.log|Registreert het resultaat van afhankelijkheden van takenreeks vóór een takenreeks gestart wordt.|Client|  
|TaskSequenceProvider.log|Registreert gegevens over takenreeksen wanneer ze worden geïmporteerd, geëxporteerd of bewerkt.|Sitesysteemserver|  
|Loadstate.log|Registreert gegevens over het hulpprogramma voor de migratie van gebruikersstatus (USMT) en het herstellen van gebruikerstatusgegevens.|Client|  
|Scanstate.log|Registreert gegevens over het hulpprogramma voor de migratie van gebruikersstatus (USMT) en het vastleggen van gebruikerstatusgegevens.|Client|  

###  <a name="BKMK_PowerMgmtLog"></a>Energiebeheer  
 De volgende tabel geeft een lijst van de logboekbestanden die informatie bevatten met betrekking tot energiebeheer.  

|Logboeknaam|Beschrijving|Computer met logboekbestand|  
|--------------|-----------------|----------------------------|  
|pwrmgmt.log|Registreert gegevens over energiebeheeractiviteiten op de clientcomputer, met inbegrip van bewaking en de uitvoering van instelling door de Agent Power Management-Client.|Client|  

###  <a name="BKMK_RCLog"></a>Beheer op afstand  
 De volgende tabel geeft een lijst van de logboekbestanden die informatie bevatten met betrekking tot controle op afstand.  

|Logboeknaam|Beschrijving|Computer met logboekbestand|  
|--------------|-----------------|----------------------------|  
|CMRcViewer.log|Registreert gegevens over de activiteit van beheer op afstand viewer.|In de map % temp % op de computer met de viewer voor beheer op afstand|  

###  <a name="BKMK_ReportLog"></a>Rapportage  
 De volgende tabel geeft een lijst van de Configuration Manager-logboekbestanden die informatie bevatten met betrekking tot rapportage.  

|Logboeknaam|Beschrijving|Computer met logboekbestand|  
|--------------|-----------------|----------------------------|  
|srsrp.log|Registreert informatie over de activiteit en status van het rapportageservicepunt.|Sitesysteemserver|  
|srsrpMSI.log|Registreert gedetailleerde resultaten van het installatieproces van het rapportageservicepunt vanuit de MSI-output.|Sitesysteemserver|  
|srsrpsetup.log|Registreert resultaten van het installatieproces van Reporting Services-punt.|Sitesysteemserver|  

###  <a name="BKMK_RBALog"></a>Op rollen gebaseerd beheer  
 De volgende tabel geeft een lijst van de logboekbestanden die informatie bevatten met betrekking tot het beheren van beheer op basis van rollen.  

|Logboeknaam|Beschrijving|Computer met logboekbestand|  
|--------------|-----------------|----------------------------|  
|hman.log|Registreert informatie over wijzigingen in siteconfiguratie en de publicatie van sitegegevens naar Active Directory Domain Services.|Siteserver|  
|SMSProv.log|Registreert toegang van de WMI-provider tot de sitedatabase.|Computer met de SMS-provider|  

###  <a name="BKMK_WITLog"></a>Het service connection point  
 In de volgende tabel worden de logboekbestanden vermeld die gegevens bevatten die betrekking hebben op het serviceverbindingspunt.  

|Logboeknaam|Beschrijving|Computer met logboekbestand|  
|--------------|-----------------|----------------------------|  
|CertMgr.log|Registreert certificaat- en proxy-accountgegevens.|Siteserver|  
|CollEval.log|Registreert gegevens over wanneer verzamelingen worden gemaakt, gewijzigd en verwijderd door de Verzamelingevaluator.|Primaire site en centrale beheersite|  
|Cloudusersync.log|Registreert inschakelen van licensies voor gebruikers.|Computer met het serviceverbindingspunt|  
|Dataldr.log|Registreert gegevens over de verwerking van MIF-bestanden.|Siteserver|  
|ddm.log|Registreert activiteiten van de Discovery Data Manager.|Siteserver|  
|Distmgr.log|Registreert gegevens over aanvragen voor distributie van inhoud.|Siteserver op het hoogste niveau|  
|Dmpdownloader.log|Registreert gegevens over downloads van Microsoft Intune.|Computer met het serviceverbindingspunt|  
|Dmpuploader.log|Registreert gegevens met betrekking tot het opladen van databasewijzigingen naar Microsoft Intune.|Computer met het serviceverbindingspunt|  
|hman.log|Registreert informatie over het doorsturen van berichten.|Siteserver|  
|objreplmgr.log|Registreert de verwerking van beleid en toewijzing.|Primaire siteserver|  
|PolicyPV.log|Registreert het beleid van het genereren van alle beleidsregels.|Siteserver|  
|outgoingcontentmanager.log|Registreert inhoud geüpload naar Microsoft Intune.|Computer met het serviceverbindingspunt|  
|Sitecomp.log|Hierin worden de gegevens over de installatie van het serviceverbindingspunt vastgelegd.|Siteserver|  
|SmsAdminUI.log|Registreert Configuration Manager-console-activiteit.|Computer waarop de Configuration Manager-console|  
|Smsprov.log|Registreert activiteiten uitgevoerd door de aanbieder van SMS. Configuration Manager-consoleactiviteiten gebruiken de SMS-Provider.|Computer met de SMS-provider|  
|SrvBoot.log|Hierin worden de gegevens over de service met het installatieprogramma voor het serviceverbindingspunt vastgelegd.|Computer met het serviceverbindingspunt|  
|Statesys.log|Registreert de verwerking van berichten voor het beheer van mobiele apparaten.|Primaire site en centrale beheersite|  

###  <a name="BKMK_SU_NAPLog"></a>Software-updates  
 In de volgende tabel worden de logboekbestanden vermeld die gegevens bevatten die betrekking hebben op software-updates.  

|Logboeknaam|Beschrijving|Computer met logboekbestand|  
|--------------|-----------------|----------------------------|  
|ccmperf.log|Registreert activiteiten die betrekking hebben op het onderhoud en vastleggen van gegeven met betrekking tot clientprestatietellers.|Client|  
|PatchDownloader.log|Registreert gegevens over het proces van downloaden van software-updates van de updatebron naar de downloadbestemming op de siteserver.|Computer die als host fungeert voor de Configuration Manager-console van waaruit de downloads worden geïnitieerd|  
|PolicyEvaluator.log|Registreert gegevens over de beoordeling van beleid op clientcomputer, met inbegrip van beleid vanaf software-updates.|Client|  
|RebootCoordinator.log|Registreert gegevens over de coördinatie van het herstarten van systemen op de clientcomputers na de installaties van de software-update.|Client|  
|ScanAgent.log|Registreert gegevens over scanverzoeken voor software-updates, de WSUS-locatie en gerelateerde acties.|Client|  
|SdmAgent.log|Registreert gegevens over het traceren van herstel en compatibiliteit. Het logboekbestand software-updates, Updatehandler.log, levert evenwel meer informatieve gegevens over het installeren van de software-updates die vereist voor naleving zijn.<br /><br /> Dit logboekbestand wordt gedeeld met instellingen voor naleving.|Client|  
|ServiceWindowManager.log|Registreert gegevens over de evaluatie van onderhoudsvensters.|Client|  
|SmsWusHandler.log|Registreert gegevens over het scanproces voor het inventarishulpprogramma voor Microsoft-updates.|Client|  
|StateMessage.log|Registreert gegevens over de software update statusberichten die zijn gemaakt en verzonden naar het beheerpunt.|Client|  
|SUPSetup.log|Registreert gegevens over de installatie van het software-updatepunt. Wanneer de installatie van het software-updatepunt is voltooid, wordt **Installatie is geslaagd** geschreven naar dit logboekbestand.|Sitesysteemserver|  
|UpdatesDeployment.log|Registreert gegevens over implementaties op de client, met inbegrip van software-updateactiviteit, beoordeling en gedwongen uitvoering. Uitgebreide logboekregistratie toont bijkomende informatie over de interactie de clientgebruikersinterface.|Client|  
|UpdatesHandler.log|Registreert gegevens over scannen van naleving van software-update en over het downloaden en de installatie van software-updates op de client.|Client|  
|UpdatesStore.log|Registreert gegevens over nalevingsstatus voor de software-updates die beoordeeld werden tijdens de cyclus van de nalevingsscan.|Client|  
|WCM.log|Registreert gegevens over de software update configuraties en verbindingen met de WSUS-server voor geabonneerde updatecategorieën, classificaties en talen.|Siteserver|  
|WSUSCtrl.log|Registreert gegevens over de configuratie, databaseconnectiviteit en status van de WUS-server voor de site.|Sitesysteemserver|  
|wsyncmgr.log|Registreert gegevens over de software update-synchronisatieproces is.|Siteserver|  
|WUAHandler.log|Registreert gegevens over de Windows Update-agent op de client wanneer hij zoekt naar software-updates.|Client|  

###  <a name="BKMK_WOLLog"></a>Wake On LAN  
 De volgende tabel bevat de logboekbestanden die informatie bevatten met betrekking op het gebruik van Wake On LAN.  

> [!NOTE]  
>  Wanneer u Wake On LAN aanvullen door wake-up proxy, wordt deze activiteit geregistreerd op de client. Zie bijvoorbeeld CcmExec.log en SleepAgent_ <*domein* \> @SYSTEM_0.log in de [clientbewerkingen](#BKMK_ClientOpLogs) sectie van dit onderwerp.  

|Logboeknaam|Beschrijving|Computer met logboekbestand|  
|--------------|-----------------|----------------------------|  
|wolcmgr.log|Registreert gegevens over welke clients ontwaakpakketten moeten toegestuurd krijgen, het aantal te zenden ontwaakpakketten en het aantal van opnieuw geprobeerde ontwaakpakketten.|Siteserver|  
|wolmgr.log|Registreert gegevens over ontwaakprocedures, zoals wanneer implementaties te activeren die geconfigureerd zijn voor Wake On LAN.|Siteserver|  

###  <a name="BKMK_WindowsServicingLog"></a>Onderhoud van Windows 10  
 De volgende tabel bevat de logboekbestanden die informatie over het onderhoud van Windows 10 bevatten.  

|Logboeknaam|Beschrijving|Computer met logboekbestand|  
|--------------|-----------------|----------------------------|  
|ccmperf.log|Registreert activiteiten die betrekking hebben op het onderhoud en vastleggen van gegeven met betrekking tot clientprestatietellers.|Client|  
|CcmRepair.log|Registreert de herstelactiviteiten van de clientagent.|Client|
|PatchDownloader.log|Registreert gegevens over het proces van downloaden van software-updates van de updatebron naar de downloadbestemming op de siteserver.|Computer die als host fungeert voor de Configuration Manager-console van waaruit de downloads worden geïnitieerd|  
|PolicyEvaluator.log|Registreert gegevens over de beoordeling van beleid op clientcomputer, met inbegrip van beleid vanaf software-updates.|Client|  
|RebootCoordinator.log|Registreert gegevens over de coördinatie van het herstarten van systemen op de clientcomputers na de installaties van de software-update.|Client|  
|ScanAgent.log|Registreert gegevens over scanverzoeken voor software-updates, de WSUS-locatie en gerelateerde acties.|Client|  
|SdmAgent.log|Registreert gegevens over het traceren van herstel en compatibiliteit. Het logboekbestand software-updates, Updatehandler.log, levert evenwel meer informatieve gegevens over het installeren van de software-updates die vereist voor naleving zijn.<br /><br /> Dit logboekbestand wordt gedeeld met instellingen voor naleving.|Client|  
|ServiceWindowManager.log|Registreert gegevens over de evaluatie van onderhoudsvensters.|Client|  
|Setupact.log|Primaire logboekbestand voor de meeste fouten die tijdens de installatie van Windows optreden. Het logboekbestand bevindt zich in de map % windir %\$Windows.~BT\sources\panther map.|Client|
|SmsWusHandler.log|Registreert gegevens over het scanproces voor het inventarishulpprogramma voor Microsoft-updates.|Client|  
|StateMessage.log|Registreert gegevens over statusberichten over software-updates die gemaakt worden en naar het beheerpunt worden gezonden.|Client|  
|SUPSetup.log|Registreert gegevens over de installatie van het software-updatepunt. Wanneer de installatie van het software-updatepunt is voltooid, wordt **Installatie is geslaagd** geschreven naar dit logboekbestand.|Sitesysteemserver|  
|UpdatesDeployment.log|Registreert gegevens over implementaties op de client, met inbegrip van software-updateactiviteit, beoordeling en gedwongen uitvoering. Uitgebreide logboekregistratie toont bijkomende informatie over de interactie de clientgebruikersinterface.|Client|  
|Updatehandler.log|Registreert gegevens over scannen van naleving van software-update en over het downloaden en de installatie van software-updates op de client.|Client|  
|UpdatesStore.log|Registreert gegevens over nalevingsstatus voor de software-updates die beoordeeld werden tijdens de cyclus van de nalevingsscan.|Client|  
|WCM.log|Registreert gegevens over de software update configuraties en verbindingen met de WSUS-server voor geabonneerde updatecategorieën, classificaties en talen.|Siteserver|  
|WSUSCtrl.log|Registreert gegevens over de configuratie, databaseconnectiviteit en status van de WUS-server voor de site.|Sitesysteemserver|  
|wsyncmgr.log|Registreert gegevens over de software update-synchronisatieproces is.|Siteserver|  
|WUAHandler.log|Registreert gegevens over de Windows Update-agent op de client wanneer hij zoekt naar software-updates.|Client|  

###  <a name="BKMK_WULog"></a>Windows Update Agent  
 De volgende tabel geeft een lijst van de logboekbestanden die informatie bevatten met betrekking tot de Windows Update-agent.  

|Logboeknaam|Beschrijving|Computer met logboekbestand|  
|--------------|-----------------|----------------------------|  
|WindowsUpdate.log|Registreert gegevens over wanneer de Windows Update Agent verbindt met de WSUS-server en software-updates voor beoordeling van naleving, haalt en of er updates beschikbaar voor de agentonderdelen zijn.|Client|  

###  <a name="BKMK_WSUSLog"></a>WSUS-server  
 De volgende tabel geeft een lijst van de logboekbestanden die informatie bevatten met betrekking tot de WSUS-server.  

|Logboeknaam|Beschrijving|Computer met logboekbestand|  
|--------------|-----------------|----------------------------|  
|Change.log|Registreert gegevens over de WSUS-server database-informatie die is gewijzigd.|WSUS-server|  
|SoftwareDistribution.log|Registreert gegevens over de software-updates die worden gesynchroniseerd vanuit de geconfigureerde updatebron naar de WSUS-server-database.|WSUS-server|  

