---
title: Cloudservices gebruiken om te voorzien in on-premises infrastructuur
titleSuffix: Configuration Manager
description: Cloudresources inrichten voor System Center Configuration Manager om te voorzien in uw on-premises infrastructuur.
ms.custom: na
ms.date: 10/06/2016
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: configmgr-other
ms.tgt_pltfrm: na
ms.topic: get-started-article
ms.assetid: 24fca61e-9cdb-447a-ad7a-f4d2e4fd6704
caps.latest.revision: "10"
caps.handback.revision: "0"
author: Brenduns
ms.author: brenduns
manager: angrobe
ms.openlocfilehash: f3a167433f90dc111d8f7e5e912db7360df5bfcf
ms.sourcegitcommit: c236214b2fcc13dae7bad96d7fb33f692868191d
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/12/2017
---
# <a name="use-cloud-services-with-system-center-configuration-manager"></a>Cloudservices met System Center Configuration Manager gebruiken

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*

System Center Configuration Manager ondersteunt verschillende cloudopties. Deze kunnen vormen een aanvulling op uw on-premises infrastructuur en kunnen op te lossen zakelijke problemen zoals:  

-   Het beheren van BYOD (met behulp van Intune mobile device Management).  

-   Klik hier voor meer informatie over het inhoudsbronnen voorzien geïsoleerde clients of bronnen op intranet buiten uw bedrijfsfirewall (met behulp van cloud-gebaseerde distributiepunten).  

-   Klik hier voor meer informatie over het infrastructuur uitbreiden wanneer fysieke hardware is niet beschikbaar of logisch ter ondersteuning van uw behoeften (door Microsoft Azure virtuele machines) niet is geplaatst.  

Hoewel cloudresources inrichting niet iets die u doen moet voordat u Configuration Manager implementeert, kan het nuttig om te begrijpen van deze opties voordat het verloopt te ver in het ontwerpplan voor een hiërarchie zijn. Het gebruik van cloudbronnen bespaart u mogelijk tijd en geld, bij het oplossen van bedrijfsproblemen die on-premises infrastructuur kan niet.  

## <a name="cloud-based-resources-you-can-use-with-configuration-manager"></a>Cloudresources kunt u met Configuration Manager  
 Omdat er voor elke optie verschillende vereisten gelden, is het zinvol om u hierin te verdiepen zodat u bekend raakt met de unieke vereisten, beperkingen en mogelijkheden voor extra kosten op basis van het gebruik.  

-   Zie voor meer informatie over cloud-gebaseerde distributiepunten [cloud-gebaseerde distributiepunten installeren](/sccm/core/servers/deploy/configure/install-cloud-based-distribution-points-in-microsoft-azure).

