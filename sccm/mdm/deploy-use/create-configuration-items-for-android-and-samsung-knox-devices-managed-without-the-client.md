---
title: Configuratie-items maken voor Android en Samsung KNOX Standard apparaten die worden beheerd met Intune
titleSuffix: Configuration Manager
description: De configuratie-item van het System Center Configuration Manager Android en Samsung KNOX Standard gebruiken om instellingen voor apparaten te beheren.
ms.custom: na
ms.date: 03/27/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: configmgr-hybrid
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 7b66f3c4-e3bb-4f6a-abd5-55be649ff90d
caps.latest.revision: "17"
caps.handback.revision: "0"
author: andredm7
ms.author: andredm
manager: angrobe
ms.openlocfilehash: 3fa824c94b02ed7141c7051bab86fa64a4a9ee49
ms.sourcegitcommit: c236214b2fcc13dae7bad96d7fb33f692868191d
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/12/2017
---
# <a name="how-to-create-configuration-items-for-android-and-samsung-knox-devices-managed-without-the-system-center-configuration-manager-client"></a>Configuratie-items maken voor Android- en Samsung KNOX-apparaten die worden beheerd zonder de System Center Configuration Manager-client

De System Center Configuration Manager gebruiken **Android en Samsung KNOX** configuratie-item voor het beheren van instellingen voor Android en Samsung KNOX-apparaten die zijn geregistreerd bij Microsoft Intune of on-premises worden beheerd door Configuration Manager.  

#### <a name="to-create-an-android-and-samsung-knox-configuration-item"></a>Maken van een configuratie-item voor Android en Samsung KNOX  

1. Kies in de Configuration Manager-console **activa en naleving**.  

2. In de **activa en naleving** werkruimte Vouw **instellingen voor naleving**, en kies vervolgens **configuratie-Items**.  

3. Op de **Start** tabblad, in de **maken** groep, kiest u **configuratie-Item maken**.  

4. Op de **algemene** pagina van de Wizard Configuratie-Item maken een naam en een optionele beschrijving voor het configuratie-item opgeven.  

5. Onder **Geef het type configuratie-item dat u wilt maken**, kies **Android en Samsung KNOX**.  

6. Kies **categorieën** als u categorieën maakt en toewijst om te zoeken en filteren van configuratie-items in de Configuration Manager-console.  

7. Op de **ondersteunde Platforms** pagina van de wizard, kies de specifieke Android- of Samsung KNOX-platforms die het configuratie-item evalueren.  

