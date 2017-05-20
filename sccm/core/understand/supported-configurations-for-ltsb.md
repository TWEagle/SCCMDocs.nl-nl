---
title: Ondersteunde configuraties voor de LTSB | Microsoft-documenten
description: Begrijp wat besturingssystemen en afhankelijke producten met de langetermijndoelen onderhoud vertakking van System Center Configuration Manager werken.
ms.custom: na
ms.date: 5/10/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: f0f818d4-7f45-402f-8758-dc88bc024953
caps.latest.revision: 0
author: Brenduns
ms.author: brenduns
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: f809c9327db9f298168674add2d09820fdecd1b8
ms.openlocfilehash: ec33d5febcbf7b57e220f7fe27db9671080fecff
ms.contentlocale: nl-nl
ms.lasthandoff: 05/17/2017


---
# <a name="supported-configurations-for-the-long-term-servicing-branch-of-system-center-configuration-manager"></a>Ondersteunde configuraties voor de lange termijn Servicing vertakking van System Center Configuration Manager

*Van toepassing op: System Center Configuration Manager (op lange termijn onderhoud vertakking)*

Gebruik de informatie in dit onderwerp om te begrijpen welke besturingssystemen en het product afhankelijkheden worden ondersteund door de langetermijndoelen onderhoud vertakking (LTSB) van Configuration Manager.
Als u niet anders wordt vermeld in dit of de LTSB onderwerpen van dezelfde configuraties en beperkingen die betrekking hebben op de huidige vertakking versie 1606 toepassing op de LTSB.  Als u conflicten optreden, gebruik de informatie die van toepassing op de versie die u gebruikt. Meestal is de LTSB beperkter dan voor de huidige vertakking.

