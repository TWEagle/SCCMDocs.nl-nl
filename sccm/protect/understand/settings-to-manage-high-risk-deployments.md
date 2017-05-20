---
title: Met een hoog risico implementaties beheren; | Microsoft-documenten
description: Leer hoe u site-instellingen configureren in System Center Configuration Manager om te waarschuwen admins als ze een implementatie met een hoog risico maken.
ms.custom: na
ms.date: 10/06/2016
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: get-started-article
ms.assetid: 8d37b983-a964-402c-819d-2512ed2d463b
caps.latest.revision: 6
author: Brenduns
ms.author: brenduns
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: bff083fe279cd6b36a58305a5f16051ea241151e
ms.openlocfilehash: 8b5564f39f07a67a3c9278379ed59ca415603d21
ms.contentlocale: nl-nl
ms.lasthandoff: 05/17/2017


---
# <a name="settings-to-manage-high-risk-deployments-for-system-center-configuration-manager"></a>Instellingen voor het beheren van implementaties met een hoog risico voor System Center Configuration Manager

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*


Met System Center Configuration Manager kunt u site-instellingen die gewaarschuwd admins als ze de implementatie van een takenreeks met een hoog risico maken. Een implementatie met een hoog risico is:  

-   Een implementatie die automatisch wordt geïnstalleerd  

-   Een implementatie die potentieel ongewenste gevolgen kan hebben  

 Bijvoorbeeld, een takenreeks die het doel van **vereist** die een besturingssysteem implementeert geldt een verhoogd risico.  

 U kunt de maximale grootte in deze implementatie verificatie-instellingen configureren zodat het risico van de implementatie van een ongewenste met een hoog risico:  

-   **De maximale grootte verzameling**: Verzamelingen met meer clients dan de limiet voor het maken van een implementatie verborgen.  

    -   **Standaardgrootte**: Deze instelling wordt de verzamelingen, standaard met meer clients dan de limiet voor het maken van een implementatie. U kunt deze verzamelingen nog steeds zien wanneer de implementatie wordt gemaakt, maar ze worden standaard verborgen. De standaardwaarde is 100. Voer een waarde van 0 in om deze instelling te negeren.  

    -   **Maximale grootte**: Deze instelling altijd verborgen verzamelingen met meer clients dan de limiet bij het maken van een implementatie. De standaardwaarde is 0, waarmee deze instelling wordt genegeerd. De waarde voor **Maximumgrootte** moet groter zijn dan de waarde voor **Standaardgrootte** .  

     Bijvoorbeeld, u instellen **standaardgrootte** en 100 en het **maximumgrootte** en 1000. Wanneer u een implementatie met een hoog risico maken de **verzameling selecteren** verzamelingen met minder dan 100 clients wordt alleen weergegeven. Als u wist de **verbergen verzamelingen met een lid tellen groter is dan de siteâ€™ s minimumgrootte configuratie** , het venster wordt weergegeven wanneer verzamelingen die minder dan 1000 clients bevatten.  

-   **Verzamelingen met sitesysteemservers**: Implementaties blokkeren of verificatie vereisen voordat de implementatie wordt gemaakt wanneer de doelverzameling een computer met een sitesysteemrol wordt gehost bevat. Wanneer een implementatie wordt geblokkeerd, moet u een andere verzameling selecteren die wel aan de verificatiecriteria voor de implementatie voldoet.  

> [!NOTE]  
>  Implementaties met een hoog risico zijn altijd beperkt tot aangepaste verzamelingen, verzameling die uzelf maakt en de ingebouwde verzameling **Onbekende computers** . Wanneer u een implementatie met een hoog risico maakt, kunt u geen ingebouwde verzameling selecteren, zoals **Alle systemen**.  

### <a name="to-configure-deployment-verification-for-a-site"></a>Implementatieverificatie voor een site configureren  

1.  Kies in de Configuration Manager-console **beheer** >**siteconfiguratie** > **Sites**, en selecteer vervolgens de primaire site configureren.  

2.  Op de **Start** tabblad, in de **eigenschappen** groep, kiest u **eigenschappen**, en selecteer vervolgens de **verificatie van de implementatie** tabblad.  

3.  Nadat de configuraties die u wilt gebruiken, kiest u **OK** aan de configuratie op te slaan.  

### <a name="see-also"></a>Zie tevens  
 [Configureren van sites en hiërarchieën voor System Center Configuration Manager](../../core/servers/deploy/configure/configure-sites-and-hierarchies.md)

