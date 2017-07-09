---
title: Beheer van hybride Android-apparaten met System Center Configuration Manager en Microsoft Intune instellen | Microsoft Docs
description: Voorbereiden voor het beheren van mobiele Android-apparaten met Configuration Manager en Intune.
ms.custom: na
ms.date: 03/27/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-hybrid
ms.tgt_pltfrm: na
ms.topic: get-started-article
ms.assetid: c517fe34-0130-465b-a020-bdb555878778
caps.latest.revision: 9
caps.handback.revision: 0
author: nathbarn
ms.author: nathbarn
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 86620254897aa9a775dc433de7010b5814c1ec3e
ms.openlocfilehash: af6fa2dfae5549e89c46d05d0cef1e24342558f9
ms.contentlocale: nl-nl
ms.lasthandoff: 07/06/2017


---
# <a name="set-up-android-hybrid-device-management-with-system-center-configuration-manager-and-microsoft-intune"></a>Hybride apparaatbeheer instellen voor Android met System Center Configuration Manager en Microsoft Intune

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*

Dit onderwerp helpt de IT-beheerder hybride registratie van Android- en Android voor werk apparaten inschakelen. De IT-beheerder kunt vervolgens System Center Configuration Manager gebruiken om de apparaten via een geconfigureerde Microsoft Intune-abonnement te beheren. Gebruikers kunnen de Android-bedrijfsportal-app waarmee ze Android (inclusief Samsung KNOX Standard)- en Android voor werk apparaten registreren downloaden van Google Play.

Als Configuration Manager-beheerder kunt u instellingen voor naleving beheren, wissen of verwijderen van Android-apparaten, apps implementeren en software en hardware-inventaris verzamelen. Zonder de Android-bedrijfsportal-app op het apparaat is geïnstalleerd, u hebt geen beheermogelijkheden, zoals inventaris en compatibiliteitsinstellingen maar kunt u nog steeds apps naar Android-apparaten implementeren.  

## <a name="enable-android-enrollment"></a>Android-registratie inschakelen  
De volgende stappen kunt Configuration Manager beheren van Android-apparaten zonder een work-profiel (dat wil zeggen, 'klassieke Android' inschrijving).

