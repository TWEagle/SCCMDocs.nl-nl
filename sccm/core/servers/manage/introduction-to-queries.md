---
title: Inleiding in query&quot;s | Microsoft-documenten
description: "Maak en query&quot;s uitvoeren om te zoeken van objecten in een System Center Configuration Manager-hiërarchie die voldoen aan uw querycriteria."
ms.custom: na
ms.date: 10/06/2016
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 03d1b3a9-41db-4d3a-a70e-e05ab5dc8141
caps.latest.revision: 5
caps.handback.revision: 0
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 10b1010ccbf3889c58c55b87e70b354559243c90
ms.openlocfilehash: f84d518670c0ece3c08c890d2293335518f7f8e9
ms.contentlocale: nl-nl
ms.lasthandoff: 05/17/2017


---
# <a name="introduction-to-queries-in-system-center-configuration-manager"></a>Inleiding in query's in System Center Configuration Manager

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*

U kunt maken en query's uitvoeren om te zoeken van objecten in een System Center Configuration Manager-hiërarchie die voldoen aan uw querycriteria. Tot deze objecten behoren items zoals bepaalde typen computers of gebruikersgroepen. Query's kunnen de meeste typen Configuration Manager-objecten, waaronder sites, verzamelingen, toepassingen en inventarisgegevens retourneren.  

 Wanneer u een query maakt, moet u minstens twee parameters opgeven: waar u wilt zoeken en wat u wilt zoeken. Bijvoorbeeld, voor de hoeveelheid schijfruimte die beschikbaar is op alle computers in een Configuration Manager-site, u kunt een query maken om te zoeken naar de **logische schijf** kenmerk klasse en de **vrije ruimte (MB)** kenmerk voor de vrije schijfruimte.  

 Wanneer u een eerste query hebt gemaakt, kunt u aanvullende querycriteria opgeven. U kunt bijvoorbeeld opgeven dat de queryresultaten alleen computers moeten bevatten die zijn toegewezen aan een opgegeven site. U kunt ook wijzigen hoe resultaten worden weergegeven, zodat u de resultaten kunt weergeven in een voor u zinnige volgorde. U kunt bijvoorbeeld opgeven dat de resultaten in oplopende of aflopende volgorde worden gesorteerd op basis van de hoeveelheid vrije schijfruimte.  

 Wanneer u een query maken, is deze opgeslagen door Configuration Manager en weergegeven in de **query's** knooppunt in de **bewaking** werkruimte. Vanuit deze locatie kunt u een nieuwe query maken en vervolgens een bestaande query uitvoeren, bijwerken of beheren.  

 U kunt ook een query importeren in een queryregel in een Configuration Manager-verzameling. Zie voor meer informatie [het maken van verzamelingen in System Center Configuration Manager](../../../core/clients/manage/collections/create-collections.md).  

## <a name="see-also"></a>Zie ook  
 [Technische naslaginformatie voor query's voor System Center Configuration Manager](../../../core/servers/manage/queries-technical-reference.md)

