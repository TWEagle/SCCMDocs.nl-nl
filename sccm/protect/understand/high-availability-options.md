---
title: Maximale beschikbaarheid
titleSuffix: Configuration Manager
description: Informatie over het implementeren van System Center Configuration Manager met behulp van de opties die een hoge servicebeschikbaarheid mogelijk.
ms.custom: na
ms.date: 10/06/2016
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 1a38421d-24c1-4fef-bf6c-42fce53109ac
caps.latest.revision: "4"
author: Brenduns
ms.author: brenduns
manager: angrobe
ms.openlocfilehash: dd38deccb7fb4fb572fb60519b4084db387baec7
ms.sourcegitcommit: c236214b2fcc13dae7bad96d7fb33f692868191d
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/12/2017
---
# <a name="high-availability-options-for-system-center-configuration-manager"></a>Opties voor hoge beschikbaarheid voor System Center Configuration Manager

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*



U kunt System Center Configuration Manager met behulp van de opties die een hoge servicebeschikbaarheid mogelijk implementeren.   

De opties die ondersteuning bieden voor hoge beschikbaarheid:   

-   Sites ondersteunen meerdere exemplaren van sitesysteemservers die belangrijke services aan clients leveren.  

-   Centrale beheersites en primaire sites ondersteunen de back-up van de sitedatabase. De sitedatabase bevat alle configuraties voor sites en clients en het wordt gedeeld tussen sites in een hiërarchie met een centrale beheersite.  

-   Ingebouwde opties voor site recovery kunnen de downtime van de server verminderen en geavanceerde opties bevatten die het herstel vereenvoudigen wanneer u een hiërarchie hebt met een centrale beheersite.  

-   Clients kunnen normale problemen zonder interventie van een beheerder automatisch worden opgelost.  

-   Sites genereren waarschuwingen over clients die geen recente gegevens dit beheerders dat potentiële problemen verwittigt kunnen worden verzonden.  

-   Configuration Manager bevat verschillende ingebouwde rapporten waarmee u kunt het identificeren van problemen en trends voordat ze problemen worden voor server- of clientbewerkingen.  

 Configuration Manager biedt geen real-service en u moet deze kan werken met enige vertraging worden bijgewerkt gegevens verwacht. Daarom is het onwaarschijnlijk voor de meeste scenario's voor een tijdelijke onderbreking van de service om te worden van een kritiek probleem. Wanneer u uw sites en hiërarchieën met hoge beschikbaarheid in gedachten hebt geconfigureerd, kunt de downtime minimaliseren, autonomie van de bewerkingen onderhouden, en een hoog niveau van de service opgegeven.  

 Bijvoorbeeld, werken Configuration Manager-clients doorgaans autonoom met behulp van bekende schema's en configuraties voor bewerkingen, en schema's om gegevens naar de site voor de verwerking te verzenden.  

-   Wanneer clients geen contact met de site, cache ze gegevens zullen worden verstuurd wanneer ze contact met de site opnemen kunnen.  

-   Clients die geen contact krijgt met de site blijven functioneren door gebruik van de laatst bekende schema's en in de cache opgeslagen gegevens, zoals een eerder gedownloade toepassing die ze moeten uitvoeren of installeren, totdat ze kunnen contact opnemen met de site en nieuw beleid kunnen ontvangen.  

-   De site controleert sitesystemen en clients op periodieke statusupdates en kan waarschuwingen genereren wanneer deze mislukken, om te registreren.  

-   Ingebouwde rapporten bieden inzicht in actieve bewerkingen historische bewerkingen en trends. Configuration Manager ondersteunt ook de status gebaseerde berichten die gegevens bijna in realtime voor lopende bewerkingen geven.  

  Gebruik de informatie in dit onderwerp samen met de informatie in de volgende artikelen:
-   [Aanbevolen hardware](../../core/plan-design/configs/recommended-hardware.md)
-   [Ondersteunde besturingssystemen voor de site system serveres](../../core/plan-design/configs/supported-operating-systems-for-site-system-servers.md)  

-   [Vereisten voor sites en sitesystemen](../../core/plan-design/configs/site-and-site-system-prerequisites.md)


