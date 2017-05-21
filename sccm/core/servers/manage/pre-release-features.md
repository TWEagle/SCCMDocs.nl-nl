---
title: Voorlopige functies | Microsoft-documenten
description: Pre-release functies in System Center Configuration Manager
ms.custom: na
ms.date: 4/24/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 6bce416b-761d-4b23-bd33-5b7c30edb10d
caps.latest.revision: 36
author: Brenduns
ms.author: brenduns
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 690d03d9c8c49a815bd318df549d7401a855bc5d
ms.openlocfilehash: b12fcb3c372c34ee47306a9b536c3d0c4764b8be
ms.contentlocale: nl-nl
ms.lasthandoff: 05/17/2017


---
# <a name="pre-release-features-in-system-center-configuration-manager"></a>Pre-release functies in System Center Configuration Manager
*Van toepassing op: System Center Configuration Manager (huidige vertakking)*

Pre-release functies zijn kenmerken die zijn opgenomen in de huidige vertakking voor vroege te testen in een productieomgeving. Ze worden volledig ondersteund, maar zijn nog in ontwikkeling active en ontvangt, kunnen wijzigingen totdat ze worden verplaatst uit de categorie voorlopige versie.

 Voordat u pre-release functies gebruiken kunt, moet u toestemming geven pre-release om functies te gebruiken van binnen de Configuration Manager-console voordat u kunt selecteren en hun gebruik inschakelen.  

Toestemming te geven, is een eenmalige bewerking per hiërarchie die niet ongedaan worden gemaakt. Totdat u toestemming geeft, kunt u nieuwe pre-release functies met updates niet inschakelen.

Als u wilt toestemming geven, in de console gaat u naar **beheer** > **siteconfiguratie** > **Sites**, en kies vervolgens **hiërarchie-instellingen**. Op de **algemeen** Kies **instemming met gebruik van pre-release functies**.

 > [!NOTE]
 > Als u hebt eerder pre-release functies van 1602 bijwerken ingeschakeld voordat u een latere updateversie installeert, die functies blijft ingeschakeld voor gebruik, zelfs als u geen toestemming geven om pre-release functies te gebruiken.

Wanneer u een update die voorlopige functies bevat installeert, zijn die functies zichtbaar in de Wizard Onderhoud en -Updates met de reguliere kenmerken die zijn opgenomen in de update:
  - **Als u toestemming hebt gegeven:** U kunt de voorlopige functies uit vanuit de Wizard Onderhoud en Updates inschakelen tijdens de installatie van de update. Hiervoor selecteert u de functies van de voorlopige versie, net zoals u met andere functies doet.     

    Eventueel wachten om in te schakelen van een voorlopige versie functie later vanuit de **beheer** > **Updates en onderhoud** > **functies** knooppunt van de console. In de **functies** knooppunt de functie en kies **inschakelen**. Deze optie is niet beschikbaar totdat u toestemming geeft. (Voor versie 1702 Updates en onderhoud is onder **beheer** > **Cloudservices**.)
  -   **Als u geen toestemming hebt gegeven:** Wanneer u een update installeert, pre-release functies zichtbaar zijn in de Wizard Onderhoud en Updates, maar zijn niet beschikbaar en kunnen niet worden ingeschakeld. Nadat de update is geïnstalleerd, kunt u zien hoe deze functies in de **functies** knooppunt, maar niet inschakelen pas nadat u toestemming hebt gegeven **hiërarchie-instellingen**.

Als u toestemming op een zelfstandige primaire site hebt gegeven en vouw vervolgens de hiërarchie door een nieuwe centrale beheersite installeert, geeft u toestemming opnieuw op de centrale beheersite.

 Wanneer u een prerelease-functie inschakelt, moet de Configuration Manager-hiërarchie manager (HMAN) de wijziging verwerken voordat deze functie beschikbaar is. Verwerking van de wijziging is vaak onmiddellijke kan, maar het duren tot 30 minuten duren, afhankelijk van de HMAN-mailverwerkingscyclus. Nadat de wijziging wordt verwerkt, moet u de console opnieuw opstarten voordat u de nieuwe gebruikersinterface aan die functies gerelateerde kunt weergeven.

**De volgende pre-release functies zijn beschikbaar:**

 |Onderdeel          |Toegevoegd als voorlopige versie | Als een volledige functie toegevoegd|  
|------------------|---------------------|---------------------|
| Beveiliging Apparaatbeheer met Configuration Manager |  [Versie 1702](/sccm/protect/deploy-use/use-device-guard-with-configuration-manager)|![Nog niet](media/83c5d168-8faf-4e8e-920b-528e3c43ffd4.gif)|
| Controleer voor het uitvoeren van uitvoerbare bestanden voordat de installatie van een toepassing  |   [Versie 1702](/sccm/apps/deploy-use/deploy-applications#how-to-check-for-running-executable-files-before-installing-an-application) |![Nog niet](media/83c5d168-8faf-4e8e-920b-528e3c43ffd4.gif)|
| Gegevens datawarehouse-servicepunt  |  [Versie 1702](/sccm/core/servers/manage/data-warehouse) |![Nog niet](media/83c5d168-8faf-4e8e-920b-528e3c43ffd4.gif)|
| Peercache voor de distributie van inhoud naar clients |  [Versie 1610](/sccm/core/plan-design/hierarchy/client-peer-cache) |![Nog niet](media/83c5d168-8faf-4e8e-920b-528e3c43ffd4.gif)|
| Cloud management gateway |  [Versie 1610](/sccm/core/clients/manage/plan-cloud-management-gateway) |![Nog niet](media/83c5d168-8faf-4e8e-920b-528e3c43ffd4.gif)|
| Client-gegevensbronnen dashboard |  [Versie 1610](/sccm/core/servers/deploy/configure/monitor-content-you-have-distributed#client-data-sources-dashboard) |![Nog niet](media/83c5d168-8faf-4e8e-920b-528e3c43ffd4.gif)|
| Connector voor Microsoft Operations Management-pakket  | [Versie 1606](../../../core/clients/manage/sync-data-microsoft-operations-management-suite.md) |![Nog niet](media/83c5d168-8faf-4e8e-920b-528e3c43ffd4.gif)|
| Onderhoud van een cluster op de hoogte-verzameling (service een servergroep)| [Versie 1602](../../../core/get-started/capabilities-in-technical-preview-1605.md#BKMK_ServerGroups)|![Nog niet](media/83c5d168-8faf-4e8e-920b-528e3c43ffd4.gif)|
|Voorwaardelijke toegang voor pc's die worden beheerd door System Center Configuration Manager | [Versie 1602](../../../protect/deploy-use/manage-access-to-o365-services-for-pcs-managed-by-sccm.md)     | [Versie 1702](/sccm/mdm/deploy-use/manage-access-to-services)                     |

