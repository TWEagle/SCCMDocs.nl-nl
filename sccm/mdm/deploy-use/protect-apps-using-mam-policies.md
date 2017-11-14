---
title: Apps beveiligen met Mobile Application Management-beleid
titleSuffix: Configuration Manager
description: De functionaliteit aanpassen van apps die u implementeert zodat deze voldoet aan uw bedrijf nalevings- en beveiligingsbeleid.
ms.custom: na
ms.date: 03/05/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: configmgr-hybrid
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 28115475-e563-4e16-bf30-f4c9fe704754
caps.latest.revision: "18"
caps.handback.revision: "0"
author: dougeby
ms.author: dougeby
manager: angrobe
ms.openlocfilehash: 4eedd96fd399cf9577da8069bd0c8d5702f50d7b
ms.sourcegitcommit: 922d6d9c91ba2158b938df381277be1b5f1d434a
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 11/13/2017
---
# <a name="protect-apps-using-mobile-application-management-policies-in-system-center-configuration-manager"></a>Apps in System Center Configuration Manager beveiligen met Mobile Application Management-beleid

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*

System Center Configuration Manager application management-beleid kunnen u de functionaliteit aanpassen van apps die u implementeert om ervoor te zorgen dat ze in overeenstemming met uw bedrijf apparaatcompatibiliteit en beveiligingsbeleid. U kunt bijvoorbeeld knippen, kopiëren en plakken binnen een beperkte app beperken of een app configureren zodat alle URL's binnen een beheerde browser openen. Ondersteuning voor beleid voor het beheer van apps:  

-   Apparaten met Android 4 en hoger  

-   Apparaten met iOS 9 en hoger  

U kunt ook mobile Application management-beleid gebruiken om apps op apparaten die niet worden beheerd door Intune te beveiligen. Met deze nieuwe mogelijkheid kunt u mam-beleid toepassen op apps die verbinding met Office 365-services maken. Dit wordt niet ondersteund voor apps die verbinding met on-premises Exchange of SharePoint maken.  

