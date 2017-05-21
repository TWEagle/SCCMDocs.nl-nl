---
title: Datawarehouse | Microsoft-documenten
description: Gegevens datawarehouse-servicepunt en de database voor System Center Configuration Manager
ms.custom: na
ms.date: 3/28/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: aaf43e69-68b4-469a-ad58-9b66deb29057
caps.latest.revision: 
author: Brenduns
ms.author: brenduns
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 3c2a07f560e0aa3d2beb7cc50e71c98ac45c27e1
ms.openlocfilehash: 9239f6e749c368835e8594ca2d07378d8555b99e
ms.contentlocale: nl-nl
ms.lasthandoff: 05/17/2017


---
#  <a name="the-data-warehouse-service-point-for-system-center-configuration-manager"></a>Het datawarehouse-servicepunt voor System Center Configuration Manager
*Van toepassing op: System Center Configuration Manager (huidige vertakking)*

Vanaf versie 1702 dat kunt u het webservicepunt van de datawarehouse opslaan en een rapport over langetermijnopslag van historische gegevens voor de Configuration Manager-implementatie.

> [!TIP]  
> Het datawarehouse-servicepunt is geïntroduceerd met versie 1702, is een voorlopige versie-functie. Als u wilt inschakelen, Zie [pre-release functies gebruiken](/sccm/core/servers/manage/pre-release-features).

Het datawarehouse ondersteunt maximaal 2 TB aan gegevens met een tijdstempel voor het bijhouden. Opslag van gegevens wordt gerealiseerd door geautomatiseerde synchronisaties uit de sitedatabase van Configuration Manager naar de datawarehouse-database. Deze informatie is toegankelijk is vanaf de Reporting Services-punt.


Gegevens die worden gesynchroniseerd omvat het volgende uit de algemene gegevens en sitegegevens groepen:
- Status van de infrastructuur
- Beveiliging
- Compatibiliteit
- Schadelijke software   
- Software-implementatie
- Inventaris-informatie (inventarisgeschiedenis is echter niet gesynchroniseerd)

Wanneer de sitesysteemrol wordt geïnstalleerd, installeert en configureert u de datawarehouse-database. Ook installeert enkele rapporten zodat u gemakkelijk kunt zoeken en in het rapport op deze gegevens.



## <a name="prerequisites-for-the-data-warehouse-service-point"></a>Vereisten voor het datawarehouse-servicepunt
- De computer waarop u de sitesysteemrol installeert .NET Framework 4.5.2 is vereist of hoger.
- Het computeraccount van de computer waarop u de sitesysteemrol installeert, wordt gebruikt om gegevens te synchroniseren met de datawarehouse-database. Deze account vereist de volgende machtigingen:  
  - **Beheerder** op de computer die als voor de datawarehouse-database host fungeert.
  - **DB_owner** machtiging op de datawarehouse-database.
-    De datawarehouse-database wordt ondersteund op een standaard of benoemde instantie van SQL Server 2012 of later. De editie moet Enterprise of Datacenter.
  - SQL Server AlwaysOn-beschikbaarheidsgroep: Deze configuratie wordt niet ondersteund.
  - SQL Server-Cluster: SQL Server-failoverclusters worden niet ondersteund. Dit komt doordat de datawarehouse-database niet diep zijn getest op SQL Server-failoverclusters.
  - Als de datawarehouse-database extern van de site server-database is, moet u een afzonderlijke licentie hebben voor de SQL Server die als host fungeert voor de database.

> [!IMPORTANT]  
> Het datawarehouse wordt niet ondersteund wanneer de computer met de datawarehouse-servicepunt of die als host fungeert de datawarehouse-database wordt uitgevoerd in een van de volgende talen:
> - JPN – Japans
> - KOR – Koreaans
> - CHS – Chinees (Vereenvoudigd)
> - CHT – traditioneel Chinees dit probleem wordt opgelost in een toekomstige release.


