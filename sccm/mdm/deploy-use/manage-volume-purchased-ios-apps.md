---
title: Volume-purchased iOS-apps beheren | Microsoft Docs
description: Implementeren, beheren en bijhouden van licenties voor apps die u hebt aangeschaft via de iOS appstore.
ms.custom: na
ms.date: 05/12/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: configmgr-hybrid
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 7c3b9316-247b-490b-a363-8f8553821579
caps.latest.revision: "18"
caps.handback.revision: "0"
author: mtillman
ms.author: mtillman
manager: angrobe
ms.openlocfilehash: ce706e938f558406044f7890c80bb7156c3b262b
ms.sourcegitcommit: 51fc48fb023f1e8d995c6c4eacfda7dbec4d0b2f
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 08/07/2017
---
# <a name="manage-volume-purchased-ios-apps-with-system-center-configuration-manager"></a>Met System Center Configuration Manager iOS-apps beheren die zijn gekocht via het volume-aankoopprogramma

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*



 De iOS appstore kunt u koopt meerdere licenties voor een app die u wilt uitvoeren binnen uw bedrijf. Zo kunt u de administratieve overhead voor het bijhouden van meerdere exemplaren van apps die u hebt gekocht reduceren.  

 System Center Configuration Manager helpt u bij het implementeren en beheren van iOS-apps die u via het programma hebt aangeschaft door de licentiegegevens uit de appstore te importeren en bij te houden van het nummer van de licenties die worden gebruikt.  

## <a name="manage-volume-purchased-apps-for-ios-devices"></a>Volume-purchased apps voor iOS-apparaten beheren  
 U koopt meerdere licenties voor iOS-apps via het Apple Volume Purchase Program (VPP). Hiervoor moet u een Apple VPP-account via de website van Apple instellen en het Apple VPP-token uploaden naar Configuration Manager, dat de volgende mogelijkheden biedt:  

-   Synchroniseren van uw aankoop volumegegevens met Configuration Manager. 
 
- Het Apple Volume Purchase Program voor bedrijven en het Apple Volume Purchase Program voor onderwijs-Sync apps.

- Koppelen van meerdere Apple volume purchase program-tokens met Configuration Manager.

-   Apps die u hebt aangeschaft, worden weergegeven in de Configuration Manager-console.  

-   U kunt apps implementeren, deze apps controleren en bijhouden van het aantal licenties voor elke app die is gebruikt.  

-   Configuration Manager kunt u licenties indien nodig met het verwijderen van volume-aankoopprogramma gekochte apps die u hebt geïmplementeerd vrijmaken.  

## <a name="before-you-start"></a>Voordat u begint  
 Voordat u begint, moet u een VPP-token ophalen van Apple en upload dit naar Configuration Manager.  

-   Als u eerder een VPP-token met een ander MDM-product in uw bestaande Apple VPP-account gebruikt, moet u een nieuwe token voor gebruik met Configuration Manager genereren.  
-   Elke token is één jaar geldig.  
-   Standaard Configuration Manager wordt gesynchroniseerd met de Apple VPP-service twee keer per dag om ervoor te zorgen dat uw licenties met Configuration Manager worden gesynchroniseerd.  
      Alleen wijzigingen in uw licenties zijn gesynchroniseerd. Maar om de zeven dagen, een volledige synchronisatie worden uitgevoerd.  
      Wanneer u de optie **Sync** hiertoe een handmatige synchronisatie, zal dit altijd een volledige synchronisatie uitvoeren.  
-   Als u wilt herstellen of herstellen van Configuration Manager-database, wordt u aangeraden dat u een handmatige synchronisatie later om ervoor te zorgen dat uw gesynchroniseerde licentiegegevens up-to-date doen.  
-   Bovendien, moet u hebt geïmporteerd een geldig certificaat voor Apple Push Notification service (APNs) van Apple zodat u voor het beheren van iOS-apparaten, met inbegrip van app-implementatie. Zie voor meer informatie [iOS hybride Apparaatbeheer instellen](enroll-hybrid-ios-mac.md).  
-   Configuration Manager ondersteunt maximaal 3000 VPP-tokens toevoegen.

Beginnen met System Center Configuration Manager 1702, kunt u gelicentieerde apps implementeren op apparaten, evenals gebruikers. Afhankelijk van de apps mogelijkheid om apparaat-licentieverlening te ondersteunen, wordt een juiste licentie wordt geclaimd bij het implementeren, als volgt:

|||||
|-|-|-|-|
|Versie van Configuration Manager|App ondersteunt apparaat licentieverlening?|Implementatietype van de verzameling|De geclaimde licentie|
|Ouder dan 1702|Ja|Gebruiker|Gebruikerslicentie|
|Ouder dan 1702|Nee|Gebruiker|Gebruikerslicentie|
|Ouder dan 1702|Ja|Apparaat|Gebruikerslicentie|
|Ouder dan 1702|Nee|Apparaat|Gebruikerslicentie|
|1702 en hoger|Ja|Gebruiker|Gebruikerslicentie|
|1702 en hoger|Nee|Gebruiker|Gebruikerslicentie|
|1702 en hoger|Ja|Apparaat|Apparaatlicentie|
|1702 en hoger|Nee|Apparaat|Gebruikerslicentie|

