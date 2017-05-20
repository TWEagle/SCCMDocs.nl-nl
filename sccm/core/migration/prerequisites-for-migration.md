---
title: Vereisten voor migratie | Microsoft-documenten
description: Begrijp de ondersteunde versies van Configuration Manager, ondersteunde bronsite talen en vereiste configuraties voor migratie.
ms.custom: na
ms.date: 3/7/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: ec976930-7467-4d3c-b33c-991bf408a74a
caps.latest.revision: 10
caps.handback.revision: 0
author: Brenduns
ms.author: brenduns
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: ee7f69bd65152deffb2456d9807e1e8fee8802ec
ms.openlocfilehash: cd90f5462ac4bb4c0a2021e6d5dde65161b9c5f6
ms.contentlocale: nl-nl
ms.lasthandoff: 05/17/2017


---
# <a name="prerequisites-for-migration-in-system-center-configuration-manager"></a>Vereisten voor migratie in System Center Configuration Manager

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*

Om te migreren vanaf een ondersteunde bronhiërarchie, moet u toegang tot elke toepasselijke Configuration Manager-bronsite en machtigingen hebben in de doelsite System Center Configuration Manager configureren en migratiebewerkingen worden uitgevoerd.  

 Gebruik de informatie in de volgende secties om te begrijpen van de versies van Configuration Manager die worden ondersteund voor migratie, plus de vereiste configuraties.  

