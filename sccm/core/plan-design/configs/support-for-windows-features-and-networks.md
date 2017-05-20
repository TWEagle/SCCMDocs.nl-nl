---
title: Ondersteuning voor Windows-onderdelen | Microsoft-documenten
description: Informatie over welke Windows- en netwerkresources functies ondersteunt van System Center Configuration Manager.
ms.custom: na
ms.date: 3/30/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 0cf4bacb-6b6d-4d4f-8640-b13fe15873de
caps.latest.revision: 8
caps.handback.revision: 0
author: Brenduns
ms.author: brenduns
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: d5166b16ffbe46af561b1ce98c0494cc4aaa72a8
ms.openlocfilehash: e040552dab21ba9a71e06a78f6acc2ffe1b0eb61
ms.contentlocale: nl-nl
ms.lasthandoff: 05/17/2017


---
# <a name="support-for-windows-features-and-networks-in-system-center-configuration-manager"></a>Ondersteuning voor Windows-onderdelen en netwerken in System Center Configuration Manager

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*

Dit onderwerp vindt u System Center Configuration Manager ondersteuning voor algemene Windows en functies voor netwerkbeheer.  


##  <a name="bkmk_branchcache"></a> BranchCache  
U kunt Windows BranchCache gebruiken met Configuration Manager wanneer u BranchCache op distributiepunten inschakelen en Configureer clients voor het gebruik van BranchCache in de gedistribueerde-cachemodus.

U kunt de BranchCache-instellingen voor een implementatietype voor toepassingen, voor de implementatie voor een pakket en voor takenreeksen configureren.  

Als de vereisten voor BranchCache wordt voldaan, kan deze functie clients op externe locaties inhoud ophalen van lokale clients met een huidige cache van de inhoud.  

Als bijvoorbeeld de eerste clientcomputer met BranchCache inhoud aanvraagt van een distributiepunt dat is geconfigureerd als een BrancheCache-server, wordt de inhoud door de clientcomputer gedownload en opgeslagen in het cachegeheugen. Deze inhoud wordt vervolgens beschikbaar gesteld voor clients op hetzelfde subnet die deze inhoud wordt aangevraagd.

De inhoud wordt eveneens door deze clients cache. Op deze wijze hoeven opeenvolgende clients in hetzelfde subnet de inhoud niet van het distributiepunt te downloaden en wordt de inhoud over meerdere clients gedistribueerd voor toekomstige overdrachten.  

**Vereisten voor de ondersteuning van BranchCache met Configuration Manager:**  
-   **Distributiepunten configureren:**  
    Voeg het onderdeel **Windows BranchCache** toe aan de sitesysteemserver die is geconfigureerd als een distributiepunt.    

    -   Distributiepunten op servers die zijn geconfigureerd voor ondersteuning van BranchCache nodig geen aanvullende configuratie.   
    -   U kunt Windows BranchCache toevoegen aan een cloud-gebaseerd distributiepunt, maar cloud-gebaseerde distributiepunten bieden ondersteuning voor het downloaden van inhoud door clients die zijn geconfigureerd voor Windows BranchCache.  

