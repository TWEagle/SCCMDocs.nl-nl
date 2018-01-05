---
title: Interoperabiliteit tussen versies
titleSuffix: Configuration Manager
description: "Informatie over het voorkomen van conflicten tussen meerdere hiërarchieën voor System Center Configuration Manager op hetzelfde netwerk."
ms.custom: na
ms.date: 1/30/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 9b0a7859-747f-4495-a2f4-13fd5991f897
caps.latest.revision: "8"
author: aczechowski
ms.author: aaroncz
manager: angrobe
ms.openlocfilehash: 66bfb130a27ed8e4b8b9d052a672ef7f72b56f59
ms.sourcegitcommit: ca9d15dfb1c9eb47ee27ea9b5b39c9f8cdcc0748
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 01/04/2018
---
# <a name="interoperability-between-different-versions-of-system-center-configuration-manager"></a>Interoperabiliteit tussen verschillende versies van System Center Configuration Manager

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*

U kunt installeren en gebruiken meerdere, onafhankelijke hiërarchieën van System Center Configuration Manager op hetzelfde netwerk. Omdat verschillende hiërarchieën van Configuration Manager niet buiten het migratieproces samenwerken, vereist elke hiërarchie configuraties om conflicten tussen hen te voorkomen. Bovendien kunt u bepaalde configuraties voor resources die u beheert het communiceren met de sitesystemen van de juiste hiërarchie.  

 De volgende secties bieden informatie over het gebruik van verschillende versies van Configuration Manager op hetzelfde netwerk:  

