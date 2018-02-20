---
title: Product Lifecycle-dashboard
titleSuffix: Configuration Manager
description: Informatie ophalen over de levenscyclus van dashboard in System Center Configuration Manager.
ms.custom: na
ms.date: 02/13/2018
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: get-started-article
ms.assetid: 8b5b144a-0e5f-4fcc-87b2-33b9bcdb5655
caps.latest.revision: 
caps.handback.revision: 
author: mestew
ms.author: mstewart
manager: dougeby
robots: noindex,nofollow
ms.openlocfilehash: cfc54c1beb92d0102897f77ce3c287cc0ef9e0f4
ms.sourcegitcommit: fbd4a9d2fa8ed4ddd3a0fecc4a2ec4fc0ccc3d0c
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 02/19/2018
---
# <a name="use-the-product-lifecycle-dashboard-to-manage-microsoft-lifecycle-policy-in-system-center-configuration-manager"></a>Gebruik het Dashboard van de levenscyclus Product voor het beheren van Microsoft Support Lifecycle-beleid in System Center Configuration Manager

Van toepassing op: System Center Configuration Manager (Technical Preview)*

Beginnen met [Technical Preview-versie 1802](/sccm/core/get-started/capabilities-in-technical-preview-1802), kunt u de levenscyclus van Configuration Manager-dashboard. Het dashboard toont de status van het Microsoft Product Lifecycle-beleid voor Microsoft-producten die zijn geïnstalleerd op apparaten die worden beheerd met Configuration Manager. Het dashboard biedt u informatie over Microsoft-producten in uw omgeving, dan staat en einddatum voor ondersteuning. U kunt het dashboard gebruiken om te begrijpen van de beschikbaarheid van ondersteuning voor elk product. Helpt u bij het plannen voor bij het bijwerken van de Microsoft-producten te gebruiken voordat hun huidige einde van ondersteuning is bereikt.  

