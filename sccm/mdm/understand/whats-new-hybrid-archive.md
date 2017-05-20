---
title: Archief met wat nieuw hybride MDM is | Microsoft-documenten
description: Archief van beschikbaar voor hybride implementaties met System Center Configuration Manager en de Intune-functies afgelopen mobiele apparaten.
ms.custom: na
ms.date: 03/05/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-hybrid
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 4c27b161-9eb7-4cdd-b469-d8eb27e71aea
author: Mtillman
ms.author: mtillman
manager: angrobe
ROBOTS: NOINDEX, NOFOLLOW
ms.translationtype: Machine Translation
ms.sourcegitcommit: 2c723fe7137a95df271c3612c88805efd8fb9a77
ms.openlocfilehash: 623a30eddebcae196ff345ef5debc8183ecd6ae6
ms.contentlocale: nl-nl
ms.lasthandoff: 05/17/2017

---
# <a name="past-hybrid-features-with-system-center-configuration-manager-and-microsoft-intune"></a>Afgelopen hybride functies met System Center Configuration Manager en Microsoft Intune

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*

Dit artikel biedt gedetailleerde informatie over het verleden mobiele apparaat management (MDM) die beschikbaar zijn voor hybride implementaties met System Center Configuration Manager en Microsoft Intune.  

##  <a name="compatibility-with-configuration-manager-versions"></a>Compatibiliteit met versies van Configuration Manager  

 Elke sectie van dit artikel geeft een overzicht van hybride functies onder 3 verschillende categorieën. Gebruik de volgende richtlijnen om te bepalen van compatibiliteit met eerdere versies van de functies in elke categorie met verschillende versies van Configuration Manager:  

|Functie categorieën|
|-|  
|**Nieuw in Microsoft Intune** -In het algemeen alle functies die worden vermeld onder deze categorie moeten samen met alle versies van de Configuration Manager met inbegrip van System Center 2012 R2 Configuration Manager-versies, aangezien deze functies alleen de Intune-service vereisen en geen aanvullende functionaliteit in Configuration Manager vereisen.<br /><br /> **Nieuw in Configuration Manager Technical Preview** -alle functies in deze categorie alleen werken met de opgegeven technische voorbeeldversie weergegeven. Als u wilt deze functies uit te proberen, moet u de opgegeven in de functiebeschrijving van de Technical Preview-versie installeren. Zie voor meer informatie [Technical Preview voor System Center Configuration Manager](../../core/get-started/technical-preview.md).<br /><br /> **Nieuw in Configuration Manager (huidige vertakking)** -alle functies vermeld onder deze categorie alleen werken met de opgegeven versie van Configuration Manager (huidige vertakking), zoals versie 1511 of 1602. Als u een oudere versie van Configuration Manager gebruikt voor uw implementatie van hybride, moet u een upgrade uitvoeren naar de Configuration Manager (huidige vertakking) versie opgegeven in de functiebeschrijving van de. Zie voor meer informatie [upgraden naar System Center Configuration Manager](../../core/servers/deploy/install/upgrade-to-configuration-manager.md).|  

## <a name="new-hybrid-features-in-october-2016"></a>Nieuwe functies voor hybride in oktober 2016

### <a name="new-in-microsoft-intune"></a>Nieuw in Microsoft Intune

De volgende Intune-functies die is geïntroduceerd in oktober 2016 werken in hybride implementaties.

- **Voorwaardelijke toegang voor mobile application management**

  U kunt toegang tot Exchange Online beperken zodat toegang afkomstig zijn uit apps die ondersteuning bieden voor Intune mobile application management-beleid zoals Outlook. [Deze nieuwe functie](/intune/deploy-use/allow-policy-managed-apps-access-to-o365) paren van perfect met Intune mobile app management (MAM)-beleid als u toegang tot de ingebouwde e-mailclients of andere apps die niet zijn geconfigureerd met de Intune MAM-beleid kunt blokkeren. Hiermee zorgt u dat uw gebruikers de gegevens van uw organisatie met apps die kunnen worden beveiligd met Intune MAM opent. U kunt aan de slag in beheer van mobiele Apps Intune via de Azure-portal. Zoek naar de nieuwe rubriek voor voorwaardelijke toegang in de blade 'Instellingen'.

-    **Intune App Wrapping Tool voor Android**

  U kunt uw gebruik van Intune mobile application management (MAM) beleid met behulp van de Intune App Wrapping Tool-apps inschakelen.

- **Android Samsung KNOX Standard compatibiliteit met Intune**

  Bepaalde modellen van het telefoonnummer Samsung Galaxy Ace kunnen niet worden beheerd door Intune als Samsung KNOX Standard-apparaten. Wanneer u deze apparaten met Intune inschrijft, wordt deze in plaats daarvan als standaard Android-apparaten worden beheerd.

  De model-getallen betrokken zijn:

  - SM-G313HU
  -    SM-G313HY
  -    SM-G313M
  -    SM-G313MY
  -    SM-G313U

  U en uw eindgebruikers hoeft er geen verdere actie te ondernemen. Ga naar de website van Samsung KNOX voor meer informatie.

### <a name="new-in-configuration-manager-technical-preview-1610"></a>Nieuw in Configuration Manager technische Preview 1610

De volgende nieuwe functies voor hybride zijn geïntroduceerd in oktober 2016 voor technische Preview 1610 van Configuration Manager.

- **Een beleid voor synchronisatie van de beheerconsole aanvragen**

  U kunt een beleid voor synchronisatie op een geregistreerde mobiele apparaat van de Configuration Manager-console in plaats van dat nodig is om aan te vragen van de synchronisatie van de bedrijfsportal-app op het apparaat zelf aanvragen. Dit is een nieuwe naam **Sync aanvraag verzenden** in het menu Acties op afstand apparaat die wordt weergegeven in het lint wanneer een mobiel apparaat wordt geselecteerd in het knooppunt apparaten.

- **Windows Defender configuratie-instellingen**

  Nu kunt u clientinstellingen voor Windows Defender op Intune zijn ingeschreven Windows 10-computers met configuratie-items in de Configuration Manager-console. Er is een nieuwe instellingsgroep met de naam **Windows Defender** in de wizard Configuratie-Item. Houd er rekening mee dat dit alleen op Windows 10 versie 1511 en hoger wordt ondersteund.


### <a name="new-in-configuration-manager-current-branch"></a>Nieuw in Configuration Manager (huidige vertakking)

Er zijn geen nieuwe hybride-functies zijn geïntroduceerd in augustus 2016 voor Configuration Manager (huidige vertakking).

