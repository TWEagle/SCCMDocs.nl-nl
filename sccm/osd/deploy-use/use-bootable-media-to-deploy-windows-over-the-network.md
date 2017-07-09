---
title: Opstartbare media gebruiken om Windows te implementeren via het netwerk | Microsoft Docs
description: Gebruik van opstartbare media implementaties in System Center Configuration Manager voor het besturingssysteem implementeren wanneer de doelcomputer wordt opgestart.
ms.custom: na
ms.date: 6/16/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-osd
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 999b5409-7e72-48d2-8554-4d44427ce383
caps.latest.revision: 5
author: mattbriggs
ms.author: mattbriggs
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: f4c46bfab9b40b29654f4e883817a5508ab25b74
ms.openlocfilehash: 9b20e5e2a66d92038033e816e6fc701581c48a7f
ms.contentlocale: nl-nl
ms.lasthandoff: 06/28/2017


---
# <a name="use-bootable-media-to-deploy-windows-over-the-network-with-system-center-configuration-manager"></a>Opstartbare media gebruiken om Windows te implementeren via het netwerk met System Center Configuration Manager

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*

U kunt het besturingssysteem implementeren wanneer de doelcomputer wordt gestart met behulp van een implementatie met opstartbare media. Het medium bevat een verwijzing naar de takenreeks, de installatiekopie van het besturingssysteem en andere vereiste inhoud vanaf het netwerk. Wanneer de doelcomputer wordt gestart, haalt de computer de items waarnaar wordt verwezen in de wijzer. Met de opstartbare media gratis van inhoud, kunt u het doel bijwerken zonder te vervangen op de media.

U kunt besturingssystemen implementeren via het netwerk met behulp van multicast in de volgende implementatiescenario's van besturingssysteem:

-   [Een bestaande computer vernieuwen met een nieuwe versie van Windows](refresh-an-existing-computer-with-a-new-version-of-windows.md)

-   [Een nieuwe versie van Windows op een nieuwe computer (bare-metal) installeren](install-new-windows-version-new-computer-bare-metal.md)  

-   [Een bestaande computer vervangen en de instellingen overzetten](replace-an-existing-computer-and-transfer-settings.md)  

Voer de stappen in een van de implementatiescenario's voor besturingssystemen uit en gebruik vervolgens de volgende secties om het besturingssysteem te implementeren met opstartbare media.  

## <a name="configure-deployment-settings"></a>Implementatie-instellingen configureren  
Wanneer u opstartbare media gebruiken om te beginnen het implementatieproces van het besturingssysteem, de implementatie configureren om het besturingssysteem beschikbaar te stellen de media. U kunt deze optie instelt op de **implementatie-instellingen** pagina van de Wizard Software implementeren of in de **implementatie-instellingen** tabblad in de eigenschappen voor de implementatie. Configureer een van de volgende waarden voor de instelling **Toegankelijk maken voor de volgende** :

-   Configuration Manager-clients, media en PXE

-   Alleen media en PXE

-   Alleen media en PXE (verborgen)

## <a name="create-the-bootable-media"></a>De opstartbare media maken
U kunt opgeven of de opstartbare media een USB-flashstation of CD/DVD-set. De computer die de media begint, moet de optie die u als opstartbaar station kiest ondersteunen. Zie voor meer informatie [opstartbare media maakt](create-bootable-media.md).  

##  <a name="BKMK_Deploy"></a> Het besturingssysteem installeren vanaf opstartbare media  
De opstartbare media invoegen in een opstartbaar station op de computer en deze vervolgens inschakelen om het besturingssysteem te installeren.

