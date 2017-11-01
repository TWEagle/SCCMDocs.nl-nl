---
title: "Bronhiërarchieën voor migratie"
titleSuffix: Configuration Manager
description: "Een bronhiërarchie en bronsites configureren zodat u gegevens naar uw System Center Configuration Manager-omgeving migreren kunt."
ms.custom: na
ms.date: 12/29/2016
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: ccce7cb5-e18f-4337-8adf-2018edca3c00
caps.latest.revision: "5"
caps.handback.revision: "0"
author: Brenduns
ms.author: brenduns
manager: angrobe
ms.openlocfilehash: 63df5f909b3718d4b720a6767da8272f1895b074
ms.sourcegitcommit: c236214b2fcc13dae7bad96d7fb33f692868191d
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/12/2017
---
# <a name="configure-source-hierarchies-and-source-sites-for-migration-to-system-center-configuration-manager"></a>Bronhiërarchieën en bronsites voor migratie naar System Center Configuration Manager configureren

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*

Om de migratie van gegevens naar uw System Center Configuration Manager-omgeving, moet u een ondersteunde bronhiërarchie van Configuration Manager en een of meer bronsites in die hiërarchie die gegevens bevatten die u wilt migreren.  

> [!NOTE]  
>  Migratiebewerkingen worden uitgevoerd op het hoogste niveau in de doelhiërarchie. Als u migratie configureert wanneer u een Configuration Manager-console die is verbonden met een primaire onderliggende site gebruikt, moet u voldoende tijd uittrekken om de configuratie te repliceren naar de centrale beheersite, start, en status worden vervolgens gerepliceerd naar de primaire site waarmee u verbonden bent.  

 Gebruik de informatie en procedures in de volgende secties Specificeer de bronhiërarchie en aanvullende bronsites toevoegen. Nadat u deze procedures hebt voltooid, kunt u migratietaken maken en starten om gegevens te migreren van de bronhiërarchie naar de doelhiërarchie.  

