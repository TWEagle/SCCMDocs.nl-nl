---
title: Beveiliging en privacy voor energiebeheer
titleSuffix: Configuration Manager
description: Beveiliging en privacy-informatie ophalen voor energiebeheer in System Center Configuration Manager.
ms.custom: na
ms.date: 04/23/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 469ff35f-59a1-484d-902b-107dd6070baf
caps.latest.revision: "5"
caps.handback.revision: "0"
author: arob98
ms.author: angrobe
manager: angrobe
ms.openlocfilehash: 5de0ed261b3069306992eeddb4b71b3fe22f197c
ms.sourcegitcommit: c236214b2fcc13dae7bad96d7fb33f692868191d
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/12/2017
---
# <a name="security-and-privacy-for-power-management-in-system-center-configuration-manager"></a>Beveiliging en privacy voor energiebeheer in System Center Configuration Manager

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*

Deze sectie bevat informatie over de beveiliging en privacy voor energiebeheer in System Center Configuration Manager.  

## <a name="security-best-practices-for-power-management"></a>Aanbevolen beveiligingsprocedures voor energiebeheer  
 Er zijn geen aanbevolen beveiligingsprocedures voor energiebeheer.  

## <a name="privacy-information-for-power-management"></a>Privacyinformatie voor energiebeheer  
 Energiebeheer maakt gebruik van functies die zijn ingebouwd in Windows om tijdens en buiten kantooruren energieverbruik te controleren en energie-instellingen toe te passen op computers. Configuration Manager verzamelt informatie over energiegebruik van computers, waaronder gegevens over wanneer een gebruiker een computer wordt gebruikt. Een verzameling kan Configuration Manager controleert stroomverbruik voor een verzameling in plaats van voor elke computer, slechts één computer bevatten. Energiebeheer is standaard niet ingeschakeld en moet worden geconfigureerd door een beheerder.  

 De informatie over energiegebruik wordt opgeslagen in de Configuration Manager-database en wordt niet naar Microsoft verzonden. Gedetailleerde informatie wordt 31 dagen in de database bewaard en een samenvatting van de gegevens wordt 13 maanden bewaard. U kunt de verwijderingstermijn niet configureren.  

 Voordat u energiebeheer configureert, moet u rekening houden met uw privacyvereisten.  
