---
title: Voorwaardelijke toegang
titleSuffix: Configuration Manager
description: Informatie over het gebruik van voorwaardelijke toegang in System Center Configuration Manager voor het beveiligen van e-mail en andere services.
ms.custom: na
ms.date: 12/22/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: configmgr-hybrid
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 7b04727b-d563-422f-8d59-4dd66215d0b3
caps.latest.revision: "26"
author: andredm7
ms.author: andredm
manager: angrobe
ms.openlocfilehash: f215e1c22d40e1fe402084b665ae624bc0c21d97
ms.sourcegitcommit: 92c3f916e6bbd35b6208463ff406e0247664543a
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 01/02/2018
---
# <a name="manage-access-to-services-in-system-center-configuration-manager"></a>Toegang tot services beheren in System Center Configuration Manager

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*


## <a name="conditional-access-in-system-center-configuration-manager"></a>Voorwaardelijke toegang in System Center Configuration Manager
Gebruik voorwaardelijke toegang voor het specificeren voorwaarden voor het beveiligen van e-mail en andere services op apparaten ingeschreven bij Microsoft Intune.  

 Zie voor informatie over voorwaardelijke toegang op apparaten die worden beheerd met Configuration Manager-client, [toegang beheren tot O365-services voor pc's die worden beheerd door System Center Configuration Manager](../../protect/deploy-use/manage-access-to-o365-services-for-pcs-managed-by-sccm.md).  


 Een typische stroom voor voorwaardelijke toegang kan er als volgt uitzien:  

 ![ConditionalAccess4](media/ConditionalAccess4.png)  

 Gebruik voorwaardelijke toegang voor het beheren van toegang tot de volgende services:  

-   Microsoft Exchange On-premises  

-   Microsoft Exchange Online  

-   Exchange Online-specifiek  

-   SharePoint Online  

-   Skype voor Bedrijven Online

-   Dynamics CRM Online

 Voor het implementeren van voorwaardelijke toegang configureren u twee beleidstypen in Configuration Manager:  

-   **Nalevingsbeleid** bestaat uit optionele beleidsregels die u kunt implementeren voor gebruikersverzamelingen en voor het evalueren van instellingen zoals:  

    -   Wachtwoordcode  

    -   Versleuteling  

    -   Of het apparaat jailbroken of geroot is  

    -   Of e-mail op het apparaat wordt beheerd door een Configuration Manager of Microsoft Intune-beleid  

     Een apparaat rapporteert voldoet aan eventuele beleidsregels voor voorwaardelijke toegang van toepassing als u geen een nalevingsbeleid voor het implementeert.

-   **Beleid voor voorwaardelijke toegang** zijn voor een bepaalde service. Deze beleidsregels definiëren regels zoals welke Azure Active Directory-beveiligingsgebruikersgroepen of Configuration Manager gebruikersverzamelingen als doel in of uitsluiten.  

     U configureert het beleid voor voorwaardelijke toegang Exchange on-premises uit de Configuration Manager-console. Echter, wanneer u een Exchange Online of SharePoint Online-beleid configureert, de Microsoft Intune-beheerconsole wordt geopend om het beleid te configureren.  

     In tegenstelling tot andere Microsoft Intune of Configuration Manager-beleid implementeert u geen beleidsregels voor voorwaardelijke toegang. In plaats daarvan u deze beleidsregels eenmaal configureren en ze gelden voor alle beoogde gebruikers.  

 Wanneer apparaten niet voldoen aan de geconfigureerde voorwaarden, wordt de gebruiker is begeleide echter registratie van het apparaat en het verhelpen van het apparaat compatibiliteitsprobleem.  

Voordat u voorwaardelijke toegang gaat gebruiken moet u controleren of u over de juiste vereisten beschikt:  

## <a name="requirements-for-exchange-online-using-the-shared-multi-tenant-environment"></a>Vereisten voor Exchange Online (met behulp van de gedeelde omgeving met meerdere tenants)
Voorwaardelijke toegang tot Exchange Online ondersteunt apparaten met:
-   Windows 8.1 en hoger (wanneer ingeschreven bij Intune)
-   Windows 7.0 of Windows 8.1 (Wanneer lid van een domein)
-   Windows Phone 8.1 en hoger
-   iOS 7.1 en hoger
-   Android 4.0 en hoger, Samsung KNOX Standard 4.0 en hoger

 **Bovendien**:
-   Apparaten moeten zijn toegevoegd aan de werkplek, waardoor wordt het apparaat geregistreerd bij de Azure Active Directory Device Registration Service (AAD DRS).<br />     
- Pc’s die lid zijn van een domein moeten automatisch via groepsbeleid of MSI bij Azure Active Directory worden geregistreerd.

  De **voorwaardelijke toegang voor pc's** sectie in dit artikel beschrijft alle vereisten voor het inschakelen van voorwaardelijke toegang voor een PC.<br />     
  AAD DRS wordt automatisch geactiveerd voor Microsoft Intune en Office 365-klanten. Klanten die de ADFS Device Registration Service al hebben geïmplementeerd, ziet geen geregistreerde apparaten in hun lokale Active Directory.
-   Office 365-abonnement met inbegrip van Exchange Online (zoals E3) gebruiken. Gebruikers moeten bovendien een licentie voor Exchange Online.
-   Exchange Server-connector is optioneel en Configuration Manager verbinding met Microsoft Exchange Online. Deze connector kunt u controleren van apparaatgegevens via de Configuration Manager-console. Zie [Mobiele apparaten beheren met System Center Configuration Manager en Exchange](../../mdm/deploy-use/manage-mobile-devices-with-exchange-activesync.md) voor meer informatie.
U hoeft niet de connector wilt gebruiken voor nalevingsbeleid of beleidsregels voor voorwaardelijke toegang. Uitvoeren van rapporten over de impact van voorwaardelijke toegang vereist dat de connector.

## <a name="requirements-for-exchange-online-dedicated"></a>Vereisten voor Exchange Online-specifiek
Voorwaardelijke toegang tot Exchange Online-specifiek ondersteunt apparaten met:
-   Windows 8 en hoger (wanneer ingeschreven bij Intune)
-   Windows 7.0 of Windows 8.1 (Wanneer lid van een domein)

  Voorwaardelijke toegang voor pc’s die lid zijn van een domein alleen voor tenants in de nieuwe Exchange Online-specifieke omgeving.
-   Windows Phone 8 en hoger
-   Een iOS-apparaat dat gebruikmaakt van een e-mailclient van Exchange ActiveSync (EAS)
-   Android 4 en hoger.
-   Voor tenants in de oude Exchange Online Dedicated-omgeving:    

  Gebruik de Exchange Server-connector, die Configuration Manager met Microsoft Exchange on-premises verbindt. De connector kunt u mobiele apparaten beheren en kan voorwaardelijke toegang worden ingeschakeld. Zie [Mobiele apparaten beheren met System Center Configuration Manager en Exchange](../../mdm/deploy-use/manage-mobile-devices-with-exchange-activesync.md) voor meer informatie.
-   Voor tenants in de nieuwe Exchange Online Dedicated-omgeving:     
  Exchange Server-connector is optioneel, die Configuration Manager verbinding met Microsoft Exchange Online en helpt bij het beheren van apparaatgegevens. Zie [Mobiele apparaten beheren met System Center Configuration Manager en Exchange](../../mdm/deploy-use/manage-mobile-devices-with-exchange-activesync.md) voor meer informatie. U hoeft niet de connector wilt gebruiken voor nalevingsbeleid of beleidsregels voor voorwaardelijke toegang. Uitvoeren van rapporten over de impact van voorwaardelijke toegang vereist dat de connector.  

## <a name="requirements-for-exchange-on-premises"></a>Vereisten voor Exchange on-premises
Voorwaardelijke toegang tot Exchange on-premises ondersteunt:
-   Windows 8 en hoger (wanneer ingeschreven bij Intune)
-   Windows Phone 8 en hoger
-   Systeemeigen e-mail-app voor iOS
-   Systeemeigen e-mail-app voor Android 4 of hoger
-   Microsoft Outlook-app is niet ondersteund (Android en iOS)

**Bovendien**:

- Versie van Exchange moet Exchange 2010 of hoger
- Matrix van Exchange server-Client Access Server (CAS) wordt ondersteund

> [!TIP]
> Als uw Exchange-omgeving zich in een configuratie met CAS-server, moet u de lokale Exchange-connector om te verwijzen naar een van de CAS-servers configureren.
- Gebruik de Exchange Server-connector, die Configuration Manager met Microsoft Exchange on-premises verbindt. De connector kunt u mobiele apparaten beheren en kan voorwaardelijke toegang worden ingeschakeld. Zie [Mobiele apparaten beheren met System Center Configuration Manager en Exchange](../../mdm/deploy-use/manage-mobile-devices-with-exchange-activesync.md) voor meer informatie.
  - Zorg ervoor dat u van de nieuwste versie van de lokale Exchange-connector gebruikmaakt. De lokale Exchange-connector via de Configuration Manager-console configureren. Zie [Mobiele apparaten beheren met Configuration Manager en Exchange](../../mdm/deploy-use/manage-mobile-devices-with-exchange-activesync.md) voor een gedetailleerde uitleg.
  - Alleen de connector op de primaire site van Configuration Manager configureren

- Exchange ActiveSync kan worden geconfigureerd met verificatie op basis van een certificaat of invoer van gebruikersreferenties


## <a name="requirements-for-skype-for-business-online"></a>Vereisten voor Skype voor bedrijven Online
Voorwaardelijke toegang tot SharePoint Online ondersteunt apparaten met:
 -   iOS 7.1 en hoger
 -   Android 4.0 en hoger
 -   Samsung KNOX Standard 4.0 of hoger

Schakel [moderne verificatie](https://aka.ms/SkypeModernAuth) voor Skype voor bedrijven Online. 

Alle gebruikers moet Skype voor bedrijven Online gebruiken. Als u een implementatie hebt met Skype voor bedrijven Online en Skype voor bedrijven on-premises, geldt beleid voor voorwaardelijke toegang niet voor on-premises gebruikers.

## <a name="requirements-for-sharepoint-online"></a>Vereisten voor SharePoint Online
Voorwaardelijke toegang tot SharePoint Online ondersteunt apparaten met:
 -   Windows 8.1 en hoger (wanneer ingeschreven bij Intune)
 -   Windows 7.0 of Windows 8.1 (Wanneer lid van een domein)
 -   Windows Phone 8.1 en hoger
 -   iOS 7.1 en hoger
 -   Android 4.0 en hoger, Samsung KNOX Standard 4.0 en hoger

 **Bovendien**:
 -   Apparaten moeten zijn toegevoegd aan de werkplek, waardoor wordt het apparaat geregistreerd bij de Azure Active Directory Device Registration Service (AAD DRS).

 Pc’s die lid zijn van een domein moeten automatisch via groepsbeleid of MSI bij Azure Active Directory worden geregistreerd. De **voorwaardelijke toegang voor pc's** sectie in dit artikel beschrijft alle vereisten voor het inschakelen van voorwaardelijke toegang voor een PC.

 AAD DRS wordt automatisch geactiveerd voor Microsoft Intune en Office 365-klanten. Klanten die de ADFS Device Registration Service al hebben geïmplementeerd, ziet geen geregistreerde apparaten in hun lokale Active Directory.
 -   Een SharePoint Online-abonnement is vereist en gebruikers moeten bovendien een licentie voor SharePoint Online.

 ### <a name="conditional-access-for-pcs"></a>Voorwaardelijke toegang voor pc's

 U kunt voorwaardelijke toegang configureren voor pc's waarop Office-bureaubladtoepassingen worden uitgevoerd en toegang tot Exchange Online of SharePoint Online. De pc’s moeten aan de volgende vereisten voldoen:
 -   De PC moet Windows 7.0 of Windows 8.1 worden uitgevoerd
 -   De PC moet een domein zijn toegevoegd of compatibel

 Om hieraan te voldoen, worden de PC moeten zijn ingeschreven bij Microsoft Intune en voldoen aan het beleid.

 U moet pc's die lid zijn van een domein zo instellen dat deze [het apparaat automatisch registreren](https://azure.microsoft.com/en-us/documentation/articles/active-directory-conditional-access-automatic-device-registration/) bij Azure Active Directory.
 -   [Moderne Office 365-verificatie moet zijn ingeschakeld](https://blogs.office.com/2015/03/23/office-2013-modern-authentication-public-preview-announced/) en alle nieuwe Office-updates moeten zijn geïnstalleerd.<br />     Moderne verificatie maakt op basis van Active Directory Authentication Library ADAL aanmelden met Office 2013 Windows-clients en zorgt voor betere beveiliging zoals multi-factor authentication en verificatie op basis van certificaten.
 -   Met het instellen van ADFS worden er regels van kracht die niet-moderne verificatieprotocollen blokkeren.  

## <a name="next-steps"></a>Volgende stappen  
 Lees de volgende onderwerpen voor meer informatie over het configureren van nalevingsbeleidsregels en beleidsregels voor voorwaardelijke toegang voor uw vereiste scenario:  

-   [Nalevingsbeleid voor apparaten in System Center Configuration Manager beheren](../../protect/deploy-use/device-compliance-policies.md)  

-   [Toegang tot e-mail in System Center Configuration Manager beheren](../../protect/deploy-use/manage-email-access.md)  

-   [Toegang tot SharePoint Online in System Center Configuration Manager beheren](../../protect/deploy-use/manage-sharepoint-online-access.md)  

-   [Toegang tot Skype voor Bedrijven Online beheren](../../protect/deploy-use/manage-skype-for-business-online-access.md)  

### <a name="see-also"></a>Zie tevens  

 [Aan de slag met instellingen voor naleving in System Center Configuration Manager](../../compliance/get-started/get-started-with-compliance-settings.md)
