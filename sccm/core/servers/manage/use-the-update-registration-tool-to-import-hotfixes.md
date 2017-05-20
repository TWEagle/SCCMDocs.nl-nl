---
title: Bijwerken van de registratie van | Microsoft-documenten
description: Ontdek wanneer en hoe u de update registratie-hulpprogramma te gebruiken om een update handmatig te importeren naar de Configuration Manager-console.
ms.custom: na
ms.date: 3/27/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 8cc13635-85d6-4b07-a3ec-c42188bc5c74
caps.latest.revision: 8
author: Brenduns
ms.author: brenduns
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: dab5da5a4b5dfb3606a8a6bd0c70a0b21923fff9
ms.openlocfilehash: 35a4c201f73469fdfaa5bb8629e91886f7ae8751
ms.contentlocale: nl-nl
ms.lasthandoff: 05/17/2017


---
# <a name="use-the-update-registration-tool-to-import-hotfixes-to-system-center-configuration-manager"></a>Gebruik het hulpprogramma Registratie bijwerken om hotfixes te importeren naar System Center Configuration Manager

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*

Sommige updates voor Configuration Manager zijn niet beschikbaar is via het Microsoft-cloudservice en out-of-band alleen worden verkregen. Een voorbeeld is een beperkt uitgegeven hotfix voor een specifiek probleem.   
Wanneer u een out-of-band-versie moet installeren en de bestandsnaam update of hotfix eindigt met de extensie **update.exe**, u de **update registratiehulpprogramma** om de update handmatig te importeren naar de Configuration Manager-console. Met het hulpprogramma kunt u het updatepakket uitpakken en overdragen naar de siteserver en de update registreren bij de Configuration Manager-console.  

 Als de hotfixbestand heeft de **.exe** bestandsextensie (niet **update.exe**), Zie [de Hotfix-installatieprogramma gebruiken om updates te installeren voor System Center Configuration Manager](../../../core/servers/manage/use-the-hotfix-installer-to-install-updates.md)  

> [!NOTE]  
>  In dit onderwerp biedt algemene richtlijnen over het installeren van hotfixes om System Center Configuration Manager bij te werken. Raadpleeg de corresponderende Knowledge Base (KB) artikel op Microsoft Support voor meer informatie over een specifieke hotfix of update.  

 **Vereisten voor het gebruik van het hulpprogramma Registratie bijwerken:**  

-   Alleen out-of-band-updates die eindigen op de **. update.exe** extensie kan worden geïnstalleerd met dit hulpprogramma  

-   Het hulpprogramma is ingesloten met de afzonderlijke updates die u rechtstreeks van Microsoft verkrijgen  

-   Het hulpprogramma is niet afhankelijk van de modus van het serviceaansluitpunt  

-   Het hulpprogramma moet worden uitgevoerd op de computer die het serviceaansluitpunt host  

-   De computer waarop het hulpprogramma wordt uitgevoerd (de service connection point-computer) moet de .NET Framework 4.52 geïnstalleerd hebben  

-   Het account waarmee u het hulpprogramma uit te voeren moet hebben **lokale beheerder** machtigingen op de computer die als host fungeert voor de service connection point (waarop het hulpprogramma wordt uitgevoerd)  

-   Het account waarmee u het hulpprogramma uit te voeren moet hebben **schrijven** machtigingen op de volgende map op de computer die als host fungeert voor de service connection point:  **&lt;Configuration Manager-installatiemap\>\EasySetupPayload\offline**  

### <a name="to-use-the-update-registration-tool"></a>Het hulpprogramma Registratie bijwerken gebruiken  

1.  Op de computer die het serviceverbindingspunt host:  

    -   Open een opdrachtprompt met beheerdersbevoegdheden en wijzig de mappen in de locatie waarin  **&lt;Product\>-&lt;productversie\>-&lt;KB-artikel-ID\>-ConfigMgr.Update.exe**  

2.  Voer de volgende opdracht uit om het hulpprogramma Registratie bijwerken te openen:  

    -   **&lt;Product\>-&lt;productversie\>-&lt;KB-artikel-ID\>-ConfigMgr.Update.exe**  

    Wanneer de hotfix is geregistreerd, wordt deze binnen 24 uur weergegeven als nieuwe update in de console.  U kunt het proces versnellen:

    - Open de Configuration Manager-console en Ga naar naar **beheer** > **Updates en onderhoud**, en klik vervolgens op **controleren op Updates**. (Voor versie 1702 Updates en onderhoud is onder **beheer** > **Cloudservices**.) 

    Het hulpprogramma Registratie bijwerken registreert de uitgevoerde bewerkingen in een logboekbestand op de lokale computer. Het logboekbestand is met dezelfde naam als de hotfix .exe-bestand en wordt geschreven naar de **%SystemRoot%/Temp** map.  

     Wanneer de update is geregistreerd, kunt u het hulpprogramma Registratie bijwerken sluiten.  

3.  Open de Configuration Manager-console en navigeer naar **beheer** > **Updates en onderhoud**. De geïmporteerde hotfixes kunnen nu worden geïnstalleerd. (Voor versie 1702 Updates en onderhoud is onder **beheer** > **Cloudservices**.)

 Zie voor meer informatie over het installeren van updates [-console updates installeren voor System Center Configuration Manager](../../../core/servers/manage/install-in-console-updates.md)  

