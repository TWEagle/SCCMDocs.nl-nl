---
title: Wat is nieuw in hybride MDM met Configuration Manager | Microsoft-documenten
description: Meer informatie over de nieuwe functies voor mobiele apparaten beschikbaar voor hybride implementaties met Configuration Manager en Intune.
ms.custom: na
ms.date: 04/21/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-hybrid
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 7b127cee-61f1-4681-9760-caebed36ddf5
caps.latest.revision: 40
author: Mtillman
ms.author: mtillman
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: ae008c91a7387ba76f2bfac13f8feb489a0cc558
ms.openlocfilehash: 0af5ae68353fcf1db846e2e27f3391fe87dcfc42
ms.contentlocale: nl-nl
ms.lasthandoff: 05/17/2017

---
# <a name="whats-new-in-hybrid-mobile-device-management-with-system-center-configuration-manager-and-microsoft-intune"></a>Wat is nieuw in hybride mobiel Apparaatbeheer met System Center Configuration Manager en Microsoft Intune

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*

Dit artikel biedt gedetailleerde informatie over de nieuwe mobiele apparaten management (MDM) die beschikbaar zijn voor hybride implementaties met System Center Configuration Manager en Microsoft Intune.  

##  <a name="compatibility-with-configuration-manager-versions"></a>Compatibiliteit met versies van Configuration Manager  

 Elke sectie van dit artikel geeft een overzicht van hybride functies onder 3 verschillende categorieën. Gebruik de volgende richtlijnen om te bepalen van compatibiliteit met eerdere versies van de functies in elke categorie met verschillende versies van Configuration Manager:  

|Functie categorieën|Beschrijving|
|-|-|
|**Nieuw in Microsoft Intune** | In het algemeen moeten alle functies die worden vermeld onder deze categorie samen met alle versies van de Configuration Manager met inbegrip van System Center 2012 R2 Configuration Manager-versies, aangezien deze functies alleen de Intune-service vereisen en geen aanvullende functionaliteit in Configuration Manager vereisen.|
|**Nieuw in Configuration Manager Technical Preview**| Alle functies die worden vermeld onder deze categorie werkt alleen met de opgegeven Technical Preview-versie. Als u wilt deze functies uit te proberen, moet u de opgegeven in de functiebeschrijving van de Technical Preview-versie installeren. Zie voor meer informatie [Technical Preview voor System Center Configuration Manager](../../core/get-started/technical-preview.md).|
|**Nieuw in Configuration Manager (huidige vertakking)**| Alle functies die worden vermeld onder deze categorie werken alleen met de opgegeven versie van Configuration Manager (huidige vertakking), zoals versie 1511 of 1602. Als u een oudere versie van Configuration Manager gebruikt voor uw implementatie van hybride, moet u een upgrade uitvoeren naar de Configuration Manager (huidige vertakking) versie opgegeven in de functiebeschrijving van de. Zie voor meer informatie [upgraden naar System Center Configuration Manager](../../core/servers/deploy/install/upgrade-to-configuration-manager.md).|

## <a name="april-2017"></a>April 2017

### <a name="new-in-microsoft-intune"></a>Nieuw in Microsoft Intune

- **MyApps beschikbaar voor Managed Browser**

  Microsoft MyApps beschikt nu over betere ondersteuning binnen de Managed Browser. Beheerde Browsergebruikers die niet zijn bedoeld voor het beheer van wordt gebracht rechtstreeks met de service MyApps, waar ze toegang krijgen tot hun admin ingericht SaaS-apps. Gebruikers die zich in de doelgroep voor het beheer van Intune blijft MyApps van de ingebouwde Managed Browser bladwijzer toegang moeten hebben.

- **Nieuwe pictogrammen voor de Managed Browser en de bedrijfsportal.**

  De Managed Browser ontvangt bijgewerkte pictogrammen voor het Android- en iOS-versies van de app. Het pictogram Nieuw bevat de bijgewerkte Intune logo zodat dit meer consistent met andere apps in de Enterprise Mobility + beveiliging (EM + S). U kunt het nieuwe pictogram zien voor de Managed Browser op de [wat is nieuw in Intune app UI pagina](/intune/whats-new/whats-new-in-intune-app-ui.md).

  De bedrijfsportal ontvangt ook bijgewerkte pictogrammen voor Android, iOS en Windows-versies van de app voor het verbeteren van de consistentie met andere apps in EM + S. Deze pictogrammen worden geleidelijk verschillende platforms van April eind mei uitgebracht.

