---
title: Apparaat-en Gebruikersbronnen detecteren | Microsoft-documenten
description: Lees een overzicht van de detectie gegevensrecords van proces en detectie.
ms.custom: na
ms.date: 2/8/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: get-started-article
ms.assetid: 30844519-ce14-456f-bfb8-4318b578e9f6
caps.latest.revision: 20
caps.handback.revision: 0
author: Brenduns
ms.author: brenduns
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 7b6674f331c82cc7899b8661cf38b9d3022cf21b
ms.openlocfilehash: 647826e9d340d3ef97abab0dba51041a3727dedc
ms.contentlocale: nl-nl
ms.lasthandoff: 05/17/2017


---
# <a name="run-discovery-for-system-center-configuration-manager"></a>Detectie uitvoeren voor System Center Configuration Manager

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*

U kunt een of meer detectiemethoden in System Center Configuration Manager apparaat- en bronnen die u kunt beheren. U kunt ook detectie gebruiken om netwerkinfrastructuur te identificeren in uw omgeving. Er zijn verschillende methoden die voor het detecteren van andere dingen kunt u en elke methode heeft een eigen configuraties en beperkingen.  

## <a name="overview-of-discovery"></a>Overzicht van detectie  
 Detectie is het proces waarmee Configuration Manager detecteert de zaken die u kunt beheren. De beschikbare detectiemethoden zijn:  

-   Detectie van Active Directory-forests  

-   Active Directory-groepdetectie  

-   Active Directory-systeemdetectie  

-   Detectie Active Directory-gebruiker  

-   Heartbeat-detectie  

-   Netwerkdetectie  

-   Serverdetectie  

> [!TIP]  
>  U vindt meer informatie over de afzonderlijke detectiemethoden in [Detectiemethoden voor System Center Configuration Manager](../../../../core/servers/deploy/configure/about-discovery-methods.md).  
>   
>  Raadpleeg voor hulp bij het selecteren van welke methoden te gebruiken en op welke sites in uw hiërarchie, [detectiemethoden gebruiken om te gebruiken voor System Center Configuration Manager selecteren](../../../../core/servers/deploy/configure/select-discovery-methods-to-use.md).  

 Als u wilt bijvoorbeeld de meeste detectiemethoden gebruiken, moet u de methode op een site inschakelen en stel maximaal specifieke netwerkprofielen zoeken of Active Directory-locaties. Wanneer deze wordt uitgevoerd, hiervoor wordt in de opgegeven locatie voor informatie over de apparaten of gebruikers die Configuration Manager kunt beheren. Wanneer een detectiemethode wordt informatie over een bron is gevonden, worden die gegevens in een bestand met de naam van een detectiegegevensrecord (DDR) geplaatst. Dit bestand wordt vervolgens verwerkt door een primaire of centrale beheersite. Als een DDR wordt verwerkt, wordt voor nieuwe gedetecteerde bronnen een nieuw record gemaakt in de sitedatabase. De records van bestaande bronnen worden bijgewerkt met de nieuwe informatie.  

 Sommige detectiemethoden kunnen grote volumes netwerkverkeer genereren en de DDR's die ze produceren tijdens de verwerking kunnen leiden tot een aanzienlijke gebruik van CPU-resources. Plan daarom alleen die detectiemethoden die u nodig hebt om uw doelstellingen te behalen. U kunt bijvoorbeeld beginnen met slechts één of twee detectiemethoden en later op een gecontroleerde manier verdere methoden inschakelen om het detectieniveau in uw omgeving uit te breiden.  

 Nadat de detectie-informatie wordt toegevoegd aan de sitedatabase, repliceert vervolgens de informatie voor elke site in de hiërarchie, ongeacht waar deze is gedetecteerd of verwerkt. Daarom terwijl u verschillende schema's en instellingen voor detectiemethoden op verschillende sites instellen kunt, misschien voert u een specifieke detectiemethode op slechts één enkele site. Dit vermindert het gebruik van netwerkbandbreedte via dubbele detectieacties en vermindert de verwerking van redundante detectiegegevens op meerdere sites.  

 U kunt detectiegegevens gebruiken voor het maken van aangepaste verzamelingen en query's die bronnen voor beheertaken, logisch groeperen. Bijvoorbeeld:  

-   Pushen clientinstallaties of upgraden.  

-   Inhoud implementeren voor gebruikers of apparaten.  

-   Implementatie van clientinstellingen en de bijbehorende configuraties.

##  <a name="BKMK_DDRs"></a>Over detectiegegevensrecords  
 DDR's zijn bestanden gemaakt door een detectiemethode. Ze bevatten informatie over een bron die u kunt beheren in Configuration Manager, zoals computers, gebruikers, en in sommige gevallen netwerkinfrastructuur. Ze worden verwerkt op primaire sites of op centrale beheersites. Nadat de broninformatie in de DDR ingevoerd is in de database, de DDR gewist en de informatie repliceert als globale gegevens naar alle sites in de hiërarchie.  

 De site waarop een DDR wordt verwerkt, hangt af van de informatie die het bevat:  

-   DDR's voor nieuwe gedetecteerde bronnen die zich worden niet in de database verwerkt op de site op het hoogste niveau van de hiërarchie. Het hoogste niveau maakt een nieuw bronrecord aan in de database en een unieke id toegewezen. DDR's worden overgedragen door replicatie op basis van het bestand totdat het hoogste niveau is bereikt.  

-   DDR's voor eerder gedetecteerde objecten zijn op primaire sites verwerkt. Onderliggende sites dragen geen DDR's over naar de centrale beheersite, wanneer de DDR informatie bevat over een bron die reeds in de database aanwezig is.  

-   Secundaire sites verwerken geen DDR's, en dragen ze altijd over door replicatie op basis van bestanden naar hun bovenliggende primaire site.  

DDR-bestanden worden geïdentificeerd door de .ddr-extense en hebben een typische grootte van ongeveer 1 KB.  

## <a name="get-started-with-discovery"></a>Aan de slag met detectie:  
 Voordat u de Configuration Manager-console voor het instellen van detectie gebruikt, moet u de verschillen tussen de methoden, welke acties ze kunnen uitvoeren, en in sommige hun beperkingen begrijpen.  

De volgende onderwerpen kunnen bouwen een foundation waarmee u detectiemethoden met succes gebruiken:  

-   [Over detectiemethoden voor System Center Configuration Manager](../../../../core/servers/deploy/configure/about-discovery-methods.md)  

-   [Selecteer detectiemethoden gebruiken om te gebruiken voor System Center Configuration Manager](../../../../core/servers/deploy/configure/select-discovery-methods-to-use.md)  

Als u de methoden die u wilt gebruiken begrijpt, zoek vervolgens richtlijnen voor het instellen van elke methode in [detectiemethoden configureren voor System Center Configuration Manager](../../../../core/servers/deploy/configure/configure-discovery-methods.md).  

