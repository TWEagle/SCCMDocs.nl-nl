---
title: Aanbevolen hardware | Microsoft-documenten
description: De aanbevolen hardware bij het schalen van uw System Center Configuration Manager-omgeving buiten een eenvoudige implementatie worden opgehaald.
ms.custom: na
ms.date: 05/04/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 5267f0af-34d3-47a0-9ab8-986c41276e6c
caps.latest.revision: 26
caps.handback.revision: 0
author: Brenduns
ms.author: brenduns
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 212628639300e9c361f7cee61b3df6b1cb6874ce
ms.openlocfilehash: 8dac6df60b07461d6410d305723b3f03fb09fa16
ms.contentlocale: nl-nl
ms.lasthandoff: 05/17/2017


---
# <a name="recommended-hardware-for-system-center-configuration-manager"></a>Aanbevolen hardware voor System Center Configuration Manager

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*

De volgende aanbevelingen volgen richtlijnen bij het schalen van uw System Center Configuration Manager-omgeving ter ondersteuning van meer dan een zeer eenvoudige implementatie van sites, sitesystemen en clients. Deze aanbevelingen omvatten niet alle mogelijke site- en hiërarchieconfiguraties.  

 Gebruik de informatie in de volgende secties als richtlijn voor het plannen voor de hardware die kan voorzien in de verwerkingsbelastingen voor clients en sites die de beschikbare Configuration Manager-functies met de standaardconfiguraties gebruiken.  


##  <a name="bkmk_ScaleSieSystems"></a>Site-systemen  
 Deze sectie vindt aanbevolen hardwareconfiguraties voor Configuration Manager de site-systemen voor implementaties met ondersteuning voor het maximum aantal clients en de meeste of alle Configuration Manager-functies gebruiken. Implementaties die kleiner zijn dan het maximum aantal clients ondersteunen en het gebruik van alle beschikbare functies niet nodig achten minder computerbronnen. In het algemeen zijn dit de belangrijkste factoren die de prestaties van het algehele systeem beperken (in volgorde):  

1.  I/O-prestaties schijf  

2.  Beschikbaar geheugen  

3.  CPU  

Gebruik voor de beste prestaties RAID 10-configuraties voor alle gegevensstations en een Ethernet-netwerk van 1 Gbps.  

###  <a name="bkmk_ScaleSiteServer"></a>Siteservers  

|Zelfstandige primaire site|CPU (kernen)|Geheugen (GB)|Geheugentoewijzing voor SQL Server (%)|  
|-------------------------------|---------------|---------------|----------------------------------------|  
|Zelfstandige primaire siteserver met de siterol van een database op dezelfde server<sup>1</sup>|16|96|80|  
|Zelfstandige primaire siteserver met een externe sitedatabase|8|16|-|  
|Externe databaseserver voor een zelfstandige primaire site|16|72|90|  
|Server centrale beheersite met de siterol van een database op dezelfde server<sup>1</sup>|20|128|80|  
|Server van de centrale beheersite met een externe sitedatabase|8|16|-|  
|Externe databaseserver voor een centrale beheersite|16|96|90|  
|Onderliggende primaire site met de siterol van een database op dezelfde server|16|96|80|  
|Onderliggende primaire siteserver met een externe sitedatabase|8|16|-|  
|Externe databaseserver voor een onderliggende primaire site|16|72|90|  
|Secundaire siteserver|8|16|-|  

 <sup>1</sup> wanneer de siteserver en SQL Server worden geïnstalleerd op dezelfde computer, de implementatie van het maximum ondersteunt [grootte en schaal getallen](/sccm/core/plan-design/configs/size-and-scale-numbers) voor sites en clients. Maar deze configuratie kunt beperken [maximaal Beschikbaarheidsopties voor System Center Configuration Manager](/sccm/protect/understand/high-availability-options), zoals met behulp van een SQL Server-cluster. Vanwege de hogere i/o-vereisten die nodig zijn voor de ondersteuning van SQL Server en de Configuration Manager-siteserver wanneer u beide op dezelfde computer uitvoert, is deze ook een goed idee overwegen om een configuratie met een externe SQL Server-computer te gebruiken als u een grotere implementatie.  

###  <a name="bkmk_RemoteSiteSystem"></a>Externe sitesysteemservers  
 De volgende informatie is bedoeld voor computers die een enkele sitesysteemrol bevatten. Houd er rekening mee dat u wijzigingen moet aanbrengen wanneer u meerdere sitesysteemrollen op dezelfde computer installeert.  

