---
title: Package Transfer Manager
titleSuffix: Configuration Manager
description: Begrijpen hoe Package Transfer Manager in System Center Configuration Manager inhoud overdraagt van een siteserver naar externe distributiepunten.
ms.custom: na
ms.date: 2/8/2017
ms.reviewer: na
ms.suite: na
ms.prod: configuration-manager
ms.technology: configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 3359f254-dd48-42b7-9eab-c92a3417e3fb
caps.latest.revision: "3"
author: Brenduns
ms.author: brenduns
manager: angrobe
ms.openlocfilehash: 7cc724404411ff2ef4897e1bb422f523f357f8eb
ms.sourcegitcommit: c236214b2fcc13dae7bad96d7fb33f692868191d
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/12/2017
---
# <a name="package-transfer-manager-in-system-center-configuration-manager"></a>Package Transfer Manager in System Center Configuration Manager

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*

De Package Transfer Manager is in een System Center Configuration Manager-site, een onderdeel van de SMS_Executive-service die de overdracht van inhoud van een siteservercomputer naar externe distributiepunten in een site beheert. (Een extern distributiepunt is een bevindt zich niet op de siteservercomputer.) De Package Transfer Manager configuraties worden niet ondersteund door de beheerder, maar de informatie over hoe dit werkt, kunt u van plan bent uw infrastructuur voor inhoudsbeheer. Zo kunt u oplossen van problemen met het distribueren van inhoud.


Wanneer u inhoud naar een of meer externe distributiepunten op een site distribueert, de **Distribution Manager** maakt een taak voor inhoudsoverdracht. Deze verwittigt vervolgens de Package Transfer Manager op primaire en secundaire siteservers om over te dragen van de inhoud naar de externe distributiepunten.

 Package Transfer Manager registreert uitgevoerde bewerkingen in de **pkgxfermgr.log** bestand op de siteserver. Het logboekbestand is de enige locatie waar u de activiteiten van de Package Transfer Manager kunt bekijken.  

> [!NOTE]  
>  In eerdere versies van Configuration Manager beheert Distribution Manager de overdracht van inhoud naar een extern distributiepunt. Distribution Manager beheert ook de overdracht van inhoud tussen sites. Met de System Center Configuration Manager, blijft Distribution Manager de overdracht van inhoud tussen twee sites beheren. De Package Transfer Manager beheert echter nu de overdracht van inhoud naar een groot aantal distributiepunten. Dit helpt de algehele prestaties van inhoudsimplementatie tussen sites en naar distributiepunten binnen een site te verhogen.  

Om inhoud te zetten naar een standaard distributiepunt, werkt Package Transfer Manager hetzelfde als de Distribution Manager in eerdere versies van Configuration Manager. Dat wil zeggen, beheert het actief de overdracht van bestanden naar elk extern distributiepunt. Echter, om inhoud te distribueren naar een pull-distributiepunt, de Package Transfer Manager waarschuwt dat het pull-distributiepunt dat de inhoud beschikbaar is. Het pull-distributiepunt wijst u vervolgens het overdrachtsproces overneemt.  

De volgende informatie beschrijft hoe Package Transfer Manager beheert de overdracht van inhoud naar standaard distributiepunten en naar distributiepunten die zijn geconfigureerd als pull-distributiepunten:
1.  **Admin implementeert inhoud naar een of meer distributiepunten op een site.**  

    -   **Standaard distributiepunt:** Distribution Manager maakt een taak voor inhoudsoverdracht voor die inhoud.  

    -   **Pull-distributiepunt:** Distribution Manager maakt een taak voor inhoudsoverdracht voor die inhoud.  

2.  **Distribution Manager voert voorbereidende controles uit.**  

    -   **Standaard distributiepunt:** Distribution Manager voert een basiscontrole uit om te bevestigen dat elk distributiepunt klaar is om de inhoud te ontvangen. Na deze controle geeft Distribution Manager een verwittiging Package Transfer Manager de overdracht van inhoud naar het distributiepunt te starten.  

    -   **Pull-distributiepunt:** Distribution Manager start Package Transfer Manager; deze vervolgens het pull-distributiepunt verwittigt wijzen dat er een nieuwe taak voor inhoudsoverdracht is. Distribution Manager controleert niet op de status van externe distributiepunten die pull-distributiepunten, omdat elk pull-distributiepunt zijn eigen inhoudsoverdrachten beheert.  

