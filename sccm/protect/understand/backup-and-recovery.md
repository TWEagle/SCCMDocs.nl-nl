---
title: Back-up en herstel | Microsoft-documenten
description: Leer een back-up en herstellen van uw sites in het geval van storing of gegevensverlies in System Center Configuration Manager.
ms.custom: na
ms.date: 3/27/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: f7832d83-9ae2-4530-8a77-790e0845e12f
caps.latest.revision: 22
author: Brenduns
ms.author: brenduns
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: dab5da5a4b5dfb3606a8a6bd0c70a0b21923fff9
ms.openlocfilehash: ea6668ee7ee6b209b659426a0dc2c0be605ceaf1
ms.contentlocale: nl-nl
ms.lasthandoff: 05/17/2017

---

# <a name="backup-and-recovery"></a>Back-up en herstel

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*

Bereid back-up en herstel strategieën om gegevensverlies te voorkomen. Voor Configuration Manager-sites kunt een back-up en herstel benadering sneller en met een miniem herstellen van sites en hiërarchieën. De secties in dit onderwerp kunnen u back-up van uw sites en herstellen van een site in het geval van storing of gegevensverlies.  



- [Back-up van een Configuration Manager-site](#BKMK_SiteBackup)   

  - [Back-uponderhoudstaak](#BKMK_BackupMaintenanceTask)   

  - [Data Protection Manager gebruiken om een back-up te maken van uw sitedatabase](#BKMK_DPMBackup)   

  -  [Archiveren van de back-upmomentopname](#BKMK_ArchivingBackupSnapshot)   

  -  [Het bestand AfterBackup.bat gebruiken](#BKMK_UsingAfterBackup)   

  -  [Aanvullende back-uptaken](#BKMK_SupplementalBackup)   

-  [Een Configuration Manager-site herstellen](#BKMK_RecoverSite)   

  -   [Uw herstelopties bepalen](#BKMK_DetermineRecoveryOptions)   

         -   [Opties voor herstel van de siteserver](#BKMK_SiteServerRecoveryOptions)   

         -   [Opties voor herstel van de sitedatabase](#BKMK_SiteDatabaseRecoveryOption)   

         -   [Bewaarperiode voor het bijhouden van wijzigingen van de SQL Server](#bkmk_SQLretention)   

         -   [Proces om site- of algemene gegevens opnieuw te initialiseren](#bkmk_reinit)   

         -   [Scenario's voor het herstel van een sitedatabase](#BKMK_SiteDBRecoveryScenarios)  

  -   [Scriptbestandsleutels voor herstel van sites zonder toezicht](#BKMK_UnattendedSiteRecoveryKeys)  

  -   [Taken na herstel](#BKMK_PostRecovery)  

  -   [Een secundaire site herstellen](#BKMK_RecoverSecondarySite)  

-   [SMS Writer-service](#BKMK_SMSWriterService)  

> [!NOTE]  
>  Als u een SQL Server AlwaysOn-beschikbaarheidsgroep gebruikt om de sitedatabase te hosten, uw plannen voor back-up en herstel aanpassen zoals beschreven in de [wijzigingen voor back-up en herstel wanneer u een SQL Server AlwaysOn-beschikbaarheidsgroep](../../core/servers/deploy/configure/sql-server-alwayson-for-a-highly-available-site-database.md#bkmk_BnR) sectie van de [SQL Server AlwaysOn van een maximaal beschikbare sitedatabase voor System Center Configuration Manager](../../core/servers/deploy/configure/sql-server-alwayson-for-a-highly-available-site-database.md) onderwerp.  

##  <a name="BKMK_SiteBackup"></a> Back-up van een Configuration Manager-site  
 Configuration Manager beschikt over een back-onderhoud die taak:  

-   Volgens een planning wordt uitgevoerd  

-   Een back-up maakt van de sitedatabase  

-   Een back-up maakt van specifieke registersleutels  

-   Een back-up maakt van specifieke mappen en bestanden  

-   Maakt een back-up van de map **CD.Latest** (zie [De map CD.Latest voor System Center Configuration Manager](../../core/servers/manage/the-cd.latest-folder.md))  

 Plan om de standaardback-uptaak voor de site minimaal elke vijf dagen uit te voeren. Dit komt doordat de Configuration Manager maakt gebruik van een [bewaarperiode voor bijhouden van SQL Server](#bkmk_SQLretention) periode van 5 dagen.  

 Het back-upproces vereenvoudigen, kunt u een **AfterBackup.bat** -bestand naar het uitvoeren van automatisch nadat de onderhoudstaak back-up wordt uitgevoerd. Het AfterBackup.bat-bestand wordt meestal gebruikt om de momentopname van de back-up naar een veilige locatie. U kunt het AfterBackup.bat-bestand ook gebruiken om te kopiëren van bestanden naar uw back-upmap en andere, aanvullende back-uptaken te beginnen.

Gebruik de volgende secties voor hulp bij het maken van de Configuration Manager-back-upstrategie.  

> [!NOTE]  
>  Configuration Manager kan de sitedatabase herstellen vanuit back-up onderhoudstaak van de Configuration Manager of vanuit een site databaseback-up die u hebt gemaakt met een ander proces. U kunt bijvoorbeeld de sitedatabase herstellen vanuit een back-up die is gemaakt als onderdeel van een Microsoft SQL Server-onderhoudsplan. U kunt de sitedatabase herstellen vanuit een back-up die is gemaakt met behulp van System Center 2012 Data Protection Manager (DPM). Zie [Data Protection Manager gebruiken om een back-up te maken van uw sitedatabase](#BKMK_DPMBackup)voor meer informatie.  

###  <a name="BKMK_BackupMaintenanceTask"></a> Back-uponderhoudstaak  
 U kunt back-up voor Configuration Manager-sites automatiseren door het plannen van de vooraf gedefinieerde onderhoudstaak voor back-upserver van Site. U kunt een back-up maken van een centrale beheersite en primaire site, maar niet van secundaire sites of sitesysteemservers. Wanneer de Configuration Manager Backup-service wordt uitgevoerd, volgt de instructies die zijn gedefinieerd in het back-upcontrolebestand (**&lt;ConfigMgrInstallationFolder\>\Inboxes\Smsbkup.box\Smsbkup.ctl**). U kunt het back-upcontrolebestand aanpassen om het gedrag van de back-upservice te wijzigen. Informatie voor siteback-upstatus wordt geschreven naar het bestand **Smsbkup.log** . Het bestand wordt gemaakt in de doelmap die u specificeert in de eigenschappen van de onderhoudstaak van de back-upserver van site.  


##### <a name="to-enable-the-site-backup-maintenance-task"></a>De onderhoudstaak van de back-upserver van site inschakelen  

1.  Open in de Configuration Manager-console **beheer** > **siteconfiguratie**  

     \> **Sites**.  

2.  Selecteer de site waarin u de onderhoudstaak van de back-upserver van site wilt inschakelen.  

3.  Op de **Start** tabblad, in de **instellingen** groep, kiest u **Siteonderhoudstaken**.  

4.  Kies **back-upserver van Site**  >  **bewerken**.  

5.  Kies **deze taak inschakelen** > **paden instellen** om de back-updoelmap te specificeren. U hebt de volgende opties:  

    > [!IMPORTANT]  
    >  Sla ter voorkoming van knoeien met de back-upbestanden deze op een veilige locatie op. Het veiligste back-uppad is naar een lokaal station zodat u machtigingen voor het NTFS-bestandssysteem kunt instellen op de map. Configuration Manager heeft de back-upgegevens die is opgeslagen in het back-uppad niet versleutelen.  

    -   **Lokaal station op siteserver voor sitegegevens en database**: Hiermee geeft u op dat de back-upbestanden voor de site en sitedatabase zijn opgeslagen in het opgegeven pad op het lokale station van de siteserver. U moet de lokale map maken voordat de back-uptaak wordt uitgevoerd. Het lokale systeemaccount op de siteserver moet **schrijf** machtigingen hebben voor het NTFS-bestandssysteem naar de lokale map voor de back-up van de siteserver. Het lokale systeemaccount op de computer waarop de SQL Server wordt uitgevoerd, moet **schrijf** machtigingen hebben voor NTFS naar de map voor de back-up van de sitedatabase.  

    -   **Netwerkpad (UNC-naam) voor sitegegevens en database**: Hiermee geeft u op dat de back-upbestanden voor de site en sitedatabase zijn opgeslagen in het opgegeven UNC-pad. U moet de share maken voordat de back-uptaak wordt uitgevoerd. Het computeraccount van de siteserver en het computeraccount van de SQL Server moeten, als SQL Server is geïnstalleerd op een andere computer, beschikken over **schrijf** machtigingen voor NTFS en deelmachtigingen naar de gedeelde netwerkmap.  

    -   **Lokale stations op siteserver en SQL Server**: Hiermee geeft u op dat de back-upbestanden voor de site worden opgeslagen in het opgegeven pad op het lokale station van de siteserver en de back-upbestanden voor de sitedatabase zijn opgeslagen in het opgegeven pad op het lokale station van de Sitedatabaseserver. U moet de lokale mappen maken voordat de back-uptaak wordt uitgevoerd. Het computeraccount van de siteserver moet **schrijf** machtigingen hebben voor NTFS naar de map die u maakt op de siteserver. Het computeraccount van de SQL Server moet **schrijf** machtigingen hebben voor NTFS naar de map die u maakt op de sitedatabaseserver. U kunt deze optie alleen gebruiken wanneer de sitedatabase niet is geïnstalleerd op de siteserver.  

    > [!NOTE]  
    >    - U kunt de optie om te bladeren naar de back-updoelmap alleen gebruiken wanneer u het UNC-pad opgeeft van de back-updoelmap.

    > - De voor de back-updoelmap gebruikte map- of sharenaam ondersteunt niet het gebruik van Unicode-tekens.  


6.  Configureer een planning voor de back-uptaak van de site. De aanbevolen planning voor het uitvoeren van een back-up is buiten werkuren. Als u een hiërarchie hebt, overweeg dan een planning die ten minste tweemaal per week wordt uitgevoerd voor maximale gegevensretentie in het geval van het uitvallen van een site.  

    Als u de Configuration Manager-console op dezelfde siteserver die u configureert voor back-up uitvoert, gebruikt de onderhoudstaak Backup siteserver lokale tijd voor de planning. Wanneer de Configuration Manager-console wordt uitgevoerd vanaf een computer die extern zijn van de site die u voor back-up configureert, gebruikt de onderhoudstaak back-upserver van Site UTC voor de planning.  

7.  Kies of u wilt maken van een waarschuwing als de site back-uptaak mislukt, klikt u op **OK**, en klik vervolgens op **OK**. Als u selecteert, maakt Configuration Manager een kritieke waarschuwing voor de back-upfouten die u kunt bekijken in de **waarschuwingen** knooppunt in de **bewaking** werkruimte.  

 Controleer vervolgens of de onderhoudstaak Backup siteserver wordt uitgevoerd, om ervoor te zorgen dat back-ups worden gemaakt.  

##### <a name="to-verify-that-the-backup-site-server-maintenance-task-is-running"></a>Om te controleren of de onderhoudstaak Backup siteserver wordt uitgevoerd  

-   Controleren of de onderhoudstaak van de Site back-up wordt uitgevoerd door het nagaan van het volgende:  

    -   Controleer de tijdstempel op de bestanden in de back-updoelmap die de taak gemaakt. Controleer of de tijdstempel is bijgewerkt met een tijd die overeenkomt met de tijd wanneer de taak het laatst is gepland om uit te voeren.  

    -   Controleer in het knooppunt **Onderdeelstatus** in de werkruimte **Bewaking** de statusberichten voor SMS_SITE_BACKUP. Als de siteback-up correct is voltooid, ziet u het bericht ID 5035 dat aangeeft dat de siteback-up zonder fouten is voltooid.  

    -   Als de onderhoudstaak van de back-upserver van de site is ingesteld op het genereren van een waarschuwing als de back-up mislukt, kunt u het knooppunt **Waarschuwingen** in de werkruimte **Bewaking** controleren op mislukte back-ups.  

    -   In &lt; *ConfigMgrInstallationFolder*> \Logs Smsbkup.log op waarschuwingen en fouten bekijken. Als de siteback-up correct is voltooid, ziet u `Backup completed` met een tijdstempel en bericht-id `STATMSG: ID=5035`.  

    > [!TIP]  
    >  Als de onderhoudstaak van de back-up mislukt, kunt u de back-uptaak opnieuw starten door de SMS_SITE_BACKUP-service te stoppen en opnieuw te starten.  

###  <a name="BKMK_DPMBackup"></a> Data Protection Manager gebruiken om een back-up te maken van uw sitedatabase  
 U kunt System Center 2012 Data Protection Manager (DPM) gebruiken om een back-up te maken van uw sitedatabase. U moet een nieuwe beveiligingsgroep maken in DPM voor de computer van de sitedatabase. Selecteer op de pagina **Groepsleden selecteren** van de wizard Nieuwe beveiligingsgroep maken de SMS Writer-service van de gegevensbronlijst en selecteer vervolgens de sitedatabase als een geschikt lid. Zie de [Documentatiebibliotheek voor Data Protection Manager](http://go.microsoft.com/fwlink/?LinkId=272772) op TechNet voor meer informatie over het gebruik van DPM om een back-up van uw sitedatabase te maken.  

> [!IMPORTANT]  
>  Configuration Manager biedt geen ondersteuning voor DPM-back-up voor een SQL Server-cluster dat een benoemd exemplaar gebruikt, maar biedt ondersteuning voor back-up van DPM op een SQL Server-cluster dat gebruik maakt van het standaardexemplaar van SQL Server.  

 Volg na herstel van de sitedatabase de stappen in Setup om de site te herstellen. Selecteer de **een sitedatabase gebruiken die handmatig is hersteld** hersteloptie om te gebruiken van de sitedatabase die u hebt hersteld met Data Protection Manager.  

###  <a name="BKMK_ArchivingBackupSnapshot"></a> Archiveren van de back-upmomentopname  
 De eerste keer dat de onderhoudstaak van de back-upserver van site wordt uitgevoerd, wordt een momentopname gemaakt van de back-up die u kunt gebruiken om uw siteserver te herstellen in het geval van een storing. Wanneer de back-uptaak opnieuw wordt uitgevoerd in latere runs, wordt een nieuwe momentopname gemaakt van de back-up die de vorige momentopname overschrijft. De site heeft daarom slechts één back-upmomentopname en u kunt eerdere momentopnames niet herstellen.  

 Het wordt om de volgende redenen aanbevolen meerdere archieven van de back-upmomentopname te bewaren:  

-   Het is gebruikelijk voor back-upmedia een fout optreedt, ze foutief worden geplaatst of slechts een gedeeltelijke back-up bevatten. Een mislukte zelfstandige primaire site op basis van een oudere back-up herstellen is beter dan deze zonder back-up te herstellen. Voor een siteserver in een hiërarchie moet de back-up in de bewaarperiode voor het bijhouden van wijzigingen van de SQL Server liggen, of de back-up is niet vereist.  

-   Een beschadiging in de site kan gedurende verschillende back-upcycli ongedetecteerd blijven. Mogelijk moet een back-upmomentopname van voor de site beschadigd geraakte gebruiken. Dit geldt voor een zelfstandige primaire site en sites in een hiërarchie waar de back-up zich in de SQL Server bevindt bijhouden bewaarperiode.  

-   De site heeft mogelijk helemaal geen back-upmomentopname, als de onderhoudstaak van de Back-upserver van site bijvoorbeeld is mislukt. Omdat de back-uptaak de vorige back-upmomentopname verwijdert voordat het een back-up begint te maken van de huidige gegevens, zal er geen geldige back-upmomentopname zijn.  

###  <a name="BKMK_UsingAfterBackup"></a> Het bestand AfterBackup.bat gebruiken  
 Na een back-up van de site gemaakt te hebben, probeert de taak Back-upserver van site automatisch een bestand uit te voeren dat AfterBackup.bat heet. U moet het AfterBackup.bat-bestand in handmatig maken &lt; *ConfigMgrInstallationFolder*> \Inboxes\Smsbkup. Als er een AfterBackup.bat-bestand bestaat en in de juiste map is opgeslagen, wordt automatisch uitgevoerd nadat de back-uptaak is voltooid. Het AfterBackup.bat-bestand laat u de back-upmomentopname archiveren aan het einde van elke back-upbewerking, en voert automatisch andere post-back-uptaken uit die geen deel uitmaken van de onderhoudstaak Back-upserver van site. Het AfterBackup.bat-bestand integreert het archief en de back-upbewerkingen, waardoor elke nieuwe back-upmomentopname wordt gearchiveerd. Wanneer het AfterBackup.bat-bestand niet aanwezig is, slaat de back-uptaak het over zonder dat het een invloed heeft op de back-upbewerking. Zie het knooppunt **Onderdeelstatus** in de werkruimte **Bewaking** en bekijk de statusberichten voor SMS_SITE_BACKUP om te controleren of de back-uptaak van de site het bestand AfterBackup.bat heeft uitgevoerd. Wanneer de taak het AfterBackup.bat-opdrachtbestand heeft gestart, ziet u de boodschap ID 5040.  

> [!TIP]  
>  Als u wilt archiveren van back-upbestanden van uw site het AfterBackup.bat-bestand maken, moet u een kopieeropdrachthulpprogramma zoals Robocopy, in het batchbestand gebruiken. U kunt bijvoorbeeld het bestand AfterBackup.bat maken en op de eerste lijn iets toevoegen als: `Robocopy E:\ConfigMgr_Backup \\ServerName\ShareName\ConfigMgr_Backup /MIR`. Zie de referentiepagina voor de opdrachtregel [Robocopy](http://go.microsoft.com/fwlink/p/?LinkId=228408) voor meer informatie over Robocopy.  

 Hoewel het beoogde gebruik van het bestand AfterBackup.bat het archiveren van back-upmomentopnamen is, kunt u het bestand AfterBackup.bat aanmaken om extra taken uit te voeren aan het einde van elke back-upbewerking.  

###  <a name="BKMK_SupplementalBackup"></a> Aanvullende back-uptaken  
 De onderhoudstaak Back-upserver van site biedt een back-upmomentopname voor de siteserverbestanden en sitedatabase, maar er zijn andere items waarvan geen back-up is gemaakt die u moet overwegen wanneer u uw back-upstrategie bepaalt. Gebruik de volgende secties voor hulp bij het voltooien van de Configuration Manager-back-upstrategie.  

#### <a name="back-up-custom-reporting-services-reports"></a>Back-up maken van aangepaste rapporten van Reporting Services  
 Wanneer u vooraf bepaalde of gemaakte aangepaste rappoten voor Reporting Services hebt gewijzigd, is het maken van een back-up voor de databasebestanden van de rapportserver een belangrijk onderdeel van uw back-upstrategie. De back-up van de rapportserver moet een back-up van de bronbestanden omvatten voor rapporten en modellen, versleutelingssleutels, aangepaste assembly's of extensies, configuratiebestanden, aangepaste SQL Server-weergaven in aangepaste rapporten, aangepaste opgeslagen procedures, enzovoort.  

> [!IMPORTANT]  
>  Wanneer Configuration Manager wordt bijgewerkt naar een nieuwere versie, kunnen u de vooraf gedefinieerde rapporten overschreven door nieuwe rapporten. Als u een vooraf gedefinieerd rapport wijzigt, back-up van het rapport en vervolgens herstellen in Reporting Services.  

 Zie [Backup and Restore Operations for a Reporting Services Installation (Back-up- en terugzetbewerkingen voor een installatie van Reporting Services)](https://technet.microsoft.com/library/ms155814\(v=sql.120\).aspx) in de SQL Server 2014 Books Online voor meer informatie over het maken van back-ups van uw aangepaste rapporten in Reporting Services.  

#### <a name="backup-content-files"></a>Back-up maken van inhoudsbestanden  
 De Inhoudsbibliotheek in Configuration Manager is de locatie waar alle inhoudsbestanden worden opgeslagen voor software-updates, toepassingen, besturingssysteemimplementatie, enzovoort. De Inhoudsbibliotheek bevindt zich op de siteserver en op elk distributiepunt. De onderhoudstaak Back-upserver van site omvat geen back-up voor de inhoudsbibliotheek of de pakketbronbestanden. Wanneer er een fout optreedt op een siteserver wordt de informatie over de inhoudsbibliotheek teruggezet op de sitedatabase, maar moet u de inhoudsbibliotheek en pakketbronbestanden op de siteserver terugzetten.  

-   **Inhoudsbibliotheek**: De Inhoudsbibliotheek moet worden hersteld voordat u inhoud opnieuw naar distributiepunten distribueren kunt. Wanneer u de herdistributie van inhoud start, kopieert Configuration Manager de bestanden van de Inhoudsbibliotheek op de siteserver naar de distributiepunten. De Inhoudsbibliotheek voor de siteserver is in de map SCCMContentLib bevindt zich doorgaans op het station met de meeste vrije schijfruimte op het moment waarop de site is geïnstalleerd.  

-   **Pakketbronbestanden**: De pakketbronbestanden moeten worden hersteld voordat u inhoud op distributiepunten kunt bijwerken. Wanneer u inhoud bijwerken start, kopieert Configuration Manager nieuwe en gewijzigde bestanden van de pakketbron naar de Inhoudsbibliotheek, die in de beurt kopieert de bestanden naar de gekoppelde distributiepunten verwijst. U kunt de volgende query in SQL Server uitvoeren om de locatie van de pakketbron voor alle pakketten en toepassingen te vinden: `SELECT * FROM v_Package`. U kunt de locatie van de pakketbron vinden door de eerste drie tekens van de pakket-id te bekijken. Als de pakket-id bijvoorbeeld CEN00001 is, is de sitecode van de bronsite CEN. Wanneer u de pakketbronbestanden herstelt, moeten u deze op dezelfde locatie waar ze vóór de fout zijn hersteld.  

 Controleer dat u zowel de inhoudsbibliotheek als pakketbronlocaties in de back-up van uw bestandssysteem voor de siteserver opneemt.  

#### <a name="back-up-custom-software-updates"></a>Back-up maken van aangepaste software-updates  
 System Center Updates Publisher 2011 is een zelfstandig hulpprogramma dat u aangepaste software-updates publiceren naar Windows Server Update Services (WSUS kunt), de software-updates voor Configuration Manager synchroniseren compatibiliteit van software-updates vaststelt en de aangepaste software-updates implementeren op clients. Updates Publisher gebruikt een lokale database voor de software-update opslagplaats ervan. Wanneer u Updates Publisher gebruikt voor het beheren van aangepaste software-updates, moet u bepalen of u moet de database Updates Publisher opnemen in uw back-upplan. Zie [System Center Updates Publisher 2011](http://go.microsoft.com/fwlink/p/?LinkId=228726) in de System Center TechCenter Library voor meer informatie over Updates Publisher.  

 Gebruik de volgende procedure back-up van de database Updates Publisher.  

###### <a name="to-back-up-the-updates-publisher-2011-database"></a>Een back-up maken van de Updates Publisher 2011-database  

1.  Op de computer waarop Updates Publisher wordt uitgevoerd, bladert u naar de Updates Publisher-databasebestand (Scupdb.sdf) in %*USERPROFILE*%\AppData\Local\Microsoft\System Center Updates Publisher 2011\5.00.1727.0000\\. Er is een verschillend databasebestand voor elke gebruiker die de Updates Publisher wordt uitgevoerd.  

2.  Kopieer het databasebestand naar uw back-upbestemming. Als uw back-upbestemming E:\ConfigMgr_Backup is, kunt u het databasebestand Updates Publisher kopiëren naar E:\ConfigMgr_Backup\SCUP2011.  

    > [!TIP]  
    >  Wanneer er meer dan één databasebestand op een computer, houd rekening met het bestand opslaan in een submap waarmee wordt aangegeven het profiel dat is gekoppeld aan het databasebestand dat. U zou bijvoorbeeld één databasebestand kunnen hebben in E:\ConfigMgr_Backup\SCUP2011\User1 en een ander databasebestand in E:\ConfigMgr_Backup\SCUP2011\User2.  

### <a name="user-state-migration-data"></a>Migratiegegevens van de gebruikersstatus  
 U kunt takenreeksen Configuration Manager vastleggen en herstellen van de gegevens in implementatiescenario's van besturingssysteem waar u de status van de gebruiker van het huidige besturingssysteem behouden. De mappen waarin de gegevens met betrekking tot de gebruikersstatus zijn opgeslagen, staan in de eigenschappen voor het statusmigratiepunt. Van deze migratiegegevens van de gebruikersstatus wordt geen back-up gemaakt als onderdeel van de onderhoudstaak Back-upserver van site. Als deel van uw back-upplan moet u handmatig een back-up maken van de mappen die u specificeert om de migratiegegevens van de gebruikersstatus op te slaan.   

#### <a name="to-determine-the-folders-used-to-store-user-state-migration-data"></a>De mappen bepalen die worden gebruikt om migratiegegevens van de gebruikersstatus op te slaan  

1.  Klik op **Beheer**in de Configuration Manager-console.  

2.  In de **beheer** werkruimte Vouw **siteconfiguratie**, en kies **Servers en sitesysteemrollen**.  

3.  Selecteer het sitesysteem dat de statusmigratierol host, en kies **Statusmigratiepunt** in **sitesysteemrollen**.  


4.  Klik op het tabblad **Siterol** in de groep **Eigenschappen** op **Eigenschappen**.  
5.  De mappen waar de migratiegegevens van de gebruikersstatus worden opgeslagen, staan in de sectie **Mapdetails** op het tabblad **Algemeen**.  

## <a name="recover-a-configuration-manager-site"></a>Een Configuration Manager-site herstellen
 Het herstel van een Configuration Manager-site is vereist wanneer een Configuration Manager-site of gegevensverlies in de sitedatabase optreedt. Het herstellen en opnieuw synchroniseren van gegevens zijn de belangrijkste taken van een siteherstel en zijn nodig om een onderbreking van de bewerkingen te voorkomen.  

> [!IMPORTANT]  
>  Doe het volgende wanneer u de database voor een site herstelt:  

>  -   U moet dezelfde versie en editie van SQL Server gebruiken. Bijvoorbeeld: terugzetten van een database die werd uitgevoerd op de SQL Server 2012 naar SQL Server 2014 wordt niet ondersteund. Op deze manier wordt terugzetten van een sitedatabase die werd uitgevoerd op een Standard-editie van SQL Server 2014 naar een Enterprise-editie van SQL Server 2014 niet ondersteund.  
> -   SQL Server moet niet worden ingesteld op **modus voor één gebruiker**.  
> -   Controleer of de .MDF- en .LDF-bestanden geldig zijn. Wanneer u een site herstelt, wordt er niet gecontroleerd op de status van de bestanden die u wilt herstellen.  


 Siteherstel wordt gestart door het uitvoeren van de Configuration Manager-installatiewizard vanaf de CD. Meest recente map.  U kunt ook het script voor installatie zonder toezicht te configureren en vervolgens met de Setup-opdrachtoptie **/script** optie voor het installatieprogramma uitvoeren vanuit deze dezelfde CD. Meest recente map. Uw herstelopties variëren afhankelijk van of u een back-up van de Configuration Manager-sitedatabase hebt. Zie [De map CD.Latest voor System Center Configuration Manager](../../core/servers/manage/the-cd.latest-folder.md) voor meer informatie.  

> [!IMPORTANT]  
>  Als u Configuration Manager Setup via uitvoeren de **Start** menu op de siteserver de **herstellen van een site** optie is niet beschikbaar.  

>  Als u eventuele updates van de Configuration Manager-console hebt geïnstalleerd voordat u uw back-up, kan niet met succes herinstallatie van de site met behulp van Setup uit vanaf installatiemedia of het installatiepad voor Configuration Manager.  

> [!NOTE]  
>  Als u een sitedatabase herstelt die was geconfigureerd voor databasereplica's, moet u, voordat u de databasereplica's kunt gebruiken, elke databasereplica opnieuw configureren, waarbij zowel de publicaties als abonnementen opnieuw worden gemaakt.  

###  <a name="BKMK_DetermineRecoveryOptions"></a> Uw herstelopties bepalen  
 Er zijn twee hoofdgebieden waarmee u rekening moet houden voor de primaire siteserver van Configuration Manager en herstel van centrale beheersite; de siteserver en de sitedatabase. Gebruik de volgende secties om u te helpen de opties te bepalen die u moet selecteren voor uw herstelscenario.  

> [!NOTE]  

####  <a name="BKMK_SiteServerRecoveryOptions"></a> Opties voor herstel van de siteserver  
 U moet het installatieprogramma starten vanaf een kopie van de CD. Meest recente map die u buiten de Configuration Manager-installatiemap maakt. Vervolgens selecteert u de optie **Een site herstellen** . Wanneer u het installatieprogramma uitvoert, hebt u de volgende herstelopties voor de mislukte siteserver:  

-   **De siteserver met behulp van een bestaande back-up herstellen**: Gebruik deze optie wanneer u een back-up van de siteserver van Configuration Manager die op de siteserver is gemaakt als onderdeel van de **back-upserver van Site** onderhoudstaak vóór de sitefout. De site wordt opnieuw geïnstalleerd, en de site-instellingen worden geconfigureerd, op basis van de site waarvan een back-up was gemaakt.  

-   **De siteserver opnieuw installeren**: Gebruik deze optie wanneer u een back-up van de siteserver niet hebt. De siteserver wordt opnieuw geïnstalleerd, en u moet de site-instellingen opgeven, net zoals u zou doen tijdens een eerste installatie. U moet dezelfde sitecode en sitedatabasenaam gebruiken die u hebt gebruikt toen de mislukte site voor het eerst werd geïnstalleerd om de site te kunnen herstellen.  

> [!NOTE]  
>  Wanneer wordt gedetecteerd dat een bestaande Configuration Manager-site op de server, kunt u een siteherstel starten, maar de herstelopties voor de siteserver zijn beperkt. Als u het installatieprogramma bijvoorbeeld uitvoert op een bestaande siteserver, wanneer u herstel kiest, kunt u de sitedatabaseserver herstellen, maar is de optie om de siteserver te herstellen uitgeschakeld.  

####  <a name="BKMK_SiteDatabaseRecoveryOption"></a> Opties voor herstel van de sitedatabase  
 Wanneer u het installatieprogramma uitvoert, hebt u de volgende herstelopties voor de sitedatabase:  

-   **Herstellen van de sitedatabase met behulp van een back-upset**: Gebruik deze optie wanneer u een back-up van de sitedatabase van Configuration Manager dat is gemaakt als onderdeel van de **back-upserver van Site** onderhoudstaak uitgevoerd op de site vóór de sitefout van de database. Wanneer u een hiërarchie hebt, worden de wijzigingen die zijn aangebracht aan de sitedatabase na de laatste back-up van de sitedatabase opgehaald uit de centrale beheersite voor een primaire site, of uit een primaire referentiesite voor een centrale beheersite. Wanneer u de sitedatabase voor een zelfstandige primaire site herstelt, gaan de sitewijzigingen na de laatste back-up verloren.  

     Wanneer u de sitedatabase voor een site in een hiërarchie herstelt, is het herstelgedrag verschillend voor een centrale beheersite en primaire site, en wanneer de laatste back-up binnen of buiten de bewaarperiode voor het bijhouden van wijzigingen van de SQL Server ligt. Zie de rubriek [Herstelscenario's voor sitedatabase](#BKMK_SiteDBRecoveryScenarios) in dit onderwerp voor meer informatie.  

    > [!NOTE]  
    >  Het herstel mislukt als u ervoor kiest de sitedatabase te herstellen met behulp van een back-upset, maar de sitedatabase reeds bestaat.  

-   **Maak een nieuwe database voor deze site**: Gebruik deze optie wanneer u een back-up van de Configuration Manager-sitedatabase niet hebt. Wanneer u een hiërarchie hebt, wordt er een nieuwe sitedatabase gemaakt, en worden de gegevens hersteld met behulp van gerepliceerde gegevens van de centrale beheersite voor een primaire site, of een primaire referentiesite voor een centrale beheersite. Deze optie is niet beschikbaar wanneer u een zelfstandige primaire site of een centrale beheersite herstelt die geen primaire sites heeft.  

-   **Een sitedatabase gebruiken die handmatig is hersteld**: Gebruik deze optie wanneer u de Configuration Manager-sitedatabase reeds hebt hersteld, maar moet het herstelproces te voltooien. Configuration Manager kan de sitedatabase herstellen vanuit back-up onderhoudstaak van de Configuration Manager of vanuit een site databaseback-up die u uitvoert door DPM of een ander proces. Nadat u de sitedatabase herstellen met behulp van een methode buiten Configuration Manager, moet u Setup uitvoert en selecteer deze optie om het herstel van de sitedatabase te voltooien. Wanneer u een hiërarchie hebt, worden de wijzigingen die zijn aangebracht aan de sitedatabase na de laatste back-up van de sitedatabase opgehaald uit de centrale beheersite voor een primaire site, of uit een primaire referentiesite voor een centrale beheersite. Wanneer u de sitedatabase voor een zelfstandige primaire site herstelt, gaan de sitewijzigingen na de laatste back-up verloren.  

    > [!NOTE]  
    >  Wanneer u DPM gebruikt voor back-up van uw sitedatabase, gebruikt u de DPM-procedures de sitedatabase herstellen naar een opgegeven locatie voordat u het herstelproces in Configuration Manager verderzet. Zie de [Documentatiebibliotheek voor de Data Protection Manager](http://go.microsoft.com/fwlink/?LinkId=272772) op TechNet Voor meer informatie over DPM.  

-   **Databaseherstel overslaan**: Gebruik deze optie wanneer er geen gegevensverlies is opgetreden op de Sitedatabaseserver van Configuration Manager. Deze optie is enkel geldig wanneer de sitedatabase zich op een andere computer bevindt dan de siteserver die u aan het herstellen bent.  

####  <a name="bkmk_SQLretention"></a> Bewaarperiode voor het bijhouden van wijzigingen van de SQL Server  
 Het bijhouden van wijzigingen is ingeschakeld voor de sitedatabase in SQL Server. Bijhouden van Configuration Manager kan informatie opvragen over de wijzigingen die zijn aangebracht aan databasetabellen na een eerder tijdspunt in de tijd. De bewaarperiode specificeert hoe lang informatie over het bijhouden van wijzigingen wordt bewaard. De sitedatabase is standaard geconfigureerd om een bewaarperiode van vijf dagen te hebben. Wanneer u een sitedatabase herstelt, vindt het herstelproces anders plaats als uw back-up binnen of buiten de bewaarperiode valt. Als er bijvoorbeeld een fout optreedt op de sitedatabaseserver, en uw laatste back-up is 7 dagen oud, dan valt het buiten de bewaarperiode.

 Zie de volgende blogs van het team van SQL Server voor meer informatie over inwendige bijhouden SQL Server: [Het bijhouden van opschoning - deel 1](https://blogs.msdn.microsoft.com/sql_server_team/change-tracking-cleanup-part-1) en [wijziging bijhouden opschoning - part 2](https://blogs.msdn.microsoft.com/sql_server_team/change-tracking-cleanup-part-2).



####  <a name="bkmk_reinit"></a> Proces om site- of algemene gegevens opnieuw te initialiseren  
 Het proces om site- of algemene gegevens opnieuw te initialiseren vervangt bestaande gegevens in de sitedatabase door gegevens uit een andere sitedatabase. Wanneer site ABC bijvoorbeeld gegevens opnieuw initialiseert van site XYR, dan vinden de volgende stappen plaats:  

-   De gegevens worden van site XYZ naar site ABC gekopieerd.  

-   De bestaande gegevens voor site XYZ worden verwijderd uit de sitedatabase op site ABC.  

-   De gekopieerde gegevens van site XYZ worden opgenomen in de sitedatabase op site ABC.  

##### <a name="example-scenario-1"></a>Voorbeeldscenario 1  
 **De primaire site initialiseert de algemene gegevens uit de centrale beheersite opnieuw**: Het herstelproces verwijdert de bestaande algemene gegevens voor de primaire site in de primaire sitedatabase en vervangt de gegevens door de algemene gegevens opgehaald uit de centrale beheersite.  

##### <a name="example-scenario-2"></a>Voorbeeldscenario 2  
 **De centrale beheersite initialiseert de sitegegevens van een primaire site opnieuw**: Het herstelproces verwijdert de bestaande sitegegevens voor die primaire site in de database van de centrale beheersite en vervangt de gegevens door de gegevens van de site gekopieerd uit de primaire site. De sitegegevens voor andere primaire sites blijven onveranderd.  

####  <a name="BKMK_SiteDBRecoveryScenarios"></a> Scenario's voor het herstel van een sitedatabase  
 Nadat een sitedatabase is hersteld van een back-up, wordt de Configuration Manager probeert de wijzigingen te herstellen in site- en algemene gegevens na de laatste databaseback-up. De volgende beschrijven de acties die Configuration Manager wordt gestart nadat een sitedatabase is hersteld van back-up.  

 **De herstelde site is een centrale beheersite:**  

-   **Back-up van database binnen de bewaarperiode voor het bijhouden van wijzigingen**  

    -   **Globale gegevens:** De wijzigingen in algemene gegevens na de back-up worden gerepliceerd van alle primaire sites.  

    -   **De gegevens van de site:** De wijzigingen in sitegegevens na de back-up worden gerepliceerd van alle primaire sites.  

-   **Databaseback-up ouder is dan de bewaarperiode voor het bijhouden van wijzigingen**  

    -   **Globale gegevens:** De centrale beheersite initialiseert de algemene gegevens uit de primaire referentiesite opnieuw, indien u dit opgeeft. Dan initialiseren alle andere primaire sites de algemene gegevens uit de centrale beheersite opnieuw. Indien er geen referentiesite is opgegeven, initialiseren alle primaire sites de algemene gegevens uit de centrale beheersite opnieuw (de gegevens die waren hersteld op basis van de back-up).  

    -   **De gegevens van de site:** De centrale beheersite initialiseert de sitegegevens van elke primaire site opnieuw.  

 **De herstelde site is een primaire site:**  

-   **Back-up van database binnen de bewaarperiode voor het bijhouden van wijzigingen**  

    -   **Globale gegevens:** De wijzigingen in algemene gegevens na de back-up worden gerepliceerd uit de centrale beheersite.  

    -   **De gegevens van de site:** De centrale beheersite initialiseert de sitegegevens uit de primaire site opnieuw. Wijzigingen na de back-up gaan verloren, maar de meeste gegevens worden opnieuw gegenereerd door clients die informatie sturen naar de primaire site.  

-   **Databaseback-up ouder is dan de bewaarperiode voor het bijhouden van wijzigingen**  

    -   **Globale gegevens:** De primaire site initialiseert de algemene gegevens uit de centrale beheersite opnieuw.  

    -   **De gegevens van de site:** De centrale beheersite initialiseert de sitegegevens uit de primaire site opnieuw. Wijzigingen na de back-up gaan verloren, maar de meeste gegevens worden opnieuw gegenereerd door clients die informatie sturen naar de primaire site.  

### <a name="site-recovery-procedures"></a>Procedures voor het herstellen van een site  
 Gebruik een van de volgende procedures om u te helpen uw siteserver en sitedatabase te herstellen.  

##### <a name="to-start-a-site-recovery-in-the-setup-wizard"></a>Een siteherstel in de Installatiewizard starten  

1.  Kopieer de CD. Meest recente map naar een locatie buiten de Configuration Manager-installatiemap. (Zie [De map CD.Latest voor System Center Configuration Manager](../../core/servers/manage/the-cd.latest-folder.md).)  

     In het exemplaar van de CD. Meest recente map, voert u de Configuration Manager Setup-Wizard.  

2.  Op de pagina **Aan de slag** selecteert u **Een site herstellen**en klikt u vervolgens op **Volgende**.  

3.  Voltooi de wizard met behulp van de opties die geschikt zijn voor uw siteherstel.  

    > [!IMPORTANT]  
    >  Tijdens het herstel identificeert het installatieprogramma de SQL Server Service Broker (SBB)-poort die wordt gebruikt door de SQL Server. Wijzig deze poortinstelling niet tijdens het herstel of de gegevensreplicatie zal niet goed werken nadat het herstel is voltooid.  

    > [!NOTE]  
    >  U kunt de oorspronkelijke of een nieuw pad wilt gebruiken voor de installatie van de Configuration Manager in de Wizard Setup opgeven.  

##### <a name="to-start-an-unattended-site-recovery"></a>Het herstel van een site zonder toezicht starten  

1.  Bereid het script voor de installatie zonder toezicht voor voor de opties die u nodig hebt voor het siteherstel.  

2.  Configuration Manager Setup uitvoert met behulp van de opdracht **/script** optie. Bijvoorbeeld, als u uw installatie-initialisatiebestand ConfigMgrUnattend.ini en opgeslagen in de directory C:\Temp van de computer waarop u Setup uitvoert, zou de opdracht zijn als volgt: **Setup/script C:\temp\ConfigMgrUnattend.ini**.  

> [!NOTE]  
>  Nadat u een centrale beheersite hebt hersteld, is het mogelijk dat de replicatie van bepaalde sitegegevens die afkomstig zijn van onderliggende sites mislukt. Het kan hierbij gaan om de hardware-inventaris, software-inventaris en statusberichten.  
>   
>  Als dit het geval is, moet u **ConfigMgrDRSSiteQueue** opnieuw voor de databasereplicatie initialiseren.  Gebruiken om dit te doen, **SQL Server Manager** de volgende query uitvoeren op de Configuration Manager sitedatabase op de centrale beheersite:  
>   
>  **IF EXISTS (SELECTEER \* IN sys.service_queues WAARBIJ name = 'ConfigMgrDRSSiteQueue' EN is_receive_enabled = 0)**  
>   
>  **ALTER QUEUE [dbo].[ConfigMgrDRSSiteQueue] WITH STATUS = ON**  

###  <a name="BKMK_UnattendedSiteRecoveryKeys"></a> Scriptbestandsleutels voor herstel van sites zonder toezicht  
 Als u een herstel zonder toezicht van een centrale beheersite voor Configuration Manager of de primaire site, kunt u een script voor installatie zonder toezicht maken en Setup gebruiken met de opdrachtoptie. Het script geeft hetzelfde type informatie die de Installatiewizard vraagt, behalve dat er geen standaardinstellingen zijn. Alle waarden moeten worden gespecificeerd voor de installatiesleutels die van toepassing zijn op het type herstel dat u gebruikt.  

 U kunt de Configuration Manager Setup zonder toezicht uitvoeren met behulp van een initialisatiebestand met de installatieopdrachtregeloptie. Installatie zonder toezicht wordt ondersteund voor het herstellen van een centrale beheersite voor Configuration Manager en de primaire site. Om de installatieopdrachtregeloptie /script te gebruiken, moet u een initialisatiebestand maken en de naam van het initialisatiebestand specificeren na de installatieopdrachtregeloptie /script. De naam van het bestand is niet belangrijk zolang het de extensie .ini heeft. Wanneer u verwijst naar het installatie-initialisatiebestand van de opdrachtregel, moet u het volledige pad naar het bestand geven. Als uw installatie-initialisatiebestand bijvoorbeeld setup.ini heet, en het is opgeslagen in de map C:\setup, dan zou uw opdrachtregel de volgende zijn:  

 **setup /script c:\setup\setup.ini**.  

> [!IMPORTANT]  
>  U moet beheerdersrechten hebben om de installatie uit te voeren. Wanneer u het installatieprogramma uitvoert met het script zonder toezicht, start u de opdrachtprompt in een beheerderscontext met **Als administrator uitvoeren**.  

 Het script bevat sectienamen, sleutelnamen en waarden. Vereiste sectiesleutelnamen variëren afhankelijk van het hersteltype waarvoor u een script schrijft. De volgorde van de sleutels binnen secties en de volgorde van secties binnen het bestand zijn niet belangrijk. De sleutels zijn niet hoofdlettergevoelig. Wanneer u waarden voor sleutels opgeeft, moet de naam van de sleutel worden gevolgd door een gelijkteken (=) en de waarde voor de sleutel.  

 Gebruik de volgende secties om u te helpen uw script te maken voor herstel van sites zonder toezicht. De tabellen geven een lijst van de beschikbare installatiescriptsleutels, de overeenkomstige waarden ervan, of ze al dan niet vereist zijn, voor welk type installatie ze worden gebruikt en een korte beschrijving voor de sleutel.  

#### <a name="recover-a-central-administration-site-unattended"></a>Herstellen van een centrale beheersite zonder toezicht  
 Gebruik de volgende informatie voor het configureren van een Setup-scriptbestand zonder toezicht om te herstellen van een centrale beheersite.  

 **Identificatie**  

-   **Sleutelnaam:** Actie  

    -   **Vereist:** Ja  

    -   **Waarden:** RecoverCCAR  

    -   **Details:** Herstelt een centrale beheersite  

-   **Sleutelnaam:** CDLatest  

    -   **Vereist:** Ja – alleen als u media vanaf de CD. Meest recente map.    

    -   **Waarden:** 1 een andere waarde dan 1 wordt beschouwd als CD niet worden gebruikt. Meest recente.

    -   **Details:** Wanneer u setup vanaf media op CD uitvoert moet uw script deze sleutel en waarde bevatten. Meest recente map voor het installeren van een primaire of centrale beheersite of een primaire of centrale beheersite te herstellen. Deze waarde informeert setup dat media CD vormen. Meest recente wordt gebruikt.  

**RecoveryOptions**  

-   **Sleutelnaam:** ServerRecoveryOptions  

    -   **Vereist:** Ja  

    -   **Waarden:** 1, 2 of 4  

         1 = Siteserver en SQL-server herstellen.  

         2 = Alleen siteserver herstellen.  

         4 = Alleen SQL Server herstellen.  

    -   **Details:** Hiermee geeft u op of het installatieprogramma de siteserver, SQL Server of beide zal herstellen. De gekoppelde sleutels zijn vereist wanneer u de volgende waarde instelt voor de instelling ServerRecoveryOptions:  

        -   **Waarde = 1** u hebt de mogelijkheid een waarde op te geven voor de sleutel **SiteServerBackupLocation** om de site te herstellen met een siteback-up. Als u geen waarde opgeeft, wordt de site opnieuw geïnstalleerd zonder dat deze wordt hersteld uit een back-upset.  

             De sleutel **BackupLocation** is vereist wanneer u een waarde van **10** configureert voor de sleutel **DatabaseRecoveryOptions** . Hiermee wordt de sitedatabase uit de back-up hersteld.  

        -   **Waarde = 2** u hebt de mogelijkheid een waarde op te geven voor de sleutel **SiteServerBackupLocation** om de site te herstellen met een siteback-up. Als u geen waarde opgeeft, wordt de site opnieuw geïnstalleerd zonder dat deze wordt hersteld uit een back-upset.  

        -   **Waarde = 4** de sleutel **BackupLocation** is vereist wanneer u een waarde van **10** configureert voor de sleutel **DatabaseRecoveryOptions** . Hiermee wordt de sitedatabase uit de back-up hersteld.  

-   **Sleutelnaam:** DatabaseRecoveryOptions  

    -   **Vereist:** Mogelijk  

    -   **Waarden:** 10, 20, 40, 80  

         10 = De sitedatabase uit de back-up herstellen.  

         20 = Gebruik een sitedatabase die handmatig wordt hersteld met behulp van een andere methode.  

         40 = Maak een nieuwe database voor de site. Gebruik deze optie wanneer er geen back-up van de sitedatabase beschikbaar is. Globale en sitegegevens worden hersteld via replicatie vanaf andere sites.  

         80 = Databaseherstel overslaan.  

    -   **Details:** Hiermee geeft u op hoe de sitedatabase in SQL Server door Setup wordt hersteld. Deze sleutel is vereist wanneer de instelling **ServerRecoveryOptions** een waarde heeft van **1** of **4**.  

-   **Sleutelnaam:** ReferenceSite  

    -   **Vereist:** Mogelijk  

    -   **Waarden:** &lt;ReferenceSiteFQDN\>  

    -   **Details:** Hiermee geeft u de primaire site die de centrale beheersite gebruikt voor het herstellen van globale gegevens als de databaseback-up ouder dan de bewaarperiode voor bijhouden of is wanneer u een site zonder een back-up herstelt.  

         Wanneer u geen referentiesite opgeeft en de back-up ouder is dan de bewaarperiode voor het bijhouden van wijzigingen, worden alle primaire sites opnieuw geïnitialiseerd met de herstelde gegevens van de centrale beheersite.  

         Wanneer u geen referentiesite opgeeft en de back-up valt binnen de bewaarperiode voor het bijhouden van wijzigingen, worden enkel wijzigingen sinds de back-up gerepliceerd van primaire sites. Wanneer er conflicterende wijzigingen van verschillende primaire sites zijn, gebruikt de centrale beheersite de eerste die het ontvangt.  

         Deze sleutel is vereist wanneer de instelling **DatabaseRecoveryOptions** een waarde heeft van **40**.  

-   **Sleutelnaam:** SiteServerBackupLocation  

    -   **Vereist:** Nee  

    -   **Waarden:** &lt;PathToSiteServerBackupSet\>  

    -   **Details:** Hiermee geeft u het pad naar de back-upset van de siteserver. Deze sleutel is optioneel wanneer de instelling **ServerRecoveryOptions** een waarde heeft van **1** of **2**. Geef een waarde op voor de sleutel **SiteServerBackupLocation** om de site te herstellen met behulp van een siteback-up. Als u geen waarde opgeeft, wordt de site opnieuw geïnstalleerd zonder dat deze wordt hersteld uit een back-upset.  

-   **Sleutelnaam:** Back-uplocatie  

    -   **Vereist:** Mogelijk  

    -   **Waarden:** &lt;PathToSiteDatabaseBackupSet\>  

    -   **Details:** Hiermee geeft u het pad naar de back-upset van de sitedatabase. De sleutel **BackupLocation** is vereist wanneer u een waarde van **1** of **4** configureert voor de sleutel **ServerRecoveryOptions** en een waarde van **10** configureert voor de sleutel **DatabaseRecoveryOptions** .  

**Opties**  

-   **Sleutelnaam:** Product-id  

    -   **Vereist:** Ja  

    -   **Waarden:**  

         xxxxx-xxxxx-xxxxx-xxxxx-xxxxx  

         Eval  

    -   **Details:** De Configuration Manager installatieproductcode, inclusief de liggende streepjes. Voer **Eval** de evaluatieversie van Configuration Manager kunt installeren.  

-   **Sleutelnaam:** SiteCode  

    -   **Vereist:** Ja  

    -   **Waarden:** &lt;Sitecode\>  

    -   **Details:** Drie alfanumerieke tekens die de site in uw hiërarchie wordt aangeduid. U moet de sitecode opgeven die werd gebruikt door de site vóór de fout.  

-   **Sleutelnaam:** Sitenaam  

    -   **Vereist:** Ja  

    -   **Waarden:** Sitenaam  

    -   **Details:** Beschrijving voor deze site.  

-   **Sleutelnaam:** SMSInstallDir  

    -   **Vereist:** Ja  

    -   **Waarden:** &lt;*Configmgrinstallatiepad*>  

    -   **Details:** Hiermee geeft u de installatiemap voor de programmabestanden van Configuration Manager.  

        > [!NOTE]  
        >  U kunt het oorspronkelijke pad of een nieuw pad wilt gebruiken voor de Configuration Manager-installatie opgeven.  

-   **Sleutelnaam:** SDKServer  

    -   **Vereist:** Ja  

    -   **Waarden:** &lt;*FQDN-naam van de SMS-Provider*>  

    -   **Details:** Hiermee geeft u de FQDN-naam voor de server die als voor de SMS-Provider host fungeert. U moet de server opgeven die als host optrad voor de SMS-provider voorafgaand aan de fout.  

         U kunt bijkomende SMS-providers voor de site configureren na de eerste installatie.  

-   **Sleutelnaam:** PrerequisiteComp  

    -   **Vereist:** Ja  

    -   **Waarden:** 0 of 1  

         0 = downloaden  

         1 = reeds gedownload  

    -   **Details:** Hiermee geeft u op of Setup vereiste bestanden die reeds zijn gedownload. Als u bijvoorbeeld de waarde 0 gebruikt, zal Setup de bestanden downloaden.  

-   **Sleutelnaam:** PrerequisitePath  

    -   **Vereist:** Ja  

    -   **Waarden:** &lt;*PathToSetupPrerequisiteFiles*>  

    -   **Details:** Hiermee geeft u het pad naar de vereiste bestanden voor Setup. Afhankelijk van de waarde van **PrerequisiteComp** gebruikt het installatieprogramma dit pad om de gedownloade bestanden op te slaan of om naar de eerder gedownloade bestanden te zoeken.  

-   **Sleutelnaam:** AdminConsole  

    -   **Vereist:** Mogelijk  

    -   **Waarden:** 0 of 1  

         0 = niet installeren  

         1 = installeren  

    -   **Details:** Hiermee kunt u de Configuration Manager-console te installeren. Deze sleutel is vereist, behalve wanneer de instelling **ServerRecoveryOptions** een waarde heeft van **4**.  

-   **Sleutelnaam:** JoinCEIP  

    -   **Vereist:** Ja  

    -   **Waarden:** 0 of 1  

         0 = niet aanmelden  

         1 = aanmelden  

    -   **Details:** Hiermee geeft u op of u wilt deelnemen aan het programma voor kwaliteitsverbetering.  

**SQLConfigOptions**  

-   **Sleutelnaam:** SQL Server-naam  

    -   **Vereist:** Ja  

    -   **Waarden:** *&lt;SQL Server-naam\>*  

    -   **Details:** De naam van de server, of de exemplaarnaam van het geclusterde, met SQL Server die fungeert als host de sitedatabase. U moet dezelfde server opgeven die als host optrad voor de sitedatabase voorafgaand aan de fout.  

-   **Sleutelnaam:** Databasenaam  

    -   **Vereist:** Ja  

    -   **Waarden:**  

         *&lt;Sitedatabasenaam\>*  

         of  

         *&lt;InstanceName\>*\\*&lt;Sitedatabasenaam\>*  

    -   **Details:** De naam van de SQL Server-database te maken of de database van de centrale beheersite installeren. U moet dezelfde databasenaam opgeven die werd gebruikt voorafgaand aan de fout.  

        > [!IMPORTANT]  
        >  U moet de naam van het exemplaar en de naam van de sitedatabase opgeven als u het standaardexemplaar niet gebruikt.  

-   **Sleutelnaam:** SQLSSBPort  

    -   **Vereist:** Nee  

    -   **Waarden:** &lt;*SSBPortNumber*>  

    -   **Details:** Geef de SQL Server Service Broker (SSB)-poort die wordt gebruikt door SQL Server. Doorgaans is SSB geconfigureerd om TCP-poort 4022 te gebruiken, maar andere poorten worden ondersteund. U moet dezelfde SSB-poort opgeven die werd gebruikt vóór de fout.  

#### <a name="recover-a-primary-site-unattended"></a>Herstellen van een primaire site zonder toezicht  
 Gebruik de volgende informatie voor het configureren van een Setup-scriptbestand zonder toezicht om te herstellen van een centrale beheersite.  

 **Identificatie**  

-   **Sleutelnaam:** Actie  

    -   **Vereist:** Ja  

    -   **Waarden:** RecoverPrimarySite  

    -   **Details:** Hiermee herstelt u een primaire site  

-   **Sleutelnaam:** CDLatest  

    -   **Vereist:** Ja – alleen als u media vanaf de CD. Meest recente map.    

    -   **Waarden:** 1 een andere waarde dan 1 wordt beschouwd als CD niet worden gebruikt. Meest recente.

    -   **Details:** Wanneer u setup vanaf media op CD uitvoert moet uw script deze sleutel en waarde bevatten. Meest recente map voor het installeren van een primaire of centrale beheersite of een primaire of centrale beheersite te herstellen. Deze waarde informeert setup dat media CD vormen. Meest recente wordt gebruikt.

**RecoveryOptions**  

-   **Sleutelnaam:** ServerRecoveryOptions  

    -   **Vereist:** Ja  

    -   **Waarden:** 1, 2 of 4  

         1 = Siteserver en SQL-server herstellen.  

         2 = Alleen siteserver herstellen.  

         4 = Alleen SQL Server herstellen.  

    -   **Details:** Hiermee geeft u op of het installatieprogramma de siteserver, SQL Server of beide zal herstellen. De gekoppelde sleutels zijn vereist wanneer u de volgende waarde instelt voor de instelling ServerRecoveryOptions:  

        -   **Waarde = 1** u hebt de mogelijkheid een waarde op te geven voor de sleutel **SiteServerBackupLocation** om de site te herstellen met een siteback-up. Als u geen waarde opgeeft, wordt de site opnieuw geïnstalleerd zonder dat deze wordt hersteld uit een back-upset.  

             De sleutel **BackupLocation** is vereist wanneer u een waarde van **10** configureert voor de sleutel **DatabaseRecoveryOptions** . Hiermee wordt de sitedatabase uit de back-up hersteld.  

        -   **Waarde = 2** u hebt de mogelijkheid een waarde op te geven voor de sleutel **SiteServerBackupLocation** om de site te herstellen met een siteback-up. Als u geen waarde opgeeft, wordt de site opnieuw geïnstalleerd zonder dat deze wordt hersteld uit een back-upset.  

        -   **Waarde = 4** de sleutel **BackupLocation** is vereist wanneer u een waarde van **10** configureert voor de sleutel **DatabaseRecoveryOptions** . Hiermee wordt de sitedatabase uit de back-up hersteld.  

-   **Sleutelnaam:** DatabaseRecoveryOptions  

    -   **Vereist:** Mogelijk  

    -   **Waarden:** 10, 20, 40, 80  

         10 = De sitedatabase uit de back-up herstellen.  

         20 = Gebruik een sitedatabase die handmatig wordt hersteld met behulp van een andere methode.  

         40 = Maak een nieuwe database voor de site. Gebruik deze optie wanneer er geen back-up van de sitedatabase beschikbaar is. Globale en sitegegevens worden hersteld via replicatie vanaf andere sites.  

         80 = Databaseherstel overslaan.  

    -   **Details:** Hiermee geeft u op hoe de sitedatabase in SQL Server door Setup wordt hersteld. Deze sleutel is vereist wanneer de instelling **ServerRecoveryOptions** een waarde heeft van **1** of **4**.  

-   **Sleutelnaam:** SiteServerBackupLocation  

    -   **Vereist:** Nee  

    -   **Waarden:** &lt;PathToSiteServerBackupSet\>  

    -   **Details:** Hiermee geeft u het pad naar de back-upset van de siteserver. Deze sleutel is optioneel wanneer de instelling **ServerRecoveryOptions** een waarde heeft van **1** of **2**. Geef een waarde op voor de sleutel **SiteServerBackupLocation** om de site te herstellen met behulp van een siteback-up. Als u geen waarde opgeeft, wordt de site opnieuw geïnstalleerd zonder dat deze wordt hersteld uit een back-upset.  

-   **Sleutelnaam:** Back-uplocatie  

    -   **Vereist:** Mogelijk  

    -   **Waarden:** &lt;PathToSiteDatabaseBackupSet\>  

    -   **Details:** Hiermee geeft u het pad naar de back-upset van de sitedatabase. De sleutel **BackupLocation** is vereist wanneer u een waarde van **1** of **4** configureert voor de sleutel **ServerRecoveryOptions** en een waarde van **10** configureert voor de sleutel **DatabaseRecoveryOptions** .  

**Opties**  

-   **Sleutelnaam:** Product-id  

    -   **Vereist:** Ja  

    -   **Waarden:**  

         xxxxx-xxxxx-xxxxx-xxxxx-xxxxx  

         Eval  

    -   **Details:** De Configuration Manager installatieproductcode, inclusief de liggende streepjes. Voer **Eval** de evaluatieversie van Configuration Manager kunt installeren.  

-   **Sleutelnaam:** SiteCode  

    -   **Vereist:** Ja  

    -   **Waarden:** &lt;Sitecode\>  

    -   **Details:** Drie alfanumerieke tekens die de site in uw hiërarchie wordt aangeduid. U moet de sitecode opgeven die werd gebruikt door de site vóór de fout.  

-   **Sleutelnaam:** Sitenaam  

    -   **Vereist:** Ja  

    -   **Waarden:** Sitenaam  

    -   **Details:** Beschrijving voor deze site.  

-   **Sleutelnaam:** SMSInstallDir  

    -   **Vereist:** Ja  

    -   **Waarden:** &lt;*Configmgrinstallatiepad*>  

    -   **Details:** Hiermee geeft u de installatiemap voor de programmabestanden van Configuration Manager.  

        > [!NOTE]  
        >  U kunt het oorspronkelijke pad of een nieuw pad wilt gebruiken voor de Configuration Manager-installatie opgeven.  

-   **Sleutelnaam:** SDKServer  

    -   **Vereist:** Ja  

    -   **Waarden:** &lt;*FQDN-naam van de SMS-Provider*>  

    -   **Details:** Hiermee geeft u de FQDN-naam voor de server die als voor de SMS-Provider host fungeert. U moet de server opgeven die als host optrad voor de SMS-provider voorafgaand aan de fout.  

         U kunt bijkomende SMS-providers voor de site configureren na de eerste installatie.  

-   **Sleutelnaam:** PrerequisiteComp  

    -   **Vereist:** Ja  

    -   **Waarden:** 0 of 1  

         0 = downloaden  

         1 = reeds gedownload  

    -   **Details:** Hiermee geeft u op of Setup vereiste bestanden die reeds zijn gedownload. Als u bijvoorbeeld de waarde 0 gebruikt, zal Setup de bestanden downloaden.  

-   **Sleutelnaam:** PrerequisitePath  

    -   **Vereist:** Ja  

    -   **Waarden:** &lt;*PathToSetupPrerequisiteFiles*>  

    -   **Details:** Hiermee geeft u het pad naar de vereiste bestanden voor Setup. Afhankelijk van de waarde van **PrerequisiteComp** gebruikt het installatieprogramma dit pad om de gedownloade bestanden op te slaan of om naar de eerder gedownloade bestanden te zoeken.  

-   **Sleutelnaam:** AdminConsole  

    -   **Vereist:** Mogelijk  

    -   **Waarden:** 0 of 1  

         0 = niet installeren  

         1 = installeren  

    -   **Details:** Hiermee kunt u de Configuration Manager-console te installeren. Deze sleutel is vereist, behalve wanneer de instelling **ServerRecoveryOptions** een waarde heeft van **4**.  

-   **Sleutelnaam:** JoinCEIP  

    -   **Vereist:** Ja  

    -   **Waarden:** 0 of 1  

         0 = niet aanmelden  

         1 = aanmelden  

    -   **Details:** Hiermee geeft u op of u wilt deelnemen aan het programma voor kwaliteitsverbetering.  

**SQLConfigOptions**  

-   **Sleutelnaam:** SQL Server-naam  

    -   **Vereist:** Ja  

    -   **Waarden:** *&lt;SQL Server-naam\>*  

    -   **Details:** De naam van de server, of de exemplaarnaam van het geclusterde, met SQL Server die fungeert als host de sitedatabase. U moet dezelfde server opgeven die als host optrad voor de sitedatabase voorafgaand aan de fout.  

-   **Sleutelnaam:** Databasenaam  

    -   **Vereist:** Ja  

    -   **Waarden:**  

         *&lt;Sitedatabasenaam\>*  

         of  

         *&lt;InstanceName\>*\\*&lt;Sitedatabasenaam\>*  

    -   **Details:** De naam van de SQL Server-database te maken of de database van de centrale beheersite installeren. U moet dezelfde databasenaam opgeven die werd gebruikt voorafgaand aan de fout.  

        > [!IMPORTANT]  
        >  U moet de naam van het exemplaar en de naam van de sitedatabase opgeven als u het standaardexemplaar niet gebruikt.  

-   **Sleutelnaam:** SQLSSBPort  

    -   **Vereist:** Nee  

    -   **Waarden:** &lt;*SSBPortNumber*>  

    -   **Details:** Geef de SQL Server Service Broker (SSB)-poort die wordt gebruikt door SQL Server. Doorgaans is SSB geconfigureerd om TCP-poort 4022 te gebruiken, maar andere poorten worden ondersteund. U moet dezelfde SSB-poort opgeven die werd gebruikt vóór de fout.  

**Optie voor hiërarchie-uitbreiding**  

-   **Sleutelnaam:** CCARSiteServer  

    -   **Vereist:** Mogelijk  

    -   **Waarden:** &lt;*SiteCodeForCentralAdministrationSite*>  

    -   **Details:** Hiermee geeft u de centrale beheersite waarmee een primaire site zal worden gekoppeld wanneer het lid van de Configuration Manager-hiërarchie. Deze instelling is vereist als de primaire site was gekoppeld aan een centrale beheersite vóór de fout. U moet de sitecode opgeven die werd gebruikt door de centrale beheersite vóór de fout.  

-   **Sleutelnaam:** CASRetryInterval  

    -   **Vereist:** Nee  

    -   **Waarden:** &lt;*Interval*>  

    -   **Details:** Hiermee geeft u het interval (in minuten) om een verbinding met de centrale beheersite nadat de verbinding is mislukt. Als de verbinding met de centrale beheersite mislukt, wacht de primaire site bijvoorbeeld het aantal minuten dat u opgeeft voor CASRetryInterval, en probeert het dan opnieuw de verbinding te maken.  

-   **Sleutelnaam:** WaitForCASTimeout  

    -   **Vereist:** Nee  

    -   **Waarden:** &lt;*Time-out*>  

    -   **Details:** Hiermee geeft u het maximum time-outwaarde (in minuten) voor een primaire site verbinding maken met de centrale beheersite. Als een primaire site bijvoorbeeld geen verbinding kan maken met een centrale beheersite, probeert de primaire site opnieuw de verbinding met de centrale beheersite te maken op basis van het CASRetryInterval tot de WaitForCASTTimeout-periode is bereikt. U kunt een waarde opgeven van 0 tot 100.  

###  <a name="BKMK_PostRecovery"></a> Taken na herstel  
 Nadat u uw site hebt hersteld, zijn er verschillende taken na herstel die u moet overwegen voordat het herstel van uw site voltooid is. Gebruik de volgende secties voor hulp bij het voltooien van uw proces voor siteherstel.  

#### <a name="re-enter-user-account-passwords"></a>Wachtwoord voor gebruikersaccount opnieuw invoeren  
 Na een siteserverherstel moeten wachtwoorden voor de gebruikersaccounts die voor de site zijn opgegeven, opnieuw worden ingevoerd omdat ze tijdens het herstel van de site opnieuw zijn ingesteld. De accounts zijn opgenomen op de pagina **Voltooid** van de installatiewizard nadat het herstel van de site is voltooid is en is opgeslagen naar C:\ConfigMgrPostRecoveryActions.html op de herstelde siteserver.  

###### <a name="to-re-enter-user-account-passwords-after-site-recovery"></a>Wachtwoorden van gebruikersaccounts opnieuw invoeren na het siteherstel  

1.  Open de Configuration Manager-console en maak verbinding met de herstelde site.  

2.  Klik op **Beheer**in de Configuration Manager-console.  

3.  Vouw in de werkruimte **Beheer** de optie **Beveiliging**uit en klik vervolgens op **Accounts**.  

4.  Voor elke account waarin u het wachtwoord opnieuw moet invoeren, doet u het volgende:  

    1.  Selecteer de account uit de lijst van accounts die waren geïdentificeerd na siteherstel. U kunt deze lijst vinden in C:\ConfigMgrPostRecoveryActions.html op de herstelde siteserver.  

    2.  Klik op **Eigenschappen** in het tabblad **Start** in de groep **Eigenschappen** om de accounteigenschappen te openen.  

    3.  Klik in het tabblad **Algemeen** op **Instellen**en voer vervolgens opnieuw de wachtwoorden voor het account in.  

    4.  Klik op **Controleren**, selecteer de geschikte gegevensbron voor het geselecteerde gebruikersaccount en klik vervolgens op **Verbinding testen** om te controleren of het gebruikersaccount een verbinding kan maken met de gegevensbron.  

    5.  Klik op **OK** om de wachtwoordwijzigingen op te slaan en klik vervolgens op **OK**.  

#### <a name="re-enter-sideloading-keys"></a>Sideloading-codes opnieuw invoeren  
 Wanneer een siteserver is hersteld, moet u de Windows-sideloading-codes opnieuw invoeren die voor de site zijn opgegeven, omdat deze tijdens het herstellen van de site gereset zijn. Nadat u de sideloading-codes, het aantal in opnieuw invoeren de **activeringen gebruikt** kolom voor Windows-sideloading-codes gereset in de Configuration Manager-console. Laten we bijvoorbeeld vóór de sitefout die u hebt een **totaal activeringen** aantal ingesteld op **100** en **activeringen gebruikt** bedraagt **90** voor het aantal codes dat door apparaten zijn gebruikt. Na het herstel van de site wordt in de kolom **Totaal activeringen** nog steeds **100**weergegeven, maar wordt in de kolom **Gebruikte activeringen** ten onrechte **0**weergegeven. Nadat echter 10 nieuwe apparaten een sideloading-code hebben gebruikt, blijven er geen sideloading-codes meer over en het volgende apparaat kan geen sideloading-code toepassen.  

#### <a name="recreate-the-microsoft-intune-subscription"></a>Het Microsoft Intune-abonnement opnieuw maken  
 Als u een Configuration Manager-siteserver herstelt nadat de site server-computer opnieuw installatiekopie is gemaakt, wordt de Microsoft Intune-abonnement niet hersteld. Nadat u een site herstelt, moet u uw abonnement opnieuw aansluiten.  Maak een nieuwe APN-aanvraag niet, maar in plaats daarvan de huidige geldig .pem-bestand dat is geüpload voor het laatst iOS-beheer is geconfigureerd of vernieuwd uploaden. Zie [Het Windows Intune-abonnement configureren](/sccm/mdm/deploy-use/configure-intune-subscription) voor meer informatie.  

#### <a name="configure-ssl-for-site-system-roles-that-use-iis"></a>SSL configureren voor sitesysteemrollen die gebruikmaken van IIS  
 Wanneer u sitesystemen met IIS herstelt die vóór de fout voor HTTPS zijn geconfigureerd, moet u IIS opnieuw configureren voor het gebruik van het webservercertificaat.  

#### <a name="reinstall-hotfixes-in-the-recovered-site-server"></a>Hotfixes opnieuw installeren op de herstelde siteserver  
 Wanneer een site is hersteld, moet u de op de siteserver toegepaste hotfixes opnieuw installeren. Nadat de site is hersteld, vindt u op de pagina **Voltooid** van de wizard Setup een lijst met eerder geïnstalleerde hotfixes. Deze lijst wordt op de herstelde siteserver opgeslagen in **C:\ConfigMgrPostRecoveryActions.html** .  

#### <a name="recover-custom-reports-on-the-computer-running-reporting-services"></a>Aangepaste rapporten herstellen op een computer met Reporting Services  
 Wanneer u aangepaste Reporting Services-rapporten hebt gemaakt en er een fout is opgetreden in Reporting Services, kunt u de rapporten herstellen wanneer u een back-up van de rapportserver hebt gemaakt. Zie [Backup and Restore Operations for a Reporting Services Installation](http://go.microsoft.com/fwlink/p/?LinkId=228724) (Back-up en herstelbewerkingen voor een Reporting Services-installatie) in SQL Server 2008 Books Online voor meer informatie over het herstellen van uw aangepaste rapporten in Reporting Services.  

#### <a name="recover-content-files"></a>Inhoudsbestanden herstellen  
 De sitedatabase bevat informatie over de locatie waar de inhoudsbestanden op de siteserver zijn opgeslagen, maar er wordt geen back-up gemaakt van de inhoudsbestanden, noch worden deze hersteld als onderdeel van het back-up- en herstelproces. Als u inhoudsbestanden volledig wilt herstellen, moet u de inhoudsbibliotheek en pakketbronbestanden op de oorspronkelijke locatie herstellen. Er zijn verschillende methoden om uw inhoudsbestanden te herstellen, maar de eenvoudigste methode is dat u de bestanden vanuit een bestandssysteemback-up van de siteserver herstelt.  

 Als u niet beschikt over een bestandssysteemback-up van de pakketbronbestanden, moet u deze handmatig kopiëren of downloaden zoals u oorspronkelijk hebt gedaan toen u het pakket voor het eerst hebt gemaakt. U kunt de volgende query in SQL Server uitvoeren om de locatie van de pakketbron voor alle pakketten en toepassingen te vinden: `SELECT * FROM v_Package`. U kunt de locatie van de pakketbron vinden door de eerste drie tekens van de pakket-id te bekijken. Als de pakket-id bijvoorbeeld CEN00001 is, is de sitecode van de bronsite CEN. Wanneer u de pakketbronbestanden herstelt, moeten deze op dezelfde locatie worden hersteld waar deze zich vóór de fout bevonden.  

 Als u beschikt over een bestandssysteemback-up waarin zich geen inhoudsbibliotheek bevindt, hebt u de volgende herstelopties:  

-   **Een voorbereid inhoudsbestand importeren**: Wanneer u een Configuration Manager-hiërarchie hebt, kunt u een voorbereid inhoudsbestand maken met alle pakketten en toepassingen van een andere locatie en importeer het voorbereide inhoudsbestand om de Inhoudsbibliotheek op de siteserver te herstellen.  

-   **Inhoud bijwerken**: Wanneer u de actie inhoud bijwerken voor een pakket of toepassing implementatietype start, wordt de inhoud van de pakketbron naar de Inhoudsbibliotheek gekopieerd. De pakketbronbestanden moeten beschikbaar zijn op de oorspronkelijke locatie om deze actie met succes te voltooien. U moet deze actie op elk pakket en elke toepassing uitvoeren.  

#### <a name="recover-custom-software-updates-on-the-computer-running-updates-publisher"></a>Aangepaste software-updates herstellen op een computer met Updates Publisher  
 Wanneer u Updates Publisher-databasebestanden in uw back-upschema hebt opgenomen, kunt u de databases bij een storing op de computer waarop Updates Publisher wordt uitgevoerd herstellen. Zie [System Center Updates Publisher 2011](http://go.microsoft.com/fwlink/p/?LinkId=228726) in de System Center TechCenter Library voor meer informatie over Updates Publisher.  

 Gebruik de volgende procedure om de Updates Publisher-database te herstellen.  

###### <a name="to-restore-the-updates-publisher-2011-database"></a>De Updates Publisher 2011-database herstellen  

1.  Installeer Updates Publisher op de herstelde computer.  

2.  Kopieer het databasebestand (Scupdb.sdf) van uw back-upbestemming %*USERPROFILE*%\AppData\Local\Microsoft\System Center Updates Publisher 2011\5.00.1727.0000\ op de computer waarop Updates Publisher wordt uitgevoerd.  

3.  Wanneer u meer dan één gebruiker Updates Publisher op de computer wordt uitgevoerd, moet u elk databasebestand naar de juiste gebruikersprofiellocatie kopiëren.  

#### <a name="user-state-migration-data"></a>Migratiegegevens van de gebruikersstatus  
 Als onderdeel van de sitesysteemeigenschappen van het statusmigratiepunt geeft u de mappen op waarop de migratiegegevens van de gebruikersstatus zijn opgeslagen. Wanneer u een server herstelt met een map waarop migratiegegevens van de gebruikersstatus zijn opgeslagen, moet u de migratiegegevens van de gebruikersstatus op de server handmatig herstellen in dezelfde mappen waarop de gegevens waren opgeslagen vóór de fout.  

#### <a name="regenerate-the-certificates-for-distribution-points"></a>De certificaten voor distributiepunten opnieuw genereren  
 Wanneer u een site hebt hersteld, kan het bestand distmgr.log de volgende vermelding voor een of meer distributiepunten bevatten: **Kan niet worden ontsleuteld cert PFX-gegevens**. Deze vermelding geeft aan dat de certificaatgegevens van het distributiepunt niet door de site kunnen worden ontsleuteld. Als u dit wilt oplossen, moet u het certificaat van de betrokken distributiepunten opnieuw genereren of opnieuw importeren. Dit kan worden gedaan met de PowerShell-cmdlet [Set-CMDistributionPoint](https://technet.microsoft.com/library/jj821872\(v=sc.20\).aspx).  

#### <a name="update-certificates-used-for-cloud-based-distribution-points"></a>Voor clouddistributiepunten gebruikte certificaten bijwerken  
 Configuration Manager vereist een beheercertificaat dat wordt gebruikt voor de siteserver verzonden om communicatie cloud-gebaseerd distributiepunt. Wanneer een site is hersteld, moet u de certificaten van clouddistributiepunten bijwerken.  

####  <a name="BKMK_RecoverSecondarySite"></a> Een secundaire site herstellen  
 Configuration Manager biedt geen ondersteuning voor de back-up van de database op een secundaire site, maar biedt ondersteuning voor herstel door de secundaire site opnieuw te installeren. Herstel van secundaire site is vereist wanneer een secundaire site van Configuration Manager is mislukt. U kunt een secundaire site herstellen via de **secundaire Site herstellen** actie van de **Sites** knooppunt in de Configuration Manager-console. In tegenstelling tot herstel voor een centraal beheer-site of de primaire site, wordt bij herstel voor een secundaire site geen back-upbestand gebruikt en worden in plaats daarvan de bestanden van de secundaire site opnieuw geïnstalleerd op de computer van de mislukte secundaire site. De gegevens van de secundaire site worden vervolgens opnieuw geïnitialiseerd met gegevens uit de bovenliggende primaire site. Configuration Manager wordt tijdens het herstelproces wordt gecontroleerd of de Inhoudsbibliotheek zich op de secundaire sitecomputer bevindt en dat de betreffende inhoud beschikbaar is. De secundaire site maakt gebruik van de bestaande inhoudsbibliotheek als deze de juiste inhoud bevat. Anders moet u voor het herstellen van de inhoudsbibliotheek van een herstelde secundaire site de inhoud opnieuw distribueren of vooraf plaatsen op de herstelde site. Wanneer u een distributiepunt hebt dat zich niet op de secundaire site bevindt, hoeft u het distributiepunt tijdens het herstellen van de secundaire site niet opnieuw te installeren. Wanneer de secundaire site is hersteld, wordt de site automatisch gesynchroniseerd met het distributiepunt.  

 U kunt de status van het herstel van secundaire site controleren via de **installatiestatus tonen** actie van de **Sites** knooppunt in de Configuration Manager-console.  

> [!IMPORTANT]  
>  U moet een computer gebruiken met dezelfde configuratie als de defecte computer, zoals de bijbehorende FQDN, om de secundaire site te kunnen herstellen. De computer moet tevens aan alle vereisten voor secundaire sites voldoen en moet zijn geconfigureerd met de juiste beveiligingsrechten Gebruik tevens hetzelfde installatiepad dat is gebruikt voor de uitgevallen site.  

> [!IMPORTANT]  
>  Tijdens het herstel van een secundaire site Configuration Manager heeft geen SQL Server Express installeren als dit niet is geïnstalleerd op de computer. Daarom moet u handmatig SQL Server Express of SQL Server installeren voordat u een secundaire site herstelt. U moet dezelfde versie van SQL Server en hetzelfde exemplaar van SQL Server gebruiken die/dat u voor de database van de secundaire site hebt gebruikt vóór de fout.  

##  <a name="BKMK_SMSWriterService"></a> SMS Writer-service  
 De SMS Writer is een service die communiceert met de VSS (Volume Shadow Copy Service) tijdens het back-upproces. De SMS Writer service moet worden uitgevoerd voor de achtergrond van Configuration Manager site tot is voltooid.  

### <a name="purpose"></a>Doel  
 SMS Writer registreert bij de VSS-service en wordt gekoppeld aan de betreffende interfaces en gebeurtenissen. Wanneer VSS gebeurtenissen uitzendt, of specifieke berichten naar de SMS Writer verstuurt, reageert de SMS Writer op het bericht en neemt de nodige actie. De SMS Writer leest het back-upcontrolebestand (smsbkup.ctl) zich in de &lt; *installatiepad voor Configuration Manager*> \inboxes\smsbkup.box en bepaalt van welke bestanden en gegevens die u wilt een back-up. De SMS Writer bouwt metadata die uit verscheidene onderdelen bestaan, gebaseerd op deze informatie en op specifieke gegevens van de SMS-registersleutel en subsleutels. De writer stuurt de metagegevens naar VSS wanneer deze wordt aangevraagd. VSS verzendt de metadata vervolgens naar de aanvragende toepassing; Configuration Manager Backup Manager. Backup Manager selecteer de gegevens waarvan een back-up wordt gemaakt en verzendt deze gegevens naar de SMS Writer via VSS. De SMS Writer neemt de nodige stappen om de back-up voor te bereiden. Later, wanneer VSS klaar is om een momentopname is, verzendt hij een gebeurtenis, de SMS Writer stopt alle Configuration Manager-services en zorgt ervoor dat de Configuration Manager-activiteiten worden bevroren onder de momentopname wordt gemaakt. Na voltooiing van de momentopname start de SMS Writer services en activiteiten opnieuw op.  

 De SMS Writer-service wordt automatisch geïnstalleerd. De service moet actief zijn wanneer de VSS-toepassing een back-up of herstel aanvraagt.  

### <a name="writer-id"></a>Schrijver-id  
 De schrijver-ID voor de SMS-schrijver is: 03ba67dd-dc6d-4729-a038-251f7018463b.  

### <a name="permissions"></a>Machtigingen  
 De SMS Writer-service moet onder het lokale systeemaccount worden uitgevoerd.  

### <a name="volume-shadow-copy-service"></a>Volume Shadow Copy-service  
 De VSS is een set van COM API's die een kader implementeert voor het maken van volume back-ups terwijl toepassingen op het systeem doorgaan met het schrijven naar de volumes. De VSS biedt een consistente interface die coördinatie toestaat tussen toepassingen die gegevens op schijf bijwerken (de SMS Writer-service) en toepassingen die back-ups maken van toepassingen (de Backup Manager-service). Zie het onderwerp [Volume Shadow Copy Service](http://go.microsoft.com/fwlink/p/?LinkId=241968) (Volume Shadow Copy-service) in het Windows Server TechCenter voor meer informatie over VSS.  

