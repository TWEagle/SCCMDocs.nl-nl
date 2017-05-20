---
title: Firewalls en domeinen | Microsoft-documenten
description: Instellen van firewalls, poorten en domeinen voorbereiden voor System Center Configuration Manager-communicatie.
ms.custom: na
ms.date: 2/6/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: get-started-article
ms.assetid: d6993bba-f6bd-4639-adbf-efc1c638b2f3
caps.latest.revision: 15
caps.handback.revision: 0
author: Brenduns
ms.author: brenduns
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: bd20983eeca47bdd63e0385440e6c8d64901b902
ms.openlocfilehash: 4a2a8f96a900a2c4959ae3ff59232771ece95991
ms.contentlocale: nl-nl
ms.lasthandoff: 05/17/2017


---
# <a name="set-up-firewalls-ports-and-domains-for-system-center-configuration-manager"></a>Instellen van firewalls, poorten en domeinen voor System Center Configuration Manager

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*

Voorbereiden van uw netwerk te ondersteunen van System Center Configuration Manager plannen voor het instellen van infrastructuur zoals firewalls uitwisselt gebruikt door Configuration Manager.  

|Overweging|Details|  
|-------------------|-------------|  
|**Poorten en protocollen** gebruik van andere Configuration Manager-mogelijkheden. Sommige poorten die vereist zijn en u kunt andere **domeinen en services**.|De meeste Configuration Manager-communicatie gebruiken algemene poorten zoals poort 80 voor HTTP- of 443 voor HTTPS-communicatie. Echter, [sommige sitesysteemrollen ondersteuning voor het gebruik van aangepaste websites](/sccm/core/plan-design/network/websites-for-site-system-servers) en aangepaste poorten.<br /><br /> **Voordat u Configuration Manager implementeert**, identificeren van de poorten die u wilt gebruiken en firewalls dienovereenkomstig instellen.<br /><br /> **Als u wilt wijzigen van een poort** na installatie van Configuration Manager Vergeet niet om te werken van firewalls op apparaten en het netwerk en de configuratie van de poort van in Configuration Manager ook wijzigen.<br /><br /> Zie voor meer informatie: </br>- [Het configureren van client-communicatiepoorten](../../../core/clients/deploy/configure-client-communication-ports.md) </br>- [Gebruikte poorten in Configuration Manager](../../../core/plan-design/hierarchy/ports.md) </br>- [Vereisten voor internettoegang voor de service connection point](/sccm/core/servers/deploy/configure/about-the-service-connection-point#bkmk_urls)|  
|**Domeinen en services** dat siteservers en clients mogelijk te gebruiken.|Configuration Manager-mogelijkheden kunnen vereisen siteservers en clients toegang hebben tot specifieke services en domeinen op het Internet, zoals Windowsudpate.microsoft.com of de Microsoft Intune-service.<br /><br /> Als u Microsoft Intune gebruiken wilt voor het beheren van mobiele apparaten, moet u ook instellen toegang tot [poorten en domeinen die Intune is vereist.](https://docs.microsoft.com/en-us/intune/get-started/network-infrastructure-requirements-for-microsoft-intune)|  
|**Proxy-servers** voor systeemservers van sites en voor clientcommunicatie. U kunt afzonderlijke proxyservers voor verschillende sitesysteemservers en clients opgeven.|Omdat deze configuraties worden gemaakt op het moment dat u een sitesysteemrol of de client installeert, hoeft u alleen zich ervan bewust zijn van de proxy-serverconfiguraties voor later gebruik wanneer u sitesysteemrollen en clients configureren.<br /><br /> Als u niet zeker uw implementatie wilt proxyservers gebruiken, controleert u [ondersteuning voor Proxy-server in System Center Configuration Manager](../../../core/plan-design/network/proxy-server-support.md) voor meer informatie over sitesysteemrollen en Clientacties die een proxyserver kunnen gebruiken.|   
|  

