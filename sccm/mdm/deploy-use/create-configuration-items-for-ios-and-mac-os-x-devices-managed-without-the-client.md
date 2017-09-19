---
title: Configuratie-items maken voor iOS- en Mac OS X-apparaten worden beheerd met Intune | Microsoft Docs
description: Gebruik de System Center Configuration Manager iOS en Mac OS X-configuratie-item voor het beheren van instellingen voor iOS en Mac OS X-apparaten.
ms.custom: na
ms.date: 03/28/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: configmgr-hybrid
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 613a48ac-c55d-4c4a-94ea-d3747a1b10cb
caps.latest.revision: "15"
caps.handback.revision: "0"
author: andredm7
ms.author: andredm
manager: angrobe
ms.openlocfilehash: 039173c9411a530348bf550e4be7b771756d57dc
ms.sourcegitcommit: b438515490e04fb09c82a8af642d38e9a0605178
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 09/15/2017
---
# <a name="how-to-create-configuration-items-for-ios-and-mac-os-x-devices-managed-with-intune"></a>Het maken van configuratie-items voor iOS en Mac OS X-apparaten worden beheerd door Intune
De System Center Configuration Manager gebruiken **iOS en Mac OS X** configuratie-item voor het beheren van instellingen voor iOS en Mac OS X-apparaten die zijn ingeschreven bij Microsoft Intune of on-premises worden beheerd door Configuration Manager.  
  
### <a name="to-create-an-ios-and-mac-os-x-configuration-item"></a>Een configuratie-item voor iOS en Mac OS X maken  
  
1.  Klik in de Configuration Manager-console op **activa en naleving**.  
  
2.  Vouw in de werkruimte **Activa en naleving** het gedeelte **Instellingen voor naleving**uit en klik vervolgens op **Configuratie-items**.  
  
3.  Klik op het tabblad **Start** in de groep **Maken** op **Configuratie-item maken**.  
  
4.  Geef op de pagina **Algemeen** van de **Wizard Configuratie-item maken** een naam en een optionele beschrijving voor het configuratie-item op.  
  
5.  Selecteer onder **Geef het type configuratie-item op dat u wilt maken** de optie **iOS en Mac OS X**.  
  
6.  Klik op **categorieën** als u categorieën maakt en toewijst om te zoeken en filteren van configuratie-items in de Configuration Manager-console.  
  
7.  Selecteer op de pagina **Ondersteunde platforms** van de wizard de specifieke iOS- of Mac OS X-platforms die het configuratie-item evalueren.  
  
