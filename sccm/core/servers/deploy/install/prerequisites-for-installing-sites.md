---
title: Vereisten voor de sites
titleSuffix: Configuration Manager
description: Meer informatie over vereisten voor het installeren van de verschillende typen van System Center Configuration Manager-sites.
ms.custom: na
ms.date: 7/31/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 92b339ef-2723-4322-bec6-077b3e8846b0
caps.latest.revision: "5"
author: mestew
ms.author: mstewart
manager: angrobe
ms.openlocfilehash: 2875a90b1f2ae853563d7716fcfe634efd551fe5
ms.sourcegitcommit: daa080cf220835f157a23e8c8e2bd2781b869bb7
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/04/2017
---
# <a name="prerequisites-for-installing-system-center-configuration-manager-sites"></a>Vereisten voor het installeren van System Center Configuration Manager-sites

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*

Voordat u begint met een site-installatie, is het een goed idee om meer informatie over de vereisten voor het installeren van de verschillende typen van System Center Configuration Manager-sites.

## <a name="primary-sites-and-the-central-administration-site"></a>Primaire sites en de centrale beheersite
De volgende vereisten zijn van toepassing op een centrale beheersite als de eerste site van een hiërarchie installeert, installeer een zelfstandige primaire site of een onderliggende primaire site installeren. Als u een centrale beheersite als onderdeel van een hiërarchie-uitbreiding installeert, Zie [uitbreiden een zelfstandige primaire site](../../../../core/servers/deploy/install/prerequisites-for-installing-sites.md#bkmk_expand) in dit onderwerp.

###  <a name="bkmk_PrereqPri"></a>Vereisten voor het installeren van een primaire site of een centrale beheersite  

-   Het gebruikersaccount dat de site installeert, moet de volgende rechten hebben:  

    -   **Beheerder** op de siteservercomputer  
    -   **Beheerder** op elke computer die fungeert als host voor de **sitedatabase** of een exemplaar van de **SMS-Provider** voor de site  
    -   **Sysadmin** op het exemplaar van SQL Server die als host fungeert voor de sitedatabase  

        > [!IMPORTANT]  
        >  Als Setup is voltooid, moeten zowel het gebruikersaccount waarmee Setup wordt uitgevoerd als het computeraccount van de siteserver sysadmin-rechten voor SQL Server behouden. Verwijder de sysadmin-rechten niet van deze accounts.  

-   Als u een primaire site installeert, moet u de volgende aanvullende rechten:  
    -  **Beheerder** op extra computers waarop u het initiële beheerpunt en distributiepunt wilt installeren, en als dat niet op de siteserver  

-   Als u een nieuwe onderliggende primaire site onder een centrale beheersite installeert, moet u de volgende aanvullende rechten:  

    -   **Beheerder** op de computer die als host fungeert voor de centrale beheersite  

    -   Op rollen gebaseerde beheerrechten beschikken in Configuration Manager die equivalent aan de beveiligingsrol van zijn **infrastructuurbeheerder** of **volledige beheerder**  

-   U moet de juiste installatiemedia (bronbestanden) gebruiken en voer Setup uit vanaf die locatie. Zie voor meer informatie over de juiste bronbestanden gebruiken voor het installeren van verschillende typen sites [opties voor het installeren van verschillende typen sites](../../../../core/servers/deploy/install/prepare-to-install-sites.md#bkmk_options) in de [voorbereiden voor het installeren van sites](../../../../core/servers/deploy/install/prepare-to-install-sites.md) onderwerp.

-   De siteservercomputer moet toegang hebben tot de bijgewerkte installatiebestanden van Microsoft, in een van de volgende manieren:
    -  Voordat u de installatie begint, kunt u downloaden en sla een kopie van deze bestanden op uw lokale netwerk met behulp van [Setup Downloader](../../../../core/servers/deploy/install/setup-downloader.md).
    -  Als een lokale kopie van deze bestand is niet beschikbaar, de siteserver moet toegang tot Internet hebben, zodat deze tijdens de installatie van deze bestanden kan downloaden van Microsoft.

- Voordat u een zelfstandige primaire site met een site system serviceverbindingspuntrol geïnstalleerd uitbreiden kunt, moet u het serviceverbindingspunt verwijderen. Slechts één exemplaar van deze rol toegestaan in een hiërarchie en dit is alleen toegestaan op de bovenste site van de hiërarchie. U hebt de mogelijkheid om opnieuw te installeren van de functie tijdens de installatie van de centrale beheersite.
- De siteserver en de sitedatabasecomputers moeten voldoen aan alle vereiste configuraties. Voordat u Setup start, kunt u [handmatig Prerequisite Checker uitvoeren](../../../../core/servers/deploy/install/prerequisite-checker.md) vaststellen en oplossen van problemen.  


### <a name="bkmk_expand"></a>Vereisten voor een zelfstandige primaire site uitbreiden
Een zelfstandige primaire site moet de volgende vereisten voldoen voordat u deze naar een hiërarchie met een centrale beheersite uitbreiden kunt:

-   **U moet de nieuwe installatie van centrale beheersite met media vanaf een CD installeren. Meest recente map (die de bronbestanden bevat) die overeenkomt met de versie van de zelfstandige primaire site**

 Zorg ervoor dat een overeenkomst is versie, de bronbestanden gebruiken die is gevonden in de [CD. Meest recente map](/sccm/core/servers/manage/the-cd.latest-folder) op de zelfstandige primaire site.

 Zie voor meer informatie over de juiste bronbestanden gebruiken voor het installeren van verschillende sites, [opties voor het installeren van verschillende typen sites](../../../../core/servers/deploy/install/prepare-to-install-sites.md#bkmk_options) in de [voorbereiden voor het installeren van sites](../../../../core/servers/deploy/install/prepare-to-install-sites.md) onderwerp.


-   **De zelfstandige primaire site kan niet worden geconfigureerd om gegevens te migreren van een andere Configuration Manager-hiërarchie**  

     U moet actieve migratie naar de zelfstandige primaire site stoppen uit andere hiërarchieën van Configuration Manager en alle configuraties voor migratie verwijderen. Dit omvat migratiejobs die niet hebt voltooid, het verzamelen van gegevens en de configuratie van de actieve bronhiërarchie.  

     Dit is nodig omdat mirgratiebewerkingen worden uitgevoerd door de bovenste site van de hiërarchie en de configuraties voor migratie niet worden overgedragen naar de centrale beheersite wanneer u een zelfstandige primaire site uitbreidt.  

     Nadat u de zelfstandige primaire site uitbreiden als u de configuratie van de migratie op de primaire site, voert de centrale beheersite de migratiegerelateerde bewerkingen. Zie voor meer informatie over het configureren van de migratie [bronhiërarchieën en bronsites voor migratie naar System Center Configuration Manager configureren](../../../../core/migration/configuring-source-hierarchies-and-source-sites-for-migration.md).  

-   **Het computeraccount van de computer die als host voor de nieuwe centrale beheersite fungeert moet een lid van de gebruikersgroep op de standa enige primaire site**  

     Om te kunnen uitbreiden van de zelfstandige primaire site, het computeraccount van de nieuwe centrale beheersite moet hebben **beheerder** rechten op de zelfstandige primaire site. Dit is enkel vereist tijdens site-uitbreiding. Het account kan worden verwijderd uit de gebruikersgroep op de primaire site als site-uitbreiding is voltooid.  

-   **Het gebruikersaccount dat wordt uitgevoerd voor het installeren van de nieuwe centrale beheersite moet op rollen gebaseerde beheerrechten hebben op de zelfstandige primaire site**  

     Als u wilt een centrale beheersite installeren als onderdeel van een site-uitbreiding, moet het gebruikersaccount dat wordt uitgevoerd voor het installeren van de centrale beheersite worden gedefinieerd in op rollen gebaseerd beheer op de zelfstandige primaire site als hetzij een **volledige beheerder** of een **infrastructuurbeheerder**.  

-   **U moet de volgende sitesysteemrollen van de zelfstandige primaire site verwijderen voordat u de site kunt uitbreiden:**  

    -   Asset Intelligence-synchronisatiepunt  
    -   Endpoint Protection-punt  
    -   Serviceverbindingspunt  

   Deze sitesysteemrollen worden alleen ondersteund op de bovenste site van de hiërarchie. Daarom moet u deze sitesysteemrollen verwijderen voordat u de zelfstandige primaire site uitbreidt. Nadat u de site hebt uitgebreid, kunt u deze sitesysteemrollen op de centrale beheersite installeren.  

    Alle andere sitesysteemrollen kunnen geïnstalleerd blijven op de primaire site.  

-   **De poort voor de SQL Server Service Broker (SSB) tussen de zelfstandige primaire site en de computer die de centrale beheersite zal installeren moet openen**  

     Configuration Manager vereist om te kunnen repliceren van gegevens tussen een centrale beheersite en een primaire site, een open poort tussen de twee sites voor SSB te gebruiken. Wanneer u een centrale beheersite installeert en een zelfstandige primaire site uitbreidt, controleert de vereistencontrole niet of de poort die u voor de SSB opgeeft geopend op de primaire site is.  

**Bekende problemen wanneer u Azure-services hebt geconfigureerd:**  
Wanneer u een van de volgende Azure-services met Configuration Manager gebruiken en u wilt uitbreiden van een site, moet u verwijderen en vervolgens opnieuw de verbinding met die service maken na het uitbreiden van de site.

Services:  
-       [Operations Manager-Suite](/sccm/core/clients/manage/sync-data-microsoft-operations-management-suite) (OMS)
-       [Gereedheid voor upgrade](/sccm/core/clients/manage/upgrade/upgrade-analytics)
-       [Windows Store voor bedrijven](/sccm/apps/deploy-use/manage-apps-from-the-windows-store-for-business)

Gebruik de volgende stappen uit om dit probleem te verhelpen:
 1.    In de Configuration Manager-console door de Azure service vanuit het knooppunt Azure-services te verwijderen.
 2.    Verwijder de Tenant die is gekoppeld aan de service van het knooppunt Azure Active Directory-Tenants in de Azure-portal.  Hiermee verwijdert u ook de Azure AD-web-app die is gekoppeld aan de service.  
 3.   Configureer opnieuw de verbinding met de Azure-service voor gebruik met Configuration Manager.


## <a name="bkmk_secondary"></a>Secundaire sites
Hier volgen de vereisten voor het installeren van secundaire sites:
-   Moet de beheerder die de installatie van de secundaire site in de Configuration Manager-console configureert op rollen gebaseerde beheerrechten beschikken die gelijk aan de beveiligingsrol zijn hebben **infrastructuurbeheerder** of **volledige beheerder**.  
-   Het computeraccount van de bovenliggende primaire site moet een **beheerder** op de secundaire siteservercomputer.  
-   Wanneer de secundaire site maakt gebruik van een eerder geïnstalleerd exemplaar van SQL Server voor het hosten van de secundaire sitedatabase:  

    -   De **computeraccount** van de bovenliggende primaire site moet hebben **sysadmin** rechten voor het exemplaar van SQL Server op de secundaire siteservercomputer.  

    -   De **lokaal systeem** account van de secundaire siteservercomputer moet beschikken over **sysadmin** rechten voor het exemplaar van SQL Server op de secundaire siteservercomputer.  

        > [!IMPORTANT]  
        >  Wanneer Setup is voltooid, moeten beide accounts sysadmin-rechten voor SQL Server behouden. Verwijder de sysadmin-rechten niet van deze accounts.  

-   De secundaire siteservercomputer moet voldoen aan alle vereiste configuraties, waaronder SQL Server en de standaardsitesysteemrollen van het beheerpunt en distributiepunt.  
