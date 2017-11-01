---
title: Grensgroepen voor 1511, 1602 en 1606
titleSuffix: Configuration Manager
description: Gebruik grensgroepen met Configuration Manager versie 1511, 1602 en 1606.
ms.custom: na
ms.date: 2/8/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: configmgr-other
ms.tgt_pltfrm: na
ms.topic: get-started-article
ms.assetid: dec1e0d7-5864-43a8-9f56-413923b3914e
caps.latest.revision: "10"
author: Brenduns
ms.author: brenduns
manager: angrobe
ms.openlocfilehash: ffd2ffe4363d33e5b61c8da76f7e14b2d6b874bb
ms.sourcegitcommit: c236214b2fcc13dae7bad96d7fb33f692868191d
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/12/2017
---
# <a name="boundary-groups-for-system-center-configuration-manager-version-1511-1602-and-1606"></a>Grensgroepen voor System Center Configuration Manager versie 1511, 1602 en 1606

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*
<!-- This topic drops from TOC with the release of version 1706 -->

De informatie in dit onderwerp is specifiek voor het gebruik van grensgroepen met versie 1511, 1602 en 1606 van System Center Configuration Manager.
Als u versie 1610 of hoger gebruikt, Zie [grensgroepen configureren](/sccm/core/servers/deploy/configure/boundary-groups) voor informatie over het gebruik van de vernieuwde grensgroepen.  


##  <a name="BKMK_BoundaryGroups"></a> Boundary groups  
 U maakt grensgroepen om gerelateerde netwerklocaties (grenzen) logisch te groeperen, zodat uw infrastructuur eenvoudiger kan worden beheerd. U moet grenzen eerst toewijzen aan grensgroepen voordat u de grensgroep kunt gebruiken. Clients gebruiken de configuratie van de grensgroep voor:  

-   Automatische sitetoewijzing  

-   Inhoudslocatie  

-   Voorkeursbeheerpunten

    Als u voorkeursbeheerpunten gebruiken wilt, moet u deze optie voor de hiërarchie en niet vanuit inschakelen configuratie van de grensgroep. Zie de *gebruik van voorkeursbeheerpunten inschakelen* procedure verderop in dit onderwerp.  

Wanneer u grensgroepen instelt, moet u een of meer grenzen aan de grensgroep toevoegen. Vervolgens configureert u aanvullende instellingen voor gebruik door clients die zich bevinden op die grenzen.  

#### <a name="to-create-a-boundary-group"></a>Een grensgroep maken  

1.  Kies in de Configuration Manager-console **beheer** > **Hiërarchieconfiguratie** >  **Grensgroepen**.  

2.  Op de **Start** tabblad, in de **maken** groep, kiest u **Grensgroep maken**.  

3.  In de **Grensgroep maken** dialoogvenster Kies de **algemene** tabblad en voer vervolgens een **naam** voor deze grensgroep.  

4.  Kies **OK** om op te slaan van de nieuwe grensgroep.  

#### <a name="to-set-up-a-boundary-group"></a>Voor het instellen van een grensgroep  

1.  Kies in de Configuration Manager-console **beheer** > **Hiërarchieconfiguratie** >  **Grensgroepen**.  

2.  Kies de grensgroep die u wilt wijzigen.  

3.  Op de **Start** tabblad, in de **eigenschappen** groep, kiest u **eigenschappen**.  

4.  In de **eigenschappen** in het dialoogvenster voor de grensgroep, kies de **algemene** tab om te wijzigen van de grenzen die lid van deze grensgroep zijn:  

    -   Als u wilt toevoegen grenzen, kies **toevoegen**, schakel het selectievakje in voor een of meer grenzen in en kies vervolgens **OK**.  

    -   Als u wilt verwijderen van grenzen, selecteert u de grens en kies vervolgens **verwijderen**.  

5.  Kies de **verwijzingen** tabblad de sitetoewijzing en een gekoppelde site server systeemconfiguratie wijzigen:  

    -   Om deze grensgroep voor gebruik door clients voor sitetoewijzing, het selectievakje in voor **deze grensgroep gebruiken voor sitetoewijzing**, en kies vervolgens een site uit de **toegewezen site** vervolgkeuzelijst.  

    -   Voor het instellen van de beschikbare sitesysteemservers die gekoppeld aan deze grensgroep zijn:  

    1.  Kies **toevoegen**, en controleert u het selectievakje voor een of meer servers. De servers worden als gekoppelde sitesysteemservers toegevoegd aan deze grensgroep. Alleen servers waarop ondersteunde sitesysteemrollen zijn geïnstalleerd, zijn beschikbaar.  

        > [!NOTE]  
        >  U kunt een combinatie van beschikbare sitesystemen van alle sites in de hiërarchie selecteren. Geselecteerde sitesystemen worden weergegeven op het tabblad **Sitesystemen** in de eigenschappen van elke grens die deel uitmaakt van deze grensgroep.  

    2.  Als een server uit deze grensgroep wilt verwijderen, kiest u de server en kies vervolgens **verwijderen**.  

        > [!NOTE]  
        >  Als u wilt stoppen met gebruik van deze grensgroep voor het koppelen van sitesystemen, moet u alle servers die worden vermeld als gekoppelde sitesysteemservers verwijderen.  

    3.  Als u wilt wijzigen van de netwerkverbindingssnelheid voor een sitesysteemserver voor deze grensgroep, kiest u de server en kies vervolgens **verbinding wijzigen**.  

         De verbindingssnelheid voor elk sitesysteem is standaard **snel**, maar u kunt de snelheid met **langzaam**. De netwerkverbindingssnelheid en configuratie van een implementatie bepalen of een client inhoud kan downloaden van de server.  

