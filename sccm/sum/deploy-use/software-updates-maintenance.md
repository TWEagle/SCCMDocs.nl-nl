---

title: Onderhoud van software-updates | Microsoft-documenten
description: Als u wilt behouden updates in Configuration Manager, kunt u de WSUS-opruimactie plannen of kunt u deze handmatig uitvoeren.
keywords: 
author: dougeby
ms.author: dougeby
manager: angrobe
ms.date: 10/06/2016
ms.topic: article
ms.prod: configuration-manager
ms.service: 
ms.technology:
- configmgr-sum
ms.assetid: 4b0e2e90-aac7-4d06-a707-512eee6e576c
ms.translationtype: Machine Translation
ms.sourcegitcommit: e6cf8c799b5be2f7dbb6fadadddf702ec974ae45
ms.openlocfilehash: 1590c623f7bc2f42a8617f110de5321212732a03
ms.contentlocale: nl-nl
ms.lasthandoff: 05/17/2017



---
# <a name="software-updates-maintenance"></a>Onderhoud van software-updates

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*

U kunt plannen en uitvoeren van de WSUS taak opschonen van de Configuration Manager-console of u kunt de WSUS-opruimactie uit handmatig uitvoeren in de eigenschappen van onderdeel Software-updatepunt. Wanneer u de WSUS-opruimtaak selecteert om deze uit te voeren, wordt deze taak uitgevoerd tijdens de volgende synchronisatie van de software-updates. De verouderde software-updates worden ingesteld op de status geweigerd op de WSUS-server en Windows Update Agent op computers scant deze software-updates niet meer. Standaard wordt de WSUS-opruimtaak elke 30 dagen uitgevoerd.  

#### <a name="to-schedule-and-run-the-wsus-cleanup-job"></a>Een WSUS-opschoontaak plannen en uitvoeren  

1.  Navigeer in de Configuration Manager-console naar **beheer** > **overzicht** > **siteconfiguratie** > **Sites**.  

2.  Klik op **Siteonderdelen configureren** in de groep **Instellingen** . Klik vervolgens op **Software-updatepunt** om Eigenschappen van software-updatepuntcomponent te openen.  

3.  Klik op het tabblad **Vervangingsregels** , selecteer **Wizard WSUS-opschoning uitvoeren**en klik op **OK**.

