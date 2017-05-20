---
title: Beveiliging en privacy voor energiebeheer | Microsoft-documenten
description: Beveiliging en privacy-informatie voor energiebeheer in System Center Configuration Manager ophalen.
ms.custom: na
ms.date: 04/23/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 469ff35f-59a1-484d-902b-107dd6070baf
caps.latest.revision: 5
caps.handback.revision: 0
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 690d03d9c8c49a815bd318df549d7401a855bc5d
ms.openlocfilehash: 94d5418c364c318dba92dc9f9066f54d1130aa34
ms.contentlocale: nl-nl
ms.lasthandoff: 05/17/2017


---
# <a name="security-and-privacy-for-power-management-in-system-center-configuration-manager"></a>Beveiliging en privacy voor energiebeheer in System Center Configuration Manager

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*

Deze sectie bevat informatie over de beveiliging en privacy voor energiebeheer in System Center Configuration Manager.  

## <a name="security-best-practices-for-power-management"></a>Aanbevolen beveiligingsprocedures voor energiebeheer  
 Er zijn geen aanbevolen beveiligingsprocedures voor energiebeheer.  

## <a name="privacy-information-for-power-management"></a>Privacyinformatie voor energiebeheer  
 Energiebeheer maakt gebruik van functies die zijn ingebouwd in Windows om tijdens en buiten kantooruren energieverbruik te controleren en energie-instellingen toe te passen op computers. Configuration Manager verzamelt informatie over het gebruik van power van computers, waaronder gegevens over wanneer een gebruiker een computer gebruikt. Hoewel Configuration Manager energieverbruik voor een verzameling, in plaats voor elke computer controleert, is een verzameling mag slechts één computer. Energiebeheer is standaard niet ingeschakeld en moet worden geconfigureerd door een beheerder.  

 De informatie over het gebruik van de stroom is opgeslagen in de Configuration Manager-database en wordt niet naar Microsoft verzonden. Gedetailleerde informatie wordt 31 dagen in de database bewaard en een samenvatting van de gegevens wordt 13 maanden bewaard. U kunt de verwijderingstermijn niet configureren.  

 Voordat u energiebeheer configureert, moet u rekening houden met uw privacyvereisten.  

