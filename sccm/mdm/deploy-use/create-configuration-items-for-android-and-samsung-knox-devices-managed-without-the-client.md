---
title: Configuratie-items voor Android en Samsung KNOX Standard-apparaten die worden beheerd door Intune maken | Microsoft-documenten
description: Gebruik de System Center Configuration Manager Android en Samsung KNOX Standard configuratie-item voor het beheren van instellingen voor apparaten.
ms.custom: na
ms.date: 03/27/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-hybrid
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 7b66f3c4-e3bb-4f6a-abd5-55be649ff90d
caps.latest.revision: 17
caps.handback.revision: 0
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 4b9261db93c9bf72c492e3c9be5b30f81835134a
ms.openlocfilehash: c9961c2e9866199571a1b39a7b185cb6bb96f998
ms.contentlocale: nl-nl
ms.lasthandoff: 05/17/2017


---
# <a name="how-to-create-configuration-items-for-android-and-samsung-knox-devices-managed-without-the-system-center-configuration-manager-client"></a>Configuratie-items maken voor Android- en Samsung KNOX-apparaten die worden beheerd zonder de System Center Configuration Manager-client

Gebruik de System Center Configuration Manager **Android en Samsung KNOX** configuratie-item voor het beheren van instellingen voor Android en Samsung KNOX-apparaten die zijn ingeschreven bij Microsoft Intune of beheerde on-premises door Configuration Manager.  

#### <a name="to-create-an-android-and-samsung-knox-configuration-item"></a>Maken van een configuratie-item voor Android en Samsung KNOX  

1. Kies in de Configuration Manager-console **activa en naleving**.  

2. In de **activa en naleving** werkruimte Vouw **compatibiliteitsinstellingen**, en kies vervolgens **configuratie-Items**.  

3. Op de **Start** tabblad, in de **maken** groep, kiest u **configuratie-Item maken**.  

4. Op de **algemeen** pagina van de Wizard Configuratie-Item maken een naam en een optionele beschrijving voor de configuratie-item opgeven.  

5. Onder **Geef het type configuratie-item dat u wilt maken**, kies **Android en Samsung KNOX**.  

6. Kies **categorieën** als u maken en toewijzen van categorieën om te zoeken en filteren van configuratie-items in de Configuration Manager-console.  

7. Op de **ondersteunde Platforms** pagina van de wizard, kiest u de specifieke Android of Samsung KNOX-platformen die het configuratie-item wordt geëvalueerd.  

