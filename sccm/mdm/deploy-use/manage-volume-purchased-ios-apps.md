---
title: Volume aangeschaft iOS-apps beheren | Microsoft-documenten
description: Implementeren, beheren en licenties voor apps die u hebt aangeschaft via de iOS appstore.
ms.custom: na
ms.date: 05/12/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-hybrid
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 7c3b9316-247b-490b-a363-8f8553821579
caps.latest.revision: 18
caps.handback.revision: 0
author: mtillman
ms.author: mtillman
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: f4cb711f369698fe8e045f8c83dd96ec6fb29d70
ms.openlocfilehash: ce706e938f558406044f7890c80bb7156c3b262b
ms.contentlocale: nl-nl
ms.lasthandoff: 05/17/2017

---
# <a name="manage-volume-purchased-ios-apps-with-system-center-configuration-manager"></a>Met System Center Configuration Manager iOS-apps beheren die zijn gekocht via het volume-aankoopprogramma

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*



 De iOS appstore kunt u meerdere licenties voor een app die u wilt uitvoeren in uw bedrijf kopen. Zo kunt u de administratieve overhead van het bijhouden van meerdere exemplaren van apps die u hebt aangeschaft verminderen.  

 System Center Configuration Manager helpt u bij het implementeren en beheren van iOS-apps die u hebt aangeschaft via het programma door de licentiegegevens uit de appstore en het volgnummer van de licenties die worden gebruikt.  

## <a name="manage-volume-purchased-apps-for-ios-devices"></a>Volume-purchased apps voor iOS-apparaten beheren  
 U zult meerdere licenties voor iOS-apps via Apple Volume aankoop programma (VPP) aanschaffen. Dit omvat het instellen van een Apple VPP-account van de website van Apple en het Apple VPP-token uploaden naar Configuration Manager, waarmee u de volgende mogelijkheden:  

-   Uw aankoop volumegegevens met Configuration Manager worden gesynchroniseerd. 
 
- Synchronisatie-apps van het Volume Purchase Program van Apple voor bedrijven en het Volume Purchase Program van Apple voor onderwijs.

- Meerdere Apple volume aankoop programma tokens met Configuration Manager koppelen.

-   Apps die u hebt aangeschaft, worden weergegeven in de Configuration Manager-console.  

-   U kunt apps implementeren, bewaken van deze apps en het aantal licenties voor elke app die is gebruikt.  

-   Configuration Manager kunt u licenties indien vereist door het verwijderen van volume aangeschaft apps die u implementeerde claimen.  

## <a name="before-you-start"></a>Voordat u begint  
 Voordat u begint, moet u een VPP-token ophalen van Apple ontvangen en dit te uploaden naar Configuration Manager.  

-   Als u eerder een VPP-token met een ander MDM-product in uw bestaande Apple VPP-account gebruikt, moet u een nieuwe moet worden gebruikt met Configuration Manager genereren.  
-   Elke token is één jaar geldig.  
-   Standaard Configuration Manager wordt gesynchroniseerd met de Apple VPP-service twee keer per dag om ervoor te zorgen dat uw licenties zijn gesynchroniseerd met Configuration Manager.  
      Alleen wijzigingen van uw licenties zijn gesynchroniseerd. Maar één keer elke zeven dagen een volledige synchronisatie wordt uitgevoerd.  
      Als u zich **Sync** hiertoe een handmatige synchronisatie, zal dit altijd een volledige synchronisatie uitvoeren.  
-   Als u wilt herstellen of u Configuration Manager-database te herstellen, raden wij aan dat u een handmatige synchronisatie om ervoor te zorgen dat uw gesynchroniseerde licentiegegevens actueel te doen.  
-   Bovendien, moet u hebt geïmporteerd een geldig certificaat voor Apple Push Notification service (APNs) van Apple ontvangen waarmee u voor het beheren van iOS-apparaten, met inbegrip van app-implementatie. Zie voor meer informatie [iOS hybride device management instellen](enroll-hybrid-ios-mac.md).  
-   Configuration Manager ondersteunt het toevoegen van maximaal 3000 VPP-tokens.

Beginnen met System Center Configuration Manager 1702, kunt u gelicentieerde apps implementeren op apparaten en gebruikers. Afhankelijk van de mogelijkheid apps voor ondersteuning van apparaat licentieverlening zal de juiste licentie worden gevraagd tijdens de implementatie, als volgt:

|||||
|-|-|-|-|
|Configuration Manager-versie|App apparaat licentieverlening ondersteunt?|Verzameling van implementatietype|Vermeende licentie|
|Ouder is dan 1702|Ja|Gebruiker|Gebruikerslicentie|
|Ouder is dan 1702|Nee|Gebruiker|Gebruikerslicentie|
|Ouder is dan 1702|Ja|Apparaat|Gebruikerslicentie|
|Ouder is dan 1702|Nee|Apparaat|Gebruikerslicentie|
|1702 en hoger|Ja|Gebruiker|Gebruikerslicentie|
|1702 en hoger|Nee|Gebruiker|Gebruikerslicentie|
|1702 en hoger|Ja|Apparaat|Apparaatlicentie|
|1702 en hoger|Nee|Apparaat|Gebruikerslicentie|

