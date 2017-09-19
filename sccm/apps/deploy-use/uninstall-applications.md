---
title: Toepassingen verwijderen | Microsoft Docs
description: Verwijderen van een toepassing met behulp van System Center Configuration Manager
ms.custom: na
ms.date: 10/06/2016
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: configmgr-app
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 0ea3edaa-27c6-4391-9896-cd97d9c5d06d
caps.latest.revision: "4"
caps.handback.revision: "0"
author: mattbriggs
ms.author: mabrigg
manager: angrobe
ms.openlocfilehash: 1e9c5506b94eecc1c95af5f31ad4c2d923c2b74f
ms.sourcegitcommit: b438515490e04fb09c82a8af642d38e9a0605178
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 09/15/2017
---
# <a name="uninstall-applications-with-system-center-configuration-manager"></a>Toepassingen met System Center Configuration Manager verwijderen

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*


Hiermee voert u de volgende acties voor het verwijderen van een toepassing die u eerder hebt geïmplementeerd.

-   Geef de opdrachtregel voor het verwijderen van de inhoud van het implementatietype op de **inhoud** pagina van de Wizard implementatietype maken.  

-   Implementeer de toepassing met behulp van een implementatieactie **Verwijderen**.  

> [!IMPORTANT]  
> Sommige toepassingtypen bieden geen ondersteuning voor verwijdering.  

 Deze lijst geeft meer informatie over de werking van toepassing verwijderen:  

-   Wanneer u een System Center Configuration Manager (Configuration Manager)-toepassing verwijdert, worden eventuele afhankelijke toepassingen niet automatisch verwijderd.  

-   Als u een toepassing die gebruikmaakt van een actie van implementeren **verwijderen** aan een gebruiker, en de toepassing werd geïnstalleerd voor alle gebruikers van de computer, mislukt de verwijdering mogelijk als het gebruikersaccount niet gemachtigd is om de toepassing te verwijderen.  

-   Als u een gebruiker of apparaat uit een verzameling met een toepassing is geïmplementeerd verwijdert, wordt de toepassing niet automatisch verwijderd van het apparaat.  

-   Bij een implementatie met het implementatiedoel **Verwijderen** , worden de regels voor vereisten niet gecontroleerd. Als de toepassing wordt geïnstalleerd op de computer waarop de implementatie wordt uitgevoerd, wordt deze verwijderd.  

> [!IMPORTANT]  
> U moet eventuele bestaande of gesimuleerde implementaties van een toepassing in een verzameling verwijderen voordat u de toepassing kunt implementeren met de implementatieactie **Verwijderen**.  

 Zie voor meer informatie over het maken van een implementatietype [toepassingen maken](../../apps/deploy-use/create-applications.md).  

 Zie voor meer informatie over het implementeren van een toepassing [toepassingen implementeren](../../apps/deploy-use/deploy-applications.md).  

## <a name="uninstall-an-application"></a>Een toepassing verwijderen  

1.  Gebruik een van de volgende methoden om het implementatietype van de toepassing te configureren met de opdrachtregel voor verwijdering:  

    -   Op de **algemene** pagina van de Wizard implementatie maken de optie **automatisch informatie identificeren over dit implementatietype vanuit installatiebestanden**. Als de informatie beschikbaar is in de installatiebestanden, wordt de opdrachtregel voor verwijdering automatisch toegevoegd aan de eigenschappen van het implementatietype.  

    -   Op de **inhoud** pagina van de Wizard implementatietype maken in de **programma voor verwijderen** veld, geeft u de opdrachtregel om de toepassing te verwijderen.  

        > [!NOTE]  
        >  De **inhoud** pagina wordt alleen weergegeven als u de optie **Geef handmatig de implementatietype-informatie** op de **algemene** pagina van de Wizard implementatietype maken.  

    -   Op de **programma's** tabblad van de * * < *naam implementatietype*> Eigenschappen ** dialoogvenster geeft u de opdrachtregel voor het verwijderen van de toepassing in de **programma voor verwijderen** veld.  

2.  Implementeer de toepassing en selecteer vervolgens de implementatie-actie **verwijderen** op de **implementatie-instellingen** pagina van de Wizard Software implementeren.  

    > [!NOTE]  
    >  Wanneer u de implementatieactie **Verwijderen**selecteert, wordt het implementatiedoel automatisch geconfigureerd als **Vereist**.  
