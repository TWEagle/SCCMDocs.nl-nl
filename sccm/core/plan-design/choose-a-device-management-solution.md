---
title: Kies een oplossing voor Apparaatbeheer - Configuration Manager | Microsoft Docs
description: Meer informatie over de oplossingen die System Center Configuration Manager biedt voor het beheren van pc's, servers en apparaten.
ms.custom: na
ms.date: 12/08/2016
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: configmgr-client
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 24633725-791a-4df7-8dce-2c24c1a19a03
caps.latest.revision: "14"
caps.handback.revision: "0"
author: arob98
ms.author: angrobe
manager: angrobe
ms.openlocfilehash: 9989ea1bf4cb74a6286ebae9de7614ed622de5b6
ms.sourcegitcommit: 51fc48fb023f1e8d995c6c4eacfda7dbec4d0b2f
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 08/07/2017
---
# <a name="choose-a-device-management-solution-for-system-center-configuration-manager"></a>Een oplossing voor apparaatbeheer kiezen voor System Center Configuration Manager

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*

System Center Configuration Manager (ook wel bekend als ConfgMgr of SCCM) biedt verschillende oplossingen voor het beheren van pc's, servers en apparaten. U kunt de oplossing die geschikt is voor u, op basis van de apparaatplatforms die u wilt beheren en de beheerfunctionaliteit die u nodig hebt.  


##  <a name="overview-of-device-management-solutions"></a>Overzicht van oplossingen voor Apparaatbeheer  
 In dit artikel bevat informatie over de vier oplossingen voor het beheer van apparaten: de Configuration Manager-clienttoepassing, on-premises Configuration Manager-infrastructuur, Microsoft Intune en Exchange. Het artikel wordt afgesloten met twee tabellen die de oplossingen voor beheer, gebaseerd op een vergelijken [ondersteunde platforms voor mobiele apparaten](#compare-device-management-solutions-based-on-supported-mobile-device-platforms), en een op basis van [beheerfunctionaliteit](#compare-mobile-device-management-solutions-based-on-management-functionality).


###  <a name="manage-devices-with-the-configuration-manager-client"></a>Apparaten beheren met Configuration Manager-client  

Deze optie, die de installatie van de Configuration Manager-clienttoepassing op de apparaten vereist, biedt de meeste functies voor het beheren van pc's, servers en andere apparaten in uw omgeving. Zie voor meer informatie [clientinstallatiemethoden in System Center Configuration Manager](/sccm/core/clients/deploy/plan/client-installation-methods).  

###  <a name="manage-devices-with-on-premises-configuration-manager-infrastructure"></a>Apparaten beheren met on-premises Configuration Manager-infrastructuur  

Deze optie worden de beheermogelijkheden voor apparaten is ingebouwd in de besturingssystemen van bepaalde apparaatplatforms gebruikt. Terwijl niet beperkter als de Clientgebaseerde beheermethode, biedt on-premises-beheer voor mobiele apparaten een minder strikte benadering van beheer met behulp van de lokale Configuration Manager-bronnen te bereiken en te beheren van apparaten. Houd er rekening mee dat deze optie wordt momenteel alleen ondersteund voor Windows 10-computers en Windows 10 Mobile-apparaten.  

Zie voor meer informatie [mobiele apparaten beheren met on-premises infrastructuur in System Center Configuration Manager](../../mdm/understand/manage-mobile-devices-with-on-premises-infrastructure.md).  

###  <a name="manage-devices-with-microsoft-intune-hybrid"></a>Apparaten beheren met Microsoft Intune (hybride)  

Deze optie maakt gebruik van Microsoft Intune inschrijven en beheren van apparaten, in plaats van lokale bronnen van Configuration Manager. Hoewel de apparaten worden beheerd door Intune, opent u de beheertaken in de Configuration Manager-console. Deze optie ondersteunt alle belangrijke besturingssystemen mobiele apparaten, waaronder Windows 10 Mobile, Windows Phone, iOS, Mac OS X en Android. Daarnaast kunt u met deze optie Windows 8.1- en Windows 10-computers in uw organisatie beheren.  

Zie [Hybride Mobile Device Management (MDM) met System Center Configuration Manager en Microsoft Intune](../../mdm/understand/hybrid-mobile-device-management.md) voor meer informatie.  

###  <a name="manage-devices-with-microsoft-exchange"></a>Apparaten beheren met Microsoft Exchange  

Deze optie wordt de Exchange Server-connector voor het verbinding maken met meerdere Exchange-servers naar Configuration Manager. Dit centraliseert het beheer van apparaten die verbinding met Exchange ActiveSync maken kunnen. U kunt Exchange functies voor mobiele apparaten, zoals het wissen van het externe apparaat en de instellingen voor meerdere Exchange-servers, vanuit de Configuration Manager-console configureren.  

Zie [Mobiele apparaten beheren met System Center Configuration Manager en Exchange](../../mdm/deploy-use/manage-mobile-devices-with-exchange-activesync.md) voor meer informatie.  

U kunt deze oplossingen voor Apparaatbeheer zelfstandig of in combinatie met elkaar. U kunt bijvoorbeeld de aanpak van clients gebaseerde beheer gebruiken voor het beheren van computers en servers in uw organisatie en Intune ook gebruiken om mobiele apparaten te beheren. Door combineren benaderingen op deze manier, kunt u al uw behoeften voor het beheer van apparaat uit de Configuration Manager-console uitgelegd.  

## <a name="compare-device-management-solutions-based-on-supported-mobile-device-platforms"></a>Oplossingen voor Apparaatbeheer op basis van de ondersteunde mobiele platforms vergelijken  

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
|Beveiliging van de public key infrastructure (PKI) tussen het mobiele apparaat en Configuration Manager (maakt gebruik van wederzijdse verificatie en SSL voor het versleutelen van gegevensoverdracht)|Ja|Ja|Ja||  
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
|In quarantaine plaatsen en blokkeren vanuit Exchange Server (en Configuration Manager)||||Ja|  
|Wissen op afstand| |Ja|Ja|Ja|  
