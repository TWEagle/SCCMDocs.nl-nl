---
title: Technische Preview 1708 | Microsoft Docs
description: Meer informatie over functies die beschikbaar zijn in de Technical Preview-versie 1708 voor System Center Configuration Manager.
ms.custom: na
ms.date: 08/25/2017
ms.prod: configuration-manager
ms.technology: configmgr-other
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 3c061ceb-3bdb-4d4f-8c60-344964bd416b
author: Brenduns
ms.author: brenduns
manager: angrobe
ms.openlocfilehash: 022c9b2540f7ed403c38521c8e68f6c416c15c7c
ms.sourcegitcommit: 974fbc4408028c8be28911e5cd646efcf47c7f15
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 08/26/2017
---
# <a name="capabilities-in-technical-preview-1708-for-system-center-configuration-manager"></a>Mogelijkheden van Technical Preview 1708 voor System Center Configuration Manager

*Van toepassing op: System Center Configuration Manager (Technical Preview)*

Dit artikel bevat de functies die beschikbaar in de Technical Preview voor System Center Configuration Manager, versie 1708 zijn. U kunt deze versie om te werken en nieuwe mogelijkheden toevoegen aan uw Configuration Manager technical preview-site installeren. Controleer voordat u deze versie van de technical preview installeert, [Technical Preview voor System Center Configuration Manager](../../core/get-started/technical-preview.md) om vertrouwd te raken met algemene vereisten en beperkingen voor het gebruik van een technical preview hoe bijwerken tussen versies en hoe u feedback over de functies in een technical preview.     


<!--  Known Issues Template   
**Known Issues in this Technical Preview:**
-   **Issue Name**. Details
    Workaround details.
