---
title: Archiveren van wat nieuw hybride MDM is | Microsoft Docs
description: Archief van afgelopen functies voor mobiele apparaten beschikbaar voor hybride implementaties met System Center Configuration Manager en Intune.
ms.custom: na
ms.date: 06/30/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: configmgr-hybrid
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 4c27b161-9eb7-4cdd-b469-d8eb27e71aea
author: Mtillman
ms.author: mtillman
manager: angrobe
ROBOTS: NOINDEX, NOFOLLOW
ms.openlocfilehash: 0abd1cdcf44e778c91bacb8011efd711818ce2e9
ms.sourcegitcommit: 51fc48fb023f1e8d995c6c4eacfda7dbec4d0b2f
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 08/07/2017
---
# <a name="past-hybrid-features-with-system-center-configuration-manager-and-microsoft-intune"></a>Afgelopen hybride functies met System Center Configuration Manager en Microsoft Intune

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*

Dit artikel bevat informatie op het mobiele apparaat van afgelopen management (MDM)-functies die beschikbaar zijn voor hybride implementaties met System Center Configuration Manager en Microsoft Intune.  

##  <a name="compatibility-with-configuration-manager-versions"></a>Compatibiliteit met versies van Configuration Manager  

 Elke sectie van dit artikel vindt u hybridefuncties onder 3 verschillende categorieën. Gebruik de volgende richtlijnen om te bepalen of de functies in elke categorie compatibel is met verschillende versies van Configuration Manager:  

|Functie categorieën|
|-|  
|**Nieuw in Microsoft Intune** -In het algemeen alle functies die worden vermeld in deze categorie moeten samenwerken met alle versies van de Configuration Manager met inbegrip van System Center 2012 R2 Configuration Manager-versies, aangezien deze functies alleen de Intune-service nodig en niet aanvullende functionaliteit in Configuration Manager hoeven.<br /><br /> **Nieuw in Configuration Manager Technical Preview** -alle functies vermeld in deze categorie alleen werken met de opgegeven Technical Preview-versie. Als u wilt deze functies uit te proberen, moet u de Technical Preview-versie die is opgegeven in de beschrijving van de functie installeren. Zie voor meer informatie [Technical Preview voor System Center Configuration Manager](../../core/get-started/technical-preview.md).<br /><br /> **Nieuw in Configuration Manager (huidige vertakking)** -alle functies vermeld in deze categorie alleen werken met de opgegeven versie van Configuration Manager (huidige vertakking), zoals versie 1511 of 1602. Als u een oudere versie van Configuration Manager voor uw hybride implementatie gebruikt, moet u upgraden naar de Configuration Manager (huidige vertakking) versie opgegeven in de beschrijving van de functie. Zie voor meer informatie [upgraden naar System Center Configuration Manager](../../core/servers/deploy/install/upgrade-to-configuration-manager.md).|  

## <a name="december-2016"></a>December 2016

### <a name="new-in-microsoft-intune"></a>Nieuw in Microsoft Intune

