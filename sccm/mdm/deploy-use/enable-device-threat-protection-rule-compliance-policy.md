---
title: Regel voor het apparaat beveiliging in nalevingsbeleid inschakelen | Microsoft-documenten
description: Mobiele bedreiging beveiliging regel in het nalevingsbeleid apparaat inschakelen.
ms.custom: na
ms.date: 03/05/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-hybrid
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 99a5b715-f172-46e1-ac27-ad55bde66d0d
caps.latest.revision: 
author: mtillman
ms.author: mtillman
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 6424fb07802b62820b4dc78a58ab30d3b956abef
ms.openlocfilehash: faa92e150686e615164ce3f5435b77a65305aab3
ms.contentlocale: nl-nl
ms.lasthandoff: 05/17/2017


---
# <a name="enable-device-threat-protection-rule-in-the-compliance-policy"></a>Regel voor de beveiliging van apparaat bedreiging in het nalevingsbeleid inschakelen

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*

Intune met altijd mobiele bedreiging beveiliging kunt u de testomgeving mobiele bedreigingen detecteren en maken van een risicoanalyse op het apparaat. U kunt een beleidsregel naleving in Configuration Manager op te nemen om te bepalen of het apparaat compatibel is de beoordeling van het risico te maken. Vervolgens kunt u het beleid voor voorwaardelijke toegang wilt toestaan of blokkeren van toegang tot Exchange, SharePoint en andere services die op basis van het apparaat moet voldoen.

Om te hebben dan bedreiging detectie van invloed zijn op het nalevingsbeleid voor het apparaat:

* De **apparaat bedreiging beveiliging** regel moet worden ingeschakeld op het nalevingsbeleid.

* De **altijd Status** pagina de **Intune-beheerconsole** moet worden weergegeven als **Active**. Zie de [inschakelen dan MTP-verbinding in Intune](enable-lookout-connection-in-intune.md) onderwerp voor meer informatie en instructies over het altijd integratie te activeren.


Voordat u het apparaat bedreiging beveiliging regel in het beleid in overeenstemming is, raden wij u [instellen van uw abonnement met altijd apparaat bedreiging beveiliging](set-up-your-subscription-with-lookout.md), [inschakelen van de verbinding dan in Intune](enable-lookout-connection-in-intune.md), en [altijd werk app configureren](configure-and-deploy-lookout-for-work-apps.md). De compliantieregel afgedwongen nadat de installatie is voltooid.

Als u wilt de regel apparaat bedreiging beveiliging inschakelt, moet u een bestaande nalevingsbeleid gebruiken of maak een nieuwe.

Als onderdeel van de setup dan apparaat bedreiging beveiliging in de [altijd console](https://aad.lookout.com), gemaakt van een beleid dat verschillende bedreigingen in hoog, gemiddeld en laag niveaus wordt geclassificeerd. In het nalevingsbeleid Intune gebruikt u de risiconiveau de maximale toegestane risiconiveau instellen.

Op de **regels** pagina van de wizard beleid voor naleving definieert u een nieuwe regel met de volgende informatie:
  * Voorwaarde: Apparaat bedreiging maximale risico beveiligingsniveau.
  * Waarde: De waarden zijn:
    * **Geen (beveiligde)**: Dit is de meest veilige. Dit betekent dat het apparaat kan niet alle bedreigingen. Als een bedreigingsniveau worden gevonden, wordt het apparaat wordt geëvalueerd als niet-compatibel.
    * **Low**: Het apparaat wordt geëvalueerd als compatibel als er slechts laag niveau bedreigingen aanwezig zijn. Een waarde hoger plaatst het apparaat in een niet-compatibele status.
    * **Gemiddeld**: Het apparaat wordt geëvalueerd als compatibel als de bedreigingen die zijn gevonden op het apparaat lage of gemiddelde niveau. Als hoog niveau bedreigingen worden gedetecteerd, wordt het apparaat bepaald als niet-compatibel.
    * **Hoge**: Dit is de minst veilige. In principe wordt hierdoor alle bedreiging niveaus en bijvoorbeeld alleen nuttig als u deze oplossing alleen voor rapportagedoeleinden.

Als u beleidsregels voor voorwaardelijke toegang voor Office 365 en andere services maakt, de bovenstaande compatibiliteitsevaluatie in acht wordt genomen en niet-compatibele apparaten hebben geen toegang tot toegang tot bedrijfsbronnen totdat de bedreiging opgelost is.

De beveiligingsstatus van de apparaat-bedreiging wordt weergegeven op de **beveiliging** knooppunt in de **bewaking** werkruimte.
Een samenvatting van de status van verschillende thread niveau wordt weergegeven in een visual grafiek. U kunt klikken op de afzonderlijke onderdelen van de grafiek voor meer informatie wilt, het aantal apparaten die rapporteren als niet-compatibel platform en eventuele fouten die zijn gerapporteerd.
U ziet ook de status van afzonderlijke apparaten in de **activa en naleving** werkruimte onder **apparaten**.  U kunt toevoegen de **bedreiging apparaatcompatibiliteit** en de **apparaat risiconiveau** kolommen voor de status.  Deze kolommen worden niet standaard weergegeven.

