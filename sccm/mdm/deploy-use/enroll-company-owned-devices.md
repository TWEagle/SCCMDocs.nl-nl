---
title: 'Apparaten in Bedrijfseigendom inschrijven '
titleSuffix: Configuration Manager
description: Meer informatie over de verschillende methoden voor het inschrijven van apparaten in Bedrijfseigendom voor hybride implementaties met Configuration Manager.
ms.custom: na
ms.date: 03/05/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: configmgr-hybrid
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: e2754ce6-1460-4ddd-9050-2cc87e7964f4
caps.latest.revision: "13"
author: dougeby
ms.author: dougeby
manager: angrobe
ms.openlocfilehash: 5b1e05e45ec6193eeef5e48cfa8d8476a92dde56
ms.sourcegitcommit: c236214b2fcc13dae7bad96d7fb33f692868191d
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/12/2017
---
# <a name="enroll-company-owned-devices-for-hybrid-deployments-with-configuration-manager"></a>Bedrijfseigen apparaten registreren voor hybride implementaties met Configuration Manager

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*

Organisatie- of apparaten in Bedrijfseigendom (COD) kunnen worden gezet kunnen op verschillende manieren, al naar gelang het apparaat en hoe u het hebt aangeschaft.  

## <a name="enroll-device-enrollment-program-ios-devices"></a>Device Enrollment Program iOS-apparaten inschrijven  
 Een inschrijvingsprofiel implementeert 'draadloos' op apparaten die zijn aangeschaft via Apples Device Enrollment Program. Wanneer de gebruiker op het apparaat Configuratieassistent uitvoert, wordt het apparaat is ingeschreven bij Intune.  Gebruikers kunnen apparaten die met DEP zijn ingeschreven, niet uitschrijven. Zie [iOS Device Enrollment Program (DEP)-inschrijving voor hybride implementaties met Configuration Manager](../../mdm/deploy-use/ios-device-enrollment-program-for-hybrid.md).  

## <a name="enroll-ios-devices-with-apple-configurator"></a>IOS-apparaten inschrijven met Apple Configurator  
 Deze methode moet de beheerder een USB verbinding maken met het iOS-apparaat met een Mac-computer met Apple Configurator om de registratie vooraf te configureren. Apparaten zijn vervolgens aan hun gebruikers die de Configuratieassistent wordt uitgevoerd voor het configureren van het apparaat met de referenties van hun werk- of schoolaccount en het registratieproces voltooien geleverd. Zie [iOS hybride-inschrijving met Apple Configurator met Configuration Manager](../../mdm/deploy-use/ios-hybrid-enrollment-using-apple-configurator.md).  

## <a name="device-enrollment-manager"></a>Apparaatinschrijvingsmanager  
 Organisaties kunnen Intune gebruiken voor het beheren van grote aantallen mobiele apparaten met één gebruikersaccount een apparaatinschrijvingsbeheerder-account genoemd. Nadat een apparaatregistratiebeheeraccount is gemaakt, kan dat account worden gebruikt door een beheerder om meer dan de vijf apparaten op normale gebruikers standaard toegestaan te schrijven. Inschrijven van apparaten met een apparaatregistratiebeheer werkt alleen voor apparaten die niet worden gebruikt door een specifieke gebruiker. Deze apparaten zijn geschikt is voor het verkooppunt of het hulpprogramma apps, bijvoorbeeld, maar niet voor gebruikers die toegang tot e-mail of bedrijfsbronnen nodig. Zie [apparaten inschrijven met apparaatregistratiebeheer met Configuration Manager](../../mdm/deploy-use/enroll-devices-with-device-enrollment-manager.md).  

## <a name="user-affinity-for-managed-devices"></a>Affiniteit tussen gebruikers en voor beheerde apparaten  
 Wanneer u profielen voor apparaten in Bedrijfseigendom configureert, kan de beheerder opgeven of de beheerde apparaten ondersteunen *gebruikersaffiniteit* die een specifieke gebruiker identificeert met het apparaat. Op apparaten die zijn geconfigureerd met **user affinity** kan de bedrijfsportal-app worden geïnstalleerd en uitgevoerd om apps te downloaden en apparaten te beheren. Zie [gebruikersaffiniteit voor hybride beheerde apparaten in Configuration Manager](../../mdm/deploy-use/user-affinity-for-hybrid-managed-devices.md).  

## <a name="manage-devices-with-activation-lock"></a>Apparaten beheren met Activeringsvergrendeling  
 Microsoft Intune kunt u iOS-Activeringsvergrendeling, een functie van de Zoek mijn iPhone-app voor iOS 7.1 en hoger apparaten beheren. Activeringsvergrendeling is automatisch ingeschakeld wanneer de app Zoek mijn iPhone op een apparaat wordt gebruikt. Zie [beheren van iOS-Activeringsvergrendeling met System Center Configuration Manager](../../mdm/deploy-use/manage-ios-activation-lock.md).

 ## <a name="predeclare-devices-with-imei-or-ios-serial-numbers"></a>Apparaten met IMEI-nummer of iOS-serienummers labelen

U kunt apparaten in Bedrijfseigendom identificeren met hun nummers van international station mobile equipment identity (IMEI-nummer) of een iOS-serienummers importeren. U kunt een door komma's gescheiden waarden (.csv)-bestand met IMEI-nummers van apparaten uploaden of u kunt de apparaatgegevens handmatig invoeren.  Zie [apparaten labelen met hardware-ID-nummers](../../mdm/deploy-use/predeclare-devices-with-hardware-id.md).