## <a name="general-statement-of-support"></a>Algemeen gesproken van ondersteuning
De volgende producten en technologieën worden ondersteund door de vertakking van Configuration Manager. Ze zijn opgenomen in deze inhoud biedt echter geen snelle een uitbreiding van ondersteuning voor een product of de versie dan dat product afzonderlijke support lifecycle. Producten die zich buiten de levenscyclus van de ondersteuning worden niet ondersteund voor gebruik met Configuration Manager. Voor meer informatie gaat u naar de [Microsoft Support Lifecycle](http://go.microsoft.com/fwlink/p/?LinkId=208270) website en lees de [Veelgestelde vragen over Microsoft Support Lifecycle-beleid](http://go.microsoft.com/fwlink/p/?LinkId=31976).

Bovendien, producten en versies die niet worden weergegeven in de volgende onderwerpen worden alleen ondersteund als ze is aangekondigd op het [Enterprise Mobility + Beveiligingsblog](https://blogs.technet.microsoft.com/enterprisemobility/).

**Beperkingen voor toekomstige ondersteuning:** De LTSB beperkte ondersteuning voor de nieuwe server en client-besturingssystemen en product afhankelijkheden. De lijst met platforms voor het LTSB wordt vastgesteld voor de duur van de release:

**Windows:**
- Alleen kwaliteit en security updates voor Windows worden ondersteund.
- Er is geen ondersteuning wordt voor de huidige vertakkingen (CB), huidige vertakkingen voor business (CBB) of LTSB van Windows 10 toegevoegd.
-    Er is geen ondersteuning voor nieuwe primaire versies van Windows Server.

**SQL Server:**
- Alleen kwaliteit en beveiligingsupdates of kleine upgrades zoals servicepacks, wordt ondersteund voor SQL Server.
- Er is geen ondersteuning voor nieuwe primaire versies van SQL Server.  

## <a name="site-systems-and-servers"></a>Site-systemen en servers
De LTSB ondersteunt het gebruik van de volgende besturingssystemen van de Windows-computer als site-systemen.  Elk besturingssysteem heeft dezelfde vereisten en beperkingen als hetzelfde beginpunt in [ondersteunde besturingssystemen voor sitesysteemservers](/sccm/core/plan-design/configs/supported-operating-systems-for-site-system-servers).  De Server Core-installatie van Windows 2012 R2 moet bijvoorbeeld een x64 versie, wordt alleen ondersteund als host voor een distributiepunt en biedt geen ondersteuning voor PXE of Multicast.

**Ondersteunde besturingssystemen:**
- Windows Server 2016
- WindowsServer 2012 (x 64): Standard, Datacenter
- Windows Server 2008 R2 met SP1 (x 64): Standard, Enterprise, Datacenter
- WindowsServer 2008 SP2 (x 86, x 64): Standard, Enterprise, Datacenter *(Zie Opmerking 1)*
- Windows 10 Enterprise 2015 LTSB (x86, x64)
- Windows 10 Enterprise 2016 LTSB (x86, x64)
- Windows 8.1 (x86, x64): Professional, Enterprise
- Windows 7 met SP1 (x 86, x 64): Professional, Enterprise, Ultimate
- De Server Core-installatie van Windows Server 2012
- De Server Core-installatie van Windows Server 2012 R2    

*Houd er rekening mee 1*: Dit besturingssysteem wordt niet ondersteund voor siteservers of sitesysteemrollen met uitzondering van het distributiepunt en het pull-distributiepunt. U kunt blijven gebruiken dit besturingssysteem als een distributiepunt tot buitengebruikstelling van deze ondersteuning is aangekondigd of dit besturingssysteem uitgebreide ondersteuning zijn verstreken. Zie voor meer informatie [installatie van System Center Configuration Manager CB en LTSB mislukt op Windows Server 2008](https://support.microsoft.com/help/4015095).

## <a name="client-management"></a>Clientbeheer
De volgende secties beschrijven de client-besturingssystemen die u met de LTSB beheren kunt. De LTSB biedt geen ondersteuning voor het toevoegen van nieuwe besturingssystemen als ondersteunde clients.

### <a name="windows-computers"></a>Windows-computers
U kunt de LTSB gebruiken de volgende Windows-computer om besturingssystemen te beheren met de Configuration Manager-clientsoftware die is opgenomen met Configuration Manager. Zie voor meer informatie [het implementeren van clients op Windows-computers in System Center Configuration Manager](/sccm/core/clients/deploy/deploy-clients-to-windows-computers).

**Ondersteunde besturingssystemen:**
- Windows Server 2016
- Windows Server 2012 R2 (x 64): Standard, Datacenter (Zie Opmerking 1)
- WindowsServer 2012 (x 64): Standard, Datacenter (Zie Opmerking 1)
- Windows Storage Server 2012 R2 (x 64)
- Windows Storage Server 2012 (x 64)
- Windows Server 2008 R2 met SP1 (x 64): Standard, Enterprise, Datacenter (Zie Opmerking 1)
- Windows Storage Server 2008 R2 (x 86, x 64): Workgroup, Standard, Enterprise
- WindowsServer 2008 SP2 (x 86, x 64): Standard, Enterprise, Datacenter (Zie Opmerking 1)
- Windows 10 Enterprise 2015 LTSB (x86, x64)
- Windows 10 Enterprise 2016 LTSB (x86, x64)
- Windows 8.1 (x86, x64): Professional, Enterprise
- Windows 7 met SP1 (x 86, x 64): Professional, Enterprise, Ultimate
- De Server Core-installatie van Windows Server 2012 R2 (x64) (Opmerking 2)
- De Server Core-installatie van Windows Server 2012 (x64) (Opmerking 2)
- De Server Core-installatie van Windows Server 2008 R2 SP1 (x64)
- De Server Core-installatie van Windows Server 2008 SP2 (x86, x64)

**(Zie Opmerking 1)**  Datacenter-versies worden ondersteund, maar niet gecertificeerd voor Configuration Manager.  
**(Zie Opmerking 2)**  Ter ondersteuning van push-clientinstallatie, moet de computer die deze versie van het besturingssysteem wordt uitgevoerd de functieservice bestandsserver voor de serverrol bestands- en opslagservices uitgevoerd. Zie voor meer informatie over het installeren van Windows-onderdelen op een Server Core-computer [installeren serverrollen en functies op een Server Core-Server](https://technet.microsoft.com/library/jj574158(v=ws.11).aspx) in de Windows Server 2012 TechNet library.

### <a name="windows-embedded"></a>Windows Embedded
U kunt de LTSB gebruiken voor het beheren van de volgende Windows Embedded-apparaten door de clientsoftware installeren op het apparaat.  Zie voor meer informatie [Planning voor clientimplementatie op Windows Embedded-apparaten in System Center Configuration Manager](/sccm/core/clients/deploy/plan/planning-for-client-deployment-to-windows-embedded-devices).

**Vereisten en beperkingen:**  

-   Alle clientfuncties worden ondersteund op ondersteunde Windows Embedded systemen waarop geen schrijffilters zijn ingeschakeld.  

-   Clients die gebruikmaken van een van de volgende worden ondersteund voor alle functies, met uitzondering van energiebeheer:  

    -   Verbeterde schrijffilters (EWF)    

    -   RAM-geheugen bestand gebaseerde schrijffilters (FBWF)    

    -   Unified Write Filters (UWF)  

-   De Toepassingscatalogus wordt niet ondersteund voor Windows Embedded-apparaat.  

-   Voordat u de gedetecteerde malware op Windows Embedded-apparaten op basis van Windows XP bewaken kunt, moet u het pakket van Microsoft Windows WMI-scripting installeren op het embedded-apparaat. Windows Embedded doel Designer gebruiken voor dit pakket installeert. De *WBEMDISP. DLL* en *WBEMDISP. TLB* bestanden zijn en deze moet worden geregistreerd in de map %windir%\System32\WBEM op het embedded-apparaat om ervoor te zorgen dat gedetecteerd schadelijke software wordt gerapporteerd.  

**Ondersteunde besturingssystemen:**  
-   Windows 10 Enterprise 2016 LTSB (x86, x64)  
-   Windows 10 Enterprise 2015 LTSB (x86, x64)  
-   Windows Embedded 8.1 Industry (x86, x64)    
-   Windows-Thin PC (x86, x64)    
-   Windows Embedded POSReady 7 (x86, x64)    
-   Windows Embedded Standard 7 met SP1 (x 86, x 64)    
-   Windows Embedded POSReady 2009 (x86)   
-   Windows Embedded Standard 2009 (x86)  

### <a name="windows-ce"></a>Windows CE  
 U kunt Windows CE-apparaten beheren met Configuration Manager verouderde clients van mobiele apparaten die zijn opgenomen met Configuration Manager.  

**Vereisten en beperkingen:**  

-   De client voor mobiele apparaten is 0.78 MB opslagruimte op de client te installeren. Een mobiel apparaat kan maximaal 256 KB extra opslagruimte aan te melden vereisen.    

-   Functies voor deze mobiele apparaten per platform en client variëren type. Zie voor informatie over het soort beheerfuncties die door Configuration Manager biedt ondersteuning voor een verouderde client van mobiele apparaten, [kiezen een oplossing voor Apparaatbeheer voor System Center Configuration Manager](/sccm/core/plan-design/choose-a-device-management-solution).  

**Ondersteunde besturingssystemen:**  

-   Windows CE 7.0 (ARM en x86 processors)  

**Ondersteunde talen zijn onder andere:**  
-   Chinees (vereenvoudigd en Traditioneel)    
-   Engels (V.S.)    
-   Frans (standaard)    
-   German    
-   Italian    
-   Japans  
-   Koreaans  
-   Portugees (Brazilië)  
-   Russisch  
-   Spaans (Spanje)  

### <a name="mac-computers"></a>Mac-computers  
 U kunt de LTSB Mac OS X-computers beheren met Configuration Manager-client voor Mac.

Het installatiepakket voor Mac-client wordt niet meegeleverd met de Configuration Manager-media. U kunt downloaden als onderdeel van het "Clients voor extra besturingssystemen" downloaden van de [Microsoft Download Center](http://go.microsoft.com/fwlink/?LinkID=525184).  

Ondersteuning voor Mac-besturingssystemen is beperkt tot die in deze sectie worden weergegeven. Ondersteuning omvat geen andere besturingssystemen die kan worden ondersteund door een toekomstige update voor Mac-clientinstallatiepakketten voor huidige vertakking.

Zie voor meer informatie [clients implementeren in Macs in System Center Configuration Manager](/sccm/core/clients/deploy/deploy-clients-to-macs).

**Ondersteunde versies:**  
-   Mac OS X 10.9 (Mavericks)  
-   Mac OS X 10.10 (Yosemite)  
-   Mac OS X 10.11 (El Capitan)  

## <a name="linux-and-unix-servers"></a>Linux en UNIX-servers
U kunt de LTSB Linux en UNIX-servers beheren met Configuration Manager-client voor Linux en UNIX.

De installatiepakketten voor Linux en UNIX-client zijn niet met de Configuration Manager-media opgegeven. Kunt u downloaden als onderdeel van het "Clients voor extra besturingssystemen" downloaden van de [Microsoft Download Center](http://go.microsoft.com/fwlink/?LinkID=525184). Naast het clientinstallatiepakketten bevat het downloaden van de client het script voor installatie die de installatie van de client op iedere computer beheert.

Ondersteuning voor Linux en UNIX-besturingssystemen is beperkt tot die in deze sectie worden weergegeven. Ondersteuning omvat geen extra besturingssystemen die door een toekomstige update voor Linux en UNIX-client-pakketten kunnen worden ondersteund voor huidige vertakking.

**Vereisten en beperkingen:**  

-   Afhankelijkheden van pakketbestanden besturingssysteem voor de client voor Linux en UNIX, Zie [vereisten voor clientimplementatie op Linux en UNIX-Servers](/sccm/core/clients/deploy/plan/planning-for-client-deployment-to-linux-and-unix-computers#bkmk_clientdeployprereqforlnu).  
-   Zie voor een overzicht van de beheermogelijkheden ondersteund voor computers waarop Linux of UNIX wordt uitgevoerd, [clients implementeren voor UNIX en Linux-servers in System Center Configuration Manager](/sccm/core/clients/deploy/deploy-clients-to-unix-and-linux-servers).  
-   Voor ondersteunde versies van Linux en UNIX bevat de vermelde versie alle volgende secundaire versies. Bijvoorbeeld, indien ondersteuning voor CentOS versie 6 wordt vermeld, omvat dit ook een latere secundaire versie van CentOS 6, zoals CentOS 6.3. Op dezelfde manier als ondersteuning voor een besturingssysteem dat gebruikmaakt van servicepacks, zoals SUSE Linux Enterprise Server 11 SP1, wordt vermeld bevat ondersteuning opeenvolgende servicepacks voor dat besturingssysteem.
-   Zie voor meer informatie over clientinstallatiepakketten en de universele Agent [clients implementeren voor UNIX en Linux-servers in System Center Configuration Manager](/sccm/core/clients/deploy/deploy-clients-to-unix-and-linux-servers).


**Ondersteunde versies:**   
De volgende versies worden ondersteund door het bestand aangegeven .tar.  
### <a name="aix"></a>AIX  

|Versie|Bestand|  
|-|-|  
|Versie 5.3 (Power)|CCM-Aix53ppc. &lt;bouwen\>.tar|  
|Versie 6.1 (Power)|CCM-Aix61ppc. &lt;bouwen\>.tar|  
|Versie 7.1 (Power)|CCM-Aix71ppc. &lt;bouwen\>.tar|  

### <a name="centos"></a>CentOS  

|Versie|Bestand|  
|-|-|  
|Versie 5 x86|CCM-Universalx86. &lt;bouwen\>.tar|  
|Versie 5 x64|CCM-Universalx64. &lt;bouwen\>.tar|  
|Versie 6 x86|CCM-Universalx86. &lt;bouwen\>.tar|  
|Versie 6 x64|CCM-Universalx64. &lt;bouwen\>.tar|  
|Versie 7 x64|CCM-Universalx64. &lt;bouwen\>.tar|  

### <a name="debian"></a>Debian  

|Versie|Bestand|    
|-|-|  
|Versie 5 x86|CCM-Universalx86. &lt;bouwen\>.tar|  
|Versie 5 x64|CCM-Universalx64. &lt;bouwen\>.tar|  
|Versie 6 x 86|CCM-Universalx86. &lt;bouwen\>.tar|  
|Versie 6 x64|CCM-Universalx64. &lt;bouwen\>.tar|  
|Versie 7 x86|CCM-Universalx86. &lt;bouwen\>.tar|  
|Versie 7 x64|CCM-Universalx64. &lt;bouwen\>.tar|  
|Versie 8 x86|CCM-Universalx86. &lt;bouwen\>.tar|  
|Versie 8 x64|CCM-Universalx64. &lt;bouwen\>.tar|  

### <a name="hp-ux"></a>HP-UX  

|Versie|Bestand|  
|-|-|  
|Versie 11iv2 IA64|CCM-HpuxB.11.23i64. &lt;bouwen\>.tar|  
|Versie 11iv2 PA-RISC|CCM-HpuxB.11.23PA. &lt;bouwen\>.tar|  
|Versie 11iv3 IA64|CCM-HpuxB.11.31i64. &lt;bouwen\>.tar|  
|Versie 11iv3 PA-RISC|CCM-HpuxB.11.31PA. &lt;bouwen\>.tar|  

### <a name="oracle-linux"></a>Oracle Linux  

|Versie|Bestand|    
|-|-|  
|Versie 5 x86|CCM-Universalx86. &lt;bouwen\>.tar|  
|Versie 5 x64|CCM-Universalx64. &lt;bouwen\>.tar|  
|Versie 6 x86|CCM-Universalx86. &lt;bouwen\>.tar|  
|Versie 6 x64|CCM-Universalx64. &lt;bouwen\>.tar|  
|Versie 7 x64|CCM-Universalx64. &lt;bouwen\>.tar|  

### <a name="red-hat-enterprise-linux-rhel"></a>Red Hat Enterprise Linux (RHEL)  

|Versie|Bestand|  
|-|-|  
|Versie 4 x86|CCM-RHEL4x86. &lt;bouwen\>.tar|  
|Versie 4 x64|CCM-RHEL4x64. &lt;bouwen\>.tar|  
|Versie 5 x86|CCM-Universalx86. &lt;bouwen\>.tar|  
|Versie 5 x64|CCM-Universalx64. &lt;bouwen\>.tar|  
|Versie 6 x86|CCM-Universalx86. &lt;bouwen\>.tar|  
|Versie 6 x64|CCM-Universalx64. &lt;bouwen\>.tar|  
|Versie 7 x64|CCM-Universalx64. &lt;bouwen\>.tar|  

### <a name="solaris"></a>Solaris  

|Versie|Bestand|   
|-|-|  
|Versie 9 SPARC|CCM-Sol9sparc. &lt;bouwen\>.tar|  
|Versie 10 x86|CCM-Sol10x86. &lt;bouwen\>.tar|  
|Versie 10 SPARC|CCM-Sol10sparc. &lt;bouwen\>.tar|  
|Versie 11 x86|CCM-Sol11x86. &lt;bouwen\>.tar|  
|Versie 11 SPARC|CCM-Sol11sparc. &lt;bouwen\>.tar|  

### <a name="suse-linux-enterprise-server-sles"></a>SUSE Linux Enterprise Server (SLES)  

|Versie|Bestand|  
|-|-|  
|Versie 9 x86|CCM-SLES9x86. &lt;bouwen\>.tar|  
|Versie 10 SP1 x86|CCM-Universalx86. &lt;bouwen\>.tar|  
|Versie 10 SP1 x64|CCM-Universalx64. &lt;bouwen\>.tar|  
|De SP1 versie 11 x86|CCM-Universalx86. &lt;bouwen\>.tar|  
|De SP1 versie 11 x64|CCM-Universalx64. &lt;bouwen\>.tar|  
|Versie 12 x64|CCM-Universalx64. &lt;bouwen\>.tar|  

### <a name="ubuntu"></a>Ubuntu  

|Versie|Bestand|    
|-|-|  
|Versie 10.04 TNS x86|CCM-Universalx86. &lt;bouwen\>.tar|  
|Versie 10.04 TNS x64|CCM-Universalx64. &lt;bouwen\>.tar|  
|Versie 12.04 TNS x86|CCM-Universalx86. &lt;bouwen\>.tar|  
|Versie 12.04 TNS x64|CCM-Universalx64. &lt;bouwen\>.tar|  
|Versie 14.04 TNS x86|CCM-Universalx86. &lt;bouwen\>.tar|  
|Versie 14.04 TNS x64|CCM-Universalx64. &lt;bouwen\>.tar|  

### <a name="exchange-server-connector"></a>Exchange Server-connector
 De LTSB ondersteunt beperkt beheer van apparaten die verbinding met uw Exchange Server-exemplaar maken zonder clientsoftware te installeren. Zie [Mobiele apparaten beheren met System Center Configuration Manager en Exchange](/sccm/mdm/deploy-use/manage-mobile-devices-with-exchange-activesync) voor meer informatie.

 **Vereisten en beperkingen:**  

-   Configuration Manager biedt beperkt beheer voor mobiele apparaten. Beperkt beheer is alleen beschikbaar wanneer u de Exchange Server-connector voor Exchange Active Sync (EAS) apparaten die verbinding maken met een server waarop Exchange Server of Exchange Online.  

-   Zie voor meer informatie over de beheerfuncties die door Configuration Manager biedt ondersteuning voor mobiele apparaten die Exchange Server-connector beheert, [kiezen een oplossing voor Apparaatbeheer voor System Center Configuration Manager](/sccm/core/plan-design/choose-a-device-management-solution).  

**Ondersteunde versies van Exchange-Server:**  
-   Exchange Server 2010 SP1  
-   Exchange Server 2010 SP2  
-   Exchange Server 2013  

> [!NOTE]
> De LTSB biedt geen ondersteuning voor het beheer van apparaten die verbinding via een online service, zoals Exchange Online (Office 365 maken).


## <a name="configuration-manager-console"></a>Configuration Manager-console
De LTSB ondersteunt de volgende besturingssystemen voor het uitvoeren van de Configuration Manager-console. Elke computer die als host fungeert voor de console moet minimaal .NET Framework-versie van 4.5.2, met uitzondering van Windows 10 waarvoor een minimum van .NET Framework 4.6 hebben.

**Ondersteunde besturingssystemen:**
- Windows Server 2016
- Windows Server 2012 R2 (x 64): Standard, Datacenter
- WindowsServer 2012 (x 64): Standard, Datacenter
- Windows Server 2008 R2 met SP1 (x 64): Standard, Enterprise, Datacenter
- WindowsServer 2008 SP2 (x 86, x 64): Standard, Enterprise, Datacenter
- Windows 10 Enterprise 2016 LTSB (x86, x64)
- Windows 10 Enterprise 2015 LTSB (x86, x64)
- Windows 8.1 (x86, x64): Professional, Enterprise
- Windows 7 met SP1 (x 86, x 64): Professional, Enterprise, Ultimate


## <a name="sql-server-versions-supported-for-the-site-database-and-reporting-point"></a>SQL Server-versies die worden ondersteund voor de sitedatabase en rapportagepunt
De LTSB ondersteunt de volgende versies van SQL Server als host voor de sitedatabase en de reporting-punt. Voor elke ondersteunde versie, de dezelfde configuratievereisten en beperkingen die worden weergegeven in [ondersteuning voor SQL Server-versies](/sccm/core/plan-design/configs/support-for-sql-server-versions) voor de huidige vertakking van toepassing op de LTSB.  Dit omvat het gebruik van een SQL Server-Cluster of een SQL Server AlwaysOn-beschikbaarheidsgroep.  

**Ondersteunde versies:**

- SQL Server 2016: Standard, Enterprise
- SQL Server 2014 SP2: Standard, Enterprise
- SQL Server 2014 SP1: Standard, Enterprise
- SQL Server 2012 SP3: Standard, Enterprise
- SQL Server 2008 R2 SP3: Standard, Enterprise, Datacenter
- SQL Server 2016 Express
- SQL Server 2014 snelle SP2
- SQL Server 2014 Express SP1
- SQL Server 2012 Express SP3

## <a name="support-for-active-directory-domains"></a>Ondersteuning voor Active Directory-domeinen
Alle LTSB sitesystemen moeten lid zijn van een ondersteunde Windows Active Directory-domein. Ondersteuning voor Active Directory-domeinen heeft dezelfde vereisten en beperkingen als die worden weergegeven in [ondersteuning voor Active Directory-domeinen](/sccm/core/plan-design/configs/support-for-active-directory-domains), maar is beperkt tot de volgende functionele domeinniveaus:

**Ondersteunde niveaus:**
- Windows Server 2008
- Windows Server 2008 R2
- Windows Server 2012
- Windows Server 2012 R2

## <a name="additional-support-topics-that-apply-to-the-long-term-servicing-branch"></a>Extra ondersteuning onderwerpen die betrekking hebben op de vertakking langetermijndoelen onderhoud
De informatie in de volgende onderwerpen in de huidige vertakking van toepassing op de LTSB:
- [Grootte en schaal getallen](/sccm/core/plan-design/configs/size-and-scale-numbers)
- [Site- en site-systeemvereisten](/sccm/core/plan-design/configs/site-and-site-system-prerequisites)
- [Opties voor hoge beschikbaarheid](/sccm/protect/understand/high-availability-options)
- [Aanbevolen hardware](/sccm/core/plan-design/configs/recommended-hardware)
- [Ondersteuning voor Windows-onderdelen en netwerken](/sccm/core/plan-design/configs/support-for-windows-features-and-networks)
- [Ondersteuning voor virtualisatieomgevingen](/sccm/core/plan-design/configs/support-for-virtualization-environments)

