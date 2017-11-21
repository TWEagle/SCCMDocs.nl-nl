---
title: Controlelijst voor 1710 | System Center Configuration Manager
titleSuffix: Configuration Manager
description: Meer informatie over acties moet uitvoeren voordat u bijwerkt naar System Center Configuration Manager versie 1710.
ms.custom: na
ms.date: 11/20/2017
ms.reviewer: na
ms.suite: na
ms.prod: configuration-manager
ms.technology: configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 7e8ab8ca-41ef-467a-943b-a115d88cafe0
caps.latest.revision: 
author: Brenduns
ms.author: brenduns
manager: angrobe
ms.openlocfilehash: 57d53a66b5bf12796e9e37e7ab3d13c8a5c95d72
ms.sourcegitcommit: 12d0d53e47bbf1a0bbd85015b8404a44589d1e14
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 11/21/2017
---
# <a name="checklist-for-installing-update-1710-for-system-center-configuration-manager"></a>Controlelijst voor het installeren van update 1710 voor System Center Configuration Manager

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*

Wanneer u de huidige vertakking van System Center Configuration Manager gebruikt, kunt u de update in de console voor versie 1710 bijwerken van uw hiërarchie van een eerdere versie installeren.

Als u de update voor versie 1710, moet u een service connection point-sitesysteemrol op het hoogste niveau van uw hiërarchie. Dit kan zijn in de online of offline-modus. Nadat uw hiërarchie downloadt het updatepakket van Microsoft, kunt u deze vinden in de console onder **beheer &gt; overzicht &gt; Cloudservices &gt; Updates en onderhoud**.

