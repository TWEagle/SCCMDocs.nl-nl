---
title: Configuratiebasislijnen maken | Microsoft-documenten
description: Configuratiebasislijnen in System Center Configuration Manager die u op een verzameling implementeren kunt maken.
ms.custom: na
ms.date: 10/06/2016
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 678c9622-c61b-47d1-ba25-690616e431c7
caps.latest.revision: 5
caps.handback.revision: 0
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: f9e939d871e95a3248d8e5d96cb73063a81fd5cf
ms.openlocfilehash: 649942d3d468ec35c7246e08f741cdebd22fb3ac
ms.contentlocale: nl-nl
ms.lasthandoff: 05/17/2017


---
# <a name="create-configuration-baselines-in-system-center-configuration-manager"></a>Configuratiebasislijnen maken in System Center Configuration Manager

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*


Configuratiebasislijnen in System Center Configuration Manager bevat vooraf gedefinieerde configuratie-items en eventueel andere configuratiebasislijnen. Nadat u een configuratiebasislijn hebt gemaakt, kunt u deze implementeren bij een verzameling, zodat apparaten in die verzameling de configuratiebasislijn downloaden en naleving ervan beoordelen.  

 Basislijnen in Configuration Manager kunnen bevatten die specifiek revisies van configuratie-items of kunnen worden geconfigureerd voor gebruik altijd de nieuwste versie van een configuratie-item. Zie voor meer informatie over configuratie-item revisies [beheertaken voor configuratiegegevens](../../compliance/deploy-use/management-tasks-for-configuration-data.md).  

 Er zijn twee methoden die u gebruiken kunt om configuratiebasislijnen maken:  

-   Configuratiegegevens uit een bestand importeren. Als u de **Wizard Configuratiegegevens importeren**wilt starten, moet u in het knooppunt **Configuratie-items** of **Configuratiebasislijnen** in de werkruimte **Activa en naleving** op **Configuratiegegevens importeren**klikken.  

-   Gebruik het dialoogvenster **Configuratiebasislijn maken** om een nieuwe configuratiebasislijn te maken.  

 Volg de volgende procedure om een configuratiebasislijn te maken in het dialoogvenster **Configuratiebasislijn maken** .  

1.  Klik in de Configuration Manager-console op **activa en naleving** > **compatibiliteitsinstellingen** > **Configuratiebasislijnen**.  

3.  Klik op het tabblad **Start** in de groep **Maken** op **Configuratiebasislijn maken**.  

4.  Voer in het dialoogvenster **Configuratiebasislijn maken** een unieke naam en een beschrijving voor de configuratiebasislijn in. U kunt maximaal 255 tekens voor de naam en 512 tekens voor de beschrijving gebruiken.  

5.  De lijst **Configuratiegegevens** geeft alle configuratie-items of configuratiebasislijnen weer die in deze configuratiebasislijn zijn opgenomen. Klik op **Toevoegen** om een nieuw configuratie-item of een nieuwe configuratiebasislijn toe te voegen aan de lijst. U kunt kiezen uit de volgende mogelijkheden:  

    -   **Configuratie-items**  

    -   **Software-updates**  

    -   **Configuratiebasislijnen**  
      > [!IMPORTANT]
      > U moet elke configuratiebasislijn om niet meer dan 1000 software-updates te beperken.
6.  Gebruik de lijst **Doel wijzigen** om het gedrag te bepalen van een configuratie-item dat u in de lijst **Configuratiegegevens** hebt geselecteerd. U kunt het volgende selecteren:  

    -   **Vereist** De configuratiebasislijn wordt beoordeeld als niet-compatibel als het configuratie-item niet op een clientapparaat wordt gedetecteerd. Als dit wel wordt gedetecteerd, wordt naleving beoordeeld  

    -   **Optioneel** Het configuratie-item wordt alleen op naleving beoordeeld als de toepassing waarnaar wordt verwezen op clientcomputers is gevonden. Als de toepassing niet is gevonden, wordt de configuratiebasislijn niet gemarkeerd als niet-compatibel (alleen van toepassing op configuratie-items van toepassingen).  

    -   **Verboden** De configuratiebasislijn wordt beoordeeld als niet-compatibel als het configuratie-item wordt gedetecteerd op clientcomputers (alleen van toepassing op configuratie-items van toepassingen).  

    > [!NOTE]
    >  De lijst **Doel wijzigen** is alleen beschikbaar als u op de optie **Dit configuratie-item bevat toepassingsinstellingen** hebt geklikt op de pagina **Algemeen** van de **Wizard Configuratie-item maken**.  

7.  Gebruik de lijst **Herziening wijzigen** om een specifieke of de nieuwste herziening van het configuratie-item te selecteren om te beoordelen op naleving op clientapparaten, of selecteer **Altijd nieuwste gebruiken** om altijd de nieuwste herziening te gebruiken. Zie voor meer informatie over configuratie-item revisies [beheertaken voor configuratiegegevens](../../compliance/deploy-use/management-tasks-for-configuration-data.md).  

8.  Als een configuratie-item uit de configuratiebasislijn wilt verwijderen, selecteert u een configuratie-item en klik vervolgens op **verwijderen**.  

9. Klik op **OK** om het dialoogvenster **Configuratiebasislijn maken** te sluiten en de configuratiebasislijn te maken.  

