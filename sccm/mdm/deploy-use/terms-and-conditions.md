---
title: Voorwaarden en bepalingen in System Center Configuration Manager | Microsoft-documenten
description: Voorwaarden en bepalingen implementeren op gebruikersgroepen in System Center Configuration Manager.
ms.custom: na
ms.date: 03/05/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-hybrid
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 4d3f9e6b-4d71-4fc4-9b91-47f1bfbd8c70
caps.latest.revision: 9
author: nathbarn
ms.author: nathbarn
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 3b1451edaed69a972551bd060293839aa11ec8b2
ms.openlocfilehash: 20be68496099a67ad2d475067f073da2cef16c86
ms.contentlocale: nl-nl
ms.lasthandoff: 05/17/2017


---
# <a name="add-terms-and-conditions-with-system-center-configuration-manager"></a>Voorwaarden en bepalingen met System Center Configuration Manager toevoegen

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*

U kunt System Center Configuration Manager-voorwaarden en bepalingen implementeren op gebruikersgroepen waarin wordt uitgelegd hoe apparaatinschrijving, toegang tot het werk en via de bedrijfsportal invloed op apparaten en gebruikers. Gebruikers moeten de voorwaarden accepteren voordat ze de bedrijfsportal kunnen gebruiken om hun apparaat te registreren en toegang te krijgen tot hun werk.  

 ## <a name="working-with-terms-and-conditions-policies-in-system-center-configuration-manager"></a>Werken met voorwaarden in System Center Configuration Manager  
 U kunt meerdere sets voorwaarden maken en implementeren. U kunt ook meerdere versies van dezelfde voorwaarden in verschillende talen maken en deze voor de betreffende groepen implementeren.  

## <a name="to-create-a-terms-and-conditions"></a>Voorwaarden maken  

1.  Ga in de Configuration Manager-console naar **Activa en naleving** > **Overzicht** > **Instellingen voor naleving** > **Voorwaarden**.  

2.  Klik op **Voorwaarden maken** om nieuwe voorwaarden te maken.  

3.  Geef op de pagina **Algemeen** de volgende gegevens op:  

    -   **Naam** -een unieke naam weergegeven in de Configuration Manager-console  

    -   **Beschrijving** - die helpen identificeren van de bepalingen en voorwaarden in de Configuration Manager-console  

     Klik vervolgens op **Volgende**.  

4.  Geef op de pagina **Voorwaarden** de volgende gegevens op:  

    -   **Titel** : de titel die voor gebruikers in de bedrijfsportal wordt weergegeven  

    -   **Tekst voor voorwaarden** : de voorwaarden die voor gebruikers in de bedrijfsportal worden weergegeven  

    -   **Tekst waarmee wordt uitgelegd wat het inhoudt als de gebruiker de voorwaarden accepteert** e verklaring die gebruikers zien in verband met aanvaarding **Voorbeeld**: "Ik ga akkoord met de voorwaarden en bepalingen."  

     Klik vervolgens op **Volgende**.  

5.  Voltooi de wizard om de nieuwe voorwaarden te maken. De nieuwe voorwaarden worden weergegeven in het knooppunt Voorwaarden van de werkruimte Activa en naleving.  

## <a name="to-deploy-a-terms-and-conditions"></a>Voorwaarden implementeren  

1.  Ga in de Configuration Manager-console naar **Activa en naleving** > **Overzicht** > **Instellingen voor naleving** > **Voorwaarden**.  

2.  Selecteer in de lijst **Voorwaarden** het item dat u wilt implementeren en klik vervolgens op **Implementeren**.  

3.  **Blader** naar de **Verzameling** waarnaar u de voorwaarden wilt implementeren en klik vervolgens op **OK**.  

     Wanneer de betreffende apparaten de bedrijfsportal-app openen, worden de voorwaarden weergegeven die u hebt geïmplementeerd. Gebruikers moeten deze voorwaarden accepteren voordat ze toegang krijgen tot bedrijfsresources.  

    > [!NOTE]  
    >  Als u een set voorwaarden implementeert naar meerdere gebruikersverzamelingen waartoe een gebruiker behoort, ziet deze gebruiker bij het openen van de bedrijfsportal meerdere exemplaren van dezelfde voorwaarden. Omdat gebruikers alleen alle voorwaarden kunnen accepteren of weigeren, is er geen gevaar voor een niet-eenduidige acceptatiestatus waar de gebruiker de voorwaarden zowel heeft geaccepteerd als geweigerd. Het rapport Acceptatie van voorwaarden bevat slechts één rij voor elke set voorwaarden voor elke gebruiker. Het rapport bevat dus geen fouten.  

