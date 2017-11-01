---
title: Controlelijst voor 1610
titleSuffix: Configuration Manager
description: Meer informatie over acties moet uitvoeren voordat u bijwerkt naar System Center Configuration Manager versie 1610.
ms.custom: na
ms.date: 6/6/2017
ms.reviewer: na
ms.suite: na
ms.prod: configuration-manager
ms.technology: configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 7b411cb0-4fd1-41f2-a2f6-33738a5bde96
caps.latest.revision: "7"
author: Brenduns
ms.author: brenduns
manager: angrobe
ms.openlocfilehash: b6451acbb17b849e8d291fa33d2cb47b16a4439f
ms.sourcegitcommit: c236214b2fcc13dae7bad96d7fb33f692868191d
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/12/2017
---
# <a name="checklist-for-installing-update-1610-for-system-center-configuration-manager"></a>Controlelijst voor het installeren van update 1610 voor System Center Configuration Manager

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*

Wanneer u de huidige vertakking van System Center Configuration Manager gebruikt, kunt u de update in de console voor versie 1610 bijwerken van uw hiërarchie van versie 1606 kunt installeren. Als uw hiërarchie versie 1511 of 1602 1606 wordt uitgevoerd, kunt u bijwerken naar versie 1610.

Als u de update voor versie 1610, moet u een service connection point-sitesysteemrol op het hoogste niveau van uw hiërarchie. Dit kan zijn in de online of offline-modus. Nadat uw hiërarchie downloadt het updatepakket van Microsoft, kunt u deze vinden in de console onder **beheer &gt; overzicht &gt; Cloudservices &gt; Updates en onderhoud**.

