---
title: "De grondbeginselen van sites en hiërarchieën"
titleSuffix: Configuration Manager
description: "Algemene informatie over System Center Configuration Manager-sites en hiërarchieën worden opgehaald."
ms.custom: na
ms.date: 12/30/2016
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 4db1e15f-e832-4cf9-be33-d3971e635a55
caps.latest.revision: "6"
author: aaroncz
ms.author: aaroncz
manager: angrobe
ms.openlocfilehash: 3e1cd18a3791b6ad009ca21851bb7173f8510f71
ms.sourcegitcommit: 7fe45ff75f05f7cc03ad021db8119791abe18049
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/01/2017
---
# <a name="fundamentals-of-sites-and-hierarchies-for-system-center-configuration-manager"></a>De grondbeginselen van sites en hiërarchieën voor System Center Configuration Manager

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*

Een System Center Configuration Manager-implementatie moet worden geïnstalleerd in een Active Directory-domein. De basis van deze implementatie bevat een of meer Configuration Manager-sites die een hiërarchie van sites vormen. Voor een hiërarchie die uit een enkele site bestaat en voor een hiërarchie die uit meerdere sites bestaat, geldt dat het type en de locatie van sites die u installeert, u de mogelijkheid bieden om uw implementatie indien nodig omhoog te schalen (uit te breiden) en om belangrijke services te leveren aan beheerde gebruikers en apparaten.

## <a name="hierarchies-of-sites"></a>Sitehiërarchieën
Wanneer u System Center Configuration Manager voor het eerst installeert, wordt de eerste site van Configuration Manager die u installeert het bereik van uw hiërarchie. De eerste site van Configuration Manager vormt de basis van waaruit u apparaten en gebruikers in uw onderneming beheert. Deze eerste site moet een centrale beheersite of een zelfstandige primaire site.  

 Een *centrale beheersite* is geschikt voor grootschalige implementaties, biedt een centraal punt voor beheer en biedt de flexibiliteit om apparaten die zijn verdeeld over een globale netwerkinfrastructuur te ondersteunen. Nadat u een centrale beheersite installeert, moet u een of meer primaire sites installeren als onderliggende sites. Deze configuratie is nodig omdat een centrale beheersite ondersteunt geen beheer van apparaten, waarop de functie van een primaire site. Een centrale beheersite ondersteunt meerdere onderliggende primaire sites. De onderliggende primaire sites worden gebruikt voor apparaten rechtstreeks beheert, en om netwerkbandbreedte te controleren wanneer de beheerde apparaten zijn in verschillende geografische locaties.  

 Een *zelfstandige primaire site* is geschikt voor kleinere implementaties en kan worden gebruikt voor het beheren van apparaten zonder aanvullende sites installeren. Hoewel een zelfstandige primaire site de grootte van uw implementatie beperkt, biedt ondersteuning voor een scenario waarin u uw hiërarchie op een later tijdstip uitbreiden door het installeren van een nieuwe centrale beheersite. Met dit scenario voor site-uitbreiding, wordt uw zelfstandige primaire site een onderliggende primaire site en kunt u extra onderliggende primaire sites onder de nieuwe centrale beheersite installeren. Vervolgens kunt u uw initiële implementatie voor toekomstige groei van uw bedrijf uitbreiden.  

> [!TIP]  
>  Een zelfstandige primaire site en een onderliggende primaire site zijn in feite hetzelfde type site: een primaire site. Het naamsverschil is gebaseerd op de hiërarchische relatie die wordt gemaakt wanneer u ook een centrale beheersite gebruikt. Deze hiërarchische relatie kan ook de installatie van bepaalde sitesysteemrollen die een uitbreiding van Configuration Manager-functionaliteit beperkt. Deze beperking van rollen treedt op omdat bepaalde sitesysteemrollen kunnen alleen worden geïnstalleerd op de bovenste site van de hiërarchie een centrale beheersite of een zelfstandige primaire site.  

 Nadat u uw eerste site hebt geïnstalleerd, kunt u aanvullende sites installeren. Als uw eerste site een centrale beheersite is, kunt u een of meer onderliggende primaire sites installeren. Nadat u een primaire site (een zelfstandige of onderliggende primaire) hebt geïnstalleerd, kunt u een of meer secundaire sites installeren.  

 Een *secundaire site* kan alleen worden geïnstalleerd als een onderliggende site onder een primaire site. Dit type site kan het bereik van een primaire site uitbreiden voor het beheer van apparaten op locaties die een trage netwerkverbinding hebben met de primaire site. Hoewel een secundaire site een uitbreiding de primaire site vormt, wordt de primaire site beheert alle clients. De secundaire site biedt ondersteuning voor apparaten in de externe locatie. Deze biedt ondersteuning door te comprimeren en vervolgens de overdracht van gegevens te beheren via het netwerk die u verzendt (implementeert) naar clients, en die clients terug naar de site.  

 De volgende diagrammen geven voorbeelden van siteontwerpen weer.  

 ![Voorbeelden van de hiërarchie](media/Hierarchy_examples.png)  

 Zie de volgende onderwerpen voor meer informatie:  

