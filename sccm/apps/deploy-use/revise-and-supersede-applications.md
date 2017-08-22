---
title: Toepassingen herzien en vervangen | Microsoft Docs
description: Informatie over het werken met versies van System Center Configuration Manager-toepassingen en toepassingen vervangen.
ms.custom: na
ms.date: 10/06/2016
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: configmgr-app
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 30170d70-489f-47f7-bebf-9ed0115db26b
caps.latest.revision: "7"
caps.handback.revision: "0"
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.openlocfilehash: 28bea9210c9c58dabbb00a995e78cfedd1738291
ms.sourcegitcommit: 51fc48fb023f1e8d995c6c4eacfda7dbec4d0b2f
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 08/07/2017
---
# <a name="revise-and-supersede-applications-in-system-center-configuration-manager"></a>Toepassingen in System Center Configuration Manager herzien en vervangen

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*

In dit onderwerp leert u hoe u werkt met toepassingsversies van System Center Configuration Manager-en het vervangen van toepassingen met een nieuwe versie.  

##  <a name="application-revisions"></a>Revisies van toepassing  
 Wanneer u wijzigingen aanbrengt in een toepassing of een implementatietype dat deel uitmaakt van een toepassing, maakt Configuration Manager een nieuwe revisie van de toepassing. U kunt de geschiedenis van elke toepassingsrevisie weergeven. Daarnaast kunt u de eigenschappen weergeven, een eerdere revisie van een toepassing herstellen of een oude revisie verwijderen.  

### <a name="to-display-an-application-revision-history"></a>De revisiegeschiedenis voor een toepassing weergeven  

1.  Kies in de Configuration Manager-console **softwarebibliotheek** > **Toepassingsbeheer** > **toepassingen**, en kies vervolgens de toepassing die u wenst.  

3.  Op de **Start** tabblad, in de **toepassing** groep, kiest u **revisiegeschiedenis** openen de **overzicht van Toepassingsrevisies** in het dialoogvenster.  

### <a name="to-view-an-application-revision"></a>Een toepassingsrevisie weergeven  

1.  In de **overzicht van Toepassingsrevisies** Selecteer een toepassingsrevisie in het dialoogvenster en kies vervolgens **weergave**.  

2.  In het dialoogvenster **Eigenschappen** controleert u de eigenschappen van de geselecteerde toepassing.  

    > [!NOTE]  
    >  De toepassingseigenschappen die worden weergegeven, zijn alleen-lezen.  

3.  Sluit het dialoogvenster **Eigenschappen** .  

### <a name="to-restore-an-application-revision"></a>Een toepassingsrevisie herstellen  

1.  In de **overzicht van Toepassingsrevisies** Selecteer een toepassingsrevisie in het dialoogvenster en kies vervolgens **herstellen**.  

2.  In de **terugzetten bevestigen** dialoogvenster Kies **Ja** om de geselecteerde toepassingsrevisie te herstellen.  

### <a name="to-delete-an-application-revision"></a>Een toepassingsrevisie verwijderen  

1.  In de **overzicht van Toepassingsrevisies** Selecteer een toepassingsrevisie in het dialoogvenster en kies vervolgens **verwijderen**.  

2.  In de **Toepassingsrevisie verwijderen** dialoogvenster Kies **Ja**.  

> [!IMPORTANT]  
>  U kunt de huidige toepassingsrevisie alleen verwijderen als de toepassing buiten gebruik is gesteld en geen verwijzingen bevat.  

##  <a name="application-supersedence"></a>Vervanging van toepassingen  
 Toepassingsbeheer in Configuration Manager kunt u upgraden of vervangen van bestaande toepassingen met behulp van een vervangingsrelatie. Wanneer u een toepassing vervangt, kunt u een nieuw implementatietype voor het implementatietype van de vervangen toepassing vervangen en ook bepalen of wilt upgraden of verwijderen van de vervangen toepassing voordat de vervangende toepassing is geïnstalleerd.  

> [!IMPORTANT]  
>  Wanneer u de optie voor het verwijderen van het vervangen implementatietype selecteert, kunt u dit implementatietype niet vervangen door een implementatietype dat is toegepast op een ander type verzameling.  Als u de optie voor het verwijderen van het vervangen implementatietype hebt geselecteerd, kunt u een implementatietype dat op een apparaatverzameling is geïmplementeerd bijvoorbeeld niet vervangen door een implementatietype dat op een gebruikersverzameling is geïmplementeerd.  

### <a name="decide-whether-to-upgrade-or-replace-an-application"></a>Bepalen of u een toepassing wilt bijwerken of vervangen  
 In het dialoogvenster met toepassingseigenschappen kunt u in het dialoogvenster **Geef vervangingsrelatie op** aangeven of u een app wilt vervangen of bijwerken. Het type vervanging is afhankelijk van of de optie **Verwijderen** is ingeschakeld in dit dialoogvenster:  

