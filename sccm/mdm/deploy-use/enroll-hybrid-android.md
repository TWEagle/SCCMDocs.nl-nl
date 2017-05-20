---
title: Android hybride device management met System Center Configuration Manager en Microsoft Intune instellen | Microsoft-documenten
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
ms.sourcegitcommit: 27a92dc1c3710ff55f0b145386319dda371533d9
ms.openlocfilehash: 0e93cd55ce49afb6395dcbe758c933bf509dd367
ms.contentlocale: nl-nl
ms.lasthandoff: 05/17/2017


---
# <a name="set-up-android-hybrid-device-management-with-system-center-configuration-manager-and-microsoft-intune"></a>Hybride apparaatbeheer instellen voor Android met System Center Configuration Manager en Microsoft Intune

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*

In dit onderwerp vindt de IT-beheerder hybride inschrijving van Android- en Android voor werk apparaten inschakelen. De IT-beheerder kan vervolgens System Center Configuration Manager worden gebruikt voor het beheren van de apparaten via een geconfigureerde Microsoft Intune-abonnement. Gebruikers kunnen de Android-bedrijfsportal-app waarmee ze Android (inclusief Samsung KNOX Standard)- en Android registreren voor werk apparaten downloaden van Google Play. 

Als een Configuration Manager-beheerder kunt u compatibiliteitsinstellingen beheren, wissen of verwijderen van Android-apparaten apps implementeren en software en hardware-inventaris verzamelen. Als de Android-bedrijfsportal-app is niet geïnstalleerd op Android-apparaten, klikt u vervolgens kunt u geen de beheermogelijkheden (zoals inventaris en compatibiliteitsinstellingen instellingen), maar u kunt nog steeds apps naar Android-apparaten implementeren.  

## <a name="enable-android-enrollment"></a>Android-inschrijving inschakelen  
De volgende stappen kunnen Configuration Manager beheren van Android-apparaten zonder een werkprofiel (dat wil zeggen "klassieke Android" inschrijving).

