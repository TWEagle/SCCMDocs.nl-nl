---
title: Proxyserverondersteuning
titleSuffix: Configuration Manager
description: Meer informatie over System Center Configuration Manager-ondersteuning voor proxyservers die gebruikmaken van sitesysteemservers en clients.
ms.custom: na
ms.date: 2/7/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 9123a87a-0b6f-43c7-b5c2-fac5d09686b1
caps.latest.revision: "6"
caps.handback.revision: "0"
author: mstewart
ms.author: mstewart
manager: angrobe
ms.openlocfilehash: 5c60af99af03a20e6ee25908a1bc230c6a50e343
ms.sourcegitcommit: 7fe45ff75f05f7cc03ad021db8119791abe18049
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/01/2017
---
# <a name="proxy-server-support-in-system-center-configuration-manager"></a>Ondersteuning voor proxyserver in System Center Configuration Manager

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*

Zowel System Center Configuration Manager-sitesysteemservers en clients kunnen een proxyserver gebruiken.  

## <a name="site-system-servers"></a>Sitesysteemservers  
Wanneer sitesysteemrollen verbinding moeten maken met Internet, kunt u ze voor het gebruik van een proxyserver configureren.  

-   Een computer die als host fungeert voor een sitesysteemserver ondersteunt een enkele proxyserverconfiguratie die wordt gedeeld door alle sitesysteemrollen op dezelfde computer weer. Als u verschillende proxyservers voor verschillende rollen of verschillende exemplaren van een rol nodig, moet u deze rollen op afzonderlijke sitesysteemservers plaatsen.  

-   Wanneer u nieuwe proxyserverinstellingen voor een sitesysteemserver waarop al een proxyserverconfiguratie configureert, wordt de oorspronkelijke configuratie overschreven.  

-   Verbindingen met de proxy maken gebruik van het account **Systeem** van de computer die als host fungeert voor de sitesysteemrol.  

De volgende sitesysteemrollen verbinding met Internet en mogelijk een proxyserver nodig.  Met één uitzondering, sitesysteemrollen die u een proxy kunnen gebruiken, doen dit zonder aanvullende configuratie. De uitzondering hierop is het software-updatepunt. De volgende lijst bevat informatie over de aanvullende configuraties die een software-updatepunt vereist:  

**Asset Intelligence-synchronisatiepunt** -deze sitesysteemrol maakt verbinding met Microsoft en gebruikt een proxyserverconfiguratie op de computer die als host fungeert voor de Asset Intelligence-synchronisatiepunt.  

**Cloud-gebaseerde distributiepunt** - voor het instellen van een proxyserver voor een cloud-gebaseerd distributiepunt, het instellen van de proxy op de primaire site die het cloud-gebaseerde distributiepunt beheert.  

Voor deze configuratie moet de primaire siteserver:  

-   Moet verbinding maken met Microsoft Azure instellen, bewaken en distribueren van inhoud naar het distributiepunt.  

-   Maakt gebruik van het systeemaccount van de computer de verbinding te maken.  

-   Standaardwebbrowser van de computer.  

U kunt een proxyserver op de cloud-gebaseerde distributiepunt in de Microsoft Azure niet instellen.  

**Cloudverbindingspunt** -deze sitesysteemrol maakt verbinding met de cloudservice van Configuration Manager versie-updates te downloaden voor Configuration Manager en maakt gebruik van een proxyserver die geconfigureerd op de computer die als host fungeert voor het serviceverbindingspunt wordt gehost.  

**Exchange Server-connector** -deze sitesysteemrol maakt verbinding met een Exchange-Server en gebruikt een proxyserverconfiguratie op de computer die als host fungeert voor de Exchange Server-connector.  

**Serviceaansluitpunt** -deze sitesysteemrol maakt verbinding met Microsoft Intune en gebruikt een proxyserverconfiguratie op de computer die als host fungeert voor het serviceverbindingspunt wordt gehost.  

**Software-updatepunt** - deze sitesysteemrol kan de proxy gebruiken bij het verbinden met Microsoft Update om patches te downloaden en informatie over updates te synchroniseren. Als u deze optie inschakelt, bij het instellen van de software-updatepunt, software-updatepunten een proxy gebruikt alleen voor de volgende opties:  

-   **Gebruik een proxyserver bij het synchroniseren van software-updates**  

-   **Een proxyserver gebruiken wanneer inhoud wordt gedownload via automatische implementatieregels** (beschikbaar voor gebruik, deze instelling wordt niet gebruikt door software-updatepunten op secundaire sites.)  

Configureer de proxyserverinstellingen op de pagina actief Software-updatepunt van de wizard sitesysteemrollen toevoegen of op de **algemene** tabblad **eigenschappen van Software-Update**.  

-   De proxyserverinstellingen zijn alleen gekoppeld met het software-updatepunt op de site.  

-   Proxyserveropties zijn alleen beschikbaar wanneer een proxyserver is al ingesteld voor de sitesysteemserver die als host fungeert voor de software-updatepunt.  

> [!NOTE]  
>  Standaard wordt het account **Systeem** voor de server waarop een automatische implementatieregel is gemaakt, gebruikt om verbinding te maken met internet en software-updates te downloaden wanneer de automatische implementatieregels worden uitgevoerd.  
>   
>  Wanneer dit account geen toegang het Internet tot, software-updates niet worden gedownload en de volgende vermelding wordt vastgelegd in het logboekbestand ruleengine.log opgeslagen: **De update downloaden van internet is mislukt. Fout = 12007.**  

#### <a name="to-set-up-the-proxy-server-for-a-site-system-server"></a>Voor het instellen van de proxyserver voor een sitesysteemserver  

1.  Kies in de Configuration Manager-console **beheer**, vouw **siteconfiguratie**, en kies vervolgens **Servers en sitesysteemrollen**.  

2.  Kies de sitesysteemserver die u wilt bewerken in de details van het deelvenster met de rechtermuisknop op **sitesysteem**, en kies vervolgens **eigenschappen**.  

3.  Selecteer in de eigenschappen van sitesysteem het **Proxy** tabblad en vervolgens de proxy-instellingen voor deze primaire siteserver instellen.  

4.  Kies **OK** om op te slaan van de nieuwe proxyserverconfiguratie serverconfiguratie.  
