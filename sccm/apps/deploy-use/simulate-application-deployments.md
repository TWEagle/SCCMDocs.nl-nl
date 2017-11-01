---
title: Toepassingsimplementaties simuleren
titleSuffix: Configuration Manager
description: De detectiemethode, vereisten en afhankelijkheden voor een implementatietype zonder de toepassing installeren evalueren.
ms.custom: na
ms.date: 10/06/2016
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: configmgr-app
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 28b240a4-d358-40ce-8006-c697b1622ece
caps.latest.revision: "6"
caps.handback.revision: "0"
author: mattbriggs
ms.author: mabrigg
manager: angrobe
ms.openlocfilehash: ecd641a14188e0247d10e0fac613ea760abb00d1
ms.sourcegitcommit: c236214b2fcc13dae7bad96d7fb33f692868191d
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/12/2017
---
# <a name="simulate-application-deployments-with-system-center-configuration-manager"></a>Implementaties van toepassingen met System Center Configuration Manager simuleren

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*

U kunt gesimuleerde implementaties gebruiken voor het testen van de implementatie van een toepassing zonder installeren of verwijderen van de toepassing. Een gesimuleerde implementatie evalueert de detectiemethode, vereisten en afhankelijkheden voor een implementatietype. Deze rapporteert de resultaten in de **implementaties** knooppunt van de **bewaking** werkruimte. Gebruik de procedure in dit onderwerp om te simuleren van de implementatie van een toepassing in System Center Configuration Manager (Configuration Manager).  

> [!NOTE]  
> U kunt gesimuleerde implementaties niet gebruiken voor verzamelingen van mobiele apparaten.  
>   
> U kunt een toepassing niet implementeren met het implementatiedoel **Verwijderen** als een gesimuleerde implementatie van dezelfde toepassing actief is.  

## <a name="configure-a-simulated-application-deployment"></a>Een gesimuleerde toepassingsimplementatie configureren

1.  Selecteer in de Configuration Manager-console een van de volgende opties:  
    -   Een verzameling gebruikers.  
    -   Een verzameling apparaten.  
    -   Een Configuration Manager-toepassing.  

2.  Op de **Start** tabblad, in de **implementatie** groep, kiest u **implementatie simuleren**.  

3.  Stel in de Wizard toepassing implementatie simuleren in de volgende gegevens voor uw gesimuleerde implementatie:  

    -   **Toepassing**. Kies **Bladeren**, en selecteer vervolgens de toepassing die u wilt maken van een gesimuleerde implementatie voor.  

    -   **Verzameling**. Kies **Bladeren**, en selecteer vervolgens de verzameling die u wilt gebruiken voor de gesimuleerde implementatie.  

    -   **Actie**. Selecteer in de vervolgkeuzelijst of u wilt de installatie of het verwijderen van de geselecteerde toepassing simuleren.  

    -   **Automatisch implementeren met of zonder gebruikersaanmelding**. Als deze optie is ingeschakeld, evalueren de clients de gesimuleerde implementatie of de clients zijn aangemeld of niet.  

4.  Klik op **volgende**, lees de informatie op de **samenvatting** pagina en voltooi de wizard voor het maken van de gesimuleerde toepassingsimplementatie.  

5.  Gesimuleerde toepassingen worden weergegeven de **implementaties** knooppunt van de **bewaking** werkruimte met als doel **simuleren**. Zie voor meer informatie over het bewaken van toepassingsimplementaties [toepassingen bewaken vanuit de System Center Configuration Manager-console](../../apps/deploy-use/monitor-applications-from-the-console.md).  
