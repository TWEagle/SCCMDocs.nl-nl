---
title: De locatie van inhoud | Microsoft-documenten
description: Meer informatie over de instellingen van System Center Configuration Manager waarmee clients om inhoud te zoeken op een traag netwerk.
ms.custom: na
ms.date: 1/3/2017
ms.reviewer: na
ms.suite: na
ms.prod: configuration-manager
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 70b5cbc0-64ba-49bd-8b34-fb4c09b2b95b
caps.latest.revision: 3
author: Brenduns
ms.author: brenduns
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 7f2fd3e550c7dc1b27996dc309b53f74e8c865e9
ms.openlocfilehash: a823458dc3b891b1c32d1cb44a96e8cafd376ed5
ms.contentlocale: nl-nl
ms.lasthandoff: 05/17/2017

---
# <a name="content-source-location-scenarios-in-system-center-configuration-manager"></a>Locatie scenario's voor inhoudsbron in System Center Configuration Manager

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*

System Center Configuration Manager ondersteund voor versie 1610 diverse instellingen die definiëren hoe en wanneer clients inhoud zoeken wanneer ze op een traag netwerk worden gecombineerd. Mogelijke combinaties van invloed op de locatie van inhoud clients worden gebruikt en of ze is een alternatieve locatie als een voorkeursbron kunnen gebruiken voor inhoud is niet beschikbaar.  