##  <a name="bkmk_snh"></a>Hoge beschikbaarheid voor sites en hiërarchieën  
 **Gebruik een SQL Server-cluster om de sitedatabase te hosten:**  

 Wanneer u een SQL Server-cluster voor de database op een centrale beheersite of primaire site gebruikt, gebruikt u de failover-ondersteuning is ingebouwd in SQL Server.  

 Secundaire sites kunnen geen SQL Server-cluster gebruiken en ondersteunen geen back-up of herstel van hun sitedatabase. Een secundaire site herstellen door de secundaire site vanuit de bovenliggende primaire site opnieuw te installeren.  

 **Een SQL Server AlwaysOn-beschikbaarheidsgroep gebruiken om de sitedatabase te hosten:**  

 Vanaf versie 1602 kunt u SQL Server AlwaysOn-beschikbaarheidsgroepen voor het hosten van de sitedatabase op primaire sites en de centrale beheersite als oplossing voor hoge beschikbaarheid en herstel na noodgevallen. Zie voor meer informatie [SQL Server AlwaysOn voor een maximaal beschikbare sitedatabase voor System Center Configuration Manager](../../core/servers/deploy/configure/sql-server-alwayson-for-a-highly-available-site-database.md).  

 **Een hiërarchie van sites met een centrale beheersite en een of meer onderliggende primaire sites implementeren:**  

 Deze configuratie kan fouttolerantie wanneer uw sites overlappende segmenten van uw netwerk beheren. Deze configuratie biedt bovendien een bijkomende hersteloptie voor het gebruik van de informatie in de gedeelde database op een andere site opnieuw opbouwen van de sitedatabase op de herstelde site. Deze optie kunt u een mislukte of niet-beschikbare back-up van de mislukte sitedatabase te vervangen.  

 **Maak regelmatig back-ups op centrale beheersites en primaire sites:**  

 Wanneer u maken en testen van een regelmatige siteback-up, kunt u ervoor zorgen dat u de gegevens die nodig zijn om een site en de ervaring hebt voor het herstellen van een site in de minimale hoeveelheid tijd te herstellen.  

 **Meerdere exemplaren van sitesysteemrollen installeren:**  

 Wanneer u meerdere exemplaren van kritieke sitesysteemrollen zoals het beheerpunt en distributiepunt installeert, voorziet u overbodige contactpunten van contactpersoon voor clients in het geval dat een specifieke sitesysteemserver offline is.  

 **Meerdere exemplaren van de SMS-Provider op een site installeren:** De SMS-Provider verleent het punt van beheercontact voor een of meer Configuration Manager-consoles. Als u meerdere SMS-providers installeert, kunt u redundantie verlenen aan contactpunten om u site en hiërarchie te beheren.  

##  <a name="bkmk_ssr"></a>Hoge beschikbaarheid voor sitesysteemrollen  
 Op elke site implementeert u sitesysteemrollen om de services die u wilt dat clients gebruiken op deze site te bieden. De sitedatabase bevat de configuratiegegevens voor de site en voor alle clients. Een of meer van de beschikbare opties gebruiken om te bieden voor hoge beschikbaarheid van de sitedatabase en het herstel van de site en sitedatabase, indien nodig.  

 **Redundantie voor belangrijke sitesysteemrollen:**  

-   Application Catalog-webservicepunt  

-   Application Catalog-websitepunt  

-   Distributiepunt  

-   Beheerpunt  

-   Software-updatepunt  

-   Statusmigratiepunt  

 U kunt meerdere exemplaren van de rol Reporting services-punt om redundantie te verlenen voor rapportage over sites en -clients installeren.

 U kunt PowerShell gebruiken voor het installeren van de sitesysteemrol van Software-update-punt op een cluster met Windows Network Load Balancing (NLB) om failover-ondersteuning te bieden  


 **Ingebouwde siteback-up:**  

 Configuration Manager bevat een ingebouwde back-uptaak om u te helpen back-up van uw site en uw kritieke informatie regelmatig. Daarnaast ondersteunt de wizard Setup van Configuration Manager siteherstelacties om u te helpen u de activiteit van een site te herstellen.  

 **Publiceren naar Active Directory Domain Services en DNS:**  

 U kunt elke site om gegevens over sitesysteemservers en -services te publiceren naar Active Directory Domain Services en naar DNS configureren. Hierdoor kunnen clients de meest toegankelijke server op het netwerk te identificeren en te identificeren wanneer nieuwe sitesysteemservers die belangrijke services, zoals beheerpunten, kunnen bieden beschikbaar zijn.  

 **SMS-Provider en Configuration Manager-console:**  

 Configuration Manager ondersteunt de installatie van meerdere SMS-Providers, elk op een afzonderlijke computer, zodat meerdere toegangspunten voor de Configuration Manager-console. Dit zorgt ervoor dat als een SMS-providercomputer offline is, u de mogelijkheid behoudt om te bekijken en Configuration Manager-sites en clients configureren.  

 Wanneer een Configuration Manager-console verbinding met een site maakt, wordt deze verbinding maakt met een exemplaar van de SMS-Provider op die site. Het exemplaar van de SMS-Provider is niet-deterministisch geselecteerd. Als de geselecteerde SMS-Provider niet beschikbaar is, hebt u de volgende opties:  

