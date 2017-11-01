---
title: Verwijzing voor onderhoudstaken
titleSuffix: Configuration Manager
description: Lees meer informatie voor elk van de onderhoudstaken voor System Center Configuration Manager-site en of deze taken zijn standaard ingeschakeld.
ms.custom: na
ms.date: 3/8/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 68dc6acd-5848-47a4-b4c1-ffa40e47890b
caps.latest.revision: "16"
caps.handback.revision: "0"
author: Brenduns
ms.author: brenduns
manager: angrobe
ms.openlocfilehash: 6cff26b689b3fb1139d235295530faa9d30f9bf6
ms.sourcegitcommit: c236214b2fcc13dae7bad96d7fb33f692868191d
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/12/2017
---
# <a name="reference-for-maintenance-tasks-for-system-center-configuration-manager"></a>Verwijzing voor onderhoudstaken voor System Center Configuration Manager

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*

Dit onderwerp bevat informatie over elk van de onderhoudstaken voor System Center Configuration Manager-site voor en geeft u op welke site waarin de taak beschikbaar is. Elk item wordt tevens aangegeven als de taak is ingeschakeld of niet standaard ingeschakeld. Zie voor meer informatie over het plannen en configureren van sites voor het uitvoeren van onderhoudstaken [onderhoudstaken voor System Center Configuration Manager](../../../core/servers/manage/maintenance-tasks.md).  

**Back-upserver van Site**: Gebruik deze taak om voor te bereiden voor het herstel van essentiële gegevens. U kunt een back-up van uw kritieke informatie voor het herstellen van een site en de Configuration Manager-database maken. Zie voor meer informatie [back-up en herstel voor System Center Configuration Manager](../../../protect/understand/backup-and-recovery.md).  

-   **Centrale beheersite**: Ingeschakeld    
-   **Primaire site**: Niet ingeschakeld    
-   Secundaire site: Niet beschikbaar  

**Titel van toepassing met Inventarisinformatie controleren**: Gebruik deze taak voor het handhaven van de consistentie tussen softwaretitels die worden gerapporteerd in de software-inventaris en de softwaretitels in de Asset Intelligence-catalogus. Zie [Inleiding op Asset Intelligence in System Center Configuration Manager](../../../core/clients/manage/asset-intelligence/introduction-to-asset-intelligence.md) voor meer informatie.  

-   **Centrale beheersite**: Ingeschakeld    
-   **Primaire site**: Ingeschakeld    
-   Secundaire site: Niet beschikbaar  

**Installatievlag wissen**: Gebruik deze taak voor de geïnstalleerde vlag te verwijderen voor clients die geen Heartbeat-detectierecord tijdens verzenden de **Clientdetectie** periode. De geïnstalleerde vlag voorkomt automatische push-clientinstallatie naar een computer waarop mogelijk een actieve Configuration Manager-client.  

-   Centrale beheersite: Niet beschikbaar    
-   **Primaire site**: Niet ingeschakeld    
-   Secundaire site: Niet beschikbaar  

**Verouderde gegevens van aanvragen van toepassing verwijderen**: Gebruik deze taak voor het verwijderen van verouderde toepassingsaanvragen uit de database. Zie voor meer informatie over toepassingsaanvragen [maken en implementeren van een toepassing met System Center Configuration Manager](/sccm/apps/get-started/create-and-deploy-an-application).  

-   Centrale beheersite: Niet beschikbaar
-   **Primaire site**: Ingeschakeld    
-   Secundaire site: Niet beschikbaar  

