---
title: Aanbevolen procedures voor rapportage | Microsoft Docs
description: Lees enkele nuttige tips over het gebruik van de rapportagemogelijkheid van System Center Configuration Manager.
ms.custom: na
ms.date: 10/06/2016
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: configmgr-other
ms.tgt_pltfrm: na
ms.topic: get-started-article
ms.assetid: 64f9d931-33f1-456f-a4e4-0ec077465bd0
caps.latest.revision: "4"
caps.handback.revision: "0"
author: Dougeby
ms.author: dougeby
manager: angrobe
ms.openlocfilehash: 759258999f3eaa810803a6a7f856f00fe7771a9e
ms.sourcegitcommit: 51fc48fb023f1e8d995c6c4eacfda7dbec4d0b2f
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 08/07/2017
---
# <a name="best-practices-for-reporting-in-system-center-configuration-manager"></a>Aanbevolen procedures voor rapportage in System Center Configuration Manager

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*

Gebruik de volgende aanbevolen procedures voor rapportage in System Center Configuration Manager:  

## <a name="for-best-performance-install-the-reporting-services-point-on-a-remote-site-system-server"></a>Installeer het Reporting Services-punt op een externe sitesysteemserver voor de beste prestaties  
 Hoewel u het Reporting Services-punt op een siteserver of extern sitesysteem kunt installeren, worden de prestaties beter als u het Reporting Services-punt op een externe sitesysteemserver installeert.  

## <a name="optimize-sql-server-reporting-services-queries"></a>Reporting Services-query's van SQL Server optimaliseren  
 Doorgaans treden vertragingen in rapportage op vanwege de tijd die het kost om query's uit te voeren en de resultaten te krijgen. Wanneer u Microsoft SQL Server gebruikt, kunt met behulp van hulpprogramma's zoals Query Analyzer en Profiler query's optimaliseren.  

## <a name="schedule-report-subscription-processing-to-run-outside-standard-office-hours"></a>Plan de verwerking van het rapportabonnement zo, dat deze buiten de standaardkantooruren wordt uitgevoerd  
 Waar mogelijk, plant u de verwerking van het rapportabonnement om uit te voeren buiten standaardkantooruren om te beperken van de CPU-verwerking op de Configuration Manager-Sitedatabaseserver. Deze aanbevolen procedure verbetert tevens de beschikbaarheid voor onverwachte rapportaanvragen.  

## <a name="next-steps"></a>Volgende stappen
[Rapportage configureren](configuring-reporting.md)
