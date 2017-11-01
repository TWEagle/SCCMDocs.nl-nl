---
title: Software-inventaris weergeven met Resource Explorer
titleSuffix: Configuration Manager
description: Resource Explorer gebruiken om software-inventaris in System Center Configuration Manager weer te geven.
ms.custom: na
ms.date: 2/22/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 4b7aa5f6-5ebd-49be-b7f3-4206caadc187
caps.latest.revision: "5"
caps.handback.revision: "0"
author: andredm7
ms.author: andredm
manager: angrobe
ms.openlocfilehash: 242bd336fcb13172097e26187a48c924dbd9acb6
ms.sourcegitcommit: c236214b2fcc13dae7bad96d7fb33f692868191d
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/12/2017
---
# <a name="how-to-use-resource-explorer-to-view-software-inventory-in-system-center-configuration-manager"></a>Resource Explorer gebruiken om software-inventaris in System Center Configuration Manager weer te geven

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*

Gebruik Resource Explorer in System Center Configuration Manager voor informatie over software-inventaris die is verzameld van computers in uw hiërarchie.  

> [!NOTE]  
>  Resource Explorer wordt inventarisgegevens weer tot er een software-inventarisatiefase is uitgevoerd op de client.  

 Resource Explorer biedt de volgende software-inventarisatie-informatie:  

-   **Software**:  

    -   **Bestanden verzameld** -bestanden die zijn verzameld tijdens het software-inventaris.  

    -   **Bestandsgegevens** -bestanden die zijn geïnventariseerd tijdens software-inventarisatie die niet gekoppeld aan een specifiek product of de fabrikant zijn.  

    -   **Vorige Softwarescan** -datum en tijd van de laatste software-inventaris en bestandsverzameling voor de clientcomputer.  

    -   **Productgegevens** -softwareproducten die door de software-inventarisatie zijn geïnventariseerd, gegroepeerd op fabrikant.  

## <a name="to-run-resource-explorer-from-the-configuration-manager-console"></a>Resource Explorer uitvoeren vanaf de Configuration Manager-console  

1.  Kies in de Configuration Manager-console **activa en naleving**

2.  In de **activa en naleving** werkruimte, kiest u **apparaten** of open een verzameling die apparaten weergeeft.  

3.  Kies de computer met de inventaris die u wilt weergeven en klikt u op de **Start** tabblad > **apparaten** groep, kiest u **Start** > **Resource Explorer**.

4.  U kunt met de rechtermuisknop op een item in het rechterdeelvenster van het Resource Explorer-venster en kies **eigenschappen** om weer te geven informatie over de verzamelde inventaris in een beter leesbare indeling.  
 
