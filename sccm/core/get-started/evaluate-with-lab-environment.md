---
title: Evalueren in een testomgeving
titleSuffix: Configuration Manager
description: Maak een testomgeving om te evalueren van System Center Configuration Manager voor gebruik in uw organisatie.
ms.custom: na
ms.date: 2/28/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 01b30260-f03a-4851-a549-d1b76e8cfc69
caps.latest.revision: "25"
caps.handback.revision: "0"
author: brenduns
ms.author: brenduns
manager: angrobe
ms.openlocfilehash: 8649f6686adad908b7806d22983aaf20171609ba
ms.sourcegitcommit: c236214b2fcc13dae7bad96d7fb33f692868191d
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/12/2017
---
# <a name="evaluate-system-center-configuration-manager-by-building-your-own-lab-environment"></a>System Center Configuration Manager evalueren door uw eigen testomgeving op te zetten

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*

 Ontdek hoe u een testomgeving kunt maken om te evalueren hoe System Center Configuration Manager in uw organisatie kan worden gebruikt.  

 System Center Configuration Manager is een complex en krachtig hulpprogramma voor het beheren van uw gebruikers, apparaten en software. Is een goed idee om grondig System Center Configuration Manager evalueren voordat u volledige implementatie, zodat u kunt trouw met conceptuele informatie over aan praktijkoefeningen.  

 Deze handleiding is hoofdzakelijk bedoeld voor beheerders die het gebruik van Configuration Manager in bedrijfsomgevingen evalueert:  

-   Beheerders die een oplossing moet volledig beheer van pc's, servers en mobiele apparaten  

-   Beheerders in hoge beveiligingseisen waarvoor de beveiliging van on-premises Apparaatbeheer met de flexibiliteit van cloud-gebaseerd Apparaatbeheer  

-   Beheerders die u wilt het schalen van van de architectuur van de lokale server beheren  

## <a name="what-this-lab-does"></a>Wat deze testomgeving biedt  
 Het belangrijkste doel van het maken van deze testomgeving is zodat u de algemene kennis aan de slag met Configuration Manager en voor het verbeteren van uw kennis van Configuration Manager. U hebt een versnelde assembly van de huidige versie van Configuration Manager met behulp van twee servers doorlopen:  

-   Een die als host fungeert voor Active Directory, de domeincontroller en de DNS-server  

-   Een die als host fungeert voor Configuration Manager en alle bijbehorende SQL Server-onderdelen  

De clientcomputers zijn geïnstalleerd in Hyper-V. De testomgeving zelf kan ook worden uitgevoerd als een volledig gevirtualiseerd systeem op één server.  

## <a name="what-this-lab-does-not-do"></a>Wat deze testomgeving niet biedt  
 In dit testlab gaat u niet alle Configuration Manager-scenario's. Het is niet ontworpen onmiddellijk worden gemigreerd naar een actieve omgeving.  

 Wanneer u deze testomgeving opzet, beschikt u over een functionele omgeving waarin u kunt werken. Maar deze omgeving is niet geoptimaliseerd voor factoren zoals de systeemprestaties, het beheer van vasteschijfruimte en SQL Server-opslag.  

##  <a name="BKMK_EvalRec"></a>Aanbevolen documentatie voordat u het lab maken  
 Er is een schat aan materiaal beschikbaar in [documentatie voor System Center Configuration Manager](http://docs.microsoft.com/sccm/). U wordt aangeraden de volgende onderwerpen uit deze bibliotheek te lezen voordat u begint met het bouwen van de testomgeving:  

-   Meer informatie over de belangrijkste concepten over de Configuration Manager-console, eindgebruikers-portals en voorbeeldscenario's in [inleiding op System Center Configuration Manager](../../core/understand/introduction.md).  

-   Meer informatie over de primaire beheerfuncties van Configuration Manager in [functies en mogelijkheden van System Center Configuration Manager](../../core/plan-design/changes/features-and-capabilities.md).  

-   Vergroot uw kennis met [basisprincipes van System Center Configuration Manager](../../core/understand/fundamentals.md).  

-   Ontdek het belang van beveiligingsrollen in [basisprincipes van beheer op basis van rollen voor System Center Configuration Manager](../../core/understand/fundamentals-of-role-based-administration.md).  

-   Meer informatie over inhoudsbeheer in [concepten voor inhoudsbeheer](../../core/plan-design/hierarchy/fundamental-concepts-for-content-management.md).  

-   Meer informatie over het dagelijkse taken in uw implementatie in goed kunt ondersteunen [begrijpen hoe clients siteresources en -services voor System Center Configuration Manager vinden](../../core/plan-design/hierarchy/understand-how-clients-find-site-resources-and-services.md).  
