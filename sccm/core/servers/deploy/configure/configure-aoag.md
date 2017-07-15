---
title: Beschikbaarheidsgroepen configureren | Microsoft Docs
description: Instellen en beheren van SQL Server altijd op beschikbaarheidsgroepen met SCCM wordt gebruikt.
ms.custom: na
ms.date: 5/26/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: get-started-article
ms.assetid: 7e4ec207-bb49-401f-af1b-dd705ecb465d
caps.latest.revision: 0
author: Brenduns
ms.author: brenduns
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: dc221ddf547c43ab1f25ff83c3c9bb603297ece6
ms.openlocfilehash: 138834b6cc64332202256961ad1d2f5ab6d176db
ms.contentlocale: nl-nl
ms.lasthandoff: 06/01/2017


---
# <a name="configure-sql-server-always-on-availability-groups-for-configuration-manager"></a>SQL Server AlwaysOn-beschikbaarheidsgroepen configureren voor Configuration Manager

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*

Gebruik de informatie in dit onderwerp om te configureren en beheren van de beschikbaarheidsgroepen die u met Configuration Manager gebruikt.

Voordat u begint:  
-   Vertrouwd zijn met de gegevens van [voorbereiden op het gebruik van SQL Server Always On availability groups met Configuration Manager](/sccm/core/servers/deploy/configure/sql-server-alwayson-for-a-highly-available-site-database).
-   Vertrouwd zijn met SQL Server-documentatie die betrekking heeft op het gebruik van beschikbaarheidsgroepen en de bijbehorende procedures die nodig zijn voor het voltooien van de volgende scenario's.

> [!TIP]  
>  Koppelingen in dit onderwerp voor SQL Server gaat u naar de inhoud voor SQL Server 2016. Als u die versie van SQL Server niet gebruikt, raadpleegt u de documentatie voor de versie die u gebruikt.

## <a name="create-and-configure-an-availability-group"></a>Maken en configureren van een beschikbaarheidsgroep
Gebruik de volgende procedure voor het maken van een beschikbaarheidsgroep en verplaatst u een kopie van de sitedatabase naar die beschikbaarheidsgroep.

Voor deze procedure, moet het account dat u gebruikt:
-   Een lid van de **lokale beheerders** groeperen op elke computer die zich in de beschikbaarheidsgroep.
-   Een **sysadmin** op elk exemplaar van SQL Server die als host voor de sitedatabase fungeert.

### <a name="to-create-and-configure-an-availability-group-for-configuration-manager"></a>Maken en een beschikbaarheidsgroep configureren voor Configuration Manager  
1.    Gebruik de volgende opdracht om te stoppen van de Configuration Manager-site: **Preinst.exe /stopsite**. Zie voor meer informatie over het gebruik van Preinst.exe [Tool hiërarchie-onderhoud](/sccm/core/servers/manage/hierarchy-maintenance-tool-preinst.exe).

2.    Wijzig het back-upmodel voor de sitedatabase van **EENVOUDIG** in **VOLLEDIG**.
Zie [Het herstelmodel van een database weergeven of wijzigen](/sql/relational-databases/backup-restore/view-or-change-the-recovery-model-of-a-database-sql-server) in de documentatie van SQL Server. (Beschikbaarheidsgroepen ondersteunen alleen VOLLEDIG).

3.    SQL Server gebruiken voor het maken van een volledige back-up van uw sitedatabase en voer een van de volgende, afhankelijk van of de server die als host fungeert voor de sitedatabase wordt een replicalid van de nieuwe beschikbaarheidsgroep of niet:
    -   **Lid van de beschikbaarheidsgroep zijn:**  
        Als u deze server als lid van de eerste primaire replica van de beschikbaarheidsgroep gebruikt, hoeft u niet om te herstellen van een kopie van de sitedatabase naar deze of een andere server in de groep. De database is al aanwezig op de primaire replica en SQL Server de database wordt gerepliceerd naar de secundaire replica's tijdens een volgende stap.  

      -    **Is geen lid is van de beschikbaarheidsgroep:**   
    U moet een kopie van de sitedatabase herstellen met de server die als host voor de primaire replica van de groep fungeert.

    Zie voor meer informatie over het uitvoeren van deze stap [maken van een volledige databaseback-up](/sql/relational-databases/backup-restore/create-a-full-database-backup-sql-server) en [herstellen van een databaseback-up met behulp van SSMS](/sql/relational-databases/backup-restore/restore-a-database-backup-using-ssms)in de documentatie van SQL Server.

