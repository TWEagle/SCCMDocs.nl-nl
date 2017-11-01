---
title: Clientupgrades voor Windows uitsluiten
titleSuffix: Configuration Manager
description: Informatie over het uitsluiten van Windows-clients ophalen in System Center Configuration Manager bijgewerkt.
ms.custom: na
ms.date: 04/23/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: configmgr-client
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 4cd6031f-8844-4d0b-8166-b24d6528a94e
author: arob98
ms.author: angrobe
manager: angrobe
ms.openlocfilehash: 6069812d8d120f65ad79344efc3eeaa219066859
ms.sourcegitcommit: c236214b2fcc13dae7bad96d7fb33f692868191d
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/12/2017
---
# <a name="how-to-exclude-upgrading-clients-for-windows-computers-in-system-center-configuration-manager"></a>Het uitsluiten van de upgrade van clients voor Windows-computers in System Center Configuration Manager

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*

Vanaf versie 1610, kunt u een verzameling van clients uitsluiten van automatisch installeren van versies van de bijgewerkte client. Dit geldt voor de automatische upgrade, evenals andere methoden, zoals software-update-gebaseerde upgrade aanmeldingsscripts en Groepsbeleid. U kunt deze gebruiken voor een verzameling van computers die moeten worden groter voorzichtig bij het upgraden van de client. Een client die zich in een uitgesloten verzameling negeert aanvragen om bijgewerkte clientsoftware te installeren.

## <a name="configure-exclusion-for-automatic-upgrades"></a>Uitsluiting voor automatische updates configureren

1. Ga in de Configuration Manager-console naar **beheer** > **siteconfiguratie** > **Sites**, en klik vervolgens op **hiërarchie-instellingen**.

2. Klik op de **Clientupgrade** tabblad.

3. Klik op het selectievakje voor **uitsluiten opgegeven clients upgrade**, en selecteer vervolgens de verzameling die u wilt uitsluiten voor uitsluiting-verzameling. U kunt slechts één verzameling voor uitsluiting selecteren.

4.  Klik op **OK** te sluiten en de configuratie op te slaan. Vervolgens, nadat clients beleid bijwerken, clients in de uitgesloten verzameling wordt niet langer automatisch updates installeren voor de clientsoftware. Zie voor meer informatie [clients voor Windows-computers bijwerken](upgrade-clients-for-windows-computers.md).

![Instellingen voor uitsluiting van Automatische upgrade](media/automatic_upgrade_exclusion.png)



>[!NOTE]
>Hoewel de gebruikersinterface wordt aangegeven dat clients niet worden bijgewerkt via een van deze methoden, zijn er twee methoden die u kunt deze instellingen overschrijven. Client-pushinstallatie en een handmatige clientinstallatie kunnen worden gebruikt voor het onderdrukken van deze configuratie. Zie de volgende sectie voor meer informatie.

## <a name="how-to-upgrade-a-client-that-is-in-an-excluded-collection"></a>Een client die zich in een uitgesloten verzameling bijwerken

Zolang een verzameling is geconfigureerd om te worden uitgesloten, kunnen leden van de verzameling alleen hun bijgewerkt door een van twee methoden, deze de uitsluiting van de heffen clientsoftware hebben:
 - **Push-clientinstallatie** – u kunt push-clientinstallatie naar een client bijwerkt die zich in een uitgesloten verzameling. Dit is toegestaan als het wordt beschouwd als de bedoeling van de beheerder en kunt u clients bijwerken zonder de volledige verzameling worden verwijderd uit uitsluiting.       

 - **Handmatige clientinstallatie** – u kunt clients die zich in een uitgesloten verzameling als u de volgende opdrachtregel-switch met ccmsetup handmatig bijwerken: ***/ignoreskipupgrade***

  Als u probeert bij te werken handmatig een client die lid is van de uitgesloten verzameling en gebruik deze schakeloptie niet, wordt de client de nieuwe clientsoftware niet installeren. Zie voor meer informatie [Configuration Manager-Clients handmatig installeren](/sccm/core/clients/deploy/deploy-clients-to-windows-computers#BKMK_Manual).

Zie voor meer informatie over clientinstallatiemethoden [clients implementeren op Windows-computers in System Center Configuration Manager](/sccm/core/clients/deploy/deploy-clients-to-windows-computers).