-   Als u wilt bijwerken naar een nieuwere versie van dezelfde toepassing (met dezelfde toepassings-ID), **niet** controleren **verwijderen**.  

-   Als u een andere toepassing wilt gebruiken (met een andere toepassings-id), schakelt u **Verwijderen**in. U moet de vervangen versie van de toepassing te verwijderen.  

### <a name="supersede-dependent-applications"></a>Afhankelijke toepassingen vervangen  
 In dit voorbeeld **de hoofdsleutel van de toepassing** verwijst naar de app die u implementeert die de afhankelijkheden heeft.  

 U kunt een vervangingsrelatie maken die de afhankelijke toepassing bijwerkt naar een nieuwe versie.  

1.  Zorg ervoor dat de nieuwe afhankelijke toepassing en de oorspronkelijke afhankelijke toepassing zich in dezelfde afhankelijkheidsgroep bevinden als de hoofdtoepassing.  

2.  Maak een vervangingsrelatie waarbij de oorspronkelijke afhankelijke toepassing wordt vervangen door de nieuwe afhankelijke toepassing.  

 Tijdens nieuwe installaties van de hoofdtoepassing is de nieuwe afhankelijke toepassing geïnstalleerd. Bestaande installaties van de hoofdtoepassing worden bijgewerkt met de nieuwe afhankelijke toepassing.  

 Het eindresultaat is dat alle implementaties van de hoofdtoepassing de nieuwe afhankelijke toepassing gebruiken.  

### <a name="further-considerations"></a>Verdere overwegingen  

-   U kunt meerdere vervangingsrelaties opgeven voor afhankelijke toepassingen. De hoogste afhankelijke toepassing in de vervangingsketen wordt geïnstalleerd.  

-   Afhankelijke toepassingen moeten worden geïmplementeerd op het apparaat waarop de hoofdtoepassing is geïnstalleerd of de afhankelijke toepassing won't geïnstalleerd.  

-   Als u meerdere afhankelijkheden hebt, bepaalt de afhankelijkheidsvolgorde welke versie van de afhankelijke toepassing voor nieuwe installaties van de hoofdtoepassing wordt geïnstalleerd.  

### <a name="to-specify-a-supersedence-relationship"></a>Een vervangingsrelatie opgeven  

1.  Kies in de Configuration Manager-console **softwarebibliotheek** > **Toepassingsbeheer** > **toepassingen**, en kies vervolgens de toepassing die een andere toepassing vervangt.  

3.  Op de **Start** tabblad, in de **eigenschappen** groep, kiest u **eigenschappen** naam van de toepassing openen **eigenschappen** in het dialoogvenster.  

4.  Op de **vervanging** tabblad van de *< toepassingsnaam\>*  **eigenschappen** dialoogvenster Kies **toevoegen**.  

5.  Klik in het dialoogvenster **Geef vervangingsrelatie op** op **Bladeren**.  

6.  In de **toepassing kiezen** dialoogvenster Kies de toepassing die u wilt vervangen, en kies vervolgens **OK**.  

7.  In de **Geef Vervangingsrelatie** dialoogvenster, typt u het implementatietype dat wordt vervangen door de implementatie van de vervangen toepassing.  

    > [!NOTE]  
    >  Standaard verwijderen het nieuwe implementatietype niet van het implementatietype van de vervangen toepassing. Dit scenario wordt doorgaans gebruikt om een upgrade voor een bestaande toepassing te implementeren. Selecteer **Verwijderen** als u het bestaande implementatietype wilt verwijderen voordat het nieuwe implementatietype wordt geïnstalleerd. Als u een toepassing wilt upgraden, kunt u dit het beste eerst testen in een testomgeving.  

8.  Kies **OK** sluiten de **Geef Vervangingsrelatie** in het dialoogvenster.  

9. Kies **OK** sluiten de *< toepassingsnaam\>*  **eigenschappen** in het dialoogvenster.  

### <a name="to-display-applications-that-supersede-the-current-application"></a>Toepassingen weergeven die de huidige toepassing vervangen  

1.  Kies in de Configuration Manager-console **softwarebibliotheek**.  

2.  In de **softwarebibliotheek** werkruimte Vouw **Toepassingsbeheer**, kies **toepassingen**, en kies vervolgens de toepassing die u wenst.  

3.  Op de **Start** tabblad, in de **eigenschappen** groep, kiest u **eigenschappen** openen de *< toepassingsnaam\>*  **eigenschappen** in het dialoogvenster.  

4.  Op de **verwijzingen** tabblad van de *< toepassingsnaam\>*  **eigenschappen** dialoogvenster Kies **toepassingen die deze toepassing vervangen** van de **relatietype** vervolgkeuzelijst.  

5.  Bekijk de lijst met toepassingen die de geselecteerde toepassing vervangen en kies vervolgens **OK** sluiten de *< toepassingsnaam\>*  **eigenschappen** in het dialoogvenster.  
