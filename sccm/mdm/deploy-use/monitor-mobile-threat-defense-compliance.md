---
title: Mobiele bedreiging verdediging naleving controleren | System Center Configuration Manager
description: Monitor voor de mobiele bedreiging verdediging partner compatibiliteitsstatus van de manager van Configuration Manager-console
ms.custom: na
ms.date: 03/21/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 408190da-bea6-4122-9dd6-f90155040e88
caps.latest.revision: 
author: andredm7
ms.author: andredm
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 212628639300e9c361f7cee61b3df6b1cb6874ce
ms.openlocfilehash: 8edf83a0f761dfc16274ce49c3aa2b878c7fe6cd
ms.contentlocale: nl-nl
ms.lasthandoff: 05/17/2017


---

# <a name="monitor-mobile-threat-defense-compliance"></a>**Mobiele bedreiging verdediging naleving controleren**

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*

## <a name="to-monitor-the-overall-compliance-status"></a>Voor het bewaken van de algehele status van naleving

De mobiele bedreiging verdediging om status te controleren:

1.  Klik in de Configuration Manager-console op **bewaking** werkruimte.

2.  In de **bewaking** werkruimte, klik op de **beveiliging** knooppunt.

U kunt een samenvatting van de compatibiliteitsstatus met andere bedreiging niveaus, dat wordt weergegeven in een visual diagram kunt zien. U kunt klikken op de afzonderlijke onderdelen van de grafieken voor meer informatie, zoals: 

- Het aantal apparaten die rapporteren als niet-compatibel per platform
- Eventuele fouten met betrekking tot de compatibiliteitsstatus van apparaat

![](http://i.imgur.com/bmPsiWk.png)

## <a name="to-monitor-the-individual-compliance-status"></a>De status van afzonderlijke naleving controleren

U kunt ook de status van afzonderlijke apparaten zien:

1.  Klik in de Configuration Manager-console op **activa en naleving** werkruimte.

2.  Klik op **apparaten**.

> [!TIP] 
> U kunt toevoegen de **bedreiging apparaatcompatibiliteit** en de **apparaat risiconiveau** kolommen voor de status. Deze kolommen worden niet standaard weergegeven.

## <a name="device-threat-protection-tab"></a>Apparaat dreigingen tabblad

Daarnaast op het **apparaten** scherm, u kunt specifieke apparaten selecteren en vervolgens klikt u op de **apparaat bedreiging beveiliging** tabblad vindt u meer details over de compatibiliteitsstatus van het apparaat. Vinden onder de kolombeschrijvingen van de en hun waarden verwacht bij het analyseren van de compatibiliteitsstatus van het apparaat.

> [!IMPORTANT] 
> Het tabblad Beveiliging van apparaat bedreiging alleen weergegeven als een mobiel apparaat is het geselecteerde apparaat.

|Kolomnaam|Standaard zichtbaar|Beschrijving| 
|-|-|-|
|**Beschrijving**| Ja | Gegevens over de bedreiging geleverd door de mobiele bedreiging verdediging partner. |
|**Tijd van laatste update**| Ja | De laatste keer dat de partner mobiele bedreiging verdediging bijgewerkte informatie over de bedreiging voor Intune verzonden. |
|**Bedreiging ernst**| Ja | Ernst bedreiging is de definitie voor een afzonderlijke dreiging op basis van de configuratie van de beheerder in de console mobiele bedreiging verdediging partner. Er is een van de drie waarden: **Low**, **Medium** or **High** |
|**Bedreiging status**| Ja | De huidige status van de dreiging op het apparaat. Mogelijke statussen: **Actieve**, **opgelost** of **genegeerd:** Geeft aan dat de gebruiker genegeerd de dreiging op hun apparaat, maar de bedreiging nog steeds aanwezig is. |
|**Type bedreiging**| Ja | Mobiele bedreiging verdediging Partnertype bedreiging. Mogelijke waarden: **App**, **File** or **OS** |
|**AAD-Account-ID**| Nee | De unieke id van de Azure Active Directory. |
|**Classificatie**| Ja | Mobiele bedreiging verdediging partner classificatie van dreiging opgegeven. Mogelijke waarden: **Hoofdmap factor, Riskware, Adware, Chargeware, DataLeak, Trojaanse paarden, Worm, Virus, misbruiken, achterdeur bot's, AppDropper, ClickFraud, Spam, Spyware, SurveillanceWare, beveiligingsprobleem, onbekend, Jailbrake, connectiviteit, TollFraud, SideloadedApp hoofdmap** |
|**Apparaat-ID**| Nee | De Azure Active Directory-object-ID voor de werkplek apparaat lid is van dreiging informatie. |
|**Bedreiging-ID**| Nee | Mobiele bedreiging verdediging partner unieke id voor de bedreiging gegenereerd. De ID bedreiging wordt gebruikt voor het bijhouden van de oplossing. |
|**Bedreiging URL**| Nee | Wanneer aanwezig is, opnieuw de bedreiging URL-koppelingen naar de mobiele bedreiging verdediging-partner management consoleweergave van deze specifieke bedreiging. |

> [!TIP] 
> Zorg dat u het inschakelen van de kolommen die geen **standaard zichtbaar** voor meer informatie over de mobiele bedreiging verdediging compatibiliteitsstatus voor uw apparaten.

