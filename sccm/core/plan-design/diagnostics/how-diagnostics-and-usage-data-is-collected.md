---
title: Verzamelen van diagnostische gegevens | Microsoft-documenten
description: Meer informatie over hoe System Center Configuration Manager diagnostische en gebruiksgegevens over zelf verzamelt.
ms.custom: na
ms.date: 12/29/2016
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: becfa825-b19f-448c-ab82-bb929255e4ae
caps.latest.revision: 5
author: Brenduns
ms.author: brenduns
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 24a233516058e645df2a43623855665b97b041b0
ms.openlocfilehash: 9c0165212fe34f460be2ce870d0542b616f3bc4d
ms.contentlocale: nl-nl
ms.lasthandoff: 05/17/2017


---
# <a name="how-diagnostics-and-usage-data-is-collected-by-system-center-configuration-manager"></a>Hoe diagnostische gegevens en gebruiksgegevens worden verzameld door System Center Configuration Manager

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*

Elke primaire site wordt voor het verzamelen van diagnostische en gebruiksgegevens voor System Center Configuration Manager, SQL Server-query's uitgevoerd op wekelijks uit te voeren. In een hiërarchie met meerdere sites worden de gegevens gerepliceerd naar de centrale beheersite.  

Deze informatie wordt op het hoogste niveau van de hiërarchie verzonden door de sitesysteemrol Serviceaansluitpunt wanneer er wordt gecontroleerd op updates. De modus van de service connection point detemines hoe de gegevens worden overgebracht:  

-   **In de onlinemodus:** Diagnostische en gebruiksgegevens wordt automatisch verzonden als een week van de serviceverbinding gaat u naar de cloudservice.  

-   **In de offline modus:** Diagnostische en gebruiksgegevens overgedragen handmatig met behulp van het hulpprogramma voor service-verbinding. Zie [Het hulpprogramma voor serviceverbindingen in System Center Configuration Manager gebruiken](../../../core/servers/manage/use-the-service-connection-tool.md) voor meer informatie.  

Zie [Informatie over het serviceaansluitpunt in System Center Configuration Manager](../../../core/servers/deploy/configure/about-the-service-connection-point.md) voor meer informatie.  

