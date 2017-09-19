---
title: Op afstand synchroniseren beleid op apparaten die zijn ingeschreven met Intune | Microsoft Docs
description: Informatie over het beleid voor Intune ingeschreven apparaten uit de Configuration Manager-console synchroniseren
ms.custom: na
ms.date: 03/05/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: configmgr-hybrid
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: b3731ad0-2a24-4042-994e-5e4c1230e3fe
caps.latest.revision: "18"
caps.handback.revision: "0"
author: arob98
ms.author: angrobe
manager: angrobe
ms.openlocfilehash: 387f6303611010ab3d72f796455409ebfff65099
ms.sourcegitcommit: b438515490e04fb09c82a8af642d38e9a0605178
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 09/15/2017
---
# <a name="remotely-synchronize-policy-on-intune-enrolled-devices-from-the-configuration-manager-console"></a>Beleid voor Intune ingeschreven apparaten uit de Configuration Manager-console op afstand te synchroniseren

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*


U kunt de synchronisatie van een beleid voor een apparaat dat is geregistreerd bij Intune via de Configuration Manager-console in plaats van een synchronisatie aanvragen bij de bedrijfsportal-app op het apparaat zelf aanvragen. 

U doet dit als volgt:

1.  Selecteer een apparaat onder **activa en naleving** > **overzicht** > **apparaten**.
2.  Klik op **synchronisatie-aanvraag verzenden** in de **acties extern apparaat** menu.


Na vijf tot tien minuten, worden eventuele wijzigingen in het beleid gesynchroniseerd naar het apparaat. Vindt u informatie over de status van de synchronisatie-aanvraag in een nieuwe kolom in de apparaat-weergaven, aangeroepen **status van externe synchronisatie**, evenals als in de sectie van de discovery data van het **eigenschappen** in het dialoogvenster voor elk apparaat.
