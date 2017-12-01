---
title: Sites configureren
titleSuffix: Configuration Manager
description: "Raadpleeg deze controlelijst om ervoor te zorgen dat u rekening houden met de meest voorkomende configuraties die invloed hebben op zowel sites als hiërarchieën."
ms.custom: na
ms.date: 2/7/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: configmgr-other
ms.tgt_pltfrm: na
ms.topic: get-started-article
ms.assetid: 9efb4061-f642-48bd-8332-3357ff5b3118
caps.latest.revision: "15"
author: mstewart
ms.author: mstewart
manager: angrobe
ms.openlocfilehash: 540a3aac3d489fb1655d769b6e31a1b4c5cc0092
ms.sourcegitcommit: 7fe45ff75f05f7cc03ad021db8119791abe18049
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/01/2017
---
# <a name="configure-sites-and-hierarchies-for-system-center-configuration-manager"></a>Sites en hiërarchieën configureren voor System Center Configuration Manager

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*

Nadat u uw eerste System Center Configuration Manager-site installeert of extra sites aan uw hiërarchie toevoegen, gebruik de volgende controlelijst om ervoor te zorgen dat u rekening houden met de meest voorkomende configuraties die invloed hebben op zowel sites als hiërarchieën.  

## <a name="checklist-of-common-configurations-for-new-and-additional-sites"></a>Controlelijst van veelgebruikte configuraties voor nieuwe en aanvullende sites  
Houd rekening met de volgende opmerkingen over de configuratie, die de meeste implementaties van toepassing:

-   Sommige opties bouwen voort op elkaar, zoals groepen van Active Directory-Forestdetectie, grenzen en grensgroepen.  

-   Diverse configuraties bevatten standaardwaarden die u, in ieder geval tijdelijk, kunt gebruiken zonder configuratiewijzigingen.  

-   Andere configuraties, zoals grensgroepen en distributiepuntengroepen, moet u configureren voordat u ze kunt gebruiken.  

