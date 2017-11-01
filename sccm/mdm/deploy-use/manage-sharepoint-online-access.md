---
title: Toegang tot SharePoint Online beheren
titleSuffix: Configuration Manager
description: Informatie over het gebruiken van System Center Configuration Manager SharePoint Online beleid voor voorwaardelijke toegang voor het beheren van toegang tot OneDrive.
ms.custom: na
ms.date: 03/05/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: configmgr-hybrid
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 49cec466-1676-4fe2-a2fe-5004f01d735e
caps.latest.revision: "11"
caps.handback.revision: "0"
author: andredm7
ms.author: andredm
manager: angrobe
ms.openlocfilehash: 2c1d7cd3462a54a064ec47d0b375ee4cdb25a4b4
ms.sourcegitcommit: c236214b2fcc13dae7bad96d7fb33f692868191d
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/12/2017
---
# <a name="manage-sharepoint-online-access-in-system-center-configuration-manager"></a>Toegang tot SharePoint Online in System Center Configuration Manager beheren

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*


De System Center Configuration Manager gebruiken **SharePoint Online** beleid voor voorwaardelijke toegang voor het beheren van toegang tot OneDrive voor bedrijven bestanden op SharePoint online, op basis van door u opgegeven voorwaarden.
U kunt toegang tot SharePoint Online beheren vanuit de volgende apps voor de genoemde platforms:  

-   Microsoft Office Mobile (Android)  

-   Microsoft OneDrive (Android en iOS)  

-   Microsoft Word (Android en iOS)  

-   Microsoft Excel (Android en iOS)  

-   Microsoft PowerPoint (Android en iOS)  

-   Microsoft OneNote (Android en iOS)

Office-bureaubladtoepassingen hebben toegang tot SharePoint Online op pc's met:  