Zie voor meer informatie over het levenscyclusbeleid van Microsoft Product [Microsoft Lifecycle Policy](https://support.microsoft.com/en-us/lifecycle).

## <a name="prerequisites"></a>Vereisten 

 Het volgende is vereist om gegevens te bekijken in het dashboard levenscyclus: 
- Internet Explorer 9 of hoger moet zijn geïnstalleerd op de computer waarop de Configuration Manager-console wordt uitgevoerd. 
- Een Reporting Services-punt is vereist voor de hyperlinkfunctionaliteit in het dashboard omdat ze aan een rapport SQL Server Reporting Services (SSRS koppelen). Zie [Rapportage in System Center Configuration Manager](/sccm/core/servers/manage/reporting) voor meer informatie. 
- De Asset Intelligence-synchronisatiepunt moet worden geconfigureerd en gesynchroniseerd. Zie voor meer informatie [Asset Intelligence configureren in System Center Configuration Manager](/sccm/core/clients/manage/asset-intelligence/configuring-asset-intelligence).

De gegevens in het dashboard is afhankelijk van het Asset Intelligence-synchronisatiepunt geïnstalleerd hebben. Het dashboard maakt gebruik van de Asset Intelligence-catalogus als metagegevens voor producttitels. De metagegevens wordt vergeleken met inventarisgegevens in uw hiërarchie. 

>[!NOTE]
>Als u het Asset Intelligence-servicepunt voor het eerst configureert, moet u [Asset Intelligence-hardware-inventarisklassen inschakelen](/sccm/core/clients/manage/asset-intelligence/configuring-asset-intelligence#BKMK_EnableAssetIntelligence). Het dashboard van de levenscyclus is afhankelijk van de Asset Intelligence-hardware-inventarisklassen en wordt niet weergave van gegevens tot clients hebt gescand op hardware-inventaris geretourneerd.  

## <a name="use-the-microsoft-product-lifecycle-dashboard"></a>Gebruik het dashboard van de levenscyclus van Microsoft-producten

Op basis van inventarisgegevens die u hebt verzameld van beheerde apparaten, het dashboard geeft informatie weer over alle huidige producten. De weergegeven informatie voor besturingssystemen en SQL Server is echter beperkt tot de volgende versies:

- WindowsServer 2008 en hoger
- Windows XP en hoger
- SQL Server 2008 en hoger

Voor toegang tot het dashboard van de levenscyclus in de Configuration Manager-console, gaat u naar **activa en naleving** > **Asset Intelligence** > **levenscyclus** .

>[!NOTE]
>De gegevens in het dashboard is gebaseerd op de site die de Configuration Manager-console verbinding maakt. Als de console verbinding met uw site bovenste laag maakt, ziet u de gegevens voor de gehele hiërarchie. Wanneer verbonden met een onderliggende primaire site, wordt alleen de gegevens van die site weergegeven.

### <a name="product-lifecycle-dashboard"></a>Product Lifecycle-dashboard

![Product Lifecycle-dashboard](/sccm/core/clients/manage/asset-intelligence/media/product-lifecycle-dashboard.png)

Het dashboard bevat de volgende tegels: 
- **Top vijf producten voorbij het einde van de levenscyclus:** Deze tegel is een geconsolideerde weergave van producten voorbij het einde van de levenscyclus gevonden in uw omgeving. De grafiek toont geïnstalleerde software die is verlopen wanneer vergeleken met de levenscyclus voor ondersteuning voor besturingssystemen en SQL server-producten.  
- **Top 5 producten bijna einde van de levenscyclus:** Deze tegel is een geconsolideerde weergave van producten die bijna zijn einde van de levenscyclus in de komende zes maanden gevonden in uw omgeving. De grafiek toont geïnstalleerde software die binnen zes maanden na het einde van de levenscyclus wanneer vergeleken met de levenscyclus voor ondersteuning voor besturingssystemen en SQL server-producten.
- **De levenscyclus van gegevens voor de geïnstalleerde producten:** Deze tegel biedt u een algemeen beeld van wanneer een product van overgangen ondersteund op de status verlopen. De grafiek bevat een verdeling van het aantal clients waarop het product is geïnstalleerd, de beschikbaarheidsstatus van ondersteuning, samen met een koppeling voor meer informatie over de volgende stappen te nemen. De volgende informatie is opgenomen in de grafiek:     
    - Ondersteuning voor resterende tijd
    - Aantal in de omgeving 
    - Gangbare einddatum voor ondersteuning
    - Einddatum voor uitgebreide ondersteuning
    - Volgende stappen 

>[!IMPORTANT]
>De informatie die wordt weergegeven in dit dashboard is opgegeven voor uw gemak en zijn alleen voor intern gebruik in uw bedrijf. U moet niet alleen afgaan op deze informatie om te controleren van naleving. Zorg ervoor dat de juistheid van de gegevens die wordt weergegeven, samen met de beschikbaarheid van gegevens via https://support.microsoft.com/en-us/lifecycle voor ondersteuning.

## <a name="reporting"></a>Rapporten
De volgende nieuwe rapporten zijn toegevoegd onder de categorie **levenscyclus**:
- **Overzicht van de levenscyclus van algemene:** Een lijst van de Product-levenscycli van weergeven. De lijst kan worden gefilterd op productnaam en dagen tot vervaldatum die door de gebruiker te definiëren. 
- **Computers met een specifieke software-product:** Bekijk een lijst met computers waarop een opgegeven product is gedetecteerd.
- **Lijst met verlopen producten gevonden in de organisatie:** Details weergeven voor producten in uw omgeving die verlopen lifecycle datums. 
- **Lijst met computers met verlopen producten in de organisatie:** Computers weergeven die producten op deze zijn verlopen. Dit rapport kunt u filteren op productnaam.

## <a name="next-steps"></a>Volgende stappen
Zie voor meer informatie over het installeren of bijwerken van de technical preview vertakking [Technical Preview voor System Center Configuration Manager](/sccm/core/get-started/technical-preview).  

