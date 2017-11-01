---
title: Firewalls en domeinen
titleSuffix: Configuration Manager
description: Instellen van firewalls, poorten en domeinen voorbereiden voor System Center Configuration Manager-communicatie.
ms.custom: na
ms.date: 2/6/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: configmgr-other
ms.tgt_pltfrm: na
ms.topic: get-started-article
ms.assetid: d6993bba-f6bd-4639-adbf-efc1c638b2f3
caps.latest.revision: "15"
caps.handback.revision: "0"
author: Brenduns
ms.author: brenduns
manager: angrobe
ms.openlocfilehash: 3bcfeb4517797b5c04615f36a166e55a3f2e4058
ms.sourcegitcommit: c236214b2fcc13dae7bad96d7fb33f692868191d
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/12/2017
---
# <a name="set-up-firewalls-ports-and-domains-for-system-center-configuration-manager"></a>Instellen van firewalls, poorten en domeinen voor System Center Configuration Manager

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*

Bereid uw netwerk te ondersteunen van System Center Configuration Manager plannen voor het instellen van de infrastructuur, zoals firewalls de communicatie gebruikt door Configuration Manager uit te wisselen.  

|Overweging|Details|  
|-------------------|-------------|  
|**Poorten en protocollen** dat andere Configuration Manager-functies gebruiken. Sommige poorten zijn vereist en u kunt andere **domeinen en services**.|De meeste Configuration Manager-communicatie gebruiken algemene poorten zoals poort 80 voor HTTP en 443 voor HTTPS-communicatie. Echter, [sommige sitesysteemrollen bieden ondersteuning voor het gebruik van aangepaste websites](/sccm/core/plan-design/network/websites-for-site-system-servers) en aangepaste poorten.<br /><br /> **Voordat u Configuration Manager implementeert**, identificeren van de poorten die u wilt gebruiken en firewalls dienovereenkomstig instellen.<br /><br /> **Als u wilt wijzigen van een poort** nadat u de Configuration Manager hebt geïnstalleerd, vergeet niet om te werken van firewalls op apparaten en het netwerk en de configuratie van de poort van in Configuration Manager ook wijzigen.<br /><br /> Zie voor meer informatie: </br>- [Clientcommunicatiepoorten configureren](../../../core/clients/deploy/configure-client-communication-ports.md) </br>- [Gebruikte poorten in Configuration Manager](../../../core/plan-design/hierarchy/ports.md) </br>- [Vereisten voor internettoegang voor het serviceverbindingspunt](/sccm/core/servers/deploy/configure/about-the-service-connection-point#bkmk_urls)|  
|**Domeinen en services** dat siteservers en clients mogelijk moet gebruiken.|Configuration Manager-functies kunnen vereisen siteservers en clients toegang hebben tot specifieke services en domeinen op het Internet, zoals windowsupdate.Microsoft.com of de Microsoft Intune-service.<br /><br /> Als u Microsoft Intune gebruiken wilt voor het beheren van mobiele apparaten, moet u ook instellen om toegang tot [poorten en domeinen die Intune vereist.](https://docs.microsoft.com/en-us/intune/get-started/network-infrastructure-requirements-for-microsoft-intune)|  
|**Proxyservers** voor sitesysteemservers en voor clientcommunicatie. U kunt afzonderlijke proxyservers voor verschillende sitesysteemservers en clients opgeven.|Omdat deze configuraties worden gemaakt op het moment dat u een sitesysteemrol of de client installeert, hoeft u alleen te worden op de hoogte van de proxy-serverconfiguraties voor later gebruik wanneer u sitesysteemrollen en clients configureert.<br /><br /> Als u niet zeker van te zijn dat uw implementatie wilt gebruiken, proxy-servers, Bekijk [ondersteuning voor proxyserver in System Center Configuration Manager](../../../core/plan-design/network/proxy-server-support.md) voor meer informatie over sitesysteemrollen en Clientacties die een proxyserver kunnen gebruiken.|   
|  
