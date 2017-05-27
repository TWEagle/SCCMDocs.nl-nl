---
title: Sites configureren | Microsoft-documenten
description: "Deze controlelijst zodat u rekening houden met de meest voorkomende configuraties die invloed hebben op sites en hiërarchieën raadplegen."
ms.custom: na
ms.date: 2/7/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: get-started-article
ms.assetid: 9efb4061-f642-48bd-8332-3357ff5b3118
caps.latest.revision: 15
author: Brenduns
ms.author: brenduns
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 5f1efaa776079b21d52b9936273380e9bb8963e9
ms.openlocfilehash: 862f420c063cb44c419d4904fbb4696efb739758
ms.contentlocale: nl-nl
ms.lasthandoff: 05/17/2017


---
# <a name="configure-sites-and-hierarchies-for-system-center-configuration-manager"></a>Sites en hiërarchieën configureren voor System Center Configuration Manager

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*

Nadat u uw eerste System Center Configuration Manager-site installeren of aanvullende sites aan uw hiërarchie toevoegen, gebruik de volgende controlelijst om ervoor te zorgen dat u rekening houden met de meest voorkomende configuraties die invloed hebben op sites en hiërarchieën.  

## <a name="checklist-of-common-configurations-for-new-and-additional-sites"></a>Controlelijst van veelgebruikte configuraties voor nieuwe en aanvullende sites  
Houd rekening met de volgende opmerkingen over de configuratie, die de meeste implementaties van toepassing:

-   Sommige opties bouwen voort op elkaar, zoals de detectie van Active Directory-forests en grenzen grens groepen.  

-   Diverse configuraties bevatten standaardwaarden die u, in ieder geval tijdelijk, kunt gebruiken zonder configuratiewijzigingen.  

-   Andere configuraties, zoals grensgroepen en distributiepuntengroepen, moet u configureren voordat u ze kunt gebruiken.  