-   Verbind de console naar de site opnieuw. Elke nieuwe verbindingsaanvraag is niet-deterministisch een exemplaar van de SMS-Provider toegewezen en is het mogelijk dat op de nieuwe verbinding een beschikbaar exemplaar zal worden toegewezen.  

-   Verbind de console met een andere Configuration Manager-site en beheer van de configuratie vanuit die verbinding. Dit introduceert een lichte vertraging van wijzigingen in de configuratie van niet meer dan een paar minuten. Nadat de SMS-Provider voor de site online is, kunt u uw Configuration Manager-console rechtstreeks naar de site die u wilt beheren kunt herstellen.  

 U kunt de Configuration Manager-console installeren op meerdere computers voor gebruik door gebruikers met beheerdersrechten. Elke SMS-Provider ondersteunt verbindingen van meerdere Configuration Manager-consoles.  

 **Beheerpunt:**  

 Installeer meerdere beheerpunten op elke primaire site en schakel de sites om sitegegevens te publiceren naar Active Directory-infrastructuur en naar DNS.  

 Meerdere beheerpunten helpt lastenverdeling in het gebruik van één beheerpunt door meerdere clients. Bovendien kunt u een of meer Databasereplica's voor beheerpunten verminderen de CPU-intensieve bewerkingen van het beheerpunt en verhoogt de beschikbaarheid van deze kritieke sitesysteemrol installeren.  

 Omdat u slechts één beheerpunt in een secundaire site installeren kunt, zich op de secundaire siteserver bevinden moet, beheerpunten op secundaire sites worden niet beschouwd als een maximaal beschikbare configuratie.  

