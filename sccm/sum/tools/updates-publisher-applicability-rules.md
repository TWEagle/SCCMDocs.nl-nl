---
title: Regels voor toepasselijkheid | Microsoft-documenten
description: Regels voor toepasselijkheid voor System Center Updates Publisher beheren
ms.custom: na
ms.date: 4/29/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 3cf0c2cd-397a-4622-b11c-961f334fb7d7
caps.latest.revision: 1
author: Brenduns
ms.author: brenduns
manager: angrobe
robots: NOINDEX, NOFOLLOW
ms.translationtype: Machine Translation
ms.sourcegitcommit: 31819a1df4e63e1114682490a9b3c3b4e5c99cfa
ms.openlocfilehash: 2925abda07abaa46ad56b9b433ce003c22aede5e
ms.contentlocale: nl-nl
ms.lasthandoff: 05/17/2017

---

# <a name="manage-applicability-rules-in-updates-publisher"></a>Regels voor toepasselijkheid in Updates Publisher beheren

*Van toepassing op: System Center Updates Publisher*

Met Updates Publisher definiëren regels voor toepasselijkheid vereisten die moeten worden voldaan voordat een apparaat een update kunt installeren. De regels worden ook gebruikt om te bepalen of de computer een update is geïnstalleerd heeft. Een regel voor toepasselijkheid die uit meerdere onderdelen complex is bedoeld om in te stellen als een regel.

Updatebundels gebruik geen regels voor toepasselijkheid.

## <a name="overview-of-applicability-rules"></a>Overzicht van regels voor toepasselijkheid
Beheren van regels voor toepasselijkheid van de **regels werkruimte**. Wanneer u een regel maakt, geeft u een of meer voorwaarden. Als meerdere voorwaarden zijn opgegeven, kunt u de relaties tussen de voorwaarden zorgen dat ze worden opeenvolgend geëvalueerd of gecombineerd in logische **en** of **of** instructies.

Het volgende is bijvoorbeeld een regelset met drie regels. De eerste regel controleert de *mijnbestand* bestand bestaat en de regels van de tweede en het controleren of de taal van het besturingssysteem Windows is Engels of Japans.

    And  
      File ‘\[PROGRAM\_FILES\] \\Microsoft\\MyFile’ exists  
      Or  
        Windows Language is English   
        Windows Language is Japanese

Alle updates moet ten minste één regel van toepassing. Updates die u reeds importeert hebben regels voor toepasselijkheid toegepast en wanneer u uw eigen updates maakt, moet u een of meer regels toevoegen aan deze. U kunt wijzigen en bevatten nadere toelichtingen bij de regels voor een update in Updates Publisher.

Op weergaveregels die u hebt gemaakt, in de **regels werkruimte**, selecteert u een regel op uit de **Mijn opgeslagen regels** lijst. De logische bewerkingen voor die regel en afzonderlijke voorwaarden worden weergegeven de **regels voor toepasselijkheid** deelvenster van de console. Regels voor updates die u importeert kunnen alleen worden weergegeven en worden gewijzigd als u de update bewerken.

U kunt regels maken op twee locaties in Updates Publisher:

-   In de **regels werkruimte** u maken en **opslaan** regel ingesteld dat u vervolgens later kunt gebruiken. Tijdens het bewerken of maken van een update kunt u **opgeslagen regel** als de **regeltype**, en selecteer vervolgens in een lijst van de vooraf gemaakte regelsets.

-   U kunt ook nieuwe regels maken op het moment dat u maakt of bewerkt van een update. Regels die u op deze manier maakt worden niet opgeslagen voor toekomstig gebruik.