6.  Kies **OK** eigenschappen van de grensgroep te sluiten en de configuratie op te slaan.  

#### <a name="to-associate-a-content-deployment-server-or-management-point-with-a-boundary-group"></a>Een inhoudsimplementatieserver of beheerpunt koppelen aan een grensgroep  

1.  Kies in de Configuration Manager-console **beheer** > **Hiërarchieconfiguratie** >  **Grensgroepen**.  

2.  Kies de grensgroep die u wilt wijzigen.  

3.  Op de **Start** tabblad, in de **eigenschappen** groep, kiest u **eigenschappen**.  

4.  In de **eigenschappen** in het dialoogvenster voor de grensgroep, kies de **verwijzingen** tabblad.  

5.  Onder **sitesysteemservers selecteren**, kies **toevoegen**, schakel het selectievakje in voor de sitesysteemservers die u wilt koppelen aan deze grensgroep en kies vervolgens **OK**.  

6.  Kies **OK** naar het dialoogvenster sluiten en de configuratie van de grensgroep op te slaan.  

#### <a name="to-enable-use-of-preferred-management-points"></a>Gebruik van voorkeursbeheerpunten inschakelen  

1.  Kies in de Configuration Manager-console **beheer** > **siteconfiguratie** > **Sites**, en klik op de **Start** Kies **hiërarchie-instellingen**.  

2.  Op de **algemene** tabblad van **hiërarchie-instellingen**, kies **Clients gebruiken liever beheerpunten die zijn opgegeven in grensgroepen**.  

3.  Kies **OK** in het dialoogvenster sluiten en de configuratie op te slaan.  

#### <a name="to-set-up-a-fallback-site-for-automatic-site-assignment"></a>Voor het instellen van een terugvalsite voor automatische sitetoewijzing  

1.  Kies in de Configuration Manager-console **beheer** > **siteconfiguratie** >  **Sites**.  

2.  Op de **Start** tabblad, in de **Sites** groep, kiest u **hiërarchie-instellingen**.  

3.  Op de **algemene** tabblad, controleert u het selectievakje voor **een terugvalsite gebruiken**, en kies vervolgens een site uit de **terugvalsite** vervolgkeuzelijst.  

4.  Kies **OK** aan de configuratie op te slaan.  

 In de volgende secties vindt u meer informatie over de configuratie van grensgroepen.  

###  <a name="BKMK_BoundarySiteAssignment"></a> Sitetoewijzing  
 U kunt elke grensgroep met een toegewezen site voor clients instellen.  

-   Een nieuw geïnstalleerde client die automatische sitetoewijzing gebruikt zal lid worden van de toegewezen site van een grensgroep die de huidige netwerklocatie van de client heeft.  

-   Een client die toegewezen aan een site wordt de sitetoewijzing niet gewijzigd wanneer de client de netwerklocatie ervan wordt gewijzigd. Bijvoorbeeld, als de client naar een netwerklocatie die wordt vertegenwoordigd door een grens in een grensgroep met een andere sitetoewijzing roamt, blijft van de client toegewezen site ongewijzigd.  

-   Wanneer door Active Directory-systeemdetectie een nieuwe bron wordt gedetecteerd, worden netwerkgegevens voor de gedetecteerde bron geëvalueerd op basis van de grenzen in grensgroepen. In dit proces wordt de nieuwe bron aan een toegewezen site gekoppeld voor de push-clientinstallatie.  

-   Wanneer een grens lid is van meerdere grensgroepen met verschillende toegewezen sites, selecteer clients willekeurig een van de sites.  

-   Wijzigingen in de toegewezen site van een grensgroep gelden alleen voor nieuwe toewijzingen van de site. Clients die eerder zijn toegewezen aan een site evalueren hun sitetoewijzing opnieuw op basis van wijzigingen in de configuratie van een grensgroep (of hun eigen netwerklocatie) niet.  

