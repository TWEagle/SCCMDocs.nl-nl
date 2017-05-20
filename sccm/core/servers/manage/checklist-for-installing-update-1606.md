---
title: Controlelijst voor 1606 | Microsoft-documenten
description: Meer informatie over acties uitvoeren voordat het bijwerken van System Center Configuration Manager versie 1511 of 1602 naar versie 1606.
ms.custom: na
ms.date: 2/7/2017
ms.reviewer: na
ms.suite: na
ms.prod: configuration-manager
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 75652cd2-a95a-46c5-91c1-6d43fc8e787e
caps.latest.revision: 7
author: Brenduns
ms.author: brenduns
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 30af3326578d39c6d995672071705bcaeb877e4d
ms.openlocfilehash: b0def6eb962d243a7ea5910b8d56bbb448b3a2e4
ms.contentlocale: nl-nl
ms.lasthandoff: 05/17/2017

---
# <a name="checklist-for-installing-update-1606-for-system-center-configuration-manager"></a>Controlelijst voor het installeren van update 1606 voor System Center Configuration Manager

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*

Versie 1606 voor System Center Configuration Manager huidige vertakking is een update die u gebruiken kunt om bij te werken vanaf versie 1511 of 1602.

Voordat u versie 1606 installeert als een update, Controleer de volgende informatie en Controlelijst voor acties uitvoeren voordat de update gestart.

