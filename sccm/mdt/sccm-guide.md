---
title: Snel starten - System Center 2012 R2 Configuration Manager
titleSuffix: Microsoft Deployment Toolkit
description: 'Quick Start guide voor Microsoft-implementatietoolkit met System Center 2012 R2 Configuration Manager. '
ms.date: 09/09/2016
ms.prod: configuration-manager
ms.technology: configmgr-osd
ms.topic: article
ms.assetid: b12de852-a799-4c16-b51c-cc3abbd3ca3a
author: aczechowski
ms.author: aaroncz
manager: angrobe
ms.openlocfilehash: 8f768ec6eef945163667b346118d2d65dcb2e3c6
ms.sourcegitcommit: 645cd5a324bdd299906efa27eaca5885eafc9e9c
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 01/16/2018
---
# <a name="quick-start-guide-for-microsoft-system-center-2012-r2-configuration-manager"></a>Quick Start Guide voor Microsoft System Center 2012 R2 Configuration Manager  
 Microsoft Deployment Toolkit (MDT) 2013 biedt technologie voor het implementeren van Windows-besturingssystemen en Microsoft Office. Deze snelstartgids kunt u snel evalueren MDT 2013 dankzij de verkorte, stapsgewijze instructies voor het gebruik van het besturingssysteem Windows 8.1 installeren met Microsoft System Center 2012 R2 Configuration Manager. Deze snelstartgids demonstreert hoe u het implementatiescenario voor nieuwe Computer die wordt ingegaan op de implementatie van Windows 8.1 naar een andere computer uitvoeren. Dit scenario wordt ervan uitgegaan dat er is geen gebruikersgegevens of profiel behouden.  

> [!NOTE]     
>  In dit document, *Windows* geldt voor de besturingssystemen Windows 8.1, Windows 8, Windows 7, Windows Server® 2012 R2, Windows Server 2012 en Windows Server 2008 R2, tenzij anders vermeld. MDT biedt geen ondersteuning voor ARM-processor gebaseerde versies van Windows. Op deze manier *MDT* verwijst naar MDT 2013, tenzij anders vermeld.  

 Bekijk na het evalueren van MDT met behulp van deze handleiding, de rest van de MDT-richtlijnen voor meer informatie over geavanceerde functies van de technologie.  

## <a name="prerequisites"></a>Vereisten  
 Nul Touch installatie installaties met Configuration Manager hebben de volgende vereisten.  

### <a name="required-software"></a>Vereiste Software  
 De volgende software is vereist voor het voltooien van deze handleiding:  

-   Windows Server 2008 R2  

-   Microsoft SQL Server 2008 R2  

-   SQL Server 2008 R2 servicepack 1 (SP1)  

-   SQL Server 2008 R2 SP1 en cumulatieve Update 6 (cu6 ondersteund)  

-   Windows 8.1  

-   System Center 2012 R2 Configuration Manager  

-   Microsoft .NET Framework versie 3.5 met SP1  

-   Windows PowerShell versie 2.0  

-   Windows Preinstallation Environment (Windows PE), die is opgenomen in Configuration Manager  

-   Netwerkservices, inclusief System DNS (Domain Name) en Dynamic Host Configuration Protocol (DHCP)  

