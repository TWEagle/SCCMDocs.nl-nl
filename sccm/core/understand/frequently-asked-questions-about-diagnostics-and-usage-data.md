---
title: Diagnostische gegevens en gebruiksgegevens Veelgestelde vragen
titleSuffix: Configuration Manager
description: Veelgestelde vragen over diagnostische gegevens en gebruiksgegevens voor System Center Configuration Manager vinden.
ms.custom: na
ms.date: 04/10/2018
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 3fe32aa2-d594-4ad0-a291-b8f5395ac50b
caps.latest.revision: 6
author: aczechowski
ms.author: aaroncz
manager: dougeby
ms.openlocfilehash: 5a8a34e14d0e4f187e520faf9b2e520945087097
ms.sourcegitcommit: fb84bcb31d825f454785e3d9d8be669e00fe2b27
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/16/2018
---
# <a name="frequently-asked-questions-about-diagnostics-and-usage-data-for-system-center-configuration-manager"></a>Veelgestelde vragen over diagnostische gegevens en gebruiksgegevens voor System Center Configuration Manager

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*

In dit artikel vindt u antwoorden op veelgestelde vragen over diagnostische gegevens en gebruiksgegevens in Configuration Manager.

## <a name="faqs"></a>Veelgestelde vragen

###  <a name="bkmk_off"></a> Hoe kan ik telemetrie uitschakelen?  
Telemetrie kan niet worden uitgeschakeld. U kunt echter het niveau van telemetriegegevens die worden verzameld. Om te beheren wanneer telemetriegegevens wordt ingediend, het service connection point in offlinemodus te gebruiken.

De huidige vertakking van Configuration Manager moet worden bijgewerkt op regelmatige basis voor de ondersteuning van nieuwe versies van Windows 10 en Microsoft Intune. Microsoft vereist ten minste het niveau basis voor diagnostische gegevens en gebruiksgegevens. Deze gegevens wordt gebruikt voor het product up-to-date te houden, de update-ervaring te verbeteren en de kwaliteit en beveiliging van het product te verbeteren.

###  <a name="bkmk_retention"></a> Wat is de bewaartermijn voor gegevens?  
 Diagnostische en gebruiksgegevens gegevens worden opgeslagen voor één jaar.  

###  <a name="bkmk_update"></a> Worden er diagnostische gegevens en gebruiksgegevens verzonden bij het installeren of bijwerken van het product?  
 Nee. Diagnostische gegevens en gebruiksgegevens worden alleen verzonden nadat de site is geïnstalleerd en operationeel is geworden.  

###  <a name="bkmk_frequency"></a> Hoe vaak worden de gegevens verzonden?  
 De SQL opgeslagen procedures elke zeven dagen vanaf de datum die de site is geïnstalleerd. Het serviceaansluitpunt is in onlinemodus geconfigureerd voor het uploaden van de gegevens nadat de query's worden uitgevoerd. In de offlinemodus gebruikt de beheerder het Service Connection-hulpprogramma om de gegevens te uploaden. (De gegevens is niet beschikbaar voor offlinegebruik tot zeven dagen nadat de site is geïnstalleerd.)  

###  <a name="bkmk_network"></a> Kunnen de gegevens worden gebruikt om een netwerkoverzicht te maken?  
 Zoals u in de beschrijving van de niveaus van diagnostische gegevens en gebruiksgegevens, bevatten de sitegegevens informatie over de tijdzone van elke site. Deze informatie kan inzicht bieden in de brede geolocatie en globale spreiding van de sites in een hiërarchie. Deze gegevens bevatten niet netwerkdetails, zoals IP-adressen of meer gedetailleerde geografische gegevens. Zie voor meer informatie, de lijst met [diagnostische gegevens en gebruiksgegevens gegevens artikelen](/sccm/core/plan-design/diagnostics/diagnostics-and-usage-data#articles), en zoek de niveaus diagnostische en gebruiksgegevens verzamelen van gegevens voor de versie die u gebruikt.


###  <a name="bkmk_tables"></a> Kunt u gegevens in aangepaste tabellen zien?  
 Nee. Configuration Manager verzamelt diagnostische gegevens en gebruiksgegevens via SQL opgeslagen procedures. Deze opgeslagen procedures tegen standaard producttabellen in de database worden uitgevoerd. Alle deze SQL-tabellen worden voorafgegaan door **TEL_**. Als onderdeel van de query met betrekking tot SQL-schemadetectie worden alle tabelnamen gehasht ter vergelijking met de bekende standaardinstellingen. Dit gedrag bepaalt dat aangepaste tabellen in de database voorkomt. De aanwezigheid van aangepaste tabellen informeert dat het databaseschema is uitgebreid dan de standaardcontext. Het bevatten niet de gegevens die zijn opgeslagen in deze tabellen.  

###  <a name="bkmk_databases"></a> Ziet u de namen van andere databases of kunt u de gegevens in andere databases zien? 
 Nee. De opgeslagen procedures voor het verzamelen van gegevens zijn beperkt tot de sitedatabase.  

### <a name="bkmk_gdpr"></a> Configuration Manager onderworpen aan de algemene gegevens beveiliging regelgeving (GDPR) is?
 Nee. Configuration Manager niet is onderworpen aan GDPR toezicht. Het is een lokaal product die u rechtstreeks implementeren, beheren en gebruiken. De diagnostische gegevens en gebruiksgegevens gegevens die Microsoft verzamelt verbetert de installatie-ervaring, kwaliteit en beveiliging van toekomstige releases. Deze gegevens zijn onderworpen aan GDPR toezicht. Er is geen identificatie-informatie voor de eindgebruiker (EUII) of door eindgebruikers pseudoniem-id's (EUPI) worden verzameld en naar Microsoft verzonden. Zie voor meer informatie over GDPR de [Microsoft Trust Center op GDPR](https://microsoft.com/gdpr). Zie voor meer informatie over Configuration Manager-gegevens, [diagnostische gegevens en gebruiksgegevens](/sccm/core/plan-design/diagnostics/diagnostics-and-usage-data).


## <a name="see-also"></a>Zie tevens  
 [Diagnostische gegevens en gebruiksgegevens](/sccm/core/plan-design/diagnostics/diagnostics-and-usage-data)
