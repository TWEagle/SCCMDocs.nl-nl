---
title: Ondersteuning voor Windows 10
titleSuffix: Configuration Manager
description: Meer informatie over de versies van Windows 10 die worden ondersteund als clients of voor OSD met System Center Configuration Manager.
ms.custom: na
ms.date: 01/25/2018
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: a1626a65-da22-49e0-9564-d2f752ea3f4b
caps.latest.revision: 
author: mestew
ms.author: mstewart
manager: dougeby
ms.openlocfilehash: 2dfe9b63e9e7c41a4f8457dc5622f386c7cceec2
ms.sourcegitcommit: b13da5ad8ffd58e3b89fa6d7170e1dec3ff130a4
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 02/01/2018
---
# <a name="support-for-windows-10-for-system-center-configuration-manager"></a>Ondersteuning voor Windows 10 voor System Center Configuration Manager  

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*


 In dit onderwerp beschrijft de versies van Windows 10 waarmee u met de verschillende versies van System Center Configuration Manager Current Branch gebruiken kunt. Deze ondersteuning omvat:
 -  Windows 10 als een Configuration Manager-client
 -  De Windows Assessment and Deployment Kit (ADK) voor Windows 10

## <a name="windows-10-as-a-client"></a>Windows 10 als een client
Configuration Manager probeert om ondersteuning te bieden als een client voor elke nieuwe versie van Windows 10 zo snel mogelijk na deze beschikbaar. Omdat de producten afzonderlijke planningen voor ontwikkeling en versie hebben, afhankelijk de ondersteuning die Configuration Manager biedt van wanneer elk beschikbaar.

Bijvoorbeeld: een Configuration Manager-versie verwijderd van de matrix na [ondersteuning voor die versie](/sccm/core/servers/manage/current-branch-versions-supported) eindigt. Op deze manier ondersteuning voor versies van Windows 10 zoals de 2015 Enterprise LTSB of 1511 verwijdert uit de matrix wanneer ze zijn verwijderd uit de ondersteuning. Zie voor meer informatie [afgeschafte besturingssystemen](/sccm/core/plan-design/changes/deprecated/removed-and-deprecated-client#deprecated-client-operating-systems).


-   De volgende informatie supplementen [ondersteunde besturingssystemen voor clients en apparaten](/sccm/core/plan-design/configs/supported-operating-systems-for-clients-and-devices).
-   Als u de Long-Term Servicing Branch van Configuration Manager gebruikt, Zie [ondersteunde configuraties voor de vertakking Long-Term onderhoud](/sccm/core/understand/supported-configurations-for-ltsb).

|Versie van Windows 10                    |  Configuration Manager 1702          |    Configuration Manager 1706 |Configuration Manager 1710          |  
|---------------------|-----|-----|-----|
|Enterprise 2015 LTSB                   |![Ondersteund](media/green_check.png) |![Ondersteund](media/green_check.png) | ![Ondersteund](media/green_check.png) |
|Enterprise 2016 LTSB                   |![Ondersteund](media/green_check.png) |![Ondersteund](media/green_check.png) | ![Ondersteund](media/green_check.png) |
|1607   <br />(Ook wel bekend als de Update van de verjaardag)<br />(*edities Zie*)   |![Ondersteund](media/green_check.png) |![Ondersteund](media/green_check.png)            |![Ondersteund](media/green_check.png) |
|1703   <br />(Ook wel bekend als de beveiligingsbeheerder-Update)<br />(*edities Zie*)      |![Achterwaarts compatibel](media/blue_compat.png) |![Ondersteund](media/green_check.png) | ![Ondersteund](media/green_check.png) |
|1709   <br />(Ook wel bekend als de beveiligingsbeheerder vallen Update)<br />(*edities Zie*) |![Niet ondersteund](media/Red_X.png)   |![Achterwaarts compatibel](media/blue_compat.png) | ![Ondersteund](media/green_check.png) |



**De volgende versies:** Enterprise, Pro, Education, Pro Education   

|Sleutel|
|--|
|![Ondersteund](media/green_check.png) = **ondersteund**  |
|![Niet ondersteund](media/blue_compat.png)  = **Backwards compatibele** -bestaande client-beheerfuncties (hardware-inventaris, software-inventaris, software-updates, enzovoort) moeten samen met de nieuwe versie van Windows 10. We zullen Documenteer bekende problemen of aanvullende opmerkingen. <br><br>Deze aanpak geeft u de mogelijkheid om te implementeren en beheren van nieuwe Windows is gebaseerd op dag één met de ondersteuning voor compatibiliteit van toepassingen zonder een nieuwe updateversie van de Configuration Manager. |
|![Ondersteund](media/Red_X.png) = **niet ondersteund**|


## <a name="windows-10-adk"></a>Windows 10 ADK
Wanneer u besturingssystemen met Configuration Manager implementeert de [Windows ADK is een externe afhankelijkheid](/sccm/osd/plan-design/infrastructure-requirements-for-operating-system-deployment) die is vereist.

De volgende tabel geeft de versies van Windows 10 ADK die u met verschillende versies van Configuration Manager gebruiken kunt.

|Windows 10 ADK-versie  |Configuration Manager 1702   |Configuration Manager 1706 |Configuration Manager 1710 |
|--------------------|-----|-----|-----|
|1607  |![Achterwaarts compatibel](media/blue_compat.png) |![Niet ondersteund](media/Red_X.png)| ![Niet ondersteund](media/Red_X.png) |
|1703  |![Ondersteund](media/green_check.png)            |![Ondersteund](media/green_check.png) | ![Achterwaarts compatibel](media/blue_compat.png)|
|1709  |![Niet ondersteund](media/Red_X.png)              |![Ondersteund](media/green_check.png) | ![Ondersteund](media/green_check.png)|

|Sleutel|
|--|
|![Ondersteunde](media/green_check.png) = **ondersteunde** : Windows adviseert het gebruik van Windows ADK die overeenkomt met de versie van Windows die u implementeert. De Windows ADK voor Windows 10 versie 1703 bijvoorbeeld gebruiken bij het implementeren van Windows 10 versie 1703. Zie voor meer informatie over Windows ADK onderdeel ondersteuningsmogelijkheden [DISM ondersteunde platforms](https://docs.microsoft.com/windows-hardware/manufacture/desktop/dism-supported-platforms) en [USMT vereisten](https://docs.microsoft.com/windows/deployment/usmt/usmt-requirements#bkmk-1). |
|![Achterwaarts compatibel](media/blue_compat.png)  = **achterwaarts compatibel** -deze combinatie is niet getest, maar moeten werken. We zullen Documenteer bekende problemen of aanvullende opmerkingen. |
|![Ondersteund](media/Red_X.png) = **niet ondersteund**|
