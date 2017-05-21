---
title: Accounts voor toegang tot inhoud in System Center Configuration Manager | Microsoft-documenten
description: Meer informatie over de accounts waar clients toegang krijgen inhoud van de System Center Configuration Manager tot.
ms.custom: na
ms.date: 2/6/2017
ms.reviewer: na
ms.suite: na
ms.prod: configuration-manager
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: a7df9d0f-fbde-47eb-97e7-3d29536424fa
caps.latest.revision: 4
author: Brenduns
ms.author: brenduns
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: e592a732259147ee71d404a68982c28e5138e243
ms.openlocfilehash: 0e982d08d54af39b13f553fc531a200f921e94a6
ms.contentlocale: nl-nl
ms.lasthandoff: 05/17/2017

---
# <a name="manage-accounts-to-access-content-in-system-center-configuration-manager"></a>Beheer van accounts voor toegang tot inhoud in System Center Configuration Manager

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*

Houd rekening met hoe clients toegang tot deze inhoud van distributiepunten voor het implementeren van inhoud in System Center Configuration Manager. Dit artikel worden de volgende accounts voor dit doel gebruikte:

-   **Account voor toegang tot het netwerk**. Gebruikt door clients verbinding maken met een distributiepunt en toegang tot inhoud. Clients proberen eerst hun computeraccount standaard.

     Dit account wordt ook gebruikt door pull-distributiepunten inhoud ophalen van een brondistributiepunt in een extern forest.  

-   **Account voor toegang tot het pakket**. Standaard Configuration Manager verleent toegang tot inhoud op een distributiepunt aan de ingebouwde accounts met de naam **gebruikers** en **beheerders**. U kunt aanvullende machtigingen om toegang te beperken instellen.  

-   **Multicastverbindingsaccount**. Gebruikt voor implementaties van besturingssystemen.  

##  <a name="bkmk_NAA"></a>Netwerktoegangsaccount  
 Clientcomputers gebruiken het netwerktoegangsaccount wanneer ze hun lokale computeraccount niet kunnen gebruiken voor toegang tot inhoud op distributiepunten. Dit is bijvoorbeeld van toepassing op werkgroepclients en computers uit niet-vertrouwde domeinen. Dit account kan ook worden gebruikt tijdens het implementeren van besturingssystemen wanneer de computer die het besturingssysteem installeert nog niet over een computeraccount voor het domein beschikt.  

-   Clients gebruiken het netwerktoegangsaccount alleen voor toegang tot bronnen op het netwerk.  

-   U kunt op iedere primaire site meerdere accounts voor gebruik als een netwerktoegangsaccount instellen.  

-   Clients proberen eerst toegang tot inhoud op een distributiepunt met hun *computername*$-account. Als dit account is mislukt, probeert clients vervolgens een netwerktoegangsaccount gebruiken. Clients blijven proberen te gebruiken het netwerktoegangsaccount, zelfs als deze eerder is mislukt.  

### <a name="permissions"></a>Machtigingen
Verleen deze account de toepasselijke minimale machtigingen voor toegang tot de software voor de inhoud die de client vereist.  

-   De account moet beschikken over de **toegang tot deze computer via het netwerk** rechts op het distributiepunt.  

-   Maak de account in elk domein dat de benodigde toegang tot bronnen biedt. Het netwerktoegangsaccount moet altijd een domeinnaam omvatten. Pass Through-beveiliging wordt niet ondersteund voor dit account. Als u over distributiepunten in meerdere domeinen beschikt, maakt u het account in een vertrouwd domein.  

> [!TIP]  
>  Wijzig het wachtwoord van een bestaand netwerktoegangsaccount niet om vergrendeling te voorkomen. In plaats daarvan een nieuw account en het nieuwe account in Configuration Manager instellen. Wanneer er voldoende tijd is verstreken voor alle clients naar de nieuwe accountdetails hebben ontvangen, de oude account verwijderen uit de gedeelde netwerkmappen en de account verwijderen.  

> [!IMPORTANT]  
>  Verleen deze account geen interactieve rechten aan te melden.  
>   
>  Aan dit account mag niet de machtiging worden toegekend om computers lid te maken van het domein. Gebruik het domeinlidmaatschapsaccount van de takenreekseditor als u tijdens een takenreeks computers lid moet maken van een domein.  

### <a name="to-configure-the-network-access-account"></a>Het netwerktoegangsaccount configureren  

1.  Kies in de Configuration Manager-console **beheer** >   **siteconfiguratie** >  **Sites**, en selecteer vervolgens de site.  

2.  Op de **instellingen** groep, kiest u **Siteonderdelen configureren** > **softwaredistributie**.  

3.  Kies de **netwerktoegangsaccount** tabblad. Instellen van een of meer accounts en kies vervolgens **OK**.  

