---
title: Hoe gebruikers apparaten inschrijven met On-premises MDM - Configuration Manager | Microsoft Docs
description: Begrijpen hoe gebruikers apparaten inschrijven met On-premises Mobile Device Management in System Center Configuration Manager.
ms.custom: na
ms.date: 03/05/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: configmgr-hybrid
ms.tgt_pltfrm: na
ms.topic: get-started-article
ms.assetid: 59004b34-b64f-4d77-898c-07bf3dc75430
caps.latest.revision: "9"
caps.handback.revision: "0"
author: Mtillman
ms.author: mtillman
manager: angrobe
ms.openlocfilehash: 8c7438c2cc0bc66654eb3e74de10553df53181d9
ms.sourcegitcommit: 51fc48fb023f1e8d995c6c4eacfda7dbec4d0b2f
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 08/07/2017
---
# <a name="how-users-enroll-devices-with-on-premises-mobile-device-management-in-system-center-configuration-manager"></a>Hoe gebruikers apparaten inschrijven met On-premises Mobile Device Management in System Center Configuration Manager

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*

Met System Center Configuration Manager On-premises Mobile Device Management, kunnen gebruikers apparaten inschrijven als ze hebben gekregen over inschrijvingsmachtigingen beschikken (door middel van bijgewerkte clientinstellingen) en hun apparaten het vereiste basiscertificaat dat is geïnstalleerd is voor een vertrouwde communicatie met de servers die als host fungeert voor de vereiste sitesysteemrollen. Zie voor meer informatie over het instellen van inschrijving [registratie van apparaten instellen voor On-premises Mobile Device Management in System Center Configuration Manager](../../mdm/get-started/set-up-device-enrollment-on-premises-mdm.md).  

> [!NOTE]  
>  De huidige vertakking van Configuration Manager ondersteunt de inschrijving in On-premises Mobile Device Management voor apparaten met de volgende besturingssystemen:  
>   
> -  Windows 10 Enterprise  
> -   Windows 10 Pro  
> -   Windows 10 Team \(vanaf versie 1602 van Configuration Manager\)  
> -   Windows 10 Mobile  
> -   Windows 10 Mobile Enterprise
> -   Windows 10 IoT Enterprise   

De volgende taken wordt uitgelegd hoe u om te schrijven en de inschrijving van computers en apparaten voor controleren op\-premises Mobile Device Management:  

-   [Een Windows 10-computer inschrijven](#bkmk_enrollDesk)  

-   [Een Windows 10 Mobile-apparaat inschrijven](#bkmk_enrollMob)  

-   [Inschrijving van apparaten controleren](#bkmk_verify)  

##  <a name="bkmk_enrollDesk"></a> Een Windows 10-computer inschrijven  

1.  Ga op een computer met Windows 10 naar **Instellingen**.  

2.  Klik op **Accounts**en klik vervolgens op **Toegang via het werknetwerk**.  

3.  Klik in Toegang via het werknetwerk bij **Verbinding maken met werk of school**op **Verbinden**, voer uw zakelijke e-mailadres in en klik op **Doorgaan**.  

4.  Voer de FQDN van de server die als host fungeert voor de inschrijving proxy sitesysteemrol en klikt u op **doorgaan**.  

5.  Voer het wachtwoord voor uw zakelijke e-mail in om verbinding met een service te maken en klik op **Aanmelden**.  

6.  Klik op **Overslaan** voor het herinneren van de aanmeldingsgegevens en wacht een ogenblik totdat het apparaat is verbonden.  

##  <a name="bkmk_enrollMob"></a> Een Windows 10 Mobile-apparaat inschrijven  

1.  Ga op een apparaat met Windows 10 Mobile naar **Instellingen**.  

2.  Klik op **Accounts**en klik vervolgens op **Toegang via het werknetwerk**.  

3.  Klik op **Verbinden**.  

4.  Voer uw zakelijke e-mailadres in en de FQDN van de server die het proxypunt voor inschrijving van de sitesysteemrol host. Klik op **Verbinden**.  

5.  Voer op het volgende scherm uw zakelijke e-mailadres en het wachtwoord in en klik vervolgens op **Aanmelden**. Na een korte periode is het apparaat ingeschreven. Klik op **Gereed**.  

##  <a name="bkmk_verify"></a> Inschrijving van apparaten controleren  
 U kunt controleren dat apparaten zijn geregistreerd in de Configuration Manager-console.  

1.  Start de Configuration Manager-console.  

2.  Klik op **Activa en naleving** > **Overzicht** > **Apparaten**. Het geregistreerde apparaat wordt weergegeven in de lijst.  
