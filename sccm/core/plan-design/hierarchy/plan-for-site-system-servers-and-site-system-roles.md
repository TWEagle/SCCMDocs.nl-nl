---
title: Sitesysteemrollen plannen | Microsoft Docs
description: "Als u van plan uw System Center Configuration Manager-hiërarchie bent, overweeg dan sitesysteemservers en sitesysteemrollen."
ms.custom: na
ms.date: 10/06/2016
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: configmgr-other
ms.tgt_pltfrm: na
ms.topic: get-started-article
ms.assetid: 0a7415ba-2c53-4433-983e-780e92aa662f
caps.latest.revision: "11"
author: Brenduns
ms.author: brenduns
manager: angrobe
ms.openlocfilehash: 0a3704a2d3b75ed7e0a7f718b681448ab6fc078d
ms.sourcegitcommit: 51fc48fb023f1e8d995c6c4eacfda7dbec4d0b2f
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 08/07/2017
---
# <a name="plan-for-site-system-servers-and-site-system-roles-for-system-center-configuration-manager"></a>Plan maken voor sitesysteemservers en sitesysteemrollen voor System Center Configuration Manager

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*

Elke System Center Configuration Manager-site die u installeert een siteserver bevat een **sitesysteemserver**. De site kan ook extra sitesysteemservers bevatten op computers die zich op afstand van de siteserver bevinden. Sitesysteemservers (de siteserver of een externe sitesysteemserver) bieden ondersteuning voor **sitesysteemrollen**.


