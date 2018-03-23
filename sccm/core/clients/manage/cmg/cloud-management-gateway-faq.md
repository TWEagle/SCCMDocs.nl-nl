---
title: VEELGESTELDE VRAGEN OVER CMG
description: In dit artikel gebruiken om te beantwoorden Veelgestelde vragen over de cloud-management-gateway
author: aczechowski
ms.author: aaroncz
manager: dougeby
ms.date: 03/22/2018
ms.topic: article
ms.prod: configuration-manager
ms.technology:
- configmgr-other
ms.assetid: 4c1a128d-22fb-49f1-8e0b-36513a8dc117
ms.openlocfilehash: 8615b28735165650a0ec25e3d3114263835803d6
ms.sourcegitcommit: 11bf4ed40ed0cbb10500cc58bbecbd23c92bfe20
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 03/23/2018
---
# <a name="frequently-asked-questions-about-the-cloud-management-gateway"></a>Veelgestelde vragen over de cloud-management-gateway

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*

Dit artikel worden de veelgestelde vragen over de cloud management gateway. Zie voor meer informatie [plan voor cloud-beheergateway](/sccm/core/clients/manage/cmg/plan-cloud-management-gateway).


## <a name="frequently-asked-questions"></a>Veelgestelde vragen

### <a name="what-certificates-do-i-need"></a>Welke certificaten moet ik gebruiken?

Voor meer informatie gedetailleerde, Zie [certificaten voor beheer cloudgateway](/sccm/core/clients/manage/cmg/certificates-for-cloud-management-gateway).


### <a name="do-i-need-azure-expressroute"></a>Heb ik nodig Azure ExpressRoute?

[Azure ExpressRoute](/azure/expressroute/expressroute-introduction) kunt u uw on-premises netwerk in de Microsoft cloud uitbreiden. ExpressRoute- of andere dergelijke virtuele netwerkverbindingen zijn niet vereist voor de Configuration Manager cloud management gateway. Het ontwerp van de cloud management gateway kan clients op internet om te communiceren via de Azure-service naar de on-premises sitesystemen waarvoor geen extra netwerk-configuratie. Zie voor meer informatie [cloudgateway management plannen](/sccm/core/clients/manage/cmg/plan-cloud-management-gateway)

Als uw organisatie gebruikmaakt van ExpressRoute, is een aanbevolen beveiligingsprocedure voor het isoleren van de Azure-abonnement voor de cloud management gateway. Deze configuratie zorgt ervoor dat de cloud management gateway-service niet per ongeluk op deze manier wordt verbonden. Zie voor meer informatie [beveiliging en privacy voor beheer cloudgateway](/sccm/core/clients/manage/cmg/security-and-privacy-for-cloud-management-gateway).


### <a name="do-i-need-to-maintain-the-azure-virtual-machines"></a>Heb ik nodig voor het onderhouden van de virtuele machines in Azure?

Er is geen onderhoud vereist. Het ontwerp van de cloud management gateway maakt gebruik van Azure-platform als een service (PaaS). Met behulp van het abonnement dat u opgeeft, maakt Configuration Manager de benodigde virtuele machines (VM's), opslag en netwerken. Azure beveiligt en werkt de virtuele machine. Deze VM's geen onderdeel van uw on-premises-omgeving, zoals het geval bij infrastructuur als een service (IaaS). De cloud management gateway is een PaaS die uitgebreider is dan de Configuration Manager-omgeving naar de cloud. 


### <a name="im-already-using-ibcm-if-i-add-cmg-how-do-clients-behave"></a>Ik gebruik al IBCM. Als ik CMG toevoegt, hoe clients gedragen?

Als u al hebt geïmplementeerd [internet-gebaseerd clientbeheer](/sccm/core/clients/manage/plan-internet-based-client-management) (IBCM), kunt u ook de cloud management gateway implementeren. Clients ontvangen beleid voor beide services. Wanneer deze naar het internet roamen, ze willekeurig selecteren en gebruik een van deze op internet gebaseerde services.


## <a name="next-steps"></a>Volgende stappen

- [Een cloudbeheergateway plannen](/sccm/core/clients/manage/cmg/plan-cloud-management-gateway)
- [Een cloudbeheergateway instellen](/sccm/core/clients/manage/cmg/setup-cloud-management-gateway)
- [Certificaten voor cloud-beheergateway](/sccm/core/clients/manage/cmg/certificates-for-cloud-management-gateway)
- [Beveiliging en privacy voor cloud-beheergateway](/sccm/core/clients/manage/cmg/security-and-privacy-for-cloud-management-gateway)
- [De cloud management gateway-grootte en schaal cijfers](/sccm/core/plan-design/configs/size-and-scale-numbers#bkmk_cmg)