-   [Interoperabiliteit tussen System Center Configuration Manager en eerdere productversies](#BKMK_SupConfigInterop)  

-   [Samenwerking voor de Configuration Manager-console](#BKMK_ConsoleInterop)  

-   [Beperkingen voor Configuration Manager in een hiërarchie met verschillende versies](#bkmk_mixed)  

##  <a name="BKMK_SupConfigInterop"></a> Interoperabiliteit tussen System Center Configuration Manager en eerdere productversies  
 Sites van verschillende versies kunnen niet worden gecombineerd in dezelfde hiërarchie, behalve tijdens de upgrade van System Center 2012 Configuration Manager naar System Center Configuration Manager of System Center Configuration Manager versie naar een nieuwere versie (met behulp van de updates in de console).   

 Omdat u een System Center Configuration Manager-site en hiërarchie side-by-side met een bestaande System Center 2012 Configuration Manager-site of hiërarchie, wordt aangeraden dat u van plan bent om te voorkomen dat clients van een bepaalde versie proberen een site uit de andere versie toe te voegen.

Bijvoorbeeld, als twee of meer Configuration Manager-hiërarchieën overlappende grenzen hebben (Zie [overlappende grenzen](/sccm/core/servers/deploy/configure/boundary-groups#overlapping-boundaries)) die dezelfde netwerklocaties bevatten, is het aanbevolen elke nieuwe client toewijzen aan een specifieke site in plaats van automatische sitetoewijzing gebruiken. Zie voor meer informatie over automatische sitetoewijzing in System Center 2012 Configuration Manager [clients toewijzen aan een site in System Center Configuration Manager](../../../core/clients/deploy/assign-clients-to-a-site.md).  

 Daarnaast wordt u een client van System Center 2012 Configuration Manager niet installeren op een computer die als host fungeert voor een sitesysteemrol van System Center Configuration Manager, noch kunt u een System Center Configuration Manager-client installeert op een computer die als host fungeert voor een sitesysteemrol van System Center 2012 Configuration Manager.  

 Daarnaast worden de volgende clients en de volgende virtuele particuliere netwerk (VPN)-verbinding niet ondersteund:  

-   Alle System Center 2012 Configuration Manager of oudere computerclient-versie  

-   Alle System Center 2012 Configuration Manager of oudere apparaatbeheerclient  

-   Windows CE Platform Builder device management-client (alle versies)  

-   System Center Mobile Device Manager VPN-verbinding  

###  <a name="BKMK_SupConfigSiteAssignment"></a> Overwegingen voor de sitetoewijzing van de client  
 System Center Configuration Manager-clients kunnen worden toegewezen aan slechts één primaire site. Wanneer automatische sitetoewijzing gebruikt wordt om clients toe te wijzen aan een site tijdens clientinstallatie en meer dan één grensgroep bevat dezelfde grens, en de grensgroepen hebben verschillende toegewezen sites, kan de huidige toewijzing van een client niet voorspeld worden.  

 Indien grenzen op meerdere Configuration Manager-sites en hiërarchieën overlappen, kunnen clients niet worden toegewezen aan de site die u verwacht of helemaal niet toegewezen aan een site op alle.  

 System Center Configuration Manager-clients controleren de versie van de Configuration Manager-site vóór ze de sitetoewijzing voltooien en kunnen niet worden toegewezen aan een eerdere versie wanneer en als sitegrenzen overlappen. System Center 2012 Configuration Manager-clients mogelijk niet goed worden toegewezen aan een System Center Configuration Manager-site.  

 Om te voorkomen dat clients toegewezen worden aan de verkeerde site wanneer twee hiërarchieën overlappende grenzen hebben, is het raadzaam dat u Configuration Manager-clientinstallatieparameters om clients toewijzen aan een specifieke site configureert.  

##  <a name="bkmk_mixed"></a>Beperkingen voor Configuration Manager in een gemengde hiërarchie  
 Wanneer u het upgraden van een System Center Configuration Manager-site, zijn er tijden wanneer verschillende sites met verschillende versies. Het is bijvoorbeeld mogelijk dat wanneer u een centrale beheersite bijwerkt naar een nieuwere versie, een of meer primaire sites vanwege de onderhoudsvenster voor de site pas later worden bijgewerkt.  

 Wanneer verschillende sites in één hiërarchie verschillende versies uitvoeren, zijn bepaalde functies niet beschikbaar. Dit kan beïnvloeden hoe u Configuration Manager-objecten in de Configuration Manager-console beheren, en welke functionaliteit beschikbaar zijn voor clients. De nieuwere versie van Configuration Manager-functionaliteit is normaal gesproken niet toegankelijk op sites of voor clients die een lagere servicepackversie uitvoeren.  

### <a name="limitations-when-upgrading--configuration-manager"></a>Beperkingen bij het upgraden van Configuration Manager  

|Object|Details|  
|------------|-------------|  
|Netwerktoegangsaccount|**Bij een upgrade van System Center 2012 Configuration Manager naar System Center Configuration Manager:** Wanneer u de accountdetails netwerktoegang vanuit een Configuration Manager-console die verbonden met een centrale beheersite die is bijgewerkt naar System Center Configuration Manager weergeeft, biedt de-console geen details weer voor accounts die zijn geconfigureerd op een primaire site waarop System Center 2012 Configuration Manager wordt uitgevoerd. Nadat de primaire site is bijgewerkt naar dezelfde versie als de centrale beheersite, zijn de accountdetails zichtbaar in de console.<br /><br /> **Bij een upgrade tussen versies van System Center Configuration Manager:** Wanneer u de accountdetails netwerktoegang vanuit een Configuration Manager-console die verbonden met een centrale beheersite die is bijgewerkt naar een nieuwe versie van System Center Configuration Manager weergeeft, biedt de-console geen details weer voor accounts die zijn geconfigureerd op een primaire site waarop een eerdere versie wordt uitgevoerd. Nadat de primaire site is bijgewerkt naar dezelfde versie als de centrale beheersite, zijn de accountdetails zichtbaar in de console.|  
|Opstartinstallatiekopieën voor implementatie van besturingssysteem|**Bij een upgrade van System Center 2012 Configuration Manager naar System Center Configuration Manager:**  Wanneer de site op het hoogste niveau van een hiërarchie wordt bijgewerkt naar System Center Configuration Manager, worden de standaardopstartinstallatiekopieën automatisch bijgewerkt opstartinstallatiekopieën op basis van Windows Assessment and Deployment Kit 10 (Windows ADK). Gebruik deze opstartinstallatiekopieën enkel voor implementaties naar clients op System Center Configuration Manager-sites. Zie [De interoperabiliteit voor de besturingssysteemimplementatie plannen in System Center Configuration Manager](../../../osd/plan-design/planning-for-operating-system-deployment-interoperability.md) voor meer informatie.<br /><br /> **Bij een upgrade tussen versies van System Center Configuration Manager:** Zolang nieuwe versies van cm6long de versie van Windows ADK die wordt gebruikt niet bijwerkt, heeft dit geen effect op de installatiekopieën.|  
|Stappen voor nieuwe takenreeksen|Wanneer u een takenreeks met een stap die is geïntroduceerd in een versie van Configuration Manager die is niet beschikbaar in een eerdere versie maakt, kunnen de volgende problemen optreden:<br /><br /> --Er is een fout optreedt wanneer u probeert te bewerken van de takenreeks van een site waarop een eerdere versie van Configuration Manager wordt uitgevoerd.<br /><br /> --De takenreeks kan niet worden uitgevoerd op een computer waarop een eerdere versie van Configuration Manager-client wordt uitgevoerd.|  
|Client naar een lager niveau punt communicatie|Een Configuration Manager-client die communiceert met een beheerpunt vanuit een site waarop een lagere versie dan de client kan alleen functionaliteit gebruiken die de downlevel-versie van Configuration Manager ondersteunt. Als u inhoud vanuit een System Center Configuration Manager-site die onlangs is bijgewerkt naar een client die communiceert met een beheerpunt dat nog niet is bijgewerkt naar deze versie implementeert, niet dat de client bijvoorbeeld nieuwe functionaliteit van de nieuwste versie gebruiken.|  

##  <a name="BKMK_ConsoleInterop"></a>Interoperabiliteit voor de Configuration Manager-console  
 De volgende tabel bevat informatie over het gebruik van de Configuration Manager-console in een omgeving die een mix van Configuration Manager-versies heeft.  

|Samenwerkingsomgeving|Meer informatie|  
|----------------------------------|----------------------|  
|Een omgeving met System Center 2012 Configuration Manager en System Center Configuration Manager|Voor het beheren van een Configuration Manager-site, moeten zowel de console en de site die de console verbinding met maakt dezelfde versie van Configuration Manager uitvoeren. Bijvoorbeeld, u een System Center 2012 Configuration Manager-console niet gebruiken om een System Center Configuration Manager-site te beheren of vice versa.<br /><br /> De System Center 2012 Configuration Manager-console en de System Center Configuration Manager-console installeren op dezelfde computer wordt niet ondersteund.|  
|Een omgeving met meerdere versies van System Center Configuration Manager.|System Center Configuration Manager biedt geen ondersteuning voor het installeren van meer dan één Configuration Manager-console op een computer. Voor het gebruik van meerdere consoles die specifiek voor verschillende versies van System Center Configuration Manager zijn, moet u de verschillende versies op afzonderlijke computers installeren.<br /><br /> Tijdens het proces van updaten van sites in een hiërarchie naar een nieuwe versie, kunt u een console verbinden met een site waarop een nieuwere versie en informatie te bekijken over andere sites in die hiërarchie. Deze configuratie wordt niet aanbevolen omdat het is mogelijk dat verschillen tussen de console en siteversie van Configuration Manager-in gegevensproblemen resulteren kunnen en bepaalde functies die beschikbaar in de meest recente versie van het product zijn niet meer beschikbaar in de console. <br />< /br / > wordt niet ondersteund voor het beheren van een site wanneer u een console met een versie die komt niet overeen met de siteversie. In dat geval kan leiden tot verlies van gegevens en uw site risico kunt plaatsen. Het is bijvoorbeeld niet ondersteund voor het gebruik van een console van versie 1610 voor het beheren van een site waarop versie 1606 wordt uitgevoerd. |
