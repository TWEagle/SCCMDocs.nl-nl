---
title: Best practices voor energiebeheer | Microsoft Docs
description: Best practices voor energiebeheer in System Center Configuration Manager worden opgehaald.
ms.custom: na
ms.date: 10/06/2016
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 9f7142e1-c972-4384-853b-2da1568cb3e3
caps.latest.revision: "5"
caps.handback.revision: "0"
author: arob98
ms.author: angrobe
manager: angrobe
ms.openlocfilehash: 68b8be80152da52be427a3d2fdbf5c466029add6
ms.sourcegitcommit: f6a428a8db7145affa388f59e0ad880bdfcf17b5
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 09/14/2017
---
# <a name="best-practices-for-power-management-in-system-center-configuration-manager"></a>Best practices voor energiebeheer in System Center Configuration Manager

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*

Gebruik de volgende best practices voor energiebeheer in System Center Configuration Manager.  

## <a name="perform-the-monitoring-phase-at-a-representative-time"></a>De controlefase op een representatief moment uitvoeren  
 De controlefase van energiebeheer biedt u informatie over het energieverbruik, de activiteit, de mogelijkheden voor energiebeheer en de uitwerking van computers in uw organisatie op het milieu. Zorg ervoor dat u een representatief moment kiest voor het uitvoeren van de controlefase. Bijvoorbeeld: het uitvoeren van de controlefase voor een feestdag geeft geen realistisch rapport van het energieverbruik van computers.  

## <a name="create-a-control-collection-of-computers-with-no-power-plans-applied"></a>Een controleverzameling maken van computers waarop geen energiebeheerschema's zijn toegepast  
 Maak twee verzamelingen van computers om de gevolgen te controleren van het toepassen van energiebeheerschema's op computers. De eerste verzameling moet het merendeel van de computers bevatten waarop u de energie-instellingen wilt toepassen. De andere verzameling (de controleverzameling) moet de overige computers bevatten. Pas het vereiste energiebeheerschema toe op de verzameling met de meeste computers. Vervolgens kunt u rapporten uitvoeren om de energiekosten, het energieverbruik en de uitwerking op milieu te vergelijken voor de computers waarop u energie-instellingen hebt toegepast met de controleverzameling waarop u geen energie-instellingen hebt toegepast.  

## <a name="run-the-power-settings-report-before-you-apply-a-power-management-plan"></a>Het rapport Energie-instellingen uitvoeren voordat u een energiebeheerschema toepast  
 Voordat u een energiebeheerschema toepast op een verzameling computers, voert u het rapport **Energie-instellingen** uit voor inzicht in de energiebeheerinstellingen die al zijn geconfigureerd voor computers in de verzameling. Als u nieuwe energiebeheerinstellingen op computers toepast zonder eerst de bestaande instellingen te controleren, kan dit leiden tot een toename van het energieverbruik.  

## <a name="exclude-servers-from-power-management"></a>Servers uitsluiten van energiebeheer  
 Energiebeheer voor computers met Windows Server wordt niet ondersteund (er worden wel gegevens over energieverbruik verzameld). Zorg dat u servers aan een verzameling toevoegt en van energiebeheer uitsluit.  

## <a name="exclude-computers-that-you-do-not-want-to-manage"></a>Computers die u niet wilt beheren uitsluiten  
 Als u computers hebt die u niet wilt beheren met energiebeheer, voegt u deze aan een verzameling toe en zorgt u ervoor dat de verzameling is uitgesloten van energiebeheer.  

 Voorbeelden van computers die u mogelijk wilt uitsluiten van energiebeheer zijn:  

-   Computers die moeten blijven ingeschakeld.  

-   Computers waarmee gebruikers verbinding moeten maken via een Extern bureaublad-verbinding.  

-   Computers die energiebeheer niet kunnen gebruiken.  

-   Computers waaraan de sitesysteemrol Distributiepunt is toegewezen.  

