---
title: Cloudservices gebruikt met Configuration Manager | Microsoft-documenten
description: Inrichten cloud-bronnen voor System Center Configuration Manager om te voorzien in uw on-premises infrastructuur.
ms.custom: na
ms.date: 10/06/2016
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: get-started-article
ms.assetid: 24fca61e-9cdb-447a-ad7a-f4d2e4fd6704
caps.latest.revision: 10
caps.handback.revision: 0
author: Brenduns
ms.author: brenduns
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 0d7ddd48cc4e75b12f893e686b847d66058441e1
ms.openlocfilehash: 52f7c63d155d5c34f0f12e13020767dec1867dab
ms.contentlocale: nl-nl
ms.lasthandoff: 05/17/2017


---
# <a name="use-cloud-services-with-system-center-configuration-manager"></a>Cloudservices met System Center Configuration Manager gebruiken

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*

System Center Configuration Manager ondersteunt verschillende opties voor cloud-gebaseerde. Deze aanvullen uw on-premises infrastructuur en u kunnen helpen bij het oplossen van zakelijke problemen zoals:  

-   Hoe BYOD (met behulp van Intune voor het beheer van mobiele apparaten).  

-   Het doorgeven van hulpbronnen voor inhoud geïsoleerd clients of resources op het intranet buiten de firewall van uw bedrijf (met behulp van cloud-gebaseerde distributiepunten).  

-   Klik hier voor meer informatie over het uitbreiden van infrastructuur als fysieke hardware niet beschikbaar of logisch ter ondersteuning van uw behoeften (met behulp van Microsoft Azure virtual machines) niet is geplaatst.  

Hoewel inrichting cloud-bronnen niet iets dat die u doen moet voordat u Configuration Manager implementeert, kan het nuttig om te begrijpen van deze opties voordat vast te ver in een hiërarchie-ontwerp-indeling zijn. Het gebruik van cloud-bronnen kan u tijd en geld besparen, bij het oplossen van bedrijfsproblemen die on-premises infrastructuur kan niet.  

## <a name="cloud-based-resources-you-can-use-with-configuration-manager"></a>Cloud-gebaseerde resources die kunt u met Configuration Manager  
 Omdat er voor elke optie verschillende vereisten gelden, is het zinvol om u hierin te verdiepen zodat u bekend raakt met de unieke vereisten, beperkingen en mogelijkheden voor extra kosten op basis van het gebruik.  

-   Zie voor meer informatie over cloud-gebaseerde distributiepunten [cloud-gebaseerde distributiepunten installeren](/sccm/core/servers/deploy/configure/install-cloud-based-distribution-points-in-microsoft-azure).

