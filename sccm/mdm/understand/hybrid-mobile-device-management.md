---
title: Hybride mobile device management (MDM) met Microsoft Intune
titleSuffix: Configuration Manager
description: Meer informatie over hybride mobile device management (MDM) met System Center Configuration Manager en Microsoft Intune.
ms.custom: na
ms.date: 03/05/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: configmgr-hybrid
ms.tgt_pltfrm: na
ms.topic: get-started-article
ms.assetid: bb95154b-f63e-4491-896e-41d732c802f8
caps.latest.revision: "34"
caps.handback.revision: "0"
author: dougeby
ms.author: dougeby
manager: angrobe
ms.openlocfilehash: da817ac299115c1151851d302c1935ad3f956bdf
ms.sourcegitcommit: c236214b2fcc13dae7bad96d7fb33f692868191d
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/12/2017
---
# <a name="hybrid-mobile-device-management-mdm-with-system-center-configuration-manager-and-microsoft-intune"></a>Hybride Mobile Device Management (MDM) met System Center Configuration Manager en Microsoft Intune

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*


U kunt iOS-, Windows- en Android-apparaten met Configuration Manager en Microsoft Intune beheren. Alle beheertaken worden verwerkt vanuit de Configuration Manager-console waar u de rest van uw beheertaken naadloos geïntegreerd met online van Microsoft Intune-service via internet uitvoert.  Configuration Manager kunt u gebruikers toegang tot bedrijfsbronnen op hun apparaten kunnen op een beveiligde, beheerde manier. Met behulp van Apparaatbeheer, beveiligt u bedrijfsgegevens en kunnen gebruikers registreren hun persoonlijke of bedrijfseigen apparaten voor toegang tot bedrijfsgegevens. Beheermogelijkheden op apparaten:

-   Apparaten buiten gebruik stellen en wissen
-   Instellingen voor naleving configureren, zoals wachtwoorden, beveiliging, roaming, versleuteling en draadloze communicatie
-   Line-of-business (LOB)-apps implementeren op apparaten
-   Apps implementeren naar apparaten die zijn verbonden met Windows Store, Windows Phone Store, App Store of Google Play
-   Hardware-inventaris verzamelen
-   Software-inventaris verzamelen met behulp van de ingebouwde rapporten

Als u wilt lezen over de nieuwe functies beschikbaar zijn voor hybride MDM, Zie [wat is er nieuw in hybride mobile device management](../understand/whats-new-in-hybrid-mobile-device-management.md).

Dit document wordt ervan uitgegaan dat u Configuration Manager gebruikt voor het beheren van computers en u bent geïnteresseerd in de uitbreiding van de Configuration Manager-console met Intune om mobiele apparaten te beheren. Zie voor informatie over de verschillen tussen Intune en hybride beheer van mobiele apparaten, [kiezen tussen Microsoft Intune standalone en hybride beheer van mobiele apparaten met System Center Configuration Manager](choose-between-standalone-intune-and-hybrid-mobile-device-management.md).

Na het uitbreiden van Configuration Manager met Intune kunnen inschrijven en beheren van apparaten in Bedrijfseigendom of gebruikers machtigen hun persoonlijke apparaten kunnen inschrijven. U kunt ook bedrijfsapparaten beheren met Intune met Configuration Manager.

## <a name="hybrid-mdm-enrollment"></a>Hybride MDM-registratie
Om apparaten in het beheer van hybride, moeten die apparaten worden geregistreerd bij de service. Hoe de apparaten voor het inschrijven van apparaten, is afhankelijk van het apparaattype, eigendom en uw beheerniveau nodig.
- 'Bring your own device' (BYOD) inschrijven kan gebruikers registreren hun persoonlijke telefoons, tablets of pc's.
- Apparaat in Bedrijfseigendom (COD)-inschrijving kunt scenario's zoals wissen op afstand, gedeelde apparaten of affiniteit tussen gebruikers en voor een apparaat voor beheer.
- Als u [Exchange ActiveSync](../plan-design/device-enrollment-methods.md#mobile-device-management-with-exchange-activesync-and-configuration-manager), on-premises of gehost in de cloud, kunt u eenvoudige Intune-beheer zonder inschrijving inschakelen. Windows-pc's kunnen ook worden beheerd via [Intune-clientsoftware](/intune/deploy-use/manage-windows-pcs-with-microsoft-intune).