> [!IMPORTANT]  
> **Als uw sites versie 1511, 1602 of 1606 uitvoeren**, de informatie in dit onderwerp is van toepassing op uw infrastructuur. Zie ook [grensgroepen voor versies 1511,1602 en 1606](/sccm/core/servers/deploy/configure/boundary-groups-for-1511-1602-and-1606) voor gegevens die specifiek is voor grensgroepen met deze versies van Configuration Manager.
>
> **Als uw sites versie wordt uitgevoerd 1610 of hoger**, gebruik de informatie in [sitegrenzen en grensgroepen definiëren voor System Center Configuration Manager](/sccm/core/servers/deploy/configure/define-site-boundaries-and-boundary-groups#boundary-groups) om te begrijpen hoe uw clients distributiepunten met beschikbare inhoud zoeken.





**De volgende drie instellingen bepalen het gedrag wanneer clients inhoud opvragen:**

-  **Terugvalbronlocatie voor inhoud toestaan** (ingeschakeld of niet is ingeschakeld): Dit is een optie die u kunt inschakelen op de **Grensgroepen** tabblad van een distributiepunt. Hiermee wordt de client een distributiepunt dat geconfigureerd als een terugvallocatie wanneer inhoud niet beschikbaar op een voorkeursdistributiepunt is.  

 - **Implementatiegedrag voor netwerkverbindingssnelheid**: Elke implementatie is geconfigureerd met een van de volgende problemen moet worden gebruikt wanneer de verbinding met het distributiepunt traag is:  

    -   **Inhoud downloaden vanaf het distributiepunt en lokaal uitvoeren**  

    -   **Inhoud niet downloaden**: Deze optie wordt alleen gebruikt wanneer een client een terugvallocatie gebruikt inhoud te verkrijgen.  

    De verbindingssnelheid voor een distributiepunt is geconfigureerd op de **verwijzingen** tabblad van een grensgroep en specifiek is voor deze grensgroep.  

 -  **Pakketdistributie op aanvraag** (naar voorkeursdistributiepunten): Dit wordt ingeschakeld wanneer u de optie **Distribueer de inhoud van dit pakket naar voorkeursdistributiepunten** op de **distributie-instellingen** tab van eigenschappen voor een pakket of de toepassing. Wanneer dit is ingeschakeld, is deze optie zorgt ervoor dat Configuration Manager automatisch kopiëren van de inhoud naar een voorkeursdistributiepunt die nog niet over de inhoud nadat een client die inhoud vanuit dat distributiepunt aanvraagt.  


 **De volgende vereisten van toepassing op alle scenario's:**


-   Inhoud is beschikbaar op een terugvaldistributiepunt  

-   Distributiepunten zijn online en zijn toegankelijk  


## <a name="scenario-1"></a>Scenario 1  
 Van toepassing wanneer het bestaan van de volgende configuraties:  

-   **Inhoud is beschikbaar op een voorkeursdistributiepunt**  

-   **Terugval toestaan**: Niet ingeschakeld  

-   **Implementatiegedrag voor langzaam netwerk**: Een willekeurige configuratie  


**Details:** (De configuratie voor pakketdistributie op aanvraag is niet relevant voor dit scenario.)  

1.  De client zendt een inhoudsaanvraag naar het beheerpunt.  

2.  Een inhoudlocatielijst wordt geretourneerd naar de client vanaf het beheerpunt met de voorkeursdistributiepunten die de inhoud bevatten.  

3.  De client downloadt de inhoud van een voorkeursdistributiepunt in de lijst.  

## <a name="scenario-2"></a>Scenario 2  
 De volgende configuraties bestaan:  

-   **Inhoud is beschikbaar op een voorkeursdistributiepunt**  

-   **Terugval toestaan**: Ingeschakeld  

-   **Implementatiegedrag voor langzaam netwerk**: Inhoud niet downloaden  


**Details:** (De configuratie voor pakketdistributie op aanvraag is niet relevant voor dit scenario.)  

1.  De client zendt een inhoudsaanvraag naar het beheerpunt. De client neemt een markering op in de aanvraag die aangeeft dat terugvaldistributiepunten zijn toegestaan.  

2.  Een inhoudlocatielijst wordt geretourneerd naar de client vanaf het beheerpunt met de voorkeursdistributiepunten en de terugvaldistributiepunten die de inhoud bevatten.  

3.  De client downloadt de inhoud van een voorkeursdistributiepunt in de lijst.  

## <a name="scenario-3"></a>Scenario 3  
 De volgende configuraties bestaan:  

-   **Inhoud is beschikbaar op een voorkeursdistributiepunt**  

-   **Terugval toestaan**: Ingeschakeld  

-   **Implementatiegedrag voor langzaam netwerk**: Inhoud downloaden en installeren  


**Details:** (De configuratie voor pakketdistributie op aanvraag is niet relevant voor dit scenario.)  

1.  De client zendt een inhoudsaanvraag naar het beheerpunt. De client neemt een markering op in de aanvraag die aangeeft dat terugvaldistributiepunten zijn toegestaan.  

2.  Een inhoudlocatielijst wordt geretourneerd naar de client vanaf het beheerpunt met de voorkeursdistributiepunten en de terugvaldistributiepunten die de inhoud bevatten.  

3.  De client downloadt de inhoud van een voorkeursdistributiepunt in de lijst.  

## <a name="scenario-4"></a>Scenario 4  
 De volgende configuraties bestaan:  

-   **Inhoud is niet beschikbaar op een voorkeursdistributiepunt**  

-   **Distribueer de inhoud van dit pakket naar voorkeursdistributiepunten** is niet ingeschakeld  

-   **Terugval toestaan**: Niet ingeschakeld  

-   **Implementatiegedrag voor langzaam netwerk**: Een willekeurige configuratie  


**Details:**  

1.  De client zendt een inhoudsaanvraag naar het beheerpunt.  

2.  Een inhoudlocatielijst wordt geretourneerd naar de client vanaf het beheerpunt met de voorkeursdistributiepunten die de inhoud bevatten. Er zijn geen voorkeursdistributiepunten in de lijst.  

3.  De client mislukt met het bericht **inhoud is niet beschikbaar** en probeer het opnieuw probeert. Een nieuwe inhoudsaanvraag wordt elk uur gestart.  

## <a name="scenario-5"></a>Scenario 5  
 De volgende configuraties bestaan:  

-   **Inhoud is niet beschikbaar op een voorkeursdistributiepunt**  

-   **Distribueer de inhoud van dit pakket naar voorkeursdistributiepunten** is niet ingeschakeld  

-   **Terugval toestaan**: Ingeschakeld  

-   **Implementatiegedrag voor langzaam netwerk**: Inhoud niet downloaden  


**Details:**  

1.  De client zendt een inhoudsaanvraag naar het beheerpunt. De client neemt een markering op in de aanvraag die aangeeft dat terugvaldistributiepunten zijn toegestaan.  

2.  Een inhoudlocatielijst wordt geretourneerd naar de client vanaf het beheerpunt met de voorkeursdistributiepunten en de terugvaldistributiepunten die de inhoud bevatten. Er zijn geen voorkeursdistributiepunten die de inhoud bevatten, maar minstens één terugvaldistributiepunt heeft de inhoud.  

3.  De inhoud is niet gedownload omdat de implementatie-eigenschap voor de client het gebruik van een terugvaldistributiepunt is ingesteld op **inhoud niet downloaden** (die wordt gebruikt wanneer clients terugvallen op het verkrijgen van de inhoud). De client mislukt met het bericht **inhoud is niet beschikbaar** en probeer het opnieuw probeert. De client maakt een nieuwe inhoudsaanvraag elk uur.  

## <a name="scenario-6"></a>Scenario 6  
 De volgende configuraties bestaan:  

-   **Inhoud is niet beschikbaar op een voorkeursdistributiepunt**  

-   **Distribueer de inhoud van dit pakket naar voorkeursdistributiepunten** is niet ingeschakeld  

-   **Terugval toestaan**: Ingeschakeld  

-   **Implementatiegedrag voor langzaam netwerk**: Inhoud downloaden en installeren  


**Details:**  

1.  De client zendt een inhoudsaanvraag naar het beheerpunt. De client neemt een markering op in de aanvraag die aangeeft dat terugvaldistributiepunten zijn ingeschakeld.  

2.  Een inhoudlocatielijst wordt geretourneerd naar de client vanaf het beheerpunt met de voorkeursdistributiepunten en de terugvaldistributiepunten die de inhoud bevatten. Er zijn geen voorkeursdistributiepunten die de inhoud bevatten, maar minstens één terugvaldistributiepunt heeft de inhoud.  

3.  De inhoud wordt gedownload van een terugvaldistributiepunt op de lijst omdat de implementatie-eigenschap voor de client het gebruik van een terugvaldistributiepunt is ingesteld op **downloaden en installeren van de inhoud**.  

## <a name="scenario-7"></a>Scenario 7  
 De volgende configuraties bestaan:  

-   **Inhoud is niet beschikbaar op een voorkeursdistributiepunt**  

-   **Distribueer de inhoud van dit pakket naar voorkeursdistributiepunten** is ingeschakeld  

-   **Terugval toestaan**: Niet ingeschakeld  

-   **Implementatiegedrag voor langzaam netwerk**: Een willekeurige configuratie  


**Details:**  

1.  De client zendt een inhoudsaanvraag naar het beheerpunt.  

2.  Een inhoudlocatielijst wordt geretourneerd naar de client vanaf het beheerpunt met de voorkeursdistributiepunten die de inhoud bevatten. Er zijn geen voorkeursdistributiepunten die de inhoud bevatten.  

3.  De client mislukt met het bericht **inhoud is niet beschikbaar** en probeer het opnieuw probeert. Een nieuwe inhoudsaanvraag wordt elk uur gemaakt.  

4.  Het beheerpunt maakt een trigger voor de Distribution Manager de inhoud distribueren naar alle voorkeursdistributiepunten voor de client die de inhoudsaanvraag heeft gemaakt.  

5.  Distribution Manager distribueert de inhoud naar alle voorkeursdistributiepunten. Meestal wordt de inhoud wordt gedistribueerd naar de voorkeursdistributiepunten binnen een uur.  

6.  Een nieuwe inhoudsaanvraag wordt door de client naar het beheerpunt gestart.  

7.  Een inhoudlocatielijst wordt geretourneerd naar de client vanaf het beheerpunt met de voorkeursdistributiepunten die de inhoud bevatten. De client downloadt de inhoud van een voorkeursdistributiepunt in de lijst.  

## <a name="scenario-8"></a>Scenario 8  
 De volgende configuraties bestaan:  

-   **Inhoud is niet beschikbaar op een voorkeursdistributiepunt**  

-   **Distribueer de inhoud van dit pakket naar voorkeursdistributiepunten** is ingeschakeld  

-   **Terugval toestaan**: Ingeschakeld  

-   **Implementatiegedrag voor langzaam netwerk**: Inhoud niet downloaden  


**Details:**  

1.  De client zendt een inhoudsaanvraag naar het beheerpunt. De client neemt een markering op in de aanvraag die aangeeft dat terugvaldistributiepunten zijn toegestaan.  

2.  Een inhoudlocatielijst wordt geretourneerd naar de client vanaf het beheerpunt met de voorkeursdistributiepunten en de terugvaldistributiepunten die de inhoud bevatten. Er zijn geen voorkeursdistributiepunten die de inhoud bevatten, maar minstens één terugvaldistributiepunt heeft de inhoud.  

3.  De inhoud is niet gedownload omdat de implementatie-eigenschap voor de client het gebruik van een terugvaldistributiepunt is ingesteld op **niet downloaden**. De client mislukt met het bericht **inhoud is niet beschikbaar** en probeer het opnieuw probeert. De client maakt een nieuwe inhoudsaanvraag elk uur.  

4.  Het beheerpunt maakt een trigger voor de Distribution Manager de inhoud distribueren naar alle voorkeursdistributiepunten voor de client die de inhoudsaanvraag heeft gemaakt.  

5.  Distribution Manager distribueert de inhoud naar alle voorkeursdistributiepunten. Meestal wordt de inhoud wordt gedistribueerd naar de voorkeursdistributiepunten binnen een uur.  

6.  Een nieuwe inhoudsaanvraag wordt door de client naar het beheerpunt gestart.  

7.  Een inhoudlocatielijst wordt geretourneerd naar de client vanaf het beheerpunt met de voorkeursdistributiepunten die de inhoud bevatten.  

8.  De client downloadt de inhoud van een voorkeursdistributiepunt in de lijst.  

## <a name="scenario-9"></a>Scenario 9  
 De volgende configuraties bestaan:  

-   **Inhoud is niet beschikbaar op een voorkeursdistributiepunt**  

-   **Distribueer de inhoud van dit pakket naar voorkeursdistributiepunten** is ingeschakeld  

-   **Terugval toestaan**: Ingeschakeld  

-   **Implementatiegedrag voor langzaam netwerk**: Inhoud downloaden en installeren  


**Details:**  

1.  De client zendt een inhoudsaanvraag naar het beheerpunt. De client neemt een markering op in de aanvraag die aangeeft dat terugvaldistributiepunten zijn toegestaan.  

2.  Een inhoudlocatielijst wordt geretourneerd naar de client vanaf het beheerpunt met de voorkeursdistributiepunten en de terugvaldistributiepunten die de inhoud bevatten. Er zijn geen voorkeursdistributiepunten die de inhoud bevatten, maar minstens één terugvaldistributiepunt heeft de inhoud.  

3.  De inhoud wordt gedownload van een terugvaldistributiepunt op de lijst omdat de implementatie-eigenschap voor de client het gebruik van een terugvaldistributiepunt is ingesteld op **downloaden en installeren van de inhoud**. Deze instelling implementatie kan clients die een locatie terugvalinhoudlocatie moet met de inhoud downloaden van die locatie.  

4.  Het beheerpunt maakt een trigger voor de Distribution Manager de inhoud distribueren naar alle voorkeursdistributiepunten voor de client die de inhoudsaanvraag heeft gemaakt.  

5.  Distribution Manager distribueert de inhoud naar alle voorkeursdistributiepunten, waarmee u meer clients de inhoud verkrijgen zonder gebruik van een terugvaldistributiepunt.  

