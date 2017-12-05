---
title: Ondersteuning voor Windows 10
titleSuffix: Configuration Manager
description: Meer informatie over de versies van Windows 10 die worden ondersteund als clients of voor OSD met System Center Configuration Manager.
ms.custom: na
ms.date: 11/20/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: a1626a65-da22-49e0-9564-d2f752ea3f4b
caps.latest.revision: "5"
author: mestew
ms.author: mstewart
manager: angrobe
ms.openlocfilehash: b2cacddfbd94340c30681bf03fc3afd7d71122c8
ms.sourcegitcommit: daa080cf220835f157a23e8c8e2bd2781b869bb7
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/04/2017
---
# <a name="support-for-windows-10-for-system-center-configuration-manager"></a>Ondersteuning voor Windows 10 voor System Center Configuration Manager  

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*


 In dit onderwerp beschrijft de versies van Windows 10 waarmee u met de verschillende versies van System Center Configuration Manager Current Branch gebruiken kunt. Dit omvat:
 -  Windows 10 als Configuration Manager-client.
 -  De Windows 10 Windows Assessment and Deployment Kit (ADK).

## <a name="windows-10-as-a-client"></a>Windows 10 als een client
Configuration Manager probeert om ondersteuning te bieden als een client voor elke nieuwe versie van Windows 10 zo snel mogelijk na deze beschikbaar. Omdat de producten afzonderlijke planningen voor ontwikkeling en versie hebben, afhankelijk de ondersteuning die Configuration Manager biedt van wanneer elk beschikbaar.

Bijvoorbeeld: een Configuration Manager-versie wordt niet verwijderen uit de matrix na [ondersteuning voor die versie](/sccm/core/servers/manage/current-branch-versions-supported) eindigt. Ondersteuning voor versies van Windows 10 zoals de 2015 Enterprise LTSB of 1511 wordt ook verwijderen uit de matrix wanneer ze zijn verwijderd uit de ondersteuning. Zie [afgeschafte besturingssystemen](/sccm/core/plan-design/changes/removed-and-deprecated-features#deprecated-operating-systems) voor meer informatie.

-   De volgende informatie supplementen [ondersteunde besturingssystemen voor clients en apparaten](/sccm/core/plan-design/configs/supported-operating-systems-for-clients-and-devices).
-   Als u de Long-Term Servicing Branch van Configuration Manager gebruikt, Zie [ondersteunde configuraties voor de vertakking Long-Term onderhoud](/sccm/core/understand/supported-configurations-for-ltsb).

|Versie van Windows 10                    |  Configuration Manager 1702          |    Configuration Manager 1706 |Configuration Manager 1710          |  
|---------------------|-----|-----|-----|
|Enterprise 2015 LTSB                   |![Ondersteund](media/green_check.png) |![Ondersteund](media/green_check.png) | ![Ondersteund](media/green_check.png) |
|Enterprise 2016 LTSB                   |![Ondersteund](media/green_check.png) |![Ondersteund](media/green_check.png) | ![Ondersteund](media/green_check.png) |
|1607   <br />(Ook wel bekend als de Update van de verjaardag)<br />(*edities Zie*)   |![Ondersteund](media/green_check.png) |![Ondersteund](media/green_check.png)            |![Ondersteund](media/green_check.png) |
|1703   <br />(Ook wel bekend als de beveiligingsbeheerder-Update)<br />(*edities Zie*)      |![Achterwaarts compatibel](media/blue_compat.png) |![Ondersteund](media/green_check.png) | ![Ondersteund](media/green_check.png) |
|1709   <br />(Ook wel bekend als de beveiligingsbeheerder vallen Update)<br />(*edities Zie*) |![Niet ondersteund](media/Red_X.png)   |![Achterwaarts compatibel](media/blue_compat.png) | ![Ondersteund](media/green_check.png) |



**De volgende versies:** Enterprise, Pro, Education, Pro onderwijs   

|Sleutel|
|--|
|![Ondersteund](media/green_check.png) = **ondersteund**  |
|![Niet ondersteund](media/blue_compat.png)  = **Backwards compatibele** -dit betekent dat de bestaande client-beheerfuncties (hardware-inventaris, software-inventaris, software-updates, enzovoort) met de nieuwe versie van Windows 10 werken moeten. Bekende problemen of waarschuwingen worden gedocumenteerd. <br><br>Deze aanpak geeft u de mogelijkheid om te implementeren en beheren van nieuwe Windows is gebaseerd op dag één met de ondersteuning voor compatibiliteit van toepassingen zonder een nieuwe updateversie van de Configuration Manager. |
|![Ondersteund](media/Red_X.png) = **niet ondersteund**|


## <a name="windows-10-adk"></a>Windows 10 ADK
Wanneer u besturingssystemen met Configuration Manager implementeert de [Windows ADK is een externe afhankelijkheid](/sccm/osd/plan-design/infrastructure-requirements-for-operating-system-deployment) die is vereist.

De onderstaande lijst de versies van Windows 10 ADK die u met verschillende versies van Configuration Manager gebruiken kunt.

|Windows 10 ADK-versie  |Configuration Manager 1702   |Configuration Manager 1706 |Configuration Manager 1710 |
|--------------------|-----|-----|-----|
|1607  |![Achterwaarts compatibel](media/blue_compat.png) |![Niet ondersteund](media/Red_X.png)| ![Niet ondersteund](media/Red_X.png) |
|1703  |![Ondersteund](media/green_check.png)            |![Ondersteund](media/green_check.png) | ![Achterwaarts compatibel](media/blue_compat.png)|
|1709  |![Niet ondersteund](media/Red_X.png)              |![Ondersteund](media/green_check.png) | ![Ondersteund](media/green_check.png)|

|Sleutel|
|--|
|![Ondersteunde](media/green_check.png) = **ondersteunde** : Windows adviseert het gebruik van Windows ADK die overeenkomt met de versie van Windows die u implementeert. De Windows ADK voor Windows 10 versie 1703 bijvoorbeeld gebruiken bij het implementeren van Windows 10 versie 1703.  |
|![Achterwaarts compatibel](media/blue_compat.png)  = **achterwaarts compatibel** -deze combinatie is niet getest, maar moeten werken. Bekende problemen of waarschuwingen worden gedocumenteerd. |
|![Ondersteund](media/Red_X.png) = **niet ondersteund**|
