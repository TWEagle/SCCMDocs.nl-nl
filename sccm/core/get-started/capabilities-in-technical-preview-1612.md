---
title: Mogelijkheden in Technical Preview 1612 Configuration Manager
description: Meer informatie over functies die beschikbaar zijn in de Technical Preview voor System Center Configuration Manager, versie 1612.
ms.custom: na
ms.date: 01/23/2017
ms.prod: configuration-manager
ms.technology: configmgr-other
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: bceab2e8-2f05-4a17-9ac8-a7a558670fb7
caps.latest.revision: "5"
author: Brenduns
ms.author: brenduns
manager: angrobe
ms.openlocfilehash: bcb14a2be312d4d8a4a9c235652c7bf971a7a976
ms.sourcegitcommit: 51fc48fb023f1e8d995c6c4eacfda7dbec4d0b2f
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 08/07/2017
---
# <a name="capabilities-in-technical-preview-1612-for-system-center-configuration-manager"></a>Mogelijkheden van Technical Preview 1612 voor System Center Configuration Manager

*Van toepassing op: System Center Configuration Manager (Technical Preview)*



Dit artikel bevat de functies die beschikbaar in de Technical Preview voor System Center Configuration Manager, versie 1612 zijn. U kunt deze versie om te werken en nieuwe mogelijkheden toevoegen aan uw Configuration Manager technical preview-site installeren. Controleer voordat u deze versie van de technical preview installeert, de inleidende informatie [Technical Preview voor System Center Configuration Manager](../../core/get-started/technical-preview.md), om vertrouwd te raken met algemene vereisten en beperkingen voor het gebruik van een technical preview hoe bijwerken tussen versies en hoe u feedback over de functies in een technical preview.    


**Hier volgen nieuwe functies die u met deze versie kunt uitproberen.**  

## <a name="the-data-warehouse-service-point"></a>Het punt-Service datawarehouse
Het punt-Service datawarehouse kunt begint met de Technical Preview-versie 1612, u op te slaan en te rapporteren over langetermijnopslag van historische gegevens voor uw Configuration Manager-implementatie. Dit wordt bereikt door geautomatiseerde synchronisaties uit de sitedatabase van Configuration Manager met een datawarehouse-database. Deze gegevens zijn toegankelijk is vanaf uw Reporting services-punt.

Standaard, wanneer u de nieuwe sitesysteemrol installeert Configuration Manager de datawarehouse-database voor u gemaakt op een SQL Server-exemplaar dat u opgeeft. Het datawarehouse ondersteunt maximaal 2 TB aan gegevens, met een tijdstempel voor het bijhouden.  Standaard bevat de gegevens die worden gesynchroniseerd vanuit de sitedatabase gegevensgroepen voor globale gegevens, sitegegevens Global_Proxy, Cloudgegevens en weergaven. U kunt ook wijzigen wat wordt gesynchroniseerd om aanvullende tabellen, of specifieke tabellen uitsluiten bij de replicatie standaardsets.
De gegevens die worden gesynchroniseerd die standaard vindt u informatie over:
- Status van de groepsbeleidstructuur
- Beveiliging
- Naleving
- Schadelijke software   
- Software-implementatie
- Inventarisgegevens (inventarisgeschiedenis is echter niet gesynchroniseerd)

Naast het installeren en configureren van de datawarehouse-database, zodat u gemakkelijk kunt naar zoeken en rapporteren verschillende nieuwe rapporten geïnstalleerd op deze gegevens.

### <a name="data-warehouse-dataflow"></a>Datawarehouse gegevensstroom   
![Datawarehouse_flow](./media/datawarehouse.png)

| Stap         | Details  |
|:------:|-----------|  
| **1**  |  De siteserver worden overgebracht en -gegevens opslaat in de sitedatabase.  |  
| **2** |   Het Data Warehouse-servicepunt haalt op basis van de planning en de configuratie, gegevens uit de sitedatabase.  |  
| **3** |  Het punt-Service datawarehouse brengt en een kopie van de gesynchroniseerde gegevens worden opgeslagen in de Data Warehouse-database. |  
| **A** |  Door ingebouwde rapporten, een aanvraag voor gegevens wordt gedaan die wordt doorgegeven aan de Reporting Services verwijzen met behulp van SQL Server Reporting Services. |  
| **B** |   De meeste rapporten zijn voor actuele informatie en deze aanvragen worden uitgevoerd op de sitedatabase. |  
| **C** | Wanneer een rapport historische gegevens aanvraagt via een van de rapporten met een *categorie* van **Data Warehouse**, de aanvraag is uitgevoerd voor de Data Warehouse-database.   |  

