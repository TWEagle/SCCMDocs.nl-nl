---
title: Beperken van toegang op basis van risico | Microsoft Docs
description: Toegang tot bedrijfsbronnen op basis van apparaat-, netwerk- en toepassing risico beperken.
ms.custom: na
ms.date: 04/25/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: configmgr-hybrid
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 9083c571-f4fc-4a78-adc5-8aec84dabcbd
caps.latest.revision: 
author: andredm7
ms.author: andredm
manager: angrobe
ms.openlocfilehash: 21841d97387f07f53993d957641f9ad892d723c2
ms.sourcegitcommit: 51fc48fb023f1e8d995c6c4eacfda7dbec4d0b2f
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 08/07/2017
---
# <a name="manage-access-to-company-resource-based-on-device-network-and-application-risk"></a>Toegang tot bedrijfsbronnen op basis van apparaat-, netwerk- en toepassing risico's beheren

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*

U kunt mobiele apparaten toegang heeft tot bedrijfsbronnen op basis van de risico-evaluatie uitgevoerd door Lookout, een apparaat threat protection-oplossing die is geïntegreerd met Microsoft Intune kunt beheren. Het risico is gebaseerd op de telemetrie die de Lookout-service worden verzameld van apparaten voor het besturingssysteem (OS) beveiligingslekken geïnstalleerde schadelijke apps en schadelijke netwerkprofielen. 

Op basis van de Lookout gemelde risicoanalyse ingeschakeld via beleidsregels voor naleving van System center configuration manager (SCCM), kunt u beleid voor voorwaardelijke toegang configureren en toestaan of blokkeren van apparaten die niet compliant is als gevolg van bedreigingen die zijn gedetecteerd op deze apparaten zijn vastgesteld.

