---
title: Internationale ondersteuning | Microsoft-documenten
description: System Center Configuration Manager om te voldoen aan specifieke internationale vereisten configureren.
ms.custom: na
ms.date: 10/06/2016
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 46dd9cb2-a812-4b6a-a747-b840f92fef8b
caps.latest.revision: 6
caps.handback.revision: 0
author: Brenduns
ms.author: brenduns
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 40e018084dd2703327ff653f962f488432b1ec98
ms.openlocfilehash: 3bab51be96445f766e8f5bbf54eee854e5d09cee
ms.contentlocale: nl-nl
ms.lasthandoff: 05/17/2017


---
# <a name="international-support-in-system-center-configuration-manager"></a>Internationale ondersteuning in System Center Configuration Manager

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*

De volgende secties vindt u technische gegevens bij het maken van System Center Configuration Manager voldoet aan specifieke internationale vereisten.  

## <a name="gb18030-requirements"></a>GB18030-vereisten  
 Configuration Manager voldoet aan de normen die zijn gedefinieerd in GB18030, zodat u Configuration Manager in China kunt. Een Configuration Manager-implementatie, moet de volgende configuraties om te voldoen aan de GB18030-vereisten hebben:  

-   Elke siteservercomputer en SQL Server-computer die u gebruikt met Configuration Manager moet een Chinees besturingssysteem gebruiken.  

-   Voor elke sitedatabase en elk exemplaar van SQL Server in de hiërarchie moet dezelfde sortering worden gebruikt, en wel een van de volgende:  

    -   Chinese_Simplified_Pinyin_100_CI_AI  

    -   Chinese_Simplified_Stroke_Order_100_CI_AI  

    > [!NOTE]  
    >  Deze databasesorteringen vormen een uitzondering op de vereisten die worden vermeld in [ondersteuning voor versies van SQL Server voor System Center Configuration Manager](../../../core/plan-design/configs/support-for-sql-server-versions.md).  

-   U moet een bestand met de naam **GB18030.SMS** in de hoofdmap van het systeemvolume van elke siteservercomputer in de hiërarchie plaatsen. Dit bestand bevat geen gegevens en mag een leeg tekstbestand zijn dat enkel deze naam heeft gekregen om aan dit vereiste te voldoen.  

