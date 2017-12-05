---
title: De installatie van sites voorbereiden
titleSuffix: Configuration Manager
description: Als u van plan bent om meerdere Configuration Manager-sites te installeren, leest u deze informatie om u te helpen u tijd besparen en om fouten te voorkomen.
ms.custom: na
ms.date: 3/1/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 9089e1b5-cba4-42bd-a2de-126ef882a3af
caps.latest.revision: "5"
author: mestew
ms.author: mstewart
manager: angrobe
ms.openlocfilehash: 67f53f6f9e346835ed3e72fe45b699c86d35766a
ms.sourcegitcommit: daa080cf220835f157a23e8c8e2bd2781b869bb7
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/04/2017
---
# <a name="prepare-to-install-system-center-configuration-manager-sites"></a>Voorbereiden voor het installeren van System Center Configuration Manager-sites

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*

Als u wilt voorbereiden voor een geslaagde implementatie van een of meer System Center Configuration Manager-sites, raken met de informatie in dit artikel. Deze stappen kunnen bespaart u tijd tijdens de installatie van meerdere sites en te voorkomen dat vergissingen zult die ertoe kunnen leiden de noodzaak om opnieuw te installeren van een of meer sites.

> [!TIP]
> Bij het beheren van System Center Configuration Manager-site en hiërarchie-infrastructuur, de voorwaarden *upgrade*, *bijwerken*, en *installeren* worden gebruikt voor het beschrijven van drie afzonderlijke concepten. Zie voor meer informatie over hoe elke term wordt gebruikt, [over upgrade-, update- en installatie](/sccm/core/understand/upgrade-update-install).

## <a name="bkmk_options"></a>Opties voor het installeren van verschillende typen sites
De versie van de bronbestanden die u kunt gebruiken wanneer u een nieuwe Configuration Manager-site installeert, zijn afhankelijk van de versie van de sites die zich al in de hiërarchie (indien aanwezig). De installatiemethoden die u kunt gebruiken, is afhankelijk van het type site dat u wilt installeren.  

Voordat u een site installeert, moet u uw hiërarchie hebt gepland, en dat u begrijpt dat het type site dat u wilt installeren. Zie voor meer informatie [een sitehiërarchie ontwerpen](../../../../core/plan-design/hierarchy/design-a-hierarchy-of-sites.md).


### <a name="first-site"></a>Eerste site
De eerste site die u in een hiërarchie installeert is een zelfstandige primaire site of een centrale beheersite.

