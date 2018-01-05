---
title: Locatie van de inhoudsbron
titleSuffix: Configuration Manager
description: Meer informatie over de System Center Configuration Manager-instellingen die inschakelen voor clients om inhoud te zoeken op een traag netwerk.
ms.custom: na
ms.date: 1/3/2017
ms.reviewer: na
ms.suite: na
ms.prod: configuration-manager
ms.technology: configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 70b5cbc0-64ba-49bd-8b34-fb4c09b2b95b
caps.latest.revision: "3"
author: aczechowski
ms.author: aaroncz
manager: angrobe
ms.openlocfilehash: 03eb4d1fb08bfe8bf69af2c3e9ee035c8e2f8ab6
ms.sourcegitcommit: ca9d15dfb1c9eb47ee27ea9b5b39c9f8cdcc0748
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 01/04/2018
---
# <a name="content-source-location-scenarios-in-system-center-configuration-manager"></a>Inhoudsbron locatie scenario's in System Center Configuration Manager

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*

System Center Configuration Manager ondersteund voorafgaand aan versie 1610, verschillende instellingen die definiëren hoe en waar clients inhoud vinden wanneer ze op een traag netwerk worden gecombineerd. De mogelijke combinaties van invloed zijn op de locatie van inhoud clients worden gebruikt en of ze met succes een terugvallocatie wanneer een voorkeursbron kunnen gebruiken voor inhoud is niet beschikbaar.  

