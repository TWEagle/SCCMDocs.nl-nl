---
title: Hotfix-installatieprogramma | Microsoft-documenten
description: Ontdek wanneer en hoe u updates via de Hotfix-installatieprogramma voor Configuration Manager te installeren.
ms.custom: na
ms.date: 10/06/2016
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: f3058277-c597-4dac-86d1-41b6f7e62b36
caps.latest.revision: 9
author: Brenduns
ms.author: brenduns
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 10b1010ccbf3889c58c55b87e70b354559243c90
ms.openlocfilehash: 8ffc7383e895909e6e6c4b8a7875fd5f0df2220e
ms.contentlocale: nl-nl
ms.lasthandoff: 05/17/2017


---
# <a name="use-the-hotfix-installer-to-install-updates-for-system-center-configuration-manager"></a>Het installatieprogramma voor hotfixes gebruiken om updates te installeren voor System Center Configuration Manager

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*

Sommige updates voor System Center Configuration Manager zijn niet beschikbaar is via het Microsoft-cloudservice en out-of-band alleen worden verkregen. Een voorbeeld is een beperkt uitgegeven hotfix voor een specifiek probleem.   
Wanneer u een update (of hotfix) die u van Microsoft ontvangt moet installeren en update is een bestandsnaam eindigt met de extensie **.exe** (niet **update.exe**), u het hotfixinstallatieprogramma die is opgenomen in deze hotfix-download de update installeren rechtstreeks naar de siteserver van Configuration Manager gebruiken.  

 Als het hotfixbestand de bestandsextensie **.update.exe** heeft, raadpleegt u [Gebruik het hulpprogramma Registratie bijwerken om hotfixes te importeren naar System Center Configuration Manager](../../../core/servers/manage/use-the-update-registration-tool-to-import-hotfixes.md).  

> [!NOTE]  
>  In dit onderwerp biedt algemene richtlijnen over het installeren van hotfixes om System Center Configuration Manager bij te werken. Raadpleeg voor meer informatie over specifieke updates het betreffende Knowledge Base-artikel op Microsoft Ondersteuning.  

##  <a name="bkmk_Overview"></a>Overzicht van hotfixes voor Configuration Manager  
 Hotfixes voor Configuration Manager zijn vergelijkbaar met die voor andere Microsoft-producten, zoals SQL Server een afzonderlijke fix of een bundel (een updatepakket) bevatten en worden beschreven in de Microsoft Knowledge Base-artikel.  

 Afzonderlijke updates bevatten één gerichte update voor een specifieke versie van Configuration Manager.  
Updatebundels bevatten meerdere updates voor een specifieke versie van Configuration Manager.  
Als een update als bundel wordt aangeboden, kunt u geen afzonderlijke updates uit die bundel installeren.  

 Als u echter implementaties wilt maken om updates op extra computers te installeren, moet u de updatebundel installeren op de server van een centrale beheersite of op een primaire siteserver.  

 Wanneer u de updatebundel uitvoert, gebeurt het volgende:  

-   De updatebestanden voor elk toepasselijk onderdeel van de updatebundel worden uitgepakt.  

-   Er wordt een wizard gestart die u door het configuratieproces en de implementatieopties voor de updates leidt.  

-   Zodra u de wizard hebt voltooid, worden de updates in de bundel die van toepassing is op siteserver geïnstalleerd op de betreffende siteserver.  

De wizard maakt ook implementaties die u kunt gebruiken voor de installatie van updates op extra computers. U kunt de updates op aanvullende computers implementeren met een ondersteunde implementatiemethode, zoals een software-implementatiepakket of Microsoft System Center Updates Publisher 2011.  

 Wanneer de wizard wordt uitgevoerd, wordt een **CAB** -bestand gemaakt op de siteserver dat kan worden gebruikt met Updates Publisher 2011. Eventueel kunt u de wizard ook zodanig configureren dat er één of meer pakketten worden gemaakt voor software-implementatie. U kunt deze implementaties gebruiken om updates te installeren op onderdelen, zoals clients of de Configuration Manager-console. U kunt updates ook handmatig installeren op computers waarop de Configuration Manager-client niet wordt uitgevoerd.  

 De volgende drie groepen in Configuration Manager kunnen worden bijgewerkt:  

