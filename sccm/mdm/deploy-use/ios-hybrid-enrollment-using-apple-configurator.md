---
title: IOS-apparaten Apple Configurator - Configuration Manager inschrijven | Microsoft-documenten
descriptions: Pre-enroll iOS devices by using Apple Configurator with Configuration Manager.
ms.custom: na
ms.date: 03/05/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-hybrid
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 61a19d95-83ff-4ad8-9a67-f304d2ba54f2
caps.latest.revision: 5
author: mtillman
ms.author: mtillman
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 2c723fe7137a95df271c3612c88805efd8fb9a77
ms.openlocfilehash: f8242b4b454622388f45c34ba71c4148c87c27b7
ms.contentlocale: nl-nl
ms.lasthandoff: 05/17/2017


---
# <a name="ios-hybrid-enrollment-using-apple-configurator-with-configuration-manager"></a>inschrijving van iOS hybride met Apple Configurator met Configuration Manager

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*

Bedrijven die iOS-apparaten kopen moet worden gebruikt door werknemers kunnen beheren met Microsoft Intune. Om voor te bereiden zakelijke iOS-apparaten voor inschrijving, een Registratieprofiel te configureren in de Configuration Manager-console en vervolgens exporteren de profiel-URL voor gebruik door Apple Configurator. U moet het iOS-apparaat voor de inschrijving van voorbereiden door verbinding te maken met een Mac-computer met een USB-kabel en instellen met behulp van Apple Configurator. Apple Configurator fabrieksinstellingen worden hersteld van het apparaat en het inschrijvingsprofiel toegevoegd zodat het apparaat kan worden ingeschreven als de gebruiker eerst het bevoegdheden van de Configuratieassistent proces.

De volgende procedure wordt aanbevolen voor specifieke iOS-apparaten met een enkele gebruiker die het apparaat toegang tot bedrijfse-mail en andere bedrijfsresources zoals apps en -datum gebruikt.  

## <a name="prerequisites"></a>Vereisten  

-   Fysieke toegang tot iOS-apparaten  

