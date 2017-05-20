---
title: Hybride beheer van mobiele apparaten (MDM) - Configuration Manager & Microsoft Intune | Microsoft-documenten
description: Meer informatie over hybride mobiel Apparaatbeheer (MDM) met System Center Configuration Manager en Microsoft Intune.
ms.custom: na
ms.date: 03/05/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-hybrid
ms.tgt_pltfrm: na
ms.topic: get-started-article
ms.assetid: bb95154b-f63e-4491-896e-41d732c802f8
caps.latest.revision: 34
caps.handback.revision: 0
author: mtillman
ms.author: mtillman
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 2c723fe7137a95df271c3612c88805efd8fb9a77
ms.openlocfilehash: e54478a03807c939ffa64ff39a21ef6f9ea4ae2d
ms.contentlocale: nl-nl
ms.lasthandoff: 05/17/2017

---
# <a name="hybrid-mobile-device-management-mdm-with-system-center-configuration-manager-and-microsoft-intune"></a>Hybride Mobile Device Management (MDM) met System Center Configuration Manager en Microsoft Intune

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*


U kunt iOS-, Windows- en Android-apparaten met Configuration Manager en Microsoft Intune beheren. Alle beheertaken worden behandeld vanuit de Configuration Manager-console waar u de rest van uw beheertaken naadloos geïntegreerd met online van Microsoft Intune-service via internet uitvoert.  Configuration Manager kunt u gebruikers toegang tot bedrijfsbronnen op hun apparaten kunnen op een veilige, begeleide wijze. Via beheer van apparaten, beveiligt u de bedrijfsgegevens en laat gebruikers schrijven hun apparaten in persoonlijk of Bedrijfseigendom voor toegang tot bedrijfsgegevens toe. Mogelijkheden voor Computerbeheer op apparaten:

-   Apparaten buiten gebruik stellen en wissen
-   Instellingen voor naleving configureren, zoals wachtwoorden, beveiliging, roaming, versleuteling en draadloze communicatie
-   Line-of-business (LOB)-apps implementeren op apparaten
-   Apps implementeren naar apparaten die zijn verbonden met Windows Store, Windows Phone Store, App Store of Google Play
-   Hardware-inventaris verzamelen
-   Software-inventaris verzamelen met behulp van de ingebouwde rapporten

Raadpleeg voor meer over de nieuwe functies zijn beschikbaar voor hybride MDM [wat is nieuw in beheer van mobiele apparaten hybride](../understand/whats-new-in-hybrid-mobile-device-management.md).

Dit document wordt ervan uitgegaan dat u van Configuration Manager gebruikmaakt voor het beheren van computers en dat u geïnteresseerd bent in de console Configuration Manager met Intune om mobiele apparaten te beheren uitbreiden. Zie voor inzicht in de verschillen tussen Intune en hybride beheer van mobiele apparaten, [kiezen tussen Microsoft Intune zelfstandige en hybride beheer van mobiele apparaten met System Center Configuration Manager](choose-between-standalone-intune-and-hybrid-mobile-device-management.md).

Na het uitbreiden van Configuration Manager met Intune kunnen inschrijven en beheren van apparaten in Bedrijfseigendom of gebruikers machtigen om in te schrijven hun persoonlijke apparaten. U kunt ook-bedrijfsapparaten beheren met Intune met Configuration Manager.

## <a name="hybrid-mdm-enrollment"></a>Hybride MDM-registratie
Om apparaten in het beheer van hybride, moeten die apparaten worden geregistreerd bij de service. Hoe apparaten worden ingeschreven apparaten, is afhankelijk van het apparaattype, eigendom en uw beheerniveau nodig.
- 'Bring your own device' (BYOD) inschrijven kiest, kunnen gebruikers schrijven hun persoonlijke telefoons, tablets en pc's.
- Inschrijving van het apparaat in Bedrijfseigendom (COD) kan beheerscenario's zoals wissen op afstand, gedeelde apparaten of affiniteit tussen gebruikers en een apparaat.
- Als u [Exchange ActiveSync](../plan-design/device-enrollment-methods.md#mobile-device-management-with-exchange-activesync-and-configuration-manager), op locatie of gehost in de cloud, kunt u eenvoudige Intune beheer zonder inschrijving inschakelen. Windows-pc's kunnen ook worden beheerd via [Intune-clientsoftware](/intune/deploy-use/manage-windows-pcs-with-microsoft-intune).

