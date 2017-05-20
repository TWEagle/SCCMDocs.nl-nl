---
title: Publicaties beheren | Microsoft-documenten
description: Groepen van software-updates beheren als een publicatie met System Center Updates Publisher
ms.custom: na
ms.date: 4/29/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: e6c1df1d-7728-4980-9199-bc32cde5439e
caps.latest.revision: 1
author: Brenduns
ms.author: brenduns
manager: angrobe
robots: NOINDEX, NOFOLLOW
ms.translationtype: Machine Translation
ms.sourcegitcommit: 31819a1df4e63e1114682490a9b3c3b4e5c99cfa
ms.openlocfilehash: ddea7af935d5be880b96e383401061f8aa11e6da
ms.contentlocale: nl-nl
ms.lasthandoff: 05/17/2017

---
# <a name="manage-publications-in-updates-publisher"></a>Publicaties in Updates Publisher beheren

*Van toepassing op: System Center Updates Publisher*

U kunt publicaties gebruiken voor het beheren van groepen van updates en bundels als een enkel object. Dit omvat de updates publiceren naar een beheerserver en exporteren van de publicatie als groep voor gebruik met een andere installatie van Updates Publisher.

## <a name="create-publications"></a>Publicaties maken
Publicaties worden gemaakt op twee manieren:

