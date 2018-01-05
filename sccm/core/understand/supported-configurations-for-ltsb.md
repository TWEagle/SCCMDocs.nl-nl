---
title: 'Ondersteunde configuraties voor de LTSB '
titleSuffix: Configuration Manager
description: Begrijpen wat besturingssystemen en afhankelijke producten met de Long-Term onderhoud vertakking van System Center Configuration Manager werken.
ms.custom: na
ms.date: 5/10/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: f0f818d4-7f45-402f-8758-dc88bc024953
caps.latest.revision: "0"
author: aczechowski
ms.author: aaroncz
manager: angrobe
ms.openlocfilehash: e634ade367375dd092cea0381fe976109c4936df
ms.sourcegitcommit: ca9d15dfb1c9eb47ee27ea9b5b39c9f8cdcc0748
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 01/04/2018
---
# <a name="supported-configurations-for-the-long-term-servicing-branch-of-system-center-configuration-manager"></a>Ondersteunde configuraties voor de lange termijn onderhoud vertakking van System Center Configuration Manager

*Van toepassing op: System Center Configuration Manager (op lange termijn onderhoud vertakking)*

Gebruik de informatie in dit onderwerp om te begrijpen welke besturingssystemen en het product afhankelijkheden worden ondersteund door de Long-Term Servicing Branch (LTSB) van Configuration Manager.
Als niet anders wordt vermeld in dit project of de LTSB onderwerpen worden dezelfde configuraties en beperkingen die betrekking hebben op de huidige vertakking versie 1606 toegepast op de LTSB.  Wanneer er conflicten optreden, gebruik de informatie die van toepassing op de editie die u gebruikt. De LTSB is doorgaans beperkter is dan de huidige vertakking.

