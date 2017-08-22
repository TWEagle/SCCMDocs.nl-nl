---
title: IOS-apps configureren met configuratiebeleid voor apps | Microsoft Docs
description: Voorkomen configuratieproblemen op apparaten met iOS 8 of hoger door het app-configuratiebeleid implementeren voor gebruikers voordat ze apps uitvoeren.
ms.custom: na
ms.date: 03/05/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: configmgr-hybrid
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: f0a78038-ea22-4826-9c07-1771b7dd2e8d
caps.latest.revision: "18"
caps.handback.revision: "0"
author: mtillman
ms.author: mtillman
manager: angrobe
ms.openlocfilehash: 50aea2afaf34974ca92ac58b6569bff56403a9ab
ms.sourcegitcommit: 51fc48fb023f1e8d995c6c4eacfda7dbec4d0b2f
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 08/07/2017
---
# <a name="apply-settings-to-ios-apps-with-app-configuration-policies-in-system-center-configuration-manager"></a>Instellingen toepassen op iOS-apps met configuratiebeleid voor apps in System Center Configuration Manager

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*


U kunt app-configuratiebeleid in System Center Configuration Manager (Configuration Manager) voor het distribueren van de instellingen die mogelijk vereist zijn wanneer een gebruiker een app uitvoert. Een app kan bijvoorbeeld vereisen dat een gebruiker deze gegevens kunt opgeven:
- Een aangepast poortnummer
- Taalinstellingen
- Beveiligingsinstellingen
- Huisstijlinstellingen, zoals een bedrijfslogo

Als de gebruiker de instellingen voert onjuist de last om op te lossen ze valt van uw helpdesk en app-implementatie traag is.
Als u deze problemen te voorkomen, kunt u app-configuratiebeleid vereist om instellingen te implementeren voor gebruikers voordat ze de app worden uitgevoerd. De instellingen worden automatisch gekoppeld aan een gebruiker. De gebruiker hoeft niet te doen.
Voor het gebruik van een app-configuratiebeleid in Configuration Manager, in plaats van het configuratiebeleid implementeren rechtstreeks aan gebruikers en apparaten, koppelt u een beleid aan een implementatietype wanneer u de app implementeert. De beleidsinstellingen worden toegepast als de app controleert ze (normaal gesproken de eerste keer de app wordt uitgevoerd).

App-configuratiebeleidsregels zijn momenteel leverbaar alleen op apparaten met iOS 8 en hoger, en voor deze toepassingstypen:

- **App-pakket voor iOS (*IPA-bestand)**
- **App-pakket voor iOS uit de App Store**

Zie voor meer informatie over app-installatietypen de [inleiding op Toepassingsbeheer](/sccm/apps/understand/introduction-to-application-management).

## <a name="create-an-app-configuration-policy"></a>Een app-configuratiebeleid maken

1. Kies in de Configuration Manager-console **softwarebibliotheek** > **Toepassingsbeheer** > **Configuratiebeleidsregels**.
2. Op de **Start** tabblad, in de **Configuratiebeleidsregels** groep, kiest u **nieuwe Toepassingsconfiguratiebeleid maken**.
3. In de App Configuration Wizard beleid maken, op de **algemene** pagina, stelt u deze beleidsinformatie:
  - **Naam**. Geef een unieke naam voor het beleid.
  - **Beschrijving**. (Optioneel) U kunt een beschrijving toevoegen voor het identificeren van het beleid te vereenvoudigen.
  - **Toegewezen categorieën voor het verbeteren van zoeken en filteren**. (Optioneel) Als u categorieën toewijzen aan het beleid wilt maken, kies **categorieën**. Categorieën gemakkelijker om te sorteren en objecten vinden in de Configuration Manager-console.
