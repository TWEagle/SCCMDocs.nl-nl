---
title: Maken van een service connection point met behulp van System Center Configuration Manager | Microsoft-documenten
description: Maak een serviceverbindingspunt met behulp van System Center Configuration Manager.
ms.custom: na
ms.date: 03/05/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-hybrid
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 617abb22-d22f-41fb-a76b-1c4259e419d2
caps.latest.revision: 18
caps.handback.revision: 0
author: mtillman
ms.author: mtillman
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 2c723fe7137a95df271c3612c88805efd8fb9a77
ms.openlocfilehash: 9a21d02cb2a50162e5de50481f0f27f2dd7a616c
ms.contentlocale: nl-nl
ms.lasthandoff: 05/17/2017

---
# <a name="create-a-service-connection-point-with-system-center-configuration-manager-and-microsoft-intune"></a>Een serviceverbindingspunt maken met System Center Configuration Manager en Microsoft Intune

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*

Wanneer u uw abonnement hebt gemaakt, kunt u de sitesysteemrol serviceaansluitpunt installeren waarmee u verbinding kunt maken met de Intune-service. Deze sitesysteemrol zendt de instellingen en toepassingen naar de Intune-service.

 De service connection point verzendt instellingen en software-implementatiegegevens naar Configuration Manager en krijgt status- en inventarisberichten van mobiele apparaten. De Configuration Manager-service fungeert als een gateway die communiceert met mobiele apparaten en instellingen opslaat.

> [!NOTE]
>  De sitesysteemrol serviceaansluitpunt kan alleen op een centrale beheersite of op een zelfstandige, primaire site worden geïnstalleerd. Het serviceaansluitpunt moet toegang hebben tot internet.


## <a name="configure-the-service-connection-point-role"></a>De rol van het service-verbinding configureren

1.  Klik op **Beheer**in de Configuration Manager-console.

2.  In de **beheer** werkruimte Vouw **Sites**, en klik vervolgens op **Servers en sitesysteemrollen**.

3.  Voeg met de bijbehorende stap de rol **Serviceaansluitpunt** toe aan een nieuwe of bestaande sitesysteemserver:

    -   Nieuwe sitesysteemserver: Op de **Start** tabblad, in de **maken** groep, klikt u op **Sitesysteemserver maken** om de Wizard Site System Server te starten.

    -   Bestaande sitesysteemserver: Klik op de server waarop u wilt installeren van de rol voor de service. Klik vervolgens op het tabblad **Start** in de groep **Server** op **Sitesysteemrollen toevoegen** om de wizard Sitesysteemrollen toevoegen te starten.

4.  Selecteer op de pagina **Systeemrolselectie** de optie **Serviceaansluitpunt** en klik op **Volgende**.
![Een serviceverbindingspunt maken](../media/mdm-service-connection-point.png)

* Voltooi de wizard.

## <a name="how-does-the-service-connection-point-authenticate-with-the-microsoft-intune-service"></a>Hoe verifieert het serviceaansluitpunt de verbinding met de service Microsoft Intune?
 De service connection point breidt de mogelijkheden van Configuration Manager door een verbinding met de cloud-gebaseerde Intune service waarmee mobiele apparaten via Internet worden beheerd. De service connection point verificatie met de Intune-service als volgt:

1.  Wanneer u een Intune-abonnement in de Configuration Manager-console maakt, wordt de beheerder van Configuration Manager geverifieerd door verbinding te maken met Azure Active Directory, dat wordt omgeleid naar de respectieve ADFS-server om de gebruikersnaam en wachtwoord te vragen. Intune geeft vervolgens een certificaat aan de tenant.

2.  Het certificaat uit stap 1 wordt geïnstalleerd op de siterol van het serviceaansluitpunt en wordt gebruikt om alle verdere communicatie met de Microsoft Intune-service te verifiëren en goed te keuren.

> [!div class="button"]
[< Vorige stap](terms-and-conditions.md)[volgende stap >  ](enable-platform-enrollment.md)

