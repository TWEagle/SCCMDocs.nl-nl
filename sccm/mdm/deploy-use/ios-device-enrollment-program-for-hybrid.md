---
title: IOS-apparaten met Device Enrollment Program (DEP) - Configuration Manager inschrijven | Microsoft Docs
description: Schakel iOS Device Enrollment Program (DEP)-inschrijving voor hybride implementaties in Configuration Manager met Intune.
ms.custom: na
ms.date: 09/22/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: configmgr-hybrid
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 78d44adc-9b1c-4bc6-b72d-e93873916ea6
caps.latest.revision: "9"
author: mtillman
ms.author: mtillman
manager: angrobe
ms.openlocfilehash: f34f7527c14e1be6229212bfb2d8fd022ee6defe
ms.sourcegitcommit: 8faf42135a8dc9c384407e64f3f8ba204fb15847
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 09/28/2017
---
# <a name="ios-device-enrollment-program-dep-enrollment-for-hybrid-deployments-with-configuration-manager"></a>inschrijving van iOS-Device Enrollment Program (DEP) voor hybride implementaties met Configuration Manager

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*

Bedrijven kunnen iOS-apparaten via Apples apparaatinschrijvingsprogramma kopen en vervolgens worden beheerd met Microsoft Intune. Bedrijven die iOS-apparaten van het bedrijf willen beheren met het DEP (Device Enrollment Program) van Apple, moeten de stappen met Apple uitvoeren om deel te nemen aan het programma en apparaten via dat programma te verkrijgen. Details van dit proces kunt u vinden op:  [https://deploy.apple.com](https://deploy.apple.com). Voordelen van het programma zijn onder andere handsfree instellen, dus zonder dat elk apparaat via een USB-verbinding op een computer hoeft te worden aangesloten.  

 Voordat u iOS-apparaten van het bedrijf met DEP kunt registreren, hebt u een DEP-token van Apple nodig. Dit token kan Intune informatie synchroniseren over van uw bedrijf die aan DEP deelnemen-apparaten. Ook kunt u Intune Hiermee inschrijvingsprofielen naar Apple uploaden en apparaten toewijzen aan die profielen.  

## <a name="apple-dep-enrollment-for-ios-devices"></a>Apple DEP-inschrijving voor iOS-apparaten  
 De volgende procedures beschrijven het opgeven van iOS-apparaten die zijn aangeschaft via Apple DEP als Intune-beheerde apparaten in Bedrijfseigendom. Wanneer de eerste gebruiker-bevoegdheden-up maken van het apparaat worden ontvangen van het DEP-management-profiel en de Configuratieassistent en brengt deze onder beheer.  

##  <a name="enable-dep-enrollment-in-configuration-manager-with-intune"></a>DEP-inschrijving in Configuration Manager met Intune inschakelen  

1.  **iOS-apparaten gaan beheren met Configuration Manager**   
    Voordat u iOS-Device Enrollment Program (DEP)-apparaten inschrijven kunt, moet u de stappen voor het uitvoeren [hybride mobile device management instellen](../../mdm/deploy-use/setup-hybrid-mdm.md) inclusief [stappen voor de ondersteuning van iOS-inschrijving](../deploy-use/enroll-hybrid-ios-mac.md).
2.  **Een DEP-tokenaanvraag maken**   
    In de Configuration Manager-console in de **beheer** werkruimte Vouw **Hiërarchieconfiguratie**, vouw **Cloudservices**, en klik op **Microsoft Intune-abonnementen**. Klik op het tabblad **Start** op **DEP-tokenaanvraag maken** , klik op **Bladeren** om de downloadlocatie voor de DEP-tokenaanvraag op te geven en klik op **Downloaden**. Sla het PEM-bestand voor de DEP-tokenaanvraag lokaal op. Het PEM-bestand wordt gebruikt om een vertrouwd token (.p7m) bij de Apple Device Enrollment Program-portal aan te vragen.  
3.  **Een DEP-token verkrijgen**   
    Ga naar de [Device Enrollment Program-portal](https://deploy.apple.com) (https://deploy.apple.com) en meld u aan met de Apple-id van uw bedrijf. Deze Apple-id moet later ook worden gebruikt om uw DEP-token te verlengen.  
    1.  In de [Device Enrollment Program-portal](https://deploy.apple.com)naar **Device Enrollment Program** > **Servers beheren**en klik op **MDM-server toevoegen**.  
    ![Schermopname van de MDM-server toevoegen in de portal Device Enrollment Program](../media/enrollment-program-token-add-server.png)
    2.  Voer de **MDM-servernaam**en klik op **Volgende**. De servernaam is voor eigen referentie en dient om de MDM-server te identificeren. Het is niet de naam of URL van de Intune of Configuration Manager-server.  
    3.  De **toevoegen < ServerName\>**  dialoogvenster wordt geopend. Klik op **Bestand kiezen** upload het .pem-bestand dat u in de vorige stap hebt gemaakt en klik vervolgens op **volgende**.  
    4.  De **toevoegen < ServerName\>**  in het dialoogvenster wordt weergegeven een **uw Servertoken** koppeling. Download het servertokenbestand (.p7m) naar uw computer en klik op **Gereed**.  

     Dit certificaatbestand (.p7m) wordt gebruikt om een vertrouwensrelatie tussen Intune en de DEP-servers van Apple tot stand te brengen.  
4.  **Het DEP-token toevoegen aan Configuration Manager**   
    In de Configuration Manager-console in de **beheer** werkruimte Vouw **Hiërarchieconfiguratie** en klik op **Microsoft Intune-abonnementen**. Klik op het tabblad **Start** op **Platforms configureren** en klik op **iOS**. Selecteer **DEP inschakelen**, blader naar het certificaatbestand (.p7m), klik op **Openen**, klik op **Uploaden**en klik vervolgens op **OK**.  

## <a name="add-a-corporate-device-enrollment-policy"></a>Een inschrijvingsbeleid voor Bedrijfsapparaten toevoegen  

1. In de Configuration Manager-console in de **activa en naleving** werkruimte Vouw **overzicht**, vouw **alle apparaten in Bedrijfseigendom**, vouw **iOS**, en klik op **Inschrijvingsprofielen**. Klik op het tabblad **Start** op **Profiel maken** om de wizard Profiel maken te openen. Configureer de instellingen op de volgende pagina's:  
2. On the **Algemeen** de volgende informatie op en klik op **Volgende**.  
  -   **Naam** : naam van het inschrijvingsprofiel voor apparaten. (niet zichtbaar voor gebruikers)  
  -   **Beschrijving** -beschrijving van het inschrijvingsprofiel voor apparaten. (niet zichtbaar voor gebruikers)  
  -   **Gebruikersaffiniteit** : hiermee wordt bepaald hoe apparaten worden ingeschreven. Zie [gebruikersaffiniteit voor hybride beheerde apparaten in Configuration Manager](../../mdm/deploy-use/user-affinity-for-hybrid-managed-devices.md).  

      -  **Vragen om gebruikersaffiniteit**: Het apparaat moet aan een gebruiker worden gekoppeld tijdens de eerste configuratie en dan toegang tot bedrijfsgegevens en e-mailadres als die gebruiker is toegestaan.  Gebruikersaffiniteit moet worden geconfigureerd voor DEP-beheerde apparaten die eigendom zijn van gebruikers en de bedrijfsportal moeten gebruiken (om apps te installeren).  
      > [!NOTE]
      > DEP gebruikersaffiniteit vereist ADFS WS-Trust 1.3 gebruikersnaam/Mixed-eindpunt om aan te vragen gebruikerstoken worden ingeschakeld.

      -   **Geen relatie met gebruiker**: Het apparaat is niet gekoppeld aan een gebruiker. Gebruik deze relatie voor apparaten waarmee taken worden uitgevoerd zonder toegang tot lokale gebruikersgegevens. Apps die een gebruikersrelatie vereisen, werken niet.  
    ![Schermopname van het DEP-profielnaam, beschrijving en Gebruikersaffiniteit vragen](../media/dep-general.png)

3. Op de **apparaatinstellingen registratie programma** pagina, geef de volgende informatie en klik vervolgens op **volgende**.  
    -   **Afdeling**: Deze informatie wordt weergegeven wanneer gebruikers tikken op 'Over configuratie' tijdens de activering.  
    -   **Telefoonnummer voor ondersteuning**: Weergegeven wanneer de gebruiker de **hulp nodig** knop tijdens de activering.
       ![Schermopname van het DEP-profiel op iOS-apparaten toewijzen](../media/dep-settings.png)

    - **Voorbereidingsmodus**: Deze status wordt ingesteld tijdens de activering en kan niet worden gewijzigd zonder de factory opnieuw instellen van het apparaat:  
        -   **Zonder supervisie** -beperkte beheermogelijkheden  
        -   **Onder supervisie** - kunnen meer beheeropties en Activeringsvergrendeling standaard uitgeschakeld  
    - **Inschrijvingsprofiel vergrendelen voor apparaat**: Deze status wordt ingesteld tijdens de activering en kan niet worden gewijzigd zonder de fabrieksinstellingen terug te zetten.  
      -   **Schakel** -Hiermee kan het beheerprofiel worden verwijderd uit de **instellingen** menu  
      -   **Schakel** -(vereist **Voorbereidingsmodus** = **onder supervisie**) iOS-instellingen die u verwijderen van het beheerprofiel kunnen zou wordt uitgeschakeld  

4.  Op de pagina **Configuratieassistent** configureert u de instellingen waarmee de iOS-configuratieassistent wordt aangepast die wordt gestart wanneer het apparaat voor het eerst wordt ingeschakeld. Klik vervolgens op **Volgende**. Deze instellingen omvatten:  
  -   **Wachtwoordcode** - vragen om de wachtwoordcode tijdens de activering. Vereis altijd een wachtwoordcode tenzij het apparaat wordt beveiligd of beheerd in een andere manier (dat wil zeggen kioskmodus waarmee het apparaat aan een app) toegang hebben.  
  -   **Locatieservices** - indien ingeschakeld, wordt Configuratieassistent gevraagd voor de service tijdens de activering  
  -   **Herstellen** - indien ingeschakeld, wordt Configuratieassistent gevraagd voor iCloud-back-up tijdens de activering  
  -   **Apple-ID** -een Apple-ID is vereist voor het downloaden van iOS-App Store-apps, waaronder die zijn geïnstalleerd door Intune. Bij inschakeling wordt iOS gebruikers voor een Apple-ID gevraagd wanneer Intune probeert te installeren van een app zonder ID.  
  -   **Voorwaarden en bepalingen** -indien ingeschakeld, wordt Configuratieassistent gevraagd gebruikers de voorwaarden bepalingen van Apple accepteren tijdens de activering  
  -   **Touch ID** - indien ingeschakeld, wordt Configuratieassistent gevraagd voor deze service tijdens de activering
  -   **Apple Pay** - indien ingeschakeld, wordt Configuratieassistent gevraagd voor deze service tijdens de activering
  -   **Zoomen** - indien ingeschakeld, wordt Configuratieassistent gevraagd voor deze service tijdens de activering
  -   **Siri** - indien ingeschakeld, wordt Configuratieassistent gevraagd voor deze service tijdens de activering  
  -   **Diagnostische gegevens verzenden naar Apple** - indien ingeschakeld, wordt Configuratieassistent gevraagd voor deze service tijdens de activering  
    ![Schermopname van het DEP-profiel op iOS-apparaten toewijzen](../media/dep-setup-assistant.png)
5.  Op de **aanvullend beheer** pagina, of een USB-verbinding kan worden gebruikt voor extra instellingen opgeven. Wanneer u selecteert **-certificaat vereist**, moet u een Apple Configurator-beheercertificaat voor dit profiel importeren.  Ingesteld op **Disallow** om te voorkomen dat synchroniseert bestanden met iTunes of beheer via Apple Configurator. Microsoft raadt u ingesteld op **Disallow**, een eventuele verdere configuratie vanuit Apple Configurator te exporteren en vervolgens implementeren als een aangepast iOS-configuratieprofiel, plaats deze instelling gebruiken voor handmatige implementatie met of zonder een certificaat.  

  -   **Niet toestaan van** -voorkomt u dat het apparaat communiceert via USB (wordt koppeling uitgeschakeld)  
  -   **Toestaan dat** -apparaat kan communiceren via USB-verbinding met een PC of Mac  
  -   **Certificaat vereisen**-Hiermee wordt een koppeling met een Mac met een certificaat dat is geïmporteerd in het Registratieprofiel  

## <a name="assign-dep-devices-for-management"></a>DEP-apparaten toewijzen voor beheer

1. Ga naar de [Device Enrollment Program-portal](https://deploy.apple.com) (https://deploy.apple.com) en meld u aan met de Apple-id van uw bedrijf.
2. Ga naar **Implementatieprogramma** > **Device Enrollment Program** > **Apparaten beheren**. Geef een manier op voor **Apparaten kiezen**, geef apparaatgegevens op en geef apparaatdetails op aan de hand van het **Serienummer**van het apparaat, het **Bestelnummer**of **door een CSV-bestand te uploaden**. Selecteer vervolgens **toewijzen aan Server** en selecteer de <*ServerName*> die u in stap 3 hebt opgegeven, en klik vervolgens op **OK**.  
![Schermopname van Apple Device Enrollment Program-portal toevoegen van apparaten](../media/enrollment-program-token-specify-serial.png)

3.  **Met DEP-beheerde apparaten synchroniseren**   
    In de **activa en naleving** werkruimte, gaat u naar **alle apparaten in Bedrijfseigendom** > **Predeclared apparaten**. Klik op het tabblad **Start** op **DEP-synchronisatie**. Er wordt een synchronisatieaanvraag verzonden naar Apple. Nadat de synchronisatie is voltooid, worden de met DEP beheerde apparaten weergegeven.

    > [!NOTE]
    > In de hybride-configuratie handmatig het DEP-synchronisatie opnieuw wordt geactiveerd door te klikken op **DEP-synchronisatie** in de Configuration Manager-console.

4.  **DEP-profiel toewijzen**<br>In de **activa en naleving** werkruimte, gaat u naar **alle apparaten in Bedrijfseigendom** > **iOS** > **Inschrijvingsprofielen**. Selecteer het DEP-inschrijvingsprofiel en klikt u op de **Start** tabblad **toewijzen aan apparaten**. Selecteer de apparaten die dit inschrijvingsprofiel gebruiken, klikt u op **toevoegen**, en klik vervolgens op **OK**.   
     ![Schermopname van het DEP-profiel op iOS-apparaten toewijzen](../media/dep-assign-profile.png)

## <a name="distribute-devices-to-users"></a>Apparaten aan gebruikers distribueren
U kunt de apparaten in bedrijfseigendom nu uitreiken aan gebruikers. Bij **Inschrijvingsstatus** voor beheerde apparaten wordt **Geen contact gemaakt** weergegeven totdat het apparaat wordt ingeschakeld, en Configuratieassistent wordt uitgevoerd om het apparaat te registreren. Wanneer een iOS-apparaat wordt ingeschakeld, zal het worden ingeschreven voor beheer door Intune.
