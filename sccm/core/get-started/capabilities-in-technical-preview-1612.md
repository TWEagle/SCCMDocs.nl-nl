---
title: Mogelijkheden in Technical Preview 1612 Configuration Manager
description: Meer informatie over functies die beschikbaar zijn in de Technical Preview voor System Center Configuration Manager, versie 1612.
ms.custom: na
ms.date: 01/23/2017
ms.prod: configuration-manager
ms.technology:
- configmgr-other
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: bceab2e8-2f05-4a17-9ac8-a7a558670fb7
caps.latest.revision: 5
author: Brenduns
ms.author: brenduns
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: dab5da5a4b5dfb3606a8a6bd0c70a0b21923fff9
ms.openlocfilehash: bcb14a2be312d4d8a4a9c235652c7bf971a7a976
ms.contentlocale: nl-nl
ms.lasthandoff: 05/17/2017

---
# <a name="capabilities-in-technical-preview-1612-for-system-center-configuration-manager"></a>Mogelijkheden in Technical Preview 1612 voor System Center Configuration Manager

*Van toepassing op: System Center Configuration Manager (technische Preview)*



Dit artikel bevat de functies die beschikbaar in de Technical Preview voor System Center Configuration Manager, versie 1612 zijn. U kunt deze versie om te werken en nieuwe mogelijkheden toevoegen aan uw technische preview van Configuration Manager site installeren. Voordat u deze versie van de technische preview installeert, leest u de inleidende onderwerp [Technical Preview voor System Center Configuration Manager](../../core/get-started/technical-preview.md), om meer vertrouwd raken met algemene vereisten en beperkingen voor het gebruik van een technische preview hoe tussen versies en hoe u feedback geven over de functies in een technische preview bijwerken.    


**De volgende zijn nieuwe functies die u met deze versie kunt uitproberen.**  

## <a name="the-data-warehouse-service-point"></a>Het punt-Service datawarehouse
Het punt-Service datawarehouse kunt beginnend met de technische voorbeeldversie 1612, u opslaan en rapporteren over langetermijnopslag van historische gegevens voor uw Configuration Manager-implementatie. Dit wordt gerealiseerd door geautomatiseerde synchronisaties uit de sitedatabase van Configuration Manager naar een datawarehouse-database. Deze informatie is toegankelijk is vanaf de Reporting services-punt.

Standaard, wanneer u de nieuwe sitesysteemrol, installeert maakt Configuration Manager de datawarehouse-database voor u op een SQL Server-exemplaar dat u opgeeft. Het datawarehouse ondersteunt maximaal 2 TB aan gegevens met een tijdstempel voor het bijhouden.  De gegevens die worden gesynchroniseerd door de sitedatabase omvat standaard de gegevensgroepen voor globale gegevens, sitegegevens Global_Proxy, Cloudgegevens en weergaven. U kunt ook wijzigen wat wordt gesynchroniseerd, zodat de aanvullende tabellen opnemen of uitsluiten van specifieke tabellen van de standaard replicatie sets.
De standaardgegevens die worden gesynchroniseerd vindt u informatie over:
- Status van de infrastructuur
- Beveiliging
- Compatibiliteit
- Schadelijke software   
- Software-implementatie
- Inventaris-informatie (inventarisgeschiedenis is echter niet gesynchroniseerd)

Naast het installeren en configureren van de datawarehouse-database, zodat u gemakkelijk kunt naar zoeken en rapporteren verschillende nieuwe rapporten geïnstalleerd op deze gegevens.

### <a name="data-warehouse-dataflow"></a>Gegevens datawarehouse gegevensstroom   
![Datawarehouse_flow](./media/datawarehouse.png)

| Stap         | Details  |
|:------:|-----------|  
| **1**  |     De siteserver overgedragen en gegevens worden opgeslagen in de sitedatabase.  |  
| **2** |      Het punt-Service datawarehouse haalt op basis van de planning en configuratie ervan, gegevens uit de sitedatabase.  |  
| **3** |  Het punt-Service datawarehouse overgedragen en wordt een kopie van de gesynchroniseerde gegevens worden opgeslagen in de datawarehouse-database. |  
| **EEN** |  Ingebouwde rapporten een aanvraag voor gegevens wordt gedaan die wordt doorgegeven aan de Reporting Services-punt met SQL Server Reporting Services. |  
| **B** |      De meeste rapporten zijn voor actuele informatie en deze aanvragen worden uitgevoerd voor de sitedatabase. |  
| **C** | Wanneer een rapport historische gegevens aanvraagt via een van de rapporten met een *categorie* van **datawarehouse**, de aanvraag is uitgevoerd voor de datawarehouse-database.   |  

