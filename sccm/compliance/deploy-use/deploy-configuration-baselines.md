---
title: Implementeer configuratiebasislijnen | Microsoft-documenten
description: "Implementeer configuratiebasislijnen voor het definiëren van implementaties van configuratiebasislijnen en voor het toevoegen of verwijderen van configuratiebasislijnen uit implementaties."
ms.custom: na
ms.date: 10/06/2016
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 9be8aaf3-075e-4acd-abd2-7459254e16e2
caps.latest.revision: 7
caps.handback.revision: 0
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: f9e939d871e95a3248d8e5d96cb73063a81fd5cf
ms.openlocfilehash: 9c9e6b7780c7c10c20a60dbbbf506e916031eb88
ms.contentlocale: nl-nl
ms.lasthandoff: 05/17/2017


---
# <a name="how-to-deploy-configuration-baselines-in-system-center-configuration-manager"></a>Het implementeren van configuratiebasislijnen in System Center Configuration Manager

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*

Configuratiebasislijnen in System Center Configuration Manager moeten worden geïmplementeerd op een of meer verzamelingen van gebruikers of apparaten voordat clientapparaten in deze verzamelingen hun compatibiliteit met de configuratiebasislijn kunnen beoordelen.  

Gebruik de **Configuratiebasislijnen implementeren** in het dialoogvenster voor het definiëren van implementaties van configuratiebasislijnen, waaronder het toevoegen aan of verwijderen van configuratiebasislijnen uit implementaties naast het opgeven van het evaluatieschema.  

## <a name="deploy-a-configuration-baseline"></a>Een configuratiebasislijn implementeren  

1.  Klik in de Configuration Manager-console op **activa en naleving** > **compatibiliteitsinstellingen** > **Configuratiebasislijnen**.  

3.  Selecteer in de lijst **Configuratiebasislijnen** de configuratiebasislijn die u wilt implementeren en klik vervolgens op het tabblad **Start** in de groep **Implementatie** op **Implementeren**.  

4.  Selecteer in het dialoogvenster **Configuratiebasislijnen implementeren** de configuratiebasislijnen die u wilt implementeren in de lijst **Beschikbare configuratiebasislijnen** . Klik op **Toevoegen** om ze toe te voegen aan de lijst **Geselecteerde configuratiebasislijnen** .  

    > [!IMPORTANT]  
    >  Als u een configuratie-item wijzigt dat is toegevoegd aan een geïmplementeerde configuratiebasislijn, wordt het gewijzigde configuratie-item pas op de volgende geplande evaluatietijd op compatibiliteit geëvalueerd.  

5.  Geef de volgende aanvullende informatie op:  

    -   **Herstellen van niet-compatibele regels, waar ondersteund** – automatisch worden eventuele regels die niet compatibel voor Windows Management Instrumentation (WMI), het register, scripts en alle instellingen voor mobiele apparaten die zijn ingeschreven door Configuration Manager zijn hersteld.  

    -   **Herstel toestaan buiten het onderhoudsvenster** : Als er een onderhoudsvenster is geconfigureerd voor de verzameling waarnaar u de configuratiebasislijn implementeert, schakelt u deze optie in om de waarde buiten het onderhoudsvenster te laten herstellen met de instellingen voor naleving. Zie voor meer informatie over onderhoudsvensters [het gebruik van onderhoudsvensters](/sccm/core/clients/manage/collections/use-maintenance-windows).  

6.  **Een waarschuwing gegenereerd** – configureert u een waarschuwing die wordt gegenereerd als de naleving van de configuratiebasislijn minder dan een opgegeven percentage op een opgegeven datum en tijd is. U kunt tevens opgeven of u een melding naar System Center Operations Manager wilt verzenden.  

7.  **Verzameling** : klik op **Bladeren** om de verzameling te selecteren waarvoor u de configuratiebasislijn wilt implementeren.  

8.  **Geef het evaluatieschema voor compatibiliteit voor deze configuratiebasislijn** Hiermee geeft u de planning op waarmee de geïmplementeerde configuratiebasislijn wordt geëvalueerd op clientcomputers. U kunt een eenvoudige of een aangepaste planning opgeven.  

    > [!NOTE]  
    >  Als de configuratiebasislijn wordt geïmplementeerd op een computer, wordt deze voor naleving binnen twee uur na het begintijdstip dat u plant geëvalueerd. Als de configuratiebasislijn wordt geïmplementeerd voor een gebruiker, wordt de naleving geëvalueerd wanneer de gebruiker zich aanmeldt.  

9. Klik op **OK** om het dialoogvenster **Configuratiebasislijnen implementeren** te sluiten en de implementatie te maken. Zie voor meer informatie over het controleren van de implementatie [instellingen voor naleving controleren](/sccm/compliance/deploy-use/monitor-compliance-settings).  

