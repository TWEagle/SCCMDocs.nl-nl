---
title: Beveiliging en privacy voor query&quot;s | Microsoft-documenten
description: Aanbevolen procedures voor beveiliging en privacy kennen wanneer u een query voor de informatie uit de sitedatabase.
ms.custom: na
ms.date: 10/06/2016
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 30080620-20d3-4c38-b8dd-db5516e1acae
caps.latest.revision: 5
caps.handback.revision: 0
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 10b1010ccbf3889c58c55b87e70b354559243c90
ms.openlocfilehash: 09f7bdaa29a01fb2a38aa223db56b5bce3bc5205
ms.contentlocale: nl-nl
ms.lasthandoff: 05/17/2017


---
# <a name="security-and-privacy-for-queries-in-system-center-configuration-manager"></a>Beveiliging en privacy voor query's in System Center Configuration Manager

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*

Query's in System Center Configuration Manager kunnen u gegevens ophalen uit de sitedatabase op basis van criteria die u opgeeft. Configuration Manager worden verzameld van de sitedatabase-informatie bij een normale werking. U kunt bijvoorbeeld op basis van met een detectie of inventarisatie verzamelde gegevens een query configureren om apparaten te identificeren die voldoen aan opgegeven criteria.  

 Zie voor meer informatie over query's [Inleiding in query's in System Center Configuration Manager](../../../core/servers/manage/introduction-to-queries.md). Zie voor meer informatie over aanbevolen beveiligingsprocedures en privacy-informatie voor Configuration Manager-bewerkingen die de informatie die u ophalen kunt met behulp van query's verzamelen [beveiliging en privacy voor System Center Configuration Manager](../../../core/plan-design/security/security-and-privacy.md).  

## <a name="security-best-practices-for-queries"></a>Aanbevolen beveiligingsprocedures voor query’s  
 Gebruik de volgende aanbevolen beveiligingsprocedures voor query’s.  

|Aanbevolen beveiligingsprocedure|Meer informatie|  
|----------------------------|----------------------|  
|Wanneer u een query wilt exporteren naar of importeren van een netwerklocatie, beveiligt u die locatie en het netwerkkanaal.|Beperk wie toegang heeft tot de netwerkmap.<br /><br /> Gebruik SBS-ondertekening (Server Message Block) of IPsec (Internet Protocol Security) tussen de netwerklocatie en de siteserver om te voorkomen dat een kwaadwillende persoon met de querygegevens kan knoeien voordat deze worden geïmporteerd.|  

## <a name="see-also"></a>Zie ook  
 [Technische naslaginformatie voor query's voor System Center Configuration Manager](../../../core/servers/manage/queries-technical-reference.md)

