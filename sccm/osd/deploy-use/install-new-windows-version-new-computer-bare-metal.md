---
title: Windows installeren op een nieuwe computer - Configuration Manager | Microsoft Docs
description: Configuration Manager gebruiken voor het installeren van een besturingssysteem op een nieuwe computer (bare-metal) met behulp van PXE, OEM of zelfstandige media.
ms.custom: na
ms.date: 01/23/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: configmgr-osd
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: f5ad22d5-7df1-49c6-8a0f-db1c3f0cda19
caps.latest.revision: "8"
author: Dougeby
ms.author: dougeby
manager: angrobe
ms.openlocfilehash: 584dad7d8b05a2da9f7a66b73028ae99ff1a594f
ms.sourcegitcommit: 51fc48fb023f1e8d995c6c4eacfda7dbec4d0b2f
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 08/07/2017
---
# <a name="install-a-new-version-of-windows-on-a-new-computer-bare-metal-with-system-center-configuration-manager"></a>Een nieuwe versie van Windows installeren op een nieuwe computer (bare-metal) met System Center Configuration Manager 

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*

Dit onderwerp bevat de algemene stappen in System Center Configuration Manager voor het installeren van een besturingssysteem op een nieuwe computer. U kunt voor dit scenario kiezen uit veel verschillende implementatiemethoden, zoals PXE, OEM of zelfstandige media. Als u niet zeker weet dat dit het juiste besturingssysteem implementatiescenario voor u is, raadpleegt u [scenario's voor het implementeren van enterprise-besturingssystemen](scenarios-to-deploy-enterprise-operating-systems.md).  

Gebruik de volgende secties om een bestaande computer te vernieuwen met een nieuwe versie van Windows.  

##  <a name="BKMK_Plan"></a> Plan  

-   **Infrastructuurvereisten plannen en implementeren**  

     Er zijn verschillende infrastructuurvereisten waaraan voldaan worden moeten voordat u besturingssystemen, zoals Windows ADK, Windows Deployment Services (WDS), ondersteunde vasteschijfconfiguraties, enzovoort. Zie voor meer informatie [vereisten voor de infrastructuur voor besturingssysteemimplementatie](../plan-design/infrastructure-requirements-for-operating-system-deployment.md).

##  <a name="BKMK_Configure"></a> Configurerenren  

1.  **Een opstartinstallatiekopie voorbereiden**  

     Opstartinstallatiekopieën starten een computer op in een Windows PE-omgeving (minimaal besturingssysteem met beperkte onderdelen en services), waarna er een volledig Windows-besturingssysteem op de computer kan worden geïnstalleerd.   Wanneer u besturingssystemen implementeert, moet u de opstartinstallatiekopie selecteren die u wilt gebruiken en de installatiekopie distribueren naar een distributiepunt. Gebruik de volgende informatie om een opstartinstallatiekopie voor te bereiden:  

    -   Zie voor meer informatie over opstartinstallatiekopieën, [opstartinstallatiekopieën beheren](../get-started/manage-boot-images.md).  

    -   Zie voor meer informatie over het aanpassen van een opstartinstallatiekopie [opstartinstallatiekopieën aanpassen](../get-started/customize-boot-images.md).  

    -   Distribueer de opstartinstallatiekopie naar distributiepunten. Zie voor meer informatie [inhoud distribueren](../../core/servers/deploy/configure/deploy-and-manage-content.md#a-namebkmkdistributea-distribute-content).  

2.  **Een installatiekopie van een besturingssysteem voorbereiden**  

     De installatiekopie van het besturingssysteem bevat de bestanden die nodig zijn om het besturingssysteem op de doelcomputer te installeren. Gebruik de volgende informatie om de installatiekopie van het besturingssysteem voor te bereiden:  

    -   Zie voor meer informatie over het maken van een installatiekopie van het besturingssysteem, [installatiekopieën van besturingssystemen beheren](../get-started/manage-operating-system-images.md).

    -   Distribueer de installatiekopie van het besturingssysteem naar distributiepunten. Zie voor meer informatie [inhoud distribueren](../../core/servers/deploy/configure/deploy-and-manage-content.md#a-namebkmkdistributea-distribute-content).

3.  **Een takenreeks maken om besturingssystemen via het netwerk te implementeren**  

     Maak een takenreeks om de installatie van het besturingssysteem via het netwerk te automatiseren. Gebruik de stappen in [een takenreeks maken om een besturingssysteem te installeren](create-a-task-sequence-to-install-an-operating-system.md) voor het maken van de takenreeks om het besturingssysteem te implementeren. Afhankelijk van de implementatiemethode waarvoor u kiest, kunnen er aanvullende overwegingen zijn bij het samenstellen van de takenreeks.  

##  <a name="BKMK_Deploy"></a> Implementeren  

-   Gebruik een van de volgende implementatiemethoden om het besturingssysteem te implementeren:  

    -   [PXE gebruiken om Windows via het netwerk te implementeren](use-pxe-to-deploy-windows-over-the-network.md)  

    -   [Multicast gebruiken om Windows via het netwerk te implementeren](use-multicast-to-deploy-windows-over-the-network.md)  

    -   [Een installatiekopie voor een OEM in de fabriek of een lokaal depot maken](create-an-image-for-an-oem-in-factory-or-a-local-depot.md)  

    -   [Zelfstandige media gebruiken om Windows te implementeren zonder gebruik van het netwerk](use-stand-alone-media-to-deploy-windows-without-using-the-network.md)  

    -   [Opstartbare media gebruiken om Windows te implementeren via het netwerk](use-bootable-media-to-deploy-windows-over-the-network.md)  

## <a name="monitor"></a>Monitor  

-   **De takenreeksimplementatie controleren**  

     Voor het bewaken van de takenreeksimplementatie om het besturingssysteem te installeren, Zie [implementaties van besturingssystemen bewaken](monitor-operating-system-deployments.md).  
