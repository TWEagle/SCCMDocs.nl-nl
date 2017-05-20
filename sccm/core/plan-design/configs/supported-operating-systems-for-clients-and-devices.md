---
title: Ondersteunde clients en apparaten | Microsoft-documenten
description: Informatie over welke besturingssystemen System Center Configuration Manager voor clients en apparaten ondersteunt.
ms.custom: na
ms.date: 2/6/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 87f4e041-67df-4c61-aa98-7444faffe565
caps.latest.revision: 5
author: arob98
ms.author: angrobe
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: d5166b16ffbe46af561b1ce98c0494cc4aaa72a8
ms.openlocfilehash: cd7b8bf35aeb26c8b7b37f6faa51c9a09138fdb9
ms.contentlocale: nl-nl
ms.lasthandoff: 05/17/2017

---
# <a name="supported-operating-systems-for-clients-and-devices-for-system-center-configuration-manager"></a>Ondersteunde besturingssystemen voor clients en apparaten voor System Center Configuration Manager

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*


 System Center Configuration Manager ondersteunt de clientsoftware op tal van Windows, Mac, Linux en UNIX-computers installeren.  

 **Vereisten en beperkingen voor alle clients:**  

-   Als het opstarttype wijzigt of **aanmelden als** instellingen voor alle Configuration Manager-service wordt niet ondersteund en is het mogelijk dat belangrijke services niet correct worden uitgevoerd.    

-   Installeren of uitvoeren van de Configuration Manager-client voor Linux of UNIX- of de client voor Mac op computers met een account met andere dan worden hoofdmap wordt niet ondersteund. In dat geval kunt voorkomen dat belangrijke services juist worden uitgevoerd.  

##  <a name="windows-computers"></a>Windows-computers  
 U kunt de Configuration Manager-client die wordt geleverd met Configuration Manager voor het beheren van de volgende Windows-besturingssystemen. Zie voor meer informatie [het implementeren van clients op Windows-computers in System Center Configuration Manager](../../../core/clients/deploy/deploy-clients-to-windows-computers.md).  

**Ondersteunde besturingssystemen:**  


-  **WindowsServer 2016**: Standard, Datacenter <sup>1</sup>
  - Dit besturingssysteem wordt ondersteund vanaf Configuration Manager versie 1606 met de hotfix rollup van KB3186654 (of de basislijn-versie van 1606, dat is gepubliceerd in oktober 2016).  

-   **Windows Server 2012 R2** (x64): Standard, Datacenter <sup>1</sup>    

-   **Windows Storage Server 2012 R2** (x64)    

-   **WindowsServer 2012** (x64): Standard, Datacenter <sup>1</sup>    

-   **Windows Storage Server 2012** (x64)    

-   **Windows Server 2008 R2 met SP1** (x64): Standard, Enterprise, Datacenter <sup>1</sup>    

-   **Windows Storage Server 2008 R2** (x86, x64): Workgroup, Standard, Enterprise    

-   **WindowsServer 2008 SP2** (x86, x64): Standard, Enterprise, Datacenter <sup>1</sup>    

-   **Windows 10**: Pro, Enterprise  
   Zie [ondersteuning voor versies van Windows 10](/sccm/core/plan-design/configs/support-for-windows-10) release voor meer informatie over de verschillende versies van Windows 10 die worden ondersteund door de verschillende versies van Configuration Manager.

-   **Windows 8.1** (x86, x64): Professional, Enterprise    

-   **Windows 8** (x86, x64): Professional, Enterprise    

-   **Windows 7 met SP1** (x86, x64): Professional, Enterprise en Ultimate    

-   **De Server Core-installatie van Windows Server 2016** (x64) <sup>2</sup>
  - Dit besturingssysteem wordt ondersteund vanaf versie 1606 met de hotfix rollup van KB3186654 (of de basislijn-versie van 1606, dat is gepubliceerd in oktober van 2016). 


-   **De Server Core-installatie van Windows Server 2012 R2** (x64) <sup>2</sup>    

-   **De Server Core-installatie van Windows Server 2012** (x64) <sup>2</sup>    

-   **De Server Core-installatie van Windows Server 2008 R2**  
    **(zonder servicepack of met SP1)**  (x64)    

