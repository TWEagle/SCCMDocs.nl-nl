---
title: Datawarehouse
titleSuffix: Configuration Manager
description: Datawarehouse-servicepunt en de database voor System Center Configuration Manager
ms.custom: na
ms.date: 02/26/2018
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: aaf43e69-68b4-469a-ad58-9b66deb29057
caps.latest.revision: 
author: mestew
ms.author: mstewart
manager: dougeby
ms.openlocfilehash: 954ec65bae15e087d6cf5afbcc8e0da1ebf83533
ms.sourcegitcommit: be939893f0ceca4add8655ae2c24e42aa16aec38
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 02/27/2018
---
#  <a name="the-data-warehouse-service-point-for-system-center-configuration-manager"></a>De datawarehouse-servicepunt voor System Center Configuration Manager
*Van toepassing op: System Center Configuration Manager (huidige vertakking)*

Begin met versie 1702 kunt u de datawarehouse-service wijst op te slaan en te rapporteren over langetermijnopslag van historische gegevens voor uw Configuration Manager-implementatie.

> [!TIP]
> Deze functie is geïntroduceerd in versie 1702 als een [functie van de voorlopige versie](/sccm/core/servers/manage/pre-release-features). Vanaf versie 1706, deze functie is niet langer een voorlopige versie.

Het datawarehouse ondersteunt maximaal 2 TB aan gegevens, met een tijdstempel voor het bijhouden. Opslag van gegevens wordt gedaan door geautomatiseerde synchronisaties uit de sitedatabase van Configuration Manager met de datawarehouse-database. Deze gegevens zijn toegankelijk is vanaf uw Reporting Service-punt. Gegevens die zijn gesynchroniseerd met de datawarehouse-database wordt drie jaar bewaard. Een ingebouwde taak verwijdert periodiek gegevens die ouder is dan drie jaar.

Gegevens worden gesynchroniseerd omvat het volgende uit de globale gegevens en sitegegevens groepen:
- Status van de groepsbeleidstructuur
- Beveiliging
- Naleving
- Schadelijke software   
- Software-implementatie
- Inventarisgegevens (inventarisgeschiedenis is echter niet gesynchroniseerd)

Wanneer de sitesysteemrol wordt geïnstalleerd, installeert en configureert u de datawarehouse-database. Deze installeert ook verschillende rapporten, zodat u gemakkelijk naar zoeken kunt en in het rapport op deze gegevens.



## <a name="prerequisites-for-the-data-warehouse-service-point"></a>Vereisten voor de data warehouse-servicepunt
- De sitesysteemrol van de datawarehouse wordt alleen ondersteund op de bovenste site van uw hiërarchie. (Een centrale beheersite of zelfstandige primaire site).
- De computer waarop u de sitesysteemrol installeert, vereist .NET Framework 4.5.2 of hoger.
- Verleen de **Account voor Reporting Services-punt** de **db_datareader** machtiging op de datawarehouse-database. 
- Het computeraccount van de computer waarop u de sitesysteemrol installeert, wordt gebruikt om gegevens te synchroniseren met de datawarehouse-database. Deze account vereist de volgende machtigingen:  
  - **Beheerder** op de computer die als host fungeert voor de datawarehouse-database.
  - **DB_Creator** machtiging op de datawarehouse-database.
  - Beide **DB_owner** of **DB_reader** met **uitvoeren** machtigingen voor de sitedatabase van de bovenste site.
- De datawarehouse-database vereist het gebruik van SQL Server 2012 of later. De editie kan zijn Standard, Enterprise of Datacenter.
- De volgende SQL Server-configuraties worden ondersteund voor het hosten van de datawarehouse-database:  
  - Een standaardexemplaar
  - Benoemd exemplaar
  - SQL Server Always On beschikbaarheidsgroep
  - SQL Server-failovercluster
