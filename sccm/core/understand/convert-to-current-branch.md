---
title: De lange termijn servicing vertakking bijwerken naar de huidige vertakking | Microsoft-documenten
description: Leer hoe u een site langetermijndoelen onderhoud vertakking converteren naar een vertakking van huidige site.
ms.custom: na
ms.date: 2/8/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: ec5b54cf-62b7-4ed1-9bb3-e8c63b9641c8
caps.latest.revision: 0
author: Brenduns
ms.author: brenduns
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 60631bc0346bd78d704e7129bb755af504c59b1b
ms.openlocfilehash: 6e7edc85630d22c5bbba1ff66bd1199903db76db
ms.contentlocale: nl-nl
ms.lasthandoff: 05/17/2017

---


# <a name="upgrade-the-long-term-servicing-branch-to-the-current-branch"></a>De lange termijn servicing vertakking bijwerken naar de huidige vertakking

*Van toepassing op: System Center Configuration Manager (op lange termijn onderhoud vertakking)*

Gebruik dit onderwerp voor meer informatie over het bijwerken van (omzetten) een site en hiërarchie met de langetermijndoelen onderhoud vertakking (LTSB) van Configuration Manager naar de huidige vertakking.

Wanneer u een huidige Software Assurance-overeenkomst (of soortgelijke licentieverlening rechten) die verleent u rechten voor het gebruik van de huidige vertakking hebt, kunt u uw installatie van de LTSB converteren naar de huidige vertakking.  Dit is een eenzijdige conversie omdat er geen ondersteuning voor het converteren van een huidige vertakking site naar de LTSB.

Als u meerdere sites hebt, hoeft u alleen de bovenste site van uw hiërarchie te converteren. Nadat de site op hoogste niveau is geconverteerd:
- Onderliggende primaire sites automatisch worden geconverteerd.
-    Secundaire sites van in de Configuration Manager-console, moet u handmatig bijwerken.

## <a name="run-setup-to-convert-the-long-term-servicing-branch"></a>Voer setup uit om de vertakking langetermijndoelen onderhoud converteren
Op de site op hoogste niveau van uw hiërarchie, kunt u Configuration Manager-installaties uitvoeren van in aanmerking komende basislijn media en selecteer **Site-onderhoud**.  Vervolgens krijgt de licentiegegevens pagina, selecteer de optie voor de huidige vertakking en voltooi de wizard.

Als uw site is geconverteerd naar de huidige vertakking, eerder zijn niet-beschikbare functies en mogelijkheden beschikbaar voor gebruik.

> [!NOTE]  
> In aanmerking komende basislijn media is een media met een versie die gelijk is aan of later zijn dan de LTSB-installatie.

Bijvoorbeeld, omdat de LTSB is gebaseerd op versie 1606, u niet gebruiken de basislijn 1511 media converteren naar de huidige vertakking. In plaats daarvan kunt u setup uitvoert vanaf de dezelfde versie 1606 basislijn media die u gebruikt voor het installeren van de site LTSB en kiest u de optie Licentieverlening voor de huidige vertakking.  Als een hoger basislijn van de huidige vertakking is vrijgegeven, kunt u ook installatie uitvoeren vanaf deze media basislijn.

Zie voor een lijst van basislijn versies **basislijn en update versies** in [Updates voor Configuration Manager](/sccm/core/servers/manage/updates).

## <a name="use-the-configuration-manager-console-to-convert-the-long-term-servicing-branch"></a>Gebruik de Configuration Manager-console op de lange termijn servicing vertakking converteren
Als uw site wordt uitgevoerd de LTSB, kunt u de volgende optie in de Configuration Manager-console om te converteren naar de huidige vertakking wordt weergegeven:

 1. In de console, gaat u naar **beheer** > **siteconfiguratie** > **Sites**, en open vervolgens **hiërarchie-instellingen**.  

 2. Selecteer de optie om te converteren naar de huidige vertakking en kies **toepassen**.  

Als uw site is geconverteerd naar de huidige vertakking, eerder zijn niet-beschikbare functies en mogelijkheden beschikbaar voor gebruik.