- **Aanmelden voortgangsindicator in Android-bedrijfsportal.**

  Een update van het Android-bedrijfsportal-app bevat verschijnt een voortgangsbalk aanmelden als de gebruiker wordt gestart of de app hervat. De indicator wordt door de nieuwe status, te beginnen met 'Verbinden...', 'Handtekening bij in...' vervolgens de, "Controleren voor de beveiligingsvereisten..." voorafgaand aan zodat de gebruiker toegang tot de app. U kunt de nieuwe schermen voor de bedrijfsportal-app voor Android zien op de [wat is nieuw in Intune app UI pagina](/intune/whats-new/whats-new-in-intune-app-ui.md).

- **Apps toegang krijgen tot SharePoint Online blokkeren**

  U kunt een beleid voor voorwaardelijke toegang op basis van een app voor het blokkeren van apps, waarvoor geen app beveiligingsbeleidsregels toegepast naar hen nu geen toegang krijgen tot maken [SharePoint Online](/InTune/deploy-use/mam-ca-for-sharepoint-online). In het scenario voor voorwaardelijke toegang op basis van apps, kunt u de apps die u wilt hebben toegang tot SharePoint Online met behulp van de Azure-portal.

### <a name="new-in-configuration-manager-technical-preview-1704"></a>Nieuw in Configuration Manager technische Preview 1704

