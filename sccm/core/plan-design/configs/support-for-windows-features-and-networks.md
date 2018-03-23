---
title: Ondersteuning voor Windows-onderdelen
titleSuffix: Configuration Manager
description: Meer informatie over welke Windows- en netwerken functies ondersteunt van System Center Configuration Manager.
ms.custom: na
ms.date: 03/22/2018
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 0cf4bacb-6b6d-4d4f-8640-b13fe15873de
caps.latest.revision: ''
caps.handback.revision: ''
author: mestew
ms.author: mstewart
manager: dougeby
ms.openlocfilehash: 4a41efa9b4c33a77d6aa2fa9e806e24ae33cc330
ms.sourcegitcommit: 11bf4ed40ed0cbb10500cc58bbecbd23c92bfe20
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 03/23/2018
---
# <a name="support-for-windows-features-and-networks-in-system-center-configuration-manager"></a>Ondersteuning voor Windows-onderdelen en -netwerken in System Center Configuration Manager

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*

In dit artikel identificeert Configuration Manager-ondersteuning voor algemene Windows- en netwerkfuncties.  


##  <a name="bkmk_branchcache"></a> BranchCache  
U kunt Windows BranchCache gebruiken met Configuration Manager wanneer u het inschakelen op distributiepunten en clients worden gebruikt in de modus gedistribueerde cache configureren.

U kunt de BranchCache-instellingen voor een implementatietype voor toepassingen, voor de implementatie voor een pakket en voor takenreeksen configureren.  

Wanneer de vereisten voor BranchCache wordt voldaan, kan deze functie clients op externe locaties inhoud ophalen van lokale clients met een huidige cache van de inhoud.  

Bijvoorbeeld, wanneer de eerste BranchCache-clients inhoud van een distributiepunt dat is geconfigureerd als een BranchCache-server aanvraagt, de client downloadt en slaat de inhoud. Deze inhoud wordt vervolgens beschikbaar gesteld voor clients op hetzelfde subnet die deze inhoud wordt aangevraagd.

Deze clients cache ook de inhoud. Andere clients in hetzelfde subnet geen inhoud te downloaden vanaf het distributiepunt. De inhoud wordt gedistribueerd over meerdere clients voor toekomstige overdrachten.  

### <a name="requirements-to-support-branchcache-with-configuration-manager"></a>Vereisten voor de ondersteuning van BranchCache met Configuration Manager
-   **Distributiepunten configureren**: Voeg de **Windows BranchCache** functie aan de sitesysteemserver die is geconfigureerd als een distributiepunt.    
    -   Distributiepunten op servers die zijn geconfigureerd voor ondersteuning van BranchCache is geen aanvullende configuratie vereist.   
    -   U kunt Windows BranchCache niet toevoegen aan een cloud-gebaseerd distributiepunt. Cloud-gebaseerde distributiepunten bieden ondersteuning voor het downloaden van inhoud door clients die zijn geconfigureerd voor Windows BranchCache.  