-   Wanneer de update wordt vermeld als **beschikbaar**, de update is gereed om te installeren. Controleer de volgende informatie voordat u versie 1710 installeert, [over het installeren van update 1710](#about-installing-update-1710) en de [controlelijst](#checklist) voor configuraties die u moet voordat u de update start.

-   Als de update wordt weergegeven als **downloaden** en niet wijzigen, Controleer de **hman.log** en **dmpdownloader.log** op fouten.

    -   Als het dmpdownloader.log wordt aangegeven dat de dmpdownloader is in de slaapstand bevindt en een interval dat wacht voordat het controleren op updates, kunt u opnieuw starten de **SMS_Executive** service op de siteserver opnieuw opstarten van het downloaden van bestanden van de update opnieuw distribueren.

    -   Een andere algemene downloaden probleem treedt op wanneer de instellingen van proxyserver te voorkomen downloads vanaf dat <http://silverlight.dlservice.microsoft.com> en <http://download.microsoft.com>.

Zie voor meer informatie over het installeren van updates [In de console updates en onderhoud](/sccm/core/servers/manage/updates#a-namebkmkinconsolea-in-console-updates-and-servicing).

Zie voor meer informatie over de versies van de huidige vertakking [basislijn- en updateversies](/sccm/core/servers/manage/updates#bkmk_Baselines) in [Updates voor System Center Configuration Manager](/sccm/core/servers/manage/updates).

## <a name="about-installing-update-1710"></a>Over het installeren van update 1710

**Sites:**  
U installeert update 1710 op het hoogste niveau van uw hiërarchie. Dit betekent dat u de installatie starten vanuit uw centrale beheersite als er een of vanuit uw zelfstandige primaire site. Nadat de update is geïnstalleerd op de bovenste site, hebben de onderliggende sites de werking van de volgende update:

-   Onderliggende primaire sites de update automatisch geïnstalleerd als de centrale beheersite de installatie van de update is voltooid. U kunt servicewindows om te bepalen wanneer een site wordt geïnstalleerd voor de update. Zie voor meer informatie [servicewindows voor siteservers Service](/sccm/core/servers/manage/service-windows).

-   U moet elke secundaire site bij vanuit de Configuration Manager-console handmatig bijwerken nadat de bovenliggende primaire site de update-installatie is voltooid. Het automatisch bijwerken van secundaire siteservers wordt niet ondersteund.

**Sitesysteemrollen:**  
Wanneer een siteserver de update installeert, wordt de sitesysteemrollen die zijn geïnstalleerd op de site server-computer en die zijn geïnstalleerd op externe computers automatisch bijgewerkt. Voordat u de update installeert, zorg dat elke sitesysteemserver voldoet aan de vereisten voor het opnieuw met de nieuwe versie van de update.

**Configuration Manager-consoles:**   
De eerste keer dat u een Configuration Manager-console gebruikt nadat de update is voltooid, wordt u gevraagd om bij te werken die console. Om dit te doen, moet u setup van Configuration Manager uitvoeren op de computer die als host fungeert voor de console en kies vervolgens de optie de console bij te werken. U kunt installeren van de update naar de console beter niet uitstellen.

> [!IMPORTANT]  
> Wanneer u een update op de centrale beheersite installeert, worden op de hoogte van de volgende beperkingen en vertragingen die bestaan totdat alle onderliggende primaire sites ook de update-installatie te voltooien:    
> - **Clientupgrades** niet starten. Het gaat hierbij om automatische updates van clients en preproductieclients. U kunt preproductieclients naar productie Bovendien kan niet promoveren totdat de laatste site de update-installatie is voltooid. Nadat de laatste site de update-installatie is voltooid, begint clientupgrades op basis van uw configuratie-opties.   
> - **Nieuwe functies** u inschakelen met de update zijn niet beschikbaar. Zo wordt voorkomen dat de replicatie van gegevens met betrekking tot deze functie wordt verzonden naar een site die ondersteuning voor deze functie nog niet is geïnstalleerd. Nadat alle primaire sites de update installeren, het onderdeel is niet beschikbaar voor gebruik.   
> - **Koppelingen voor databasereplicatie** tussen de centrale beheersite en de onderliggende primaire sites weergegeven als niet-bijgewerkte. Deze wordt weergegeven in de status van de installatie van de update pack zoals de status voltooid met waarschuwing voor replicatie-initialisatie voor bewaking. In het knooppunt controle van de console, deze wordt weergegeven zoals *koppeling wordt geconfigureerd*.


## <a name="checklist"></a>Controlelijst

**Zorg ervoor dat alle sites een versie van System Center Configuration Manager dat ondersteunt naar 1710 bijwerken uitgevoerd:**   
Elke siteserver in de hiërarchie moet dezelfde versie van System Center Configuration Manager uitvoeren voordat u de installatie van update 1710 kunt starten. Als u wilt bijwerken naar 1710, moet u versie 1610, 1702 of 1706 gebruiken.

**Controleer de status van uw Software Assurance of gelijkwaardige abonnementsrechten:**   
U moet een actieve Software Assurance (SA)-overeenkomst voor het installeren van update 1710 hebben. Wanneer u deze update installeert de **Licensing** tabblad geeft de optie om te bevestigen dat uw **Software Assurance vervaldatum**.

Dit is een optionele waarde die u als een handige herinnering aan de vervaldatum van uw licentie opgeven kunt. Deze datum is zichtbaar wanneer u toekomstige updates installeert. Mogelijk hebt u eerder opgegeven deze waarde tijdens setup of installatie van een update of met behulp van de **Licensing** tabblad van de **hiërarchie-instellingen**, uit binnen de Configuration Manager-console.

Zie voor meer informatie [licenties en vertakkingen voor System Center Configuration Manager](/sccm/core/understand/learn-more-editions).

**Microsoft .NET-versies revisie geïnstalleerd op sitesysteemservers:** Wanneer een site deze update is geïnstalleerd, installeert Configuration Manager automatisch .NET Framework 4.5.2 op elke computer die als host fungeert voor een van de volgende sitesysteemrollen als .NET Framework 4.5 of hoger, niet al is geïnstalleerd:

-   Proxypunt voor inschrijving
-   Inschrijvingspunt
-   Beheerpunt
-   Serviceverbindingspunt

Deze installatie kunt u de sitesysteemserver in een opnieuw opstarten in behandeling zijnde status en het rapport fouten in de viewer voor Configuration Manager component status plaatsen. Bovendien kunnen .NET-toepassingen op de server willekeurige fouten optreden, totdat de server opnieuw is opgestart.

Zie voor meer informatie [Site and site system prerequisites](/sccm/core/plan-design/configs/site-and-site-system-prerequisites) (Vereisten voor sites en sitesystemen).

**Controleer de versie van de Windows Assessment and Deployment Kit (ADK) voor Windows 10** de Windows 10 ADK moet 1703 of hoger. (Zie voor meer informatie over ondersteunde versies van Windows ADK [Windows 10 ADK](/sccm/core/plan-design/configs/support-for-windows-10#windows-10-adk).) Als u de Windows ADK bijwerken moet, doen voordat u de update van Configuration Manager. Hierdoor worden dat de standaardopstartinstallatiekopieën automatisch bijgewerkt naar de nieuwste versie van Windows PE. (Aangepaste opstartinstallatiekopieën handmatig moeten worden bijgewerkt.)

Als u de site bijwerkt vóór de upgrade van Windows ADK, Zie [distributiepunten bijwerken met de installatiekopie](/sccm/osd/get-started/manage-boot-images#update-distribution-points-with-the-boot-image) voor verbeteringen aan dit proces in Configuration Manager versie 1710.

**Bekijk de site en hiërarchiestatus en controleer of er geen onopgeloste problemen zijn:** Voordat u een site bijwerkt, moet u alle operationele problemen voor de siteserver, de Sitedatabaseserver en de sitesysteemrollen die zijn geïnstalleerd op externe computers oplossen. De update van een site kan mislukken door bestaande operationele problemen.

Zie [Waarschuwingen en het statussysteem voor System Center Configuration Manager gebruiken](/sccm/core/servers/manage/use-alerts-and-the-status-system) voor meer informatie.

**Bestands- en databasereplicatie tussen sites controleren:**   
Zorg ervoor dat bestand en databasereplicatie tussen sites operationeel en actueel is. Vertragingen of achterstanden in een kunnen voorkomen dat een smooth, geslaagde update.
Voor databasereplicatie kunt u Replication Link Analyzer gebruiken om u te helpen bij het oplossen van problemen voordat u de update start.

Zie voor meer informatie [over de Replication Link Analyzer](/sccm/core/servers/manage/monitor-hierarchy-and-replication-infrastructure#BKMK_RLA) in de [hiërarchie- en replicatie-infrastructuur bewaken in System Center Configuration Manager](/sccm/core/servers/manage/monitor-hierarchy-and-replication-infrastructure) onderwerp.

**Installeer alle toepasselijke kritieke updates voor besturingssystemen op computers die als host fungeren voor de site, de Sitedatabaseserver en externe sitesysteemrollen:** Voordat u een update voor Configuration Manager installeert, installeert u alle kritieke updates voor elk toepasselijk sitesysteem. Als een update die u installeert, vereist dat de computer opnieuw wordt opgestart, start de desbetreffende computers dan opnieuw op voordat u de upgrade start.

**Databasereplica's voor beheerpunten op primaire sites uitschakelen:**   
Configuration Manager kan niet met succes bijwerken voor een primaire site die een databasereplica voor beheerpunten ingeschakeld heeft. Schakel databasereplicatie uit voordat u een update voor Configuration Manager installeert.

Zie [Databasereplica's voor beheerpunten voor System Center Configuration Manager](/sccm/core/servers/deploy/configure/database-replicas-for-management-points) voor meer informatie.

**SQL Server AlwaysOn-beschikbaarheidsgroepen op handmatige failover ingesteld:**   
Als u een beschikbaarheidsgroep gebruikt, zorg ervoor dat de beschikbaarheidsgroep is ingesteld op handmatige failover voordat u de installatie van updates. Nadat de site is bijgewerkt, kunt u failover worden automatisch herstellen. Zie voor meer informatie [SQL Server AlwaysOn voor een sitedatabase](/sccm/core/servers/deploy/configure/sql-server-alwayson-for-a-highly-available-site-database).

**Software-updatepunten met NLB's opnieuw configureren:**   
<!-- Support for NLBs is fully removed with 1702. When 1702 is no longer in support, this statement can drop -->
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

**Clientproef plannen:**   
Wanneer u een update die de client wordt bijgewerkt installeert, kunt u die nieuwe clientupdate testen in een testomgeving voordat deze worden geïmplementeerd en alle actieve clients worden bijgewerkt.

Als u wilt profiteren van deze optie, moet u uw site ter ondersteuning van automatische upgrades voor preproductie voordat u de installatie van de update configureren.

Zie voor meer informatie [in System Center Configuration Manager-clients bijwerken](/sccm/core/clients/manage/upgrade/upgrade-clients) en [clientupgrades testen in pre-productieverzameling in System Center Configuration Manager](/sccm/core/clients/manage/upgrade/test-client-upgrades).

**Wilt u gebruiken servicewindows om te bepalen wanneer siteservers updates installeren:**   
Servicewindows gebruiken voor het definiëren van een periode gedurende welke updates u moet een site server kan worden geïnstalleerd.

Hiermee kunt u bepalen wanneer de sites in uw hiërarchie de update installeren. Zie voor meer informatie [servicewindows voor siteservers Service](/sccm/core/servers/manage/service-windows).

**De setup prerequisite checker uitvoeren:**   
Wanneer de update wordt vermeld in de console als **beschikbaar,** kunt u de prerequisite checker onafhankelijk uitvoeren voordat u de update installeert. (Wanneer u de update op de site installeert, prerequisite checker opnieuw uitgevoerd.)

Voor een controle van vereisten uitvoeren vanaf de console, gaat u naar **beheer > overzicht > Cloudservices > Updates en onderhoud.** Vervolgens met de rechtermuisknop op **updatepakket voor Configuration Manager 1710**, en kies vervolgens **controle van vereisten uitvoeren**.

Zie voor meer informatie over het starten en vervolgens de controle op vereisten controleren **stap 3: De prerequisite checker uitvoeren voordat u een update installeert** in het onderwerp [updates in de console installeren voor System Center Configuration Manager](/sccm/core/servers/manage/install-in-console-updates).

> [!IMPORTANT]  
> Wanneer de prerequisite checker wordt uitgevoerd als onderdeel van de installatie van een update of onafhankelijk, werkt het proces enkele bronbestanden product die worden gebruikt voor siteonderhoudstaken. Daarom dat na het uitvoeren van de prerequisite checker maar voordat de update wordt geïnstalleerd als u wilt uitvoeren van een siteonderhoudstaak uitvoeren **Setupwpf.exe** (het installatieprogramma van Configuration Manager) vanaf de CD. Meest recente map op de siteserver.

**Sites bijwerken:**   
U bent nu klaar om de installatie van de update voor uw hiërarchie. Zie voor meer informatie over het installeren van de update [updates in de console installeren.](/sccm/core/servers/manage/install-in-console-updates#a-namebkmkinstalla-install-in-console-updates)

Het is raadzaam dat u installeren, de update buiten kantooruren voor elke site wilt wanneer het installatieproces van de update en de bijbehorende acties voor het installeren van de Siteonderdelen en sitesysteemrollen minimale invloed heeft op uw zakelijke activiteiten.

Zie [Updates voor System Center Configuration Manager](/sccm/core/servers/manage/updates) voor meer informatie.

## <a name="post-update-checklist"></a>Update van post controlelijst
Bekijk de volgende acties ondernemen nadat de installatie van de update is voltooid.
1.  Zorg ervoor dat site-naar-site-replicatie actief is. In de console weergeven **bewaking** > **sitehiërarchie**, en **bewaking** > **databasereplicatie** nakijken op aanwijzingen van problemen of een bevestiging dat koppelingen voor databasereplicatie actief zijn.
2.  Zorg ervoor dat elke siteserver en de sitesysteemrol is bijgewerkt naar versie 1710. In de console kunt u de optionele kolom toevoegen **versie** bij het weergeven van sommige knooppunten inclusief **Sites** en **distributiepunten**.

 Indien nodig, wordt automatisch een sitesysteemrol opnieuw als u wilt bijwerken naar de nieuwe versie. U kunt opnieuw starten van externe sitesystemen die niet bijgewerkt.
3.  Databasereplica voor beheerpunten op primaire sites die u uitgeschakeld voordat u de update start opnieuw configureren.
4.  Configureer databaseonderhoudstaken die u hebt uitgeschakeld voordat u de update start opnieuw.
5.  Als u testen voordat u de update installeert van de client hebt geconfigureerd, kunt u clients per abonnement dat u hebt gemaakt upgraden.
