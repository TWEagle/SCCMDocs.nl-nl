---
title: Clients bewaken - Configuration Manager | Microsoft-documenten
description: Krijgen gedetailleerde aanwijzingen voor het bewaken van clients in System Center Configuration Manager.
ms.custom: na
ms.date: 04/23/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-client
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 2c8f57cf-1968-48de-87fb-4897432ed6e0
caps.latest.revision: 23
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 690d03d9c8c49a815bd318df549d7401a855bc5d
ms.openlocfilehash: 08a4d9b29871b49e3118aef949572cef64940f96
ms.contentlocale: nl-nl
ms.lasthandoff: 05/17/2017


---
# <a name="how-to-monitor-clients-in-system-center-configuration-manager"></a>Clients controleren in System Center Configuration Manager

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*


 Zodra de System Center Configuration Manager-clienttoepassing op de Windows-computers en apparaten in uw site is geïnstalleerd, kunt u hun status en activiteit in de Configuration Manager-console bewaken.  

##  <a name="bkmk_about"></a> Over de clientstatus  
 Configuration Manager biedt de volgende soorten informatie als de status van de client:  

-   **Online clientstatus** -vanaf versie 1602 van Configuration Manager wordt deze status geeft aan of de computer online is. Een computer wordt als online beschouwd als de computer is verbonden met het beheerpunt dat eraan is toegewezen.  Om aan te geven dat de client online is, verstuurt het ping-achtige berichten naar het beheerpunt. Als het beheerpunt na ongeveer 5 minuten geen bericht heeft ontvangen, wordt de client als offline beschouwd.  

-   **Clientactiviteit** -deze status geeft aan of de client actief aantrekkelijke met Configuration Manager in de afgelopen 7 dagen is. Als de client de afgelopen 7 dagen geen beleidsupdate heeft aangevraagd of heartbeat-bericht of hardware-inventaris heeft verzonden, wordt de client als inactief beschouwd.  

