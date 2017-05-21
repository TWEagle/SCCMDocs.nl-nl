---
title: Sitesysteemrollen voor clients | Microsoft-documenten
description: Sitesysteemrollen bepalen voor clients in System Center Configuration Manager.
ms.custom: na
ms.date: 04/23/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-client
ms.tgt_pltfrm: na
ms.topic: get-started-article
ms.assetid: 984e8d92-7327-4b08-9228-0c955e6ac778
caps.latest.revision: 9
caps.handback.revision: 0
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 690d03d9c8c49a815bd318df549d7401a855bc5d
ms.openlocfilehash: 9f2dda834f23b2ee85c4c301c7e1b6a3a54ebc97
ms.contentlocale: nl-nl
ms.lasthandoff: 05/17/2017


---
# <a name="determine-the-site-system-roles-for-system-center-configuration-manager-clients"></a>De sitesysteemrollen bepalen voor System Center Configuration Manager-clients

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*

In dit onderwerp kan u helpen bepalen de sitesysteemrollen die u nodig hebt voor het implementeren van Configuration Manager-clients:  

 Zie voor meer informatie over waar u de sitesysteemrollen installeren vereist in de hiërarchie [ontwerpen van een hiërarchie van sites voor System Center Configuration Manager](../../../../core/plan-design/hierarchy/design-a-hierarchy-of-sites.md).  

 Zie voor meer informatie over het installeren en configureren van de sitesysteemrollen die u nodig hebt, [sitesysteemrollen installeren](../../../../core/servers/deploy/configure/install-site-system-roles.md).  

##  <a name="determine-if-you-need-a-management-point"></a>Bepaal of u een beheerpunt moet  
 Standaard worden alle Windows-clientcomputers een distributiepunt gebruiken om de Configuration Manager-client te installeren en kunnen terugvallen op een beheerpunt wanneer een distributiepunt niet beschikbaar is. Maar u kunt Windows-clients installeren vanaf een alternatieve bron op computers wanneer u de CCMSetup opdrachtregeleigenschap **/bron: < pad\>**. U kunt dit bijvoorbeeld doen als u clients op het Internet installeert. Een ander scenario is wanneer u geen netwerkpakketten tussen de computer en het beheerpunt wordt verzenden tijdens de clientinstallatie, mogelijk omdat de vereiste poorten worden geblokkeerd door een firewall wilt maken of omdat u een verbinding met lage bandbreedte. Alle clients moeten echter communiceren met een beheerpunt om toe te wijzen aan een site en te worden beheerd door Configuration Manager.  

 Voor meer informatie over de CCMSetup opdrachtregeleigenschap **/bron: < pad\>**, Zie [over eigenschappen van clientinstallatie in System Center Configuration Manager](../../../../core/clients/deploy/about-client-installation-properties.md).  

 Als u meer dan één beheerpunt in de hiërarchie installeert, worden clients automatisch verbinding met een beheerpunt op basis van hun forest-lidmaatschap en de netwerklocatie locatie. U kunt meer dan één beheerpunt op een secundaire site installeren.  

 Mac-computerclients clients en mobiele apparaten die u met Configuration Manager altijd registreert een beheerpunt nodig hebt voor de clientinstallatie. Dit beheerpunt moet zich in een primaire site moet worden geconfigureerd voor ondersteuning van mobiele apparaten en moet clientverbindingen via Internet accepteren. Deze clients kunnen beheerpunten op secundaire sites gebruiken of verbinding maken met beheerpunten in andere primaire sites.  

##  <a name="determine-if-you-need-a-fallback-status-point"></a>Bepaal of u een terugvalstatuspunt moet.  
 U kunt een terugvalstatuspunt gebruiken om te controleren van clientimplementatie voor Windows-computers. U kunt ook de Windows-computer-clients die niet beheerd worden omdat ze niet kunnen met een beheerpunt communiceren identificeren. Mac-computers, mobiele apparaten die zijn ingeschreven door Configuration Manager en mobiele apparaten die worden beheerd via de Exchange Server-connector gebruik niet een terugvalstatuspunt.  

 Een terugvalstatuspunt is niet vereist om clientactiviteiten en clientstatus te bewaken.  

 Het terugvalstatuspunt communiceert altijd met clients via HTTP, Hierbij maakt gebruik van niet-geverifieerde verbindingen en worden gegevens verzonden in normale tekst. Hiermee wordt het terugvalstatuspunt kwetsbaar voor aanvallen, vooral wanneer het gebruik in combinatie met clientbeheer via Internet. Beperk uw kwetsbaarheid door altijd een speciale server voor het uitvoeren van het terugvalstatuspunt en installeer geen andere sitesysteemrollen op dezelfde server in een productieomgeving.  

 Installeer een terugvalstatuspunt als alle volgende van toepassing zijn:  

