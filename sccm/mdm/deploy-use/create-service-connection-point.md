---
title: Een serviceverbindingspunt met System Center Configuration Manager maken | Microsoft Docs
description: Maak een serviceverbindingspunt met System Center Configuration Manager.
ms.custom: na
ms.date: 03/05/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: configmgr-hybrid
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 617abb22-d22f-41fb-a76b-1c4259e419d2
caps.latest.revision: "18"
caps.handback.revision: "0"
author: mtillman
ms.author: mtillman
manager: angrobe
ms.openlocfilehash: 9a21d02cb2a50162e5de50481f0f27f2dd7a616c
ms.sourcegitcommit: 51fc48fb023f1e8d995c6c4eacfda7dbec4d0b2f
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 08/07/2017
---
# <a name="create-a-service-connection-point-with-system-center-configuration-manager-and-microsoft-intune"></a>Een serviceverbindingspunt maken met System Center Configuration Manager en Microsoft Intune

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*

Wanneer u uw abonnement hebt gemaakt, kunt u de sitesysteemrol serviceaansluitpunt installeren waarmee u verbinding kunt maken met de Intune-service. Deze sitesysteemrol zendt de instellingen en toepassingen naar de Intune-service.

 Het serviceaansluitpunt verzendt instellingen en software-implementatiegegevens naar Configuration Manager en krijgt status- en inventarisberichten van mobiele apparaten. De Configuration Manager-service fungeert als een gateway die communiceert met mobiele apparaten en instellingen opslaat.

> [!NOTE]
>  De sitesysteemrol serviceaansluitpunt kan alleen op een centrale beheersite of op een zelfstandige, primaire site worden geïnstalleerd. Het serviceaansluitpunt moet toegang hebben tot internet.


## <a name="configure-the-service-connection-point-role"></a>De rol serviceaansluitpunt configureren

1.  Klik op **Beheer**in de Configuration Manager-console.

2.  In de **beheer** werkruimte Vouw **Sites**, en klik vervolgens op **Servers en sitesysteemrollen**.

3.  Voeg met de bijbehorende stap de rol **Serviceaansluitpunt** toe aan een nieuwe of bestaande sitesysteemserver:

    -   Nieuwe sitesysteemserver: Op de **Start** tabblad, in de **maken** groep, klikt u op **Sitesysteemserver maken** starten van de Site Wizard maken.

    -   Bestaande sitesysteemserver: Klik op de server waarop u wilt de rol serviceaansluitpunt installeren. Klik vervolgens op het tabblad **Start** in de groep **Server** op **Sitesysteemrollen toevoegen** om de wizard Sitesysteemrollen toevoegen te starten.

4.  Selecteer op de pagina **Systeemrolselectie** de optie **Serviceaansluitpunt** en klik op **Volgende**.
![Een serviceverbindingspunt maken](../media/mdm-service-connection-point.png)

* Voltooi de wizard.

## <a name="how-does-the-service-connection-point-authenticate-with-the-microsoft-intune-service"></a>Hoe verifieert het serviceaansluitpunt de verbinding met de service Microsoft Intune?
 Het service connection point breidt de mogelijkheden van Configuration Manager door het maken van een verbinding met de op cloud-gebaseerde Intune-service waarmee mobiele apparaten via Internet worden beheerd. Het serviceaansluitpunt wordt als volgt geverifieerd met de Intune-service:

1.  Wanneer u een Intune-abonnement in de Configuration Manager-console maakt, wordt de Configuration Manager-beheerder geverifieerd door verbinding te maken met Azure Active Directory, dat wordt omgeleid naar de respectieve ADFS-server om de gebruikersnaam en wachtwoord wordt gevraagd. Intune verstrekt vervolgens een certificaat aan de tenant.

2.  Het certificaat uit stap 1 wordt geïnstalleerd op de siterol van het serviceaansluitpunt en wordt gebruikt om alle verdere communicatie met de Microsoft Intune-service te verifiëren en goed te keuren.

> [!div class="button"]
[< Vorige stap](terms-and-conditions.md)[volgende stap >  ](enable-platform-enrollment.md)
