---
title: Controlelijst voor 1602 | Microsoft-documenten
description: Meer informatie over acties uitvoeren voordat het bijwerken van System Center Configuration Manager versie 1511 naar versie 1602.
ms.custom: na
ms.date: 2/7/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: b63ef197-01f0-4894-b929-5ef8403c5195
caps.latest.revision: 13
author: Brenduns
ms.author: brenduns
manager: angrobe
robots: NOINDEX, NOFOLLOW
ms.translationtype: Machine Translation
ms.sourcegitcommit: dab5da5a4b5dfb3606a8a6bd0c70a0b21923fff9
ms.openlocfilehash: 3e0de56b7a592b105e6a61b3d6654b1d0142584d
ms.contentlocale: nl-nl
ms.lasthandoff: 05/17/2017

---
# <a name="checklist-for-installing-update-1602-for-system-center-configuration-manager"></a>Controlelijst voor het installeren van update 1602 voor System Center Configuration Manager

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*

Bekijk de volgende informatie en Controlelijst voor acties uitvoeren voordat de update starten van System Center Configuration Manager versie 1511 bijwerken naar versie 1602.  

 **Over het installeren van update 1602:**  

 Update 1602 kan alleen op de site op het hoogste niveau van uw hiërarchie worden opgegeven. Dit betekent dat u de installatie starten vanuit uw centrale beheersite als er een hebt of vanuit uw zelfstandige primaire site.  

-   Onderliggende primaire sites de update automatisch geïnstalleerd nadat de centrale beheersite is voltooid met het installeren van de update. U kunt onderhoudsvensters om te bepalen wanneer een site updates worden geïnstalleerd. Beginnen met de release van de update 1602, onderhoudsvensters zijn gewijzigd *windows service*. Zie voor meer informatie [windows voor siteservers Service](/sccm/core/servers/manage/service-windows).  

-   Nadat de primaire bovenliggende site is voltooid de update is geïnstalleerd, moet u handmatig secundaire sites van in de Configuration Manager-console bijwerken. Automatische updates van secundaire siteservers worden niet ondersteund.  

Als de siteserver de update is geïnstalleerd, bijgewerkt sitesysteemrollen die op de siteserver en toepassingen die automatisch worden geïnstalleerd op externe computers zijn geïnstalleerd. Daarom de update is geïnstalleerd, zorg er voordat elke sitesysteemserver voldoet aan de nieuwe vereisten voor bewerkingen met de nieuwe versie van de update.  

De eerste keer dat u een Configuration Manager-console gebruiken nadat de update is voltooid, wordt u gevraagd om bij te werken die console. Om dit te doen, moet u het installatieprogramma van Configuration Manager uitvoeren op de computer die als host fungeert voor de console en kies de optie de console bijwerken. U kunt installeren van de update naar de console beter niet uitstellen.  

 **Controlelijst:**  

 **Zorg ervoor dat alle sites een ondersteunde versie van System Center Configuration Manager wordt uitgevoerd:**  Elke siteserver in de hiërarchie moet de System Center Configuration Manager versie 1511 voordat u kunt de installatie van update 1602 uitvoeren.  

 **Microsoft .NET-versies revisie geïnstalleerd op sitesysteemservers:** Als een site 1602-update geïnstalleerd, installeert Configuration Manager automatisch .NET Framework 4.5.2 op elke computer die als host fungeert voor een van de volgende sitesysteemrollen (als .NET Framework 4.5 of hoger niet al is geïnstalleerd):  

-   Proxypunt voor inschrijving  

-   Inschrijvingspunt  

-   Beheerpunt  

-   Serviceverbindingspunt  

Deze installatie kunt u de sitesysteemserver in een opnieuw opstarten in behandeling zijnde status en fouten rapporteren bij de viewer van Configuration Manager component status plaatsen. Daarnaast .NET-toepassingen op de server te maken kunnen krijgen willekeurig mislukken totdat de server opnieuw is gestart.  

 Zie voor meer informatie [Site and site system prerequisites](../../../core/plan-design/configs/site-and-site-system-prerequisites.md) (Vereisten voor sites en sitesystemen).  

 **Bekijk de site en hiërarchiestatus en controleer of er geen onopgeloste problemen:** Voordat u een site bijwerkt, moet u alle operationele problemen voor de siteserver, de Sitedatabaseserver en de sitesysteemrollen die op externe computers zijn geïnstalleerd oplossen. De update van een site kan mislukken door bestaande operationele problemen.  