### <a name="prerequisites-for-the-data-warehouse-service-point-and-database"></a>Vereisten voor het controlepunt van de Service datawarehouse en de database
- Uw hiërarchie moet een Reporting services sitesysteemrol geïnstalleerd hebben.
- De computer waarop u de sitesysteemrol installeert .NET Framework 4.5.2 is vereist of hoger.
- Het computeraccount van de computer waarop u de sitesysteemrol installeert, moet lokale beheerdersmachtigingen op de computer die als voor de datawarehouse-database host fungeert hebben.
- De u de sitesysteemrol installeert met Administrator-account moet een DBO op het exemplaar van SQL Server die als voor de datawarehouse-database host fungeert.  
-  De database wordt ondersteund:
  - Met SQL Server 2012 of later, Enterprise of Datacenter-editie.
  - Op een standaardwaarde of een benoemd exemplaar
  - Op een *SQL Server-Cluster*. Hoewel deze configuratie werken moet, is niet getest en ondersteuning is de beste poging.
  - Wanneer met CO-locaties met ofwel de sitedatabase of Reporting services-punt-database. Echter aangeraden deze worden geïnstalleerd op een afzonderlijke server.  
- Het account dat wordt gebruikt als de *Account voor Reporting Services-punt* moet de **db_datareader** machtiging voor de datawarehouse-database.  
- De database wordt niet ondersteund op een *SQL Server AlwaysOn-beschikbaarheidsgroep*.

### <a name="install-the-data-warehouse"></a>Het datawarehouse installeren
U de datawarehouse-sitesysteemrol op een centrale beheersite of primaire site installeren via de **toevoegen Wizard sitesysteemrollen** of de **maken Sitessysteemserver**. Zie [sitesysteemrollen installeren](/sccm/core/servers/deploy/configure/install-site-system-roles) voor meer informatie. Een hiërarchie ondersteunt meerdere exemplaren van deze rol, maar slechts één instantie wordt ondersteund op elke site.  

