---
title: Voorwaardelijke toegang | Microsoft Docs
description: Informatie over het gebruik van voorwaardelijke toegang in System Center Configuration Manager voor het beveiligen van e-mail en andere services.
ms.custom: na
ms.date: 03/05/2017
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
ms.openlocfilehash: d6933a331bb229f7e378e8f0bfa511f6b0553ae9
ms.sourcegitcommit: 51fc48fb023f1e8d995c6c4eacfda7dbec4d0b2f
ms.translationtype: HT
ms.contentlocale: nl-NL
ms.lasthandoff: 08/07/2017
---
# <a name="manage-access-to-services-in-system-center-configuration-manager"></a>Toegang tot services beheren in System Center Configuration Manager

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*


## <a name="conditional-access-in-system-center-configuration-manager"></a>Voorwaardelijke toegang in System Center Configuration Manager
Gebruik **voorwaardelijke toegang** voor het beveiligen van e-mail en andere services op apparaten die zijn geregistreerd bij Microsoft Intune, afhankelijk van de door u opgegeven voorwaarden.  

 Voor informatie over **voorwaardelijke toegang op pc's die worden beheerd met System Center Configuration Manager** en beoordeeld op naleving, Zie [toegang beheren tot O365-services voor pc's die worden beheerd door System Center Configuration Manager](../../protect/deploy-use/manage-access-to-o365-services-for-pcs-managed-by-sccm.md).  


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

    -   Of e-mail op het apparaat wordt beheerd door een Configuration Manager of Intune-beleid  

     **Als er geen nalevingsbeleid wordt geïmplementeerd op een apparaat, wordt het apparaat als compatibel wordt beschouwd door alle beleidsregels voor voorwaardelijke toegang van toepassing**.  

-   **Beleid voor voorwaardelijke toegang** worden voor een bepaalde service geconfigureerd en definiëren regels zoals welke Azure Active Directory-beveiligingsgebruikersgroepen of Configuration Manager-gebruikersverzamelingen worden opgenomen of uitgesloten.  

     U configureert het voorwaardelijke-toegangsbeleid van de On-Premises Exchange vanuit de Configuration Manager-console. Echter, wanneer u een Exchange Online of SharePoint Online-beleid configureert, Hiermee opent u de Intune-beheerconsole waar u het beleid configureert.  

     In tegenstelling tot andere Intune of Configuration Manager-beleid implementeert u geen beleidsregels voor voorwaardelijke toegang. In plaats daarvan configureert u deze eenmalig en past u deze toe op alle bedoelde gebruikers.  

 Wanneer apparaten niet voldoen aan de voorwaarden die u configureert, wordt de gebruiker geleid door de procedure voor het inschrijven van het apparaat en het verhelpen van het probleem dat verhindert dat het apparaat compatibel is.  

**Voordat u** u aan de slag met voorwaardelijke toegang, zorg ervoor dat u de juiste **vereisten** voldaan:  

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

  In de sectie **Voorwaardelijke toegang voor pc's** in dit onderwerp vindt u een beschrijving van alle vereisten voor het inschakelen van voorwaardelijke toegang voor een pc.<br />     
  AAD DRS wordt automatisch geactiveerd voor Intune- en Office 365-klanten. Klanten die de ADFS Device Registration Service al hebben geïmplementeerd, zien geen geregistreerde apparaten in hun on-premises Active Directory.
-   U moet een Office 365-abonnement met inbegrip van Exchange Online (zoals E3) gebruiken en gebruikers moeten bovendien een licentie voor Exchange Online.
-   De optionele **Exchange Server-connector** is optioneel en Configuration Manager verbinding met Microsoft Exchange Online en helpt u bij het controleren van apparaatgegevens via de Configuration Manager-console (Zie [mobiele apparaten beheren met System Center Configuration Manager en Exchange](../../mdm/deploy-use/manage-mobile-devices-with-exchange-activesync.md)).
U hoeft de connector niet te gebruiken om nalevingsbeleid of beleidsregels voor voorwaardelijke toegang te kunnen gebruiken, maar deze is vereist voor het uitvoeren van rapporten die helpen bij het evalueren van de impact van voorwaardelijke toegang.

