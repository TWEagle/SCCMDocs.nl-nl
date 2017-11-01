---
title: Pre-release functies
titleSuffix: Configuration Manager
description: Functies van evaluatieversies in System Center Configuration Manager
ms.custom: na
ms.date: 7/31/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 6bce416b-761d-4b23-bd33-5b7c30edb10d
caps.latest.revision: "36"
author: Brenduns
ms.author: brenduns
manager: angrobe
ms.openlocfilehash: 6d7ec308aa465f2b715ce51b8c6bbbe59faaf2cb
ms.sourcegitcommit: b36f8c8b06e4b2e13f8c1500a82af79a071ab4f6
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/20/2017
---
# <a name="pre-release-features-in-system-center-configuration-manager"></a>Functies van evaluatieversies in System Center Configuration Manager
*Van toepassing op: System Center Configuration Manager (huidige vertakking)*

Functies van evaluatieversies zijn functies die zich in de huidige vertakking voor vroege testdoeleinden in een productieomgeving. Deze functies worden volledig ondersteund maar nog in ontwikkeling actief zijn en wijzigingen mogelijk ontvangen totdat ze worden verplaatst buiten de categorie van de voorlopige versie.

 Voordat u de functies van evaluatieversies gebruiken kunt, moet u toestemming geven om te gebruiken pre-release functies vanuit de Configuration Manager-console voordat u kunt selecteren en het gebruik ervan.  

Toestemming verlenen is een eenmalige handeling per hiërarchie die niet ongedaan worden gemaakt. Totdat u toestemming geeft, kunt u nieuwe functies van evaluatieversies opgenomen met updates niet inschakelen. Nadat u een prerelease-functie inschakelt, kan u deze uitschakelen.

Als u toestemming geven, in de console gaat u naar **beheer** > **siteconfiguratie** > **Sites**, en kies vervolgens **hiërarchie-instellingen**. Op de **algemene** Kies **instemming met gebruik van functies van evaluatieversies**.

 > [!NOTE]
 > Als u functies van evaluatieversies van Update 1602 ingeschakeld voordat u een nieuwere updateversie hebt geïnstalleerd, deze functies zijn ingeschakeld voor gebruik, zelfs als u geen toestemming om functies van voorlopige versie te gebruiken.

Wanneer u een update die functies van evaluatieversies bevat installeert, zijn die functies zichtbaar in de Wizard Updates en onderhoud met de normale functies in de update:
  - **Als u toestemming hebt gegeven:** Wanneer u de update installeert, kunt u functies van evaluatieversies van in de Wizard Updates en onderhoud inschakelen. Hiervoor selecteert u de functies van de voorlopige versie, net zoals u met andere functies doet.     

    U kunt eventueel wachten met een voorlopige versie inschakelen vanuit de **beheer** > **Updates en onderhoud** > **functies** knooppunt van de console. In de **functies** knooppunt de functie en kies **inschakelen**. Deze optie is niet beschikbaar totdat u toestemming. (Voorafgaand aan versie 1702, Updates en onderhoud is onder **beheer** > **Cloudservices**.)
  -   **Als u geen toestemming hebt gegeven:** Wanneer u een update installeert, functies van evaluatieversies zichtbaar zijn in de Wizard Updates en onderhoud, maar zijn niet beschikbaar en kunnen niet worden ingeschakeld. Nadat de update is geïnstalleerd, kunt u zien hoe deze functies in de **functies** knooppunt. Echter, u ze niet inschakelen totdat nadat u toestemming hebt gegeven **hiërarchie-instellingen**.

Als u toestemming op een zelfstandige primaire site hebt opgegeven en vouw vervolgens de hiërarchie door een nieuwe centrale beheersite installeert, moet u toestemming op de centrale beheersite opnieuw.

 Wanneer u een prerelease-functie inschakelt, moet de Configuration Manager-hiërarchie manager (HMAN) de wijziging verwerken voordat deze functie beschikbaar wordt. Verwerking van de wijziging is vaak onmiddellijke, maar duurt maximaal 30 minuten duren, afhankelijk van de HMAN verwerkingscyclus. Nadat de wijziging wordt verwerkt, moet u de console opnieuw opstarten voordat u de nieuwe gebruikersinterface die betrekking hebben op deze functie kunt weergeven.

**De volgende functies van evaluatieversies zijn beschikbaar:**

 |Onderdeel          |Als een voorlopige versie toegevoegd | Als een volledige functie toegevoegd|  
|------------------|---------------------|---------------------|
| Maken en PowerShell-scripts uitvoeren vanaf de Configuration Manager-console |  [Versie 1706](/sccm/apps/deploy-use/create-deploy-scripts)|![Nog niet](media/83c5d168-8faf-4e8e-920b-528e3c43ffd4.gif)|
| Guard Apparaatbeheer met Configuration Manager |  [Versie 1702](/sccm/protect/deploy-use/use-device-guard-with-configuration-manager)|![Nog niet](media/83c5d168-8faf-4e8e-920b-528e3c43ffd4.gif)|
| Controleer voor het uitvoeren van uitvoerbare bestanden voordat u een toepassing installeert  |   [Versie 1702](/sccm/apps/deploy-use/deploy-applications#how-to-check-for-running-executable-files-before-installing-an-application) |[Versie 1706](/sccm/apps/deploy-use/deploy-applications#how-to-check-for-running-executable-files-before-installing-an-application)|
| Datawarehouse-servicepunt  |  [Versie 1702](/sccm/core/servers/manage/data-warehouse) |[Versie 1706](/sccm/core/servers/manage/data-warehouse)|
| Peer-Cache voor de distributie van inhoud aan clients |  [Versie 1610](/sccm/core/plan-design/hierarchy/client-peer-cache) |![Nog niet](media/83c5d168-8faf-4e8e-920b-528e3c43ffd4.gif)|
| Beheergateway cloud |  [Versie 1610](/sccm/core/clients/manage/plan-cloud-management-gateway) |![Nog niet](media/83c5d168-8faf-4e8e-920b-528e3c43ffd4.gif)|
| Client gegevensbronnen dashboard |  [Versie 1610](/sccm/core/servers/deploy/configure/monitor-content-you-have-distributed#client-data-sources-dashboard) |![Nog niet](media/83c5d168-8faf-4e8e-920b-528e3c43ffd4.gif)|
| Microsoft Operations Management Suite-Connector  | [Versie 1606](../../../core/clients/manage/sync-data-microsoft-operations-management-suite.md) |![Nog niet](media/83c5d168-8faf-4e8e-920b-528e3c43ffd4.gif)|
| Onderhoud van een clusterbewuste verzameling (service een servergroep)| [Versie 1602](../../../core/get-started/capabilities-in-technical-preview-1605.md#BKMK_ServerGroups)|![Nog niet](media/83c5d168-8faf-4e8e-920b-528e3c43ffd4.gif)|
|Voorwaardelijke toegang voor pc's die worden beheerd door System Center Configuration Manager | [Versie 1602](../../../protect/deploy-use/manage-access-to-o365-services-for-pcs-managed-by-sccm.md)     | [Versie 1702](/sccm/mdm/deploy-use/manage-access-to-services)                     |
