---
title: Hardware-inventaris weergeven | Microsoft documenten | Resource Explorer
description: Resource Explorer gebruiken om hardware-inventaris in System Center Configuration Manager weer te geven.
ms.custom: na
ms.date: 01/03/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 375912f5-436d-4315-bdbe-d77afee6c9f3
caps.latest.revision: 7
author: andredm7
ms.author: andredm
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9c5d1e48b76392beaf54b5377c69b648537e86f8
ms.openlocfilehash: e39fa60a5d215fa1b0a98d4463058497e63a4d4f
ms.contentlocale: nl-nl
ms.lasthandoff: 05/29/2017


---
# <a name="how-to-use-resource-explorer-to-view-hardware-inventory-in-system-center-configuration-manager"></a>Resource Explorer gebruiken om hardware-inventaris te bekijken in System Center Configuration Manager

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*

Gebruik Resource Explorer in System Center Configuration Manager om informatie over hardware-inventaris werd verzameld van clients in uw hiërarchie weer te geven.  

> [!NOTE]  
>  Resource Explorer geeft geen inventarisgegevens weer tot er een hardware-inventarisatiefase is uitgevoerd op de client waarmee u verbinding maakt.  

 Resource Explorer heeft de volgende secties die betrekking hebben op hardware-inventaris:  

-   **Hardware** -bevat de meest recente hardware-inventaris verzameld van de opgegeven client-apparaat.  **Status van werkstation** is de tijd en datum waarop het apparaat laatste hardware-inventarisatie uitgevoerd.  

-   **Hardware geschiedenis** -bevat een overzicht van de geïnventariseerde artikelen die zijn gewijzigd sinds de laatste hardware-inventaris plaatsgevonden heeft. Elk item bevat een **huidige** knooppunt en een of meer *< datum\>*  knooppunten. U kunt de informatie in het huidige knooppunt naar een van de historische knooppunten voor het detecteren van items die zijn gewijzigd vergelijken.  

    > [!NOTE]  
    >  Configuration Manager behoudt hardware-inventarisgeschiedenis voor het aantal dagen die u opgeeft in de **verouderde Inventarisgeschiedenis verwijderen** siteonderhoudstaak  

> [!NOTE]  
>  Zie voor meer informatie over het weergeven van de hardware-inventaris van clients met Linux en UNIX [Clients controleren voor Linux- en UNIX-servers in System Center Configuration Manager](../../../../core/clients/manage/monitor-clients-for-linux-and-unix-servers.md).  

### <a name="how-to-run-resource-explorer-from-the-configuration-manager-console"></a>Resource Explorer uitvoeren vanaf de Configuration Manager-console  

1.  Kies in de Configuration Manager-console **activa en naleving** > **apparaten**, of open een verzameling die apparaten weergeeft.  

3.  Kies de computer met de inventaris die u wilt weergeven en klik op de **Start** tabblad > **apparaten** groep, kiest u **Start** >  **Resource Explorer**.   

4.  Met de rechtermuisknop op een item in het rechterdeelvenster van het **Resource Explorer** venster en kies **eigenschappen** openen de *< Itemnaam\>***eigenschappen** in het dialoogvenster om de verzamelde Inventarisinformatie beter leesbaar indeling weer te geven.  