### <a name="prerequisites-for-the-data-warehouse-service-point-and-database"></a>Vereisten voor de Data Warehouse-servicepunt en de database
- Uw hiërarchie moet een Reporting services sitesysteemrol geïnstalleerd hebben.
- De computer waarop u de sitesysteemrol installeert, vereist .NET Framework 4.5.2 of hoger.
- Het computeraccount van de computer waarop u de sitesysteemrol installeert, moet lokale beheerdersmachtigingen op de computer die als voor de datawarehouse-database host fungeert hebben.
- De Administrator-account die u gebruiken voor het installeren van de sitesysteemrol moet een DBO op het exemplaar van SQL Server die als host voor de datawarehouse-database fungeert.  
-  De database wordt ondersteund:
  - Met SQL Server 2012 of later, Enterprise of Datacenter edition.
  - Op een standaard of benoemd exemplaar
  - Op een *SQL Server-Cluster*. Hoewel deze configuratie werken moet, is niet getest en ondersteuning is zo goed mogelijke poging.
  - Wanneer de CO-locatie met een database van de site of Reporting services-punt-database. We raden echter aan deze worden geïnstalleerd op een afzonderlijke server.  
- Het account dat wordt gebruikt als de *Account voor Reporting Services-punt* moet de **db_datareader** machtiging voor de datawarehouse-database.  
- De database wordt niet ondersteund op een *SQL Server AlwaysOn-beschikbaarheidsgroep*.

### <a name="install-the-data-warehouse"></a>Het datawarehouse installeren
Installeren van de datawarehouse-sitesysteemrol op een centrale beheersite of primaire site met behulp van de **toevoegen Wizard sitesysteemrollen** of de **maken Wizard Sitesysteemserver**. Zie [sitesysteemrollen installeren](/sccm/core/servers/deploy/configure/install-site-system-roles) voor meer informatie. Een hiërarchie biedt ondersteuning voor meerdere exemplaren van deze rol, maar slechts één exemplaar wordt ondersteund op elke site.  

