---
title: Ondersteuning voor het virtualisatie
titleSuffix: Configuration Manager
description: Vereisten voor het installeren van System Center Configuration Manager-client en de sitesysteemrollen in een virtualisatieomgeving ophalen.
ms.custom: na
ms.date: 1/12/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 1098e8c5-9676-4c2b-841b-ec88bd04e495
caps.latest.revision: "6"
author: Brenduns
ms.author: brenduns
manager: angrobe
ms.openlocfilehash: 25806078d0133c188918f788c543fa86db5b3be8
ms.sourcegitcommit: c236214b2fcc13dae7bad96d7fb33f692868191d
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/12/2017
---
# <a name="support-for-virtualization-environments-for-system-center-configuration-manager"></a>Ondersteuning voor virtualisatieomgevingen voor System Center Configuration Manager

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*

Configuration Manager ondersteunt de installatie van de client en sitesysteemrollen op ondersteunde besturingssystemen die worden uitgevoerd als een virtuele machines in de virtualisatieomgevingen die in dit artikel worden vermeld. Deze ondersteuning geldt zelfs wanneer de host van de virtuele machine (virtualisatieomgeving) niet wordt ondersteund als een client of siteserver.  

 Bijvoorbeeld, als u Microsoft Hyper-V Server 2012 gebruikt voor het hosten van een virtuele machine met Windows Server 2012 wordt uitgevoerd, kunt u de client of de sitesysteemrollen op de virtuele machine (Windows Server 2012), maar niet op de host (Microsoft Hyper-V Server 2012).  

|Virtualisatieomgeving|  
|--------------------------------|  
|Windows Server 2008 R2|  
|Microsoft Hyper-V Server 2008 R2|  
|Windows Server 2012|  
|Microsoft Hyper-V Server 2012|  
|Windows Server 2012 R2|
|Windows Server 2016 <sup>(Zie *Opmerking 1*)</sup>|
|Microsoft Hyper-V Server 2016 <sup>(Zie *Opmerking 1*)|
-  *Opmerking 1*: Configuration Manager biedt geen ondersteuning voor [geneste virtualisatie](https://technet.microsoft.com/windows-server-docs/compute/hyper-v/what-s-new-in-hyper-v-on-windows#a-namebkmknestedanested-virtualization-new), die is er nieuw in Windows Server 2016.


 Elke virtuele computer die u gebruikt, moet voldoen aan of groter zijn dan de dezelfde hardware- en softwarevereisten die u voor een fysieke computer in de Configuration Manager gebruiken wilt.  

 U kunt controleren of uw virtualisatieomgeving wordt ondersteund voor Configuration Manager met behulp van de Server Virtualization Validation Program en de Wizard online virtualisatie programma ondersteuning beleid. Zie voor meer informatie over het Server Virtualization Validation Program [Windows Server Virtualization Validation Program](https://www.windowsservercatalog.com/svvp.aspx).  

> [!NOTE]  
>  Configuration Manager biedt geen ondersteuning voor Virtual PC of Virtual Server gastbesturingssystemen die worden uitgevoerd op de Mac-computers.  

Configuration Manager kan geen virtuele machines beheren, tenzij deze online zijn. Een installatiekopie van een offline virtuele machine kan niet worden bijgewerkt. ook kan inventaris worden verzameld met behulp van de Configuration Manager-client op de hostcomputer.  

Er wordt geen speciale aandacht besteed aan virtuele machines. Configuration Manager kan bijvoorbeeld niet bepalen of een update heeft opnieuw moet worden toegepast op de installatiekopie van een virtuele machine als de virtuele machine is gestopt en opnieuw opgestart zonder op te slaan de status van de virtuele machine waarop de update is toegepast.  

##  <a name="bkmk_Azure"></a> Virtuele Microsoft Azure-machines  
 Net als deze wordt uitgevoerd op de lokale Configuration Manager kunt uitvoeren op virtuele machines in Azure binnen uw fysieke bedrijfsnetwerk. U kunt de Configuration Manager gebruiken met Azure virtuele machines in de volgende scenario's:  

-   **Scenario 1:** U kunt de Configuration Manager uitvoeren op Azure een virtuele machine en gebruiken voor het beheren van clients die zijn geïnstalleerd op andere virtuele machines in Azure.  

-   **Scenario 2:** U kunt de Configuration Manager uitvoeren op Azure een virtuele machine en gebruiken voor het beheren van clients die niet worden uitgevoerd op Azure.  

-   **Scenario 3:** U kunt andere Configuration Manager-sitesysteemrollen uitvoeren op Azure virtuele machines tegelijkertijd andere rollen uitvoeren in uw fysieke bedrijfsnetwerk (met de juiste netwerkverbinding voor communicatie).  

Dezelfde vereisten voor netwerken, ondersteunde configuraties en hardwarevereisten die van toepassing aan het installeren van Configuration Manager lokaal op uw fysieke bedrijfsnetwerk System Center Configuration Manager zijn ook van toepassing op installatie op virtuele machines in Azure.  

Zie voor meer informatie [Configuration Manager in Azure--Frequently Asked Questions](/sccm/core/understand/configuration-manager-on-azure).

> [!IMPORTANT]  
>  Configuration Manager-sites en clients die worden uitgevoerd op virtuele machines in Azure zijn onderworpen aan dezelfde licentievereisten als on-premises installaties.  
