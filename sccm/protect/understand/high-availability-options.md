---
title: Hoge beschikbaarheid | Microsoft-documenten
description: Informatie over het implementeren van System Center Configuration Manager met de opties die een hoge servicebeschikbaarheid mogelijk.
ms.custom: na
ms.date: 10/06/2016
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 1a38421d-24c1-4fef-bf6c-42fce53109ac
caps.latest.revision: 4
author: Brenduns
ms.author: brenduns
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 1a4a9da88caba55d9e340c7fb1f31f4e3b957f3e
ms.openlocfilehash: d3e9afb90cdc85bc7299626b642c52be659e3bdf
ms.contentlocale: nl-nl
ms.lasthandoff: 05/17/2017

---
# <a name="high-availability-options-for-system-center-configuration-manager"></a>Opties voor maximale beschikbaarheid voor System Center Configuration Manager

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*



U kunt System Center Configuration Manager met behulp van de opties die een hoge servicebeschikbaarheid mogelijk implementeren.   

De opties die maximale beschikbaarheid ondersteunen:   

-   Sites ondersteunen meerdere exemplaren van sitesysteemservers die belangrijke services aan clients leveren.  

-   Centrale beheersites en primaire sites ondersteunen de back-up van de sitedatabase. De sitedatabase bevat alle configuraties voor sites en clients en wordt gedeeld tussen sites in een hiërarchie die een centrale beheersite bevat.  

-   Ingebouwde opties voor site recovery kunnen de downtime van de server verminderen en geavanceerde opties bevatten die het herstel vereenvoudigen wanneer u een hiërarchie hebt met een centrale beheersite.  

-   Clients kunnen normale problemen zonder interventie van een beheerder automatisch oplossen.  

-   Sites genereren waarschuwingen over clients die geen recente gegevens dit beheerders dat er mogelijk problemen verwittigt kunnen versturen.  

-   Configuration Manager bevat verschillende ingebouwde rapporten waarmee u kunt het identificeren van problemen en trends voordat ze problemen worden voor server- of clientbewerkingen.  

 Configuration Manager biedt geen real-service en moet je het verwacht op de hoogte met enige vertraging gegevens worden bijgewerkt. Het is daarom ongebruikelijk voor de meeste scenario's voor een tijdelijke onderbreking van de service een kritiek probleem veroorzaakt. Wanneer u uw sites en hiërarchieën hebt geconfigureerd met maximale beschikbaarheid in gedachten, kunt de downtime minimaliseren, behouden de autonomie van de bewerkingen en een hoog serviceniveau.  

 Bijvoorbeeld, werken Configuration Manager-clients meestal autonoom met behulp van bekende schema's en configuraties voor bewerkingen en schema's om gegevens naar de site voor de verwerking te sturen.  

-   Wanneer clients geen contact met de site, cache ze gegevens totdat ze contact met de site opnemen kunnen wordt verzonden.  

-   Clients die geen contact met de site blijven werken met de laatst bekende schema's en in cache opgeslagen gegevens, zoals een eerder gedownloade toepassing die ze moeten uitvoeren of installeren, totdat ze kunnen contact opnemen met de site en nieuw beleid kunnen ontvangen.  

-   De site controleert sitesystemen en clients op periodieke statusupdates en kan waarschuwingen genereren wanneer deze niet registreren.  

-   Ingebouwde rapporten bieden inzicht in actieve bewerkingen historische bewerkingen en trends. Configuration Manager ondersteunt ook status gebaseerde berichten die bijna realtime gegevens voor actieve bewerkingen leveren.  

  Gebruik de informatie in dit onderwerp samen met de informatie in de volgende artikelen:
-   [Aanbevolen hardware](../../core/plan-design/configs/recommended-hardware.md)
-   [Ondersteunde besturingssystemen voor site-systeem serveres](../../core/plan-design/configs/supported-operating-systems-for-site-system-servers.md)  

-   [Site- en site-systeemvereisten](../../core/plan-design/configs/site-and-site-system-prerequisites.md)


