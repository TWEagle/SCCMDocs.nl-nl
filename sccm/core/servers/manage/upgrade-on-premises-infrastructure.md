---
title: Upgrade van on-premises infrastructuur | Microsoft-documenten
description: Informatie over het bijwerken van de infrastructuur, zoals SQL Server en het besturingssysteem van de site van site-systemen.
ms.custom: na
ms.date: 2/14/2017
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
ms.sourcegitcommit: 2e711cce2435957f3e85dad08f17260e1a224fc2
ms.openlocfilehash: c6448932e91a02984ca57cef0b75c10ea3f43fa1
ms.contentlocale: nl-nl
ms.lasthandoff: 05/17/2017


---
# <a name="upgrade-on-premises-infrastructure-that-supports-system-center-configuration-manager"></a>Lokale infrastructuur bijwerken die ondersteuning biedt voor System Center Configuration Manager

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*

Gebruik de informatie in dit onderwerp voor hulp bij de upgrade van de infrastructuur van de server met System Center Configuration Manager.  

 - Als u wilt upgraden van een eerdere versie van Configuration Manager voor System Center Configuration Manager, Zie [upgraden naar System Center Configuration Manager](/sccm/core/servers/deploy/install/upgrade-to-configuration-manager).

- Als u uw infrastructuur voor System Center Configuration Manager bijwerken naar een nieuwe versie wilt, Zie [voor System Center Configuration Manager-Updates](/sccm/core/servers/manage/updates).

##  <a name="BKMK_SupConfigUpgradeSiteSrv"></a>Werk het besturingssysteem van de site-systemen  
 Configuration Manager ondersteunt de in-place upgrade van het besturingssysteem van servers die als host optreden van een siteserver en externe servers waarop een sitesysteemrol in de volgende situaties:  