##  <a name="bkmk_Paa"></a>Pakkettoegangsaccounts  
 Pakkettoegangsaccounts kunt u machtigingen voor NTFS-bestandssysteem om op te geven van de gebruikers en gebruikersgroepen die toegang pakketinhoud op distributiepunten tot instellen. Standaard Configuration Manager alleen toegang verleend aan de algemene **gebruikers** en **beheerders** accounts. U kunt echter toegang voor clientcomputers beheren via aanvullende Windows-accounts of groepen. Mobiele apparaten niet de Pakkettoegangsaccounts gebruiken, omdat deze apparaten pakketinhoud altijd anoniem halen.  

 Standaard, wanneer de Configuration Manager kopieert de inhoudsbestanden in een pakket naar een distributiepunt, kent het **lezen** toegang tot de lokale **gebruikers** groep en **volledig beheer** aan de lokale **beheerders** groep. De werkelijke machtigingen die vereist zijn, is afhankelijk van het pakket. Als er sprake is van clients in werkgroepen of in niet-vertrouwde forests, kunnen deze clients het netwerktoegangsaccount gebruiken voor toegang tot de pakketinhoud. Zorg ervoor dat de netwerktoegangsaccount machtigingen voor het pakket met behulp van de gedefinieerde Pakkettoegangsaccounts.  

 Gebruik accounts in een domein dat toegang heeft tot de distributiepunten. Als u het account maakt of aanpast nadat het pakket is gemaakt, moet u het pakket opnieuw distribueren. Bijwerken van het pakket, verandert de NTFS-bestandssysteemmachtigingen van het pakket niet.  

 U hoeft niet de Network Access Account toevoegen als een Pakkettoegangsaccount omdat het lidmaatschap van de **gebruikers** groep automatisch toegevoegd. Als u het pakkettoegangsaccount uitsluitend tot het netwerktoegangsaccount beperkt, blijven clients toegang houden tot het pakket.  

### <a name="to-manage-access-accounts"></a>Toegangsaccounts beheren  

1.  Kies in de Configuration Manager-console **softwarebibliotheek**.  

2.  In de **softwarebibliotheek** werkruimte bepalen welk type inhoud waarvoor u accounts wilt beheren en volg de stappen:  

    -   **Toepassingen**: Vouw **Toepassingsbeheer**, kies **toepassingen**, en selecteer vervolgens de toepassingen waarvoor u accounts wilt beheren.  

    -   **Pakketten**: Vouw **Toepassingsbeheer**, kies **pakketten**, en selecteer vervolgens de pakketten waarvoor u accounts wilt beheren.  

    -   **Implementatiepakketten**: Vouw **Software-Updates**, kies **implementatiepakketten**, en selecteer vervolgens de implementatiepakketten waarvoor u accounts wilt beheren.  

    -   **Stuurprogrammapakketten**: Vouw **besturingssystemen**, kies **stuurprogrammapakketten**, en selecteer vervolgens de stuurprogrammapakketten waarvoor u accounts wilt beheren.  

    -   **Installatiekopieën van besturingssystemen**: Vouw **besturingssystemen**, kies **installatiekopieën van besturingssystemen**, en selecteer vervolgens de installatiekopieën van besturingssystemen waarvoor u accounts wilt beheren.  

    -   **Installatieprogramma's van besturingssysteem**: Vouw **besturingssystemen**, kies **installatieprogramma's van besturingssysteem**, en selecteer vervolgens de installatieprogramma's van het besturingssysteem waarvoor u accounts wilt beheren.  

    -   **Opstartinstallatiekopieën**: Vouw **besturingssystemen**, kies **opstartinstallatiekopieën**, en selecteer vervolgens de stuurprogrammapakketten waarvoor u accounts wilt beheren.  

3.  Met de rechtermuisknop op het geselecteerde object en kies vervolgens **toegangsaccounts beheren**.  

4.  In de **Account toevoegen** dialoogvenster, geeft u het accounttype op waaraan toegang tot de inhoud wordt verleend en geef vervolgens de toegangsrechten die zijn gekoppeld aan het account.  

    > [!NOTE]  
    >  Wanneer u een gebruikersnaam op voor het account toevoegt en Configuration Manager vindt u zowel een lokale gebruikersaccount en een domeingebruikersaccount met die naam, stelt Configuration Manager toegangsrechten voor de domeingebruikersaccount.  

##  <a name="bkmk_multi"></a>Multicastverbindingsaccount  
 De Multicastverbindingsaccount wordt gebruikt door distributiepunten die zijn ingesteld voor multicast om informatie te lezen uit de sitedatabase.  

-   U geeft een serviceaccount te gebruiken bij het instellen van Configuration Manager-databaseverbindingen voor multicast.  

-   Standaard het computeraccount van het distributiepunt wordt gebruikt, maar u kunt een gebruikersaccount in plaats daarvan instellen.  

-   U moet een gebruikersaccount opgeven wanneer de sitedatabase zich in een niet-vertrouwd forest bevindt.  

-   Het account moet hebben **lezen** machtigingen voor de sitedatabase.  

Als uw datacentrum bijvoorbeeld een perimeternetwerk heeft in een ander forest dan de siteserver en sitedatabase, kunt u dit account gebruiken om de multicastinformatie uit de sitedatabase te lezen.

Als u deze account maakt, kunt u deze als een lokale account op de computer waarop Microsoft SQL Server wordt uitgevoerd met weinig rechten maken.  

> [!IMPORTANT]  
>  Verleen deze account geen interactieve rechten aan te melden.  

