---
title: Back-sites
titleSuffix: Configuration Manager
description: Informatie over het back-up van uw sites voordat de gebeurtenis van storing of gegevensverlies in System Center Configuration Manager.
ms.custom: na
ms.date: 6/5/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: f7832d83-9ae2-4530-8a77-790e0845e12f
caps.latest.revision: "22"
author: mstewart
ms.author: mstewart
manager: angrobe
ms.openlocfilehash: 55d7f4c45ac8cf95da3c46616d436e227ff87369
ms.sourcegitcommit: 7fe45ff75f05f7cc03ad021db8119791abe18049
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/01/2017
---
# <a name="back-up-a-configuration-manager-site"></a>Back-up van een Configuration Manager-site

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*

Bereid de back-up en herstel benaderingen om gegevensverlies te voorkomen. Voor Configuration Manager-sites kunt een back-up en herstel benadering u voor het herstellen van sites en hiërarchieën sneller en met de minimaal verlies van gegevens.  

De secties in dit onderwerp kunt u back-up van uw sites. Zie voor een site herstelt, [herstel voor Configuration Manager](/sccm/protect/understand/recover-sites).  

## <a name="considerations-before-creating-a-backup"></a>Overwegingen voor het maken van een back-up  
-   **Als u een SQL Server Always On-beschikbaarheidsgroep gebruikt om de sitedatabase te hosten:** Uw back-up- en herstelplannen aanpassen zoals is beschreven [voorbereiden op het gebruik van SQL Server Always On](/sccm/core/servers/deploy/configure/sql-server-alwayson-for-a-highly-available-site-database#changes-for-site-backup).

-   Configuration Manager kan de sitedatabase herstellen vanuit back-up onderhoudstaak van de Configuration Manager of vanuit een site-databaseback-up die u met een ander proces maakt.   

    U kunt bijvoorbeeld de sitedatabase herstellen vanuit een back-up die is gemaakt als onderdeel van een Microsoft SQL Server-onderhoudsplan. U kunt ook een back-up die is gemaakt door Data Protection Manager gebruiken voor back-up van uw sitedatabase (DPM) gebruiken.

####  <a name="using-data-protection-manager-to-back-up-your-site-database"></a>Data Protection Manager gebruiken om een back-up te maken van uw sitedatabase
U kunt System Center 2012 Data Protection Manager (DPM) gebruiken om een back-up te maken van uw sitedatabase.

U moet een nieuwe beveiligingsgroep maken in DPM voor de computer van de sitedatabase. Selecteer op de pagina **Groepsleden selecteren** van de wizard Nieuwe beveiligingsgroep maken de SMS Writer-service van de gegevensbronlijst en selecteer vervolgens de sitedatabase als een geschikt lid. Zie de [Documentatiebibliotheek voor Data Protection Manager](http://go.microsoft.com/fwlink/?LinkId=272772) op TechNet voor meer informatie over het gebruik van DPM om een back-up van uw sitedatabase te maken.  

> [!IMPORTANT]  
>  Configuration Manager biedt geen ondersteuning voor DPM terug voor een SQL servercluster dat een benoemd exemplaar gebruikt, maar biedt ondersteuning voor DPM een back-up in een SQL Server-cluster dat gebruik maakt van het standaardexemplaar van SQL Server.  

 Volg na herstel van de sitedatabase de stappen in Setup om de site te herstellen. Selecteer de **gebruik een sitedatabase die handmatig is hersteld** hersteloptie voor het gebruik van de sitedatabase die u hebt hersteld met Data Protection Manager.  

## <a name="backup-maintenance-task"></a>Back-uponderhoudstaak
U kunt back-up voor Configuration Manager-sites automatiseren door het plannen van de vooraf gedefinieerde onderhoudstaak voor back-upserver van Site. Deze taak:

-   Volgens een planning wordt uitgevoerd
-   Een back-up maakt van de sitedatabase
-   Een back-up maakt van specifieke registersleutels
-   Een back-up maakt van specifieke mappen en bestanden
-   Back-ups van de [CD. Meest recente map](/sccm/core/servers/manage/the-cd.latest-folder)   

Plan om de standaardback-uptaak voor de site minimaal elke vijf dagen uit te voeren. Dit is omdat Configuration Manager gebruikt een *bewaarperiode voor bijhouden van SQL Server* van 5 dagen.  (Zie [bewaarperiode voor bijhouden van SQL Server](/sccm/protect/understand/recover-sites#bkmk_SQLretention) in het onderwerp van de sites herstellen.)

Als u wilt het back-upproces vereenvoudigen, kunt u een **AfterBackup.bat** bestand automatisch uit te voeren na de back-up nadat de onderhoudstaak back-up wordt uitgevoerd. Het AfterBackup.bat-bestand wordt meestal gebruikt om de momentopname van de back-up naar een veilige locatie. U kunt het AfterBackup.bat-bestand ook gebruiken om te kopiëren van bestanden naar uw back-upmap en andere, aanvullende back-uptaken te beginnen.  

U kunt een back-up maken van een centrale beheersite en primaire site, maar niet van secundaire sites of sitesysteemservers.

Wanneer de Backup-service van Configuration Manager wordt uitgevoerd, de instructies gevolgd die gedefinieerd in het back-upcontrolebestand (**&lt;ConfigMgrInstallationFolder\>\Inboxes\Smsbkup.box\Smsbkup.ctl**). U kunt het back-upcontrolebestand aanpassen om het gedrag van de back-upservice te wijzigen.  

Informatie voor siteback-upstatus wordt geschreven naar het bestand **Smsbkup.log** . Het bestand wordt gemaakt in de doelmap die u specificeert in de eigenschappen van de onderhoudstaak van de back-upserver van site.  

#### <a name="to-enable-the-site-backup-maintenance-task"></a>De onderhoudstaak van de back-upserver van site inschakelen  

1.  Open in de Configuration Manager-console **beheer** > **siteconfiguratie** > **Sites**.  

2.  Selecteer de site waarin u de onderhoudstaak van de back-upserver van site wilt inschakelen.  

3.  Op de **Start** tabblad, in de **instellingen** groep, kiest u **Siteonderhoudstaken**.  

4.  Kies **back-upserver van Site**  >  **bewerken**.  

5.  Kies **deze taak inschakelen** > **paden instellen** om de back-updoelmap te specificeren. U hebt de volgende opties:  

    > [!IMPORTANT]  
    >  Sla ter voorkoming van knoeien met de back-upbestanden deze op een veilige locatie op. Het veiligste back-uppad is naar een lokaal station zodat u machtigingen voor NTFS-bestandssysteem op de map instellen kunt. Configuration Manager wordt niet gecodeerd voor de back-upgegevens die in de back-uppad zijn opgeslagen.  

    -   **Lokaal station op siteserver voor sitegegevens en database**: Hiermee geeft u op dat de back-upbestanden voor de site en sitedatabase zijn opgeslagen in het opgegeven pad op de lokale vaste schijf van de siteserver. U moet de lokale map maken voordat de back-uptaak wordt uitgevoerd. Het lokale systeemaccount op de siteserver moet **schrijf** machtigingen hebben voor het NTFS-bestandssysteem naar de lokale map voor de back-up van de siteserver. Het lokale systeemaccount op de computer waarop de SQL Server wordt uitgevoerd, moet **schrijf** machtigingen hebben voor NTFS naar de map voor de back-up van de sitedatabase.  

    -   **Netwerkpad (UNC-naam) voor sitegegevens en database**: Hiermee geeft u op dat de back-upbestanden voor de site en sitedatabase zijn opgeslagen in het opgegeven UNC-pad. U moet de share maken voordat de back-uptaak wordt uitgevoerd. Het computeraccount van de siteserver en het computeraccount van de SQL Server moeten, als SQL Server is geïnstalleerd op een andere computer, beschikken over **schrijf** machtigingen voor NTFS en deelmachtigingen naar de gedeelde netwerkmap.  

    -   **Lokale stations op siteserver en SQL Server**: Hiermee geeft u op dat de back-upbestanden voor de site worden opgeslagen in het opgegeven pad op de lokale schijf van de siteserver en de back-upbestanden voor de sitedatabase zijn opgeslagen in het opgegeven pad op het lokale station van de Sitedatabaseserver. U moet de lokale mappen maken voordat de back-uptaak wordt uitgevoerd. Het computeraccount van de siteserver moet **schrijf** machtigingen hebben voor NTFS naar de map die u maakt op de siteserver. Het computeraccount van de SQL Server moet **schrijf** machtigingen hebben voor NTFS naar de map die u maakt op de sitedatabaseserver. U kunt deze optie alleen gebruiken wanneer de sitedatabase niet is geïnstalleerd op de siteserver.  

    > [!NOTE]  
    >   U kunt de optie om te bladeren naar de back-updoelmap alleen gebruiken wanneer u het UNC-pad opgeeft van de back-updoelmap.

    > De voor de back-updoelmap gebruikte map- of sharenaam ondersteunt niet het gebruik van Unicode-tekens.  

6.  Configureer een planning voor de back-uptaak van de site. De aanbevolen planning voor het uitvoeren van een back-up is buiten werkuren. Als u een hiërarchie hebt, overweeg dan een planning die ten minste tweemaal per week wordt uitgevoerd voor maximale gegevensretentie in het geval van het uitvallen van een site.  

    Wanneer u de Configuration Manager-console op dezelfde siteserver die u configureert voor back-up uitvoert, gebruikt de onderhoudstaak back-upserver van Site de lokale tijd voor de planning. Wanneer de Configuration Manager-console wordt uitgevoerd vanaf een computer die extern zijn van de site die u voor back-up configureert, gebruikt de onderhoudstaak back-upserver van Site UTC voor de planning.  

7.  Kies of u wilt maken van een waarschuwing als de site back-uptaak mislukt, klikt u op **OK**, en klik vervolgens op **OK**. Wanneer u selecteert, Configuration Manager maakt een kritieke waarschuwing voor de back-upfouten die u kunt bekijken in de **waarschuwingen** knooppunt in de **bewaking** werkruimte.  

 Controleer vervolgens of de onderhoudstaak Backup siteserver wordt uitgevoerd, om ervoor te zorgen dat back-ups worden gemaakt.  

#### <a name="to-verify-that-the-backup-site-server-maintenance-task-is-running"></a>Om te controleren of de onderhoudstaak Backup siteserver wordt uitgevoerd  
Controleren of de onderhoudstaak van de siteback-up wordt uitgevoerd door het nagaan van het volgende:  

-   Controleer de tijdstempel op de bestanden in de back-updoelmap die de taak gemaakt. Controleer of de tijdstempel is bijgewerkt met een tijd die overeenkomt met de tijd wanneer de taak voor het laatst is gepland om uit te voeren.  

-   Controleer in het knooppunt **Onderdeelstatus** in de werkruimte **Bewaking** de statusberichten voor SMS_SITE_BACKUP. Als de siteback-up correct is voltooid, ziet u het bericht ID 5035 dat aangeeft dat de siteback-up zonder fouten is voltooid.  

-   Als de onderhoudstaak van de back-upserver van de site is ingesteld op het genereren van een waarschuwing als de back-up mislukt, kunt u het knooppunt **Waarschuwingen** in de werkruimte **Bewaking** controleren op mislukte back-ups.  

-   In &lt; *ConfigMgrInstallationFolder*> \Logs, Controleer het bestand Smsbkup.log op waarschuwingen en fouten. Als de siteback-up correct is voltooid, ziet u `Backup completed` met een tijdstempel en bericht-id `STATMSG: ID=5035`.  

    > [!TIP]  
    >  Als de onderhoudstaak van de back-up mislukt, kunt u de back-uptaak opnieuw starten door de SMS_SITE_BACKUP-service te stoppen en opnieuw te starten.  

## <a name="archive-the-backup-snapshot"></a>De back-upmomentopname archiveren  
De eerste keer dat de onderhoudstaak van de back-upserver van site wordt uitgevoerd, wordt een momentopname gemaakt van de back-up die u kunt gebruiken om uw siteserver te herstellen in het geval van een storing. Wanneer de back-uptaak opnieuw wordt uitgevoerd in latere runs, wordt een nieuwe momentopname gemaakt van de back-up die de vorige momentopname overschrijft. De site heeft daarom slechts één back-upmomentopname en u kunt eerdere momentopnames niet herstellen.  

Het wordt om de volgende redenen aanbevolen meerdere archieven van de back-upmomentopname te bewaren:  

-   Het is gebruikelijk voor back-upmedia een fout optreedt, ze foutief worden geplaatst of bevatten alleen een gedeeltelijke back-up. Een mislukte zelfstandige primaire site op basis van een oudere back-up herstellen is beter dan deze zonder back-up te herstellen. Voor een siteserver in een hiërarchie moet de back-up in de bewaarperiode voor het bijhouden van wijzigingen van de SQL Server liggen, of de back-up is niet vereist.  

-   Een beschadiging in de site kan gedurende verschillende back-upcycli ongedetecteerd blijven. Mogelijk moet een back-upmomentopname uit voor de site beschadigd geraakte gebruiken. Dit geldt voor een zelfstandige primaire site en naar sites in een hiërarchie waar de back-up in de SQL-Server bijhouden bewaarperiode.  

-   De site heeft mogelijk helemaal geen back-upmomentopname, als de onderhoudstaak van de Back-upserver van site bijvoorbeeld is mislukt. Omdat de back-uptaak de vorige back-upmomentopname verwijdert voordat het een back-up begint te maken van de huidige gegevens, zal er geen geldige back-upmomentopname zijn.  

## <a name="using-the-afterbackupbat-file"></a>Het bestand AfterBackup.bat gebruiken  
Na een back-up van de site gemaakt te hebben, probeert de taak Back-upserver van site automatisch een bestand uit te voeren dat AfterBackup.bat heet. U moet het AfterBackup.bat-bestand in handmatig maken &lt; *ConfigMgrInstallationFolder*> \Inboxes\Smsbkup. Als er een AfterBackup.bat-bestand bestaat en in de juiste map is opgeslagen, wordt automatisch uitgevoerd nadat de back-uptaak is voltooid.

Het AfterBackup.bat-bestand laat u de back-upmomentopname archiveren aan het einde van elke back-upbewerking, en voert automatisch andere post-back-uptaken uit die geen deel uitmaken van de onderhoudstaak Back-upserver van site. Het AfterBackup.bat-bestand integreert het archief en de back-upbewerkingen, waardoor elke nieuwe back-upmomentopname wordt gearchiveerd.

Wanneer het AfterBackup.bat-bestand niet aanwezig is, slaat de back-uptaak het over zonder dat het een invloed heeft op de back-upbewerking. Zie het knooppunt **Onderdeelstatus** in de werkruimte **Bewaking** en bekijk de statusberichten voor SMS_SITE_BACKUP om te controleren of de back-uptaak van de site het bestand AfterBackup.bat heeft uitgevoerd. Wanneer de taak het AfterBackup.bat-opdrachtbestand heeft gestart, ziet u de boodschap ID 5040.  

> [!TIP]  
>  Voor het maken van het AfterBackup.bat-bestand voor het archiveren van back-upbestanden van de siteserver, moet u een kopieeropdrachthulpprogramma zoals [Robocopy](http://go.microsoft.com/fwlink/p/?LinkId=228408), in de batch-bestand. Bijvoorbeeld, u kunt het AfterBackup.bat-bestand maken en op de eerste lijn zou u ongeveer als volgt:`Robocopy E:\ConfigMgr_Backup \\ServerName\ShareName\ConfigMgr_Backup /MIR`  

 Hoewel het beoogde gebruik van het bestand AfterBackup.bat het archiveren van back-upmomentopnamen is, kunt u het bestand AfterBackup.bat aanmaken om extra taken uit te voeren aan het einde van elke back-upbewerking.  

##  <a name="supplemental-backup-tasks"></a>Aanvullende back-uptaken  
De onderhoudstaak Back-upserver van site biedt een back-upmomentopname voor de siteserverbestanden en sitedatabase, maar er zijn andere items waarvan geen back-up is gemaakt die u moet overwegen wanneer u uw back-upstrategie bepaalt. Gebruik de volgende secties voor hulp bij het voltooien van uw Configuration Manager back-upstrategie.  

### <a name="back-up-custom-reporting-services-reports"></a>Back-up maken van aangepaste rapporten van Reporting Services  
Wanneer u vooraf bepaalde of gemaakte aangepaste rappoten voor Reporting Services hebt gewijzigd, is het maken van een back-up voor de databasebestanden van de rapportserver een belangrijk onderdeel van uw back-upstrategie. De back-up van de rapportserver moet een back-up van de bronbestanden omvatten voor rapporten en modellen, versleutelingssleutels, aangepaste assembly's of extensies, configuratiebestanden, aangepaste SQL Server-weergaven in aangepaste rapporten, aangepaste opgeslagen procedures, enzovoort.  

> [!IMPORTANT]  
>  Wanneer de Configuration Manager-updates naar een nieuwere versie, worden de vooraf gedefinieerde rapporten mogelijk overschreven door nieuwe rapporten. Als u een vooraf gedefinieerd rapport wijzigt, back-up van het rapport en vervolgens herstellen in Reporting Services.  

 Zie [Backup and Restore Operations for a Reporting Services Installation (Back-up- en terugzetbewerkingen voor een installatie van Reporting Services)](https://technet.microsoft.com/library/ms155814\(v=sql.120\).aspx) in de SQL Server 2014 Books Online voor meer informatie over het maken van back-ups van uw aangepaste rapporten in Reporting Services.  

### <a name="back-up-content-files"></a>Back-up van inhoudsbestanden  
De Inhoudsbibliotheek in Configuration Manager is de locatie waar alle inhoudsbestanden worden opgeslagen voor software-updates, toepassingen en implementatie van besturingssystemen. De Inhoudsbibliotheek bevindt zich op de siteserver en op elk distributiepunt. De onderhoudstaak Back-upserver van site omvat geen back-up voor de inhoudsbibliotheek of de pakketbronbestanden. Wanneer er een fout optreedt op een siteserver wordt de informatie over de inhoudsbibliotheek teruggezet op de sitedatabase, maar moet u de inhoudsbibliotheek en pakketbronbestanden op de siteserver terugzetten.  

-   **Inhoudsbibliotheek**: De Inhoudsbibliotheek moet worden hersteld voordat u inhoud opnieuw naar distributiepunten distribueren kunt. Wanneer u de herdistributie van inhoud start, kopieert Configuration Manager de bestanden van de Inhoudsbibliotheek op de siteserver naar de distributiepunten. De Inhoudsbibliotheek voor de siteserver is in de map SCCMContentLib, die meestal zich bevindt op het station met de meeste vrije schijfruimte op het tijdstip waarop de site is geïnstalleerd.  

-   **Pakketbronbestanden**: De pakketbronbestanden moeten worden hersteld voordat u inhoud op distributiepunten kunt bijwerken. Wanneer u een update van inhoud start, Configuration Manager worden nieuwe of gewijzigde bestanden gekopieerd van de pakketbron naar de Inhoudsbibliotheek, die in Schakel exemplaren bestanden voor de gekoppelde distributiepunten verwijst. U kunt de volgende query in SQL Server uitvoeren om de locatie van de pakketbron voor alle pakketten en toepassingen te vinden: `SELECT * FROM v_Package`. U kunt de locatie van de pakketbron vinden door de eerste drie tekens van de pakket-id te bekijken. Als de pakket-id bijvoorbeeld CEN00001 is, is de sitecode van de bronsite CEN. Wanneer u de pakketbronbestanden herstelt, moeten u deze op dezelfde locatie waar ze vóór de fout was hersteld.  

 Controleer dat u zowel de inhoudsbibliotheek als pakketbronlocaties in de back-up van uw bestandssysteem voor de siteserver opneemt.  

### <a name="back-up-custom-software-updates"></a>Back-up maken van aangepaste software-updates  
 System Center Updates Publisher 2011 is een zelfstandig hulpprogramma waarmee u aangepaste software-updates publiceren naar Windows Server Update Services (WSUS), synchroniseren van de software-updates voor Configuration Manager, compatibiliteit van software-updates vaststelt en de aangepaste software-updates implementeren op clients. Updates Publisher gebruikt een lokale database voor de software-update opslagplaats. Wanneer u Updates Publisher gebruikt om aangepaste software-updates te beheren, moet u bepalen of u de Updates Publisher-database in uw back-upplan moet opnemen. Zie [System Center Updates Publisher 2011](http://go.microsoft.com/fwlink/p/?LinkId=228726) in de System Center TechCenter Library voor meer informatie over Updates Publisher.  

 Gebruik de volgende procedure back-up van de Updates Publisher-database.  

#### <a name="to-back-up-the-updates-publisher-2011-database"></a>Een back-up maken van de Updates Publisher 2011-database  

1.  Op de computer waarop Updates Publisher wordt uitgevoerd, bladert u naar de Updates Publisher-databasebestand (Scupdb.sdf) in %*USERPROFILE*%\AppData\Local\Microsoft\System Center Updates Publisher 2011\5.00.1727.0000\\\. Er is een verschillend databasebestand voor elke gebruiker waarop Updates Publisher wordt uitgevoerd.  

2.  Kopieer het databasebestand naar uw back-upbestemming. Als uw back-upbestemming E:\ConfigMgr_Backup is, kunt u het databasebestand Updates Publisher kopiëren naar E:\ConfigMgr_Backup\SCUP2011.  

    > [!TIP]  
    >  Wanneer er meer dan één databasebestand op een computer, overweeg dan het bestand opslaan in een submap die aangeeft het gebruikersprofiel die zijn gekoppeld aan het databasebestand dat. U zou bijvoorbeeld één databasebestand kunnen hebben in E:\ConfigMgr_Backup\SCUP2011\User1 en een ander databasebestand in E:\ConfigMgr_Backup\SCUP2011\User2.  

## <a name="user-state-migration-data"></a>Migratiegegevens van de gebruikersstatus  
U kunt takenreeksen Configuration Manager vastleggen en herstellen van de gebruikersstatusgegevens in implementatiescenario's van besturingssysteem waar u wilt bewaren van de gebruikersstatus van het huidige besturingssysteem. De mappen waarin de gegevens met betrekking tot de gebruikersstatus zijn opgeslagen, staan in de eigenschappen voor het statusmigratiepunt. Van deze migratiegegevens van de gebruikersstatus wordt geen back-up gemaakt als onderdeel van de onderhoudstaak Back-upserver van site. Als deel van uw back-upplan moet u handmatig een back-up maken van de mappen die u specificeert om de migratiegegevens van de gebruikersstatus op te slaan.   

### <a name="to-determine-the-folders-used-to-store-user-state-migration-data"></a>De mappen bepalen die worden gebruikt om migratiegegevens van de gebruikersstatus op te slaan  

1.  Klik op **Beheer**in de Configuration Manager-console.  

2.  In de **beheer** werkruimte Vouw **siteconfiguratie**, en kies **Servers en sitesysteemrollen**.  

3.  Selecteer het sitesysteem dat de statusmigratierol host, en kies **Statusmigratiepunt** in **sitesysteemrollen**.  


4.  Klik op het tabblad **Siterol** in de groep **Eigenschappen** op **Eigenschappen**.  
5.  De mappen waar de migratiegegevens van de gebruikersstatus worden opgeslagen, staan in de sectie **Mapdetails** op het tabblad **Algemeen** .  



## <a name="about-the-sms-writer-service"></a>Over de SMS Writer-service  
De SMS Writer is een service die communiceert met de VSS (Volume Shadow Copy Service) tijdens het back-upproces. De SMS Writer-service moet worden uitgevoerd voor de Configuration Manager-site-back maximaal met succes voltooid.  

### <a name="purpose"></a>Doel  
SMS Writer registreert bij de VSS-service en wordt gekoppeld aan de betreffende interfaces en gebeurtenissen. Wanneer VSS gebeurtenissen uitzendt, of specifieke berichten naar de SMS Writer verstuurt, reageert de SMS Writer op het bericht en neemt de nodige actie. De SMS Writer leest het back-upcontrolebestand (smsbkup.ctl) zich in de &lt; *ConfigMgr-installatiepad*> \inboxes\smsbkup.box en bepaalt welke bestanden en gegevens die u wilt back-up worden gemaakt. De SMS Writer bouwt metadata die uit verscheidene onderdelen bestaan, gebaseerd op deze informatie en op specifieke gegevens van de SMS-registersleutel en subsleutels. De writer stuurt de metagegevens naar VSS wanneer deze wordt aangevraagd. VSS verzendt de metadata vervolgens naar de aanvragende toepassing; Manager van Configuration Manager back-up. Backup Manager selecteer de gegevens waarvan een back-up wordt gemaakt en verzendt deze gegevens naar de SMS Writer via VSS. De SMS Writer neemt de nodige stappen om de back-up voor te bereiden. Later, wanneer VSS klaar is om een momentopname te is, verzendt hij een gebeurtenis, de SMS Writer stopt alle Configuration Manager-services en zorgt ervoor dat de Configuration Manager-activiteiten worden bevroren onder de momentopname wordt gemaakt. Na voltooiing van de momentopname start de SMS Writer services en activiteiten opnieuw op.  

De SMS Writer-service wordt automatisch geïnstalleerd. De service moet actief zijn wanneer de VSS-toepassing een back-up of herstel aanvraagt.  

### <a name="writer-id"></a>Schrijver-id  
De schrijver-ID voor de SMS Writer is: 03ba67dd-dc6d-4729-a038-251f7018463b.  

### <a name="permissions"></a>Machtigingen  
De SMS Writer-service moet onder het lokale systeemaccount worden uitgevoerd.  

### <a name="volume-shadow-copy-service"></a>Volume Shadow Copy-service  
De VSS is een set van COM API's die een kader implementeert voor het maken van volume back-ups terwijl toepassingen op het systeem doorgaan met het schrijven naar de volumes. De VSS biedt een consistente interface die coördinatie toestaat tussen toepassingen die gegevens op schijf bijwerken (de SMS Writer-service) en toepassingen die back-ups maken van toepassingen (de Backup Manager-service). Zie voor meer informatie de [Volume Shadow Copy Service](http://go.microsoft.com/fwlink/p/?LinkId=241968) onderwerp in het Windows Server TechCenter.  

## <a name="next-steps"></a>Volgende stappen
Nadat u een back-up hebt gemaakt, in de praktijk [site recovery](/sccm/protect/understand/recover-sites) met back-up. Hiermee kunt u meer vertrouwd raken met het herstelproces voordat u moet erop vertrouwen en kan helpen bij het bevestigen van de back-up is voltooid voor het beoogde doel.  
