---
title: Regel voor het beveiliging in nalevingsbeleid voor apparaten inschakelen
titleSuffix: Configuration Manager
description: Schakel mobiele threat protection regel in het nalevingsbeleid voor apparaten.
ms.custom: na
ms.date: 03/05/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: configmgr-hybrid
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 99a5b715-f172-46e1-ac27-ad55bde66d0d
caps.latest.revision: 
author: dougeby
ms.author: dougeby
manager: angrobe
ms.openlocfilehash: d74360ce800f030e85e2b87defc1de3376c6aee5
ms.sourcegitcommit: c236214b2fcc13dae7bad96d7fb33f692868191d
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/12/2017
---
# <a name="enable-device-threat-protection-rule-in-the-compliance-policy"></a>Device threat protection regel in het nalevingsbeleid inschakelen

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*

Intune met Lookout mobiele threat protection biedt u de mogelijkheid mobiele bedreigingen detecteren en maken van een risicoanalyse uit te voeren op het apparaat. U kunt een beleidsregel voor naleving in Configuration Manager om op te nemen van de risico-evaluatie om te bepalen of het apparaat compatibel maken. Vervolgens kunt u beleid voor voorwaardelijke toegang wilt toestaan of blokkeren van toegang tot Exchange, SharePoint en andere services op basis van de naleving van apparaat.

Lookout apparaat detectie van dreigingen invloed hebben op het nalevingsbeleid voor het apparaat hebben:

* De **Device Threat Protection** regel moet worden ingeschakeld op het nalevingsbeleid.

* De **Lookout Status** pagina in de **Intune-beheerconsole** moeten worden weergegeven als **Active**. Zie de [inschakelen Lookout MTP-verbinding in Intune](enable-lookout-connection-in-intune.md) onderwerp voor meer informatie en instructies over het activeren van Lookout integratie.


Voordat u de regel device threat protection maakt in het beleid compliancy, we raden aan dat u [instellen van uw abonnement met Lookout device threat protection](set-up-your-subscription-with-lookout.md), [Lookout verbinding in Intune inschakelen](enable-lookout-connection-in-intune.md), en [de Lookout for work-app configureren](configure-and-deploy-lookout-for-work-apps.md). De regel voor naleving van kracht nadat de installatie is voltooid.

Om de regel device threat protection, moet u een bestaande nalevingsbeleid gebruiken of maak een nieuwe.

Als onderdeel van de installatie van Lookout device threat protection in de [Lookout console](https://aad.lookout.com), gemaakt van een beleid dat verschillende bedreigingen in hoog, gemiddeld en laag niveaus wordt geclassificeerd. In de Intune-nalevingsbeleid gebruikt u het risiconiveau het dreigingsniveau van de maximale toegestane instellen.

Op de **regels** pagina van de wizard nalevingsbeleid, definieert u een nieuwe regel met de volgende informatie:
  * Voorwaarde: Device threat protection maximale risiconiveau.
  * Waarde: De waarde kan een van de volgende zijn:
    * **Geen (beveiligde)**: Dit is de veiligste. Dit betekent dat het apparaat kan niet alle bedreigingen. Als elk bedreigingsniveau worden gevonden, wordt het apparaat wordt geëvalueerd als niet-compatibel.
    * **Lage**: Het apparaat wordt geëvalueerd als compatibel als alleen laag niveau bedreigingen aanwezig zijn. Een waarde hoger plaatst het apparaat in een niet-compatibele status.
    * **Gemiddeld**: Het apparaat wordt geëvalueerd als compatibel als de bedreigingen die zijn gevonden op het apparaat laag of gemiddeld niveau zijn. Als hoog niveau dreigingen worden gedetecteerd, wordt het apparaat bepaald als niet-compatibel.
    * **Hoge**: Dit is de minst veilige. In wezen hierdoor alle threat niveaus en bijvoorbeeld alleen nuttig als u deze oplossing werkt alleen voor rapportagedoeleinden.

Als u beleid voor voorwaardelijke toegang voor Office 365 en andere services maakt, wordt de bovenstaande compatibiliteitsevaluatie rekening is gehouden en niet-compatibele apparaten hebben geen toegang tot toegang tot bedrijfsbronnen totdat de bedreiging opgelost is.

De status van het apparaat threat protection wordt weergegeven op de **beveiliging** knooppunt in de **bewaking** werkruimte.
Een samenvatting van de status met verschillende thread-niveau wordt weergegeven in een visual grafiek. U kunt klikken op de afzonderlijke secties van de grafiek voor meer informatie, zoals, het aantal apparaten die rapporteren als niet-compatibel per platform en eventuele fouten die worden gerapporteerd.
U ziet ook de status van afzonderlijke apparaten in de **activa en naleving** werkruimte onder **apparaten**.  U kunt toevoegen de **threat apparaatcompatibiliteit** en de **apparaat risiconiveau** kolommen om de status te bekijken.  Deze kolommen worden niet standaard weergegeven.
