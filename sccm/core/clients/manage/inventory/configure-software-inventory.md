---
title: Software-inventaris configureren
titleSuffix: Configuration Manager
description: Software-inventaris configureren en mappen uitsluiten van software-inventarisatie in Configuration Manager.
ms.custom: na
ms.date: 01/03/2018
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: configmgr-other
ms.tgt_pltfrm: na
ms.topic: get-started-article
ms.assetid: f86559de-092a-4ce8-9b43-5d7530e0b763
caps.latest.revision: "5"
caps.handback.revision: "0"
author: andredm7
ms.author: andredm
manager: angrobe
ms.openlocfilehash: afddcef2caab6e1af0aacdac91366fa430f21d85
ms.sourcegitcommit: ca9d15dfb1c9eb47ee27ea9b5b39c9f8cdcc0748
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 01/04/2018
---
# <a name="how-to-configure-software-inventory-in-system-center-configuration-manager"></a>Het configureren van software-inventaris in System Center Configuration Manager

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*

Deze procedure configureert u de standaardclientinstellingen voor software-inventaris en van toepassing op alle computers in uw hiërarchie. Als u wilt dat deze instellingen toepassen op alleen op enkele computers, maakt een aangepaste apparaatclientinstelling en wijst deze toe aan een verzameling. Zie voor meer informatie over het maken van aangepaste apparaatinstellingen [het configureren van clientinstellingen in System Center Configuration Manager](../../../../core/clients/deploy/configure-client-settings.md).   

## <a name="to-configure-software-inventory"></a>De software-inventarisatie configureren  

1.  Kies in de Configuration Manager-console **beheer** > **clientinstellingen****Standaardclientinstellingen**.  

4.  Op de **Start** tabblad, in de **eigenschappen** groep, kiest u **eigenschappen**.  

5.  In de **standaardinstellingen** dialoogvenster Kies **Software-inventaris**.  

6.  Configureer de volgende waarden in de lijst **Apparaatinstellingen** :  

    -   **Software-inventaris op clients inschakelen** - Selecteer in de vervolgkeuzelijst, selecteer **True**.  

    -   **Planning software-inventaris en de bestandsnaam verzameling schema** : Hiermee configureert u het interval op welke clients verzamelen software-inventaris en bestanden.   

7.  Configureer de clientinstellingen die u nodig hebt. De [Software-inventaris](../../../../core/clients/deploy/about-client-settings.md#software-inventory) sectie van de [over clientinstellingen in System Center Configuration Manager](../../../../core/clients/deploy/about-client-settings.md) artikel bevat een lijst met instellingen voor de client.  

 Clientcomputers zullen worden geconfigureerd met deze instellingen wanneer ze de volgende keer het clientbeleid downloaden. Raadpleeg [Clients beheren in System Center Configuration Manager](../../../../core/clients/manage/manage-clients.md) voor informatie over het initiëren van het ophalen van beleid voor één client.  

 > [!TIP]  
        >   Foutcode 80041006 in inventoryprovider.log betekent dat de WMI-provider heeft te weinig geheugen. Dat wil zeggen, de quotalimiet geheugen voor een provider is bereikt en inventarisprovider kan niet worden voortgezet.
In dit geval maakt de inventarisagent een rapport met 0 vermeldingen dus geen inventarisitems worden gerapporteerd. <br/>
Een mogelijke oplossing voor deze fout kan zijn op het bereik van de software-inventarisatie-verzameling te beperken. In het geval als de fout optreedt nadat het beperken van het bereik inventaris, uitbreiding van de [MemoryPerHost](https://blogs.technet.microsoft.com/askperf/2008/09/16/memory-and-handle-quotas-in-the-wmi-provider-service/) -eigenschap worden gedefinieerd de [_ProviderHostQuotaConfiguration](https://msdn.microsoft.com/library/aa394671) klasse kunt bieden een oplossing.

<!--SMS.480648 include WMI Out of memory tip -->


## <a name="to-exclude-folders-from-software-inventory"></a>Mappen uitsluiten van software-inventaris  

1.  Met behulp van Notepad.exe maakt u een leeg bestand met de naam **Skpswi.dat**.  

2.  Met de rechtermuisknop op de **Skpswi.dat** -bestand en klik op **eigenschappen**. Selecteer in de eigenschappen van het bestand Skpswi.dat het kenmerk **Verborgen** .  

3.  Plaats het bestand **Skpswi.dat** in de hoofdmap van elke harde schijf van een client of elke mapstructuur die u wilt uitsluiten van software-inventaris.  

> [!NOTE]  
>  Met software-inventaris wordt het station van de client niet opnieuw geïnventariseerd tenzij dit bestand wordt verwijderd uit het station op de clientcomputer.