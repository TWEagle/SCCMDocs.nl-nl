---
title: Vervangen van een bestaande computer en Overdrachtinstellingen | Microsoft-documenten
description: In Configuration Manager, kiezen uit implementatiemethoden, zoals opstartbare media, multicast of Software Center om een bestaande computer vervangen door een nieuwe computer.
ms.custom: na
ms.date: 10/06/2016
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-osd
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: d28f4363-9e8a-4c54-9cb7-0594fabfff26
caps.latest.revision: 6
author: Dougeby
ms.author: dougeby
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 74341fb60bf9ccbc8822e390bd34f9eda58b4bda
ms.openlocfilehash: 243433980e1720fd468d52a4a61f2c3a8e3659b5
ms.contentlocale: nl-nl
ms.lasthandoff: 05/17/2017


---
# <a name="replace-an-existing-computer-and-transfer-settings-with-system-center-configuration-manager"></a>Een bestaande computer vervangen en de instellingen overzetten met System Center Configuration Manager

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*

Dit onderwerp bevat de algemene stappen in System Center Configuration Manager om een bestaande computer vervangen door een nieuwe computer. U kunt voor dit scenario kiezen uit veel verschillende implementatiemethoden, zoals het implementeren via opstartbare media, multicast of Software Center. U kunt er ook voor kiezen om een statusmigratiepunt te installeren waarin de instellingen kunnen worden opgeslagen om deze vervolgens terug te zetten in het nieuwe besturingssysteem nadat dit is geïnstalleerd. Als u weet dat dit het juiste besturingssysteem implementatiescenario voor u is, ziet u [scenario's voor het implementeren van besturingssystemen enterprise](scenarios-to-deploy-enterprise-operating-systems.md).  

 Gebruik de volgende secties om een bestaande computer te vernieuwen met een nieuwe versie van Windows.  

##  <a name="BKMK_Plan"></a> Plan  

-   **Infrastructuurvereisten plannen en implementeren**  

     Er zijn verschillende vereisten voor de infrastructuur die voldaan worden moeten voordat u kunt implementeren besturingssystemen, zoals Windows ADK, gebruiker State Migration Tool (USMT), Windows Deployment Services (WDS) ondersteunde configuraties van harde schijf, enzovoort. Zie voor meer informatie [vereisten voor de infrastructuur voor implementatie van besturingssysteem](../plan-design/infrastructure-requirements-for-operating-system-deployment.md)  

-   **Een statusmigratiepunt installeren (alleen vereist als u instellingen overzet)**  

     Wanneer u de instellingen van een bestaande computer wilt vastleggen om deze vervolgens terug te zetten in het nieuwe besturingssysteem, moet u een statusmigratiepunt installeren. Zie voor meer informatie [Statusmigratiepunt](../get-started/prepare-site-system-roles-for-operating-system-deployments.md#BKMK_StateMigrationPoints).  

##  <a name="BKMK_Configure"></a> Configurerenren  

1.  **Een opstartinstallatiekopie voorbereiden**  

     Opstartinstallatiekopieën starten een computer op in een Windows PE-omgeving (minimaal besturingssysteem met beperkte onderdelen en services), waarna er een volledig Windows-besturingssysteem op de computer kan worden geïnstalleerd. Wanneer u besturingssystemen implementeert, moet u de opstartinstallatiekopie selecteren die u wilt gebruiken en de installatiekopie distribueren naar een distributiepunt. Gebruik de volgende informatie om een opstartinstallatiekopie voor te bereiden:  

    -   Zie voor meer informatie over opstartinstallatiekopieën [opstartinstallatiekopieën beheren](../get-started/manage-boot-images.md).  

    -   Zie voor meer informatie over het aanpassen van een opstartinstallatiekopie [opstartinstallatiekopieën aanpassen](../get-started/customize-boot-images.md).  

    -   Distribueer de opstartinstallatiekopie naar distributiepunten. Zie voor meer informatie [inhoud distribueren](../../core/servers/deploy/configure/deploy-and-manage-content.md#a-namebkmkdistributea-distribute-content).  

2.  **Een installatiekopie van een besturingssysteem voorbereiden**  

     De installatiekopie van het besturingssysteem bevat de bestanden die nodig zijn om het besturingssysteem op de doelcomputer te installeren. Gebruik de volgende informatie om de installatiekopie van het besturingssysteem voor te bereiden:  

    -   Zie voor meer informatie over het maken van een besturingssysteeminstallatiekopie [installatiekopieën van besturingssystemen beheren](../get-started/manage-operating-system-images.md).  

    -   Distribueer de installatiekopie van het besturingssysteem naar distributiepunten. Zie voor meer informatie [inhoud distribueren](../../core/servers/deploy/configure/deploy-and-manage-content.md#a-namebkmkdistributea-distribute-content).  

3.  **Een takenreeks maken om besturingssystemen via het netwerk te implementeren**  

     Maak een takenreeks om de installatie van het besturingssysteem via het netwerk te automatiseren. Gebruik de stappen in [maken van een takenreeks om een besturingssysteem te installeren](create-a-task-sequence-to-install-an-operating-system.md) voor het maken van de takenreeks om het besturingssysteem te implementeren. Afhankelijk van de implementatiemethode waarvoor u kiest, kunnen er aanvullende overwegingen zijn bij het samenstellen van de takenreeks.  

    > [!NOTE]  
    >  Als u in dit scenario gebruikersinstellingen en bestanden vastlegt en terugzet, kunt u ervoor kiezen om een statusmigratiepunt te gebruiken om de bestanden lokaal op te slaan. Zie voor meer informatie [Gebruikersstatus beheren](../get-started/manage-user-state.md).  

##  <a name="BKMK_Deploy"></a> Implementeren  

-   Gebruik een van de volgende implementatiemethoden om het besturingssysteem te implementeren:  

    -   [Software Center gebruiken om Windows te implementeren via het netwerk](use-software-center-to-deploy-windows-over-the-network.md)  

    -   [Opstartbare media gebruikt om Windows te implementeren via het netwerk](use-bootable-media-to-deploy-windows-over-the-network.md)  

    -   [Gebruik multicast om Windows te implementeren via het netwerk](use-multicast-to-deploy-windows-over-the-network.md)  

    -   [Een installatiekopie maken voor een OEM in de fabriek of een lokale depot](create-an-image-for-an-oem-in-factory-or-a-local-depot.md)  

## <a name="monitor"></a>Monitor  

-   **De takenreeksimplementatie controleren**  

     Zie voor het controleren van de implementatie van takenreeks om het besturingssysteem te installeren, [bewaken van implementaties van besturingssystemen](monitor-operating-system-deployments.md).  