-   **De Server Core-installatie van Windows Server 2008 SP2** (x86, x64)  

 <sup>1</sup> Datacenter-versies worden ondersteund, maar niet gecertificeerd voor Configuration Manager. Hotfix-ondersteuning is niet beschikbaar voor problemen die specifiek voor Windows Server Datacenter Edition zijn.  

 <sup>2</sup> ter ondersteuning van push-clientinstallatie, moet de computer die deze versie van het besturingssysteem wordt uitgevoerd de functieservice bestandsserver voor de serverrol bestands- en opslagservices uitgevoerd. Zie voor meer informatie over het installeren van Windows-onderdelen op een Server Core-computer [installeren serverrollen en functies op een Server Core-Server](http://go.microsoft.com/fwlink/p/?LinkId=299359) in de Windows Server 2012 TechNet library.  


##  <a name="windows-embedded-computers"></a>Windows Embedded-computers  
 U kunt Windows Embedded-apparaten beheren met Configuration Manager-clientsoftware installeren op het apparaat.  Zie voor meer informatie [Planning voor clientimplementatie op Windows Embedded-apparaten in System Center Configuration Manager](../../../core/clients/deploy/plan/planning-for-client-deployment-to-windows-embedded-devices.md).  

**Vereisten en beperkingen:**  

-   Alle clientfuncties worden ondersteund op Windows Embedded systemen waarop geen schrijffilters zijn ingeschakeld.  

-   Clients die gebruikmaken van een van de volgende worden ondersteund voor alle functies, met uitzondering van energiebeheer:  

    -   Verbeterde schrijffilters (EWF)    

    -   RAM-geheugen bestand gebaseerde schrijffilters (FBWF)    

    -   Unified Write Filters (UWF)  

-   De Toepassingscatalogus wordt niet ondersteund voor Windows Embedded-apparaat.  

-   Voordat u de gedetecteerde malware op Windows Embedded-apparaten die zijn gebaseerd op Windows XP bewaken kunt, moet u het pakket van Microsoft Windows WMI-scripting installeren op het apparaat. Windows Embedded doel Designer gebruiken voor dit pakket installeert.
De bestanden **WBEMDISP. DLL** en **WBEMDISP. TLB** zijn en deze moet worden geregistreerd in de map **%windir%\System32\WBEM** op het embedded-apparaat om ervoor te zorgen gedetecteerde schadelijke software wordt gerapporteerd.  

**Ondersteunde besturingssystemen:**  

-   **Windows 10 Enterprise** (x86, x64)  

-   **Windows 10 IoT Enterprise** (x86, x64)  

-   **Windows Embedded 8.1 Industry** (x86, x64)    

-   **Windows Embedded 8 Industry** (x86, x64)    

-   **Windows Embedded 8 Standard** (x86, x64)    

-   **Windows Embedded 8 Pro** (x86, x64)    

-   **Windows dun PC** (x86, x64)    

-   **Windows Embedded POSReady 7** (x86, x64)    

-   **Windows Embedded Standard 7 met SP1** (x86, x64)    

-   **WEPOS 1.1 met SP3** (x86)    

-   **Windows Embedded POSReady 2009** (x86)    

-   **Windows grondbeginselen voor Legacy PCs (WinFLP)** (x86)    

-   **Windows XP SP3 ingesloten** (x86)    

-   **Windows Embedded Standard 2009** (x86)  

## <a name="windows-ce-computers"></a>Computers met Windows CE
 U kunt Windows CE-apparaten beheren met Configuration Manager verouderde clients van mobiele apparaten die zijn opgenomen met Configuration Manager.  

**Vereisten en beperkingen**  

-   De client voor mobiele apparaten is 0.78 MB aan opslagruimte vereist voor installatie. Aanmelden, kan maximaal 256 KB extra opslagruimte vereisen.    

-   Functies voor deze mobiele apparaten per platform en client variëren type. Zie voor meer informatie over het beheer van welke functies worden ondersteund, [kiezen een oplossing voor Apparaatbeheer voor System Center Configuration Manager](../../../core/plan-design/choose-a-device-management-solution.md).  

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

## <a name="mac-computers"></a>Mac-computers  
 U kunt Mac OS X-computers beheren met Configuration Manager-client voor Mac.  

 Het installatiepakket voor Mac-client wordt niet meegeleverd met de Configuration Manager-media. Download de **Clients voor andere besturingssystemen** van de [Microsoft Download Center](http://go.microsoft.com/fwlink/?LinkID=525184).  

 Zie voor meer informatie [clients implementeren in Macs in System Center Configuration Manager](../../../core/clients/deploy/deploy-clients-to-macs.md).  

**Ondersteunde versies:**  

-   **Mac OS X 10,6** (sneeuw Leopard)

-   **Mac OS X 10.7** (Lion)

-   **Mac OS X 10,8** (Mountain Lion)

-   **Mac OS X 10.9** (Mavericks)

-   **Mac OS X 10.10** (Yosemite)  

-   **Mac OS X 10.11** (El Capitan)  

-   **Mac OS X 10,12** (Mac OS Sierra)

##  <a name="linux-and-unix-servers"></a>Linux en UNIX-servers  
 U kunt Linux en UNIX-servers beheren met Configuration Manager-client voor Linux en UNIX.  

 De pakketten zijn Linux en UNIX-client-installatie worden niet geleverd met de Configuration Manager-media. Download de **Clients voor andere besturingssystemen** van de [Microsoft Download Center](http://go.microsoft.com/fwlink/?LinkID=525184). Naast het clientinstallatiepakketten bevat het downloaden van de client het script dat de installatie van de client op iedere computer beheert.  

**Vereisten en beperkingen:**  

-   Afhankelijkheden van pakketbestanden besturingssysteem voor de client voor Linux en UNIX, Zie [vereisten voor clientimplementatie op Linux en UNIX-Servers](../../../core/clients/deploy/plan/planning-for-client-deployment-to-linux-and-unix-computers.md#BKMK_ClientDeployPrereqforLnU).  

-   Zie voor een overzicht van ondersteunde beheerfuncties voor Linux of UNIX [clients implementeren voor UNIX en Linux-servers in System Center Configuration Manager](../../../core/clients/deploy/deploy-clients-to-unix-and-linux-servers.md).  

-   Voor ondersteunde versies van Linux en UNIX bevat de vermelde versie alle volgende secundaire versies. CentOS versie 6 bevat bijvoorbeeld CentOS 6.3. Op deze manier ondersteuning voor een besturingssysteem dat servicepacks gebruikt (zoals SUSE Linux Enterprise Server 11 SP1) bevat alle daaropvolgende servicepacks voor dat besturingssysteem.  

-   Zie voor meer informatie over clientinstallatiepakketten en de universele Agent [clients implementeren voor UNIX en Linux-servers in System Center Configuration Manager](../../../core/clients/deploy/deploy-clients-to-unix-and-linux-servers.md).  

**Ondersteunde versies:** De volgende versies worden ondersteund door het bestand aangegeven .tar.  

### <a name="aix"></a>AIX  

|||  
|-|-|  
|Versie 5.3 (Power)|CCM-Aix53ppc. &lt;bouwen\>.tar|  
|Versie 6.1 (Power)|CCM-Aix61ppc. &lt;bouwen\>.tar|  
|Versie 7.1 (Power)|CCM-Aix71ppc. &lt;bouwen\>.tar|  

### <a name="centos"></a>CentOS  

|||  
|-|-|  
|Versie 5 x86|CCM-Universalx86. &lt;bouwen\>.tar|  
|Versie 5 x64|CCM-Universalx64. &lt;bouwen\>.tar|  
|Versie 6 x86|CCM-Universalx86. &lt;bouwen\>.tar|  
|Versie 6 x64|CCM-Universalx64. &lt;bouwen\>.tar|  
|Versie 7 x64|CCM-Universalx64. &lt;bouwen\>.tar|  

### <a name="debian"></a>Debian  

|||  
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

|||  
|-|-|  
|Versie 11iv2 IA64|CCM-HpuxB.11.23i64. &lt;bouwen\>.tar|  
|Versie 11iv2 PA-RISC|CCM-HpuxB.11.23PA. &lt;bouwen\>.tar|  
|Versie 11iv3 IA64|CCM-HpuxB.11.31i64. &lt;bouwen\>.tar|  
|Versie 11iv3 PA-RISC|CCM-HpuxB.11.31PA. &lt;bouwen\>.tar|  

### <a name="oracle-linux"></a>Oracle Linux  

|||  
|-|-|  
|Versie 5 x86|CCM-Universalx86. &lt;bouwen\>.tar|  
|Versie 5 x64|CCM-Universalx64. &lt;bouwen\>.tar|  
|Versie 6 x86|CCM-Universalx86. &lt;bouwen\>.tar|  
|Versie 6 x64|CCM-Universalx64. &lt;bouwen\>.tar|  
|Versie 7 x64|CCM-Universalx64. &lt;bouwen\>.tar|  

### <a name="red-hat-enterprise-linux-rhel"></a>Red Hat Enterprise Linux (RHEL)  

|||  
|-|-|  
|Versie 4 x86|CCM-RHEL4x86. &lt;bouwen\>.tar|  
|Versie 4 x64|CCM-RHEL4x64. &lt;bouwen\>.tar|  
|Versie 5 x86|CCM-Universalx86. &lt;bouwen\>.tar|  
|Versie 5 x64|CCM-Universalx64. &lt;bouwen\>.tar|  
|Versie 6 x86|CCM-Universalx86. &lt;bouwen\>.tar|  
|Versie 6 x64|CCM-Universalx64. &lt;bouwen\>.tar|  
|Versie 7 x64|CCM-Universalx64. &lt;bouwen\>.tar|  

### <a name="solaris"></a>Solaris  

|||  
|-|-|  
|Versie 9 SPARC|CCM-Sol9sparc. &lt;bouwen\>.tar|  
|Versie 10 x86|CCM-Sol10x86. &lt;bouwen\>.tar|  
|Versie 10 SPARC|CCM-Sol10sparc. &lt;bouwen\>.tar|  
|Versie 11 x86|CCM-Sol11x86. &lt;bouwen\>.tar|  
|Versie 11 SPARC|CCM-Sol11sparc. &lt;bouwen\>.tar|  

### <a name="suse-linux-enterprise-server-sles"></a>SUSE Linux Enterprise Server (SLES)  

|||  
|-|-|  
|Versie 9 x86|CCM-SLES9x86. &lt;bouwen\>.tar|  
|Versie 10 SP1 x86|CCM-Universalx86. &lt;bouwen\>.tar|  
|Versie 10 SP1 x64|CCM-Universalx64. &lt;bouwen\>.tar|  
|De SP1 versie 11 x86|CCM-Universalx86. &lt;bouwen\>.tar|  
|De SP1 versie 11 x64|CCM-Universalx64. &lt;bouwen\>.tar|  
|Versie 12 x64|CCM-Universalx64. &lt;bouwen\>.tar|  

### <a name="ubuntu"></a>Ubuntu  

|||  
|-|-|  
|Versie 10.04 TNS x86|CCM-Universalx86. &lt;bouwen\>.tar|  
|Versie 10.04 TNS x64|CCM-Universalx64. &lt;bouwen\>.tar|  
|Versie 12.04 TNS x86|CCM-Universalx86. &lt;bouwen\>.tar|  
|Versie 12.04 TNS x64|CCM-Universalx64. &lt;bouwen\>.tar|  
|Versie 14.04 TNS x86|CCM-Universalx86. &lt;bouwen\>.tar|  
|Versie 14.04 TNS x64|CCM-Universalx64. &lt;bouwen\>.tar|  

##  <a name="mobile-devices-enrolled-by-microsoft-intune"></a>Mobiele apparaten die zijn geregistreerd door Microsoft Intune  
 Zie de volgende twee onderwerpen in de Microsoft Intune Documentatiebibliotheek voor meer informatie over de computers en apparaten die u beheren kunt wanneer u Microsoft Intune geïntegreerd met Configuration Manager:  

-   [Beheermogelijkheden voor mobiele apparaten in Microsoft Intune](https://docs.microsoft.com/intune/get-started/choose-how-to-manage-devices)  
-   [Windows-PC-mogelijkheden voor Computerbeheer in Microsoft Intune](https://docs.microsoft.com/intune/get-started/windows-pc-management-capabilities-in-microsoft-intune)  

##  <a name="bkmk_OnpremOS"></a>Lokale beheer van mobiele apparaten  
 Configuration Manager beschikt over ingebouwde mogelijkheden voor beheer van apparaten die zijn lokale zonder clientsoftware te installeren.  Zie voor meer informatie [mobiele apparaten beheren met on-premises infrastructuur in System Center Configuration Manager](../../../mdm/understand/manage-mobile-devices-with-on-premises-infrastructure.md).  

 **Vereisten en beperkingen:**  

-   U moet configureren de **serviceverbindingspunt** op de bovenste site van uw hiërarchie.  

**Ondersteunde besturingssystemen:**  

- **Windows 10 Pro** (x86, x64)  

- **Windows 10 Pro Enterprise** (x86, x64)  

- **Windows 10 IoT Enterprise** (x86, x64)

- **Windows 10 Mobile**  

- **Windows 10 Mobile Enterprise**  

- **Windows 10 Mobile IoT Enterprise**

- **Windows 10 Team voor oppervlak Hub**

##  <a name="bkmk_ExSrvConOS"></a>Exchange Server-connector  
Configuration Manager ondersteunt beperkt beheer van apparaten die verbinding met uw Exchange-Server, maken zonder dat de Configuration Manager-client installeert. Zie [Mobiele apparaten beheren met System Center Configuration Manager en Exchange](../../../mdm/deploy-use/manage-mobile-devices-with-exchange-activesync.md) voor meer informatie.  

 **Vereisten en beperkingen:**  

-   Configuration Manager biedt beperkt beheer voor mobiele apparaten als u apparaten met Exchange Server-connector voor Exchange ActiveSync die verbinding maken met een server waarop Exchange Server of Exchange Online.  

-   Zie voor meer informatie over welke beheerfuncties Configuration Manager biedt ondersteuning voor mobiele apparaten die Exchange Server-connector beheert, bepalen hoe mobiele apparaten beheren in Configuration Manager.  

**Ondersteunde versies van Exchange-Server:**  

-   **Exchange Server 2010 SP1**  

-   **Exchange Server 2010 SP2**  

-   **Exchange Server 2013**  

-   **Exchange Online (Office 365)**: Dit omvat Business Productivity Online Standard Suite  

