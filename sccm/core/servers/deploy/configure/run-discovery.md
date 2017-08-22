---
title: Apparaat-en Gebruikersbronnen detecteren | Microsoft Docs
description: Een overzicht van de detectie en detectie van proces gegevensrecords lezen.
ms.custom: na
ms.date: 2/8/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: configmgr-other
ms.tgt_pltfrm: na
ms.topic: get-started-article
ms.assetid: 30844519-ce14-456f-bfb8-4318b578e9f6
caps.latest.revision: "20"
caps.handback.revision: "0"
author: Brenduns
ms.author: brenduns
manager: angrobe
ms.openlocfilehash: 647826e9d340d3ef97abab0dba51041a3727dedc
ms.sourcegitcommit: 51fc48fb023f1e8d995c6c4eacfda7dbec4d0b2f
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 08/07/2017
---
# <a name="run-discovery-for-system-center-configuration-manager"></a>Detectie uitvoeren voor System Center Configuration Manager

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*

U kunt een of meer detectiemethoden in System Center Configuration Manager apparaat- en resources zoeken die u kunt beheren. U kunt detectie ook gebruiken om te identificeren netwerkinfrastructuur in uw omgeving. Er zijn verschillende methoden die u gebruiken kunt om verschillende objecten te detecteren en elke methode heeft z'n eigen configuraties en beperkingen.  

## <a name="overview-of-discovery"></a>Overzicht van detectie  
 Detectie is het proces waarmee Configuration Manager gegevens verzamelt over de elementen die u kunt beheren. De beschikbare detectiemethoden zijn:  

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
>  Voor hulp bij het selecteren welke methoden te gebruiken en op welke sites in uw hiërarchie, Zie [detectiemethoden selecteren om te gebruiken voor System Center Configuration Manager](../../../../core/servers/deploy/configure/select-discovery-methods-to-use.md).  

 Voor het gebruik van de meeste detectiemethoden moet u de methode op een site inschakelen en instellen dat deze zoekopdracht specifieke netwerk- of Active Directory-locaties. Wanneer deze wordt uitgevoerd, wordt de opgegeven locatie voor informatie over apparaten of gebruikers die met Configuration Manager beheren kunnen opgevraagd. Wanneer een detectiemethode informatie over een bron gevonden, worden die gegevens in een bestand met de naam van een detectiegegevensrecord (DDR) geplaatst. Dit bestand wordt vervolgens verwerkt door een primaire of centrale beheersite. Als een DDR wordt verwerkt, wordt voor nieuwe gedetecteerde bronnen een nieuw record gemaakt in de sitedatabase. De records van bestaande bronnen worden bijgewerkt met de nieuwe informatie.  

 Sommige detectiemethoden kunnen een grote hoeveelheid netwerkverkeer genereren en het aantal DDR's die ze produceren kunnen leiden tot een aanzienlijk gebruik van CPU-resources tijdens de verwerking. Plan daarom alleen die detectiemethoden die u nodig hebt om uw doelstellingen te behalen gebruiken. U kunt bijvoorbeeld beginnen met slechts één of twee detectiemethoden en later op een gecontroleerde manier verdere methoden inschakelen om het detectieniveau in uw omgeving uit te breiden.  

 Nadat detectie-informatie is toegevoegd aan de sitedatabase, wordt de gegevens vervolgens gerepliceerd naar elke site in de hiërarchie, ongeacht waar deze is gedetecteerd of verwerkt. Daarom terwijl u verschillende planningen en instellingen voor detectiemethoden op verschillende sites instellen kunt, kunt u een detectiemethode uitvoeren op één site. Dit vermindert het gebruik van netwerkbandbreedte door dubbele detectieacties en vermindert de verwerking van redundante detectiegegevens op meerdere sites.  

 U kunt detectiegegevens gebruiken voor het maken van aangepaste verzamelingen en query's waarmee u bronnen voor beheertaken logisch groepen. Bijvoorbeeld:  

-   Pushen clientinstallaties of upgraden.  

-   Inhoud implementeren voor gebruikers of apparaten.  

-   Clientinstellingen en gerelateerde configuraties implementeren.

##  <a name="BKMK_DDRs"></a>Over detectiegegevensrecords  
 DDR's zijn bestanden gemaakt door een detectiemethode. Ze bevatten informatie over een bron die u kunt beheren in Configuration Manager, zoals computers, gebruikers, en in sommige gevallen netwerkinfrastructuur. Ze worden verwerkt op primaire sites of op centrale beheersites. Nadat de broninformatie in de DDR ingevoerd is in de database, de DDR gewist en de informatie repliceert als globale gegevens naar alle sites in de hiërarchie.  

 De site waarop een DDR wordt verwerkt, hangt af van de informatie die het bevat:  

-   DDR's voor nieuwe gedetecteerde bronnen die zich worden niet in de database verwerkt op het hoogste niveau van de hiërarchie. Op het hoogste niveau maakt een nieuwe bronrecord in de database, en een unieke id toegewezen. DDR's worden overgedragen door middel van bestandsgebaseerde replicatie totdat ze op het hoogste niveau.  

-   DDR's voor eerder gedetecteerde objecten zijn op primaire sites verwerkt. Onderliggende sites dragen geen DDR's over naar de centrale beheersite, wanneer de DDR informatie bevat over een bron die reeds in de database aanwezig is.  

-   Secundaire sites niet verwerken DDR's, en dragen ze altijd over door replicatie op basis van bestanden naar hun bovenliggende primaire site.  

DDR-bestanden worden geïdentificeerd door de .ddr-extense en hebben een typische grootte van ongeveer 1 KB.  

## <a name="get-started-with-discovery"></a>Aan de slag met detectie:  
 Voordat u de Configuration Manager-console voor het instellen van detectie gebruikt, moet u de verschillen tussen de methoden, wat ze kunnen uitvoeren, en in sommige gevallen hun beperkingen begrijpen.  

De volgende onderwerpen kunnen een basis vormen waarmee kunt u detectiemethoden met succes gebruiken:  

-   [Over detectiemethoden voor System Center Configuration Manager](../../../../core/servers/deploy/configure/about-discovery-methods.md)  

-   [Detectiemethoden selecteren om te gebruiken voor System Center Configuration Manager](../../../../core/servers/deploy/configure/select-discovery-methods-to-use.md)  

Als u de methoden die u wilt gebruiken begrijpt, zoek vervolgens richtlijnen voor het instellen van elke methode in [detectiemethoden configureren voor System Center Configuration Manager](../../../../core/servers/deploy/configure/configure-discovery-methods.md).  