-   [Versies van Configuration Manager die worden ondersteund voor migratie](#BKMK_SupportedMigrationVersions)  

-   [Bronsitetalen die worden ondersteund voor migratie](#BKMK_SorceSiteLanguage)  

-   [Vereiste configuraties voor migratie](#BKMK_Required_Configurations)  

##  <a name="BKMK_SupportedMigrationVersions"></a> Versies van Configuration Manager die worden ondersteund voor migratie  
 U kunt gegevens migreren vanaf een bronhiërarchie met elk van de volgende versies van Configuration Manager:  

-   Configuration Manager 2007 SP2 (oog op migratie Configuration Manager 2007 R2 of R3 op de bronsite zijn geen overweging. Zolang de bron site uitvoert SP2, sites waarop de R2- of R3-invoegtoepassing is geïnstalleerd, ondersteund voor migratie naar System Center Configuration Manager).  

-   System Center 2012 Configuration Manager SP2 of System Center 2012 R2 Configuration Manager SP1.  

    > [!TIP]  
    >  Naast de migratie, kunt u een upgrade ter plaatse van sites met System Center 2012 Configuration Manager voor System Center Configuration Manager.  

-   Een System Center Configuration Manager-hiërarchie van dezelfde of een lagere versie van System Center Configuration Manager.  

  Als u een doelhiërarchie met System Center Configuration Manager 1606 hebt, kan u migratie gebruiken om gegevens te kopiëren vanuit een bronhiërarchie waarop versie 1606 of 1602. U zou kunnen gegevens echter niet migreren vanuit een bronhiërarchie waarop 1610.  


##  <a name="BKMK_SorceSiteLanguage"></a> Bronsitetalen die worden ondersteund voor migratie  
 Wanneer u gegevens tussen hiërarchieën van Configuration Manager migreert, de gegevens worden opgeslagen in de doelhiërarchie is ingesteld in de taalneutrale indeling voor System Center Configuration Manager. Omdat de configuratie Manager2007 slaat geen gegevens in een taalneutrale indeling, moet het migratieproces objecten converteren naar deze indeling tijdens de migratie van Configuration Manager 2007. Daarom worden alleen Configuration Manager 2007-bronsites die zijn geïnstalleerd met de volgende talen ondersteund voor migratie:  

-   Engels  

-   Frans  

-   German  

-   Japans  

-   Korean  

-   Russisch  

-   Vereenvoudigd Chinees  

-   Traditioneel Chinees  

Wanneer u gegevens vanuit een System Center 2012 Configuration Manager of System Center Configuration Manager-hiërarchie migreert, zijn er geen beperkingen bronsite taal. Objecten in de database van de bronsite hebben al een taalneutrale indeling.  

##  <a name="BKMK_Required_Configurations"></a> Vereiste configuraties voor migratie  
Verderop staan de vereiste configuraties voor het gebruik van migratie en migratiebewerkingen:  

-   **Als u wilt configureren, uitvoeren en migratie bewaken in de Configuration Manager-console:**  

     Op de doelsite moet aan uw account de op rollen gebaseerde beheerbeveiligingsrol van **Infrastructuurbeheerder**worden toegewezen. Met deze beveiligingsrol worden machtigingen verleend om alle migratiebewerkingen te beheren, inclusief maken van migratietaken, opruimen, bewaken en de actie om distributiepunten te delen en bij te werken.  

-   **Gegevens verzamelen:**  

     Om ervoor te zorgen dat de doelsite gegevens kan verzamelen, moet u de volgende twee toegangaccounts op de bronsite configureren voor gebruik met elke bronsite:  

    -   **Bronsiteaccount:** Dit account wordt gebruikt voor toegang tot de SMS-Provider van de bronsite.  

        -   Voor een bronsite Configuration Manager2007 SP2 deze account vereist **lezen** machtiging voor alle bronsiteobjecten.  

        -   Voor een bronsite System Center 2012 Configuration Manager of System Center Configuration Manager deze account vereist **lezen** machtiging voor alle bronsiteobjecten, u verleent deze machtiging aan het account via op rollen gebaseerd beheer. Zie [De basisprincipes van beheer op basis van rollen voor System Center Configuration Manager](../../core/understand/fundamentals-of-role-based-administration.md) voor meer informatie over beveiligingsbereiken en beheer op basis van rollen.  

    -   **Bronsitedatabaseaccount:** Dit account wordt gebruikt voor toegang tot de SQL Server-database van de bronsite en vereist **Connect**, **Execute**, en **selecteren** machtigingen voor de database van de bronsite.  

    U kunt deze accounts configureren wanneer u een nieuwe bronhiërarchie of het verzamelen van gegevens voor een aanvullende bronsite configureert, of wanneer u de referenties voor een bronsite opnieuw configureert. Deze accounts kunnen gebruikmaken van een domeingebruikersaccount of u kunt het computeraccount van de site op het hoogste niveau van de doelhiërarchie opgeven.  

    > [!IMPORTANT]  
    >  Als u het computeraccount van de Configuration Manager voor beide toegangsaccount gebruiken, ervoor zorgen dat dit account lid is van de beveiligingsgroep **DCOM-gebruikers** in het domein waar de bronsite zich bevindt.  

    Wanneer u gegevens verzamelt, worden de volgende netwerkprotocollen en -poorten gebruikt:  

    -   NetBIOS/SMB - 445 (TCP)  

    -   RPC (WMI) - 135 (TCP)  

    -   SQL Server - De TCP-poorten die worden gebruikt door de databases van zowel de bron- als de doelsite.  

-   **Software-updates migreren:**  

     Voordat u software-updates migreert, moet u de doelhiërarchie configureren met een software-updatepunt. Zie [De migratie van software-updates plannen](../../core/migration/planning-for-the-migration-of-objects.md#Plan_migrate_Software_updates) voor meer informatie.  

-   **Distributiepunten delen:**  

     Als u distributiepunten van een bronsite correct wilt delen, moet minstens één primaire site of de centrale beheersite in de doelhiërarchie dezelfde poortnummers voor clientaanvragen gebruiken als de bronsite. Zie [Clientcommunicatiepoorten in System Center Configuration Manager configureren](../../core/clients/deploy/configure-client-communication-ports.md) voor meer informatie over clientaanvraagpoorten.  

     Voor elke bronsite worden alleen de distributiepunten gedeeld die zijn geïnstalleerd op sitesysteemservers die zijn geconfigureerd met een FQDN.  

     Daarnaast een distributiepunt deelt van een bronsite System Center 2012 Configuration Manager of System Center Configuration Manager de **Bronsiteaccount** (die toegang heeft tot de SMS-Provider voor de server van de bronsite), moeten **wijzigen** machtigingen voor de **Site** object op de bronsite. U verleent deze machtiging aan het account door gebruik te maken van beheer op basis van rollen. Zie [De basisprincipes van beheer op basis van rollen voor System Center Configuration Manager](../../core/understand/fundamentals-of-role-based-administration.md) voor meer informatie over beveiligingsbereiken en beheer op basis van rollen.  


-   **Distributiepunten bijwerken of opnieuw toewijzen:**  

     Het **Toegangsaccount voor de bronsite** dat is geconfigureerd om gegevens te verzamelen vanaf de SMS-provider van de bronsite, moet beschikken over de volgende machtigingen:  

    -   Upgrade van een distributiepunt configuratie Manager2007 moet het account vereist **lezen**, **Execute**, en **verwijderen** machtigingen voor de **Site** klasse op de siteserver van Configuration Manager2007 naar het distributiepunt verwijderen van de bronsite configuratie Manager2007  

    -   Als u wilt een System Center 2012 Configuration Manager of System Center Configuration Manager-distributiepunt opnieuw toewijst, moet de account hebben **wijzigen** machtiging voor het **Site** object op de bronsite. U verleent deze machtiging aan het account door gebruik te maken van beheer op basis van rollen. Zie [De basisprincipes van beheer op basis van rollen voor System Center Configuration Manager](../../core/understand/fundamentals-of-role-based-administration.md) voor meer informatie over beveiligingsbereiken en beheer op basis van rollen.  

     Als u een distributiepunt correct wilt bijwerken of toewijzen aan een nieuwe hiërarchie, moeten de poorten die zijn geconfigureerd voor clientaanvragen op de site waar het distributiepunt in de bronhiërarchie wordt beheerd, overeenkomen met de poorten die zijn geconfigureerd voor clientaanvragen op de doelsite waar het distributiepunt wordt beheerd. Zie [Clientcommunicatiepoorten in System Center Configuration Manager configureren](../../core/clients/deploy/configure-client-communication-ports.md) voor meer informatie over clientaanvraagpoorten.  

