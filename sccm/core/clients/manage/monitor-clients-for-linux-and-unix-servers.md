---
title: Clients voor Linux/UNIX - Configuration Manager controleren | Microsoft Docs
description: Clients op Linux en UNIX-servers in System Center Configuration Manager controleren.
ms.custom: na
ms.date: 08/04/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: configmgr-client
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: d827cf91-b18f-4ee7-b538-24ba6f003ab9
caps.latest.revision: "6"
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.openlocfilehash: 62843bd544217734c4566d656a7c3a35bd5613cb
ms.sourcegitcommit: 51fc48fb023f1e8d995c6c4eacfda7dbec4d0b2f
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 08/07/2017
---
# <a name="how-to-monitor-clients-for-linux-and-unix-servers-in-system-center-configuration-manager"></a>Clients controleren voor Linux- en UNIX-servers in System Center Configuration Manager

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*

U kunt gegevens van Linux en UNIX-servers weergeven in de System Center Configuration Manager-console met dezelfde methoden die u gebruikt om informatie van Windows-clients weer te geven.  

 U kunt de volgende gegevens bekijken:  

-   Details van status van clients in de console-dashboards voor Configuration Manager  

-   Gegevens over de clients in de standaard Configuration Manager-rapporten  

-   Inventarisgegevens in Resource Explorer  

 De volgende secties wordt beschreven hoe deze gegevens ophalen van de resource explorer en rapporten.  

##  <a name="BKMK_UseResourceExpforLnU"></a>Resource explorer gebruiken om de inventaris voor Linux en UNIX-servers te bekijken  

 Nadat een Configuration Manager-client verzendt een hardware-inventaris naar de Configuration Manager-site, kunt u Resource Explorer gebruiken om deze informatie weer te geven. Configuration Manager-client voor Linux en UNIX voegt geen nieuwe klassen of weergaven voor inventaris aan Resource Explorer. De Linux- en UNIX-inventarisgegevens zijn gekoppeld aan bestaande WMI-klassen. U kunt de inventarisgegevens voor Linux- en UNIX-servers met Resource Explorer bekijken in de Windows-classificaties.  

 U kunt bijvoorbeeld de lijst met alle systeemeigen geïnstalleerde programma's op uw Linux- en UNIX-servers verzamelen. Voorbeelden van systeemeigen geïnstalleerde programma's zijn **.rpms** in Linux of **.pkgs** in Solaris. Nadat de inventarisatie is verzonden door een Linux- of UNIX-client, kunt u de lijst met alle systeemeigen geïnstalleerde Linux of UNIX-programma's in Resource Explorer bekijken in de Configuration Manager-console.  

 Zie voor meer informatie over het gebruik van Resource Explorer [Resource Explorer gebruiken om hardware-inventaris in System Center Configuration Manager weer te geven](../../../core/clients/manage/inventory/use-resource-explorer-to-view-hardware-inventory.md).  

##  <a name="BKMK_UseReportsforLnU"></a> Rapporten gebruiken om gegevens over Linux- en UNIX-servers te bekijken  
 Voor Configuration Manager-rapporten bevatten informatie van Linux en UNIX-servers samen met informatie van Windows-computers. Er zijn geen aanvullende configuraties nodig om de Linux- en UNIX-gegevens in de rapporten te integreren.  

 Als u bijvoorbeeld het rapport met de naam Aantal besturingssysteemversies uitvoert, wordt er een lijst weergegeven met de verschillende besturingssystemen en het aantal clients waarop elk besturingssysteem wordt uitgevoerd. Het rapport is gebaseerd op de hardware-inventarisatie-informatie die is verzonden door de verschillende Configuration Manager-clients die worden uitgevoerd op verschillende besturingssystemen.  

 Het is ook mogelijk om aangepaste rapporten te maken die specifiek zijn ontworpen voor Linux- en UNIX-servergegevens. De eigenschap **Bijschrift** van de hardware-inventarisklasse **Besturingssysteem** is een nuttig kenmerk waarmee u de specifieke besturingssystemen kunt aangeven in de rapportquery.  

 Zie voor meer informatie over rapporten in Configuration Manager [rapportage in System Center Configuration Manager](../../../core/servers/manage/reporting.md).  
