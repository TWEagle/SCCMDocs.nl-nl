---
title: Extra beheer met behulp van System Center Configuration Manager instellen | Microsoft-documenten
description: Extra beheer met behulp van System Center Configuration Manager instellen.
ms.custom: na
ms.date: 03/05/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-hybrid
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 4877d674-6bbc-4e16-810c-daad70c74daa
caps.latest.revision: 18
caps.handback.revision: 0
author: mtillman
ms.author: mtillman
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 2c723fe7137a95df271c3612c88805efd8fb9a77
ms.openlocfilehash: 947d2a85f2ac68c7ccaf9a1237fd60e89e7d1d10
ms.contentlocale: nl-nl
ms.lasthandoff: 05/17/2017

---
# <a name="set-up-additional-management-with-system-center-configuration-manager"></a>Aanvullende management met System Center Configuration Manager instellen

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*

(Optioneel) U kunt extra beheerservers instellen voordat apparaten zijn ingeschreven. Deze beheeroplossingen kunnen worden gemaakt en geïmplementeerd nadat apparaten zijn geregistreerd, hoewel veel organisaties wil deze apparaten zijn onder beheer gebracht implementeren.

**Configuratie-items** kunt u instellingen zoals het vereisen van een PINCODE of het vereisen van versleuteling op ingeschreven apparaten op basis van apparaatplatform beheren:
- [Windows 10 en Windows 8.1-apparaten](create-configuration-items-for-windows-8.1-and-windows-10-devices-managed-without-the-client.md)
- [Windows Phone-apparaten](create-configuration-items-for-windows-phone-devices-managed-without-the-client.md)
- [iOS- en Mac-apparaten](create-configuration-items-for-ios-and-mac-os-x-devices-managed-without-the-client.md)
- [Android en Samsung KNOX Standard-apparaten](create-configuration-items-for-android-and-samsung-knox-devices-managed-without-the-client.md)

**Toepassingen** kan worden toegepast op beheerde apparaten:
- [iOS-toepassingen](creating-ios-applications.md)
- [Mac-toepassingen](../../apps/get-started/creating-mac-computer-applications.md)
- [Windows-PC-toepassingen](../../apps/get-started/creating-windows-applications.md)
- [Windows Phone-toepassingen](creating-windows-phone-applications.md)
- [Android-toepassingen](creating-android-applications.md)

**Voorwaardelijke toegang** kunt u toegang tot bedrijfsresources, zoals beheren:  
- [Toegang tot e-mail](manage-email-access.md)
- [Toegang tot SharePoint](manage-sharepoint-online-access.md)
- [Skype voor bedrijven toegang](manage-skype-for-business-online-access.md)
- [Dynamische CRM Online](manage-dynamics-crm-online-access.md)

**Multi-factor Authentication (MFA)** kunt u meer dan één verificatiemethode waarmee een cruciale tweede beveiligingslaag beveiliging worden toegevoegd aan gebruiker aanmeldingen en transacties vereisen.
U zou eerder, gaat u naar de Intune-console of de Configuration Manager-console in te stellen van MFA voor inschrijvingen met Intune. Nu u aanmelden bij de [Microsoft Azure-portal](https://manage.windowsazure.com) met behulp van uw Intune-referenties en MFA-instellingen via de Azure AD configureren. Zie voor meer informatie, [multi-factor authentication voor Microsoft Intune](https://aka.ms/mfa_ad).

> [!div class="button"]
[< Vorige stap](enable-platform-enrollment.md)[volgende stap >  ](verify-mdm-configuration.md)

