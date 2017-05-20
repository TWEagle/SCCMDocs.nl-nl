---
title: "De grondbeginselen van sites en hiërarchieën | Microsoft-documenten"
description: "Algemene informatie over System Center Configuration Manager-sites en hiërarchieën ophalen."
ms.custom: na
ms.date: 12/30/2016
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 4db1e15f-e832-4cf9-be33-d3971e635a55
caps.latest.revision: 6
author: Brenduns
ms.author: brenduns
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 68527c0e82861106b7ec28b34bffa8fd74b2dd4a
ms.openlocfilehash: f13f38be2a19ab8a1ead246e5272515dd0570984
ms.contentlocale: nl-nl
ms.lasthandoff: 05/17/2017


---
# <a name="fundamentals-of-sites-and-hierarchies-for-system-center-configuration-manager"></a>De grondbeginselen van sites en hiërarchieën voor System Center Configuration Manager

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*

Een System Center Configuration Manager-implementatie moet worden geïnstalleerd in een Active Directory-domein. De basis voor deze implementatie bestaat uit een of meer Configuration Manager-sites die een hiërarchie van sites vormen. Voor een hiërarchie die uit een enkele site bestaat en voor een hiërarchie die uit meerdere sites bestaat, geldt dat het type en de locatie van sites die u installeert, u de mogelijkheid bieden om uw implementatie indien nodig omhoog te schalen (uit te breiden) en om belangrijke services te leveren aan beheerde gebruikers en apparaten.

## <a name="hierarchies-of-sites"></a>Sitehiërarchieën
Wanneer u System Center Configuration Manager voor het eerst installeert, bepaalt de eerste Configuration Manager-site die u installeert het bereik van uw hiërarchie. De eerste site van Configuration Manager is de basis van waaruit u apparaten en gebruikers in uw onderneming beheert wordt. Deze eerste site moet een centrale beheersite of een zelfstandige primaire site.  

 Een *centrale beheersite* is geschikt voor grootschalige implementaties, biedt een centraal punt voor beheer en biedt de flexibiliteit om apparaten die zijn verdeeld over meerdere algemene netwerkinfrastructuur te ondersteunen. Nadat u een centrale beheersite installeert, moet u een of meer primaire sites installeren als onderliggende sites. Deze configuratie is nodig omdat een centrale beheersite ondersteunt niet beheer van apparaten, dit de functie van een primaire site is. Een centrale beheersite ondersteunt meerdere onderliggende primaire sites. De onderliggende primaire sites worden gebruikt voor het rechtstreeks beheren van apparaten en om netwerkbandbreedte te controleren wanneer uw beheerde apparaten zich op verschillende geografische locaties.  

 Een *zelfstandige primaire site* is geschikt voor kleinere implementaties en kan worden gebruikt voor het beheren van apparaten zonder bijkomende sites installeren. Hoewel een zelfstandige primaire site de grootte van uw implementatie beperken kunt, ondersteunt een scenario om uit te breiden van uw hiërarchie op een later tijdstip door een nieuwe centrale beheersite installeert. Met dit scenario voor site-uitbreiding, wordt uw zelfstandige primaire site een onderliggende primaire site en kunt u bijkomende onderliggende primaire sites onder de nieuwe centrale beheersite installeren. Vervolgens kunt u uw initiële implementatie voor toekomstige groei van uw bedrijf uitbreiden.  

> [!TIP]  
>  Een zelfstandige primaire site en een onderliggende primaire site zijn eigenlijk niet hetzelfde type site: een primaire site. Het naamsverschil is gebaseerd op de hiërarchische relatie die wordt gemaakt wanneer u ook een centrale beheersite gebruikt. Deze Hiërarchierelatie kunt beperken de installatie van bepaalde sitesysteemrollen waarmee Configuration Manager-functionaliteit worden uitgebreid. Deze beperking van de rollen treedt op omdat bepaalde sitesysteemrollen kunnen alleen worden geïnstalleerd op de site op hoogste niveau van de hiërarchie een centrale beheersite of een zelfstandige primaire site.  

 Nadat u uw eerste site hebt geïnstalleerd, kunt u aanvullende sites installeren. Als uw eerste site een centrale beheersite is, kunt u een of meer onderliggende primaire sites installeren. Nadat u een primaire site (zelfstandig of onderliggende primaire) hebt geïnstalleerd, kunt u vervolgens een of meer secundaire sites installeren.  

 Een *secundaire site* kan alleen worden geïnstalleerd als een onderliggende site onder een primaire site. Dit type site kan het bereik van een primaire site uitbreiden voor het beheer van apparaten op locaties die een trage netwerkverbinding hebben met de primaire site. Hoewel een secundaire site de primaire site uitbreidt, wordt de primaire site beheert alle clients. De secundaire site biedt ondersteuning voor apparaten in de externe locatie. Deze biedt ondersteuning door het comprimeren en vervolgens de overdracht van gegevens over uw netwerk die u verzendt te beheren () op clients te implementeren, en dat clients naar de site verzenden.  

 De volgende diagrammen geven voorbeelden van siteontwerpen weer.  

 ![Hiërarchie-voorbeelden](media/Hierarchy_examples.png)  

 Zie de volgende onderwerpen voor meer informatie:  

