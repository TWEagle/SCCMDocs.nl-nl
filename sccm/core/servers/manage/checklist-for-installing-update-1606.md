---
title: Controlelijst voor 1606
titleSuffix: Configuration Manager
description: Meer informatie over acties moet uitvoeren voordat het bijwerken van System Center Configuration Manager versie 1511 of 1602 naar versie 1606.
ms.custom: na
ms.date: 6/6/2017
ms.reviewer: na
ms.suite: na
ms.prod: configuration-manager
ms.technology: configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 75652cd2-a95a-46c5-91c1-6d43fc8e787e
caps.latest.revision: "7"
author: mestew
ms.author: mstewart
manager: angrobe
ms.openlocfilehash: ce41852584f11d881c24c201867e13124595eba8
ms.sourcegitcommit: 2867fd119256ec670fc5ae65cdc8a80d39f9b4d4
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/20/2017
---
# <a name="checklist-for-installing-update-1606-for-system-center-configuration-manager"></a>Controlelijst voor het installeren van update 1606 voor System Center Configuration Manager

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*

Versie 1606 voor de huidige vertakking van System Center Configuration Manager is een update die u gebruiken kunt om bij te werken van versie 1511 of 1602.

Voordat u versie 1606 installeert als een update, Controleer de volgende informatie en Controlelijst voor acties moet uitvoeren voordat u de update start.