> [!IMPORTANT]  
> **Als uw sites versie 1511 of 1602 1606 uitgevoerd**, de informatie in dit onderwerp is van toepassing op uw infrastructuur. Zie ook [grensgroepen voor versies 1511,1602 en 1606](/sccm/core/servers/deploy/configure/boundary-groups-for-1511-1602-and-1606) voor informatie die specifiek is voor grensgroepen met deze versies van Configuration Manager.
>
> **Als uw sites versie wordt uitgevoerd 1610 of hoger**, gebruik de informatie in [sitegrenzen en grensgroepen definiëren voor System Center Configuration Manager](/sccm/core/servers/deploy/configure/define-site-boundaries-and-boundary-groups#boundary-groups) om te begrijpen hoe uw clients distributiepunten waarvoor beschikbare inhoud te vinden.





**De volgende drie instellingen bepalen het gedrag wanneer clients inhoud opvragen:**

-  **Terugvalbronlocatie voor inhoud toestaan** (ingeschakeld of niet is ingeschakeld): Dit is een optie die u kunt inschakelen op de **Grensgroepen** tabblad van een distributiepunt. Hierdoor kan de client een distributiepunt dat geconfigureerd als terugvallocatie wanneer inhoud niet beschikbaar is op een voorkeursdistributiepunt.  

 - **Implementatiegedrag voor netwerkverbindingssnelheid**: Elke implementatie is geconfigureerd met een van de volgende gedragingen wanneer de verbinding met het distributiepunt traag is:  

    -   **Inhoud downloaden vanaf het distributiepunt en lokaal uitvoeren**  

    -   **Inhoud niet downloaden**: Deze optie wordt alleen gebruikt wanneer een client een terugvallocatie gebruikt om inhoud te verkrijgen.  

    De verbindingssnelheid voor een distributiepunt is geconfigureerd op de **verwijzingen** tabblad van een grensgroep, en specifiek is voor de grensgroep.  

 -  **Pakketdistributie op aanvraag** (naar voorkeursdistributiepunten): Dit is ingeschakeld wanneer u de optie **Distribueer de inhoud voor dit pakket naar voorkeursdistributiepunten** op de **distributie-instellingen** tabblad van de eigenschappen van een pakket of toepassing. Wanneer dit is ingeschakeld, is deze optie zorgt ervoor dat Configuration Manager automatisch de inhoud kopieert naar een voorkeursdistributiepunt dat nog niet over de inhoud nadat een client die inhoud bij dat distributiepunt aanvraagt.  


 **De volgende vereisten zijn van toepassing op alle scenario's:**


-   Inhoud is beschikbaar op een terugvaldistributiepunt.  

-   Distributiepunten zijn online en toegankelijk is  


## <a name="scenario-1"></a>Scenario 1  
 Van toepassing wanneer de volgende configuraties bestaan:  

-   **Inhoud is beschikbaar op een voorkeursdistributiepunt.**  

-   **Terugval toestaan**: Niet ingeschakeld  

-   **Implementatiegedrag voor een traag netwerk**: Een willekeurige configuratie  


**Details:** (De configuratie voor pakketdistributie op aanvraag is niet relevant is in dit scenario.)  

1.  De client zendt een inhoudsaanvraag naar het beheerpunt.  

2.  Een inhoudlocatielijst wordt geretourneerd naar de client vanaf het beheerpunt met de voorkeursdistributiepunten die de inhoud bevatten.  

3.  De client downloadt de inhoud van een voorkeursdistributiepunt in de lijst.  

## <a name="scenario-2"></a>Scenario 2  
 De volgende configuraties bestaan:  

-   **Inhoud is beschikbaar op een voorkeursdistributiepunt.**  

-   **Terugval toestaan**: Ingeschakeld  

-   **Implementatiegedrag voor een traag netwerk**: Inhoud niet downloaden  


**Details:** (De configuratie voor pakketdistributie op aanvraag is niet relevant is in dit scenario.)  

1.  De client zendt een inhoudsaanvraag naar het beheerpunt. De client neemt een markering op in de aanvraag die aangeeft dat terugvaldistributiepunten zijn toegestaan.  

2.  Een inhoudlocatielijst wordt geretourneerd naar de client vanaf het beheerpunt met de voorkeursdistributiepunten en de terugvaldistributiepunten die de inhoud bevatten.  

3.  De client downloadt de inhoud van een voorkeursdistributiepunt in de lijst.  

## <a name="scenario-3"></a>Scenario 3  
 De volgende configuraties bestaan:  

-   **Inhoud is beschikbaar op een voorkeursdistributiepunt.**  

-   **Terugval toestaan**: Ingeschakeld  

-   **Implementatiegedrag voor een traag netwerk**: Inhoud downloaden en installeren  


**Details:** (De configuratie voor pakketdistributie op aanvraag is niet relevant is in dit scenario.)  

1.  De client zendt een inhoudsaanvraag naar het beheerpunt. De client neemt een markering op in de aanvraag die aangeeft dat terugvaldistributiepunten zijn toegestaan.  

2.  Een inhoudlocatielijst wordt geretourneerd naar de client vanaf het beheerpunt met de voorkeursdistributiepunten en de terugvaldistributiepunten die de inhoud bevatten.  

3.  De client downloadt de inhoud van een voorkeursdistributiepunt in de lijst.  

## <a name="scenario-4"></a>Scenario 4  
 De volgende configuraties bestaan:  

-   **Inhoud is niet beschikbaar op een voorkeursdistributiepunt.**  

-   **Distribueer de inhoud voor dit pakket naar voorkeursdistributiepunten** is niet ingeschakeld  

-   **Terugval toestaan**: Niet ingeschakeld  

-   **Implementatiegedrag voor een traag netwerk**: Een willekeurige configuratie  


**Details:**  

1.  De client zendt een inhoudsaanvraag naar het beheerpunt.  

2.  Een inhoudlocatielijst wordt geretourneerd naar de client vanaf het beheerpunt met de voorkeursdistributiepunten die de inhoud bevatten. Er zijn geen voorkeursdistributiepunten in de lijst.  

3.  De client mislukt met het bericht **inhoud is niet beschikbaar** en probeert het opnieuw. Een nieuwe inhoudsaanvraag wordt elk uur gestart.  

## <a name="scenario-5"></a>Scenario 5  
 De volgende configuraties bestaan:  

-   **Inhoud is niet beschikbaar op een voorkeursdistributiepunt.**  

-   **Distribueer de inhoud voor dit pakket naar voorkeursdistributiepunten** is niet ingeschakeld  

-   **Terugval toestaan**: Ingeschakeld  

-   **Implementatiegedrag voor een traag netwerk**: Inhoud niet downloaden  


**Details:**  

1.  De client zendt een inhoudsaanvraag naar het beheerpunt. De client neemt een markering op in de aanvraag die aangeeft dat terugvaldistributiepunten zijn toegestaan.  

2.  Een inhoudlocatielijst wordt geretourneerd naar de client vanaf het beheerpunt met de voorkeursdistributiepunten en de terugvaldistributiepunten die de inhoud bevatten. Er zijn geen voorkeursdistributiepunten die de inhoud bevatten, maar minstens één terugvaldistributiepunt heeft de inhoud.  

3.  De inhoud wordt niet gedownload omdat de implementatie-eigenschap voor de client het gebruik van een terugvaldistributiepunt is ingesteld op **inhoud niet downloaden** (die wordt gebruikt wanneer clients terugvallen op het ophalen van inhoud). De client mislukt met het bericht **inhoud is niet beschikbaar** en probeert het opnieuw. De client maakt een nieuwe inhoudsaanvraag elk uur.  

## <a name="scenario-6"></a>Scenario 6  
 De volgende configuraties bestaan:  

-   **Inhoud is niet beschikbaar op een voorkeursdistributiepunt.**  

-   **Distribueer de inhoud voor dit pakket naar voorkeursdistributiepunten** is niet ingeschakeld  

-   **Terugval toestaan**: Ingeschakeld  

-   **Implementatiegedrag voor een traag netwerk**: Inhoud downloaden en installeren  


**Details:**  

1.  De client zendt een inhoudsaanvraag naar het beheerpunt. De client neemt een markering op in de aanvraag die aangeeft dat terugvaldistributiepunten zijn ingeschakeld.  

2.  Een inhoudlocatielijst wordt geretourneerd naar de client vanaf het beheerpunt met de voorkeursdistributiepunten en de terugvaldistributiepunten die de inhoud bevatten. Er zijn geen voorkeursdistributiepunten die de inhoud bevatten, maar minstens één terugvaldistributiepunt heeft de inhoud.  

3.  De inhoud wordt gedownload van een terugvaldistributiepunt op de lijst omdat de implementatie-eigenschap voor de client het gebruik van een terugvaldistributiepunt is ingesteld op **downloaden en installeren van de inhoud**.  

## <a name="scenario-7"></a>Scenario 7  
 De volgende configuraties bestaan:  

-   **Inhoud is niet beschikbaar op een voorkeursdistributiepunt.**  

-   **Distribueer de inhoud voor dit pakket naar voorkeursdistributiepunten** is ingeschakeld  

-   **Terugval toestaan**: Niet ingeschakeld  

-   **Implementatiegedrag voor een traag netwerk**: Een willekeurige configuratie  


**Details:**  

1.  De client zendt een inhoudsaanvraag naar het beheerpunt.  

2.  Een inhoudlocatielijst wordt geretourneerd naar de client vanaf het beheerpunt met de voorkeursdistributiepunten die de inhoud bevatten. Er zijn geen voorkeursdistributiepunten die de inhoud bevatten.  

3.  De client mislukt met het bericht **inhoud is niet beschikbaar** en probeert het opnieuw. Een nieuwe inhoudsaanvraag wordt elk uur uitgevoerd.  

4.  Het beheerpunt maakt een trigger voor de Distribution Manager de inhoud te distribueren naar alle voorkeursdistributiepunten voor de client die de aanvraag heeft ingediend inhoud.  

5.  Distribution Manager distribueert de inhoud naar alle voorkeursdistributiepunten. In de meeste gevallen de inhoud wordt gedistribueerd naar de voorkeursdistributiepunten binnen een uur.  

6.  Een nieuwe inhoudsaanvraag wordt door de client naar het beheerpunt gestart.  

7.  Een inhoudlocatielijst wordt geretourneerd naar de client vanaf het beheerpunt met de voorkeursdistributiepunten die de inhoud bevatten. De client downloadt de inhoud van een voorkeursdistributiepunt in de lijst.  

## <a name="scenario-8"></a>Scenario 8  
 De volgende configuraties bestaan:  

-   **Inhoud is niet beschikbaar op een voorkeursdistributiepunt.**  

-   **Distribueer de inhoud voor dit pakket naar voorkeursdistributiepunten** is ingeschakeld  

-   **Terugval toestaan**: Ingeschakeld  

-   **Implementatiegedrag voor een traag netwerk**: Inhoud niet downloaden  


**Details:**  

1.  De client zendt een inhoudsaanvraag naar het beheerpunt. De client neemt een markering op in de aanvraag die aangeeft dat terugvaldistributiepunten zijn toegestaan.  

2.  Een inhoudlocatielijst wordt geretourneerd naar de client vanaf het beheerpunt met de voorkeursdistributiepunten en de terugvaldistributiepunten die de inhoud bevatten. Er zijn geen voorkeursdistributiepunten die de inhoud bevatten, maar minstens één terugvaldistributiepunt heeft de inhoud.  

3.  De inhoud wordt niet gedownload omdat de implementatie-eigenschap voor de client het gebruik van een terugvaldistributiepunt is ingesteld op **niet downloaden**. De client mislukt met het bericht **inhoud is niet beschikbaar** en probeert het opnieuw. De client maakt een nieuwe inhoudsaanvraag elk uur.  

4.  Het beheerpunt maakt een trigger voor de Distribution Manager de inhoud te distribueren naar alle voorkeursdistributiepunten voor de client die de aanvraag heeft ingediend inhoud.  

5.  Distribution Manager distribueert de inhoud naar alle voorkeursdistributiepunten. In de meeste gevallen de inhoud wordt gedistribueerd naar de voorkeursdistributiepunten binnen een uur.  

6.  Een nieuwe inhoudsaanvraag wordt door de client naar het beheerpunt gestart.  

7.  Een inhoudlocatielijst wordt geretourneerd naar de client vanaf het beheerpunt met de voorkeursdistributiepunten die de inhoud bevatten.  

8.  De client downloadt de inhoud van een voorkeursdistributiepunt in de lijst.  

## <a name="scenario-9"></a>Scenario 9  
 De volgende configuraties bestaan:  

-   **Inhoud is niet beschikbaar op een voorkeursdistributiepunt.**  

-   **Distribueer de inhoud voor dit pakket naar voorkeursdistributiepunten** is ingeschakeld  

-   **Terugval toestaan**: Ingeschakeld  

-   **Implementatiegedrag voor een traag netwerk**: Inhoud downloaden en installeren  


**Details:**  

1.  De client zendt een inhoudsaanvraag naar het beheerpunt. De client neemt een markering op in de aanvraag die aangeeft dat terugvaldistributiepunten zijn toegestaan.  

2.  Een inhoudlocatielijst wordt geretourneerd naar de client vanaf het beheerpunt met de voorkeursdistributiepunten en de terugvaldistributiepunten die de inhoud bevatten. Er zijn geen voorkeursdistributiepunten die de inhoud bevatten, maar minstens één terugvaldistributiepunt heeft de inhoud.  

3.  De inhoud wordt gedownload van een terugvaldistributiepunt op de lijst omdat de implementatie-eigenschap voor de client het gebruik van een terugvaldistributiepunt is ingesteld op **downloaden en installeren van de inhoud**. Deze implementatie-instelling kan een client die een locatie terugvalinhoudlocatie gebruiken moet om op te halen van de inhoud van die locatie.  

4.  Het beheerpunt maakt een trigger voor de Distribution Manager de inhoud te distribueren naar alle voorkeursdistributiepunten voor de client die de aanvraag heeft ingediend inhoud.  

5.  Distribution Manager distribueert de inhoud naar alle voorkeursdistributiepunten, waardoor meer clients inhoud kunnen verkrijgen zonder een terugvaldistributiepunt.  