**Installatiemedia**: Als u wilt een centrale beheersite of een zelfstandige primaire site als de eerste site in een nieuwe hiërarchie installeert, moet u [een basislijnversie gebruiken](../../../../core/servers/manage/updates.md#bkmk_Baselines) van Configuration Manager. Installeer de eerste site van een nieuwe hiërarchie niet met bijgewerkte bronbestanden vanuit de [CD. Meest recente map](../../../../core/servers/manage/the-cd.latest-folder.md) van elke site.

**Installatiemethode**: U kunt beide typen site installeren met behulp van de [Configuration Manager-installatiewizard](../../../../core/servers/deploy/install/use-the-setup-wizard-to-install-sites.md), of kunt u een script te gebruiken met een [installatie vanaf de opdrachtregel in een script vastgelegd](../../../../core/servers/deploy/install/use-a-command-line-to-install-sites.md).


### <a name="additional-sites"></a>Extra sites
Nadat de eerste site is geïnstalleerd, kunt u meer sites op elk gewenst moment toevoegen. U hebt de volgende opties voor het toevoegen van sites (maximaal [ondersteund limieten](../../../../core/plan-design/configs/size-and-scale-numbers.md)):

|Site die u hebt|Type aanvullende site die kunt u installeren|
|---|---|
|Centrale beheersite|Onderliggende primaire site|
|Onderliggende primaire site|Secundaire site|
|Zelfstandige primaire site|Secundaire site (u kunt de primaire site, die de zelfstandige primaire site naar een onderliggende primaire site converteert uitbreiden)|

**Installatiemedia**: Wanneer u een centrale beheersite als u wilt uitbreiden een zelfstandige primaire site installeert, of als u een nieuwe onderliggende primaire site in een bestaande hiërarchie installeert, moet u installatiemedia (die bronbestanden bevat) die overeenkomt met de versie van de bestaande site of websites.

> [!IMPORTANT]
> Als u in de console-updates die zijn gewijzigd van de versie van de eerder geïnstalleerde sites hebt geïnstalleerd, gebruik niet de originele installatiemedia. Gebruik in plaats daarvan in dat scenario bronbestanden op uit de [CD. Meest recente map](../../../../core/servers/manage/the-cd.latest-folder.md) van een bijgewerkte site. Configuration Manager moet u bronbestanden gebruiken die overeenkomen met de versie van de bestaande site die de nieuwe site verbinding maken.

Een secundaire site moet worden geïnstalleerd vanuit de Configuration Manager-console. Op deze manier worden altijd secundaire sites geïnstalleerd met behulp van de bronbestanden van de bovenliggende primaire site.

**Installatiemethode**: De methode die u gebruikt om aanvullende sites te installeren, is afhankelijk van het type site dat u wilt installeren.
-   **Toevoegen van een centrale beheersite**:  U kunt de Setup Wizard van Configuration Manager of een script opdrachtregel gebruiken voor het installeren van de nieuwe centrale beheersite als een bovenliggende site naar uw bestaande zelfstandige primaire site. Zie voor meer informatie [uitbreiden een zelfstandige primaire site](../../../../core/servers/deploy/install/prerequisites-for-installing-sites.md#bkmk_expand).
-   **Toevoegen van een onderliggende primaire site**:  U kunt de Setup Wizard van Configuration Manager of een installatie vanaf de opdrachtregel gebruiken om toe te voegen een onderliggende primaire site onder een centrale beheersite.
-   **Toevoegen van een secundaire site**:  De Configuration Manager-console gebruiken voor het installeren van een secundaire site als een onderliggende site onder een primaire site. Andere methoden worden niet ondersteund voor het toevoegen van secundaire sites.

## <a name="bkmk_tasks"></a>Algemene taken zijn voltooid voordat u een installatie
-   **De hiërarchietopologie die u voor uw implementatie gebruiken wilt begrijpen**    
Zie voor meer informatie [een sitehiërarchie ontwerpen voor System Center Configuration Manager](../../../../core/plan-design/hierarchy/design-a-hierarchy-of-sites.md).  

-   **Bereid en afzonderlijke servers configureren om te voldoen aan de vereisten en ondersteunde configuraties voor gebruik met Configuration Manager**         
Zie voor meer informatie [Site and site system prerequisites](../../../../core/plan-design/configs/site-and-site-system-prerequisites.md) (Vereisten voor sites en sitesystemen).  

-   **SQL Server als host voor de sitedatabase installeren en configureren**     
Zie voor meer informatie [ondersteuning voor SQL Server-versies voor System Center Configuration Manager](../../../../core/plan-design/configs/support-for-sql-server-versions.md).  

-   **Uw netwerkomgeving ter ondersteuning van Configuration Manager voorbereiden**      
Zie voor meer informatie [firewalls, poorten en domeinen voorbereiden voor Configuration Manager configureren](../../../../core/plan-design/network/configure-firewalls-ports-domains.md).  

- **Als u een openbare-sleutelinfrastructuur (PKI) gebruiken wilt, moet u voorbereiden uw infrastructuur en certificaten**      
Zie voor meer informatie [PKI-certificaatvereisten voor Configuration Manager](../../../../core/plan-design/network/pki-certificate-requirements.md).

-   **De meest recente beveiligingsupdates installeren op computers die u wilt gebruiken als siteservers of sitesysteemservers en indien nodig, zodat deze opnieuw opstarten**

## <a name="bkmk_sitecodes"></a>Over sitenamen en sitecodes
Sitecodes en sitenamen worden gebruikt om te bepalen en de sites in een Configuration Manager-hiërarchie beheren. In de Configuration Manager-console de sitecode en sitenaam worden weergegeven in de &lt; *sitecode*\> - &lt;*sitenaam* \> indeling. Elke sitecode die u in uw hiërarchie gebruikt moet uniek zijn. Als het Active Directory-schema wordt uitgebreid voor Configuration Manager en uw sites gegevens publiceren, moet de sitecodes die binnen een Active Directory-forest gebruikt uniek zelfs als ze worden gebruikt in een andere Configuration Manager-hiërarchie of als deze zijn gebruikt in eerdere installaties van Configuration Manager. Zorg dat u zorgvuldig plannen van uw sitecodes en sitenamen voordat u uw hiërarchie implementeert.

### <a name="specify-a-site-code-and-site-name"></a>Geef een sitecode en sitenaam
Wanneer u Setup van Configuration Manager uitvoert, wordt u gevraagd om een sitecode en sitenaam voor de centrale beheersite, en voor elke primaire site en de installatie van secundaire site. Een sitecode moet een unieke identificatie voor elke site in de hiërarchie. Aangezien de sitecode in mapnamen wordt gebruikt, nooit de volgende namen voor de sitecode, waaronder namen die zijn gereserveerd voor Configuration Manager en Windows te gebruiken:
  -  AUX
  -  CON
  -  NUL
  -  PRN
  -  SMS

> [!NOTE]
> Setup van Configuration Manager controleert niet of een sitecode niet al in gebruik.

Om in te voeren de sitecode voor een site wanneer u Setup van Configuration Manager uitvoert, moet u drie alfanumerieke karakters invoeren. Alleen de letters *A* via *Z* en de getallen *0* via *9*, in een willekeurige combinatie in sitecodes zijn toegestaan. De volgorde van letters of cijfers heeft geen effect op de communicatie tussen sites. Het is bijvoorbeeld niet nodig als naam voor een primaire site *ABC* en een secundaire site *DEF*.

Naam van de site is een beschrijvende naam-id voor de site. U kunt alleen de tekens *A* via *Z*, *een* via *z*, *0* via *9*, en het afbreekstreepje (*-*) in sitenamen.

> [!IMPORTANT]
> Een wijziging van de sitecode of sitenaam na installatie van de site wordt niet ondersteund.

### <a name="reuse-a-site-code"></a>Een sitecode hergebruikt
Sitecodes kunnen niet worden gebruikt meer dan één keer in een hiërarchie van Configuration Manager voor een centrale beheersite of een primaire site, zelfs als de oorspronkelijke site en de sitecode is verwijderd. Als u een sitecode hergebruikt, risico u conflicterende object-ID's in uw hiërarchie. U kunt de sitecode voor een secundaire site opnieuw gebruiken als deze secundaire site en de sitecode niet langer in gebruik in uw Configuration Manager-hiërarchie of in Active Directory-forest.

## <a name="limits-and-restrictions-for-installed-sites"></a>Limieten en beperkingen voor geïnstalleerde sites
Voordat u een site installeert, is het belangrijk te begrijpen van de volgende beperkingen die betrekking hebben op sites en sitehiërarchieën:
-   Nadat Setup is uitgevoerd, kunt u de volgende site-eigenschappen niet wijzigen zonder de site verwijderen en vervolgens opnieuw installeert met behulp van de nieuwe waarden:  
  -   Map voor installatie programmabestanden  
  -   Sitecode  
  -   Sitebeschrijving  
-   Wanneer uw hiërarchie een centrale beheersite bevat:  
  -   Configuration Manager biedt geen ondersteuning voor het verplaatsen van een onderliggende primaire site uit een hiërarchie maken van een zelfstandige primaire site of te koppelen aan een andere hiërarchie. In plaats daarvan de onderliggende primaire site verwijderen en opnieuw installeren als een nieuwe zelfstandige primaire site of als een onderliggende site van de centrale beheersite van een andere hiërarchie.  


## <a name="bkmk_optionalsteps"></a>Optionele stappen voordat u Setup uitvoert
**Handmatig uitvoeren [Setup Downloader](../../../../core/servers/deploy/install/setup-downloader.md)**

Voor het downloaden van bijgewerkte installatiebestanden voor Configuration Manager, kunt u Setup Downloader uitvoeren. Als de computer waar u de installatie uitvoert niet is verbonden met Internet of als u verwacht dat meerdere siteservers te installeren, kunt u overwegen Setup Downloader om de vereiste updates te downloaden. Hier vindt u aanvullende informatie:
-  Het installatieprogramma maakt standaard verbinding met Internet te downloaden van bijgewerkte installatiebestanden.
-  Standaard worden de bestanden opgeslagen in de map Redist.
-  U kunt het installatieprogramma verwijzen naar een locatie op het netwerk waar u eerder een kopie van deze bestanden hebt opgeslagen.

**Handmatig uitvoeren [Prerequisite Checker](../../../../core/servers/deploy/install/prerequisite-checker.md)**

Om te identificeren en oplossen van problemen voordat u Setup voor de installatie van een site uitvoert en voordat u een sitesysteemrol op een server installeert, kunt u de Prerequisite Checker uitvoeren. Prerequisite Checker zorgt ervoor dat de computer voldoet aan de vereisten voor het hosten van de site of sitesysteemrol. Hier vindt u aanvullende informatie:
 -  Setup wordt standaard Prerequisite Checker uitgevoerd.
 -  Als er fouten zijn, stopt Setup totdat het probleem is opgelost.

**Stel vast welke poorten**

Optionele poorten voor sitesystemen en clients te gebruiken, kunt u identificeren. Hier vindt u aanvullende informatie:
 -  Standaard, sitesystemen en clients vooraf gedefinieerde poorten te gebruiken om te communiceren.
 -  Tijdens de installatie kunt u alternatieve poorten te configureren.

 Zie voor meer informatie [poorten die worden gebruikt in System Center Configuration Manager](../../../../core/plan-design/hierarchy/ports.md).
