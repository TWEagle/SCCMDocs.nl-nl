---
title: Mogelijkheden in Technical Preview 1609 Configuration Manager
description: Meer informatie over functies die beschikbaar zijn in de Technical Preview voor System Center Configuration Manager, versie 1609.
ms.custom: na
ms.date: 01/23/2017
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.prod: configuration-manager
ms.technology:
- configmgr-other
ms.topic: article
ms.assetid: e2a59116-b2e5-4dd2-90eb-0b8a5eb50b56
caps.latest.revision: 2
author: Brenduns
ms.author: brenduns
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 5d08d1f9ccd995d544c3c21c4af52ede73343077
ms.openlocfilehash: 89a41c8a3137d0e54011ddf9a1d9b4894ecb7df8
ms.contentlocale: nl-nl
ms.lasthandoff: 05/17/2017

---
# <a name="capabilities-in-technical-preview-1609-for-system-center-configuration-manager"></a>Mogelijkheden in Technical Preview 1609 voor System Center Configuration Manager

*Van toepassing op: System Center Configuration Manager (technische Preview)*



Dit artikel worden de functies die beschikbaar in de Technical Preview voor System Center Configuration Manager, versie 1609 zijn geïntroduceerd. U kunt deze versie om te werken en nieuwe mogelijkheden toevoegen aan uw technische preview van Configuration Manager site installeren.      Voordat u deze versie van de technische preview installeert, leest u de inleidende onderwerp [Technical Preview voor System Center Configuration Manager](../../core/get-started/technical-preview.md), om meer vertrouwd raken met algemene vereisten en beperkingen voor het gebruik van een technische preview hoe tussen versies en hoe u feedback geven over de functies in een technische preview bijwerken.    

**Bekende problemen in deze Technical Preview:**  
*  Wanneer u naar de Configuration Manager 1609 Technical Preview bijwerkt, kunt u eventuele edition upgrade beleidsregels die u hebt geïmplementeerd wordt verwijderd. Als u wilt blijven gebruiken deze beleidsregels, moet u opnieuw maken en implementeren.


**De volgende zijn nieuwe functies die u met deze versie kunt uitproberen.**  

## <a name="improvements-to-endpoint-protection"></a>Verbeteringen in de Endpoint Protection
Verbetering van de beleidsinstellingen voor schadelijke software van Endpoint Protection - u nu het toegangsniveau kunt opgeven waarmee de beveiligingsservice Endpoint Protection Cloud verdachte bestanden wordt geblokkeerd. Een nieuwe instelling kan beheerders "riskant" computers op basis van de hoge bedragen kwaadaardige software die ze tegenkomen opgeven.

## <a name="increased-number-of-enrolled-devices"></a>Toenemend aantal geregistreerde apparaten
Beheerders kunnen nu gebruikers kunnen maximaal 15 apparaten in beheer van hybride mobiele apparaten met Intune inschrijven inschakelen. De limiet is eerder 5 apparaten per gebruiker.

## <a name="additional-apple-dep-settings"></a>Aanvullende Apple DEP-instellingen

Beheerders kunnen nu de volgende Apple Device Enrollment Program (DEP)-instellingen configureren in het DEP-profiel voor iOS- en Mac-apparaten:
- **Touch ID**
- **Zoomen**
- **Siri**

Bij inschakeling vraagt Apples Configuratieassistent om deze service tijdens het activeren van het apparaat.

## <a name="integration-with-upgrade-analytics"></a>Integratie met de Upgrade Analytics

Upgrade analytics kunt u om te beoordelen en analyseren apparaat gereedheid en compatibiliteit met Windows 10 zodat eenvoudiger en vloeiende upgrades. Met de Upgrade Analytics met Configuration Manager-integratie kunt u toegang tot de upgradecompatibiliteit gegevens in de beheerconsole van Configuration Manager en vervolgens uit de lijst met apparaten doelapparaten voor herstel of upgrade.

