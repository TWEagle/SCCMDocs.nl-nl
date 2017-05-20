---
title: Mobiele bedreiging verdediging | System Center Configuration Manager
description: Beperk de toegang tot bedrijfsbronnen op basis van het apparaat, netwerk en toepassing risico met behulp van Configuration Manager en de Intune Mobile bedreiging verdediging partners
ms.custom: na
ms.date: 03/02/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 4c0e6824-2dfe-4700-b817-d5631e0eb872
caps.latest.revision: 
author: andredm7
ms.author: andredm
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 266897b7ac674a369931e8ed63ff464edc10c9d8
ms.openlocfilehash: 298d879638a2d20d421b19752cb5f20f6725df14
ms.contentlocale: nl-nl
ms.lasthandoff: 05/17/2017


---
# <a name="intune-mobile-threat-defense-connectors-in-configuration-manager"></a>Intune Mobile bedreiging verdediging connectors in Configuration Manager

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*

De [hybride MDM-implementatie (SCCM met Intune)](https://docs.microsoft.com/en-us/sccm/mdm/understand/choose-between-standalone-intune-and-hybrid-mobile-device-management) en de integratie tussen Intune en de mobiele bedreiging verdediging partners geeft u de mogelijkheid de toegang tot bedrijfsbronnen en gegevens op basis van risicoanalyse apparaat beheren.

Intune Mobile bedreiging verdediging connectors kunnen u gebruikmaken van de leverancier van uw gekozen mobiele bedreiging verdediging als een bron van informatie voor uw nalevingsbeleid en regels voor voorwaardelijke toegang. Dit kunnen IT-beheerders een beveiligingslaag toevoegen aan hun bedrijfsbronnen zoals Exchange en Sharepoint, speciaal van meer mobiele apparaten.

## <a name="what-problem-does-this-solve"></a>Wat is het probleem opgelost.

Gevoelige gegevens beschermen tegen mogelijke bedreigingen zoals fysieke, op basis van een app, en op het netwerk, en het besturingssysteem beveiligingslekken moeten bedrijven.
Bedrijven zijn, in het verleden proactieve wanneer pc's beveiligen tegen een aanval, terwijl mobiele apparaten niet bewaakt, en niet-beveiligde gaat. Mobiele platforms hebt geïntegreerde beveiliging zoals app isolatie en gerenommeerde consument app stores, maar deze systemen blijven kwetsbaar voor geavanceerde aanvallen. Vandaag meer werknemers apparaten gebruiken voor het werk en toegang tot gevoelige informatie nodig. Apparaten moeten worden beschermd tegen steeds meer geavanceerde aanvallen.

## <a name="how-the-intune-mobile-threat-defense-connectors-work"></a>Hoe de Intune Mobile bedreiging verdediging connectors werken?

De connector beschermt bedrijfsbronnen te maken van een kanaal van communicatie tussen Intune en de leverancier van uw gekozen mobiele bedreiging verdediging. Intune Mobile bedreiging verdediging partners bieden intuïtieve, eenvoudig te implementeren van toepassingen voor mobiele apparaten die actief scannen en analyseren van informatie over de bedreiging voor het delen met Intune, voor een rapport of afdwinging doeleinden. Bijvoorbeeld, als een verbonden mobiele bedreiging verdediging app aan de leverancier mobiele bedreiging verdediging een telefoon op uw netwerk is momenteel is verbonden met een netwerk dat vatbaar voor Man in de Middle-aanvallen rapporteert is, deze informatie wordt gedeeld met en gecategoriseerd voor een juiste risiconiveau (laag/gemiddeld/hoog –) die vervolgens kan worden vergeleken met de geconfigureerde risico niveau rechten in Intune om te bepalen als toegang tot bepaalde bronnen van uw keuze worden ingetrokken terwijl de apparaat is aangetast.

## <a name="sample-scenarios"></a>Voorbeeldscenario 's

Wanneer een apparaat wordt beschouwd als geïnfecteerd door de mobiele bedreiging verdediging oplossing:

![](http://i.imgur.com/Li1WUOU.png)

Toegang te krijgen wanneer het apparaat is hersteld:

![](http://i.imgur.com/VCIwpdz.png)

## <a name="mobile-threat-defense-partners"></a>Mobiele bedreiging verdediging partners

Meer informatie over het beveiligen van toegang tot bedrijfsresources op basis van het apparaat, netwerk- en toepassing risico met:

- [Zoek](https://docs.microsoft.com/sccm/protect/deploy-use/lookout-mobile-threat-defense-in-configuration-manager)
