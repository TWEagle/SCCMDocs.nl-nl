---
title: Setup hybride MDM | Microsoft-documenten
description: Hybride apparaatinschrijving met Configuration Manager en Intune instellen.
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
ms.openlocfilehash: c494fcc38955571c06507278a1ae88e5777b5708
ms.contentlocale: nl-nl
ms.lasthandoff: 05/17/2017

---

# <a name="setup-hybrid-mobile-device-management-mdm-with-system-center-configuration-manager-and-microsoft-intune"></a>Hybride mobiel Apparaatbeheer (MDM) met System Center Configuration Manager en Microsoft Intune instellen

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*


Voordat u iOS-, Windows- en Android-apparaten met Configuration Manager beheren kunt, moet het worden ingeschreven met Intune. Gebruik de volgende stappen naar setup hybride apparaatinschrijving met Configuration Manager, met behulp van Intune. Via de volgende stappen hanteert u 'bring your own device' (BYOD) inschrijven voor uw gebruikers. Deze stappen zijn ook vereisten voor [BYOD-apparaten inschrijven](enroll-hybrid-ios-mac.md) en [apparaten eigendom van het bedrijf inschrijven](enroll-company-owned-devices.md).

 |Stappen|Details|  
 |-----------|-------------|  
 |**Stap 1:** [Een verzameling MDM maken](create-mdm-collection.md)|Maak een Gebruikersverzameling van Configuration Manager met gebruikers wiens apparaten worden ingeschreven.|  
 |**Stap 2:** [Vereisten voor de naam van het domein](confirm-dns.md)|Bevestigen van uw organisatie domain name service (DNS) en Active Directory-Gebruikersbeheer MDM voldoet|
 |**Stap 3:** [Intune-abonnement configureren](configure-intune-subscription.md)|De Intune-service kunt u apparaten beheren via het Internet.|  
 |**Stap 4:** [Voorwaarden toevoegen](terms-and-conditions.md)| Voorwaarden en bepalingen waarnaar gebruikers moeten akkoord gaan voordat ze de bedrijfsportal-app kunt maken|
 |**Stap 5:** [Het service connection point maken](create-service-connection-point.md)|De service connection point verzendt instellingen en software-implementatiegegevens naar Configuration Manager en krijgt status- en inventarisberichten van mobiele apparaten. |  
 |**Stap 6:** [Platform-inschrijving inschakelen](enable-platform-enrollment.md)|MDM-registratie voor iOS en Windows-apparaten zijn extra stappen vereist voor communicatie tussen de service en de apparaten. Android is geen aanvullende configuratie vereist.|  
 |**Stap 7:** [Extra beheer instellen](set-up-additional-management.md)|(Optioneel) Configuratie-items en voorwaardelijke toegang voor geregistreerde apparaten instellen|
 |**Stap 8:** [Controleer of de MDM-configuratie](verify-mdm-configuration.md)|Logboekbestanden weergeven om te bevestigen dat de service connection point is gemaakt en gebruikersaccounts die zijn gesynchroniseerd.|

Op zoek naar Intune zonder Configuration Manager?
> [!div class="button"]
[Intune documenten weergeven >](https://docs.microsoft.com/intune/deploy-use/enroll-devices-in-microsoft-intune)


## <a name="enroll-devices"></a>Apparaten inschrijven
Nadat de hybride setup is voltooid, kunnen apparaten worden ingeschreven in Configuration Manager op een aantal verschillende manieren:
- **Eigendom van het bedrijf (COD)-apparaten:** [Apparaten van het bedrijf inschrijven](enroll-company-owned-devices.md) biedt richtlijnen voor verschillende manieren platform-specifieke apparaten eigendom van het bedrijf in te schrijven.
- **Eigendom van gebruiker (BYOD)-apparaten:** [Eigendom van gebruiker (BYOD)-apparaten inschrijven](enroll-hybrid-ios-mac.md) biedt richtlijnen voor manieren om eigendom van gebruiker apparaten te registreren.

