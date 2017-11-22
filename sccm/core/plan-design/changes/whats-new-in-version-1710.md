---
title: Nieuwe versie 1710 | Microsoft Docs
titleSuffix: Configuration Manager
description: "Meer informatie over deze wijzigingen en nieuwe mogelijkheden die zijn geïntroduceerd in versie 1710 van System Center Configuration Manager."
ms.custom: na
ms.date: 11/20/2017
ms.reviewer: na
ms.suite: na
ms.technology: configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: bc6c3e5f-b9e2-400e-9d9d-446ff93c520c
author: Brenduns
ms.author: brenduns
manager: angrobe
ms.openlocfilehash: 33a5bff1e202822ce3ec5755958d34af461957e9
ms.sourcegitcommit: 536f7295e9ea361f1f9ead6c25f3685deb041ad8
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 11/21/2017
---
# <a name="what39s-new-in-version-1710-of-system-center-configuration-manager"></a>Wat &#39; s is nieuw in versie 1710 van System Center Configuration Manager

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*

Update 1710 voor de huidige vertakking van System Center Configuration Manager is beschikbaar als een update in de console voor eerder geïnstalleerde sites waarop versie 1610, 1702 of 1706 wordt uitgevoerd.

> [!TIP]  
> Een nieuwe site te installeren, moet u een basislijnversie van Configuration Manager.  
>  Meer informatie over:    
>   - [Nieuwe sites installeren](https://technet.microsoft.com/library/mt590197.aspx)  
>   - [Updates installeren op sites](https://technet.microsoft.com/library/mt607046.aspx)  
>   - [Basislijn- en updateversies](/sccm/core/servers/manage/updates#a-namebkmkbaselinesa-baseline-and-update-versions)  

De volgende secties bevatten informatie over wijzigingen en nieuwe mogelijkheden die zijn geïntroduceerd in versie 1710 van Configuration Manager.  

<!--
## Deprecated features and operating systems
Learn about support changes before they are implemented in [removed and deprecated features](/sccm/core/plan-design/changes/removed-and-deprecated-features).

Version 1710 drops support for the following products:
-->


## <a name="site-infrastructure"></a>Site-infrastructuur

### <a name="updates-for-peer-cache-----sms500850---"></a>Updates voor Peer-Cache<!-- sms500850 -->
Vanaf deze release is is Peer-Cache niet langer een functie van de voorlopige versie.  Er zijn geen andere wijzigingen voor Peer-Cache zijn geïntroduceerd in deze release. Zie voor meer informatie [Peer-Cache voor Configuration Manager-clients](/sccm/core/plan-design/hierarchy/client-peer-cache).

### <a name="cloud-distribution-point-support-for-azure-government-cloud------sms491428---"></a>Cloud distribution point-ondersteuning voor Azure Government Cloud<!-- sms491428 -->
U kunt nu [cloud-gebaseerde distributiepunten](/sccm/core/plan-design/hierarchy/use-a-cloud-based-distribution-point) in de cloud Azure Government.   


<!-- ## Migration  -->


## <a name="client-management"></a>Clientbeheer

### <a name="co-management-for-windows-10-devices"></a>CO-beheer voor Windows 10-apparaten    
<!-- 1350871 -->
Beginnen met het Windows 10 versie 1607 (ook wel bekend als de verjaardag Update), u kunt deelnemen aan een Windows 10-apparaten met on-premises Active Directory (AD) en Azure AD cloud-gebaseerd op hetzelfde moment (hybride Azure AD). Mede management maakt gebruik van deze verbetering en kunt u gelijktijdig Windows 10-apparaten beheren met behulp van zowel Configuration Manager en Intune. Het is een oplossing waarmee een verbinding met traditionele naar moderne management biedt en u een pad voor de overgang met behulp van een gefaseerde benadering. Zie voor meer informatie [mede management voor Windows 10-apparaten](/sccm/core/clients/manage/co-management-overview).

### <a name="restart-computers-form-the-configuration-manager-console-----1356283---"></a>Opnieuw opstarten van computers uit de Configuration Manager-console<!-- 1356283 -->
Vanaf deze release kunt kunt u de Configuration Manager-console gebruiken om clientapparaten waarvoor opnieuw opstarten te identificeren en gebruik vervolgens een melding clientactie te starten.

Zie [clients in System Center Configuration Manager beheren](/sccm/core/clients/manage/manage-clients#restart-clients)


<!--  ## Compliance settings  -->


## <a name="application-management"></a>Toepassingsbeheer
### <a name="improvements-for-run-scripts------1236459---"></a>Verbeteringen voor het uitvoeren van Scripts<!-- 1236459 -->
Deze versie biedt verschillende verbeteringen voor de **Scripts uitvoeren** functie kunt u PowerShell-scripts uit te voeren op beheerde apparaten implementeren. Deze functie is geïntroduceerd in versie 1706.

Verbeteringen zijn onder andere:
- Beveiligingsbereiken gebruiken om te bepalen wie Scripts uitvoeren kunt
- Real-time bewaking van de scripts die u uitvoert
- Parameters voor de weergave van het script in Script-Wizard maken ondersteuning voor validatie en worden aangeduid als verplicht of optioneel.

Zie voor meer informatie over het gebruik van Scripts uitvoeren [maken en uitvoeren van scripts](../../../apps/deploy-use/create-deploy-scripts.md).

### <a name="new-mobile-application-management-policy-settings"></a>Nieuwe beleidsinstellingen voor mobile application management
<!-- 1324760 -->
De volgende instellingen zijn toegevoegd aan de mobiele toepassing management-beleidsinstellingen:
- **Synchronisatie van contactpersonen uitschakelen**: Hiermee voorkomt dat de app opslaan van gegevens in de systeemeigen contactpersonen-app op het apparaat.
- **Afdrukken uitschakelen**: Voorkomt dat de app vanuit afdrukken werk- of schoolgegevens.

### <a name="software-center-no-longer-distorts-icons-larger-than-250x250"></a>Software Center niet meer mogelijk vervormd pictogrammen groter is dan 250 x 250  
<!-- 1356194 -->

Software Center wordt met deze release niet meer vervormd pictogrammen die groter dan 250 x 250 zijn. Software Center gedaan deze pictogrammen fuzzy zoeken. U kunt nu een pictogram met een afmetingen in pixels van maximaal 512 x 512 instellen en zonder vervormd wordt weergegeven.

Zie voor informatie over het toevoegen van een pictogram voor uw app in Software Center [toepassingen maken](/sccm/apps/deploy-use/create-applications).

## <a name="operating-system-deployment"></a>Implementatie van besturingssystemen
 > [!TIP]   
 > <!-- 1354281 -->
 > Beginnen met Windows 10 versie 1709 (ook wel bekend als de vallen auteurs Update), bevat Windows media meerdere edities. Bij het configureren van een takenreeks om een upgradepakket voor besturingssysteem of de installatiekopie van besturingssysteem te gebruiken, moet u selecteren een [-editie die wordt ondersteund voor gebruik door Configuration Manager](/sccm/core/plan-design/configs/support-for-windows-10#windows-10-as-a-client).

### <a name="add-child-task-sequences-to-a-task-sequence"></a>Takenreeksen onderliggende toevoegen aan een takenreeks
<!-- 1261338 -->

U kunt een nieuwe takenreeksstap met een andere takenreeks die u een bovenliggende/onderliggende relatie tussen de takenreeksen maakt toevoegen. Hiermee kunt u meer modulaire takenreeksen maken die u opnieuw kunt gebruiken.  

Zie voor meer informatie over de onderliggende takenreeks, [onderliggende takenreeks](/sccm/osd/understand/task-sequence-steps#child-task-sequence).

## <a name="software-center-customization"></a>Aanpassing van software Center
<!-- 1351224 -->
U kunt enterprise huisstijl elementen toevoegen en geef de zichtbaarheid van tabbladen in Software Center. U kunt de naam van uw Software Center-specifieke bedrijf toevoegen, een kleurthema van Software Center configuratie instellen, een bedrijfslogo, en instellen van de zichtbare tabbladen voor clientapparaten.

Zie [Toepassingsbeheer plannen en configureren in System Center Configuration Manager](/sccm/apps/plan-design/plan-for-and-configure-application-management) 

## <a name="software-updates"></a>Software-updates

### <a name="surface-driver-updates-----1098490---"></a>Updates voor Surface stuurprogramma 's<!-- 1098490 -->
Vanaf deze release is is het beheren van updates voor Surface stuurprogramma's niet langer een functie van de voorlopige versie.  


## <a name="reporting"></a>Rapporten

### <a name="limit-windows-10-enhanced-telemetry-to-only-send-data-relevant-to-windows-analytics-device-health"></a>Windows 10 verbeterde telemetrie alleen om gegevens te verzenden relevant zijn voor Windows Analytics Apparaatstatus beperken
<!-- 1356148 -->

U kunt nu instellen de gegevensverzameling voor Windows 10-telemetrie op **uitgebreid (beperkt)**. Deze instelling kunt u actie worden uitgevoerd om inzicht te krijgen over de apparaten in uw omgeving zonder apparaten rapportage van de gegevens in de **uitgebreid** telemetrie niveau met Windows 10 versie 1709 of hoger.

Zie voor meer informatie [het configureren van clientinstellingen in System Center Configuration Manager](/sccm/core/clients/deploy/configure-client-settings).

<!-- ## Inventory  -->


## <a name="mobile-device-management"></a>Beheer van mobiele apparaten

### <a name="windows-10-arm64-device-support"></a>Ondersteuning voor Windows 10 ARM64 apparaten
<!-- 1355000 -->

Hybride mobile device management (MDM)-scenario's worden ondersteund op ARM64 apparaten met Windows 10 wanneer deze apparaten beschikbaar zijn.

Deze scenario's omvatten:

- [Apparaten inschrijven](../../../mdm/deploy-use/enroll-hybrid-windows.md)
- [Volledige en selectief wissen op afstand bewerkingen uitvoeren](../../../mdm/deploy-use/wipe-lock-reset-devices.md)
- [Instellingen door middel van configuratie-items en basislijnen beheren](../../../mdm/deploy-use/create-configuration-items-for-windows-8.1-and-windows-10-devices-managed-without-the-client.md)
- [Nalevingsbeleid voor apparaten beheren](../../../mdm/deploy-use/device-compliance-policies.md)
- De toegang tot bedrijfsbronnen via beheren:
   - [Certificaatprofielen](../../../mdm/deploy-use/create-pfx-certificate-profiles.md)
   - [VPN-profielen](../../../mdm/deploy-use/create-vpn-profiles.md)
   - [Wi-Fi-profielen](../../../mdm/deploy-use/create-wifi-profiles.md)
   - [E-mailprofielen](../../../mdm/deploy-use/create-exchange-activesync-profiles.md)
- [Configureer Windows Hello voor bedrijven-beleid](../../../mdm/deploy-use/windows-hello-for-business-settings.md)
- [Toepassingen beheren](../../../mdm/deploy-use/management-tasks-applications.md)

### <a name="improved-vpn-profile-experience-in-configuration-manager-console"></a>Verbeterde VPN-profiel ervaring in Configuration Manager-Console 
<!-- 1318232 -->

We hebben de VPN-profiel wizard eigenschappen pagina's en om weer te geven van de instellingen die geschikt is voor het geselecteerde platform bijgewerkt met deze versie:


- Elk platform heeft een eigen workflow, wat betekent dat nieuwe VPN-profielen alleen de instelling die wordt ondersteund door het platform bevatten.
- De **ondersteunde Platforms** pagina wordt nu weergegeven na de **algemene** pagina.  U kunt nu het platform kiezen voordat u de waarden van eigenschappen.
- Wanneer het platform is ingesteld op **Android**, **Android for Work**, of **Windows Phone 8.1**, wordt de **ondersteunde platforms** pagina is niet nodig en is niet weergegeven.
- De werkstroom op basis van een client van Configuration Manager is nu gecombineerd met de hybride mobiele apparaten (MDM)-client-werkstromen op basis van Windows 10; ze ondersteunen dezelfde instellingen.
- Elke werkstroom platform bevat alleen de instellingen die geschikt is voor die werkstroom.  De Android werkstroom bevat bijvoorbeeld instellingen voor Android; instellingen voor iOS of Windows 10 Mobile wordt niet meer weergegeven in de Android-werkstroom.
- Voor Windows 8.1-apparaten, verbindingstypen worden beheerd door Configuration Manager-client (wordt niet ondersteund door Intune) duidelijk zijn gemarkeerd.
- De automatische VPN-pagina is verouderd en is verwijderd.

Deze wijzigingen van toepassing op nieuwe VPN-profielen.  

Compatibiliteit om risico te beperken, zijn de bestaande VPN-profielen ongewijzigd.  Wanneer u een bestaand profiel bewerkt, worden de instellingen weergegeven zoals wanneer het profiel is gemaakt.  

Zie voor meer informatie [VPN-profielen op mobiele apparaten in System Center Configuration Manager](../../../mdm/deploy-use/create-vpn-profiles.md).

### <a name="limited-support-for-cryptography-next-generation-cng-certificates----1356191---"></a>Beperkte ondersteuning voor cryptografie: Volgende Generation (CNG)-certificaten<!-- 1356191 -->

Configuration Manager biedt beperkte ondersteuning voor cryptografie: Volgende Generation (CNG)-certificaten. Configuration Manager-clients kunnen PKI-clientverificatiecertificaat met persoonlijke sleutel in CNG Sleutelarchiefprovider (KSP) gebruiken. Met ondersteuning voor KSP ondersteuning Configuration Manager-clients voor op hardware gebaseerde persoonlijke sleutel, zoals TPM KSP voor PKI-verificatie van clientcertificaten.

Zie voor meer informatie [CNG-certificaten overzicht](../network/cng-certificates-overview.md).

## <a name="protect-devices"></a>Apparaten beveiligen

### <a name="create-and-deploy-exploit-guard-policies"></a>Ter voorkoming van misbruik beleid maken en implementeren
<!-- 1355468 -->

U kunt [beleid maken en implementeren](/sccm/protect/deploy-use/create-deploy-exploit-guard-policy) dat alle vier onderdelen van Windows Defender misbruiken Guard, met inbegrip van de aanval beperken, toegang tot beheerde map misbruik beveiliging en netwerkbeveiliging beheren.

### <a name="create-and-deploy-windows-defender-application-guard-policy"></a>Windows Defender toepassing Guard beleid maken en implementeren
<!-- 1351960 -->

U kunt [maken en implementeren van beleid voor Windows Defender toepassing Guard](/sccm/protect/deploy-use/create-deploy-application-guard-policy) met behulp van de Configuration Manager endpoint protection.

### <a name="device-guard-policy-changes"></a>Device Guard beleidswijzigingen
<!-- 1355092 -->
De volgende drie wijzigingen zijn aangebracht ten opzichte van Device Guard beleid:

- Device Guard beleidsregels is hernoemd aan beleidsregels voor toepassingsbeheer voor Windows Defender. Zo is, bijvoorbeeld de **wizard beleid voor Device Guard maken** heet nu **wizard beleid voor Windows Defender Toepassingsbeheer maken**.
- Apparaten met behulp van de vallen auteurs Update voor Windows versie 1709 niet moeten opnieuw worden opgestart om toe te passen van het beleid voor toepassingsbeheer voor Windows Defender. Opnieuw opstarten is nog steeds de standaard, maar u kunt [opnieuw opstarten uitschakelen](/sccm/protect/deploy-use/use-device-guard-with-configuration-manager).
- U kunt [apparaten ingesteld op automatisch uitgevoerde software](/sccm/protect/deploy-use/use-device-guard-with-configuration-manager) vertrouwd door de Intelligent Security-grafiek.





## <a name="next-steps"></a>Volgende stappen
Wanneer uw gereed voor installatie van deze versie, Zie [Updates voor Configuration Manager](/sccm/core/servers/manage/updates).
