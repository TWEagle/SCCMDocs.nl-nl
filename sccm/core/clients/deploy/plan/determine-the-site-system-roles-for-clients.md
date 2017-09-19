---
title: Sitesysteemrollen voor clients | Microsoft Docs
description: Sitesysteemrollen bepalen voor clients in System Center Configuration Manager.
ms.custom: na
ms.date: 04/23/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: configmgr-client
ms.tgt_pltfrm: na
ms.topic: get-started-article
ms.assetid: 984e8d92-7327-4b08-9228-0c955e6ac778
caps.latest.revision: "9"
caps.handback.revision: "0"
author: arob98
ms.author: angrobe
manager: angrobe
ms.openlocfilehash: 65c165ababafab3dd0d9ce8f1ce775be0d72a573
ms.sourcegitcommit: b438515490e04fb09c82a8af642d38e9a0605178
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 09/15/2017
---
# <a name="determine-the-site-system-roles-for-system-center-configuration-manager-clients"></a>De sitesysteemrollen voor System Center Configuration Manager-clients bepalen

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*

In dit onderwerp kunt u de sitesysteemrollen die u nodig hebt voor het implementeren van Configuration Manager-clients bepalen:  

 Zie voor meer informatie over waar u de sitesysteemrollen installeren die zijn vereist in de hiërarchie [een sitehiërarchie ontwerpen voor System Center Configuration Manager](../../../../core/plan-design/hierarchy/design-a-hierarchy-of-sites.md).  

 Zie voor meer informatie over het installeren en configureren van de sitesysteemrollen die u nodig hebt, [sitesysteemrollen installeren](../../../../core/servers/deploy/configure/install-site-system-roles.md).  

##  <a name="determine-if-you-need-a-management-point"></a>Bepalen of u een beheerpunt moet  
 Standaard worden alle Windows-clientcomputers een distributiepunt gebruiken om de Configuration Manager-client te installeren en kunnen terugvallen op een beheerpunt wanneer een distributiepunt niet beschikbaar is. Echter, u kunt Windows-clients installeren vanaf een alternatieve bron op computers wanneer u de CCMSetup opdrachtregeleigenschap **/source: < pad\>**. U kunt dit bijvoorbeeld doen als u clients op het Internet installeert. Een ander scenario is wanneer u voorkomen dat het verzenden van pakketten tussen de computer en het beheerpunt tijdens de clientinstallatie, mogelijk wilt omdat de vereiste poorten wordt geblokkeerd door een firewall of omdat er een verbinding met een lage bandbreedte. Alle clients moeten echter communiceren met een beheerpunt toewijzen aan een site en worden beheerd door Configuration Manager.  

 Voor meer informatie over de CCMSetup opdrachtregeleigenschap **/source: < pad\>**, Zie [over eigenschappen van clientinstallatie in System Center Configuration Manager](../../../../core/clients/deploy/about-client-installation-properties.md).  

 Wanneer u meer dan één beheerpunt in de hiërarchie installeert, worden clients automatisch verbinding met een beheerpunt op basis van hun forest-lidmaatschap en netwerk-locatie. U kunt meer dan één beheerpunt niet installeren op een secundaire site.  

 Mac-computerclients en clients voor mobiele apparaten die u met Configuration Manager altijd inschrijft vereisen een beheerpunt voor clientinstallaties. Dit beheerpunt moet zich in een primaire site, moet zijn geconfigureerd voor ondersteuning van mobiele apparaten en moet clientverbindingen accepteert van het Internet. Deze clients kunnen beheerpunten in secundaire sites gebruiken of verbinding maken met beheerpunten in andere primaire sites.  

##  <a name="determine-if-you-need-a-fallback-status-point"></a>Bepalen of u een terugvalstatuspunt moet.  
 U kunt een terugvalstatuspunt gebruiken om te controleren van clientimplementatie voor Windows-computers. U kunt ook de Windows-computer-clients die onbeheerd zijn doordat ze niet kunnen met een beheerpunt communiceren identificeren. Mac-computers, mobiele apparaten die zijn ingeschreven door Configuration Manager en mobiele apparaten die worden beheerd via de Exchange Server-connector gebruik een terugvalstatuspunt niet.  

 Een terugvalstatuspunt is niet vereist voor het bewaken van clientactiviteit en status van de client.  

 Het terugvalstatuspunt communiceert altijd met clients via HTTP, die gebruikmaakt van niet-geverifieerde verbindingen en gegevens in leesbare tekst verzonden. Dit maakt het terugvalstatuspunt kwetsbaar voor aanvallen, vooral wanneer deze wordt gebruikt met clientbeheer op Internet. Om te beperken van de kwetsbaarheid voor aanvallen, altijd een speciale server voor het uitvoeren van het terugvalstatuspunt en installeer geen andere sitesysteemrollen op dezelfde server in een productieomgeving.  

 Installeer een terugvalstatuspunt als alle volgende van toepassing:  