Zie voor meer informatie over basislijnversies [basislijn- en updateversies](../../../core/servers/manage/updates.md#bkmk_Baselines) in [Updates voor System Center Configuration Manager](../../../core/servers/manage/updates.md).

 ## <a name="about-installing-update-1606"></a>Over het installeren van update 1606

Als een *bijwerken*, 1606 kan alleen worden geïnstalleerd op het hoogste niveau van uw hiërarchie. Dit betekent dat u de installatie starten vanuit uw centrale beheersite als er een of vanuit uw zelfstandige primaire site.  

-   Onderliggende primaire sites de update automatisch geïnstalleerd als de centrale beheersite is voltooid met het installeren van de update. U kunt servicewindows om te bepalen wanneer een site updates installeert. Voorafgaand aan versie 1606, werden servicewindows onderhoudsvensters genoemd. Zie voor meer informatie [servicewindows voor siteservers Service](/sccm/core/servers/manage/service-windows).  

-   U moet secundaire sites uit binnen de Configuration Manager-console handmatig bijwerken nadat de primaire bovenliggende site is voltooid met het installeren van de update. Het automatisch bijwerken van secundaire siteservers wordt niet ondersteund.  

Wanneer de siteserver wordt geïnstalleerd voor de update, sitesysteemrollen die zijn geïnstalleerd op de siteserver en toepassingen die zijn geïnstalleerd op externe computers automatisch bijgewerkt. Daarom voordat u de update installeert, zorg dat elke sitesysteemserver voldoet aan de nieuwe vereisten voor bewerkingen met de nieuwe versie van de update.  

De eerste keer dat u een Configuration Manager-console gebruikt nadat de update is geïnstalleerd, wordt u gevraagd om bij te werken die console.  Om dit te doen, moet u setup van Configuration Manager uitvoeren op de computer die als host fungeert voor de console en kies vervolgens de optie de console bij te werken. U kunt installeren van de update naar de console beter niet uitstellen.

 **Bekende problemen voor deze update**   
  De volgende problemen van toepassing wanneer u de status van de installatie van de update pack weergeven:
  - Bij het bijwerken van versie 1602 naar 1606 de stap **nettolading van het updatepakket uitpakken** een Status weer van **niet gestart**, zelfs als het downloaden is voltooid.
  - Bij het bijwerken van versie 1511 naar 1606, een aantal stappen ziet de status van **voltooid** maar wordt niet weergegeven voor een waarde voor **tijd van laatste Update**.


## <a name="checklist"></a>Controlelijst  

 **Zorg ervoor dat alle sites een ondersteunde versie van System Center Configuration Manager wordt uitgevoerd:**  Voordat u de installatie van update 1606, elke siteserver in de hiërarchie dezelfde versie van System Center Configuration Manager moet uitvoeren: eender welke versie 1511 of 1602.

 **Bekijk Microsoft.NET versies hebt geïnstalleerd op sitesysteemservers:** Wanneer een site update 1606 is geïnstalleerd, installeert Configuration Manager automatisch .NET Framework 4.5.2 op elke computer die als host fungeert voor een van de volgende sitesysteemrollen (als .NET Framework 4.5 of hoger nog niet is geïnstalleerd):  

-   Proxypunt voor inschrijving  

-   Inschrijvingspunt  

-   Beheerpunt  

-   Serviceverbindingspunt  

Deze installatie kunt u de sitesysteemserver in een opnieuw opstarten in behandeling zijnde status en het rapport fouten in de viewer voor Configuration Manager component status plaatsen. Bovendien kunnen .NET-toepassingen op de server mogelijk willekeurig mislukken totdat de server opnieuw is gestart.  

 Zie voor meer informatie [Site en site-systeemvereisten](../../../core/plan-design/configs/site-and-site-system-prerequisites.md).  

 **Bekijk de site en hiërarchiestatus en controleer of er geen onopgeloste problemen zijn:** Voordat u een site bijwerkt, moet u alle operationele problemen voor de siteserver, de Sitedatabaseserver en de sitesysteemrollen die zijn geïnstalleerd op externe computers oplossen. De update van een site kan mislukken door bestaande operationele problemen.

 Zie [Waarschuwingen en het statussysteem voor System Center Configuration Manager gebruiken](../../../core/servers/manage/use-alerts-and-the-status-system.md) voor meer informatie.  

 **Bestands- en databasereplicatie tussen sites controleren:**  Zorg ervoor dat bestand en databasereplicatie tussen sites operationeel en actueel is. Vertragingen of achterstanden in een kunnen voorkomen dat een smooth, geslaagde update.    

Voor databasereplicatie kunt u Replication Link Analyzer gebruiken om u te helpen bij het oplossen van problemen voordat u de update start. Zie voor meer informatie [over de Replication Link Analyzer](../../../core/servers/manage/monitor-hierarchy-and-replication-infrastructure.md#BKMK_RLA) in het onderwerp [hiërarchie- en replicatie-infrastructuur bewaken in System Center Configuration Manager](../../../core/servers/manage/monitor-hierarchy-and-replication-infrastructure.md).  

 **Installeer alle toepasselijke kritieke updates voor besturingssystemen op computers die als host fungeren voor de site, de Sitedatabaseserver en externe sitesysteemrollen:** Voordat u een update voor Configuration Manager installeert, installeert u alle kritieke updates voor elk toepasselijk sitesysteem. Als een update die u installeert, vereist dat de computer opnieuw wordt opgestart, start de desbetreffende computers dan opnieuw op voordat u de upgrade start.  

 **Databasereplica's voor beheerpunten op primaire sites uitschakelen:** Configuration Manager kan niet met succes bijwerken voor een primaire site die een databasereplica voor beheerpunten ingeschakeld heeft. Schakel databasereplicatie uit voordat u een update voor Configuration Manager installeert.  

Zie voor meer informatie [Databasereplica's voor beheerpunten voor System Center Configuration Manager](../../../core/servers/deploy/configure/database-replicas-for-management-points.md).  

 **SQL Server AlwaysOn-beschikbaarheidsgroepen op handmatige failover ingesteld:**  
 Zorg ervoor dat de beschikbaarheidsgroep is ingesteld op handmatige failover voor de installatie van updates, zoals versie 1606. Nadat de site is bijgewerkt, kunt u failover worden automatisch herstellen. Zie voor meer informatie [SQL Server AlwaysOn voor een sitedatabase](../../../core/servers/deploy/configure/sql-server-alwayson-for-a-highly-available-site-database.md).

 **Software-updatepunten met NLB's opnieuw configureren:** Configuration Manager kan een site die gebruikmaakt van een Network Load Balancing (NLB) cluster host software-updatepunten niet bijwerken.  

Als u NLB-clusters voor software-updatepunten gebruikt, moet u Windows PowerShell gebruiken om te verwijderen van het NLB-cluster.    

 Zie [Software-updates plannen in System Center Configuration Manager](../../../sum/plan-design/plan-for-software-updates.md) voor meer informatie.  

 **Alle siteonderhoudstaken op elke site uitschakelen voor de duur van de installatie van de update op die site:** Voordat u de update installeert, schakel alle siteonderhoudstaken die mogelijk worden uitgevoerd op het moment dat het updateproces actief is. Dit omvat, maar is niet beperkt tot het volgende:  

-   Back-upserver van site  

-   Verouderde clientbewerkingen verwijderen  

-   Verouderde detectiegegevens verwijderen  

Wanneer een onderhoudstaak van de sitedatabase wordt uitgevoerd tijdens de installatie van updates, kan de installatie van de update mislukken. Voordat u een taak, registreert u het schema van de taak uitschakelt zodat u kunt de configuratie ervan herstellen kunt nadat de update is geïnstalleerd.  

Zie voor meer informatie [onderhoudstaken voor System Center Configuration Manager](../../../core/servers/manage/maintenance-tasks.md) en [verwijzing voor het onderhoud van taken voor System Center Configuration Manager](../../../core/servers/manage/reference-for-maintenance-tasks.md). 

**Stop tijdelijk antivirussoftware op de System Center Configuration Manager-servers:** Voordat u een site bijwerkt, zorg ervoor dat u antivirussoftware op de Configuration Manager-servers. <!--SMS.503481--> 

 **Maak een back-up van de sitedatabase op de centrale beheersite en primaire sites:** Voordat u een site bijwerkt, maakt u een back-up van de sitedatabase om ervoor te zorgen dat hebt u een goede back-up voor herstel na noodgevallen.   

Zie voor meer informatie [back-up en herstel voor System Center Configuration Manager](../../../protect/understand/backup-and-recovery.md).  

<!-- Removed from update guidance 6/6/2017
 **Test the database upgrade on a copy of the most recent site database backup:** Before you update a System Center Configuration Manager central administration site or primary site, test the site database upgrade process on a copy of the site database.  

-   You should test the site database upgrade process because when you upgrade a site, the site database might be modified.  

-   Although a test database upgrade is not required, it can identify problems for the upgrade before your production database is affected.  

-   A failed site database upgrade can render your site database inoperable and might require a site recovery to restore functionality.  

-   Although the site database is shared between sites in a hierarchy, plan to test the database at each applicable site before you upgrade that site.  

-   If you use database replicas for management points at a primary site, disable replication before you create the backup of the site database.  

Configuration Manager does not support the backup of secondary sites nor does it support the test upgrade of a secondary site database.   

Do not run a test database upgrade on the production site database. Doing so updates the site database and could render your site inoperable. For more information, For more information, see [Step 2: Test the database upgrade before installing an update](/sccm/core/servers/manage/install-in-console-updates#bkmk_step2) from **Before you install an in-console update**.
-->

 **Clientproef plannen:** Wanneer u een update die de client wordt bijgewerkt installeert, kunt u die nieuwe clientupdate testen in een testomgeving voordat deze worden geïmplementeerd en alle actieve clients worden bijgewerkt.   

 Als u wilt profiteren van deze optie, voordat u begint de installatie van de update, moet u uw site ter ondersteuning van automatische upgrades voor preproductie configureren. Zie voor meer informatie [Upgrade clients in System Center Configuration Manager](../../../core/clients/manage/upgrade/upgrade-clients.md) (Clients bijwerken in System Center Configuration Manager) en   
[Clientupgrades testen in pre-productieverzameling in System Center Configuration Manager](../../../core/clients/manage/upgrade/test-client-upgrades.md).  

 **Wilt u gebruiken servicewindows om te bepalen wanneer siteservers updates installeren:** U kunt servicewindows gebruiken voor het definiëren van een periode gedurende welke updates op een siteserver kunnen worden geïnstalleerd.

Hiermee kunt u bepalen wanneer de sites in uw hiërarchie de update installeren.
Voorafgaand aan versie 1606, werden servicewindows onderhoudsvensters genoemd. Zie voor meer informatie [servicewindows voor siteservers Service](/sccm/core/servers/manage/service-windows).  

 **Setup prerequisite checker uitvoeren:**  Voordat u update 1606 installeert, kunt u de prerequisite checker onafhankelijk van de update-installatie uitvoeren. Wanneer u de update op de site installeert, wordt prerequisite checker opnieuw uitgevoerd.  

Zie voor meer informatie **stap 3: De prerequisite checker uitvoeren voordat u een update installeert** in de [Updates voor System Center Configuration Manager](../../../core/servers/manage/install-in-console-updates.md) onderwerp.  

> [!IMPORTANT]  
>  Wanneer de prerequisite checker wordt uitgevoerd als onderdeel van de installatie van een update of onafhankelijk, werkt het proces enkele bronbestanden product die worden gebruikt voor siteonderhoudstaken. Daarom dat na het uitvoeren van de prerequisite checker maar voordat de update 1606 is geïnstalleerd als u wilt uitvoeren van een siteonderhoudstaak uitvoeren **Setupwpf.exe** (het installatieprogramma van Configuration Manager) vanaf de CD. Meest recente map op de siteserver.  

 **Sites bijwerken:** U bent nu klaar om de installatie van de update voor uw hiërarchie.  
  Het is raadzaam dat u installeren, de update buiten kantooruren voor elke site wilt wanneer het installatieproces van de update en de bijbehorende acties voor het installeren van de Siteonderdelen en sitesysteemrollen minimale invloed heeft op uw zakelijke activiteiten.

Zie [Updates voor System Center Configuration Manager](../../../core/servers/manage/updates.md) voor meer informatie.  
