---
title: Vereisten voor de infrastructuur voor besturingssysteemimplementatie | Microsoft Docs
description: Zorg ervoor dat u externe afhankelijkheden en afhankelijkheden product weten voordat u System Center 2012 Configuration Manager voor de implementatie van besturingssystemen gebruiken.
ms.custom: na
ms.date: 10/06/2016
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: configmgr-osd
ms.tgt_pltfrm: na
ms.topic: get-started-article
ms.assetid: 1dc74219-7ff5-4e3b-b4f6-5aad663bb75b
caps.latest.revision: "24"
author: mattbriggs
ms.author: mabrigg
manager: angrobe
ms.openlocfilehash: 523c7e7fd406274b0c0d88fcc4bd6b6247fa34e8
ms.sourcegitcommit: c145e515843a0f37c2e5ca5dbd22072a219d06b4
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/03/2017
---
# <a name="infrastructure-requirements-for-operating-system-deployment-in-system-center-configuration-manager"></a>Vereisten voor de infrastructuur voor besturingssysteemimplementatie in System Center Configuration Manager

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*

Besturingssysteemimplementatie in System Center 2012 Configuration Manager heeft externe afhankelijkheden en afhankelijkheden binnen het product. Gebruik de volgende secties als leidraad bij het voorbereiden van de besturingssysteemimplementatie.  

##  <a name="BKMK_ExternalDependencies"></a> Afhankelijkheden extern aan Configuration Manager  
 Hieronder vindt u informatie over externe hulpprogramma's, installatie-kits en besturingssystemen die vereist zijn voor het implementeren van besturingssystemen in Configuration Manager.  

### <a name="windows-adk-for-windows-10"></a>Windows ADK voor Windows 10  
 Windows ADK is een verzameling van hulpprogramma's die de configuratie en implementatie ondersteunen van Windows besturingssystemen. Configuration Manager gebruikt Windows ADK voor Windows-installaties te automatiseren, Windows installatiekopieën vast te leggen, gebruikersprofielen en gegevens te migreren, enzovoort.  

 De volgende functies van Windows ADK moeten geïnstalleerd server op locatie van het hoogste niveau van de hiärarchie, op de siteserver van elke primaire site in de hiërarchie en op de SMS Provider sitesysteemserver:  

-   Hulpprogramma voor migratie van gebruikersstatus (USMT) <sup>1</sup>  

-   Windows-hulpprogramma's  

-   Windows Voorinstallatieomgeving (Windows PE)