- Als u [gedistribueerde weergaven](/sccm/core/servers/manage/data-transfers-between-sites#bkmk_distviews), de datawarehouse service sitesysteemrol moet installeren op dezelfde server die als host fungeert voor de sitedatabase van de centrale beheersite.

Zie voor informatie over SQL Server-licentieverlening voor de datawarehouse-database, de [product en veelgestelde vragen over licentieverlening](/sccm/core/understand/product-and-licensing-faq). <!-- sms500967 -->


> [!IMPORTANT]  
> Het datawarehouse wordt niet ondersteund wanneer de computer die het gegevenspunt van de datawarehouse-service wordt uitgevoerd of die als host fungeert voor de datawarehouse-database wordt uitgevoerd een van de volgende talen:
> - JPN – Japans
> - KOR – Koreaans
> - CHS – Chinees (Vereenvoudigd)
> - CHT – traditioneel Chinees dit probleem wordt opgelost in een toekomstige release.


## <a name="install-the-data-warehouse"></a>Het datawarehouse installeren
Elke hiërarchie ondersteunt slechts één exemplaar van deze rol op elk sitesysteem van de bovenste site. De SQL Server die als host fungeert voor de database voor het datawarehouse kan zijn voor de sitesysteemrol lokale of externe. Het datawarehouse werkt met reporting services-punt geïnstalleerd op dezelfde site. U hoeft niet te installeren van de twee sitesysteemrollen op dezelfde server.   

U kunt de functie installeren met de **toevoegen Wizard sitesysteemrollen** of de **maken Wizard Sitesysteemserver**. Zie voor meer informatie [sitesysteemrollen installeren](/sccm/core/servers/deploy/configure/install-site-system-roles).  

Wanneer u de rol installeert, maakt Configuration Manager de datawarehouse-database voor u op het exemplaar van SQL Server die u opgeeft. Als u de naam van een bestaande database opgeven (zoals u doen zou als u [de datawarehouse-database verplaatsen naar een nieuwe SQL-Server](#move-the-data-warehouse-database)), Configuration Manager heeft niet een nieuwe database maken, maar in plaats daarvan gebruikt de die u opgeeft.

### <a name="configurations-used-during-installation"></a>Configuraties die worden gebruikt tijdens de installatie
**Selectie van Systeemrol** pagina:  

**Algemene** pagina:
-   **Configuration Manager-datawarehouse verbindingsinstellingen voor database**:
     - **SQL Server FQDN-naam**: Geef de FQDN-naam (Fully qualified domain name) van de server die als host fungeert voor de datawarehouse-service point-database.
     - **SQL Server-instantienaam, indien van toepassing**: Als u niet een standaardexemplaar van SQL Server gebruikt, moet u het exemplaar opgeven.
     - **Databasenaam**: Geef een naam voor de datawarehouse-database. Naam van de database kan niet groter zijn dan 10 tekens. (De lengte van de ondersteunde worden verhoogd in een toekomstige release).
     Configuration Manager maakt de datawarehouse-database met deze naam. Als u de naam van een database die al bestaat op het exemplaar van SQL server opgeeft, wordt in Configuration Manager dat de database gebruikt.
     - **SQL Server-poort gebruikt voor verbinding**: Geef het nummer van de TCP/IP-poort die wordt gebruikt door de SQL Server die als host fungeert voor de datawarehouse-database. Deze poort wordt gebruikt door de datawarehouse-synchronisatieservice verbinding maken met de datawarehouse-database.  

**Synchronisatieplanning** pagina:   
- **Synchronisatieplanning**:
    - **Begintijd**: Geef de tijd die u wilt dat de datawarehouse-synchronisatie te starten.
    - **Terugkeerpatroon**:
         - **Dagelijkse**: Geef op dat de synchronisatie wordt uitgevoerd elke dag.
         - **Wekelijkse**: Geef een enkele dag elke week en wekelijkse terugkeerpatronen voor synchronisatie.

## <a name="reporting"></a>Rapporten
Nadat u een gegevenspunt van de datawarehouse-service hebt geïnstalleerd, worden diverse rapporten beschikbaar zijn op de reporting services-punt is geïnstalleerd op dezelfde site. Als u het gegevenspunt van de datawarehouse-service installeren voordat u een reporting services-punt installeert, worden de rapporten worden automatisch toegevoegd wanneer u later de reporting services-punt installeert.

De sitesysteemrol van de datawarehouse bevat de volgende rapporten, waarvoor een categorie van **Data Warehouse**:
 - **Toepassingsimplementatie - historische**: Details weergeven voor de implementatie van de toepassing voor een bepaalde toepassing en de machine.
 - **Endpoint Protection en Software-Update naleving - historische**: Computers weergeven die software-updates ontbreekt.  
 - **Algemene Hardware-inventarisatie - historische**: Alle hardware-inventaris voor een specifieke computer weer.
 - **Algemene Software-inventarisatie - historische**: Alle software-inventaris voor een specifieke machine weergeven.
 - **Overzicht van de Health netwerkinfrastructuur - historische**: Geeft een overzicht van de status van uw Configuration Manager-infrastructuur
 - **Lijst met Malware gedetecteerd - historische**:   Weergave kwaadaardige software die is aangetroffen in de organisatie.
 - **Software distribueren samenvatting - historische**: Een samenvatting van softwaredistributie voor een specifieke advertentie en de machine.


## <a name="expand-an-existing-stand-alone-primary-into-a-hierarchy"></a>Een bestaande zelfstandige primaire uitbreiden naar een hiërarchie
Voordat u een centrale beheersite als u een bestaande zelfstandige primaire site uitbreiden installeren kunt, moet u eerst de datawarehouse rol verwijderen. Nadat u de centrale beheersite installeert, kunt u de sitesysteemrol op de centrale beheersite installeren.  

In tegenstelling tot een verplaatsing van de datawarehouse-database, wordt deze wijziging resulteert in een verlies van de historische gegevens die u eerder hebt gesynchroniseerd op de primaire site. Dit wordt niet ondersteund voor back-up van de database van de primaire site en deze herstellen op de centrale beheersite.




## <a name="move-the-data-warehouse-database"></a>De datawarehouse-database verplaatsen
Gebruik de volgende stappen uit de datawarehouse-database verplaatsen naar een nieuwe SQL-Server:

1.  SQL Server Management Studio gebruiken voor back-up van de datawarehouse-database. Vervolgens die database herstellen naar een SQL-Server op de nieuwe computer die als host fungeert voor het datawarehouse.   
> [!NOTE]     
> Nadat u de database naar de nieuwe server teruggezet, zorg ervoor dat de toegangsmachtigingen voor de database op de nieuwe datawarehouse-database dezelfde zijn als ze op de oorspronkelijke datawarehouse-database waren.  

2.  De Configuration Manager-console gebruiken om te verwijderen van de datawarehouse-service de sitesysteemrol van de huidige server.
3.  Installeer het gegevenspunt van de datawarehouse-service opnieuw. Geef de naam van de nieuwe SQL Server en -exemplaar dat hosts de gegevens datawarehouse-database die u teruggezet.
4.  Nadat de sitesysteemrol is geïnstalleerd, wordt de verplaatsing is voltooid.

## <a name="troubleshooting-data-warehouse-issues"></a>Het oplossen van problemen met de datawarehouse
**Logboekbestanden**  
Gebruik de volgende logboeken voor het onderzoeken van problemen met de installatie van het gegevenspunt van de datawarehouse-service of de synchronisatie van gegevens:
 - *DWSSMSI.log* en *DWSSSetup.log* -deze Logboeken gebruiken voor het onderzoeken van fouten bij het installeren van het gegevenspunt van de datawarehouse-service.
 - *Microsoft.ConfigMgrDataWarehouse.log* : dit logboek gebruikt voor het onderzoeken van gegevenssynchronisatie tussen de sitedatabase naar de datawarehouse-database.

**Fout bij instellen**  
 Installatie van het gegevenspunt van de datawarehouse-service mislukt op een externe sitesysteemserver als het datawarehouse is de eerste sitesysteemrol die op die computer installeert.  
  - **Oplossing**: Zorg ervoor dat de computer die u installeert de datawarehouse-service al hosts ten minste één andere sitesysteemrollen wijst.  


**Bekende synchronisatieproblemen**:   
Synchronisatie mislukt met het volgende bericht in *Microsoft.ConfigMgrDataWarehouse.log*: **'is mislukt voor het vullen van de schema-objecten'**  
 - **Oplossing**: Zorg ervoor dat het computeraccount van de computer die als host fungeert voor de sitesysteemrol is een **db_owner** op de datawarehouse-database.

Rapporten datawarehouse niet worden geopend wanneer de datawarehouse-database en reporting service-punt zich op verschillende systemen.  

 - **Oplossing**: Verleen de **Account voor Reporting Services-punt** de **db_datareader** machtiging op de datawarehouse-database.

Wanneer u een rapport met inventarisatiegegevens datawarehouse opent, wordt de volgende fout geretourneerd:

*Er is een fout opgetreden tijdens de rapportverwerking. (rsProcessingAborted) Kan geen verbinding met gegevensbron 'AutoGen__39B693BB_524B_47DF_9FDB_9000C3118E82_' niet maken. (rsErrorOpeningConnection) Is een verbinding met de server tot stand gebracht, maar vervolgens is er een fout opgetreden tijdens de handshake vóór aanmelding. (provider: SSL-Provider, fout: 0 - de certificaatketen is uitgegeven door een certificeringsinstantie die wordt niet vertrouwd.)*

- **Oplossing**: Gebruik de volgende stappen uit om certificaten te configureren:

  1. Op de computer die als host fungeert voor de datawarehouse-database:

    1. Open IIS, klik op **servercertificaten**, met de rechtermuisknop op **zelfondertekend certificaat maken**, en geef vervolgens de 'beschrijvende naam"van de naam van het certificaat als **Data Warehouse SQL Server Identification Certificate**. Selecteer het certificaatarchief als **persoonlijke**.
    2. Open **SQL Server Configuration Manager**onder **SQL Server-netwerkconfiguratie**, klik met de rechtermuisknop om te selecteren **eigenschappen** onder **protocollen voor MSSQLSERVER**. Klik op de **certificaat** tabblad **Data Warehouse SQL Server Identification Certificate** als het certificaat en sla de wijzigingen.  
    3. Open **SQL Server Configuration Manager**. Onder **SQL Server-Services**, opnieuw opstarten de **SQL Server-service** en **Reporting Service** services.
    4.  Open de Microsoft Management Console (MMC) en voeg de module voor **certificaten**optie voor het beheren van het certificaat voor **computeraccount** van de lokale computer. Vouw vervolgens in de MMC de **persoonlijke** map > **certificaten**, en exporteer de **Data Warehouse SQL Server Identification Certificate** als een **DER encoded binary X.509 (. CER)** bestand.    
  2.    Open de MMC-module op de computer die als host fungeert voor SQL Server Reporting Services, en voeg de module voor **certificaten**. Selecteer voor het beheren van certificaten voor **computeraccount**. Onder de **vertrouwde basiscertificeringsinstanties** map importeren de **Data Warehouse SQL Server Identification Certificate**.


## <a name="data-warehouse-dataflow"></a>Datawarehouse gegevensstroom   
![Datawarehouse_flow](./media/datawarehouse.png)

**Opslag van gegevens en synchronisatie**

| Stap   | Details  |
|:------:|-----------|  
| **1**  |  De siteserver worden overgebracht en -gegevens opslaat in de sitedatabase.  |  
| **2**  |      Het gegevenspunt van de datawarehouse-service haalt op basis van de planning en de configuratie, gegevens uit de sitedatabase.  |  
| **3**  |  Het gegevenspunt van de datawarehouse-service draagt en slaat een kopie van de gesynchroniseerde gegevens in de datawarehouse-database. |  
**Rapporten**

| Stap   | Details  |
|:------:|-----------|  
| **A**  |  Door ingebouwde rapporten, opvraagt een gebruiker gegevens. Deze aanvraag wordt doorgegeven aan het reporting servicepunt met SQL Server Reporting Services. |  
| **B**  |      De meeste rapporten zijn voor actuele informatie en deze aanvragen worden uitgevoerd op de sitedatabase. |  
| **C**  | Wanneer een rapport historische gegevens aanvraagt via een van de rapporten met een *categorie* van **Data Warehouse**, de aanvraag wordt uitgevoerd op de datawarehouse-database.   |  
