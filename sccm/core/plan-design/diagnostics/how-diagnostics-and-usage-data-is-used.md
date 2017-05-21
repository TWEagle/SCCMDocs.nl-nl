---
title: Gebruik van diagnostische gegevens | Microsoft-documenten
description: Meer informatie over hoe Microsoft gebruikt de diagnostics- en gebruiksgegevens die door System Center Configuration Manager worden verzameld.
ms.custom: na
ms.date: 12/29/2016
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: a8021bc8-2799-41f4-83c2-e27d1242028c
caps.latest.revision: 5
author: Brenduns
ms.author: brenduns
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 24a233516058e645df2a43623855665b97b041b0
ms.openlocfilehash: 9864f6ba7b9a2211c99b1a5d9ebd582e01ccfeb6
ms.contentlocale: nl-nl
ms.lasthandoff: 05/17/2017


---
# <a name="how-diagnostics-and-usage-data-is-used-for-system-center-configuration-manager"></a>Hoe diagnostische gegevens en gebruiksgegevens worden gebruikt voor System Center Configuration

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*

Diagnostische en gebruiksgegevens gegevens die door System Center Configuration Manager worden verzameld biedt Microsoft vrijwel onmiddellijk feedback over hoe het product werkt en wordt gebruikt om toekomstige updates aan te passen. We kunnen ook de configuratiegegevens zien, zodat we de configuraties die in productie zijn, kunnen samenstellen en testen. Bijvoorbeeld:  

-   De Windows-serverversies die worden gebruikt door siteservers  

-   De geïnstalleerde taalpakketten  

-   De verschillen van het SQL-schema ten opzichte van de productstandaard  

Met behulp van deze gegevens kan het engineeringteam toekomstige tests plannen en zorgen voor de beste ervaring bij het gebruik van de meest voorkomende configuraties. Als updates voor Configuration Manager zijn uitgebracht op een snellere rekenen (voor betere ondersteuning snel verplaatsen van technologieën zoals Windows 10 en Microsoft Intune), zijn deze gegevens zijn cruciaal snel aanpassen en aan te passen.  

Net zo belangrijk is hoe de gegevens van diagnoses en gebruik niet wordt gebruikt. Microsoft gebruikt deze gegevens niet voor:  

-   Licentiecontroles, bijvoorbeeld het vergelijken van het gebruik van de klant met de licentieovereenkomsten  

-   Controle van producten die niet worden ondersteund  

-   Advertenties op basis van beschikbare gegevens zoals het gebruik van de functie of geolocatie (tijdzone)  

##  <a name="bkmk_improve"></a>Voorbeelden van hoe diagnostische en gebruiksgegevens het product verbetert  
Microsoft gebruikt beschikbare gegevens voor het verbeteren van het product. Hier volgen enkele voorbeelden:  

-   **Herziene ondersteuning voor oudere serverbesturingssystemen:**  

     De eerste ondersteuning geboden door de huidige vertakking van System Center Configuration Manager beperkt de tijdlijn ondersteuning voor Windows Server 2008 R2. Na onderzoek van de gebruiksgegevens van klanten die een upgrade heeft uitgevoerd naar de huidige vertakking van de Configuration Manager geïdentificeerd we moet herzien en deze tijdlijn ter ondersteuning van klanten die nog steeds gebruik van deze server-besturingssysteem op de site-host-servers en sitesysteemrollen uit te breiden.  

-   **Verbeterde controles van vereisten:**  

     Op basis van de gebruiksgegevens, hebben we de controles van vereisten voor het installeren van een update voor het verwijderen van verouderde regels, voor extra gevallen en in sommige gevallen kan een aantal problemen automatisch oplossen verbeterd.  

