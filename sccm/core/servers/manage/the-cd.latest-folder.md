---
title: De CD. Meest recente map | Microsoft-documenten
description: Meer informatie over het nieuwe updateproces voor de die updates voor het product van de Configuration Manager-console biedt.
ms.custom: na
ms.date: 05/02/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 8db92d67-5d9c-4e9c-80d0-ae6fa0dd4817
caps.latest.revision: 6
author: Brenduns
ms.author: brenduns
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 90775fcf2549080a43e9c1606caa79d9eb90a89c
ms.openlocfilehash: 5c39e09b44500fa2f356f83579bb2fb2c1d0e937
ms.contentlocale: nl-nl
ms.lasthandoff: 05/17/2017


---
# <a name="the-cdlatest-folder-for-system-center-configuration-manager"></a>De map CD.Latest voor System Center Configuration Manager

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*

System Center Configuration Manager introduceert een nieuwe updateproces die updates voor het product van de Configuration Manager-console biedt. Ter ondersteuning van deze nieuwe methode voor het bijwerken van Configuration Manager, een nieuwe map wordt gemaakt met de naam **CD. Meest recente** die een kopie van de Configuration Manager-installatiebestanden voor de bijgewerkte versie van uw site bevat.  

Vanaf update 1606 bevat de map CD.Latest een map met de naam **Redist** die de herdistribueerbare bestanden bevat. Deze worden gedownload en gebruikt door Setup. Deze bestanden zijn afgestemd op de versie van de Configuration Manager-bestanden die te vinden zijn in de map CD.Latest. Wanneer u Setup uitvoert vanuit de map CD.Latest, dient u de bestanden te gebruiken die zijn afgestemd op die versie van Setup. Hiervoor kunt u via Setup opdracht geven voor het downloaden van nieuwe en actuele bestanden van Microsoft, of u kunt de opdracht geven dat de bestanden uit de map Redist (die in de map CD.Latest staat) worden gebruikt.

Basislijn media, zoals echter de basisversie 1606 die in oktober van 2016 uitgebracht, bevat geen een Redist-map. De map Redist zal niet worden gemaakt totdat u een update in de console installeert. In de tussentijd de Redist-map die u hebt gebruikt bij het installeren van sites uit de basislijn media gebruiken.  

> [!TIP]
> Als u versie 1606 nog niet hebt geïnstalleerd, controleert u of de redist-bestanden die u gebruikt, actueel zijn. Als u de redist-bestanden niet recentelijk hebt gedownload, stelt u Setup zodanig in dat ze van Microsoft worden gedownload.   

 Hieronder volgen scenario's voor het maken of bijwerken van de map CD.Latest op een centrale beheersite of primaire siteserver:  

-   U installeert een update of hotfix verwijderen van de Configuration Manager-console: De map wordt gemaakt of bijgewerkt in de Configuration Manager-installatiemap.  

-   U kunt de ingebouwde back-uptaak van Configuration Manager uitvoeren: De map wordt gemaakt of bijgewerkt op de aangewezen back-upmap locatie.  

-  Vanaf versie 1606, de CD. Meest recente map wordt gemaakt wanneer u een nieuwe site met behulp van basislijn media (zoals versie 1606 of 1702) installeren.

De bronbestanden vanuit de map CD.Latest worden ondersteund voor het volgende:  

1.  **Back-up en herstel:** Als u wilt herstellen op een site, moet u de bronbestanden vanaf een CD gebruiken. Meest recente map die overeenkomt met uw site. Wanneer u een back-up van site met behulp van de ingebouwde back-uptaak van de site, de CD uitvoeren. Meest recente map is opgenomen als onderdeel van de back-up.

    -   **Wanneer u een site opnieuw installeert als onderdeel van een siteherstel** , installeert u de site vanuit de map CD.Latest in uw back-up. Hiermee wordt de site geïnstalleerd met de bestandsversies die overeenkomen met uw siteback-up en sitedatabase.  Als u geen hebt toegang tot de juiste CD. Meest recente versie van de map, kunt u een CD. Meest recente map met de juiste versies door de installatie van een site in een testomgeving en vervolgens bij te werken die site zodat deze overeenkomen met de versie die u wilt herstellen.

        > [!IMPORTANT]  
        >  Als u niet over de juiste map CD.Latest en de bijbehorende inhoud beschikt, kunt u de site niet herstellen en moet deze opnieuw worden geïnstalleerd.  

    -   Wanneer u niet over een CD.Latest beschikt, maar wel een werkende onderliggende primaire site of centrale beheersite hebt, kunt u die site kunt gebruiken als referentiesite voor een siteherstel.  

2.  **Een onderliggende primaire site wilt installeren:** Als u installeren van een nieuwe onderliggende primaire site onder een centrale beheersite die een of meer console updates heeft geïnstalleerd wilt, moet u Setup en de bronbestanden vanaf de CD. Meest recente map vanaf de centrale beheersite. Wanneer Setup wordt uitgevoerd vanuit een kopie van de map CD.Latest vanaf de centrale beheersite, worden hiervoor de bronbestanden voor installatie gebruikt die overeenkomen met de versie van de centrale beheersite. Zie [Use the Setup Wizard to install System Center Configuration Manager-sites](../../../core/servers/deploy/install/use-the-setup-wizard-to-install-sites.md) (De wizard Setup gebruiken om System Center Configuration Manager-sites te installeren) voor meer informatie.  

3.  **Een zelfstandige primaire site uitbreiden:** Wanneer u een zelfstandige primaire site uitbreidt door een nieuwe centrale beheersite installeert, moet u Setup en de bronbestanden vanaf de CD. Meest recente map vanaf de primaire site naar de nieuwe centrale beheersite installeren. Wanneer een installatie wordt uitgevoerd vanuit een kopie van de map CD.Latest vanaf de primaire site, worden de bronbestanden voor installatie gebruikt die overeenkomen met de versie van de primaire site. Zie [Expand a stand-alone primary site](../../../core/servers/deploy/install/use-the-setup-wizard-to-install-sites.md#bkmk_expand) (Een zelfstandige primaire site uitbreiden) in het onderwerp [Use the Setup Wizard to install System Center Configuration Manager-sites](../../../core/servers/deploy/install/use-the-setup-wizard-to-install-sites.md) (De wizard Setup gebruiken om System Center Configuration Manager-sites te installeren) voor meer informatie.

> [!IMPORTANT]  
>  De bronbestanden in de bijgewerkte map CD.Latest worden niet ondersteund voor:  
>   
>  -   Installatie van een nieuwe site voor een nieuwe hiërarchie  
>  -   Een Microsoft System Center 2012 Configuration Manager-site upgraden naar System Center Configuration Manager
