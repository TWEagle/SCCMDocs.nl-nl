---
title: Ondersteuning voor virtualisatie | Microsoft-documenten
description: Vereisten voor het installeren van System Center Configuration Manager-client en de sitesysteemrollen in een virtualisatieomgeving worden opgehaald.
ms.custom: na
ms.date: 1/12/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 1098e8c5-9676-4c2b-841b-ec88bd04e495
caps.latest.revision: 6
author: Brenduns
ms.author: brenduns
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 10192da2633555ab3bae60dbb1156d1926f9a4a0
ms.openlocfilehash: b49bd179da850cee35b2487a353bb1788df03d58
ms.contentlocale: nl-nl
ms.lasthandoff: 05/17/2017


---
# <a name="support-for-virtualization-environments-for-system-center-configuration-manager"></a>Ondersteuning voor virtualisatieomgevingen voor System Center Configuration Manager

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*

Configuration Manager ondersteunt de installatie van de client en de sitesysteemrollen op ondersteunde besturingssystemen die worden uitgevoerd als een virtuele machines in de virtualisatieomgevingen die in dit artikel worden vermeld. Deze ondersteuning geldt zelfs wanneer de host van de virtuele machine (virtualisatieomgeving) niet wordt ondersteund als een client of siteserver.  

 Bijvoorbeeld, als u Microsoft Hyper-V Server 2012 gebruiken voor het hosten van een virtuele machine die Windows Server 2012 wordt uitgevoerd, kunt u installeren de client of site systeemrollen op de virtuele machine (Windows Server 2012), maar niet op de host (Microsoft Hyper-V Server 2012).  

|Virtualisatieomgeving|  
|--------------------------------|  
|Windows Server 2008 R2|  
|Microsoft Hyper-V Server 2008 R2|  
|Windows Server 2012|  
|Microsoft Hyper-V Server 2012|  
|Windows Server 2012 R2|
|Windows Server 2016 <sup>(Zie *Opmerking 1*)</sup>|
|Microsoft Hyper-V Server 2016 <sup>(Zie *Opmerking 1*)|
-  *Houd er rekening mee 1*: Configuration Manager biedt geen ondersteuning voor [geneste virtualization](https://technet.microsoft.com/windows-server-docs/compute/hyper-v/what-s-new-in-hyper-v-on-windows#a-namebkmknestedanested-virtualization-new), dit is nieuw in Windows Server 2016.


 Elke virtuele computer die u gebruikt, moet voldoen aan of groter zijn dan de dezelfde hardware- en softwarevereisten die u voor een fysieke computer Configuration Manager gebruiken zou.  

 U kunt controleren of uw omgeving virtualization voor Configuration Manager met behulp van de Server Virtualization Validation Program en de Wizard online Virtualization programma ondersteuning beleid wordt ondersteund. Zie voor meer informatie over het programma Server Virtualization validatie [Windows Server Virtualization Validation Program](https://www.windowsservercatalog.com/svvp.aspx).  

> [!NOTE]  
>  Configuration Manager biedt geen ondersteuning voor Virtual PC of Virtual Server gastbesturingssystemen die worden uitgevoerd op Mac-computers.  

Configuration Manager kan geen virtuele machines beheren, tenzij ze online zijn. Een installatiekopie van een offline virtuele machine kan niet worden bijgewerkt en kan-inventarisatie wordt uitgevoerd met behulp van de Configuration Manager-client op de hostcomputer.  

Er wordt geen speciale aandacht besteed aan virtuele machines. Configuration Manager kan bijvoorbeeld niet bepalen of een update heeft opnieuw te worden toegepast op een installatiekopie van een virtuele machine als de virtuele machine is gestopt en opnieuw opgestart zonder op te slaan de status van de virtuele machine waarop de update is toegepast.  

##  <a name="bkmk_Azure"></a> Virtuele Microsoft Azure-machines  
 Configuration Manager kan worden uitgevoerd op virtuele machines in Azure net zoals deze wordt uitgevoerd op de lokale binnen uw fysieke bedrijfsnetwerk. U kunt de Configuration Manager gebruiken met virtuele Azure-machines in de volgende scenario's:  

-   **Scenario 1:** U kunt Configuration Manager uitvoeren op virtuele machine in Azure en deze gebruiken voor het beheren van clients die zijn geïnstalleerd op een andere virtuele machines in Azure.  

-   **Scenario 2:** U kunt Configuration Manager uitvoeren op virtuele machine in Azure en deze gebruiken voor het beheren van clients die niet worden uitgevoerd op Azure.  

-   **Scenario 3:** U kunt verschillende sitesysteemfuncties van Configuration Manager uitvoeren op virtuele machines in Azure tijdens het uitvoeren van andere functies in uw fysieke bedrijfsnetwerk (met de juiste netwerkverbinding voor communicaties).  

Dezelfde vereisten voor System Center Configuration Manager voor netwerken, ondersteunde configuraties en hardwarevereisten die van toepassing zijn voor het installeren van Configuration Manager op locatie op het fysieke netwerk zijn ook van toepassing op installatie op virtuele machines in Azure.  

Zie voor meer informatie [Configuration Manager op Azure--Veelgestelde vragen](/sccm/core/understand/configuration-manager-on-azure).

> [!IMPORTANT]  
>  Gelden dezelfde licentievereisten als lokale installaties in Configuration Manager-sites en clients die worden uitgevoerd op virtuele machines in Azure.  

