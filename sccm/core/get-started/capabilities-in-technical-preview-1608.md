---
title: Mogelijkheden van Technical Preview 1608
titleSuffix: Configuration Manager
description: Meer informatie over functies die beschikbaar zijn in de Technical Preview voor System Center Configuration Manager, versie 1608.
ms.custom: na
ms.date: 01/23/2017
ms.prod: configuration-manager
ms.technology: configmgr-other
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 63e1df5e-637c-4b07-b7ec-95340f43a805
caps.latest.revision: "15"
author: erikje
ms.author: erikje
manager: angrobe
ms.openlocfilehash: 09f85813c2572351e7d2f6192c06c7ea55a055a6
ms.sourcegitcommit: 7fe45ff75f05f7cc03ad021db8119791abe18049
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/01/2017
---
# <a name="capabilities-in-technical-preview-1608-for-system-center-configuration-manager"></a>Mogelijkheden van Technical Preview 1608 voor System Center Configuration Manager

*Van toepassing op: System Center Configuration Manager (Technical Preview)*

Dit artikel bevat de functies die beschikbaar in de Technical Preview voor System Center Configuration Manager, versie 1608 zijn. U kunt deze versie om te werken en nieuwe mogelijkheden toevoegen aan uw Configuration Manager technical preview-site installeren.      Controleer voordat u deze versie van de technical preview installeert, de inleidende informatie [Technical Preview voor System Center Configuration Manager](../../core/get-started/technical-preview.md), om vertrouwd te raken met algemene vereisten en beperkingen voor het gebruik van een technical preview hoe bijwerken tussen versies en hoe u feedback over de functies in een technical preview.    


**Hier volgen nieuwe functies die u met deze versie kunt uitproberen.**  




##  <a name="improvements-to-the-prepare-configmgr-client-for-capture-task-sequence-step"></a>Verbeteringen in de takenreeksstap ConfigMgr-client voorbereiden voor vastleggen  
De ConfigMgr-Client voorbereiden stap wordt de Configuration Manager-client, in plaats van alleen het verwijderen van belangrijke gegevens nu volledig verwijderd. Wanneer de takenreeks wordt geïmplementeerd voor de vastgelegde besturingssysteeminstallatiekopie wordt deze elke keer dat een nieuwe Configuration Manager-client installeren.  


## <a name="improvements-to-software-center"></a>Verbeteringen aan Software Center
* Het Software Center **toepassingen**, **Updates**, en **besturingssystemen** tabbladen nu zien welke software zijn recentelijk toegevoegd. Nummers in het navigatievenster weergeven hoeveel nieuwe stukjes software op elk tabblad zijn.
* Gebruikers kunnen nu goedkeuring aanvragen voor toepassingen en bekijk vervolgens de aanvraaggeschiedenis van de in de **Toepassingdetails** weergeven in Software Center. De **aanvragen** knop in **Toepassingdetails** niet langer wordt omgeleid naar het web gebaseerde Application Catalog.

## <a name="improvements-to-asset-intelligence"></a>Verbeteringen in Asset Intelligence
Een veld in de eigenschappen voor geïnventariseerde software waarmee u een bovenliggende en onderliggende relatie met andere software die is ingesteld, hebben we toegevoegd. U kunt in de lijst geïnventariseerde Software vervolgens het bovenliggende lid van alle software weergeven en alle onderliggende software ook verbergen.

### <a name="configure-a-parent-to-child-relationship"></a>Configureren van een bovenliggende-onderliggende relatie
  1. Als bovenliggende software, in het knooppunt geïnventariseerde Software, met de rechtermuisknop op een software-item in de **geïnventariseerde Software** lijst en kies **eigenschappen**.
  2. Selecteer de software die u wilt instellen als het bovenliggende software voor uw eerste selectie in het dialoogvenster.

### <a name="filter-the-software-display"></a>De software te filteren
Nadat u hebt de bovenliggende naar onderliggende relaties gedefinieerd, u kunt uw weergave filteren zodat alleen software die is een bovenliggende of die heeft geen gedefinieerde relatie. Alle software die is ingesteld als een onderliggend element van een andere geïnventariseerde software wordt verborgen. Te doen:
   1.   De zoekbalk kiezen **Criteria toevoegen**
   2. Selecteer **bovenliggende Software** en wijzig de waarde van de criteria voor **is leeg**, en klik vervolgens op **Search**.

De weergave wordt nu alleen de hoofdartikelen software of software die heeft geen gedefinieerde relaties. Software die is alleen een onderliggend element van een andere titel wordt niet weergegeven.

## <a name="remote-control-keyboard-translation"></a>De vertaling van beheer op afstand toetsenbord
In het verleden verzonden Configuration Manager de belangrijkste positie van de viewer locatie naar de gedeelde locatie. Dit was problematisch voor toetsenbord-configuraties die van de viewer naar gedeelde afwijkt. Bijvoorbeeld, een viewer met een Engels toetsenbord typt een "A", maar de gedeelde Franse toetsenbord 'Q' wilt opgeven. We zijn het standaardgedrag wijzigen zodat het teken zelf wordt overgebracht van de viewer toetsenbord naar de gedeelde en wat de viewer wil typt u bij de gedeelde resource aankomt.

Dit gedrag kan worden uitgeschakeld door de viewer als ze naar het type volgens de gedeelde toetsenbord regeling liever. Voor het wijzigen van het gedrag in **afstandbediening voor Configuration Manager**, kies **actie**, en kies **toetsenbord-omzetting inschakelen** voor het verzenden van de belangrijkste positie.

> [!NOTE]
>
> Speciale drukken, zoals ~! # $@ %, niet correct worden vertaald.
