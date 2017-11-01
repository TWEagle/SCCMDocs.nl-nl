---
title: Nieuw in versie 1602
titleSuffix: Configuraton Manager
description: "Meer informatie over deze wijzigingen en nieuwe mogelijkheden die zijn geïntroduceerd in versie 1602 van System Center Configuration Manager."
ms.custom: na
ms.date: 12/30/2016
ms.reviewer: na
ms.suite: na
ms.prod: configuration-manager
ms.technology: configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 4021eca1-adfb-4e5a-adee-159263c29637
caps.latest.revision: "3"
author: Brenduns
ms.author: brenduns
manager: angrobe
robots: noindex,nofollow
ms.openlocfilehash: 0e151b01d3399dafc6ed3962560e8e9975a37a8e
ms.sourcegitcommit: c236214b2fcc13dae7bad96d7fb33f692868191d
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/12/2017
---
# <a name="what39s-new-in-version-1602-of-system-center-configuration-manager"></a>Wat &#39; s is nieuw in versie 1602 van System Center Configuration Manager

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*


Update 1602 voor System Center Configuration Manager is alleen beschikbaar als een update in de console voor eerder geïnstalleerde sites waarop versie 1511 uitgevoerd. Versie 1511 is de eerste, basislijnversie die u gebruikt om nieuwe Configuration Manager-sites te installeren.  


> [!TIP]  
>  Meer informatie over:  
>   
>   -   [Nieuwe sites installeren](/sccm/core/servers/deploy/install) (met behulp van een basislijnversie zoals 1511)  
>   -   [Updates installeren op sites](/sccm/core/servers/manage/updates) (zoals update 1602)  

 De volgende secties bevatten informatie over wijzigingen en nieuwe mogelijkheden die zijn geïntroduceerd in versie 1602 van Configuration Manager.  

## <a name="site-infrastructure"></a>Site-infrastructuur  

###  <a name="bkmk_UpgradeOS"></a>In-place upgrade van het besturingssysteem van siteservers waarop Windows Server 2008 R2 wordt uitgevoerd  
 Configuration Manager-sites waarop versie 1602 of hoger wordt uitgevoerd, ondersteunen de in-place upgrade van de site servers besturingssysteem van Windows Server 2008 R2 naar Windows Server 2012 R2.  

