---
title: Mogelijkheden van Technical Preview 1703
titleSuffix: Configuration Manager
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
caps.latest.revision: ''
author: erikje
ms.author: erikje
manager: angrobe
ms.openlocfilehash: a44d6a0c9b02a529fe8776033e58e971af37e332
ms.sourcegitcommit: 11bf4ed40ed0cbb10500cc58bbecbd23c92bfe20
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 03/27/2018
---
# <a name="capabilities-in-technical-preview-1703-for-system-center-configuration-manager"></a>Mogelijkheden van Technical Preview 1703 voor System Center Configuration Manager

*Van toepassing op: System Center Configuration Manager (Technical Preview)*

Dit artikel bevat de functies die beschikbaar in de Technical Preview voor System Center Configuration Manager, versie 1703 zijn. U kunt deze versie om te werken en nieuwe mogelijkheden toevoegen aan uw Configuration Manager technical preview-site installeren. Controleer voordat u deze versie van de technical preview installeert, de inleidende informatie [Technical Preview voor System Center Configuration Manager](../../core/get-started/technical-preview.md), om vertrouwd te raken met algemene vereisten en beperkingen voor het gebruik van een technical preview hoe bijwerken tussen versies en hoe u feedback over de functies in een technical preview.    


**Hier volgen nieuwe functies die u met deze versie kunt uitproberen.**  

## <a name="deploy-volume-purchased-ios-apps-to-device-collections"></a>Volume-purchased iOS-apps implementeren op apparaatverzamelingen

U kunt nu gelicentieerde apps implementeren op apparaten, evenals gebruikers. Afhankelijk van de apps mogelijkheid om apparaat-licentieverlening te ondersteunen, wordt een juiste licentie wordt geclaimd bij het implementeren, als volgt:

|||||
|-|-|-|-|
|Versie van Configuration Manager|App ondersteunt apparaat licentieverlening?|Implementatietype van de verzameling|De geclaimde licentie|
|Ouder dan 1702|Ja|Gebruiker|Gebruikerslicentie|
|Ouder dan 1702|Nee|Gebruiker|Gebruikerslicentie|
|Ouder dan 1702|Ja|Apparaat|Gebruikerslicentie|
|Ouder dan 1702|Nee|Apparaat|Gebruikerslicentie|
|1702 en hoger|Ja|Gebruiker|Gebruikerslicentie|
|1702 en hoger|Nee|Gebruiker|Gebruikerslicentie|
|1702 en hoger|Ja|Apparaat|Apparaatlicentie|
|1702 en hoger|Nee|Apparaat|Gebruikerslicentie|

Zie voor meer informatie over volume-purchased iOS-apps, [volume-purchased iOS-apps beheren](/sccm/mdm/deploy-use/manage-volume-purchased-ios-apps).

## <a name="direct-links-to-applications-in-software-center"></a>Directe koppelingen naar toepassingen in Software Center

U kunt nu eindgebruikers met een directe koppeling naar een toepassing in Software Center opgeven. Dit betekent dat ze niet langer moeten open Software Center en zoek naar een toepassing voordat deze kan worden geïnstalleerd. Dit is alleen beschikbaar voor Configuration Manager-toepassingen, geen pakketten en programma's of takenreeksen.

### <a name="try-it-out"></a>Try it out in                 

Gebruik de volgende URL-indeling te openen van Software Center voor een bepaalde toepassing:

**Softwarecenter:SoftwareId=*Application Identifier***

### <a name="how-to-get-the-application-identifier-of-an-application"></a>Het ophalen van de toepassings-id van een toepassing.

1.  Klik in de Configuration Manager-console op **Softwarebibliotheek**.
2.  Vouw in de werkruimte softwarebibliotheek **Toepassingsbeheer**, en klik vervolgens op **toepassingen**.
3.  In de **toepassingen** weergeven en selecteer vervolgens in de lijst met de rechtermuisknop op een van de kolomkoppen **unieke CI-ID**. Ziet u de unieke ID van elke toepassing wordt nu weergegeven in de lijst.
4.  Opmerking de **unieke CI-ID** van de toepassing die u wilt bijvoorbeeld een koppeling naar, opgeven: **ScopeId_1672B0CD-912A-4613-9BAB-D4EF2696D416/Application_970b1fef-1f38-405c-ad37-c753400b895f/2**
5.  Verwijder alle tekst in dit geval de GUID van de toepassing na **/2**. Dit laat u de met de toepassings-id.
6.  Ten slotte voor het voltooien van het construeren van de koppeling moet worden voorafgegaan door deze met **Softwarecenter:SoftwareID =**. Het bovenstaande voorbeeld gebruikt, wordt de laatste koppeling gelezen: **Softwarecenter:SoftwareId= ScopeId_1672B0CD-912A-4613-9BAB-D4EF2696D416/Application_970b1fef-1f38-405c-ad37-c753400b895f**.

