---
title: Evalueren van Configuration Manager | Microsoft-documenten
description: Maak een testomgeving om te evalueren van System Center Configuration Manager voor gebruik in uw organisatie.
ms.custom: na
ms.date: 2/28/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 01b30260-f03a-4851-a549-d1b76e8cfc69
caps.latest.revision: 25
caps.handback.revision: 0
author: brenduns
ms.author: brenduns
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 0ea90d3f3bef80b8acf9018a1338ae05fc948af4
ms.openlocfilehash: d7ea785ab1beee09b9adda735a87f89bc9481620
ms.contentlocale: nl-nl
ms.lasthandoff: 05/17/2017


---
# <a name="evaluate-system-center-configuration-manager-by-building-your-own-lab-environment"></a>System Center Configuration Manager evalueren door uw eigen testomgeving op te zetten

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*

 Ontdek hoe u een testomgeving kunt maken om te evalueren hoe System Center Configuration Manager in uw organisatie kan worden gebruikt.  

 System Center Configuration Manager is een complex en krachtige hulpprogramma voor het beheren van uw gebruikers, apparaten en software. Dit is een goed idee om te evalueren zorgvuldig door System Center Configuration Manager voor de volledige implementatie zodat u kunt trouw met conceptuele understanding met praktische oefeningen.  

 Deze handleiding is hoofdzakelijk bedoeld voor beheerders die het gebruik van Configuration Manager in bedrijfsomgevingen evalueert:  

-   Beheerders die een oplossing moet volledig beheer van pc's, servers en mobiele apparaten  

-   Beheerders in sterk beveiligde sectoren waarvoor de beveiliging van lokale apparaten beheren met de flexibiliteit van cloud-gebaseerde Apparaatbeheer  

-   Beheerders die u wilt de schaal-up van de architectuur van de lokale server beheren  

## <a name="what-this-lab-does"></a>Wat deze testomgeving biedt  
 Het belangrijkste doel van deze testomgeving maken is dat u de algemene kennis aan de slag met Configuration Manager en voor het verbeteren van uw kennis van Configuration Manager. U doorloopt een versnelde assembly van de huidige versie van Configuration Manager met behulp van de twee servers:  

-   Een die als host fungeert voor Active Directory, de domeincontroller en de DNS-server  

-   Een die als host fungeert voor Configuration Manager en alle onderdelen zijn gekoppeld aan SQL Server  

De clientcomputers zijn geïnstalleerd in Hyper-V. De testomgeving zelf kan ook worden uitgevoerd als een volledig gevirtualiseerd systeem op één server.  

## <a name="what-this-lab-does-not-do"></a>Wat deze testomgeving niet biedt  
 Deze cursus gaat u niet alle Configuration Manager-scenario's. Het is niet ontworpen om onmiddellijk worden gemigreerd naar een actieve omgeving.  

 Wanneer u deze testomgeving opzet, beschikt u over een functionele omgeving waarin u kunt werken. Maar deze omgeving niet geoptimaliseerd voor factoren zoals systeemprestaties, harde schijfruimte management en SQL Server-opslag.  

##  <a name="BKMK_EvalRec"></a>Aanbevolen lezen voordat u de testomgeving samenstellen  
 Er is een schat aan inhoud beschikbaar is in [documentatie voor System Center Configuration Manager](http://docs.microsoft.com/sccm/). Wij raden u aan de volgende onderwerpen van deze bibliotheek te lezen voordat u begint met het maken van het lab:  

-   Informatie over de belangrijkste concepten over de Configuration Manager-console door eindgebruikers portals en voorbeeldscenario's in [Inleiding voor System Center Configuration Manager](../../core/understand/introduction.md).  

-   Meer informatie over de primaire beheerfuncties van Configuration Manager in [functies en mogelijkheden van System Center Configuration Manager](../../core/plan-design/changes/features-and-capabilities.md).  

-   Oefen uw kennis met uw [grondbeginselen van System Center Configuration Manager](../../core/understand/fundamentals.md).  

-   Informatie over het belang van beveiligingsrollen in [grondbeginselen van op rollen gebaseerd beheer voor System Center Configuration Manager](../../core/understand/fundamentals-of-role-based-administration.md).  

-   Meer informatie over inhoudsbeheer in [concepten voor inhoudsbeheer](../../core/plan-design/hierarchy/fundamental-concepts-for-content-management.md).  

-   Meer informatie over het met succes ondersteuning voor dagelijkse taken in uw implementatie in de gehele [begrijpen hoe clients vinden sitebronnen en services voor System Center Configuration Manager](../../core/plan-design/hierarchy/understand-how-clients-find-site-resources-and-services.md).  

