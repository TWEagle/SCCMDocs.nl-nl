---
title: Controlelijst voor 1602
titleSuffix: Configuration Manager
description: Meer informatie over acties moet uitvoeren voordat het bijwerken van System Center Configuration Manager versie 1511 naar versie 1602.
ms.custom: na
ms.date: 2/7/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: b63ef197-01f0-4894-b929-5ef8403c5195
caps.latest.revision: "13"
author: Brenduns
ms.author: brenduns
manager: angrobe
robots: NOINDEX, NOFOLLOW
ms.openlocfilehash: 629f09a8e4306a7030850d377f26311f962a9e7a
ms.sourcegitcommit: c236214b2fcc13dae7bad96d7fb33f692868191d
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/12/2017
---
# <a name="checklist-for-installing-update-1602-for-system-center-configuration-manager"></a>Controlelijst voor het installeren van update 1602 voor System Center Configuration Manager

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*

Lees voordat van System Center Configuration Manager versie 1511 naar versie 1602 bijwerken, de volgende informatie en Controlelijst voor acties moet uitvoeren voordat u de update start.  

 **Over het installeren van update 1602:**  

 Update 1602 kan alleen op de site op het hoogste niveau van uw hiërarchie worden opgegeven. Dit betekent dat u de installatie starten vanuit uw centrale beheersite als er een of vanuit uw zelfstandige primaire site.  

-   Onderliggende primaire sites de update automatisch geïnstalleerd als de centrale beheersite is voltooid met het installeren van de update. U kunt onderhoudsvensters om te bepalen wanneer een site updates installeert. Vanaf de release van update 1602 kunt onderhoudsvensters zijn gewijzigd *windows service*. Zie voor meer informatie [servicewindows voor siteservers Service](/sccm/core/servers/manage/service-windows).  

-   U moet secundaire sites uit binnen de Configuration Manager-console handmatig bijwerken nadat de primaire bovenliggende site is voltooid met het installeren van de update. Automatische updates van secundaire siteservers worden niet ondersteund.  

Wanneer de siteserver wordt geïnstalleerd voor de update, sitesysteemrollen die zijn geïnstalleerd op de siteserver en toepassingen die zijn geïnstalleerd op externe computers automatisch bijgewerkt. Voordat u de update installeert, Controleer daarom elke sitesysteemserver voldoet aan de nieuwe vereisten voor bewerkingen met de nieuwe versie van de update.  

De eerste keer dat u een Configuration Manager-console gebruikt nadat de update is voltooid, wordt u gevraagd om bij te werken die console. Om dit te doen, moet u setup van Configuration Manager uitvoeren op de computer die als host fungeert voor de console en kies de optie de console bij te werken. U kunt installeren van de update naar de console beter niet uitstellen.  

 **Controlelijst:**  

 **Zorg ervoor dat alle sites een ondersteunde versie van System Center Configuration Manager wordt uitgevoerd:**  Elke siteserver in de hiërarchie moet System Center Configuration Manager versie 1511 voordat u de installatie van update 1602 kunt gaan uitvoeren.  

 **Microsoft .NET-versies revisie geïnstalleerd op sitesysteemservers:** Wanneer een site update 1602 installeert, installeert Configuration Manager automatisch .NET Framework 4.5.2 op elke computer die als host fungeert voor een van de volgende sitesysteemrollen (als .NET Framework 4.5 of hoger nog niet is geïnstalleerd):  

-   Proxypunt voor inschrijving  

-   Inschrijvingspunt  

-   Beheerpunt  

-   Serviceverbindingspunt  

Deze installatie kunt u de sitesysteemserver in een opnieuw opstarten in behandeling zijnde status en fouten rapporteren bij Configuration Manager component statusviewer plaatsen. Bovendien kunnen .NET-toepassingen op de server willekeurige fouten optreden, totdat de server opnieuw is gestart.  

 Zie voor meer informatie [Site and site system prerequisites](../../../core/plan-design/configs/site-and-site-system-prerequisites.md) (Vereisten voor sites en sitesystemen).  

 **Bekijk de site en hiërarchiestatus en controleer of er geen onopgeloste problemen zijn:** Voordat u een site bijwerkt, moet u alle operationele problemen voor de siteserver, de Sitedatabaseserver en de sitesysteemrollen die zijn geïnstalleerd op externe computers oplossen. De update van een site kan mislukken door bestaande operationele problemen.  

