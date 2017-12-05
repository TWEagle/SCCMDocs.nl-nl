---
title: Regels voor toepasselijkheid
titleSuffix: Configuration Manager
description: Regels voor toepasselijkheid beheren voor System Center Updates Publisher
ms.custom: na
ms.date: 4/29/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 3cf0c2cd-397a-4622-b11c-961f334fb7d7
caps.latest.revision: "1"
author: mestew
ms.author: mstewart
manager: angrobe
robots: NOINDEX, NOFOLLOW
ms.openlocfilehash: 469081b31741812d0fe1b3e9f3d59fd29c93ee97
ms.sourcegitcommit: daa080cf220835f157a23e8c8e2bd2781b869bb7
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/04/2017
---
# <a name="manage-applicability-rules-in-updates-publisher"></a>Regels voor toepasselijkheid in Updates Publisher beheren

*Van toepassing op: System Center Updates Publisher*

Met Updates Publisher Definieer regels voor toepasselijkheid vereisten waaraan moeten worden voldaan voordat een apparaat kan een update installeert. De regels worden ook gebruikt om te bepalen of de computer een update is geïnstalleerd heeft. Een toepassingsregel die uit meerdere onderdelen complex is bedoeld om in te stellen als een regel.

Updatebundels gebruik geen regels voor toepasselijkheid.

## <a name="overview-of-applicability-rules"></a>Overzicht van regels voor toepasselijkheid
Beheren van regels voor toepasselijkheid van de **regels werkruimte**. Wanneer u een regel maakt, geeft u een of meer voorwaarden. Wanneer meerdere voorwaarden zijn opgegeven, kunt u de relaties tussen de voorwaarden zorgen dat ze worden opeenvolgend geëvalueerd of gecombineerd in logische configureren **en** of **of** instructies.

Het volgende is bijvoorbeeld een regelset dat drie regels bevat. De eerste regel controleert de *mijnbestand* bestand bestaat en de tweede en derde regels controleren of de taal van het besturingssysteem Windows Engels of Japans.

    And  
      File ‘\[PROGRAM\_FILES\] \\Microsoft\\MyFile’ exists  
      Or  
        Windows Language is English   
        Windows Language is Japanese

Alle updates moet ten minste één toepassingsregel. Updates die u al importeren, hebben regels voor toepasselijkheid toegepast en wanneer u uw eigen updates maakt, moet u een of meer regels toevoegen aan deze. U kunt aanpassen en uitbreiden van de regels voor een update in Updates Publisher.

Op weergaveregels die u hebt gemaakt, in de **regels werkruimte**, selecteer een regel van de **Mijn opgeslagen regels** lijst. De logische bewerkingen voor die regel en afzonderlijke voorwaarden weergegeven in de **regels voor toepasselijkheid** deelvenster van de console. Regels voor updates die u importeert, kunnen alleen weergeven en wijzigen als u deze update bewerken.

U kunt regels maken op twee locaties in Updates Publisher:

-   In de **regels werkruimte** u maken en **opslaan** regelsets dat u kunt vervolgens later gebruiken. Tijdens het bewerken of maken van een update kunt u **opgeslagen regel** als de **regeltype**, en selecteer vervolgens in een lijst van de vooraf gemaakte regelsets.

-   U kunt ook nieuwe regels maken op het moment dat u maakt of bewerkt u een update. Regels die u op deze manier maakt worden niet opgeslagen voor toekomstig gebruik.

