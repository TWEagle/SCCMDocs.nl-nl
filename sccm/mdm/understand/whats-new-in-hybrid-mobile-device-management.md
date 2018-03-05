---
title: Wat is er nieuw in hybride MDM
titleSuffix: Configuration Manager
description: Meer informatie over de nieuwe functies voor mobiele apparaten beschikbaar voor hybride implementaties met Configuration Manager en Intune.
ms.custom: na
ms.date: 03/01/2018
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-hybrid
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 7b127cee-61f1-4681-9760-caebed36ddf5
author: aczechowski
ms.author: aaroncz
manager: dougeby
ms.openlocfilehash: 3b48c5296caecd66b5abb6d40578af2009ef0f11
ms.sourcegitcommit: 6e4fca19083b5dbdcd841012f6e1051bb7c00eb8
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 03/05/2018
---
# <a name="whats-new-in-hybrid-mobile-device-management-with-configuration-manager-and-microsoft-intune"></a>Wat is er nieuw in hybride mobile device management met Configuration Manager en Microsoft Intune

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*

Dit artikel bevat informatie op de nieuwe mobiele apparaat management (MDM)-functies die beschikbaar zijn voor hybride implementaties met System Center Configuration Manager en Microsoft Intune.     

> [!Note]    
> Intune in Azure is de aanbevolen MDM-oplossing van Microsoft.     
> - Zie voor meer informatie over nieuwe functies en -updates in de zelfstandige versie van Intune [wat is er nieuw in Intune](https://docs.microsoft.com/intune/whats-new).    
> - Zie voor meer informatie over het migreren naar Intune zelfstandige [hybride MDM-gebruikers en apparaten migreren naar Intune standalone](https://docs.microsoft.com/sccm/mdm/deploy-use/migrate-hybridmdm-to-intunesa).
> - Zie voor meer informatie over updates van de gebruikersinterface voor Intune en hybride MDM [UI-updates voor Intune-eindgebruikers apps](https://docs.microsoft.com/intune/whats-new-app-ui). 

##  <a name="compatibility-with-configuration-manager-versions"></a>Compatibiliteit met versies van Configuration Manager  
Elke sectie van dit artikel vindt u hybridefuncties onder drie verschillende categorieën. Gebruik de volgende richtlijnen om te bepalen of de functies in elke categorie compatibel is met verschillende versies van Configuration Manager:  

|Functie categorieën|Beschrijving|
|-|-|
|**Nieuw in Microsoft Intune** | In het algemeen moeten alle functies die worden vermeld in deze categorie samen met alle versies van de Configuration Manager. Deze inclusief System Center 2012 R2 Configuration Manager worden vrijgegeven, aangezien deze functies alleen de Intune-service nodig en niet aanvullende functionaliteit in Configuration Manager hoeven.|
|**Nieuw in Configuration Manager Technical Preview**| Alle functies die worden vermeld in deze categorie werken alleen met de opgegeven Technical Preview-versie. Als u wilt deze functies uit te proberen, moet u de Technical Preview-versie die is opgegeven in de beschrijving van de functie installeren. Zie voor meer informatie [Technical Preview voor System Center Configuration Manager](../../core/get-started/technical-preview.md).|
|**Nieuw in Configuration Manager (huidige vertakking)**| Alle functies die worden vermeld in deze categorie werken alleen met de opgegeven versie van Configuration Manager (huidige vertakking), zoals versie 1511 of 1602. Als u een oudere versie van Configuration Manager voor uw hybride implementatie gebruikt, moet u upgraden naar de Configuration Manager (huidige vertakking) versie opgegeven in de beschrijving van de functie. Zie voor meer informatie [upgraden naar System Center Configuration Manager](../../core/servers/deploy/install/upgrade-to-configuration-manager.md).|



## <a name="february-2018"></a>2018 februari

### <a name="new-in-microsoft-intune"></a>Nieuw in Microsoft Intune

- **Mac OS bedrijfsportal ondersteuning voor inschrijvingen die gebruikmaken van de Apparaatinschrijvingsbeheerder**  
    Gebruikers kunnen nu de Apparaatinschrijvingsbeheerder gebruiken bij het inschrijven met de Mac OS-bedrijfsportal.
    <!-- 1352411 -->


## <a name="january-2018"></a>2018 januari

### <a name="new-in-microsoft-intune"></a>Nieuw in Microsoft Intune

- **Goedkeuren van de bedrijfsportal-app voor Android for Work.**  
  Als uw organisatie Android for Work gebruikt, handmatig goedkeuren van de bedrijfsportal-app voor Android. Vervolgens gaat door Automatische updates ontvangen van de beheerde Google Play store.
  <!--1797090 -->  

- **Beleid voor voorwaardelijke toegang voor Intune zijn alleen beschikbaar in de Azure-portal**   
  Vanaf deze release, moet u configureren en beheren van uw beleid voor voorwaardelijke toegang in de [Azure-portal](https://portal.azure.com) van **Azure Active Directory** > **voorwaardelijke toegang** . Voor uw gemak u kunt ook toegang tot deze blade van Intune in de Azure portal op **Intune** > **voorwaardelijke toegang**.
  <!-- 1737088 1634311 --> 

- **Updates voor naleving e-mailberichten**    
  Wanneer een e-mailbericht wordt verzonden naar een niet-compatibel apparaat rapporteren, wordt informatie over de niet-compatibel apparaat zijn opgenomen. 
  <!--1637547 -->

- **Nieuwe functionaliteit voor de actie 'Los' voor Android-apparaten**    
  De bedrijfsportal-app voor Android is de actie 'Los' voor uitbreidbare **bijwerken apparaatinstellingen** om op te lossen [apparaat versleuteling problemen](https://docs.microsoft.com/intune-user-help/encrypt-your-device-android).
  <!--1583480-->

- **Vergrendelen op afstand beschikbaar in de bedrijfsportal-app voor Windows 10**    
  Eindgebruikers kunnen hun apparaten uit de bedrijfsportal-app nu op afstand vergrendelen voor Windows 10. Deze actie wordt niet weergegeven voor het lokale apparaat dat actief wordt gebruikt.
  <!--676506-->

- **Eenvoudiger oplossen van problemen met naleving voor de bedrijfsportal-app voor Windows 10**   
  Eindgebruikers met Windows-apparaten kunt tikt u op de niet-naleving reden hiervoor in de bedrijfsportal-app. Indien mogelijk, gaan deze actie ze rechtstreeks naar de juiste locatie in de app instellingen om het probleem te verhelpen.
  <!--676546-->    



## <a name="december-2017"></a>December 2017

### <a name="new-in-microsoft-intune"></a>Nieuw in Microsoft Intune

- **Beschikbare implementaties nu ondersteund voor Android Enterprise**    
  U kunt nu Android Enterprise (voorheen Android for Work) apps implementeren als **beschikbaar**, naast **vereist**. Zie voor meer informatie [maken Android-toepassingen met System Center Configuration Manager](/sccm/mdm/deploy-use/creating-android-applications).



## <a name="november-2017"></a>November 2017

### <a name="new-in-microsoft-intune"></a>Nieuw in Microsoft Intune

- **Tekst-protocol toegestaan van beheerde Apps**  
  Apps die worden beheerd door de Intune App SDK zijn SMS-berichten verzenden.
  <!-- 1414050  -->   

- **Bedrijfsportal-app voor Mac OS is beschikbaar**   
  De Intune-bedrijfsportal op Mac OS heeft een nieuwe ervaring. Is geoptimaliseerd om alle informatie en naleving meldingen die uw gebruikers nodig hebben voor alle apparaten die ze hebben ingeschreven foutloos weer te geven. En nadat de Intune bedrijfsportal is geïmplementeerd op een apparaat, Microsoft AutoUpdate voor Mac OS biedt deze updates. Download de nieuwe Intune-bedrijfsportal voor Mac OS door aan te melden bij de Intune-bedrijfsportal-website vanaf een Mac OS-apparaat.
  <!--1541700-->   

- **Microsoft Planner maakt nu deel uit van de mobiele app management (MAM)-lijst met goedgekeurde apps**    
  De app Microsoft Planner voor iOS en Android is nu onderdeel van de goedgekeurde apps voor mobile app management (MAM). Configureer de app via de Intune App Protection blade in de Azure portal voor alle tenants. Zie voor meer informatie [MAM lijst met goedgekeurde apps](https://www.microsoft.com/cloud-platform/microsoft-intune-apps).
  <!-- 1248473 -->    

- **Toegang tot de logboeken van de beheerde app voor iOS**    
  Eindgebruikers met de beheerde Browser is geïnstalleerd, kunnen nu de weergave de status van beheer van alle Microsoft gepubliceerde apps en logboeken voor het oplossen van hun beheerde iOS-apps verzendt.
  <!-- 1469920 -->    

  Meer informatie over het inschakelen van de probleemoplossingsmodus in de Managed Browser op een iOS-apparaat, Zie [hoe de toegang tot beheerde app logboeken met behulp van de Managed Browser voor iOS](https://docs.microsoft.com/intune/app-configuration-managed-browser#how-to-access-to-managed-app-logs-using-the-managed-browser-on-ios).

- **Verbeteringen in apparaat instellen werkstroom in de bedrijfsportal voor iOS in versie 2.9.0**    
  We hebben de apparaat-setup-werkstroom in de bedrijfsportal-app voor iOS verbeterd. De taal is gebruikersvriendelijker en we schermen hebt gecombineerd waar mogelijk. We hebben de taal ook meer specifieke aangebracht in uw bedrijf met behulp van de naam van uw bedrijf overal in de setup-tekst. U kunt deze bijgewerkte werkstroom zien op de [wat is er nieuw in app UI](https://docs.microsoft.com/intune/whats-new-app-ui#week-of-november-13-2017) pagina.

- **Feedback wordt u gevraagd om de bedrijfsportal-app voor Android**    
  De bedrijfsportal-app voor Android is nu aanvragen van feedback van eindgebruikers. Deze feedback wordt rechtstreeks naar Microsoft verzonden en hebben eindgebruikers dankzij de mogelijkheid om te controleren van de app in de openbare Google Play store. Feedback is niet vereist en kan eenvoudig worden gesloten zodat gebruikers kunnen doorgaan met de app. 
  <!--1165249-->    

- **Eindgebruikers informeren over welke gegevens van een apparaat worden weergegeven voor Windows 10-apparaten**    
  We hebben toegevoegd **eigendomstype** naar het scherm Apparaatdetails op de bedrijfsportal-app voor Windows 10. Deze informatie kan gebruikers meer informatie over privacy rechtstreeks vanuit de Intune-eindgebruikers-documenten. Ze kunnen ook deze informatie vinden op de **over** scherm.
  <!--1337920-->    

- **Nieuwe 'Oplossen' actie beschikbaar voor Android-apparaten**    
  De bedrijfsportal-app voor Android introduceert een actie 'Oplossen' op de _bijwerken apparaatinstellingen_ pagina. Als u deze optie selecteert, gaat de gebruiker rechtstreeks naar de instelling die wordt veroorzaakt door hun apparaat niet compatibel is. De bedrijfsportal-app voor Android ondersteunt momenteel deze actie uit voor de [wachtwoordcode](https://docs.microsoft.com/intune-user-help/set-your-pin-or-password-android), [apparaatversleuteling](https://docs.microsoft.com/intune-user-help/encrypt-your-device-android), [USB-foutopsporing](https://docs.microsoft.com/intune-user-help/you-need-to-turn-off-usb-debugging-android), en [onbekend Bronnen](https://docs.microsoft.com/intune-user-help/you-need-to-turn-off-unknown-sources-android) instellingen. 
  <!--1583480-->    


### <a name="new-in-configuration-manager-current-branch"></a>Nieuw in Configuration Manager (huidige vertakking)

- **Acties voor niet-naleving**    
  U kunt nu een tijd besteld reeks acties die worden toegepast op apparaten die niet compatibel. U kunt bijvoorbeeld meldingen verzenden naar gebruikers van niet-compatibele apparaten via e-mail of die apparaten niet-compatibele markeren. Zie voor meer informatie [acties instellen voor niet-naleving](/sccm/mdm/deploy-use/actions-for-noncompliance).
  <!--1321366 -->

- **Nieuwe beleidsinstellingen voor mobile application management**     
  De volgende instellingen zijn toegevoegd aan de mobiele toepassing management-beleidsinstellingen:
  - **Synchronisatie van contactpersonen uitschakelen**: Hiermee voorkomt dat de app opslaan van gegevens in de systeemeigen contactpersonen-app op het apparaat.
  - **Afdrukken uitschakelen**: Voorkomt dat de app vanuit afdrukken werk- of schoolgegevens.
  <!-- 1324760 -->    

  Zie [apps beveiligen met beleid voor app-beveiliging in Configuration Manager](/sccm/mdm/deploy-use/protect-apps-using-mam-policies) om te proberen de nieuwe beleidsinstellingen van de app-beveiliging.

- **Ondersteuning voor Windows 10 ARM64 apparaten**     
  Hybride mobile device management (MDM)-scenario's worden ondersteund op ARM64 apparaten met Windows 10 wanneer deze apparaten beschikbaar zijn. Zie voor meer informatie [ondersteuning voor Windows 10 ARM64 apparaten](/sccm/core/plan-design/changes/whats-new-in-version-1710#windows-10-arm64-device-support).
  <!-- 1355000 -->    

- **Verbeterde ervaring van VPN-profiel in de Configuration Manager-console**     
  We hebben de VPN-profiel wizard eigenschappen pagina's en om weer te geven van de instellingen die geschikt is voor het geselecteerde platform bijgewerkt met deze release. Deze functie was eerder beschikbaar in Configuration Manager Technical Preview 1709. Het is nu beschikbaar in hybride implementaties met Intune en Configuration Manager (huidige vertakking) versie 1710. Zie voor meer informatie [verbeterd VPN-profiel ervaring in Configuration Manager-console](/sccm/core/plan-design/changes/whats-new-in-version-1710#improved-vpn-profile-experience-in-configuration-manager-console).
  <!-- 1318232 -->


### <a name="new-in-configuration-manger-technical-preview-1711"></a>Nieuw in Configuration Manager Technical Preview 1711

- **Nieuwe opties voor nalevingsbeleid voor Windows 10**   
  U kunt nu de nieuwe opties voor nalevingsbeleid voor Windows 10-apparaten configureren. De nieuwe instellingen omvatten beleid voor de Firewall, User Account Control, Windows Defender Antivirus en OS-build-versiebeheer. Zie voor meer informatie [nieuwe opties voor nalevingsbeleid voor Windows 10](/sccm/core/get-started/capabilities-in-technical-preview-1711#new-compliance-policy-options-for-windows-10).



## <a name="october-2017"></a>Oktober 2017

### <a name="new-in-configuration-manager-technical-preview-1709"></a>Nieuw in Configuration Manager Technical Preview 1709

- **Verbeterde ervaring voor VPN-profiel in Configuration Manager-console**      
  Instellingen voor VPN-profiel zijn nu gefilterd volgens platform. Wanneer u nieuwe VPN-profielen maken, bevat elk ondersteund platform alleen de instellingen die geschikt is voor het platform. Bestaande VPN-profielen worden niet getroffen. U kunt meer lezen over deze wijziging [hier](/sccm/core/get-started/capabilities-in-technical-preview-1709#improved-vpn-profile-experience-in-configuration-manager-console).
  <!-- 1313282 -->


### <a name="new-in-microsoft-intune"></a>Nieuw in Microsoft Intune  

- **Uw gebruikers helpen zichzelf aan de bedrijfsportal-app voor Android**     
  De bedrijfsportal-app voor Android is instructies voor eindgebruikers om te begrijpen en oplossen mogelijk zelf op nieuwe gebruiksvoorbeelden toegevoegd.
    - Als eindgebruikers hebben bereikt het maximumaantal apparaten die ze kunnen toevoegen, worden ze geleid naar de [Azure Active Directory-portal](https://account.activedirectory.windowsazure.com/r/#/profile) om een apparaat te verwijderen.
    - Eindgebruikers krijgen stappen volgen om u te helpen [activeringsfoutmelding los op Samsung Knox apparaten](https://go.microsoft.com/fwlink/?linkid=859718) of [Energiebesparing modus uit te schakelen](https://docs.microsoft.com/intune-user-help/power-saving-mode-android). Als geen van deze oplossingen het probleem is opgelost, bieden we een uitleg van hoe [logboeken naar Microsoft verzenden](https://docs.microsoft.com/intune-user-help/send-logs-to-microsoft-android).
  <!-- 1573324, 1573150, 1558616, 1564878 -->      

- **Apparaat setup voortgangsindicator in Android-bedrijfsportal**    
  De bedrijfsportal-app voor Android ziet u een voortgangsindicator voor installatie van apparaat wanneer een gebruiker inschrijving van het apparaat. De indicator bevat nieuwe statussen, beginnen met ' Uw apparaat instellen...', vervolgens 'Registreren van uw apparaat...', vervolgens 'Is voltooid voor het registreren van uw apparaat...' vervolgens 'Instellen... van uw apparaat is voltooid'.  
  <!--1565657-->    

- **Ondersteuning voor verificatie op basis van certificaten op de bedrijfsportal voor iOS**    
  Er is ondersteuning toegevoegd voor verificatie op basis van certificaten (CBA) in de bedrijfsportal-app voor iOS. Gebruikers met CBA hun gebruikersnaam invoeren en tik op de koppeling 'Meld u aan een certificaat met'. CBA wordt al op de bedrijfsportal-apps voor Android en Windows ondersteund. Meer informatie vindt u op de [aanmelden bij de bedrijfsportal-app](https://docs.microsoft.com/intune-user-help/sign-in-to-the-company-portal) pagina.
  <!--1029830-->   

- **Verbeteringen in apparaat setup werkstroom in de bedrijfsportal**     
  We hebben de apparaat-setup-werkstroom in de bedrijfsportal-app voor Android verbeterd. De taal is gebruiksvriendelijker en specifiek voor uw bedrijf. Tevens hebben we waar mogelijk schermen gecombineerd. U ziet deze verbeteringen op het [wat is er nieuw in app UI](https://docs.microsoft.com/intune/whats-new-app-ui#week-of-october-2-2017) pagina.
  <!--1490692-->     

- **Verbeterde richtlijnen met betrekking tot de aanvraag voor toegang tot contacten op Android-apparaten**     
  De bedrijfsportal-app voor Android is vaak vereist voor de eindgebruiker de machtiging contactpersonen accepteren. Als een eindgebruiker deze toegang weigert, zien ze een melding in de app die waarschuwingen om het voor voorwaardelijke toegang te geven. 
  <!--1484985-->     

- **Beveiligd opstarten herstel voor Android**     
  Eindgebruikers met Android-apparaten kunt tikt u op de niet-naleving reden hiervoor in de bedrijfsportal-app. Indien mogelijk, gaan deze actie ze rechtstreeks naar de juiste locatie in de app instellingen om het probleem te verhelpen. 
  <!--1490712-->    

- **Aanvullende pushmeldingen voor eindgebruikers op de bedrijfsportal-app voor Android Oreo**    
  Eindgebruikers zien aanvullende meldingen om aan te geven aan wanneer de bedrijfsportal-app voor Android Oreo achtergrondtaken, zoals het ophalen van beleid van de Intune-service uitvoert. De meldingen verhoogt de transparantie voor eindgebruikers over het uitvoeren van de bedrijfsportal is beheertaken op hun apparaat. Dankzij deze verbetering maakt deel uit van de algemene [optimalisatie van de gebruikersinterface van de Portal bedrijf](https://blogs.technet.microsoft.com/intunesupport/2017/08/21/android-8-0-o-behaviour-changes-and-microsoft-intune) voor de bedrijfsportal-app voor Android Oreo. 
  <!--1475932 -->     

- **Nieuw gedrag voor de bedrijfsportal-app voor Android met werkprofielen**     
  Wanneer u een Android voor Work-apparaat met een werk-profiel hebt ingeschreven, is de bedrijfsportal-app in de work-profiel dat beheertaken op het apparaat uitvoert. 

  Tenzij u een app met MAM-functionaliteit in het persoonlijk profiel, langer de bedrijfsportal-app voor Android niet gebruik. Ter verbetering van de werkervaring profiel verborgen Intune automatisch de persoonlijke app bedrijfsportal na de inschrijving van een geslaagde work-profiel.

  De bedrijfsportal-app voor Android kan worden ingeschakeld op elk gewenst moment in het persoonlijk profiel door te bladeren voor [bedrijfsportal in de Play Store](https://play.google.com/store/apps/details?id=com.microsoft.windowsintune.companyportal) en tik op **inschakelen**.
  <!--1485783-->    

- **Portal voor Windows 8.1 en Windows Phone 8.1 verplaatsen naar de modus voor de bedrijfsportal**    
  Een bericht is toegevoegd aan te kondigen of de bedrijfsportal-apps voor Windows 8.1 en Windows Phone 8.1 zijn verplaatst naar de modus. Zie voor meer informatie [meldingen](#notices).  
  <!--1428681-->    

- **Inschrijving van een niet-ondersteunde Samsung Knox-apparaten blokkeren**   
  De app bedrijfsportal probeert alleen ondersteunde Samsung Knox-apparaten in te schrijven. Om te voorkomen KNOX activeringsfouten waardoor MDM-registratie, apparaatinschrijving alleen uitgevoerd als het apparaat wordt weergegeven in de [lijst met apparaten die zijn gepubliceerd door Samsung](https://www.samsungknox.com/knox-supported-devices/knox-workspace). Samsung apparaten kunnen model getallen die met KNOX ondersteunen en anderen die geen hebben. Knox compatibiliteit met uw wederverkoper apparaat controleren voordat de aankoop en implementatie. U vindt de volledige lijst met gecontroleerde apparaten in de [beleidsinstellingen voor Android en Samsung KNOX Standard](https://docs.microsoft.com/intune-classic/deploy-use/android-policy-settings-in-microsoft-intune#supported-samsung-knox-standard-devices).
  <!-- 1490695 -->     

- **Einde van ondersteuning voor Android 4.3 en lager**     
  Een aankondiging is toegevoegd voor het einde van ondersteuning voor Android 4.3 en lager. Zie voor meer informatie [meldingen](#notices).
  <!--1171126, 1326920 -->     

- **Eindgebruikers informeren over welke gegevens van een apparaat kan worden weergegeven op ingeschreven apparaten**     
  We toevoegen **eigendomstype** naar het scherm Apparaatdetails op alle bedrijfsportal-apps. Deze informatie kan gebruikers meer informatie over privacy rechtstreeks vanuit de [welke gegevens kan uw bedrijf zien?](https://docs.microsoft.com/intune-user-help/what-info-can-your-company-see-when-you-enroll-your-device-in-intune) artikel. Dankzij deze verbetering implementatie in alle bedrijfsportal-apps in de nabije toekomst. We deze functie voor iOS in aangekondigd [September](https://docs.microsoft.com/intune/whats-new#week-of-september-11-2017). 
  <!--1165314-->     



## <a name="september-2017"></a>September 2017

### <a name="new-in-microsoft-intune"></a>Nieuw in Microsoft Intune     

- **Vernieuwen van de actie die zijn toegevoegd aan de bedrijfsportal-app voor Windows 10**    
    De bedrijfsportal-app voor Windows 10 kan gebruikers de gegevens in de app vernieuwen door beide binnenhalen om te vernieuwen, of op desktops, op F5 te drukken.
    <!-- 1132468 -->     

- **Eindgebruikers informeren over welke gegevens van een apparaat worden weergegeven voor iOS**   
    We hebben toegevoegd **eigendomstype** naar het scherm Apparaatdetails op de bedrijfsportal-app voor iOS. Deze informatie kan gebruikers meer informatie over privacy rechtstreeks vanuit de Intune-eindgebruikers-documenten. Ze kunnen ook deze informatie in het scherm over vinden. 
    <!--739894-->    

- **Gemakkelijker te begrijpen formulering voor de bedrijfsportal-app voor Android**   
    Het inschrijvingsproces voor de bedrijfsportal-app voor Android is vereenvoudigd door nieuwe tekst om het gemakkelijker voor eindgebruikers te registreren. Als u aangepaste inschrijving documentatie hebt, bijwerken om de nieuwe schermen weer te geven. U kunt voorbeeldquery afbeeldingen vinden op onze [UI-updates voor Intune-eindgebruikers apps](https://docs.microsoft.com/intune/whats-new-app-ui#week-of-september-11-2017) pagina.
    <!---1396349-->    

- **Windows 10-bedrijfsportal-app toegevoegd aan Windows Information Protection toestaan**    
    De app bedrijfsportal voor Windows 10 is bijgewerkt ter ondersteuning van Windows-beveiliging (OHW). De app kan worden toegevoegd aan het onderhanden werk toestaan. Met deze wijziging heeft de app niet meer worden toegevoegd aan de **uitgezonderd** lijst. 

    Alleen een enkele OHW-configuratie-item kan worden geleverd op een apparaat. Als twee OHW-configuratie-items zijn gericht op hetzelfde apparaat, wordt geen van beide OHW-beleid van toepassing.
    <!-- 677129 -->    

- **Einde van de kennisgeving van ondersteuning toegevoegd voor iOS 8.0**    
    Een bericht is toegevoegd voor einde van ondersteuning voor iOS 8.0. Zie voor meer informatie [meldingen](#notices).



## <a name="august-2017"></a>Augustus 2017

### <a name="new-in-microsoft-intune"></a>Nieuw in Microsoft Intune     

- **Nieuwe aangemelde ervaring voor Android-bedrijfsportal gebruikers- en beveiligingsbeleid van App-gebruikers**    
  Eindgebruikers kunnen nu apps bladeren, apparaten beheren en weergeven contact opnemen met IT gegevens door middel van de Android-bedrijfsportal-app zonder hun Android-apparaten inschrijven. Bovendien, als een eindgebruiker al gebruikmaakt van een app door Intune-App worden beveiligd, en de Android-bedrijfsportal start, ontvangt de eindgebruiker geen meer gevraagd het apparaat te registreren.
  <!-- 621669 -->



## <a name="july-2017"></a>Juli 2017

### <a name="new-in-microsoft-intune"></a>Nieuw in Microsoft Intune

- **Einde van aankondigingen van ondersteuning toegevoegd voor Android en Windows Phone**    
    Nieuwe meldingen zijn toegevoegd voor het einde van ondersteuning voor Android en Windows Phone-versies. Zie voor meer informatie [meldingen](#notices).


### <a name="new-in-configuration-manager-current-branch"></a>Nieuw in Configuration Manager (huidige vertakking)

De volgende functies eerder beschikbaar waren in Configuration Manager Technical Preview-versies. Deze functies zijn nu beschikbaar in hybride implementaties met Intune en Configuration Manager (huidige vertakking) versie 1706.

- [Ondersteuning voor certificeringsinstanties Entrust belasten](/sccm/core/get-started/capabilities-in-technical-preview-1706#support-for-entrust-certification-authorities)
- [Nieuwe beleidsinstellingen voor mobile application management](/sccm/core/plan-design/changes/whats-new-in-version-1706#new-mobile-application-management-policy-settings)
- [Updates voor Android for Work-configuratie voor delen](/sccm/core/plan-design/changes/whats-new-in-version-1706#updates-to-android-for-work-sharing-configuration)
- [Nieuwe beleidsregels voor naleving van apparaat](/sccm/core/plan-design/changes/whats-new-in-version-1706#new-device-compliance-policy-rules)
- [Nieuwe configuratie-instellingen voor Windows 10-apparaten die niet worden beheerd met Configuration Manager-client](/sccm/core/plan-design/changes/whats-new-in-version-1706#new-configuration-settings-for-windows-10-devices-that-are-not-managed-with-the-configuration-manager-client)
- [Cisco (IPsec) ondersteuning voor Mac OS VPN-profielen](/sccm/core/get-started/capabilities-in-technical-preview-1706#cisco-ipsec-support-for-macos-vpn-profiles)
- [Beperkingen voor android en iOS-inschrijving](/sccm/core/plan-design/changes/whats-new-in-version-1706#android-and-ios-enrollment-restrictions) 



## <a name="june-2017"></a>Juni 2017

### <a name="new-in-microsoft-intune"></a>Nieuw in Microsoft Intune

- **Wijzigen van uw MDM-instantie**    
  U kunt vanaf Configuration Manager versie 1610 kan uw MDM-instantie wijzigen zonder contact opnemen met Microsoft Support. U ook geen registratie ongedaan maken en registreren van uw bestaande beheerde apparaten. Zie voor meer informatie [wijzigen van uw MDM-instantie](/sccm/mdm/deploy-use/change-mdm-authority).

- **Beheerde browser en app-proxy-integratie**    
  De Intune Managed Browser kunnen nu geïntegreerd met de service Azure AD-toepassingsproxy gebruikers toegang biedt tot interne websites, zelfs wanneer ze extern werken. Gebruikers van de browser Voer de URL van de site zoals ze normaal en de Managed Browser de aanvraag via de gateway application proxy web stuurt. Zie voor meer informatie [toegang tot het Internet beheren met beheerde-browserbeleid](https://docs.microsoft.com/intune/app-configuration-managed-browser).

- **Bedrijfsportal-app voor Android is nu een nieuwe ervaring voor de eindgebruiker voor App-beveiligingsbeleid**  
  Op basis van feedback van klanten, hebben we de bedrijfsportal-app voor Android om weer te geven gewijzigd een **toegang bedrijf inhoud** knop. De bedoeling is om te voorkomen dat eindgebruikers onnodig gaan via het registratieproces wanneer ze alleen toegang tot apps die ondersteuning bieden voor App-beleid voor beveiliging, een functie van Intune-beheer van mobiele toepassingen nodig. U kunt deze wijzigingen kan zien op de [wat is er nieuw in app UI](https://docs.microsoft.com/intune/whats-new-app-ui) pagina.

- **Nieuwe menu Actie eenvoudig bedrijfsportal verwijderen**  
  Op basis van feedback van gebruikers, is de bedrijfsportal-app voor Android een nieuwe menu Actie voor het initiëren van het verwijderen van de bedrijfsportal van uw apparaat toegevoegd. Deze actie verwijdert het apparaat uit Intune-beheer, zodat de app kan worden verwijderd van het apparaat door de gebruiker. U kunt deze wijzigingen kan zien op de [wat is er nieuw in gebruikersinterface-app](https://docs.microsoft.com/intune/whats-new-app-ui) pagina en in de [documentatie voor Android-eindgebruikers](https://docs.microsoft.com/intune-user-help/unenroll-your-device-from-intune-android).

- **Verbeteringen in de app worden gesynchroniseerd met Windows 10 auteurs Update**  
  De bedrijfsportal-app voor Windows 10 nu start automatisch een synchronisatie voor aanvragen van de app installeren voor apparaten met Windows 10 auteurs Update (versie 1703). Hierdoor wordt de uitgifte van de app wordt geïnstalleerd tijdens de status 'In behandeling Sync' afslaan. Bovendien kunnen gebruikers zich aan om een synchronisatie uit vanuit de app handmatig te starten. U kunt deze wijzigingen kan zien op de [wat is er nieuw in app UI](https://docs.microsoft.com/intune/whats-new-app-ui) pagina.

- **Nieuwe begeleide ervaring voor Windows 10-bedrijfsportal**  
  De bedrijfsportal-app voor Windows 10 bevat een begeleide ervaring van Intune walkthrough voor apparaten die nog niet hebt geïdentificeerd of zijn ingeschreven. De nieuwe ervaring bevat stapsgewijze instructies die begeleid bij het registreren in Azure Active Directory (vereist voor voorwaardelijke toegang functies) en de MDM-registratie (vereist voor apparaatfuncties management). De begeleide ervaring is toegankelijk vanaf de startpagina van de bedrijfsportal. Als gebruikers geen registratie en inschrijving hebt voltooid, kunnen ze doorgaan met de app gebruiken, maar heeft beperkte functionaliteit optreden.

  Deze update is alleen zichtbaar op apparaten met Windows 10 Verjaardag Update (build 1607) of hoger. U kunt deze wijzigingen kan zien op de [wat is er nieuw in app UI](https://docs.microsoft.com/intune/whats-new-app-ui) pagina.

- **Verbeteringen in de app-tegels in de bedrijfsportal-app voor iOS**  
  Het ontwerp van de app-tegels op de startpagina in overeenstemming met de huisstijl kleur die u voor de bedrijfsportal instelt is bijgewerkt. Zie voor meer informatie [wat is er nieuw in app UI](https://docs.microsoft.com/intune/whats-new-app-ui).

- **Account objectkiezer nu beschikbaar voor de bedrijfsportal-app voor iOS**  
  Als gebruikers van iOS-apparaten hun werk gebruiken- of schoolaccount aanmelden bij andere Microsoft-apps, zien ze mogelijk onze nieuwe account kiezen wanneer ze zich in de bedrijfsportal. Zie voor meer informatie [wat is er nieuw in app UI](https://docs.microsoft.com/intune/whats-new-app-ui).

### <a name="new-in-configuration-manager-technical-preview-1706"></a>Nieuw in Configuration Manager Technical Preview 1706

- **Nieuwe configuratie-item-instellingen van Windows**      
  Nieuwe Windows-configuratie-items zijn beschikbaar voor de instelling wachtwoord, apparaat, Store en Microsoft Edge categorieën. Zie voor meer informatie [nieuwe Windows-configuratie-iteminstellingen](/sccm/core/get-started/capabilities-in-technical-preview-1706#new-windows-configuration-item-settings).
  <!-- 1354715 -->

- **Nieuwe beleidsregels voor naleving van apparaat**   
  U kunt nu de nieuwe opties voor nalevingsbeleid die eerder alleen beschikbaar in zelfstandige versie van Intune waren configureren. Zie voor meer informatie [apparaat naleving beleid verbeteringen](/sccm/core/get-started/capabilities-in-technical-preview-1706#new-device-compliance-policy-rules).

- **Beperkingen voor android en iOS-inschrijving**       
  Beheerders kunnen nu opgeven dat gebruikers persoonlijke Android- of iOS-apparaten in hun omgeving hybride kunnen niet registreren. Deze actie kunt u limiet ingeschreven apparaten predeclared, bedrijfseigen apparaten of alleen met Device Enrollment Program ingeschreven iOS-apparaten. Zie voor meer informatie [Android en iOS-inschrijving beperkingen](/sccm/core/get-started/capabilities-in-technical-preview-1706#android-and-ios-enrollment-restrictions).
  <!-- 1290826 -->

- **Ondersteuning voor Entrust certificeringsinstanties**      
  Configuration Manager ondersteunt nu Entrust certificeringsinstanties. Deze ondersteuning kunnen de levering van PFX-certificaat voor apparaten die zijn ingeschreven bij Microsoft Intune.    
  <!-- 1350740 -->

  U kunt Entrust configureren als de certificeringsinstantie (CA) bij het toevoegen van een rol Certificaatregistratiepunt in Configuration Manager. Wanneer u een nieuw certificaatprofiel die PFX-certificaten uitgeeft toevoegt, kunt u een Microsoft- of Entrust certificeringsinstantie selecteren.

  **Bekende probleem**: PFX-certificaten worden niet in de technical preview 1706 verleend voor Microsoft-certificeringsinstanties. Dit probleem heeft geen invloed op geïmporteerde PFX-certificaten of SCEP-profielen.

- **Cisco (IPsec) ondersteuning voor Mac OS VPN-profielen**      
  U kunt een Mac OS VPN-profiel maken met Cisco (IPsec) als het verbindingstype. Zie voor meer informatie [VPN-profielen maken](/sccm/mdm/deploy-use/create-vpn-profiles#create-vpn-profiles).
  <!-- 1321367 -->


## <a name="april-2017"></a>April 2017

### <a name="new-in-microsoft-intune"></a>Nieuw in Microsoft Intune

- **MyApps beschikbaar voor Managed Browser**  
  Microsoft MyApps hebben nu een betere ondersteuning binnen de Managed Browser. Beheerde Browsergebruikers die niet zijn in de doelgroep voor het beheer zijn gebracht rechtstreeks aan de service MyApps, waar ze toegang krijgen tot hun admin ingericht SaaS-apps. Gebruikers die zijn bedoeld voor Intune-beheer blijven toegang tot MyApps van de ingebouwde Managed Browser bladwijzer.

- **Nieuwe pictogrammen voor de Managed Browser en de bedrijfsportal**  
  De Managed Browser ontvangt bijgewerkte pictogrammen voor de Android- en iOS-versies van de app. Het pictogram Nieuw bevat de bijgewerkte Intune badge om het te maken met andere apps consistente in Enterprise Mobility + Security (EM + S). U kunt het nieuwe pictogram voor de Managed Browser zien op de [wat is er nieuw in Intune op de pagina app UI](https://docs.microsoft.com/intune/whats-new-app-ui).

  Bijgewerkte pictogrammen voor de Android, iOS en Windows-versies van de app voor het verbeteren van de consistentie met andere apps in EM + S is ook ontvangen van de bedrijfsportal. Deze pictogrammen worden geleidelijk verschillende platforms van April laat kan vrijgegeven.

- **Aanmelden voortgangsindicator in Android-bedrijfsportal**  
  Een update voor de Android-bedrijfsportal-app toont een voortgangsindicator aanmelden wanneer de gebruiker wordt gestart of de app hervat. De indicator doorloopt nieuwe statussen, beginnen met 'Verbinden...' vervolgens 'Ondertekening in...' en 'Controleren voor de beveiligingsvereisten...' voorafgaand aan zodat de gebruiker toegang tot de app. U kunt de nieuwe schermen voor de bedrijfsportal-app voor Android zien op de [wat is er nieuw in Intune op de pagina app UI](https://docs.microsoft.com/intune/whats-new-app-ui).

- **Toegang tot SharePoint Online blokkeren apps**  
  U kunt een beleid voor voorwaardelijke toegang op basis van een app voor het blokkeren van apps, waarvoor geen app protection-beleid toegepast naar hen nu toegang tot maken [SharePoint Online](https://docs.microsoft.com/intune-classic/deploy-use/mam-ca-for-sharepoint-online). In het scenario voor voorwaardelijke toegang op basis van apps, kunt u de apps die u wilt toegang hebben tot SharePoint Online met Azure portal.

### <a name="new-in-configuration-manager-technical-preview-1704"></a>Nieuw in Configuration Manager Technical Preview 1704

- **Android-apps met app-configuratiebeleid configureren**  
  Wanneer een gebruiker een app op Android voor werk apparaten uitvoert, app-configuratiebeleid in Configuration Manager gebruiken voor het distribueren van vooraf geconfigureerde instellingen. Configuratiebeleid voor android-app zijn alleen beschikbaar voor apparaten met Android for Work. Deze beleidsregels toepassen op goedgekeurde apps uit de Play voor werk store. Zie voor meer informatie [configureren Android-apps met configuratiebeleid voor apps](/sccm/core/get-started/capabilities-in-technical-preview-1704#configure-android-apps-with-app-configuration-policies).



## <a name="march-2017"></a>Maart 2017

### <a name="new-in-microsoft-intune"></a>Nieuw in Microsoft Intune

- **Nieuwe gebruikerservaring op voor de bedrijfsportal-app voor Android**  
  De bedrijfsportal-app voor Android is een meer moderne vormgeving op de gebruikersinterface. De belangrijke updates zijn:

  - Kleuren: Bedrijf Portal tabblad headers zijn gekleurd in huisstijl IT gedefinieerd.
  - Apps: In de **Apps** tabblad de **aanbevolen Apps** en **alle Apps** knoppen worden bijgewerkt.
  - Zoeken: In de **Apps** tabblad de **zoeken** een zwevende actie knop.
  - Navigeren Apps: **Alle Apps** weergave toont tabbladen weergeven van **aanbevolen**, **alle**, en **categorieën** voor navigatie te vereenvoudigen.
  - Ondersteuning: **Mijn apparaten** en **contact opnemen met IT** tabbladen zijn bijgewerkt voor een betere leesbaarheid.

  Zie voor meer informatie over deze wijzigingen [UI-updates voor Intune-eindgebruikers apps](https://docs.microsoft.com/intune/whats-new-app-ui).

- **Script voor Windows 10-bedrijfsportal te ondertekenen**  
  Als u downloaden en de bedrijfsportal voor Windows 10-Apps sideloaden wilt, kunt u nu een script gebruiken om te vereenvoudigen en het proces voor het ondertekenen van Apps voor uw organisatie te stroomlijnen. Zie voor het downloaden van het script en de instructies voor het gebruik ervan [Microsoft Intune-ondertekening Script voor Windows 10 bedrijfsportal](https://aka.ms/win10cpscript) op TechNet-galerie. Zie voor meer informatie over deze aankondiging [bijwerken van uw Windows 10-bedrijfsportal-app](https://blogs.technet.microsoft.com/intunesupport/2017/03/13/updating-your-windows-10-company-portal-app/) op het Intune-teamblog voor ondersteuning.

- **Verbeterde ondersteuning voor Android-gebruikers op basis van China**  
  Wegens het ontbreken van de Google Play Store in China, moeten Android-apparaten ophalen met apps Chinees marktplaatsen. Deze werkstroom biedt ondersteuning voor de bedrijfsportal. Android-gebruikers in China om de bedrijfsportal-App en Outlook-apps downloaden van lokale app stores wordt hij omgeleid. Dit gedrag verbetert de ervaring van de gebruiker wanneer het beleid voor voorwaardelijke toegang ingeschakeld, zowel voor beheer van mobiele apparaten en voor Mobile Application Management. De bedrijfsportal-App en Outlook-apps voor Android zijn beschikbaar op de volgende Chinees app worden opgeslagen:

  - [Baidu](https://go.microsoft.com/fwlink/?linkid=836946)
  - [Xiaomi](https://go.microsoft.com/fwlink/?linkid=836947)
  - [Tencent](https://go.microsoft.com/fwlink/?linkid=836949)
  - [Huawei](https://go.microsoft.com/fwlink/?linkid=836948)
  - [Wandoujia](https://go.microsoft.com/fwlink/?linkid=836950)

- **Zorg ervoor dat uw bedrijfsportal-apps zijn bijgewerkt**  
  December 2016, wij een update uitgebracht die afdwingen voor multi-factor authentication (MFA) ingeschakeld op een groep gebruikers wanneer ze een iOS-, Android, Windows 8.1 + of Windows Phone 8.1 + apparaat inschrijven. Deze functie kan niet werken zonder bepaalde basislijnversies van de bedrijfsportal-app voor Android (v5.0.3419.0 +) en iOS (v2.1.17 +).

  Mogelijkheden van Intune verbeteren continu. Veel verbeteringen hebben gecoördineerd updates voor de bedrijfsportal apps op alle ondersteunde platforms. We adviseren u de nieuwste versies van de bedrijfsportal-apps op apparaten geïnstalleerd op. Deze procedure maakt gebruik van verbeteringen in Intune en voor de beste gebruikerservaring.

  >[!Tip]
  > Laat uw gebruikers hun apparaten automatisch bijwerken van de juiste appstore-apps in te stellen. Als u hebt de Android-bedrijfsportal-app beschikbaar gesteld op een netwerkshare bevindt, kunt u downloaden met de meest recente versie van [Microsoft Download Center](https://www.microsoft.com/download/details.aspx?id=49140).

- **Microsoft-Teams is nu ingeschakeld voor MAM op iOS en Android**  
  De Microsoft-Teams apps voor iOS en Android zijn nu beschikbaar met de mogelijkheden van Intune mobile Application management (MAM). Zorgen dat uw teams vrijelijk werken op apparaten, terwijl u ervoor zorgt dat conversaties en bedrijfsgegevens worden beschermd. Zie voor meer informatie [de aankondiging van de Microsoft-Teams](https://blogs.technet.microsoft.com/enterprisemobility/2017/03/14/microsoft-teams-is-now-generally-available-and-mam-enabled-on-ios-and-android/) op de Enterprise Mobility and Security-blog.

### <a name="new-in-configuration-manager-technical-preview-1703"></a>Nieuw in Configuration Manager Technical Preview 1703

- **Extra ondersteuning voor Apple Volume Purchase Program-scenario 's**  
   Vanaf Technical Preview 1703, hebt u nu ondersteuning voor het volgende Volume Purchase Program (VPP)-scenario's:

   - Apparaat licenties - Apps die ondersteuning voor de apparaat-licentieverlening en geïmplementeerd in apparaatverzamelingen nu slechts één licentie per apparaat nodig. Voorheen moest u een licentie voor elke gebruiker op een apparaat gebruiken. Zie voor meer informatie [iOS volume-aankoopprogramma gekochte apps implementeren op apparaatverzamelingen](/sccm/core/get-started/capabilities-in-technical-preview-1703#deploy-volume-purchased-ios-apps-to-device-collections).
   - Gebruik van meerdere VPP-tokens in een enkel hybride-tenant met beide tokens voor het beheer van VPP-apps.
   - Gebruik van VPP-tokens education met de mogelijkheid om onderscheid maken tussen bedrijven en education tokens.

### <a name="new-in-configuration-manager-current-branch"></a>Nieuw in Configuration Manager (huidige vertakking)

De volgende functies eerder beschikbaar waren in Configuration Manager Technical Preview-versies. Deze functies zijn nu beschikbaar in hybride implementaties met Intune en Configuration Manager (huidige vertakking) versie 1702.

- [Android voor Work-ondersteuning](/sccm/core/plan-design/changes/whats-new-in-version-1702##android-for-work-support)
- [Instellingen voor naleving van niet-compatibele Apps](/sccm/core/plan-design/changes/whats-new-in-version-1702#conditional-access-device-compliance-policy-improvements)
- [PFX-certificaat maken en distributie en het S/MIME-ondersteuning](/sccm/core/plan-design/changes/whats-new-in-version-1702#improvements-to-certificate-profiles)
- [Android en iOS-versies worden niet meer targetable in wizards voor hybride MDM maken](/sccm/core/plan-design/changes/whats-new-in-version-1702#android-and-ios-versions-are-no-longer-targetable-in-creation-wizards-for-hybrid-mdm)

De volgende aanvullende hybridefuncties zijn ook opgenomen in versie 1702 van Configuration Manager (huidige vertakking):

- **Verbeterde ondersteuning voor Apple Volume Purchase Program (VPP)**  
  - U kunt nu gelicentieerde apps implementeren op apparaten, evenals gebruikers. Afhankelijk van de mogelijkheid apps ter ondersteuning van apparaat-licentieverlening, wordt een juiste licentie aangevraagd bij het implementeren, als volgt:

    | Versie van Configuration Manager | App ondersteunt apparaat licentieverlening? | Implementatietype van de verzameling | De geclaimde licentie |
    |-|-|-|-|
    |Ouder dan 1702|Ja|Gebruiker|Gebruikerslicentie|
    |Ouder dan 1702|Nee|Gebruiker|Gebruikerslicentie|
    |Ouder dan 1702|Ja|Apparaat|Gebruikerslicentie|
    |Ouder dan 1702|Nee|Apparaat|Gebruikerslicentie|
    |1702 en hoger|Ja|Gebruiker|Gebruikerslicentie|
    |1702 en hoger|Nee|Gebruiker|Gebruikerslicentie|
    |1702 en hoger|Ja|Apparaat|Apparaatlicentie|
    |1702 en hoger|Nee|Apparaat|Gebruikerslicentie|

  - U kunt nu ook implementeren en bijhouden van apps die u hebt aangeschaft via de iOS Volume Purchase Program voor onderwijs.

  - U kunt meerdere Apple volume purchase program-tokens nu koppelen met Configuration Manager.

  Zie voor meer informatie over volume-purchased iOS-apps, [volume-purchased iOS-apps beheren](/sccm/mdm/deploy-use/manage-volume-purchased-ios-apps).

- **Ondersteuning voor line-of-business-apps in Microsoft Store voor bedrijven**  
  U kunt aangepaste LOB-apps uit de Microsoft Store voor bedrijven nu synchroniseren.

- **Nieuwe mobiele Threat verdediging controlehulpprogramma 's**  
    U hebt nu een nieuwe manieren om de compatibiliteitsstatus met uw serviceprovider Mobile Threat verdediging te controleren.

    Zie voor meer informatie [Mobile Threat verdediging naleving controleren](/sccm/mdm/deploy-use/monitor-mobile-threat-defense-compliance).



## <a name="notices"></a>Aankondigingen

### <a name="company-portal-for-windows-81-and-windows-phone-81-moving-to-sustaining-mode"></a>Portal voor Windows 8.1 en Windows Phone 8.1 verplaatsen naar de modus voor de bedrijfsportal 
<!--1428681-->
*6 oktober 2017*   
 
Vanaf oktober 2017 kan verplaatsen de bedrijfsportal-apps voor Windows 8.1 en Windows Phone 8.1 naar de modus. Deze modus betekent dat de apps en de bestaande scenario's, zoals de inschrijving en naleving, blijven worden ondersteund voor deze platforms. Deze apps blijven worden gedownload via bestaande release kanalen, zoals de Microsoft Store. 

Eenmaal in de modus, deze apps ontvangt alleen kritieke beveiligingsupdates. Er is geen aanvullende updates of onderdelen worden uitgebracht voor deze apps. Nieuwe functies, wordt u aangeraden apparaten bij te werken naar Windows 10 of Windows 10 Mobile. 

### <a name="end-of-support-for-ios-80"></a>Einde van ondersteuning voor iOS 8.0 
<!---1164477--->
Beheerde apps en de bedrijfsportal-app voor iOS vereisen iOS 9.0 en hoger voor toegang tot bedrijfsbronnen. Apparaten die niet zijn bijgewerkt voor September zijn niet langer toegang tot de bedrijfsportal of deze apps. 

### <a name="platform-support-reminder-windows-phone-81-mainstream-support-ended-july-11-2017"></a>Herinnering voor platform-ondersteuning: Algemene ondersteuning voor Windows Phone 8.1 11 juli 2017 beëindigd
<!-- 1327781 -->
*11 juli 2017*

De Windows Phone 8.1-platform is geëindigd algemeen worden ondersteund. Ondersteuning voor Windows 8.1-PC wordt niet beïnvloed.

Er zijn geen directe gevolgen op een Windows Phone 8.1-apparaat dat wordt beheerd door de Intune-service, inclusief apparaten die zijn ingeschreven in een hybride MDM Apparaten die zijn ingeschreven, blijven werken. Alle beleidsregels, configuraties en apps blijven werken zoals verwacht. Let op: Er zijn geen verbeteringen die zijn bedoeld voor het Windows Phone 8.1-platform in de Intune-service en de Windows Phone 8.1-bedrijfsportal-app.

Het is raadzaam om in aanmerking komende Windows Phone 8.1-apparaten upgraden naar Windows 10 Mobile op zo snel mogelijk.  

### <a name="end-of-support-for-android-43-and-lower"></a>Einde van ondersteuning voor Android 4.3 en lager
<!---1171127--->
*6 juli 2017*

Beheerde apps en de bedrijfsportal-app voor Android vereist Android 4.4 en hoger voor toegang tot bedrijfsbronnen. Apparaten die niet zijn bijgewerkt voor het begin van oktober zijn niet langer toegang tot de bedrijfsportal of deze apps. December worden alle geregistreerde apparaten buiten gebruik gesteld in December, wat leidt tot verlies van toegang tot bedrijfsbronnen force. Als u van beveiligingsbeleid app zonder MDM gebruikmaakt, apps ontvangt geen updates en de kwaliteit van hun ervaring instelt, vermindert u gedurende een bepaalde periode.



## <a name="see-also"></a>Zie ook

- [Uit het verleden hybride MDM-functies en meldingen](whats-new-hybrid-archive.md)
- [Wat is er nieuw voor MDM in System Center 2012 Configuration Manager](https://technet.microsoft.com/library/mt445560.aspx)
