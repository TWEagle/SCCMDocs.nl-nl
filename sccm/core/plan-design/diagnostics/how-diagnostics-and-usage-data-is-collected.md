---
title: Verzamelen van diagnostische gegevens
titleSuffix: Configuration Manager
description: Meer informatie over hoe System Center Configuration Manager diagnostische gegevens en gebruiksgegevens over zichzelf verzamelt.
ms.custom: na
ms.date: 12/29/2016
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: becfa825-b19f-448c-ab82-bb929255e4ae
caps.latest.revision: "5"
author: aaroncz
ms.author: aaroncz
manager: angrobe
ms.openlocfilehash: a879bd0eba04ffef1f3c6c6ce8426c380aefc1d3
ms.sourcegitcommit: 7fe45ff75f05f7cc03ad021db8119791abe18049
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/01/2017
---
# <a name="how-diagnostics-and-usage-data-is-collected-by-system-center-configuration-manager"></a>Hoe diagnostische gegevens en gebruiksgegevens worden verzameld door System Center Configuration Manager

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*

Voor het verzamelen van diagnostische gegevens en gebruiksgegevens voor System Center Configuration Manager, voert elke primaire site SQL Server-query's op wekelijks uit te voeren. In een hiërarchie met meerdere sites worden de gegevens gerepliceerd naar de centrale beheersite.  

Deze informatie wordt op het hoogste niveau van de hiërarchie verzonden door de sitesysteemrol Serviceaansluitpunt wanneer er wordt gecontroleerd op updates. De modus van de service connection point detemines hoe de gegevens worden overgebracht:  

-   **In de onlinemodus:** Diagnostische gegevens en gebruiksgegevens worden automatisch één keer per week van het serviceverbindingspunt verwijzen naar de cloudservice verzonden.  

-   **In de offlinemodus:** Diagnostische gegevens en gebruiksgegevens worden handmatig verzonden via het hulpprogramma voor serviceverbindingen. Zie [Het hulpprogramma voor serviceverbindingen in System Center Configuration Manager gebruiken](../../../core/servers/manage/use-the-service-connection-tool.md) voor meer informatie.  

Zie [Informatie over het serviceaansluitpunt in System Center Configuration Manager](../../../core/servers/deploy/configure/about-the-service-connection-point.md) voor meer informatie.  