-   [Inleiding op System Center Configuration Manager](../../core/understand/introduction.md)  

-   [Een sitehiërarchie ontwerpen voor System Center Configuration Manager](../../core/plan-design/hierarchy/design-a-hierarchy-of-sites.md)  

-   [System Center Configuration Manager-sites installeren](/sccm/core/servers/deploy/install/installing-sites)  

## <a name="site-system-servers-and-site-system-roles"></a>Sitesysteemservers en sitesysteemrollen  
 Elke Configuration Manager-site installeert *sitesysteemrollen* die beheerbewerkingen ondersteunen. De volgende rollen worden standaard geïnstalleerd wanneer u een site installeert:

-   De siteserverrol is toegewezen aan de computer waarop u de site installeert.

-   De sitedatabaseserverrol is toegewezen aan de SQL Server die als host fungeert voor de sitedatabase.

Andere sitesysteemrollen zijn optioneel en worden alleen gebruikt wanneer u wilt gebruiken van de functionaliteit die actief is in een sitesysteemrol. Elke computer die als host fungeert voor een sitesysteemrol wordt een sitesysteemserver genoemd.  

 Voor een kleinere implementatie van Configuration Manager, kunt u in eerste instantie uitvoeren alle van uw site sitesysteemrollen rechtstreeks op de siteservercomputer. Naarmate uw beheerde omgeving en behoeften groeien, kunt u extra sitesysteemservers installeren met de extra sitesysteemrollen host om de efficiëntie van de site in de levering van services aan meer apparaten te verbeteren.  

 Zie voor meer informatie over de verschillende sitesysteemrollen [sitesysteemrollen](../../core/plan-design/hierarchy/plan-for-site-system-servers-and-site-system-roles.md#bkmk_planroles) in [plan maken voor sitesysteemservers en sitesysteemrollen voor System Center Configuration Manager](../../core/plan-design/hierarchy/plan-for-site-system-servers-and-site-system-roles.md).

## <a name="publishing-site-information-to-active-directory-domain-services"></a>Sitegegevens publiceren naar Active Directory Domain Services  
 Om beheer te vereenvoudigen van Configuration Manager, kunt u het Active Directory-schema voor ondersteuning van gegevens die worden gebruikt door Configuration Manager uitbreiden en vervolgens sites de belangrijkste informatie publiceren naar Active Directory Domain Services (AD DS). De computers die u wilt beheren kunnen vervolgens veilig site-gerelateerde informatie ophalen van de vertrouwde bron van AD DS. De informatie die clients kunnen ophalen identificeert de beschikbare sites, sitesysteemservers en services die deze sitesysteemservers bieden.  

 *Het Active Directory-schema uitbreiden* wordt slechts één keer voor elke forest uitgevoerd en kan plaatsvinden vóór of na het installeren van Configuration Manager.   Wanneer u het schema uitbreidt, moet u een nieuwe Active Directory-container Systeembeheer in elk domein met de naam maken. De container bevat een Configuration Manager-site die gegevens publiceert voor clients om te zoeken. Zie voor meer informatie [Active Directory voorbereiden voor het publiceren van site](../../core/plan-design/network/extend-the-active-directory-schema.md).  

 *Sitegegevens publiceren* verbetert de beveiliging van uw Configuration Manager-hiërarchie en vermindert de administratieve overhead, maar is niet vereist voor de basisfunctionaliteit van Configuration Manager.  
