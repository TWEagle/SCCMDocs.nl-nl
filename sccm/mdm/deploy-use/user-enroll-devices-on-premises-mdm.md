---
title: Hoe gebruikers apparaten inschrijven met On-premises MDM - Configuration Manager | Microsoft-documenten
description: Begrijpen hoe gebruikers apparaten inschrijven met On-premises mobiele apparaten beheren in System Center Configuration Manager.
ms.custom: na
ms.date: 03/05/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-hybrid
ms.tgt_pltfrm: na
ms.topic: get-started-article
ms.assetid: 59004b34-b64f-4d77-898c-07bf3dc75430
caps.latest.revision: 9
caps.handback.revision: 0
author: Mtillman
ms.author: mtillman
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 507bad02c6e028f09a8b0c8a566ac55f7c3942a5
ms.openlocfilehash: 8c7438c2cc0bc66654eb3e74de10553df53181d9
ms.contentlocale: nl-nl
ms.lasthandoff: 05/17/2017


---
# <a name="how-users-enroll-devices-with-on-premises-mobile-device-management-in-system-center-configuration-manager"></a>Hoe gebruikers apparaten inschrijven met On-premises mobiele apparaten beheren in System Center Configuration Manager

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*

Met beheer van System Center Configuration Manager On-premises mobiele apparaten, kunnen gebruikers apparaten inschrijven als ze gemachtigd inschrijving (in de instellingen van de bijgewerkte client) en hun apparaten de vereiste basiscertificaat geïnstalleerd voor de communicatie met de servers die als host fungeert voor de vereiste sitesysteemrollen hebben vertrouwd. Zie voor meer informatie over het instellen van inschrijving [apparaatinschrijving voor On-premises mobiele apparaten beheren in System Center Configuration Manager instellen](../../mdm/get-started/set-up-device-enrollment-on-premises-mdm.md).  

> [!NOTE]  
>  De huidige vertakking van Configuration Manager ondersteunt de inschrijving in beheer van mobiele apparaten On-premises voor apparaten met de volgende besturingssystemen:  
>   
> -  Windows 10 Enterprise  
> -   Windows 10 Pro  
> -   Windows 10 Team \(vanaf in Configuration Manager versie 1602\)  
> -   Windows 10 Mobile  
> -   Windows 10 Mobile Enterprise
> -   Windows 10 IoT Enterprise   

De volgende taken wordt uitgelegd hoe inschrijven en verifiëren van computers en apparaten voor inschrijving op\-premises beheer van mobiele apparaten:  

-   [Een Windows 10-computer inschrijven](#bkmk_enrollDesk)  

-   [Een Windows 10 Mobile-apparaat inschrijven](#bkmk_enrollMob)  

-   [Inschrijving van apparaten controleren](#bkmk_verify)  

##  <a name="bkmk_enrollDesk"></a> Een Windows 10-computer inschrijven  

1.  Ga op een computer met Windows 10 naar **Instellingen**.  

2.  Klik op **Accounts**en klik vervolgens op **Toegang via het werknetwerk**.  

3.  Klik in Toegang via het werknetwerk bij **Verbinding maken met werk of school**op **Verbinden**, voer uw zakelijke e-mailadres in en klik op **Doorgaan**.  

4.  Voer de FQDN-naam van de server die als host fungeert voor de inschrijving proxy-puntsitesysteemrol en klikt u op **doorgaan**.  

5.  Voer het wachtwoord voor uw zakelijke e-mail in om verbinding met een service te maken en klik op **Aanmelden**.  

6.  Klik op **Overslaan** voor het herinneren van de aanmeldingsgegevens en wacht een ogenblik totdat het apparaat is verbonden.  

##  <a name="bkmk_enrollMob"></a> Een Windows 10 Mobile-apparaat inschrijven  

1.  Ga op een apparaat met Windows 10 Mobile naar **Instellingen**.  

2.  Klik op **Accounts**en klik vervolgens op **Toegang via het werknetwerk**.  

3.  Klik op **Verbinden**.  

4.  Voer uw zakelijke e-mailadres in en de FQDN van de server die het proxypunt voor inschrijving van de sitesysteemrol host. Klik op **Verbinden**.  

5.  Voer op het volgende scherm uw zakelijke e-mailadres en het wachtwoord in en klik vervolgens op **Aanmelden**. Na een korte periode is het apparaat ingeschreven. Klik op **Gereed**.  

##  <a name="bkmk_verify"></a> Inschrijving van apparaten controleren  
 U kunt controleren of die apparaten met succes hebben ingeschreven in de Configuration Manager-console.  

1.  Start de Configuration Manager-console.  

2.  Klik op **Activa en naleving** > **Overzicht** > **Apparaten**. Het geregistreerde apparaat wordt weergegeven in de lijst.  

