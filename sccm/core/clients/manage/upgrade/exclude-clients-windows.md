---
title: Clientupdates uitsluiten | Windows | System Center Configuration Manager
description: Leer hoe u Windows-clients om uit te sluiten ophalen in System Center Configuration Manager bijgewerkt.
ms.custom: na
ms.date: 04/23/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-client
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 4cd6031f-8844-4d0b-8166-b24d6528a94e
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 690d03d9c8c49a815bd318df549d7401a855bc5d
ms.openlocfilehash: de5602179f3ac55b51133b8280a0143f1b0ff30e
ms.contentlocale: nl-nl
ms.lasthandoff: 05/17/2017


---
# <a name="how-to-exclude-upgrading-clients-for-windows-computers-in-system-center-configuration-manager"></a>Het uitsluiten van upgraden clients voor Windows-computers in System Center Configuration Manager

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*

Vanaf versie 1610, kunt u een verzameling van clients uitsluiten van bijgewerkte clientversies automatisch worden geïnstalleerd. Dit geldt voor automatische upgrade, evenals andere methoden zoals het bijwerken van de software update-gebaseerde, aanmeldingsscripts en Groepsbeleid. U kunt deze gebruiken voor een verzameling van computers die groter voorzichtig moeten bij het upgraden van de client. Een client die zich in een verzameling uitgesloten negeert aanvragen om bijgewerkte clientsoftware te installeren.

## <a name="configure-exclusion-for-automatic-upgrades"></a>Het uitsluiten voor automatische updates configureren

1. Ga in de Configuration Manager-console naar **beheer** > **siteconfiguratie** > **Sites**, en klik vervolgens op **hiërarchie-instellingen**.

2. Klik op de **Clientupgrade** tabblad.

3. Klik op het selectievakje voor **uitsluiten opgegeven clients upgrade**, en selecteer vervolgens de verzameling die u wilt uitsluiten voor uitsluiting-verzameling. U kunt slechts één verzameling voor uitsluiting selecteren.

4.  Klik op **OK** om te sluiten en de configuratie op te slaan. Klik, nadat clients beleid bijwerken, clients in de verzameling uitgesloten wordt niet langer automatisch updates installeren voor de clientsoftware. Zie voor meer informatie [clients voor Windows-computers upgraden](upgrade-clients-for-windows-computers.md).

![Instellingen voor automatische upgrade uitsluiting](media/automatic_upgrade_exclusion.png)



>[!NOTE]
>Hoewel de gebruikersinterface wordt aangegeven dat clients niet worden bijgewerkt via een van deze methoden, zijn er twee methoden die u kunt deze instellingen overschrijven. Client-pushinstallatie en een handmatige clientinstallatie kunnen worden gebruikt om deze configuratie te onderdrukken. Zie de volgende sectie voor meer informatie.

## <a name="how-to-upgrade-a-client-that-is-in-an-excluded-collection"></a>Het bijwerken van een client die zich in een verzameling uitgesloten

Zolang op een verzameling wordt geconfigureerd om te worden uitgesloten, hebben leden van deze verzameling alleen de clientsoftware op een van twee manieren heffen uitsluiting bijgewerkt:
 - **Push-clientinstallatie** – u kunt push-clientinstallatie naar een client bijwerkt die zich in een verzameling met de uitgesloten. Dit is toegestaan omdat deze wordt beschouwd als het uw bedoeling van de beheerder en maakt u om clients te upgraden zonder te verwijderen van de volledige verzameling van uitsluiting.       

 - **Handmatige clientinstallatie** – u kunt clients die zich in een verzameling met de uitgesloten als u de volgende opdrachtregelparameter met ccmsetup handmatig bijwerken: ***/ignoreskipupgrade***

  Als u probeert bij te werken handmatig een client die lid is van de uitgesloten verzameling en gebruik deze switch, zal de client de nieuwe clientsoftware niet installeren. Zie voor meer informatie [handmatig Configuration Manager Clients installeren](/sccm/core/clients/deploy/deploy-clients-to-windows-computers#BKMK_Manual).

Zie voor meer informatie over installatiemethoden voor clients [het implementeren van clients op Windows-computers in System Center Configuration Manager](/sccm/core/clients/deploy/deploy-clients-to-windows-computers).

