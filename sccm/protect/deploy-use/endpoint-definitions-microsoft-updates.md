---
title: Endpoint Protection-malwaredefinities vanaf netwerkshare | Microsoft Docs
description: Informatie over het inschakelen van de Endpoint Protection-malware-definities van Microsoft-Updates voor Configuration Manager te downloaden.
ms.custom: na
ms.date: 02/14/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: configmgr-other
ms.tgt_pltfrm: na
ms.topic: get-started-article
ms.assetid: ab7626ae-d4bf-4ca6-ab25-c61f96800a02
caps.latest.revision: "21"
author: NathBarn
ms.author: nathbarn
manager: angrobe
ms.openlocfilehash: 58c468fc3d4427cc1f2a8f197ab784a767151203
ms.sourcegitcommit: 51fc48fb023f1e8d995c6c4eacfda7dbec4d0b2f
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 08/07/2017
---
# <a name="enable-endpoint-protection-malware-definitions-to-download-from-microsoft-updates-for-configuration-manager"></a>Endpoint Protection-malware-definities te downloaden van Microsoft-Updates voor Configuration Manager inschakelen

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*


 Wanneer u ervoor kiest om definitie-updates te downloaden vanaf de Microsoft Update-site, wordt de Microsoft Update-site door de clients gecontroleerd volgens het interval dat is gedefinieerd in de sectie **Definitie-updates** in het dialoogvenster voor anti-malwarebeleid.

 Deze methode kan nuttig zijn wanneer de client geen verbinding met de Configuration Manager-site of als u wilt dat gebruikers kunnen definitieupdates te initiëren.

> [!IMPORTANT]
>  Clients moeten toegang hebben tot Microsoft Update op internet om via deze methode definitie-updates te downloaden.

## <a name="using-the-microsoft-malware-protection-center-to-download-definitions"></a>Definities downloaden met Microsoft Malware Protection Center
 U kunt clients configureren voor het downloaden van definitie-updates van Microsoft Malware Protection Center. Deze optie wordt gebruikt door Endpoint Protection-clients definitieupdates te downloaden als ze zijn geen updates downloaden vanaf een andere bron. Deze updatemethode kan nuttig zijn als er is een probleem met uw Configuration Manager-infrastructuur waardoor de levering van updates.

> [!IMPORTANT]
>  Clients moeten toegang hebben tot Microsoft Update op internet om via deze methode definitie-updates te downloaden.


> [!div class="button"]
[Volgende stap >](endpoint-antimalware-policies.md)

> [!div class="button"]
[Terug >](endpoint-configure-alerts.md)