8. Op de **apparaatinstellingen** pagina van de wizard, kiest u de instellingengroep die u wilt configureren. Zie [Android en Samsung KNOX verwijzing configuratie-item instellingen](#BKMK_setref) in dit onderwerp voor meer informatie en kies vervolgens **volgende**.  

    > [!TIP]  
    >  Als de instelling die u wilt dat niet wordt weergegeven, controleert u de **extra instellingen configureren die niet zijn opgenomen in de standaardinstellingsgroepen** vak.  

9. Op elke instellingenpagina configureert u de instellingen die u nodig hebt. Bovendien kunt u kiezen of u herstellen wilt, wanneer ze niet compliant zijn op apparaten (wanneer dit wordt ondersteund).  

10. U kunt ook de ernst die worden gerapporteerd als een configuratie-item niet compliant is gevonden voor elke instellingsgroep configureren:  

    - **Geen**. Apparaten die niet voldoen aan deze compliantieregel wordt de ernst voor rapporten van Configuration Manager niet rapporteren.  

    - **Informatie**. Apparaten die niet voldoen aan deze compliantieregel fouternst van **informatie** voor Configuration Manager-rapporten.  

    - **Waarschuwing**. Apparaten die niet voldoen aan deze compliantieregel fouternst van **waarschuwing** voor Configuration Manager-rapporten.  

    - **Kritieke**. Apparaten die niet voldoen aan deze compliantieregel fouternst van **Kritiek** voor Configuration Manager-rapporten.  

    - **Kritiek met gebeurtenis**. Apparaten die niet voldoen aan deze compliantieregel fouternst van **Kritiek** voor Configuration Manager-rapporten. Dit ernstniveau wordt ook vastgelegd als een Windows-gebeurtenis in het logboek voor toepassingsgebeurtenissen.  

11. Op de **Platformtoepasbaarheid** pagina van de wizard controleert u alle instellingen die niet compatibel met de ondersteunde platforms die u eerder hebt gekozen. U kunt teruggaan en deze instellingen verwijderen of u kunt doorgaan.  

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
|**Wachtwoordverlooptijd in dagen**|Hiermee geeft u het aantal dagen voordat een wachtwoord moet worden gewijzigd.|  
|**Aantal onthouden wachtwoorden**|Voorkomt dat eerder gebruikte wachtwoorden opnieuw gebruiken.|  
|**Aantal mislukte aanmeldingspogingen voordat het apparaat wordt gewist**|Wordt het apparaat gewist als dit aantal is mislukt aanmeldingspogingen.|  
|**Niet-actieve periode waarna apparaat wordt vergrendeld**|Hiermee geeft u de hoeveelheid tijd voordat het apparaat wordt vergrendeld als dit niet wordt gebruikt.|
|**Wachtwoordkwaliteit**|Hiermee geeft u de vereiste wachtwoordcomplexiteit en of biometrische apparaten kunnen worden gebruikt.|  
|**Smart Lock en andere vertrouwde agents toestaan**|Hiermee kunt u de Smart Lock-functie op compatibele Android-apparaten beheren. Met deze telefoonmogelijkheid kunt u uitschakelen of het wachtwoord van het apparaat vergrendelen scherm overslaan als het apparaat zich in een vertrouwde locatie bevindt, zoals wanneer deze is verbonden met een bepaald Bluetooth-apparaat, of wanneer het in de buurt van een NFC-tag bevindt. U kunt deze instelling gebruiken om te voorkomen dat gebruikers Smart Lock configureren.|
|**Vingerafdruk voor ontgrendelen (KNOX 5.0 +)**|Kan het gebruik van een vingerafdruk voor het ontgrendelen van compatibele apparaten.|

### <a name="device"></a>Apparaat   

|Instelling|Details|  
|------------------|-------------|  
|**Nummer inspreken**|Schakelt de functie inspreken van telefoonnummers op het apparaat of uit.|
|**Spraakassistent**|Staat het gebruik van voice-assistent software op het apparaat.|
|**Schermopname**|Kan de gebruiker de scherminhoud als afbeelding vastleggen.|
|**Verzending van diagnostische gegevens**|Hiermee kunt het apparaat diagnostische gegevens verzendt naar Google.|
|**Geolocatie**|Hiermee kunt het apparaat locatiegegevens gebruiken.|
|**Kopiëren en plakken**|Kan functies kopiëren en plakken op het apparaat.|
|**Fabrieksinstellingen terugzetten**|Kan de gebruiker die u de fabrieksinstellingen op het apparaat.|  |
|**Klembord delen tussen toepassingen**|Kan de gebruiker die het gebruik van het Klembord kopiëren en plakken tussen apps.|  |
|**Bluetooth**|Kan het gebruik van Bluetooth op het apparaat.|

### <a name="store"></a>Opslaan

|Instelling|Details|  
|------------------|-------------|  
|**App Store**|Kan de gebruiker de Google Play store openen op het apparaat.|

### <a name="browser"></a>Browser

|Instelling|Details|  
|------------------|-------------|  
|**Webbrowser toestaan**|Kan de standaardwebbrowser van het apparaat moet worden gebruikt.|
|**Automatisch doorvoeren**|Hiermee kunt de functie automatisch doorvoeren van de webbrowser moet worden gebruikt.|
|**Active Scripting**|Hiermee kunt de webbrowser van het apparaat gebruikmaakt van active scripting.|
|**Pop-upblokkering**|Hiermee kunt het gebruik van de pop-upblokkering in de webbrowser.|
|**Cookies**|Hiermee kunt de webbrowser van het apparaat gebruikmaken van cookies.|

### <a name="cloud"></a>Cloud  

|Instelling|Details|  
|-------------|-------------|  
|**Google-back-up**|Kan het gebruik van Google-back-up.|  
|**Google-account automatisch synchroniseren**|Toestaan dat instellingen voor Google-accounts automatisch worden gesynchroniseerd.|  

### <a name="security"></a>Beveiliging  

|Instelling|Details|  
|-------------|-------------|  
|**SMS- en MMS-berichten**|Kan het gebruik van de SMS- en MMS-berichten op het apparaat.|
|**Verwisselbare opslag**|Hiermee kunt het apparaat Verwisselbare opslag gebruiken, zoals een SD-kaart.|
|**Camera**|Gebruik van de camera op het apparaat toestaan.<br /><br /> Geldt voor Android- en Samsung KNOX-apparaten.|
|**Near Field Communication (NFC)**|Hiermee kunt taken die in de buurt van veld-communicatie gebruiken als het apparaat wordt ondersteund.|
|**YouTube**|Staat het gebruik van de YouTube-app op het apparaat.<br /><br /> Geldt alleen voor Samsung KNOX-apparaten.|  
|**Uitschakelen**|Staat toe dat het apparaat wordt uitgeschakeld.<br /><br /> Geldt alleen voor Samsung KNOX-apparaten.|  

### <a name="roaming"></a>Roaming

|Instelling|Details|  
|-------------|-------------|  
|Spraakroaming|Staat spraakroaming wanneer het apparaat op een mobiel netwerk.|
|Gegevensroaming|Hiermee staat u dataroaming wanneer het apparaat op een mobiel netwerk.|


### <a name="encryption"></a>Versleuteling  
 Deze instellingen gelden voor Android- en Samsung KNOX-apparaten.  

|Instelling|Details|  
|-------------|-------------|  
|**Versleuteling opslagkaart**|Vereist dat de opslagkaart van het apparaat is versleuteld.|
|**Bestandsversleuteling op apparaat**|Vereist dat bestanden op het mobiele apparaat zijn versleuteld.|  

### <a name="wireless-communications"></a>Draadloze communicatie

|Instelling|Details|  
|-------------|-------------|  
|**Draadloze netwerkverbinding**|Kan het gebruik van de Wi-Fi-mogelijkheden van het apparaat.|
|**Wi-Fi-tethering**|Kan het gebruik van Wi-Fi-tethering op het apparaat.|


### <a name="compliant-and-noncompliant-apps-android"></a>Compatibele en niet-compatibele apps (Android)  
U kunt een lijst van Android-apps die compatibel of niet compatibel zijn in uw bedrijf opgeven. U kunt vervolgens rapporten apparaten die niet-compatibele apps geïnstalleerd hebben weer te geven en de bijbehorende gebruiker gebruiken.  

U kunt niet zowel compatibele als niet-compatibele apps in hetzelfde configuratie-item opgeven.  

#### <a name="to-specify-the-compliant-or-noncompliant-apps-list"></a>De lijst met compatibele of niet-compatibele apps opgeven  

Op de pagina **Compatibele en niet-compatibele apps (Android)** geeft u de volgende gegevens op:  

|Instelling|Meer informatie|  
|-------------|----------------------|  
|**Lijst met niet-compatibele apps**|Hiermee geeft u een lijst met apps die worden gerapporteerd als niet-compatibel als geïnstalleerd door gebruikers.|  
|**Lijst van compatibele apps**|Hiermee geeft u een lijst met apps die gebruikers mogen installeren. Andere geïnstalleerde apps worden gerapporteerd als niet-compatibel.|  
|**Toevoegen**|Hiermee voegt u een app toe aan de geselecteerde lijst. Geef een naam van uw keuze op, eventueel de uitgever van de app, en de URL van de app in de App Store.<br /><br /> De URL opgeven van de [sectie apps van Google Play](https://play.google.com/store/apps), zoekt u de app die u wilt gebruiken.<br /><br /> Open de pagina van de app en kopieer de URL naar het klembord. U kunt deze nu als de URL gebruiken in de lijst met compatibele apps of de lijst met niet-compatibele apps.<br /><br /> **Voorbeeld:** Zoek in Google Play naar **Microsoft Office Mobile**. De URL die u gebruikt **https://play.google.com/store/apps/details?id=com.microsoft.office.officehub**.|  
|**Bewerken**|Hiermee kunt u de naam, uitgever en de URL van de geselecteerde app bewerken.|  
|**Verwijderen**|Hiermee verwijdert u de geselecteerde app uit de lijst.|  
|**Importereneren**|Een lijst met apps die u hebt opgegeven in een bestand met door komma's gescheiden waarden geïmporteerd. Gebruik de indeling toepassingsnaam, uitgever, app-URL in het bestand.|  

## <a name="android-for-work-configuration-items"></a>Android voor configuratie van werkitems
Android for Work heeft twee instellingsgroepen voor configuratie-items:

- **Wachtwoord**. Identiek aan de instellingen voor Android 'klassiek'.

- **Profiel werken**. Maakt gebruik van de volgende Android for Work-instellingen:
  - **Gegevens delen tussen werk en persoonlijke profielen toestaan**
  - **Werk profiel meldingen verbergen wanneer apparaat is vergrendeld** (Android 6.0 en hoger)
  - **Standaardbeleid app machtiging instellen** (Android 6.0 en hoger)

Als u wilt een configuratie-item in de Android work-profiel maakt, kiest u **Android for Work** op de **algemene** pagina en configureer instellingen voor elk van de instellingsgroepen. Het configuratie-item toevoegen aan een basislijn en gewoon implementeren. Deze instellingen gelden alleen voor apparaten die worden ingeschreven als Android for Work en niet op apparaten die zijn geregistreerd als Android.

### <a name="kiosk-mode-samsung-knox-only"></a>Kioskmodus (alleen Samsung KNOX)  
Kioskmodus kunt u een apparaat zo vergrendelen dat alleen bepaalde functies werken. Bijvoorbeeld, kunt u een apparaat slechts één beheerde app die u opgeeft uitvoert of u kunt de volumeknoppen op een apparaat uitschakelen. Deze instellingen kunnen worden gebruikt voor een demonstratiemodel van een apparaat. Of ze kunnen worden gebruikt voor een apparaat dat is toegewezen aan slechts één functie, zoals een verkooppuntapparaat.  

#### <a name="to-configure-kiosk-mode-for-a-samsung-knox-device"></a>De kioskmodus configureren voor Samsung KNOX-apparaten  

1. Op de **configureren van instellingen voor kioskmodus voor Samsung KNOX-apparaten** pagina van de Wizard Configuratie-Item maken de volgende informatie opgeven:  

   |Instelling|Meer informatie|  
   |-------------|----------------------|  
   |**App selecteren**|Kies **Bladeren** om een Configuration Manager-Android-toepassing te selecteren (met de extensie **.apk**) die mag worden uitgevoerd wanneer het apparaat in kioskmodus is. Er mogen geen andere apps op het apparaat worden uitgevoerd.|  
   |**Volumeknoppen**|Hiermee wordt het gebruik van de volumeknoppen op het apparaat in- of uitgeschakeld.|  
   |**Scherm slaapstand**|Hiermee wordt de knop voor slaapstand/ontwaken van het scherm in- of uitgeschakeld op het apparaat.|  

2. Als u klaar bent, kiest u **volgende**.  

## <a name="reports-for-monitoring"></a>Rapporten voor bewaking
U kunt een van de volgende rapporten gebruiken om te controleren en niet-compatibele apps:  

- **Lijst met niet-compatibele Apps en apparaten voor een opgegeven gebruiker**. Geeft informatie weer over gebruikers en apparaten die apps geïnstalleerd hebben die niet compatibel met een door u opgegeven beleid.  

- **Overzicht van gebruikers met niet-compatibele Apps**. Bevat informatie over gebruikers die apps geïnstalleerd hebben die niet compatibel zijn met een beleid dat u hebt opgegeven.  

Zie [Rapportage in System Center Configuration Manager](../../core/servers/manage/reporting.md) voor meer informatie over het gebruik van rapporten.  

## <a name="see-also"></a>Zie tevens  
[Configuratie-items voor apparaten die worden beheerd zonder de System Center Configuration Manager-client](../../compliance/deploy-use/configuration-items-for-devices-managed-without-the-client.md)
