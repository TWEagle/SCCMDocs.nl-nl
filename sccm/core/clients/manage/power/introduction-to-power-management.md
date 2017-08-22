---
title: Inleiding op Energiebeheer | Microsoft Docs
description: Maak kennis met energiebeheer in System Center Configuration Manager.
ms.custom: na
ms.date: 10/06/2016
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 3ddff2a7-99eb-4ef8-b969-f3f7f24053db
caps.latest.revision: "4"
caps.handback.revision: "0"
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.openlocfilehash: f46c9479021c814b1102d72c7d493f21a7243bf1
ms.sourcegitcommit: 51fc48fb023f1e8d995c6c4eacfda7dbec4d0b2f
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 08/07/2017
---
# <a name="introduction-to-power-management-in-system-center-configuration-manager"></a>Inleiding op Energiebeheer in System Center Configuration Manager

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*

Energiebeheer in System Center Configuration Manager heeft betrekking op de behoeften van veel organisaties hebben om te controleren en het energieverbruik van hun computers verminderen. Hierbij wordt gebruikgemaakt van de ingebouwde Windows-functies voor energiebeheer om relevante en consistente instellingen op computers in de organisatie toe te passen. U kunt tijdens kantooruren en buiten kantooruren verschillende energie-instellingen toepassen op computers. Het is bijvoorbeeld mogelijk dat u buiten kantooruren een meer beperkend energiebeheerschema op computers wilt toepassen. Wanneer computers altijd ingeschakeld moeten blijven, kunt u voorkomen dat energiebeheerinstellingen worden toegepast.  

 Energiebeheer in Configuration Manager bevat diverse rapporten waarmee u kunt analyseren power gebruiks- en energie-instellingen in uw organisatie. U kunt de rapporten ook gebruiken om problemen met energiebeheer op te lossen.  

 Zie voor een gedetailleerde werkstroom over het configureren en gebruiken van energiebeheer [controlelijst voor beheerders voor energiebeheer in System Center Configuration Manager](../../../../core/clients/manage/power/administrator-checklist-for-power-management.md).  

> [!IMPORTANT]  
>  Configuration Manager-energiebeheer wordt niet ondersteund op virtuele machines. U kunt geen energiebeheerschema's toepassen op virtuele machines en u kunt hiervoor geen energiegegevens rapporteren.  

## <a name="the-power-management-workflow"></a>De werkstroom voor energiebeheer  
 Gebruik de volgende drie fasen plannen en implementeren van energiebeheer in Configuration Manager.  

### <a name="monitoring-and-planning-phase"></a>Bewaking- en planningsfase  
 Energiebeheer maakt gebruik van hardware-inventaris van Configuration Manager voor het verzamelen van gegevens over gebruik en power computerinstellingen voor computers in de site. U kunt verschillende rapporten gebruiken om deze gegevens te analyseren en de optimale energiebeheerinstellingen voor computers te bepalen. Tijdens de bewakings- en planningsfase van de werkstroom voor energiebeheer kunt u bijvoorbeeld verzamelingen maken die zijn gebaseerd op de gegevens die zijn opgenomen in het rapport **Stroomvoorzieningsmogelijkheden** en die gegevens gebruiken om de computers te identificeren die niet geschikt zijn voor energiebeheer. Vervolgens kunt u deze computers uitsluiten van energiebeheer.  

> [!IMPORTANT]  
>  Pas geen energiebeheerschema's op uw computers toe voordat u de energiegegevens van clientcomputers hebt verzameld en geanalyseerd. Als u nieuwe energiebeheerinstellingen op computers toepast zonder eerst de bestaande instellingen te controleren, kan dit leiden tot een toename van het energieverbruik.  

### <a name="enforcement-phase"></a>Afdwingingsfase  
 Met energiebeheer kunt u energiebeheerschema's maken die u op verzamelingen computers in uw site kunt toepassen. Met deze energiebeheerschema's worden Windows-instellingen voor energiebeheer geconfigureerd op computers. U kunt de energiebeheerschema's die geleverd met Configuration Manager worden gebruiken of u kunt uw eigen aangepaste energiebeheerschema's configureren. U kunt de energiegegevens die tijdens de bewakings- en planningsfase zijn verzameld, gebruiken als basislijn om energiebesparingen te evalueren nadat u een energiebeheerschema op computers hebt toegepast. Zie voor meer informatie [controlelijst voor beheerders voor energiebeheer in System Center Configuration Manager](../../../../core/clients/manage/power/administrator-checklist-for-power-management.md).  

### <a name="compliance-phase"></a>Nalevingsfase  
 In de nalevingsfase kunt u rapporten uitvoeren om het energieverbruik en energiebesparingskosten in uw organisatie te evalueren. U kunt ook rapporten die worden beschreven de verbeteringen in de hoeveelheid CO2 gegenereerd door computers uitvoeren. Er zijn ook rapporten beschikbaar waarmee u kunt controleren of energie-instellingen correct zijn toegepast op computers en u problemen kunt oplossen met de functie voor energiebeheer.  