Meer informatie over upgraden Analytics in [aan de slag met Analytics Upgrade](https://technet.microsoft.com/itpro/windows/deploy/upgrade-analytics-get-started).

## <a name="native-connection-types-for-windows-10-vpn-hybrid-profiles"></a>Systeemeigen verbindingstypen voor Windows 10 hybride VPN-profielen

Wanneer u Configuration Manager met Intune, kunt u nu Windows 10 VPN-profielen maken met Microsoft Automatic, IKEv2, PPTP en L2TP verbindingstypen in de Configuration Manager-console zonder met behulp van OMA-URI.

## <a name="enhancements-to-windows-store-for-business-integration-with-configuration-manager"></a>Uitbreidingen voor Windows Store voor Business-integratie met Configuration Manager

In deze release we hebben bijgewerkt [Windows Store voor integratie van Business](/sccm/apps/deploy-use/manage-apps-from-the-windows-store-for-business) met deze nieuwe functies:

**Update:** In de huidige technische voorbeeldversie werkt de onmiddellijke synchronisatiefunctie niet.

- Eerder, kunt u gratis apps uit de Windows Store voor bedrijven alleen implementeren. Configuration Manager nu bovendien ondersteunt implementeren online betaalde licentie apps (voor Intune ingeschreven apparaten).
- U kunt nu een onmiddellijke synchronisatie tussen de Windows Store voor bedrijven en Configuration Manager te starten.
- U kunt nu de client geheime sleutel die u hebt ontvangen van Azure Active Directory wijzigen

### <a name="try-it-out"></a>Probeer het nu!

#### <a name="purchase-and-sync-a-paid-online-licensed-app"></a>Koop en synchroniseren van een betaalde licentie online app

1. Koop een betaald online gelicentieerde vanuit de Windows Store voor bedrijven.
2. In de **beheer** werkruimte van de Configuration Manager-console klikt u op **Cloudservices** > **Updates en onderhoud** > **Windows Store voor bedrijven**.
3. Op de **Start** tabblad, in de **Sync** groep, klikt u op **nu synchroniseren**.
4. Snel daarna de app die u hebt aangeschaft wordt weergegeven in de **licentie-informatie voor de Store-Apps** knooppunt van de **Toepassingsbeheer** werkruimte.

#### <a name="create-and-deploy-a-configuration-manager-application-from-the-synchronized-app-data"></a>Maken en implementeren van een Configuration Manager-toepassing van de gesynchroniseerde app-gegevens

De procedure voor het maken en implementeren van een Configuration Manager-toepassing van een betaald store-app is hetzelfde als die voor het maken van een toepassing van een gratis app. Zie de sectie **maken en implementeren van een Configuration Manager-toepassing in een Windows Store voor Business-app** in [apps beheren vanuit de Windows Store voor bedrijven met System Center Configuration Manager](/sccm/apps/deploy-use/manage-apps-from-the-windows-store-for-business).


#### <a name="modify-the-client-secret-key-from-azure-active-directory"></a>Wijzigen van de geheime sleutel van de client van Azure Active Directory

1. In de **beheer** werkruimte van de Configuration Manager-console klikt u op **Cloudservices** > **Updates en onderhoud** > **Windows Store voor bedrijven**.
2. Selecteer uw Windows Store voor bedrijven-account en klik vervolgens op **eigenschappen**.
3. In de **Windows Store voor zakelijke accounteigenschappen** dialoogvenster, voert u een nieuwe sleutel in de **Client geheime sleutel** veld en klik vervolgens op **controleren**. Nadat gecontroleerd, klikt u op **toepassen**, sluit het dialoogvenster.


## <a name="new-compliance-settings-for-configuration-items"></a>Nieuwe compatibiliteitsinstellingen voor configuratie-items

Veel nieuwe instellingen die u in uw configuratie-items voor verschillende apparaatplatforms gebruiken kunt toegevoegd.
Dit zijn de instellingen die eerder beschikbaar waren in Microsoft Intune in een zelfstandige configuratie en zijn nu beschikbaar wanneer u Intune met Configuration Manager.
Als u hulp nodig met een van deze instellingen, open je [instellingen en functies op uw apparaten met Microsoft Intune-beleid beheren](https://docs.microsoft.com/en-us/intune/deploy-use/manage-settings-and-features-on-your-devices-with-microsoft-intune-policies) en selecteer vervolgens het onderwerp van de instellingen voor het platform dat u wilt.


### <a name="new-settings-for-android-devices"></a>Nieuwe instellingen voor Android-apparaten

#### <a name="password-settings"></a>Wachtwoordinstellingen

- **Wachtwoordgeschiedenis onthouden**
- **Vingerafdruk toestaan ontgrendelen**

#### <a name="security-settings"></a>Beveiligingsinstellingen

- **Versleuteling vereisen voor opslagkaarten**
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

#### <a name="device-capability-settings"></a>Mogelijkheid apparaatinstellingen

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
- **Handmatige unenrollment toestaan**

#### <a name="device-capability-settings"></a>Mogelijkheid apparaatinstellingen

- **VPN via mobiele verbinding toestaan**
- **VPN-roaming via mobiele verbinding toestaan**
- **Opnieuw instellen van telefoon toestaan**
- **USB-verbinding toestaan**
- **Cortana toestaan**
- **Meldingen van Onderhoudscentrum toestaan**

### <a name="new-settings-for-windows-10-team-devices"></a>Nieuwe instellingen voor Windows 10 Team-apparaten

#### <a name="device-settings"></a>Instellingen voor apparaten

- **Azure Operational Insights inschakelen**
- **Draadloze projectie Miracast inschakelen**
- **Kies de vergadering informatie die wordt weergegeven op het welkomstscherm te selecteren**
- **URL achtergrondafbeelding Lockscreen**


### <a name="new-settings-for-windows-81-devices"></a>Nieuwe instellingen voor Windows 8.1-apparaten

#### <a name="applicability-settings"></a>Instellingen van toepassing

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
- **Afbeeldingswachtwoord en PINCODE toestaan**

#### <a name="browser-settings"></a>Browserinstellingen

- **Automatische detectie van intranetnetwerk toestaan**


### <a name="new-settings-for-windows-phone-81-devices"></a>Nieuwe instellingen voor Windows Phone 8.1-apparaten

#### <a name="applicability-settings"></a>Instellingen van toepassing

- **Alle configuraties toepassen op Windows 10**

#### <a name="password-settings"></a>Wachtwoordinstellingen

- **Minimum aantal tekensets**
- **Eenvoudige wachtwoorden toestaan**
- **Wachtwoordgeschiedenis onthouden**

#### <a name="device-capability-settings"></a>Mogelijkheid apparaatinstellingen

- **Automatische verbinding met gratis Wi-Fi-hotspots toestaan**


## <a name="improvements-for-boundary-groups"></a>Verbeteringen voor grensgroepen
Dit voorbeeld bevat belangrijke wijzigingen aan grensgroepen, en hoe ze werken met distributiepunten. Deze wijzigingen wordt het ontwerp van uw inhoud infrastructuur vereenvoudigen tijdens het doorgeven van meer controle over hoe en wanneer clients terugval om te zoeken naar aanvullende distributie als de locatie van de inhoudsbron verwijst. Dit omvat zowel lokaal als cloud-gebaseerde distributiepunten.

Deze verbeteringen concepten en gedrag dat u bekend bent met vandaag (zoals het configureren van distributiepunten als snel of traag) worden vervangen en vervangen door een nieuw model die eenvoudiger kan worden geconfigureerd en onderhouden. Deze wijzigingen zijn ook voordat u begint met toekomstige wijzigingen die andere sitesysteemrollen die u aan grensgroepen koppelen verbeteren.  

Tijdens de upgrade naar 1609, zet de upgrade uw huidige configuratie van de groep grens aan te passen van het nieuwe model zodat deze wijzigingen niet de configuraties van de distributie van inhoud storen (Zie [bestaande grensgroepen bijwerken naar het nieuwe model](/sccm/core/get-started/capabilities-in-technical-preview-1609#bkmk_update)).

De volgende secties detailleren de wijzigingen die werden geïntroduceerd in dit voorbeeld de werking van het nieuwe model en wat u kunt verwachten wanneer u een upgrade van een site die al grensgroepen die zijn geconfigureerd is.



### <a name="changes-in-ui-and-behavior-for-boundary-groups-and-content-locations"></a>Wijzigingen in de gebruikersinterface en het gedrag voor grensgroepen en locaties van inhoud
De volgende belangrijke wijzigingen zijn in grensgroepen en hoe clients inhoud vinden. Veel van deze wijzigingen en concepten samenwerken.
-    **Configuraties voor snel of traag zijn verwijderd:** U configureert niet langer individuele distributiepunten om snel of traag.  In plaats daarvan elk sitesysteem dat is gekoppeld aan een grensgroep wordt behandeld hetzelfde. Vanwege deze wijziging, de **verwijzingen** tabblad van eigenschappen van de grensgroep biedt geen ondersteuning voor de configuratie van snel of traag.
-     **Nieuwe standaard grensgroep op elke site:**  Elke primaire site heeft een nieuwe standaard grensgroep met de naam ***standaard---Sitegrensgroep\<sitecode >***.  Wanneer een client zich niet op een netwerklocatie bevindt die is toegewezen aan een grensgroep bevindt, dat de client de sitesystemen die zijn gekoppeld aan de standaardgroep van de toegewezen site gebruiken. Wilt u deze grensgroep gebruiken als een vervangende met het concept van een locatie terugvalinhoudlocatie.      
 -    **'Alternatieve bronlocaties voor inhoud toestaan'** wordt verwijderd: U configureert niet langer expliciet een distributiepunt moet worden gebruikt voor terugval en de opties in te stellen dit worden verwijderd uit de gebruikersinterface.

    Daarnaast het resultaat van de instelling **clients met een terugvalbronlocatie voor inhoud toestaan** op een implementatie van het type voor toepassingen is gewijzigd. Deze instelling op een implementatietype te detecteren, kunnen clients de standaard sitegrensgroep gebruiken als bronlocatie voor inhoud.

 -    **Grens groepen relaties:** Elke grensgroep kan worden gekoppeld aan een of meer extra grensgroepen. Deze koppelingen vormen relaties die zijn geconfigureerd op de nieuwe grens groep tabblad Eigenschappen met de naam **relaties**:
     -    Elke grensgroep die een client rechtstreeks is gekoppeld aan heet een **huidige** grensgroep.  
    -     Andere grensgroepen die een client kan gebruiken als gevolg van een koppeling tussen die client *huidige* grensgroep en een andere groep heet een **neighbor** grensgroep.
    -  Deze zich op de **relaties** tabblad dat u die kunnen worden gebruikt toevoegt als een *neighbor* grensgroep. U kunt ook een tijd in minuten dat bepaalt wanneer een client die niet kunnen zoeken naar inhoud vanaf een distributiepunt in de *huidige* begint om te zoeken naar de locatie van inhoud van die groep *neighbor* grensgroepen.

        Wanneer u toevoegen of wijzigen van de configuratie van een grensgroep, hebt u de optie naar blok fallback naar die grensgroep specifieke van de huidige groep die u configureert.

    Expliciete koppelingen (koppelingen) uit een grensgroep definiëren voor het gebruik van de nieuwe configuratie en alle distributiepunten configureren in de gekoppelde groep met dezelfde tijd in minuten. De tijd die u configureert bepaalt wanneer een client die niet kunnen vinden van een inhoudsbron van de *huidige* grensgroep kunt beginnen met zoeken naar inhoudsbronnen uit die groep neighbor grens.

    Naast de grensgroepen die uitdrukkelijk configureren, heeft elke grensgroep een impliciete koppeling naar de standaard sitegrensgroep. Deze koppeling wordt geactiveerd nadat 120 minuten op dat moment wordt de standaardgroep van de site-grens van een neighbor-grensgroep waarmee de clients om de distributiepunten die zijn gekoppeld aan deze grensgroep als bronlocatie voor inhoud te gebruiken.

    Dit gedrag vervangt wat eerder is aangeduid als terugval voor inhoud.  U kunt dit standaardgedrag van 120 minuten door expliciet koppelen van de grensgroep standaard website naar een *huidige* groep, en het instellen van een bepaalde tijd in minuten of blokkeren terugval volledig om te voorkomen dat het gebruik ervan.


-     **Clients proberen inhoud op te halen van elk distributiepunt tot 2 minuten:** Wanneer een client zoekt naar een locatie van de inhoudsbron, probeert ze toegang krijgen tot elk distributiepunt 2 minuten en probeer het vervolgens een ander distributiepunt. Dit is een wijziging ten opzichte van eerdere versies waar clients heeft geprobeerd verbinding maken met een distributiepunt maximaal 2 uur.

    - Het eerste distributiepunt dat u een client probeert te gebruiken is willekeurig hebt geselecteerd in de groep met beschikbare distributiepunten in de client *huidige* grensgroep (of groepen).

    - Na twee minuten als de client niet voor de inhoud gevonden is deze verandert in een nieuw distributiepunt en probeert inhoud op te halen van die server. Dit proces wordt herhaald voor elke twee minuten totdat de client de inhoud is gevonden of de laatste server in de groep van toepassingen is bereikt.

    - Als een client een geldig inhoudsbronlocatie uit niet vinden de *huidige* groep voordat u de periode voor terugval naar een *neighbor* grensgroep is bereikt, wordt de client worden de distributiepunten uit die *neighbor* groeperen met het einde van de huidige lijst en zoek vervolgens de uitgevouwen groep bronlocaties die de distributiepunten van beide grensgroepen bevat.

        > [!TIP]  
        > Wanneer u een expliciete koppeling te van de huidige grensgroep toe aan de grensgroep standaard site maken en een alternatief tijd die kleiner is dan de alternatieve tijd voor een koppeling naar een grensgroep neighbor definiëren, zullen clients begint met zoeken bronlocaties van de standaard sitegrensgroep voordat de neighbor-groep.

    - Wanneer de client niet kan inhoud op te halen uit de laatste server in de groep, begint het proces opnieuw.


### <a name="how-the-new-model-works"></a>De werking van het nieuwe model
Wanneer u grensgroepen configureert, koppelen u grenzen (netwerklocaties) en sitesysteemrollen, zoals distributiepunten aan de grensgroep. Hiermee wordt koppeling clients sitesysteemservers zoals distributiepunten die zich bevinden in de buurt van de clients op het netwerk.   
-    U kunt dezelfde grens toewijzen aan meerdere grensgroepen
-    Sitesysteemservers, zoals de distributiepunten, kunnen worden gekoppeld aan meerdere grensgroepen, zodat ze beschikbaar zijn voor een groot aantal netwerklocaties
-    Als een distributiepunt niet gekoppeld aan een grensgroep is, kunnen clients worden niet dat distributiepunt gebruiken als bronlocatie voor inhoud.

Vanaf deze technische preview, definieert u de groepsrelaties grens om alternatieve gedrag voor inhoudsbron locaties te configureren. Hierdoor is geconfigureerd op de nieuwe **relaties** tabblad van de eigenschappen van grensgroep en vervangt sitesystemen zo langzaam of snel worden configureren en het configureren van een grensgroep zodat terugvalbronlocatie voor inhoud.

Op het tabblad relaties toevoegen u andere grensgroepen configureren van een relatie aan deze groepen. Elke relatie is een eenzijdige koppeling in de **huidige** grensgroep toe aan de grensgroep u hebt toegevoegd, die wordt aangeroepen een **neighbor**. Voor elke koppeling die u maakt, kunt u distributiepunten configureren met een alternatieve tijd in minuten. Deze tijd wordt gebruikt om te bepalen na hoe lang clients in de *huidige* grensgroep kunt gaan gebruiken distributiepunten in de *neighbor* grensgroep als ze geen geldige inhoudsbronlocatie vinden van hun huidige grensgroep.

Wanneer een client inhoud niet vinden kan en zoeken naar locaties van neighbor grensgroepen wordt gestart, neemt de groep met beschikbare distributiepunten voor die client op een gecontroleerde manier.  

-    Een grensgroep kan meer dan één relatie hebben. Hiermee kunt u terugval naar andere neighbors na verschillende perioden configureren.
-    Clients worden alleen terugval aan een grensgroep die een directe neighbor van hun huidige grensgroep.
-    Wanneer een client lid is van meerdere grensgroepen behoort, wordt de huidige grensgroep gedefinieerd als een samenvoeging van die grensgroepen zijn van de client.  Client kan vervolgens terugval naar een neighbor van elk van de oorspronkelijke grensgroepen.

Naast de koppelingen die u definieert, is er een impliciete koppeling die automatisch wordt gemaakt tussen de grensgroepen die u maakt en de standaard-grensgroep die automatisch wordt gemaakt voor elke site. Deze automatische koppeling:
-    Wordt gebruikt door clients die zijn niet op een grens die automatisch zijn gekoppeld aan andere grensgroepen die in uw hiërarchie gebruiken de standaardgroep van de grens van hun toegewezen site om geldige inhoudsbron locaties te identificeren.   
-     Is een standaard terugvaloptie uit de huidige grensgroep toe aan de grensgroep voor sites standaard die wordt gebruikt na 120 minuten.

**Voorbeeld van het gebruik van het nieuwe model:**     
U maken drie grensgroepen die niet grenzen of sitesysteemservers delen:
-    Groep BG_A met distributiepunten DP_A1 en DP_A2 die zijn gekoppeld aan de groep
-    Groep BG_B met distributiepunten DP_B1 en DP_B2 die zijn gekoppeld aan de groep
-    Groep BG_C met distributiepunten DP_C1 en DP_C2 die zijn gekoppeld aan de groep

U de netwerklocaties van uw clients toevoegen als grenzen tot aan de grensgroep BG_A en u vervolgens relaties uit die grensgroep aan de andere twee grensgroepen configureren:
-    Configureren van distributiepunten voor de eerste *neighbor* groep (BG_B) moet worden gebruikt na 10 minuten. Deze groep bevat distributiepunten DP_B1 en DP_B2. Beide zijn goed verbonden zijn met de eerste groepen grenslocaties.
-    Configureren van de tweede *neighbor* groep (BG_C) moet worden gebruikt na 20 minuten. Deze groep bevat distributiepunten DP_C1 en DP_C2. Beide worden via een WAN van de andere twee grensgroepen.
-    U ook toevoegen een extra distributiepunt dat zich bevindt op de siteserver aan de grensgroep sites standaard site. Dit is de locatie van de minste voorkeur inhoudsbron, maar het is centraal bevindt aan alle grensgroepen.

    Voorbeeld van grensgroepen en alternatieve tijden:

     ![BG_Fallack](media/BG_Fallback.png)


Met deze configuratie:
-    De client begint met zoeken naar inhoud vanaf distributiepunten in de *huidige* grensgroep (BG_A), zoeken naar elk distributiepunt wijst twee minuten voordat u overschakelt naar het volgende distributiepunt in de grensgroep. De groep clients geldige inhoud bronlocaties omvat DP_A1 en DP_A2.
-    Als de client niet kan vinden van inhoud van de *huidige* grensgroep na 10 minuten zoekt, vervolgens wordt toegevoegd de distributiepunten van de grensgroep BG_B de zoekopdracht. Vervolgens gaat door om te zoeken naar inhoud vanaf een distributiepunt in de gecombineerde toepassingen van distributiepunten die bevat nu informatie over de objecten uit de BG_A en de BG_B grensgroepen. Neem contact op met elk distributiepunt twee minuten voordat u overschakelt naar het volgende distributiepunt uit de groep blijft de client. De groep clients geldige inhoud bronlocaties omvat DP_A1, DP_A2 DP_B1 en DP_B2.
-    Na nog 10 minuten zijn verstreken (totaal 20 minuten) als de client nog steeds niet een distributiepunt met inhoud gevonden is, het breidt de adresgroep van beschikbare distributiepunten op te nemen die uit de tweede *neighbor* groeperen, grensgroep BG_C. De client 6 distributiepunten om te zoeken (DP_A1, DP_A2 DP_B2, DP_B2, DP_C1 en DP_C2) is nu en blijft het wijzigen van een nieuw distributiepunt om twee minuten tot inhoud is gevonden.
-    Als de client niet voor inhoud na een totaal van 120 minuten gevonden is, vallen terug zodat de *sitegrensgroep standaard* als onderdeel van de verder te zoeken. Distributiepunten in de groep bevat nu alle distributiepunten van de drie geconfigureerde grensgroepen en het laatste distributiepunt zich op de site server-computer.  Vervolgens blijft de client de zoekopdracht voor inhoud, distributiepunten wijzigen om twee minuten tot inhoud is gevonden.

U bepaalt wanneer specifieke distributiepunten worden toegevoegd als een inhoudsbronlocatie en wanneer, of als de client voor inhoud die niet beschikbaar is van een andere locatie veiligheidsredenen terugval toe aan de grensgroep standaard site gebruikt door het configureren van de verschillende neighbor groepen zijn beschikbaar op verschillende tijdstippen.


### <a name="bkmk_update"></a>Bestaande grensgroepen in het nieuwe model bijwerken
Wanneer u versie 1609 installeren en bijwerken van uw site, worden de volgende configuraties automatisch gemaakt. Deze zijn bedoeld om ervoor te zorgen dat uw huidige alternatieve gedrag blijft beschikbaar, totdat u een nieuwe grensgroepen en relaties configureren.  
-    Niet-beveiligde distributiepunten op een site worden toegevoegd aan de *standaard---Sitegrensgroep\<sitecode >* grensgroep van die site.
-    Een kopie wordt van elke bestaande grensgroep die een siteserver die is geconfigureerd met een langzame verbinding gemaakt. De naam van de nieuwe groep is *** \<oorspronkelijke grens groepsnaam > - traag - Tmp***:  
    -    Sitesystemen waarop een snelle verbinding blijven in de oorspronkelijke grensgroep.
    -    Een kopie van de site-systemen die een trage verbinding hebt worden toegevoegd aan de kopie van de grensgroep. De oorspronkelijke sitesystemen zijn geconfigureerd als langzaam blijven in de oorspronkelijke grensgroep voor achterwaartse compatibiliteit, maar worden niet gebruikt uit deze grensgroep.
    -     Deze kopie van de groep grens heeft geen grenzen die ermee verbonden zijn. Echter wordt een alternatieve koppeling gemaakt tussen de oorspronkelijke groep en de nieuwe grens groep kopie bevat de alternatieve tijd ingesteld op nul.

 De volgende tabel bevat de nieuwe alternatieve gedrag u kunt verwachten van de combinatie van de oorspronkelijke implementatie-instellingen en distributie wijst configuraties:

Oorspronkelijke implementatieconfiguratie voor "Programma niet uitvoeren" in langzaam netwerk  |Configuratie voor 'Client toestaan een terugvalbronlocatie voor inhoud te gebruiken' oorspronkelijke distributiepunt  |Nieuw alternatief gedrag  
---------|---------|---------
Geselecteerd     |  Geselecteerd    |  **Er is geen terugval** -enkel de distributiepunten in de huidige grensgroep gebruiken       
Geselecteerd     |  Niet ingeschakeld|  **Er is geen terugval** -enkel de distributiepunten in de huidige grensgroep gebruiken       
Niet ingeschakeld |  Niet ingeschakeld|  **Fallback naar neighbor** - gebruik van de distributiepunten in de huidige grensgroep en klikt u vervolgens de distributiepunten toevoegen van de grensgroep neighbor. Tenzij een expliciete koppeling naar de standaardgroep voor de grens van site is geconfigureerd, clients zal nalaten fallback naar die groep.    
Niet ingeschakeld | Geselecteerd        |   **Normale terugval** -distributiepunten in de huidige grensgroep gebruiken, dan die van de site en neighbor standaard grensgroepen

 Alle andere configuraties voor de implementatie leiden tot **normale terugval**.  



## <a name="office-365-client-management-dashboard"></a>Office 365 clientbeheer dashboard  
De Configuration Manager 1609 Technical Preview introduceert een nieuwe dashboard. Als u wilt weergeven in het dashboard, in de Configuration Manager-console gaat u naar **softwarebibliotheek** > **overzicht** > **Office 365-clientbeheer**.
>[!NOTE]
>In de **What's New** werkruimte in de Configuration Manager-console, het nieuwe dashboard heet onjuist **dashboard Office 365 onderhoud**.

Het dashboard geeft grafieken voor het volgende weer:

- Aantal Office 365-clients
- Office 365-clientversies
- Clienttalen voor Office 365
- Office 365 client kanalen     
Zie voor meer informatie [overzicht van de update voor Office 365 ProPlus communicatiekanalen](https://technet.microsoft.com/library/mt455210.aspx).
- Regels voor automatische implementatie met Office 365-Client in de set beschikbare producten is geselecteerd.

U kunt de volgende acties uitvoeren op het dashboard:
- Aan de bovenkant van het dashboard, gebruiken de **verzameling** vervolgkeuzelijst instelling voor het filteren van dashboardgegevens door leden van een specifieke verzameling.
- Klik in de rechterbovenhoek van het dashboard op **Office 365 Installer** starten van de Wizard Office 365 Client installeren voor Office 365-apps implementeren op clients. Zie voor meer informatie, [implementeren Office 365-apps aan clients](#deploy-office-365-apps-to-clients).
- Klik op de zijde midden rechts van het dashboard **maken van een ADR** openen van de Wizard automatische implementatie regel voor het maken van een nieuwe regel voor automatische implementatie (ADR). Voor het maken van een ADR voor Office 365-apps selecteert **Office 365 Client** wanneer u het product. Zie voor meer informatie [software-updates automatisch implementeren](/sccm/sum/deploy-use/automatically-deploy-software-updates).
- Klik in de rechterbenedenhoek van het dashboard op **Clientagentinstellingen maken** clientagentinstellingen openen. Zie voor meer informatie [over clientinstellingen](/sccm/core/clients/deploy/about-client-settings).



Zie voor meer informatie over Office 365 ProPlus updates [Office 365 ProPlus beheren met Configuration Manager-updates](/sccm/sum/deploy-use/manage-office-365-proplus-updates).

## <a name="deploy-office-365-apps-to-clients"></a>Office 365-apps implementeren op clients
In deze versie van het dashboard clientbeheer voor Office 365, kunt u het installatieprogramma van Office 365 waarmee u Office 365-installatie-instellingen configureren, bestanden downloaden van inhoud voor de levering van bedrijfsnetwerken (CDN) en de bestanden implementeren als een toepassing in Configuration Manager te starten.

### <a name="limitations-of-office-365-deployment"></a>Beperkingen van Office 365-implementatie
- U kunt problemen hebben wanneer u probeert te importeren bestaande clientinstellingen (XML) in de wizard Office 365-App installeren. U kunt de instellingen van de client zonder problemen handmatig configureren.

#### <a name="to-deploy-office-365-apps-to-clients"></a>Office 365-apps te implementeren op clients
1. Navigeer in de Configuration Manager-console naar **softwarebibliotheek** > **overzicht** > **Office 365-clientbeheer**.
2. Klik op **Office 365 Installer** in het rechter deelvenster. De Wizard Office 365-clientinstallatie wordt geopend.
3. Op de **toepassingsinstellingen** pagina, Geef een naam en beschrijving in voor de app, voer de downloadlocatie voor de bestanden en klik vervolgens op **volgende**. Houd er rekening mee dat de locatie moet worden opgegeven in het formulier &#92; &#92; *server*&#92; *delen*.
4. Op de **clientinstellingen importeren** pagina, kiezen of de clientinstellingen voor Office 365 importeren uit een bestaand XML-configuratiebestand of geef handmatig de instellingen en klik vervolgens op **volgende**.
Wanneer u een bestaand configuratiebestand hebt, geef de locatie voor het bestand en gaat u naar stap 7. Houd er rekening mee dat de locatie moet worden opgegeven in het formulier &#92; &#92; *server*&#92; *delen*&#92;* bestandsnaam*. XML.

    > [!IMPORTANT]
    >U kunt problemen hebben wanneer u probeert te importeren bestaande clientinstellingen (XML) in deze technische preview.

5. Op de **clientproducten** pagina, selecteert u de Office 365-pakket dat u gebruikt, selecteer de toepassingen die u wilt opnemen, selecteert u extra Office-producten die moeten worden opgenomen en klik vervolgens op **volgende**.
6. Op de **clientinstellingen** pagina, kiest u de instellingen wilt opnemen en klik op **volgende**.
7. Op de **implementatie** pagina, kies of u de toepassing te implementeren en klik vervolgens op **volgende**.
Als u ervoor kiest om niet te implementeren van het pakket in de wizard, gaat u naar stap 9.
8. Configureer de rest van de wizardpagina's zoals u zou voor een typische toepassingsimplementatie doen. Zie voor meer informatie [maken en implementeren van een toepassing](/sccm/apps/get-started/create-and-deploy-an-application).
9. Voltooi de wizard.
10. U kunt implementeren of de toepassing te bewerken, net zoals u zou hebben met een andere toepassing in Configuration Manager uit **softwarebibliotheek** > **overzicht** > **Toepassingsbeheer** > **toepassingen**.

>[!NOTE]
>Nadat u Office 365-apps implementeert, kunt u regels voor automatische implementatie voor het onderhouden van de apps maken. Als u wilt een ADR voor Office 365-apps maken, klikt u op **maken van een ADR**, en selecteer **Office 365 Client** wanneer u het product. Zie voor meer informatie [software-updates automatisch implementeren](/sccm/sum/deploy-use/automatically-deploy-software-updates).

## <a name="BKMK_UEFIConversion"></a>Verbeteringen voor BIOS in UEFI-conversie
U kunt nu een takenreeks voor implementatie van besturingssysteem met een nieuwe variabele TSUEFIDrive, zodat de Computer opnieuw opstarten stap overgang naar UEFI een FAT32-partitie op de harde schijf wordt voorbereid. De volgende procedure geeft een voorbeeld van hoe u takenreeksstappen voor het voorbereiden van de harde schijf voor het BIOS UEFI conversie kunt maken.

#### <a name="to-prepare-the-fat32-partition-for-the-conversion-to-uefi"></a>De FAT32-partitie voor de conversie naar UEFI voorbereiden:
In een bestaande takenreeks om een besturingssysteem te installeren, moet u een nieuwe groep met stappen om te doen het BIOS UEFI conversie toevoegen.

1. Een takenreeksgroep maken na de stappen voor het vastleggen van bestanden en instellingen en voor de stappen om het besturingssysteem te installeren. Maak bijvoorbeeld een groep na de **vastleggen van bestanden en instellingen** groep met de naam **BIOS op UEFI**.
2. Op de **opties** tabblad toevoegen van de nieuwe groep, een nieuwe takenreeksvariabele als een voorwaarde waar **_SMSTSBootUEFI** is **niet gelijk aan** naar **waar**. Dit voorkomt dat de stappen in de groep wordt uitgevoerd wanneer een computer al in UEFI-modus is.
![BIOS UEFI-groep](media/BIOS-to-UEFI-group.png)
3. Voeg onder de nieuwe groep, de **Computer opnieuw opstarten** takenreeksstap. In **aan te geven wat om uit te voeren na opnieuw opstarten**, selecteer **de opstartinstallatiekopie toegewezen aan deze takenreeks is geselecteerd** Start de computer in Windows PE.  
4. Op de **opties** tabblad, het toevoegen van een takenreeksvariabele worden uitgevoerd als een voorwaarde waar **_SMSTSInWinPE gelijk is aan false**. Hierdoor wordt voorkomen dat deze stap uitvoeren als de computer al in Windows PE is.

    ![Stap van de Computer opnieuw opstarten](media/Restart-in-Windows-PE.png)
5. Een stap voor het starten van de OEM-hulpprogramma dat de firmware van BIOS wordt converteren naar UEFI toevoegen. Dit is doorgaans een **opdrachtregel uitvoeren** takenreeksstap met een opdrachtregel te gebruiken om te starten van de OEM-hulpprogramma.
5.    Voeg de schijf formatteren en partitioneren takenreeksstap toe die wordt partitioneer en formatteer de vaste schijf. In de stap door het volgende te doen:
    1.    Maak de FAT32-partitie gebruikt die wordt omgezet in UEFI voordat het besturingssysteem wordt geïnstalleerd. Kies **GPT** voor **type schijf**.
    ![Formatteren en partitioneren schijf stap](media/Format-and-partition-disk.png)
    2.    Ga naar de eigenschappen voor de partitie FAT32. Voer **TSUEFIDrive** in de **variabele** veld. Als de takenreeks deze variabele detecteert, wordt deze voorbereiden voor de overgang UEFI voordat u de computer opnieuw opstart.
    ![Partitie-eigenschappen](media/Partition-properties.png)
    3. Maak een NTFS-partitie die de takenreeks-engine gebruikt om op te slaan de status en voor het opslaan van logboekbestanden.
6.    Voeg de **Computer opnieuw opstarten** takenreeksstap. In **aan te geven wat om uit te voeren na opnieuw opstarten**, selecteer **de opstartinstallatiekopie toegewezen aan deze takenreeks is geselecteerd** Start de computer in Windows PE.  




## <a name="intune-compliance-charts"></a>Intune compatibiliteit grafieken
In deze versie kunt u een snelle weergave van algemene compatibiliteit krijgen voor apparaten en de belangrijkste redenen voor non-compatibiliteit met behulp van nieuwe grafieken onder **werkruimte Monitoring** in de Configuration Manager-console.

#### <a name="to-view-the-intune-compliance-charts"></a>Om de compatibiliteit Intune grafieken
1. Ga in de Configuration Manager-console naar **bewaking** > **overzicht** > **compatibiliteitsinstellingen**.
2. De **algemene apparaatcompatibiliteit** grafiek wordt weergegeven.
3. Klik op de **nalevingsbeleid** knooppunt om weer te geven de **algemene apparaatcompatibiliteit** en **boven Non-compatibiliteit redenen** grafieken.

### <a name="limitations-of-intune-compliance-charts-in-tp-1609"></a>Beperkingen van Intune naleving grafieken in TP 1609
- De DrillDown voor de **algemene apparaatcompatibiliteit** grafiek momenteel er wordt een foutmelding.
- De **Top Non-compatibiliteit redenen** grafiek bevat de naam van het beleid en niet de individuele non-compatibiliteit redenen. U kunt klikken op het beleid voor inzoomen en de apparaten die niet compatibel zijn voor dat beleid zijn zichtbaar.

### <a name="try-it-out"></a>Probeer het nu
Voer de volgende secties in volgorde:

#### <a name="check-overall-compliance-chart"></a>Diagram van de algemene compatibiliteit controleren
1. Toevoegen aan twee iOS nalevingsbeleid in Configuration Manager. Een beleid moet één set met instellingen voor apparaten (bijvoorbeeld set pincodelengte 6). Het andere beleid moet een andere set-instellingen (bijvoorbeeld PINCODE complexiteit) hebben. De beleidsinstellingen moeten niet overlappen of er conflicten optreden.
2. De twee beleidsregels implementeren op een groep gebruikers.
3. Twee iOS-apparaten inschrijven in Intune met hetzelfde gebruikersaccount en een account dat het beleid in de vorige stap hebt ontvangen. De apparaten moeten niet voldoen aan de criteria van het nalevingsbeleid.
4. In Configuration Manager, Controleer de **algemene apparaatcompatibiliteit** grafiek. Beide apparaten moeten rapporteren als niet-compatibel.
<!-- 5. Click the **Non-compliant** section of the chart. Both devices should appear in the filtered view under **Assets and Compliance** > **Overview** > **Device**. -->

#### <a name="check-the-top-non-compliance-reasons-chart"></a>Controleer de bovenste Non-compatibiliteit redenen-grafiek
5. Controleer de **Top Non-compatibiliteit redenen** grafiek. Deze tabel geeft een overzicht van de top 5 redenen voor non-compatibiliteit, maar wanneer slechts twee compatibiliteitsinstellingen zijn ingesteld op beleid alleen de bovenste 2 non-compatibiliteit redenen worden weergegeven.
6. Klik op een van de secties in de grafiek. Beide apparaten moeten worden weergegeven in de gefilterde weergave onder **activa en naleving** > **overzicht** > **apparaat**.

#### <a name="make-devices-compliant-and-check-the-charts"></a>Apparaten compatibel te maken en controleer de grafieken
7. Moet een van de apparaten die compatibel zijn met een van de beleidsregels. Controleer de **algemene apparaatcompatibiliteit** grafiek opnieuw. De grafiek moet een compatibel apparaat en een niet-compatibele apparaten worden weergegeven.
8. De andere apparaat compatibel zijn met dezelfde beleidsregel maken. Hiermee maakt u een apparaat compatibel zijn met het beleid en één apparaat compatibel is met slechts één van de beleidsregels.
9. Controleer de **Top Non-compatibiliteit redenen** grafiek. Er moet een niet-naleving reden hiervoor weergegeven.
<!--7. Click the **Compliant** section of the chart. Only the compliant device should appear in the filtered view. -->





## <a name="see-also"></a>Zie ook
[Technische Preview van System Center Configuration Manager](../../core/get-started/technical-preview.md)