##  <a name="bkmk_snh"></a>Hoge beschikbaarheid voor sites en hiërarchieën  
 **Gebruik een SQL Server-cluster om de sitedatabase te hosten:**  

 Wanneer u een SQL Server-cluster voor de database op een centrale beheersite of primaire site gebruikt, gebruikt u de failover-ondersteuning in SQL Server ingebouwd.  

 Secundaire sites kunnen geen SQL Server-cluster gebruiken en ondersteunen geen back-up of herstel van hun sitedatabase. Een secundaire site herstellen door de secundaire site vanuit de bovenliggende primaire site opnieuw te installeren.  

 **Gebruik een SQL Server AlwaysOn-beschikbaarheidsgroep om de sitedatabase te hosten:**  

 Vanaf versie 1602, kunt u SQL Server AlwaysOn-beschikbaarheidsgroepen voor het hosten van de sitedatabase op primaire sites en de centrale beheersite als een oplossing voor hoge beschikbaarheid en herstel na noodgevallen. Zie voor meer informatie [SQL Server AlwaysOn van een maximaal beschikbare sitedatabase voor System Center Configuration Manager](../../core/servers/deploy/configure/sql-server-alwayson-for-a-highly-available-site-database.md).  

 **Implementeer een hiërarchie van sites met een centrale beheersite en een of meer onderliggende primaire sites:**  

 Deze configuratie kan fouttolerantie verlenen wanneer uw sites overlappende segmenten van uw netwerk beheren. Deze configuratie biedt bovendien een bijkomende hersteloptie de informatie in de gedeelde database op een andere site gebruiken om de sitedatabase van de herstelde site opnieuw. Gebruik deze optie kunt u een mislukte of niet-beschikbare back-up van de mislukte sitedatabase te vervangen.  

 **Maak regelmatig back-ups op centrale beheersites en primaire sites:**  

 Wanneer u maken en testen van een regelmatige siteback-up, kunt u ervoor zorgen dat er gegevens die noodzakelijk zijn om een site en de ervaring voor het herstellen van een site in de minimale hoeveelheid tijd te herstellen.  

 **Installeer meerdere exemplaren van sitesysteemrollen:**  

 Wanneer u meerdere exemplaren van kritieke sitesysteemrollen zoals het beheerpunt en distributiepunt installeert, voorziet u overbodige contactpunten voor clients in het geval dat een specifieke sitesysteemserver offline is.  

 **Installeer meerdere exemplaren van de SMS-Provider op een site:** De SMS-Provider verleent het punt van beheercontact voor een of meer Configuration Manager-consoles. Als u meerdere SMS-providers installeert, kunt u redundantie verlenen aan contactpunten om u site en hiërarchie te beheren.  

##  <a name="bkmk_ssr"></a>Hoge beschikbaarheid voor sitesysteemrollen  
 U implementeert op elke site sitesysteemrollen om de services die u wilt dat clients gebruiken op deze site te leveren. De sitedatabase bevat de configuratiegegevens voor de site en voor alle clients. Gebruik een of meer van de beschikbare opties te bieden voor maximale beschikbaarheid van de sitedatabase en het herstel van de site en sitedatabase, indien nodig.  

 **Redundantie voor belangrijke sitesysteemrollen:**  

-   Application Catalog-webservicepunt  

-   Application Catalog-websitepunt  

-   Distributiepunt  

-   Beheerpunt  

-   Software-updatepunt  

-   Statusmigratiepunt  

 U kunt meerdere exemplaren van de rol Reporting services-punt om redundantie te verlenen voor rapportage over sites en clients te installeren.

 U kunt PowerShell gebruiken voor het installeren van de sitesysteemrol van Software-update-punt op een cluster van Windows Network Load Balancing (NLB) om failover-ondersteuning te verlenen  


 **Ingebouwde siteback-up:**  

 Configuration Manager bevat een ingebouwde back-uptaak om u te helpen Maak een back-up van uw site en uw kritieke informatie regelmatig. Daarnaast ondersteunt de installatiewizard van Configuration Manager siteherstelacties om u te helpen u activiteit van een site te herstellen.  

 **Publiceren naar Active Directory Domain Services en DNS:**  

 U kunt elke site om gegevens over sitesysteemservers en -services te publiceren naar Active Directory Domain Services en naar DNS configureren. Hierdoor kunnen clients om de meest toegankelijke server op het netwerk, en om te bepalen wanneer nieuwe sitesysteemservers die belangrijke services, zoals beheerpunten, kunnen verlenen beschikbaar zijn.  

 **SMS-Provider en Configuration Manager-console:**  

 Configuration Manager ondersteunt de installatie van meerdere SMS-Providers, elk op een afzonderlijke computer, zodat meerdere toegangspunten voor de Configuration Manager-console. Dit zorgt ervoor dat als een SMS-providercomputer offline is, u de mogelijkheid om te geven en te configureren voor Configuration Manager-sites en clients.  

 Wanneer een Configuration Manager-console verbinding met een site maakt, verbindt deze met een exemplaar van de SMS-Provider op die site. Het exemplaar van de SMS-Provider is niet-deterministisch geselecteerd. Als de geselecteerde SMS-Provider niet beschikbaar is, hebt u de volgende opties:  

