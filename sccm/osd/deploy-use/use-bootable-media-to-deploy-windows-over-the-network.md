---
title: Opstartbare media gebruikt om Windows te implementeren via het netwerk | Microsoft-documenten
description: Gebruik implementaties met opstartbare media in System Center Configuration Manager voor het implementeren van het besturingssysteem, wanneer de doelcomputer wordt gestart.
ms.custom: na
ms.date: 10/06/2016
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-osd
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 999b5409-7e72-48d2-8554-4d44427ce383
caps.latest.revision: 5
author: Dougeby
ms.author: dougeby
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 74341fb60bf9ccbc8822e390bd34f9eda58b4bda
ms.openlocfilehash: beb730efbe4d9bae7c4c97f4e587c8919bd79049
ms.contentlocale: nl-nl
ms.lasthandoff: 05/17/2017


---
# <a name="use-bootable-media-to-deploy-windows-over-the-network-with-system-center-configuration-manager"></a>Opstartbare media gebruikt om Windows te implementeren via het netwerk met System Center Configuration Manager

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*

Implementaties met opstartbare media in System Center Configuration Manager kunnen u het besturingssysteem implementeren wanneer de doelcomputer wordt gestart. De doelcomputer haalt de takenreeks, de installatiekopie van het besturingssysteem en alle andere vereiste inhoud van het netwerk op tijdens het opstarten. Omdat die inhoud zich niet op de media bevindt, kunt u de inhoud bijwerken zonder de media opnieuw te moeten maken.  

 U kunt besturingssystemen via het netwerk implementeren met behulp van multicast in de volgende implementatiescenario's voor besturingssystemen:  

-   [Vernieuwen van een bestaande computer met een nieuwe versie van Windows](refresh-an-existing-computer-with-a-new-version-of-windows.md)  

-   [Een nieuwe versie van Windows installeren op een nieuwe computer (bare metal)](install-new-windows-version-new-computer-bare-metal.md)  

-   [Vervangen van een bestaande computer en instellingen overzetten](replace-an-existing-computer-and-transfer-settings.md)  

 Voer de stappen in een van de implementatiescenario's voor besturingssystemen uit en gebruik vervolgens de volgende secties om het besturingssysteem te implementeren met opstartbare media.  

## <a name="configure-deployment-settings"></a>Implementatie-instellingen configureren  
 Als u het implementatieproces voor een besturingssysteem wilt starten vanaf opstartbare media, moet u de implementatie configureren om het besturingssysteem beschikbaar te stellen voor media. U kunt dit configureren op de pagina **Implementatie-instellingen** van de wizard Software implementeren of op het tabblad **Implementatie-instellingen** in de eigenschappen voor de implementatie.  Configureer een van de volgende waarden voor de instelling **Toegankelijk maken voor de volgende** :  

-   **Configuration Manager-clients, media en PXE**  

-   **Alleen media en PXE**  

-   **Alleen media en PXE (verborgen)**  

## <a name="create-the-bootable-media"></a>De opstartbare media maken  
 U kunt opgeven of de opstartbare media worden gevormd door een USB-flashstation of een cd-/dvd-set. De optie die u als opstartbaar station kiest, moet worden ondersteund door de computer waarop de media worden gestart. Zie voor meer informatie [opstartbare media maakt](create-bootable-media.md).  

##  <a name="BKMK_Deploy"></a> Het besturingssysteem installeren vanaf opstartbare media  
 De opstartbare media invoegen in een opstartbaar station op de computer en deze vervolgens inschakelen om het besturingssysteem te installeren.  

