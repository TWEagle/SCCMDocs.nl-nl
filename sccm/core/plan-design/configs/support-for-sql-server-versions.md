---
title: Ondersteunde versies van SQL Server | Microsoft-documenten
description: SQL Server-versie en configuratie-vereisten voor het hosten van een System Center Configuration Manager-sitedatabase worden opgehaald.
ms.custom: na
ms.date: 05/10/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 35e237b6-9f7b-4189-90e7-8eca92ae7d3d
caps.latest.revision: 21
author: Brenduns
ms.author: brenduns
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: f809c9327db9f298168674add2d09820fdecd1b8
ms.openlocfilehash: 4166560602edf6eb299511c8b59dc3903e3bfffc
ms.contentlocale: nl-nl
ms.lasthandoff: 05/17/2017


---
# <a name="supported-sql-server-versions-for-system-center-configuration-manager"></a>Ondersteunde versies van SQL Server voor System Center Configuration Manager

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*

Elke System Center Configuration Manager-site moet een ondersteunde versie van SQL Server en -configuratie voor het hosten van de sitedatabase.  

##  <a name="bkmk_Instances"></a> SQL Server-exemplaren en -locaties  
 **Centrale beheersite en primaire sites:**  
De sitedatabase moet een volledige installatie van SQL Server gebruiken.  

 SQL Server kan worden gevonden op:  

-   De siteservercomputer.  
-   Een computer die extern is van de siteserver.  

De volgende exemplaren worden ondersteund:  

-   De standaardwebsite of een benoemd exemplaar van SQL Server.  
-   Configuraties met meerdere exemplaar.  
-   Een SQL Server-cluster. Zie [een SQL Server-cluster gebruiken als host voor de sitedatabase](../../../core/servers/deploy/configure/use-a-sql-server-cluster-for-the-site-database.md).
-   Een SQL Server AlwaysOn-beschikbaarheidsgroep. Deze optie vereist Configuration Manager 1602 of hoger. Zie voor meer informatie, [SQL Server AlwaysOn van een maximaal beschikbare sitedatabase voor System Center Configuration Manager](../../../core/servers/deploy/configure/sql-server-alwayson-for-a-highly-available-site-database.md).


 **Secundaire sites:**  
 De sitedatabase kunt het standaardexemplaar van een volledige installatie van SQL Server of SQL Server Express gebruiken.  

 SQL Server moet zich bevinden op de siteservercomputer.  

 **Beperkingen voor de ondersteuning van**   
 De volgende configuraties worden niet ondersteund:
 -   Een SQL Server-cluster in een clusterconfiguratie Network Load Balancing (NLB)
 -   Een SQL Server-cluster op een Cluster Shared Volume (CSV)
 -   SQL Server-datbase spiegelen technologie en peer-to-peer-replicatie

