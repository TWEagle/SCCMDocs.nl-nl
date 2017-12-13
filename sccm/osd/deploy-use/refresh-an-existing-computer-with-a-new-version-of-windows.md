---
title: Een bestaande computer vernieuwen met een nieuwe versie van Windows
titleSuffix: Configuration Manager
description: U kunt verschillende methoden gebruiken in Configuration Manager voor het partitioneren en formatteren (wissen) een bestaande computer en een nieuw besturingssysteem installeert op de computer.
ms.custom: na
ms.date: 10/06/2016
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: configmgr-osd
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: b189a346-8c0d-4870-a876-0719fbb0ab04
caps.latest.revision: "7"
author: aczechowski
ms.author: aaroncz
manager: angrobe
ms.openlocfilehash: 2a5489c35acc82c6fc11a0e83b7a5101b2e472fb
ms.sourcegitcommit: 08f9854fb6c6d21e1e923b13e38a64d0bc2bc9a4
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/12/2017
---
# <a name="refresh-an-existing-computer-with-a-new-version-of-windows-using-system-center-configuration-manager"></a>Een bestaande computer via System Center Configuration Manager vernieuwen met een nieuwe versie van Windows

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*

Dit onderwerp bevat de algemene stappen in System Center Configuration Manager voor het partitioneren en formatteren (wissen) een bestaande computer en installeer een nieuw besturingssysteem op de computer. U kunt voor dit scenario kiezen uit veel verschillende implementatiemethoden, zoals PXE, opstartbare media of Software Center. U kunt er ook voor kiezen om een statusmigratiepunt te installeren waarin de instellingen kunnen worden opgeslagen om deze vervolgens terug te zetten in het nieuwe besturingssysteem nadat dit is geïnstalleerd. Als u niet zeker weet dat dit het juiste besturingssysteem implementatiescenario voor u is, raadpleegt u [scenario's voor het implementeren van enterprise-besturingssystemen](scenarios-to-deploy-enterprise-operating-systems.md).  

 Gebruik de volgende secties om een bestaande computer te vernieuwen met een nieuwe versie van Windows.  

##  <a name="BKMK_Plan"></a> Plan  

-   **Infrastructuurvereisten plannen en implementeren**  

     Er zijn verschillende infrastructuurvereisten waaraan voldaan worden moeten voordat u kunt implementeren besturingssystemen, zoals Windows ADK, User status Migration Tool (USMT), Windows Deployment Services (WDS) ondersteunde vasteschijfconfiguraties, enzovoort. Zie voor meer informatie [vereisten voor de infrastructuur voor besturingssysteemimplementatie](../plan-design/infrastructure-requirements-for-operating-system-deployment.md).  

-   **Een statusmigratiepunt installeren (alleen vereist als u instellingen overzet)**  

     Wanneer u de instellingen van een bestaande computer wilt vastleggen om deze vervolgens terug te zetten in het nieuwe besturingssysteem, moet u een statusmigratiepunt installeren. Zie voor meer informatie [Statusmigratiepunt](../get-started/prepare-site-system-roles-for-operating-system-deployments.md#BKMK_StateMigrationPoints).  

##  <a name="BKMK_Configure"></a> Configurerenren  

1.  **Een opstartinstallatiekopie voorbereiden**  

     Opstartinstallatiekopieën starten een computer op in een Windows PE-omgeving (minimaal besturingssysteem met beperkte onderdelen en services), waarna er een volledig Windows-besturingssysteem op de computer kan worden geïnstalleerd.   Wanneer u besturingssystemen implementeert, moet u de opstartinstallatiekopie selecteren die u wilt gebruiken en de installatiekopie distribueren naar een distributiepunt. Gebruik de volgende informatie om een opstartinstallatiekopie voor te bereiden:  

    -   Zie voor meer informatie over opstartinstallatiekopieën, [opstartinstallatiekopieën beheren](../get-started/manage-boot-images.md).  

    -   Zie voor meer informatie over het aanpassen van een opstartinstallatiekopie [opstartinstallatiekopieën aanpassen](../get-started/customize-boot-images.md).  

    -   Distribueer de opstartinstallatiekopie naar distributiepunten. Zie voor meer informatie [inhoud distribueren](../../core/servers/deploy/configure/deploy-and-manage-content.md#bkmk_distribute).  

2.  **Een installatiekopie van een besturingssysteem voorbereiden**  

     De installatiekopie van het besturingssysteem bevat de bestanden die nodig zijn om het besturingssysteem op de doelcomputer te installeren. Gebruik de volgende informatie om de installatiekopie van het besturingssysteem voor te bereiden:  

    -   Zie voor meer informatie over het maken van een installatiekopie van het besturingssysteem, [installatiekopieën van besturingssystemen beheren](../get-started/manage-operating-system-images.md).  

    -   Distribueer de installatiekopie van het besturingssysteem naar distributiepunten. Zie voor meer informatie [inhoud distribueren](../../core/servers/deploy/configure/deploy-and-manage-content.md#bkmk_distribute).  

3.  **Een takenreeks maken om besturingssystemen via het netwerk te implementeren**  

     Maak een takenreeks om de installatie van het besturingssysteem via het netwerk te automatiseren. Gebruik de stappen in [een takenreeks maken om een besturingssysteem te installeren](create-a-task-sequence-to-install-an-operating-system.md) voor het maken van de takenreeks om het besturingssysteem te implementeren. Afhankelijk van de implementatiemethode waarvoor u kiest, kunnen er aanvullende overwegingen zijn bij het samenstellen van de takenreeks.  

    > [!NOTE]  
    >  In dit scenario worden de harde schijven op de computer met deze takenreeks geformatteerd en gepartitioneerd. Als u gebruikersinstellingen wilt vastleggen, moet u het statusmigratiepunt gebruiken en **Gebruikersinstellingen en bestanden opslaan op een statusmigratiepunt** selecteren op de pagina **Statusmigratie** van de wizard Takenreeks maken. Als u de gebruikersinstellingen en bestanden lokaal opslaat, worden deze verloren wanneer de vaste schijf wordt geformatteerd en Configuration Manager kan geen om de instellingen te herstellen. Zie voor meer informatie [Gebruikersstatus beheren](../get-started/manage-user-state.md).  

##  <a name="BKMK_Deploy"></a> Implementeren  

-   Gebruik een van de volgende implementatiemethoden om het besturingssysteem te implementeren:  

    -   [PXE gebruiken om Windows via het netwerk te implementeren](use-pxe-to-deploy-windows-over-the-network.md)  

    -   [Multicast gebruiken om Windows via het netwerk te implementeren](use-multicast-to-deploy-windows-over-the-network.md)  

    -   [Een installatiekopie voor een OEM in de fabriek of een lokaal depot maken](create-an-image-for-an-oem-in-factory-or-a-local-depot.md)  

    -   [Zelfstandige media gebruiken om Windows te implementeren zonder gebruik van het netwerk](use-stand-alone-media-to-deploy-windows-without-using-the-network.md)  

    -   [Opstartbare media gebruiken om Windows te implementeren via het netwerk](use-bootable-media-to-deploy-windows-over-the-network.md)  

    -   [Windows met Software Center via het netwerk implementeren](use-software-center-to-deploy-windows-over-the-network.md)  

## <a name="monitor"></a>Monitor  

-   **De takenreeksimplementatie controleren**  

     Voor het bewaken van de takenreeksimplementatie om het besturingssysteem te installeren, Zie [implementaties van besturingssystemen bewaken](monitor-operating-system-deployments.md).  
