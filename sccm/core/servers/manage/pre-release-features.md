---
title: Pre-release functies
titleSuffix: Configuration Manager
description: Functies van evaluatieversies zijn functies die zich in de huidige vertakking voor vroege testdoeleinden in een productieomgeving.
ms.custom: na
ms.date: 04/10/2018
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 6bce416b-761d-4b23-bd33-5b7c30edb10d
caps.latest.revision: 36
author: aczechowski
ms.author: aaroncz
manager: dougeby
ms.openlocfilehash: 6e3a6a8dd437238a9dd08b07494b51333283f41c
ms.sourcegitcommit: fb84bcb31d825f454785e3d9d8be669e00fe2b27
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/16/2018
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


> [!Important]  
> U kunt alleen optionele of pre-release functies van de centrale beheersite in een hiërarchie met meerdere locaties inschakelen. Dit gedrag zorgt ervoor dat er zijn geen conflicten in de hiërarchie. <!--507197-->  
> Als u toestemming op een zelfstandige primaire site hebt opgegeven en vouw vervolgens de hiërarchie door een nieuwe centrale beheersite installeert, moet u toestemming op de centrale beheersite opnieuw.  

 Wanneer u een prerelease-functie inschakelt, moet de Configuration Manager-hiërarchie manager (HMAN) de wijziging verwerken voordat deze functie beschikbaar wordt. Verwerking van de wijziging is vaak onmiddellijke, maar duurt maximaal 30 minuten duren, afhankelijk van de HMAN verwerkingscyclus. Nadat de wijziging wordt verwerkt, moet u de console opnieuw opstarten voordat u de nieuwe gebruikersinterface die betrekking hebben op deze functie kunt weergeven.

**De volgende functies van evaluatieversies zijn beschikbaar:**

 |Onderdeel          |Als een voorlopige versie toegevoegd | Als een volledige functie toegevoegd|  
|------------------|---------------------|---------------------|
|Gefaseerde implementaties<!--1356837-->|[Versie 1802](/sccm/osd/deploy-use/create-phased-deployment-for-task-sequence.md)|![Nog niet](media/83c5d168-8faf-4e8e-920b-528e3c43ffd4.gif)|
| Takenreeksstap uitvoeren <!-- 1261338 --> |  [Versie 1710](/sccm/osd/understand/task-sequence-steps#child-task-sequence) |[Versie 1802](/sccm/osd/deploy-use/manage-task-sequences-to-automate-tasks#add-child-task-sequences-to-a-task-sequence)|
| Windows Defender misbruik Guard <!-- 1355468 --> |  [Versie 1710](/sccm/protect/deploy-use/create-deploy-exploit-guard-policy) |[Versie 1802](/sccm/protect/deploy-use/create-deploy-exploit-guard-policy)|
| Apparaat Health Attestation beoordeling van de beleidsregels voor naleving van voorwaardelijke toegang <!-- 1235616 --> |  [Versie 1710](/sccm/mdm/deploy-use/manage-access-to-o365-services-for-pcs-managed-by-sccm) |[Versie 1802](/sccm/mdm/deploy-use/manage-access-to-o365-services-for-pcs-managed-by-sccm)|
| Maken en PowerShell-scripts uitvoeren vanaf de Configuration Manager-console <!-- 1236459 --> |  [Versie 1706](/sccm/apps/deploy-use/create-deploy-scripts)|[Versie 1802](/sccm/apps/deploy-use/create-deploy-scripts)|
| Updates voor Microsoft Surface stuurprogramma's beheren <!-- 1098490 --> |  [Versie 1706](/sccm/sum/get-started/configure-classifications-and-products) | [Versie 1710](/sccm/sum/get-started/configure-classifications-and-products)|
| Guard Apparaatbeheer met Configuration Manager <!-- 1319346 --> |  [Versie 1702](/sccm/protect/deploy-use/use-device-guard-with-configuration-manager)|![Nog niet](media/83c5d168-8faf-4e8e-920b-528e3c43ffd4.gif)|
| Taak reeks vooraf inhoudcaching <!-- 1021244 --> |  [Versie 1702](/sccm/osd/deploy-use/create-a-task-sequence-to-upgrade-an-operating-system#configure-pre-cache-content) | [Versie 1710](/sccm/osd/deploy-use/create-a-task-sequence-to-upgrade-an-operating-system#configure-pre-cache-content)|
| Controleer voor het uitvoeren van uitvoerbare bestanden voordat u een toepassing installeert <!-- 1284624 --> |   [Versie 1702](/sccm/apps/deploy-use/deploy-applications#how-to-check-for-running-executable-files-before-installing-an-application) |[Versie 1706](/sccm/apps/deploy-use/deploy-applications#how-to-check-for-running-executable-files-before-installing-an-application)|
| Datawarehouse-servicepunt <!-- 1277922 --> |  [Versie 1702](/sccm/core/servers/manage/data-warehouse) |[Versie 1706](/sccm/core/servers/manage/data-warehouse)|
| Peer-Cache voor de distributie van inhoud aan clients <!-- 1101436 --> |  [Versie 1610](/sccm/core/plan-design/hierarchy/client-peer-cache) | [Versie 1710](/sccm/core/plan-design/hierarchy/client-peer-cache)|
| Beheergateway cloud <!-- 1101764 --> |  [Versie 1610](/sccm/core/clients/manage/plan-cloud-management-gateway) |[Versie 1802](/sccm/core/clients/manage/plan-cloud-management-gateway)|
| Microsoft Operations Management Suite-Connector <!-- 1236739 --> | [Versie 1606](../../../core/clients/manage/sync-data-microsoft-operations-management-suite.md) |[Versie 1802](../../../core/clients/manage/sync-data-microsoft-operations-management-suite.md)|
| Onderhoud van een clusterbewuste verzameling (service een servergroep) <!-- 1081776 --> | [Versie 1602](../../../core/get-started/capabilities-in-technical-preview-1605.md#BKMK_ServerGroups)|![Nog niet](media/83c5d168-8faf-4e8e-920b-528e3c43ffd4.gif)|
| Voorwaardelijke toegang voor pc's die worden beheerd door System Center Configuration Manager <!--  --> | [Versie 1602](/sccm/mdm/deploy-use/manage-access-to-o365-services-for-pcs-managed-by-sccm)     | [Versie 1702](/sccm/mdm/deploy-use/manage-access-to-o365-services-for-pcs-managed-by-sccm)                     |
<!--Image used = ![Not yet](media/83c5d168-8faf-4e8e-920b-528e3c43ffd4.gif) -->

> [!Tip]  
> Zie voor meer informatie over pre release functies waarmee u moet eerst [optionele functies van updates inschakelen](/sccm/core/servers/manage/install-in-console-updates#bkmk_options).  
> Zie voor meer informatie over functies die alleen beschikbaar in de technische preview vertakking [Technical Preview](/sccm/core/get-started/technical-preview).  
