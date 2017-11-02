---
title: Hybride MDM instellen
titleSuffix: Configuration Manager
description: Registratie van hybride-apparaten met Configuration Manager en Intune instellen.
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
ms.openlocfilehash: 63b49cbef7c584b0bc77752ec9b0e89811c68494
ms.sourcegitcommit: c236214b2fcc13dae7bad96d7fb33f692868191d
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/12/2017
---
# <a name="setup-hybrid-mobile-device-management-mdm-with-system-center-configuration-manager-and-microsoft-intune"></a>Hybride mobile device management (MDM) met System Center Configuration Manager en Microsoft Intune instellen

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*


Voordat u iOS-, Windows- en Android-apparaten met Configuration Manager beheren kunt, moeten ze worden geregistreerd bij Intune. Gebruik de volgende stappen voor het installatieprogramma hybride apparaatinschrijving met Configuration Manager, met behulp van Intune. De volgende stappen hanteert u 'bring your own device' (BYOD) inschrijven voor uw gebruikers. Deze stappen zijn ook vereisten voor [BYOD-apparaten inschrijven](enroll-hybrid-ios-mac.md) en [apparaten in Bedrijfseigendom inschrijven](enroll-company-owned-devices.md).

 |Stappen|Details|  
 |-----------|-------------|  
 |**Stap 1:** [Een MDM-verzameling maken](create-mdm-collection.md)|Maak een Configuration Manager Gebruikersverzameling met gebruikers wiens apparaten kunnen worden ingeschreven.|  
 |**Stap 2:** [Vereisten voor de naam van het domein](confirm-dns.md)|Bevestig uw organisatie domeinnaamservices (DNS) en beheer van Active Directory-gebruikers voldoet aan MDM-vereisten|
 |**Stap 3:** [Intune-abonnement configureren](configure-intune-subscription.md)|De Intune-service kunt u apparaten beheren via het Internet.|  
 |**Stap 4:** [Voorwaarden toevoegen](terms-and-conditions.md)| Voorwaarden en bepalingen waaraan gebruikers moeten akkoord gaan voordat ze de bedrijfsportal-app kunt maken|
 |**Stap 5:** [Serviceverbindingspunt maken](create-service-connection-point.md)|Het serviceaansluitpunt verzendt instellingen en software-implementatiegegevens naar Configuration Manager en krijgt status- en inventarisberichten van mobiele apparaten. |  
 |**Stap 6:** [Platforminschrijving inschakelen](enable-platform-enrollment.md)|MDM-inschrijving voor iOS en Windows-apparaten zijn extra stappen vereist voor communicatie tussen de service en de apparaten. Android is geen aanvullende configuratie vereist.|  
 |**Stap 7:** [Aanvullend beheer instellen](set-up-additional-management.md)|(Optioneel) Configuratie-items en voorwaardelijke toegang voor geregistreerde apparaten instellen|
 |**Stap 8:** [MDM-configuratie controleren](verify-mdm-configuration.md)|Logboekbestanden weergeven om te bevestigen dat het service connection point is gemaakt en gebruikersaccounts worden gesynchroniseerd.|

Zoekt u Intune zonder Configuration Manager?
> [!div class="button"]
[Intune documenten weergeven >](https://docs.microsoft.com/intune/deploy-use/enroll-devices-in-microsoft-intune)


## <a name="enroll-devices"></a>Apparaten inschrijven
Nadat u hybride setup is voltooid, kunnen apparaten in Configuration Manager op een aantal verschillende manieren worden geregistreerd:
- **Bedrijfseigendom (COD)-apparaten:** [Apparaten in Bedrijfseigendom inschrijven](enroll-company-owned-devices.md) biedt richtlijnen voor verschillende platform-specifieke manieren bedrijfseigen apparaten te registreren.
- **Eigendom van gebruiker (BYOD)-apparaten:** [Apparaten in eigendom van gebruiker (BYOD) inschrijven](enroll-hybrid-ios-mac.md) biedt richtlijnen voor manieren inschrijven van apparaten van gebruikers.
