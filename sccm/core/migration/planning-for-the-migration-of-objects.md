---
title: Migreer de objecten | Microsoft Docs
description: "Informatie over het plannen voor de migratie van objecten tussen hiërarchieën in een omgeving met System Center Configuration Manager."
ms.custom: na
ms.date: 1/12/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 066caf00-e419-4efb-93d3-ba4ba878297c
caps.latest.revision: "7"
caps.handback.revision: "0"
author: Brenduns
ms.author: brenduns
manager: angrobe
ms.openlocfilehash: 17f3955aa7c63a13bab03b46002f7de0b0ec38fe
ms.sourcegitcommit: 51fc48fb023f1e8d995c6c4eacfda7dbec4d0b2f
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 08/07/2017
---
# <a name="plan-for-the-migration-of-configuration-manager-objects-to-system-center-configuration-manager"></a>Plan voor de migratie van Configuration Manager-objecten naar System Center Configuration Manager

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*

Met System Center Configuration Manager kunt u veel van de verschillende objecten die gekoppeld aan verschillende functies die gevonden op een bronsite zijn kunt migreren. Gebruik de volgende secties om u te helpen plannen voor de migratie van objecten tussen hiërarchieën.  

-   [Software-updates migreren](#Plan_migrate_Software_updates)  

-   [Plan voor het migreren van inhoud](#Plan_Migrate_content)  

-   [Plan voor het migreren van verzamelingen](#BKMK_MigrateCollections)  

-   [Plan voor het migreren van implementaties van besturingssystemen](#Plan_migrate_OSD)  

-   [Plan voor het migreren van gewenst Configuratiebeheer](#Plan_Migrate_Compliance_settings)  

-   [Migratie van grenzen plannen](#Plan_migrate_Boundaries)  

-   [Migratie van rapporten plannen](#Plan_Migrate_reports)  

-   [Plannen voor het migreren van organisatorische en zoekmappen](#Plan_Migrate_Org_Folders)  

-   [Plan voor het migreren van Asset Intelligence-aanpassingen](#Plan_Migrate_AI)  

-   [Plannen voor het migreren van aanpassingen van de regels voor softwarelicentiecontrole](#Plan_Migrate_SWM_Rules)  

##  <a name="Plan_migrate_Software_updates"></a>Software-updates migreren  
 U kunt software-Updateobjecten migreren, zoals implementaties van software-updatepakketten en software-update.  

 Als u wilt migreren van objecten voor software-update, moet u eerst uw doelhiërarchie met configuraties die overeenkomen met uw bronhiërarchieomgeving instellen. Dit vereist de volgende acties:  

-   Een actief software-updatepunt in de doelhiërarchie implementeren  

-   Instellen van de catalogus met producten en talen in overeenkomst met de configuratie van uw bronhiërarchie  

-   Synchroniseren van de software-updatepunt in de doelhiërarchie met Windows Server Update Services (WSUS)  

Overweeg, als u software-updates migreert, het volgende:  

-   Migratie van software-Updateobjecten kan falen wanneer u gegevens niet zijn gesynchroniseerd in uw doelhiërarchie in overeenkomst met de configuratie van uw bronhiërarchie.  

    > [!WARNING]  
    >  Configuration Manager biedt geen ondersteuning voor gebruik van het WSUSutil-hulpprogramma gegevens synchroniseren tussen een bron- en doelhiërarchie.  

-   U kunt geen aangepaste updates migreren die gepubliceerd zijn door gebruik te maken van System Center Updates Publisher. Aangepaste updates moeten in plaats daarvan opnieuw worden gepubliceerd naar de doelhiërarchie.  

Wanneer u van een Configuration Manager 2007-bronhiërarchie migreert, wijzigt het migratieproces sommige objecten voor software-update met de indeling in gebruik door de doelhiërarchie. Gebruik de volgende tabel voor het plannen van de migratie van objecten voor software-update van Configuration Manager 2007.  

|Configuration Manager 2007-object|Objectnaam na migratie|  
|-----------------------------------|---------------------------------|  
|Lijsten met software-updates|Lijsten met software-updates worden geconverteerd naar software-updategroepen.|  
|Software-update-implementaties|Software-update-implementaties worden omgezet in implementaties en groepen bijwerken.<br /><br /> Nadat u de implementatie van een software-update van Configuration Manager 2007 migreert, moet u het inschakelen in de doelhiërarchie voordat u deze kunt implementeren.|  
|Software-updatepakketten|Software-updatepakketten blijven software-updatepakketten.|  
|Software-update-sjablonen|Software-update sjablonen blijven sjablonen voor software-update.<br /><br /> De **duur** waarde in de Configuration Manager 2007-implementatiesjablonen worden niet gemigreerd.|  

Wanneer u objecten vanaf een bronhiërarchie System Center 2012 Configuration Manager of System Center Configuration Manager migreert, worden de software-Updateobjecten niet gewijzigd.  

##  <a name="Plan_Migrate_content"></a>Plan voor het migreren van inhoud  
 U kunt inhoud migreren vanaf een ondersteunde bronhiërarchie naar uw doelhiërarchie. Voor een Configuration Manager 2007-bronhiërarchie bevat deze inhoud softwaredistributiepakketten en programma's en virtuele toepassingen, zoals Microsoft Application Virtualization (App-V). Voor System Center 2012 Configuration Manager en System Center Configuration Manager-bronhiërarchieën bevat deze inhoud toepassingen en App-V virtuele toepassingen. Wanneer u inhoud tussen hiërarchieën migreert, worden de gecomprimeerde bronbestanden migreren naar de doelhiërarchie.  

### <a name="packages-and-programs"></a>Pakketten en programma's  
 Wanneer u pakketten en programma's migreert, worden ze niet gewijzigd door migratie. Echter, voordat u deze migreert, moet u instellen elk pakket met een pad (Universal Naming Convention) bevinden voor de bronlocatie van het bestand. Als onderdeel van de configuratie van pakketten en programma's, moet u een site toewijzen in de doelhiërarchie om deze inhoud te beheren. De inhoud wordt niet gemigreerd vanaf de toegewezen site, maar na de migratie, de toegewezen site toegang heeft tot de locatie van het originele bronbestand met behulp van de UNC-toewijzing.  

 Nadat u een pakket en programma migreert naar de doelhiërarchie en terwijl de migratie van de bronhiërarchie actief blijft, kunt u de inhoud beschikbaar maken voor clients in die hiërarchie met behulp van een gedeeld distributiepunt. Om een gedeeld distributiepunt te gebruiken, moet de inhoud beschikbaar blijven op het distributiepunt op de bronsite. Zie voor meer informatie over gedeelde distributiepunten [distributiepunten delen tussen de bron- en Doelhiërarchieën](../../core/migration/planning-a-content-deployment-migration-strategy.md#About_Shared_DPs_in_Migration) in [een migratiestrategie voor inhoudsimplementatie in System Center Configuration Manager plannen](../../core/migration/planning-a-content-deployment-migration-strategy.md).  

 Voor inhoud die gemigreerd is, indien de inhoudversie wijzigt in de bronhiërarchie of de doelhiërarchie, clients geen toegang meer de inhoud van het gedeelde distributiepunt in de doelhiërarchie tot kunnen. In dit scenario moet u opnieuw de inhoud naar het herstellen van een consistente versie van het pakket tussen de bronhiërarchie en de doelhiërarchie migreren. Deze informatie wordt gesynchroniseerd tijdens de gegevensverzameling-cyclus.  

> [!TIP]  
>  Voor elk pakket dat u migreert, werkt u het pakket bij in de doelhiërarchie. Met deze actie kunnen problemen met de implementatie van het pakket op distributiepunten in de doelhiërarchie worden voorkomen. Echter, wanneer u een pakket op het distributiepunt in de doelhiërarchie, clients bijwerkt in deze hiërarchie niet meer mogelijk dat pakket ophalen van een gedeeld distributiepunt. Voor het bijwerken van een pakket in de doelhiërarchie, in de Configuration Manager-console gaat u naar de softwarebibliotheek, met de rechtermuisknop op het pakket en selecteer vervolgens **distributiepunten bijwerken**. Voer deze actie voor elk pakket dat u migreert.  

> [!TIP]  
>  U kunt Microsoft System Center Configuration Manager Package Conversion Manager gebruiken om te converteren van pakketten en programma's naar System Center Configuration Manager-toepassingen. Download Package Conversion Manager vanaf de [Microsoft Downloadcentrum](http://go.microsoft.com/fwlink/p/?LinkId=212950)-site. Zie [Configuration Manager Package Conversion Manager](http://go.microsoft.com/fwlink/p/?LinkId=247245) voor meer informatie.  

### <a name="virtual-applications"></a>Virtuele toepassingen  
Wanneer u App-V pakketten vanaf een ondersteunde Configuration Manager 2007-site migreert, converteert het migratieproces ze tot toepassingen in de doelhiërarchie. Bovendien worden gebaseerd op bestaande advertenties voor het App-V-pakket, de volgende implementatietypen gemaakt in de doelhiërarchie:  

-   Indien er geen advertenties zijn, wordt één implementatietype gecreëerd dat de standaard implementatietype-instellingen gebruikt.  

-   Indien een advertentie bestaat, wordt één implementatietype gecreëerd dat dezelfde instellingen als de Configuration Manager 2007-aankondiging gebruikt.  

-   Indien meerdere advertenties bestaan, wordt een implementatietype gemaakt voor elke Configuration Manager 2007-aankondiging door de instellingen voor deze advertentie.  

> [!IMPORTANT]  
>  Als u een eerder gemigreerde Configuration Manager 2007-App-V-pakket migreert, faalt de migratie omdat virtuele toepassingspakketten het overschrijvingsgedrag van migratie niet ondersteunen. In dit scenario moet u het gemigreerde virtuele toepassingspakket wissen van de doelhiërarchie en dan een nieuwe migratietaak maken om de virtuele toepassing te migreren.  

> [!NOTE]  
>  Nadat u een App-V-pakket migreert, kunt u de wizard inhoud bijwerken om te wijzigen van het bronpad voor implementatietypen van App-V. Zie voor meer informatie over het bijwerken van inhoud voor een implementatietype beheren implementatietypen in [beheertaken voor System Center Configuration Manager-toepassingen](../../apps/deploy-use/management-tasks-applications.md).  

Wanneer u vanaf een bronhiërarchie System Center 2012 Configuration Manager of System Center Configuration Manager migreert, kunt u objecten voor de virtuele omgeving van App-V naast App-V implementatietypes en toepassingen migreren. Zie voor meer informatie over App-V-omgevingen [virtuele toepassingen van App-V implementeren met System Center Configuration Manager](../../apps/get-started/deploying-app-v-virtual-applications.md).  

### <a name="advertisements"></a>Aankondigingen  
U kunt advertenties migreren vanaf een ondersteunde Configuration Manager 2007-bronsite naar de doelhiërarchie met behulp van een migratie op basis van een verzameling. Indien u een client updatet, behoudt hij de geschiedenis van eerder uitgevoerde advertenties om te voorkomen dat de client opnieuw gemigreerde advertenties uitvoert.  

> [!NOTE]  
>  U kunt advertenties voor virtuele pakketten niet migreren. Dit is een uitzondering voor het migreren van advertenties.  

### <a name="applications"></a>Toepassingen  
 U kunt toepassingen migreren vanaf een ondersteunde System Center 2012 Configuration Manager of System Center Configuration Manager-bronhiërarchie naar een doelhiërarchie. Indien u een client opnieuw toewijst vanaf een bronhiërarchie naar de doelhiërarchie, behoudt de client de geschiedenis van voordien geïnstalleerde toepassingen om te voorkomen dat de client opnieuw een gemigreerde toepassing uitvoert.  

##  <a name="BKMK_MigrateCollections"></a>Plan voor het migreren van verzamelingen  
 U kunt de criteria voor verzamelingen migreren vanaf een ondersteunde bronhiërarchie System Center 2012 Configuration Manager of System Center Configuration Manager. Hiervoor kunt u een object gebaseerde migratietaak. Wanneer u een verzameling migreert, migreert u de regels voor de verzameling en niet informatie over de leden van de verzameling of informatie of objecten gerelateerd tot leden van de verzameling.  

 Migratie van het verzamelingobject wordt niet ondersteund wanneer u van een Configuration Manager 2007-bronhiërarchie migreert.  

##  <a name="Plan_migrate_OSD"></a>Plan voor het migreren van implementaties van besturingssystemen  
U kunt de volgende implementatieobjecten van besturingssystemen migreren vanaf een ondersteunde bronhiërarchie:  

-   Installatiekopieën van besturingssystemen en pakketten. Het bronpad van opstartinstallatiekopieën is bijgewerkt naar de standaardlocatie van de afbeelding voor de Windows Administrative Installation Kit (Windows AIK) op de doelsite. Het volgende zijn vereisten en beperking voor het migreren van besturingssystemen en pakketten:  

    -   Als u wilt migreren afbeeldingsbestanden, het computeraccount van de server van SMS-Provider voor de bovenste site van de doelhiërarchie moet hebben **lezen** en **schrijven** machtiging voor de bronbestanden van de installatiekopie van Windows AIK locatie van de bronsite.  

    -   Wanneer u een besturingssysteeminstallatiepakket migreert, zorg ervoor dat de configuratie van het pakket op de bronsite wijst naar de map die het WIM-bestand heeft en niet naar het WIM-bestand zelf. Indien het installatiepakket wijst naar het WIM-bestand, zal de migratie van het installatiepakket falen.  

    -   Wanneer u een opstartinstallatiekopie-pakket van een Configuration Manager 2007-bronsite migreert, wordt de pakket-ID van het pakket niet behouden in de doelsite. Het resultaat hiervan is dat clients in de doelhiërarchie geen opstartinstallatiekopieën kunnen gebruiken die beschikbaar zijn op gedeelde distributiepunten.  

-   Takenreeksen. Wanneer u een takenreeks bevat een verwijzing naar een clientinstallatiepakket migreert, wordt deze referentie vervangen door een verwijzing naar het clientinstallatiepakket van de doelhiërarchie.  

    > [!NOTE]  
    >  Wanneer u een takenreeks migreert, kan Configuration Manager-objecten die niet zijn in de doelhiërarchie vereist migreren. Deze objecten bevatten opstartinstallatiekopieën en clientinstallatiepakketten van Configuration Manager 2007.  

-   Stuurprogramma's en stuurprogrammapakketten. Wanneer u stuurprogrammapakketten migreert, moet het computeraccount van de SMS-Provider in de doelhiërarchie volledig beheer hebben voor de pakketbron.

##  <a name="Plan_Migrate_Compliance_settings"></a>Plan voor het migreren van gewenst Configuratiebeheer  
U kunt de configuratie-items en configuratiebasislijnen migreren.  

> [!NOTE]  
>  Niet-geïnterpreteerde configuratie-items uit Configuration Manager 2007-bronhiërarchieën worden niet ondersteund voor migratie. U kunt deze configuratie-items niet migreren of importeren naar de doelhiërarchie. Zie voor meer informatie over niet-geïnterpreteerde configuratie-items, niet-geïnterpreteerde configuratie-items in de [over configuratie-Items in Desired Configuration Management](http://go.microsoft.com/fwlink/?LinkId=103846) onderwerp in de Configuration Manager 2007-documentatiebibliotheek.  

U kunt de Configuration Manager 2007-configuratiepakketten importeren. Het importproces converteert automatisch de configuratiepakketten zodat het compatibel is met System Center Configuration Manager.  

##  <a name="Plan_migrate_Boundaries"></a>Migratie van grenzen plannen  
 U kunt grenzen tussen hiërarchieën migreren. Wanneer u grenzen uit Configuration Manager 2007 migreert, migreert tegelijkertijd door elke grens van de bronsite en wordt toegevoegd aan een nieuwe grensgroep die is gemaakt in de doelhiërarchie. Wanneer u grenzen uit een System Center 2012 Configuration Manager of System Center Configuration Manager-hiërarchie migreert, wordt elke door die u geselecteerde toegevoegd aan een nieuwe grensgroep in de doelhiërarchie.  

 Voor elke automatisch gemaakte grensgroep is locatie van inhoud ingeschakeld, maar niet sitetoewijzing. Hiermee wordt voorkomen dat grenzen voor sitetoewijzing tussen de bron- en doelhiërarchieën elkaar overlappen. Wanneer u van een Configuration Manager 2007-bronsite migreert, helpt u hiermee voorkomen dat nieuwe Configuration Manager 2007-clients die worden geïnstalleerd onjuist worden toegewezen aan de doelhiërarchie. Standaard toewijzen System Center Configuration Manager-clients geen automatisch aan Configuration Manager 2007-sites.  

 Als u tijdens de migratie een distributiepunt deelt met de doelhiërarchie, migreren aan dit distributiepunt gekoppelde grenzen automatisch naar de doelhiërarchie. Migratie maakt in de doelhiërarchie een nieuwe alleen-lezen grensgroep voor elk gedeeld distributiepunt. Als u de grenzen van het distributiepunt in de bronhiërarchie wijzigt, wordt de grensgroep in de doelhiërarchie tijdens de volgende gegevensverzamelingscyclus bijgewerkt met deze wijzigingen.  

##  <a name="Plan_Migrate_reports"></a>Migratie van rapporten plannen  
Configuration Manager biedt geen ondersteuning voor migratie van rapporten. In plaats daarvan kunt u met SQL Server Reporting Services Report Builder rapporten uit de bronhiërarchie exporteren en vervolgens in de doelhiërarchie importeren.  

> [!NOTE]  
>  Omdat er wijzigingen in het schema voor Configuration Manager 2007 en System Center Configuration Manager-rapporten, test u elk rapport dat u uit een Configuration Manager 2007-hiërarchie importeert om ervoor te zorgen dat het functioneert volgens verwachting.  

Zie voor meer informatie over het rapporteren van [rapportage in System Center Configuration Manager](../../core/servers/manage/reporting.md).  

##  <a name="Plan_Migrate_Org_Folders"></a>Plannen voor het migreren van organisatorische en zoekmappen  
 U kunt organisatorische mappen en zoekmappen vanuit een ondersteunde bronhiërarchie naar een doelhiërarchie migreren. Bovendien vanuit een bronhiërarchie System Center 2012 Configuration Manager of System Center Configuration Manager kunt u de criteria voor een zoekopdracht naar een doelhiërarchie migreren.  

 Wanneer u migreert, wordt in het migratieproces standaard de structuur van uw zoekmap en beheermap gehandhaafd voor objecten en verzamelingen. Echter, in de wizard migratietaak maken op de **instellingen** pagina kunt u een migratietaak instellen voor het migreren van de organisatiestructuur voor objecten niet door het selectievakje voor deze optie uitschakelt. De organisatiestructuren van verzamelingen worden altijd gehandhaafd.  

 Een uitzondering hierop is een zoekmap met virtuele toepassingen. Wanneer een App-V-pakket wordt gemigreerd, wordt het App-V-pakket omgezet in een toepassing in System Center Configuration Manager. Na de migratie van de zoekmap alleen de resterende pakketten te vinden en de zoekmap kan een App-V-pakket niet vinden vanwege deze omzetting in een toepassing wanneer de App-V-pakket wordt gemigreerd.  

 Wanneer u een opgeslagen zoekopdracht van een System Center 2012 Configuration Manager of System Center Configuration Manager-bronhiërarchie migreert, migreert u de criteria voor de zoekopdracht en niet de informatie over de zoekresultaten. Migratie van een opgeslagen zoekopdracht is niet toepasselijk vanuit een Configuration Manager 2007-bronsite.  

##  <a name="Plan_Migrate_AI"></a>Plan voor het migreren van Asset Intelligence-aanpassingen  
 U kunt aanpassingen voor Asset Intelligence vanuit een ondersteunde bronhiërarchie naar een doelhiërarchie migreren. Er zijn geen belangrijke wijzigingen in de structuur van Asset Intelligence-aanpassingen tussen Configuration Manager 2007 en System Center Configuration Manager.  

> [!NOTE]  
>  System Center Configuration Manager biedt geen ondersteuning voor de migratie van Asset Intelligence-objecten van een Configuration Manager 2007-site die Asset Intelligence Service 2.0 (AIS 2.0) gebruikt.  

##  <a name="Plan_Migrate_SWM_Rules"></a>Plannen voor het migreren van aanpassingen van de regels voor softwarelicentiecontrole  
 Er zijn geen belangrijke wijzigingen aangebracht in softwarelicentiecontrole tussen Configuration Manager 2007 en System Center Configuration Manager. U kunt uw regels voor softwarelicentiecontrole vanuit een ondersteunde bronhiërarchie naar een doelhiërarchie migreren.  

 Standaard worden de door u naar een doelhiërarchie gemigreerde regels voor softwarelicentiecontrole niet aan een specifieke site in de doelhiërarchie gekoppeld en zijn daarentegen van toepassing op alle clients in de hiërarchie. Wanneer u een regel voor softwarelicentiecontrole wilt laten gelden voor clients op een specifieke site, moet u de regel voor softwarelicentiecontrole bewerken na de migratie ervan.  