Via deze koppeling kunt eindgebruikers Software Center openen rechtstreeks naar de toepassing die u hebt opgegeven.


## <a name="pfx-certificates-for-configuration-manager-windows-client-computers"></a>PFX-certificaten voor Configuration Manager Windows-clientcomputers

U kunt nu PFX-certificaatprofielen die u hebt geïmporteerd naar Configuration Manager-clientcomputers met Windows 10 implementeren.

### <a name="try-it-out"></a>Try it out in

Volg de instructies in [PFX-certificaatprofielen maken](/sccm/mdm/deploy-use/create-pfx-certificate-profiles) implementeren van het profiel voor het importeren van een PFX-profiel en controleer vervolgens of het certificaat is geïnstalleerd voor de betreffende gebruiker.



## <a name="configure-azure-services-wizard"></a>Wizard Azure-Services configureren
Technical preview 1703 introduceert de **Azure-Services configureren** wizard. Deze wizard biedt een algemene configuratie-ervaring die wordt vervangen door de afzonderlijke werkstromen voor het instellen van de cloudservices die u met Configuration Manager gebruikt. Dit wordt gedaan met behulp van een **Azure-web-app** om het abonnement en configuratie details die u anders telkens wanneer u een nieuwe Configuration Manager-component of de service met Azure instellen te verstrekken.

Met technical preview 1703 wordt alleen Windows Store voor bedrijven (WSfB) geconfigureerd met deze wizard.  Andere cloudservices worden geconfigureerd met behulp van hun afzonderlijke werkstromen.