> [!WARNING]  
>  Voordat u een naar Windows Server 2012 R2 upgrade, moet u WSUS 3.2 verwijderen van de server.  
>   
>  Voor informatie over deze kritieke stap, Zie de sectie 'New and changed functionality' in [overzicht van Windows Server Update Services](https://technet.microsoft.com/library/hh852345.aspx), in de documentatie van Windows Server.  

 Gebruik de upgradeprocedures van Windows Server 2012 R2 voor het bijwerken van een server. U hoeft niet uitvoeren voor een Configuration Manager site server herstellen na de upgrade. Zie [Upgradeopties voor Windows Server 2012 R2](https://technet.microsoft.com/library/dn303416.aspx) in de Windows Server-documentatie voor de upgradeprocedures.  

###  <a name="bkmk_AOAG"></a>SQL Server AlwaysOn-beschikbaarheidsgroepen  
 SQL Server AlwaysOn-beschikbaarheidsgroepen gebruiken als host van de sitedatabase op primaire sites en de centrale beheersite als oplossing voor hoge beschikbaarheid en herstel na noodgevallen.  

 Zie voor meer informatie [SQL Server AlwaysOn voor een maximaal beschikbare sitedatabase voor System Center Configuration Manager](../../../core/servers/deploy/configure/sql-server-alwayson-for-a-highly-available-site-database.md).  

## <a name="operating-system-deployment"></a>Implementatie van besturingssystemen  

### <a name="windows-10-servicing"></a>Onderhoud van Windows 10  
 De volgende verbeteringen voor onderhoud van Windows 10 zijn toegevoegd in versie 1602 van Configuration Manager:  

-   Er zijn nieuwe filteropties beschikbaar voor onderhoudsplannen waarmee u kunt filteren op **taal**, **vereist**, en **titel**. Alleen de upgrades die voldoen aan de opgegeven criteria worden aan de gekoppelde implementatie toegevoegd.  

-   Wanneer u selecteert de **Upgrades** synchronisatie van classificatie voor software-updates, wordt er een waarschuwing weergegeven. Deze waarschuwing laat u weten dat [hotfix 3095113](https://support.microsoft.com/kb/3095113) voor Windows Server Update Services (WSUS) 4.0 is vereist voordat u software-updates met succes kunt synchroniseren, en voor het onderhoud van Windows 10 goed te laten werken. Van het waarschuwingsbericht staan aangegeven, kunt u naar de bijbehorende knowledge base-artikel gaan.  

-   Beschikbare Windows upgrades 10 worden nu alleen weergegeven in de **onderhoud van Windows 10** \ **alle Windows 10-Updates** knooppunt van de Configuration Manager-console. Deze updates worden niet meer weergegeven de **Software-Updates** \ **alle Software-Updates** knooppunt van de console.  

-   Een onderhoudsplan wordt beschouwd als een implementatie met hoog risico en de **verzameling selecteren** venster geeft alleen de aangepaste verzamelingen die voldoen aan de implementatie van de verificatie-instellingen die zijn geconfigureerd in de site eigenschappen. Zie [Instellingen voor het beheren van implementaties met een hoog risico voor System Center Configuration Manager](../../../protect/understand/settings-to-manage-high-risk-deployments.md) voor meer informatie.  

-   Gebruikers die een Windows 10-upgradepakket nu starten ontvangen een bericht dat ze hun besturingssysteem wordt bijgewerkt.  

## <a name="application-management"></a>Toepassingsbeheer  

### <a name="ios-app-configuration-policies"></a>Configuratiebeleidsregels voor IOS-apps  
 Configuration Manager-app-configuratiebeleid gebruiken voor het opgeven van instellingen die mogelijk vereist zijn wanneer de gebruiker een iOS-app uitvoert. Een app kan bijvoorbeeld vereisen dat de gebruiker om op te geven van een aangepast poortnummer, de taal, beveiligingsinstellingen en huisstijlinstellingen (zoals een bedrijfslogo). Als deze instellingen niet correct worden ingevoerd, kan dit de werkbelasting van uw helpdesk verhogen en ook de acceptatie van nieuwe apps vertragen.  

 Configuratiebeleid voor apps kunt u deze problemen voorkomen doordat u kunt deze instellingen implementeren voor gebruikers in een beleid voordat ze de app worden uitgevoerd. De instellingen worden vervolgens automatisch aangeleverd, en de gebruiker niet hoeft geen actie te ondernemen. Zie voor meer informatie [iOS-apps configureren met configuratiebeleid voor apps in System Center Configuration Manager](../../../apps/deploy-use/configure-ios-apps-with-app-configuration-policies.md).  

### <a name="manage-volume-purchased-ios-apps"></a>iOS-apps beheren die zijn gekocht via het volume-aankoopprogramma  
 Configuration Manager kunt u apps die u hebt aangeschaft via het Apple Volume Purchase Program (VPP) implementeren en beheren. Configuration Manager importeert de licentiegegevens uit de appstore en bijgehouden hoeveel licenties u hebt gebruikt.  

 Zie voor meer informatie [volume-purchased iOS-apps met System Center Configuration Manager beheren](../../../apps/deploy-use/manage-volume-purchased-ios-apps.md).  

### <a name="automatic-creation-of-office-mobile-apps"></a>Automatische aanmaak van mobiele Office-apps  
 Wanneer u naar versie 1602 vanaf 1511 bijwerkt, maakt Configuration Manager automatisch de volgende mobiele Microsoft Office-apps voor Android en iOS:  

-   Microsoft Word  

-   Microsoft Excel  

-   Microsoft PowerPoint  

-   Microsoft OneDrive  

-   Microsoft OneNote (alleen iOS)  

-   Microsoft Outlook  

U vindt deze apps in de **toepassingen** knooppunt van de Configuration Manager-console.  

 Zie voor meer informatie over het implementeren van toepassingen [toepassingen met System Center Configuration Manager implementeren](../../../apps/deploy-use/deploy-applications.md).  

## <a name="software-updates"></a>Software-updates  

### <a name="manage-office-365-client-updates"></a>Updates voor Office 365-clients beheren  
 System Center Configuration Manager heeft de mogelijkheid voor het beheren van updates voor Office 365-clients met behulp van de werkstroom voor software-update. Zie voor meer informatie [Office 365 ProPlus beheren met System Center Configuration Manager-updates](/sccm/sum/deploy-use/manage-office-365-proplus-updates).  

## <a name="compliance-settings"></a>Instellingen voor naleving  

### <a name="compliance-settings-for-devices-running-windows-10-team"></a>Instellingen voor naleving voor apparaten met Windows 10 Team  
 Nieuwe instellingen zijn toegevoegd aan de **Windows 8.1 en Windows 10** configuratie-item. Deze instellingen helpen u apparaten met Windows 10 Team, zoals Surface Hub-apparaten worden beheerd.  

 Zie voor meer informatie [het maken van configuratie-items voor Windows 8.1 en Windows 10-apparaten worden beheerd zonder de System Center Configuration Manager-client](../../../compliance/deploy-use/create-configuration-items-for-windows-8.1-and-windows-10-devices-managed-without-the-client.md).  

### <a name="kiosk-mode-settings-for-android-samsung-knox-standard-devices"></a>Instellingen voor kioskmodus voor Android Samsung KNOX Standard-apparaten  
 Kioskmodus kunt u een apparaat vergrendelen zodat alleen bepaalde functies werken. Bijvoorbeeld, kunt u een apparaat slechts één beheerde app die u opgeeft uitvoert of u kunt de volumeknoppen op een apparaat uitschakelen. Deze instellingen kunnen worden gebruikt voor een demonstratiemodel van een apparaat of een apparaat dat is toegewezen aan slechts één functie, zoals een verkooppuntapparaat. In Configuration Manager kunt u nu instellingen voor kioskmodus voor Samsung KNOX Standard-apparaten opgeven.  

 Zie voor meer informatie [het maken van configuratie-items voor Android en Samsung KNOX Standard-apparaten worden beheerd zonder de System Center Configuration Manager-client](../../../compliance/deploy-use/create-configuration-items-for-android-and-samsung-knox-devices-managed-without-the-client.md).  

## <a name="conditional-access"></a>Voorwaardelijke toegang  

### <a name="conditional-access-for-pcs-managed-by-system-center-configuration-manager"></a>Voorwaardelijke toegang voor pc's die worden beheerd door System Center Configuration Manager  
 Voor deze release voor voorwaardelijke toegang instellen voor een PC, de PC ofwel om te worden ingeschreven in Intune of had om te worden van een domein-PC. Vanaf update 1602 kunt wordt voorwaardelijke toegang voor pc's die worden beheerd door System Center Configuration manager ondersteund. Voor de pc's die worden beheerd door System Center Configuration Manager, kunt u toegang tot Exchange Online en SharePoint Online beperken tot apparaten die compatibel zijn met het nalevingsbeleid dat u instelt.  

 Zie voor meer informatie [toegang beheren tot O365-services voor pc's die worden beheerd door System Center Configuration Manager](../../../protect/deploy-use/manage-access-to-o365-services-for-pcs-managed-by-sccm.md).  

### <a name="restricting-access-based-on-the-health-of-devices"></a>Beperken van toegang op basis van de status van apparaten  
 U kunt nu toegang beperken tot e-mail en 0ffice 365-services op basis van de status van apparaten, zoals gemeld door de Health Attestation-Service. Daarnaast worden apparaten die worden beheerd door Intune opgenomen in de statusrapporten over apparaten.  

 De Configuration Manager-console biedt een nieuwe regel voor naleving die u opgeven kunt of de apparaten moeten worden toegestaan of geblokkeerd toegang op basis van hun gezondheidsstatus. Zie voor meer informatie over Health Attestation-Service en hoe de status van apparaten in Intune wordt gerapporteerd [Health attestation voor System Center Configuration Manager](../../../core/servers/manage/health-attestation.md).  

### <a name="new-compliance-policy-rules"></a>Nieuwe beleidsregels voor naleving  
 Nieuwe beleidsregels voor naleving, zoals automatische updates en een wachtwoord vereisen voor het ontgrendelen van apparaten, zijn toegevoegd ter ondersteuning van striktere beveiligingsvereisten.

 Zie voor meer informatie [nalevingsbeleid voor apparaten in System Center Configuration Manager](../../../protect/deploy-use/device-compliance-policies.md).  

### <a name="make-sure-enrolled-and-compliant-devices-always-have-access-to-exchange-on-premises"></a>Zorg ervoor dat ingeschreven en compatibele apparaten altijd toegang tot Exchange on-premises hebben  
 Als u de volgende optie inschakelt, mogen apparaten die zijn ingeschreven in Intune en voldoen aan het nalevingsbeleid toegang tot Exchange on-premises: **Standaardregel negeren - altijd toestaan geregistreerd bij Intune en compatibele apparaten toegang tot Exchange lokale:**. Deze regel is beschikbaar op de **pagina Algemeen** van de **Wizard voorwaardelijke toegang configureren beleid** voor Exchange on-premises.

 Deze regel wordt de standaardregel, wat dat betekent zelfs als u de standaardregel ingesteld op quarantaine of de toegang blokkeert, ingeschreven en compatibele apparaten nog steeds toegang tot Exchange worden on-premises genegeerd. Gebruik deze instelling als u wilt dat ingeschreven en compatibele apparaten altijd toegang hebben tot e-mail via Exchange on-premises.   

 Zie voor de gedetailleerde walktrough [toegang tot e-mail beheren in System Center Configuration Manager](../../../protect/deploy-use/manage-email-access.md).  

## <a name="client-management"></a>Clientbeheer  

### <a name="client-online-status"></a>Onlinestatus van clients  
 Een nieuwe status voor clients is beschikbaar voor bewaking als een computer online is. Een computer wordt beschouwd als online als deze verbonden met de bijbehorende toegewezen beheerpunt. Om aan te geven dat de computer online is, verzendt de client ping-achtige berichten naar het beheerpunt. Als het beheerpunt een bericht na 5 minuten ontvangen heeft, wordt de client als offline beschouwd.  

 Zie voor meer informatie [clients in System Center Configuration Manager controleren](../../../core/clients/manage/monitor-clients.md).  

### <a name="refresh-pc-machine-and-user-policy-from-software-center"></a>PC-computer en de gebruiker beleid vanuit Software Center vernieuwen  
 Een nieuwe optie **Synchronisatiebeleid**, is toegevoegd aan de **opties** > **Computeronderhoud** pagina van het Software Center zorgt ervoor dat de PC vernieuwen van de Configuration Manager voor computer- en beleid.  

### <a name="software-center-branding-changes"></a>Huisstijlwijzigingen voor software Center  
 U kunt de kleur, de naam van de organisatie en het pictogram die worden weergegeven in Software Center wijzigen. Deze instellingen worden toegepast volgens de volgende regels:  

- Als de siteserverrol van Application Catalog-website-punt is niet geïnstalleerd, wordt de Software Center de organisatienaam die is opgegeven bevat in de **Computeragent** clientinstelling aangeroepen **weergegeven organisatienaam in Software Center**.  

- Als de siteserverrol van Application Catalog-website-punt is geïnstalleerd, worden Software Center de naam van de organisatie en de kleur die is opgegeven in de eigenschappen van de siteserverrol van Application Catalog-website-punt.  

- Als een Microsoft Intune-abonnement is geconfigureerd en is verbonden met de Configuration Manager-omgeving, geeft Software Center de naam van de organisatie, kleur en bedrijfslogo opgegeven in de eigenschappen van de Intune-abonnement.  

### <a name="health-attestation"></a>Health Attestation  
 Beheerders kunnen de status van Windows 10 Apparaatstatusverklaring bekijken in de Configuration Manager-console. Dit is beschikbaar voor Configuration Manager, evenals de Configuration Manager met Microsoft Intune. Met Health Attestation van apparaten kan de beheerder ervoor zorgen dat clientcomputers over de volgende betrouwbare configuraties van BIOS, TPM en opstartsoftware beschikken:  

-   Early launch antimalware  

-   BitLocker  

-   Beveiligd opstarten  

-   Code-integriteit  

Zie voor meer informatie [Health attestation voor System Center Configuration Manager](../../../core/servers/manage/health-attestation.md).  

### <a name="improvements-to-endpoint-protection-antimalware-settings"></a>Verbeteringen in Endpoint Protection antimalware-instellingen  
 1602 wordt de volgende nieuwe instellingen in het antimalwarebeleid van Endpoint Protection voor Windows Defender toegevoegd:  

-   Realtime-beveiliging: Potentieel ongewenste toepassingen tijdens downloaden voorafgaand aan installatie geblokkeerd.  

-   Scaninstellingen: Toegewezen netwerkstations scannen tijdens een volledige scan.  

-   Automatische instellingen verzenden van voorbeeldbestanden:  

     De antimalware-engine aanvragen dat voorbeeldbestanden voor verdere analyse naar Microsoft worden verzonden. Standaard wordt altijd om bevestiging gevraagd voordat dergelijke voorbeeldbestanden worden verzonden. Beheerders kunnen nu de volgende instellingen beheren om dit gedrag te configureren:  

    -   Geavanceerd: Schakel automatisch verzenden van voorbeeldbestanden zodat Microsoft kan bepalen of bepaalde gedetecteerde items schadelijk zijn.  

    -   Geavanceerd: Toestaan dat gebruikers instellingen voor verzending van automatische voorbeeldbestanden wijzigen.  

    Bovendien, in de sectie 'Uitsluitingsinstellingen' van antimalwarebeleid endpoint protection, de bestaande **bestanden en mappen uitsluiten** instelling nu kan apparaten kunnen worden uitgesloten.  

Zie voor meer informatie [maken en implementeren van antimalwarebeleid voor Endpoint Protection in System Center Configuration Manager](../../../protect/deploy-use/endpoint-antimalware-policies.md).  

## <a name="mobile-device-management"></a>Beheer van mobiele apparaten  

### <a name="ios-activation-lock"></a>iOS-Activeringsvergrendeling  
 Configuration Manager kunt u iOS-Activeringsvergrendeling, een functie van de Zoek mijn iPhone-app voor iOS 7.1 en hoger apparaten beheren. Activeringsvergrendeling is automatisch ingeschakeld wanneer de app Zoek mijn iPhone op een apparaat wordt gebruikt. Nadat de vergrendeling is ingeschakeld, moeten de Apple ID en het wachtwoord van de gebruiker worden ingevoerd voordat een van de volgende handelingen kan worden verricht:  

-   Zoek mijn iPhone uitschakelen.  

-   Het apparaat wissen.  

-   Het apparaat opnieuw activeren.  

Configuration Manager kunnen aanvragen van de status van de Activeringsvergrendeling van apparaten voor zowel en zonder supervisie waarop iOS 7.1 en hoger wordt uitgevoerd. Voor apparaten onder supervisie kan Configuration Manager de bypass-code van de Activeringsvergrendeling ophalen en direct aan het apparaat worden uitgegeven.  

 Zie voor meer informatie [iOS-apparaten met Activeringsvergrendeling overslaan in System Center Configuration Manager-beschermen](/sccm/mdm/deploy-use/manage-ios-activation-lock).  

### <a name="monitor-terms-and-conditions-deployments"></a>Implementaties voor voorwaarden bewaken  
 U kunt voorwaarden en bepalingen implementaties controleren in de Configuration Manager-console.  

 Selecteer de implementatie voor voorwaarden in de lijst met implementaties. Het gedeelte overzicht ziet u de volgende statistische gegevens:  

-   **Compatibele**: Gebruikers hebben de nieuwste versie van de voorwaarden geaccepteerd.  

-   **Fout**  

-   **Niet-compatibele**: Gebruikers hebben geaccepteerd, een versie van de voorwaarden, maar niet de nieuwste versie.  

-   **Onbekende**: Gebruikers hebben nooit geaccepteerd voor de voorwaarden en bepalingen, inclusief gebruikers met een geregistreerd apparaat.  
