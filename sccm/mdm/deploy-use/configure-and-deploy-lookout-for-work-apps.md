---
title: Lookout voor werk app implementeren
titleSuffix: Configuration Manager
description: Configureren en implementeren van Lookout voor zakelijke apps.
ms.custom: na
ms.date: 03/05/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: configmgr-hybrid
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 3f62b763-4347-453d-b0a7-1f4a0d1d4105
caps.latest.revision: 
author: dougeby
ms.author: dougeby
manager: angrobe
ms.openlocfilehash: 02da89a5df37f328c387aa453f532e82b5153f87
ms.sourcegitcommit: c236214b2fcc13dae7bad96d7fb33f692868191d
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/12/2017
---
# <a name="configure-and-deploy-lookout-for-work-apps"></a>Configureer en implementeer Lookout voor bedrijfs-apps

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*

In dit artikel wordt uitgelegd hoe configureren en implementeren van de Lookout for Work-app voor Android en iOS-apparaten.

## <a name="android-google-play-store-app"></a>Android (Google Play Store-app)
1.  Klik in de Configuration Manager-console op **softwarebibliotheek** > **Toepassingsbeheer** > **toepassingen**.

2.  Geef op de pagina **Algemeen** van de wizard Software implementeren de volgende gegevens op:
  * Type: Selecteer **App-pakket voor Android in Google Play**.
  * Locatie: de Lookout for work app koppeling kopiëren uit de Google Play store, zoals hier plakken
  * Uitgever: Lookout mobiele beveiliging
  * Naam: Lookout for Work
  * Beschrijving: Lookout biedt de beste beveiliging tegen mobiele bedreigingen voor het beveiligen van uw apparaat. Wanneer de app Lookout op het apparaat is geïnstalleerd, wordt de app uw apparaat worden beschermd tegen bedreigingen en geeft een waarschuwing u en uw bedrijfsbeheerder aangetroffen.
  * Beheercategorie: Computerbeheer

  Na geslaagde voltooiing nu ziet u de Lookout for work-app in de lijst met toepassingen.

3.  Op de **Start** tabblad, in de **implementatie** groep, kiest u **implementeren** de Lookout for Work-app implementeren voor gebruikers.
>[!IMPORTANT]
>U moet dezelfde gebruikers toegevoegd aan de optie voor inschrijving in de console Lookout MTP selecteren.

  Kies de **vereiste installatie** optie vereist dat de app Lookout worden geïnstalleerd op het apparaat van de gebruiker.

## <a name="ios-enterprise-signed-version-of-lookout-app"></a>iOS (Enterprise ondertekend versie van Lookout app)

* **Stap 1:** Zorg ervoor dat **iOS-beheer** is ingesteld op uw apparaat. Zie voor instructies over het instellen van uw apparaat voor beheer van iOS [iOS en Mac-Apparaatbeheer instellen]().

* **Stap 2:** **Opnieuw ondertekenen** de Lookout for Work iOS-app. Lookout distribueert de Lookout for Work iOS-app buiten de iOS App Store. **Voordat u de app distribueert**, moet u de app opnieuw ondertekenen met het iOS Developer Enterprise-certificaat voor. Zie voor gedetailleerde instructies voor het ondertekenen van de Lookout for Work iOS-apps opnieuw [Lookout for Work iOS-app opnieuw te ondertekenen proces](https://personal.support.lookout.com/hc/en-us/articles/114094038714) op de site Lookout.


* **Stap 3:** Azure Active Directory-verificatie inschakelen voor de iOS-gebruikers als volgt:
  1.  Meld u aan bij de [Azure Active Directory-beheerportal](https://manage.windowsazure.com), en Ga naar de toepassingspagina.
  2.  Voeg de **Lookout for Work iOS-app** als een **native client-toepassing**.
  ![Schermafbeelding van de apps-dialoogvenster toevoegen met de native client app-optie](media/aad-add-app.png)

  3. Vervang de **com.lookout.enterprise.yourcompanyname** met de klant bundel-ID die u hebt geselecteerd toen u zich de IPA.
  4.  Toevoegen van aanvullende omleidings-URI:  **&lt;companyportal://code/ >** gevolgd door een URLencoded-versie van uw oorspronkelijke omleidings-URI.
  5.  Voeg **overgedragen machtigingen** aan uw app.

  Zie voor meer informatie [configureren van een systeemeigen clienttoepassing](https://azure.microsoft.com/en-us/documentation/articles/app-service-mobile-how-to-configure-active-directory-authentication/#optional-configure-a-native-client-application).


* **Stap 4:** Upload het opnieuw ondertekend IPA-bestand, zoals beschreven in de [iOS-toepassingen maken in System Center Configuration Manager-onderwerp](https://docs.microsoft.com/en-us/sccm/apps/get-started/creating-ios-applications) onderwerp. De minimale versie van besturingssysteem instellen op iOS 8.0 of hoger.


* **Stap 5:** De beheerde app-configuratiebeleid maken zoals beschreven in de [iOS-apps configureren met configuratiebeleid voor mobiele apps in System Center Configuration Manager](https://docs.microsoft.com/en-us/sccm/apps/deploy-use/configure-ios-apps-with-app-configuration-policies) onderwerp.


* **Stap 6:** **De app implementeren voor gebruikers**, selecteer de Lookout for Work-app in de **toepassingen** pagina van de **Start** tabblad, in de **implementatie** groep, kiest u **implementeren**.

  U moet dezelfde gebruikers die zijn toegevoegd aan de optie voor inschrijving in de console Lookout selecteren.  
Kies de **vereiste installatie** optie vereist dat de app Lookout worden geïnstalleerd op het apparaat van de gebruiker.

## <a name="what-happens-when-the-deployed-app-is-opened-on-the-device"></a>Wat gebeurt er wanneer de geïmplementeerde app wordt geopend op het apparaat




Wanneer de gebruiker de Lookout for Work op het apparaat opent wordt ze gevraagd de app activeren en kies de aanmelden Azure Active Directory-optie. In de volgende onderwerpen vindt u een gedetailleerd overzicht met de stroom van de eindgebruiker:

* [U wordt gevraagd Lookout for Work installeren op uw Android-apparaat](http://docs.microsoft.com/intune/enduser/you-are-prompted-to-install-lookout-for-work-android)

* [U moet een bedreiging die Lookout for Work op uw Android-apparaat gevonden oplossen](http://docs.microsoft.com/intune/enduser/you-need-to-resolve-a-threat-found-by-lookout-for-work-android)

## <a name="next-steps"></a>Volgende stappen
* [Device threat protection regel in het nalevingsbeleid inschakelen](enable-device-threat-protection-rule-compliance-policy.md)
