---
title: Vereisten voor rapportage | Microsoft Docs
description: Inzicht in verschillende afhankelijkheden die van invloed zijn op uw gebruik van rapportage in System Center Configuration Manager.
ms.custom: na
ms.date: 10/06/2016
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: configmgr-other
ms.tgt_pltfrm: na
ms.topic: get-started-article
ms.assetid: 9cc508a5-5023-4833-b776-ae9a6971138f
caps.latest.revision: "5"
caps.handback.revision: "0"
author: Dougeby
ms.author: dougeby
manager: angrobe
ms.openlocfilehash: 2e624eb2ea061a4eb7d92365410fada335640224
ms.sourcegitcommit: 51fc48fb023f1e8d995c6c4eacfda7dbec4d0b2f
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 08/07/2017
---
# <a name="prerequisites-for-reporting-in-system-center-configuration-manager"></a>Vereisten voor rapportage in System Center Configuration Manager

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*

Rapportage in System Center Configuration Manager heeft externe afhankelijkheden en afhankelijkheden binnen het product.  

## <a name="dependencies-external-to-configuration-manager"></a>Afhankelijkheden extern aan Configuration Manager  
 De volgende tabel bevat de externe afhankelijkheden voor rapportage.  

|Vereiste|Meer informatie|  
|------------------|----------------------|  
|SQL Server Reporting Services|Voordat u de rapportage in Configuration Manager gebruiken kunt, moet u het installeren en configureren van SQL Server Reporting Services.<br /><br /> Voor informatie over planning en implementering van Reporting Services in uw omgeving, zie de sectie [Reporting Services](http://go.microsoft.com/fwlink/p/?LinkId=212032) in de SQL Server 2008 boeken online.|  
|Sitesysteemrolafhankelijkheden voor de computers die het Reporting Services-punt uitvoeren.|[Ondersteunde configuraties voor System Center Configuration Manager](../../../core/plan-design/configs/supported-configurations.md)|  

## <a name="dependencies-internal-to-configuration-manager"></a>Afhankelijkheden intern aan Configuration Manager  
 De volgende tabel bevat de afhankelijkheden voor rapportage in Configuration Manager.  

|Vereiste|Meer informatie|  
|------------------|----------------------|  
|Reporting Services-punt|Het reporting services sitesysteemrol moet worden geconfigureerd voordat u rapportage in Configuration Manager kunt gebruiken. Voor meer informatie over het installeren en configureren van een reporting services-punt, Zie [rapportage in System Center Configuration Manager configureren](../../../core/servers/manage/configuring-reporting.md).|  

## <a name="supported-sql-server-versions-for-the-reporting-services-point"></a>Ondersteunde SQL Server-versies voor het Reporting Services-punt  
 De Reporting Services-database kan geïnstalleerd worden op ofwel een standaard exemplaar of een exemplaar met naam van een 64-bit SQL Server. Het SQL Server exemplaar kan in hetzelfde volume geplaatst worden als de sitesysteemserver, of op een externe computer.  

 De volgende tabel geeft een lijst van de SQL Server-versies die ondersteund worden door het Reporting Services-punt.  

|SQL Server-versie|Reporting Services-punt|  
|------------------------|------------------------------|  
|SQL Server 2008 SP2 met een minimum van cumulatieve update 9<br /><br /> -Standaard<br />-Enterprise<br />-Datacenter|Ja|  
|SQL Server 2008 SP3 met een minimum van cumulatieve update 4<br /><br /> -Standaard<br />-Enterprise<br />-Datacenter|Ja|  
|SQL Server 2008 R2 met SP1 en met een minimale cumulatieve update 6<br /><br /> -Standaard<br />-Enterprise<br />-Datacenter|Ja|  
|SQL Server 2008 R2 met SP2<br /><br /> -Standaard<br />-Enterprise<br />-Datacenter|Ja|  
|SQL Server Express 2008 R2 met SP1 en met een minimale cumulatieve update 4|Niet ondersteund|  
|SQL Server Express 2008 R2 met SP2|Niet ondersteund|  
|SQL Server 2012 R2 en met een minimale cumulatieve update 2<br /><br /> -Standaard<br />-Enterprise|Ja|  
|SQL Server 2012 met SP1 en geen minimale cumulatieve update<br /><br /> -Standaard<br />-Enterprise|Ja|  
|SQL Server 2014<br /><br /> -Standaard<br />-Enterprise|Ja|
|SQL Server 2016<br /><br /> -Standaard<br />-Enterprise|Ja|
|SQL Server 2016 met SP1<br /><br /> -Standaard<br />-Enterprise|Ja|
## <a name="next-steps"></a>Volgende stappen
[Bewerkingen en onderhoud voor rapportage](operations-and-maintenance-for-reporting.md)
