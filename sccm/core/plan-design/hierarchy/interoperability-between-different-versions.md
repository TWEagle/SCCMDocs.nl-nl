---
title: Interoperabiliteit tussen de versies van Configuration Manager | Microsoft-documenten
description: "Informatie over het voorkomen van conflicten tussen meerdere hiërarchieën van System Center Configuration Manager op hetzelfde netwerk."
ms.custom: na
ms.date: 1/30/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 9b0a7859-747f-4495-a2f4-13fd5991f897
caps.latest.revision: 8
author: Brenduns
ms.author: brenduns
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: dab5da5a4b5dfb3606a8a6bd0c70a0b21923fff9
ms.openlocfilehash: 28593d271603ff9775425327996d844d7ed358cd
ms.contentlocale: nl-nl
ms.lasthandoff: 05/17/2017


---
# <a name="interoperability-between-different-versions-of-system-center-configuration-manager"></a>Interoperabiliteit tussen verschillende versies van System Center Configuration Manager

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*

U kunt installeren en te gebruiken meerdere, onafhankelijke hiërarchieën van System Center Configuration Manager op hetzelfde netwerk. Omdat verschillende hiërarchieën van Configuration Manager niet buiten het migratieproces samenwerken, vereist elke hiërarchie configuraties om conflicten tussen elkaar voorkomen. Daarnaast kunt u bepaalde configuraties bronnen die u beheert, helpen interageren met de sitesystemen van de juiste hiërarchie.  

 De volgende secties bieden informatie over het gebruik van verschillende versies van Configuration Manager op hetzelfde netwerk:  