-   [Inleiding tot System Center Configuration Manager](../../core/understand/introduction.md)  

-   [Een hiërarchie van sites ontwerpen voor System Center Configuration Manager](../../core/plan-design/hierarchy/design-a-hierarchy-of-sites.md)  

-   [Installatie van System Center Configuration Manager-sites](/sccm/core/servers/deploy/install/installing-sites)  

## <a name="site-system-servers-and-site-system-roles"></a>Sitesysteemservers en sitesysteemrollen  
 Elke Configuration Manager-site installeert *sitesysteemrollen* ondersteuning van beheerbewerkingen. De volgende rollen worden standaard geïnstalleerd wanneer u een site installeert:

-   De siteserverrol wordt toegewezen aan de computer waarop u de site installeert.

-   De sitedatabaseserverrol is toegewezen aan de SQL Server die als host fungeert voor de sitedatabase.

Andere sitesysteemrollen zijn optioneel en worden alleen gebruikt wanneer u de functionaliteit gebruiken die actief zijn in een sitesysteemrol wordt gehost. Elke computer die als host fungeert voor een sitesysteemrol wordt een sitesysteemserver genoemd.  

 Voor een kleinere implementatie van Configuration Manager voert u misschien in eerste instantie alle van uw site systeemrollen rechtstreeks op de siteservercomputer. Klik, als uw beheerde omgeving en vereisten vergroten, kunt u extra sitesysteemservers installeren met de extra sitesysteemrollen host om de efficiëntie van de site voor meer apparaten te verbeteren.  

 Zie voor meer informatie over de verschillende sitesysteemrollen [sitesysteemrollen](../../core/plan-design/hierarchy/plan-for-site-system-servers-and-site-system-roles.md#bkmk_planroles) in [plannen voor de sitesysteemservers en sitesysteemrollen voor System Center Configuration Manager](../../core/plan-design/hierarchy/plan-for-site-system-servers-and-site-system-roles.md).

## <a name="publishing-site-information-to-active-directory-domain-services"></a>Sitegegevens publiceren naar Active Directory Domain Services  
 Om beheer te vereenvoudigen van Configuration Manager, kunt u het Active Directory-schema voor ondersteuning van de details die worden gebruikt door Configuration Manager uitbreiden en vervolgens sites hun belangrijke informatie publiceren naar Active Directory Domain Services (AD DS). De computers die u wilt beheren kunnen vervolgens veilig site-gerelateerde informatie ophalen van de vertrouwde bron van AD DS. De informatie die clients kunnen ophalen identificeert de beschikbare sites, sitesysteemservers en services die deze sitesysteemservers bieden.  

 *Het Active Directory-schema uitbreiden* slechts één keer voor elke forest is uitgevoerd en kan worden uitgevoerd vóór of na het installeren van Configuration Manager.   Wanneer u het schema uitbreidt, moet u een nieuwe Active Directory-container Systeembeheer in elk domein met de naam maken. De container bevat een Configuration Manager-site die clients kunnen zoeken naar gegevens zal publiceren. Zie voor meer informatie [Active Directory voorbereiden voor sitepublicatie](../../core/plan-design/network/extend-the-active-directory-schema.md).  

 *Sitegegevens publiceren* verbetert de beveiliging van uw Configuration Manager-hiërarchie en de administratieve overhead verminderd, maar is niet vereist voor de basisfunctionaliteit van Configuration Manager.  

