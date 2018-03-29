---
title: Toegang tot SharePoint Online beheren
titleSuffix: Configuration Manager
description: Informatie over het gebruiken van System Center Configuration Manager SharePoint Online beleid voor voorwaardelijke toegang voor het beheren van toegang tot OneDrive.
ms.custom: na
ms.date: 12/09/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-hybrid
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 49cec466-1676-4fe2-a2fe-5004f01d735e
caps.latest.revision: ''
caps.handback.revision: ''
author: arob98
ms.author: angrobe
manager: angrobe
ms.openlocfilehash: ac696941e701dd5d42500b2811bec136e64a28fe
ms.sourcegitcommit: a19e12d5c3198764901d44f4df7c60eb542e765f
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 03/28/2018
---
# <a name="manage-sharepoint-online-access-in-system-center-configuration-manager"></a>Toegang tot SharePoint Online in System Center Configuration Manager beheren

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*


Beleid voor voorwaardelijke toegang van Configuration Manager voor **SharePoint Online** beheert de toegang tot OneDrive voor bedrijven-bestanden die zijn opgeslagen in SharePoint Online. Toegang is gebaseerd op de door u opgegeven voorwaarden.
U kunt toegang tot SharePoint Online beheren vanuit de volgende apps voor de genoemde platforms:  

-   Microsoft Office Mobile (Android)  

-   Microsoft OneDrive (Android en iOS)  

-   Microsoft Word (Android en iOS)  

-   Microsoft Excel (Android en iOS)  

-   Microsoft PowerPoint (Android en iOS)  

-   Microsoft OneNote (Android en iOS)

Office-bureaubladtoepassingen hebben toegang tot SharePoint Online op pc's met:  

