---
title: Controlelijst voor beheerders voor energiebeheer | Microsoft Docs
description: Gebruik de controlelijst voor beheerder voor hulp bij het plannen en implementeren van energiebeheer in System Center Configuration Manager.
ms.custom: na
ms.date: 10/06/2016
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 94e42cbe-9df8-4228-a04e-0ad7626180ca
caps.latest.revision: "6"
caps.handback.revision: "0"
author: arob98
ms.author: angrobe
manager: angrobe
ms.openlocfilehash: 8779acc39a5a0f8d5affef387d0ec242a59b4038
ms.sourcegitcommit: b438515490e04fb09c82a8af642d38e9a0605178
ms.translationtype: HT
ms.contentlocale: nl-NL
ms.lasthandoff: 09/15/2017
---
# <a name="administrator-checklist-for-power-management-in-system-center-configuration-manager"></a>Controlelijst voor beheerders voor energiebeheer in System Center Configuration Manager

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*

Deze controlelijst bevat de aanbevolen stappen voor het gebruik van System Center Configuration Manager-energiebeheer in uw organisatie.  

## <a name="configuring-power-management"></a>Energiebeheer configureren  
 Volg deze stappen om uw hiërarchie te configureren om energiebeheerinformatie te verzamelen bij clientcomputers.  

> [!IMPORTANT]  
>  Pas geen energiebeheerschema's toe op computers in uw hiërarchie tot u gegevens van energiebeheer van clientcomputers hebt verzameld en geanalyseerd. Als u nieuwe energiebeheerinstellingen op computers toepast zonder eerst de bestaande instellingen te controleren, kan dit leiden tot een toename van het energieverbruik.  

|Taak|Details|  
|----------|-------------|  
|Bekijk de energiebeheerconcepten in de Configuration Manager documentation library.|Zie [inleiding op Energiebeheer](introduction-to-power-management.md).|  
|Bekijk de energiebeheervereisten in de Configuration Manager documentation library.|Zie [vereisten voor energiebeheer](prerequisites-for-power-management.md).|  
|Bekijk de informatie over de aanbevolen procedures voor energiebeheer.|Zie [Best practices voor energiebeheer](best-practices-for-power-management.md).|  
|Configureer uw verzamelingen voor het energieverbruik van computers in uw omgeving beheren.|Gebruik de **verzamelen voor rapportage over basislijngegevens**, **verzamelen voor rapportage over basislijngegevens**, **verzameling van computers die niet geschikt voor energiebeheer**, **verzamelingen van computers waarop energiebeheerplannen worden toegepast**, **verzamelingen van computers waarop energiebeheerplannen worden toegepast**, en **verzamelingen van computers met Windows Server** voor het beheren van energie-instellingen voor computers in uw hiërarchie. U kunt meerdere verzamelingen maken en verschillende energiebeheerschema's toepassen op elke verzameling.|  
|Energiebeheer inschakelen.|Voordat u energiebeheer kunt gaan gebruiken, moet u dit inschakelen en de vereiste clientinstellingen configureren. Zie voor meer informatie [energiebeheer configureren](configuring-power-management.md).|  
|Energiebeheerinformatie verzamelen bij clientcomputers.|Gegevens van energiebeheer is gerapporteerd door clients via hardware-inventaris van Configuration Manager. Afhankelijk van de hardware-inventarisplanning die u hebt geconfigureerd, kan het enige tijd duren om inventarisgegevens bij alle clientcomputers op te vragen.|  

## <a name="monitoring-and-planning-phase"></a>Bewaking- en planningsfase  

|Taak|Details|  
|----------|-------------|  
|Voer het rapport **Computeractiviteit**uit.|In het rapport **Computeractiviteit** wordt een grafiek weergegeven met bewakings-, computer- en gebruikersactiviteit voor een opgegeven verzameling gedurende een opgegeven periode. Dit rapport is gekoppeld aan het rapport **Details van computeractiviteit** waarin de slaap- en waakmogelijkheden van computers in de opgegeven verzameling worden weergegeven. Zie voor meer informatie [bewaken en plannen voor energiebeheer](monitor-and-plan-for-power-management.md).|  
|Voer het rapport **Energieverbruik** of **Energieverbruik per dag**uit.|In het rapport **Energieverbruik** en het rapport **Energieverbruik per dag** worden het totale maandelijkse energieverbruik in kilowatt per uur (kWh) weergegeven voor een opgegeven verzameling gedurende een opgegeven periode. Zie voor meer informatie [bewaken en plannen voor energiebeheer](monitor-and-plan-for-power-management.md).|  
|Voer het rapport **Uitwerking op milieu** of  **Uitwerking op het milieu op dag**uit.|In de rapporten **Uitwerking op milieu** en **Uitwerking op milieu op dag** wordt een grafiek met kooldioxide-uitstoot (CO2) weergegeven die wordt bespaard door een opgegeven verzameling van computers gedurende een opgegeven periode. Zie voor meer informatie [bewaken en plannen voor energiebeheer](monitor-and-plan-for-power-management.md).|  
|Voer het rapport **Energiekosten** of **Energiekosten op dag**uit.|In de rapporten **Energiekosten** en **Energiekosten op dag** worden de totale energieverbruikskosten weergegeven voor een opgegeven periode. Zie voor meer informatie [bewaken en plannen voor energiebeheer](monitor-and-plan-for-power-management.md).|  
|Voer het rapport **Stroomvoorzieningsmogelijkheden**uit.|Het rapport **Stroomvoorzieningsmogelijkheden** geeft de energiebeheermogelijkheden van computers in de opgegeven verzameling weer. Zie voor meer informatie [bewaken en plannen voor energiebeheer](monitor-and-plan-for-power-management.md).|  
|Voer het rapport **Energie-instellingen**uit.|Het rapport **Energie-instellingen** bevat een samengevoegde lijst met de huidige energie-instellingen die door computers in een opgegeven verzameling worden gebruikt. Zie voor meer informatie [bewaken en plannen voor energiebeheer](monitor-and-plan-for-power-management.md).|  
|Alle vereiste verzamelingen van computers uitsluiten van energiebeheer.|Zie [energiebeheer configureren](configuring-power-management.md).|  

