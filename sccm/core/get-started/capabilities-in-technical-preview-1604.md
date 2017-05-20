---
title: Mogelijkheden in Technical Preview 1604 Configuration Manager
description: Meer informatie over functies die beschikbaar zijn in de Technical Preview voor System Center Configuration Manager, versie 1604.
ms.custom: na
ms.date: 01/23/2017
ms.prod: configuration-manager
ms.technology:
- configmgr-other
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 684a5559-9e6e-469b-86ae-e768e9f0c9ac
caps.latest.revision: 8
author: Brenduns
ms.author: brenduns
manager: angrobe
robots: noindex,nofollow
ms.translationtype: Machine Translation
ms.sourcegitcommit: dab5da5a4b5dfb3606a8a6bd0c70a0b21923fff9
ms.openlocfilehash: 26b0d8ea7b3e841c48945df55f8860394a98a29f
ms.contentlocale: nl-nl
ms.lasthandoff: 05/17/2017

---
# <a name="capabilities-in-technical-preview-1604-for-system-center-configuration-manager"></a>Mogelijkheden in Technical Preview 1604 voor System Center Configuration Manager

*Van toepassing op: System Center Configuration Manager (technische Preview)*

Dit artikel worden de functies die beschikbaar in de Technical Preview voor System Center Configuration Manager, versie 1604 zijn geïntroduceerd. U kunt deze versie om te werken en nieuwe mogelijkheden toevoegen aan uw technische preview van Configuration Manager site installeren.      Voordat u deze versie van de technische preview installeert, leest u de inleidende onderwerp [Technical Preview voor System Center Configuration Manager](../../core/get-started/technical-preview.md), om meer vertrouwd raken met algemene vereisten en beperkingen voor het gebruik van een technische preview hoe tussen versies en hoe u feedback geven over de functies in een technische preview bijwerken.  

 De volgende zijn nieuwe functies die u met deze versie kunt uitproberen.  