-   In-place upgrade naar een hoger servicepack voor Windows Server als het resulterende servicepack van Windows ondersteund door Configuration Manager blijft.  
-   In-place upgrade van:
    - Windows Server 2012 R2 naar Windows Server 2016 ([Zie aanvullende informatie](#upgrade-windows-server-2012-r2-to-2016)).
    - Windows Server 2012 naar Windows Server 2012 R2 ([Zie aanvullende informatie](#upgrade-windows-server-2012-to-windows-server-2012-r2)).
    - Wanneer u Configuration Manager versie 1602 of hoger, wordt ook ondersteund voor upgrade van Windows Server 2008 R2 naar Windows Server 2012 R2 ([Zie aanvullende informatie](#upgrade-windows-server-2008-r2-to-windows-server-2012-r2)).

    > [!WARNING]  
    >  Voordat u de upgrade naar Windows Server 2012 R2 uitvoert, *dient u WSUS 3.2 te verwijderen* van de server.  
    >   
    >  Voor informatie over deze kritieke stap, Zie de sectie "Nieuwe en gewijzigde functionaliteit" in [overzicht van Windows Server Update Services](https://technet.microsoft.com/library/hh852345.aspx) in de documentatie van Windows Server.  

Gebruik de upgrade procedures door het besturingssysteem die u wilt naar bijwerken voor het bijwerken van een server.  Zie het volgende:
  -  [Opties voor Windows Server 2012 R2 bijwerken](https://technet.microsoft.com/library/dn303416.aspx) in de documentatie van Windows Server.  
  - [Upgrade en conversie-opties voor Windows Server 2016](https://technet.microsoft.com/windows-server-docs/get-started/supported-upgrade-paths) in de documentatie van Windows Server.

### <a name="upgrade-windows-server-2012-r2-to-2016"></a>Upgrade uitvoeren van WindowsServer 2012 R2-2016  
Dit besturingssysteem upgrade scenario gelden de volgende voorwaarden:

**Voor de upgrade:**  
-     Verwijder de System Center Endpoint Protection (SCEP)-client. Windows Server 2016 heeft Windows-Defender ingebouwd, die de client SCEP vervangt. De aanwezigheid van de client SCEP kan voorkomen dat een upgrade naar Windows Server 2016.

**Na de upgrade:**
-     Zorg ervoor dat Windows Defender is ingeschakeld, instellen voor automatisch starten, en worden uitgevoerd.
-     Zorg ervoor dat de volgende Configuration Manager-services worden uitgevoerd:
  -     SMS EXECUTIVE-SERVICE
  -     SMS SITE COMPONENT MANAGER


-     Zorg ervoor dat de **Windows Process Activation** en **WWWW3svc/** services zijn ingeschakeld, stel voor automatisch starten, en worden uitgevoerd voor de volgende sitesysteemrollen (deze services zijn uitgeschakeld tijdens de upgrade):
  -     Siteserver
  -     Beheerpunt
  -     Application Catalog-webservicepunt
  -     Application Catalog-websitepunt


-     Zorg ervoor dat elke server die als host fungeert voor een sitesysteemrol blijft voldoen aan alle van de [prequisites voor sitesysteemrollen](/sccm/core/plan-design/configs/site-and-site-system-prerequisites) die worden uitgevoerd op die server. U wilt bijvoorbeeld BITS, WSUS, opnieuw installeren of configureren van specifieke instellingen voor IIS.

  Na het herstellen van ontbrekende vereiste onderdelen, de server opnieuw opstarten nog een keer om ervoor te zorgen services zijn gestart en operationele.

**Bekende problemen voor externe Configuration Manager-consoles:**  
Na de upgrade van de siteserver of een server die als host fungeert voor een exemplaar van de SMS_Provider naar Windows Server 2016, kunnen gebruikers met beheerdersrechten mogelijk niet een Configuration Manager-console verbinden met de site. U kunt dit probleem omzeilen, moet u machtigingen voor de SMS Admins-groep in WMI handmatig herstellen. Machtigingen zijn ingesteld op de siteserver en op elke externe server die als host fungeert voor een exemplaar van de SMS_Provider:

1. Op de desbetreffende servers, opent u de Microsoft Management Console (MMC) en voeg de module voor **WMI-beheer**, en selecteer vervolgens **lokale computer**.
2. Open in de MMC de **eigenschappen** van **WMI-beheer (lokaal)** en selecteer de **beveiliging** tabblad.
3. Vouw de structuur hieronder Root, selecteer de **SMS** knooppunt en kies vervolgens **beveiliging**.  Zorg ervoor dat de **SMS Admins** groep heeft de volgende machtigingen:
  -     Account inschakelen
  -     Op afstand inschakelen
4. Op de **tabblad Beveiliging** onder de **SMS** knooppunt, selecteer de **site_**&lt;*sitecode*> knooppunt en kies vervolgens **beveiliging**. Zorg ervoor dat de **SMS Admins** groep heeft de volgende machtigingen:
  -   Methoden uitvoeren
  -   Provider schrijven
  -   Account inschakelen
  -   Op afstand inschakelen
5. Sla de machtigingen voor toegang voor de Configuration Manager-console herstellen.

### <a name="windows-server-2012-to-windows-server-2012-r2"></a>WindowsServer 2012 naar Windows Server 2012 R2

**Voor de upgrade:**
-  In tegenstelling tot de andere ondersteunde scenario's vereist in dit scenario geen extra overwegingen voor de upgrade.

**Na de upgrade:**
  -    Zorg ervoor dat de Windows Deployment Service is gestart en wordt uitgevoerd voor de volgende sitesysteemrollen (deze service is gestopt tijdens de upgrade):
    - Siteserver
    - Beheerpunt
    - Application Catalog-webservicepunt
    - Application Catalog-websitepunt


  -     Zorg ervoor dat de **Windows Process Activation** en **WWWW3svc/** services zijn ingeschakeld, stel voor automatisch starten, en worden uitgevoerd voor de volgende sitesysteemrollen (deze services zijn uitgeschakeld tijdens de upgrade):
    -     Siteserver
    -     Beheerpunt
    -     Application Catalog-webservicepunt
    -     Application Catalog-websitepunt


  -     Zorg ervoor dat elke server die als host fungeert voor een sitesysteemrol blijft voldoen aan alle van de [prequisites voor sitesysteemrollen](/sccm/core/plan-design/configs/site-and-site-system-prerequisites) die worden uitgevoerd op die server. U wilt bijvoorbeeld BITS, WSUS, opnieuw installeren of configureren van specifieke instellingen voor IIS.

  Na het herstellen van ontbrekende vereiste onderdelen, de server opnieuw opstarten nog een keer om ervoor te zorgen services zijn gestart en operationele.

### <a name="upgrade-windows-server-2008-r2-to-windows-server-2012-r2"></a>Upgrade van Windows Server 2008 R2 naar Windows Server 2012 R2
Dit besturingssysteem upgrade scenario gelden de volgende voorwaarden:  

**Voor de upgrade:**
-     WSUS 3.2 verwijderen.  
    Voordat u een serverbesturingssysteem naar Windows Server 2012 R2 bijwerkt, moet u WSUS 3.2 verwijderen van de server. Zie voor informatie over deze kritieke stap nieuwe en gewijzigde functionaliteit sectie in het overzicht van Windows Server Update Services in de documentatie van Windows Server.

**Na de upgrade:**
  -    Zorg ervoor dat de Windows Deployment Service is gestart en wordt uitgevoerd voor de volgende sitesysteemrollen (deze service is gestopt tijdens de upgrade):
    - Siteserver
    - Beheerpunt
    - Application Catalog-webservicepunt
    - Application Catalog-websitepunt


  -     Zorg ervoor dat de **Windows Process Activation** en **WWWW3svc/** services zijn ingeschakeld, stel voor automatisch starten, en worden uitgevoerd voor de volgende sitesysteemrollen (deze services zijn uitgeschakeld tijdens de upgrade):
    -     Siteserver
    -     Beheerpunt
    -     Application Catalog-webservicepunt
    -     Application Catalog-websitepunt


  -     Zorg ervoor dat elke server die als host fungeert voor een sitesysteemrol blijft voldoen aan alle [vereisten voor sitesysteemrollen](/sccm/core/plan-design/configs/site-and-site-system-prerequisites) die worden uitgevoerd op die server. U wilt bijvoorbeeld BITS, WSUS, opnieuw installeren of configureren van specifieke instellingen voor IIS.

  Na het herstellen van ontbrekende vereiste onderdelen, de server opnieuw opstarten nog een keer om ervoor te zorgen services zijn gestart en operationele.


### <a name="unsupported-upgrade-scenarios"></a>Niet-ondersteunde upgradescenario 's
De volgende upgradescenario's van Windows Server veelgestelde over, maar niet ondersteund door Configuration Manager:  

-   Windows Server 2008 naar Windows Server 2012 of hoger  
-   Windows Server 2008 R2 naar WindowsServer 2012



##  <a name="BKMK_SupConfigUpgradeClient"></a>Werk het besturingssysteem van de Configuration Manager-clients  
 Configuration Manager ondersteunt een in-place upgrade van het besturingssysteem voor Configuration Manager-clients in de volgende situaties:  

-   In-place upgrade naar een hoger Windows servicepack als de resulterende servicepack-niveau ondersteund door Configuration Manager blijft.  

-   In-place upgrade van Windows vanuit een ondersteunde versie voor Windows 10. Zie [Windows upgraden naar de nieuwste versie met System Center Configuration Manager](../../../osd/deploy-use/upgrade-windows-to-the-latest-version.md) voor meer informatie.  

-   Build-naar-build servicing upgrades van Windows 10.  Zie [Windows als een service beheren met System Center Configuration Manager](../../../osd/deploy-use/manage-windows-as-a-service.md) voor meer informatie.  

##  <a name="BKMK_SupConfigUpgradeDBSrv"></a>SQL Server op de siteserver van de database bijwerken  
  Configuration Manager ondersteunt een in-place upgrade van SQL Server van een ondersteunde versie van SQL op de Sitedatabaseserver. De SQL Server upgradescenario's in deze sectie worden ondersteund door Configuration Manager en zijn vereisten voor elk scenario.

 Zie voor meer informatie over de versies van SQL Server die ondersteund worden door Configuration Manager [ondersteuning voor versies van SQL Server voor System Center Configuration Manager](../../../core/plan-design/configs/support-for-sql-server-versions.md).  

 **Upgrade de servicepackversie van SQL Server:**    
 Configuration Manager ondersteunt de in-place upgrade van SQL Server naar een hoger servicepack als de resulterende SQL Server service pack-niveau ondersteund door Configuration Manager blijft.

 Wanneer u meerdere Configuration Manager-sites in een hiërarchie hebt, elke site kan een andere versie van servicepack van SQL Server worden uitgevoerd en er is geen beperking in de volgorde waarin de versie van het servicepack van SQL Server die wordt gebruikt voor de sitedatabase voor het updaten van sites.

 **Een upgrade naar een nieuwe versie van SQL Server:**   
 Configuration Manager ondersteunt de in-place upgrade van SQL Server op de volgende versies:

 - SQL Server 2012  
 - SQL Server 2014  
 - SQL Server 2016  

Wanneer u de versie van SQL Server die als host fungeert voor de sitedatabase bijwerkt, moet u de SQL Server-versie die wordt gebruikt voor sites in de volgende volgorde bijwerken:

 1. Voer eerst een upgrade uit voor SQL Server op de centrale beheersite.
 2. Secundaire sites bijwerken voordat u een upgrade van een secundaire site bovenliggende primaire site uitvoert.
 3. Voer het laatst een upgrade uit voor bovenliggende primaire sites. Dit omvat zowel onderliggende primaire sites die rapporteren aan een centrale beheersite als zelfstandige primaire sites die de site op het hoogste niveau van een hiërarchie.

**SQL Server kardinaliteit schatting niveau en de sitedatabase:**   
Wanneer een site-database van een eerdere versie van SQL Server wordt bijgewerkt, wordt in de database zijn bestaande SQL kardinaliteit schatting (CE)-niveau worden als de service is toegestaan voor het exemplaar van SQL Server minimaal. SQL-Server met een database op een lager compatibiliteitsniveau dan het toegestane niveau automatisch bijwerkt, wordt de database ingesteld op het laagste niveau van databasecompatibiliteit toegestaan door SQL Server.

De volgende tabel bevat de aanbevolen compatibiliteitsniveaus voor Configuration Manager-sitedatabases:

|SQL Server-versie | Ondersteunde compatibiliteitsniveaus |Aanbevolen niveau|
|----------------|--------------------|--------|
| SQL Server 2016| 130, 120, 110, 100 | 130|
| SQL Server 2014| 120, 110, 100      | 110|

Voer de volgende SQL-query op de siteserver van de database om het compatibiliteitsniveau van de SQL Server CE wordt gebruikt voor de database van uw site hebt geïdentificeerd:  **Principal-naam, compatibility_level FROM sys.databases selecteren**

 Zie voor meer informatie over SQL CE-compatibiliteitsniveaus en het instellen van deze [ALTER databasecompatibiliteitsniveau (Transact-SQL)](https://msdn.microsoft.com/library/bb510680.aspx).


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