3.  **Package Transfer Manager bereidt de overdracht van inhoud.**  

    -   **Standaard distributiepunt:** Package Transfer Manager onderzoekt de single instance store van elk opgegeven extern distributiepunt. Het doel hiervan is het identificeren van bestanden die zich al op dat distributiepunt. Vervolgens voegt Package Transfer Manager voor overdracht alleen de bestanden die nog niet aanwezig.  

        > [!NOTE]  
        >  Om te kopiëren elk bestand in de distributie naar het distributiepunt, zelfs als de bestanden al aanwezig in de single instance store van het distributiepunt, gebruikt de **distribueren** actie voor inhoud.  

    -   **Pull-distributiepunt:** Voor elk pull-distributiepunt in de distributie controleert Package Transfer Manager dat het pull-distributiepunten bron, om te controleren of de inhoud beschikbaar is.  

        -   Wanneer de inhoud beschikbaar op ten minste één brondistributiepunt is, verzendt Package Transfer Manager een melding naar dat pull-distributiepunt. De melding stuurt dat distributiepunt om te beginnen met het proces van inhoudsoverdracht. De melding omvat bestandsnamen en grootten, kenmerken en hash-waarden.  

        -   Wanneer de inhoud nog niet beschikbaar is, verzendt Package Transfer Manager geen melding naar het distributiepunt. In plaats daarvan wordt de controle elke 20 minuten totdat de inhoud beschikbaar is herhaald. Vervolgens, wanneer de inhoud beschikbaar is, verzendt Package Transfer Manager de melding naar dat pull-distributiepunt.  

        > [!NOTE]  
        >  Voor het pull-distributiepunt die om te kopiëren van elk bestand in de distributie naar het distributiepunt, zelfs als de bestanden al aanwezig in de single instance store van het pull-distributiepunt, gebruikt u de **distribueren** actie voor inhoud.  

4.  **Inhoud wordt gestart om over te dragen.**  

    -   **Standaard distributiepunt:** Package Transfer Manager kopieert bestanden naar elk extern distributiepunt. Tijdens de overdracht naar een standaard distributiepunt:  

        -   Standaard kunt Package Transfer Manager tegelijk verwerken drie unieke pakketten, en ze distribueren naar vijf distributiepunten parallel. Deze heten gezamenlijk **instellingen voor gelijktijdige distributie**. Voor het instellen van gelijktijdige distributie in de **eigenschappen van Softwaredistributieonderdelen** voor elke site, gaat u naar de **algemene** tabblad.  

        -   Package Transfer Manager gebruikt de planning- en netwerkbandbreedteconfiguraties van elk distributiepunt bij de overdracht van inhoud naar het distributiepunt. Deze instellingen configureren in de **eigenschappen** van elk extern distributiepunt, gaat u naar de **planning** en **frequentielimieten** tabbladen. Zie voor meer informatie [inhoud en infrastructuur voor System Center Configuration Manager beheren](../../../core/servers/deploy/configure/manage-content-and-content-infrastructure.md).  

    -   **Pull-distributiepunt:** Als een pull-distributiepunt een meldingsbestand ontvangt, begint het distributiepunt het proces voor het overdragen van de inhoud. Het overdrachtsproces wordt onafhankelijk uitgevoerd op elk pull-distributiepunt:  

        1.   Het pull-distributiepunt identificeert de bestanden in de distributie van inhoud die het heeft geen al in zijn single instance store en bereidt het downloaden van die inhoud van een van de brondistributiepunten.  

        2.   Vervolgens het pull-distributiepunt controles met elk van de brondistributiepunten in volgorde, totdat zoekt deze een brondistributiepunt dat de inhoud beschikbaar is. Als het pull-distributiepunt een brondistributiepunt met de inhoud identificeert, begint deze het downloaden van die inhoud.  

        > [!NOTE]  
        >  Het proces om inhoud te downloaden door het pull-distributiepunt is hetzelfde als die door Configuration Manager-clients gebruikt. Voor de overdracht van inhoud door het pull-distributiepunt, worden niet instellingen voor gelijktijdige overdracht gebruikt. Planning en bandbreedtebeperking opties die u configureert voor standaarddistributiepunten worden niet gebruikt.  

5.  **Inhoudsoverdracht wordt voltooid.**  

    -   **Standaard distributiepunt:** Nadat de Package Transfer Manager klaar is overdracht van bestanden naar elk aangewezen extern distributiepunt, verifieert het de hash van de inhoud op het distributiepunt. Deze verwittigt vervolgens Distribution Manager dat de distributie voltooid is.  

    -   **Pull-distributiepunt:** Nadat het pull-distributiepunt het downloaden van de inhoud voltooit, verifieert het distributiepunt de hash van de inhoud. Verzendt vervolgens een statusbericht naar het sitebeheerpunt om aan te geven geslaagd. Als deze status niet na 60 minuten ontvangen is, ontwaakt de Package Transfer Manager opnieuw. Er wordt gecontroleerd met de pull-distributiepunt om te bevestigen of het pull-distributiepunt de inhoud heeft gedownload. Als het downloaden van de inhoud wordt uitgevoerd, de Package Transfer Manager de inactieve modus inschakelt voor een andere 60 minuten voordat deze het pull-distributiepunt opnieuw controleert. De cyclus gaat door totdat het pull-distributiepunt de inhoudstransfer voltooit.  
