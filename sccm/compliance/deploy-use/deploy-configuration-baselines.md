---
title: Configuratiebasislijnen implementeren
titleSuffix: Configuration Manager
description: "Implementeer configuratiebasislijnen voor het definiëren van implementaties van configuratiebasislijnen en voor het toevoegen of verwijderen van configuratiebasislijnen uit implementaties."
ms.custom: na
ms.date: 10/06/2016
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 9be8aaf3-075e-4acd-abd2-7459254e16e2
caps.latest.revision: "7"
caps.handback.revision: "0"
author: andredm7
ms.author: andredm
manager: angrobe
ms.openlocfilehash: e61314c5c10f4a4c9eda1f0a292cb5a9c72b32bb
ms.sourcegitcommit: c236214b2fcc13dae7bad96d7fb33f692868191d
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/12/2017
---
# <a name="how-to-deploy-configuration-baselines-in-system-center-configuration-manager"></a>Het implementeren van configuratiebasislijnen in System Center Configuration Manager

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*

Configuratiebasislijnen in System Center Configuration Manager moeten worden geïmplementeerd op een of meer verzamelingen van gebruikers of apparaten voordat clientapparaten in deze verzamelingen hun compatibiliteit met de configuratiebasislijn kunnen beoordelen.  

Gebruik de **Configuratiebasislijnen implementeren** in het dialoogvenster voor het definiëren van implementaties van configuratiebasislijnen, waaronder het toevoegen aan of verwijderen van configuratiebasislijnen uit implementaties naast het opgeven van het evaluatieschema.  

## <a name="deploy-a-configuration-baseline"></a>Een configuratiebasislijn implementeren  

1.  Klik in de Configuration Manager-console op **activa en naleving** > **instellingen voor naleving** > **Configuratiebasislijnen**.  

3.  Selecteer in de lijst **Configuratiebasislijnen** de configuratiebasislijn die u wilt implementeren en klik vervolgens op het tabblad **Start** in de groep **Implementatie** op **Implementeren**.  

4.  Selecteer in het dialoogvenster **Configuratiebasislijnen implementeren** de configuratiebasislijnen die u wilt implementeren in de lijst **Beschikbare configuratiebasislijnen** . Klik op **Toevoegen** om ze toe te voegen aan de lijst **Geselecteerde configuratiebasislijnen** .  

    > [!IMPORTANT]  
    >  Als u een configuratie-item wijzigt dat is toegevoegd aan een geïmplementeerde configuratiebasislijn, wordt het gewijzigde configuratie-item pas op de volgende geplande evaluatietijd op compatibiliteit geëvalueerd.  

5.  Geef de volgende aanvullende informatie op:  

    -   **Herstellen, waar ondersteund** – automatisch herstelt de regels die niet compatibel voor Windows Management Instrumentation (WMI), het register, scripts en alle instellingen voor mobiele apparaten die zijn ingeschreven door Configuration Manager zijn.  

    -   **Herstel toestaan buiten het onderhoudsvenster** : Als er een onderhoudsvenster is geconfigureerd voor de verzameling waarnaar u de configuratiebasislijn implementeert, schakelt u deze optie in om de waarde buiten het onderhoudsvenster te laten herstellen met de instellingen voor naleving. Zie voor meer informatie over onderhoudsvensters [het gebruik van onderhoudsvensters](/sccm/core/clients/manage/collections/use-maintenance-windows).  

6.  **Waarschuwing genereren** – Hiermee configureert u een waarschuwing die wordt gegenereerd als de naleving van de configuratiebasislijn kleiner dan een opgegeven percentage voor een opgegeven datum en tijd is. U kunt tevens opgeven of u een melding naar System Center Operations Manager wilt verzenden.  

7.  **Verzameling** : klik op **Bladeren** om de verzameling te selecteren waarvoor u de configuratiebasislijn wilt implementeren.  

8.  **Geef het evaluatieschema voor compatibiliteit op voor deze configuratiebasislijn** Hiermee geeft u de planning op waarmee de geïmplementeerde configuratiebasislijn wordt geëvalueerd op clientcomputers. U kunt een eenvoudige of een aangepaste planning opgeven.  

    > [!NOTE]  
    >  Als de configuratiebasislijn wordt geïmplementeerd op een computer, wordt deze voor naleving binnen twee uur na het begintijdstip dat u plant geëvalueerd. Als de configuratiebasislijn wordt geïmplementeerd voor een gebruiker, wordt de naleving geëvalueerd wanneer de gebruiker zich aanmeldt.  

9. Klik op **OK** om het dialoogvenster **Configuratiebasislijnen implementeren** te sluiten en de implementatie te maken. Zie voor meer informatie over het bewaken van de implementatie [instellingen voor naleving bewaken](/sccm/compliance/deploy-use/monitor-compliance-settings).  