## <a name="create-applicability-rule"></a>Toepassingsregel maken
De volgende informatie is vergelijkbaar met hoe u regels vanuit maken de [maken bijwerken wizard](/sccm/sum/tools/create-updates-with-updates-publisher#the-create-update-wizard). Maar in tegenstelling tot de wizard hebt u de optie voor het opslaan van de regelsets voor toekomstig gebruik.

1.  In de **regels werkruimte**, kies **maken** openen de **regel maken** wizard.

2.  Geef een naam voor de regel en klik vervolgens op ![nieuwe regel](media/newrule.png). Hiermee opent u de **Toepassingsregel** pagina waar u regels kunt configureren.

3.  Voor **regeltype,** Selecteer een van de volgende. De opties die u moet configureren verschillen voor elk type:

    -   **Bestand** : deze regel gebruiken om te vereisen dat een apparaat een bestand met de eigenschappen die voldoen aan een of meer criteria die u voordat u deze update opgeeft kunnen worden toegepast.

    -   **Register –** gebruik van dit type Registerdetails die aanwezig zijn moeten voordat een apparaat in aanmerking komt voor het installeren van deze update opgeven.

    -   **Systeem:** met deze regel details van systeem gebruikt om te bepalen van de toepassing. U kunt kiezen tussen een Windows-versie, een Windows-taal, de processorarchitectuur definiëren of geef een WMI-query om te identificeren van het besturingssysteem van de apparaten.

    -   **Windows Installer –** dit regeltype gebruiken om te bepalen op basis van een geïnstalleerde toepassing. MSI- of Windows Installer-patch (. MSP). U kunt ook bepalen of bepaalde onderdelen of functies zijn geïnstalleerd als onderdeel van de vereiste.

       > [!IMPORTANT]   
       > Op beheerde deices, de Windows Update Agent kan niet worden geïnstalleerd door Windows-pakketten die zijn geïnstalleerd per gebruiker detecteren. Wanneer u dit regeltype gebruikt, regels voor toepasselijkheid aanvullende, zoals versies van bestanden of registersleutelwaarden zodanig configureren dat de Windows Installer-pakket correct ongeacht basis per gebruiker of per systeem kan worden gedetecteerd.

    -   **Regel: opgeslagen** deze optie kunt u zoeken en regels die u eerder hebt geconfigureerd en opgeslagen.

4.  Doorgaan met het toevoegen en configureer de gewenste extra regels.

5.  Gebruik de knoppen logische bewerking om te sorteren en groeperen van verschillende regels voor het maken, hoe complexer vereiste controles.

6.  Wanneer de regelset voltooid is, klikt u op **OK** op te slaan. Nu de regelset wordt weergegeven in de **Mijn opgeslagen regels** lijst.

## <a name="edit-applicability-rule-sets"></a>Toepasselijkheid regelsets bewerken
Een toepassingsregel bewerken de **regels werkruimte** selecteert u een regel die is opgeslagen in de **Mijn opgeslagen regels** lijst en kies vervolgens **bewerken** vanuit het lint. Hiermee opent u de **regel bewerken** wizard.

De **regel bewerken** wizard geeft de huidige regels voor de regelinstellingen. U de regels op dezelfde manier bewerken als u de **regel maken** wizard nieuwe regels maken. Deze wizard kunt u de regelinstellingen wijzigen, regels, regels opnieuw rangschikken en relaties verwijderen of nieuwe regels toevoegen.

Nadat u wijzigingen aanbrengt, kiest u **OK** de wijzigingen opslaan en sluiten van de wizard.

Zie voor meer informatie over het gebruik van de wizard regel voor **stap 7**, de pagina toepasbaarheid van de [maken bijwerken wizard](/sccm/sum/tools/create-updates-with-updates-publisher#the-create-update-wizard).

## <a name="delete-applicability-rules"></a>Regels voor toepasselijkheid verwijderen
Verwijderen van een opgeslagen toepassingsregel de **regels werkruimte** selecteert u de regel of de regelset van de **Mijn opgeslagen regels** lijst en kies vervolgens **verwijderen** vanuit het lint. Hiermee verwijdert u de opgeslagen regel of de regelset van Updates Publisher.

Als u wilt een regel verwijderen uit een specifieke update, moet u [bewerken van de update](/sccm/sum/tools/manage-updates-with-updates-publisher#edit-updates-and-bundles).