-   Wanneer de update wordt vermeld als **beschikbaar**, de update is gereed om te installeren. Controleer de volgende informatie voordat u versie 1610 installeert, [over het installeren van update 1610](#about-installing-update-1610) en de [controlelijst](#checklist) voor configuraties die u moet voordat u de update start.

-   Als de update wordt weergegeven als **downloaden** en niet wijzigen, Controleer de **hman.log** en **dmpdownloader.log** op fouten.

    -   Meestal kunt u ook opnieuw starten de **SMS_Executive** service op de siteserver opnieuw opstarten van het downloaden van bestanden van de update opnieuw distribueren.

    -   Een andere algemene downloaden probleem treedt op wanneer de instellingen van proxyserver te voorkomen downloads vanaf dat <http://silverlight.dlservice.microsoft.com> en <http://download.microsoft.com>.

Zie voor meer informatie over het installeren van updates [In de console updates en onderhoud](/sccm/core/servers/manage/updates#a-namebkmkinconsolea-in-console-updates-and-servicing).

Zie voor meer informatie over de versies van de huidige vertakking [basislijn- en updateversies](/sccm/core/servers/manage/updates#bkmk_Baselines) in [Updates voor System Center Configuration Manager](/sccm/core/servers/manage/updates).

## <a name="about-installing-update-1610"></a>Over het installeren van update 1610

**Sites:**  
Update 1610 kan alleen worden geïnstalleerd op het hoogste niveau van uw hiërarchie. Dit betekent dat u de installatie starten vanuit uw centrale beheersite als er een of vanuit uw zelfstandige primaire site. Nadat de update wordt geïnstalleerd op de bovenste site, hebben de onderliggende sites de werking van de volgende update:

-   Onderliggende primaire sites de update automatisch geïnstalleerd nadat de installatie van de update is voltooid voor de centrale beheersite. U kunt servicewindows om te bepalen wanneer een site updates installeert. Voorafgaand aan versie 1606, werden servicewindows onderhoudsvensters genoemd. Zie voor meer informatie [servicewindows voor siteservers Service](/sccm/core/servers/manage/service-windows).

-   U moet secundaire sites uit binnen de Configuration Manager-console handmatig bijwerken nadat de bovenliggende primaire site de update-installatie is voltooid. Het automatisch bijwerken van secundaire siteservers wordt niet ondersteund.

**Sitesysteemrollen:**  
Wanneer de siteserver wordt geïnstalleerd voor de update, wordt de sitesysteemrollen die zijn geïnstalleerd op de siteserver en toepassingen die zijn geïnstalleerd op externe computers automatisch bijgewerkt. Voordat u de update installeert, zorg er dus dat elke sitesysteemserver voldoet aan de nieuwe vereisten voor het opnieuw met de nieuwe versie van de update.

**Configuration Manager-consoles:**   
De eerste keer dat u een Configuration Manager-console gebruikt nadat de update is voltooid, wordt u gevraagd om bij te werken die console. Om dit te doen, moet u setup van Configuration Manager uitvoeren op de computer die als host fungeert voor de console en kies vervolgens de optie de console bij te werken. U kunt installeren van de update naar de console beter niet uitstellen.



## <a name="checklist"></a>Controlelijst

**Zorg ervoor dat alle sites een ondersteunde versie van System Center Configuration Manager wordt uitgevoerd:** Voordat u de installatie van update 1610, elke site in de hiërarchie moet worden uitgevoerd dezelfde versie van System Center Configuration Manager: eender welke versie 1511 of 1602 1606.

**Controleer de status van uw Software Assurance of gelijkwaardige abonnementsrechten:**   
U moet een actieve Software Assurance (SA)-overeenkomst voor het installeren van update 1610 hebben. Wanneer u versie 1610 installeert, hebt u de optie op de **Licensing** tabblad om te bevestigen dat uw **Software Assurance vervaldatum**.

Dit is een optionele waarde die u als een handige herinnering aan uw vervaldatum licentie, dat weergegeven opgeven kunt wordt wanneer u toekomstige updates installeren. Als u Configuration Manager van de basislijnmedia versie 1606 hebt geïnstalleerd, hebt u mogelijk eerder opgegeven deze waarde tijdens de installatie of op de **Licensing** tabblad van de **hiërarchie-instellingen** na de installatie van de site.

Zie voor meer informatie [licenties en vertakkingen voor System Center Configuration Manager](/sccm/core/understand/learn-more-editions).

**Microsoft .NET-versies revisie geïnstalleerd op sitesysteemservers:** Wanneer een site update 1610 is geïnstalleerd, installeert Configuration Manager automatisch .NET Framework 4.5.2 op elke computer die als host fungeert voor een van de volgende sitesysteemrollen als .NET Framework 4.5 of hoger, niet al is geïnstalleerd:

-   Proxypunt voor inschrijving
-   Inschrijvingspunt
-   Beheerpunt
-   Serviceverbindingspunt

Deze installatie kunt u de sitesysteemserver in een opnieuw opstarten in behandeling zijnde status en het rapport fouten in de viewer voor Configuration Manager component status plaatsen. Bovendien kunnen .NET-toepassingen op de server willekeurige fouten optreden, totdat de server opnieuw is opgestart.

Zie voor meer informatie [Site and site system prerequisites](/sccm/core/plan-design/configs/site-and-site-system-prerequisites) (Vereisten voor sites en sitesystemen).

**Bekijk de site en hiërarchiestatus en controleer of er geen onopgeloste problemen zijn:** Voordat u een site bijwerkt, moet u alle operationele problemen voor de siteserver, de Sitedatabaseserver en de sitesysteemrollen die zijn geïnstalleerd op externe computers oplossen. De update van een site kan mislukken door bestaande operationele problemen.

Zie [Waarschuwingen en het statussysteem voor System Center Configuration Manager gebruiken](/sccm/core/servers/manage/use-alerts-and-the-status-system) voor meer informatie.

**Bestands- en databasereplicatie tussen sites controleren:**   
Zorg ervoor dat bestand en databasereplicatie tussen sites operationeel en actueel is. Vertragingen of achterstanden in een kunnen voorkomen dat een smooth, geslaagde update.
Voor databasereplicatie kunt u Replication Link Analyzer gebruiken om u te helpen bij het oplossen van problemen voordat u de update start.

Zie voor meer informatie [over de Replication Link Analyzer](/sccm/core/servers/manage/monitor-hierarchy-and-replication-infrastructure#BKMK_RLA) in de [hiërarchie- en replicatie-infrastructuur bewaken in System Center Configuration Manager](/sccm/core/servers/manage/monitor-hierarchy-and-replication-infrastructure) onderwerp.

**Installeer alle toepasselijke kritieke updates voor besturingssystemen op computers die als host fungeren voor de site, de Sitedatabaseserver en externe sitesysteemrollen:** Voordat u een update voor Configuration Manager installeert, installeert u alle kritieke updates voor elk toepasselijk sitesysteem. Als een update die u installeert een herstart is vereist, start u de desbetreffende computers opnieuw voordat u begint met de Configuration Manager-update.

**Databasereplica's voor beheerpunten op primaire sites uitschakelen:**   
Configuration Manager kan niet met succes bijwerken voor een primaire site die een databasereplica voor beheerpunten ingeschakeld heeft. Schakel databasereplicatie uit voordat u een update voor Configuration Manager installeert.

Zie [Databasereplica's voor beheerpunten voor System Center Configuration Manager](/sccm/core/servers/deploy/configure/database-replicas-for-management-points) voor meer informatie.

**SQL Server AlwaysOn-beschikbaarheidsgroepen op handmatige failover ingesteld:**   
Zorg ervoor dat de beschikbaarheidsgroep is ingesteld op handmatige failover voor de installatie van updates, zoals versie 1610. Nadat de site is bijgewerkt, kunt u failover worden automatisch herstellen. Zie voor meer informatie [SQL Server AlwaysOn voor een sitedatabase](/sccm/core/servers/deploy/configure/sql-server-alwayson-for-a-highly-available-site-database).

**Software-updatepunten met NLB's opnieuw configureren:**   
Configuration Manager kan een site die gebruikmaakt van een network load balancing (NLB) cluster host software-updatepunten niet bijwerken.

Als u NLB-clusters voor software-updatepunten gebruikt, moet u Windows PowerShell gebruiken om te verwijderen van het NLB-cluster.
Zie [Software-updates plannen in System Center Configuration Manager](/sccm/sum/plan-design/plan-for-software-updates) voor meer informatie.

**Alle siteonderhoudstaken op elke site uitschakelen voor de duur van de installatie van de update op die site:**   
Voordat u de update installeert, schakel alle siteonderhoudstaken die mogelijk worden uitgevoerd tijdens de tijd die het updateproces actief is. Dit omvat, maar is niet beperkt tot het volgende:

-   Back-upserver van site
-   Verouderde clientbewerkingen verwijderen
-   Verouderde detectiegegevens verwijderen

Wanneer een onderhoudstaak van de sitedatabase wordt uitgevoerd tijdens de installatie van updates, kan de installatie van de update mislukken. Voordat u een taak, registreert u het schema van de taak uitschakelt zodat u kunt de configuratie ervan herstellen kunt nadat de update is geïnstalleerd.

Zie voor meer informatie [onderhoudstaken voor System Center Configuration Manager](/sccm/core/servers/manage/maintenance-tasks) en [verwijzing voor het onderhoud van taken voor System Center Configuration Manager](/sccm/core/servers/manage/reference-for-maintenance-tasks).

**Maak een back-up van de sitedatabase op de centrale beheersite en primaire sites:** Voordat u een site bijwerkt, maakt u een back-up van de sitedatabase om ervoor te zorgen dat hebt u een goede back-up voor herstel na noodgevallen.

Zie voor meer informatie [back-up en herstel voor System Center Configuration Manager](/sccm/protect/understand/backup-and-recovery).

<!-- Removed from update guidance 6/6/2017
**Test the database upgrade on a copy of the most recent site database backup:** 
Before you update a System Center Configuration Manager central administration site or primary site, test the site database upgrade process on a copy of the site database.

-   We recommend that you test the site database upgrade process because when you upgrade a site, the site database might be modified.

-   Although a test database upgrade is not required, it can identify problems for the upgrade before your production database is affected.

-   A failed site database upgrade can render your site database inoperable and might require a site recovery to restore functionality.

-   Although the site database is shared between sites in a hierarchy, plan to test the database at each applicable site before you upgrade that site.

-   If you use database replicas for management points at a primary site, disable replication before you create the backup of the site database.

Configuration Manager does not support the backup of secondary sites nor does it support the test upgrade of a secondary site database.

Do not run a test database upgrade on the production site database. Doing so updates the site database and could render your site inoperable. For more information, see [Step 2: Test the database upgrade before installing an update](/sccm/core/servers/manage/install-in-console-updates#bkmk_step2) from **Before you install an in-console update**.
-->

**Clientproef plannen:**   
Wanneer u een update die de client wordt bijgewerkt installeert, kunt u die nieuwe clientupdate testen in een testomgeving voordat deze worden geïmplementeerd en alle actieve clients worden bijgewerkt.

Als u wilt profiteren van deze optie, moet u uw site ter ondersteuning van automatische upgrades voor preproductie voordat u de installatie van de update configureren.

Zie voor meer informatie [in System Center Configuration Manager-clients bijwerken](/sccm/core/clients/manage/upgrade/upgrade-clients) en [clientupgrades testen in pre-productieverzameling in System Center Configuration Manager](/sccm/core/clients/manage/upgrade/test-client-upgrades).

**Wilt u gebruiken servicewindows om te bepalen wanneer siteservers updates installeren:**   
U kunt servicewindows gebruiken voor het definiëren van een periode gedurende welke updates op een siteserver kunnen worden geïnstalleerd.

Hiermee kunt u bepalen wanneer de sites in uw hiërarchie de update installeren. Voorafgaand aan versie 1606, werden servicewindows onderhoudsvensters genoemd. Zie voor meer informatie [servicewindows voor siteservers Service](/sccm/core/servers/manage/service-windows).

**De setup prerequisite checker uitvoeren:**   
Wanneer de update wordt vermeld in de console als **beschikbaar,** kunt u de prerequisite checker onafhankelijk uitvoeren voordat u de update installeert. (Wanneer u de update op de site installeert, prerequisite checker opnieuw uitgevoerd.)

Voor een controle van vereisten uitvoeren vanaf de console, gaat u naar **beheer > overzicht > Cloudservices > Updates en onderhoud.** Vervolgens met de rechtermuisknop op **updatepakket voor Configuration Manager 1610**, en kies vervolgens **controle van vereisten uitvoeren**.

Zie voor meer informatie over het starten en vervolgens de controle op vereisten controleren **stap 3: De prerequisite checker uitvoeren voordat u een update installeert** in het onderwerp [updates in de console installeren voor System Center Configuration Manager](/sccm/core/servers/manage/install-in-console-updates).

> [!IMPORTANT]  
> Wanneer de prerequisite checker wordt uitgevoerd als onderdeel van de installatie van een update of onafhankelijk, werkt het proces enkele bronbestanden product die worden gebruikt voor siteonderhoudstaken. Daarom dat na het uitvoeren van de prerequisite checker maar voordat de update 1610 installeren als u wilt uitvoeren van een siteonderhoudstaak uitvoeren **Setupwpf.exe** (het installatieprogramma van Configuration Manager) vanaf de CD. Meest recente map op de siteserver.

**Sites bijwerken:**   
U bent nu klaar om de installatie van de update voor uw hiërarchie. Zie voor meer informatie over het installeren van de update [updates in de console installeren.](/sccm/core/servers/manage/install-in-console-updates#a-namebkmkinstalla-install-in-console-updates)

Het is raadzaam dat u installeren, de update buiten kantooruren voor elke site wilt wanneer het installatieproces van de update en de bijbehorende acties voor het installeren van de Siteonderdelen en sitesysteemrollen minimale invloed heeft op uw zakelijke activiteiten.

Zie [Updates voor System Center Configuration Manager](/sccm/core/servers/manage/updates) voor meer informatie.
