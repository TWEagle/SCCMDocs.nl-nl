---
title: Ondersteunde versies van SQL Server
titleSuffix: Configuration Manager
description: Ophalen van SQL Server-versie en configuratie van vereisten voor het hosten van een System Center Configuration Manager-sitedatabase.
ms.custom: na
ms.date: 10/10/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 35e237b6-9f7b-4189-90e7-8eca92ae7d3d
caps.latest.revision: "21"
author: Brenduns
ms.author: brenduns
manager: angrobe
ms.openlocfilehash: 740a37478b4159fb9dcbfd9eaceeeaa307edd745
ms.sourcegitcommit: c236214b2fcc13dae7bad96d7fb33f692868191d
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/12/2017
---
# <a name="supported-sql-server-versions-for-system-center-configuration-manager"></a>Ondersteunde versies van SQL Server voor System Center Configuration Manager

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*

Elke System Center Configuration Manager-site is vereist voor een ondersteunde versie van SQL Server en -configuratie om de sitedatabase te hosten.  

##  <a name="bkmk_Instances"></a> SQL Server-exemplaren en -locaties  
 **Centrale beheersite en primaire sites:**  
De sitedatabase moet een volledige installatie van SQL Server gebruiken.  

 SQL Server kan zich bevinden op:  

-   De siteservercomputer.  
-   Een computer die extern zijn van de siteserver.  

De volgende exemplaren worden ondersteund:  

-   De standaard of benoemd exemplaar van SQL Server.  
-   Configuraties met meerdere exemplaren.  
-   Een SQL Server-cluster. Zie [SQL Server-cluster gebruiken voor het hosten van de sitedatabase](../../../core/servers/deploy/configure/use-a-sql-server-cluster-for-the-site-database.md).
-   Een SQL Server AlwaysOn-beschikbaarheidsgroep. Deze optie is Configuration Manager versie 1602 of hoger vereist. Zie voor meer informatie [SQL Server AlwaysOn voor een maximaal beschikbare sitedatabase voor System Center Configuration Manager](../../../core/servers/deploy/configure/sql-server-alwayson-for-a-highly-available-site-database.md).


 **Secundaire sites:**  
 De sitedatabase kan het standaardexemplaar van een volledige installatie van SQL Server of SQL Server Express gebruiken.  

 SQL Server moet zich bevinden op de siteservercomputer.  

 **Beperkingen voor de ondersteuning van**   
 De volgende configuraties worden niet ondersteund:
 -   Een SQL Server-cluster in een clusterconfiguratie Network Load Balancing (NLB)
 -   Een SQL Server-cluster op een Cluster Shared Volume (CSV)
 -   SQL Server databasespiegeling en peer-to-peer-replicatie,