Voor het gebruik van deze nieuwe mogelijkheid, moet u de Azure preview portal gebruiken. De volgende onderwerpen kunnen u op weg helpen:  
-   [Aan de slag met beleid voor Mobile App Management in Azure Portal](https://technet.microsoft.com/library/mt627830.aspx)  
-   [Beleid voor Mobile App Management maken en implementeren met Microsoft Intune](https://technet.microsoft.com/library/mt627829.aspx)  

 U kunt een beleid voor toepassingsbeheer niet implementeren rechtstreeks u doen met configuratie-items en basislijnen in Configuration Manager. In plaats daarvan koppelt u het beleid aan het toepassingsimplementatietype dat u wilt beperken. Wanneer het implementatietype van de app is geïmplementeerd en geïnstalleerd op apparaten, de instellingen die u opgeeft te laten treden.  

Als beperkingen wilt toepassen op een app, moet de app gebruikmaken van de Microsoft Intune App Software Development Kit (SDK). Er zijn twee methoden voor het verkrijgen van dit type app:  

-   **Een door beleid beheerde app gebruiken** (Android en iOS): Deze apps hebben de ingebouwde App SDK. Om dit type app toe te voegen, geeft u een koppeling op naar de app uit een app store zoals iTunes store of Google Play. Er is geen verdere verwerking vereist voor dit type app. Zie [Beheerde apps voor Microsoft Intune-beleid voor het beheer van mobiele toepassingen](https://technet.microsoft.com/library/dn708489.aspx) voor een lijst met door beleid beheerde apps die beschikbaar zijn voor iOS- en Android-apparaten.  

-   **Een 'verpakte' app gebruiken** (Android en iOS): Deze apps opnieuw zijn verpakt met de App-SDK met behulp van de **Microsoft Intune App Wrapping Tool**. Dit hulpprogramma wordt meestal gebruikt voor het verwerken van bedrijfsapps die intern zijn gemaakt. Het kan niet worden gebruikt voor het verwerken van apps die zijn gedownload uit de app store. Zie de volgende artikelen voor meer informatie:
    - [IOS-apps voorbereiden voor mobile application management met Microsoft Intune App Wrapping Tool](https://technet.microsoft.com/library/dn878028.aspx)

    - [Android-apps voorbereiden voor mobile application management met Microsoft Intune App Wrapping Tool](https://technet.microsoft.com/library/mt147413.aspx)  

## <a name="create-and-deploy-an-app-with-a-mobile-application-management-policy"></a>Een app maken en implementeren met Mobile Application Management-beleid  

##  <a name="step-1-obtain-the-link-to-a-policy-managed-app-or-create-a-wrapped-app"></a>Stap 1: De koppeling naar een door beleid beheerde app verkrijgen of een verpakte app maken  

-   **Haal een koppeling naar een door beleid beheerde app**: Zoek uit de appstore, en noteer de URL van het beleid beheerde app die u wilt implementeren.  

     De URL van de app Microsoft Word voor iPad is bijvoorbeeld **https://itunes.apple.com/us/app/microsoft-word-for-ipad/id586447913?mt=8**  

-   **Een verpakte app maken**: Gebruik de informatie in de onderwerpen [iOS-apps voorbereiden voor mobile application management met Microsoft Intune App Wrapping Tool](https://technet.microsoft.com/library/dn878028.aspx) en [Android-apps voorbereiden voor mobile application management met Microsoft Intune App Wrapping Tool](https://technet.microsoft.com/library/mt147413.aspx) een verpakte app maken.  

     Het hulpprogramma maakt een verwerkte app en een daaraan gekoppeld manifestbestand. U kunt deze bestanden gebruiken bij het maken van een Configuration Manager-toepassing die de app bevat.  

##  <a name="step-2-create-a-configuration-manager-application-that-contains-an-app"></a>Stap 2: Een Configuration Manager-toepassing waarin een app maken  
 De procedure voor het maken van de Configuration Manager-toepassing verschilt, afhankelijk van of u gebruikmaakt van een door beleid beheerde app (externe koppeling) of een app die is gemaakt met behulp van de Microsoft Intune App Wrapping Tool voor iOS (App-pakket voor iOS). Gebruik een van de volgende procedures om de Configuration Manager-toepassing maken.  

1.  Kies in de Configuration Manager-console **softwarebibliotheek** > **Toepassingsbeheer** > **toepassingen**.  

3.  In de **Start** tabblad, in de **maken** groep, kiest u **toepassing maken** openen de **toepassing maken** Wizard.  

4.  Selecteer op de pagina **Algemeen** de optie **Automatisch informatie over deze toepassing detecteren uit installatiebestanden**.  

5.  Selecteer **App-pakket voor iOS \*IPA-bestand) in de vervolgkeuzelijst **Type****.  

6.  Kies **Bladeren** selecteren van het app-pakket dat u wilt importeren, en kies vervolgens **volgende**.  

7.  Voer op de pagina **Algemene informatie** de beschrijvende tekst en categorie-informatie in die u voor gebruikers wilt weergeven op de bedrijfsportal.  

8.  Voltooi de wizard.  

 De nieuwe toepassing wordt weergegeven in het knooppunt **Toepassingen** van de werkruimte **Softwarebibliotheek** .  

### <a name="create-an-application-that-contains-a-link-to-a-policy-managed-app"></a>Maken van een toepassing met een koppeling naar een door beleid beheerde app  

1.  Kies in de Configuration Manager-console **softwarebibliotheek** > **Toepassingsbeheer** > **toepassingen**.  

3.  In de **Start** tabblad, in de **maken** groep, kiest u **toepassing maken** openen de **toepassing maken** Wizard.  

4.  Selecteer op de pagina **Algemeen** de optie **Automatisch informatie over deze toepassing detecteren uit installatiebestanden**.  

5.  Selecteer in de vervolgkeuzelijst **Type** een van de volgende opties:  

    -   Voor iOS: **App-pakket voor iOS uit de App Store**  

    -   Voor Android: **App-pakket voor Android in Google Play**  

6.  Voer de URL voor de app (uit stap 1) en kies vervolgens **volgende**.  

7.  Voer op de pagina **Algemene informatie** de beschrijvende tekst en categorie-informatie in die u voor gebruikers wilt weergeven op de bedrijfsportal.  

8.  Voltooi de wizard.  

 De nieuwe toepassing wordt weergegeven in het knooppunt **Toepassingen** van de werkruimte **Softwarebibliotheek** .  

##  <a name="step-3-create-an-application-management-policy"></a>Stap 3: Een beleid voor toepassingsbeheer maken  
 Maak vervolgens een beleid voor toepassingsbeheer dat u aan de toepassing koppelt. U kunt een algemeen beleid of Managed Browser-beleid maken.  

1)  Kies in de Configuration Manager-console **softwarebibliotheek** > **Toepassingsbeheer** > **Application Management-beleid**.  

2)  In de **Start** tabblad, in de **maken** groep, kiest u **beleid voor toepassingsbeheer maken**.  

3)  Op de **algemene** pagina, voer de naam en beschrijving voor het beleid en kies vervolgens **volgende**.  

4)  Op de **beleidstype** pagina, selecteer het platform en beleidstype voor dit beleid en kies vervolgens **volgende**. U kunt uit de volgende beleidstypen kiezen:  

-   **Algemene**: Het beleidstype algemeen kunt u de functionaliteit van apps die u implementeert om ervoor te zorgen dat ze in overeenstemming met uw bedrijf nalevings- en beveiligingsbeleid wijzigen. U kunt bijvoorbeeld bewerkingen zoals knippen, kopiëren en plakken binnen een beperkte app beperken.  

-   **Managed Browser**: De Managed Browser-beleid kunt u beslissen of u wilt toestaan of blokkeren van de beheerde browser een lijst met URL's opent. Met het beleidstype Managed Browser kunt u de functionaliteit van de Intune Managed Browser-app wijzigen. Dit is een browser waarmee u de acties die gebruikers kunnen uitvoeren, kunt beheren, met inbegrip van de websites die ze kunnen bezoeken en de manier waarop koppelingen naar inhoud in de browser worden geopend. Meer informatie over de  [Intune Managed Browser-app voor iOS](https://itunes.apple.com/us/app/microsoft-intune-managed-browser/id943264951?mt=8) en de [Intune Managed Browser-app voor Android](https://play.google.com/store/apps/details?id=com.microsoft.intune.mam.managedbrowser&hl=en).

5)  Op de **iOS-beleid** of **Android-beleid** pagina, configureer de volgende waarden zoals vereist en kies vervolgens **volgende**. De opties kunnen variëren, afhankelijk van het apparaattype waarvoor u het beleid configureert.  

