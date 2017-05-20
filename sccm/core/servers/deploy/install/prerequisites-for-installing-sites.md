---
title: Vereisten voor de sites | Microsoft-documenten
description: Meer informatie over vereisten voor het installeren van de verschillende typen van System Center Configuration Manager-sites.
ms.custom: na
ms.date: 3/27/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 92b339ef-2723-4322-bec6-077b3e8846b0
caps.latest.revision: 5
author: Brenduns
ms.author: brenduns
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: dab5da5a4b5dfb3606a8a6bd0c70a0b21923fff9
ms.openlocfilehash: ff89d4aea6be871e64e0a788f054ba4cadb3e51d
ms.contentlocale: nl-nl
ms.lasthandoff: 05/17/2017

---
# <a name="prerequisites-for-installing-system-center-configuration-manager-sites"></a>Vereisten voor het installeren van System Center Configuration Manager-sites

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*

Voordat u begint met een site-installatie, is een goed idee voor meer informatie over de vereisten voor het installeren van de verschillende typen van System Center Configuration Manager-sites.

## <a name="primary-sites-and-the-central-administration-site"></a>Primaire sites en de centrale beheersite
De volgende vereisten van toepassing op een centrale beheersite als de eerste site van een hiërarchie installeert, installeert een zelfstandige primaire site of een onderliggende primaire site installeren. Als u een centrale beheersite als onderdeel van een hiërarchie-uitbreiding installeert, Zie [uitbreiden een zelfstandige primaire site](../../../../core/servers/deploy/install/prerequisites-for-installing-sites.md#bkmk_expand) in dit onderwerp.

###  <a name="bkmk_PrereqPri"></a>Vereisten voor het installeren van een primaire site of een centrale beheersite  

-   Het gebruikersaccount dat de site installeert, moet de volgende rechten hebben:  

    -   **Beheerder** op de siteservercomputer  
    -   **Beheerder** op elke computer die fungeert als host voor de **sitedatabase** of een exemplaar van de **SMS-Provider** voor de site  
    -   **Sysadmin** op het exemplaar van SQL Server die als host fungeert voor de sitedatabase  

        > [!IMPORTANT]  
        >  Wanneer Setup is voltooid, moeten de gebruikersaccount die het installatieprogramma uitvoert en de computeraccount van de siteserver sysadmin-rechten voor SQL Server bewaren. Verwijder de sysadmin-rechten van deze accounts.  

-   Als u een primaire site installeert, moet u de volgende aanvullende rechten:  
    -  **Beheerder** op extra computers waarop u het eerste beheerpunt en distributiepunt wilt installeren, op de siteserver  

-   Als u een nieuwe onderliggende primaire site onder een centrale beheersite installeert, moet u de volgende aanvullende rechten:  

    -   **Beheerder** op de computer die als host fungeert voor de centrale beheersite  

    -   Op rollen gebaseerde beheerrechten beschikken in Configuration Manager die gelijk aan de beveiligingsrol zijn **infrastructuurbeheerder** of **volledige beheerder**  

-   U moet de juiste installatiemedia (bronbestanden) gebruiken en voer Setup uit vanaf die locatie. Zie voor meer informatie over de juiste bronbestanden moet worden gebruikt voor het installeren van verschillende typen sites [opties voor het installeren van de verschillende soorten sites](../../../../core/servers/deploy/install/prepare-to-install-sites.md#bkmk_options) in de [voorbereiden om sites te installeren](../../../../core/servers/deploy/install/prepare-to-install-sites.md) onderwerp.

-   De siteservercomputer moet toegang hebben tot de bijgewerkte installatiebestanden van Microsoft, in een van de volgende manieren:
    -  Voordat u de installatie, kunt u downloaden en opslaan van een kopie van deze bestanden op uw lokale netwerk via [Downloadprogramma](../../../../core/servers/deploy/install/setup-downloader.md).
    -  Als een lokale kopie van moet deze bestand is niet beschikbaar, de siteserver toegang tot Internet zodat deze tijdens de installatie van deze bestanden kan downloaden van Microsoft.

- Voordat u een zelfstandige primaire site met een service connection point sitesysteemrol geïnstalleerd uitbreiden kunt, moet u de service connection point verwijderen. Slechts één exemplaar van deze rol is toegestaan in een hiërarchie en dit is alleen toegestaan op de bovenste site van de hiërarchie. U hebt de mogelijkheid om de rol installeren tijdens de installatie van de centrale beheersite.
- De siteserver en computers voor site-database moeten voldoen aan alle vereiste configuraties. Voordat u Setup start, kunt u [Prerequisite Checker handmatig uitvoeren](../../../../core/servers/deploy/install/prerequisite-checker.md) te identificeren en oplossen van problemen.  


### <a name="bkmk_expand"></a>Vereisten voor een zelfstandige primaire site uitbreiden
Een zelfstandige primaire site moet voldoen aan de volgende vereisten voordat u deze naar een hiërarchie met een centrale beheersite uitbreiden kunt:

-   **U moet de nieuwe installatie van centrale beheersite met media vanaf een CD installeren. Meest recente map (die de bronbestanden bevat) die overeenkomt met de versie van de zelfstandige primaire site**

 Zorg ervoor dat een overeenkomst versie, de bronbestanden gevonden in de [CD. Meest recente map](/sccm/core/servers/manage/the-cd.latest-folder) op de zelfstandige primaire site.

 Zie voor meer informatie over de juiste bronbestanden moet worden gebruikt om verschillende sites te installeren, [opties voor het installeren van de verschillende soorten sites](../../../../core/servers/deploy/install/prepare-to-install-sites.md#bkmk_options) in de [voorbereiden om sites te installeren](../../../../core/servers/deploy/install/prepare-to-install-sites.md) onderwerp.


-   **De zelfstandige primaire site kan niet worden geconfigureerd om gegevens te migreren vanaf een andere Configuration Manager-hiërarchie**  

     U moet actieve migratie naar de zelfstandige primaire site stoppen van andere Configuration Manager-hiërarchieën en alle configuraties voor migratie verwijderen. Dit omvat migratiejobs die nog niet voltooid, het verzamelen van gegevens en de configuratie van de actieve bronhiërarchie.  

     Dit is nodig omdat mirgratiebewerkingen worden uitgevoerd door de bovenste site van de hiërarchie en de configuraties voor migratie niet worden overgedragen naar de centrale beheersite wanneer u een zelfstandige primaire site uitbreidt.  

     Nadat u de zelfstandige primaire site uitgebreid als u migratie op de primaire site opnieuw configureert, uitvoert de centrale beheersite de migratiegerelateerde bewerkingen. Zie voor meer informatie over het configureren van migratie [bronhiërarchieën en bronsites voor migratie naar System Center Configuration Manager configureren](../../../../core/migration/configuring-source-hierarchies-and-source-sites-for-migration.md).  

-   **De computeraccount van de computer die als voor de nieuwe centrale beheersite host fungeert moet lid zijn van de beheergroep van de gebruiker op de primaire site standa alleenstaande**  

     Om te kunnen uitbreiden de zelfstandige primaire site, het computeraccount van de nieuwe centrale beheersite moet hebben **Administrator** -rechten op de zelfstandige primaire site. Dit is enkel vereist tijdens site-uitbreiding. De account kan worden verwijderd uit de gebruikersgroep op de primaire site als site-uitbreiding is voltooid.  

-   **De gebruikersaccount die het installatieprogramma voor het installeren van de nieuwe centrale beheersite uitvoert moet op rollen gebaseerde beheerdersrechten hebben op de zelfstandige primaire site**  

     Als u wilt een centrale beheersite installeren als onderdeel van een site-uitbreiding, het gebruikersaccount dat de installatie uitvoert om te installeren van de centrale beheersite moet worden gedefinieerd in op rollen gebaseerd beheer op de zelfstandige primaire site als hetzij een **volledige beheerder** of een **infrastructuurbeheerder**.  

-   **U moet de volgende sitesysteemrollen van de zelfstandige primaire site verwijderen voordat u de site kunt uitbreiden.**  

    -   Asset Intelligence-synchronisatiepunt  
    -   Endpoint Protection-punt  
    -   Serviceverbindingspunt  

   Deze sitesysteemrollen worden alleen op de site op hoogste niveau van de hiërarchie ondersteund. Daarom moet u deze sitesysteemrollen verwijderen voordat u de zelfstandige primaire site uitbreidt. Nadat u de site uitbreidt, kunt u deze sitesysteemrollen op de centrale beheersite kunt installeren.  

    Alle andere sitesysteemrollen kunnen geïnstalleerd blijven op de primaire site.  

-   **De poort voor de SQL Server Service Broker (SSB) tussen de zelfstandige primaire site en de computer die de centrale beheersite zal installeren moet open zijn.**  

     Configuration Manager vereist om te kunnen repliceren van gegevens tussen een centrale beheersite en een primaire site, een open poort tussen de twee sites voor SSB te gebruiken. Wanneer u een centrale beheersite installeert en een zelfstandige primaire site uitbreidt, controleert de vereistencontrole niet of de poort die u voor de SSB opgeeft open op de primaire site is.  


## <a name="bkmk_secondary"></a>Secundaire sites
Hier volgen de vereisten voor het installeren van secundaire sites:
-   Moet de beheerder die de installatie van de secundaire site in de Configuration Manager-console configureert op rollen gebaseerde beheerrechten beschikken die equivalent aan de beveiligingsrol zijn hebben **infrastructuurbeheerder** of **volledige beheerder**.  
-   Het computeraccount van de bovenliggende primaire site moet een **Administrator** op de servercomputer van de secundaire site.  
-   Als de secundaire site een eerder geïnstalleerd exemplaar van SQL Server gebruikt voor het hosten van de secundaire sitedatabase:  

    -   De **computeraccount** van de bovenliggende primaire site moet hebben **sysadmin** rechten voor het exemplaar van SQL Server op de servercomputer van de secundaire site.  

    -   De **lokaal systeem** account van de secundaire siteservercomputer moet beschikken over **sysadmin** rechten voor het exemplaar van SQL Server op de servercomputer van de secundaire site.  

        > [!IMPORTANT]  
        >  Als Setup is voltooid, moeten beide accounts sysadmin-rechten voor SQL Server behouden. Verwijder de sysadmin-rechten van deze accounts.  

-   De secundaire siteservercomputer moet voldoen aan alle vereiste configuraties, waaronder SQL Server en de standaardsitesysteemrollen van het beheerpunt en distributiepunt.  