|Actie|Details|  
|------------|-------------|  
|Beheer op basis van rollen configureren|Scheiden administratieve toewijzingen om te bepalen welke gebruikers met beheerdersrechten kunnen weergeven en beheren van verschillende objecten en gegevens in uw Configuration Manager-omgeving.<br /><br /> Configuraties voor beheer op basis van rollen worden gedeeld met alle sites in een hiërarchie.   <br/><br/>Zie voor meer informatie [op rollen gebaseerd beheer voor System Center Configuration Manager configureert](../../../../core/servers/deploy/configure/configure-role-based-administration.md).|  
|Sitegegevens publiceren naar Active Directory Domain Services (AD DS)|Kunt u gemakkelijk voor clients om te zoeken, services en efficiënt sitebronnen.<br /><br /> U moet eerst [het Active Directory-schema uitbreidt voor System Center Configuration Manager](../../../../core/plan-design/network/extend-the-active-directory-schema.md), en vervolgens elke site afzonderlijk te moet worden geconfigureerd [sitegegevens publiceren voor System Center Configuration Manager](../../../../core/servers/deploy/configure/publish-site-data.md)|  
|Een serviceverbindingspunt configureren|Plan installeren en configureren van de service connection point op de bovenste site van uw hiërarchie. Zie [Informatie over het serviceaansluitpunt in System Center Configuration Manager](../../../../core/servers/deploy/configure/about-the-service-connection-point.md) voor meer informatie.|  
|Sitesysteemrollen toevoegen|Een of meer extra sitesysteemrollen installeren voor afzonderlijke sites.  Zie voor meer informatie [sitesysteemrollen toevoegen voor System Center Configuration Manager](../../../../core/servers/deploy/configure/add-site-system-roles.md).|  
|Sitegrenzen en grensgroepen configureren|Geef de grenzen die netwerklocaties definiëren op het intranet die apparaten kan bevatten die u wilt beheren. Vervolgens grensgroepen configureren zodat clients op deze netwerklocaties Configuration Manager-bronnen vindt. Zie voor meer informatie [sitegrenzen en grensgroepen definiëren voor System Center Configuration Manager](../../../../core/servers/deploy/configure/define-site-boundaries-and-boundary-groups.md).|  
|Distributiepuntengroepen configureren|Configureer logische groepen van distributiepunten om het implementatiebeheer te vereenvoudigen. Zie voor meer informatie [distributiepuntgroepen beheren](../../../../core/servers/deploy/configure/install-and-configure-distribution-points.md#bkmk_manage) in [installeren en configureren van distributiepunten voor System Center Configuration Manager](../../../../core/servers/deploy/configure/install-and-configure-distribution-points.md).|  
|De detectie uitvoeren|Voer detectie om te zoeken naar bronnen op het netwerk, met inbegrip van de netwerkinfrastructuur, apparaten en gebruikers.<br /><br /> Zie [Detectie uitvoeren voor System Center Configuration Manager](../../../../core/servers/deploy/configure/run-discovery.md) voor meer informatie.|  
|Voeg redundantie en capaciteit voor beheerders die uw infrastructuur beheren|Aanvullende SMS-providers en Configuration Manager-consoles om uit te breiden capaciteit voor beheerders voor het beheren van uw infrastructuur installeren:<br /><br /> **Installeren van extra SMS-providers** redundantie contactpunten voor het beheer van uw site en hiërarchie. Zie voor meer informatie [beheren van de SMS-provider](../../../../core/servers/manage/modify-your-infrastructure.md#BKMK_ManageSMSprovider) in [wijzigen van de System Center Configuration Manager-infrastructuur](../../../../core/servers/manage/modify-your-infrastructure.md).<br /><br /> **Aanvullende Configuration Manager-consoles installeren** om toegang te bieden aan extra gebruikers met beheerdersrechten. Zie voor meer informatie [installeert Configuration Manager-consoles](../../../../core/servers/deploy/install/install-consoles.md).|  
|Siteonderdelen configureren|Site-onderdelen op elke site om het gedrag van sitesysteemrollen en statusrapportage site configureren. Zie [Siteonderdelen voor System Center Configuration Manager](../../../../core/servers/deploy/configure/site-components.md) voor meer informatie.|  
|Aangepaste verzamelingen maken|Met informatie over de apparaten en gebruikers die is gedetecteerd, maakt u aangepaste verzamelingen van objecten die moeten worden toekomstige beheertaken vereenvoudigen. Zie voor meer informatie [het maken van verzamelingen in System Center Configuration Manager](../../../../core/clients/manage/collections/create-collections.md).|  
|Instellingen configureren voor het beheren van implementaties met een hoog risico|Instellingen configureren op een site die gebruikers met beheerdersrechten waarschuwt bij het maken van een hoog risico takenreeksimplementatie.  Zie voor meer informatie [instellingen voor het beheren van implementaties met een hoog risico voor System Center Configuration Manager](../../../../protect/understand/settings-to-manage-high-risk-deployments.md).|  
|Databasereplica's voor beheerpunten configureren|Configureer een databasereplica verminderen de CPU-belasting op de siteserver van de database door beheerpunten wordt geplaatst terwijl ze het afhandelen van clients. Zie [Databasereplica's voor beheerpunten voor System Center Configuration Manager](../../../../core/servers/deploy/configure/database-replicas-for-management-points.md) voor meer informatie.|  
|Configureren van een SQL Server AlwaysOn-beschikbaarheidsgroep om de sitedatabase te hosten|Vanaf versie 1602-beschikbaarheidsgroepen configureren als oplossingen voor hoge beschikbaarheid en herstel na noodgevallen voor het hosten van de sitedatabase op primaire sites en de centrale beheersite. Zie voor meer informatie [SQL Server AlwaysOn van een maximaal beschikbare sitedatabase voor System Center Configuration Manager](../../../../core/servers/deploy/configure/sql-server-alwayson-for-a-highly-available-site-database.md).|  
|Replicatie tussen sites wijzigen|Zie [Gegevensoverdracht tussen sites in System Center Configuration Manager](../../../../core/servers/manage/data-transfers-between-sites.md) voor meer informatie over de volgende onderwerpen:<br /><br /> Configureer [bestandsgebaseerde replicatie](../../../../core/servers/manage/data-transfers-between-sites.md#bkmk_fileroute) tussen secundaire sites<br /><br /> Configureer [database-replicatiekoppelingen](../../../../core/servers/manage/data-transfers-between-sites.md#bkmk_Dblinks)<br /><br /> Configureer [gedistribueerde weergaven](../../../../core/servers/manage/data-transfers-between-sites.md#bkmk_distviews)|  

