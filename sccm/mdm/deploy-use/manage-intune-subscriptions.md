---
title: Een Intune-abonnement beheren
titleSuffix: Configuration Manager
description: Een Intune-abonnement dat is gekoppeld met System Center Configuration Manager beheren.
ms.custom: na
ms.date: 06/02/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: configmgr-hybrid
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 9b494767-68c1-47b1-9a86-591bff0ad491
caps.latest.revision: "18"
caps.handback.revision: "0"
author: dougeby
ms.author: dougeby
manager: angrobe
ms.openlocfilehash: a6bb27adeddc366526df699b69e95c6e7d6482ae
ms.sourcegitcommit: c236214b2fcc13dae7bad96d7fb33f692868191d
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/12/2017
---
# <a name="manage-an-intune-subscription-associated-with-system-center-configuration-manager"></a>Een Intune-abonnement dat is gekoppeld met System Center Configuration Manager beheren

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*

Als u Microsoft Intune (een proefabonnement of een betaald abonnement) aan Configuration Manager toevoegt en moet overschakelen naar een ander Intune-abonnement, moet u zowel de **Microsoft Intune-abonnement** en de **Serviceaansluitpunt** vanuit de Configuration Manager-console voordat u een nieuw abonnement kunt toevoegen.

> [!NOTE]
> U kunt slechts één Intune-abonnement configureren op een tijd in hybride mobile device management.

## <a name="how-to-delete-an-intune-subscription-from-configuration-manager"></a>Een Intune-abonnement verwijderen uit Configuration Manager

> [!IMPORTANT]
>  Alle inhoud, met inbegrip van de gebruikersinschrijvingen, beleid en app-implementaties die zijn geconfigureerd voor apparaten die worden beheerd door de Intune-abonnement worden verwijderd wanneer u het abonnement verwijderd.

1.  Ga in de Configuration Manager-console naar **beheer** > **overzicht** > **Cloudservices** > **Microsoft Intune-abonnementen**.

2.  Met de rechtermuisknop op de vermelde **Microsoft Intune-abonnement**, en klik vervolgens op **verwijderen**.

3.   Klik in de wizard op **Microsoft Intune-abonnement van Configuration Manager verwijderen**, klikt u op **volgende**, en klik vervolgens op **volgende** opnieuw aan het abonnement niet verwijderen.


## <a name="how-to-remove-the-service-connection-point-role"></a>Het verwijderen van de rol serviceaansluitpunt

1.  Ga naar **beheer** > **overzicht** > **Site-configuratie** > **Servers en sitesysteemrollen**.

2.  Selecteer de server waarop de rol **Serviceaansluitpunt** wordt gehost.

3.  In de lijst **sitesysteemrollen** selecteert u **Serviceaansluitpunt**. Klik vervolgens op **Rol verwijderen** in het lint. Bevestig dat u de rol wilt verwijderen. Het serviceaansluitpunt wordt verwijderd.

U kunt nu een nieuw serviceaansluitpunt maken, een nieuw Intune-abonnement toevoegen aan Configuration Manager en Configuration Manager instellen als MDM-instantie.

## <a name="how-to-change-mdm-authority-to-intune"></a>Het wijzigen van de MDM-instantie aan Intune
Vanaf versie 1610 van Configuration Manager en Microsoft Intune version 1705, kunt u uw MDM-instantie zonder contact opnemen met Microsoft Support en zonder de registratie ongedaan maken en registreren van uw bestaande beheerde apparaten. Zie voor meer informatie [wijzigen van uw MDM-instantie](/sccm/mdm/deploy-use/change-mdm-authority).
