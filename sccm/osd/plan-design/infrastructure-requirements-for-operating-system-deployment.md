---
title: Vereisten voor de infrastructuur OSD
titleSuffix: Configuration Manager
description: Informatie over de externe en de product-afhankelijkheden en de vereisten voor implementatie van besturingssysteem
ms.custom: na
ms.date: 03/22/2018
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-osd
ms.tgt_pltfrm: na
ms.topic: get-started-article
ms.assetid: 1dc74219-7ff5-4e3b-b4f6-5aad663bb75b
caps.latest.revision: ''
author: aczechowski
ms.author: aaroncz
manager: dougeby
ms.openlocfilehash: 36e49206154a1c061fb8266e0c8ed8691cc4d4f0
ms.sourcegitcommit: 11bf4ed40ed0cbb10500cc58bbecbd23c92bfe20
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 03/23/2018
---
# <a name="infrastructure-requirements-for-os-deployment-in-system-center-configuration-manager"></a>Vereisten voor de infrastructuur voor besturingssysteemimplementatie in System Center Configuration Manager

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*

Implementatie van een besturingssysteem in Configuration Manager heeft externe afhankelijkheden en afhankelijkheden binnen het product. Gebruik dit artikel kunt u de infrastructuur voorbereiden voor implementatie van het besturingssysteem.  



##  <a name="BKMK_ExternalDependencies"></a> Afhankelijkheden extern aan Configuration Manager  
 Deze sectie bevat informatie over externe hulpprogramma's, installatie-kits en OS-versies die nodig zijn voor het implementeren van besturingssystemen in Configuration Manager.  

### <a name="windows-adk-for-windows-10"></a>Windows ADK voor Windows 10  
 De Windows Assessment and Deployment Kit (ADK) is een set van hulpprogramma's die ondersteuning bieden voor de configuratie en implementatie van Windows. Configuration Manager gebruikt de Windows ADK voor het automatiseren van acties zoals het installeren van Windows, het vastleggen van installatiekopieën en het migreren van gebruikersprofielen en gegevens.  

 De volgende functies van Windows ADK moeten worden geïnstalleerd op de siteserver van de site op het hoogste niveau in de hiërarchie, op de siteserver van elke primaire site in de hiërarchie en op de SMS Provider sitesysteemserver:  

-   Hulpprogramma voor migratie van gebruikersstatus (USMT) <sup>1</sup>  

-   Windows-hulpprogramma's  

-   Windows Voorinstallatieomgeving (Windows PE)

