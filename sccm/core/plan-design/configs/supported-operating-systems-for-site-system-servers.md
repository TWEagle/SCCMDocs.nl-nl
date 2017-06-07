---
title: Ondersteunde sitesysteemservers | Microsoft-documenten
description: Informatie over welke versies van Windows kunt u een System Center Configuration Manager-site of sitesysteemrol hosten.
ms.custom: na
ms.date: 3/9/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 17905b4c-3895-4ad4-a69c-5e0d0fc5a8c3
caps.latest.revision: 44
author: Brenduns
ms.author: brenduns
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: dab5da5a4b5dfb3606a8a6bd0c70a0b21923fff9
ms.openlocfilehash: 86109f7186422c2b29ee933e827a7d14123e5792
ms.contentlocale: nl-nl
ms.lasthandoff: 05/17/2017


---
# <a name="supported-operating-systems-for-system-center-configuration-manager-site-system-servers"></a>Ondersteunde besturingssystemen voor System Center Configuration Manager-sitesysteemservers

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*


Dit artikel wordt de Windows-versies die u gebruiken kunt voor het hosten van een System Center Configuration Manager-site of sitesysteemrol.


Gebruik de informatie in dit onderwerp samen met de informatie in de volgende artikelen:
-   [Aanbevolen hardware voor Configuration Manager](../../../core/plan-design/configs/recommended-hardware.md)
-   [Site- en systeemvereisten site voor Configuration Manager](../../../core/plan-design/configs/site-and-site-system-prerequisites.md)
-   [Grootte en schaal cijfers voor Configuration Manager](../../../core/plan-design/configs/size-and-scale-numbers.md)



## <a name="windows-server-2016-standard-and-datacenter"></a>WindowsServer 2016: Standaard en Datacenter
Vanaf versie 1606 met de hotfix rollup van KB3186654 (of de basislijn-versie van 1606, dat is gepubliceerd in oktober van 2016) wordt dit besturingssysteem ondersteund voor het volgende:

**Siteservers:**  

-   Centrale beheersite  

-   Primaire site  

-   Secundaire site  

**Sitesysteemservers:**  

-   Application Catalog-webservicepunt  

-   Application Catalog-websitepunt  

-   Asset Intelligence-synchronisatiepunt  

-   Certificaatregistratiepunt  

-   Distributiepunt  

     Distributiepunten bieden ondersteuning voor configuraties die elk verschillende vereisten hebben. In sommige gevallen kan ondersteuning voor deze configuraties installatie niet alleen op servers, maar op de client-besturingssystemen. Zie voor meer informatie over de opties die beschikbaar voor distributiepunten zijn [inhoud en -infrastructuur voor System Center Configuration Manager beheert](../../../core/servers/deploy/configure/manage-content-and-content-infrastructure.md).  

-   Endpoint Protection-punt  

-   Inschrijvingspunt  

-   Proxypunt voor inschrijving  

-   Terugvalstatuspunt  

-   Beheerpunt

-   Reporting Services-punt  

-   Serviceverbindingspunt  

