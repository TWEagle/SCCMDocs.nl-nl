---
title: Toegang beheren tot O365-services voor beheerde pc's | Microsoft Docs
description: Informatie over het configureren van voorwaardelijke toegang voor pc's die worden beheerd door System Center Configuration Manager.
ms.custom: na
ms.date: 03/05/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: configmgr-hybrid
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 34024741-edfa-4088-8599-d6bafc331e62
caps.latest.revision: "15"
author: andredm7
ms.author: andredm
manager: angrobe
ms.openlocfilehash: aede531a0406c3d30c9cca957896e002ed22ae51
ms.sourcegitcommit: 51fc48fb023f1e8d995c6c4eacfda7dbec4d0b2f
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 08/07/2017
---
# <a name="manage-access-to-o365-services-for-pcs-managed-by-system-center-configuration-manager"></a>Toegang beheren tot O365-services voor pc’s die worden beheerd door System Center Configuration Manager

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*

Vanaf versie 1602 van Configuration Manager, kunt u voorwaardelijke toegang configureren voor pc's die worden beheerd door System Center Configuration Manager.  

> [!IMPORTANT]  
> Dit is een voorlopige versie-functie beschikbaar zijn in de update 1602, update 1606 en update 1610. Functies van evaluatieversies zijn opgenomen in het product voor vroege testdoeleinden in een productieomgeving, maar mogen niet worden beschouwd als gereed voor productie. Zie [Use pre-release features from updates](../../core/servers/manage/install-in-console-updates.md#bkmk_prerelease) (Functies van evaluatieversies gebruiken) voor meer informatie.
> - Nadat u update 1602 installeert, wordt het onderdeeltype weergegeven als ondanks dat deze voorlopige versie is vrijgegeven.
> - Als u vervolgens een update van 1602 naar 1606, blijft de functie type worden weergegeven als vrijgegeven zelfs via deze voorlopige versie.
> - Als u rechtstreeks naar 1606 van versie 1511 bijwerken, wordt het functietype weergegeven als de voorlopige versie.

Zie [Toegang tot services beheren in System Center Configuration Manager](../../protect/deploy-use/manage-access-to-services.md) als u informatie zoekt over het configureren van voorwaardelijke toegang voor apparaten die zijn ingeschreven en worden beheerd door Intune, of pc's die zijn lid zijn van een domein en niet worden beoordeeld op naleving.

## <a name="supported-services"></a>Ondersteunde services  

-   Exchange Online
-   SharePoint Online

## <a name="supported-pcs"></a>Ondersteunde pc’s  

-   Windows 7
-   Windows 8.1
-   Windows 10

## <a name="supported-windows-servers"></a>Ondersteunde Windows-Servers

-   2008 R2
-   2012
-   2012 R2
-   2016

    > [!IMPORTANT]
    > Voor Windows-Servers die mogelijk zijn er meerdere gebruikers tegelijk aangemeld, moeten hetzelfde beleid voor voorwaardelijke toegang worden geïmplementeerd op alle gebruikers aangemeld.

## <a name="configure-conditional-access"></a>Voorwaardelijke toegang configureren  
 Als u voorwaardelijke toegang wilt instellen, moet u eerst een nalevingsbeleid maken en beleid voor voorwaardelijke toegang configureren. Wanneer u beleidsregels voor voorwaardelijke toegang instelt voor pc's, kunt u vereisen dat pc's compatibel zijn met het nalevingsbeleid om toegang te krijgen tot Exchange Online en SharePoint Online-services.  

### <a name="prerequisites"></a>Vereisten  

-   AD FS-synchronisatie en een O365-abonnement. Het abonnement O365 wordt gebruikt voor het instellen van Exchange Online en SharePoint Online.  

-   Een Microsoft Intune-abonnement. Het Microsoft Intune-abonnement moet worden geconfigureerd in de Configuration Manager-console. Het Intune-abonnement wordt gebruikt om de relay-apparaat compatibiliteitsstatus aan Azure Active Directory en voor de gebruiker-licentieverlening.  

 De pc’s moeten aan de volgende vereisten voldoen:  

-   [Vereisten](https://azure.microsoft.com/en-us/documentation/articles/active-directory-conditional-access-automatic-device-registration/?rnd=1) voor automatische apparaatregistratie bij Azure Active Directory  

     U kunt pc's Azure AD registreren via het nalevingsbeleid.  

    -   Voor Windows 8.1- en Windows 10-pc’s kunt u een Active Directory-groepsbeleid gebruiken om uw apparaten automatisch te registreren bij Azure AD.  

    -   o   Voor Windows 7-pc's moet u via System Center Configuration Manager het softwarepakket voor apparaatregistratie implementeren op uw Windows 7-pc. De [automatische apparaatregistratie met Azure Active Directory for Windows Domain-Joined apparaten](https://azure.microsoft.com/en-us/documentation/articles/active-directory-conditional-access-automatic-device-registration/?rnd=1) onderwerp bevat meer informatie.  

-   Gebruik van Office 2013 of Office 2016 is vereist en moderne verificatie moet zijn [ingeschakeld](https://support.office.com/en-US/article/Using-Office-365-modern-authentication-with-Office-clients-776c0036-66fd-41cb-8928-5495c0f9168a).  

 De stappen die hieronder worden beschreven, zijn van toepassing voor zowel Exchange Online als SharePoint Online  

### <a name="step-1-configure-compliance-policy"></a>Stap 1. Nalevingsbeleid configureren  
 Maak in de Configuration Manager-Console een nalevingsbeleid met de volgende regels:  

-   Registratie in Azure Active Directory vereisen: Deze regel controleert u of het apparaat van de gebruiker lid is van werk plaats naar Azure AD en als dat niet het geval is, wordt het apparaat automatisch geregistreerd bij Azure AD. Automatische inschrijving wordt alleen ondersteund op Windows 8.1. Implementeer een MSI-bestand om automatische inschrijving voor Windows 7-pc's uit te voeren. Zie [Aan de slag met Azure Active Directory-apparaatregistratie](https://azure.microsoft.com/en-us/documentation/articles/active-directory-conditional-access-automatic-device-registration/?rnd=1)voor meer informatie.  

-   **Alle vereiste updates zijn geïnstalleerd met een deadline die ouder zijn dan een bepaald aantal dagen:** Deze regel controleert u of apparaat van de gebruiker alle vereiste updates (opgegeven in de regel vereiste automatische updates) binnen de deadline en respijtperiode door u opgegeven is, en eventuele vereiste updates die nog niet automatisch worden geïnstalleerd.  

-   **BitLocker-stationsversleuteling vereisen:** Dit is een controleert u of het primaire station (bijvoorbeeld C:\\) op het apparaat BitLocker versleuteld. Als Bitlocker-versleuteling niet is ingeschakeld op het primaire station, wordt de toegang tot e-mail en SharePoint-services geblokkeerd.  

-   **Antimalware vereisen:** Dit is een controleert u of de antimalwaresoftware (System Center Endpoint Protection of alleen Windows Defender) is ingeschakeld en worden uitgevoerd. Indien dit niet is ingeschakeld, wordt de toegang tot e-mail en SharePoint-services geblokkeerd.  

### <a name="step-2-evaluate-the-effect-of-conditional-access"></a>Stap 2. Het effect van voorwaardelijke toegang evalueren  
 Voer het rapport voor naleving van voorwaardelijke toegang uit. Dit vindt u in de sectie bewaking onder rapporten > compatibiliteit en instellingen beheren. Hiermee wordt de status van naleving voor alle apparaten weergegeven.  Voor apparaten die worden gerapporteerd als niet-compatibel, wordt de toegang tot Exchange Online en SharePoint Online geblokkeerd.  

 ![CA&#95;naleving&#95;rapport](media/CA_compliance_report.png)  

### <a name="configure-active-directory-security-groups"></a>Active Directory-beveiligingsgroepen configureren  
 U richt de beleidsregels voor voorwaardelijke toegang op gebruikersgroepen, afhankelijk van de soorten beleid. Deze groepen bevatten de gebruikers die deel uitmaken van de doelgroep, of op wie het beleid juist niet van toepassing is. Wanneer een gebruiker deel uitmaakt van de doelgroep voor het beleid, moet elk apparaat dat wordt gebruikt, compatibel zijn om toegang te kunnen krijgen tot de service.  

 Active Directory-beveiligingsgebruikersgroepen Deze groepen moeten worden gesynchroniseerd naar Azure Active Directory. U kunt deze groepen ook configureren in het Office 365-beheercentrum of in de Intune-accountportal.  

 U kunt twee soorten groepen opgeven in elk beleid. :  

-   **Doelgroepen** -gebruikersgroepen waarop het beleid wordt toegepast. Dezelfde groep moet worden gebruikt voor naleving en beleid voor voorwaardelijke toegang.  

-   **Uitgesloten groepen** -gebruikersgroepen die uitgesloten van het beleid (optioneel zijn)  
    Als een gebruiker zich in beide groepen bevindt, wordt het beleid niet op de gebruiker toegepast.  

     Alleen de doelgroepen van het beleid voor voorwaardelijke toegang worden geëvalueerd.  

### <a name="step-3--create-a-conditional-access-policy-for-exchange-online-and-sharepoint-online"></a>Stap 3.  Maak een beleid voor voorwaardelijke toegang tot Exchange Online en SharePoint Online.  

1.  Klik op **Activa en naleving**op de Configuration Manager-console.  

2.  Selecteer **Beleid voor voorwaardelijke toegang inschakelen voor Exchange Online**als u een beleid voor Exchange Online wilt maken.  

     Selecteer **Beleid voor voorwaardelijke toegang inschakelen voor Exchange Online**als u een beleid voor SharePoint Online wilt maken.  

3.  Ga naar het tabblad **Start** en klik in de groep **Koppelingen** op **Voorwaardelijk toegangsbeleid configureren in de Intune-console**. Mogelijk moet u de gebruikersnaam en het wachtwoord opgeven van het account dat wordt gebruikt om Configuration Manager verbinding te laten maken met Intune.  

     De Intune-beheerconsole wordt geopend.  

4.  Voor Exchange Online in de Microsoft Intune-beheerconsole, klikt u op **beleid > voorwaardelijke toegang > Exchange Online-beleid**.  

     SharePoint Online in de Microsoft Intune-beheerconsole, klikt u op **beleid > voorwaardelijke toegang > SharePoint Online-beleid**.  

5.  Stel de vereiste voor Windows-pc’s in op de optie**Apparaten moeten voldoen aan dit beleid**.  

6.  Klik onder **Doelgroepen**op **Wijzigen** om de Active Directory-beveiligingsgroepen te selecteren waarop het beleid van toepassing moet zijn.  

    > [!NOTE]  
    >  De dezelfde beveiligingsgroep van de gebruiker moet worden gebruikt voor het implementeren van compliancy beleid en de doelgroep voor beleid voor voorwaardelijke toegang.  

     Klik desgewenst onder **Uitgesloten groepen**op **Wijzigen** om de Active Directory-beveiligingsgroepen te selecteren waarop dit beleid niet van toepassing is.  

7.  Klik op **Opslaan** om het beleid te maken en op te slaan  

 Eindgebruikers die zijn geblokkeerd vanwege niet-compatibele wordt compatibiliteitsinformatie weergeven in de System Center Configuration Manager Software Center en een nieuwe evaluatie van het beleid wordt gestart wanneer de nalevingsproblemen zijn hersteld.  

<!---
##  <a name="bkmk_KnownIssues"></a> Known issues  
 You may see the following issues when using this feature:  

-   In this 1602 update,  the 5 day compliance is not enforced. Even if compliance check on the end-user's device has happened more than 5 days ago, users still can access Office 365 and SharePoint online.  

-   When a device is not compliant with the compliance policy, the reason is not automatically displayed. The end- user must go to the new Software Center to find the reason for non-compliance. The reason is displayed in the Device compliance section of the Software Center.  

-   Windows 10 users may see multiple access failures when trying to reach O365 and/or SharePoint online resources. Note that conditional access is not fully supported for Windows 10.  
--->
## <a name="see-also"></a>Zie tevens

- [Beveiligen van gegevens en site-infrastructuur met System Center Configuration Manager](../../protect/understand/protect-data-and-site-infrastructure.md)
- [Voorwaardelijke toegang oplossen flow-chart voor Configuration Manager](https://gallery.technet.microsoft.com/Conditional-access-fd747c1a?redir=0)
