---
title: Gebruik multicast om Windows via het netwerk implementeren
titleSuffix: Configuration Manager
description: Gebruik van multicast in uw omgeving voor System Center Configuration Manager zodat meerdere computers kunnen tegelijkertijd de installatiekopie van het besturingssysteem downloaden.
ms.custom: na
ms.date: 10/06/2016
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: configmgr-osd
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 4cafb7fc-380b-41b1-b83e-045aebfb7131
caps.latest.revision: "13"
author: aczechowski
ms.author: aaroncz
manager: angrobe
ms.openlocfilehash: d254b7ff1f66d73996cda66c0fb2134033868cb1
ms.sourcegitcommit: 08f9854fb6c6d21e1e923b13e38a64d0bc2bc9a4
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/12/2017
---
# <a name="use-multicast-to-deploy-windows-over-the-network-with-system-center-configuration-manager"></a>Multicast gebruiken om Windows te implementeren via het netwerk met System Center Configuration Manager

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*

Multicast is een methode voor netwerkoptimalisatie die u kunt gebruiken in uw System Center Configuration Manager-omgeving waar meerdere clients zich waarschijnlijk dezelfde installatiekopie van het besturingssysteem downloaden op hetzelfde moment. Wanneer multicast wordt gebruikt, kunnen meerdere computers tegelijkertijd de installatiekopie van het besturingssysteem downloaden, aangezien deze door het distributiepunt wordt aangeboden via multicasting. Het distributiepunt verzendt dus geen kopie van de gegevens via een aparte verbinding naar elke client.  

 U kunt besturingssystemen via het netwerk implementeren met behulp van multicast in de volgende implementatiescenario's voor besturingssystemen:  

-   [Een bestaande computer vernieuwen met een nieuwe versie van Windows](refresh-an-existing-computer-with-a-new-version-of-windows.md)  

-   [Een nieuwe versie van Windows op een nieuwe computer (bare-metal) installeren](install-new-windows-version-new-computer-bare-metal.md)  

 Voer de stappen in een van de implementatiescenario’s voor besturingssystemen uit en gebruik de volgende secties om multicast te ondersteunen.  

##  <a name="BKMK_Configure"></a> Een distributiepunt configureren voor de ondersteuning van multicast  
 Als u multicast wilt gebruiken om het besturingssysteem te implementeren, moet u een distributiepunt configureren voor de ondersteuning van multicast. Zie voor meer informatie [configureren ter ondersteuning van multicast-distributiepunten](../get-started/prepare-site-system-roles-for-operating-system-deployments.md#BKMK_DPMulticast).  

## <a name="prepare-an-operating-system-image-for-multicast-deployments"></a>De installatiekopie van een besturingssysteem voorbereiden voor multicast-implementaties  
 Voor het configureren van het installatiekopiepakket van het besturingssysteem voor multicast-ondersteuning, Zie [de installatiekopie van het besturingssysteem voorbereiden voor multicast-implementaties](../get-started/manage-operating-system-images.md#BKMK_OSImageMulticast).  

##  <a name="BKMK_Deploy"></a> De takenreeks implementeren  
 Implementeer het besturingssysteem in een doelverzameling. Zie [Een takenreeks implementeren](manage-task-sequences-to-automate-tasks.md#BKMK_DeployTS) voor meer informatie.  
