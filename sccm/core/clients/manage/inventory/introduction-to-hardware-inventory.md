---
title: Hardware-inventaris - Configuration Manager | Microsoft-documenten
description: Kennismaking met hardware-inventaris in System Center Configuration Manager.
ms.custom: na
ms.date: 02/22/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: get-started-article
ms.assetid: 3969952e-9d05-49c9-82a2-e7e90ccef511
caps.latest.revision: 6
caps.handback.revision: 0
author: andredm7
ms.author: andredm
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9c5d1e48b76392beaf54b5377c69b648537e86f8
ms.openlocfilehash: c64f0b42bff25e8e91cf9101d6fbb538634eab15
ms.contentlocale: nl-nl
ms.lasthandoff: 05/17/2017


---
# <a name="introduction-to-hardware-inventory-in-system-center-configuration-manager"></a>Inleiding tot de hardware-inventaris in System Center Configuration Manager

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*

Hardware-inventarisatie in System Center Configuration Manager voor het verzamelen van informatie over de hardwareconfiguratie van clientapparaten in uw organisatie gebruiken. Als u de hardware-inventaris wilt verzamelen, moet de instelling **Hardware-inventaris op clients inschakelen** in de clientinstellingen zijn ingeschakeld.  

 Nadat de hardware-inventarisatie is ingeschakeld en een hardware-inventarisatiefase door de client wordt uitgevoerd, verzendt de client de informatie naar een beheerpunt in de site van de client. Het beheerpunt stuurt vervolgens de inventaris doorgegeven aan de Configuration Manager-siteserver waarin de Inventarisinformatie wordt opgeslagen in de sitedatabase. Hardware-inventarisatie wordt op clients uitgevoerd volgens het schema dat u in de clientinstellingen opgeeft.  

 U kunt verschillende methoden gebruiken om de hardware-inventarisgegevens verzameld van Configuration Manager weer te geven. Dit zijn:  

-   [Query's maken die de apparaten die zijn gebaseerd op een specifieke hardwareconfiguratie geretourneerd](../../../../core/servers/manage/queries-technical-reference.md).  

-   [Maken van query's gebaseerde verzamelingen die zijn gebaseerd op een specifieke hardwareconfiguratie](../../../../core/clients/manage/collections/introduction-to-collections.md). Op query's gebaseerde verzamelinglidmaatschappen worden automatisch volgens een schema bijgewerkt. U kunt verzamelingen gebruiken voor de verschillende taken, waaronder software-implementatie. .  

-   [Rapporten uitvoeren waarmee u specifieke gegevens over hardwareconfiguraties in uw organisatie weergeven](../../../../core/servers/manage/reporting.md).   

-   [Resource Explorer gebruiken](../../../../core/clients/manage/inventory/use-resource-explorer-to-view-hardware-inventory.md) gedetailleerde informatie weergeven over de hardware-inventaris die wordt verzameld van clientapparaten.   

 Wanneer een hardware-inventarisatie op een clientapparaat wordt uitgevoerd, omvatten de inventarisgegevens die door de client worden geretourneerd altijd een volledige inventarisatie. Volgende inventarisgegevens bevatten alleen gewijzigde inventarisgegevens. De siteserver verwerkt gewijzigde inventarisgegevens in de volgorde waarin deze worden ontvangen. Als verschillen voor een client informatie ontbreekt, wordt de siteserver verwerpt delta-aanvullende informatie en geeft de client een cyclus volledige inventaris uitvoert.  

 Configuration Manager geeft beperkte ondersteuning voor dual-boot-computers. Configuration Manager dual-boot computers kan detecteren, maar alleen retourneert informatie-inventarisatie van het besturingssysteem dat actief op het moment van de inventarisatiecyclus was is uitgevoerd.  

> [!NOTE]  
>  Zie voor meer informatie over het gebruik van hardware-inventaris met clients die Linux en UNIX uitvoeren [Hardware-inventaris voor Linux en UNIX in System Center Configuration Manager](../../../../core/clients/manage/inventory/hardware-inventory-for-linux-and-unix.md).  

## <a name="extending-configuration-manager-hardware-inventory"></a>Hardware-inventarisatie in Configuration Manager uitbreiden  
 Naast de ingebouwde hardware-inventaris in Configuration Manager kunt u een van de volgende methoden ook gebruiken om uit te breiden hardware-inventaris om extra informatie te verzamelen:  

- U kunt inschakelen, uitschakelen, toevoegen en verwijderen van inventarisklassen voor hardware-inventarisatie van de Configuration Manager-console. |  
- NOIDMIF-bestanden gebruiken voor het verzamelen van informatie over clientapparaten die door Configuration Manager kan niet worden geïnventariseerd. Het is bijvoorbeeld mogelijk dat u informatie wilt verzamelen over het activumnummer van een apparaat, dat alleen als label bestaat op het apparaat. NOIDMIF-inventarisatie is automatisch gekoppeld aan het clientapparaat waarvan deze is verzameld.  
- IDMIF-bestanden voor het verzamelen van informatie over activa die gekoppeld aan een Configuration Manager-client, bijvoorbeeld zijn, projectors, fotokopieerapparaten en netwerkprinters gebruiken.  

 Zie voor meer informatie over hardware-inventaris van Configuration Manager uitbreiden met behulp van deze methoden, [hardware-inventaris configureren in System Center Configuration Manager](../../../../core/clients/manage/inventory/configure-hardware-inventory.md).  