Zie [Waarschuwingen en het statussysteem voor System Center Configuration Manager gebruiken](../../../core/servers/manage/use-alerts-and-the-status-system.md) voor meer informatie.  

 **Bestands- en databasereplicatie tussen sites controleren:**  Zorg ervoor dat bestand en databasereplicatie tussen sites operationeel en actueel is. Vertragingen of achterstanden in een kunnen voorkomen dat een smooth, geslaagde update.    

Voor databasereplicatie kunt u Replication Link Analyzer gebruiken om u te helpen bij het oplossen van problemen voordat u de update start.    

 Zie voor meer informatie [over de Replication Link Analyzer](../../../core/servers/manage/monitor-hierarchy-and-replication-infrastructure.md#BKMK_RLA) in de [hiërarchie- en replicatie-infrastructuur bewaken in System Center Configuration Manager](../../../core/servers/manage/monitor-hierarchy-and-replication-infrastructure.md) onderwerp.  

 **Installeer alle toepasselijke kritieke updates voor besturingssystemen op computers die als host fungeren voor de site, de Sitedatabaseserver en externe sitesysteemrollen:** Voordat u een update voor Configuration Manager installeert, installeert u alle kritieke updates voor elk toepasselijk sitesysteem. Als een update die u installeert, vereist dat de computer opnieuw wordt opgestart, start de desbetreffende computers dan opnieuw op voordat u de upgrade start.  

 **Databasereplica's voor beheerpunten op primaire sites uitschakelen:** Configuration Manager kan niet met succes bijwerken voor een primaire site die een databasereplica voor beheerpunten ingeschakeld heeft. Schakel databasereplicatie uit voordat u:  

-   Maak een back-up van de sitedatabase om de database-upgrade te testen.  

-   Een update voor Configuration Manager installeert.  

Zie voor meer informatie [Databasereplica's voor beheerpunten voor System Center Configuration Manager](../../../core/servers/deploy/configure/database-replicas-for-management-points.md).  

 **Software-updatepunten met NLB's opnieuw configureren:** Configuration Manager kan een site die gebruikmaakt van een Network Load Balancing (NLB) cluster host software-updatepunten niet bijwerken.  Als u NLB-clusters voor software-updatepunten gebruikt, moet u Windows PowerShell gebruiken om te verwijderen van het NLB-cluster.    

 Zie [Software-updates plannen in System Center Configuration Manager](../../../sum/plan-design/plan-for-software-updates.md) voor meer informatie.  

 **Alle siteonderhoudstaken op elke site uitschakelen voor de duur van de installatie van de update op die site:** Voordat u updates installeert, schakel alle siteonderhoudstaken die mogelijk worden uitgevoerd tijdens de tijd die het updateproces actief is. Deze taken bevatten (maar niet beperkt) in het volgende:  

-   Back-upserver van site  

-   Verouderde clientbewerkingen verwijderen  

-   Verouderde detectiegegevens verwijderen  

Wanneer een onderhoudstaak van de sitedatabase wordt uitgevoerd tijdens de installatie van updates, kan de installatie van de update mislukken. Voordat u een taak uitschakelt, registreert u het schema van de taak zodat u de configuratie ervan kunt herstellen nadat de update is geïnstalleerd.  

 Zie voor meer informatie [onderhoudstaken voor System Center Configuration Manager](../../../core/servers/manage/maintenance-tasks.md) en [verwijzing voor het onderhoud van taken voor System Center Configuration Manager](../../../core/servers/manage/reference-for-maintenance-tasks.md).  

 **Maak een back-up van de sitedatabase op de centrale beheersite en primaire sites:** Voordat u een site bijwerkt, back-up van de sitedatabase om ervoor te zorgen dat er een goede back-up voor herstel na noodgevallen.   

Zie voor meer informatie [back-up en herstel voor System Center Configuration Manager](../../../protect/understand/backup-and-recovery.md).  

 **Back-up van een aangepast bestand Configuration.mof:** Als u een aangepast bestand Configuration.mof gebruikt voor het definiëren van gegevensklassen die u met hardware-inventaris gebruikt, maakt u een back-up van dit bestand voordat u de site bijwerkt. Nadat de update, dit bestand te herstellen naar de site van uw versie 1602. Wanneer u een site bijwerkt, wordt het huidige bestand overschreven met de oorspronkelijke (standaard) versie van het bestand. Zie voor meer informatie over het gebruik van dit bestand [hardware-inventarisatie in System Center Configuration Manager uitbreiden](../../../core/clients/manage/inventory/extend-hardware-inventory.md).  

 **Test de upgrade van de database op een kopie van de recentste site-databasebackup:** Voordat u een System Center Configuration Manager-centrale beheersite of primaire site bijwerkt, test u de site-database-upgradeproces op een kopie van de sitedatabase.  

-   Omdat wanneer u een site bijwerkt, de sitedatabase kan worden gewijzigd, moet u het upgradeproces sitedatabase testen.  

-   Hoewel een testdatabase-upgrade niet vereist is, kan dit problemen voor de upgrade identificeren voordat deze de productiedatabase beïnvloeden.  

-   Een mislukte upgrade van de sitedatabase kan leiden tot een onbruikbare sitedatabase, waardoor u mogelijk een site recovery moet uitvoeren om de functionaliteit te herstellen.  

-   Hoewel de sitedatabase wordt gedeeld tussen sites in een hiërarchie, plan een test van de database op elke toepasselijke site vóór de upgrade van die site.  

-   Als u Databasereplica's voor beheerpunten op een primaire site gebruikt, schakel u replicatie uit voordat u de back-up van de sitedatabase maakt.  

Configuration Manager biedt geen ondersteuning voor de back-up van secundaire sites en ook ondersteuning voor de testupgrade van een secundaire sitedatabase.   
Voer een testdatabase-upgrade niet op de productie-sitedatabase. Dit leidt tot een update van de sitedatabase en kan tot gevolg hebben dat uw site onbruikbaar wordt. Zie voor meer informatie [stap 2: De upgrade database testen voordat u een update installeert](/sccm/core/servers/manage/install-in-console-updates#bkmk_step2) van **voordat u een update in de console installeert**.  

 **Clientproef plannen:** Wanneer u een update die de client wordt bijgewerkt installeert, kunt u die nieuwe clientupdate testen in een testomgeving voordat deze worden geïmplementeerd en alle actieve clients worden bijgewerkt.   

 Als u wilt profiteren van deze optie, moet u uw site ter ondersteuning van automatische upgrades voor preproductie voordat u de installatie van de update configureren. Zie voor meer informatie [Upgrade clients in System Center Configuration Manager](../../../core/clients/manage/upgrade/upgrade-clients.md) (Clients bijwerken in System Center Configuration Manager) en   
[Clientupgrades testen in pre-productieverzameling in System Center Configuration Manager](../../../core/clients/manage/upgrade/test-client-upgrades.md).  

 **Plan voor het gebruik van onderhoudsvensters om te bepalen wanneer siteservers updates installeren:** U kunt de onderhoudsvensters gebruiken voor het definiëren van een bepaalde periode gedurende welke updates naar de siteserver kunnen worden geïnstalleerd. Hiermee kunt u bepalen wanneer de sites in uw hiërarchie de update installeren.   

Vanaf de release van update 1602 kunt onderhoudsvensters zijn gewijzigd *windows service*. Zie voor meer informatie [servicewindows voor siteservers Service](/sccm/core/servers/manage/service-windows).  

 **Setup prerequisite checker uitvoeren:**  Voordat u update 1602 installeert, kunt u de prerequisite checker onafhankelijk van de update-installatie uitvoeren. Wanneer u de update op de site installeert, wordt prerequisite checker opnieuw uitgevoerd.  

Zie voor meer informatie **stap 3: De prerequisite checker uitvoeren voordat u een update installeert** in de [Updates voor System Center Configuration Manager](../../../core/servers/manage/updates.md) onderwerp.  

> [!IMPORTANT]  
>  Wanneer de prerequisite checker wordt uitgevoerd als onderdeel van de installatie van een update of onafhankelijk, werkt het proces enkele bronbestanden product die worden gebruikt voor siteonderhoudstaken. Daarom dat na het uitvoeren van de prerequisite checker maar voordat de update 1602 installeren als u wilt uitvoeren van een siteonderhoudstaak uitvoeren **Setupwfe.exe** (het installatieprogramma van Configuration Manager) vanaf de CD. Meest recente map op de siteserver.  

 **Sites bijwerken:** U bent nu klaar om de installatie van de update voor uw hiërarchie. Het is raadzaam dat u installeren, de update buiten kantooruren voor elke site wilt wanneer het installatieproces van de update en de bijbehorende acties voor het installeren van de Siteonderdelen en sitesysteemrollen minimale invloed heeft op uw zakelijke activiteiten.

Zie [Updates voor System Center Configuration Manager](../../../core/servers/manage/updates.md) voor meer informatie.  

## <a name="see-also"></a>Zie tevens  
 [Updates voor System Center Configuration Manager](../../../core/servers/manage/updates.md)
