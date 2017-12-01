---
title: Gebruik van grenzen en grensgroepen
titleSuffix: Configuration Manager
description: "Gebruik grenzen en grensgroepen definiëren netwerklocaties en toegankelijk sitesystemen voor apparaten die u beheert."
ms.custom: na
ms.date: 3/27/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: configmgr-other
ms.tgt_pltfrm: na
ms.topic: get-started-article
ms.assetid: 54aa20d5-791e-4416-9db4-5aaea472c0b7
caps.latest.revision: "10"
author: mstewart
ms.author: mstewart
manager: angrobe
ms.openlocfilehash: b6a8deb30f73e74701e07e0796047ed03102cabf
ms.sourcegitcommit: 7fe45ff75f05f7cc03ad021db8119791abe18049
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/01/2017
---
# <a name="define-site-boundaries-and-boundary-groups-for-system-center-configuration-manager"></a>Sitegrenzen en grensgroepen definiëren voor System Center Configuration Manager

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*

Grenzen voor System Center Configuration Manager definiëren netwerklocaties op uw intranet die apparaten kan bevatten die u wilt beheren. Grensgroepen zijn logische groepen grenzen die u configureert.

 Een hiërarchie kan een onbeperkt aantal grensgroepen bevatten en elke grensgroep kan een combinatie van de volgende grenstypen bevatten:  

-   IP-subnet,  
-   Active Directory-sitenaam  
-   IPv6-voorvoegsel  
-   IP-adresbereik  

Clients op het intranet evalueren hun huidige netwerklocatie en gebruiken deze informatie vervolgens om vast te stellen tot welke grensgroepen ze behoren.  

 Clients gebruiken grensgroepen voor de volgende doeleinden:  
-   **Een toegewezen site vinden:** Grensgroepen kunnen clients een primaire site vinden voor clienttoewijzing (automatische sitetoewijzing).  
-   **Zoeken naar bepaalde sitesysteemrollen die kan worden gebruikt:** Als u een grensgroep aan bepaalde sitesysteemrollen koppelt, biedt de grensgroep clients die lijst met sitesystemen voor gebruik tijdens de Inhoudslocatie en als voorkeursbeheerpunten.  

Clients die verbinding hebben met internet of zijn geconfigureerd als internetclients, gebruiken geen grensgegevens. Deze clients kunnen geen gebruik maken van automatische sitetoewijzing en kunnen inhoud altijd downloaden van een distributiepunt van hun toegewezen site wanneer het distributiepunt is geconfigureerd om clientverbindingen vanaf internet toe te staan.  

**Aan de slag:**
- Eerst [netwerklocaties als grenzen definiëren](/sccm/core/servers/deploy/configure/boundaries).
- Vervolgens gaat u door [grensgroepen configureren](/sccm/core/servers/deploy/configure/boundary-groups) om te koppelen van clients in deze grenzen voor de sitesysteemservers die kan worden gebruikt.



##  <a name="BKMK_BoundaryBestPractices"></a>Aanbevolen procedures voor grenzen en grensgroepen  

-   **Gebruik een combinatie van het minste aantal grenzen die aan uw behoeften voldoet:**  
   In het verleden raden we het gebruik van bepaalde grenstypen boven andere. Met wijzigingen in de prestaties verbeteren, nu we aanbevelen u welke grenstype of typen die u kiest die voor uw omgeving en waarmee u werken het minste aantal grenzen gebruiken kunt u uw beheertaken vereenvoudigen.      

-   **Voorkom overlappende grenzen voor automatische sitetoewijzing:**  
     Hoewel zowel configuraties voor sitetoewijzing als inhoudslocaties door elke grensgroep worden ondersteund, wordt het aanbevolen een afzonderlijke reeks grensgroepen te maken die alleen worden gebruikt voor sitetoewijzing. Controleer daarom of de grenzen in een grensgroep geen lid zijn van een andere grensgroep met een andere sitetoewijzing. Dit is van belang omdat:  

    -   Eén grens kan worden opgenomen in meerdere grensgroepen  

    -   Elke grensgroep kan worden gekoppeld aan een andere primaire site voor sitetoewijzing  

    -   Een client op een grens die lid is van twee verschillende grensgroepen met verschillende sitetoewijzingen selecteert willekeurig een site om zich daarbij te voegen. Dit kan een andere site zijn dan waaraan u de client wilt toevoegen.  Deze configuratie wordt overlappende grenzen genoemd.  

     Overlappende grenzen zijn geen probleem voor inhoudslocatie, maar vormen vaak een gewenste configuratie waarmee clients toegang hebben tot aanvullende resources of de inhoudslocaties die ze kunnen gebruiken.  
