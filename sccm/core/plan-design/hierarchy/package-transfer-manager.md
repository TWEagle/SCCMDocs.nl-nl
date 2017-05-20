---
title: Transfer Manager het pakket | Microsoft-documenten
description: Begrijpen hoe Package Transfer Manager in System Center Configuration Manager inhoud overdraagt vanaf een siteserver naar externe distributiepunten.
ms.custom: na
ms.date: 2/8/2017
ms.reviewer: na
ms.suite: na
ms.prod: configuration-manager
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 3359f254-dd48-42b7-9eab-c92a3417e3fb
caps.latest.revision: 3
author: Brenduns
ms.author: brenduns
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 099345d59891841a336cbada896ec349751fecd3
ms.openlocfilehash: 54e54409a1792c7e28620a5e3cea3e8d8695c7d4
ms.contentlocale: nl-nl
ms.lasthandoff: 05/17/2017

---
# <a name="package-transfer-manager-in-system-center-configuration-manager"></a>Package Transfer Manager in System Center Configuration Manager

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*

In een System Center Configuration Manager-site is de Package Transfer Manager een onderdeel van de SMS Executive-service die de overdracht van inhoud van een siteservercomputer naar externe distributiepunten in een site beheert. (Een extern distributiepunt is een bevindt zich niet op de siteservercomputer.) De Package Transfer Manager configuraties worden niet ondersteund door de beheerder, maar begrijpen hoe het werkt, kunt u van plan bent uw infrastructuur voor inhoudsbeheer. Dit kan ook helpen bij het oplossen van problemen met het distribueren van inhoud.


Wanneer u inhoud naar een of meer externe distributiepunten op een site distribueert de **Distributiebeheer** maakt een taak voor inhoudsoverdracht. Deze verwittigt vervolgens de Package Transfer Manager op primaire en secundaire siteservers om over te dragen van de inhoud naar de externe distributiepunten.

 Package Transfer Manager registreert uitgevoerde bewerkingen in de **pkgxfermgr.log** -bestand op de siteserver. Het logboekbestand is de enige locatie waar u de activiteiten van de Package Transfer Manager kunt bekijken.  

> [!NOTE]  
>  In eerdere versies van Configuration Manager beheert Distribution Manager de overdracht van inhoud naar een extern distributiepunt. Distribution Manager beheert ook de overdracht van inhoud tussen sites. Met de System Center Configuration Manager, blijft Distribution Manager de overdracht van inhoud tussen twee sites beheren. De Package Transfer Manager beheert nu echter de overdracht van inhoud naar een groot aantal distributiepunten. Dit helpt bij het verhogen van de algehele prestaties van inhoudsimplementatie tussen sites en naar distributiepunten binnen een site.  

Voor het overbrengen van inhoud naar een standaard distributiepunt werkt Package Transfer Manager hetzelfde als het Distributiebeheer in eerdere versies van Configuration Manager. Dat wil zeggen, beheert het actief de overdracht van bestanden naar elk extern distributiepunt. Echter om inhoud te distribueren naar een pull-distributiepunt, verwittigt de Package Transfer Manager dat het pull-distributiepunt dat de inhoud beschikbaar is. Het pull-distributiepunt beheerpunt vervolgens neemt over het overdrachtsproces.  

De volgende informatie beschrijft hoe Package Transfer Manager beheert de overdracht van inhoud naar standaard distributiepunten en naar distributiepunten die zijn geconfigureerd als pull-distributiepunten:
1.  **Beheerder implementeert inhoud naar een of meer distributiepunten op een site.**  

    -   **Standaard distributiepunt:** Distribution Manager maakt een taak voor inhoudsoverdracht voor die inhoud.  

    -   **Pull-distributiepunt:** Distribution Manager maakt een taak voor inhoudsoverdracht voor die inhoud.  

2.  **Distribution Manager voert voorbereidende controles uit.**  

    -   **Standaard distributiepunt:** Distribution Manager voert een basiscontrole uit om te bevestigen dat elk distributiepunt klaar is om de inhoud te ontvangen. Na deze controle geeft Distribution Manager een verwittiging Package Transfer Manager om te beginnen met de overdracht van inhoud naar het distributiepunt.  

    -   **Pull-distributiepunt:** Distribution Manager start Package Transfer Manager; deze vervolgens het pull-distributiepunt verwittigt wijzen dat er een nieuwe taak voor inhoudsoverdracht is. Distribution Manager controleert niet op de status van externe distributiepunten die pull-distributiepunten, omdat elk pull-distributiepunt zijn eigen inhoudsoverdrachten beheert.  