-   Gewenste clientcommunicatiefouten van Windows-computers worden verzonden naar de site, zelfs als deze clientcomputers niet kunnen met een beheerpunt communiceren.  

-   U wilt gebruiken van de Configuration Manager clientimplementatierapporten, waarin de gegevens die worden verzonden door het terugvalstatuspunt worden weergegeven.  

-   U hebt een speciale server voor deze sitesysteemrol en hebt aanvullende beveiligingsmaatregelen getroffen om de server te beschermen tegen een aanval.  

-   De voordelen van het gebruik van een terugvalstatuspunt bieden, opwegen tegen eventuele beveiligingsrisico's met niet-geverifieerde verbindingen en leesbare tekst overdrachten via HTTP-verkeer.  

 Installeer een terugvalstatuspunt niet als de beveiligingsrisico's van het uitvoeren van een website met niet-verbindingen geverifieerde en overdrachten ongecodeerde tekst bieden, opwegen tegen de voordelen van clientcommunicatieproblemen te identificeren.  

##  <a name="determine-whether-you-need-a-reporting-services-point"></a>Bepalen of u een reporting moet services-punt  
 Configuration Manager biedt tal van rapporten helpen bij het bewaken van de installatie, de toewijzing en het beheer van clients in de Configuration Manager-console. Sommige van de clientimplementatierapporten vereisen dat clients zijn toegewezen aan een terugvalstatuspunt.  

 Hoewel de rapporten niet nodig zijn voor het implementeren van clients en u enige implementatiegegevens in de Configuration Manager-console bekijken of gebruik de logboekbestanden van client voor meer informatie, bieden de clientrapporten waardevolle informatie voor het controleren en problemen oplossen clientimplementatie.  

##  <a name="determine-if-you-need-an-enrollment-point-and-an-enrollment-proxy-point"></a>Bepalen of u een inschrijvingspunt en een inschrijvingsproxypunt nodig hebt  
 Configuration Manager vereist het inschrijvingspunt en het inschrijvingsproxypunt mobiele apparaten te registreren en het inschrijven van certificaten voor Mac-computers. Deze sitesysteemrollen zijn niet nodig als u mobiele apparaten beheren wilt met behulp van de Exchange Server-connector of als u de verouderde client van mobiele apparaten (bijvoorbeeld voor Windows CE) installeert of als u aanvragen en installeren van het clientcertificaat op Mac-computers onafhankelijk van Configuration Manager.  

##  <a name="determine-if-you-need-a-distribution-point"></a>Bepalen of u een distributiepunt moet  
 U hoeft niet een distributiepunt voor het installeren van Configuration Manager-clients op Windows-computers. Echter, standaard, Configuration Manager maakt gebruik van een distributiepunt voor het installeren van de clientbronbestanden op Windows-computers maar kunnen terugvallen op deze bestanden downloaden van een beheerpunt. Distributiepunten worden niet gebruikt voor het installeren van clients van mobiele apparaten die zijn ingeschreven door Configuration Manager, maar worden gebruikt als u de verouderde client voor mobiele apparaten installeert. Als u de Configuration Manager-client als onderdeel van de implementatie van een besturingssysteem installeert, wordt de installatiekopie van het besturingssysteem opgeslagen en opgehaald uit een distributiepunt.  

 Hoewel u mogelijk geen distributiepunten voor het installeren van de meeste Configuration Manager-clients, moet u deze software zoals toepassingen en software-updates te installeren op de clients.  

##  <a name="determine-if-you-need-an-application-catalog-website-point-and-an-application-catalog-web-services-point"></a>Bepalen of u een application catalog-websitepunt en een toepassingscatalogus Web services-punt moet  
 De application catalog-websitepunt en application catalog-webservicepunt zijn niet nodig voor de clientimplementatie. Echter, u mogelijk ze wil installeren als onderdeel van uw clientimplementatie, zodat gebruikers de volgende acties uitvoeren kunnen als u de Configuration Manager-client is geïnstalleerd op Windows-computers:  

-   Hun mobiele apparaten wissen.  

-   Zoeken en installeren van toepassingen uit de Application Catalog.  

-   Toepassingen implementeren voor gebruikers en apparaten met een implementatiedoel van **beschikbaar**.  

##  <a name="determine-whether-you-require-a-cloud-management-gateway-connector-point"></a>Bepalen of u een punt Cloud Management Gateway-Connector nodig 

U moet een cloud gateway connector beheerpunt als u instelt een [cloudgateway management](/sccm/core/clients/manage/setup-cloud-management-gateway) naar [beheren van clients op het Internet](/sccm/core/clients/manage/manage-clients-internet).


 