---
title: Beperk de toegang op basis van risico | Microsoft-documenten
description: Beperk de toegang tot bedrijfsbronnen op basis van het apparaat, netwerk en toepassing risico.
ms.custom: na
ms.date: 04/25/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-hybrid
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 9083c571-f4fc-4a78-adc5-8aec84dabcbd
caps.latest.revision: 
author: andredm7
ms.author: andredm
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: c6a6137fa978e1ea28aefea2aea4e29ba661efd6
ms.openlocfilehash: 21841d97387f07f53993d957641f9ad892d723c2
ms.contentlocale: nl-nl
ms.lasthandoff: 05/17/2017


---
# <a name="manage-access-to-company-resource-based-on-device-network-and-application-risk"></a>Toegang tot bedrijfsresources op basis van het apparaat, netwerk- en toepassing risico beheren

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*

U kunt de toegang van mobiele apparaten tot bedrijfsbronnen op basis van risico evaluatie die altijd, een oplossing voor Apparaatbeheer bedreiging beveiliging die is geïntegreerd met Microsoft Intune. Het risico is gebaseerd op telemetrische informatie bij die de service altijd uit apparaten voor het besturingssysteem (OS) beveiligingslekken geïnstalleerde schadelijke apps en schadelijke netwerkprofielen verzamelt. 

Op basis van de gerapporteerde risicoanalyse van altijd ingeschakeld via nalevingsbeleid voor System center configuration manager (SCCM), kunt u beleidsregels voor voorwaardelijke toegang configureren en toestaan of blokkeren van apparaten die niet compliant is vanwege bedreigingen gedetecteerd op deze apparaten zijn vastgesteld.

