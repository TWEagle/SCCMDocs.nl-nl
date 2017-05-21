---
title: Zoek voor werk app implementeren | Microsoft-documenten
description: Configureren en dan voor zakelijke apps te implementeren.
ms.custom: na
ms.date: 03/05/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-hybrid
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 3f62b763-4347-453d-b0a7-1f4a0d1d4105
caps.latest.revision: 
author: mtillman
ms.author: mtillman
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 6424fb07802b62820b4dc78a58ab30d3b956abef
ms.openlocfilehash: 59f43c922d1d3bc64625733014b0def1e42c4d2d
ms.contentlocale: nl-nl
ms.lasthandoff: 05/17/2017


---
# <a name="configure-and-deploy-lookout-for-work-apps"></a>Configureer en implementeer altijd voor zakelijke apps

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*

Dit artikel wordt uitgelegd hoe configureren en zoek naar werk app voor Android en iOS-apparaten implementeren.

## <a name="android-google-play-store-app"></a>Android (Google Play Store app)
1.  Klik in de Configuration Manager-console op **softwarebibliotheek** > **Toepassingsbeheer** > **toepassingen**.

2.  Geef op de pagina **Algemeen** van de wizard Software implementeren de volgende gegevens op:
  * Type: Selecteer **App-pakket voor Android in Google Play**.
  * Locatie: zoek naar werk app koppeling kopiëren uit de Google Play store zoals hier plakken
  * Uitgever: Zoek mobiele beveiliging
  * Naam: Zoek naar werk
  * Beschrijving: Zoek biedt de beste beveiliging tegen mobiele bedreigingen om uw apparaat te beschermen. Wanneer de app Zoek op het apparaat is geïnstalleerd, wordt de app beschermt u uw apparaat tegen bedreigingen en geeft een waarschuwing u en uw bedrijfsbeheerder aangetroffen.
  * Beheercategorie: Computerbeheer

  Na geslaagde voltooiing nu ziet u altijd werk app in de lijst met toepassingen.

3.  Op de **Start** tabblad, in de **implementatie** groep, kiest u **implementeren** altijd werk app implementeren voor gebruikers.
>[!IMPORTANT]
>U moet dezelfde gebruikers die zijn toegevoegd aan de inschrijving Beheeroptie in de console altijd MTP selecteren.

  Kies de **vereiste installatie** optie vereist dat de app altijd worden geïnstalleerd op het apparaat van de gebruiker.

## <a name="ios-enterprise-signed-version-of-lookout-app"></a>iOS (versie Enterprise ondertekend van altijd app)

* **Stap 1:** Zorg ervoor dat **iOS-beheer** is ingesteld op het apparaat. Zie voor instructies over het instellen van uw apparaat voor iOS-beheer, [stellen iOS- en Apparaatbeheer Mac]().

* **Stap 2:** **Onderteken het opnieuw** altijd werk iOS-app. Zoek distribueert de altijd werk iOS-app buiten de iOS App Store. **Voordat u de app distribueert**, u moet de app opnieuw met het iOS Developer Enterprise-certificaat voor ondertekenen. Zie voor gedetailleerde instructies opnieuw ondertekenen altijd werk iOS-apps [werk iOS-app opnieuw proces ondertekenen altijd](https://personal.support.lookout.com/hc/en-us/articles/114094038714) op de site dan.


* **Stap 3:** Azure Active Directory-verificatie inschakelen voor de iOS-gebruikers als volgt:
  1.  Meld u aan bij de [Azure Active Directory-beheerportal](https://manage.windowsazure.com), en gaat u naar de pagina van de toepassing.
  2.  Voeg de **dan werk iOS-app** als een **native client-toepassing**.
  ![Schermafdruk van het apps-dialoogvenster toevoegen met de native client app-optie](media/aad-add-app.png)

  3. Vervang de **com.lookout.enterprise.yourcompanyname** bundel-ID die u hebt geselecteerd toen u de IPA ondertekend met de klant.
  4.  Toevoegen van aanvullende omleidings-URI:  **&lt;companyportal://code/ >** gevolgd door een URLencoded-versie van uw oorspronkelijke omleidings-URI.
  5.  Voeg **overgedragen machtigingen** aan uw app.

  Zie voor meer informatie [een native client configureren](https://azure.microsoft.com/en-us/documentation/articles/app-service-mobile-how-to-configure-active-directory-authentication/#optional-configure-a-native-client-application).


* **Stap 4:** Het opnieuw ondertekend IPA-bestand uploaden, zoals beschreven in de [iOS-toepassingen maken in System Center Configuration Manager onderwerp](https://docs.microsoft.com/en-us/sccm/apps/get-started/creating-ios-applications) onderwerp. De minimale versie van het besturingssysteem ingesteld op iOS 8.0 of hoger.


* **Stap 5:** Maak het configuratiebeleid beheerde app, zoals beschreven in de [iOS-apps met configuratiebeleid voor mobiele app in System Center Configuration Manager configureren](https://docs.microsoft.com/en-us/sccm/apps/deploy-use/configure-ios-apps-with-app-configuration-policies) onderwerp.


* **Stap 6:** **De app implementeren voor gebruikers**, selecteert u altijd werk app in de **toepassingen** pagina van de **Start** tabblad, in de **implementatie** groep, kiest u **implementeren**.

  U moet dezelfde gebruikers die zijn toegevoegd aan de inschrijving Beheeroptie in de console altijd selecteren.  
Kies de **vereiste installatie** optie vereist dat de app altijd worden geïnstalleerd op het apparaat van de gebruiker.

## <a name="what-happens-when-the-deployed-app-is-opened-on-the-device"></a>Wat gebeurt er wanneer de geïmplementeerde app wordt geopend op het apparaat




Wanneer de gebruiker wordt geopend. Zoek for Work op het apparaat wordt ze gevraagd naar de app activeren en kies de Meld u aan met Azure Active Directory-optie. Een gedetailleerd overzicht met de stroom door eindgebruikers vindt u in de volgende onderwerpen:

* [U wordt gevraagd werk altijd installeren op een Android-apparaat](http://docs.microsoft.com/intune/enduser/you-are-prompted-to-install-lookout-for-work-android)

* [U moet een bedreiging die altijd for Work op een Android-apparaat gevonden oplossen](http://docs.microsoft.com/intune/enduser/you-need-to-resolve-a-threat-found-by-lookout-for-work-android)

## <a name="next-steps"></a>Volgende stappen
* [Regel voor de beveiliging van apparaat bedreiging in het nalevingsbeleid inschakelen](enable-device-threat-protection-rule-compliance-policy.md)