##  <a name="bkmk_siteservers"></a> Sitesysteemservers  
 Wanneer u een sitesysteemrol op een computer installeert, wordt die computer een sitesysteemserver. U kunt een of meer aanvullende sitesysteemservers installeren op elke site. U kunt ook niet op extra sitesysteemservers installeren en uitvoeren van al uw sitesysteemrollen rechtstreeks op de siteservercomputer. Elke sitesysteemserver ondersteunt één of meer sitesysteemrollen. Extra servers kunnen u de mogelijkheden en capaciteit van een site breiden door te delen van de CPU-verwerkingsbelasting op een server sitesysteemrollen.  

 Wanneer u overweegt een sitesysteemserver toe te voegen, zorg ervoor dat de server voldoet aan de vereisten voor het beoogde gebruik. Het is ook een goed idee toe te voegen op een netwerklocatie bevindt die voldoende bandbreedte heeft om te communiceren met de verwachte eindpunten, met inbegrip van de siteserver, domeinresources een cloudlocatie, sitesysteemservers en clients).  

 Als u de sitesysteemserver met een proxy voor gebruik door sitesysteemrollen configureert, Zie [sitesysteemrollen die u kunt een proxyserver gebruiken](#bkmk_proxy).  

##  <a name="bkmk_planroles"></a> Site system roles  
 Sitesysteemrollen worden op een computer geïnstalleerd om ervoor te zorgen dat er meer mogelijkheden zijn met de site. Voorbeelden zijn:  

-   Extra beheerpunten zodat de site meer apparaten, maximaal ondersteunde capaciteit van de site kan ondersteunen.  

-   Extra distributiepunten voor het uitbreiden van uw inhoudsinfrastructuur, verbeteren de prestaties van inhoudsdistributies naar apparaten en gebruikers.  

-   Een of meer specifieke sitesysteemrollen. Bijvoorbeeld, een software-updatepunt kunt u software-updates voor beheerde apparaten te beheren of een reporting services-punt kunt u rapporten uitvoeren om te controleren en inzicht in of delen van informatie over uw implementatie.  


Andere Configuration Manager-sites kunnen verschillende sets van sitesysteemrollen ondersteunen. De ondersteunde set van sitesysteemrollen, is afhankelijk van het type site (een centrale beheersite, primaire site of secundaire site). De topologie van uw hiërarchie kan de plaatsing van sommige rollen bij bepaalde typen sites worden beperkt. Zo wordt het serviceaansluitpunt bijvoorbeeld alleen ondersteund door de bovenste site uit de hiërarchie; dit kan een centrale beheersite zijn of en zelfstandige primaire site. Deze rol wordt niet ondersteund op een onderliggende primaire site of secundaire sites.  

Nadat een site is geïnstalleerd, kunt u de locatie van enkele sitesysteemrollen wijzigen van de standaardlocatie op de siteserver naar een andere server. Dit is bijvoorbeeld geldt ook voor het beheerpunt of distributiepunt wordt standaard geïnstalleerd op een primaire of secundaire siteserver. U kunt ook extra exemplaren van sommige sitesysteemrollen uit te breiden de functionaliteit van uw site installeren (meer services aanbieden aan klanten), en om te voldoen aan uw bedrijfsvereisten. Sommige rollen zijn vereist, terwijl andere optioneel.  

-   **Configuration Manager-siteserver.** Deze rol staat voor de server waar de installatie van Configuration Manager wordt uitgevoerd om een site te installeren of de server waarop u een secundaire site installeert. Deze rol kan pas worden verplaatst of verwijderd wanneer de site is verwijderd.  

-   **Configuration Manager-sitesysteem.** Deze rol wordt toegewezen aan een computer waarop u een site installeert of waarop een sitesysteemrol installeert. Deze rol kan pas worden verplaatst of verwijderd wanneer de laatste sitesysteemrol is verwijderd van de computer.  

-   **Configuration Manager componentsitesysteemrol.** Deze rol staat voor een sitesysteem dat een exemplaar van de SMS Executive-service wordt uitgevoerd en is vereist voor ondersteuning van andere rollen, zoals beheerpunten. Deze rol kan pas worden verplaatst of verwijderd wanneer de laatste geschikte sitesysteemrol is verwijderd van de computer.  

-   **Configuration Manager-Sitedatabaseserver.** Deze rol wordt toegewezen aan sitesysteemservers waarop een exemplaar van de sitedatabase voor een site. Deze rol kan alleen worden verplaatst naar een nieuwe server door het wijzigen van de site naar een ander exemplaar van SQL Server gebruiken om de sitedatabase te hosten.  

-   **SMS-Provider.** De rol van de SMS-Provider wordt toegewezen aan elke computer die als host fungeert voor een exemplaar van de SMS-Provider, de interface tussen een Configuration Manager-console en de sitedatabase. Standaard wordt deze rol automatisch geïnstalleerd op de siteserver van een centrale beheersite en primaire sites. U kunt extra exemplaren op elke site om toegang te bieden aan extra gebruikers met beheerdersrechten kunt installeren.  

     Voor het installeren van extra providers, moet u Configuration Manager Setup uitvoeren [beheren van de SMS-Provider](../../../core/servers/manage/modify-your-infrastructure.md#BKMK_ManageSMSprovider). U kunt vervolgens extra providers installeren op extra computers. U kunt slechts één exemplaar van de SMS-Provider installeren op een computer en die computer moet zich in hetzelfde domein als de siteserver.  

-   **Application Catalog-webservicepunt.** Een sitesysteemrol die software-informatie biedt aan de Application Catalog-website van de softwarebibliotheek. Hoewel deze rol alleen op primaire sites wordt ondersteund, kunt u meerdere exemplaren van deze rol op een site of op meerdere sites in dezelfde hiërarchie installeren.  

-   **Application Catalog-websitepunt.** Een sitesysteemrol die gebruikers een lijst biedt met beschikbare software uit Application Catalog. Hoewel deze rol alleen op primaire sites wordt ondersteund, kunt u meerdere exemplaren van deze rol op een site of op meerdere sites in dezelfde hiërarchie installeren.  

     Wanneer de Application Catalog clientcomputers op het Internet ondersteunt, is het aanbevolen beveiligingsprocedure voor het installeren van de Application Catalog-websitepunt in een perimeternetwerk voor beveiliging en voor het installeren van het Application Catalog-webservicepunt op het intranet.  

-   **Asset Intelligence-synchronisatiepunt.** Een sitesysteemrol die verbinding maakt met Microsoft om informatie voor de Asset Intelligence-catalogus te downloaden. Deze rol uploadt ook niet-gecategoriseerde titels, zodat deze kunnen worden overwogen voor toekomstige opname in de catalogus. Een hiërarchie ondersteunt slechts één exemplaar van deze rol en die moet op de bovenste site van uw hiërarchie (een centrale beheersite of de zelfstandige primaire site). Als u een zelfstandige primaire site naar een grotere hiërarchie wilt uitbreiden, moet u deze rol in de primaire site verwijderen en vervolgens op de centrale beheersite installeren.   Zie [Asset Intelligence in System Center Configuration Manager](../../../core/clients/manage/asset-intelligence/introduction-to-asset-intelligence.md) voor meer informatie.  

-   **Certificaatregistratiepunt.** Een sitesysteemrol die communiceert met een server waarop de Network Device Enrollment Service wordt uitgevoerd. Deze rol beheert certificaataanvragen voor apparaten die gebruikmaken van het Simple Certificate Enrollment Protocol (SCEP). Deze rol wordt alleen op primaire sites en op de centrale beheersite ondersteund.

     Hoewel een enkel certificaatregistratiepunt functionaliteit aan de gehele hiërarchie bieden kan, wilt u mogelijk meerdere exemplaren van deze rol op een site en op meerdere sites in dezelfde hiërarchie installeren. Zo kunt u met load balancing. Als er meerdere exemplaren bestaan in een hiërarchie, worden clients willekeurig toegewezen aan een certificaatregistratiepunt.  

     Elk certificaatregistratiepunt vereist toegang tot een afzonderlijk exemplaar van een registratieservice voor netwerkapparaten. U kunt twee of meerdere certificaatregistratiepunten configureren om dezelfde registratieservice voor netwerkapparaten te gebruiken. Bovendien mag het certificaatregistratiepunt niet worden geïnstalleerd op de server waarop ook de registratieservice voor netwerkapparaten wordt uitgevoerd.  

- **Cloud-gateway connector beheerpunt.** Een sitesysteemrol voor communicatie met de [management cloudgateway](/sccm/core/clients/manage/setup-cloud-management-gateway).

-   **Distributiepunt.** Een sitesysteemrol die bronbestanden bevat die clients kunnen downloaden, zoals toepassingsinhoud, softwarepakketten, software-updates, installatiekopieën van besturingssystemen en opstartinstallatiekopieën. Standaard wordt deze rol geïnstalleerd op de servercomputer van de nieuwe primaire en secundaire sites wanneer de site wordt geïnstalleerd. Deze rol wordt niet ondersteund op een centrale beheersite. U kunt meerdere exemplaren van deze rol op een ondersteunde site en op meerdere sites in de hiërarchie installeren. Zie [Basisconcepten voor inhoudsbeheer in System Center Configuration Manager](../../../core/plan-design/hierarchy/fundamental-concepts-for-content-management.md) en [Inhoud en infrastructuur voor inhoud beheren voor System Center Configuration Manager](../../../core/servers/deploy/configure/manage-content-and-content-infrastructure.md) voor meer informatie.  

-   **Terugvalstatuspunt.** Een sitesysteemrol die u helpt clientinstallatie bewaken en identificeren van de clients die onbeheerd zijn doordat ze niet kunnen met hun beheerpunt communiceren. Hoewel deze rol alleen op primaire sites wordt ondersteund, kunt u meerdere exemplaren van deze rol op een site en op meerdere sites in dezelfde hiërarchie installeren.     


-   **Endpoint Protection-punt.** Een sitesysteemrol die Configuration Manager gebruikt de licentievoorwaarden van Endpoint Protection accepteert en het standaardlidmaatschap van Cloud Protection Service configureert. Een hiërarchie ondersteunt slechts één exemplaar van deze rol en die moet op de bovenste site van uw hiërarchie (een centrale beheersite of de zelfstandige primaire site). Als u een zelfstandige primaire site naar een grotere hiërarchie wilt uitbreiden, moet u deze rol in de primaire site verwijderen en vervolgens op de centrale beheersite installeren. Zie voor meer informatie [Endpoint Protection in System Center Configuration Manager](../../../protect/deploy-use/endpoint-protection.md).  

-   **Inschrijvingspunt.** Een sitesysteemrol die PKI-certificaten voor Configuration Manager gebruikt voor het inschrijven van mobiele apparaten en Mac-computers. Hoewel deze rol alleen op primaire sites wordt ondersteund, kunt u meerdere exemplaren van deze rol op een site of op meerdere sites in dezelfde hiërarchie installeren.  

     Als een gebruiker mobiele apparaten inschrijft met behulp van Configuration Manager en de Active Directory-account van de gebruiker zich in een forest dat niet wordt vertrouwd door het forest van de siteserver, moet u een inschrijvingspunt installeren in het forest van gebruiker. De gebruiker vervolgens kan worden geverifieerd.  

-   **Proxypunt voor inschrijving.** Een sitesysteemrol die inschrijvingsaanvragen van Configuration Manager van mobiele apparaten en Mac-computers beheert. Hoewel deze rol alleen op primaire sites wordt ondersteund, kunt u meerdere exemplaren van deze rol op een site of op meerdere sites in dezelfde hiërarchie installeren.  

     Wanneer u mobiele apparaten op Internet ondersteunt, installeer het proxypunt voor inschrijving in een perimeternetwerk voor beveiliging en installeer het inschrijvingspunt op het intranet.  

-   **Exchange Server-connector.** Zie voor meer informatie over deze rol [mobiele apparaten beheren met System Center Configuration Manager en Exchange](../../../mdm/deploy-use/manage-mobile-devices-with-exchange-activesync.md)  

-   **Beheerpunt.** Een sitesysteemrol die beleid en servicelocatie-informatie biedt aan clients en die configuratiegegevens ontvangt van clients.  

    Standaard wordt deze rol geïnstalleerd op de servercomputer van de nieuwe primaire en secundaire sites wanneer de site wordt geïnstalleerd. Primaire sites ondersteunen meerdere exemplaren van deze rol. Secundaire sites ondersteunen een enkel beheerpunt, beleidsregels voor een lokaal contactpunt voor clients om op te halen van de computer en gebruiker (een beheerpunt op een secundaire site wordt aangeduid als een proxy-beheerpunt).  

     Beheerpunten kunnen worden ingesteld voor de ondersteuning van HTTP of HTTPs, evenals ter ondersteuning van mobiele apparaten die u met System Center Configuration Manager On-premises Mobile Device Management beheert. U kunt databasereplica's gebruiken voor beheerpunten voor System Center Configuration Manager (zie [Databasereplica's voor beheerpunten voor System Center Configuration Manager](../../../core/servers/deploy/configure/database-replicas-for-management-points.md)) om de CPU-belasting te verminderen die de sitedatabaseserver ondervindt bij serviceaanvragen van clients.  

