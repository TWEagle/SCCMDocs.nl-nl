---
title: Apps beheren vanuit de Windows Store voor bedrijven | Microsoft-documenten
description: Beheren en implementeren van apps vanuit de Windows Store voor bedrijven met behulp van System Center Configuration Manager.
ms.custom: na
ms.date: 3/29/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-app
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 8cdb22a6-72d7-41f5-9bed-c098b1bcf675
caps.latest.revision: 11
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 6accec2d356861b273b25ba2b6338d9684a46ff6
ms.openlocfilehash: f2d9da1c584f78e27e84b7f55e7ffe4dd052a27c
ms.contentlocale: nl-nl
ms.lasthandoff: 05/17/2017

---

# <a name="manage-apps-from-the-windows-store-for-business-with-system-center-configuration-manager"></a>Apps beheren via de Windows Store voor Bedrijven met System Center Configuration Manager
De [Windows Store voor bedrijven](https://www.microsoft.com/business-store) kunt u vinden en koopt van Windows-apps voor uw organisatie, afzonderlijk of in volume. De store naar de Configuration Manager verbinding maakt, kunt u de lijst met apps met Configuration Manager hebt aangeschaft, weergeven in de Configuration Manager-console en deze implementeren net als elke andere app synchroniseren.


## <a name="online-and-offline-apps"></a>Online en offline-apps

De Windows Store voor bedrijven ondersteunt twee typen app:

- **Online** -dit licentietype is vereist voor gebruikers en apparaten verbinding maken met de store en de licentie voor een app ophalen. Windows 10-apparaten moet Azure Active Directory domein.
- **Offline** - organisaties apps in cache en licenties voor het implementeren van rechtstreeks in hun lokale netwerk, zonder verbinding maken met de store of een internetverbinding hebben.

[Meer informatie](https://technet.microsoft.com/itpro/windows/whats-new/windows-store-for-business-overview?f=255&MSPPError=-2147217396) over de Windows Store voor bedrijven.

Configuration Manager biedt ondersteuning voor het beheren van Windows Store voor Business-apps op Windows 10-apparaten waarop de Configuration Manager-client wordt uitgevoerd, en ook Windows 10-apparaten die zijn ingeschreven bij Microsoft Intune (ook wel een hybride-configuratie). Configuration Manager biedt de volgende mogelijkheden voor online en offline apps.

> [!IMPORTANT]
> Voor het gebruik van deze mogelijkheid, Windows 10-apparaten moeten worden uitgevoerd de release van November 2015 (1511) of hoger.


|Mogelijkheid|Offline-apps|Online apps|
|------------|------------|------------|
|Appgegevens naar Configuration Manager worden gesynchroniseerd<br>(vindt synchronisatie plaats elke 24 uur)|Ja|Ja|
|Configuration Manager-toepassingen uit de store-apps maken|Ja|Ja|
|Ondersteuning voor gratis apps uit de store|Ja|Ja|
|Ondersteuning voor betaald apps uit de store|Nee|Ja|
|Ondersteuning voor vereiste implementaties voor gebruikers of apparaten verzamelingen|Ja|Ja|
|Beschikbare implementaties naar verzamelingen van gebruikers of apparaten ondersteunen|Ja|Ja|
|Ondersteuning voor line-of-business-apps uit de store|Ja|Ja|

Om online gelicentieerde apps op Windows 10-computers implementeren met de Configuration Manager-client, ze moeten worden uitgevoerd de Windows Update beveiligingsbeheerder 10 of hoger.

## <a name="deploying-online-apps-using-the-windows-store-for-business-with-pcs-that-run-the-configuration-manager-client"></a>Online voor bedrijven met computers waarop de Configuration Manager-client wordt uitgevoerd met behulp van de Windows Store-apps te implementeren
Voordat u de Windows Store voor Business-apps op computers met de volledige Configuration Manager-client implementeert, kunt u het volgende:

- Voor de volledige functionaliteit, pc's moeten worden uitgevoerd de Windows Update beveiligingsbeheerder 10 of hoger.
- Pc's moet Azure Active Directory werkplek lid zijn van en worden in de dezelfde AAD-tenant waar u de Windows Store voor bedrijven geregistreerd als een management-hulpprogramma.
- Wanneer u pc's bent aangemeld met het ingebouwde Administrator-account, geen ze toegang tot Windows Store voor Business-apps.
- Pc's moeten een actieve internetverbinding hebben tot de Windows Store voor bedrijven.

### <a name="notes-for-pcs-running-earlier-versions-of-windows-10"></a>Opmerkingen voor pc's met eerdere versies van Windows 10
Op computers waarop een versie van Windows 10 ouder is dan de beveiligingsbeheerder Update (met de Configuration Manager-client), geldt de volgende functionaliteit:


- Wanneer de installatie wordt afgedwongen door de gebruiker de toepassing of de toepassing die de installatiedeadline wordt bereikt installeert of nieuwe evaluatie van de installatie voor vereiste implementaties posten:
    - De toepassing wordt 'afgedwongen' door de Windows Store voor Business-app te starten. 
    - De eindgebruiker moet vervolgens de installatie uit de store voltooien voordat deze daadwerkelijk wordt geïnstalleerd
    - De status van de toepassing in de Configuration Manager-console worden gerapporteerd als mislukt wordt aangeduid met de fout "Windows Store-app op de client-PC is geopend en wordt gewacht tot de gebruiker om de installatie te voltooien."
- Op de volgende beoordelingscyclus:
    - Als de toepassing is geïnstalleerd door de eindgebruiker uit de store, de Status van de toepassing wordt doorgegeven **geslaagd**. 
    - Als de gebruiker heeft geen poging tot het installeren van de app uit de store:
        - Vereiste implementaties probeert te starten van de store en het afdwingen van de installatie van de toepassing opnieuw.
        - Beschikbare implementaties worden niet opnieuw worden afgedwongen.

#### <a name="further-notes-for-pcs-running-earlier-versions-of-windows-10"></a>Meer opmerkingen voor pc's met eerdere versies van Windows 10:

- U kunt LOB-apps vanuit de Windows Store voor bedrijven niet implementeren
- Wanneer u een betaald apps uit de store implementeert, wordt eindgebruikers aangevraagd aan te melden in het archief en de app zelf kopen.
- Als u een Groepsbeleid uitschakelen toegang hebt geïmplementeerd naar de consumentenversie van de Windows Store, werkt implementaties vanuit de Windows Store voor bedrijven niet, zelfs als de Windows Store voor bedrijven is ingeschakeld.


## <a name="set-up-windows-store-for-business-synchronization"></a>Windows Store voor het synchroniseren van zakelijke instellen

**Registreren bij Azure Active Directory, Configuration Manager als een "Web Application en/of Web API" management-hulpprogramma. Hiermee krijgt u een client-ID die u later nodig hebt.**
1. In het knooppunt Active Directory van [https://manage.windowsazure.com](https://manage.windowsazure.com), selecteer uw Azure Active Directory en klik vervolgens op **toepassingen** > **toevoegen**.
2.  Klik op **toevoegen van een toepassing die het ontwikkelen van mijn organisatie**.
3.  Voer een naam voor de toepassing, selecteer **webtoepassing** en/of **Web API**, klikt u vervolgens de **volgende** pijl.
4.  Geef dezelfde URL voor zowel de **aanmelding URL** en **App-ID-URI**. De URL kan en hoeft niet te herleiden tot een echte adres. Bijvoorbeeld, kunt u *https://yourdomain/sccm*.
5.  Voltooi de wizard.

**In Azure Active Directory, maakt u een client-sleutel voor het geregistreerde management-hulpprogramma**
1.  Markeer de toepassing die u zojuist hebt gemaakt en klik op **configureren**.
2.  Onder **sleutels**, selecteer een duur in de lijst en klik vervolgens op **opslaan**. Hiermee wordt een nieuwe sleutel van de client gemaakt. Geen verlaat deze pagina totdat u is vrijgegeven de Windows Store voor bedrijven aan Configuration Manager hebt.

**In de Windows Store voor bedrijven, configureert u Configuration Manager als het beheerprogramma store**
1.  Open [https://businessstore.microsoft.com/en-us/managementtools](https://businessstore.microsoft.com/en-us/managementtools) en aanmelden als u wordt gevraagd.
2.  De gebruiksvoorwaarden accepteren als aangevraagd.
3.  Onder **beheerhulpprogramma's**, klikt u op **toevoegen van een beheerprogramma**.
4.  In **zoekt u het hulpprogramma met de naam**, typ de naam van de toepassing die u eerder hebt in AAD gemaakt en klik vervolgens op **toevoegen**.
5.  Klik op **activeren** naast de toepassing die u zojuist hebt geïmporteerd.
6.  In de **beheren > accountgegevens** optie **Show Offline-Licensed Apps** als u wilt toestaan dat offline gelicentieerde-apps worden aangeschaft.

**De store-account toevoegen aan Configuration Manager**

1. Zorg ervoor dat u ten minste één vanuit de Windows Store voor bedrijven hebt aangeschaft. In de **beheer** werkruimte van de Configuration Manager-console, vouw **Cloudservices**, klikt u vervolgens op **Windows Store voor bedrijven**.
2.  Op de **Start** tabblad, in de **Windows Store voor bedrijven** groep, klikt u op **toevoegen Windows Store voor bedrijven-Account**. 
3.  Uw tenant-ID, de client-id en de client sleutel toevoegen van Azure Active Directory en voltooi de wizard.
4. Nadat u klaar bent, ziet u het account dat u hebt geconfigureerd in de **Windows Store voor bedrijven** lijst in de Configuration Manager-console.


## <a name="create-and-deploy-a-configuration-manager-application-from-a-windows-store-for-business-app"></a>Maken en implementeren van een Configuration Manager-toepassing in een Windows Store voor Business-app.
1.  In de **softwarebibliotheek** werkruimte van de Configuration Manager-console, vouw **Toepassingsbeheer**, klikt u vervolgens op **licentie-informatie voor de Store-Apps**.
2.  Kies de app die u implementeren wilt, klik op de **Start** tabblad, in de **maken** groep, klikt u op **toepassing maken**.
Een Configuration Manager-toepassing wordt gemaakt met de Windows Store voor Business-app. U kunt vervolgens implementeren en controleren van deze toepassing als u een andere Configuration Manager-toepassing.
> [!IMPORTANT]
> Voor apparaten die zijn geregistreerd met Intune, zijn geïmplementeerde apps alleen beschikbaar voor de gebruiker die het apparaat oorspronkelijk ingeschreven. Er zijn geen andere gebruikers toegang tot de app.

## <a name="monitor-windows-store-for-business-apps"></a>Monitor voor Windows Store voor Business-Apps

In de **softwarebibliotheek** werkruimte Vouw **Toepassingsbeheer**, klikt u vervolgens op **licentie-informatie voor de Store-Apps**.

Voor elke store app u beheert, kunt u informatie bekijken over de app met inbegrip van de naam, platform en het aantal licenties voor de app die u bezit en het aantal licenties beschikbaar zijn voor u.