SQL Server transactionele replicatie wordt alleen ondersteund voor het repliceren van objecten naar beheerpunten die zijn geconfigureerd voor gebruik [databasereplica](https://technet.microsoft.com/library/mt608546.aspx).  

##  <a name="bkmk_SQLVersions"></a> Ondersteunde versies van SQL Server  
 In een hiërarchie met meerdere sites kunnen verschillende sites verschillende versies van SQL Server gebruiken voor het hosten van de sitedatabase, zolang de volgende voorwaarden voldaan wordt:
 -  Configuration Manager ondersteunt de versies van SQL Server die u gebruikt.
 -  De SQL Server-versies die u gebruikt, blijven worden ondersteund door Microsoft.
 -  SQL Server biedt ondersteuning voor replicatie tussen de twee versies van SQL Server.  Bijvoorbeeld: [SQL Server biedt geen ondersteuning voor replicatie tussen SQL Server 2008 R2 en SQL Server 2016](https://docs.microsoft.com/sql/relational-databases/replication/deprecated-features-in-sql-server-replication).



 Tenzij anders vermeld, worden de volgende versies van SQL Server worden ondersteund met alle actieve versies van System Center Configuration Manager. Als ondersteuning voor een nieuwe SQL Server-versie of servicepack wordt toegevoegd, wordt de Configuration Manager-versie die wordt toegevoegd die ondersteuning bieden voor worden opgemerkt. Op dezelfde manier als ondersteuning is afgeschaft, zoek voor meer informatie over de desbetreffende versies van Configuration Manager.   

Ondersteuning voor een specifieke SQL Server-servicepack bevat cumulatieve updates naar die servicepack, tenzij een cumulatieve update de achterwaartse die basisservice pack-versie. Wanneer er geen versie van het servicepack is vermeld, is de ondersteuning voor die versie van SQL Server zonder service Pack. In de toekomst, als een servicepack voor die versie wordt uitgebracht, wordt een afzonderlijke ondersteuningsverklaring worden gedeclareerd voordat deze nieuwe versie van servicepack wordt ondersteund.


> [!IMPORTANT]  
>  Wanneer u SQL Server Standard voor de database op de centrale beheersite gebruikt, beperkt u het totale aantal clients dat een hiërarchie kan ondersteunen. Zie [Grootte en schaalgetallen](../../../core/plan-design/configs/size-and-scale-numbers.md).

### <a name="sql-server-2016-sp1-standard-enterprise"></a>SQL Server 2016 SP1: Standard, Enterprise  
U kunt deze versie van SQL Server zonder minimale cumulatieve updateversie gebruiken voor het volgende:  

-   Een centrale beheersite  
-   Een primaire site  
-   Een secundaire site  

### <a name="sql-server-2016-standard-enterprise"></a>SQL Server 2016: Standard, Enterprise  
U kunt deze versie van SQL Server zonder minimale cumulatieve updateversie gebruiken voor het volgende:  

-   Een centrale beheersite  
-   Een primaire site  
-   Een secundaire site  


### <a name="sql-server-2014-sp2-standard-enterprise"></a>SQL Server 2014 SP2: Standard, Enterprise  
U kunt deze versie van SQL Server zonder minimale cumulatieve updateversie gebruiken voor het volgende:  

-   Een centrale beheersite  
-   Een primaire site  
-   Een secundaire site



### <a name="sql-server-2014-sp1-standard-enterprise"></a>SQL Server 2014 SP1: Standard, Enterprise  
 U kunt deze versie van SQL Server zonder minimale cumulatieve updateversie gebruiken voor het volgende:  

-   Een centrale beheersite  
-   Een primaire site  
-   Een secundaire site

### <a name="sql-server-2012-sp4-standard-enterprise"></a>SQL Server 2012 SP4: Standard, Enterprise  
 U kunt deze versie van SQL Server zonder minimale cumulatieve updateversie gebruiken voor het volgende:  

-   Een centrale beheersite  
-   Een primaire site  
-   Een secundaire site  

### <a name="sql-server-2012-sp3-standard-enterprise"></a>SQL Server 2012 SP3: Standard, Enterprise  
 U kunt deze versie van SQL Server zonder minimale cumulatieve updateversie gebruiken voor het volgende:  

-   Een centrale beheersite  
-   Een primaire site  
-   Een secundaire site  

<!-- Support for this service pack version has been dropped by Microsoft    
### SQL Server 2012 SP2: Standard, Enterprise   
 You can use this version of SQL Server with no minimum cumulative update version for the following:  

-   A central administration site  
-   A primary site  
-   A secondary site  
-->

### <a name="sql-server-2008-r2-sp3-standard-enterprise-datacenter"></a>SQL Server 2008 R2 SP3: Standard, Enterprise, Datacenter     
  Deze versie van SQL Server wordt niet ondersteund [vanaf versie 1702](/sccm/core/plan-design/changes/removed-and-deprecated-features#deprecated-support-for-sql-server-versions-as-a-site-database).  
 Deze versie van SQL Server blijft ondersteund wanneer u een eerdere versie van Configuration Manager dan 1702 gebruikt.

Wanneer dit wordt ondersteund door uw versie van Configuration Manager, kunt u deze versie van SQL Server zonder minimale cumulatieve updateversie gebruiken voor het volgende:  

-   Een centrale beheersite  
-   Een primaire site
-   Een secundaire site



### <a name="sql-server-2016-express-sp1"></a>SQL Server 2016 snelle SP1  
U kunt deze versie van SQL Server zonder minimale cumulatieve updateversie gebruiken voor het volgende:
-   Een secundaire site

### <a name="sql-server-2016-express"></a>SQL Server 2016 Express
U kunt deze versie van SQL Server zonder minimale cumulatieve updateversie gebruiken voor het volgende:
-   Een secundaire site


### <a name="sql-server-2014-express-sp2"></a>SQL Server 2014 snelle SP2   
U kunt deze versie van SQL Server zonder minimale cumulatieve updateversie gebruiken voor het volgende:  

-   Een secundaire site  


### <a name="sql-server-2014-express-sp1"></a>SQL Server 2014 Express SP1   
 U kunt deze versie van SQL Server zonder minimale cumulatieve updateversie gebruiken voor het volgende:  

-   Een secundaire site  

### <a name="sql-server-2012-express-sp3"></a>SQL Server 2012 Express SP3  
U kunt deze versie van SQL Server zonder minimale cumulatieve updateversie gebruiken voor het volgende:  

-   Een secundaire site  

<!-- Support for this service pack version has been dropped by Microsoft   
### SQL Server 2012 Express SP2   
 You can use this version of SQL Server with no minimum cumulative update version for the following:  

-   A secondary site  
-->


##  <a name="bkmk_SQLConfig"></a> Vereiste configuraties voor SQL Server  
 Het volgende is vereist voor alle installaties van SQL Server die u voor een sitedatabase gebruikt (inclusief SQL Server Express). Wanneer Configuration Manager SQL Server Express als onderdeel van een secundaire site-installatie installeert, worden deze configuraties automatisch voor u gemaakt.  

 **Versie van SQL Server-architectuur:**  
 Configuration Manager vereist een 64-bits versie van SQL Server om de sitedatabase te hosten.  

 **Databasesortering:**  
 Het exemplaar van SQL Server die wordt gebruikt voor de site en de sitedatabase moet de volgende sortering gebruiken op elke site: **SQL_Latin1_General_CP1_CI_AS**.  

 Configuration Manager ondersteunt twee uitzonderingen op deze sortering om te voldoen aan de normen die zijn gedefinieerd in GB18030 voor gebruik in China. Voor meer informatie, zie [Internationale ondersteuning in System Center Configuration Manager](../../../core/plan-design/hierarchy/international-support.md).  

 **SQL Server-functies:**  
 Alleen het onderdeel **Database-engineservices** is vereist voor elke siteserver.  

 Configuration Manager-databasereplicatie vereist de **SQL Server-replicatie** functie. Deze SQL Server-configuratie is echter vereist als u [Databasereplica's voor beheerpunten voor System Center Configuration Manager](../../../core/servers/deploy/configure/database-replicas-for-management-points.md).  

 **Windows-verificatie:**  
 Configuration Manager vereist **Windows-verificatie** valideren van verbindingen met de database.  

 **SQL Server-exemplaar:**  
 U moet een exclusief exemplaar van SQL Server gebruiken voor elke site. Dit kan een **benoemd exemplaar** of het **standaardexemplaar**zijn.  

 **SQL Server-geheugen:**  
 Reserveer geheugen voor SQL Server met behulp van SQL Server Management Studio en instelling van de **Minimum servergeheugen** onder **Servergeheugenopties**. Zie voor meer informatie over het instellen van een vaste hoeveelheid geheugen [hoe: Instellen van een vaste hoeveelheid geheugen (SQL Server Management Studio)](http://go.microsoft.com/fwlink/p/?LinkId=233759).  

-   **Voor een databaseserver die is geïnstalleerd op dezelfde computer als de siteserver:** Beperk het geheugen voor SQL Server tot 50 à 80 procent van het beschikbare systeemgeheugen.  

-   **Voor een toegewezen databaseserver (extern van de siteserver):** Beperk het geheugen voor SQL Server tot 80 à 90 procent van het beschikbare systeemgeheugen.  

-   **Voor een geheugenreservering op voor de buffergroep van elk SQL Server-exemplaar gebruikt:**  

    -   Voor een centrale beheersite: Stel een minimum van 8 gigabyte (GB).  
    -   Voor een primaire site: Stel een minimum van 8 gigabyte (GB).  
    -   Voor een secundaire site: Stel een minimum van 4 gigabyte (GB).  

**Geneste SQL-triggers:**  
 [Genest SQL-triggers](http://go.microsoft.com/fwlink/?LinkId=528802) moet zijn ingeschakeld.  

 **SQL Server CLR-integratie**  
  SQL Server Common Language Runtime (CLR) moet zijn ingeschakeld voor de sitedatabase. Dit wordt automatisch ingeschakeld wanneer Configuration Manager wordt geïnstalleerd. Zie voor meer informatie over CLR [Inleiding tot SQL Server CLR-integratie](https://msdn.microsoft.com/library/ms254498\(v=vs.110\).aspx).  

##  <a name="bkmk_optional"></a> Optionele configuraties voor SQL Server  
 De volgende configuraties zijn optioneel voor elke database die een volledige installatie van SQL Server gebruikt.  

 **SQL Server-service:**  
 U kunt de SQL Server-service zo configureren dat deze wordt uitgevoerd met:  

-   Een *domeingebruiker van laag niveau aan rechten* account:  

    -   Dit is een best practice en mogelijk moet u de service principal name (SPN) voor het account handmatig registreren.  

-   De **lokaal systeem** account van de computer waarop SQL Server wordt uitgevoerd:  

    -   Gebruik het account voor het lokale systeem om het configuratieproces te vereenvoudigen.  
    -   Wanneer u het lokale systeemaccount gebruikt, wordt in Configuration Manager automatisch de SPN voor de SQL Server-service geregistreerd.  
    -   Houd er wel rekening mee dat u het lokale systeemaccount in SQL Server beter niet kunt gebruiken voor de SQL Server-service.  

Wanneer de computer met SQL Server niet de lokale systeemaccount gebruikt de SQL Server-service uit te voeren, moet u de SPN-naam van het account dat de SQL Server-service wordt uitgevoerd in Active Directory Domain Services configureren. (Wanneer het systeem-account wordt gebruikt, de SPN-naam wordt automatisch voor u geregistreerd.)

Zie voor meer informatie over de SPN's voor de sitedatabase [beheren van de SPN voor de Sitedatabaseserver](../../../core/servers/manage/modify-your-infrastructure.md#bkmk_SPN) in de [uw infrastructuur van System Center Configuration Manager aanpassen](../../../core/servers/manage/modify-your-infrastructure.md) onderwerp.  

Zie voor meer informatie over het wijzigen van het account dat wordt gebruikt door de SQL Server-service [hoe: Het starten van de serviceaccount voor SQL Server (SQL Server Configuration Manager) wijzigen](http://go.microsoft.com/fwlink/p/?LinkId=237661).  

**SQL Server Reporting Services:**  
SQL Server Reporting Services is vereist voor het installeren van een reporting services-punt waarmee u rapporten uitvoeren.  

> [!IMPORTANT]  
> Nadat u SQL Server een van een eerdere versie upgrade, ziet u mogelijk de volgende fout:  *Report Builder bestaat niet*.    
> U lost deze fout, moet u de reporting services-punt-sitesysteemrol installeren.

**SQL Server-poorten:**  
Voor communicatie met de SQL Server database engine en voor intersitereplicatie kunt u de standaardconfiguratie van de SQL Server-poort gebruiken of aangepaste poorten opgeven:  

-   **Intersite-communicatie** SQL Server Service Broker dat via TCP-4022 standaard poort gebruiken.  
-   **Intrasite-communicatie** tussen de SQL Server database engine en verschillende Configuration Manager-sitesysteem functies gebruiken standaard poort TCP 1433. De volgende sitesysteemrollen communiceren direct met de SQL Server database:  

    -   Beheerpunt  
    -   Computer van de SMS-provider  
    -   Reporting Services-punt  
    -   Siteserver  

Wanneer een computer met SQL Server als host fungeert voor een database van meer dan één site, moet elke database een afzonderlijk exemplaar van SQL Server gebruiken. Elk exemplaar moet ook worden geconfigureerd voor het gebruik van een unieke set van poorten.  

> [!WARNING]  
>  Configuration Manager biedt geen ondersteuning voor dynamische poorten. Omdat SQL Server genoemde instanties standaard dynamische poorten gebruiken voor verbindingen naar de database-engine, moet u, wanneer u een genoemde instantie gebruikt, de statische poort, die u wenst te gebruiken voor intrasite-communicatie, handmatig configureren.  

Als u een firewall hebt ingeschakeld op de computer waarop SQL Server wordt uitgevoerd, controleer dan of deze de poorten toestaat die bij uw implementatie en op de locaties in het netwerk tussen computers die communiceren met de SQL Server, worden gebruikt.  

Zie voor een voorbeeld van hoe u SQL Server configureren voor het gebruik van een specifieke poort [hoe: Configureren van een Server om te luisteren naar een specifieke TCP-poort (SQL Server Configuration Manager)](http://go.microsoft.com/fwlink/p/?LinkID=226349) in de SQL Server TechNet-bibliotheek.  

## <a name="upgrade-options-for-sql-server"></a>Upgrade-opties voor SQL Server
Als u moet de versie van SQL Server wilt bijwerken, raden wij de volgende methoden van eenvoudig complexere.
1. [SQL Server in-place upgrade](/sccm/core/servers/manage/upgrade-on-premises-infrastructure#a-namebkmksupconfigupgradedbsrva-upgrade-sql-server-on-the-site-database-server) (aanbevolen).
2. Een nieuwe versie van SQL Server op een nieuwe computer installeren en vervolgens [gebruikt u de optie-database verplaatsen](/sccm/core/servers/manage/modify-your-infrastructure#a-namebkmkdbconfiga-modify-the-site-database-configuration) installatieprogramma van Configuration Manager uw siteserver verwijzen naar de nieuwe SQL-Server.
3. Gebruik [back-up en herstel](/sccm/protect/understand/backup-and-recovery).
