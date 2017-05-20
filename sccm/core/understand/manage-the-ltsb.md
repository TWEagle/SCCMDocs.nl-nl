---
title: Beheren van de LTSB | Microsoft-documenten
description: Beheer van de verschillen voor LTSB van System Center Configuration Manager.
ms.custom: na
ms.date: 05/01/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 8da2887a-fd8e-438c-b926-849c121f7fdf
caps.latest.revision: 0
author: Brenduns
ms.author: brenduns
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 31819a1df4e63e1114682490a9b3c3b4e5c99cfa
ms.openlocfilehash: 9c6f349ead906532a7a58df74609de976769e251
ms.contentlocale: nl-nl
ms.lasthandoff: 05/17/2017


---
# <a name="manage-the-long-term-servicing-branch-of-configuration-manager"></a>De lange termijn onderhoud vertakking van Configuration Manager beheren

*Van toepassing op: System Center Configuration Manager (op lange termijn onderhoud vertakking)*

Wanneer u de langetermijndoelen onderhoud vertakking (LTSB) van System Center Configuration Manager, kunt het volgende u informatie over belangrijke wijzigingen die van invloed op hoe u uw infrastructuur beheren.

Omdat de LTSB is gelijk aan het huidige vertakking versie 1606 (met enkele uitzonderingen zoals Intune-integratie en cloud-functies), zijn de meeste taken die u voor de planning, implementatie, configuratie en beheer van dagelijkse gebruikt hetzelfde.

De LTSB ondersteunt bijvoorbeeld hetzelfde aantal sites, site-typen, clients en algemene infrastructuur als de huidige vertakking. Daarom kunt u de richtlijnen gevonden in de site en hiërarchie onderwerpen over planning en ontwerp voor de huidige vertakking gebruiken. Op deze manier voor functies uit met de LTSB die worden ondersteund door zowel vertakkingen, zoals Software-Updates of implementatie van besturingssystemen gebruik van de richtlijnen in die gedeeltes van de huidige vertakking documentatie met de voorbehouden hebben geen toegang tot de functiewijzigingen die zijn geïntroduceerd na versie 1606 van de huidige vertakking gevonden.

De volgende secties bevatten informatie over taken die niet lijken te beheren.

## <a name="updates-and-servicing"></a>Updates en onderhoud
Alleen kritieke beveiligingsupdates worden beschikbaar gesteld als console updates in de LTSB.  

Informatie over regelmatig updates voor de volgende huidige vertakking releases in de console worden weergegeven, maar zijn niet beschikbaar gesteld aan de LTSB. Ze niet zijn gedownload en kunnen niet worden geïnstalleerd.

Een site LTSB vereist ter ondersteuning van updates in de console voor kritieke beveiligingsproblemen, het gebruik van [de service connection point](/sccm/core/servers/deploy/configure/about-the-service-connection-point). U kunt deze sitesysteemrol in de modus voor offline- of configureren zoals wordt uitgevoerd voor de huidige vertakking. De LTSB verzamelt en verstuurt dezelfde Telemetrie en het gebruik van gegevens als de huidige vertakking.

De LTSB ondersteunt het gebruik van het installatieprogramma Hotfix en het hulpprogramma registratie bijwerken, zoals beschreven voor de huidige vertakking.

Raadpleeg voor algemene informatie over updates en onderhoud [Updates voor Configuration Manager](/sccm/core/servers/manage/updates).


## <a name="changes-for-site-expansion-and-the-cdlatest-folder"></a>Wijzigingen voor site-uitbreiding en de CD. Meest recente map
Wanneer u de LTSB uitvoert en een zelfstandige primaire site uitbreidt door een nieuwe centrale beheersite installeert, moet u Setup en de bronbestanden van de versie 1606 basislijn media gebruiken. Voor de huidige vertakking u Setup uitvoert en de bronbestanden vanaf de CD. Meest recente map.

Hoewel u niet het installatieprogramma voor site-uitbreiding vanaf de CD uitvoert. Meest recente map u blijven gebruiken de CD. Meest recente map voor herstel van sites en voor het installeren van een nieuwe onderliggende primaire site wanneer u uw eerste site LTSB is een centrale beheersite.

Zie voor meer informatie over site-uitbreiding [een zelfstandige primaire site uitbreidt](/sccm/core/servers/deploy/install/use-the-setup-wizard-to-install-sites#expand-a-stand-alone-primary-site). Voor meer informatie over de CD. Meest recente map, Zie [de CD. Meest recente map](/sccm/core/servers/manage/the-cd.latest-folder).


## <a name="recovery"></a>Herstel
Wanneer u een site herstelt, moet u de site of de sitedatabase herstellen naar de oorspronkelijke vertakking. U kunt een vertakking van huidige site-database niet herstellen naar een LTSB-installatie, en vice versa.

