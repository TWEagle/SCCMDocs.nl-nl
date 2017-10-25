---
title: 'Hardware-inventarisatie: Configuration Manager | Microsoft Docs'
description: Maak kennis met de hardware-inventaris in System Center Configuration Manager.
ms.custom: na
ms.date: 02/22/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: configmgr-other
ms.tgt_pltfrm: na
ms.topic: get-started-article
ms.assetid: 3969952e-9d05-49c9-82a2-e7e90ccef511
caps.latest.revision: "6"
caps.handback.revision: "0"
author: andredm7
ms.author: andredm
manager: angrobe
ms.openlocfilehash: c64f0b42bff25e8e91cf9101d6fbb538634eab15
ms.sourcegitcommit: 51fc48fb023f1e8d995c6c4eacfda7dbec4d0b2f
ms.translationtype: HT
ms.contentlocale: nl-NL
ms.lasthandoff: 08/07/2017
---
# <a name="introduction-to-hardware-inventory-in-system-center-configuration-manager"></a>Inleiding op hardware-inventarisatie in System Center Configuration Manager

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*

Hardware-inventarisatie in System Center Configuration Manager voor het verzamelen van informatie over de hardwareconfiguratie van clientapparaten in uw organisatie gebruiken. Als u de hardware-inventaris wilt verzamelen, moet de instelling **Hardware-inventaris op clients inschakelen** in de clientinstellingen zijn ingeschakeld.  

 Nadat de hardware-inventarisatie is ingeschakeld en een hardware-inventarisatiefase is uitgevoerd door de client, verzendt de client de informatie naar een beheerpunt in de site van de client. Het beheerpunt stuurt vervolgens de informatie over de inventaris naar de Configuration Manager-siteserver waarin de inventarisatiegegevens worden opgeslagen in de sitedatabase. Hardware-inventarisatie wordt op clients uitgevoerd volgens het schema dat u in de clientinstellingen opgeeft.  

 U kunt verschillende methoden gebruiken om weer te geven van de hardware-inventarisgegevens die door Configuration Manager worden verzameld. Dit zijn:  

-   [Query's maken die apparaten retourneren die zijn gebaseerd op een specifieke hardwareconfiguratie](../../../../core/servers/manage/queries-technical-reference.md).  

-   [Query's gebaseerde verzamelingen maken die zijn gebaseerd op een specifieke hardwareconfiguratie](../../../../core/clients/manage/collections/introduction-to-collections.md). Op query's gebaseerde verzamelinglidmaatschappen worden automatisch volgens een schema bijgewerkt. U kunt verzamelingen gebruiken voor de verschillende taken, waaronder software-implementatie. .  

-   [Uitvoeren van rapporten met specifieke details over hardwareconfiguraties in uw organisatie](../../../../core/servers/manage/reporting.md).   

-   [Resource Explorer gebruiken](../../../../core/clients/manage/inventory/use-resource-explorer-to-view-hardware-inventory.md) om gedetailleerde informatie over de hardware-inventaris worden verzameld van clientapparaten weer te geven.   

 Wanneer een hardware-inventarisatie op een clientapparaat wordt uitgevoerd, omvatten de inventarisgegevens die door de client worden geretourneerd altijd een volledige inventarisatie. Volgende inventarisgegevens bevatten alleen gewijzigde inventarisgegevens. De siteserver verwerkt gewijzigde inventarisgegevens in de volgorde waarin deze worden ontvangen. Als delta-informatie voor een client ontbreekt, wordt de siteserver wordt geweigerd delta-aanvullende informatie en instrueert de client uit te voeren een volledige inventarisatie.  

 Configuration Manager biedt beperkte ondersteuning voor dual-boot-computers. Configuration Manager kan dual-boot-computers detecteren maar retourneert alleen inventarisatiegegevens van het besturingssysteem dat op het moment dat de inventarisatiecyclus actief was uitgevoerd.  

> [!NOTE]  
>  Zie voor meer informatie over het gebruik van hardware-inventaris met clients met Linux en UNIX [Hardware-inventaris voor Linux en UNIX in System Center Configuration Manager](../../../../core/clients/manage/inventory/hardware-inventory-for-linux-and-unix.md).  

## <a name="extending-configuration-manager-hardware-inventory"></a>Hardware-inventarisatie in Configuration Manager uitbreiden  
 Naast de ingebouwde hardware-inventarisatie in Configuration Manager kunt u een van de volgende methoden ook gebruiken om uit te breiden hardware-inventaris verzamelen van aanvullende informatie:  

- U kunt inschakelen, uitschakelen, toevoegen en verwijderen inventarisklassen voor hardware-inventaris uit de Configuration Manager-console. |  
- Gebruik NOIDMIF-bestanden voor het verzamelen van informatie over clientapparaten die niet kunnen worden geïnventariseerd door Configuration Manager. Het is bijvoorbeeld mogelijk dat u informatie wilt verzamelen over het activumnummer van een apparaat, dat alleen als label bestaat op het apparaat. NOIDMIF-inventarisatie is automatisch gekoppeld aan het clientapparaat waarvan deze is verzameld.  
- Gebruik IDMIF-bestanden voor het verzamelen van informatie over activa dat niet zo gekoppeld aan een Configuration Manager-client zijn, projectors, fotokopieerapparaten en netwerkprinters.  

 Zie voor meer informatie over het gebruik van deze methoden om hardware-inventaris van Configuration Manager uitbreiden [hardware-inventaris configureren in System Center Configuration Manager](../../../../core/clients/manage/inventory/configure-hardware-inventory.md).  