4. Op de **iOS-beleid** pagina, kiest u het instellen van de configuratiegegevens voor beleid:
  - **Geef de naam / waarde-paren**. U kunt deze optie gebruiken voor eigenschappenlijstbestanden die gebruik niet nesten.

      *Een combinatie van naam en waarde opgeven*
        1. Als u wilt een nieuwe set toevoegen, kiest u **nieuw**.
        2. In de **naam/waarde-paar toevoegen** dialoogvenster geeft u het volgende:
            - **Type**. Selecteer het type van de waarde die u wilt opgeven in de lijst.
            - **Naam**. Voer de naam van de lijst met sleutel waarvan u wilt een waarde op te geven.
            - **Waarde**. Voer de waarde die wordt toegepast op de sleutel die u hebt ingevoerd.

  - **Blader naar een eigenschappenlijstbestand**. Gebruik deze optie als u al een XML-bestand van de app-configuratie of voor complexere bestanden met nesten.

    *Om te bladeren naar een eigenschappenlijstbestand*

      1.  In de **App-configuratiebeleid** en voer de eigenschappenlijstgegevens voor het in de juiste XML-indeling.

      Zie voor meer informatie over XML-eigenschappenlijsten, [Understanding XML Property Lists](https://developer.apple.com/library/ios/documentation/Cocoa/Conceptual/PropertyLists/UnderstandXMLPlist/UnderstandXMLPlist.html) in de iOS Developer-bibliotheek.

De indeling van de XML-eigenschappenlijst is afhankelijk van de app die u configureert. Neem contact op met de leverancier van de app voor meer informatie over de indeling moet worden gebruikt.
Intune ondersteunt de volgende gegevenstypen in een eigenschappenlijst:
            
            ```
            <integer>
            <real>
            <string>
            <array>
            <dict>
            <true /> or <false />
            ```
Zie voor meer informatie over gegevenstypen [over eigenschappenlijsten](https://developer.apple.com/library/content/documentation/Cocoa/Conceptual/PropertyLists/AboutPropertyLists/AboutPropertyLists.html) in de iOS Developer-bibliotheek.
Intune ondersteunt ook de volgende typen token in de lijst met eigenschappen:
            
            ```
            {{userprincipalname}} - (Example: John@contoso.com)
            {{mail}} - (Example: John@contoso.com)
            {{partialupn}} - (Example: John)
            {{accountid}} - (Example: fc0dc142-71d8-4b12-bbea-bae2a8514c81)
            {{deviceid}} - (Example: b9841cd9-9843-405f-be28-b2265c59ef97)
            {{userid}} - (Example: 3ec2c00f-b125-4519-acf0-302ac3761822)
            {{username}} - (Example: John Doe)
            {{serialnumber}} - (Example: F4KN99ZUG5V2) for iOS devices
            {{serialnumberlast4digits}} - (Example: G5V2) for iOS devices
            ```

De {{en}} tekens worden gebruikt door alleen tokentypen en mogen niet worden gebruikt voor andere doeleinden.
            
5. Als u wilt importeren in een XML-bestand dat u eerder hebt gemaakt, kies **bestand selecteren**.
6. Kies **volgende**. Als er fouten in de XML-code zijn, hebt u deze corrigeren voordat u doorgaat.
7. Voltooi de stappen in de wizard.

De nieuwe app-configuratiebeleid wordt weergegeven in de **softwarebibliotheek** werkruimte, in de **Configuratiebeleidsregels** knooppunt.

## <a name="associate-an-app-configuration-policy-with-a-configuration-manager-application"></a>Een app-configuratiebeleid aan een Configuration Manager-toepassing koppelen

Als u wilt een app-configuratiebeleid koppelen aan de implementatie van een iOS-app, implementeert u de toepassing normaal met behulp van de procedure in de [toepassingen implementeren](/sccm/apps/deploy-use/deploy-applications) onderwerp.

In de Wizard Software implementeren op de **Configuratiebeleidsregels** pagina **nieuw**. In de **App-configuratiebeleid selecteren** dialoogvenster Kies een toepassingsimplementatietype en de app-configuratiebeleid die u wilt koppelen aan.
Wanneer het implementatietype wordt geïnstalleerd, wordt de app-instellingen voor configuratiebeleid voor automatisch toegepast.

## <a name="example-format-for-the-mobile-app-configuration-xml-file"></a>Voorbeeld van een indeling voor XML-configuratiebestand van de mobiele app

Wanneer u een configuratiebestand voor de mobiele app maakt, kunt u deze indeling gebruiken om op te geven van een of meer van de volgende waarden:

```
<dict>
  <key>userprincipalname</key>
  <string>{{userprincipalname}}</string>
  <key>mail</key>
  <string>{{mail}}</string>
  <key>partialupn</key>
  <string>{{partialupn}}</string>
  <key>accountid</key>
  <string>{{accountid}}</string>
  <key>deviceid</key>
  <string>{{deviceid}}</string>
  <key>userid</key>
  <string>{{userid}}</string>
  <key>username</key>
  <string>{{username}}</string>
  <key>serialnumber</key>
  <string>{{serialnumber}}</string>
  <key>serialnumberlast4digits</key>
  <string>{{serialnumberlast4digits}}</string>
  <key>udidlast4digits</key>
  <string>{{udidlast4digits}}</string>
</dict>
```