## <a name="create-applicability-rule"></a>Regel voor toepasselijkheid maken
De volgende informatie is vergelijkbaar met hoe u regels vanuit maken de [maken bijwerken wizard](/sccm/sum/tools/create-updates-with-updates-publisher#the-create-update-wizard). Maar in tegenstelling tot de wizard hebt u de optie om op te slaan, uw regelsets voor toekomstig gebruik.

1.  In de **regels werkruimte**, kies **maken** openen de **Create Rule** wizard.

2.  Geef een naam voor de regel en klik vervolgens op ![nieuwe regel](media/newrule.png). Hiermee opent u de **toepasbaarheid regel** pagina waar u regels kunt configureren.

3.  Voor **type, regel** Selecteer een van de volgende. De opties die u moet configureren varieert voor elk type:

    -   **Bestand** : met deze regel gebruiken om te vereisen dat een apparaat beschikt over een bestand met eigenschappen die voldoen aan een of meer opgegeven criteria voordat deze update kunnen worden toegepast.

    -   **Register –** dit type gebruiken om op te geven Registerdetails die aanwezig zijn moeten voordat een apparaat, gelden deze update te installeren.

    -   **Systeem –** met deze regel details van systeem gebruikt om te bepalen van toepassing. U kunt kiezen tussen een Windows-versie, een Windows-taal, processorarchitectuur definiëren of geef een WMI-query om te identificeren van het besturingssysteem voor apparaten.

    -   **Windows Installer-** Gebruik dit regeltype om te bepalen op basis van een geïnstalleerde toepassing. MSI- of Windows Installer-patch (. MSP). U kunt ook bepalen of specifieke onderdelen of onderdelen zijn geïnstalleerd als onderdeel van de vereiste.

       > [!IMPORTANT]   
       > Op beheerde deices, de Windows Update Agent kan niet detecteren Windows installeren pakketten die per gebruiker geïnstalleerd. Wanneer u dit regeltype, aanvullende voorwaarden, zoals bestandsversies of registersleutelwaarden, zo configureren dat de Windows Installer-pakket correct ongeacht basis per gebruiker of per systeem kan worden gedetecteerd.

    -   **Regel – opgeslagen** deze optie kunt u zoeken en regels die u eerder hebt geconfigureerd en opgeslagen.

4.  Doorgaan met het toevoegen en configureer de gewenste aanvullende regels.

5.  Gebruik de knoppen logische bewerking bestellen en groep verschillende regels voor het maken van complexe vereiste controles.

6.  Wanneer de regelset voltooid is, klikt u op **OK** op te slaan. De regel nu wordt weergegeven in de **Mijn opgeslagen regels** lijst.

## <a name="edit-applicability-rule-sets"></a>Toepasbaarheid regelsets bewerken
Een regel toepasbaarheid bewerken de **regels werkruimte** Selecteer eventuele regels die zijn opgeslagen in de **Mijn opgeslagen regels** lijst en kies vervolgens **bewerken** van het lint. Hiermee opent u de **regel bewerken** wizard.

De **regel bewerken** wizard geeft de huidige regels voor de regel. U regels op dezelfde manier bewerken als u de **Create Rule** wizard nieuwe regels maken. Deze wizard kunt u de regelinstellingen wijzigen, regels, volgorde regels en relaties worden verwijderd of nieuwe regels toevoegen.

Nadat u wijzigingen aanbrengt, kiest u **OK** de wijzigingen opslaan en sluiten van de wizard.

Zie voor meer informatie over het gebruik van de wizard regel voor **stap 7**, de pagina toepasbaarheid van de [maken bijwerken wizard](/sccm/sum/tools/create-updates-with-updates-publisher#the-create-update-wizard).

## <a name="delete-applicability-rules"></a>Regels voor toepasselijkheid verwijderen
Een regel opgeslagen toepasbaarheid verwijderen de **regels werkruimte** selecteert u de regel of de regel ingesteld vanuit de **Mijn opgeslagen regels** lijst en kies vervolgens **verwijderen** van het lint. Hiermee verwijdert u de opgeslagen of set van Updates Publisher.

Als u wilt een regel hebt verwijderd van een specifieke update, moet u [de update bewerken](/sccm/sum/tools/manage-updates-with-updates-publisher#edit-updates-and-bundles).