|Waarde|Meer informatie|  
|-----------|----------------------|  
|**Webinhoud beperken en weergeven in een bedrijfsbeheerde browser**|Hiermee kunt alle koppelingen in de app wordt geopend in de Managed Browser. Deze optie werkt alleen als u deze app hebt geïmplementeerd op apparaten.|  
|**Back-ups van Android verhinderen** of **Back-ups van iTunes en iCloud verhinderen**|Hiermee worden back-ups van gegevens uit de app uitgeschakeld.|  
|**App mag gegevens overdragen naar ander apps**|Hiermee geeft u de apps aan waarnaar deze app gegevens kan verzenden. U kunt kiezen om geen gegevensoverdracht naar Apps, alleen overdracht naar andere beperkte apps toestaat, toe te staan of overdracht naar alle Apps.<br /><br /> Om bij iOS-apparaten documentoverdracht tussen beheerde en onbeheerde apps te voorkomen, moet u ook een beveiligingsbeleid voor mobiele apparaten configureren en implementeren, waarmee de instelling **Beheerde documenten toestaan in andere onbeheerde apps**wordt uitgeschakeld.<br /><br /> Als u selecteert alleen overdracht naar andere beperkte apps toestaat, worden de Intune PDF- en afbeeldingsviewers (indien geïmplementeerd) gebruikt om inhoud van de verschillende typen te openen.|  
|**App mag gegevens ontvangen van andere apps**|Hiermee geeft u de apps op waarvan deze app gegevens mag ontvangen. U kunt kiezen om geen gegevensoverdracht vanuit alle Apps toe te staan dat overdracht vanaf andere beperkte apps toe te staan of overdracht vanaf alle Apps.|  
|**Opslaan als verhinderen**|Hiermee schakelt u het gebruik van de **OpslaanAls** optie in elke app die gebruikmaakt van dit beleid.|  
|**Knippen, kopiëren en plakken met andere apps beperken**|Hiermee geeft u op hoe knip-, kopieer- en plakbewerkingen kunnen worden gebruikt met de app. U kunt kiezen uit:<br /><br /> **Geblokkeerd** – mag geen knip-, kopieer- en plakbewerkingen tussen deze app en andere apps.<br /><br /> **Beleid beheerde Apps** – Hiermee kunt u knippen, kopiëren en plakken tussen alleen deze app en andere beperkte apps.<br /><br /> **Beleid beheerde Apps met plakken In** – maakt het mogelijk gegevens dat is geknipt of gekopieerd uit deze app worden geplakt in andere beperkte apps. Hiermee kunt gegevens die worden geknipt of gekopieerd uit alle apps in deze app worden geplakt.<br /><br /> **Elke App** : geen beperkingen aan knip-, kopieer- en plakbewerkingen naar of vanuit deze app.|  
|**Eenvoudige pincode vereist voor toegang**|De gebruiker een pincode die zij opgeven voor het gebruik van deze app vereist. De gebruiker wordt gevraagd om in te stellen dat dit de eerste keer dat de app uitvoert.|  
|**Aantal pogingen voordat pincode opnieuw wordt ingesteld**|Hiermee geeft u het aantal invoerpogingen PINCODE die kunnen worden uitgevoerd voordat de gebruiker de PINCODE opnieuw moet instellen.|  
|**Bedrijfsreferenties vereisen voor toegang**|Vereist dat gebruikers hun zakelijke gegevens aanmelden invoeren moeten voordat ze toegang heeft tot de app.|  
|**Apparaatcompatibiliteit met bedrijfsbeleid vereisen voor toegang**|Kan de app moet worden gebruikt wanneer het apparaat niet opengebroken is of geroot.|  
|**Toegangsvereisten opnieuw controleren na (minuten)**|Hiermee geeft u de tijdsperiode op waarna de toegangsvereisten voor de app opnieuw worden gecontroleerd nadat de app wordt gestart (in de **time-out** veld).<br /><br /> In de **Offline respijtperiode** veld als het apparaat offline is, geeft u de tijdsperiode op waarna de toegangsvereisten voor de app opnieuw worden gecontroleerd.|  
|**Appgegevens versleutelen**|Hiermee geeft u op dat alle gegevens die is gekoppeld aan deze app worden versleuteld, met inbegrip van gegevens die extern, zoals gegevens die zijn opgeslagen op de SD-kaarten zijn opgeslagen.<br /><br /> **Versleuteling voor iOS**<br /><br /> Voor apps die gekoppeld aan een mobile application management-beleid van Configuration Manager zijn, worden de gegevens versleuteld in rust met behulp van versleuteling op apparaatniveau die wordt geleverd door het besturingssysteem. Dit wordt ingeschakeld via apparaatpincodebeleid dat moet worden ingesteld door de IT-beheerder. Als een PINCODE vereist is, wordt de gegevens versleuteld volgens de instellingen in het mobile application management-beleid. Zoals vermeld in de Apple-documentatie [de modules die worden gebruikt door iOS 7 zijn FIPS 140-2 gecertificeerd](http://support.apple.com/en-us/HT202739).<br /><br /> **Versleuteling voor Android**<br /><br /> Voor apps die gekoppeld aan een mobile application management-beleid van Configuration Manager zijn, wordt versleuteling geleverd door Microsoft. Gegevens worden synchroon versleuteld tijdens bestands-I/O-bewerkingen overeenkomstig de instelling in het Mobile Application Management-beleid. Beheerde apps op Android gebruiken AES-128-versleuteling in CBC-modus waarbij de cryptografiebibliotheken van het platform worden gebruikt. De versleutelingsmethode is niet gecertificeerd volgens FIPS 140-2. Inhoud in de apparaatopslag wordt altijd versleuteld.|  
    |**Schermafbeelding blokkeren** (alleen Android-apparaten)|Hiermee wordt opgegeven dat de schermafbeeldingsmogelijkheden van het apparaat zijn geblokkeerd bij gebruik van deze app.|  

6)  Op de **Managed Browser** pagina, selecteert u of de beheerde browser mag alleen URL's openen in de lijst of de beheerde browser openen van URL's in de lijst en kies vervolgens **volgende**.  
Zie voor meer informatie [internettoegang beheren met beheerde-browserbeleid](manage-internet-access-using-managed-browser-policies.md).  