## <a name="new-hybrid-features-in-september-2016"></a>Nieuwe functies voor hybride in September 2016

### <a name="new-in-microsoft-intune"></a>Nieuw in Microsoft Intune

De volgende Intune-functies die is geïntroduceerd in September 2016 werken in hybride implementaties.

- **Toevoeging van "Meldingen" aan de bedrijfsportal voor Android**

  Pictogram van een nieuwe meldingen is toegevoegd aan de bedrijfsportal voor Android op de startpagina. Op dit pictogram te tikken heeft toegang tot de pagina meldingen die uw eindgebruikers toont alle items die in de bedrijfsportal-app, zoals het apparaat niet-compatibele inschrijvingsupdate en activering van inschrijving aandacht nodig hebben. De iOS-bedrijfsportal-app al is meldingen optreden. Om de nieuwe pagina middelen voor meldingen zichtbaar die gebruiker niet voor de installatie van bedrijfstoegang pagina telkens wanneer ze starten of hervatten van de bedrijfsportal zolang het apparaat is al geregistreerd. Als u de richtlijnen van uw eigen door eindgebruikers maakt, is het raadzaam om bij te werken de documentatie voor deze wijziging. Bijgewerkte schermafbeeldingen vinden [hier](https://aka.ms/androidcpupdate).

- **Wijzigingen in ondersteuning voor de iOS-bedrijfsportal-app**

  Alle gebruikers van de Microsoft Intune-bedrijfsportal-app voor iOS zijn nu vereist voor het gebruik van de meest recente versie. Nieuwe gebruikers kunnen alleen de meest recente versie downloaden en huidige gebruikers bij te werken naar deze vereist zijn. De meest recente versie vereist iOS 8.0 of hoger, zodat apparaten met oudere versies van iOS kunnen de bedrijfsportal gebruiken of inschrijven totdat ze hun apparaat naar iOS 8.0 of hoger bijwerken en werk vervolgens de bedrijfsportal-app naar de nieuwste versie. Blijven ingeschreven apparaten met een versie onder iOS 8.0 zullen worden beheerd en weergegeven in de Intune-beheerconsole.

- **Feedbackknop toegevoegd aan Windows Phone 8.1-bedrijfsportal-app**

  De Windows Phone 8.1-bedrijfsportal-app kan eindgebruikers feedback over de app kunt verzenden door middel van een nieuwe knop "feedback verzenden". Ga voor de knop gebruikers Tik op het menu "drie punten" in de rechterbenedenhoek van het scherm bedrijfsportal-app en tik **feedback verzenden**. De verzamelde, geanonimiseerde feedback helpt Microsoft bij het verbeteren van de bedrijfsportal-app-ervaring voor gebruikers.

### <a name="new-in-configuration-manager-technical-preview-1609"></a>Nieuw in Configuration Manager technische Preview 1609

De volgende nieuwe functies voor hybride zijn geïntroduceerd in September 2016 voor technische Preview 1609 van Configuration Manager.

- **Extra instellingen en verbeterde ervaring voor instellingen van de configuratie-Item**

  Nieuwe instellingen voor Android, iOS en Windows zijn toegevoegd en alleen de instellingen die betrekking hebben op de platforms die u op de pagina ondersteunde Platforms selecteert worden weergegeven in de wizard. Zie voor meer informatie [nieuwe compatibiliteitsinstellingen voor configuratie-items in TP 1609](/sccm/core/get-started/capabilities-in-technical-preview-1609#new-compliance-settings-for-configuration-items).

- **Extra instellingen voor DEP-profielen**

  TouchID, ApplePay en zoomen zijn toegevoegd als configureerbare instellingen in de DEP-profielen voor iOS-apparaten.

- **Windows Store-Apps betalen voor bedrijven**

  U kunt nu betaald en beschikbare toepassingen naar Windows Store voor bedrijven toevoegen en implementeren voor gebruikers in uw organisatie. Zie voor meer informatie [uitbreidingen voor Windows Store voor bedrijven in TP 1609](/sccm/core/get-started/capabilities-in-technical-preview-1609#enhancements-to-windows-store-for-business-integration-with-configuration-manager).

- **Systeemeigen verbindingstypen voor Windows 10 VPN-profielen**

  U kunt nu Windows 10 VPN-profielen voor met MDM maken met Microsoft Automatic IKEv2 en PPTP verbindingstypen in de Configuration Manager-console zonder met behulp van OMA-URI.

- **Intune compatibiliteit grafieken**

  U krijgt een snelle weergave van algemene apparaat naleving en top redenen voor compatibiliteit met nieuwe grafieken onder de werkruimte bewaking. Zie voor meer informatie [Intune naleving grafieken in TP 1609](/sccm/core/get-started/capabilities-in-technical-preview-1609#intune-compliance-charts).

### <a name="new-in-configuration-manager-current-branch"></a>Nieuw in Configuration Manager (huidige vertakking)

De volgende nieuwe functie die is geïntroduceerd in September 2016 is beschikbaar voor hybride implementaties met Microsoft Intune en Configuration Manager versie 1606 (huidige vertakking).

- **iOS-10-ondersteuning**

  Als u profielen of configuratie-items die zijn gericht op alle platforms van iOS, wordt deze ook naar iOS 10 gepusht. We hebben ook een update van Configuration Manager versie 1606 waarmee u doel profielen en configuratie-items voor afzonderlijke iOS-platforms zoals iOS 10 uitgebracht. U kunt de update installeren met de Configuration Manager-beheerconsole op **beheer > overzicht > Cloudservices > Updates en onderhoud**. U vindt meer informatie over de update op [http://support.microsoft.com/kb/3192616](http://support.microsoft.com/kb/3192616).

## <a name="new-hybrid-features-in-august-2016"></a>Nieuwe functies voor hybride in augustus 2016

### <a name="new-in-microsoft-intune"></a>Nieuw in Microsoft Intune

De volgende Intune-functies die is geïntroduceerd in augustus 2016 werken in hybride implementaties.

- **Android 7-ondersteuning in de bedrijfsportal-app**

  De Intune-bedrijfsportal-app voor Android biedt 'day 0'-ondersteuning voor de toekomstige Android 7.0 besturingssysteem voor mobiele apparaten.

- **Google verwijderen van externe code functionaliteit op Android 7.0 apparaten opnieuw instellen**

  Google verwijdert de mogelijkheid van IT-beheerders en eindgebruikers de wachtwoordcode van Android 7.0 apparaten op afstand opnieuw instellen. Eerder IT-beheerders kunnen op afstand opnieuw instellen van een gebruiker wachtwoordcode en eindgebruikers kunnen hun toegangscodes van de bedrijfsportal-website opnieuw instellen.

- **Beleid voor toegestane en geblokkeerde apps voor Samsung KNOX Standard-apparaten**

  U kunt nu een aangepast beleid voor Samsung KNOX Standard-apparaten waarmee u bij het maken van een van de volgende configureren:

  - Een lijst met apps die niet kunnen worden uitgevoerd op het apparaat zijn geblokkeerd. Zelfs als geïnstalleerd, kan een app in de lijst met geblokkeerde gedefinieerd op het apparaat niet geactiveerd.
  - Een lijst met apps die gebruikers van het apparaat kunnen installeren uit de Google Play store. Er zijn geen andere apps kunnen worden geïnstalleerd uit de store.

  Deze instellingen kunnen alleen worden gebruikt door apparaten met Samsung KNOX Standard. Zie voor meer informatie, [aangepast beleid gebruiken voor het toestaan en blokkeren van apps voor Samsung KNOX Standard-apparaten](/intune/deploy-use/custom-policy-to-allow-and-block-samsung-knox-apps).

- **Koppeling van de bedrijfsportal feedback naar Microsoft**

   De website van de bedrijfsportal kan eindgebruikers Tik op een nieuwe feedbackkoppeling "" aan de onderkant van de pagina om feedback te verzenden naar Microsoft over hun ervaringen met de site. De verzamelde, geanonimiseerde feedback helpt Microsoft bij het verbeteren van de bedrijfsportal-website-ervaring voor gebruikers.

- **Minimale iOS Managed Browser-versie is bijgewerkt naar 8.0**

  De beheerde Browser van Microsoft Intune-app voor iOS is bijgewerkt voor ondersteuning van apparaten met iOS-8.0 of hoger. Terwijl het iOS 7.1-apparaten kunnen nog steeds de bestaande beheerde-browserapp gebruiken, kunt u uw gebruikers om te werken naar iOS 8.0 of hoger voor toegang tot en profiteren van nieuwe functies van Managed Browser.

### <a name="new-in-configuration-manager-technical-preview"></a>Nieuw in Configuration Manager Technical Preview

Er zijn geen nieuwe hybride-functies zijn geïntroduceerd in augustus 2016 voor technische Preview van Configuration Manager.

### <a name="new-in-configuration-manager-current-branch"></a>Nieuw in Configuration Manager (huidige vertakking)

Er zijn geen nieuwe hybride-functies zijn geïntroduceerd in augustus 2016 voor Configuration Manager (huidige vertakking).

## <a name="new-hybrid-features-in-july-2016"></a>Nieuwe functies voor hybride in juli 2016

### <a name="new-in-microsoft-intune"></a>Nieuw in Microsoft Intune

De volgende Intune-functies die is geïntroduceerd in juli 2016 werken in hybride implementaties.

- **Xamarin-SDK voor Intune-apps is beschikbaar**

  Het onderdeel Intune App SDK Xamarin kunt u de functies voor Intune mobiele app in de mobiele iOS- en gebouwd met Xamarin Android-apps inschakelen. U vindt het onderdeel in de [Xamarin store](https://components.xamarin.com/view/Microsoft.Intune.MAM) of op de [Microsoft Intune Github pagina](https://github.com/msintuneappsdk).

- **Verbeterde gebruikerservaring tijdens de inschrijving van Windows-apparaten**

  Wanneer u van voorwaardelijke toegang gebruikmaakt, zijn de stappen voor inschrijving voor Windows 8.1, Windows 10 Desktop en Windows 10 Mobile is verklaard in de bedrijfsportal-website. Gebruikers zien nu afzonderlijke **apparaatinschrijving** en **Workplace Join** stappen, waardoor u gemakkelijker dat ze de status van hun apparaat en het proces te voltooien als ze tegenkomt dat er een fout Workplace Join (WPJ). De afzonderlijke stappen worden ook geacht om het te vereenvoudigen voor probleemoplossing voor IT-beheerders. Eerder wanneer eindgebruikers geprobeerd om in te schrijven en alle stappen van de inschrijving is voltooid, met uitzondering van WPJ, zou het geregistreerde apparaat niet weergegeven in de lijst met apparaten voor gebruikers om te identificeren, waardoor verwarring voor gebruikers.

 - **Volledig wissen nu beschikbaar voor Windows 10-apparaten**

    Windows 10-pc's en laptops ingeschreven als mobiele apparaten kunnen u het apparaat opnieuw instellen op de fabrieksinstellingen worden gewist. Zie voor meer informatie [het beveiligen van uw apparaten met wissen op afstand](/sccm/mdm/deploy-use/wipe-lock-reset).

- **Accounts in de iOS-bedrijfsportal-app wordt gewijzigd in Apparaatinschrijvingsmanager.**

  Voor een betere prestaties en schaal, wordt niet meer bij Intune alle Device Enrollment Managers (DEM) apparaten weergegeven in het deelvenster mijn apparaten van de iOS-bedrijfsportal-app. Alleen het lokale apparaat uitvoeren van de app wordt weergegeven, en alleen als het is geregistreerd via de bedrijfsportal-app.

  De gebruiker DEM acties kan uitvoeren op het lokale apparaat, maar extern beheer van andere geregistreerde apparaten kan alleen worden uitgevoerd vanuit de Intune-beheerconsole. Intune wordt daarnaast DEM accounts met de Apple Device Enrollment Program of het hulpprogramma Apple Configurator bestandstypen. Inschrijving van de gebruiker ondersteuning deze inschrijving twee methoden al voor gedeelde iOS-apparaten.

  DEM accounts alleen gebruiken als gebruikersloos inschrijving voor gedeelde apparaten niet beschikbaar is. Zie voor meer informatie [apparaten in Bedrijfseigendom met de Apparaatinschrijvingsbeheerder in Microsoft Intune inschrijven](../deploy-use/enroll-devices-with-device-enrollment-manager.md).

- **Wijzigingen in de Android-bedrijfsportal-app**

  Als eindgebruikers Android ziet een foutbericht met de mededeling hun apparaat dat ontbreekt een vereist certificaat, kunnen ze Tik op een knop "Het oplossen van dit" om stappen voor het installeren van het certificaat ontbreekt. Als gebruikers de stappen, maar een extra "ontbrekend certificaat" Zie foutbericht, wordt gevraagd contact op met hun IT-beheerder en deze koppeling waarin staat beschreven waarmee IT-beheerders los het probleem van het certificaat opgeven.

- **Beperken van extern geladen app-installaties moeten worden ingeschreven Android-apparaten**

  Android-apparaten kunnen geen toepassingen meer installeren via de bedrijfsportal-website tenzij de apparaten zijn ingeschreven in Intune via de Intune-bedrijfsportal-app voor Android.


### <a name="new-in-configuration-manager-technical-preview"></a>Nieuw in Configuration Manager Technical Preview

Er zijn geen nieuwe hybride-functies zijn geïntroduceerd in juli 2016 voor technische Preview van Configuration Manager.

### <a name="new-in-configuration-manager-current-branch"></a>Nieuw in Configuration Manager (huidige vertakking)

De volgende functies die eerder beschikbaar in Configuration Manager technische Preview-versies waren zijn nu beschikbaar in hybride implementaties met Intune en Configuration Manager (huidige vertakking) versie 1606.

* Zoeken, beheren en distribueren van Windows Store voor Business-apps voor Windows 10-apparaten van de Configuration Manager-console ([1604](#new-in-1604-technical-preview))
*     SmartLock-instelling voor Android-apparaten ([1604](#new-in-1604-technical-preview))
*    VPN voor Windows 10-apparaten App geactiveerd ([1605](#new-in-1605-technical-preview))
*    Nieuwe ervaring voor externe apparaat acties ([1605](#new-in-1605-technical-preview))
*    Windows Store voor Business-apps ([1605](#new-in-1605-technical-preview))
*    Algemene verbeteringen voor apps volume aangeschaft ([1605](#new-in-1605-technical-preview))
*    Windows Information Protection (OHW) ([1605](#new-in-1605-technical-preview))
*    Vooraf declareren apparaten in Bedrijfseigendom met IMEI-nummer of iOS-serienummer ([1605](#new-in-1605-technical-preview))
*    Apparaten automatisch categoriseren in verzamelingen ([1606](#new-in-1606-technical-preview))

Zie de documentatie voor de opgegeven technische voorbeeldversie voor informatie over de nieuwe functionaliteit.

## <a name="new-hybrid-features-in-june-2016"></a>Nieuwe functies voor hybride in juni 2016

### <a name="new-in-microsoft-intune"></a>Nieuw in Microsoft Intune
De volgende Intune-functies die is geïntroduceerd in juni 2016 werken in hybride implementaties.

- **Intune-servicestatus** Service statusgegevens voor Intune is verplaatst naar een centrale locatie met andere Microsoft-services. Nu moet u deze informatie vinden in de Office 365-beheerportal onder Servicestatus. Zie voor meer informatie dit [blogbericht](https://blogs.technet.microsoft.com/enterprisemobility/2016/04/28/intune-service-health-is-now-available-in-the-office-365-portal/).

- **Windows 10 enterprise gegevens beleid verbeterde ervaring**

  Intune is nu een verbeterde ervaring voor het configureren van Windows 10 Informatiebeveiligingsbeleid. Verbeteringen zijn betere manieren voor het app-regels maken, grens netwerkdefinitie en andere Windows Information Protection-instellingen opgeven. Zie voor meer informatie, [maken van een Windows-beveiliging (OHW)-beleid met Microsoft Intune](https://technet.microsoft.com/itpro/windows/keep-secure/create-wip-policy-using-intune).

- **Cisco ISE netwerk toegangscontrolebeleid voor Intune**

  Klanten die Cisco identiteit Service Engine (ISE) 2.1 gebruiken en Microsoft Intune ook gebruiken kunnen u een netwerktoegangsbeleid in ISE instellen. Met dit beleid, apparaten die verbinding moeten maken met het netwerk met behulp van Wi-Fi of VPN moeten voldoen aan de volgende voorwaarden voordat ze toegang hebben:

  - Moet worden beheerd door Intune
  - Moet voldoen aan het geïmplementeerde Intune nalevingsbeleid

  Eindgebruikers van niet-compatibele apparaten wordt gevraagd om in te schrijven en herstellen van nalevingsproblemen om toegang te krijgen.

- **Voorwaardelijke toegang voor browser**

  U kunt een beleid voor voorwaardelijke toegang voor Exchange Online en SharePoint Online instellen, zodat ze alleen toegankelijk zijn vanuit ondersteunde webbrowsers op beheerde en compatibele iOS en Android-apparaten. Eindgebruikers die proberen aanmelden bij Outlook Web Access (OWA) en SharePoint-sites met iOS en Android-apparaten wordt gevraagd hun apparaat inschrijven bij Intune ook garantie los eventuele problemen non-compatibiliteit voordat aanmelden kan worden voltooid. Zie voor meer informatie.

  * [Beperk de toegang tot e-mail tot Exchange Online en nieuwe Exchange Online-specifieke met Intune](https://docs.microsoft.com/intune/deploy-use/restrict-access-to-exchange-online-with-microsoft-intune)
  * [Beperk de toegang tot SharePoint Online met Microsoft Intune](https://docs.microsoft.com/intune/deploy-use/restrict-access-to-sharepoint-online-with-microsoft-intune)

- **Dynamics CRM Online ondersteunt voorwaardelijke toegang**

  U kunt een beleid voor voorwaardelijke toegang voor Dynamics CRM Online instellen zodat deze alleen toegankelijk is voor beheerde en compatibele iOS en Android-apparaten. Eindgebruikers die probeert te melden bij de Dynamics CRM mobiele app op iOS en Android wordt gevraagd naar bij Intune worden ingeschreven als non-compatibiliteit problemen verhelpen voordat aanmelden kan worden voltooid. Zie voor meer informatie [Beperk de toegang tot Dynamics CRM Online met Microsoft Intune](https://docs.microsoft.com/intune/deploy-use/restrict-access-to-dynamics-crm-online-with-microsoft-intune).

- **Updates voor de Android-bedrijfsportal-app**

  Intune is nu de volgende nieuwe beleidsregels die gevolgen voor Android-bedrijfsportal gebruikers hebben:   

  Beleid  |Gevolgen voor gebruikers  
  ---------|---------
  Vereisen dat apparaten niet toestaan van installatie van apps van onbekende bronnen (Android 4.0 +)     |  Eindgebruikers kunnen met Android 4.0 of hoger apparaten ziet het bericht, "Installatie van onbekende bronnen moet worden uitgeschakeld." Gebruikers moeten gaat u naar **instellingen > beveiliging** op hun apparaten, en schakel **onbekende bronnen**. Een koppeling in het bericht compatibiliteit kan gebruikers meer informatie over het bericht en waarom ze worden nodig zijn voor de instelling uitschakelen.
  Vereisen dat apparaten niet toestaan van installatie van apps van onbekende bronnen (Android 4.0 +)  |    Eindgebruikers kunnen met Android 4.0 of hoger apparaten ziet het bericht, "Scannen apparaat voor beveiligingsrisico's." Gebruikers moeten gaat u naar **instellingen > Google > beveiliging** op hun apparaten en inschakelen **Scan apparaat voor beveiligingsrisico's**. Een koppeling in het bericht compatibiliteit kunt gebruikers in staat om meer informatie over het bericht en waarom ze zijn vereist om in te schakelen op de instelling.     
  Vereisen dat de USB-foutopsporing is uitgeschakeld (Android 4.2 +)  | Eindgebruikers kunnen met Android 4.2 of latere apparaten ziet het bericht, "USB-foutopsporing moet worden uitgeschakeld." Gebruikers moeten gaat u naar **instellingen > Opties voor ontwikkelaars** op hun apparaten, en schakel **USB-foutopsporing**. Een koppeling in het bericht compatibiliteit kan gebruikers meer informatie over het bericht en waarom ze worden nodig zijn voor de instelling uitschakelen.
  Minimale Android patch beveiligingsniveau (Android 6.0 +)  | Eindgebruikers kunnen met Android 6.0 of latere apparaten ziet het bericht, "dit apparaat voldoet niet aan de minimale Android patch beveiligingsniveau." Gebruikers moeten de vereiste patch installeren. Een koppeling in het bericht compatibiliteit kan gebruikers informatie over het installeren van de vereiste patch en om te zien welke beveiligingspatch ze momenteel zijn geïnstalleerd.

- **Updates voor de iOS-bedrijfsportal-app**

  * Wanneer eindgebruikers van LOB-apps installeren, zien ze nu een verbeterde app-installatie optreden. Als de app-installatie lang duurt, kunnen gebruikers hun apparaten als u wilt afdwingen dat het synchronisatieproces hervatten handmatig synchroniseren. De eindgebruiker instructies, Zie synchronisatie een iOS-apparaat handmatig.
  * De Microsoft Intune-bedrijfsportal-app voor iOS is bijgewerkt om iOS-versie 8.0 en hoger ondersteund. Deze update betekent dat eindgebruikers kunnen de bedrijfsportal-app installeren en nieuwe apparaten in Intune inschrijven alleen als het apparaat iOS-versie 8.0 of hoger wordt uitgevoerd. Gebruikers die werken met eerder ingeschreven apparaten die worden uitgevoerd op een niet-ondersteunde versie van iOS kunnen blijven gebruiken de bedrijfsportal-app op hun apparaat is.


### <a name="new-in-1606-technical-preview"></a>Nieuw in 1606 Technical Preview
De volgende nieuwe functies in juni 2016 zijn beschikbaar in hybride implementaties met Intune en Configuration Manager technische Preview 1606.

- **Apparaten automatisch categoriseren in verzamelingen**

  U kunt categorieën voor apparaatstuurprogramma die kunnen worden gebruikt om apparaten automatisch plaats in apparaatverzamelingen wanneer u Configuration Manager met Intune kunt maken. Vervolgens moeten gebruikers een apparaatcategorie kiezen wanneer ze een apparaat in Intune inschrijft. Bovendien kunt u de categorie van een apparaat wijzigen van de Configuration Manager-console. Zie voor meer informatie [apparaten automatisch categoriseren in verzamelingen](/sccm/core/get-started/capabilities-in-technical-preview-1606#dmp_category) in [mogelijkheden in technische Preview 1606 voor System Center Configuration Manager](/sccm/core/get-started/capabilities-in-technical-preview-1606).

  > [!IMPORTANT]
  > Deze functie werkt met de release van juni 2016 van Microsoft Intune. Zorg ervoor dat u hebt bijgewerkt naar deze versie voordat u deze procedures uitproberen.

### <a name="new-in-configuration-manager-current-branch"></a>Nieuw in Configuration Manager (huidige vertakking)
Er zijn geen nieuwe hybride-functies zijn geïntroduceerd in juni 2016 voor Configuration Manager (huidige vertakking).

##  <a name="new-hybrid-features-in-may-2016"></a>Nieuwe functies voor hybride in mei 2016  

### <a name="new-in-microsoft-intune"></a>Nieuw in Microsoft Intune  
 De volgende Intune-functies die is geïntroduceerd in mei 2016 werken in hybride implementaties.

- **MAM SDK: Ondersteuning voor PINCODE lengte configuratie**

  U kunt nu de lengte van de PINCODE voor MAM apps vergelijkbaar met een apparaat PINCODE opgeven. Hiervoor moet eindgebruikers om te voldoen aan de nieuwe beperkingen. Het scherm PINCODE is iets aan het account voor de langer invoer gewijzigd. Zie voor meer informatie, [MAM-beleidsinstellingen voor Android](https://docs.microsoft.com/intune/deploy-use/android-mam-policy-settings), en [MAM-beleidsinstellingen voor iOS](https://docs.microsoft.com/intune/deploy-use/ios-mam-policy-settings).  

- **Skype voor bedrijven voor iOS en Android**

  U kunt nu Skype voor bedrijven met als doel [MAM zonder inschrijvingsbeleid](https://docs.microsoft.com/intune/deploy-use/get-ready-to-configure-mobile-app-management-policies-with-microsoft-intune). Als gebruikers zich aanmelden, wordt de MAM-beleid toegepast.  

- **Nieuwe apps beschikbaar zijn voor beheer met MAM-beleid**

  De Microsoft Word, Excel en PowerPoint apps voor Android kunnen nu worden gekoppeld aan MAM-beleid op apparaten die niet zijn ingeschreven met Intune. Ga voor een volledige lijst met ondersteunde apps de galerie met Microsoft Intune mobiele toepassingen op de [partners voor Microsoft Intune-toepassing](https://www.microsoft.com/en-us/server-cloud/products/microsoft-intune/partners.aspx) pagina.  

- **Android-bedrijfsportal-app: Eindgebruiker toast meldingen**

  Toast meldingen van het Android-bedrijfsportal-app worden weergegeven wanneer eindgebruikers schrijven of te verwijderen van hun apparaten via de bedrijfsportal.  

- **Portal-website van bedrijf: Apparaat-id banner geven informatie voor eindgebruikers**

  Eindgebruikers kunnen nu gemakkelijker identificatie van het apparaat dat ze hebt geselecteerd wanneer ze de bedrijfsportal-website gebruiken. Als het verkeerde apparaat is ingeschakeld, kunnen ze het juiste apparaat selecteren door te tikken op de **Tik hier** koppeling in de koptekst van de startpagina.  


### <a name="new-in-1605-technical-preview"></a>Nieuw in 1605 Technical Preview  
 De volgende nieuwe functies in mei 2016 zijn beschikbaar in hybride implementaties met Intune en Configuration Manager technische Preview 1605. Deze functies vereisen dat u de Configuration Manager-console gebruiken om te configureren en beheren.  

- **App geactiveerd VPN voor Windows 10-apparaten**

  Voor Windows 10-apparaten worden beheerd met Configuration Manager met Intune, kunt u een lijst met apps die automatisch een VPN-verbinding die u hebt geconfigureerd via de Configuration Manager-beheerconsole opent toevoegen. Zie voor meer informatie [VPN-App is geactiveerd voor Windows 10-apparaten](/sccm/core/get-started/capabilities-in-technical-preview-1605) in [mogelijkheden in technische Preview 1605 voor System Center Configuration Manager](/sccm/core/get-started/capabilities-in-technical-preview-1605)  

- **Nieuwe ervaring voor externe apparaat acties**

  De ervaring voor het externe apparaat acties uit te voeren vanuit de Configuration Manager-console, is verbeterd.

  Algemene acties zoals **buiten gebruik stellen/wissen**, **wachtwoordcode opnieuw instellen**, **vergrendelen op afstand**, en **Bypass Activeringsvergrendeling** is nu te vinden de **externe apparaat acties** menu toegankelijk is via de **activa en naleving** werkruimte

  Zie voor meer informatie [nieuwe ervaring voor externe apparaat acties](/sccm/core/get-started/capabilities-in-technical-preview-1605#new-experience-for-remote-device-actions) in [mogelijkheden in technische Preview 1605 voor System Center Configuration Manager](/sccm/core/get-started/capabilities-in-technical-preview-1605).  

- **Windows Store voor Business-apps**

  De [Windows Store voor bedrijven](https://www.microsoft.com/en-us/business-store) kunt u vinden en apps koopt voor uw organisatie, afzonderlijk of in volume. Verbinding maken met de store naar de Configuration Manager, kunt u apps volume aangeschaft beheren vanuit de Configuration Manager-console. Zie voor meer informatie [Windows Store voor Business-apps](/sccm/core/get-started/capabilities-in-technical-preview-1605.md#windows-store-for-business-apps) in [mogelijkheden in technische Preview 1605 voor System Center Configuration Manager](/sccm/core/get-started/capabilities-in-technical-preview-1605).  

- **Algemene verbeteringen voor volume aangeschaft apps**

  Volume aangeschaft apps uit de Windows Store voor bedrijven en de iOS appstore zijn samengevoegd in dezelfde weergave **licentie-informatie voor Apps opslaan**. Ook moet is de manier waarop u volume aangeschaft apps voor iOS maken verbeterd. Zie voor meer informatie[algemene verbeteringen voor apps volume aangeschaft](/sccm/core/get-started/capabilities-in-technical-preview-1605.md#general-improvements-for-volume-purchased-apps) in [mogelijkheden in technische Preview 1605 voor System Center Configuration Manager](/sccm/core/get-started/capabilities-in-technical-preview-1605).  

- **Vooraf declareren apparaten in Bedrijfseigendom met IMEI-nummer of iOS-serienummer**

  U kunt nu apparaten in Bedrijfseigendom identificeren door het importeren van hun internationale station mobile equipment identity (IMEI) getallen. U kunt een apparaat IMEI getallen met door komma's gescheiden waarden (.csv)-bestand uploaden of u kunt de apparaatgegevens handmatig invoeren.  U kunt ook importeren serienummers voor iOS-apparaten.  Zie voor meer informatie [vooraf declareren apparaten in Bedrijfseigendom met IMEI-nummer of iOS-serienummer](../../core/get-started/capabilities-in-technical-preview-1605.md#BKMK_IMEI) in [mogelijkheden in technische Preview 1605 voor System Center Configuration Manager](/sccm/core/get-started/capabilities-in-technical-preview-1605).  

- **Windows Information Protection (OHW)**

  U kunt configuratie-items u uw Windows-beveiliging (OHW)-beleid kunnen, inclusief zodat u ervoor kiezen uw beveiligde apps, uw OHW beveiligingsniveau en zoeken naar enterprise gegevens op het netwerk kunt implementeren. Zie de volgende onderwerpen voor meer informatie over OHW:  

  -   [Uw Ondernemingsgegevens beveiligen via Windows-beveiliging (OHW)](https://technet.microsoft.com/itpro/windows/keep-secure/protect-enterprise-data-using-wip)  

  -   [Maken en implementeren van een Windows-beveiliging (OHW)-beleid met behulp van System Center Configuration Manager](https://technet.microsoft.com/itpro/windows/keep-secure/create-wip-policy-using-sccm)  

### <a name="new-in-configuration-manager-current-branch"></a>Nieuw in Configuration Manager (huidige vertakking)  
 Er zijn geen nieuwe hybride-functies zijn geïntroduceerd in mei 2016 voor Configuration Manager (huidige vertakking).  

##  <a name="new-hybrid-features-in-april-2016"></a>Nieuwe functies voor hybride in April 2016  

### <a name="new-in-microsoft-intune"></a>Nieuw in Microsoft Intune  
 De volgende Intune-functies die is geïntroduceerd in April 2016 werken in hybride implementaties.  

- **MAM gebruikerscompatibiliteit**

  U kunt nu de status van uw beleid voor het beheer van toepassingen voor gebruikers in uw tenant Azure Active Directory (AAD) weergeven.  Zie voor meer informatie [bewaken mobiele app management-beleid met Microsoft Intune](/intune/deploy-use/monitor-mobile-app-management-policies-with-microsoft-intune) in de Intune-bibliotheek.  

- **MAM besturingselementen om te voorkomen dat de synchronisatie van Outlook-contactpersonen (Android)**

  Vindt u een nieuwe instelling waarmee u om te voorkomen dat een toepassing met het synchroniseren van contactpersonen aan het systeemeigen adresboek op Android-apparaten. Deze nieuwe instelling wordt in eerste instantie ondersteund door de Outlook-toepassing op Android-apparaten. Zie voor meer informatie [maken en implementeren van beleid voor beheer van mobiele app met Microsoft Intune](/intune/deploy-use/monitor-mobile-app-management-policies-with-microsoft-intune) in de Intune-bibliotheek.  

- **Verbeteringen in de bedrijfsportal-website**

  Wanneer Windows 10 Mobile- en Windows Phone 8.1-gebruikers LOB-apps installeert, zien ze nu de volgende nieuwe statussen, die ze bieden voor meer informatie over de status van de installatie:  

  -   **Wachten op apparaat synchroniseren** : de gebruiker heeft wel "Installeren" en het apparaat wordt nu geprobeerd om te synchroniseren met de Intune-infrastructuur. De synchronisatie is vereist voordat de installatie te voltooien. Het bericht "Wachten apparaat synchroniseren" is ook een koppeling waarmee gebruikers kunnen Tik om te zien instructies over het handmatig synchroniseren van hun apparaten met Intune als het synchronisatieproces lang duurt of vastgelopen opgehaald.  

  -   **Downloaden van** : de gebruiker downloadverzoek wordt verwerkt en het apparaat is downloaden en installeren de app.  

- **Verbeteringen in de Android-bedrijfsportal-app**

  Gebruikers die hun apparaat in Intune niet hebben ingeschreven en die hoeven niet het juiste certificaat geïnstalleerd pas weer aanmelden bij de Android-bedrijfsportal-app en het bericht wordt weergegeven, "Je niet aanmelden omdat uw apparaat ontbreekt een vereist certificaat." Het bericht bevat een koppeling naar "Het oplossen van dit" die gebruikers kunnen Tik om te zien instructies voor het installeren van het certificaat. Zie voor de stappen die eindgebruikers kunnen uitvoeren als het probleem wilt oplossen, [uw apparaat ontbreekt een vereist certificaat](/intune/enduser/using-your-android-device-with-intune) in de Intune-bibliotheek.  

- **Verbeteringen in de bedrijfsportal-app voor iOS**

  Er is ondersteuning toegevoegd voor de actie pull te vernieuwen vernieuwen van de inhoud op het startscherm, waaronder de apps in lijst apparaten in de lijst en IT-contactpersoon informatie. De actie pull te vernieuwen, controleert niet compatibiliteit of beleid gegevens, die kan worden uitgevoerd door de tegel voor uw huidige apparaat te selecteren en vervolgens op de **Sync** knop.  

- **Verbeteringen in Windows 10 Mobile- en Windows Phone 8.1-bedrijfsportal bedrijfsportal-app**

  Wanneer eindgebruikers van LOB-apps installeren, zien ze nu een verbeterde app-installatie optreden. Als de app-installatie lang duurt, kunnen gebruikers hun apparaten als u wilt afdwingen dat het synchronisatieproces hervatten handmatig synchroniseren. De eindgebruiker instructies, Zie [synchroniseren van uw apparaat handmatig installeren van apps sneller](/intune/enduser/using-your-windows-device-with-intune) in de Intune-bibliotheek.  

###  <a name="new-in-1604-technical-preview"></a>Nieuw in 1604 Technical Preview
 De volgende nieuwe functies in April 2016 zijn beschikbaar in hybride implementaties met Intune en Configuration Manager technische Preview 1604. Deze functies vereisen dat u de Configuration Manager-console gebruiken om te configureren en beheren.  

- **Zoeken, beheren en distribueren van Windows Store voor Business-apps voor Windows 10-apparaten van de Configuration Manager-console**


  Ondersteuning voor Windows Store voor bedrijven is beschikbaar in Configuration Manager technische Preview 1604 om te zoeken, beheren en distribueren van apps voor de Windows 10-apparaten die u wilt beheren. Zie voor meer informatie, [volume aangeschaft apps beheren vanuit de Windows Store voor bedrijven](/sccm/core/get-started/capabilities-in-technical-preview-1604#manage-volume-purchased-apps-from-the-windows-store-for-business) in [mogelijkheden in technische Preview 1604 voor System Center Configuration Manager](/sccm/core/get-started/capabilities-in-technical-preview-1604).  

- **SmartLock-instelling voor Android-apparaten**

  Een nieuwe instelling is toegevoegd aan de Android en Samsung KNOX Standard configuratie-item dat u kunt de functie SmartLock op Android-compatibele apparaten beheren.  U kunt deze instelling gebruiken om te voorkomen dat eindgebruikers SmartLock configureren. Zie [SmartLock-instelling voor Android-apparaten](/sccm/get-started/capabilities-in-technical-preview-1604#smartlock-setting-for-android-devices) in [mogelijkheden in technische Preview 1604 voor System Center Configuration Manager](/sccm/core/get-started/capabilities-in-technical-preview-1604.md).  

### <a name="new-in-configuration-manager-current-branch"></a>Nieuw in Configuration Manager (huidige vertakking)  
 Er zijn geen nieuwe functies voor hybride werden geïntroduceerd in April 2016 voor Configuration Manager (huidige vertakking).  

##  <a name="new-hybrid-features-in-march-2016"></a>Nieuwe functies voor hybride in maart 2016  

### <a name="new-in-microsoft-intune"></a>Nieuw in Microsoft Intune  
 De volgende Intune-functies die is geïntroduceerd in maart 2016 werken in hybride implementaties.  

- **MAM besturingselementen om te voorkomen dat de Outlook-contactpersonen sync (iOS)**

  Vindt u een nieuwe instelling waarmee u om te voorkomen dat een toepassing met het synchroniseren van contactpersonen aan het systeemeigen adresboek op iOS-apparaten. Deze nieuwe instelling wordt ondersteund door de Outlook-toepassing op iOS-apparaten. Zie voor meer informatie over deze en andere instellingen [maken en implementeren van beleid MAM](/intune/deploy-use/monitor-mobile-app-management-policies-with-microsoft-intune) in de Intune-bibliotheek.  

- **Skype voor bedrijven Online ondersteunt voorwaardelijke toegang**

  U kunt een beleid voor voorwaardelijke toegang voor Skype voor bedrijven Online instellen zodat deze alleen toegankelijk is voor beheerde en compatibele iOS en Android-apparaten.  Zie voor meer informatie, [toegang beheren tot Skype voor bedrijven Online](/intune/deploy-use/restrict-access-to-skype-for-business-online-with-microsoft-intune) in de Intune-bibliotheek.  

- **Ondersteuning voor iOS 9,3**

  Op maandag maart 21 aangekondigd Apple de beschikbaarheid van iOS 9.3. Alle bestaande Intune-functies die momenteel beschikbaar is voor het beheren van iOS-apparaten blijven werken naadloos gebruikers hun apparaten voor iOS 9.3 upgraden.  

- **Windows app-pakketten beschikbaar rechtstreeks vanuit de bedrijfsportal-website**

  Gebruikers van Windows 8, Windows 8.1 en Windows RT-pc's kunnen nu Windows app-pakketten (met de extensie .appx) rechtstreeks vanaf de website van de bedrijfsportal installeren. Voorheen moest u implementeren of moesten gebruikers de bedrijfsportal-app installeren op hun apparaten om apps te installeren.  

- **Gebruikers kunnen hun apparaat van de bedrijfsportal-website op afstand vergrendelen**

  Een nieuwe optie vergrendelen op afstand is toegevoegd aan de bedrijfsportal-website waarmee gebruikers kunnen hun apparaat via de Portal op afstand vergrendelen als hun apparaat is vermist of gestolen.  

- **Profiteren van iOS "Openen in" beheer voor apparaten die zijn ingeschreven in een derde MDM-oplossing**

  U kunt de leverancier van uw mobiele apparaten van derden management (MDM) gebruiken om te profiteren van iOS "Openen In" management. U kunt de beperkingen in de configuratie van de profielinstellingen en implementeer de app met uw MDM-software. Wanneer de gebruiker de beheerde app is geïnstalleerd, worden de beperkingen toegepast. Voor meer informatie: [Microsoft Intune mobile app management-beleid en iOS openen In](/intune/deploy-use/introduction-to-device-compliance-policies-in-microsoft-intune) in de Intune-bibliotheek.  

- **Microsoft-apps die ondersteuning bieden voor MAM**

  De lijst met Microsoft-apps die kunt u met Intune mobile application management-beleid is bijgewerkt zodat de meest recente apps (voor apparaten die zijn ingeschreven met Intune alleen).  

- **Adobe Reader voor Microsoft Intune implementeren voor Intune beheerde iOS-apparaten in uw onderneming**

  De Adobe Reader-app voor iOS kan nu worden beheerd op ingeschreven apparaten met de Intune mobile application management-beleid.  

- De Rights Management-app voor delen wordt ondersteund voor Android

  IT-beheerders mobile application management-beleid kunnen implementeren, zodat eindgebruikers bekijken, afbeeldingen, AV en PDF kunnen-bestanden veiliger of IT Intune gebruikt om de apparaten te beheren.  

- **Verbeteringen in de Android en iOS-bedrijfsportal-app**

  -   Wanneer uw gebruikers een app die wordt beheerd door beheer van mobiele toepassingen (MAM) start, zien ze een bericht met de mededeling dat de app wordt beheerd door hun bedrijf. Gebruikers kunnen nu Tik op een koppeling "Meer informatie over" hier meer informatie over wat betekent "beheerde apps". Ze kunnen ook Tik op "Niet meer weergeven" zodat het bericht niet meer wordt weergegeven wanneer ze de app starten.  

  -   Nieuwe schermen zijn toegevoegd aan gebruikers via het inschrijvingsproces geleid en meer informatie over waarom de gebruikers te registreren en IT-beheerders kunnen en kunnen niet op de geregistreerde apparaten bekijken.  

  -   Inschrijving foutberichten worden nu weergegeven in de bedrijfsportal-app.  

### <a name="new-in-configuration-manager-technical-preview"></a>Nieuw in Configuration Manager Technical Preview  
 Er zijn geen nieuwe functies voor hybride werden geïntroduceerd in maart 2016 voor technische Preview van Configuration Manager.  

### <a name="new-in-configuration-manager-current-branch"></a>Nieuw in Configuration Manager (huidige vertakking)  
 De volgende nieuwe functies in maart 2016 zijn beschikbaar in hybride implementaties met Intune en Configuration Manager (huidige vertakking) versie 1602. Deze functies vereisen dat u de Configuration Manager-console gebruiken om te configureren en beheren.  

- **configuratiebeleid voor iOS-app**

  In versie 1602 van Configuration Manager (huidige vertakking) kunt u beleidsregels voor app-configuratie op te geven van de instellingen die vereist zijn kunnen wanneer de gebruiker een iOS-app wordt uitgevoerd. Zie voor meer informatie, [iOS-apps met app-configuratiebeleid in System Center Configuration Manager configureren](/sccm/apps/deploy-use/configure-ios-apps-with-app-configuration-policies).  

- **Volume aangeschaft iOS-apps beheren**

  U kunt in versie 1602 van Configuration Manager (huidige vertakking), implementeren en beheren van apps die u hebt aangeschaft in volume uit de Apple Volume aankoop programma (VPP) door de licentiegegevens uit de appstore en bijhouden hoeveel van de licenties die u hebt gebruikt. Zie voor meer informatie, [volume aangeschaft iOS-apps met System Center Configuration Manager beheren](/sccm/apps/deploy-use/manage-volume-purchased-ios-apps).  

- **Automatische aanmaak van mobiele Office-apps**

  Vanaf versie 1602 van Configuration Manager (huidige vertakking), worden Microsoft Office de volgende mobiele apps voor Android en iOS gemaakt wanneer u een van versie 1511 upgrade:  

  -   Microsoft Word  
  -   Microsoft Excel  
  -   Microsoft PowerPoint  
  -   Microsoft OneDrive  
  -   Microsoft OneNote (alleen iOS)  
  -   Microsoft Outlook  

  Deze apps vindt u in het knooppunt toepassingen van de Configuration Manager-console. Zie voor meer informatie over het implementeren van toepassingen [het implementeren van toepassingen met System Center Configuration Manager](../../apps/deploy-use/deploy-applications.md).  

- **Instellingen voor kioskmodus voor Android Samsung KNOX Standard-apparaten**

  Met de kioskmodus kunt u een apparaat zo vergrendelen dat alleen bepaalde functies werken.  Vanaf versie 1602 van Configuration Manager (huidige vertakking), kunt u nu instellingen opgeven voor kioskmodus voor Samsung KNOX Standard-apparaten. Zie voor meer informatie, [het maken van configuratie-items voor Android en Samsung KNOX Standard-apparaten beheerd zonder dat de System Center Configuration Manager-client](/sccm/compliance/deploy-use/create-configuration-items-for-android-and-samsung-knox-devices-managed-without-the-client).  

- **iOS Activeringsvergrendeling**

  Vanaf versie 1602 van Configuration Manager (huidige vertakking), kunt u iOS Activeringsvergrendeling, een functie van de app Zoek mijn iPhone voor iOS 7.1 en hoger apparaten beheren. Activeringsvergrendeling is automatisch ingeschakeld wanneer de app Zoek mijn iPhone op een apparaat wordt gebruikt.  Zie voor meer informatie, [beheren iOS Activeringsvergrendeling overslaan voor System Center Configuration Manager](/sccm/mdm/deploy-use/manage-ios-activation-lock#bypass-activation-lock).  