-   Configuration Manager-serverfuncties, waaronder:  

    -   Centrale beheersite  

    -   Primaire site  

    -   Secundaire site  

    -   Externe SMS-provider  

-   Configuration Manager-console  

-   Configuration Manager-client  

> [!NOTE]  
>  **Updates voor sitesysteemrollen** (inclusief updates voor de sitedatabase en de clouddistributiepunten) worden geïnstalleerd als onderdeel van de update voor siteservers en services van de Site Component Manager.  
>   
>  Updates pull-distributiepunten worden echter afgehandeld door Distributiebeheer in plaats van de site-onderdeelbeheer.  

 Iedere updatebundel voor Configuration Manager is een zelfuitpakkend .exe-bestand (SFX) dat de bestanden die nodig zijn bevat voor de update installeren op de toepasselijke componenten van Configuration Manager. Het SFX-bestand kan normaal gesproken de volgende bestanden bevatten:  

|Bestand|Details|  
|----------|-------------|  
|&lt;Productversie\>- QFE KB&lt;KB-artikel-ID\>-&lt;platform\>-&lt;taal\>.exe|Dit is het updatebestand. De opdrachtregel voor dit bestand wordt beheerd door Updatesetup.exe.<br /><br /> Bijvoorbeeld:<br />CM1511RTM-QFE-KB123456-X 64-ENU.exe|  
|Updatesetup.exe|Deze MSI-wrapper beheert de installatie van de updatebundel.<br /><br /> Wanneer u de update uitvoert, detecteert Updatesetup.exe de weergavetaal van de computer waarop hij wordt uitgevoerd. De gebruikersinterface voor de update is standaard in het Engels. Wanneer de weergavetaal echter wordt ondersteund, geeft de gebruikersinterface inhoud in de lokale taal van de computer weer.|  
|License_&lt;taal\>.rtf|Wanneer van toepassing bevat iedere update een of meerdere licentiebestanden voor ondersteunde talen.|  
|&lt;Product & updatetype >-&lt;productversie\>-&lt;KB-artikel-ID\>-&lt;platform\>.msp|Wanneer de update voor de Configuration Manager-console of de clients geldt, bevat de updatebundel afzonderlijke Windows Installer-patch (.msp) bestanden.<br /><br /> Bijvoorbeeld:<br /><br /> **Configuration Manager-console-update:** ConfigMgr1511 AdminUI-KB1234567 i386.msp<br /><br /> **Client-update:** ConfigMgr1511 client-KB1234567 i386.msp<br />ConfigMgr1511 client-KB1234567 x64.msp|  

 De updatebundel registreert standaard zijn bewerkingen in een logboekbestand op de siteserver. Het logboekbestand heeft dezelfde naam als de updatebundel en wordt naar de map **%SystemRoot%/Temp** geschreven.  

 Wanneer u de updatebundel uitvoert, pakt deze een bestand uit met dezelfde naam als de updatebundel in een tijdelijke map op de computer en voert Updatesetup.exe uit. Updatesetup.exe start de Software-Update voor Configuration Manager &lt;productversie\> &lt;KB-nummer\> Wizard.  

 Indien van toepassing op het bereik van de update, de wizard maakt een aantal mappen aan onder de System Center Configuration Manager-installatiemap op de siteserver. De mapstructuur lijkt op het volgende:   
 **\\\\&lt;Server Name\>\SMS_&lt;Site Code\>\Hotfix\\&lt;KB Number\>\\&lt;Update Type\>\\&lt;Platform\>**.  

 De volgende tabel biedt details over de mappen in de mapstructuur:  

|Mapnaam|Meer informatie|  
|-----------------|----------------------|  
|&lt;Servernaam\>|Dit is de naam van de siteserver waar u de updatebundel uitvoert.|  
|SMS_&lt;sitecode\>|Dit is de sharenaam van de Configuration Manager-installatiemap.|  
|&lt;KB-nummer\>|Dit is het ID-nummer van het Knowledge Base-artikel voor deze updatebundel.|  
|&lt;Update-type\>|Dit zijn de soorten updates voor Configuration Manager. De wizard maakt een afzonderlijke map aan voor ieder soort update in de updatebundel. De mapnamen staan voor de update-typen. Ze bevatten het volgende:<br /><br /> **Server**: Bevat updates voor siteservers, sitedatabaseservers en computers waarop de SMS-Provider wordt uitgevoerd.<br /><br /> **Client**: Bevat updates voor Configuration Manager-client.<br /><br /> **AdminConsole**: Bevat updates voor de Configuration Manager-console<br /><br /> Naast de update-typen hierboven wordt met de wizard nog een map met de naam **SCUP** gemaakt. Deze map staat niet voor een type update, maar bevat het CAB-bestand voor Updates Publisher.|  
|&lt;Platform\>|Dit is een platform-specifieke map. Deze bevat update-bestanden die specifiek zijn voor een type processor.  Deze mappen bevatten onder andere:<br /><br />-x64<br /><br /> -I386|  

