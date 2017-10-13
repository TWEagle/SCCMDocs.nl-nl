---
title: Aanbevolen procedures voor verzamelingen | Microsoft Docs
description: Aanbevolen procedures voor verzamelingen in System Center Configuration Manager worden opgehaald.
ms.custom: na
ms.date: 2/22/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 7a2abb79-9ae5-4a25-9e18-5dcf528de3bf
caps.latest.revision: "4"
caps.handback.revision: "0"
author: andredm7
ms.author: andredm
manager: angrobe
ms.openlocfilehash: fd62af3910c0745e0f1105417701b894e10cbbac
ms.sourcegitcommit: 51fc48fb023f1e8d995c6c4eacfda7dbec4d0b2f
ms.translationtype: HT
ms.contentlocale: nl-NL
ms.lasthandoff: 08/07/2017
---
# <a name="best-practices-for-collections-in-system-center-configuration-manager"></a>Aanbevolen procedures voor verzamelingen in System Center Configuration Manager

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*

Gebruik de volgende aanbevolen procedures voor verzamelingen in System Center Configuration Manager.  

## <a name="do-not-use-incremental-updates-for-a-large-number-of-collections"></a>Gebruik geen incrementele updates voor een groot aantal verzamelingen  
 Als u de optie **Incrementele updates gebruiken voor deze verzameling** activeert, kan deze configuratie beoordelingsvertragingen veroorzaken wanneer u deze voor veel verzamelingen inschakelt. De drempelwaarde is ongeveer 200 verzamelingen in uw hiërarchie. Het exacte aantal is afhankelijk van de volgende factoren:  

-   Het totale aantal verzamelingen  

-   De frequentie van nieuwe resources die worden toegevoegd en gewijzigd in de hiërarchie  

-   Het aantal clients in uw hiërarchie  

-   De complexiteit van de lidmaatschapsregels voor de verzamelingen in uw hiërarchie  

## <a name="make-sure-that-maintenance-windows-are-large-enough-to-deploy-critical-software-updates"></a>Zorg ervoor dat de onderhoudsvensters groot genoeg zijn om kritieke software-updates te implementeren  
 U kunt de onderhoudsvensters voor apparaatverzamelingen om de tijdstippen dat Configuration Manager software op deze apparaten installeren kunt te beperken. Als u het onderhoudsvenster te klein configureert, is het mogelijk dat de client kritieke software-updates niet kan installeren. Dit maakt de client kwetsbaar voor de aanval die wordt verholpen door de software-update.  
