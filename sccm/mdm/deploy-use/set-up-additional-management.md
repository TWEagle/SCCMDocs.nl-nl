---
title: Extra beheer instellen
titleSuffix: Configuration Manager
description: Extra beheer met behulp van System Center Configuration Manager instellen.
ms.custom: na
ms.date: 03/05/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: configmgr-hybrid
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 4877d674-6bbc-4e16-810c-daad70c74daa
caps.latest.revision: "18"
caps.handback.revision: "0"
author: dougeby
ms.author: dougeby
manager: angrobe
ms.openlocfilehash: e3aaefb1d240449467dc9744a3e959e21d3351d3
ms.sourcegitcommit: c236214b2fcc13dae7bad96d7fb33f692868191d
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/12/2017
---
# <a name="set-up-additional-management-with-system-center-configuration-manager"></a>Extra beheer met System Center Configuration Manager instellen

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*

(Optioneel) U kunt aanvullende management instellen voordat apparaten worden ingeschreven. Deze beheersystemen worden gemaakt en geïmplementeerd nadat apparaten zijn geregistreerd, hoewel veel organisaties implementeren wilt, zoals apparaten onder beheer zijn gebracht.

**Configuratie-items** kunt u instellingen, zoals een PINCODE of het vereisen van versleuteling op ingeschreven apparaten op basis van apparaatplatform beheren:
- [Windows 10 en Windows 8.1-apparaten](create-configuration-items-for-windows-8.1-and-windows-10-devices-managed-without-the-client.md)
- [Windows Phone-apparaten](create-configuration-items-for-windows-phone-devices-managed-without-the-client.md)
- [iOS en Mac-apparaten](create-configuration-items-for-ios-and-mac-os-x-devices-managed-without-the-client.md)
- [Android en Samsung KNOX Standard-apparaten](create-configuration-items-for-android-and-samsung-knox-devices-managed-without-the-client.md)

**Toepassingen** kan worden geïmplementeerd op beheerde apparaten:
- [iOS-toepassingen](creating-ios-applications.md)
- [Mac-toepassingen](../../apps/get-started/creating-mac-computer-applications.md)
- [Windows-PC-toepassingen](../../apps/get-started/creating-windows-applications.md)
- [Windows Phone-toepassingen](creating-windows-phone-applications.md)
- [Android-toepassingen](creating-android-applications.md)

**Voorwaardelijke toegang** kunt u toegang tot bedrijfsresources zoals beheren:  
- [Toegang tot e-mail](manage-email-access.md)
- [Toegang tot SharePoint](manage-sharepoint-online-access.md)
- [Skype voor bedrijven-toegang](manage-skype-for-business-online-access.md)
- [Dynamische CRM Online](manage-dynamics-crm-online-access.md)

**Multi-factor Authentication (MFA)** kunt u vereisen meer dan één verificatiemethode, die een kritieke tweede beveiligingslaag wordt toegevoegd aan de gebruikersaanmeldingen en transacties.
Eerder, gaat u naar de Intune-console of de Configuration Manager-console in te stellen van MFA voor Intune inschrijvingen. Nu u aanmelden bij de [Microsoft Azure-portal](https://manage.windowsazure.com) met behulp van uw Intune-referenties en het configureren van MFA-instellingen via Azure AD. Zie voor meer informatie, [multi-factor authentication voor Microsoft Intune](https://aka.ms/mfa_ad).

> [!div class="button"]
[< Vorige stap](enable-platform-enrollment.md)[volgende stap >  ](verify-mdm-configuration.md)