-   **Reporting services-punt.** Een sitesysteemrol die integreert met SQL Server Reporting Services maken en beheren van rapporten voor Configuration Manager. Deze rol wordt op primaire sites en de centrale beheersite ondersteund en u kunt meerdere exemplaren van deze rol op een ondersteunde site installeren. Zie [Rapportage in System Center Configuration Manager plannen](../../../core/servers/manage/planning-for-reporting.md) voor meer informatie.  

-   **Het service connection point.** Een sitesysteemrol waarmee u mobiele apparaten beheren met Microsoft Intune en on-premises MDM. Deze rol uploadt ook gebruiksgegevens van uw site, en is vereist om updates voor Configuration Manager beschikbaar in de Configuration Manager-console. Een hiërarchie ondersteunt slechts één exemplaar van deze rol en die moet op de bovenste site van uw hiërarchie (een centrale beheersite of de zelfstandige primaire site). Als u een zelfstandige primaire site naar een grotere hiërarchie wilt uitbreiden, moet u deze rol in de primaire site verwijderen en vervolgens op de centrale beheersite installeren. Zie [Informatie over het serviceaansluitpunt in System Center Configuration Manager](../../../core/servers/deploy/configure/about-the-service-connection-point.md) voor meer informatie.  

-   **Software-updatepunt.** Een sitesysteemrol die in combinatie met Windows Server Update Services (WSUS) voor software-updates biedt aan Configuration Manager-clients. Deze rol wordt ondersteund op alle sites:  

    -   Installeer dit sitesysteem in de centrale beheersite om te synchroniseren met WSUS.  

    -   Instellen van elk exemplaar van deze rol op onderliggende primaire sites om te synchroniseren met de centrale beheersite.  

    -   Overweeg een software-updatepunt in secundaire sites te installeren wanneer gegevensoverdracht over het netwerk traag is.  

    Zie [Software-updates plannen in System Center Configuration Manager](../../../sum/plan-design/plan-for-software-updates.md) voor meer informatie.  