## <a name="to-monitor-terms-and-conditions"></a>Voorwaarden controleren  

1.  U kunt voorwaarden en bepalingen implementaties in de Configuration Manager-console bewaken. Open de Configuration Manager-console en ga naar **Bewaking** > **Overzicht** > **Implementaties**.  

2.  Selecteer de implementatie voor voorwaarden in de lijst met implementaties.  

     In het samenvattingsgebied worden de volgende statistische gegevens weergegeven:  

    -   **Compatibel** : gebruikers hebben de nieuwste versie van de voorwaarden geaccepteerd  

    -   **Fout**  

    -   **Niet-compatibel** : gebruikers hebben een versie van de voorwaarden geaccepteerd, maar niet de meest recente versie  

    -   **Onbekend** : gebruikers hebben de voorwaarden nooit geaccepteerd, inclusief gebruikers met een geregistreerd apparaat  

3.  Selecteer een implementatie voor voorwaarden en selecteer vervolgens **Samenvatting uitvoeren** om de implementatiestatus van afzonderlijke gebruikers te bekijken.  

     Op het scherm Implementatiestatus kunt u de statustabbladen selecteren om gebruikers met die status weer te geven. U kunt op **Samenvatting uitvoeren** klikken om de gegevens in de gehele hiërarchie bij te werken. Klik op **Vernieuwen** om de gegevens in de console bij te werken.  

## <a name="to-view--a-terms-and-conditions-report"></a>Een rapport van voorwaarden weergeven  

1.  Open de Configuration Manager-console en ga naar **Bewaking** > **Overzicht** > **Rapportage** > **Rapport**.  

2.  Selecteer **Acceptatie van de Voorwaarden** en klik vervolgens op **Uitvoeren**. Het rapport Acceptatie van voorwaarden wordt geopend. Het rapport geeft elke gebruiker weer voor wie de voorwaarden zijn geïmplementeerd. Dit zijn enkele velden:  

    -   Naam van voorwaarden  

    -   Gebruikersnaam  

    -   Geaccepteerde versie  

    -   Geaccepteerd op  

    -   Laatste geaccepteerd  

## <a name="updates-and-version-control-for-terms-and-conditions"></a>Updates en versiebeheer voor voorwaarden  
 Wanneer u bestaande voorwaarden bewerkt, kunt u het gewenste gedrag kiezen wanneer u de voorwaarden implementeert. Volg de volgende procedure om bestaande voorwaarden bij te werken.  

### <a name="how-to-work-with-multiple-versions-of-terms-and-conditions"></a>Met meerdere versies van voorwaarden werken  

1.  Ga in de Configuration Manager-console naar **Activa en naleving** > **Overzicht** > **Instellingen voor naleving** > **Voorwaarden**.  

2.  Selecteer het exemplaar van de voorwaarden dat u wilt bewerken en dubbelklik om dit te openen.  

3.  U kunt gewenste wijzigingen doorvoeren op de pagina **Algemeen** of **Voorwaarden** .  

4.  Op de pagina **Voorwaarden** geeft u aan of alle gebruikers de nieuwe voorwaarden moeten accepteren, of dat alleen nieuwe gebruikers de nieuwe versie zien.  

     Het wordt aangeraden het versienummer te verhogen en elke keer dat u belangrijke wijzigingen doorvoert te vereisen dat gebruikers de nieuwe voorwaarden accepteren. Behoud het huidige versienummer als u bijvoorbeeld typefouten wilt herstellen of de opmaak wilt wijzigen.

> [!div class="button"]
[< Vorige stap](configure-intune-subscription.md)[volgende stap >  ](create-service-connection-point.md)

