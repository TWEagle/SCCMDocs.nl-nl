---
title: Migreer de objecten | Microsoft-documenten
description: "Informatie over het plannen voor de migratie van objecten tussen hiërarchieën in een omgeving met System Center Configuration Manager."
ms.custom: na
ms.date: 1/12/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 066caf00-e419-4efb-93d3-ba4ba878297c
caps.latest.revision: 7
caps.handback.revision: 0
author: Brenduns
ms.author: brenduns
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 45931f60273f3130cca36320770126a36dcc3d1e
ms.openlocfilehash: 9870ffa6ae5f80db823bfc74a7cc2e67fc8cf21d
ms.contentlocale: nl-nl
ms.lasthandoff: 05/17/2017


---
# <a name="plan-for-the-migration-of-configuration-manager-objects-to-system-center-configuration-manager"></a>Plannen voor de migratie van Configuration Manager-objecten naar System Center Configuration Manager

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*

Met System Center Configuration Manager kunt u veel van de verschillende objecten die gekoppeld aan verschillende functies die gevonden op een bronsite zijn kunt migreren. Gebruik de volgende secties om u te helpen plannen voor de migratie van objecten tussen hiërarchieën.  

-   [Plan de migratie van software-updates](#Plan_migrate_Software_updates)  

-   [Migreren van inhoud](#Plan_Migrate_content)  

-   [Migreren van verzamelingen](#BKMK_MigrateCollections)  

-   [Implementaties van besturingssystemen migreren](#Plan_migrate_OSD)  

-   [Migreren van gewenst Configuratiebeheer](#Plan_Migrate_Compliance_settings)  

-   [Migreren van grenzen](#Plan_migrate_Boundaries)  

-   [Plan de migratie van rapporten](#Plan_Migrate_reports)  

-   [Plan bent om te migreren van organisatorische mappen en zoekmappen](#Plan_Migrate_Org_Folders)  

-   [Plan de migratie van Asset Intelligence-aanpassingen](#Plan_Migrate_AI)  

-   [Migreren van aanpassingen van de regels voor softwarelicentiecontrole](#Plan_Migrate_SWM_Rules)  

##  <a name="Plan_migrate_Software_updates"></a>Plan de migratie van software-updates  
 U kunt software-Updateobjecten migreren, zoals software-updatepakketten en software-implementaties update.  

 Met succes software-update om objecten te migreren, moet u eerst uw doelhiërarchie met configuraties die overeenkomen met uw bronhiërarchieomgeving instellen. Dit vereist de volgende acties:  

-   Implementeer een actief software-updatepunt in de doelhiërarchie  

-   De productcatalogus en talen zodat dit overeenkomt met de configuratie van uw bronhiërarchie instellen  

-   Synchroniseren van de software-updatepunt in de doelhiërarchie met Windows Server Update Services (WSUS)  

Overweeg, als u software-updates migreert, het volgende:  

-   Migratie van software-Updateobjecten kan falen wanneer u gegevens niet gesynchroniseerd in uw doelhiërarchie zodat dit overeenkomt met de configuratie van uw bronhiërarchie.  

    > [!WARNING]  
    >  Configuration Manager biedt geen ondersteuning voor gebruik van het WSUSutil-hulpprogramma gegevens te synchroniseren tussen een bron- en doelhiërarchie.  

-   U kunt geen aangepaste updates migreren die gepubliceerd zijn door gebruik te maken van System Center Updates Publisher. Aangepaste updates moeten in plaats daarvan opnieuw worden gepubliceerd naar de doelhiërarchie.  

Wanneer u van een Configuration Manager 2007-bronhiërarchie migreert, wijzigt het migratieproces sommige objecten voor software-update naar de notatie wordt gebruikt door de doelhiërarchie. Gebruik de volgende tabel voor het plannen van de migratie van objecten voor software-update van Configuration Manager 2007.  

|Configuration Manager 2007-object|Objectnaam na migratie|  
|-----------------------------------|---------------------------------|  
|Lijsten met software-updates|Lijsten met software-updates worden geconverteerd naar software-updategroepen.|  
|Software-update-implementaties|Software-update-implementaties worden omgezet in implementaties en groepen bijwerken.<br /><br /> Nadat u de implementatie van een software-update van Configuration Manager 2007 migreert, moet u ze inschakelen in de doelhiërarchie vóór u ze kunt implementeren.|  
|Software-updatepakketten|Software-updatepakketten blijven software-updatepakketten.|  
|Software-update-sjablonen|Software-update sjablonen blijven sjablonen voor software-update.<br /><br /> De **duur** waarde in Configuration Manager 2007-implementatiesjablonen niet worden gemigreerd.|  

Wanneer u objecten vanaf een bronhiërarchie System Center 2012 Configuration Manager of System Center Configuration Manager migreert, worden de software-Updateobjecten niet gewijzigd.  

##  <a name="Plan_Migrate_content"></a>Migreren van inhoud  
 U kunt inhoud migreren vanaf een ondersteunde bronhiërarchie naar uw doelhiërarchie. Dit materiaal bevat voor een bronhiërarchie Configuration Manager 2007 softwaredistributiepakketten en programma's en virtuele toepassingen zoals Microsoft Application Virtualization (App-V). Dit materiaal bevat voor System Center 2012 Configuration Manager en System Center Configuration Manager-bronhiërarchieën en App-V virtuele toepassingen. Wanneer u inhoud tussen hiërarchieën migreert, worden de gecomprimeerde bronbestanden migreert naar de doelhiërarchie.  

### <a name="packages-and-programs"></a>Pakketten en programma's  
 Wanneer u pakketten en programma's migreert, worden ze niet gewijzigd door migratie. Echter, voordat u deze migreert, moet u instellen elk pakket met een pad (Universal Naming Convention) bevinden voor zijn bronlocatie. Als onderdeel van de configuratie van pakketten en programma's, moet u een site toewijzen in de doelhiërarchie om deze inhoud te beheren. De inhoud wordt niet gemigreerd vanaf de toegewezen site, maar na migratie, de toegewezen site toegang tot de oorspronkelijk bronbestandlocatie met behulp van de UNC-toewijzing.  

 Nadat u een pakket en programma migreert naar de doelhiërarchie en terwijl de migratie van de bronhiërarchie actief blijft, kunt u de inhoud beschikbaar maken voor clients in die hiërarchie met behulp van een gedeeld distributiepunt. Om een gedeeld distributiepunt te gebruiken, moet de inhoud beschikbaar blijven op het distributiepunt op de bronsite. Zie voor meer informatie over gedeelde distributiepunten [distributiepunten delen tussen de bron- en Doelhiërarchieën](../../core/migration/planning-a-content-deployment-migration-strategy.md#About_Shared_DPs_in_Migration) in [strategie voor inhoudsdistributie migratie in System Center Configuration Manager](../../core/migration/planning-a-content-deployment-migration-strategy.md).  

 Voor inhoud die gemigreerd is, indien de inhoudversie wijzigt in de bronhiërarchie of de doelhiërarchie, clients niet langer toegang de inhoud van het gedeelde distributiepunt in de doelhiërarchie tot kunnen. In dit scenario moet u opnieuw de inhoud naar het herstellen van een consistente Pakketversie tussen de bron en de doelhiërarchie migreren. Deze informatie wordt gesynchroniseerd tijdens de gegevensverzameling-cyclus.  

> [!TIP]  
>  Voor elk pakket dat u migreert, werkt u het pakket bij in de doelhiërarchie. Met deze actie kunnen problemen met de implementatie van het pakket op distributiepunten in de doelhiërarchie worden voorkomen. Wanneer u een pakket op het distributiepunt in de doelhiërarchie, kunnen clients bijwerkt in deze hiërarchie niet langer worden echter mogelijk om te verkrijgen dat pakket van een gedeeld distributiepunt. Voor het bijwerken van een pakket in de doelhiërarchie, in de Configuration Manager-console gaat u naar de softwarebibliotheek met de rechtermuisknop op het pakket en selecteer vervolgens **distributiepunten bijwerken**. Voer deze actie uit voor elk pakket dat u migreert.  

> [!TIP]  
>  U kunt Microsoft System Center Configuration Manager Package Conversion Manager gebruiken om te converteren van pakketten en programma's naar System Center Configuration Manager-toepassingen. Download Package Conversion Manager vanaf de [Microsoft Downloadcentrum](http://go.microsoft.com/fwlink/p/?LinkId=212950)-site. Zie [Configuration Manager Package Conversion Manager](http://go.microsoft.com/fwlink/p/?LinkId=247245) voor meer informatie.  

### <a name="virtual-applications"></a>Virtuele toepassingen  
Wanneer u App-V pakketten vanaf een ondersteunde Configuration Manager 2007-site migreert, converteert het migratieproces ze tot toepassingen in de doelhiërarchie. Daarnaast gebaseerd op bestaande advertenties voor het App-V-pakket, de volgende implementatietypes gecreëerd in de doelhiërarchie:  

-   Indien er geen advertenties zijn, wordt één implementatietype gecreëerd dat de standaard implementatietype-instellingen gebruikt.  

-   Indien een advertentie bestaat, wordt één implementatietype gecreëerd dat dezelfde instellingen als de advertentie Configuration Manager 2007 gebruikt.  

-   Indien meerdere advertenties bestaan, wordt een implementatietype gemaakt voor elke advertentie van Configuration Manager 2007 met behulp van de instellingen voor deze advertentie.  

> [!IMPORTANT]  
>  Als u een eerder gemigreerde Configuration Manager 2007-App-V-pakket hebt gemigreerd, mislukt de migratie omdat virtuele toepassingspakketten het overschrijvingsgedrag van migratie niet ondersteunen. In dit scenario moet u het gemigreerde virtuele toepassingspakket wissen van de doelhiërarchie en dan een nieuwe migratietaak maken om de virtuele toepassing te migreren.  

> [!NOTE]  
>  Nadat u een App-V-pakket hebt gemigreerd, kunt u de wizard inhoud bijwerken om het bronpad voor App-V-implementatietypen te wijzigen. Zie voor meer informatie over het bijwerken van inhoud voor een implementatietype beheren implementatietypen in [beheertaken voor System Center Configuration Manager-toepassingen](../../apps/deploy-use/management-tasks-applications.md).  

Wanneer u van een System Center 2012 Configuration Manager of System Center Configuration Manager-bronhiërarchie migreert, kunt u objecten voor de virtuele omgeving App-V naast App-V implementatietypes en toepassingen kunt migreren. Zie voor meer informatie over App-V omgevingen, [implementeren App-V virtuele toepassingen met System Center Configuration Manager](../../apps/get-started/deploying-app-v-virtual-applications.md).  

### <a name="advertisements"></a>Aankondigingen  
U kunt advertenties migreren vanaf een ondersteunde Configuration Manager 2007-bronsite naar de doelhiërarchie met behulp van migratietaken op basis van een verzameling. Indien u een client updatet, behoudt hij de geschiedenis van eerder uitgevoerde advertenties om te voorkomen dat de client opnieuw gemigreerde advertenties uitvoert.  

> [!NOTE]  
>  U kunt advertenties voor virtuele pakketten niet migreren. Dit is een uitzondering voor het migreren van advertenties.  

### <a name="applications"></a>Toepassingen  
 U kunt toepassingen migreren vanaf een ondersteunde bronhiërarchie System Center 2012 Configuration Manager of System Center Configuration Manager naar een doelhiërarchie. Indien u een client opnieuw toewijst vanaf een bronhiërarchie naar de doelhiërarchie, behoudt de client de geschiedenis van voordien geïnstalleerde toepassingen om te voorkomen dat de client opnieuw een gemigreerde toepassing uitvoert.  

##  <a name="BKMK_MigrateCollections"></a>Migreren van verzamelingen  
 U kunt de criteria voor verzamelingen migreren vanaf een ondersteunde bronhiërarchie System Center 2012 Configuration Manager of System Center Configuration Manager. Voor dit gebruikt u een object gebaseerde migratietaak. Wanneer u een verzameling migreert, migreert u de regels voor de verzameling en niet informatie over de leden van de verzameling of informatie of objecten gerelateerd tot leden van de verzameling.  

 Migratie van het verzamelingobject wordt niet ondersteund wanneer u van een Configuration Manager 2007-bronhiërarchie migreert.  

##  <a name="Plan_migrate_OSD"></a>Implementaties van besturingssystemen migreren  
U kunt de volgende implementatieobjecten van besturingssystemen migreren vanaf een ondersteunde bronhiërarchie:  

-   Installatiekopieën van besturingssystemen en pakketten. Het bronpad van opstartinstallatiekopieën wordt bijgewerkt naar de standaard installatiekopie-locatie voor de Windows Administrative Installation Kit (Windows AIK) op de doelsite. Het volgende zijn vereisten en beperking voor het migreren van besturingssystemen en pakketten:  

    -   Te migreren-installatiekopiebestanden, het computeraccount van de server van de SMS-Provider voor de bovenste site van de doelhiërarchie moet hebben **lezen** en **schrijven** tot de bronbestanden van de installatiekopie van Windows AIK locatie van de bronsite.  

    -   Wanneer u een installatiepakket voor een besturingssysteem migreert, zorg ervoor dat de configuratie van het pakket op de bronsite wijst naar de map die het WIM-bestand heeft en niet naar het WIM-bestand zelf. Indien het installatiepakket wijst naar het WIM-bestand, zal de migratie van het installatiepakket falen.  

    -   Wanneer u een opstartinstallatiekopie-pakket van een Configuration Manager 2007-bronsite migreert, wordt de pakket-ID van het pakket niet behouden in de doelsite. Het resultaat hiervan is dat clients in de doelhiërarchie geen opstartinstallatiekopieën kunnen gebruiken die beschikbaar zijn op gedeelde distributiepunten.  

-   Takenreeksen. Wanneer u een takenreeks die naar een clientinstallatiepakket migreert verwijst, wordt deze referentie vervangen door een verwijzing naar het clientinstallatiepakket van de doelhiërarchie.  

    > [!NOTE]  
    >  Wanneer u een takenreeks migreert, kan Configuration Manager-objecten die niet zijn in de doelhiërarchie vereist migreren. Deze objecten bevatten opstartinstallatiekopieën en clientinstallatiepakketten van Configuration Manager 2007.  

-   Stuurprogramma's en stuurprogrammapakketten.  

##  <a name="Plan_Migrate_Compliance_settings"></a>Migreren van gewenst Configuratiebeheer  
U kunt de configuratie-items en configuratiebasislijnen migreren.  

> [!NOTE]  
>  Niet-geïnterpreteerde configuratie-items uit Configuration Manager 2007-bronhiërarchieën worden niet ondersteund voor migratie. U kunt deze configuratie-items niet migreren of importeren naar de doelhiërarchie. Zie voor meer informatie over niet-geïnterpreteerde configuratie-items, niet-geïnterpreteerde configuratie-items in de [over configuratie-Items in Desired Configuration Management](http://go.microsoft.com/fwlink/?LinkId=103846) onderwerp in de Documentatiebibliotheek van Configuration Manager 2007.  

U kunt de Configuration Manager 2007-configuratiepakketten importeren. Het importproces converteert automatisch het configuratiepakketten configureren zodat het compatibel is met System Center Configuration Manager.  

##  <a name="Plan_migrate_Boundaries"></a>Migreren van grenzen  
 U kunt grenzen tussen hiërarchieën migreren. Wanneer u grenzen uit Configuration Manager 2007 migreert, migreert tegelijkertijd elke grens van de bronsite op en wordt toegevoegd aan een nieuwe grensgroep die is gemaakt in de doelhiërarchie. Wanneer u grenzen uit een System Center 2012 Configuration Manager of System Center Configuration Manager-hiërarchie migreert, wordt elke door u geselecteerde grens toegevoegd aan een nieuwe grensgroep in de doelhiërarchie.  

 Voor elke automatisch gemaakte grensgroep is locatie van inhoud ingeschakeld, maar niet sitetoewijzing. Hiermee wordt voorkomen dat grenzen voor sitetoewijzing tussen de bron- en doelhiërarchieën elkaar overlappen. Wanneer u vanaf een bronsite Configuration Manager 2007 migreert, helpt u hiermee voorkomen dat nieuwe Configuration Manager 2007-clients die worden geïnstalleerd onjuist worden toegewezen aan de doelhiërarchie. Standaard kunnen System Center Configuration Manager-clients niet automatisch toewijzen aan Configuration Manager 2007-sites.  

 Als u tijdens de migratie een distributiepunt deelt met de doelhiërarchie, migreren aan dit distributiepunt gekoppelde grenzen automatisch naar de doelhiërarchie. Migratie wordt in de doelhiërarchie een nieuwe alleen-lezen grensgroep voor elk gedeeld distributiepunt gemaakt. Als u de grenzen van het distributiepunt in de bronhiërarchie wijzigt, wordt de grensgroep in de doelhiërarchie tijdens de volgende gegevensverzamelingscyclus bijgewerkt met deze wijzigingen.  

##  <a name="Plan_Migrate_reports"></a>Plan de migratie van rapporten  
Configuration Manager biedt geen ondersteuning voor migratie van rapporten. In plaats daarvan kunt u met SQL Server Reporting Services Report Builder rapporten uit de bronhiërarchie exporteren en vervolgens in de doelhiërarchie importeren.  

> [!NOTE]  
>  Omdat er schemawijzigingen rapporten tussen Configuration Manager 2007 en System Center Configuration Manager, test u elk rapport dat u uit een Configuration Manager 2007-hiërarchie importeert om ervoor te zorgen dat het functioneert volgens verwachting.  

Zie voor meer informatie over het rapporteren van [rapportage in System Center Configuration Manager](../../core/servers/manage/reporting.md).  

##  <a name="Plan_Migrate_Org_Folders"></a>Plan bent om te migreren van organisatorische mappen en zoekmappen  
 U kunt organisatorische mappen en zoekmappen vanuit een ondersteunde bronhiërarchie naar een doelhiërarchie migreren. Bovendien vanuit een bronhiërarchie System Center 2012 Configuration Manager of System Center Configuration Manager kunt u de criteria voor een opgeslagen zoekopdracht naar een doelhiërarchie migreren.  

 Wanneer u migreert, wordt in het migratieproces standaard de structuur van uw zoekmap en beheermap gehandhaafd voor objecten en verzamelingen. In de wizard migratietaak maken op de **instellingen** pagina kunt u een migratietaak instellen voor de organisatiestructuur voor objecten niet migreren door het selectievakje voor deze optie uitschakelt. De organisatiestructuren van verzamelingen worden altijd gehandhaafd.  

 Een uitzondering hierop is een zoekmap met virtuele toepassingen. Wanneer een App-V-pakket wordt gemigreerd, wordt het App-V-pakket omgezet in een toepassing in System Center Configuration Manager. Na de migratie van de zoekmap alleen de resterende pakketten te vinden en de zoekmap kan een App-V-pakket vinden vanwege deze omzetting in een toepassing bij de App-V-pakket wordt gemigreerd.  

 Wanneer u een opgeslagen zoekopdracht van een System Center 2012 Configuration Manager of System Center Configuration Manager-bronhiërarchie migreert, migreert u de criteria voor de zoekopdracht en niet de informatie over de zoekresultaten. Migratie van een opgeslagen zoekopdracht is niet van toepassing van een Configuration Manager 2007-bronsite.  

##  <a name="Plan_Migrate_AI"></a>Plan de migratie van Asset Intelligence-aanpassingen  
 U kunt aanpassingen voor Asset Intelligence vanuit een ondersteunde bronhiërarchie naar een doelhiërarchie migreren. Er zijn geen belangrijke wijzigingen aangebracht in de structuur van Asset Intelligence-aanpassingen tussen Configuration Manager 2007 en System Center Configuration Manager.  

> [!NOTE]  
>  System Center Configuration Manager biedt geen ondersteuning voor de migratie van Asset Intelligence-objecten van een Configuration Manager 2007-site die Asset Intelligence Service 2.0 (AIS 2.0).  

##  <a name="Plan_Migrate_SWM_Rules"></a>Migreren van aanpassingen van de regels voor softwarelicentiecontrole  
 Er zijn geen belangrijke wijzigingen aangebracht in softwarelicentiecontrole tussen Configuration Manager 2007 en System Center Configuration Manager. U kunt uw regels voor softwarelicentiecontrole vanuit een ondersteunde bronhiërarchie naar een doelhiërarchie migreren.  

 Standaard worden de door u naar een doelhiërarchie gemigreerde regels voor softwarelicentiecontrole niet aan een specifieke site in de doelhiërarchie gekoppeld en zijn daarentegen van toepassing op alle clients in de hiërarchie. Wanneer u een regel voor softwarelicentiecontrole wilt laten gelden voor clients op een specifieke site, moet u de regel voor softwarelicentiecontrole bewerken na de migratie ervan.  