-   [Een bronhiërarchie voor migratie opgeven](#BKBM_ConfigSrcHierarchy)  

-   [Aanvullende bronsites van de bronhiërarchie bepalen](#BKBM_ConfigSrcSites)  

##  <a name="BKBM_ConfigSrcHierarchy"></a>Een bronhiërarchie voor migratie opgeven  
 Om gegevens te migreren naar uw doelhiërarchie, moet u een ondersteunde bronhiërarchie met de gegevens die u wilt migreren. Het hoogste niveau van die hiërarchie wordt standaard een bronsite van de bronhiërarchie. Als u van een Configuration Manager 2007-hiërarchie migreert, kunt u automatisch instellen om aanvullende bronsites voor migratie nadat gegevens zijn verzameld vanaf de oorspronkelijke bronsite. Als u van een System Center 2012 Configuration Manager of System Center Configuration Manager-hiërarchie migreert, hoeft u geen aanvullende bronsites instellen voor het migreren van gegevens van de bronhiërarchie. Dit komt doordat in deze versies van Configuration Manager gebruikt een gedeelde database die beschikbaar is op het hoogste niveau van de bronhiërarchie. De gedeelde database bevat alle informatie die u kunt migreren.  

 Gebruik de volgende procedures om op te geven van een bronhiërarchie voor migratie en aanvullende bronsites in een Configuration Manager 2007-hiërarchie te identificeren.  

 Deze procedure uitvoert met een Configuration Manager-console die is verbonden met de doelhiërarchie:  

### <a name="to-configure-a-source-hierarchy"></a>Een bronhiërarchie configureren   

1.  Klik op **Beheer**in de Configuration Manager-console.  

2.  Vouw **Migratie** uit in de werkruimte **Beheer**en klik vervolgens op **Bronhiërarchie**.  

3.  Op de **Start** tabblad, in de **migratie** groep, klikt u op **bronhiërarchie opgeven**.  

4.  In de **bronhiërarchie opgeven** in het dialoogvenster voor **bronhiërarchie**, selecteer **nieuwe bronhiërarchie**.  

5.  Voor **Top-level Configuration Manager-siteserver**, geef de naam of IP-adres van het hoogste niveau van een ondersteunde bronhiërarchie.  

6.  Geef de bronaccounts voor toegang tot die de volgende machtigingen hebben:  

    -   Bronsiteaccount: **Lees** machtiging voor de SMS-Provider voor de opgegeven site op het hoogste niveau in de bronhiërarchie. Delen van distributiepunten en upgrades vereisen **wijzigen** en **verwijderen** machtigingen voor de site in de bronhiërarchie.

    -   Bronsitedatabaseaccount: **Lees** en **Execute** machtiging voor de SQL Server-database voor de opgegeven site op het hoogste niveau in de bronhiërarchie.  

     Als u het gebruik van het computeraccount opgeeft, wordt in Configuration Manager maakt gebruik van het computeraccount van het hoogste niveau van de doelhiërarchie. Zorg ervoor dat dit account lid van de beveiligingsgroep is voor deze optie **DCOM-gebruikers** in het domein waarin het hoogste niveau van de bronhiërarchie zich bevindt.  

7.  Als u wilt delen van distributiepunten tussen de bron- en Doelhiërarchieën, selecteer de **inschakelen voor de bronsiteserver deling van distributiepunt** selectievakje. Als u niet op dit moment delen van distributiepunten inschakelt, kunt u doen zodat door de referenties van de bronsite te bewerken nadat gegevens verzamelen is voltooid.  

8.  Klik op **OK** om de configuratie op te slaan. Hiermee opent u de **Status gegevensverzameling** in het dialoogvenster en start het automatisch verzamelen van gegevens.  

9. Wanneer gegevens zijn verzameld, klikt u op **sluiten** sluiten de **Status gegevensverzameling** dialoogvenster en de configuratie te voltooien.  

##  <a name="BKBM_ConfigSrcSites"></a>Aanvullende bronsites van de bronhiërarchie bepalen  
 Wanneer u een ondersteunde bronhiërarchie configureert, wordt het hoogste niveau van die hiërarchie automatisch geconfigureerd als een bronsite en gegevens automatisch verzameld vanaf die site. De volgende actie die u wilt uitvoeren, is afhankelijk van de versie van Configuration Manager die wordt uitgevoerd door de bronhiërarchie:  

-   Voor een Configuration Manager 2007-bronhiërarchie, kunt u beginnen met migratie van die oorspronkelijke bronsite of Stel aanvullende bronsites van de bronhiërarchie nadat het verzamelen van gegevens is voltooid voor de oorspronkelijke bronsite. Om gegevens te migreren die alleen beschikbaar op een onderliggende site, Stel u aanvullende bronsites voor een Configuration Manager 2007-hiërarchie. U kunt bijvoorbeeld aanvullende bronsites voor het verzamelen van gegevens over inhoud die u migreren wilt als deze wordt gemaakt op een onderliggende site in de bronhiërarchie en niet beschikbaar op de bovenste site van de bronhiërarchie is configureren.  

-   Voor een System Center 2012 Configuration Manager of System Center Configuration Manager-bronhiërarchie hoeft u geen aanvullende bronsites te configureren. Dit komt doordat in deze versies van Configuration Manager gebruikt een gedeelde database die beschikbaar is op het hoogste niveau van de bronhiërarchie. De gedeelde database bevat alle informatie die u vanaf alle sites in die bronhiërarchie migreren kunt. Hierdoor worden de gegevens die u kunt migreren beschikbaar vanaf de site op het hoogste niveau van de bronhiërarchie.  

Wanneer u aanvullende bronsites voor een Configuration Manager 2007-bronhiërarchie configureert, moet u aanvullende bronsites vanaf de bovenkant van de bronhiërarchie naar de onderkant configureren. Voordat u een van de onderliggende sites als bronsites configureren, moet u een bovenliggende site configureren als een bronsite.  

Gebruik de volgende procedure als u aanvullende bronsites configureren voor Configuration Manager 2007-bronhiërarchieën:  

### <a name="to-identify-additional-source-sites-in-the-source-hierarchy"></a>Aanvullende bronsites in de bronhiërarchie identificeren 

1.  Klik op **Beheer**in de Configuration Manager-console.  

2.  Vouw **Migratie** uit in de werkruimte **Beheer**en klik vervolgens op **Bronhiërarchie**.  

3.  Kies de site die u wilt configureren als een bronsite.  

4.  Klik op het tabblad **Start** in de groep **Bronsite** op **Configureren**.  

5.  In de **Bronsitereferenties** in het dialoogvenster voor de toegangsaccounts bron accounts opgeven die de volgende machtigingen hebben:  

    -   Bronsiteaccount: **Lees** machtiging voor de SMS-Provider voor de opgegeven site op het hoogste niveau in de bronhiërarchie. Delen van distributiepunten en upgrades vereisen **wijzigen** en **verwijderen** machtigingen voor de site in de bronhiërarchie.  

    -   Bronsitedatabaseaccount: **Lees** en **Execute** machtiging voor de SQL Server-database voor de opgegeven site op het hoogste niveau in de bronhiërarchie.  

    Als u het gebruik van het computeraccount opgeeft, wordt in Configuration Manager maakt gebruik van het computeraccount van het hoogste niveau van de doelhiërarchie. Zorg ervoor dat dit account lid van de beveiligingsgroep is voor deze optie **DCOM-gebruikers** in het domein waarin het hoogste niveau van de bronhiërarchie zich bevindt.  

6.  Als u wilt delen van distributiepunten tussen de bron- en Doelhiërarchieën, selecteer de **inschakelen voor de bronsiteserver deling van distributiepunt** selectievakje. Als u niet op dit moment delen van distributiepunten inschakelt, kunt u doen zodat door de referenties voor de bronsite te bewerken nadat gegevens verzamelen is voltooid.  

7. Klik op **OK** om de configuratie op te slaan. Hiermee opent u de **Status gegevensverzameling** in het dialoogvenster en start het automatisch verzamelen van gegevens.  

8.  Wanneer gegevens zijn verzameld, klikt u op **sluiten** om de configuratie te voltooien.  
