---
title: Mogelijkheden in Technical Preview 1608 Configuration Manager
description: Meer informatie over functies die beschikbaar zijn in de Technical Preview voor System Center Configuration Manager, versie 1608.
ms.custom: na
ms.date: 01/23/2017
ms.prod: configuration-manager
ms.technology:
- configmgr-other
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 63e1df5e-637c-4b07-b7ec-95340f43a805
caps.latest.revision: 15
author: Brenduns
ms.author: brenduns
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 5d08d1f9ccd995d544c3c21c4af52ede73343077
ms.openlocfilehash: c22e29da8036d69db917205f28a19a69281a64db
ms.contentlocale: nl-nl
ms.lasthandoff: 05/17/2017

---
# <a name="capabilities-in-technical-preview-1608-for-system-center-configuration-manager"></a>Mogelijkheden in Technical Preview 1608 voor System Center Configuration Manager

*Van toepassing op: System Center Configuration Manager (technische Preview)*

Dit artikel worden de functies die beschikbaar in de Technical Preview voor System Center Configuration Manager, versie 1608 zijn geïntroduceerd. U kunt deze versie om te werken en nieuwe mogelijkheden toevoegen aan uw technische preview van Configuration Manager site installeren.      Voordat u deze versie van de technische preview installeert, leest u de inleidende onderwerp [Technical Preview voor System Center Configuration Manager](../../core/get-started/technical-preview.md), om meer vertrouwd raken met algemene vereisten en beperkingen voor het gebruik van een technische preview hoe tussen versies en hoe u feedback geven over de functies in een technische preview bijwerken.    


**De volgende zijn nieuwe functies die u met deze versie kunt uitproberen.**  




##  <a name="improvements-to-the-prepare-configmgr-client-for-capture-task-sequence-step"></a>Verbeteringen in de takenreeksstap ConfigMgr-client voorbereiden voor vastleggen  
De ConfigMgr-Client voorbereiden stap wordt de Configuration Manager-client in plaats van alleen verwijderen sleutelinformatie nu volledig verwijderd. Wanneer de takenreeks de vastgelegde installatiekopie implementeert wordt wordt telkens wanneer een nieuwe Configuration Manager-client geïnstalleerd.  


## <a name="improvements-to-software-center"></a>Verbeteringen in Software Center
* Het Software Center **toepassingen**, **Updates**, en **besturingssystemen** tabbladen nu zien welke software zijn recentelijk toegevoegd. Getallen in het navigatievenster weergeven hoeveel nieuwe soorten software op elk tabblad zijn.
* Gebruikers kunnen nu goedkeuring aanvragen voor toepassingen en bekijk vervolgens de aanvraaggeschiedenis in de **Toepassingdetails** weergeven in Software Center. De **aanvragen** knop **Toepassingdetails** niet langer wordt omgeleid naar de Toepassingscatalogus op het Internet.

## <a name="improvements-to-asset-intelligence"></a>Verbeteringen in de Asset Intelligence
We hebben toegevoegd een veld in de eigenschappen voor geïnventariseerde software waarmee u een bovenliggende en onderliggende relatie met andere software die is ingesteld. In de lijst met geïnventariseerde Software kunt u vervolgens het bovenliggende lid van alle software en alle onderliggende software ook verbergen.

### <a name="configure-a-parent-to-child-relationship"></a>Configureren van een bovenliggende-onderliggende relatie
  1. Om in te stellen bovenliggende software, in het knooppunt geïnventariseerde Software, met de rechtermuisknop op een software-item in de **geïnventariseerde Software** lijst en kies **eigenschappen**.
  2. Selecteer de software die u wilt instellen als de bovenliggende software voor uw eerste selectie in het dialoogvenster.

### <a name="filter-the-software-display"></a>De software te filteren
Nadat u hebt bovenliggende naar onderliggende relaties gedefinieerd, u kunt uw weergave filteren zodat alleen software die is een bovenliggende of die geen gedefinieerde relatie heeft. Alle software die is ingesteld als een onderliggende site van een andere geïnventariseerde software wordt verborgen. Als u dit doet:
   1.    De zoekbalk zelf kiezen **Criteria toevoegen**
   2. Selecteer **bovenliggende Software** en wijzig de waarde van de criteria voor **is leeg**, en klik vervolgens op **zoeken**.

De weergave wordt nu alleen de items van de bovenliggende software of software die heeft geen gedefinieerde relaties. Software die is alleen een onderliggende site van een andere titel wordt niet weergegeven.

## <a name="remote-control-keyboard-translation"></a>Beheer op afstand toetsenbord vertaling
In het verleden verzonden Configuration Manager de belangrijkste positie van de locatie van de viewer naar de gedeelde locatie. Dit was problematisch zijn eruit voor toetsenbord-configuraties die van de viewer naar gedeelde afwijkt. Bijvoorbeeld, een viewer met een Engels toetsenbord typt een "A", maar de gedeelde Frans toetsenbord "Q" wilt opgeven. We zijn het standaardgedrag wijzigen zodat het teken zelf van de viewer toetsenbord wordt verzonden naar de gedeelde resource en de viewer plan is naar het type op de gedeelde resource aankomt.

Dit probleem kan worden uitgeschakeld door de viewer als ze de voorkeur geven op basis van de gedeelde toetsenbord rangschikking type. Het gedrag wijzigen **afstandbediening voor Configuration Manager**, kies **actie**, en kies **inschakelen toetsenbord vertaling** voor het verzenden van belangrijke positie.

> [!NOTE]
>
> Speciale drukken, zoals ~! #@ $%, niet correct worden vertaald.

