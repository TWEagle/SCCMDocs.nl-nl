---
title: Software-inventaris | Microsoft Docs
description: Maak kennis met software-inventaris in System Center Configuration Manager.
ms.custom: na
ms.date: 2/22/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: configmgr-other
ms.tgt_pltfrm: na
ms.topic: get-started-article
ms.assetid: 79eb49da-cd2b-4ffc-b355-b595aeba3aea
caps.latest.revision: "5"
caps.handback.revision: "0"
author: andredm7
ms.author: andredm
manager: angrobe
ms.openlocfilehash: 969f2d28649853ddc95860fe72597d6d2c9a94e9
ms.sourcegitcommit: 51fc48fb023f1e8d995c6c4eacfda7dbec4d0b2f
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 08/07/2017
---
# <a name="introduction-to-software-inventory-in-system-center-configuration-manager"></a>Inleiding tot software-inventaris in System Center Configuration Manager

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*

Software-inventaris gebruiken voor het verzamelen van informatie over bestanden op clientapparaten. Software-inventaris kan ook bestanden bij clientapparaten verzamelen en op te slaan op de siteserver. Software-inventaris worden verzameld wanneer u ervoor kiest de **software-inventaris inschakelen op clients** instellen in de clientinstellingen, waarin u kunt ook plannen de bewerking.  

Nadat de software-inventarisatie is ingeschakeld en de clients een software-inventarisatiefase uitvoert, verzendt de client de informatie naar een beheerpunt in de site van de client. Het beheerpunt stuurt vervolgens de informatie over de inventaris naar de siteserver van Configuration Manager, die de gegevens in de sitedatabase opslaat.   

 Hier volgen manieren om de software-inventarisatiegegevens weer te geven:  

-   [Query's maken](../../../../core/servers/manage/queries-technical-reference.md) die apparaten retourneren met de opgegeven bestanden.   

-   Maak [query's gebaseerde verzamelingen](../../../../core/clients/manage/collections/introduction-to-collections.md) die apparaten met de opgegeven bestanden bevatten.   

-   [Rapporten uitvoeren](../../../../core/servers/manage/reporting.md) die vindt u informatie over bestanden op apparaten.

-   Gebruik [Resource Explorer](../../../../core/clients/manage/inventory/use-resource-explorer-to-view-software-inventory.md) om gedetailleerde informatie over de bestanden die zijn geïnventariseerd en verzameld van clientapparaten.   

 Wanneer software-inventaris op een clientapparaat wordt uitgevoerd, is het eerste rapport een volledige inventarisatie. Daaropvolgende rapporten bevatten alleen gewijzigde inventarisgegevens. De siteserver verwerkt delta-gegevens in de volgorde ontvangen. Als delta-informatie voor een client ontbreekt, wordt de siteserver afgewezen verdere gegevens over gewijzigde en instrueert de client een volledige inventarisatie uitvoeren.  

 Configuration Manager kan dual-boot-computers detecteren maar retourneert alleen inventarisatiegegevens van het besturingssysteem dat op het moment van de inventarisatie actief was.  

**Mobiele apparaten:** Zie [software-inventaris voor mobiele apparaten die zijn ingeschreven bij Microsoft Intune](../../../../mdm/deploy-use/software-inventory-mobile-devices.md) voor meer informatie over het verzamelen van inventarisgegevens voor geïnstalleerde apps op mobiele apparaten.