-   Serienummers - [hoe u een iOS-serienummer](https://support.apple.com/en-us/HT204308)  

-   Mac-computer met [Apple Configurator 2.0](http://go.microsoft.com/fwlink/?LinkId=518017)  

-   USB-kabels voor het verbinden van apparaten op uw Mac-computer  

## <a name="step-1-add-a-corporate-owned-device-enrollment-profile"></a>Stap 1: Toevoegen van een inschrijvingsprofiel voor apparaten in Bedrijfseigendom beheren

1.  Ga in de Configuration Manager-console naar **activa en naleving** > **overzicht** > **alle apparaten in Bedrijfseigendom** > **iOS** > **Inschrijvingsprofielen**. Klik op **-profiel maken** om de wizard profiel maken te openen. Configureer de instellingen op de volgende pagina's:  

2.  Geef op de pagina **Algemeen** de volgende gegevens op:  

    -   **Naam** (niet zichtbaar voor gebruikers)  

    -   **Beschrijving** (niet zichtbaar voor gebruikers)  

    -   **Gebruikersaffiniteit** : hiermee wordt bepaald hoe apparaten worden ingeschreven. Gebruik voor de meeste Configuratieassistent-scenario's **Vragen voor relatie met gebruiker**.  

        -   **Vragen om gebruikersaffiniteit**: Het apparaat tijdens de eerste installatie moet zijn gekoppeld aan een gebruiker en kan vervolgens worden toegestaan voor toegang tot bedrijfsgegevens en e-mailadres als die gebruiker.  

        -   **Geen affiniteit tussen gebruikers en**: Het apparaat is niet gekoppeld aan een gebruiker. Gebruik deze relatie voor apparaten waarmee taken worden uitgevoerd zonder toegang tot lokale gebruikersgegevens. Apps die een gebruikersrelatie vereisen, werken niet.

    Klik op **Volgende** om verder te gaan.  

3.  Op de **Device Enrollment Program** pagina, laat de **configureren Device Enrollment Program-instellingen voor dit profiel** selectievakje uitgeschakeld, en klikt u op **volgende**.  

4.  Bekijk het overzicht en klik vervolgens op **volgende** voor het maken van het inschrijvingsprofiel. Klik op **Sluiten** om de wizard te voltooien. U kunt nu om toe te voegen IMEI-nummers of serienummers voor de apparaten die u wilt inschrijven.  

## <a name="step-2-predeclare-devices-to-enroll-with-setup-assistant"></a>Stap 2: Apparaten voor inschrijving met Configuratieassistent predeclare

In deze stap kunt u apparaten als Bedrijfseigendom predeclare door te geven een lijst van hardware-id's (IMEI-nummer of serienummers).

Zie voor meer informatie [Predeclare apparaten met IMEI-nummer en iOS-serienummer](predeclare-devices-with-hardware-id.md). Wanneer u met die taak bent klaar, terug naar deze pagina om door te gaan met de volgende stap.

## <a name="step-3-export-the-profile-to-deploy-to-ios-devices"></a>Stap 3: Exporteren van het profiel dat u wilt implementeren op iOS-apparaten

1.  Ga in de Configuration Manager-console naar **activa en naleving** > **overzicht** > **alle apparaten in Bedrijfseigendom** > **iOS** > **Inschrijvingsprofielen**.

2.  Selecteer het Registratieprofiel te implementeren op mobiele apparaten en op **exporteren...** .

3.  Kopieer en sla de **profiel-URL** in een bestand dat u kunt bewerken.   

4.  Voor ondersteuning van Apple Configurator 2, moet de 2.0 profiel-URL worden bewerkt. Vervang in het volgende gedeelte van de URL:  

    ```  
    https://manage.microsoft.com/EnrollmentServer/Discovery.svc/iOS/ESProxy?id=  

    ```  

     met  

    ```  
    https://appleconfigurator2.manage.microsoft.com/MDMServiceConfig?id=  

    ```

5.  Slaat de bewerkte profiel-URL. U kunt het toevoegen van de inschrijving profiel-URL in Apple Configurator in de [volgende sectie](#step-4-prepare-the-device-with-apple-configurator).  

> [!NOTE]
> De URL van het inschrijvingsprofiel blijft twee weken geldig vanaf de export. Na twee weken, moet u een nieuwe URL voor het inschrijven van iOS-apparaten te exporteren.

## <a name="step-4-prepare-the-device-with-apple-configurator"></a>Stap 4: Het apparaat voorbereiden met Apple Configurator

Om voor te bereiden voor de inschrijving van iOS-apparaten, elk apparaat aansluit op een Mac-computer en het Registratieprofiel te uploaden.  

> [!WARNING]  
>  Apple Configurator wordt gewist en stelt het apparaten op de fabrieksconfiguraties.  

1.  Open op een Mac-computer **Apple Configurator 2**.  

2.  Klik in de menubalk op **Apple Configurator 2** > **voorkeuren**.  

2.  Selecteer in het deelvenster Voorkeuren **Servers** en klik op het symbool "+" onder het linkerdeelvenster om de wizard MDM-Server te starten. Klik op **Volgende**.  

3.  Voer de **naam** en **inschrijvings-URL** u opgeslagen [eerdere](#step-3-export-the-profile-to-deploy-to-ios-devices). Klik op **Volgende**.  

   > [!NOTE]
   > Als u een waarschuwing over de vereisten voor het profiel voor Apple tv-vertrouwensrelatie ontvangt, kunt u veilig annuleren de **vertrouwensrelatie profiel** optie door te klikken op de grijs "X". Ook waarschuwingen over ankercertificaten kunt u veilig negeren.

   Als u wilt doorgaan, klikt u op **Volgende** totdat de wizard is voltooid.  

4.  Op de **Servers** deelvenster op "bewerken" naast de nieuwe server-profiel. Zorg ervoor dat de inschrijvings-URL exact overeenkomt met de URL die u eerder hebt ingevoerd. De URL opnieuw in als deze en klikt u op **opslaan**.  

5.  Verbinding met een USB-kabel een iOS-apparaat met de Mac-computer.  

  > [!WARNING]  
  >  Dit proces stelt de apparaten in op de fabrieksconfiguraties. Voordat het apparaat verbindt, het apparaat opnieuw instellen en deze vervolgens inschakelt. Als een best practice moet het apparaat op het scherm Hallo voordat u doorgaat.  

6.  Klik op **voorbereiden**. Op de **voorbereiden iOS-apparaat** venster **handmatig**, en klik vervolgens op **volgende**.  

7.  Op de **inschrijven in MDM-Server** deelvenster, selecteer de server u hebt gemaakt, en klik vervolgens op **volgende**.  

9. Op de **maken van een organisatie** deelvenster Kies de **organisatie** of maak een nieuwe organisatie en klik vervolgens op **volgende**.  

10. Op de **configureert iOS-Configuratieassistent** deelvenster kiest u de stappen om te presenteren aan de gebruiker en klik vervolgens op **voorbereiden**. Voer als u hierom wordt gevraagd een verificatie uit om de instellingen voor de vertrouwensrelatie bij te werken.  

11. Wanneer u klaar bent, kunt u de USB-kabel verbinding verbreken.  

Herhaal deze stappen voor alle apparaten die u wilt voorbereiden om te schrijven.

## <a name="step-5-distribute-devices"></a>Stap 5: Apparaten distribueren

De apparaten zijn nu gereed voor bedrijfsinschrijving. Schakel de apparaten uit en distribueer ze naar gebruikers. Wanneer het apparaat is ingeschakeld, Configuratieassistent start en de gebruiker vragen om hun werk- of schoolaccount-account om te beginnen met inschrijving.

