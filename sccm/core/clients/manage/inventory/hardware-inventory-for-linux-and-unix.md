---
title: 'Hardware-inventaris | Microsoft Docs | Linux, UNIX '
description: Meer informatie over hoe hardware-inventaris voor Linux en UNIX in System Center Configuration Manager gebruiken.
ms.custom: na
ms.date: 02/22/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 1026d616-2a20-4fb2-8604-d331763937f8
caps.latest.revision: "6"
author: andredm7
ms.author: andredm
manager: angrobe
ms.openlocfilehash: b6776fbe0cfca23244d767cffd554a2ef4567a2d
ms.sourcegitcommit: 51fc48fb023f1e8d995c6c4eacfda7dbec4d0b2f
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 08/07/2017
---
# <a name="hardware-inventory-for-linux-and-unix-in-system-center-configuration-manager"></a>Hardware-inventaris voor Linux en UNIX in System Center Configuration Manager

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*

De System Center Configuration Manager-client voor Linux en UNIX ondersteunt hardware-inventaris. Nadat het verzamelen van hardware-inventaris kunt u inventaris weergeven in de resource explorer of Configuration Manager-rapporten uitvoeren en deze informatie gebruiken om het maken van query's en verzamelingen die u de volgende bewerkingen:  

-   Software-implementatie  

-   Onderhoudsvensters afdwingen  