- **Android-apps configureren met app-configuratiebeleid**

  U kunt app-configuratiebeleid in System Center Configuration Manager (Configuration Manager) vooraf geconfigureerde instellingen distribueren wanneer een gebruiker een app uitvoert op Android voor werk apparaten. Configuratiebeleid voor android-app zijn alleen beschikbaar voor apparaten met Android for Work en goedgekeurde apps van de Play voor werk store toepassen. Zie voor meer informatie over het uitproberen van deze functie [configureren Android-apps met app-configuratiebeleid](/sccm/core/get-started/capabilities-in-technical-preview-1704#configure-android-apps-with-app-configuration-policies).

## <a name="march-2017"></a>2017 maart

### <a name="new-in-microsoft-intune"></a>Nieuw in Microsoft Intune

- **Nieuwe gebruikerservaring op voor de bedrijfsportal-app voor Android**

  De bedrijfsportal-app voor Android is een moderne uiterlijk aan de gebruikersinterface. Belangrijke updates zijn:

  - Kleuren: Bedrijf Portal tabblad headers zijn gekleurd in het branding-IT gedefinieerd.
  - Apps: In de **Apps** tabblad, het **aanbevolen Apps** en **alle Apps** knoppen worden bijgewerkt.
  - Zoeken: In de **Apps** tabblad, het **zoeken** een zwevende knop in te grijpen.
  - Navigeren Apps: **Alle Apps** weergave toont tabbladen weergeven van **speciale**, **alle**, en **categorieën** voor navigatie te vereenvoudigen.
  - Ondersteuning voor: **Mijn apparaten** en **contact opnemen met IT** tabbladen voor een betere leesbaarheid worden bijgewerkt.

  Zie voor meer informatie over deze wijzigingen [UI-updates voor Intune eindgebruiker apps](/intune/whats-new/whats-new-in-intune-app-ui).

- **Script ondertekenen voor Windows 10 bedrijfsportal**

  Als u downloaden en de Windows-10-bedrijfsportal-app sideloaden wilt, kunt u nu een script gebruiken om te vereenvoudigen en stroomlijnen apps te ondertekenen voor uw organisatie.  U kunt downloaden van het script en de instructies voor het gebruik ervan [Microsoft Intune ondertekening Script voor Windows 10 bedrijfsportal](https://aka.ms/win10cpscript) op TechNet-galerie. Zie voor meer informatie over deze aankondiging [bijwerken van uw app bedrijfsportal voor Windows 10](https://blogs.technet.microsoft.com/intunesupport/2017/03/13/updating-your-windows-10-company-portal-app/) op de Support-teamblog van Intune.

- **Verbeterde ondersteuning voor Android gebruikers in China gebaseerd**

  Omdat deze de Google Play Store in China, moeten de Android-apparaten apps verkrijgen van Chinese marktplaatsen. De bedrijfsportal ondersteunt deze werkstroom door het omleiden van Android gebruikers in China om te downloaden van de bedrijfsportal-App en Outlook apps van lokale app stores. Dit verbetert de gebruikerservaring wanneer beleidsregels voor voorwaardelijke toegang zijn ingeschakeld voor het beheer van mobiele apparaten en voor Mobile Application Management. De bedrijfsportal-App en Outlook apps voor Android, zijn beschikbaar op de volgende Chinees app stores:

  - [Baidu](https://go.microsoft.com/fwlink/?linkid=836946)
  - [Xiaomi](https://go.microsoft.com/fwlink/?linkid=836947)
  - [Tencent](https://go.microsoft.com/fwlink/?linkid=836949)
  - [Huawei](https://go.microsoft.com/fwlink/?linkid=836948)
  - [Wandoujia](https://go.microsoft.com/fwlink/?linkid=836950)

- **Zorg ervoor dat de bedrijfsportal-apps zijn bijgewerkt**

  In December 2016 we een update uitgebracht die bekrachtiging van multi-factor authentication (MFA) ingeschakeld op een groep gebruikers wanneer ze een iOS, Android, Windows 8.1 + of Windows Phone 8.1 + apparaat inschrijven. Deze functie kan niet werken zonder bepaalde basislijn versies van de bedrijfsportal-app voor Android (v5.0.3419.0 +) en iOS (v2.1.17 +).

  Beheermogelijkheden van Intune continu verbeteren en tal van verbeteringen ten hebben gecoördineerd updates voor de bedrijfsportal apps op alle ondersteunde platforms. Als gevolg hiervan wordt aangeraden dat u de nieuwste versies van de bedrijfsportal-apps op is geïnstalleerd op apparaten om te profiteren van verbeteringen in Intune en voor de beste gebruikerservaring.

  >[!Tip]
  > Hebben uw gebruikers hun apparaten automatisch te laten bijwerken de juiste appstore-apps in te stellen. Als u de Android-bedrijfsportal-app beschikbaar op een netwerkshare bevindt gemaakt hebt, kunt u downloaden met de meest recente versie van [Microsoft Download Center](https://www.microsoft.com/download/details.aspx?id=49140).

- **Microsoft-Teams is nu ingeschakeld voor MAM op iOS en Android**

  De Microsoft-Teams apps voor iOS en Android zijn nu beschikbaar met de mogelijkheden van Intune mobile app management (MAM), zodat u mogelijkheden aan uw teams bieden kunt werken vrijelijk verschillende apparaten, terwijl dat conversaties en bedrijfsgegevens op elke beurt is beveiligd. Zie voor meer informatie [de Microsoft-Teams aankondiging](https://blogs.technet.microsoft.com/enterprisemobility/2017/03/14/microsoft-teams-is-now-generally-available-and-mam-enabled-on-ios-and-android/) op het blog van de Enterprise Mobility en beveiliging.

### <a name="new-in-configuration-manager-technical-preview-1703"></a>Nieuw in Configuration Manager technische Preview 1703

- **Extra ondersteuning voor Apple Volume Purchase Program scenario 's**

   Technische Preview 1703 begin, hebt u nu ondersteuning voor de volgende Volume aankoop programma VPP ()-scenario's:

   - Apparaat licenties - Apps die zijn geïmplementeerd in apparaatverzamelingen en ondersteunen licentieverlening apparaat slechts één licentie per apparaat vereist.  Voorheen moest u een licentie voor elke gebruiker op een apparaat gebruiken. Zie voor meer informatie [volume aangeschaft iOS-apps implementeren op apparaatverzamelingen](/sccm/core/get-started/capabilities-in-technical-preview-1703#deploy-volume-purchased-ios-apps-to-device-collections).
   - Gebruik van meerdere VPP-tokens voor een enkele hybride-tenant met beide tokens voor het beheer van VPP-apps.
   - Gebruik van VPP-tokens onderwijs kunnen een onderscheid maken tussen bedrijfs- en onderwijs-tokens.

### <a name="new-in-configuration-manager-current-branch"></a>Nieuw in Configuration Manager (huidige vertakking)

De volgende functies die eerder beschikbaar in Configuration Manager technische Preview-versies waren zijn nu beschikbaar in hybride implementaties met Intune en Configuration Manager (huidige vertakking) versie 1702.

- [Android voor ondersteuning van werkitems](/sccm/core/plan-design/changes/whats-new-in-version-1702##android-for-work-support)
- [Instellingen voor naleving van niet-compatibele Apps](/sccm/core/plan-design/changes/whats-new-in-version-1702#conditional-access-device-compliance-policy-improvements)
- [Het maken van het PFX-certificaat en distributie en S/MIME-ondersteuning](/sccm/core/plan-design/changes/whats-new-in-version-1702#improvements-to-certificate-profiles)
- [Android en iOS-versies zijn niet langer targetable in wizards voor hybride MDM maken](/sccm/core/plan-design/changes/whats-new-in-version-1702#android-and-ios-versions-are-no-longer-targetable-in-creation-wizards-for-hybrid-mdm)

De volgende aanvullende hybride-functies worden ook opgenomen in versie 1702 van Configuration Manager (huidige vertakking):

- **Verbeterde ondersteuning voor Apple Volume aankoop programma VPP)**

  - U kunt nu gelicentieerde apps implementeren op apparaten en gebruikers. Afhankelijk van de mogelijkheid apps voor ondersteuning van apparaat licentieverlening zal de juiste licentie worden gevraagd tijdens de implementatie, als volgt:

    | Configuration Manager-versie | App apparaat licentieverlening ondersteunt? | Verzameling van implementatietype | Vermeende licentie |
    |-|-|-|-|
    |Ouder is dan 1702|Ja|Gebruiker|Gebruikerslicentie|
    |Ouder is dan 1702|Nee|Gebruiker|Gebruikerslicentie|
    |Ouder is dan 1702|Ja|Apparaat|Gebruikerslicentie|
    |Ouder is dan 1702|Nee|Apparaat|Gebruikerslicentie|
    |1702 en hoger|Ja|Gebruiker|Gebruikerslicentie|
    |1702 en hoger|Nee|Gebruiker|Gebruikerslicentie|
    |1702 en hoger|Ja|Apparaat|Apparaatlicentie|
    |1702 en hoger|Nee|Apparaat|Gebruikerslicentie|

  - U kunt nu ook implementeren en apps die u hebt aangeschaft van het bestand iOS Volume Purchase Program voor onderwijs bijhouden.

  - U kunt meerdere Apple volume aankoop programma tokens nu koppelen met Configuration Manager.

  Zie voor meer informatie over het volume aangeschaft iOS-apps [volume aangeschaft iOS-apps beheren](/sccm/mdm/deploy-use/manage-volume-purchased-ios-apps).

- **Ondersteuning voor LOB-apps in Windows Store voor bedrijven**

  U kunt nu synchroniseren aangepaste line-of-business-apps vanuit de Windows Store voor bedrijven.

- **Nieuwe mobiele bedreiging verdediging controleprogramma 's**

    U hebt nu nieuwe manieren voor het bewaken van de compatibiliteitsstatus met uw serviceprovider mobiele bedreiging verdediging hebben.

    Zie voor meer informatie [mobiele bedreiging verdediging naleving controleren](/sccm/mdm/deploy-use/monitor-mobile-threat-defense-compliance).

## <a name="february-2017"></a>Februari 2017

### <a name="new-in-microsoft-intune"></a>Nieuw in Microsoft Intune

- **De website van de bedrijfsportal moderniseert**

  Apps die zijn bedoeld voor gebruikers die geen beheerde apparaten biedt ondersteuning voor de website van de bedrijfsportal. De website wordt uitgelijnd met andere Microsoft-producten en services met behulp van een nieuw tegengestelde kleurenschema, dynamische illustraties en een "hamburger menu" met de helpdesk contactgegevens en informatie over bestaande beheerde apparaten. De startpagina is voor apps die beschikbaar voor gebruikers met carrousels voor speciale en onlangs bijgewerkt apps zijn benadrukken gerangschikt. U kunt vinden voor en na installatiekopieën beschikbaar is op de [UI updates](/intune/whats-new/whats-new-in-intune-app-ui) pagina.

- **Nieuwe MDM-serveradres voor Windows-apparaten**

  Het adres van de MDM-server voor de registratie van Windows en Windows Phone-apparaten is gewijzigd van manage.microsoft.com in enrollment.manage.microsoft.com. De gebruiker enrollment.manage.microsoft.com als het adres van de MDM-server gebruiken als u wordt gevraagd om tijdens het inschrijven van een Windows waarschuwen of en Windows Phone-apparaat. Deze update is ook een CNAME in DNS die enterpriseenrollment.contoso.com doorverwijst naar manage.microsoft.com worden vervangen door een CNAME in DNS die enterpriseenrollment.contoso.com doorverwijst naar EnterpriseEnrollment-s.manage.microsoft.com vereist. Ga voor meer informatie over deze wijziging naar http://aka.ms/intuneenrollsvrchange.

### <a name="new-in-configuration-manager-technical-preview-1702"></a>Nieuw in Configuration Manager technische Preview 1702

- **Android voor ondersteuning van werkitems**

  U kunt nu Android-apparaten met Android for Work in hybride MDM-omgevingen met behulp van Configuration Manager technische Preview 1702 beheren. Ondersteunde Android-apparaten kunnen nu worden ingeschreven als Android voor werk apparaten, waardoor een werkprofiel wordt gemaakt op het apparaat waarop apps goedgekeurd in Play for Work kunnen worden geïmplementeerd. U kunt ook configureren en implementeren van configuratie-items en nalevingsbeleid toegangsprofielen voor deze apparaten. Zie voor meer informatie [Android voor werk ondersteuning](/sccm/core/get-started/capabilities-in-technical-preview-1702#android-for-work-support).

- **Instellingen voor naleving van niet-compatibele Apps**

  U kunt nu regels niet-compatibele apps voor Android en iOS-apps maken in het nalevingsbeleid. Apparaten hebben de opgegeven toepassingen zijn geïnstalleerd, ze 'niet-compatibele' worden gemarkeerd als toegang tot bedrijfsbronnen op basis van beleid voor voorwaardelijke toegang in plaats gaan verloren. Voor meer informatie [voorwaardelijke toegang apparaat naleving beleid verbeteringen](/sccm/core/get-started/capabilities-in-technical-preview-1702#conditional-access-device-compliance-policy-improvements).

- **Het maken van het PFX-certificaat en distributie en S/MIME-ondersteuning**

  U kunt nu maken en implementeren van PFX-certificaten voor gebruikers in een hybride omgeving. Deze certificaten kunnen vervolgens worden gebruikt voor S/MIME-e-codering en decodering door apparaten die de gebruiker is geregistreerd. Zie voor meer informatie [maken PFX-certificaten met S MIME ondersteunen](/sccm/core/get-started/capabilities-in-technical-preview-1702#create-pfx-certificates-with-s-mime-support).

- **Ondersteuning voor extra iOS-configuratie-instellingen**
   
    U hebt nu 42 extra iOS-instellingen die u als onderdeel van een configuratie-item kunt configureren. De meeste instellingen (35 in alle) zijn toegevoegd voor supervisie iOS-apparaten. Zie voor meer informatie [nieuwe compatibiliteitsinstellingen voor iOS-apparaten](/sccm/core/get-started/capabilities-in-technical-preview-1702#new-compliance-settings-for-ios-devices).

## <a name="january-2017"></a>Januari 2017

### <a name="new-in-microsoft-intune"></a>Nieuw in Microsoft Intune

- **Ondersteuning voor android 7.1.1**

  Intune nu volledig ondersteund en Android 7.1.1 beheert.

- **Probleem waarbij iOS-apparaten zijn niet actief of de beheerconsole niet kan communiceren met deze op te lossen**

  Wanneer apparaten van gebruikers contact met Intune verliest, kunt u deze stappen voor nieuwe voor probleemoplossing worden gebruikt om weer toegang tot bedrijfsbronnen geven. Zie [apparaten niet actief zijn of de beheerconsole niet kan communiceren met deze](/intune/troubleshoot/troubleshoot-device-enrollment-in-intune#devices-are-inactive-or-the-admin-console-cannot-communicate-with-them).

### <a name="new-in-configuration-manager-technical-preview-1701"></a>Nieuw in Configuration Manager technische Preview 1701

- **Android en iOS-versies zijn niet langer targetable in wizards voor hybride MDM maken**

  Technische Preview 1701 vanaf hybride beheer van mobiele apparaten (MDM) wordt moet niet langer u specifieke versies van Android en iOS doel bij het maken van nieuwe beleidsregels en -profielen voor Intune-beheerde apparaten. Met deze wijziging kunnen hybride implementaties ondersteuning bieden sneller voor nieuwe Android en iOS-versies zonder een nieuwe release van Configuration Manager of een uitbreiding. Zie voor meer informatie, [Android en iOS-versies zijn niet langer in wizards voor het maken van targetable](/sccm/core/get-started/capabilities-in-technical-preview-1701#android-and-ios-versions-are-no-longer-targetable-in-creation-wizards-for-hybrid-mdm).


## <a name="december-2016"></a>December 2016

### <a name="new-in-microsoft-intune"></a>Nieuw in Microsoft Intune

- **Multi-Factor authentication (MFA) voor inschrijving wordt verplaatst naar de Azure-portal**

  U zou eerder, gaat u naar de Intune-console of de Configuration Manager-console in te stellen van MFA voor inschrijvingen met Intune. Met deze functie bijgewerkte u nu aanmelden bij de [Microsoft Azure-portal] (https://manage.windowsazure.com) met behulp van uw Intune-referenties en MFA configureren via de Azure AD. Voor meer informatie, Zie [multi-factor authentication voor Microsoft Intune] (https://aka.ms/mfa_ad).

- **Bedrijfsportal-app voor Android is nu beschikbaar in China**

  De bedrijfsportal-app voor Android is nu beschikbaar in China. Vanwege het ontbreken van Google Play Store in China, moeten de Android-apparaten apps verkrijgen van Chinese app marktplaatsen. De bedrijfsportal-app voor Android is gedownload op de volgende databases:

  -    [Baidu](https://go.microsoft.com/fwlink/?linkid=836946)
  -    [Huawei](https://go.microsoft.com/fwlink/?linkid=836948)
  -    [Tencent](https://go.microsoft.com/fwlink/?linkid=836949)
  -    [Wandoujia](https://go.microsoft.com/fwlink/?linkid=836950)
  -    [Xiaomi](https://go.microsoft.com/fwlink/?linkid=836947)

  De bedrijfsportal-app voor Android gebruikt Google Play-Services om te communiceren met de Microsoft Intune-service. Aangezien de Google Play-Services zijn nog niet beschikbaar in China, kan een van de volgende taken uitvoeren tot 8 uur duren.

  | Configuration Manager-beheerconsole | Intune-bedrijfsportal-app voor Android | Intune-Portal bedrijfswebsite |
  |----|----|----|        
  | Buiten gebruik stellen/wissen (alle gegevens verwijderen)    | Een apparaat verwijderen | Apparaat (lokale en externe) verwijderen |
  | Buiten gebruik stellen/wissen (bedrijfsgegevens verwijderen)    | Apparaat opnieuw instellen | Apparaat opnieuw instellen|
  | Nieuwe of bijgewerkte app-implementaties | Installeren van beschikbare LOB-apps | Wachtwoordcode opnieuw instellen van apparaat|
  | Vergrendelen op afstand    | | |
  | Wachtwoordcode opnieuw instellen | | |        


## <a name="november-2016"></a>November 2016

### <a name="new-in-microsoft-intune"></a>Nieuw in Microsoft Intune

- **Nieuwe Microsoft Intune-bedrijfsportal beschikbaar voor Windows 10-apparaten**

  Microsoft heeft een nieuwe [bedrijfsportal-app voor Windows 10-apparaten](https://www.microsoft.com/store/apps/9wzdncrfj3pz). Deze app maakt gebruik van de nieuwe Windows 10 universele indeling biedt een bijgewerkte gebruikerservaring die identiek is op alle Windows 10-apparaten, PC en mobiele die met terwijl u toch dezelfde functionaliteit verstrekt door vorige bedrijfsportal-apps.

  De nieuwe app maakt gebruik van platform functies zoals eenmalige aanmelding (SSO) en verificatie op basis van een certificaat voor Windows 10-apparaten. De app is beschikbaar als een upgrade naar de bestaande bedrijfsportal voor Windows 8.1 en Windows Phone 8.1-bedrijfsportal wordt geïnstalleerd vanuit de Windows Store. Voor meer informatie gaat u naar de [Intune Support-teamblog](http://aka.ms/intunecp_universalapp).

  Nieuwe bedrijfsportal-app ook een Windows Store voor zakelijke toepassingen gemarkeerd weergegeven **beschikbaar** in de Configuration Manager-console.


### <a name="new-in-configuration-manager-current-branch"></a>Nieuw in Configuration Manager (huidige vertakking)

De volgende functies die eerder beschikbaar in Configuration Manager technische Preview-versies waren zijn nu beschikbaar in hybride implementaties met Intune en Configuration Manager (huidige vertakking) versie 1610.

* [Extra instellingen en verbeterde ervaring voor configuratie-items](/sccm/core/plan-design/changes/whats-new-in-version-1610#new-compliance-settings-for-configuration-items)
* [Extra instellingen voor DEP-profielen](whats-new-hybrid-archive.md#new-in-configuration-manager-technical-preview-1609)
* [Windows Store-apps betalen voor bedrijven](/sccm/apps/deploy-use/manage-apps-from-the-windows-store-for-business)
* [Systeemeigen verbindingstypen voor Windows 10 VPN-profielen](whats-new-hybrid-archive.md#new-in-configuration-manager-technical-preview-1609)
* [Intune compatibiliteit grafieken](/sccm/protect/deploy-use/create-compliance-policy#monitor-the-compliance-policy)
* [Aanvraag voor het beleid voor synchronisatie van console](/sccm/mdm/deploy-use/sync-intune-device)
* [Configuratie-instellingen voor Windows Defender](/sccm/compliance/deploy-use/create-configuration-items-for-windows-8.1-and-windows-10-devices-managed-without-the-client#windows-defender)

De volgende aanvullende hybride-functies worden ook opgenomen in versie 1610 van Configuration Manager (huidige vertakking):

- **Toenemend aantal geregistreerde apparaten**

  U kunt nu gebruikers maximaal 15 apparaten kunnen inschrijven inschakelen. De limiet voor de vorige is 5 apparaten per gebruiker.


- **Ondersteuning voor extra beveiliging**

  Naast het volledige beheerder hebben de volgende ingebouwde beveiligingsrollen nu volledige toegang tot items in het knooppunt alle apparaten in Bedrijfseigendom, waaronder Predeclared apparaten, iOS-Inschrijvingsprofielen en Windows-Inschrijvingsprofielen:

    - Asset Intelligence-beheerder
    - Toegang tot bedrijfsbronnen

  Alleen-lezen toegang tot deze gebieden van de Configuration Manager-console wordt nog steeds verleend aan de rol alleen-Lezenanalist.

- **Automatische activering VPN-toegang van apps voor Windows-gegevensbeveiliging**

  U kunt een Windows-gegevensbeveiliging primair domein toevoegen aan Windows 10 VPN-profielen die ervoor zorgt dat alle apps die worden gekoppeld aan een VPN-verbinding automatisch wordt geactiveerd wanneer ze worden uitgevoerd op het apparaat. Deze optie is alleen beschikbaar als u kiest een systeemeigen verbindingstype.

- **Voorwaardelijke toegang voor Windows 10 VPN-profielen**

    U kunt nu vereisen Windows 10 apparaten geregistreerd in Azure Active Directory aan het beleid voldoen om VPN-toegang hebben via Windows 10 VPN-profielen die zijn gemaakt in de Configuration Manager-console. Dit is mogelijk via het nieuwe **voorwaardelijke toegang inschakelen voor deze VPN-verbinding** selectievakje op de pagina methode voor verificatie in de wizard VPN-profiel en de eigenschappen van VPN-profiel voor Windows 10 VPN-profielen. Deze optie is alleen beschikbaar als u kiest een systeemeigen verbindingstype.

    U kunt ook een afzonderlijke certificaat voor verificatie voor eenmalige aanmelding opgeven als u voorwaardelijke toegang voor het profiel inschakelen.


## <a name="notices"></a>Kennisgevingen

### <a name="system-center-2012-configuration-sp1-and-system-center-2012-r2-configuration-manager-rtm-support-for-hybrid-mobile-device-management-ending-on-april-10-2017"></a>System Center 2012 Configuration SP1 en System Center 2012 R2 Configuration Manager (RTM): Ondersteuning voor het beheer van mobiele apparaten hybride eindigt op 10 April 2017

*11 januari 2017*

Ondersteuning voor System Center 2012 Configuration Manager SP1 en System Center 2012 R2 Configuration Manager RTM is gestopt op 12 juli 2016. Later, ondersteuning voor deze verbinding maken met de Microsoft Intune-service voor hybride MDM op 10 April 2017 eindigt releases. Na deze datum stoppen hybride MDM werkt met deze releases. Beheerde apparaten in wezen niet-beheerd worden omdat de Intune-Connector niet meer verbinding met de Intune-service maken wordt. Configuration Manager-gegevens (zoals beleidsregels en toepassingen) wordt niet stromen tot Intune en beheerde apparaten wordt niet gegevensstroom naar Configuration Manager totdat u een upgrade wordt uitgevoerd.

Als u een hybride implementatie met Configuration Manager 2012 SP1 of R2 RTM uitvoert, raden wij u aan vóór 10 April 2017 te upgraden naar Configuration Manager (huidige vertakking) of de laatste ondersteunde servicepack voor Configuration Manager 2012 (R2 SP1 of SP2) om te voorkomen dat de service wordt onderbroken.

Aanvullende bronnen:
-    [Upgraden naar System Center Configuration Manager (huidige vertakking)](/sccm/core/servers/deploy/install/upgrade-to-configuration-manager)
-    [Planning voor het upgraden naar System Center 2012 R2 Configuration Manager SP1](https://technet.microsoft.com/library/jj822981.aspx#BKMK_PlanningR2SP1Upgrade)
-    [Planning voor het upgraden naar System Center 2012 Configuration Manager SP2](https://technet.microsoft.com/library/jj822981.aspx#BKMK_PlanningSP2Upgrade)

### <a name="windows-phone-8-company-portal-upload-deprecated"></a>Windows Phone 8-bedrijfsportal uploaden afgeschaft
*25 oktober 2016*

De mogelijkheid voor het uploaden van een ondertekende bedrijfsportal-app is verwijderd uit de Configuration Manager-console, zoals ondersteuning voor Intune wordt vervangen voor Windows 8, Windows Phone 8 en Windows RT en ondersteuning voor de Windows Phone 8-bedrijfsportal wordt beëindigd in November.  Windows 8, Windows Phone 8 en Windows RT-apparaten die al zijn ingeschreven wordt nog steeds ondersteund, maar inschrijven extra apparaten met deze platforms worden niet ondersteund.


### <a name="see-also"></a>Zie ook

- [Het verleden hybride MDM-functies](whats-new-hybrid-archive.md)
- [Wat is nieuw voor met MDM in System Center 2012 Configuration Manager](https://technet.microsoft.com/library/mt445560.aspx)

