---
title: Hardware-inventaris configureren | Microsoft-documenten
description: Hardware-inventaris instellen voor alle clients of voor een verzameling in System Center Configuration Manager.
ms.custom: na
ms.date: 02/22/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 0e45290e-f8f7-4335-801e-570225d12c2b
caps.latest.revision: 5
caps.handback.revision: 0
author: andredm7
ms.author: andredm
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9c5d1e48b76392beaf54b5377c69b648537e86f8
ms.openlocfilehash: 0baadb95ec8dbb945f1a611ebb95a03cec3199bd
ms.contentlocale: nl-nl
ms.lasthandoff: 05/17/2017


---
# <a name="how-to-configure-hardware-inventory-in-system-center-configuration-manager"></a>Hardware-inventaris configureren in System Center Configuration Manager

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*

Met deze procedure configureert u de standaardinstellingen voor de hardware-inventarisatie die voor alle clients in uw hiërarchie geldt. Als u wilt dat deze instellingen alleen van toepassing zijn op enkele clients, maakt u een aangepaste clientapparaatinstelling en wijst u deze toe aan een verzameling waartoe de apparaten behoren die u wilt inventariseren. Zie [clientinstellingen configureren in System Center Configuration Manager](../../../../core/clients/deploy/configure-client-settings.md).  

> [!NOTE]  
>  Als een clientapparaat instellingen voor hardware-inventarisatie van meerdere sets clientinstellingen ontvangt, worden de hardware-inventarisatieklassen van elke set instellingen samengevoegd wanneer de client hardware-inventarisatie rapporteert.  

### <a name="to-configure-hardware-inventory"></a>Hardware-inventarisatie configureren  

1.  Kies in de Configuration Manager-console **beheer** > **clientinstellingen** > **Standaardclientinstellingen**.  

4.  Op de **Start** tabblad, in de **eigenschappen** groep, kiest u **eigenschappen**.  

5.  In de **standaardinstellingen** dialoogvenster Kies **Hardware-inventaris**.  

6.  In de lijst **Apparaatinstellingen** configureert u dan het volgende:  

    -   **Hardware-inventaris op clients inschakelen** - Selecteer **waar**.  

    -   **Hardware-inventarisplanning** -Klik op **schema** het interval waarmee clients hardware-inventaris verzamelen.  

7.  Configureer andere [hardware-inventaris clientinstellingen](../../../../core/clients/deploy/about-client-settings.md#hardware-inventory) die u nodig hebt.  

De volgende keer dat clientapparaten clientbeleid downloaden, worden deze instellingen geconfigureerd. Raadpleeg [Clients beheren in System Center Configuration Manager](../../../../core/clients/manage/manage-clients.md) voor informatie over het initiëren van het ophalen van beleid voor één client.  