Zie voor een lijst van de versies van Windows 10 ADK die u met verschillende versies van Configuration Manager gebruiken kunt [ondersteuning voor Windows 10](/sccm/core/plan-design/configs/support-for-windows-10#windows-10-adk).

 <sup>1</sup> USMT is niet vereist op de SMS Provider sitesysteemserver.  

> [!NOTE]  
>  U moet handmatig de Windows ADK installeren op elke siteserver voordat u de Configuration Manager-site installeert.  

 Zie voor meer informatie:  

-   [Windows ADK voor Windows 10-scenario's voor IT-professionals](/windows/deployment/windows-adk-scenarios-for-it-pros)  

-   [Download Windows ADK voor Windows 10](/windows-hardware/get-started/adk-install)  

-   [Ondersteuning voor Windows 10](/sccm/core/plan-design/configs/support-for-windows-10)  


### <a name="user-state-migration-tool-usmt"></a>Hulpprogramma voor migratie van gebruikersstatus (USMT)  
 Configuration Manager gebruikt een USMT-pakket dat de USMT 10-bronbestanden voor het vastleggen en herstellen van status van de gebruiker als onderdeel van uw implementatie van het besturingssysteem bevat. Setup van Configuration Manager op het hoogste niveau maakt automatisch het USMT-pakket. USMT 10 vastgelegd Gebruikersstatus van Windows 7, Windows 8, Windows 8.1 en Windows 10.  

 Zie voor meer informatie:  

-   [Algemene migratiescenario's voor USMT 10](/windows/deployment/usmt/usmt-common-migration-scenarios)  

-   [De gebruikersstatus beheren](../get-started/manage-user-state.md)  

### <a name="windows-pe"></a>Windows PE  
 Windows PE wordt gebruikt om een computer met een installatiekopie op te starten. Er is een Windowsversie met beperkte diensten dat wordt gebruikt tijdens voorinstallatie en implementatie van Windows. De volgende lijst bevat de ondersteunde versies van Windows ADK voor Configuration Manager, huidige vertakking:  

-   **Windows ADK-versie**  

     Windows ADK voor Windows 10. Zie voor meer informatie [ondersteuning voor Windows 10](/sccm/core/plan-design/configs/support-for-windows-10#windows-10-adk).

-   **Windows PE-versies voor installatiekopieën die aanpasbaar zijn via de Configuration Manager-console**  

     Windows PE 10  

-   **Ondersteunde Windows PE-versies voor installatiekopieën die niet aanpasbaar zijn via de Configuration Manager-console**  

     Windows PE 3.1<sup>1</sup> en Windows PE 5  

     <sup>1</sup> u kunt alleen een opstartinstallatiekopie toevoegen aan Configuration Manager wanneer deze is gebaseerd op Windows PE 3.1. Installeer Windows AIK Supplement voor Windows 7 SP1 om een upgrade van Windows AIK voor Windows 7 (gebaseerd op Windows PE 3) naar Windows AIK Supplement voor Windows 7 SP1 (gebaseerd op Windows PE 3.1) uit te voeren. U kunt Windows AIK Supplement voor Windows 7 SP1 downloaden via het [Microsoft Downloadcentrum](https://www.microsoft.com/download/details.aspx?id=5188).  

     Bijvoorbeeld, wanneer u Configuration Manager hebt, kunt u opstartinstallatiekopieën uit Windows ADK voor Windows 10 (gebaseerd op Windows PE 10) aanpassen via de Configuration Manager-console. Hoewel installatiekopieën die zijn gebaseerd op Windows PE 5 wel worden wel ondersteund, moet u ze aanpassen op een andere computer en moet u die versie van DISM gebruiken die is geïnstalleerd met Windows ADK voor Windows 8. Vervolgens kunt u de installatiekopie toevoegen aan de Configuration Manager-console. Voor meer informatie over de stappen voor het aanpassen van een installatiekopie (toevoegen van optionele componenten en stuurprogramma's), inschakelen van opdrachtondersteuning aan de opstartinstallatiekopie, de installatiekopie toevoegen aan de Configuration Manager-console en distributiepunten bijwerken met de installatiekopie, Zie [opstartinstallatiekopieën aanpassen](../get-started/customize-boot-images.md). Zie [Opstartinstallatiekopieën beheren met System Center Configuration Manager](../get-started/manage-boot-images.md) voor meer informatie over opstartinstallatiekopieën.  


### <a name="windows-server-update-services-wsus"></a>Windows Server Update Services (WSUS)  
 WSUS is vereist voor de software-updatepunt is vereist voor het installeren van software-updates tijdens de implementatie van het besturingssysteem. Zie voor meer informatie [installeren van een configureren van een software-updatepunt](/sccm/sum/get-started/install-a-software-update-point).


### <a name="internet-information-services-iis-on-the-site-system-servers"></a>IIS (Internet Information Services) op de sitesysteemservers  
 IIS is vereist voor het distributiepunt, het statusmigratiepunt en het beheerpunt. Zie voor meer informatie [Site and site system prerequisites](../../core/plan-design/configs/site-and-site-system-prerequisites.md) (Vereisten voor sites en sitesystemen).  


### <a name="windows-deployment-services-wds"></a>Windows Deployment Services (WDS)  
 WDS is nodig voor PXE-implementaties en wanneer u multicast gebruikt om te bandbreedte in uw implementaties te optimaliseren. Zie voor meer informatie [Windows Deployment Services](#BKMK_WDS) in dit artikel.  


### <a name="dynamic-host-configuration-protocol-dhcp"></a>Dynamic Host Configuration Protocol (DHCP)  
 DHCP is vereist voor PXE-implementaties. U moet een werkende DHCP-server hebben met een actieve host om besturingssystemen te implementeren door gebruik te maken van PXE. Zie voor meer informatie over PXE-implementaties [PXE gebruiken om Windows te implementeren via het netwerk](../deploy-use/use-pxe-to-deploy-windows-over-the-network.md).  


### <a name="supported-operating-systems-and-hard-disk-configurations"></a>Ondersteunde besturingssystemen en vaste-schijfconfiguraties  
 Zie voor meer informatie over de versies van besturingssystemen en vaste-schijfconfiguraties die door Configuration Manager worden ondersteund wanneer u besturingssystemen implementeert [ondersteunde besturingssystemen](#BKMK_SupportedOS) en [ondersteund schijfconfiguraties](#BKMK_SupportedDiskConfig).  


### <a name="windows-device-drivers"></a>Windows-apparaatstuurprogramma 's  
 Windows-apparaatstuurprogramma's kunnen worden gebruikt wanneer u het besturingssysteem op de doelcomputer installeert. Ze worden ook gebruikt wanneer u Windows PE in een opstartinstallatiekopie uitvoert. Zie voor meer informatie [stuurprogramma's beheren](../get-started/manage-drivers.md).  



##  <a name="BKMK_InternalDependencies"></a> Configuration Manager-afhankelijkheden  
 Deze sectie bevat informatie over Configuration Manager-OS vereisten voor implementatie.  


### <a name="os-image"></a>Installatiekopie van het besturingssysteem  
 Installatiekopieën van het besturingssysteem in Configuration Manager worden opgeslagen in de bestandsindeling (WIM: Windows Imaging). Ze omvatten een gecomprimeerde verzameling referentiebestanden en-mappen. Deze installatiekopieën zijn vereist voor het installeren en configureren van een besturingssysteem op een computer. Zie voor meer informatie [installatiekopieën van besturingssystemen beheren](../get-started/manage-operating-system-images.md).  


### <a name="driver-catalog"></a>Stuurprogrammacatalogus  
 Voor het implementeren van een stuurprogramma, moet u het apparaatstuurprogramma importeren, inschakelen en beschikbaar maken op een distributiepunt dat de Configuration Manager-client toegang kan hebben. Zie voor meer informatie over de stuurprogrammacatalogus [stuurprogramma's beheren](../get-started/manage-drivers.md).  


### <a name="management-point"></a>Beheerpunt  
 Via beheerpunten wordt informatie overgedragen tussen clients en de Configuration Manager-site. Uitvoeren van de takenreeks voor het voltooien van de implementatie van het besturingssysteem gebruikt de client een beheerpunt. Zie voor meer informatie over takenreeksen [planningsoverwegingen voor het automatiseren van taken](planning-considerations-for-automating-tasks.md).  


### <a name="distribution-point"></a>Distributiepunt  
 Distributiepunten worden in de meeste implementaties gebruikt voor het opslaan van de gegevens die worden gebruikt voor het implementeren van een besturingssysteem, zoals de afbeelding of het stuurprogramma-pakketten. Takenreeksen halen typisch gegevens van een distributiepunt voor het implementeren van het besturingssysteem. Zie voor meer informatie over het installeren van distributiepunten en beheren van inhoud [inhoud en infrastructuur beheren](../../core/servers/deploy/configure/manage-content-and-content-infrastructure.md).  


### <a name="pxe-enabled-distribution-point"></a>Distributiepunt met PXE-functionaliteit  
 Om PXE-geïnitieerde implementaties te implementeren, moet u een distributiepunt configureren zodat het PXE-verzoeken van clients aanvaardt. Zie voor meer informatie [een distributiepunt configureren](/sccm/core/servers/deploy/configure/install-and-configure-distribution-points#pxe).


### <a name="multicast-enabled-distribution-point"></a>Multicast-distributiepunt  
 Uw besturingssysteem om implementaties te optimaliseren door multicast, moet u een distributiepunt voor multicast-ondersteuning configureren. Zie voor meer informatie [een distributiepunt configureren](/sccm/core/servers/deploy/configure/install-and-configure-distribution-points#multicast).   


### <a name="state-migration-point"></a>Statusmigratiepunt  
 Wanneer u gegevens over de gebruikersstatus opneemt en herstelt voor gelijktijdige implementaties en voor het vernieuwen van implementaties, moet u een statusmigratiepunt configureren om gebruikersgegevens op te slaan op een andere computer.  

 Zie [Statusmigratiepunt](../get-started/prepare-site-system-roles-for-operating-system-deployments.md#BKMK_StateMigrationPoints) voor meer informatie over hoe het configureren van een statusmigratiepunt.  

 Zie voor meer informatie over het vastleggen en herstellen van gebruikersstatus [Gebruikersstatus beheren](../get-started/manage-user-state.md).  


### <a name="reporting-services-point"></a>Reporting Services-punt  
 Voor het gebruik van Configuration Manager-rapporten voor OS-implementaties, moet u installeren en configureren van een reporting services-punt. Zie voor meer informatie [rapportage](../../core/servers/manage/reporting.md).  


### <a name="security-permissions-for-os-deployments"></a>Machtigingen voor implementaties van besturingssysteem  
 De **Besturingssysteemimplementatie** beveiligingsrol is een ingebouwde rol die u niet kunt wijzigen. U kunt evenwel de rol kopiëren, wijzigingen maken en dan deze wijzigingen opslaan als een nieuwe aangepaste beveiligingsrol. Hier zijn enkele machtigingen die rechtstreeks van toepassing op implementaties van besturingssysteem:  

-   **Installatiekopiepakket**: Maken, verwijderen, wijzigen, map wijzigen, Object verplaatsen, lezen, beveiligingsbereik instellen  

-   **Apparaatstuurprogramma's**: Maken, verwijderen, wijzigen, map wijzigen, rapport wijzigen, Object verplaatsen, lezen, rapport uitvoeren  

-   **Stuurprogrammapakket**: Maken, verwijderen, wijzigen, map wijzigen, Object verplaatsen, lezen, beveiligingsbereik instellen  

-   **Installatiekopie van besturingssysteem**: Maken, verwijderen, wijzigen, map wijzigen, Object verplaatsen, lezen, beveiligingsbereik instellen  

-   **Besturingssysteeminstallatiepakket**: Maken, verwijderen, wijzigen, map wijzigen, Object verplaatsen, lezen, beveiligingsbereik instellen  

-   **Taakvolgordepakket**: Maken, het maken van de taak Takenreeksmedia, verwijderen, wijzigen, map wijzigen, rapport wijzigen, Object verplaatsen, lezen, rapport uitvoeren, Veiligheidsbereik instellen  

 Zie voor meer informatie [aangepaste beveiligingsrollen maken](../../core/servers/deploy/configure/configure-role-based-administration.md#BKMK_CreateSecRole).  


### <a name="security-scopes-for-os-deployments"></a>Beveiligingsbereiken voor implementaties van besturingssysteem  
 Gebruik veiligheidsbereiken om gebruikers met beheerdersrechten toegang bieden tot de beveiligbare objecten in de OS-implementaties, zoals besturingssysteem en opstartinstallatiekopieën, stuurprogrammapakketten en takenreekspakketten gebruikt. Zie [Beveiligingsbereiken](../../core/understand/fundamentals-of-role-based-administration.md#bkmk_PlanScope) voor meer informatie.  



##  <a name="BKMK_WDS"></a> Windows Deployment Services  
 Windows Deployment Services (WDS) moeten geïnstalleerd zijn op dezelfde server als de distributiepunten die u configureert om PXE of multicast te ondersteunen. WDS is opgenomen in het besturingssysteem van de server. Voor PXE-implementaties is WDS de service die het opstarten van PXE uitvoert. Wanneer het distributiepunt is geïnstalleerd en ingeschakeld is voor PXE, installeert Configuration Manager een provider in WDS, die de WDS PXE-opstartfuncties gebruikt.  

> [!NOTE]  
>  Als de server opnieuw opstarten moet, wordt de installatie van WDS kan mislukken. 


### <a name="wds-requirements"></a>WDS-vereisten  

-   De WDS-installatie op de server vereist dat de beheerder lid is van de lokale groep Administrators.  

-   De WDS-server moet lid zijn van een Active Directory-domein of een domeinbeheerder voor een Active Directory-domein. Alle Windows-domein- en forestconfiguraties ondersteunen WDS.  

-   Als de provider is geïnstalleerd op een externe server, moet u WDS installeren op de siteserver en de externe provider.  


###  <a name="BKMK_WDSandDHCP"></a> Overwegingen wanneer u WDS en DHCP op dezelfde server uitvoert  
 Houd rekening met de volgende configuratiekwesties als u van plan bent het distributiepunt te hosten op een server waarop ook DHCP wordt uitgevoerd.  

-   U moet beschikken over een werkende DHCP-server met een actief bereik. WDS wordt gebruikt voor PXE, waarvoor een DHCP-server vereist.  

-   DHCP en WDS vereisen poortnummer 67. Als u dezelfde host WDS en DHCP, kunt u DHCP of het distributiepunt dat is geconfigureerd voor PXE naar een aparte server. Of u kunt de volgende procedure de WDS-server om te luisteren op een andere poort configureren.  

    #### <a name="to-configure-the-wds-server-to-listen-on-a-different-port"></a>De WDS-server om te luisteren op een andere poort configureren  

    1.  Wijzig de volgende registersleutel:  

         `HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\WDSServer\Providers\WDSPXE`  

    2.  Stel de registerwaarde **UseDHCPPorts** naar **0**.  

    3.  Voer de volgende opdracht uit op de server om de nieuwe configuratie van kracht te laten worden:  

         `WDSUTIL /Set-Server /UseDHCPPorts:No /DHCPOption60:Yes`  

-   Een DNS-server is vereist voor het uitvoeren van WDS.  

-   De volgende UDP-poorten moeten geopend zijn op de WDS-server.  

    -   Poort 67 (DHCP)  

    -   Poort 69 (TFTP)  

    -   Poort 4011 (PXE)  

    > [!NOTE]  
    >  Als DHCP-verificatie is op de server vereist, moet u DHCP-clientpoort 68 geopend zijn op de server.  



##  <a name="BKMK_SupportedOS"></a> Ondersteunde besturingssystemen  
 Alle Windows-besturingssystemen vermeld als ondersteunde clients in [ondersteunde besturingssystemen voor clients en apparaten](../../core/plan-design/configs/supported-operating-systems-for-clients-and-devices.md) worden ondersteund voor implementatie van het besturingssysteem.  



##  <a name="BKMK_SupportedDiskConfig"></a> Ondersteunde schijfconfiguraties  
 De configuratiecombinaties van harde schijf op referentie- en doelcomputers die worden ondersteund voor implementatie van het besturingssysteem van de Configuration Manager worden weergegeven in de volgende tabel:  

|Harde-schijfconfiguratie van referentiecomputer|Harde-schijfconfiguratie van doelcomputer|  
|------------------------------------------------|--------------------------------------------------|  
|Standaardschijf|Standaardschijf|  
|Eenvoudig volume op een dynamische schijf|Eenvoudig volume op een dynamische schijf|  

 Configuration Manager ondersteunt het vastleggen van een installatiekopie van het besturingssysteem alleen vanaf computers die zijn geconfigureerd met eenvoudige volumes. Er is geen ondersteuning voor de volgende harde-schijfconfiguraties:  

-   Spanned volumes  

-   Striped volumes (RAID 0)  

-   Gespiegelde volumes (RAID-1)  

-   Pariteitsvolumes (RAID-5)  

 De volgende tabel ziet een aanvullende harde-schijfconfiguratie op de bron- en doelcomputers die niet wordt ondersteund met de implementatie van het besturingssysteem van de Configuration Manager.  

|Harde-schijfconfiguratie van referentiecomputer|Harde-schijfconfiguratie van doelcomputer|  
|------------------------------------------------|--------------------------------------------------|  
|Standaardschijf|Dynamische schijf|  



## <a name="next-steps"></a>Volgende stappen
- [Sitesysteemrollen voorbereiden voor OS-implementaties](/sccm/osd/get-started/prepare-site-system-roles-for-operating-system-deployments)
- [Implementatie van het besturingssysteem voorbereiden](../get-started/prepare-for-operating-system-deployment.md)