SQL Server transactionele replicatie wordt alleen ondersteund voor het repliceren van objecten op beheerpunten die zijn geconfigureerd voor gebruik [database replica's](https://technet.microsoft.com/library/mt608546.aspx).  

##  <a name="bkmk_SQLVersions"></a> Ondersteunde versies van SQL Server  
 In een hiërarchie met meerdere sites kunnen verschillende sites verschillende versies van SQL Server gebruiken voor het hosten van de sitedatabase zolang het volgende waar zijn:
 -  Configuration Manager ondersteunt de versies van SQL Server die u gebruikt.
 -  De SQL Server-versies die u gebruikt, blijven ondersteund door Microsoft.
 -  SQL Server ondersteunt de replicatie tussen de twee versies van SQL Server.  Bijvoorbeeld, [SQL Server biedt geen ondersteuning voor replicatie tussen SQL Server 2008 R2 en SQL Server 2016](https://docs.microsoft.com/sql/relational-databases/replication/deprecated-features-in-sql-server-replication).



 Tenzij anders bepaald, worden de volgende versies van SQL Server worden ondersteund met alle actieve versies van System Center Configuration Manager. Als ondersteuning voor een nieuwe SQL Server-versie of servicepack wordt toegevoegd, wordt de Configuration Manager-versie die wordt toegevoegd die ondersteuning bieden voor worden vermeld. Op dezelfde manier als ondersteuning is afgekeurd en zoek vervolgens voor meer informatie over de desbetreffende versies van Configuration Manager.   

Ondersteuning voor een specifieke SQL Server servicepack bevat cumulatieve updates voor servicepack, tenzij een cumulatieve update de achterwaartse naar die base versie van servicepack. Als clientversie zonder servicepack wordt aangegeven, is de ondersteuning voor die versie van SQL Server zonder service Pack. In de toekomst, als een servicepack wordt vrijgegeven voor die versie, wordt een afzonderlijke ondersteuningsverklaring worden gedeclareerd voordat deze nieuwe versie van servicepack wordt ondersteund.


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
 Deze versie van SQL Server blijft ondersteund wanneer u een versie van Configuration Manager vóór 1702.

Als dit wordt ondersteund door uw versie van Configuration Manager, kunt u deze versie van SQL Server als clientversie zonder minimale cumulatieve update voor het volgende:  

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
 Het volgende vereist zijn voor alle installaties van SQL Server die u voor een sitedatabase gebruikt (inclusief SQL Server Express). Wanneer Configuration Manager SQL Server Express als onderdeel van een secundaire site-installatie installeert, worden deze configuraties automatisch voor u gemaakt.  

 **Versie van SQL Server-architectuur:**  
 Configuration Manager vereist een 64-bits versie van SQL Server om de sitedatabase te hosten.  

 **Databasesortering:**  
 Zowel het exemplaar van SQL Server die wordt gebruikt voor de site en de sitedatabase moet de volgende sortering gebruiken op elke site: **SQL_Latin1_General_CP1_CI_AS**.  

 Configuration Manager ondersteunt twee uitzonderingen voor deze verzameling om te voldoen aan de normen die zijn gedefinieerd in GB18030 voor gebruik in China. Voor meer informatie, zie [Internationale ondersteuning in System Center Configuration Manager](../../../core/plan-design/hierarchy/international-support.md).  

 **SQL Server-functies:**  
 Alleen het onderdeel **Database-engineservices** is vereist voor elke siteserver.  

 Geen Configuration Manager-databasereplicatie vereist de **SQL Server-replicatie** functie. Deze SQL Server-configuratie is echter vereist als u [replica's voor beheerpunten voor System Center Configuration Manager-database](../../../core/servers/deploy/configure/database-replicas-for-management-points.md).  

 **Windows-verificatie:**  
 Configuration Manager vereist **Windows-verificatie** valideren verbindingen met de database.  

 **SQL Server-exemplaar:**  
 U moet een exclusief exemplaar van SQL Server gebruiken voor elke site. Dit kan een **benoemd exemplaar** of het **standaardexemplaar**zijn.  

 **SQL Server-geheugen:**  
 Geheugen gereserveerd voor SQL Server met behulp van SQL Server Management Studio en instelling de **Minimum servergeheugen** stellen onder **Servergeheugenopties**. Zie voor meer informatie over het instellen van een vaste hoeveelheid geheugen [How to: Instellen van een vaste hoeveelheid geheugen (SQL Server Management Studio)](http://go.microsoft.com/fwlink/p/?LinkId=233759).  

-   **Voor een database-server die op dezelfde computer als de siteserver is geïnstalleerd:** Beperk het geheugen voor SQL Server op 50 80 procent van de beschikbare adresseerbare systeemgeheugen.  

-   **Voor een databaseserver (externe van de siteserver):** Beperk het geheugen voor SQL Server 80 tot 90 procent van de beschikbare adresseerbare systeemgeheugen.  

-   **Voor een geheugenreservering op voor de bufferpool van elk SQL Server-exemplaar gebruikt:**  

    -   Voor een centrale beheersite: Stel een minimum van 8 gigabyte (GB).  
    -   Voor een primaire site: Stel een minimum van 8 gigabyte (GB).  
    -   Voor een secundaire site: Stel een minimum van 4 GB (Gigabyte).  

**Geneste SQL-triggers:**  
 [Genest SQL-triggers](http://go.microsoft.com/fwlink/?LinkId=528802) moet zijn ingeschakeld.  

 **SQL Server CLR-integratie**  
  SQL Server Common Language Runtime (CLR) moet zijn ingeschakeld voor de sitedatabase. Dit is automatisch ingeschakeld wanneer Configuration Manager wordt geïnstalleerd. Zie voor meer informatie over CLR [Inleiding tot SQL Server CLR-integratie](https://msdn.microsoft.com/library/ms254498\(v=vs.110\).aspx).  

##  <a name="bkmk_optional"></a> Optionele configuraties voor SQL Server  
 De volgende configuraties zijn optioneel voor elke database die een volledige installatie van SQL Server gebruikt.  

 **SQL Server-service:**  
 U kunt de SQL Server-service zo configureren dat deze wordt uitgevoerd met:  

-   De **lokale domeingebruiker** account:  

    -   Dit is een best practice en mogelijk moet u de service principal name (SPN) voor het account handmatig registreren.  

-   De **lokaal systeem** -account van de computer met SQL Server:  

    -   Gebruik het account voor het lokale systeem om het configuratieproces te vereenvoudigen.  
    -   Wanneer u het lokale systeemaccount, Configuration Manager automatisch wordt geregistreerd, de SPN voor de SQL Server-service.  
    -   Houd er wel rekening mee dat u het lokale systeemaccount in SQL Server beter niet kunt gebruiken voor de SQL Server-service.  

Wanneer de computer met SQL Server niet de lokale systeemaccount gebruikt de SQL Server-service uit te voeren, moet u de SPN-naam van het account dat de SQL Server-service wordt uitgevoerd in Active Directory Domain Services configureren. (Als het systeem-account wordt gebruikt, de SPN-naam wordt automatisch geregistreerd voor u.)

Zie voor meer informatie over de SPN-namen voor de sitedatabase [beheren van de SPN voor de Sitedatabaseserver](../../../core/servers/manage/modify-your-infrastructure.md#bkmk_SPN) in de [wijzigen van de System Center Configuration Manager-infrastructuur](../../../core/servers/manage/modify-your-infrastructure.md) onderwerp.  

Zie voor meer informatie over het wijzigen van het account dat wordt gebruikt door de SQL Server-service [How to: Het starten van de serviceaccount voor SQL Server (SQL Server Configuration Manager) wijzigen](http://go.microsoft.com/fwlink/p/?LinkId=237661).  

**SQL Server Reporting Services:**  
SQL Server Reporting Services is vereist voor het installeren van een reporting services-punt waarmee u rapporten uitvoeren.  

> [!IMPORTANT]  
> Na de upgrade van SQL Server van een eerdere versie, ziet u de volgende fout:  *Report Builder bestaat niet*.    
> U kunt dit probleem oplossen, moet u de reporting services puntsitesysteemrol installeren.

**SQL Server-poorten:**  
Voor communicatie met de SQL Server database engine en voor replicatie tussen sites, kunt u de standaardconfiguratie van de SQL Server-poort gebruiken of aangepaste poorten opgeven:  

-   **Intersite-communicatie** SQL Server Service Broker TCP 4022 welke gebruikt standaard poort wordt gebruikt.  
-   **Intrasite-communicatie** tussen de SQL Server database engine en verschillende Configuration Manager-sitesysteem rollen gebruiken standaard poort TCP 1433. De volgende sitesysteemrollen communiceren direct met de SQL Server database:  

    -   Beheerpunt  
    -   Computer van de SMS-provider  
    -   Reporting Services-punt  
    -   Siteserver  

Wanneer een computer met SQL Server als host fungeert voor een database van meer dan één site, moet elke database een afzonderlijk exemplaar van SQL Server gebruiken. Ook moet moet elke instantie geconfigureerd zijn voor het gebruik van een unieke set van poorten.  

> [!WARNING]  
>  Configuration Manager biedt geen ondersteuning voor dynamische poorten. Omdat SQL Server genoemde instanties standaard dynamische poorten gebruiken voor verbindingen naar de database-engine, moet u, wanneer u een genoemde instantie gebruikt, de statische poort, die u wenst te gebruiken voor intrasite-communicatie, handmatig configureren.  

Als u een firewall hebt ingeschakeld op de computer waarop SQL Server wordt uitgevoerd, controleer dan of deze de poorten toestaat die bij uw implementatie en op de locaties in het netwerk tussen computers die communiceren met de SQL Server, worden gebruikt.  

Zie voor een voorbeeld van het SQL Server configureren voor gebruik van een specifieke poort [How to: Een Server configureert om te luisteren op een specifieke TCP-poort (SQL Server Configuration Manager)](http://go.microsoft.com/fwlink/p/?LinkID=226349) in de SQL Server TechNet-bibliotheek.  

## <a name="upgrade-options-for-sql-server"></a>Opties voor SQL Server bijwerken
Als u moet de versie van SQL Server wilt bijwerken, raden wij de volgende methoden van eenvoudig complexe.
1. [SQL Server in-place upgrade](/sccm/core/servers/manage/upgrade-on-premises-infrastructure#a-namebkmksupconfigupgradedbsrva-upgrade-sql-server-on-the-site-database-server) (aanbevolen).
2. Een nieuwe versie van SQL Server op een nieuwe computer installeren en vervolgens [gebruikt u de optie datbase verplaatsen](/sccm/core/servers/manage/modify-your-infrastructure#a-namebkmkdbconfiga-modify-the-site-database-configuration) van Configuration Manager setup uw siteserver verwijzen naar de nieuwe SQL Server.
3. Gebruik [back-up en herstel](/sccm/protect/understand/backup-and-recovery).

