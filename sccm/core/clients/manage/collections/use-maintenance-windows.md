---
title: Onderhoudsvensters gebruiken | Microsoft-documenten
description: Gebruik verzamelingen en onderhoudsvensters effectief om clients te beheren in System Center Configuration Manager.
ms.custom: na
ms.date: 02/22/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 4564ebcb-41a8-4eb0-afdb-2e1f0795cfa2
caps.latest.revision: 6
caps.handback.revision: 0
author: andredm7
ms.author: andredm
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9c5d1e48b76392beaf54b5377c69b648537e86f8
ms.openlocfilehash: fa67cf597c73bab47209c9b98539f97e174ae70b
ms.contentlocale: nl-nl
ms.lasthandoff: 05/17/2017


---
# <a name="how-to-use-maintenance-windows-in-system-center-configuration-manager"></a>Het gebruik van onderhoudsvensters in System Center Configuration Manager

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*

Onderhoudsvensters kunnen u een tijdstip waarop Configuration Manager-bewerkingen kunnen worden uitgevoerd op een apparatenverzameling definiëren. U kunt onderhoudsvensters gebruiken om ervoor te zorgen dat wijzigingen plaatsvinden tijdens perioden die geen invloed hebben op de productiviteit van de clientconfiguratie.  

 De volgende bewerkingen ondersteunen onderhoudsvensters:  

-   Software-implementatie  

-   Software-update-implementaties  

-   Implementatie en beoordeling van instellingen voor naleving  

-   Implementaties van besturingssystemen  

-   Implementaties van takenreeksen  

 Onderhoudsvensters configureren met een startdatum, een start- en eindtijd en een terugkeerpatroon. De maximale duur van een venster is minder dan 24 uur. Wanneer de computer opnieuw opgestart door een implementatie mogen niet buiten een onderhoudsvenster, maar u kunt de standaardwaarde te overschrijven. Onderhoudsvensters zijn alleen de tijd waarop het implementatieprogramma wordt uitgevoerd; invloed toepassingen die zijn geconfigureerd om te downloaden en lokaal uitvoeren kunnen inhoud van buiten het venster downloaden.  

 Wanneer een clientcomputer lid is van een apparaatverzameling met een onderhoudsvenster, een implementatieprogramma wordt alleen uitgevoerd als de maximaal toegestane uitvoeringstijd niet groter zijn dan de duur die is geconfigureerd voor het venster. Als de uitvoering van het programma mislukt, wordt er een waarschuwing gegenereerd en wordt de implementatie opnieuw uitgevoerd tijdens het volgende geplande onderhoudsvenster dat over voldoende tijd beschikt.  

## <a name="using-multiple-maintenance-windows"></a>Meerdere onderhoudsvensters gebruiken  
 Wanneer een clientcomputer lid van meerdere apparaatverzamelingen waarbij onderhoudsvensters zijn is, gelden deze regels:  

-   Als de onderhoudsvenster elkaar niet overlappen, worden deze behandeld als twee onafhankelijke vensters.  

-   Als de onderhoudsvensters elkaar overlappen, worden deze behandeld als één enkel onderhoudsvenster dat een tijdsduur omvat die door beide onderhoudsvenster wordt ingenomen. Als twee bijvoorbeeld windows, een uur elk elkaar overlappen duur van 30 minuten wordt de effectieve duur van het onderhoudsvenster zou 90 minuten.  

 Wanneer een gebruiker de installatie van een toepassing vanuit Software Center begint, wordt de toepassing onmiddellijk geïnstalleerd, ongeacht enig onderhoudsvensters.  

 Als de implementatie van een toepassing met het doel **Vereist** buiten kantooruren de installatiedeadline bereikt die door de gebruiker in Software Center is gedefinieerd, wordt de toepassing geïnstalleerd.  

### <a name="how-to-configure-maintenance-windows"></a>Onderhoudsvensters configureren  

1.  Kies in de Configuration Manager-console **activa en naleving**>  **Apparaatverzamelingen**.  

3.  In de **Apparaatverzamelingen** , selecteert u een verzameling. U kunt geen onderhoudsvensters maken voor de verzameling **Alle systemen** .  

4.  Op de **Start** tabblad, in de **eigenschappen** groep, kiest u **eigenschappen**.  

5.  In de **Onderhoudsvensters** tabblad van het  **&lt;Collectienaam\> eigenschappen** dialoogvenster Kies de **New** pictogram.  

6.  Voltooi de  **&lt;nieuwe\> schema** dialoogvenster.  

7.  Maak een selectie uit de **toepassen van deze planning voor** vervolgkeuzelijst.  

8.  Kies **OK** en sluit vervolgens de  **&lt;Collectienaam\> eigenschappen** in het dialoogvenster.  