1. Voordat u inschrijven voor elk platform instellen kunt, hebt u de vereisten en procedures in [Setup hybride MDM](setup-hybrid-mdm.md).  
2. In de Configuration Manager-console in de **beheer** werkruimte, kiest u **overzicht** > **Cloudservices** > **Microsoft Intune-abonnement** en kies uw Intune-abonnement.  
3. Op de **Start** tabblad de **abonnement** groep, kiest u **Platforms configureren** > **Android**.  
4. In de **eigenschappen van Microsoft Intune-abonnement** dialoogvenster Kies de **Android** tabblad en controleer de **Android-inschrijving inschakelen** vak.  

 Nadat u alles hebt ingesteld, moet u uw gebruikers laten weten hoe ze kunnen hun apparaten inschrijven. Zie [Wat u uw eindgebruikers vertelt over het gebruik van Microsoft Intune](https://docs.microsoft.com/intune/deploy-use/what-to-tell-your-end-users-about-using-microsoft-intune). Deze informatie is van toepassing op mobiele apparaten die worden beheerd door Configuration Manager en Microsoft Intune.

## <a name="enable-android-for-work-enrollment"></a>Android voor zakelijke inschrijving inschakelen
De volgende stappen kunt Configuration Manager beheren van Android-apparaten met een werk-profiel.

1. Maakt een Google-account op https://accounts.google.com/SignUp als uw Android wilt gebruiken voor werk-beheeraccount. Of meld u aan met het account dat is gekoppeld aan alle Android voor werk beheertaken voor Intune-tenant. Dit account heeft mogelijk een Google-account die wordt gedeeld door de beheerders die Android-apparaten beheren. Dit is het Google-account die uw organisatie te beheren en publiceren van apps in de Play voor Work-console gebruikt. Met dit account kunt u het goedkeuren van apps in de Play voor werk store, dus bijhouden van de accountnaam en wachtwoord.
2. Android-registratie inschakelen door de binding van het Google-account voor de Intune-tenant die wordt beheerd in Configuration Manager:
   1. In de Configuration Manager-console in de **beheer** werkruimte, kiest u **overzicht** > **Cloudservices** > **Microsoft Intune-abonnementen** en kies uw Intune-abonnement.
   2. Op de **Start** tabblad de **abonnement** groep, kiest u **Platforms configureren** > **Android for Work**.
   3. Kies in het dialoogvenster **Android configureren voor werk in de Intune-console**. De Intune-console wordt geopend in uw webbrowser.
   4. Gebruik uw Intune-beheerdersreferenties aan te melden bij de Intune-portal.
   5. Kies **configureren** Android van Google Play voor werk website openen.
   6. Geef de referenties van de Google-account uit stap 1 op Google aanmeldingspagina, en geef vervolgens de gegevens van uw bedrijf.
3. Wanneer u naar de Intune-portal terugkeert, Android for Work is ingeschakeld en hebt u drie Inschrijvingsopties voor Android voor werk apparaten:
   - **Alle apparaten beheren als Android** (uitgeschakeld). Alle Android-apparaten, inclusief apparaten die ondersteuning bieden voor Android voor werk, worden geregistreerd als conventionele Android-apparaten.
   - **Ondersteunde apparaten beheren als Android for Work** (ingeschakeld). Alle apparaten die ondersteuning bieden voor Android for Work worden geregistreerd als Android voor Work-apparaten. Een Android-apparaat dat biedt geen ondersteuning voor Android for Work is als een conventionele Android-apparaat ingeschreven.
   - **Ondersteunde apparaten voor gebruikers die alleen in deze groepen beheren als Android for Work** (ingeschakeld voor een aantal groepen alleen). Hiermee kunt u Android doel voor werkstroombeheer voor een beperkt aantal gebruikers. Apparaten die ondersteuning bieden voor Android for Work worden geregistreerd als Android voor de apparaten werken alleen als leden van de geselecteerde groepen ze registreren. Alle andere apparaten worden geregistreerd als Android-apparaten.

> [!NOTE]
> Een bekend probleem dat voorkomt dat de **beheren ondersteunde apparaten voor gebruikers die alleen in deze groepen als Android for Work** optie niet werkt zoals verwacht. Apparaten van gebruikers in de opgegeven Azure AD-groepen registreren als Android in plaats van Android for Work. Als u wilt Android for Work inschakelen, moet u de **alle ondersteunde apparaten beheren als Android for Work** optie.


Nadat u alles hebt ingesteld, moet u uw gebruikers laten weten hoe ze kunnen hun apparaten inschrijven. Zie [Wat u uw eindgebruikers vertelt over het gebruik van Microsoft Intune](https://docs.microsoft.com/intune/deploy-use/what-to-tell-your-end-users-about-using-microsoft-intune). Deze informatie is van toepassing op mobiele apparaten die worden beheerd door Configuration Manager en Microsoft Intune.

Als de binding is voltooid, ziet u de accountnaam en de naam van de organisatie in de Intune-portal. U kunt beide browsers sluiten op dat moment.

### <a name="enroll-an-android-for-work-device"></a>Een Android voor Work-apparaat inschrijven
Hoe uw gebruikers Android inschrijven voor zakelijke apparaten is vergelijkbaar met inschrijving voor Android. Gebruikers kunnen downloaden en installeren van de bedrijfsportal-app voor Android op hun mobiele apparaten. De app vraagt hen een werk-profiel maken als onderdeel van het registratieproces. Nadat de work-profiel is gemaakt, worden gebruikers moeten overschakelen naar de beheerde versie van de bedrijfsportal. De beheerde bedrijfsportal is gemarkeerd met een klein oranje werkmap in de rechterbenedenhoek.

### <a name="manage-android-for-work-devices"></a>Android voor werk apparaten beheren
Nadat u Android voor inschrijving voor werk inschakelt, kunt u de volgende beheertaken uitvoeren voor Android voor werk apparaten:
- [Goedkeuren van apps](/sccm/mdm/deploy-use/creating-android-applications#approve-and-deploy-android-for-work-apps)
- [Configuratie-items maken](/sccm/mdm/deploy-use/create-configuration-items-for-android-for-work-devices-managed-without-the-client)
- [Compatibiliteitsinstellingen beheren](/sccm/mdm/deploy-use/create-configuration-items-for-android-for-work-devices-managed-without-the-client)
- [E-mailprofielen beheren](/sccm/mdm/deploy-use/create-exchange-activesync-profiles)
- [Selectief wissen work-profiel](/sccm/mdm/deploy-use/wipe-lock-reset-devices#selective-wipe)

> [!div class="button"]
[< Vorige stap](create-service-connection-point.md)[volgende stap >  ](set-up-additional-management.md)

