---
title: Beleid voor apparaten die zijn geregistreerd met Intune extern synchroniseren | Microsoft-documenten
description: Meer informatie over het beleid op Intune ingeschreven apparaten uit de Configuration Manager-console synchroniseren
ms.custom: na
ms.date: 03/05/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-hybrid
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: b3731ad0-2a24-4042-994e-5e4c1230e3fe
caps.latest.revision: 18
caps.handback.revision: 0
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 2c723fe7137a95df271c3612c88805efd8fb9a77
ms.openlocfilehash: 337814fd5ba49ed17fc97aba49f79f02df817f4e
ms.contentlocale: nl-nl
ms.lasthandoff: 05/17/2017

---
# <a name="remotely-synchronize-policy-on-intune-enrolled-devices-from-the-configuration-manager-console"></a>Beleid voor Intune ingeschreven apparaten uit de Configuration Manager-console op afstand synchroniseren

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*


U kunt de synchronisatie van een beleid voor een apparaat dat is geregistreerd met Intune vanuit de Configuration Manager-console in plaats van een synchronisatie van de bedrijfsportal-app op het apparaat zelf aanvragen aanvragen. 

U doet dit als volgt:

1.    Selecteer een apparaat onder **activa en naleving** > **overzicht** > **apparaten**.
2.    Klik op **Sync aanvraag verzenden** in de **externe apparaat acties** menu.


Na vijf tot tien minuten worden geen wijzigingen in het beleid op het apparaat gesynchroniseerd. Vindt u informatie over de status van de synchronisatie-aanvraag in een nieuwe kolom in de apparaat-weergaven kunt genoemd **afstand synchronisatiestatus**, evenals als in de sectie discovery data van de **eigenschappen** in het dialoogvenster voor elk apparaat.

