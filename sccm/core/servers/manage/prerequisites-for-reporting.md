---
title: Vereisten voor rapportage
titleSuffix: Configuration Manager
description: Inzicht in verschillende afhankelijkheden die van invloed zijn op uw gebruik van rapportage in System Center Configuration Manager.
ms.custom: na
ms.date: 01/29/2018
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: get-started-article
ms.assetid: 9cc508a5-5023-4833-b776-ae9a6971138f
caps.latest.revision: 
caps.handback.revision: 
author: Dougeby
ms.author: dougeby
manager: angrobe
ms.openlocfilehash: 3feafa8a20bedfba381c29a5d7fe80a47517b6ab
ms.sourcegitcommit: b13da5ad8ffd58e3b89fa6d7170e1dec3ff130a4
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 02/01/2018
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
|SQL Server 2017 met een minimum van cumulatieve update 2<br /><br /> -   Standard<br />-   Enterprise|Ja, beginnend in Configuration Manager versie 1710|  
|SQL Server 2016 met SP1<br /><br /> -   Standard<br />-   Enterprise|Ja| 
|SQL Server 2016<br /><br /> -   Standard<br />-   Enterprise|Ja|
|SQL Server 2014 with SP2<br /><br /> -   Standard<br />-   Enterprise|Ja|
|SQL Server 2014 met SP1<br /><br /> -   Standard<br />-   Enterprise|Ja|
|SQL Server 2012 with SP4 <br /><br /> -   Standard<br />-   Enterprise|Ja|  
|SQL Server 2012 with SP3 <br /><br /> -   Standard<br />-   Enterprise|Ja|  
|SQL Server 2008 R2 with SP3<br /><br /> -   Standard<br />-   Enterprise<br />-Datacenter|Ja, voor ondersteunde versies van Configuration Manager 1702.|  
|SQL Server Express 2008 R2 met SP3|Niet ondersteund| 




## <a name="next-steps"></a>Volgende stappen
[Bewerkingen en onderhoud voor rapportage](operations-and-maintenance-for-reporting.md)
