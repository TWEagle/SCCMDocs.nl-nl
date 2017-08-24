---
title: VPN-profielen in System Center Configuration Manager | Microsoft Docs
description: Informatie over het VPN-profielen in System Center Configuration Manager gebruiken voor het implementeren van VPN-instellingen voor gebruikers in uw organisatie.
ms.custom: na
ms.date: 11/27/2016
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: c0f094f1-852e-4606-91db-97846d8f0772
caps.latest.revision: "6"
caps.handback.revision: "0"
author: arob98
ms.author: angrobe
manager: angrobe
ms.openlocfilehash: e07a80c1a59043b74cda7219f78c5fef66989ba8
ms.sourcegitcommit: 51fc48fb023f1e8d995c6c4eacfda7dbec4d0b2f
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 08/07/2017
---
# <a name="vpn-profiles-in-system-center-configuration-manager"></a>VPN-profielen in System Center Configuration Manager

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*


VPN-profielen in System Center Configuration Manager (ook wel bekend als Configuration Manager of SCCM) gebruiken voor het implementeren van VPN-instellingen voor gebruikers in uw organisatie. Door het implementeren van deze instellingen minimaliseert u de eindgebruikersinspanningen die vereist zijn om verbinding te maken met resources op het bedrijfsnetwerk.  

 Bijvoorbeeld, wilt u inrichten alle apparaten waarop het besturingssysteem Windows RT wordt uitgevoerd met de instellingen die zijn vereist om te verbinden met een bestandsshare op het bedrijfsnetwerk. U kunt een VPN-profiel met de instellingen die nodig zijn om verbinding maken met het bedrijfsnetwerk en vervolgens implementeert dit profiel voor alle gebruikers hebben apparaten met Windows RT in uw hiërarchie maken. Gebruikers van Windows RT-apparaten zien de VPN-verbinding in de lijst met beschikbare netwerken en kunnen verbinding maken met dit netwerk met een minimale inspanning.  

 Wanneer u een VPN-profiel maakt, kunt u een breed scala aan beveiligingsinstellingen, waaronder certificaten voor servervalidatie en clientverificatie die zijn ingericht met behulp van System Center Configuration Manager-certificaatprofielen kunt opnemen. Zie [Certificaatprofielen in System Center Configuration Manager](introduction-to-certificate-profiles.md) voor meer informatie over certificaatprofielen.  

 De volgende secties wordt uitgelegd welke apparaten die u met VPN-profielen configureren kunt als u van Configuration Manager gebruikmaakt.

 Zie [VPN-profielen op mobiele apparaten](/sccm/mdm/deploy-use/create-vpn-profiles) om te controleren van de apparaten die u configureren kunt wanneer u Configuration Manager met Microsoft Intune.  

## <a name="vpn-profiles-when-using-configuration-manager"></a>VPN-profielen wanneer u Configuration Manager  
 De volgende tabel beschrijft de VPN-profielen die u voor verschillende platforms configureren kunt.  

|Type verbinding|Windows 8.1|Windows RT|Windows RT 8.1|Windows 10|  
|---------------------|-----------------|----------------|--------------------|----------------|  
|**Cisco AnyConnect**|Nee|Nee|Nee|Nee|  
|**Pulse Secure**|Ja|Nee|Ja|Ja|  
|**F5 Edge Client**|Ja|Nee|Ja|Ja|  
|**Dell SonicWALL Mobile Connect**|Ja|Nee|Ja|Ja|  
|**Check Point Mobile VPN**|Ja|Nee|Ja|Ja|  
|**Microsoft SSL (SSTP)**|Ja|Ja|Ja|Nee|  
|**Microsoft Automatic**|Ja|Ja|Ja|Nee|  
|**IKEv2**|Ja|Ja|Ja|Nee|  
|**PPTP**|Ja|Ja|Ja|Nee|  
|**L2TP**|Ja|Ja|Ja|Nee|  

### <a name="next-steps"></a>Volgende stappen  
 Gebruik de volgende onderwerpen voor hulp bij het plannen, configureren, gebruiken en onderhouden van VPN-profielen in Configuration Manager.  

-   [Vereisten voor VPN-profielen in System Center Configuration Manager](../plan-design/prerequisites-for-wifi-vpn-profiles.md)  

-   [Beveiliging en privacy voor VPN-profielen in System Center Configuration Manager](../plan-design/security-and-privacy-for-wifi-vpn-profiles.md)
