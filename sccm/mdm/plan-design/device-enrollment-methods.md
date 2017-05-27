---
title: Device Enrollment methoden voor het hybride MDM | Microsoft-documenten
description: Device enrollment methoden voor het hybride MDM
ms.custom: na
ms.date: 03/05/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-hybrid
ms.tgt_pltfrm: na
ms.topic: get-started-article
ms.assetid: b81d06dc-3844-4117-9937-16732a227994
caps.latest.revision: 9
caps.handback.revision: 0
author: Mtillman
ms.author: mtillman
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 6424fb07802b62820b4dc78a58ab30d3b956abef
ms.openlocfilehash: e09e639e939b846cdc162681f9d7bd4c39cd6fbf
ms.contentlocale: nl-nl
ms.lasthandoff: 05/17/2017


---
# <a name="overview-of-device-enrollment-methods"></a>Overzicht van methoden van apparaten voor certificaatinschrijving

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*

Nadat u de Configuration Manager met Intune uitbreidt, kunt u inschrijven en beheren van apparaten in Bedrijfseigendom of gebruikers machtigen om in te schrijven hun persoonlijke apparaten. U kunt ook-bedrijfsapparaten beheren met Intune met Configuration Manager.

De volgende tabel toont de van inschrijvingsmethoden met hun ondersteunde mogelijkheden. Deze mogelijkheden zijn:
- **Wissen** -fabrieksinstellingen het apparaat, alle gegevens verwijderd. [Apparaten buiten gebruik stellen](../deploy-use/wipe-lock-reset-devices.md)
- **Affiniteit** -apparaten wordt gekoppeld aan gebruikers. Vereist voor het beheer van mobiele toepassingen (MAM) en voorwaardelijke toegang tot bedrijfsgegevens. [Affiniteit tussen gebruikers](../deploy-use/user-affinity-for-hybrid-managed-devices.md)
- **Vergrendeling** wordt voorkomen dat gebruikers het apparaat verwijdert uit het beheer. iOS-apparaten vereisen Supervised modus voor vergrendeling. [Vergrendelen op afstand](../deploy-use/wipe-lock-reset-devices.md#remote-lock)

**methoden voor iOS-inschrijving**

| **Methode** |    **Wissen** |    **Affiniteit**    |    **Vergrendelen** | **Details** |
|:---:|:---:|:---:|:---:|:---:|
|**[BYOD](#byod)** | Nee|    Ja |    Nee | [meer](../deploy-use/enable-platform-enrollment.md)|
|**[DEM](#dem)**|    Nee |Nee |Nee    | [meer](../deploy-use/enroll-devices-with-device-enrollment-manager.md)|
|**[DEP](#dep)**|    Ja |    Optioneel |    Optioneel|[meer](../deploy-use/ios-device-enrollment-program-for-hybrid.md)|
|**[USB-SA](#usb-sa)**|    Ja |    Optioneel |    Nee| [meer](../deploy-use/ios-hybrid-enrollment-using-apple-configurator.md)|

**Windows- en Android-inschrijvingsmethoden**

| **Methode** |    **Wissen** |    **Affiniteit**    |    **Vergrendelen** | **Details**|
|:---:|:---:|:---:|:---:|:---:|:---:|
|**[BYOD](#byod)** | Nee|    Ja |    Nee | [meer](../deploy-use/enroll-hybrid-windows.md)|
|**[DEM](#dem)**|    Nee |Nee |Nee    |[meer](../deploy-use/enroll-devices-with-device-enrollment-manager.md)|

Voor een reeks vraag die u helpen de juiste methode vinden, Zie [kiezen hoe u apparaten in te schrijven](/intune/get-started/choose-how-to-enroll-devices1).

## <a name="byod"></a>BYOD
'Bring your own device' (BYOD) gebruikers de bedrijfsportal-app installeren en het inschrijven van hun apparaat. Hiermee kunt gebruikers verbinding maken met het bedrijfsnetwerk aan het domein of Azure Active Directory. Inschakelen van BYOD is inschrijving een vereiste voor veel Kabeljauw scenario's voor de meeste platforms. Zie [Setup hybride MDM](../deploy-use/setup-hybrid-mdm.md). ([Terug naar de tabel](#overview-of-device-enrollment-methods))

## <a name="corporate-owned-devices"></a>Apparaten van bedrijf
Apparaten in Bedrijfseigendom (COD) kunnen worden beheerd met de Configuration Manager-console. iOS-apparaten kunnen worden ingeschreven rechtstreeks in hulpprogramma's van Apple. Alle typen apparaten kunnen worden ingeschreven door een beheerder of manager met de apparaatinschrijvingsbeheerder. Apparaten met een IMEI-nummer worden ook geïdentificeerd en gemarkeerd als eigendom van het bedrijf om in te schakelen Kabeljauw scenario's.

[Apparaten in Bedrijfseigendom inschrijven](../deploy-use/enroll-company-owned-devices.md)

### <a name="dem"></a>DEM
Apparaatinschrijvingsbeheerder is een speciaal gebruikersaccount gebruikt voor het inschrijven en beheren van meerdere apparaten in Bedrijfseigendom. Managers kunnen de bedrijfsportal installeren en veel gebruikersloos apparaten inschrijven. Meer informatie over [DEM](../deploy-use/enroll-devices-with-device-enrollment-manager.md). ([Terug naar de tabel](#overview-of-device-enrollment-methods))

### <a name="dep"></a>DEP
Beheer van Apple Device Enrollment Program (DEP) kunt u beleid maken en implementeren 'draadloos' op iOS-apparaten die zijn gekocht en beheerd met DEP. Het apparaat wordt geregistreerd wanneer de gebruiker op het apparaat voor de eerste keer wordt, en de iOS-Configuratieassistent wordt uitgevoerd. Deze methode ondersteunt **iOS Supervised** modus waarmee op zijn beurt:
  -    Vergrendelde inschrijving
  -    Voorwaardelijke toegang
  -    Detectie van jailbreakdetectie
  -    Beheer van mobiele toepassingen

Meer informatie over [DEP](../deploy-use/ios-device-enrollment-program-for-hybrid.md). ([Terug naar de tabel](#overview-of-device-enrollment-methods))

### <a name="usb-sa"></a>USB-SA
USB-adapter zijn verbonden, Configuratieassistent inschrijving. De beheerder maakt een beleid en exporteert u het naar Apple Configurator. USB-adapter zijn verbonden, Bedrijfseigendom apparaten zijn voorbereid met het beleid. De beheerder moet elk apparaat handmatig registreren. Gebruikers hun apparaten ontvangen en Configuratieassistent, hun apparaat inschrijven. Deze methode ondersteunt **iOS Supervised** modus waarmee op zijn beurt:
  -    Voorwaardelijke toegang
  -    Detectie van jailbreakdetectie
  -    Beheer van mobiele toepassingen

Meer informatie over [Configuratieassistent inschrijven met Apple Configurator](../deploy-use/ios-hybrid-enrollment-using-apple-configurator.md). ([Terug naar de tabel](#overview-of-device-enrollment-methods))

## <a name="mobile-device-management-with-exchange-activesync-and-configuration-manager"></a>Beheer van mobiele apparaten met Exchange ActiveSync en Configuration Manager
Mobiele apparaten die niet zijn geregistreerd, maar die verbinding maken met Exchange ActiveSync (EAS) kunnen worden beheerd door Intune met behulp van MDM EAS-beleid. Intune een Exchange-Connector gebruikt om te communiceren met EAS op locatie en cloud wordt gehost.

[Beheer van mobiele apparaten met Exchange ActiveSync en Intune](../deploy-use/manage-mobile-devices-with-exchange-activesync.md)

