---
title: Voor Configuration Manager-siteservers afgeschaft
titleSuffix: Configuration Manager
description: Meer informatie over de producten en besturingssystemen die door System Center Configuration Manager niet langer ondersteund voor siteservers.
ms.custom: na
ms.date: 01/25/2018
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: get-started-article
ms.assetid: d53ac075-438b-41da-ab85-42f33982da0c
caps.latest.revision: 
caps.handback.revision: 
author: mestew
ms.author: mstewart
manager: angrobe
ms.openlocfilehash: 0124939ae1ea5c1244c5776973297727b292e028
ms.sourcegitcommit: b13da5ad8ffd58e3b89fa6d7170e1dec3ff130a4
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 02/01/2018
---
# <a name="removed-and-deprecated-for-system-center-configuration-manager-site-servers"></a>Verwijderde en afgeschafte voor System Center Configuration Manager-siteservers

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*

Dit artikel wordt beschreven, producten en besturingssystemen die worden verwijderd van ondersteuning voor System Center Configuration Manager-siteservers of wordt verwijderd in een toekomstige update (afgeschaft). Dit artikel bevat vroege kennisgeving over toekomstige wijzigingen die invloed kunnen zijn op uw gebruik van Configuration Manager.  

Deze informatie kan worden gewijzigd in toekomstige versies, en bevat mogelijk niet alle afgeschafte functies, producten of besturingssysteem.  


## <a name="deprecated-server-operating-systems"></a>Afgeschafte serverbesturingssystemen  

|**Besturingssystemen**|**Afschaffing eerst aangekondigd**|**Ondersteuning verwijderd** |  
|-|-|-| 
|Windows Server 2008 R2|10 juli 2015| Versie 1702 (Zie Opmerking 1)| 
|Windows Server 2008|10 juli 2015|Versie 1511 </br></br>Ondersteuning voor een sitesysteem is verwijderd. (Zie Opmerking 2).|  

>[!NOTE]
>-   Windows Server 2008 R2, dat is vanaf versie 1702, wordt niet ondersteund voor siteservers of de meeste sitesysteemrollen. Versies voorafgaand aan 1702 blijven echter ondersteuning voor het gebruik ervan. Dit besturingssysteem blijft ondersteund voor de sitesysteemrol distributiepunt (inclusief pull-distributiepunten en voor PXE en multicast) totdat afschaffing van ondersteuning wordt aangekondigd of het besturingssysteem uitgebreide ondersteuning is verstreken. Vanaf versie 1602 kunt u in-place upgrade van het besturingssysteem van een siteserver van Windows Server 2008 R2 naar Windows Server 2012 R2.  
>- Zie voor meer informatie over in-place upgrade uit van een besturingssysteem van de site-servers, de [In-place upgrade van het besturingssysteem van siteservers waarop Windows Server 2008 R2 uitgevoerd](/sccm/core/servers/manage/upgrade-on-premises-infrastructure#bkmk_from2008r2) in sectie [lokale Upgrade infrastructuur die ondersteuning biedt voor System Center Configuration Manager](/sccm/core/servers/manage/upgrade-on-premises-infrastructure).

>[!NOTE]
>-   Windows Server 2008 wordt niet ondersteund voor siteservers of sitesysteemrollen behalve distributiepunt en pull-distributiepunt. U kunt blijven gebruiken van dit besturingssysteem als een distributiepunt totdat afschaffing van ondersteuning wordt aangekondigd of het besturingssysteem uitgebreide ondersteuning is verstreken. Zie voor meer informatie [installatie van System Center Configuration Manager CB en LTSB mislukt op Windows Server 2008](https://support.microsoft.com/help/4015095).

## <a name="deprecated-support-for-sql-server-versions-as-a-site-database"></a>Afgeschafte ondersteuning voor versies van SQL Server als een sitedatabase  

|**SQL Server-versies**|**Afschaffing eerst aangekondigd**|**Ondersteuning verwijderd**|   
|-|-|-| 
|SQL Server 2008 R2|10 juli 2015|Versie 1702| 
|SQL Server 2008|10 juli 2015|Versie 1511|  


Als u moet de versie van SQL Server wilt bijwerken, raden wij de volgende methoden van eenvoudig complexere.
1. [SQL Server in-place upgrade](/sccm/core/servers/manage/upgrade-on-premises-infrastructure#a-namebkmksupconfigupgradedbsrva-upgrade-sql-server-on-the-site-database-server) (aanbevolen).
2. Een nieuwe versie van SQL Server installeren op een nieuwe computer. Vervolgens [gebruikt u de optie-database verplaatsen](/sccm/core/servers/manage/modify-your-infrastructure#a-namebkmkdbconfiga-modify-the-site-database-configuration) installatieprogramma van Configuration Manager uw siteserver op de nieuwe SQL-Server verwijzen.
3. Gebruik [back-up en herstel](/sccm/protect/understand/backup-and-recovery).


## <a name="more-information"></a>Meer informatie
Zie voor meer informatie:
 - [Verwijderde en afgeschafte](/sccm/core/plan-design/changes/deprecated/removed-and-deprecated)
 - De [Microsoft Support Lifecycle](https://support.microsoft.com/lifecycle) website.
 - [Ondersteuning voor de huidige vertakking versies van Configuration Manager](/sccm/core/servers/manage/current-branch-versions-supported).