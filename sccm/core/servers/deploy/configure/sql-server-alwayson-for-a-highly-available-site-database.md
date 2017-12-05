---
title: SQL Server Always On
titleSuffix: Configuration Manager
description: Plan het gebruik van een SQL Server altijd op beschikbaarheidsgroep met SCCM.
ms.custom: na
ms.date: 11/20/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: configmgr-other
ms.tgt_pltfrm: na
ms.topic: get-started-article
ms.assetid: 58d52fdc-bd18-494d-9f3b-ccfc13ea3d35
caps.latest.revision: "16"
author: mestew
ms.author: mstewart
manager: angrobe
ms.openlocfilehash: 42d5a059e11dffc7890ec78ce7361ebfe905a050
ms.sourcegitcommit: daa080cf220835f157a23e8c8e2bd2781b869bb7
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/04/2017
---
# <a name="prepare-to-use-sql-server-always-on-availability-groups-with-configuration-manager"></a>Voorbereiden op het gebruik van SQL Server Always On availability groups met Configuration Manager

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*

Bereid voor System Center Configuration Manager SQL Server AlwaysOn-beschikbaarheidsgroepen gebruiken als een hoge beschikbaarheid en noodherstel hersteloplossing voor de sitedatabase.  
Configuration Manager ondersteunt het gebruik van beschikbaarheidsgroepen:
-     Op primaire sites en de centrale beheersite.
-     On-premises of in Microsoft Azure.

