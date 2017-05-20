---
title: Software-inventaris | Microsoft-documenten
description: Kennismaking met software-inventaris in System Center Configuration Manager.
ms.custom: na
ms.date: 2/22/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: get-started-article
ms.assetid: 79eb49da-cd2b-4ffc-b355-b595aeba3aea
caps.latest.revision: 5
caps.handback.revision: 0
author: andredm7
ms.author: andredm
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: f9097014c7e988ec8e139e518355c4efb19172b3
ms.openlocfilehash: 969f2d28649853ddc95860fe72597d6d2c9a94e9
ms.contentlocale: nl-nl
ms.lasthandoff: 05/17/2017


---
# <a name="introduction-to-software-inventory-in-system-center-configuration-manager"></a>Inleiding tot software-inventaris in System Center Configuration Manager

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*

Software-inventaris gebruiken voor het verzamelen van informatie over de bestanden op clientapparaten. Software-inventaris kan ook bestanden worden verzameld van clientapparaten en op te slaan op de siteserver. Software-inventaris wordt verzameld wanneer u ervoor kiest de **software-inventaris inschakelen op clients** stellen in de clientinstellingen, waarin u kunt ook plannen het opnieuw.  

Nadat de software-inventarisatie is ingeschakeld en de clients een software-inventarisatiefase uitvoert, verzendt de client de informatie naar een beheerpunt in de site van de client. Het beheerpunt stuurt vervolgens de Inventarisinformatie naar de siteserver van Configuration Manager, die de informatie in de sitedatabase opgeslagen.   

 Hier zijn manieren om de software-inventarisgegevens weer te geven:  

-   [Query's maken](../../../../core/servers/manage/queries-technical-reference.md) die apparaten met de opgegeven bestanden retourneren.   

-   Maak [query's gebaseerde verzamelingen](../../../../core/clients/manage/collections/introduction-to-collections.md) die apparaten met de opgegeven bestanden bevatten.   

-   [Rapporten uitvoeren](../../../../core/servers/manage/reporting.md) die vindt u informatie over bestanden op apparaten.

-   Gebruik [Resource Explorer](../../../../core/clients/manage/inventory/use-resource-explorer-to-view-software-inventory.md) om gedetailleerde informatie over de bestanden die zijn geïnventariseerd en verzameld van clientapparaten.   

 Wanneer software-inventarisatie wordt uitgevoerd op een clientapparaat, is het eerste rapport een volledige inventarisatie. Latere rapporten bevatten alleen delta-inventarisatie-informatie. De siteserver processen delta-gegevens in de volgorde ontvangen. Delta-informatie voor een client ontbreekt, de siteserver verwerpt verdere informatie verschillen als Hiermee geeft de client een volledige inventaris uitvoert.  

 Configuration Manager dual-boot computers kan detecteren, maar retourneert alleen inventarisatie-informatie van het besturingssysteem dat actief op het moment van de inventarisatie was.  

**Mobiele apparaten:** Zie [software-inventaris voor mobiele apparaten die zijn geregistreerd met Microsoft Intune](../../../../mdm/deploy-use/software-inventory-mobile-devices.md) voor informatie over het verzamelen van de inventaris voor geïnstalleerde apps op mobiele apparaten.

