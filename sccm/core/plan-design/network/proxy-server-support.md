---
title: Ondersteuning voor proxy server | Microsoft-documenten
description: Meer informatie over System Center Configuration Manager ondersteuning voor proxyservers die gebruikmaken van sitesysteemservers en clients.
ms.custom: na
ms.date: 2/7/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 9123a87a-0b6f-43c7-b5c2-fac5d09686b1
caps.latest.revision: 6
caps.handback.revision: 0
author: Brenduns
ms.author: brenduns
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: c4f30e4839709722b216262b21d7b51c07d24d1e
ms.openlocfilehash: dc36be47310d2c2178c974a2b503d0b5f9f6e2ec
ms.contentlocale: nl-nl
ms.lasthandoff: 05/17/2017


---
# <a name="proxy-server-support-in-system-center-configuration-manager"></a>Ondersteuning voor proxyserver in System Center Configuration Manager

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*

System Center Configuration Manager-sitesysteemservers en clients kunnen een proxyserver gebruiken.  

## <a name="site-system-servers"></a>Sitesysteemservers  
Wanneer sitesysteemrollen verbonden zijn met het Internet moeten, kunt u ze voor het gebruik van een proxyserver configureren.  

-   Een computer die als host fungeert voor een sitesysteemserver ondersteunt een enkele proxyserverconfiguratie wordt gedeeld door alle sitesysteemrollen op dezelfde computer weer. Als u moet afzonderlijke proxyservers voor verschillende rollen of exemplaren van een rol, schakelt u deze functies op afzonderlijke sitesysteemservers.  

-   Wanneer u nieuwe instellingen van proxyserver voor een sitesysteemserver waarop al een proxy-serverconfiguratie configureert, wordt de oorspronkelijke configuratie overschreven.  

-   Verbindingen met de proxy maken gebruik van het account **Systeem** van de computer die als host fungeert voor de sitesysteemrol.  

De volgende sitesysteemrollen verbinding met Internet en kunnen een proxyserver nodig hebben.  Met één uitzondering, sitesysteemrollen die u een proxy kunnen gebruiken, doen dit zonder aanvullende configuratie. De uitzondering hierop is het software-updatepunt. De volgende lijst bevat informatie over de aanvullende configuraties die vereist dat een software-updatepunt:  

**Asset Intelligence-synchronisatiepunt** -deze sitesysteemrol maakt een verbinding naar Microsoft en gebruikt een proxyserverconfiguratie op de computer die als host fungeert voor de Asset Intelligence-synchronisatiepunt.  

**Cloud-gebaseerde distributiepunt** - voor het instellen van een proxyserver voor een cloud-gebaseerd distributiepunt, het instellen van de proxyserver op de primaire site die het cloud-gebaseerde distributiepunt beheert.  

Voor deze configuratie moet de primaire siteserver:  

-   Moet verbinding maken met Microsoft Azure instellen, bewaken en distribueren van inhoud naar het distributiepunt.  

-   Maakt gebruik van het systeemaccount van de computer de verbinding te maken.  

-   Maakt gebruik van de standaardwebbrowser die computer.  

U kunt een proxyserver op de cloud-gebaseerd distributiepunt in Microsoft Azure niet instellen.  

**Verbindingspunt cloud** -deze sitesysteemrol maakt een verbinding met de Configuration Manager-cloudservice versie om updates te downloaden voor Configuration Manager en maakt gebruik van een proxyserver die geconfigureerd op de computer die als host fungeert voor de service connection point.  

**Exchange Server-connector** -deze sitesysteemrol maakt een verbinding met een Exchange Server en gebruikt een proxyserverconfiguratie op de computer die als host fungeert voor Exchange Server-connector.  

**Serviceverbindingspunt** -deze sitesysteemrol maakt een verbinding met Microsoft Intune en gebruikt een proxyserverconfiguratie op de computer die als host fungeert voor de service connection point.  

**Software-updatepunt** - deze sitesysteemrol kan de proxy gebruiken bij het verbinden met Microsoft Update om patches te downloaden en informatie over updates te synchroniseren. Wanneer u deze optie inschakelt, bij het instellen van de software-updatepunt, software-updatepunten een proxyserver gebruiken voor de volgende opties:  

-   **Gebruik een proxyserver bij het synchroniseren van software-updates**  

-   **Een proxyserver gebruiken wanneer inhoud wordt gedownload via automatische implementatieregels** (terwijl beschikbaar voor gebruik, deze instelling wordt niet gebruikt door software-updatepunten op secundaire sites.)  

Configureer de proxyserverinstellingen op de pagina actieve Software-updatepunt van de wizard sitesysteemrollen toevoegen of op de **algemeen** tabblad **eigenschappen van Software-Update**.  

-   De proxyserverinstellingen zijn alleen gekoppeld met het software-updatepunt op de site.  

-   Proxyserveropties zijn alleen beschikbaar als een proxyserver is al ingesteld voor de sitesysteemserver die als host fungeert voor de software-updatepunt.  

> [!NOTE]  
>  Standaard wordt het account **Systeem** voor de server waarop een automatische implementatieregel is gemaakt, gebruikt om verbinding te maken met internet en software-updates te downloaden wanneer de automatische implementatieregels worden uitgevoerd.  
>   
>  Als dit account geen toegang het Internet tot, software-updates niet worden gedownload en de volgende vermelding is geregistreerd in het logboekbestand ruleengine.log opgeslagen: **De update downloaden van internet is mislukt. Fout = 12007.**  

#### <a name="to-set-up-the-proxy-server-for-a-site-system-server"></a>Voor het instellen van de proxyserver voor een sitesysteemserver  

1.  Kies in de Configuration Manager-console **beheer**, vouw **siteconfiguratie**, en kies vervolgens **Servers en sitesysteemrollen**.  

2.  Kies de sitesysteemserver die u bewerken wilt, in de details van het deelvenster met de rechtermuisknop op **sitesysteem**, en kies vervolgens **eigenschappen**.  

3.  Selecteer in de sitesysteemeigenschappen, de **Proxy** tabblad, en vervolgens de proxy-instellingen voor deze primaire siteserver.  

4.  Kies **OK** om op te slaan de nieuwe proxy-serverconfiguratie.  

