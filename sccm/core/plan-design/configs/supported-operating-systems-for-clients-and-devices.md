---
title: Ondersteunde clients en apparaten
titleSuffix: Configuration Manager
description: Meer informatie over welke besturingssystemen voor System Center Configuration Manager voor clients en apparaten ondersteunt.
ms.custom: na
ms.date: 8/30/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 87f4e041-67df-4c61-aa98-7444faffe565
caps.latest.revision: "5"
author: mestew
ms.author: mstewart
manager: angrobe
ms.openlocfilehash: c740e9b23cb2968463e8843b5f3cdcbaba7c4d91
ms.sourcegitcommit: 645cd5a324bdd299906efa27eaca5885eafc9e9c
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 01/16/2018
---
# <a name="supported-operating-systems-for-clients-and-devices-for-system-center-configuration-manager"></a>Ondersteunde besturingssystemen voor clients en apparaten voor System Center Configuration Manager

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*


 System Center Configuration Manager ondersteunt de installatie van clientsoftware op tal van Windows, Mac, Linux en UNIX-computers.  

 **Vereisten en beperkingen voor alle clients:**  

-   Als u het opstarttype wijzigt of **aanmelden als** instellingen voor alle Configuration Manager-service wordt niet ondersteund en kan voorkomen dat belangrijke services correct uitgevoerd.    

-   Installeren of uitvoeren Configuration Manager-client voor Linux of UNIX of de client voor Mac op computers met een account met andere dan worden hoofdmap wordt niet ondersteund. In dat geval kunt belangrijke services niet correct uitgevoerd.  

##  <a name="windows-computers"></a>Windows-computers  
 U kunt de Configuration Manager-client die wordt geleverd met Configuration Manager voor het beheren van de volgende Windows-besturingssystemen. Zie voor meer informatie [clients implementeren op Windows-computers in System Center Configuration Manager](../../../core/clients/deploy/deploy-clients-to-windows-computers.md).  

**Ondersteunde besturingssystemen:**  


-  **Windows Server 2016**: Standard, Datacenter <sup>1</sup>
  - Dit besturingssysteem wordt ondersteund vanaf Configuration Manager versie 1606, met de rollup hotfix van KB3186654 (of de basislijnversie van 1606, die werd gepubliceerd in oktober 2016).  

-   **Windows Server 2012 R2** (x64): Standard, Datacenter <sup>1</sup>    

-   **Windows Storage Server 2012 R2** (x64)    

-   **Windows Server 2012** (x64): Standard, Datacenter <sup>1</sup>    

-   **Windows Storage Server 2012** (x64)    

-   **Windows Server 2008 R2 met SP1** (x64): Standard, Enterprise, Datacenter <sup>1</sup>    

-   **Windows Storage Server 2008 R2** (x86, x64): Workgroup, Standard, Enterprise    

-   **WindowsServer 2008 met SP2** (x86, x64): Standard, Enterprise, Datacenter <sup>1</sup>    

-   **Windows 10** Zie [ondersteuning voor versies van Windows 10](/sccm/core/plan-design/configs/support-for-windows-10) release voor meer informatie over de verschillende versies van Windows 10 die worden ondersteund door de verschillende versies van Configuration Manager.

-   **Windows 8.1** (x86, x64): Professional, Enterprise    

<!---   **Windows 8** (x86, x64): Professional, Enterprise  -removed Jan 12,2018 sms505863-->

-   **Windows 7 met SP1** (x86, x64): Professional, Enterprise en Ultimate    

-   **De Server Core-installatie van Windows Server 2016** (x64) <sup>2</sup>
  - Dit besturingssysteem wordt ondersteund vanaf versie 1606 met de rollup hotfix van KB3186654 (of de basislijnversie van 1606, die werd gepubliceerd in oktober 2016).


-   **De Server Core-installatie van Windows Server 2012 R2** (x64) <sup>2</sup>    

-   **De Server Core-installatie van Windows Server 2012** (x64) <sup>2</sup>    

-   **De Server Core-installatie van Windows Server 2008 R2**  
    **(zonder servicepack of met SP1)**  (x64)    

