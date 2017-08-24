---
title: Vereisten voor verzamelingen | Microsoft Docs
description: Vereisten voor het gebruik van verzamelingen in System Center Configuration Manager worden opgehaald.
ms.custom: na
ms.date: 2/22/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: a53e4cf1-518a-4210-9c16-022c4261d2fe
caps.latest.revision: "7"
caps.handback.revision: "0"
author: andredm7
ms.author: andredm
manager: angrobe
ms.openlocfilehash: 41fc3eb20a7441939eb0dc80bc121c8f3ea322b2
ms.sourcegitcommit: 51fc48fb023f1e8d995c6c4eacfda7dbec4d0b2f
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 08/07/2017
---
# <a name="prerequisites-for-collections-in-system-center-configuration-manager"></a>Vereisten voor verzamelingen in System Center Configuration Manager

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*

Verzamelingen in System Center Configuration Manager bevatten alleen afhankelijkheden binnen het product.  

## <a name="configuration-manager-dependencies"></a>Configuration Manager-afhankelijkheden  

|Afhankelijkheid|Meer informatie|  
|----------------|----------------------|  
|Reporting Services-punt|De sitesysteemrol Reporting Services-punt moet zijn geïnstalleerd voordat u rapporten kunt uitvoeren voor verzamelingen. Zie [Rapportage in System Center Configuration Manager](../../../../core/servers/manage/reporting.md) voor meer informatie.|  
|Er moeten specifieke beveiligingsmachtigingen zijn verleend om verzamelingen te beheren|U moet over de volgende beveiligingsmachtigingen beschikken om instellingen voor naleving te beheren:<br /><br /> -Te maken en beheren van verzamelingen: **Maak**, **verwijderen**, **wijzigen**, **map wijzigen**, **Object verplaatsen**, **lezen** en **Resource lezen** voor de **verzameling** Object.<br /><br /> -Om verzamelingsinstellingen te beheren: **Wijzig de instelling verzameling** voor de **verzameling** Object.<br /><br /> De machtiging **Map wijzigen** is vereist voor alle verzamelingsmappen, met inbegrip van de hoofdmap.|  