Wanneer u de rol installeert, maakt Configuration Manager de datawarehouse-database voor u op het exemplaar van SQL Server die u opgeeft. Als u de naam van een bestaande database opgeven (zoals u doen zou als u [de datawarehouse-database verplaatsen naar een nieuwe SQL-Server](#move-the-data-warehouse-database)), Configuration Manager heeft niet een nieuwe database maken, maar in plaats daarvan gebruikt de die u opgeeft.

#### <a name="configurations-used-during-installation"></a>Configuraties die worden gebruikt tijdens de installatie
Gebruik de volgende informatie om de installatie van de sitesysteemrol te voltooien:

**Selectie van Systeemrol** pagina:  
Voordat u de Wizard verschijnt er een optie om te selecteren en de punt-Service datawarehouse installeert, moet hebt u een Reporting services-punt geïnstalleerd.

**Algemene** pagina: De volgende algemene informatie is vereist:
- **Configuration Manager-database-instellingen:**   
  - **Servernaam** -Geef de FQDN van de server die als host fungeert voor de sitedatabase. Als u niet een standaardexemplaar van SQL Server gebruikt, moet u het exemplaar na de FQDN-naam in de volgende indeling: ***&lt;Sqlserver_FQDN >\&lt; exemplaarnaam >***
  - **Databasenaam** -Geef de naam van de sitedatabase.
  - **Controleer of** -Klik op **controleren** om ervoor te zorgen dat de verbinding met de sitedatabase geslaagd is.
</br></br>
- **Datawarehouse-database-instellingen:**
  - **Servernaam** : Geef de FQDN-naam van de server die als host fungeert voor het Data Warehouse-servicepunt en de database. Als u niet een standaardexemplaar van SQL Server gebruikt, moet u het exemplaar na de FQDN-naam in de volgende indeling: ***&lt;Sqlserver_FQDN >\&lt; exemplaarnaam >***
  - **Databasenaam** -Specificeer de FQDN voor de datawarehouse-database.  Configuration Manager maakt de database met deze naam. Als u de naam van een database die al bestaat op het exemplaar van SQL server opgeeft, wordt Configuration Manager dat de database gebruikt.
  - **Controleer of** -Klik op **controleren** om ervoor te zorgen dat de verbinding met de sitedatabase geslaagd is.

**Synchronisatie-instellingen** pagina:   
- **Instellingen voor gegevens:**
  - **Replicatiegroepen synchroniseren** – Selecteer de gegevensgroepen die u wilt synchroniseren. Zie voor meer informatie over de verschillende soorten gegevensgroepen [databasereplicatie](/sccm/core/servers/manage/data-transfers-between-sites#a-namebkmkdbrepa-database-replication) en **gedistribueerde weergaven** in [gegevensoverdracht tussen sites](/sccm/core/servers/manage/data-transfers-between-sites).
  - **Tabellen die zijn opgenomen om te synchroniseren** – Geef de naam van elke aanvullende tabel die u wilt synchroniseren. Meerdere tabellen worden gescheiden door een komma. Deze tabellen wordt gesynchroniseerd vanaf de sitedatabase naast de replicatiegroepen die u selecteert.
  - **Tabellen die zijn uitgesloten synchroniseren** -Geef de naam van de afzonderlijke tabellen uit replicatiegroepen die u synchroniseert. Tabellen die u opgeeft, zullen worden uitgesloten van. Meerdere tabellen worden gescheiden door een komma.
- **Synchronisatie-instellingen:**
  - **Synchronisatie-interval (minuten)** -Geef een waarde op in minuten. Nadat het interval is bereikt, wordt er een nieuwe synchronisatie gestart. Dit biedt ondersteuning voor een bereik van 60 en 1440 minuten (24 uur).
  - **Planning** -Geef de dagen die u wilt dat de synchronisatie uit te voeren.

**Reporting point toegang**:   
Nadat de datawarehouse-rol is geïnstalleerd, zorg ervoor dat het account dat wordt gebruikt als de *Account voor Reporting Services-punt* heeft de **db_datareader** machtiging voor de datawarehouse-database.

#### <a name="troubleshoot-installation-and-data-synchronization"></a>Installatie en gegevenssynchronisatie oplossen
Gebruik de volgende logboeken voor het onderzoeken van problemen met de installatie van de Data Warehouse-Service-punt of de synchronisatie van gegevens:
- **DWSSMSI.log** en **DWSSSetup.log** -deze Logboeken gebruiken voor het onderzoeken van fouten bij het installeren van het gegevenspunt van de datawarehouse-service.
-   **Microsoft.ConfigMgrDataWarehouse.log** : dit logboek gebruikt voor het onderzoeken van gegevenssynchronisatie tussen de sitedatabase naar de datawarehouse-database.

### <a name="reporting"></a>Rapporten
Nadat u een datawarehouse-sitesysteemrol hebt geïnstalleerd, de volgende rapporten zijn beschikbaar op de Reporting services-punt met een *categorie* van **datawarehouse:**

|Rapport                   | Details                                  |
|-------------------------|------------------------------------------|
| **Rapport over toepassing clientimplementatie** | Details weergeven voor de implementatie van de toepassing voor een bepaalde toepassing en de machine.|
| **Endpoint Protection en een rapport voor naleving van Software-Update**   | Computers weergeven die software-updates ontbreekt.|
| **Hardware-inventaris voor algemeen rapport**  | Alle hardware-inventaris voor een specifieke computer weer.|
| **Software-inventaris voor algemeen rapport**  | Alle software-inventaris voor een specifieke machine weergeven.|
| **Overzicht van de gezondheid van de netwerkinfrastructuur**  |Geeft een overzicht van de status van uw Configuration Manager-infrastructuur.|
| **Lijst met Malware is gedetecteerd**  |Weergave kwaadaardige software die is aangetroffen in de organisatie.|
|** Software distributie samenvatting rapport ** | Een samenvatting van softwaredistributie voor een specifieke advertentie en de machine.|

### <a name="move-the-data-warehouse-database"></a>De Data Warehouse-database verplaatsen
Gebruik de volgende stappen uit de datawarehouse-database verplaatsen naar een nieuwe SQL-Server:

  1. Controleer de databaseconfiguratie van de huidige en noteert u de configuratie-informatie, zoals:  
   - De gegevensgroepen die u synchroniseert
   - Tabellen u opnemen of uitsluiten van synchronisatie       

   Deze gegevensgroepen en tabellen wordt opnieuw configureren nadat u de database naar een nieuwe server herstellen en de sitesysteemrol installeert.  

  2. SQL Server Management Studio gebruiken voor back-up van de datawarehouse-database, en vervolgens opnieuw aan die database herstellen naar een SQL-server op de nieuwe computer die als host voor het datawarehouse fungeert.

  Nadat u de database naar de nieuwe server teruggezet, zorg ervoor dat de toegangsmachtigingen voor de database op de nieuwe datawarehouse-database dezelfde zijn als ze op de oorspronkelijke datawarehouse-database waren.

  3. Gebruik de Configuration Manager-console de sitesysteemrol-Service datawarehouse verwijderen uit de huidige server.

  4. Een nieuwe Service datawarehouse-punt installeren en geef de naam van de nieuwe SQL-Server en het exemplaar dat als host fungeert voor de Data Warehouse-database die u teruggezet.

  5. Nadat de sitesysteemrol is geïnstalleerd, wordt de verplaatsing is voltooid.

U kunt de volgende logboeken Configuration Manager om te bevestigen dat is de sitesysteemrol opnieuw bekijken:  
- **DWSSMSI.log** en **DWSSSetup.log** -deze Logboeken gebruiken voor het onderzoeken van fouten bij het installeren van het gegevenspunt van de datawarehouse-service.
-   **Microsoft.ConfigMgrDataWarehouse.log** : dit logboek gebruikt voor het onderzoeken van gegevenssynchronisatie tussen de sitedatabase naar de datawarehouse-database.


## <a name="content-library-cleanup-tool"></a>Inhoudsbibliotheek opschoonprogramma
Vanaf Technical Preview-versie 1612, kunt u een nieuw vanaf de opdrachtregel-hulpprogramma (**ContentLibraryCleanup.exe**) inhoud die niet meer is gekoppeld aan een pakket of toepassing van een distributiepunt te verwijderen (en gaat zweven inhoud). Dit hulpprogramma wordt de Inhoudsbibliotheek opschoonprogramma genoemd.

Dit hulpprogramma is alleen van invloed op de inhoud op het distributiepunt dat u opgeeft wanneer u het hulpprogramma uitvoeren en inhoud van de Inhoudsbibliotheek op de siteserver niet verwijderen.

Nadat u de Technical Preview 1612 installeert, kunt u vinden **ContentLibraryCleanup.exe** in de *%CM_Installation_Path%\cd.latest\SMSSETUP\TOOLS\ContentLibraryCleanup\* map op de siteserver van de Technical Preview.

Het hulpprogramma uitgebracht met deze Technical Preview is bedoeld ter vervanging van oudere versies van vergelijkbare hulpmiddelen uitgebracht voor afgelopen Configuration Manager-producten. Hoewel deze hulpprogrammaversie niet meer werken na 1 maart 2017 vrijgeven nieuwe versies met toekomstige Technical Previews zolang dit hulpprogramma is uitgebracht als onderdeel van de huidige vertakking of een productie gereed out-of-band-release.

### <a name="requirements"></a>Vereisten  
 - Het hulpprogramma kan worden uitgevoerd, rechtstreeks op de computer die als host fungeert voor het distributiepunt of extern vanaf een andere server. Het hulpprogramma kan alleen worden uitgevoerd voor één distributiepunt tegelijk.
 - Het gebruikersaccount dat het hulpprogramma uitvoert moet rechtstreeks machtigingen voor beheer op basis van rollen die gelijk aan een volledige beheerder op de Configuration Manager-hiërarchie zijn hebben.  De tool werkt niet als gebruikersaccount machtigingen worden toegekend als lid van een Windows-beveiligingsgroep die de volledige beheerdersrechten heeft.

### <a name="modes-of-operation"></a>Bedrijfsmodi
Het hulpprogramma kan worden uitgevoerd in twee modi:
  1.    **Wat-als de modus**:   
      Wanneer u geeft niet de **/verwijderen** switch, het hulpprogramma in wat-als-modus wordt uitgevoerd en de inhoud die worden verwijderd van het distributiepunt identificeert maar niet daadwerkelijk verwijderen geen gegevens.

      - Wanneer het hulpprogramma wordt uitgevoerd in deze modus, wordt automatisch informatie over de inhoud die worden verwijderd geschreven naar het logboekbestand van de hulpprogramma's. De gebruiker niet gevraagd om elke mogelijke verwijdering te bevestigen.
      - Standaard is het logboekbestand geschreven naar de map temp van gebruikers op de computer waarop u het hulpprogramma uitvoert maar kunt u de schakeloptie voor het logboekbestand omleiden naar een andere locatie.  
      </br>

    U wordt aangeraden het hulpprogramma uitvoeren in deze modus en de resulterende logboekbestand controleren voordat u het hulpprogramma met de schakeloptie/DELETE uitvoeren.  

  2. **De modus verwijderen**: Wanneer u het hulpprogramma uitvoert met de **/verwijderen** switch, het hulpprogramma wordt uitgevoerd in de modus verwijderen.

     - Wanneer het hulpprogramma wordt uitgevoerd in deze modus, kan zwevende inhoud die is gevonden op het opgegeven distributiepunt worden verwijderd uit de Inhoudsbibliotheek het distributiepunt.
     -  Voordat u elk bestand verwijdert, wordt de gebruiker gevraagd om te bevestigen dat het bestand moet worden verwijderd.  U kunt selecteren, **Y** Ja, **N** voor Nee, of **Ja op Alles** verdere aanwijzingen overslaan en alle zwevende inhoud verwijderen.  
     </br>

     U wordt aangeraden het hulpprogramma uitvoeren in wat-als de modus en de resulterende logboekbestand controleren voordat u het hulpprogramma met de schakeloptie/DELETE uitvoeren.  

Wanneer de Inhoudsbibliotheek opschoonprogramma in de modus wordt uitgevoerd, wordt automatisch een logboekbestand gemaakt met een naam met de modus voor die het hulpprogramma wordt uitgevoerd in, de naam van distributiepunt, de datum en tijd van de bewerking. Het logboekbestand wordt automatisch geopend wanneer het hulpprogramma is voltooid. Standaard dit logboek wordt geschreven naar de gebruikers **temp** map op de computer waarop u het hulpprogramma uitvoert. u kunt echter gebruiken een opdrachtregelparameter het logboekbestand omleiden naar een andere locatie, met inbegrip van een netwerkshare.   


### <a name="run-the-tool"></a>Het hulpprogramma uitvoeren
Het hulpprogramma uitvoert:
1. Open een beheeropdrachtprompt naar een map met **ContentLibraryCleanup.exe**.  
2. Geef vervolgens een opdrachtregel met de vereiste opdrachtregelparameters en schakelopties die u wilt gebruiken.

**Bekende probleem** wanneer het hulpprogramma wordt uitgevoerd, een fout als volgt kan worden geretourneerd wanneer een pakket of de implementatie is mislukt of uitgevoerd wordt:
-  *System.InvalidOperationException: Deze Inhoudsbibliotheek kan niet worden opgeschoond nu omdat pakket <packageID> niet volledig is geïnstalleerd.*

**Tijdelijke oplossing:** Geen. Het hulpprogramma kan geen betrouwbare zwevende bestanden bepalen wanneer inhoud uitgevoerd wordt of is mislukt om te implementeren. Daarom kunt het hulpprogramma niet u tot de inhoud opschonen totdat dit probleem opgelost is.



### <a name="command-line-switches"></a>Opdrachtregelopties  
De volgende opdrachtregelopties kunnen worden gebruikt in een willekeurige volgorde.   

|Switch|Details|
|---------|-------|
|**/ Delete**  |**Optioneel** </br> Gebruik deze switch als u inhoud wilt verwijderen uit het distributiepunt. U wordt gevraagd voordat inhoud wordt verwijderd. </br></br> Wanneer deze switch niet gebruikt wordt, registreert het hulpprogramma resultaten over welke inhoud wordt verwijderd, maar worden niet alle inhoud verwijderd uit het distributiepunt. </br></br> Voorbeeld: ***/ Delete ContentLibraryCleanup.exe /dp server1.contoso.com*** |
| **/q**       |**Optioneel** </br> Het hulpprogramma uitvoeren in stille modus die alle prompts onderdrukken (zoals wordt u gevraagd wanneer u inhoud wilt verwijderen) en het logboekbestand niet automatisch openen. </br></br> Voorbeeld: ***ContentLibraryCleanup.exe /q /dp server1.contoso.com*** |
| **/dp &lt;distribution point FQDN >**  | **Vereist** </br> Geef de volledig gekwalificeerde domeinnaam (FQDN) van het distributiepunt dat u wilt opruimen. </br></br> Voorbeeld:  ***ContentLibraryCleanup.exe /dp server1.contoso.com***|
| **/PS &lt;primaire site FQDN >**       | **Optionele** bij het opschonen van de inhoud van een distributiepunt op een primaire site.</br>**Vereist** bij het opschonen van de inhoud van een distributiepunt op een secundaire site. </br></br> Geef dat de FQDN-naam van de primaire site op het distributiepunt naar of van de bovenliggende primaire bovenliggende behoort, wanneer het distributiepunt zich op een secundaire site. </br></br> Voorbeeld: ***ContentLibraryCleanup.exe /dp server1.contoso.com /ps siteserver1.contoso.com*** |
| **/sc &lt;primaire sitecode >**  | **Optionele** bij het opschonen van de inhoud van een distributiepunt op een primaire site.</br>**Vereist** bij het opschonen van de inhoud van een distributiepunt op een secundaire site. </br></br> Geef de sitecode van de primaire site die het distributiepunt bij of van de bovenliggende primaire site wanneer het distributiepunt zich op een secundaire site.</br></br> Voorbeeld: ***ContentLibraryCleanup.exe /dp server1.contoso.com /sc ABC*** |
| **/ log<log file directory>**       |**Optioneel** </br> Geef de map voor het plaatsen van de logboekbestanden in. Dit kan een lokaal station of een netwerkshare.</br></br> Wanneer deze switch niet gebruikt wordt, worden logboekbestanden automatisch geplaatst in de map temp van gebruikers.</br></br> Voorbeeld van de lokale schijf: ***ContentLibraryCleanup.exe /dp server1.contoso.com/log C:\Users\Administrator\Desktop*** </br></br>Voorbeeld van een netwerkshare bevinden: ***/ Log ContentLibraryCleanup.exe /dp server1.contoso.com \\ &lt;delen >\&lt; map >***|


## <a name="improvements-for-in-console-search"></a>Verbeteringen voor zoeken in de console
Op basis van Uservoice-feedback, hebben we de volgende verbeteringen toegevoegd in de console zoeken:
 - **Pad naar het object:**  
  Veel objecten ondersteunen nu een nieuwe kolom die met de naam **objectpad**.  Wanneer u zoeken en deze kolom in de weergave van de resultaten bevatten, kunt u het pad naar elk object kunt weergeven. Bijvoorbeeld, als u een zoekopdracht voor apps in het knooppunt toepassingen uitvoeren en zoekt ook onderliggende knooppunten de *objectpad* kolom in het resultatenvenster ziet u het pad naar elk object dat wordt geretourneerd.   

- **Behoud van zoektekst:**  
  Wanneer u tekst in het zoekvak invoeren en weer schakelen tussen het zoeken naar een onderliggende knooppunt en het huidige knooppunt, wordt de tekst die u hebt getypt nu behouden blijven en beschikbaar blijven voor een nieuwe zoekopdracht zonder te hoeven typen.

- **Behoud van uw beslissing om te zoeken van onderliggende knooppunten:**  
 De geselecteerde optie voor beide zoeken de *huidige knooppunt* of *alle onderliggende knooppunten* nu zich blijft voordoen wanneer u het knooppunt dat u in werkt wijzigt.   Dit nieuwe gedrag betekent dat u niet wilt dat de beslissing voortdurend opnieuw instellen als u de console navigeert.  Als u de console opent is de optie om te zoeken alleen het huidige knooppunt.

## <a name="prevent-installation-of-an-application-if-a-specified-program-is-running"></a>Installatie van een toepassing worden voorkomen als een opgegeven programma wordt uitgevoerd.
U kunt nu een lijst met uitvoerbare bestanden (met de extensie .exe) configureren in de implementatie-type-eigenschappen die als actief is, wordt de installatie van een toepassing geblokkeerd. Nadat de installatie wordt uitgevoerd, ziet de gebruiker een dialoogvenster te sluiten van de processen die installatie zijn geblokkeerd.

### <a name="try-it-out"></a>Try it out in
Een lijst met uitvoerbare bestanden configureren
1.  Kies op de eigenschappenpagina van elk implementatietype de **afhandeling van Installer** tabblad.
2.  Klik op **toevoegen**, een meer uitvoerbare bestanden toevoegen aan de lijst (bijvoorbeeld **Edge.exe**)
3.  Klik op **OK** implementatie type in het dialoogvenster Eigenschappen te sluiten.

Nu, wanneer u deze toepassing implementeert op een gebruiker of een apparaat en een van de uitvoerbare bestanden die u hebt toegevoegd wordt uitgevoerd, ziet de gebruiker een dialoogvenster voor Software Center melden dat de installatie is mislukt omdat een toepassing wordt uitgevoerd.

## <a name="new-windows-hello-for-business-notification-for-end-users"></a>Nieuwe Windows Hello voor bedrijven kennisgeving voor eindgebruikers

Een nieuwe Windows 10-melding informeert gebruikers dat ze extra acties voltooid Windows Hello voor bedrijven-instellingen (bijvoorbeeld het instellen van een PINCODE) moeten uitvoeren.

## <a name="windows-store-for-business-support-in-configuration-manager"></a>Windows Store voor bedrijven-ondersteuning in Configuration Manager

U kunt nu online gelicentieerde apps met een implementatiedoel implementeren **beschikbaar** vanaf de Windows Store voor bedrijven op pc's met de Configuration Manager-client.
Zie voor meer informatie [apps beheren via de Windows Store voor bedrijven met System Center Configuration Manager](https://docs.microsoft.com/sccm/apps/deploy-use/manage-apps-from-the-windows-store-for-business).

Ondersteuning voor deze functie is momenteel alleen beschikbaar op pc's met de preview-versie van Windows 10 RS2.

## <a name="return-to-previous-page-when-a-task-sequence-fails"></a>Terug naar vorige pagina wanneer een takenreeks mislukt
U kunt nu terugkeren naar een vorige pagina als u een takenreeks uitvoert en er een fout is. Vóór deze versie moest u de takenreeks opnieuw opstarten als er een fout is opgetreden. U kunt bijvoorbeeld de **vorige** knop in de volgende scenario's:

- Wanneer een computer wordt opgestart in Windows PE, wordt het dialoogvenster taak sequence bootstrap mogelijk weer voordat de takenreeks beschikbaar is. Wanneer u in dit scenario op Volgende klikt, wordt de laatste pagina van de takenreeks weergegeven met een bericht dat er geen takenreeksen beschikbaar zijn. Nu kunt u **vorige** opnieuw zoeken naar beschikbare takenreeksen. U kunt dit proces herhalen totdat de takenreeks beschikbaar is.
- Wanneer u een takenreeks uitvoert, maar de afhankelijke inhoud pakketten nog niet beschikbaar zijn op distributiepunten zijn, mislukt de takenreeks wordt uitgevoerd. U kunt nu de ontbrekende inhoud distribueren (indien deze nog niet is gedistribueerd) of wacht totdat de inhoud beschikbaar zijn op distributiepunten en klik op **vorige** het zoeken van de reeks taak opnieuw naar de inhoud hebben.

## <a name="express-installation-files-support-for-windows-10-updates"></a>Snelle installatie bestanden ondersteuning voor Windows 10-updates
Bestanden voor snelle installatie in Configuration Manager ondersteuning voor Windows 10-updates, hebben we toegevoegd. Wanneer u een ondersteunde versie van Windows 10, kunt u nu Configuration Manager-instellingen gebruiken voor het downloaden van alleen de delta tussen de huidige maand Windows 10 cumulatieve Update en de vorige maand update. De volledige 10 cumulatieve Update voor Windows (met inbegrip van alle updates van afgelopen maanden) zijn momenteel in Configuration Manager Current Branch gedownload elke maand. Het gebruik van bestanden voor snelle installatie biedt voor kleinere downloaden en installatie sneller op clients.

> [!IMPORTANT]
> Tijdens de instellingen voor de ondersteuning van het gebruik van bestanden voor snelle installatie is beschikbaar in Configuration Manager deze functionaliteit wordt alleen ondersteund in Windows 10 versie 1607 met een Windows Update Agent-update die deel uitmaakt van de updates zijn uitgebracht op 10 januari 2017 (Patch-dinsdag). Zie voor meer informatie over deze updates [artikel 3213986](https://support.microsoft.com/help/4009938/january-10-2017-kb3213986-os-build-14393-693). U kunt profiteren van de bestanden voor snelle installatie bij de volgende set updates zijn uitgebracht op 14 februari 2017. Windows 10 versie 1607 zonder de update en eerdere versies bieden geen ondersteuning voor bestanden voor snelle installatie.


### <a name="to-enable-the-download-of-express-installation-files-for-windows-10-updates-on-the-server"></a>Het downloaden van bestanden voor snelle installatie voor Windows 10-updates op de server inschakelen
Als u wilt synchroniseren van de metagegevens voor Windows 10-bestanden voor snelle installatie, moet u het inschakelen in de eigenschappen van Software-updatepunt.
1.  Navigeer in de Configuration Manager-console naar **beheer** > **siteconfiguratie** > **Sites**.
2.  Selecteer de centrale beheersite of de zelfstandige primaire site.
3.  Klik op het tabblad **Start** in de groep **Instellingen** op **Sitecomponenten configureren**en klik op **Software-updatepunt**. Op de **updatebestanden** tabblad **volledige bestanden voor alle goedgekeurde updates downloaden en bestanden voor snelle installatie voor Windows 10**.

### <a name="to-enable-support-for-clients-to-download-and-install-express-installation-files"></a>Ondersteuning voor clients kunnen downloaden en installeren van bestanden voor snelle installatie inschakelen
Snelle installatie bestanden als ondersteuning wilt inschakelen op clients, moet u de bestanden voor snelle installatie op clients in de sectie Software-Updates van clientinstellingen inschakelen. Hiermee maakt u een nieuwe HTTP-listener naar aanvragen luistert voor het downloaden van bestanden voor snelle installatie op de poort die u opgeeft. Wanneer u clientinstellingen zodat deze functionaliteit op de client implementeert, wordt geprobeerd de verschillen tussen de huidige maand Windows 10 cumulatieve Update en de vorige maand update downloaden (clients moeten een versie van Windows 10 dat ondersteunt bestanden voor snelle installatie uitvoeren).
1.  Schakel ondersteuning voor bestanden voor snelle installatie in de eigenschappen van onderdeel Software-updatepunt (vorige procedure).
2.  Navigeer in de Configuration Manager-console naar **beheer** > **clientinstellingen**.
3.  Selecteert u de juiste clientinstellingen, klik op de **Start** tabblad **eigenschappen**.
4.  Selecteer de **Software-Updates** pagina, configureert **Ja** voor de **installatie van de Express-Updates op clients inschakelen** instellen en configureren van de poort die wordt gebruikt door de HTTP-listener op de client voor de **poort wordt gebruikt om inhoud te downloaden voor Updates Express** instelling.


## <a name="odata-endpoint-data-access"></a>Toegang tot de gegevens van de OData-eindpunt

 Configuration Manager biedt nu een RESTful OData-eindpunt voor toegang tot gegevens van Configuration Manager. Het eindpunt is compatibel met Odata-versie 4, waardoor de hulpprogramma's zoals Excel en Power BI eenvoudig toegang tot Configuration Manager-gegevens via één eindpunt. Technische Preview 1612 ondersteunt alleen leestoegang tot de objecten in Configuration Manager.  

Gegevens die momenteel beschikbaar is in de [Configuration Manager WMI-Provider](/sccm/develop/reference/configuration-manager-reference) is nu ook toegankelijk zijn met het nieuwe RESTful OData-eindpunt. De entiteitsets die worden weergegeven door de OData-eindpunt kunnen u dezelfde gegevens die u kunt met de WMI-provider een query inventariseren.

### <a name="try-it-out"></a>Try it out in

Voordat u de OData-eindpunt gebruiken kunt, moet u het inschakelen voor de site.

1.  Ga naar **beheer** > **Site-configuratie** > **Sites**.
2.  Selecteer de primaire site en klik op **eigenschappen**.
3.  Klik op het tabblad Algemeen van het eigenschappenblad voor de primaire site **eindpunt voor de REST inschakelen voor alle providers op deze site**, en klik vervolgens op **OK**.

In uw favoriete OData-query-viewer kunt u query's die vergelijkbaar is met de volgende voorbeelden om terug te keren verscheidene objecten in Configuration Manager:

| Doel | OData-query |
|---|---|
| Ophalen van alle verzamelingen | `http://localhost/CMRestProvider/Collection` |
| Ophalen van een verzameling | `http://localhost/CMRestProvider/Collection('SMS00001')`
| Ophalen van de top 100 apparaten in de verzameling | `http://localhost/CMRestProvider/Collection('SMS00001')/Device?$top=100` |
| Ophalen van een apparaat met een resource-ID in de verzameling | `http://localhost/CMRestProvider/Collection('SMS00001')/Device(16777573)` |
| Ophalen van het besturingssysteem van het apparaat in de verzameling | `http://localhost/CMRestProvider/Collection('SMS00001')/Device(16777573)/OPERATING_SYSTEM` |
| Gebruikers krijgen in de verzameling | `http://localhost/CMRestProvider/Collection('SMS00001')/User` |

> [!NOTE]
> De voorbeelden van query's weergegeven in de tabel *localhost* als host voor de naam in de URL en op de computer waarop de SMS-Provider kan worden gebruikt. Als u uw query's vanaf een andere computer uitvoert, vervangt u localhost met de FQDN van de server waarop de SMS Provider is geïnstalleerd.

## <a name="azure-active-directory-onboarding"></a>De voorbereiding op Azure Active Directory

De voorbereiding op Azure Active Directory (AD) maakt een verbinding tussen Configuration Manager en Azure Active Directory moet worden gebruikt door andere cloudservices. Dit kan op dit moment worden gebruikt voor het maken van de verbinding nodig is voor de Cloud Management Gateway.

Deze taak met een Azure-beheerder uitvoeren als u hebt Azure beheerdersreferenties nodig.

#### <a name="to-create-the-connection"></a>De verbinding te maken:

2. In de **beheer** werkruimte, kiest u **Cloudservices** > **Azure Active Directory** > **Azure Active Directory toevoegen**.
2. Kies **aanmelden** het verbinding maken met Azure AD.

#### <a name="configuration-manager-client-requirements"></a>Vereisten voor Configuration Manager-client

Er zijn verschillende vereisten voor het inschakelen van het maken van gebruikersbeleid in de Cloud Management Gateway.

- Het Azure AD-voorbereidingsproces moet zijn voltooid en de client in eerste instantie zijn verbonden met het bedrijfsnetwerk ophalen van gegevens voor de verbinding heeft.
- Clients moeten beide domein (geregistreerd in Active Directory) en cloud-domein (geregistreerd bij Azure AD).
- U moet uitvoeren [Active Directory-Gebruikersdetectie](/sccm/core/servers/deploy/configure/about-discovery-methods#active-directory-user-discovery#active-directory-user-discovery).
- U moet de Configuration Manager-client, zodat gebruikers beleidsaanvragen via Internet wijzigen en implementeren van de wijziging aan de client. Omdat deze wijziging naar de client plaats vindt *op het clientapparaat*, deze kan worden geïmplementeerd via de Cloud Management Gateway Hoewel u dit nog niet hebt voltooid die nodig zijn voor gebruikersbeleid wijzigingen in de configuratie.
- Uw beheerpunt moet worden geconfigureerd om HTTPS te gebruiken voor het beveiligen van het token in het netwerk, en moet .net 4.5 geïnstalleerd hebben.

Nadat u deze wijzigingen in de configuratie, kunt u een gebruikersbeleid maken en clients overschakelen naar het Internet voor het testen van het beleid. Gebruiker beleidsaanvragen via de Cloud Management Gateway wordt geverifieerd met Azure AD-verificatie op basis van tokens.

## <a name="change-to-configuring-multi-factor-authentication-for-device-enrollment"></a>Wijzig bij het configureren van multi-factor authentication voor apparaatinschrijving

Nu dat u multi-factor authentication (MFA) voor apparaatinschrijving in de Azure portal instellen kunt, is de MFA-optie verwijderd uit de Configuration Manager-console. U vindt meer informatie over het instellen van MFA voor inschrijving [in dit onderwerp voor Microsoft Intune](https://docs.microsoft.com/en-us/intune/deploy-use/multi-factor-authentication-azure-active-directory).
