---
title: On-premises infrastructuur bijwerken | Microsoft Docs
description: Informatie over het upgraden van de infrastructuur, zoals SQL Server en het besturingssysteem van de site van site-systemen.
ms.custom: na
ms.date: 06/05/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 8ca970dd-e71c-404f-9435-d36e773a0db2
caps.latest.revision: 7
caps.handback.revision: 0
author: Brenduns
ms.author: brenduns
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 0564cb678200d17d97c0f1d111c0b4b41d8ba40e
ms.openlocfilehash: 188b7f2537dd0e569a5c00995620124512cf311b
ms.contentlocale: nl-nl
ms.lasthandoff: 06/30/2017


---
# <a name="upgrade-on-premises-infrastructure-that-supports-system-center-configuration-manager"></a>Lokale infrastructuur bijwerken die ondersteuning biedt voor System Center Configuration Manager

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*

Gebruik de informatie in dit onderwerp voor hulp bij het upgraden van de infrastructuur van de server waarop System Center Configuration Manager wordt uitgevoerd.  

 - Als u upgraden vanaf een eerdere versie van Configuration Manager naar System Center Configuration Manager wilt, raadpleegt u [upgraden naar System Center Configuration Manager](/sccm/core/servers/deploy/install/upgrade-to-configuration-manager).

- Als u uw infrastructuur voor System Center Configuration Manager bijwerken naar een nieuwe versie wilt, Zie [Updates voor System Center Configuration Manager](/sccm/core/servers/manage/updates).

##  <a name="BKMK_SupConfigUpgradeSiteSrv"></a>Werk het besturingssysteem van de site-systemen  
 Configuration Manager ondersteunt de in-place upgrade van het besturingssysteem van de servers die als host fungeren van een siteserver en externe servers die als host fungeren van elke sitesysteemrol in de volgende situaties:  

