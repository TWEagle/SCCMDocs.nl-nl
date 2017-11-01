---
title: Updates beheren
titleSuffix: Configuration Manager
description: De updates die u implementeert en maken met System Center Updates Publisher beheren
ms.custom: na
ms.date: 4/29/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: cd64994c-b426-4465-96cd-54b0edc2778d
caps.latest.revision: "1"
author: Brenduns
ms.author: brenduns
manager: angrobe
robots: NOINDEX, NOFOLLOW
ms.openlocfilehash: 19a1a84a58923d3345852fc1245a524e7f246e5b
ms.sourcegitcommit: c236214b2fcc13dae7bad96d7fb33f692868191d
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/12/2017
---
# <a name="manage-software-updates-in-updates-publisher"></a>Software-updates in Updates Publisher beheren

*Van toepassing op: System Center Updates Publisher*     

In System Center Updates Publisher, gebruikt u de **werkruimte Updates** voor het beheren van software-updates en pakketten die u hebt geïmporteerd in de opslagplaats.  

Beheertaken bevatten dupliceren, bewerken en verloopt of opnieuw activeren van updates en pakketten, toewijzen en updates bundels publicaties. U kunt ook aangepaste catalogussen voor gebruik met andere installaties van Updates Publisher exporteren.

Ophalen van updates die u kunt beheren:
-  [Toevoegen van een update-catalogus](/sccm/sum/tools/updates-publisher-catalogs#add-software-update-catalogs) op de installatie van Updates Publisher
-  [Importeren](/sccm/sum/tools/updates-publisher-catalogs#import-updates) de updates uit die catalogus naar uw opslagplaats.

U kunt ook [maken van uw eigen updates](/sccm/sum/tools/create-updates-with-updates-publisher).



## <a name="create-a-duplicate-of-an-update"></a>Een duplicaat van een update maken
U kunt duplicaten, of een kopie van de updates die in de opslagplaats maken. Vervolgens kunt u de kopie in plaats van het wijzigen van de oorspronkelijke update wijzigen. U kunt geen kopieën van updatebundels maken.

Als u wilt een kopie maken, selecteer een update in de **werkruimte Updates**, en kies vervolgens **dubbele**. De kopie van de update wordt weergegeven op dezelfde locatie in de werkruimte Updates met *kopiëren van* toegevoegd aan de naam ervan.

Een nieuw exemplaar dat u maakt, heeft de status van **Unexpired**, maar de instellingen van de oorspronkelijke anders behoudt.

## <a name="edit-updates-and-bundles"></a>Updates en bundels bewerken
U kunt updates en bundels die zich in uw opslagplaats wijzigen.

In de **werkruimte Updates** selecteert u een update of bundel en selecteer vervolgens **bewerken** van de **Start** tabblad om de wizard bewerken te openen. Updates en bundels hebt afzonderlijke maar nauw verwante wizards die beschikken over dezelfde opties als de [maken bijwerken](/sccm/sum/tools/create-updates-with-updates-publisher#the-create-update-wizard) of [bundel maken](/sccm/sum/tools/create-updates-with-updates-publisher#the-create-bundle-wizard) wizards.

Wanneer u bewerkt, kunt u alle beschikbare details over de update wijzigen of bundel zodat deze kan worden gebruikt in uw omgeving. U kunt bijvoorbeeld, bewerk de regels voor toepasselijkheid of prioriteit of de taal te wijzigen. U kunt ook wijzigen in het product en de leverancier van de update verplaatsen of bundel naar een aangepaste map groep updates voor uw eigen gebruik.

## <a name="assign-updates-and-bundles-to-a-publication"></a>Updates en bundels toewijzen aan een publicatie
Kunt u updates en pakketten in de **werkruimte Updates** en kies vervolgens **toewijzen** van de **Start** tabblad van het lint toe te voegen aan een publicatie. Hiermee start u de **toewijzen van Software-Updates** wizard.
-  Zie [publiceren van updates en bundels](#publish-updates-and-bundles-from-the-updates-workspace) voor informatie over het selecteren en updates en bundels publiceren als een enkele taak.
-  Zie [beheren publicaties](/sccm/sum/tools/updates-publisher-publications) voor informatie over het beheren van groepen van updates en bundels als een enkel object. Nadat u de updates op een publicatie toewijst, kunt u publicatie, waaronder op zijn beurt alle toegewezen updates kunt beheren.

Wanneer u updates toewijst aan een publicatie:

-   U kunt verlopen en niet verlopen updates en bundels opnemen in dezelfde publicatie.

-   Geef het publicatietype:

    -   **Volledige inhoud** – Hiermee publiceert u de volledige inhoud van de update naar uw WSUS-Server. Dit omvat metagegevens en de binaire updatebestanden.

    -   **Alleen metagegevens** – Hiermee alleen de metagegevens publiceert; binaire updatebestanden worden niet gepubliceerd. U kunt deze optie als u wilt verzamelen van Nalevingsgegevens.

    -   **Automatische** – deze modus is alleen beschikbaar wanneer u naar Configuration Manager hebt verbonden voor Updates Publisher (Zie de [Configuration Manager-Server](/sccm/sum/tools/updates-publisher-options#configmgr-server) optie.)

    Met dit type query Updates Publisher Configuration Manager om te bepalen of de updates of bundels moeten worden gepubliceerd met de volledige inhoud of alleen metagegevens. Volledige inhoud van een update is gepubliceerd, alleen wanneer dat werk voldoet aan de **drempelwaarde voor het aantal aangevraagde client** en **pakket bron grootte drempelwaarde** die zijn opgegeven op de **Configuration Manager-Server** pagina van de opties voor Updates Publisher.

-   Selecteer een publicatie:

    -   Gebruik **software-update toewijzen aan bestaande publicaties** wanneer u een publicatie die u wilt gebruiken al hebt gemaakt. Deze optie is niet beschikbaar totdat er ten minste één publicatie bestaat.

    -   Gebruik **software-update toewijzen aan een nieuwe publicatie** wanneer u niet over een geschikte publicatie. Hiermee wordt een nieuwe publicatie gemaakt met de naam die u opgeeft.

Nadat u de updates op een publicatie toewijst, kunt u de **publicatie werkruimte** naar [publiceren](/sccm/sum/tools/updates-publisher-publications#publish-pubilcations) of [exporteren](/sccm/sum/tools/updates-publisher-publications#export-a-pubilcation) de publicatie als een groep.

## <a name="publish-updates-and-bundles-from-the-updates-workspace"></a>Updates en bundels vanuit de werkruimte Updates publiceren
Wanneer u updates en bundels publiceert, wordt informatie over deze updates en bundels (metagegevens) en mogelijk de binaire bestanden voor de updates (volledige inhoud) in Updates Publisher toegevoegd aan een updateserver voor implementatie op apparaten.

Voordat u de optie om te publiceren hebt, moet u de [updateserver](/sccm/sum/tools/updates-publisher-options#update-server) optie voor Updates Publisher. Als u wilt deze configuratieoptie openen, gaat u naar **werkruimte Updates** &gt; **overzicht** en selecteer **WSUS configureren en certificaat voor ondertekening.** U kunt ook gaan naar de updateserver pagina in de opties voor Updates Publisher.

Er zijn twee manieren om updates en bundels te publiceren:
-   Rechtstreeks vanuit de werkruimte Updates. (Zie de volgende procedure *voor het publiceren van updates en bundels*.)
-   Als een [publicatie](/sccm/sum/tools/updates-publisher-publications#publish-pubilcations) vanuit de werkruimte publicaties.  

> [!NOTE]   
> Updates die 375 megabytes (MB) of de grootte zijn kan alleen worden gepubliceerd in updates Publisher.

### <a name="to-publish-updates-and-bundles"></a>Updates en bundels publiceren
1.  Ga naar **werkruimte Updates** en selecteer een of meer updates en pakketten die u wilt publiceren. Kies vervolgens **publiceren** van **Start** tabblad van het lint.

2.  Op de **Selecteer** pagina van de **publiceren** wizard, selecteer hoe wilt u de updates publiceren. De opties zijn hetzelfde als voor [updates toe te wijzen](#assign-updates-and-bundles-to-a-publication): **Volledige inhoud**, **bestaan alleen uit metagegevens**, of **automatische**.

    U kunt ook voor het ondertekenen van alle updates met een nieuw certificaat voor de publicatie.

3.  Voltooi de wizard.

Als het publiceren is mislukt, krijgt u een koppeling naar het bestand UpdatesPublisher.log met meer informatie.

## <a name="export-updates"></a>Het exporteren van updates
U kunt updates en bundels exporteren van uw opslagplaats Updates Publisher te maken van een aangepaste update-catalogus. Vervolgens kunt u [toevoegen](/sccm/sum/tools/updates-publisher-catalogs#add-software-update-catalogs) en vervolgens [importeren](/sccm/sum/tools/updates-publisher-catalogs#mport-updates) die catalogus naar een ander exemplaar van de Updates Publisher. (U kunt ook [updates exporteren als een publicatie](/sccm/sum/tools/updates-publisher-publications##export-a-publication).)

Als u wilt exporteren rechtstreeks, gaat u naar **werkruimte Updates** > **alle Software-Updates** en selecteer een of meer updates en bundels. U kunt een leverancier of de hoofdmap van het product niet exporteren, maar u kunt een map selecteren en selecteer vervolgens de updates in de map voor uitvoer.

Met een of meer updates geselecteerd, kiest **exporteren** van de **Start** tabblad van het lint en geef een pad en bestandsnaam voor het exporteren van de catalogus.

U hebt de mogelijkheid om te exporteren (inclusief) afhankelijke software-updates.

## <a name="delete-updates-and-bundles"></a>Updates en bundels verwijderen
U kunt updates en bundels van updates om ze te verwijderen uit de opslagplaats voor Updates Publisher verwijderen.

Ga naar **werkruimte Updates** > **alle Software-Updates** en selecteer een of meer afzonderlijke updates. Kies vervolgens **verwijderen** van de **Start** tabblad van het lint.

-   Als de selectie bevat alleen updates of pakketten die niet zijn gepubliceerd of die zijn verstreken, wordt u gevraagd te bevestigen voordat ze worden verwijderd.

-   Als uw selectie bevat een update of bundel die is gepubliceerd en nog niet is verlopen, krijgt u een waarschuwing. U moet [verlopen](/sccm/sum/tools/updates-publisher-pubilcations#expire-or-reactivate-updates-and-bundles) die updates en vervolgens die wijziging publiceren voordat u deze uit de opslagplaats verwijderen.  

Als u een update te verwijderen of bundel van een leverancier en vervolgens opnieuw die catalogus importeren, wordt deze update wordt teruggezet naar uw opslagplaats.

## <a name="manage-vendor-and-product-folders"></a>Leverancier en product mappen beheren
Voor een lijst met leveranciers en producten voor elke leverancier waarvoor u hebt geïmporteerd of updates gemaakt, gaat u naar **werkruimte Updates** > **overzicht** > **alle Software-Updates**.

Mappen voor leveranciers en -producten worden automatisch door Updates Publisher gemaakt wanneer u een wizard gebruiken om te importeren of een software-update of bundel maken. U kunt deze mappen ook handmatig maken.

-   Een Leveranciermap maken in het navigatievenster van de **werkruimte Updates**, met de rechtermuisknop op **alle Software-Updates**, en kies vervolgens **maken leverancier**.

-   Met de rechtermuisknop op de Leveranciermap voor het maken van een productmap onder de Leveranciermap van een, en kies **Product maken**.

U kunt naast het maken van mappen wijzigen of verwijderen van een leverancier of de hoofdmap van het product in de opslagplaats. Dit doet, met de rechtermuisknop op de map en kies de gewenste optie **naam** of **verwijderen**. Een map verwijdert, wordt de updates en bundels in die map en bijbehorende mappen product uit de opslagplaats voor Updates Publisher.

U kunt updates verplaatsen tussen leverancier en product mappen, met inbegrip van mappen die u maakt. Als u wilt verplaatsen van een update of naar een nieuwe map te bundelen, u moet selecteren en vervolgens **bewerken** update of bundel. Klik op de **informatie** pagina van de wizard Update bewerken kunt u de leverancier en product toewijzen. Wanneer de **bewerken bijwerken** wizard is voltooid, wordt de wijziging toegepast en de update wordt verplaatst naar de nieuwe map.

## <a name="view-the-xml-of-an-update-or-bundle"></a>De XML van een update of bundel weergeven
U kunt selecteren van een update of bundel de **werkruimte Updates** en kies vervolgens **weergave** XML om weer te geven van de XML-structuur van de update. Er zijn geen opties in de XML-structuur om rechtstreeks te bewerken.
