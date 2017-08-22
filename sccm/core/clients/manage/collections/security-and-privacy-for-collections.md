---
title: Verzamelingen beveiliging en privacy | Microsoft Docs
description: Aanbevolen procedures voor beveiliging en privacy in verzamelingen in System Center Configuration Manager worden opgehaald.
ms.custom: na
ms.date: 2/22/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 30bf2451-5415-4be2-ba8d-21759370cd83
caps.latest.revision: "5"
caps.handback.revision: "0"
author: andredm7
ms.author: andredm
manager: angrobe
ms.openlocfilehash: 0cade975e96220e193db1de92816f97cd253532d
ms.sourcegitcommit: 51fc48fb023f1e8d995c6c4eacfda7dbec4d0b2f
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 08/07/2017
---
# <a name="security-and-privacy-for-collections-in-system-center-configuration-manager"></a>Beveiliging en privacy voor verzamelingen in System Center Configuration Manager

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*

Dit onderwerp bevat aanbevolen beveiligingsprocedures en privacy-informatie voor verzamelingen in System Center Configuration Manager.  

 Er is geen privacyinformatie voor verzamelingen in Configuration Manager. Verzamelingen zijn containers voor resources, zoals gebruikers en apparaten. Lidmaatschap van verzameling is vaak afhankelijk van de informatie die door Configuration Manager worden verzameld bij een normale werking. U kunt bijvoorbeeld op basis van met een detectie of inventarisatie verzamelde resourcegegevens een verzameling configureren om de apparaten te bevatten die voldoen aan opgegeven criteria. Verzamelingen kunnen ook worden gebaseerd op de huidige statusinformatie voor clientbeheeroperaties, zoals het implementeren van software en het controleren op naleving. Naast deze op query's gebaseerde verzamelingen kunnen gebruikers met beheerdersrechten ook resources aan verzamelingen toevoegen.  

 Zie voor meer informatie over verzamelingen [inleiding op verzamelingen in System Center Configuration Manager](../../../../core/clients/manage/collections/introduction-to-collections.md). Zie voor meer informatie over aanbevolen beveiligingsprocedures en privacy-informatie voor Configuration Manager-bewerkingen die kunnen worden gebruikt voor het configureren van het lidmaatschap van verzameling [best practices voor beveiliging en privacy-informatie voor System Center Configuration Manager](../../../../core/plan-design/security/security-best-practices-and-privacy-information.md).  

## <a name="security-best-practices-for-collections"></a>Aanbevolen procedures voor verzamelingen  
 Gebruik de volgende aanbevolen beveiligingsprocedures voor verzamelingen.  

|Aanbevolen beveiligingsprocedure|Meer informatie|  
|----------------------------|----------------------|  
|Wanneer u een verzameling in een MOF-bestand (Managed Object Format) wilt exporteren naar of importeren van een netwerklocatie, beveiligt u die locatie en het netwerkkanaal.|Hiermee beperkt u wie toegang heeft tot de netwerkmap.<br /><br /> Gebruik SBS-ondertekening (Server Message Block) of IPsec (Internet Protocol Security) tussen de netwerklocatie en de siteserver om te voorkomen dat een kwaadwillende persoon met de geëxporteerde verzamelingsgegevens kan knoeien. Gebruik IPsec om de gegevens op het netwerk te versleutelen om openbaarmaking van informatie te voorkomen.|  

### <a name="security-issues-for-collections"></a>Beveiligingsproblemen voor verzamelingen  
 Bij verzamelingen komen de volgende beveiligingsproblemen kijken:  

-   Als u verzamelingsvariabelen gebruikt, kunnen lokale beheerders potentieel gevoelige informatie lezen.  

     Verzamelingsvariabelen kunnen worden gebruikt wanneer u een besturingssysteem implementeert.  
