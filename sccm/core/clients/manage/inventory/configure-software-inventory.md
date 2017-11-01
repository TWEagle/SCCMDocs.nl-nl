---
title: Software-inventaris configureren
titleSuffix: Configuration Manager
description: Software-inventaris configureren en mappen uitsluiten van software-inventarisatie in Configuration Manager.
ms.custom: na
ms.date: 02/22/2017
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
ms.openlocfilehash: 3aac8bdf45a90f0c9c734d2f796e590e5dc9b90e
ms.sourcegitcommit: c236214b2fcc13dae7bad96d7fb33f692868191d
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/12/2017
---
# <a name="how-to-configure-software-inventory-in-system-center-configuration-manager"></a>Het configureren van software-inventaris in System Center Configuration Manager

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*

 Met deze procedure configureert u de standaardinstellingen voor de software-inventarisatie die voor alle computers in uw hiërarchie geldt. Als u wilt dat deze instellingen toepassen op alleen op enkele computers, maakt een aangepaste apparaatclientinstelling en deze toewijzen aan een verzameling waartoe de computers die u wilt gebruiken, software-inventaris. Zie voor meer informatie over het maken van aangepaste apparaatinstellingen [het configureren van clientinstellingen in System Center Configuration Manager](../../../../core/clients/deploy/configure-client-settings.md).  

## <a name="to-configure-software-inventory"></a>De software-inventarisatie configureren  

1.  Kies in de Configuration Manager-console **beheer** > **clientinstellingen****Standaardclientinstellingen**.  

4.  Op de **Start** tabblad, in de **eigenschappen** groep, kiest u **eigenschappen**.  

5.  In de **standaardinstellingen** dialoogvenster Kies **Software-inventaris**.  

6.  Configureer de volgende waarden in de lijst **Apparaatinstellingen** :  

    -   **Software-inventaris op clients inschakelen** - Selecteer in de vervolgkeuzelijst, selecteer **True**.  

    -   **Planning software-inventaris en de bestandsnaam verzameling schema** : Hiermee configureert u het interval op welke clients verzamelen software-inventaris en bestanden.   

7.  Configureer de clientinstellingen die u nodig hebt. Zie voor een lijst met clientinstellingen voor software-inventaris die u kunt configureren, de [Software-inventaris](../../../../core/clients/deploy/about-client-settings.md#software-inventory) sectie het [over clientinstellingen in System Center Configuration Manager](../../../../core/clients/deploy/about-client-settings.md) onderwerp.  

 Clientcomputers zullen worden geconfigureerd met deze instellingen wanneer ze de volgende keer het clientbeleid downloaden. Raadpleeg [Clients beheren in System Center Configuration Manager](../../../../core/clients/manage/manage-clients.md) voor informatie over het initiëren van het ophalen van beleid voor één client.  


## <a name="to-exclude-folders-from-software-inventory"></a>Mappen uitsluiten van software-inventaris  

1.  Met behulp van Notepad.exe maakt u een leeg bestand met de naam **Skpswi.dat**.  

2.  Klik met de rechtermuisknop het bestand **Skpswi.dat** en klik op **Eigenschappen**. Selecteer in de eigenschappen van het bestand Skpswi.dat het kenmerk **Verborgen** .  

3.  Plaats het bestand **Skpswi.dat** in de hoofdmap van elke harde schijf van een client of elke mapstructuur die u wilt uitsluiten van software-inventaris.  

> [!NOTE]  
>  Met software-inventaris wordt het station van de client niet opnieuw geïnventariseerd tenzij dit bestand wordt verwijderd uit het station op de clientcomputer.