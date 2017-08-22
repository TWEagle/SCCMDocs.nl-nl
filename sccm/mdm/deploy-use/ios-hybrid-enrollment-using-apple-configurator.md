---
title: IOS-apparaten Apple Configurator - Configuration Manager inschrijven | Microsoft Docs
descriptions: Pre-enroll iOS devices by using Apple Configurator with Configuration Manager.
ms.custom: na
ms.date: 08/15/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: configmgr-hybrid
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 61a19d95-83ff-4ad8-9a67-f304d2ba54f2
caps.latest.revision: "5"
author: mtillman
ms.author: mtillman
manager: angrobe
ms.openlocfilehash: 403f3b730e24c0f76314b04bcdd1d2f817bcd908
ms.sourcegitcommit: db7b7ec347638efd05cdba474e8a8f8535516116
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 08/16/2017
---
# <a name="ios-hybrid-enrollment-using-apple-configurator-with-configuration-manager"></a>inschrijving van hybride iOS met Apple Configurator met Configuration Manager

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*

Bedrijven die kopen van iOS-apparaten moet worden gebruikt door werknemers kunnen deze met Microsoft Intune beheren. Als u met het voorbereiden van zakelijke eigendom iOS-apparaten voor inschrijving, een inschrijvingsprofiel configureren in de Configuration Manager-console en vervolgens de profiel-URL voor gebruik door Apple Configurator te exporteren. U voorbereiden voor de inschrijving van het iOS-apparaat door verbinding maken met een Mac-computer met een USB-kabel en met behulp van Apple Configurator instellen. Apple Configurator factory fabrieksinstellingen van het apparaat en het inschrijvingsprofiel toegevoegd zodat het apparaat kan worden geregistreerd wanneer de gebruiker eerst drijft de en Configuratieassistent proces.

De volgende procedure wordt aanbevolen voor specifieke iOS-apparaten waarvoor een afzonderlijke gebruiker die gebruikmaakt van het apparaat toegang tot bedrijfse-mail en andere bedrijfsresources, zoals apps en datum.  

## <a name="prerequisites"></a>Vereisten  

-   Fysieke toegang tot iOS-apparaten  

