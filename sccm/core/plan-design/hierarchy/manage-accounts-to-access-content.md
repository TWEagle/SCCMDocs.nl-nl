---
title: Accounts voor toegang tot inhoud
titleSuffix: Configuration Manager
description: Meer informatie over de accounts waar clients toegang krijgen inhoud van de System Center Configuration Manager tot.
ms.custom: na
ms.date: 2/6/2017
ms.reviewer: na
ms.suite: na
ms.prod: configuration-manager
ms.technology: configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: a7df9d0f-fbde-47eb-97e7-3d29536424fa
caps.latest.revision: "4"
author: Brenduns
ms.author: brenduns
manager: angrobe
ms.openlocfilehash: 3767fe81db62d8604de02d7a5867ce03a09ba2e4
ms.sourcegitcommit: c236214b2fcc13dae7bad96d7fb33f692868191d
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/12/2017
---
# <a name="manage-accounts-to-access-content-in-system-center-configuration-manager"></a>Accounts voor toegang tot inhoud in System Center Configuration Manager beheren

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*

Overweeg hoe clients toegang tot die inhoud van distributiepunten voordat het implementeren van inhoud in System Center Configuration Manager. Dit artikel worden de volgende accounts voor dit doel gebruikt:

-   **Netwerktoegangsaccount**. Verbinding maken met een distributiepunt en toegang tot inhoud door clients gebruikt. Clients proberen standaard eerst hun computeraccount.

     Dit account wordt ook gebruikt door pull-distributiepunten om inhoud te verkrijgen van een brondistributiepunt in een extern forest.  

-   **Pakkettoegangsaccount**. Standaard Configuration Manager verleent toegang tot inhoud op een distributiepunt op de ingebouwde accounts met de naam **gebruikers** en **beheerders**. U kunt instellen wanneer er aanvullende machtigingen om toegang te beperken.  

-   **Multicastverbindingsaccount**. Gebruikt voor implementaties van besturingssystemen.  

##  <a name="bkmk_NAA"></a>Netwerktoegangsaccount  
 Clientcomputers gebruiken het netwerktoegangsaccount wanneer ze hun lokale computeraccount niet kunnen gebruiken voor toegang tot inhoud op distributiepunten. Dit is bijvoorbeeld van toepassing op werkgroepclients en computers uit niet-vertrouwde domeinen. Dit account kan ook worden gebruikt tijdens het implementeren van besturingssystemen wanneer de computer die het besturingssysteem installeert nog niet over een computeraccount voor het domein beschikt.  

-   Clients gebruiken het netwerktoegangsaccount alleen voor het openen van bronnen op het netwerk.  

-   U kunt op elke primaire site meerdere accounts voor gebruik als een netwerktoegangsaccount instellen.  

-   Clients proberen eerst toegang tot inhoud op een distributiepunt met hun *computername*$-account. Als dit account is mislukt, probeert clients een netwerktoegangsaccount gebruiken. Clients blijven proberen om te gebruiken het netwerktoegangsaccount, zelfs als deze eerder is mislukt.  

### <a name="permissions"></a>Machtigingen
Verleen aan deze account de minimaal vereiste machtigingen voor toegang tot de software voor de inhoud die de client vereist.  

-   De account moet beschikken over de **toegang tot deze computer vanaf het netwerk** rechts op het distributiepunt.  

-   Maak de account in elk domein dat de benodigde toegang tot bronnen biedt. Het netwerktoegangsaccount moet altijd een domeinnaam omvatten. Pass Through-beveiliging wordt niet ondersteund voor dit account. Als u over distributiepunten in meerdere domeinen beschikt, maakt u het account in een vertrouwd domein.  

> [!TIP]  
>  Wijzig het wachtwoord van een bestaand netwerktoegangsaccount niet om vergrendeling te voorkomen. In plaats daarvan een nieuw account maken en instellen van het nieuwe account in Configuration Manager. Wanneer er voldoende tijd is verstreken waarbinnen alle clients de nieuwe accountgegevens hebben ontvangen, verwijder de oude account uit de gedeelde netwerkmappen en het account verwijderen.  

> [!IMPORTANT]  
>  Ken deze account geen interactieve rechten aan te melden.  
>   
>  Aan dit account mag niet de machtiging worden toegekend om computers lid te maken van het domein. Gebruik het domeinlidmaatschapsaccount van de takenreekseditor als u tijdens een takenreeks computers lid moet maken van een domein.  

### <a name="to-configure-the-network-access-account"></a>Het netwerktoegangsaccount configureren  

1.  Kies in de Configuration Manager-console **beheer** >   **siteconfiguratie** >  **Sites**, en selecteer vervolgens de site.  

2.  Op de **instellingen** groep, kiest u **Siteonderdelen configureren** > **softwaredistributie**.  

3.  Kies de **netwerktoegangsaccount** tabblad. Instellen van een of meer accounts en kies vervolgens **OK**.  