-   Openbare computers zoals 'kioskcomputers', informatieschermen of bewakingsconsoles, waarbij de computer en de monitor altijd moeten blijven ingeschakeld.  

 Zie voor meer informatie [energiebeheer configureren in System Center Configuration Manager](../../../../core/clients/manage/power/configuring-power-management.md).  

## <a name="first-apply-power-plans-to-a-test-collection-of-computers"></a>Pas eerst energiebeheerschema's toe op een testverzameling computers  
 Test het effect van het toepassen van een energiebeheerschema op een testverzameling computers voordat u het energiebeheerschema op een grotere verzameling computers toepast.  

 Energie-instellingen die worden toegepast op computers met Windows XP of Windows Server 2003 worden niet hersteld naar de oorspronkelijke waarden, zelfs niet als u de computer van energiebeheer uitsluit. In hogere versies van Windows worden bij het uitsluiten van een computer voor energiebeheer alle energie-instellingen teruggezet naar de oorspronkelijke waarden. Het is niet mogelijk oorspronkelijke waarden van afzonderlijke energie-instellingen te herstellen.  

## <a name="apply-power-plan-settings-individually"></a>Energiebeheerschema-instellingen afzonderlijk toepassen  
 Controleer het effect van het toepassen van elke energie-instelling voordat u de volgende toepast zodat elke instelling het vereiste effect heeft. Zie voor meer informatie over energiebeheerschema-instellingen, [instellingen voor beschikbare energiebeheerschema's](../../../../core/clients/manage/power/create-and-apply-power-plans.md#BKMK_Plans) in het onderwerp [maken en toepassen van energiebeheerschema's in System Center Configuration Manager](../../../../core/clients/manage/power/create-and-apply-power-plans.md).  

## <a name="regularly-monitor-computers-to-see-if-they-have-multiple-power-plans-applied"></a>Regelmatig controleren of op computers meerdere energiebeheerschema's zijn toegepast  
 Energiebeheer bevat een rapport met computers waarop meer dan één energiebeheerschema is toegepast.  

 Als een computer lid is van meerdere verzamelingen, die elk verschillende energiebeheerschema’s toepassen, worden de volgende acties ondernomen:  

-   Energiebeheerschema: Als u meerdere waarden voor energie-instellingen worden toegepast op een computer, wordt de minst beperkende waarde gebruikt.  

-   Activeringstijd: Als er meerdere activeringstijden worden toegepast op een desktopcomputer, wordt de tijd die het dichtst bij middernacht wordt gebruikt.  

     Zie voor meer informatie [Computers met meerdere energiebeheerschema's](../../../../core/clients/manage/power/monitor-and-plan-for-power-management.md#BKMK_Multiple) in het onderwerp [bewaken en plannen voor energiebeheer in System Center Configuration Manager](../../../../core/clients/manage/power/monitor-and-plan-for-power-management.md). Zie voor meer informatie over het omzetten van conflicten met Energiebeheer [maken en toepassen van energiebeheerschema's in System Center Configuration Manager](../../../../core/clients/manage/power/create-and-apply-power-plans.md).  

## <a name="save-or-export-power-management-information-during-the-monitoring-and-planning-phase-of-power-management"></a>Energiebeheergegevens opslaan of exporteren tijdens de bewakings- en planningsfase van energiebeheer  
 Informatie over energiebeheer die wordt gebruikt door dagelijkse rapporten wordt bewaard in de Configuration Manager-sitedatabase 31 dagen.  

 Informatie over energiebeheer die wordt gebruikt door maandelijkse rapporten wordt 13 maanden bewaard in de Configuration Manager-sitedatabase.  

 Wanneer u rapporten tijdens de bewaking planning- en nalevingsfase van energiebeheer uitvoeren, opslaan of exporteren van de resultaten uit rapporten die u wilt behouden de gegevens voor later te vergelijken als ze later zijn verwijderd door Configuration Manager.  