## <a name="step-1---to-get-and-upload-an-apple-vpp-token"></a>Stap 1: een Apple VPP-token verkrijgen en uploaden  

1.  Kies in de Configuration Manager-console **beheer** > **Cloudservices** > **Apple Volume aankoop programma Tokens**.   

3.  Op de **Start** tabblad, in de **Apple Volume aankoop programma Tokens** groep, kiest u **toevoegen Apple Volume aankoop programma Token**.  

4.  Op de **algemeen** pagina van de **toevoegen Apple Volume aankoop programma Token** wizard, configureer dan het volgende:   

    -   **Naam** -Geef een naam voor dit token zoals die wordt weergegeven in de Configuration Manager-console.  

    -   **Token** -kiezen **Bladeren**, en kies vervolgens het VPP-token dat u hebt gedownload van de website van Apple.  

         Kies de **Zie Apple VPP-account** koppelen, en als u nog niet gedaan hebt, meldt u voor het bedrijf of opleiding aankoopprogramma van volume. Nadat u bent aangemeld, downloadt u het Apple VPP-token voor uw account.  

    -   **Beschrijving** - u kunt desgewenst een omschrijving waarmee u bij het identificeren van deze VPP-token in de Configuration Manager-console.  

    -   **Toegewezen categorieën voor het verbeteren van zoeken en filteren** - eventueel kunt u categorieën toewijzen aan het VPP-token eenvoudiger te zoeken in de Configuration Manager-console.  
    -   **Apple-ID** -dat is gekoppeld aan het VPP-Token van apple-e-ID invoeren.
    -   **Type token** -Selecteer het type VPP-token die u wilt gebruiken. U kunt kiezen **Business** en **EDU** token typen.

5.  Kies **volgende**, en voltooi de wizard.  

Van de **Apple Volume aankoop programma Tokens** knooppunt, kunt u nu informatie over het Apple VPP-token toevoegen wanneer deze het laatst werd bijgewerkt, wanneer het verloopt en wanneer het laatst is gesynchroniseerd weergeven.

U kunt de gegevens vastgehouden door Apple met Configuration Manager op elk gewenst moment door het kiezen van volledig synchroniseren **Sync** op de **Start** tabblad de **Sync** groep.  

## <a name="step-2---deploy-a-volume-purchased-app"></a>Stap 2: een volume-purchased app implementeren  

1.  Kies in de Configuration Manager-console **softwarebibliotheek** > **Toepassingsbeheer** > **licentie-informatie voor de Store-Apps**.  

3.  Kies de app die u implementeren wilt, en klik in de **Start** tabblad, in de **maken** groep, kiest u **toepassing maken**.
De Configuration Manager-toepassing die is gemaakt, heeft de Windows Store voor Business-app. U kunt vervolgens implementeren en controleren van deze toepassing als u een andere Configuration Manager-toepassing.

    > [!IMPORTANT]  
    > U moet een implementatiedoel van kiezen **vereist**. Beschikbare installaties zijn momenteel niet ondersteund.

 Wanneer u de app implementeert, wordt een licentie wordt gebruikt door elke gebruiker of voor apparaat installeert, elk apparaat waarop de app wordt geïnstalleerd.  Als u een apparatenverzameling aan een app die ondersteuning biedt voor apparaat licentieverlening richt, wordt een apparaatlicentie geclaimd.  Als u een apparatenverzameling aan een app die geen ondersteuning biedt voor het apparaat licentieverlening richt, wordt een gebruikerslicentie geclaimd. 

 Bij het maken van een app uit de **licentie-informatie voor de Store-Apps** knooppunt de app is gekoppeld aan de licenties van het token voor de app die u hebt geselecteerd.  U ziet bijvoorbeeld twee versies van dezelfde app in het knooppunt. Dit is omdat elke versie van de app gekoppeld aan een andere Apple VPP-token is.  Vervolgens kan u apps van elke token maken en deze afzonderlijk implementeren.

 Als u wilt een licentie vrijmaken, moet u een nieuwe implementatie voor de app maken met een implementatiebewerking van **verwijderen**. U kunt de implementatie-actie in de oorspronkelijke implementatie niet wijzigen. De licentie vrijgemaakt nadat de app wordt verwijderd.  

## <a name="step-3---monitor-ios-vpp-apps"></a>Stap 3: iOS VPP-apps bewaken  
 De **licentie-informatie voor de Store-Apps** knooppunt van de **softwarebibliotheek** werkruimte geeft informatie weer over uw volume aangeschaft iOS-apps. De informatie omvat het totale aantal licenties dat u bezit voor elke app en het aantal die zijn geïmplementeerd. Daarnaast ziet de weergave u welke VPP-token dat de app is gekoppeld en het type van het token

 U kunt ook bewaken met het gebruik van licenties van alle VPP-apps die u hebt aangeschaft via de **Apple Volume Purchase Program apps voor iOS met licentie aantallen** rapport.  

 Dit rapport geeft de naam van elke toepassing samen met het totale aantal licenties dat u hebt gekocht, het aantal licenties beschikbaar zijn, en meer.  

 Zie voor meer informatie over het uitvoeren van Configuration Manager-rapporten [rapportage in System Center Configuration Manager](../../core/servers/manage/reporting.md).  

