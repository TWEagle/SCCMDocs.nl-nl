---
title: Site recovery | Microsoft Docs
description: Informatie over het herstellen van uw sites in System Center Configuration Manager.
ms.custom: na
ms.date: 6/5/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 19539f4d-1667-4b4c-99a1-9995f12cf5f7
caps.latest.revision: 
author: Brenduns
ms.author: brenduns
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: f7cd9c71287d62c9f5d36e2f032bc2a6065572ae
ms.openlocfilehash: 49eea15ea2888f8f93c33eb771c09147ba21529e
ms.contentlocale: nl-nl
ms.lasthandoff: 06/06/2017

---

#  <a name="recover-a-configuration-manager-site"></a>Een Configuration Manager-site herstellen

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*

Een Configuration Manager uitvoeren siteherstel nadat een Configuration Manager-site is mislukt of gegevensverlies in de sitedatabase optreedt. Het herstellen en opnieuw synchroniseren van gegevens zijn de belangrijkste taken van een siteherstel en zijn nodig om een onderbreking van de bewerkingen te voorkomen.

De secties in dit onderwerp kunt u een Configuration Manager-site te herstellen. Zie het maken van een back-up [voor Configuration Manager back-](/sccm/protect/understand/backup-and-recovery).

## <a name="considerations-before-recovering-a-site"></a>Overwegingen voor het herstellen van een site
**U moet dezelfde versie en editie van SQL Server gebruiken:** Bijvoorbeeld: terugzetten van een database die is uitgevoerd op SQL Server 2014 naar SQL Server-2016is niet ondersteund. Op deze manier wordt terugzetten van een sitedatabase die is uitgevoerd op een Standard-editie van SQL Server 2016 naar een Enterprise-editie van SQL Server 2016 niet ondersteund.
-   SQL Server moet niet worden ingesteld op **modus voor één gebruiker**.
-   Controleer of de .MDF- en .LDF-bestanden geldig zijn. Wanneer u een site herstelt, is er geen controle voor de status van de bestanden die u wilt herstellen.

