---
title: De sitedatabase plannen
titleSuffix: Configuration Manager
description: "Als u uw System Center Configuration Manager-hiërarchie plant, overweeg dan de sitedatabase en de sitedatabaseserverrol."
ms.custom: na
ms.date: 03/08/20168
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: get-started-article
ms.assetid: 104fb4cc-6e83-40a3-8e6b-ac909fb9ec7d
caps.latest.revision: 
caps.handback.revision: 
author: aczechowski
ms.author: aaroncz
manager: angrobe
ms.openlocfilehash: 908ca61bc99db3ca93f46120a806cd9ae54c81f7
ms.sourcegitcommit: b653342fb5d69a16e71b3548a7e9a2e47e54bf88
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 03/12/2018
---
# <a name="plan-for-the-site-database-for-system-center-configuration-manager"></a>De sitedatabase plannen voor System Center Configuration Manager

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*

De Sitedatabaseserver is een computer waarop een ondersteunde versie van Microsoft SQL Server wordt uitgevoerd. SQL Server wordt gebruikt voor het opslaan van informatie voor Configuration Manager-sites. Elke site in een Configuration Manager-hiërarchie bevat een sitedatabase en een server die de sitedatabaseserverrol is toegewezen.  

-   Voor centrale beheersites en primaire sites kunt u SQL Server op de siteserver installeren of u kunt SQL Server installeren op een andere computer dan de siteserver.  

-   Voor secundaire sites kunt u SQL Server Express gebruiken in plaats van een volledige installatie van SQL Server. De database-server moet zijn, echter worden uitgevoerd op de secundaire siteserver.  

-  Gebruik het herstelmodel van de Database voor de SQL-beschikbaarheidsgroep moet worden ingesteld op FULL  

-  Voor niet - SQL-beschikbaarheidsgroep moet gebruik het herstelmodel van de Database worden ingesteld op eenvoudig  

Meer informatie over de modi van SQL-herstel vindt u in Recovery modellen (SQL Server) (https://docs.microsoft.com/sql/relational-databases/backup-restore/recovery-models-sql-server).

De volgende SQL Server-configuraties kunnen worden gebruikt om de sitedatabase te hosten:  

-   Het standaardexemplaar van SQL Server  

-   Een benoemd exemplaar op één computer met SQL Server  

-   Een benoemd exemplaar op een geclusterd exemplaar van SQL Server  

-   Een SQL Server AlwaysOn-beschikbaarheidsgroep (vanaf versie 1602 van System Center Configuration Manager)


Voor het hosten van de sitedatabase, de SQL-Server moet voldoen aan de vereisten uiteengezet in [ondersteuning voor SQL Server-versies voor System Center Configuration Manager](../../../core/plan-design/configs/support-for-sql-server-versions.md).  



## <a name="remote-database-server-location-considerations"></a>Overwegingen bij de locatie van de externe database server  

Als u een externe databaseservercomputer gebruikt, zorg ervoor dat de interveniërende netwerkverbinding een hoge beschikbaarheid, hoge bandbreedte netwerkverbinding. De siteserver en sommige sitesysteemrollen communiceren constant met de externe server die als host voor de sitedatabase fungeert.

-   De hoeveelheid bandbreedte die vereist zijn voor communicatie met de databaseserver is afhankelijk van een combinatie van veel verschillende site- en clientconfiguraties. Daarom kan niet de werkelijke bandbreedte die vereist gemakkelijk worden voorspeld.  

-   Elke computer die de SMS Provider uitvoert en een verbinding maakt met de sitedatabase verhoogt de vereisten met betrekking tot de netwerkbandbreedte.  

-   De computer waarop SQL Server moet zich in een domein dat een tweerichtingsvertrouwensrelatie heeft met de siteserver en op alle computers met de SMS-Provider.  

-   U kunt geen geclusterde SQL Server gebruiken voor de sitedatabaseserver wanneer de sitedatabase zich op dezelfde locatie als de siteserver bevindt.  


Gewoonlijk ondersteunt een sitesysteemserver sitesysteemrollen van slechts één Configuration Manager-site. U kunt echter verschillende exemplaren van SQL Server op geclusterde of niet-geclusterde servers met SQL Server gebruiken om een database van verschillende Configuration Manager-sites te hosten. Om databases voor verschillende sites te ondersteunen, moet u elk exemplaar van SQL Server configureren om unieke poorten voor communicatie te gebruiken.  
