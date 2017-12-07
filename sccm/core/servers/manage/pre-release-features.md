---
title: Pre-release functies
titleSuffix: Configuration Manager
description: Functies van evaluatieversies in System Center Configuration Manager
ms.custom: na
ms.date: 12/05/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 6bce416b-761d-4b23-bd33-5b7c30edb10d
caps.latest.revision: "36"
author: mestew
ms.author: mstewart
manager: angrobe
ms.openlocfilehash: c132f1512d8a1d6a4657079c8ecd2d7a050797b9
ms.sourcegitcommit: 52b956cfe32c3f06ae68d6ba6fc3244ce5a66325
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/06/2017
---
# <a name="pre-release-features-in-system-center-configuration-manager"></a>Functies van evaluatieversies in System Center Configuration Manager
*Van toepassing op: System Center Configuration Manager (huidige vertakking)*

Functies van evaluatieversies zijn functies die zich in de huidige vertakking voor vroege testdoeleinden in een productieomgeving. Deze functies worden volledig ondersteund maar nog in ontwikkeling actief zijn en wijzigingen mogelijk ontvangen totdat ze worden verplaatst buiten de categorie van de voorlopige versie.

 Voordat u de functies van evaluatieversies gebruiken kunt, moet u toestemming geven om te gebruiken pre-release functies vanuit de Configuration Manager-console voordat u kunt selecteren en het gebruik ervan.  

Toestemming verlenen is een eenmalige handeling per hiërarchie die niet ongedaan worden gemaakt. Totdat u toestemming geeft, kunt u nieuwe functies van evaluatieversies opgenomen met updates niet inschakelen. Nadat u een prerelease-functie inschakelt, kan u deze uitschakelen.

Als u toestemming geven, in de console gaat u naar **beheer** > **siteconfiguratie** > **Sites**, en kies vervolgens **hiërarchie-instellingen**. Op de **algemene** Kies **instemming met gebruik van functies van evaluatieversies**.

Wanneer u een update die functies van evaluatieversies bevat installeert, zijn die functies zichtbaar in de Wizard Updates en onderhoud met de normale functies in de update:
  - **Als u toestemming hebt gegeven:** Wanneer u de update installeert, kunt u functies van evaluatieversies van in de Wizard Updates en onderhoud inschakelen. Hiervoor selecteert u de functies van de voorlopige versie, net zoals u met andere functies doet.     

    U kunt eventueel wachten met een voorlopige versie inschakelen vanuit de **beheer** > **Updates en onderhoud** > **functies** knooppunt van de console. In de **functies** knooppunt de functie en kies **inschakelen**. Deze optie is niet beschikbaar totdat u toestemming. (Voorafgaand aan versie 1702, Updates en onderhoud is onder **beheer** > **Cloudservices**.)
  -   **Als u geen toestemming hebt gegeven:** Wanneer u een update installeert, functies van evaluatieversies zichtbaar zijn in de Wizard Updates en onderhoud, maar zijn niet beschikbaar en kunnen niet worden ingeschakeld. Nadat de update is geïnstalleerd, kunt u zien hoe deze functies in de **functies** knooppunt. Echter, u ze niet inschakelen totdat nadat u toestemming hebt gegeven **hiërarchie-instellingen**.

Als u toestemming op een zelfstandige primaire site hebt opgegeven en vouw vervolgens de hiërarchie door een nieuwe centrale beheersite installeert, moet u toestemming op de centrale beheersite opnieuw.

 Wanneer u een prerelease-functie inschakelt, moet de Configuration Manager-hiërarchie manager (HMAN) de wijziging verwerken voordat deze functie beschikbaar wordt. Verwerking van de wijziging is vaak onmiddellijke, maar duurt maximaal 30 minuten duren, afhankelijk van de HMAN verwerkingscyclus. Nadat de wijziging wordt verwerkt, moet u de console opnieuw opstarten voordat u de nieuwe gebruikersinterface die betrekking hebben op deze functie kunt weergeven.

