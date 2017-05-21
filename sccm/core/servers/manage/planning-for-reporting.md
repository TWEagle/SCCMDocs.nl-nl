---
title: Rapportage plannen | Microsoft-documenten
description: Van details over de installatie op beveiliging en bandbreedte van het netwerk is het belangrijk om te plannen voor rapportage in Configuration Manager.
ms.custom: na
ms.date: 10/06/2016
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: get-started-article
ms.assetid: ff920c84-d5c8-458c-b67f-bc7219b05690
caps.latest.revision: 6
author: Dougeby
ms.author: dougeby
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 10b1010ccbf3889c58c55b87e70b354559243c90
ms.openlocfilehash: 119f501057bf44e483be31db20b88326b3d05ebb
ms.contentlocale: nl-nl
ms.lasthandoff: 05/17/2017


---
# <a name="planning-for-reporting-in-system-center-configuration-manager"></a>Rapportage in System Center Configuration Manager plannen

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*

Rapportage in System Center Configuration Manager biedt een set hulpprogramma's en resources waarmee u de Geavanceerde rapportagemogelijkheden van SQL Server Reporting Services gebruiken. Gebruik de volgende secties om te plannen voor rapportage in Configuration Manager.  

##  <a name="BKMK_InstallReportingServicesPoint"></a> Bepalen waar u het Reporting Services-punt wilt installeren  
 Wanneer u Configuration Manager-rapporten op een site uitvoert, hebben de rapporten toegang tot de informatie in de sitedatabase waarin de verbinding plaatsvindt. U kunt met behulp van de volgende rubrieken bepalen waar u het Reporting Services-punt wilt installeren en welke gegevensbron u wilt gebruiken.  

> [!NOTE]  
>  Zie voor meer informatie over het plannen van sitesystemen in Configuration Manager [sitesysteemrollen toevoegen](../deploy/configure/add-site-system-roles.md).  

###  <a name="BKMK_SupportedSiteServers"></a> Ondersteunde sitesysteemservers  
 U kunt het Reporting Services-punt op een centrale beheersite en primaire sites, maar ook op systemen voor meerdere sites op een site en op andere sites in de hiërarchie installeren. Het Reporting Services-punt wordt niet ondersteund op secundaire sites. Het eerste Reporting Services-punt op een site wordt geconfigureerd als de standaardrapportserver. U kunt meer reporting services-punten op een site toevoegen, maar de standaardrapportserver op elke site wordt actief gebruikt voor Configuration Manager-rapporten. U kunt het Reporting Services-punt op de siteserver of een extern sitesysteem installeren. Vanwege de prestaties is het echter de aanbevolen procedure om Reporting Services te gebruiken op een externe sitesysteemserver.  

###  <a name="BKMK_DataReplication"></a> Overwegingen voor gegevensreplicatie  
 Configuration Manager deelt de gegevens die deze als globale gegevens hetzij sitegegevens repliceert. Globale gegevens verwijzen naar objecten die door gebruikers met beheerdersrechten zijn gemaakt en die naar alle sites binnen de hiërarchie zijn gerepliceerd, terwijl secundaire sites alleen een deelverzameling van de globale gegevens ontvangen. Voorbeelden van globale gegevens zijn onder meer software-implementaties, software-updates, verzamelingen en op functie gebaseerde beheerbeveiligingsbereiken. Sitegegevens verwijzen naar operationele informatie die primaire Configuration Manager-sites en de clients die rapport naar primaire sites maken. Sitegegevens worden gerepliceerd naar de centrale beheersite, maar niet naar andere primaire sites. Voorbeelden van sitegegevens zijn onder meer inventarisatiegegevens van hardware, statusberichten, waarschuwingen en de resultaten van op query's gebaseerde verzamelingen. Sitegegevens zijn alleen zichtbaar op de centrale beheersite en de primaire site waar de gegevens vandaan komen.  

 U kunt de volgende factoren overwegen om te kunnen bepalen waar u uw Reporting Services-punten wilt installeren:  

-   Een reporting services-punt met de database van de centrale beheersite als rapportgegevensbron toegang tot alle globale en sitegegevens in de Configuration Manager-hiërarchie heeft. Als u rapporten nodig hebt die sitegegevens voor meerdere sites in een hiërarchie bevatten, Overweeg de installatie van het reporting services-punt op een sitesysteem op de centrale beheersite en de centrale beheersite database gebruiken als rapportgegevensbron.  

