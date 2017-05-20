---
title: Gebruik Software Center om Windows te implementeren via het netwerk | Microsoft-documenten
description: U kunt een besturingssysteem implementeren op Software Center vernieuwen van een bestaande computer met een nieuwe versie van Windows of upgrade van Windows voor de nieuwste versie.
ms.custom: na
ms.date: 10/06/2016
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-osd
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 919e3636-53fe-4119-ad14-2d03702b391b
caps.latest.revision: 5
author: Dougeby
ms.author: dougeby
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 74341fb60bf9ccbc8822e390bd34f9eda58b4bda
ms.openlocfilehash: 4c3ec20396da37d36f908af527f445a7a736e0ac
ms.contentlocale: nl-nl
ms.lasthandoff: 05/17/2017


---
# <a name="use-software-center-to-deploy-windows-over-the-network-with-system-center-configuration-manager"></a>Windows met Software Center via het netwerk implementeren met System Center Configuration Manager

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*

De takenreeks een besturingssysteem installeren in System Center Configuration Manager kan beschikbaar worden gesteld in Software Center. U kunt een besturingssysteem implementeren naar Software Center in de volgende implementatiescenario's voor besturingssystemen:  

-   [Vernieuwen van een bestaande computer met een nieuwe versie van Windows](refresh-an-existing-computer-with-a-new-version-of-windows.md)  

-   [Upgrade van Windows voor de nieuwste versie](upgrade-windows-to-the-latest-version.md)  

 Voer de stappen in een van de implementatiescenario's voor besturingssystemen uit en gebruik vervolgens de volgende secties om voor te bereiden voor implementaties die beschikbaar worden gesteld in Software Center.  

## <a name="configure-deployment-settings"></a>Implementatie-instellingen configureren  
 Wanneer u de implementatie van besturingssystemen moet beschikbaar in Software Center, moet u de implementatie van het besturingssysteem om beschikbaar te maken voor Configuration Manager-clients configureren. U kunt dit configureren op de pagina **Implementatie-instellingen** van de wizard Software implementeren of op het tabblad **Implementatie-instellingen** in de eigenschappen voor de implementatie.  Voor de instelling **Toegankelijk maken voor de volgende** configureert u **Alleen Configuration Manager-clients** of **Configuration Manager-clients, media en PXE**. Nadat het besturingssysteem is geïmplementeerd, wordt het in Software Center weergegeven voor leden van de doelverzameling.  

##  <a name="BKMK_Deploy"></a> De takenreeks implementeren naar computers  
 Het besturingssysteem implementeren naar een doelverzameling. Zie [Een takenreeks implementeren](manage-task-sequences-to-automate-tasks.md#BKMK_DeployTS) voor meer informatie. Wanneer u besturingssystemen voor Software Center implementeert, configureert u of de implementatie vereist of beschikbaar is.  

-   **Vereiste implementatie**: Vereiste implementaties wordt beschikbaar maken voor het besturingssysteem in Software Center, maar deze wordt automatisch gestart op de geconfigureerde toegewezen planning.  

-   **Beschikbare implementatie**: Het besturingssysteem zijn beschikbaar in Software Center en kan de gebruiker deze op aanvraag installeren.  