- **Multi-factor authentication (MFA) tijdens de inschrijving wordt verplaatst naar de Azure-portal**

  Eerder, gaat u naar de Intune-console of de Configuration Manager-console in te stellen van MFA voor Intune inschrijvingen. Met deze functie van bijgewerkte u nu aanmelden bij de [Microsoft Azure-portal] (https://manage.windowsazure.com) met behulp van uw Intune-referenties en configureren van MFA-instellingen via Azure AD. Zie voor meer informatie, [multi-factor authentication voor Microsoft Intune] (https://aka.ms/mfa_ad).

- **Bedrijfsportal-app voor Android is nu beschikbaar in China**

  De bedrijfsportal-app voor Android is nu beschikbaar in China. Wegens het ontbreken van Google Play Store in China, moeten Android-apparaten ophalen met apps Chinees app marktplaatsen. De bedrijfsportal-app voor Android is beschikbaar voor downloaden op de volgende opgeslagen:

  - [Baidu](https://go.microsoft.com/fwlink/?linkid=836946)
  - [Huawei](https://go.microsoft.com/fwlink/?linkid=836948)
  - [Tencent](https://go.microsoft.com/fwlink/?linkid=836949)
  - [Wandoujia](https://go.microsoft.com/fwlink/?linkid=836950)
  - [Xiaomi](https://go.microsoft.com/fwlink/?linkid=836947)

  De bedrijfsportal-app voor Android maakt gebruik van Google Play Services om te communiceren met de Microsoft Intune-service. Omdat de Google Play Services zijn nog niet beschikbaar in China, kan een van de volgende taken uitvoeren tot 8 uur duren.

  | Configuration Manager-beheerconsole | Intune-bedrijfsportal-app voor Android | Intune bedrijfsportal-Website |
  |----|----|----|      
  | Buiten gebruik stellen/wissen (alle gegevens verwijderen)   | Een extern apparaat verwijderen | Apparaat (lokaal en extern) verwijderen |
  | Buiten gebruik stellen/wissen (bedrijfsgegevens verwijderen)   | Apparaat opnieuw instellen | Apparaat opnieuw instellen|
  | Nieuwe of bijgewerkte app-implementaties | Installeren van beschikbare LOB-apps | Wachtwoordcode opnieuw instellen van apparaat|
  | Vergrendelen op afstand | | |
  | Wachtwoordcode opnieuw instellen | | |        


## <a name="november-2016"></a>November 2016

### <a name="new-in-microsoft-intune"></a>Nieuw in Microsoft Intune

- **Nieuwe Microsoft Intune-bedrijfsportal beschikbaar voor Windows 10-apparaten**

  Microsoft heeft een nieuwe [bedrijfsportal-app voor Windows 10-apparaten](https://www.microsoft.com/store/apps/9wzdncrfj3pz). Deze app die gebruikmaakt van de nieuwe Windows 10 Universal-indeling, biedt een bijgewerkte gebruiker-ervaring die identiek is op alle Windows 10-apparaten, PC en mobiele zowel terwijl nog steeds dezelfde functionaliteit van de vorige bedrijfsportal-apps.

  De nieuwe app maakt gebruik van de platformfuncties, zoals het eenmalige aanmelding (SSO) en verificatie op basis van een certificaat op Windows 10-apparaten. De app is beschikbaar als een upgrade voor de bestaande bedrijfsportal voor Windows 8.1 en Windows Phone 8.1-bedrijfsportal geïnstalleerd vanuit de Windows Store. Voor meer informatie gaat u naar de [Intune Support-teamblog](http://aka.ms/intunecp_universalapp).

  De nieuwe bedrijfsportal-app worden ook weergegeven voor alle Windows Store voor bedrijven-toepassingen die zijn gemarkeerd **beschikbaar** in de Configuration Manager-console.


### <a name="new-in-configuration-manager-current-branch"></a>Nieuw in Configuration Manager (huidige vertakking)

De volgende functies die eerder beschikbaar in Configuration Manager Technical Preview-versies waren zijn nu beschikbaar in hybride implementaties met Intune en Configuration Manager (huidige vertakking) versie 1610.

* [Extra instellingen en een verbeterde ervaring voor configuratie-items](/sccm/core/plan-design/changes/whats-new-in-version-1610#new-compliance-settings-for-configuration-items)
* [Aanvullende instellingen voor DEP-profielen](whats-new-hybrid-archive.md#new-in-configuration-manager-technical-preview-1609)
* [Betaalde apps in Windows Store voor bedrijven](/sccm/apps/deploy-use/manage-apps-from-the-windows-store-for-business)
* [Systeemeigen verbindingstypen voor Windows 10 VPN-profielen](whats-new-hybrid-archive.md#new-in-configuration-manager-technical-preview-1609)
* [Intune naleving grafieken](/sccm/protect/deploy-use/create-compliance-policy#monitor-the-compliance-policy)
* [Aanvraag voor het beleid voor synchronisatie van console](/sccm/mdm/deploy-use/sync-intune-device)
* [Configuratie-instellingen voor Windows Defender](/sccm/compliance/deploy-use/create-configuration-items-for-windows-8.1-and-windows-10-devices-managed-without-the-client#windows-defender)

De volgende aanvullende hybridefuncties zijn ook opgenomen in versie 1610 van Configuration Manager (huidige vertakking):

- **Toenemend aantal geregistreerde apparaten**

  U kunt nu gebruikers maximaal 15 apparaten kunnen inschrijven inschakelen. De vorige limiet is 5 apparaten per gebruiker.


- **Ondersteuning voor extra beveiliging**

  Naast volledige beheerder hebben de volgende ingebouwde beveiligingsrollen nu volledige toegang tot de items in het knooppunt alle apparaten in Bedrijfseigendom, inclusief apparaten Predeclared, iOS-Inschrijvingsprofielen en Windows-Inschrijvingsprofielen:

    - Asset Intelligence-beheerder
    - Toegang tot bedrijfsbronnen

  Alleen-lezen toegang tot deze gebieden van de Configuration Manager-console nog steeds te krijgen tot de alleen-Lezenanalist-rol.

- **Automatische trigger VPN-toegang van apps voor Windows-gegevensbeveiliging**

  U kunt een Windows-gegevensbeveiliging primair domein toevoegen aan Windows 10 VPN-profielen zorgt ervoor dat alle gekoppelde apps aan een VPN-verbinding automatisch wordt geactiveerd wanneer ze worden uitgevoerd op het apparaat. Deze optie is alleen beschikbaar bij het kiezen van een systeemeigen verbindingstype.

- **Voorwaardelijke toegang voor Windows 10 VPN-profielen**

    U kunt nu Windows 10 vereisen apparaten zijn ingeschreven in Azure Active Directory aan het beleid voldoen om VPN-toegang tot en met Windows 10 VPN-profielen die zijn gemaakt in de Configuration Manager-console. Dit is mogelijk via de nieuwe **voorwaardelijke toegang inschakelen voor deze VPN-verbinding** selectievakje op de pagina methode voor verificatie in de wizard VPN-profiel en de eigenschappen van de VPN-profiel voor Windows 10 VPN-profielen. Deze optie is alleen beschikbaar bij het kiezen van een systeemeigen verbindingstype.

    U kunt ook een apart certificaat voor eenmalige aanmelding verificatie opgeven als u voorwaardelijke toegang voor het profiel inschakelen.

## <a name="october-2016"></a>Oktober 2016

### <a name="new-in-microsoft-intune"></a>Nieuw in Microsoft Intune

De volgende Intune-functies die zijn geïntroduceerd in oktober 2016 werken in hybride implementaties.

- **Voorwaardelijke toegang voor mobile application management**

  U kunt toegang tot Exchange Online beperken zodat toegang afkomstig zijn uit apps die ondersteuning bieden voor Intune mobile application management-beleid zoals Outlook. [Deze nieuwe functie](/intune/deploy-use/allow-policy-managed-apps-access-to-o365) paren van perfect met beleid voor Intune mobile app management (MAM) als u toegang tot de ingebouwde e-mailclients of andere apps die niet zijn geconfigureerd met Intune MAM-beleid kunt blokkeren. Dit zorgt ervoor dat uw gebruikers gebruikmaken van de gegevens van uw organisatie met apps die kunnen worden beveiligd met Intune MAM. U kunt aan de slag in de Intune mobile Application management via de Azure-portal. Zoek naar de nieuwe sectie voorwaardelijke toegang op de blade 'Instellingen'.

-   **Intune App Wrapping Tool voor Android**

  U kunt uw apps Intune mobile application management (MAM)-beleid gebruiken met behulp van de Intune App Wrapping Tool kunt inschakelen.

- **Android Samsung KNOX Standard compatibiliteit met Intune**

  Bepaalde modellen van het telefoonnummer Samsung Galaxy Ace kunnen niet worden beheerd door Intune als Samsung KNOX Standard-apparaten. Wanneer u deze apparaten met Intune inschrijft, wordt deze in plaats daarvan worden beheerd als een standaard Android-apparaten.

  De model-nummers van invloed op een zijn:

  - SM-G313HU
  - SM-G313HY
  - SM-G313M
  - SM-G313MY
  - SM-G313U

  U en uw eindgebruikers hoeft er geen verdere actie te ondernemen. Ga naar de Samsung KNOX-website voor meer informatie.

### <a name="new-in-configuration-manager-technical-preview-1610"></a>Nieuw in Configuration Manager Technical Preview 1610

De volgende nieuwe hybridefuncties zijn geïntroduceerd in oktober 2016 voor Configuration Manager Technical Preview 1610.

- **Aanvragen van een beleid voor synchronisatie van de beheerconsole**

  U kunt een beleid synchronisatie op een ingeschreven mobiele apparaat aanvragen via de Configuration Manager-console, in plaats van hoeven aan te vragen van de synchronisatie in de bedrijfsportal-app op het apparaat zelf. Dit is een nieuwe actie aangeroepen **synchronisatie-aanvraag verzenden** in het menu Acties extern apparaat die wordt weergegeven in het lint wanneer een mobiel apparaat wordt geselecteerd in het knooppunt apparaten.

- **Windows Defender configuratie-instellingen**

  U kunt nu instellingen voor Windows Defender-client configureren op Intune ingeschreven Windows 10-computers met configuratie-items in de Configuration Manager-console. Er is een nieuwe instellingsgroep genaamd **Windows Defender** in de wizard Configuratie-Item. Houd er rekening mee dat dit alleen op Windows 10 versie 1511 en hoger wordt ondersteund.


### <a name="new-in-configuration-manager-current-branch"></a>Nieuw in Configuration Manager (huidige vertakking)

Er zijn geen nieuwe hybridefuncties zijn geïntroduceerd in augustus 2016 voor Configuration Manager (huidige vertakking).

## <a name="september-2016"></a>September 2016

### <a name="new-in-microsoft-intune"></a>Nieuw in Microsoft Intune

De volgende Intune-functies die zijn geïntroduceerd in September 2016 werken in hybride implementaties.

- **Toevoeging van 'Meldingen' aan de bedrijfsportal voor Android**

  Een nieuw meldingspictogram is toegevoegd aan de bedrijfsportal voor Android op de startpagina. Op dit pictogram te tikken heeft toegang tot de pagina meldingen, die uw eindgebruikers geeft alle items die aandacht in de bedrijfsportal-app, zoals het apparaat niet-compatibele, inschrijvingsupdates en activering van inschrijvingen vereisen. De iOS-bedrijfsportal-app al is meldingen optreden. Om de nieuwe meldingen pagina middelen die gebruiker won't pagina wordt weergegeven het instellen van bedrijfstoegang telkens wanneer ze starten of hervatten van de bedrijfsportal, zolang het apparaat is al geregistreerd. Als u de richtlijnen van uw eigen eindgebruiker maakt, is het raadzaam om bij te werken uw documentatie bij zodat deze wijziging. Bijgewerkte schermafbeeldingen vindt [hier](https://aka.ms/androidcpupdate).

- **Wijzigingen in de ondersteuning voor de iOS-bedrijfsportal-app**

  Alle gebruikers van de Microsoft Intune-bedrijfsportal-app voor iOS moeten nu naar de nieuwste versie. Nieuwe gebruikers zich kunnen alleen de nieuwste versie downloaden en bestaande gebruikers moeten bijwerken naar. De meest recente versie vereist iOS 8.0 of hoger, zodat apparaten met oudere versies van iOS kunnen niet de bedrijfsportal gebruiken of registreren totdat ze hun apparaat naar iOS 8.0 of hoger werken en werk vervolgens de bedrijfsportal-app naar de nieuwste versie. Geregistreerde apparaten met een versie lager dan iOS 8.0 blijven worden beheerd met en vermeld in de Intune-beheerconsole.

- **Feedbackknop toegevoegd aan Windows Phone 8.1-bedrijfsportal-app**

  De Windows Phone 8.1-bedrijfsportal-app kan eindgebruikers feedback over de app met behulp van een nieuwe knop voor "feedback verzenden" te verzenden. Ga voor de knop gebruikers tikken op het menu 'drie punten' in de rechterbenedenhoek van het scherm van de app bedrijfsportal en tik vervolgens op **feedback verzenden**. De verzamelde, geanonimiseerde feedback helpt Microsoft bij het verbeteren van de bedrijfsportal-app-ervaring voor gebruikers.

### <a name="new-in-configuration-manager-technical-preview-1609"></a>Nieuw in Configuration Manager Technical Preview 1609

De volgende nieuwe hybridefuncties zijn geïntroduceerd in September 2016 voor Configuration Manager Technical Preview 1609.

- **Extra instellingen en een verbeterde ervaring voor configuratie-Item-instellingen**

  Nieuwe instellingen voor Android, iOS en Windows zijn toegevoegd en alleen de instellingen die gelden voor de platforms die u op de pagina ondersteunde Platforms selecteert worden weergegeven in de wizard. Zie voor meer informatie [nieuwe instellingen voor naleving voor configuratie-items in TP 1609](/sccm/core/get-started/capabilities-in-technical-preview-1609#new-compliance-settings-for-configuration-items).

- **Aanvullende instellingen voor DEP-profielen**

  Touch id, ApplePay en zoomen zijn toegevoegd als configureerbare instellingen in DEP-profielen voor iOS-apparaten.

- **Betaalde Apps in Windows Store voor bedrijven**

  U kunt nu betaald en beschikbare toepassingen naar Windows Store voor bedrijven toevoegen en implementeren voor gebruikers in uw organisatie. Zie voor meer informatie [verbeteringen in Windows Store voor bedrijven in TP 1609](/sccm/core/get-started/capabilities-in-technical-preview-1609#enhancements-to-windows-store-for-business-integration-with-configuration-manager).

- **Systeemeigen verbindingstypen voor Windows 10 VPN-profielen**

  U kunt nu Windows 10 VPN-profielen voor MDM met Microsoft Automatic, IKEv2 en PPTP verbindingstypen in de Configuration Manager-console maken zonder met OMA-URI.

- **Intune naleving grafieken**

  Compatibiliteit en top redenen voor compatibiliteit met nieuwe grafieken onder de werkruimte voor bewaking, kunt u een overzicht van de algehele apparaat ophalen. Zie voor meer informatie [Intune naleving grafieken in TP 1609](/sccm/core/get-started/capabilities-in-technical-preview-1609#intune-compliance-charts).

### <a name="new-in-configuration-manager-current-branch"></a>Nieuw in Configuration Manager (huidige vertakking)

De volgende nieuwe functie geïntroduceerd in September 2016 is beschikbaar voor hybride implementaties met Microsoft Intune en Configuration Manager versie 1606 (huidige vertakking).

- **iOS-10-ondersteuning**

  Als u profielen of configuratie-items die zijn gericht op alle platforms van iOS hebt, wordt deze ook naar iOS 10 gepusht. We hebben ook een update voor Configuration Manager versie 1606, waarmee u doel profielen en configuratie-items voor afzonderlijke iOS platforms, zoals iOS 10 uitgebracht. U kunt de update installeren met de Configuration Manager-beheerconsole op **beheer > overzicht > Cloudservices > Updates en onderhoud**. U vindt meer informatie over de update op [http://support.microsoft.com/kb/3192616](http://support.microsoft.com/kb/3192616).

## <a name="august-2016"></a>Augustus 2016

### <a name="new-in-microsoft-intune"></a>Nieuw in Microsoft Intune

De volgende Intune-functies die zijn geïntroduceerd in augustus 2016 werken in hybride implementaties.

- **Android-7 ondersteuning in de bedrijfsportal-app**

  De Intune-bedrijfsportal-app voor Android biedt 'day 0'-ondersteuning voor het toekomstige Android 7.0-besturingssysteem voor mobiele apparaten.

- **Google verwijdert externe wachtwoordcode opnieuw instellen voor Android 7.0-apparaten**

  Google verwijdert de mogelijkheid van IT-beheerders en eindgebruikers de wachtwoordcode van Android 7.0-apparaten op afstand opnieuw instellen. Eerder IT-beheerders op afstand opnieuw instellen van een gebruiker de wachtwoordcode en eindgebruikers hun wachtwoordcodes van de bedrijfsportal-website opnieuw instellen.

- **Beleid voor toegestane en geblokkeerde apps voor Samsung KNOX Standard-apparaten**

  U kunt nu een aangepast beleid voor Samsung KNOX Standard-apparaten waarmee u bij het maken van een van de volgende configureren:

  - Een lijst met apps die kunnen worden uitgevoerd op het apparaat. Zelfs als geïnstalleerd, kan een app die is gedefinieerd in de lijst met geblokkeerde kan niet worden geactiveerd op het apparaat.
  - Een lijst met apps die gebruikers van het apparaat kunnen installeren uit de Google Play store. Geen andere apps kunnen worden geïnstalleerd vanuit de store.

  Deze instellingen kunnen alleen worden gebruikt door apparaten met Samsung KNOX Standard. Zie voor meer informatie [aangepast beleid gebruiken voor het toestaan en blokkeren van apps voor Samsung KNOX Standard-apparaten](/intune/deploy-use/custom-policy-to-allow-and-block-samsung-knox-apps).

- **Feedbackkoppeling van de bedrijfsportal naar Microsoft**

   De website van de bedrijfsportal kan eindgebruikers tikken op een nieuwe koppeling 'Feedback' onderaan de pagina om feedback te verzenden naar Microsoft over hun ervaringen met de site. De verzamelde, geanonimiseerde feedback helpt Microsoft bij het verbeteren van de bedrijfsportal-website-ervaring voor gebruikers.

- **Minimale iOS Managed Browser-versie is bijgewerkt naar 8.0**

  De Microsoft Intune Managed Browser-app voor iOS is bijgewerkt ter ondersteuning van apparaten met iOS 8.0 of hoger. Terwijl iOS 7.1-apparaten nog steeds de bestaande Managed Browser-app gebruiken kunnen, kunt u uw gebruikers te werken naar iOS 8.0 of hoger om toegang te kunnen profiteren van nieuwe functies van Managed Browser.

### <a name="new-in-configuration-manager-technical-preview"></a>Nieuw in Configuration Manager Technical Preview

Geen nieuwe hybridefuncties zijn geïntroduceerd in augustus 2016 voor Configuration Manager Technical Preview.

### <a name="new-in-configuration-manager-current-branch"></a>Nieuw in Configuration Manager (huidige vertakking)

Er zijn geen nieuwe hybridefuncties zijn geïntroduceerd in augustus 2016 voor Configuration Manager (huidige vertakking).

## <a name="july-2016"></a>Juli 2016

### <a name="new-in-microsoft-intune"></a>Nieuw in Microsoft Intune

De volgende Intune-functies die zijn geïntroduceerd in juli 2016 werken in hybride implementaties.

- **Xamarin SDK voor Intune-apps is beschikbaar**

  Het onderdeel Intune App SDK Xamarin kunt u de Intune mobile app management-functies in uw mobiele iOS- en gebouwd met Xamarin Android-apps inschakelen. U vindt het onderdeel in de [Xamarin store](https://components.xamarin.com/view/Microsoft.Intune.MAM) of op de [Microsoft Intune Github-pagina](https://github.com/msintuneappsdk).

- **Verbeterde gebruikerservaring bij het inschrijven van Windows-apparaten**

  Wanneer u voorwaardelijke toegang gebruikt, zijn de stappen voor inschrijving voor Windows 8.1, Windows 10 Desktop en Windows 10 Mobile verbeterd op de bedrijfsportalwebsite. Gebruikers zien nu de afzonderlijke **apparaatinschrijving** en **Workplace Join** stappen, waardoor het gemakkelijker wordt om de status van hun apparaat te bekijken en het proces wordt voltooid wanneer er een fout van Workplace Join (WPJ). De afzonderlijke stappen zijn ook verwacht voor het vereenvoudigen van het proces voor probleemoplossing voor IT-beheerders. Voorheen wanneer eindgebruikers probeerden in te schrijven en alle inschrijvingsstappen waren geslaagd behalve WPJ, het ingeschreven apparaat weergegeven niet in de lijst met apparaten voor gebruikers, wat verwarrend was voor gebruikers.

 - **Volledig wissen nu beschikbaar voor Windows 10-apparaten**

    Windows 10-pc's en laptops ingeschreven als mobiele apparaten kunnen worden gewist om het apparaat opnieuw instellen op de fabrieksinstellingen. Zie voor meer informatie [het beveiligen van uw apparaten met wissen op afstand](/sccm/mdm/deploy-use/wipe-lock-reset).

- **Wijzigingen in de apparaatregistratiebeheeraccounts in de iOS-bedrijfsportal-app**

  Ter verbetering van prestaties en schaalbaarheid, weergegeven Intune niet meer alle Device Enrollment Managers (DEM)-apparaten in het deelvenster mijn apparaten van de iOS-bedrijfsportal-app. Alleen het lokale apparaat uitvoeren van de app wordt weergegeven en wel alleen als het is geregistreerd via de bedrijfsportal-app.

  De DEM-gebruiker kan acties op het lokale apparaat uitvoeren, maar extern beheer van andere geregistreerde apparaten kan alleen worden uitgevoerd vanuit de Intune-beheerconsole. Bovendien is het gebruik in Intune van DEM-accounts met het Apple Device Enrollment Program of het hulpprogramma Apple Configurator. Deze twee registratiemethoden bieden al ondersteuning voor gebruikersloze registratie voor gedeelde iOS-apparaten.

  Gebruik alleen DEM-accounts wanneer gebruikersloze registratie voor gedeelde apparaten niet beschikbaar is. Zie voor meer informatie [inschrijven van apparaten in Bedrijfseigendom met de Apparaatinschrijvingsbeheerder in Microsoft Intune](../deploy-use/enroll-devices-with-device-enrollment-manager.md).

- **Wijzigingen in de Android-bedrijfsportal-app**

  Als Android-eindgebruikers ziet een vereist certificaat ontbreekt in een foutbericht dat hun apparaat, tik ze op een knop 'Het oplossen van dit' als u de stappen voor het installeren van het ontbrekende certificaat weer te geven. Als gebruikers de stappen hebt uitgevoerd, maar een extra 'ontbrekend certificaat' Zie foutbericht wordt weergegeven, wordt gevraagd contact opnemen met hun IT-beheerder en geef deze koppeling klikt, waarin staat beschreven waarmee IT-beheerders kunt los het certificaatprobleem.

- **Beperken van extern geladen app-installaties op ingeschreven Android-apparaten**

  Android-apparaten kunnen geen toepassingen meer installeren via de bedrijfsportalwebsite tenzij de apparaten zijn ingeschreven bij Intune via de Intune-bedrijfsportal-app voor Android.


### <a name="new-in-configuration-manager-technical-preview"></a>Nieuw in Configuration Manager Technical Preview

Er zijn geen nieuwe hybridefuncties hebt is geïntroduceerd in juli 2016 voor Configuration Manager Technical Preview.

### <a name="new-in-configuration-manager-current-branch"></a>Nieuw in Configuration Manager (huidige vertakking)

De volgende functies die eerder beschikbaar in Configuration Manager Technical Preview-versies waren zijn nu beschikbaar in hybride implementaties met Intune en Configuration Manager (huidige vertakking) versie 1606.

* Zoeken, beheren en distribueren van Windows Store voor bedrijven-apps voor Windows 10-apparaten van de Configuration Manager-console ([1604](#new-in-1604-technical-preview))
*   SmartLock-instelling voor Android-apparaten ([1604](#new-in-1604-technical-preview))
*   App geactiveerd VPN voor Windows 10-apparaten ([1605](#new-in-1605-technical-preview))
*   Nieuwe ervaring voor acties extern apparaat ([1605](#new-in-1605-technical-preview))
*   Windows Store voor bedrijven-apps ([1605](#new-in-1605-technical-preview))
*   Algemene verbeteringen van de volume-aankoopprogramma gekochte apps ([1605](#new-in-1605-technical-preview))
*   Windows-gegevensbeveiliging (OHW) ([1605](#new-in-1605-technical-preview))
*   Vooraf declareren van apparaten in Bedrijfseigendom met IMEI-nummer of iOS-serienummer ([1605](#new-in-1605-technical-preview))
*   Apparaten automatisch categoriseren in verzamelingen ([1606](#new-in-1606-technical-preview))

Zie voor informatie over de nieuwe functionaliteit, de documentatie voor de opgegeven Technical Preview-versie.

## <a name="june-2016"></a>Juni 2016

### <a name="new-in-microsoft-intune"></a>Nieuw in Microsoft Intune
De volgende Intune-functies die zijn geïntroduceerd in juni 2016 werken in hybride implementaties.

- **Servicestatus van Intune** servicestatusgegevens voor Intune is verplaatst naar een centrale locatie met andere Microsoft-services. U vindt deze informatie nu in de Office 365-beheerportal onder Servicestatus. Zie voor meer informatie dit [blogbericht](https://blogs.technet.microsoft.com/enterprisemobility/2016/04/28/intune-service-health-is-now-available-in-the-office-365-portal/).

- **Verbeterde Windows 10 enterprise data beleid ervaring voor configuratie**

  Intune heeft nu een verbeterde ervaring voor het configureren van Windows 10 information protection-beleid. Verbeteringen bestaan onder andere betere methoden voor het maken van app-regels, netwerkdefinities en andere Windows Information Protection-instellingen opgeven. Zie voor meer informatie, [maken van een Windows-beveiliging (OHW)-beleid met Microsoft Intune](https://technet.microsoft.com/itpro/windows/keep-secure/create-wip-policy-using-intune).

- **Cisco ISE netwerktoegangscontrolebeleid voor Intune**

  Klanten die Cisco Identity Service Engine (ISE) 2.1 gebruiken en Microsoft Intune ook gebruiken, kunnen een netwerktoegangsbeleid instellen in ISE. Met dit beleid, apparaten die verbinding moeten maken met het netwerk via Wi-Fi of VPN moeten voldoen aan de volgende voorwaarden voordat ze toegang krijgen:

  - Moet worden beheerd door Intune
  - Moet voldoen aan geïmplementeerd Intune-nalevingsbeleid

  Eindgebruikers van niet-compatibele apparaten wordt gevraagd om u te registreren en nalevingsproblemen op te lossen om toegang te krijgen.

- **Voorwaardelijke toegang voor de browser**

  U kunt beleid voor voorwaardelijke toegang instellen voor Exchange Online en SharePoint Online, zodat deze alleen toegankelijk zijn via ondersteunde webbrowsers op beheerde en compatibele iOS en Android-apparaten. Eindgebruikers die proberen aan te melden bij Outlook Web Access (OWA) en SharePoint-sites met iOS- en Android-apparaten wordt gevraagd hun apparaat inschrijven bij Intune en eventuele problemen te lossen niet-naleving voordat ze kunnen aanmelding worden voltooid. Zie voor meer informatie.

  * [Toegang tot e-mail beperken bij Exchange Online en nieuwe Exchange Online Dedicated met Microsoft Intune](https://docs.microsoft.com/intune/deploy-use/restrict-access-to-exchange-online-with-microsoft-intune)
  * [Toegang tot SharePoint Online beperken met Microsoft Intune](https://docs.microsoft.com/intune/deploy-use/restrict-access-to-sharepoint-online-with-microsoft-intune)

- **Dynamics CRM Online biedt ondersteuning voor voorwaardelijke toegang**

  U kunt beleid voor voorwaardelijke toegang voor Dynamics CRM Online instellen zodat deze alleen toegankelijk is voor beheerde en compatibele iOS en Android-apparaten. Eindgebruikers die proberen aan te melden bij de mobiele app Dynamics CRM op iOS en Android wordt gevraagd om te schrijven bij Intune als niet-naleving problemen verhelpen voordat de aanmelding wordt voltooid. Zie voor meer informatie [toegang beperken tot Dynamics CRM Online met Microsoft Intune](https://docs.microsoft.com/intune/deploy-use/restrict-access-to-dynamics-crm-online-with-microsoft-intune).

- **Updates voor de Android-bedrijfsportal-app**

  Intune heeft nu de volgende nieuwe beleidsregels die gevolgen voor Android-bedrijfsportal gebruikers hebben:   

  Beleid  |Gevolgen voor gebruikers  
  ---------|---------
  Vereisen dat apparaten niet toestaan van installatie van apps van onbekende bronnen (Android 4.0 +)     |  Eindgebruikers met Android 4.0 of hoger het bericht wordt weergegeven, "Installatie vanuit onbekende bronnen moet worden uitgeschakeld." Gebruikers moeten naar **instellingen > beveiliging** op hun apparaten en schakel **onbekende bronnen**. Een koppeling in het nalevingsbericht kunnen gebruikers meer informatie over het bericht en over waarom ze de instelling moeten uitschakelen.
  Vereisen dat apparaten niet toestaan van installatie van apps van onbekende bronnen (Android 4.0 +)  |    Eindgebruikers met Android 4.0 of hoger ziet het bericht "Apparaat scannen op beveiligingsrisico's." Gebruikers moeten naar **instellingen > Google > beveiliging** op hun apparaten en inschakelen **apparaat scannen op beveiligingsrisico's**. Een koppeling in het nalevingsbericht kunnen gebruikers in staat om meer informatie over het bericht en over waarom ze de instelling inschakelen.     
  Vereisen dat USB-foutopsporing is uitgeschakeld (Android 4.2 en hoger)  | Eindgebruikers met Android 4.2 of hoger het bericht wordt weergegeven, USB-foutopsporing moet worden uitgeschakeld." Gebruikers moeten naar **instellingen > Opties voor ontwikkelaars** op hun apparaten en schakel **USB-foutopsporing**. Een koppeling in het nalevingsbericht kunnen gebruikers meer informatie over het bericht en over waarom ze de instelling moeten uitschakelen.
  Minimale Android-beveiligingspatchniveau (Android 6.0 en hoger)  | Eindgebruikers met Android 6.0 of latere apparaten zien het bericht, "dit apparaat voldoet niet aan het minimale Android-beveiligingspatchniveau." Gebruikers moeten de vereiste beveiligingspatch installeren. Een koppeling in het nalevingsbericht kunnen gebruikers in staat om informatie over het installeren van de vereiste beveiligingspatch en om te zien welke beveiligingspatch momenteel is geïnstalleerd.

- **Updates voor de iOS-bedrijfsportal-app**

  * Wanneer eindgebruikers line-of-business-apps installeren, zien ze nu een verbeterde app-installatie optreden. Als de app-installatie lang duurt, kunnen gebruikers hun apparaat voor het afdwingen van hervatting van het synchronisatieproces handmatig synchroniseren. U kunt de instructies voor eindgebruikers, synchronisatie uw iOS-apparaat handmatig te bekijken.
  * De Microsoft Intune-bedrijfsportal-app voor iOS is bijgewerkt ter ondersteuning van iOS-versie 8.0 en hoger. Deze update betekent dat eindgebruikers kunnen de bedrijfsportal-app installeert en nieuwe apparaten inschrijven in Intune alleen als het apparaat iOS-versie 8.0 of hoger. Gebruikers die werken met eerder ingeschreven apparaten die worden uitgevoerd op een niet-ondersteunde versie van iOS kunnen blijven gebruiken van de bedrijfsportal-app die op hun apparaat is.


### <a name="new-in-1606-technical-preview"></a>Nieuw in 1606 Technical Preview
De volgende nieuwe functies geïntroduceerd in juni 2016 zijn beschikbaar in hybride implementaties met Intune en Configuration Manager Technical Preview 1606.

- **Apparaten automatisch categoriseren in verzamelingen**

  U kunt apparaatcategorieën dat kunnen worden gebruikt voor apparaten worden automatisch op apparaatverzamelingen plaatsen wanneer u van Configuration Manager met Intune gebruikmaakt kunt maken. Gebruikers hoeven vervolgens een apparaatcategorie kiezen wanneer ze een apparaat bij Intune inschrijven. Bovendien kunt u de categorie van een apparaat wijzigen vanuit de Configuration Manager-console. Zie voor meer informatie [apparaten automatisch categoriseren in verzamelingen](/sccm/core/get-started/capabilities-in-technical-preview-1606#dmp_category) in [mogelijkheden van Technical Preview 1606 voor System Center Configuration Manager](/sccm/core/get-started/capabilities-in-technical-preview-1606).

  > [!IMPORTANT]
  > Deze mogelijkheid werkt met de release van juni 2016 van Microsoft Intune. Zorg ervoor dat u hebt bijgewerkt naar deze versie voordat u deze procedures.

### <a name="new-in-configuration-manager-current-branch"></a>Nieuw in Configuration Manager (huidige vertakking)
Geen nieuwe hybridefuncties zijn geïntroduceerd in juni 2016 voor Configuration Manager (huidige vertakking).

##  <a name="may-2016"></a>Mei 2016  

### <a name="new-in-microsoft-intune"></a>Nieuw in Microsoft Intune  
 De volgende Intune-functies die zijn geïntroduceerd in mei 2016 werken in hybride implementaties.

- **MAM SDK: De configuratie van de lengte PINCODE ondersteuning**

  U kunt nu de lengte van de PINCODE voor MAM-apps is vergelijkbaar met een PINCODE voor Apparaattoegang opgeven. Dit vereist dat eindgebruikers om te voldoen aan de nieuwe beperkingen die u instelt. Het scherm van de PINCODE is enigszins gewijzigd in de account voor de langer invoer. Zie voor meer informatie [MAM-beleidsinstellingen voor Android](https://docs.microsoft.com/intune/deploy-use/android-mam-policy-settings), en [MAM-beleidsinstellingen voor iOS](https://docs.microsoft.com/intune/deploy-use/ios-mam-policy-settings).  

- **Skype voor bedrijven voor iOS en Android**

  U kunt er nu Skype voor bedrijven gebruiken met [MAM zonder registratiebeleid](https://docs.microsoft.com/intune/deploy-use/get-ready-to-configure-mobile-app-management-policies-with-microsoft-intune). Zodra gebruikers zich aanmelden, wordt het MAM-beleid toegepast.  

- **Nieuwe beschikbare apps voor beheer met MAM-beleid**

  De Microsoft Word, Excel en PowerPoint-apps voor Android kunnen nu worden gekoppeld aan MAM-beleid op apparaten die niet zijn ingeschreven met Intune. Ga voor een volledige lijst met ondersteunde apps, de galerie met mobiele toepassingen van Microsoft Intune op de [Microsoft Intune-toepassingspartners](https://www.microsoft.com/en-us/server-cloud/products/microsoft-intune/partners.aspx) pagina.  

- **Android-bedrijfsportal-app: Pop-upmeldingen voor eindgebruikers**

  Pop-upmeldingen uit de Android-bedrijfsportal-app worden weergegeven wanneer eindgebruikers schrijven of verwijderen van hun apparaten via de bedrijfsportal.  

- **Bedrijfsportal-website: Apparaat banner voor apparaatidentificatie biedt meer informatie voor eindgebruikers**

  Eindgebruikers kunnen het apparaat dat ze hebben geselecteerd wanneer ze de bedrijfsportal-website gebruiken nu gemakkelijker identificeren. Als een verkeerd apparaat is ingeschakeld, kunnen ze het juiste apparaat selecteren door te tikken op de **Tik hier** koppeling in de banner van de startpagina.  


### <a name="new-in-1605-technical-preview"></a>Nieuw in 1605 Technical Preview  
 De volgende nieuwe functies geïntroduceerd in mei 2016 zijn beschikbaar in hybride implementaties met Intune en Configuration Manager Technical Preview 1605. Deze functies moeten u de Configuration Manager-console gebruiken om te configureren en beheren.  

- **App geactiveerd VPN voor Windows 10-apparaten**

  Voor Windows 10-apparaten die worden beheerd met Configuration Manager met Intune, kunt u een lijst met apps die automatisch een VPN-verbinding die u hebt geconfigureerd via de Configuration Manager-beheerconsole opent toevoegen. Zie voor meer informatie [App geactiveerd VPN voor Windows 10-apparaten](/sccm/core/get-started/capabilities-in-technical-preview-1605) in [mogelijkheden van Technical Preview 1605 voor System Center Configuration Manager](/sccm/core/get-started/capabilities-in-technical-preview-1605)  

- **Nieuwe ervaring voor acties extern apparaat**

  De ervaring voor het uitvoeren van acties extern apparaat van de Configuration Manager-console is verbeterd.

  Algemene acties zoals **buiten gebruik stellen/wissen**, **wachtwoordcode opnieuw instellen**, **vergrendelen op afstand**, en **Bypass van Activeringsvergrendeling** kan nu worden gevonden in de **acties extern apparaat** menu toegankelijk is vanuit de **activa en naleving** werkruimte

  Zie voor meer informatie [nieuwe ervaring voor acties extern apparaat](/sccm/core/get-started/capabilities-in-technical-preview-1605#new-experience-for-remote-device-actions) in [mogelijkheden van Technical Preview 1605 voor System Center Configuration Manager](/sccm/core/get-started/capabilities-in-technical-preview-1605).  

- **Windows Store voor Bedrijven-apps**

  De [Windows Store voor bedrijven](https://www.microsoft.com/en-us/business-store) kunt u vinden en apps voor uw organisatie, kopen, afzonderlijk of in volume. U kunt de store koppelt aan Configuration Manager, volume-aankoopprogramma gekochte apps beheren vanuit de Configuration Manager-console. Zie voor meer informatie [Windows Store voor bedrijven-apps](/sccm/core/get-started/capabilities-in-technical-preview-1605.md#windows-store-for-business-apps) in [mogelijkheden van Technical Preview 1605 voor System Center Configuration Manager](/sccm/core/get-started/capabilities-in-technical-preview-1605).  

- **Algemene verbeteringen van de volume-aankoopprogramma gekochte apps**

  Volume-aankoopprogramma gekochte apps uit de Windows Store voor bedrijven en de iOS appstore zijn samengevoegd in dezelfde weergave **licentie-informatie voor Apps opslaan**. Ook is de manier waarop u de volume-purchased apps voor iOS maken verbeterd. Zie voor meer informatie[algemene verbeteringen van de volume-aankoopprogramma gekochte apps](/sccm/core/get-started/capabilities-in-technical-preview-1605.md#general-improvements-for-volume-purchased-apps) in [mogelijkheden van Technical Preview 1605 voor System Center Configuration Manager](/sccm/core/get-started/capabilities-in-technical-preview-1605).  

- **Vooraf declareren van apparaten in Bedrijfseigendom met IMEI-nummer of iOS-serienummer**

  U kunt apparaten in Bedrijfseigendom nu identificeren door het importeren van hun nummers international station mobile equipment identity (IMEI-nummer). U kunt een door komma's gescheiden waarden (.csv)-bestand met IMEI-nummers van apparaten uploaden of u kunt de apparaatgegevens handmatig invoeren.  U kunt ook importeren serienummers voor iOS-apparaten.  Zie voor meer informatie [vooraf declareren van apparaten in Bedrijfseigendom met IMEI-nummer of iOS-serienummer](../../core/get-started/capabilities-in-technical-preview-1605.md#BKMK_IMEI) in [mogelijkheden van Technical Preview 1605 voor System Center Configuration Manager](/sccm/core/get-started/capabilities-in-technical-preview-1605).  

- **Windows-gegevensbeveiliging (OHW)**

  U kunt configuratie-items u uw Windows-beveiliging (OHW)-beleid kunnen, inclusief zodat u kunt ervoor kiezen uw beveiligde apps, het beveiligingsniveau op uw OHW en hoe Ondernemingsgegevens vinden op het netwerk te implementeren. Zie de volgende onderwerpen voor meer informatie over OHW:  

  -   [Uw Ondernemingsgegevens beveiligen met Windows-beveiliging (OHW)](https://technet.microsoft.com/itpro/windows/keep-secure/protect-enterprise-data-using-wip)  

  -   [Een Windows-beveiliging (OHW)-beleid met behulp van System Center Configuration Manager maken en implementeren](https://technet.microsoft.com/itpro/windows/keep-secure/create-wip-policy-using-sccm)  

### <a name="new-in-configuration-manager-current-branch"></a>Nieuw in Configuration Manager (huidige vertakking)  
 Geen nieuwe hybridefuncties zijn geïntroduceerd in mei 2016 voor Configuration Manager (huidige vertakking).  

##  <a name="april-2016"></a>April 2016  

### <a name="new-in-microsoft-intune"></a>Nieuw in Microsoft Intune  
 De volgende Intune-functies die zijn geïntroduceerd in April 2016 werken in hybride implementaties.  

- **Naleving van MAM-gebruiker**

  U kunt nu de status van uw toepassing management-beleid voor elke gebruiker bekijken in de tenant van uw Azure Active Directory (AAD).  Zie voor meer informatie [mobiele app management-beleid bewaken met Microsoft Intune](/intune/deploy-use/monitor-mobile-app-management-policies-with-microsoft-intune) in de Intune-bibliotheek.  

- **MAM-besturingselementen om te voorkomen dat Outlook-contactpersonen worden gesynchroniseerd (Android)**

  Er is een nieuwe instelling beschikbaar waarmee u voorkomen dat een toepassing contactpersonen in het systeemeigen adresboek op Android-apparaten synchroniseren. Deze nieuwe instelling wordt in eerste instantie ondersteund door de Outlook-toepassing op Android-apparaten. Zie voor meer informatie [maken en implementeren van beleid voor mobile app management met Microsoft Intune](/intune/deploy-use/monitor-mobile-app-management-policies-with-microsoft-intune) in de Intune-bibliotheek.  

- **Verbeteringen in de bedrijfsportal-website**

  Wanneer gebruikers van Windows 10 Mobile en Windows Phone 8.1 LOB-apps installeren, zien ze nu de volgende nieuwe statussen, waardoor ze meer details over de status van hun installatie:  

  -   **Wachten op apparaatsynchronisatie** : de gebruiker heeft getikt 'Installeren' en wordt nu geprobeerd het apparaat kunnen worden gesynchroniseerd met de Intune-infrastructuur. De synchronisatie is vereist voordat de installatie te voltooien. Het bericht 'Wachten op apparaatsynchronisatie' is ook een koppeling waarop gebruikers tikken kunnen om instructies te zien over het handmatig synchroniseren van hun apparaat bij Intune als het synchronisatieproces lang duurt of vastloopt.  

  -   **Downloaden van** : de downloadaanvraag van de gebruiker wordt verwerkt en het apparaat downloadt en installeert u de app.  

- **Verbeteringen in de Android-bedrijfsportal-app**

  Gebruikers die niet hun apparaat bij Intune hebben ingeschreven en bij wie niet het juiste certificaat is geïnstalleerd zich niet aanmelden bij de Android-bedrijfsportal-app en het bericht wordt weergegeven, 'U niet aanmelden omdat een vereist certificaat ontbreekt op uw apparaat.' Het bericht bevat een "How oplossing" koppeling waarop gebruikers tikken kunnen om instructies voor het installeren van het certificaat te zien. Als u wilt zien welke stappen eindgebruikers moeten volgen om het probleem te verhelpen, Zie [een vereist certificaat ontbreekt op uw apparaat](/intune/enduser/using-your-android-device-with-intune) in de Intune-bibliotheek.  

- **Verbeteringen in de iOS-bedrijfsportal-app**

  Er is ondersteuning toegevoegd voor de actie pull om te vernieuwen vernieuwen van de inhoud van het startscherm, waaronder apps in de lijst, lijst met apparaten en de contactgegevens van IT informatie. De actie pull te vernieuwen wordt niet gecontroleerd naleving of beleid informatie, die kan worden gedaan door de tegel voor uw huidige apparaat te selecteren en tik op de **Sync** knop.  

- **Verbeteringen in Windows 10 Mobile en Windows Phone 8.1-bedrijfsportal-app voor**

  Wanneer eindgebruikers line-of-business-apps installeren, zien ze nu een verbeterde app-installatie optreden. Als de app-installatie lang duurt, kunnen gebruikers hun apparaat voor het afdwingen van hervatting van het synchronisatieproces handmatig synchroniseren. De instructies voor eindgebruikers Zie [synchroniseren van uw apparaat handmatig als u wilt versnellen app-installaties](/intune/enduser/using-your-windows-device-with-intune) in de Intune-bibliotheek.  

###  <a name="new-in-1604-technical-preview"></a>Nieuw in Technical Preview 1604
 De volgende nieuwe functies geïntroduceerd in April 2016 zijn beschikbaar in hybride implementaties met Intune en Configuration Manager Technical Preview 1604. Deze functies moeten u de Configuration Manager-console gebruiken om te configureren en beheren.  

- **Zoeken, beheren en distribueren van Windows Store voor bedrijven-apps voor Windows 10-apparaten van de Configuration Manager-console**


  Ondersteuning voor Windows Store voor bedrijven is beschikbaar in Configuration Manager Technical Preview 1604 om te zoeken, beheren en distribueren van apps voor de Windows 10-apparaten die u beheert. Zie voor meer informatie [volume-aankoopprogramma gekochte apps beheren via de Windows Store voor bedrijven](/sccm/core/get-started/capabilities-in-technical-preview-1604#manage-volume-purchased-apps-from-the-windows-store-for-business) in [mogelijkheden van Technical Preview 1604 voor System Center Configuration Manager](/sccm/core/get-started/capabilities-in-technical-preview-1604).  

- **SmartLock-instelling voor Android-apparaten**

  Een nieuwe instelling is toegevoegd aan de Android en Samsung KNOX Standard configuratie-item waarmee u de Smart Lock-functie op compatibele Android-apparaten beheren.  U kunt deze instelling gebruiken om te voorkomen dat eindgebruikers Smart LOCK configureren. Zie [SmartLock-instelling voor Android-apparaten](/sccm/get-started/capabilities-in-technical-preview-1604#smartlock-setting-for-android-devices) in [mogelijkheden van Technical Preview 1604 voor System Center Configuration Manager](/sccm/core/get-started/capabilities-in-technical-preview-1604.md).  

### <a name="new-in-configuration-manager-current-branch"></a>Nieuw in Configuration Manager (huidige vertakking)  
 Er zijn geen nieuwe hybridefuncties geïntroduceerd in April 2016 voor Configuration Manager (huidige vertakking).  

##  <a name="march-2016"></a>Maart 2016  

### <a name="new-in-microsoft-intune"></a>Nieuw in Microsoft Intune  
 De volgende Intune-functies die zijn geïntroduceerd in maart 2016 werken in hybride implementaties.  

- **MAM-besturingselementen om te voorkomen dat Outlook-contactpersonen worden gesynchroniseerd (iOS)**

  Er is een nieuwe instelling beschikbaar waarmee u voorkomen dat een toepassing contactpersonen in het systeemeigen adresboek op iOS-apparaten synchroniseren. Deze nieuwe instelling wordt ondersteund door de Outlook-toepassing op iOS-apparaten. Zie voor meer informatie over deze en andere instellingen [maken en implementeren van MAM-beleid](/intune/deploy-use/monitor-mobile-app-management-policies-with-microsoft-intune) in de Intune-bibliotheek.  

- **Skype voor bedrijven Online biedt ondersteuning voor voorwaardelijke toegang**

  U kunt beleid voor voorwaardelijke toegang voor Skype voor bedrijven Online instellen zodat deze alleen toegankelijk is voor beheerde en compatibele iOS en Android-apparaten.  Zie voor meer informatie [toegang tot Skype voor bedrijven Online beheren](/intune/deploy-use/restrict-access-to-skype-for-business-online-with-microsoft-intune) in de Intune-bibliotheek.  

- **Ondersteuning voor iOS 9.3**

  Op maandag 21 maart heeft Apple aangekondigd dat iOS 9.3. Alle bestaande Intune-functies die momenteel beschikbaar zijn voor het beheren van iOS-apparaten blijven naadloos werken wanneer gebruikers hun apparaten naar iOS 9.3 upgraden.  

- **Windows app-pakketten beschikbaar rechtstreeks vanuit de bedrijfsportal-website**

  Gebruikers van Windows 8, Windows 8.1 en Windows RT-pc's kunnen Windows app-pakketten (met de extensie .appx) nu rechtstreeks vanuit de bedrijfsportal-website installeren. Voorheen moest u implementeren of moesten gebruikers de bedrijfsportal-app installeren op hun apparaten om apps te installeren.  

- **Gebruikers kunnen hun apparaat via de bedrijfsportal-website op afstand vergrendelen**

  Een nieuwe optie voor vergrendelen op afstand is toegevoegd aan de bedrijfsportal-website waarmee gebruikers hun apparaat via de Portal op afstand vergrendelen als hun apparaat is zoekgeraakt of gestolen.  

- **Profiteren van iOS 'Open-in'-beheer voor apparaten die zijn ingeschreven bij een MDM-oplossing van derden**

  U kunt de leverancier van uw mobiele apparaten van derden management (MDM) gebruiken om te profiteren van iOS 'Open-In'-beheer. U kunt de beperkingen in de configuratie configuratieprofielinstellingen configureren en implementeren van de app via uw MDM-software. Wanneer de gebruiker de beheerde app installeert, worden de beperkingen toegepast. Voor meer informatie: [Microsoft Intune mam-beleid en iOS Open In](/intune/deploy-use/introduction-to-device-compliance-policies-in-microsoft-intune) in de Intune-bibliotheek.  

- **Microsoft-apps die ondersteuning bieden voor MAM**

  De lijst met Microsoft-apps die u met Intune mobile application management-beleid gebruiken kunt is bijgewerkt zodat de meest recente apps (voor apparaten die zijn ingeschreven met Intune alleen).  

- **Adobe Reader voor Microsoft Intune implementeren op Intune beheerde iOS-apparaten in uw onderneming**

  De Adobe Reader-app voor iOS kan nu worden beheerd op ingeschreven apparaten met de Intune mobile application management-beleid.  

- De Rights Management-app voor delen wordt ondersteund voor Android

  IT-beheerders mobile application management-beleid kunnen implementeren, zodat eindgebruikers bekijken, afbeeldingen, AV en PDF kunnen-bestanden veiliger, al dan niet IT Intune gebruikt om de apparaten te beheren.  

- **Verbeteringen in de Android en iOS-bedrijfsportal-app**

  -   Wanneer uw gebruikers een app openen die wordt beheerd via mobile application management (MAM), zien ze een bericht met de mededeling dat de app wordt beheerd door hun bedrijf. Gebruikers kunnen nu tikken op "Meer informatie" voor hier meer informatie over wat het betekent 'beheerde apps'. Ze kunnen ook tikken op 'Niet meer weergeven' zodat het bericht niet meer wordt weergegeven bij het openen van de app.  

  -   Nieuwe schermen zijn toegevoegd om gebruikers door het registratieproces te leiden en meer informatie over waarom de gebruikers moeten registreren en wat de IT-beheerders wel en niet kunnen op de ingeschreven apparaten zien te bieden.  

  -   Registratiefoutberichten worden nu weergegeven in de bedrijfsportal-app.  

### <a name="new-in-configuration-manager-technical-preview"></a>Nieuw in Configuration Manager Technical Preview  
 Er zijn geen nieuwe hybridefuncties zijn geïntroduceerd in maart 2016 voor Configuration Manager Technical Preview.  

### <a name="new-in-configuration-manager-current-branch"></a>Nieuw in Configuration Manager (huidige vertakking)  
 De volgende nieuwe functies geïntroduceerd in maart 2016 zijn beschikbaar in hybride implementaties met Intune en Configuration Manager (huidige vertakking) versie 1602. Deze functies moeten u de Configuration Manager-console gebruiken om te configureren en beheren.  

- **Configuratiebeleidsregels voor IOS-apps**

  In versie 1602 van Configuration Manager (huidige vertakking) kunt u app-configuratiebeleid te voorzien van instellingen die mogelijk vereist zijn wanneer de gebruiker een iOS-app uitvoert. Zie voor meer informatie [iOS-apps configureren met configuratiebeleid voor apps in System Center Configuration Manager](/sccm/apps/deploy-use/configure-ios-apps-with-app-configuration-policies).  

- **Volume-purchased iOS-apps beheren**

  U kunt in versie 1602 van Configuration Manager (huidige vertakking), implementeren en beheren van apps die u hebt aangeschaft via het Apple Volume Purchase Program (VPP) door de licentiegegevens uit de appstore te importeren en bij te houden hoeveel licenties u hebt gebruikt. Zie voor meer informatie [volume-purchased iOS-apps met System Center Configuration Manager beheren](/sccm/apps/deploy-use/manage-volume-purchased-ios-apps).  

- **Automatische aanmaak van mobiele Office-apps**

  Vanaf versie 1602 van Configuration Manager (huidige vertakking), worden de volgende mobiele Microsoft Office-apps voor Android en iOS gemaakt wanneer u een van versie 1511 upgrade:  

  -   Microsoft Word  
  -   Microsoft Excel  
  -   Microsoft PowerPoint  
  -   Microsoft OneDrive  
  -   Microsoft OneNote (alleen iOS)  
  -   Microsoft Outlook  

  Deze apps vindt u in het knooppunt toepassingen van de Configuration Manager-console. Zie voor meer informatie over het implementeren van toepassingen [toepassingen met System Center Configuration Manager implementeren](../../apps/deploy-use/deploy-applications.md).  

- **Instellingen voor kioskmodus voor Android Samsung KNOX Standard-apparaten**

  Met de kioskmodus kunt u een apparaat zo vergrendelen dat alleen bepaalde functies werken.  U kunt nu een instellingen voor kioskmodus voor Samsung KNOX Standard-apparaten opgeven vanaf versie 1602 van Configuration Manager (huidige vertakking) is. Zie voor meer informatie [het maken van configuratie-items voor Android en Samsung KNOX Standard-apparaten worden beheerd zonder de System Center Configuration Manager-client](/sccm/compliance/deploy-use/create-configuration-items-for-android-and-samsung-knox-devices-managed-without-the-client).  

- **iOS-Activeringsvergrendeling**

  Vanaf versie 1602 van Configuration Manager (huidige vertakking), kunt u iOS-Activeringsvergrendeling, een functie van de app Zoek mijn iPhone voor iOS 7.1 en hoger apparaten beheren. Activeringsvergrendeling is automatisch ingeschakeld wanneer de app Zoek mijn iPhone op een apparaat wordt gebruikt.  Zie voor meer informatie [beheren iOS-Activeringsvergrendeling overslaan voor System Center Configuration Manager](/sccm/mdm/deploy-use/manage-ios-activation-lock#bypass-activation-lock).  
