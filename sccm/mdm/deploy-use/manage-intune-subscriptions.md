---
title: Een Intune-abonnement dat is gekoppeld met System Center Configuration Manager beheren | Microsoft-documenten
description: Een Intune-abonnement dat is gekoppeld met System Center Configuration Manager beheren.
ms.custom: na
ms.date: 03/05/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-hybrid
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 9b494767-68c1-47b1-9a86-591bff0ad491
caps.latest.revision: 18
caps.handback.revision: 0
author: mtillman
ms.author: mtillman
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 2c723fe7137a95df271c3612c88805efd8fb9a77
ms.openlocfilehash: 2e0b3cd1070d0f8adb1219acd33c3126d2758a49
ms.contentlocale: nl-nl
ms.lasthandoff: 05/17/2017

---
# <a name="manage-an-intune-subscription-associated-with-system-center-configuration-manager"></a>Een Intune-abonnement dat is gekoppeld met System Center Configuration Manager beheren

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*

Als u een Microsoft Intune (een proefabonnement of een betaald abonnement) aan Configuration Manager toevoegen en moet overschakelen naar een ander Intune-abonnement, moet u zowel de **Microsoft Intune-abonnement** en de **serviceverbindingspunt** vanuit de Configuration Manager-console voordat u een nieuw abonnement kunt toevoegen.

> [!NOTE]
> U kunt slechts één Intune-abonnement configureren op een tijdstip in beheer van hybride mobiele apparaten.

## <a name="how-to-delete-an-intune-subscription-from-configuration-manager"></a>Een Intune-abonnement verwijderen uit Configuration Manager

> [!IMPORTANT]
>  Alle inhoud, met inbegrip van de gebruiker inschrijvingen, beleid en app-implementaties die zijn geconfigureerd voor apparaten die worden beheerd door de Intune-abonnement worden verwijderd wanneer u het abonnement verwijderen.

1.  Ga in de Configuration Manager-console naar **beheer** > **overzicht** > **Cloudservices** > **Microsoft Intune-abonnementen**.

2.  Met de rechtermuisknop op de vermelde **Microsoft Intune-abonnement**, en klik vervolgens op **verwijderen**.

3.   Klik in de wizard op **Microsoft Intune-abonnement van Configuration Manager verwijderen**, klikt u op **volgende**, en klik vervolgens op **volgende** nogmaals in het abonnement niet verwijderen.


## <a name="how-to-remove-the-service-connection-point-role"></a>Het verwijderen van de verbindingsrol

1.  Ga naar **beheer** > **overzicht** > **Site-configuratie** > **Servers en sitesysteemrollen**.

2.  Selecteer de server waarop de rol **Serviceaansluitpunt** wordt gehost.

3.  In de lijst **sitesysteemrollen** selecteert u **Serviceaansluitpunt**. Klik vervolgens op **Rol verwijderen** in het lint. Bevestig dat u de rol wilt verwijderen. Het serviceaansluitpunt wordt verwijderd.

U kunt nu een nieuw serviceaansluitpunt maken, een nieuw Intune-abonnement toevoegen aan Configuration Manager en Configuration Manager instellen als MDM-instantie.

## <a name="how-to-change-mdm-authority-to-intune"></a>Het wijzigen van MDM-instantie bij Intune

Vanaf versie 1610, kunt u als u wilt overschakelen van de MDM-instantie van de Configuration Manager met Intune. Informatie over deze functie is binnenkort beschikbaar.

