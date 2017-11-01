---
title: Mogelijkheden van Technical Preview 1604
titleSuffix: Configuration Manager
description: Meer informatie over functies die beschikbaar zijn in de Technical Preview voor System Center Configuration Manager, versie 1604.
ms.custom: na
ms.date: 01/23/2017
ms.prod: configuration-manager
ms.technology: configmgr-other
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 684a5559-9e6e-469b-86ae-e768e9f0c9ac
caps.latest.revision: "8"
author: Brenduns
ms.author: brenduns
manager: angrobe
robots: noindex,nofollow
ms.openlocfilehash: e632a3f4819cb2cbdaa4517b8dd0ae34fe868b3c
ms.sourcegitcommit: c236214b2fcc13dae7bad96d7fb33f692868191d
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/12/2017
---
# <a name="capabilities-in-technical-preview-1604-for-system-center-configuration-manager"></a>Mogelijkheden van Technical Preview 1604 voor System Center Configuration Manager

*Van toepassing op: System Center Configuration Manager (Technical Preview)*

Dit artikel bevat de functies die beschikbaar in de Technical Preview voor System Center Configuration Manager, versie 1604 zijn. U kunt deze versie om te werken en nieuwe mogelijkheden toevoegen aan uw Configuration Manager technical preview-site installeren.      Controleer voordat u deze versie van de technical preview installeert, de inleidende informatie [Technical Preview voor System Center Configuration Manager](../../core/get-started/technical-preview.md), om vertrouwd te raken met algemene vereisten en beperkingen voor het gebruik van een technical preview hoe bijwerken tussen versies en hoe u feedback over de functies in een technical preview.  

 Hier volgen nieuwe functies die u met deze versie kunt uitproberen.  