-   [Interoperabiliteit tussen System Center Configuration Manager en eerdere productversies](#BKMK_SupConfigInterop)  

-   [Samenwerking voor de Configuration Manager-console](#BKMK_ConsoleInterop)  

-   [Beperkingen voor Configuration Manager in een hiërarchie met verschillende versies](#bkmk_mixed)  

##  <a name="BKMK_SupConfigInterop"></a> Interoperabiliteit tussen System Center Configuration Manager en eerdere productversies  
 Sites met verschillende versies kunnen niet tegelijk bestaan in dezelfde hiërarchie, behalve tijdens de upgrade van System Center 2012 Configuration Manager voor System Center Configuration Manager of van één versie van System Center Configuration Manager naar een nieuwere versie (in de console-updates via).   

 Omdat u een System Center Configuration Manager-site en hiërarchie side-by-side met een bestaande System Center 2012 Configuration Manager-site of hiërarchie, het is raadzaam dat u van plan bent om te voorkomen dat clients van een bepaalde versie proberen te vervoegen van een site in de andere versie.

Als u twee of meer Configuration Manager-hiërarchieën overlappende grenzen hebben bijvoorbeeld (Zie [overlappende grenzen](/sccm/core/servers/deploy/configure/boundary-groups#overlapping-boundaries)) die dezelfde netwerklocaties bevatten, is het aanbevolen om elke nieuwe client toewijzen aan een specifieke site in plaats van met automatische sitetoewijzing. Zie voor meer informatie over automatische sitetoewijzing in System Center 2012 Configuration Manager [clients toewijzen aan een site in System Center Configuration Manager](../../../core/clients/deploy/assign-clients-to-a-site.md).  

 Daarnaast wordt u een client van System Center 2012 Configuration Manager niet installeren op een computer die als host fungeert voor een sitesysteemrol van System Center Configuration Manager, noch kunt u een System Center Configuration Manager-client installeert op een computer die als host fungeert voor een sitesysteemrol van System Center 2012 Configuration Manager.  

 Op dezelfde manier worden de volgende clients en de volgende Virtual Private Network (VPN)-verbinding niet ondersteund:  

-   Elke System Center 2012 Configuration Manager of oudere computerclient-versie  

-   Alle System Center 2012 Configuration Manager of oudere apparaatbeheerclient  

-   Windows CE Platform Builder apparaatbeheerclient (alle versies)  

-   System Center Mobile Device Manager VPN-verbinding  

###  <a name="BKMK_SupConfigSiteAssignment"></a> Overwegingen voor de sitetoewijzing van de client  
 System Center Configuration Manager-clients kunnen worden toegewezen aan slechts één primaire site. Wanneer automatische sitetoewijzing gebruikt wordt om clients toe te wijzen aan een site tijdens clientinstallatie en meer dan één grensgroep bevat dezelfde grens, en de grensgroepen hebben verschillende toegewezen sites, kan de huidige toewijzing van een client niet voorspeld worden.  

 Indien grenzen op meerdere Configuration Manager-sites en hiërarchieën overlappen, kunnen clients niet worden toegewezen aan de site die u verwacht of helemaal niet toegewezen aan een site in het geheel.  

 System Center Configuration Manager-clients controleren de versie van de Configuration Manager-site vóór ze de site-toewijzing vervolledigen en kunnen niet worden toegewezen aan een eerdere versie wanneer en als sitegrenzen overlappen. System Center 2012 Configuration Manager-clients mogelijk niet correct worden toegewezen aan een System Center Configuration Manager-site.  

 Om te voorkomen dat clients toegewezen worden aan de verkeerde site wanneer twee hiërarchieën overlappende grenzen hebben, raden wij aan dat u Configuration Manager-clientinstallatieparameters om clients toewijzen aan een specifieke site configureren.  

##  <a name="bkmk_mixed"></a>Configuration Manager-beperkingen in een gemengde hiërarchie  
 Als u een upgrade van een System Center Configuration Manager-site, zijn er tijden wanneer verschillende sites met verschillende versies. Het is bijvoorbeeld mogelijk dat wanneer u een centrale beheersite bijwerkt naar een nieuwere versie, een of meer primaire sites vanwege de onderhoudsvenster voor de site pas later worden bijgewerkt.  

 Wanneer verschillende sites in één hiërarchie verschillende versies uitvoeren, zijn bepaalde functies niet beschikbaar. Dit kan beïnvloeden hoe het beheren van Configuration Manager-objecten in de Configuration Manager-console, en welke functionaliteit beschikbaar zijn voor clients. Functionaliteit van de nieuwere versie van Configuration Manager is doorgaans niet toegankelijk op sites of voor clients die een lagere servicepackversie uitvoeren.  

### <a name="limitations-when-upgrading--configuration-manager"></a>Beperkingen bij het upgraden van Configuration Manager  

|Object|Details|  
|------------|-------------|  
|Netwerktoegangsaccount|**Bij het upgraden van System Center 2012 Configuration Manager voor System Center Configuration Manager:** Als u de accountdetails netwerk van een Configuration Manager-console die verbonden met een centrale beheersite die is bijgewerkt naar System Center Configuration Manager weergeeft, worden met de console geen details voor accounts die geconfigureerd zijn op een primaire site met System Center 2012 Configuration Manager weer. Nadat de primaire site wordt bijgewerkt naar dezelfde versie als de centrale beheersite, zijn de accountdetails zichtbaar in de console.<br /><br /> **Bij een upgrade tussen versies van System Center Configuration Manager:** Als u de accountdetails netwerk van een Configuration Manager-console die verbonden met een centrale beheersite die is bijgewerkt naar een nieuwe versie van System Center Configuration Manager weergeeft, worden met de console geen details voor accounts die geconfigureerd zijn op een primaire site waarop een vorige versie weer. Nadat de primaire site wordt bijgewerkt naar dezelfde versie als de centrale beheersite, zijn de accountdetails zichtbaar in de console.|  
|Opstartinstallatiekopieën voor implementatie van besturingssysteem|**Bij het upgraden van System Center 2012 Configuration Manager voor System Center Configuration Manager:**  Wanneer de site op het hoogste niveau van een hiërarchie wordt bijgewerkt naar System Center Configuration Manager, wordt de standaardopstartinstallatiekopieën worden automatisch bijgewerkt opstartinstallatiekopieën op basis van Windows Assessment and Deployment Kit 10 (Windows ADK). Gebruik deze opstartinstallatiekopieën enkel voor implementaties naar clients op System Center Configuration Manager-sites. Zie [De interoperabiliteit voor de besturingssysteemimplementatie plannen in System Center Configuration Manager](../../../osd/plan-design/planning-for-operating-system-deployment-interoperability.md) voor meer informatie.<br /><br /> **Bij een upgrade tussen versies van System Center Configuration Manager:** Als nieuwe versies van cm6long de versie van Windows-ADK die wordt gebruikt niet bijwerkt, is er geen invloed op de opstartinstallatiekopieën.|  
|Stappen voor nieuwe takenreeksen|Wanneer u een takenreeks met een stap die is geïntroduceerd in één versie van Configuration Manager die is niet beschikbaar in een eerdere versie maakt, kunnen de volgende problemen optreden:<br /><br /> --Er is een fout optreedt wanneer u probeert te bewerken van de takenreeks van een site waarop een eerdere versie van Configuration Manager wordt uitgevoerd.<br /><br /> --De takenreeks kan niet worden uitgevoerd op een computer waarop een vorige versie van de Configuration Manager-client.|  
|Downlevel punt communicatie tussen clients en|Configuration Manager-client die communiceert met een beheerpunt vanuit een site die een lagere versie dan de client wordt uitgevoerd, kan enkel functionaliteit die ondersteuning biedt voor de eerdere versie van Configuration Manager gebruiken. Als u inhoud vanuit een System Center Configuration Manager-site die onlangs is bijgewerkt naar een client die communiceert met een beheerpunt dat nog niet is bijgewerkt naar versie implementeert, kan deze client bijvoorbeeld nieuwe functionaliteit van de meest recente versie gebruiken.|  

##  <a name="BKMK_ConsoleInterop"></a>Samenwerking voor de Configuration Manager-console  
 De volgende tabel bevat informatie over het gebruik van de Configuration Manager-console in een omgeving die een mix van Configuration Manager-versies heeft.  

|Samenwerkingsomgeving|Meer informatie|  
|----------------------------------|----------------------|  
|Een omgeving met System Center 2012 Configuration Manager en System Center Configuration Manager|Voor het beheren van een Configuration Manager-site, moeten de console en de site die de console maakt verbinding met dezelfde versie van Configuration Manager uitvoeren. Bijvoorbeeld, u een System Center 2012 Configuration Manager-console niet gebruiken voor een site met System Center Configuration Manager beheren of vice versa.<br /><br /> Het wordt niet ondersteund voor het installeren van de System Center 2012 Configuration Manager-console en de System Center Configuration Manager-console op dezelfde computer.|  
|Een omgeving met meerdere versies van System Center Configuration Manager.|System Center Configuration Manager biedt geen ondersteuning voor het installeren van meer dan één Configuration Manager-console op een computer. Voor het gebruik van meerdere consoles die specifiek voor verschillende versies van System Center Configuration Manager zijn, moet u de verschillende versies op afzonderlijke computers installeren.<br /><br /> Tijdens het bijwerken van sites in een hiërarchie naar een nieuwe versie, kunt u een console verbinden met een site met een nieuwere versie en informatie te bekijken van andere sites in die hiërarchie. Deze configuratie wordt niet aanbevolen omdat het is mogelijk dat verschillen tussen de console en siteversie van Configuration Manager-tot problemen met gegevens leiden kunnen en sommige functies die beschikbaar in de meest recente versie van het product zijn niet meer beschikbaar in de console. <br />< /br / > een site beheren wanneer u een console met een versie die niet overeenkomen met de site-versie wordt niet ondersteund. In dat geval kan leiden tot verlies van gegevens en uw site risico kunt plaatsen. Bijvoorbeeld, wordt het niet ondersteund voor het gebruik van een console van versie 1610 voor het beheren van een site waarop versie 1606. |

