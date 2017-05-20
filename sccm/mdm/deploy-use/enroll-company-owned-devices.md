---
title: Registreren-bedrijfsapparaten - Configuration Manager | Microsoft-documenten
description: Meer informatie over verschillende methoden voor het bedrijf apparaten registreren voor hybride implementaties met Configuration Manager.
ms.custom: na
ms.date: 03/05/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-hybrid
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: e2754ce6-1460-4ddd-9050-2cc87e7964f4
caps.latest.revision: 13
author: mtillman
ms.author: mtillman
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 2c723fe7137a95df271c3612c88805efd8fb9a77
ms.openlocfilehash: f0b503d8c9eba2dd1b6eb4c41ec40c001b727326
ms.contentlocale: nl-nl
ms.lasthandoff: 05/17/2017


---
# <a name="enroll-company-owned-devices-for-hybrid-deployments-with-configuration-manager"></a>Eigendom van het bedrijf apparaten registreren voor hybride implementaties met Configuration Manager

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*

Organisatie of apparaten in Bedrijfseigendom (COD) kunnen worden gezet in het beheer van op verschillende manieren, al naar gelang het apparaat en hoe u het hebt aangeschaft.  

## <a name="enroll-device-enrollment-program-ios-devices"></a>Device Enrollment Program iOS-apparaten inschrijven  
 Een inschrijvingsprofiel implementeert 'draadloos' op apparaten die zijn aangeschaft via Apples Device Enrollment Program. Wanneer de gebruiker op het apparaat Configuratieassistent uitvoert, wordt het apparaat wordt ingeschreven in Intune.  Gebruikers kunnen apparaten die met DEP zijn ingeschreven, niet uitschrijven. Zie [inschrijving van iOS-Device Enrollment Program (DEP) voor hybride implementaties met Configuration Manager](../../mdm/deploy-use/ios-device-enrollment-program-for-hybrid.md).  

## <a name="enroll-ios-devices-with-apple-configurator"></a>IOS-apparaten inschrijven met Apple Configurator  
 Deze methode moet de beheerder USB verbinding maken met het iOS-apparaat naar een Mac-computer met Apple Configurator om vooraf de registratie te configureren. Apparaten worden vervolgens afgeleverd bij hun gebruikers de Configuratieassistent proces, het apparaat met hun werk- of schoolaccount-referenties configureren en de inschrijving te voltooien. Zie [iOS hybride inschrijven met Apple Configurator met Configuration Manager](../../mdm/deploy-use/ios-hybrid-enrollment-using-apple-configurator.md).  

## <a name="device-enrollment-manager"></a>Apparaatinschrijvingsbeheerder  
 Organisaties kunnen Intune gebruiken voor het beheren van grote aantallen mobiele apparaten met één gebruikersaccount een apparaatinschrijvingsbeheerder-account genoemd. Na het maken van een apparaatinschrijvingsbeheerder-account kan dat account worden gebruikt door een manager inschrijven van meer dan de standaard vijf apparaten op normale gebruikers standaard toegestaan. Inschrijven van apparaten met een apparaatinschrijvingsbeheerder werkt alleen voor apparaten die niet worden gebruikt door een specifieke gebruiker. Deze apparaten zijn geschikt voor verkooppunt of het hulpprogramma apps, bijvoorbeeld, maar ongeldige voor gebruikers die toegang nodig tot e-mailadres of bedrijf resources. Zie [apparaten inschrijven met de apparaatinschrijvingsbeheerder met Configuration Manager](../../mdm/deploy-use/enroll-devices-with-device-enrollment-manager.md).  

## <a name="user-affinity-for-managed-devices"></a>Affiniteit tussen gebruikers en beheerde apparaten  
 Wanneer u profielen voor apparaten in Bedrijfseigendom configureert, kan de beheerder opgeven of de beheerde apparaten ondersteunen *affiniteit tussen gebruikers en* die een specifieke gebruiker wordt geïdentificeerd met het apparaat. Op apparaten die zijn geconfigureerd met **user affinity** kan de bedrijfsportal-app worden geïnstalleerd en uitgevoerd om apps te downloaden en apparaten te beheren. Zie [affiniteit tussen gebruikers en hybride beheerde apparaten in Configuration Manager](../../mdm/deploy-use/user-affinity-for-hybrid-managed-devices.md).  

## <a name="manage-devices-with-activation-lock"></a>Apparaten beheren met Activeringsvergrendeling  
 Microsoft Intune kunt u iOS Activeringsvergrendeling, een functie van de Zoek mijn iPhone-app voor iOS 7.1 en hoger apparaten beheren. Activeringsvergrendeling is automatisch ingeschakeld wanneer de app Zoek mijn iPhone op een apparaat wordt gebruikt. Zie [iOS Activeringsvergrendeling met System Center Configuration Manager beheren](../../mdm/deploy-use/manage-ios-activation-lock.md).

 ## <a name="predeclare-devices-with-imei-or-ios-serial-numbers"></a>Apparaten met IMEI-nummer of iOS-serienummers predeclare

U kunt apparaten in Bedrijfseigendom identificeren door hun internationale station mobile equipment identity (IMEI) getallen of iOS-serienummers importeren. U kunt een apparaat IMEI getallen met door komma's gescheiden waarden (.csv)-bestand uploaden of u kunt de apparaatgegevens handmatig invoeren.  Zie [Predeclare apparaten met hardware-ID-nummers](../../mdm/deploy-use/predeclare-devices-with-hardware-id.md).

