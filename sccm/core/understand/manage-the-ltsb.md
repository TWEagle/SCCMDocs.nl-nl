---
title: De LTSB beheren
titleSuffix: Configuration Manager
description: Beheer de verschillen voor de LTSB van System Center Configuration Manager.
ms.custom: na
ms.date: 05/01/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 8da2887a-fd8e-438c-b926-849c121f7fdf
caps.latest.revision: "0"
author: aczechowski
ms.author: aaroncz
manager: angrobe
ms.openlocfilehash: 74c51cfc4c53f5edf8cfc8043a7b81fe833cc832
ms.sourcegitcommit: ca9d15dfb1c9eb47ee27ea9b5b39c9f8cdcc0748
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 01/04/2018
---
# <a name="manage-the-long-term-servicing-branch-of-configuration-manager"></a>De lange termijn Servicing Branch van Configuration Manager beheren

*Van toepassing op: System Center Configuration Manager (op lange termijn onderhoud vertakking)*

Wanneer u de Long-Term Servicing Branch (LTSB) van System Center Configuration Manager gebruikt, vindt het volgende u informatie over belangrijke wijzigingen die invloed hebben op hoe u uw infrastructuur beheren.

Omdat de LTSB is gelijk aan de huidige vertakking versie 1606 (met enkele uitzonderingen zoals Intune-integratie en cloud-gerelateerde functies), zijn de meeste taken die u voor de planning, implementatie, configuratie en beheer van dagelijkse gebruikt hetzelfde.

De LTSB ondersteunt bijvoorbeeld hetzelfde aantal sites, typen sites, clients en algemene infrastructuur als de huidige vertakking. Gebruik daarom de richtlijnen gevonden in de site en hiërarchie onderwerpen over planning en ontwerp voor de huidige vertakking. Op deze manier voor functies met de LTSB die worden ondersteund door zowel vertakkingen, zoals Software-Updates of implementatie van besturingssystemen gebruik van de richtlijnen gevonden in deze gedeelten van de documentatie van de huidige vertakking met het voorbehoud hebben geen toegang tot de functiewijzigingen die zijn geïntroduceerd na versie 1606 van de huidige vertakking.

De volgende secties bevatten informatie over taken die niet gelijkvormig zijn beheren.

## <a name="updates-and-servicing"></a>Updates en onderhoud
Alleen beveiligingsupdates worden beschikbaar gesteld als console-updates in de LTSB.  

Informatie over regelmatig updates voor de latere versies van de Current Branch zijn zichtbaar in de console, maar zijn niet beschikbaar gesteld voor de LTSB. Ze niet zijn gedownload en kunnen niet worden geïnstalleerd.

Ter ondersteuning van updates in de console voor kritieke beveiligingsproblemen, een site LTSB vereist het gebruik van [het service connection point](/sccm/core/servers/deploy/configure/about-the-service-connection-point). U kunt deze sitesysteemrol in de modus voor offline- of configureren, zoals wordt uitgevoerd voor de huidige vertakking. De LTSB verzamelt en verzendt dezelfde Telemetrie en het gebruik van gegevens als de huidige vertakking.

De LTSB ondersteunt het gebruik van het installatieprogramma voor hotfixes en het hulpprogramma registratie bijwerken zoals beschreven voor de huidige vertakking.

Raadpleeg voor algemene informatie over updates en onderhoud [Updates voor Configuration Manager](/sccm/core/servers/manage/updates).


## <a name="changes-for-site-expansion-and-the-cdlatest-folder"></a>Wijzigingen voor site-uitbreiding en de CD. Meest recente map
Wanneer u de LTSB uitvoert en een zelfstandige primaire site uitbreidt door een nieuwe centrale beheersite installeert, moet u Setup en de bronbestanden van de basislijnmedia versie 1606 gebruiken. Voor de huidige vertakking u Setup uitvoert en de bronbestanden vanaf de CD. Meest recente map.

Hoewel u niet het installatieprogramma voor site-uitbreiding vanaf de CD uitvoert. Meest recente map u blijven gebruiken van de CD. Meest recente map voor site recovery en een nieuwe onderliggende primaire site wordt geïnstalleerd wanneer u uw eerste LTSB-site is een centrale beheersite.

Zie voor meer informatie over site-uitbreiding, [een zelfstandige primaire site uitbreiden](/sccm/core/servers/deploy/install/use-the-setup-wizard-to-install-sites#expand-a-stand-alone-primary-site). Voor meer informatie over de CD. Meest recente map, Zie [de CD. Meest recente map](/sccm/core/servers/manage/the-cd.latest-folder).


## <a name="recovery"></a>Herstel
Wanneer u een site herstelt, moet u de site of de sitedatabase herstellen naar de oorspronkelijke vertakking. U kunt een Current Branch-sitedatabase niet herstellen naar een LTSB-installatie of vice versa.
