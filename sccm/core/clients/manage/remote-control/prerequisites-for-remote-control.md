---
title: Vereisten voor beheer op afstand | Microsoft Docs
description: Ophalen van de vereisten voor extern beheer in System Center Configuration Manager.
ms.custom: na
ms.date: 04/23/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: c1b2057e-b74f-43fa-a293-763a8f866d3d
caps.latest.revision: "6"
caps.handback.revision: "0"
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.openlocfilehash: 12c602ddfa237768af497324440091e17e597ae9
ms.sourcegitcommit: 51fc48fb023f1e8d995c6c4eacfda7dbec4d0b2f
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 08/07/2017
---
# <a name="prerequisites-for-remote-control-in-system-center-configuration-manager"></a>Vereisten voor extern beheer in System Center Configuration Manager

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*

Beheer op afstand in System Center Configuration Manager heeft externe afhankelijkheden en afhankelijkheden binnen het product.  

## <a name="dependencies-external-to-configuration-manager"></a>Afhankelijkheden extern aan Configuration Manager  

|Afhankelijkheid|Meer informatie|  
|----------------|----------------------|  
|Videokaartstuurprogramma van de computer|Zorg ervoor dat het meest recente videostuurprogramma is geïnstalleerd op clientcomputers om optimale prestaties van extern beheer te garanderen.|  

 Apparaten waarop Windows Embedded, Windows Embedded voor Point van Service (POS) of Windows Fundamentalss voor Legacy PCs is geïnstalleerd, bieden geen ondersteuning voor de viewer voor extern beheer, maar ze bieden wel ondersteuning voor de client voor extern beheer.  

 Afstandbediening voor Configuration Manager kan niet worden gebruikt voor het extern beheren van clientcomputers met Systems Management Server 2003 of Configuration Manager 2007.  

> [!NOTE]  
>  Er zijn geen Windows-services vereist als een externe afhankelijkheid voor extern beheer.  

### <a name="supported-operating-systems-for-the-remote-control-viewer"></a>Ondersteunde besturingssystemen voor de viewer voor extern beheer  
De viewer voor beheer op afstand wordt ondersteund op alle besturingssystemen die worden ondersteund voor de Configuration Manager-console. Zie voor informatie [ondersteunde configuraties voor System Center Configuration Manager-consoles](../../../../core/plan-design/configs/supported-operating-systems-consoles.md).   

## <a name="configuration-manager-dependencies"></a>Configuration Manager-afhankelijkheden  

|Afhankelijkheid|Meer informatie|  
|----------------|----------------------|  
|Beheer op afstand moet worden ingeschakeld voor clients|Extern beheer is standaard niet ingeschakeld wanneer u Configuration Manager installeert. Zie voor meer informatie over het inschakelen en configureren van beheer op afstand [beheer op afstand configureren in System Center Configuration Manager](../../../../core/clients/manage/remote-control/configuring-remote-control.md).|  
|Reporting Services-punt|De sitesysteemrol Reporting Services-punt moet zijn geïnstalleerd voordat u rapporten kunt uitvoeren voor extern beheer. Zie [Rapportage in System Center Configuration Manager](../../../../core/servers/manage/reporting.md) voor meer informatie.|  
|Beveiligingsmachtigingen voor het beheren van extern beheer|Toegang tot verzamelingsbronnen en het starten van een sessie voor extern beheer van de Configuration Manager-console: **Lees**, **Resource lezen**, en **beheer op afstand** machtiging voor de **verzameling** object.<br /><br /> De **Operator voor externe hulpprogramma's voor** beveiligingsrol bevat deze machtigingen die nodig zijn voor het beheren van extern beheer in Configuration Manager.<br /><br /> Zie voor meer informatie [beheer op basis van rollen voor System Center Configuration Manager configureren](../../../../core/servers/deploy/configure/configure-role-based-administration.md).<br /><br /> Toegelaten viewers moeten bovendien de gegeven toestemming voor het gebruik van beheer op afstand door deze gebruikers toevoegen aan de **toegelaten viewers van beheer op afstand en hulp op afstand** lijst de **externe hulpprogramma's** clientinstellingen.
