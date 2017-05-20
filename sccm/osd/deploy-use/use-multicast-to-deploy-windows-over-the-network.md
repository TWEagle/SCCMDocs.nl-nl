---
title: Gebruik multicast om Windows te implementeren via het netwerk | Microsoft-documenten
description: Gebruik van multicast in uw omgeving voor System Center Configuration Manager zodat meerdere computers tegelijkertijd de installatiekopie van het besturingssysteem kunnen downloaden.
ms.custom: na
ms.date: 10/06/2016
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-osd
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 4cafb7fc-380b-41b1-b83e-045aebfb7131
caps.latest.revision: 13
author: Dougeby
ms.author: dougeby
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 74341fb60bf9ccbc8822e390bd34f9eda58b4bda
ms.openlocfilehash: 55266696aa7340fddda3a57ff90e20222ff665a5
ms.contentlocale: nl-nl
ms.lasthandoff: 05/17/2017


---
# <a name="use-multicast-to-deploy-windows-over-the-network-with-system-center-configuration-manager"></a>Gebruik multicast om Windows te implementeren via het netwerk met System Center Configuration Manager

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*

Multicast is een methode voor netwerkoptimalisatie die u kunt gebruiken in uw System Center Configuration Manager-omgeving waarbij meerdere clients kunnen dezelfde installatiekopie van het besturingssysteem downloaden op hetzelfde moment zijn geïnstalleerd. Wanneer multicast wordt gebruikt, kunnen meerdere computers tegelijkertijd de installatiekopie van het besturingssysteem downloaden, aangezien deze door het distributiepunt wordt aangeboden via multicasting. Het distributiepunt verzendt dus geen kopie van de gegevens via een aparte verbinding naar elke client.  

 U kunt besturingssystemen via het netwerk implementeren met behulp van multicast in de volgende implementatiescenario's voor besturingssystemen:  

-   [Vernieuwen van een bestaande computer met een nieuwe versie van Windows](refresh-an-existing-computer-with-a-new-version-of-windows.md)  

-   [Een nieuwe versie van Windows installeren op een nieuwe computer (bare metal)](install-new-windows-version-new-computer-bare-metal.md)  

 Voer de stappen in een van de implementatiescenario’s voor besturingssystemen uit en gebruik de volgende secties om multicast te ondersteunen.  

##  <a name="BKMK_Configure"></a> Een distributiepunt configureren voor de ondersteuning van multicast  
 Als u multicast wilt gebruiken om het besturingssysteem te implementeren, moet u een distributiepunt configureren voor de ondersteuning van multicast. Zie voor meer informatie [distributiepunten voor multicast-ondersteuning configureren](../get-started/prepare-site-system-roles-for-operating-system-deployments.md#BKMK_DPMulticast).  

## <a name="prepare-an-operating-system-image-for-multicast-deployments"></a>De installatiekopie van een besturingssysteem voorbereiden voor multicast-implementaties  
 Zie voor het configureren van het installatiekopiepakket van het besturingssysteem voor multicast-ondersteuning [voorbereiden van de installatiekopie van het besturingssysteem voor multicast-implementaties](../get-started/manage-operating-system-images.md#BKMK_OSImageMulticast).  

##  <a name="BKMK_Deploy"></a> De takenreeks implementeren  
 Implementeer het besturingssysteem in een doelverzameling. Zie [Een takenreeks implementeren](manage-task-sequences-to-automate-tasks.md#BKMK_DeployTS) voor meer informatie.  

