---
title: Onderhoudsvensters gebruiken
titleSuffix: Configuration Manager
description: Verzamelingen en onderhoudsvensters gebruiken clients in System Center Configuration Manager effectief te beheren.
ms.custom: na
ms.date: 02/22/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 4564ebcb-41a8-4eb0-afdb-2e1f0795cfa2
caps.latest.revision: "6"
caps.handback.revision: "0"
author: andredm7
ms.author: andredm
manager: angrobe
ms.openlocfilehash: 960955af87cdae9c43b5b520c348e32e1f48ef32
ms.sourcegitcommit: c236214b2fcc13dae7bad96d7fb33f692868191d
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/12/2017
---
# <a name="how-to-use-maintenance-windows-in-system-center-configuration-manager"></a>Het gebruik van onderhoudsvensters in System Center Configuration Manager

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*

Onderhoudsvensters kunnen u een tijdstip waarop Configuration Manager-bewerkingen kunnen worden uitgevoerd op een apparatenverzameling definiëren. U kunt onderhoudsvensters gebruiken om ervoor te zorgen dat wijzigingen plaatsvinden tijdens perioden die niet van invloed zijn op de productiviteit van de clientconfiguratie.  

 De volgende bewerkingen ondersteunen onderhoudsvensters:  

-   Software-implementatie  

-   Software-update-implementaties  

-   Implementatie en beoordeling van instellingen voor naleving  

-   Implementaties van besturingssystemen  

-   Implementaties van takenreeksen  

 Onderhoudsvensters configureren met een startdatum, een start- en eindtijd en een terugkeerpatroon. De maximumduur van een venster is minder dan 24 uur. Computer opnieuw opgestart door een implementatie zijn niet toegestaan buiten een onderhoudsvenster, maar u kunt deze standaardinstelling negeren. Onderhoudsvensters invloed hebben op alleen de tijd waarop het implementatieprogramma wordt uitgevoerd; toepassingen die zijn geconfigureerd om te downloaden en lokaal uitvoeren kunnen downloaden van inhoud van buiten het venster.  

 Wanneer een clientcomputer lid is van een apparatenverzameling die een onderhoudsvenster, implementatieprogramma alleen uitgevoerd als de maximaal toegestane uitvoeringstijd niet langer zijn dan de duur die is geconfigureerd voor het venster. Als de uitvoering van het programma mislukt, wordt er een waarschuwing gegenereerd en wordt de implementatie opnieuw uitgevoerd tijdens het volgende geplande onderhoudsvenster dat over voldoende tijd beschikt.  

## <a name="using-multiple-maintenance-windows"></a>Meerdere onderhoudsvensters gebruiken  
 Wanneer een clientcomputer lid is van meerdere apparaatverzamelingen waarbij onderhoudsvensters zijn, wordt deze regels toepassen:  

-   Als de onderhoudsvenster elkaar niet overlappen, worden deze behandeld als twee onafhankelijke vensters.  

-   Als de onderhoudsvensters elkaar overlappen, worden deze behandeld als één enkel onderhoudsvenster dat een tijdsduur omvat die door beide onderhoudsvenster wordt ingenomen. Wanneer bijvoorbeeld twee windows elk een uur in duur overlappen met 30 minuten, de effectieve duur van het onderhoudsvenster 90 minuten zijn.  

 Wanneer een gebruiker de installatie van een toepassing in Software Center begint, wordt de toepassing onmiddellijk geïnstalleerd, ongeacht enig onderhoudsvensters.  

 Als de implementatie van een toepassing met het doel **Vereist** buiten kantooruren de installatiedeadline bereikt die door de gebruiker in Software Center is gedefinieerd, wordt de toepassing geïnstalleerd.  

### <a name="how-to-configure-maintenance-windows"></a>Onderhoudsvensters configureren  

1.  Kies in de Configuration Manager-console **activa en naleving**>  **Apparaatverzamelingen**.  

3.  In de **Apparaatverzamelingen** , selecteert u een verzameling. U kunt geen onderhoudsvensters maken voor de verzameling **Alle systemen** .  

4.  Op de **Start** tabblad, in de **eigenschappen** groep, kiest u **eigenschappen**.  

5.  In de **Onderhoudsvensters** tabblad van de  **&lt;verzamelingsnaam\> eigenschappen** dialoogvenster Kies de **nieuw** pictogram.  

6.  Voltooi de  **&lt;nieuwe\> planning** dialoogvenster.  

7.  Maak een keuze uit de **dit schema toepassen op** vervolgkeuzelijst.  

8.  Kies **OK** en sluit vervolgens de  **&lt;verzamelingsnaam\> eigenschappen** in het dialoogvenster.  