**Als u een SQL Server Always On-beschikbaarheidsgroep gebruikt om de sitedatabase te hosten:** De herstelplannen aanpassen zoals is beschreven [voorbereiden op het gebruik van SQL Server Always On](/sccm/core/servers/deploy/configure/sql-server-alwayson-for-a-highly-available-site-database#changes-for-site-recovery).

**Wanneer u Databasereplica's gebruikt:** Als u een sitedatabase herstelt die was geconfigureerd voor databasereplica's, moet u, voordat u de databasereplica's kunt gebruiken, elke databasereplica opnieuw configureren, waarbij zowel de publicaties als abonnementen opnieuw worden gemaakt.

## <a name="determine-your-recovery-options"></a>Uw herstelopties bepalen
Er zijn twee hoofdgebieden in overweging moet nemen voor de primaire siteserver van Configuration Manager en herstel van centrale beheersite; de **siteserver** en de **sitedatabase**.
De volgende secties kunt u selecteert de beste opties voor uw herstelscenario.

> [!NOTE]   
> Wanneer wordt gedetecteerd dat een bestaande Configuration Manager-site op de server, kunt u een siteherstel starten, maar de herstelopties voor de siteserver zijn beperkt. Als u het installatieprogramma bijvoorbeeld uitvoert op een bestaande siteserver, wanneer u herstel kiest, kunt u de sitedatabaseserver herstellen, maar is de optie om de siteserver te herstellen uitgeschakeld.

### <a name="site-server-recovery-options"></a>Opties voor herstel van de siteserver
Het installatieprogramma starten vanaf een kopie van de **CD. Meest recente** map die u hebt gemaakt buiten de installatiemap van Configuration Manager.
-   Als u Configuration Manager Setup vanuit uitvoeren de **Start** menu op de siteserver de **een site herstellen** optie is niet beschikbaar.
-   Als u eventuele updates van de Configuration Manager-console geïnstalleerd voordat u uw back-up hebt gemaakt, kunt u de site niet opnieuw installeren met behulp van Setup uit vanaf installatiemedia of het pad voor de Configuration Manager-installatie.

Selecteer vervolgens de **een site herstellen** optie. U hebt de volgende herstelopties voor de mislukte siteserver:

-   **De siteserver met behulp van een bestaande back-up herstellen:** Gebruik deze optie wanneer er een back-up van de siteserver van Configuration Manager die op de siteserver is gemaakt als onderdeel van de **back-upserver van Site** onderhoudstaak vóór de sitefout. De site wordt opnieuw geïnstalleerd, en de site-instellingen worden geconfigureerd, op basis van de site waarvan een back-up was gemaakt.
-   **De siteserver opnieuw installeren:** Gebruik deze optie wanneer u een back-up van de siteserver niet hebt. De siteserver wordt opnieuw geïnstalleerd, en u moet de site-instellingen opgeven, net zoals u zou doen tijdens een eerste installatie.
  -   U moet de dezelfde sitecode en Sitedatabasenaam die u hebt gebruikt toen de mislukte site is geïnstalleerd.
  -   U kunt de site opnieuw installeren op een nieuwe computer die een nieuw besturingssysteem wordt uitgevoerd.
  -   De computer moet dezelfde naam, FQDN van de oorspronkelijke siteserver gebruiken.   

### <a name="site-database-recovery-options"></a>Opties voor herstel van de sitedatabase
Wanneer u het installatieprogramma uitvoert, hebt u de volgende herstelopties voor de sitedatabase:
-   **De sitedatabase met behulp van een back-upset herstellen:** Gebruik deze optie wanneer er een back-up van de Configuration Manager-sitedatabase die is gemaakt als onderdeel van de **back-upserver van Site** onderhoudstaak uitgevoerd op de site voordat de sitedatabasefout zich voordeed. Wanneer u een hiërarchie hebt, worden de wijzigingen die zijn aangebracht aan de sitedatabase na de laatste back-up van de sitedatabase opgehaald uit de centrale beheersite voor een primaire site, of uit een primaire referentiesite voor een centrale beheersite. Wanneer u de sitedatabase voor een zelfstandige primaire site herstelt, gaan de sitewijzigingen na de laatste back-up verloren.

   Wanneer u de sitedatabase voor een site in een hiërarchie herstelt, is het herstelgedrag verschillend voor een centrale beheersite en primaire site, en wanneer de laatste back-up binnen of buiten de bewaarperiode voor het bijhouden van wijzigingen van de SQL Server ligt. Zie de rubriek [Herstelscenario's voor sitedatabase](##site-database-recovery-scenarios) in dit onderwerp voor meer informatie.
  > [!NOTE]   
  > Het herstel mislukt als u ervoor kiest de sitedatabase te herstellen met behulp van een back-upset, maar de sitedatabase reeds bestaat.  

-   **Maak een nieuwe database voor deze site:** Gebruik deze optie wanneer u niet een back-up van de Configuration Manager-sitedatabase hebt. Wanneer u een hiërarchie hebt, wordt er een nieuwe sitedatabase gemaakt, en worden de gegevens hersteld met behulp van gerepliceerde gegevens van de centrale beheersite voor een primaire site, of een primaire referentiesite voor een centrale beheersite. Deze optie is niet beschikbaar wanneer u een zelfstandige primaire site of een centrale beheersite herstelt die geen primaire sites heeft.

-   **Gebruik een sitedatabase die handmatig is hersteld:** Gebruik deze optie wanneer u de Configuration Manager-sitedatabase al hebt hersteld, maar het herstelproces moet voltooien.
    -   Configuration Manager kan de sitedatabase herstellen vanuit back-up onderhoudstaak van de Configuration Manager of vanuit een site-databaseback-up die u uitvoert door DPM of een ander proces. Nadat u de sitedatabase herstellen met behulp van een methode buiten Configuration Manager, moet u Setup uitvoert en selecteer deze optie om het herstel van de sitedatabase te voltooien.

    > [!NOTE]   
    > Wanneer u DPM back-up van uw sitedatabase gebruikt, gebruikt u de DPM-procedures voor het herstellen van de sitedatabase naar een opgegeven locatie voordat u het herstelproces in Configuration Manager verderzet. Zie de [Documentatiebibliotheek voor de Data Protection Manager]() op TechNet Voor meer informatie over DPM.    

    -   Wanneer u een hiërarchie hebt, worden de wijzigingen die zijn aangebracht aan de sitedatabase na de laatste back-up van de sitedatabase opgehaald uit de centrale beheersite voor een primaire site, of uit een primaire referentiesite voor een centrale beheersite. Wanneer u de sitedatabase voor een zelfstandige primaire site herstelt, gaan de sitewijzigingen na de laatste back-up verloren.     


-   **Databaseherstel overslaan:** Gebruik deze optie wanneer er geen gegevensverlies is opgetreden op de Sitedatabaseserver van Configuration Manager. Deze optie is enkel geldig wanneer de sitedatabase zich op een andere computer bevindt dan de siteserver die u aan het herstellen bent.

### <a name="sql-server-change-tracking-retention-period"></a>Bewaarperiode voor het bijhouden van wijzigingen van de SQL Server
Het bijhouden van wijzigingen is ingeschakeld voor de sitedatabase in SQL Server. Wijzigingen bijhouden kunt Configuration Manager informatie opvragen over de wijzigingen die zijn aangebracht aan databasetabellen na een eerder punt in tijd. De bewaarperiode specificeert hoe lang informatie over het bijhouden van wijzigingen wordt bewaard. De sitedatabase is standaard geconfigureerd om een bewaarperiode van vijf dagen te hebben. Wanneer u een sitedatabase herstelt, vindt het herstelproces anders plaats als uw back-up binnen of buiten de bewaarperiode valt. Als er bijvoorbeeld een fout optreedt op de sitedatabaseserver, en uw laatste back-up is 7 dagen oud, dan valt het buiten de bewaarperiode.

Zie voor meer informatie over SQL Server-bijhouden interne werking van de volgende blogs van het team van SQL Server: [Het bijhouden van opschoning - deel 1](https://blogs.msdn.microsoft.com/sql_server_team/change-tracking-cleanup-part-1/) en [Change Tracking opschoning - deel 2](https://blogs.msdn.microsoft.com/sql_server_team/change-tracking-cleanup-part-2).

### <a name="reinitialization-of-site-or-global-data"></a>Herinitialisatie van de site of globale gegevens
Het proces om site- of algemene gegevens opnieuw te initialiseren vervangt bestaande gegevens in de sitedatabase door gegevens uit een andere sitedatabase. Wanneer site ABC bijvoorbeeld gegevens opnieuw initialiseert van site XYR, dan vinden de volgende stappen plaats:
-   De gegevens worden van site XYZ naar site ABC gekopieerd.
-   De bestaande gegevens voor site XYZ worden verwijderd uit de sitedatabase op site ABC.
-   De gekopieerde gegevens van site XYZ worden opgenomen in de sitedatabase op site ABC.

#### <a name="example-scenario-1"></a>Voorbeeldscenario 1
**De primaire site initialiseert de algemene gegevens uit de centrale beheersite opnieuw:** Het herstelproces verwijdert de bestaande algemene gegevens voor de primaire site in de primaire sitedatabase en vervangt de gegevens door de algemene gegevens gekopieerd van de centrale beheersite.

#### <a name="example-scenario-2"></a>Voorbeeldscenario 2
**De centrale beheersite initialiseert de sitegegevens uit een primaire site opnieuw:** Het herstelproces verwijdert de bestaande sitegegevens voor die primaire site in de database van centrale beheersite en vervangt de gegevens door de sitegegevens die zijn gekopieerd uit de primaire site. De sitegegevens voor andere primaire sites blijven onveranderd.

### <a name="site-database-recovery-scenarios"></a>Scenario's voor het herstel van een sitedatabase
Nadat een sitedatabase is hersteld van een back-up, probeert de Configuration Manager de wijzigingen te herstellen in site- en algemene gegevens na de laatste databaseback-up. De volgende beschrijven de acties die begint met Configuration Manager nadat een sitedatabase is hersteld vanuit back-up.

**De herstelde site is een centrale beheersite:**
-   **Back-up van database binnen de bewaarperiode voor het bijhouden van wijzigingen**
    -   **Globale gegevens:** De wijzigingen in globale gegevens na de back-up worden gerepliceerd vanaf alle primaire sites.
    -   **Sitegegevens:** De wijzigingen in sitegegevens na de back-up worden gerepliceerd vanaf alle primaire sites.


-   **Databaseback-up ouder is dan de bewaarperiode voor het bijhouden van wijzigingen**
    -   **Globale gegevens:** De centrale beheersite initialiseert de algemene gegevens uit de primaire referentiesite opnieuw, indien u dit opgeeft. Dan initialiseren alle andere primaire sites de algemene gegevens uit de centrale beheersite opnieuw. Indien er geen referentiesite is opgegeven, initialiseren alle primaire sites de algemene gegevens uit de centrale beheersite opnieuw (de gegevens die waren hersteld op basis van de back-up).
    -   **Sitegegevens:** De centrale beheersite initialiseert de sitegegevens van elke primaire site opnieuw.


**De herstelde site is een primaire site:**
-   **Back-up van database binnen de bewaarperiode voor het bijhouden van wijzigingen**
    -   **Globale gegevens:** De wijzigingen in globale gegevens na de back-up worden gerepliceerd uit de centrale beheersite.
    -   **Sitegegevens:** De centrale beheersite initialiseert de sitegegevens uit de primaire site opnieuw. Wijzigingen na de back-up gaan verloren, maar de meeste gegevens worden opnieuw gegenereerd door clients die informatie naar de primaire site sturen.


-   **Databaseback-up ouder is dan de bewaarperiode voor het bijhouden van wijzigingen**
    -   **Globale gegevens:** De primaire site initialiseert de algemene gegevens uit de centrale beheersite opnieuw.
    -   **Sitegegevens:** De centrale beheersite initialiseert de sitegegevens uit de primaire site opnieuw. Wijzigingen na de back-up gaan verloren, maar de meeste gegevens worden opnieuw gegenereerd door clients die informatie naar de primaire site sturen.

## <a name="site-recovery-procedures"></a>Procedures voor het herstellen van een site
Gebruik een van de volgende procedures om u te helpen uw siteserver en sitedatabase te herstellen.

### <a name="to-start-a-site-recovery-in-the-setup-wizard"></a>Een siteherstel in de Installatiewizard starten
1.  Kopieer de [CD. Meest recente map](/sccm/core/servers/manage/the-cd.latest-folde) naar een locatie buiten de installatiemap van Configuration Manager.
Via de kopie van de CD. Meest recente map, voer de installatiewizard van Configuration Manager.

2.  Op de pagina **Aan de slag** selecteert u **Een site herstellen**en klikt u vervolgens op **Volgende**.

3.  Voltooi de wizard met behulp van de opties die geschikt zijn voor uw siteherstel.

  -   Tijdens het herstel identificeert het installatieprogramma de SQL Server Service Broker (SBB)-poort die wordt gebruikt door de SQL Server. Wijzig deze poortinstelling niet tijdens het herstel of de gegevensreplicatie zal niet goed werken nadat het herstel is voltooid.

  -   U kunt het oorspronkelijke of een nieuw pad wilt gebruiken voor de installatie van de Configuration Manager in de Wizard Setup opgeven.

### <a name="to-start-an-unattended-site-recovery"></a>Het herstel van een site zonder toezicht starten
  1.    Bereid het script voor de installatie zonder toezicht voor voor de opties die u nodig hebt voor het siteherstel.  Zie [script site zonder toezicht-bestand herstelsleutels](/sccm/protect/understand/unattended-site-recovery-script-file-keys).

  2.    Setup van Configuration Manager uitvoeren met behulp van de opdracht **/script** optie. Bijvoorbeeld, als u uw installatie-initialisatiebestand ConfigMgrUnattend.ini met de naam en opgeslagen in de map C:\Temp van de computer waarop u Setup uitvoert, zou de opdracht zijn als volgt: **Setup/script C:\temp\ConfigMgrUnattend.ini**.

  > [!NOTE]   
  >  Nadat u een centrale beheersite hebt hersteld, is het mogelijk dat de replicatie van bepaalde sitegegevens die afkomstig zijn van onderliggende sites mislukt. Het kan hierbij gaan om de hardware-inventaris, software-inventaris en statusberichten.
  >
  >  Als dit het geval is, moet u **ConfigMgrDRSSiteQueue** opnieuw voor de databasereplicatie initialiseren.  Gebruiken om dit te doen **SQL Server Manager** de volgende query uitvoeren op de Configuration Manager sitedatabase op de centrale beheersite:
  >
  >  **IF EXISTS (SELECTEER \* IN sys.service_queues WAARBIJ name = 'ConfigMgrDRSSiteQueue' EN is_receive_enabled = 0)**
  >
  >  **ALTER QUEUE [dbo].[ConfigMgrDRSSiteQueue] WITH STATUS = ON**


## <a name="post-recovery-tasks"></a>Taken na herstel
Nadat u uw site hebt hersteld, zijn er verschillende taken na herstel die u moet overwegen voordat het herstel van uw site voltooid is. Gebruik de volgende secties voor hulp bij het voltooien van uw proces voor siteherstel.

### <a name="re-enter-user-account-passwords"></a>Wachtwoord voor gebruikersaccount opnieuw invoeren
Na een siteserverherstel moeten wachtwoorden voor de gebruikersaccounts die voor de site zijn opgegeven, opnieuw worden ingevoerd omdat ze tijdens het herstel van de site opnieuw zijn ingesteld. De accounts zijn opgenomen op de pagina **Voltooid** van de installatiewizard nadat het herstel van de site is voltooid is en is opgeslagen naar C:\ConfigMgrPostRecoveryActions.html op de herstelde siteserver.

#### <a name="to-re-enter-user-account-passwords-after-site-recovery"></a>Wachtwoorden van gebruikersaccounts opnieuw invoeren na het siteherstel

1.  Open de Configuration Manager-console en maak verbinding met de herstelde site.

2.  Klik op **Beheer**in de Configuration Manager-console.

3.  Vouw in de werkruimte **Beheer** de optie **Beveiliging**uit en klik vervolgens op **Accounts**.

4.  Voor elke account waarin u het wachtwoord opnieuw invoeren, doet u het volgende:

    1.  Selecteer de account uit de lijst van accounts die waren geïdentificeerd na siteherstel. U kunt deze lijst vinden in C:\ConfigMgrPostRecoveryActions.html op de herstelde siteserver.

    2.  Klik op **Eigenschappen** in het tabblad **Start** in de groep **Eigenschappen** om de accounteigenschappen te openen.

    3.  Klik in het tabblad **Algemeen** op **Instellen**en voer vervolgens opnieuw de wachtwoorden voor het account in.

    4.  Klik op **Controleren**, selecteer de geschikte gegevensbron voor het geselecteerde gebruikersaccount en klik vervolgens op **Verbinding testen** om te controleren of het gebruikersaccount een verbinding kan maken met de gegevensbron.

    5.  Klik op **OK** om de wachtwoordwijzigingen op te slaan en klik vervolgens op **OK**.

### <a name="re-enter-sideloading-keys"></a>Sideloading-codes opnieuw invoeren
Wanneer een siteserver is hersteld, moet u de Windows-sideloading-codes opnieuw invoeren die voor de site zijn opgegeven, omdat deze tijdens het herstellen van de site gereset zijn. Nadat u de sideloading-codes, het aantal in opnieuw invoeren de **gebruikte activeringen** kolom voor Windows-sideloading-codes gereset in de Configuration Manager-console. Bijvoorbeeld, stel vóór de sitefout die u hebt een **totaal activeringen** aantal ingesteld op **100** en **gebruikte activeringen** loopt **90** voor het aantal codes dat door apparaten zijn gebruikt. Na het herstel van de site wordt in de kolom **Totaal activeringen** nog steeds **100**weergegeven, maar wordt in de kolom **Gebruikte activeringen** ten onrechte **0**weergegeven. Nadat echter 10 nieuwe apparaten een sideloading-code hebben gebruikt, blijven er geen sideloading-codes meer over en het volgende apparaat kan geen sideloading-code toepassen.

### <a name="recreate-the-microsoft-intune-subscription"></a>Het Microsoft Intune-abonnement opnieuw maken
 Als u een Configuration Manager-siteserver herstelt nadat de site server-computer opnieuw installatiekopie gemaakt wordt, wordt de Microsoft Intune-abonnement niet hersteld. Nadat u een site herstelt, moet u uw abonnement opnieuw aansluiten.  Maak een nieuwe APN-aanvraag geen, maar in plaats daarvan de huidige geldig .pem-bestand dat is geüpload voor het laatst iOS-beheer is geconfigureerd of vernieuwd uploaden. Zie [Het Windows Intune-abonnement configureren](/sccm/mdm/deploy-use/configure-intune-subscription) voor meer informatie.

### <a name="configure-ssl-for-site-system-roles-that-use-iis"></a>SSL configureren voor sitesysteemrollen die gebruikmaken van IIS
Wanneer u sitesystemen met IIS herstelt die vóór de fout voor HTTPS zijn geconfigureerd, moet u IIS opnieuw configureren voor het gebruik van het webservercertificaat.

### <a name="reinstall-hotfixes-in-the-recovered-site-server"></a>Hotfixes opnieuw installeren op de herstelde siteserver
Wanneer een site is hersteld, moet u de op de siteserver toegepaste hotfixes opnieuw installeren. Bekijk de lijst met eerder geïnstalleerde hotfixes op de **voltooid** pagina van de Wizard Setup na het siteherstel. Deze lijst wordt ook opgeslagen in **C:\ConfigMgrPostRecoveryActions.html** op de herstelde siteserver.

### <a name="recover-custom-reports-on-the-computer-running-reporting-services"></a>Aangepaste rapporten herstellen op een computer met Reporting Services
Wanneer u aangepaste Reporting Services-rapporten hebt gemaakt en er een fout is opgetreden in Reporting Services, kunt u de rapporten herstellen wanneer u een back-up van de rapportserver hebt gemaakt. Zie [Backup and Restore Operations for a Reporting Services Installation](http://go.microsoft.com/fwlink/p/?LinkId=228724) (Back-up en herstelbewerkingen voor een Reporting Services-installatie) in SQL Server 2008 Books Online voor meer informatie over het herstellen van uw aangepaste rapporten in Reporting Services.

### <a name="recover-content-files"></a>Inhoudsbestanden herstellen
 De sitedatabase bevat informatie over de locatie waar de inhoudsbestanden op de siteserver zijn opgeslagen, maar er wordt geen back-up gemaakt van de inhoudsbestanden, noch worden deze hersteld als onderdeel van het back-up- en herstelproces. Als u inhoudsbestanden volledig wilt herstellen, moet u de inhoudsbibliotheek en pakketbronbestanden op de oorspronkelijke locatie herstellen. Er zijn verschillende methoden om uw inhoudsbestanden te herstellen, maar de eenvoudigste methode is dat u de bestanden vanuit een bestandssysteemback-up van de siteserver herstelt.

 Als u geen een bestandssysteemback-up van de pakketbronbestanden, moet u handmatig kopiëren of downloaden zoals u oorspronkelijk hebt gedaan toen u het pakket voor het eerst hebt gemaakt. U kunt de volgende query in SQL Server uitvoeren om de locatie van de pakketbron voor alle pakketten en toepassingen te vinden: `SELECT * FROM v_Package`. U kunt de locatie van de pakketbron vinden door de eerste drie tekens van de pakket-id te bekijken. Als de pakket-id bijvoorbeeld CEN00001 is, is de sitecode van de bronsite CEN. Wanneer u de pakketbronbestanden herstelt, moeten deze op dezelfde locatie worden hersteld waar deze zich vóór de fout bevonden.

 Als u beschikt over een bestandssysteemback-up waarin zich geen inhoudsbibliotheek bevindt, hebt u de volgende herstelopties:

-   **Een voorbereid inhoudsbestand importeren**: Wanneer u een Configuration Manager-hiërarchie hebt, kunt u een voorbereid inhoudsbestand maken met alle pakketten en toepassingen van een andere locatie en importeer het voorbereide inhoudsbestand te herstellen van de Inhoudsbibliotheek op de siteserver.

-   **Inhoud bijwerken**: Wanneer u de actie inhoud bijwerken voor een pakket of toepassing implementatietype start, wordt de inhoud van de pakketbron gekopieerd naar de Inhoudsbibliotheek. De pakketbronbestanden moeten beschikbaar zijn op de oorspronkelijke locatie om deze actie met succes te voltooien. U moet deze actie op elk pakket en elke toepassing uitvoeren.

### <a name="recover-custom-software-updates-on-the-computer-running-updates-publisher"></a>Aangepaste software-updates herstellen op een computer met Updates Publisher
Wanneer u Updates Publisher-databasebestanden in uw back-upschema hebt opgenomen, kunt u de databases bij een storing op de computer waarop Updates Publisher wordt uitgevoerd herstellen. Zie [System Center Updates Publisher 2011](http://go.microsoft.com/fwlink/p/?LinkId=228726) in de System Center TechCenter Library voor meer informatie over Updates Publisher.

Gebruik de volgende procedure om de Updates Publisher-database te herstellen.

#### <a name="to-restore-the-updates-publisher-2011-database"></a>De Updates Publisher 2011-database herstellen
1.  Installeer Updates Publisher op de herstelde computer.

2.  Kopieer het databasebestand (Scupdb.sdf) van uw back-upbestemming %*USERPROFILE*%\AppData\Local\Microsoft\System Center Updates Publisher 2011\5.00.1727.0000\ op de computer waarop Updates Publisher wordt uitgevoerd.

3.  Wanneer meer dan één gebruiker Updates Publisher op de computer wordt uitgevoerd, moet u elk databasebestand naar de locatie van de betreffende gebruikersprofiel kopiëren.

### <a name="user-state-migration-data"></a>Migratiegegevens van de gebruikersstatus
Als onderdeel van de sitesysteemeigenschappen van het statusmigratiepunt geeft u de mappen op waarop de migratiegegevens van de gebruikersstatus zijn opgeslagen. Wanneer u een server herstelt met een map waarop migratiegegevens van de gebruikersstatus zijn opgeslagen, moet u de migratiegegevens van de gebruikersstatus op de server handmatig herstellen in dezelfde mappen waarop de gegevens waren opgeslagen vóór de fout.

### <a name="regenerate-the-certificates-for-distribution-points"></a>De certificaten voor distributiepunten opnieuw genereren
Wanneer u een site hebt hersteld, bevat het bestand distmgr.log mogelijk de volgende vermelding voor een of meer distributiepunten: **Kan bepaalde PFX-gegevens te ontsleutelen**. Deze vermelding geeft aan dat de certificaatgegevens van het distributiepunt niet door de site kunnen worden ontsleuteld. U lost dit op, moet u opnieuw genereren of het certificaat voor de betrokken distributiepunten opnieuw te importeren. Dit kan worden gedaan met de PowerShell-cmdlet [Set-CMDistributionPoint](https://technet.microsoft.com/library/jj821872\(v=sc.20\).aspx).

### <a name="update-certificates-used-for-cloud-based-distribution-points"></a>Voor clouddistributiepunten gebruikte certificaten bijwerken
 Configuration Manager vereist een beheercertificaat dat wordt gebruikt voor de siteserver naar de cloud-gebaseerd distributiepunt communicatie. Wanneer een site is hersteld, moet u de certificaten van clouddistributiepunten bijwerken.

## <a name="recover-a-secondary-site"></a>Een secundaire site herstellen
 Configuration Manager biedt geen ondersteuning voor de back-up van de database op een secundaire site, maar wel ondersteuning voor herstel door de secundaire site opnieuw te installeren. Herstel van secundaire site is vereist wanneer een secundaire site van Configuration Manager is mislukt.

### <a name="requirements-for-reinstalling-a-secondary-site"></a>Vereisten voor een secundaire site opnieuw te installeren
-   De computer moet voldoen aan alle vereisten van secundaire site en juist beveiligingscertificaat hebben geconfigureerd.
-   U moet hetzelfde installatiepad dat is gebruikt voor de uitgevallen site.
-   U moet een computer gebruiken met dezelfde configuratie als de defecte computer, zoals de bijbehorende FQDN, om de secundaire site te kunnen herstellen.
-   De computer moet dezelfde SQL Server-configuratie als de mislukte site hebben.
  -   Tijdens het herstel van een secundaire site Configuration Manager heeft geen SQL Server Express installeren als deze nog niet is geïnstalleerd op de computer.
  -   U moet dezelfde versie van SQL Server en hetzelfde exemplaar van SQL Server gebruiken die/dat u voor de database van de secundaire site hebt gebruikt vóór de fout.

### <a name="to-recover-a-secondary-site"></a>Een secundaire site te herstellen:
Als u wilt herstellen op een secundaire site, gebruiken de **secundaire Site herstellen** actie van de **Sites** knooppunt in de Configuration Manager-console. In tegenstelling tot herstel voor een centraal beheer-site of de primaire site, wordt bij herstel voor een secundaire site geen back-upbestand gebruikt en worden in plaats daarvan de bestanden van de secundaire site opnieuw geïnstalleerd op de computer van de mislukte secundaire site. Nadat de site opnieuw geïnstalleerd, wordt de secundaire sitegegevens geherinitialiseerd met gegevens van de bovenliggende primaire site.

Configuration Manager wordt tijdens het herstelproces wordt gecontroleerd of de Inhoudsbibliotheek zich op de secundaire sitecomputer bevindt en dat de betreffende inhoud beschikbaar is. De secundaire site maakt gebruik van de bestaande inhoudsbibliotheek als deze de juiste inhoud bevat. Anders moet u voor het herstellen van de inhoudsbibliotheek van een herstelde secundaire site de inhoud opnieuw distribueren of vooraf plaatsen op de herstelde site.

Wanneer u een distributiepunt hebt dat zich niet op de secundaire site bevindt, hoeft u het distributiepunt tijdens het herstellen van de secundaire site niet opnieuw te installeren. Wanneer de secundaire site is hersteld, wordt de site automatisch gesynchroniseerd met het distributiepunt.

U kunt de status van het herstel van secundaire site controleren via de **installatiestatus tonen** actie van de **Sites** knooppunt in de Configuration Manager-console.

