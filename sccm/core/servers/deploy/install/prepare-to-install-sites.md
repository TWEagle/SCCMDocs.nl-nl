---
title: Voorbereiden om sites te installeren | Microsoft-documenten
description: Als u van plan bent om meerdere Configuration Manager-sites te installeren, leest u deze informatie om u tijd besparen en om fouten te voorkomen.
ms.custom: na
ms.date: 3/1/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 9089e1b5-cba4-42bd-a2de-126ef882a3af
caps.latest.revision: 5
author: Brenduns
ms.author: brenduns
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 73c34d40d70fb3ae5f8702f3d5f1e5b51a1b28a7
ms.openlocfilehash: 829f2d44a9b8d203a5b753ebb6d8f759b1a05111
ms.contentlocale: nl-nl
ms.lasthandoff: 05/17/2017

---
# <a name="prepare-to-install-system-center-configuration-manager-sites"></a>Voorbereiden voor het installeren van System Center Configuration Manager-sites

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*

Om voor te bereiden voor implementatie van een of meer System Center Configuration Manager-sites, vertrouwd zijn met de informatie in dit artikel. Deze stappen kunnen opslaan u tijd tijdens de installatie van meerdere sites en vergissingen zult die ertoe leiden kunnen bij het installeren van een of meer sites moet voorkomen.

> [!TIP]
> Bij het beheren van System Center Configuration Manager-site en hiërarchie-infrastructuur, de voorwaarden *upgrade*, *bijwerken*, en *installeren* worden gebruikt om te beschrijven van drie verschillende concepten. Zie voor meer informatie over hoe elke term wordt gebruikt, [over upgrade-, update- en installatie](/sccm/core/understand/upgrade-update-install).

## <a name="bkmk_options"></a>Opties voor het installeren van de verschillende soorten sites
De versie van de bronbestanden die u kunt gebruiken wanneer u een nieuwe Configuration Manager-site installeert, zijn afhankelijk van de versie van sites die zich al in de hiërarchie (indien aanwezig). De installatiemethoden die u kunt gebruiken, is afhankelijk van het type site dat u wilt installeren.  

Installatie van een site, zorg er voordat u uw hiërarchie hebt gepland en dat u bekend bent met het type site dat u wilt installeren. Zie voor meer informatie [ontwerpen van een hiërarchie van sites](../../../../core/plan-design/hierarchy/design-a-hierarchy-of-sites.md).


### <a name="first-site"></a>Eerste site
De eerste site die u in een hiërarchie installeert zich op een zelfstandige primaire site of een centrale beheersite.

