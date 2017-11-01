---
title: Software-inventaris beveiliging privacy
titleSuffix: Configuration Manager
description: Beveiliging en privacy-informatie ophalen voor software-inventaris in System Center Configuration Manager.
ms.custom: na
ms.date: 2/22/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 8e68e1fb-a8ec-4543-bb8a-cbbaf184a418
caps.latest.revision: "5"
caps.handback.revision: "0"
author: andredm7
ms.author: andredm
manager: angrobe
ms.openlocfilehash: 6e784bc131b9006ba441c1fc32d67469e01bacad
ms.sourcegitcommit: c236214b2fcc13dae7bad96d7fb33f692868191d
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/12/2017
---
# <a name="security-and-privacy-for-software-inventory-in-system-center-configuration-manager"></a>Beveiliging en privacy voor software-inventaris in System Center Configuration Manager

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*

Dit onderwerp bevat beveiligings- en privacy-informatie voor software-inventaris in System Center Configuration Manager.  

##  <a name="BKMK_Security_HardwareInventory"></a> Aanbevolen beveiligingsprocedures voor software-inventaris  
 Gebruik de volgende aanbevolen beveiligingsprocedures voor wanneer u software-inventarisgegevens bij clients verzamelt:  

|Aanbevolen beveiligingsprocedure|Meer informatie|  
|----------------------------|----------------------|  
|Inventarisgegevens ondertekenen en versleutelen|Wanneer clients via HTTPS communiceren met beheerpunten, worden alle gegevens die ze verzenden met behulp van SSL versleuteld. Wanneer clientcomputers echter op het intranet via HTTP met beheerpunten communiceren, kunnen clientinventarisgegevens en verzamelde bestanden niet-ondertekend en niet-versleuteld worden verzonden. Zorg ervoor dat de site zodanig is geconfigureerd dat ondertekening is vereist en versleuteling wordt gebruikt. Bovendien, als clients het SHA-256-algoritme kunnen ondersteunen, selecteer dan de optie die SHA-256 vereist.|  
|Gebruik bestandsverzameling niet om essentiële bestanden of gevoelige gegevens te verzamelen|Configuration Manager software-inventaris gebruikt alle rechten van het lokale systeemaccount, dat de mogelijkheid voor het verzamelen van kopieën van essentiële systeembestanden, zoals het register of de beveiligingsaccountdatabase heeft. Wanneer deze bestanden beschikbaar zijn op de siteserver, kan iemand met het recht Bron lezen of het recht NTFS op de opgeslagen locatie de inhoud analyseren en mogelijk belangrijke informatie achterhalen over de client om vervolgens de beveiliging ervan in gevaar te brengen.|  
|Beperk lokale beheerrechten op clientcomputers|Een gebruiker met lokale beheerdersrechten kan ongeldige gegevens als inventarisatie-informatie verzenden.|  

### <a name="security-issues-for-software-inventory"></a>Beveiligingsproblemen voor software-inventaris  
 Bij het verzamelen van inventaris komen potentiële beveiligingslekken naar voren. Kwaadwillende personen kunnen het volgende doen:  

-   Ongeldige gegevens verzenden, die door het beheerpunt worden geaccepteerd, zelfs wanneer de clientinstelling voor software-inventaris is uitgeschakeld en bestandsverzameling niet is ingeschakeld.  

-   Uitzonderlijk grote hoeveelheden gegevens verzenden in een enkel bestand en in heel veel bestanden, wat kan leiden tot een denial-of-service.  

-   Toegang krijgen tot inventarisgegevens wanneer deze worden overgedragen naar Configuration Manager.  

 Als gebruikers weten dat ze een verborgen bestand kunnen maken met de naam **Skpswi.dat** en dit in de hoofdmap op de harde schijf van een client kunnen plaatsen om dit uit te sluiten van software-inventaris, kunt u geen software-inventarisatiegegevens bij die computer verzamelen.  

 Omdat een gebruiker met lokale beheerdersbevoegdheden geen informatie als inventarisgegevens verzenden kan, dient u niet inventarisgegevens die worden verzameld door Configuration Manager niet als gezaghebbend.  

 Software-inventarisatie is standaard ingeschakeld als een clientinstelling.  

##  <a name="BKMK_Privacy_HardwareInventory"></a> Privacy-informatie voor software-inventarisatie  
 Hardware-inventarisatie kunt u alle informatie die is opgeslagen in het register en in WMI op de Configuration Manager-clients op te halen. Met een software-inventarisatie kunt u alle bestanden van een bepaald type ontdekken of alle bestanden van een bepaald type bij clients verzamelen. Asset Intelligence verbetert de inventarisatiefuncties door hardware- en software-inventarisatie uit te breiden en nieuwe licentiebeheerfunctionaliteit toe te voegen.  

 Hardware-inventarisatie is standaard ingeschakeld als een clientinstelling en welke WMI-gegevens worden verzameld, wordt bepaald door de opties die u selecteert. Software-inventarisatie is standaard ingeschakeld, maar er worden standaard geen bestanden verzameld. Asset Intelligence-gegevensverzameling is automatisch ingeschakeld, maar u kunt selecteren welke hardware-inventarisrapportageklassen u wilt inschakelen.  

 Er wordt geen inventarisinformatie naar Microsoft verzonden. Inventarisatie-informatie wordt opgeslagen in de Configuration Manager-database. Wanneer clients HTTPS gebruiken om verbinding te maken met beheerpunten, worden de inventarisatiegegevens die ze naar de site verzenden tijdens de overdracht versleuteld. Als clients HTTP gebruiken om verbinding te maken met beheerpunten, hebt u de mogelijkheid versleuteling voor het inventarisatieproces in te schakelen. De inventarisatiegegevens worden niet in een versleutelde indeling in de database opgeslagen. Informatie wordt bewaard in de database tot deze om de 90 dagen wordt verwijderd door de siteonderhoudstaak **Verouderde inventarisgeschiedenis verwijderen** of **Verouderde verzamelde bestanden verwijderen** . U kunt het verwijderingsinterval configureren.  

 Bedenk wat uw privacyvereisten zijn voordat u hardware-inventarisatie, software-inventarisatie, het verzamelen van bestanden of het verzamelen van Asset Intelligence-gegevens configureert.  