##  <a name="BKMK_WindowsVPP"></a>Volume aangeschaft apps vanuit de Windows Store voor bedrijven beheren  
 De [Windows Store voor bedrijven](https://www.microsoft.com/en-us/business-store) kunt u vinden en apps koopt voor uw organisatie, afzonderlijk of in volume. Verbinding maken met de store naar de Configuration Manager, kunt u beheren volume aangeschaft apps vanuit de Configuration Manager-console, bijvoorbeeld:  

-   U kunt de lijst met aangekochte apps te synchroniseren met Configuration Manager  

-   Apps die zijn gesynchroniseerd, worden weergegeven in de Configuration Manager-console en u kunt deze net als andere apps implementeren  

-   U kunt volgen hoeveel licenties beschikbaar zijn en hoeveel al worden gebruikt in de Configuration Manager-console  

### <a name="try-it-out"></a>Probeer het nu!  

##### <a name="scenario-1-set-up-windows-store-for-business-synchronization"></a>Scenario 1: Windows Store voor het synchroniseren van zakelijke instellen  

1.  Registreren bij Azure Active Directory, Configuration Manager als een "Web Application en/of Web API" management-hulpprogramma. Hiermee krijgt u een client-ID die u later nodig hebt.  

    1.  In de **Active Directory** knooppunt van [https://manage.windowsazure.com](https://manage.windowsazure.com), selecteer uw Azure Active Directory en klik vervolgens op **toepassingen** > **toevoegen**.  

    2.  Klik op **toevoegen van een toepassing die het ontwikkelen van mijn organisatie**.  

    3.  Voer een naam voor de toepassing, selecteer **webtoepassing** en/of **Web API**, klikt u op de volgende pijl.  

    4.  Geef dezelfde URL voor zowel de **aanmelding URL** en **App-ID-URI**.  De URL kan en hoeft niet te herleiden tot een echte adres. Bijvoorbeeld, kunt u **https://&lt;uwdomein\>/sccm**.  

    5.  Voltooi de wizard.  

2.  In Azure Active Directory, een client-sleutel voor het geregistreerde beheerprogramma te maken.  

    1.  Markeer de toepassing die u zojuist hebt gemaakt en klik op **configureren**.  

    2.  Onder **sleutels**, selecteer een duur in de lijst en klikt u op **opslaan**.  Hiermee wordt een nieuwe sleutel van de client gemaakt.  Geen verlaat deze pagina totdat u is vrijgegeven Windows Store voor bedrijven aan Configuration Manager hebt.  

3.  In de Windows Store voor bedrijven, configureert u Configuration Manager als het beheerprogramma store.  

    1.  Open [https://businessstore.microsoft.com/en-us/managementtools](https://businessstore.microsoft.com/en-us/managementtools) en aanmelden als u wordt gevraagd.  

    2.  Accepteer de gebruiksvoorwaarden indien nodig.  

    3.  Onder **beheerhulpprogramma's**, klikt u op **toevoegen van een beheerprogramma**.  

    4.  In **zoekt u het hulpprogramma met de naam**, typ de naam van de toepassing die u eerder hebt in AAD gemaakt en klik vervolgens op **toevoegen**.  

    5.  Klik op **activeren** naast de toepassing die u zojuist hebt geïmporteerd.  

    6.  In de **Show Offline-Licensed Apps** wizard, klikt u op **Ja** als u toestaan dat offline gelicentieerde-toepassingen wilt te kopen.  

4.  Koop ten minste één vanuit de Windows Store voor bedrijven.  

5.  In de **beheer** werkruimte van de Configuration Manager-console, vouw **Cloudservices**, klikt u vervolgens op **Windows Store voor bedrijven**.  

6.  Op de **Start** tabblad, in de **maken** groep, klikt u op **toevoegen Windows Store voor bedrijven-Account**.  

7.  Uw tenant-ID, de client-id en de client sleutel toevoegen van Azure Active Directory en voltooi de wizard.  

8.  Nadat u klaar bent, ziet u het account dat u hebt geconfigureerd in de **Windows Store voor zakelijke Accounts** lijst in de Configuration Manager-console.  

##### <a name="scenario-2-create-and-deploy-a-configuration-manager-application-from-a-windows-store-for-business-offline-licensed-app"></a>Scenario 2: Een Configuration Manager-toepassing in een Windows Store voor zakelijke offline gelicentieerde app maken en implementeren  

1.  In de **softwarebibliotheek** werkruimte van de Configuration Manager-console, vouw **Toepassingsbeheer**, klikt u vervolgens op **licentie-informatie voor de Store-Apps**.  

2.  De **aangeschaft Windows Store voor Business-apps** lijst bevat een lijst met apps die zijn gesynchroniseerd met de store. Kies de app die u implementeren wilt, klik op de **Start** tabblad, in de **maken** groep, klikt u op **toepassing maken**.  

3.  Een Configuration Manager-toepassing wordt gemaakt met de Windows Store voor Business-app. U kunt vervolgens implementeren en controleren van deze toepassing als u een andere Configuration Manager-toepassing.  

##  <a name="BKMK_PFW"></a>Verbeteringen in Microsoft Passport voor werkstroombeheer  
 Nu u paspoort voor werk beleid voor het domein Windows 10-apparaten worden beheerd door de Configuration Manager-client.  

##  <a name="bkmk_switchsup"></a>Optie voor clients overschakelen naar een nieuw software-updatepunt  
 U kunt de optie voor Configuration Manager-clients in te schakelen naar een nieuw software-updatepunt wanneer er problemen met het actieve software-updatepunt zijn inschakelen in de Technical Preview 1604. Voor deze optie moet u meerdere software-updatepunten beschikbaar op een primaire site hebben. U Schakel deze optie op een apparatenverzameling en eenmaal ingeschakeld, de clients in de verzameling zoeken naar een ander software-updatepunt op de volgende scan wanneer de client kan geen verbinding maken met het actieve software-updatepunt. Afhankelijk van uw WSUS-instellingen (updateclassificaties, producten, enz.), wordt het overschakelen naar een nieuw software-updatepunt aanvullende netwerkverkeer genereren. Gebruik deze optie daarom alleen wanneer dat nodig is.  

#### <a name="to-enable-the-option-to-switch-software-update-points"></a>De optie inschakelen om van software-updatepunt te wisselen  

1.  Klik in de Configuration Manager-console op **Activa en naleving > Overzicht > Apparaatverzamelingen**.  

2.  Klik op het tabblad **Start** in de groep **Verzameling** op **Clientmelding**en klik vervolgens op **Overschakelen naar het volgende software-updatepunt**.  

> [!NOTE]  
>  Deze optie is alleen beschikbaar op sites met meerdere software-updatepunten.  

##  <a name="bkmk_peercache"></a>Clientinstellingen voor het beheren van de clientcache-instellingen en client-Peercache  
 Technische preview-versie 1604 bevat twee nieuwe client apparaatinstellingen die van invloed op het gebruik van een client-cache. Beide afzonderlijk kunnen worden gebruikt, maar zijn geconfigureerd in het eigenschappenvenster dezelfde voor clientinstellingen en combineren om u te helpen bij het beheren van de implementatie van inhoud aan uw clients op externe locaties.  

-   Eerst wordt **client-Peercache**, een ingebouwde Configuration Manager-oplossing voor clients inhoud te delen met andere clients rechtstreeks vanuit de lokale cache. Voor Peer-Cache-clients inhoud te delen, moeten ze lid van dezelfde grensgroep. Peercache is geen vervanging voor het gebruik van andere oplossingen zoals BracnchCache, maar in plaats daarvan werkt side-by-side zodat u meer opties traditionele inhoudsdistributie oplossingen zoals distributiepunten uit te breiden.  

     Nadat u clientinstellingen die Peer-Cache op een verzameling inschakelen hebt geïmplementeerd, kunnen leden van deze verzameling fungeren als een peer-inhoudsbron voor andere clients in de grensgroep.  De client die fungeert als een peer content bron wordt een lijst met beschikbare inhoud verzenden deze is in de cache opgeslagen naar het beheerpunt. Wanneer de volgende client in die grensgroep die inhoud aanvraagt, wordt de bron van de cache peer vervolgens als een mogelijke inhoudsbron samen met alle distributiepunten die zijn geconfigureerd om snel aangeboden. De client selecteert een willekeurige inhoudsbron van deze gecombineerde groep inhoudsbronnen. Clients inwint alleen inhoud van een distributiepunt dat is geconfigureerd voor traag verlopen wanneer er geen snelle distributiepunten of peer cache bronnen aanwezig zijn in de grensgroep.  

-   De tweede nieuwe instelling kunt u **beheren van de grootte van de cache** op clients. U kunt instellen dat de cache hebben een maximale grootte in MB en een maximale grootte als percentage van de schijfruimte van clients.  De client vereist de instelling die het eerst wordt bereikt.  

U helpen bij het gebruik van client-Peercache, vindt u de **Client gegevensbronnen** dashboard. In de console gaat u naar **bewaking > clientstatus > gegevensbronnen Client**. Hier kunt u een bepaalde periode te kunnen toepassen op het dashboard. Klik in de weergave kunt u de grensgroep of het pakket waarvoor u wilt weergeven. Wanneer informatie bekijkt, kunt u de muis de muisaanwijzer op het oppervlak voor meer informatie over de verschillende inhoud of bronnen van beleid.  

 U kunt ook een nieuw rapport **gegevensbronnen voor Client - samenvatting**om weer te geven van een samenvatting van de client-gegevensbronnen voor elke grensgroep.   
**Vereisten voor Peer-Cache gebruiken:**  

-   Moet u uw site met een **netwerktoegangsaccount** waarvoor **volledig beheer** naar de cachemap op elke client. Dit is standaard **%windir%\ccmcache**  

-   Clients kunnen alleen inhoud met behulp van Peer-Cache wanneer ze deel uitmaken van dezelfde grensgroep worden overgedragen.  

#### <a name="to-configure-client-peer-cache-client-settings"></a>Peer-clientcache clientinstellingen configureren  

1.  Beide instellingen zijn geconfigureerd op dezelfde pagina van de clientinstellingen. Ga in de Configuration Manager-console naar **beheer > clientinstellingen**, en vervolgens open apparaatclientinstellingen object u wilt gebruiken. U kunt ook de Standaardclientinstellingen object wijzigen.  

2.  Selecteer in de lijst met beschikbare instellingen **clientcache-instellingen**.  

3.  Instellen voor het beheren van de grootte van de cache **configureren van client-cachegrootte** gelijk zijn aan **Ja**. Vervolgens kunt u de maximale cachegrootte voor beide megabytes en als een percentage van de schijfruimte van clients.  

4.  Ingesteld zodat clients deelnemen aan client-Peercache **inschakelen Configuration Manager-client in een volledig besturingssysteem inhoud te delen** gelijk zijn aan **Ja**. Vervolgens kunt u de poorten die clients gebruiken, inclusief, indien ze HTTP of HTTPS zullen.  

### <a name="try-it-out"></a>Probeer het nu!  
 Probeer de volgende taken uitvoeren en vervolgens de feedbackgegevens boven in dit onderwerp gebruiken om te laat ons weten hoe het werkt:  

1.  Wijzigen van de clientinstellingen voor het opgeven van een nieuwe grootte voor het cachegeheugen van de client en bevestig deze instelling op een client.  

2.  Clientinstellingen gebruiken voor het configureren van meerdere clients voor het gebruik van Peer-Cache  

3.  Inhoud implementeren voor clients, zodat een aantal of de meeste clients die inhoud van een andere client via Peer-Cache.  U kunt bevestigen dat de inhoudsbron die wordt gebruikt door nieuwe dashboard weer te geven.  

    > [!NOTE]  
    >  Om deze taak met de technische preview en een enkel distributiepunt, het distributiepunt configureert als langzaam voor de netwerklocatie van alle clients. Vervolgens de inhoud distribueert naar één client.  Nadat de client de inhoud opgehaald, kunt u de inhoud distribueert naar extra clients die lokale peers te gebruiken als inhoudsbron voordat u het distributiepunt dat wordt beschouwd als langzaam vanaf de locatie van de client te vinden.  

##  <a name="bkmk_passport"></a>Ondersteuning voor Passport for Work als een Sleutelarchiefprovider  
 System Center Configuration Manager kunt u integreren met Microsoft Passport for Work is een alternatieve-toegestane aanmeldingsmethode die gebruikmaakt van Active Directory of Azure Active Directory-account een wachtwoord, smartcard of virtuele smartcard vervangen.  
Passport kunt u een beweging van de gebruiker aanmelden, in plaats van een wachtwoord gebruiken. Een beweging van de gebruiker is mogelijk een eenvoudige PINCODE of biometrische verificatie, zoals Windows Hello een extern apparaat zoals een vingerafdruklezer.  

-   U kunt de Configuration Manager gebruiken om te bepalen welke gebaren gebruikers kunnen en aan te melden en configureren van PINCODE complexiteitsvereisten voldoen niet gebruiken.  

-   U kunt certificaten voor serververificatie opslaan in de Passport for Work sleutelarchiefprovider (KSP).  

Wanneer een gebruiker een PINCODE voor Passport maakt, stuurt Windows een melding dat Configuration Manager voor luistert.  Hiermee wordt Configuration Manager om te snel worden op de hoogte van welke gebruikers een PINCODE voor Passport hebt gemaakt. Configuration Manager kunnen vervolgens ook nieuwe certificaten uitgeven voor deze gebruikers als Passport als de opslagprovider sleutel in het certificaatprofiel van een wordt gebruikt.  

##  <a name="bkmk_onpremdha"></a>On-premises apparaat Health Attestation-bewerking  
 Health-verklaring voor Windows 10-apparaten kan nu worden geconfigureerd om te communiceren met de on-premises infrastructuur.  Beheerders kunnen opgeven of reporting vindt plaats via de cloud of on-premises resources.  Als **lokale** health attestation rapporten is geselecteerd, wordt een URI voor de service kan worden opgegeven. Hierdoor kunnen client-pc's zonder internettoegang inschakelen en apparaten beheren met behulp van status Attestation-bewerking.  

#### <a name="enable-health-attestation-for-on-premises-devices"></a>Health-verklaring voor lokale apparaten inschakelen  

1.  Navigeer in de Configuration Manager-console naar **Beheer** > **Overzicht** > **Clientinstellingen**en stel **On-premises statusverklaringsservice** gebruiken in op **Ja**.  

2.  Geef de **URL op voor de on-premises statusverklaringsservice**en klik op **OK**.  

Om te proberen het uit, lokale Attestation statusservice agent-instellingen te configureren.  

##  <a name="BKMK_Smart"></a>SmartLock-instelling voor Android-apparaten  
 Een nieuwe instelling **SmartLock toestaan en andere vertrouwen agents** is toegevoegd aan de **Android en Samsung KNOX** configuratie-item dat u kunt de functie SmartLock op Android-compatibele apparaten beheren. Met deze telefoonmogelijkheid (soms ook wel vertrouwde agent genoemd) kunt u het vergrendelingsschermwachtwoord op het apparaat uitschakelen of overslaan als het zich op een vertrouwde locatie bevindt, zoals wanneer het is verboden met een bepaald Bluetooth-apparaat, of wanneer het zich in de buurt bevindt van een NFC-tag. U kunt deze instelling gebruiken om te voorkomen dat eindgebruikers SmartLock configureren.  