-   **Clients configureren**:    
    -   De clients die BranchCache kunnen ondersteunen, moeten worden geconfigureerd voor de gedistribueerde-cachemodus van BranchCache.  
    -   De besturingssysteeminstelling voor BITS-clientinstellingen moet zijn ingeschakeld voor de ondersteuning van BranchCache.   <br /> <br />

    Zie voor informatie [clients configureren voor BranchCache](https://docs.microsoft.com/windows/deployment/update/waas-branchcache#configure-clients-for-branchcache) in de documentatie van Windows.


### <a name="configuration-manager-supported-os-versions-with-windows-branchcache"></a>Configuration Manager wordt ondersteund door Windows BranchCache OS-versies

|Besturingssysteem|Ondersteuningsgegevens|  
|----------------------|---------------------|  
|Windows 7 met SP1|Standaard ondersteund|  
|Windows 8|Standaard ondersteund|  
|Windows 8.1|Standaard ondersteund|  
|Windows 10|Standaard ondersteund|  
|Windows Server 2008 met SP2|**BITS 4.0 vereist**: U kunt de BITS 4.0-release van Configuration Manager-clients installeren met behulp van software-updates of softwaredistributie. Zie voor meer informatie [Windows Management Framework](https://support.microsoft.com/help/968929/windows-management-framework-windows-powershell-2-0-winrm-2-0-and-bits).<br /><br /> Op dit besturingssysteem de BranchCache-clientfunctionaliteit niet ondersteund voor softwaredistributie die wordt uitgevoerd vanaf het netwerk of voor SMB-bestandsoverdrachten. Bovendien kan dit besturingssysteem de BranchCache-functionaliteit niet gebruiken met clouddistributiepunten.|  
|Windows Server 2008 R2|Standaard ondersteund|  
|Windows Server 2012|Standaard ondersteund|  
|Windows Server 2012 R2|Standaard ondersteund|  
|Windows Server 2016|Standaard ondersteund|  

 Zie voor meer informatie [BranchCache voor Windows](https://docs.microsoft.com/windows-server/networking/branchcache/branchcache) in de documentatie van Windows Server.  



##  <a name="bkmk_Workgroups"></a> Computers in werkgroepen  
Configuration Manager biedt ondersteuning voor clients in werkgroepen.  

-   Configuration Manager ondersteunt het verplaatsen van een client van een werkgroep naar een domein of van een domein naar een werkgroep. Zie voor meer informatie [Configuration Manager-clients installeren op computers in werkgroepen](../../../core/clients/deploy/deploy-clients-to-windows-computers.md#BKMK_ClientWorkgroup) in de [clients implementeren op Windows-computers](../../../core/clients/deploy/deploy-clients-to-windows-computers.md) onderwerp.  

> [!NOTE]  
>  Hoewel clients in werkgroepen worden ondersteund, moeten alle sitesystemen lid van een ondersteund Active Directory-domein.  



##  <a name="bkmmk_datadedup"></a> Gegevensontdubbeling  
Configuration Manager ondersteunt het gebruik van gegevensontdubbeling met distributiepunten op de volgende besturingssystemen:  

-   Windows Server 2016
-   Windows Server 2012 R2  
-   Windows Server 2012  


> [!IMPORTANT]  
>  Het volume dat als host fungeert voor bronbestanden van een pakket kan niet worden gemarkeerd voor gegevensontdubbeling. Deze beperking is omdat bij gegevensontdubbeling gebruik wordt gemaakt van gegevens reparsepunten. Configuration Manager biedt geen ondersteuning voor het gebruik van een inhoudsbronlocatie met bestanden die op reparsepunten worden opgeslagen.  

Zie voor meer informatie [distributiepunten van Configuration Manager en Windows Server 2012-Gegevensontdubbeling](https://cloudblogs.microsoft.com/enterprisemobility/2014/02/18/configuration-manager-distribution-points-and-windows-server-2012-data-deduplication/) op de Configuration Manager-teamblog en [overzicht Gegevensontdubbeling](https://docs.microsoft.com/windows-server/storage/data-deduplication/overview) in de Windows Server-documentatie.  



##  <a name="bkmk_DA"></a> DirectAccess  
Configuration Manager ondersteunt de DirectAccess-onderdeel voor de communicatie tussen clients en sitesystemen van de server.  

-   Wanneer u de vereisten voor DirectAccess is voldaan, kan Configuration Manager-clients op internet om te communiceren met hun toegewezen site alsof ze op het intranet.  

-   Voor Serveracties, zoals beheer op afstand en clientpushinstallaties, moet de initiërende computer IPv6 worden uitgevoerd. Dit protocol moet worden ondersteund op alle betrokken netwerkapparaten.  

Configuration Manager biedt geen ondersteuning voor de volgende functionaliteit via DirectAccess:  

-   De implementatie van besturingssystemen  

-   Communicatie tussen sites van Configuration Manager  

-   Communicatie tussen Configuration Manager-sitesysteemservers binnen een site  



##  <a name="bkmk_dualboot"></a> Dual-bootcomputers  
 Configuration Manager kan niet meer dan één besturingssysteem op één computer beheren. Als er meer dan één besturingssysteem op een computer om te beheren, aanpassen van de site-detectie- en installatiemethoden voor clients om ervoor te zorgen dat de Configuration Manager client alleen wordt geïnstalleerd op het besturingssysteem dat moet worden beheerd.  



##  <a name="bkmk_IPv6"></a> Internet Protocol versie 6  
 Configuration Manager ondersteunt naast Internet Protocol versie 4 (IPv4), Internet Protocol versie 6 (IPv6) met de volgende uitzonderingen:  

|Functie| Uitzondering op IPv6-ondersteuning|  
|--------------|-------------------------------|  
|Clouddistributiepunten|IPv4 is vereist voor de ondersteuning van Microsoft Azure en clouddistributiepunten.|  
|Beheergateway cloud|IPv4 is vereist voor de ondersteuning van Microsoft Azure en de cloud management gateway.|  
|Mobiele apparaten die zijn geregistreerd door Microsoft Intune en de Microsoft-serviceconnector|IPv4 is vereist voor ondersteuning van mobiele apparaten die zijn geregistreerd door Microsoft Intune en de Microsoft-serviceconnector.|  
|Netwerkdetectie|IPv4 is vereist als u een DHCP-server configureert om in Netwerkdetectie te zoeken.|  
|Implementatie van het besturingssysteem|IPv4 is vereist voor de ondersteuning van de implementatie van het besturingssysteem. |  
|Communicatie van de wake-up proxy|IPv4 is vereist voor de ondersteuning van de pakketten voor de wake-up proxy van clients.|  
|Windows CE|IPv4 is vereist voor de ondersteuning van Configuration Manager-client op Windows CE-apparaten.|  



##  <a name="bkmk_NAT"></a> Network Address Translation  
 NAT (Network Address Translation) wordt niet ondersteund voor in Configuration Manager, tenzij de site biedt ondersteuning voor clients die zich op het internet en de client detecteert dat is verbonden met internet. Zie voor meer informatie over clientbeheer op internet, [plannen voor het beheren van clients op internet](../../../core/clients/deploy/plan/plan-for-managing-internet-based-clients.md).  



##  <a name="bkmk_storage"></a> Gespecialiseerde opslagtechnologie  
 Configuration Manager werkt met alle hardware die is gecertificeerd op de Windows Hardware Compatibility List voor de versie van het besturingssysteem waarop het onderdeel Configuration Manager is geïnstalleerd.

Site server-rollen vereisen NTFS, zodat dat Configuration Manager kan map- en bestandsmachtigingen instellen. Configuration Manager wordt ervan uitgegaan dat er volledig eigenaar is van een logisch station. Sitesystemen die op afzonderlijke computers worden uitgevoerd, niet een logische partitie in welke opslagtechnologie delen. Elke computer kan echter een afzonderlijke logische partitie gebruiken op dezelfde fysieke partitie van een gedeeld opslagapparaat.  

 ### <a name="support-considerations"></a>Overwegingen voor ondersteuning

-   **Storage Area Network**: Een Storage Area Network (SAN) wordt ondersteund wanneer een ondersteunde Windows-server rechtstreeks wordt gekoppeld aan het volume dat wordt gehost door de SAN.  

-   **Single Instance Storage**: Configuration Manager biedt geen ondersteuning voor configuratie van mappen voor distributiepuntpakketten en handtekeningen in een Single Instance Storage SIS-volume.  

     Bovendien worden de cache van een Configuration Manager-client wordt niet ondersteund in een SIS-volume.  

-   **Verwisselbare-schijfstation**: Configuration Manager biedt geen ondersteuning voor de installatie van Configuration Manager-sitesystemen of clients op een verwisselbaar station.  