1. Voordat u de inschrijving voor elk platform instellen kunt, hebt u de vereisten en de procedures in [Setup hybride MDM](setup-hybrid-mdm.md).  
2. In de Configuration Manager-console in de **beheer** werkruimte kiezen **overzicht** > **Cloudservices** > **Microsoft Intune-abonnement** en kies uw Intune-abonnement.  
3. Op de **Start** tabblad de **abonnement** groep, kiest u **Platforms configureren** > **Android**.  
4. In de **eigenschappen van Microsoft Intune-abonnement** dialoogvenster Kies de **Android** tabblad en controleer de **inschakelen Android-inschrijving** vak.  

 Nadat u hebt ingesteld, moet u, kunnen uw gebruikers weten hoe u kunt hun apparaten kunnen inschrijven. Zie [Wat u uw eindgebruikers vertelt over het gebruik van Microsoft Intune](https://docs.microsoft.com/intune/deploy-use/what-to-tell-your-end-users-about-using-microsoft-intune). Deze informatie is van toepassing op mobiele apparaten die worden beheerd door Configuration Manager en Microsoft Intune.

## <a name="enable-android-for-work-enrollment"></a>Android inschakelen voor de inschrijving van werkitems
De volgende stappen kunnen Configuration Manager beheren van Android-apparaten zonder een werkprofiel (dat wil zeggen "klassieke Android" inschrijving).

1. Maakt een Google-account op https://accounts.google.com/SignUp wilt gebruiken als uw Android voor werk-beheeraccount. Of meld u aan met het account dat aan alle Android voor werk beheertaken voor deze tenant Intune gekoppeld worden zal. Dit wordt mogelijk een Google-account die wordt gedeeld onder de beheerders die Android-apparaten te beheren. Dit is het Google-account die gebruikmaakt van uw organisatie te beheren en publiceren van apps in de Play voor werk-console. U gebruikt dit account voor het goedkeuren van apps in de Play voor werk store, dus bijhouden van de accountnaam en wachtwoord.
2. Android-inschrijving inschakelen door het binden van Google-account voor de Intune-tenant die wordt beheerd in Configuration Manager:
   1. In de Configuration Manager-console in de **beheer** werkruimte kiezen **overzicht** > **Cloudservices** > **Microsoft Intune-abonnementen** en kies uw Intune-abonnement.
   2. Op de **Start** tabblad de **abonnement** groep, kiest u **Platforms configureren** > **Android for Work**.
   3. Kies in het dialoogvenster **Android configureren voor werkitems in de Intune-beheerconsole**. De Intune-console wordt geopend in uw webbrowser.
   4. Gebruik uw Intune-beheerdersreferenties aanmelden bij de Intune-portal.
   5. Kies **configureren** Android van Google Play voor werk website te openen.
   6. Voer de referenties van het Google-account uit stap 1 op van Google-aanmeldingspagina, en geef vervolgens de gegevens van uw bedrijf.
3. Wanneer u naar de Intune-portal terugkeert, Android for Work is ingeschakeld en hebt u drie Inschrijvingsopties voor Android voor werk apparaten:
   - **Alle apparaten beheren als Android** (uitgeschakeld). Alle Android-apparaten, met inbegrip van apparaten die ondersteuning bieden voor Android voor werk, worden geregistreerd als conventionele Android-apparaten.
   - **Ondersteunde apparaten beheren als Android for Work** (ingeschakeld). Alle apparaten die ondersteuning bieden voor Android voor taken die worden geregistreerd als Android voor werk apparaten. Een Android-apparaat dat biedt geen ondersteuning voor Android voor werk is geregistreerd als een conventionele Android-apparaat.
   - **Ondersteunde apparaten voor gebruikers alleen in deze groepen beheren als Android for Work** (voor bepaalde groepen alleen ingeschakeld). Hiermee kunt u zich richten op Android voor werkstroombeheer voor een beperkte set van gebruikers. Apparaten die ondersteuning bieden voor Android voor taken die worden geregistreerd als Android voor werk apparaten alleen als leden van de geselecteerde groepen registreren. Alle andere apparaten worden geregistreerd als Android-apparaten.

> [!NOTE]
> Een bekend probleem voorkomt dat de **beheren apparaten voor gebruikers in deze groepen alleen ondersteund als Android for Work** optie niet werkt zoals verwacht. Apparaten van gebruikers in de opgegeven Azure AD-groepen als Android in plaats van Android for Work gaan registreren. Om in te schakelen Android voor werk, moet u de **alle ondersteunde apparaten beheren als Android for Work** optie.


Nadat u hebt ingesteld, moet u, kunnen uw gebruikers weten hoe u kunt hun apparaten kunnen inschrijven. Zie [Wat u uw eindgebruikers vertelt over het gebruik van Microsoft Intune](https://docs.microsoft.com/intune/deploy-use/what-to-tell-your-end-users-about-using-microsoft-intune). Deze informatie is van toepassing op mobiele apparaten die worden beheerd door Configuration Manager en Microsoft Intune.

U ziet de accountnaam en de naam van de organisatie in de Intune-portal wanneer de binding is voltooid. Op dat moment kunt u beide browsers sluiten.

### <a name="enroll-an-android-for-work-device"></a>Een Android voor werk apparaat inschrijven
Hoe uw gebruikers Android inschrijven voor werk apparaten is vergelijkbaar met inschrijving voor Android. Gebruikers kunnen downloaden en installeren van de bedrijfsportal-app voor Android op hun mobiele apparaten. De app wordt gevraagd om een werkprofiel maken als onderdeel van het registratieproces. Nadat de werkprofiel is gemaakt, worden gebruikers moeten overschakelen naar de beheerde versie van de bedrijfsportal. De beheerde bedrijfsportal is gemarkeerd met een klein oranje werkmap in de rechterbenedenhoek.

### <a name="manage-android-for-work-devices"></a>Android voor werk apparaten beheren
Nadat u Android voor de inschrijving van het werk inschakelt, kunt u de volgende beheertaken uitvoeren voor Android voor werk apparaten:
- [Apps goedkeuren](/sccm/mdm/deploy-use/creating-android-applications#approve-and-deploy-android-for-work-apps)
- [Configuratie-items maken](/sccm/mdm/deploy-use/create-configuration-items-for-android-for-work-devices-managed-without-the-client)
- [Compatibiliteitsinstellingen beheren](/sccm/mdm/deploy-use/create-configuration-items-for-android-for-work-devices-managed-without-the-client)
- [E-mailprofielen beheert](/sccm/mdm/deploy-use/create-exchange-activesync-profiles)
- [De werkprofiel selectief wissen](/sccm/mdm/deploy-use/wipe-lock-reset-devices#selective-wipe)

> [!div class="button"]
[< Vorige stap](create-service-connection-point.md)[volgende stap >  ](set-up-additional-management.md)