## <a name="install-the-data-warehouse"></a>Het datawarehouse installeren
U kunt de gegevens datawarehouse Systeemrol alleen de bovenste site van uw hiërarchie (een centrale beheersite of zelfstandige primaire site) installeren.

Elke hiërarchie ondersteunt slechts één exemplaar van deze rol, en kunnen op elk sitesysteem van die site op hoogste niveau bevinden. De SQL Server die als host fungeert voor de database voor het datawarehouse kan lokaal op de sitesysteemrol of extern zijn. Hoewel het datawarehouse met de Reporting Services-punt is geïnstalleerd op dezelfde site werkt, hoeft de twee sitesysteemrollen niet op dezelfde server zijn geïnstalleerd.   

Gebruiken voor het installeren van de rol, de **toevoegen Wizard sitesysteemrollen** of de **maken Sitessysteemserver**. Zie [sitesysteemrollen installeren](/sccm/core/servers/deploy/configure/install-site-system-roles) voor meer informatie.  

Wanneer u de rol installeert, maakt Configuration Manager de datawarehouse-database voor u op het exemplaar van SQL Server die u opgeeft. Als u de naam van een bestaande database opgeven (zoals u doen zou als u [de datawarehouse-database verplaatsen naar een nieuwe SQL Server](#move-the-data-warehouse-database)), Configuration Manager heeft niet een nieuwe database maken, maar in plaats daarvan gebruikt de die u opgeeft.

### <a name="configurations-used-during-installation"></a>Configuraties die worden gebruikt tijdens de installatie
**Selectie van Systeemrol** pagina:  

**Algemene** pagina:
-     **Configuration Manager-datawarehouse, instellingen voor de databaseverbinding**:
 - **SQL Server volledig gekwalificeerde domeinnaam**:  
 Geef de volledig gekwalificeerde domeinnaam (FQDN) van de server die als host fungeert voor de service-punt datawarehousedatabase.
 - **SQL Server-instantienaam, indien van toepassing**:   
 Als u een standaardexemplaar van SQL Server niet gebruikt, moet u het exemplaar opgeven.
 - **Databasenaam**:   
 Geef een naam voor de datawarehouse-database.  Configuration Manager maakt het datawarehouse-database met deze naam. Als u de naam van een database die al bestaat op het exemplaar van SQL server opgeeft, wordt in Configuration Manager database gebruikt.
 - **SQL Server-poort gebruikt voor verbinding**:   
 Geef het TCP/IP-poortnummer dat is geconfigureerd voor de SQL Server die als host fungeert voor de datawarehouse-datbase van gegevens. Deze poort wordt gebruikt door de datawarehouse-synchronisatieservice verbinding maken met de datawarehouse-database.  

**Synchronisatieplanning** pagina:   
- **Synchronisatieplanning**:
 - **Begintijd**:  
 Geef de duur die u wilt dat de datawarehouse-synchronisatie te starten.
 - **Terugkeerpatroon**:
    - **Dagelijkse**: Geef op dat synchronisatie wordt uitgevoerd voor elke dag.
    - **Wekelijkse**: Geef een enkele dag elke week en wekelijks terugkeerpatroon voor synchronisatie.

## <a name="reporting"></a>Rapporten
Nadat u een datawarehouse-servicepunt geïnstalleerd, worden diverse rapporten beschikbaar is op de Reporting Services-punt is geïnstalleerd op dezelfde site. Als u de datawarehouse-servicepunt installeren voordat u een Reporting Services-punt installeert, wordt de rapporten automatisch toegevoegd wanneer u later de Reporting Services-punt installeert.

De sitesysteemrol van het datawarehouse bevat de volgende rapporten, waarvoor een categorie van **datawarehouse**:
 - **Toepassingsimplementatie - historische**:   
 Details weergeven voor de implementatie van de toepassing voor een bepaalde toepassing en de machine.
 - **Endpoint Protection en Software-Update compatibiliteit - historische**: Computers weergeven die software-updates ontbreken.  
 - **Algemene Hardware-inventaris - historische**:      
 Alle hardware-inventaris voor een specifieke computer weergeven.
 - **Algemene Software-inventarisatie - historische**:      
 Alle software-inventaris voor een specifieke computer weergeven.
 - **Infrastructuur Health overzicht - historische**:     
 Geeft een overzicht van de status van de Configuration Manager-infrastructuur
 - **Lijst met Malware gedetecteerd - historische**:     
 Weergave kwaadaardige software die is aangetroffen in de organisatie.
 - **Software distribueren samenvatting - historische**:     
 Een samenvatting van softwaredistributie te gebruiken voor een specifieke advertentie en de machine.


## <a name="expand-an-existing-stand-alone-primary-into-a-hierarchy"></a>Een bestaande zelfstandige primaire uitbreiden tot een hiërarchie
Voordat u een centrale beheersite om uit te breiden van een bestaande zelfstandige primaire site installeert, moet u eerst de rol van het datawarehouse service verwijderen. Nadat u de centrale beheersite installeert, kunt u vervolgens de sitesysteemrol op de centrale beheersite installeren.  

In tegenstelling tot een verplaatsing van de datawarehouse-database, wordt deze wijziging resulteert in een verlies van de historische gegevens die u eerder hebt gesynchroniseerd op de primaire site. Het wordt niet ondersteund voor back-up van de database van de primaire site en deze herstellen op de centrale beheersite.




## <a name="move-the-data-warehouse-database"></a>De datawarehouse-database verplaatsen
Gebruik de volgende stappen uit de datawarehouse-database verplaatsen naar een nieuwe SQL-Server:

1.    Gebruik SQL Server Management Studio back-up van de gegevens te datawarehouse-database en zet u dat de database naar een SQL Server op de nieuwe computer die als voor het datawarehouse host fungeert.   
> [!NOTE]     
> Nadat u de database naar de nieuwe server herstellen, zorg ervoor dat de toegangsmachtigingen voor de database op de nieuwe datawarehouse-database op dezelfde zoals ze op de oorspronkelijke datawarehouse-database waren.  

2.    Gebruik de Configuration Manager-console te verwijderen van de datawarehouse-service de sitesysteemrol van de huidige server.
3.    Installeer de Data Warehouse-servicepunt en geef de naam van de nieuwe SQL-Server en het exemplaar dat als host fungeert voor de datawarehouse-database die u hebt hersteld.
4.    Nadat de sitesysteemrol is geïnstalleerd, is de verplaatsing is voltooid.

## <a name="troubleshooting-data-warehouse-issues"></a>Problemen met datawarehouses oplossen
**Logboekbestanden**:  
Gebruik de volgende logboeken voor het onderzoeken van problemen met de installatie van het datawarehouse-servicepunt of de synchronisatie van gegevens:
 - *DWSSMSI.log* en *DWSSSetup.log* -deze Logboeken gebruiken voor het onderzoeken van fouten bij de installatie van het datawarehouse-servicepunt.
 - *Microsoft.ConfigMgrDataWarehouse.log* – dit logboek gebruikt voor het onderzoeken van synchronisatie van gegevens tussen de sitedatabase naar de datawarehouse-database.

**Fout bij instellen**  
 Installatie van het datawarehouse-servicepunt mislukt op een externe sitesysteemserver bevindt wanneer het datawarehouse de eerste sitesysteemrol op die computer geïnstalleerd is.  
  - **Oplossing**:   
    Zorg ervoor dat de computer die u de datawarehouse-servicepunt op al installeert als host fungeert voor ten minste één andere sitesysteemrol.  


**Bekende problemen met synchronisatie**:   
Synchronisatie is mislukt met de volgende handelingen uit in de *Microsoft.ConfigMgrDataWarehouse.log*: **"het vullen van de schema-objecten is mislukt"**  
 - **Oplossing**:  
    Zorg ervoor dat het computeraccount van de computer die als host fungeert voor de sitesysteemrol is een **db_owner** op de datawarehouse-database.

Datawarehouse-rapporten niet worden geopend wanneer de datawarehouse-database en reporting service-punt zich op verschillende site-systemen.  

 - **Oplossing**:  
    Verleen de **Account voor Reporting Services-punt** de **db_datareader** machtiging op de datawarehouse-database.

Wanneer u een rapport met DataWarehouse opent, wordt de volgende fout geretourneerd:

*Er is een fout opgetreden tijdens de rapportverwerking. (rsProcessingAborted) Kan geen verbinding met gegevensbron 'AutoGen__39B693BB_524B_47DF_9FDB_9000C3118E82_' niet maken. (rsErrorOpeningConnection) Er is een verbinding met de server tot stand gebracht, maar vervolgens is een fout opgetreden tijdens de handshake voorafgaand aan de aanmelding. (provider: SSL-Provider, fout: 0 - de certificaatketen is uitgegeven door een certificeringsinstantie die niet wordt vertrouwd.)*

- **Oplossing**: Gebruik de volgende stappen uit om certificaten te configureren:

  1. Op de computer die als host fungeert voor de datawarehouse-database:

    1. Open IIS, klik op **servercertificaten**, met de rechtermuisknop op **zelfondertekend certificaat maken**, en geef vervolgens de "beschrijvende naam" van de naam van het certificaat als **gegevens datawarehouse SQL Server identificatiecertificaat**. Selecteer het certificaatarchief als **persoonlijke**.
    2. Open **SQL Server Configuration Manager**onder **SQL Server-netwerkconfiguratie**, klik met de rechtermuisknop en selecteer **eigenschappen** onder **protocollen voor MSSQLSERVER**. Klik vervolgens op de **certificaat** tabblad **gegevens datawarehouse SQL Server identificatiecertificaat** als het certificaat en sla de wijzigingen.  
    3. Open **SQL Server Configuration Manager**onder **SQL Server-Services**, opnieuw opstarten **SQL Server-service** en **rapportageservice**.
    4.    Open de Microsoft Management Console (MMC) en voeg de module voor **certificaten**optie voor het beheren van het certificaat voor **computeraccount** van de lokale computer. Vouw vervolgens in de MMC de **persoonlijke** map > **certificaten**, en exporteren van de **gegevens datawarehouse SQL Server identificatiecertificaat** als een **DER gecodeerde binaire X.509 (. CER)** bestand.    
  2.    Open de MMC-module op de computer die als host fungeert voor SQL Server Reporting Services, en voeg de module voor **certificaten**, en selecteer vervolgens het certificaat voor beheren **computeraccount**. Onder de **vertrouwde basiscertificeringsinstanties** map, importeer de **gegevens datawarehouse SQL Server identificatiecertificaat**.


## <a name="data-warehouse-dataflow"></a>Gegevens datawarehouse gegevensstroom   
![Datawarehouse_flow](./media/datawarehouse.png)

**Opslag van gegevens en synchronisatie**

| Stap   | Details  |
|:------:|-----------|  
| **1**  |     De siteserver overgedragen en gegevens worden opgeslagen in de sitedatabase.  |  
| **2**  |      Het datawarehouse-servicepunt haalt op basis van de planning en configuratie ervan, gegevens uit de sitedatabase.  |  
| **3**  |  Het datawarehouse-servicepunt overgedragen en wordt een kopie van de gesynchroniseerde gegevens worden opgeslagen in de datawarehouse-database. |  
**Rapportage**

| Stap   | Details  |
|:------:|-----------|  
| **EEN**  |  Ingebouwde rapporten gebruikt, vraagt gegevens aan een gebruiker. Deze aanvraag wordt doorgegeven aan de Reporting Services-punt met SQL Server Reporting Services. |  
| **B**  |      De meeste rapporten zijn voor actuele informatie en deze aanvragen worden uitgevoerd voor de sitedatabase. |  
| **C**  | Wanneer een rapport historische gegevens aanvraagt via een van de rapporten met een *categorie* van **datawarehouse**, de aanvraag is uitgevoerd voor de datawarehouse-database.   |  