Zie [Waarschuwingen en het statussysteem voor System Center Configuration Manager gebruiken](../../../core/servers/manage/use-alerts-and-the-status-system.md) voor meer informatie.  

 **Controleer de bestands- en replicatie tussen sites:**  Zorg ervoor dat bestand en databasereplicatie tussen sites operationele en actueel. Vertragingen of achterstanden in ofwel kunnen voorkomen dat een goede geslaagde update.    

Voor databasereplicatie kunt u Replication Link Analyzer gebruiken om u te helpen bij het oplossen van problemen voordat u de update start.    

 Zie voor meer informatie [over de Replication Link Analyzer](../../../core/servers/manage/monitor-hierarchy-and-replication-infrastructure.md#BKMK_RLA) in de [controleren-hiërarchie en de replicatie van de infrastructuur in System Center Configuration Manager](../../../core/servers/manage/monitor-hierarchy-and-replication-infrastructure.md) onderwerp.  

 **Installeer alle toepasselijke kritieke updates voor besturingssystemen op computers die als host fungeren voor de site, de Sitedatabaseserver en externe sitesysteemrollen:** Voordat u een update voor Configuration Manager installeert, installeert u alle kritieke updates voor elk toepasselijk sitesysteem. Als een update die u installeert, vereist dat de computer opnieuw wordt opgestart, start de desbetreffende computers dan opnieuw op voordat u de upgrade start.  

 **Databasereplica's voor beheerpunten op primaire sites uitschakelen:** Configuration Manager kan een primaire site die een databasereplica voor beheerpunten ingeschakeld heeft niet bijwerken. Schakel databasereplicatie uit voordat u:  

-   Maak een back-up van de sitedatabase om de database-upgrade te testen.  

-   Installatie van een update voor Configuration Manager.  

Zie voor meer informatie [replica's voor beheerpunten voor System Center Configuration Manager-Database](../../../core/servers/deploy/configure/database-replicas-for-management-points.md).  

 **Software-updatepunten met NLB opnieuw:** Configuration Manager kan een site die gebruikmaakt van een Network Load Balancing (NLB) cluster host software-updatepunten niet bijwerken.  Als u NLB-clusters voor software-updatepunten gebruikt, moet u Windows PowerShell gebruiken om te verwijderen van het NLB-cluster.    

 Zie [Software-updates plannen in System Center Configuration Manager](../../../sum/plan-design/plan-for-software-updates.md) voor meer informatie.  

 **Schakel alle siteonderhoudstaken op elke site tijdens de duur van de installatie van updates op die site:** Voordat u updates installeert, schakel alle siteonderhoudstaken die mogelijk worden uitgevoerd tijdens de tijd die het updateproces actief is. Deze taken bevatten (maar niet beperkt zijn) in het volgende:  

-   Back-upserver van site  

-   Verouderde clientbewerkingen verwijderen  

-   Verouderde detectiegegevens verwijderen  

Wanneer een onderhoudstaak van de sitedatabase wordt uitgevoerd tijdens de installatie van updates, kan de installatie van de update mislukken. Voordat u een taak uitschakelt, registreert u het schema van de taak zodat u de configuratie ervan kunt herstellen nadat de update is geïnstalleerd.  

 Zie voor meer informatie [onderhoudstaken voor System Center Configuration Manager](../../../core/servers/manage/maintenance-tasks.md) en [verwijzing voor het onderhoud van taken voor System Center Configuration Manager](../../../core/servers/manage/reference-for-maintenance-tasks.md).  

 **Maak een back-up van de sitedatabase op de centrale beheersite en primaire sites:** Voordat u een site bijwerkt, back-up van de sitedatabase om ervoor te zorgen dat er een geslaagde back-up moet worden gebruikt voor herstel na noodgevallen.   

Zie voor meer informatie [back-up en herstel voor System Center Configuration Manager](../../../protect/understand/backup-and-recovery.md).  

 **Back-up van een bestand met aangepaste Configuration.mof:** Als u een bestand met aangepaste Configuration.mof definiëren gegevensklassen die u met de hardware-inventaris gebruikt gebruiken, maakt u een back-up van dit bestand voordat u de site bijwerkt. Na de update dit bestand naar uw site versie 1602 te herstellen. Wanneer u een site bijwerkt, wordt het huidige bestand met de oorspronkelijke versie (standaard) van het bestand overschreven. Zie voor meer informatie over het gebruik van dit bestand [het uitbreiden van hardware-inventaris in System Center Configuration Manager](../../../core/clients/manage/inventory/extend-hardware-inventory.md).  

 **Test het database-upgrade op een kopie van de databaseback-up van de meest recente site:** Voordat u een site voor Centraal beheer van System Center Configuration Manager of de primaire site bijwerken, test u de site-database-upgradeproces op een kopie van de sitedatabase.  

-   Omdat bij een upgrade van een site, de sitedatabase kan zijn gewijzigd, moet u het upgradeproces sitedatabase testen.  

-   Hoewel een testdatabase-upgrade niet vereist is, kunt u problemen voor de upgrade detecteren voordat uw productiedatabase Hierdoor wordt beïnvloed.  

-   Een mislukte upgrade van de sitedatabase kan leiden tot een onbruikbare sitedatabase, waardoor u mogelijk een site recovery moet uitvoeren om de functionaliteit te herstellen.  

-   Hoewel de sitedatabase wordt gedeeld tussen sites in een hiërarchie, plan een test voor de database op iedere betreffende site voordat u die site upgradet.  

-   Als u Databasereplica's voor beheerpunten op een primaire site, schakelt u replicatie uit voordat u de back-up van de sitedatabase maakt.  

Configuration Manager biedt geen ondersteuning voor de back-up van secundaire sites noch ondersteunen de testupgrade van een secundaire sitedatabase.   
Voer een testdatabase-upgrade niet op de productie-sitedatabase. Dit leidt tot een update van de sitedatabase en kan tot gevolg hebben dat uw site onbruikbaar wordt. Zie voor meer informatie [stap 2: Testen van de upgrade van de database voordat u een update installeert](/sccm/core/servers/manage/install-in-console-updates#bkmk_step2) van **voordat u een update in de console**.  

 **Plannen voor haalbaarheidsonderzoek client:** Wanneer u een update die updates van de client installeert, kunt u die nieuwe clientupdate testen in een testomgeving voordat deze worden geïmplementeerd en alle actieve clients worden bijgewerkt.   

 Als u wilt profiteren van deze optie, moet u uw site voor ondersteuning van automatische updates voor de test voordat u begint de installatie van de update. Zie voor meer informatie [Upgrade clients in System Center Configuration Manager](../../../core/clients/manage/upgrade/upgrade-clients.md) (Clients bijwerken in System Center Configuration Manager) en   
[Het testen van clientupgrades in een pre-productieverzameling in System Center Configuration Manager](../../../core/clients/manage/upgrade/test-client-upgrades.md).  

 **Plannen voor het gebruik van onderhoudsvensters om te bepalen wanneer siteservers updates installeren:** U kunt de onderhoudsvensters gebruiken voor het definiëren van een bepaalde periode gedurende welke updates naar de siteserver kunnen worden geïnstalleerd. Hiermee kunt u bepalen wanneer de sites in uw hiërarchie de update installeren.   

Beginnen met de release van de update 1602, onderhoudsvensters zijn gewijzigd *windows service*. Zie voor meer informatie [windows voor siteservers Service](/sccm/core/servers/manage/service-windows).  

 **Setup prerequisite checker uitvoeren:**  Voordat u update 1602 installeert, kunt u de prerequisite checker onafhankelijk van de update-installatie uitvoeren. Wanneer u de update op de site installeert, wordt prerequisite checker opnieuw uitgevoerd.  

Zie voor meer informatie **stap 3: De prerequisite checker uitvoeren voordat u een update installeert** in de [voor System Center Configuration Manager-Updates](../../../core/servers/manage/updates.md) onderwerp.  

> [!IMPORTANT]  
>  Wanneer de vereistencontrole wordt uitgevoerd, afzonderlijk of als onderdeel van een installatie van updates, werkt het proces enkele product bronbestanden die worden gebruikt voor siteonderhoudstaken. Daarom dat na het uitvoeren van de prerequisite checker maar voordat de update 1602 installeren als u wilt uitvoeren van een siteonderhoudstaak uitgevoerd **Setupwfe.exe** (installatie van Configuration Manager) vanaf de CD. Meest recente map op de siteserver.  

 **Sites bijwerken:** U bent nu klaar om de installatie van de update voor uw hiërarchie. Het is raadzaam dat u van plan bent de update te installeren buiten kantooruren voor elke site, wanneer het proces om de update en de bijbehorende acties opnieuw installeren van site-onderdelen en sitesysteemrollen te installeren wordt de minste invloed op uw zakelijke activiteiten hebben.

Zie [Updates voor System Center Configuration Manager](../../../core/servers/manage/updates.md) voor meer informatie.  

## <a name="see-also"></a>Zie tevens  
 [Updates voor System Center Configuration Manager](../../../core/servers/manage/updates.md)