7)  Voltooi de wizard.  

 Het nieuwe beleid wordt weergegeven in het knooppunt **Beleid voor toepassingsbeheer** van de werkruimte **Softwarebibliotheek** .  

##  <a name="step-4-associate-the-application-management-policy-with-a-deployment-type"></a>Stap 4: Beleid voor toepassingsbeheer koppelen aan een implementatietype  

 Wanneer een implementatietype is gemaakt voor een app waarvoor beleid voor toepassingsbeheer is vereist, wordt Configuration Manager herkent dit en krijgt u een app management-beleid te koppelen. U moet de beheerde browser zowel een algemeen beleid als Managed Browser beleid koppelen. Zie voor meer informatie [toepassingen maken](create-applications.md).  

> [!IMPORTANT]  
>  Als de toepassing al is geïmplementeerd, mislukt de implementatie van het nieuwe implementatietype totdat deze koppeling wordt gemaakt. U kunt op het tabblad **Toepassingsbeheer** de koppeling aanbrengen in **Eigenschappen** voor de toepassing.  

> [!IMPORTANT]  
>  Voor apparaten met besturingssystemen ouder dan iOS 7.1, worden de bijbehorende beleid worden niet verwijderd wanneer de app wordt verwijderd.  
>   
>  Als het apparaat wordt uitgeschreven uit Configuration Manager, het beleid niet verwijderd uit de apps. Apps waarop beleid werd toegepast, behouden de beleidsinstellingen zelfs nadat de app is verwijderd en opnieuw geïnstalleerd.  

