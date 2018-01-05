---
title: 'Upgrade van de lange termijn onderhoud vertakking naar de huidige vertakking '
titleSuffix: Configuration Manager
description: Informatie over het converteren van een filiaalsite Long-Term onderhoud naar een Current Branch-site.
ms.custom: na
ms.date: 2/8/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: ec5b54cf-62b7-4ed1-9bb3-e8c63b9641c8
caps.latest.revision: "0"
author: aczechowski
ms.author: aaroncz
manager: angrobe
ms.openlocfilehash: 8adc118643cdc9bb4db8226b6d5c5f14a20898a4
ms.sourcegitcommit: ca9d15dfb1c9eb47ee27ea9b5b39c9f8cdcc0748
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 01/04/2018
---
# <a name="upgrade-the-long-term-servicing-branch-to-the-current-branch"></a>Upgrade van de lange termijn onderhoud vertakking naar de huidige vertakking

*Van toepassing op: System Center Configuration Manager (op lange termijn onderhoud vertakking)*

Gebruik dit onderwerp voor informatie over het upgraden van (omzetten), een site en hiërarchie waarop de Long-Term Servicing Branch (LTSB) van Configuration Manager uitgevoerd naar de huidige vertakking.

Wanneer u een huidige Software Assurance-overeenkomst (of vergelijkbaar licentierechten) die verleent u rechten voor het gebruik van de huidige vertakking hebt, kunt u de installatie van de LTSB converteren naar de huidige vertakking.  Dit is een eenzijdige conversie omdat er geen ondersteuning is voor het converteren van een site van de huidige vertakking naar de LTSB.

Als u meerdere sites hebt, hoeft u alleen de bovenste site van uw hiërarchie te converteren. Nadat de bovenste site is geconverteerd:
- Onderliggende primaire sites automatisch worden geconverteerd.
-   U moet secundaire sites uit binnen de Configuration Manager-console handmatig bijwerken.

## <a name="run-setup-to-convert-the-long-term-servicing-branch"></a>Setup uitvoeren om te converteren van de vertakking Long-Term onderhoud
Op de bovenste site van uw hiërarchie, kunt u setup van Configuration Manager niet in aanmerking komt basislijnmedia uitvoeren en selecteer **Site-onderhoud**.  Wanneer met de licentiegegevens pagina weergegeven, klikt u vervolgens de optie voor de huidige vertakking en voltooi de wizard.

Als uw site is geconverteerd naar de huidige vertakking, eerder zijn niet-beschikbare functies en mogelijkheden beschikbaar voor gebruik.

> [!NOTE]  
> In aanmerking komende basislijnmedia is een medium met een versie die gelijk is aan of later zijn dan de LTSB-installatie.

Bijvoorbeeld, omdat de LTSB is gebaseerd op versie 1606, u niet gebruiken de basislijnmedia 1511 converteren naar de huidige vertakking. In plaats daarvan u het installatieprogramma uitvoeren vanaf de dezelfde versie 1606 basislijnmedia die u gebruikt voor het installeren van de LTSB-site en kiest u de optie Licentieverlening voor de huidige vertakking.  Ook als een hoger basislijn van de huidige vertakking is vrijgegeven, kunt u setup uitvoeren vanaf die basislijnmedia.

Zie voor een lijst van basislijnversies **basislijn- en updateversies** in [Updates voor Configuration Manager](/sccm/core/servers/manage/updates).

## <a name="use-the-configuration-manager-console-to-convert-the-long-term-servicing-branch"></a>De Configuration Manager-console gebruiken voor het converteren van de lange termijn onderhoud vertakking
Als uw site wordt uitgevoerd de LTSB, kunt u de volgende optie in de Configuration Manager-console gebruiken om te converteren naar de huidige vertakking:

 1. Ga in de console naar **beheer** > **siteconfiguratie** > **Sites**, en open vervolgens **hiërarchie-instellingen**.  

 2. Selecteer de optie voor het converteren naar de huidige vertakking en kies vervolgens **toepassen**.  

Als uw site is geconverteerd naar de huidige vertakking, eerder zijn niet-beschikbare functies en mogelijkheden beschikbaar voor gebruik.