-   Als u updates en bundels in beheert de **werkruimte Updates**, kunt u [toewijzen](/sccm/sum/tools/manage-updates-with-updates-publisher#assign-updates-and-bundles-to-a-publication) ze naar een nieuwe publicatie die op dat moment wordt gemaakt.

-   In de **publicaties werkruimte** kunt u de **maken** knop op de **publicatie** tabblad van het lint. Deze methode maakt u een publicatie voor toekomstig gebruik. Later, wanneer u updates toewijst, kunt u deze publicatie.

## <a name="rename-a-publication"></a>Wijzig de naam van een publicatie
Wijzig de naam van een publicatie, selecteert u de publicatie vanuit de **publicaties werkruimte**, en klik vervolgens op de **publicatie** tabblad van het lint kiezen **bewerken**.

## <a name="change-the-publication-type-of-updates-in-a-publication"></a>De publicatie van updates in een publicatie wijzigen
Van de **publicatie werkruimte**, kunt u de **publicatietype** van updates en pakketten die zijn toegewezen aan een publicatie.

1. Selecteer de publicatie met de updates die u wilt wijzigen en selecteer vervolgens een of meer update of bundels van de **alle &lt;publicatienaam > updates van** lijst.

2. Vervolgens worden op de **Start** Kies een van de volgende opties. De opties die beschikbaar zijn, is afhankelijk van het type van de publicatie van de updates die u hebt geselecteerd.

  -   **Automatisch**
  -   **Volledige inhoud**
  -   **Alleen metagegevens**

Na een wijziging doorvoert, moet u misschien Vernieuw de weergave van de publicatie voor de nieuwe waarden.

Zie voor meer informatie over de verschillende publicatietypen [updates en bundels toewijzen aan een publicatie](/sccm/sum/tools/manage-updates-with-updates-publisher#assign-updates-and-bundles-to-a-publication).

> [!TIP]    
> Als u het type van de publicatie van een bundel instelt, worden alle software-updates in die bundel gepubliceerd met het publicatietype van die bundel.

## <a name="remove-updates-from-a-publication"></a>Updates op een publicatie verwijderen
Updates of bundels verwijderen uit een publicatie de **publicaties werkruimte** selecteert u de publicatie die u wilt wijzigen en selecteer vervolgens de updates en pakketten die u wilt verwijderen. Vervolgens worden op de **Start** tabblad van het lint kiezen **verwijderen**.

Nadat updates zijn verwijderd uit een publicatie, blijven ze beschikbaar in de opslagplaats Updates Publisher.

## <a name="publish-publications"></a>Publicaties publiceren
Wanneer u updates en bundels publiceert, wordt informatie over deze updates en -bundels (metagegevens) en, waar mogelijk de binaire bestanden voor de updates (volledige inhoud) toegevoegd aan een updateserver voor implementatie op apparaten van Updates Publisher.

Voordat u de mogelijkheid om te publiceren hebt, moet u de [updateserver](/sccm/sum/tools/updates-publisher-options#update-server) optie voor Updates Publisher. Om te openen met deze configuratieoptie, gaat u naar **werkruimte Updates** &gt; **overzicht** en selecteer **WSUS configureren en het certificaat voor ondertekening.** U kunt ook gaan naar de updateserver pagina in de Updates Publisher-opties.

> [!NOTE]   
> Updates Publisher kan alleen updates die 375 megabytes (MB) of groot publiceren.

### <a name="to-publish-a-publication"></a>Publiceren van een publicatie

1.  Ga naar de **publicaties werkruimte**, en selecteer vervolgens een publicatie met de groep van updates en pakketten die u wilt publiceren of u wilt exporteren. Kies **publiceren** van **Start** tabblad van het lint.

2.  Op de **selecteren** pagina van de **publiceren** wizard kunt u alle updates met een nieuw publishing certificaat ondertekenen, maar u kunt het publicatietype niet wijzigen.

3.  Voltooi de wizard.

  Als de publicatie is mislukt, verschijnt er een koppeling naar het bestand UpdatesPublisher.log met meer informatie.

## <a name="export-a-publication"></a>Exporteren van een publicatie
U kunt een publicatie van uw opslagplaats Updates Publisher exporteren. Hiermee exporteert u de updates en pakketten die zijn toegewezen aan de publicatie en maakt u een update-catalogus. U kunt vervolgens [toevoegen](/sccm/sum/tools/updates-publisher-catalogs#add-software-update-catalogs) en vervolgens [importeren](/sccm/sum/tools/updates-publisher-catalogs#mport-updates) die catalogus naar een ander exemplaar van Updates Publisher. U kunt ook [updates exporteren](/sccm/sum/tools/manage-updates-with-updates-publisher#export-updates) die geen deel uitmaken van een publicatie.

Voor het exporteren van een publicatie, gaat u naar de **publicaties werkruimte** en selecteert u de publicatie die updates bevat die u wilt exporteren. U kunt slechts één publicatie op een tijdstip selecteren.

Met de publicatie is geselecteerd, kiezen **exporteren** van de **Start** tabblad van het lint en geeft u een pad en bestandsnaam voor het exporteren van de catalogus.

U hebt ook de mogelijkheid om te exporteren (inclusief) afhankelijke software-updates als onderdeel van de export.

## <a name="rename-a-publication"></a>Wijzig de naam van een publicatie
Wijzig de naam van een publicatie, selecteert u de publicatie de **publicaties werkruimte**, en kies vervolgens **bewerken** van de **publicatie** tabblad van het lint.

## <a name="delete-a-publication"></a>Een publicatie verwijderen
Als u wilt een publicatie verwijderen, selecteert u de publicatie de **publicaties werkruimte**, en kies vervolgens **verwijderen** van de **publicatie** tabblad van het lint.

Nadat de publicatie van Updates Publisher wordt verwijderd, blijven de updates die in de publicatie zijn beschikbaar in de opslagplaats Updates Publisher.

## <a name="expire-or-reactivate-updates-and-bundles"></a>Verlopen of opnieuw activeren van updates en bundels
U kunt de **werkruimte Updates** om te selecteren en verlopen of opnieuw activeren van updates en bundels. U kunt verlopen en opnieuw activeren van updates en bundels zo vaak als u kiest.

-   **Verlopen updates of bundels**, selecteert u in de werkruimte Updates een of meer updates of die verzamelt niet zijn verlopen en kies vervolgens **laten verlopen** van de **Start** tabblad. Totdat u de update of bundel als verlopen naar Configuration Manager publiceert, kunt u het opnieuw activeren.

    Voordat u (verwijderen) een aangepaste update of bundel uit Configuration Manager verwijderen kunt, moet u deze verlopen en publiceert die verlopen status naar Configuration Manager. Nadat updates of bundels in Configuration Manager verlopen, kunt u niet langer implementeren of opnieuw activeren van de update of bundel.

-   **Opnieuw activeren van updates of bundels**, selecteer een of meer updates die zijn verlopen en kies vervolgens in de werkruimte Updates **opnieuw activeren** van de **Start** tabblad van het lint. Als de update verlopen is eerder is gepubliceerd als verlopen naar Configuration Manager, niet u het opnieuw activeren.