4.    Op de server die als host voor de eerste primaire replica van de groep fungeert, gebruikt u de [nieuwe Wizard beschikbaarheidsgroep](/sql/database-engine/availability-groups/windows/use-the-availability-group-wizard-sql-server-management-studio) voor het maken van de beschikbaarheidsgroep. In de wizard:
      -    Op de **Database selecteren** pagina, selecteert u de database voor u Configuration Manager-site.  

      -    Configureer op de pagina **Replica's opgeven** het volgende:
          -    **Replica's:** Geef de servers die als secundaire replica's host.

          -    **Listener:** Geef de **Listener DNS-naam** als een volledige DNS-naam, zoals  **&lt;Listener_Server >. fabrikam.com**. Dit wordt gebruikt bij het configureren van Configuration Manager moet de database in de beschikbaarheidsgroep te gebruiken.

      -    Selecteer op de pagina **Eerste gegevenssynchronisatie selecteren** de optie **Volledig**. Nadat de wizard de beschikbaarheidsgroep maakt, wordt de wizard Back-up van de primaire database en transactielogboeken logboek en herstel deze op elke server die als host fungeert voor een secundaire replica. (Als u deze stap niet uitvoert, u moet een kopie van de sitedatabase herstellen op elke server die als host fungeert voor een secundaire replica en die database handmatig toevoegen aan de groep.)   

