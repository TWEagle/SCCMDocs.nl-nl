---
title: Apps beheren via de Microsoft Store voor bedrijven
titleSuffix: Configuration Manager
description: Beheren en implementeren van apps uit de Microsoft Store voor bedrijven met behulp van System Center Configuration Manager.
ms.custom: na
ms.date: 12/29/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: configmgr-app
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 8cdb22a6-72d7-41f5-9bed-c098b1bcf675
caps.latest.revision: "11"
author: aczechowski
ms.author: aaroncz
manager: angrobe
ms.openlocfilehash: 15644a8c1acdbde85c7ca194a72a10c3cc2c0fcc
ms.sourcegitcommit: f1535281b2c3fecff773b722c3f7590bf6ba10a0
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 01/03/2018
---
# <a name="manage-apps-from-the-microsoft-store-for-business-with-system-center-configuration-manager"></a>Apps beheren via de Microsoft Store voor bedrijven met System Center Configuration Manager
De [Microsoft Store voor bedrijven](https://www.microsoft.com/business-store) kunt u vinden en Windows-apps voor uw organisatie, kopen, afzonderlijk of in volume. De store koppelt aan Configuration Manager, kunt u de lijst met apps die u hebt aangeschaft synchroniseren met Configuration Manager. U kunt deze apps bekijken in de Configuration Manager-console, en deze implementeren zoals u zou ook een andere app implementeren.


## <a name="online-and-offline-apps"></a>Online en offline apps

De Microsoft Store voor bedrijven ondersteunt twee typen app:

- **Online** -dit licentietype is vereist voor gebruikers en apparaten verbinding maken met de store om op te halen van een app en de licentie. Windows 10-apparaten moet Azure Active Directory domein.
- **Offline** -kunt u apps in cache en licenties voor het implementeren van rechtstreeks vanuit uw on-premises netwerk. Apparaten hoeft niet te verbinden met de store of een verbinding hebben met Internet.

[Lees meer](https://docs.microsoft.com/microsoft-store/microsoft-store-for-business-overview) over de Microsoft Store voor bedrijven.

Configuration Manager ondersteunt het beheer van Microsoft Store voor bedrijven-apps op zowel Windows 10-apparaten met Configuration Manager-client, en Windows 10-apparaten die zijn ingeschreven bij Microsoft Intune. Configuration Manager biedt de volgende mogelijkheden voor online en offline apps.

> [!IMPORTANT]
> Voor het gebruik van Microsoft Store voor bedrijven, Windows 10-apparaten moeten worden uitgevoerd de release van November 2015 (1511) of hoger.


|Mogelijkheid|Offline apps|Online-apps|
|------------|------------|------------|
|Synchroniseren van app-gegevens naar Configuration Manager<br>(synchronisatie wordt uitgevoerd om de 24 uur)|Ja|Ja|
|Configuration Manager-toepassingen maken vanuit de store-apps|Ja|Ja|
|Ondersteuning voor gratis apps uit de store|Ja|Ja|
|Ondersteuning voor betaalde apps uit de store|Nee|Ja<sup>1</sup>|
|Ondersteuning voor vereiste implementaties voor verzamelingen gebruikers of apparaten|Ja|Ja|
|Ondersteuning voor beschikbare implementaties voor verzamelingen gebruikers of apparaten|Ja|Ja|
|Ondersteuning voor line-of-business-apps uit de store|Ja|Ja|

<sup>1</sup>om online gelicentieerde apps implementeren op Windows 10-pc's met de Configuration Manager-client, ze moeten worden uitgevoerd de Update voor Windows 10 maken, of later.

### <a name="deploying-online-apps-using-the-microsoft-store-for-business-with-pcs-that-run-the-configuration-manager-client"></a>Online-apps met de Microsoft Store voor bedrijven met pc's met de Configuration Manager-client implementeren
Voordat u de Microsoft Store voor bedrijven-apps op pc's met de volledige Configuration Manager-client implementeert, houd rekening met de volgende punten:

- Voor volledige functionaliteit pc's moeten worden uitgevoerd de Update auteurs van Windows 10 of hoger.
- Pc's moeten worden toegevoegd aan Azure Active Directory in dezelfde tenant waar u de Microsoft Store voor bedrijven als beheerprogramma geregistreerd.
- Wanneer u pc's bent aangemeld met het ingebouwde administratoraccount, geen ze toegang tot Microsoft Store voor bedrijven-apps.
- Pc's moeten een actieve internetverbinding hebben tot de Microsoft Store voor bedrijven.

### <a name="notes-for-pcs-running-earlier-versions-of-windows-10"></a>Opmerkingen voor pc's met eerdere versies van Windows 10
Op computers met een versie van Windows 10 ouder is dan de beveiligingsbeheerder Update (met de Configuration Manager-client), geldt de volgende functionaliteit:


- Bij het afdwingen van de installatie door de gebruiker installeren van de toepassing, de toepassing de installatiedeadline wordt bereikt, of door het nieuwe evaluatie voor vereiste implementaties na de installatie:
    - De toepassing wordt 'afgedwongen' door de Microsoft Store voor bedrijven-app te starten. 
    - De gebruiker moet vervolgens de installatie vanuit de store voltooien voordat de app is geïnstalleerd
    - In de Configuration Manager console probleem rapporten voor de status van toepassingen met de volgende fout: 'De Microsoft Store-app op de client-PC is geopend en wacht tot de gebruiker om de installatie te voltooien.'
- Bij de volgende beoordelingscyclus van toepassing:
    - Als de toepassing is geïnstalleerd door de gebruiker uit de store, de toepassing meldt de Status **geslaagd**. 
    - Als de gebruiker heeft niet geprobeerd de app te installeren vanuit de store:
        - Vereiste implementaties poging tot het starten van de store en het afdwingen van de installatie van de toepassing opnieuw.
        - Beschikbare implementaties niet opnieuw worden afgedwongen.

#### <a name="further-notes-for-pcs-running-earlier-versions-of-windows-10"></a>Aanvullende opmerkingen voor pc's met eerdere versies van Windows 10:

- U kunt geen line-of-business-apps uit de Microsoft Store voor bedrijven implementeren
- Wanneer u een betaalde apps uit de store implementeert, moet de eindgebruikers aanmelden bij de store en de aankoop van de app zelf.
- Als u een Groepsbeleid om de toegang tot de consumentenversie van de Microsoft Store uitschakelen implementeert, werkt implementaties van de Microsoft Store voor bedrijven niet, zelfs als de Microsoft Store voor bedrijven is ingeschakeld.


## <a name="set-up-microsoft-store-for-business-synchronization"></a>Microsoft Store voor bedrijven-synchronisatie instellen
Synchroniseren van de lijst met apps hebt aangeschaft door uw organisatie, kunt u deze apps in de Configuration Manager-console.

<!-- Remove below after 1802... -->
### <a name="for-configuration-manager-versions-prior-to-1706"></a>Voor eerdere versies 1706 Configuration Manager

**Registreren bij Azure Active Directory, Configuration Manager als beheerprogramma 'Webtoepassing en/of Web-API'. Deze actie geeft u een client-ID die u later nodig.**
1. In het Active Directory-knooppunt van [https://manage.windowsazure.com](https://manage.windowsazure.com), selecteer uw Azure Active Directory en klik vervolgens op **toepassingen** > **toevoegen**.
2.  Klik op **mijn organisatie ontwikkelt toepassing toevoegen**.
3.  Voer een naam voor de toepassing, selecteer **webtoepassing** en/of **Web API**, klikt u vervolgens op de **volgende** pijl.
4.  Voer dezelfde URL voor zowel de **aanmeldings-URL** en **App ID URI**. De URL kan van alles zijn en hoeft niet omzetten in een echte adres. Bijvoorbeeld, kunt u *https://yourdomain/sccm*.
5.  Voltooi de wizard.

**Maak in Azure Active Directory een clientsleutel voor het geregistreerde beheerprogramma**
1.  Markeer de toepassing die u hebt gemaakt en klik op **configureren**.
2.  Onder **sleutels**, selecteert u een duur in de lijst en klik vervolgens op **opslaan**. Deze actie wordt een nieuwe clientsleutel gemaakt. Verlaat deze pagina totdat u is vrijgegeven Microsoft Store voor bedrijven naar Configuration Manager.

**Configuration Manager in Microsoft Windows Store voor bedrijven configureren als het winkelbeheerprogramma**
1.  Open [https://businessstore.microsoft.com/en-us/managementtools](https://businessstore.microsoft.com/en-us/managementtools) en meld u als u wordt gevraagd.
2.  Accepteer de gebruiksvoorwaarden als aangevraagd.
3.  Onder **beheerhulpprogramma's**, klikt u op **beheerprogramma toevoegen**.
4.  In **zoeken voor het hulpprogramma met de naam**, typ de naam van de toepassing die u eerder in Add hebt gemaakt en klik vervolgens op **toevoegen**.
5.  Klik op **activeren** naast de toepassing die u hebt geïmporteerd.
6.  In de **beheren > accountgegevens** pagina **Apps met offline licentie weergeven** als u toestaan dat apps offline licentie wilt aan te schaffen.

**De store-account toevoegen aan Configuration Manager**

1. Zorg ervoor dat u ten minste één app in de Microsoft Store voor bedrijven hebt aangeschaft. In de **beheer** werkruimte van de Configuration Manager-console, vouw **Cloudservices**, klikt u vervolgens op **Microsoft Store voor bedrijven**.
2.  Op de **Start** tabblad, in de **Microsoft Store voor bedrijven** groep, klikt u op **Microsoft Store voor bedrijven-Account toevoegen**. 
3.  Uw tenant-ID, client-ID en clientsleutel uit Azure Active Directory toevoegen en voltooi de wizard.
4. Wanneer u klaar bent, ziet u het account onder **Microsoft Store voor bedrijven** in de Configuration Manager-console.

### <a name="for-configuration-manager-version-1706-and-later"></a>Voor Configuration Manager versie 1706 en hoger
<!-- ...remove above after 1802 -->

1. Ga in de console naar **beheer** > **Cloudservices** > **Azure Services**, en kies vervolgens **Azure configureren Services** starten de **Wizard Azure-Services**.
2. Op de **Azure Services** pagina, selecteert u de service die u wilt configureren en klik vervolgens op **volgende**.
3. Op de **algemene** pagina, Geef een beschrijvende naam voor de naam van de Azure-service en een optionele beschrijving en klik vervolgens op **volgende**.
4. Op de **App** pagina, Geef uw Azure-omgeving en klik vervolgens op **Bladeren** openen de **App Server** venster.
5. In de **App Server** venster, selecteer de server-app die u wilt gebruiken en klik vervolgens op **OK**. Server-apps zijn de Azure-web-apps die de configuraties voor uw Azure-account, inclusief uw tenant-ID, client-ID en een geheime sleutel voor clients bevatten. Als u een beschikbare server-app niet hebt, gebruikt u een van de volgende acties:
    - **Maken:** Klik op om een nieuwe server app **maken**. Geef een beschrijvende naam voor de app en de tenant. Vervolgens, nadat u zich bij Azure aanmelden Configuration Manager maakt de web-app in Azure voor u, met inbegrip van de client-ID en een geheime sleutel voor gebruik met de web-app. Later kunt kunt u deze waarden uit de Azure portal weergeven.
    - **Importeren:** Met een web-app die al in uw Azure-abonnement bestaat, klikt u op **importeren**. Geef een beschrijvende naam voor de app en de tenant. Geef vervolgens de tenant-ID, client-ID en de geheime sleutel voor de Azure-web-app die u wilt dat Configuration Manager te gebruiken. Nadat u **controleren** de gegevens, klikt u op **OK** om door te gaan. 
6. Controleer de **informatie** pagina en eventuele extra stappen en configuraties voltooid zoals beschreven. Deze configuraties zijn nodig om de service gebruiken met Configuration Manager. Als u bijvoorbeeld de Microsoft Store voor bedrijven configureren:
    - In Azure, moet u Configuration Manager registreert als een webtoepassing of Web-API en vastleggen van de client-ID. U kunt ook een clientsleutel voor gebruik opgeven door het management-hulpprogramma (dit is de Configuration Manager).
    - In de Microsoft Store voor bedrijven-portal moet u Configuration Manager configureren als het winkelbeheerprogramma, ondersteuning voor offline gelicentieerde apps inschakelen en vervolgens ten minste één app kopen. 
7. Klik op **volgende** wanneer u bent klaar om door te gaan.
8. Op de **App configuraties** pagina en klik vervolgens op de app-catalogus en taal configuraties voor deze service **volgende**.
9. Nadat de wizard is voltooid, ziet u de Configuration Manager-console dat u hebt geconfigureerd **Microsoft Store voor bedrijven** als een **Cloud Service Type**.




## <a name="create-and-deploy-a-configuration-manager-application-from-a-microsoft-store-for-business-app"></a>Een Configuration Manager-toepassing in een Microsoft-Store voor bedrijven-app maken en implementeren
Na de synchronisatie, maken en implementeren van de store-apps, net als elke andere app.

1.  In de **softwarebibliotheek** werkruimte van de Configuration Manager-console, vouw **Toepassingsbeheer**, klikt u vervolgens op **licentiegegevens voor Store-Apps**.
2.  Kies de app die u implementeren wilt, klik op de **Start** tabblad, in de **maken** groep, klikt u op **toepassing maken**.
Een Configuration Manager-toepassing wordt gemaakt met van de Microsoft Store voor bedrijven-app. U kunt implementeren en bewaken van deze toepassing, net als elke andere Configuration Manager-toepassing.

> [!IMPORTANT]
> Voor apparaten met Microsoft Intune zijn ingeschreven, zijn geïmplementeerde apps alleen beschikbaar voor de gebruiker die het apparaat oorspronkelijk ingeschreven. Er zijn geen andere gebruikers hebben toegang tot de app.

## <a name="next-steps"></a>Volgende stappen

In de **softwarebibliotheek** werkruimte Vouw **Toepassingsbeheer**, klikt u vervolgens op **licentiegegevens voor Store-Apps**.

Voor elke store-app die u beheert, kunt u informatie over de app weergeven. Deze informatie bevat de naam van de app, platform, het aantal licenties voor de app die u bezit en het aantal licenties er beschikbaar zijn.

Na implementatie van online apps, eventuele updates voor die app wordt rechtstreeks afkomstig zijn uit de Microsoft Store. Configuration Manager controleert bovendien niet compatibiliteit van de versie van online apps, alleen dat Windows de app meldt geïnstalleerd.  

Wanneer u offline apps implementeert naar Windows 10-apparaten met Configuration Manager-client, gebruikers externe toepassingen voor Configuration Manager-implementaties bijwerken niet toestaan. Beheer van updates voor offline apps is vooral belangrijk in omgevingen met meerdere gebruikers zoals klaslokaal. Een optie voor het uitschakelen van de Microsoft Store is via [groepsbeleid](https://docs.microsoft.com/en-us/windows/configuration/stop-employees-from-using-microsoft-store#a-href-idblock-store-group-policyablock-microsoft-store-using-group-policy). 

Na de Microsoft Store voor bedrijven beheerder een offline-app aankopen, publiceer de app niet aan gebruikers via de store. Deze configuratie zorgt ervoor dat gebruikers kunnen installeren of online bijwerken. Gebruikers ontvangt alleen offline app-updates via de Configuration Manager. 
