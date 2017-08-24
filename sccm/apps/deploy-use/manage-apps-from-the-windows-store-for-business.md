---
title: Apps beheren via de Windows Store voor bedrijven | Microsoft Docs
description: Beheren en implementeren van apps uit de Windows Store voor bedrijven met behulp van System Center Configuration Manager.
ms.custom: na
ms.date: 7/31/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: configmgr-app
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 8cdb22a6-72d7-41f5-9bed-c098b1bcf675
caps.latest.revision: "11"
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.openlocfilehash: 369b6a82a20a90ca534f9484c0be71096dd35a30
ms.sourcegitcommit: 51fc48fb023f1e8d995c6c4eacfda7dbec4d0b2f
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 08/07/2017
---
# <a name="manage-apps-from-the-windows-store-for-business-with-system-center-configuration-manager"></a>Apps beheren via de Windows Store voor Bedrijven met System Center Configuration Manager
De [Windows Store voor bedrijven](https://www.microsoft.com/business-store) kunt u vinden en Windows-apps voor uw organisatie, kopen, afzonderlijk of in volume. De store koppelt aan Configuration Manager, kunt u de lijst met apps die u hebt aangeschaft synchroniseren met Configuration Manager. U kunt deze apps bekijken in de Configuration Manager-console, en deze implementeren zoals u zou ook een andere app implementeren.


## <a name="online-and-offline-apps"></a>Online en offline apps

De Windows Store voor bedrijven ondersteunt twee typen app:

- **Online** -dit licentietype is vereist voor gebruikers en apparaten verbinding maken met de store om op te halen van een app en de licentie. Windows 10-apparaten moet Azure Active Directory domein.
- **Offline** -kunt u apps in cache en licenties voor het implementeren van rechtstreeks vanuit uw on-premises netwerk zonder verbinding te maken met de store of het hebben van een verbinding met Internet.

[Lees meer](https://technet.microsoft.com/itpro/windows/whats-new/windows-store-for-business-overview?f=255&MSPPError=-2147217396) over de Windows Store voor bedrijven.

Configuration Manager ondersteunt het beheer van Windows Store voor bedrijven-apps op zowel Windows 10-apparaten waarop de Configuration Manager-client wordt uitgevoerd, en Windows 10-apparaten die zijn geregistreerd bij Microsoft Intune (ook wel een hybride configuratie genoemd). Configuration Manager biedt de volgende mogelijkheden voor online en offline apps.

> [!IMPORTANT]
> Voor het gebruik van deze mogelijkheid Windows 10-apparaten moeten worden uitgevoerd de release van November 2015 (1511) of hoger.


|Mogelijkheid|Offline apps|Online-apps|
|------------|------------|------------|
|Synchroniseren van app-gegevens naar Configuration Manager<br>(synchronisatie wordt uitgevoerd om de 24 uur)|Ja|Ja|
|Configuration Manager-toepassingen maken vanuit de store-apps|Ja|Ja|
|Ondersteuning voor gratis apps uit de store|Ja|Ja|
|Ondersteuning voor betaalde apps uit de store|Nee|Ja|
|Ondersteuning voor vereiste implementaties voor verzamelingen gebruikers of apparaten|Ja|Ja|
|Ondersteuning voor beschikbare implementaties voor verzamelingen gebruikers of apparaten|Ja|Ja|
|Ondersteuning voor line-of-business-apps uit de store|Ja|Ja|

Als u wilt implementeren online gelicentieerde apps op Windows 10-pc's met de Configuration Manager-client, ze moeten worden uitgevoerd de Update voor Windows 10 maken, of later.

## <a name="deploying-online-apps-using-the-windows-store-for-business-with-pcs-that-run-the-configuration-manager-client"></a>Implementatie van online-apps met behulp van de Windows Store voor bedrijven met pc's waarop de Configuration Manager-client wordt uitgevoerd
Voordat het implementeren van Windows Store voor bedrijven-apps op pc's waarop de volledige Configuration Manager-client wordt uitgevoerd, moet u de volgende punten:

- Voor volledige functionaliteit pc's moeten worden uitgevoerd de Update auteurs van Windows 10 of hoger.
- Pc's moeten zijn voor Azure Active Directory werkplek toegevoegd en worden in dezelfde AAD-tenant waar u de Windows Store voor bedrijven als beheerprogramma geregistreerd.
- Wanneer u pc's bent aangemeld met het ingebouwde Administrator-account, geen ze toegang tot Windows Store voor bedrijven-apps.
- Pc's moeten een actieve internetverbinding hebben tot de Windows Store voor bedrijven.

### <a name="notes-for-pcs-running-earlier-versions-of-windows-10"></a>Opmerkingen voor pc's met eerdere versies van Windows 10
Op computers met een versie van Windows 10 ouder is dan de beveiligingsbeheerder Update (met de Configuration Manager-client), geldt de volgende functionaliteit:


- Wanneer de installatie wordt uitgevoerd door de gebruiker de toepassing te installeren, door de toepassing de installatiedeadline wordt bereikt of door na installatie van nieuwe evaluatie voor vereiste implementaties:
    - De toepassing wordt 'afgedwongen' door de Windows Store voor bedrijven-app te starten. 
    - De gebruiker moet vervolgens de installatie vanuit de store voltooien voordat de app is geïnstalleerd
    - De status van de toepassing in de Configuration Manager-console rapporten is mislukt met de fout 'de Windows Store-app op de client-PC is geopend en wacht tot de gebruiker om de installatie te voltooien.'
- Bij de volgende beoordelingscyclus van toepassing:
    - Als de toepassing is geïnstalleerd door de gebruiker uit de store, de toepassing meldt de Status **geslaagd**. 
    - Als de gebruiker heeft niet geprobeerd de app te installeren vanuit de store:
        - Vereiste implementaties poging tot het starten van de store en het afdwingen van de installatie van de toepassing opnieuw.
        - Beschikbare implementaties niet opnieuw worden afgedwongen.

#### <a name="further-notes-for-pcs-running-earlier-versions-of-windows-10"></a>Aanvullende opmerkingen voor pc's met eerdere versies van Windows 10:

- U kunt geen line-of-business-apps uit de Windows Store voor bedrijven implementeren
- Wanneer u een betaalde apps uit de store implementeert, moet de eindgebruikers aanmelden bij de store en de aankoop van de app zelf.
- Als u een Groepsbeleid uit te schakelen toegang hebt geïmplementeerd naar de consumentenversie van de Windows Store, werkt implementaties uit de Windows Store voor bedrijven niet, zelfs als de Windows Store voor bedrijven is ingeschakeld.


## <a name="set-up-windows-store-for-business-synchronization"></a>Windows Store voor bedrijven-synchronisatie instellen

### <a name="for-configuration-manager-versions-prior-to-1706"></a>Voor eerdere versies 1706 Configuration Manager

**Registreren bij Azure Active Directory, Configuration Manager als beheerprogramma 'Webtoepassing en/of Web-API'. Deze actie geeft u een client-ID die u later nodig.**
1. In het Active Directory-knooppunt van [https://manage.windowsazure.com](https://manage.windowsazure.com), selecteer uw Azure Active Directory en klik vervolgens op **toepassingen** > **toevoegen**.
2.  Klik op **mijn organisatie ontwikkelt toepassing toevoegen**.
3.  Voer een naam voor de toepassing, selecteer **webtoepassing** en/of **Web API**, klikt u vervolgens op de **volgende** pijl.
4.  Voer dezelfde URL voor zowel de **aanmeldings-URL** en **App ID URI**. De URL kan van alles zijn en hoeft niet omzetten in een echte adres. Bijvoorbeeld, kunt u *https://yourdomain/sccm*.
5.  Voltooi de wizard.

**Maak in Azure Active Directory een clientsleutel voor het geregistreerde beheerprogramma**
1.  Markeer de toepassing die u hebt gemaakt en klik op **configureren**.
2.  Onder **sleutels**, selecteert u een duur in de lijst en klik vervolgens op **opslaan**. Deze actie wordt een nieuwe clientsleutel gemaakt. Verlaat deze pagina totdat u is vrijgegeven de Windows Store voor bedrijven naar Configuration Manager.

**In de Windows Store voor bedrijven, Configuration Manager configureren als het winkelbeheerprogramma**
1.  Open [https://businessstore.microsoft.com/en-us/managementtools](https://businessstore.microsoft.com/en-us/managementtools) en meld u als u wordt gevraagd.
2.  Accepteer de gebruiksvoorwaarden als aangevraagd.
3.  Onder **beheerhulpprogramma's**, klikt u op **beheerprogramma toevoegen**.
4.  In **zoeken voor het hulpprogramma met de naam**, typ de naam van de toepassing die u eerder in Add hebt gemaakt en klik vervolgens op **toevoegen**.
5.  Klik op **activeren** naast de toepassing die u hebt geïmporteerd.
6.  In de **beheren > accountgegevens** pagina **Apps met offline licentie weergeven** als u toestaan dat apps offline licentie wilt aan te schaffen.

**De store-account toevoegen aan Configuration Manager**

1. Zorg ervoor dat u ten minste één app in de Windows Store voor bedrijven hebt aangeschaft. In de **beheer** werkruimte van de Configuration Manager-console, vouw **Cloudservices**, klikt u vervolgens op **Windows Store voor bedrijven**.
2.  Op de **Start** tabblad, in de **Windows Store voor bedrijven** groep, klikt u op **toevoegen Windows Store voor bedrijven-Account**. 
3.  Uw tenant-ID, client-id en clientsleutel uit Azure Active Directory toevoegen en voltooi de wizard.
4. Wanneer u klaar bent, ziet u het account dat u hebt geconfigureerd in de **Windows Store voor bedrijven** in de Configuration Manager-console.

### <a name="for-configuration-manager-version-1706-and-later"></a>Voor Configuration Manager versie 1706 en hoger

1. Ga in de console naar **beheer** > **overzicht** > **Cloud Services Management** > **Azure** > **Azure Services**, en kies vervolgens **Azure-Services configureren** starten de **Wizard Azure-Services**.
2. Op de **Azure Services** pagina, selecteert u de service die u wilt configureren en klik vervolgens op **volgende**.
3. Op de **algemene** pagina, Geef een beschrijvende naam voor de naam van de Azure-service en een optionele beschrijving en klik vervolgens op **volgende**.
4. Op de **App** pagina, Geef uw Azure-omgeving en klik vervolgens op **Bladeren** openen de **App Server** venster.
5. In de **App Server** venster, selecteer de server-app die u wilt gebruiken en klik vervolgens op **OK**. Server-apps zijn de Azure-web-apps die de configuraties voor uw Azure-account, inclusief uw Tenant-ID, Client-ID en een geheime sleutel voor clients bevatten. Als u een beschikbare server-app niet hebt, gebruikt u een van de volgende:
    - **Maken:** Klik op om een nieuwe server app **maken**. Geef een beschrijvende naam voor de app en de tenant. Vervolgens, nadat u aanmelden bij Azure, Configuration Manager maakt de web-app in Azure voor u, met inbegrip van de Client-ID en een geheime sleutel voor gebruik met de web-app. U kunt later uit de Azure-portal bekijken.
    - **Importeren:** Met een web-app die al in uw Azure-abonnement bestaat, klikt u op **importeren**. Geef een beschrijvende naam voor de app en het tenantnetwerk en geef vervolgens de Tenant-ID, Client-ID en de geheime sleutel voor de Azure-web-app die u wilt dat Configuration Manager te gebruiken. Nadat u **controleren** de gegevens, klikt u op **OK** om door te gaan. 
6. Controleer de **informatie** pagina en eventuele extra stappen en configuraties voltooid zoals beschreven. Deze configuraties zijn nodig om de service gebruiken met Configuration Manager. Als u bijvoorbeeld de Windows Store voor bedrijven configureren:
    - In Azure moet u Configuration Manager registreert als een webtoepassing of Web-API en vastleggen van de client-ID. U kunt ook een clientsleutel voor gebruik opgeven door het management-hulpprogramma (dit is de Configuration Manager).
    - In de Windows Store voor bedrijven-console moet u Configuration Manager configureren als het winkelbeheerprogramma, ondersteuning voor offline gelicentieerde apps inschakelen en vervolgens ten minste één app kopen. 
7. Klik op **volgende** wanneer u bent klaar om door te gaan.
8. Op de **App configuraties** pagina en klik vervolgens op de app-catalogus en taal configuraties voor deze service **volgende**.
9. Nadat de wizard is voltooid, ziet u de Configuration Manager-console dat u hebt geconfigureerd **Windows Store voor bedrijven** als een **Cloud Service Type**.




## <a name="create-and-deploy-a-configuration-manager-application-from-a-windows-store-for-business-app"></a>Maken en implementeren van een Configuration Manager-toepassing in een Windows Store voor bedrijven-app.
1.  In de **softwarebibliotheek** werkruimte van de Configuration Manager-console, vouw **Toepassingsbeheer**, klikt u vervolgens op **licentiegegevens voor Store-Apps**.
2.  Kies de app die u implementeren wilt, klik op de **Start** tabblad, in de **maken** groep, klikt u op **toepassing maken**.
Een Configuration Manager-toepassing wordt gemaakt met van de Windows Store voor bedrijven-app. U kunt implementeren en bewaken van deze toepassing, net als elke andere Configuration Manager-toepassing.

> [!IMPORTANT]
> Voor apparaten die zijn ingeschreven bij Intune, zijn geïmplementeerde apps alleen beschikbaar voor de gebruiker die het apparaat oorspronkelijk ingeschreven. Er zijn geen andere gebruikers hebben toegang tot de app.

## <a name="next-steps"></a>Volgende stappen

In de **softwarebibliotheek** werkruimte Vouw **Toepassingsbeheer**, klikt u vervolgens op **licentiegegevens voor Store-Apps**.

Voor elke store-app u beheert, kunt u informatie weergeven over de app met inbegrip van de naam, platform en het aantal licenties voor de app die u bezit en het aantal licenties er beschikbaar zijn.
