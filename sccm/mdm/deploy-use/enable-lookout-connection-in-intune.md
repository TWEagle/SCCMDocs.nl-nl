---
title: Lookout MTP in Intune inschakelen
titleSuffix: Configuration Manager
description: Schakel de beveiliging van mobiele threat Lookout in de Intune-beheerconsole.
ms.custom: na
ms.date: 03/05/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: configmgr-hybrid
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 7e4ada34-63bf-4b9f-8246-31816aa44196
caps.latest.revision: 
author: dougeby
ms.author: dougeby
manager: angrobe
ms.openlocfilehash: 2d4cdb20f66864ac9bf79b89189e97fab26b34f3
ms.sourcegitcommit: c236214b2fcc13dae7bad96d7fb33f692868191d
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/12/2017
---
# <a name="enable-lookout-mtp-connection-in-the-intune-admin-console"></a>Lookout MTP-verbinding in de Intune-beheerconsole inschakelen

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*

Dit onderwerp leest u het inschakelen van de Lookout MTP-verbinding in Intune. U moet al hebt geconfigureerd de Intune-Connector in de console Lookout voordat u deze stap uitvoert.  Als u dit nog niet hebt gedaan, gaat u de stappen in [instellen van uw abonnement met Lookout mobiele threat protection](set-up-your-subscription-with-lookout.md).

De Lookout MTP-verbinding in Intune, inschakelen op de **beheer** pagina in de [Microsoft Intune-beheerconsole](https://manage.microsoft.com), kies **van derden-integratie**. Kies **Lookout status** en schakel **synchronisatie met MTP** met behulp van de wisselknop.

![Schermafbeelding van de pagina Lookout synchronisatie met de wisselknop inschakelen is gemarkeerd](media/lookout-intune-synchronization.png)

Dit voltooit de installatie van de Lookout en Intune-integratie in de Intune-beheerconsole.  De volgende stappen voor het implementeren van deze oplossing betrekken implementeren de [Lookout for Work apps](configure-and-deploy-lookout-for-work-apps.md) en het instellen van de [naleving](enable-device-threat-protection-rule-compliance-policy.md) beleid.

>[!IMPORTANT]
> U **moet** configureren de Lookout for Work-app voor het maken van beleidsregels voor naleving en voorwaardelijke toegang configureren. Dit zorgt ervoor dat de app is gereed en beschikbaar zijn voor eindgebruikers te installeren voordat ze toegang tot e-mail of andere bedrijfsresources krijgen kunnen.

## <a name="next-steps"></a>Volgende stappen
[Lookout voor Work-app configureren](configure-and-deploy-lookout-for-work-apps.md)
