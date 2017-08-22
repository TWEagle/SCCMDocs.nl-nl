---
title: Endpoint Protection-malwaredefinities vanaf netwerkshare | Microsoft Docs
description: Informatie over het handmatig de meest recente definitie-updates downloaden van Microsoft en Configureer clients voor het downloaden van deze definities.
ms.custom: na
ms.date: 02/14/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: configmgr-other
ms.tgt_pltfrm: na
ms.topic: get-started-article
ms.assetid: ddef4d2a-f481-4020-9ddd-9cca5f9795cb
caps.latest.revision: "21"
author: NathBarn
ms.author: nathbarn
manager: angrobe
ms.openlocfilehash: 110bd9a9d04b27ef6794145fae66dbd910308bdc
ms.sourcegitcommit: 51fc48fb023f1e8d995c6c4eacfda7dbec4d0b2f
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 08/07/2017
---
# <a name="enable-endpoint-protection-malware-definitions-to-download-from-a-network-share-for-configuration-manager"></a>Endpoint Protection-malware-definities te downloaden vanaf een netwerkshare voor Configuration Manager inschakelen

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*

 U kunt handmatig de meest recente definitie-updates van Microsoft downloaden en vervolgens clients zo configureren dat deze de definities uit een gedeelde map op het netwerk downloaden. Gebruikers kunnen ook definitie-updates in gang zetten wanneer u deze bron voor updates gebruikt.

> [!NOTE]
>  Clients moeten leestoegang hebben tot de gedeelde map om de definitie-updates te kunnen downloaden.

 Zie voor meer informatie over het downloaden van de definitie en engine-updates op te slaan op de bestandsshare [installeert de meest recente Microsoft antimalware- en software](http://www.microsoft.com/security/portal/Definitions/HowToForeFront.aspx).

## <a name="to-configure-definition-downloads-from-a-file-share"></a>Definitiedownloads van een bestandsshare configureren

1.  Klik op **Activa en naleving**op de Configuration Manager-console.

2.  Vouw **Endpoint Protection** uit in de werkruimte **Activa en naleving**en klik vervolgens op **Anti-malwarebeleidsregels**.

3.  Open de eigenschappenpagina van het **standaard toegepaste anti-malwarebeleid** of maak een nieuw anti-malwarebeleid. Zie voor meer informatie over het maken van beleidsregels voor antimalware [maken en implementeren van antimalwarebeleid voor Endpoint Protection in System Center Configuration Manager](endpoint-antimalware-policies.md).

4.  Klik in de sectie **Definitie-updates** van het dialoogvenster Eigenschappen anti-malware op **Bron instellen**.

5.  Selecteer in het dialoogvenster **Definitie-updatebronnen configureren** de optie **Updates vanuit UNC-bestandsshares**.

6.  Klik op **OK** om het dialoogvenster **Definitie-updatebronnen configureren** te sluiten.

7.  Klik op **Paden instellen**. Voeg vervolgens in het dialoogvenster **UNC-paden voor definitie-updates configureren** een of meer UNC-paden toe aan de locatie van de definitie-updates op een netwerkshare.

8.  Klik op **OK** om het dialoogvenster **UNC-paden voor definitie-updates configureren** te sluiten.


> [!div class="button"]
[Volgende stap >](endpoint-antimalware-policies.md)

> [!div class="button"]
[Terug >](endpoint-configure-alerts.md)
