---
title: Beperken van toegang op basis van risico
titleSuffix: Configuration Manager
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
ms.openlocfilehash: e013c2a3758685aacdacf0707ca0df2c258976b2
ms.sourcegitcommit: c236214b2fcc13dae7bad96d7fb33f692868191d
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/12/2017
---
# <a name="manage-access-to-company-resource-based-on-device-network-and-application-risk"></a>Toegang tot bedrijfsbronnen op basis van apparaat-, netwerk- en toepassing risico's beheren

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*

Mobile Threat verdediging connectors kunnen u gebruikmaken van de leverancier van uw gekozen Mobile Threat verdediging als een bron van informatie voor uw nalevingsbeleid en de regels voor voorwaardelijke toegang. Dit kunnen IT-beheerders een beschermingslaag toevoegen aan hun bedrijfsbronnen zoals Exchange en Sharepoint, speciaal van verdacht mobiele apparaten.

## <a name="what-problem-does-this-solve"></a>Welk probleem opgelost.

Er moeten bedrijven gevoelige gegevens beveiligen tegen opkomende bedreigingen, met inbegrip van fysieke, op basis van een app en netwerk gebaseerde bedreigingen, evenals besturingssysteem beveiligingsproblemen.
Bedrijven zijn in het verleden hebben proactieve wanneer pc's beveiligen tegen een aanval, terwijl het mobiele apparaten gaan niet bewaakte en niet-beveiligde. Mobiele platforms hebt geïntegreerde beveiliging zoals app isolatie en gerenommeerde consumer app stores, maar deze platforms blijven kwetsbaar voor geavanceerde aanvallen. Vandaag de dag meer werknemers apparaten gebruiken voor het werk en toegang tot gevoelige informatie nodig. Apparaten moeten worden beschermd tegen steeds meer geavanceerde aanvallen.

De [hybride MDM-implementatie (SCCM met Intune)](https://docs.microsoft.com/sccm/mdm/understand/choose-between-standalone-intune-and-hybrid-mobile-device-management) biedt u de mogelijkheid de toegang tot bedrijfsbronnen en gegevens op basis van de risico-evaluatie apparaat threat protection oplossingen zoals Mobile Threat verdediging partners bieden.

## <a name="how-the-intune-mobile-threat-defense-connectors-work"></a>Hoe de Intune Mobile Threat Defense-connectors werken?

De connector beschermt bedrijfsbronnen te maken van een kanaal van communicatie tussen Intune en de leverancier van uw gekozen Mobile Threat verdediging. Intune Mobile Threat verdediging partners bieden intuïtieve, eenvoudig te implementeren van toepassingen voor mobiele apparaten die actief scannen en analyseren van informatie over de bedreiging te delen met Intune, voor een rapport of afdwinging doeleinden. Bijvoorbeeld, als een verbonden app voor Mobile Threat verdediging aan de leverancier Mobile Threat verdediging rapporteert dat een telefoon op uw netwerk momenteel is verbonden met een netwerk dat kwetsbaar voor Man in the-Middle-aanvallen is, deze informatie wordt gedeeld met en gecategoriseerd voor een juiste risiconiveau (laag/gemiddeld/hoog –) die vervolgens kan worden vergeleken met de geconfigureerde risico niveau rechten in Intune om te bepalen als toegang tot bepaalde bronnen van uw keuze worden ingetrokken wanneer het apparaat is geknoeid.

## <a name="sample-scenarios"></a>Voorbeeldscenario 's

Wanneer een apparaat wordt beschouwd als geïnfecteerd door de mobiele Threat Defense-oplossing:

![Mobile Threat verdediging geïnfecteerde apparaten](../media/mtp/MTD-image-1.png)

Wanneer het apparaat is hersteld, wordt toegang verleend:

![Mobile Threat verdediging toegang verleend](../media/mtp/MTD-image-2.png)

## <a name="next-steps"></a>Volgende stappen

Meer informatie over het beveiligen van toegang tot bedrijfsbronnen op basis van apparaat-, netwerk- en toepassing risico's met:

- [Lookout](https://docs.microsoft.com/intune/deploy-use/lookout-mobile-threat-defense-connector)