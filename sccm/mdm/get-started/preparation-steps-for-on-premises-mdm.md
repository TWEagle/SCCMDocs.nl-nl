---
title: Voorbereidende stappen | Microsoft-documenten
description: Voorbereiden voor het beheren van apparaten met On-premises mobiele apparaten beheren in System Center Configuration Manager.
ms.custom: na
ms.date: 03/05/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-hybrid
ms.tgt_pltfrm: na
ms.topic: get-started-article
ms.assetid: 1ef60106-8f31-46d6-95a6-25a6495f22c7
caps.latest.revision: 4
author: Mtillman
ms.author: mtillman
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 6424fb07802b62820b4dc78a58ab30d3b956abef
ms.openlocfilehash: 85bdadaaaeed9a42cfa5165d2b9f0f3ef434dc03
ms.contentlocale: nl-nl
ms.lasthandoff: 05/17/2017


---
# <a name="preparation-steps-for-on-premises-mobile-device-management-in-system-center-configuration-manager"></a>Voorbereidingsstappen voor on-premises Mobile Device Management in System Center Configuration Manager

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*

Beheer van apparaten met System Center Configuration Manager op\-premises beheer van mobiele apparaten vereist de Configuration Manager-infrastructuur om te worden ingesteld zodat de vereiste sitesysteemrollen (proxypunt voor inschrijving, registratiepunt beheerpunt en distributiepunt) via een vertrouwde kanaal kunnen communiceren met de mobiele apparaten worden beheerd.  

 De volgende taken op hoog niveau nodig zijn voor de Configuration Manager-systeem voor het voorbereiden op\-premises beheer van mobiele apparaten:  

-   [Een abonnement op Microsoft Intune instellen voor On-premises mobiele apparaten beheren in System Center Configuration Manager](../../mdm/get-started/set-up-intune-subscription-on-premises-mdm.md)  

     In deze taak kunt u aanmelden voor Microsoft Intune en voegt u het abonnement voor Configuration Manager via de Configuration Manager-console. Deze stap is uitsluitend vereist voor licentieverlening. Intune wordt niet gebruikt om de apparaten te beheren of beheergegevens opslaan. Alle coördinatie bij problemen en beheer van apparaten is met uw organisatie enterprise met behulp van de lokale Configuration Manager-infrastructuur.  

-   [Sitesysteemrollen installeren voor On-premises mobiele apparaten beheren in System Center Configuration Manager](../../mdm/get-started/install-site-system-roles-for-on-premises-mdm.md)  

     In deze taak Installeer en configureer de sitesysteemrollen om apparaten met de lokale Configuration Manager-infrastructuur te beheren. Op\-lokale beheer van mobiele apparaten minimaal vereist het proxypunt voor inschrijving, registratiepunt, beheerpunt en distributiepunt sitesysteemrollen.  

-   [Certificaten voor vertrouwde communicatie voor On-premises mobiele apparaten beheren in System Center Configuration Manager instellen](../../mdm/get-started/set-up-certificates-on-premises-mdm.md)  

     In deze taak configureert u de lokale Configuration Manager-infrastructuur zodat vertrouwde communicatie (HTTPS) tussen beheerde apparaten en de servers die als host fungeert voor de vereiste sitesysteemrollen.  

-   [Apparaatinschrijving voor On-premises mobiele apparaten beheren in System Center Configuration Manager instellen](../../mdm/get-started/set-up-device-enrollment-on-premises-mdm.md)  

     In deze taak verleent u toestemming aan gebruikers om computers en apparaten te registreren en installeert u het vertrouwde basiscertificaat op apparaten (meestal apparaten die geen lid zijn van het domein) om HTTPS-verbindingen met de sitesysteemservers toe te staan.  