##  <a name="BKMK_WindowsVPP"></a>Volume-aankoopprogramma gekochte apps beheren via de Windows Store voor bedrijven  
 De [Windows Store voor bedrijven](https://www.microsoft.com/en-us/business-store) kunt u vinden en apps voor uw organisatie, kopen, afzonderlijk of in volume. De store koppelt aan Configuration Manager, kunt u volume-aankoopprogramma gekochte apps bijvoorbeeld beheren vanuit de Configuration Manager-console:  

-   U kunt de lijst met aangeschafte apps synchroniseren met Configuration Manager  

-   Apps die zijn gesynchroniseerd in de Configuration Manager-console worden weergegeven en kunt u ze vervolgens net als alle andere apps implementeren  

-   U kunt bijhouden hoeveel licenties beschikbaar zijn en hoeveel worden gebruikt in de Configuration Manager-console  

### <a name="try-it-out"></a>Probeer het nu!  

##### <a name="scenario-1-set-up-windows-store-for-business-synchronization"></a>Scenario 1: Windows Store voor bedrijven-synchronisatie instellen  

1.  Registreren bij Azure Active Directory, Configuration Manager als beheerprogramma 'Webtoepassing en/of Web-API'. Hierdoor krijgt u een client-ID die u later nodig hebt.  

    1.  In de **Active Directory** knooppunt van [https://manage.windowsazure.com](https://manage.windowsazure.com), selecteer uw Azure Active Directory en klik vervolgens op **toepassingen** > **toevoegen**.  

    2.  Klik op **mijn organisatie ontwikkelt toepassing toevoegen**.  

    3.  Voer een naam voor de toepassing, selecteer **webtoepassing** en/of **Web API**, klik vervolgens op de pijl Volgende.  

    4.  Voer dezelfde URL voor zowel de **aanmeldings-URL** en **App ID URI**.  De URL kan van alles zijn en hoeft niet omzetten in een echte adres. Bijvoorbeeld, kunt u **https://&lt;uwdomein\>/sccm**.  

    5.  Voltooi de wizard.  

2.  In Azure Active Directory, maakt u een clientsleutel voor het geregistreerde beheerprogramma.  

    1.  Markeer de toepassing die u zojuist hebt gemaakt en klik op **configureren**.  

    2.  Onder **sleutels**, selecteert u een duur in de lijst en klikt u op **opslaan**.  Hiermee wordt een nieuwe clientsleutel gemaakt.  Verlaat deze pagina totdat u is vrijgegeven Windows Store voor bedrijven naar Configuration Manager.  

3.  In de Windows Store voor bedrijven, configureert u de Configuration Manager als het winkelbeheerprogramma.  

    1.  Open [https://businessstore.microsoft.com/en-us/managementtools](https://businessstore.microsoft.com/en-us/managementtools) en meld u als u wordt gevraagd.  

    2.  Accepteer de gebruiksvoorwaarden indien nodig.  

    3.  Onder **beheerhulpprogramma's**, klikt u op **beheerprogramma toevoegen**.  

    4.  In **zoeken voor het hulpprogramma met de naam**, typ de naam van de toepassing die u eerder in Add hebt gemaakt en klik vervolgens op **toevoegen**.  

    5.  Klik op **activeren** naast de toepassing die u zojuist hebt geïmporteerd.  

    6.  In de **Apps met offline licentie weergeven** wizard, klikt u op **Ja** als u toestaan dat toepassingen offline licentie wilt aan te schaffen.  

4.  Koop ten minste één app in de Windows Store voor bedrijven.  

5.  In de **beheer** werkruimte van de Configuration Manager-console, vouw **Cloudservices**, klikt u vervolgens op **Windows Store voor bedrijven**.  

6.  Op de **Start** tabblad, in de **maken** groep, klikt u op **toevoegen Windows Store voor bedrijven-Account**.  

7.  Uw tenant-ID, client-id en clientsleutel uit Azure Active Directory toevoegen en voltooi de wizard.  

8.  Wanneer u klaar bent, ziet u het account dat u hebt geconfigureerd in de **Windows Store voor bedrijven-Accounts** in de Configuration Manager-console.  

##### <a name="scenario-2-create-and-deploy-a-configuration-manager-application-from-a-windows-store-for-business-offline-licensed-app"></a>Scenario 2: Een Configuration Manager-toepassing in een Windows Store voor bedrijven offline gelicentieerde app maken en implementeren  

1.  In de **softwarebibliotheek** werkruimte van de Configuration Manager-console, vouw **Toepassingsbeheer**, klikt u vervolgens op **licentiegegevens voor Store-Apps**.  

2.  De **aangeschafte Windows Store voor bedrijven-apps** lijst bevat een lijst met apps die zijn gesynchroniseerd vanuit de store. Kies de app die u implementeren wilt, klik op de **Start** tabblad, in de **maken** groep, klikt u op **toepassing maken**.  

3.  Een Configuration Manager-toepassing wordt gemaakt met van de Windows Store voor bedrijven-app. U kunt implementeren en bewaken van deze toepassing, net als elke andere Configuration Manager-toepassing.  

##  <a name="BKMK_PFW"></a>Verbeteringen in Microsoft Passport voor Work-beheer  
 U kunt nu Passport voor Work-beleid van domein Windows 10-apparaten worden beheerd door Configuration Manager-client implementeren.  

##  <a name="bkmk_switchsup"></a>Optie voor clients overschakelen naar een nieuw software-updatepunt  
 In de Technical Preview 1604 kunt u de optie voor Configuration Manager-clients overschakelen naar een nieuw software-updatepunt als er problemen met het actieve software-updatepunt zijn. Voor deze optie moet u meerdere software-updatepunten beschikbaar hebben op een primaire site. U deze optie inschakelt op een apparatenverzameling en eenmaal ingeschakeld, de clients in de verzameling wordt gezocht naar een ander software-updatepunt op de volgende scan als de client is mislukt om verbinding te maken met het actieve software-updatepunt. Afhankelijk van uw WSUS-instellingen (updateclassificaties, producten, enzovoort), wordt het overschakelen naar een nieuw software-updatepunt extra netwerkverkeer genereren. Gebruik deze optie daarom alleen wanneer dat nodig is.  

#### <a name="to-enable-the-option-to-switch-software-update-points"></a>De optie inschakelen om van software-updatepunt te wisselen  

1.  Klik in de Configuration Manager-console op **Activa en naleving > Overzicht > Apparaatverzamelingen**.  

2.  Klik op het tabblad **Start** in de groep **Verzameling** op **Clientmelding**en klik vervolgens op **Overschakelen naar het volgende software-updatepunt**.  

> [!NOTE]  
>  Deze optie is alleen beschikbaar op sites met meerdere software-updatepunten.  

##  <a name="bkmk_peercache"></a>Clientinstellingen voor het beheren van de clientcache-instellingen en client-Peer-Cache  
 Technical preview versie 1604 bevat twee nieuwe apparaatclientinstellingen die invloed hebben op het gebruik van een client-cache. Beide kunnen afzonderlijk worden gebruikt, maar op hetzelfde eigenschappenvenster voor clientinstellingen zijn geconfigureerd en combineren om u te helpen bij het beheren van de implementatie van inhoud aan uw clients op externe locaties.  

-   Eerst wordt **client-Peer-Cache**, een ingebouwde Configuration Manager-oplossing voor clients om inhoud te delen met andere clients rechtstreeks vanuit het lokale cachegeheugen. Voor Peer-Cache-clients om inhoud te delen, moeten ze lid zijn van dezelfde grensgroep. Peer-Cache niet vervangen en het gebruik van andere oplossingen zoals BracnchCache, maar in plaats daarvan werkt side-by-side zodat u meer opties voor het uitbreiden van de traditionele implementatieoplossingen voor inhoud zoals distributiepunten.  

     Nadat u clientinstellingen waarmee Peer-Cache op een verzameling implementeert, fungeren leden van deze verzameling als een peer-inhoudsbron voor andere clients in de grensgroep.  De client die wordt uitgevoerd als een peer content bron wordt een lijst met beschikbare inhoud verzenden deze in de cache naar het beheerpunt. Vervolgens, wanneer de volgende client in die grensgroep die inhoud aanvraagt, wordt de peer-cachebron wordt aangeboden als een mogelijke inhoudsbron samen met alle distributiepunten die zijn geconfigureerd voor het snel. De client selecteert willekeurig inhoudsbron uit deze gecombineerde pool van inhoudsbronnen. Clients inwint alleen inhoud van een distributiepunt dat is geconfigureerd voor traag verlopen wanneer er geen snelle distributiepunten of bronnen van peer-cache aanwezig zijn in de grensgroep.  

-   De tweede nieuwe instelling kunt u **beheren van de grootte van de cache** op clients. U kunt het cachegeheugen een maximale grootte in megabytes en een maximale grootte als percentage van de schijfruimte voor clients instellen.  De client gebruikt de instelling die het eerst wordt bereikt.  

U helpen bij het gebruik van de client-Peer-Cache, vindt u de **Clientgegevensbronnen** dashboard. Ga in de console naar **bewaking > clientstatus > Clientgegevensbronnen**. Hier kunt u een bepaalde periode moeten worden toegepast op het dashboard. Klik in de weergave kunt u de grensgroep of het pakket waarvoor u wilt weergeven. Wanneer u informatie bekijkt, kunt u de muisaanwijzer over het oppervlak voor meer informatie over de verschillende inhoud of het beleid bronnen.  

 U kunt ook een nieuw rapport **Clientgegevensbronnen - samenvatting**om een samenvatting van de clientgegevensbronnen van elke grensgroep weer te geven.   
**Vereisten voor Peer-Cache gebruiken:**  

-   U moet uw site configureren met een **netwerktoegangsaccount** die heeft **volledig beheer** voor de cachemap op elke client. Dit is standaard **%windir%\ccmcache**  

-   Clients kunnen alleen inhoud overdragen via Peer-Cache wanneer ze deel uitmaken van dezelfde grensgroep.  

#### <a name="to-configure-client-peer-cache-client-settings"></a>Client-Peer-Cache-clientinstellingen configureren  

1.  Beide instellingen worden geconfigureerd op dezelfde pagina van de clientinstellingen. Ga in de Configuration Manager-console naar **beheer > clientinstellingen**, en vervolgens open apparaatclientinstellingen objecten u wilt gebruiken. U kunt ook de Standaardclientinstellingen object wijzigen.  

2.  Selecteer in de lijst met beschikbare instellingen **clientcache-instellingen**.  

3.  Voor het beheren van de grootte van de cache ingesteld **clientcachegrootte configureren** gelijk zijn aan **Ja**. Vervolgens kunt u de maximale cachegrootte megabytes en als een percentage van de schijfruimte van clients configureren.  

4.  Instellen zodat clients kunnen deel uitmaken van client-Peer-Cache **inschakelen Configuration Manager-client in volledige OS in staat om inhoud te delen** gelijk zijn aan **Ja**. Vervolgens kunt u de poorten die clients gebruiken, inclusief, indien ze HTTP of HTTPS wordt configureren.  

### <a name="try-it-out"></a>Probeer het nu!  
 Voer de volgende taken uitvoeren en vervolgens met de feedbackinformatie boven aan dit onderwerp laat ons weten hoe het is gegaan:  

1.  Wijzigen van de clientinstellingen voor het opgeven van een nieuwe grootte voor het cachegeheugen van de client en bevestig deze instelling op een client.  

2.  Clientinstellingen gebruiken voor meerdere clients voor het gebruik van Peer-Cache configureren  

3.  Inhoud implementeren voor clients, zodat een aantal of de meeste clients die inhoud van een andere client ophalen met behulp van Peer-Cache.  U kunt bevestigen dat de bron van de inhoud die wordt gebruikt door nieuwe dashboard weer te geven.  

    > [!NOTE]  
    >  Voor het voltooien van deze taak met de technical preview en één distributiepunt, het distributiepunt configureert als langzaam is voor de netwerklocatie van al uw clients. Distribueer vervolgens de inhoud naar één client.  Wanneer die client de inhoud, kunt u de inhoud naar aanvullende clients die lokale peers te gebruiken als inhoudsbron voordat het distributiepunt dat is als langzaam beschouwd vanaf de locatie van de client moeten zoeken kunt distribueren.  

##  <a name="bkmk_passport"></a>Ondersteuning voor Passport for Work als een KSP  
 System Center Configuration Manager kunt u de integratie met Microsoft Passport for Work. dit een alternatieve aanmeldingsmethode waarbij Active Directory of een Azure Active Directory-account worden gebruikt is ter vervanging van een wachtwoord, smartcard of virtuele smartcard.  
Passport kunt u een gebaar van de gebruiker, in plaats van een wachtwoord gebruiken. Een gebaar van de gebruiker mogelijk een eenvoudige PINCODE, biometrische verificatie zoals Windows Hello of een extern apparaat zoals een vingerafdruklezer.  

-   U kunt de Configuration Manager gebruiken om te bepalen welke gebaren gebruikers wel en niet gebruiken om aan te melden en compexiteitsvereisten voor PINCODES te configureren.  

-   U kunt certificaten voor clientverificatie voor opslaan in de Passport for Work-sleutelarchiefprovider (KSP).  

Wanneer een gebruiker een PINCODE voor Passport maakt, verzendt Windows een melding die wordt herkend door Configuration Manager voor.  Hierdoor kan Configuration Manager te snel worden op de hoogte welke gebruikers een PINCODE voor Passport hebt gemaakt. Configuration Manager stuurt nieuwe certificaten voor deze gebruikers als Passport wordt gebruikt als de Sleutelarchiefprovider in een certificaatprofiel.  

##  <a name="bkmk_onpremdha"></a>On-premises Apparaatstatusverklaring  
 De statusverklaring voor Windows 10-apparaten kan nu worden geconfigureerd om te communiceren met de on-premises infrastructuur.  Beheerders kunnen opgeven of rapportage wordt uitgevoerd via de cloud of on-premises resources.  Als **lokale** is geselecteerd voor statusverklaringen, wordt een URI worden opgegeven voor de service. Hierdoor kunnen client-pc's zonder internettoegang inschakelen en beheren met behulp van de health attestation van apparaten.  

#### <a name="enable-health-attestation-for-on-premises-devices"></a>Statusverklaringen inschakelen voor on-premises apparaten  

1.  Navigeer in de Configuration Manager-console naar **Beheer** > **Overzicht** > **Clientinstellingen**en stel **On-premises statusverklaringsservice** gebruiken in op **Ja**.  

2.  Geef de **URL op voor de on-premises statusverklaringsservice**en klik op **OK**.  

Probeer het uit configureren met behulp van clientagentinstellingen van lokale Health Attestation-Service.  

##  <a name="BKMK_Smart"></a>SmartLock-instelling voor Android-apparaten  
 Een nieuwe instelling **toestaan Smart LOCK en andere vertrouwde agents** is toegevoegd aan de **Android en Samsung KNOX** configuratie-item waarmee u de Smart Lock-functie op compatibele Android-apparaten beheren. Met deze telefoonmogelijkheid (soms ook wel vertrouwde agent genoemd) kunt u het vergrendelingsschermwachtwoord op het apparaat uitschakelen of overslaan als het zich op een vertrouwde locatie bevindt, zoals wanneer het is verboden met een bepaald Bluetooth-apparaat, of wanneer het zich in de buurt bevindt van een NFC-tag. U kunt deze instelling gebruiken om te voorkomen dat eindgebruikers Smart LOCK configureren.  