##  <a name="bkmk_Install"></a> Updates installeren  
 Voor de installatie van updates moet u eerst de updatebundel installeren op een siteserver. Wanneer u een updatebundel installeert, wordt er een installatiewizard gestart voor die update. Deze wizard doet het volgende:  

-   De updatebestanden uitpakken  

-   Helpen bij de configuratie van implementaties  

-   De betreffende updates op de serveronderdelen van de lokale computer installeren  

Nadat u de updatebundel op een siteserver installeert, u kunt extra onderdelen bijwerken voor Configuration Manager. In de volgende tabel staan updatebewerkingen voor deze verschillende onderdelen:  

|Component|Instructies|  
|---------------|------------------|  
|Siteserver|Implementeer updates op een externe siteserver wanneer u de updatebundel niet direct op die externe siteserver wilt installeren.|  
|Sitedatabase|Implementeer voor externe siteservers die serverupdates die een update bevatten van de sitedatabase als u de updatebundel niet direct op die externe siteserver installeert.|  
|Configuration Manager-console|Na de eerste installatie van de Configuration Manager-console kunt u updates voor de Configuration Manager-console installeren op elke computer die de console wordt uitgevoerd. U kunt de installatiebestanden van de Configuration Manager-console om de updates toepassen tijdens de eerste installatie van de console niet wijzigen.|  
|Externe SMS-provider|Installeer updates voor ieder exemplaar van de SMS-provider dat op een computer wordt uitgevoerd die niet de siteserver is waar u de updatebundel hebt geïnstalleerd.|  
|Configuration Manager-clients|U kunt na de eerste installatie van de Configuration Manager-client updates installeren voor de Configuration Manager-client op elke computer die de client uitvoert.|  

> [!NOTE]  
>  U kunt updates alleen implementeren op computers waarop de Configuration Manager-client wordt uitgevoerd.  

 Als u een client, Configuration Manager-console of SMS-Provider installeert, moet u ook de updates voor deze onderdelen opnieuw installeren.  

 Gebruik de informatie in de volgende rubrieken om updates te installeren op elk van de onderdelen voor Configuration Manager.  

###  <a name="bkmk_servers"></a> Updateservers  
 Updates voor servers kunnen updates zijn voor **sites**, de **site database**en computers waarop een instantie van de **SMS-provider**wordt uitgevoerd:  

####  <a name="bkmk_site"></a>Een site bijwerken  
 Voor het bijwerken van een Configuration Manager-site, kunt u de updatebundel direct op de siteserver installeren of u kunt de updates implementeren op een siteserver nadat u de updatebundel op een andere site installeert.  

 Als u een update installeert op een siteserver, beheert het update-installatieproces aanvullende bewerkingen die nodig zijn om de update toe te passen, zoals het bijwerken van sitesysteemrollen. De uitzondering hierop is de sitedatabase. De volgende rubrieken bevatten informatie over hoe u de sitedatabase kunt bijwerken.  

####  <a name="bkmk_database"></a>Bijwerken van een sitedatabase  
 Voor het bijwerken van de sitedatabase, voert het installatieproces een bestand met de naam **update.sql** uit op de sitedatabase. U kunt het updateproces instellen op het automatisch bijwerken van de sitedatabase of u kunt dit later zelf handmatig doen.  

 **Automatische Update van de sitedatabase**  

 Wanneer u de updatebundel op een siteserver installeert, kunt u de sitedatabase automatisch laten bijwerken wanneer de serverupdate wordt geïnstalleerd. Dit geldt alleen voor de siteserver waarop u de updatebundel installeert en geldt niet voor implementaties die zijn gemaakt voor het installeren van de updates op externe siteservers.  

> [!NOTE]  
>  Als u de sitedatabase automatisch laten bijwerken kiest, werkt het proces een database ongeacht of de database zich bevindt op de siteserver of op een externe computer.  

