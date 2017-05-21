---
title: Vereisten voor beheer op afstand | Microsoft-documenten
description: De vereisten voor beheer op afstand in System Center Configuration Manager opgehaald.
ms.custom: na
ms.date: 04/23/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: c1b2057e-b74f-43fa-a293-763a8f866d3d
caps.latest.revision: 6
caps.handback.revision: 0
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 690d03d9c8c49a815bd318df549d7401a855bc5d
ms.openlocfilehash: e08bca886dfc0730ab45ab899754394ae61335e3
ms.contentlocale: nl-nl
ms.lasthandoff: 05/17/2017


---
# <a name="prerequisites-for-remote-control-in-system-center-configuration-manager"></a>Vereisten voor beheer op afstand in System Center Configuration Manager

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*

Beheer op afstand in System Center Configuration Manager heeft externe afhankelijkheden en afhankelijkheden binnen het product.  

## <a name="dependencies-external-to-configuration-manager"></a>Afhankelijkheden extern aan Configuration Manager  

|Afhankelijkheid|Meer informatie|  
|----------------|----------------------|  
|Videokaartstuurprogramma van de computer|Zorg ervoor dat het meest recente videostuurprogramma is geïnstalleerd op clientcomputers om optimale prestaties van extern beheer te garanderen.|  

 Apparaten waarop Windows Embedded, Windows Embedded voor Point van Service (POS) of Windows Fundamentalss voor Legacy PCs is geïnstalleerd, bieden geen ondersteuning voor de viewer voor extern beheer, maar ze bieden wel ondersteuning voor de client voor extern beheer.  

 Beheer op afstand Configuration Manager kan niet worden gebruikt voor het extern beheren van clientcomputers met Systems Management Server 2003 of Configuration Manager 2007.  

> [!NOTE]  
>  Er zijn geen Windows-services vereist als een externe afhankelijkheid voor extern beheer.  

### <a name="supported-operating-systems-for-the-remote-control-viewer"></a>Ondersteunde besturingssystemen voor de viewer voor extern beheer  
 De volgende tabel bevat informatie over de ondersteunde besturingssystemen voor de viewer voor extern bheer. Zie voor meer informatie over ondersteunde clientbesturingssystemen [ondersteunde configuraties voor System Center Configuration Manager](../../../../core/plan-design/configs/supported-configurations.md).  

|Besturingssysteem|Viewer-ondersteuning|Meer informatie|  
|----------------------|--------------------|----------------------|  
|Windows XP (32-bits)|Ja|Beheer op afstand viewer op dit besturingssysteem worden uitgevoerd, moet u eerst downloaden en installeren van de [Remote Desktop Connection (RDC)-client-update (KB969084) 7.0](https://www.microsoft.com/en-us/download/details.aspx?id=12767) via het Microsoft Download Center.|  
|Windows XP (64-bits)|Nee|Geen aanvullende informatie.|  
|Windows Vista (32-bits)|Ja|Beheer op afstand viewer op dit besturingssysteem worden uitgevoerd, moet u eerst downloaden en installeren van de [Remote Desktop Connection (RDC)-client-update (KB969084) 7.0](https://www.microsoft.com/en-us/download/details.aspx?id=12767) via het Microsoft Download Center.|  
|Windows Vista (64-bits)|Ja|Beheer op afstand viewer op dit besturingssysteem worden uitgevoerd, moet u eerst downloaden en installeren van de [Remote Desktop Connection (RDC)-client-update (KB969084) 7.0](https://www.microsoft.com/en-us/download/details.aspx?id=12767) via het Microsoft Download Center.|  
|Windows 7 (32-bits)|Ja|Geen aanvullende informatie.|  
|Windows 7 (64-bits)|Ja|Geen aanvullende informatie.|  
|Windows Server 2003 (32-bits)|Nee|Geen aanvullende informatie.|  
|Windows Server 2003 (64-bits)|Nee|Geen aanvullende informatie.|  
|Windows Server 2008 (32-bits)|Nee|Geen aanvullende informatie.|  
|Windows Server 2008 (64-bits)|Nee|Geen aanvullende informatie.|  
|Windows Server 2008 R2 (64-bits)|Ja|Geen aanvullende informatie.|  

## <a name="configuration-manager-dependencies"></a>Configuration Manager-afhankelijkheden  

|Afhankelijkheid|Meer informatie|  
|----------------|----------------------|  
|Beheer op afstand moet worden ingeschakeld voor clients|Beheer op afstand is standaard niet ingeschakeld wanneer u Configuration Manager installeert. Zie voor meer informatie over het inschakelen en configureren van beheer op afstand [beheer op afstand configureren in System Center Configuration Manager](../../../../core/clients/manage/remote-control/configuring-remote-control.md).|  
|Reporting Services-punt|De sitesysteemrol Reporting Services-punt moet zijn geïnstalleerd voordat u rapporten kunt uitvoeren voor extern beheer. Zie [Rapportage in System Center Configuration Manager](../../../../core/servers/manage/reporting.md) voor meer informatie.|  
|Beveiligingsmachtigingen voor het beheren van extern beheer|Voor toegang tot resources verzamelen en om een sessie beheer op afstand van de Configuration Manager-console te initiëren: **AMT beheren**, **lezen**, **Resource lezen**, en **beheer op afstand** machtiging voor het **verzameling** object.<br /><br /> De **Operator voor externe hulpprogramma's** beveiligingsrol bevat deze machtigingen die vereist zijn voor het beheren van beheer op afstand in Configuration Manager.<br /><br /> Zie voor meer informatie [op rollen gebaseerd beheer voor System Center Configuration Manager configureert](../../../../core/servers/deploy/configure/configure-role-based-administration.md).<br /><br /> Bovendien moet u gebruikers aan wie u machtigingen wilt verlenen voor het gebruik van extern beheer en hulp op afstand toevoegen aan de lijst met toegestane weergaven van extern beheer met behulp van de optie toevoegen **Toegelaten viewers van Beheer op afstand en Hulp op afstand** in de clientinstellingen **Externe hulpprogramma's** .|  

