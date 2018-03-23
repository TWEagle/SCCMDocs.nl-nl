---
title: CO-Beheerdashboard
titleSuffix: System Center Configuration Manager
description: Bekijk informatie over CO-beheer via het dashboard.
ms.custom: na
ms.date: 03/22/2018
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-client
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: e83a7b0d-b381-4b4a-8eca-850385abbebb
caps.latest.revision: ''
author: mestew
ms.author: mstewart
manager: dougeby
ms.openlocfilehash: 380ca748921a806a0e5edf608a62e8a44edf4d84
ms.sourcegitcommit: 11bf4ed40ed0cbb10500cc58bbecbd23c92bfe20
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 03/23/2018
---
# <a name="co-management-dashboard-in-system-center-configuration-manager"></a>Dashboard mede management in System Center Configuration Manager
*Van toepassing op: System Center Configuration Manager (huidige vertakking)*

Vanaf versie 1802, kunt u een dashboard met informatie over het beheer van CO weergeven. Het dashboard kunt u computers die CO beheerde in uw omgeving zijn controleren. De grafieken kunnen u apparaten identificeren die aandacht vereisen mogelijk.<!--1356648-->

## <a name="open-the-co-management-dashboard"></a>Open het dashboard met CO-management
U kunt het dashboard mede management openen met de volgende stappen uit: 

1. Open de Configuration Manager-console. 
2. Klik op de **bewaking** knooppunt. 
3. Als u wilt laden in het dashboard, klikt u op **mede management**.

## <a name="reviewing-information-in-the-co-management-dashboard"></a>Lezen van de informatie in het dashboard mede management

Het dashboard mede management bevat vier grafieken voor uw omgeving. 

- **Naast beheerde apparaten** -kunt u het percentage naast beheerde apparaten in uw omgeving.

    ![Naast beheerde apparaten grafiek](media\co-management-dashboard\Percent-Co-managed-graph.PNG)

- **BS client distributie** -toont het aantal client-apparaten met versie per besturingssysteem. De volgende groeperingen worden gebruikt: </br>
    - Windows 7 & 8.x
    - Windows 10 lager is dan 1709
    - Windows 10 1709 en hoger

         > [!NOTE] 
         > Windows 10 versie 1709 en hoger, is een vereiste voor het beheer van collega.

     Muiswijzer op een gedeelte van de grafiek geeft het percentage apparaten in het besturingssysteem geselecteerde groeperen.

     ![Grafiek van de distributie van de Client-besturingssysteem](media\co-management-dashboard\Co-management-OS-distribution-graph.PNG)

- **Mede Beheerstatus**-de uitsplitsing van apparaat slagen of mislukken in de volgende categorieën:
    - Geslaagd, hybride Azure AD join
    - Geslaagd, Azure AD die lid zijn van
    - Fout: Automatische inschrijving is mislukt
    
     Muiswijzer op een grafiek sectie kunt u het percentage apparaten in de categorie. 

     ![Statusgrafiek voor CO-management](media\co-management-dashboard\Co-management-status-graph.PNG)

     Te klikken op een grafiek sectie gaat u naar een lijst met apparaten voor de categorie.
 
     ![Lijst met apparaten voor inschrijving-fout](media\co-management-dashboard\Enrollment-Failure_Device-List.PNG)


- **Overgang van de werkbelasting**-wordt een staafdiagram weergegeven met het aantal apparaten dat u voor de vier beschikbare werkbelastingen is overgegaan naar Microsoft Intune:
    - Nalevingsbeleid
    - Toegang tot bedrijfsbronnen
    - Windows Update voor bedrijven
    - Endpoint Protection

     Muiswijzer op een gedeelte van de grafiek geeft het aantal apparaten voor de werkbelasting is overgegaan. 
     ![Werkbelasting overgang staafdiagram](media\co-management-dashboard\Workload-Transition.PNG)


## <a name="next-steps"></a>Volgende stappen

Zie voor meer informatie over CO management:
 - [Co-beheer voor Windows 10-apparaten](/sccm/core/clients/manage/co-management-overview.md)
 - [Windows 10-apparaten voorbereiden op co-beheer](/sccm/core/clients/manage/co-management-prepare.md)

    