## <a name="requirements-for-exchange-online-dedicated"></a>Vereisten voor Exchange Online-specifiek
Voorwaardelijke toegang tot Exchange Online-specifiek ondersteunt apparaten met:
-   Windows 8 en hoger (wanneer ingeschreven bij Intune)
-   Windows 7.0 of Windows 8.1 (Wanneer lid van een domein)

  Voorwaardelijke toegang voor pc’s die lid zijn van een domein alleen voor tenants in de nieuwe Exchange Online-specifieke omgeving.
-   Windows Phone 8 en hoger
-   Een iOS-apparaat dat gebruikmaakt van een e-mailclient van Exchange ActiveSync (EAS)
-   Android 4 en hoger.
-   Voor tenants in de **oude Exchange Online Dedicated-omgeving**:    

  Moet u de **Exchange Server-connector** die Configuration Manager met Microsoft Exchange On-premises verbindt. Hiermee kunt u uw mobiele apparaten beheren en kan voorwaardelijke toegang worden ingeschakeld (zie [Mobiele apparaten beheren met Configuration Manager en Exchange](../../mdm/deploy-use/manage-mobile-devices-with-exchange-activesync.md)).
-   Voor tenants in de **nieuwe Exchange Online Dedicated-omgeving**:     
  De optionele **Exchange Server-connector** maakt Configuration Manager verbinding met Microsoft Exchange Online en helpt bij het beheren van apparaatgegevens (Zie [mobiele apparaten beheren met System Center Configuration Manager en Exchange](../../mdm/deploy-use/manage-mobile-devices-with-exchange-activesync.md)). U hoeft de connector niet te gebruiken om nalevingsbeleid of beleidsregels voor voorwaardelijke toegang te kunnen gebruiken, maar deze is vereist voor het uitvoeren van rapporten die helpen bij het evalueren van de impact van voorwaardelijke toegang.  

## <a name="requirements-for-exchange-on-premises"></a>Vereisten voor Exchange On-premises
Voorwaardelijke toegang tot Exchange On-premises ondersteunt:
-   Windows 8 en hoger (wanneer ingeschreven bij Intune)
-   Windows Phone 8 en hoger
-   Systeemeigen e-mail-app voor iOS
-   Systeemeigen e-mail-app voor Android 4 of hoger
-   Microsoft Outlook-app is niet ondersteund (Android en iOS).

**Bovendien**:

-  Versie van Exchange moet Exchange 2010 of hoger. De CAS-matrix (Client Access Server) voor Exchange-servers wordt ondersteund.

> [!TIP]
> Als uw Exchange-omgeving zich in een configuratie met CAS-server, moet u de lokale Exchange-connector om te verwijzen naar een van de CAS-servers configureren.
- Moet u de **Exchange Server-connector** die Configuration Manager met Microsoft Exchange On-premises verbindt. Hiermee kunt u uw mobiele apparaten beheren en kan voorwaardelijke toegang worden ingeschakeld (zie [Mobiele apparaten beheren met Configuration Manager en Exchange](../../mdm/deploy-use/manage-mobile-devices-with-exchange-activesync.md)).
  - Gebruik de nieuwste versie van de **on-premises Exchange-Connector**. De on-premises Exchange-connector moet worden geconfigureerd via de Configuration Manager-console. Zie [Mobiele apparaten beheren met Configuration Manager en Exchange](../../mdm/deploy-use/manage-mobile-devices-with-exchange-activesync.md) voor een gedetailleerde uitleg.
  - De connector moet alleen op de primaire site voor System Center Configuration Manager worden geconfigureerd.</li><li>Deze connector ondersteunt de Exchange CAS-omgeving. <br />        Wanneer u de connector configureert, moet u deze instellen zodat deze communiceert met een van de Exchange CAS-servers.

- Exchange ActiveSync kan worden geconfigureerd met verificatie op basis van een certificaat of invoer van gebruikersreferenties


## <a name="requirements-for-skype-for-business-online"></a>Vereisten voor Skype voor bedrijven Online
Voorwaardelijke toegang tot SharePoint Online ondersteunt apparaten met:
 -   iOS 7.1 en hoger
 -   Android 4.0 en hoger
 -   Samsung KNOX Standard 4.0 of hoger