-->
**Bekende problemen in deze Technical Preview:**
-   **Update voor de preview-versie 1708 mislukt wanneer u een siteserver in de passieve modus hebt**. Wanneer u de preview-versie 1706 of 1707 uitvoert, en hebben een [primaire siteserver in de passieve modus](/sccm/core/get-started/capabilities-in-technical-preview-1706#site-server-role-high-availability), moet u de passieve modus siteserver verwijderen voordat u de preview-site met succes naar versie 1708 bijwerken kunt. Nadat u uw site versie 1708 wordt uitgevoerd, kunt u de passieve modus siteserver opnieuw installeren.

  Verwijderen van de siteserver van de passieve modus:
  1. Ga in de console naar **beheer** > **overzicht** > **siteconfiguratie** > **Servers en sitesysteemrollen**, en selecteer vervolgens de passieve modus-siteserver.
  2. In de **sitesysteemrollen** deelvenster, rechts Klik op de **siteserver** rol, en kies vervolgens **rol verwijderen**.
  3. Met de rechtermuisknop op de siteserver van de passieve modus, en kies vervolgens **verwijderen**.
  4. Nadat de siteserver verwijdert, op de primaire siteserver van de actieve service opnieuw starten de **CONFIGURATION_MANAGER_UPDATE**.




**Hier volgen nieuwe functies die u met deze versie kunt uitproberen.**  

<!--  Rough Section Template
##  FEATURE

### Procedure 1
### Try it out!  
 Try to complete the following tasks and then send us **Feedback** from the **Home** tab of the Ribbon to let us know how it worked:
 -  Task 1
 -  Task 2              
-->

## <a name="improvements-for-specifying-script-parameters-when-you-deploy-powershell-scripts-from-configuration-manager"></a>Verbeteringen voor de scriptparameters op te geven wanneer u een PowerShell-scripts uit Configuration Manager implementeren
<!-- 1236459 -->

In configuratie en hoger 1706 Manager, kunt u [maken en uitvoeren van PowerShell-scripts uit de Configuration Manager-console](/sccm/apps/deploy-use/create-deploy-scripts).

In [Technical Preview 1707](/sccm/core/get-started/capabilities-in-technical-preview-1707#add-parameters-when-you-deploy-powershell-scripts-from-configuration-manager), we uitgevouwen op deze mogelijkheid te laten Configuration Manager parameters lezen uit het script.

In deze Technical Preview we hebt uitgebreid de mogelijkheid van de parameters script om te detecteren welke parameters zijn verplicht en die optioneel zijn en deze opgeven.

### <a name="try-it-out"></a>Probeer het nu!

1. Volg de instructies voor [maken en uitvoeren van PowerShell-scripts uit de Configuration Manager-console](/sccm/apps/deploy-use/create-deploy-scripts).
2. Op de nieuwe **scriptparameters** pagina van de **Wizard Script maken**, kiest u een parameter en bewerk vervolgens de waarden.
De wizard geeft weer welke parameters zijn verplicht en die optioneel zijn.
4. Wanneer u klaar bent met het bewerken van parameters, moet u de wizard voltooien.

Wanneer het script wordt uitgevoerd, wordt u ingestelde parameterwaarden gebruikt. Als u een verplichte parameter niet hebt geconfigureerd, wordt de eindgebruiker gevraagd om te voorzien van de parameter wanneer het script wordt uitgevoerd.

## <a name="management-insights"></a>Management insights
<!-- 1353967 -->
Nu krijgt u inzicht in de huidige status van uw omgeving op basis van de analyse van gegevens in de sitedatabase. Insights kunnen u beter inzicht in uw omgeving en Neem maatregelen op basis van het inzicht. Bekijk inzichten in de Configuration Manager-console op beheer **beheer** > **Management Insights** > **alle Insights**. In deze release zijn de volgende inzichten zijn nu beschikbaar:

- **Toepassingen zonder implementaties**: Hier worden de toepassingen in uw omgeving die u geen actieve implementaties hebt. Dit helpt u om te zoeken en verwijderen van ongebruikte toepassingen voor het vereenvoudigen van de lijst met toepassingen die worden weergegeven in de console.
- **Lege verzamelingen**: Hier worden de verzamelingen in uw omgeving die geen leden hebben. U kunt deze verzamelingen om te vereenvoudigen, de lijst met weergegeven bij het implementeren van objecten, bijvoorbeeld verzamelingen verwijderen.


## <a name="restart-computers-from-the-configuration-manager-console"></a>Computers uit de Configuration Manager-console opnieuw opstarten   
<!-- 1356283 -->
Vanaf deze release kunt kunt u de Configuration Manager-console gebruiken om clientapparaten waarvoor opnieuw opstarten te identificeren en gebruik vervolgens een melding clientactie te starten.

Om apparaten te identificeren die opnieuw opgestart worden, gaat u naar **activa en naleving** > **apparaten** en selecteer een verzameling met apparaten die u opnieuw opstarten moet mogelijk. Nadat u een verzameling selecteren, kunt u de status voor elk apparaat weergeven in het detailvenster in een nieuwe kolom die met de naam **opnieuw opstarten**. Elk apparaat heeft een waarde van **Ja**, of **Nee**.

De clientmelding opnieuw opstarten van een apparaat maken:
1.  Zoek het apparaat dat u wilt starten in het knooppunt apparaten van de console.
2.  Met de rechtermuisknop op het apparaat, selecteer **Clientmelding**, en selecteer vervolgens **opnieuw opstarten**. Hiermee opent u een informatievenster van de over het opnieuw opstarten. Klik op **OK** om te bevestigen dat de aanvraag opnieuw.

Wanneer de melding wordt ontvangen door een client een **Software Center** meldingsvenster wordt geopend om te informeren over de gebruiker over de herstart. Standaard wordt het opnieuw opstarten na 90 minuten plaatsvindt. U kunt voor het opstarten wijzigen door het configureren van [clientinstellingen](/sccm/core/clients/deploy/configure-client-settings). Instellingen voor het gedrag voor opnieuw opstarten worden gevonden op de [opnieuw opstarten van Computer](/sccm/core/clients/deploy/about-client-settings#computer-restart) tabblad van de standaardinstellingen.


### <a name="try-it-out"></a>Probeer het nu!
Voer de volgende taken en klikt u vervolgens Stuur ons **Feedback** van de **Start** tabblad van het lint te laten weten hoe het is gegaan:
1.  Een app implementeren of bijwerken naar een apparaat dat is vereist dat het apparaat om opnieuw te starten om installatie te voltooien.
2.  Zoek het apparaat in de **activa en naleving** > **apparaten** knooppunt van de console en controleer het weergegeven **Ja** in de **opnieuw opstarten** kolom. Het kunt maximaal 20 minuten duren voordat de status opnieuw opstarten worden weergegeven in de console.
3.  Bewaken van het apparaat om te bevestigen dat de melding Software Center wordt geopend en dat het apparaat is opnieuw wordt gestart.


## <a name="software-center-customization"></a>Aanpassing van software Center
<!-- 1351224 -->
U kunt enterprise huisstijl elementen toevoegen en geef de zichtbaarheid van tabbladen in Software Center. U kunt de naam van uw Software Center-specifieke bedrijf toevoegen, een kleurthema van Software Center configuratie instellen, een bedrijfslogo, en instellen van de zichtbare tabbladen voor clientapparaten.

### <a name="customize-software-center"></a>Software Center aanpassen

Software Center wijzigen:

1. In de **Configuration Manager** console, kiest u **beheer** > **clientinstellingen**. Klik op de instantie van de gewenste client-instelling.
2. Op de **Start** tabblad, in de **eigenschappen** groep, kiest u **eigenschappen**.
3. In de **standaardinstellingen** dialoogvenster Kies **Software Center**.
4. Selecteer **Ja** naar **Selecteer de nieuwe instellingen om op te geven bedrijfsgegevens** zodat uw aanpassingsinstellingen Software Center.
5. Typ uw **bedrijfsnaam**.
6. Selecteer uw **kleurenschema voor Software Center**.
7. Klik op **Bladeren** om te navigeren naar uw logo voor Software Center. Het logo moet een JPEG of PNG van 400 x 100 pixels en een maximale grootte van 750 KB.
8. Selecteer **Ja** tabbladen om zichtbaar te maken in Software Center voor clientapparaten. Ten minste één tabblad moet zichtbaar zijn:

    -  Op het tabblad toepassingen inschakelen
    -  Tabblad Updates inschakelen
    -  Tabblad besturingssystemen inschakelen
    -  Tabblad installatiestatus inschakelen
    -  Tabblad van de naleving apparaat inschakelen
    -  Tabblad Opties inschakelen

### <a name="next-steps"></a>Volgende stappen

Zie voor meer informatie over Toepassingsbeheer in Configuration Manager, [inleiding op Toepassingsbeheer in System Center Configuration Manager](\sccm\apps\understand\introduction-to-application-management).
