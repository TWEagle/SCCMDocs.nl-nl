---
title: Android configureren voor zakelijke apps met configuratiebeleid voor apps
titleSuffix: Configuration Manager
description: Voorkomen configuratieproblemen op apparaten met Android for Work door het app-configuratiebeleid implementeren voor gebruikers voordat ze apps uitvoeren.
ms.custom: na
ms.date: 09/12/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-hybrid
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 9126d188-7780-45a4-b21d-7fcf4fad7da2
caps.latest.revision: 0
caps.handback.revision: 0
author: NathBarn
ms.author: NathBarn
manager: angrobe
ms.openlocfilehash: 0b1d4993e6ddb2301121a1e32b1672425e919dea
ms.sourcegitcommit: fb84bcb31d825f454785e3d9d8be669e00fe2b27
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/16/2018
---
# <a name="apply-settings-to-android-for-work-apps-with-app-configuration-policies-in-system-center-configuration-manager"></a>Instellingen toepassen op Android voor zakelijke apps met configuratiebeleid voor apps in System Center Configuration Manager

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*

U kunt app-configuratiebeleid in System Center Configuration Manager voor het distribueren van de instellingen die mogelijk vereist zijn wanneer een gebruiker een app uitvoert. Een app kan bijvoorbeeld vereisen dat een gebruiker deze gegevens kunt opgeven:
- Een aangepast poortnummer
- Taalinstellingen
- Beveiligingsinstellingen
- Huisstijlinstellingen, zoals een bedrijfslogo

Als de gebruiker de instellingen voert onjuist de last om op te lossen ze valt van uw helpdesk en app-implementatie traag is. Als u deze problemen te voorkomen, kunt u app-configuratiebeleid vereist om instellingen te implementeren voor gebruikers voordat ze de app worden uitgevoerd. De instellingen worden automatisch gekoppeld aan een gebruiker. De gebruiker hoeft niet te doen.
In plaats van het implementeren van beleidsregels voor de configuratie rechtstreeks aan gebruikers en apparaten, koppelt u een beleid aan een implementatietype wanneer u de app implementeert. De beleidsinstellingen worden toegepast als de app zoekt, meestal de eerste keer dat de app wordt uitgevoerd.

Configuratiebeleid voor android-app zijn alleen beschikbaar voor apparaten met Android for Work. App-configuratiebeleid toepassen op goedgekeurde apps uit de Play voor werk store. Zie voor meer informatie over Android-volume-aankoopprogramma gekochte apps [apps implementeren op Android voor werk apparaten](https://docs.microsoft.com/intune/deploy-use/android-for-work-apps).

Zie voor meer informatie over app-installatietypen de [inleiding op Toepassingsbeheer](/sccm/apps/understand/introduction-to-application-management).

## <a name="create-an-app-configuration-policy"></a>Een app-configuratiebeleid maken

1. Kies in de Configuration Manager-console **softwarebibliotheek** > **Toepassingsbeheer** > **Configuratiebeleidsregels**.
2. Op de **Start** tabblad, in de **Configuratiebeleidsregels** groep, kiest u **App-configuratiebeleid maken**.
3. In de App Configuration Wizard beleid maken, op de **algemene** pagina, stelt u deze beleidsinformatie:
  - **Naam**. Geef een unieke naam voor het beleid.
  - **Beschrijving**. (Optioneel) U kunt een beschrijving toevoegen voor het identificeren van het beleid te vereenvoudigen.
  -  **Selecteer een type configuration beleid**. Geef het platform waarop de app-configuratiebeleid: **Configuratiebeleid voor Android voor zakelijke apps**.
  -  **Toegewezen categorieën voor het verbeteren van zoeken en filteren**. (Optioneel) Als u categorieën toewijzen aan het beleid wilt maken, kies **categorieën**. Categorieën gemakkelijker om te sorteren en objecten vinden in de Configuration Manager-console.
4. Op de **Android for Work-beleid** pagina, kiest u het instellen van de configuratiegegevens voor beleid:
  - **Geef de naam / waarde-paren**. U kunt deze optie gebruiken voor eigenschappenlijstbestanden die gebruik niet nesten. Geef een naam en waarde-paar op:
        1. Als u wilt een nieuwe JSON-set toevoegen, kiest u **nieuw**.
        2. In de **naam/waarde-paar toevoegen** dialoogvenster geeft u de volgende details:
            - **Type**. Selecteer het type van de waarde die u wilt opgeven in de lijst.
            - **Naam**. Voer de naam van de lijst met sleutel waarvan u wilt een waarde op te geven.
            - **Waarde**. Voer de waarde die wordt toegepast op de sleutel die u hebt ingevoerd.

  - **Blader naar een lijst met JSON-bestand van de eigenschap**. Gebruik deze optie als u al een app JSON-configuratiebestand hebt, of voor complexere bestanden met nesten. In de **App-configuratiebeleid** en voer de eigenschappenlijstgegevens voor het in de juiste JSON-indeling.
5. Als u wilt importeren in een JSON-bestand dat u eerder hebt gemaakt, kies **bestand selecteren**.
6. Kies **volgende**. Als er fouten in de JSON-code zijn, deze corrigeren voordat u doorgaat.
7. Voltooi de stappen in de wizard.

De nieuwe app-configuratiebeleid wordt weergegeven in de **softwarebibliotheek** werkruimte, in de **Configuratiebeleidsregels** knooppunt.

## <a name="associate-an-app-configuration-policy-with-a-configuration-manager-application"></a>Een app-configuratiebeleid aan een Configuration Manager-toepassing koppelen

Als u wilt een app-configuratiebeleid koppelen aan de implementatie van een Android voor werk app, implementeert u de toepassing normaal met behulp van de procedure in de [toepassingen implementeren](/sccm/apps/deploy-use/deploy-applications) onderwerp.

In de Wizard Software implementeren op de **Configuratiebeleidsregels** pagina **nieuw**. In de **App-configuratiebeleid selecteren** dialoogvenster Kies een toepassingsimplementatietype en de app-configuratiebeleid die u wilt koppelen aan.
Wanneer het implementatietype wordt geïnstalleerd, wordt de app-instellingen voor configuratiebeleid voor automatisch toegepast.
