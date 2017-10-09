---
title: Wat is er nieuw in hybride MDM met Configuration Manager | Microsoft Docs
description: Meer informatie over de nieuwe functies voor mobiele apparaten beschikbaar voor hybride implementaties met Configuration Manager en Intune.
ms.custom: na
ms.date: 10/04/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: configmgr-hybrid
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 7b127cee-61f1-4681-9760-caebed36ddf5
author: dougeby
ms.author: dougeby
manager: angrobe
ms.openlocfilehash: 6c2c6ffee3b2084ede61e5602a78bf5ca82446f6
ms.sourcegitcommit: 6c70e0af8d9af208009641786a3b555db4482e97
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/05/2017
---
# <a name="whats-new-in-hybrid-mobile-device-management-with-system-center-configuration-manager-and-microsoft-intune"></a>Wat is er nieuw in hybride mobile device management met System Center Configuration Manager en Microsoft Intune

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

## <a name="september-2017"></a>September 2017

### <a name="new-in-microsoft-intune"></a>Nieuw in Microsoft Intune     

- **Vernieuwen van de actie die zijn toegevoegd aan de bedrijfsportal-app voor Windows 10**<!-- 1132468 -->    
    De bedrijfsportal-app voor Windows 10 kan gebruikers de gegevens in de app vernieuwen door beide binnenhalen om te vernieuwen, of op desktops, op F5 te drukken.

- **Eindgebruikers informeren over welke gegevens van een apparaat worden weergegeven voor iOS**<!--739894-->    
    We hebben toegevoegd **eigendomstype** naar het scherm Apparaatdetails op de bedrijfsportal-app voor iOS. Hiermee kunnen gebruikers voor meer informatie over privacy rechtstreeks op deze pagina van de Intune-eindgebruikers-documenten. Ze is ook mogelijk om deze informatie in het scherm over te vinden. 

