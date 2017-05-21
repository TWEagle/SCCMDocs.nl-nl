---
title: IOS-apps configureren met app-configuratiebeleid | Microsoft-documenten
description: Oplossen configuratieproblemen op apparaten met iOS 8 of hoger configuratiebeleid app implementeren voor gebruikers voordat ze apps worden uitgevoerd.
ms.custom: na
ms.date: 03/05/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-hybrid
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: f0a78038-ea22-4826-9c07-1771b7dd2e8d
caps.latest.revision: 18
caps.handback.revision: 0
author: mtillman
ms.author: mtillman
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 23b1d24e908d04b64c3bbfa518793a44e696d468
ms.openlocfilehash: 50aea2afaf34974ca92ac58b6569bff56403a9ab
ms.contentlocale: nl-nl
ms.lasthandoff: 05/17/2017

---
# <a name="apply-settings-to-ios-apps-with-app-configuration-policies-in-system-center-configuration-manager"></a>Instellingen van toepassing op iOS-apps met app-configuratiebeleid in System Center Configuration Manager

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*


U kunt app configuratiebeleid in System Center Configuration Manager (Configuration Manager) distribueren instellingen die vereist zijn kunnen wanneer een gebruiker een app wordt uitgevoerd. Een app vereisen bijvoorbeeld een gebruiker kan deze gegevens opgeven:
- Een aangepast poortnummer
- Taalinstellingen
- Beveiligingsinstellingen
- Huisstijl-instellingen, zoals een bedrijfslogo

Als de gebruiker de instellingen voert foutief, de belasting te corrigeren valt uw helpdesk en app-implementatie traag is.
Om te voorkomen dat deze problemen, kunt u beleidsregels voor app-configuratie vereist om instellingen te implementeren voor gebruikers voordat de app uitvoert. De instellingen worden automatisch gekoppeld aan een gebruiker. De gebruiker hoeft niet geen actie te ondernemen.
Voor het gebruik van een app-configuratiebeleid in Configuration Manager, in plaats van het configuratiebeleid implementeren rechtstreeks aan gebruikers en apparaten, koppelt u een beleid met een implementatietype te detecteren wanneer u de app implementeert. De instellingen worden toegepast wanneer de app controleert ze (normaal gesproken de eerste keer de app wordt uitgevoerd).

App-configuratiebeleid zijn momenteel beschikbaar alleen op apparaten met iOS 8 en hoger, en voor deze toepassingstypen:

- **App-pakket voor iOS (*IPA-bestand)**
- **App-pakket voor iOS uit de App Store**

Zie voor meer informatie over app-installatietypen de [inleiding op Toepassingsbeheer](/sccm/apps/understand/introduction-to-application-management).

## <a name="create-an-app-configuration-policy"></a>Een app-configuratiebeleid maken

1. Kies in de Configuration Manager-console **softwarebibliotheek** > **Toepassingsbeheer** > **App configuratiebeleid**.
2. Op de **Start** tabblad, in de **App configuratiebeleid** groep, kiest u **nieuwe toepassing configuratiebeleid maken**.
3. In de App configuratie beleid Wizard, op de **algemeen** pagina, stelt u deze beleidsinformatie:
  - **Naam**. Geef een unieke naam voor het beleid.
  - **Beschrijving**. (Optioneel) U kunt een beschrijving toevoegen om te identificeren van het beleid te vereenvoudigen.
  - **Toegewezen categorieën voor het verbeteren van zoeken en filteren**. (Optioneel) Als u categorieën toewijzen aan het beleid wilt maken, kies **categorieën**. Categorieën maken het gemakkelijker om te sorteren en objecten vinden in de Configuration Manager-console.
4. Op de **iOS-beleid** pagina, kiest u de configuratiegegevens voor beleid instellen:
  - **Geef de naam- en waardeparen**. U kunt deze optie gebruiken voor de eigenschap lijst met bestanden die geen geneste gebruiken.

      *Een naam en waarde-paar opgeven*
        1. Kies een nieuwe set toevoegen, **New**.
        2. In de **naam/waarde-paar toevoegen** dialoogvenster, geeft u het volgende:
            - **Type**. Selecteer het type van de waarde die u wilt opgeven in de lijst.
            - **Naam**. Voer de naam van de lijst met sleutel waarvan u wilt een waarde op te geven.
            - **Waarde**. Voer de waarde die wordt toegepast op de sleutel die u hebt ingevoerd.

  - **Blader naar een bestand eigenschappenlijst**. Gebruik deze optie als u al een XML-configuratiebestand app, of voor complexere bestanden met nesten.

    *Om te bladeren naar een bestand eigenschappenlijst*

      1.  In de **App configuratiebeleid** veld, voert u de informatie over de lijst in de juiste XML-indeling.

      Zie voor meer informatie over de lijsten met zoekeigenschappen van XML, [Understanding XML-eigenschap geeft een lijst van](https://developer.apple.com/library/ios/documentation/Cocoa/Conceptual/PropertyLists/UnderstandXMLPlist/UnderstandXMLPlist.html) in de iOS Developer-bibliotheek.

De indeling van de eigenschap XML-lijst is afhankelijk van de app die u configureert. Neem contact op met de leverancier van de app voor meer informatie over de notatie moet worden gebruikt.
Intune ondersteunt de volgende gegevenstypen in een lijst met eigenschappen:
            
            ```
            <integer>
            <real>
            <string>
            <array>
            <dict>
            <true /> or <false />
            ```
Zie voor meer informatie over de gegevenstypen [over lijsten met eigenschappen](https://developer.apple.com/library/content/documentation/Cocoa/Conceptual/PropertyLists/AboutPropertyLists/AboutPropertyLists.html) in de iOS Developer-bibliotheek.
Intune biedt ook ondersteuning voor de volgende typen token in de lijst met eigenschappen:
            
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

De {{en}} tekens worden gebruikt door alleen token typen en mag niet worden gebruikt voor andere doeleinden.
            
5. Als u wilt importeren in een XML-bestand dat u eerder hebt gemaakt, kies **kiest u bestand**.
6. Kies **volgende**. Als er fouten in de XML-code, hebt u deze corrigeren voordat u doorgaat.
7. De stappen die worden weergegeven in de wizard voltooien.

Het nieuwe beleid van de app-configuratie wordt weergegeven in de **softwarebibliotheek** werkruimte in de **App configuratiebeleid** knooppunt.

## <a name="associate-an-app-configuration-policy-with-a-configuration-manager-application"></a>Een app-configuratiebeleid aan een Configuration Manager-toepassing koppelen

Implementeer de toepassing als u wilt een app-configuratiebeleid koppelen aan de implementatie van een iOS-app, zoals u dat gewend bent met de procedure in de [toepassingen implementeren](/sccm/apps/deploy-use/deploy-applications) onderwerp.

In de Wizard Software implementeren op de **App configuratiebeleid** pagina, kiest u **New**. In de **configuratiebeleid App selecteren** dialoogvenster Selecteer een toepassingsimplementatietype en het configuratiebeleid app die u wilt koppelen aan.
Wanneer het implementatietype wordt geïnstalleerd, wordt automatisch de beleidsinstellingen van de app-configuratie toegepast.

## <a name="example-format-for-the-mobile-app-configuration-xml-file"></a>Voorbeeld van de indeling voor de mobiele app XML-configuratiebestand

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

