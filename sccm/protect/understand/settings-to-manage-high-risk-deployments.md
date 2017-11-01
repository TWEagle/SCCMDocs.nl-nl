---
title: Implementaties met een hoog risico beheren
titleSuffix: Configuration Manager
description: Informatie over het site-instellingen configureren in System Center Configuration Manager en beheerders waarschuwen als ze een implementatie met hoog risico maken.
ms.custom: na
ms.date: 10/06/2016
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: configmgr-other
ms.tgt_pltfrm: na
ms.topic: get-started-article
ms.assetid: 8d37b983-a964-402c-819d-2512ed2d463b
caps.latest.revision: "6"
author: Brenduns
ms.author: brenduns
manager: angrobe
ms.openlocfilehash: 6c0ae39c674202bc999c3fccc9547a60ff8c6627
ms.sourcegitcommit: c236214b2fcc13dae7bad96d7fb33f692868191d
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/12/2017
---
# <a name="settings-to-manage-high-risk-deployments-for-system-center-configuration-manager"></a>Instellingen voor het beheren van implementaties van met een hoog risico voor System Center Configuration Manager

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*


Met System Center Configuration Manager kunt u site-instellingen die beheerders wordt gewaarschuwd als ze een takenreeksimplementatie hoog risico maken. Een implementatie met een hoog risico is:  

-   Een implementatie die automatisch wordt geïnstalleerd  

-   Een implementatie die potentieel ongewenste gevolgen kan hebben  

 Bijvoorbeeld een takenreeks met het doel van **vereist** die een besturingssysteem implementeert geldt een verhoogd risico.  

 Als u het risico van een implementatie met een ongewenst hoog risico, kunt u de maximale grootte in de verificatie-instellingen voor deze implementatie configureren:  

-   **De maximale grootte verzameling**: Verzamelingen met meer clients bevatten dan de limiet voor het maken van een implementatie verborgen.  

    -   **Standaardgrootte**: Deze instelling verborgen verzamelingen die standaard met meer clients bevatten dan de limiet voor het maken van een implementatie. U kunt deze verzamelingen nog steeds zien wanneer de implementatie wordt gemaakt, maar ze worden standaard verborgen. De standaardwaarde is 100. Voer een waarde van 0 in om deze instelling te negeren.  

    -   **Maximale grootte**: Deze instelling worden verzamelingen verborgen met meer clients bevatten dan de limiet bij het maken van een implementatie. De standaardwaarde is 0, waarmee deze instelling wordt genegeerd. De waarde voor **Maximumgrootte** moet groter zijn dan de waarde voor **Standaardgrootte** .  

     Bijvoorbeeld, u stelt **standaardgrootte** en 100 en de **maximumgrootte** tot en met 1000. Wanneer u een implementatie met hoog risico maakt de **verzameling selecteren** venster alleen verzamelingen weergegeven die minder dan 100 clients bevatten. Als u het selectievakje de **lid zamelingen verbergen groter is dan de siteâ€™ s minimumgrootte configuratie** uitschakelt, het venster verzamelingen weergegeven die minder dan 1000 clients bevatten.  

-   **Verzamelingen met sitesysteemservers**: Blokkeren implementaties of vereisen verificatie voordat de implementatie wordt gemaakt wanneer de doelverzameling een computer met een sitesysteemrol bevat. Wanneer een implementatie wordt geblokkeerd, moet u een andere verzameling selecteren die wel aan de verificatiecriteria voor de implementatie voldoet.  

> [!NOTE]  
>  Implementaties met een hoog risico zijn altijd beperkt tot aangepaste verzamelingen, verzameling die uzelf maakt en de ingebouwde verzameling **Onbekende computers** . Wanneer u een implementatie met een hoog risico maakt, kunt u geen ingebouwde verzameling selecteren, zoals **Alle systemen**.  

### <a name="to-configure-deployment-verification-for-a-site"></a>Implementatieverificatie voor een site configureren  

1.  Kies in de Configuration Manager-console **beheer** >**siteconfiguratie** > **Sites**, en selecteer vervolgens de primaire site configureren.  

2.  Op de **Start** tabblad, in de **eigenschappen** groep, kiest u **eigenschappen**, en kies vervolgens de **Implementatieverificatie** tabblad.  

3.  Nadat de configuraties die u wilt gebruiken, kiest u **OK** aan de configuratie op te slaan.  

### <a name="see-also"></a>Zie tevens  
 [Sites en hiërarchieën voor System Center Configuration Manager configureren](../../core/servers/deploy/configure/configure-sites-and-hierarchies.md)
