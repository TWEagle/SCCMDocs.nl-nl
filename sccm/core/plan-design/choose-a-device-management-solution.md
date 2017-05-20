---
title: Kies een oplossing voor Apparaatbeheer - Configuration Manager | Microsoft-documenten
description: Meer informatie over de oplossingen die System Center Configuration Manager biedt voor het beheer van pc&quot;s, servers en apparaten.
ms.custom: na
ms.date: 12/08/2016
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-client
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 24633725-791a-4df7-8dce-2c24c1a19a03
caps.latest.revision: 14
caps.handback.revision: 0
author: arob98
ms.author: angrobe
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 3eb48942c1259d2aa1b3c200fad73b39b11c0b8c
ms.openlocfilehash: 9989ea1bf4cb74a6286ebae9de7614ed622de5b6
ms.contentlocale: nl-nl
ms.lasthandoff: 05/17/2017


---
# <a name="choose-a-device-management-solution-for-system-center-configuration-manager"></a>Een oplossing voor apparaatbeheer kiezen voor System Center Configuration Manager

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*

System Center Configuration Manager (ook wel bekend als ConfgMgr of SCCM) biedt verschillende oplossingen voor het beheer van pc's, servers en apparaten. U kunt de oplossing die geschikt is voor u, op basis van de apparaatplatforms die u wilt beheren en de beheerfunctionaliteit die u moet kiezen.  


