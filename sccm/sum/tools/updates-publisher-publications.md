---
title: Publicaties beheren
titleSuffix: Configuration Manager
description: Groepen van software-updates beheren als een publicatie met System Center Updates Publisher
ms.custom: na
ms.date: 4/29/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: e6c1df1d-7728-4980-9199-bc32cde5439e
caps.latest.revision: "1"
author: mstewart
ms.author: mstewart
manager: angrobe
robots: NOINDEX, NOFOLLOW
ms.openlocfilehash: b9a0ee1e8d2efb96b082cdcdbaf1a4436128fb9f
ms.sourcegitcommit: 7fe45ff75f05f7cc03ad021db8119791abe18049
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/01/2017
---
# <a name="manage-publications-in-updates-publisher"></a>Publicaties in Updates Publisher beheren

*Van toepassing op: System Center Updates Publisher*

U kunt publicaties gebruiken om groepen te beheren van updates en bundels als een enkel object. Dit omvat de updates publiceren naar een beheerserver en de publicatie exporteren als groep voor gebruik met een andere installatie van Updates Publisher.

## <a name="create-publications"></a>Publicaties maken
Publicaties worden gemaakt op twee manieren:

-   Wanneer het beheren van updates en pakketten in de **werkruimte Updates**, kunt u [toewijzen](/sccm/sum/tools/manage-updates-with-updates-publisher#assign-updates-and-bundles-to-a-publication) ze naar een nieuwe publicatie die op dat moment wordt gemaakt.

-   In de **publicaties werkruimte** kunt u de **maken** knop op de **publicatie** tabblad van het lint. Deze methode maakt u een publicatie voor toekomstig gebruik. Wanneer u updates toewijst, kunt u later deze publicatie gebruiken.

## <a name="rename-a-publication"></a>Wijzig de naam van een publicatie
Wijzig de naam van een publicatie, selecteert u de publicatie van binnen de **publicaties werkruimte**, en klik vervolgens op de **publicatie** tabblad van het lint, kies **bewerken**.

## <a name="change-the-publication-type-of-updates-in-a-publication"></a>De publicatie van updates in een publicatie wijzigen
Van de **publicatie werkruimte**, kunt u de **publicatietype** van updates en pakketten die zijn toegewezen aan een publicatie.

1. Selecteer de publicatie met de updates die u wilt wijzigen, en selecteer vervolgens een of meer update- of bundels van de **alle &lt;publicatienaam > lid updates** lijst.

2. Volgende op de **Start** tabblad, kies een van de volgende opties. De opties die beschikbaar zijn, is afhankelijk van het type van de publicatie van de updates die u hebt geselecteerd.

  -   **Automatisch**
  -   **Volledige inhoud**
  -   **Alleen metagegevens**

Nadat u een wijziging, moet u mogelijk de publicatie weergave vernieuwen om te zien van de nieuwe waarden.

Zie voor meer informatie over de verschillende publicatietypen [updates en bundels toewijzen aan een publicatie](/sccm/sum/tools/manage-updates-with-updates-publisher#assign-updates-and-bundles-to-a-publication).

> [!TIP]    
> Wanneer u het type van de publicatie van een bundel instelt, worden de software-updates in die bundel met het publicatietype van die bundel gepubliceerd.

## <a name="remove-updates-from-a-publication"></a>Updates op een publicatie verwijderen
Updates of bundels verwijderen uit een publicatie in de **publicaties werkruimte** selecteert u de publicatie die u wilt wijzigen en selecteer vervolgens de updates en pakketten die u wilt verwijderen. Volgende op de **Start** tabblad van het lint, kies **verwijderen**.

Nadat updates zijn verwijderd uit een publicatie, blijven ze beschikbaar in de opslagplaats voor Updates Publisher.

## <a name="publish-publications"></a>Publicaties publiceren
Wanneer u updates en bundels publiceert, wordt informatie over deze updates en bundels (metagegevens) en mogelijk de binaire bestanden voor de updates (volledige inhoud) in Updates Publisher toegevoegd aan een updateserver voor implementatie op apparaten.

Voordat u de optie om te publiceren hebt, moet u de [updateserver](/sccm/sum/tools/updates-publisher-options#update-server) optie voor Updates Publisher. Als u wilt deze configuratieoptie openen, gaat u naar **werkruimte Updates** &gt; **overzicht** en selecteer **WSUS configureren en certificaat voor ondertekening.** U kunt ook gaan naar de updateserver pagina in de opties voor Updates Publisher.

> [!NOTE]   
> Updates die 375 megabytes (MB) of de grootte zijn kan alleen worden gepubliceerd in updates Publisher.

### <a name="to-publish-a-publication"></a>Voor het publiceren van een publicatie

1.  Ga naar de **publicaties werkruimte**, en selecteer vervolgens een publicatie met de groep van updates en pakketten die u wilt publiceren of te exporteren. Kies vervolgens **publiceren** van **Start** tabblad van het lint.

2.  Op de **Selecteer** pagina van de **publiceren** wizard kunt u voor het ondertekenen van alle updates met een nieuw certificaat voor de publicatie, maar u kunt het publicatietype niet wijzigen.

3.  Voltooi de wizard.

  Als het publiceren is mislukt, krijgt u een koppeling naar het bestand UpdatesPublisher.log met meer informatie.

## <a name="export-a-publication"></a>Exporteren van een publicatie
U kunt een publicatie exporteren uit de opslagplaats voor Updates Publisher. In dat geval exporteert u de updates en pakketten die zijn toegewezen aan deze publicatie en maakt u een update-catalogus. U kunt vervolgens [toevoegen](/sccm/sum/tools/updates-publisher-catalogs#add-software-update-catalogs) en vervolgens [importeren](/sccm/sum/tools/updates-publisher-catalogs#mport-updates) die catalogus naar een ander exemplaar van de Updates Publisher. U kunt ook [updates exporteren](/sccm/sum/tools/manage-updates-with-updates-publisher#export-updates) die geen deel uitmaken van een publicatie.

Als u wilt een publicatie exporteren, gaat u naar de **publicaties werkruimte** en selecteert u de publicatie die updates bevat die u wilt exporteren. U kunt slechts één publicatie op een tijdstip selecteren.

Met de publicatie is geselecteerd, kiest **exporteren** van de **Start** tabblad van het lint en geef een pad en bestandsnaam voor het exporteren van de catalogus.

U hebt ook de optie voor het exporteren (inclusief) afhankelijke software-updates als onderdeel van de export.

## <a name="rename-a-publication"></a>Wijzig de naam van een publicatie
Wijzig de naam van een publicatie, selecteert u de publicatie de **publicaties werkruimte**, en kies vervolgens **bewerken** van de **publicatie** tabblad van het lint.

## <a name="delete-a-publication"></a>Een publicatie verwijderen
Als u wilt een publicatie verwijderen, selecteert u de publicatie de **publicaties werkruimte**, en kies vervolgens **verwijderen** van de **publicatie** tabblad van het lint.

Nadat de publicatie van Updates Publisher wordt verwijderd, blijven de updates die in de publicatie zijn beschikbaar in de opslagplaats voor Updates Publisher.

## <a name="expire-or-reactivate-updates-and-bundles"></a>Verlopen of opnieuw activeren van updates en bundels
U kunt de **werkruimte Updates** om te selecteren en verlopen of opnieuw activeren van updates en bundels. U kunt verlopen en opnieuw activeren van updates en bundels zo vaak als u kiest.

-   **Verlopen updates of bundels**, selecteert u in de werkruimte Updates een of meer updates of die verzamelt niet zijn verlopen en kies vervolgens **verloopt** van de **Start** tabblad. Totdat u de update of bundel als verlopen naar Configuration Manager publiceert, kunt u het opnieuw activeren.

    Voordat u (verwijderen) een aangepaste update of bundel uit Configuration Manager verwijderen kunt, moet u deze verlopen en vervolgens die verlopen status publiceren naar Configuration Manager. Nadat updates of bundels in Configuration Manager verlopen, kunt u niet langer implementeren of opnieuw activeren van de update of bundel.

-   **Updates of bundels reactiveren**, selecteer een of meer updates die zijn verlopen en kies vervolgens in de werkruimte Updates **opnieuw activeren** van de **Start** tabblad van het lint. Als de verlopen update al is gepubliceerd als verlopen naar Configuration Manager, niet kunt u het opnieuw activeren.