##  <a name="step-5-monitor-the-app-deployment"></a>Stap 5: Controleer de implementatie van de app  
 Zodra u hebt gemaakt en een app die is gekoppeld aan een mobile application management-beleid hebt geïmplementeerd, kunt u de app bewaken en eventuele beleidsconflicten oplossen.  

1.  Kies in de Configuration Manager-console **softwarebibliotheek** > **overzicht** > **implementaties**.  

3.  Selecteer de implementatie die u hebt gemaakt. Klik op de **Start** Kies **eigenschappen**.  

4.  In het detailvenster voor de implementatie onder **verwante objecten**, kies **Application Management-beleid**.  

 Zie voor meer informatie over het bewaken van toepassingen [toepassingen bewaken](/sccm/apps/deploy-use/monitor-applications-from-the-console).  

##  <a name="learn-how-policy-conflicts-are-resolved"></a>Meer informatie over hoe beleidsconflicten worden opgelost  
 Wanneer er een conflict met mobile application management-beleid op de eerste implementatie voor de gebruiker of apparaat, wordt de specifieke instelling-waarde die in conflict is verwijderd uit het beleid dat is geïmplementeerd voor de app. Vervolgens gebruikt de app een ingebouwde conflictwaarde.  

 Wanneer er een conflict met mobile Application management-beleid bij latere implementaties naar de app of gebruiker, de specifieke instelling-waarde die in conflict is niet bijgewerkt op de mam-beleid dat is geïmplementeerd voor de app en de app gebruikt de bestaande waarde voor die instelling.  

 In gevallen waarin het apparaat of de gebruiker twee conflicterende sets beleidsregels ontvangt, is het volgende van toepassing:  

-   Als op het apparaat nog een beleid is geïmplementeerd, worden de bestaande beleidsinstellingen niet overschreven.  

-   Als er geen beleid is al is geïmplementeerd op het apparaat en twee conflicterende instellingen zijn geïmplementeerd, is de standaardinstelling die ingebouwd in het apparaat wordt gebruikt.  

##  <a name="see-a-list-of-available-policy-managed-apps"></a>Een lijst met beschikbare door beleid beheerde apps  
 Zie voor een lijst met door beleid beheerde apps die beschikbaar zijn voor iOS en Android-apparaten [Microsoft Intune-toepassingspartners](https://www.microsoft.com/cloud-platform/microsoft-intune-partners).  
