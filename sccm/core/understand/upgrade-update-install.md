---
title: Over de upgrade, update en installeer | Microsoft-documenten
description: Informatie over het verschil tussen de voorwaarden installeren, bijwerken en Upgrade bij het beheren van Configuration Manager-infrastructuur.
ms.custom: na
ms.date: 1/11/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 17fab17f-304d-4f6a-87c7-30ab4f5521ed
caps.latest.revision: 0
caps.handback.revision: 0
author: Brenduns
ms.author: brenduns
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 0d0735c170820259ac8bb6706aac7cc5569a1628
ms.openlocfilehash: 6bd6cd7ea3c41fa1d70e17a1290c9f1f74cc9e37
ms.contentlocale: nl-nl
ms.lasthandoff: 05/17/2017

---

# <a name="about-upgrade-update-and-install-for-site-and-hierarchy-infrastructure"></a>Over de upgrade, bijwerken en installeren voor de site en hiërarchie-infrastructuur

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*


Bij het beheren van System Center Configuration Manager-site en hiërarchie-infrastructuur, de voorwaarden *upgrade*, *bijwerken*, en *installeren* worden gebruikt om te beschrijven van drie verschillende concepten.

## <a name="upgrade"></a>Upgrade
*Upgrade* of *upgrade ter plaatse*, wordt gebruikt bij het converteren van uw Configuration Manager 2012-site of hiërarchie naar een System Center Configuration Manager wordt uitgevoerd.
Wanneer u System Center 2012 Configuration Manager naar System Center Configuration Manager upgraden, blijven u dezelfde servers gebruiken voor het hosten van uw sites en siteservers en u uw bestaande gegevens en configuraties voor Configuration Manager behoudt.  Dit wijkt af van [migratie](/sccm/core/migration/migrate-data-between-hierarchies) die is een manier om uw configuraties en gegevens over beheerde apparaten behouden tijdens het gebruik van nieuwe System Center Configuration Manager-sites naar nieuwe hardware is geïnstalleerd.

Zie voor meer informatie [upgraden naar System Center Configuration Manager](/sccm/core/servers/deploy/install/upgrade-to-configuration-manager).



## <a name="update"></a>Update
*Update* wordt gebruikt voor het installeren van updates in de console voor System Center Configuration Manager, en voor out-of-band-updates updates die van kan niet worden bezorgd binnen de Configuration Manager-console. In de console-updates kunnen de versie van uw huidige vertakking site (of technische Preview van site) zo wijzigen dat deze een hogere versie wordt uitgevoerd. Bijvoorbeeld, u als uw site versie 1606 uitvoert, kunt u een update voor versie 1610 installeren. Updates kunnen oplossingen voor een bekend probleem ook installeren zonder het wijzigen van de versie van de sites.      

Normaal gesproken toevoegen updates beveiligingsverbeteringen, kwaliteitsverbetering en nieuwe functies voor uw bestaande implementatie. Als u de vertakking Technical Preview, kan een update een nieuwere versie van de technische Preview kunt installeren.
-    U bepaalt wanneer de update console installeren vanaf de site op hoogste niveau van uw hiërarchie.
- U kunt de updates die beschikbaar is via de console installeren. Bijvoorbeeld, als uw site wordt uitgevoerd op versie 1602 en 1606 en 1610 worden aangeboden, u moet rekening houden met versie 1610 installeren omdat elke versie bevat de functies die voor het eerst werden beschikbaar gesteld in eerder uitgebrachte versies.
- Nadat de installatie op de bovenste site van een nieuwe update is voltooid, wordt het proces om bij te werken automatisch starten door onderliggende primaire sites. U kunt echter instellen [Service Windows](/sccm/core/servers/manage/install-in-console-updates#a-namebkmkservicewindowa-service-windows-for-site-servers) voor het beheren van de timing van updates.
- Secundaire sites installeren niet automatisch updates. In plaats daarvan, start u handmatig de update uit in de Configuration Manager-console.

Zie voor meer [Updates voor System Center Configuration Manager](/sccm/core/servers/manage/updates), en [Technical Preview voor System Center Configuration Manager](/sccm/core/get-started/technical-preview).



## <a name="install"></a>Installeren
*Installeer* wordt gebruikt bij een nieuwe Configuration Manager-hiërarchie helemaal maken en aanvullende sites toevoegen aan een bestaande hiërarchie.  

De locatie van setup.exe en de bijbehorende bronbestanden die u gebruikt wanneer u een nieuwe primaire site of centrale beheersite installeert, zijn afhankelijk van uw installatie uit te voeren.

Zie voor meer [voorbereiden om sites te installeren](/sccm/core/servers/deploy/install/prepare-to-install-sites).

