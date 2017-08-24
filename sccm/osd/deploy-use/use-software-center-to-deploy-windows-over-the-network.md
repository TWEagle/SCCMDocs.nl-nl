---
title: Gebruik Software Center om Windows te implementeren via het netwerk | Microsoft Docs
description: U kunt een besturingssysteem implementeren naar Software Center naar een bestaande computer vernieuwen met een nieuwe versie van Windows of Windows upgraden naar de nieuwste versie.
ms.custom: na
ms.date: 6/16/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: configmgr-osd
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 919e3636-53fe-4119-ad14-2d03702b391b
caps.latest.revision: "5"
author: mattbriggs
ms.author: mabrigg
manager: angrobe
ms.openlocfilehash: 8988409c68b7f69439ed03872c316b2139d25616
ms.sourcegitcommit: 51fc48fb023f1e8d995c6c4eacfda7dbec4d0b2f
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 08/07/2017
---
# <a name="use-software-center-to-deploy-windows-over-the-network-with-system-center-configuration-manager"></a>Windows met Software Center via het netwerk implementeren met System Center Configuration Manager

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*

U kunt de takenreeks die u een besturingssysteem in System Center Configuration Manager beschikbaar in Software Center installeert. U kunt een besturingssysteem implementeren naar Software Center met de volgende implementatiescenario's voor besturingssystemen:

-   [Een bestaande computer vernieuwen met een nieuwe versie van Windows](refresh-an-existing-computer-with-a-new-version-of-windows.md)

-   [Windows bijwerken naar de laatste versie](upgrade-windows-to-the-latest-version.md)

Voltooi de stappen in een van de implementatiescenario's voor besturingssystemen. Gebruik de volgende secties om voor te bereiden voor implementaties die beschikbaar in Software Center zijn.

## <a name="configure-deployment-settings"></a>Implementatie-instellingen configureren  
Als u de implementatie van besturingssystemen in Software Center, de implementatie te configureren. U kunt de implementatie configureren op de **implementatie-instellingen** pagina van de Wizard Software implementeren of de **implementatie-instellingen** tabblad in de eigenschappen voor de implementatie. Voor de instelling **Toegankelijk maken voor de volgende** configureert u **Alleen Configuration Manager-clients** of **Configuration Manager-clients, media en PXE**. Nadat het systeem het besturingssysteem implementeert, wordt het besturingssysteem weergegeven in Software Center voor leden van de doelverzameling.

##  <a name="BKMK_Deploy"></a> De takenreeks implementeren naar computers  
Het besturingssysteem implementeren naar een doelverzameling. Zie [Een takenreeks implementeren](manage-task-sequences-to-automate-tasks.md#BKMK_DeployTS) voor meer informatie. Wanneer u besturingssystemen voor Software Center implementeert, kunt u configureren of de implementatie vereist of beschikbaar.

-   **Vereiste implementatie**: Vereiste implementaties wordt het besturingssysteem beschikbaar gesteld in Software Center, maar wordt automatisch gestart volgens de geconfigureerde toewijzingsplanning.

-   **Beschikbare implementatie**: Het besturingssysteem wordt beschikbaar gesteld in Software Center en de gebruiker deze op verzoek kan installeren.