-   Sitedatabaseserver  

     Sitedatabaseservers worden niet ondersteund op een alleen-lezen domeincontroller (RODC). Zie [You may encounter problems when installing SQL Server on a domain controller (U kunt problemen ervaren wanneer u SQL Server installeert op een domeincontroller)](http://go.microsoft.com/fwlink/p/?LinkId=264856) in de Microsoft Knowledge Base voor meer informatie. Bovendien worden secundaire siteservers niet ondersteund op domeincontrollers.  

-   SMS_Provider  

-   Software-updatepunt  

-   Statusmigratiepunt

## <a name="windows-server-2012-r2-x64-standard-and-datacenter"></a>Windows Server 2012 R2 (x 64): Standaard en Datacenter  
**Siteservers:**  

-   Centrale beheersite  

-   Primaire site  

-   Secundaire site  

**Sitesysteemservers:**  

-   Application Catalog-webservicepunt  

-   Application Catalog-websitepunt  

-   Asset Intelligence-synchronisatiepunt  

-   Certificaatregistratiepunt  

-   Distributiepunt  

     Distributiepunten bieden ondersteuning voor configuraties die elk verschillende vereisten hebben. In sommige gevallen kan ondersteuning voor deze configuraties installatie niet alleen op servers, maar op de client-besturingssystemen. Zie voor meer informatie over de opties die beschikbaar voor distributiepunten zijn [inhoud en -infrastructuur voor System Center Configuration Manager beheert](../../../core/servers/deploy/configure/manage-content-and-content-infrastructure.md).  

-   Endpoint Protection-punt  

-   Inschrijvingspunt  

-   Proxypunt voor inschrijving  

-   Terugvalstatuspunt  

-   Beheerpunt

-   Reporting Services-punt  

-   Serviceverbindingspunt  

-   Sitedatabaseserver  

     Sitedatabaseservers worden niet ondersteund op een alleen-lezen domeincontroller (RODC). Zie [You may encounter problems when installing SQL Server on a domain controller (U kunt problemen ervaren wanneer u SQL Server installeert op een domeincontroller)](http://go.microsoft.com/fwlink/p/?LinkId=264856) in de Microsoft Knowledge Base voor meer informatie. Bovendien worden secundaire siteservers niet ondersteund op domeincontrollers.  

-   SMS_Provider  

-   Software-updatepunt  

-   Statusmigratiepunt  

## <a name="windows-server-2012-x64-standard-and-datacenter"></a>WindowsServer 2012 (x 64): Standaard en Datacenter  
**Siteservers:**  

-   Centrale beheersite  

-   Primaire site  

-   Secundaire site  

**Sitesysteemservers:**  

-   Application Catalog-webservicepunt  

-   Application Catalog-websitepunt  

-   Asset Intelligence-synchronisatiepunt  

-   Certificaatregistratiepunt  

-   Distributiepunt  

     Distributiepunten bieden ondersteuning voor configuraties die elk verschillende vereisten hebben. In sommige gevallen kan ondersteuning voor deze configuraties installatie niet alleen op servers, maar op de client-besturingssystemen. Zie voor meer informatie over de opties die beschikbaar voor distributiepunten zijn [inhoud en -infrastructuur voor System Center Configuration Manager beheert](../../../core/servers/deploy/configure/manage-content-and-content-infrastructure.md).  

-   Endpoint Protection-punt  

-   Inschrijvingspunt  

-   Proxypunt voor inschrijving  

-   Terugvalstatuspunt  

-   Beheerpunt

-   Reporting Services-punt  

-   Serviceverbindingspunt  

-   Sitedatabaseserver  

     Sitedatabaseservers worden niet ondersteund op een alleen-lezen domeincontroller (RODC). Zie [You may encounter problems when installing SQL Server on a domain controller (U kunt problemen ervaren wanneer u SQL Server installeert op een domeincontroller)](http://go.microsoft.com/fwlink/p/?LinkId=264856) in de Microsoft Knowledge Base voor meer informatie. Bovendien worden secundaire siteservers niet ondersteund op domeincontrollers.  

-   SMS_Provider  

-   Software-updatepunt  

-   Statusmigratiepunt  

## <a name="windows-server-2008-r2-with-sp1-x64-standard-enterprise-and-datacenter"></a>Windows Server 2008 R2 met SP1 (x 64): Standard, Enterprise en Datacenter  
 Windows Server 2008 R2 is nu in de uitgebreide ondersteuning en niet langer in algemene ondersteuning, zoals beschreven in [Microsoft Support Lifecycle](https://support.microsoft.com/lifecycle). Zie voor meer informatie over toekomstige ondersteuning voor deze besturingssystemen als sitesysteemservers met Configuration Manager [verwijderd en afgeschaft onderdelen voor System Center Configuration Manager](../../../core/plan-design/changes/removed-and-deprecated-features.md).  

 Beginnend met Configuration Manager versie 1702, dit besturingssysteem wordt niet ondersteund voor siteservers of de meeste sitesysteemrollen, maar ondersteunde is zichtbaar voor het statusmigratiepunt en distribueren sitesysteemrol (inclusief pull-distributiepunten, en voor PXE en multicast).
 
 Versies vóór 1702 blijven ondersteuning voor het gebruik ervan voor de volgende.


**Siteservers:**  

-   Centrale beheersite  

-   Primaire site  

-   Secundaire site  

**Sitesysteemservers:**  

-   Application Catalog-webservicepunt  

-   Application Catalog-websitepunt  

-   Asset Intelligence-synchronisatiepunt  

-   Certificaatregistratiepunt  

-   Distributiepunt  

     Distributiepunten bieden ondersteuning voor configuraties die elk verschillende vereisten hebben. In sommige gevallen kan ondersteuning voor deze configuraties installatie niet alleen op servers, maar op de client-besturingssystemen. Zie voor meer informatie over de opties die beschikbaar voor distributiepunten zijn [inhoud en -infrastructuur voor System Center Configuration Manager beheert](../../../core/servers/deploy/configure/manage-content-and-content-infrastructure.md).  

-   Endpoint Protection-punt  

-   Inschrijvingspunt  

-   Proxypunt voor inschrijving  

-   Terugvalstatuspunt  

-   Beheerpunt

-   Reporting Services-punt  

-   Serviceverbindingspunt  

-   Sitedatabaseserver  

     Sitedatabaseservers worden niet ondersteund op een alleen-lezen domeincontroller (RODC). Zie [You may encounter problems when installing SQL Server on a domain controller (U kunt problemen ervaren wanneer u SQL Server installeert op een domeincontroller)](http://go.microsoft.com/fwlink/p/?LinkId=264856) in de Microsoft Knowledge Base voor meer informatie. Bovendien worden secundaire siteservers niet ondersteund op domeincontrollers.  

-   SMS_Provider  

-   Software-updatepunt  

-   Statusmigratiepunt  

## <a name="windows-server-2008-with-sp2-x86-x64-standard-enterprise-and-datacenter"></a>WindowsServer 2008 SP2 (x 86, x 64): Standard, Enterprise en Datacenter  
 Windows Server 2008 is nu in de uitgebreide ondersteuning en niet langer in algemene ondersteuning, zoals beschreven in [Microsoft Support Lifecycle](https://support.microsoft.com/lifecycle). Zie voor meer informatie over toekomstige ondersteuning voor deze besturingssystemen als sitesysteemservers met Configuration Manager [verwijderd en afgeschaft onderdelen voor System Center Configuration Manager](../../../core/plan-design/changes/removed-and-deprecated-features.md).  

Dit besturingssysteem wordt niet ondersteund voor siteservers of sitesysteemrollen met uitzondering van het distributiepunt en het pull-distributiepunt. U kunt blijven gebruiken dit besturingssysteem als een distributiepunt tot buitengebruikstelling van deze ondersteuning is aangekondigd of dit besturingssysteem uitgebreide ondersteuning zijn verstreken. Zie voor meer informatie [installatie van System Center Configuration Manager CB en LTSB mislukt op Windows Server 2008](https://support.microsoft.com/help/4015095).

**Sitesysteemservers:**  
-   Distributiepunt  

    -   Distributiepunten voor dit besturingssysteem bieden geen ondersteuning voor Multicast.  

    -   Distributiepunten in dit besturingssysteem worden ondersteund voor PXE, maar bieden geen ondersteuning voor het opstarten van het netwerk van clientcomputers in EFI-modus. Clientcomputers met BIOS- of EFI-opstarten in de legacy-modus worden ondersteund.  

    -   Distributiepunten bieden ondersteuning voor configuraties die elk verschillende vereisten hebben. In sommige gevallen kan ondersteuning voor deze configuraties installatie niet alleen op servers, maar op de client-besturingssystemen. Zie voor meer informatie over de opties die beschikbaar voor distributiepunten zijn [inhoud en -infrastructuur voor System Center Configuration Manager beheert](../../../core/servers/deploy/configure/manage-content-and-content-infrastructure.md).  



## <a name="windows-10-x86-x64-pro-and-enterprise"></a>Windows 10 (x86, x64): Pro en Enterprise  
**Sitesysteemservers:**  

-   Distributiepunt  

    -   Distributiepunten voor dit besturingssysteem worden niet ondersteund voor PXE.  

    -   Distributiepunten voor deze besturingssysteemversie bieden geen ondersteuning voor Multicast.  

    -   Distributiepunten bieden ondersteuning voor configuraties die elk verschillende vereisten hebben. In sommige gevallen kan ondersteuning voor deze configuraties installatie niet alleen op servers, maar op de client-besturingssystemen. Zie voor meer informatie over de opties die beschikbaar voor distributiepunten zijn [inhoud en -infrastructuur voor System Center Configuration Manager beheert](../../../core/servers/deploy/configure/manage-content-and-content-infrastructure.md).  

## <a name="windows-81-x86-x64-professional-and-enterprise"></a>Windows 8.1 (x86, x64): Professional en Enterprise  
**Sitesysteemservers:**  

-   Distributiepunt  

    -   Distributiepunten voor dit besturingssysteem worden niet ondersteund voor PXE.  

    -   Distributiepunten voor deze besturingssysteemversie bieden geen ondersteuning voor Multicast.  

    -   Distributiepunten bieden ondersteuning voor configuraties die elk verschillende vereisten hebben. In sommige gevallen kan deze configuratie ondersteuning installatie niet alleen op servers, maar op de client-besturingssystemen. Zie voor meer informatie over de opties die beschikbaar voor distributiepunten zijn [inhoud en -infrastructuur voor System Center Configuration Manager beheert](../../../core/servers/deploy/configure/manage-content-and-content-infrastructure.md).  

## <a name="windows-8-x86-x64-professional-and-enterprise"></a>Windows 8 (x86, x64): Professional en Enterprise
**Sitesysteemservers:**  

-   Distributiepunt  

    -   Distributiepunten voor dit besturingssysteem worden niet ondersteund voor PXE.  

    -   Distributiepunten voor deze besturingssysteemversie bieden geen ondersteuning voor Multicast.  

    -   Distributiepunten bieden ondersteuning voor configuraties die elk verschillende vereisten hebben. In sommige gevallen kan ondersteuning voor deze configuraties installatie niet alleen op servers, maar op de client-besturingssystemen. Zie voor meer informatie over de opties die beschikbaar voor distributiepunten zijn [inhoud en -infrastructuur voor System Center Configuration Manager beheert](../../../core/servers/deploy/configure/manage-content-and-content-infrastructure.md).  

## <a name="windows-7-with-sp1-x86-x64-professional-enterprise-and-ultimate"></a>Windows 7 met SP1 (x 86, x 64): Professional, Enterprise en Ultimate  
**Sitesysteemservers:**  

-   Distributiepunt  

    -   Distributiepunten voor dit besturingssysteem worden niet ondersteund voor PXE.  

    -   Distributiepunten voor deze besturingssysteemversie bieden geen ondersteuning voor Multicast.  

    -   Distributiepunten bieden ondersteuning voor configuraties die elk verschillende vereisten hebben. In sommige gevallen kan ondersteuning voor deze configuraties installatie niet alleen op servers, maar op de client-besturingssystemen. Zie voor meer informatie over de opties die beschikbaar voor distributiepunten zijn [inhoud en -infrastructuur voor System Center Configuration Manager beheert](../../../core/servers/deploy/configure/manage-content-and-content-infrastructure.md).  


## <a name="the-server-core-installation-of-windows-server-2016"></a>De server core-installatie van Windows Server 2016
Vanaf versie 1606 met de hotfix rollup van KB3186654 (of de basislijn-versie van 1606, dat is gepubliceerd in oktober van 2016) dit besturingssysteem wordt ondersteund voor gebruik als een distributiepunt punt met de volgende beperkingen:  
  -   Alleen de x64-bits versie wordt ondersteund.
  -   Distributiepunten op dit besturingssysteem bieden geen ondersteuning voor PXE of Multicast.  


## <a name="the-server-core-installation-of-windows-server-2012-r2"></a>De Server Core-installatie van Windows Server 2012 R2  
 Naast de eerdere besturingssystemen die worden vermeld, wordt de server core-installatie van Windows Server 2012 R2 ondersteund voor gebruik als een distributiepunten met de volgende beperkingen:  

-   Alleen de x64-bits versie wordt ondersteund.

-   Distributiepunten op dit besturingssysteem bieden geen ondersteuning voor PXE of Multicast.  

## <a name="the-server-core-installation-of-windows-server-2012"></a>De Server Core-installatie van Windows Server 2012  
 Naast de eerdere besturingssystemen die worden vermeld, wordt ook de server core-installatie van Windows Server 2012 ondersteund voor gebruik als een distributiepunt punt met de volgende beperkingen:  

-   Alleen de 64-bits versie wordt ondersteund.  

-   Distributiepunten op dit besturingssysteem bieden geen ondersteuning voor PXE of Multicast.
