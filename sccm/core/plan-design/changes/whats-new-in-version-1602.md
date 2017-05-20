---
title: Nieuw in System Center Configuration Manager versie 1602 | Microsoft-documenten
description: "Meer informatie over deze wijzigingen en nieuwe functies die zijn geïntroduceerd in versie 1602 van System Center Configuration Manager."
ms.custom: na
ms.date: 12/30/2016
ms.reviewer: na
ms.suite: na
ms.prod: configuration-manager
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 4021eca1-adfb-4e5a-adee-159263c29637
caps.latest.revision: 3
author: Brenduns
ms.author: brenduns
manager: angrobe
robots: noindex,nofollow
ms.translationtype: Machine Translation
ms.sourcegitcommit: dab5da5a4b5dfb3606a8a6bd0c70a0b21923fff9
ms.openlocfilehash: 9a548f43625a907173e7b967d26356bd80f1c5d9
ms.contentlocale: nl-nl
ms.lasthandoff: 05/17/2017

---
# <a name="what39s-new-in-version-1602-of-system-center-configuration-manager"></a>Wat &#39; s is nieuw in versie 1602 van System Center Configuration Manager

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*


Update 1602 voor System Center Configuration Manager is alleen beschikbaar als een update in de console voor eerder geïnstalleerde sites waarop versie 1511. Versie 1511 is de eerste, basisversie die u gebruiken om nieuwe Configuration Manager-sites te installeren.  


> [!TIP]  
>  Meer informatie over:  
>   
>   -   [Installatie van nieuwe sites](/sccm/core/servers/deploy/install) (met behulp van een basislijn versie zoals 1511)  
>   -   [Installatie van updates op sites](/sccm/core/servers/manage/updates) (zoals 1602 update)  

 De volgende secties bevatten informatie over wijzigingen en nieuwe mogelijkheden die is geïntroduceerd in versie 1602 van Configuration Manager.  

## <a name="site-infrastructure"></a>Site-infrastructuur  

###  <a name="bkmk_UpgradeOS"></a>In-place upgrade het besturingssysteem van de siteservers waarop Windows Server 2008 R2 wordt uitgevoerd  
 Configuration Manager-sites waarop versie 1602 of hoger wordt uitgevoerd, ondersteunen de in-place upgrade van de site servers besturingssysteem van Windows Server 2008 R2 naar Windows Server 2012 R2.  