**Verouderde Client downloadgeschiedenis**: Gebruik deze taak te verwijderen van historische gegevens over de download-bron die door clients gebruikt. Downloaden van informatie van gegevensbron wordt gebruikt voor het vullen van de [Clientgegevensbronnen dashboard](/sccm/core/servers/deploy/configure/monitor-content-you-have-distributed#client-data-sources-dashboard).  
-  Centrale beheersite-niet beschikbaar
-    **Primaire site** - Ingeschakeld
-  Secundaire site - Niet beschikbaar

**Verouderde Clientbewerkingen verwijderen**: Gebruik deze taak voor het verwijderen van alle verouderde gegevens voor clientbewerkingen uit de sitedatabase. Dit omvat bijvoorbeeld gegevens voor verouderde of verlopen clientmeldingen (zoals downloadaanvragen voor computer- of gebruikersbeleid) en voor Endpoint Protection (zoals aanvragen door een gebruiker met beheerdersrechten om clients bijgewerkte definities te laten scannen of downloaden).

-   **Centrale beheersite**: Ingeschakeld    
-   **Primaire site**: Ingeschakeld    
-   Secundaire site: Niet beschikbaar  

**Verouderde Clientaanwezigheidsgeschiedenis verwijderen**: Gebruik deze taak te verwijderen van de van geschiedenisinformatie over de onlinestatus van clients (geregistreerd via clientmeldingen) dat ouder is dan de opgegeven tijd. Zie [Clients controleren in System Center Configuration Manager](../../../core/clients/manage/monitor-clients.md) voor meer informatie over clientmeldingen.  

-   **Centrale beheersite**: Ingeschakeld   
-   **Primaire site**: Ingeschakeld    
-   Secundaire site: Niet beschikbaar  

**Verwijderen van verouderde Cloud Management Gateway-verkeersgegevens**: Gebruik deze taak voor het verwijderen van alle verouderde gegevens over het verkeer dat wordt doorgegeven via de [management cloudgateway](/sccm/core/clients/manage/plan-cloud-management-gateway) uit de sitedatabase. Dit omvat bijvoorbeeld gegevens over het aantal aanvragen, totale aanvraag bytes totale reactietijd bytes, aantal mislukte aanvragen en maximum aantal gelijktijdige aanvragen.  
- **Centrale beheersite** - Ingeschakeld
- **Primaire site** - Ingeschakeld
- Secundaire site - Niet beschikbaar


**Verouderde verzamelde bestanden verwijderen**: Gebruik deze taak verouderde informatie over verzamelde bestanden verwijderen uit de database. Deze taak verwijdert tevens de verzamelde bestanden uit de siteservermapstructuur op de geselecteerde site. Standaard de vijf meest recente kopieën van verzamelde bestanden worden opgeslagen op de siteserver in de **Inboxes\sinv.box\FileCol** directory. Zie voor meer informatie [Inleiding tot software-inventaris in System Center Configuration Manager](/sccm/core/clients/manage/inventory/introduction-to-software-inventory).  

-   Centrale beheersite: Niet beschikbaar    
-   **Primaire site**: Ingeschakeld    
-   Secundaire site: Niet beschikbaar  

**Verouderde gegevens van computerkoppeling verwijderen**: Gebruik deze taak worden verouderde computerkoppelingsgegevens voor Besturingssysteemimplementatie uit de database verwijderd. Deze informatie wordt gebruikt bij het voltooien van herstelbewerkingen voor gebruikersstatussen. Zie [De gebruikersstatus beheren in System Center Configuration Manager](../../../osd/get-started/manage-user-state.md) voor meer informatie over computerkoppelingen.  

-   Centrale beheersite: Niet beschikbaar    
-   **Primaire site**: Ingeschakeld    
-   Secundaire site: Niet beschikbaar  

**Verwijderen van gegevens van Verwijderingsdetectie verwijderen**: Gebruik deze taak worden verouderde gegevens verwijderd uit de database die is gemaakt via Extractieweergaven. Extractieweergaven zijn standaard uitgeschakeld. U alleen inschakelen deze met behulp van de Configuration Manager-SDK. Deze taak verwijdert alleen gegevens als er extractieweergaven zijn ingeschakeld.  

-   **Centrale beheersite**: Ingeschakeld    
-   **Primaire site**: Ingeschakeld    
-   Secundaire site: Niet beschikbaar  

**Verouderde Record van apparaat wissen verwijderen**: Gebruik deze taak worden verouderde gegevens over wisbewerkingen voor mobiele apparaten uit de database verwijderd. Zie voor meer informatie over het wissen van mobiele apparaten [gegevens beschermen met wissen op afstand, vergrendelen of wachtwoordcodeherstel via System Center Configuration Manager](/sccm/mdm/deploy-use/wipe-lock-reset-devices).  

-   Centrale beheersite: Niet beschikbaar    
-   **Primaire site**: Ingeschakeld    
-   Secundaire site: Niet beschikbaar  

**Verouderde apparaten die worden beheerd door de Exchange Server-Connector verwijderen**: Gebruik deze taak om verouderde gegevens over mobiele apparaten die worden beheerd via de Exchange Server-connector te verwijderen. Deze gegevens worden verwijderd volgens het interval dat is geconfigureerd voor de **mobiele apparaten negeren die langer dan (dagen) inactief zijn** kiezen op de **detectie** tabblad van de eigenschappen van de Exchange Server-connector. Zie [Mobiele apparaten beheren met System Center Configuration Manager en Exchange](../../../mdm/deploy-use/manage-mobile-devices-with-exchange-activesync.md) voor meer informatie.  

-   Centrale beheersite: Niet beschikbaar   
-   **Primaire site**: Ingeschakeld    
-   Secundaire site: Niet beschikbaar  

**Verouderde Detectiegegevens verwijderen**: Gebruik deze taak verouderde detectiegegevens verwijderen uit de database. Deze gegevens kunnen records die het gevolg zijn van heartbeat-detectie, netwerkdetectie en Active Directory Domain Services-detectiemethoden (systeem, gebruiker en groep) bevatten. Gegevens die zijn gekoppeld aan een site worden verwijderd wanneer deze taak wordt uitgevoerd op die site, en deze wijzigingen worden gerepliceerd naar andere sites. Zie [Detectie uitvoeren voor System Center Configuration Manager](../../../core/servers/deploy/configure/run-discovery.md) voor informatie over Discovery.  

-   Centrale beheersite: Niet beschikbaar    
-   **Primaire site**: Ingeschakeld    
-   Secundaire site: Niet beschikbaar  

**Verouderde gebruiksgegevens van distributiepunten verwijderen**: Gebruik deze taak verwijdert uit de database verouderde gegevens voor distributiepunten die langer dan een opgegeven periode zijn opgeslagen.  

-   **Centrale beheersite**: Ingeschakeld    
-   **Primaire site**: Ingeschakeld    
-   Secundaire site: Niet beschikbaar  

**Verouderde Endpoint Protection gegevens van geschiedenis status**: Gebruik deze taak voor het verwijderen van verouderde statusinformatie voor Endpoint Protection uit de database. Zie [Endpoint Protection in System Center Configuration Manager controleren](../../../protect/deploy-use/monitor-endpoint-protection.md) voor meer informatie over de Endpoint Protection-statusinformatie.  

-   Centrale beheersite: Niet beschikbaar    
-   **Primaire site**: Ingeschakeld    
-   Secundaire site: Niet beschikbaar  

**Verouderde geregistreerde apparaten verwijderen**: Vanaf de update voor 1602 is is deze taak standaard uitgeschakeld. U kunt deze taak gebruiken om te verwijderen uit de sitedatabase verouderde gegevens over mobiele apparaten die nog niet gerapporteerd gedurende een opgegeven periode geen informatie aan de site.

Deze taak is van toepassing op apparaten die zijn geregistreerd met Microsoft Intune (hybride) of Configuration Manager on-premises beheer van mobiele apparaten. Zie voor meer informatie over de besturingssystemen van apparaten die zijn geregistreerd met behulp van Configuration Manager of Intune de [mobiele apparaten die zijn geregistreerd door Microsoft Intune](../../../core/plan-design/configs/supported-operating-systems-for-clients-and-devices.md#mobile-devices-enrolled-by-microsoft-intune) in sectie [ondersteunde besturingssystemen voor clients en apparaten voor System Center Configuration Manager](../../../core/plan-design/configs/supported-operating-systems-for-clients-and-devices.md).

-   Centrale beheersite: Niet beschikbaar    
-   **Primaire site**: Niet ingeschakeld    
-   Secundaire site: Niet beschikbaar  

**Verouderde Inventarisgeschiedenis verwijderen**: Gebruik deze taak om inventarisgegevens die langer dan een opgegeven periode uit de database zijn opgeslagen te verwijderen. Zie [Resource Explorer gebruiken om de hardware-inventaris in System Center Configuration Manager te bekijken](../../../core/clients/manage/inventory/use-resource-explorer-to-view-hardware-inventory.md) voor informatie over de inventarisgeschiedenis.  

-   Centrale beheersite: Niet beschikbaar    
-   **Primaire site**: Ingeschakeld    
-   Secundaire site: Niet beschikbaar  

**Verouderde logboekgegevens verwijderen**: Gebruik deze taak om verouderde logboekgegevens die wordt gebruikt voor het oplossen van problemen uit de database te verwijderen. Deze gegevens is niet gerelateerd aan de bewerkingen van de Configuration Manager-onderdeel.  

> [!IMPORTANT]  
> Deze taak wordt standaard dagelijks op elke site uitgevoerd. Op een centrale beheersite en primaire sites verwijdert deze taak gegevens die ouder zijn dan 30 dagen. Wanneer u SQL Server Express op een secundaire site gebruikt, zorg ervoor dat deze taak dagelijks wordt uitgevoerd en verwijdert deze gegevens die zeven dagen inactief is geweest.  

-   **Centrale beheersite**: Ingeschakeld    
-   **Primaire site**: Ingeschakeld    
-   **Secundaire site**: Ingeschakeld  

**Verouderde Meldingstakengeschiedenis verwijderen**: Gebruik deze taak om informatie te verwijderen over clientmeldingstaken uit de sitedatabase wanneer deze gedurende een opgegeven periode nog niet is bijgewerkt. Zie voor meer informatie over clientmeldingen [clientimplementatietaken voor System Center Configuration Manager](../../../core/clients/manage/monitor-clients.md).  

-   Centrale beheersite: Niet beschikbaar    
-   **Primaire site**: Ingeschakeld    
-   Secundaire site: Niet beschikbaar  

**Verouderde Replicatieoverzichtsgegevens verwijderen**: Gebruik deze taak verouderde replicatieoverzichtsgegevens verwijderen uit de sitedatabase wanneer deze gedurende een opgegeven periode nog niet is bijgewerkt. Meer informatie kunt u vinden in de sectie [Databasereplicatiekoppelingen en de replicatiestatus bewaken](../../../core/servers/manage/monitor-hierarchy-and-replication-infrastructure.md#BKMK_MonitorRepLinksAndStatuss) in het onderwerp [Hiërarchie- en replicatie-infrastructuur bewaken in System Center Configuration Manager](../../../core/servers/manage/monitor-hierarchy-and-replication-infrastructure.md).  

-   **Centrale beheersite**: Ingeschakeld    
-   **Primaire site**: Ingeschakeld    
-   **Secundaire site**: Ingeschakeld  

**Verouderde Wachtwoordcoderecords verwijderen**: Gebruik deze taak op het hoogste niveau van uw hiërarchie om verouderde gegevens van wachtwoordcode opnieuw instellen voor Android en Windows Phone-apparaten te verwijderen. Gegevens van de wachtwoordcode opnieuw instellen is versleuteld, maar bevatten wel de PINCODE voor apparaten. Standaard is deze taak is ingeschakeld en worden de gegevens die ouder is dan één dag verwijderd.  

-   **Centrale beheersite**: Ingeschakeld    
-   **Primaire site**: Ingeschakeld    
-   Secundaire site: Niet beschikbaar  

**Verouderde gegevens het volgen van replicaties**: Gebruik deze taak om verouderde gegevens over databasereplicatie tussen sites van Configuration Manager uit de database te verwijderen. Wanneer u de configuratie van deze onderhoudstaak wijzigt, geldt de configuratie voor elke toepasselijke site in de hiërarchie. Meer informatie kunt u vinden in de sectie [Databasereplicatiekoppelingen en de replicatiestatus bewaken](../../../core/servers/manage/monitor-hierarchy-and-replication-infrastructure.md#BKMK_MonitorRepLinksAndStatuss) in het onderwerp [Hiërarchie- en replicatie-infrastructuur bewaken in System Center Configuration Manager](../../../core/servers/manage/monitor-hierarchy-and-replication-infrastructure.md).  

-   **Centrale beheersite**: Ingeschakeld    
-   **Primaire site**: Ingeschakeld    
-   **Secundaire site**: Ingeschakeld  

**Verouderde gegevens van Softwaremeter verwijderen**: Gebruik deze taak om verouderde gegevens voor softwarelicentiecontrole die langer dan een opgegeven periode uit de database zijn opgeslagen te verwijderen. Zie [Softwarelicentiecontrole in System Center Configuration Manager](../../../apps/deploy-use/monitor-app-usage-with-software-metering.md) voor meer informatie.  

-   Centrale beheersite: Niet beschikbaar    
-   **Primaire site**: Ingeschakeld    
-   Secundaire site: Niet beschikbaar  

**Verouderde samenvattingsgegevens van Softwaremeter verwijderen**: Gebruik deze taak te verwijderen van verouderde samenvattingsgegevens voor softwarelicentiecontrole die langer dan een opgegeven periode uit de database zijn opgeslagen. Zie [Softwarelicentiecontrole in System Center Configuration Manager](../../../apps/deploy-use/monitor-app-usage-with-software-metering.md) voor meer informatie.  

-   Centrale beheersite: Niet beschikbaar    
-   **Primaire site**: Ingeschakeld    
-   Secundaire site: Niet beschikbaar  

**Verouderde statusberichten verwijderen**: Gebruik deze taak te verwijderen van verouderde statusberichtgegevens zoals deze in statusfilterregels uit de database geconfigureerd. Voor meer informatie, Zie de sectie 'Bewaken het statussysteem van Configuration Manager' in het onderwerp [waarschuwingen en het statussysteem voor System Center Configuration Manager gebruiken](../../../core/servers/manage/use-alerts-and-the-status-system.md).  

-   **Centrale beheersite**: Ingeschakeld    
-   **Primaire site**: Ingeschakeld    
-   Secundaire site: Niet beschikbaar  

**Verouderde Bedreigingsgegevens verwijderen**: Gebruik deze taak om verouderde Endpoint Protection-bedreigingsgegevens die langer dan een opgegeven periode uit de database zijn opgeslagen te verwijderen. Zie [Endpoint Protection in System Center Configuration Manager controleren](../../../protect/deploy-use/endpoint-protection.md) voor informatie over Endpoint Protection.  

-   Centrale beheersite: Niet beschikbaar    
-   **Primaire site**: Ingeschakeld    
-   Secundaire site: Niet beschikbaar  

**Verouderde onbekende Computers verwijderen**: Gebruik deze taak om informatie te verwijderen over onbekende computers uit de sitedatabase wanneer deze gedurende een opgegeven periode nog niet is bijgewerkt. Zie [Voorbereiden op onbekende computerimplementaties in System Center Configuration Manager](../../../osd/get-started/prepare-for-unknown-computer-deployments.md) voor meer informatie.  

-   Centrale beheersite: Niet beschikbaar    
-   **Primaire site**: Ingeschakeld    
-   Secundaire site: Niet beschikbaar  

**Verouderde gegevens Apparaataffiniteit voor gebruikers verwijderen**: Gebruik deze taak worden verouderde gegevens van affiniteit van gebruikersapparaat verwijderd uit de database. Zie [Gebruikers en apparaten koppelen met affiniteit tussen gebruikers en apparaten in System Center Configuration Manager](../../../apps/deploy-use/link-users-and-devices-with-user-device-affinity.md) voor meer informatie.  

-   Centrale beheersite: Niet beschikbaar    
-   **Primaire site**: Ingeschakeld    
-   Secundaire site: Niet beschikbaar  

**Verwijder verlopen MDM-Bulkinschrijvingspakket-pakket Records**: Gebruik deze taak voor het verwijderen van oude Bulkinschrijving certificaten en de bijbehorende profielen nadat de van het inschrijvingscertificaat is verlopen. Zie voor meer informatie [certificaatprofielen maken](/sccm/protect/deploy-use/create-certificate-profiles).
-   **Centrale beheersite**: Ingeschakeld
-   **Primaire site**: Ingeschakeld
-   Secundaire Site: Niet beschikbaar

**Niet-actieve Clientdetectiegegevens verwijderen**: Gebruik deze taak te verwijderen van detectiegegevens voor inactieve clients uit de database. Clients worden als inactief gemarkeerd wanneer de client wordt gevlagd als verouderd en via configuraties die voor clientstatus worden gedaan.

Deze taak werkt alleen op bronnen die Configuration Manager-clients. Dit is anders dan de **verouderde Detectiegegevens verwijderen** verouderde detectiegegevensrecords van taak, die worden verwijderd. Wanneer deze taak op één site wordt uitgevoerd, verwijdert deze gegevens uit de database op alle sites in een hiërarchie. Zie [De clientstatus configureren in System Center Configuration Manager](../../../core/clients/deploy/configure-client-status.md) voor meer informatie.  

> [!IMPORTANT]  
> Wanneer deze ingeschakeld, configureert u deze taak moet worden uitgevoerd bij een interval dat groter is dan de **Heartbeat-detectie** planning. Hierdoor kunnen actieve clients voor het verzenden van een record met Heartbeat-detectie waarmee hun clientrecord als actief wordt gemarkeerd, zodat deze taak ze niet verwijdert.  

-   Centrale beheersite: Niet beschikbaar    
-   **Primaire site**: Niet ingeschakeld    
-   Secundaire site: Niet beschikbaar  

**Verouderde waarschuwingen verwijderen**: Gebruik deze taak om verlopen waarschuwingen die langer dan een opgegeven periode uit de database zijn opgeslagen te verwijderen. Zie [Waarschuwingen en het statussysteem voor System Center Configuration Manager gebruiken](../../../core/servers/manage/use-alerts-and-the-status-system.md) voor meer informatie.  

-   **Centrale beheersite**: Ingeschakeld    
-   **Primaire site**: Ingeschakeld    
-   Secundaire site: Niet beschikbaar  

**Verouderde Clientdetectiegegevens verwijderen**: Gebruik deze taak voor het verwijderen van verouderde clientrecords uit de database. Een record die als verouderd is gemarkeerd, is gewoonlijk vervangen door een nieuwere record voor dezelfde client. De nieuwe record wordt de huidige record van de client. Zie [Detectie uitvoeren voor System Center Configuration Manager](../../../core/servers/deploy/configure/run-discovery.md) voor informatie over Discovery.  

> [!IMPORTANT]  
> Wanneer deze ingeschakeld, configureert u deze taak moet worden uitgevoerd bij een interval dat groter is dan de planning voor Heartbeat-detectie. De client wordt hierdoor in staat gesteld om een Heartbeat-detectierecord te verzenden waarmee de status verouderd correct wordt ingesteld.  

-   Centrale beheersite: Niet beschikbaar    
-   **Primaire site**: Niet ingeschakeld    
-   Secundaire site: Niet beschikbaar  

**Verouderde Forestdetectiesites en -Subnets verwijderen**: Gebruik deze taak om gegevens over Active Directory-sites, subnetten en domeinen die nog niet is gedetecteerd door de Active Directory Forest Discovery-methode in de afgelopen 30 dagen te verwijderen. Deze taak verwijdert de detectiegegevens, maar heeft geen invloed op grenzen die van deze detectiegegevens zijn gemaakt. Zie [Detectie uitvoeren voor System Center Configuration Manager](../../../core/servers/deploy/configure/run-discovery.md) voor meer informatie.  

-   **Centrale beheersite**: Ingeschakeld    
-   **Primaire site**: Ingeschakeld    
-   Secundaire site: Niet beschikbaar  

**Zwevende statusrecords voor clientimplementatie verwijderen**: Gebruik deze taak voor het periodiek opschonen van de tabel met informatie over de status van de client-implementatie. Deze taak wordt verouderde of buiten gebruik gestelde apparaten gekoppeld records opschonen.  
-   **Centrale beheersite**: Ingeschakeld    
-   **Primaire site**: Ingeschakeld    
-   Secundaire site: Niet beschikbaar

**Ongebruikte revisies van toepassing verwijderen**: Gebruik deze taak om toepassingsrevisies die niet meer worden verwezen te verwijderen. Zie [Toepassingen herzien en vervangen in System Center Configuration Manager](../../../apps/deploy-use/revise-and-supersede-applications.md) voor meer informatie.  

-   Centrale beheersite: Niet beschikbaar    
-   **Primaire site**: Ingeschakeld    
-   Secundaire site: Niet beschikbaar  

**Verzamelingsleden evalueren**: U configureert evaluatie lidmaatschap verzameling als sitecomponent. Zie [Siteonderdelen voor System Center Configuration Manager](../../../core/servers/deploy/configure/site-components.md) voor informatie over site-onderdelen.  

-   Centrale beheersite: Niet beschikbaar    
-   **Primaire site**: Ingeschakeld    
-   Secundaire site: Niet beschikbaar  

**Sleutels bewaken**: Gebruik deze taak de integriteit van de primaire sleutels van Configuration Manager-database bewaken. Een primaire sleutel is een kolom (of een combinatie van kolommen) die uniek wordt aangeduid één rij en deze onderscheidt van andere rijen in een Microsoft SQL Server-databasetabel.  

-   **Centrale beheersite**: Ingeschakeld    
-   **Primaire site**: Ingeschakeld    
-   Secundaire site: Niet beschikbaar  

**Indexen opnieuw samenstellen**: Gebruik deze taak voor de Configuration Manager-database-indexen opnieuw samenstellen. Een index is een databasestructuur die op een databasetabel is gemaakt om het ophalen van gegevens sneller te laten verlopen. Bijvoorbeeld zoeken naar een geïndexeerde kolom is vaak veel sneller dan zoeken naar een kolom die is niet geïndexeerd.

Om prestaties te verbeteren, worden de indexen Configuration Manager-database regelmatig bijgewerkt om gesynchroniseerd met de zich voortdurend wijzigende gegevens die zijn opgeslagen in de database te blijven. Deze taak maakt indexen voor databasekolommen die voor ten minste 50 procent uniek zijn, verwijdert indexen voor kolommen die voor minder dan 50 procent uniek zijn en stelt alle bestaande indexen opnieuw samen die aan de uniekheidscriteria voor gegevens voldoen.  

-   **Centrale beheersite**: Niet ingeschakeld    
-   **Primaire site**: Niet ingeschakeld    
-   **Secundaire site**: Niet ingeschakeld  

**Geïnstalleerde softwaregegevens samenvatten**: Gebruik deze taak de gegevens van geïnstalleerde software vanuit meerdere records in één algemeen record samenvatten. Gegevenssamenvatting kunt de hoeveelheid gegevens die zijn opgeslagen in de Configuration Manager-database comprimeren. Zie voor meer informatie [Inleiding tot software-inventaris in System Center Configuration Manager](../../clients/manage/inventory\introduction-to-software-inventory.md).  

-   Centrale beheersite: Niet beschikbaar    
-   **Primaire site**: Ingeschakeld    
-   Secundaire site: Niet beschikbaar  

**Bestand gebruiksgegevens van Softwaremeter samenvatten**: Gebruik deze taak de gegevens uit meerdere records softwaremeterbestand in één algemeen record samenvatten. Gegevenssamenvatting kunt de hoeveelheid gegevens die zijn opgeslagen in de Configuration Manager-database comprimeren.

U kunt deze taak met de **maandelijks gebruik samenvatten** softwarelicentiecontrolegegevens samenvatten en zo schijfruimte besparen in de Configuration Manager-database. Zie [Softwarelicentiecontrole in System Center Configuration Manager](../../../apps/deploy-use/monitor-app-usage-with-software-metering.md) voor meer informatie.  

-   Centrale beheersite: Niet beschikbaar    
-   **Primaire site**: Ingeschakeld    
-   Secundaire site: Niet beschikbaar  

**Maandelijkse gebruiksgegevens van Softwaremeter samenvatten**: Gebruik deze taak de gegevens uit meerdere records voor de maandelijkse gebruiksgegevens van softwaremeter in één algemeen record samenvatten. Gegevenssamenvatting kunt de hoeveelheid gegevens die zijn opgeslagen in de Configuration Manager-database comprimeren.

U kunt deze taak met de **bestand gebruik samenvatten** gegevens van softwaremeter samenvatten en zo schijfruimte besparen in de Configuration Manager-database. Zie [Softwarelicentiecontrole in System Center Configuration Manager](../../../apps/deploy-use/monitor-app-usage-with-software-metering.md) voor meer informatie.  

-   Centrale beheersite: Niet beschikbaar    
-   **Primaire site**: Ingeschakeld    
-   Secundaire site: Niet beschikbaar  

**Beschikbare doelitems voor toepassing bijwerken**: Gebruik deze taak wilt laten Configuration Manager de toewijzing van beleid en toepassingsimplementaties aan resources in verzamelingen opnieuw berekent. Wanneer u beleidsregels of toepassingen op een verzameling implementeert, Configuration Manager een eerste toewijzing gemaakt tussen de objecten die u implementeert en leden van de verzameling.

Deze toewijzingen worden opgeslagen in een tabel zodat u deze eenvoudig kunt raadplegen. Wanneer een verzamelingslidmaatschap verandert, worden deze opgeslagen toewijzingen bijgewerkt op basis van deze wijzigingen. Het is echter mogelijk dat de toewijzingen niet goed worden gesynchroniseerd. Als de site bijvoorbeeld een meldingsbestand niet goed verwerkt, wordt die wijziging mogelijk niet weerspiegeld in een wijziging in de toewijzingen. Deze taak wordt de toewijzing op basis van huidige verzamelingslidmaatschap vernieuwd.  

-   Centrale beheersite: Niet beschikbaar    
-   **Primaire site**: Ingeschakeld    
-   Secundaire site: Niet beschikbaar  

**Application Catalog-tabellen bijwerken**: Gebruik deze taak in de Application Catalog-websitedatabasecache met de meest recente toepassingsinformatie synchroniseren. Wanneer u de configuratie van deze onderhoudstaak wijzigt, geldt de configuratie voor alle primaire sites in de hiërarchie.  

-   Centrale beheersite: Niet beschikbaar    
-   **Primaire site**: Ingeschakeld    
-   Secundaire site: Niet beschikbaar  
