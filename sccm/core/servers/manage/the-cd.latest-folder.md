---
title: De map CD.Latest
titleSuffix: Configuration Manager
description: Meer informatie over de nieuwe updateproces dat het product via de Configuration Manager-console updates levert.
ms.custom: na
ms.date: 03/28/2018
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 8db92d67-5d9c-4e9c-80d0-ae6fa0dd4817
caps.latest.revision: ''
author: mestew
ms.author: mstewart
manager: dougeby
ms.openlocfilehash: 86b6393a6719895357d34fe8e562f3d0c967ad06
ms.sourcegitcommit: 27da4be015f1496b7b89ebddb517a2685f1ecf74
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 03/28/2018
---
# <a name="the-cdlatest-folder-for-system-center-configuration-manager"></a>De map CD.Latest voor System Center Configuration Manager

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*

System Center Configuration Manager introduceert een nieuwe updateproces waarmee updates aan het product via de Configuration Manager-console levert. Ter ondersteuning van deze nieuwe methode voor het bijwerken van Configuration Manager, een nieuwe map gemaakt met de naam **CD. Meest recente** die een kopie van de Configuration Manager-installatiebestanden voor de bijgewerkte versie van uw site bevat.  

De CD. Meest recente map bevat een map met de naam **Redist** waarin de herdistribueerbare bestanden die door setup downloadt en gebruikt. Deze bestanden zijn afgestemd op de versie van de Configuration Manager-bestanden die te vinden zijn in de map CD.Latest. Wanneer u Setup uitvoert vanuit de map CD.Latest, dient u de bestanden te gebruiken die zijn afgestemd op die versie van Setup. Hiervoor kunt u via Setup opdracht geven voor het downloaden van nieuwe en actuele bestanden van Microsoft, of u kunt de opdracht geven dat de bestanden uit de map Redist (die in de map CD.Latest staat) worden gebruikt.

Basislijnmedia, zoals echter de basislijnversie 1802 die in maart van 2018 uitgebracht, bevat geen een Redist-map. De map Redist wordt niet gemaakt totdat u een update in de console installeert. In de tussentijd de Redist-map die u hebt gebruikt bij het installeren van sites uit de basislijnmedia gebruiken.  

> [!TIP]
> Zorg ervoor dat de herdistribueerbare bestanden die u gebruikt actueel zijn. Als u onlangs niet herdistribueerbare bestanden hebt gedownload, kunt u plannen zodat de installatie om dit te doen van Microsoft.   

 Hieronder volgen scenario's voor het maken of bijwerken van de map CD.Latest op een centrale beheersite of primaire siteserver:  

-   U installeert een update of hotfix uit binnen de Configuration Manager-console: De map wordt gemaakt of bijgewerkt in de installatiemap van Configuration Manager.  

-   U uitvoeren de ingebouwde back-uptaak voor Configuration Manager: De map wordt gemaakt of bijgewerkt op de aangewezen back-upmap.  

-  De CD. Meest recente map wordt gemaakt wanneer u een nieuwe site met behulp van de basislijnmedia (zoals versie 1802) installeert.

De bronbestanden vanuit de map CD.Latest worden ondersteund voor het volgende:  

1.  **Back-up en herstel:** U kunt een site herstellen, moet u de bronbestanden vanaf een CD. Meest recente map die overeenkomt met uw site. Wanneer u een siteback-up met behulp van de ingebouwde back-uptaak van de site, de CD uitvoeren. Meest recente map is opgenomen als onderdeel van de back-up.

    -   **Wanneer u een site opnieuw installeert als onderdeel van een siteherstel** , installeert u de site vanuit de map CD.Latest in uw back-up. Hiermee wordt de site geïnstalleerd met de bestandsversies die overeenkomen met uw siteback-up en sitedatabase.  Als u geen hebt toegang tot de juiste CD. Meest recente versie van de map, kunt u een CD. Meest recente map met de juiste versies door een site in een testomgeving installeren en vervolgens bij te werken zodat deze overeenkomen met de versie van die site die u wilt herstellen.

        > [!IMPORTANT]  
        >  Als u niet over de juiste map CD.Latest en de bijbehorende inhoud beschikt, kunt u de site niet herstellen en moet deze opnieuw worden geïnstalleerd.  

    -   Wanneer u niet over een CD.Latest beschikt, maar wel een werkende onderliggende primaire site of centrale beheersite hebt, kunt u die site kunt gebruiken als referentiesite voor een siteherstel.  

2.  **Een onderliggende primaire site installeren:** Als u installeren, een nieuwe onderliggende primaire site onder een centrale beheersite met een of meer console-updates zijn geïnstalleerd wilt, moet u Setup en de bronbestanden vanaf de CD. Meest recente map uit de centrale beheersite. Wanneer Setup wordt uitgevoerd vanuit een kopie van de map CD.Latest vanaf de centrale beheersite, worden hiervoor de bronbestanden voor installatie gebruikt die overeenkomen met de versie van de centrale beheersite. Zie [Use the Setup Wizard to install System Center Configuration Manager-sites](../../../core/servers/deploy/install/use-the-setup-wizard-to-install-sites.md) (De wizard Setup gebruiken om System Center Configuration Manager-sites te installeren) voor meer informatie.  

3.  **Een zelfstandige primaire site uitbreiden:** Wanneer u een zelfstandige primaire site uitbreidt door een nieuwe centrale beheersite installeert, moet u Setup en de bronbestanden vanaf de CD. Meest recente map van de primaire site voor het installeren van de nieuwe centrale beheersite. Wanneer een installatie wordt uitgevoerd vanuit een kopie van de map CD.Latest vanaf de primaire site, worden de bronbestanden voor installatie gebruikt die overeenkomen met de versie van de primaire site. Zie [Expand a stand-alone primary site](../../../core/servers/deploy/install/use-the-setup-wizard-to-install-sites.md#bkmk_expand) (Een zelfstandige primaire site uitbreiden) in het onderwerp [Use the Setup Wizard to install System Center Configuration Manager-sites](../../../core/servers/deploy/install/use-the-setup-wizard-to-install-sites.md) (De wizard Setup gebruiken om System Center Configuration Manager-sites te installeren) voor meer informatie.

> [!IMPORTANT]  
>  De bronbestanden in de bijgewerkte map CD.Latest worden niet ondersteund voor:  
>   
>  -   Installatie van een nieuwe site voor een nieuwe hiërarchie  
>  -   Een Microsoft System Center 2012 Configuration Manager-site upgraden naar System Center Configuration Manager
>  -   Configuration Manager-client installeren
>  -   Beheerconsole Configuration Manager installeren

