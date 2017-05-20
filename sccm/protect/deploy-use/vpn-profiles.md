---
title: VPN-profielen in System Center Configuration Manager | Microsoft-documenten
description: Informatie over het VPN-profielen in System Center Configuration Manager gebruiken voor het implementeren van VPN-instellingen voor gebruikers in uw organisatie.
ms.custom: na
ms.date: 11/27/2016
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: c0f094f1-852e-4606-91db-97846d8f0772
caps.latest.revision: 6
caps.handback.revision: 0
author: arob98
ms.author: angrobe
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 199096db7a23fb14db98b95e75246ed254848ab7
ms.openlocfilehash: e07a80c1a59043b74cda7219f78c5fef66989ba8
ms.contentlocale: nl-nl
ms.lasthandoff: 05/17/2017


---
# <a name="vpn-profiles-in-system-center-configuration-manager"></a>VPN-profielen in System Center Configuration Manager

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*


VPN-profielen in System Center Configuration Manager (ook wel bekend als Configuration Manager of SCCM) gebruiken voor het implementeren van VPN-instellingen voor gebruikers in uw organisatie. Door het implementeren van deze instellingen minimaliseert u de eindgebruikersinspanningen die vereist zijn om verbinding te maken met resources op het bedrijfsnetwerk.  

 Bijvoorbeeld, wilt u inrichten alle apparaten waarop het Windows RT-besturingssysteem wordt uitgevoerd met de instellingen die zijn vereist om te verbinden met een bestandsshare op het bedrijfsnetwerk. U kunt een VPN-profiel met de instellingen die nodig zijn om te verbinden met het bedrijfsnetwerk en dit profiel vervolgens implementeren voor alle gebruikers met een apparaat met Windows RT in uw hiërarchie. Gebruikers van Windows RT-apparaten zien de VPN-verbinding in de lijst met beschikbare netwerken en verbinding kunnen maken met dit netwerk met een minimale inspanning.  

 Wanneer u een VPN-profiel maakt, kunt u een groot aantal beveiligingsinstellingen, waaronder certificaten voor servervalidatie en clientverificatie die zijn ingericht met behulp van System Center Configuration Manager-certificaatprofielen opnemen. Zie [Certificaatprofielen in System Center Configuration Manager](introduction-to-certificate-profiles.md) voor meer informatie over certificaatprofielen.  

 De volgende secties wordt uitgelegd welke apparaten kunt u als u van Configuration Manager gebruikmaakt configureren met VPN-profielen.

 Zie [VPN-profielen op mobiele apparaten](/sccm/mdm/deploy-use/create-vpn-profiles) te bekijken van de apparaten die u kunt configureren voor het gebruik van Configuration Manager met Microsoft Intune.  

## <a name="vpn-profiles-when-using-configuration-manager"></a>VPN-profielen bij gebruik van Configuration Manager  
 De volgende tabel beschrijft de VPN-profielen die u voor verschillende apparaatplatforms configureren kunt.  

|Type verbinding|Windows 8.1|Windows RT|Windows RT 8.1|Windows 10|  
|---------------------|-----------------|----------------|--------------------|----------------|  
|**Cisco AnyConnect**|Nee|Nee|Nee|Nee|  
|**Pulse beveiligen**|Ja|Nee|Ja|Ja|  
|**F5 Edge Client**|Ja|Nee|Ja|Ja|  
|**Dell SonicWALL Mobile Connect**|Ja|Nee|Ja|Ja|  
|**Mobiele VPN controlepunt**|Ja|Nee|Ja|Ja|  
|**Microsoft SSL (SSTP)**|Ja|Ja|Ja|Nee|  
|**Microsoft Automatic**|Ja|Ja|Ja|Nee|  
|**IKEv2**|Ja|Ja|Ja|Nee|  
|**PPTP**|Ja|Ja|Ja|Nee|  
|**L2TP**|Ja|Ja|Ja|Nee|  

### <a name="next-steps"></a>Volgende stappen  
 Gebruik de volgende onderwerpen om te plannen, configureren, gebruiken en onderhouden van VPN-profielen in Configuration Manager.  

-   [Vereisten voor VPN-profielen in System Center Configuration Manager](../plan-design/prerequisites-for-wifi-vpn-profiles.md)  

-   [Beveiliging en privacy voor VPN-profielen in System Center Configuration Manager](../plan-design/security-and-privacy-for-wifi-vpn-profiles.md)