3.  **Package Transfer Manager bereidt de overdracht van inhoud.**  

    -   **Standaard distributiepunt:** Package Transfer Manager onderzoekt de single instance store van elk opgegeven extern distributiepunt. Het doel van dit is het identificeren van bestanden die zich al op dat distributiepunt. Vervolgens voegt Package Transfer Manager voor overdracht toe alleen de bestanden die nog niet aanwezig zijn.  

        > [!NOTE]  
        >  Als u wilt kopiëren elk bestand in de distributie naar het distributiepunt, zelfs als de bestanden al aanwezig in de single instance store van het distributiepunt zijn, gebruikt u de **distribueren** actie voor inhoud.  

    -   **Pull-distributiepunt:** Voor elk pull-distributiepunt in de distributie controleert Package Transfer Manager dat het pull-distributiepunten bron, om te bevestigen dat de inhoud beschikbaar.  

        -   Wanneer de inhoud beschikbaar is op ten minste één brondistributiepunt aanwezig is, verzendt Package Transfer Manager een melding naar dat pull-distributiepunt. De melding dat distributiepunt controleert om te beginnen met het proces van inhoudsoverdracht. De melding bevat namen en grootten, kenmerken en hash-waarden.  

        -   Wanneer de inhoud nog niet beschikbaar is, verzendt Package Transfer Manager geen melding naar het distributiepunt. In plaats daarvan wordt de controle elke 20 minuten totdat de inhoud beschikbaar is herhaald. Klik, wanneer de inhoud beschikbaar is, verzendt Package Transfer Manager de melding naar dat pull-distributiepunt.  

        > [!NOTE]  
        >  Voor het pull-distributiepunt elk bestand kopiëren in de distributie naar het distributiepunt, zelfs als de bestanden al aanwezig in de single instance store van het pull-distributiepunt, gebruikt u de **distribueren** actie voor inhoud.  

4.  **Inhoud wordt gestart om over te dragen.**  

    -   **Standaard distributiepunt:** Package Transfer Manager kopieert bestanden naar elk extern distributiepunt. Tijdens de overdracht naar een standaard distributiepunt:  

        -   Standaard kan Package Transfer Manager gelijktijdig verwerken drie unieke pakketten en ze distribueren naar vijf distributiepunten parallel. Gezamenlijk dit zijn de zogenaamde **instellingen voor gelijktijdige distributie**. Voor het instellen van gelijktijdige distributie in de **eigenschappen van Softwaredistributieonderdelen** voor elke site, gaat u naar de **algemeen** tabblad.  

        -   Package Transfer Manager gebruikt de planning- en netwerkbandbreedteconfiguraties van elk distributiepunt bij de overdracht van inhoud naar het distributiepunt. Deze instellingen configureren de **eigenschappen** van elk extern distributiepunt, gaat u naar de **schema** en **frequentielimieten** tabbladen. Zie voor meer informatie [inhoud en -infrastructuur voor System Center Configuration Manager beheert](../../../core/servers/deploy/configure/manage-content-and-content-infrastructure.md).  

    -   **Pull-distributiepunt:** Het distributiepunt begint het proces voor het overbrengen van de inhoud wanneer een pull-distributiepunt een meldingsbestand ontvangt. Het overdrachtsproces wordt onafhankelijk uitgevoerd op elk pull-distributiepunt:  

        1.   Het pull-distributiepunt identificeert de bestanden in de inhoudsdistributie die het nog niet heeft in zijn single instance store en bereidt het downloaden van die inhoud van een van zijn brondistributiepunten.  

        2.   Vervolgens het pull-distributiepunt controles met elk van de brondistributiepunten in volgorde, totdat het een brondistributiepunt dat de inhoud beschikbaar vindt. Wanneer het pull-distributiepunt een brondistributiepunt met de inhoud identificeert, wordt het downloaden van die inhoud gestart.  

        > [!NOTE]  
        >  Het proces om inhoud te downloaden door het pull-distributiepunt is hetzelfde als die wordt gebruikt door Configuration Manager-clients. Voor de overdracht van inhoud door het pull-distributiepunt, worden niet de instellingen voor gelijktijdige overdracht gebruikt. Plannings- en beperkingsopties die u configureert voor standaarddistributiepunten worden niet gebruikt.  

5.  **Inhoudsoverdracht wordt voltooid.**  

    -   **Standaard distributiepunt:** Nadat de Package Transfer Manager klaar is met overdracht van bestanden naar elk aangewezen extern distributiepunt, verifieert het de hash van de inhoud op het distributiepunt. Deze verwittigt vervolgens Distribution Manager de distributie is voltooid.  

    -   **Pull-distributiepunt:** Nadat het pull-distributiepunt het downloaden van de inhoud voltooit, verifieert het distributiepunt de hash van de inhoud. Vervolgens verzendt een statusbericht naar het sitebeheerpunt om aan te geven geslaagd. Als deze status na 60 minuten ontvangen wordt, haalt de Package Transfer Manager opnieuw uit. Deze controleert het pull-distributiepunt om te bevestigen of het pull-distributiepunt de inhoud heeft gedownload. Als het downloaden van de inhoud wordt uitgevoerd, de Package Transfer Manager de inactieve modus inschakelt voor een andere 60 minuten voordat deze het pull-distributiepunt opnieuw controleert. De cyclus gaat door totdat het pull-distributiepunt de inhoudstransfer voltooit.  