Wanneer u beschikbaarheidsgroepen in Microsoft Azure gebruikt, kunt u de beschikbaarheid van uw sitedatabase verder verhogen met behulp van *Beschikbaarheidssets van Azure*. Zie voor meer informatie over beschikbaarheidssets van Azure [Manage the availability of virtual machines](https://azure.microsoft.com/documentation/articles/virtual-machines-windows-manage-availability/)(De beschikbaarheid van virtuele machines beheren).

>  [!Important]   
>  Voordat u doorgaat, worden bekendheid met het configureren van SQL Server en SQL Server-beschikbaarheidsgroepen. De informatie die volgt verwijst naar de Documentatiebibliotheek van SQL Server en -procedures.

## <a name="supported-scenarios"></a>Ondersteunde scenario's
Hier volgen de ondersteunde scenario's voor het gebruik van beschikbaarheidsgroepen met Configuration Manager. Meer informatie en procedures voor elk vindt u in [beschikbaarheidsgroepen configureren voor Configuration Manager](/sccm/core/servers/deploy/configure/configure-aoag).


-      [Maken van een beschikbaarheidsgroep voor gebruik met Configuration Manager](/sccm/core/servers/deploy/configure/configure-aoag#create-and-configure-an-availability-group).
-     [Configureren van een site voor het gebruik van een beschikbaarheidsgroep](/sccm/core/servers/deploy/configure/configure-aoag#configure-a-site-to-use-the-database-in-the-availability-group).
-     [Replicatieleden toevoegen of verwijderen synchrone van een beschikbaarheidsgroep die als host fungeert voor een sitedatabase](/sccm/core/servers/deploy/configure/configure-aoag#add-and-remove-synchronous-replica-members).
-     [Configureren van replica's voor asynchrone doorvoer](/sccm/core/servers/deploy/configure/configure-aoag#configure-an-asynchronous-commit-repilca) (vereist Configuration Manager versie 1706 of hoger.)
-     [Een site herstellen van een replica met asynchrone doorvoer](/sccm/core/servers/deploy/configure/configure-aoag#use-the-asynchronous-replica-to-recover-your-site) (vereist Configuration Manager versie 1706 of hoger.)
-     [Een sitedatabase buiten een beschikbaarheidsgroep verplaatsen naar een standaard of benoemd exemplaar van een zelfstandige SQL Server](/sccm/core/servers/deploy/configure/configure-aoag#stop-using-an-availability-group).


## <a name="prerequisites"></a>Vereisten
De volgende vereisten gelden voor alle scenario's. Aanvullende vereisten van toepassing op een specifiek scenario, wordt de gedetailleerde met dit scenario.   

### <a name="configuration-manager-accounts-and-permissions"></a>Configuration Manager-accounts en machtigingen
**De siteserver naar de Ledentoegang replica:**   
Het computeraccount van de siteserver moet lid zijn van de groep **Lokale beheerders** op elke computer die lid is van de beschikbaarheidsgroep.

### <a name="sql-server"></a>SQL Server
**Versie:**  
Elke replica in de beschikbaarheidsgroep moet een versie van SQL Server die wordt ondersteund door uw versie van Configuration Manager uitvoeren. Wanneer dit wordt ondersteund door SQL Server, kunnen verschillende knooppunten van een beschikbaarheidsgroep verschillende versies van SQL Server kunnen uitvoeren.

**Editie:**  
Moet u een *Enterprise* editie van SQL Server.

**Account:**  
Elk exemplaar van SQL Server kunt uitvoeren onder een domeinaccount van de gebruiker (**-serviceaccount**) of een niet-domeinaccount. Elke replica in een groep kan een andere configuratie hebben. Per [aanbevolen procedures voor SQL Server](/sql/sql-server/install/security-considerations-for-a-sql-server-installation#before-installing-includessnoversionincludesssnoversion-mdmd), gebruik een account met de laagst mogelijke machtigingen.

-   Voor het configureren van de Service-Accounts en machtigingen voor SQL Server 2016 Zie [Windows-Accounts configureren en machtigingen](/sql/database-engine/configure-windows/configure-windows-service-accounts-and-permissions) op MSDN.
-   U moet certificaten gebruiken voor het gebruik van een niet-domeinaccount. Zie voor meer informatie [gebruikmaken van certificaten voor een Database Mirroring-eindpunt (Transact-SQL)](https://docs.microsoft.com/sql/database-engine/database-mirroring/use-certificates-for-a-database-mirroring-endpoint-transact-sql).


Zie voor meer informatie [maken van een Database Mirroring-eindpunt voor altijd op beschikbaarheidsgroepen](/sql/database-engine/availability-groups/windows/database-mirroring-always-on-availability-groups-powershell).

### <a name="availability-group-configurations"></a>Configuraties van beschikbaarheid
**Replicatieleden:**  
-   De beschikbaarheidsgroep moet één primaire replica hebben.
-   U kunt maximaal twee synchrone secundaire replica's hebben voorafgaand aan versie 1706.
-   Vanaf versie 1706, kunt u hetzelfde aantal en type van replica's in een beschikbaarheidsgroep als ondersteund door de versie van SQL Server die u gebruikt.

-   Vanaf versie 1706, kunt u een replica met asynchrone doorvoer voor het herstellen van de synchrone replica. Zie [opties voor herstel van site]( /sccm/protect/understand/backup-and-recovery#BKMK_SiteDatabaseRecoveryOption) in het onderwerp back-up en herstel voor meer informatie over om dit te bereiken.
    > [!CAUTION]  
    > Configuration Manager biedt geen ondersteuning voor failover voor het gebruik van de replica met asynchrone doorvoer als uw sitedatabase.
Omdat Configuration Manager wordt de status van de replica met asynchrone doorvoer om te bevestigen dat het huidige, is niet gevalideerd en [standaard deze replica kan niet synchroon]( https://msdn.microsoft.com/library/ff877884(SQL.120).aspx(d=robot)#Availability%20Modes), het gebruik van een replica met asynchrone doorvoer als de sitedatabase kunt risico voor de integriteit van uw site en -gegevens.

Elk replicalid van de moet:
-   Het **standaardexemplaar**gebruiken.  
    *Vanaf versie 1702, kunt u een* ***benoemd exemplaar***.

-     Hebben **verbindingen in de primaire rol** ingesteld op **Ja**
-     Hebben **leesbare secundaire** ingesteld op **Ja**  
-     Worden ingesteld op **handmatige failover**.      

    >  [!TIP]
    >  Configuration Manager ondersteunt het gebruik van de beschikbaarheid van de groep synchrone replica's als de waarde **automatische Failover**. Echter, **handmatige Failover** moet worden ingesteld als:
    >  -  U uitvoeren Setup voor het gebruik van de sitedatabase opgeeft in de beschikbaarheidsgroep.
    >  -  Wanneer u een update installeert voor Configuration Manager (niet alleen updates die van toepassing op de sitedatabase).  

**Locatie van de replica-lid:**  
Alle replica's in een beschikbaarheidsgroep moeten gehoste lokaal of gehost op Microsoft Azure. Een groep die een lid van de lokale en lid in Azure bevat wordt niet ondersteund.     

Wanneer u een beschikbaarheidsgroep in Azure instellen en de groep zich achter een interne of externe load balancer, zijn de volgende standaardpoorten, moet u ook openen voor Setup toegang tot elke replica:   

-     RCP eindpunttoewijzer - **TCP-poort 135**   
-     Server Message Block – **TCP 445**  
    *Nadat de verplaatsing van de database is voltooid, kunt u deze poort verwijderen. Vanaf versie 1702, het deze poort is niet langer vereist.*
-     SQL Server Service Broker - **TCP 4022**
-     SQL via TCP – **TCP 1433**   

Nadat Setup is voltooid, moeten de volgende poorten toegankelijk blijven:
-     SQL Server Service Broker - **TCP 4022**
-     SQL via TCP – **TCP 1433**

Vanaf versie 1702, kunt u aangepaste poorten voor deze configuraties. Dezelfde poorten moeten worden gebruikt door het eindpunt en op alle replica's in de beschikbaarheidsgroep.


**Listener:**   
De beschikbaarheidsgroep moet ten minste één **beschikbaarheidsgroeplistener**hebben. De virtuele naam van deze listener wordt gebruikt bij het configureren van Configuration Manager voor het gebruik van de sitedatabase in de beschikbaarheidsgroep. Hoewel een beschikbaarheidsgroep meerdere listeners bevatten kan, kunt alleen Configuration Manager maken gebruik van een. Zie [maken of configureren van een beschikbaarheidsgroep-Listener (SQL Server)](/sql/database-engine/availability-groups/windows/create-or-configure-an-availability-group-listener-sql-server) voor meer informatie.

**Bestandspaden:**   
Wanneer u Configuration Manager Setup uitvoeren om te configureren van een site voor het gebruik van de database in een beschikbaarheidsgroep, elke secundaire replica-server moet een SQL Server-bestandspad die identiek is aan het pad voor de sitedatabasebestanden als gevonden op de huidige primaire replica.
-   Als een identiek pad niet bestaat, wordt het exemplaar voor de beschikbaarheidsgroep toevoegen als de nieuwe locatie van de sitedatabase installatie mislukken.
-   Het lokale SQL Server-serviceaccount moet bovendien hebben **volledig beheer** machtiging voor deze map.

Op de secundaire replicaservers is dit bestandspad alleen vereist op het moment dat u Setup gebruikt om het database-exemplaar in de beschikbaarheidsgroep op te geven. Nadat Setup is voltooid de configuratie van de sitedatabase in de beschikbaarheidsgroep, kunt u het ongebruikte pad verwijderen van secundaire replicaservers.

Denk bijvoorbeeld eens aan het volgende scenario:
-   U maakt een beschikbaarheidsgroep die drie SQL-Servers gebruikt.

-   Uw primaire replicaserver is een nieuwe installatie van SQL Server 2014. Standaard wordt de database. MDF en. LDF-bestanden worden opgeslagen in C:\Program Files\Microsoft SQL Server\MSSQL12. MSSQLSERVER\MSSQL\DATA.

-   Beide van de secundaire replica-servers zijn bijgewerkt naar SQL Server 2014 van vorige versies en het oorspronkelijke bestandspad voor het opslaan van bestanden van de database behouden: C:\Program Files\Microsoft SQL Server\MSSQL10. MSSQLSERVER\MSSQL\DATA.

-   Voordat u de sitedatabase verplaatsen naar deze beschikbaarheidsgroep, op elke secundaire replica-server moet u het volgende pad zelfs als de secundaire replica's maakt geen gebruik van deze locatie: C:\Program Files\Microsoft SQL Server\MSSQL12. MSSQLSERVER\MSSQL\DATA (dit is een duplicaat van het pad dat wordt gebruikt op de primaire replica).

-   U verleent vervolgens het SQL Server-serviceaccount op elke secundaire replica volledige beheertoegang krijgen tot de locatie van het zojuist gemaakte bestand op die server.

-   U kunt nu de installatie van Configuration Manager voor het configureren van de site voor het gebruik van de sitedatabase in de beschikbaarheidsgroep is uitvoeren.

**Configureer de database op een nieuwe replica:**   
 De database van elke replica moet worden ingesteld met de volgende opties:
-   **CLR-integratie** moet *ingeschakeld*
-     **Max text repl grootte** moet *2147483647*
-     De database-eigenaar moet de *SA-account*
-     **TRUSTWORTY** moet **ON**
-     **Service Broker** moet *ingeschakeld*

U kunt deze configuraties op alleen primaire replica. Voor het configureren van een secundaire replica, moet u de eerste failover van de primaire naar de secundaire om te maken van de secundaire waardoor de secundaire de nieuwe primaire replica.   

Gebruik SQL Server-documentatie om u te helpen u de instellingen configureren. Zie bijvoorbeeld [TRUSTWORTHY](/sql/relational-databases/security/trustworthy-database-property) of [CLR-integratie](/sql/relational-databases/clr-integration/clr-integration-enabling) in de documentatie van SQL Server.

### <a name="verification-script"></a>Verificatie-script
U kunt het volgende script om te controleren of de databaseconfiguraties voor primaire en secundaire replica's kunt uitvoeren. Voordat u een probleem op een secundaire replica oplossen kunt, moet u die secundaire replica als de primaire replica.

    SET NOCOUNT ON

    DECLARE @dbname NVARCHAR(128)

    SELECT @dbname = sd.name FROM sys.sysdatabases sd WHERE sd.dbid = DB_ID()

    IF (@dbname = N'master' OR @dbname = N'model' OR @dbname = N'msdb' OR @dbname = N'tempdb' OR @dbname = N'distribution' ) BEGIN
    RAISERROR(N'ERROR: Script is targetting a system database.  It should be targeting the DB you created instead.', 0, 1)
    GOTO Branch_Exit;
    END ELSE
    PRINT N'INFO: Targetted database is ' + @dbname + N'.'

    PRINT N'INFO: Running verifications....'

    IF NOT EXISTS (SELECT * FROM sys.configurations c WHERE c.name = 'clr enabled' AND c.value_in_use = 1)
    PRINT N'ERROR: CLR is not enabled!'
    ELSE
    PRINT N'PASS: CLR is enabled.'

    DECLARE @repltable TABLE (
    name nvarchar(max),
    minimum int,
    maximum int,
    config_value int,
    run_value int )

    INSERT INTO @repltable
    EXEC sp_configure 'max text repl size (B)'

    IF NOT EXISTS(SELECT * from @repltable where config_value = 2147483647 and run_value = 2147483647 )
    PRINT N'ERROR: Max text repl size is not correct!'
    ELSE
    PRINT N'PASS: Max text repl size is correct.'

    IF NOT EXISTS (SELECT db.owner_sid FROM sys.databases db WHERE db.database_id = DB_ID() AND db.owner_sid = 0x01)
    PRINT N'ERROR: Database owner is not sa account!'
    ELSE
    PRINT N'PASS: Database owner is sa account.'

    IF NOT EXISTS( SELECT * FROM sys.databases db WHERE db.database_id = DB_ID() AND db.is_trustworthy_on = 1 )
    PRINT N'ERROR: Trustworthy bit is not on!'
    ELSE
    PRINT N'PASS: Trustworthy bit is on.'

    IF NOT EXISTS( SELECT * FROM sys.databases db WHERE db.database_id = DB_ID() AND db.is_broker_enabled = 1 )
    PRINT N'ERROR: Service broker is not enabled!'
    ELSE
    PRINT N'PASS: Service broker is enabled.'

    IF NOT EXISTS( SELECT * FROM sys.databases db WHERE db.database_id = DB_ID() AND db.is_honor_broker_priority_on = 1 )
    PRINT N'ERROR: Service broker priority is not set!'
    ELSE
    PRINT N'PASS: Service broker priority is set.'

    PRINT N'Done!'

    Branch_Exit:

## <a name="limitations-and-known-issues"></a>Bekende problemen en beperkingen
De volgende beperkingen zijn van toepassing op alle scenario's.   

**SQL Server-opties en configuraties die niet worden ondersteund:**
- **Basic-beschikbaarheidsgroepen**  
  Geïntroduceerd in SQL Server 2016 Standard edition [basic beschikbaarheidsgroepen](https://msdn.microsoft.com/library/mt614935.aspx) bieden geen ondersteuning voor leestoegang tot secundaire replica's is een vereiste voor gebruik met Configuration Manager.
- **Failover Cluster exemplaar**  
  [Failover Cluster Instances](/sql/sql-server/failover-clusters/windows/always-on-failover-cluster-instances-sql-server) worden niet ondersteund voor een replica die u met Configuration Manager gebruikt.

- **MultiSubnetFailover**    
    Het wordt niet ondersteund voor het gebruik van een beschikbaarheidsgroep in een configuratie met meerdere subnetten of met de [MutliSubnetFailover](/sql/database-engine/availability-groups/windows/create-or-configure-an-availability-group-listener-sql-server#MultiSubnetFailover) sleutelwoord verbindingsreeks.



**SQL-servers die als host aanvullende beschikbaarheidsgroepen fungeren:**   
Voorafgaand aan de Configuration Manager versie 1610, wanneer een beschikbaarheidsgroep op een SQL Server-hosts een of meer beschikbaarheidsgroepen naast de groep die u voor Configuration Manager, elke replica in elk van deze groepen extra beschikbaarheid gebruikt moeten hebben de volgende configuraties die zijn ingesteld op het moment dat u Configuration Manager Setup uitvoert of een update installeert voor Configuration Manager:
-   **handmatige failover**
-   **elke alleen-lezen verbinding toe te staan**

**Gebruik van de database niet ondersteund:**
-   **Configuration Manager ondersteunt alleen de database van de site in een beschikbaarheidsgroep:** Het volgende worden niet ondersteund:
    -   Rapportagedatabase
    -   WSUS-database
-   **Bestaande database:** U kunt nieuwe database gemaakt op de replica niet gebruiken. In plaats daarvan moet u een kopie van een bestaande Configuration Manager-database herstellen naar de primaire replica bij het configureren van een beschikbaarheidsgroep.

**Installatiefouten in ConfigMgrSetup.log:**  
Wanneer u Setup een sitedatabase verplaatsen naar een beschikbaarheidsgroep uitvoert, kan Setup probeert databaserollen op de secundaire replica's van de beschikbaarheidsgroep te verwerken en registreert fouten als volgt:
-   FOUT: SQL Server-fout: [25000] [3906] [Microsoft] [SQL Server Native Client 11.0] [SQL Server] is mislukt voor het bijwerken van database 'CM_AAA', omdat de database alleen-lezen is. Configuration Manager Setup 21/1/2016 4:54:59 PM 7344 (0x1CB0)  

Deze fouten kunnen veilig worden genegeerd.

## <a name="changes-for-site-backup"></a>Wijzigingen voor back-up van site
**Back-updatabase bestanden:**  
Wanneer een sitedatabase wordt uitgevoerd in een beschikbaarheidsgroep, moet u de ingebouwde **back-up siteserver** onderhoudstaak back-up maken van algemene Configuration Manager-instellingen en bestanden. Echter niet gebruiken de. MDF of. LDF-bestanden die door deze back-up gemaakt. Zorg in plaats daarvan direct back-ups van deze databasebestanden met behulp van SQL Server.

**Transactielogboek:**  
Het herstelmodel van de sitedatabase moet worden ingesteld op **volledige** (een vereiste voor gebruik in een beschikbaarheidsgroep). Met deze configuratie van plan bent te bewaken en onderhouden van de grootte van het transactielogboek van sitedatabase. In het volledige herstelmodel worden de transacties niet gehard totdat een volledige back-up van de database of het transactielogboek wordt gemaakt. Zie [Back-Up en herstellen van SQL Server-Databases](/sql/relational-databases/backup-restore/back-up-and-restore-of-sql-server-databases) in de SQL Server-documentatie voor meer informatie.

## <a name="changes-for-site-recovery"></a>Wijzigingen voor site recovery
U kunt de optie voor siteherstel **databaseherstel overslaan (deze optie als de sitedatabase onbeschadigd gebruiken)** als ten minste één knooppunt van de beschikbaarheidsgroep werken blijft.

 Voordat u de site herstellen kunt als alle knooppunten van een beschikbaarheidsgroep verloren gegaan zijn, moet u de beschikbaarheidsgroep opnieuw maken. Configuration Manager kan niet opnieuw samenstellen of herstellen van het beschikbaarheidsknooppunt. Nadat de groep wordt opnieuw gemaakt, en een back-up hersteld en opnieuw geconfigureerd, kunt u vervolgens de optie voor siteherstel gebruiken **databaseherstel overslaan (deze optie als de sitedatabase onbeschadigd gebruiken)**.

Zie voor meer informatie [back-up en herstel voor System Center Configuration Manager](/sccm/protect/understand/backup-and-recovery).

## <a name="changes-for-reporting"></a>Wijzigingen voor rapportage
**Het reporting servicepunt installeren:**  
Reporting services-punt biedt geen ondersteuning met behulp van de virtuele naam van de listener van de beschikbaarheidsgroep of het hosten van de reporting services-database in een SQL Server Always On-beschikbaarheidsgroep:
-   Standaard het reporting services-punt installatie stelt de **naam Sitedatabaseserver** in de virtuele naam die is opgegeven als de listener. Dit om op te geven van een computernaam en het exemplaar van een replica in de beschikbaarheidsgroep wijzigen.
-   Voor de offload van de reporting belasting en beschikbaarheid verbeteren wanneer een replica-knooppunt offline is, Overweeg de installatie van aanvullende reporting services-punten op elk knooppunt van de replica- en configuratie van elke reporting services Point-to-Point aan zijn eigen computernaam.

Wanneer u een reporting servicepunt op elke replica van de beschikbaarheidsgroep installeert, reporting kunt altijd verbinding maken met een actieve reporting point-server.

**De reporting services-punt gebruikt door de console switch:**  
Als u wilt uitvoeren van rapporten in de console gaat u naar **bewaking** > **overzicht** > **reporting** > **rapporten**, en kies vervolgens **Rapportopties**. Selecteer de gewenste reporting services-punt in het dialoogvenster Opties.

## <a name="next-steps"></a>Volgende stappen
Nadat u weet de vereisten wat, beperkingen en wijzigingen aan algemene taken die vereist zijn voor het gebruik van beschikbaarheidsgroepen, Zie [beschikbaarheidsgroepen configureren voor Configuration Manager](/sccm/core/servers/deploy/configure/configure-aoag), voor procedures voor het instellen en configureren van uw site voor het gebruik van beschikbaarheidsgroepen.
