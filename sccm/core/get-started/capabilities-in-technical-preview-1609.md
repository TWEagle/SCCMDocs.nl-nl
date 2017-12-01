---
title: Mogelijkheden van Technical Preview 1609
titleSuffix: Configuration Manager
description: Meer informatie over functies die beschikbaar zijn in de Technical Preview voor System Center Configuration Manager, versie 1609.
ms.custom: na
ms.date: 01/23/2017
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.prod: configuration-manager
ms.technology: configmgr-other
ms.topic: article
ms.assetid: e2a59116-b2e5-4dd2-90eb-0b8a5eb50b56
caps.latest.revision: "2"
author: erikje
ms.author: erikje
manager: angrobe
ms.openlocfilehash: e1cceae5f73d003be2fe64df9e6dbaa7badaf0c7
ms.sourcegitcommit: 7fe45ff75f05f7cc03ad021db8119791abe18049
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/01/2017
---
# <a name="capabilities-in-technical-preview-1609-for-system-center-configuration-manager"></a>Mogelijkheden van Technical Preview 1609 voor System Center Configuration Manager

*Van toepassing op: System Center Configuration Manager (Technical Preview)*



Dit artikel bevat de functies die beschikbaar in de Technical Preview voor System Center Configuration Manager, versie 1609 zijn. U kunt deze versie om te werken en nieuwe mogelijkheden toevoegen aan uw Configuration Manager technical preview-site installeren.      Controleer voordat u deze versie van de technical preview installeert, de inleidende informatie [Technical Preview voor System Center Configuration Manager](../../core/get-started/technical-preview.md), om vertrouwd te raken met algemene vereisten en beperkingen voor het gebruik van een technical preview hoe bijwerken tussen versies en hoe u feedback over de functies in een technical preview.    

**Bekende problemen in deze Technical Preview:**  
*  Wanneer u naar de Configuration Manager 1609 Technical Preview bijwerkt, kunt u elke editie-Upgradebeleid die u hebt geïmplementeerd wordt verwijderd. Als u wilt blijven gebruiken van deze beleidsregels, moet u opnieuw te maken en implementeren.


**Hier volgen nieuwe functies die u met deze versie kunt uitproberen.**  

## <a name="improvements-to-endpoint-protection"></a>Verbeteringen in Endpoint Protection
Verbetering van de instellingen voor het antimalwarebeleid Endpoint Protection - u kunt nu het niveau waarop de Endpoint Protection Cloud Protection-Service verdachte bestanden blokkeert opgeven. Een nieuwe instelling kan beheerders opgeven "riskant" computers op basis van de hoge hoeveelheden malware optreden.

## <a name="increased-number-of-enrolled-devices"></a>Toenemend aantal geregistreerde apparaten
Nu kunnen beheerders gebruikers inschrijven maximaal 15 apparaten in hybride mobile device management met Intune inschakelen. De limiet is eerder 5 apparaten per gebruiker.

## <a name="additional-apple-dep-settings"></a>Aanvullende Apple DEP-instellingen

Beheerders kunnen nu de volgende Apple Device Enrollment Program (DEP)-instellingen configureren in het DEP-profiel voor iOS en Mac-apparaten.
- **Touch ID**
- **Uitzoomen**
- **Siri**

Bij inschakeling van Apple Configuratieassistent wordt gevraagd voor deze service tijdens de activering van het apparaat.

## <a name="integration-with-upgrade-analytics"></a>Integratie met de Upgrade Analytics

Upgrade analytics kunt u om te beoordelen en analyseren van de gereedheid van het apparaat en compatibiliteit met Windows 10, zodat u gemakkelijker en soepeler upgrades. Met de Upgrade Analytics met Configuration Manager-integratie kunt u toegang tot de upgradecompatibiliteit gegevens in de beheerconsole van Configuration Manager en vervolgens uit de lijst met apparaten doelapparaten voor herstel of upgrade.

