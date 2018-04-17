---
title: Toegang beheren tot O365-services
titleSuffix: Configuration Manager
description: Informatie over het configureren van voorwaardelijke toegang tot Office 365-services voor pc's die worden beheerd door System Center Configuration Manager.
ms.custom: na
ms.date: 04/10/2018
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-hybrid
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 34024741-edfa-4088-8599-d6bafc331e62
caps.latest.revision: 15
author: aczechowski
ms.author: aaroncz
manager: dougeby
ms.openlocfilehash: 1e02cb911397d5f1f837996318b12049d328c9c3
ms.sourcegitcommit: fb84bcb31d825f454785e3d9d8be669e00fe2b27
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/16/2018
---
# <a name="manage-access-to-o365-services-for-pcs-managed-by-system-center-configuration-manager"></a>Toegang beheren tot O365-services voor pc’s die worden beheerd door System Center Configuration Manager

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*

<!--1191496-->
Voorwaardelijke toegang tot Office 365-services voor pc's die worden beheerd door Configuration Manager configureren.  

> [!Note]  
> Configuration Manager deze optionele functie standaard niet ingeschakeld. Voordat u deze gebruikt, moet u deze functie inschakelen. Zie voor meer informatie [optionele functies van updates inschakelen](/sccm/core/servers/manage/install-in-console-updates#bkmk_options).<!--505213-->  


Zie voor meer informatie over het configureren van voorwaardelijke toegang voor apparaten zijn ingeschreven en beheerd door Microsoft Intune [toegang tot services in System Center Configuration Manager beheren](../../protect/deploy-use/manage-access-to-services.md). Dat artikel bevat ook informatie over apparaten die zijn van een domein is toegevoegd en op compatibiliteit geëvalueerd.

## <a name="supported-services"></a>Ondersteunde services  

-   Exchange Online
-   SharePoint Online

## <a name="supported-pcs"></a>Ondersteunde pc’s  

-   Windows 7
-   Windows 8.1
-   Windows 10

## <a name="supported-windows-servers"></a>Ondersteunde Windows-Servers

-   Windows Server 2008 R2
-   Windows Server 2012
-   Windows Server 2012 R2
-   Windows Server 2016

    > [!IMPORTANT]
    > Voor Windows-Servers die mogelijk zijn er meerdere gebruikers tegelijk aangemeld, hetzelfde beleid voor voorwaardelijke toegang op al deze gebruikers te implementeren.

## <a name="configure-conditional-access"></a>Voorwaardelijke toegang configureren  
 Als u voorwaardelijke toegang instelt, moet u eerst een nalevingsbeleid maken en configureren van beleid voor voorwaardelijke toegang. Wanneer u beleidsregels voor voorwaardelijke toegang voor pc's configureert, kunt u vereisen dat de pc's compatibel zijn om toegang tot Exchange Online en SharePoint Online-services zijn.  

### <a name="prerequisites"></a>Vereisten  

-   AD FS-synchronisatie en een O365-abonnement. Het abonnement O365 wordt gebruikt voor het instellen van Exchange Online en SharePoint Online.  

-   Een Microsoft Intune-abonnement. Het Microsoft Intune-abonnement moet worden geconfigureerd in de Configuration Manager-console. Het Intune-abonnement wordt gebruikt om de relay-apparaat compatibiliteitsstatus aan Azure Active Directory en voor de gebruiker-licentieverlening.  

 De pc’s moeten aan de volgende vereisten voldoen:  

-   [Vereisten](https://docs.microsoft.com/azure/active-directory/device-management-hybrid-azuread-joined-devices-setup) voor automatische apparaatregistratie bij Azure Active Directory  

     U kunt pc's Azure AD registreren via het nalevingsbeleid.  

    -   Voor Windows 8.1- en Windows 10-pc’s kunt u een Active Directory-groepsbeleid gebruiken om uw apparaten automatisch te registreren bij Azure AD.  

    -   o   Voor Windows 7-pc's moet u via System Center Configuration Manager het softwarepakket voor apparaatregistratie implementeren op uw Windows 7-pc. De [automatische apparaatregistratie met Azure Active Directory for Windows Domain-Joined apparaten](https://docs.microsoft.com/azure/active-directory/device-management-hybrid-azuread-joined-devices-setup) artikel bevat meer informatie.  

-   Gebruik van Office 2013 of Office 2016 is vereist en moderne verificatie moet zijn [ingeschakeld](https://support.office.com/article/Using-Office-365-modern-authentication-with-Office-clients-776c0036-66fd-41cb-8928-5495c0f9168a).  

 De volgende stappen gelden voor Exchange Online en SharePoint Online  

### <a name="step-1-configure-compliance-policy"></a>Stap 1. Nalevingsbeleid configureren  
 Maak in de Configuration Manager-Console een nalevingsbeleid met de volgende regels:  

-   **Registratie in Azure Active Directory vereisen:** Deze regel controleert u of het apparaat van de gebruiker lid is van werk plaats naar Azure AD en als dat niet het geval is, wordt het apparaat automatisch geregistreerd bij Azure AD. Automatische inschrijving wordt alleen ondersteund op Windows 8.1. Implementeer een MSI-bestand om automatische inschrijving voor Windows 7-pc's uit te voeren. Zie voor meer informatie [automatische apparaatregistratie met Azure Active Directory](https://docs.microsoft.com/azure/active-directory/device-management-hybrid-azuread-joined-devices-setup)  

-   **Alle vereiste updates zijn geïnstalleerd met een deadline die ouder zijn dan een bepaald aantal dagen:** Geef de waarde voor de respijtperiode van de deadline van de implementatie voor de vereiste updates op het apparaat van de gebruiker. Ook automatisch deze regel toe te voegen, worden eventuele vereiste updates geïnstalleerd. Geef de vereiste updates in de **vereiste automatische updates** regel.   

-   **BitLocker-stationsversleuteling vereisen:** Deze regel controleert u of het primaire station (bijvoorbeeld C:\\) op het apparaat BitLocker versleuteld. Als Bitlocker-versleuteling niet is ingeschakeld op het primaire apparaat toegang tot e-mail en SharePoint services wordt geblokkeerd.  

-   **Antimalware vereisen:** Deze regel controleert of System Center Endpoint Protection of Windows Defender ingeschakeld en worden uitgevoerd is. Indien dit niet is ingeschakeld, wordt de toegang tot e-mail en SharePoint-services geblokkeerd.  

-   **Gerapporteerd als in orde door Health Attestation-Service:** Deze voorwaarde bevat vier subregels om te controleren van de naleving van het apparaat op basis van het apparaat health attestation-service. Zie voor meer informatie [Health attestation](/sccm/core/servers/manage/health-attestation). 

    - **BitLocker moet zijn ingeschakeld op het apparaat vereisen**
    - **Beveiligd opstarten moet zijn ingeschakeld op het apparaat vereist** 
    - **Code-integriteit worden ingeschakeld op het apparaat vereist**
    - **Vroegtijdig starten Anti-Malware worden ingeschakeld op het apparaat vereist**  

    >[!Tip]  
    > De criteria voor voorwaardelijke toegang voor de health attestation van apparaten is geïntroduceerd in versie 1710 als een [functie van de voorlopige versie](/sccm/core/servers/manage/pre-release-features). Vanaf versie 1802, deze functie is niet langer een voorlopige versie.<!--1235616-->  

    > [!Note]  
    > Configuration Manager deze optionele functie standaard niet ingeschakeld. Voordat u deze gebruikt, moet u deze functie inschakelen. Zie voor meer informatie [optionele functies van updates inschakelen](/sccm/core/servers/manage/install-in-console-updates#bkmk_options).<!--505213-->  

### <a name="step-2-evaluate-the-effect-of-conditional-access"></a>Stap 2. Het effect van voorwaardelijke toegang evalueren  
 Voer de **rapport voor naleving van voorwaardelijke toegang**. Kan worden gevonden in **bewaking** werkruimte **rapporten** > **compatibiliteit en instellingen beheren**. Dit rapport geeft de status van naleving voor alle apparaten. Apparaten die rapporteren als niet-compatibel in toegang tot Exchange Online en SharePoint Online geblokkeerd.  

 ![Configuration Manager-console, werkruimte bewaking, rapportage, rapporten, compatibiliteit en instellingen beheren: Rapport voor naleving van voorwaardelijke toegang](media/CA_compliance_report.png)  

### <a name="configure-active-directory-security-groups"></a>Active Directory-beveiligingsgroepen configureren  
 U richt de beleidsregels voor voorwaardelijke toegang op gebruikersgroepen, afhankelijk van de soorten beleid. Deze groepen bevatten de gebruikers die de doelen van beleid of uitgesloten van het beleid. Wanneer een beleid is bedoeld voor een gebruiker, moet elk apparaat dat ze gebruiken compatibel toegang tot de service zijn.  

 Active Directory-beveiligingsgebruikersgroepen Deze groepen moeten worden gesynchroniseerd naar Azure Active Directory. U kunt deze groepen ook configureren in het Office 365-beheercentrum of in de Intune-accountportal.  

 U kunt twee soorten groepen opgeven in elk beleid. :  

-   **Doelgroepen** -gebruikersgroepen waarop het beleid wordt toegepast. Dezelfde groep moet worden gebruikt voor naleving en beleid voor voorwaardelijke toegang.  

-   **Uitgesloten groepen** -gebruikersgroepen die uitgesloten van het beleid (optioneel zijn).  
    Als een gebruiker zich in beide, zijn deze uitgesloten van het beleid.  

     Alleen de doelgroepen van het beleid voor voorwaardelijke toegang worden geëvalueerd.  

### <a name="step-3-create-a-conditional-access-policy-for-exchange-online-and-sharepoint-online"></a>Stap 3. Maak een beleid voor voorwaardelijke toegang tot Exchange Online en SharePoint Online.  

1.  Klik op **Activa en naleving** op de Configuration Manager-console.  

2.  Selecteer **Beleid voor voorwaardelijke toegang inschakelen voor Exchange Online**als u een beleid voor Exchange Online wilt maken.  

     Selecteer **Beleid voor voorwaardelijke toegang inschakelen voor Exchange Online**als u een beleid voor SharePoint Online wilt maken.  

3.  Ga naar het tabblad **Start** en klik in de groep **Koppelingen** op **Voorwaardelijk toegangsbeleid configureren in de Intune-console**. Mogelijk moet u de gebruikersnaam en het wachtwoord opgeven van het account dat wordt gebruikt om Configuration Manager verbinding te laten maken met Intune.  

     De Intune-beheerconsole wordt geopend.  

4.  Voor Exchange Online in de Microsoft Intune-beheerconsole, klikt u op **beleid > voorwaardelijke toegang > Exchange Online-beleid**.  

     SharePoint Online in de Microsoft Intune-beheerconsole, klikt u op **beleid > voorwaardelijke toegang > SharePoint Online-beleid**.  

5.  Stel de vereiste voor Windows-pc’s in op de optie**Apparaten moeten voldoen aan dit beleid**.  

6.  Onder **doelgroepen**, klikt u op **wijzigen** selecteren van de Azure Active Directory-beveiligingsgroepen waarop het beleid van toepassing is.  

    > [!NOTE]  
    >  De dezelfde beveiligingsgroep van de gebruiker moet worden gebruikt voor het implementeren van compliancy beleid en de doelgroep voor beleid voor voorwaardelijke toegang.  

     Klik desgewenst onder **Uitgesloten groepen**op **Wijzigen** om de Active Directory-beveiligingsgroepen te selecteren waarop dit beleid niet van toepassing is.  

7.  Klik op **Opslaan** om het beleid te maken en op te slaan  

Gebruikers wordt compatibiliteitsinformatie weergeven in Software Center. Als vanwege beleidsschending geblokkeerd, start u een nieuwe beleidsevaluatie na het oplossen van problemen met naleving van.  


## <a name="see-also"></a>Zie tevens

- [Beveiligen van gegevens en site-infrastructuur met System Center Configuration Manager](../../protect/understand/protect-data-and-site-infrastructure.md)
- [Voorwaardelijke toegang oplossen flow-chart voor Configuration Manager](https://gallery.technet.microsoft.com/Conditional-access-fd747c1a?redir=0)
