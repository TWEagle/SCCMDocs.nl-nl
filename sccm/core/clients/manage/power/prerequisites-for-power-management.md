---
title: Vereisten voor energiebeheer | Microsoft Docs
description: Ophalen van de vereisten voor energiebeheer in System Center Configuration Manager.
ms.custom: na
ms.date: 10/06/2016
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 9c062f13-3c1f-4621-9cae-de0e322aa03f
caps.latest.revision: "4"
caps.handback.revision: "0"
author: arob98
ms.author: angrobe
manager: angrobe
ms.openlocfilehash: 5247bf1ce5b04264bc0d3e04c5de7f98300905c9
ms.sourcegitcommit: b438515490e04fb09c82a8af642d38e9a0605178
ms.translationtype: HT
ms.contentlocale: nl-NL
ms.lasthandoff: 09/15/2017
---
# <a name="prerequisites-for-power-management-in-system-center-configuration-manager"></a>Vereisten voor energiebeheer in System Center Configuration Manager

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*

Energiebeheer in System Center Configuration Manager heeft externe afhankelijkheden en afhankelijkheden binnen het product.  

## <a name="dependencies-external-to-configuration-manager"></a>Afhankelijkheden extern aan Configuration Manager  
 De volgende tabel bevat de afhankelijkheden extern aan Configuration Manager voor het gebruik van energiebeheer.  

|Afhankelijkheid|Meer informatie|  
|----------------|----------------------|  
|Clientcomputers moeten de vereiste energiestatussen ondersteunen|Voor het gebruik van alle functies van energiebeheer moeten clientcomputers de acties slaapstand, sluimerstand, activeren vanuit slaapstand en activeren vanuit sluimerstand ondersteunen. U kunt het rapport **Energiemogelijkheden** gebruiken om te bepalen of computers deze acties ondersteunen. Zie voor meer informatie [rapport Stroomvoorzieningsmogelijkheden](../../../../core/clients/manage/power/monitor-and-plan-for-power-management.md#BKMK_Capabilites) in het onderwerp [bewaken en plannen voor energiebeheer in System Center Configuration Manager](../../../../core/clients/manage/power/monitor-and-plan-for-power-management.md).|  

## <a name="configuration-manager-dependencies"></a>Configuration Manager-afhankelijkheden  
 De volgende tabel bevat de afhankelijkheden in Configuration Manager voor het gebruik van energiebeheer.  

|Afhankelijkheid|Meer informatie|  
|----------------|----------------------|  
|Energiebeheer moet worden ingeschakeld voordat u energiebeheerschema's kunt maken en controleren.|Zie voor meer informatie over het inschakelen en configureren van energiebeheer [energiebeheer configureren in System Center Configuration Manager](../../../../core/clients/manage/power/configuring-power-management.md).|  
|Reporting Services-punt|U moet een Reporting Services-punt configureren voordat u energiebeheerrapporten kunt weergeven. Zie [Rapportage in System Center Configuration Manager](../../../../core/servers/manage/reporting.md) voor meer informatie.|  
