---
title: Voorbereidende stappen | Microsoft Docs
description: Voorbereiden voor het beheren van apparaten met On-premises Mobile Device Management in System Center Configuration Manager.
ms.custom: na
ms.date: 03/05/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: configmgr-hybrid
ms.tgt_pltfrm: na
ms.topic: get-started-article
ms.assetid: 1ef60106-8f31-46d6-95a6-25a6495f22c7
caps.latest.revision: "4"
author: Mtillman
ms.author: mtillman
manager: angrobe
ms.openlocfilehash: 85bdadaaaeed9a42cfa5165d2b9f0f3ef434dc03
ms.sourcegitcommit: 51fc48fb023f1e8d995c6c4eacfda7dbec4d0b2f
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 08/07/2017
---
# <a name="preparation-steps-for-on-premises-mobile-device-management-in-system-center-configuration-manager"></a>Voorbereidingsstappen voor on-premises Mobile Device Management in System Center Configuration Manager

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*

Apparaten beheren met System Center Configuration Manager op\-premises Mobile Device Management is vereist voor de Configuration Manager-infrastructuur worden ingesteld zodat de vereiste sitesysteemrollen (proxypunt voor inschrijving, inschrijvingspunt, apparaatbeheerpunt en distributiepunt) via een vertrouwd kanaal kunnen communiceren met de mobiele apparaten worden beheerd.  

 De volgende taken op hoog niveau zijn nodig voor het voorbereiden van de Configuration Manager-systeem voor op\-premises Mobile Device Management:  

-   [Een Microsoft Intune-abonnement instellen voor On-premises Mobile Device Management in System Center Configuration Manager](../../mdm/get-started/set-up-intune-subscription-on-premises-mdm.md)  

     Aanmelden voor Microsoft Intune in deze taak en voeg vervolgens het abonnement naar Configuration Manager via de Configuration Manager-console. Deze stap is uitsluitend vereist voor licentieverlening. Intune wordt niet gebruikt voor de apparaten te beheren of beheergegevens worden opgeslagen. Alle coördinatie en beheer van apparaten is met uw bedrijfsorganisatie met behulp van de on-premises Configuration Manager-infrastructuur.  

-   [Sitesysteemrollen installeren voor On-premises Mobile Device Management in System Center Configuration Manager](../../mdm/get-started/install-site-system-roles-for-on-premises-mdm.md)  

     In deze taak installeren en configureren van de sitesysteemrollen die zijn vereist voor het beheren van apparaten met on-premises Configuration Manager-infrastructuur. Op\-premises Mobile Device Management minimaal vereist het proxypunt voor inschrijving, inschrijvingspunt, apparaatbeheerpunt en distributiepunt sitesysteemrollen.  

-   [Certificaten voor vertrouwde communicatie voor On-premises Mobile Device Management in System Center Configuration Manager instellen](../../mdm/get-started/set-up-certificates-on-premises-mdm.md)  

     In deze taak configureert u de on-premises Configuration Manager-infrastructuur zodat vertrouwde communicatie (HTTPS) tussen beheerde apparaten en de servers die als host fungeert voor de vereiste sitesysteemrollen.  

-   [Registratie van apparaten instellen voor On-premises Mobile Device Management in System Center Configuration Manager](../../mdm/get-started/set-up-device-enrollment-on-premises-mdm.md)  

     In deze taak verleent u toestemming aan gebruikers om computers en apparaten te registreren en installeert u het vertrouwde basiscertificaat op apparaten (meestal apparaten die geen lid zijn van het domein) om HTTPS-verbindingen met de sitesysteemservers toe te staan.  