-   **Statusmigratiepunt.** Een sitesysteemrol die gebruikersstatusgegevens opslaat wanneer een computer naar een nieuw besturingssysteem wordt gemigreerd. Deze rol wordt ondersteund op primaire sites en secundaire sites. U kunt meerdere exemplaren van deze rol op een site en op meerdere sites in dezelfde hiërarchie installeren. Zie [De gebruikersstatus beheren in System Center Configuration Manager](../../../osd/get-started/manage-user-state.md) voor meer informatie over het opslaan van de gebruikersstatus bij het implementeren van besturingssystemen.  

-   **System Health Validator-punt.** Hoewel deze sitesysteemrol, zichtbaar in de Configuration Manager-console blijft, wordt deze niet meer gebruikt.  

###  <a name="bkmk_proxy"></a> Sitesysteemrollen die gebruik kunnen maken van een proxyserver  
 Sommige Configuration Manager-sitesysteemrollen is verbinding met Internet vereist en wordt een proxyserver gebruiken wanneer de sitesysteemserver die als host fungeert voor de rol is geconfigureerd voor een. Deze verbinding wordt meestal gemaakt de **system** context van de computer waarop de sitesysteemrol is geïnstalleerd. De verbinding kan geen proxyconfiguratie gebruiken voor typische gebruikersaccounts. Als een proxyserver nodig is om een verbinding met Internet te voltooien, moet u de computer instellen om een proxyserver te gebruiken:  

