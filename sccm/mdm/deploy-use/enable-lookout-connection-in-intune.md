---
title: Schakel altijd MTP in Intune | Microsoft-documenten
description: Schakel de beveiliging van mobiele bedreiging dan in de Intune-beheerconsole.
ms.custom: na
ms.date: 03/05/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-hybrid
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 7e4ada34-63bf-4b9f-8246-31816aa44196
caps.latest.revision: 
author: mtillman
ms.author: mtillman
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 6424fb07802b62820b4dc78a58ab30d3b956abef
ms.openlocfilehash: f9ddbcc981fa1274a41ae16a6a939c0cdf739c3e
ms.contentlocale: nl-nl
ms.lasthandoff: 05/17/2017


---
# <a name="enable-lookout-mtp-connection-in-the-intune-admin-console"></a>Zoek MTP-verbinding in de Intune-beheerconsole inschakelen

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*

In dit onderwerp wordt beschreven hoe u de verbinding dan MTP in Intune inschakelen. U moet al hebt geconfigureerd de Intune-Connector in de console altijd voordat u deze stap uitvoert.  Als u dit nog niet hebt gedaan, gaat u als de stappen in [instellen van uw abonnement met altijd mobiele bedreiging beveiliging](set-up-your-subscription-with-lookout.md).

Inschakelen van de verbinding dan MTP in Intune, op de **beheer** pagina de [Microsoft Intune-beheerconsole](https://manage.microsoft.com), kies **van derden-integratie**. Kies **altijd status** en schakel **synchronisatie met MTP** met behulp van de knop in-of uitschakelen.

![Schermafdruk van de pagina altijd met de inschakelen wisselknop gemarkeerd](media/lookout-intune-synchronization.png)

Dit voltooit de installatie van de integratie altijd en Intune in de Intune-beheerconsole.  De volgende stappen om deze oplossing te implementeren omvatten implementeren de [dan zakelijke apps](configure-and-deploy-lookout-for-work-apps.md) en het instellen van de [naleving](enable-device-threat-protection-rule-compliance-policy.md) beleid.

>[!IMPORTANT]
> U **moet** altijd werk app voordat u naleving beleidsregels maken en configureren van voorwaardelijke toegang configureren. Dit zorgt ervoor dat de app is gereed en beschikbaar zijn voor eindgebruikers te installeren voordat ze toegang tot e-mail of andere bedrijfsresources krijgen kunnen.

## <a name="next-steps"></a>Volgende stappen
[Zoek voor werk app configureren](configure-and-deploy-lookout-for-work-apps.md)

