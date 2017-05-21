---
title: Beheren van toepassingen in System Center Configuration Manager | Microsoft-documenten
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
caps.latest.revision: 18
caps.handback.revision: 0
author: mtillman
ms.author: mtillman
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 2c723fe7137a95df271c3612c88805efd8fb9a77
ms.openlocfilehash: bc7bb99bc526ed0bbaaad15fc9af39fa8b7c3893
ms.contentlocale: nl-nl
ms.lasthandoff: 05/17/2017

---
# <a name="manage-applications-in-system-center-configuration-manager"></a>Toepassingen in System Center Configuration Manager beheren

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*

Wanneer u apparaten via Microsoft Intune beheren of Configuration Manager on-premises Apparaatbeheer, kunt u deze extra toepassingstypen beheren:
- Windows Phone-app-pakket (XAP-bestand)
- App-pakket voor iOS (*.ipa-bestand)
- App-pakket voor Android (*.apk-bestand)
- App-pakket voor Android in Google Play
- Windows Phone-app-pakket (in de Windows Phone Store)
- Windows Installer via MDM
- Webtoepassing

Deze sectie bevat gedetailleerde informatie over het maken en beheren van toepassingen met hybride MDM of on-premises MDM

[Beheertaken voor System Center Configuration Manager-toepassingen](../../apps/deploy-use/management-tasks-applications.md) bevat meer algemene informatie over het beheren van System Center Configuration Manager-toepassingen en implementatietypen.

## <a name="deploying-and-monitoring-apps"></a>Implementeren en controleren van apps

Implementeren en controleren van toepassingen in System Center Configuration Manager zijn dezelfde processen voor mobiele apparaten voor apparaten op locatie, zoals laptops en desktops. U kunt lezen via de volgende onderwerpen voor algemene informatie over het implementeren en bewaking van toepassingen:

- [Toepassingen implementeren in System Center Configuration Manager](../../apps/deploy-use/deploy-applications.md)
- [Toepassingen in System Center Configuration Manager controleren](../../apps/deploy-use/monitor-applications-from-the-console.md)

Hier volgen enkele punten waarmee u rekening moet houden bij het implementeren en bewaking van toepassingen, specifiek zijn voor beheer van mobiele apparaten.

- MDM ingeschreven apparaten bieden geen ondersteuning voor gesimuleerde implementaties gebruikerservaring en programmatie-instellingen.

- U kunt de implementatie koppelen aan een configuratiebeleid voor iOS-app als u al hebt congured een. Zie [iOS-apps configureren met app-configuratiebeleid](configure-ios-apps-with-app-configuration-policies.md).

### <a name="next-steps"></a>Volgende stappen

Uiteindelijk raadzaam wijzigingen aanbrengen in een toepassing, een toepassing verwijderen of een reeds geïmplementeerde toepassing vervangen door een nieuwe toepassing. Lees [Update en buiten gebruik stellen van toepassingen met System Center Configuration Manager](../../apps/deploy-use/update-and-retire-applications.md) om te begrijpen van deze mogelijkheden.