-   Office Desktop 2013 en hoger waarvoor [moderne verificatie](https://support.office.com/en-US/article/Using-Office-365-modern-authentication-with-Office-clients-776c0036-66fd-41cb-8928-5495c0f9168a) is ingeschakeld.  

-   Windows 7.0 of Windows 8.1  

> [!NOTE]  
>  Pc's moeten lid zijn van domein of voldoen aan de beleidsregels in Intune.  



 Wanneer een gebruiker in de doelgroep probeert verbinding te maken met een bestand via een ondersteunde app, zoals OneDrive, op zijn of haar apparaat, wordt de volgende evaluatie uitgevoerd:  

 ![ConditionalAccess8&#45;6](media/ConditionalAccess8-6.png)  

 Om verbinding te kunnen maken met de vereiste bestanden moet het apparaat waarop OneDrive wordt uitgevoerd:  

-   Met Microsoft Intune worden ingeschreven of PC die lid van een domein.  

-   Registreer het apparaat bij Azure Active Directory (dit gebeurt automatisch wanneer het apparaat is ingeschreven bij Intune.  

     Voor pc’s die deel uitmaken van een domein, moet u dit instellen op [automatisch registreren](https://azure.microsoft.com/en-us/documentation/articles/active-directory-conditional-access-automatic-device-registration/) bij Azure Active Directory.  

-   Voldoen aan het geïmplementeerde nalevingsbeleid Configuration Manager  

 De apparaatstatus wordt opgeslagen in Azure Active Directory, die toegang tot de bestanden verleent of blokkeert op basis van de opgegeven voorwaarden.  

 Als niet aan een voorwaarde wordt voldaan, krijgt de gebruiker een van de volgende berichten te zien wanneer deze zich aanmeldt:  

-   Als het apparaat niet is ingeschreven bij Intune of niet is geregistreerd bij Azure Active Directory, wordt een bericht weergegeven met instructies over het installeren van de bedrijfsportal-app en het inschrijven.  

-   Als het apparaat niet compatibel is, wordt een bericht weergegeven waarin wordt verwezen door de gebruiker de Intune-webportal waar informatie is te vinden over het probleem en hoe u worden opgelost.  

- Voor mobiele apparaten:

  Kunt u de toegang beperken tot SharePoint Online wanneer hiertoe toegang wordt verkregen vanuit een browser van **iOS**- en **Android**apparaten.  Toegang wordt alleen toegestaan vanuit ondersteunde browsers op compatibele apparaten:
* Safari (iOS)
* Chrome (Android)
* Beheerde browser (iOS en Android)

  Niet-ondersteunde browsers worden geblokkeerd.
-   Voor een pc:  


    -   Als het beleid zo is ingesteld dat de pc lid moet zijn van een domein en de pc geen lid is van een domein, wordt in een bericht weergegeven dat contact moet worden opgenomen met de IT-beheerder.  

    -   Als het beleid zo is ingesteld dat de pc lid moet zijn van een domein of aan het beleid moet voldoen en de pc niet aan de vereiste voldoet, wordt er een bericht weergegeven met instructies over het installeren van de bedrijfsportal-app en de registratie.  

 U kunt de toegang tot SharePoint Online blokkeren vanuit de volgende apps:  

-   Microsoft Office Mobile (Android)  

-   Microsoft OneDrive (Android en iOS)  

-   Microsoft Word (Android en iOS)  

-   Microsoft Excel (Android en iOS)  

-   Microsoft PowerPoint (Android en iOS)  

-   Microsoft OneNote (Android en iOS)  

## <a name="configure-conditional-access-for-sharepoint-online"></a>Voorwaardelijke toegang configureren voor SharePoint Online  

### <a name="step-1-configure-active-directory-security-groups"></a>Stap 1: Active Directory-beveiligingsgroepen configureren  
 Voordat u begint, moet u Azure Active Directory-beveiligingsgroepen configureren voor het beleid voor voorwaardelijke toegang. U kunt deze groepen configureren in het **Office 365-beheercentrum** of in de **Intune-accountportal**. Deze groepen bevatten de gebruikers die deel uitmaken van de doelgroep, of op wie het beleid juist niet van toepassing is. Wanneer een gebruiker deel uitmaakt van de doelgroep voor het beleid, moet elk apparaat dat hij of zij gebruikt, aan het beleid voldoen om toegang te krijgen tot bronnen.  

 U kunt twee soorten groepen opgeven in een SharePoint Online-beleid:  

-   **Doelgroepen** â €' bevat groepen gebruikers waarop het beleid van toepassing  

-   **Uitgesloten groepen** â €' bevat groepen gebruikers die uitgesloten van het beleid (optioneel zijn)  

 Als een gebruiker zich in beide groepen bevindt, wordt het beleid niet op de gebruiker toegepast.  

### <a name="step-2-configure-and-deploy-a-compliance-policy"></a>Stap 2: Configureer en implementeer een nalevingsbeleid  
 Zorg ervoor dat u een nalevingsbeleid maakt en implementeert op alle apparaten waarop het SharePoint Online-beleid van toepassing is.  

> [!NOTE]  
>  Terwijl nalevingsbeleid wordt geïmplementeerd voor groepen van Intune of Configuration Manager-verzamelingen, worden de beleidsregels voor voorwaardelijke toegang gericht op Azure Active Directory-beveiligingsgroepen.  

 Zie [Nalevingsbeleid voor apparaten beheren in System Center Configuration Manager](../../protect/deploy-use/device-compliance-policies.md) voor meer informatie over het configureren van het nalevingsbeleid.  

> [!IMPORTANT]  
>  Als u geen nalevingsbeleid hebt geïmplementeerd en daarna het SharePoint Online-beleid inschakelt, krijgen alle apparaten uit de doelgroep toegang.  

 Wanneer u klaar bent, gaat u door naar **Stap 3**.  

###  <a name="BKMK_OneDrive"></a>Stap 3: Het SharePoint Online-beleid configureren  


 Configureer vervolgens het beleid om ervoor te zorgen dat alleen beheerde apparaten en apparaten die aan het beleid voldoen toegang hebben tot SharePoint Online. Dit beleid wordt opgeslagen in Azure Active Directory.

 >[!NOTE]
 >U kunt ook een beleid voor voorwaardelijke toegang maken in de Azure AD-beheerconsole. Azure AD-beheerconsole kunt u het apparaat Intune beleidsregels voor voorwaardelijke toegang (aangeduid als het beleid voor voorwaardelijke toegang op basis van apparaten in Azure AD) naast andere beleidsregels voor voorwaardelijke toegang zoals multi-factor authentication-server maken. U kunt ook beleidsregels voor voorwaardelijke toegang voor Enterprise-apps van derden zoals Salesforce instellen en het selectievakje dat Azure AD ondersteunt. Zie voor meer informatie [het instellen van Azure Active Directory op basis van apparaten voorwaardelijke toegangsbeleid voor toegangsbeheer voor Azure Active Directory verbonden toepassingen](https://azure.microsoft.com/en-us/documentation/articles/active-directory-conditional-access-policy-connected-applications/).  

1.  Klik op **Activa en naleving**op de Configuration Manager-console.  

2.  Selecteer **Beleid voor voorwaardelijke toegang inschakelen voor SharePoint Online**.  

     ![IntuneSASharePointOnlineCAPolicy](media/IntuneSASharePointOnlineCAPolicy.png)  

3.  Onder **Toegang voor toepassingen** kunt u voor Outlook en andere apps die moderne verificatie gebruiken, ervoor kiezen de toegang te beperken tot apparaten die voldoen aan het beleid voor elk platform.  

    > [!TIP]  
    >  **Moderne verificatie** biedt aanmelding bij Office-clients op basis van Active Directory Authentication Library (ADAL).  
    >   
    >  -   Dankzij verificatie op basis van ADAL is voor Office-clients verificatie via een browser (ook wel passieve verificatie) mogelijk.  De gebruiker wordt hierbij naar een aanmeldingspagina geleid om de verificatie uit te voeren.  
    > -   Deze nieuwe aanmeldingsmethode maakt nieuwe scenario's, zoals voorwaardelijke toegang, mogelijk op basis van **apparaatcompatibiliteit** en of **meervoudige verificatie** is uitgevoerd.  
    >   
    >  Dit [artikel](https://support.office.com/en-US/article/How-modern-authentication-works-for-Office-2013-and-Office-2016-client-apps-e4c45989-4b1a-462e-a81b-2a13191cf517) bevat gedetailleerde informatie over de werking van moderne verificatie.  

     Voor windows-pc's moet moet de PC zijn van een domein lid zijn van of ingeschreven met Intune en voldoen. U kunt de volgende vereisten instellen:  

    -   **Apparaten moeten lid zijn van een domein of voldoen aan het beleid.** Dit betekent dat de pc's moeten zijn van een domein gekoppelde of voldoen aan het beleid in Intune instellen. Als de PC niet voldoet niet aan een van deze vereisten voldoet, wordt de gebruiker gevraagd het apparaat inschrijven bij Intune.  

    -   **Apparaten moeten lid zijn van een domein.** Dit betekent dat de pc's lid moeten zijn van een domein om toegang te krijgen tot Exchange Online. Als de pc geen lid is van een domein, wordt de toegang tot e-mail geblokkeerd en wordt de gebruiker gevraagd contact op te nemen met de IT-beheerder.  

    -   **Apparaten moeten voldoen aan het beleid.** Dit betekent dat de pc's moeten zijn geregistreerd in Intune en voldoen. Als de pc niet is geregistreerd, wordt een bericht met instructies voor de registratie weergegeven.  

4.  Onder **browsertoegang** tot SharePoint Online en OneDrive voor bedrijven, kunt u kiezen om toegang tot Exchange Online alleen via de ondersteunde browsers: Safari (iOS) en Chrome (Android). Toegang via andere browsers wordt geblokkeerd.  Dezelfde platformbeperkingen die u hebt geselecteerd voor Toegang tot toepassingen voor OneDrive zijn ook hier van toepassing.

    Op **Android** -apparaten moeten gebruikers de browsertoegang inschakelen.  Om dit te doen de eindgebruiker wordt de â €inschakelen optie Browser Accessâ€ op het ingeschreven apparaat door moeten als volgt inschakelen:
    1.  Open de app **Bedrijfsportal**.
    2.  Ga naar de **instellingen** pagina van de drie puntjes (â €¦) of de menuknop hardware.
    3.  Druk op de knop **Browsertoegang inschakelen** .
    4.  In de browser Chrome meldt u zich af bij Office 365 en vervolgens start u Chrome opnieuw op.

    Op **iOS en Android** -platforms, zal Azure Active Directory een TLS-certificaat (Transport Layer Security) aan het apparaat verlenen om het apparaat te kunnen identificeren dat wordt gebruikt voor het verkrijgen van toegang.  Op het apparaat wordt het certificaat weergegeven met een verzoek aan de eindgebruiker om het certificaat te selecteren, zoals wordt weergegeven in de onderstaande schermafbeeldingen. De eindgebruiker moet dit certificaat selecteren om de browser te kunnen blijven gebruiken.

     **iOS**

     ![schermafbeelding van het certificaat met het verzoek op een ipad](media/mdm-browser-ca-ios-cert-prompt_v2.png)

     **Android**

      ![schermafbeelding van het certificaat met het verzoek op een Android-apparaat](media/mdm-browser-ca-android-cert-prompt.png)

4.  Ga naar het tabblad **Start** en klik in de groep **Koppelingen** op **Voorwaardelijk toegangsbeleid configureren in de Intune-console**. Mogelijk moet u de gebruikersnaam en het wachtwoord opgeven van het account dat wordt gebruikt om Configuration Manager verbinding te laten maken met Intune.  

     De Intune-beheerconsole wordt geopend.  

5.  Klik in de [Microsoft Intune-beheerconsole](https://manage.microsoft.com) op **Beleid** > **Voorwaardelijke toegang** > **SharePoint Online-beleid**.  

6.  Selecteer **Apps blokkeren zodat deze geen toegang hebben tot SharePoint Online als het apparaat niet aan het nalevingsbeleid voldoet**.  

7.  Klik onder **Doelgroepen** op **Wijzigen** om de Active Directory-beveiligingsgroepen te selecteren waarop het beleid van toepassing moet zijn.  

8.  Klik desgewenst onder **Uitgesloten groepen** op **Wijzigen** om de Active Directory-beveiligingsgroepen te selecteren waarop dit beleid niet van toepassing is.  

9. Wanneer u klaar bent, klikt u op **Opslaan**.  

 U hoeft het beleid voor voorwaardelijke toegang niet te implementeren; het wordt direct van kracht.  

 Zie [toegang tot SharePoint Online beheren met Microsoft Intune](https://technet.microsoft.com/library/dn705844.aspx) voor meer informatie over hoe u het beleid vanuit de Intune-console kunt bewaken.  

### <a name="see-also"></a>Zie tevens  

 [Toegang tot services in System Center Configuration Manager beheren](../../protect/deploy-use/manage-access-to-services.md)
