---
title: Toegang tot e-mail beheren
titleSuffix: Configuration Manager
description: Informatie over het gebruik van voorwaardelijke toegang voor System Center Configuration Manager voor het beheren van toegang tot Exchange.
ms.custom: na
ms.date: 03/05/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-hybrid
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: fa648e73-5fb8-4818-ab57-7466ffaf888e
caps.latest.revision: 24
author: andredm7
ms.author: andredm
manager: angrobe
ms.openlocfilehash: e36674d27757daab9ced4e7e8b51942a4929b5ff
ms.sourcegitcommit: fb84bcb31d825f454785e3d9d8be669e00fe2b27
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/16/2018
---
# <a name="manage-email-access-in-system-center-configuration-manager"></a>Toegang tot e-mail beheren in System Center Configuration Manager

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*

Gebruik System Center Configuration Manager voorwaardelijke toegang voor het beheren van toegang tot Exchange op basis van door u opgegeven voorwaarden.  

U kunt de toegang beheren tot:  

-   Microsoft Exchange On-premises  

-   Microsoft Exchange Online  

-   Exchange Online-specifiek

U kunt toegang tot Exchange Online en Exchange On-premises beheren vanuit de ingebouwde e-mailclient op de volgende platforms:  

-   Android 4.0 en hoger, Samsung KNOX Standard 4.0 en hoger  

-   iOS 9.0 of hoger  

-   Windows Phone 8.1 en hoger  

-   E-mailtoepassing op Windows 8.1 en hoger

Office-bureaubladtoepassingen hebben toegang tot Exchange Online op pc's met:  

