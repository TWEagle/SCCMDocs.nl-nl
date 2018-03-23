---
title: Ondersteuning voor Windows 10
titleSuffix: Configuration Manager
description: Meer informatie over de versies van Windows 10 die worden ondersteund als clients of voor OSD met System Center Configuration Manager
ms.custom: na
ms.date: 03/22/2018
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: a1626a65-da22-49e0-9564-d2f752ea3f4b
caps.latest.revision: ''
author: aczechowski
ms.author: aaroncz
manager: dougeby
ms.openlocfilehash: 877732c4095438b19a863335a4a0026b7b088b24
ms.sourcegitcommit: 11bf4ed40ed0cbb10500cc58bbecbd23c92bfe20
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 03/23/2018
---
# <a name="support-for-windows-10-in-system-center-configuration-manager"></a>Ondersteuning voor Windows 10 in System Center Configuration Manager  

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*


Meer informatie over de versies van Windows 10 die Configuration Manager ondersteunt, met inbegrip van:
 -  Windows 10 als een Configuration Manager-client
 -  De Windows Assessment and Deployment Kit (ADK) voor Windows 10

## <a name="windows-10-as-a-client"></a>Windows 10 als een client
Configuration Manager probeert om ondersteuning te bieden als een client voor elke nieuwe versie van Windows 10 zo snel mogelijk na deze beschikbaar. Omdat de producten afzonderlijke planningen voor ontwikkeling en versie hebben, afhankelijk de ondersteuning die Configuration Manager biedt van wanneer elk beschikbaar.

Bijvoorbeeld: een Configuration Manager-versie verwijderd van de matrix na [ondersteuning voor die versie](/sccm/core/servers/manage/current-branch-versions-supported) eindigt. Op deze manier ondersteuning voor versies van Windows 10 zoals de 2015 Enterprise LTSB of 1511 verwijdert uit de matrix wanneer ze zijn verwijderd uit de ondersteuning. Zie voor meer informatie [afgeschafte besturingssystemen](/sccm/core/plan-design/changes/deprecated/removed-and-deprecated-client#deprecated-client-operating-systems).


-   De volgende informatie supplementen [ondersteunde besturingssystemen voor clients en apparaten](/sccm/core/plan-design/configs/supported-operating-systems-for-clients-and-devices).
-   Als u de Long-Term Servicing Branch van Configuration Manager gebruikt, Zie [ondersteunde configuraties voor de vertakking Long-Term onderhoud](/sccm/core/understand/supported-configurations-for-ltsb).

| Versie van Windows 10 | Configuration Manager 1706 | Configuration Manager 1710 | Configuration Manager 1802 |
|---------------------|-----|-----|-----|
| Enterprise 2015 LTSB            <!--10/14/2025-->   | ![Ondersteund](media/green_check.png) | ![Ondersteund](media/green_check.png) | ![Ondersteund](media/green_check.png) |
| Enterprise 2016 LTSB            <!--10/13/2026-->   | ![Ondersteund](media/green_check.png) | ![Ondersteund](media/green_check.png) | ![Ondersteund](media/green_check.png) |
| 1607   <br />(*edities Zie*)   <!--04/10/2018-->   | ![Ondersteund](media/green_check.png) | ![Ondersteund](media/green_check.png) | ![Ondersteund](media/green_check.png) |
| 1703   <br />(*edities Zie*)   <!--10/09/2018-->   | ![Ondersteund](media/green_check.png) | ![Ondersteund](media/green_check.png) | ![Ondersteund](media/green_check.png) |
| 1709   <br />(*edities Zie*)   <!--04/09/2019-->   | ![Achterwaarts compatibel](media/blue_compat.png) | ![Ondersteund](media/green_check.png) | ![Ondersteund](media/green_check.png) |

<!-- lifecycle reference: https://support.microsoft.com/help/13853/windows-lifecycle-fact-sheet -->

**De volgende versies:** Enterprise, Pro, Education, Pro Education   

|Sleutel|
|--|
|![Ondersteund](media/green_check.png) = **ondersteund**  |
|![Backwards compatibele](media/blue_compat.png)  = **Backwards compatibele** -functies voor bestaande client moeten samenwerken met de nieuwe versie van Windows 10. Bijvoorbeeld, hardware-inventaris, software-inventarisatie en software-updates. We zullen Documenteer bekende problemen of aanvullende opmerkingen. <br><br>Deze aanpak biedt de mogelijkheid om te implementeren en beheren van nieuwe versies van Windows meteen met ondersteuning voor compatibiliteit van toepassingen en zonder een nieuwe updateversie van de Configuration Manager. |
|![Niet ondersteund](media/Red_X.png) = **niet ondersteund**|

 > [!NOTE]
 > Vanaf versie 1802, ondersteunt Configuration Manager de client op Windows 10 ARM64 apparaten. Functies voor bestaande client moeten samenwerken met deze nieuwe apparaten. Bijvoorbeeld, hardware en software-inventaris, software-updates en toepassingen beheren. Implementatie van besturingssysteem is momenteel niet ondersteund. <!-- 1353704 --> 



## <a name="windows-10-adk"></a>Windows 10 ADK
Wanneer u besturingssystemen met Configuration Manager implementeert de [Windows ADK is een externe afhankelijkheid](/sccm/osd/plan-design/infrastructure-requirements-for-operating-system-deployment) die is vereist.

De volgende tabel geeft de versies van Windows 10 ADK die u met verschillende versies van Configuration Manager gebruiken kunt.

| Windows 10 ADK-versie  | Configuration Manager 1706 | Configuration Manager 1710 | Configuration Manager 1802   |
|--------------------|-----|-----|-----|
| 1607  | ![Niet ondersteund](media/Red_X.png)   | ![Niet ondersteund](media/Red_X.png) | ![Niet ondersteund](media/Red_X.png) |
| 1703  | ![Ondersteund](media/green_check.png) | ![Achterwaarts compatibel](media/blue_compat.png) | ![Achterwaarts compatibel](media/blue_compat.png) |
| 1709  | ![Ondersteund](media/green_check.png) | ![Ondersteund](media/green_check.png) | ![Ondersteund](media/green_check.png) |

|Sleutel|
|--|
|![Ondersteunde](media/green_check.png) = **ondersteunde** : Windows adviseert het gebruik van Windows ADK die overeenkomt met de versie van Windows die u implementeert. De Windows ADK voor Windows 10 versie 1703 bijvoorbeeld gebruiken bij het implementeren van Windows 10 versie 1703. Zie voor meer informatie over Windows ADK onderdeel ondersteuningsmogelijkheden [DISM ondersteunde platforms](https://docs.microsoft.com/windows-hardware/manufacture/desktop/dism-supported-platforms) en [USMT vereisten](https://docs.microsoft.com/windows/deployment/usmt/usmt-requirements#bkmk-1). |
|![Achterwaarts compatibel](media/blue_compat.png)  = **achterwaarts compatibel** -deze combinatie is niet getest, maar moeten werken. We zullen Documenteer bekende problemen of aanvullende opmerkingen. |
|![Niet ondersteund](media/Red_X.png) = **niet ondersteund**|

 > [!Note]
 > Configuration Manager ondersteunt alleen x86- en amd64 onderdelen van Windows 10 ADK. Het ondersteunt momenteel geen arm of arm64 onderdelen. 