5.    Controleer de configuratie voor elke replica:   
  1.    Zorg ervoor dat de computeraccount van de siteserver is lid van de **lokale beheerders** groeperen op elke computer die lid is van de beschikbaarheidsgroep.  

  2.  Voer de [verificatie script](/sccm/core/servers/deploy/configure/sql-server-alwayson-for-a-highly-available-site-database#prerequisites) uit de vereisten om te bevestigen dat de sitedatabase op elke replica correct is geconfigureerd.

  3.    Als het benodigde configuraties op secundaire replica's instellen, moet u handmatig failover de primaire replica naar de secundaire replica alvorens de omdat u alleen de database van een primaire replica kunt configureren. Zie voor meer informatie [uitvoeren van een geplande handmatige Failover van een beschikbaarheidsgroep](/sql/database-engine/availability-groups/windows/perform-a-planned-manual-failover-of-an-availability-group-sql-server) in de documentatie van SQL Server.

6.    Nadat alle replica's aan de vereisten voldoet, is de beschikbaarheidsgroep is klaar voor gebruik met Configuration Manager.

## <a name="configure-a-site-to-use-the-database-in-the-availability-group"></a>Een site voor het gebruik van de database in de beschikbaarheidsgroep configureren
Nadat u [maken en configureren van de beschikbaarheidsgroep](#create-and-configure-an-availability-group), Configuration Manager-site-onderhoud gebruiken voor het configureren van de site voor het gebruik van de database die wordt gehost door de beschikbaarheidsgroep.

Dit wordt niet ondersteund voor het installeren van een nieuwe site met de database in een beschikbaarheidsgroep. Als u de basislijn 1702 media gebruikt, moet u bijvoorbeeld de site met één exemplaar van SQL Server installeren. Nadat de site is geïnstalleerd, kunt u vervolgens de sitedatabase verplaatsen aan de beschikbaarheidsgroep.

Voor deze procedure, moet het account waarmee u Setup van Configuration Manager uit te voeren:
-   Een lid van de **lokale beheerders** groeperen op elke computer die lid is van de beschikbaarheidsgroep.
-   Een **sysadmin** op elk exemplaar van SQL Server die als host fungeert voor de sitedatabase.

> [!IMPORTANT]
> Wanneer u Microsoft Intune met Configuration Manager in een hybride configuratie gebruikt, activeert de sitedatabase verplaatsen naar of van een beschikbaarheidsgroep een hersynchronisatie aan gegevens met de cloud. Dit kan niet worden vermeden.

### <a name="to-configure-a-site-to-use-the-availability-group"></a>Een site voor het gebruik van de beschikbaarheidsgroep configureren
1.    Voer **Setup van Configuration Manager** van  **&lt;* Configuration Manager site-installatiemap*> \BIN\X64\setup.exe**.

2.    Selecteer op de pagina **Aan de slag** de optie **Siteonderhoud uitvoeren of deze site resetten**en klik op **Volgende**.

3.    Selecteer de optie **SQL Server-configuratie wijzigen** en klik vervolgens op **Volgende**.

4.    Configureer de volgende instellingen opnieuw voor de sitedatabase:
    -   **SQL Server-naam:** Voer de virtuele naam in voor de beschikbaarheidsgroep **listener** dat u bij het maken van de beschikbaarheidsgroep hebt geconfigureerd. De virtuele naam moet een volledige DNS-naam, zoals  **&lt;* endpointServer*>. fabrikam.com**.  

    -   **Exemplaar:** Deze waarde moet leeg zijn om op te geven van het standaardexemplaar voor de *listener* van de beschikbaarheidsgroep. Als de huidige sitedatabase is geïnstalleerd op een benoemd exemplaar, wordt het benoemde exemplaar vermeld en moet worden gewist.

    -   **Database:** Laat de naam zoals deze wordt weergegeven. Dit is de naam van de huidige sitedatabase.

5.    Nadat u de informatie voor de nieuwe locatie van de database hebt opgegeven, voltooit u de installatie volgens uw normale proces en configuraties.



## <a name="add-and-remove-replica-members"></a>Replicatieleden toevoegen en verwijderen  
Wanneer uw sitedatabase wordt gehost in een beschikbaarheidsgroep, gebruik de volgende procedures toevoegen of verwijderen van replicatieleden. Configuration Manager ondersteunt één primair en maximaal twee secundaire knooppunten.

Als u wilt de volgende procedures hebt voltooid, moet het account dat u gebruikt:
-   Een lid van de **lokale beheerders** groeperen op elke computer die lid is van de beschikbaarheidsgroep.
-   Een **sysadmin** op elke SQL-Server die fungeert als host of de sitedatabase zal hosten.


### <a name="to-add-a-new-replica-member"></a>Een nieuw replicalid toevoegen
1.    Voeg de nieuwe server als een secundaire replica toe aan de beschikbaarheidsgroep. Zie [een secundaire Replica toevoegen aan een beschikbaarheidsgroep (SQL Server)](/sql/database-engine/availability-groups/windows/add-a-secondary-replica-to-an-availability-group-sql-server) in de Documentatiebibliotheek van SQL Server.

2.    De Configuration Manager-site stoppen door het uitvoeren van **Preinst.exe stopsite**. Zie [Tool hiërarchie-onderhoud](/sccm/core/servers/manage/hierarchy-maintenance-tool-preinst.exe).

3.    Maak met SQL Server een back-up van de sitedatabase van de primaire replica en herstel deze back-up naar de nieuwe secundaire replicaserver. Zie [maken van een volledige databaseback-up](/sql/relational-databases/backup-restore/create-a-full-database-backup-sql-server) en [herstellen van een databaseback-up met behulp van SSMS](/sql/relational-databases/backup-restore/restore-a-database-backup-using-ssms) in de documentatie van SQL Server.

4.    Configureer de secundaire replica of replica’s. Voer de volgende acties uit voor elke secundaire replica in de beschikbaarheidsgroep:

    1.    Zorg ervoor dat de computeraccount van de siteserver is lid van de **lokale beheerders** groeperen op elke computer die lid is van de beschikbaarheidsgroep.

    2.    Voer de [verificatie script](/sccm/core/servers/deploy/configure/sql-server-alwayson-for-a-highly-available-site-database#prerequisites) uit de vereisten om te bevestigen dat de sitedatabase op elke replica correct is geconfigureerd.

    3.    Als het nodig zijn voor het configureren van de nieuwe replica, handmatige failover uit van de primaire replica naar de nieuwe secundaire replica en breng vervolgens de vereiste instellingen. Zie [Een geplande handmatige failover van een beschikbaarheidsgroep uitvoeren](/sql/database-engine/availability-groups/windows/perform-a-planned-manual-failover-of-an-availability-group-sql-server) in de documentatie van SQL Server.

5.    Start Beheer van siteonderdelen (**sitecomp**) en de **SMS_Executive** -services om de site opnieuw te starten.

### <a name="to-remove-a-replica-member"></a>Een replicalid verwijderen
Gebruik de informatie in deze procedure [een secundaire Replica verwijderen uit een beschikbaarheidsgroep](/sql/database-engine/availability-groups/windows/remove-a-secondary-replica-from-an-availability-group-sql-server) uit de SQL Server-documentatie.

## <a name="stop-using-an-availability-group"></a>Stoppen met het gebruik van een beschikbaarheidsgroep
Voer de volgende procedure uit als u de sitedatabase niet meer wilt hosten in een beschikbaarheidsgroep. Dit omvat de sitedatabase terug verplaatsen naar één exemplaar van SQL Server.

Voor deze procedure, moet het account dat u gebruikt:
-   Een lid van de **lokale beheerders** groeperen op elke computer die lid is van de beschikbaarheidsgroep.
-   Een **sysadmin** op elk exemplaar van SQL Server die als host fungeert voor de sitedatabase.

> [!IMPORTANT]  
> Wanneer u Microsoft Intune met Configuration Manager in een hybride configuratie gebruikt, activeert de sitedatabase verplaatsen naar of van een beschikbaarheidsgroep een hersynchronisatie aan gegevens met de cloud. Dit kan niet worden vermeden.

### <a name="to-move-the-site-database-from-an-availability-group-back-to-a-single-instance-sql-server"></a>De sitedatabase vanuit een beschikbaarheidsgroep terug verplaatsen naar een SQL Server met één exemplaar
1.    De Configuration Manager-site stoppen met de volgende opdracht: **Preinst.exe /stopsite**. Zie voor meer informatie [Tool hiërarchie-onderhoud](/sccm/core/servers/manage/hierarchy-maintenance-tool-preinst.exe).

2.    Maak met behulp van SQL Server een volledige back-up van uw sitedatabase vanaf de primaire replica: Zie [Een volledige databaseback-up maken](/sql/relational-databases/backup-restore/create-a-full-database-backup-sql-server) in de documentatie van SQL Server voor informatie over het uitvoeren van deze stap.

3.    Als de server die de primaire replica voor de beschikbaarheidsgroep het exemplaar van de sitedatabase host wordt, kunt u deze stap overslaan:  

    -   Herstel met SQL Server de back-up van de sitedatabase naar de server die als host voor de sitedatabase moet dienen. Zie [herstellen van een databaseback-up met behulp van SSMS](/sql/relational-databases/backup-restore/restore-a-database-backup-using-ssms) in de documentatie van SQL Server.   <br />  <br />

4.    Op de server die als host fungeert voor de sitedatabase (de primaire replica of de server waar u de sitedatabase hebt hersteld), wijzigt u de back-upmodel voor de sitedatabase van **volledige** naar **eenvoudige**. Zie [Het herstelmodel van een database weergeven of wijzigen](/sql/relational-databases/backup-restore/view-or-change-the-recovery-model-of-a-database-sql-server) in de documentatie van SQL Server.  

5.    Voer **Setup van Configuration Manager** van  **&lt;* Configuration Manager site-installatiemap >*\BIN\X64\setup.exe**.

6.    Selecteer op de pagina **Aan de slag** de optie **Siteonderhoud uitvoeren of deze site resetten**en klik op **Volgende**.  

7.    Selecteer de optie **SQL Server-configuratie wijzigen** en klik vervolgens op **Volgende**.  

8.    Configureer de volgende instellingen opnieuw voor de sitedatabase:
    -   **SQL Server-naam:** Voer de naam van de server die nu als host fungeert voor de sitedatabase.

    -   **Exemplaar:** Geef het benoemde exemplaar dat als host fungeert voor de sitedatabase of laat dit leeg als de database zich op het standaardexemplaar.

    -   **Database:** Laat de naam zoals deze wordt weergegeven. Dit is de naam van de huidige sitedatabase.    

9.    Nadat u de informatie voor de nieuwe locatie van de database hebt opgegeven, voltooit u de installatie volgens uw normale proces en configuraties. Als Setup is voltooid, wordt de site opnieuw opgestart en wordt de nieuwe locatie van de database in gebruik genomen.    

10.    Volg de instructies in [Een beschikbaarheidsgroep verwijderen](/sql/database-engine/availability-groups/windows/remove-an-availability-group-sql-server) in de documentatie van SQL Server om de servers op te schonen die lid waren van de beschikbaarheidsgroep.