-   Office Desktop 2013 en hoger waarvoor [moderne verificatie](https://support.office.com/article/Using-Office-365-modern-authentication-with-Office-clients-776c0036-66fd-41cb-8928-5495c0f9168a) is ingeschakeld.  

-   Windows 7.0 of Windows 8.1  

> [!NOTE]  
>  Pc's moeten lid zijn van domein of voldoen aan de beleidsregels in Intune.  



 Wanneer een gebruiker in de doelgroep verbinding maken met een bestand met een ondersteunde app, zoals OneDrive op hun apparaat probeert, wordt de volgende evaluatie uitgevoerd:  

 ![ConditionalAccess8&#45;6](media/ConditionalAccess8-6.png)  

 Om verbinding te kunnen maken met de vereiste bestanden moet het apparaat waarop OneDrive wordt uitgevoerd:  

-   Met Microsoft Intune worden ingeschreven of PC die lid van een domein.  

-   Registreer het apparaat bij Azure Active Directory (Azure AD). Deze registratie gebeurt automatisch wanneer het apparaat wordt geregistreerd bij Intune.  

     Voor domein-pc's, moet u dit instellen maximaal [automatisch registreren](/azure/active-directory/device-management-hybrid-azuread-joined-devices-setup) met Azure AD.  

-   Voldoen aan het geïmplementeerde nalevingsbeleid Configuration Manager  

    Azure AD slaat de apparaatstatus. Deze toegang verleent of blokkeert tot de bestanden op basis van de door u opgegeven voorwaarden.  

    Als een voorwaarde wordt niet voldaan, wordt de gebruiker weergegeven met een van de volgende berichten te zien wanneer deze zich aanmeldt:  

-   Als het apparaat is niet geregistreerd bij Intune of niet is geregistreerd in Azure AD, wordt een bericht weergegeven met instructies over het installeren van de bedrijfsportal-app en het inschrijven.  

-   Als het apparaat niet compatibel is, wordt een bericht weergegeven waarin de gebruiker naar de Intune-webportal wordt verwezen. Er vindt informatie over het probleem en hoe worden opgelost.  

- Voor mobiele apparaten:

  U kunt de toegang beperken tot SharePoint Online wanneer deze vanuit een browser op **iOS** en **Android** apparaten. Toegang is alleen toegestaan vanaf ondersteunde browsers op compatibele apparaten:  
    - Safari (iOS)
    - Chrome (Android)
    - Beheerde browser (iOS en Android)  

    Niet-ondersteunde browser worden geblokkeerd.  

-   Voor een pc:  


    -   Als het beleid is ingesteld dat aan domein toevoegen en de PC niet verbonden met het domein is, wordt een bericht weergegeven dat contact op met de IT-beheerder.  

    -   Als het beleid is ingesteld dat domein of voldoen, en de PC niet aan de vereiste voldoet, wordt een bericht weergegeven met instructies over het installeren van de bedrijfsportal-app en het inschrijven.  

U kunt de toegang tot SharePoint Online blokkeren vanuit de volgende apps:  

-   Microsoft Office Mobile (Android)  

-   Microsoft OneDrive (Android en iOS)  

-   Microsoft Word (Android en iOS)  

-   Microsoft Excel (Android en iOS)  

-   Microsoft PowerPoint (Android en iOS)  

-   Microsoft OneNote (Android en iOS)  



## <a name="configure-conditional-access-for-sharepoint-online"></a>Voorwaardelijke toegang configureren voor SharePoint Online  

### <a name="step-1-configure-active-directory-security-groups"></a>Stap 1: Active Directory-beveiligingsgroepen configureren  
 Voordat u begint, moet u Azure AD-beveiligingsgroepen voor het beleid voor voorwaardelijke toegang configureren. U kunt deze groepen configureren in het **Office 365-beheercentrum**of in de **Intune-accountportal**. Deze groepen bevatten de gebruikers die gericht of uitgesloten van het beleid zijn. Wanneer een gebruiker door een beleid is gericht, wordt elk apparaat die dat wordt gebruikt moet voldoen aan het beleid voor toegang tot bronnen.  

 U kunt twee soorten groepen opgeven in een SharePoint Online-beleid:  

-   **Doelgroepen**: Bevat groepen gebruikers waarop het beleid van toepassing is  

-   **Uitgesloten groepen**: Dit zijn groepen gebruikers die uitgesloten van het beleid (optioneel zijn)  

 Als een gebruiker zich in beide groepen, zijn ze uitgesloten van het beleid.  

### <a name="step-2-configure-and-deploy-a-compliance-policy"></a>Stap 2: Configureer en implementeer een nalevingsbeleid  
 Maak en implementeer een nalevingsbeleid op alle apparaten waarop het SharePoint Online-beleid is gericht.  

> [!NOTE]   
>  Terwijl nalevingsbeleid wordt geïmplementeerd voor groepen van Intune of Configuration Manager-verzamelingen, worden de beleidsregels voor voorwaardelijke toegang gericht op Azure AD-beveiligingsgroepen.  

 Zie [Nalevingsbeleid voor apparaten beheren in System Center Configuration Manager](../../protect/deploy-use/device-compliance-policies.md) voor meer informatie over het configureren van het nalevingsbeleid.  

> [!IMPORTANT]  
>  Als u een nalevingsbeleid dat nog niet hebt geïmplementeerd en daarna het SharePoint Online-beleid inschakelt, worden alle apparaten uit de doelgroep toegang.  

   

###  <a name="BKMK_OneDrive"></a> Stap 3: Het SharePoint Online-beleid configureren  

 Configureer vervolgens het beleid om ervoor te zorgen dat alleen beheerde apparaten en apparaten die aan het beleid voldoen toegang hebben tot SharePoint Online. Dit beleid wordt opgeslagen in Azure AD.

 >[!NOTE]
 >U kunt ook een beleid voor voorwaardelijke toegang maken in de Azure AD-beheerconsole. De Azure AD-beheerconsole kunt u het beleid voor voorwaardelijke toegang van Intune apparaat maken. Azure AD verwijst naar dit beleid als beleid voor voorwaardelijke toegang op basis van apparaten. U kunt ook andere beleidsregels voor voorwaardelijke toegang, zoals multi-factor authentication-server maken. U kunt beleid voor voorwaardelijke toegang voor derden zakelijke apps die Azure AD, zoals Salesforce en vak ondersteunt instellen in de portal. Zie voor meer informatie [het instellen van Azure AD voorwaardelijke toegang op basis van apparaten beleid voor toegangsbeheer voor Azure AD verbonden toepassingen](/azure/active-directory/active-directory-conditional-access-policy-connected-applications).  

1.  Klik op **Activa en naleving**op de Configuration Manager-console.  

2.  Selecteer **beleid voor voorwaardelijke toegang inschakelen voor SharePoint Online**.  

     ![IntuneSASharePointOnlineCAPolicy](media/IntuneSASharePointOnlineCAPolicy.png)  

3.  Onder **Toegang voor toepassingen** kunt u voor Outlook en andere apps die moderne verificatie gebruiken, ervoor kiezen de toegang te beperken tot apparaten die voldoen aan het beleid voor elk platform.  

    > [!TIP]  
    >  **Moderne verificatie** biedt op basis van Active Directory Authentication Library ADAL aanmelden bij Office-clients.  
    >   
    >  -   De verificatie op basis van ADAL kunnen Office-clients verificatie op basis van een browser (ook wel passieve verificatie). De gebruiker wordt hierbij naar een aanmeldingspagina geleid om de verificatie uit te voeren.  
    > -   Deze nieuwe aanmeldingsmethode maakt nieuwe scenario's zoals voorwaardelijke toegang op basis van **apparaatcompatibiliteit**, en of **multi-factorauthenticatie** is uitgevoerd.  
    >   
    >  Zie voor meer informatie [hoe moderne verificatie werkt voor apps van Office 2013 en Office 2016 client](https://support.office.com/article/How-modern-authentication-works-for-Office-2013-and-Office-2016-client-apps-e4c45989-4b1a-462e-a81b-2a13191cf517).  

     Voor windows-pc's moet moet de PC zijn van een domein lid zijn van of ingeschreven met Intune en voldoen. U kunt de volgende vereisten instellen:  

    -   **Apparaten moeten domein zijn toegevoegd of compatibel**: De pc's moeten een domein zijn toegevoegd of voldoen aan het beleid in Intune instellen. Als de PC niet voldoet aan een van deze vereisten, wordt de gebruiker gevraagd het apparaat inschrijven bij Intune.  

    -   **Apparaten moeten zijn verbonden met het domein**: De pc's moeten zijn van een domein zijn toegevoegd voor toegang tot Exchange Online. Als de PC geen lid van domein is, toegang tot e-mail geblokkeerd en wordt de gebruiker gevraagd contact opnemen met de IT-beheerder.  

    -   **Apparaten moeten voldoen**: De pc's moeten zijn ingeschreven in Intune en voldoen. Als de PC niet is ingeschreven, wordt een bericht met instructies voor het inschrijven weergegeven.  

4.  Onder **browsertoegang** tot SharePoint Online en OneDrive voor bedrijven, kunt u kiezen om toegang tot Exchange Online alleen via de ondersteunde browsers: Safari (iOS) en Chrome (Android). Toegang vanaf andere browsers wordt geblokkeerd. Dezelfde platformbeperkingen die u hebt geselecteerd voor Toegang tot toepassingen voor OneDrive zijn ook hier van toepassing.

    Op **Android** apparaten, gebruikers moeten inschakelen de **Browsertoegang inschakelen** optie op het ingeschreven apparaat als volgt:
    1.  Open de app **Bedrijfsportal**.
    2.  Ga naar de **instellingen** pagina van de drie puntjes (...) of de menuknop hardware.
    3.  Druk op de knop **Browsertoegang inschakelen** .
    4.  In de browser Chrome meldt u zich af bij Office 365 en vervolgens start u Chrome opnieuw op.

    Op **iOS en Android** platforms te bepalen welk apparaat dat wordt gebruikt voor toegang tot de Azure AD-service een TLS-certificaat uitgeeft aan het apparaat. Het apparaat wordt het certificaat met een prompt weergegeven voor de eindgebruiker het certificaat te selecteren, zoals in de volgende schermafbeeldingen: De eindgebruiker moet dit certificaat selecteren voordat u ze kunnen blijven gebruiken van de browser.

     **iOS**

     ![Schermopname van het certificaatprompt op een iPad](media/mdm-browser-ca-ios-cert-prompt_v2.png)

     **Android**

      ![schermafbeelding van het certificaat met het verzoek op een Android-apparaat](media/mdm-browser-ca-android-cert-prompt.png)

4.  Ga naar het tabblad **Start** en klik in de groep **Koppelingen** op **Voorwaardelijk toegangsbeleid configureren in de Intune-console**. Mogelijk moet u de gebruikersnaam en het wachtwoord opgeven van het account dat wordt gebruikt om Configuration Manager verbinding te laten maken met Intune.  

     De Intune-beheerconsole wordt geopend.  

5.  Klik in de [Microsoft Intune-beheerconsole](https://manage.microsoft.com) op **Beleid** > **Voorwaardelijke toegang** > **SharePoint Online-beleid**.  

6.  Selecteer **Apps blokkeren zodat deze geen toegang hebben tot SharePoint Online als het apparaat niet aan het nalevingsbeleid voldoet**.  

7.  Onder **doelgroepen**, klikt u op **wijzigen** selecteren van de Azure AD-beveiligingsgroepen waarop het beleid van toepassing is.  

8.  Onder **uitgesloten groepen**desgewenst klikt u op **wijzigen** om de Azure AD-beveiligingsgroepen die uitgesloten van dit beleid zijn te selecteren.  

9. Wanneer u klaar bent, klikt u op **Opslaan**.  

 U hoeft te implementeren van beleid voor voorwaardelijke toegang, het wordt direct van kracht.  

 Zie [toegang tot SharePoint Online beheren met Microsoft Intune](/intune-classic/deploy-use/restrict-access-to-sharepoint-online-with-microsoft-intune) voor meer informatie over hoe u het beleid vanuit de Intune-console kunt bewaken.  

### <a name="see-also"></a>Zie tevens  

 [Toegang tot services in System Center Configuration Manager beheren](../../protect/deploy-use/manage-access-to-services.md)