-   Serienummers - [het ophalen van een iOS-serienummer](https://support.apple.com/en-us/HT204308)  

-   Mac-computer met [Apple Configurator 2.0](http://go.microsoft.com/fwlink/?LinkId=518017)  

-   USB-kabels voor het verbinden van apparaten met uw Mac-computer  

## <a name="add-a-corporate-owned-device-enrollment-profile"></a>Een inschrijvingsprofiel voor apparaten in Bedrijfseigendom toevoegen

1.  Ga in de Configuration Manager-console naar **activa en naleving** > **overzicht** > **alle apparaten in Bedrijfseigendom** > **iOS** > **Inschrijvingsprofielen**. Klik op **profiel maken** om de wizard profiel maken te openen. Configureer de instellingen op de volgende pagina's:  

2.  Geef op de pagina **Algemeen** de volgende gegevens op:  

    -   **Naam** (niet zichtbaar voor gebruikers)  

    -   **Beschrijving** (niet zichtbaar voor gebruikers)  

    -   **Gebruikersaffiniteit** : hiermee wordt bepaald hoe apparaten worden ingeschreven. Gebruik voor de meeste Configuratieassistent-scenario's **Vragen voor relatie met gebruiker**.  

        -   **Vragen om gebruikersaffiniteit**: Het apparaat moet aan een gebruiker worden gekoppeld tijdens de eerste configuratie en dan toegang tot bedrijfsgegevens en e-mailadres als die gebruiker is toegestaan.  

        -   **Geen relatie met gebruiker**: Het apparaat is niet gekoppeld aan een gebruiker. Gebruik deze relatie voor apparaten waarmee taken worden uitgevoerd zonder toegang tot lokale gebruikersgegevens. Apps die een gebruikersrelatie vereisen, werken niet.

    Klik op **Volgende** om verder te gaan.  

3.  Op de **Device Enrollment Program** pagina, laat u de **configureren apparaat registratie programma-instellingen voor dit profiel** selectievakje dit selectievakje uitschakelt, en klik op **volgende**.  

4.  Bekijk het overzicht en klik vervolgens op **volgende** het inschrijvingsprofiel maken. Klik op **Sluiten** om de wizard te voltooien. U kunt nu IMEI-nummers of serienummers van de apparaten die u wilt inschrijven toe te voegen.  

## <a name="predeclare-devices-to-enroll-with-setup-assistant"></a>Apparaten voor inschrijving met Configuratieassistent labelen

In deze stap kunt u apparaten als Bedrijfseigendom labelen door te geven een lijst met hardware-id's (IMEI- of serienummers).

Zie voor meer informatie [apparaten met IMEI-nummer en iOS-serienummer labelen](predeclare-devices-with-hardware-id.md). Wanneer u met die taak bent klaar, terug naar deze pagina om door te gaan met de volgende stap.

## <a name="export-the-profile-to-deploy-to-ios-devices"></a>Het profiel exporteren voor implementatie op iOS-apparaten

1.  Ga in de Configuration Manager-console naar **activa en naleving** > **overzicht** > **alle apparaten in Bedrijfseigendom** > **iOS** > **Inschrijvingsprofielen**.

2.  Selecteer een inschrijvingsprofiel implementeren op mobiele apparaten en klikt u op **exporteren...** .

3.  Kopieer en sla de **profiel-URL** in een bestand dat u kunt bewerken.   

4.  Voor ondersteuning van Apple Configurator 2 moet de profiel-URL 2.0 bewerken. Vervang het volgende gedeelte van de URL:  

    ```  
    https://manage.microsoft.com/EnrollmentServer/Discovery.svc/iOS/ESProxy?id=  

    ```  

     met  

    ```  
    https://appleconfigurator2.manage.microsoft.com/MDMServiceConfig?id=  

    ```

5.  Sla de bewerkte profiel-URL. U wordt gebruikt om het toevoegen van de registratie profiel-URL in Apple Configurator in de [volgende sectie](#step-4-prepare-the-device-with-apple-configurator).  

> [!NOTE]
> De URL van het inschrijvingsprofiel blijft twee weken geldig vanaf de export. Na twee weken moet u een nieuwe URL voor het inschrijven van iOS-apparaten te exporteren.

## <a name="prepare-the-device-with-apple-configurator"></a>Het apparaat voorbereiden met Apple Configurator

Om voor te bereiden voor de inschrijving van iOS-apparaten, moet u elk apparaat aansluit op een Mac-computer en upload het inschrijvingsprofiel naar deze.  

> [!WARNING]  
>  Apple Configurator wordt gewist en herstelt u de apparaten op de fabrieksconfiguraties.  

1.  Open op een Mac-computer **Apple Configurator 2**.  

2.  Klik in de menubalk op **Apple Configurator 2** > **voorkeuren**.  

2.  Selecteer in het deelvenster met voorkeuren **Servers** en klik op het symbool plusteken (+) onder het linkerdeelvenster om de wizard MDM-Server te starten. Klik op **Volgende**.  

3.  Voer de **naam** en **inschrijvings-URL** u opgeslagen [eerdere](#step-3-export-the-profile-to-deploy-to-ios-devices). Klik op **Volgende**.  

   > [!NOTE]
   > Als u een waarschuwing over vereisten voor vertrouwde profielen voor Apple TV ontvangt, kunt u veilig annuleren de **Vertrouwensprofiel** optie door te klikken op de grijze 'X'. Ook waarschuwingen over ankercertificaten kunt u veilig negeren.

   Als u wilt doorgaan, klikt u op **Volgende** totdat de wizard is voltooid.  

4.  Op de **Servers** deelvenster op 'bewerken' naast de nieuwe server-profiel. Zorg ervoor dat de inschrijvings-URL exact overeenkomt met de URL die u eerder hebt ingevoerd. De URL opnieuw in als deze afwijkt en klik op **opslaan**.  

5.  Met een USB-kabel door een iOS-apparaat verbinding te maken met de Mac-computer.  

  > [!WARNING]  
  >  Dit proces stelt apparaten opnieuw op de fabrieksconfiguraties. Voordat u verbinding maakt met het apparaat, het apparaat opnieuw instellen en inschakelen. Als een best practice moet het apparaat vanaf het welkomstscherm op voordat u doorgaat.  

6.  Klik op **voorbereiden**. Op de **iOS-apparaat voorbereiden** deelvenster **handmatige**, en klik vervolgens op **volgende**.  

7.  Op de **inschrijven in MDM-Server** deelvenster, selecteert u de server u hebt gemaakt en klik vervolgens op **volgende**.  

9. Op de **maken van een organisatie** deelvenster, kies de **organisatie** of maak een nieuwe organisatie en klik vervolgens op **volgende**.  

10. Op de **iOS-Configuratieassistent configureren** deelvenster, kiest u de stappen voor het voor de gebruiker en klik vervolgens op **voorbereiden**. Voer als u hierom wordt gevraagd een verificatie uit om de instellingen voor de vertrouwensrelatie bij te werken.  

11. Als u klaar bent, kunt u de USB-kabel loskoppelen.  

Herhaal deze stappen voor alle apparaten die u wilt voorbereiden voor de inschrijving.

## <a name="distribute-devices"></a>Apparaten distribueren

De apparaten zijn nu gereed voor bedrijfsinschrijving. Schakel de apparaten uit en distribueer ze naar gebruikers. Wanneer het apparaat is ingeschakeld, Configuratieassistent start en de gebruiker gevraagd om hun werk of school-account om te schrijven.
