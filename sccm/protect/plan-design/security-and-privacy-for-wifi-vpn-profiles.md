---
title: Wi-Fi en VPN-profiel beveiliging en privacy | Microsoft Docs
description: Meer informatie over de beveiliging aanbevolen procedures voor het beheren van Wi-Fi en VPN-profielen voor apparaten in System Center Configuration Manager.
ms.custom: na
ms.date: 12/28/2016
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: ef3ab519-9cf7-47fc-8831-d400e0e96df8
caps.latest.revision: "4"
caps.handback.revision: "0"
author: Nbigman
ms.author: nbigman
manager: angrobe
ms.openlocfilehash: 6d1d0a393a2ce614ae5f819475bd47b05e699b45
ms.sourcegitcommit: 51fc48fb023f1e8d995c6c4eacfda7dbec4d0b2f
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 08/07/2017
---
# <a name="security-and-privacy-for-wi-fi-and-vpn-profiles-in-system-center-configuration-manager"></a>Beveiliging en privacy voor Wi-Fi en VPN-profielen in System Center Configuration Manager

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*

##  <a name="security-best-practices-for-wi-fi--and-vpn-profiles"></a>Aanbevolen beveiligingsprocedures voor Wi-Fi en VPN-profielen  
 Gebruik de volgende aanbevolen beveiligingsprocedures wanneer u Wi-Fi en VPN-profielen voor apparaten beheert.  

|Aanbevolen beveiligingsprocedure|Meer informatie|  
|----------------------------|----------------------|  
|Kies indien mogelijk de veiligste opties die ondersteuning voor uw Wi-Fi en VPN-infrastructuur en clientbesturingssystemen biedt.|Wi-Fi en VPN-profielen bieden een handige methode om centraal te distribueren en beheren van Wi-Fi en VPN-instellingen die uw apparaten al ondersteunen. Configuration Manager voegt geen Wi-Fi of VPN-functionaliteit.<br /><br /> Bepaal, implementeer en volg alle 'best practice' beveiligingsprocedures die voor uw apparaten en infrastructuur worden aanbevolen.|  

## <a name="privacy-information-for-wi-fi-profiles"></a>Privacy-informatie voor Wi-Fi-profielen  
 Wi-Fi en VPN-profielen kunt u configureren dat clientapparaten verbinding maken met Wi-Fi en VPN-servers en te evalueren of die apparaten compatibel worden nadat de profielen zijn toegepast. De compatibiliteitsinformatie wordt door het beheerpunt naar de siteserver verzonden en deze informatie wordt opgeslagen in de sitedatabase. De informatie wordt versleuteld wanneer apparaten deze naar het beheerpunt verzenden, maar deze wordt niet in een versleutelde indeling opgeslagen in de sitedatabase. Informatie wordt bewaard in de database en wordt na negentig dagen verwijderd door de siteonderhoudstaak **Verouderde gegevens van Configuration Manager verwijderen** . Het standaardinterval voor verwijderen is 90 dagen, maar dit kunt u wijzigen. Er wordt geen compatibiliteitsinformatie naar Microsoft verzonden.  

 Standaard apparaten niet geëvalueerd Wi-Fi en VPN-profielen. Bovendien moet u de profielen configureren en implementeren voor gebruikers.  

 Bedenk wat uw privacyvereisten voordat u Wi-Fi of VPN-profielen configureert.  
