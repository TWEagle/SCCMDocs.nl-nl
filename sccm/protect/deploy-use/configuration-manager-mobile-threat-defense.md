---
title: Mobiele Threat verdediging | System Center Configuration Manager
description: Toegang tot bedrijfsbronnen op basis van het apparaat, netwerk- en risico's met behulp van Configuration Manager en Intune Mobile Threat verdediging partners beperken
ms.custom: na
ms.date: 03/02/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 4c0e6824-2dfe-4700-b817-d5631e0eb872
caps.latest.revision: 
author: andredm7
ms.author: andredm
manager: angrobe
ms.openlocfilehash: 25d68e7b16afe8e24939897f01f173d3daa7fa09
ms.sourcegitcommit: 621b9f8fedf7f1d53ea7abd804af4b63c85dbeb1
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/02/2017
---
# <a name="intune-mobile-threat-defense-connectors-in-configuration-manager"></a>Intune Mobile Threat verdediging connectors in Configuration Manager

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*

De [hybride MDM-implementatie (SCCM met Intune)](https://docs.microsoft.com/sccm/mdm/understand/choose-between-standalone-intune-and-hybrid-mobile-device-management) en de integratie tussen Intune en de partners Mobile Threat verdediging bieden u de mogelijkheid de toegang tot bedrijfsbronnen en gegevens op basis van het apparaat risico-evaluatie.

Intune Mobile Threat verdediging connectors kunnen u gebruikmaken van de leverancier van uw gekozen Mobile Threat verdediging als een bron van informatie voor uw nalevingsbeleid en de regels voor voorwaardelijke toegang. Dit kunnen IT-beheerders een beschermingslaag toevoegen aan hun bedrijfsbronnen zoals Exchange en Sharepoint, speciaal van verdacht mobiele apparaten.

## <a name="what-problem-does-this-solve"></a>Welk probleem opgelost.

Er moeten bedrijven gevoelige gegevens beveiligen tegen opkomende bedreigingen, met inbegrip van fysieke, op basis van een app en netwerk gebaseerde bedreigingen, evenals besturingssysteem beveiligingsproblemen.
Bedrijven zijn in het verleden hebben proactieve wanneer pc's beveiligen tegen een aanval, terwijl het mobiele apparaten gaan niet bewaakte en niet-beveiligde. Mobiele platforms hebt geïntegreerde beveiliging zoals app isolatie en gerenommeerde consumer app stores, maar deze platforms blijven kwetsbaar voor geavanceerde aanvallen. Vandaag de dag meer werknemers apparaten gebruiken voor het werk en toegang tot gevoelige informatie nodig. Apparaten moeten worden beschermd tegen steeds meer geavanceerde aanvallen.

## <a name="how-the-intune-mobile-threat-defense-connectors-work"></a>Hoe de Intune Mobile Threat Defense-connectors werken?

De connector beschermt bedrijfsbronnen te maken van een kanaal van communicatie tussen Intune en de leverancier van uw gekozen Mobile Threat verdediging. Intune Mobile Threat verdediging partners bieden intuïtieve, eenvoudig te implementeren van toepassingen voor mobiele apparaten die actief scannen en analyseren van informatie over de bedreiging te delen met Intune, voor een rapport of afdwinging doeleinden. Bijvoorbeeld, als een verbonden app voor Mobile Threat verdediging aan de leverancier Mobile Threat verdediging rapporteert dat een telefoon op uw netwerk momenteel is verbonden met een netwerk dat kwetsbaar voor Man in the-Middle-aanvallen is, deze informatie wordt gedeeld met en gecategoriseerd voor een juiste risiconiveau (laag/gemiddeld/hoog –) die vervolgens kan worden vergeleken met de geconfigureerde risico niveau rechten in Intune om te bepalen als toegang tot bepaalde bronnen van uw keuze worden ingetrokken wanneer het apparaat is geknoeid.

## <a name="sample-scenarios"></a>Voorbeeldscenario 's

Wanneer een apparaat wordt beschouwd als geïnfecteerd door de mobiele Threat Defense-oplossing:

![](http://i.imgur.com/Li1WUOU.png)

Wanneer het apparaat is hersteld, wordt toegang verleend:

![](http://i.imgur.com/VCIwpdz.png)

## <a name="mobile-threat-defense-partners"></a>Mobile Threat Defense-partners

Meer informatie over het beveiligen van toegang tot bedrijfsbronnen op basis van apparaat-, netwerk- en toepassing risico's met:

- [Lookout](https://docs.microsoft.com/sccm/protect/deploy-use/lookout-mobile-threat-defense-in-configuration-manager)