-   Zie voor meer informatie over Azure [Azure](http://go.microsoft.com/fwlink/p/?LinkId=262965) in de MSDN-bibliotheek.  

### <a name="azure-virtual-machines-for-cloud-based-infrastructure"></a>Azure virtuele machines (voor cloud-gebaseerde infrastructuur)  
 Configuration Manager ondersteunt het gebruik van computers waarop de virtuele machines in Azure, net zoals lokale binnen uw fysieke bedrijfsnetwerk wanneer kan worden uitgevoerd. U kunt in de volgende scenario's kunt virtuele Azure-machines gebruiken:  

-   **Scenario 1:** U kunt Configuration Manager uitvoeren op een virtuele machine en deze gebruiken voor het beheren van clients die zijn geïnstalleerd in andere virtuele machines.  

-   **Scenario 2:** U kunt Configuration Manager uitvoeren op een virtuele machine en deze gebruiken voor het beheren van clients die niet worden uitgevoerd in Azure.  

-   **Scenario 3:** U kunt verschillende sitesysteemfuncties van Configuration Manager uitvoeren op virtuele machines tijdens het uitvoeren van andere functies in uw fysieke bedrijfsnetwerk (met de juiste netwerkverbinding voor communicatie).  

Dezelfde vereisten voor netwerken, besturingssystemen en hardwarevereisten die betrekking hebben op de Configuration Manager installeren op het fysieke netwerk zijn ook van toepassing op de installatie van Configuration Manager in Azure.  

Een Azure-abonnement is vereist voor het gebruik van virtuele machines in Azure. U kosten op basis van het aantal virtuele machines die u gebruikt, hun configuratie en gebruik van cloud-gebaseerde resources in rekening gebracht.  

Configuration Manager-sites en clients die worden uitgevoerd in de virtuele machines in Azure zijn daarnaast onderworpen aan dezelfde licentievereisten als lokale installaties.  

### <a name="azure-services-for-cloud-based-distribution-points"></a>Azure-services (voor cloud-gebaseerde distributiepunten)  
 U kunt een Azure-service gebruiken voor het hosten van een Configuration Manager-distributiepunt een genoemd cloud-gebaseerd distributiepunt wordt genoemd. U kunt [cloud-gebaseerde distributiepunt gebruiken met System Center Configuration Manager](../../core/plan-design/hierarchy/use-a-cloud-based-distribution-point.md) naast de on-premises distributiepunten en distributiepunten die zijn geïmplementeerd in virtuele machines in Azure.  

 Dit verschilt van het gebruik van een virtuele Azure-machine, waarop u een sitesysteemrol implementeert. Cloud-gebaseerde distributiepunten:  

-   Als een service in Azure, niet op een virtuele machine uitgevoerd.  

-   Automatisch schalen om te voldoen aan de toegenomen inhoud aanvragen van clients.  

-   Ondersteuning voor clients op het Internet en intranet.  

Een Azure-abonnement is vereist voor het gebruik van Azure naar de distributiepunten host. U gevolgen voor de kosten op basis van de hoeveelheid gegevens die worden verstuurd naar en van de service.  

### <a name="microsoft-intune-for-mobile-device-management"></a>Microsoft Intune (beheer van mobiele apparaten)  
 U kunt uw Microsoft Intune-abonnement integreren met Configuration Manager voor het beheer van apparaten met behulp van de Intune-service. Deze integratie:  

-   Een hybride-configuratie wordt genoemd en Configuration Manager (of Intune, afhankelijk van uw perspectief) ter ondersteuning van een groot aantal apparaten wordt uitgebreid.  

-   Vereist de Microsoft Intune-Connector-sitesysteemrol.  

-   Moet u beschikken over een afzonderlijke Intune-abonnement met voldoende licenties voor de apparaten die u met Intune beheren wilt.  

Hoewel Intune Azure gebruikt, deze vereist niet dat u Azure afzonderlijk te configureren, noch gelden aanvullende kosten tot voorbij dat het Intune-abonnement.  

### <a name="additional-configuration-manager-capabilities"></a>Aanvullende Configuration Manager-functies  
 Sommige mogelijkheden van Configuration Manager verbinding kunnen maken met cloud-gebaseerde services, zoals:  

-   Windows Server updateservices (WSUS).  

-   De Configuration Manager service cloud, voor het downloaden van updates voor Configuration Manager.  

Deze extra functies niet vereisen dat u hebt een Azure-abonnement. U hebt geen specifieke verbindingen, certificaten of services instellen in de cloud. In plaats daarvan worden ze automatisch beheerd door Configuration Manager voor u. Alles wat u moet doen is Zorg ervoor dat de betreffende site-systemen en apparaten krijgen toegang tot de URL op basis van het Internet.  

##  <a name="BKMK_CloudSec"></a>Beveiliging voor cloud-gebaseerde services  
 Configuration Manager maakt gebruik van certificaten in te richten en heeft toegang tot de inhoud in Azure en voor het beheren van de services die u gebruikt. Configuration Manager codeert de gegevens die u in Azure opslaat, maar wordt geen aanvullende beveiliging of gegevensbeheer toegevoegd naast Azure zelf.  

 Zie de details voor de andere resource cloud-gebaseerde scenario's voor meer informatie. U kunt ook de volgende onderwerpen voor Azure-beveiliging weergeven:  

-   [Azure: Security Account Management in Azure begrijpen](http://go.microsoft.com/fwlink/p/?LinkId=262968)  

-   [Overzicht van Azure-beveiliging](http://go.microsoft.com/fwlink/p/?LinkId=262970)  

-   [Beveiligingsdilemma's tijdens de Cloudmigratie overwinnen](http://go.microsoft.com/fwlink/p/?LinkId=262971)  

-   [Gegevensbeveiliging in Azure, deel 1 van 2](http://go.microsoft.com/fwlink/p/?LinkId=262974)  