> [!IMPORTANT]  
>  Maak voordat u de sitedatabase bijwerkt een back-up van de sitedatabase. U kunt een update van de sitedatabase niet verwijderen. Zie voor meer informatie over het maken van een back-up voor Configuration Manager [back-up en herstel voor System Center Configuration Manager](../../../protect/understand/backup-and-recovery.md).  

 **Handmatige update van de sitedatabase**  

 Als u ervoor kiest de sitedatabase niet automatisch te laten bijwerken wanneer u de updatebundel installeert op de siteserver, wijzigt de serverupdate de database op de siteserver waarop de updatebundel wordt uitgevoerd niet. Echter bijwerken die gebruikmaken van het pakket dat is gemaakt voor software-implementatie of die altijd installeert de sitedatabase.  

> [!WARNING]  
>  Wanneer de update updates bevat voor zowel de siteserver als de sitedatabase, is de update niet functioneel totdat de update is voltooid voor zowel de siteserver als de sitedatabase. De site wordt niet ondersteund totdat de update wordt toegepast op de sitedatabase.  

 **Een sitedatabase handmatig bijwerken:**  

1.  De SMS site Component Manager-service te stoppen op de siteserver en vervolgens de SMS_EXECUTIVE-service stoppen.  

2.  Sluit de Configuration Manager-console.  

3.  Voer het updatescript **update.sql** uit op de database van die site. Zie de documentatie voor de versie van SQL Server die u voor de databaseserver van uw site gebruikt voor meer informatie over het uitvoeren van een script voor het bijwerken van een SQL Server-database.  

4.  Start de services die in de vorige stappen zijn gestopt.  

5.  Wanneer de updatebundel is geïnstalleerd, pakt deze **update.sql** naar de volgende locatie op de siteserver:  **\\\\&lt;Servernaam\>\SMS_&lt;sitecode\>\Hotfix\\&lt;KB-nummer\>\update.sql**  

####  <a name="bkmk_provider"></a>Een computer bijwerken waarop de SMS-Provider  
 Wanneer u een updatebundel installeert met updates voor de SMS-provider, moet u de update voor elke computer implementeren waarop de SMS-provider draait. De enige uitzondering hierop is het exemplaar van de SMS-provider dat voorheen op de siteserver was geïnstalleerd, waarop u de updatebundel installeert. Het lokale exemplaar van de SMS-Provider op de siteserver wordt bijgewerkt wanneer u de updatebundel installeert.  

 Als u de SMS-provider eerst verwijdert en opnieuw installeert op een computer, moet u de update voor de SMS-provider op die computer opnieuw installeren.  