-   Aangepaste clientinstellingen implementeren  

 Voor hardware-inventaris voor Linux en UNIX-servers wordt een op standaarden gebaseerde CIM-server (Common Information Model) gebruikt. De CIM-server wordt uitgevoerd als een softwareservice (of daemon) en biedt een infrastructuur die is gebaseerd op standaarden voor DMTF (Distributed Management Task Force). De CIM-server biedt functionaliteit die vergelijkbaar is met de CIM-mogelijkheden van WMI (Windows Management Infrastructure) die beschikbaar zijn op Windows-computers.  

 Vanaf cumulatieve update 1 gebruikt de client voor Linux en UNIX versie 1.0.6 van de open source **omniserver** van de **Open Groep**. (Voor cumulatieve update 1 gebruikte de client **nanowbem** als CIM-server).  

 De CIM-server wordt geïnstalleerd als onderdeel van de client voor Linux en UNIX. De client voor Linux en UNIX communiceert rechtstreeks met de CIM-server en maakt geen gebruik van de WS-MAN-interface van de CIM-server. De WS-MAN-poort op de CIM-server wordt uitgeschakeld als de client wordt geïnstalleerd. Microsoft ontwikkelde de CIM-server die nu als open source beschikbaar is via het OMI-project (Open Management Infrastructure). Zie de website [The Open Group](http://go.microsoft.com/fwlink/p/?LinkId=262317) over het Open Management Infrastructure Project voor meer informatie.  

 Hardware-inventaris op Linux- en UNIX-servers werkt via het toewijzen van bestaande Win32 WMI-klassen en eigenschappen aan gelijkwaardige klassen en eigenschappen voor Linux- en UNIX-servers. Deze-op-een toewijzing van klassen en eigenschappen kunt de Linux- en UNIX hardware-inventaris te integreren met Configuration Manager. Inventarisgegevens van Linux en UNIX-servers worden weergegeven samen met de inventaris van Windows-computers in de Configuration Manager-console en rapporten. Dit biedt een consistente heterogene beheerervaring.  

> [!TIP]  
>  U kunt de waarde **Bijschrift** voor de klasse **Besturingssysteem** gebruiken voor het identificeren van verschillende Linux- en UNIX-besturingssystemen in query's en verzamelingen.  

##  <a name="BKMK_ConfigHardwareforLnU"></a> Hardware-inventaris voor Linux- en UNIX-servers configureren  
 U kunt de standaardclientinstellingen gebruiken of aangepaste clientapparaatinstellingen maken om de hardware-inventaris te configureren. Wanneer u aangepaste clientinstellingen voor apparaten gebruikt, kunt u de klassen en eigenschappen configureren die u alleen van alleen uw Linux- en UNIX-servers wilt verzamelen. U kunt ook aangepaste schema's opgeven wanneer u de volledige inventaris en delta-inventaris van uw Linux- en UNIX-servers wilt verzamelen.  

 De client voor Linux en UNIX ondersteunt de volgende hardware-inventarisklassen die beschikbaar op Linux- en UNIX-servers:  

-   Win32_BIOS  

-   Win32_ComputerSystem  

-   Win32_DiskDrive  

-   Win32_DiskPartition  

-   Win32_NetworkAdapter  

-   Win32_NetworkAdapterConfiguration  

-   Win32_OperatingSystem  

-   Win32_Process  

-   Win32_Service  

-   Win32Reg_AddRemovePrograms  

-   SMS_LogicalDisk  

-   SMS_Processor  

 Niet alle eigenschappen voor deze inventarisklassen zijn ingeschakeld voor Linux en UNIX-computers in Configuration Manager.  

##  <a name="BKMK_OperationsforHardwareforLnU"></a> Bewerkingen voor hardware-inventaris  
 Nadat u de hardware-inventaris van uw Linux- en UNIX-servers hebt verzameld, kunt u deze informatie op dezelfde manier bekijken en gebruiken als de inventaris die u verzamelt van andere computers:  

-   Gebruik Resource Explorer om gedetailleerde informatie weer te geven over de hardware-inventaris die wordt verzameld van Linux- en UNIX-servers.  

-   Query's op basis van specifieke hardwareconfiguraties maken  

-   Op query’s gebaseerde verzamelingen maken die zijn gebaseerd op specifieke hardwareconfiguraties  

-   Rapporten met specifieke details over hardwareconfiguraties uitvoeren  

 Hardware-inventaris op een Linux- of UNIX-server wordt uitgevoerd volgens de planning die u in de clientinstellingen configureert. Dit is standaard elke zeven dagen. De client voor Linux en UNIX ondersteunt zowel volledige inventarisatiecycli als delta-inventarisatiecycli.  

 Ook kunt u de client op een Linux- of UNIX-server dwingen onmiddellijk hardware-inventaris uit te voeren. Gebruik voor het uitvoeren van de hardware-inventaris op een client **hoofdreferenties** om de volgende opdracht uit te voeren en een hardware-inventariscyclus te starten: **/opt/microsoft/configmgr/bin/ccmexec -rs hinv**  

 Acties voor hardware-inventaris worden ingevoerd in het logboekbestand van de client, **scxcm.log**.  

##  <a name="BKMK_CustomHINVforLinux"></a> Open Management Infrastructure gebruiken om aangepaste een hardware-inventaris te maken  
 De client voor Linux en UNIX ondersteunt aangepaste hardware-inventaris die u kunt maken met behulp van de Open Management Infrastructure (OMI). Volg hiervoor de volgende stappen:  

1.  Een aangepaste inventarisprovider maken met de OMI-bron  

2.  Computers configureren voor het gebruik van de nieuwe provider voor inventarisrapportage  

3.  Configuration Manager voor de ondersteuning van de nieuwe provider inschakelen  

###  <a name="BKMK_LinuxProvider"></a> Een aangepaste hardware-inventarisprovider maken voor Linux- en UNIX-computers.  
 Gebruik voor het maken van een aangepaste hardware-inventarisprovider voor Configuration Manager-client voor Linux en UNIX **OMI Source - v.1.0.6** en volg de instructies uit de introductiehandleiding. Met dit proces maakt u een Managed Object Format-bestand waarmee u het schema van de nieuwe provider definieert. Later importeert u het MOF-bestand naar Configuration Manager ondersteuning van de nieuwe aangepaste inventarisklasse inschakelen.  

 U kunt de OMI Source - v.1.0.6 en de introductiehandleiding voor OMI downloaden van de website [The Open Group](http://go.microsoft.com/fwlink/p/?LinkId=262317) . U vindt deze downloads op de **documenten** op de volgende webpagina op de website opengroup.org tabblad: [Open Management Infrastructure (OMI)](http://go.microsoft.com/fwlink/p/?LinkId=286805).  

###  <a name="BKMK_AddProvidertoLinux"></a> Configureer elke computer met Linux of UNIX met de aangepaste hardware-inventarisprovider:  
 Nadat u een aangepaste inventarisprovider hebt gemaakt, moet u het providerbibliotheekbestand kopiëren naar en registreren op elke computer waarvan u de inventaris wilt verzamelen.  

1.  Kopieer de providerbibliotheek naar elke Linux- en UNIX-computer waarvan u de inventaris wilt verzamelen. De naam van de providerbibliotheek lijkt op het volgende: **XYZ_MyProvider.so**  

2.  Registreer vervolgens de providerbibliotheek op elke Linux- en UNIX-computer bij de OMI-server. De OMI-server geïnstalleerd op de computer wanneer u de Configuration Manager-client voor Linux en UNIX installeert, maar u moet aangepaste providers handmatig registreren. Gebruik de volgende opdrachtregel voor het registreren van de provider: **/opt/microsoft/omi/bin/omireg XYZ_MyProvider.so**  

3.  Nadat u de nieuwe provider hebt geregistreerd, test u de provider met behulp van het **omicli** -hulpprogramma. De **omicli** hulpprogramma is geïnstalleerd op elke Linux- en UNIX-computer wanneer u de Configuration Manager-client voor Linux en UNIX installeert. Voorbeeld: als **XYZ_MyProvider** de naam is van de provider die u hebt gemaakt, voert u de volgende opdracht op de computer: **/opt/microsoft/omi/bin/omicli ei root/cimv2 XYZ_MyProvider**  

     voor informatie over **omicli** het testen van aangepaste providers.  

> [!TIP]  
>  Gebruik softwaredistributie om de aangepaste providers te implementeren en om aangepaste providers op elke Linux- en UNIX-clientcomputer te registreren.  

###  <a name="BKMK_AddLinuxProvidertoCM"></a> Schakel de nieuwe inventarisklasse in Configuration Manager in:  
 Voordat u met Configuration Manager rapporten kunt maken over de inventaris die door de nieuwe provider op Linux- en UNIX-computers wordt gerapporteerd, moet u het Managed Object Format-bestand importeren waarin u het schema van uw aangepaste provider hebt gedefinieerd.  

 Als u wilt importeren van een aangepaste MOF-bestand in Configuration Manager, Zie [hardware-inventaris configureren in System Center Configuration Manager](../../../../core/clients/manage/inventory/configure-hardware-inventory.md).  