Zie voor een lijst van de versies van Windows 10 ADK die u met verschillende versies van Configuration Manager gebruiken kunt [ondersteuning voor Windows 10 als een client](https://docs.microsoft.com/sccm/core/plan-design/configs/support-for-windows-10#windows-10-adk).

 <sup>1</sup> USMT is niet vereist op de SMS Provider sitesysteemserver.  

> [!NOTE]  
>  U moet handmatig de Windows ADK installeren op elke computer die een centrale beheersite of primaire site hosten zal voordat u de Configuration Manager-site installeert.  

 Zie voor meer informatie:  

-   [Windows ADK voor Windows 10-scenario's voor IT-professionals](https://technet.microsoft.com/library/mt280162\(v=vs.85\).aspx)  

-   [Download Windows ADK voor Windows 10](https://msdn.microsoft.com/windows/hardware/dn913721.aspx#adkwin10)  

-   [Ondersteuning voor Windows 10](/sccm/core/plan-design/configs/support-for-windows-10)  


### <a name="user-state-migration-tool-usmt"></a>Hulpprogramma voor migratie van gebruikersstatus (USMT)  
 Configuration Manager gebruikt een USMT-pakket dat de USMT 10-bronbestanden voor het vastleggen en herstellen van status van de gebruiker als onderdeel van uw implementatie van besturingssystemen bevat. Setup van Configuration Manager op het hoogste niveau maakt automatisch het USMT-pakket. Met USMT 10 kunt u de gebruikersstatus registreren in Windows 7, Windows 8, Windows 8.1 en Windows 10. USMT 10 wordt gedistribueerd in Windows Assessment and Deployment Kit (Windows ADK) voor Windows 10.  

 Zie voor meer informatie:  

-   [Algemene migratiescenario's voor USMT 10](https://technet.microsoft.com/library/mt299169\(v=vs.85\).aspx)  

-   [De gebruikersstatus beheren](../get-started/manage-user-state.md)  

### <a name="windows-pe"></a>Windows PE  
 Windows PE wordt gebruikt om een computer met een installatiekopie op te starten. Dit is een Windows-besturingssysteem met beperkte diensten dat wordt gebruikt tijdens voorinstallatie en implementatie van Windows-besturingssystemen. Hieronder vindt u de versie van Configuration Manager en de ondersteunde versie van Windows ADK, de Windows PE-versie die op waarop de opstartinstallatiekopie is gebaseerd die kan worden aangepast via de Configuration Manager-console en de Windows PE-versies waarop de opstartinstallatiekopie is gebaseerd die u kunt aanpassen met behulp van DISM en vervolgens de installatiekopie aan de opgegeven versie van Configuration Manager toevoegen.  

#### <a name="configuration-manager-version-1511"></a>Configuration Manager versie 1511  
 Hieronder vindt u de ondersteunde versie van Windows ADK, de Windows PE-versie die op waarop de opstartinstallatiekopie is gebaseerd die kan worden aangepast via de Configuration Manager-console en de Windows PE-versies waarop de opstartinstallatiekopie is gebaseerd, u kunt aanpassen met behulp van DISM en vervolgens de installatiekopie toevoegen aan Configuration Manager.  

-   **Windows ADK-versie**  

     Windows ADK voor Windows 10  

-   **Windows PE-versies voor installatiekopieën die aanpasbaar zijn via de Configuration Manager-console**  

     Windows PE 10  

-   **Ondersteunde Windows PE-versies voor installatiekopieën die niet aanpasbaar zijn via de Configuration Manager-console**  

     Windows PE 3.1<sup>1</sup> en Windows PE 5  

     <sup>1</sup> u kunt alleen een opstartinstallatiekopie toevoegen aan Configuration Manager wanneer deze is gebaseerd op Windows PE 3.1. Installeer Windows AIK Supplement voor Windows 7 SP1 om een upgrade van Windows AIK voor Windows 7 (gebaseerd op Windows PE 3) naar Windows AIK Supplement voor Windows 7 SP1 (gebaseerd op Windows PE 3.1) uit te voeren. U kunt Windows AIK Supplement voor Windows 7 SP1 downloaden via het [Microsoft Downloadcentrum](http://www.microsoft.com/download/details.aspx?id=5188).  

     Bijvoorbeeld, wanneer u Configuration Manager hebt, kunt u opstartinstallatiekopieën uit Windows ADK voor Windows 10 (gebaseerd op Windows PE 10) aanpassen via de Configuration Manager-console. Hoewel installatiekopieën die zijn gebaseerd op Windows PE 5 wel worden wel ondersteund, moet u ze aanpassen op een andere computer en moet u die versie van DISM gebruiken die is geïnstalleerd met Windows ADK voor Windows 8. Vervolgens kunt u de installatiekopie toevoegen aan de Configuration Manager-console. Voor meer informatie over de stappen voor het aanpassen van een installatiekopie (toevoegen van optionele componenten en stuurprogramma's), inschakelen van opdrachtondersteuning aan de opstartinstallatiekopie, de installatiekopie toevoegen aan de Configuration Manager-console en distributiepunten bijwerken met de installatiekopie, Zie [opstartinstallatiekopieën aanpassen](../get-started/customize-boot-images.md). Zie [Opstartinstallatiekopieën beheren met System Center Configuration Manager](../get-started/manage-boot-images.md) voor meer informatie over opstartinstallatiekopieën.  

### <a name="windows-server-update-services-wsus"></a>Windows Server Update Services (WSUS)  
U moet de volgende WSUS 4.0-hotfixes installeren:
  - [Hotfix 3095113](https://support.microsoft.com/kb/3095113) is nodig voor onderhoud van Windows 10 waarbij de infrastructuur voor software-updates wordt gebruikt voor het ophalen van upgrades voor Windows 10-onderdelen. Wanneer u WSUS 3.2 hebt, moet u takenreeksen gebruiken om bij te werken naar Windows 10. Zie voor meer informatie [Windows beheren als een service](../deploy-use/manage-windows-as-a-service.md).  
  - [Hotfix 3159706](https://support.microsoft.com/kb/3159706) is nodig om Windows 10-onderhoudsdashboard om een upgrade van computers voor de Update voor Windows 10 verjaardag, evenals voor subsequence versies te gebruiken. Er zijn handmatige stappen wordt beschreven in het ondersteuningsartikel die u uitvoeren moet om deze hotfix te installeren. Zie voor meer informatie [Windows beheren als een service](../deploy-use/manage-windows-as-a-service.md).


### <a name="internet-information-services-iis-on-the-site-system-servers"></a>IIS (Internet Information Services) op de sitesysteemservers  
 IIS is vereist voor het distributiepunt, het statusmigratiepunt en het beheerpunt. Zie voor meer informatie over deze vereiste [Site en site-systeemvereisten](../../core/plan-design/configs/site-and-site-system-prerequisites.md).  

### <a name="windows-deployment-services-wds"></a>Windows Deployment Services (WDS)  
 WDS is nodig voor PXE-implementaties wanneer u multicast gebruikt om de bandbreedte in uw implementaties te optimaliseren en voor de offline-installatie van afbeeldingen. Als de provider is geïnstalleerd op een externe server, moet u WDS installeren op de siteserver en de externe provider. Zie [Windows Deployment Services](#BKMK_WDS) in dit onderwerp voor meer informatie.  

### <a name="dynamic-host-configuration-protocol-dhcp"></a>Dynamic Host Configuration Protocol (DHCP)  
 DHCP is vereist voor PXE-implementaties. U moet een werkende DHCP-server hebben met een actieve host om besturingssystemen te implementeren door gebruik te maken van PXE. Zie voor meer informatie over PXE-implementaties [PXE gebruiken om Windows te implementeren via het netwerk](../deploy-use/use-pxe-to-deploy-windows-over-the-network.md).  

### <a name="supported-operating-systems-and-hard-disk-configurations"></a>Ondersteunde besturingssystemen en vaste-schijfconfiguraties  
 Zie voor meer informatie over de versies van besturingssystemen en vaste-schijfconfiguraties die door Configuration Manager worden ondersteund wanneer u besturingssystemen implementeert [besturingssystemen ondersteund](#BKMK_SupportedOS) en [ondersteunde schijfconfiguraties](#BKMK_SupportedDiskConfig).  

### <a name="windows-device-drivers"></a>Windows-apparaatstuurprogramma 's  
 Windows apparaatstuurprogramma's kunnen gebruikt worden wanneer u het besturingssysteem installeert op de doelcomputer en wanneer u Windows PE uitvoert door een opstartinstallatiekopie te gebruiken. Zie voor meer informatie over apparaatstuurprogramma's [stuurprogramma's beheren](../get-started/manage-drivers.md).  

##  <a name="BKMK_InternalDependencies"></a> Configuration Manager-afhankelijkheden  
 Hieronder vindt u informatie over Configuration Manager-besturingssysteem vereisten voor implementatie.  

### <a name="operating-system-image"></a>Installatiekopie van besturingssysteem  
 Installatiekopieën van besturingssystemen in Configuration Manager worden opgeslagen met de WIM-bestandsindeling (Windows Imaging). Ze omvatten een gecomprimeerde verzameling referentiebestanden en -mappen die zijn vereist om een besturingssysteem correct te installeren en te configureren op een computer. Zie voor meer informatie [installatiekopieën van besturingssystemen beheren](../get-started/manage-operating-system-images.md).  

### <a name="driver-catalog"></a>Stuurprogrammacatalogus  
 Voor het implementeren van een stuurprogramma, moet u het apparaatstuurprogramma importeren, inschakelen en beschikbaar maken op een distributiepunt dat de Configuration Manager-client toegang kan hebben. Zie voor meer informatie over de stuurprogrammacatalogus [stuurprogramma's beheren](../get-started/manage-drivers.md).  

### <a name="management-point"></a>Beheerpunt  
 Via beheerpunten wordt informatie overgedragen tussen clientcomputers en de Configuration Manager-site. De client gebruikt een beheerpunt om takenreeksen uit te voeren die vereist zijn om de implementatie van het besturingssysteem te vervolledigen.  

 Zie voor meer informatie over takenreeksen [planningsoverwegingen voor het automatiseren van taken](planning-considerations-for-automating-tasks.md).  

### <a name="distribution-point"></a>Distributiepunt  
 Distributiepunten worden in de meeste implementaties gebruikt om de gegevens op te slaan die gebruikt worden om een besturingssysteem te implementeren, zoals de installatiekopie van een besturingssysteem of van stuurprogrammapakketten. Takenreeksen halen typisch gegevens van een distributiepunt om het besturingssysteem te implementeren.  

 Zie voor meer informatie over het installeren van distributiepunten en beheren van inhoud [inhoud en infrastructuur beheren](../../core/servers/deploy/configure/manage-content-and-content-infrastructure.md).  

### <a name="pxe-enabled-distribution-point"></a>Distributiepunt met PXE-functionaliteit  
 Om PXE-geïnitieerde implementaties te implementeren, moet u een distributiepunt configureren zodat het PXE-verzoeken van clients aanvaardt. Zie voor meer informatie over het configureren van het distributiepunt [een distributiepunt configureren](/sccm/core/servers/deploy/configure/install-and-configure-distribution-points#pxe).  

### <a name="multicast-enabled-distribution-point"></a>Multicast-distributiepunt  
 Om uw implementaties van besturingssystemen te optimaliseren door multicast te gebruiken, moet u een distributiepunt configureren zodat het multicast kan ondersteunen. Zie voor meer informatie over het configureren van het distributiepunt [een distributiepunt configureren](/sccm/core/servers/deploy/configure/install-and-configure-distribution-points#multicast).   

### <a name="state-migration-point"></a>Statusmigratiepunt  
 Wanneer u gegevens over de gebruikersstatus opneemt en herstelt voor gelijktijdige implementaties en voor het vernieuwen van implementaties, moet u een statusmigratiepunt configureren om gebruikersgegevens op te slaan op een andere computer.  

 Zie [Statusmigratiepunt](../get-started/prepare-site-system-roles-for-operating-system-deployments.md#BKMK_StateMigrationPoints) voor meer informatie over hoe het configureren van een statusmigratiepunt.  

 Zie voor meer informatie over het vastleggen en herstellen van gebruikersstatus [Gebruikersstatus beheren](../get-started/manage-user-state.md).  

### <a name="service-connection-point"></a>Serviceverbindingspunt  
 Als u WaaS (Windows as a Service) gebruikt om Windows 10 Current Branch te implementeren, moet het serviceaansluitpunt zijn geïnstalleerd. Zie voor meer informatie [Windows beheren als een service](../deploy-use/manage-windows-as-a-service.md).  

### <a name="reporting-services-point"></a>Reporting Services-punt  
 Voor het gebruik van Configuration Manager-rapporten voor implementaties van besturingssystemen, moet u installeren en configureren van een reporting services-punt. Zie voor meer informatie [rapportage](../../core/servers/manage/reporting.md).  

### <a name="security-permissions-for-operating-system-deployments"></a>Machtigingen voor implementaties van besturingssystemen  
 De beveiligingsrol voor **Beheerder besturingssysteemimplementatie** is een ingebouwde rol die niet kan worden gewijzigd. U kunt evenwel de rol kopiëren, wijzigingen maken en dan deze wijzigingen opslaan als een nieuwe aangepaste beveiligingsrol. Hier zijn enkele machtigingen die rechtstreeks van toepassing zijn op besturingssysteemimplementaties:  

-   **Installatiekopiepakket**: Maken, verwijderen, wijzigen, map wijzigen, Object verplaatsen, lezen, beveiligingsbereik instellen  

-   **Apparaatstuurprogramma's**: Maken, verwijderen, wijzigen, map wijzigen, rapport wijzigen, Object verplaatsen, lezen, rapport uitvoeren  

-   **Stuurprogrammapakket**: Maken, verwijderen, wijzigen, map wijzigen, Object verplaatsen, lezen, beveiligingsbereik instellen  

-   **Installatiekopie van besturingssysteem**: Maken, verwijderen, wijzigen, map wijzigen, Object verplaatsen, lezen, beveiligingsbereik instellen  

-   **Besturingssysteeminstallatiepakket**: Maken, verwijderen, wijzigen, map wijzigen, Object verplaatsen, lezen, beveiligingsbereik instellen  

-   **Taakvolgordepakket**: Maken, het maken van de taak Takenreeksmedia, verwijderen, wijzigen, map wijzigen, rapport wijzigen, Object verplaatsen, lezen, rapport uitvoeren, Veiligheidsbereik instellen  

 Zie [Aangepaste beveiligingsrollen maken](../../core/servers/deploy/configure/configure-role-based-administration.md#BKMK_CreateSecRole) voor meer informatie over aangepaste beveiligingsrollen.  

### <a name="security-scopes-for-operating-system-deployments"></a>Beveiligingsbereiken voor implementaties van besturingssystemen  
 Gebruik veiligheidsbereiken om gebruikers met beheerdersrechten te voorzien van toegang tot te beveiligen objecten die gebruikt worden in implementaties van besturingssystemen, zoals kopieën van besturingssystemen en installatiekopieën, stuurprogrammapakketten en takenreekspakketten. Zie [Beveiligingsbereiken](../../core/understand/fundamentals-of-role-based-administration.md#bkmk_PlanScope) voor meer informatie.  

##  <a name="BKMK_WDS"></a> Windows Deployment Services  
 Windows Deployment Services (WDS) moeten geïnstalleerd zijn op dezelfde server als de distributiepunten die u configureert om PXE of multicast te ondersteunen. WDS is opgenomen in het besturingssysteem van de server. Voor PXE-implementaties is WDS de service die het opstarten van PXE uitvoert. Wanneer het distributiepunt is geïnstalleerd en ingeschakeld is voor PXE, installeert Configuration Manager een provider in WDS, die de WDS PXE-opstartfuncties gebruikt.  

> [!NOTE]  
>  Als de server opnieuw opstarten moet, wordt de installatie van WDS kan mislukken. 

 Andere WDS-configuraties die moeten worden beschouwd zijn onder meer de volgende:  

-   De WDS-installatie op de server vereist dat de beheerder lid is van de lokale groep beheerders.  

-   De WDS-server moet lid zijn van een Active Directory-domein of een domeinbeheerder voor een Active Directory-domein. Alle Windows-domein- en forestconfiguraties ondersteunen WDS.  

-   Als de provider is geïnstalleerd op een externe server, moet u WDS installeren op de siteserver en de externe provider.  

###  <a name="BKMK_WDSandDHCP"></a> Overwegingen wanneer u WDS en DHCP op dezelfde server uitvoert  
 Houd rekening met de volgende configuratiekwesties als u van plan bent het distributiepunt te hosten op een server waarop ook DHCP wordt uitgevoerd.  

-   U moet beschikken over een werkende DHCP-server met een actief bereik. Windows Deployment Services maakt gebruik van PXE, waarvoor een DHCP-server vereist is.  

-   Voor DHCP en Windows Deployment Services moet poortnummer 67 worden gebruikt. Als u voor Windows Deployment Services en DHCP dezelfde host gebruikt, kunt u DHCP of het distributiepunt dat is geconfigureerd voor PXE, verplaatsen naar een aparte server. U kunt ook de volgende procedure gebruiken om de Windows Deployment Services-server te configureren zodat deze luistert op een andere poort.  

    #### <a name="to-configure-the-windows-deployment-services-server-to-listen-on-a-different-port"></a>De Windows Deployment Services-server configureren zodat deze luistert op een andere poort  

    1.  Wijzig de volgende registersleutel:  

         **HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\WDSServer\Providers\WDSPXE**  

    2.  De registerwaarde instellen op: **UseDHCPPorts = 0**  

    3.  Voer de volgende opdracht uit op de server om de nieuwe configuratie van kracht te laten worden:  

         `WDSUTIL /Set-Server /UseDHCPPorts:No /DHCPOption60:Yes`  

-   Een DNS-server is vereist voor het uitvoeren van Windows Deployment Services.  

-   De volgende UDP-poorten moeten geopend zijn op de Windows Deployment Services-server.  

    -   Poort 67 (DHCP)  

    -   Poort 69 (TFTP)  

    -   Poort 4011 (PXE)  

    > [!NOTE]  
    >  Als DHCP-verificatie vereist is op de server, moet DHCP-clientpoort 68 bovendien geopend zijn op de server.  

##  <a name="BKMK_SupportedOS"></a> Ondersteunde besturingssystemen  
 Alle Windows-besturingssystemen vermeld als ondersteunde clientbesturingssystemen in [ondersteunde besturingssystemen voor clients en apparaten](../../core/plan-design/configs/supported-operating-systems-for-clients-and-devices.md) worden ondersteund voor implementaties van besturingssystemen.  

##  <a name="BKMK_SupportedDiskConfig"></a> Ondersteunde schijfconfiguraties  
 De configuratiecombinaties van harde schijf op referentie- en doelcomputers die worden ondersteund voor besturingssysteemimplementatie van Configuration Manager worden weergegeven in de volgende tabel.  

|Harde-schijfconfiguratie van referentiecomputer|Harde-schijfconfiguratie van doelcomputer|  
|------------------------------------------------|--------------------------------------------------|  
|Standaardschijf|Standaardschijf|  
|Eenvoudig volume op een dynamische schijf|Eenvoudig volume op een dynamische schijf|  

 Configuration Manager ondersteunt het vastleggen van een besturingssysteeminstallatiekopie alleen vanaf computers die zijn geconfigureerd met eenvoudige volumes. Er wordt geen ondersteuning geboden voor de volgende harde-schijfconfiguraties:  

-   Spanned volumes  

-   Striped volumes (RAID 0)  

-   Gespiegelde volumes (RAID-1)  

-   Pariteitsvolumes (RAID-5)  

 De volgende tabel ziet een aanvullende harde-schijfconfiguratie op de bron- en doelcomputers die niet wordt ondersteund bij installatie van Configuration Manager-besturingssysteem.  

|Harde-schijfconfiguratie van referentiecomputer|Harde-schijfconfiguratie van doelcomputer|  
|------------------------------------------------|--------------------------------------------------|  
|Standaardschijf|Dynamische schijf|  

## <a name="next-steps"></a>Volgende stappen
[Implementatie van het besturingssysteem voorbereiden](../get-started/prepare-for-operating-system-deployment.md)