De [hybride MDM-implementatie (SCCM met Intune)](https://docs.microsoft.com/sccm/mdm/understand/choose-between-standalone-intune-and-hybrid-mobile-device-management) biedt u de mogelijkheid om te bepalen van de toegang tot bedrijfsbronnen en gegevens op basis van risicoanalyse dat apparaat dreiging oplossingen zoals altijd biedt.

## <a name="how-do-the-hybrid-mdm-deployment-and-lookout-device-threat-protection-help-protect-company-resources"></a>Hoe de implementatie van hybride MDM en profiteer zo veel mogelijk apparaat bedreiging bescherming beschermen bedrijfsbronnen?
Zoek de mobiele app (zoek naar werk), uitgevoerd op mobiele apparaten, bestandssysteem, netwerkstack, apparaat en toepassing telemetrie vastgelegd (indien beschikbaar) en verzendt dit naar de altijd apparaat bedreiging protection cloud-service voor het berekenen van een statistische apparaat risico voor mobiele bedreigingen. U kunt ook de indeling van het risiconiveau voor de bedreigingen in de console altijd volgens uw vereisten wijzigen.  

Het nalevingsbeleid in SCCM bevat nu een nieuwe regel voor altijd mobiele bedreiging beveiliging die is gebaseerd op de altijd apparaat bedreiging risico-evaluatie. Als deze regel is ingeschakeld, wordt het apparaat op compatibiliteit geëvalueerd.

Als het apparaat wordt als niet-compatibel met het nalevingsbeleid bepaald, betekent dit dat toegang tot bronnen, zoals Exchange Online en SharePoint Online kunt met behulp van beleid voor voorwaardelijke toegang geblokkeerd. Wanneer de toegang is geblokkeerd, worden de eindgebruikers verstrekt met een overzicht om te helpen het probleem op te lossen en toegang krijgen tot bedrijfsbronnen. In dit scenario wordt gestart via altijd werk app.

## <a name="supported-platforms"></a>Ondersteunde platforms:
* **Android 4.1 en hoger**, en die zijn ingeschreven bij Microsoft Intune.
* **iOS 8 en hoger**, en die zijn ingeschreven bij Microsoft Intune.
Zie voor informatie over platforms en talen die ondersteuning biedt voor zoek [artikel](https://personal.support.lookout.com/hc/en-us/articles/114094140253).

## <a name="prerequisites"></a>Vereisten:
* [Hybride MDM-implementatie](https://docs.microsoft.com/sccm/mdm/understand/choose-between-standalone-intune-and-hybrid-mobile-device-management)
* Een abonnement op Microsoft Intune en Azure Active Directory.
* Een enterprise-abonnement op zoek mobiele EndPoint Security.  Zie voor meer informatie [altijd mobiele Endpoint Security](https://www.lookout.com/products/mobile-endpoint-security)

## <a name="example-scenarios"></a>Voorbeeldscenario 's
Hieronder volgen enkele algemene scenario's:
### <a name="control-access-based-on-threat-from-malicious-apps"></a>De toegang beheren op basis van de bedreiging van schadelijke apps:
Wanneer schadelijke apps zoals kwaadaardige software wordt gedetecteerd op het apparaat, kunt u deze apparaten vanaf blokkeren:
* Verbinding maken met bedrijfs-e-voordat de bedreiging oplossen.
* Synchroniseren van zakelijke bestanden met behulp van de OneDrive voor werk app.
* Toegang tot bedrijfskritische apps.

**Toegang geblokkeerd als schadelijke apps worden gedetecteerd:**

![diagram van voorwaardelijke toegang beleid blokkeren, toegang wanneer het apparaat wordt bepaald dat niet-compatibel vanwege schadelijke apps op het apparaat](media/config-mgr-maliciousapps_blocked.png)

**Apparaat gedeblokkeerd en is toegang tot bedrijfsbronnen krijgen wanneer de bedreiging is hersteld:**

![diagram van beleid voor voorwaardelijke toegang verlenen van toegang wanneer het apparaat wordt bepaald dat deze compatibel na herstel](media/config-mgr-maliciousapps-unblocked.png)
### <a name="control-access-based-on-threat-to-network"></a>De toegang beheren op basis van een bedreiging vormt voor het netwerk:
Detecteer bedreigingen uw netwerk, zoals Man-in-the-middle-aanvallen en beperk de toegang tot Wi-Fi-netwerken die op basis van het risico van het apparaat.

**Toegang tot het netwerk via Wi-Fi geblokkeerd:**

![diagram van voorwaardelijke toegang blokkeren Wi-Fi-toegang op basis van netwerk bedreigingen](media/config-mgr-network-wifi-blocked.png)

**Er is toegang verleend op herstel:**

![diagram van voorwaardelijke toegang op herstel van de bedreiging toegang toe te staan](media/config-mgr-network-wifi-unblocked.png)
### <a name="control-access-to-sharepoint-online-based-on-threat-to-network"></a>Toegang tot SharePoint Online op basis van een bedreiging vormt voor het netwerk beheren:

Bedreigingen uw netwerk, zoals Man-in-the-middle-aanvallen detecteren en te voorkomen dat de synchronisatie van zakelijke bestanden op basis van het risico van het apparaat.

**Toegang tot SharePoint Online op basis van netwerk bedreiging is gedetecteerd op het apparaat geblokkeerd:**

![Diagram van voorwaardelijke toegang blokkeren Apparaattoegang tot SharePoint Online op basis van dreiging detectie](media/config-mgr-network-spo-blocked.png)


**Er is toegang verleend op herstel:**

![Diagram van voorwaardelijke toegang toegang toe te staan nadat de netwerk-bedreiging is hersteld](media/config-mgr-network-spo-unblocked.png)

## <a name="next-steps"></a>Volgende stappen
Hier worden de belangrijkste stappen die u doen moet om deze oplossing te implementeren:
1.    [Instellen van uw abonnement met altijd mobiele bedreiging-beveiliging](set-up-your-subscription-with-lookout.md)
2.    [Zoek MTP-verbinding in Intune inschakelen](enable-lookout-connection-in-intune.md)
3.  [Configureer en implementeer altijd voor werktoepassing](configure-and-deploy-lookout-for-work-apps.md)
4.    [Nalevingsbeleid configureren](enable-device-threat-protection-rule-compliance-policy.md)
5.    [Zoek integratie oplossen](troubleshoot-lookout-integration.md)