## <a name="general-statement-of-support"></a>Algemeen overzicht van ondersteuning
De volgende producten en technologieën worden ondersteund door deze vertakking van Configuration Manager. Maar biedt ze zijn opgenomen in deze inhoud geen verlenging van ondersteuning voor een product of de versie van het product afzonderlijke ondersteuning levenscyclus. Producten waarvan de levenscyclus van de ondersteuning worden niet ondersteund voor gebruik met Configuration Manager. Voor meer informatie gaat u naar de [Microsoft Support Lifecycle](http://go.microsoft.com/fwlink/p/?LinkId=208270) website en lees de [Microsoft Support Lifecycle Policy FAQ](http://go.microsoft.com/fwlink/p/?LinkId=31976).

Bovendien producten en versies die niet worden weergegeven in de volgende onderwerpen worden niet ondersteund tenzij deze is vermeld in de [Enterprise Mobility + Security-Blog](https://blogs.technet.microsoft.com/enterprisemobility/).

**Beperkingen voor toekomstige ondersteuning:** De LTSB beperkte ondersteuning voor de nieuwe server en client-besturingssystemen en product afhankelijkheden. De lijst met platforms voor het LTSB wordt vastgesteld voor de duur van de release:

**Windows:**
- Alleen kwaliteit en beveiliging updates voor Windows worden ondersteund.
- Er wordt geen ondersteuning voor huidige vertakkingen (CB), huidige vertakkingen van business (CBB) of Windows 10 LTSB toegevoegd.
-   Er is geen ondersteuning voor nieuwe primaire versies van Windows Server.

**SQL Server:**
- Alleen kwaliteit en beveiligingsupdates of kleine upgrades zoals servicepacks, wordt ondersteund voor SQL Server.
- Er is geen ondersteuning voor nieuwe primaire versies van SQL Server.  

## <a name="site-systems-and-servers"></a>Sitesystemen en -servers
De LTSB ondersteunt het gebruik van de volgende besturingssystemen van de Windows-computer als site-systemen.  Elk besturingssysteem heeft de dezelfde vereisten en beperkingen als hetzelfde beginpunt in [ondersteunde besturingssystemen voor sitesysteemservers](/sccm/core/plan-design/configs/supported-operating-systems-for-site-system-servers).  De Server Core-installatie van Windows 2012 R2 moet bijvoorbeeld een x64 versie, wordt alleen ondersteund voor het hosten van een distributiepunt en biedt geen ondersteuning voor PXE of Multicast.

**Ondersteunde besturingssystemen:**
- Windows Server 2016
- Windows Server 2012 R2 (x 64): Standard, Datacenter
- WindowsServer 2012 (x 64): Standard, Datacenter
- Windows Server 2008 R2 met SP1 (x 64): Standard, Enterprise, Datacenter
- WindowsServer 2008 met SP2 (x 86, x 64): Standard, Enterprise, Datacenter *(Zie Opmerking 1)*
- Windows 10 Enterprise 2015 LTSB (x86, x64)
- Windows 10 Enterprise 2016 LTSB (x86, x64)
- Windows 8.1 (x86, x64): Professional, Enterprise
- Windows 7 met SP1 (x 86, x 64): Professional, Enterprise, Ultimate
- De Server Core-installatie van Windows Server 2012
- De Server Core-installatie van Windows Server 2012 R2    

*Opmerking 1*: Dit besturingssysteem wordt niet ondersteund voor siteservers of sitesysteemrollen met uitzondering van het distributiepunt en pull-distributiepunt. U kunt blijven gebruiken van dit besturingssysteem als een distributiepunt totdat afschaffing van deze ondersteuning wordt aangekondigd of de periode voor uitgebreide ondersteuning van dit besturingssysteem is verstreken. Zie voor meer informatie [installatie van System Center Configuration Manager CB en LTSB mislukt op Windows Server 2008](https://support.microsoft.com/help/4015095).

## <a name="client-management"></a>Clientbeheer
De volgende secties beschrijven de client-besturingssystemen die u met de LTSB kunt beheren. De LTSB biedt geen ondersteuning voor het toevoegen van nieuwe besturingssystemen als ondersteunde clients.

### <a name="windows-computers"></a>Windows-computers
U kunt de LTSB gebruiken voor het beheren van de volgende Windows-besturingssystemen met de Configuration Manager-clientsoftware die is opgenomen met Configuration Manager. Zie voor meer informatie [clients implementeren op Windows-computers in System Center Configuration Manager](/sccm/core/clients/deploy/deploy-clients-to-windows-computers).

**Ondersteunde besturingssystemen:**
- Windows Server 2016
- Windows Server 2012 R2 (x 64): Standard, Datacenter (Opmerking 1)
- WindowsServer 2012 (x 64): Standard, Datacenter (Opmerking 1)
- Windows Storage Server 2012 R2 (x 64)
- Windows Storage Server 2012 (x 64)
- Windows Server 2008 R2 met SP1 (x 64): Standard, Enterprise, Datacenter (Opmerking 1)
- Windows Storage Server 2008 R2 (x 86, x 64): Workgroup, Standard, Enterprise
- WindowsServer 2008 met SP2 (x 86, x 64): Standard, Enterprise, Datacenter (Opmerking 1)
- Windows 10 Enterprise 2015 LTSB (x86, x64)
- Windows 10 Enterprise 2016 LTSB (x86, x64)
- Windows 8.1 (x86, x64): Professional, Enterprise
- Windows 7 met SP1 (x 86, x 64): Professional, Enterprise, Ultimate
- De Server Core-installatie van Windows Server 2012 R2 (x64) (Opmerking 2)
- De Server Core-installatie van Windows Server 2012 (x64) (Opmerking 2)
- De Server Core-installatie van Windows Server 2008 R2 SP1 (x64)
- De Server Core-installatie van Windows Server 2008 SP2 (x86, x64)

**(Opmerking 1)**  Datacenter-releases worden ondersteund, maar niet gecertificeerd voor Configuration Manager.  
**(Zie Opmerking 2)**  Ter ondersteuning van push-clientinstallatie, de computer met deze besturingssysteemversie de functieservice File Server voor de serverfunctie bestands- en opslagservices moet worden uitgevoerd. Zie voor meer informatie over het installeren van Windows-onderdelen op een Server Core-computer [installeren van serverfuncties en onderdelen op een Server Core-Server](https://technet.microsoft.com/library/jj574158(v=ws.11).aspx) in de Windows Server 2012 TechNet-bibliotheek.

### <a name="windows-embedded"></a>Windows Embedded
U kunt de LTSB gebruiken voor het beheren van de volgende Windows Embedded-apparaten door de clientsoftware installeren op het apparaat.  Zie voor meer informatie [Planning voor clientimplementatie op Windows Embedded-apparaten in System Center Configuration Manager](/sccm/core/clients/deploy/plan/planning-for-client-deployment-to-windows-embedded-devices).

**Vereisten en beperkingen:**  

-   Alle clientfuncties worden ondersteund op ondersteunde Windows Embedded-systemen waarvoor geen schrijffilters zijn ingeschakeld.  

-   Clients die gebruikmaken van een van de volgende worden ondersteund voor alle functies behalve energiebeheer:  

    -   Verbeterde schrijffilters (EWF)    

    -   RAM File Based Write Filters (FBWF)    

    -   Unified Write Filters (UWF)  

-   De Toepassingscatalogus wordt niet ondersteund voor Windows Embedded-apparaten.  

-   Voordat u gedetecteerde malware op Windows Embedded-apparaten op basis van Windows XP controleren kunt, moet u het pakket van Microsoft Windows WMI-scripts installeren op het ingesloten apparaat. Gebruik Windows Embedded Target Designer voor het installeren van dit pakket. De *WBEMDISP. DLL-bestand* en *WBEMDISP. TLB* bestanden moet aanwezig zijn en zijn geregistreerd in de map %windir%\System32\WBEM op het ingesloten apparaat zodat gedetecteerde malware wordt gerapporteerd.  

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
 U kunt Windows CE-apparaten beheren met Configuration Manager verouderde clients van mobiele apparaten die wordt geleverd met Configuration Manager.  

**Vereisten en beperkingen:**  

-   De client voor mobiele apparaten is 0,78 MB aan opslagruimte voor het installeren van de client. Een mobiel apparaat kunt vereisen tot 256 KB aan extra opslagruimte aan te melden.    

-   Functies voor deze mobiele apparaten per platform en clienttype variëren type. Zie voor meer informatie over de aard van de beheerfuncties die ondersteuning biedt voor een verouderde client voor mobiele apparaten voor Configuration Manager [een oplossing voor Apparaatbeheer kiezen voor System Center Configuration Manager](/sccm/core/plan-design/choose-a-device-management-solution).  

**Ondersteunde besturingssystemen:**  

-   Windows CE 7.0 (ARM- en x86 processors)  

**Ondersteunde talen zijn onder andere:**  
-   Chinees (vereenvoudigd en Traditioneel)    
-   Engels (VS)    
-   Frans (Frankrijk)    
-   German    
-   Italian    
-   Japans  
-   Korean  
-   Portugees (Brazilië)  
-   Russisch  
-   Spaans (Spanje)  

### <a name="mac-computers"></a>Mac-computers  
 U kunt de LTSB Mac OS X-computers beheren met Configuration Manager-client voor Mac.

Het installatiepakket voor Mac-client wordt niet meegeleverd met de Configuration Manager-media. U kunt downloaden als onderdeel van de download ' Clients voor aanvullende besturingssystemen ' van de [Microsoft Download Center](http://go.microsoft.com/fwlink/?LinkID=525184).  

Ondersteuning voor Mac-besturingssystemen is beperkt tot die zijn opgenomen in deze sectie. Ondersteuning is niet opgenomen voor aanvullende besturingssystemen die kan worden ondersteund door een toekomstige update Mac clientinstallatiepakketten voor de huidige vertakking.

Zie voor meer informatie [clients implementeren op Mac-computers in System Center Configuration Manager](/sccm/core/clients/deploy/deploy-clients-to-macs).

**Ondersteunde versies:**  
-   Mac OS X 10.9 (Mavericks)  
-   Mac OS X 10.10 (Yosemite)  
-   Mac OS X 10.11 (El Capitan)  

## <a name="linux-and-unix-servers"></a>Linux en UNIX-servers
U kunt de LTSB Linux en UNIX-servers beheren met Configuration Manager-client voor Linux en UNIX.

De installatiepakketten voor Linux en UNIX-client worden niet meegeleverd met de Configuration Manager-media. U kunt downloaden als onderdeel van de download ' Clients voor aanvullende besturingssystemen ' van de [Microsoft Download Center](http://go.microsoft.com/fwlink/?LinkID=525184). Naast de clientinstallatiepakketten bevat de clientdownload het installatiescript waarmee de installatie van de client op elke computer wordt beheerd.

Ondersteuning voor Linux en UNIX-besturingssystemen is beperkt tot die zijn opgenomen in deze sectie. Ondersteuning is niet opgenomen voor aanvullende besturingssystemen die mogelijk worden ondersteund door een toekomstige update pakketten voor Linux en UNIX-client voor de huidige vertakking.

**Vereisten en beperkingen:**  

-   Afhankelijkheden van besturingssysteembestanden voor de client voor Linux en UNIX Zie [vereisten voor de clientimplementatie op Linux en UNIX-Servers](/sccm/core/clients/deploy/plan/planning-for-client-deployment-to-linux-and-unix-computers#bkmk_clientdeployprereqforlnu).  
-   Zie voor een overzicht van de beheermogelijkheden die wordt ondersteund voor computers waarop Linux of UNIX [clients implementeren op UNIX en Linux-servers in System Center Configuration Manager](/sccm/core/clients/deploy/deploy-clients-to-unix-and-linux-servers).  
-   Voor ondersteunde versies van Linux en UNIX bevat de vermelde versie alle daaropvolgende secundaire versies. Bijvoorbeeld, indien ondersteuning voor CentOS-versie 6 is aangegeven, bevat dit ook de daaropvolgende secundaire versies van CentOS 6, zoals CentOS 6.3. Op dezelfde manier als ondersteuning wordt vermeld voor een besturingssysteem dat gebruikmaakt van servicepacks, zoals SUSE Linux Enterprise Server 11 SP1 omvat ondersteuning de daaropvolgende servicepacks voor dat besturingssysteem.
-   Zie voor meer informatie over clientinstallatiepakketten en Universal Agent [clients implementeren op UNIX en Linux-servers in System Center Configuration Manager](/sccm/core/clients/deploy/deploy-clients-to-unix-and-linux-servers).


**Ondersteunde versies:**   
De volgende versies worden ondersteund met behulp van het aangegeven .tar-bestand.  
### <a name="aix"></a>AIX  

|Versie|Bestand|  
|-|-|  
|Versie 5.3 (Power)|CCM-Aix53ppc. &lt;bouwen\>tar|  
|Versie 6.1 (Power)|CCM-Aix61ppc. &lt;bouwen\>tar|  
|Versie 7.1 (Power)|CCM-Aix71ppc. &lt;bouwen\>tar|  

### <a name="centos"></a>CentOS  

|Versie|Bestand|  
|-|-|  
|Versie 5 x86|CCM-Universalx86. &lt;bouwen\>tar|  
|Versie 5 x64|CCM-Universalx64. &lt;bouwen\>tar|  
|Versie 6 x86|CCM-Universalx86. &lt;bouwen\>tar|  
|Versie 6 x64|CCM-Universalx64. &lt;bouwen\>tar|  
|Versie 7 x64|CCM-Universalx64. &lt;bouwen\>tar|  

### <a name="debian"></a>Debian  

|Versie|Bestand|    
|-|-|  
|Versie 5 x86|CCM-Universalx86. &lt;bouwen\>tar|  
|Versie 5 x64|CCM-Universalx64. &lt;bouwen\>tar|  
|Versie 6 x 86|CCM-Universalx86. &lt;bouwen\>tar|  
|Versie 6 x64|CCM-Universalx64. &lt;bouwen\>tar|  
|Versie 7 x86|CCM-Universalx86. &lt;bouwen\>tar|  
|Versie 7 x64|CCM-Universalx64. &lt;bouwen\>tar|  
|Versie 8 x86|CCM-Universalx86. &lt;bouwen\>tar|  
|Versie 8 x64|CCM-Universalx64. &lt;bouwen\>tar|  

### <a name="hp-ux"></a>HP-UX  

|Versie|Bestand|  
|-|-|  
|Versie 11iv2 IA64|CCM-HpuxB.11.23i64. &lt;bouwen\>tar|  
|Versie 11iv2 PA-RISC|CCM-HpuxB.11.23PA. &lt;bouwen\>tar|  
|Versie 11iv3 IA64|CCM-HpuxB.11.31i64. &lt;bouwen\>tar|  
|Versie 11iv3 PA-RISC|CCM-HpuxB.11.31PA. &lt;bouwen\>tar|  

### <a name="oracle-linux"></a>Oracle Linux  

|Versie|Bestand|    
|-|-|  
|Versie 5 x86|CCM-Universalx86. &lt;bouwen\>tar|  
|Versie 5 x64|CCM-Universalx64. &lt;bouwen\>tar|  
|Versie 6 x86|CCM-Universalx86. &lt;bouwen\>tar|  
|Versie 6 x64|CCM-Universalx64. &lt;bouwen\>tar|  
|Versie 7 x64|CCM-Universalx64. &lt;bouwen\>tar|  

### <a name="red-hat-enterprise-linux-rhel"></a>Red Hat Enterprise Linux (RHEL)  

|Versie|Bestand|  
|-|-|  
|Versie 4 x86|CCM-RHEL4x86. &lt;bouwen\>tar|  
|Versie 4 x64|CCM-RHEL4x64. &lt;bouwen\>tar|  
|Versie 5 x86|CCM-Universalx86. &lt;bouwen\>tar|  
|Versie 5 x64|CCM-Universalx64. &lt;bouwen\>tar|  
|Versie 6 x86|CCM-Universalx86. &lt;bouwen\>tar|  
|Versie 6 x64|CCM-Universalx64. &lt;bouwen\>tar|  
|Versie 7 x64|CCM-Universalx64. &lt;bouwen\>tar|  

### <a name="solaris"></a>Solaris  

|Versie|Bestand|   
|-|-|  
|Versie 9 SPARC|CCM-Sol9sparc. &lt;bouwen\>tar|  
|Versie 10 x86|CCM-Sol10x86. &lt;bouwen\>tar|  
|Versie 10 SPARC|CCM-Sol10sparc. &lt;bouwen\>tar|  
|Versie 11 x86|CCM-Sol11x86. &lt;bouwen\>tar|  
|Versie 11 SPARC|CCM-Sol11sparc. &lt;bouwen\>tar|  

### <a name="suse-linux-enterprise-server-sles"></a>SUSE Linux Enterprise Server (SLES)  

|Versie|Bestand|  
|-|-|  
|Versie 9 x86|CCM-SLES9x86. &lt;bouwen\>tar|  
|Versie 10 SP1 x86|CCM-Universalx86. &lt;bouwen\>tar|  
|Versie 10 SP1 x64|CCM-Universalx64. &lt;bouwen\>tar|  
|Versie 11 SP1 x86|CCM-Universalx86. &lt;bouwen\>tar|  
|Versie 11 SP1 x64|CCM-Universalx64. &lt;bouwen\>tar|  
|Versie 12 x64|CCM-Universalx64. &lt;bouwen\>tar|  

### <a name="ubuntu"></a>Ubuntu  

|Versie|Bestand|    
|-|-|  
|Versie 10.04 LTS x86|CCM-Universalx86. &lt;bouwen\>tar|  
|Versie 10.04 LTS x64|CCM-Universalx64. &lt;bouwen\>tar|  
|Versie 12.04 LTS x86|CCM-Universalx86. &lt;bouwen\>tar|  
|Versie 12.04 LTS x64|CCM-Universalx64. &lt;bouwen\>tar|  
|Versie 14.04 LTS x86|CCM-Universalx86. &lt;bouwen\>tar|  
|Versie 14.04 LTS x64|CCM-Universalx64. &lt;bouwen\>tar|  

### <a name="exchange-server-connector"></a>Exchange Server-connector
 De LTSB ondersteunt beperkt beheer van apparaten die verbinding met uw Exchange Server-exemplaar, maken zonder clientsoftware te installeren. Zie [Mobiele apparaten beheren met System Center Configuration Manager en Exchange](/sccm/mdm/deploy-use/manage-mobile-devices-with-exchange-activesync) voor meer informatie.

 **Vereisten en beperkingen:**  

-   Configuration Manager biedt beperkt beheer voor mobiele apparaten. Beperkt beheer is beschikbaar wanneer u de Exchange Server-connector voor Exchange Active Sync (EAS) om apparaten die verbinding maken met een server met Exchange Server of Exchange Online.  

-   Zie voor meer informatie over de beheerfuncties die Configuration Manager ondersteunt voor mobiele apparaten die Exchange Server-connector beheert, [een oplossing voor Apparaatbeheer kiezen voor System Center Configuration Manager](/sccm/core/plan-design/choose-a-device-management-solution).  

**Ondersteunde versies van Exchange-Server:**  
-   Exchange Server 2010 SP1  
-   Exchange Server 2010 SP2  
-   Exchange Server 2013  

> [!NOTE]
> De LTSB biedt geen ondersteuning voor het beheer van apparaten die verbinding via een online service, zoals Exchange Online (Office 365 maken).


## <a name="configuration-manager-console"></a>Configuration Manager-console
De LTSB ondersteunt de volgende besturingssystemen om uit te voeren van de Configuration Manager-console. Elke computer die als host fungeert voor de console moet minimaal .NET Framework versie 4.5.2, met uitzondering van Windows 10, waarvoor minimaal .NET Framework 4.6 vereist hebben.

**Ondersteunde besturingssystemen:**
- Windows Server 2016
- Windows Server 2012 R2 (x 64): Standard, Datacenter
- WindowsServer 2012 (x 64): Standard, Datacenter
- Windows Server 2008 R2 met SP1 (x 64): Standard, Enterprise, Datacenter
- WindowsServer 2008 met SP2 (x 86, x 64): Standard, Enterprise, Datacenter
- Windows 10 Enterprise 2016 LTSB (x86, x64)
- Windows 10 Enterprise 2015 LTSB (x86, x64)
- Windows 8.1 (x86, x64): Professional, Enterprise
- Windows 7 met SP1 (x 86, x 64): Professional, Enterprise, Ultimate


## <a name="sql-server-versions-supported-for-the-site-database-and-reporting-point"></a>SQL Server-versies ondersteund voor de sitedatabase en de reporting-punt
De LTSB ondersteunt de volgende versies van SQL Server als host voor de sitedatabase en het rapportagepunt. Voor elke ondersteunde versie, de dezelfde configuratievereisten en beperkingen die worden weergegeven in [ondersteuning voor SQL Server-versies](/sccm/core/plan-design/configs/support-for-sql-server-versions) voor de huidige vertakking van toepassing op de LTSB.  Dit omvat het gebruik van een SQL Server-Cluster of een SQL Server AlwaysOn-beschikbaarheidsgroep.  

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
Alle LTSB-sitesystemen moeten lid zijn van een ondersteund Windows Active Directory-domein. Ondersteuning voor Active Directory-domeinen heeft dezelfde vereisten en beperkingen als die worden weergegeven in [ondersteuning voor Active Directory-domeinen](/sccm/core/plan-design/configs/support-for-active-directory-domains), maar is beperkt tot de volgende functionaliteitsniveaus:

**Ondersteunde niveaus:**
- Windows Server 2008
- Windows Server 2008 R2
- Windows Server 2012
- Windows Server 2012 R2

## <a name="additional-support-topics-that-apply-to-the-long-term-servicing-branch"></a>Aanvullende ondersteuning onderwerpen die betrekking hebben op de vertakking Long-Term onderhoud
De informatie in de volgende onderwerpen in de huidige vertakking van toepassing op de LTSB:
- [Grootte en schaalgetallen](/sccm/core/plan-design/configs/size-and-scale-numbers)
- [Vereisten voor sites en sitesystemen](/sccm/core/plan-design/configs/site-and-site-system-prerequisites)
- [Opties voor hoge beschikbaarheid](/sccm/protect/understand/high-availability-options)
- [Aanbevolen hardware](/sccm/core/plan-design/configs/recommended-hardware)
- [Ondersteuning voor Windows-onderdelen en -netwerken](/sccm/core/plan-design/configs/support-for-windows-features-and-networks)
- [Ondersteuning voor virtualisatieomgevingen](/sccm/core/plan-design/configs/support-for-virtualization-environments)
