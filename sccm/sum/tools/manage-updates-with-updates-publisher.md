---
title: Beheren van updates | Microsoft-documenten
description: De updates die u implementeert en maakt met System Center Updates Publisher beheren
ms.custom: na
ms.date: 4/29/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: cd64994c-b426-4465-96cd-54b0edc2778d
caps.latest.revision: 1
author: Brenduns
ms.author: brenduns
manager: angrobe
robots: NOINDEX, NOFOLLOW
ms.translationtype: Machine Translation
ms.sourcegitcommit: 90775fcf2549080a43e9c1606caa79d9eb90a89c
ms.openlocfilehash: 1d6c3b1db14867bdbc5cae8ded099d9024a79549
ms.contentlocale: nl-nl
ms.lasthandoff: 05/17/2017

---
# <a name="manage-software-updates-in-updates-publisher"></a>Software-updates in Updates Publisher beheren

*Van toepassing op: System Center Updates Publisher*     

In System Center Updates Publisher, gebruikt u de **werkruimte Updates** voor het beheren van software-updates en pakketten die u hebt geïmporteerd naar de bibliotheek.  

Beheertaken zijn dupliceren, bewerken en verlopen of opnieuw activeren van updates en bundels, toewijzen en updates bundels publicaties. U kunt ook aangepaste catalogussen voor gebruik met andere installaties van Updates Publisher exporteren.

