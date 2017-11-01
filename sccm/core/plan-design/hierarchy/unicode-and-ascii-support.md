---
title: Unicode en ASCII-ondersteuning
titleSuffix: Configuration Manager
description: Meer informatie over ondersteuning voor Unicode en ASCII-tekens in System Center Configuration Manager-objecten.
ms.custom: na
ms.date: 3/1/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 2bdec799-905f-48bc-aed5-2d92134739e8
caps.latest.revision: "6"
caps.handback.revision: "0"
author: Brenduns
ms.author: brenduns
manager: angrobe
ms.openlocfilehash: 1314c0bc8de25c343b80f40de7d2a007024a17dd
ms.sourcegitcommit: c236214b2fcc13dae7bad96d7fb33f692868191d
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/12/2017
---
# <a name="unicode-and-ascii-support-in-system-center-configuration-manager"></a>Ondersteuning voor Unicode en ASCII in System Center Configuration Manager

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*

System Center Configuration Manager maakt de meeste objecten door Unicode-tekens. Echter verscheidene objecten ondersteunen alleen ASCII-tekens of hebben andere beperkingen.  

 De volgende secties worden de objecten die tekens bevatten uit de ASCII-tekenset alleen moet gebruiken, of die aanvullende beperkingen hebben.  

-   [Objecten die gebruikmaken van ASCII-tekens](#BKMK_ASCIIchar)  

-   [Aanvullende beperkingen](#BKMK_OtherCharLimitations)  

-   [Configuration Manager-objecten die niet zijn gelokaliseerd](#BKMK_LangNonLocalize)  

##  <a name="BKMK_ASCIIchar"></a>Objecten die gebruikmaken van ASCII-tekens  
 Configuration Manager ondersteunt de ASCII-tekenset alleen wanneer u de volgende objecten maakt:  

-   Sitecode  

-   Alle sitegegevens computernamen van siteserversystemen  

-   De volgende Configuration Manager-accounts:  

    > [!NOTE]  
    >  Deze accounts ondersteunen ASCII-tekens en RUS-tekens op een site die wordt uitgevoerd in Russisch.  

    -   Clientpushinstallatie-account  

    -   Status publicatieaccount Health  

    -   Opvraagaccount Health-statusreferentie  

    -   Beheerpunt-databaseverbindingsaccount  

    -   Netwerktoegangsaccount  

    -   Pakkettoegangsaccount  

    -   Standaardafzenderaccount  

    -   Installatieaccount sitesysteem  

    -   Verbindingsaccount software-updatepunt  

    -   Proxyserveraccount voor software-update-punt  

    > [!NOTE]  
    >  De accounts die u voor op rollen gebaseerd beheer opgeeft ondersteunen Unicode.  
    >   
    >  Reporting Services-punt account ondersteunt Unicode, met uitzondering van RUS-tekens.  

-   Volledig gekwalificeerde domeinnaam (FQDN) voor siteservers en sitesystemen  

-   Installatiepad voor Configuration Manager  

-   Namen van SQL Server-exemplaar  

-   Het pad voor de volgende sitesysteemrollen:  

    -   Application Catalog-webservicepunt  

    -   Application Catalog-websitepunt  

    -   Inschrijvingspunt  

    -   Proxypunt voor inschrijving  

    -   Reporting Services-punt  

    -   Statusmigratiepunt  

-   Het pad voor de volgende mappen:  

    -   De map waarop migratiegegevens van de status van de opgeslagen  

    -   De map waarin de Configuration Manager-rapporten  

    -   De map waarin de Configuration Manager back-up wordt opgeslagen  

    -   De map waarin de installatiebronbestanden voor de installatie van de site wordt opgeslagen  

    -   De map met de vereiste downloads voor gebruik door setup  

-   Het pad voor de volgende objecten:  

    -   IIS-website  

    -   Installatiepad van virtuele toepassing  

    -   De naam van de virtuele toepassing  

-   De volgende objecten voor AMT- en out-of-band beheer:  

    -   De FQDN-naam van de AMT-gebaseerde computer  

    -   De naam van de AMT-gebaseerde computer  

    -   De NetBIOS-domeinnaam  

    -   De naam van het draadloze profiel en SSID  

    -   Naam van de vertrouwde basis-CA  

    -   De naam van de certificeringsinstantie (CA) en sjabloonnamen  

    -   De bestandsnaam en het pad voor het installatiekopiebestand voor IDE-omleiding  

    -   De inhoud van de AMT-gegevensopslag  

-   ISO-bestandsnamen voor opstartmedia  

##  <a name="BKMK_OtherCharLimitations"></a>Aanvullende beperkingen  
 Hieronder vindt aanvullende beperkingen voor ondersteunde tekensets en taalversies beschreven:  

-   Configuration Manager biedt geen ondersteuning voor het wijzigen van de landinstellingen van de siteservercomputer.  

-   Een enterprise-certificeringsinstantie (CA) biedt geen ondersteuning voor namen van clientcomputers die gebruikmaken van DBCS-tekensets (DBCS). De namen van clientcomputers die u kunt gebruiken, worden beperkt door de PKI-beperking van de IA5-tekenset. Configuration Manager biedt bovendien geen ondersteuning CA-namen waarden of onderwerpnamen die gebruikmaken van tekensets met dubbele BYTES.  

##  <a name="BKMK_LangNonLocalize"></a>Configuration Manager-objecten die niet zijn gelokaliseerd  
 De Configuration Manager-database ondersteunt Unicode voor de meeste objecten die hierin worden opgeslagen en indien mogelijk wordt er informatie weergegeven in de besturingssysteemtaal die overeenkomt met de landinstellingen van de computer. De landinstellingen van de computer moet overeenkomen met een client- of servertaal die u op een site installeert voor de clientinterface of Configuration Manager-console informatie weergeven in de besturingssysteemtaal van de computer.  

 Echter verschillende Configuration Manager-objecten ondersteunen geen Unicode, en ze worden opgeslagen in de database op basis van ASCII of er gelden aanvullende taalbeperkingen. Deze informatie wordt altijd weergegeven met behulp van de ASCII-tekenset of in de taal die werd gebruikt toen het object is gemaakt.  
