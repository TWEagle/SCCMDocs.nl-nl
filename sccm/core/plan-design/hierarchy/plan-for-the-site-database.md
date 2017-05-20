---
title: Plannen van de sitedatabase | Microsoft-documenten
description: "Als u uw System Center Configuration Manager-hiërarchie plant, overweeg dan de sitedatabase en de sitedatabaseserverrol."
ms.custom: na
ms.date: 10/06/2016
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: get-started-article
ms.assetid: 104fb4cc-6e83-40a3-8e6b-ac909fb9ec7d
caps.latest.revision: 5
caps.handback.revision: 0
author: Brenduns
ms.author: brenduns
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: cec63ed7781e236dbf5e8baa0a468193ea794339
ms.openlocfilehash: d4efe1f013dbb74efca79cd27f7248fc085c7424
ms.contentlocale: nl-nl
ms.lasthandoff: 05/17/2017


---
# <a name="plan-for-the-site-database-for-system-center-configuration-manager"></a>De sitedatabase plannen voor System Center Configuration Manager

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*

De Sitedatabaseserver is een computer waarop een ondersteunde versie van Microsoft SQL Server wordt uitgevoerd. SQL Server wordt gebruikt voor het opslaan van informatie voor Configuration Manager-sites. Elke site in een Configuration Manager-hiërarchie bevat een sitedatabase en een server waaraan de sitedatabaseserverrol is toegewezen.  

-   Voor centrale beheersites en primaire sites, kunt u SQL Server installeren op de siteserver of u kunt SQL Server installeren op een andere computer dan de siteserver.  

-   Voor secundaire sites kunt u SQL Server Express gebruiken in plaats van een volledige installatie van SQL Server. De database-server moet zijn, echter worden uitgevoerd op de secundaire siteserver.  

De volgende configuraties voor SQL Server kunnen worden gebruikt om de sitedatabase te hosten:  

-   Het standaardexemplaar van SQL Server  

-   Een benoemd exemplaar op één computer met SQL Server  

-   Een benoemd exemplaar op een geclusterd exemplaar van SQL Server  

-   Een SQL Server AlwaysOn-beschikbaarheidsgroep (begin met versie 1602 van System Center Configuration Manager)


Als host voor de sitedatabase, het SQL-Server moet voldoen aan de vereisten uiteengezet in [ondersteuning voor versies van SQL Server voor System Center Configuration Manager](../../../core/plan-design/configs/support-for-sql-server-versions.md).  



## <a name="remote-database-server-location-considerations"></a>Overwegingen bij de locatie van de externe database server  

Als u een externe databaseservercomputer gebruikt, zorg ervoor dat de interveniërende netwerkverbinding een netwerkverbinding van hoge beschikbaarheid en hoge bandbreedte. De siteserver en sommige sitesysteemrollen moeten constant communiceren met de externe server die als host voor de sitedatabase fungeert.

-   De hoeveelheid bandbreedte die vereist is voor communicatie met de databaseserver is afhankelijk van een combinatie van veel verschillende site- en clientconfiguraties. Daarom kan niet de werkelijke bandbreedte die vereist gemakkelijk worden voorspeld.  

-   Elke computer die de SMS Provider uitvoert en een verbinding maakt met de sitedatabase verhoogt de vereisten met betrekking tot de netwerkbandbreedte.  

-   De computer met SQL Server moet zich bevinden in een domein dat een tweerichtingsvertrouwensrelatie heeft met de siteserver en alle computers met de SMS-Provider.  

-   U kunt geen geclusterde SQL Server gebruiken voor de sitedatabaseserver wanneer de sitedatabase zich op dezelfde locatie als de siteserver bevindt.  


Gewoonlijk ondersteunt een sitesysteemserver sitesysteemrollen van slechts één site voor Configuration Manager. U kunt, echter verschillende exemplaren van SQL Server, op al dan niet geclusterde servers met SQL Server gebruiken om een database van andere Configuration Manager-sites te hosten. Om databases voor verschillende sites te ondersteunen, moet u elk exemplaar van SQL Server configureren om unieke poorten voor communicatie te gebruiken.  