-   Active Directory Domain Services (AD DS)  

 Zie de [ondersteunde configuraties voor Configuration Manager](http://technet.microsoft.com/library/gg682077.aspx) voor combinaties van aanvullende software die kunnen worden gebruikt voor het installeren van Configuration Manager.  

> [!NOTE]   
>  De Taaksequencer gebruikt voor implementaties van MDT is vereist dat het maken van globale Object recht worden toegewezen aan de referenties die worden gebruikt voor toegang tot en het uitvoeren van de Workbench-implementatie en het implementatieproces. Dit recht is normaal gesproken beschikbaar voor accounts met machtigingen op Administrator-niveau (tenzij expliciet worden verwijderd). Ook beveiliging gespecialiseerde – beveiligingsprofiel beperkte functionaliteit (SSLF) Hiermee verwijdert u het recht globale objecttoegang maken en moet niet worden toegepast op computers met MDT geïmplementeerd.  

### <a name="computer-configuration"></a>Computerconfiguratie  
 Instellen van de computers die worden vermeld in de volgende tabel voor het voltooien van deze handleiding. Deze computers kunnen zijn voor fysieke computers of virtuele machines (VM's) met de systeembronnen die is aangewezen.  


|**Computer**|**Beschrijving en de systeembronnen**|  
|-|-|  
|MDT-01-WDG|Deze computer wordt uitgevoerd voor de infrastructuur van de MDT en Configuration Manager. De computer wordt uitgevoerd van Windows Server 2008 R2 met de volgende netwerkservices geïnstalleerd:<br /><br /> -AD DS<br />-DNS-Server<br />-DHCP-Server<br />-De Windows Deployment Services<br /><br /> De resources van de computer zijn als volgt:<br /><br /> -Quad core-processor van 2,66 GHz (gigahertz) of sneller uitgevoerd<br />-4 gigabyte (GB) of meer fysiek geheugen<br />-Een schijfpartitie met 40 GB of meer van de beschikbare schijfruimte; Deze worden de partitie van station C<br />-Een CD-ROM of dvd-station dat de stationsletter D wordt toegewezen<br />-Een schijfpartitie met 40 GB of meer van de beschikbare schijfruimte; Deze worden partitie E.|  
|WDG-REF-01|Dit is de referentiecomputer die wordt uitgevoerd geen huidige besturingssysteem. De resources van de computer zijn als volgt:<br /><br /> -Processor met 1,4 GHz of sneller<br />-1 GB of meer fysiek geheugen<br />-16 GB of meer van de beschikbare schijfruimte|  
|CLI-01-WDG|Dit is de doelcomputer en dat er geen huidige besturingssysteem wordt uitgevoerd. De resources van de computer zijn als volgt:<br /><br /> -Processor met 1,4 GHz of sneller<br />-1 GB of meer fysiek geheugen<br />-16 GB of meer van de beschikbare schijfruimte|  

 De bronnen in de voorgaande tabel overeen met de systeembronnen aanbevolen om uit te voeren van de stappen in deze handleiding. Voor informatie over de minimale systeemvereisten met resource voor:  

-   WindowsServer 2008 R2, Zie [installeren van Windows Server 2008 R2](http://technet.microsoft.com/library/dd379511.aspx)  

-   SQL Server 2008 R2 Zie [Hardware- en softwarevereisten voor het installeren van SQL Server 2008 R2](http://technet.microsoft.com/library/ms143506.aspx)  

> [!NOTE]   
>  Deze handleiding wordt ervan uitgegaan dat MDT wordt geëvalueerd op 64-bits (x 64) fysieke of virtuele computers. Als de evaluatie MDT op 32-bits (x 86) platforms, downloaden en installeren de x86-edities van MDT en de onderdelen die in deze handleiding worden beschreven.  

## <a name="step-1-prepare-the-prerequisite-infrastructure"></a>Stap 1: De vereiste infrastructuur voorbereiden  
 Voor de doeleinden van deze handleiding, alle de vereiste infrastructuur-services worden uitgevoerd op de computer met de naam *MDT-01-WDG*. De vereiste software, serverfuncties en -services op deze computer installeren voordat u MDT installeert.  

> [!NOTE]   
>  Deze sectie wordt ervan uitgegaan dat u een nieuwe Configuration Manager-infrastructuur voor MDT maakt. Als u van een bestaande Configuration Manager-infrastructuur gebruikmaakt, bekijkt u de stappen in deze sectie en vervang bestaande resourcenamen voor de resources die zijn gemaakt in deze sectie (zoals de computernaam en gedeelde mappen). Bekijk deze sectie gaat u verder met [stap 2: De MDT-omgeving voorbereiden](#PrepareMDTEnvironment).  

 De vereiste infrastructuur voorbereiden voordat u MDT door installeert:  

-   Windows Server 2008 R2 installeren zoals is beschreven in [stap 1-1: Installeer Windows Server 2008 R2](#InstallWindowsServer)  

-   Maken van de vereiste mappen en netwerk deelt, zoals beschreven in [stap 1-2: De vereiste mappen maken en netwerkshares](#CreateRequiredFolders)  

-   Het verkrijgen van de software nodig voor het uitvoeren van de stappen in deze handleiding, zoals beschreven in [stap 1-3: De vereiste Software verkrijgen](#ObtainRequiredSoftware)  

-   De AD DS-serverrol installeren zoals is beschreven in [stap 1-4: De AD DS-serverfunctie installeren](#InstallADDSRole)  

-   De DHCP-serverfunctie installeren zoals is beschreven in [stap 1-5: De DHCP-serverfunctie installeren](#InstallDHCPServerRole)  

-   De serverfunctie Web Services (IIS) installeren zoals is beschreven in [stap 1-6: De serverfunctie Web Services (IIS) installeren](#InstallIISRole)  

-   Toevoegen van de vereiste onderdelen voor Windows Server 2008 R2, zoals beschreven in [stap 1-7: De vereiste Windows Server 2008 R2-onderdelen toevoegen](#AddRequiredServerFeatures)  

-   Maken van de gebruikers- en serviceaccounts vereist voor het uitvoeren van de stappen in deze handleiding, zoals wordt beschreven [stap 1-8: Maak de gebruiker vereist en serviceaccounts](#CreateRequiredUserAccounts)  

-   Installatie van SQL Server 2008 R2 voor Configuration Manager te gebruiken zoals beschreven in [stap 1-9: Installeer SQL Server 2008 R2](#InstallSQLServer)  

-   De siteserver toevoegen aan de beveiligingsgroep Administrators, zoals beschreven in [stap 1-10: De siteserver toevoegen aan de beveiligingsgroep Administrators](#AddSiteSecuritytoAdminGroup)  

-   Installeren van Configuration Manager, zoals beschreven in [stap 1-11: Configuration Manager installeren](#InstallConfigManager)  

-   Configureren van het netwerktoegangsaccount die Configuration Manager-clients gebruiken voor toegang tot distributiepunten van Configuration Manager verwijst, zoals beschreven in [stap 1-12: Het netwerktoegangsaccount configureren](#ConfigureNetworkAccessAccount)  

-   De Configuration Manager-sitegrenzen en grensgroepen configureren zoals beschreven in [stap 1-13: De Configuration Manager-Sitegrenzen en Grensgroepen configureren](#ConfigurationManagerSiteBoundaries)  

-   Het publiceren van site-informatie in AD DS en DNS configureren zoals beschreven in [stap 1-14: Het publiceren van Site-informatie in AD DS en DNS configureren](#ConfigurePublishingSiteInfo)  

###  <a name="InstallWindowsServer"></a>Stap 1-1: Installeer Windows Server 2008 R2  
  Informatie voor het installeren van Windows Server 2008 R2.  Accepteer de standaardwaarden tenzij anders vermeld.  

|Als u wordt gevraagd| Deze waarden opgeven|   
|-|-|  
|**Waar wilt u Windows installeren?**|**Schijf 0 niet-toegewezen ruimte**|  
|**Wachtwoord**|Een sterk wachtwoord|  
|**Computernaam**|**MDT-01-WDG**|  
|**De notatie voor de volumes C en E**|**NTFS**|  
|**TCP/IP-configuratie**|Met een statische IP-adresconfiguratie, met de andere TCP/IP-configuratieopties voor de omgeving configureren|  

###  <a name="CreateRequiredFolders"></a>Stap 1-2: De vereiste mappen maken en netwerkshares  
 Het implementatieproces MDT vereist aanvullende mappen die worden gebruikt als bron voor bestanden of bestanden die zijn gemaakt tijdens het implementatieproces MDT op te slaan. Sommige van deze mappen moet worden gedeeld, zodat deze toegankelijk is vanaf andere computers.  

#### <a name="to-create-the-required-folders-and-share"></a>De vereiste mappen maken en delen  
1. Het implementatieproces MDT vereist verschillende mappen. Maak de volgende mappen en shares met de opgegeven machtigingen voor elke share.    

  |Deze map maken  |Met deze sharenaam  |Met deze machtigingen voor delen  |  
  |----|----|----|  
  |E:\Source$|Bron$|**Beheerders:** Mede-eigenaar<br /><br /> **Iedereen:** Lezen|  
  |E:\Images$|Installatiekopieën$|**Beheerders:** Mede-eigenaar<br /><br /> **Iedereen:** Lezen|  
  |E:\Capture$|$ Vastleggen|**Beheerders:** Mede-eigenaar<br /><br /> **Iedereen:** Lezen|  
  |E:\Packages$|Pakketten$|**Beheerders:** Mede-eigenaar<br /><br /> **Iedereen:** Lezen|  

2. Maak de volgende mappen:  

    -   E:\CMDownloads  

    -   E:\Source$\CustomSettings  

    -   E:\Source$\Drivers  

    -   E:\Source$\Windows_8-1  

    -   E:Source$ MDT_2013  

    -   E:Source$ SQL2008R2  

    -   E:Source$ SQL2008R2SP1  

    -   E:Source$ SQL2008R2CU6  

    -   E:Source$ ConfigMgr  

    -   E:Packages$ stuurprogramma 's  

3. Kopieer de apparaatstuurprogramma's voor de referentiecomputer (WDG-REF-01) en de doelcomputer (WDG-CLI-01) naar E:\Source$\Drivers.  

> [!NOTE]   
>  De processen in deze handleiding wordt ervan uitgegaan dat de referentiecomputer en de doelcomputer de dezelfde apparaten hebben en geen stuurprogramma's voor verschillende apparaten vereisen.  

###  <a name="ObtainRequiredSoftware"></a>Stap 1-3: De vereiste Software verkrijgen  
 Naast Windows Server 2008 R2, Windows 8.1-en Configuration Manager, worden bepaalde software is vereist voor evaluatie van MDT op basis van de processen in deze handleiding.  De volgende tabel bevat de software nodig voor het uitvoeren van implementaties met MDT, waar u kunt de software te verkrijgen en waar u de software op de MDT-01-WDG plaatsen.  

 |**Deze software verkrijgen**|**In deze map te plaatsen**|  
 |-|-|  
 |MDT 2013|E:\Source$\MDT_2013|  
 |Windows 8.1 distributiebestanden van de productmedia|E:\Source$\Windows_8-1|  
 |Apparaatstuurprogramma's vereist zijn voor de referentie- en doelcomputers computers (WDG-REF-01 en CLI-01-WDG)|E:\Source$\Drivers|  
 |SQL Server 2008 R2 van de productmedia|E:\Source$\SQL2008R2|  
 |SQL Server 2008 R2 SP1, beschikbaar op [http://www.microsoft.com/download/details.aspx?id=26727](http://www.microsoft.com/download/details.aspx?id=26727)|E:\Source$\SQL2008R2SP1|  
 |SQL Server 2008 R2 SP1 cu6 ondersteund, beschikbaar op [http://support.microsoft.com/kb/2679367](http://support.microsoft.com/kb/2679367)|E:\Source$\SQL2008R2SP1CU6|  
 |Configuration Manager van de productmedia|E:\Source$\ConfigMgr|  

###  <a name="InstallADDSRole"></a>Stap 1-4: De AD DS-serverfunctie installeren  
 AD DS is vereist voor verificatie en fungeren als een opslagplaats voor configuratiewaarden voor de Microsoft-producten en technologieën die gebruikmaakt van MDT, zoals SQL Server 2008 R2 en Configuration Manager.  

 AD DS wilt installeren, moet u de DCPROMO-Wizard voor het configureren van de computer als een domeincontroller uitvoeren. Installatie van AD DS met behulp van de volgende informatie de standaardinstellingen accepteren, tenzij anders vermeld.  

|**Als u wordt gevraagd**|**Dit doet**|
|-|-|   
|Voor het domeintype|Een nieuw domein in een nieuw forest maakt.|  
|Voor de volledig gekwalificeerde domeinnaam|Type **mdt2013.corp.woodgrovebank.com**.|  
|Voor het functionele forestniveau|Selecteer **Windows Server 2008 R2**.|  
|De DNS-Server-service installeren als onderdeel van het installatieproces van domeincontroller|Klik op **Ja**.|  

###  <a name="InstallDHCPServerRole"></a>Stap 1-5: De DHCP-serverfunctie installeren  
 De serverfunctie DHCP-Server is vereist voor het bieden van automatische IP-configuratie voor de doelcomputers. DHCP-Server installeren met behulp van de volgende informatie de standaardinstellingen accepteren, tenzij anders vermeld.  

> [!NOTE]   
>  Als u van een gevirtualiseerde omgeving gebruikmaakt, uitschakelen DHCP-configuratie met de virtualisatiesoftware op de computer. Zorg ervoor dat de MDT-01-WDG met DHCP-Server-service de enige provider van IP-configuratie met behulp van DHCP.  

|**Op deze wizardpagina**|**Dit doet**|  
|-|-|  
|**DHCP-server in Active Directory autoriseren**|WDG-MDT-01 voor client-IP-configuratie toestaan.|  
|**DHCP-scopes**|Maak een juiste scope die kan worden gebruikt om automatisch te configureren TCP/IP voor WDG-REF-01 en WDG-CLI-01.|  
|**Configuratie van stateless DHCPv6**|Uitschakelen van stateless DHCPv6-modus voor deze server.|  

###  <a name="InstallIISRole"></a>Stap 1-6: De serverfunctie Web Services (IIS) installeren  
 De serverfunctie Web Services (IIS) installeren met de functieservices die worden vermeld in de volgende tabel.  Deze functieservices zijn vereist voor de SQL Server 2008 R2 en Configuration Manager. Tenzij anders vermeld, moet u de standaardwaarden gebruikt.  

|Functieservice|Status|  
|-|-|  
|Webserver|geïnstalleerd|  
|Veelvoorkomende HTTP-functies|geïnstalleerd|  
|Statische inhoud|geïnstalleerd|  
|Standaarddocument|geïnstalleerd|  
|Bladeren door mappen|geïnstalleerd|  
|HTTP-fouten|geïnstalleerd|  
|HTTP-omleiding|geïnstalleerd|  
|WebDAV-publicaties|geïnstalleerd|  
|Toepassingsontwikkeling|geïnstalleerd|  
|ASP.NET|geïnstalleerd|  
|.NET-uitbreidbaarheid|geïnstalleerd|  
|ASP|Niet geïnstalleerd|  
|CGI|Niet geïnstalleerd|  
|ISAPI-extensies|geïnstalleerd|  
|ISAPI-filters|geïnstalleerd|  
|Insluiten vanaf server|Niet geïnstalleerd|  
|Status en diagnose|geïnstalleerd|  
|HTTP-logboekregistratie|geïnstalleerd|  
|Logboekregistratieprogramma 's|geïnstalleerd|  
|Controle aanvragen|geïnstalleerd|  
|tracering|geïnstalleerd|  
|Aangepaste logboekregistratie|Niet geïnstalleerd|  
|ODBC-registratie|Niet geïnstalleerd|  
|Beveiliging|geïnstalleerd|  
|Basisverificatie|Niet geïnstalleerd|  
|Windows-verificatie|geïnstalleerd|  
|Digest-verificatie|Niet geïnstalleerd|  
|Verificatie van clientcertificaattoewijzing|Niet geïnstalleerd|  
|Verificatie van IIS-clientcertificaattoewijzing|Niet geïnstalleerd|  
|URL-autorisatie|Niet geïnstalleerd|  
|Filtering aanvragen|geïnstalleerd|  
|IP-adres en domein beperking|Niet geïnstalleerd|  
|Prestatie|geïnstalleerd|  
|Compressie van statische inhoud|geïnstalleerd|  
|Compressie van dynamische inhoud|Niet geïnstalleerd|  
|Beheerhulpprogramma's|geïnstalleerd|  
|IIS-beheerconsole|geïnstalleerd|  
|Scripts voor IIS-beheer en hulpprogramma 's|Niet geïnstalleerd|  
|Management-Service|Niet geïnstalleerd|  
|Compatibiliteit met IIS 6-beheer|geïnstalleerd|  
|Compatibiliteit met IIS 6-metabase|geïnstalleerd|  
|Compatibiliteit met IIS 6 WMI|geïnstalleerd|  
|IIS 6-scripthulpprogramma 's|Niet geïnstalleerd|  
|IIS 6-beheerconsole|Niet geïnstalleerd|  
|FTP-publicatieservice|Niet geïnstalleerd|  
|FTP-Server|Niet geïnstalleerd|  
|FTP-beheerconsole|Niet geïnstalleerd|  
|IIS Hostable Web Core|Niet geïnstalleerd|  

###  <a name="AddRequiredServerFeatures"></a>Stap 1-7: De vereiste Windows Server 2008 R2-onderdelen toevoegen  
 Naast het installeren van de vereiste functies voor Windows Server 2008 R2-server, voeg de volgende vereiste onderdelen in Serverbeheer in de **Functieoverzicht** sectie:  

-   Background Intelligent Transfer Service  

-   Externe differentiële compressie  

###  <a name="CreateRequiredUserAccounts"></a>Stap 1-8: Maak de gebruiker vereist en serviceaccounts  
 Configuration Manager en SQL Server 2008 R2 moet gebruikersaccounts tijdens de installatie.  Gebruik de volgende informatie voor het maken van deze accounts.  


|**Dit account maakt**|**Met deze instellingen**|  
|-|-|  
|SQL Server Agent-serviceaccount|1.  In **voornaam**, type **SQL Agent**.<br />2.  In **achternaam**, type **serviceaccount**.<br />3.  In **aanmeldingsnaam van gebruiker**, type **SQLAgent**.<br />4.  In **wachtwoord** en **wachtwoord bevestigen**, type  **P@ssw0rd** .<br />5.  Schakel de **gebruiker moet wachtwoord bij volgende aanmelding wijzigen** selectievakje.<br />6.  Selecteer de **wachtwoord verloopt nooit** selectievakje.<br />7.  Maak het account lid is van de beveiligingsgroep Domeinadministrators.<br />8.  In **beschrijving**, type **-serviceaccount gebruikt SQL Server 2008 R2-Agent-service uit te voeren**.|  
|Database-Engine van SQL Server-serviceaccount|1.  In **voornaam**, type **SQL DB-Engine**.<br />2.  In **achternaam**, type **serviceaccount**.<br />3.  In **aanmeldingsnaam van gebruiker**, type **SQLDBEngine**.<br />4.  In **wachtwoord** en **wachtwoord bevestigen**, type  **P@ssw0rd** .<br />5.  Schakel de **gebruiker moet wachtwoord bij volgende aanmelding wijzigen** selectievakje.<br />6.  Selecteer de **wachtwoord verloopt nooit** selectievakje.<br />7.  Maak het account lid is van de beveiligingsgroep Domeinadministrators.<br />8.  In **beschrijving**, type **-serviceaccount gebruikt voor het uitvoeren van de database-engine van SQL Server 2008 R2**.|  
|SQL Server Reporting Services-serviceaccount|1.  In **voornaam**, type **SQL Reporting**.<br />2.  In **achternaam**, type **serviceaccount**.<br />3.  In **aanmeldingsnaam van gebruiker**, type **SQLReport**.<br />4.  In **wachtwoord** en **wachtwoord bevestigen**, type  **P@ssw0rd** .<br />5.  Schakel de **gebruiker moet wachtwoord bij volgende aanmelding wijzigen** selectievakje.<br />6.  Selecteer de **wachtwoord verloopt nooit** selectievakje.<br />7.  Maak het account lid is van de beveiligingsgroep Domeinadministrators.<br />8.  In **beschrijving**, type **gebruikt voor het uitvoeren van SQL Server 2008 R2 reporting services-serviceaccount**.|  
|System Center Configuration Manager-Client Network Access account|1.  In **voornaam**, type **CM 2012**.<br />2.  In **achternaam**, type **toegang tot het netwerk van de Client**.<br />3.  In **aanmeldingsnaam van gebruiker**, type **CMNetAccess**.<br />4.  In **wachtwoord** en **wachtwoord bevestigen**, type  **P@ssw0rd** .<br />5.  Schakel de **gebruiker moet wachtwoord bij volgende aanmelding wijzigen** selectievakje.<br />6.  Selecteer de **wachtwoord verloopt nooit** selectievakje.<br />7.  In **beschrijving**, type **-serviceaccount gebruikt als het netwerktoegangsaccount voor Configuration Manager-Client**.|  

###  <a name="InstallSQLServer"></a>Stap 1-9: Installeer SQL Server 2008 R2  
 Voordat u Configuration Manager installeert, installeert u SQL Server 2008 R2 met SP1 en cu6 ondersteund voor SP1.  

> [!NOTE]   
>  Als u alle functies van de SQL Server 2008 R2, installeert u de serverfunctie Web Services (IIS) voordat u SQL Server 2008 R2 installeert.  

#### <a name="to-install-sql-server-2008-r2"></a>Voor het installeren van SQL Server 2008 R2
1.  Start het Installatiecentrum van SQL Server.  

2.  Klik in de SQL Server-installatie Center in het navigatiedeelvenster op **installatie**.  

3.  Klik in het detailvenster op **nieuwe installatie of functies toevoegen aan een bestaande installatie**.  

     SQL Server 2008 R2-installatiewizard wordt gestart.  

4.  Installeer SQL Server 2008 R2 met behulp van de volgende informatie, accepteer de standaardwaarden tenzij anders vermeld.  

  |**Op deze wizardpagina**|**Dit doet**|  
  |-|-|  
  |**Setup-Ondersteuningsregels**|Klik op **OK**.|  
  |**Productcode**|Klik op **Volgende**.|  
  |**Licentievoorwaarden**|Selecteer de **ik ga akkoord met de licentievoorwaarden** selectievakje en klik vervolgens op **volgende**.|  
  |**Setup-ondersteuningsbestanden**|Klik op **Installeren**.|  
  |**Setup-Ondersteuningsregels**|Zorg ervoor dat er geen kritieke resultaten bestaan voor de regels en klik vervolgens op **volgende**.|  
  |**Setup-rol**|Klik op **SQL Server Feature Installation**, en klik op **volgende**.|  
  |**Functies selecteren**|1.  Selecteer **Database Engine-Services** selectievakje.<br />2.  Selecteer **Reporting Services** selectievakje.<br />3.  Selecteer **zoeken in volledige tekst** selectievakje.<br />4.  Selecteer **beheerprogramma's - voltooien** selectievakje.<br />5.  Klik op **Volgende**.|  
  |**Installatieregels**|Klik op **Volgende**.|  
  |**De configuratie van exemplaar**|Klik op **Volgende**.|  
  |**Benodigde schijfruimte**|Klik op **Volgende**.|  
  |**Serverconfiguratie**|1.  Voor **SQL Server Agent**in **accountnaam**, type **MDT2013\SQLAgent**, en in **wachtwoord**, type  **P@ssw0rd**.<br />2.  Voor **SQL Server Database Engine**in **accountnaam**, type **MDT2013\SQLDBEngine**in **wachtwoord**, type  **P@ssw0rd** .<br />3.  Voor **SQL Server Reporting Services**in **accountnaam**, type **MDT2013\SQLReport**in **wachtwoord**, type  **P@ssw0rd** .<br />4.  Klik op **Volgende**.|  
  |**Configuratie van de Database-Engine**|Klik op **huidige gebruiker toevoegen**, en klik op **volgende**.|  
  |**Configuratie van Reporting Services**|Klik op **Volgende**.|  
  |**Foutrapportage**|Klik op **Volgende**.|  
  |**Configuratieregels voor installatie**|Klik op **Volgende**.|  
  |**Gereed voor installatie**|Klik op **Installeren**.|  
  |**Voltooien**|Klik op **Sluiten**.|  

5.  Sluit het Installatiecentrum van SQL Server.  

#### <a name="to-install-sql-server-2008-r2-sp1"></a>Voor het installeren van SQL Server 2008 R2 SP1
1.  In Windows Verkenner, Ga naar E:\Source$\SQL2008R2SP1 en dubbelklikt u op **SQLServer2008R2SP1-KB2528583-x64-ENU.exe**.  

     De **uitpakken van bestanden** in het dialoogvenster geeft het proces bestand uitpakken. Wanneer het proces voltooid is, wordt de SQL Server 2008 R2 Service Pack 1 Update installatiewizard gestart.  

2.  Installeer SQL Server 2008 R2 SP1 met behulp van de volgende informatie, accepteer de standaardwaarden tenzij anders vermeld.        

  |**Op deze wizardpagina**|**Dit doet**|  
  |-|-|  
  |**Update van SQL Server 2008 R2**|Klik op **Volgende**.|  
  |**Licentievoorwaarden**|Selecteer de **ik ga akkoord met de licentievoorwaarden** selectievakje en klik vervolgens op **volgende**.|  
  |**Functies selecteren**|Klik op **Volgende**.|  
  |**Controleer de bestanden In gebruik**|Klik op **Volgende**.|  
  |**Gereed om te werken**|Klik op **Update**.|  
  |**Voortgang van bijwerken**|Als de update wordt uitgevoerd en is voltooid, wordt de voortgang van de weergegeven op de wizardpagina.|  
  |**Voltooien**|Klik op **Sluiten**.|  

#### <a name="to-install-sql-server-2008-r2-sp1-cu6"></a>Voor het installeren van SQL Server 2008 R2 SP1 cu6 ondersteund
1.  In Windows Verkenner, Ga naar E:\Source$\SQL2008R2SP1CU6 en dubbelklikt u op **446622_intl_x64_zip.exe**.  

     De **Microsoft Extractor** dialoogvenster wordt weergegeven.  

2.  In de **Microsoft Extractor** in het dialoogvenster, klikt u op **doorgaan**.  

3.  In de **Microsoft Extractor** het dialoogvenster **Selecteer de map waar u wilt uitpakken van bestanden voor de**, type **E:\Source$\SQL2008R2SP1CU6**, en klik vervolgens op  **OK**.  

    > [!NOTE]   
    >  U kunt klikken op de knop met weglatingstekens (...) om te bladeren naar de map E:\Source$\SQL2008R2SP1CU6.  

     Het uitpakken worden weergegeven. Wanneer het proces voltooid is, wordt de voltooiingsstatus weergegeven.  

4.  In de **Microsoft Extractor** in het dialoogvenster, klikt u op **OK**.  

5.  In Windows Verkenner, Ga naar E:\Source$\SQL2008R2SP1CU6 en dubbelklikt u op **SQLServer2008R2-KB2679367-x64.exe**.  

     De **uitpakken van bestanden** in het dialoogvenster geeft het proces bestand uitpakken. Wanneer het proces voltooid is, wordt de SQL Server 2008 R2 Service Pack 1 cu6 ondersteund Update installatiewizard gestart.  

6.  Installeer SQL Server 2008 R2 SP1 cu6 ondersteund met de volgende gegevens, accepteer de standaardwaarden tenzij anders vermeld.  

  |**Op deze wizardpagina**|**Dit doet**|  
  |-|-|  
  |**Update van SQL Server 2008 R2**|Klik op **Volgende**.|  
  |**Licentievoorwaarden**|Selecteer de **ik ga akkoord met de licentievoorwaarden** selectievakje en klik vervolgens op **volgende**.|  
  |**Functies selecteren**|Klik op **Volgende**.|  
  |**Controleer de bestanden In gebruik**|Klik op **Volgende**.|  
  |**Gereed om te werken**|Klik op **Update**.|  
  |**Voortgang van bijwerken**|Als de update wordt uitgevoerd, wordt de voortgang van de weergegeven op de wizardpagina.|  
  |**Voltooien**|Klik op **Sluiten**.|  

  De **installeren van een Update van SQL Server 2008 R2** dialoogvenster wordt weergegeven waarin u de computer u voltooit de installatie opnieuw opstarten wordt gevraagd.  

7.  In de **een update van SQL Server 2008 R2 installeert** in het dialoogvenster, klikt u op **OK**.  

8.  Start de computer opnieuw op.  

9. Na de installatie van SQL Server 2008 R2 SP1 cu6 ondersteund, moet het buildnummer voor SQL Server 10.51.2811.0.  

    > [!TIP]    
    >  U kunt het buildnummer voor SQL Server controleren door het bekijken van de SQL Server-updates toegepast in de programma's en onderdelen in het Configuratiescherm item door te klikken op **geïnstalleerde updates weergeven**.  

###  <a name="AddSiteSecuritytoAdminGroup"></a>Stap 1-10: De siteserver toevoegen aan de beveiligingsgroep Administrators  
 Wanneer alle computers in hetzelfde forest, moet u handmatig het computeraccount van de siteserver toevoegen aan de lokale groep Administrators op elke computer. Deze stap hebt voltooid voordat u de computer configureert als een sitesysteem.  

 **De siteserver toevoegen aan de beveiligingsgroep Administrators**  

1.  Klik op **Start**, wijs **Systeembeheer**, en klik vervolgens op **Active Directory: gebruikers en Computers**.  

2.  Ga naar mdt2013.corp.woodgrovebank.com/Builtin in de consolestructuur van Active Directory: gebruikers en Computers.  

3.  In het voorbeeldvenster met de rechtermuisknop op **beheerders**, en klik vervolgens op **eigenschappen**.  

4.  In de **beheerders eigenschappen** in het dialoogvenster, klikt u op de **leden** tabblad en klik vervolgens op **toevoegen**.  

5.  In de **gebruikers, contactpersonen, Computers, of groepen selecteren** in het dialoogvenster, klikt u op **objecttypen**.  

6.  In de **objecttypen** het dialoogvenster **objecttypen**, selecteer **Computers**, en klik vervolgens op **OK**.  

7.  In de **gebruikers, contactpersonen, Computers, of groepen selecteren** het dialoogvenster **Geef de objectnamen op**, type **MDT-01-WDG**. Klik op **namen controleren**, en klik vervolgens op **OK**.  

8.  Sluit alle vensters geopend.  

###  <a name="InstallConfigManager"></a>Stap 1-11: Configuration Manager installeren  
 Wanneer de andere producten en technologieën hebt geïnstalleerd, installeert Configuration Manager. Voordat u dit doet, echter uitbreiden Active Directory-schema zodat computers de distributiepunten, service-locator verwijst en andere serverfuncties vinden kunnen. Nadat u de Configuration Manager hebt geïnstalleerd, kunt u ook het schema uitbreiden. Zie de sectie 'Breid het Active Directory-Schema' in de Documentatiebibliotheek van Configuration Manager, dat geïnstalleerd is met Configuration Manager voor meer informatie over het uitbreiden van het Active Directory-schema voor Configuration Manager.  

 Na het Active Directory-schema uitbreidt, installeert Configuration Manager. De configuratie van de MDT-01-WDG ondersteunt Configuration Manager voor dit voorbeeld. De configuratie van computers in het productienetwerk kan variëren. Zie voor meer informatie over de vereisten voor het installeren van Configuration Manager, [ondersteunde configuraties voor Configuration Manager](http://technet.microsoft.com/library/gg682077.aspx).  

#### <a name="to-install-configuration-manager"></a>Voor het installeren van Configuration Manager
1.  Start het welkomstscherm van Setup van System Center 2012 R2 Configuration Manager.  

2.  Klik op het welkomstscherm van Setup van System Center 2012 R2 Configuration Manager op de **installeren** koppeling.  

     De Wizard Microsoft System Center 2012 R2 Configuration Manager Setup wordt gestart.  

3.  Voltooi de Wizard Microsoft System Center 2012 R2 Configuration Manager Setup met behulp van de volgende informatie, accepteer de standaardwaarden tenzij anders vermeld.  

  |**Op deze wizardpagina**|**Dit doet**|  
  |-|-|  
  |**Voordat u begint**|Klik op **Volgende**.|  
  |**Aan de slag**|Klik op **Volgende**.|  
  |**Productcode**|In **Voer uw productcode van 25 tekens**, type ***productcode*** (waarbij *productcode* uw productcode is voor Configuration Manager).|  
  |**Licentievoorwaarden voor Microsoft-Software**|Selecteer de **ik aanvaard deze licentievoorwaarden** selectievakje en klik vervolgens op **volgende**.|  
  |**Vereiste licenties**|1.  In de **Microsoft SQL Server 2008 R2 Express** sectie, selecteer de **ik aanvaard deze licentievoorwaarden** selectievakje.<br />2.  In de **Microsoft SQL Server 2008 Native Client** sectie, selecteer de **ik aanvaard deze licentievoorwaarden** selectievakje.<br />3.  In de **Microsoft Silverlight 4** sectie, selecteer de **ik aanvaard deze licentievoorwaarden en automatische updates van Silverlight** selectievakje.<br />4.  Klik op **Volgende**.|  
  |**Vereiste onderdelen bijwerken**|In **downloaden en gebruiken van de meest recente updates. Updates worden opgeslagen op de volgende locatie**, type **E:\CMDownloads**, en klik vervolgens op **volgende**.|  
  |**Selectie van servertaal**|Klik op **Volgende**.|  
  |**Clienttaal**|Klik op **Volgende**.|  
  |**Site- en installatie-instellingen**|1.  In **sitecode**, type **NYC**.<br />2.  In **sitenaam**, type **New York City Site**.<br />3.  Klik op **Volgende**.|  
  |**Primaire Site-installatie**|1.  Klik op **de primaire site installeren als een zelfstandige site**.<br />2.  Klik op **Volgende**.<br />     De **Configuration Manager** dialoogvenster wordt weergegeven, waarin wordt bevestigd dat u wilt deze site installeren als een zelfstandige site.<br />3.  In de **Configuration Manager** in het dialoogvenster, klikt u op **Ja**.|  
  |**Database-informatie**|Klik op **Volgende**.|  
  |**SMS-Providerinstellingen**|Klik op **Volgende**.|  
  |**Communicatie-instellingen voor clientcomputer**|Klik op **communicatiemethode configureren voor elke sitesysteemrol**, en klik vervolgens op **volgende**.|  
  |**Sitesysteemrollen**|Klik op **Volgende**.|  
  |**Configuratie voor programma voor kwaliteitsverbetering**|1.  Selecteer de juiste deelname aan het programma voor kwaliteitsverbetering voor uw organisatie.<br />2.  Klik op **Volgende**.|  
  |**Samenvatting van instellingen**|Klik op **Volgende**.|  
  |**Controle van vereisten**|Klik op **installatie begint**.|  
  |**Installeren**|1.  Het installatieproces bewaken totdat deze voltooid is.<br />2.  Klik op **Sluiten**.|  

4.  Sluit alle geopende vensters en dialoogvensters.  

 Wanneer de wizard voltooid is, wordt Configuration Manager is geïnstalleerd.  

###  <a name="ConfigureNetworkAccessAccount"></a>Stap 1-12: Het netwerktoegangsaccount configureren  
 De Configuration Manager-client moet een account om uw referenties bij het openen van de Configuration Manager-distributiepunten, implementatieshares MDT en gedeelde mappen. Dit account heet de *netwerktoegangsaccount*. Het account CMNetAccess is eerder in het proces om te gebruiken als het account toegang tot het netwerk gemaakt.  

#### <a name="to-configure-the-network-access-account"></a>Het netwerktoegangsaccount configureren  
1.  Klik op **Start**, wijs **alle programma's**, en wijs vervolgens **Microsoft System Center 2012**. Wijs **Configuration Manager**, en klik vervolgens op **Configuration Manager-Console**.  

2.  Klik in de Configuration Manager-console in het navigatievenster op **beheer**.  

3.  Ga naar overzicht/Configuration/Sites Site in de werkruimte beheer.  

4.  Klik in het voorbeeldvenster op **NYC - New York City Site**.  

5.  Klik op het lint op **instellingen**, klikt u op **Siteonderdelen configureren**, en klik vervolgens op **softwaredistributie**.  

6.  In de **eigenschappen van Softwaredistributieonderdelen** in het dialoogvenster, klikt u op de **netwerktoegangsaccount** tabblad.  

7.  In **netwerktoegangsaccount**, klikt u op **de account opgeven die toegang netwerklocaties tot**, klikt u op **ingesteld**, en klik vervolgens op **nieuwe Account**.  

     De **Windows-gebruikersaccount** dialoogvenster wordt weergegeven.  

8.  Voltooi de **Windows-gebruikersaccount** in het dialoogvenster met de volgende informatie en klik vervolgens op **OK**.    

 |**Voor deze**|**Dit doet**|  
 |-|-|  
 |**Gebruikersnaam**|Type **MDT2013\CMNetAccess**.|  
 |**Wachtwoord**|Type  **P@ssw0rd** .|  
 |**Wachtwoord bevestigen**|Type  **P@ssw0rd** .|  

9. In de **eigenschappen van Softwaredistributieonderdelen** in het dialoogvenster, klikt u op **OK**.  

10. Sluit alle vensters geopend.  

###  <a name="ConfigurationManagerSiteBoundaries"></a>Stap 1-13: De Configuration Manager-Sitegrenzen en Grensgroepen configureren  
 De Configuration Manager-client moet weten de grenzen van de site. Tenzij de grenzen van de site zijn opgegeven, de client wordt verondersteld dat de computer met Configuration Manager op een externe locatie. Toevoegen aan dat de sitegrens van een op basis van het IP-subnet dat MDT-01-WDG, WDG-REF-01 en WDG-CLI-01-gebruik. De sitegrens vervolgens toevoegen aan een sitegrensgroep.  

#### <a name="to-create-a-configuration-manager-site-boundary"></a>De sitegrens van een Configuration Manager-maken
1.  Klik op **Start**, wijs **alle programma's**, en wijs vervolgens **Microsoft System Center 2012**. Wijs **Configuration Manager**, en klik vervolgens op **Configuration Manager-Console**.  

2.  Klik in de Configuration Manager-console in het navigatievenster op **beheer**.  

3.  Ga naar overzicht/hiërarchie Configuration/grenzen in de werkruimte beheer.  

4.  Klik op het lint op **grens maken**.  

     De **grens maken** dialoogvenster wordt geopend.  

5.  Voltooi de **grens maken** in het dialoogvenster met de volgende informatie en klik vervolgens op **OK**.  

    > [!NOTE]   
    >  Voor dit voorbeeld wordt de sitegrens opgegeven met netwerkadres. U kunt echter ook opgeven met behulp van een AD DS sitegrenzen site-naam of een IP-adresbereik.  

   |**Voor deze**|**Dit doet**|  
   |-|-|  
   |**Beschrijving**|Type **IP-Subnetgrens**.|  
   |**Type**|Selecteer **IP-subnet**.|  
   |**Netwerk**|Type ***network_address*** (waarbij *network_address* is het netwerkadres van het subnet waarop de computers zijn geïnstalleerd).|  
   |**Subnetmasker**|Type ***subnet_mask*** (waarbij *subnet_mask* is het subnetmasker van het subnet waarop de computers zijn geïnstalleerd).|  

#### <a name="to-add-the-configuration-manager-site-boundary-to-a-site-boundary-group"></a>De Configuration Manager-sitegrens toevoegen aan een sitegrensgroep  
1.  Klik in de Configuration Manager-console in het navigatievenster op **beheer**.  

2.  Ga naar overzicht/hiërarchie Configuration/Grensgroepen in de werkruimte beheer.  

3.  Klik op het lint op **Grensgroep maken**.  

     De **Grensgroep maken** dialoogvenster wordt geopend.  

4.  Voltooi de **algemene** tabblad van de **Grensgroep maken** met de volgende gegevens in het dialoogvenster.

  |**Voor deze**|**Dit doet**|  
  |-|-|  
  |**Naam**|Type **New York City Grensgroep**.|  
  |**Beschrijving**|Type **dit is de grensgroep voor de grenzen van de site op de site New York City**.|  
  |Grenzen|1.  Klik op **Toevoegen**.<br />     De **toevoegen grenzen** dialoogvenster wordt weergegeven.<br />2.  In de **toevoegen grenzen** dialoogvenster, ***site_boundary*** (waarbij *site_boundary* grens van de site's die u eerder in het proces gemaakt), en klik vervolgens op **OK**.<br />     De sitegrens wordt weergegeven in de lijst met grenzen.|  

5.  Voltooi de **verwijzingen** tabblad van de **Grensgroep maken** in het dialoogvenster met de volgende informatie en klik vervolgens op **OK**.  

  |**Voor deze**|**Dit doet**|  
  |-|-|  
  |**Sitetoewijzing**|Selecteer de **deze grensgroep gebruiken voor sitetoewijzing** selectievakje.|  
  |**Locatie van inhoud**|1.  Klik op **Toevoegen**.<br />     De **Sitesystemen toevoegen** dialoogvenster wordt weergegeven.<br />2.  In de **Sitesystemen toevoegen** dialoogvenster,  **\\\WDG-MDT-01.mdt2013.corp.woodgrovebank.com**, en klik vervolgens op **OK**.<br />     De sitesysteemserver wordt weergegeven in de lijst met sitesysteemservers.|  

6.  Sluit alle vensters geopend.  

###  <a name="ConfigurePublishingSiteInfo"></a>Stap 1-14: Het publiceren van Site-informatie in AD DS en DNS configureren  
 Configuration Manager-client moet de verschillende serverrollen van de Configuration Manager-vinden. De eigenschappen van de site de site om informatie te publiceren in AD DS en DNS-wijzigen.  

 **Het publiceren van site-informatie in AD DS en in DNS configureren**  

1.  Klik op **Start**, wijs **alle programma's**, en wijs vervolgens **Microsoft System Center 2012**. Wijs **Configuration Manager**, en klik vervolgens op **Configuration Manager-Console**.  

2.  Klik in de Configuration Manager-console in het navigatievenster op **beheer**.  

3.  Ga naar overzicht/Configuration/Sites Site in de werkruimte beheer.  

4.  Klik in het voorbeeldvenster op **NYC - New York City Site**.  

5.  Klik op het lint op **eigenschappen**.  

6.  In de **New York City Site-eigenschappen** in het dialoogvenster op de **Publishing** tabblad, Controleer de **mdt2013.corp.woodgrovebank.com** Active Directory-forest wordt weergegeven, en Klik vervolgens op **annuleren**.  

7.  Sluit alle vensters geopend.  

##  <a name="PrepareMDTEnvironment"></a>Stap 2: De MDT-omgeving voorbereiden  
 De eerste stap in het implementatieproces is de MDT-omgeving voorbereiden. Als deze stap voltooid is, kunt u de referentiecomputer maken en implementeren van een vastgelegde installatiekopie van het naar de doelcomputer (WDG-CLI-01) met Configuration Manager-integratie met MDT.  

 De MDT-omgeving door voorbereiden:  

-   MDT installeren zoals is beschreven in [stap 2-1: MDT installeren](#InstallMDT)  

-   Integratie van Configuration Manager-console inschakelen door het uitvoeren van het script Configuration Manager-integratie configureren zoals beschreven in [stap 2-2: Integratie van Configuration Manager-Console inschakelen](#EnableConfigManagerConsole)  

###  <a name="InstallMDT"></a>Stap 2-1: MDT installeren  
 Voor installatie MDT, voert u de volgende stappen uit:  

1.  In Windows Verkenner, Ga naar E:\Source$\MDT_2013.  

2.  Dubbelklik op **MicrosoftDeploymentToolkit2013_x64.msi** (voor 64-bits besturingssystemen) of **MicrosoftDeploymentToolkit2013_x86.msi** (voor 32-bits besturingssystemen), en klik vervolgens op **Installeren**.  

     De Microsoft Deployment Toolkit 2013-installatiewizard wordt gestart.  

3.  Voltooi de Microsoft Deployment Toolkit 2013 Setup Wizard met behulp van de informatie in de volgende tabel.  Accepteer de standaardwaarden tenzij anders vermeld.  

  |**Op deze wizardpagina**|**Dit doet**|  
  |-|-|  
  |**Welkom bij de Microsoft Deployment Toolkit 2013-installatiewizard**|Klik op **Volgende**.|  
  |**Gebruiksrechtovereenkomst**|Klik op **ik ga akkoord met de voorwaarden in deze gebruiksrechtovereenkomst**, en klik vervolgens op **volgende**.|  
  |**Aangepaste installatie**|Klik op **Volgende**.|  
  |**Gereed voor installatie van Microsoft Deployment Toolkit 2013**|Klik op **Installeren**.|  
  |**Microsoft Deployment Toolkit 2013 installeren**|De voortgang voor het installeren van MDT wordt weergegeven.|  
  |**De Wizard Setup van Microsoft Deployment Toolkit 2013 voltooien**|Klik op **Voltooien**.|  

 De Wizard Setup van Microsoft Deployment Toolkit 2013 is voltooid en MDT is geïnstalleerd op de MDT-01-WDG.  

###  <a name="EnableConfigManagerConsole"></a>Stap 2-2: Integratie van Configuration Manager-Console inschakelen  
 Voordat u de Configuration Manager-integratiefuncties van MDT gebruiken kunt, moet u het script Configuration Manager-integratie configureren uitvoeren. Dit script kopieert de juiste integratie-bestanden naar de map waarin u Configuration Manager is geïnstalleerd. Het script voegt ook Windows Management Instrumentation (WMI)-klassen voor de nieuwe aangepaste acties in MDT. De klassen worden toegevoegd door het compileren van een nieuw Managed Object Format (MOF) bestand met de nieuwe klassedefinities.  

 **Integratie van Configuration Manager-console inschakelen**  

> [!NOTE]   
>  Zorg ervoor dat de Configuration Manager-console is afgesloten tijdens het uitvoeren van deze stappen.  

1.  Klik op **Start**, en wijs vervolgens **alle programma's**. Wijs **Microsoft Deployment Toolkit**, en klik vervolgens op **Configuration Manager-integratie configureren**.  

     De Wizard Configuration Manager-integratie configureren wordt gestart.  

2.  Voltooi de Configuration Manager-integratie Wizard configureren met behulp van de informatie in de volgende tabel. Accepteer de standaardwaarden tenzij anders vermeld.  

  |**Op deze wizardpagina**|**Dit doet**|  
  |-|-|  
  |**Opties**|1.  Controleer de **installeren van de MDT-console-uitbreidingen voor System Center 2012 R2 Configuration Manager** selectievakje is ingeschakeld.<br />2.  Controleer de **de MDT-takenreeksacties toevoegen aan een System Center 2012 R2 Configuration Manager-server** selectievakje is ingeschakeld.<br />3.  In **siteservernaam**, Controleer of de waarde **WDG-MDT-01.mdt2013.corp.woodgrovebank.com**.<br />4.  In **sitecode**, Controleer of de waarde **NYC**.<br />5.  Klik op **Volgende**.|  
  |**Bevestiging**|Klik op **Voltooien**.|  

 De Wizard Configuration Manager-integratie is voltooid en MDT is geïntegreerd met Configuration Manager.  

## <a name="step-3-create-and-configure-a-task-sequence-to-create-a-reference-computer"></a>Stap 3: Maken en een Takenreeks voor het maken van een referentiecomputer configureren  
 Wanneer u de MDT-omgeving hebt voorbereid, maakt u de referentiecomputer. De referentiecomputer is de sjabloon voor het implementeren van installatiekopieën van het nieuwe op de doelcomputers. Configureer deze computer (WDG-REF-01) precies zoals u de doelcomputers configureert. U wordt vervolgens een installatiekopie van de referentiecomputer en de installatiekopie implementeren op de doelcomputers.  

 Maken van de referentiecomputer WDG-REF-01, door:  

-   Maken van een takenreeks MDT om Windows 8.1 implementeren op de referentiecomputer, zoals beschreven in [stap 3-1: Een Takenreeks MDT maken voor het implementeren van de referentiecomputer](#CreateMDTTaskSequence)  

-   Als u de distributiepunten voor de nieuwe pakketten en installatiekopieën van de MDT Wizard Takenreeks maken maakt zoals beschreven in [stap 3-2: Selecteer de distributiepunten voor de nieuwe pakketten en installatiekopieën](#SelectDistroPoints)  

-   De benodigde apparaatstuurprogramma's toevoegen voor een nieuw station pakket en de juiste opstartinstallatiekopieën zoals beschreven in [stap 3-3: De benodigde apparaatstuurprogramma's toevoegen](#AddDeviceDrivers)  

-   Schakel de bewaking van het implementatieproces van MDT, zoals beschreven in [stap 3 en 4: MDT-implementatie in te schakelen procesbewaking](#EnableMDTDeployProcess)  

-   Configureren van de MDT-configuratiebestanden voor de referentiecomputer, in het bijzonder het CustomSettings.ini-bestand, zoals beschreven in [stap 3-5: Het aanpassen van de MDT-configuratiebestanden voor de referentiecomputer](#CustomizeMDTConfigFiles)  

-   Bijwerken van de Configuration Manager-distributiepunten voor het pakket bestanden met aangepaste instellingen, zoals beschreven in [stap 3-6: De distributiepunten voor het pakket met aangepaste instellingen voor bestanden bijwerken](#UpdateDistroPoint)  

-   De takenreeks voor de referentiecomputer aanpassen zoals beschreven in [stap 3-7: De Takenreeks voor de referentiecomputer aanpassen](#CustomizeTaskSequence)  

###  <a name="CreateMDTTaskSequence"></a>Stap 3-1: Een Takenreeks MDT maken voor het implementeren van de referentiecomputer  
 Gebruik de MDT Wizard Takenreeks maken in de Configuration Manager-console voor het maken van takenreeksen in Configuration Manager waarmee zijn geïntegreerd met MDT. MDT bevat de sjabloon standaard Clienttakenreeks die u gebruiken kunt voor het implementeren van de referentiecomputer.  

 De Wizard maken Takenreeks MDT vervangt door de pakketten en installatiekopieën die zijn geselecteerd voor de tijdelijke aanduidingen in de reeks taaksjablonen. Na het voltooien van de wizard verwijst nieuwe takenreeks de juiste pakketten en afbeeldingen.  

> [!NOTE]   
>  Gebruik altijd de MDT Wizard Takenreeks maken voor het maken van takenreeksen op basis van de MDT taak reeks sjablonen. Hoewel u de taak reeks sjablonen handmatig importeren kunt, niet wordt aangeraden dit proces.  

#### <a name="to-create-a-task-sequence-for-deploying-the-reference-computer"></a>Maken van een takenreeks voor het implementeren van de referentiecomputer  

1.  Klik op **Start**, wijs **alle programma's**, en wijs vervolgens **Microsoft System Center 2012**. Wijs **Configuration Manager**, en klik vervolgens op **Configuration Manager-Console**.  

2.  Klik in de Configuration Manager-console in het navigatievenster op **softwarebibliotheek**.  

3.  Ga in de werkruimte softwarebibliotheek naar overzicht/Operating Systems/Takenreeksen.  

4.  Klik op het lint op de **Start** tabblad, in de **Takenreeksen** groep, klikt u op **Takenreeks MDT maken**.  

     De MDT Wizard Takenreeks maken wordt gestart.  

5.  Voltooi de MDT Wizard Takenreeks maken met de informatie in de volgende tabel. Accepteer de standaardwaarden tenzij anders vermeld.  

  |**Op deze wizardpagina**|**Dit doet**|  
  |-|-|  
  |**Sjabloon kiezen**|Selecteer **Clienttakenreeks**, en klik vervolgens op **volgende**.|  
  |**Sjabloon kiezen: Algemeen**|1.  In **takenreeksnaam**, type **Windows 8.1 verwijzing implementatie**.<br />2.  In **Task sequence opmerkingen**, type **Takenreeks voor het Windows 8.1 implementeren op de referentiecomputer (WDG-REF-01)**, en klik vervolgens op **volgende**.|  
  |**Sjabloon kiezen: Meer informatie**|1.  Klik op **lid van een werkgroep**.<br />2.  In **werkgroep**, type **werkgroep**.<br />3.  In **gebruikersnaam**, type **Woodgrove Bank werknemer**.<br />4.  In **organisatienaam**, type **Woodgrove Bank**.<br />5.  In **productcode**, type ***productcode*** (waarbij *productcode* is de productcode voor Windows 8.1).<br />6.  Klik op **Volgende**.|  
  |**Sjabloon kiezen: Instellingen vastleggen**|<ol><li>Klik op **deze takenreeks kan worden gebruikt voor het vastleggen en image**.</li><li>In **vastleggen bestemming**, type  **\\\WDG-MDT-01\Capture$\WDG-REF-01.wim**.</li><li>In **account voor het vastleggen**, klikt u op **ingesteld**.</li><li>Voltooi de **Windows-gebruikersaccount** dialoogvenster door de volgende stappen uit te voeren:<br /><br /> <ol><li>In **gebruikersnaam**, type **MDT2013\Administrator**.</li><li>In **wachtwoord** en **wachtwoord bevestigen**, type  **P@ssw0rd** .</li></ol></li><li>Klik op **OK**.</li><li>Klik op **Volgende**.</li></ol>|  
  |**Opstartinstallatiekopie**|1.  Klik op **maken van een nieuwe opstartinstallatiekopie-pakket**.<br />2.  In **pakketbronmap worden gemaakt**, type  **\\\WDG-MDT-01\Packages$\WINPE_Custom**, en klik vervolgens op **volgende**.|  
  |**Opstartinstallatiekopie: Algemene instellingen**|1.  In **naam**, type **Windows PE aangepaste**.<br />2.  In **versie**, type **1,00**.<br />3.  In **opmerkingen**, type **aangepaste versie van Windows PE moet worden gebruikt in de implementatie van de referentie-en**, en klik vervolgens op **volgende**.|  
  |**Opstartinstallatiekopie: Opties**|Onder **Platform**, klikt u op **x64**, en klik vervolgens op **volgende**.|  
  |**Opstartinstallatiekopie: Onderdelen**|Klik op **Volgende**.|  
  |**Opstartinstallatiekopie: Aanpassing**|Klik op **Volgende**.|  
  |**MDT-pakket**|1.  Klik op **een nieuw pakket van Microsoft Deployment Toolkit-bestanden maken**.<br />2.  In **pakketbronmap worden gemaakt**, type  **\\\WDG-MDT-01\Packages$\MDT_Files**, en klik vervolgens op **volgende**.|  
  |**MDT pakket: MDT-Details**|1.  In **naam**, type **MDT bestanden**.<br />2.  In **versie**, type **1,00**.<br />3.  In **opmerkingen**, type **biedt toegang tot MDT bestanden tijdens het implementatieproces van de Configuration Manager**, en klik vervolgens op **volgende**.|  
  |**Installatiekopie van het besturingssysteem**|1.  Klik op **Maak een nieuw besturingssysteem installatiepakket**.<br />2.  In **OS-installatielocatie map**, type  **\\\WDG-MDT-01\Source$\Windows_7**.<br />3.  In **pakketbronmap worden gemaakt**, type  **\\\WDG-MDT-01\Packages$\Windows_7**, en klik vervolgens op **volgende**.|  
  |**Installatiekopie van het besturingssysteem: Details van de afbeelding**|1.  In **naam**, type **Windows 8.1**.<br />2.  In **versie**, type **1,00**.<br />3.  In **opmerkingen**, type **Windows 8.1-pakket gebruikt om te implementeren om referentiecomputers te**, en klik vervolgens op **volgende**.|  
  |**Methode-implementatie**|Klik op **Volgende**.|  
  |**Clientpakket**|Klik op **maken van een nieuwe ConfigMgr-clientpakket**, en klik vervolgens op **volgende**.|  
  |**USMT-pakket**|1.  Klik op **een nieuw USMT-pakket maken**.<br />2.  In **pakketbronmap worden gemaakt**, type  **\\\WDG-MDT-01\Packages$\USMT**, en klik vervolgens op **volgende**.|  
  |**USMT-pakket: USMT-Details**|1.  In **naam**, type **USMT**.<br />2.  In **versie**, type **1,00**.<br />3.  In **opmerkingen**, type **USMT-bestanden gebruikt voor het vastleggen en herstellen van informatie over migratie van gebruikersstatus**, en klik vervolgens op **volgende**.|  
  |**Instellingen pakket**|1.  Klik op **Maak een nieuw pakket van de instellingen**.<br />2.  In **pakketbronmap worden gemaakt**, type  **\\\WDG-MDT-01\Packages$\CustomSettings_Reference**, en klik vervolgens op **volgende**.|  
  |**Instellingen voor pakket: Details van instellingen**|1.  In **naam**, type **aangepaste instellingen referentiecomputer MDT**.<br />2.  In **versie**, type **1,00**.<br />3.  In **opmerkingen**, type **configuratie-instellingen voor de MDT-implementatieproces (zoals CustomSettings.ini) voor de referentiecomputer**, en klik vervolgens op **volgende**.|  
  |**Sysprep-pakket**|Klik op **Volgende**.|  
  |**Samenvatting**|1.  Lees de informatie in de **Details** vak die die u hebt opgegeven tijdens het uitvoeren van de vorige wizardpagina's.<br />2.  Klik op **Volgende**.|  
  |**Voortgang**|De voortgang voor het maken van de takenreeks wordt weergegeven.|  
  |**Bevestiging**|Klik op **Voltooien**.|  

   De nieuwe takenreeks weergegeven in het voorbeeldvenster.  

###  <a name="SelectDistroPoints"></a>Stap 3-2: Selecteer de distributiepunten voor de nieuwe pakketten en installatiekopieën  
 De MDT Wizard Takenreeks maken maakt een aantal pakketten en afbeeldingen. Nadat deze pakketten en afbeeldingen worden gemaakt, selecteert u de distributiepunten op waarop de pakketten en afbeeldingen, gekopieerd en beschikbaar zijn voor de doelcomputers worden moeten.  

> [!NOTE]   
>  In dit voorbeeld is er slechts één distributiepunt (WDG-MDT-01). De meeste productienetwerken hebben echter meerdere distributiepunten. Wanneer u deze stap uitvoert in een productieomgeving, selecteer de juiste distributiepunten voor het netwerk.  

#### <a name="to-select-the-distribution-points-for-software-distribution-packages"></a>Selecteer de distributiepunten voor softwaredistributiepakketten  
1.  Klik op **Start**, wijs **alle programma's**, en wijs vervolgens **Microsoft System Center 2012**. Wijs **Configuration Manager**, en klik vervolgens op **Configuration Manager-Console**.  

2.  Klik in de Configuration Manager-console in het navigatievenster op **softwarebibliotheek**.  

3.  Ga in de werkruimte softwarebibliotheek naar overzicht/Operating Systems/Takenreeksen.  

4.  Selecteer in het voorbeeldvenster **Windows 8.1 verwijzing implementatie**.  

5.  Klik op het lint op de **Start** tabblad, in de **implementatie** groep, klikt u op **inhoud distribueren**.  

     De Wizard inhoud distribueren wordt gestart.  

6.  Voltooi de Wizard inhoud distribueren met behulp van de informatie in de volgende tabel. Accepteer de standaardwaarden tenzij anders vermeld.  

  |**Op deze wizardpagina**|**Dit doet**|  
  |-|-|  
  |**Algemeen**|Klik op **Volgende**.|  
  |**Algemeen: Inhoud**|Klik op **Volgende**.|  
  |**Algemeen: Doel van inhoud**|1.  Klik op **toevoegen**, en klik vervolgens op **distributiepunt**.<br />     De **distributiepunten toevoegen** dialoogvenster wordt weergegeven.<br />2.  In de **distributiepunten toevoegen** dialoogvenster, **WDG-MDT-01.mdt2013.corp.woodgrovebank.com**, en klik vervolgens op **OK**.<br />     WDG-MDT-01.corp.woodgrovebank.com wordt weergegeven in de **doel van inhoud** lijst.<br />3.  Klik op **Volgende**.|  
  |**Samenvatting**|1.  Lees de informatie in de **Details** vak die die u hebt opgegeven tijdens het uitvoeren van de vorige wizardpagina's.<br />2.  Klik op **Volgende**.|  
  |**Voortgang**|De voortgang voor het distribueren van de software wordt weergegeven.|  
  |**Voltooiing**|Klik op **Sluiten**.|  

7.  Sluit alle geopende vensters en dialoogvensters.  

###  <a name="AddDeviceDrivers"></a>Stap 3-3: De benodigde apparaatstuurprogramma's toevoegen  
 Wanneer de takenreeks MDT is gemaakt, toevoegen eventuele apparaatstuurprogramma's vereist zijn voor de referentiecomputer (WDG-REF-01) aan de Windows PE-installatiekopie en op de installatiekopie van Windows 8.1. De apparaatstuurprogramma's toevoegen in het knooppunt stuurprogramma's in de Configuration Manager-console. Maak een pakket met de apparaatstuurprogramma's en de stuurprogramma's invoeren in de aangepaste Windows PE-installatiekopie die eerder in het proces hebt gemaakt.  

 Nadat het maken van het pakket dat de stuurprogramma's bevat, selecteert u de verdeling punt waarop het pakket wordt geïmplementeerd.  

#### <a name="to-add-the-necessary-device-drivers"></a>De benodigde apparaatstuurprogramma's toevoegen
1.  Klik op **Start**, wijs **alle programma's**, en wijs vervolgens **Microsoft System Center 2012**. Wijs **Configuration Manager**, en klik vervolgens op **Configuration Manager-Console**.  

2.  Klik in de Configuration Manager-console in het navigatievenster op **softwarebibliotheek**.  

3.  Ga naar overzicht/Operating Systems/Drivers in de werkruimte softwarebibliotheek.  

4.  Klik op het lint op de **Start** tabblad, in de **maken** groep, klikt u op **stuurprogramma importeren**.  

     De Wizard Nieuw stuurprogramma importeren wordt gestart.  

5.  Voltooi de Wizard Nieuw stuurprogramma importeren met behulp van de informatie in de volgende tabel.  Accepteer de standaardwaarden tenzij anders vermeld.  

  |**Op deze wizardpagina**|**Dit doet**|  
  |-|-|  
  |**Stuurprogramma vinden**|In **bronmap**, type  **\\\WDG-MDT-01\Source$\Drivers**, en klik vervolgens op **volgende**.|  
  |**Stuurprogramma vinden: Details van stuurprogramma**|Klik op **Volgende**.|  
  |**Stuurprogramma vinden: Stuurprogramma's toevoegen aan pakket**|<ol><li>Klik op **nieuw pakket**.</li><li>Voltooi de **nieuw stuurprogrammapakket** dialoogvenster door de volgende stappen uit te voeren:<br /><br /> <ol><li>In **naam**, type ***device_driver_name*** pakket (waarbij *device_driver_name* is een beschrijvende naam voor de apparaatstuurprogramma's).</li><li>In **Opmerking**, type **apparaatstuurprogramma's die nodig voor de referentie- en doelcomputers computers zijn**.</li></ol></li><li>In **stuurprogramma pakketbron**, type  **\\\WDG-MDT-01\Packages$\Drivers**, en klik vervolgens op **OK**.</li><li>Klik op **Volgende**.</li></ol>|  
  |**Stuurprogramma vinden: Stuurprogramma aan installatiekopieën toevoegen**|1.  Selecteer in de lijst met afbeeldingen, de **Windows PE aangepaste** selectievakje.<br />2.  Selecteer de **distributiepunten bijwerken na voltooiing** selectievakje en klik vervolgens op **volgende**.|  
  |**Samenvatting**|1.  Lees de informatie in de **Details** vak die die u hebt opgegeven tijdens het uitvoeren van de vorige wizardpagina's.<br />2.  Klik op **Volgende**.|  
  |**Voortgang**|De voortgang voor het importeren van apparaatstuurprogramma's wordt weergegeven.|  
  |**Bevestiging**|Klik op **Sluiten**.|  

#### <a name="to-select-the-distribution-points-for-the-driver-package"></a>De distributiepunten voor het stuurprogrammapakket selecteren
1.  Klik op **Start**, wijs **alle programma's**, en wijs vervolgens **Microsoft System Center 2012**. Wijs **Configuration Manager**, en klik vervolgens op **Configuration Manager-Console**.  

2.  Klik in de Configuration Manager-console in het navigatievenster op **softwarebibliotheek**.  

3.  Ga in de werkruimte softwarebibliotheek naar overzicht/Operating Systems/stuurprogrammapakketten.  

4.  Klik in het voorbeeldvenster op ***device_driver_name*** **pakket** (waarbij *device_driver_name* is een beschrijvende naam voor de apparaatstuurprogramma's).  

5.  Klik op het lint op de **Start** tabblad, in de **implementatie** groep, klikt u op **inhoud distribueren**.  

     De Wizard inhoud distribueren wordt gestart.  

6.  Voltooi de Wizard inhoud distribueren met behulp van de volgende informatie. Accepteer de standaardwaarden tenzij anders vermeld.  

  |**Op deze wizardpagina**|**Dit doet**|  
  |-|-|  
  |**Algemeen**|Klik op **Volgende**.|  
  |**Algemeen: Inhoud**|Klik op **Volgende**.|  
  |**Algemeen: Doel van inhoud**|1.  Klik op **toevoegen**, en klik vervolgens op **distributiepunt**.<br />     De **distributiepunten toevoegen** dialoogvenster wordt weergegeven.<br />2.  In de **distributiepunten toevoegen** dialoogvenster,  **\\\WDG-MDT-01.mdt2013.corp.woodgrovebank.com**, en klik vervolgens op **OK**.<br />     \\\WDGMDT01.mdt2013.corp.woodgrovebank.com wordt weergegeven in de **doel van inhoud** lijst.<br />3.  Klik op **Volgende**.|  
  |**Samenvatting**|1.  Lees de informatie in de **Details** vak die die u hebt opgegeven tijdens het uitvoeren van de vorige wizardpagina's.<br />2.  Klik op **Volgende**.|  
  |**Voortgang**|De voortgang voor het distribueren van de software wordt weergegeven.|  
  |**Voltooiing**|Klik op **Sluiten**.|  

7.  Sluit alle geopende vensters en dialoogvensters.  

###  <a name="EnableMDTDeployProcess"></a>Stap 3 en 4: MDT-implementatie in te schakelen procesbewaking  
 Vóór de implementatie van de referentiecomputer (WDG-REF-01) met opstartbare media voor de takenreeks MDT-controle van het implementatieproces ZTI inschakelen. U inschakelen bewaking op de **bewaking** tabblad van de implementatieshare **eigenschappen** in het dialoogvenster. Later in het proces wordt u het implementatieproces van ZTI met behulp van de implementatie-Workbench controleren of de **Get-MDTMonitorData** cmdlet.  

 **MDT bewaking van het implementatieproces ZTI wilt inschakelen**  

1.  Klik op **Start**, en wijs vervolgens **alle programma's**. Wijs **Microsoft Deployment Toolkit**, en klik vervolgens op **implementatie-Workbench**.  

2.  Ga naar de implementatie Workbench/Implementatieshares in de consolestructuur van de implementatie-Workbench.  

3.  Klik in het deelvenster Acties op **nieuwe Implementatieshares**.  

     De Wizard Nieuwe Deployment Share wordt gestart.  

4.  De implementatie van Wizard Nieuwe Share met de volgende gegevens voltooien

   |**Op deze wizardpagina**|**Dit doet**|  
   |-|-|  
   |**Op deze wizardpagina**|**Dit doet**|  
   |**Pad**|In **implementatie sharepad**, type **C:\DeploymentShare$**, en klik vervolgens op **volgende**.|  
   |**Delen**|Klik op **Volgende**.|  
   |**Beschrijvende naam**|Klik op **Volgende**.|  
   |**Opties**|Klik op **Volgende**.|  
   |**Samenvatting**|Klik op **Volgende**.|  
   |**Voortgang**|De voortgang voor het maken van de implementatieshare wordt weergegeven.|  
   |**Bevestiging**|Klik op **Voltooien**.|  

  De Wizard Nieuw implementatietype is voltooid en de nieuwe implementatieshare: MDT Deployment Share (C:\DeploymentShare$)—appears in het detaildeelvenster.  


5.  Klik in het detailvenster op **MDT-Implementatieshare (C:\DeploymentShare$)**.  

6.  Klik in het deelvenster Acties op **eigenschappen**.  

     De **eigenschappen van de MDT-Implementatieshare (C:\DeploymentShare$)** dialoogvenster wordt geopend.  

7.  In de **eigenschappen MDT Deployment Share (C:\DeploymentShare$)** in het dialoogvenster op de **bewaking** tabblad de **Schakel bewaking voor deze implementatieshare** selectievakje , en klik vervolgens op **toepassen**.  

8.  In de **eigenschappen van de MDT-Implementatieshare (C:\DeploymentShare$)** in het dialoogvenster op de **regels** tabblad, zoals u ziet de **EventService** eigenschap is toegevoegd aan de CustomSettings.ini-bestand en klik vervolgens op **OK**.  

  De **EventService** eigenschap is als volgt:  

    ```  
    EventService=http://WDG-MDT-01:9800  
    ```  

9. Sluit alle geopende vensters en dialoogvensters.  

###  <a name="CustomizeMDTConfigFiles"></a>Stap 3-5: Het aanpassen van de MDT-configuratiebestanden voor de referentiecomputer  
 Wanneer de takenreeks MDT is gemaakt, aanpassen van de MDT-configuratiebestanden die voorzien in de configuratie-instellingen voor Windows 8.1 implementeren met de doelcomputer. In het bijzonder het CustomSettings.ini-bestand aanpassen.  

 Wanneer het bestand CustomSettings.ini aanpassing is voltooid, moet u de bijgewerkte bestanden opslaan voor de bronmap voor het aangepaste instellingen referentiecomputer MDT pakket eerder in het proces (E:\Packages$\CustomSettings_Reference) gemaakt. Voeg vervolgens de **DoCapture** en **EventService** eigenschappen en bijbehorende waarden aan het CustomSettings.ini-bestand zodat het implementatieproces MDT legt een installatiekopie van de computer verwijzing (vast WDG-REF-01) na de implementatie van Windows 8.1.  

#### <a name="to-customize-the-mdt-configuration-files-for-the-reference-computer"></a>Voor het aanpassen van de MDT-configuratiebestanden voor de referentiecomputer

1.  In Windows Verkenner, Ga naar E:\Packages$\CustomSettings_Reference en dubbelklik vervolgens op **CustomSettings.ini**.  

2.  Open Microsoft Notepad en vervolgens de volgende regels toevoegen aan het einde van het CustomSettings.ini-bestand:

    ```  
    DoCapture=YES  
    EventService=http://WDG-MDT-01:9800  
    ```  

    Voorbeeld van het bestand CustomSettings.ini na het toevoegen van de eigenschap DoCapture:

    ```  
    [Settings]  
    Priority=Default  
    Properties=MyCustomProperty  

    [Default]  
    OSInstall=Y  
    SkipCapture=YES  
    SkipAdminPassword=NO  
    SkipProductKey=YES  
    DoCapture=YES  
    EventService=http://WDG-MDT-01:9800  
    ```  

3.  Sla het bestand in Kladblok en sluit Kladblok.  

###  <a name="UpdateDistroPoint"></a>Stap 3-6: De distributiepunten voor het pakket met aangepaste instellingen voor bestanden bijwerken  
 Wanneer de bronmap voor het aangepaste instellingen referentiecomputer MDT-pakket in Configuration Manager is bijgewerkt, werkt u de distributiepunten voor het pakket bestanden met MDT verwijzing Computer aangepaste instellingen. De distributiepunten bijgewerkt, kopieert de bijgewerkte versie van het CustomSettings.ini-bestand naar de implementatieshares die is opgegeven in het pakket.  

 **Distributiepunten de distributiepunten bijwerken voor het pakket met aangepaste instellingen**  

1.  Klik op **Start**, wijs **alle programma's**, en wijs vervolgens **Microsoft System Center 2012**. Wijs **Configuration Manager**, en klik vervolgens op **Configuration Manager-Console**.  

2.  Klik in de Configuration Manager-console in het navigatievenster op **softwarebibliotheek**.  

3.  Ga naar overzicht/Application Management/pakketten in de werkruimte softwarebibliotheek.  

4.  Klik in het voorbeeldvenster op **aangepaste instellingen referentiecomputer MDT**.  

5.  Klik op het lint op de **Start** tabblad, in de **implementatie** groep, klikt u op **distributiepunten bijwerken**.  

     De **Configuration Manager** in het dialoogvenster wordt geopend, om u te informeren dat u gaat bijwerken van het pakket op alle distributiepunten.  

6.  In de **Configuration Manager** in het dialoogvenster, klikt u op **OK**.  

7.  Sluit alle geopende vensters en dialoogvensters.  

 Configuration Manager wordt gestart op de distributiepunten bijwerken met de nieuwste versies van het CustomSettings.ini-bestand. Dit proces kan enkele minuten duren. Controleer de status van het pakket totdat de **laatste Update** waarde van de pakketstatus is bijgewerkt naar een recente datum en tijd.  

###  <a name="CustomizeTaskSequence"></a>Stap 3-7: De Takenreeks voor de referentiecomputer aanpassen  
 Voor de meeste implementaties de **Windows 8.1 verwijzing implementatie** takenreeks eerder in het proces gemaakt voert de benodigde stappen zonder aanpassing. In dit voorbeeld wijzigt u de takenreeks voor het wachtwoord voor het lokale Administrator-account instellen in een bekende waarde. Standaard wordt de takenreeks het wachtwoord voor het lokale Administrator-account ingesteld op een willekeurige waarde. Verdere aanpassing van de takenreeks is mogelijk vereist, afhankelijk van de omgeving.  

 **Voor het aanpassen van de takenreeks voor implementatie van Windows 8.1-verwijzing**  

1.  Klik op **Start**, wijs **alle programma's**, en wijs vervolgens **Microsoft System Center 2012**. Wijs **Configuration Manager**, en klik vervolgens op **Configuration Manager-Console**.  

2.  Klik in de Configuration Manager-console in het navigatievenster op **softwarebibliotheek**.  

3.  Ga in de werkruimte softwarebibliotheek naar overzicht/Operating Systems/Takenreeksen.  

4.  Klik in het voorbeeldvenster op **Windows 8.1 verwijzing implementatie**.  

5.  Klik op het lint op de **Start** tabblad, in de **Takenreeks** groep, klikt u op **bewerken**.  

     De **Takenreeks voor implementatie van Windows 8.1-referentie-Editor** dialoogvenster wordt geopend.  

6.  In de **Takenreeks voor implementatie van Windows 8.1-referentie-Editor** in het dialoogvenster, gaat u naar de Windows-instellingen PostInstall/toepassen.  

7.  Op de **eigenschappen** tabblad **het account inschakelen en geef het lokale beheerderswachtwoord**.  

8.  Op de **eigenschappen** tabblad, in **wachtwoord** en **wachtwoord bevestigen**, type  **P@ssw0rd** , en klik vervolgens op **toepassen** .  

9. Breng eventuele aanvullende wijzigingen aan de takenreeks waarvoor de omgeving en klik vervolgens op **OK**.  

10. Sluit alle geopende vensters en dialoogvensters.  

## <a name="step-4-deploy-windows-81-and-capture-an-image-of-the-reference-computer"></a>Stap 4: Implementeer Windows 8.1 en een installatiekopie van de referentiecomputer  
 Wanneer u hebt gemaakt van de takenreeks voor Windows 8.1 implementeren op de referentiecomputer en een installatiekopie van de referentiecomputer wordt vastgelegd, start u de takenreeks wordt uitgevoerd. Maken van het besturingssysteem vastleggen met behulp van de Wizard Takenreeks Media in de Configuration Manager-console.  

 Windows 8.1 implementeren en een installatiekopie van de referentiecomputer door:  

-   De referentiecomputer toevoegen aan de database van de Configuration Manager-site, zoals beschreven in [stap 4-1: De referentiecomputer toevoegen aan de sitedatabase van Configuration Manager](#AddRefComptoConfigDB)  

-   Maken van een verzameling die de referentiecomputer die u zojuist hebt toegevoegd, zoals beschreven in bevat [stap 4-2: Een verzameling maken die de referentiecomputer bevat](#CreateCollectionContainRefComp)  

-   Implementeer de takenreeks van de referentie-computer, zoals beschreven in [stap 4-3: De verwijzing naar Computer-Takenreeks implementeren](#DeployRefCompTaskSeq)  

-   Met behulp van de Wizard Takenreeksmedia maken van een takenreeks opstartbare media zoals beschreven in schijf [stap 4-4: De opstartbare Takenreeksmedia maken](#CreateTaskSeqBootMedia)  

-   Opstartbare media schijf zoals beschreven in de takenreeks wordt uitgevoerd vanaf de referentiecomputer [stap 4 en 5: Start de referentiecomputer met opstartbare Media voor de Takenreeks](#StartRefCompwithTaskSeqBootMedia)  

###  <a name="AddRefComptoConfigDB"></a>Stap 4-1: De referentiecomputer toevoegen aan de sitedatabase van Configuration Manager  
 Voor het implementeren van een besturingssysteem zonder zelfstandige media naar een nieuwe computer die Configuration Manager momenteel niet beheert, moet u de nieuwe computer toevoegen aan de Configuration Manager-sitedatabase vóór het starten van het implementatieproces van het besturingssysteem. Configuration Manager kan automatisch detecteren van computers in het netwerk met een Windows-besturingssysteem geïnstalleerd. Als de computer geen besturingssysteem geïnstalleerd is, gebruiken, de Wizard computergegevens importeren naar de nieuwe computergegevens importeren.  

#### <a name="to-add-the-reference-computer-to-the-configuration-manager-site-database"></a>De referentiecomputer toevoegen aan de sitedatabase van Configuration Manager  

1.  Klik op **Start**, wijs **alle programma's**, en wijs vervolgens **Microsoft System Center 2012**. Wijs **Configuration Manager**, en klik vervolgens op **Configuration Manager-Console**.  

2.  Klik in de Configuration Manager-console in het navigatievenster op **activa en naleving**.  

3.  In de activa en naleving werkruimte, gaat u naar overzicht/apparaten.  

4.  Klik op het lint op de **Start** tabblad, in de **maken** groep, klikt u op **computergegevens importeren**.  

     De Wizard computergegevens importeren wordt gestart.  

5.  Voltooi de Wizard computergegevens importeren met behulp van de volgende informatie. Accepteer de standaardwaarden tenzij anders vermeld.  

  |**Op deze wizardpagina**|**Dit doet**|  
  |-|-|  
  |**Bron selecteren**|Klik op **Eén computer importeren**, en klik vervolgens op **volgende**.|  
  |**Bron selecteren: Één Computer**|1.  In **computernaam**, type **WDG-REF-01**.<br />2.  In **MAC-adres**, type ***Mac*** (waarbij *Mac* is het adres media access control [MAC] van de primaire-netwerkadapter voor de referentiecomputer WDG-REF-01).<br />3.  Klik op **Volgende**.|  
  |**Bron selecteren: Voorbeeld van gegevens**|Klik op **Volgende**.|  
  |**Bron selecteren: Kies doelverzameling**|Klik op **Volgende**.|  
  |**Samenvatting**|1.  Lees de informatie in de **Details** vak die die u hebt opgegeven tijdens het uitvoeren van de vorige wizardpagina's.<br />2.  Klik op **Volgende**.|  
  |**Voortgang**|De voortgang voor het importeren van de computer wordt weergegeven.|  
  |**Bevestiging**|Klik op **Sluiten**.|  

 Zie voor meer informatie over het toevoegen van een nieuwe computer aan de sitedatabase van Configuration Manager de sectie ' voor het importeren van computergegevens voor één computer' in de sectie 'Hoe te implementeren van besturingssystemen in Configuration Manager,' in de configuratie Documentatiebibliotheek Manager, die met Configuration Manager is geïnstalleerd.  

###  <a name="CreateCollectionContainRefComp"></a>Stap 4-2: Een verzameling maken die de referentiecomputer bevat  
 In de Configuration Manager-console maakt u een verzameling die de referentiecomputer (WDG-REF-01) bevat. De computerverzameling van deze wordt later gebruikt wanneer de takenreeks reclame eerder in het proces gemaakt.  

 **Een verzameling die de referentiecomputer bevat maken**  

1.  Klik op **Start**, wijs **alle programma's**, en wijs vervolgens **Microsoft System Center 2012**. Wijs **Configuration Manager**, en klik vervolgens op **Configuration Manager-Console**.  

2.  Klik in de Configuration Manager-console in het navigatievenster op **activa en naleving**.  

3.  In de activa en naleving werkruimte, gaat u naar overzicht/Apparaatverzamelingen.  

4.  Klik op het lint op de **Start** tabblad, in de **maken** groep, klikt u op **maken**, en klik vervolgens op apparaat maken **verzameling**.  

     De Wizard Apparaatverzameling maken wordt gestart.  

5.  Voltooi de Wizard Apparaatverzameling maken met de volgende gegevens. Accepteer de standaardwaarden tenzij anders vermeld.  

    |**Op deze wizardpagina**|**Dit doet**|  
    |-|-|  
    |**Algemeen**|<ol><li>In **naam**, type **Microsoft Deployment – referentiecomputer**.</li><li>In **Opmerking**, type **Computer die moet worden van de referentiecomputer voor de doelcomputers te worden geïmplementeerd**.</li><li>In **beperkte verzameling**, klikt u op **Bladeren**.<br /><br />     De **verzameling selecteren** dialoogvenster wordt weergegeven. Voer in het dialoogvenster door de volgende stappen uit te voeren:<br /><br /> <ol><li>In **naam**, klikt u op **alle systemen**.</li><li>Klik op **OK**.</li></ol></li><li>Klik op **Volgende**.</li></ol>|  
    |**Lidmaatschapsregels**|<ol><li>Klik op **regel toevoegen**, en klik vervolgens op **directe regel**.<br /><br />     De Wizard regel voor Direct lidmaatschap maken wordt gestart.</li><li>Voltooi de Wizard regel voor Direct lidmaatschap maken door de volgende stappen uit te voeren:<br /><br /> <ol><li>Klik op de pagina **Welkom** op **Volgende**.</li><li>Op de **zoeken naar Resources** pagina **bronklasse**, selecteer **systeembron**; in **kenmerknaam**, selecteer  **Naam**; in **waarde**, type **WDG-REF-01**; en klik vervolgens op **volgende**.</li><li>Op de **Resources selecteren** pagina **WDG-REF-01**, en klik vervolgens op **volgende**.</li><li>Op de **samenvatting** pagina, klikt u op **volgende**.</li><li>Op de **voortgang** pagina, de voortgang voor het maken van de nieuwe lidmaatschapsregel weergeven.</li><li>Op de **voltooiing** pagina, klikt u op **sluiten**.</li></ol></li><li>Klik op **Volgende**.</li></ol>|  
    |**Samenvatting**|1.  Lees de informatie in de **Details** vak die die u hebt opgegeven tijdens het uitvoeren van de vorige wizardpagina's.<br />2.  Klik op **Volgende**.|  
    |**Voortgang**|De voortgang voor het maken van de apparatenverzameling wordt weergegeven.|  
    |**Voltooiing**|Klik op **Sluiten**.|  

 Zie voor meer informatie de sectie 'Hoe te maken van verzamelingen in Configuration Manager,' in de Configuration manager Documentation Library die met Configuration Manager is geïnstalleerd.  

###  <a name="DeployRefCompTaskSeq"></a>Stap 4-3: De verwijzing naar Computer-Takenreeks implementeren  
 Implementeer de takenreeks die eerder in het proces in de apparaatverzameling met de referentiecomputer gemaakt eerder in het proces hebt gemaakt in de Configuration Manager-console.  

#### <a name="to-deploy-the-task-sequence"></a>De takenreeks implementeren
1.  Klik op **Start**, wijs **alle programma's**, en wijs vervolgens **Microsoft System Center 2012**. Wijs **Configuration Manager**, en klik vervolgens op **Configuration Manager-Console**.  

2.  Klik in de Configuration Manager-console in het navigatievenster op **softwarebibliotheek**.  

3.  Ga in de werkruimte softwarebibliotheek naar overzicht/Operating Systems/Takenreeksen.  

4.  Klik in het voorbeeldvenster op **Windows 8.1 verwijzing implementatie**.  

5.  Klik op het lint op de **Start** tabblad, in de **implementatie** groep, klikt u op **implementeren**.  

     De Wizard Software implementeren wordt gestart.  

6.  Voltooi de Wizard Software implementeren met behulp van de volgende informatie. Accepteer de standaardwaarden tenzij anders vermeld.

    |**Op deze wizardpagina**|**Dit doet**|  
    |-|-|  
    |**Algemeen**|1.  In **verzameling**, klikt u op **Bladeren**.<br />2.  In de **verzameling Bladeren** in het dialoogvenster, klikt u op **Microsoft Deployment – referentiecomputer**, en klik vervolgens op **OK**.<br />3.  In **Opmerking**, type **Windows 8.1 implementeren op de referentiecomputer en vervolgens vastleggen een installatiekopie van de referentiecomputer**.<br />4.  Klik op **Volgende**.|  
    |**Implementatie-instellingen**|1.  In **doel**, selecteer **beschikbaar**.<br />2.  Selecteer de **beschikbaar maken voor opstartmedia en PXE** selectievakje.<br />3.  Klik op **Volgende**.|  
    |**Implementatie-instellingen: Planning**|Klik op **Volgende**.|  
    |**Implementatie-instellingen: Gebruikerservaring**|Klik op **Volgende**.|  
    |**Implementatie-instellingen: Waarschuwingen**|Klik op **Volgende**.|  
    |**Implementatie-instellingen: Distributiepunten**|Klik op **Volgende**.|  
    |**Samenvatting**|1.  Lees de informatie in de **Details** vak die die u hebt opgegeven tijdens het uitvoeren van de vorige wizardpagina's.<br />2.  Klik op **Volgende**.|  
    |**Voortgang**|De voortgang voor het implementeren van de takenreeks wordt weergegeven.|  
    |**Voltooiing**|Klik op **Sluiten**.|  

 Zie voor meer informatie de sectie 'Hoe te implementeren van een Takenreeks,' in de Configuration manager Documentation Library die met Configuration Manager is geïnstalleerd.  

###  <a name="CreateTaskSeqBootMedia"></a>Stap 4-4: De opstartbare Takenreeksmedia maken  
 Bieden een methode voor het starten van de computer met Windows PE en de benodigde software door het maken van de schijf taak sequence opstartbare media voor het initiëren van de MDT-proces. Gebruik de Wizard Takenreeks Media in de Configuration Manager-console voor het maken van opstartbare media voor opslag op een USB-flashstation, cd-rom of DVD.  

#### <a name="to-create-a-task-sequence-bootable-media-disk"></a>Een schijf taak sequence opstartbare media maken  

1.  Klik op **Start**, wijs **alle programma's**, en wijs vervolgens Microsoft System Center 2012. Wijs **Configuration Manager**, en klik vervolgens op **Configuration Manager-Console**.  

2.  Klik in de Configuration Manager-console in het navigatievenster op **softwarebibliotheek**.  

3.  Ga in de werkruimte softwarebibliotheek naar overzicht/Operating Systems/Takenreeksen.  

4.  Klik op het lint op de **Start** tabblad, in de **maken** groep, klikt u op **Takenreeksmedia maken**.  

     De Wizard maakt Takenreeksmedia taak wordt gestart.  

5.  Voltooi de Wizard Takenreeks maken Media met de volgende gegevens. Accepteer de standaardwaarden tenzij anders vermeld.

    |**Op deze wizardpagina**|**Dit doet**|  
    |-|-|  
    |**Mediatype selecteren**|1.  Klik op **opstartbare media**.<br />2.  Schakel de **implementatie van besturingssysteem zonder toezicht toestaan** selectievakje.<br />3.  Klik op **Volgende**.|  
    |**Het mediatype selecteren: Mediabeheer**|Klik op **Site gebaseerde media**, en klik vervolgens op **volgende**.|  
    |**Het mediatype selecteren: Mediatype**|In **mediabestand**, type  **\\\WDG-MDT-01\Capture$\CM2012_TS_Boot_Media.iso**, en klik vervolgens op **volgende**.|  
    |**Het mediatype selecteren: Beveiliging**|In **wachtwoord** en **wachtwoord bevestigen**, type  **P@ssw0rd** , en klik vervolgens op **volgende**.|  
    |**Het mediatype selecteren: Opstartinstallatiekopie**|1.  In **opstartinstallatiekopie**, klikt u op **Bladeren**.<br />2.  In de **een opstartinstallatiekopie selecteren** in het dialoogvenster, klikt u op **Windows PE aangepaste**, en klik vervolgens op **OK**.<br />3.  In **distributiepunt**, klikt u op  **\\\WDG-MDT-01.mdt2013.corp.woodgrovebank.com**, en klik vervolgens op **OK**.<br />4.  In **beheerpunt**, klikt u op  **\\\WDG-MDT-01.mdt2013.corp.woodgrovebank.com**, en klik vervolgens op **OK**.<br />5.  Klik op **Volgende**.|  
    |**Het mediatype selecteren: Aanpassing**|Klik op **Volgende**.|  
    |**Samenvatting**|1.  Lees de informatie in de **Details** vak die die u hebt opgegeven tijdens het uitvoeren van de vorige wizardpagina's.<br />2.  Klik op **Volgende**.|  
    |**Voortgang**|De voortgang voor het maken van media voor de takenreeks wordt weergegeven.|  
    |**Voltooiing**|Klik op **Sluiten**.|  

    De wizard maakt het bestand CM2012_TS_Boot_Media.iso in de MDT-WDG-01Capture$ gedeelde map.  

6.  Als REF-01-WDG een fysieke computer is, maakt u een CD of DVD van de International Organization for Standardization (ISO)-bestand. Als REF-01-WDG een virtuele machine is, start u de virtuele machine rechtstreeks vanuit het ISO-bestand.  

 Zie voor meer informatie over het maken van de schijf taak sequence opstartbare media de sectie 'Hoe te maken van opstartbare Media,' in de Configuration manager Documentation Library die met Configuration Manager is geïnstalleerd.  

###  <a name="StartRefCompwithTaskSeqBootMedia"></a>Stap 4 en 5: Start de referentiecomputer met opstartbare Media voor de Takenreeks  
 Start de referentiecomputer (WDG-REF-01) met de taak sequence opstartbare media schijf die eerder in het proces wordt gemaakt. Dit medium wordt Windows PE gestart op de referentiecomputer en start het proces MDT. Windows 8.1 is geïmplementeerd op de referentiecomputer en een installatiekopie van de referentiecomputer wordt opgeslagen in \WDG-MDT-01\Capture$\WDG-REF-01.wim aan het einde van de MDT-proces.  

> [!NOTE]   
>  U kunt ook de MDT-proces starten door het starten van de doelcomputer vanaf de Windows Deployment Services.  

#### <a name="to-start-the-reference-computer-with-the-task-sequence-bootable-media"></a>Starten van de referentiecomputer met opstartbare media voor de takenreeks

1.  Start WDG-REF-01 met opstartbare media voor de takenreeks eerder in het proces hebt gemaakt.  

     Windows PE wordt gestart en vervolgens de Wizard Takenreeks wordt gestart.  

2.  Voltooi de Wizard Takenreeks met behulp van de volgende informatie. Accepteer de standaardwaarden tenzij anders vermeld.  

    |**Op deze wizardpagina**|**Dit doet**|  
    |-|-|  
    |**Welkom bij de Wizard Takenreeks**|In **wachtwoord**, type  **P@ssw0rd** , en klik vervolgens op **volgende**.|  
    |**Selecteer een Takenreeks**|Selecteer in de keuzelijst **Windows 8.1 verwijzing implementatie**, en klik vervolgens op **volgende**.|  

#### <a name="to-monitor-the-reference-computer-deployment-process-using-the-deployment-workbench-complete-the-following-steps-on-wdg-mdt-01"></a>Voor het bewaken van het implementatieproces van de verwijzing naar computer met behulp van de implementatie-Workbench, de volgende stappen op de MDT-01-WDG

1.  Klik op WDG-MDT-01 **Start**, en wijs vervolgens **alle programma's**. Wijs **Microsoft Deployment Toolkit**, en klik vervolgens op **implementatie-Workbench**.  

2.  In de consolestructuur van de implementatie-Workbench gaat u naar de implementatie Workbench/implementatie Shares/MDT-Implementatieshare (C:\DeploymentShare$)/Monitoring.  

3.  In het deelvenster met details weergeven het implementatieproces voor **WDG-REF-01**.  

4.  Klik in het deelvenster Acties periodiek op **vernieuwen**.  

     De status van het implementatieproces is bijgewerkt in het detaildeelvenster. Blijven volgen het implementatieproces totdat het proces voltooid is.  

5.  Klik in het detailvenster op **WDG-REF-01**.  

6.  Klik in het deelvenster Acties op **eigenschappen**.  

     De **WDG-REF-01-eigenschappen** in het dialoogvenster wordt weergegeven.  

7.  In de **WDG-REF-01-eigenschappen** in het dialoogvenster op de **identiteit** tabblad, de controle-informatie gegeven over het implementatieproces als volgt bekijken:

    |**Informatie**|**Beschrijving**|  
    |-|-|  
    |**ID**|De unieke id voor de computer wordt geïmplementeerd.|  
    |**Computernaam**|De naam van de computer wordt geïmplementeerd.|  
    |**Implementatiestatus**|De huidige status van de computer wordt geïmplementeerd; de status kan een van de volgende zijn:<br /><br /> -   **Met**. De takenreeks is in orde en wordt uitgevoerd.<br />-   **Kan geen**. De takenreeks is mislukt en het implementatieproces is mislukt.<br />-   **Voltooid**. De takenreeks is voltooid.<br />-   **Niet-reagerende**. De takenreeks heeft de status ervan niet bijgewerkt in de afgelopen vier uur en wordt ervan uitgegaan dat niet meer reageert.|  
    |**Stap**|De huidige takenreeksstap wordt uitgevoerd.|  
    |**Voortgang**|De algemene voortgang van de takenreeks wordt uitgevoerd. De voortgangsbalk geeft aan hoeveel takenreeksstappen van het totale aantal met takenreeksstappen zijn uitgevoerd.|  
    |**Start**|De tijd die het implementatieproces gestart.|  
    |**Einde**|De tijd die het implementatieproces is beëindigd.|  
    |**Verstreken**|Hoe lang het implementatieproces actief is geweest of duurde om uit te voeren als de implementatie is voltooid.|  
    |**Fouten**|Het aantal fouten zijn opgetreden tijdens het implementatieproces.|  
    |**Waarschuwingen**|Het aantal waarschuwingen aangetroffen tijdens het implementatieproces.|  
    |**Extern bureaublad**|Deze knop kunt u extern bureaublad verbinding te maken met de computer wordt geïmplementeerd met behulp van de functie Extern bureaublad van Windows. Deze methode wordt ervan uitgegaan dat:<br /><br /> -Het beoogde besturingssysteem wordt uitgevoerd en ondersteuning voor externe bureaublad is ingeschakeld<br />-   **mstsc.exe** zich in het pad **Opmerking:**  Deze knop wordt altijd weergegeven, maar mogelijk niet tot stand brengen van een extern bureaublad-sessiehost als de bewaakte computer wordt uitgevoerd Windows PE, installatie van het beoogde besturingssysteem niet is voltooid of beschikt niet over de functie Extern bureaublad is ingeschakeld.|  
    |**VM-verbinding**|Deze knop kunt u extern bureaublad verbinding te maken met een virtuele machine in HyperV® uitgevoerd. Deze methode wordt ervan uitgegaan dat:<br /><br /> -De implementatie wordt uitgevoerd op een virtuele machine waarop Hyper-V<br />-   **vmconnect.exe** bevindt zich in de map %ProgramFiles%\Hyper-V **Opmerking:**  Deze knop wordt weergegeven wanneer ZTIGather.wsf detecteert dat de onderdelen voor Hyper-V-integratie worden uitgevoerd op de bewaakte computer. Anders wordt is deze knop alleen zichtbaar.|  
    |**DaRT extern beheer**|Deze knop kunt u tot stand brengen van een sessie voor extern beheer met de viewer voor extern-functie in de Diagnostics and Recovery Toolkit (DaRT).<br /><br /> Deze methode wordt ervan uitgegaan dat:<br /><br /> -DaRT is geïmplementeerd op de doelcomputer en wordt momenteel uitgevoerd.<br />-   **DartRemoteViewer.exe** bevindt zich in de map %ProgramFiles%\Microsoft DaRT 7\v7 **Opmerking:**  Deze knop wordt weergegeven wanneer ZTIGather.wsf detecteert dat DaRT wordt uitgevoerd op de bewaakte computer. Anders wordt is deze knop alleen zichtbaar.|  
    |**Deze informatie om de tien seconden automatisch worden vernieuwd**|Selectievakje die bepaalt of de informatie in het dialoogvenster automatisch wordt vernieuwd. Als het selectievakje is:<br /><br /> -Geselecteerd, de gegevens worden vernieuwd elke 10 seconden<br />-Uitgeschakeld, de informatie is niet automatisch vernieuwd en moet handmatig vernieuwen met behulp van de **nu vernieuwen** knop|  
    |**Nu vernieuwen**|Deze knop wordt onmiddellijk vernieuwd voor de informatie die wordt weergegeven in het dialoogvenster.|  

8.  In de **WDG-REF-01-eigenschappen** in het dialoogvenster, klikt u op **OK**.  

9. Sluit de implementatie-Workbench.  

#### <a name="to-monitor-the-reference-computer-deployment-process-using-the-get-mdtmonitordata-cmdlet-complete-the-following-steps-on-wdg-mdt-01"></a>Voltooi de volgende stappen op de MDT-01-WDG voor het controleren van het implementatieproces van de verwijzing naar computer met de cmdlet Get-MDTMonitorData

1.  Klik op WDG-MDT-01 **Start**, klik vervolgens op **Systeembeheer**, en klik vervolgens op **Windows PowerShell-Modules**.  

     Hiermee opent u de opdrachtprompt van Windows PowerShell-Modules.  

2.  Maken van een PowerShell-station dat gebruikmaakt van de MDT-PowerShell-provider door het uitvoeren van de [nieuw PSDrive](http://technet.microsoft.com/library/hh849829.aspx) cmdlet zoals weergegeven in het volgende voorbeeld:  

    ```  
    New-PSDrive -Name DS001 -PSProvider mdtprovider -Root d:\DeploymentShare$  
    ```  

3.  Weergeven van de MDT bewakingsproces door het uitvoeren van de **Get-MDTMonitorData** cmdlet zoals weergegeven in het volgende voorbeeld:  

    ```  
    Get-MDTMonitorData -Path DS001:  
    ```  

     Deze opdracht retourneert de bewakingsgegevens verzameld door de MDT-service wordt uitgevoerd op dezelfde computer die als host fungeert de implementatieshare, bewaking, zoals wordt weergegeven in de volgende voorbeelduitvoer:  

    ```  
    Name               : WDG-REF-01  
    PercentComplete    : 96  
    Settings           :  
    Warnings           : 0  
    Errors             : 0  
    DeploymentStatus   : 1  
    StartTime          : 6/7/2012 6:45:39 PM  
    EndTime            :   
    ID                 : 1  
    UniqueID           : 94a0830e-f2bb-421c-b1e0-6f86f9eb9fa1  
    CurrentStep        : 130  
    TotalSteps         : 134  
    StepName           : Gather  
    LastTime           : 6/7/2012 8:46:32 PM  
    DartIP             :  
    DartPort           :  
    DartTicket         :  
    VMHost             : XYL-DC-02  
    VMName             : WDG-REF-01  
    ComputerIdentities : {}  
    ```  

4.  Sluit de Windows PowerShell-console.  

 Als er problemen tijdens de implementatie optreden, raadpleegt u het document MDT *probleemoplossing verwijzing*. Wanneer het voltooid, een vastgelegde installatiekopie van de referentiecomputer moet bestaan in \\\WDG-MDT-01\Capture$\WDG-REF-01.wim.  

## <a name="step-5-create-and-configure-a-task-sequence-to-deploy-the-target-computer"></a>Stap 5: Maken en configureren van een Takenreeks voor het implementeren van de doelcomputer  
 Nadat de takenreeks voor het implementeren van de referentiecomputer (WDG-REF-01) is voltooid, een vastgelegde installatiekopie van de referentiecomputer wordt opgeslagen in \\\WDG-MDT-01\Capture$\WDG-REF-01.wim. Maak nu een takenreeks die de vastgelegde installatiekopie van de referentiecomputer op de doelcomputer (WDG-CLI-01) gaat implementeren. Wanneer deze stap voltooid is, kunt u de vastgelegde installatiekopie van de referentiecomputer implementeren op de doelcomputer.  

 Maak en configureer een takenreeks voor het implementeren van de doelcomputer door:  

-   Importeren van het WIM-bestand dat is vastgelegd in de vorige stap in Configuration Manager, met behulp van de Wizard besturingssysteem afbeelding toevoegen, zoals beschreven in [stap 5-1: Het vastgelegde WIM-bestand importeren in Configuration Manager](#ImportCapturedwimFile)  

-   Met behulp van de MDT Wizard Takenreeks maken voor het maken van een sjabloon voor sequence MDT-taak voor het implementeren van de vastgelegde installatiekopie van de referentiecomputer op de doelcomputer, zoals beschreven in [stap 5 2: Maak een MDT-Takenreeks voor het implementeren van de vastgelegde installatiekopie](#CreateMDTTaskSeqDeployCapturedImage)  

-   Als u de distributiepunten voor de nieuwe pakketten en installatiekopieën van de MDT Wizard Takenreeks maken maakt zoals beschreven in [stap 5-3: Selecteer de distributiepunten voor de nieuwe pakketten en installatiekopieën](#SelectDistroPointsNewPackagesImages)  

-   Aanpassen van de MDT-configuratiebestanden voor de doelcomputer, met name het CustomSettings.ini-bestand, zoals beschreven in [stap 5-4: De MDT-configuratiebestanden aanpassen](#CustomizetheMDTConfigFiles)  

-   Bijwerken van de Configuration Manager-distributiepunten voor het pakket met aangepaste instellingen, zoals beschreven in [stap 5 tot en met 5: De distributiepunten bijwerken voor het pakket met aangepaste instellingen](#UpdateDistroPointsforCustomSettings)  

-   De takenreeks voor de doelcomputer aanpassen zoals beschreven in [stap 5 tot en met 6: De Takenreeks voor de doelcomputer aanpassen](#CustomizeTaskSequenceTargetComputer)  

###  <a name="ImportCapturedwimFile"></a>Stap 5-1: Het vastgelegde WIM-bestand importeren in Configuration Manager  
 Nadat de installatiekopie van de referentiecomputer (WDG-REF-01) is vastgelegd naar het WIM-bestand, importeer het vastgelegde WIM-bestand naar Configuration Manager. Het vastgelegde WIM-bestand importeren in de node Besturingssysteemimages met de Wizard besturingssysteem installatiekopie toevoegen.  

 Het vastgelegde WIM bevat twee afbeeldingen, één voor elke partitie op de referentiecomputer. Identificeren welke van de installatiekopieën van de vastgelegde Windows 8.1-besturingssysteem is door het controleren van de installatiekopie beschrijving die *Windows 8.1*. U gebruikt de Afbeeldingsindex bij het maken van de takenreeks voor het implementeren van de vastgelegde installatiekopie op de doelcomputer.  

 **Het vastgelegde WIM-bestand importeren in Configuration Manager**  

1.  Klik op **Start**, wijs **alle programma's**, en wijs vervolgens **Microsoft System Center 2012**. Wijs **Configuration Manager**, en klik vervolgens op **Configuration Manager-Console**.  

2.  Klik in de Configuration Manager-console in het navigatievenster op **softwarebibliotheek**.  

3.  Ga naar overzicht/Operating Systems/Operating-installatiekopieën in de werkruimte softwarebibliotheek.  

4.  Klik op het lint in de **maken** groep, klikt u op **installatiekopie van besturingssysteem toevoegen**.  

     De Wizard besturingssysteem afbeelding toevoegen wordt gestart.  

5.  Voltooi de besturingssysteem Wizard afbeelding toevoegen met behulp van de volgende informatie. Accepteer de standaardwaarden tenzij anders vermeld.  

    |**Op deze wizardpagina**|**Dit doet**|  
    |-|-|  
    |**Op deze wizardpagina**|**Dit doet**|  
    |**Gegevensbron**|In **pad**, type  **\\\WDG-MDT-01\Capture$\WDG-REF-01.wim**, en klik vervolgens op **volgende**.|  
    |**Algemeen**|1.  In **naam**, type **referentie-installatiekopie voor Windows 8.1**.<br /><br /> 1.  In **versie**, type **1,00**.<br /><br /> 1.  In **opmerkingen**, type **Windows 8.1 vastgelegde installatiekopie van een referentiecomputer (WDG-REF-01) gebruikt om te implementeren op doelcomputers**, en klik vervolgens op **volgende**.|  
    |**Samenvatting**|1.  Lees de informatie in de **Details** vak die die u hebt opgegeven tijdens het uitvoeren van de vorige wizardpagina's.<br />2.  Klik op **Volgende**.|  
    |**Voortgang**|De voortgang voor het importeren van de installatiekopie van het besturingssysteem wordt weergegeven.|  
    |**Voltooiing**|Klik op **Sluiten**.|  

6.  Klik in het voorbeeldvenster op **referentie-installatiekopie voor Windows 8.1**.  

7.  Klik in het voorbeeldvenster op de **Details** tabblad.  

     De lijst met partities van besturingssysteem vastgelegd in het WIM wordt weergegeven. De installatiekopie-index met Windows 8.1 is de installatiekopie-index die u later tijdens de MDT Wizard Takenreeks maken.  

8.  Leg de installatiekopie-index met Windows 8.1.  

    > [!TIP]    
    >  Installatiekopie-index 2 moet het besturingssysteem Windows 8.1 hebben voor de doeleinden van dit voorbeeld.  

###  <a name="CreateMDTTaskSeqDeployCapturedImage"></a>Stap 5-2: Maak een MDT-Takenreeks voor het implementeren van de vastgelegde installatiekopie  
 Nadat de installatiekopie wordt vastgelegd, moet u een takenreeks voor het implementeren van de vastgelegde installatiekopie van de referentiecomputer (WDG-REF-01) maken met de doelcomputer (WDG-CLI-01). De meeste van de pakketten die nodig zijn voor deze takenreeks zijn eerder in het proces gemaakt. Echter, moet u een nieuwe MDT aangepaste instellingen pakket dat de juiste configuratie-instellingen voor de doelcomputer en maakt een installatiekopie van het besturingssysteem van de vastgelegde installatiekopie van de referentiecomputer.  

#### <a name="to-create-a-task-sequence-template-to-deploy-the-captured-image-to-the-target-computer"></a>Een taak sequence-sjabloon voor het implementeren van de vastgelegde installatiekopie op de doelcomputer maken  

1.  Klik op **Start**, wijs **alle programma's**, en wijs vervolgens **Microsoft System Center 2012**. Wijs **Configuration Manager**, en klik vervolgens op **Configuration Manager-Console**.  

2.  Klik in de Configuration Manager-console in het navigatievenster op **softwarebibliotheek**.  

3.  Ga in de werkruimte softwarebibliotheek naar overzicht/Operating Systems/Takenreeksen.  

4.  Klik op het lint op de **Start** tabblad, in de **Takenreeksen** groep, klikt u op **Takenreeks MDT maken**.  

     De MDT Wizard Takenreeks maken wordt gestart.  

5.  Voltooi de MDT Wizard Takenreeks maken met de volgende gegevens. Accepteer de standaardwaarden tenzij anders vermeld.  

    |**Op deze wizardpagina**|**Dit doet**|  
    |-|-|  
    |**Sjabloon kiezen**|Selecteer **Clienttakenreeks**, en klik vervolgens op **volgende**.|  
    |**Sjabloon kiezen: Algemeen**|1.  In **takenreeksnaam**, type **Doelimplementatie voor Windows 8.1**.<br />2.  In **Task sequence opmerkingen**, type **Takenreeks voor het implementeren van de vastgelegde referentiesysteemkopie op de doelcomputer (WDG-CLI-01)**, en klik vervolgens op **volgende**.|  
    |**Sjabloon kiezen: Meer informatie**|<ol><li>Klik op **toevoegen aan een domein**.</li><li>In **domein**, type **mdt2013.corp.woodgrovebank.com**.</li><li>In **Account**, klikt u op **ingesteld**, en voltooi vervolgens de **Windows-gebruikersaccount** dialoogvenster door de volgende stappen uit te voeren:<br /><br /> <ol><li>In **gebruikersnaam**, type **MDT2013\Administrator**.</li><li>In **wachtwoord** en **wachtwoord bevestigen**, type  **P@ssw0rd** .</li><li>Klik op **OK**.</li></ol></li><li>In **gebruikersnaam**, type **Woodgrove Bank werknemer**.</li><li>In **organisatienaam**, type **Woodgrove Bank**.</li><li>In **productcode**, type ***productcode*** (waarbij *productcode* is de productcode voor Windows 8.1).</li><li>Klik op **Volgende**.</li></ol>|  
    |**Sjabloon kiezen: Instellingen vastleggen**|Klik op **Volgende**.|  
    |**Opstartinstallatiekopie**|1.  In **opgeven van een bestaand pakket met opstartinstallatiekopie**, klikt u op **Bladeren**.<br />2.  In **pakket selecteren** in het dialoogvenster, klikt u op **Windows PE aangepaste**, en klik vervolgens op **OK**.<br />3.  Klik op **Volgende**.|  
    |**MDT-pakket**|1.  In **Geef een bestaand pakket voor Microsoft Deployment Toolkit bestanden**, klikt u op **Bladeren**.<br />2.  In de **pakket selecteren** in het dialoogvenster, klikt u op **MDT bestanden**, en klik vervolgens op **OK**.<br />3.  Klik op **Volgende**.|  
    |**Installatiekopie van het besturingssysteem**|1.  Klik op **Geef een bestaande OS-installatiekopie**.<br />2.  In **Geef een bestaande OS-installatiekopie**, klikt u op **Bladeren**.<br />3.  In de **pakket selecteren** in het dialoogvenster, klikt u op **referentie-installatiekopie voor Windows 8.1**, en klik vervolgens op **OK**.<br />4.  Klik op **Volgende**.|  
    |**Installatiekopie van het besturingssysteem: Index van de installatiekopie van het besturingssysteem**|1.  In **het gekozen besturingssysteem (WIM)-bestand meerdere installatiekopieën bevat**. **Geef de afbeelding die u wilt implementeren**, selecteer ***Index_van_installatiekopie*** (waarbij *Index_van_installatiekopie* is de installatiekopie-index van de installatiekopie die Windows 8.1, die is geïdentificeerd in de sectie bevat [Stap 5-1: Het vastgelegde WIM-bestand importeren in Configuration Manager](#ImportCapturedwimFile); voor de doeleinden van deze handleiding, selecteer **2**).<br />2.  Klik op **Volgende**.|  
    |**Methode-implementatie**|Klik op **Volgende**.|  
    |**Clientpakket**|1.  In **opgeven van een bestaande ConfigMgr-clientpakket**, klikt u op **Bladeren**.<br />2.  In de **pakket selecteren** in het dialoogvenster, klikt u op **Microsoft Configuration Manager-Clientupgrade**, en klik vervolgens op **OK**.<br />3.  Klik op **Volgende**.|  
    |**USMT-pakket**|1.  In **Geef een bestaand USMT-pakket**, klikt u op **Bladeren**.<br />2.  In de **pakket selecteren** in het dialoogvenster, klikt u op **USMT**, en klik vervolgens op **OK**.<br />3.  Klik op **Volgende**.|  
    |**Instellingen pakket**|1.  Klik op **Maak een nieuw pakket van de instellingen**.<br />2.  In **pakketbronmap worden gemaakt**, type  **\\\WDG-MDT-01\Packages$\CustomSettings_Target**, en klik vervolgens op **volgende**.|  
    |**Instellingen voor pakket: Details van instellingen**|1.  In **naam**, type **MDT doel Computer aangepaste instellingen**.<br />2.  In **versie**, type **1,00**.<br />3.  In **opmerkingen**, type **configuratie-instellingen voor de MDT-implementatieproces (zoals CustomSettings.ini) voor de doelcomputer**, en klik vervolgens op **volgende**.|  
    |**Sysprep-pakket**|Klik op **Volgende**.|  
    |**Samenvatting**|1.  Lees de informatie in de **Details** vak die die u hebt opgegeven tijdens het uitvoeren van de vorige wizardpagina's.<br />2.  Klik op **Volgende**.|  
    |**Voortgang**|De voortgang voor het maken van de takenreeks wordt weergegeven.|  
    |**Bevestiging**|Klik op **Voltooien**.|  

 De lijst met takenreeksen wordt weergegeven. De takenreeks die u zojuist hebt gemaakt (Windows 8.1 Doelimplementatie) wordt vermeld in de lijst van takenreeksen.  

###  <a name="SelectDistroPointsNewPackagesImages"></a>Stap 5-3: Selecteer de distributiepunten voor de nieuwe pakketten en installatiekopieën  
 De MDT Wizard Takenreeks maken maakt een aantal pakketten en afbeeldingen. Nadat deze pakketten en afbeeldingen worden gemaakt, selecteert u de distributiepunten op waarop de pakketten en afbeeldingen, gekopieerd en beschikbaar zijn voor de doelcomputers worden moeten.  

> [!NOTE]
>  In dit voorbeeld is er slechts één distributiepunt (WDG-MDT-01). De meeste productienetwerken hebben echter meerdere distributiepunten. Wanneer u deze stap uitvoert in een productieomgeving, selecteer de juiste distributiepunten voor het netwerk.  

#### <a name="to-select-the-distribution-points-for-software-distribution-packages"></a>Selecteer de distributiepunten voor softwaredistributiepakketten  

1.  Klik op **Start**, wijs **alle programma's**, en wijs vervolgens **Microsoft System Center 2012**. Wijs **Configuration Manager**, en klik vervolgens op **Configuration Manager-Console**.  

2.  Klik in de Configuration Manager-console in het navigatievenster op **softwarebibliotheek**.  

3.  Ga in de werkruimte softwarebibliotheek naar overzicht/Operating Systems/Takenreeksen.  

4.  Selecteer in het voorbeeldvenster **Doelimplementatie voor Windows 8.1**.  

5.  Klik op het lint op de **Start** tabblad, in de **implementatie** groep, klikt u op **inhoud distribueren**.  

     De Wizard inhoud distribueren wordt gestart.  

6.  Voltooi de Wizard inhoud distribueren met behulp van de volgende informatie. Accepteer de standaardwaarden tenzij anders vermeld.  

    |**Op deze wizardpagina**|**Dit doet**|  
    |-|-|  
    |**Algemeen**|Klik op **Volgende**.|  
    |**Inhoud**|Klik op **Volgende**.|  
    |**Algemeen: Inhoud**|Klik op **Volgende**.|  
    |**Algemeen: Doel van inhoud**|1.  Klik op **toevoegen**, en klik vervolgens op **distributiepunt**.<br />     De **distributiepunten toevoegen** dialoogvenster wordt weergegeven.<br />2.  In de **distributiepunten toevoegen** dialoogvenster,  **\\\WDGMDT01.mdt2013.corp.woodgrovebank.com**, en klik vervolgens op **OK**.<br />     \\\WDGMDT01.mdt2013.corp.woodgrovebank.com wordt weergegeven in de **doel van inhoud** lijst.<br />3.  Klik op **Volgende**.|  
    |**Samenvatting**|1.  Lees de informatie in de **Details** vak die die u hebt opgegeven tijdens het uitvoeren van de vorige wizardpagina's.<br />2.  Klik op **Volgende**.|  
    |**Voortgang**|De voortgang voor het distribueren van de software wordt weergegeven.|  
    |**Voltooiing**|Klik op **Sluiten**.|  

7.  Sluit alle geopende vensters en dialoogvensters.  

###  <a name="CustomizetheMDTConfigFiles"></a>Stap 5-4: De MDT-configuratiebestanden aanpassen  
 Wanneer de takenreeks voor de doelcomputer is gemaakt, aanpassen de MDT-configuratiebestanden die voorzien in de configuratie-instellingen voor Windows 8.1 implementeren met de doelcomputer, in het bijzonder CustomSettings.ini.  

 Wanneer het CustomSettings.ini-bestand is aangepast, moet u de bijgewerkte bestanden opslaan voor de bronmap voor het pakket MDT aangepaste instellingen is eerder in het proces (E:\Packages$\CustomSettings_Target) gemaakt.  

#### <a name="to-customize-the-mdt-configuration-files-for-the-target-computer"></a>Voor het aanpassen van de MDT-configuratiebestanden voor de doelcomputer  

1.  In Windows Verkenner, Ga naar de map E:\Packages$\CustomSettings_Target en dubbelklik vervolgens op **CustomSettings.ini**.  

2.  Open Kladblok en vervolgens de volgende regels toevoegen aan het CustomSettings.ini-bestand:  

    ```  
    EventService=http://WDG-MDT-01:9800  
    ```  

     Deze instelling configureert bewaking van de implementatie van de doel-computers.  

    > [!NOTE]
    >  Breng eventuele wijzigingen die voor uw omgeving vereist zijn.  

     **Voorbeeld van het bewerkte CustomSettings.ini-bestand:**  

    ```  
    [Settings]  
    Priority=Default  
    Properties=MyCustomProperty  

    [Default]  
    OSInstall=Y  
    SkipCapture=YES  
    SkipAdminPassword=NO  
    SkipProductKey=YES  
    EventService=http://WDG-MDT-01:9800  

    ```  

3.  Sla het bestand op en sluit Kladblok.  

###  <a name="UpdateDistroPointsforCustomSettings"></a>Stap 5 tot en met 5: De distributiepunten bijwerken voor het pakket met aangepaste instellingen  
 Wanneer de bronmap voor het pakket MDT doel Computer aangepaste instellingen in Configuration Manager is bijgewerkt, werkt u de distributiepunten voor het pakket MDT doel Computer aangepaste instellingen. De distributiepunten bijgewerkt, kopieert de bijgewerkte versie van het CustomSettings.ini-bestand naar de implementatieshares die is opgegeven in het pakket.  

#### <a name="to-update-the-distribution-points-for-the-custom-settings-package"></a>Distributiepunten de distributiepunten bijwerken voor het pakket met aangepaste instellingen  

1.  Klik op **Start**, wijs **alle programma's**, en wijs vervolgens **Microsoft System Center 2012**. Wijs **Configuration Manager**, en klik vervolgens op **Configuration Manager-Console**.  

2.  Klik in de Configuration Manager-console in het navigatievenster op **softwarebibliotheek**.  

3.  Ga naar overzicht/Application Management/pakketten in de werkruimte softwarebibliotheek.  

4.  Klik in het voorbeeldvenster op **MDT doel Computer aangepaste instellingen**.  

5.  Klik op het lint op de **Start** tabblad, in de **implementatie** groep, klikt u op **distributiepunten bijwerken**.  

     De **Configuration Manager** in het dialoogvenster wordt geopend, om u te informeren dat u gaat bijwerken van het pakket op alle distributiepunten.  

6.  In de **Configuration Manager** in het dialoogvenster, klikt u op **OK**.  

7.  Sluit alle geopende vensters en dialoogvensters.  

###  <a name="CustomizeTaskSequenceTargetComputer"></a>Stap 5 tot en met 6: De Takenreeks voor de doelcomputer aanpassen  
 Voor de meeste implementaties voert de takenreeks voor implementatie van Windows 8.1 doel eerder in het proces hebt gemaakt de benodigde stappen zonder aanpassing. In dit voorbeeld wordt de taak sequence sjabloon aanpassen zodat het wachtwoord voor het lokale Administrator-account instellen in een bekende waarde. (Standaard de taakvolgorde stelt het wachtwoord voor het lokale Administrator-account op een willekeurige waarde.) De takenreeks kan vereisen verdere aanpassing afhankelijk van de omgeving.  

#### <a name="to-customize-the-windows-81-target-deployment-task-sequence"></a>Voor het aanpassen van de takenreeks voor implementatie van Windows 8.1-doel

1.  Klik op **Start**, wijs **alle programma's**, en wijs vervolgens **Microsoft System Center 2012**. Wijs **Configuration Manager**, en klik vervolgens op **Configuration Manager-Console**.  

2.  Klik in de Configuration Manager-console in het navigatievenster op **softwarebibliotheek**.  

3.  Ga in de werkruimte softwarebibliotheek naar overzicht/Operating Systems/Takenreeksen.  

4.  Klik in het voorbeeldvenster op **Windows 8.1 verwijzing implementatie**.  

5.  Klik op het lint op de **Start** tabblad, in de **Takenreeks** groep, klikt u op **bewerken**.  

     De **Takenreeks voor implementatie van Windows 8.1-referentie-Editor** dialoogvenster wordt geopend.  

6.  In de **Takenreeks voor implementatie van Windows 8.1-referentie-Editor** in het dialoogvenster, gaat u naar de Windows-instellingen PostInstall/toepassen.  

7.  Op de **eigenschappen** tabblad **het account inschakelen en geef het lokale beheerderswachtwoord**.  

8.  Op de **eigenschappen** tabblad, in **wachtwoord** en **wachtwoord bevestigen**, type  **P@ssw0rd** , en klik vervolgens op **toepassen** .  

9. Breng eventuele aanvullende wijzigingen aan de takenreeks waarvoor de omgeving en klik vervolgens op **OK**.  

10. Sluit alle geopende vensters en dialoogvensters.  



## <a name="step-6-deploy-the-captured-image-of-the-reference-computer-to-the-target-computer"></a>Stap 6: De vastgelegde installatiekopie van de referentiecomputer implementeren op de doelcomputer  
 Wanneer u de installatiekopie van de referentiecomputer vastgelegd en gemaakt en de takenreeks wordt geconfigureerd, moet u de vastgelegde installatiekopie implementeren. Configureer MDT om op te geven van alle benodigde configuratie-instellingen implementeren op de doelcomputer. De installatiekopie van de referentiecomputer met Windows 8.1 is na het initiëren van het implementatieproces automatisch geïmplementeerd op de doelcomputer en geconfigureerd met de instellingen die zijn gedefinieerd.  

 De vastgelegde installatiekopie door implementeren:  

-   De doelcomputer toevoegen aan de database van de Configuration Manager-site, zoals beschreven in [stap 6-1: De doelcomputer toevoegen aan de sitedatabase van Configuration Manager](#AddTargetComptoConfigManager)  

-   Maken van een computerverzameling die de doelcomputer bevat zoals beschreven in [stap 6 2: Maak een Computerverzameling met de doelcomputer](#CreateComputerCollectionIncludesTarget)  

-   Eerder in het proces voor het implementeren van de takenreeks gemaakt zoals beschreven in [stap 6-3: Implementeer de Takenreeks van de doel-Computer](#DeployTargetComputerTaskSequence)  

-   Starten van de doelcomputer met opstartbare media voor de takenreeks, zoals beschreven in [stap 6-4: Start de doelcomputer met opstartbare Media voor de Takenreeks](#StartTargetComputerTaskSequenceMedia)  

###  <a name="AddTargetComptoConfigManager"></a>Stap 6-1: De doelcomputer toevoegen aan de sitedatabase van Configuration Manager  
 Voor het implementeren van een besturingssysteem zonder zelfstandige media naar een nieuwe computer die Configuration Manager momenteel niet beheert, moet u de nieuwe computer toevoegen aan de Configuration Manager-sitedatabase vóór het starten van het implementatieproces van het besturingssysteem. Configuration Manager kan automatisch detecteren van computers in het netwerk met een Windows-besturingssysteem geïnstalleerd. Als de computer geen besturingssysteem geïnstalleerd is, gebruiken, de Wizard computergegevens importeren naar de nieuwe computergegevens importeren.  

#### <a name="to-add-the-target-computer-to-the-configuration-manager-site-database"></a>De doelcomputer toevoegen aan de sitedatabase van Configuration Manager  

1.  Klik op **Start**, wijs **alle programma's**, en wijs vervolgens **Microsoft System Center 2012**. Wijs **Configuration Manager**, en klik vervolgens op **Configuration Manager-Console**.  

2.  Klik in de Configuration Manager-console in het navigatievenster op **activa en naleving**.  

3.  In de activa en naleving werkruimte, gaat u naar overzicht/apparaten.  

4.  Klik op het lint op de **Start** tabblad, in de **maken** groep, klikt u op **computergegevens importeren**.  

     De Wizard computergegevens importeren wordt gestart.  

5.  Voltooi de Wizard computergegevens importeren met behulp van de volgende informatie. Accepteer de standaardwaarden tenzij anders vermeld.  

    |**Op deze wizardpagina**|**Dit doet**|  
    |-|-|  
    |**Bron selecteren**|Klik op **Eén computer importeren**, en klik vervolgens op **volgende**.|  
    |**Bron selecteren: Één Computer**|1.  In **computernaam**, type **CLI-01-WDG**.<br />2.  In **MAC-adres**, type ***Mac*** (waarbij *Mac* MAC-adres van de primaire-netwerkadapter voor de doelcomputer, CLI-01-WDG).<br />3.  Klik op **Volgende**.|  
    |**Bron selecteren: Voorbeeld van gegevens**|Klik op **Volgende**.|  
    |**Bron selecteren: Kies doelverzameling**|Klik op **Volgende**.|  
    |**Samenvatting**|1.  Lees de informatie in de **Details** vak die die u hebt opgegeven tijdens het uitvoeren van de vorige wizardpagina's.<br />2.  Klik op **Volgende**.|  
    |**Voortgang**|De voortgang voor het importeren van de computer wordt weergegeven.|  
    |**Bevestiging**|Klik op **Sluiten**.|  

 Zie voor meer informatie over het toevoegen van een nieuwe computer aan de sitedatabase van Configuration Manager de sectie ' voor het importeren van computergegevens voor één computer' in de sectie 'Hoe te implementeren van besturingssystemen in Configuration Manager,' in de configuratie Manager Documentation Library die met Configuration Manager is geïnstalleerd.  

###  <a name="CreateComputerCollectionIncludesTarget"></a>Stap 6-2: Maak een Computerverzameling met de doelcomputer  
 In de Configuration Manager-console maakt een verzameling die de doelcomputer (WDG-CLI-01) bevat. U gebruikt deze computerverzameling later wanneer reclame van de takenreeks die eerder in het proces hebt gemaakt.  

#### <a name="to-create-a-computer-collection-that-includes-the-target-computer"></a>Om de computerverzameling van een met de doelcomputer te maken

1.  Klik op **Start**, wijs **alle programma's**, en wijs vervolgens **Microsoft System Center 2012**. Wijs **Configuration Manager**, en klik vervolgens op **Configuration Manager-Console**.  

2.  Klik in de Configuration Manager-console in het navigatievenster op **activa en naleving**.  

3.  In de activa en naleving werkruimte, gaat u naar overzicht/Apparaatverzamelingen.  

4.  Klik op het lint op de **Start** tabblad, in de **maken** groep, klikt u op **Apparaatverzameling maken**.  

     De Wizard Apparaatverzameling maken wordt gestart.  

5.  Voltooi de Wizard Apparaatverzameling maken met de volgende gegevens. Accepteer de standaardwaarden tenzij anders vermeld.  

    |**Op deze wizardpagina**|**Dit doet**|  
    |-|-|  
    |**Op deze wizardpagina**|**Dit doet**|  
    |**Algemeen**|<ol><li>In **naam**, type **Microsoft Deployment – Batch 01**.</li><li>In **Opmerking**, type **Computers die moeten worden opgenomen in de eerste batch van computers die zijn geïmplementeerd**.</li><li>In **beperkte verzameling**, klikt u op **Bladeren**.<br /><br />     De **verzameling selecteren** dialoogvenster wordt weergegeven. Voer in het dialoogvenster door de volgende stappen uit te voeren:<br /><br /> <ol><li>In de **verzameling selecteren** het dialoogvenster **naam**, klikt u op **alle systemen**.</li><li>Klik op **OK**.</li></ol></li><li>Klik op **Volgende**.</li></ol>|  
    |**Lidmaatschapsregels**|<ol><li>Klik op **regel toevoegen**, en klik vervolgens op **directe regel**.<br /><br />     De Wizard regel voor Direct lidmaatschap maken wordt gestart.</li><li>Voltooi de Wizard regel voor Direct lidmaatschap maken door de volgende stappen uit te voeren:<br /><br /> <ol><li>Klik op de pagina **Welkom** op **Volgende**.</li><li>Op de **zoeken naar Resources** pagina **bronklasse**, selecteer **systeembron**; in **kenmerknaam**, selecteer  **Naam**; in **waarde**, type **WDG-CLI-01**; en klik vervolgens op **volgende**.</li><li>Op de **Resources selecteren** pagina **WDG-CLI-01**, en klik vervolgens op **volgende**. **Opmerking:**          Het proces voor het toevoegen van de doelcomputer (WDG-CLI-01) aan alle systemen kan enkele minuten duren. Als de CLI-01-WDG niet wordt weergegeven in de lijst, Herhaal stap b en c totdat WDGCLI01 wordt weergegeven.</li><li>Op de **samenvatting** pagina, klikt u op **volgende**.</li><li>Op de **voltooiing** pagina, klikt u op **sluiten**.</li></ol></li><li>Klik op **Volgende**.</li></ol>|  
    |**Samenvatting**|1.  Lees de informatie in de **Details** vak die die u hebt opgegeven tijdens het uitvoeren van de vorige wizardpagina's.<br />2.  Klik op **Volgende**.|  
    |**Voortgang**|De voortgang voor het maken van de apparatenverzameling wordt weergegeven.|  
    |**Voltooiing**|Klik op **Sluiten**.|  

 Zie voor meer informatie de sectie 'Hoe te maken van verzamelingen in Configuration Manager,' in de Configuration manager Documentation Library die met Configuration Manager is geïnstalleerd.  

###  <a name="DeployTargetComputerTaskSequence"></a>Stap 6-3: Implementeer de Takenreeks van de doel-Computer  
 Implementeer de takenreeks die eerder in het proces voor de doelcomputers gemaakt in de Configuration Manager-console. De takenreeks implementeren voor de verzameling van doelcomputers die eerder in het proces hebt gemaakt.  

#### <a name="to-deploy-the-task-sequence"></a>De takenreeks implementeren  

1.  Klik op **Start**, wijs **alle programma's**, en wijs vervolgens **Microsoft System Center 2012**. Wijs **Configuration Manager**, en klik vervolgens op **Configuration Manager-Console**.  

2.  Klik in de Configuration Manager-console in het navigatievenster op **softwarebibliotheek**.  

3.  Ga in de werkruimte softwarebibliotheek naar overzicht/Operating Systems/Takenreeksen.  

4.  Klik in het voorbeeldvenster op **Doelimplementatie voor Windows 8.1**.  

5.  Klik op het lint op de **Start** tabblad, in de **implementatie** groep, klikt u op **implementeren**.  

     De Wizard Software implementeren wordt gestart.  

6.  Voltooi de Wizard Software implementeren met behulp van de volgende informatie.  Accepteer de standaardwaarden tenzij anders vermeld.  

    |**Op deze wizardpagina**|**Dit doet**|  
    |-|-|  
    |**Algemeen**|1.  In **verzameling**, klikt u op **Bladeren**.<br />2.  In de **verzameling Bladeren** in het dialoogvenster, klikt u op **Microsoft Deployment – Batch 01**, en klik vervolgens op **OK**.<br />3.  In **Opmerking**, type **Windows 8.1 implementeren naar de eerste batch van doelcomputers**.<br />4.  Klik op **Volgende**.|  
    |**Implementatie-instellingen**|1.  In **doel**, selecteer **beschikbaar**.<br />2.  Selecteer de **beschikbaar maken voor opstartmedia en PXE** selectievakje.<br />3.  Klik op **Volgende**.|  
    |**Implementatie-instellingen: Planning**|Klik op **Volgende**.|  
    |**Implementatie-instellingen: Gebruikerservaring**|Klik op **Volgende**.|  
    |**Implementatie-instellingen: Waarschuwingen**|Klik op **Volgende**.|  
    |**Implementatie-instellingen: Distributiepunten**|Klik op **Volgende**.|  
    |**Samenvatting**|1.  Lees de informatie in de **Details** vak die die u hebt opgegeven tijdens het uitvoeren van de vorige wizardpagina's.<br />2.  Klik op **Volgende**.|  
    |**Voortgang**|De voortgang voor het implementeren van de takenreeks wordt weergegeven.|  
    |**Voltooiing**|Klik op **Sluiten**.|  

 Zie voor meer informatie de sectie 'Hoe te implementeren van een Takenreeks,' in de Configuration manager Documentation Library die met Configuration Manager is geïnstalleerd.  

###  <a name="StartTargetComputerTaskSequenceMedia"></a>Stap 6-4: Start de doelcomputer met opstartbare Media voor de Takenreeks  
 Start de doelcomputer (WDG-CLI-01) met opstartbare media voor de takenreeks eerder in het proces hebt gemaakt. Dit medium wordt Windows PE gestart op de referentiecomputer en start het proces MDT. Windows 8.1 wordt aan het einde van het proces MDT geïmplementeerd op de doelcomputer.  

> [!NOTE]
>  U kunt ook de MDT-proces starten door het starten van de doelcomputer vanaf de Windows Deployment Services.  

#### <a name="to-start-the-target-computer-with-the-task-sequence-bootable-media"></a>Starten van de doelcomputer met opstartbare media voor de takenreeks

1.  CLI-01-WDG beginnen met opstartbare media voor de takenreeks eerder in het proces hebt gemaakt.  

     Windows PE wordt gestart en vervolgens de Wizard Takenreeks wordt gestart.  

2.  Voltooi de Wizard Takenreeks met behulp van de volgende informatie. Accepteer de standaardwaarden tenzij anders vermeld.  

    |**Op deze wizardpagina**|**Dit doet**|  
    |-|-|      
    |**Welkom bij de Wizard Takenreeks**|In **wachtwoord**, type  **P@ssw0rd** , en klik vervolgens op **volgende**.|  
    |**Selecteer een Takenreeks**|Selecteer in de keuzelijst **Windows 8.1 Doelimplementatie**, en klik vervolgens op **volgende**.|  

#### <a name="to-monitor-the-reference-computer-deployment-process-using-the-deployment-workbench"></a>Het implementatieproces van de verwijzing naar computer met behulp van de implementatie-Workbench bewaken

1.  Klik op WDG-MDT-01 **Start**, en wijs vervolgens **alle programma's**. Wijs **Microsoft Deployment Toolkit**, en klik vervolgens op **implementatie-Workbench**.  

2.  In de consolestructuur van de implementatie-Workbench gaat u naar de implementatie Workbench/implementatie Shares/MDT-Implementatieshare (C:\DeploymentShare$)/Monitoring.  

3.  In het deelvenster met details weergeven het implementatieproces voor **CLI-01-WDG**.  

4.  Klik in het deelvenster Acties periodiek op **vernieuwen**.  

     De status van het implementatieproces is bijgewerkt in het detaildeelvenster. Blijven volgen het implementatieproces totdat het proces voltooid is.  

5.  Klik in het detailvenster op **CLI-01-WDG**.  

6.  Klik in het deelvenster Acties op **eigenschappen**.  

     De **WDG-CLI-01-eigenschappen** in het dialoogvenster wordt weergegeven.  

7.  In de **WDG-CLI-01-eigenschappen** in het dialoogvenster op de **identiteit** tabblad, de controle-informatie gegeven over het implementatieproces, zoals beschreven in de volgende tabel bekijken:

    |**Informatie**|**Beschrijving**|  
    |-|-|  
    |**ID**|De unieke id voor de computer wordt geïmplementeerd.|  
    |**Computernaam**|De naam van de computer wordt geïmplementeerd.|  
    |**Implementatiestatus**|De huidige status van de computer wordt geïmplementeerd; de status kan een van de volgende zijn:<br /><br /> -   **Met**. De takenreeks is in orde en wordt uitgevoerd.<br />-   **Kan geen**. De takenreeks is mislukt en het implementatieproces is mislukt.<br />-   **Voltooid**. De takenreeks is voltooid.<br />-   **Niet-reagerende**. De takenreeks heeft de status ervan niet bijgewerkt in de afgelopen vier uur en wordt ervan uitgegaan dat niet meer reageert.|  
    |**Stap**|De huidige takenreeksstap wordt uitgevoerd.|  
    |**Voortgang**|De algemene voortgang van de takenreeks wordt uitgevoerd. De voortgangsbalk geeft aan hoeveel takenreeksstappen van het totale aantal met takenreeksstappen zijn uitgevoerd.|  
    |**Start**|De tijd die het implementatieproces gestart.|  
    |**Einde**|De tijd die het implementatieproces is beëindigd.|  
    |**Verstreken**|Hoe lang het implementatieproces actief is geweest of duurde om uit te voeren als de implementatie is voltooid.|  
    |**Fouten**|Het aantal fouten zijn opgetreden tijdens het implementatieproces.|  
    |**Waarschuwingen**|Het aantal waarschuwingen aangetroffen tijdens het implementatieproces.|  
    |**Extern bureaublad**|Deze knop kunt u extern bureaublad verbinding te maken met de computer wordt geïmplementeerd met behulp van de functie Extern bureaublad van Windows. Deze methode wordt ervan uitgegaan dat:<br /><br /> -Het beoogde besturingssysteem wordt uitgevoerd en ondersteuning voor externe bureaublad is ingeschakeld<br />-   **mstsc.exe** zich in het pad **Opmerking:**  Deze knop wordt altijd weergegeven, maar mogelijk niet tot stand brengen van een extern bureaublad-sessiehost als de bewaakte computer wordt uitgevoerd Windows PE, installatie van het beoogde besturingssysteem niet is voltooid of beschikt niet over de functie Extern bureaublad is ingeschakeld.|  
    |**VM-verbinding**|Deze knop kunt u extern bureaublad verbinding te maken met een virtuele machine in Hyper-V wordt uitgevoerd. Deze methode wordt ervan uitgegaan dat:<br /><br /> -De implementatie wordt uitgevoerd op een virtuele machine waarop Hyper-V<br />-   **vmconnect.exe** bevindt zich in de map %ProgramFiles%\Hyper-V **Opmerking:**  Deze knop wordt weergegeven wanneer ZTIGather.wsf detecteert dat de onderdelen voor Hyper-V-integratie worden uitgevoerd op de bewaakte computer. Anders wordt is deze knop alleen zichtbaar.|  
    |**DaRT extern beheer**|Deze knop kunt u tot stand brengen van een sessie voor extern beheer met de viewer voor extern-functie in de Diagnostics and Recovery Toolkit (DaRT).<br /><br /> Deze methode wordt ervan uitgegaan dat:<br /><br /> -DaRT is geïmplementeerd op de doelcomputer en wordt momenteel uitgevoerd.<br />-   **DartRemoteViewer.exe** bevindt zich in de map %ProgramFiles%\Microsoft DaRT 7\v7 **Opmerking:**  Deze knop wordt weergegeven wanneer ZTIGather.wsf detecteert dat DaRT wordt uitgevoerd op de bewaakte computer. Anders wordt is deze knop alleen zichtbaar.|  
    |**Deze informatie om de tien seconden automatisch worden vernieuwd**|Selectievakje die bepaalt of de informatie in het dialoogvenster automatisch wordt vernieuwd. Als het selectievakje is:<br /><br /> -Geselecteerd, de gegevens worden vernieuwd elke 10 seconden<br />-Uitgeschakeld, de informatie is niet automatisch vernieuwd en moet handmatig vernieuwen met behulp van de **nu vernieuwen** knop|  
    |**Nu vernieuwen**|Deze knop wordt onmiddellijk vernieuwd voor de informatie die wordt weergegeven in het dialoogvenster.|  

8.  In de **WDG-REF-01-eigenschappen** in het dialoogvenster, klikt u op **OK**.  

9. Sluit de implementatie-Workbench.  

#### <a name="to-monitor-the-reference-computer-deployment-process-using-the-get-mdtmonitordata-cmdlet"></a>Voor het bewaken van het implementatieproces van de verwijzing naar computer met de cmdlet Get-MDTMonitorData

1.  Klik op WDG-MDT-01 **Start**, wijs **Systeembeheer**, en klik vervolgens op **Windows PowerShell-Modules**. Hiermee opent u de opdrachtprompt van Windows PowerShell-Modules.  

2.  Maken van een PowerShell-station dat gebruikmaakt van de MDT-PowerShell-provider door het uitvoeren van de [nieuw PSDrive](http://technet.microsoft.com/library/hh849829.aspx) cmdlet zoals weergegeven in het volgende voorbeeld:  

    ```  
    New-PSDrive -Name DS001 -PSProvider mdtprovider -Root d:\DeploymentShare$  
    ```  

3.  Weergeven van de MDT bewakingsproces door het uitvoeren van de **Get-MDTMonitorData** cmdlet zoals weergegeven in het volgende voorbeeld:  

    ```  
    Get-MDTMonitorData -Path DS001:  
    ```  

     Deze opdracht retourneert de bewakingsgegevens verzameld door de MDT-service wordt uitgevoerd op dezelfde computer die als host fungeert de implementatieshare zoals weergegeven in de volgende voorbeelduitvoer bewaking:  

    ```  
    Name               : WDG-REF-01  
    PercentComplete    : 96  
    Settings           :  
    Warnings           : 0  
    Errors             : 0  
    DeploymentStatus   : 1  
    StartTime          : 6/7/2012 6:45:39 PM  
    EndTime            :   
    ID                 : 1  
    UniqueID           : 94a0830e-f2bb-421c-b1e0-6f86f9eb9fa1  
    CurrentStep        : 130  
    TotalSteps         : 134  
    StepName           : Gather  
    LastTime           : 6/7/2012 8:46:32 PM  
    DartIP             :  
    DartPort           :  
    DartTicket         :  
    VMHost             : XYL-DC-02  
    VMName             : WDG-REF-01  
    ComputerIdentities : {}  

    Name               : WDG-CLI-01  
    PercentComplete    : 26  
    Settings           :  
    Warnings           : 0  
    Errors             : 0  
    DeploymentStatus   : 1  
    StartTime          : 6/7/2012 3:07:13 AM  
    EndTime            :   
    ID                 : 2  
    UniqueID           : 94a0830e-f2bb-421c-b1e0-6f86f9eb9fa1  
    CurrentStep        : 49  
    TotalSteps         : 134  
    StepName           : Capture Network Settings using MDT  
    LastTime           : 6/7/2012 3:08:32 AM  
    DartIP             :  
    DartPort           :  
    DartTicket         :  
    VMHost             :   
    VMName             :   
    ComputerIdentities : {}  
    ```  

4.  Sluit de Windows PowerShell-console.  

 Als er problemen tijdens de implementatie optreden, raadpleegt u het document MDT *probleemoplossing verwijzing*. Als voltooid, wordt de doelcomputer een besturingssysteem Windows 8.1 is geconfigureerd als de referentiecomputer uitgevoerd.
