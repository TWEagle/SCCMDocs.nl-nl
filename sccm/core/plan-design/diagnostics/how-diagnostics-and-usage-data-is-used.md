---
title: Gebruik van diagnostische gegevens
titleSuffix: Configuration Manager
description: Meer informatie over hoe Microsoft gebruikt de diagnostische gegevens en gebruiksgegevens die door System Center Configuration Manager worden verzameld.
ms.custom: na
ms.date: 12/29/2016
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: a8021bc8-2799-41f4-83c2-e27d1242028c
caps.latest.revision: "5"
author: Brenduns
ms.author: brenduns
manager: angrobe
ms.openlocfilehash: e6395421e88baf822bc0a8971119b6fe360e6680
ms.sourcegitcommit: c236214b2fcc13dae7bad96d7fb33f692868191d
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/12/2017
---
# <a name="how-diagnostics-and-usage-data-is-used-for-system-center-configuration-manager"></a>Hoe diagnostische gegevens en gebruiksgegevens worden gebruikt voor System Center Configuration

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*

Diagnostische gegevens en gebruiksgegevens die door System Center Configuration Manager worden verzameld bieden Microsoft vrijwel onmiddellijk feedback over hoe het product werkt en wordt gebruikt om toekomstige updates. We kunnen ook de configuratiegegevens zien, zodat we de configuraties die in productie zijn, kunnen samenstellen en testen. Bijvoorbeeld:  

-   De Windows-serverversies die worden gebruikt door siteservers  

-   De geïnstalleerde taalpakketten  

-   De verschillen van het SQL-schema ten opzichte van de productstandaard  

Met behulp van deze gegevens kan het engineeringteam toekomstige tests plannen en zorgen voor de beste ervaring bij het gebruik van de meest voorkomende configuraties. Als updates voor Configuration Manager zijn beschikbaar op een snellere uitgebracht (voor betere ondersteuning van snel veranderende technologieën zoals Windows 10 en Microsoft Intune), is deze gegevens essentieel om snel aanpassingen te passen.  

Even belangrijk is hoe de diagnostische gegevens en gebruiksgegevens worden niet gebruikt. Microsoft gebruikt deze gegevens niet voor:  

-   Licentiecontroles, bijvoorbeeld het vergelijken van het gebruik van de klant met de licentieovereenkomsten  

-   Controle van producten die niet worden ondersteund  

-   Advertenties op basis van beschikbare gegevens, zoals het gebruik van functies of geolocatie (tijdzone)  

##  <a name="bkmk_improve"></a>Voorbeelden van hoe diagnostische gegevens en gebruiksgegevens het product verbetert  
Microsoft gebruikt beschikbare gegevens voor het verbeteren van het product. Hieronder volgen enkele voorbeelden:  

-   **Herziene ondersteuning voor oudere serverbesturingssystemen:**  

     De eerste ondersteuning wordt aangeboden door de huidige vertakking van System Center Configuration Manager beperkt de ondersteuningstijdlijn voor Windows Server 2008 R2. Na onderzoek van de gebruiksgegevens van klanten die is bijgewerkt naar de huidige vertakking van Configuration Manager is de behoefte aan herzien en uit te breiden ter ondersteuning van klanten die nog steeds Dit serverbesturingssysteem voor host-siteservers en sitesysteemrollen gebruik van deze tijdlijn geïdentificeerd.  

-   **Verbeterde controles van vereisten:**  

     Op basis van de gebruiksgegevens, hebben we de controles van vereisten voor het installeren van een update voor het verwijderen van verouderde regels, account voor aanvullende aanvragen en, in sommige gevallen, voor het automatisch oplossen van problemen verbeterd.  
