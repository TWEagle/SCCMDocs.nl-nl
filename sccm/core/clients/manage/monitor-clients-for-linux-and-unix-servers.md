---
title: Linux/UNIX-clients - Configuration Manager controleren | Microsoft-documenten
description: Clients op Linux en UNIX-servers in System Center Configuration Manager controleren.
ms.custom: na
ms.date: 04/23/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-client
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: d827cf91-b18f-4ee7-b538-24ba6f003ab9
caps.latest.revision: 6
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 690d03d9c8c49a815bd318df549d7401a855bc5d
ms.openlocfilehash: d6478fa75c27e07e22702f3f8d5577df73ebdd48
ms.contentlocale: nl-nl
ms.lasthandoff: 05/17/2017


---
# <a name="how-to-monitor-clients-for-linux-and-unix-servers-in-system-center-configuration-manager"></a>Clients controleren voor Linux- en UNIX-servers in System Center Configuration Manager

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*

U kunt informatie weergeven vanaf Linux en UNIX-servers in de System Center Configuration Manager-console dezelfde methoden te gebruiken kunt u gegevens uit Windows gebaseerde clients weergeven.  

 U kunt de volgende gegevens bekijken:  

-   Details van de status van clients in de Configuration Manager-console dashboards  

-   Meer informatie over de clients in de standaard Configuration Manager-rapporten  

-   Inventarisgegevens in Resource Explorer  

 De volgende secties wordt beschreven hoe u deze gegevens ophalen uit de resource explorer en rapporten.  

##  <a name="BKMK_UseResourceExpforLnU"></a>Resource explorer gebruikt om inventaris voor Linux en UNIX-servers weer te geven  

 Nadat een Configuration Manager-client zijn verzonden hardware-inventaris naar de Configuration Manager-site, kunt u Resource Explorer gebruiken om deze informatie weer te geven. Configuration Manager-client voor Linux en UNIX wordt geen nieuwe klassen of weergaven voor inventarisatie toegevoegd aan de Resource Explorer. De Linux- en UNIX-inventarisgegevens zijn gekoppeld aan bestaande WMI-klassen. U kunt de inventarisgegevens voor Linux- en UNIX-servers met Resource Explorer bekijken in de Windows-classificaties.  

 U kunt bijvoorbeeld de lijst met alle systeemeigen geïnstalleerde programma's op uw Linux- en UNIX-servers verzamelen. Voorbeelden van systeemeigen geïnstalleerde programma's zijn **.rpms** in Linux of **.pkgs** in Solaris. Nadat de inventarisatie is verzonden door een client voor Linux of UNIX, kunt u de lijst met alle systeemeigen geïnstalleerde Linux of UNIX-programma's in Resource Explorer weergeven in de Configuration Manager-console.  

 Zie voor meer informatie over het gebruik van de Resource Explorer [Resource Explorer gebruiken om te bekijken van hardware-inventaris in System Center Configuration Manager](../../../core/clients/manage/inventory/use-resource-explorer-to-view-hardware-inventory.md).  

##  <a name="BKMK_UseReportsforLnU"></a> Rapporten gebruiken om gegevens over Linux- en UNIX-servers te bekijken  
 Voor Configuration Manager-rapporten bevatten informatie van Linux en UNIX-servers samen met gegevens van Windows-computers. Er zijn geen aanvullende configuraties nodig om de Linux- en UNIX-gegevens in de rapporten te integreren.  

 Als u bijvoorbeeld het rapport met de naam Aantal besturingssysteemversies uitvoert, wordt er een lijst weergegeven met de verschillende besturingssystemen en het aantal clients waarop elk besturingssysteem wordt uitgevoerd. Het rapport is gebaseerd op de hardware-inventarisatie-informatie die is verzonden door de andere Configuration Manager-clients die op verschillende besturingssystemen worden uitgevoerd.  

 Het is ook mogelijk om aangepaste rapporten te maken die specifiek zijn ontworpen voor Linux- en UNIX-servergegevens. De eigenschap **Bijschrift** van de hardware-inventarisklasse **Besturingssysteem** is een nuttig kenmerk waarmee u de specifieke besturingssystemen kunt aangeven in de rapportquery.  

 Zie voor meer informatie over rapporten in Configuration Manager [rapportage in System Center Configuration Manager](../../../core/servers/manage/reporting.md).  