- **Gemakkelijker te begrijpen formulering voor de bedrijfsportal-app voor Android**<!---1396349-->       
    Het inschrijvingsproces voor de bedrijfsportal-app voor Android is vereenvoudigd door nieuwe tekst om het gemakkelijker voor eindgebruikers te registreren. Als u aangepaste inschrijving documentatie hebt, wilt u een update uit om de nieuwe schermen weer te geven. U kunt voorbeeldquery afbeeldingen vinden op onze [UI-updates voor Intune-eindgebruikers apps](https://docs.microsoft.com/intune/whats-new-app-ui#week-of-september-11-2017) pagina.

- **Windows 10-bedrijfsportal-app toegevoegd aan Windows Information Protection toestaan**<!-- 677129 -->    
    De app bedrijfsportal voor Windows 10 is bijgewerkt ter ondersteuning van Windows-beveiliging (OHW). De app kan worden toegevoegd aan het onderhanden werk toestaan. Met deze wijziging heeft de app niet meer worden toegevoegd aan de **uitgezonderd** lijst. 

- **Einde van de kennisgeving van ondersteuning toegevoegd voor iOS 8.0**    
    Een bericht is toegevoegd voor einde van ondersteuning voor iOS 8.0. Zie voor meer informatie [meldingen](#notices).

## <a name="august-2017"></a>Augustus 2017

### <a name="new-in-microsoft-intune"></a>Nieuw in Microsoft Intune     

- **Nieuwe aangemelde ervaring voor Android-bedrijfsportal gebruikers- en beveiligingsbeleid van App-gebruikers**<!-- 621669 -->    
Eindgebruikers kunnen nu apps bladeren, apparaten beheren en weergeven contact opnemen met IT gegevens door middel van de Android-bedrijfsportal-app zonder hun Android-apparaten inschrijven. Bovendien, als een eindgebruiker al gebruikmaakt van een app door Intune-App worden beveiligd en start de Android-bedrijfsportal, de eindgebruiker niet langer gevraagd het apparaat te registreren.


## <a name="july-2017"></a>Juli 2017

### <a name="new-in-microsoft-intune"></a>Nieuw in Microsoft Intune

- **Einde van aankondigingen van ondersteuning toegevoegd voor Android en Windows Phone**

    Nieuwe meldingen zijn toegevoegd voor het einde van ondersteuning voor Android en Windows Phone-versies. Zie voor meer informatie [meldingen](#notices).


### <a name="new-in-configuration-manager-current-branch"></a>Nieuw in Configuration Manager (huidige vertakking)

De volgende functies die eerder beschikbaar in Configuration Manager Technical Preview-versies waren zijn nu beschikbaar in hybride implementaties met Intune en Configuration Manager (huidige vertakking) versie 1706.

- [Ondersteuning voor certificeringsinstanties Entrust belasten](/sccm/core/get-started/capabilities-in-technical-preview-1706#support-for-entrust-certification-authorities)
- [Nieuwe beleidsinstellingen voor mobile application management](/sccm/core/plan-design/changes/whats-new-in-version-1706#new-mobile-application-management-policy-settings)
- [Updates voor Android for Work-configuratie voor delen](/sccm/core/plan-design/changes/whats-new-in-version-1706#updates-to-android-for-work-sharing-configuration)
- [Nieuwe beleidsregels voor naleving van apparaat](/sccm/core/plan-design/changes/whats-new-in-version-1706#new-device-compliance-policy-rules)
- [Nieuwe configuratie-instellingen voor Windows 10-apparaten die niet worden beheerd met Configuration Manager-client](/sccm/core/plan-design/changes/whats-new-in-version-1706#new-configuration-settings-for-windows-10-devices-that-are-not-managed-with-the-configuration-manager-client)
- [Cisco (IPsec) ondersteuning voor Mac OS VPN-profielen](/sccm/core/get-started/capabilities-in-technical-preview-1706#cisco-ipsec-support-for-macos-vpn-profiles)
- [Beperkingen voor android en iOS-inschrijving](/sccm/core/plan-design/changes/whats-new-in-version-1706#android-and-ios-enrollment-restrictions) 

## <a name="june-2017"></a>Juni 2017

### <a name="new-in-microsoft-intune"></a>Nieuw in Microsoft Intune

- **Uw MDM-instantie wijzigen**

  Vanaf Configuration Manager versie 1610, kunt u uw MDM-instantie zonder contact opnemen met Microsoft Support en zonder de registratie ongedaan maken en registreren van uw bestaande beheerde apparaten. Zie voor meer informatie [wijzigen van uw MDM-instantie]( /sccm/mdm/deploy-use/change-mdm-authority).

- **Beheerde browser en app-proxy-integratie**

  De Intune Managed Browser kunnen nu geïntegreerd met de service Azure AD-toepassingsproxy gebruikers toegang biedt tot interne websites, zelfs wanneer ze extern werken. Gebruikers van de browser Voer de URL van de site zoals ze normaal en de Managed Browser de aanvraag via de gateway application proxy web stuurt. Zie voor meer informatie [toegang tot het Internet beheren met beheerde-browserbeleid](/intune/app-configuration-managed-browser).

- **Bedrijfsportal-app voor Android is nu een nieuwe ervaring voor de eindgebruiker voor App-beveiligingsbeleid**

  Op basis van feedback van klanten, hebben we de bedrijfsportal-app voor Android om weer te geven gewijzigd een **toegang bedrijf inhoud** knop. De bedoeling is om te voorkomen dat eindgebruikers onnodig gaan via het registratieproces wanneer ze alleen toegang tot apps die ondersteuning bieden voor App-beleid voor beveiliging, een functie van Intune-beheer van mobiele toepassingen nodig. U kunt deze wijzigingen kan zien op de [wat is er nieuw in app UI](/intune/whats-new-app-ui) pagina.

- **Nieuwe menu Actie eenvoudig bedrijfsportal verwijderen**

  Op basis van feedback van gebruikers, is de bedrijfsportal-app voor Android een nieuwe menu Actie voor het initiëren van het verwijderen van de bedrijfsportal van uw apparaat toegevoegd. Deze actie verwijdert het apparaat uit Intune-beheer, zodat de app kan worden verwijderd van het apparaat door de gebruiker. U kunt deze wijzigingen kan zien op de [wat is er nieuw in gebruikersinterface-app](/intune/whats-new-app-ui) pagina en in de [documentatie voor Android-eindgebruikers](/intune-user-help/unenroll-your-device-from-intune-android).

- **Verbeteringen in de app worden gesynchroniseerd met Windows 10 auteurs Update**

  De bedrijfsportal-app voor Windows 10 nu start automatisch een synchronisatie voor aanvragen van de app installeren voor apparaten met Windows 10 auteurs Update (versie 1703). Dit vermindert het probleem van app-installaties afslaan tijdens de status 'Sync in behandeling'. Bovendien kunnen gebruikers zich aan om een synchronisatie uit vanuit de app handmatig te starten. U kunt deze wijzigingen kan zien op de [wat is er nieuw in app UI](/intune/whats-new-app-ui) pagina.

- **Nieuwe begeleide ervaring voor Windows 10-bedrijfsportal**

  De bedrijfsportal-app voor Windows 10 bevat een begeleide ervaring van Intune walkthrough voor apparaten die niet zijn geïdentificeerd of geregistreerd. De nieuwe ervaring bevat stapsgewijze instructies die de gebruiker door het registratieproces te in Azure Active Directory leiden (vereist voor voorwaardelijke toegang functies) en de MDM-registratie (vereist voor apparaatfuncties management). De begeleide ervaring zijn toegankelijk vanaf de startpagina van de bedrijfsportal. Gebruikers kunnen de app gebruiken als ze niet registratie en de inschrijving uitvoert, maar heeft beperkte functionaliteit merken blijven.

  Deze update is alleen zichtbaar op apparaten met Windows 10 Verjaardag Update (build 1607) of hoger. U kunt deze wijzigingen kan zien op de [wat is er nieuw in app UI](/intune/whats-new-app-ui) pagina.

- **Verbeteringen in de app-tegels in de bedrijfsportal-app voor iOS**

  Het ontwerp van de app-tegels op de startpagina in overeenstemming met de huisstijl kleur die u voor de bedrijfsportal instelt is bijgewerkt. Zie voor meer informatie [wat is er nieuw in app UI](/intune/whats-new-app-ui).

- **Account objectkiezer nu beschikbaar voor de bedrijfsportal-app voor iOS**

  Gebruikers van iOS-apparaten zien mogelijk onze nieuwe account kiezen wanneer ze zich in de bedrijfsportal als ze hun werk- of gebruikt schoolaccount voor aanmelding bij andere Microsoft-apps. Zie voor meer informatie [wat is er nieuw in app UI](/intune/whats-new-app-ui).

### <a name="new-in-configuration-manager-technical-preview-1706"></a>Nieuw in Configuration Manager Technical Preview 1706

- **Nieuwe beleidsinstellingen voor mobile application management**    

  De volgende beleidsinstellingen voor mobile application management (MAM) zijn nu beschikbaar:

  - **Schermafbeelding (alleen Android-apparaten) blokkeren:** Hiermee wordt opgegeven dat de schermafbeeldingsmogelijkheden van het apparaat zijn geblokkeerd bij gebruik van deze app.
  - **Synchronisatie van contactpersonen uitschakelen:** Hiermee voorkomt dat de app opslaan van gegevens in de systeemeigen contactpersonen-app op het apparaat.
  - **Afdrukken uitschakelen:** Voorkomt dat de app vanuit afdrukken werk- of schoolgegevens.

  Zie [apps beveiligen met beleid voor app-beveiliging in Configuration Manager](https://docs.microsoft.com/sccm/mdm/deploy-use/protect-apps-using-mam-policies) om te proberen de nieuwe beleidsinstellingen van de app-beveiliging.

- **Nieuwe configuratie-item-instellingen van Windows**  <!-- 1354715 -->    

  Nieuwe Windows-configuratie-items zijn beschikbaar voor de instelling wachtwoord, apparaat, Store en Microsoft Edge categorieën. Zie voor meer informatie [nieuwe Windows-configuratie-iteminstellingen](/sccm/core/get-started/capabilities-in-technical-preview-1706#new-windows-configuration-item-settings).

- **Nieuwe beleidsregels voor naleving van apparaat**    

  U kunt nu de nieuwe opties voor nalevingsbeleid die eerder alleen beschikbaar in zelfstandige versie van Intune waren configureren. Zie voor meer informatie [apparaat naleving beleid verbeteringen](/sccm/core/get-started/capabilities-in-technical-preview-1706#new-device-compliance-policy-rules).

- **Android en iOS-inschrijving beperkingen**<!-- 1290826 -->      

  Beheerders kunnen nu opgeven dat gebruikers persoonlijke Android- of iOS-apparaten in hun omgeving hybride kunnen niet registreren. Hiermee kunt u limiet ingeschreven apparaten predeclared, bedrijfseigen apparaten of alleen met Device Enrollment Program ingeschreven iOS-apparaten. Zie voor meer informatie [Android en iOS-inschrijving beperkingen](/sccm/core/get-started/capabilities-in-technical-preview-1706#android-and-ios-enrollment-restrictions).

- **Ondersteuning voor certificeringsinstanties Entrust**<!-- 1350740 -->     

  Configuration Manager ondersteunt nu Entrust certificeringsinstanties; Hierdoor kunnen de levering van PFX-certificaat voor apparaten die zijn ingeschreven bij Microsoft Intune.    

  U kunt Entrust configureren als de certificeringsinstantie (CA) bij het toevoegen van een rol Certificaatregistratiepunt in Configuration Manager. Wanneer u een nieuw certificaatprofiel die PFX-certificaten uitgeeft toevoegt, kunt u een Microsoft- of Entrust certificeringsinstantie selecteren.

  **Bekende probleem**: In de technical preview 1706 zijn PFX-certificaten niet uitgegeven voor Microsoft-certificeringsinstanties. Dit geldt niet voor geïmporteerde PFX-certificaten of SCEP-profielen.

- **Cisco (IPsec) ondersteuning voor Mac OS VPN-profielen**  <!-- 1321367 -->    

  U kunt een Mac OS VPN-profiel maken met Cisco (IPsec) als het verbindingstype. Zie voor meer informatie [VPN-profielen maken](/sccm/mdm/deploy-use/create-vpn-profiles#create-vpn-profiles).


## <a name="april-2017"></a>April 2017

### <a name="new-in-microsoft-intune"></a>Nieuw in Microsoft Intune

- **MyApps beschikbaar voor Managed Browser**

  Microsoft MyApps hebben nu een betere ondersteuning binnen de Managed Browser. Beheerde Browsergebruikers die niet zijn bedoeld voor het beheer wordt geopend rechtstreeks aan de service MyApps, waar ze toegang krijgen tot hun admin ingericht SaaS-apps. Gebruikers die zijn bedoeld voor het beheer van Intune blijven MyApps van de ingebouwde Managed Browser bladwijzer toegang moeten hebben.

- **Nieuwe pictogrammen voor de Managed Browser en de bedrijfsportal**

  De Managed Browser ontvangt bijgewerkte pictogrammen voor de Android- en iOS-versies van de app. Het pictogram Nieuw bevatten de bijgewerkte Intune badge om het te maken met andere apps consistente in Enterprise Mobility + Security (EM + S). U kunt het nieuwe pictogram voor de Managed Browser zien op de [wat is er nieuw in Intune op de pagina app UI](/intune/whats-new/whats-new-in-intune-app-ui.md).

  Bijgewerkte pictogrammen voor de Android, iOS en Windows-versies van de app voor het verbeteren van de consistentie met andere apps in EM + S is ook ontvangen van de bedrijfsportal. Deze pictogrammen worden verschillende platforms van April eind mei geleidelijk uitgebracht.

- **Meld u aan voortgangsindicator in Android-bedrijfsportal**

  Een update voor de Android-bedrijfsportal-app bevat een teken in voortgangsindicator, wanneer de gebruiker wordt gestart of de app hervat. De indicator doorloopt nieuwe statussen, beginnen met 'Verbinden...' vervolgens 'Ondertekening in...' en 'Controleren voor de beveiligingsvereisten...' voorafgaand aan zodat de gebruiker toegang tot de app. U kunt de nieuwe schermen voor de bedrijfsportal-app voor Android zien op de [wat is er nieuw in Intune op de pagina app UI](/intune/whats-new/whats-new-in-intune-app-ui.md).

- **Toegang tot SharePoint Online blokkeren apps**

  U kunt een beleid voor voorwaardelijke toegang op basis van een app voor het blokkeren van apps, waarvoor geen app protection-beleid toegepast naar hen nu toegang tot maken [SharePoint Online](/InTune/deploy-use/mam-ca-for-sharepoint-online). In het scenario voor voorwaardelijke toegang op basis van apps, kunt u de apps die u wilt toegang hebben tot SharePoint Online met Azure portal.

### <a name="new-in-configuration-manager-technical-preview-1704"></a>Nieuw in Configuration Manager Technical Preview 1704

- **Android-apps met app-configuratiebeleid configureren**

  U kunt app-configuratiebeleid in System Center Configuration Manager (Configuration Manager) vooraf geconfigureerde instellingen distribueren wanneer een gebruiker een app uitvoert op Android gebruiken voor werk apparaten. Configuratiebeleid voor android-app zijn alleen beschikbaar voor apparaten met Android for Work en gelden voor goedgekeurde apps uit de Play voor werk store. Zie voor meer informatie over het uitproberen van deze functie [configureren Android-apps met configuratiebeleid voor apps](/sccm/core/get-started/capabilities-in-technical-preview-1704#configure-android-apps-with-app-configuration-policies).

## <a name="march-2017"></a>Maart 2017

### <a name="new-in-microsoft-intune"></a>Nieuw in Microsoft Intune

- **Nieuwe gebruikerservaring op voor de bedrijfsportal-app voor Android**

  De bedrijfsportal-app voor Android is een meer moderne vormgeving op de gebruikersinterface. De belangrijke updates zijn:

  - Kleuren: Bedrijf Portal tabblad headers zijn gekleurd in huisstijl IT gedefinieerd.
  - Apps: In de **Apps** tabblad de **aanbevolen Apps** en **alle Apps** knoppen worden bijgewerkt.
  - Zoeken: In de **Apps** tabblad de **zoeken** een zwevende actie knop.
  - Navigeren Apps: **Alle Apps** weergave toont tabbladen weergeven van **aanbevolen**, **alle**, en **categorieën** voor navigatie te vereenvoudigen.
  - Ondersteuning: **Mijn apparaten** en **contact opnemen met IT** tabbladen zijn bijgewerkt voor een betere leesbaarheid.

  Zie voor meer informatie over deze wijzigingen [UI-updates voor Intune-eindgebruikers apps](/intune/whats-new/whats-new-in-intune-app-ui).

- **Script voor Windows 10-bedrijfsportal te ondertekenen**

  Als u downloaden en de bedrijfsportal voor Windows 10-Apps sideloaden wilt, kunt u nu een script gebruiken om te vereenvoudigen en het proces voor het ondertekenen van Apps voor uw organisatie te stroomlijnen.  Zie voor het downloaden van het script en de instructies voor het gebruik ervan [Microsoft Intune-ondertekening Script voor Windows 10 bedrijfsportal](https://aka.ms/win10cpscript) op TechNet-galerie. Zie voor meer informatie over deze aankondiging [bijwerken van uw Windows 10-bedrijfsportal-app](https://blogs.technet.microsoft.com/intunesupport/2017/03/13/updating-your-windows-10-company-portal-app/) op het Intune-teamblog voor ondersteuning.

- **Verbeterde ondersteuning voor Android-gebruikers op basis van China**

  Wegens het ontbreken van de Google Play Store in China, moeten Android-apparaten ophalen met apps Chinees marktplaatsen. De bedrijfsportal ondersteunt deze werkstroom door het omleiden van Android-gebruikers in China om de bedrijfsportal-App en Outlook-apps downloaden van lokale app stores. Dit verbetert de ervaring van de gebruiker wanneer het beleid voor voorwaardelijke toegang ingeschakeld, zowel voor beheer van mobiele apparaten en voor Mobile Application Management. De bedrijfsportal-App en Outlook-apps voor Android zijn beschikbaar op de volgende Chinees app worden opgeslagen:

  - [Baidu](https://go.microsoft.com/fwlink/?linkid=836946)
  - [Xiaomi](https://go.microsoft.com/fwlink/?linkid=836947)
  - [Tencent](https://go.microsoft.com/fwlink/?linkid=836949)
  - [Huawei](https://go.microsoft.com/fwlink/?linkid=836948)
  - [Wandoujia](https://go.microsoft.com/fwlink/?linkid=836950)

- **Zorg ervoor dat uw bedrijfsportal-apps zijn bijgewerkt**

  December 2016, wij een update uitgebracht die afdwingen voor multi-factor authentication (MFA) ingeschakeld op een groep gebruikers wanneer ze een iOS-, Android, Windows 8.1 + of Windows Phone 8.1 + apparaat inschrijven. Deze functie kan niet werken zonder bepaalde basislijnversies van de bedrijfsportal-app voor Android (v5.0.3419.0 +) en iOS (v2.1.17 +).

  Mogelijkheden van Intune continu verbeteren en veel verbeteringen hebben gecoördineerd updates voor de bedrijfsportal apps op alle ondersteunde platforms. Als gevolg hiervan adviseren we dat u de nieuwste versies van de bedrijfsportal-apps op is geïnstalleerd op apparaten om te profiteren van verbeteringen in Intune en voor de beste gebruikerservaring.

  >[!Tip]
  > Laat uw gebruikers hun apparaten automatisch bijwerken van de juiste appstore-apps in te stellen. Als u hebt de Android-bedrijfsportal-app beschikbaar gesteld op een netwerkshare bevindt, kunt u downloaden met de meest recente versie van [Microsoft Download Center](https://www.microsoft.com/download/details.aspx?id=49140).

- **Microsoft-Teams is nu ingeschakeld voor MAM op iOS en Android**

  De Microsoft-Teams apps voor iOS en Android zijn nu beschikbaar met de mogelijkheden van Intune mobile Application management (MAM), zodat u dat uw teams vrijelijk werken op apparaten zorgen kunt, terwijl u ervoor zorgt dat conversaties en zakelijke gegevens op elke beurt beveiligd. Zie voor meer informatie [de aankondiging van de Microsoft-Teams](https://blogs.technet.microsoft.com/enterprisemobility/2017/03/14/microsoft-teams-is-now-generally-available-and-mam-enabled-on-ios-and-android/) op de Enterprise Mobility and Security-blog.

### <a name="new-in-configuration-manager-technical-preview-1703"></a>Nieuw in Configuration Manager Technical Preview 1703

- **Extra ondersteuning voor Apple Volume Purchase Program-scenario 's**

   Vanaf Technical Preview 1703, hebt u nu ondersteuning voor het volgende Volume Purchase Program (VPP)-scenario's:

   - Apparaat licenties - Apps die ondersteuning voor de apparaat-licentieverlening en geïmplementeerd in apparaatverzamelingen nu slechts één licentie per apparaat nodig.  Voorheen moest u een licentie voor elke gebruiker op een apparaat gebruiken. Zie voor meer informatie [iOS volume-aankoopprogramma gekochte apps implementeren op apparaatverzamelingen](/sccm/core/get-started/capabilities-in-technical-preview-1703#deploy-volume-purchased-ios-apps-to-device-collections).
   - Gebruik van meerdere VPP-tokens in een enkel hybride-tenant met beide tokens voor het beheer van VPP-apps.
   - Gebruik van VPP-tokens education met de mogelijkheid om onderscheid maken tussen bedrijven en education tokens.

### <a name="new-in-configuration-manager-current-branch"></a>Nieuw in Configuration Manager (huidige vertakking)

De volgende functies die eerder beschikbaar in Configuration Manager Technical Preview-versies waren zijn nu beschikbaar in hybride implementaties met Intune en Configuration Manager (huidige vertakking) versie 1702.

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

- **Ondersteuning voor line-of-business-apps in Windows Store voor bedrijven**

  U kunt aangepaste LOB-apps vanuit de Windows Store voor bedrijven nu synchroniseren.

- **Nieuwe mobiele Threat verdediging controlehulpprogramma 's**

    U hebt nu een nieuwe manieren om de compatibiliteitsstatus met uw serviceprovider Mobile Threat verdediging te controleren.

    Zie voor meer informatie [Mobile Threat verdediging naleving controleren](/sccm/mdm/deploy-use/monitor-mobile-threat-defense-compliance).

## <a name="february-2017"></a>Februari 2017

### <a name="new-in-microsoft-intune"></a>Nieuw in Microsoft Intune

- **De bedrijfsportalwebsite modernisering**

  De bedrijfsportalwebsite ondersteunt apps die zijn gericht op gebruikers die geen beheerde apparaten. De website wordt uitgelijnd met andere Microsoft-producten en services met behulp van een nieuw tegengestelde kleurenschema, dynamische illustraties en een 'hamburger menu"met de helpdesk contactgegevens en informatie over het bestaande beheerde apparaten. De startpagina is geordend, zodat de apps die beschikbaar voor gebruikers met een carrousels voor aanbevolen en onlangs bijgewerkt apps zijn benadrukken. U kunt vinden voor en na installatiekopieën beschikbaar zijn op de [UI updates](/intune/whats-new/whats-new-in-intune-app-ui) pagina.

- **Nieuw adres door MDM-server voor Windows-apparaten**

  Het adres van de MDM-server voor het inschrijven van Windows en Windows Phone-apparaten is gewijzigd van manage.microsoft.com in enrollment.manage.microsoft.com. Uw gebruiker enrollment.manage.microsoft.com gebruiken als het adres van de MDM-server als gevraagd om deze tijdens het inschrijven van een Windows waarschuwen of en Windows Phone-apparaat. Deze update moet ook een CNAME in DNS die enterpriseenrollment.contoso.com omleidt naar manage.microsoft.com worden vervangen door een CNAME in DNS die enterpriseenrollment.contoso.com omleidt naar EnterpriseEnrollment-s.manage.microsoft.com. Ga naar http://aka.ms/intuneenrollsvrchange voor meer informatie over deze wijziging.

### <a name="new-in-configuration-manager-technical-preview-1702"></a>Nieuw in Configuration Manager Technical Preview 1702

- **Android voor Work-ondersteuning**

  U kunt nu Android-apparaten met Android for Work in hybride MDM-omgevingen met behulp van Configuration Manager Technical Preview 1702 beheren. Ondersteunde Android-apparaten kunnen nu worden ingeschreven als Android voor Work-apparaten die u maakt een work-profiel op het apparaat waarop de apps die zijn goedgekeurd in de Play voor werk kunnen worden geïmplementeerd. U kunt ook configureren en implementeren van configuratie-items, beleidsregels voor naleving en brontoegangsprofielen voor deze apparaten. Zie voor meer informatie [Android voor ondersteuning van werk](/sccm/core/get-started/capabilities-in-technical-preview-1702#android-for-work-support).

- **Instellingen voor naleving van niet-compatibele Apps**

  U kunt nu regels van de niet-compatibele apps voor Android en iOS-apps in een nalevingsbeleid maken. Als apparaten de opgegeven toepassingen geïnstalleerd zijn, wordt deze 'niet-compatibele' zijn gemarkeerd en geen toegang meer tot bedrijfsbronnen op basis van beleid voor voorwaardelijke toegang in plaats. Voor meer informatie [voorwaardelijke toegang apparaat naleving beleid verbeteringen](/sccm/core/get-started/capabilities-in-technical-preview-1702#conditional-access-device-compliance-policy-improvements).

- **PFX-certificaat maken en distributie en het S/MIME-ondersteuning**

  U kunt nu maken en implementeren van PFX-certificaten voor gebruikers in een hybride omgeving. Deze certificaten kunnen vervolgens worden gebruikt voor S/MIME-e-versleuteling en ontsleuteling door apparaten waarop de gebruiker is ingeschreven. Zie voor meer informatie [maken PFX-certificaten met S MIME ondersteunen](/sccm/core/get-started/capabilities-in-technical-preview-1702#create-pfx-certificates-with-s-mime-support).

- **Ondersteuning voor extra iOS-configuratie-instellingen**
   
    U hebt nu 42 aanvullende iOS-instellingen die u als onderdeel van een configuratie-item configureren kunt. De meeste instellingen (35 in alle) zijn voor onder supervisie iOS-apparaten toegevoegd. Zie voor meer informatie [nieuwe instellingen voor naleving voor iOS-apparaten](/sccm/core/get-started/capabilities-in-technical-preview-1702#new-compliance-settings-for-ios-devices).

## <a name="january-2017"></a>Januari 2017

### <a name="new-in-microsoft-intune"></a>Nieuw in Microsoft Intune

- **Ondersteuning voor android 7.1.1**

  Intune nu volledig ondersteund en Android 7.1.1 beheert.

- **Probleem waarbij iOS-apparaten zijn niet actief of de beheerconsole niet kan communiceren met deze oplossen**

  Wanneer apparaten van gebruikers contact met Intune kwijtraken, kunt u ze nieuwe mogelijke problemen en oplossingen om u te helpen weer toegang tot bedrijfsbronnen op te geven. Zie [apparaten zijn niet actief of de beheerconsole kan niet communiceren met hen](/intune/troubleshoot/troubleshoot-device-enrollment-in-intune#devices-are-inactive-or-the-admin-console-cannot-communicate-with-them).

### <a name="new-in-configuration-manager-technical-preview-1701"></a>Nieuw in Configuration Manager Technical Preview 1701

- **Android en iOS-versies worden niet meer targetable in wizards voor hybride MDM maken**

  Vanaf Technical Preview 1701 voor hybride mobile device management (MDM) is hoeft niet langer te gericht op specifieke versies van Android en iOS bij het maken van nieuwe beleidsregels en profielen voor Intune-beheerde apparaten. Met deze wijziging kunnen hybride implementaties ondersteuning bieden sneller op nieuwe versies van Android en iOS zonder een nieuwe release van Configuration Manager of een uitbreiding. Zie voor meer informatie, [Android en iOS-versies worden niet meer in wizards voor het maken van targetable](/sccm/core/get-started/capabilities-in-technical-preview-1701#android-and-ios-versions-are-no-longer-targetable-in-creation-wizards-for-hybrid-mdm).


## <a name="notices"></a>Aankondigingen

### <a name="end-of-support-for-ios-80"></a>Einde van ondersteuning voor iOS 8.0 
<!---1164477--->
Beheerde apps en de bedrijfsportal-app voor iOS is vereist voor iOS 9.0 en hoger voor toegang tot bedrijfsbronnen. Apparaten die niet worden bijgewerkt voordat September niet langer toegang tot de bedrijfsportal of deze apps. 

### <a name="platform-support-reminder-windows-phone-81-mainstream-support-ended-july-11-2017"></a>Herinnering voor platform-ondersteuning: Algemene ondersteuning voor Windows Phone 8.1 11 juli 2017 beëindigd
<!-- 1327781 -->
*11 juli 2017*

De Windows Phone 8.1-platform is geëindigd algemeen worden ondersteund. Ondersteuning voor Windows 8.1-PC wordt niet beïnvloed.

Er zijn geen directe gevolgen op een Windows Phone 8.1-apparaat dat wordt beheerd door de Intune-service, waaronder die zijn ingeschreven in een hybride MDM Apparaten die zijn ingeschreven blijven werken en alle beleidsregels, configuraties en apps blijven werken zoals verwacht. Houd er rekening mee, er zijn geen verbeteringen die zijn bedoeld voor het Windows Phone 8.1-platform in de Intune-service en de Windows Phone 8.1-bedrijfsportal-app.

Het is raadzaam om in aanmerking komende Windows Phone 8.1-apparaten upgraden naar Windows 10 Mobile op zo snel mogelijk.  

### <a name="end-of-support-for-android-43-and-lower"></a>Einde van ondersteuning voor Android 4.3 en lager
<!---1171127--->
*Juli, 6, 2017*

Beheerde apps en de bedrijfsportal-app voor Android moeten Android 4.4 en hoger voor toegang tot bedrijfsresources. Apparaten die niet worden bijgewerkt voordat het begin van oktober niet langer toegang tot de bedrijfsportal of deze apps. Door December moeten alle ingeschreven apparaten verplicht worden gesteld in December, wat leidt tot verlies van toegang tot bedrijfsbronnen. Als u van beveiligingsbeleid app zonder MDM gebruikmaakt, apps ontvangt geen updates en de kwaliteit van hun ervaring zal afnemen.


### <a name="system-center-2012-configuration-sp1-and-system-center-2012-r2-configuration-manager-rtm-support-for-hybrid-mobile-device-management-ending-on-april-10-2017"></a>System Center 2012 Configuration SP1 en System Center 2012 R2 Configuration Manager (RTM): Ondersteuning voor hybride mobile device management eindigt op 10 April 2017
*11 januari 2017*

Ondersteuning voor System Center 2012 Configuration Manager SP1 en System Center 2012 R2 Configuration Manager RTM beëindigd op 12 juli 2016. Vervolgens kunt u ondersteuning voor deze verbinding maken met de Microsoft Intune-service voor hybride MDM op 10 April 2017 eindigt releases. Na deze datum functioneert hybride MDM deze uitgaven. Beheerde apparaten wordt in wezen worden beheerd, zoals de Intune-Connector niet meer verbinding met de Intune-service maken wordt. Configuration Manager-gegevens (zoals beleidsregels en toepassingen) niet stromen naar Intune en beheerd apparaat wordt niet gegevensstroom naar beneden op Configuration Manager totdat u een upgrade wordt uitgevoerd.

Als u een hybride implementatie met Configuration Manager 2012 SP1 of R2 RTM uitvoert, wordt u aangeraden vóór 10 April 2017 te upgraden naar Configuration Manager (huidige vertakking) of het meest recente ondersteunde servicepack voor Configuration Manager 2012 (R2 SP1 of SP2) om te voorkomen dat onderbreking van de service.

Aanvullende bronnen:
-   [Upgraden naar System Center Configuration Manager (huidige vertakking)](/sccm/core/servers/deploy/install/upgrade-to-configuration-manager)
-   [Upgrade naar System Center 2012 R2 Configuration Manager SP1](https://technet.microsoft.com/library/jj822981.aspx#BKMK_PlanningR2SP1Upgrade)
-   [Upgrade naar System Center 2012 Configuration Manager SP2](https://technet.microsoft.com/library/jj822981.aspx#BKMK_PlanningSP2Upgrade)

### <a name="windows-phone-8-company-portal-upload-deprecated"></a>Windows Phone 8-bedrijfsportal uploaden afgeschaft
*25 oktober 2016*

De mogelijkheid voor het uploaden van een ondertekende bedrijfsportal-app is verwijderd uit de Configuration Manager-console, zoals ondersteuning voor Intune wordt afgeschaft voor Windows 8, Windows Phone 8 en Windows RT en ondersteuning voor de Windows Phone 8-bedrijfsportal wordt beëindigd in November.  Windows 8, Windows Phone 8 en Windows RT-apparaten die al zijn ingeschreven wordt nog steeds ondersteund, maar de registratie van extra apparaten via deze platforms worden niet ondersteund.


### <a name="see-also"></a>Zie ook

- [Hybride MDM-functies uit het verleden](whats-new-hybrid-archive.md)
- [Wat is er nieuw voor MDM in System Center 2012 Configuration Manager](https://technet.microsoft.com/library/mt445560.aspx)
