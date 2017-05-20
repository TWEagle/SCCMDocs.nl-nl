---
title: IOS-apparaten met Device Enrollment Program (DEP) - Configuration Manager inschrijven | Microsoft-documenten
description: IOS-inschrijving voor hybride implementatie in Configuration Manager met Intune Device Enrollment Program (DEP) inschakelen.
ms.custom: na
ms.date: 03/05/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-hybrid
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 78d44adc-9b1c-4bc6-b72d-e93873916ea6
caps.latest.revision: 9
author: mtillman
ms.author: mtillman
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: ae60eb25383f4bd07faaa1265185a471ee79b1e9
ms.openlocfilehash: 5b5eadd7b4026eae59acceaef43cdacd7a33d3ac
ms.contentlocale: nl-nl
ms.lasthandoff: 05/17/2017

---
# <a name="ios-device-enrollment-program-dep-enrollment-for-hybrid-deployments-with-configuration-manager"></a>inschrijving van iOS-Device Enrollment Program (DEP) voor hybride implementaties met Configuration Manager

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*

Bedrijven kunnen iOS-apparaten via Apples apparaatinschrijvingsprogramma koop en beheer deze met Microsoft Intune. Bedrijven die iOS-apparaten van het bedrijf willen beheren met het DEP (Device Enrollment Program) van Apple, moeten de stappen met Apple uitvoeren om deel te nemen aan het programma en apparaten via dat programma te verkrijgen. Details van dit proces kunt u vinden op:  [https://deploy.apple.com](https://deploy.apple.com). Voordelen van het programma zijn onder andere handsfree instellen, dus zonder dat elk apparaat via een USB-verbinding op een computer hoeft te worden aangesloten.  

 Voordat u iOS-apparaten van het bedrijf met DEP kunt registreren, hebt u een DEP-token van Apple nodig. Kan Intune met de informatie synchroniseren over apparaten die aan DEP deelnemen van uw bedrijf die dit token. U kunt ook Intune Hiermee inschrijvingsprofielen naar Apple uploaden en apparaten toewijzen aan die profielen.  

## <a name="apple-dep-enrollment-for-ios-devices"></a>Apple DEP-inschrijving voor iOS-apparaten  
 De volgende procedures beschrijven het iOS-apparaten die zijn aangeschaft via Apples DEP als Intune-beheerde apparaten van bedrijf opgeven. Wanneer de gebruiker eerst bevoegdheden-up maken van het apparaat worden ontvangen van het DEP-beheerprofiel en de Configuratieassistent en ervoor te zorgen onder beheer.  

###  <a name="enable-dep-enrollment-in-configuration-manager-with-intune"></a>DEP-inschrijving in Configuration Manager met Intune inschakelen  

1.  **iOS-apparaten gaan beheren met Configuration Manager**   
    Voordat u iOS-Device Enrollment Program (DEP)-apparaten inschrijven kunt, moet u stappen voltooien [hybride mobile device management instellen](../../mdm/deploy-use/setup-hybrid-mdm.md) inclusief [stappen voor het ondersteunen van iOS-inschrijving](../deploy-use/enroll-hybrid-ios-mac.md).

2.  **Een DEP-tokenaanvraag maken**   
    In de Configuration Manager-console in de **beheer** werkruimte Vouw **Hiërarchieconfiguratie**, vouw **Cloudservices**, en klikt u op **Microsoft Intune-abonnementen**. Klik op het tabblad **Start** op **DEP-tokenaanvraag maken** , klik op **Bladeren** om de downloadlocatie voor de DEP-tokenaanvraag op te geven en klik op **Downloaden**. Sla het PEM-bestand voor de DEP-tokenaanvraag lokaal op. Het PEM-bestand wordt gebruikt om een vertrouwd token (.p7m) bij de Apple Device Enrollment Program-portal aan te vragen.  

3.  **Een DEP-token verkrijgen**   
    Ga naar de [Device Enrollment Program-portal](https://deploy.apple.com) (https://deploy.apple.com) en meld u aan met de Apple-id van uw bedrijf. Deze Apple-id moet later ook worden gebruikt om uw DEP-token te verlengen.  

    1.  In de [Device Enrollment Program-portal](https://deploy.apple.com)naar **Device Enrollment Program** > **Servers beheren**en klik op **MDM-server toevoegen**.  

    2.  Voer de **MDM-servernaam**en klik op **Volgende**. De servernaam is voor eigen referentie en dient om de MDM-server te identificeren. Het is niet de naam of URL van de Intune of Configuration Manager-server.  

    3.  De **toevoegen < ServerName\>**  in het dialoogvenster wordt geopend. Klik op **Bestand kiezen** upload het .pem-bestand dat u in de vorige stap hebt gemaakt en klik vervolgens op **volgende**.  

    4.  De **toevoegen < ServerName\>**  in het dialoogvenster wordt weergegeven een **uw Servertoken** koppeling. Download het servertokenbestand (.p7m) naar uw computer en klik op **Gereed**.  

     Dit certificaatbestand (.p7m) wordt gebruikt om een vertrouwensrelatie tussen Intune en de DEP-servers van Apple tot stand te brengen.  

4.  **Het DEP-token toevoegen aan Configuration Manager**   
    In de Configuration Manager-console in de **beheer** werkruimte Vouw **Hiërarchieconfiguratie** en klikt u op **Microsoft Intune-abonnementen**. Klik op het tabblad **Start** op **Platforms configureren** en klik op **iOS**. Selecteer **DEP inschakelen**, blader naar het certificaatbestand (.p7m), klik op **Openen**, klik op **Uploaden** en klik vervolgens op **OK**.  

#### <a name="set-up-enrollment-for-apple-device-enrollment-program-dep-ios-devices"></a>Inschrijving voor iOS-apparaten met Apple Device Enrollment Program (DEP) instellen  

1.  **Beleid voor inschrijving van Bedrijfsapparaten toevoegen**   
    In de Configuration Manager-console in de **activa en naleving** werkruimte Vouw **overzicht**, vouw **alle apparaten in Bedrijfseigendom**, vouw **iOS**, en klikt u op **Inschrijvingsprofielen**. Klik op het tabblad **Start** op **Profiel maken** om de wizard Profiel maken te openen. Configureer de instellingen op de volgende pagina's:  

    1.  On the **Algemeen** de volgende informatie op en klik op **Volgende**.  

        -   **Naam** : naam van het inschrijvingsprofiel voor apparaten. (niet zichtbaar voor gebruikers)  

        -   **Beschrijving** -beschrijving van het inschrijvingsprofiel voor apparaten. (niet zichtbaar voor gebruikers)  

        -   **Gebruikersaffiniteit** : hiermee wordt bepaald hoe apparaten worden ingeschreven. Zie [affiniteit tussen gebruikers en hybride beheerde apparaten in Configuration Manager](../../mdm/deploy-use/user-affinity-for-hybrid-managed-devices.md).  

            -   **Vragen om gebruikersaffiniteit**: Het apparaat tijdens de eerste installatie moet zijn gekoppeld aan een gebruiker en kan vervolgens worden toegestaan voor toegang tot bedrijfsgegevens en e-mailadres als die gebruiker.  Gebruikersaffiniteit moet worden geconfigureerd voor DEP-beheerde apparaten die eigendom zijn van gebruikers en de bedrijfsportal moeten gebruiken (om apps te installeren).  

            > [!NOTE]
            > DEP affiniteit tussen gebruikers en vereist ADFS WS-Trust 1.3 gebruikersnaam/gemengd eindpunt gebruikerstoken aanvragen zijn ingeschakeld.

            -   **Geen affiniteit tussen gebruikers en**: Het apparaat is niet gekoppeld aan een gebruiker. Gebruik deze relatie voor apparaten waarmee taken worden uitgevoerd zonder toegang tot lokale gebruikersgegevens. Apps die een gebruikersrelatie vereisen, werken niet.  
             ![Schermopname van het DEP-profielnaam, beschrijving en affiniteit tussen gebruikers en vragen](../media/dep-general.png)

    2.  Op de **instellingen** pagina en klik vervolgens op de volgende informatie opgeven **volgende**.  

        -   **Afdeling**: Deze informatie wordt weergegeven wanneer gebruikers Tik op "Over configuratie" tijdens de activering.  

        -   **Telefoonnummer voor ondersteuning**: Weergegeven wanneer de gebruiker de **hulp nodig** knop tijdens de activering.
       ![Schermopname van het DEP-profiel op iOS-apparaten toewijzen](../media/dep-settings.png)

        -   **Voorbereiding modus**: Deze status is ingesteld tijdens de activering en kan niet worden gewijzigd zonder de factory opnieuw instellen van het apparaat:  

            -   **Werkende** -beperkt mogelijkheden voor Computerbeheer  

            -   **Onder supervisie** - meer beheeropties en Activeringsvergrendeling uitschakelt standaard  

        -   **Vergrendel inschrijvingsprofiel op apparaat**: Deze status is ingesteld tijdens de activering en kan niet worden gewijzigd zonder een terugzetten op fabrieksinstellingen.  

            -   **Schakel** -Hiermee kunt u het profiel management worden verwijderd uit de **instellingen** menu  

            -   **Schakel** -(vereist **voorbereiding modus** = **Supervised**) schakelt iOS-instellingen, waardoor het verwijderen van het profiel voor het beheren  

    3.  Op de pagina **Configuratieassistent** configureert u de instellingen waarmee de iOS-configuratieassistent wordt aangepast die wordt gestart wanneer het apparaat voor het eerst wordt ingeschakeld. Klik vervolgens op **Volgende**. Deze instellingen omvatten:  
        -   **Wachtwoordcode** - vragen om wachtwoordcode tijdens de activering. Altijd een wachtwoordcode vereist tenzij het apparaat wordt beveiligd of beheerd in een andere wijze (dat wil zeggen kioskmodus die het apparaat, tot één app beperkt) toegang hebben.  
        -   **Locatieservices** - als ingeschakeld, Configuratieassistent vraagt om de service tijdens de activering  
        -   **Terugzetten** - als ingeschakeld, Configuratieassistent vraagt om back-up iCloud tijdens de activering  
        -   **Apple-ID** -een Apple-ID is vereist voor het downloaden van de iOS App Store-apps, zoals die zijn geïnstalleerd door Intune. Bij inschakeling wordt iOS gebruikers voor een Apple-ID gevraagd wanneer Intune probeert een app zonder een id te installeren  
        -   **Voorwaarden en bepalingen** -bij inschakeling Configuratieassistent gebruikers wordt gevraagd Apples voorwaarden bepalingen te accepteren tijdens de activering  
        -   **Touch ID** - als ingeschakeld, Configuratieassistent vraagt om deze service tijdens de activering
        -   **Apple betalen** - als ingeschakeld, Configuratieassistent vraagt om deze service tijdens de activering
        -   **Zoom** - als ingeschakeld, Configuratieassistent vraagt om deze service tijdens de activering
        -   **Siri** - als ingeschakeld, Configuratieassistent vraagt om deze service tijdens de activering  
        -   **Diagnostische gegevens verzenden naar Apple** - als ingeschakeld, Configuratieassistent vraagt om deze service tijdens de activering  
        ![Schermopname van het DEP-profiel op iOS-apparaten toewijzen](../media/dep-setup-assistant.png)

    4.  Op de **latere** pagina, of een USB-verbinding kan worden gebruikt voor extra beheerinstellingen opgeven. Wanneer u selecteert **-certificaat vereist**, moet u een Apple Configurator-beheercertificaat voor dit profiel importeren.  Ingesteld op **toestaan** om te voorkomen dat gesynchroniseerd bestanden met iTunes of beheer via Apple Configurator. Microsoft raadt u ingesteld op **toestaan**, er nog verdere configuratie exporteren uit de Apple Configurator en vervolgens implementeren als een aangepast iOS-configuratieprofiel plaats van deze instelling voor handmatige implementatie met of zonder een certificaat gebruiken.  

        -   **Niet toestaan van** -voorkomt dat het apparaat communiceren via USB (schakelt koppelen)  

        -   **Toestaan dat** -apparaat kan communiceren via USB-verbinding met een PC of Mac  

        -   **Certificaat**-kunt koppelen aan een Mac met een certificaat importeren in het Registratieprofiel  

2.  **DEP-apparaten toewijzen voor beheer**   
    Ga naar de [Device Enrollment Program-portal](https://deploy.apple.com) (https://deploy.apple.com) en meld u aan met de Apple-id van uw bedrijf. Ga naar **Implementatieprogramma** > **Device Enrollment Program** > **Apparaten beheren**. Geef een manier op voor **Apparaten kiezen**, geef apparaatgegevens op en geef apparaatdetails op aan de hand van het **Serienummer**van het apparaat, het **Bestelnummer**of **door een CSV-bestand te uploaden**. Selecteer vervolgens **toewijzen aan Server** en selecteer de <*ServerName*> die u in stap 3 hebt opgegeven en klik vervolgens op **OK**.  

3.  **Met DEP-beheerde apparaten synchroniseren**   
    In de **activa en naleving** werkruimte, Ga naar **alle apparaten in Bedrijfseigendom** > **Predeclared apparaten**. Klik op het tabblad **Start** op **DEP-synchronisatie**. Er wordt een synchronisatieaanvraag verzonden naar Apple. Nadat de synchronisatie is voltooid, worden de met DEP beheerde apparaten weergegeven.

4.  **DEP-profiel toewijzen**<br>In de **activa en naleving** werkruimte, Ga naar **alle apparaten in Bedrijfseigendom** > **iOS** > **Inschrijvingsprofielen**. Selecteer het profiel voor DEP-inschrijving en klik in de **Start** tabblad **toewijzen aan apparaten**. Selecteer de apparaten die u wilt dit inschrijvingsprofiel gebruiken, klikt u op **toevoegen**, en klik vervolgens op **OK**.   
     ![Schermopname van het DEP-profiel op iOS-apparaten toewijzen](../media/dep-assign-profile.png)

5.  **Apparaten aan gebruikers distribueren**   
    U kunt de apparaten in bedrijfseigendom nu uitreiken aan gebruikers. Bij **Inschrijvingsstatus** voor beheerde apparaten wordt **Geen contact gemaakt** weergegeven totdat het apparaat wordt ingeschakeld, en Configuratieassistent wordt uitgevoerd om het apparaat te registreren. Wanneer een iOS-apparaat wordt ingeschakeld, zal het worden ingeschreven voor beheer door Intune.