Meer informatie over Upgrade Analytics in [aan de slag met de Upgrade Analytics](https://technet.microsoft.com/itpro/windows/deploy/upgrade-analytics-get-started).

## <a name="native-connection-types-for-windows-10-vpn-hybrid-profiles"></a>Systeemeigen verbindingstypen voor Windows 10 hybride VPN-profielen

Als u Configuration Manager met Intune, kunt u nu Windows 10 VPN-profielen maken met Microsoft Automatic, IKEv2, PPTP- en L2TP verbindingstypen in de Configuration Manager-console zonder met OMA-URI.

## <a name="enhancements-to-windows-store-for-business-integration-with-configuration-manager"></a>Verbeteringen in Windows Store voor bedrijven-integratie met Configuration Manager

In deze versie bijgewerkt [Windows Store voor bedrijven-integratie](/sccm/apps/deploy-use/manage-apps-from-the-windows-store-for-business) met deze nieuwe functies:

**Update:** De functie directe synchronisatie is niet functioneel in de huidige technical preview-versie.

- Eerder kon u alleen gratis apps uit de Windows Store voor bedrijven implementeren. Configuration Manager nu bovendien ondersteunt de implementatie van betaald online gelicentieerde apps (voor Intune ingeschreven apparaten).
- U kunt nu een directe synchronisatie tussen de Windows Store voor bedrijven en Configuration Manager initiëren.
- U kunt nu de client geheime sleutel die u hebt verkregen via Azure Active Directory wijzigen

### <a name="try-it-out"></a>Probeer het nu!

#### <a name="purchase-and-sync-a-paid-online-licensed-app"></a>Koopt en een betaald online gelicentieerde Apps synchroniseren

1. Schaf een betaald online gelicentieerde Apps uit de Windows Store voor bedrijven.
2. In de **beheer** werkruimte van de Configuration Manager-console, klikt u op **Cloudservices** > **Updates en onderhoud** > **Windows Store voor bedrijven**.
3. Op de **Start** tabblad, in de **Sync** groep, klikt u op **nu synchroniseren**.
4. Snel daarna verschijnt de app die u hebt aangeschaft in de **licentiegegevens voor Store-Apps** knooppunt van de **Toepassingsbeheer** werkruimte.

#### <a name="create-and-deploy-a-configuration-manager-application-from-the-synchronized-app-data"></a>Maken en implementeren van een Configuration Manager-toepassing van de gesynchroniseerde app-gegevens

De procedure voor het maken en implementeren van een Configuration Manager-toepassing van een betaald store-app is hetzelfde als voor het maken van een toepassing van een gratis app. Zie de sectie **maken en implementeren van een Configuration Manager-toepassing in een Windows Store voor bedrijven-app** in [apps beheren via de Windows Store voor bedrijven met System Center Configuration Manager](/sccm/apps/deploy-use/manage-apps-from-the-windows-store-for-business).


#### <a name="modify-the-client-secret-key-from-azure-active-directory"></a>De geheime sleutel van de client van Azure Active Directory wijzigen

1. In de **beheer** werkruimte van de Configuration Manager-console, klikt u op **Cloudservices** > **Updates en onderhoud** > **Windows Store voor bedrijven**.
2. Selecteer uw Windows Store voor bedrijven-account en klik vervolgens op **eigenschappen**.
3. In de **Windows Store voor bedrijven accounteigenschappen** dialoogvenster Voer een nieuwe sleutel in de **geheime sleutel van de Client** veld en klik vervolgens op **controleren**. Zodra gecontroleerd, klikt u op **toepassen**, sluit het dialoogvenster.


## <a name="new-compliance-settings-for-configuration-items"></a>Nieuwe instellingen voor naleving voor configuratie-items

Veel nieuwe instellingen die kunt u in uw configuratie-items voor verschillende platforms toegevoegd.
Dit zijn de instellingen die eerder beschikbaar waren in Microsoft Intune in een zelfstandige configuratie en zijn nu beschikbaar wanneer u Intune met Configuration Manager.
Als u hulp nodig met een van deze instellingen, open [instellingen en functies op uw apparaten met Microsoft Intune-beleid beheren](https://docs.microsoft.com/en-us/intune/deploy-use/manage-settings-and-features-on-your-devices-with-microsoft-intune-policies) en selecteer vervolgens het onderwerp van de instellingen voor het platform dat u wilt.


### <a name="new-settings-for-android-devices"></a>Nieuwe instellingen voor Android-apparaten

#### <a name="password-settings"></a>Wachtwoordinstellingen

- **Wachtwoordgeschiedenis onthouden**
- **Vingerafdruk toestaan ontgrendelen**

#### <a name="security-settings"></a>Beveiligingsinstellingen

- **Versleuteling vereisen op opslagkaarten**
- **Schermafbeelding toestaan**
- **Verzending van diagnostische gegevens toestaan**

#### <a name="browser-settings"></a>Browserinstellingen

- **Webbrowser toestaan**
- **Automatisch invullen toestaan**
- **Pop-upblokkering toestaan**
- **Cookies toestaan**
- **Active scripting toestaan**

#### <a name="app-settings"></a>App-instellingen

- **Google Play store toestaan**

#### <a name="device-capability-settings"></a>Instellingen voor apparaatfuncties

- **Verwisselbare opslag toestaan**
- **Wi-Fi-tethering toestaan**
- **Geolocatie toestaan**
- **NFC toestaan**
- **Bluetooth toestaan**
- **Spraakroaming toestaan**
- **Gegevensroaming toestaan**
- **SMS-en MMS-berichten toestaan**
- **Spraakassistent toestaan**
- **Nummer inspreken toestaan**
- **Kopiëren en plakken toestaan**


### <a name="new-settings-for-ios-devices"></a>Nieuwe instellingen voor iOS-apparaten

#### <a name="password-settings"></a>Wachtwoordinstellingen

- **Aantal complexe tekens vereist in wachtwoord**
- **Eenvoudige wachtwoorden toestaan**
- **Minuten van inactiviteit voordat wachtwoord vereist is**
- **Wachtwoordgeschiedenis onthouden**

### <a name="new-settings-for-mac-os-x-devices"></a>Nieuwe instellingen voor Mac OS X-apparaten

#### <a name="password-settings"></a>Wachtwoordinstellingen

- **Aantal complexe tekens vereist in wachtwoord**
- **Eenvoudige wachtwoorden toestaan**
- **Wachtwoordgeschiedenis onthouden**
- **Minuten van inactiviteit voordat de screensaver wordt geactiveerd**

### <a name="new-settings-for-windows-10-desktop-and-mobile-devices"></a>Nieuwe instellingen voor Windows 10 Desktop en Mobile-apparaten

#### <a name="password-settings"></a>Wachtwoordinstellingen

- **Minimum aantal tekensets**
- **Wachtwoordgeschiedenis onthouden**
- **Wachtwoord vereisen wanneer het apparaat wordt geactiveerd vanuit een niet-actieve status**

#### <a name="security-settings"></a>Beveiligingsinstellingen

- **Versleuteling vereisen op mobiele apparaten**
- **Handmatige uitschrijving toestaan**

#### <a name="device-capability-settings"></a>Instellingen voor apparaatfuncties

- **VPN via mobiele verbinding toestaan**
- **VPN-roaming via mobiele verbinding toestaan**
- **Opnieuw instellen van telefoon toestaan**
- **USB-verbinding toestaan**
- **Cortana toestaan**
- **Meldingen van Onderhoudscentrum toestaan**

### <a name="new-settings-for-windows-10-team-devices"></a>Nieuwe instellingen voor Windows 10 Team-apparaten

#### <a name="device-settings"></a>Instellingen voor apparaten

- **Operationeel inzicht van Azure inschakelen**
- **Draadloze Miracast-projectie inschakelen**
- **Kiezen welke vergaderingsinformatie wordt weergegeven op het welkomstscherm**
- **URL naar de achtergrondafbeelding van het Vergrendelingsscherm**


### <a name="new-settings-for-windows-81-devices"></a>Nieuwe instellingen voor Windows 8.1-apparaten

#### <a name="applicability-settings"></a>Toepasselijkheidsinstellingen

- **Alle configuraties toepassen op Windows 10**

#### <a name="password-settings"></a>Wachtwoordinstellingen

- **Vereist Wachtwoordtype**
- **Minimum aantal tekensets**
- **Minimale wachtwoordlengte**
- **Aantal herhaalde, mislukte aanmeldingen dat is toegestaan voordat het apparaat wordt gewist**
- **Minuten van inactiviteit voordat het scherm wordt uitgeschakeld**
- **Wachtwoord verloopt (dagen)**
- **Wachtwoordgeschiedenis onthouden**
- **Hergebruik van wachtwoorden voorkomen**
- **Afbeeldingswachtwoord en PIN toestaan**

#### <a name="browser-settings"></a>Browserinstellingen

- **Automatische detectie van intranetnetwerk toestaan**


### <a name="new-settings-for-windows-phone-81-devices"></a>Nieuwe instellingen voor Windows Phone 8.1-apparaten

#### <a name="applicability-settings"></a>Toepasselijkheidsinstellingen

- **Alle configuraties toepassen op Windows 10**

#### <a name="password-settings"></a>Wachtwoordinstellingen

- **Minimum aantal tekensets**
- **Eenvoudige wachtwoorden toestaan**
- **Wachtwoordgeschiedenis onthouden**

#### <a name="device-capability-settings"></a>Instellingen voor apparaatfuncties

- **Automatische verbinding met gratis Wi-Fi-hotspots toestaan**


## <a name="improvements-for-boundary-groups"></a>Verbeteringen voor grensgroepen
Deze preview introduceert belangrijke wijzigingen aan grensgroepen en hoe deze werken met distributiepunten. Deze wijzigingen wordt het ontwerp van uw inhoudsinfrastructuur vereenvoudigen tijdens zodat u meer controle over hoe en wanneer clients terugvallen op extra distributiepunten zoeken als inhoudsbron locaties verwijst. Dit omvat zowel on-premises en cloud-gebaseerde distributiepunten.

Deze verbeteringen vervangen concepten en gedrag bekend met bent vandaag de dag (zoals het configureren van distributiepunten als snel of traag) en ze vervangen door een nieuw model moet zijn gemakkelijker te configureren en te onderhouden. Deze wijzigingen zijn ook als basis voor toekomstige wijzigingen die andere sitesysteemrollen die u aan grensgroepen koppelen verbeteren.  

Tijdens de upgrade naar 1609, converteert de upgrade uw huidige configuratie van grensgroepen voor het nieuwe model passen zodat deze wijzigingen niet de configuraties voor de distributie van inhoud storen (Zie [bestaande grensgroepen bijwerken naar het nieuwe model](/sccm/core/get-started/capabilities-in-technical-preview-1609#bkmk_update)).

De volgende secties detailleren de wijzigingen die zijn geïntroduceerd in dit voorbeeld, hoe het nieuwe model werkt en wat u kunt verwachten bij een upgrade van een site die al geconfigureerd grensgroepen is.



### <a name="changes-in-ui-and-behavior-for-boundary-groups-and-content-locations"></a>Wijzigingen in de gebruikersinterface en het gedrag voor grensgroepen en inhoudslocaties
Hieronder vindt u belangrijke wijzigingen in grensgroepen en hoe clients inhoud vinden. Veel van deze wijzigingen en concepten werken samen.
-   **Configuraties voor het snel of traag worden verwijderd:** U configureert niet langer afzonderlijke distributiepunten worden snel of traag.  In plaats daarvan elk sitesysteem die zijn gekoppeld aan een grensgroep wordt behandeld hetzelfde. Vanwege deze wijziging de **verwijzingen** tabblad van de eigenschappen van de grensgroep biedt geen ondersteuning voor de configuratie van snel of traag.
-   **Nieuwe standaard grensgroep op elke site:**  Elke primaire site heeft een nieuwe grensgroep standaard is met de naam ***-Site-grens-standaardgroep\<sitecode >***.  Wanneer een client zich niet op een netwerklocatie bevindt die is toegewezen aan een grensgroep, wordt die client de sitesystemen die zijn gekoppeld aan de standaardgroep van de toegewezen site gebruiken. Wilt u deze grensgroep gebruiken als ter vervanging van het concept van locatie terugvalinhoudlocatie.    
 -  **'Alternatieve bronlocaties voor inhoud toestaan'** wordt verwijderd: U configureert niet langer expliciet een distributiepunt moet worden gebruikt voor terugval en de opties in te stellen dat deze worden verwijderd uit de gebruikersinterface.

    Daarnaast het resultaat van de instelling **clients met een terugvalbronlocatie voor inhoud toestaan** op een implementatie van het type voor toepassingen is gewijzigd. Deze instelling op een implementatietype kan een client de standaard sitegrensgroep gebruiken als bronlocatie voor inhoud.

 -  **Grens groepen relaties:** Elke grensgroep kan worden gekoppeld aan een of meer extra grensgroepen. Deze koppelingen vormen relaties die zijn geconfigureerd op het nieuwe grens groep tabblad Eigenschappen met de naam **relaties**:
    -   Elke grensgroep die een client rechtstreeks is gekoppeld, heet een **huidige** grensgroep.  
    -   Elke grensgroep een client kan gebruiken als gevolg van een koppeling tussen die client *huidige* grensgroep en een andere groep, heet een **neighbor** grensgroep.
    -  Deze zich op de **relaties** tabblad die u grensgroepen die kunnen worden gebruikt toevoegt als een *neighbor* grensgroep. U kunt ook een tijd in minuten die bepaalt wanneer een client die niet kunnen vinden van inhoud vanaf een distributiepunt in de *huidige* begint om te zoeken naar inhoud locaties van die groep *neighbor* grensgroepen.

        Wanneer u toevoegen of wijzigen van de configuratie van een grensgroep, hebt u de mogelijkheid om te blokkeren fallback naar specifieke grensgroep uit de huidige groep die u configureert.

    Expliciete koppelingen (koppelingen) uit een grensgroep naar een andere definiëren voor het gebruik van de nieuwe configuratie, en alle distributiepunten configureren in de bijbehorende groep met de dezelfde periode in minuten. De tijd die u configureert, bepaalt wanneer een client die niet kunnen vinden van een bron van de inhoud van de *huidige* grensgroep kunt beginnen met zoeken naar inhoudsbronnen van neighbor van de grensgroep.

    Naast de grensgroepen die expliciet configureren, heeft elke grensgroep een impliciete koppeling aan de standaardgroep voor de site-grens. Deze koppeling wordt na 120 minuten op dat moment wordt de standaardgroep voor de site-grens van een neighbor grensgroep waarmee de clients gebruiken de distributiepunten die zijn gekoppeld aan de grensgroep als inhoudsbron locaties actief.

    Dit gedrag vervangt wat eerder werd aangeduid als terugval voor inhoud.  U kunt dit standaardgedrag van 120 minuten overschrijven expliciet koppelen van de grensgroep voor standaard site naar een *huidige* groep, en het instellen van een bepaalde tijd in minuten of terugval blokkeren volledig om te voorkomen dat het gebruik ervan.


-   **Clients proberen inhoud op te halen van elk distributiepunt maximaal 2 minuten:** Wanneer een client zoekt naar een inhoudsbronlocatie, probeert het toegang krijgen tot elk distributiepunt voor 2 minuten voordat u vervolgens probeert een ander distributiepunt. Dit is een wijziging ten opzichte van vorige versies waar clients heeft geprobeerd verbinding maken met een distributiepunt voor maximaal twee uur.

    - Het eerste distributiepunt dat een client probeert te gebruiken is willekeurig geselecteerd uit de groep met beschikbare distributiepunten in de client *huidige* grensgroep (of groepen).

    - Na twee minuten als de client niet voor de inhoud gevonden is het verandert in een nieuw distributiepunt en probeert inhoud op te halen van die server. Dit proces wordt herhaald voor elke twee minuten totdat de client de inhoud wordt gevonden of de laatste server in de groep van toepassingen is bereikt.

    - Als een client kan geen geldige inhoudsbronlocatie van vinden de *huidige* van toepassingen voordat u de periode voor terugvallen op een *neighbor* grensgroep is bereikt, de client worden de distributiepunten uit de die *neighbor* groeperen met het einde van de huidige lijst en zoek vervolgens de uitgevouwen groep bronlocaties die de distributiepunten van beide grensgroepen bevat.

        > [!TIP]  
        > Wanneer u een expliciete koppeling te van de huidige grensgroep aan de standaardgroep voor de grens van site maken en een fallback-tijd die kleiner is dan de terugval tijd voor een koppeling naar een grensgroep neighbor definiëren, beginnen clients bronlocaties uit de grensgroep standaard site voordat de groep neighbor zoeken.

    - Wanneer de client niet kan inhoud op te halen van de laatste server in de groep, begint het proces opnieuw.


### <a name="how-the-new-model-works"></a>De werking van het nieuwe model
Wanneer u grensgroepen configureert, koppelt u grenzen (netwerklocaties) en sitesysteemrollen, zoals distributiepunten aan de grensgroep. Dit helpt koppeling clients sitesysteemservers zoals distributiepunten die zich bevinden in de buurt van de clients op het netwerk.   
-   U kunt dezelfde grens toewijzen aan meerdere grensgroepen
-   Sitesysteemservers, zoals distributiepunten, kunnen worden gekoppeld aan meerdere grensgroepen, zodat ze beschikbaar zijn voor een breed scala aan netwerklocaties
-   Als een distributiepunt niet gekoppeld aan een grensgroep is, kunnen clients zich niet dat distributiepunt als bronlocatie voor inhoud gebruiken.

Vanaf deze technical preview kunt definiëren u grens groepsrelaties om terugval gedrag voor inhoudsbron locaties te configureren. Hierdoor is geconfigureerd op de nieuwe **relaties** tabblad van de eigenschappen van grensgroep en vervangt sitesystemen zo langzaam en snelle configureren en het configureren van een grensgroep zodat terugvalbronlocatie voor inhoud.

Op het tabblad relaties kunt u andere grensgroepen voor het configureren van een relatie aan deze groepen toevoegen. Elke relatie is een eenzijdige koppeling van de **huidige** grensgroep toe aan de grensgroep u toevoegt, die is aangeroepen een **neighbor**. Voor elke koppeling die u maakt, kunt u distributiepunten configureren met een fallback tijd in minuten. Deze tijd wordt gebruikt om te bepalen na hoe lang clients in de *huidige* grensgroep kunt gaan gebruiken distributiepunten in de *neighbor* grensgroep als ze niet kunnen vinden van de locatie van een geldige inhoudsbron uit hun huidige grensgroep.

Wanneer een client kan geen inhoud vinden en begint met zoeken naar de locaties van neighbor grensgroepen, neemt de groep met beschikbare distributiepunten voor dat de client op een gecontroleerde manier.  

-   Een grensgroep kan meer dan één relatie hebben. Hiermee kunt u configureren terugval naar andere neighbors na verschillende perioden.
-   Clients worden alleen terugval aan een grensgroep die is een directe neighbor van hun huidige grensgroep.
-   Wanneer een client lid is van meerdere grensgroepen, wordt de huidige grensgroep gedefinieerd als een samenvoeging van die grensgroepen van de client.  Client kan vervolgens terugvallen op een neighbor van elk van de oorspronkelijke grensgroepen.

Er is een impliciete koppeling die automatisch wordt gemaakt tussen de grensgroepen die u maakt en de standaard grensgroep die automatisch wordt gemaakt voor elke site naast de koppelingen die u definieert. Deze automatische koppeling:
-   Wordt gebruikt door clients die zijn niet op een grens die automatisch zijn gekoppeld aan elke grensgroep in uw hiërarchie gebruiken de standaard grensgroep van hun toegewezen site om geldige inhoudsbron locaties te identificeren.   
-   Is een standaard terugvaloptie uit de huidige grensgroep toe aan de grensgroep voor sites standaard die wordt gebruikt na 120 minuten.

**Voorbeeld van het gebruik van het nieuwe model:**     
U maakt drie grensgroepen die geen grenzen of sitesysteemservers delen:
-   Groep BG_A met distributiepunten DP_A1 en DP_A2 die zijn gekoppeld aan de groep
-   Groep BG_B met distributiepunten DP_B1 en DP_B2 die zijn gekoppeld aan de groep
-   Groep BG_C met distributiepunten DP_C1 en DP_C2 die zijn gekoppeld aan de groep

U de netwerklocaties van uw clients toevoegen als grenzen alleen de grensgroep BG_A, en u vervolgens relaties uit die grensgroep aan de andere twee grensgroepen configureren:
-   Configureren van distributiepunten voor de eerste *neighbor* groep (BG_B) moet worden gebruikt na 10 minuten. Deze groep bevat distributiepunten DP_B1 en DP_B2. Beide zijn goed verbonden zijn met de eerste groepen grenslocaties.
-   Configureren van de tweede *neighbor* groep (BG_C) moet worden gebruikt na 20 minuten. Deze groep bevat distributiepunten DP_C1 en DP_C2. Beide zijn via een WAN van de andere twee grensgroepen.
-   U ook toevoegen een extra distributiepunt dat zich bevindt op de siteserver aan de grensgroep sites standaard site. Dit is de locatie van de minste voorkeur inhoudsbron, maar bevindt centraal aan uw grensgroepen.

    Voorbeeld van grensgroepen en terugval tijden:

     ![BG_Fallack](media/BG_Fallback.png)


Met deze configuratie:
-   De client begint met zoeken naar inhoud vanaf distributiepunten in de *huidige* grensgroep (BG_A), zoeken naar elk distributiepunt wijst twee minuten voordat u overschakelt naar het volgende distributiepunt in de grensgroep. De groep clients met geldige inhoudsbron locaties bevat DP_A1 en DP_A2.
-   Als de client niet kan vinden van inhoud van de *huidige* grensgroep na 10 minuten zoekt, toegevoegd de distributiepunten van de grensgroep BG_B in de zoekopdracht. Vervolgens gaat door om te zoeken naar inhoud vanaf een distributiepunt in de gecombineerde van toepassingen van distributiepunten nu met die van de BG_A en de BG_B grensgroepen. De client blijft contact opnemen met elk distributiepunt voor twee minuten voordat u overschakelt naar het volgende distributiepunt uit de groep. De groep clients met geldige inhoudsbron locaties bevat DP_A1, DP_A2 DP_B1 en DP_B2.
-   Na een extra 10 minuten (totaal 20 minuten) als de client nog steeds niet een distributiepunt met inhoud gevonden is, deze wordt uitgebreid de groep van de beschikbare distributiepunten om op te nemen die uit de tweede *neighbor* groeperen, grensgroep BG_C. 6 distributiepunten om te zoeken (DP_A1, DP_A2 DP_B2, DP_B2, DP_C1 en DP_C2) heeft nu de client en deze blijft wijzigen in een nieuw distributiepunt elke twee minuten tot inhoud is gevonden.
-   Als de client niet voor inhoud na een totaal van 120 minuten gevonden is, vallen terug om op te nemen de *sitegrensgroep standaard* als onderdeel van de verder te zoeken. Distributiepunten in de groep bevat nu alle distributiepunten van de drie geconfigureerde grensgroepen en het laatste distributiepunt dat zich op de siteservercomputer.  De client blijft vervolgens de zoekactie voor inhoud, distributiepunten voor het wijzigen van elke twee minuten tot inhoud is gevonden.

U beheren wanneer specifieke distributiepunten worden toegevoegd als een inhoudsbronlocatie en wanneer, of als de client terugvallen op de standaard sitegrensgroep als veiligheidsnet voor inhoud die niet beschikbaar is van een andere locatie worden gebruikt door de verschillende neighbor-groepen zijn beschikbaar op verschillende tijdstippen configureren.


### <a name="bkmk_update"></a>Bijwerken van bestaande grensgroepen naar het nieuwe model
Wanneer u versie 1609 installeren en bijwerken van uw site, worden de volgende configuraties worden automatisch gemaakt. Deze zijn bedoeld om te controleren of dat uw huidige terugval gedrag beschikbaar is, blijft totdat u een nieuwe grensgroepen en relaties configureren.  
-   Niet-beveiligde distributiepunten op een site worden toegevoegd aan de *-Site-grens-standaardgroep\<sitecode >* grensgroep van die site.
-   Er wordt een kopie gemaakt van elke bestaande grensgroep die een siteserver die is geconfigureerd met een trage verbinding. De naam van de nieuwe groep is  ***\<oorspronkelijke grens groepsnaam > - traag - Tmp***:  
    -   Sitesystemen waarop een snelle verbinding blijven de oorspronkelijke grensgroep.
    -   Een kopie van de sitesystemen die een trage verbinding hebt worden toegevoegd aan de kopie van de grensgroep. De oorspronkelijke sitesystemen die zijn geconfigureerd als langzaam blijven in de oorspronkelijke grensgroep voor compatibiliteit met eerdere versies, maar worden niet gebruikt uit deze grensgroep.
    -   Dit exemplaar van de groep grens heeft geen grenzen die zijn gekoppeld. Echter, een fallback koppeling wordt gemaakt tussen de oorspronkelijke groep en de nieuwe grens groep kopie bevat de terugval tijd is ingesteld op nul.

 De volgende tabel bevat de nieuwe terugval gedrag u kunt verwachten van de combinatie van de oorspronkelijke implementatie-instellingen en distributie wijst configuraties:

De configuratie van het oorspronkelijke implementatie voor 'Programma niet uitvoeren' in een langzaam netwerk  |Oorspronkelijke distributiepunt in de configuratie voor 'Client toestaan een terugvalbronlocatie voor inhoud te gebruiken'  |Nieuwe terugval gedrag  
---------|---------|---------
Geselecteerd     |  Geselecteerd    |  **Er geen terugval** -gebruik alleen de distributiepunten in de huidige grensgroep.       
Geselecteerd     |  Geen geselecteerd|  **Er geen terugval** -gebruik alleen de distributiepunten in de huidige grensgroep.       
Geen geselecteerd |  Geen geselecteerd|  **Terugval naar aan neighbor** - gebruik van de distributiepunten in de huidige grensgroep en voeg vervolgens de distributiepunten van de grensgroep neighbor. Tenzij een expliciete koppeling aan de standaardgroep voor de grens van site is geconfigureerd, clients niet wordt terugval naar aan die groep.    
Geen geselecteerd | Geselecteerd     |   **Fallback normale** -distributiepunten gebruiken in de huidige grensgroep, en vervolgens die van de site en neighbor standaard grensgroepen

 Alle andere implementatieconfiguraties leiden tot **fallback normale**.  



## <a name="office-365-client-management-dashboard"></a>Dashboard voor Office 365-clientbeheer  
De Configuration Manager 1609 Technical Preview introduceert een nieuw dashboard. Als u wilt weergeven in het dashboard, in de Configuration Manager-console gaat u naar **softwarebibliotheek** > **overzicht** > **Office 365-clientbeheer**.
>[!NOTE]
>In de **What's New** werkruimte in de Configuration Manager-console, het nieuwe dashboard heet onjuist **Office 365-onderhoudsdashboard**.

Het dashboard toont de grafieken voor het volgende:

- Aantal Office 365-clients
- Versies van Office 365-client
- Clienttalen voor Office 365
- Office 365 client kanalen     
Zie voor meer informatie [overzicht van de update voor Office 365 ProPlus kanalen](https://technet.microsoft.com/library/mt455210.aspx).
- Regels voor automatische implementatie die u geselecteerd in de set beschikbare producten van Office 365 Client hebt.

U kunt de volgende acties uitvoeren op het dashboard:
- Aan de bovenkant van het dashboard gebruiken de **verzameling** Vervolgkeuze-instelling voor het filteren van de dashboardgegevens door leden van een specifieke verzameling.
- Klik in de rechterbovenhoek van het dashboard op **Office 365 Installer** starten van de Wizard Office 365 Client installeren voor Office 365-apps implementeren op clients. Zie voor meer informatie [implementeren Office 365-apps aan clients](#deploy-office-365-apps-to-clients).
- Klik aan de midden rechts van het dashboard op **een ADR maakt** openen van de Wizard automatische implementatie regel voor het maken van een nieuwe regel voor automatische implementatie (ADR). Voor het maken van een ADR voor Office 365-apps selecteert **Office 365 Client** wanneer u kiest voor het product. Zie voor meer informatie [softwareupdates automatisch implementeren](/sccm/sum/deploy-use/automatically-deploy-software-updates).
- Klik in de rechterbenedenhoek van het dashboard op **Clientagentinstellingen maken** om instellingen voor Clientagent te openen. Zie voor meer informatie [over clientinstellingen](/sccm/core/clients/deploy/about-client-settings).



Zie voor meer informatie over Office 365 ProPlus-updates, [Office 365 ProPlus beheren met Configuration Manager-updates](/sccm/sum/deploy-use/manage-office-365-proplus-updates).

## <a name="deploy-office-365-apps-to-clients"></a>Office 365-apps implementeren op clients
In deze release van het dashboard clientbeheer voor Office 365, kunt u het installatieprogramma van Office 365 waarmee u Office 365-installatie-instellingen configureren, bestanden downloaden van inhoud levering bedrijfsnetwerken (CDN) en de bestanden kunnen worden geïmplementeerd als een toepassing in Configuration Manager te starten.

### <a name="limitations-of-office-365-deployment"></a>Beperkingen van Office 365-implementatie
- Mogelijk hebt u problemen wanneer u probeert te importeren van bestaande clientinstellingen (XML) in de wizard Office 365-App installeren. U kunt de instellingen van de client zonder problemen handmatig configureren.

#### <a name="to-deploy-office-365-apps-to-clients"></a>Office 365-apps implementeren op clients
1. Navigeer in de Configuration Manager-console naar **softwarebibliotheek** > **overzicht** > **Office 365-clientbeheer**.
2. Klik op **Office 365 Installer** in het deelvenster rechtsboven. De Wizard Client installeren van Office 365 wordt geopend.
3. Op de **toepassingsinstellingen** pagina, Geef een naam en beschrijving voor de app, voer de downloadlocatie voor de bestanden en klik vervolgens op **volgende**. Houd er rekening mee dat de locatie moet worden opgegeven in het formulier &#92; &#92; *server*&#92; *delen*.
4. Op de **clientinstellingen importeren** pagina, kiest u of de Office 365 client-instellingen importeren van een bestaande XML-configuratiebestand of geef handmatig de instellingen en klik vervolgens op **volgende**.
Wanneer u een bestaand configuratiebestand hebt, voer de locatie voor het bestand en gaat u verder met stap 7. Houd er rekening mee dat de locatie moet worden opgegeven in het formulier &#92; &#92; *server*&#92; *delen*&#92; *bestandsnaam*. XML.

    > [!IMPORTANT]
    >Mogelijk hebt u problemen wanneer u probeert te importeren van bestaande clientinstellingen (XML) in deze technical preview.

5. Op de **clientproducten** pagina, selecteer de Office 365-pakket dat u gebruikt, selecteer de toepassingen die u wilt opnemen, selecteert u alle aanvullende Office-producten dat moeten worden opgenomen en klik vervolgens op **volgende**.
6. Op de **clientinstellingen** pagina, kiest u de instellingen die u wilt opnemen en klik op **volgende**.
7. Op de **implementatie** pagina, kies of u de toepassing implementeren en klik vervolgens op **volgende**.
Als u niet voor de implementatie van het pakket in de wizard kiest, gaat u naar stap 9.
8. De rest van de wizardpagina's configureren zoals u zou voor een typische implementatie doen. Zie voor meer informatie [maken en implementeren van een toepassing](/sccm/apps/get-started/create-and-deploy-an-application).
9. Voltooi de wizard.
10. U kunt implementeren of bewerken van de toepassing net zoals u zou doen met een andere toepassing in Configuration Manager uit **softwarebibliotheek** > **overzicht** > **Toepassingsbeheer** > **toepassingen**.

>[!NOTE]
>Nadat u Office 365-apps implementeert, kunt u regels voor automatische implementatie voor het onderhouden van de apps kunt maken. Klik op om een ADR voor Office 365-apps **een ADR maakt**, en selecteer **Office 365 Client** wanneer u kiest voor het product. Zie voor meer informatie [softwareupdates automatisch implementeren](/sccm/sum/deploy-use/automatically-deploy-software-updates).

## <a name="BKMK_UEFIConversion"></a>Verbeteringen voor BIOS in UEFI-conversie
U kunt nu een takenreeks voor implementatie van besturingssysteem met een nieuwe variabele, TSUEFIDrive, zodat de Computer opnieuw opstarten stap een FAT32-partitie op de harde schijf voor de overgang naar UEFI bereidt. De volgende procedure bevat een voorbeeld van hoe u de stappen in de takenreeks de harde schijf voorbereiden voor de conversie van UEFI-BIOS kunt maken.

#### <a name="to-prepare-the-fat32-partition-for-the-conversion-to-uefi"></a>De FAT32-partitie voor de conversie naar UEFI voorbereiden:
In een bestaande takenreeks om een besturingssysteem te installeren, wordt u een nieuwe groep met stappen om te doen het BIOS UEFI conversie toevoegen.

1. Maak een nieuwe takenreeksgroep na de stappen voor het vastleggen van bestanden en instellingen en voor de stappen voor het besturingssysteem installeren. Maakt bijvoorbeeld een groep na de **vastleggen van bestanden en instellingen** groep met de naam **BIOS-UEFI-**.
2. Op de **opties** tabblad van de nieuwe groep, een nieuwe takenreeksvariabele als een voorwaarde toevoegen waarbij **_SMSTSBootUEFI** is **niet gelijk aan** naar **true**. Dit voorkomt dat de stappen in de groep uitgevoerd wanneer een computer al in UEFI-modus is.
![BIOS UEFI-groep](media/BIOS-to-UEFI-group.png)
3. Voeg onder de nieuwe groep, de **Computer opnieuw opstarten** takenreeksstap. In **instellen wat moet worden uitgevoerd na herstart**, selecteer **de opstartinstallatiekopie toegewezen aan deze takenreeks is geselecteerd** Start de computer in Windows PE.  
4. Op de **opties** tabblad, een takenreeksvariabele toevoegen als een voorwaarde waar **_SMSTSInWinPE gelijk is aan false**. Dit voorkomt dat deze stap uitvoert als de computer al in Windows PE is.

    ![Stap van de Computer opnieuw opstarten](media/Restart-in-Windows-PE.png)
5. Een stap voor het starten van de OEM-hulpprogramma dat de firmware van BIOS wordt converteren naar UEFI toevoegen. Dit wordt doorgaans een **opdrachtregel uitvoeren** takenreeksstap met een opdrachtregel het OEM-hulpprogramma starten.
5.  De schijf formatteren en partitioneren takenreeksstap die partitioneren en formatteren van de harde schijf toevoegen. In de stap wordt het volgende doen:
    1.  Maak de FAT32-partitie worden geconverteerd naar UEFI voordat het besturingssysteem wordt geïnstalleerd. Kies **GPT** voor **schijftype**.
    ![Formatteren en partitioneren schijf stap](media/Format-and-partition-disk.png)
    2.  Ga naar de eigenschappen voor de FAT32-partitie. Voer **TSUEFIDrive** in de **variabele** veld. Wanneer de takenreeks deze variabele detecteert, bereidt het voor de overgang UEFI voordat de computer opnieuw wordt opgestart.
    ![Partitie-eigenschappen](media/Partition-properties.png)
    3. Maak een NTFS-partitie met de engine voor takenreeksen op te slaan de status en voor het opslaan van logboekbestanden.
6.  Voeg de **Computer opnieuw opstarten** takenreeksstap. In **instellen wat moet worden uitgevoerd na herstart**, selecteer **de opstartinstallatiekopie toegewezen aan deze takenreeks is geselecteerd** Start de computer in Windows PE.  




## <a name="intune-compliance-charts"></a>Intune naleving grafieken
In deze release kunt u een overzicht van de algemene compatibiliteit krijgen voor apparaten en de belangrijkste redenen voor niet-naleving met behulp van de nieuwe grafieken onder **werkruimte bewaking** in de Configuration Manager-console.

#### <a name="to-view-the-intune-compliance-charts"></a>Om de compatibiliteit van de Intune-grafieken.
1. Ga in de Configuration Manager-console naar **bewaking** > **overzicht** > **instellingen voor naleving**.
2. De **algehele apparaatcompatibiliteit** grafiek wordt weergegeven.
3. Klik op de **nalevingsbeleid** knooppunt om weer te geven de **algehele apparaatcompatibiliteit** en **boven niet-naleving redenen** grafieken.

### <a name="limitations-of-intune-compliance-charts-in-tp-1609"></a>Beperkingen van Intune naleving diagrammen in TP 1609
- De DrillDown voor de **algehele apparaatcompatibiliteit** grafiek momenteel, treedt een fout.
- De **de belangrijkste redenen voor niet-naleving** grafiek bevat de naam van het beleid en niet de afzonderlijke niet-naleving redenen. U kunt klikken op het beleid voor inzoomen en raadpleegt de apparaten die niet compatibel zijn voor dat beleid.

### <a name="try-it-out"></a>Try it out in
Voer de volgende secties in volgorde:

#### <a name="check-overall-compliance-chart"></a>Diagram van de algemene compatibiliteit controleren
1. Toevoegen aan twee iOS nalevingsbeleid in Configuration Manager. Één beleid moet één reeks instellingen voor apparaten (bijvoorbeeld set pincodelengte tot en met 6) hebben. Het andere beleid moet een andere set-instellingen (bijvoorbeeld PINCODE complexiteit) hebben. De beleidsinstellingen moeten niet overlappen of er conflicten optreden.
2. De twee beleidsregels implementeren op een groep gebruikers.
3. Twee iOS-apparaten inschrijven in Intune met hetzelfde gebruikersaccount en een account dat het beleid in de vorige stap hebt ontvangen. De apparaten niet aan de criteria van het nalevingsbeleid voldoen.
4. In Configuration Manager controleren de **algehele apparaatcompatibiliteit** grafiek. Beide apparaten moeten worden gerapporteerd als niet-compatibel.
<!-- 5. Click the **Non-compliant** section of the chart. Both devices should appear in the filtered view under **Assets and Compliance** > **Overview** > **Device**. -->

#### <a name="check-the-top-non-compliance-reasons-chart"></a>De grafiek met de belangrijkste redenen voor niet-naleving controleren
5. Controleer de **de belangrijkste redenen voor niet-naleving** grafiek. Dit diagram geeft een lijst van de bovenste 5 redenen voor niet-naleving, maar wanneer u slechts twee instellingen voor naleving zijn ingesteld via beleid voor de bovenste 2 niet-naleving redenen weergegeven.
6. Klik op een van de secties in de grafiek. Beide apparaten moeten worden weergegeven in de gefilterde weergave onder **activa en naleving** > **overzicht** > **apparaat**.

#### <a name="make-devices-compliant-and-check-the-charts"></a>Apparaten voldoen aan het beleid maken en controleren van de grafieken
7. Maak een van de apparaten compatibel zijn met een van de beleidsregels. Controleer de **algehele apparaatcompatibiliteit** grafiek opnieuw. Een compatibel apparaat en één niet-compatibel apparaat moet worden weergegeven in de grafiek.
8. De andere apparaat compatibel zijn met hetzelfde beleid maken. Hiermee maakt u één apparaat compatibel is met zowel de beleidsregels en één apparaat compatibel zijn met slechts één van de beleidsregels.
9. Controleer de **de belangrijkste redenen voor niet-naleving** grafiek. Er mag alleen een niet-naleving van de redenen vermeld.
<!--7. Click the **Compliant** section of the chart. Only the compliant device should appear in the filtered view. -->





## <a name="see-also"></a>Zie ook
[Technical Preview voor System Center Configuration Manager](../../core/get-started/technical-preview.md)