-   **Clientcontrole** -deze status geeft aan dat het succes van de periodieke evaluatie van de Configuration Manager-client wordt uitgevoerd op de computer.  De evaluatie controleert de computer en herstelt mogelijk enkele gevonden problemen. Zie [Controles en herstel uitgevoerd door clientcontrole](#BKMK_ClientHealth)voor meer informatie.  

     Op computers met Windows 7 worden clientcontroles uitgevoerd als een geplande taak. Voor nieuwere besturingssystemen wordt de clientcontrole automatisch uitgevoerd tijdens het Windows-onderhoudsvenster.  

     U kunt configureren dat herstel niet wordt uitgevoerd op specifieke computers, bijvoorbeeld, een bedrijfskritische server. Bovendien, als er extra items zijn die u wilt evalueren, kunt u instellingen voor naleving van Configuration Manager om op te geven van een uitgebreide oplossing voor het controleren van de algemene status, activiteit en compatibiliteit van computers in uw organisatie. Zie [Instellingen voor naleving plannen en configureren in Configuration Manager](../../../compliance/plan-design/plan-for-and-configure-compliance-settings.md) voor meer informatie over de instellingen voor naleving.  

##  <a name="bkmk_indStatus"></a> De status van afzonderlijke clients controleren  

1.  Klik in de Configuration Manager-console op **activa en naleving** > **apparaten** of kies een verzameling onder **Apparaatverzamelingen**.  

     Vanaf versie 1602 van Configuration Manager, geven de pictogrammen aan het begin van elke rij de online status van het apparaat:  

    |||  
    |-|-|  
    |![online-statuspictogram voor clients](../../../core/clients/manage/media/online-status-icon.png)|Het apparaat is online.|  
    |![offline-statuspictogram voor clients](../../../core/clients/manage/media/offline-status-icon.png)|Het apparaat is offline.|  
    |![onbekende-statuspictogram voor clients](../../../core/clients/manage/media/unknown-status-icon.png)|De onlinestatus is onbekend.|  
    |![client niet geïnstalleerd](../../../core/clients/manage/media/client-not-installed.png)|De client is niet op het apparaat geïnstalleerd.|  

2.  Voor meer gedetailleerde onlinestatus de onlinestatus clientinformatie toevoegen aan het apparaat weergeven met de rechtermuisknop op de kolomkop en klik in de online statusvelden die u wilt toevoegen. Dit zijn de kolommen die u kunt toevoegen:  

    -   **Onlinestatus van het apparaat** geeft aan of de client op dit moment online of offline is. (Dit is opgegeven door de pictogrammen dezelfde informatie).  

    -   **Laatste tijdstip online** geeft aan wanneer de onlinestatus van de client is gewijzigd in online.  

    -   **Laatste tijdstip offline** geeft aan wanneer de status is gewijzigd in offline.  

3.  Klik op een individuele client in het lijstdeelvenster om meer statusgegevens in het deelvenster weer te geven, waaronder informatie over clientactiviteiten en clientcontroles.  

##  <a name="bkmk_allStatus"></a> De status van alle clients controleren  

1.  Klik in de Configuration Manager-console op **bewaking** > **clientstatus**. Op deze pagina van de console kunt u de algemene statistieken voor clientactiviteit en clientcontroles op de site bekijken.  U kunt ook het bereik van de gegevens wijzigen door een andere verzameling te kiezen.  

2.  Als u wilt inzoomen in detail over de gemelde statistische gegevens, klikt u op de naam van de gerapporteerde gegevens (zoals **actieve clients waarbij de clientcontrole, of geen resultaten zijn verstreken**) en controleer de informatie over de afzonderlijke clients.  

3.  Klik op **clientactiviteit** om te zien grafieken met een afbeelding van de activiteit van de client op uw Configuration Manager-site.  

4.  Klik op **clientcontrole** om te zien grafieken met de status van de client controleert in uw Configuration Manager-site.  

 U kunt waarschuwingen configureren om u op de hoogte te brengen wanneer clients resultaten controleren of de clientactiviteit zakt onder een gespecificeerd percentage van clients in een verzameling of wanneer herstel op een gespecificeerd percentage van clients mislukt. Zie [De clientstatus configureren in System Center Configuration Manager](../../../core/clients/deploy/configure-client-status.md) voor meer informatie over het configureren van de clientstatus.  

##  <a name="BKMK_ClientHealth"></a> Controles en herstel uitgevoerd door clientcontrole  
 De volgende controles en herstelbewerkingen kunnen door clientcontrole worden uitgevoerd.  

|Clientcontrole|Herstelactie|Meer informatie|  
|------------------|------------------------|----------------------|  
|Controleer of dat de clientcontrole onlangs is uitgevoerd|Clientcontrole uitvoeren|Controleert of de clientcontrole ten minste eenmaal in de voorbije drie dagen is uitgevoerd.|  
|Controleer of vereiste clientonderdelen zijn geïnstalleerd|Installeer de vereiste clientonderdelen|Controleert of vereiste clientonderdelen zijn geïnstalleerd. Leest het bestand ccmsetup.xml in de clientinstallatiemap om te bepalen welke onderdelen vereist zijn.|  
|Integriteitstest WMI-rapportage|Installeer de Configuration Manager-client opnieuw|Controleert of de clientvermeldingen van Configuration Manager-in WMI aanwezig zijn.|  
|Controleer of de clientservice actief is|Start de clientservice (SMS Agent Host)|Geen aanvullende informatie|  
|Test WMI-gebeurtenis-opvanger.|Start de clientservice opnieuw|Controleer of de Configuration Manager gerelateerde WMI-gebeurtenis-opvanger is verbroken|  
|Controleer of de WMI-service (Windows Management Instrumentation) bestaat|Geen herstel mogelijk|Geen aanvullende informatie|  
|Controleer of de client correct is geïnstalleerd|Installeer de client opnieuw|Geen aanvullende informatie|  
|Lees- en schrijftest WMI-opslag|Stel de WMI-opslag en installeer de Configuration Manager-client opnieuw|Herstel van deze clientcontrole wordt alleen uitgevoerd op computers met Windows Server 2003, Windows XP (64-bits) of eerdere versies.|  
|Controleer of het opstarttype voor de antimalwareservice automatisch is|Stel het opstarttype van de service opnieuw in op automatisch|Geen aanvullende informatie|  
|Controleer of de antimalwareservice actief is|Start de antimalwareservice|Geen aanvullende informatie|  
|Controleer of het opstarttype voor de Windows Update-service automatisch of handmatig is|Stel het opstarttype van de service opnieuw in op automatisch|Geen aanvullende informatie|  
|Controleer of het opstarttype voor de clientservice (SMS Agent Host) automatisch is|Stel het opstarttype van de service opnieuw in op automatisch|Geen aanvullende informatie|  
|Controleer of de WMI-service (Windows Management Instrumentation) actief is.|Start de WMI-service|Geen aanvullende informatie|  
|Controleer de conditie van de Microsoft SQL CE-database|Installeer de Configuration Manager-client opnieuw|Geen aanvullende informatie|  
|WMI-integriteitstest van het Microsoft-beleidsplatform|Het Microsoft-beleidsplatform herstellen|Geen aanvullende informatie|  
|Controleer of de service Microsoft-beleidsplatform bestaat|Het Microsoft-beleidsplatform herstellen|Geen aanvullende informatie|  
|Controleer of het opstarttype voor de service Microsoft-beleidsplatform handmatig is.|Stel het opstarttype van de service opnieuw in op handmatig|Geen aanvullende informatie|  
|Controleer of Background Intelligent Transfer Service bestaat|Geen herstel mogelijk|Geen aanvullende informatie|  
|Controleer of het opstarttype voor Background Intelligent Transfer Service automatisch of handmatig is|Stel het opstarttype van de service opnieuw in op automatisch|Geen aanvullende informatie|  
|Controleer of het opstarttype voor de netwerkinspectieservice handmatig is|Stel het opstarttype van de service, indien geïnstalleerd, opnieuw in op handmatig|Geen aanvullende informatie|  
|Controleer of het opstarttype voor de WMI-service (Windows Management Instrumentation) automatisch is.|Stel het opstarttype van de service opnieuw in op automatisch|Geen aanvullende informatie|  
|Controleer of het opstarttype voor de Windows Update-service op Windows 8-computers automatisch of handmatig is|Stel het opstarttype van de service opnieuw in op handmatig|Geen aanvullende informatie|  
|Controleer of de clientservice (SMS Agent Host) bestaat.|Geen herstel mogelijk|Geen aanvullende informatie|  
|Controleer of het opstarttype voor de Configuration Manager-service voor extern beheer automatisch of handmatig is|Stel het opstarttype van de service opnieuw in op automatisch|Geen aanvullende informatie|  
|Controleer of de Configuration Manager-service voor extern beheer wordt uitgevoerd|Start de service voor extern beheer|Geen aanvullende informatie|  
|Controleer de status van de WMI-provider van de client|Start de WMI-service opnieuw|Herstel van deze clientcontrole wordt alleen uitgevoerd op computers met Windows Server 2003, Windows XP (64-bits) of eerdere versies.|  
|Controleer of de service Wake-up proxy wordt uitgevoerd|Start de ConfigMgr-service Wake-up proxy|Deze clientcontrole wordt alleen uitgevoerd als de **energiebeheer**: **Wake-up proxy inschakelen** client-instelling is ingesteld op **Ja** op ondersteunde clientbesturingssystemen.|  
|Controleer of het opstarttype voor de service Wake-up proxy automatisch is|Stel het opstarttype voor de ConfigMgr-service Wake-up proxy opnieuw in op automatisch|Deze clientcontrole wordt alleen uitgevoerd als de **energiebeheer**: **Wake-up proxy inschakelen** client-instelling is ingesteld op **Ja** op ondersteunde clientbesturingssystemen.|  

## <a name="client-deployment-log-files"></a>Logboekbestanden van client-implementatie
Zie voor meer informatie over de logboekbestanden die worden gebruikt door de clientimplementatie en bewerkingen voor [in System Center Configuration Manager-logboekbestanden](/sccm/core/plan-design/hierarchy/log-files#BKMK_ClientLogs).