###  <a name="BKMK_clients"></a>Clients bijwerken  
 Wanneer u een update met updates voor Configuration Manager-client installeert, wordt de optie voor werkt automatisch clients bij met de installatie van updates of clients handmatig bijwerken op een later tijdstip weergegeven. Zie [How to upgrade clients for Windows computers](https://technet.microsoft.com/library/mt627885.aspx)bijwerken.  

 U kunt updates implementeren met Updates Publisher of een software-implementatiepakket. Ook kunt u ervoor kiezen om een update handmatig op elke client te installeren. Zie de sectie [Updates implementeren voor Configuration Manager](#BKMK_Deploy) in dit onderwerp voor meer informatie over het gebruik van implementaties voor het installeren van updates.  

> [!IMPORTANT]  
>  Wanneer u updates voor clients installeert en de updatebundel updates voor servers bevat, moet u ook de om serverupdates te installeren op de primaire site waaraan de clients zijn toegewezen.  

U moet uitvoeren om de clientupdate handmatig installeren op elke client Configuration Manager, **Msiexec.exe** en verwijzen naar het .msp-bestand platform-specifieke clientupdate.  

 U kunt bijvoorbeeld de volgende opdrachtregel gebruiken voor een clientupdate. Met deze opdrachtregel wordt MSIEXEC op de clientcomputer uitgevoerd en wordt aan het MSP-bestand dat de updatebundel op de siteserver heeft uitgepakt: **msiexec.exe /p \\ \\ &lt;ServerName\>\SMS_&lt;SiteCode\>\Hotfix\\&lt;KB-nummer\>\Client\\&lt;Platform\>\\&lt;msp\> /L\*v &lt;logfile\>REINSTALLMODE = MOU opnieuw installeren = ALL**  

###  <a name="BKMK_console"></a>Configuration Manager-consoles bijwerken  
 Voor het bijwerken van een Configuration Manager-console, moet u de update installeren op de computer waarop de console wordt uitgevoerd nadat de installatie van de console is voltooid.  

> [!IMPORTANT]  
>  Wanneer u updates voor de Configuration Manager-console installeert en de updatebundel updates voor servers bevat, moet u ook de om serverupdates te installeren op de site die u met de Configuration Manager-console gebruikt.  

Als de computer die u wilt bijwerken, de Configuration Manager-client voert:  

-   u kunt een implementatie gebruiken om de update te installeren. Zie de sectie [Updates implementeren voor Configuration Manager](#BKMK_Deploy) in dit onderwerp voor meer informatie over het gebruik van implementaties voor het installeren van updates.  

-   Als u zich hebt aangemeld op de clientcomputer, kunt u de installatie interactief uitvoeren.  

-   U kunt handmatig de update installeren op elke computer. Om handmatig de update van de console Configuration Manager installeren op elke computer waarop de Configuration Manager-console wordt uitgevoerd, kunt u Msiexec.exe uitvoeren en verwijzen naar de Configuration Manager console .msp-bestand.  

U kunt bijvoorbeeld de volgende opdrachtregel bijwerken van een Configuration Manager-console. Deze opdrachtregel wordt MSIEXEC op de computer wordt uitgevoerd en wordt aan het MSP-bestand dat de updatebundel op de siteserver heeft uitgepakt: **msiexec.exe /p \\ \\ &lt;ServerName\>\SMS_&lt;SiteCode\>\Hotfix\\&lt;KB-nummer\>\AdminConsole\\&lt;Platform\>\\&lt;msp\> /L\*v &lt;logfile\>REINSTALLMODE = MOU opnieuw installeren = ALL**  

##  <a name="BKMK_Deploy"></a> Updates implementeren voor Configuration Manager  
 Wanneer u de updatebundel op een siteserver installeert, kunt u een van de volgende drie methoden gebruiken om updates te implementeren op extra computers.  

###  <a name="BKMK_DeploySCUP"></a>Updates Publisher 2011 gebruiken om updates te installeren  
 Wanneer u de updatebundel op een siteserver installeert, maakt de installatiewizard een catalogusbestand aan voor Updates Publisher dat u kunt gebruiken om de updates op de toepasselijke computers te implementeren. De wizard maakt deze catalogus altijd, zelfs wanneer u de optie **Pakket en programma gebruiken om deze update te implementeren**bijwerken.  

 De catalogus voor Updates Publisher heet **SCUPCatalog.cab** en vindt u in de volgende locatie op de computer waarop de updatebundel wordt uitgevoerd: **\\\\&lt;ServerName\>\SMS_&lt;SiteCode\>\Hotfix\\&lt;KB-nummer\>\SCUP\SCUPCatalog.cab**  

> [!IMPORTANT]  
>  Omdat het bestand SCUPCatalog.cab wordt gemaakt door gebruik te maken van paden die specifiek zijn voor de siteserver waarop de updatebundel is geïnstalleerd, kan het niet op andere siteservers worden gebruikt.  

 Nadat de wizard voltooid is, kunt u de catalogus importeren in Updates Publisher, en vervolgens met Configuration Manager-software-updates de updates implementeren. Zie voor meer informatie over Updates Publisher [Updates Publisher 2011](http://go.microsoft.com/fwlink/p/?LinkID=83449) in de TechNet library voor System Center 2012.  

 Gebruik de volgende procedure het bestand SCUPCatalog.cab importeren in Updates Publisher en de updates publiceren.  

##### <a name="to-import-the-updates-to-updates-publisher-2011"></a>De updates importeren in Updates Publisher 2011  

1.  Start de Updates Publisher-console en klikt u op **importeren**.  

2.  Op de **importtype** pagina van de Software-Updates Wizard Catalogus importeren, selecteert u **het pad opgeven naar de te importeren catalogus**, en geef vervolgens het bestand SCUPCatalog.cab.  

3.  Klik op **volgende**, en klik vervolgens op **volgende** opnieuw.  

4.  Klik in het dialoogvenster **Beveiligingswaarschuwing - Validatie catalogus** op **Accepteren**. Sluit de wizard nadat deze is voltooid.  

5.  In de console Updates Publisher, selecteert u de update die u wilt implementeren en klik vervolgens op **publiceren**.  

6.  Op de **opties publiceren** pagina van de Software-Updates Wizard publiceren, selecteer **volledige inhoud**, en klik vervolgens op **volgende**.  

7.  Voer de wizard uit om de updates te publiceren.  

###  <a name="BKMK_DeploySWDist"></a>Software-implementatie gebruiken om updates te installeren  
 Wanneer u de updatebundel op de siteserver van een primaire site of een centrale beheersite installeert, kunt u de installatiewizard configureren om updatepakketten te maken voor software-implementatie. U kunt vervolgens elk pakket implementeren op een verzameling van computers die u wilt bijwerken.  

 Als u een software-implementatiepakket wilt maken, schakelt u op de pagina **Implementatie software-update configureren** van de wizard het selectievakje in voor elk updatepakkettype dat u wilt bijwerken. De beschikbare typen kunnen onder meer servers, Configuration Manager-consoles en clients. Er wordt een apart pakket gemaakt voor ieder soort update die u selecteert.  

> [!NOTE]  
>  Het pakket voor servers bevat updates voor de volgende onderdelen:  
>   
>  -   Siteserver  
>  -   SMS-provider  
>  -   Sitedatabase  

 Daarna selecteert u op de pagina **Implementatiemethode software-updates configureren** van de wizard de optie **Ik gebruik softwaredistributie**. Deze selectie stelt de wizard om de software-implementatiepakketten te maken.  

 Nadat de wizard voltooid is, ziet u de pakketten die wordt gemaakt in de Configuration Manager-console in de **pakketten** knooppunt in de **softwarebibliotheek** werkruimte. Vervolgens kunt u het standaardproces softwarepakketten implementeren in Configuration Manager-clients. Wanneer een pakket wordt uitgevoerd op een client, worden de updates geïnstalleerd voor de toepasselijke componenten van Configuration Manager op de clientcomputer.  

 Zie voor meer informatie over het implementeren van pakketten naar Configuration Manager-clients [pakketten en programma's in System Center Configuration Manager](../../../apps/deploy-use/packages-and-programs.md).  

###  <a name="BKMK_DeployCollections"></a>Maken van verzamelingen voor het implementeren van updates voor Configuration Manager  
 U kunt specifieke updates implementeren naar toepasselijke clients. De volgende informatie kunt u apparaatverzamelingen maken voor de verschillende onderdelen voor Configuration Manager.  

|Component van Configuration Manager|Instructies|  
|----------------------------------------|------------------|  
|Server centrale beheersite|Maak een directe lidmaatschapquery en voeg de servercomputer van de centrale beheersite toe.|  
|Alle primaire siteservers|Maak een directe lidmaatschapquery en voeg de servercomputer van elke primaire site toe.|  
|Alle secundaire siteservers|Maak een directe lidmaatschapquery en voeg de servercomputer van elke secundaire site toe.|  
|Alle x 86-clients|Maak een verzameling met de volgende querycriteria:<br /><br /> **Selecteer \* van SMS_R_System inner join SMS_G_System_SYSTEM op SMS_G_System_SYSTEM. ResourceID = SMS_R_System.ResourceId waarbij SMS_G_System_SYSTEM. SystemType = "X86-based PC"**|  
|Alle x 64-clients|Maak een verzameling met de volgende querycriteria:<br /><br /> **Selecteer \* van SMS_R_System inner join SMS_G_System_SYSTEM op SMS_G_System_SYSTEM. ResourceID = SMS_R_System.ResourceId waarbij SMS_G_System_SYSTEM. SystemType = "X64-based PC"**|  
|Alle computers waarop de Configuration Manager-console wordt uitgevoerd|Maak een directe lidmaatschapquery en voeg elke computer toe.|  
|Externe computers waarop een exemplaar van de SMS-provider wordt uitgevoerd|Maak een directe lidmaatschapquery en voeg elke computer toe.|  

> [!NOTE]  
>  Implementeer de update op de siteserver van de site voor het bijwerken van een sitedatabase.  

 Zie [Verzamelingen maken in Configuration Manager](../../../core/clients/manage/collections/create-collections.md) voor meer informatie over het maken van verzamelingen.  