-   Office Desktop 2013 en hoger waarvoor [moderne verificatie](https://support.office.com/article/Using-Office-365-modern-authentication-with-Office-clients-776c0036-66fd-41cb-8928-5495c0f9168a) is ingeschakeld.  

-   Windows 7.0 of Windows 8.1  

> [!NOTE]  
>  Pc's moeten lid zijn van domein of voldoen aan de beleidsregels in Intune.  


## <a name="device-requirements"></a>Vereisten voor apparaten
 Als u voorwaardelijke toegang configureert voordat gebruikers verbinding kunnen maken met hun e-mail, moet het apparaat dat ze gebruiken:  

-   Zijn ingeschreven bij Intune of PC die lid van een domein.  

-   Registreer het apparaat bij Azure Active Directory (dit gebeurt automatisch wanneer het apparaat is ingeschreven bij Intune (alleen voor Exchange Online). Bovendien moet de client-id van Exchange ActiveSync worden geregistreerd bij Azure Active Directory (niet van toepassing op Windows- en Windows Phone-apparaten die verbinding maken met Exchange On-Premises).  

     Een pc die lid is van een domein moet zo zijn ingesteld dat deze automatisch wordt geregistreerd bij Azure Active Directory.  In de sectie **Voorwaardelijke toegang voor pc's** van het onderwerp [Toegang tot services beheren in System Center Configuration Manager](../../protect/deploy-use/manage-access-to-services.md) wordt de volledige lijst met vereisten gegeven voor het inschakelen van voorwaardelijke toegang voor pc's.  

-   Compatibel zijn met een Configuration Manager-nalevingsbeleid op dat apparaat is geïmplementeerd  

 Als niet aan een voorwaarde voor voorwaardelijke toegang wordt voldaan, krijgt de gebruiker een van de volgende berichten te zien wanneer de gebruiker zich aanmeldt.  

-   Als het apparaat niet is ingeschreven bij Intune of niet is geregistreerd in Azure Active Directory, wordt een bericht weergegeven met instructies over het installeren van de bedrijfsportal-app, het registreren van het apparaat en (voor Android en iOS-apparaten) en het activeren van e-mailadres waarmee de Exchange ActiveSync-ID van het apparaat worden gekoppeld aan de apparaatrecord in Azure Active Directory.  

-   Als het apparaat niet compatibel is, wordt een bericht weergegeven waarin wordt verwezen door de gebruiker de Intune-webportal waar ze informatie over het probleem en herstel kunnen vinden.  

**Voor mobiele apparaten:**

Kunt u de toegang beperken tot **Outlook Web Access (OWA)** op Exchange Online wanneer hiertoe toegang wordt verkregen vanuit een browser van **iOS** - en **Android** apparaten.  Toegang wordt alleen toegestaan vanuit ondersteunde browsers op compatibele apparaten:

* Safari (iOS)
* Chrome (Android)
* Beheerde browser (iOS en Android)

Niet-ondersteunde browsers worden geblokkeerd. De OWA-apps voor iOS en Android worden niet ondersteund.  Ze moeten worden geblokkeerd via regels die van kracht worden door ADFS:
* Met het instellen van ADFS worden er regels van kracht die niet-moderne verificatieprotocollen blokkeren. Gedetailleerde instructies vindt u in scenario 3 - [alle toegang tot O365 blokkeren behalve op browser gebaseerde toepassingen](https://technet.microsoft.com/library/dn592182.aspx).

 **Voor pc's:**  

-   Als de vereiste van het beleid voor voorwaardelijke toegang is om **domein toegevoegd** of **compatibel**toe te staan, wordt een bericht met instructies voor het registreren van het apparaat weergegeven. Als de PC niet aan een van de vereisten voldoet voldoet, wordt de gebruiker gevraagd het apparaat inschrijven bij Intune.  

-   Als de vereiste van het beleid voor voorwaardelijke toegang is ingesteld om alleen Windows-apparaten toe te staan die aan een domein zijn toegevoegd, wordt het apparaat geblokkeerd en wordt er een bericht weergegeven dat de gebruiker contact moet opnemen met de IT-beheerder.  

 U kunt op de volgende platformen toegang tot Exchange blokkeren via de op het apparaat ingebouwde Exchange ActiveSync-e-mailclient:  

-   Android 4.0 en hoger, Samsung KNOX Standard 4.0 en hoger  

-   iOS 9.0 of hoger  

-   Windows Phone 8.1 en hoger  

-   De toepassing **E-mail** in Windows 8.1 en hoger  

 Outlook-app voor iOS en Android en Outlook-bureaublad 2013 en hoger wordt alleen ondersteund voor Exchange Online.  

 De **op lokale Exchange-connector** tussen Configuration Manager en Exchange is vereist voor voorwaardelijke toegang werkt.  

 U kunt beleid voor voorwaardelijke toegang voor Exchange On-premises uit de Configuration Manager-console configureren. Wanneer u een beleid voor voorwaardelijke toegang voor Exchange Online configureert, kunt u beginnen met het proces in de Configuration Manager-console, die wordt gestart van de Intune-console waar u het proces kunt voltooien.  

## <a name="configure-conditional-access"></a>Voorwaardelijke toegang configureren
### <a name="step-1-evaluate-the-effect-of-the-conditional-access-policy"></a>Stap 1: Het effect van het beleid voor voorwaardelijke toegang evalueren  
 Nadat u hebt geconfigureerd de **op lokale Exchange-connector**, kunt u de Configuration Manager**lijst met apparaten op voorwaardelijke toegangsstatus** om apparaten die toegang tot Exchange na het configureren van beleid voor voorwaardelijke toegang wordt geblokkeerd. Voor dit rapport is tevens het volgende vereist:  

-   Een abonnement op Intune  

-   Het serviceaansluitpunt moet worden geconfigureerd en geïmplementeerd  

 Selecteer in de rapportparameters de Intune-groep die u wilt evalueren en, indien nodig, de apparaatplatforms waarop het beleid van toepassing.  

 Zie [Rapportage in System Center Configuration Manager](../../core/servers/manage/reporting.md) voor meer informatie over het uitvoeren van rapporten.  

 Nadat u het rapport hebt uitgevoerd, controleert u deze vier kolommen om te bepalen of een gebruiker wordt geblokkeerd:  

-   **Beheerkanaal** -geeft aan of het apparaat wordt beheerd door Intune, Exchange ActiveSync of beide.  

-   **Geregistreerd bij AAD** -geeft aan of het apparaat is geregistreerd bij Azure Active Directory (Workplace Join genoemd).  

-   **Compatibele** -geeft aan of het apparaat voldoet aan alle nalevingsbeleidsregels die u hebt geïmplementeerd.  

-   **EAS geactiveerd** -iOS en Android-apparaten hoeven te hebben van de Exchange ActiveSync-ID die is gekoppeld aan de apparaatregistratierecord in Azure Active Directory. Dit gebeurt wanneer de gebruiker op de koppeling **E-mail activeren** klikt in de quarantaine-e-mail.  

    > [!NOTE]  
    >  Op Windows Phone-apparaten wordt altijd een waarde weergegeven in deze kolom.  

 Apparaten die deel uitmaken van een doelgroep of doelverzameling, krijgen geen toegang tot Exchange, tenzij de kolomwaarden overeenkomen met de waarden die in de volgende tabel worden weergegeven:  

|Beheerkanaal|Geregistreerd bij AAD|compatibel|EAS geactiveerd|Resulterende actie|  
|------------------------|--------------------|---------------|-------------------|----------------------|  
|**Beheerd door Microsoft Intune en Exchange ActiveSync**|Ja|Ja|**Ja** of **Nee** wordt weergegeven|Toegang tot e-mail toegestaan|  
|Een andere waarde|Nee|Nee|Er wordt geen waarde weergegeven|Toegang tot e-mail geblokkeerd|  

 U kunt de inhoud van het rapport exporteren en de kolom **E-mailadres** gebruiken om gebruikers ervan op de hoogte te stellen dat toegang voor hen wordt geblokkeerd.  

### <a name="step-2-configure-user-groups-or-collections-for-the-conditional-access-policy"></a>Stap 2: Gebruikersgroepen of -verzamelingen voor het beleid voor voorwaardelijke toegang configureren  
 U richt de beleidsregels voor voorwaardelijke toegang op verschillende gebruikersgroepen of -verzamelingen, afhankelijk van de soorten beleid. Deze groepen bevatten de gebruikers die deel uitmaken van de doelgroep, of op wie het beleid juist niet van toepassing is. Wanneer een gebruiker deel uitmaakt van de doelgroep voor het beleid, moet elk apparaat dat wordt gebruikt, compatibel zijn om toegang te kunnen krijgen tot e-mail.  

-   **Voor het Exchange Online-beleid** - gericht op Azure Active Directory-beveiligingsgebruikersgroepen. U kunt deze groepen configureren in het **Office 365-beheercentrum**of in de **Intune-accountportal**.  

-   **Voor het beleid voor Exchange On-premises** - verzamelingen van Configuration Manager-gebruikers. U kunt deze configureren in de werkruimte **Activa en naleving** .  

 U kunt twee soorten groepen opgeven in elk beleid:  

-   **Doelgroepen** -gebruikersgroepen of -verzamelingen waarop het beleid wordt toegepast  

-   **Uitgesloten groepen** -gebruikersgroepen of -verzamelingen die uitgesloten van het beleid (optioneel zijn)  

 Als een gebruiker zich in beide groepen bevindt, wordt het beleid niet op de gebruiker toegepast.  

 Alleen de doelgroepen of -verzamelingen van het beleid voor voorwaardelijke toegang worden beoordeeld voor toegang tot Exchange.  

### <a name="step-3-configure-and-deploy-a-compliance-policy"></a>Stap 3: Configureer en implementeer een nalevingsbeleid  
 Zorg ervoor dat u een nalevingsbeleid hebt gemaakt en geïmplementeerd op alle apparaten waar het Exchange-beleid voor voorwaardelijke toegang op van toepassing is.  

 Zie [Nalevingsbeleid voor apparaten beheren in System Center Configuration Manager](device-compliance-policies.md) voor meer informatie over het configureren van het nalevingsbeleid.  

> [!IMPORTANT]  
>  Als u geen nalevingsbeleid hebt geïmplementeerd en daarna een Exchange-beleid voorwaardelijke toegang inschakelt, krijgen alle apparaten uit de doelgroep toegang.  

 Wanneer u klaar bent, gaat u door naar **Stap 4**.  

### <a name="step-4-configure-the-conditional-access-policy"></a>Stap 4: Beleid voor voorwaardelijke toegang configureren  

#### <a name="for-exchange-online-and-tenants-in-the-new-exchange-online-dedicated-environment"></a>Voor Exchange Online (en tenants in de nieuwe Exchange Online-specifieke omgeving)

>[!NOTE]
>U kunt ook een beleid voor voorwaardelijke toegang maken in de Azure AD-beheerconsole. Azure AD-beheerconsole kunt u het apparaat Intune beleidsregels voor voorwaardelijke toegang (aangeduid als het beleid voor voorwaardelijke toegang op basis van apparaten in Azure AD) naast andere beleidsregels voor voorwaardelijke toegang zoals multi-factor authentication-server maken. U kunt ook beleidsregels voor voorwaardelijke toegang voor Enterprise-apps van derden zoals Salesforce instellen en het selectievakje dat Azure AD ondersteunt. Zie voor meer informatie [het instellen van Azure Active Directory op basis van apparaten voorwaardelijke toegangsbeleid voor toegangsbeheer voor Azure Active Directory verbonden toepassingen](https://azure.microsoft.com/documentation/articles/active-directory-conditional-access-policy-connected-applications/).

 De volgende stroom wordt gebruikt door het beleid voor voorwaardelijke toegang van Exchange Online om te beoordelen of apparaten toegang moeten krijgen of moeten worden geblokkeerd.  

 ![ConditionalAccess8&#45;1](media/ConditionalAccess8-1.png)  

 Voor toegang tot e-mail moet het apparaat:  

-   Registreren bij Intune  

-   Pc's moeten lid zijn van domein of worden ingeschreven en voldoen aan het beleid in Intune instellen.  

-   Registreer het apparaat bij Azure Active Directory (dit gebeurt automatisch wanneer het apparaat is ingeschreven bij Intune.  

     U moet pc's die lid zijn van een domein zo instellen dat deze [het apparaat automatisch registreren](https://azure.microsoft.com/documentation/articles/active-directory-conditional-access-automatic-device-registration/) bij Azure Active Directory.  

-   E-mailadres waarmee de Exchange ActiveSync-ID van het apparaat worden gekoppeld aan de apparaatrecord in Azure Active Directory (van toepassing op iOS- en alleen Android-apparaten) activeren.  

-   Voldoen aan een geïmplementeerd nalevingsbeleid  

 De apparaatstatus wordt opgeslagen in Azure Active Directory, die toegang tot e-mail verleent of blokkeert op basis van de geëvalueerde voorwaarden.  

 Als niet aan een voorwaarde wordt voldaan, krijgt de gebruiker een van de volgende berichten te zien wanneer deze zich aanmeldt:  

-   Als het apparaat niet is ingeschreven, of is geregistreerd bij Azure Active Directory, wordt een bericht weergegeven met instructies over het installeren van de bedrijfsportal-app en het inschrijven  

-   Als het apparaat niet compatibel is, wordt een bericht weergegeven waarin de gebruiker naar de Intune-bedrijfsportal-website of de bedrijfsportal-app wordt verwezen waar informatie is te vinden over het probleem en hoe u worden opgelost.  

-   Voor een pc:  

    -   Als het beleid zo is ingesteld dat de pc lid moet zijn van een domein en de pc geen lid is van een domein, wordt in een bericht weergegeven dat contact moet worden opgenomen met de IT-beheerder.  

    -   Als het beleid zo is ingesteld dat de pc lid moet zijn van een domein of aan het beleid moet voldoen en de pc niet aan de vereiste voldoet, wordt er een bericht weergegeven met instructies over het installeren van de bedrijfsportal-app en de registratie.  

 Het bericht wordt op het apparaat weergegeven aan Exchange Online-gebruikers en tenants in de nieuwe Exchange Online-specifiek omgeving en gebruikers van Exchange On-Premises en oudere Exchange Online-specifieke apparaten ontvangen het bericht in hun Postvak IN.  

> [!NOTE]  
>  Configuration Manager regels voor voorwaardelijke toegang overschrijven, toestaan, blokkeren en in quarantaine regels die zijn gedefinieerd in de Exchange Online-beheerconsole.  

> [!NOTE]  
>  Het beleid voor voorwaardelijke toegang moet worden geconfigureerd in de Intune-console. De volgende stappen beginnen met het openen van de Intune-console via Configuration Manager. Als hierom wordt gevraagd, meldt u zich aan met dezelfde referenties die zijn gebruikt om het serviceaansluitpunt tussen Configuration Manager en Intune in te stellen.  

##### <a name="to-enable-the-exchange-online-policy"></a>Het Exchange Online-beleid inschakelen  

1.  Klik op **Activa en naleving**op de Configuration Manager-console.  

2.  Vouw **Compatibiliteitsinstellingen uit**, vouw **Voorwaardelijke toegang**uit en klik vervolgens op **Exchange Online**.  

3.  Ga naar het tabblad **Start** en klik in de groep **Koppelingen** op **Voorwaardelijk toegangsbeleid configureren in de Intune-console**. Mogelijk moet u de gebruikersnaam en wachtwoord van het account dat wordt gebruikt om Configuration Manager verbinding met een globale beheerder voor de Intune-service te bieden.  

     De Intune-beheerconsole wordt geopend.  

4.  In de [Microsoft Intune-beheerconsole](https://manage.microsoft.com)klikt u op **Beleid** > **Voorwaardelijke toegang** > **Exchange Online-beleid**.  

     ![HybridOnlineSetupIntune](media/HybridOnlineSetupIntune.png)  

5.  Selecteer op de pagina **Exchange Online-beleid** de optie **Beleid voor voorwaardelijke toegang inschakelen voor Exchange Online**. Als u dit selectievakje inschakelt, moet het apparaat compatibel zijn. Als dit niet is ingeschakeld, wordt voorwaardelijke toegang niet toegepast.  

    > [!NOTE]  
    >  Als u geen nalevingsbeleid hebt geïmplementeerd en daarna het Exchange Online-beleid inschakelt, worden alle apparaten gerapporteerd als zijnde compatibel.  
    >   
    >  Ongeacht de nalevingsstatus moeten alle gebruikers die zijn gericht door het beleid moet op hun apparaten inschrijven bij Intune.  

6.  Onder **Toegang voor toepassingen**kunt u voor Outlook en andere apps die moderne authenticatie gebruiken, ervoor kiezen de toegang te beperken tot apparaten die voldoen aan het beleid voor elk platform.  Windows-apparaten moeten lid zijn van een domein of moeten zijn ingeschreven bij en voldoen aan het beleid van Intune.  

    > [!TIP]  
    >  **Moderne verificatie** biedt aanmelding bij Office-clients op basis van Active Directory Authentication Library (ADAL).  
    >   
    >  -   Dankzij verificatie op basis van ADAL is voor Office-clients verificatie via een browser (ook wel passieve verificatie) mogelijk.  De gebruiker wordt hierbij naar een aanmeldingspagina geleid om de verificatie uit te voeren.  
    > -   Deze nieuwe aanmeldingsmethode maakt nieuwe scenario's, zoals voorwaardelijke toegang, mogelijk op basis van **apparaatcompatibiliteit** en of **meervoudige verificatie** is uitgevoerd.  
    >   
    >  Dit [artikel](https://support.office.com/en-US/article/How-modern-authentication-works-for-Office-2013-and-Office-2016-client-apps-e4c45989-4b1a-462e-a81b-2a13191cf517) bevat gedetailleerde informatie over de werking van moderne verificatie.  

     Als u Exchange Online met Configuration Manager en Intune gebruikt, kunt u niet alleen mobiele apparaten met voorwaardelijke toegang beheren, maar ook desktopcomputers. Pc's moeten lid zijn van een domein of moeten zijn geregistreerd en voldoen aan het beleid. U kunt de volgende vereisten instellen:  

    -   **Apparaten moeten lid zijn van een domein of voldoen aan het beleid.** Pc's moeten lid zijn van een domein of voldoen aan het beleid dat is ingesteld. Als een PC niet voldoet niet aan een van deze vereisten voldoet, wordt de gebruiker gevraagd het apparaat inschrijven bij Intune.  

    -   **Apparaten moeten lid zijn van een domein.** Pc's moeten lid zijn van een domein om toegang te krijgen tot Exchange Online. Als een pc geen lid is van een domein, wordt de toegang tot e-mail geblokkeerd en wordt de gebruiker gevraagd contact op te nemen met de IT-beheerder.  

    -   **Apparaten moeten voldoen aan het beleid.** Pc's moeten zijn ingeschreven in Intune en voldoen. Als een pc niet is ingeschreven, wordt een bericht met instructies voor de inschrijving weergegeven.  

7.  Onder **Outlook web access (OWA)**, u kunt kiezen om toegang tot Exchange Online alleen via de ondersteunde browsers: Safari (iOS) en Chrome (Android). Toegang via andere browsers wordt geblokkeerd. Dezelfde platformbeperkingen die u hebt geselecteerd voor Toegang tot toepassingen voor Outlook zijn ook hier van toepassing.

    Op **Android** -apparaten moeten gebruikers de browsertoegang inschakelen.  Om dit te doen de eindgebruiker moeten de 'Browsertoegang inschakelen' optie inschakelen op het ingeschreven apparaat als volgt:
     1. Open de app **Bedrijfsportal**.
     2. Ga naar de **instellingen** pagina van de drie puntjes (...) of de menuknop hardware.
      3.    Druk op de knop **Browsertoegang inschakelen** .
      4.    In de browser Chrome meldt u zich af bij Office 365 en vervolgens start u Chrome opnieuw op.

     Op **iOS en Android** -platforms, zal Azure Active Directory een TLS-certificaat (Transport Layer Security) aan het apparaat verlenen om het apparaat te kunnen identificeren dat wordt gebruikt voor het verkrijgen van toegang.  Op het apparaat wordt het certificaat weergegeven met een verzoek aan de eindgebruiker om het certificaat te selecteren, zoals wordt weergegeven in de onderstaande schermafbeeldingen. De eindgebruiker moet dit certificaat selecteren om de browser te kunnen blijven gebruiken.

     **iOS**

     ![schermafbeelding van het certificaat met het verzoek op een ipad](media/mdm-browser-ca-ios-cert-prompt_v2.png)

    **Android**

    ![schermafbeelding van het certificaat met het verzoek op een Android-apparaat](media/mdm-browser-ca-android-cert-prompt.png)

7.  Voor**Exchange ActiveSync-e-mail-apps**kunt u voorkomen dat e-mail via Exchange Online wordt geopend als het apparaat niet aan het beleid voldoet en kunt u selecteren of u de toegang tot e-mail wilt toestaan of blokkeren als Intune het apparaat niet kan beheren.  

8.  Onder **Doelgroepen**selecteert u de Active Directory-beveiligingsgebruikersgroepen waarop het beleid van toepassing moet zijn.  

    > [!NOTE]  
    >  Voor gebruikers in Doelgroepen wordt het Intune-beleid vervangen door Exchange-regels en -beleid.  
    >   
    >  In Exchange worden alleen in de volgende gevallen regels voor toestaan, blokkeren en in quarantaine plaatsen die zijn gedefinieerd in Exchange en Exchange-beleid afgedwongen:  
    >   
    >  -   De gebruiker heeft geen licentie voor Intune.  
    > -   De gebruiker heeft een licentie voor Intune, maar de gebruiker behoort niet tot een beveiligingsgroep die is gedefinieerd in het beleid voor voorwaardelijke toegang.  

9. Onder **Uitgesloten groepen**selecteert u de Active Directory-beveiligingsgebruikersgroepen waarop dit beleid niet van toepassing is. Als een gebruiker zich in beide groepen bevindt, wordt het beleid niet op de gebruiker toegepast en heeft de gebruiker toegang tot zijn e-mail.  

10. Klik op **Opslaan**als u klaar bent.  

-   U hoeft het beleid voor voorwaardelijke toegang niet te implementeren; het wordt direct van kracht.  

-   Wanneer een gebruiker een e-mailaccount maakt, wordt het apparaat onmiddellijk geblokkeerd.  

-   Als een geblokkeerde gebruiker het apparaat bij Intune inschrijft (of de compatibiliteit herstelt), is binnen twee minuten toegang tot e-mail niet geblokkeerd.  

-   Als de gebruiker het apparaat uitschrijft, wordt de toegang tot e-mail na circa 6 uur geblokkeerd.  

### <a name="for-exchange-on-premises-and-tenants-in-the-legacy-exchange-online-dedicated-environment"></a>Voor Exchange On-Premises (en tenants in de oude Exchange Online-specifieke omgeving)  
 De volgende stroom wordt gebruikt door het beleid voor voorwaardelijke toegang van Exchange On-Premises en tenants in de oude Exchange Online-specifieke omgeving om te beoordelen of apparaten toegang moeten krijgen of moeten worden geblokkeerd.  

 ![ConditionalAccess8&#45;2](media/ConditionalAccess8-2.png)  

##### <a name="to-enable-the-exchange-on-premises-policy"></a>Het beleid van Exchange On-Premises inschakelen  

1.  Klik op **Activa en naleving**op de Configuration Manager-console.  

2.  Vouw **Instellingen voor naleving**uit, vouw **Voorwaardelijke toegang**uit en klik vervolgens op **On-Premises Exchange**.  

3.  Klik op het tabblad **Start** , in de groep **On-Premises Exchange** op **Voorwaardelijk toegangsbeleid configureren**.  

4.  **Vanaf versie 1602 van Configuration Manager**geeft u op de pagina **Algemeen** van de **wizard Beleid voor voorwaardelijke toegang configureren**op of u de standaardregel voor Exchange ActiveSync wilt overschrijven. Klik op deze optie als u wilt dat geregistreerde en compatibele apparaten altijd toegang hebben tot e-mail, zelfs wanneer de standaardregel is ingesteld op quarantaine of het blokkeren van de toegang.  

    > [!NOTE]  
    >  Er is een probleem met het overschrijven van de standaard voor Android-apparaten. Als de standaardregel voor de toegang van de Exchange-server is ingesteld op **Blokkeren** en het Exchange-beleid voor voorwaardelijke toegang is ingeschakeld met de standaardoptie voor het overschrijven van de regel, wordt de blokkering op Android-apparaten van de beoogde gebruikers mogelijk niet opgeheven, zelfs nadat de apparaten zijn ingeschreven bij Intune en aan het beleid daarvan voldoen.  Als tijdelijke oplossing voor dit probleem stelt u de standaardtoegangsregel voor Exchange in op **Quarantaine**. Het apparaat krijgt standaard geen toegang tot Exchange en de beheerder kan een rapport van de Exchange-server ophalen over de lijst met apparaten die in quarantaine zijn geplaatst.  

     Als u geen e-mailaccount voor meldingen hebt ingesteld tijdens de configuratie van de Exchange-connector, wordt er een waarschuwing weergegeven op deze pagina en wordt de knop **Volgende** uitgeschakeld.  Voordat u verder kunt gaan, moet u eerst e-mailinstellingen voor meldingen configureren in de Exchange-connector en vervolgens terugkeren naar de **wizard Beleid voor voorwaardelijke toegang configureren** om het proces te voltooien.  

     ![HybridCondAccessWiz1](media/HybridCondAccessWiz1.PNG)  

     Klik op **Volgende**.  

5.  Op de pagina **Doelverzamelingen** voegt u één of meerdere gebruikersverzamelingen toe. Als u Exchange opent, moeten gebruikers in deze verzamelingen hun apparaten inschrijven bij Intune en ook moeten voldoen aan alle nalevingsbeleidsregels die u hebt geïmplementeerd.  

     ![HybridCondAccessWiz2](media/HybridCondAccessWiz2.PNG)  

     Klik op **Volgende**.  

6.  Op de pagina **Vrijgestelde verzamelingen** voegt u de gebruikersverzamelingen toe die u wilt vrijstellen van het voorwaardelijke toegangsbeleid. Gebruikers in deze groepen moeten hun apparaten inschrijven bij Intune en niet hoeft niet te voldoen aan het geïmplementeerde nalevingsbeleid om toegang tot Exchange.  

     ![HybridCondAccessWiz3](media/HybridCondAccessWiz3.png)  

     Als een gebruiker zich in beide lijsten bevindt, wordt het beleid niet op de gebruiker toegepast.  

     Klik op **Volgende**.  

7.  Op de **gebruikersmelding bewerken** pagina, de e-mail die door Intune worden verzonden naar gebruikers met instructies over het om de blokkering van hun apparaat (in aanvulling op de e-mailbericht dat Exchange wordt verzonden) te configureren.  

     U kunt het standaardbericht bewerken en HTML-codes gebruiken om de opmaak van de tekst te wijzigen. U kunt ook van tevoren een e-mailbericht naar uw werknemers verzenden met een melding van de komende wijzigingen en met instructies voor het inschrijven van hun apparaten.  

     ![HybridCondAccessWiz4](media/HybridCondAccessWiz4.PNG)  

    > [!NOTE]  
    >  Omdat de Intune-meldingse-mail met herstelinstructies wordt bezorgd in de Exchange-postvak van de gebruiker in het geval dat een apparaat van de gebruiker worden geblokkeerd voordat ze het e-mailbericht ontvangen, kunnen ze een niet-geblokkeerd apparaat of een andere methode gebruiken voor toegang tot Exchange en weergeven van het bericht.  

    > [!NOTE]  
    >  Als u ervoor wilt zorgen dat Exchange de e-mailmelding kan verzenden, moet u het account dat wordt gebruikt om de e-mailmelding te verzenden, configureren. U doet dit wanneer u de eigenschappen van de Exchange Server-connector configureert.  
    >   
    >  Voor meer informatie, zie [Mobiele apparaten beheren met System Center Configuration Manager en Exchange](../../mdm/deploy-use/manage-mobile-devices-with-exchange-activesync.md).  

     Klik op **Volgende**.  

8.  Controleer uw instellingen op de pagina  **Overzicht** en voltooi daarna de wizard.  

-   U hoeft het beleid voor voorwaardelijke toegang niet te implementeren; het wordt direct van kracht.  

-   Wanneer een gebruiker een Exchange ActiveSync-profiel heeft ingesteld, kan het apparaat is geblokkeerd (als deze niet wordt beheerd door Intune) 1-3 uur duren.  

-   Als een geblokkeerde gebruiker vervolgens het apparaat bij Intune inschrijft (of de compatibiliteit herstelt), wordt toegang tot e-mail binnen twee minuten te worden gedeblokkeerd.  

-   Als de gebruiker un-inschrijft bij Intune het apparaat is geblokkeerd 1-3 uur kan duren.  

### <a name="see-also"></a>Zie tevens  
 [Toegang tot services in System Center Configuration Manager beheren](../../protect/deploy-use/manage-access-to-services.md)
