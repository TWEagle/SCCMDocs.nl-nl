---
title: Ondersteuning voor Windows 10 | Microsoft-documenten
description: Meer informatie over de Windows-10-versies die worden ondersteund als clients of voor OSD met System Center Configuration Manager.
ms.custom: na
ms.date: 05/09/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: a1626a65-da22-49e0-9564-d2f752ea3f4b
caps.latest.revision: 5
author: brenduns
ms.author: brenduns
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: f809c9327db9f298168674add2d09820fdecd1b8
ms.openlocfilehash: ed5efcf7b305f8bee6e99e00c5285f6ae7033d82
ms.contentlocale: nl-nl
ms.lasthandoff: 05/17/2017

---
# <a name="support-for-windows-10-for-system-center-configuration-manager"></a>Ondersteuning voor Windows 10 voor System Center Configuration Manager  

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*


 In dit onderwerp wordt de versies van Windows 10 die u met de verschillende versies van System Center Configuration Manager huidige vertakking wordt weergegeven gebruiken kunt. Dit omvat:
 -  Windows 10 als Configuration Manager-client.
 -  De Windows 10 Windows Assessment and Deployment Kit (ADK).

## <a name="windows-10-as-a-client"></a>Windows 10 als een client
Configuration Manager probeert om ondersteuning te verlenen als een client voor elke nieuwe versie van Windows 10 zo snel mogelijk na die versie van Windows worden vrijgegeven. Omdat de producten afzonderlijke ontwikkeling en release planningen, de ondersteuning van Configuration Manager, hangt af van de versies en vertakkingen van elk product versie te bieden.

Bijvoorbeeld, een Configuration Manager-versie wordt niet verwijderen uit de matrix na [ondersteuning voor die versie](/sccm/core/servers/manage/current-branch-versions-supported) eindigt. Ondersteuning voor versies van Windows 10 zoals het Enterprise 2015 LTSB of 1607 (CBB) wordt op dezelfde manier verwijderen uit de matrix wanneer ze zijn verwijderd uit de lijst met ondersteunde configuraties van Configuration Manager. Zie [afgeschaft besturingssystemen](/sccm/core/plan-design/changes/removed-and-deprecated-features#deprecated-operating-systems) voor meer informatie.

-   De volgende informatie aanvullingen [ondersteunde besturingssystemen voor clients en apparaten](/sccm/core/plan-design/configs/supported-operating-systems-for-clients-and-devices).
-   Als u de langetermijndoelen onderhoud vertakking van Configuration Manager gebruikt, Zie [ondersteunde configuraties voor de vertakking langetermijndoelen onderhoud](/sccm/core/understand/supported-configurations-for-ltsb).

|Versies van Windows 10                    |Configuration Manager 1606          |Configuration Manager 1610          |    Configuration Manager 1702 |
|---------------------|-----|-----|-----|
|Enterprise 2015 LTSB                   |![Ondersteund](media/green_check.png) |![Ondersteund](media/green_check.png) |![Ondersteund](media/green_check.png) |
|1507 <br />(*edities Zie*)            |![Ondersteund](media/green_check.png) |![Ondersteund](media/green_check.png) |![Ondersteund](media/green_check.png) |
|1511 (CB) (CBB)<br />(*edities Zie*) |![Ondersteund](media/green_check.png) |![Ondersteund](media/green_check.png) |![Ondersteund](media/green_check.png) |
|Enterprise 2016 LTSB                   |![Ondersteund](media/green_check.png) |![Ondersteund](media/green_check.png) |![Ondersteund](media/green_check.png) |
|1607 (CB)    <br />Verjaardag Update<br />(*edities Zie*)      |![Achterwaarts compatibele](media/blue_compat.png) |![Ondersteund](media/green_check.png) |![Ondersteund](media/green_check.png) |
|1607 (CBB)    <br />Verjaardag Update<br />(*edities Zie*)      |![Niet ondersteund](media/Red_X.png)   |![Ondersteund](media/green_check.png) |![Ondersteund](media/green_check.png) |
|1703 (CB)    <br />Beveiligingsbeheerder bijwerken<br />(*edities Zie*)      |![Niet ondersteund](media/Red_X.png)   |![Niet ondersteund](media/Red_X.png) |![Achterwaarts compatibele](media/blue_compat.png) |


**De volgende versies:** Enterprise, Pro, onderwijs, Pro onderwijs   

|Sleutel|
|--|
|![Ondersteund](media/green_check.png) = **ondersteund**  |
|![Niet ondersteund](media/blue_compat.png)  = **Backwards compatibele** -dit betekent dat de bestaande client-functies (hardware-inventaris, software-inventaris, software-updates, enzovoort) met de nieuwe Windows 10 huidige vertakking build samen moeten. Bekende problemen of waarschuwingen worden aangegeven. <br><br>Deze aanpak geeft u de mogelijkheid om te implementeren en beheren van de nieuwe Windows 10 CB borduurt op dag één met ondersteuning voor compatibiliteit van toepassingen voort zonder een nieuwe updateversie van de Configuration Manager. |
|![Ondersteund](media/Red_X.png) = **niet ondersteund**|


## <a name="windows-10-adk"></a>Windows 10 ADK
Wanneer u besturingssystemen met Configuration Manager implementeert de [Windows ADK is een externe afhankelijkheid](/sccm/osd/plan-design/infrastructure-requirements-for-operating-system-deployment) die is vereist.

De volgende tabel worden de versies van Windows 10 ADK die u met verschillende versies van Configuration Manager gebruiken kunt.

|Versies van Windows 10 ADK |Configuration Manager 1606 |Configuration Manager 1610  |Configuration Manager 1702 |
|--------------------|-----|-----|-----|
|1507  |![Niet ondersteund](media/Red_X.png)         |![Niet ondersteund](media/Red_X.png)  |![Niet ondersteund](media/Red_X.png)|
|1511  |![Achterwaarts compatibele](media/blue_compat.png)|![Niet ondersteund](media/Red_X.png)  |![Niet ondersteund](media/Red_X.png)|
|1607  |![Ondersteund](media/green_check.png)       |![Ondersteund](media/green_check.png)|![Achterwaarts compatibele](media/blue_compat.png) |
|1703  |![Niet ondersteund](media/Red_X.png)         |![Niet ondersteund](media/Red_X.png)  |![Ondersteund](media/green_check.png) |  

|Sleutel|
|--|
|![Ondersteunde](media/green_check.png) = **ondersteunde** - Windows raadt met behulp van de Windows-ADK die overeenkomt met de versie van Windows die u implementeert. De Windows ADK voor Windows 10 versie 1703 bijvoorbeeld gebruiken bij het implementeren van Windows 10 versie 1703.  |
|![Achterwaarts compatibele](media/blue_compat.png)  = **achterwaarts compatibele** -deze combinatie is niet getest maar moet werken. Bekende problemen of waarschuwingen worden aangegeven. |
|![Ondersteund](media/Red_X.png) = **niet ondersteund**|