8.  Op de pagina **Apparaatinstellingen** van de wizard selecteert u de instellingengroep die u wilt configureren. Zie [Naslaginformatie voor het configuratie-item voor iOS en Mac OS X](#BKMK_Setref) in dit onderwerp voor meer informatie en klik daarna op **Volgende**.  
  
    > [!TIP]  
    >  Als de gewenste instelling niet wordt weergegeven, schakelt u het selectievakje **Extra instellingen configureren die niet zijn opgenomen in de standaardinstellingsgroepen** in.  
  
9. Op elke instellingenpagina configureert u de instellingen die u nodig hebt en geeft u aan of u deze wilt corrigeren wanneer ze niet compliant zijn op apparaten (wanneer dit wordt ondersteund).  
  
10. U kunt voor elke instellingengroep ook de ernst configureren die wordt gerapporteerd als wordt geconstateerd dat een configuratie-item niet compliant is:  
  
    -   **Geen** -apparaten die niet voldoen aan deze compliantieregel niet rapporteren ernst voor Configuration Manager-rapporten.  
  
    -   **Informatie** -apparaten die niet voldoen aan deze compliantieregel fouternst van **informatie** voor Configuration Manager-rapporten.  
  
    -   **Waarschuwing** -apparaten die niet voldoen aan deze compliantieregel fouternst van **waarschuwing** voor Configuration Manager-rapporten.  
  
    -   **Kritieke** -apparaten die niet voldoen aan deze compliantieregel fouternst van **kritieke** voor Configuration Manager-rapporten.  
  
    -   **Kritiek met gebeurtenis** -apparaten die niet voldoen aan deze compliantieregel fouternst van **kritieke** voor Configuration Manager-rapporten. Dit ernstniveau wordt ook vastgelegd als een Windows-gebeurtenis in het logboek voor toepassingsgebeurtenissen.  
  
11. Op de pagina **Platformtoepasbaarheid** van de wizard controleert u alle instellingen die niet compatibel zijn met de ondersteunde platforms die u eerder hebt geselecteerd. U kunt teruggaan en deze instellingen verwijderen of u kunt doorgaan.  
  
    > [!TIP]  
    >  Niet-ondersteunde instellingen worden niet beoordeeld op compliantie.  
  
12. Voltooi de wizard.  
  
 U kunt het nieuwe configuratie-item weergeven in het knooppunt **Configuratie-items** van de werkruimte **Activa en naleving**.  
  
##  <a name="ios-and-mac-os-x-configuration-item-settings-reference"></a>Naslaginformatie voor het configuratie-item voor iOS en Mac OS X  
  
###  <a name="password"></a>Wachtwoord  
  
|Naam van de instelling|Details|  
|------------------|-------------|  
|**Wachtwoordinstellingen vereisen op mobiele apparaten**|Hiermee vereist u een wachtwoord op ondersteunde apparaten.|  
|**Minimale wachtwoordlengte (tekens)**|De minimale lengte van het wachtwoord.|  
|**Wachtwoordverlooptijd in dagen**|Het aantal dagen waarna een wachtwoord moet worden gewijzigd.|  
|**Aantal onthouden wachtwoorden**|Voorkomt dat eerder gebruikte wachtwoorden opnieuw worden gebruikt.|  
|**Aantal mislukte aanmeldingspogingen voordat het apparaat wordt gewist**|Wist de gegevens op het apparaat als dit aantal aanmeldingspogingen mislukt.<br /><br /> (alleen iOS)|  
|**Wachtwoordcomplexiteit**|Hiermee kunt u opgeven of u een pincode, zoals '1234', wilt gebruiken of dat er een sterk wachtwoord moet worden opgegeven.| 
|**Eenvoudige wachtwoorden toestaan**|Toestaan dat eenvoudige wachtwoorden, zoals **0000** en **1234**.|
|**Vingerafdruk voor ontgrendelen**|Staat het gebruik van een vingerafdruk voor het ontgrendelen van het apparaat.|
|**Wijziging van de wachtwoordcode** (onder supervisie alleen)|Toestaan dat het wachtwoord van het apparaat worden toegevoegd, gewijzigd of verwijderd.|
  
###  <a name="device"></a>Apparaat  
 Deze instellingen gelden voor zowel iOS- als Mac OS X-apparaten.  
  
|Naam van de instelling|Details|  
|------------------|-------------|  
|**Game center-vrienden toevoegen**|Staat het toevoegen van vrienden in de Game Center-app toe|
|**Nummer inspreken**|Staat het gebruik toe van de functie voor het inspreken van nummers op het apparaat.|  
|**Spraakassistent**|Staat het gebruik toe van een app voor spraakondersteuning, zoals Siri.|  
|**Spraakassistent bij vergrendeling**|Staat het gebruik toe van een app voor spraakondersteuning, zoals Siri, wanneer het apparaat is vergrendeld.|  
|**Schermopname**|Staat het maken van een beeldschermopname voor het apparaat toe.|  
|**Videochatclient**|Staat het gebruik van videochat-apps, zoals Facetime, toe.|  
|**Games voor meerdere spelers**|Staat het spelen van games met andere spelers op internet toe.|  
|**Persoonlijke portemonneesoftware tijdens vergrendeling**|Staat het gebruik van Personal Wallet-software, zoals Passbook, toe.|  
|**Verzending van diagnostische gegevens**|Staat het verzenden van app- logboekbestanden toe.|  
|**Meldingen van Onderhoudscentrum**|De gebruiker toegang heeft tot de weergave van meldingen zonder het ontgrendelen van het apparaat toestaan.|
|**Apple muziek** (onder supervisie alleen)|Gebruik van de app Apple muziek toestaan.|
|**Podcasts** (onder supervisie alleen)|Gebruik van de app Podcasts toestaan.|
|**App berichten** (onder supervisie alleen)|Hiermee staat u gebruik van de app berichten om berichten te verzenden.|
|**Achtergrond wijziging** (onder supervisie alleen)|De gebruiker te wijzigen van de achtergrond van het apparaat toestaan.|
|**Word opzoeken** (onder supervisie alleen)|Toestaan dat de iOS-functie waarmee u een woord markeren en de definitie opzoeken.|
|**Pols detectie voor de gekoppelde Apple kijkt naar**|Wanneer dit is ingeschakeld, kan de Apple Watch meldingen niet weergegeven wanneer deze niet wordt gedragen.|
|**Siri taalgebruik filter** (onder supervisie alleen)|Voorkomt dat met Siri op dicteren of schennende taal spreken.|
|**Apparaat naam wijziging** (onder supervisie alleen)|De gebruiker te wijzigen van de naam van het apparaat toestaan.|
|**Verzending van diagnostische gegevens wijziging** (onder supervisie alleen)|Toestaan of blokkeren van het apparaat verzending van diagnostische gegevens naar Apple.|
|**Game center** (onder supervisie alleen)|Gebruik van de app Game Center toestaan.|
|**iTunes Radio** (onder supervisie alleen)|Gebruik van de keuzerondjes iTunes app toestaan.|
|**Apple nieuws** (onder supervisie alleen)|Gebruik van de Apple-nieuws app toestaan.|
|**Koppelen van Apple Watch** (onder supervisie alleen)|Toestaan dat het apparaat koppelen aan een Apple Watch.|
|**Automatische correcties** (onder supervisie alleen)|Hiermee kunt het apparaat automatisch corrigeren verkeerd gespelde woorden.|
|**Wijziging van de Bluetooth-** (onder supervisie alleen)|Kan de gebruiker te wijzigen van de Bluetooth-instellingen op het apparaat.|
|**Wijzigingen in de app-instellingen voor het gebruik van mobiel dataverkeer** (onder supervisie alleen)|Kan de gebruiker om te bepalen welke apps mobiel dataverkeer gebruiken zijn toegestaan.|
|**Sneltoetsen** (onder supervisie alleen)|Staat het gebruik van sneltoetsen.|
|**Voorspeld toetsenborden** (onder supervisie alleen)|Het gebruik van voorspellende toetsenborden aangeraden woorden die de gebruiker mogelijk wilt toestaan.|
|**Toetsenbord spellingcontrole** (onder supervisie alleen)|Kan de spellingcontrole apparaat.|
|**Melding wijziging** (onder supervisie alleen)|Kan de gebruiker de melding apparaatinstellingen te wijzigen.|
|**Retourneren van resultaten op Internet in zoekopdrachten met Spotlight** (onder supervisie alleen)|Verbinding maken met het Internet voor aanvullende resultaten zoekopdrachten met Spotlight laten.|
|**Gebruik van Siri op door gebruikers gegenereerde query-inhoud op Internet** (onder supervisie alleen)|Siri voor toegang tot websites om vragen te beantwoorden toestaan.|

  
###  <a name="store"></a>Opslaan  
 Deze instellingen gelden alleen voor iOS-apparaten.  
  
|Naam van de instelling|Details|  
|------------------|-------------|  
|**App Store**|Staat toegang tot de App Store op het apparaat toe.|  
|**Een wachtwoord invoeren voor toegang tot de App Store**|Gebruikers moeten een wachtwoord invoeren voor toegang tot de App Store.|  
|**Aankopen vanuit app**|Staat gebruikers toe om aankopen te doen vanuit apps.|
|**Installeren van apps met Apple Configurator en alleen iTunes** (onder supervisie alleen)|Hiermee schakelt de App Store van het startscherm van een apparaat of. Gebruikers kunnen nog steeds iTunes of het hulpprogramma Apple Configurator gebruiken om te installeren en bijwerken van apps.|
|**Toegang tot de iBooks store** (onder supervisie alleen)|De gebruiker om te bladeren en kopen boeken uit de iBooks store toestaan.|
|**Automatische app downloads** (onder supervisie alleen)|Toestaan dat apps die zijn aangeschaft op andere apparaten automatisch downloaden naar dit apparaat. Deze instelling heeft geen invloed op app-updates.|

  
###  <a name="browser"></a>Browser  
 Deze instellingen gelden alleen voor iOS-apparaten.  
  
|Naam van de instelling|Details|  
|------------------|-------------|  
|**Standaardbrowser**|Gebruiker kan de standaardbrowser wijzigen.|  
|**Automatisch doorvoeren**|Gebruiker kan de instellingen voor automatisch aanvullen in de browser wijzigen.|  
|**Active Scripting**|Browser kan scripts, zoals Active X-scripts, uitvoeren.|  
|**Pop-upblokkering**|Hiermee schakelt u de pop-upblokkering voor browsers in of uit.|  
|**Cookies**|Toestaan dat cookies op het apparaat worden opgeslagen.|  
|**Fraudewaarschuwing**|Hiermee schakelt u de waarschuwingen voor mogelijke frauduleuze websites in of uit.|  
  
###  <a name="content-rating"></a>Inhoudsrestricties  
 Deze instellingen gelden alleen voor iOS-apparaten.  
  
|Naam van de instelling|Details|  
|------------------|-------------|  
|**Expliciete inhoud in mediastore**|Hiermee kunt u opgeven of u wilt toestaan dat inhoud voor volwassenen toegankelijk is vanuit de App Store.|  
|**Classificatieregio**|Hiermee geeft u het land op waarvoor u de classificatiebeperkingen wilt toepassen.|  
|**Classificatie van films**|Hiermee geeft u de maximale classificatie van filminhoud aan die u wilt toestaan.|  
|**Classificatie van tv**|Hiermee geeft u de maximale classificatie van tv-programma's aan die u wilt toestaan.|  
|**Classificatie van apps**|Hiermee geeft u de maximale classificatie van apps aan die u wilt toestaan.| 
|**Inhoud uit de Ibooks store als Erotisch gemarkeerd,'** (onder supervisie alleen)|Toestaan dat de gebruiker downloaden boeken uit de categorie 'Erotisch'.| 
  
> [!NOTE]  
>  De classificaties die u kunt selecteren, verschillen afhankelijk van de **Classificatieregio** die u hebt gekozen.  
  
###  <a name="cloud"></a>Cloud  
 Deze instellingen gelden alleen voor iOS-apparaten.  
  
|Naam van de instelling|Details|  
|------------------|-------------|  
|**Back-up van de cloud**|Het maken van back-ups met cloudservices, zoals iCloud, toestaan.|  
|**Versleutelde back-ups**|Het versleutelen van back-ups die worden gemaakt met een cloudservice toestaan.|  
|**Synchronisatie van documenten**|Synchronisatie van documenten door een cloudservice toestaan.|  
|**Synchronisatie van foto 's**|Synchronisatie van foto’s door een cloudservice toestaan.| 
|**iCloud afbeeldingsbibliotheek**|Indien ingesteld op **Nee**, wordt het gebruik van iCloud afbeeldingsbibliotheek waarmee gebruikers foto's en video's opslaan in de cloud. Foto's niet volledig zijn gedownload van iCloud afbeeldingsbibliotheek op het apparaat wordt verwijderd van het apparaat als deze is ingesteld op **Nee**.|
|**iCloud foto's delen**|Ingesteld op **Nee** iCloud foto's delen op het apparaat uitschakelen.|
|**Voortzetten van activiteiten op een ander apparaat via Handoff**|Toestaan dat gebruikers kunnen doorgaan met werk waaraan ze zijn begonnen op een iOS-apparaat op een ander iOS of Mac OS X-apparaat.|
|**Gegevens synchroniseren vanuit beheerde apps met iCloud**|Toestaan dat apps die u met Intune gegevens synchroniseren naar iCloud-account van de gebruiker beheert.|

  
###  <a name="security"></a>Beveiliging  
 Deze instellingen gelden alleen voor iOS-apparaten.  
  
|Naam van de instelling|Details|  
|------------------|-------------|  
|**Camera**|Gebruik van de camera op het apparaat toestaan.| 
|**Nieuwe enterprise app auteurs vertrouwen**|Kan de gebruiker selecteren om te vertrouwen apps die niet zijn gedownload uit de appstore.| 
  
###  <a name="roaming"></a>Roaming  
 Deze instellingen gelden alleen voor iOS-apparaten.  
  
|Naam van de instelling|Details|  
|------------------|-------------|  
|**Spraakroaming**|Staat spraakroaming tijdens het roamen toe.|  
|**Automatische synchronisatie tijdens roamen**|Staat toe dat het het apparaat automatisch wordt gesynchroniseerd tijdens het roamen.|  
|**Gegevensroaming**|Roaming tussen netwerken toestaan tijdens het ophalen van gegevens.|  
  
###  <a name="system-security"></a>Systeembeveiliging  
 Deze instellingen gelden alleen voor iOS-apparaten.  
  
|Naam van de instelling|Details|  
|------------------|-------------|  
|**Gebruiker accepteert niet-vertrouwde TLS-certificaten**|Als **Toegestaan** is geselecteerd, wordt de gebruiker toegestaan om deze certificaten te accepteren. Als **Niet toegestaan** is geselecteerd, worden niet-vertrouwde certificaten automatisch geweigerd.|
|**Activeringsvergrendeling (alleen in supervisiemodus) toestaan**|Gebruik deze instelling om iOS-activeringsvergrendeling in te schakelen op iOS-apparaten **onder supervisie** die u beheert. Zie voor meer informatie over activeringsvergrendeling [iOS-activeringsvergrendeling beheren met System Center Configuration Manager](../../mdm/deploy-use/manage-ios-activation-lock.md).
|**Vergrendelingsscherm voor beheercentrum**|Bepaalt of toegang tot de Control Center-app mogelijk is wanneer het apparaat is vergrendeld.|  
|**Weergave van meldingen in vergrendelingsscherm**|Bepaalt of meldingen kunnen worden bekeken wanneer het apparaat is vergrendeld.|  
|**Weergave van vandaag in vergrendelingsscherm**|Bepaalt of de weergave van vandaag kan worden bekeken wanneer het apparaat is vergrendeld.|  
|**Wijzigen van accountinstellingen** (onder supervisie alleen)|Toestaan dat de gebruiker accountinstellingen, zoals e-configuraties wijzigen.|
|**Wijzigingen aanbrengen in de instellingen van de app Zoek vrienden** (onder supervisie alleen)|De gebruiker te wijzigen van instellingen voor de app Zoek vrienden toestaan.|
|**Gebruik een host om te bepalen met welke apparaten een iOS-apparaat kunt koppelen aan** (onder supervisie alleen)|Een host toe, waarmee de beheerder kan bepalen welke apparaten een iOS-apparaat kunt koppelen aan toestaan.|
|**Wissen van alle inhoud en instellingen** (onder supervisie alleen)|De gebruiker de optie te gebruiken van het wissen van alle inhoud en instellingen op het apparaat toestaan.|
|**Configureert u beperkingen op apparaat** (onder supervisie alleen)|De gebruiker voor het configureren van beperkingen voor apparaat (Ouderlijk toezicht) op het apparaat toestaan.|
|**Installeren van configuratieprofielen en -certificaten** (onder supervisie alleen)|De gebruiker voor het installeren van configuratieprofielen en -certificaten toestaan.|
|**Wachtwoord voor aanvragen voor uitgaande AirPlay**|Vereist een wachtwoord voor koppelen wanneer AirPlay door de gebruiker wordt gebruikt om inhoud te streamen naar andere Apple-apparaten.|
  
###  <a name="data-protection"></a>Gegevensbescherming  
 Deze instellingen gelden alleen voor iOS-apparaten.  
  
|Naam van de instelling|Details|  
|------------------|-------------|  
|**Documenten in beheerde apps openen in andere onbeheerde apps**|Voor gebruik met apps die worden beheerd door Configuration Manager application management-beleid.|  
|**Documenten in onbeheerde apps openen in andere beheerde apps**|Voor gebruik met apps die worden beheerd door Configuration Manager application management-beleid.| 
|**AirDrop behandelen als een niet-beheerde doel** (onder supervisie alleen)|Stopt van beheerde apps kan worden verzonden gegevens via. Airdrop.|
|**AirDrop** (onder supervisie alleen)|Gebruik van de functie AirDrop voor het uitwisselen van inhoud met apparaten in de buurt toestaan.|
  
###  <a name="compliant-and-noncompliant-apps-ios"></a>Compatibele en niet-compatibele apps (iOS)  
 Hiermee kunt u een lijst opgeven van iOS-apps die in uw bedrijf compatibel of niet compatibel zijn. Vervolgens kunt u rapporten gebruiken om apparaten weer te geven waarop niet-compatibele apps zijn geïnstalleerd en wie de gebruikers van de apparaten zijn.  
  
 U kunt niet zowel compatibele als niet-compatibele apps in hetzelfde configuratie-item opgeven.  
  
#### <a name="to-specify-the-compliant-or-noncompliant-apps-list"></a>De lijst met compatibele of niet-compatibele apps opgeven  
  
1.  Op de pagina **Compatibele en niet-compatibele apps (iOS)** geeft u de volgende gegevens op:  
  
    -   **Lijst met niet-compatibele apps**: selecteer deze optie als u een lijst wilt opgeven met apps die worden gerapporteerd als niet-compatibel als deze worden geïnstalleerd door gebruikers.  
  
    -   **Lijst met compatibele apps**: selecteer deze optie als u een lijst wilt opgeven met apps die gebruikers mogen installeren. Andere geïnstalleerde apps worden gerapporteerd als niet-compatibel.  
  
    -   **Toevoegen**: hiermee voegt u een app toe aan de geselecteerde lijst. Geef een naam van uw keuze op, eventueel de uitgever van de app, en de URL van de app in de App Store.  
  
         Zoek in de iTunes App Store de app die u wilt gebruiken om de URL op te geven.  
  
         Open de pagina van de app en kopieer de URL naar het klembord. U kunt deze nu als de URL gebruiken in de lijst met compatibele apps of de lijst met niet-compatibele apps.  
  
         **Voorbeeld:** Zoek in de store naar de **Microsoft Word voor iPad** app. De URL die u gebruikt, is **https://itunes.apple.com/us/app/microsoft-word-for-ipad/id586447913?mt=8**.  
  
    -   **Bewerken**: hiermee kunt u de naam, de uitgever en de URL van de geselecteerde app bewerken.  
  
    -   **Verwijderen**: hiermee verwijdert u de geselecteerde app uit de lijst.  
  
    -   **Importeren**: hiermee importeert u een lijst met apps die u hebt opgegeven in een bestand met door komma's gescheiden waarden. Gebruik de notatie, toepassingsnaam, uitgever en app-URL in het bestand.  
  
2.  Klik op **Volgende** wanneer u klaar bent.  
  
 U kunt een van de volgende rapporten gebruiken om compatibele en niet-compatibele apps te controleren:  
  
-   **Lijst met niet-compatibele apps en apparaten voor een opgegeven gebruiker**: bevat informatie over gebruikers en hun apparaten waarop apps zijn geïnstalleerd die niet compatibel zijn met een beleid dat u hebt opgegeven.  
  
-   **Overzicht van gebruikers met niet-compatibele apps**: bevat informatie over gebruikers die apps hebben geïnstalleerd die niet compatibel zijn met een beleid dat u hebt opgegeven.  
  
 Zie [Rapportage in System Center Configuration Manager](../../core/servers/manage/reporting.md) voor meer informatie over het gebruik van rapporten.  
  
###  <a name="compliant-and-noncompliant-apps-mac-os-x"></a>Compatibele en niet-compatibele apps (Mac OS X)  
 Hiermee kunt u een lijst opgeven van Mac OS X-apps die in uw bedrijf compatibel of niet compatibel zijn. Vervolgens kunt u rapporten gebruiken om apparaten weer te geven waarop niet-compatibele apps zijn geïnstalleerd en wie de gebruikers van de apparaten zijn.  
  
 U kunt niet zowel compatibele als niet-compatibele apps in hetzelfde configuratie-item opgeven.  
  
#### <a name="to-specify-the-compliant-or-noncompliant-apps-list"></a>De lijst met compatibele of niet-compatibele apps opgeven  
  
1.  Op de pagina **Compatibele en niet-compatibele apps (Mac OS X)** geeft u de volgende gegevens op:  
  
    -   **Lijst met niet-compatibele apps**: selecteer deze optie als u een lijst wilt opgeven met apps die worden gerapporteerd als niet-compatibel als deze worden geïnstalleerd door gebruikers.  
  
    -   **Lijst met compatibele apps**: selecteer deze optie als u een lijst wilt opgeven met apps die gebruikers mogen installeren. Andere geïnstalleerde apps worden gerapporteerd als niet-compatibel.  
  
    -   **Toevoegen**: hiermee voegt u een app toe aan de geselecteerde lijst. Geef een naam van uw keuze op, eventueel de uitgever van de app en de bundel-id van de app.  
  
        > [!TIP]  
        >  Als u de bundel-id van een app wilt vinden, volgt u de volgende stappen op een Mac-computer waarop de app is geïnstalleerd:  
        >   
        >  1.  Open de map waarin de app is geïnstalleerd (bijvoorbeeld **/Toepassingen**)  
        > 2.  Selecteer de *<app-naam\>***.app**-bundel en kies **Pakketinhoud weergeven**  
        > 3.  Open het bestand **Info.plist**  
        > 4.  Controleer de waarde die is gekoppeld aan de sleutel **CFBundleIdentifier**  
        >   
        >  De notatie voor de bundel-id is** com.contoso.appname**  
  
    -   **Bewerken**: hiermee kunt u de naam, de uitgever en de bundel-id van de geselecteerde app bewerken.  
  
    -   **Verwijderen**: hiermee verwijdert u de geselecteerde app uit de lijst.  
  
    -   **Importeren**: hiermee importeert u een lijst met apps die u hebt opgegeven in een bestand met door komma's gescheiden waarden. Gebruik de indeling, app-naam, uitgever en de app-bundel-id in het bestand.  
  
2.  Klik op **Volgende** wanneer u klaar bent.  
  
 U kunt een van de volgende rapporten gebruiken om compatibele en niet-compatibele apps te controleren:  
  
-   **Lijst met niet-compatibele apps en apparaten voor een opgegeven gebruiker**: bevat informatie over gebruikers en hun apparaten waarop apps zijn geïnstalleerd die niet compatibel zijn met een beleid dat u hebt opgegeven.  
  
-   **Overzicht van gebruikers met niet-compatibele apps**: bevat informatie over gebruikers die apps hebben geïnstalleerd die niet compatibel zijn met een beleid dat u hebt opgegeven.  
  
 Zie [Rapportage in System Center Configuration Manager](../../core/servers/manage/reporting.md) voor meer informatie over het gebruik van rapporten.  
  
### <a name="ios-and-mac-os-x-custom-profile-settings"></a>Aangepaste profielinstellingen voor iOS en Mac OS X  
 Gebruik **Aangepaste iOS- en Mac OS X-profielen** om instellingen op iOS- en Mac OS X-apparaten te implementeren die u hebt gemaakt met het [hulpprogramma Apple Configurator](https://itunes.apple.com/us/app/apple-configurator-2/id1037126344?mt=12). Met dit hulpprogramma kunt u veel instellingen configureren die de werking van deze apparaten regelen en kunt u deze instellingen exporteren naar een configuratieprofiel. U kunt dit configuratieprofiel vervolgens importeren naar een aangepast iOS- en Mac OS X-profiel en de instellingen implementeren voor gebruikers en apparaten in uw organisatie.  
  
> [!NOTE]  
>  Controleer of de instellingen die u vanuit het hulpprogramma Apple Configurator exporteert compatibel zijn met de versie van iOS of Mac OS X op de apparaten, waarop u het profiel implementeert. Als u meer wilt weten over het oplossen van problemen bij incompatibele instellingen, zoekt u op de [Apple Developer](https://developer.apple.com/)-website naar 'Configuration Profile Reference' (naslag voor configuratieprofielen) en 'Mobile Device Management Protocol Reference' (naslag voor beheerprotocol voor mobiele apparaten).  
  
#### <a name="to-create-an-ios-and-mac-os-x-custom-profile"></a>Een aangepast profiel voor iOS en Mac OS X maken  
  
1.  Op de pagina **Instellingen van aangepast iOS- en Mac OS X-profiel configureren** van de **wizard Configuratie-item maken** geeft u de volgende informatie op:  
  
    -   **Aangepaste configuratieprofielnaam (weergegeven aan gebruikers)** -Geef een naam voor het beleid, zoals die wordt weergegeven op het apparaat en in Configuration Manager-rapporten.  
  
    -   **Importeren**: kies een bestand dat u met het hulpprogramma Apple Configurator hebt geëxporteerd.  
  
    -   **Configuratieprofieldetails**: bevat het bestand dat u hebt geïmporteerd.  
  
    -   **Niet-compatibele instellingen herstellen** -  
  
         Geef aan of u niet-compatibele configuratie-instellingen wilt corrigeren (indien ondersteund).  
  
    -   **Ernst van niet-naleving voor rapporten**: geef de ernst aan die wordt gerapporteerd als wordt vastgesteld dat het nalevingsbeleid niet compatibel is. De beschikbare ernstniveaus zijn als volgt:  
  
        > [!NOTE]  
        >  Als op een Mac OS X-apparaat de slaapstandmodus is ingeschakeld, kunnen beleidsregels en profielen niet worden afgeleverd of geïnventariseerd. Als gevolg hiervan de Configuration Manager-console mogelijk tijdelijk de beleidsinstellingen van de status fout tot de volgende keer dat het apparaat uit de slaapstand wordt gehaald.  
  
        -   **Geen** apparaten die niet voldoen aan deze compliantieregel niet rapporteren ernst voor Configuration Manager-rapporten.  
  
        -   **Informatie** apparaten die niet voldoen aan deze compliantieregel fouternst van **informatie** voor Configuration Manager-rapporten.  
  
        -   **Waarschuwing** apparaten die niet voldoen aan deze compliantieregel fouternst van **waarschuwing** voor Configuration Manager-rapporten.  
  
        -   **Kritieke** apparaten die niet voldoen aan deze compliantieregel fouternst van **kritieke** voor Configuration Manager-rapporten.  
  
        -   **Kritiek met gebeurtenis** apparaten die niet voldoen aan deze compliantieregel fouternst van **kritieke** voor Configuration Manager-rapporten. Dit ernstniveau wordt ook vastgelegd als een Windows-gebeurtenis in het logboek voor toepassingsgebeurtenissen.  
  
#### <a name="how-to-create-a-configuration-profile-file"></a>Een configuratieprofielbestand maken  
 U kunt het configuratieprofielbestand dat door het aangepaste beleid wordt gebruikt op twee manieren maken:  
  
-   Exporteer het bestand (met de extensie **.mobileconfig**) uit het hulpprogramma Apple Configurator.  
  
-   Schrijf het bestand zelf met behulp van het bijbehorende schema van de [Apple Configuration Profile Key Reference](https://developer.apple.com/library/ios/featuredarticles/iPhoneConfigurationProfileRef/Introduction/Introduction.html).  
  
###  <a name="kiosk-mode-ios"></a>Kioskmodus (iOS)  
 Met de kioskmodus kunt u een apparaat zo vergrendelen dat alleen bepaalde functies werken. U kunt bijvoorbeeld toestaan dat een apparaat slechts één beheerde app uitvoert die u opgeeft, of kunt u de volumeknoppen op een apparaat uitschakelen. Deze instellingen kunnen worden gebruikt voor een demonstratiemodel van een apparaat of voor een apparaat dat is toegewezen aan slechts één functie, zoals een verkooppuntapparaat.  
  
#### <a name="to-configure-kiosk-mode-for-ios-devices"></a>Kioskmodus configureren voor iOS-apparaten  
  
1.  Op de pagina **Instellingen van de kioskmodus voor iOS-apparaten** van de **wizard Configuratie-item maken** geeft u de volgende informatie op:  
  
    -   **App selecteren**: selecteer de app die mag worden uitgevoerd wanneer het apparaat zich in kioskmodus bevindt. Er mogen geen andere apps op het apparaat worden uitgevoerd. U kunt kiezen uit:  
  
        -   **Beheerde app**: klik op Bladeren en selecteer vervolgens een beheerde app.  
  
        -   **Store-app**: geef de URL op naar een app in de app store en klik vervolgens op **App-id ophalen** om het veld **App-id** in te vullen.  
  
         De app-URL opzoeken:  
  
        -   Gebruik een zoekmachine om de app te zoeken die u wilt gebruiken in de iTunes App Store en open de pagina voor de app.  
  
        -   Kopieer de URL van de pagina en geef hiermee de app op die u in kioskmodus wilt uitvoeren.  
  
        -   **Voorbeeld:** Zoeken naar **Microsoft Word voor iPad**. De URL die u gebruikt, is **https://itunes.apple.com/us/app/microsoft-word-for-ipad/id586447913?mt=8**.  
  
    -   **Touchscreen**: hiermee wordt het aanraakscherm op het apparaat in- of uitgeschakeld.  
  
    -   **Schermrotatie**: hiermee wordt de wijziging van de schermstand wanneer u het apparaat roteert, in- of uitgeschakeld.  
  
    -   **Volumeknoppen**: hiermee wordt het gebruik van de volumeknoppen op het apparaat in- of uitgeschakeld.  
  
    -   **Schakelaar voor belsignaal**: hiermee wordt de schakelaar voor het belsignaal (dempen) op het apparaat in- of uitgeschakeld.  
  
    -   **Knop voor slaapstand en ontwaken van scherm**: hiermee wordt de knop voor slaapstand/ontwaken van het scherm in- of uitgeschakeld op het apparaat.  
  
    -   **Automatisch vergrendelen**: hiermee wordt automatische vergrendeling van het apparaat in- of uitgeschakeld.  
  
    -   **Mono-audio**: hiermee wordt de toegankelijkheidsinstelling **Mono-audio** in- of uitgeschakeld.  
  
    -   **Voice-over**: hiermee wordt de toegankelijkheidsinstelling **Voice-over** die tekst op het apparaatscherm voorleest, in- of uitgeschakeld.  
  
    -   **Aanpassingen aan voice-over**: hiermee worden aanpassingen aan de functie Voice-over (bijvoorbeeld hoe snel schermtekst wordt voorgelezen) in- of uitgeschakeld.  
  
    -   **Zoomen**: hiermee wordt de toegankelijkheidsinstelling **Zoomen** waarmee u via aanraken kunt in- en uitzoomen op het apparaatscherm, in- of uitgeschakeld.  
  
    -   **Aanpassingen aan zoomen**: hiermee worden aanpassingen aan de zoomfunctie in- of uitgeschakeld.  
  
    -   **Kleuren omkeren**: hiermee wordt de toegankelijkheidsinstelling **Kleuren omkeren** die het scherm aanpast voor gebruikers met een beperkt gezichtsvermogen, in- of uitgeschakeld.  
  
    -   **Aanpassingen aan kleuren omkeren**: hiermee worden aanpassingen aan de functie Kleuren omkeren in- of uitgeschakeld.  
  
    -   **Ondersteund aanraken**: hiermee wordt de toegankelijkheidsinstelling **Ondersteunend aanraken**, waarmee gebruikers schermbewegingen kunnen uitvoeren die moeilijk voor hen kunnen zijn, in- of uitgeschakeld.  
  
    -   **Aanpassingen aan ondersteund aanraken**: hiermee worden aanpassingen aan de functie Ondersteunend aanraken in- of uitgeschakeld.  
  
    -   **Spraakselectie**: hiermee worden de toegankelijkheidsinstellingen voor **Selectie uitspreken**, waarmee door u geselecteerde tekst wordt voorgelezen, in- of uitgeschakeld.  
  
    -   **Niet-compatibele instellingen herstellen**: geef aan of u niet-compatibele configuratie-instellingen wilt corrigeren (indien ondersteund).  
  
    -   **Ernst van niet-naleving voor rapporten**: geef de ernst aan die wordt gerapporteerd als wordt vastgesteld dat het nalevingsbeleid niet compatibel is. U kunt kiezen uit de volgende ernstniveaus:  
  
        -   **Geen** apparaten die niet voldoen aan deze compliantieregel niet rapporteren ernst voor Configuration Manager-rapporten.  
  
        -   **Informatie** apparaten die niet voldoen aan deze compliantieregel fouternst van **informatie** voor Configuration Manager-rapporten.  
  
        -   **Waarschuwing** apparaten die niet voldoen aan deze compliantieregel fouternst van **waarschuwing** voor Configuration Manager-rapporten.  
  
        -   **Kritieke** apparaten die niet voldoen aan deze compliantieregel fouternst van **kritieke** voor Configuration Manager-rapporten.  
  
        -   **Kritiek met gebeurtenis** apparaten die niet voldoen aan deze compliantieregel fouternst van **kritieke** voor Configuration Manager-rapporten. Dit ernstniveau wordt ook vastgelegd als een Windows-gebeurtenis in het logboek voor toepassingsgebeurtenissen.  
  
## <a name="see-also"></a>Zie ook  
 [Configuratie-items voor apparaten die worden beheerd zonder de System Center Configuration Manager-client](../../compliance/deploy-use/configuration-items-for-devices-managed-without-the-client.md)
