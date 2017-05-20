---
title: Mogelijkheden in Technical Preview 1703 Configuration Manager
description: Meer informatie over functies die beschikbaar zijn in de Technical Preview voor System Center Configuration Manager, versie 1703.
ms.custom: na
ms.date: 03/24/2017
ms.prod: configuration-manager
ms.technology:
- configmgr-other
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 2e801f8c-d331-41ee-8f27-908448fc0951
caps.latest.revision: 5
author: Brenduns
ms.author: brenduns
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: f4cb711f369698fe8e045f8c83dd96ec6fb29d70
ms.openlocfilehash: bb1b96a56db68dcea22270855b899ba3a90afd0d
ms.contentlocale: nl-nl
ms.lasthandoff: 05/17/2017

---
# <a name="capabilities-in-technical-preview-1703-for-system-center-configuration-manager"></a>Mogelijkheden in Technical Preview 1703 voor System Center Configuration Manager

*Van toepassing op: System Center Configuration Manager (technische Preview)*

Dit artikel worden de functies die beschikbaar in de Technical Preview voor System Center Configuration Manager, versie 1703 zijn geïntroduceerd. U kunt deze versie om te werken en nieuwe mogelijkheden toevoegen aan uw technische preview van Configuration Manager site installeren. Voordat u deze versie van de technische preview installeert, leest u de inleidende onderwerp [Technical Preview voor System Center Configuration Manager](../../core/get-started/technical-preview.md), om meer vertrouwd raken met algemene vereisten en beperkingen voor het gebruik van een technische preview hoe tussen versies en hoe u feedback geven over de functies in een technische preview bijwerken.    


**De volgende zijn nieuwe functies die u met deze versie kunt uitproberen.**  

## <a name="deploy-volume-purchased-ios-apps-to-device-collections"></a>Volume aangeschaft iOS-apps implementeren op apparaatverzamelingen

U kunt nu gelicentieerde apps implementeren op apparaten en gebruikers. Afhankelijk van de mogelijkheid apps voor ondersteuning van apparaat licentieverlening zal de juiste licentie worden gevraagd tijdens de implementatie, als volgt:

|||||
|-|-|-|-|
|Configuration Manager-versie|App apparaat licentieverlening ondersteunt?|Verzameling van implementatietype|Vermeende licentie|
|Ouder is dan 1702|Ja|Gebruiker|Gebruikerslicentie|
|Ouder is dan 1702|Nee|Gebruiker|Gebruikerslicentie|
|Ouder is dan 1702|Ja|Apparaat|Gebruikerslicentie|
|Ouder is dan 1702|Nee|Apparaat|Gebruikerslicentie|
|1702 en hoger|Ja|Gebruiker|Gebruikerslicentie|
|1702 en hoger|Nee|Gebruiker|Gebruikerslicentie|
|1702 en hoger|Ja|Apparaat|Apparaatlicentie|
|1702 en hoger|Nee|Apparaat|Gebruikerslicentie|

Zie voor meer informatie over het volume aangeschaft iOS-apps [volume aangeschaft iOS-apps beheren](/sccm/mdm/deploy-use/manage-volume-purchased-ios-apps).

## <a name="direct-links-to-applications-in-software-center"></a>Directe koppelingen naar toepassingen in Software Center

U kunt nu eindgebruikers opgeven met een directe koppeling naar een toepassing in Software Center. Dit betekent dat ze niet langer moeten openen Software Center en zoek naar een toepassing voordat ze deze kunnen installeren. Dit is alleen beschikbaar voor Configuration Manager-toepassingen, geen pakketten en programma's of takenreeksen.

### <a name="try-it-out"></a>Probeer het nu                 

Gebruik de volgende URL-indeling te openen van Software Center voor een bepaalde toepassing:

**Softwarecenter:SoftwareId =*toepassings-id***

### <a name="how-to-get-the-application-identifier-of-an-application"></a>Het ophalen van de toepassings-id van een toepassing.