-   U wilt dat clientcommunicatiefouten van Windows-computers moet worden verzonden naar de site, zelfs als deze clientcomputers niet kunnen met een beheerpunt communiceren.  

-   U wilt gebruiken van de Configuration Manager clientimplementatierapporten, waarin de gegevens die zijn verzonden naar het terugvalstatuspunt worden weergegeven.  

-   U hebt een speciale server voor deze sitesysteemrol en hebt aanvullende beveiligingsmaatregelen getroffen om de server te beschermen tegen een aanval.  

-   De voordelen van het gebruik van een terugvalstatuspunt wegen tegen een beveiligingsrisico's die zijn gekoppeld aan niet-geverifieerde verbindingen en leesbare tekst overdrachten via HTTP-verkeer.  

 Installeer een terugvalstatuspunt niet als de beveiligingsrisico's van het uitvoeren van een website met niet-verbindingen geverifieerde en ongecodeerde tekst overdrachten wegen tegen de voordelen van de client communicatieproblemen identificeren.  

##  <a name="determine-whether-you-need-a-reporting-services-point"></a>Bepaal of u een reporting moet services-punt  
 Configuration Manager biedt tal van rapporten kunt u de installatie, toewijzing en beheer van clients in de Configuration Manager-console bewaken. Voor sommige clientimplementatierapporten moeten clients zijn toegewezen aan een terugvalstatuspunt.  

 Hoewel de rapporten niet nodig zijn voor het implementeren van clients en u kunt sommige implementatie informatie zien in de Configuration Manager-console of de Clientlogboekbestanden gebruiken voor gedetailleerde informatie, bieden de clientrapporten waardevolle informatie voor het controleren en problemen met implementatie van clients.  

##  <a name="determine-if-you-need-an-enrollment-point-and-an-enrollment-proxy-point"></a>Bepalen of u een inschrijvingspunt en een inschrijvingsproxypunt nodig hebt  
 Configuration Manager vereist het inschrijvingspunt en het inschrijvingsproxypunt om mobiele apparaten te registreren en de inschrijving van certificaten voor Mac-computers. Deze sitesysteemrollen zijn niet nodig als u mobiele apparaten beheert via de Exchange Server-connector, of als u de verouderde client van mobiele apparaten (bijvoorbeeld Windows CE) installeert of als u aanvragen en installeren van het clientcertificaat op Mac-computers onafhankelijk van Configuration Manager.  

##  <a name="determine-if-you-need-a-distribution-point"></a>Bepalen of u een distributiepunt nodig  
 U hoeft niet een distributiepunt voor het installeren van Configuration Manager-clients op Windows-computers. Standaard Configuration Manager maakt gebruik van een distributiepunt voor het installeren van de clientbronbestanden op Windows-computers Hoewel terugvallen op deze bestanden te downloaden van een beheerpunt. Distributiepunten worden niet gebruikt voor het installeren van clients van mobiele apparaten die zijn ingeschreven door Configuration Manager, maar worden gebruikt als u de verouderde client voor mobiele apparaten installeert. Als u de Configuration Manager-client als onderdeel van de implementatie van een besturingssysteem installeert, wordt de installatiekopie van het besturingssysteem opgeslagen en opgehaald uit een distributiepunt.  

 Hoewel u mogelijk geen distributiepunten voor het installeren van de meeste Configuration Manager-clients, moet u deze software zoals toepassingen en software-updates te installeren op de clients.  

##  <a name="determine-if-you-need-an-application-catalog-website-point-and-an-application-catalog-web-services-point"></a>Bepaal of u een application catalog-websitepunt en een application catalog-webservicepunt moet  
 De application catalog-websitepunt en application catalog-webservicepunt niet nodig zijn voor clientimplementatie. U wilt misschien echter ze te installeren als onderdeel van uw clientimplementatie, zodat gebruikers de volgende acties uitvoeren kunnen als de Configuration Manager-client is geïnstalleerd op Windows-computers:  

-   Mobiele apparaten wissen.  

-   Zoeken en installeren van toepassingen uit de Application Catalog.  

-   Toepassingen implementeren voor gebruikers en apparaten met een implementatiedoel van **beschikbaar**.  

##  <a name="determine-whether-you-require-a-cloud-management-gateway-connector-point"></a>Bepalen of u een punt Cloud Management Gateway-Connector nodig hebt 

U moet een cloud-gateway-connector beheerpunt bij het instellen van een [cloud management gateway](/sccm/core/clients/manage/setup-cloud-management-gateway) naar [beheren van clients op het Internet](/sccm/core/clients/manage/manage-clients-internet).


 
