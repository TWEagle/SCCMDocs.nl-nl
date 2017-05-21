---
title: Updates Publisher | Microsoft-documenten
description: System Center Updates Publisher gebruiken voor het beheren van aangepaste updates
ms.custom: na
ms.date: 4/29/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 2200b02b-e76b-4aa7-a77a-6dc5e70f1333
caps.latest.revision: 1
author: Brenduns
ms.author: brenduns
manager: angrobe
robots: NOINDEX, NOFOLLOW
ms.translationtype: Machine Translation
ms.sourcegitcommit: 31819a1df4e63e1114682490a9b3c3b4e5c99cfa
ms.openlocfilehash: f4951c204b32da58174b94a539b380c278fa9756
ms.contentlocale: nl-nl
ms.lasthandoff: 05/17/2017

---
# <a name="system-center-updates-publisher"></a>System Center Updates Publisher

*Van toepassing op: System Center Updates Publisher*

System Center Updates Publisher (Updates Publisher) is een zelfstandig hulpprogramma dat wordt onafhankelijke softwareleveranciers of toepassingsontwikkelaars van LOB-voor het beheren van aangepaste updates ingeschakeld. Dit omvat updates die afhankelijkheden, zoals stuurprogramma's en updatebundels hebben.

Met Updates Publisher, kunt u het volgende doen:

-   Updates hebt geïmporteerd uit externe catalogussen (niet-Microsoft update-catalogus).
-   Inclusief toepasselijkheid en metagegevens voor de implementatie-updatedefinities wijzigen.
-   Updates exporteren naar externe catalogussen.
-   Updates publiceren naar een updateserver.

Nadat u de updates naar een updateserver publiceren, kunt u vervolgens System Center Configuration Manager gebruiken om te detecteren en implementeren die updates op uw beheerde apparaten.

> [!TIP]  
> De vorige versie [System Center Updates Publisher 2011](http://go.microsoft.com/fwlink/?LinkId=848111), blijft in de ondersteuning. Deze bijgewerkte versie behoudt dezelfde functionaliteit, maar biedt ondersteuning voor andere besturingssystemen, nieuwe functies vereenvoudigen sommige taken, en heeft een bijgewerkte gebruikersinterface.

## <a name="workspaces"></a>Werkruimten
Wanneer u Updates Publisher opent, wordt de standaardwaarde aan het knooppunt overzicht van de *werkruimte Updates.*

![Updates Publisher-console](media/console1.png)   


Updates Publisher heeft vier werkruimten kunt ordenen.


**De werkruimte updates:** Gebruik deze werkruimte [maken](/sccm/sum/tools/create-updates-with-updates-publisher) en [beheren](/sccm/sum/tools/manage-updates-with-updates-publisher) software-updates en updatebundels. Dit omvat updates toe te wijzen en op een publicatie, publiceren en exporteren naar een andere Updates Publisher opslagplaats verzamelt.

**Publicaties-werkruimte:** Dit is wanneer u [publicaties beheren](/sccm/sum/tools/updates-publisher-publications). Een publicatie is de groep van updates die u maakt om de uitvoer en publiceren van de updates te vereenvoudigen.

Publicaties beheren bevat publishing updates voor een server, zodat uw clients kunnen zoeken en installeren, updates en bundels voor gebruik door andere installaties van Updates Publisher exporteren of het wijzigen van de inhoud van of de details van een publicatie.



**Regels-werkruimte:** Hier is wanneer u [regels voor toepasselijkheid beheren](/sccm/sum/tools/updates-publisher-applicability-rules) die kunnen worden opgeslagen en wordt gebruikt met updates die u implementeert. Er zijn twee soorten regels:

-   Installeerbare regels – deze regels te helpen bepalen hoe als een client een update moet installeren.
-   De geïnstalleerde regels – deze regels controleren of er al een update is geïnstalleerd.

**Werkruimte catalogussen worden geïmporteerd:** Deze werkruimte gebruiken om toe te voegen en [software update-catalogussen beheren](/sccm/sum/tools/updates-publisher-catalogs). Dit omvat het importeren van software-updates vanaf deze catalogussen worden geïmporteerd met de opslagplaats Updates Publisher.
## <a name="first-steps"></a>Eerste stappen
Aan de slag, eerst [installeren](/sccm/sum/tools/install-updates-publisher), en vervolgens [opties configureren](/sccm/sum/tools/updates-publisher-options) voor Updates Publisher.