1.    Klik in de Configuration Manager-console op **Softwarebibliotheek**.
2.    Vouw in de werkruimte softwarebibliotheek **Toepassingsbeheer**, en klik vervolgens op **toepassingen**.
3.    In de **toepassingen** weergeven en selecteer vervolgens in de lijst met de rechtermuisknop op een van de kolomkoppen **unieke ID configuratie-item**. U ziet de unieke ID van elke toepassing wordt nu weergegeven in de lijst.
4.    Opmerking het **unieke ID configuratie-item** van de toepassing die u wilt bijvoorbeeld een koppeling naar, geven: **ScopeId_1672B0CD-912A-4613-9BAB-D4EF2696D416/Application_970b1fef-1f38-405c-ad37-c753400b895f/2**
5.    Verwijder vervolgens alle tekst in dit geval de GUID van de toepassing na **/2**. Hierbij blijft u met de toepassings-id.
6.    Ten slotte, voor het voltooien van de koppeling te maken, plaatst u met **Softwarecenter:SoftwareID =**. In het bovenstaande voorbeeld wordt raadpleegt u de laatste koppeling: **Softwarecenter:SoftwareId = ScopeId_1672B0CD-912A-4613-9BAB-D4EF2696D416/Application_970b1fef-1f38-405c-ad37-c753400b895f**.

Via deze koppeling kunnen eindgebruikers Software Center open rechtstreeks naar de toepassing die u hebt opgegeven.


## <a name="pfx-certificates-for-configuration-manager-windows-client-computers"></a>PFX-certificaten voor Configuration Manager Windows client-computers

U kunt nu PFX-certificaatprofielen die u hebt geïmporteerd naar Configuration Manager clientcomputers met Windows 10 implementeren.

### <a name="try-it-out"></a>Probeer het nu

Volg de instructies in [PFX-certificaatprofielen maken](/sccm/mdm/deploy-use/create-pfx-certificate-profiles) implementeren van het profiel voor het importeren van een PFX-profiel en controleer of het certificaat is geïnstalleerd voor de betreffende gebruiker.



## <a name="configure-azure-services-wizard"></a>Wizard Azure-Services configureren
Technische preview 1703 introduceert de **Azure-Services configureren** wizard. Deze wizard biedt een algemene configuratie ervaring die wordt vervangen door de afzonderlijke werkstromen voor het instellen van de cloudservices die u met Configuration Manager gebruikt. Dit vindt plaats via een **Azure web-app** om het abonnement en configuratie details die u anders telkens wanneer u een nieuwe Configuration Manager-onderdeel of service met Azure instellen te bieden.

Technische preview 1703 wordt alleen Windows Store voor bedrijven (WSfB) geconfigureerd met deze wizard.  Andere cloudservices worden met hun afzonderlijke werkstromen geconfigureerd.