-   Verbind de console met de site opnieuw. Elke nieuwe verbindingsaanvraag wordt niet-deterministisch een exemplaar van de SMS-Provider toegewezen en het is mogelijk dat op de nieuwe verbinding een beschikbaar exemplaar zal worden toegewezen.  

-   Verbind de console met een andere Configuration Manager-site en beheer de configuratie vanuit die verbinding. Dit introduceert een lichte vertraging van wijzigingen in de configuratie van niet meer dan enkele minuten duren. Nadat de SMS-Provider voor de site online is, kunt u uw Configuration Manager-console rechtstreeks naar de site die u wilt beheren kunt herstellen.  

 U kunt de Configuration Manager-console installeren op meerdere computers voor gebruik door gebruikers met beheerdersrechten. Elke SMS-Provider ondersteunt verbindingen van meerdere Configuration Manager-consoles.  

 **Beheerpunt:**  

 Installeer meerdere beheerpunten op elke primaire site en schakel de sites om sitegegevens te publiceren naar Active Directory-infrastructuur en naar DNS.  

 Meerdere beheerpunten helpt bij de taakverdeling van het gebruik van één beheerpunt door meerdere clients. Bovendien kunt u een of meer Databasereplica's voor beheerpunten te verminderen, de bewerkingen met intensief CPU-gebruik van het beheerpunt, en om de beschikbaarheid van deze kritieke sitesysteemrol te verhogen.  

 U kunt slechts één beheerpunt installeren op een secundaire site, zich op de secundaire siteserver bevinden moet, beheerpunten op secundaire sites worden daarom niet beschouwd als over een maximaal beschikbare configuratie te beschikken.  