-   **Clients configureren:**    
    -   De clients die ondersteuning voor BranchCache bieden moeten worden geconfigureerd voor gedistribueerde-cachemodus van BranchCache.  
    -   De instelling van het besturingssysteem voor BITS-clientinstellingen moet zijn ingeschakeld voor de ondersteuning van BranchCache.   <br /> <br />
        
    Zie voor meer informatie over het configureren van clients te bieden ondersteuning voor BranchCache: de [clients configureren](https://technet.microsoft.com/itpro/windows/manage/waas-branchcache#configure-clients-for-branchcache) in sectie [BranchCache configureren voor Windows 10-updates](https://technet.microsoft.com/itpro/windows/manage/waas-branchcache).


**Configuration Manager ondersteunt de volgende client-besturingssystemen met Windows BranchCache:**  

|Besturingssysteem|Ondersteuningsgegevens|  
|----------------------|---------------------|  
|Windows 7 met SP1|Standaard ondersteund|  
|Windows 8|Standaard ondersteund|  
|Windows 8.1|Standaard ondersteund|  
|Windows 10|Standaard ondersteund|  
|Windows Server 2008 met SP2|**Vereist BITS 4.0**: U kunt de release BITS 4.0 op Configuration Manager-clients installeren met behulp van software-updates of softwaredistributie. Zie [Windows Management Framework](http://go.microsoft.com/fwlink/p/?LinkId=181979)voor meer informatie over de BITS 4.0-release.<br /><br /> Dit besturingssysteem biedt geen ondersteuning voor de BranchCache-clientfunctie voor softwaredistributie die wordt uitgevoerd vanaf het netwerk of voor SMB-bestandsoverdrachten. Bovendien kan dit besturingssysteem de BranchCache-functionaliteit niet gebruiken met clouddistributiepunten.|  
|Windows Server 2008 R2|Standaard ondersteund|  
|Windows Server 2012|Standaard ondersteund|  
|Windows Server 2012 R2|Standaard ondersteund|  

 Zie [BranchCache voor Windows](http://go.microsoft.com/fwlink/p/?LinkId=177945) in de Windows Server-documentatie voor meer informatie.  

##  <a name="bkmk_Workgroups"></a>Computers in werkgroepen  
Configuration Manager biedt ondersteuning voor clients in werkgroepen.  

-   Configuration Manager ondersteunt de verplaatsing van een client van een werkgroep aan een domein of van een domein in een werkgroep. Zie voor meer informatie [Configuration Manager-clients installeren op Computers in werkgroepen](../../../core/clients/deploy/deploy-clients-to-windows-computers.md#BKMK_ClientWorkgroup) in de [het implementeren van clients op Windows-computers in System Center Configuration Manager](../../../core/clients/deploy/deploy-clients-to-windows-computers.md) onderwerp.  

> [!NOTE]  
>  Hoewel clients in werkgroepen worden ondersteund, moeten alle sitesystemen lid van een ondersteunde Active Directory-domein.  


##  <a name="bkmmk_datadedup"></a> Gegevensontdubbeling  
Configuration Manager ondersteunt het gebruik van gegevensontdubbeling met distributiepunten op de volgende besturingssystemen:  

-   Windows Server 2012  

-   Windows Server 2012 R2  

> [!IMPORTANT]  
>  Het volume dat als host fungeert voor bronbestanden van een pakket kan niet worden gemarkeerd voor gegevensontdubbeling. Dit is omdat gegevensontdubbeling reparsepunten gebruikt en Configuration Manager biedt geen ondersteuning voor het gebruik van inhoudsbronlocatie met bestanden die zijn opgeslagen op reparsepunten.  

Zie voor meer informatie [distributiepunten van Configuration Manager en Windows Server 2012 Gegevensontdubbeling](http://blogs.technet.com/b/configmgrteam/archive/2014/02/18/configuration-manager-distribution-points-and-windows-server-2012-data-deduplication.aspx) op de Configuration Manager-teamblog en [overzicht Gegevensontdubbeling](http://technet.microsoft.com/library/hh831602.aspx) in de Windows Server TechNet-bibliotheek.  

##  <a name="bkmk_DA"></a> DirectAccess  
Configuration Manager ondersteunt de DirectAccess-functie in Windows Server 2008 R2 en hoger voor communicatie tussen clients en sitesystemen van de server.  

-   Als de vereisten voor DirectAccess wordt voldaan, kan DirectAccess Configuration Manager-clients op het Internet communiceren met hun toegewezen site alsof ze zich op het intranet.  

-   Voor serveracties, zoals beheer op afstand en clientpushinstallaties, moet op de computer die deze actie in gang heeft gezet (zoals de siteserver) IPv6 worden uitgevoerd en dit protocol moet worden ondersteund op alle betrokken netwerkapparaten.  

Configuration Manager biedt geen ondersteuning voor het volgende via DirectAccess:  

-   De implementatie van besturingssystemen.  

-   Communicatie tussen Configuration Manager-sites  

-   Communicatie tussen Configuration Manager-sitesysteemservers binnen een site  

##  <a name="bkmk_dualboot"></a> Dual-bootcomputers  
 Configuration Manager kan niet meer dan één besturingssysteem op een enkele computer te beheren. Als er meer dan één besturingssysteem op een computer die moet worden beheerd is, past u de detectie- en installatietaken methoden die worden gebruikt om ervoor te zorgen dat de Configuration Manager client is geïnstalleerd op het besturingssysteem die moet worden beheerd.  

##  <a name="bkmk_IPv6"></a>Internet Protocol versie 6  
 Configuration Manager ondersteunt naast Internet Protocol versie 4 (IPv4), Internet Protocol versie 6 (IPv6) met de volgende uitzonderingen:  

|Functie| Uitzondering op IPv6-ondersteuning|  
|--------------|-------------------------------|  
|Clouddistributiepunten|IPv4 is vereist voor de ondersteuning van Microsoft Azure en clouddistributiepunten.|  
|Mobiele apparaten die zijn geregistreerd door Microsoft Intune en de connector voor Microsoft-service|IPv4 is vereist voor ondersteuning van mobiele apparaten die zijn geregistreerd door Microsoft Intune en de connector voor Microsoft-service.|  
|Netwerkdetectie|IPv4 is vereist als u een DHCP-server configureert om in Netwerkdetectie te zoeken.|  
|Implementatie van besturingssystemen|IPv4 is vereist voor ondersteuning van de implementatie van besturingssystemen.|  
|Communicatie van de wake-up proxy|IPv4 is vereist voor de ondersteuning van de pakketten voor de wake-up proxy van clients.|  
|Windows CE|IPv4 is vereist voor ondersteuning van de Configuration Manager-client op apparaten met Windows CE.|  

##  <a name="bkmk_NAT"></a> Network Address Translation  
 NAT (Network Address Translation) wordt niet ondersteund voor in Configuration Manager, tenzij de site biedt ondersteuning voor clients die zich op het Internet en de client detecteert dat is verbonden met Internet. Zie voor meer informatie over clientbeheer via Internet, [plannen voor het beheren van clients op Internet in System Center Configuration Manager](../../../core/clients/deploy/plan/plan-for-managing-internet-based-clients.md).  

##  <a name="bkmk_storage"></a> Gespecialiseerde opslagtechnologie  
 Configuration Manager werkt met alle hardware die is gecertificeerd op de Windows Hardware Compatibility List voor de versie van het besturingssysteem dat op het Configuration Manager-onderdeel is geïnstalleerd.

Voor siteserverfuncties zijn NTFS-bestandssystemen vereist zodat map- en bestandsmachtigingen kunnen worden ingesteld. Omdat Configuration Manager wordt ervan uitgegaan dat er volledige eigendom van een logisch station, kunnen geen site-systemen die worden uitgevoerd op afzonderlijke computers een logische partitie opslag bevindt delen. Elke computer kan echter een afzonderlijke logische partitie gebruiken op dezelfde fysieke partitie van een gedeeld opslagapparaat.  

 **Ondersteuningsoverwegingen:**  

-   **Storage Area Network**: Een Storage Area Network (SAN) wordt ondersteund als er een ondersteunde Windows-server gekoppeld is rechtstreeks naar het volume dat wordt gehost door de SAN.  

-   **Single Instance Storage**: Configuration Manager biedt geen ondersteuning voor configuratie van distribution point pakket en handtekening mappen op een volume Single Instance Storage SIS-functionaliteit.  

     Bovendien worden de cache van een Configuration Manager-client wordt niet ondersteund op een volume SIS is ingeschakeld.  

-   **Verwisselbaar station**: Configuration Manager biedt geen ondersteuning voor de installatie van Configuration Manager-sitesystemen of clients op een verwisselbaar station.  