Om updates te downloaden die u kunt beheren:
-  [Toevoegen van een update-catalogus](/sccm/sum/tools/updates-publisher-catalogs#add-software-update-catalogs) op uw installatie van Updates Publisher
-  [Importeren](/sccm/sum/tools/updates-publisher-catalogs#import-updates) de updates uit deze catalogus naar uw opslagplaats.

U kunt ook [maken van uw eigen updates](/sccm/sum/tools/create-updates-with-updates-publisher).



## <a name="create-a-duplicate-of-an-update"></a>Een duplicaat van een update maken
U kunt dubbele waarden of een kopie van de updates die in uw opslagplaats maken. Vervolgens kunt u de kopie in plaats van het wijzigen van de oorspronkelijke update wijzigen. U kunt geen kopieën van updatebundels maken.

Als u een kopie maakt, selecteert u een update in de **werkruimte Updates**, en kies vervolgens **dubbele**. De kopie van de update wordt weergegeven in dezelfde locatie in de werkruimte Updates met *kopiëren van* toegevoegd aan de naam ervan.

Een nieuw exemplaar dat u maakt een status heeft van **Unexpired**, maar worden de instellingen van de oorspronkelijke anders behouden.

## <a name="edit-updates-and-bundles"></a>Updates en bundels bewerken
U kunt updates selecteren en bundels die zich in de bibliotheek om ze te wijzigen.

In de **werkruimte Updates** selecteert u een update of bundel en selecteer vervolgens **bewerken** van de **Start** tabblad om de wizard bewerken te openen. Updates en bundels hebben afzonderlijke maar nauw verwante wizards die beschikken over dezelfde opties als de [maken bijwerken](/sccm/sum/tools/create-updates-with-updates-publisher#the-create-update-wizard) of [bundel maken](/sccm/sum/tools/create-updates-with-updates-publisher#the-create-bundle-wizard) wizards.

Wanneer u bewerkt, kunt u alle beschikbare details over de update wijzigen of bundelen zodat het kan worden gebruikt in uw omgeving. U kunt bijvoorbeeld de regels voor toepasselijkheid of prioriteit bewerken of de taal te wijzigen. U kunt ook het product en de leverancier van uw bundelen in een aangepaste map groep updates voor uw eigen gebruik of verplaatsen van de update wijzigen.

## <a name="assign-updates-and-bundles-to-a-publication"></a>Updates en bundels toewijzen aan een publicatie
U kunt updates selecteren en pakketten in de **werkruimte Updates** en kies vervolgens **toewijzen** van de **Start** tabblad van het lint te voegen aan een publicatie. Hiermee start u de **toewijzen van Software-Updates** wizard.
-  Zie [publiceren updates en bundels](#publish-updates-and-bundles-from-the-updates-workspace) voor informatie over het selecteren en -updates en bundels publiceren als een enkele taak.
-  Zie [beheren publicaties](/sccm/sum/tools/updates-publisher-publications) voor meer informatie over het beheren van groepen van updates en bundels als een enkel object. Nadat u de updates op een publicatie toewijst, kunt u de publicatie, waaronder op zijn beurt de toegewezen updates kunt beheren.

Wanneer u updates toewijst aan een publicatie:

-   U kunt verlopen en niet verlopen updates en bundels opnemen in dezelfde publicatie.

-   Geef op de publicatietype:

    -   **Volledige inhoud** – dit publiceert de volledige inhoud van de update naar de WSUS-Server. Dit omvat metagegevens en de binaire updatebestanden.

    -   **Alleen metagegevens** – dit alleen de metagegevens publiceert; binaire bestanden worden niet gepubliceerd. U kunt deze optie als u wilt verzamelen compatibiliteitsgegevens.

    -   **Automatische** – deze modus is alleen beschikbaar wanneer u verbinding hebt gemaakt Updates Publisher naar Configuration Manager (Zie de [Configuration Manager-Server](/sccm/sum/tools/updates-publisher-options#configmgr-server) optie.)

    Met dit type query Updates Publisher Configuration Manager om te bepalen of updates of bundels moeten worden gepubliceerd met de volledige inhoud of alleen metagegevens. Volledige inhoud van een update is gepubliceerd, alleen wanneer die voldoet aan de **drempelwaarde verzocht client aantal** en **pakket bron grootte drempelwaarde** die zijn opgegeven op de **Configuration Manager-Server** pagina van de opties voor Updates Publisher.

-   Selecteer een publicatie:

    -   Gebruik **software-update toewijzen aan bestaande publicaties** wanneer u een publicatie die u wilt gebruiken al hebt gemaakt. Deze optie is niet beschikbaar totdat er ten minste één publicatie bestaat.

    -   Gebruik **software-update toewijzen aan een nieuwe publicatie** wanneer u niet over een geschikte publicatie. Hiermee wordt een nieuwe publicatie gemaakt met de naam die u opgeeft.

Nadat u de updates op een publicatie toewijst, kunt u de **publicatie werkruimte** naar [publiceren](/sccm/sum/tools/updates-publisher-publications#publish-pubilcations) of [exporteren](/sccm/sum/tools/updates-publisher-publications#export-a-pubilcation) de publicatie als een groep.

## <a name="publish-updates-and-bundles-from-the-updates-workspace"></a>Updates en bundels vanuit de werkruimte Updates publiceren
Wanneer u updates en bundels publiceert, wordt informatie over deze updates en -bundels (metagegevens) en, waar mogelijk de binaire bestanden voor de updates (volledige inhoud) toegevoegd aan een updateserver voor implementatie op apparaten van Updates Publisher.

Voordat u de mogelijkheid om te publiceren hebt, moet u de [updateserver](/sccm/sum/tools/updates-publisher-options#update-server) optie voor Updates Publisher. Om te openen met deze configuratieoptie, gaat u naar **werkruimte Updates** &gt; **overzicht** en selecteer **WSUS configureren en het certificaat voor ondertekening.** U kunt ook gaan naar de updateserver pagina in de Updates Publisher-opties.

Er zijn twee manieren om updates en bundels te publiceren:
-   Rechtstreeks vanuit de werkruimte Updates. (Zie de volgende procedure *voor het publiceren van updates en bundels*.)
-   Als een [publicatie](/sccm/sum/tools/updates-publisher-publications#publish-pubilcations) vanuit de werkruimte publicaties.  

> [!NOTE]   
> Updates Publisher kan alleen updates die 375 megabytes (MB) of groot publiceren.

### <a name="to-publish-updates-and-bundles"></a>Updates en bundels publiceren
1.  Ga naar **werkruimte Updates** en selecteer een of meer updates en pakketten die u wilt publiceren. Kies **publiceren** van **Start** tabblad van het lint.

2.  Op de **selecteren** pagina van de **publiceren** wizard, selecteert u hoe u wilt de updates publiceren. De opties zijn hetzelfde als voor [updates toe te wijzen](#assign-updates-and-bundles-to-a-publication): **Volledige inhoud**, **bestaan alleen uit metagegevens**, of **automatische**.

    U kunt ook alle updates met een nieuw publishing certificaat ondertekenen.

3.  Voltooi de wizard.

Als de publicatie is mislukt, verschijnt er een koppeling naar het bestand UpdatesPublisher.log met meer informatie.

## <a name="export-updates"></a>Het exporteren van updates
U kunt updates en bundels exporteren van uw opslagplaats Updates Publisher te maken van een aangepaste update-catalogus. Vervolgens kunt u [toevoegen](/sccm/sum/tools/updates-publisher-catalogs#add-software-update-catalogs) en vervolgens [importeren](/sccm/sum/tools/updates-publisher-catalogs#mport-updates) die catalogus naar een ander exemplaar van Updates Publisher. (U kunt ook [updates exporteren als een publicatie](/sccm/sum/tools/updates-publisher-publications##export-a-publication).)

Voor het rechtstreeks exporteren, gaat u naar **werkruimte Updates** > **alle Software-Updates** en selecteer een of meer updates en bundels. U kunt een leverancier of de hoofdmap van het product niet exporteren, maar u kunt een map selecteren en selecteer vervolgens de updates in de map voor uitvoer.

Met een of meer updates geselecteerd, kiezen **exporteren** van de **Start** tabblad van het lint en geeft u een pad en bestandsnaam voor het exporteren van de catalogus.

U hebt de mogelijkheid om te exporteren (inclusief) afhankelijke software-updates.

## <a name="delete-updates-and-bundles"></a>Updates en bundels verwijderen
U kunt updates en bundels van updates om ze te verwijderen van de opslagplaats Updates Publisher verwijderen.

Ga naar **werkruimte Updates** > **alle Software-Updates** en selecteer een of meer afzonderlijke updates. Kies **verwijderen** van de **Start** tabblad van het lint.

-   Als uw selectie bevat alleen updates of pakketten die niet zijn gepubliceerd of die zijn verlopen, wordt u gevraagd om verwijdering te bevestigen voordat ze worden verwijderd.

-   Als uw selectie bevat een update of een bundel die is gepubliceerd en nog niet is verlopen, krijgt u een waarschuwing. U moet [verlopen](/sccm/sum/tools/updates-publisher-pubilcations#expire-or-reactivate-updates-and-bundles) die updates op en publiceert u deze wijziging voordat u deze uit de bibliotheek verwijderen.  

Als u een update te verwijderen of van een leverancier bundelen en vervolgens opnieuw die catalogus importeren, wordt deze update naar uw opslagplaats hersteld.

## <a name="manage-vendor-and-product-folders"></a>Leverancier en product mappen beheren
Voor een lijst met leveranciers en producten voor elke leverancier waarvoor u hebt geïmporteerd of updates gemaakt, gaat u naar **werkruimte Updates** > **overzicht** > **alle Software-Updates**.

Mappen voor leveranciers en producten worden automatisch gemaakt door de Updates Publisher wanneer u een wizard gebruiken om te importeren of een software-update of bundel maken. U kunt deze mappen ook handmatig maken.

-   Een Leveranciermap maken in het navigatievenster van de **werkruimte Updates**, met de rechtermuisknop op **alle Software-Updates**, en kies vervolgens **leverancier maken**.

-   Met de rechtermuisknop op de Leveranciermap voor het maken van een productmap onder de Leveranciermap van een en kies **Product maken**.

U kunt naast het maken van mappen, wijzigen of verwijderen van een leverancier of de hoofdmap van het product in de bibliotheek. Om te doen, met de rechtermuisknop op de map en kiest u de gewenste optie, **naam** of **verwijderen**. Een map verwijdert, wordt de updates en bundels in die map en bijbehorende mappen product van de opslagplaats Updates Publisher.

U kunt updates verplaatsen tussen leverancier en product mappen, met inbegrip van mappen die u maakt. U moet selecteren voor het verplaatsen van een update of bundelen in een nieuwe map, en vervolgens **bewerken** update of bundel. Klik vervolgens op de **informatie** pagina van de wizard Update bewerken kunt u de leverancier en product toewijzen. Wanneer de **bewerken bijwerken** wizard is voltooid, wordt de wijziging toegepast en de update wordt verplaatst naar de nieuwe map.

## <a name="view-the-xml-of-an-update-or-bundle"></a>De XML van een update of bundel weergeven
U kunt één update selecteren of bundelen de **werkruimte Updates** en kies vervolgens **weergave** XML om weer te geven van de XML-structuur van de update. Er zijn geen opties voor de XML-structuur rechtstreeks bewerken.

