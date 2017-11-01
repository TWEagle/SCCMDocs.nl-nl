---
title: Mobile Threat Defense-naleving bewaken
titleSuffix: Configuration Manager
description: De status van naleving partner Mobile Threat verdediging vanuit de console van Configuration manager controleren
ms.custom: na
ms.date: 03/21/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 408190da-bea6-4122-9dd6-f90155040e88
caps.latest.revision: 
author: andredm7
ms.author: andredm
manager: angrobe
ms.openlocfilehash: 33c2d3c05020d0c06344bfe6bb67a35f7d75e51d
ms.sourcegitcommit: c236214b2fcc13dae7bad96d7fb33f692868191d
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/12/2017
---
# <a name="monitor-mobile-threat-defense-compliance"></a>**Mobile Threat Defense-naleving bewaken**

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*

## <a name="to-monitor-the-overall-compliance-status"></a>De algehele status van naleving bewaken

De status van de verdediging mobiele threat bewaken:

1.  Klik in de Configuration Manager-console op **bewaking** werkruimte.

2.  In de **bewaking** werkruimte, klik op de **beveiliging** knooppunt.

U kunt een samenvatting van de compatibiliteitsstatus met verschillende threat niveaus, die wordt weergegeven in een visual diagram kunt zien. U kunt klikken op de afzonderlijke secties van de grafieken voor meer informatie, zoals: 

- Het aantal apparaten die rapporteren als niet-compatibel per platform
- Eventuele fouten met betrekking tot de compatibiliteitsstatus van het apparaat

![](http://i.imgur.com/bmPsiWk.png)

## <a name="to-monitor-the-individual-compliance-status"></a>De status van afzonderlijke naleving bewaken

U ziet ook de status van afzonderlijke apparaten:

1.  Klik in de Configuration Manager-console op **activa en naleving** werkruimte.

2.  Klik op **apparaten**.

> [!TIP] 
> U kunt toevoegen de **threat apparaatcompatibiliteit** en de **apparaat risiconiveau** kolommen om de status te bekijken. Deze kolommen worden niet standaard weergegeven.

## <a name="device-threat-protection-tab"></a>Device Threat Protection-tabblad

Bovendien op de **apparaten** scherm, u kunt specifieke apparaten selecteren en vervolgens klikt u op de **Device Threat Protection** tabblad dat meer informatie over de compatibiliteitsstatus van het apparaat biedt. Vinden onder de kolombeschrijvingen en hun waarden verwacht bij het analyseren van de compatibiliteitsstatus van het apparaat.

> [!IMPORTANT] 
> Het tabblad Device Threat Protection alleen weergegeven als een mobiel apparaat is het geselecteerde apparaat.

|Kolomnaam|Standaard zichtbaar|Beschrijving| 
|-|-|-|
|**Beschrijving**| Ja | Gegevens over de bedreiging geleverd door de mobiele Threat Defense-partner. |
|**Laatst bijgewerkt**| Ja | De partner Mobile Threat verdediging verzonden voor het laatst bijgewerkt details over de bedreiging voor Intune. |
|**Threat ernst**| Ja | Ernst van de Threat is de definitie voor een afzonderlijke dreiging op basis van de configuratie van de beheerder in de console van de partner Mobile Threat verdediging. Er is een van de drie waarden: **Lage**, **gemiddeld** of **hoog** |
|**Status van de Threat**| Ja | De huidige status van de dreiging op het apparaat. Mogelijke statussen: **Actieve**, **opgelost** of **genegeerd:** Hiermee wordt aangegeven dat de gebruiker de dreiging op hun apparaat genegeerd, maar het gevaar nog steeds aanwezig is. |
|**Threat type**| Ja | Mobile Threat verdediging partner type threat. Mogelijke waarden: **App**, **bestand** of **OS** |
|**AAD-Account-ID**| Nee | De unieke id van de Azure Active Directory. |
|**Classificatie**| Ja | Mobile Threat verdediging partner classificatie van bedreiging wordt opgegeven. Mogelijke waarden: **Basis-factor, Riskware, Adware, Chargeware, DataLeak, Trojaanse paarden, Worm, Virus, misbruik, achterdeur Bot, AppDropper, ClickFraud, Spam, Spyware, SurveillanceWare, beveiligingsprobleem, onbekend, Jailbrake, connectiviteit, TollFraud, SideloadedApp hoofdmap** |
|**Apparaat-ID**| Nee | De Azure Active Directory-object-ID voor de werkplek toegevoegd apparaat met informatie. |
|**Bedreigings-ID**| Nee | Mobile Threat verdediging partner unieke id voor de bedreiging gegenereerd. De Bedreigings-ID wordt gebruikt voor het bijhouden van resolutie. |
|**URL van de Threat**| Nee | Wanneer aanwezig is, wordt de URL van de Threat koppelingen naar de mobiele Threat Defense-partner management console-weergave van deze specifieke bedreiging opnieuw. |

> [!TIP] 
> Zorg ervoor dat u het inschakelen van de kolommen die geen **standaard zichtbaar** voor meer informatie over de status van de naleving Mobile Threat verdediging voor uw apparaten.