## <a name="step-1---to-get-and-upload-an-apple-vpp-token"></a>Stap 1: een Apple VPP-token verkrijgen en uploaden  

1.  Kies in de Configuration Manager-console **beheer** > **Cloudservices** > **Apple Volume Purchase Program-Tokens**.   

3.  Op de **Start** tabblad, in de **Apple Volume Purchase Program-Tokens** groep, kiest u **toevoegen Apple Volume Purchase Program-Token**.  

4.  Op de **algemene** pagina van de **toevoegen Apple Volume Purchase Program-Token** wizard configureert u het volgende:   

    -   **Naam** -Voer een naam voor dit token, zoals het moet worden weergegeven in de Configuration Manager-console.  

    -   **Token** -Kies **Bladeren**, en kies vervolgens het VPP-token dat u hebt gedownload van de website van Apple.  

         Kies de **Zie Apple VPP-account** koppelen, en als u nog niet gedaan hebt, meldt u voor de bedrijven of onderwijsinstellingen volume purchase program. Nadat u zich hebt aangemeld, download u het Apple VPP-token voor uw account.  

    -   **Beschrijving** : Geef indien gewenst, voer een beschrijving in waarmee u deze VPP-token in de Configuration Manager-console te identificeren.  

    -   **Toegewezen categorieën voor het verbeteren van zoeken en filteren** : Geef indien gewenst, kunt u categorieën toewijzen aan het VPP-token maken het gemakkelijker om te zoeken naar in de Configuration Manager-console.  
    -   **Apple-ID** -voert u de apple-e-mail-ID die is gekoppeld aan het VPP-Token.
    -   **Type token** -Selecteer het type VPP-token die u wilt gebruiken. U kunt kiezen **Business** en **EDU** token typen.

5.  Kies **volgende**, en voltooi de wizard.  

Van de **Apple Volume Purchase Program-Tokens** knooppunt, u kunt nu informatie bekijken over het Apple VPP-token, inclusief wanneer het laatst is bijgewerkt, wanneer het verloopt en wanneer deze voor het laatst is gesynchroniseerd.

U kunt de gegevens waarover Apple met Configuration Manager op elk gewenst moment door te kiezen volledig synchroniseren **Sync** op de **Start** tabblad de **Sync** groep.  

## <a name="step-2---deploy-a-volume-purchased-app"></a>Stap 2: een volume-purchased app implementeren  

1.  Kies in de Configuration Manager-console **softwarebibliotheek** > **Toepassingsbeheer** > **licentiegegevens voor Store-Apps**.  

3.  Kies de app die u implementeren wilt, en klikt u op de **Start** tabblad, in de **maken** groep, kiest u **toepassing maken**.
De Configuration Manager-toepassing die is gemaakt, heeft de Windows Store voor bedrijven-app. U kunt implementeren en bewaken van deze toepassing, net als elke andere Configuration Manager-toepassing.

    > [!IMPORTANT]  
    > U moet een implementatiedoel van kiezen **vereist**. Beschikbare installaties worden momenteel niet ondersteund.

 Wanneer u de app implementeert, wordt een licentie wordt gebruikt door elke gebruiker of voor apparaat installeert, elk apparaat waarop de app installeert.  Wanneer u een apparatenverzameling aan een app dat apparaat licentieverlening ondersteunt, wordt een apparaatlicentie geclaimd.  Wanneer u een apparatenverzameling aan een app die geen ondersteuning biedt voor het apparaat-licentieverlening, wordt een licentie aangevraagd. 

 Bij het maken van een app van de **licentiegegevens voor Store-Apps** knooppunt, de app is gekoppeld aan de licenties van het token voor de app die u hebt geselecteerd.  U ziet bijvoorbeeld twee versies van dezelfde app in het knooppunt. Dit is omdat elke versie van de app gekoppeld aan een ander Apple VPP-token is.  Vervolgens kan u apps uit elke token maken en deze afzonderlijk implementeren.

 Een als licentie wilt vrijmaken, moet u een nieuwe implementatie voor de app maken met de implementatieactie **verwijderen**. U kunt de implementatie-actie in de oorspronkelijke implementatie niet wijzigen. De licentie wordt vrijgemaakt nadat de app is verwijderd.  

## <a name="step-3---monitor-ios-vpp-apps"></a>Stap 3: iOS VPP-apps bewaken  
 De **licentiegegevens voor Store-Apps** knooppunt van de **softwarebibliotheek** werkruimte geeft informatie weer over uw volume-purchased iOS-apps. De informatie omvat het totale aantal licenties dat u bezit voor elke app en het aantal die zijn geïmplementeerd. Bovendien ziet de weergave u welke VPP-token dat de app is gekoppeld en het type van het token

 U kunt ook bewaken met het licentiegebruik van alle VPP-apps die u hebt aangeschaft via de **Apple Volume Purchase Program-apps voor iOS met licentieaantallen** rapport.  

 Dit rapport geeft de naam van elke toepassing samen met het totale aantal licenties dat u hebt gekocht, het aantal licenties beschikbaar zijn, en meer.  

 Zie voor informatie over het uitvoeren van Configuration Manager-rapporten, [rapportage in System Center Configuration Manager](../../core/servers/manage/reporting.md).  
