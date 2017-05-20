---
title: Controlelijst voor 1702 | System Center Configuration Manager
description: Meer informatie over de acties te ondernemen voordat u bijwerkt naar System Center Configuration Manager versie 1702.
ms.custom: na
ms.date: 05/02/2017
ms.reviewer: na
ms.suite: na
ms.prod: configuration-manager
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: b587779e-1bd3-4ee3-8146-8e31f53499bd
caps.latest.revision: 7
author: Brenduns
ms.author: brenduns
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 90775fcf2549080a43e9c1606caa79d9eb90a89c
ms.openlocfilehash: c4ace452d62d4fa08f4457cb1735718ca4bd016d
ms.contentlocale: nl-nl
ms.lasthandoff: 05/17/2017

---
# <a name="checklist-for-installing-update-1702-for-system-center-configuration-manager"></a>Controlelijst voor het installeren van update 1702 voor System Center Configuration Manager

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*

Wanneer u de huidige vertakking van System Center Configuration Manager gebruikt, kunt u de update in de console voor versie 1702 bijwerken van uw hiërarchie van een eerdere versie installeren.

> [!TIP]  
Versie 1702 is ook beschikbaar als [basislijn media](/sccm/core/servers/manage/updates#a-namebkmkbaselinesa-baseline-and-update-versions) waarmee u kunt de eerste site van een nieuwe hiërarchie te installeren.

Als u de update voor versie 1702, moet u een service connection point-sitesysteemrol op de site op het hoogste niveau van uw hiërarchie. Dit kan zijn in de online of offline modus. Nadat uw hiërarchie het updatepakket van Microsoft downloadt, u kunt deze vinden in de console onder **beheer &gt; overzicht &gt; Cloudservices &gt; Updates en onderhoud**.

-   Wanneer de update wordt vermeld als **beschikbaar**, de update is gereed om te installeren. De volgende informatie bekijken voordat u versie 1702 installeert, [over het installeren van update 1702](#about-installing-update-1702) en de [controlelijst](#checklist) configuraties voor het maken voordat u de update.

-   Als de update wordt weergegeven als **downloaden** en niet wijzigen, Controleer de **hman.log** en **dmpdownloader.log** op fouten.

    -   Als de dmpdownloader.log geeft aan dat het proces dmpdownloader is in de slaapstand bevinden en wachten op een interval voor voordat controleren op updates, kunt u opnieuw opstarten de **SMS_Executive** service op de siteserver verzonden om het downloaden van de updatebestanden herdistributie opnieuw starten.

    -   Een andere algemene downloaden probleem treedt op wanneer de instellingen van proxyserver te voorkomen downloads vanaf dat <http://silverlight.dlservice.microsoft.com> en <http://download.microsoft.com>.

Zie voor meer informatie over het installeren van updates [-console updates en onderhoud](/sccm/core/servers/manage/updates#a-namebkmkinconsolea-in-console-updates-and-servicing).

Zie voor meer informatie over de versies van de huidige vertakking [basislijn en update versies](/sccm/core/servers/manage/updates#bkmk_Baselines) in [voor System Center Configuration Manager-Updates](/sccm/core/servers/manage/updates).

## <a name="about-installing-update-1702"></a>Over het installeren van update 1702

**Sites:**  
U installeert update 1702 op de site op het hoogste niveau van uw hiërarchie. Dit betekent dat u de installatie starten vanuit uw centrale beheersite als er een hebt of vanuit uw zelfstandige primaire site. Nadat de update is geïnstalleerd op de site op hoogste niveau, hebben onderliggende sites in de werking van de volgende update:

-   Onderliggende primaire sites de update automatisch geïnstalleerd nadat de installatie van de update door de centrale beheersite is voltooid. U kunt windows service om te bepalen wanneer een site de update is geïnstalleerd. Zie voor meer informatie [windows voor siteservers Service](/sccm/core/servers/manage/service-windows).

-   Nadat de primaire bovenliggende site de update-installatie is voltooid, moet u handmatig elke secundaire site vanuit de Configuration Manager-console bijwerken. Het automatisch bijwerken van secundaire siteservers wordt niet ondersteund.

**Sitesysteemrollen:**  
Wanneer een siteserver de update installeert, de sitesysteemrollen die op de siteservercomputer en toepassingen die zijn geïnstalleerd op externe computers zijn geïnstalleerd automatisch bijgewerkt. Voordat u de update installeert, zorg dat elke sitesysteemserver voldoet aan de vereisten voor het opnieuw met de nieuwe versie van de update.

**Configuration Manager-consoles:**   
De eerste keer dat u een Configuration Manager-console gebruiken nadat de update is voltooid, wordt u gevraagd om bij te werken die console. Om dit te doen, moet u Configuration Manager setup uitvoert op de computer die als host fungeert voor de console en kiest u de optie de console bijwerken. U kunt installeren van de update naar de console beter niet uitstellen.

> [!IMPORTANT]  
> Wanneer u een update op de centrale beheersite installeert, worden op de hoogte van de volgende beperkingen en vertragingen die bestaan totdat alle onderliggende primaire sites ook de installatie van updates:    
> - **Clientupgrades** worden niet gestart. Dit omvat automatische updates van clients en test-clients. Bovendien kan niet bevordert u clients test naar productie totdat de laatste site zijn installatie van de update is voltooid. Nadat de laatste site zijn de update-installatie is voltooid, begint clientupdates op basis van uw configuratie-opties.   
> - **Nieuwe functies** u inschakelen met de update zijn niet beschikbaar. Hiermee wordt voorkomen dat de replicatie van gegevens met betrekking tot deze functie worden verzonden naar een site die ondersteuning voor die functie nog niet is geïnstalleerd. Nadat alle primaire sites de update installeren, het onderdeel is niet beschikbaar voor gebruik.   
> - **Replicatiekoppelingen** tussen de centrale beheersite en de onderliggende primaire sites weergegeven als niet bijgewerkt. Hiermee worden weergegeven in de status van de installatie van de update pack als de status voltooid met waarschuwing voor replicatie-initialisatie voor bewaking. In het knooppunt controle van de console deze wordt weergegeven zoals *koppeling wordt geconfigureerd*.



## <a name="checklist"></a>Controlelijst

**Zorg ervoor dat alle sites een versie van System Center Configuration Manager dat ondersteunt naar 1702 bijwerken uitvoeren:**   
Elke siteserver in de hiërarchie moet dezelfde versie van System Center Configuration Manager uitvoeren voordat u kunt de installatie van update 1702. Als u wilt bijwerken naar 1702, moet u versie 1602, 1606 of 1610 gebruiken.

**Controleer de status van uw Software Assurance of gelijkwaardige abonnementsrechten:**   
U moet een actief Software Assurance (SA) overeenkomst installatie van update 1702 hebben. Als u deze update installeert de **volumelicenties** tabblad geeft de optie om te bevestigen uw **Software Assurance-vervaldatum**.

Dit is een optionele waarde die u als een handige herinnering aan de verloopdatum van uw licentie opgeven kunt. Deze datum is zichtbaar wanneer u toekomstige updates installeert. U kunt eerder opgegeven hebben deze waarde tijdens setup of installatie van een update of met behulp van de **volumelicenties** tabblad van het **hiërarchie-instellingen**, uit in de Configuration Manager-console.

Zie voor meer informatie [volumelicenties en vertakkingen voor System Center Configuration Manager](/sccm/core/understand/learn-more-editions).

**Microsoft .NET-versies revisie geïnstalleerd op sitesysteemservers:** Als een site deze update is geïnstalleerd, installeert Configuration Manager automatisch .NET Framework 4.5.2 op elke computer die als host fungeert voor een van de volgende sitesysteemrollen als .NET Framework 4.5 of later is niet geïnstalleerd:

-   Proxypunt voor inschrijving
-   Inschrijvingspunt
-   Beheerpunt
-   Serviceverbindingspunt

Deze installatie kan de sitesysteemserver in een opnieuw opstarten in behandeling zijnde status en het rapport fouten in de viewer van Configuration Manager component status geplaatst. Daarnaast .NET-toepassingen op de server te maken kunnen krijgen willekeurig mislukken totdat de server opnieuw is opgestart.

Zie voor meer informatie [Site and site system prerequisites](/sccm/core/plan-design/configs/site-and-site-system-prerequisites) (Vereisten voor sites en sitesystemen).

**Controleer de versie van Windows Assessment and Deployment Kit (ADK) voor Windows 10** 10 met de Windows ADK moet 1607 of hoger. Als u de ADK bijwerken moet, doen voordat u begint met bijwerken van Configuration Manager. Hiermee zorgt u dat de standaardopstartinstallatiekopieën worden automatisch bijgewerkt naar de nieuwste versie van Windows PE. (Aangepaste opstartinstallatiekopieën handmatig moeten worden bijgewerkt.)

Als u de site bijwerken voordat u de ADK bijwerken, raadpleegt u de blog [Configuration Manager en de Windows ADK voor Windows 10 versie 1607](https://blogs.technet.microsoft.com/enterprisemobility/2016/09/09/configuration-manager-and-the-windows-adk-for-windows-10-version-1607/) voor een script dat kan worden gebruikt voor het genereren van de opstartinstallatiekopieën ondernemen.

**Bekijk de site en hiërarchiestatus en controleer of er geen onopgeloste problemen:** Voordat u een site bijwerkt, moet u alle operationele problemen voor de siteserver, de Sitedatabaseserver en de sitesysteemrollen die op externe computers zijn geïnstalleerd oplossen. De update van een site kan mislukken door bestaande operationele problemen.

Zie [Waarschuwingen en het statussysteem voor System Center Configuration Manager gebruiken](/sccm/core/servers/manage/use-alerts-and-the-status-system) voor meer informatie.

**Controleer de bestands- en replicatie tussen sites:**   
Zorg ervoor dat bestand en databasereplicatie tussen sites operationele en actueel. Vertragingen of achterstanden in ofwel kunnen voorkomen dat een goede geslaagde update.
Voor databasereplicatie kunt u Replication Link Analyzer gebruiken om u te helpen bij het oplossen van problemen voordat u de update start.

Zie voor meer informatie [over de Replication Link Analyzer](/sccm/core/servers/manage/monitor-hierarchy-and-replication-infrastructure#BKMK_RLA) in de [controleren-hiërarchie en de replicatie van de infrastructuur in System Center Configuration Manager](/sccm/core/servers/manage/monitor-hierarchy-and-replication-infrastructure) onderwerp.

**Installeer alle toepasselijke kritieke updates voor besturingssystemen op computers die als host fungeren voor de site, de Sitedatabaseserver en externe sitesysteemrollen:** Voordat u een update voor Configuration Manager installeert, installeert u alle kritieke updates voor elk toepasselijk sitesysteem. Als een update die u installeert, vereist dat de computer opnieuw wordt opgestart, start de desbetreffende computers dan opnieuw op voordat u de upgrade start.

**Databasereplica's voor beheerpunten op primaire sites uitschakelen:**   
Configuration Manager kan een primaire site die een databasereplica voor beheerpunten ingeschakeld heeft niet bijwerken. Schakel databasereplicatie uit voordat u:

-   Maak een back-up van de sitedatabase om de database-upgrade te testen.
-   Installatie van een update voor Configuration Manager.

Zie [Databasereplica's voor beheerpunten voor System Center Configuration Manager](/sccm/core/servers/deploy/configure/database-replicas-for-management-points) voor meer informatie.

**SQL Server AlwaysOn-beschikbaarheidsgroepen wilt handmatige failover instellen:**   
Als u een beschikbaarheidsgroep, zorg ervoor dat de beschikbaarheidsgroep is ingesteld op handmatige failover voordat u de installatie van updates begint. Nadat de site is bijgewerkt, kunt u failover worden automatisch herstellen. Zie voor meer informatie [SQL Server AlwaysOn van een sitedatabase](/sccm/core/servers/deploy/configure/sql-server-alwayson-for-a-highly-available-site-database).

**Software-updatepunten met NLB opnieuw:**   
Configuration Manager kan een site die gebruikmaakt van een network load balancing (NLB) cluster host software-updatepunten niet bijwerken.

Als u NLB-clusters voor software-updatepunten gebruikt, moet u Windows PowerShell gebruiken om te verwijderen van het NLB-cluster.
Zie [Software-updates plannen in System Center Configuration Manager](/sccm/sum/plan-design/plan-for-software-updates) voor meer informatie.

**Schakel alle siteonderhoudstaken op elke site tijdens de duur van de installatie van updates op die site:**   
Voordat u de update installeren, schakel alle siteonderhoudstaken die mogelijk worden uitgevoerd tijdens de tijd die het updateproces actief is. Dit omvat, maar is niet beperkt tot het volgende:

-   Back-upserver van site
-   Verouderde clientbewerkingen verwijderen
-   Verouderde detectiegegevens verwijderen

Wanneer een onderhoudstaak van de sitedatabase wordt uitgevoerd tijdens de installatie van updates, kan de installatie van de update mislukken. Voordat u een taak, registreert u het schema van de taak uitschakelt zodat u de configuratie ervan herstellen kunt nadat de update is geïnstalleerd.

Zie voor meer informatie [onderhoudstaken voor System Center Configuration Manager](/sccm/core/servers/manage/maintenance-tasks) en [verwijzing voor het onderhoud van taken voor System Center Configuration Manager](/sccm/core/servers/manage/reference-for-maintenance-tasks).

**Maak een back-up van de sitedatabase op de centrale beheersite en primaire sites:** Voordat u een site bijwerkt, maakt u een back-up van de sitedatabase om ervoor te zorgen dat hebt u een geslaagde back-up moet worden gebruikt voor herstel na noodgevallen.

Zie voor meer informatie [back-up en herstel voor System Center Configuration Manager](/sccm/protect/understand/backup-and-recovery).

**Test het database-upgrade op een kopie van de databaseback-up van de meest recente site:** Voordat u een site voor Centraal beheer van System Center Configuration Manager of de primaire site hebt bijgewerkt, kunt u het upgradeproces van de sitedatabase op een kopie van de sitedatabase kunt testen.

-   Het is raadzaam om het upgradeproces van de site te testen, omdat wanneer u een site upgradet, de sitedatabase kan worden gewijzigd.

-   Hoewel een testdatabase-upgrade niet vereist is, kunt u problemen voor de upgrade detecteren voordat uw productiedatabase Hierdoor wordt beïnvloed.

-   Een mislukte upgrade van de sitedatabase kan leiden tot een onbruikbare sitedatabase, waardoor u mogelijk een site recovery moet uitvoeren om de functionaliteit te herstellen.

-   Hoewel de sitedatabase wordt gedeeld tussen sites in een hiërarchie, plan een test voor de database op iedere betreffende site voordat u die site upgradet.

-   Als u Databasereplica's voor beheerpunten op een primaire site, schakelt u replicatie uit voordat u de back-up van de sitedatabase maakt.

Configuration Manager biedt geen ondersteuning voor de back-up van secundaire sites noch ondersteunen de testupgrade van een secundaire sitedatabase.

Voer een testdatabase-upgrade niet op de productie-sitedatabase. Dit leidt tot een update van de sitedatabase en kan tot gevolg hebben dat uw site onbruikbaar wordt. Zie voor meer informatie [stap 2: Testen van de upgrade van de database voordat u een update installeert](/sccm/core/servers/manage/install-in-console-updates#bkmk_step2) van **voordat u een update in de console**.

**Plannen voor haalbaarheidsonderzoek client:**   
Wanneer u een update die updates van de client installeert, kunt u die nieuwe clientupdate testen in een testomgeving voordat deze worden geïmplementeerd en alle actieve clients worden bijgewerkt.

Als u wilt profiteren van deze optie, moet u uw site voor ondersteuning van automatische updates voor de test voordat u begint de installatie van de update.

Zie voor meer informatie [in System Center Configuration Manager-clients bijwerken](/sccm/core/clients/manage/upgrade/upgrade-clients) en [clientupgrades testen in een pre-productieverzameling in System Center Configuration Manager](/sccm/core/clients/manage/upgrade/test-client-upgrades).

**Plannen voor het gebruik van windows service om te bepalen wanneer siteservers updates installeren:**   
Windows service gebruiken voor het definiëren van een periode gedurende welke updates aan een site server kan worden geïnstalleerd.

Hiermee kunt u bepalen wanneer de sites in uw hiërarchie de update installeren. Zie voor meer informatie [windows voor siteservers Service](/sccm/core/servers/manage/service-windows).

**Setup prerequisite checker uitvoert:**   
Wanneer de update wordt weergegeven in de console, gezien **beschikbaar,** u kunt de prerequisite checker onafhankelijk uitvoeren voordat u de update installeert. (Wanneer u de update op de site installeren, prerequisite checker opnieuw uitgevoerd.)

Voor een controle van vereisten uitvoeren vanaf de console, gaat u naar **beheer > overzicht > Cloudservices > Updates en onderhoud.** Vervolgens met de rechtermuisknop op **updatepakket voor Configuration Manager 1702**, en kies vervolgens **controle van vereisten uitvoeren**.

Zie voor meer informatie over het starten en vervolgens de controle op vereisten controleren **stap 3: De prerequisite checker uitvoeren voordat u een update installeert** in het onderwerp [-console updates installeren voor System Center Configuration Manager](/sccm/core/servers/manage/install-in-console-updates).

> [!IMPORTANT]  
> Wanneer de vereistencontrole wordt uitgevoerd, afzonderlijk of als onderdeel van een installatie van updates, werkt het proces enkele product bronbestanden die worden gebruikt voor siteonderhoudstaken. Daarom dat na het uitvoeren van de prerequisite checker maar voordat de update installeren als u wilt uitvoeren van een siteonderhoudstaak uitgevoerd **Setupwpf.exe** (installatie van Configuration Manager) vanaf de CD. Meest recente map op de siteserver.

**Sites bijwerken:**   
U bent nu klaar om de installatie van de update voor uw hiërarchie. Zie voor meer informatie over het installeren van de update [-console updates installeren.](/sccm/core/servers/manage/install-in-console-updates#a-namebkmkinstalla-install-in-console-updates)

Het is raadzaam dat u van plan bent de update te installeren buiten kantooruren voor elke site wanneer het proces om de update en de bijbehorende acties opnieuw installeren van site-onderdelen en sitesysteemrollen te installeren wordt de minste invloed op uw zakelijke activiteiten hebben.

Zie [Updates voor System Center Configuration Manager](/sccm/core/servers/manage/updates) voor meer informatie.

## <a name="post-update-checklist"></a>Update van post controlelijst
Bekijk de volgende acties ondernemen na de installatie van de update is voltooid.
1.    Zorg ervoor dat replicatie tussen sites actief is. In de console weergeven **bewaking** > **sitehiërarchie**, en **bewaking** > **databasereplicatie** voor aanwijzingen voor problemen of een bevestiging replicatiekoppelingen actief zijn.
2.    Zorg ervoor dat elke siteserver en de sitesysteemrol is bijgewerkt naar versie 1702. In de console kunt u de optionele kolom toevoegen **versie** bij het weergeven van sommige knooppunten inclusief **Sites** en **distributiepunten**.

 Indien nodig, wordt automatisch een sitesysteemrol opnieuw om bij te werken naar de nieuwe versie. Houd rekening met externe site-systemen die niet met succes bijwerken opnieuw te starten.
3.    Databasereplica's voor beheerpunten op primaire sites die u uitgeschakeld voordat u de update opnieuw configureren.
4.  De configuratie van databaseonderhoudstaken die u uitgeschakeld voordat de update gestart.
5.    Als u geconfigureerd client haalbaarheidsonderzoek voordat de update te installeren, upgraden clients per het plan dat u hebt gemaakt.