Zie voor informatie over de versies van de basislijn [basislijn en update versies](../../../core/servers/manage/updates.md#bkmk_Baselines) in [voor System Center Configuration Manager-Updates](../../../core/servers/manage/updates.md).

 ## <a name="about-installing-update-1606"></a>Over het installeren van update 1606

Als een *bijwerken*, 1606 kan alleen worden geïnstalleerd op de site op het hoogste niveau van uw hiërarchie. Dit betekent dat u de installatie starten vanuit uw centrale beheersite als er een hebt of vanuit uw zelfstandige primaire site.  

-   Onderliggende primaire sites de update automatisch geïnstalleerd nadat de centrale beheersite is voltooid met het installeren van de update. U kunt windows service om te bepalen wanneer een site updates worden geïnstalleerd. Voor versie 1606 riep de service windows onderhoudsvensters. Zie voor meer informatie [windows voor siteservers Service](/sccm/core/servers/manage/service-windows).  

-   Nadat de primaire bovenliggende site is voltooid de update is geïnstalleerd, moet u handmatig secundaire sites van in de Configuration Manager-console bijwerken. Het automatisch bijwerken van secundaire siteservers wordt niet ondersteund.  

Wanneer de update wordt geïnstalleerd door de siteserver, sitesysteemrollen die op de siteserver en toepassingen die zijn geïnstalleerd op externe computers zijn geïnstalleerd automatisch bijgewerkt. Daarom voordat u de update installeert, zorg dat elke sitesysteemserver voldoet aan de nieuwe vereisten voor bewerkingen met de nieuwe versie van de update.  

De eerste keer dat u een Configuration Manager-console gebruiken nadat de update is geïnstalleerd, wordt u gevraagd om bij te werken die console.  Om dit te doen, moet u Configuration Manager setup uitvoert op de computer die als host fungeert voor de console en kiest u de optie de console bijwerken. U kunt installeren van de update naar de console beter niet uitstellen.

 **Bekende problemen voor deze update**   
  De volgende problemen van toepassing wanneer u de status van de installatie van de update pack weergeven:
  - Bij het bijwerken van versie 1602-1606 de stap **Extract update pakket nettolading** een Status weer van **niet gestart**, zelfs als het downloaden is voltooid.
  - Bij het bijwerken van versie 1511-1606, een aantal stappen leert status **voltooid** maar wordt niet weergegeven voor een waarde voor **tijd van laatste Update**.


## <a name="checklist"></a>Controlelijst  

 **Zorg ervoor dat alle sites een ondersteunde versie van System Center Configuration Manager wordt uitgevoerd:**  Voordat u de installatie van update 1606, elke siteserver in de hiërarchie moet dezelfde versie van System Center Configuration Manager uitvoeren: eender welke versie 1511 of 1602.

 **Controleer Microsoft.NET versies hebt geïnstalleerd op sitesysteemservers:** Als een site 1606-update geïnstalleerd, installeert Configuration Manager automatisch .NET Framework 4.5.2 op elke computer die als host fungeert voor een van de volgende sitesysteemrollen (als .NET Framework 4.5 of hoger niet al is geïnstalleerd):  

-   Proxypunt voor inschrijving  

-   Inschrijvingspunt  

-   Beheerpunt  

-   Serviceverbindingspunt  

Deze installatie kan de sitesysteemserver in een opnieuw opstarten in behandeling zijnde status en het rapport fouten in de viewer van Configuration Manager component status geplaatst. Bovendien kunnen .NET-toepassingen op de server mogelijk willekeurig mislukken totdat de server opnieuw is gestart.  

 Zie voor meer informatie [Site en de systeemvereisten site](../../../core/plan-design/configs/site-and-site-system-prerequisites.md).  

 **Bekijk de site en hiërarchiestatus en controleer of er geen onopgeloste problemen:** Voordat u een site bijwerkt, moet u alle operationele problemen voor de siteserver, de Sitedatabaseserver en de sitesysteemrollen die op externe computers zijn geïnstalleerd oplossen. De update van een site kan mislukken door bestaande operationele problemen.

 Zie [Waarschuwingen en het statussysteem voor System Center Configuration Manager gebruiken](../../../core/servers/manage/use-alerts-and-the-status-system.md) voor meer informatie.  

 **Controleer de bestands- en replicatie tussen sites:**  Zorg ervoor dat bestand en databasereplicatie tussen sites operationele en actueel. Vertragingen of achterstanden in ofwel kunnen voorkomen dat een goede geslaagde update.    

Voor databasereplicatie kunt u Replication Link Analyzer gebruiken om u te helpen bij het oplossen van problemen voordat u de update start. Zie voor meer informatie [over de Replication Link Analyzer](../../../core/servers/manage/monitor-hierarchy-and-replication-infrastructure.md#BKMK_RLA) in het onderwerp [controleren-hiërarchie en de replicatie van de infrastructuur in System Center Configuration Manager](../../../core/servers/manage/monitor-hierarchy-and-replication-infrastructure.md).  

 **Installeer alle toepasselijke kritieke updates voor besturingssystemen op computers die als host fungeren voor de site, de Sitedatabaseserver en externe sitesysteemrollen:** Voordat u een update voor Configuration Manager installeert, installeert u alle kritieke updates voor elk toepasselijk sitesysteem. Als een update die u installeert, vereist dat de computer opnieuw wordt opgestart, start de desbetreffende computers dan opnieuw op voordat u de upgrade start.  

 **Databasereplica's voor beheerpunten op primaire sites uitschakelen:** Configuration Manager kan een primaire site die een databasereplica voor beheerpunten ingeschakeld heeft niet bijwerken. Schakel databasereplicatie uit voordat u:  

-   Maak een back-up van de sitedatabase om de database-upgrade te testen.  

-   Installatie van een update voor Configuration Manager.  

Zie voor meer informatie [replica's voor beheerpunten voor System Center Configuration Manager-Database](../../../core/servers/deploy/configure/database-replicas-for-management-points.md).  

 **SQL Server AlwaysOn-beschikbaarheidsgroepen wilt handmatige failover instellen:**  
 Voordat de installatie van updates, zoals versie 1606, controleert u of de beschikbaarheidsgroep is ingesteld op handmatige failover. Nadat de site is bijgewerkt, kunt u failover worden automatisch herstellen. Zie voor meer informatie [SQL Server AlwaysOn van een sitedatabase](../../../core/servers/deploy/configure/sql-server-alwayson-for-a-highly-available-site-database.md).

 **Software-updatepunten met NLB opnieuw:** Configuration Manager kan een site die gebruikmaakt van een Network Load Balancing (NLB) cluster host software-updatepunten niet bijwerken.  

Als u NLB-clusters voor software-updatepunten gebruikt, moet u Windows PowerShell gebruiken om te verwijderen van het NLB-cluster.    

 Zie [Software-updates plannen in System Center Configuration Manager](../../../sum/plan-design/plan-for-software-updates.md) voor meer informatie.  

 **Schakel alle siteonderhoudstaken op elke site tijdens de duur van de installatie van updates op die site:** Voordat u de update installeren, schakel alle siteonderhoudstaken die mogelijk worden uitgevoerd op het moment dat het updateproces actief is. Dit omvat, maar is niet beperkt tot het volgende:  

-   Back-upserver van site  

-   Verouderde clientbewerkingen verwijderen  

-   Verouderde detectiegegevens verwijderen  

Wanneer een onderhoudstaak van de sitedatabase wordt uitgevoerd tijdens de installatie van updates, kan de installatie van de update mislukken. Voordat u een taak, registreert u het schema van de taak uitschakelt zodat u de configuratie ervan herstellen kunt nadat de update is geïnstalleerd.  

Zie voor meer informatie [onderhoudstaken voor System Center Configuration Manager](../../../core/servers/manage/maintenance-tasks.md) en [verwijzing voor het onderhoud van taken voor System Center Configuration Manager](../../../core/servers/manage/reference-for-maintenance-tasks.md).  

 **Maak een back-up van de sitedatabase op de centrale beheersite en primaire sites:** Voordat u een site bijwerkt, maakt u een back-up van de sitedatabase om ervoor te zorgen dat hebt u een geslaagde back-up moet worden gebruikt voor herstel na noodgevallen.   

Zie voor meer informatie [back-up en herstel voor System Center Configuration Manager](../../../protect/understand/backup-and-recovery.md).  


 **Test het database-upgrade op een kopie van de databaseback-up van de meest recente site:** Voordat u een site voor Centraal beheer van System Center Configuration Manager of de primaire site bijwerken, test u de site-database-upgradeproces op een kopie van de sitedatabase.  

-   Omdat bij een upgrade van een site, de sitedatabase kan zijn gewijzigd, moet u het upgradeproces sitedatabase testen.  

-   Hoewel een testdatabase-upgrade niet vereist is, kunt u problemen voor de upgrade detecteren voordat uw productiedatabase Hierdoor wordt beïnvloed.  

-   Een mislukte upgrade van de sitedatabase kan leiden tot een onbruikbare sitedatabase, waardoor u mogelijk een site recovery moet uitvoeren om de functionaliteit te herstellen.  

-   Hoewel de sitedatabase wordt gedeeld tussen sites in een hiërarchie, plan een test voor de database op iedere betreffende site voordat u die site upgradet.  

-   Als u Databasereplica's voor beheerpunten op een primaire site, schakelt u replicatie uit voordat u de back-up van de sitedatabase maakt.  

Configuration Manager biedt geen ondersteuning voor de back-up van secundaire sites noch ondersteunen de testupgrade van een secundaire sitedatabase.   

Voer een testdatabase-upgrade niet op de productie-sitedatabase. Dit leidt tot een update van de sitedatabase en kan tot gevolg hebben dat uw site onbruikbaar wordt. Zie voor meer informatie voor meer informatie [stap 2: Testen van de upgrade van de database voordat u een update installeert](/sccm/core/servers/manage/install-in-console-updates#bkmk_step2) van **voordat u een update in de console**.

 **Plannen voor haalbaarheidsonderzoek client:** Wanneer u een update die updates van de client installeert, kunt u die nieuwe clientupdate testen in een testomgeving voordat deze worden geïmplementeerd en alle actieve clients worden bijgewerkt.   

 Als u wilt profiteren van deze optie, voordat u begint de installatie van de update, moet u uw site voor ondersteuning van automatische updates voor de test configureren. Zie voor meer informatie [Upgrade clients in System Center Configuration Manager](../../../core/clients/manage/upgrade/upgrade-clients.md) (Clients bijwerken in System Center Configuration Manager) en   
[Het testen van clientupgrades in een pre-productieverzameling in System Center Configuration Manager](../../../core/clients/manage/upgrade/test-client-upgrades.md).  

 **Plannen voor het gebruik van windows service om te bepalen wanneer siteservers updates installeren:** U kunt windows service gebruiken voor het definiëren van een periode gedurende welke updates op een siteserver kunnen worden geïnstalleerd.

Hiermee kunt u bepalen wanneer de sites in uw hiërarchie de update installeren.
Voor versie 1606 riep de service windows onderhoudsvensters. Zie voor meer informatie [windows voor siteservers Service](/sccm/core/servers/manage/service-windows).  

 **Setup prerequisite checker uitvoeren:**  Voordat u update 1606 installeert, kunt u de prerequisite checker onafhankelijk van de update-installatie uitvoeren. Wanneer u de update op de site installeert, wordt prerequisite checker opnieuw uitgevoerd.  

Zie voor meer informatie **stap 3: De prerequisite checker uitvoeren voordat u een update installeert** in de [voor System Center Configuration Manager-Updates](../../../core/servers/manage/install-in-console-updates.md) onderwerp.  

> [!IMPORTANT]  
>  Wanneer de vereistencontrole wordt uitgevoerd, afzonderlijk of als onderdeel van een installatie van updates, werkt het proces enkele product bronbestanden die worden gebruikt voor siteonderhoudstaken. Daarom dat na het uitvoeren van de prerequisite checker maar voordat de update 1606 installeren als u wilt uitvoeren van een siteonderhoudstaak uitgevoerd **Setupwpf.exe** (installatie van Configuration Manager) vanaf de CD. Meest recente map op de siteserver.  

 **Sites bijwerken:** U bent nu klaar om de installatie van de update voor uw hiërarchie.  
  Het is raadzaam dat u van plan bent de update te installeren buiten kantooruren voor elke site, wanneer het proces om de update en de bijbehorende acties opnieuw installeren van site-onderdelen en sitesysteemrollen te installeren wordt de minste invloed op uw zakelijke activiteiten hebben.

Zie [Updates voor System Center Configuration Manager](../../../core/servers/manage/updates.md) voor meer informatie.  