Wanneer u de rol installeert, maakt Configuration Manager de datawarehouse-database voor u op het exemplaar van SQL Server die u opgeeft. Als u de naam van een bestaande database opgeven (zoals u doen zou als u [de datawarehouse-database verplaatsen naar een nieuwe SQL Server](#move-the-data-warehouse-database)), Configuration Manager heeft niet een nieuwe database maken, maar in plaats daarvan gebruikt de die u opgeeft.

#### <a name="configurations-used-during-installation"></a>Configuraties die worden gebruikt tijdens de installatie
Gebruik de volgende informatie om de installatie van de sitesysteemrol te voltooien:

**Selectie van Systeemrol** pagina:  
Voordat u de Wizard verschijnt er een optie om te selecteren en de punt-Service datawarehouse installeert, moet hebt u een Reporting services-punt geïnstalleerd.

**Algemene** pagina: De volgende algemene informatie is vereist:
- **Configuration Manager-database-instellingen:**   
  - **Servernaam** -Geef de FQDN-naam van de server die als host fungeert voor de sitedatabase. Als u een standaardexemplaar van SQL Server niet gebruikt, moet u het exemplaar na de FQDN-naam in de volgende notatie: ***&lt;Sqlserver_FQDN >\&lt; exemplaarnaam >***
  - **Databasenaam** -Geef de naam van de sitedatabase.
  -    **Controleer of** -Klik op **controleren** om ervoor te zorgen dat de verbinding met de sitedatabase voltooid is.
</br></br>
- **Instellingen voor het datawarehouse-database gegevens:**
  -    **Servernaam** : Geef de FQDN-naam van de server die als host fungeert voor de point-Service datawarehouse en database. Als u een standaardexemplaar van SQL Server niet gebruikt, moet u het exemplaar na de FQDN-naam in de volgende notatie: ***&lt;Sqlserver_FQDN >\&lt; exemplaarnaam >***
  -    **Databasenaam** -Specificeer de FQDN voor de datawarehouse-database.  Configuration Manager maakt de database met deze naam. Als u de naam van een database die al bestaat op het exemplaar van SQL server opgeeft, wordt in Configuration Manager database gebruikt.
  -    **Controleer of** -Klik op **controleren** om ervoor te zorgen dat de verbinding met de sitedatabase voltooid is.

**Synchronisatie-instellingen** pagina:   
- **Instellingen van gegevens:**
  - **Replicatiegroepen synchroniseren** : de gegevens selecteren die u wilt synchroniseren. Zie voor meer informatie over de verschillende soorten gegevensgroepen [databasereplicatie](/sccm/core/servers/manage/data-transfers-between-sites#a-namebkmkdbrepa-database-replication) en **gedistribueerde weergaven** in [gegevensoverdracht tussen sites](/sccm/core/servers/manage/data-transfers-between-sites).
  - **Tabellen die zijn opgenomen als u wilt synchroniseren** – Geef de naam van elke aanvullende tabel die u wilt synchroniseren. Scheid meerdere tabellen met een komma. Deze tabellen worden uit de sitedatabase naast de replicatiegroepen die u selecteert gesynchroniseerd.
  - **Tabellen die zijn uitgesloten synchroniseren** -Geef de naam van de afzonderlijke tabellen uit replicatiegroepen die u synchroniseert. Tabellen die u opgeeft worden uitgesloten uit. Scheid meerdere tabellen met een komma.
- **Synchronisatie-instellingen:**
  - **Synchronisatie-interval (minuten)** -Geef een waarde in minuten. Nadat het interval is bereikt, wordt een nieuwe synchronisatie wordt gestart. Dit ondersteunt een bereik tussen 60 en 1440 minuten (24 uur).
  - **Planning** -Geef de dagen die u wilt synchroniseren om uit te voeren.

**Reporting point toegang**:   
Nadat de gegevens datawarehouse-rol is geïnstalleerd, zorg ervoor dat het account dat wordt gebruikt als de *Account voor Reporting Services-punt* heeft de **db_datareader** machtiging voor de datawarehouse-database.

#### <a name="troubleshoot-installation-and-data-synchronization"></a>Installatie en gegevenssynchronisatie oplossen
Gebruik de volgende logboeken voor het onderzoeken van problemen met de installatie van het punt-Service datawarehouse of de synchronisatie van gegevens:
- **DWSSMSI.log** en **DWSSSetup.log** -deze Logboeken gebruiken voor het onderzoeken van fouten bij de installatie van het gegevenspunt van de datawarehouse-service.
-     **Microsoft.ConfigMgrDataWarehouse.log** – dit logboek gebruikt voor het onderzoeken van synchronisatie van gegevens tussen de sitedatabase naar de datawarehouse-database.

### <a name="reporting"></a>Rapporten
Nadat u een datawarehouse-sitesysteemrol hebt geïnstalleerd, de volgende rapporten zijn beschikbaar op de Reporting services-punt met een *categorie* van **-datawarehouse:**

|Rapport                   | Details                                  |
|-------------------------|------------------------------------------|
| **Rapport over de clientimplementatie van toepassing** | Details weergeven voor de implementatie van de toepassing voor een bepaalde toepassing en de machine.|
| **Endpoint Protection en rapport voor compatibiliteit van Software-updatepunt**   | Computers weergeven die software-updates ontbreken.|
| **Hardware-inventaris voor algemeen rapport**  | Alle hardware-inventaris voor een specifieke computer weergeven.|
| **Software-inventaris voor algemeen rapport**  | Alle software-inventaris voor een specifieke computer weergeven.|
| **Overzicht van de infrastructuur-status**  |Geeft een overzicht van de status van de Configuration Manager-infrastructuur.|
| **Lijst met Malware gedetecteerd**  |Weergave kwaadaardige software die is aangetroffen in de organisatie.|
|** Software distributie samenvatting rapport ** | Een samenvatting van softwaredistributie te gebruiken voor een specifieke advertentie en de machine.|

### <a name="move-the-data-warehouse-database"></a>De datawarehouse-database verplaatsen
Gebruik de volgende stappen uit de datawarehouse-database verplaatsen naar een nieuwe SQL-Server:

  1. Controleer de configuratie van de huidige en noteer de configuratiedetails, met inbegrip van:  
   - De gegevensgroepen die u synchroniseert
   - Tabellen u opnemen of uitsluiten van synchronisatie       

   Deze gegevensgroepen en tabellen wordt opnieuw configureren nadat u de database naar een nieuwe server herstellen en opnieuw installeren van de sitesysteemrol.  

  2. SQL Server Management Studio gebruiken voor back-up van de datawarehouse-database, en vervolgens opnieuw aan die database herstellen naar een SQL-server op de nieuwe computer die als voor het datawarehouse host fungeert.

  Nadat u de database naar de nieuwe server herstellen, zorg ervoor dat de toegangsmachtigingen voor de database op de nieuwe datawarehouse-database op dezelfde zoals ze op de oorspronkelijke datawarehouse-database waren.

  3. Gebruik de Configuration Manager-console te verwijderen van de sitesysteemrol-Service datawarehouse van de huidige server.

  4. Een nieuwe Service datawarehouse-punt installeren en geef de naam van de nieuwe SQL-Server en het exemplaar dat als host fungeert voor de datawarehouse-database die u hebt hersteld.

  5. Nadat de sitesysteemrol is geïnstalleerd, is de verplaatsing is voltooid.

U kunt de volgende logboeken Configuration Manager om te bevestigen van dat de sitesysteemrol is opnieuw weergeven:  
- **DWSSMSI.log** en **DWSSSetup.log** -deze Logboeken gebruiken voor het onderzoeken van fouten bij de installatie van het gegevenspunt van de datawarehouse-service.
-     **Microsoft.ConfigMgrDataWarehouse.log** – dit logboek gebruikt voor het onderzoeken van synchronisatie van gegevens tussen de sitedatabase naar de datawarehouse-database.


## <a name="content-library-cleanup-tool"></a>Inhoudsbibliotheek-hulpprogramma
Beginnend met technische voorbeeldversie 1612, kunt u een nieuw opdrachtregel-hulpprogramma (**ContentLibraryCleanup.exe**) inhoud die is niet meer gekoppeld aan een pakket of toepassing vanuit een distributiepunt te verwijderen (en gaat zweven inhoud). Dit hulpprogramma wordt het hulpprogramma Inhoudsbibliotheek genoemd.

Dit hulpprogramma is alleen van invloed op de inhoud op het distributiepunt dat u opgeeft wanneer u het hulpprogramma uitvoeren en inhoud van de Inhoudsbibliotheek op de siteserver niet verwijderen.

Nadat u technische Preview 1612 installeert, kunt u vinden **ContentLibraryCleanup.exe** in de *%CM_Installation_Path%\cd.latest\SMSSETUP\TOOLS\ContentLibraryCleanup\* map op de siteserver Technical Preview.

Het hulpprogramma uitgebracht met deze Technical Preview is bedoeld ter vervanging van oudere versies van vergelijkbare hulpmiddelen vrijgegeven voor afgelopen Configuration Manager-producten. Hoewel deze hulpprogrammaversie niet meer werken na 1 maart 2017 release nieuwe versies met toekomstige technische voorbeelden zolang dit hulpprogramma is uitgebracht als onderdeel van de huidige vertakking of een productie gereed out-of-band-release.

### <a name="requirements"></a>Vereisten  
 - Het hulpprogramma kan rechtstreeks op de computer die fungeert als host voor het distributiepunt of op afstand vanaf een andere server worden uitgevoerd. Het hulpprogramma kan alleen worden uitgevoerd tegen één distributiepunt tegelijk.
 - Het gebruikersaccount dat het hulpprogramma uitvoert moet rechtstreeks op rollen gebaseerd beheerdersmachtigingen die gelijk aan een volledige beheerder op de Configuration Manager-hiërarchie zijn hebben.  Het hulpprogramma werkt niet wanneer gebruikersaccount machtigingen zijn toegekend als lid van een Windows-beveiligingsgroep die de volledige beheerdersrechten heeft.

### <a name="modes-of-operation"></a>Bedrijfsmodi
Het hulpprogramma u kunt uitvoeren in twee modi:
  1.    **Wat als modus**:   
      Wanneer u geeft niet de **/verwijderen** switch, het hulpprogramma in wat als modus wordt uitgevoerd en identificeert de inhoud die wordt verwijderd uit het distributiepunt maar niet daadwerkelijk verwijderen geen gegevens.

      - Wanneer het hulpprogramma in deze modus wordt uitgevoerd, wordt informatie over de inhoud die wordt verwijderd automatisch geschreven naar een logboekbestand voor de hulpprogramma's. De gebruiker niet gevraagd naar elke mogelijke verwijdering te bevestigen.
      - Standaard het logboekbestand geschreven naar de tijdelijke map van gebruikers op de computer waarop u het hulpprogramma, maar u de schakeloptie kunt het logboekbestand omleiden naar een andere locatie.  
      </br>

    U wordt aangeraden u het hulpprogramma uitvoeren in deze modus en het resulterende logboekbestand controleren voordat u het hulpprogramma met de schakeloptie/DELETE uitvoeren.  

  2. **Modus verwijderen**: Wanneer u het hulpprogramma uitvoert met de **/verwijderen** switch, het hulpprogramma wordt uitgevoerd in de modus verwijderen.

     - Wanneer het hulpprogramma in deze modus wordt uitgevoerd, kan zwevende inhoud die is gevonden op de opgegeven distributiepunt worden verwijderd uit de Inhoudsbibliotheek het distributiepunt.
     -     Voordat u elk bestand verwijdert, wordt de gebruiker gevraagd om te bevestigen dat het bestand moet worden verwijderd.  U kunt selecteren, **Y** Ja, **N** voor Nee, of **Ja op Alles** verdere aanwijzingen overslaan en alle zwevende inhoud verwijderen.  
     </br>

     U wordt aangeraden u het hulpprogramma uitvoeren in de modus wat als en het resulterende logboekbestand controleren voordat u het hulpprogramma met de schakeloptie/DELETE uitvoeren.  

Wanneer de Inhoudsbibliotheek hulpprogramma wordt uitgevoerd in de modus, maakt deze automatisch een logboek met een naam met de modus voor die het hulpprogramma wordt uitgevoerd in naam van distributiepunt, datum en tijd van de bewerking. Het logboekbestand wordt automatisch geopend wanneer het hulpprogramma is voltooid. Standaard wordt dit logboek geschreven naar de gebruikers **temp** map op de computer waarop u het hulpprogramma., maar u kunt een opdrachtregelparameter het logboekbestand omleiden naar een andere locatie, met inbegrip van een netwerkshare.   


### <a name="run-the-tool"></a>Het hulpprogramma uitvoeren
Het hulpprogramma uitvoeren:
1. Open een beheeropdrachtprompt naar een map met **ContentLibraryCleanup.exe**.  
2. Voer vervolgens een opdrachtregel te gebruiken dat de vereiste opdrachtregelparameters en schakelopties die u wilt gebruiken.

**Bekende probleem** wanneer het hulpprogramma wordt uitgevoerd, een fout als volgt kan worden geretourneerd als een pakket of de implementatie is mislukt of uitgevoerd wordt:
-  *System.InvalidOperationException: Deze Inhoudsbibliotheek kan niet worden opgeruimd nu omdat pakket <packageID> is niet volledig geïnstalleerd.*

**Tijdelijke oplossing:** Geen. Het hulpprogramma kan geen betrouwbare zwevende bestanden identificeren wanneer inhoud uitgevoerd wordt of is niet is geïmplementeerd. Daarom kunt het hulpprogramma u niet opschonen inhoud totdat dit probleem opgelost is.



### <a name="command-line-switches"></a>Opdrachtregelparameters  
De volgende opdrachtregelopties kunnen worden gebruikt in een willekeurige volgorde.   

|Switch|Details|
|---------|-------|
|**/ Delete**  |**Optionele** </br> Gebruik deze switch als u inhoud wilt verwijderen uit het distributiepunt. U wordt gevraagd voordat inhoud wordt verwijderd. </br></br> Wanneer deze schakeloptie niet wordt gebruikt, registreert het hulpprogramma resultaten over welke inhoud wordt verwijderd, maar wordt de inhoud niet verwijderd uit het distributiepunt. </br></br> Voorbeeld: ***/ Delete ContentLibraryCleanup.exe /dp server1.contoso.com*** |
| **/q**       |**Optionele** </br> Het hulpprogramma uitvoeren in stille modus waarbij alle prompts onderdrukken (zoals prompts wanneer u inhoud wilt verwijderen) en niet automatisch het logboekbestand openen. </br></br> Voorbeeld: ***ContentLibraryCleanup.exe /q /dp server1.contoso.com*** |
| **/dp &lt;distribution point FQDN >**  | **Vereist** </br> Geef de volledig gekwalificeerde domeinnaam (FQDN) van het distributiepunt dat u wilt reinigen. </br></br> Voorbeeld:  ***ContentLibraryCleanup.exe /dp server1.contoso.com***|
| **/PS &lt;primaire site FQDN-naam >**       | **Optionele** bij het opschonen van de inhoud van een distributiepunt op een primaire site.</br>**Vereist** bij het opschonen van de inhoud van een distributiepunt op een secundaire site. </br></br> Geef dat de FQDN-naam van de primaire site het distributiepunt naar of van de bovenliggende primaire bovenliggende behoort, wanneer het distributiepunt zich op een secundaire site. </br></br> Voorbeeld: ***ContentLibraryCleanup.exe /dp server1.contoso.com /ps siteserver1.contoso.com*** |
| **/sc &lt;primaire sitecode >**  | **Optionele** bij het opschonen van de inhoud van een distributiepunt op een primaire site.</br>**Vereist** bij het opschonen van de inhoud van een distributiepunt op een secundaire site. </br></br> Geef de sitecode van de primaire site die deel uitmaakt van het distributiepunt naar of van de bovenliggende primaire site wanneer het distributiepunt zich op een secundaire site.</br></br> Voorbeeld: ***ContentLibraryCleanup.exe /dp server1.contoso.com /sc ABC*** |
| **/ log<log file directory>**       |**Optionele** </br> Geef een map wilt vestigen logboekbestanden in. Dit kan een lokaal station of een netwerkshare.</br></br> Wanneer deze schakeloptie niet wordt gebruikt, worden logboekbestanden automatisch geplaatst in de map temp van gebruikers.</br></br> Voorbeeld van een lokale schijf: ***ContentLibraryCleanup.exe /dp server1.contoso.com/log C:\Users\Administrator\Desktop*** </br></br>Voorbeeld van een netwerkshare: ***/ Log ContentLibraryCleanup.exe /dp server1.contoso.com \\ &lt;delen >\&lt; map >***|


## <a name="improvements-for-in-console-search"></a>Verbeteringen voor de zoekopdracht console
Op basis van gebruiker stem feedback, hebben we de volgende verbeteringen toegevoegd aan de console zoeken:
 - **Pad naar het object:**  
  Veel objecten ondersteunen nu een nieuwe kolom genaamd **objectpad**.  Als u zoeken en deze kolom in uw resultaten weergeven weglaat, kunt u het pad naar elk object weergeven. Als u een zoekopdracht voor apps uitvoeren in het knooppunt toepassingen en zoekt zijn onderliggende knooppunten, bijvoorbeeld de *objectpad* kolom in het resultatenvenster ziet u het pad naar elk object dat wordt geretourneerd.   

- **Behoud van zoektekst:**  
  Wanneer u tekst in het tekstvak Zoeken invoeren en vervolgens schakelen tussen het doorzoeken van een onderliggende knooppunt en het huidige knooppunt, wordt de tekst die u hebt getypt nu blijven behouden en beschikbaar blijven voor een nieuwe zoekopdracht zonder te hoeven typen.

- **Behoud van uw keuze om te zoeken naar onderliggende knooppunten:**  
 De optie die u voor beide zoeken selecteert de *huidige knooppunt* of *alle onderliggende knooppunten* nu zich blijft voordoen wanneer u het knooppunt dat u in werkt wijzigt.   Dit nieuwe gedrag betekent dat u hoeft niet voortdurend de beschikking opnieuw instellen als u de console verplaatsen.  Wanneer u de console opent is de optie om te zoeken alleen het huidige knooppunt.

## <a name="prevent-installation-of-an-application-if-a-specified-program-is-running"></a>Voorkomen dat de installatie van een toepassing als een opgegeven programma wordt uitgevoerd.
U kunt nu een lijst met uitvoerbare bestanden (met de extensie .exe) configureren in de eigenschappen van het implementatietype dat als wordt uitgevoerd, wordt de installatie van een toepassing geblokkeerd. Nadat de installatie wordt uitgevoerd, zichtbaar voor gebruikers een dialoogvenster te sluiten van de processen die installatie wordt geblokkeerd.

### <a name="try-it-out"></a>Probeer het nu
Een lijst met uitvoerbare bestanden configureren
1.    Kies op de eigenschappenpagina van eender welk implementatietype de **installatieprogramma afhandeling** tabblad.
2.    Klik op **toevoegen**, zodat er meer uitvoerbare bestanden toevoegen aan de lijst (bijvoorbeeld **Edge.exe**)
3.    Klik op **OK** implementatie type in het dialoogvenster Eigenschappen te sluiten.

Nu als u deze toepassing op een gebruiker of een apparaat en een van de uitvoerbare bestanden die u hebt toegevoegd wordt uitgevoerd implementeert, ziet de gebruiker een dialoogvenster met het Software Center melden dat de installatie is mislukt omdat een toepassing wordt uitgevoerd.

## <a name="new-windows-hello-for-business-notification-for-end-users"></a>Nieuwe Windows Hello voor zakelijke kennisgeving voor eindgebruikers

Een nieuwe Windows 10-melding informeert gebruikers dat ze extra acties voltooid Windows Hello voor de installatie van Business (bijvoorbeeld, het instellen van een PINCODE) moeten uitvoeren.

## <a name="windows-store-for-business-support-in-configuration-manager"></a>Windows Store voor Business-ondersteuning in Configuration Manager

U kunt nu implementeren online gelicentieerde apps met een implementatiedoel van **beschikbaar** de Configuration Manager-client uitvoert vanuit de Windows Store voor bedrijven om pc's.
Zie voor meer informatie [apps beheren vanuit de Windows Store voor bedrijven met System Center Configuration Manager](https://docs.microsoft.com/sccm/apps/deploy-use/manage-apps-from-the-windows-store-for-business).

Ondersteuning voor deze functie is alleen beschikbaar voor Windows 10 RS2 preview build uitgevoerd pc's.

## <a name="return-to-previous-page-when-a-task-sequence-fails"></a>Teruggaan naar vorige pagina wanneer een takenreeks mislukt
U kunt nu teruggaan naar vorige pagina wanneer u een takenreeks uitvoert en er een fout is opgetreden is. Vóór deze release moest u de takenreeks wordt opnieuw gestart als er een fout opgetreden is. U kunt bijvoorbeeld de **vorige** knop in de volgende scenario's:

- Wanneer een computer in Windows PE is opgestart, wordt het dialoogvenster taak volgorde bootstrap mogelijk weergegeven voordat de takenreeks beschikbaar is. Wanneer u in dit scenario op Volgende klikt, wordt de laatste pagina van de takenreeks weergegeven met een bericht dat er geen takenreeksen beschikbaar zijn. Nu kunt u **vorige** Zoek opnieuw voor de beschikbare takenreeksen. U kunt dit proces herhalen totdat de takenreeks beschikbaar is.
- Wanneer u een takenreeks uitvoert, maar afhankelijke inhoudspakketten nog niet beschikbaar zijn op distributiepunten zijn, mislukt de takenreeks. U kunt nu de ontbrekende inhoud distribueren (als deze nog niet is gedistribueerd) of wacht totdat de inhoud moet beschikbaar zijn op distributiepunten en klik op **vorige** taak volgorde zoeken opnieuw naar de inhoud hebben.

## <a name="express-installation-files-support-for-windows-10-updates"></a>Snelle installatie bestanden ondersteuning voor Windows 10-updates
We hebben toegevoegd bestanden voor snelle installatie in Configuration Manager ondersteuning voor Windows 10-updates. Wanneer u een ondersteunde versie van Windows 10, kunt u nu Configuration Manager-instellingen gebruiken voor het downloaden van alleen de verschillen tussen de huidige maand Windows 10 cumulatieve Update en de vorige maand update. De volledige Windows 10 cumulatieve Update (met inbegrip van alle updates van vorige maanden) zijn momenteel in Configuration Manager huidige vertakking gedownload elke maand. Gebruik van bestanden voor snelle installatie zorgt voor downloads kleiner en sneller installatietijden op clients.

> [!IMPORTANT]
> Tijdens de instellingen voor de ondersteuning van het gebruik van bestanden voor snelle installatie beschikbaar is in Configuration Manager deze functionaliteit wordt alleen ondersteund in Windows 10 versie 1607 met een Windows Update Agent-update bevat met de updates zijn uitgebracht op 10 januari 2017 (Patch-dinsdag). Zie voor meer informatie over deze updates [artikel 3213986](https://support.microsoft.com/help/4009938/january-10-2017-kb3213986-os-build-14393-693). U kunt profiteren van bestanden voor snelle installatie wanneer de volgende set updates zijn uitgebracht op 14 februari 2017. Windows 10 1607 zonder de update versie en eerdere versies bieden geen ondersteuning voor bestanden voor snelle installatie.


### <a name="to-enable-the-download-of-express-installation-files-for-windows-10-updates-on-the-server"></a>Het downloaden van bestanden voor snelle installatie voor Windows 10-updates op de server inschakelen
Om te beginnen met het synchroniseren van de metagegevens voor Windows 10-bestanden voor snelle installatie, moet u ze inschakelen in de eigenschappen van Software-updatepunt.
1.    Navigeer in de Configuration Manager-console naar **beheer** > **siteconfiguratie** > **Sites**.
2.    Selecteer de centrale beheersite of de zelfstandige primaire site.
3.    Klik op het tabblad **Start** in de groep **Instellingen** op **Sitecomponenten configureren**en klik op **Software-updatepunt**. Op de **updatebestanden** tabblad **volledige bestanden voor alle goedgekeurde updates downloaden en installatiebestanden express voor Windows 10**.

### <a name="to-enable-support-for-clients-to-download-and-install-express-installation-files"></a>Ondersteuning voor clients downloaden en installeren van de bestanden voor snelle installatie inschakelen
Snelle installatie bestanden als ondersteuning wilt inschakelen op clients, moet u de bestanden voor snelle installatie op clients in de sectie Software-Updates van clientinstellingen inschakelen. Hiermee maakt u een nieuwe HTTP-listener naar aanvragen luistert voor het downloaden van bestanden voor snelle installatie op de poort die u opgeeft. Als u clientinstellingen voor deze functionaliteit op de client implementeert, wordt geprobeerd de verschillen tussen de huidige maand Windows 10 cumulatieve Update en de vorige maand update downloaden (clients moeten een versie van Windows 10 dat express ondersteunt installatiebestanden uitvoeren).
1.    Ondersteuning voor bestanden voor snelle installatie in de eigenschappen van onderdeel Software-updatepunt (vorige procedure) inschakelen.
2.    Navigeer in de Configuration Manager-console naar **beheer** > **clientinstellingen**.
3.    Selecteer de juiste clientinstellingen vervolgens op de **Start** tabblad **eigenschappen**.
4.    Selecteer de **Software-Updates** pagina, configureert u **Ja** voor de **installatie van de Express-Updates op clients inschakelen** instellen en configureren van de poort die wordt gebruikt door de HTTP-listener op de client voor de **poort wordt gebruikt om inhoud te downloaden voor Updates Express** instelling.


## <a name="odata-endpoint-data-access"></a>Toegang tot de gegevens van de OData-eindpunt

 Configuration Manager biedt nu een RESTful OData-eindpunt voor toegang tot gegevens van Configuration Manager. Het eindpunt is compatibel met Odata-versie 4, waarmee de hulpprogramma's zoals Excel en Power BI gemakkelijk toegang krijgt tot Configuration Manager-gegevens via een enkelvoudig eindpunt. Technische Preview 1612 ondersteunt alleen lezen-toegang tot objecten in Configuration Manager.  

Gegevens die momenteel beschikbaar is in de [WMI-Provider van Configuration Manager](/sccm/develop/reference/configuration-manager-reference) is nu ook toegankelijk zijn met het nieuwe RESTful OData-eindpunt. De entiteit sets weergegeven door de OData-eindpunt kunnen u dezelfde gegevens die u kunt een query met de WMI-provider inventariseren.

### <a name="try-it-out"></a>Probeer het nu

Voordat u de OData-eindpunt gebruiken kunt, moet u het inschakelen voor de site.

1.  Ga naar **beheer** > **Site-configuratie** > **Sites**.
2.  Selecteer de primaire site en klik op **eigenschappen**.
3.  Klik op het tabblad Algemeen van het eigenschappenblad voor de primaire site **eindpunt voor de REST inschakelen voor alle providers op deze site**, en klik vervolgens op **OK**.

In uw favoriete OData-query-viewer kunt u query's is vergelijkbaar met de volgende voorbeelden om terug te keren verscheidene objecten in Configuration Manager:

| Doel | De OData-query |
|---|---|
| Alle verzamelingen ophalen | `http://localhost/CMRestProvider/Collection` |
| Een verzameling ophalen | `http://localhost/CMRestProvider/Collection('SMS00001')`
| De top 100 apparaten in de verzameling ophalen | `http://localhost/CMRestProvider/Collection('SMS00001')/Device?$top=100` |
| Ophalen van een apparaat met een bron-ID in de verzameling | `http://localhost/CMRestProvider/Collection('SMS00001')/Device(16777573)` |
| Besturingssysteem van het apparaat in de verzameling ophalen | `http://localhost/CMRestProvider/Collection('SMS00001')/Device(16777573)/OPERATING_SYSTEM` |
| Gebruikers krijgen in de verzameling | `http://localhost/CMRestProvider/Collection('SMS00001')/User` |

> [!NOTE]
> De voorbeeld-query's weergegeven in de tabel *localhost* naam als de host in de URL en kan worden gebruikt op de computer met de SMS-Provider. Als u uw query's vanaf een andere computer uitvoert, vervangt u localhost met de FQDN-naam van de server waarop de SMS-Provider geïnstalleerd.

## <a name="azure-active-directory-onboarding"></a>Azure Active Directory voorbereiden

Voorbereiden op Azure Active Directory (AD) maakt een verbinding tussen Configuration Manager en Azure Active Directory moet worden gebruikt door andere cloudservices. Dit kan op dit moment worden gebruikt voor het maken van de verbinding die nodig zijn voor de Cloud Management Gateway.

Deze taak met een Azure-beheerder uitvoeren als u Azure-beheerdersreferenties moet.

#### <a name="to-create-the-connection"></a>Het om verbinding te maken:

2. In de **beheer** werkruimte kiezen **Cloudservices** > **Azure Active Directory** > **Azure Active Directory toevoegen**.
2. Kies **aanmelden** het verbinding maken met Azure AD.

#### <a name="configuration-manager-client-requirements"></a>Vereisten voor de client Configuration Manager

Er zijn verschillende vereisten voor het inschakelen van het maken van het gebruikersbeleid opneemt in de Cloud Management Gateway.

- Het Azure AD-voorbereidingsproces moet zijn voltooid en de client in eerste instantie worden verbonden met het bedrijfsnetwerk ophalen van gegevens voor de verbinding heeft.
- Clients moeten beide domein (geregistreerd in Active Directory) en cloud-domein (geregistreerd in Azure AD).
- U moet uitvoeren [Active Directory User Discovery](/sccm/core/servers/deploy/configure/about-discovery-methods#active-directory-user-discovery#active-directory-user-discovery).
- U moet de Configuration Manager-client zodat gebruiker beleidsaanvragen via het Internet wijzigen en implementeren van de wijziging aan de client. Omdat deze wijziging naar de client plaats vindt *op het clientapparaat*, het kan worden geïmplementeerd via de Cloud Management Gateway Hoewel u de wijzigingen in de configuratie die nodig zijn voor gebruikersbeleid nog niet voltooid.
- Uw beheerpunt moet worden geconfigureerd om HTTPS te gebruiken voor het beveiligen van het token op het netwerk en moet .net 4.5 geïnstalleerd hebben.

Nadat u deze wijzigingen in de configuratie, kunt u een beleid maken en clients overschakelen naar het Internet voor het testen van het beleid. Beleidsaanvragen van gebruikers via de Cloud Management Gateway zal worden geverifieerd met Azure AD-token gebaseerde verificatie.

## <a name="change-to-configuring-multi-factor-authentication-for-device-enrollment"></a>Wijzig in configureren multi-factor authentication voor apparaatinschrijving

Nu dat u multi-factor authentication (MFA) voor de inschrijving in de Azure-portal apparaten instellen kunt, is de optie MFA verwijderd uit de Configuration Manager-console. U vindt meer informatie over het instellen van MFA voor inschrijving [in dit onderwerp voor Microsoft Intune](https://docs.microsoft.com/en-us/intune/deploy-use/multi-factor-authentication-azure-active-directory).