-   U kunt een proxyserver instellen wanneer u een sitesysteemrol installeert.  

-   U kunt toevoegen of wijzigen van een proxyserverconfiguratie wanneer u de Configuration Manager-console gebruiken.  

-   Dezelfde configuratie van de proxyserver wordt gebruikt voor alle sitesysteemrollen op een sitesysteemserver die een proxyserver-configuratie kunt gebruiken. Als u nodig hebt voor verschillende sitesysteemrollen om verschillende proxyservers te gebruiken, moet u de sitesysteemrollen op verschillende sitesysteemservercomputers installeren.  

-   Als u de proxyserverconfiguratie wijzigt of een nieuwe sitesysteemrol installeert op een computer waarop al een proxyserverconfiguratie staat, wordt de oorspronkelijke configuratie overschreven door de nieuwe configuratie.  


Voor procedures over het instellen van de proxyserver voor sitesysteemrollen, Zie de [sitesysteemrollen voor System Center Configuration Manager toevoegen](../../../core/servers/deploy/configure/add-site-system-roles.md) onderwerp.  

Verderop staan de sitesysteemrollen die een proxyserver kunnen gebruiken:  

-   **Asset Intelligence-synchronisatiepunt.** Deze sitesysteemrol maakt verbinding met Microsoft, gebruikt een proxyserverconfiguratie op de computer die als host fungeert voor de Asset Intelligence-synchronisatiepunt.  

-   **Cloud-gebaseerd distributiepunt.** Wanneer u een cloud-gebaseerd distributiepunt gebruikt, is de primaire site die het cloud-gebaseerde distributiepunt beheert moet verbinding maken met Microsoft Azure inrichten, bewaken en distribueren van inhoud naar het distributiepunt. Als een proxyserver vereist voor deze verbinding is, moet u de proxyserver op de primaire siteserver instellen. U kunt een proxyserver op de cloud-gebaseerde distributiepunt in Azure niet instellen. Zie voor meer informatie de [Configureer proxy-instellingen voor primaire sites die cloudservices beheren](../../../core/servers/deploy/configure/install-cloud-based-distribution-points-in-microsoft-azure.md#BKMK_ConfigProxyforCloud) sectie het [cloud-gebaseerde distributiepunten in Microsoft Azure voor System Center Configuration Manager installeert](../../../core/servers/deploy/configure/install-cloud-based-distribution-points-in-microsoft-azure.md) onderwerp.  

-   **Exchange Server-connector.** Deze sitesysteemrol maakt verbinding met een Exchange-Server en gebruikt een proxyserverconfiguratie op de computer die als host fungeert voor de Exchange Server-connector.  

-   **Software-updatepunt.** Deze sitesysteemrol kan verbinding met Microsoft Update om patches te downloaden en synchroniseren van informatie over updates vereisen. Bij het instellen van de proxyserver, gebruikt elke sitesysteemrol op de computer die het gebruik van de proxyserver ondersteunt gewoonlijk de proxyserver. Er is geen aanvullende configuratie vereist. Een uitzondering hierop is de software-updatespunt. Standaard een software-updatespunt gebruikt geen beschikbare proxyserver tenzij u ook de volgende opties inschakelt wanneer u de software-updatespunt instelt:  

    -   **Gebruik een proxyserver bij het synchroniseren van software-updates**  

    -   **Gebruik een proxyserver bij het downloaden van inhoud met behulp van automatische implementatieregels**  

    > [!TIP]  
    >  Voordat u eender welke optie selecteren kunt, moet een proxyserver worden ingesteld op de sitesysteemserver die als host fungeert voor de software-updatespunt. De proxyserver wordt enkel gebruikt voor de specifieke opties die u selecteert.  

 Voor meer informatie over proxyservers voor software-updatepunten, Zie de sectie 'Proxyserverinstellingen' in [installeert een software-updatepunt](../../../sum/get-started/install-a-software-update-point.md) onderwerp.  

-   **Het service connection point.** Bij het instellen van online te zijn (niet offline), deze sitesysteemrol maakt verbinding met Microsoft Intune en de cloudservice van Microsoft.  