-    Gebruik de informatie in dit onderwerp preview ter vervanging van de configuratiestappen vinden in de [Windows Store instellen voor het synchroniseren van zakelijke](/sccm/apps/deploy-use/manage-apps-from-the-windows-store-for-business#set-up-windows-store-for-business-synchronization) gedeelte van het huidige vertakking onderwerp [apps beheren vanuit de Windows Store voor bedrijven met System Center Configuration Manager](/sccm/apps/deploy-use/manage-apps-from-the-windows-store-for-business).

-    Zie voor meer informatie over web-apps [verificatie en autorisatie in Azure App Service](https://docs.microsoft.com/azure/app-service/app-service-authentication-overview), en [Web-Apps overzicht](https://docs.microsoft.com/azure/app-service-web/app-service-web-overview).

### <a name="prerequisites-and-planning"></a>Vereisten en planning
Wanneer u een verbinding tussen Configuration Manager en de Windows Store voor bedrijven instelt, moet u een map waar app inhoud gesynchroniseerd uit het archief wordt bewaard opgeven. Om ervoor te zorgen dat deze map beveiligd is en dat de inhoud kan worden geïmplementeerd naar apparaten, moet dat de volgende machtigingen op hun plaats zijn:
-    De computer waarop u de service connection point sitesysteemrol (het hoogste niveau in de hiërarchie) installeert moet beschikken over machtigingen lezen en schrijven naar de map die u hebt opgegeven bij gebruik van de **Computer$** account.  

-    De auteur van de app moet leesmachtigingen hebben voor de opgegeven map.  

-    De **Computer$** -account van elke computer die als host fungeert voor een exemplaar van de SMS-Provider moet staat zijn om de map die u hebt opgegeven te gebruiken.

Registreren bij Azure Active Directory, Configuration Manager als een webtoepassing of Web API management-hulpprogramma. Hiermee maakt u de client-ID die u later nodig hebt.

### <a name="use-the-wizard-to-configure-the-wsfb-cloud-service"></a>Gebruik de wizard voor het configureren van de cloudservice WSfB

1. In de console, gaat u naar **beheer** > **overzicht** > **Cloud Services Management** > **Azure** > **Azure-Services**, en kies vervolgens **Azure-Services configureren** starten de **Wizard Azure-Services**.

2. Op de **Azure-Services** pagina, selecteert u de service die u wilt configureren en klik vervolgens op **volgende**. Met dit voorbeeld kan alleen WSfB worden geconfigureerd.

3. Op de **algemeen** pagina, Geef een beschrijvende naam voor de **Azure servicenaam** en een optionele beschrijving, en klik vervolgens op **volgende**.

4. Op de **App** pagina, Geef uw Azure-omgeving en klik vervolgens op **Bladeren** om de Server App-venster te openen.

5. In de **App Server** venster, selecteer de server-app die u wilt gebruiken en klik vervolgens op **OK**.
Server apps zijn de Azure web-apps met de configuraties voor uw Azure-account, inclusief de ID van uw Tenant, Client-ID en een geheime sleutel voor clients. Als u een beschikbare server-app niet hebt, gebruikt u een van de volgende:
  -    **Maak**: Klik op om een nieuwe server app **maken**. Geef een beschrijvende naam voor de app en de tenant. Klik, nadat u aanmelden voor Azure, Configuration Manager de web-app in Azure voor u gemaakt, met inbegrip van de Client-ID en een geheime sleutel voor gebruik met de web-app. Later kunt u deze vanaf de Azure-portal weergeven.
  -    **Importeren**: Met een web-app die al in uw Azure-abonnement bestaat, klikt u op **importeren**. Geef een beschrijvende naam voor de app en de tenant en geef de ID van de Tenant, Client-ID en de geheime sleutel voor de Azure web-app die u wilt dat de Configuration Manager te gebruiken. Nadat u **controleren** de gegevens, klikt u op **OK** om door te gaan.  </br></br>

6. Controleer de **informatie** pagina en eventuele extra stappen en configuraties te voltooien te gaan. Deze configuraties zijn nodig om de service gebruiken met Configuration Manager.
Bijvoorbeeld, WSfB configureren:

  1. In Azure moet u Configuration Manager registreren als een webtoepassing of Web API en noteer de client-ID. U ook opgeven een client sleutel voor gebruik door het beheerprogramma (dat Configuration Manager).

  2.    In de console WSfB moet u Configuration Manager configureren als het beheerprogramma store, schakelt u ondersteuning voor offline gelicentieerde apps en vervolgens kopen ten minste één app.   </br>

  Klik op **volgende** wanneer u bent klaar om door te gaan.

7. Op de **App configuraties** pagina en klik vervolgens op de app-catalogus en taal configuraties voor deze service **volgende**.
8. Nadat de wizard is voltooid, wordt de Configuration Manager-console bevat dat u hebt geconfigureerd **Windows Store voor bedrijven** als een **Cloud servicetype**.

U kunt nu de rest van de [huidige filiaal inhoud](/sccm/apps/deploy-use/manage-apps-from-the-windows-store-for-business) voor het beheer van apps uit de WSfB om te synchroniseren, maken en implementeren en bewaken van Windows Store voor Business-Apps.

### <a name="modify-a-cloud-service-configuration"></a>Een cloud-serviceconfiguratie wijzigen
U kunt weergeven en bewerken van de eigenschappen van een cloudservice om de configuratie te wijzigen.

In de console gaat u naar **beheer** > **overzicht** > **Cloud Services Management** > **Azure** > **Azure-Services**, en kies vervolgens **Azure-Services configureren**, selecteert u een Cloudservice en kies vervolgens **eigenschappen**.

## <a name="convert-from-bios-to-uefi-during-an-in-place-upgrade"></a>Omzetten van BIOS UEFI tijdens een upgrade ter plekke
Windows 10 beveiligingsbeheerder Update introduceert een eenvoudige conversie-hulpprogramma dat automatiseert het proces voor het partitioneren van de harde schijf voor UEFI-functionaliteit hardware en het hulpprogramma conversie integreert in de Windows 7 voor Windows 10 in-place upgradeproces. Wanneer u dit hulpprogramma worden gecombineerd met de upgrade besturingssysteemtaaksequentie en het OEM-hulpprogramma dat de firmware van BIOS naar UEFI converteert, kunt u uw computers converteren van BIOS naar UEFI tijdens een upgrade ter plekke met Windows 10 beveiligingsbeheerder Update. Zie voor meer informatie, [Takenreeksstappen voor het beheren van BIOS UEFI conversie](/sccm/osd/deploy-use/task-sequence-steps-to-manage-bios-to-uefi-conversion#convert-from-bios-to-uefi-during-an-in-place-upgrade).

## <a name="collapsible-task-sequence-groups"></a>Samenvouwbare takenreeksgroepen
Deze versie bevat de mogelijkheid om takenreeksgroepen samenvouwen uit te vouwen. U kunt uitvouwen of samenvouwen afzonderlijke groepen of groepen uitvouwen of samenvouwen alle tegelijk.


## <a name="client-settings-to-configure-windows-analytics-for-upgrade-readiness"></a>Clientinstellingen voor het configureren van Windows Analytics voor gereedheid voor Upgrade
Vanaf deze versie kunt u clientinstellingen voor apparaten vereenvoudigen de configuratie van de Windows-telemetrie nodig zijn om te gebruiken [Windows Analytics](https://www.microsoft.com/en-us/WindowsForBusiness/windows-analytics) oplossingen zoals [gereedheid voor Upgrade](/sccm/core/clients/manage/upgrade/upgrade-analytics) met Configuration Manager. Configuration Manager kan gegevens ophalen van Windows-analyse waarmee waardevolle inzichten in de huidige status van uw omgeving op basis van de Windows-telemetriegegevens gemeld door de clientcomputers. Windows-telemetriegegevens worden gerapporteerd door clientcomputers naar de Windows-service Telemetrie en vervolgens relevante gegevens vervolgens wordt overgedragen aan Windows Analytics-oplossingen die worden gehost in een van uw organisatie OMS werkruimten. Gereedheid voor upgrade is een Windows Analytics-oplossing waarmee u prioriteren nemen van beslissingen over Windows-upgrades voor uw beheerde apparaten.

Zie voor meer informatie over Windows telemetrie-instellingen [telemetrische informatie bij Windows configureren in uw organisatie](https://technet.microsoft.com/itpro/windows/manage/configure-windows-telemetry-in-your-organization).

### <a name="prerequisites"></a>Vereisten
- U moet uw site voor het gebruik van de gereedheid voor Upgrade van cloud-service hebt geconfigureerd. Zie voor meer informatie [gereedheid voor Upgrade](/sccm/core/clients/manage/upgrade/upgrade-analytics)

### <a name="configure-windows-analytics-client-settings"></a>Windows Analytics clientinstellingen configureren
Windows Analytics configureren, in de Configuration Manager-console gaat u naar **beheer** > **clientinstellingen**, dubbelklikt u op **aangepaste Apparaatclientinstellingen maken** en controleer vervolgens **Windows Analytics**.  

Configureer vervolgens de volgende na het navigeren naar de **Windows Analytics** tabblad instellingen:
- **Commerciële-ID**  
De commerciële ID sleutel maps informatie vanaf apparaten die u naar de werkruimte OMS die als host fungeert voor uw organisatie Windows analytische gegevens beheren. Als u al een commerciële ID-sleutel voor gebruik met de gereedheid van de Upgrade hebt geconfigureerd, gebruikt u ID. Als u nog geen commerciële ID sleutel, Zie [uw commerciële ID sleutel genereren]( https://technet.microsoft.com /itpro/windows/deploy/upgrade-readiness-get-started#generate-your-commercial-id-key).

- Stel een **telemetrie niveau voor Windows 10-apparaten**   
Zie voor meer informatie over wat wordt verzameld door elk Windows 10 telemetrie niveau [telemetrische informatie bij Windows configureren in uw organisatie]( https://technet.microsoft.com/itpro/windows/manage/configure-windows-telemetry-in-your-organization#telemetry-levels).

- Ervoor kiezen om te **aanmelden voor commerciële gegevensverzameling op Windows 7, 8 en 8.1-apparaten**   
Voor informatie over gegevens verzameld van deze besturingssystemen wanneer u aanmelden, Zie downloaden de [velden en Windows 7, Windows 8 en Windows 8.1 appraiser telemetrie gebeurtenissen](https://go.microsoft.com/fwlink/?LinkID=822965) pdf-bestand van Microsoft.

- **Internet Explorer gegevensverzameling configureert** op apparaten met Windows 8.1 of lager, Internet Explorer gegevensverzameling gereedheid voor Upgrade voor het detecteren van web-app incompatibiliteiten die voorkomen een goede upgrade naar Windows 10 dat kunnen kan ertoe leiden. Internet Explorer gegevensverzameling kan worden ingeschakeld in een per zone per internet. Zie voor meer informatie over internetzones [over beveiligingszones](https://msdn.microsoft.com/en-us/library/ms537183(v=vs.85).aspx).