|Sitesysteemrol|CPU (kernen)|Geheugen (GB)|Schijfruimte (GB)|  
|----------------------|---------------|---------------|--------------------|  
|Beheerpunt|4|8|50|  
|Distributiepunt|2|8|Zoals wordt vereist door het besturingssysteem en voor het opslaan van inhoud die u implementeert|  
|Toepassingscatalogus, met de webservice en website op de sitesysteemcomputer|4|16|50|  
|Software-updatepunt<sup>1</sup>|8|16|Zoals wordt vereist door het besturingssysteem en voor het opslaan van updates die u implementeert|  
|Alle andere sitesysteemrollen|4|8|50|  

 <sup>1</sup> de computer die als host fungeert voor een software-updatepunt, de volgende configuraties vereist voor groepen van IIS-toepassingen:  

-   Vergroot de **WsusPool wachtrijlengte** naar **2000**.  

-   Vergroot de **WsusPool privé-geheugenlimiet** door 4 keer of stel deze in op **0** (onbeperkt).  

###  <a name="bkmk_DiskSpace"></a>Schijfruimte voor site-systemen  
 Toegewezen schijfruimte en configuratie bijdraagt aan de prestaties van Configuration Manager. Omdat elke Configuration Manager-omgeving anders is, worden de waarden die u implementeert kunnen variëren van het volgende advies.  

 Voor de beste prestaties plaatst u elk object op een afzonderlijk, speciaal RAID-volume. Gebruik voor alle gegevensvolumes (Configuration Manager en de bijbehorende databasebestanden) RAID 10 voor de beste prestaties.  

|Gegevensgebruik|Minimale schijfruimte|25.000 clients|50.000 clients|100.000 clients|150.000 clients|700.000 clients (centrale beheersite)|  
|----------------|------------------------|--------------------|--------------------|---------------------|---------------------|-----------------------------------------------------|  
|Besturingssysteem|Zie de richtlijnen voor het besturingssysteem.|Zie de richtlijnen voor het besturingssysteem.|Zie de richtlijnen voor het besturingssysteem.|Zie de richtlijnen voor het besturingssysteem.|Zie de richtlijnen voor het besturingssysteem.|Zie de richtlijnen voor het besturingssysteem.|  
|Configuration Manager-toepassing en logboekbestanden bestanden|25 GB|50 GB|100 GB|200 GB|300 GB|200 GB|  
|MDF-bestand van sitedatabase|75 GB voor elke 25.000 clients|75 GB|150 GB|300 GB|500 GB|2 TB|  
|LDF-bestand van sitedatabase|25 GB voor elke 25.000 clients|25 GB|50 GB|100 GB|150 GB|100 GB|  
|Tijdelijke databasebestanden (MDF en LDF)|Indien nodig|Indien nodig|Indien nodig|Indien nodig|Indien nodig|Indien nodig|  
|Inhoud (distributiepuntshares)|Indien nodig<sup>1</sup>|Indien nodig<sup>1</sup>|Indien nodig<sup>1</sup>|Indien nodig<sup>1</sup>|Indien nodig<sup>1</sup>|Indien nodig<sup>1</sup>|  

 <sup>1</sup> het advies ruimte niet de benodigde ruimte voor inhoud die in de Inhoudsbibliotheek op de siteserver of distributiepunt bevindt zich bevat. Zie [De inhoudsbibliotheek](../../../core/plan-design/hierarchy/the-content-library.md) voor informatie over het plannen van de inhoudsbibliotheek.  

 Naast het voorafgaande advies moet u ook rekening houden met de volgende richtlijnen wanneer u de vereisten voor de schijfruimte plant:  

-   Voor elke client is ongeveer 5 MB aan ruimte vereist.  

-   Wanneer u plant voor de grootte van de tijdelijke database voor een primaire site, plan dan een gecombineerde grootte die 25% tot 30% van het MDF-bestand van de site-database. De daadwerkelijke grootte kan aanzienlijk worden kleiner of groter: het hangt af van de prestaties van de siteserver en het volume van binnenkomende gegevens gedurende zowel korte als lange perioden.  

    > [!NOTE]  
    >  Wanneer u 50.000 of meer clients op een site hebt, plan dan vier of meer tijdelijke database .mdf-bestanden gebruiken.  

-   De grootte van de tijdelijke database voor een centrale beheersite is doorgaans veel kleiner dan voor een primaire site.  

-   De secundaire sitedatabase is in grootte beperkt tot het volgende:  

    -   SQL Server 2012 Express: 10 GB  

    -   SQL Server 2014 Express: 10 GB  

##  <a name="bkmk_ScaleClient"></a>Clients  
 Deze sectie vindt aanbevolen hardwareconfiguraties voor computers die u beheert met behulp van Configuration Manager-clientsoftware.  

