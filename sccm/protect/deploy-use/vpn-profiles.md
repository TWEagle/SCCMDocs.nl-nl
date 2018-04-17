---
title: VPN-profielen
titleSuffix: Configuration Manager
description: Informatie over het VPN-profielen in System Center Configuration Manager gebruiken voor het implementeren van VPN-instellingen voor gebruikers in uw organisatie.
ms.custom: na
ms.date: 04/10/2018
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
author: aczechowski
ms.author: aaroncz
manager: dougeby
ms.openlocfilehash: d30e7cc834f1693f2cbcf2db840d650421062a19
ms.sourcegitcommit: fb84bcb31d825f454785e3d9d8be669e00fe2b27
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/16/2018
---
# <a name="vpn-profiles-in-system-center-configuration-manager"></a>VPN-profielen in System Center Configuration Manager

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*

<!--1283610-->
Gebruiken om VPN-instellingen implementeren voor gebruikers in uw organisatie, VPN-profielen in Configuration Manager. Door het implementeren van deze instellingen minimaliseert u de eindgebruikersinspanningen die vereist zijn om verbinding te maken met resources op het bedrijfsnetwerk.  

 U wilt bijvoorbeeld alle Windows 10-apparaten met de instellingen die zijn vereist om verbinding met een bestandsshare op het bedrijfsnetwerk te configureren. U kunt een VPN-profiel maken met de instellingen nodig verbinding maken met het bedrijfsnetwerk. Vervolgens implementeert u dit profiel voor alle gebruikers die hebben apparaten met Windows 10. Deze gebruikers zien de VPN-verbinding in de lijst met beschikbare netwerken en kunnen moeiteloos verbinding.  

 Wanneer u een VPN-profiel maakt, kunt u een groot aantal beveiligingsinstellingen opnemen. Deze instellingen omvatten certificaten voor servervalidatie en clientverificatie die u met Configuration Manager-certificaatprofielen inricht. Zie voor meer informatie [Certificaatprofielen](introduction-to-certificate-profiles.md).  

> [!Note]  
> Configuration Manager deze optionele functie standaard niet ingeschakeld. Voordat u deze gebruikt, moet u deze functie inschakelen. Zie voor meer informatie [optionele functies van updates inschakelen](/sccm/core/servers/manage/install-in-console-updates#bkmk_options).<!--505213-->  


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
