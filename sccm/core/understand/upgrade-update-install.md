---
title: Over upgrade-, update- en installatie
titleSuffix: Configuration Manager
description: Meer informatie over het verschil tussen de voorwaarden Install-, Update- en Upgrade, bij het beheren van Configuration Manager-infrastructuur.
ms.custom: na
ms.date: 1/11/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 17fab17f-304d-4f6a-87c7-30ab4f5521ed
caps.latest.revision: "0"
caps.handback.revision: "0"
author: Brenduns
ms.author: brenduns
manager: angrobe
ms.openlocfilehash: b78f35e60365742ceda9773ae63eae5bb3d5b538
ms.sourcegitcommit: c236214b2fcc13dae7bad96d7fb33f692868191d
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/12/2017
---
# <a name="about-upgrade-update-and-install-for-site-and-hierarchy-infrastructure"></a>Over upgrade, bijwerken en voor de site en hiërarchie-infrastructuur installeren

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*


Bij het beheren van System Center Configuration Manager-site en hiërarchie-infrastructuur, de voorwaarden *upgrade*, *bijwerken*, en *installeren* worden gebruikt voor het beschrijven van drie afzonderlijke concepten.

## <a name="upgrade"></a>Upgrade
*Upgrade* of *in-place upgrade*, wordt gebruikt bij het converteren van uw Configuration Manager 2012-site of hiërarchie naar een System Center Configuration Manager wordt uitgevoerd.
Wanneer u naar System Center Configuration Manager System Center 2012 Configuration Manager bijwerkt, blijft dezelfde servers gebruiken voor het hosten van uw sites en siteservers en u uw bestaande gegevens en configuraties voor Configuration Manager behouden.  Dit verschilt van [migratie](/sccm/core/migration/migrate-data-between-hierarchies) dit is een manier om uw configuraties en gegevens over beheerde apparaten behouden tijdens het gebruik van nieuwe System Center Configuration Manager-sites naar nieuwe hardware is geïnstalleerd.

Zie voor meer informatie [upgraden naar System Center Configuration Manager](/sccm/core/servers/deploy/install/upgrade-to-configuration-manager).



## <a name="update"></a>bijwerken
*Update* wordt gebruikt voor het installeren van updates in de console voor System Center Configuration Manager en voor out-of-band-updates die zijn updates die van kunnen niet worden bezorgd binnen de Configuration Manager-console. Updates in de console kunnen de versie van uw site van de huidige vertakking (of Technical Preview-site) wijzigen zodat deze een hogere versie wordt uitgevoerd. Bijvoorbeeld, u als uw site versie 1606 wordt uitgevoerd, kunt u een update voor versie 1610 installeren. Updates kunnen oplossingen voor een bekend probleem ook installeren zonder te wijzigen van de versie van de sites.      

Normaal gesproken toevoegen updates beveiligingsproblemen, kwaliteitsverbetering en nieuwe functies aan uw bestaande implementatie. Als u de vertakking Technical Preview gebruikt, kunt een update een nieuwere versie van de Technical Preview installeren.
-   U kiezen wanneer de update in de console installeren vanaf de bovenste site van uw hiërarchie.
- U kunt de updates die beschikbaar is vanuit de console installeren. Bijvoorbeeld, als uw site versie 1602 wordt uitgevoerd en 1606 zowel 1610 worden aangeboden, moet u versie 1610 installeren omdat elke versie bevat de functies die voor het eerst werden beschikbaar gesteld in eerder uitgebrachte versies.
- Nadat de installatie op de bovenste site van een nieuwe update is voltooid, wordt het proces om bij te werken automatisch starten door onderliggende primaire sites. U kunt echter instellen [Servicewindows](/sccm/core/servers/manage/install-in-console-updates#a-namebkmkservicewindowa-service-windows-for-site-servers) om te bepalen van de timing van updates.
- Secundaire sites Installeer updates niet automatisch. In plaats daarvan, start u handmatig de update uit in de Configuration Manager-console.

Zie voor meer [Updates voor System Center Configuration Manager](/sccm/core/servers/manage/updates), en [Technical Preview voor System Center Configuration Manager](/sccm/core/get-started/technical-preview).



## <a name="install"></a>Installeren
*Installeer* is gebruikt bij een nieuwe Configuration Manager-hiërarchie helemaal zelf maken of extra sites toevoegt aan een bestaande hiërarchie.  

De locatie van setup.exe en de bijbehorende bronbestanden die u gebruikt wanneer u een nieuwe primaire site of centrale beheersite installeert, zijn afhankelijk van uw installatiescenario.

Zie voor meer [voorbereiden voor het installeren van sites](/sccm/core/servers/deploy/install/prepare-to-install-sites).