|Actie|Details|  
|------------|-------------|  
|Beheer op basis van rollen configureren|Afzonderlijke beheertoewijzingen gebruiken om te bepalen welke gebruikers met beheerdersrechten kunnen weergeven en beheren van verschillende objecten en gegevens in uw Configuration Manager-omgeving.<br /><br /> Configuraties voor beheer op basis van rollen worden gedeeld met alle sites in een hiërarchie.   <br/><br/>Zie voor meer informatie [beheer op basis van rollen voor System Center Configuration Manager configureren](../../../../core/servers/deploy/configure/configure-role-based-administration.md).|  
|Sitegegevens publiceren naar Active Directory Domain Services (AD DS)|Maakt het eenvoudig voor clients om te zoeken, services en efficiënt sitebronnen.<br /><br /> U moet eerst [Active Directory-schema voor System Center Configuration Manager uitbreiden](../../../../core/plan-design/network/extend-the-active-directory-schema.md), en vervolgens afzonderlijk op elke site moet geconfigureerd [sitegegevens voor System Center Configuration Manager publiceren](../../../../core/servers/deploy/configure/publish-site-data.md)|  
|Een serviceverbindingspunt configureren|Plan voor het installeren en configureren van het serviceverbindingspunt wordt gehost op de bovenste site van uw hiërarchie. Zie [Informatie over het serviceaansluitpunt in System Center Configuration Manager](../../../../core/servers/deploy/configure/about-the-service-connection-point.md) voor meer informatie.|  
|Sitesysteemrollen toevoegen|Een of meer extra sitesysteemrollen installeren voor afzonderlijke sites.  Zie voor meer informatie [sitesysteemrollen voor System Center Configuration Manager toevoegen](../../../../core/servers/deploy/configure/add-site-system-roles.md).|  
|Sitegrenzen en grensgroepen configureren|Geef grenzen op die de netwerklocaties op uw intranet die apparaten kan bevatten die u wilt beheren definiëren. Configureer vervolgens grensgroepen, zodat clients op deze netwerklocaties Configuration Manager-resources kunnen vinden. Zie voor meer informatie [sitegrenzen en grensgroepen definiëren voor System Center Configuration Manager](../../../../core/servers/deploy/configure/define-site-boundaries-and-boundary-groups.md).|  
|Distributiepuntengroepen configureren|Configureer logische groepen van distributiepunten om het implementatiebeheer te vereenvoudigen. Zie voor meer informatie [distributiepuntgroepen beheren](../../../../core/servers/deploy/configure/install-and-configure-distribution-points.md#bkmk_manage) in [installeren en configureren van distributiepunten voor System Center Configuration Manager](../../../../core/servers/deploy/configure/install-and-configure-distribution-points.md).|  
|De detectie uitvoeren|Voer detectie om resources te zoeken in het netwerk, zoals de netwerkinfrastructuur, apparaten en gebruikers.<br /><br /> Zie [Detectie uitvoeren voor System Center Configuration Manager](../../../../core/servers/deploy/configure/run-discovery.md) voor meer informatie.|  
|Redundantie en capaciteit toevoegen voor beheerders die uw infrastructuur beheren|Installeer aanvullende SMS-providers en Configuration Manager-consoles om uit te breiden capaciteit voor beheerders om uw infrastructuur te beheren:<br /><br /> **Installeren van extra SMS-providers** redundantie contactpunten voor het beheren van uw site en hiërarchie. Zie voor meer informatie [beheren van de SMS-provider](../../../../core/servers/manage/modify-your-infrastructure.md#BKMK_ManageSMSprovider) in [uw infrastructuur van System Center Configuration Manager aanpassen](../../../../core/servers/manage/modify-your-infrastructure.md).<br /><br /> **Installeer aanvullende Configuration Manager-consoles** om toegang te bieden aan extra gebruikers met beheerdersrechten. Zie voor meer informatie [installeert Configuration Manager-consoles](../../../../core/servers/deploy/install/install-consoles.md).|  
|Siteonderdelen configureren|Siteonderdelen configureren op elke site het gedrag van sitesysteemrollen en sitestatusrapportage te wijzigen. Zie [Siteonderdelen voor System Center Configuration Manager](../../../../core/servers/deploy/configure/site-components.md) voor meer informatie.|  
|Aangepaste verzamelingen maken|Gebruik de informatie die is gedetecteerd over apparaten en gebruikers, maak aangepaste verzamelingen van objecten om toekomstige beheertaken te vereenvoudigen. Zie voor meer informatie [verzamelingen maken in System Center Configuration Manager](../../../../core/clients/manage/collections/create-collections.md).|  
|Instellingen configureren voor het beheren van implementaties met een hoog risico|Instellingen configureren op een site die gebruikers met beheerdersrechten waarschuwt wanneer ze de takenreeksimplementatie in een hoog risico maken.  Zie voor meer informatie [instellingen voor het beheren van implementaties van met een hoog risico voor System Center Configuration Manager](../../../../protect/understand/settings-to-manage-high-risk-deployments.md).|  
|Databasereplica's voor beheerpunten configureren|Configureer een databasereplica om de CPU-belasting dat op de Sitedatabaseserver wordt geplaatst door beheerpunten serviceaanvragen van clients te verminderen. Zie [Databasereplica's voor beheerpunten voor System Center Configuration Manager](../../../../core/servers/deploy/configure/database-replicas-for-management-points.md) voor meer informatie.|  
|Configureren van een SQL Server AlwaysOn-beschikbaarheidsgroep om de sitedatabase te hosten|Vanaf versie 1602 beschikbaarheidsgroepen configureren als hoge beschikbaarheid en herstel na noodgevallen oplossingen voor het hosten van de sitedatabase op primaire sites en de centrale beheersite. Zie voor meer informatie [SQL Server AlwaysOn voor een maximaal beschikbare sitedatabase voor System Center Configuration Manager](../../../../core/servers/deploy/configure/sql-server-alwayson-for-a-highly-available-site-database.md).|  
|Replicatie tussen sites wijzigen|Zie [Gegevensoverdracht tussen sites in System Center Configuration Manager](../../../../core/servers/manage/data-transfers-between-sites.md) voor meer informatie over de volgende onderwerpen:<br /><br /> Configureer [bestandsgebaseerde replicatie](../../../../core/servers/manage/data-transfers-between-sites.md#bkmk_fileroute) tussen secundaire sites<br /><br /> Configureer [koppelingen voor databasereplicatie](../../../../core/servers/manage/data-transfers-between-sites.md#bkmk_Dblinks)<br /><br /> Configureer [gedistribueerde weergaven](../../../../core/servers/manage/data-transfers-between-sites.md#bkmk_distviews)|  
