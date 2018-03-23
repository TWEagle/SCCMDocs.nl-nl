---
title: Diagnostische gegevens en gebruiksgegevens
titleSuffix: Configuration Manager
description: Meer informatie over de diagnostische gegevens en gebruiksgegevens die door System Center Configuration Manager worden verzameld over zichzelf.
ms.custom: na
ms.date: 03/22/2018
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 88ac4e55-d47b-4c94-b9c3-704c6a48b845
caps.latest.revision: ''
caps.handback.revision: ''
author: aczechowski
ms.author: aaroncz
manager: dougeby
ms.openlocfilehash: 5f783f11f6fbabda2fd1d6f98748e945affa878e
ms.sourcegitcommit: 11bf4ed40ed0cbb10500cc58bbecbd23c92bfe20
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 03/23/2018
---
# <a name="diagnostics-and-usage-data-for-system-center-configuration-manager"></a>Diagnostische gegevens en gebruiksgegevens voor System Center Configuration Manager

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*

Configuration Manager verzamelt diagnostische gegevens en gebruiksgegevens over zichzelf, die door Microsoft wordt gebruikt voor het verbeteren van de installatie-ervaring, kwaliteit en beveiliging van toekomstige releases.  

 Diagnostische gegevens en gebruiksgegevens is ingeschakeld voor elke Configuration Manager-hiërarchie. Bestaat uit SQL Server-query's die wekelijks worden uitgevoerd op elke primaire site en op de centrale beheersite. Als de hiërarchie een centrale beheersite gebruikt, worden de gegevens vervolgens vanaf de primaire sites gerepliceerd naar die site. Op het hoogste niveau van uw hiërarchie, het service connection point deze informatie wordt verzonden wanneer op updates wordt gecontroleerd. Als het serviceverbindingspunt zich in de offlinemodus bevindt, wordt de informatie overgedragen met het hulpprogramma voor serviceverbindingen.  

> [!NOTE]  
>  Configuration Manager verzamelt gegevens uit SQL server-database van de site alleen en verzamelt geen gegevens rechtstreeks bij clients of siteservers.  

 Zie voor meer informatie de [privacyverklaring van Microsoft](https://go.microsoft.com/fwlink/?LinkID=626527).  

## <a name="articles"></a>Artikelen
 Meer informatie over diagnostische gegevens en gebruiksgegevens voor Configuration Manager in de volgende artikelen:  

-   [Hoe diagnostische gegevens en gebruiksgegevens worden gebruikt](../../../core/plan-design/diagnostics/how-diagnostics-and-usage-data-is-used.md)  

-   Niveaus van diagnostische gebruiksgegevens verzamelen:
    - [Diagnostische gegevens voor 1802](/sccm/core/plan-design/diagnostics/levels-of-diagnostic-usage-data-collection-1802)  
    - [Diagnostische gegevens voor 1710](/sccm/core/plan-design/diagnostics/levels-of-diagnostic-usage-data-collection-1710)  
    - [Diagnostische gegevens voor 1706](/sccm/core/plan-design/diagnostics/levels-of-diagnostic-usage-data-collection-1706)    

<!--
    - [Diagnostic data for 1702](/sccm/core/plan-design/diagnostics/levels-of-diagnostic-usage-data-collection-1702)      
    - [Diagnostic data for 1610](/sccm/core/plan-design/diagnostics/levels-of-diagnostic-usage-data-collection-1610)  
    - [Diagnostic data for  1606](/sccm/core/plan-design/diagnostics/levels-of-diagnostic-usage-data-collection-1606)    
    - [Diagnostic data for 1602](/sccm/core/plan-design/diagnostics/levels-of-diagnostic-usage-data-collection-1602)
    - [Diagnostic data for  1511](/sccm/core/plan-design/diagnostics/levels-of-diagnostic-usage-data-collection-1511)
-->

-   [Hoe diagnostische gegevens en gebruiksgegevens worden verzameld](../../../core/plan-design/diagnostics/how-diagnostics-and-usage-data-is-collected.md)  

-   [Diagnostische gegevens en gebruiksgegevens weergeven](../../../core/plan-design/diagnostics/view-diagnostics-and-usage-data.md)  

-   [Programma voor verbetering van de gebruikerservaring (CEIP)](../../../core/plan-design/diagnostics/customer-experience-improvement-program-ceip.md)  

     > [!Note]  
     > Starten van de functie programma voor Kwaliteitsverbetering in Configuration Manager versie 1802 is verwijderd uit het product.


-   [Veelgestelde vragen over diagnostische gegevens en gebruiksgegevens](../../../core/understand/frequently-asked-questions-about-diagnostics-and-usage-data.md)  

## <a name="see-also"></a>Zie ook  
 [Het serviceverbindingspunt](../../../core/servers/deploy/configure/about-the-service-connection-point.md)