-   In-place upgrade naar een hoger Windows Server-servicepack als het resulterende servicepackniveau van Windows ondersteund door Configuration Manager blijft.  
-   In-place upgrade van:
    - Windows Server 2012 R2 naar Windows Server 2016 ([Zie aanvullende informatie](#bkmk_2016)).
    - Windows Server 2012 naar Windows Server 2016 ([Zie aanvullende informatie](#bkmk_2016)).
    - Windows Server 2012 naar Windows Server 2012 R2 ([Zie aanvullende informatie](#bkmk_2012r2)).
    - Wanneer u Configuration Manager versie 1602 of hoger, wordt ook ondersteund voor een upgrade van Windows Server 2008 R2 naar Windows Server 2012 R2 ([Zie aanvullende informatie](#bkmk_from2008r2).

    > [!WARNING]  
    >  Voordat u de upgrade naar Windows Server 2012 R2 uitvoert, *dient u WSUS 3.2 te verwijderen* van de server.  
    >   
    >  Voor informatie over deze kritieke stap, Zie de sectie 'New and changed functionality' in [overzicht van Windows Server Update Services](https://technet.microsoft.com/library/hh852345.aspx) in de documentatie van Windows Server.  

Gebruik de upgradeprocedures geleverd door het besturingssysteem dat u een upgrade uitvoert voor het bijwerken van een server.  Zie de volgende:
  -  [Opties voor Windows Server 2012 R2 upgraden](https://technet.microsoft.com/library/dn303416.aspx) in de documentatie van Windows Server.  
  - [Upgrade en conversie-opties voor Windows Server 2016](https://technet.microsoft.com/windows-server-docs/get-started/supported-upgrade-paths) in de documentatie van Windows Server.

### <a name="bkmk_2016"></a>Upgrade van WindowsServer 2012 of WindowsServer 2012 R2-2016
Wanneer u Windows Server 2012 of Windows Server 2012 R2 naar Windows Server 2016, de volgende van toepassing upgraden:


**Voor de upgrade:**  
-   De System Center Endpoint Protection (SCEP)-client verwijderen. Windows Server 2016 heeft ingebouwde Windows-Defender die de SCEP-client vervangt. De aanwezigheid van de SCEP-client kunt voorkomen dat een upgrade naar Windows Server 2016.

**Na de upgrade:**
-   Zorg ervoor dat Windows Defender is ingeschakeld, instellen voor automatisch starten en wordt uitgevoerd.
-   Zorg ervoor dat de volgende Configuration Manager-services worden uitgevoerd:
  -     SMS EXECUTIVE
  -     SMS SITE COMPONENT MANAGER


-   Zorg ervoor dat de **Windows Process Activation** en **WWW/W3svc** services zijn ingeschakeld, worden ingesteld voor automatisch starten en de volgende sitesysteemrollen (deze services worden uitgeschakeld tijdens de upgrade) worden uitgevoerd:
  -     Siteserver
  -     Beheerpunt
  -     Application Catalog-webservicepunt
  -     Application Catalog-websitepunt

-   Zorg ervoor dat elke server die als host fungeert voor een sitesysteemrol blijft voldoen aan alle de [vereisten voor sitesysteemrollen](/sccm/core/plan-design/configs/site-and-site-system-prerequisites) die worden uitgevoerd op die server. U wilt bijvoorbeeld BITS, WSUS, opnieuw installeren of configureren met specifieke instellingen voor IIS.

-   Na het terugzetten van ontbrekende vereiste onderdelen, start opnieuw op de server een keer om ervoor te zorgen services zijn gestart en operationele.

**Bekend probleem voor externe Configuration Manager-consoles:**  
Na de upgrade van de siteserver of een server die als host fungeert voor een exemplaar van de SMS-provider naar Windows Server 2016, kunnen gebruikers met beheerdersrechten mogelijk niet een Configuration Manager-console verbinden met de site. U kunt dit probleem omzeilen, moet u machtigingen voor de SMS Admins-groep in WMI handmatig herstellen. Machtigingen zijn ingesteld op de siteserver en op elke externe server die als host fungeert voor een exemplaar van de SMS-provider:

1. Open Microsoft Management Console (MMC) op de desbetreffende servers en voeg de module voor **WMI-beheer**, en selecteer vervolgens **lokale computer**.
2. Open in de MMC, de **eigenschappen** van **WMI-beheer (lokaal)** en selecteer de **beveiliging** tabblad.
3. Vouw de structuur hieronder Root, selecteer de **SMS** knooppunt, en kies vervolgens **beveiliging**.  Zorg ervoor dat de **SMS Admins** groep heeft de volgende machtigingen:
  -     Account inschakelen
  -     Op afstand inschakelen
4. Op de **tabblad Beveiliging** onder de **SMS** knooppunt, selecteer de **site_&lt;sitecode**>-knooppunt, en kies vervolgens **beveiliging**. Zorg ervoor dat de **SMS Admins** groep heeft de volgende machtigingen:
  -   Methoden uitvoeren
  -   Schrijftoegang tot providerobjecten
  -   Account inschakelen
  -   Op afstand inschakelen
5. Sla de machtigingen voor toegang voor de Configuration Manager-console herstellen.

### <a name="bkmk_2012r2"></a>WindowsServer 2012 naar Windows Server 2012 R2

**Voor de upgrade:**
-  In tegenstelling tot de andere ondersteunde scenario's, is dit scenario geen extra overwegingen vóór upgrade vereist.

**Na de upgrade:**
  - Zorg ervoor dat de Windows Deployment Service is gestart en worden uitgevoerd voor de volgende sitesysteemrollen (deze service is gestopt tijdens de upgrade):
    - Siteserver
    - Beheerpunt
    - Application Catalog-webservicepunt
    - Application Catalog-websitepunt

  -     Zorg ervoor dat de **Windows Process Activation** en **WWW/W3svc** services zijn ingeschakeld, worden ingesteld voor automatisch starten en de volgende sitesysteemrollen (deze services worden uitgeschakeld tijdens de upgrade) worden uitgevoerd:
    -   Siteserver
    -   Beheerpunt
    -   Application Catalog-webservicepunt
    -   Application Catalog-websitepunt


  -     Zorg ervoor dat elke server die als host fungeert voor een sitesysteemrol blijft voldoen aan alle de [vereisten voor sitesysteemrollen](/sccm/core/plan-design/configs/site-and-site-system-prerequisites) die worden uitgevoerd op die server. U wilt bijvoorbeeld BITS, WSUS, opnieuw installeren of configureren met specifieke instellingen voor IIS.

  Na het terugzetten van ontbrekende vereiste onderdelen, start opnieuw op de server een keer om ervoor te zorgen services zijn gestart en operationele.

### <a name="bkmk_from2008r2"></a>Upgrade van Windows Server 2008 R2 naar Windows Server 2012 R2
Dit besturingssysteem upgradescenario heeft de volgende voorwaarden:  

**Voor de upgrade:**
-   WSUS 3.2 verwijderen.  
    Voordat u een besturingssysteem naar Windows Server 2012 R2 upgraden, moet u WSUS 3.2 verwijderen van de server. Zie de sectie nieuwe en gewijzigde functionaliteit in het overzicht van Windows Server Update Services in Windows Server-documentatie voor informatie over deze kritieke stap.

**Na de upgrade:**
  - Zorg ervoor dat de Windows Deployment Service is gestart en worden uitgevoerd voor de volgende sitesysteemrollen (deze service is gestopt tijdens de upgrade):
    - Siteserver
    - Beheerpunt
    - Application Catalog-webservicepunt
    - Application Catalog-websitepunt


  -     Zorg ervoor dat de **Windows Process Activation** en **WWW/W3svc** services zijn ingeschakeld, worden ingesteld voor automatisch starten en de volgende sitesysteemrollen (deze services worden uitgeschakeld tijdens de upgrade) worden uitgevoerd:
    -   Siteserver
    -   Beheerpunt
    -   Application Catalog-webservicepunt
    -   Application Catalog-websitepunt


  -     Zorg ervoor dat elke server die als host fungeert voor een sitesysteemrol blijft voldoen aan alle [vereisten voor sitesysteemrollen](/sccm/core/plan-design/configs/site-and-site-system-prerequisites) die worden uitgevoerd op die server. U wilt bijvoorbeeld BITS, WSUS, opnieuw installeren of configureren met specifieke instellingen voor IIS.

  Na het terugzetten van ontbrekende vereiste onderdelen, start opnieuw op de server een keer om ervoor te zorgen services zijn gestart en operationele.


### <a name="unsupported-upgrade-scenarios"></a>Niet-ondersteunde upgradescenario 's
De volgende upgradescenario's van Windows Server veelgestelde over, maar niet ondersteund door Configuration Manager:  

-   Windows Server 2008 naar Windows Server 2012 of hoger  
-   Windows Server 2008 R2 naar WindowsServer 2012



##  <a name="BKMK_SupConfigUpgradeClient"></a>Werk het besturingssysteem van Configuration Manager-clients  
 Configuration Manager ondersteunt een in-place upgrade van het besturingssysteem voor Configuration Manager-clients in de volgende situaties:  

-   In-place upgrade naar een hoger Windows servicepack als het resulterende servicepackniveau ondersteund door Configuration Manager blijft.  

-   In-place upgrade van Windows vanuit een ondersteunde versie naar Windows 10. Zie [Windows upgraden naar de nieuwste versie met System Center Configuration Manager](../../../osd/deploy-use/upgrade-windows-to-the-latest-version.md) voor meer informatie.  

-   Upgrades van build-naar-build onderhoud van Windows 10.  Zie [Windows als een service beheren met System Center Configuration Manager](../../../osd/deploy-use/manage-windows-as-a-service.md) voor meer informatie.  

##  <a name="BKMK_SupConfigUpgradeDBSrv"></a>SQL Server op de Sitedatabaseserver bijwerken  
  Configuration Manager ondersteunt een in-place upgrade van SQL Server vanuit een ondersteunde versie van SQL op de Sitedatabaseserver. De SQL Server upgradescenario's in deze sectie worden ondersteund door Configuration Manager en vereisten voor elk scenario bevatten.

 Zie voor meer informatie over de versies van SQL Server die worden ondersteund door Configuration Manager [ondersteuning voor SQL Server-versies voor System Center Configuration Manager](../../../core/plan-design/configs/support-for-sql-server-versions.md).  

 **Upgrade de servicepackversie van SQL Server:**    
 Configuration Manager ondersteunt de in-place upgrade van SQL Server naar een hoger servicepack als het resulterende SQL Server-servicepackniveau ondersteund door Configuration Manager blijft.

 Wanneer u meerdere Configuration Manager-sites in een hiërarchie hebt, kan elke site een andere servicepackversie van SQL Server worden uitgevoerd en er geldt geen beperking voor de volgorde waarin de servicepackversie van SQL Server die wordt gebruikt voor de sitedatabase de sites wordt bijgewerkt.

 **Een upgrade naar een nieuwe versie van SQL Server:**   
 Configuration Manager ondersteunt de in-place upgrade van SQL Server op de volgende versies:

 - SQL Server 2012  
 - SQL Server 2014  
 - SQL Server 2016  

Wanneer u de versie van SQL Server die als host fungeert voor de sitedatabase bijwerkt, moet u een upgrade van de SQL Server-versie die wordt gebruikt op sites in de volgende volgorde:

 1. Voer eerst een upgrade uit voor SQL Server op de centrale beheersite.
 2. Upgraden van secundaire sites voordat u een secundaire site bovenliggende primaire site bijwerkt.
 3. Voer het laatst een upgrade uit voor bovenliggende primaire sites. Dit omvat zowel onderliggende primaire sites die rapporteren aan een centrale beheersite als zelfstandige primaire sites die zijn van het hoogste niveau van een hiërarchie.

**SQL Server Kardinaliteitsschatting niveau en de sitedatabase:**   
Wanneer een sitedatabase van een eerdere versie van SQL Server wordt bijgewerkt, wordt in de database zijn bestaande SQL kardinaliteit schatting (CE)-niveau behouden als het is ingesteld op de minimaal toegestane voor dat betreffende exemplaar van SQL Server. SQL Server bijwerken met een database op een lager compatibiliteitsniveau dan het toegestane niveau automatisch, wordt de database ingesteld op het laagste niveau van databasecompatibiliteit toegestaan door SQL Server.

De volgende tabel bevat de aanbevolen compatibiliteitsniveaus voor Configuration Manager-sitedatabases:

|SQL Server-versie | Ondersteunde compatibiliteitsniveaus |Aanbevolen niveau|
|----------------|--------------------|--------|
| SQL Server 2016| 130, 120, 110, 100 | 130|
| SQL Server 2014| 120, 110, 100      | 110|

Om het compatibiliteitsniveau van de SQL Server CE gebruikt voor de database van uw site hebt geïdentificeerd, voer de volgende SQL-query op de Sitedatabaseserver:  **Selecteer de naam, compatibility_level FROM sys.databases.**

 Zie voor meer informatie over SQL CE-compatibiliteitsniveaus en hoe deze [ALTER databasecompatibiliteitsniveau (Transact-SQL)](https://msdn.microsoft.com/library/bb510680.aspx).


Zie de documentatie van SQL Server op TechNet voor meer informatie over SQL Server:
-   [Upgrade naar SQL Server 2012](http://technet.microsoft.com/library/ms143393\(v=sql.110))
-   [Upgrade naar SQL Server 2014](http://technet.microsoft.com/library/ms143393\(v=sql.120))  
-   [Upgrade naar SQL Server 2016](https://technet.microsoft.com/library/bb677622(v=sql.130))



### <a name="to-upgrade-sql-server-on-the-site-database-server"></a>Een upgrade uitvoeren voor SQL Server op de sitedatabaseserver  

1.  Stop alle Configuration Manager-services op de site.  
2.  Werk SQL Server bij naar een ondersteunde versie.  
3.  De Configuration Manager-services opnieuw starten.  

> [!NOTE]  
>  Wanneer u de SQL Server-editie die wordt gebruikt op de centrale beheersite wijzigt van een Standard-editie in een Datacenter- of Enterprise-editie, wordt de databasepartitie met beperkingen voor het aantal clients dat door de hiërarchie wordt ondersteund niet aangepast.