##  <a name="overview-of-device-management-solutions"></a>Overzicht van beheeroplossingen voor apparaten  
 Dit artikel bevat informatie over de vier beheeroplossingen voor apparaten: de Configuration Manager-clienttoepassing op de lokale Configuration Manager-infrastructuur, Microsoft Intune en Exchange. Het artikel wordt afgesloten met twee tabellen die de beheeroplossingen gebaseerd op een vergelijken [ondersteunde platformen voor mobiele apparaten](#compare-device-management-solutions-based-on-supported-mobile-device-platforms), en een op basis van [beheerfunctionaliteit](#compare-mobile-device-management-solutions-based-on-management-functionality).


###  <a name="manage-devices-with-the-configuration-manager-client"></a>Apparaten beheren met Configuration Manager-client  

Deze optie, die de installatie van de Configuration Manager-clienttoepassing op de apparaten vereist, biedt de meeste functies voor het beheer van pc's, servers en andere apparaten in uw omgeving. Zie voor meer informatie [installatiemethoden voor clients in System Center Configuration Manager](/sccm/core/clients/deploy/plan/client-installation-methods).  

###  <a name="manage-devices-with-on-premises-configuration-manager-infrastructure"></a>Apparaten beheren met Configuration Manager-infrastructuur op locatie  

Deze optie worden de beheermogelijkheden voor apparaat ingebouwd in de besturingssystemen van sommige apparaatplatforms gebruikt. Terwijl niet als complete als beheer op basis van een client, beheer van mobiele apparaten op het lokale voorziet in een lichte touch aanpak voor beheer met behulp van de lokale Configuration Manager bronnen bereiken en beheren van apparaten. Houd er rekening mee dat deze optie wordt momenteel alleen ondersteund voor Windows 10-computers en Windows 10 Mobile-apparaten.  

Zie voor meer informatie [mobiele apparaten beheren met on-premises infrastructuur in System Center Configuration Manager](../../mdm/understand/manage-mobile-devices-with-on-premises-infrastructure.md).  

###  <a name="manage-devices-with-microsoft-intune-hybrid"></a>Apparaten beheren met Microsoft Intune (hybride)  

Deze optie maakt gebruik van Microsoft Intune inschrijven en beheren van apparaten, in plaats van Configuration Manager lokale bronnen. Hoewel de apparaten worden beheerd door Intune, kunt u uw beheertaken in de Configuration Manager-console openen. Deze optie ondersteunt alle belangrijke mobiele apparaat-besturingssystemen, met inbegrip van Windows 10 Mobile, Windows Phone, iOS, Mac OS X- en Android. Daarnaast kunt u met deze optie Windows 8.1- en Windows 10-computers in uw organisatie beheren.  

Zie [Hybride Mobile Device Management (MDM) met System Center Configuration Manager en Microsoft Intune](../../mdm/understand/hybrid-mobile-device-management.md) voor meer informatie.  

###  <a name="manage-devices-with-microsoft-exchange"></a>Apparaten beheren met Microsoft Exchange  

Deze optie maakt gebruik van de Exchange Server-connector verbinding maken met meerdere Exchange-servers naar Configuration Manager. Dit zijn gecentraliseerd beheer van apparaten die verbinding met Exchange ActiveSync maken kunnen. Hier kunt u Exchange mobiele apparaten beheerfuncties, zoals het externe apparaat wissen en de controle van de instellingen voor meerdere Exchange-servers van de Configuration Manager-console.  

Zie [Mobiele apparaten beheren met System Center Configuration Manager en Exchange](../../mdm/deploy-use/manage-mobile-devices-with-exchange-activesync.md) voor meer informatie.  

U kunt deze beheeroplossingen apparaten zelf of in combinatie met elkaar. U kunt bijvoorbeeld de beheer op basis van een client-benadering gebruiken voor het beheren van computers en servers in uw organisatie en Intune ook gebruiken om mobiele apparaten te beheren. Door combineren benaderingen op deze manier, kunt u alle van de behoeften van uw apparaat beheer van de Configuration Manager-console bestrijkt.  

## <a name="compare-device-management-solutions-based-on-supported-mobile-device-platforms"></a>Vergelijken beheeroplossingen voor apparaten op basis van de ondersteunde mobiele apparaten  

|Platform|Met de Configuration Manager-client|Configuration Manager met Microsoft Intune (hybride)|Op\-premises beheer van mobiele apparaten|Configuration Manager met Exchange|  
|--------------|-------------------------------------------|-------------------------------------------------------------------|-------------------------------|-----------------------------------------|  
|Android||Ja||Ja|  
|iOS||Ja||Ja|  
|Mac OS X|Ja|||Ja|  
|UNIX/Linux|Ja|||Ja|  
|Windows 10|Ja|Ja|Ja|Ja|  
|Windows 10 Mobile||Ja|Ja|Ja|  
|Windows (vorige versies)|Ja|Ja||Ja|  
|Windows CE|Ja (met oudere client van mobiel apparaat)|||Ja|  
|Windows Embedded|Ja||||  
|Windows Phone||Ja||Ja|  
|Windows Server|Ja|||Ja|  

 Zie voor een volledige lijst met ondersteunde platforms [ondersteunde besturingssystemen voor clients en apparaten voor System Center Configuration Manager](configs\supported-operating-systems-for-clients-and-devices.md).

##  <a name="bkmk_comp2"></a> Oplossingen voor het beheren van mobiele apparaten vergelijken op basis van de beheerfunctionaliteit  

|Beheerfunctionaliteit|Met de Configuration Manager-client|Configuration Manager met Microsoft Intune (hybride)|Op\-premises beheer van mobiele apparaten|Configuration Manager met Exchange|  
|------------------------------|-------------------------------------------|-------------------------------------------------------------------|-------------------------------|-----------------------------------------|  
|Beveiliging van de openbare-sleutelinfrastructuur (PKI) tussen het mobiele apparaat en de Configuration Manager (maakt gebruik van wederzijdse verificatie en SSL voor het versleutelen van de gegevensoverdracht)|Ja|Ja|Ja||  
|Clientinstallatie|Ja||||  
|Ondersteuning via Internet|Ja||||  
|Detectie|Ja|||Ja|  
|Hardware-inventaris|Ja|Ja|Ja|Ja|  
|Software-inventaris|Ja|||Ja|  
|Instellingen|Ja|Ja|Ja|Ja|  
|Software-implementatie|Ja|Ja|Ja||  
|Bewaking met terugvalstatuspunt|Ja||||  
|Verbindingen met beheerpunten|Ja||Ja||  
|Verbindingen met distributiepunten|Ja||Ja||  
|Blok van Configuration Manager|Ja|Ja|Ja||  
|Quarantaine plaatsen en blokkeren vanuit Exchange Server (en Configuration Manager)||||Ja|  
|Wissen op afstand| |Ja|Ja|Ja|  