##  <a name="bkmk_Paa"></a>Pakkettoegangsaccounts  
 Pakkettoegangsaccounts kunt u NTFS-bestandssysteemmachtigingen om op te geven van de gebruikers en gebruikersgroepen die toegang pakketinhoud op distributiepunten tot instellen. Standaard Configuration Manager alleen toegang verleend aan de algemene **gebruikers** en **beheerders** accounts. U kunt echter toegang voor clientcomputers beheren via aanvullende Windows-accounts of groepen. Mobiele apparaten niet de Pakkettoegangsaccounts niet gebruiken omdat deze apparaten pakketinhoud altijd anoniem halen.  

 Standaard wanneer Configuration Manager de inhoudsbestanden in een pakket naar een distributiepunt kopieert, kent het **lezen** toegang tot de lokale **gebruikers** groep en **volledig beheer** aan de lokale **beheerders** groep. De werkelijke machtigingen die vereist zijn, is afhankelijk van het pakket. Als er sprake is van clients in werkgroepen of in niet-vertrouwde forests, kunnen deze clients het netwerktoegangsaccount gebruiken voor toegang tot de pakketinhoud. Controleer of het netwerktoegangsaccount machtigingen voor het pakket heeft met behulp van de gedefinieerde Pakkettoegangsaccounts.  

 Gebruik accounts in een domein dat toegang heeft tot de distributiepunten. Als u het account maakt of aanpast nadat het pakket is gemaakt, moet u het pakket opnieuw distribueren. Bijwerken van het pakket, wordt de machtigingen voor NTFS-bestandssysteem op het pakket niet gewijzigd.  

 U hoeft niet de netwerktoegangsaccount toevoegen als een Pakkettoegangsaccount omdat het lidmaatschap van de **gebruikers** groep automatisch toegevoegd. Als u het pakkettoegangsaccount uitsluitend tot het netwerktoegangsaccount beperkt, blijven clients toegang houden tot het pakket.  

### <a name="to-manage-access-accounts"></a>Toegangsaccounts wilt beheren  

1.  Kies in de Configuration Manager-console **softwarebibliotheek**.  

2.  In de **softwarebibliotheek** werkruimte, het type inhoud waarvoor u toegangsaccounts wilt beheren wilt bepalen en volg de stappen:  

    -   **Toepassingen**: Vouw **Toepassingsbeheer**, kies **toepassingen**, en selecteer vervolgens de toepassingen waarvoor u toegangsaccounts wilt beheren.  

    -   **Pakketten**: Vouw **Toepassingsbeheer**, kies **pakketten**, en selecteer vervolgens de pakketten waarvoor u toegangsaccounts wilt beheren.  

    -   **Implementatiepakketten**: Vouw **Software-Updates**, kies **implementatiepakketten**, en selecteer vervolgens de implementatiepakketten waarvoor u toegangsaccounts wilt beheren.  

    -   **Stuurprogrammapakketten**: Vouw **besturingssystemen**, kies **stuurprogrammapakketten**, en selecteer vervolgens de stuurprogrammapakketten waarvoor u toegangsaccounts wilt beheren.  

    -   **Installatiekopieën van besturingssystemen**: Vouw **besturingssystemen**, kies **installatiekopieën van besturingssystemen**, en selecteer vervolgens de installatiekopieën van besturingssystemen waarvoor u toegangsaccounts wilt beheren.  

    -   **Installatieprogramma's besturingssystemen**: Vouw **besturingssystemen**, kies **installatieprogramma's besturingssystemen**, en selecteer vervolgens de installatieprogramma's van het besturingssysteem waarvoor u toegangsaccounts wilt beheren.  

    -   **Opstartinstallatiekopieën**: Vouw **besturingssystemen**, kies **opstartinstallatiekopieën**, en selecteer vervolgens de opstartinstallatiekopieën waarvoor u toegangsaccounts wilt beheren.  

3.  Met de rechtermuisknop op het geselecteerde object en kies vervolgens **toegangsaccounts beheren**.  

4.  In de **Account toevoegen** dialoogvenster Geef het accounttype op waaraan toegang tot de inhoud wordt verleend en geef vervolgens de toegangsrechten die zijn gekoppeld aan het account.  

    > [!NOTE]  
    >  Wanneer u een gebruikersnaam voor het account toevoegt en Configuration Manager vindt u zowel een lokaal gebruikersaccount en een domeingebruikersaccount met die naam, stelt de Configuration Manager toegangsrechten voor het domeingebruikersaccount.  

##  <a name="bkmk_multi"></a>Multicastverbindingsaccount  
 De Multicastverbindingsaccount wordt gebruikt door distributiepunten die zijn ingesteld voor multicast om informatie te lezen uit de sitedatabase.  

-   U geeft een account te gebruiken bij het instellen van Configuration Manager-databaseverbindingen voor multicast.  

-   Standaard het computeraccount van het distributiepunt wordt gebruikt, maar u kunt een gebruikersaccount in plaats daarvan instellen.  

-   U moet een gebruikersaccount opgeven wanneer de sitedatabase zich in een niet-vertrouwd forest bevindt.  

-   Het account moet hebben **lezen** machtigingen voor de sitedatabase.  

Als uw datacentrum bijvoorbeeld een perimeternetwerk heeft in een ander forest dan de siteserver en sitedatabase, kunt u dit account gebruiken om de multicastinformatie uit de sitedatabase te lezen.

Als u dit account maakt, maakt u dit als een beperkte rechten, lokaal account op de computer waarop Microsoft SQL Server uitvoert.  

> [!IMPORTANT]  
>  Ken deze account geen interactieve rechten aan te melden.  