-   Gebruik de informatie in dit onderwerp preview ter vervanging van de configuratiestappen gevonden in de [Windows Store voor bedrijven-synchronisatie instellen](/sccm/apps/deploy-use/manage-apps-from-the-windows-store-for-business#set-up-windows-store-for-business-synchronization) gedeelte van het onderwerp Current Branch [apps beheren via de Windows Store voor bedrijven met System Center Configuration Manager](/sccm/apps/deploy-use/manage-apps-from-the-windows-store-for-business).

-   Zie voor meer informatie over web-apps, [verificatie en autorisatie in Azure App Service](https://docs.microsoft.com/azure/app-service/app-service-authentication-overview), en [overzicht van Web-Apps](https://docs.microsoft.com/azure/app-service-web/app-service-web-overview).

### <a name="prerequisites-and-planning"></a>Vereisten en planning
Bij het instellen van een verbinding tussen Configuration Manager en de Windows Store voor bedrijven, moet u opgeven dat een map waarin de app-inhoud gesynchroniseerd vanuit de store worden bewaard. Om ervoor te zorgen dat deze map beveiligd is en dat de inhoud ervan kan worden geïmplementeerd op apparaten, moet dat de volgende machtigingen zijn voldaan:
-   De computer waarop u de service connection point sitesysteemrol (de site op het hoogste niveau in de hiërarchie) installeren moet beschikken over machtigingen lezen en schrijven naar de map die u hebt opgegeven bij gebruik van de **Computer$** account.  

-   De auteur van de app moet leesmachtigingen hebben voor de opgegeven map.  

-   De **Computer$** account van elke computer die als host fungeert voor een exemplaar van de SMS-Provider moet gebruikmaken van de opgegeven map.

Registreren bij Azure Active Directory, Configuration Manager als een webtoepassing of Web-API management-hulpprogramma. Hiermee maakt u de client-ID die u later nodig hebt.

### <a name="use-the-wizard-to-configure-the-wsfb-cloud-service"></a>Gebruik de wizard voor het configureren van de cloudservice WSfB

1. Ga in de console naar **beheer** > **overzicht** > **Cloud Services Management** > **Azure** > **Azure Services**, en kies vervolgens **Azure-Services configureren** starten de **Wizard Azure-Services**.

2. Op de **Azure Services** pagina, selecteert u de service die u wilt configureren en klik vervolgens op **volgende**. Met deze preview kan alleen WSfB worden geconfigureerd.

3. Op de **algemene** pagina, Geef een beschrijvende naam voor de **Azure servicenaam** en een optionele beschrijving en klik vervolgens op **volgende**.

4. Op de **App** pagina, Geef uw Azure-omgeving en klik vervolgens op **Bladeren** om de Server App-venster te openen.

5. In de **App Server** venster, selecteer de server-app die u wilt gebruiken en klik vervolgens op **OK**.
Server-apps zijn de Azure-web-apps die de configuraties voor uw Azure-account, inclusief uw Tenant-ID, Client-ID en een geheime sleutel voor clients bevatten. Als u een beschikbare server-app niet hebt, gebruikt u een van de volgende:
  - **Maak**: Klik op om een nieuwe server app **maken**. Geef een beschrijvende naam voor de app en de tenant. Vervolgens, nadat u aanmelden bij Azure, Configuration Manager maakt de web-app in Azure voor u, met inbegrip van de Client-ID en een geheime sleutel voor gebruik met de web-app. U kunt later uit de Azure-portal bekijken.
  - **Importeren**: Met een web-app die al in uw Azure-abonnement bestaat, klikt u op **importeren**. Geef een beschrijvende naam voor de app en het tenantnetwerk en geef vervolgens de Tenant-ID, Client-ID en de geheime sleutel voor de Azure-web-app die u wilt dat Configuration Manager te gebruiken. Nadat u **controleren** de gegevens, klikt u op **OK** om door te gaan.  </br></br>

6. Controleer de **informatie** pagina en eventuele extra stappen en configuraties voltooid zoals beschreven. Deze configuraties zijn nodig om de service gebruiken met Configuration Manager.
Als u bijvoorbeeld WSfB configureren:

  1. In Azure moet u Configuration Manager registreert als een webtoepassing of Web-API en vastleggen van de client-ID. U kunt ook een clientsleutel voor gebruik opgeven door het management-hulpprogramma (dit is de Configuration Manager).

  2.    In de console WSfB moet u Configuration Manager configureren als het winkelbeheerprogramma, ondersteuning voor offline gelicentieerde apps inschakelen en vervolgens ten minste één app kopen.   </br>

  Klik op **volgende** wanneer u bent klaar om door te gaan.

7. Op de **App configuraties** pagina en klik vervolgens op de app-catalogus en taal configuraties voor deze service **volgende**.
8. Nadat de wizard is voltooid, ziet u de Configuration Manager-console dat u hebt geconfigureerd **Windows Store voor bedrijven** als een **Cloud Service Type**.

U kunt nu de rest van de [Current Branch inhoud](/sccm/apps/deploy-use/manage-apps-from-the-windows-store-for-business) voor het beheren van apps uit de WSfB om te synchroniseren, maken en implementeren en controleren van Windows Store voor bedrijven-Apps.

### <a name="modify-a-cloud-service-configuration"></a>Een cloud service-configuratie wijzigen
U kunt bekijken en bewerken van de eigenschappen van een cloudservice om de configuratie wijzigen.

Ga in de console naar **beheer** > **overzicht** > **Cloud Services Management** > **Azure** > **Azure Services**, en kies vervolgens **Azure-Services configureren**, selecteert u een Cloudservice en kies vervolgens **eigenschappen**.

## <a name="convert-from-bios-to-uefi-during-an-in-place-upgrade"></a>Converteren van BIOS naar UEFI tijdens een upgrade ter plekke
Windows 10 auteurs Update introduceert een conversie van eenvoudige hulpprogramma dat automatiseert het proces voor het partitioneren van de harde schijf voor UEFI geschikte hardware en het hulpprogramma voor de conversie is geïntegreerd in de Windows 7 naar Windows 10 in-place upgradeproces. Wanneer u dit hulpprogramma worden gecombineerd met de upgradetakenreeks van uw besturingssysteem en het OEM-hulpprogramma dat de firmware van BIOS naar UEFI converteert, kunt u uw computers converteren vanuit BIOS naar UEFI tijdens een in-place upgrade naar de Update voor Windows 10 auteurs. Zie voor meer informatie [Takenreeksstappen voor het beheren van BIOS naar UEFI conversie](/sccm/osd/deploy-use/task-sequence-steps-to-manage-bios-to-uefi-conversion#convert-from-bios-to-uefi-during-an-in-place-upgrade).

## <a name="collapsible-task-sequence-groups"></a>Samenvouwbare takenreeksgroepen
Deze versie bevat de mogelijkheid om takenreeksgroepen samenvouwen uit te vouwen. U kunt uitvouwen of samenvouwen afzonderlijke groepen of groepen uitvouwen of samenvouwen alle tegelijk.


## <a name="client-settings-to-configure-windows-analytics-for-upgrade-readiness"></a>Clientinstellingen voor het configureren van Windows Analytics gereedheid voor Upgrade
Vanaf deze versie, kunt u clientinstellingen voor apparaten te vereenvoudigen, de configuratie van de Windows-telemetrie moet gebruiken [Windows Analytics](https://www.microsoft.com/en-us/WindowsForBusiness/windows-analytics) oplossingen zoals [gereedheid voor Upgrade](/sccm/core/clients/manage/upgrade/upgrade-analytics) met Configuration Manager. Configuration Manager kunt u gegevens ophalen uit Windows Analytics waarmee waardevolle inzichten in de huidige status van uw omgeving op basis van de Windows-telemetriegegevens gerapporteerd door uw clientcomputers. Windows-telemetriegegevens is gerapporteerd door clientcomputers met de Windows-service Telemetrie en vervolgens relevante gegevens vervolgens wordt overgedragen aan Windows Analytics-oplossingen die worden gehost in een van uw organisatie OMS werkruimten. Gereedheid voor upgrade is een Windows Analytics-oplossing kunt u prioriteiten nemen van beslissingen over de Windows-upgrades voor uw beheerde apparaten.

Zie voor meer informatie over de telemetrie-instellingen voor Windows [telemetrie van de configuratie van Windows in uw organisatie](https://technet.microsoft.com/itpro/windows/manage/configure-windows-telemetry-in-your-organization).

### <a name="prerequisites"></a>Vereisten
- U moet uw site voor het gebruik van de gereedheid van de Upgrade-cloudservice hebt geconfigureerd. Zie voor meer informatie [gereedheid voor Upgrade](/sccm/core/clients/manage/upgrade/upgrade-analytics)

### <a name="configure-windows-analytics-client-settings"></a>Windows Analytics clientinstellingen configureren
Voor het configureren van Windows Analytics, in de Configuration Manager-console gaat u naar **beheer** > **clientinstellingen**, dubbelklikt u op **aangepaste Apparaatclientinstellingen maken** en controleer vervolgens **Windows Analytics**.  

Configureer vervolgens de volgende na het navigeren naar de **Windows Analytics** tabblad instellingen:
- **Commerciële-ID**  
De commerciële ID sleutel maps informatie vanaf apparaten die u naar de OMS-werkruimte die als host fungeert voor Windows Analytics-gegevens van uw organisatie beheren. Als u al een commerciële ID-sleutel voor gebruik met de gereedheid van de Upgrade hebt geconfigureerd, gebruikt u die-ID. Als u nog geen een commerciële ID-sleutel, Zie [uw commerciële ID-sleutel genereren]( https://technet.microsoft.com /itpro/windows/deploy/upgrade-readiness-get-started#generate-your-commercial-id-key).

- Stel een **telemetrie niveau voor Windows 10-apparaten**   
Zie voor informatie over wat op elk Windows 10 telemetrie-niveau worden verzameld, [telemetrie van de configuratie van Windows in uw organisatie]( https://technet.microsoft.com/itpro/windows/manage/configure-windows-telemetry-in-your-organization#telemetry-levels).

- Kies voor **aanmelden voor commerciële gegevensverzameling op Windows 7, 8 en 8.1-apparaten**   
Voor informatie over de gegevens verzameld van deze besturingssystemen wanneer u meedoen, Zie downloaden de [velden en Windows 7, Windows 8 en Windows 8.1 appraiser telemetrische gebeurtenissen](https://go.microsoft.com/fwlink/?LinkID=822965) PDF-bestand van Microsoft.

- **Internet Explorer gegevensverzameling configureert** op apparaten met Windows 8.1 of eerder is Internet Explorer gegevensverzameling gereedheid voor Upgrade voor het detecteren van web-app incompatibiliteiten die voorkomen een smooth upgrade naar Windows 10 dat kunnen kunt toestaan. Internet Explorer gegevensverzameling kan worden ingeschakeld voor een per zone per internet. Zie voor meer informatie over de zones internet [over beveiligingszones](https://msdn.microsoft.com/en-us/library/ms537183(v=vs.85).aspx).