**Installatiemedia**: Voor het installeren van een centrale beheersite of een zelfstandige primaire site als de eerste site in een nieuwe hiërarchie, moet u [basislijn versie](../../../../core/servers/manage/updates.md#bkmk_Baselines) van Configuration Manager. Installeer de eerste site van een nieuwe hiërarchie met bijgewerkte bronbestanden van de [CD. Meest recente map](../../../../core/servers/manage/the-cd.latest-folder.md) van elke site.

**Installatiemethode**: U kunt een van beide typen site installeren met behulp van de [Configuration Manager-installatiewizard](../../../../core/servers/deploy/install/use-the-setup-wizard-to-install-sites.md), of kunt u een script dat wordt gebruikt met een [installatie vanaf de opdrachtregel in een script vastgelegd](../../../../core/servers/deploy/install/use-a-command-line-to-install-sites.md).


### <a name="additional-sites"></a>Extra sites
Nadat de eerste site is geïnstalleerd, kunt u meer sites op elk gewenst moment toevoegen. U hebt de volgende opties voor het toevoegen van sites (maximaal [ondersteund limieten](../../../../core/plan-design/configs/size-and-scale-numbers.md)):

|Site die u hebt|Type aanvullende site die kunt u installeren|
|---|---|
|Centrale beheersite|Onderliggende primaire site|
|Onderliggende primaire site|Secundaire site|
|Zelfstandige primaire site|Secundaire site (u kunt de primaire site waarmee de zelfstandige primaire site wordt geconverteerd naar een onderliggende primaire site uitbreiden)|

**Installatiemedia**: Wanneer u een centrale beheersite installeert om een zelfstandige primaire site uitbreidt, of als u een nieuwe onderliggende primaire site in een bestaande hiërarchie installeert, moet u de installatiemedia (die bronbestanden bevat) gebruiken die overeenkomt met de versie van de bestaande site of websites.

> [!IMPORTANT]
> Als u in de console-updates die zijn gewijzigd, de versie van de eerder geïnstalleerde sites hebt geïnstalleerd, gebruik niet de originele installatiemedia. Gebruik in plaats daarvan in dat scenario bronbestanden van de [CD. Meest recente map](../../../../core/servers/manage/the-cd.latest-folder.md) van een bijgewerkte site. Configuration Manager moet u bronbestanden gebruiken die overeenkomen met de versie van de bestaande site die de nieuwe site wordt de verbinding.

Een secundaire site moet worden geïnstalleerd vanaf de Configuration Manager-console. Op deze manier worden altijd secundaire sites geïnstalleerd met behulp van de bronbestanden van de bovenliggende primaire site.

**Installatiemethode**: De methode die u gebruikt om bijkomende sites te installeren, is afhankelijk van het type site dat u wilt installeren.
-   **Toevoegen van een centrale beheersite**:  Kunt u de installatiewizard van Configuration Manager of een script opdrachtregel te gebruiken voor het installeren van de nieuwe centrale beheersite als een bovenliggende site aan uw bestaande zelfstandige primaire site. Zie voor meer informatie [uitbreiden een zelfstandige primaire site](../../../../core/servers/deploy/install/prerequisites-for-installing-sites.md#bkmk_expand).
-   **Toevoegen van een onderliggende primaire site**:  U kunt de installatiewizard van Configuration Manager of een installatie vanaf de opdrachtregel toevoegen van een onderliggende primaire site onder een centrale beheersite.
-   **Toevoegen van een secundaire site**:  De Configuration Manager-console gebruiken om een secundaire site installeren als een onderliggende site onder een primaire site. Andere methoden worden niet ondersteund voor het toevoegen van secundaire sites.

## <a name="bkmk_tasks"></a>Algemene taken die moeten worden voltooid voordat u een installatie
-   **De hiërarchie-topologie die u voor uw implementatie gebruiken wilt begrijpen**    
Zie voor meer informatie [ontwerpen van een hiërarchie van sites voor System Center Configuration Manager](../../../../core/plan-design/hierarchy/design-a-hierarchy-of-sites.md).  

-   **Bereid en afzonderlijke servers configureren om te voldoen aan de vereisten en ondersteunde configuraties voor gebruik met Configuration Manager**         
Zie voor meer informatie [Site and site system prerequisites](../../../../core/plan-design/configs/site-and-site-system-prerequisites.md) (Vereisten voor sites en sitesystemen).  

-   **SQL Server als host voor de sitedatabase installeren en configureren**     
Zie voor meer informatie [ondersteuning voor versies van SQL Server voor System Center Configuration Manager](../../../../core/plan-design/configs/support-for-sql-server-versions.md).  

-   **Bereid de netwerkomgeving voor de ondersteuning van Configuration Manager**      
Zie voor meer informatie [configureren van firewalls, poorten en domeinen voorbereiden voor Configuration Manager](../../../../core/plan-design/network/configure-firewalls-ports-domains.md).  

- **Als u een openbare-sleutelinfrastructuur (PKI) gebruiken wilt, maakt u de infrastructuur en certificaten**      
Zie voor meer informatie [PKI-certificaatvereisten voor Configuration Manager](../../../../core/plan-design/network/pki-certificate-requirements.md).

-   **De meest recente beveiligingsupdates op computers die u wilt gebruiken als siteservers of sitesysteemservers en indien nodig, opnieuw installeren**

## <a name="bkmk_sitecodes"></a>Over sitenamen en sitecodes
Sitecodes en sitenamen worden gebruikt om te bepalen en beheren van de sites in een Configuration Manager-hiërarchie. In de Configuration Manager-console de sitecode en sitenaam worden weergegeven in de &lt; *sitecode*\> - &lt;*sitenaam* \> indeling. Elke sitecode die u in uw hiërarchie gebruikt moet uniek zijn. Als het Active Directory-schema wordt uitgebreid voor Configuration Manager en uw sites gegevens publiceren, moet de sitecodes die binnen een Active Directory-forest gebruikt uniek zelfs als ze worden gebruikt in een andere Configuration Manager-hiërarchie of als ze in eerdere installaties van Configuration Manager zijn gebruikt. Zorg ervoor dat goede planning maakt voor uw sitecodes en sitenamen voordat u uw hiërarchie implementeert.

### <a name="specify-a-site-code-and-site-name"></a>Een sitecode en sitenaam specificeren
Wanneer u Configuration Manager Setup uitvoert, wordt u gevraagd om een sitecode en sitenaam voor de centrale beheersite, en voor elke primaire site en de installatie van secundaire site. Een sitecode moet een unieke identificatie van elke site in de hiërarchie. Aangezien de sitecode in mapnamen wordt gebruikt, nooit de volgende namen voor de sitecode, waaronder de namen die zijn gereserveerd voor Configuration Manager en Windows te gebruiken:
  -  AUX
  -  CON
  -  NUL
  -  PRN
  -  SMS

> [!NOTE]
> Installatie van Configuration Manager controleert niet of een sitecode niet al gebruikt wordt.

Als u wilt de sitecode invoeren voor een site wanneer u de installatie van Configuration Manager uitvoert, moet u drie alfanumerieke karakters invoeren. Alleen de letters *A* via *Z* en de cijfers *0* via *9*, in een willekeurige combinatie in sitecodes zijn toegestaan. De volgorde van letters of cijfers heeft geen effect op de communicatie tussen sites. Bijvoorbeeld, het is niet noodzakelijk om een primaire site de naam *ABC* en een secundaire site *DEF*.

De sitenaam is een beschrijvende naam voor de site. U kunt alleen de tekens *A* via *Z*, *een* via *z*, *0* via *9*, en het koppelteken (*-*) in sitenamen.

> [!IMPORTANT]
> Een wijziging van de sitecode of sitenaam na installatie van de site wordt niet ondersteund.

### <a name="reuse-a-site-code"></a>Een sitecode hergebruikt
Sitecodes kunnen niet worden gebruikt meer dan één keer in een hiërarchie van Configuration Manager voor een centrale beheersite of een primaire site, zelfs als de originele site en de sitecode is verwijderd. Als u een sitecode hergebruikt, kunnen de conflicterende object-ID's in uw hiërarchie. U kunt de sitecode voor een secundaire site opnieuw gebruiken als deze secundaire site en de sitecode niet langer in gebruik in uw Configuration Manager-hiërarchie of in Active Directory-forest zijn.

## <a name="limits-and-restrictions-for-installed-sites"></a>Limieten en -beperkingen voor geïnstalleerde sites
Voordat u een site installeert, is het belangrijk om te begrijpen van de volgende beperkingen die betrekking hebben op sites en sitehiërarchieën:
-   Nadat Setup is uitgevoerd, kunt u de volgende site-eigenschappen niet wijzigen zonder de site verwijderen en vervolgens opnieuw installeert met behulp van de nieuwe waarden:  
  -   Installatiemap programma  
  -   Sitecode  
  -   Beschrijving van site  
-   Wanneer uw hiërarchie een centrale beheersite bevat:  
  -   Configuration Manager biedt geen ondersteuning voor het verplaatsen van een onderliggende primaire site uit een hiërarchie een zelfstandige primaire site maken of te koppelen aan een andere hiërarchie. In plaats daarvan de onderliggende primaire site verwijderen en opnieuw installeren als een nieuwe zelfstandige primaire site of als een onderliggende site van de centrale beheersite van een andere hiërarchie.  


## <a name="bkmk_optionalsteps"></a>Optionele stap voordat u Setup uitvoert
**Handmatig uitvoeren [Setup Downloader](../../../../core/servers/deploy/install/setup-downloader.md)**

U kunt de bijgewerkte instellingen om bestanden te downloaden voor Configuration Manager, Setup Downloader uitvoeren. Als de computer waarop u Setup wordt uitgevoerd niet is verbonden met het Internet, of als u van plan meerdere siteservers te installeren, kunt u overwegen Downloadprogramma om de vereiste updates te downloaden. Hier vindt u aanvullende informatie:
-  Standaard verbindt Setup met het Internet te downloaden van bijgewerkte Setup-bestanden.
-  Standaard worden de bestanden opgeslagen in de map Redist.
-  Setup kunt u sturen naar een locatie op uw netwerk waar u eerder een kopie van deze bestanden hebt opgeslagen.

**Handmatig uitvoeren [vereistencontrole](../../../../core/servers/deploy/install/prerequisite-checker.md)**

Om te identificeren en oplossen van problemen, vóór u Startup uitvoert om een site te installeren en voordat u een sitesysteemrol op een server installeert, kunt u Prerequisite Checker uitvoeren. Prerequisite Checker zorgt ervoor dat de computer voldoet aan de vereisten voor het hosten van de site of sitesysteemrol. Hier vindt u aanvullende informatie:
 -  Standaard voert installatieprogramma Prerequisite Checker.
 -  Als er fouten zijn, wordt Setup stopt totdat het probleem is opgelost.

**Optionele poorten identificeren**

U kunt optionele poorten voor sitesystemen en clients gebruik kunnen identificeren. Hier vindt u aanvullende informatie:
 -  Standaard gebruik sitesystemen en clients van vooraf gedefinieerde poorten om te communiceren.
 -  U kunt andere poorten configureren tijdens de installatie.

 Zie voor meer informatie [poorten die worden gebruikt in System Center Configuration Manager](../../../../core/plan-design/hierarchy/ports.md).

