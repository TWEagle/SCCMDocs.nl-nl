---
title: Hardware-inventaris beveiliging privacy | Microsoft Docs
description: Beveiliging en privacy-informatie ophalen voor hardware-inventaris in System Center Configuration Manager.
ms.custom: na
ms.date: 2/22/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 62e20d86-db6d-4a1f-b14a-905a9de31698
caps.latest.revision: "6"
author: andredm7
ms.author: andredm
manager: angrobe
ms.openlocfilehash: ec182ec3102e0f4ae8bcf3d1ef843b25510b6ce6
ms.sourcegitcommit: 51fc48fb023f1e8d995c6c4eacfda7dbec4d0b2f
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 08/07/2017
---
# <a name="security-and-privacy-for-hardware-inventory-in-system-center-configuration-manager"></a>Beveiliging en privacy voor hardware-inventarisatie in System Center Configuration Manager

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*

Dit onderwerp bevat beveiligings- en privacy-informatie voor hardware-inventarisatie in System Center Configuration Manager.  

##  <a name="BKMK_Security_HardwareInventory"></a> Aanbevolen beveiligingsprocedures voor hardware-inventarisatie  
 Gebruik de volgende aanbevolen beveiligingsprocedures wanneer u hardware-inventarisgegevens bij clients verzamelt:  

|Aanbevolen beveiligingsprocedure|Meer informatie|  
|----------------------------|----------------------|  
|Inventarisgegevens ondertekenen en versleutelen|Wanneer clients via HTTPS communiceren met beheerpunten, worden alle gegevens die ze verzenden met behulp van SSL versleuteld. Wanneer clientcomputers echter op het intranet via HTTP met beheerpunten communiceren, kunnen clientinventarisgegevens en verzamelde bestanden niet-ondertekend en niet-versleuteld worden verzonden. Zorg ervoor dat de site zodanig is geconfigureerd dat ondertekening is vereist en versleuteling wordt gebruikt. Bovendien, als clients het SHA-256-algoritme kunnen ondersteunen, selecteert u de optie die SHA-256 vereist.|  
|Verzamel geen IDMIF- en NOIDMIF-bestanden in sterk beveiligde omgevingen|U kunt verzamelen van IDMIF- en NOIDMIF-bestanden gebruiken om het verzamelen voor hardware-inventarisatie uit te breiden. Indien nodig, wordt Configuration Manager nieuwe tabellen gemaakt of bestaande tabellen gewijzigd in de Configuration Manager-database om de eigenschappen in IDMIF- en NOIDMIF-bestanden te ondersteunen. Echter, Configuration Manager valideert niet IDMIF- en NOIDMIF-bestanden, zodat deze bestanden kunnen worden gebruikt voor het wijzigen van tabellen die u niet wilt gewijzigd. Geldige gegevens kunnen worden overschreven door ongeldige gegevens. Bovendien kunnen grote hoeveelheden gegevens worden toegevoegd en de verwerking van deze gegevens vertragingen veroorzaken bij alle Configuration Manager-functies. Configureer de clientinstelling voor hardware-inventarisatie **MIF-bestanden verzamelen** als **Geen**om deze risico's te beperken.|  

### <a name="security-issues-for-hardware-inventory"></a>Beveiligingsproblemen voor hardware-inventarisatie  
 Bij het verzamelen van inventarisatiegegevens komen potentiële beveiligingslekken naar voren. Kwaadwillende personen kunnen het volgende doen:  

-   Ongeldige gegevens verzenden, die door het beheerpunt worden geaccepteerd, zelfs wanneer de clientinstelling voor software-inventaris is uitgeschakeld en bestandsverzameling niet is ingeschakeld.  

-   Uitzonderlijk grote hoeveelheden gegevens verzenden in een enkel bestand en in heel veel bestanden, wat kan leiden tot een denial-of-service.  

-   Toegang krijgen tot inventarisgegevens wanneer deze worden overgedragen naar Configuration Manager.  

 Omdat een gebruiker met lokale beheerdersbevoegdheden geen informatie als inventarisgegevens verzenden kan, dient u niet inventarisgegevens die worden verzameld door Configuration Manager niet als gezaghebbend.  

 Hardware-inventarisatie is standaard ingeschakeld als een clientinstelling.  

##  <a name="BKMK_Privacy_HardwareInventory"></a> Privacy-informatie voor hardware-inventarisatie  
 Hardware-inventarisatie kunt u alle informatie die is opgeslagen in het register en in WMI op de Configuration Manager-clients op te halen. Met een software-inventarisatie kunt u alle bestanden van een bepaald type ontdekken of alle bestanden van een bepaald type bij clients verzamelen. Asset Intelligence verbetert de inventarisatiefuncties door hardware- en software-inventarisatie uit te breiden en nieuwe licentiebeheerfunctionaliteit toe te voegen.  

 Hardware-inventarisatie is standaard ingeschakeld als een clientinstelling en welke WMI-gegevens worden verzameld, wordt bepaald door de opties die u selecteert. Software-inventarisatie is standaard ingeschakeld, maar er worden standaard geen bestanden verzameld. Asset Intelligence-gegevensverzameling is automatisch ingeschakeld, maar u kunt selecteren welke hardware-inventarisrapportageklassen u wilt inschakelen.  

 Er wordt geen inventarisinformatie naar Microsoft verzonden. Inventarisatie-informatie wordt opgeslagen in de Configuration Manager-database. Wanneer clients HTTPS gebruiken om verbinding te maken met beheerpunten, worden de inventarisatiegegevens die ze naar de site verzenden tijdens de overdracht versleuteld. Als clients HTTP gebruiken om verbinding te maken met beheerpunten, hebt u de mogelijkheid versleuteling voor het inventarisatieproces in te schakelen. De inventarisatiegegevens worden niet in een versleutelde indeling in de database opgeslagen. Informatie wordt bewaard in de database tot deze om de 90 dagen wordt verwijderd door de siteonderhoudstaak **Verouderde inventarisgeschiedenis verwijderen** of **Verouderde verzamelde bestanden verwijderen** . U kunt het verwijderingsinterval configureren.  

 Bedenk wat uw privacyvereisten zijn voordat u hardware-inventarisatie, software-inventarisatie, het verzamelen van bestanden of het verzamelen van Asset Intelligence-gegevens configureert.  
