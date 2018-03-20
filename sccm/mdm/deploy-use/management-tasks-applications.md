---
title: Toepassingen beheren
titleSuffix: Configuration Manager
description: Toepassingen in System Center Configuration Manager beheren.
ms.custom: na
ms.date: 03/05/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-hybrid
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 8adbe2e2-de26-4a80-8bbd-a5f34b8bac79
caps.latest.revision: 
caps.handback.revision: 
author: dougeby
ms.author: dougeby
manager: angrobe
ms.openlocfilehash: 4e61962ef4be43f4c32d79ba531d4e68534df6fe
ms.sourcegitcommit: 52080ef1b0f9a27c123711ef274ac3ffe070e8e0
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 03/20/2018
---
# <a name="manage-applications-in-system-center-configuration-manager"></a>Toepassingen in System Center Configuration Manager beheren

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*

Als u apparaten via Microsoft Intune beheren of Configuration Manager on-premises beheer van apparaten, kunt u deze extra toepassingstypen kunt beheren:
- Windows Phone-app-pakket (XAP-bestand)
- App-pakket voor iOS (*.ipa-bestand)
- App-pakket voor Android (*.apk-bestand)
- App-pakket voor Android in Google Play
- Windows Phone-app-pakket (in de Windows Phone Store)
- Windows Installer via MDM
- Webtoepassing

Deze sectie bevat gedetailleerde informatie over het maken en beheren van toepassingen die gebruikmaken van hybride MDM of on-premises MDM.

[Beheertaken voor System Center Configuration Manager-toepassingen](../../apps/deploy-use/management-tasks-applications.md) meer algemene informatie over het beheren van System Center Configuration Manager-toepassingen en implementatietypen.

## <a name="deploying-and-monitoring-apps"></a>Implementeren en bewaken van apps

Implementeren en bewaken van toepassingen in System Center Configuration Manager zijn dezelfde processen voor mobiele apparaten als voor de apparaten op locatie, zoals laptops en desktops. U kunt lezen via de volgende onderwerpen voor algemene informatie over het implementeren en controleren van toepassingen:

- [Implementeren van toepassingen in System Center Configuration Manager](../../apps/deploy-use/deploy-applications.md)
- [Toepassingen bewaken in System Center Configuration Manager](../../apps/deploy-use/monitor-applications-from-the-console.md)

Hier volgen enkele punten waarmee u rekening moet houden bij het implementeren en controleren van toepassingen, specifiek voor het beheer van mobiele apparaten.

- MDM-ingeschreven apparaten bieden geen ondersteuning voor gesimuleerde implementaties, gebruikerservaring en programmatie-instellingen.

- U kunt de implementatie kunt koppelen aan een configuratiebeleid voor iOS-app als u al hebt congured een. Zie [iOS-apps configureren met configuratiebeleidsregels](configure-ios-apps-with-app-configuration-policies.md).

### <a name="next-steps"></a>Volgende stappen

Mogelijk uiteindelijk u wijzigingen aanbrengen in een toepassing, een toepassing verwijderen of een geïmplementeerde toepassing vervangen door een nieuwe toepassing. Lees [bijwerken en buiten gebruik stellen met System Center Configuration Manager-toepassingen](../../apps/deploy-use/update-and-retire-applications.md) deze mogelijkheden begrijpen.