-   Een Reporting Services-punt met een database van een onderliggende primaire site als rapportgegevensbron heeft alleen toegang tot globale gegevens en sitegegevens van de lokale primaire site en eventuele onderliggende secundaire sites. Sitegegevens voor andere primaire sites in de Configuration Manager-hiërarchie worden niet gerepliceerd naar de primaire site en waardoor Reporting Services kan geen toegang toe heeft. Als u rapporten nodig hebt die sitegegevens voor een specifieke primaire site of globale gegevens bevatten, maar u niet wilt dat de rapportgebruiker toegang hebben tot sitegegevens van andere primaire sites, een reporting services-punt installeren op een sitesysteem op de primaire site en de primaire site-database worden gebruikt als rapportgegevensbron.  

###  <a name="BKMK_NetworkBandwidth"></a> Overwegingen voor netwerkbandbreedte  
 Sitesysteemservers in dezelfde site communiceren met elkaar door middel van SMB (Server Message Block), HTTP of HTTPS, afhankelijk van de wijze waarop u de site hebt geconfigureerd. Omdat deze communicatie niet wordt beheerd en op willekeurige tijdstippen plaatsvindt zonder beheer van het netwerkbandbreedte, dient u de beschikbare netwerkbandbreedte te controleren voordat u de rol Reporting Services-punt op een sitesysteem installeert.  

> [!NOTE]  
>  Zie voor meer informatie over het plannen van sitesystemen [sitesysteemrollen toevoegen](../deploy/configure/add-site-system-roles.md).  

##  <a name="BKMK_RoleBaseAdministration"></a> Planning voor op rollen gebaseerd beheer voor rapporten  
 Beveiliging voor rapporteren lijkt erg veel op andere objecten in Configuration Manager, waar u beveiligingsrollen en machtigingen aan gebruikers met beheerdersrechten toewijzen kunt. Gebruikers met beheerdersrechten kunnen alleen rapporten uitvoeren en wijzigen waarvoor zij over de toepasselijke beveiligingsrechten beschikken. Als u wilt uitvoeren van rapporten in de Configuration Manager-console, hebt u de **lezen** voor de **Site** machtigingen en de machtigingen die zijn geconfigureerd voor specifieke objecten.  

 In tegenstelling tot andere objecten in Configuration Manager, moeten de beveiligingsrechten die u voor gebruikers met beheerdersrechten in de Configuration Manager-console echter ook worden geconfigureerd in Reporting Services. Wanneer u beveiligingsrechten in de Configuration Manager-console configureert, wordt de reporting services-punt verbinding met Reporting Services en stelt de toepasselijke machtigingen voor rapporten. Zo beschikt de beveiligingsrol **Software-updatebeheer** over de machtigingen **Rapport uitvoeren** en **Rapport wijzigen** die daaraan zijn gekoppeld. Gebruikers met beheerdersrechten die uitsluitend de rol **Software-updatebeheer** zijn toegewezen, kunnen alleen rapporten voor software-updates uitvoeren en wijzigen. Rapporten voor andere objecten worden niet weergegeven in de Configuration Manager-console. De uitzondering hierop is dat enkele rapporten niet gekoppeld aan een specifieke Configuration Manager beveiligbare objecten zijn. De gebruiker met beheerdersrechten moet voor deze rapporten beschikken over het recht **Lezen** voor de machtiging **Site** om de rapporten uit te voeren en de rechten **Wijzigen** voor de machtiging **Site** om de rapporten te wijzigen.  

 Rapporten zijn volledig ingeschakeld voor op rollen gebaseerd beheer. De gegevens voor alle rapporten met Configuration Manager is gefilterd op basis van de machtigingen van de gebruiker met beheerdersrechten die het rapport uitvoert. Gebruikers met beheerdersrechten die specifieke rollen hebben kunnen alleen de informatie inzien die is gedefinieerd voor hun rollen.  

 Zie voor meer informatie over beveiligingsrechten voor rapporteren [configureren reporting](configuring-reporting.md).  

 Zie voor meer informatie over op rollen gebaseerd beheer in Configuration Manager [op rollen gebaseerd beheer configureert](../deploy/configure/configure-role-based-administration.md).  

## <a name="next-steps"></a>Volgende stappen  
 Gebruik de volgende aanvullende onderwerpen over het plannen voor rapportage in Configuration Manager:  

-   [Vereisten voor rapportage in System Center Configuration Manager](../../../core/servers/manage/prerequisites-for-reporting.md)  
-   [Aanbevolen procedures voor rapportage in System Center Configuration Manager](../../../core/servers/manage/best-practices-for-reporting.md)  

