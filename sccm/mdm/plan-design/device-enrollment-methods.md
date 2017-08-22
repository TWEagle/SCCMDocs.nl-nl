---
title: Registratiemethoden voor apparaten voor hybride MDM | Microsoft Docs
description: Registratiemethoden voor apparaten voor hybride MDM
ms.custom: na
ms.date: 03/05/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: configmgr-hybrid
ms.tgt_pltfrm: na
ms.topic: get-started-article
ms.assetid: b81d06dc-3844-4117-9937-16732a227994
caps.latest.revision: "9"
caps.handback.revision: "0"
author: Mtillman
ms.author: mtillman
manager: angrobe
ms.openlocfilehash: e09e639e939b846cdc162681f9d7bd4c39cd6fbf
ms.sourcegitcommit: 51fc48fb023f1e8d995c6c4eacfda7dbec4d0b2f
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 08/07/2017
---
# <a name="overview-of-device-enrollment-methods"></a>Overzicht van registratiemethoden voor apparaten

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*

Nadat u de Configuration Manager met Intune uitbreidt, kunt u registreren en beheren van apparaten in Bedrijfseigendom of gebruikers machtigen hun persoonlijke apparaten kunnen inschrijven. U kunt ook bedrijfsapparaten beheren met Intune met Configuration Manager.

De volgende tabel bevat registratiemethoden met hun ondersteunde mogelijkheden. Deze mogelijkheden zijn:
- **Wissen** -de fabrieksinstellingen van het apparaat, alle gegevens verwijderd. [Apparaten buiten gebruik stellen](../deploy-use/wipe-lock-reset-devices.md)
- **Affiniteit** -apparaten worden gekoppeld aan gebruikers. Vereist voor het beheer van mobiele toepassingen (MAM) en voorwaardelijke toegang tot bedrijfsgegevens. [Affiniteit tussen gebruikers](../deploy-use/user-affinity-for-hybrid-managed-devices.md)
- **Vergrendeling** voorkomen dat gebruikers het apparaat uit beheer verwijderd. iOS-apparaten vereisen modus onder supervisie actief voor vergrendeling. [Vergrendelen op afstand](../deploy-use/wipe-lock-reset-devices.md#remote-lock)

**iOS-registratiemethoden**

| **Methode** |  **Wissen** |  **Affiniteit**    |   **Vergrendelen** | **Details** |
|:---:|:---:|:---:|:---:|:---:|
|**[BYOD](#byod)** | Nee|    Ja |   Nee | [meer](../deploy-use/enable-platform-enrollment.md)|
|**[DEM](#dem)**|   Nee |Nee |Nee  | [meer](../deploy-use/enroll-devices-with-device-enrollment-manager.md)|
|**[DEP](#dep)**|   Ja |   Optioneel |  Optioneel|[meer](../deploy-use/ios-device-enrollment-program-for-hybrid.md)|
|**[USB-SA](#usb-sa)**| Ja |   Optioneel |  Nee| [meer](../deploy-use/ios-hybrid-enrollment-using-apple-configurator.md)|

**Windows- en Android-registratiemethoden**

| **Methode** |  **Wissen** |  **Affiniteit**    |   **Vergrendelen** | **Details**|
|:---:|:---:|:---:|:---:|:---:|:---:|
|**[BYOD](#byod)** | Nee|    Ja |   Nee | [meer](../deploy-use/enroll-hybrid-windows.md)|
|**[DEM](#dem)**|   Nee |Nee |Nee  |[meer](../deploy-use/enroll-devices-with-device-enrollment-manager.md)|

Voor een reeks van vraag die u helpen de juiste methode vinden, Zie [kiezen hoe u apparaten registreert](/intune/get-started/choose-how-to-enroll-devices1).

## <a name="byod"></a>BYOD
'Bring your own device' (BYOD) gebruikers de bedrijfsportal-app installeren en registreren van hun apparaat. Dit kunt gebruiken om gebruikers verbinding maken met het bedrijfsnetwerk, aan het domein of Azure Active Directory. Inschakelen van BYOD-inschrijving is een vereiste voor veel COD-scenario's voor de meeste platforms. Zie [Setup hybride MDM](../deploy-use/setup-hybrid-mdm.md). ([Terug naar de tabel](#overview-of-device-enrollment-methods))

## <a name="corporate-owned-devices"></a>Apparaten in Bedrijfseigendom
Apparaten in Bedrijfseigendom (COD) kunnen worden beheerd met de Configuration Manager-console. iOS-apparaten kunnen worden ingeschreven rechtstreeks via hulpprogramma's van Apple. Alle typen apparaten kunnen worden ingeschreven door een beheerder of manager met behulp van de manager voor apparaatregistratie. Apparaten met een IMEI-nummer worden ook geïdentificeerd en worden deze gelabeld als Bedrijfseigendom COD-scenario's te maken.

[Apparaten inschrijven waarvan het bedrijf de eigenaar is](../deploy-use/enroll-company-owned-devices.md)

### <a name="dem"></a>DEM
Apparaatinschrijvingsbeheerder is een speciaal gebruikersaccount gebruikt om te registreren en beheren van meerdere apparaten in Bedrijfseigendom. Beheerders kunnen de bedrijfsportal installeren en veel apparaten zonder gebruiker registreren. Meer informatie over [DEM](../deploy-use/enroll-devices-with-device-enrollment-manager.md). ([Terug naar de tabel](#overview-of-device-enrollment-methods))

### <a name="dep"></a>DEP
Apple Device Enrollment Program (DEP)-beheer kunt u beleid maken en implementeren 'draadloos' op iOS-apparaten die zijn gekocht en beheerd met DEP. Het apparaat wordt geregistreerd wanneer de gebruiker het apparaat voor het eerst inschakelt en de iOS-Configuratieassistent wordt uitgevoerd. Deze methode ondersteunt **iOS onder supervisie** modus die zorgt:
  - Vergrendelde registratie
  - Voorwaardelijke toegang
  - Jailbreakdetectie
  - Beheer van mobiele toepassingen

Meer informatie over [DEP](../deploy-use/ios-device-enrollment-program-for-hybrid.md). ([Terug naar de tabel](#overview-of-device-enrollment-methods))

### <a name="usb-sa"></a>USB-SA
Door USB verbonden registratie met Configuratieassistent. De beheerder maakt een beleid en exporteert het naar Apple Configurator. USB-verbinding, zakelijke eigendom apparaten worden voorbereid met het beleid. De beheerder moet elk apparaat handmatig registreren. Gebruikers ontvangen hun apparaten en voeren Configuratieassistent uit inschrijving van het apparaat. Deze methode ondersteunt **iOS onder supervisie** modus die zorgt:
  - Voorwaardelijke toegang
  - Jailbreakdetectie
  - Beheer van mobiele toepassingen

Meer informatie over [inschrijving via Configuratieassistent met Apple Configurator](../deploy-use/ios-hybrid-enrollment-using-apple-configurator.md). ([Terug naar de tabel](#overview-of-device-enrollment-methods))

## <a name="mobile-device-management-with-exchange-activesync-and-configuration-manager"></a>Mobile device management met Exchange ActiveSync en Configuration Manager
Mobiele apparaten die niet zijn geregistreerd, maar die verbinding maken met Exchange ActiveSync (EAS) kunnen worden beheerd door Intune met EAS MDM-beleid. Intune gebruikt een Exchange-Connector om te communiceren met EAS, on-premises en cloud-gebaseerde.

[Mobile device management met Exchange ActiveSync en Intune](../deploy-use/manage-mobile-devices-with-exchange-activesync.md)