> [!NOTE]  
>  Apparaten die worden beheerd door on-premises-beheer voor mobiele apparaten verbinding maken met slechts één beheerpunt op een primaire site. Het beheerpunt tijdens de inschrijving door Configuration Manager is toegewezen aan het mobiele apparaat en wordt niet gewijzigd. Wanneer u meerdere beheerpunten installeert en meer dan één voor mobiele apparaten inschakelen, is het beheerpunt dat is toegewezen aan een client voor mobiele apparaten niet-deterministisch.  
>   
>  Als het beheerpunt dat gebruikmaakt van een client voor mobiele apparaten niet beschikbaar is, moet u los het probleem met dat beheerpunt of het mobiele apparaat wissen en het mobiele apparaat opnieuw inschrijven zodat deze kan worden toegewezen aan een geactiveerd beheerpunt dat ingeschakeld is voor mobiele apparaten.  

 **Distributiepunt:**  

 Installeer meerdere distributiepunten en implementeer inhoud naar meerdere distributiepunten. U kunt overlappende grensgroepen configureren voor de locatie van inhoud om ervoor te zorgen dat clients op elk subnet toegang krijgen een implementatie uit twee of meer distributiepunten tot. Ten slotte kunt u overwegen een of meer distributiepunten configureren als terugvallocaties voor inhoud.  

 Zie voor meer informatie over terugvallocaties voor inhoud, [inhoud en infrastructuur voor System Center Configuration Manager beheren](../../core/servers/deploy/configure/manage-content-and-content-infrastructure.md).  

 **Application Catalog-webservicepunt en Application Catalog-websitepunt:**  

 U kunt meerdere exemplaren van elke sitesysteemrol en voor de beste prestaties installeren, één van elk op dezelfde sitesysteemcomputer implementeert.  

 Elke Application Catalog-sitesysteemrol biedt dezelfde informatie als andere instanties van die sitesysteemrol, ongeacht de locatie van deze siteserverrol in de hiërarchie. Daarom wanneer een client een aanvraag doet voor de Application Catalog en u hebt geconfigureerd de standaard Application Catalog-website-punt clientinstelling voor apparaten automatisch detecteren, kan de client naar een beschikbare instantie worden omgeleid. De voorkeur wordt gegeven voor lokale Application Catalog sitesysteemservers, op basis van de huidige netwerklocatie van de client.  

 Zie voor meer informatie over deze clientinstelling en de werking van automatische detectie werkt, de [Computeragent](../../core/clients/deploy/about-client-settings.md#computer-agent) sectie het [over clientinstellingen in System Center Configuration Manager](../../core/clients/deploy/about-client-settings.md) onderwerp.  

##  <a name="bkmk_client"></a>Hoge beschikbaarheid voor clients  
 **Clientbewerkingen zijn autonoom:**  

 Configuration Manager-clientautonomie omvat het volgende:  

-   Clients hebben geen continu contact met een specifieke sitesysteemserver nodig. Ze gebruiken bekende configuraties om uit te voeren van vooraf geconfigureerde acties volgens een schema.  

-   Clients kunnen elke beschikbaar exemplaar van een sitesysteemrol die services aan clients levert gebruiken, en ze zullen proberen om contact op met bekende servers totdat een beschikbare server zich bevindt.  

-   Clients kunnen uitvoeren-inventarisatie, software-implementaties en vergelijkbare geplande acties onafhankelijk van rechtstreeks contact met sitesysteemservers.  

-   Clients die zijn geconfigureerd voor het gebruik van een terugvalstatuspunt kunnen gegevens verzenden naar het terugvalstatuspunt wanneer ze niet kunnen met een beheerpunt communiceren.  

 **Clients kunnen zichzelf herstellen:**  

 Meest voorkomende problemen zonder rechtstreekse interventie van een beheerder wordt automatisch hersteld door clients:  

-   Clients worden regelmatig zelf evalueren hun status en onderneem actie typische problemen oplossen met behulp van een lokale cache herstelstappen en bronbestanden voor reparaties.  

-   De site kan een waarschuwing kan genereren wanneer een client mislukt statusinformatie naar de site verzenden. Gebruikers met beheerdersrechten die deze waarschuwingen ontvangen, kunnen onmiddellijk actie te herstellen van de normale werking van de client ondernemen.  

 **Informatie over het gebruik in de toekomst in het cachegeheugen:**  

 Wanneer een client met een beheerpunt communiceert, kan de client kan verkrijgen en de volgende informatie in de cache:  

-   Clientinstellingen.  

-   Clientschema's.  

-   Informatie over software-implementaties en downloaden van een van de software van de client is te installeren, wanneer de implementatie is geconfigureerd voor deze actie gepland.  

 Wanneer een client kan geen verbinding maken met een beheerpunt de clients lokaal cache de status, status en client-gegevens die ze naar de site rapporteren, en deze gegevens overgedragen nadat ze contact met een beheerpunt tot stand brengen.  

 **Client kan de status verzenden naar een terugvalstatuspunt:**  

 Wanneer u een client een terugvalstatuspunt configureert, kunt u een extra contactpunt voor de client verzenden van belangrijke informatie over de werking ervan opgeven. Clients die zijn geconfigureerd voor gebruik van een terugvalstatuspunt blijven status van hun activiteiten verzenden naar die sitesysteemrol, zelfs wanneer de client niet kan met een beheerpunt communiceren.  

 **Centraal beheer van clientgegevens en clientidentiteit:**  

 De sitedatabase in plaats van de individuele client bevat belangrijke informatie over de identiteit van de client en koppelt die gegevens op een specifieke computer of gebruiker. Dit betekent dat:  

-   De clientbronbestanden op een computer kunnen worden verwijderd en opnieuw geïnstalleerd zonder de historische records voor de computer waarop de client is geïnstalleerd.  

-   Fout van een clientcomputer heeft geen invloed op de integriteit van de informatie die is opgeslagen in de database. Deze informatie kan beschikbaar blijven voor rapportage.  

##  <a name="bkmk_nonHAoptions"></a>Opties voor sites en sitesysteemrollen die niet maximaal beschikbaar  
 Verschillende sitesystemen bieden geen ondersteuning voor meerdere exemplaren op een site of in de hiërarchie. Deze informatie kunt u deze sitesystemen offline gaan voorbereiden.  

 **Siteserver (site):**  

 Configuration Manager biedt geen ondersteuning voor de installatie van de siteserver voor elke site op een Windows Server-cluster of NLB-cluster.  

 De volgende informatie kunt u als een siteserver uitvalt of niet operationeel is voorbereiden:  

-   Gebruik de ingebouwde back-uptaak Maak regelmatig een back-up van de site. In een testomgeving regelmatig practice sites terugzetten vanuit een back-up.  

-   Implementeer meerdere Configuration Manager primaire sites in een hiërarchie met een centrale beheersite om redundantie tot stand. Als u een site uitvalt ondervindt, kunt u overwegen Windows-groep of aanmeldscripts te gebruiken op het opnieuw toewijzen van clients naar een werkende site.  

-   Als u een hiërarchie met een centrale beheersite hebt, kunt u de centrale beheersite of een onderliggende primaire site kunt herstellen met behulp van de optie voor het herstellen van een sitedatabase van een andere site in uw hiërarchie.  

-   Secundaire sites kunnen niet worden hersteld en opnieuw moeten worden geïnstalleerd.  

 **Asset Intelligence-synchronisatiepunt (hiërarchie):**  

 Deze sitesysteemrol wordt niet als bedrijfskritisch gezien en biedt optionele functionaliteit in Configuration Manager. Als dit sitesysteem offline gaat, gebruikt u een van de volgende opties:  

-   Los de oorzaak van het sitesysteem offline zijn.  

-   De rol niet verwijderen van de huidige server en de functie installeren op een nieuwe server.  

 **Endpoint Protection-punt (hiërarchie):**  

 Deze sitesysteemrol wordt niet als bedrijfskritisch gezien en biedt optionele functionaliteit in Configuration Manager. Als dit sitesysteem offline gaat, gebruikt u een van de volgende opties:  

-   Los de oorzaak van het sitesysteem offline zijn.  

-   De rol niet verwijderen van de huidige server en de functie installeren op een nieuwe server.  

 **Inschrijvingspunt (site):**  

 Deze sitesysteemrol wordt niet als bedrijfskritisch gezien en biedt optionele functionaliteit in Configuration Manager. Als dit sitesysteem offline gaat, gebruikt u een van de volgende opties:  

-   Los de oorzaak van het sitesysteem offline zijn.  

-   De rol niet verwijderen van de huidige server en de functie installeren op een nieuwe server.  

 **Inschrijvingsproxypunt (site):**  

 Deze sitesysteemrol wordt niet als bedrijfskritisch gezien en biedt optionele functionaliteit in Configuration Manager. U kunt echter meerdere exemplaren van deze sitesysteemrol op een site en op meerdere sites in de hiërarchie installeren. Als dit sitesysteem offline gaat, gebruikt u een van de volgende opties:  

-   Los de oorzaak van het sitesysteem offline zijn.  

-   De rol niet verwijderen van de huidige server en de functie installeren op een nieuwe server.  

 Wanneer u meer dan één inschrijvingsproxyserver in een site hebt, gebruikt u een DNS-alias voor de servernaam. Wanneer u deze configuratie gebruikt, DNS round robin enige fouttolerantie en taakverdeling voor wanneer gebruikers hun mobiele apparaten inschrijven biedt.  

 **Terugvalstatuspunt (site of hiërarchie):**  

 Deze sitesysteemrol wordt niet als bedrijfskritisch gezien en biedt optionele functionaliteit in Configuration Manager. Als dit sitesysteem offline gaat, gebruikt u een van de volgende opties:  

-   Los de oorzaak van het sitesysteem offline zijn.  

-   De rol niet verwijderen van de huidige server en de functie installeren op een nieuwe server. Omdat clients worden toegewezen aan het terugvalstatuspunt tijdens de clientinstallatie, moet u bestaande clients voor het gebruik van de nieuwe sitesysteemserver te wijzigen.  

### <a name="see-also"></a>Zie tevens  
 [Ondersteunde configuraties voor System Center Configuration Manager](../../core/plan-design/configs/supported-configurations.md)