-   **De Server Core-installatie van Windows Server 2008 SP2** (x86, x64)  

 <sup>1</sup> Datacenter-releases worden ondersteund, maar niet gecertificeerd voor Configuration Manager. Hotfix-ondersteuning is niet beschikbaar voor problemen die specifiek voor Windows Server Datacenter Edition zijn.  

 <sup>2</sup> ter ondersteuning van push-clientinstallatie, de computer met deze besturingssysteemversie de functieservice File Server voor de serverfunctie bestands- en opslagservices moet worden uitgevoerd. Zie voor meer informatie over het installeren van Windows-onderdelen op een Server Core-computer [installeren van serverfuncties en onderdelen op een Server Core-Server](http://go.microsoft.com/fwlink/p/?LinkId=299359) in de Windows Server 2012 TechNet-bibliotheek.  


##  <a name="windows-embedded-computers"></a>Windows Embedded-computers  
 U kunt Windows Embedded-apparaten beheren met Configuration Manager-clientsoftware installeren op het apparaat.  Zie voor meer informatie [Planning voor clientimplementatie op Windows Embedded-apparaten in System Center Configuration Manager](../../../core/clients/deploy/plan/planning-for-client-deployment-to-windows-embedded-devices.md).  

**Vereisten en beperkingen:**  

-   Alle clientfuncties worden ondersteund op Windows Embedded-systemen waarvoor geen schrijffilters zijn ingeschakeld.  

-   Clients die gebruikmaken van een van de volgende worden ondersteund voor alle functies behalve energiebeheer:  

    -   Verbeterde schrijffilters (EWF)    

    -   RAM File Based Write Filters (FBWF)    

    -   Unified Write Filters (UWF)  

-   De Toepassingscatalogus wordt niet ondersteund voor Windows Embedded-apparaten.  

-   Voordat u gedetecteerde malware op Windows Embedded-apparaten die zijn gebaseerd op Windows XP controleren kunt, moet u het pakket van Microsoft Windows WMI-scripts installeren op het apparaat. Gebruik Windows Embedded Target Designer voor het installeren van dit pakket.
De bestanden **WBEMDISP. DLL-bestand** en **WBEMDISP. TLB** moet aanwezig zijn en zijn geregistreerd in de map **%windir%\System32\WBEM** op het ingesloten apparaat zodat gedetecteerde malware wordt gerapporteerd.  

**Ondersteunde besturingssystemen:**  

-   **Windows 10 Enterprise** (x86, x64)  

-   **Windows 10 IoT Enterprise** (x86, x64)  

-   **Windows Embedded 8.1 Industry** (x86, x64)    

   <!----   **Windows Embedded 8 Industry** (x86, x64)  -removed Jan 12,2018 sms505863-->

-   **Windows Embedded Standard 8** (x86, x64)    

<!---   **Windows Embedded 8 Pro** (x86, x64)    -removed Jan 12,2018 sms505863-->

-   **Windows Thin PC** (x86, x64)    

-   **Windows Embedded POSReady 7** (x86, x64)    

-   **Windows Embedded Standard 7 met SP1** (x86, x64)    

De volgende besturingssystemen zijn gebaseerd op Windows XP Embedded en wordt alleen ondersteund met Configuration Manager versie 1610 en eerdere versies. [Vanaf versie 1702, deze ingesloten besturingssystemen worden niet langer ondersteund](/sccm/core/plan-design/changes/removed-and-deprecated-features#client-operating-systems).  

-   **WEPOS 1.1 met SP3** (x86)    

-   **Windows Embedded POSReady 2009** (x86)    

-   **Windows Fundamentalss voor Legacy PCs (WinFLP)** (x86)    

-   **Ingesloten Windows XP SP3** (x86)    

-   **Windows Embedded Standard 2009** (x86)  

## <a name="windows-ce-computers"></a>Computers met Windows CE
 U kunt Windows CE-apparaten beheren met Configuration Manager verouderde clients van mobiele apparaten die wordt geleverd met Configuration Manager.  

**Vereisten en beperkingen**  

-   De client voor mobiele apparaten is 0,78 MB aan opslagruimte voor de installatie. Aanmelden met een kan tot 256 KB aan extra opslagruimte vereisen.    

-   Functies voor deze mobiele apparaten per platform en clienttype variëren type. Zie voor informatie over welke functies worden ondersteund, [een oplossing voor Apparaatbeheer kiezen voor System Center Configuration Manager](../../../core/plan-design/choose-a-device-management-solution.md).  

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

## <a name="mac-computers"></a>Mac-computers  
 U kunt Mac OS X-computers beheren met Configuration Manager-client voor Mac.  

 Het installatiepakket voor Mac-client wordt niet meegeleverd met de Configuration Manager-media. Download de **Clients voor aanvullende besturingssystemen** van de [Microsoft Download Center](http://go.microsoft.com/fwlink/?LinkID=525184).  

 Zie voor meer informatie [clients implementeren op Mac-computers in System Center Configuration Manager](../../../core/clients/deploy/deploy-clients-to-macs.md).  

**Ondersteunde versies:**  

-   **Mac OS X 10.6** (sneeuw Leopard)

-   **Mac OS X 10.7** (Lion)

-   **Mac OS X 10.8** (Mountain Lion)

-   **Mac OS X 10.9** (Mavericks)

-   **Mac OS X 10.10** (Yosemite)  

-   **Mac OS X 10.11** (El Capitan)  

-   **Mac OS X 10.12** (macOS Sierra)

##  <a name="linux-and-unix-servers"></a>Linux en UNIX-servers  
 U kunt Linux en UNIX-servers beheren met Configuration Manager-client voor Linux en UNIX.  

 De installatiepakketten voor Linux en UNIX-client worden niet meegeleverd met de Configuration Manager-media. Download de **Clients voor aanvullende besturingssystemen** van de [Microsoft Download Center](http://go.microsoft.com/fwlink/?LinkID=525184). Naast de clientinstallatiepakketten bevat de clientdownload het script dat de installatie van de client op elke computer wordt beheerd.  

**Vereisten en beperkingen:**  

-   Afhankelijkheden van besturingssysteembestanden voor de client voor Linux en UNIX Zie [vereisten voor de clientimplementatie op Linux en UNIX-Servers](../../../core/clients/deploy/plan/planning-for-client-deployment-to-linux-and-unix-computers.md#BKMK_ClientDeployPrereqforLnU).  

-   Zie voor een overzicht van ondersteunde beheermogelijkheden voor Linux of UNIX [clients implementeren op UNIX en Linux-servers in System Center Configuration Manager](../../../core/clients/deploy/deploy-clients-to-unix-and-linux-servers.md).  

-   Voor ondersteunde versies van Linux en UNIX bevat de vermelde versie alle daaropvolgende secundaire versies. CentOS-versie 6 bevat bijvoorbeeld CentOS 6.3. Op deze manier ondersteuning voor een besturingssysteem dat servicepacks gebruikt (zoals SUSE Linux Enterprise Server 11 SP1) daaropvolgende servicepacks voor die versie van het besturingssysteem bevat.  

-   Zie voor meer informatie over clientinstallatiepakketten en Universal Agent [clients implementeren op UNIX en Linux-servers in System Center Configuration Manager](../../../core/clients/deploy/deploy-clients-to-unix-and-linux-servers.md).  

**Ondersteunde versies:** De volgende versies worden ondersteund met behulp van het aangegeven .tar-bestand.  

### <a name="aix"></a>AIX  

|||  
|-|-|  
|Versie 6.1 (Power)|ccm-Aix61ppc.&lt;build\>.tar|  
|Versie 7.1 (Power)|ccm-Aix71ppc.&lt;build\>.tar|  

### <a name="centos"></a>CentOS  

|||  
|-|-|  
|Versie 5 x86|ccm-Universalx86.&lt;build\>.tar|  
|Versie 5 x64|ccm-Universalx64.&lt;build\>.tar|  
|Versie 6 x86|ccm-Universalx86.&lt;build\>.tar|  
|Versie 6 x64|ccm-Universalx64.&lt;build\>.tar|  
|Versie 7 x64|ccm-Universalx64.&lt;build\>.tar|  

### <a name="debian"></a>Debian  

|||  
|-|-|  
|Versie 5 x86|ccm-Universalx86.&lt;build\>.tar|  
|Versie 5 x64|ccm-Universalx64.&lt;build\>.tar|  
|Versie 6 x 86|ccm-Universalx86.&lt;build\>.tar|  
|Versie 6 x64|ccm-Universalx64.&lt;build\>.tar|  
|Versie 7 x86|ccm-Universalx86.&lt;build\>.tar|  
|Versie 7 x64|ccm-Universalx64.&lt;build\>.tar|  
|Versie 8 x86|ccm-Universalx86.&lt;build\>.tar|  
|Versie 8 x64|ccm-Universalx64.&lt;build\>.tar|  

### <a name="hp-ux"></a>HP-UX  

|||  
|-|-|  
|Versie 11iv3 IA64|ccm-HpuxB.11.31i64.&lt;build\>.tar|  

### <a name="oracle-linux"></a>Oracle Linux  

|||  
|-|-|  
|Versie 5 x86|ccm-Universalx86.&lt;build\>.tar|  
|Versie 5 x64|ccm-Universalx64.&lt;build\>.tar|  
|Versie 6 x86|ccm-Universalx86.&lt;build\>.tar|  
|Versie 6 x64|ccm-Universalx64.&lt;build\>.tar|  
|Versie 7 x64|ccm-Universalx64.&lt;build\>.tar|  

### <a name="red-hat-enterprise-linux-rhel"></a>Red Hat Enterprise Linux (RHEL)  

|||  
|-|-|  
|Versie 5 x86|ccm-Universalx86.&lt;build\>.tar|  
|Versie 5 x64|ccm-Universalx64.&lt;build\>.tar|  
|Versie 6 x86|ccm-Universalx86.&lt;build\>.tar|  
|Versie 6 x64|ccm-Universalx64.&lt;build\>.tar|  
|Versie 7 x64|ccm-Universalx64.&lt;build\>.tar|  

### <a name="solaris"></a>Solaris  

|||  
|-|-|  
|Versie 10 x86|ccm-Sol10x86.&lt;build\>.tar|  
|Versie 10 SPARC|ccm-Sol10sparc.&lt;build\>.tar|  
|Versie 11 x86|ccm-Sol11x86.&lt;build\>.tar|  
|Versie 11 SPARC|ccm-Sol11sparc.&lt;build\>.tar|  

### <a name="suse-linux-enterprise-server-sles"></a>SUSE Linux Enterprise Server (SLES)  

|||  
|-|-|  
|Versie 10 SP1 x86|ccm-Universalx86.&lt;build\>.tar|  
|Versie 10 SP1 x64|ccm-Universalx64.&lt;build\>.tar|  
|Versie 11 SP1 x86|ccm-Universalx86.&lt;build\>.tar|  
|Versie 11 SP1 x64|ccm-Universalx64.&lt;build\>.tar|  
|Versie 12 x64|ccm-Universalx64.&lt;build\>.tar|  

### <a name="ubuntu"></a>Ubuntu  

|||  
|-|-|  
|Versie 10.04 LTS x86|ccm-Universalx86.&lt;build\>.tar|  
|Versie 10.04 LTS x64|ccm-Universalx64.&lt;build\>.tar|  
|Versie 12.04 LTS x86|ccm-Universalx86.&lt;build\>.tar|  
|Versie 12.04 LTS x64|ccm-Universalx64.&lt;build\>.tar|  
|Versie 14.04 LTS x86|ccm-Universalx86.&lt;build\>.tar|  
|Versie 14.04 LTS x64|ccm-Universalx64.&lt;build\>.tar|  
|Versie 16.04 LTS x86|ccm-Universalx86.&lt;build\>.tar|  
|Versie 16.04 LTS x64|ccm-Universalx64.&lt;build\>.tar|  


##  <a name="mobile-devices-enrolled-by-microsoft-intune"></a>Mobiele apparaten die zijn geregistreerd door Microsoft Intune  
 Zie de volgende twee onderwerpen in de Microsoft Intune-Documentatiebibliotheek voor meer informatie over de computers en apparaten die u beheren kunt wanneer u Microsoft Intune met Configuration Manager integreert:  

-   [Beheermogelijkheden voor mobiele apparaten in Microsoft Intune](https://docs.microsoft.com/intune/get-started/choose-how-to-manage-devices)  
-   [Windows-PC-beheermogelijkheden in Microsoft Intune](https://docs.microsoft.com/intune/get-started/windows-pc-management-capabilities-in-microsoft-intune)  

##  <a name="bkmk_OnpremOS"></a>Lokaal beheer van mobiele apparaten  
 Configuration Manager beschikt over ingebouwde mogelijkheden voor het beheren van apparaten met on-premises zonder clientsoftware te installeren.  Zie voor meer informatie [mobiele apparaten beheren met on-premises infrastructuur in System Center Configuration Manager](../../../mdm/understand/manage-mobile-devices-with-on-premises-infrastructure.md).  

 **Vereisten en beperkingen:**  

-   U moet configureren de **Serviceaansluitpunt** op de bovenste site van uw hiërarchie.  

**Ondersteunde besturingssystemen:**  

- **Windows 10 Pro** (x86, x64)  

- **Windows 10 Pro Enterprise** (x86, x64)  

- **Windows 10 IoT Enterprise** (x86, x64)

- **Windows 10 Mobile**  

- **Windows 10 Mobile Enterprise**  

- **Windows 10 IoT Mobile Enterprise**

- **Windows 10 Team voor Surface Hub**

##  <a name="bkmk_ExSrvConOS"></a>Exchange Server-connector  
Configuration Manager ondersteunt beperkt beheer van apparaten die verbinding met uw Exchange-Server maken zonder de Configuration Manager-client installeert. Zie [Mobiele apparaten beheren met System Center Configuration Manager en Exchange](../../../mdm/deploy-use/manage-mobile-devices-with-exchange-activesync.md) voor meer informatie.  

 **Vereisten en beperkingen:**  

-   Configuration Manager biedt beperkt beheer voor mobiele apparaten wanneer u apparaten met Exchange Server-connector voor Exchange Active Sync die verbinding maken met een server waarop Exchange Server of Exchange Online.  

-   Zie voor meer informatie over welke beheerfuncties Configuration Manager ondersteunt voor mobiele apparaten die Exchange Server-connector beheert, bepalen hoe mobiele apparaten beheren in Configuration Manager.  

**Ondersteunde versies van Exchange-Server:**  

-   **Exchange Server 2010 SP1**  

-   **Exchange Server 2010 SP2**  

-   **Exchange Server 2013**  

-   **Exchange Online (Office 365)**: Dit bevat Business Productivity Online Standard Suite  