Zie voor meer informatie over clientsitetoewijzing [automatische sitetoewijzing gebruiken voor Computers](../../../../core/clients/deploy/assign-clients-to-a-site.md#BKMK_AutomaticAssignment) in [clients toewijzen aan een site in System Center Configuration Manager](../../../../core/clients/deploy/assign-clients-to-a-site.md).  

###  <a name="BKMK_BoundaryContentLocation"></a> Inhoudslocatie  
 U kunt elke grensgroep met een of meer distributiepunten en statusmigratiepunten instellen en u kunt dezelfde distributiepunten en statusmigratiepunten koppelen aan meerdere grensgroepen.  

-   **Tijdens de softwaredistributie**vragen clients een locatie aan voor de implementatie-inhoud. Configuration Manager stuurt de client een lijst met distributiepunten die zijn gekoppeld aan elke grensgroep die de huidige netwerklocatie van de client bevat.  

-   **Tijdens de implementatie van besturingssysteem**, vragen clients een locatie te verzenden of ontvangen van hun migratiestatusinformatie. Configuration Manager stuurt de client een lijst met statusmigratiepunten die zijn gekoppeld aan elke grensgroep die de huidige netwerklocatie van de client bevat.  

Dit gedrag kan de client de dichtstbijzijnde server waarvan de inhoud overbrengen selecteren of statusmigratie-informatie.  

###  <a name="BKMK_PreferredMP"></a> Voorkeursbeheerpunten  
 Voorkeursbeheerpunten kunnen een client een beheerpunt dat is gekoppeld aan de huidige netwerklocatie (grens) te identificeren.  

-   Een client probeert te gebruiken van een voorkeursbeheerpunt van de toegewezen site voordat deze maakt gebruik van een beheerpunt vanuit zijn toegewezen site die niet is ingesteld als voorkeursbeheerpunt.  

-   Om deze optie gebruikt, moet u voor de hiërarchie inschakelen en grensgroepen ingesteld op de afzonderlijke primaire sites op te nemen van de beheerpunten die gekoppeld aan deze grensgroep gekoppelde grenzen worden moeten  

-   Wanneer voorkeursbeheerpunten zijn ingesteld en een client de lijst van management ordent verwijst, de client plaatsen voorkeur beheerpunten boven aan de lijst met toegewezen beheerpunten, waaronder alle beheerpunten van de client toegewezen site.  

> [!NOTE]  
>  Wanneer een client roamt, zoals wanneer een laptop verzonden naar een externe locatie en de netwerklocatie verandert deze mogelijk gebruiken een beheerpunt (of proxybeheerpunt) van de lokale site op de nieuwe locatie voordat wordt geprobeerd een beheerpunt vanuit zijn toegewezen site (waaronder de voorkeursbeheerpunten) gebruiken.  Zie [begrijpen hoe clients siteresources en -services voor System Center Configuration Manager vinden](../../../../core/plan-design/hierarchy/understand-how-clients-find-site-resources-and-services.md) voor meer informatie.  

###  <a name="BKMK_BoundaryOverlap"></a> Overlappende grenzen  
 Configuration Manager ondersteunt configuraties met overlappende grenzen voor Inhoudslocatie:  

-   **Wanneer een client inhoud aanvraagt**, en de clientnetwerklocatie tot meerdere grensgroepen behoort, Configuration Manager stuurt de client een lijst van alle distributiepunten die de inhoud bevatten.  

-   **Wanneer een client een server te verzenden of ontvangen van statusmigratie-informatie opvraagt**, en de clientnetwerklocatie tot meerdere grensgroepen behoort, Configuration Manager stuurt de client een lijst met alle statusmigratiepunten die zijn gekoppeld aan een grensgroep die de huidige netwerklocatie van de client bevat.  

Dit gedrag kan de client de dichtstbijzijnde server waarvan de inhoud overbrengen selecteren of statusmigratie-informatie.  

###  <a name="BKMK_BoudnaryNetworkSpeed"></a> Netwerkverbindingssnelheid  
 U kunt de netwerkverbindingssnelheid instellen voor elke sitesysteemserver in een grensgroep. Deze instelling geldt voor clients die verbinding met een sitesysteem op basis van deze grensgroep configuratie maken. Op dezelfde sitesysteemserver kan hiervoor een andere verbindingssnelheid zijn ingesteld in verschillende grensgroepen.  

 De netwerkverbindingssnelheid wordt standaard ingesteld op **snel**, maar u kunt wijzigen naar **langzaam**. De netwerkverbindingssnelheid en configuratie van de implementatie moet u controleren of een client inhoud vanaf een distributiepunt downloaden kan wanneer de client zich in een gekoppelde grensgroep.  

 Zie voor meer informatie over de invloed van de configuratie voor de netwerkverbindingssnelheid op hoe clients inhoud downloaden [locatie van inhoudsbronnen](../../../../core/plan-design/hierarchy/content-source-location-scenarios.md).  