> [!NOTE]  
>  Apparaten die worden beheerd door beheer van lokale mobiele apparaten verbinding maken met slechts één beheerpunt op een primaire site. Het beheerpunt tijdens de inschrijving door Configuration Manager is toegewezen aan het mobiele apparaat en wordt niet gewijzigd. Wanneer u meerdere beheerpunten installeert en meer dan één voor mobiele apparaten inschakelt, is het beheerpunt dat is toegewezen aan een client voor mobiele apparaten niet-deterministisch.  
>   
>  Als het beheerpunt dat gebruikmaakt van een client voor mobiele apparaten niet beschikbaar is, moet u los het probleem met een beheerpunt of het mobiele apparaat wissen en het mobiele apparaat opnieuw inschrijven zodat deze kan worden toegewezen aan een geactiveerd beheerpunt dat is ingeschakeld voor mobiele apparaten.  

 **Distributiepunt:**  

 Installeer meerdere distributiepunten en implementeer inhoud naar verschillende distributiepunten. U kunt overlappende grensgroepen configureren voor de locatie van inhoud om ervoor te zorgen dat clients op elk subnet toegang hebben tot een implementatie vanuit twee of meer distributiepunten. Ten slotte kunt u overwegen een of meer distributiepunten configureren als terugvallocaties voor inhoud.  

 Zie voor meer informatie over terugvallocaties voor inhoud, [inhoud en -infrastructuur voor System Center Configuration Manager beheert](../../core/servers/deploy/configure/manage-content-and-content-infrastructure.md).  

 **Application Catalog-webservicepunt en Application Catalog-websitepunt:**  

 U kunt één van elk op dezelfde sitesysteemcomputer implementeert, installeren van meerdere exemplaren van elke sitesysteemrol en voor de beste prestaties.  

 Elke Application Catalog-sitesysteemrol biedt dezelfde informatie als andere instanties van die sitesysteemrol, ongeacht de locatie van deze siteserverrol in de hiërarchie. Daarom wanneer een client een aanvraag doet voor de Application Catalog en u hebt geconfigureerd de standaard Application Catalog-website-punt clientinstelling voor apparaten automatisch wordt gedetecteerd, kan de client naar een beschikbare instantie worden omgeleid. De voorkeur wordt gegeven voor lokale Application Catalog sitesysteemservers, op basis van de huidige netwerklocatie van de client.  

 Zie voor meer informatie over deze clientinstelling en de werking van automatische detectie werkt de [Computeragent](../../core/clients/deploy/about-client-settings.md#computer-agent) sectie het [over clientinstellingen in System Center Configuration Manager](../../core/clients/deploy/about-client-settings.md) onderwerp.  

##  <a name="bkmk_client"></a>Maximale beschikbaarheid voor clients  
 **Clientbewerkingen zijn autonoom:**  

 Configuration Manager-clientautonomie omvat het volgende:  

-   Clients hebben geen continu contact met een specifieke sitesysteemserver nodig. Ze gebruiken bekende configuraties om uit te voeren vooraf geconfigureerde acties volgens een planning.  

-   Clients kunnen elke beschikbaar exemplaar van een sitesysteemrol die services aan clients levert gebruiken, en ze zullen proberen om contact op met bekende servers totdat er een beschikbare server wordt gevonden.  

-   Clients kunnen uitvoeren-inventaris, software-implementaties en vergelijkbare geplande acties onafhankelijk van rechtstreeks contact met sitesysteemservers.  

-   Clients die zijn geconfigureerd voor het gebruik van een terugvalstatuspunt kunnen gegevens verzenden naar het terugvalstatuspunt als ze niet kunnen met een beheerpunt communiceren.  

 **Clients kunnen zichzelf herstellen:**  

 Clients verhelpen automatisch de meest voorkomende problemen zonder rechtstreekse interventie van een beheerder:  

-   Van tijd tot tijd clients zelfbeoordeling uit van hun status en maatregelen typische problemen oplossen met behulp van een lokaal cachegeheugen van herstelstappen en bronbestanden voor herstellingen.  

-   Wanneer een client er niet in te dienen statusinformatie naar de site, kan de site een waarschuwing genereren. Gebruikers met beheerdersrechten die deze waarschuwingen ontvangen, kunnen onmiddellijk actie om terug te zetten van de normale werking van de client ondernemen.  

 **Clients slaan informatie op in de toekomst gebruiken:**  

 Wanneer een client met een beheerpunt communiceert, kan de client kan verkrijgen en cache van de volgende informatie:  

-   Clientinstellingen.  

-   Clientschema's.  

-   Informatie over software-implementaties en een download van de software op de client is te installeren, als de implementatie is geconfigureerd voor deze actie gepland.  

 Wanneer een client geen contact met een beheerpunt de clients lokaal cachegeheugen van de status, status en client-gegevens die ze naar de site rapporteren, en vervolgens deze gegevens overgedragen nadat ze contact is gelegd met een beheerpunt.  

 **Client kan de status verzenden naar een terugvalstatuspunt:**  

 Als u een client moet gebruiken, een terugvalstatuspunt configureert, geeft u een extra contactpunt voor de client om belangrijke informatie over de activiteiten ervan te verzenden. Clients die zijn geconfigureerd voor gebruik van een terugvalstatuspunt blijven status van hun activiteiten verzenden naar die sitesysteemrol, zelfs wanneer de client met een beheerpunt communiceren kan.  

 **Centraal beheer van clientgegevens en clientidentiteit:**  

 De sitedatabase, en niet de individuele client bevat belangrijke informatie over de identiteit van elke client en koppelt die gegevens aan een specifieke computer of gebruiker. Dit betekent:  

-   De clientbronbestanden op een computer kunnen worden verwijderd en opnieuw geïnstalleerd zonder gevolg voor de historische records voor de computer waarop de client is geïnstalleerd.  

-   Fout van een clientcomputer heeft geen invloed op de integriteit van de informatie die is opgeslagen in de database. Deze informatie kan beschikbaar blijven voor rapportage.  

##  <a name="bkmk_nonHAoptions"></a>Opties voor sites en sitesysteemrollen die niet maximaal beschikbaar  
 Verschillende sitesystemen bieden geen ondersteuning voor meerdere exemplaren op een site of in de hiërarchie. Deze informatie kan helpen bij het voorbereiden van deze sitesystemen offline gaan.  

 **Siteserver (site):**  

 Configuration Manager biedt geen ondersteuning voor de installatie van de siteserver voor elke site op een Windows Server-cluster of NLB-cluster.  

 De volgende informatie kan helpen bij het voorbereiden van wanneer een siteserver uitvalt of niet operationeel is:  

-   Maak regelmatig een back-up van de site met behulp van de ingebouwde back-uptaak. Een testomgeving Oefen regelmatig in om sites vanuit een back-up te herstellen.  

-   Implementeer meerdere Configuration Manager primaire sites in een hiërarchie met een centrale beheersite om redundantie tot stand. Als u een site uitvalt, overweeg het gebruik van Windows-groepsbeleid of aanmeldscripts te gebruiken voor het opnieuw toewijzen van clients naar een werkende site.  

-   Als u een hiërarchie met een centrale beheersite hebt, kunt u de centrale beheersite of een onderliggende primaire site kunt herstellen met de optie voor een sitedatabase herstellen vanuit een andere site in uw hiërarchie.  

-   Secundaire sites kunnen niet worden hersteld en moeten opnieuw worden geïnstalleerd.  

 **Asset Intelligence-synchronisatiepunt (hiërarchie):**  

 Deze sitesysteemrol is niet als bedrijfskritisch gezien en biedt optionele functionaliteit in Configuration Manager. Als dit sitesysteem offline gaat, gebruikt u een van de volgende opties:  

-   Oplossen van de reden voor het sitesysteem offline zijn.  

-   De rol verwijderen van de huidige server en de rol op een nieuwe server installeren.  

 **Endpoint Protection-punt (hiërarchie):**  

 Deze sitesysteemrol is niet als bedrijfskritisch gezien en biedt optionele functionaliteit in Configuration Manager. Als dit sitesysteem offline gaat, gebruikt u een van de volgende opties:  

-   Oplossen van de reden voor het sitesysteem offline zijn.  

-   De rol verwijderen van de huidige server en de rol op een nieuwe server installeren.  

 **Inschrijvingspunt (site):**  

 Deze sitesysteemrol is niet als bedrijfskritisch gezien en biedt optionele functionaliteit in Configuration Manager. Als dit sitesysteem offline gaat, gebruikt u een van de volgende opties:  

-   Oplossen van de reden voor het sitesysteem offline zijn.  

-   De rol verwijderen van de huidige server en de rol op een nieuwe server installeren.  

 **Inschrijvingsproxypunt (site):**  

 Deze sitesysteemrol is niet als bedrijfskritisch gezien en biedt optionele functionaliteit in Configuration Manager. U kunt echter meerdere exemplaren van deze sitesysteemrol op een site en op meerdere sites in de hiërarchie installeren. Als dit sitesysteem offline gaat, gebruikt u een van de volgende opties:  

-   Oplossen van de reden voor het sitesysteem offline zijn.  

-   De rol verwijderen van de huidige server en de rol op een nieuwe server installeren.  

 Wanneer u meer dan één inschrijvingsproxyserver in een site, gebruikt u een DNS-alias voor de servernaam. Wanneer u deze configuratie gebruikt, DNS round robin enige fouttolerantie en taakverdeling voor wanneer gebruikers hun mobiele apparaten inschrijven biedt.  

 **Terugvalstatuspunt (site of hiërarchie):**  

 Deze sitesysteemrol is niet als bedrijfskritisch gezien en biedt optionele functionaliteit in Configuration Manager. Als dit sitesysteem offline gaat, gebruikt u een van de volgende opties:  

-   Oplossen van de reden voor het sitesysteem offline zijn.  

-   De rol verwijderen van de huidige server en de rol op een nieuwe server installeren. Omdat clients tijdens de clientinstallatie het terugvalstatuspunt toegewezen, moet u bestaande clients voor het gebruik van de systeemserver van de nieuwe site aan te passen.  

### <a name="see-also"></a>Zie tevens  
 [Ondersteunde configuraties voor System Center Configuration Manager](../../core/plan-design/configs/supported-configurations.md)

