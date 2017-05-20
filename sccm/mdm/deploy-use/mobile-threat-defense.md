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
ms.openlocfilehash: 250671660c1c6da0ca9b593b06b8f344dfe17ad6
ms.contentlocale: nl-nl
ms.lasthandoff: 05/17/2017


---

# <a name="manage-access-to-company-resource-based-on-device-network-and-application-risk"></a>Toegang tot bedrijfsresources op basis van het apparaat, netwerk- en toepassing risico beheren

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*

Mobiele bedreiging verdediging connectors kunnen u gebruikmaken van de leverancier van uw gekozen mobiele bedreiging verdediging als een bron van informatie voor uw nalevingsbeleid en regels voor voorwaardelijke toegang. Dit kunnen IT-beheerders een beveiligingslaag toevoegen aan hun bedrijfsbronnen zoals Exchange en Sharepoint, speciaal van meer mobiele apparaten.

## <a name="what-problem-does-this-solve"></a>Wat is het probleem opgelost.

Gevoelige gegevens beschermen tegen mogelijke bedreigingen zoals fysieke, op basis van een app, en op het netwerk, en het besturingssysteem beveiligingslekken moeten bedrijven.
Bedrijven zijn, in het verleden proactieve wanneer pc's beveiligen tegen een aanval, terwijl mobiele apparaten niet bewaakt, en niet-beveiligde gaat. Mobiele platforms hebt geïntegreerde beveiliging zoals app isolatie en gerenommeerde consument app stores, maar deze systemen blijven kwetsbaar voor geavanceerde aanvallen. Vandaag meer werknemers apparaten gebruiken voor het werk en toegang tot gevoelige informatie nodig. Apparaten moeten worden beschermd tegen steeds meer geavanceerde aanvallen.

De [hybride MDM-implementatie (SCCM met Intune)](https://docs.microsoft.com/sccm/mdm/understand/choose-between-standalone-intune-and-hybrid-mobile-device-management) biedt u de mogelijkheid de toegang tot bedrijfsbronnen en gegevens op basis van risicoanalyse die apparaat bedreiging oplossingen zoals mobiele bedreiging verdediging partners bieden.

## <a name="how-the-intune-mobile-threat-defense-connectors-work"></a>Hoe de Intune Mobile bedreiging verdediging connectors werken?

De connector beschermt bedrijfsbronnen te maken van een kanaal van communicatie tussen Intune en de leverancier van uw gekozen mobiele bedreiging verdediging. Intune Mobile bedreiging verdediging partners bieden intuïtieve, eenvoudig te implementeren van toepassingen voor mobiele apparaten die actief scannen en analyseren van informatie over de bedreiging voor het delen met Intune, voor een rapport of afdwinging doeleinden. Bijvoorbeeld, als een verbonden mobiele bedreiging verdediging app aan de leverancier mobiele bedreiging verdediging een telefoon op uw netwerk is momenteel is verbonden met een netwerk dat vatbaar voor Man in de Middle-aanvallen rapporteert is, deze informatie wordt gedeeld met en gecategoriseerd voor een juiste risiconiveau (laag/gemiddeld/hoog –) die vervolgens kan worden vergeleken met de geconfigureerde risico niveau rechten in Intune om te bepalen als toegang tot bepaalde bronnen van uw keuze worden ingetrokken terwijl de apparaat is aangetast.

## <a name="sample-scenarios"></a>Voorbeeldscenario 's

Wanneer een apparaat wordt beschouwd als geïnfecteerd door de mobiele bedreiging verdediging oplossing:

![Mobiele bedreiging verdediging geïnfecteerd apparaat](../media/mtp/MTD-image-1.png)

Toegang te krijgen wanneer het apparaat is hersteld:

![Mobiele bedreiging verdediging toegang verleend](../media/mtp/MTD-image-2.png)

## <a name="next-steps"></a>Volgende stappen

Meer informatie over het beveiligen van toegang tot bedrijfsresources op basis van het apparaat, netwerk- en toepassing risico met:

- [Zoek](https://docs.microsoft.com/intune/deploy-use/lookout-mobile-threat-defense-connector)