> [!IMPORTANT]  
>  Zorg ervoor dat u de rapporten met energiebeheergegevens opslaat die tijdens de bewakings- en planningsfase zijn gegenereerd. U kunt deze gegevens vergelijken met energiebeheergegevens die zijn gegenereerd tijdens de afdwingings- en nalevingsfase, zodat u het energieverbruik, de energiekosten en milieubesparingen kunt beoordelen die horen bij het toepassen van een energieplan op computers in uw hiërarchie.  

## <a name="enforcement-phase"></a>Afdwingingsfase  

|Taak|Details|  
|----------|-------------|  
|Bestaande energiebeheerschema's selecteren of nieuwe energiebeheerschema's maken voor verzamelingen van computers in uw organisatie.|Zie [maken en energiebeheerschema's toepassen](create-and-apply-power-plans.md).|  
|Deze energiebeheerschema's toepassen op computers.|Zie [maken en energiebeheerschema's toepassen](create-and-apply-power-plans.md).|  

## <a name="compliance-phase"></a>Nalevingsfase  

|Taak|Details|  
|----------|-------------|  
|Voer het rapport **Computeractiviteit**uit.|In het rapport **Computeractiviteit** wordt een grafiek weergegeven met bewakings-, computer- en gebruikersactiviteit voor een opgegeven verzameling gedurende een opgegeven periode. Dit rapport is gekoppeld aan het rapport **Details van computeractiviteit** waarin de slaap- en waakmogelijkheden van computers in de opgegeven verzameling worden weergegeven. Zie voor meer informatie [bewaken en plannen voor energiebeheer](monitor-and-plan-for-power-management.md).|  
|Voer het rapport **Energieverbruik** of **Energieverbruik per dag**uit.|In het rapport **Energieverbruik** en het rapport **Energieverbruik per dag** worden het totale maandelijkse energieverbruik in kilowatt per uur (kWh) weergegeven voor een opgegeven verzameling gedurende een opgegeven periode. Zie voor meer informatie [bewaken en plannen voor energiebeheer](monitor-and-plan-for-power-management.md).|  
|Voer het rapport **Uitwerking op milieu** of **Uitwerking op het milieu op dag**uit.|In de rapporten **Uitwerking op milieu** en **Uitwerking op milieu op dag** wordt een grafiek met kooldioxide-uitstoot (CO2) weergegeven die wordt bespaard door een opgegeven verzameling van computers gedurende een opgegeven periode. Zie voor meer informatie [bewaken en plannen voor energiebeheer](monitor-and-plan-for-power-management.md).|  
|Voer het rapport **Energiekosten** of **Energiekosten op dag**uit.|In de rapporten **Energiekosten** en **Energiekosten op dag** worden de totale energieverbruikskosten weergegeven voor een opgegeven periode. Zie voor meer informatie [bewaken en plannen voor energiebeheer](monitor-and-plan-for-power-management.md).|  

## <a name="troubleshooting"></a>Probleemoplossing  

|Taak|Details|  
|----------|-------------|  
|Als de computers in uw hiërarchie niet zijn overgeschakeld op de slaapstand of sluimerstand, voert u het **slapeloosheidsrapport** uit om mogelijke oorzaken weer te geven.|Het **slapeloosheidsrapport** geeft een lijst met algemene oorzaken weer die verhinderen dat computers naar de slaapstand of sluimerstand overschakelen, evenals het aantal computers dat hierdoor gedurende een bepaalde periode is getroffen. Zie voor meer informatie [bewaken en plannen voor energiebeheer](monitor-and-plan-for-power-management.md).|  
|Als er meerdere energiebeheerschema's worden toegepast op een computer, wordt het minst beperkende energiebeheerschema toegepast. Voer het rapport **Computers met meerdere energiebeheerschema's** uit om de computers te zien waarop meerdere energiebeheerschema's worden toegepast.|Zie **Computers met meerdere energiebeheerschema's** in [bewaken en plannen voor energiebeheer](monitor-and-plan-for-power-management.md).|  
