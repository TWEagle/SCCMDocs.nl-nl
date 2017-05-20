---
title: SQL Server AlwaysOn | Microsoft-documenten
ms.custom: na
ms.date: 1/4/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: get-started-article
ms.assetid: 58d52fdc-bd18-494d-9f3b-ccfc13ea3d35
caps.latest.revision: 16
author: Brenduns
ms.author: brenduns
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: dab5da5a4b5dfb3606a8a6bd0c70a0b21923fff9
ms.openlocfilehash: aaaab003ddd22f18160d4be63cfeab3a7e7f6b03
ms.contentlocale: nl-nl
ms.lasthandoff: 05/17/2017


---
# <a name="sql-server-alwayson-for-a-highly-available-site-database-for-system-center-configuration-manager"></a>SQL Server AlwaysOn voor een maximaal beschikbare sitedatabase voor System Center Configuration Manager

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*


 Beginnen met System Center Configuration Manager versie 1602, kunt u SQL Server [AlwaysOn Availability Groups](https://msdn.microsoft.com/library/hh510230\(v=sql.120\).aspx) voor het hosten van de sitedatabase op primaire sites en de centrale beheersite als een oplossing voor hoge beschikbaarheid en herstel na noodgevallen. De beschikbaarheidsgroep kan lokaal of in Microsoft Azure worden gehost.  

 Als u de beschikbaarheidsgroep host met behulp van Microsoft Azure, kunt u de beschikbaarheid van uw sitedatabase verder verhogen met behulp van SQL Server AlwaysOn-beschikbaarheidsgroepen met beschikbaarheidssets van Azure. Zie voor meer informatie over beschikbaarheidssets van Azure [Manage the availability of virtual machines](https://azure.microsoft.com/documentation/articles/virtual-machines-windows-manage-availability/)(De beschikbaarheid van virtuele machines beheren).  

 Configuration Manager ondersteunt die als host fungeert voor de sitedatabase op een SQL-beschikbaarheidsgroep die zich achter een interne of externe Load Balancer. Naast het configureren van firewalluitzonderingen voor elke replica, moet u load balancing-regels voor de volgende poorten toevoegen:
  - SQL via TCP: TCP 1433
  - SQL Server Service Broker: TCP 4022
  - Server Message Block (SMB): TCP 445
  - RPC-eindpunttoewijzer: TCP 135


De volgende scenario's worden ondersteund door beschikbaarheidsgroepen:  

-   U kunt de sitedatabase verplaatsen naar het standaardexemplaar van een beschikbaarheidsgroep  

-   U kunt replicatieleden toevoegen aan of verwijderen uit een beschikbaarheidsgroep die als host fungeert voor een site-database  

-   U kunt de sitedatabase verplaatsen van een beschikbaarheidsgroep naar een standaard of benoemd exemplaar van een zelfstandige SQL Server  

> [!Important]  
> Wanneer u Microsoft Intune met Configuration Manager gebruiken in een hybride-configuratie, de verplaatsing van de sitedatabase van een groep beschikbaarheid triggers en een hersynchronisatie aan gegevens met de cloud. Dit kan niet worden vermeden. 



> [!NOTE]  
>  Voor een juiste configuratie en een juist gebruik van beschikbaarheidsgroepen is het noodzakelijk dat u vertrouwd bent met het configureren van SQL Server en met beschikbaarheidsgroepen van SQL Server. De procedures voor System Center Configuration Manager in dit onderwerp zijn afhankelijk van aanvullende documentatie en procedures in de Documentatiebibliotheek voor SQL Server.  

 **Bekende problemen bij het gebruik van AlwaysOn-beschikbaarheidsgroepen met Configuration Manager:**  

-   **Alle replicaservers vereisen een identiek bestandspad op het moment dat u Configuration Manager instelt om de beschikbaarheidsgroep te gebruiken:**  

    -   Op het moment dat u het installatieprogramma van Configuration Manager voor de omleiding van de site voor het gebruik van de database in een beschikbaarheidsgroep uitvoert, moet elke secundaire replica-server in de groep hebben een bestandspad die identiek is aan het pad dat wordt gebruikt voor het hosten van bestanden van de sitedatabase op de huidige primaire replica. Als secundaire replica's geen identiek pad bevatten, kan Setup de instantie van de beschikbaarheidsgroepen niet toevoegen als de nieuwe locatie voor de sitedatabase.  

         Bovendien moet de lokale SQL Server-serviceaccount op elke secundaire replicaserver de machtiging **Volledig beheer** voor deze map hebben.  

         Op de secundaire replicaservers is dit bestandspad alleen vereist op het moment dat u Setup gebruikt om het database-exemplaar in de beschikbaarheidsgroep op te geven.  Nadat Setup de wijziging om de sitedatabase in de beschikbaarheidsgroep te gebruiken heeft voltooid, kunt u het ongebruikte pad verwijderen van secundaire replicaservers.  

         Denk bijvoorbeeld eens aan het volgende scenario:  

        -   U maakt een beschikbaarheidsgroep die gebruikmaakt van drie SQL-Servers.  

        -   Uw primaire replicaserver is een nieuwe installatie van SQL Server 2014.  Standaard worden de databasebestanden .MDF en .LDF opgeslagen in C:\Program Files\Microsoft SQL Server\MSSQL12.MSSQLSERVER\MSSQL\DATA  

        -   Beide van de secundaire replica-servers zijn bijgewerkt naar SQL Server 2014 uit eerdere versies en het oorspronkelijke pad voor het opslaan van databasebestanden van de te behouden: C:\Program Files\Microsoft SQL Server\MSSQL10. MSSQLSERVER\MSSQL\DATA  

        -   Voordat u probeert de sitedatabase verplaatsen naar deze beschikbaarheidsgroep, op elke secundaire replica-server moet u het volgende pad zelfs als de secundaire replica's niet voor deze locatie gebruikt worden:  C:\Program Files\Microsoft SQL Server\MSSQL12. MSSQLSERVER\MSSQL\DATA (dit is een duplicaat is van het pad dat wordt gebruikt op de primaire replica)  

        -   Vervolgens moet u de SQL Server-serviceaccount op elke secundaire replica volledige toegang verlenen tot de nieuwe locatie op die server  

        -   U kunt nu Configuration Manager Setup geeft u de site op het gebruik van de sitedatabase in de beschikbaarheidsgroep uitgevoerd  

-   **Wanneer Setup wordt uitgevoerd om de sitedatabase om te leiden zodat deze de beschikbaarheidsgroep gebruikt, kunnen er fouten als de volgende worden vastgelegd in het logboekbestand ConfigMgrSetup.log:**  

    -   FOUT: SQL Server-fout: [25000] [3906] [Microsoft] [SQL Server Native Client 11.0] [SQL-Server] is mislukt voor het bijwerken van database 'CM_AAA' omdat de database alleen-lezen.   Configuration Manager Setup 1/21/2016 4:54:59 PM  7344 (0x1CB0)  

     Deze fouten worden vastgelegd als Setup probeert databaserollen te verwerken op secundaire replica's van de beschikbaarheidsgroep. Deze fouten kunnen worden genegeerd.
- **SQL-servers die als host extra beschikbaarheidsgroepen fungeren:**

  Voor de installatie van versie 1610, wanneer u een beschikbaarheidsgroep en vervolgens Configuration Manager setup uitvoert of een update voor Configuration Manager installeert, moet elke replica in elke extra beschikbaarheidsgroep op de SQL Server die als host fungeert voor de beschikbaarheidsgroep Configuration Manager de volgende configuraties hebben:
    - **handmatige failover**
    - **elke alleen-lezen verbinding toe te staan**


##  <a name="bkmk_BnR"></a> Wijzigingen voor back-up en herstel als u een SQL Server AlwaysOn-beschikbaarheidsgroep gebruikt  
 **Back-up:**  

 Wanneer een site-database wordt uitgevoerd in een beschikbaarheidsgroep, moet u doorgaan met het ingebouwde **back-upsite** server onderhoudstaak voor back-up maken van algemene Configuration Manager-instellingen en bestanden, maar wilt niet gebruiken de. MDF of. LDF-bestanden die door deze back-up gemaakt. Neem in plaats daarvan in de planning op dat directe back-ups van de sitedatabase worden gemaakt met behulp van SQL Server.  

 Omdat het herstelmodel van de database is ingesteld op volledig, moet u daarnaast in de planning opnemen dat de grootte van het logboek voor databasetransacties wordt bewaakt en onderhouden.  In het volledige herstelmodel worden de transacties niet gehard totdat een volledige back-up van de database of het transactielogboek wordt gemaakt. Een herstelmodel van volledige is een vereiste van het gebruik van de database van de site in een beschikbaarheidsgroep en bij het configureren van de groep voor gebruik met Configuration Manager. Zie [Back-up en herstel van SQL Server-databases](https://msdn.microsoft.com/library/ms187048\(v=sql.120\).aspx) in de documentatie van SQL Server voor meer informatie over back-up en herstel in SQL Server.  

 **Herstel:**  

 Zolang tijdens een herstelbewerking van de site één knooppunt van de beschikbaarheidsgroep blijft werken, kunt u de optie voor siteherstel **Databaseherstel overslaan (deze optie gebruiken als de sitedatabase onbeschadigd is)**gebruiken.  

 Echter, als alle knooppunten van een beschikbaarheidsgroep verloren gegaan, zijn voordat u de site kunt herstellen, moet u opnieuw maken de beschikbaarheidsgroep (System Center Configuration Manager kan niet opnieuw maken of terugzetten van het knooppunt beschikbaarheid).  Nadat de groep opnieuw is gemaakt of vanaf een back-up is hersteld en opnieuw is geconfigureerd, kunt u vervolgens de optie voor siteherstel **Databaseherstel overslaan (deze optie gebruiken als de sitedatabase onbeschadigd is)** gebruiken.  

 Zie [Back-up en herstel voor System Center Configuration Manager](../../../../protect/understand/backup-and-recovery.md) voor meer informatie over back-up en herstel.  

##  <a name="bkmk_create"></a> Een beschikbaarheidsgroep configureren voor gebruik met Configuration Manager  
 Voordat u de volgende procedure, bekend zijn met de SQL Server-procedures die nodig zijn om deze configuratie te voltooien en de volgende details die van toepassing op beschikbaarheidsgroepen configureren voor gebruik met Configuration Manager.  

 **Vereisten voor AlwaysOn-beschikbaarheidsgroepen die u gebruikt met System Center Configuration Manager:**  

-  *Versie*: Elk knooppunt (of replica) in de beschikbaarheidsgroep moet een versie van SQL Server wordt ondersteund door System Center Configuration Manager uitvoeren. Als dit wordt ondersteund door SQL Server, kunnen verschillende knooppunten van de beschikbaarheidsgroep verschillende versies van SQL Server uitgevoerd.   

- *Edition*: U moet een Enterprise-editie van SQL Server gebruiken.  SQL Server 2016 Standard edition introduceert Basic beschikbaarheidsgroepen, die door Configuration Manager worden niet ondersteund.


-   De beschikbaarheidsgroep kan één primaire replica moet hebben en er maximaal twee synchrone secundaire replica's.  

-  Nadat u een database aan een beschikbaarheidsgroep toevoegt, moet u een failover voor de primaire replica naar een secundaire replica maken (waardoor dit de nieuwe primaire replica wordt), en configureert u vervolgens de database met de volgende opties:
    - Trustworthy inschakelen: gelijk aan waar
    - De Service Broker inschakelen: gelijk aan waar
    - De dbowner instellen: gelijk aan SA

    U kunt het volgende script uitvoeren om deze instellingen te configureren, waarbij cm_ABC de naam is van uw sitedatabase:  

    >     Model gebruiken  
    >     ALTER DATABASE cm_ABC SET NEW_BROKER   
    >     ALTER DATABASE cm_ABC SET ENABLE_BROKER  
    >     ALTER DATABASE cm_ABC stellen betrouwbare ON;  
    >     Gebruik cm_ABC  
    >     EXEC sp_changedbowner 'sa'  
    >     Exec sp_configure 'max text repl size (B)', 2147483647 opnieuw configureren



-   De beschikbaarheidsgroep moet ten minste één **beschikbaarheidsgroeplistener**hebben.  De virtuele naam van deze listener wordt gebruikt bij het configureren van Configuration Manager naar de sitedatabase gebruikt in de beschikbaarheidsgroep. Hoewel een beschikbaarheidsgroep meerdere listeners bevatten kan, kunt alleen Configuration Manager maken gebruik van een  

-   Elke primaire en secundaire replica moet:  
    - Worden ingesteld om **elke alleen-lezen verbinding toe te staan**.
    - Het **standaardexemplaar**gebruiken.
    - Worden ingesteld op **handmatige failover**.  

        > [!TIP]  
        >  System Center Configuration Manager ondersteunt het gebruik van de beschikbaarheidsgroepreplica's als ingesteld op automatische Failover. Handmatige Failover moet echter worden ingesteld wanneer u Setup uitvoeren om te gebruiken van de sitedatabase opgeven in de beschikbaarheidsgroep en op het moment u updates installeert voor Configuration Manager (niet alleen updates die betrekking hebben op de sitedatabase).  

  **Beperkingen voor beschikbaarheidsgroepen**
   - Basic-beschikbaarheidsgroepen (die werden geïntroduceerd in SQL Server 2016 Standard edition) worden niet ondersteund. Dit komt doordat eenvoudige beschikbaarheidsgroepen bieden geen ondersteuning voor leestoegang tot secundaire replica's van een vereiste voor gebruik met Configuration Manager. Zie voor meer [Basic Availability Groups (altijd op beschikbaarheidsgroepen)](https://msdn.microsoft.com/en-us/library/mt614935.aspx).

   - Beschikbaarheidsgroepen worden alleen ondersteund voor de sitedatabase en niet voor de software update-database of rapportagedatabase.   
   - Wanneer u een beschikbaarheidsgroep gebruikt, moet u uw rapportagepunt handmatig configureren om gebruik te maken van de huidige primaire replica en niet van de beschikbaarheidsgroeplistener. Als er een failover van de primaire replica optreedt naar een andere replica, moet u het rapportagepunt opnieuw configureren zodat deze de nieuwe primaire replica gebruikt.  
   - Voordat u updates installeert, zoals versie 1606, moet u controleren of de beschikbaarheidsgroep is ingesteld op handmatige failover. Nadat de site is bijgewerkt, kunt u failover terugzetten op automatisch.



 **Vereiste machtigingen om beschikbaarheidsgroepen te configureren en gebruiken:**  

-   Het computeraccount van de siteserver moet lid zijn van de groep **Lokale beheerders** op elke computer die lid is van de beschikbaarheidsgroep.  

#### <a name="to-configure-an-availability-group-to-host-a-site-database"></a>Een beschikbaarheidsgroep configureren om als host te dienen voor een sitedatabase  

1.  De volgende opdracht gebruiken om te stoppen van de Configuration Manager-site:  
     **Preinst.exe /stopsite**  

     Zie [Hierarchy Maintenance Tool (Preinst.exe) voor System Center Configuration Manager](../../../../core/servers/manage/hierarchy-maintenance-tool-preinst.exe.md) voor meer informatie over het gebruik van Preinst.exe.  

2.  Wijzig het back-upmodel voor de sitedatabase van **EENVOUDIG** in **VOLLEDIG**.  

     Zie [Het herstelmodel van een database weergeven of wijzigen](https://msdn.microsoft.com/library/ms189272\(v=sql.120\).aspx) in de documentatie van SQL Server. (Beschikbaarheidsgroepen ondersteunen alleen VOLLEDIG).  

3.  Voer op de server die als host voor de primaire replica van de groep dient, de **wizard Nieuwe beschikbaarheidsgroep** uit om de beschikbaarheidsgroep te maken. In de wizard:  

    -   Op de **Database selecteren** pagina, selecteert u de database voor u Configuration Manager-site  

    -   Configureer op de pagina **Replica's opgeven** het volgende:  

        -   **Replica's**: Geef de servers die als secundaire replica's host  

        -   **Listener**: Geef de **Listener DNS-naam** als een volledige DNS-naam, zoals  **&lt;Listener_Server >. fabrikam.com**. Dit wordt gebruikt bij het configureren van Configuration Manager database worden gebruikt in de beschikbaarheidsgroep.

    -   Selecteer op de pagina **Eerste gegevenssynchronisatie selecteren** de optie **Volledig**. Nadat de wizard de beschikbaarheidsgroep heeft gemaakt, voert de wizard een back-up uit van de primaire database en het transactielogboek en worden deze hersteld op elke server die als host dient voor een secundaire replica. Als u deze stap niet uitvoert, moet u een kopie van de sitedatabase herstellen op elke server die als host dient voor een secundaire replica en die database handmatig toevoegen aan de groep.  

    Zie [De wizard Beschikbaarheidsgroep gebruiken](https://msdn.microsoft.com/library/hh403415\(v=sql.120\).aspx) in de documentatie van SQL Server voor meer informatie.  

4.  Nadat de beschikbaarheidsgroep is geconfigureerd, configureert u de sitedatabase op de primaire replica met de eigenschap **TRUSTWORTHY** (betrouwbaar) en **schakelt u vervolgens CLR-integratie in**. Zie [Database-eigenschap TRUSTWORTHY](https://msdn.microsoft.com/library/ms187861\(v=sql.120\).aspx) en  [CLR-integratie inschakelen](https://msdn.microsoft.com/library/ms131048\(v=sql.120\).aspx) in de documentatie van SQL Server voor meer informatie over het configureren van deze instellingen.  

5.  Voer de volgende acties uit om elke secundaire replica in de beschikbaarheidsgroep te configureren:  

    1.  Voer een handmatige failover uit van de huidige primaire replica naar een secundaire replica. Zie [Een geplande handmatige failover van een beschikbaarheidsgroep uitvoeren](https://msdn.microsoft.com/library/hh231018\(v=sql.120\).aspx) in de documentatie van SQL Server.  

    2.  Configureer de sitedatabase op de nieuwe primaire replica met de eigenschap **TRUSTWORTHY** en **schakel vervolgens CLR-integratie in**.  

6.  Nadat alle replica's worden gepromoveerd tot de primaire replica's en de databases die zijn geconfigureerd, is de beschikbaarheidsgroep is gereed voor gebruik met Configuration Manager.  





##  <a name="bkmk_direct"></a> Een sitedatabase aan een beschikbaarheidsgroep toevoegen  
 U kunt een sitedatabase voor een eerder geïnstalleerde site verplaatsen naar een beschikbaarheidsgroep. U moet eerst de beschikbaarheidsgroep maken en vervolgens de database configureren om te werken in de beschikbaarheidsgroep.  

 Voor deze procedure moet het gebruikersaccount dat Configuration Manager Setup wordt uitgevoerd lid is van de **lokale beheerders** groep op elke computer die lid is van de beschikbaarheidsgroep.  

#### <a name="to-move-a-site-database-to-an-availability-group"></a>Een sitedatabase naar een beschikbaarheidsgroep verplaatsen  

1.  Voer **installatie van Configuration Manager** van  **&lt;installatiemap Configuration Manager-site\>\BIN\X64\setup.exe**.  

2.  Selecteer op de pagina **Aan de slag** de optie **Siteonderhoud uitvoeren of deze site resetten**en klik op **Volgende**.  

3.  Selecteer de optie **SQL Server-configuratie wijzigen** en klik vervolgens op **Volgende**.  

4.  Configureer de volgende instellingen opnieuw voor de sitedatabase:  

    -   **Naam van SQL Server:** Geef de virtuele naam voor de beschikbaarheidsgroep-listener die u hebt geconfigureerd bij het maken van de beschikbaarheidsgroep. De virtuele naam moet een volledige DNS-naam, zoals  **&lt;endpointServer\>. fabrikam.com**  

    -   **Exemplaar:** Deze waarde moet het standaardexemplaar opgeven voor de beschikbaarheidsgroep-listener van de beschikbaarheidsgroep leeg zijn.  Als de huidige sitedatabase is geïnstalleerd op een benoemd exemplaar, wordt het benoemde exemplaar vermeld en moet het worden gewist  

    -   **Database:** Laat u de naam zoals deze wordt weergegeven. Dit is de naam van de huidige sitedatabase.  

5.  Nadat u de informatie voor de nieuwe locatie van de database hebt opgegeven, voltooit u de installatie volgens uw normale proces en configuraties.  

##  <a name="bkmk_change"></a> Leden toevoegen aan of verwijderen uit een actieve beschikbaarheidsgroep  
 U kunt replicatielid van een verwijderen of een extra replica-lid (niet langer zijn dan één primaire en twee secundaire knooppunten) toevoegen nadat Configuration Manager maakt gebruik van een sitedatabase die in een beschikbaarheidsgroep worden gehost.  

#### <a name="to-add-a-new-replica-member"></a>Een nieuw replicalid toevoegen  

1.  Voeg de nieuwe server als een secundaire replica toe aan de beschikbaarheidsgroep. Zie  [Een secundaire replica toevoegen aan een beschikbaarheidsgroep (SQL Server)](https://msdn.microsoft.com/library/hh213247\(v=sql.120\).aspx)in de documentatiebibliotheek van SQL Server.  

2.  De Configuration Manager-site stoppen door het uitvoeren van **Preinst.exe/stopsite** Zie [Hiërarchieonderhoud-hulpprogramma (Preinst.exe) voor System Center Configuration Manager](../../../../core/servers/manage/hierarchy-maintenance-tool-preinst.exe.md).  

3.  Configureer de secundaire replica of replica’s. Voer de volgende acties uit voor elke secundaire replica in de beschikbaarheidsgroep:  

    1.  Voer een handmatige failover uit van de huidige primaire replica naar de nieuwe secundaire replica. Zie [Een geplande handmatige failover van een beschikbaarheidsgroep uitvoeren](https://msdn.microsoft.com/library/hh231018\(v=sql.120\).aspx) in de documentatie van SQL Server.  

    2.  Configureer de database op de nieuwe server als betrouwbaar (Trustworthy) en schakel CLR-integratie in. Zie [Database-eigenschap TRUSTWORTHY](https://msdn.microsoft.com/library/ms187861\(v=sql.120\).aspx) en  [CLR-integratie inschakelen](https://msdn.microsoft.com/library/ms131048\(v=sql.120\).aspx)in de documentatie van SQL Server.  

4.  Start Beheer van siteonderdelen (**sitecomp**) en de **SMS_Executive** -services om de site opnieuw te starten.  

#### <a name="to-remove-a-replica-member-from-the-availability-group"></a>Een replicalid verwijderen uit de beschikbaarheidsgroep  

-   Ga te werk volgens de informatie in [Een secundaire replica uit een beschikbaarheidsgroep verwijderen](https://msdn.microsoft.com/library/hh213149\(v=sql.120\).aspx) uit de SQL Server-documentatie.  

##  <a name="bkmk_remove"></a> De sitedatabase vanuit een beschikbaarheidsgroep terug verplaatsen naar een SQL Server met één exemplaar  
 Voer de volgende procedure uit als u de sitedatabase niet meer wilt hosten in een beschikbaarheidsgroep.  

#### <a name="to-move-the-site-database-from-an-availability-group-back-to-a-single-instance-sql-server"></a>De sitedatabase vanuit een beschikbaarheidsgroep terug verplaatsen naar een SQL Server met één exemplaar  

1.  De Configuration Manager-site stoppen met de volgende opdracht:  
     **Preinst.exe /stopsite**.  Zie [Hierarchy Maintenance Tool (Preinst.exe) voor System Center Configuration Manager](../../../../core/servers/manage/hierarchy-maintenance-tool-preinst.exe.md) voor meer informatie.  

2.  Maak met behulp van SQL Server een volledige back-up van uw sitedatabase vanaf de primaire replica: Zie [Een volledige databaseback-up maken](https://msdn.microsoft.com/library/ms187510\(v=sql.120\).aspx) in de documentatie van SQL Server voor informatie over het uitvoeren van deze stap.  

3.  Als de server die als host dient voor de primaire replica voor de beschikbaarheidsgroep vanaf nu als host dient voor het enkele exemplaar van de sitedatabase, slaat u de volgende stap over:  

    -   Herstel met SQL Server de back-up van de sitedatabase naar de server die als host voor de sitedatabase moet dienen.  Zie [Een databaseback-up herstellen (SQL Server Management Studio)](https://msdn.microsoft.com/library/ms177429\(v=sql.120\).aspx) in de documentatie van SQL Server.  

4.  Wijzig op de herstelde sitedatabase het back-upmodel voor de sitedatabase van **VOLLEDIG** in **EENVOUDIG**.  Zie [Het herstelmodel van een database weergeven of wijzigen](https://msdn.microsoft.com/library/ms189272\(v=sql.120\).aspx) in de documentatie van SQL Server.  

5.  Voer **installatie van Configuration Manager** van  **&lt;installatiemap Configuration Manager-site\>\BIN\X64\setup.exe**.  

6.  Selecteer op de pagina **Aan de slag** de optie **Siteonderhoud uitvoeren of deze site resetten**en klik op **Volgende**.  

7.  Selecteer de optie **SQL Server-configuratie wijzigen** en klik vervolgens op **Volgende**.  

8.  Configureer de volgende instellingen opnieuw voor de sitedatabase:  

    -   **Naam van SQL Server:** Voer de naam van de server die nu als host fungeert voor de sitedatabase.  

    -   **Exemplaar:** Geef het benoemde exemplaar dat als host fungeert voor de sitedatabase of laat dit leeg als de database zich op het standaardexemplaar.  

    -   **Database:** Laat u de naam zoals deze wordt weergegeven. Dit is de naam van de huidige sitedatabase.  

9. Nadat u de informatie voor de nieuwe locatie van de database hebt opgegeven, voltooit u de installatie volgens uw normale proces en configuraties. Als Setup is voltooid, wordt de site opnieuw opgestart en wordt de nieuwe locatie van de database in gebruik genomen.  

10. Volg de instructies in [Een beschikbaarheidsgroep verwijderen](https://msdn.microsoft.com/library/ff878113\(v=sql.120\).aspx) in de documentatie van SQL Server om de servers op te schonen die lid waren van de beschikbaarheidsgroep.