> [!WARNING]  
>  Voordat u naar Windows Server 2012 R2 bijwerkt, moet u WSUS 3.2 verwijderen van de server.  
>   
>  Voor informatie over deze kritieke stap, Zie de sectie "Nieuwe en gewijzigde functionaliteit" in [overzicht van Windows Server Update Services](https://technet.microsoft.com/library/hh852345.aspx), in de documentatie van Windows Server.  

 Gebruik de procedures van Windows Server 2012 R2-upgrade voor het bijwerken van een server. U hoeft niet uitvoeren van een Configuration Manager site server-herstel na de upgrade. Zie [Upgradeopties voor Windows Server 2012 R2](https://technet.microsoft.com/library/dn303416.aspx) in de Windows Server-documentatie voor de upgradeprocedures.  

###  <a name="bkmk_AOAG"></a>SQL Server AlwaysOn-beschikbaarheidsgroepen  
 SQL Server AlwaysOn-beschikbaarheidsgroepen gebruiken voor het hosten van de sitedatabase op primaire sites en de centrale beheersite als een oplossing voor hoge beschikbaarheid en herstel na noodgevallen.  

 Zie voor meer informatie, [SQL Server AlwaysOn van een maximaal beschikbare sitedatabase voor System Center Configuration Manager](../../../core/servers/deploy/configure/sql-server-alwayson-for-a-highly-available-site-database.md).  

## <a name="operating-system-deployment"></a>Implementatie van besturingssystemen  

### <a name="windows-10-servicing"></a>Onderhoud van Windows 10  
 De volgende verbeteringen voor het onderhoud van Windows 10 zijn in Configuration Manager versie 1602 toegevoegd:  

-   Nieuwe filteropties zijn beschikbaar voor onderhoudsplannen waarmee u kunt filteren op **taal**, **vereist**, en **titel**. Alleen de upgrades die voldoen aan de opgegeven criteria worden aan de gekoppelde implementatie toegevoegd.  

-   Wanneer u selecteert de **Upgrades** synchronisatie classificatie voor software-updates, wordt een waarschuwing weergegeven. Deze waarschuwing jou laten weten dat [hotfix 3095113](https://support.microsoft.com/kb/3095113) voor Windows Server Update Services (WSUS) 4.0 is vereist voordat u software-updates met succes kunt synchroniseren, en voor Windows 10 onderhoud goed te laten werken. Van de waarschuwing weergegeven gaat u naar de bijbehorende knowledge base-artikel.  

-   Beschikbare Windows 10 werkt nu alleen worden weergegeven in de **Windows 10 onderhoud** \ **alle Windows 10-Updates** knooppunt van de Configuration Manager-console. Deze updates niet meer weergegeven de **Software-Updates** \ **alle Software-Updates** knooppunt van de console.  

-   Een servicing plan wordt beschouwd als een implementatie met een hoog risico en de **verzameling selecteren** venster geeft alleen de aangepaste verzamelingen die voldoen aan de implementatie verificatie-instellingen die zijn geconfigureerd in de site eigenschappen. Zie [Instellingen voor het beheren van implementaties met een hoog risico voor System Center Configuration Manager](../../../protect/understand/settings-to-manage-high-risk-deployments.md) voor meer informatie.  

-   Gebruikers die een Upgrade van Windows 10 pakket nu starten bericht een dat ze hun besturingssysteem wordt bijgewerkt.  

## <a name="application-management"></a>Toepassingsbeheer  

### <a name="ios-app-configuration-policies"></a>Configuratiebeleidsregels voor IOS-apps  
 Beleidsregels van Configuration Manager-app-configuratie gebruiken voor het opgeven van instellingen die vereist zijn kunnen wanneer de gebruiker een iOS-app wordt uitgevoerd. Zo kan een app moet de gebruiker om op te geven van een aangepast poortnummer, de taal, beveiligingsinstellingen en huisstijl-instellingen (zoals een bedrijfslogo). Als deze instellingen zijn niet juist ingevoerd, kan dit vergroot de belasting van uw helpdesk en ook vertragingen in de ingebruikname van nieuwe apps.  

 Beleidsregels voor App-configuratie kunt u deze problemen elimineren doordat u deze instellingen implementeren voor gebruikers in een beleid voordat ze de app worden uitgevoerd. De instellingen worden vervolgens automatisch geleverd en de gebruiker niet hoeft geen actie te ondernemen. Zie voor meer informatie, [iOS-apps met app-configuratiebeleid in System Center Configuration Manager configureren](../../../apps/deploy-use/configure-ios-apps-with-app-configuration-policies.md).  

### <a name="manage-volume-purchased-ios-apps"></a>iOS-apps beheren die zijn gekocht via het volume-aankoopprogramma  
 Configuration Manager kunt u implementeren en beheren van apps die u hebt aangeschaft in volume uit de Apple Volume aankoop programma (VPP). Configuration Manager de licentiegegevens geïmporteerd uit de appstore en houdt hoeveel van de licenties die u hebt gebruikt.  

 Zie voor meer informatie, [volume aangeschaft iOS-apps met System Center Configuration Manager beheren](../../../apps/deploy-use/manage-volume-purchased-ios-apps.md).  

### <a name="automatic-creation-of-office-mobile-apps"></a>Automatische aanmaak van mobiele Office-apps  
 Wanneer u naar versie 1602 van 1511 bijwerkt, maakt Configuration Manager automatisch de volgende Microsoft Office mobiele apps voor Android en iOS:  

-   Microsoft Word  

-   Microsoft Excel  

-   Microsoft PowerPoint  

-   Microsoft OneDrive  

-   Microsoft OneNote (alleen iOS)  

-   Microsoft Outlook  

U vindt deze apps in de **toepassingen** knooppunt van de Configuration Manager-console.  

 Zie voor meer informatie over het implementeren van toepassingen [het implementeren van toepassingen met System Center Configuration Manager](../../../apps/deploy-use/deploy-applications.md).  

## <a name="software-updates"></a>Software-updates  

### <a name="manage-office-365-client-updates"></a>Updates voor Office 365-clients beheren  
 System Center Configuration Manager heeft de mogelijkheid voor het beheren van updates voor Office 365-clients met behulp van de werkstroom software-update. Zie voor meer informatie [Office 365 ProPlus beheren met System Center Configuration Manager-updates](/sccm/sum/deploy-use/manage-office-365-proplus-updates).  

## <a name="compliance-settings"></a>Instellingen voor naleving  

### <a name="compliance-settings-for-devices-running-windows-10-team"></a>Compatibiliteitsinstellingen voor apparaten met Windows 10 Team  
 Nieuwe instellingen zijn toegevoegd aan de **Windows 8.1 en Windows 10** configuratie-item. Deze instellingen kunt u met Windows 10 Team, zoals een apparaat oppervlak Hub-apparaten worden beheerd.  

 Zie voor meer informatie, [het maken van configuratie-items voor Windows 8.1 en Windows 10-apparaten beheerd zonder dat de System Center Configuration Manager-client](../../../compliance/deploy-use/create-configuration-items-for-windows-8.1-and-windows-10-devices-managed-without-the-client.md).  

### <a name="kiosk-mode-settings-for-android-samsung-knox-standard-devices"></a>Instellingen voor kioskmodus voor Android Samsung KNOX Standard-apparaten  
 Kioskmodus kunt u een apparaat vergrendelen zodat alleen bepaalde functies werken. Bijvoorbeeld, kunt u een apparaat slechts één beheerde app die u opgeeft, of u kunt de volumeknoppen op een apparaat uitschakelen. Deze instellingen kunnen worden gebruikt voor een demonstratiemodel van een apparaat of een apparaat dat is toegewezen aan slechts één functie, zoals een verkooppunt apparaat. In Configuration Manager, kunt u nu instellingen voor kioskmodus voor Samsung KNOX Standard-apparaten opgeven.  

 Zie voor meer informatie, [het maken van configuratie-items voor Android en Samsung KNOX Standard-apparaten beheerd zonder dat de System Center Configuration Manager-client](../../../compliance/deploy-use/create-configuration-items-for-android-and-samsung-knox-devices-managed-without-the-client.md).  

## <a name="conditional-access"></a>Voorwaardelijke toegang  

### <a name="conditional-access-for-pcs-managed-by-system-center-configuration-manager"></a>Voorwaardelijke toegang voor pc's die worden beheerd door System Center Configuration Manager  
 Voor deze release voor voorwaardelijke toegang instellen voor een PC, de PC dat opnieuw moest worden ingeschreven in Intune of dat opnieuw moest worden van een domein-PC. Beginnen met de update 1602, wordt voorwaardelijke toegang voor pc's die worden beheerd door System Center Configuration manager ondersteund. Voor uw pc's die worden beheerd door System Center Configuration Manager, kunt u alleen naar apparaten die compatibel zijn met het nalevingsbeleid dat u toegang tot Exchange Online en SharePoint Online beperken.  

 Zie voor meer informatie, [toegang tot services O365 voor pc's die worden beheerd door System Center Configuration Manager beheren](../../../protect/deploy-use/manage-access-to-o365-services-for-pcs-managed-by-sccm.md).  

### <a name="restricting-access-based-on-the-health-of-devices"></a>Beperken van toegang op basis van de status van apparaten  
 U kunt nu toegang tot e-mail en 0ffice 365-services op basis van de status van de apparaten beperken, zoals gemeld door de Attestation-statusservice. Daarnaast worden apparaten die worden beheerd door Intune opgenomen in de rapporten van de status van apparaat.  

 De Configuration Manager-console biedt een nieuwe regel voor naleving die u opgeven kunt als de apparaten moeten worden toegestaan of geblokkeerd op basis van hun gezondheidsstatus toegang. Zie voor meer informatie over Health Attestation-Service en hoe de status van apparaten in Intune wordt gerapporteerd, [Health-verklaring voor System Center Configuration Manager](../../../core/servers/manage/health-attestation.md).  

### <a name="new-compliance-policy-rules"></a>Nieuwe beleidsregels voor naleving  
 Nieuwe beleidsregels van naleving, zoals automatische updates en een wachtwoord voor het ontgrendelen van apparaten, zijn toegevoegd aan de vereisten voor betere beveiliging ondersteunen.

 Zie voor meer informatie [nalevingsbeleid voor apparaten in System Center Configuration Manager](../../../protect/deploy-use/device-compliance-policies.md).  

### <a name="make-sure-enrolled-and-compliant-devices-always-have-access-to-exchange-on-premises"></a>Zorg ervoor dat de apparaten geregistreerd en voldoen altijd toegang tot Exchange on-premises hebben  
 Wanneer u de volgende opties inschakelt, worden apparaten die zijn ingeschreven in Intune, en voldoen aan het nalevingsbeleid voor toegang tot Exchange on-premises toegestaan: **Regel overschrijven standaard - altijd toestaan Intune geregistreerd en compatibele apparaten voor toegang tot Exchange lokale:**. Deze regel is beschikbaar op de **pagina Algemeen** van de **configureren voorwaardelijke toegang Wizard beleid voor** voor Exchange on-premises.

 Deze regel overschrijft de standaardregel, wat dat betekent zelfs als u de standaardregel op quarantaine of blok toegang instellen, geregistreerd en compatibele apparaten nog steeds toegang tot Exchange worden on-premises. Gebruik deze instelling als u wilt ingeschreven en compatibele apparaten altijd toegang tot e-mail via Exchange lokale hebben.   

 Zie voor de gedetailleerd overzicht [toegang tot e-mail beheren in System Center Configuration Manager](../../../protect/deploy-use/manage-email-access.md).  

## <a name="client-management"></a>Clientbeheer  

### <a name="client-online-status"></a>Onlinestatus van clients  
 Een nieuwe status voor clients is beschikbaar voor bewaking, indien een computer online is. Een computer wordt beschouwd als online als deze verbonden met het bijbehorende toegewezen beheerpunt. Om aan te geven dat de computer online is, verzendt de client ping-achtige berichten naar het beheerpunt. Als het beheerpunt een na 5 minuten bericht heeft niet, wordt de client offline beschouwd.  

 Zie voor meer informatie, [in System Center Configuration Manager clients bewaken](../../../core/clients/manage/monitor-clients.md).  

### <a name="refresh-pc-machine-and-user-policy-from-software-center"></a>PC-computer en de gebruiker beleid vanuit Software Center vernieuwen  
 Een nieuwe optie **Sync beleid**, is toegevoegd aan de **opties** > **Computeronderhoud** pagina van het Software Center die ervoor zorgt dat de PC te vernieuwen van de Configuration Manager voor computer- en beleid.  

### <a name="software-center-branding-changes"></a>Software Center huisstijl wijzigingen  
 U kunt de kleur, organisatienaam en pictogram die worden weergegeven in Software Center wijzigen. Deze instellingen worden toegepast volgens de volgende regels:  

- Als de Application Catalog-website-puntrol siteserver is niet geïnstalleerd en Software Center wordt vervolgens de organisatienaam die is opgegeven in de **Computeragent** client instelling **weergegeven organisatienaam in Software Center**.  

- Als de Application Catalog-website-puntrol siteserver is geïnstalleerd, geeft Software Center de naam van de organisatie en de kleur die is opgegeven in de eigenschappen van Application Catalog-website-punt siteserverrol.  

- Als een Microsoft Intune-abonnement is geconfigureerd en met de Configuration Manager-omgeving verbonden, geeft Software Center de naam van de organisatie, kleur en bedrijfslogo opgegeven in de eigenschappen van de Intune-abonnement.  

### <a name="health-attestation"></a>Health-verklaring  
 Beheerders kunnen de status van Windows 10 apparaat Health Attestation weergeven in de Configuration Manager-console. Dit is beschikbaar voor Configuration Manager, evenals de Configuration Manager met Microsoft Intune. Met Health Attestation van apparaten kan de beheerder ervoor zorgen dat clientcomputers over de volgende betrouwbare configuraties van BIOS, TPM en opstartsoftware beschikken:  

-   Vroege starten antimalware  

-   BitLocker  

-   Beveiligd opstarten  

-   Code-Integriteitsbeleidsbestand  

Zie voor meer informatie, [Health-verklaring voor System Center Configuration Manager](../../../core/servers/manage/health-attestation.md).  

### <a name="improvements-to-endpoint-protection-antimalware-settings"></a>Verbeteringen in de instellingen van Endpoint Protection schadelijke software  
 1602 voegt de volgende nieuwe instellingen in het antimalwarebeleid Endpoint Protection voor Windows Defender toe:  

-   Realtime-beveiliging: Blokkeren mogelijk ongewenste toepassingen te downloaden voor installatie.  

-   Instellingen voor scanschema: Toegewezen netwerkstations scannen tijdens een volledige scan.  

-   Instellingen voor automatische verzending bestand verzenden:  

     De antimalware-engine kan verzoeken voorbeeldbestanden voor verdere analyse naar Microsoft worden verzonden. Standaard wordt altijd om bevestiging gevraagd voordat dergelijke voorbeeldbestanden worden verzonden. Beheerders kunnen nu de volgende instellingen beheren om dit gedrag te configureren:  

    -   Geavanceerde: Schakel automatisch verzenden van voorbeeldbestanden kan Microsoft bepalen of bepaalde gedetecteerde items kwaadaardig zijn.  

    -   Geavanceerde: Toestaan dat gebruikers om automatische verzending bestand verzenden instellingen te wijzigen.  

    Bovendien, in de sectie "Uitsluitingsinstellingen" van antimalwarebeleid endpoint protection, de bestaande **bestanden en mappen uitsluiten** apparaat uitsluitingen instelling nu toestaat.  

Zie voor meer informatie, [maken en implementeren van antimalware-beleidsregels voor Endpoint Protection in System Center Configuration Manager](../../../protect/deploy-use/endpoint-antimalware-policies.md).  

## <a name="mobile-device-management"></a>Beheer van mobiele apparaten  

### <a name="ios-activation-lock"></a>iOS Activeringsvergrendeling  
 Configuration Manager kunt u iOS Activeringsvergrendeling, een functie van de Zoek mijn iPhone-app voor iOS 7.1 en hoger apparaten beheren. Activeringsvergrendeling is automatisch ingeschakeld wanneer de app Zoek mijn iPhone op een apparaat wordt gebruikt. Nadat de vergrendeling is ingeschakeld, moeten de Apple ID en het wachtwoord van de gebruiker worden ingevoerd voordat een van de volgende handelingen kan worden verricht:  

-   Schakel uit Zoek mijn iPhone.  

-   Het apparaat wissen.  

-   Activeer het apparaat.  

Configuration Manager kunnen de status van de Activeringsvergrendeling van supervisie en werkende apparaten met iOS 7.1 en hoger aanvragen. Voor de bewaakte apparaten Configuration Manager ophalen van de Activeringsvergrendeling bypass-code en rechtstreeks verlenen aan het apparaat.  

 Zie voor meer informatie, [bescherming van iOS-apparaten met Activeringsvergrendeling in System Center Configuration Manager omzeilen](/sccm/mdm/deploy-use/manage-ios-activation-lock).  

### <a name="monitor-terms-and-conditions-deployments"></a>Voorwaarden en bepalingen implementaties bewaken  
 U kunt voorwaarden en bepalingen implementaties in de Configuration Manager-console bewaken.  

 Selecteer de implementatie van de voorwaarden en bepalingen in de lijst van implementaties. Het gedeelte overzicht ziet u de volgende statistische gegevens:  

-   **Compatibel**: Gebruikers hebben de nieuwste versie van de voorwaarden geaccepteerd.  

-   **Fout**  

-   **Niet-compatibele**: Gebruikers hebben een versie van de voorwaarden en bepalingen, maar niet de meest recente versie hebben geaccepteerd.  

-   **Onbekende**: Gebruikers hebben nooit de voorwaarden en bepalingen, inclusief verbindingen zonder een geregistreerde apparaat geaccepteerd.  