De [hybride MDM-implementatie (SCCM met Intune)](https://docs.microsoft.com/sccm/mdm/understand/choose-between-standalone-intune-and-hybrid-mobile-device-management) biedt u de mogelijkheid om te bepalen van de toegang tot bedrijfsbronnen en gegevens op basis van de risico-evaluatie dat apparaat dreiging oplossingen voor gegevensbeveiliging zoals Lookout biedt.

## <a name="how-do-the-hybrid-mdm-deployment-and-lookout-device-threat-protection-help-protect-company-resources"></a>Hoe de implementatie van hybride MDM en Lookout device threat protection helpen bedrijfsresources beveiligen?
Lookout van mobiele Apps (Lookout for work), uitgevoerd op mobiele apparaten, bestandssysteem, network-stack, apparaat en toepassing telemetrie vastgelegd (indien beschikbaar) en verzendt het naar de Lookout device threat protection cloudservice voor het berekenen van een statistische apparaat risico voor mobiele bedreigingen. U kunt ook de indeling van het risiconiveau voor het omgaan met bedreigingen in de console Lookout volgens uw vereisten wijzigen.  

Het nalevingsbeleid in SCCM bevat nu een nieuwe regel voor Lookout mobiele threat protection die is gebaseerd op de Lookout device threat risico-evaluatie. Als deze regel is ingeschakeld, wordt het apparaat op compatibiliteit geëvalueerd.

Als het apparaat wordt vastgesteld als niet-compatibel met het nalevingsbeleid, betekent dit dat toegang tot resources, zoals Exchange Online en SharePoint Online kunt met behulp van beleid voor voorwaardelijke toegang geblokkeerd. Wanneer toegang wordt geblokkeerd, wordt de eindgebruikers worden geleverd bij een scenario om u te helpen het probleem is opgelost en toegang krijgen tot bedrijfsbronnen. In dit scenario wordt gestart via de Lookout for work-app.

## <a name="supported-platforms"></a>Ondersteunde platforms:
* **Android 4.1 en hoger**, en ingeschreven bij Microsoft Intune.
* **iOS 8 en hoger**, en ingeschreven bij Microsoft Intune.
Zie voor informatie over platforms en talen die ondersteuning biedt voor Lookout [artikel](https://personal.support.lookout.com/hc/en-us/articles/114094140253).

## <a name="prerequisites"></a>Vereisten:
* [Hybride MDM-implementatie](https://docs.microsoft.com/sccm/mdm/understand/choose-between-standalone-intune-and-hybrid-mobile-device-management)
* Een abonnement op Microsoft Intune en Azure Active Directory.
* Een enterprise-abonnement op Lookout Mobile EndPoint Security.  Zie voor meer informatie [Lookout Mobile Endpoint Security](https://www.lookout.com/products/mobile-endpoint-security)

## <a name="example-scenarios"></a>Voorbeeldscenario 's
Hieronder volgen enkele algemene scenario's:
### <a name="control-access-based-on-threat-from-malicious-apps"></a>Toegangsbeheer op basis van dreiging van schadelijke apps:
Wanneer schadelijke apps zoals malware wordt gedetecteerd op het apparaat, kunt u dergelijke apparaten blokkeren:
* Verbinding maken met zakelijke e-mailadres voor het omzetten van de bedreiging.
* Synchroniseren van zakelijke bestanden met behulp van de OneDrive voor Work-app.
* Toegang tot essentiële apps.

**De toegang is geblokkeerd wanneer schadelijke apps worden gedetecteerd:**

![diagram van voorwaardelijk beleid blokkeren van toegang wanneer het apparaat niet-compatibele vanwege schadelijke apps op het apparaat wordt bepaald](media/config-mgr-maliciousapps_blocked.png)

**Apparaat gedeblokkeerd en toegang tot bedrijfsresources wanneer de bedreiging wordt hersteld is:**

![diagram van beleid voor voorwaardelijke toegang verlenen van toegang wanneer het apparaat wordt bepaald aan het beleid voldoen na herstel](media/config-mgr-maliciousapps-unblocked.png)
### <a name="control-access-based-on-threat-to-network"></a>Toegangsbeheer op basis van het netwerk:
Bedreigingen voor uw netwerk zoals Man-in-the-middle-aanvallen te detecteren en beperk de toegang tot Wi-Fi-netwerken op basis van het risico van het apparaat.

**Toegang tot netwerk via Wi-Fi geblokkeerd:**

![diagram van voorwaardelijke toegang blokkeren Wi-Fi-toegang op basis van bedreigingen voor netwerken](media/config-mgr-network-wifi-blocked.png)

**De toegang is verleend op herstel:**

![diagram van voorwaardelijke toegang waardoor de toegang van herstel van de bedreiging](media/config-mgr-network-wifi-unblocked.png)
### <a name="control-access-to-sharepoint-online-based-on-threat-to-network"></a>Toegang tot SharePoint Online op basis van het netwerk beheren:

Bedreigingen voor uw netwerk zoals Man-in-the-middle-aanvallen te detecteren en te voorkomen dat de synchronisatie van zakelijke bestanden op basis van het risico van het apparaat.

**Toegang tot SharePoint Online op basis van netwerk-bedreiging is gedetecteerd op het apparaat geblokkeerd:**

![Diagram van voorwaardelijke toegang Apparaattoegang tot SharePoint Online op basis van detectie van dreigingen worden geblokkeerd](media/config-mgr-network-spo-blocked.png)


**De toegang is verleend op herstel:**

![Diagram van voorwaardelijke toegang om toegang kunnen nadat de netwerk-bedreiging is hersteld](media/config-mgr-network-spo-unblocked.png)

## <a name="next-steps"></a>Volgende stappen
Hier volgen de belangrijkste stappen die u doen moet om deze oplossing te implementeren:
1.  [Instellen van uw abonnement met Lookout mobiele threat protection](set-up-your-subscription-with-lookout.md)
2.  [Lookout MTP-verbinding in Intune inschakelen](enable-lookout-connection-in-intune.md)
3.  [Configureer en implementeer Lookout voor work-toepassing](configure-and-deploy-lookout-for-work-apps.md)
4.  [Nalevingsbeleid configureren](enable-device-threat-protection-rule-compliance-policy.md)
5.  [Problemen oplossen met de integratie van Lookout](troubleshoot-lookout-integration.md)