-   Zie voor meer informatie over Azure [Azure](http://go.microsoft.com/fwlink/p/?LinkId=262965) in de MSDN-bibliotheek.  

### <a name="azure-virtual-machines-for-cloud-based-infrastructure"></a>Azure virtuele machines (voor een cloudinfrastructuur)  
 Configuration Manager ondersteunt het gebruik van computers die worden uitgevoerd op virtuele machines in Azure, net zoals het on-premises in uw fysieke bedrijfsnetwerk worden uitgevoerd. U kunt in de volgende scenario's kunt virtuele Azure-machines gebruiken:  

-   **Scenario 1:** U kunt de Configuration Manager uitvoeren op een virtuele machine en gebruiken voor het beheren van clients die zijn geïnstalleerd op andere virtuele machines.  

-   **Scenario 2:** U kunt de Configuration Manager uitvoeren op een virtuele machine en gebruiken voor het beheren van clients die niet worden uitgevoerd in Azure.  

-   **Scenario 3:** U kunt verschillende sitesysteemrollen van Configuration Manager uitvoeren op virtuele machines tegelijkertijd andere rollen uitvoeren in uw fysieke bedrijfsnetwerk (met de juiste netwerkverbinding voor communicatie).  

Dezelfde vereisten voor netwerken, besturingssystemen en hardwarevereisten die betrekking hebben op de Configuration Manager installeren op uw fysieke bedrijfsnetwerk zijn ook van toepassing op de installatie van Configuration Manager in Azure.  

Een Azure-abonnement is vereist voor het gebruik van virtuele machines in Azure. U kosten op basis van het aantal virtuele machines dat u gebruikt, hun configuratie en gebruik van cloudresources.  

Configuration Manager-sites en clients die worden uitgevoerd in Azure virtuele machines zijn daarnaast onderworpen aan dezelfde licentievereisten als on-premises installaties.  

### <a name="azure-services-for-cloud-based-distribution-points"></a>Azure-services (voor cloud-gebaseerde distributiepunten)  
 U kunt een Azure-service gebruiken voor het hosten van een Configuration Manager-distributiepunt een opgeroepen cloud-gebaseerd distributiepunt wordt aangeroepen. U kunt [een cloud-gebaseerd distributiepunt gebruiken met System Center Configuration Manager](../../core/plan-design/hierarchy/use-a-cloud-based-distribution-point.md) naast on-premises distributiepunten en distributiepunten die zijn geïmplementeerd in virtuele machines in Azure.  

 Dit verschilt van het gebruik van een virtuele Azure-machine, waarop u een sitesysteemrol implementeert. Cloud-gebaseerde distributiepunten:  

-   Als een service in Azure, niet op een virtuele machine wordt uitgevoerd.  

-   Automatisch schalen om te voldoen aan de toegenomen inhoudsaanvragen van clients.  

-   Ondersteuning voor clients op het Internet en intranet.  

Een Azure-abonnement is vereist voor het gebruik van Azure naar de distributiepunten host. U kosten op basis van de hoeveelheid gegevens die worden verstuurd naar en van de service.  

### <a name="microsoft-intune-for-mobile-device-management"></a>Microsoft Intune (voor beheer van mobiele apparaten)  
 U kunt uw Microsoft Intune-abonnement integreren met Configuration Manager voor beheer van apparaten met behulp van de Intune-service. Deze integratie:  

-   Wordt een hybride configuratie genoemd en deze breidt Configuration Manager (of Intune, afhankelijk van uw perspectief) ter ondersteuning van een groot aantal apparaten.  

-   Vereist de Microsoft Intune-Connector-sitesysteemrol.  

-   Moet u een afzonderlijke Intune-abonnement met voldoende licenties voor de apparaten die u met Intune beheren wilt hebben.  

Hoewel Intune Azure gebruikt, dit vereist niet dat u Azure apart te configureren en worden extra kosten in rekening naast het Intune-abonnement.  

### <a name="additional-configuration-manager-capabilities"></a>Aanvullende Configuration Manager-functies  
 Bepaalde functies van Configuration Manager verbinding kunnen maken met cloudservices, zoals:  

-   Windows Server updateservices (WSUS).  

-   De Configuration Manager servicecloud om updates te downloaden voor Configuration Manager.  

Deze aanvullende mogelijkheden hebben niet nodig dat u hebt een Azure-abonnement. Er geen specifieke verbindingen, certificaten of services instellen in de cloud. In plaats daarvan worden ze automatisch door Configuration Manager beheerd voor u. U moet doen maar zorgen dat de betreffende sitesystemen en apparaten hebben toegang tot de URL op basis van het Internet.  

##  <a name="BKMK_CloudSec"></a>Beveiliging voor cloudservices  
 Configuration Manager gebruikt certificaten in te richten en toegang tot uw inhoud in Azure en het beheren van de services die u gebruikt. Configuration Manager versleutelt de gegevens die u in Azure opslaat, maar er wordt geen aanvullende beveiliging of gegevensbeheer toegevoegd naast die door Azure worden geboden.  

 Zie de details voor de verschillende cloudresourcescenario's voor meer informatie. U kunt ook de volgende onderwerpen voor Azure-beveiliging bekijken:  

-   [Azure: Wat is Security Account Management in Azure?](http://go.microsoft.com/fwlink/p/?LinkId=262968)  

-   [Overzicht Azure-beveiliging](http://go.microsoft.com/fwlink/p/?LinkId=262970)  

-   [Hoe krijg ik Beveiligingsdilemma's tijdens de Cloudmigratie overwinnen](http://go.microsoft.com/fwlink/p/?LinkId=262971)  

-   [Gegevensbeveiliging in Azure, deel 1 van 2](http://go.microsoft.com/fwlink/p/?LinkId=262974)  