### <a name="client-for-windows-computers"></a>Client voor Windows-computers:  
 Hier volgen de minimale vereisten voor Windows-computers die u beheert met behulp van Configuration Manager, waaronder embedded-besturingssystemen:  

-   **Processor en geheugen:** Raadpleeg de processor- en RAM-vereisten voor het computerbesturingssysteem.  

-   **Schijfruimte:** 500 MB vrije schijfruimte 5 GB wordt aanbevolen voor de clientcache voor Configuration Manager. Minder schijfruimte is vereist als u aangepaste instellingen gebruikt om de Configuration Manager-client te installeren:  

    -   De /skipprereq CCMSetup-opdrachtregeleigenschap gebruiken om te voorkomen dat bestanden die niet voor de client vereist te installeren. Bijvoorbeeld, voer **CCMSetup.exe /skipprereq:silverlight.exe** als de client de Toepassingscatalogus niet gebruiken.  

    -   Gebruik de Client.msi-eigenschap SMSCACHESIZE om een cachebestand in te stellen dat kleiner is dan de standaardgrootte van 5120 MB. De minimumgrootte is 1 MB. Met **CCMSetup.exe SMSCachesize=2** maakt u bijvoorbeeld een cache van 2 MB.  

    Zie [Over de eigenschappen van clientinstallatie in System Center Configuration Manager](../../../core/clients/deploy/about-client-installation-properties.md) voor meer informatie over deze instellingen voor een clientinstallatie.  

    > [!TIP]  
    >  Het installeren van de client met minimale schijfruimte is handig voor Windows Embedded-apparaten die doorgaans over een kleinere schijf beschikken dan de gewone Windows-computers.  



 Hier volgen extra minimale hardwarevereisten beschreven voor optionele functionaliteit in Configuration Manager.  

-   **Implementatie van besturingssysteem:** 384 MB RAM-geheugen  

-   **Software Center:** Processor van 500 MHz  

-   **Beheer op afstand:** Pentium 4 Hyper-Threaded 3 GHz (enkele kern) of vergelijkbare CPU met ten minste 1 GB RAM-geheugen voor optimale ervaring  

### <a name="client-for-linux-and-unix"></a>Client voor Linux en UNIX  
 Hier volgen de minimale vereisten voor Linux en UNIX-servers die u met Configuration Manager beheert.  

|Vereiste|Details|  
|-----------------|-------------|  
|Processor en geheugen|Raadpleeg de processor- en RAM-vereisten voor het besturingssysteem van de computer.|  
|Schijfruimte|500 MB vrije schijfruimte 5 GB wordt aanbevolen voor de clientcache voor Configuration Manager.|  
|Netwerkconnectiviteit|Configuration Manager-clientcomputers moeten netwerkverbinding met de Configuration Manager site-systemen voor het beheer hebben.|  

##  <a name="bkmk_ScaleConsole"></a>Configuration Manager-console  
 De vereisten in de volgende tabel van toepassing op elke computer waarop de Configuration Manager-console.  

 **Minimale hardwareconfiguratie:**  

-   Intel i3 of vergelijkbare CPU  

-   2 GB RAM-geheugen  

-   2 GB aan schijfruimte  

|DPI-instelling|Minimale resolutie|  
|-----------------|------------------------|  
|96 / 100%|1024 x 768|  
|120 / 125%|1280 x 960|  
|144 / 150%|1600 x 1200|  
|196 / 200%|2500 x 1600|  

 **Ondersteuning voor PowerShell:**  

 Wanneer u ondersteuning voor PowerShell op een computer waarop de Configuration Manager-console wordt uitgevoerd installeert, voert u PowerShell-cmdlets op die computer voor het beheren van Configuration Manager.

 - PowerShell 3.0 of hoger wordt ondersteund.

Naast PowerShell, wordt Windows Management Framework (WMF) versie 3.0 of hoger ondersteund.   


##  <a name="bkmk_ScaleLab"></a>Lab-implementaties  
 Gebruik de volgende minimale hardware-aanbevelingen voor lab en test implementaties van Configuration Manager. Deze aanbevelingen zijn van toepassing op alle site-typen, maximaal 100 clients:  

|Rol|CPU (kernen)|Geheugen (GB)|Schijfruimte (GB)|  
|----------|---------------|-------------------|-----------------------|  
|Site- en databaseserver|2 - 4|7 - 12|100|  
|Sitesysteemserver|1 - 4|2 - 4|50|  
|Client|1 - 2|1 - 3|30|  