**Bovendien** moet u moderne verificatie voor Skype voor bedrijven Online inschakelen. Vul dit [Connect-formulier](https://connect.microsoft.com/office/Survey/NominationSurvey.aspx?SurveyID=17299&ProgramID=8715) in om u in te schrijven voor het programma voor moderne verificatie.

Uw eindgebruikers moeten gebruikmaken van Skype voor Bedrijven Online. Als u een implementatie hebt met Skype voor Bedrijven Online en Skype voor Bedrijven on-premises, wordt beleid voor voorwaardelijke toegang niet toegepast op eindgebruikers die zich in de on-premises-implementatie bevinden.

## <a name="requirements-for-sharepoint-online"></a>Vereisten voor SharePoint Online
Voorwaardelijke toegang tot SharePoint Online ondersteunt apparaten met:
 -   Windows 8.1 en hoger (wanneer ingeschreven bij Intune)
 -   Windows 7.0 of Windows 8.1 (Wanneer lid van een domein)
 -   Windows Phone 8.1 en hoger
 -   iOS 7.1 en hoger
 -   Android 4.0 en hoger, Samsung KNOX Standard 4.0 en hoger

 **Bovendien**:
 -   Apparaten moeten zijn toegevoegd aan de werkplek, waardoor wordt het apparaat geregistreerd bij de Azure Active Directory Device Registration Service (AAD DRS).

 Pc’s die lid zijn van een domein moeten automatisch via groepsbeleid of MSI bij Azure Active Directory worden geregistreerd. In de sectie **Voorwaardelijke toegang voor pc's** in dit onderwerp vindt u een beschrijving van alle vereisten voor het inschakelen van voorwaardelijke toegang voor een pc.

 AAD DRS wordt automatisch geactiveerd voor Intune- en Office 365-klanten. Klanten die de ADFS Device Registration Service al hebben geïmplementeerd, zien geen geregistreerde apparaten in hun on-premises Active Directory.
 -   Een SharePoint Online-abonnement is vereist en gebruikers moeten bovendien een licentie voor SharePoint Online.

 ### <a name="conditional-access-for-pcs"></a>Voorwaardelijke toegang voor pc's

 U kunt voorwaardelijke toegang instellen voor pc's waarop Office-bureaubladtoepassingen worden uitgevoerd zodat deze toegang hebben tot **Exchange Online** en **SharePoint Online** als de pc's aan de volgende vereisten voldoen:
 -   De PC moet Windows 7.0 of Windows 8.1 worden uitgevoerd.
 -   De PC moet zijn van een domein gekoppelde of compatibel.

 Om hieraan te voldoen, de PC zijn ingeschreven in Intune en voldoen aan het beleid.

 U moet pc's die lid zijn van een domein zo instellen dat deze [het apparaat automatisch registreren](https://azure.microsoft.com/en-us/documentation/articles/active-directory-conditional-access-automatic-device-registration/) bij Azure Active Directory.
 -   [Moderne Office 365-verificatie moet zijn ingeschakeld](https://blogs.office.com/2015/03/23/office-2013-modern-authentication-public-preview-announced/) en alle nieuwe Office-updates moeten zijn geïnstalleerd.<br />     Moderne verificatie brengt op Active Directory Authentication Library (ADAL) gebaseerde aanmelding naar Windows-clients met Office 2013 en zorgt voor betere beveiliging zoals **meervoudige verificatie**en **verificatie op basis van een certificaat**.
 -   Met het instellen van ADFS worden er regels van kracht die niet-moderne verificatieprotocollen blokkeren.  

## <a name="next-steps"></a>Volgende stappen  
 Lees de volgende onderwerpen voor meer informatie over het configureren van nalevingsbeleidsregels en beleidsregels voor voorwaardelijke toegang voor uw vereiste scenario:  

-   [Nalevingsbeleid voor apparaten in System Center Configuration Manager beheren](../../protect/deploy-use/device-compliance-policies.md)  

-   [Toegang tot e-mail in System Center Configuration Manager beheren](../../protect/deploy-use/manage-email-access.md)  

-   [Toegang tot SharePoint Online in System Center Configuration Manager beheren](../../protect/deploy-use/manage-sharepoint-online-access.md)  

-   [Toegang tot Skype voor Bedrijven Online beheren](../../protect/deploy-use/manage-skype-for-business-online-access.md)  

### <a name="see-also"></a>Zie tevens  

 [Aan de slag met instellingen voor naleving in System Center Configuration Manager](../../compliance/get-started/get-started-with-compliance-settings.md)
