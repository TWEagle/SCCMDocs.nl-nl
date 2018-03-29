---
title: Lookout voor werk app implementeren
titleSuffix: Configuration Manager
description: Configureren en implementeren van Lookout voor zakelijke apps.
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
caps.latest.revision: ''
author: dougeby
ms.author: dougeby
manager: angrobe
ms.openlocfilehash: 01c388377948ab362d60951cb8398a9276e668fb
ms.sourcegitcommit: a19e12d5c3198764901d44f4df7c60eb542e765f
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 03/28/2018
---
# <a name="configure-and-deploy-lookout-for-work-apps"></a>Configureer en implementeer Lookout voor bedrijfs-apps

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*

In dit artikel wordt uitgelegd hoe configureren en implementeren van de Lookout for Work-app voor Android en iOS-apparaten.

## <a name="android-google-play-store-app"></a>Android (Google Play Store-app)
1.  Klik in de Configuration Manager-console op **softwarebibliotheek** > **Toepassingsbeheer** > **toepassingen**.

2.  Geef op de pagina **Algemeen** van de wizard Software implementeren de volgende gegevens op:  
    - Type: Selecteer **App-pakket voor Android in Google Play**.
    - Locatie: de Lookout for work app koppeling kopiëren uit de Google Play store, zoals hier plakken
    - Uitgever: Lookout mobiele beveiliging
    - Naam: Lookout for Work
    - Beschrijving: Lookout biedt de beste beveiliging tegen mobiele bedreigingen voor het beveiligen van uw apparaat. Wanneer de app Lookout is geïnstalleerd, de app uw apparaat worden beschermd tegen bedreigingen. Als er bedreigingen, er een waarschuwing gegeven u en uw IT-beheerder.
    - Beheercategorie: Computerbeheer  

    Geslaagde is voltooid ziet u de Lookout for Work-app in de lijst met toepassingen.

3.  Op de **Start** tabblad, in de **implementatie** groep, kiest u **implementeren** de Lookout for Work-app implementeren voor gebruikers.   
    >[!IMPORTANT]  
    >U moet dezelfde gebruikers toegevoegd aan de optie voor inschrijving in de console Lookout MTP selecteren.  

    Kies de **vereiste installatie** optie. Deze optie moet de app Lookout installeren op het apparaat van de gebruiker.  



## <a name="ios-enterprise-signed-version-of-lookout-app"></a>iOS (enterprise ondertekend versie van Lookout app)

- **Stap 1:** Zorg ervoor dat **iOS-beheer** is ingesteld op uw apparaat. Zie voor instructies over het instellen van uw apparaat voor beheer van iOS [iOS en Mac-Apparaatbeheer instellen](/sccm/mdm/deploy-use/enroll-hybrid-ios-mac).

- **Stap 2:** **Opnieuw ondertekenen** de Lookout for Work iOS-app. Lookout distribueert de Lookout for Work iOS-app buiten de iOS App Store. **Voordat u de app distribueert**, moet u de app opnieuw ondertekenen met het iOS Developer Enterprise-certificaat voor. Zie voor gedetailleerde instructies voor het ondertekenen van de Lookout for Work iOS-apps opnieuw [Lookout for Work iOS-app opnieuw te ondertekenen proces](https://personal.support.lookout.com/hc/articles/114094038714) op de site Lookout.


- **Stap 3:** Azure Active Directory-verificatie inschakelen voor de iOS-gebruikers als volgt u de volgende stappen uit:
  1.  Meld u aan bij de [Azure Active Directory-beheerportal](https:/portal.azure.com), en Ga naar de toepassingspagina.
  2.  Voeg de **Lookout for Work iOS-app** als een **native client-toepassing**.
  ![Schermafbeelding van de apps-dialoogvenster toevoegen met de native client app-optie](media/aad-add-app.png)

  3. Vervang de **com.lookout.enterprise.yourcompanyname** met de klant bundel-ID die u hebt geselecteerd toen u zich de IPA.
  4.  Toevoegen van aanvullende omleidings-URI:  **&lt;companyportal://code/ >** gevolgd door een URLencoded-versie van uw oorspronkelijke omleidings-URI.
  5.  Voeg **overgedragen machtigingen** aan uw app.

  Zie voor meer informatie [configureren van een systeemeigen clienttoepassing](/azure/app-service/app-service-mobile-how-to-configure-active-directory-authentication#optional-configure-a-native-client-application).


- **Stap 4:** Upload het opnieuw ondertekend IPA-bestand, zoals beschreven in de [iOS-toepassingen maken in System Center Configuration Manager-onderwerp](/sccm/apps/get-started/creating-ios-applications) onderwerp. De minimale versie van besturingssysteem instellen op iOS 8.0 of hoger.


- **Stap 5:** De beheerde app-configuratiebeleid maken zoals beschreven in de [iOS-apps configureren met configuratiebeleid voor mobiele apps in System Center Configuration Manager](/sccm/apps/deploy-use/configure-ios-apps-with-app-configuration-policies) onderwerp.


- **Stap 6:** **De app implementeren voor gebruikers**, selecteer de Lookout for Work-app in de **toepassingen** pagina van de **Start** tabblad, in de **implementatie** groep, kiest u  **Implementeer**.

  Selecteer dezelfde gebruikers die zijn toegevoegd aan de optie voor inschrijving in de console Lookout. Kies de **vereiste installatie** optie. Deze optie moet de app Lookout installeren op het apparaat van de gebruiker.



## <a name="what-happens-when-the-deployed-app-is-opened-on-the-device"></a>Wat gebeurt er wanneer de geïmplementeerde app wordt geopend op het apparaat

Wanneer de gebruiker de Lookout for Work op het apparaat opent, wordt gevraagd deze om de app te activeren. Ze moeten zich aanmelden via de Azure Active Directory-optie kiezen. Er is een gedetailleerd overzicht met de stroom door eindgebruikers in de volgende artikelen:

- [U wordt gevraagd Lookout for Work installeren op uw Android-apparaat](/intune-user-help/you-are-prompted-to-install-lookout-for-work-android)

- [U moet een bedreiging die Lookout for Work op uw Android-apparaat gevonden oplossen](/intune-user-help/you-need-to-resolve-a-threat-found-by-lookout-for-work-android)



## <a name="next-steps"></a>Volgende stappen
- [Device threat protection regel in het nalevingsbeleid inschakelen](enable-device-threat-protection-rule-compliance-policy.md)
