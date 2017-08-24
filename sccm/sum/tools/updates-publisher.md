---
title: Updates Publisher | Microsoft Docs
description: System Center Updates Publisher gebruiken voor het beheren van aangepaste updates
ms.custom: na
ms.date: 4/29/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 2200b02b-e76b-4aa7-a77a-6dc5e70f1333
caps.latest.revision: "1"
author: Brenduns
ms.author: brenduns
manager: angrobe
robots: NOINDEX, NOFOLLOW
ms.openlocfilehash: f4951c204b32da58174b94a539b380c278fa9756
ms.sourcegitcommit: 51fc48fb023f1e8d995c6c4eacfda7dbec4d0b2f
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 08/07/2017
---
# <a name="system-center-updates-publisher"></a>System Center Updates Publisher

*Van toepassing op: System Center Updates Publisher*

System Center Updates Publisher (Updates Publisher) is een zelfstandig hulpprogramma dat kan onafhankelijke softwareleveranciers of line-of-business-toepassingsontwikkelaars om aangepaste updates te beheren. Dit omvat de updates die afhankelijkheden, zoals stuurprogramma's en updatebundels hebben.

Met Updates Publisher, kunt u het volgende doen:

-   Updates importeren uit externe catalogi (niet-Microsoft update-catalogus).
-   Updatedefinities inclusief toepasselijkheid en de metagegevens voor de implementatie wijzigen.
-   Updates naar externe catalogi exporteren.
-   Updates aan een updateserver publiceren.

Nadat u updates naar een updateserver publiceert, kunt u vervolgens System Center Configuration Manager gebruiken om te detecteren en implementeren die updates op uw beheerde apparaten.

> [!TIP]  
> De vorige versie [System Center Updates Publisher 2011](http://go.microsoft.com/fwlink/?LinkId=848111), blijft in de ondersteuning. Deze bijgewerkte versie behoudt dezelfde functionaliteit, maar biedt ondersteuning voor aanvullende besturingssystemen, nieuwe functies voor het vereenvoudigen van sommige taken, en heeft een bijgewerkte gebruiker-interface.

## <a name="workspaces"></a>Werkruimten
Wanneer u Updates Publisher opent, wordt standaard naar het knooppunt overzicht van de *werkruimte Updates.*

![Updates Publisher-console](media/console1.png)   


Updates Publisher heeft vier werkruimten om te ordenen.


**De werkruimte updates:** Gebruik deze werkruimte naar [maken](/sccm/sum/tools/create-updates-with-updates-publisher) en [beheren](/sccm/sum/tools/manage-updates-with-updates-publisher) software-updates en updatebundels. Dit omvat updates toe te wijzen en verzamelt voor een publicatie, publiceren en te exporteren naar een andere Updates Publisher-opslagplaats.

**Publicaties-werkruimte:** Dit is wanneer u [publicaties beheren](/sccm/sum/tools/updates-publisher-publications). Een publicatie is de groep van updates die u maakt om de uitvoer en publiceren van de updates te vereenvoudigen.

Het beheren van publicaties bevat publishing updates naar een server zodat uw clients kunnen vinden en installeren, updates en bundels voor gebruik door andere installaties van Updates Publisher exporteren of het wijzigen van de inhoud van of de details van een publicatie.



**Regels-werkruimte:** Hier is wanneer u [regels voor toepasselijkheid beheren](/sccm/sum/tools/updates-publisher-applicability-rules) die kunnen worden opgeslagen en vervolgens worden gebruikt met updates die u implementeert. Er zijn twee typen regels:

-   Installeerbare regels – deze regels kunnen u bepalen als een client moet een update installeren.
-   De geïnstalleerde regels – deze regels controleren of een update al is geïnstalleerd.

**Catalogussen-werkruimte:** Gebruik deze werkruimte om toe te voegen en [software-update-catalogussen beheren](/sccm/sum/tools/updates-publisher-catalogs). Dit omvat het importeren van software-updates uit die catalogi naar de opslagplaats voor Updates Publisher.
## <a name="first-steps"></a>Eerste stappen
Aan de slag eerst [installeren](/sccm/sum/tools/install-updates-publisher), en vervolgens [opties configureren](/sccm/sum/tools/updates-publisher-options) voor Updates Publisher.
