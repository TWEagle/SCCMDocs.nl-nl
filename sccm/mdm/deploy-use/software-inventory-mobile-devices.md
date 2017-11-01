---
title: Software-inventaris voor mobiele apparaten die zijn ingeschreven bij Microsoft Intune
titleSuffix: Configuration Manager
description: Software-inventaris voor mobiele apparaten die zijn ingeschreven bij Microsoft Intune.
ms.custom: na
ms.date: 03/05/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: configmgr-hybrid
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: a0eae17a-60a8-4132-91af-0b10ad338c92
caps.latest.revision: "18"
caps.handback.revision: "0"
author: dougeby
ms.author: dougeby
manager: angrobe
ms.openlocfilehash: c0a583de1a0b24bd31c0d55c1acb54f480bb4230
ms.sourcegitcommit: c236214b2fcc13dae7bad96d7fb33f692868191d
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/12/2017
---
# <a name="software-inventory-for-mobile-devices-enrolled-with-microsoft-intune"></a>Software-inventarisatie voor mobiele apparaten die zijn geregistreerd bij Microsoft Intune

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*

 U kunt de inventaris voor geïnstalleerde apps op mobiele apparaten verzamelen. Welke apps worden geïnventariseerd, hangt ervan af of het apparaat in bedrijfseigendom of persoonlijk eigendom is. Alleen apps die zijn geïnventariseerd zijn voor persoonlijke apparaten, apps die worden beheerd door Microsoft Intune.  

> [!NOTE]  
>  Inventarisatie van de geïnstalleerde apps op mobiele apparaten worden verzameld als onderdeel van de [hardware-inventaris](mobile-device-hardware-inventory-hybrid.md) proces.  

 Hier volgen de apps die zijn geïnventariseerd voor apparaten die persoonlijk eigendom of eigendom van het bedrijf.  

|Platform|Voor apparaten die persoonlijk eigendom zijn|Voor apparaten die bedrijfseigendom zijn|  
|--------------|---------------------------------|--------------------------------|  
|Windows 10 (zonder de Configuration Manager-client)|Alleen beheerde apps|Alleen beheerde apps|
|Windows 8.1 (zonder de Configuration Manager-client)|Alleen beheerde apps|Alleen beheerde apps|  
|Windows Phone 8|Alleen beheerde apps|Alleen beheerde apps|  
|Windows RT|Alleen beheerde apps|Alleen beheerde apps|  
|iOS|Alleen beheerde apps|Alle apps die op het apparaat zijn geïnstalleerd|  
|Android|Alleen beheerde apps|Alle apps die op het apparaat zijn geïnstalleerd|  

Zie [Inleiding tot software-inventaris](../../core/clients/manage/inventory/introduction-to-software-inventory.md) en [het configureren van software-inventaris ](../../core/clients/manage/inventory/configure-software-inventory.md) voor gedetailleerde informatie over het gebruik van software-inventaris te verzamelen van bestandsgegevens op clientapparaten.
