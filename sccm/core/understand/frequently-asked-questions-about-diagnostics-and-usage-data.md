---
title: Diagnostische gegevens Veelgestelde vragen | Microsoft Docs
description: Veelgestelde vragen over diagnostische gegevens en gebruiksgegevens voor System Center Configuration Manager vinden.
ms.custom: na
ms.date: 2/8/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 3fe32aa2-d594-4ad0-a291-b8f5395ac50b
caps.latest.revision: "6"
author: Brenduns
ms.author: brenduns
manager: angrobe
ms.openlocfilehash: 177a30a30f6b8579fa1956d28581d4f9d3a11838
ms.sourcegitcommit: 51fc48fb023f1e8d995c6c4eacfda7dbec4d0b2f
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 08/07/2017
---
# <a name="frequently-asked-questions-about-diagnostics-and-usage-data-for-system-center-configuration-manager"></a>Veelgestelde vragen over diagnostische gegevens en gebruiksgegevens voor System Center Configuration Manager

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*

Hieronder volgen Veelgestelde vragen over diagnostische gegevens en gebruiksgegevens voor System Center Configuration Manager:  

###  <a name="bkmk_off"></a> Hoe kan ik telemetrie uitschakelen?  
Telemetrie kan niet worden uitgeschakeld. U kunt echter het niveau van telemetriegegevens die worden verzameld. U kunt ook een service connection point in de offlinemodus gebruiken om te beheren wanneer telemetriegegevens wordt ingediend.

De huidige vertakking van Configuration Manager moet worden bijgewerkt op regelmatige basis voor de ondersteuning van nieuwe versies van Windows 10 en Microsoft Intune. Microsoft vereist ten minste het niveau basis voor diagnostische en gebruiksgegevens het product up-to-date te houden, de update-ervaring te verbeteren, en de kwaliteit en beveiliging van het product te verbeteren.

###  <a name="bkmk_retention"></a> Wat is de bewaartermijn voor gegevens?  
 Diagnostische gegevens en gebruiksgegevens worden een jaar bewaard.  

###  <a name="bkmk_update"></a> Worden er diagnostische gegevens en gebruiksgegevens verzonden bij het installeren of bijwerken van het product?  
 Nee. Diagnostische gegevens en gebruiksgegevens worden alleen verzonden nadat de site is geïnstalleerd en operationeel is geworden.  

###  <a name="bkmk_frequency"></a> Hoe vaak worden de gegevens verzonden?  
 De SQL opgeslagen procedures elke zeven dagen (vanaf de datum waarop de site is geïnstalleerd). Het serviceaansluitpunt is in onlinemodus geconfigureerd voor het uploaden van de gegevens nadat de query's worden uitgevoerd. In de offlinemodus gebruikt de beheerder het Service Connection-hulpprogramma om de gegevens te uploaden. (Houd er rekening mee dat de gegevens niet beschikbaar voor offlinegebruik tot zeven dagen zijn nadat de site is geïnstalleerd.)  

###  <a name="bkmk_network"></a> Kunnen de gegevens worden gebruikt om een netwerkoverzicht te maken?  
 Zoals u in de beschrijving van de niveaus van gegevensverzameling van diagnostische gebruiksgegevens voor System Center Configuration Manager, bevatten de sitegegevens informatie over de tijdzone van elke site. Deze informatie kan inzicht bieden in de brede geolocatie en globale spreiding van de sites in een hiërarchie. Echter geen netwerkgegevens verzameld, (zoals IP-adressen of meer gedetailleerde geografische informatie).
 - [Diagnostische gegevens voor 1511](/sccm/core/plan-design/diagnostics/levels-of-diagnostic-usage-data-collection-1511)
 - [Diagnostische gegevens voor 1602](/sccm/core/plan-design/diagnostics/levels-of-diagnostic-usage-data-collection-1602)
 - [Diagnostische gegevens voor 1606](/sccm/core/plan-design/diagnostics/levels-of-diagnostic-usage-data-collection-1606)
 - [Diagnostische gegevens voor 1610](/sccm/core/plan-design/diagnostics/levels-of-diagnostic-usage-data-collection-1610)


###  <a name="bkmk_tables"></a> Kunt u gegevens in aangepaste tabellen zien?  
 Nee. Diagnostische gegevens en gebruiksgegevens worden verzameld via in SQL opgeslagen procedures tegen standaard producttabellen in de database (die worden voorafgegaan door **TEL_** ). Als onderdeel van de query met betrekking tot SQL-schemadetectie worden alle tabelnamen gehasht ter vergelijking met de bekende standaardinstellingen. Dit kunt vaststellen dat er aangepaste tabellen gedefinieerd in de database (die het databaseschema is uitgebreid van de standaardwaarde), maar niet een van de gegevens in deze tabellen.  

###  <a name="bkmk_databases"></a>Ziet u de namen van andere databases of kunt u de gegevens in andere databases zien?  
 Nee. De opgeslagen procedures voor het verzamelen van gegevens zijn beperkt tot de sitedatabase.  

## <a name="see-also"></a>Zie tevens  
 [Diagnostische gegevens en gebruiksgegevens voor System Center Configuration Manager](../../core/plan-design/diagnostics/diagnostics-and-usage-data.md)