**De volgende functies van evaluatieversies zijn beschikbaar:**

 |Onderdeel          |Als een voorlopige versie toegevoegd | Als een volledige functie toegevoegd|  
|------------------|---------------------|---------------------|
| Takenreeksstap uitvoeren<!-- 1261338 --> |  [Versie 1710](/sccm/osd/understand/task-sequence-steps#child-task-sequence) |![Nog niet](media/83c5d168-8faf-4e8e-920b-528e3c43ffd4.gif)|
| Windows Defender misbruik Guard<!-- 1355468 --> |  [Versie 1710](/sccm/protect/deploy-use/create-deploy-exploit-guard-policy) |![Nog niet](media/83c5d168-8faf-4e8e-920b-528e3c43ffd4.gif)|
| Maken en PowerShell-scripts uitvoeren vanaf de Configuration Manager-console<!-- 1236459 --> |  [Versie 1706](/sccm/apps/deploy-use/create-deploy-scripts)|![Nog niet](media/83c5d168-8faf-4e8e-920b-528e3c43ffd4.gif)|
| Guard Apparaatbeheer met Configuration Manager<!-- 1319346 --> |  [Versie 1702](/sccm/protect/deploy-use/use-device-guard-with-configuration-manager)|![Nog niet](media/83c5d168-8faf-4e8e-920b-528e3c43ffd4.gif)|
| Taak reeks vooraf inhoudcaching<!-- 1021244 --> |  [Versie 1702](/sccm/osd/deploy-use/create-a-task-sequence-to-upgrade-an-operating-system#configure-pre-cache-content) | [Versie 1706](/sccm/osd/deploy-use/create-a-task-sequence-to-upgrade-an-operating-system#configure-pre-cache-content)|
| Controleer voor het uitvoeren van uitvoerbare bestanden voordat u een toepassing installeert<!-- 1284624 --> |   [Versie 1702](/sccm/apps/deploy-use/deploy-applications#how-to-check-for-running-executable-files-before-installing-an-application) |[Versie 1706](/sccm/apps/deploy-use/deploy-applications#how-to-check-for-running-executable-files-before-installing-an-application)|
| Datawarehouse-servicepunt<!-- 1277922 --> |  [Versie 1702](/sccm/core/servers/manage/data-warehouse) |[Versie 1706](/sccm/core/servers/manage/data-warehouse)|
| Peer-Cache voor de distributie van inhoud aan clients<!-- 1101436 --> |  [Versie 1610](/sccm/core/plan-design/hierarchy/client-peer-cache) | [Versie 1710](/sccm/core/plan-design/hierarchy/client-peer-cache)|
| Beheergateway cloud<!-- 1101764 --> |  [Versie 1610](/sccm/core/clients/manage/plan-cloud-management-gateway) |![Nog niet](media/83c5d168-8faf-4e8e-920b-528e3c43ffd4.gif)|
| Microsoft Operations Management Suite-Connector<!-- 1236739 --> | [Versie 1606](../../../core/clients/manage/sync-data-microsoft-operations-management-suite.md) |![Nog niet](media/83c5d168-8faf-4e8e-920b-528e3c43ffd4.gif)|
| Onderhoud van een clusterbewuste verzameling (service een servergroep)<!-- 1081776 --> | [Versie 1602](../../../core/get-started/capabilities-in-technical-preview-1605.md#BKMK_ServerGroups)|![Nog niet](media/83c5d168-8faf-4e8e-920b-528e3c43ffd4.gif)|
| Voorwaardelijke toegang voor pc's die worden beheerd door System Center Configuration Manager<!--  --> | [Versie 1602](../../../protect/deploy-use/manage-access-to-o365-services-for-pcs-managed-by-sccm.md)     | [Versie 1702](/sccm/mdm/deploy-use/manage-access-to-services)                     |
