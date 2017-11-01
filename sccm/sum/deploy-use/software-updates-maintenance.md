---
title: Onderhoud voor software-updates
titleSuffix: Configuration Manager
description: Om te blijven van updates in Configuration Manager, kunt u de WSUS-opschoontaak plannen of kunt u deze handmatig uitvoeren.
keywords: 
author: dougeby
ms.author: dougeby
manager: angrobe
ms.date: 10/06/2016
ms.topic: article
ms.prod: configuration-manager
ms.service: 
ms.technology: configmgr-sum
ms.assetid: 4b0e2e90-aac7-4d06-a707-512eee6e576c
ms.openlocfilehash: 51e103b09ced9916fc76f9c87654379b538248b4
ms.sourcegitcommit: c236214b2fcc13dae7bad96d7fb33f692868191d
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/12/2017
---
# <a name="software-updates-maintenance"></a>Onderhoud voor software-updates

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*

U kunt plannen en uitvoeren van de WSUS opschoontaak uit de Configuration Manager-console of u kunt de WSUS-opschoontaak van handmatig uitvoeren in de eigenschappen van Software-Updatepuntcomponenten. Wanneer u de WSUS-opruimtaak selecteert om deze uit te voeren, wordt deze taak uitgevoerd tijdens de volgende synchronisatie van de software-updates. De verouderde software-updates worden ingesteld op de status geweigerd op de WSUS-server en Windows Update Agent op computers scant deze software-updates niet meer. Standaard wordt de WSUS-opruimtaak elke 30 dagen uitgevoerd.  

#### <a name="to-schedule-and-run-the-wsus-cleanup-job"></a>Een WSUS-opschoontaak plannen en uitvoeren  

1.  Navigeer in de Configuration Manager-console naar **beheer** > **overzicht** > **siteconfiguratie** > **Sites**.  

2.  Klik op **Siteonderdelen configureren** in de groep **Instellingen** . Klik vervolgens op **Software-updatepunt** om Eigenschappen van software-updatepuntcomponent te openen.  

3.  Klik op het tabblad **Vervangingsregels** , selecteer **Wizard WSUS-opschoning uitvoeren**en klik op **OK**.