8. Op de **apparaatinstellingen** pagina van de wizard, kies de instellingsgroep die u wilt configureren. Zie [Android en Samsung KNOX verwijzing configuratie-item instellingen](#BKMK_setref) in dit onderwerp voor meer informatie, en kies vervolgens **volgende**.  

    > [!TIP]  
    >  Als de instelling die u wilt dat niet wordt vermeld, controleert u de **extra instellingen configureren die zich niet in de standaardinstellingsgroepen** vak.  

9. Configureer de instellingen die u nodig hebt op elke pagina-instellingen. Ook kunt u kiezen of u ze herstellen wilt wanneer ze niet compatibel is op apparaten zijn (wanneer dit wordt ondersteund).  

10. U kunt ook de ernst die worden gerapporteerd als is geconstateerd dat een configuratie-item niet-compatibele configureren voor elke instellingsgroep:  

    - **Geen**. Apparaten die niet voldoen aan deze compliantieregel doen geen fouternst voor Configuration Manager-rapporten.  

    - **Informatie**. Apparaten die niet voldoen aan deze compliantieregel fouternst van **informatie** voor Configuration Manager-rapporten.  

    - **Waarschuwing**. Apparaten die niet voldoen aan deze compliantieregel fouternst van **waarschuwing** voor Configuration Manager-rapporten.  

    - **Kritieke**. Apparaten die niet voldoen aan deze compliantieregel fouternst van **kritieke** voor Configuration Manager-rapporten.  

    - **Kritiek met gebeurtenis**. Apparaten die niet voldoen aan deze compliantieregel fouternst van **kritieke** voor Configuration Manager-rapporten. Dit ernstniveau wordt ook vastgelegd als een Windows-gebeurtenis in het logboek voor toepassingsgebeurtenissen.  

11. Op de **Platform toepasbaarheid** pagina van de wizard Controleer alle instellingen die niet compatibel zijn met de ondersteunde platforms die u eerder hebt gekozen. U kunt teruggaan en deze instellingen verwijderen of u kunt doorgaan.  

    > [!TIP]  
    >  Niet-ondersteunde instellingen worden niet beoordeeld op compliantie.  

12. Sluit de wizard af.  

 U kunt het nieuwe configuratie-item weergeven in het knooppunt **Configuratie-items** van de werkruimte **Activa en naleving** .  

## <a name="android-and-samsung-knox-configuration-item-settings-reference"></a>Naslaginformatie voor het configuratie-item voor Android en Samsung KNOX  

### <a name="password"></a>Wachtwoord  
Deze instellingen gelden voor Android- en Samsung KNOX-apparaten.  

|Instelling|Details|  
|-------------|-------------|  
|**Wachtwoordinstellingen vereisen op mobiele apparaten**|Vereist een wachtwoord op ondersteunde apparaten.|  
|**Minimale wachtwoordlengte (tekens)**|Hiermee geeft u de minimale lengte van het wachtwoord.|  
|**Wachtwoordverlooptijd in dagen**|Hiermee geeft u het aantal dagen waarna een wachtwoord moet worden gewijzigd.|  
|**Aantal onthouden wachtwoorden**|Voorkomt dat eerder gebruikte wachtwoorden.|  
|**Aantal mislukte aanmeldingspogingen voordat het apparaat wordt gewist**|Tussen het apparaat als dit aantal mislukken aanmeldingspogingen.|  
|**Niet-actieve tijd voordat het apparaat wordt vergrendeld**|Hiermee geeft u de hoeveelheid tijd voordat het apparaat wordt vergrendeld als deze niet wordt gebruikt.|
|**Wachtwoordkwaliteit**|Hiermee geeft u de vereiste wachtwoordcomplexiteit en of biometrische apparaten kunnen worden gebruikt.|  
|**Smart vergrendelen en andere agents vertrouwensrelatie toestaan**|Hiermee kunt u de functie Smart vergrendeling op Android-compatibele apparaten beheren. Deze mogelijkheid phone kunt u het wachtwoord van het apparaat vergrendelen scherm overslaan als het apparaat zich in een vertrouwde locatie, zoals wanneer deze is verbonden met een specifiek Bluetooth-apparaat of als deze in de buurt bevindt een NFC-tag- of uitschakelen. U kunt deze instelling gebruiken om gebruikers te verhinderen Smart vergrendelen configureren.|
|**Vingerafdruk voor ontgrendelen (KNOX 5.0 +)**|Hiermee kunt het gebruik van een vingerafdruk voor het ontgrendelen van compatibele apparaten.|

### <a name="device"></a>Apparaat   

|Instelling|Details|  
|------------------|-------------|  
|**Nummer inspreken**|Schakelt de functie Voice-over kiezen op het apparaat of uit.|
|**Spraakassistent**|Kan het gebruik van voice assistent-software op het apparaat.|
|**Schermopname**|Kan de gebruiker die de scherminhoud als een installatiekopie vast te leggen.|
|**Verzending van diagnostische gegevens**|Hiermee kunt het apparaat diagnostische gegevens voor Google verzenden.|
|**Geolocatie**|Hiermee kunt het apparaat locatiegegevens gebruiken.|
|**Kopiëren en plakken**|Kan functies kopiëren en plakken op het apparaat.|
|**Fabrieksinstellingen terugzetten**|Hiermee kunt de gebruiker een fabrieksinstellingen op het apparaat kan uitvoeren.|  |
|**Klembord delen tussen toepassingen**|Kan de gebruiker die het gebruik van het Klembord kopiëren en plakken tussen apps.|  |
|**Bluetooth**|Hiermee kunt het gebruik van Bluetooth op het apparaat.|

### <a name="store"></a>Opslaan

|Instelling|Details|  
|------------------|-------------|  
|**App Store**|Kan de gebruiker die toegang tot de Google Play store op het apparaat.|

### <a name="browser"></a>Browser

|Instelling|Details|  
|------------------|-------------|  
|**Webbrowser toestaan**|Hiermee kunt u de standaardwebbrowser van het apparaat moet worden gebruikt.|
|**Automatisch doorvoeren**|Hiermee kunt de functie automatisch doorvoeren van de webbrowser moet worden gebruikt.|
|**Active Scripting**|Hiermee kunt het apparaat webbrowser gebruiken active scripting.|
|**Pop-upblokkering**|Hiermee kunt het gebruik van het pop-upblokkering in de webbrowser.|
|**Cookies**|Hiermee kunt de webbrowser van het apparaat gebruikmaken van cookies.|

### <a name="cloud"></a>Cloud  

|Instelling|Details|  
|-------------|-------------|  
|**Google-back-up**|Hiermee kunt het gebruik van Google-back-up.|  
|**Automatische synchronisatie van Google-account**|Toestaan dat instellingen voor Google-accounts automatisch worden gesynchroniseerd.|  

### <a name="security"></a>Beveiliging  

|Instelling|Details|  
|-------------|-------------|  
|**SMS- en MMS-berichten**|Hiermee kunt het gebruik van de SMS- en MMS-berichten op het apparaat.|
|**Verwisselbare opslag**|Hiermee kunt het apparaat Gebruik Verwisselbare opslag, zoals een SD-kaart.|
|**Camera**|Gebruik van de camera op het apparaat toestaan.<br /><br /> Geldt voor Android- en Samsung KNOX-apparaten.|
|**Near Field Communication (NFC)**|Hiermee kunt u taken waarvoor near field communication als het apparaat wordt ondersteund.|
|**YouTube**|Hiermee kunt het gebruik van de app YouTube op het apparaat.<br /><br /> Geldt alleen voor Samsung KNOX-apparaten.|  
|**Uitschakelen**|Staat toe dat het apparaat wordt uitgeschakeld.<br /><br /> Geldt alleen voor Samsung KNOX-apparaten.|  

### <a name="roaming"></a>Roaming

|Instelling|Details|  
|-------------|-------------|  
|Spraakroaming|Hiermee kunt u spraakroaming wanneer het apparaat op een mobiel netwerk.|
|Gegevensroaming|Hiermee kunt dataroaming wanneer het apparaat op een mobiel netwerk.|


### <a name="encryption"></a>Versleuteling  
 Deze instellingen gelden voor Android- en Samsung KNOX-apparaten.  

|Instelling|Details|  
|-------------|-------------|  
|**Versleuteling opslagkaart**|Vereist dat de opslagkaart van het apparaat worden versleuteld.|
|**Bestandsversleuteling op apparaat**|Vereist dat bestanden op het mobiele apparaat zijn versleuteld.|  

### <a name="wireless-communications"></a>Draadloze communicatie

|Instelling|Details|  
|-------------|-------------|  
|**Draadloze netwerkverbinding**|Hiermee kunt het gebruik van de Wi-Fi-mogelijkheden van het apparaat.|
|**Wi-Fi-tethering**|Hiermee kunt het gebruik van Wi-Fi-tethering op het apparaat.|


### <a name="compliant-and-noncompliant-apps-android"></a>Compatibele en niet-compatibele apps (Android)  
U kunt een lijst van Android-apps die compatibel of niet compatibel zijn in uw bedrijf opgeven. Vervolgens kunt u rapporten om weer te geven van apparaten die niet-compatibele Apps geïnstalleerd en de bijbehorende gebruiker.  

U kunt niet zowel compatibele als niet-compatibele apps in hetzelfde configuratie-item opgeven.  

#### <a name="to-specify-the-compliant-or-noncompliant-apps-list"></a>De lijst met compatibele of niet-compatibele apps opgeven  

Op de pagina **Compatibele en niet-compatibele apps (Android)** geeft u de volgende gegevens op:  

|Instelling|Meer informatie|  
|-------------|----------------------|  
|**Lijst met niet-compatibele apps**|Hiermee geeft u een lijst met apps die worden gerapporteerd als niet-compatibel als geïnstalleerd door gebruikers.|  
|**Lijst van compatibele apps**|Hiermee geeft u een lijst met apps die gebruikers mogen installeren. Andere geïnstalleerde apps worden gerapporteerd als niet-compatibel.|  
|**Toevoegen**|Hiermee voegt u een app toe aan de geselecteerde lijst. Geef een naam van uw keuze op, eventueel de uitgever van de app, en de URL van de app in de App Store.<br /><br /> De URL opgeven van de [sectie apps van Google Play](https://play.google.com/store/apps), zoekt u de app die u wilt gebruiken.<br /><br /> Open de pagina van de app en kopieer de URL naar het klembord. U kunt deze nu als de URL gebruiken in de lijst met compatibele apps of de lijst met niet-compatibele apps.<br /><br /> **Voorbeeld:** Zoek in Google Play voor **Microsoft Office Mobile**. De URL die u gebruikt **https://play.google.com/store/apps/details?id=com.microsoft.office.officehub**.|  
|**Bewerken**|Hiermee kunt u de naam, de uitgever en de URL van de geselecteerde app bewerken.|  
|**Verwijderen**|Hiermee verwijdert u de geselecteerde app uit de lijst.|  
|**Importereneren**|Hiermee importeert u een lijst met apps die u hebt opgegeven in een bestand met door komma's gescheiden waarden. Gebruik de indeling toepassingsnaam, uitgever en app-URL in het bestand.|  

## <a name="android-for-work-configuration-items"></a>Android voor configuratie van werkitems
Android for Work heeft twee instellingsgroepen voor configuratie-items:

- **Wachtwoord**. Identiek aan de instellingen voor Android "klassieke."

- **Profiel werken**. Hiermee kunt de volgende Android voor werk instellingen:
  -    **Gegevens delen tussen werk en persoonlijke profielen toestaan**
  - **Werk profiel meldingen verbergen wanneer het apparaat is vergrendeld** (Android 6.0 +)
  -    **App machtiging standaardbeleid instellen** (Android 6.0 +)

Kiezen voor het maken van een configuratie-item in de Android werkprofiel **Android for Work** op de **algemeen** pagina en configureer instellingen voor elk van de instellingsgroepen. Het configuratie-item toevoegen aan een basislijn en gewoon implementeren. Deze instellingen wordt alleen toegepast op apparaten die zijn geregistreerd als Android voor werk, en niet op apparaten die worden ingeschreven als Android.

### <a name="kiosk-mode-samsung-knox-only"></a>Kioskmodus (alleen Samsung KNOX)  
Kioskmodus kunt u een apparaat zo vergrendelen dat alleen bepaalde functies werken. Bijvoorbeeld, kunt u een apparaat slechts één beheerde app die u opgeeft, of u kunt de volumeknoppen op een apparaat uitschakelen. Deze instellingen kunnen worden gebruikt voor een demonstratiemodel van een apparaat. Of ze kunnen worden gebruikt voor een apparaat dat is toegewezen aan slechts één functie, zoals een verkooppunt apparaat.  

#### <a name="to-configure-kiosk-mode-for-a-samsung-knox-device"></a>De kioskmodus configureren voor Samsung KNOX-apparaten  

1. Op de **configureren van instellingen voor kioskmodus voor Samsung KNOX-apparaten** pagina van de Wizard Configuratie-Item maken de volgende informatie opgeven:  

   |Instelling|Meer informatie|  
   |-------------|----------------------|  
   |**App selecteren**|Kies **Bladeren** om een Configuration Manager Android-toepassing te selecteren (met de extensie **.apk**) die mag worden uitgevoerd wanneer het apparaat in kioskmodus is. Er mogen geen andere apps op het apparaat worden uitgevoerd.|  
   |**Volumeknoppen**|Hiermee wordt het gebruik van de volumeknoppen op het apparaat in- of uitgeschakeld.|  
   |**Slaapstandknop voor scherm en knop activeren**|Hiermee wordt de knop voor slaapstand/ontwaken van het scherm in- of uitgeschakeld op het apparaat.|  

2. Als u klaar bent, kiest u **volgende**.  

## <a name="reports-for-monitoring"></a>Rapporten voor de bewaking
U kunt een van de volgende rapporten gebruiken om te controleren en niet-compatibele apps:  

- **Lijst met niet-compatibele Apps en apparaten voor een opgegeven gebruiker**. Bevat informatie over gebruikers en apparaten die een App geïnstalleerd hebben die niet compatibel zijn met een beleid dat u hebt opgegeven.  

- **Samenvatting van de gebruikers die niet-compatibele Apps**. Bevat informatie over gebruikers die een App geïnstalleerd hebben die niet compatibel zijn met een beleid dat u hebt opgegeven.  

Zie [Rapportage in System Center Configuration Manager](../../core/servers/manage/reporting.md) voor meer informatie over het gebruik van rapporten.  

## <a name="see-also"></a>Zie tevens  
[Configuratie-items voor apparaten die worden beheerd zonder dat de System Center Configuration Manager-client](../../compliance/deploy-use/configuration-items-for-devices-managed-without-the-client.md)

