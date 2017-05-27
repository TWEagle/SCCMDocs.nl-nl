---
title: Diagnostische en gebruiksgegevens | Microsoft-documenten
description: Meer informatie over de diagnostics- en gebruiksgegevens die door System Center Configuration Manager worden verzameld over zelf.
ms.custom: na
ms.date: 3/27/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 88ac4e55-d47b-4c94-b9c3-704c6a48b845
caps.latest.revision: 9
caps.handback.revision: 0
author: Brenduns
ms.author: brenduns
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: dab5da5a4b5dfb3606a8a6bd0c70a0b21923fff9
ms.openlocfilehash: 4a4b7c9c0d40b6bd3ea2f318e37d744f1a0cc084
ms.contentlocale: nl-nl
ms.lasthandoff: 05/17/2017


---
# <a name="diagnostics-and-usage-data-for-system-center-configuration-manager"></a>Diagnostische gegevens en gebruiksgegevens voor System Center Configuration Manager

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*

System Center Configuration Manager verzamelt informatie over diagnostische en gebruiksgegevens over zelf, die door Microsoft wordt gebruikt voor het verbeteren van de installatie-ervaring, kwaliteit en beveiliging van toekomstige releases.  

 Diagnostische en gebruiksgegevens is ingeschakeld voor elke System Center Configuration Manager-hiërarchie. Het bestaat uit SQL Server-query's die worden uitgevoerd op een wekelijks uit te voeren op elke primaire site en op de centrale beheersite. Als de hiërarchie een centrale beheersite gebruikt, worden de gegevens vervolgens vanaf de primaire sites gerepliceerd naar die site. De service connection point verzendt deze gegevens op de site op het hoogste niveau van uw hiërarchie wanneer er wordt gecontroleerd op updates. Als het serviceverbindingspunt zich in de offlinemodus bevindt, wordt de informatie overgedragen met het hulpprogramma voor serviceverbindingen.  

> [!NOTE]  
>  Configuration Manager verzamelt gegevens van SQL server-database van de site alleen en verzamelt geen gegevens rechtstreeks van clients of siteservers.  

 Zie voor meer informatie de [privacyverklaring voor System Center Configuration Manager](http://go.microsoft.com/fwlink/?LinkID=626527).  

 Meer informatie over diagnostische en gebruiksgegevens voor System Center Configuration Manager in de volgende artikelen:  

-   [Hoe diagnostische en gebruiksgegevens voor System Center Configuration Manager worden gebruikt](../../../core/plan-design/diagnostics/how-diagnostics-and-usage-data-is-used.md)  

-   Niveaus van diagnostische gebruiksgegevens verzamelen:
    - [Diagnostische gegevens voor 1702](/sccm/core/plan-design/diagnostics/levels-of-diagnostic-usage-data-collection-1702)      
    - [Diagnostische gegevens voor 1610](/sccm/core/plan-design/diagnostics/levels-of-diagnostic-usage-data-collection-1610)  
    - [Diagnostische gegevens voor 1606](/sccm/core/plan-design/diagnostics/levels-of-diagnostic-usage-data-collection-1606)    

<!--
    - [Diagnostic data for 1602](/sccm/core/plan-design/diagnostics/levels-of-diagnostic-usage-data-collection-1602)
    - [Diagnostic data for  1511](/sccm/core/plan-design/diagnostics/levels-of-diagnostic-usage-data-collection-1511)
-->

-   [Hoe diagnostische en gebruiksgegevens door System Center Configuration Manager worden verzameld](../../../core/plan-design/diagnostics/how-diagnostics-and-usage-data-is-collected.md)  

-   [Diagnostische en gebruiksgegevens weergeven voor System Center Configuration Manager](../../../core/plan-design/diagnostics/view-diagnostics-and-usage-data.md)  

-   [Programma voor kwaliteitsverbetering (CEIP) voor System Center Configuration Manager](../../../core/plan-design/diagnostics/customer-experience-improvement-program-ceip.md)  

-   [Veelgestelde vragen over diagnostische en gebruiksgegevens voor System Center Configuration Manager](../../../core/understand/frequently-asked-questions-about-diagnostics-and-usage-data.md)  

## <a name="see-also"></a>Zie ook  
 [Over de service connection point in System Center Configuration Manager](../../../core/servers/deploy/configure/about-the-service-connection-point.md)

