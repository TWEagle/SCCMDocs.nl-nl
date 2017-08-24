---
title: Beveiliging en privacy voor query's | Microsoft Docs
description: Best practices voor beveiliging en privacy begrijpen als u een query voor gegevens uit de sitedatabase.
ms.custom: na
ms.date: 10/06/2016
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 30080620-20d3-4c38-b8dd-db5516e1acae
caps.latest.revision: "5"
caps.handback.revision: "0"
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.openlocfilehash: e42b13c68ecaeac94245838c2f42e2790799de2b
ms.sourcegitcommit: 51fc48fb023f1e8d995c6c4eacfda7dbec4d0b2f
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 08/07/2017
---
# <a name="security-and-privacy-for-queries-in-system-center-configuration-manager"></a>Beveiliging en privacy voor query's in System Center Configuration Manager

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*

Query's in System Center Configuration Manager kunnen u gegevens ophalen uit de sitedatabase op basis van de criteria die u opgeeft. Configuration Manager verzamelt de sitedatabasegegevens bij een normale werking. U kunt bijvoorbeeld op basis van met een detectie of inventarisatie verzamelde gegevens een query configureren om apparaten te identificeren die voldoen aan opgegeven criteria.  

 Zie voor meer informatie over query's [inleiding op query's in System Center Configuration Manager](../../../core/servers/manage/introduction-to-queries.md). Zie voor meer informatie over aanbevolen beveiligingsprocedures en privacy-informatie voor Configuration Manager-bewerkingen die de gegevens die u ophalen kunt met behulp van query's verzamelen, [beveiliging en privacy voor System Center Configuration Manager](../../../core/plan-design/security/security-and-privacy.md).  

## <a name="security-best-practices-for-queries"></a>Aanbevolen beveiligingsprocedures voor query’s  
 Gebruik de volgende aanbevolen beveiligingsprocedures voor query’s.  

|Aanbevolen beveiligingsprocedure|Meer informatie|  
|----------------------------|----------------------|  
|Wanneer u exporteert of importeert van een query die wordt opgeslagen naar een netwerklocatie, Beveilig de locatie en het netwerkkanaal.|Beperk wie toegang heeft tot de netwerkmap.<br /><br /> Gebruik SBS-ondertekening (Server Message Block) of IPsec (Internet Protocol Security) tussen de netwerklocatie en de siteserver om te voorkomen dat een kwaadwillende persoon met de querygegevens kan knoeien voordat deze worden geïmporteerd.|  

## <a name="see-also"></a>Zie tevens  
 [Technische naslaginformatie voor query's voor System Center Configuration Manager](../../../core/servers/manage/queries-technical-reference.md)
