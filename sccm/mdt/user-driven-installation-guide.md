---
title: "Snel starten - installatie door gebruikers geïnitieerde"
titleSuffix: Microsoft Deployment Toolkit
description: "Een guiide snel starten voor het gebruik van Microsoft Deployment Toolkit voor de installatie door gebruikers geïnitieerde. "
ms.date: 09/09/2016
ms.prod: configuration-manager
ms.technology: configmgr-osd
ms.topic: article
ms.assetid: dcddc250-9361-4e69-af45-472da4ef5fd5
author: aczechowski
ms.author: aaroncz
manager: angrobe
ms.openlocfilehash: 56d65db90e87e67cb3d0dcdd3224206444d44888
ms.sourcegitcommit: 645cd5a324bdd299906efa27eaca5885eafc9e9c
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 01/16/2018
---
# <a name="quick-start-guide-for-user-driven-installation"></a>Snelstartgids voor de installatie door gebruikers geïnitieerde  
 Microsoft Deployment Toolkit (MDT) 2013 biedt technologie voor het implementeren van Windows-besturingssystemen en Microsoft Office. Deze snelstartgids kunt u snel verkorte, stapsgewijze instructies voor het gebruik van het besturingssysteem Windows 8.1 en Microsoft Office Professional Plus 2010 installeren met UDI (User Driven installatie) en Microsoft geëvalueerd MDT 2013 System Center 2012 R2 Configuration Manager. Deze snelstartgids demonstreert hoe u het implementatiescenario voor de nieuwe Computer MDT die bevat informatie over de implementatie van Windows 8.1 naar een andere computer uitvoeren. Dit scenario wordt ervan uitgegaan dat er is geen gebruikersgegevens of profiel behouden.  

> [!NOTE]
>  In dit document, *Windows* geldt voor de besturingssystemen Windows 8.1, Windows 8, Windows 7, Windows Server® 2012 R2, Windows Server 2012 en Windows Server 2008 R2, tenzij anders vermeld. MDT biedt geen ondersteuning voor ARM-processor gebaseerde versies van Windows. Op deze manier *MDT* verwijst naar MDT 2013, tenzij anders vermeld.  

 Bekijk na het evalueren van MDT met behulp van deze handleiding, de rest van de MDT-richtlijnen voor meer informatie over geavanceerde functies van de technologie.  

> [!NOTE]
>  De hier beschreven infrastructuur-instellingen is voor evaluatiedoeleinden gebruikt en niet bedoeld voor een productiesysteem.  

## <a name="prerequisites"></a>Vereisten  
 UDI installaties met System Center 2012 R2 Configuration Manager hebben de volgende vereisten.  

### <a name="required-software"></a>Vereiste Software  
 De volgende software is vereist voor het voltooien van deze handleiding:  

-   Windows Server 2008 R2  

-   Microsoft SQL Server® 2008 R2  

-   SQL Server 2008 R2 servicepack 1 (SP1)  

-   SQL Server 2008 R2 SP1 en cumulatieve Update 6 (cu6 ondersteund)  

-   Windows 8.1  

-   System Center 2012 R2 Configuration Manager  

-   Office Professional Plus 2010 volumelicentie, 32-bits versie  

-   Microsoft .NET Framework versie 3.5 met SP1  

-   Windows PowerShell™ versie 2.0  

-   Windows Preinstallation Environment (Windows PE), die is opgenomen in Configuration Manager  

-   Netwerkservices, inclusief System DNS (Domain Name) en Dynamic Host Configuration Protocol (DHCP)  

-   Actieve Directory® Domain Services (AD DS)  

> [!NOTE]
>  De Taaksequencer gebruikt voor implementaties van MDT is vereist dat het maken van globale Object recht worden toegewezen aan de referenties die worden gebruikt voor toegang tot en het uitvoeren van de Workbench-implementatie en het implementatieproces. Dit recht is normaal gesproken beschikbaar voor accounts met machtigingen op Administrator-niveau (tenzij expliciet worden verwijderd). Ook beveiliging gespecialiseerde – beveiligingsprofiel beperkte functionaliteit (SSLF) Hiermee verwijdert u het recht globale objecttoegang maken en moet niet worden toegepast op computers met MDT geïmplementeerd.  

### <a name="computer-configuration"></a>Computerconfiguratie  
 Voor het voltooien van deze handleiding, de computers die worden vermeld in tabel 1 instellen. Deze computers kunnen zijn voor fysieke computers of virtuele machines (VM's) met de systeembronnen die is aangewezen.  

### <a name="table-1-computers-used-in-this-guide"></a>Tabel 1. Computers die worden gebruikt in deze handleiding  

|**Computer** |**Beschrijving en de systeembronnen** |  
|-|-|  
|MDT-01-WDG|Deze computer wordt uitgevoerd voor de infrastructuur van de MDT en Configuration Manager. De computer wordt uitgevoerd van Windows Server 2008 R2 met de volgende netwerkservices geïnstalleerd:<br /><br /> -AD DS<br />-DNS-Server<br />-DHCP-Server<br />-De Windows Deployment Services<br /><br /> De resources van de computer zijn als volgt:<br /><br /> -Quad core-processor van 2,66 GHz (gigahertz) of sneller uitgevoerd<br />-4 gigabyte (GB) of meer fysiek geheugen<br />-Een schijfpartitie met 40 GB of meer van de beschikbare schijfruimte; Deze worden de partitie van station C<br />-Een CD-ROM of dvd-station dat de stationsletter D wordt toegewezen<br />-Een schijfpartitie met 40 GB of meer van de beschikbare schijfruimte; Deze worden partitie E.|  
|WDG-REF-01|Dit is de referentiecomputer die wordt uitgevoerd geen huidige besturingssysteem. De resources van de computer zijn als volgt:<br /><br /> -Processor met 1,4 GHz of sneller<br />-1 GB of meer fysiek geheugen<br />-16 GB of meer van de beschikbare schijfruimte|  
|CLI-01-WDG|Dit is de doelcomputer en dat er geen huidige besturingssysteem wordt uitgevoerd. De resources van de computer zijn als volgt:<br /><br /> -Processor met 1,4 GHz of sneller<br />-1 GB of meer fysiek geheugen<br />-16 GB of meer van de beschikbare schijfruimte|  

 De bronnen in tabel 1 weerspiegelen de systeembronnen aanbevolen om uit te voeren van de stappen in deze handleiding. Voor informatie over de minimale systeemvereisten met resource voor:  

-   WindowsServer 2008 R2, Zie [installeren van Windows Server 2008 R2](http://technet.microsoft.com/library/dd379511\(WS.10\).aspx)  

-   SQL Server 2008 R2 Zie [Hardware- en softwarevereisten voor het installeren van SQL Server 2008 R2](http://technet.microsoft.com/library/ms143506.aspx)  

> [!NOTE]
>  Deze handleiding wordt ervan uitgegaan dat MDT wordt geëvalueerd op 64-bits (x 64) fysieke of virtuele computers. Als de evaluatie MDT op 32-bits (x 86) platforms, downloaden en installeren de x86-edities van MDT en de onderdelen die in deze handleiding worden beschreven.  

## <a name="step-1-prepare-the-prerequisite-infrastructure"></a>Stap 1: De vereiste infrastructuur voorbereiden  
 Voor de doeleinden van deze handleiding, alle de vereiste infrastructuur-services worden uitgevoerd op de computer met de naam *MDT-01-WDG*. De vereiste software, serverfuncties en -services op deze computer installeren voordat u MDT installeert.  

> [!NOTE]
>  Deze sectie wordt ervan uitgegaan dat u een nieuwe Configuration Manager-infrastructuur voor MDT maakt. Als u van een bestaande Configuration Manager-infrastructuur gebruikmaakt, bekijkt u de stappen in deze sectie en vervang bestaande resourcenamen voor de resources die zijn gemaakt in deze sectie (zoals de computernaam en gedeelde mappen). Bekijk deze sectie gaat u verder met [stap 2: De MDT-omgeving voorbereiden](#PreparetheMDTEnvironment)  

 De vereiste infrastructuur voorbereiden voordat u MDT door installeert:  

-   Windows Server 2008 R2 installeren zoals is beschreven in [stap 1-1: Installeer Windows Server 2008 R2](#InstallWindowsServer2008)  

-   Maken van de vereiste mappen en netwerk deelt, zoals beschreven in [stap 1-2: De vereiste mappen maken en netwerkshares](#CreatetheRequiredFoldersandNetworkShares)  

-   Het verkrijgen van de software nodig voor het uitvoeren van de stappen in deze handleiding, zoals beschreven in [stap 1-3: De vereiste Software verkrijgen](#ObtaintheRequiredSoftware)  

-   De AD DS-serverrol installeren zoals is beschreven in [stap 1-4: De AD DS-serverfunctie installeren](#InstalltheADDSServerRole)  

-   De DHCP-serverfunctie installeren zoals is beschreven in [stap 1-5: De DHCP-serverfunctie installeren](#InstalltheDHCPServerServerRole)  

-   De serverfunctie Web Services (IIS) installeren zoals is beschreven in [stap 1-6: De serverfunctie Web Services (IIS) installeren](#InstalltheWebServicesServerRole)  

-   Toevoegen van de vereiste onderdelen voor Windows Server 2008 R2, zoals beschreven in [stap 1-7: De vereiste Windows Server 2008 R2-onderdelen toevoegen](#AddtheRequiredWindowsServer2008Features)  

-   Maken van de gebruikers- en serviceaccounts vereist voor het uitvoeren van de stappen in deze handleiding, zoals wordt beschreven [stap 1-8: Maak de gebruiker vereist en serviceaccounts](#CreatetheRequiredUserandServiceAccounts)  

-   Installatie van SQL Server 2008 R2 voor Configuration Manager te gebruiken zoals beschreven in [stap 1-9: Installeer SQL Server 2008 R2](#InstallSQLServer2008)  

-   De siteserver toevoegen aan de beveiligingsgroep Administrators, zoals beschreven in [stap 1-10: De siteserver toevoegen aan de beveiligingsgroep Administrators](#AddtheSiteServertotheAdministratorsSecurityGroup)  

-   Installeren van Configuration Manager, zoals beschreven in [stap 1-11: Configuration Manager installeren](#InstallConfigurationManager)  

-   Configureren van het netwerktoegangsaccount die Configuration Manager-clients gebruiken voor toegang tot distributiepunten van Configuration Manager verwijst, zoals beschreven in [stap 1-12: Het netwerktoegangsaccount configureren](#ConfiguretheNetworkAccessAccount)  

-   De Configuration Manager-sitegrenzen en grensgroepen configureren zoals beschreven in [stap 1-13: De Configuration Manager-Sitegrenzen en Grensgroepen configureren](#ConfiguretheConfigurationManagerSiteBoundaries)  

-   Het publiceren van site-informatie in AD DS en DNS configureren zoals beschreven in [stap 1-14: Het publiceren van Site-informatie in AD DS en DNS configureren](#ConfigurethePublishingofSiteIntofrmation)  

-   Configuratie van detectie van gebruikers in AD DS, zoals beschreven in [stap 1-15: Configuratie van detectie van Active Directory-gebruikers](#ConfigureDiscoveryofActiveDirectoryUsers)  

###  <a name="InstallWindowsServer2008"></a>Stap 1-1: Installeer Windows Server 2008 R2  
 Gebruik de informatie in 2 Windows Server 2008 R2 installeren. Accepteer de standaardwaarden tenzij anders vermeld.  

### <a name="table-2-information-for-installing-windows-server-2008-r2"></a>Tabel 2. Informatie voor het installeren van Windows Server 2008 R2  

|**Als u wordt gevraagd** |**Deze waarden opgeven** |  
|-|-|  
|**Waar wilt u Windows installeren?** |**Schijf 0 niet-toegewezen ruimte** |  
|**Wachtwoord** |Een sterk wachtwoord|  
|**Computernaam** |**MDT-01-WDG** |  
|**De notatie voor de volumes C en E** |**NTFS** |  
|**TCP/IP-configuratie** |Met een statische IP-adresconfiguratie, met de andere TCP/IP-configuratieopties voor de omgeving configureren|  

###  <a name="CreatetheRequiredFoldersandNetworkShares"></a>Stap 1-2: De vereiste mappen maken en netwerkshares  
 Het implementatieproces MDT vereist aanvullende mappen die worden gebruikt als bron voor bestanden of bestanden die zijn gemaakt tijdens het implementatieproces MDT op te slaan. Sommige van deze mappen moet worden gedeeld, zodat deze toegankelijk is vanaf andere computers.  

 **De vereiste mappen en shares te maken**  

1.  De mappen en shares die worden vermeld in tabel 3 met de machtigingen die zijn opgegeven voor elke bestandsshare maken  

    ### <a name="table-3-folders-that-the-mdt-deployment-process-requires"></a>Tabel 3. Mappen waarvoor de MDT-implementatieproces  

    |**Deze map maken** |**Met deze sharenaam** |**Met deze machtigingen voor delen** |  
    |-|-|-|  
    |E:\Source$|Bron$|**Beheerders**: Mede-eigenaar<br /><br /> **Iedereen**: Lezen|  
    |E:\Images$|Installatiekopieën$|**Beheerders**: Mede-eigenaar<br /><br /> **Iedereen**: Lezen|  
    |E:\Capture$|$ Vastleggen|**Beheerders**: Mede-eigenaar<br /><br /> **Iedereen**: Lezen|  
    |E:\Packages$|Pakketten$|**Beheerders**: Mede-eigenaar<br /><br /> **Iedereen**: Lezen|  

2.  Maak de volgende mappen:  

    -   E:\CMDownloads  

    -   E:\Source$\CustomSettings  

    -   E:\Source$\Drivers  

    -   E:Source$ Windows_8-1  

    -   E:Source$ MDT_2013  

    -   E:Source$ SQL2008R2  

    -   E:Source$ SQL2008R2SP1  

    -   E:Source$ SQL2008R2CU6  

    -   E:Source$ OfficeProPlus2010  

    -   E:Source$ ConfigMgr  

    -   E:Packages$ stuurprogramma 's  

3.  Kopieer de apparaatstuurprogramma's voor de referentiecomputer (WDG-REF-01) en de doelcomputer (WDG-CLI-01) naar E:\Source$\Drivers.  

    > [!NOTE]
    >  De processen in deze handleiding wordt ervan uitgegaan dat de referentiecomputer en de doelcomputer de dezelfde apparaten hebben en geen stuurprogramma's voor verschillende apparaten vereisen.  

###  <a name="ObtaintheRequiredSoftware"></a>Stap 1-3: De vereiste Software verkrijgen  
 Naast Windows Server 2008 R2, Windows 8.1-en System Center 2012 R2 Configuration Manager, worden bepaalde software is vereist voor evaluatie van MDT op basis van de processen in deze handleiding. Tabel 4 geeft een lijst van de software nodig voor het uitvoeren van implementaties met MDT, waar u kunt de software te verkrijgen en waar u de software op de MDT-01-WDG plaatsen.  

### <a name="table-4-additional-software-required-for-deployment-using-mdt"></a>Tabel 4. Aanvullende Software vereist voor MDT-implementatie  

|**Deze software verkrijgen** |**In deze map te plaatsen** |  
|-|-|  
|MDT 2013|E:\Source$\MDT_2013|  
|Windows 8.1 distributiebestanden van de productmedia|E:\Source$\Windows_8-1|  
|Apparaatstuurprogramma's vereist zijn voor de referentie- en doelcomputers computers (WDG-REF-01 en CLI-01-WDG)|E:\Source$\Drivers|  
|SQL Server 2008 R2 van de productmedia|E:\Source$\SQL2008|  
|SQL Server 2008 R2 SP1, beschikbaar op [http://www.microsoft.com/download/en/details.aspx?id=26727](http://www.microsoft.com/download/en/details.aspx?id=26727)|E:\Source$\SQL2008R2SP1|  
|SQL Server 2008 R2 SP1 cu6 ondersteund, beschikbaar op [http://support.microsoft.com/kb/2679367](http://support.microsoft.com/kb/2679367)|E:\Source$\SQL2008R2SP1CU6|  
|System Center 2012 R2 Configuration Manager van de productmedia|E:\Source$\ConfigMgr|  
|Office Professional Plus 2010 32-bits Volume Licensing-versie van de productmedia|E:\ Bron$ \OfficeProPlus2010|  

###  <a name="InstalltheADDSServerRole"></a>Stap 1-4: De AD DS-serverfunctie installeren  
 AD DS is vereist voor verificatie en fungeren als een opslagplaats voor configuratiewaarden voor de Microsoft-producten en technologieën die gebruikmaakt van MDT, zoals Microsoft SQL Server en Configuration Manager.  

 AD DS wilt installeren, moet u de DCPROMO-Wizard voor het configureren van de computer als een domeincontroller uitvoeren. Installeer AD DS met behulp van de informatie in de tabel 5, de standaardinstellingen accepteren, tenzij anders vermeld.  

### <a name="table-5-information-for-installing-ad-ds"></a>Tabel 5. Informatie voor het installeren van AD DS  

|**Als u wordt gevraagd** |**Dit doet** |  
|-|-|  
|Voor het domeintype|Een nieuw domein in een nieuw forest maakt.|  
|Voor de volledig gekwalificeerde domeinnaam|Type **mdt2013.corp.woodgrovebank.com**.|  
|Voor het functionele forestniveau|Selecteer **Windows Server 2008 R2.** |  
|De DNS-Server-service installeren als onderdeel van het installatieproces van domeincontroller|Klik op **Ja**.|  

###  <a name="InstalltheDHCPServerServerRole"></a>Stap 1-5: De DHCP-serverfunctie installeren  
 De serverfunctie DHCP-Server is vereist voor het bieden van automatische IP-configuratie voor de doelcomputers. Gebruik de informatie in tabel 6, de standaardinstellingen accepteren, tenzij anders opgegeven DHCP-Server installeren.  

> [!NOTE]
>  Als u van een gevirtualiseerde omgeving gebruikmaakt, uitschakelen DHCP-configuratie met de virtualisatiesoftware op de computer. Zorg ervoor dat de MDT-01-WDG met DHCP-Server-service de enige provider van IP-configuratie met behulp van DHCP.  

### <a name="table-6-information-for-installing-the-dhcp-server-server-role"></a>Tabel 6. Informatie voor het installeren van de DHCP-serverfunctie  

|**Op deze wizardpagina** |**Dit doet** |  
|-|-|  
|**DHCP-server in Active Directory autoriseren** |WDG-MDT-01 voor client-IP-configuratie toestaan.|  
|**DHCP-scopes** |Maak een juiste scope die kan worden gebruikt om automatisch te configureren TCP/IP voor WDG-REF-01 en WDG-CLI-01.|  
|**Configuratie van stateless DHCPv6** |Uitschakelen van stateless DHCPv6-modus voor deze server.|  

###  <a name="InstalltheWebServicesServerRole"></a>Stap 1-6: De serverfunctie Web Services (IIS) installeren  
 De serverfunctie Web Services (IIS) met de functieservices die worden vermeld in tabel 7, die nodig voor SQL Server 2008 R2 en Configuration Manager zijn installeert. Tenzij anders vermeld, moet u de standaardwaarden gebruikt.  

### <a name="table-7-information-for-installing-the-web-services-iis-server-role"></a>Tabel 7. Informatie voor het installeren van de serverfunctie Web Services (IIS)  

|**Functieservice** |**Status** |  
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

###  <a name="AddtheRequiredWindowsServer2008Features"></a>Stap 1-7: De vereiste Windows Server 2008 R2-onderdelen toevoegen  
 Naast het installeren van de vereiste functies voor Windows Server 2008 R2-server, voeg de volgende vereiste onderdelen in Serverbeheer in de **Functieoverzicht** sectie:  

-   Background Intelligent Transfer Service  

-   Externe differentiële compressie  

###  <a name="CreatetheRequiredUserandServiceAccounts"></a>Stap 1-8: Maak de gebruiker vereist en serviceaccounts  
 Configuration Manager en SQL Server 2008 R2 moet gebruikersaccounts tijdens de installatie. Tabel 8 bevat de informatie die nodig zijn voor het maken van deze accounts.  

### <a name="table-8-information-for-creating-the-required-accounts"></a>Tabel 8. Informatie over het maken van de vereiste Accounts  

|**Dit account maakt** |**Met deze instellingen** |  
|-|-|  
|SQL Server Agent-serviceaccount|1.  In **voornaam**, type **SQL Agent**.<br />2.  In **achternaam**, type **serviceaccount**.<br />3.  In **aanmeldingsnaam van gebruiker**, type **SQLAgent**.<br />4.  In **wachtwoord** en **wachtwoord bevestigen**, type  **P@ssw0rd** .<br />5.  Schakel de **gebruiker moet wachtwoord bij volgende aanmelding wijzigen** selectievakje.<br />6.  Selecteer de **wachtwoord verloopt nooit** selectievakje.<br />7.  Maak het account lid is van de beveiligingsgroep Domeinadministrators.<br />8.  In **beschrijving**, type **-serviceaccount gebruikt SQL Server 2008 R2-Agent-service uit te voeren**.|  
|Database-Engine van SQL Server-serviceaccount|1.  In **voornaam**, type **SQL DB-Engine**.<br />2.  In **achternaam**, type **serviceaccount**.<br />3.  In **aanmeldingsnaam van gebruiker**, type **SQLDBEngine**.<br />4.  In **wachtwoord** en **wachtwoord bevestigen**, type  **P@ssw0rd** .<br />5.  Schakel de **gebruiker moet wachtwoord bij volgende aanmelding wijzigen** selectievakje.<br />6.  Selecteer de **wachtwoord verloopt nooit** selectievakje.<br />7.  Maak het account lid is van de beveiligingsgroep Domeinadministrators.<br />8.  In **beschrijving**, type **-serviceaccount gebruikt voor het uitvoeren van de database-engine van SQL Server 2008 R2**.|  
|SQL Server Reporting Services-serviceaccount|1.  In **voornaam**, type **SQL Reporting**.<br />2.  **In de achternaam**, type **serviceaccount**.<br />3.  In **aanmeldingsnaam van gebruiker**, type **SQLReport**.<br />4.  In **wachtwoord** en **wachtwoord bevestigen**, type  **P@ssw0rd** .<br />5.  Schakel de **gebruiker moet wachtwoord bij volgende aanmelding wijzigen** selectievakje.<br />6.  Selecteer de **wachtwoord verloopt nooit** selectievakje.<br />7.  Maak het account lid is van de beveiligingsgroep Domeinadministrators.<br />8.  In **beschrijving**, type **gebruikt voor het uitvoeren van SQL Server 2008 R2 reporting services-serviceaccount**.|  
|System Center Configuration Manager-Client Network Access account|1.  In **voornaam**, type **CM 2012**.<br />2.  In **achternaam**, type **toegang tot het netwerk van de Client**.<br />3.  In **gebruikersaanmelding** , typt **CMNetAccess**.<br />4.  In **wachtwoord** en **wachtwoord bevestigen**, type  **P@ssw0rd** .<br />5.  Schakel de **gebruiker moet wachtwoord bij volgende aanmelding wijzigen** selectievakje.<br />6.  Selecteer de **wachtwoord verloopt nooit** selectievakje.<br />7.  In **beschrijving**, type **-serviceaccount gebruikt als het netwerktoegangsaccount voor Configuration Manager-Client**.|  

###  <a name="InstallSQLServer2008"></a>Stap 1-9: Installeer SQL Server 2008 R2  
 Voordat u Configuration Manager installeert, installeert u SQL Server 2008 R2 SP1 en cu6 ondersteund.  

> [!NOTE]
>  Als u alle functies van de SQL Server 2008 R2, installeert u de serverfunctie Web Services (IIS) voordat u SQL Server 2008 R2 installeert.  

 **Voor het installeren van SQL Server 2008 R2**  

1.  Start het Installatiecentrum van SQL Server.  

2.  Klik in de SQL Server-installatie Center in het navigatiedeelvenster op **installatie**.  

3.  Klik in het voorbeeldvenster op **nieuwe installatie of functies toevoegen aan een bestaande installatie**.  

     SQL Server 2008 R2-installatiewizard wordt gestart.  

4.  Installeer SQL Server 2008 R2 met behulp van de informatie in de tabel 9, accepteer de standaardwaarden tenzij anders vermeld.  

    ### <a name="table-9-information-for-installing-sql-server-2008-r2"></a>Tabel 9. Informatie voor het installeren van SQL Server 2008 R2  

    |**Op deze wizardpagina** |**Dit doet** |  
    |-|-|  
    |**Setup-Ondersteuningsregels** |Klik op **OK**.|  
    |**Productcode** |Klik op **Volgende**.|  
    |**Licentievoorwaarden** |Selecteer de **ik ga akkoord met de licentievoorwaarden** selectievakje en klik vervolgens op **volgende**.|  
    |**Setup-ondersteuningsbestanden** |Klik op **Installeren**.|  
    |**Setup-Ondersteuningsregels** |Zorg ervoor dat er geen kritieke resultaten bestaan voor de regels en klik vervolgens op **volgende**.|  
    |**Setup-rol** |Klik op **SQL Server Feature Installation**, en klik vervolgens op **volgende**.|  
    |**Functies selecteren** |1.  Selecteer de **Database Engine-Services** selectievakje.<br />2.  Selecteer de **Reporting Services** selectievakje.<br />3.  Selecteer de **zoeken in volledige tekst** selectievakje.<br />4.  Selecteer de **beheerprogramma's - voltooien** selectievakje.<br />5.  Klik op **Volgende**.|  
    |**Installatieregels** |Klik op **Volgende**.|  
    |**De configuratie van exemplaar** |Klik op **Volgende**.|  
    |**Benodigde schijfruimte** |Klik op **Volgende**.|  
    |**Serverconfiguratie** |1.  Voor **SQL Server Agent**in **accountnaam**, type **MDT2013\SQLAgent**in **wachtwoord**, type  **P@ssw0rd** .<br />2.  Voor **SQL Server Database Engine**in **accountnaam**, type **MDT2013\SQLDBEngine**in **wachtwoord**, type  **P@ssw0rd** .<br />3.  Voor **SQL Server Reporting Services**in **accountnaam**, type **MDT2013\SQLReport**in **wachtwoord**, type  **P@ssw0rd** .<br />4.  Klik op **Volgende**.|  
    |**Configuratie van de Database-Engine** |Klik op **huidige gebruiker toevoegen**, en klik vervolgens op **volgende**.|  
    |**Configuratie van Reporting Services** |Klik op **Volgende**.|  
    |**Foutrapportage** |Klik op **Volgende**.|  
    |**Configuratieregels voor installatie** |Klik op **Volgende**.|  
    |**Gereed voor installatie** |Klik op **Installeren**.|  
    |**Voltooien** |Klik op **Sluiten**.|  

5.  Sluit het Installatiecentrum van SQL Server.  

 **Voor het installeren van SQL Server 2008 R2 SP1**  

1.  In Windows Verkenner, Ga naar E:\Source$\SQL2008R2SP1 en dubbelklikt u op **SQLServer2008R2SP1-KB2528583-x64-ENU.exe**.  

     De **uitpakken van bestanden** in het dialoogvenster geeft het proces bestand uitpakken. Wanneer het proces voltooid is, wordt de SQL Server 2008 R2 Service Pack 1 Update installatiewizard gestart.  

2.  Installeer SQL Server 2008 R2 SP1 met behulp van de informatie in de tabel 10, accepteer de standaardwaarden tenzij anders vermeld.  

    ### <a name="table-10-information-for-installing-sql-server-2008-r2-sp1"></a>Tabel 10. Informatie voor het installeren van SQL Server 2008 R2 SP1  

    |**Op deze wizardpagina** |**Dit doet** |  
    |-|-|  
    |**Update van SQL Server 2008 R2** |Klik op **Volgende**.|  
    |**Licentievoorwaarden** |Selecteer de **ik ga akkoord met de licentievoorwaarden** selectievakje en klik vervolgens op **volgende**.|  
    |**Functies selecteren** |Klik op **Volgende**.|  
    |**Controleer de bestanden In gebruik** |Klik op **Volgende**.|  
    |**Gereed om te werken** |Klik op **Update**.|  
    |**Voortgang van bijwerken** |Als de update wordt uitgevoerd en is voltooid, wordt de voortgang van de weergegeven op de wizardpagina.|  
    |**Voltooien** |Klik op **Sluiten**.|  

 **Voor het installeren van SQL Server 2008 R2 SP1 cu6 ondersteund**  

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

6.  Installeer SQL Server 2008 R2 SP1 cu6 ondersteund met de informatie in de tabel 11, accepteer de standaardwaarden tenzij anders vermeld.  

    ### <a name="table-11-information-for-installing-sql-server-2008-r2-sp1-cu6"></a>Tabel 11. Informatie voor het installeren van SQL Server 2008 R2 SP1 cu6 ondersteund  

    |**Op deze wizardpagina** |**Dit doet** |  
    |-|-|  
    |**Update van SQL Server 2008 R2** |Klik op **Volgende**.|  
    |**Licentievoorwaarden** |Selecteer de **ik ga akkoord met de licentievoorwaarden** selectievakje en klik vervolgens op **volgende**.|  
    |**Functies selecteren** |Klik op **Volgende**.|  
    |**Controleer de bestanden In gebruik** |Klik op **Volgende**.|  
    |**Gereed om te werken** |Klik op **Update**.|  
    |**Voortgang van bijwerken** |Als de update wordt uitgevoerd en is voltooid, wordt de voortgang van de weergegeven op de wizardpagina.|  
    |**Voltooien** |Klik op **Sluiten**.|  

     De **een update van SQL Server 2008 R2 installeert** dialoogvenster wordt weergegeven waarin u de computer u voltooit de installatie opnieuw opstarten wordt gevraagd.  

7.  In de **een update van SQL Server 2008 R2 installeert** in het dialoogvenster, klikt u op **OK**.  

8.  Start de computer opnieuw op.  

9. Na de installatie van SQL Server 2008 R2 SP1 cu6 ondersteund, moet het buildnummer voor SQL Server 10.51.2811.0.  

    > [!TIP]
    >  U kunt het buildnummer voor SQL Server controleren door het bekijken van de SQL Server-updates toegepast in de programma's en onderdelen in het Configuratiescherm item door te klikken op **geïnstalleerde updates weergeven**.  

###  <a name="AddtheSiteServertotheAdministratorsSecurityGroup"></a>Stap 1-10: De siteserver toevoegen aan de beveiligingsgroep Administrators  
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

###  <a name="InstallConfigurationManager"></a>Stap 1-11: Configuration Manager installeren  
 Wanneer de andere producten en technologieën hebt geïnstalleerd, installeert Configuration Manager. Voordat u dit doet, echter uitbreiden Active Directory-schema zodat computers de distributiepunten, service-locator verwijst en andere serverfuncties vinden kunnen. Nadat u de Configuration Manager hebt geïnstalleerd, kunt u ook het schema uitbreiden. Zie de sectie 'Breid het Active Directory-Schema' in de Documentatiebibliotheek van Configuration Manager, dat geïnstalleerd is met Configuration Manager voor meer informatie over het uitbreiden van het Active Directory-schema voor Configuration Manager.  

 Na het Active Directory-schema uitbreidt, installeert Configuration Manager. De configuratie van de MDT-01-WDG ondersteunt Configuration Manager voor dit voorbeeld. De configuratie van computers in het productienetwerk kan variëren. Zie voor meer informatie over de vereisten voor het installeren van Configuration Manager, [ondersteunde configuraties voor Configuration Manager](http://technet.microsoft.com/library/gg682077.aspx).  

 **Voor het installeren van Configuration Manager**  

1.  Start het welkomstscherm van Setup van System Center 2012 R2 Configuration Manager.  

2.  Klik op het welkomstscherm van Setup van System Center 2012 R2 Configuration Manager op de **installeren** koppeling.  

     De Wizard Microsoft System Center 2012 R2 Configuration Manager Setup wordt gestart.  

3.  Voltooi de Wizard Microsoft System Center 2012 R2 Configuration Manager Setup van de informatie in de tabel 12. Accepteer de standaardwaarden tenzij anders vermeld.  

    ### <a name="table-12-information-for-installing-configuration-manager"></a>Tabel 12. Informatie voor het installeren van Configuration Manager  

    |**Op deze wizardpagina** |**Dit doet** |  
    |-|-|  
    |**Voordat u begint** |Klik op **Volgende**.|  
    |**Aan de slag** |Klik op **Volgende**.|  
    |**Productcode** |In **Voer uw productcode van 25 tekens**, type ***productcode*** (waarbij *productcode* uw productcode is voor Configuration Manager).|  
    |**Licentievoorwaarden voor Microsoft-Software** |Selecteer de **ik aanvaard deze licentievoorwaarden** selectievakje en klik vervolgens op **volgende**.|  
    |**Vereiste onderdelen bijwerken** |In **downloaden en gebruiken van de meest recente updates. Updates worden opgeslagen op de volgende locatie**, type **E:\CMDownloads**, en klik vervolgens op **volgende**.|  
    |**Selectie van servertaal** |Klik op **Volgende**.|  
    |**Clienttaal** |Klik op **Volgende**.|  
    |**Site- en installatie-instellingen** |1.  In **sitecode**, type **NYC**.<br />2.  In **sitenaam**, type **New York City Site**.<br />3.  Klik op **Volgende**.|  
    |**Primaire Site-installatie** |1.  Klik op **de primaire site installeren als een zelfstandige site**.<br />2.  Klik op **Volgende**.<br />     De **Configuration Manager** dialoogvenster wordt weergegeven, waarin wordt bevestigd dat u wilt deze site installeren als een zelfstandige site.<br />3.  In de **Configuration Manager** in het dialoogvenster, klikt u op **Ja**.|  
    |**Database-informatie** |Klik op **Volgende**.|  
    |**SMS-Providerinstellingen** |Klik op **Volgende**.|  
    |**Communicatie-instellingen voor clientcomputer** |Klik op **communicatiemethode configureren voor elke sitesysteemrol**, en klik vervolgens op **volgende**.|  
    |**Sitesysteemrollen** |Klik op **Volgende**.|  
    |**Configuratie voor programma voor kwaliteitsverbetering** |Selecteer de juiste deelname aan het programma voor kwaliteitsverbetering voor uw organisatie en klik vervolgens op **volgende**.|  
    |**Samenvatting van instellingen** |Klik op **Volgende**.|  
    |**Controle van vereisten** |Klik op **installatie begint**.|  
    |**Installeren** |Controleren van het installatieproces totdat deze is voltooid en klik vervolgens op **sluiten**.|  

4.  Sluit alle geopende vensters en dialoogvensters.  

 Wanneer de wizard voltooid is, wordt Configuration Manager is geïnstalleerd.  

###  <a name="ConfiguretheNetworkAccessAccount"></a>Stap 1-12: Het netwerktoegangsaccount configureren  
 De Configuration Manager-client moet een account om uw referenties bij het openen van de Configuration Manager-distributiepunten, implementatieshares MDT en gedeelde mappen. Dit account heet de *netwerktoegangsaccount*. Het account CMNetAccess is eerder in het proces om te gebruiken als het account toegang tot het netwerk gemaakt.  

 **Het netwerktoegangsaccount configureren**  

1.  Klik op **Start**, wijs **alle programma's**, en wijs vervolgens **Microsoft System Center 2012**. Wijs **Configuration Manager**, en klik vervolgens op **Configuration Manager-Console**.  

2.  Klik in de Configuration Manager-console in het navigatievenster op **beheer**.  

3.  Ga naar overzicht/Configuration/Sites Site in de werkruimte beheer.  

4.  Klik in het voorbeeldvenster op **NYC - New York City Site**.  

5.  Klik op het lint op **instellingen**, klikt u op **Siteonderdelen configureren**, en klik vervolgens op **softwaredistributie**.  

6.  In de **distributie-eigenschappen van Software** in het dialoogvenster, klikt u op de **netwerktoegangsaccount** tabblad.  

7.  In **netwerktoegangsaccount**, klikt u op **de account opgeven die toegang netwerklocaties tot**, klikt u op **ingesteld**, en klik vervolgens op **nieuwe Account**.  

     De **Windows-gebruikersaccount** dialoogvenster wordt weergegeven.  

8.  Voltooi de **Windows-gebruikersaccount** in het dialoogvenster met de informatie in de tabel 13 en klik vervolgens op **OK**.  

    ### <a name="table-13-information-required-to-complete-the-windows-user-account-dialog-box"></a>Tabel 13. Informatie voor het dialoogvenster Windows gebruiker Account  

    |**Voor deze** |**Dit doet** |  
    |-|-|  
    |**Gebruikersnaam** |Type **MDT2013\CMNetAccess**.|  
    |**Wachtwoord** |Type  **P@ssw0rd** .|  
    |**Wachtwoord bevestigen** |Type  **P@ssw0rd** .|  

9. In de **distributie-eigenschappen van Software** in het dialoogvenster, klikt u op **OK**.  

10. Sluit alle vensters geopend.  

###  <a name="ConfiguretheConfigurationManagerSiteBoundaries"></a>Stap 1-13: De Configuration Manager-Sitegrenzen en Grensgroepen configureren  
 De Configuration Manager-client moet weten de grenzen van de site. Tenzij de grenzen van de site zijn opgegeven, de client wordt verondersteld dat de computer met Configuration Manager op een externe locatie. Toevoegen aan dat de sitegrens van een op basis van het IP-subnet dat MDT-01-WDG, WDG-REF-01 en WDG-CLI-01-gebruik. De sitegrens vervolgens toevoegen aan een sitegrensgroep.  

 **De sitegrens van een Configuration Manager-maken**  

1.  Klik op **Start**, wijs **alle programma's**, en wijs vervolgens **Microsoft System Center 2012**. Wijs **Configuration Manager**, en klik vervolgens op **Configuration Manager-Console**.  

2.  Klik in de Configuration Manager-console in het navigatievenster op **beheer**.  

3.  Ga naar overzicht/hiërarchie Configuration/grenzen in de werkruimte beheer.  

4.  Klik op het lint op **grens maken**.  

     De **grens maken** dialoogvenster wordt geopend.  

5.  Voltooi de **grens maken** in het dialoogvenster met de informatie in de tabel 14 en klik vervolgens op **OK**.  

    > [!NOTE]
    >  Voor dit voorbeeld wordt de sitegrens opgegeven met netwerkadres. U kunt echter ook opgeven met behulp van een AD DS sitegrenzen site-naam of een IP-adresbereik.  

    ### <a name="table-14-information-required-to-complete-the-create-boundary-dialog-box"></a>Tabel 14. Benodigde informatie om te voltooien het dialoogvenster grens maken  

    |**Voor deze** |**Dit doet** |  
    |-|-|  
    |**Beschrijving** |Type **IP-Subnetgrens**.|  
    |**Type** |Selecteer **IP-subnet**.|  
    |Netwerk|Type ***network_address*** (waarbij *network_address* is het netwerkadres van het subnet waarop de computers zijn geïnstalleerd).|  
    |**Subnetmasker** |Type ***subnet_mask*** (waarbij *subnet_mask* is het subnetmasker van het subnet waarop de computers zijn geïnstalleerd).|  

 **De Configuration Manager-sitegrens toevoegen aan een sitegrensgroep**  

1.  Klik in de Configuration Manager-console in het navigatievenster op **beheer**.  

2.  Ga naar overzicht/hiërarchie Configuration/Grensgroepen in de werkruimte beheer.  

3.  Klik op het lint op **Grensgroep maken**.  

     De **Grensgroep maken** dialoogvenster wordt geopend.  

4.  Voltooi de **algemene** tabblad van de **Grensgroep maken** in het dialoogvenster met de informatie in de tabel 15.  

    ### <a name="table-arabic-15-information-required-to-complete-the-general-tab-of-the-create-boundary-group-dialog-box"></a>Tabel Arabische 15. Gegevens die zijn vereist voor het voltooien van het tabblad Algemeen van het dialoogvenster Grensgroep maken  

    |**Voor deze** |**Dit doet** |  
    |-|-|  
    |**Naam** |Type **New York City Grensgroep**.|  
    |Beschrijving|Type **grensgroep voor de grenzen van de site op de site New York City**.|  
    |**Grenzen** |1.  Klik op **Toevoegen**.<br />     De **toevoegen grenzen** dialoogvenster wordt weergegeven.<br />2.  In de **toevoegen grenzen** dialoogvenster, ***site_boundary*** (waarbij *site_boundary* grens van de site's die u eerder in het proces gemaakt), en klik vervolgens op **OK**.<br />     De sitegrens wordt weergegeven in de lijst met grenzen.|  

5.  Voltooi de **verwijzingen** tabblad van de **Grensgroep maken** in het dialoogvenster met de informatie in de tabel 16 en klik vervolgens op **OK**.  

    ### <a name="table-16-information-required-to-complete-the-references-tab-of-the-create-boundary-group-dialog-box"></a>Tabel 16. Informatie voor de Tab verwijzingen van het dialoogvenster Grensgroep maken  

    |**Voor deze** |**Dit doet** |  
    |-|-|  
    |**Sitetoewijzing** |Selecteer de **deze grensgroep gebruiken voor sitetoewijzing** selectievakje.|  
    |**Locatie van inhoud** |1.  Klik op **Toevoegen**.<br />     De **Sitesystemen toevoegen** dialoogvenster wordt weergegeven.<br />2.  In de **Sitesystemen toevoegen** dialoogvenster,  **\\\WDG-MDT-01.mdt2013.corp.woodgrovebank.com**, en klik vervolgens op **OK**.<br />     De sitesysteemserver wordt weergegeven in de lijst met sitesysteemservers.|  

6.  Sluit alle vensters geopend.  

###  <a name="ConfigurethePublishingofSiteIntofrmation"></a>Stap 1-14: Het publiceren van Site-informatie in AD DS en DNS configureren  
 Configuration Manager-client moet de verschillende serverrollen van de Configuration Manager-vinden. De eigenschappen van de site de site om informatie te publiceren in AD DS en DNS-wijzigen.  

 **Het publiceren van site-informatie in AD DS en in DNS configureren**  

1.  Klik op **Start**, wijs **alle programma's**, en wijs vervolgens **Microsoft System Center 2012**. Wijs **Configuration Manager**, en klik vervolgens op **Configuration Manager-Console**.  

2.  Klik in de Configuration Manager-console in het navigatievenster op **beheer**.  

3.  Ga naar overzicht/Configuration/Sites Site in de werkruimte beheer.  

4.  Klik in het voorbeeldvenster op **NYC - New York City Site**.  

5.  Klik op het lint op **eigenschappen**.  

6.  In de **New York City Site-eigenschappen** in het dialoogvenster op de **Publishing** tabblad, Controleer de **mdt2013.corp.woodgrovebank.com** Active Directory-forest wordt weergegeven, en Klik vervolgens op **annuleren**.  

7.  Sluit alle vensters geopend.  

###  <a name="ConfigureDiscoveryofActiveDirectoryUsers"></a>Stap 1-15: Configuratie van detectie van Active Directory-gebruikers  
 In sommige gevallen wordt de software worden geïmplementeerd op verzamelingen van gebruikers die detecteert de Configuration Manager. Configuration Manager kunt gebruikersaccounts detectie opgeslagen in AD DS met behulp van de methode Active Directory-Gebruikersdetectie.  

 **Detectie van Active Directory-gebruikers te configureren**  

1.  Klik op **Start**, wijs **alle programma's**, en wijs vervolgens **Microsoft System Center 2012**. Wijs **Configuration Manager**, en klik vervolgens op **Configuration Manager-Console**.  

2.  Klik in de Configuration Manager-console in het navigatievenster op **beheer**.  

3.  Ga naar de hiërarchie-overzicht/detectiemethoden gebruiken in de werkruimte beheer.  

4.  Klik in het voorbeeldvenster op **Active Directory-Gebruikersdetectie**.  

5.  Klik op het lint op de **Start** tabblad **eigenschappen**.  

     De **eigenschappen van Active Directory Discovery** dialoogvenster wordt weergegeven.  

6.  In de **eigenschappen van Active Directory Discovery** in het dialoogvenster op de **algemene** tabblad, voert u de volgende stappen uit:  

    1.  Selecteer de **inschakelen Active Directory-Gebruikersdetectie** selectievakje.  

    2.  In **Active Directory-containers**, klikt u op **nieuw**.  

         De **nieuwe Active Directory-Container** in het dialoogvenster wordt weergegeven.  

    3.  In de **nieuwe Active Directory-Container** het dialoogvenster **pad**, klikt u op **Bladeren**.  

         De **nieuwe Container selecteren** dialoogvenster wordt weergegeven.  

    4.  In de **nieuwe Container selecteren** in het dialoogvenster, klikt u op **mdt2013**, en klik vervolgens op **OK**.  

         In de **nieuwe Active Directory-Container** in het dialoogvenster het Lightweight Directory Access Protocol (LDAP)-pad wordt weergegeven in de **pad** vak.  

    5.  In de **nieuwe Active Directory-Container** dialoogvenster op OK.  

     Het LDAP-pad wordt weergegeven in de **Active Directory-containers** keuzelijst met invoervak.  

7.  In de **eigenschappen van Active Directory Discovery** in het dialoogvenster, klikt u op **OK**.  

     De **Configuration Manager** dialoogvenster wordt weergegeven, bij het controleren of u wilt de detectie zo snel mogelijk uitvoeren.  

8.  In de **Configuration Manager** in het dialoogvenster, klikt u op **Ja**.  

9. Klik in de Configuration Manager-console in het navigatievenster op **activa en naleving**.  

10. In de activa en naleving werkruimte, gaat u naar overzicht/gebruikers.  

     De lijst met gebruikers die zijn gedetecteerd in AD DS wordt weergegeven in het voorbeeldvenster.  

11. Sluit alle vensters geopend.  

##  <a name="PreparetheMDTEnvironment"></a>Stap 2: De MDT-omgeving voorbereiden  
 De eerste stap in het implementatieproces is de MDT-omgeving voorbereiden. Als deze stap voltooid is, kunt u de referentiecomputer maken en implementeren van een vastgelegde installatiekopie van het naar de doelcomputer (WDG-CLI-01) met Configuration Manager-integratie met MDT.  

 De MDT-omgeving door voorbereiden:  

-   MDT installeren zoals is beschreven in [stap 2-1: MDT installeren](#InstallMDT)  

-   Integratie van Configuration Manager-console inschakelen door het uitvoeren van de wizard Configuration Manager-integratie configureren zoals beschreven in [stap 2-2: Integratie van Configuration Manager-Console inschakelen](#EnableConfigurationManagerConsoleIntegration)  

###  <a name="InstallMDT"></a>Stap 2-1: MDT installeren  
 Voor installatie MDT, voert u de volgende stappen uit:  

1.  In Windows Verkenner, Ga naar E:\Source$\MDT_2013.  

2.  Dubbelklik op **MicrosoftDeploymentToolkit2013_x64.msi** (voor 64-bits besturingssystemen) of **MicrosoftDeploymentToolkit2013_x86.msi** (voor 32-bits besturingssystemen), en klik vervolgens op **Installeren**.  

     De Microsoft Deployment Toolkit 2013-installatiewizard wordt gestart.  

3.  Voltooi de Microsoft Deployment Toolkit 2013 Setup Wizard met de informatie in de tabel 17. Accepteer de standaardwaarden tenzij anders vermeld.  

    ### <a name="table-17-information-for-completing-the-microsoft-deployment-toolkit-2013-setup-wizard"></a>Tabel 17. Informatie over het voltooien van de Wizard Setup van Microsoft Deployment Toolkit 2013  

    |**Op deze wizardpagina** |**Dit doet** |  
    |-|-|  
    |**Welkom bij de Microsoft Deployment Toolkit 2013-installatiewizard** |Klik op **Volgende**.|  
    |**Gebruiksrechtovereenkomst** |Klik op **ik ga akkoord met de voorwaarden in deze gebruiksrechtovereenkomst**, en klik vervolgens op **volgende**.|  
    |**Aangepaste installatie** |Klik op **Volgende**.|  
    |**Gereed voor installatie van Microsoft Deployment Toolkit 2013** |Klik op **Installeren**.|  
    |**Microsoft Deployment Toolkit 2013 installeren** |De voortgang voor het installeren van MDT wordt weergegeven.|  
    |**De Wizard Setup van Microsoft Deployment Toolkit 2013 voltooid** |Klik op **Voltooien**.|  

 De Wizard Setup van Microsoft Deployment Toolkit 2013 is voltooid en MDT is geïnstalleerd op de MDT-01-WDG.  

###  <a name="EnableConfigurationManagerConsoleIntegration"></a>Stap 2-2: Integratie van Configuration Manager-Console inschakelen  
 Voordat u de Configuration Manager-integratiefuncties van MDT gebruiken kunt, moet u de wizard Configuration Manager-integratie configureren uitvoeren. Deze wizard kopieert de juiste integratie-bestanden naar de map waarin u Configuration Manager is geïnstalleerd. De wizard voegt ook Windows Management Instrumentation (WMI)-klassen voor de nieuwe aangepaste acties in MDT. De klassen worden toegevoegd door het compileren van een nieuw Managed Object Format (MOF) bestand met de nieuwe klassedefinities.  

 **Integratie van Configuration Manager-console inschakelen**  

> [!NOTE]
>  Zorg ervoor dat de Configuration Manager-console is afgesloten tijdens het uitvoeren van deze stappen.  

1.  Klik op **Start**, en wijs vervolgens **alle programma's**. Wijs **Microsoft Deployment Toolkit**, en klik vervolgens op **Configuration Manager-integratie configureren**.  

     De Wizard Configuration Manager-integratie configureren wordt gestart.  

2.  De Wizard configureren voltooit Configuration Manager-integratie met de informatie in de tabel 18. Accepteer de standaardwaarden tenzij anders vermeld.  

    ### <a name="table-18-information-for-completing-the-configure-configmgr-integration-wizard"></a>Tabel 18. Informatie voor het voltooien van de Wizard integratie met Configuration Manager configureren  

    |**Op deze wizardpagina** |**Dit doet** |  
    |-|-|  
    |**Opties** |1.  Controleer de **installeren van de MDT-console-uitbreidingen voor Configuration Manager 2012** selectievakje is ingeschakeld.<br />2.  Controleer de **de MDT-takenreeksacties toevoegen aan een ConfigMgr-server** selectievakje is ingeschakeld.<br />3.  In **siteservernaam**, Controleer of de waarde **WDG-MDT-01.mdt2013.corp.woodgrovebank.com**.<br />4.  In **sitecode**, Controleer of de waarde **NYC**.<br />5.  Klik op **Volgende**.|  
    |**Bevestiging** |Klik op **Voltooien**.|  

 De Wizard Configuration Manager-integratie is voltooid en MDT is geïntegreerd met Configuration Manager.  

## <a name="step-3-create-and-configure-a-task-sequence-to-create-a-reference-computer"></a>Stap 3: Maken en een Takenreeks voor het maken van een referentiecomputer configureren  
 Wanneer u de MDT-omgeving hebt voorbereid, maakt u de referentiecomputer. De referentiecomputer is de sjabloon voor het implementeren van installatiekopieën van het nieuwe op de doelcomputers. Configureer deze computer (WDG-REF-01) precies zoals u de doelcomputers configureert. U wordt vervolgens een installatiekopie van de referentiecomputer en de installatiekopie implementeren op de doelcomputers.  

 Maken van de referentiecomputer WDG-REF-01, door:  

-   Maken van een takenreeks MDT om Windows 8.1 implementeren op de referentiecomputer, zoals beschreven in [stap 3-1: Een Takenreeks MDT maken voor het implementeren van de referentiecomputer](#CreateMDTTaskSequenceforDeployingReferenceComputer)  

-   Als u de distributiepunten voor de nieuwe pakketten en installatiekopieën van de MDT Wizard Takenreeks maken maakt zoals beschreven in [stap 3-2: Selecteer de distributiepunten voor de nieuwe pakketten en installatiekopieën](#SelectDistributionPointsfortheNewPackages)  

-   De benodigde apparaatstuurprogramma's toevoegen voor een nieuw station pakket en de juiste opstartinstallatiekopieën zoals beschreven in [stap 3-3: De benodigde apparaatstuurprogramma's toevoegen](#AddtheNecessaryDeviceDrivers)  

-   Schakel de bewaking van het implementatieproces van MDT, zoals beschreven in [stap 3 en 4: MDT-implementatie in te schakelen procesbewaking](#EnableMDTDeploymentProcessMonitoring)  

-   Configureren van de MDT-configuratiebestanden voor de referentiecomputer, in het bijzonder het CustomSettings.ini-bestand, zoals beschreven in [stap 3-5: Het aanpassen van de MDT-configuratiebestanden voor de referentiecomputer](#CustomizeMDTConfigFilesforReferenceComputer)  

-   Bijwerken van de Configuration Manager-distributiepunten voor het pakket bestanden met aangepaste instellingen, zoals beschreven in [stap 3-6: De distributiepunten voor het pakket met aangepaste instellingen voor bestanden bijwerken](#UpdateDistributionPointsforCustomSettings)  

-   De takenreeks voor de referentiecomputer aanpassen zoals beschreven in [stap 3-7: De Takenreeks voor de referentiecomputer aanpassen](#CustomizeTaskSequenceforReferenceComputer)  

###  <a name="CreateMDTTaskSequenceforDeployingReferenceComputer"></a>Stap 3-1: Een Takenreeks MDT maken voor het implementeren van de referentiecomputer  
 Gebruik de MDT Wizard Takenreeks maken in de Configuration Manager-console voor het maken van takenreeksen in Configuration Manager waarmee zijn geïntegreerd met MDT. MDT bevat de sjabloon standaard Clienttakenreeks die u gebruiken kunt voor het implementeren van de referentiecomputer.  

 De Wizard maken Takenreeks MDT vervangt door de pakketten en installatiekopieën die zijn geselecteerd voor de tijdelijke aanduidingen in de reeks taaksjablonen. Na het voltooien van de wizard verwijst nieuwe takenreeks de juiste pakketten en afbeeldingen.  

> [!NOTE]
>  Gebruik altijd de MDT Wizard Takenreeks maken voor het maken van takenreeksen op basis van de MDT taak reeks sjablonen. Hoewel u de taak reeks sjablonen handmatig importeren kunt, niet wordt aangeraden dit proces.  

 **Maken van een takenreeks voor het implementeren van de referentiecomputer**  

1.  Klik op **Start**, wijs **alle programma's**, en wijs vervolgens **Microsoft System Center 2012**. Wijs **Configuration Manager**, en klik vervolgens op **Configuration Manager-Console**.  

2.  Klik in de Configuration Manager-console in het navigatievenster op **softwarebibliotheek**.  

3.  Ga in de werkruimte softwarebibliotheek naar overzicht/Operating Systems/Takenreeksen.  

4.  Klik op het lint op de **Start** tabblad, in de **Takenreeksen** groep, klikt u op **Takenreeks MDT maken**.  

     De MDT Wizard Takenreeks maken wordt gestart.  

5.  De MDT Wizard Takenreeks maken met de informatie in de tabel 19 voltooien. Accepteer de standaardwaarden tenzij anders vermeld.  

    ### <a name="table-19-information-for-completing-the-create-mdt-task-sequence-wizard"></a>Tabel 19. Informatie voor het voltooien van de Wizard Takenreeks MDT maken  

    |**Op deze wizardpagina** |**Dit doet** |  
    |-|-|  
    |**Sjabloon kiezen** |Selecteer **Clienttakenreeks**, en klik vervolgens op **volgende**.|  
    |**Sjabloon kiezen: Algemeen** |1.  In **takenreeksnaam**, type **Windows 8.1 verwijzing implementatie**.<br />2.  In **Task sequence opmerkingen**, type **Takenreeks voor het Windows 8.1 implementeren op de referentiecomputer (WDG-REF-01)**, en klik vervolgens op **volgende**.|  
    |**Sjabloon kiezen: Meer informatie** |1.  Klik op **lid van een werkgroep**.<br />2.  In **werkgroep**, type **werkgroep**.<br />3.  In **gebruikersnaam**, type **Woodgrove Bank werknemer**.<br />4.  In **organisatienaam**, type **Woodgrove Bank**.<br />5.  In **productcode**, type ***productcode*** (waarbij *productcode* is de productcode voor Windows 8.1).<br />6.  Klik op **Volgende**.|  
    |**Sjabloon kiezen: Instellingen vastleggen** |<ol><li>Klik op **deze takenreeks kan worden gebruikt voor het vastleggen en image**.</li><li>In **vastleggen bestemming**, type  **\\\WDG-MDT-01\Capture$\WDG-REF-01.wim**.</li><li>In **account voor het vastleggen**, klikt u op **ingesteld**.</li><li>Voltooi de **Windows-gebruikersaccount** dialoogvenster door de volgende stappen uit te voeren:<br /><br /> <ol><li>In **gebruikersnaam**, type **MDT2013\Administrator**.</li><li>In **wachtwoord** en **wachtwoord bevestigen**, type  **P@ssw0rd** .</li></ol></li><li>Klik op **OK**.</li><li>Klik op **Volgende**.</li></ol>|  
    |**Opstartinstallatiekopie** |1.  Klik op **maken van een nieuwe opstartinstallatiekopie-pakket**.<br />2.  In **pakketbronmap worden gemaakt**, type  **\\\WDG-MDT-01\Packages$\WINPE_Custom**, en klik vervolgens op **volgende**.|  
    |**Opstartinstallatiekopie: Algemene instellingen** |1.  In **naam**, type **Windows PE aangepaste**.<br />2.  In **versie**, type **1,00**.<br />3.  In **opmerkingen**, type **aangepaste versie van Windows PE moet worden gebruikt in de implementatie van de referentie-en**, en klik vervolgens op **volgende**.|  
    |**Opstartinstallatiekopie: Opties** |Onder **Platform**, klikt u op **x64**, en klik vervolgens op **volgende**.|  
    |**Opstartinstallatiekopie: Onderdelen** |Klik op **Volgende**.|  
    |**Opstartinstallatiekopie: Aanpassing** |Klik op **Volgende**.|  
    |**MDT-pakket** |1.  Klik op **een nieuw pakket van Microsoft Deployment Toolkit-bestanden maken**.<br />2.  In **pakketbronmap worden gemaakt**, type  **\\\WDG-MDT-01\Packages$\MDT_Files**, en klik vervolgens op **volgende**.|  
    |**MDT pakket: MDT-Details** |1.  In **naam**, type **MDT bestanden**.<br />2.  In **versie**, type **1,00**.<br />3.  In **opmerkingen**, type **biedt toegang tot MDT bestanden tijdens het implementatieproces van de Configuration Manager**, en klik vervolgens op **volgende**.|  
    |**Installatiekopie van het besturingssysteem** |1.  Klik op **Maak een nieuw besturingssysteem installatiepakket**.<br />2.  In **OS-installatielocatie map**, type  **\\\WDG-MDT-01\Source$\Windows_8-1**.<br />3.  In **pakketbronmap worden gemaakt**, type  **\\\WDG-MDT-01\Packages$\Windows_8-1**, en klik vervolgens op **volgende**.|  
    |**Installatiekopie van het besturingssysteem: Details van de afbeelding** |1.  In **naam**, type **Windows 8.1**.<br />2.  In **versie**, type **1,00**.<br />3.  In **opmerkingen**, type **Windows 8.1-pakket gebruikt om te implementeren om referentiecomputers te**, en klik vervolgens op **volgende**.|  
    |**Methode-implementatie** |Klik op **Volgende**.|  
    |**Clientpakket** |Klik op **maken van een nieuwe ConfigMgr-clientpakket**, en klik vervolgens op **volgende**.|  
    |**USMT-pakket** |1.  Klik op **een nieuw USMT-pakket maken**.<br />2.  In **pakketbronmap worden gemaakt**, type  **\\\WDG-MDT-01\Packages$\USMT**, en klik vervolgens op **volgende**.|  
    |**USMT-pakket: USMT-Details** |1.  In **naam**, type **USMT**.<br />2.  In **versie**, type **1,00**.<br />3.  In **opmerkingen**, type **USMT-bestanden gebruikt voor het vastleggen en herstellen van informatie over migratie van gebruikersstatus**, en klik vervolgens op **volgende**.|  
    |**Instellingen pakket** |1.  Klik op **Maak een nieuw pakket van de instellingen**.<br />2.  In **pakketbronmap worden gemaakt**, type  **\\\WDG-MDT-01\Packages$\CustomSettings_Reference**, en klik vervolgens op **volgende**.|  
    |**Instellingen voor pakket: Details van instellingen** |1.  In **naam**, type **aangepaste instellingen referentiecomputer MDT**.<br />2.  In **versie**, type **1,00**.<br />3.  In **opmerkingen**, type **configuratie-instellingen voor de MDT-implementatieproces (zoals CustomSettings.ini) voor de referentiecomputer**, en klik vervolgens op **volgende**.|  
    |**Sysprep-pakket** |Klik op **Volgende**.|  
    |**Samenvatting** |Lees de informatie in de **Details** vak die die u hebt opgegeven tijdens het uitvoeren van de vorige wizardpagina's en klik vervolgens op **volgende**.|  
    |**Voortgang** |De voortgang voor het maken van de takenreeks wordt weergegeven.|  
    |**Bevestiging** |Klik op **Voltooien**.|  

 De nieuwe takenreeks weergegeven in het voorbeeldvenster.  

###  <a name="SelectDistributionPointsfortheNewPackages"></a>Stap 3-2: Selecteer de distributiepunten voor de nieuwe pakketten en installatiekopieën  
 De MDT Wizard Takenreeks maken maakt een aantal pakketten en afbeeldingen. Nadat deze pakketten en afbeeldingen worden gemaakt, selecteert u de distributiepunten op waarop de pakketten en afbeeldingen, gekopieerd en beschikbaar zijn voor de doelcomputers worden moeten.  

> [!NOTE]
>  In dit voorbeeld is er slechts één distributiepunt (WDG-MDT-01). De meeste productienetwerken hebben echter meerdere distributiepunten. Wanneer u deze stap uitvoert in een productieomgeving, selecteer de juiste distributiepunten voor het netwerk.  

 **Selecteer de distributiepunten voor softwaredistributiepakketten**  

1.  Klik op **Start**, wijs **alle programma's**, en wijs vervolgens **Microsoft System Center 2012**. Wijs **Configuration Manager**, en klik vervolgens op **Configuration Manager-Console**.  

2.  Klik in de Configuration Manager-console in het navigatievenster op **softwarebibliotheek**.  

3.  Ga in de werkruimte softwarebibliotheek naar overzicht/Operating Systems/Takenreeksen.  

4.  Selecteer in het voorbeeldvenster **Windows 8.1 verwijzing implementatie**.  

5.  Klik op het lint op de **Start** tabblad, in de **implementatie** groep, klikt u op **inhoud distribueren**.  

     De Wizard inhoud distribueren wordt gestart.  

6.  Voltooi de Wizard inhoud distribueren met behulp van de informatie in 20. Accepteer de standaardwaarden tenzij anders vermeld.  

    ### <a name="table-20-information-for-completing-the-distribute-content-wizard"></a>Tabel 20. Informatie voor het voltooien van de Wizard inhoud distribueren  

    |**Op deze wizardpagina** |**Dit doet** |  
    |-|-|  
    |**Algemeen** |Klik op **Volgende**.|  
    |**Algemeen: Inhoud** |Klik op **Volgende**.|  
    |**Algemeen: Doel van inhoud** |1.  Klik op **toevoegen**, en klik vervolgens op **distributiepunt**.<br />     De **distributiepunten toevoegen** dialoogvenster wordt weergegeven.<br />2.  In de **distributiepunten toevoegen** dialoogvenster,  **\\\WDGMDT01.mdt2013.corp.woodgrovebank.com**, en klik vervolgens op **OK**.<br />     \\\WDGMDT01.mdt2013.corp.woodgrovebank.com wordt weergegeven in de **doel van inhoud** lijst.<br />3.  Klik op **Volgende**.|  
    |**Samenvatting** |Lees de informatie in de **Details** vak die die u hebt opgegeven tijdens het uitvoeren van de vorige wizardpagina's en klik vervolgens op **volgende**.|  
    |**Voortgang** |De voortgang voor het distribueren van de software wordt weergegeven.|  
    |**Voltooiing** |Klik op **Sluiten**.|  

7.  Sluit alle geopende vensters en dialoogvensters.  

###  <a name="AddtheNecessaryDeviceDrivers"></a>Stap 3-3: De benodigde apparaatstuurprogramma's toevoegen  
 Wanneer de takenreeks MDT is gemaakt, toevoegen eventuele apparaatstuurprogramma's vereist zijn voor de referentiecomputer (WDG-REF-01) aan de Windows PE-installatiekopie en op de installatiekopie van Windows 8.1. De apparaatstuurprogramma's toevoegen in het knooppunt stuurprogramma's in de Configuration Manager-console. Maak een pakket met de apparaatstuurprogramma's en de stuurprogramma's invoeren in de aangepaste Windows PE-installatiekopie die eerder in het proces hebt gemaakt.  

 Nadat het maken van het pakket dat de stuurprogramma's bevat, selecteert u de verdeling punt waarop het pakket wordt geïmplementeerd.  

 **De benodigde apparaatstuurprogramma's toevoegen**  

1.  Klik op **Start**, wijs **alle programma's**, en wijs vervolgens **Microsoft System Center 2012**. Wijs **Configuration Manager**, en klik vervolgens op **Configuration Manager-Console**.  

2.  Klik in de Configuration Manager-console in het navigatievenster op **softwarebibliotheek**.  

3.  Ga naar overzicht/Operating Systems/Drivers in de werkruimte softwarebibliotheek.  

4.  Klik op het lint op de **Start** tabblad, in de **maken** groep, klikt u op **stuurprogramma importeren**.  

     De Wizard Nieuw stuurprogramma importeren wordt gestart.  

5.  Voltooi de Wizard Nieuw stuurprogramma importeren met de informatie in de tabel 21. Accepteer de standaardwaarden tenzij anders vermeld.  

    ### <a name="table-21-information-for-completing-the-import-new-driver-wizard"></a>Tabel 21. Informatie over het voltooien van de Wizard Nieuw stuurprogramma importeren  

    |**Op deze wizardpagina** |**Dit doet** |  
    |-|-|  
    |**Stuurprogramma vinden** |**In de bronmap**, type  **\\\WDG-MDT-01\Source$\Drivers**, en klik vervolgens op **volgende**.|  
    |**Stuurprogramma vinden: Details van stuurprogramma** |Klik op **Volgende**.|  
    |**Stuurprogramma vinden: Stuurprogramma's toevoegen aan pakket** |<ol><li>Klik op **nieuw pakket**.</li><li>Voltooi de **nieuw stuurprogrammapakket** dialoogvenster door de volgende stappen uit te voeren:<br /><br /> <ol><li>In **naam**, type ***device_driver_name*** **pakket** (waarbij *device_driver_name* is een beschrijvende naam voor de apparaatstuurprogramma's).</li><li>In **Opmerking**, type **apparaatstuurprogramma's die nodig voor de referentie- en doelcomputers computers zijn**.</li></ol></li><li>In **stuurprogramma pakketbron**, type  **\\\WDG-MDT-01\Packages$\Drivers**, en klik vervolgens op **OK**.</li><li>Klik op **Volgende**.</li></ol>|  
    |**Stuurprogramma vinden: Stuurprogramma aan installatiekopieën toevoegen** |1.  Selecteer in de lijst met afbeeldingen, de **Windows PE aangepaste** selectievakje.<br />2.  Selecteer de **distributiepunten bijwerken na voltooiing** selectievakje en klik vervolgens op **volgende**.|  
    |**Samenvatting** |Lees de informatie in de **Details** vak die die u hebt opgegeven tijdens het uitvoeren van de vorige wizardpagina's en klik vervolgens op **volgende**.|  
    |**Voortgang** |De voortgang voor het importeren van apparaatstuurprogramma's wordt weergegeven.|  
    |**Bevestiging** |Klik op **Sluiten**.|  

 **De distributiepunten voor het stuurprogrammapakket selecteren**  

1.  Klik op **Start**, wijs **alle programma's**, en wijs vervolgens **Microsoft System Center 2012**. Wijs **Configuration Manager**, en klik vervolgens op **Configuration Manager-Console**.  

2.  Klik in de Configuration Manager-console in het navigatievenster op **softwarebibliotheek**.  

3.  Ga in de werkruimte softwarebibliotheek naar overzicht/Operating Systems/stuurprogrammapakketten.  

4.  Klik in het voorbeeldvenster op ***device_driver_name*** **pakket** (waarbij *device_driver_name* is een beschrijvende naam voor de apparaatstuurprogramma's).  

5.  Klik op het lint op de **Start** tabblad, in de **implementatie** groep, klikt u op **inhoud distribueren**.  

     De Wizard inhoud distribueren wordt gestart.  

6.  Voltooi de Wizard inhoud distribueren met behulp van de informatie in de tabel 22. Accepteer de standaardwaarden tenzij anders vermeld.  

    ### <a name="table-22-information-for-completing-the-distribute-content-wizard"></a>Tabel 22. Informatie voor het voltooien van de Wizard inhoud distribueren  

    |**Op deze wizardpagina** |**Dit doet** |  
    |-|-|  
    |**Algemeen** |Klik op **Volgende**.|  
    |**Algemeen: Inhoud** |Klik op **Volgende**.|  
    |**Algemeen: Doel van inhoud** |1.  Klik op **toevoegen**, en klik vervolgens op **distributiepunt**.<br />     De **distributiepunten toevoegen** dialoogvenster wordt weergegeven.<br />2.  In de **distributiepunten toevoegen** dialoogvenster,  **\\\WDG-MDT-01.mdt2013.corp.woodgrovebank.com**, en klik vervolgens op **OK**.<br />     \\\WDGMDT01.mdt2013.corp.woodgrovebank.com wordt weergegeven in de **doel van inhoud** lijst.<br />3.  Klik op **Volgende**.|  
    |**Samenvatting** |Lees de informatie in de **Details** vak die die u hebt opgegeven tijdens het uitvoeren van de vorige wizardpagina's en klik vervolgens op **volgende**.|  
    |**Voortgang** |De voortgang voor het distribueren van de software wordt weergegeven.|  
    |Voltooiing|Klik op **Sluiten**.|  

7.  Sluit alle geopende vensters en dialoogvensters.  

###  <a name="EnableMDTDeploymentProcessMonitoring"></a>Stap 3 en 4: MDT-implementatie in te schakelen procesbewaking  
 Vóór de implementatie van de referentiecomputer (WDG-REF-01) met opstartbare media voor de takenreeks MDT-controle van het implementatieproces ZTI inschakelen. U inschakelen bewaking op de **bewaking** tabblad van de implementatieshare **eigenschappen** in het dialoogvenster. Later in het proces wordt u het implementatieproces van ZTI met behulp van de implementatie-Workbench controleren of de **Get-MDTMonitorData** cmdlet.  

 **MDT bewaking van het implementatieproces ZTI wilt inschakelen**  

1.  Klik op **Start**, en wijs vervolgens **alle programma's**. Wijs **Microsoft Deployment Toolkit**, en klik vervolgens op **implementatie-Workbench**.  

2.  Ga naar de implementatie Workbench/Implementatieshares in de consolestructuur van de implementatie-Workbench.  

3.  In het deelvenster Acties **klikt u op de nieuwe Implementatieshares**.  

     De Wizard Nieuwe Deployment Share wordt gestart.  

4.  De implementatie van Wizard Nieuwe Share met de informatie in de tabel 23 voltooien.  

    ### <a name="table-23-information-for-completing-the-new-deployment-share-wizard"></a>Tabel 23. Informatie over het voltooien van de Wizard Nieuwe Deployment Share  

    |**Op deze wizardpagina** |**Dit doet** |  
    |-|-|  
    |**Pad** |**In het pad naar bestandsshare implementatie**, type **C:\DeploymentShare$**, en klik vervolgens op **volgende**.|  
    |**Delen** |Klik op **Volgende**.|  
    |**Beschrijvende naam** |Klik op **Volgende**.|  
    |**Opties** |Klik op **Volgende**.|  
    |**Samenvatting** |Klik op **Volgende**.|  
    |**Voortgang** |De voortgang voor het maken van de implementatieshare wordt weergegeven.|  
    |**Bevestiging** |Klik op voltooien.|  

     De Wizard Nieuw implementatietype is voltooid en de nieuwe implementatieshare: MDT Deployment Share (C:\DeploymentShare$)—appears in het detaildeelvenster.  

5.  Klik in het detailvenster op **MDT-Implementatieshare (C:\DeploymentShare$)**.  

6.  Klik op eigenschappen in het deelvenster Acties.  

     De **eigenschappen van de MDT-Implementatieshare (C:\DeploymentShare$)** dialoogvenster wordt geopend.  

7.  In de **eigenschappen MDT Deployment Share (C:\DeploymentShare$)** in het dialoogvenster op de **bewaking** tabblad de **Schakel bewaking voor deze implementatieshare** selectievakje , en klik vervolgens op **toepassen**.  

8.  In de **eigenschappen van de MDT-Implementatieshare (C:\DeploymentShare$)** in het dialoogvenster op de **regels** tabblad, zoals u ziet de **EventService** eigenschap is toegevoegd aan de CustomSettings.ini-bestand en klik vervolgens op **OK**.  

     De **EventService** eigenschap is als volgt:  

    ```  
    EventService=http://WDG-MDT-01:9800  
    ```  

9. Sluit alle geopende vensters en dialoogvensters.  

###  <a name="CustomizeMDTConfigFilesforReferenceComputer"></a>Stap 3-5: Het aanpassen van de MDT-configuratiebestanden voor de referentiecomputer  
 Wanneer de takenreeks MDT is gemaakt, aanpassen van de MDT-configuratiebestanden die voorzien in de configuratie-instellingen voor Windows 8.1 implementeren met de doelcomputer. In het bijzonder het CustomSettings.ini-bestand aanpassen.  

 Wanneer het bestand CustomSettings.ini aanpassing is voltooid, moet u de bijgewerkte bestanden opslaan voor de bronmap voor het aangepaste instellingen referentiecomputer MDT pakket eerder in het proces (E:\Packages$\CustomSettings_Reference) gemaakt. Voeg vervolgens de **DoCapture** en **EventService** eigenschappen en bijbehorende waarden aan het CustomSettings.ini-bestand zodat het implementatieproces MDT legt een installatiekopie van de computer verwijzing (vast WDG-REF-01) na de implementatie van Windows 8.1.  

 **Voor het aanpassen van de MDT-configuratiebestanden voor de referentiecomputer**  

1.  In Windows Verkenner, Ga naar E:\Packages$\CustomSettings_Reference en dubbelklik vervolgens op **CustomSettings.ini**.  

2.  Open Microsoft Notepad en vervolgens de volgende regels toevoegen aan het einde van het CustomSettings.ini-bestand, zoals weergegeven in de lijst 1:  

    ```  
    DoCapture=YES  
    EventService=http://WDG-MDT-01:9800  
    ```  

    > [!NOTE]
    >  Zorg ervoor dat u aanvullende instellingen behalve die wordt weergegeven in de lijst 1 verwijderen.  

     **Aanbieding 1. Na het toevoegen van de eigenschap DoCapture CustomSettings.ini-bestand**  

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

3.  Sla het bestand op en sluit Kladblok.  

###  <a name="UpdateDistributionPointsforCustomSettings"></a>Stap 3-6: De distributiepunten voor het pakket met aangepaste instellingen voor bestanden bijwerken  
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

###  <a name="CustomizeTaskSequenceforReferenceComputer"></a>Stap 3-7: De Takenreeks voor de referentiecomputer aanpassen  
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

-   De referentiecomputer toevoegen aan de database van de Configuration Manager-site, zoals beschreven in [stap 4-1: De referentiecomputer toevoegen aan de sitedatabase van Configuration Manager](#AddReferenceComputertoConfigurationManagerSite)  

-   Maken van een verzameling die de referentiecomputer die u zojuist hebt toegevoegd, zoals beschreven in bevat [stap 4-2: Een verzameling maken die de referentiecomputer bevat](#CreateCollectionthatContainsReferenceComputer)  

-   Implementeer de takenreeks van de referentie-computer, zoals beschreven in [stap 4-3: De verwijzing naar Computer-Takenreeks implementeren](#DeployReferenceComputerTaskSequence)  

-   Met behulp van de Wizard Takenreeksmedia maken van een takenreeks opstartbare media zoals beschreven in schijf [stap 4-4: De opstartbare Takenreeksmedia maken](#CreateTaskSequenceBootableMedia)  

-   Opstartbare media schijf zoals beschreven in de takenreeks wordt uitgevoerd vanaf de referentiecomputer [stap 4 en 5: Start de referentiecomputer met opstartbare Media voor de Takenreeks](#StartReferenceComputerwithTaskSequenceBootableMedia)  

###  <a name="AddReferenceComputertoConfigurationManagerSite"></a>Stap 4-1: De referentiecomputer toevoegen aan de sitedatabase van Configuration Manager  
 Voor het implementeren van een besturingssysteem zonder zelfstandige media naar een nieuwe computer die Configuration Manager momenteel niet beheert, moet u de nieuwe computer toevoegen aan de Configuration Manager-sitedatabase vóór het starten van het implementatieproces van het besturingssysteem. Configuration Manager kan automatisch detecteren van computers in het netwerk met een Windows-besturingssysteem geïnstalleerd. Als de computer geen besturingssysteem geïnstalleerd is, gebruiken, de Wizard computergegevens importeren naar de nieuwe computergegevens importeren.  

 **De referentiecomputer toevoegen aan de sitedatabase van Configuration Manager**  

1.  Klik op **Start**, wijs **alle programma's**, en wijs vervolgens **Microsoft System Center 2012**. Wijs **Configuration Manager**, en klik vervolgens op **Configuration Manager-Console**.  

2.  Klik in de Configuration Manager-console in het navigatievenster op **activa en naleving**.  

3.  In de activa en naleving werkruimte, gaat u naar overzicht/apparaten.  

4.  Klik op het lint op de **Start** tabblad, in de **maken** groep, klikt u op **computergegevens importeren**.  

     De Wizard computergegevens importeren wordt gestart.  

5.  Voltooi de Wizard computergegevens importeren met behulp van de informatie in de 24. Accepteer de standaardwaarden tenzij anders vermeld.  

    ### <a name="table-24-information-for-completing-import-computer-information-wizard"></a>Tabel 24. Informatie over het voltooien van de Wizard computergegevens importeren  

    |**Op deze wizardpagina** |**Dit doet** |  
    |-|-|  
    |**Bron selecteren** |Klik op **Eén computer importeren**, en klik vervolgens op **volgende**.|  
    |Bron selecteren: Één Computer|1.  In **computernaam**, type **WDG-REF-01**.<br />2.  In **MAC-adres**, type ***Mac*** (waarbij *Mac* is het adres media access control [MAC] van de primaire-netwerkadapter voor de referentiecomputer WDG-REF-01).<br />3.  Klik op **Volgende**.|  
    |**Bron selecteren: Voorbeeld van gegevens** |Klik op **Volgende**.|  
    |**Bron selecteren: Kies doelverzameling** |Klik op **Volgende**.|  
    |**Samenvatting** |Lees de informatie in de **Details** vak die die u hebt opgegeven tijdens het uitvoeren van de vorige wizardpagina's en klik vervolgens op **volgende**.|  
    |**Voortgang** |De voortgang voor het importeren van de computer wordt weergegeven.|  
    |**Bevestiging** |Klik op **Sluiten**.|  

 Zie voor meer informatie over het toevoegen van een nieuwe computer aan de sitedatabase van Configuration Manager de sectie ' voor het importeren van computergegevens voor één computer' in de sectie 'Hoe te implementeren van besturingssystemen in Configuration Manager,' in de configuratie Documentatiebibliotheek Manager, die met Configuration Manager is geïnstalleerd.  

###  <a name="CreateCollectionthatContainsReferenceComputer"></a>Stap 4-2: Een verzameling maken die de referentiecomputer bevat  
 In de Configuration Manager-console maakt u een verzameling die de referentiecomputer (WDG-REF-01) bevat. De computerverzameling van deze wordt later gebruikt wanneer de takenreeks reclame eerder in het proces gemaakt.  

 **Een verzameling die de referentiecomputer bevat maken**  

1.  Klik op **Start**, wijs **alle programma's**, en wijs vervolgens **Microsoft System Center 2012**. Wijs **Configuration Manager**, en klik vervolgens op **Configuration Manager-Console**.  

2.  Klik in de Configuration Manager-console in het navigatievenster op **activa en naleving**.  

3.  In de activa en naleving werkruimte, gaat u naar overzicht/Apparaatverzamelingen.  

4.  Klik op het lint op de **Start** tabblad, in de **maken** groep, klikt u op **maken**, en klik vervolgens op **Apparaatverzameling maken**.  

     De Wizard Apparaatverzameling maken wordt gestart.  

5.  Voltooi de Wizard Apparaatverzameling maken met de informatie in de tabel 25. Accepteer de standaardwaarden tenzij anders vermeld.  

    ### <a name="table-25-information-for-completing-the-create-device-collection-wizard"></a>Tabel 25. Informatie voor het voltooien van de wizard Apparaatverzameling maken  

    |**Op deze wizardpagina** |**Dit doet** |  
    |-|-|  
    |**Algemeen** |<ol><li>In **naam**, type **Microsoft Deployment – referentiecomputer**.</li><li>In **Opmerking**, type **Computer die moet worden van de referentiecomputer voor de doelcomputers te worden geïmplementeerd**.</li><li>In **beperkte verzameling**, klikt u op **Bladeren**.<br /><br />     De **verzameling selecteren** dialoogvenster wordt weergegeven. Voer in het dialoogvenster door de volgende stappen uit te voeren:<br /><br /> <ol><li>In **naam**, klikt u op **alle systemen**.</li><li>Klik op **OK**.</li></ol></li><li>Klik op **Volgende**.</li></ol>|  
    |**Lidmaatschapsregels** |<ol><li>Klik op **regel toevoegen**, en klik vervolgens op **directe regel**.<br /><br />     De Wizard regel voor Direct lidmaatschap maken wordt gestart.</li><li>Voltooi de Wizard regel voor Direct lidmaatschap maken door de volgende stappen uit te voeren:<br /><br /> <ol><li>Klik op de pagina **Welkom** op **Volgende**.</li><li>Op de **zoeken naar Resources** pagina **bronklasse**, selecteer **systeembron**; in **kenmerknaam**, selecteer  **Naam**; in **waarde**, type **WDG-REF-01**; en klik vervolgens op **volgende**.</li><li>Op de **Resources selecteren** pagina **WDG-REF-01**, en klik vervolgens op **volgende**.</li><li>Op de **samenvatting** pagina, klikt u op **volgende**.</li><li>Op de **voortgang** pagina, de voortgang voor het maken van de nieuwe lidmaatschapsregel weergeven.</li><li>Op de **voltooiing** pagina, klikt u op **sluiten**.</li></ol></li><li>Klik op **Volgende**.</li></ol>|  
    |**Samenvatting** |Lees de informatie in de **Details** vak die die u hebt opgegeven tijdens het uitvoeren van de vorige wizardpagina's en klik vervolgens op **volgende**.|  
    |**Voortgang** |De voortgang voor het maken van de apparatenverzameling wordt weergegeven.|  
    |**Voltooiing** |Klik op **Sluiten**.|  

 Zie de sectie 'Hoe te maken van verzamelingen in Configuration Manager,' in de Documentatiebibliotheek van Configuration Manager, dat geïnstalleerd is met Configuration Manager voor meer informatie.  

###  <a name="DeployReferenceComputerTaskSequence"></a>Stap 4-3: De verwijzing naar Computer-Takenreeks implementeren  
 Implementeer de takenreeks die eerder in het proces in de apparaatverzameling met de referentiecomputer gemaakt eerder in het proces hebt gemaakt in de Configuration Manager-console.  

 **De takenreeks implementeren**  

1.  Klik op **Start**, wijs **alle programma's**, en wijs vervolgens **Microsoft System Center 2012**. Wijs **Configuration Manager**, en klik vervolgens op **Configuration Manager-Console**.  

2.  Klik in de Configuration Manager-console in het navigatievenster op **softwarebibliotheek**.  

3.  Ga in de werkruimte softwarebibliotheek naar overzicht/Operating Systems/Takenreeksen.  

4.  Klik in het voorbeeldvenster op **Windows 8.1 verwijzing implementatie**.  

5.  Klik op het lint op de **Start** tabblad, in de **implementatie** groep, klikt u op **implementeren**.  

     De Wizard Software implementeren wordt gestart.  

6.  Voltooi de Wizard Software implementeren met de informatie in de tabel 26. Accepteer de standaardwaarden tenzij anders vermeld.  

    ### <a name="table-arabic-26-information-for-completing-the-deploy-software-wizard"></a>Tabel Arabische 26. Informatie voor het voltooien van de Wizard Software implementeren  

    |**Op deze wizardpagina** |**Dit doet** |  
    |-|-|  
    |**Algemeen** |1.  In **verzameling**, klikt u op **Bladeren**.<br />2.  In de **verzameling Bladeren** in het dialoogvenster, klikt u op **Microsoft Deployment – referentiecomputer**, en klik vervolgens op **OK**.<br />3.  In **Opmerking**, type **Windows 8.1 implementeren op de referentiecomputer en vervolgens vastleggen een installatiekopie van de referentiecomputer**.<br />4.  Klik op **Volgende**.|  
    |**Implementatie-instellingen** |1.  In **doel**, selecteer **beschikbaar**.<br />2.  Selecteer de **beschikbaar maken voor opstartmedia en PXE** selectievakje.<br />3.  Klik op **Volgende**.|  
    |**Implementatie-instellingen: Planning** |Klik op **Volgende**.|  
    |**Implementatie-instellingen: Gebruikerservaring** |Klik op **Volgende**.|  
    |**Implementatie-instellingen: Waarschuwingen** |Klik op **Volgende**.|  
    |**Implementatie-instellingen: Distributiepunten** |Klik op **Volgende**.|  
    |**Samenvatting** |Lees de informatie in de **Details** vak die die u hebt opgegeven tijdens het uitvoeren van de vorige wizardpagina's en klik vervolgens op **volgende**.|  
    |**Voortgang** |De voortgang voor het implementeren van de takenreeks wordt weergegeven.|  
    |**Voltooiing** |Klik op **Sluiten**.|  

 Zie de sectie 'Hoe te implementeren van een Takenreeks,' in de Documentatiebibliotheek van Configuration Manager, dat geïnstalleerd is met Configuration Manager voor meer informatie.  

###  <a name="CreateTaskSequenceBootableMedia"></a>Stap 4-4: De opstartbare Takenreeksmedia maken  
 Bieden een methode voor het starten van de computer met Windows PE en de benodigde software door het maken van de schijf taak sequence opstartbare media voor het initiëren van de MDT-proces. Gebruik de Wizard Takenreeks Media in de Configuration Manager-console voor het maken van opstartbare media voor opslag op een USB-flashstation, cd-rom of DVD.  

 **Een schijf taak sequence opstartbare media maken**  

1.  Klik op **Start**, wijs **alle programma's**, en wijs vervolgens **Microsoft System Center 2012**. Wijs **Configuration Manager**, en klik vervolgens op **Configuration Manager-Console**.  

2.  Klik in de Configuration Manager-console in het navigatievenster op **softwarebibliotheek**.  

3.  Ga in de werkruimte softwarebibliotheek naar overzicht/Operating Systems/Takenreeksen.  

4.  Klik op het lint op de **Start** tabblad, in de **maken** groep, klikt u op **Takenreeksmedia maken**.  

     De Wizard maakt Takenreeksmedia taak wordt gestart.  

5.  Voltooi de Wizard Takenreeks maken Media met de informatie in de tabel 27. Accepteer de standaardwaarden tenzij anders vermeld.  

    ### <a name="table-27-information-for-completing-the-create-task-sequence-media-wizard"></a>Tabel 27. Informatie over het voltooien van de Wizard Takenreeksmedia maken  

    |**Op deze wizardpagina** |**Dit doet** |  
    |-|-|  
    |**Mediatype selecteren** |1.  Klik op **opstartbare media**.<br />2.  Schakel de **implementatie van besturingssysteem zonder toezicht toestaan** selectievakje.<br />3.  Klik op **Volgende**.|  
    |**Het mediatype selecteren: Mediabeheer** |Klik op **Site gebaseerde media**, en klik vervolgens op **volgende**.|  
    |**Het mediatype selecteren: Mediatype** |In **mediabestand**, type  **\\\WDG-MDT-01\Capture$\CM2012_TS_Boot_Media.iso**, en klik vervolgens op **volgende**.|  
    |**Het mediatype selecteren: Beveiliging** |In **wachtwoord** en **wachtwoord bevestigen**, type  **P@ssw0rd** , en klik vervolgens op **volgende**.|  
    |**Het mediatype selecteren: Opstartinstallatiekopie** |1.  In **opstartinstallatiekopie**, klikt u op **Bladeren**.<br />2.  In de **een opstartinstallatiekopie selecteren** in het dialoogvenster, klikt u op **Windows PE aangepaste**, en klik vervolgens op **OK**.<br />3.  In **distributiepunt**, klikt u op  **\\\WDG-MDT-01.mdt2013.corp.woodgrovebank.com**, en klik vervolgens op **OK**.<br />4.  In **beheerpunt**, klikt u op  **\\\WDG-MDT-01.mdt2013.corp.woodgrovebank.com**, en klik vervolgens op **OK**.<br />5.  Klik op **Volgende**.|  
    |**Het mediatype selecteren: Aanpassing** |Klik op **Volgende**.|  
    |**Samenvatting** |Lees de informatie in de **Details** vak die die u hebt opgegeven tijdens het uitvoeren van de vorige wizardpagina's en klik vervolgens op **volgende**.|  
    |**Voortgang** |De voortgang voor het maken van media voor de takenreeks wordt weergegeven.|  
    |**Voltooiing** |Klik op **Sluiten**.|  

     De wizard maakt het bestand CM2012_TS_Boot_Media.iso in de MDT-WDG-01Capture$ gedeelde map.  

6.  Als REF-01-WDG een fysieke computer is, maakt u een CD of DVD van de International Organization for Standardization (ISO)-bestand. Als REF-01-WDG een virtuele machine is, start u de virtuele machine rechtstreeks vanuit het ISO-bestand.  

 Zie voor meer informatie over het maken van de schijf taak sequence opstartbare media de sectie 'Hoe te maken van opstartbare Media,' in de Documentatiebibliotheek van Configuration Manager, die met Configuration Manager is geïnstalleerd.  

###  <a name="StartReferenceComputerwithTaskSequenceBootableMedia"></a>Stap 4 en 5: Start de referentiecomputer met opstartbare Media voor de Takenreeks  
 Start de referentiecomputer (WDG-REF-01) met de taak sequence opstartbare media schijf die eerder in het proces wordt gemaakt. Dit medium wordt Windows PE gestart op de referentiecomputer en start het proces MDT. Windows 8.1 is geïmplementeerd op de referentiecomputer en een installatiekopie van de referentiecomputer wordt opgeslagen in \WDG-MDT-01\Capture$\WDG-REF-01.wim aan het einde van de MDT-proces.  

> [!NOTE]
>  U kunt ook de MDT-proces starten door het starten van de doelcomputer vanaf de Windows Deployment Services.  

 **Starten van de referentiecomputer met opstartbare media voor de takenreeks**  

1.  Start WDG-REF-01 met opstartbare media voor de takenreeks eerder in het proces hebt gemaakt.  

     Windows PE wordt gestart en vervolgens de Wizard Takenreeks wordt gestart.  

2.  Voltooi de Wizard Takenreeks met de informatie in de tabel 28. Accepteer de standaardwaarden tenzij anders vermeld.  

    ### <a name="table-28-information-for-completing-the-task-sequence-wizard"></a>Tabel 28. Informatie over het voltooien van de Wizard Takenreeks  

    |**Op deze wizardpagina** |**Dit doet** |  
    |-|-|  
    |**Welkom bij de Wizard Takenreeks** |In **wachtwoord**, type  **P@ssw0rd** , en klik vervolgens op **volgende**.|  
    |**Selecteer een Takenreeks** |Selecteer in de keuzelijst **Windows 8.1 verwijzing implementatie**, en klik vervolgens op **volgende**.|  

 **Het implementatieproces van de verwijzing naar computer met behulp van de implementatie-Workbench bewaken**  

1.  Klik op WDG-MDT-01 **Start**, en wijs vervolgens **alle programma's**. Wijs **Microsoft Deployment Toolkit**, en klik vervolgens op **implementatie-Workbench**.  

2.  In de consolestructuur van de implementatie-Workbench gaat u naar de implementatie Workbench/implementatie Shares/MDT-Implementatieshare (C:\DeploymentShare$)/Monitoring.  

3.  In het detailvenster het implementatieproces voor WDG-REF-01 te bekijken.  

4.  Klik in het deelvenster Acties periodiek op **vernieuwen**.  

     De status van het implementatieproces is bijgewerkt in het detaildeelvenster. Blijven volgen het implementatieproces totdat het proces voltooid is.  

5.  Klik in het detailvenster op **WDG-REF-01**.  

6.  Klik in het deelvenster Acties op **eigenschappen**.  

     De **WDG-REF-01-eigenschappen** in het dialoogvenster wordt weergegeven.  

7.  In de **WDG-REF-01-eigenschappen** in het dialoogvenster op de **identiteit** tabblad, de controle-informatie gegeven over het implementatieproces, zoals beschreven in de tabel 29 weergeven.  

    ### <a name="table-29-monitoring-information-about-the-deployment-process"></a>Tabel 29. Bewaking van informatie over het implementatieproces  

    |**Informatie** |**Beschrijving** |  
    |-|-|  
    |**ID** |De unieke id voor de computer wordt geïmplementeerd.|  
    |**Computernaam** |De naam van de computer wordt geïmplementeerd.|  
    |Implementatiestatus|De huidige status van de computer wordt geïmplementeerd; de status kan een van de volgende zijn:<br /><br /> -   **Met**. De takenreeks is in orde en wordt uitgevoerd.<br />-   **Kan geen**. De takenreeks is mislukt en het implementatieproces is mislukt.<br />-   **Voltooid**. De takenreeks is voltooid.<br />-   **Niet-reagerende**. De takenreeks heeft de status ervan niet bijgewerkt in de afgelopen vier uur en wordt ervan uitgegaan dat niet meer reageert.|  
    |**Stap** |De huidige takenreeksstap wordt uitgevoerd.|  
    |**Voortgang** |De algemene voortgang van de takenreeks wordt uitgevoerd. De voortgangsbalk geeft aan hoeveel takenreeksstappen van het totale aantal met takenreeksstappen zijn uitgevoerd.|  
    |**Start** |De tijd die het implementatieproces gestart.|  
    |**Einde** |De tijd die het implementatieproces is beëindigd.|  
    |**Verstreken** |Hoe lang het implementatieproces actief is geweest of duurde om uit te voeren als de implementatie is voltooid.|  
    |**Fouten** |Het aantal fouten zijn opgetreden tijdens het implementatieproces.|  
    |**Waarschuwingen** |Het aantal waarschuwingen aangetroffen tijdens het implementatieproces.|  
    |**Extern bureaublad** |Deze knop kunt u extern bureaublad verbinding te maken met de computer wordt geïmplementeerd met behulp van de functie Extern bureaublad van Windows. Deze methode wordt ervan uitgegaan dat:<br /><br /> -Het beoogde besturingssysteem wordt uitgevoerd en ondersteuning voor externe bureaublad is ingeschakeld<br />-   **mstsc.exe** zich in het pad **Opmerking:**  Deze knop wordt altijd weergegeven, maar mogelijk niet tot stand brengen van een extern bureaublad-sessiehost als de bewaakte computer wordt uitgevoerd Windows PE, installatie van het beoogde besturingssysteem niet is voltooid of beschikt niet over de functie Extern bureaublad is ingeschakeld.|  
    |**VM-verbinding** |Deze knop kunt u extern bureaublad verbinding te maken met een virtuele machine in HyperV® uitgevoerd. Deze methode wordt ervan uitgegaan dat:<br /><br /> -De implementatie wordt uitgevoerd op een virtuele machine waarop Hyper-V<br />-   **vmconnect.exe** bevindt zich in de map %ProgramFiles%\Hyper-V **Opmerking:**  Deze knop wordt weergegeven wanneer ZTIGather.wsf detecteert dat de onderdelen voor Hyper-V-integratie worden uitgevoerd op de bewaakte computer. Anders wordt is deze knop alleen zichtbaar.|  
    |**DaRT extern beheer** |Deze knop kunt u tot stand brengen van een sessie voor extern beheer met de viewer voor extern-functie in de Diagnostics and Recovery Toolkit (DaRT).<br /><br /> Deze methode wordt ervan uitgegaan dat:<br /><br /> -DaRT is geïmplementeerd op de doelcomputer en wordt momenteel uitgevoerd.<br />-   **DartRemoteViewer.exe** bevindt zich in de map %ProgramFiles%\Microsoft DaRT 7\v7 **Opmerking:**  Deze knop wordt weergegeven wanneer ZTIGather.wsf detecteert dat DaRT wordt uitgevoerd op de bewaakte computer. Anders wordt is deze knop alleen zichtbaar.|  
    |**Deze informatie om de tien seconden automatisch worden vernieuwd** |Selectievakje die bepaalt of de informatie in het dialoogvenster automatisch wordt vernieuwd. Als het selectievakje is:<br /><br /> -Geselecteerd, de gegevens worden vernieuwd elke 10 seconden<br />-Uitgeschakeld, de informatie is niet automatisch vernieuwd en moet handmatig vernieuwen met behulp van de **nu vernieuwen** knop|  
    |**Nu vernieuwen** |Deze knop wordt onmiddellijk vernieuwd voor de informatie die wordt weergegeven in het dialoogvenster.|  

8.  In de **WDG-REF-01-eigenschappen** in het dialoogvenster, klikt u op **OK**.  

9. Sluit de implementatie-Workbench.  

 **Voor het bewaken van het implementatieproces van de verwijzing naar computer met de cmdlet Get-MDTMonitorData**  

1.  Klik op WDG-MDT-01 **Start**, wijs **Systeembeheer**, en klik vervolgens op **Windows PowerShell-Modules**.  

     Hiermee opent u de opdrachtprompt van Windows PowerShell-Modules.  

2.  Maken van een Windows PowerShell-station dat gebruikmaakt van de MDT-PowerShell-provider door het uitvoeren van de [nieuw PSDrive](http://technet.microsoft.com/library/hh849829.aspx) cmdlet, zoals weergegeven in het volgende voorbeeld:  

    ```  
    New-PSDrive -Name DS001 -PSProvider mdtprovider -Root d:\DeploymentShare$  
    ```  

3.  Weergeven van de MDT bewakingsproces door het uitvoeren van de **Get-MDTMonitorData** cmdlet, zoals weergegeven in het volgende voorbeeld:  

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

-   Importeren van het WIM-bestand dat is vastgelegd in de vorige stap in Configuration Manager, met behulp van de Wizard besturingssysteem afbeelding toevoegen, zoals beschreven in [stap 5-1: Het vastgelegde WIM-bestand importeren in Configuration Manager](#ImportCapturedwimFileintoCOnfigurationManager)  

-   Met behulp van de MDT Wizard Takenreeks maken voor het maken van een sjabloon voor sequence MDT-taak voor het implementeren van de vastgelegde installatiekopie van de referentiecomputer op de doelcomputer, zoals beschreven in [stap 5 2: Maak een MDT-Takenreeks voor het implementeren van de vastgelegde installatiekopie](#CreateMDTTaskSequencetoDeployCapturedImage)  

-   Als u de distributiepunten voor de nieuwe pakketten en installatiekopieën van de MDT Wizard Takenreeks maken maakt zoals beschreven in [stap 5-3: Selecteer de distributiepunten voor de nieuwe pakketten en installatiekopieën](#SelectDistributionPointsforNewPackagesandImages)  

-   Aanpassen van de MDT-configuratiebestanden voor de doelcomputer, met name het CustomSettings.ini-bestand, zoals beschreven in [stap 5-4: De MDT-configuratiebestanden aanpassen](#CustomizeMDTConfigurationFiles)  

-   Bijwerken van de Configuration Manager-distributiepunten voor het pakket met aangepaste instellingen, zoals beschreven in [stap 5 tot en met 5: De distributiepunten bijwerken voor het pakket met aangepaste instellingen](#UpdateDistributionPointsforCustomSettingsPackage)  

-   De takenreeks voor de doelcomputer aanpassen zoals beschreven in [stap 5 tot en met 6: De Takenreeks voor de doelcomputer aanpassen](#CustomizeTaskSequenceforTargetComputer)  

-   Installatie zonder toezicht van Office Professional Plus 2010 configureren zoals beschreven in [stap 5-7: Configureren van een installatie zonder toezicht van Office Professional Plus 2010](#ConfigureUnattendedInstallationofOfficeProPlus)  

-   Maken van een Configuration Manager-toepassing voor het implementeren van Office Professional Plus 2010, zoals beschreven in [stap 5-8: Een Office Professional Plus 2010-toepassing maken](#CreateOfficeProPlusApplication)  

-   De toepassing Office Professional Plus 2010 naar de distributiepunten distribueren, zoals beschreven in [stap 5-9: De Office Professional Plus 2010 toepassing distribueren](#DistributeOfficePeoPlusApplication)  

-   De toepassing Office Professional Plus 2010 beschikbaar maken voor alle gebruikers zoals beschreven in [stap 5-10: De Office Professional Plus 2010 toepassing beschikbaar te maken voor alle gebruikers](#MakeOfficeProPlusApplicationAvailable)  

-   De Wizard UDI-configuratiebestand aanpassen zoals beschreven in [stap 5-11: Het configuratiebestand van de UDI-Wizard voor de doelcomputer aanpassen](#CustomizeUDIWizardConfigFile)  

-   Maken van een nieuwe aangepaste wizardpagina voor het verzamelen van aanvullende implementatie-informatie, zoals beschreven in [stap 5-13: Maak een nieuwe aangepaste Wizard-pagina](#CreateNewCustomWizardPage)  

-   Besturingselementen toe te voegen aan de nieuwe aangepaste wizardpagina zoals beschreven in [stap 5-14: Besturingselementen toevoegen aan nieuwe aangepaste wizardpagina](#AddControlstoNewcustomWizardPage)  

-   Bijwerken van de MDT-pakket met het bijgewerkte configuratiebestand van de Wizard UDI zoals beschreven in bestanden [stap 5 tot 15: Update de distributiepunten voor het pakket van de MDT-bestanden](#UpdateDistributionPointsforMDTFilesPackage)  

###  <a name="ImportCapturedwimFileintoCOnfigurationManager"></a>Stap 5-1: Het vastgelegde WIM-bestand importeren in Configuration Manager  
 Nadat de installatiekopie van de referentiecomputer (WDG-REF-01) is vastgelegd naar het WIM-bestand, importeer het vastgelegde WIM-bestand naar Configuration Manager. Het vastgelegde WIM-bestand importeren in de node Besturingssysteemimages met de Wizard besturingssysteem installatiekopie toevoegen.  

 Het vastgelegde WIM-bestand bevat twee afbeeldingen, één voor elke partitie op de referentiecomputer. Identificeren welke van de installatiekopieën van het vastgelegde Windows 8.1-besturingssysteem met behulp van de beschrijving voor de installatiekopie met Windows 8.1 heeft. U kunt de installatiekopie-index gebruiken bij het maken van de takenreeks voor het implementeren van de vastgelegde installatiekopie op de doelcomputer.  

 **Het vastgelegde WIM-bestand importeren in Configuration Manager**  

1.  Klik op **Start**, wijs **alle programma's**, en wijs vervolgens **Microsoft System Center 2012**. Wijs **Configuration Manager**, en klik vervolgens op **Configuration Manager-Console**.  

2.  Klik in de Configuration Manager-console in het navigatievenster op **softwarebibliotheek**.  

3.  Ga naar overzicht/Operating Systems/Operating-installatiekopieën in de werkruimte softwarebibliotheek.  

4.  Klik op het lint in de **maken** groep, klikt u op **installatiekopie van besturingssysteem toevoegen**.  

     De Wizard besturingssysteem afbeelding toevoegen wordt gestart.  

5.  Voltooi de Wizard besturingssysteem toevoegen installatiekopie met de informatie in de tabel 30. Accepteer de standaardwaarden tenzij anders vermeld.  

    ### <a name="table-30-information-for-completing-the-add-operating-system-image-wizard"></a>Tabel 30. Informatie voor het voltooien van de Wizard installatiekopie van besturingssysteem toevoegen  

    |**Op deze wizardpagina** |**Dit doet** |  
    |-|-|  
    |**Gegevensbron** |Typ in het pad,  **\\\WDG-MDT-01\Capture$\WDG-REF-01.wim**, en klik vervolgens op **volgende**.|  
    |**Algemeen** |1.  In **naam**, type **referentie-installatiekopie voor Windows 8.1**.<br />2.  In **versie**, type **1,00**.<br />3.  In **opmerkingen**, type **Windows 8.1 vastgelegde installatiekopie van een referentiecomputer (WDG-REF-01) gebruikt om te implementeren op doelcomputers**, en klik vervolgens op **volgende**.|  
    |**Samenvatting** |Lees de informatie in de **Details** vak die die u hebt opgegeven tijdens het uitvoeren van de vorige wizardpagina's en klik vervolgens op **volgende**.|  
    |**Voortgang** |De voortgang voor het importeren van de installatiekopie van het besturingssysteem wordt weergegeven.|  
    |**Voltooiing** |Klik op **Sluiten**.|  

6.  Klik in het voorbeeldvenster op **referentie-installatiekopie voor Windows 8.1**.  

7.  Klik in het voorbeeldvenster op de **Details** tabblad.  

     De lijst met partities van besturingssysteem vastgelegd in het WIM-bestand wordt weergegeven. De installatiekopie-index met Windows 8.1 is de installatiekopie-index die u later tijdens de MDT Wizard Takenreeks maken.  

8.  Leg de installatiekopie-index met Windows 8.1.  

    > [!TIP]
    >  Installatiekopie-index 2 moet het besturingssysteem Windows 8.1 hebben voor de doeleinden van dit voorbeeld.  

###  <a name="CreateMDTTaskSequencetoDeployCapturedImage"></a>Stap 5-2: Maak een MDT-Takenreeks voor het implementeren van de vastgelegde installatiekopie  
 Nadat de installatiekopie wordt vastgelegd, moet u een takenreeks voor het implementeren van de vastgelegde installatiekopie van de referentiecomputer (WDG-REF-01) maken met de doelcomputer (WDG-CLI-01). De meeste van de pakketten die nodig zijn voor deze takenreeks zijn eerder in het proces gemaakt. Echter, moet u een nieuwe MDT aangepaste instellingen pakket dat de juiste configuratie-instellingen voor de doelcomputer en maakt een installatiekopie van het besturingssysteem van de vastgelegde installatiekopie van de referentiecomputer.  

 **Een taak sequence-sjabloon voor het implementeren van de vastgelegde installatiekopie op de doelcomputer maken**  

1.  Klik op **Start**, wijs **alle programma's**, en wijs vervolgens **Microsoft System Center 2012**. Wijs **Configuration Manager**, en klik vervolgens op **Configuration Manager-Console**.  

2.  Klik in de Configuration Manager-console in het navigatievenster op **softwarebibliotheek**.  

3.  Ga in de werkruimte softwarebibliotheek naar overzicht/Operating Systems/Takenreeksen.  

4.  Klik op het lint op de **Start** tabblad, in de **Takenreeksen** groep, klikt u op **Takenreeks MDT maken**.  

     De MDT Wizard Takenreeks maken wordt gestart.  

5.  Voltooi de MDT Wizard Takenreeks maken met de informatie in de tabel 31. Accepteer de standaardwaarden tenzij anders vermeld.  

    ### <a name="table-31-information-for-completing-the-create-mdt-task-sequence-wizard"></a>Tabel 31. Informatie voor het voltooien van de Wizard Takenreeks MDT maken  

    |**Op deze wizardpagina** |**Dit doet** |  
    |-|-|  
    |**Sjabloon kiezen** |Selecteer **Clienttakenreeks**, en klik vervolgens op **volgende**.|  
    |**Sjabloon kiezen: Algemeen** |1.  In **takenreeksnaam**, type **UDI - implementatie van Windows 8.1 doel**.<br />2.  In **Task sequence opmerkingen**, type **Takenreeks voor het implementeren van de vastgelegde referentiesysteemkopie op de doelcomputer (WDG-CLI-01) met behulp van UDI**, en klik vervolgens op **volgende**.|  
    |Sjabloon kiezen: Details|1.  In **gebruik de naam van**, type **Woodgrove Bank werknemer**.<br />2.  In **organisatienaam**, type **Woodgrove Bank**.<br />3.  Klik op **Volgende**.|  
    |**Sjabloon kiezen: Instellingen vastleggen** |Klik op **Volgende**.|  
    |**Opstartinstallatiekopie** |1.  In **opgeven van een bestaand pakket met opstartinstallatiekopie**, klikt u op **Bladeren**.<br />2.  In **pakket selecteren** in het dialoogvenster, klikt u op **Windows PE aangepaste**, en klik vervolgens op **OK**.<br />3.  Klik op **Volgende**.|  
    |**MDT-pakket** |1.  In **Geef een bestaand pakket voor Microsoft Deployment Toolkit bestanden**, klikt u op **Bladeren**.<br />2.  In de **pakket selecteren** in het dialoogvenster, klikt u op **MDT bestanden**, en klik vervolgens op **OK**.<br />3.  Klik op **Volgende**.|  
    |**Installatiekopie van het besturingssysteem** |1.  Klik op **Geef een bestaande OS-installatiekopie**.<br />2.  In **Geef een bestaande OS-installatiekopie**, klikt u op **Bladeren**.<br />3.  In de **pakket selecteren** in het dialoogvenster, klikt u op **referentie-installatiekopie voor Windows 8.1**, en klik vervolgens op **OK**.<br />4.  Klik op **Volgende**.|  
    |**Installatiekopie van het besturingssysteem: Index van de installatiekopie van het besturingssysteem** |1.  In **het gekozen besturingssysteem (WIM)-bestand meerdere installatiekopieën bevat. Geef de afbeelding die u wilt implementeren**, selecteer ***Index_van_installatiekopie*** (waarbij *Index_van_installatiekopie* is de installatiekopie-index van de installatiekopie met Windows 8.1, die is geïdentificeerd in de [Stap 5-1: Het vastgelegde WIM-bestand importeren in Configuration Manager](#ImportCapturedwimFileintoCOnfigurationManager); voor de doeleinden van deze handleiding, selecteert u 2).<br />2.  Klik op **Volgende**.|  
    |**Methode-implementatie** |Klik op **voert u een 'Driven installatie'**, en klik vervolgens op **volgende**.|  
    |**Clientpakket** |1.  In **opgeven van een bestaande ConfigMgr-clientpakket**, klikt u op **Bladeren**.<br />2.  In de **pakket selecteren** in het dialoogvenster, klikt u op **Microsoft Configuration Manager-Clientupgrade**, en klik vervolgens op **OK**.<br />3.  Klik op **Volgende**.|  
    |**USMT-pakket** |1.  In **Geef een bestaand USMT-pakket**, klikt u op **Bladeren**.<br />2.  In de **pakket selecteren** in het dialoogvenster, klikt u op **USMT**, en klik vervolgens op **OK**.<br />3.  Klik op **Volgende**.|  
    |Instellingen pakket|1.  Klik op **Maak een nieuw pakket van de instellingen**.<br />2.  In **pakketbronmap worden gemaakt**, type  **\\\WDG-MDT-01\Packages$\UDICustomSettings_Target**, en klik vervolgens op **volgende**.|  
    |**Instellingen voor pakket: Details van instellingen** |1.  In **naam**, type **UDI doel Computer aangepaste instellingen**.<br />2.  In **versie**, type **1,00**.<br />3.  In **opmerkingen**, type **configuratie-instellingen voor de MDT-implementatieproces UDI (zoals CustomSettings.ini) voor de doelcomputer met**, en klik vervolgens op **volgende**.|  
    |**Sysprep-pakket** |Klik op **Volgende**.|  
    |**Samenvatting** |Lees de informatie in de **Details** vak die die u hebt opgegeven tijdens het uitvoeren van de vorige wizardpagina's en klik vervolgens op **volgende**.|  
    |**Voortgang** |De voortgang voor het maken van de takenreeks wordt weergegeven.|  
    |**Bevestiging** |Klik op **Voltooien**.|  

 De lijst met takenreeksen wordt weergegeven. De takenreeks die u zojuist hebt gemaakt (**UDI – Windows 8.1 Doelimplementatie**) wordt vermeld in de lijst met takenreeksen.  

###  <a name="SelectDistributionPointsforNewPackagesandImages"></a>Stap 5-3: Selecteer de distributiepunten voor de nieuwe pakketten en installatiekopieën  
 Uitvoeren van de MDT Wizard Takenreeks maken voor het maken van de takenreeks voor het doel, genereert een nieuwe software-distributiepakket en een nieuwe installatiekopie. Wanneer het pakket en de installatiekopie worden gemaakt, selecteert u de distributiepunten op waarop het pakket en de installatiekopie, gekopieerd en beschikbaar zijn voor de doelcomputers worden moeten.  

> [!NOTE]
>  In dit voorbeeld is er slechts één distributiepunt (WDG-MDT-01). De meeste productienetwerken hebben echter meerdere distributiepunten. Wanneer u deze stap uitvoert in een productieomgeving, selecteer de juiste distributiepunten voor het netwerk.  

 Selecteer de distributiepunten voor het software-distributiepakket (voor het nieuwe pakket voor het aangepaste instellingen target-computer aangeroepen *MDT 2013 Computer aangepaste doelinstellingen*) en het installatiekopiepakket van het besturingssysteem (voor de nieuwe vastgelegde WIM-bestand van de referentiecomputer genoemd *referentie-installatiekopie voor Windows 8.1*).  

 **Selecteer de distributiepunten voor het software-distributiepakket**  

1.  Klik op **Start**, wijs **alle programma's**, en wijs vervolgens **Microsoft System Center 2012**. Wijs **Configuration Manager**, en klik vervolgens op **Configuration Manager-Console**.  

2.  Klik in de Configuration Manager-console in het navigatievenster op **softwarebibliotheek**.  

3.  Ga in de werkruimte softwarebibliotheek naar overzicht/Operating Systems/Takenreeksen.  

4.  Selecteer in het voorbeeldvenster **UDI - implementatie van Windows 8.1 doel**.  

     Klik op het lint op de **Start** tabblad, in de **implementatie** groep, klikt u op **inhoud distribueren**.  

     De Wizard inhoud distribueren wordt gestart.  

5.  Voltooi de Wizard inhoud distribueren met behulp van de informatie in de tabel 32. Accepteer de standaardwaarden tenzij anders vermeld.  

    ### <a name="table-32-information-for-completing-the-distribute-content-wizard"></a>Tabel 32. Informatie voor het voltooien van de Wizard inhoud distribueren  

    |**Op deze wizardpagina** |**Dit doet** |  
    |-|-|  
    |**Algemeen** |Klik op **Volgende**.|  
    |**Inhoud** |Klik op **Volgende**.|  
    |**Algemeen: Doel van inhoud** |1.  Klik op **toevoegen**, en klik vervolgens op **distributiepunt**.<br />     De **distributiepunten toevoegen** dialoogvenster wordt weergegeven.<br />2.  In de **distributiepunten toevoegen** dialoogvenster,  **\\\WDGMDT01.mdt2013.corp.woodgrovebank.com**, en klik vervolgens op **OK**.<br />     \\\WDGMDT01.mdt2013.corp.woodgrovebank.com wordt weergegeven in de **doel van inhoud** lijst.<br />3.  Klik op **Volgende**.|  
    |**Samenvatting** |Lees de informatie in de **Details** vak die die u hebt opgegeven tijdens het uitvoeren van de vorige wizardpagina's en klik vervolgens op **volgende**.|  
    |**Voortgang** |De voortgang voor het distribueren van de software wordt weergegeven.|  
    |**Voltooiing** |Klik op **Sluiten**.|  

###  <a name="CustomizeMDTConfigurationFiles"></a>Stap 5-4: De MDT-configuratiebestanden aanpassen  
 Wanneer de takenreeks voor de doelcomputer is gemaakt, aanpassen de MDT-configuratiebestanden die voorzien in de configuratie-instellingen voor Windows 8.1 implementeren met de doelcomputer, in het bijzonder CustomSettings.ini.  

 Wanneer het CustomSettings.ini-bestand is aangepast, moet u de bijgewerkte bestanden opslaan voor de bronmap voor het pakket MDT aangepaste instellingen is eerder in het proces (E:\Packages$\CustomSettings_Target) gemaakt.  

 **Voor het aanpassen van de MDT-configuratiebestanden voor de doelcomputer**  

1.  In Windows Verkenner, Ga naar de map E:\Packages$\CustomSettings_Target en dubbelklik vervolgens op **CustomSettings.ini**.  

2.  Open Kladblok en voeg de volgende regel toe aan het CustomSettings.ini-bestand dat de omgeving vereist, zoals weergegeven in de lijst 2:  

     Deze instelling wordt de bewaking van de implementatie van de computer doel geconfigureerd.  

    > [!NOTE]
    >  Breng eventuele wijzigingen die in uw omgeving vereist.  

     **Aanbieding 2. Standaard CustomSettings.ini-bestand**  

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

###  <a name="UpdateDistributionPointsforCustomSettingsPackage"></a>Stap 5 tot en met 5: De distributiepunten bijwerken voor het pakket met aangepaste instellingen  
 Wanneer de bronmap voor het pakket MDT doel Computer aangepaste instellingen in Configuration Manager is bijgewerkt, werkt u de distributiepunten voor het pakket MDT doel Computer aangepaste instellingen. De distributiepunten bijgewerkt, kopieert de bijgewerkte versie van het CustomSettings.ini-bestand naar de implementatieshares die is opgegeven in het pakket.  

 **Distributiepunten de distributiepunten bijwerken voor het pakket met aangepaste instellingen**  

1.  Klik op **Start**, wijs **alle programma's**, en wijs vervolgens **Microsoft System Center 2012**. Wijs **Configuration Manager**, en klik vervolgens op **Configuration Manager-Console**.  

2.  Klik in de Configuration Manager-console in het navigatievenster op **softwarebibliotheek**.  

3.  Ga naar overzicht/Application Management/pakketten in de werkruimte softwarebibliotheek.  

4.  Klik in het voorbeeldvenster op **MDT doel Computer aangepaste instellingen**.  

5.  Klik op het lint op de **Start** tabblad, in de **implementatie** groep, klikt u op **distributiepunten bijwerken**.  

     De **Configuration Manager** in het dialoogvenster wordt geopend, om u te informeren dat u gaat bijwerken van het pakket op alle distributiepunten.  

6.  In de **Configuration Manager** in het dialoogvenster, klikt u op **OK**.  

7.  Sluit alle geopende vensters en dialoogvensters.  

###  <a name="CustomizeTaskSequenceforTargetComputer"></a>Stap 5 tot en met 6: De Takenreeks voor de doelcomputer aanpassen  
 Voor de meeste implementaties voert de takenreeks voor implementatie van Windows 8.1 doel eerder in het proces hebt gemaakt de benodigde stappen zonder aanpassing. In dit voorbeeld wordt de taak sequence sjabloon aanpassen zodat het wachtwoord voor het lokale Administrator-account instellen in een bekende waarde. (Standaard de taakvolgorde stelt het wachtwoord voor het lokale Administrator-account op een willekeurige waarde.) De takenreeks kan vereisen verdere aanpassing afhankelijk van de omgeving.  

 **Voor het aanpassen van de takenreeks voor implementatie van Windows 8.1-doel**  

1.  Klik op **Start**, wijs **alle programma's**, en wijs vervolgens **Microsoft System Center 2012**. Wijs **Configuration Manager**, en klik vervolgens op **Configuration Manager-Console**.  

2.  Klik in de Configuration Manager-console in het navigatievenster op **softwarebibliotheek**.  

3.  Ga in de werkruimte softwarebibliotheek naar overzicht/Operating Systems/Takenreeksen.  

4.  Klik in het voorbeeldvenster op **UDI - implementatie van Windows 8.1 doel**.  

5.  Klik op het lint op de **Start** tabblad, in de **Takenreeks** groep, klikt u op **bewerken**.  

     De **Takenreeks voor implementatie van Windows 8.1-referentie-Editor** dialoogvenster wordt geopend.  

6.  In de **Takenreeks voor implementatie van Windows 8.1-referentie-Editor** in het dialoogvenster, gaat u naar de Windows-instellingen PostInstall/toepassen.  

7.  Op de **eigenschappen** tabblad **het account inschakelen en geef het lokale beheerderswachtwoord**.  

8.  Op de **eigenschappen** tabblad, in **wachtwoord** en **wachtwoord bevestigen**, type  **P@ssw0rd** , en klik vervolgens op **toepassen** .  

9. Breng eventuele aanvullende wijzigingen aan de takenreeks waarvoor de omgeving en klik vervolgens op **OK**.  

10. Sluit alle geopende vensters en dialoogvensters.  

###  <a name="ConfigureUnattendedInstallationofOfficeProPlus"></a>Stap 5-7: Configureren van een installatie zonder toezicht van Office Professional Plus 2010  
 Configuration Manager distribueert de bestanden en mappen die worden gebruikt voor het implementeren van Office Professional Plus 2010 maar voorziet niet in de methode voor het uitvoeren van een installatie zonder toezicht na het distributiepunt. De installatie zonder toezicht moet in plaats daarvan worden geconfigureerd met behulp van methoden die beschikbaar zijn in Office Professional Plus 2010. U kunt van Office Professional Plus 2010 voor installatie zonder toezicht (silent) configureren met behulp van een van de volgende methoden:  

-   Maak een bestand in Office Customization Tool (OCT) Setup aanpassing (MSP-bestand).  

-   Het bestand Config.xml wijzigen.  

 Zie voor meer informatie over elk van deze methoden [Setup aanpassen voordat u Office 2010 installeert](http://technet.microsoft.com/library/cc179121.aspx).  

 Voor de doeleinden van deze handleiding wordt de installatie zonder toezicht van Office Professional Plus 2010 worden uitgevoerd door het maken van een OCT aanpassing installatiebestand (MSP-bestand). U wordt de installatie van de OCT aanpassingsbestand opslaan in de map Updates worden automatisch gescand door de installatiewizard Office Professional Plus 2010.  

 **Een installatie zonder toezicht van Office Professional Plus 2010 configureren**  

1.  Bij een opdrachtprompt, typ de volgende opdracht en druk op ENTER.  

    ```  
    e:  
    ```  

2.  Bij een opdrachtprompt, typ de volgende opdracht en druk op ENTER.  

    ```  
    cd \Source$\OfficeProPlus2010\  
    ```  

3.  Bij een opdrachtprompt, typ de volgende opdracht en druk op ENTER.  

    ```  
    setup /admin  
    ```  

     De OCT wordt gestart, en de **Product selecteren** dialoogvenster wordt geopend.  

4.  In de OCT in de **Product selecteren** in het dialoogvenster, klikt u op **OK**.  

     De OCT laadt de juiste informatie en vervolgens worden de instellingen die kunnen worden aangepast in het MSP-bestand weergegeven.  

5.  In de OCT, in het navigatiedeelvenster, gaat u naar het Setup/installeren en naam van organisatie.  

6.  In het voorbeeldvenster in **organisatienaam**, type **Woodgrove Bank**.  

7.  Ga in de OCT, in het navigatiedeelvenster naar het Setup/Licensing en gebruikersinterface.  

8.  Selecteer in het voorbeeldvenster de **ik ga akkoord met de voorwaarden in deze gebruiksrechtovereenkomst** selectievakje.  

9. In het voorbeeldvenster in **niveau weergeeft**, selecteer **geen**.  

10. Van de **bestand** menu, klikt u op **OpslaanAls**.  

     De **OpslaanAls** dialoogvenster wordt geopend.  

11. In de **OpslaanAls** in het dialoogvenster, type **E:\Source$\OfficeProPlus2010\Updates\OPP2010_Unattend**, en klik vervolgens op **opslaan**.  

     Het bestand OPP2010_Unattend.msp wordt opgeslagen.  

12. Sluit alle geopende vensters en dialoogvensters.  

###  <a name="CreateOfficeProPlusApplication"></a>Stap 5-8: Een Office Professional Plus 2010-toepassing maken  
 Een van de voordelen van het uitvoeren van de MDT-implementaties met UDI is de mogelijkheid voor de gebruiker te selecteren van de toepassingen te installeren tijdens de implementatie. U kunt een willekeurig aantal toepassingen voor Configuration Manager toevoegen en selecteer vervolgens de toepassingen bij het uitvoeren van de Wizard UDI zoals beschreven in [stap 6-4: Start de doelcomputer met opstartbare Media voor de Takenreeks](#StartTargetComputerwithTaskSequenceBootableMedia).  

 U kunt de toepassingen die worden weergegeven in de Wizard UDI is met de ontwerpfunctie van de Wizard UDI configureren zoals beschreven in [stap 5-11: Het UDI Wizard-configuratiebestand aanpassen voor de doelcomputer](#CustomizeUDIWizardConfigFile).  

 **Een Office Professional Plus 2010-toepassing maken**  

1.  Klik op **Start**, wijs **alle programma's**, en wijs vervolgens **Microsoft System Center 2012**. Wijs **Configuration Manager**, en klik vervolgens op **Configuration Manager-Console**.  

2.  Klik in de Configuration Manager-console in het navigatievenster op **softwarebibliotheek**.  

3.  Ga naar overzicht/toepassing/beheertoepassingen in de werkruimte softwarebibliotheek.  

4.  Klik op het lint op de **Start** tabblad, in de **maken** groep, klikt u op **toepassing maken**.  

     De Wizard toepassing maken wordt gestart.  

5.  Voltooi de Wizard toepassing maken met de informatie in de tabel 33. Accepteer de standaardwaarden tenzij anders vermeld.  

    ### <a name="table-3-information-for-completing-the-create-application-wizard"></a>Tabel 3. Informatie voor het voltooien van de wizard toepassing maken  

    |**Op deze wizardpagina** |**Dit doet** |  
    |-|-|  
    |**Algemeen** |Klik op **de toepassingsinformatie handmatig opgeven**, en klik vervolgens op **volgende**.|  
    |**Algemeen: Algemeen** |1.  In **naam**, type **Microsoft Office Professional Plus 2010 – x86**.<br />2.  In **beheerderopmerkingen**, type **32-bits versie van Microsoft Office Professional Plus 2010**.<br />3.  Selecteer de **toe dat deze toepassing wordt geïnstalleerd door de takenreeksactie toepassing installeren in plaats van handmatig implementeren** selectievakje.<br />4.  Klik op **Volgende**.|  
    |**Algemeen: Application Catalog** |1.  In **gelokaliseerde beschrijving**, type **32-bits versie van Microsoft Office Professional Plus 2010 voor gebruik door werknemers van Woodgrove Bank**.<br />2.  In **trefwoorden**, **Typ Office Professional Plus 2010**.<br />3.  Klik op **Volgende**.|  
    |**Algemeen: Implementatietype s** |<ol><li>Klik op **Toevoegen**.<br /><br />     Het maken van de Wizard-implementatie Type wordt gestart.</li><li>In de **Wizard implementatietype maken**op de **algemene** pagina, klikt u op **Geef handmatig de implementatietype-informatie** en klik vervolgens op **volgende**.</li><li>Op de **algemeen: Algemene informatie** pagina, voer de volgende stappen uit en klik vervolgens op **volgende**:<br /><br /> <ol><li>In **naam**, type **Microsoft Office Professional Plus 2010 – x32 (Windows Installer)**.</li><li>In **beheerderopmerkingen**, type **implementeren van Microsoft Office Professional Plus 2010 met systeemeigen Windows Installer**.</li></ol></li><li>Op de **algemeen: Inhoud** pagina, voer de volgende stappen uit en klik vervolgens op **volgende**:<br /><br /> <ol><li>In **locatie van inhoud**, type  **\\\WDGMDT01\Source$\OfficeProPlus2010**.</li><li>In **installatieprogramma**, type **setup.exe**.</li><li>In **programma voor verwijderen**, type **setup.exe / uninstall PROPLUS**.</li></ol></li><li>Op de **algemeen: Detectiemethode** pagina, voer de volgende stappen uit en klik vervolgens op **volgende**:<br /><br /> <ol><li>Klik op toevoegen **component**,<br /><br />         De **detectieregel** dialoogvenster wordt weergegeven.</li><li>In de **detectieregel** het dialoogvenster **Instellingstype**, selecteer **Windows Installer**.</li><li>In **productcode**, klikt u op **bladeren**<br /><br />         De **Open** dialoogvenster wordt weergegeven.</li><li>In de **geopend dialoogvenster** in het vak **bestandsnaam**, type  **\\\WDGMDT01\Source$\OfficeProPlus2010\ProPlus.WW\ProPlusWW.msi**, en klik vervolgens op **Open**.<br /><br />         De productcode van Office Professional Plus 2010 wordt weergegeven in de **productcode** vak.</li><li>In de **detectieregel** in het dialoogvenster, klikt u op **OK**.</li></ol></li><li>Op de **algemeen: Gebruikerservaring** pagina, voer de volgende stappen uit en klik vervolgens op **volgende**:<br /><br /> <ol><li>In **installatiegedrag**, selecteer **installeren voor systeem**.</li><li>In **aanmeldvereiste**, selecteer **al dan niet een gebruiker is aangemeld**.</li><li>In **zichtbaarheid installatieprogramma**, selecteer **normaal**.</li><li>In **geschatte installatietijd**, type **120**.</li></ol></li><li>Op de **vereisten** pagina, klikt u op **volgende**.</li><li>Op de **afhankelijkheden** pagina, klikt u op **volgende**.</li><li>Op de **samenvatting** pagina, klikt u op **volgende**.</li><li>Op de **voltooiing** pagina, klikt u op **sluiten**.<br /><br />     De Wizard toepassing maken wordt gestart.</li><li>Klik op **Volgende**.</li></ol>|  
    |**Samenvatting** |Lees de informatie in de **Details** vak die die u hebt opgegeven tijdens het uitvoeren van de vorige wizardpagina's en klik vervolgens op **volgende**.|  
    |**Voortgang** |De voortgang voor het maken van de toepassing wordt weergegeven.|  
    |**Voltooiing** |Klik op **Sluiten**.|  

 De Office Professional Plus 2010 – x86 toepassing wordt weergegeven in het voorbeeldvenster.  

###  <a name="DistributeOfficePeoPlusApplication"></a>Stap 5-9: De Office Professional Plus 2010 toepassing distribueren  
 Nadat u de Office Professional Plus 2010-toepassing hebt gemaakt, moet u de toepassing naar de distributiepunten te distribueren. Hierdoor kunnen de installatie van de toepassing uit de distributiepunten. Er is slechts één distributiepunt (WDG-MDT-01) voor de doeleinden van deze handleiding. Bij normale implementaties van Configuration Manager zijn er meestal meerdere distributiepunten.  

 **De toepassing Office Professional Plus 2010 te distribueren**  

1.  Klik op **Start**, wijs **alle programma's**, en wijs vervolgens **Microsoft System Center 2012**. Wijs **Configuration Manager**, en klik vervolgens op **Configuration Manager-Console**.  

2.  Klik in de Configuration Manager-console in het navigatievenster op **softwarebibliotheek**.  

3.  Ga naar overzicht/toepassing/beheertoepassingen in de werkruimte softwarebibliotheek.  

4.  Klik in het voorbeeldvenster op **Microsoft Office Professional Plus 2012 – x86**.  

5.  Klik op het lint op de **Start** tabblad, in de **implementatie** groep, klikt u op **inhoud distribueren**.  

     De Wizard inhoud distribueren wordt gestart.  

6.  Voltooi de Wizard inhoud distribueren met behulp van de informatie in de tabel 34. Accepteer de standaardwaarden tenzij anders vermeld.  

    ### <a name="table-34-information-for-completing-the-distribute-content-wizard"></a>Tabel 34. Informatie voor het voltooien van de Wizard inhoud distribueren  

    |**Op deze wizardpagina** |**Dit doet** |  
    |-|-|  
    |**Algemeen** |Klik op **Volgende**.|  
    |**Algemeen: Inhoud** |Klik op **Volgende**.|  
    |**Algemeen: Doel van inhoud** |1.  Klik op **toevoegen**, en klik vervolgens op **distributiepunt**.<br />     De **distributiepunt toevoegen** punten dialoogvenster wordt weergegeven.<br />2.  In de **distributiepunten toevoegen** dialoogvenster,  **\\\WDGMDT01.mdt2013.corp.woodgrovebank.com**, en klik vervolgens op **OK**.<br />     \\\WDGMDT01.mdt2013.corp.woodgrovebank.com weergegeven in de lijst van het doel van inhoud.<br />3.  Klik op **Volgende**.|  
    |Samenvatting|Lees de informatie in de **Details** vak die die u hebt opgegeven tijdens het uitvoeren van de vorige wizardpagina's en klik vervolgens op **volgende**.|  
    |**Voortgang** |De voortgang voor het distribueren van de toepassing wordt weergegeven.|  
    |**Voltooiing** |Klik op **Sluiten**.|  

7.  Sluit alle geopende vensters en dialoogvensters.  

###  <a name="MakeOfficeProPlusApplicationAvailable"></a>Stap 5-10: De Office Professional Plus 2010 toepassing beschikbaar te maken voor alle gebruikers  
 Nadat u de Office Professional Plus 2010-toepassing hebt gemaakt, moet u de toepassing naar de distributiepunten te distribueren. Hierdoor kunnen de installatie van de toepassing uit de distributiepunten. Er is slechts één distributiepunt (WDG-MDT-01) voor de doeleinden van deze handleiding. Bij normale implementaties van Configuration Manager zijn er meestal meerdere distributiepunten.  

 **De toepassing Office Professional Plus 2010 beschikbaar maken voor alle gebruikers**  

1.  Klik op **Start**, wijs **alle programma's**, en wijs vervolgens **Microsoft System Center 2012**. Wijs **Configuration Manager**, en klik vervolgens op **Configuration Manager-Console**.  

2.  Klik in de Configuration Manager-console in het navigatievenster op **softwarebibliotheek**.  

3.  Ga naar overzicht/toepassing/beheertoepassingen in de werkruimte softwarebibliotheek.  

4.  Klik in het voorbeeldvenster op **Microsoft Office Professional Plus 2010 – x86**.  

5.  Klik op het lint op de **Start** tabblad, in de **implementatie** groep, klikt u op **implementeren**.  

     De Wizard Software implementeren wordt gestart.  

6.  Voltooi de Wizard Software implementeren met de informatie in de tabel 35. Accepteer de standaardwaarden tenzij anders vermeld.  

    ### <a name="table-35-information-for-completing-the-deploy-software-wizard"></a>Tabel 35. Informatie voor het voltooien van de Wizard Software implementeren  

    |**Op deze wizardpagina** |**Dit doet** |  
    |-|-|  
    |**Algemeen** |1.  In **verzameling**, klikt u op **Bladeren**.<br />     De **verzameling selecteren** dialoogvenster wordt weergegeven.<br />2.  In de **verzameling selecteren** in het dialoogvenster, klikt u op **alle gebruikers**, en klik vervolgens op **OK**.<br />3.  In **opmerkingen**, type **moet Microsoft Office Professional Plus 2010 beschikbaar voor implementatie naar alle gebruikers**.<br />4.  Klik op **Volgende**.|  
    |**Inhoud** |Klik op **Volgende**.|  
    |**Implementatie-instellingen** |Klik op **Volgende**.|  
    |**Plannen** |Klik op **Volgende**.|  
    |**Waarschuwingen** |Klik op **Volgende**.|  
    |**Samenvatting** |Lees de informatie in de **Details** vak die die u hebt opgegeven tijdens het uitvoeren van de vorige wizardpagina's en klik vervolgens op **volgende**.|  
    |**Voortgang** |De voortgang voor het implementeren van de toepassing wordt weergegeven.|  
    |**Voltooiing** |Klik op **Sluiten**.|  

7.  Sluit alle geopende vensters en dialoogvensters.  

###  <a name="CustomizeUDIWizardConfigFile"></a>Stap 5-11: Het configuratiebestand van de UDI-Wizard voor de doelcomputer aanpassen  
 De sjabloon van Driven installatie taak reeks bevat een takenreeksstap waarop de Wizard UDI wordt uitgevoerd. Wanneer een takenreeksstap wordt uitgevoerd van de Wizard UDI, de stap een verwijzing naar een XML-bestand dat de configuratie van de Wizard UDI bepaalt. Het bestand UDIWizard_Config.xml in de map Scripts bepaalt het gedrag van de Wizard UDI. Het UDIWizard_Config.xml-bestand met de waarde van de Wizard UDI aanpassen.  

 De waarde van de Wizard UDI bevat vooraf gedefinieerde fase groepen voor de Wizard UDI is vermeld in de tabel 36. U kunt toevoegen of verwijderen van de wizardpagina's die worden weergegeven in de Wizard UDI en de volgorde van elke pagina van de wizard voor elke fase-groep.  

### <a name="table-36-predefined-stage-groups-for-each-supported-mdt-deployment-scenario"></a>Tabel 36. Vooraf gedefinieerde fase groepen voor elk Scenario ondersteunde MDT-implementatie  

|**Fase groep** |**Beschrijving** |  
|-|-|  
|**Nieuwe Computer** |Deze fase-groep gebruiken als basis voor uw implementatie wanneer een nieuwe installatie van een Windows-besturingssysteem wordt geïmplementeerd naar een nieuwe computer en er is geen Gebruikersstatus wordt gemigreerd.|  
|**Vernieuwen** |Gebruik deze fase-groep als basis voor uw implementatie als een computer wordt vernieuwd, waaronder computers die moeten worden siteservercomputer voor installatiekopie normalisatie of om een probleem te verhelpen.|  
|**Vervangen** |Deze groep fase als basis voor uw implementatie gebruiken wanneer een computer wordt vervangen door een andere computer. De bestaande gegevens migreren is vanaf de oorspronkelijke computer opgeslagen. Vervolgens wordt een nieuwe installatie van Windows op een nieuwe computer geïmplementeerd. Ten slotte wordt de gebruikersstatusgegevens teruggezet naar de nieuwe computer.|  

 **Voor het aanpassen van het configuratiebestand van de Wizard UDI voor de referentiecomputer**  

1.  Klik op **Start**, wijs **alle programma's**, wijs **Microsoft Deployment Toolkit**, en klik vervolgens op **de Wizard UDI**.  

     De waarde van de Wizard UDI wordt gestart.  

2.  Klik op het lint op de **Start** tabblad, in de **bestandsmenu** groep, klikt u op **Open**.  

3.  In de **Open** het dialoogvenster **bestandsnaam**, type  **\\\WDG-MDT-01\Packages$\MDT_Files\Scripts\UDIWizard_Config.xml**, en klik vervolgens op **Open**.  

    > [!NOTE]
    >  Hiermee opent u de kopie van de UDIWizard_Config.xml-bestand dat zich in de MDT-pakket map die u hebt gemaakt bevindt toen u de Microsoft-implementatiewizard Takenreeks maken eerder in het proces uitgevoerd.  

4.  Klik in de bibliotheek pagina **programma's installeren**.  

5.  Klik op het lint op de **Start** tabblad, in de **instellingen bewerken** groep, klikt u op **Configuration Manager**.  

     De **Site-instellingen** dialoogvenster wordt weergegeven.  

6.  In de **dialoogvenster Instellingen voor Site** vak en klik vervolgens op de volgende stappen uitvoeren **OK**:  

    1.  In **Siteservernaam**, type **MDT-01-WDG**.  

    2.  In **sitecode**, type **NYC**.  

    3.  Klik op **valideren Site**.  

    4.  In **toepassing verzameling**, type **alle gebruikers**.  

        > [!NOTE]
        >  De Configuration Manager-verzameling die u hier opgeeft, moet overeenkomen met de Configuration Manager-verzameling waarop u uw toepassingen hebt geïmplementeerd. In deze handleiding vindt u de verzameling alle gebruikers in geselecteerde [stap 5-10: De Office Professional Plus 2010 toepassing beschikbaar te maken voor alle gebruikers](#MakeOfficeProPlusApplicationAvailable).  

7.  In het voorbeeldvenster op de **Flow** tabblad uit, vouw **StageGroup: Nieuwe Computer**.  

     De lijst van wizardpagina's in de StageGroup gebruikt: Nieuwe Computer stroom wordt weergegeven.  

    > [!NOTE]
    >  Noteer de volgorde van de wizardpagina's in de StageGroup: Stroom van de nieuwe Computer in de waarde van de Wizard UDI. Wizardpagina's in dezelfde volgorde wordt weergegeven wanneer u de Wizard UDI uitvoert in [stap 6-4: Start de doelcomputer met opstartbare Media voor de Takenreeks](#StartTargetComputerwithTaskSequenceBootableMedia).  

8.  Configureer de **StageGroup: Nieuwe Computer** stroom met de informatie voor elke pagina die worden vermeld in de tabel 37. Accepteer de standaardwaarden tenzij anders vermeld.  

    ### <a name="table-37-information-for-configuring-udi-wizard-designer-pages"></a>Tabel 37. Informatie voor het configureren van UDI wizardpagina Designer 's  

    |**Pagina van wizard** |**Klik op het tabblad configureren en voer de volgende** |  
    |-|-|  
    |**BitLocker** |<ol><li>Onder **BitLocker modus**, vouw **BitLocker modus**. In **BitLocker Checkbox**, schakelt de **dit selectievakje in eerste instantie** selectievakje.</li><li>Onder **BitLocker modus**, klikt u op **ontgrendeld** voor elk van de volgende configuratieopties:<br /><br /> <ul><li>**BitLocker selectievakje**</li><li>**Keuzerondjes voor BitLocker-modus**</li><li>**Tekstvak PINCODE**</li></ul></li></ol><br /> De status voor elke configuratieoptie **vergrendeld**, die voorkomt dat gebruikers deze opties in de Wizard UDI.|  
    |**Volume** |<ol><li>Onder **installatiekopie keuzelijst met invoervak**, vouw **gedrag van de keuzelijst met invoervak afbeelding**onder **waarden van de installatiekopie van keuzelijst met invoervak**, met de rechtermuisknop op **Windows 8.1 RTM (x 86)**, en vervolgens cliczk Selecteer een **Besturingssysteeminstallatiekopie**.<br /><br />     De **een installatiekopie van besturingssysteem selecteren** dialoogvenster wordt weergegeven.</li><li>Voltooi de **een installatiekopie van besturingssysteem selecteren** in het dialoogvenster door het uitvoeren van de volgende stappen uit en klik vervolgens op **OK**:<br /><br /> <ol><li>In **Selecteer een afbeelding/installatieprogramma besturingssysteem toevoegen**, klikt u op ***Index_van_installatiekopie*** (waarbij *Index_van_installatiekopie* is de installatiekopie-index van de installatiekopie met Windows 8.1, die is in geïdentificeerd [stap 5-1: Het vastgelegde WIM-bestand importeren in Configuration Manager](#ImportCapturedwimFileintoCOnfigurationManager); voor de doeleinden van deze handleiding, selecteer **2**).</li><li>In **weergavenaam**, type **Windows 8.1 referentie-installatiekopie – x64**.</li></ol></li><li>Onder **installatiekopie keuzelijst met invoervak**, vouw **gedrag van de keuzelijst met invoervak afbeelding**; onder **waarden van de installatiekopie van keuzelijst met invoervak**, met de rechtermuisknop op **Windows 8.1 RTM (x 86)**, en Klik vervolgens op **Item verwijderen**.<br /><br />     De **verwijderen Item bevestigen** dialoogvenster wordt weergegeven.</li><li>In de **verwijderen Item bevestigen** in het dialoogvenster, klikt u op **Ja**.</li><li>Onder **gebruikersgegevens en -instellingen**, vouw **gebruikersgedrag gegevens keuzelijst met invoervak**, en selecteer vervolgens de **indeling: Alle gegevens op het doelvolume tijdens de installatie opschonen** selectievakje.</li><li>Onder **gebruikersgedrag gegevens keuzelijst met invoervak**, klikt u op **ontgrendeld** voor elk van de volgende configuratieopties:<br /><br /> <ul><li>**Schijf formatteren**</li><li>**Windows Directory**</li></ul></li></ol><br /> De status voor elke configuratieoptie **vergrendeld**, die voorkomt dat gebruikers deze opties in de Wizard UDI.|  
    |**Details van de nieuwe Computer** |1.  Onder **netwerkdetails**, vouw **netwerkdetails**; in **domein of werkgroep keuzerondjes**, klikt u op **domein**.<br />2.  Onder **domein of werkgroep keuzerondjes**, klikt u op **ontgrendeld**.<br />     De status gewijzigd in **vergrendeld**, die voorkomt dat gebruikers deze optie in de Wizard UDI.<br />3.  Onder **netwerkdetails**, vouw **domeinen en OE**, en klik vervolgens op **domein toevoegen**.<br />     De **maken of bewerken domeingegevens** dialoogvenster wordt weergegeven.<br />4.  In de **maken of bewerken domeingegevens** het dialoogvenster **domeinnaam** type **mdt2013.corp.woodgrovebank.com**.<br />5.  In de **maken of bewerken domeingegevens** het dialoogvenster **beschrijvende naam**, type **Woodgrove Bank Active Directory-domein**, en klik vervolgens op **OK**.|  
    |**Programma's installeren** |<ol><li>Onder **-Software en -groepen**, met de rechtermuisknop op een leeg gebied en klik vervolgens op **Software groep toevoegen**.<br /><br />     De **toevoegen/bewerken van een groep Software** dialoogvenster wordt weergegeven.</li><li>In de **toevoegen/bewerken van een groep Software** het dialoogvenster **naam**, type **Woodgrove Bank toepassingen**, en klik vervolgens op **OK**.</li><li>Onder **-Software en -groepen**, klikt u op **Woodgrove Bank toepassingen**.</li><li>Klik op het lint op de **Start** tabblad, in de **algemene instellingen voor Software-Item** groep, klikt u op **toevoegen**, en klik vervolgens op **Software toevoegen aan groep**.<br /><br />     De Software toevoegen aan groep-Wizard wordt gestart.</li><li>De Software toevoegen aan groep Wizard voltooien door de volgende stappen uit te voeren:<br /><br /> <ol><li>Op de **welk type software-item wilt u toevoegen** pagina, klikt u op **ik wil een toepassing toevoegen**, en klik vervolgens op **volgende**.</li><li>Op de **zoeken Configuration Manager voor de Software-Item toevoegen** pagina **weergavenaam**, type **Microsoft Office Professional Plus 2010 – x86**.</li><li>Op de **zoeken Configuration Manager voor de Software-Item toevoegen** pagina, klikt u op **Selecteer**.<br /><br />         De **zoektoepassingen** dialoogvenster wordt weergegeven.</li><li>In de **zoektoepassingen** in het dialoogvenster, klikt u op **Search**, klikt u op **Microsoft Office Professional Plus 2010 – X86**, en klik vervolgens op **OK** .</li><li>Op de **zoeken Configuration Manager voor de Software-Item op de pagina toevoegen**, klikt u op **voltooien**.</li></ol><br />     **Microsoft Office Professional Plus 2010 – x86** wordt weergegeven onder de **Woodgrove Bank toepassingen** software-groep.</li><li>Onder **-Software en -groepen**, klikt u op **algemene Software**.</li><li>Klik op het lint op de **Start** tabblad, in de **algemene instellingen voor Software-Item** groep, klikt u op **toevoegen**, en klik vervolgens op **Item verwijderen**.<br /><br />     De **het geselecteerde Item verwijderen** dialoogvenster wordt weergegeven.</li><li>In de **het geselecteerde Item verwijderen** in het dialoogvenster, klikt u op **Ja**.</li><li>Onder **-Software en -groepen**, schakel het selectievakje voor **Woodgrove Bank toepassingen**.<br /><br />     De groep en Microsoft Office Professional Plus 2010 – x86 zijn geselecteerd.</li></ol>|  

9. Klik op het lint op de **Start** tabblad **opslaan**.  

     De **bestand opslaan** dialoogvenster wordt weergegeven.  

10. In de **bestand opslaan** in het dialoogvenster, klikt u op **OK**.  

11. Laat de waarde van de Wizard UDI geopend voor de volgende stap.  

###  <a name="CreateNewCustomWizardPage"></a>Stap 5-13: Maak een nieuwe aangepaste Wizard-pagina  
 U kunt aangepaste wizardpagina's waarmee u kunt het verzamelen van informatie over de implementatie naast de informatie die verzameld op andere pagina's van de Wizard UDI maken. Maken van aangepaste wizardpagina's op basis van de **uw eigen pagina bouwen** wizard paginatype. Nadat u de aangepaste wizardpagina hebt gemaakt, kunt u besturingselementen toevoegt en configureren van de variabelen voor de besturingselementen ingesteld.  

 Deze handleiding wil Woodgrove Bank toestaan dat gebruikers met hun gebruikersnaam en de afdeling waarin ze werken. Woodgrove Bank is departmentalized op geografische locatie. Deze informatie wordt gebruikt voor het configureren van de naam van de geregistreerde gebruiker en organisatie in Windows. In deze stap maakt toevoegen u een nieuwe aangepaste wizardpagina aan de nieuwe Computer fase-groep.  

 **Een nieuwe aangepaste wizardpagina maken**  

1.  Klik op het lint op de **Start** tabblad, in de **pagina bibliotheek** groep, klikt u op **pagina toevoegen**. De **nieuwe pagina toevoegen** dialoogvenster wordt weergegeven.  

2.  In de **nieuwe pagina toevoegen** het dialoogvenster de **paginatype** kolom, klikt u op **uw eigen pagina bouwen**.  

3.  In **weergavenaam**, type **gebruikersgegevens**.  

4.  In **paginanaam**, type **UserInformationPage**, en klik vervolgens op **OK**.  

     De **gebruikersgegevens** pagina wordt weergegeven in de bibliotheek pagina.  

5.  Klik in het detailvenster op de **Flow** tabblad.  

6.  Op de **Flow** tabblad uit, vouw de groep van de nieuwe Computer-fase.  

     De lijst met wizardpagina's in de nieuwe Computer fase-groep wordt weergegeven.  

7.  In de bibliotheek pagina Sleep de **gebruikersgegevens** pagina naar een punt direct voor de **BitLocker** pagina in de nieuwe Computer fase-groep op de **Flow** tabblad.  

8.  Klik op het lint op de **Start** tabblad **opslaan**.  

     De **bestand opslaan** dialoogvenster wordt weergegeven.  

9. In de **bestand opslaan** in het dialoogvenster, klikt u op **OK**.  

10. Laat de waarde van de Wizard UDI geopend voor de volgende stap.  

###  <a name="AddControlstoNewcustomWizardPage"></a>Stap 5-14: Besturingselementen toevoegen aan nieuwe aangepaste wizardpagina  
 Nadat de nieuwe aangepaste wizardpagina voor UDI is toegevoegd aan de computergroep voor nieuwe fase, moeten de juiste besturingselementen worden toegevoegd aan de nieuwe aangepaste wizardpagina. De besturingselementen zijn toegevoegd aan de pagina wizard Aangepaste uit de werkset van uw eigen pagina bouwen, dat wordt weergegeven wanneer u de aangepaste wizardpagina weergeven op de **configureren** tabblad in de waarde van de Wizard UDI.  

 Tabel 38 bevat de typen besturingselementen naar uw aangepaste wizardpagina dat wordt weergegeven in afbeelding 1.  

### <a name="table-38-types-of-controls-in-the-udi-build-your-own-page-toolbox"></a>Tabel 38. Typen besturingselementen in de UDI bouwen uw eigen pagina werkset  

|**Besturingselementtype** |**Beschrijving** |  
|-|-|  
|**Checkbox** |Dit besturingselement kunt u selecteren of wissen van een configuratieoptie en gedraagt zich als een selectievakje voor traditionele gebruiker gebruikersinterface (UI). Dit besturingselement heeft een bijbehorende label dat u gebruiken kunt om te beschrijven van het doel van het selectievakje in. De status van dit besturingselement is waar als het selectievakje is ingeschakeld en ONWAAR wanneer het selectievakje is uitgeschakeld. De status van het selectievakje wordt opgeslagen in de takenreeksvariabele die is geconfigureerd voor dit besturingselement. Zie voor meer informatie over dit besturingselement 'Selectievakje Control' in het document MDT *Toolkit verwijzing*.|  
|**Combobox** |Dit besturingselement kunt u een item selecteren uit een lijst met items en gedraagt zich als een vervolgkeuzelijst traditionele gebruikersinterface. Dit besturingselement kunt u toevoegen of verwijderen van items uit de lijst en geef een overeenkomende waarde die in de takenreeksvariabele die is geconfigureerd voor dit besturingselement worden ingesteld. Zie voor meer informatie over dit besturingselement 'Keuzelijst met invoervak' in het document MDT *Toolkit verwijzing*.|  
|**Line** |Dit besturingselement kunt u een horizontale lijn delen van een deel van de aangepaste wizardpagina van een andere toevoegen. Dit besturingselement verzamelt niet alle configuratiewaarden, maar in plaats daarvan wordt gebruikt voor het verbeteren van de gebruikersinterface visueel. Zie voor meer informatie over dit besturingselement 'Regel Control' in het document MDT *Toolkit verwijzing*.|  
|**Label** |Dit besturingselement kunt u beschrijvende, alleen-lezen tekst toevoegen aan de wizardpagina. Dit besturingselement verzamelt niet alle configuratiewaarden, maar in plaats daarvan wordt gebruikt voor het verbeteren van de gebruikersinterface visueel. Zie voor meer informatie over dit besturingselement 'Labelbesturingselement' in het document MDT *Toolkit verwijzing*.|  
|**Radio** |Dit besturingselement kunt u een configuratieoptie selecteren uit een groep van twee of meer opties. Net als bij traditionele keuzerondjes, twee of meer van deze besturingselementen kunnen worden gegroepeerd, en vervolgens de gebruiker kunt selecteren een van de opties in de groep met keuzerondjes. Een unieke waarde is toegewezen aan elke optie. De waarde die is toegewezen aan de geselecteerde optie-besturingselement wordt opgeslagen in de takenreeksvariabele die is geconfigureerd voor dit besturingselement. Zie voor meer informatie over dit besturingselement 'Keuzerondjes Control' in het document MDT *Toolkit verwijzing*.|  
|**Bitmap** |Dit besturingselement kunt u een bitmapafbeelding (bmp-bestand) toevoegen aan de aangepaste wizardpagina. Dit besturingselement verzamelt niet alle configuratiewaarden, maar in plaats daarvan wordt gebruikt voor het verbeteren van de gebruikersinterface visueel. Het pad naar het bmp-bestand is gebaseerd op de locatie van de Wizard UDI (OSDSetupWizard.exe). Zie voor meer informatie over dit besturingselement 'Bitmap Control' in het document MDT *Toolkit verwijzing*.|  
|**Textbox** |Dit besturingselement kunt u tekst op de pagina wizard Aangepaste invoeren. De tekst die in dit besturingselement getypt wordt opgeslagen in de takenreeksvariabele die is geconfigureerd voor dit besturingselement. Zie voor meer informatie over dit besturingselement 'Besturingselement Textbox' in het document MDT *Toolkit verwijzing*.|  

 U kunt toevoegen om een combinatie van deze besturingselementen naar uw aangepaste wizardpagina op basis van de informatie die u wilt verzamelen. Bovendien kunt u de **rasterlijnen weergeven** selectievakje in als de rasterlijnen die kunnen worden gebruikt om te helpen bij het ontwerpen van de aangepaste wizardpagina visueel weergeven of verbergen.  

 Voor de doeleinden van dit voorbeeld maakt u een aangepaste wizardpagina zoals geïllustreerd in afbeelding 1.  

 ![QuickStartGuideforUDI](media/QuickStartGuideforUDI.jpg "QuickStartGuideforUDI")  
Afbeelding 1. Aangepaste wizardpagina worden gemaakt  

 **Afbeelding 1. Aangepaste wizardpagina worden gemaakt**  

 **Besturingselementen toevoegen aan de nieuwe aangepaste wizardpagina**  

1.  Klik in de bibliotheek pagina **gebruikersgegevens** pagina.  

2.  Klik in het detailvenster op de **configureren** tabblad.  

     De werkset van uw eigen pagina bouwen en de lege wizardpagina worden weergegeven.  

3.  In de werkset van uw eigen pagina bouwen, sleept u de **Label** beheer om de lege wizardpagina op ongeveer de volgende coördinaten:  

    -   *x* = 30  

    -   *y* = 5  

     Het labelbesturingselement is geplaatst op de wizardpagina en de naam *label1*.  

4.  Klik op de pagina wizard aangepaste **label1** (het labelbesturingselement toegevoegd in stap 3).  

     Dit besturingselement fungeert als een kop voor de aangepaste wizardpagina en het doel van de pagina beschrijft.  

5.  Configureer de Indelingseigenschappen van **label1** op de **lay-out** tabblad met de informatie in de tabel 39. Accepteer de standaardwaarden tenzij anders vermeld.  

    ### <a name="table-39-label1-layout-properties"></a>Tabel 39. Eigenschappen voor de indeling Label1  

    |**Eigenschap** |**Waarde** |  
    |-|-|  
    |**Label** |Gebruiker en organisatie-informatie|  
    |**X** |30|  
    |**Y** |5|  

6.  In de werkset van uw eigen pagina bouwen, sleept u de **Label** beheer om de lege wizardpagina op ongeveer de volgende coördinaten:  

    -   *x* = 60  

    -   *y* = 60  

     Het labelbesturingselement is geplaatst op de wizardpagina en de naam *label2*.  

7.  Klik op de pagina wizard aangepaste **label2** (het besturingselement in de vorige stap hebt toegevoegd).  

     Dit besturingselement fungeert als een label voor het tekstvak dat wordt gebruikt voor het invoeren van de gebruikersnaam.  

8.  Configureer de Indelingseigenschappen van **label2** op de **lay-out** tabblad met de informatie in de tabel 40. Accepteer de standaardwaarden tenzij anders vermeld.  

    ### <a name="table-40-lable2-layout-properties"></a>Tabel 40. Eigenschappen voor de indeling lable2  

    |**Eigenschap** |**Waarde** |  
    |-|-|  
    |**Label** |Gebruikersnaam|  
    |**X** |60|  
    |**Y** |60|  

9. In de werkset van uw eigen pagina bouwen, klik en sleep de **Textbox** beheer om de lege wizardpagina op ongeveer de volgende coördinaten:  

    -   *x* = 60  

    -   *y* = 80  

     De **Textbox** besturingselement is geplaatst op de wizardpagina en de naam *Tekst1*.  

10. Klik op de pagina wizard aangepaste **Tekst1** (het besturingselement in de vorige stap hebt toegevoegd).  

     Dit besturingselement is gebruikt voor het invoeren van de gebruikersnaam in van het tekstvak.  

11. Configureer de Indelingseigenschappen van **Tekst1** op de **lay-out** tabblad met de informatie in de tabel 41. Accepteer de standaardwaarden tenzij anders vermeld.  

    ### <a name="table-41-text1-layout-properties"></a>Tabel 41. Eigenschappen voor de indeling Tekst1  

    |**Eigenschap** |**Waarde** |  
    |-|-|  
    |**X** |60|  
    |**Y** |80|  
    |**Breedte** |400|  

12. Configureer de eigenschappen van de instellingen van **Tekst1** op de **instellingen** tabblad met de informatie in de tabel 42. Accepteer de standaardwaarden tenzij anders vermeld.  

    ### <a name="table-42-text1-settings-properties"></a>Tabel 42. Eigenschappen voor Tekst1  

    |**Eigenschap** |**Waarde** |  
    |-|-|  
    |**Variabele naam op van takenreeks** |**FullName** |  
    |**Beschrijvende weergavenaam zichtbaar in de pagina overzicht** |De naam van de geregistreerde gebruiker|  

13. In de werkset van uw eigen pagina bouwen, sleept u de **Label** beheer om de lege wizardpagina op ongeveer de volgende coördinaten:  

    -   *x* = 60  

    -   *y* = 60  

     De **Label** besturingselement is geplaatst op de wizardpagina en de naam *label3*.  

14. Klik op de pagina wizard aangepaste **label3** (het besturingselement in de vorige stap hebt toegevoegd).  

     Dit besturingselement fungeert als een label voor de keuzelijst met invoervak gebruikt voor het selecteren van de organisatie of de naam van de afdeling voor de gebruiker.  

15. Configureer de Indelingseigenschappen van **lable3** op de **lay-out** tabblad met de informatie in de tabel 43. Accepteer de standaardwaarden tenzij anders vermeld.  

    ### <a name="table-43-lable3-layout-properties"></a>Tabel 43. Eigenschappen voor de indeling lable3  

    |**Eigenschap** |**Waarde** |  
    |-|-|  
    |**Label** |De naam van organisatie of afdeling|  
    |**X** |60|  
    |**Y** |121|  

16. In de werkset van uw eigen pagina bouwen, sleept u de **Combobox** beheer om de lege wizardpagina op ongeveer de volgende coördinaten:  

    -   *x* = 60  

    -   *y* = 140  

     De **Combobox** besturingselement is geplaatst op de wizardpagina en de naam *combo1*.  

17. Klik op de pagina wizard aangepaste **combo1** (het besturingselement in de vorige stap hebt toegevoegd).  

     Dit besturingselement is de keuzelijst met invoervak gebruikt voor het selecteren van de naam van de organisatie.  

18. Configureer de Indelingseigenschappen van **combo1** op de **lay-out** tabblad met de informatie in de tabel 44. Accepteer de standaardwaarden tenzij anders vermeld.  

    ### <a name="table-44-combo1-layout-properties"></a>Tabel 44. Eigenschappen voor de indeling Combo1  

    |**Eigenschap** |**Waarde** |  
    |-|-|  
    |**X** |60|  
    |**Y** |80|  
    |**Breedte** |400|  

19. Gegevensitems toevoegen aan de lay-eigenschappen van **combo1** op de **lay-out** tabblad met de informatie in de tabel 45. Accepteer de standaardwaarden tenzij anders vermeld.  

    ### <a name="table-45-combo1-data-items"></a>Tabel 45. Combo1 gegevensitems  

    |**Waarde** |**Waarde weergeven** |  
    |-|-|  
    |**Woodgrove Bank – New York City** |Woodgrove Bank – New York City|  
    |**Woodgrove Bank – Dallas** |Woodgrove Bank – Dallas|  
    |**Woodgrove Bank – Chicago** |Woodgrove Bank – Chicago|  
    |**Woodgrove Bank – Haarlem** |Woodgrove Bank – Haarlem|  

20. Configureer de eigenschappen van de instellingen van **combo1** op de **instellingen** tabblad met de informatie in de tabel 46. Accepteer de standaardwaarden tenzij anders vermeld.  

    ### <a name="table-46-combo1-settings-properties"></a>Tabel 46. Eigenschappen voor Combo1  

    |**Eigenschap** |**Waarde** |  
    |-|-|  
    |**Variabele naam op van takenreeks** |**OrgName** |  
    |Beschrijvende weergavenaam zichtbaar in de pagina overzicht|Geregistreerde organisatienaam|  

21. Klik op het lint op de **Start** tabblad **opslaan**.  

     De **bestand opslaan** dialoogvenster wordt weergegeven.  

22. In de **bestand opslaan** in het dialoogvenster, klikt u op **OK**.  

23. Sluit de Wizard UDI Designer.  

###  <a name="UpdateDistributionPointsforMDTFilesPackage"></a>Stap 5 tot 15: Update de distributiepunten voor het pakket van de MDT-bestanden  
 Na het configuratiebestand van de Wizard UDI UDIWizard_Config.xml, voor het pakket met de MDT-bestanden in Configuration Manager is bijgewerkt, werkt de distributiepunten voor het pakket MDT-bestanden. De distributiepunten bijgewerkt, kopieert de bijgewerkte versie van het bestand UDIWizard_Config.xml naar de implementatieshares die is opgegeven in het pakket.  

 **Bijwerken van de distributiepunten voor het pakket MDT-bestanden**  

1.  Klik op **Start**, wijs **alle programma's**, en wijs vervolgens **Microsoft System Center 2012**. Wijs **Configuration Manager**, en klik vervolgens op **Configuration Manager-Console**.  

2.  Klik in de Configuration Manager-console in het navigatievenster op **softwarebibliotheek**.  

3.  Ga naar overzicht/Application Management/pakketten in de werkruimte softwarebibliotheek.  

4.  Klik in het voorbeeldvenster op **MDT bestanden**.  

5.  Klik op het lint op de **Start** tabblad, in de **implementatie** groep, klikt u op **distributiepunten bijwerken**.  

     De **Configuration Manager** in het dialoogvenster wordt geopend, om u te informeren dat u gaat bijwerken van het pakket op alle distributiepunten.  

6.  In de **Configuration Manager** in het dialoogvenster, klikt u op **OK**.  

7.  Sluit alle geopende vensters en dialoogvensters.  

 Configuration Manager wordt gestart op de distributiepunten bijwerken met de nieuwste versies van het bestand UDIWizard_Config.xml. Dit proces kan enkele minuten duren. Controleer de status van het pakket totdat de **laatste Update** waarde van de pakketstatus is bijgewerkt naar een recente datum en tijd.  

## <a name="step-6-deploy-the-captured-image-of-the-reference-computer-to-the-target-computer"></a>Stap 6: De vastgelegde installatiekopie van de referentiecomputer implementeren op de doelcomputer  
 Wanneer u de installatiekopie van de referentiecomputer vastgelegd en gemaakt en de takenreeks wordt geconfigureerd, moet u de vastgelegde installatiekopie implementeren. Configureer MDT om op te geven van alle benodigde configuratie-instellingen implementeren op de doelcomputer. De installatiekopie van de referentiecomputer met Windows 8.1 is na het initiëren van het implementatieproces automatisch geïmplementeerd op de doelcomputer en geconfigureerd met de instellingen die zijn gedefinieerd.  

 De vastgelegde installatiekopie door implementeren:  

-   De doelcomputer toevoegen aan de database van de Configuration Manager-site, zoals beschreven in [stap 6-1: De doelcomputer toevoegen aan de sitedatabase van Configuration Manager](#AddTargetComputertoConfigureManagerSite)  

-   Maken van een computerverzameling die de doelcomputer bevat zoals beschreven in [stap 6 2: Maak een Computerverzameling met de doelcomputer](#CreateComputerCollectionThatIncludesTargetComputer)  

-   Implementeer de takenreeks die eerder in het proces wordt gemaakt, zoals beschreven in [stap 6-3: Implementeer de Takenreeks van de doel-Computer](#DeployTargetComputerTaskSequence)  

-   Starten van de doelcomputer met opstartbare media voor de takenreeks, zoals beschreven in [stap 6-4: Start de doelcomputer met opstartbare Media voor de Takenreeks](#StartTargetComputerwithTaskSequenceBootableMedia)  

###  <a name="AddTargetComputertoConfigureManagerSite"></a>Stap 6-1: De doelcomputer toevoegen aan de sitedatabase van Configuration Manager  
 Voor het implementeren van een besturingssysteem zonder zelfstandige media naar een nieuwe computer die Configuration Manager momenteel niet beheert, moet u de nieuwe computer toevoegen aan de Configuration Manager-sitedatabase vóór het starten van het implementatieproces van het besturingssysteem. Configuration Manager kan automatisch detecteren van computers in het netwerk met een Windows-besturingssysteem geïnstalleerd. Als de computer geen besturingssysteem geïnstalleerd is, gebruiken, de Wizard computergegevens importeren naar de nieuwe computergegevens importeren.  

 **De doelcomputer toevoegen aan de sitedatabase van Configuration Manager**  

1.  Klik op **Start**, wijs **alle programma's**, en wijs vervolgens **Microsoft System Center 2012**. Wijs **Configuration Manager**, en klik vervolgens op **Configuration Manager-Console**.  

2.  Klik in de Configuration Manager-console in het navigatievenster op **activa en naleving**.  

3.  In de activa en naleving werkruimte, gaat u naar overzicht/apparaten.  

4.  Klik op het lint op de **Start** tabblad, in de **maken** groep, klikt u op **computergegevens importeren**.  

     De Wizard computergegevens importeren wordt gestart.  

5.  Voltooi de Wizard computergegevens importeren met de informatie in de tabel 47. Accepteer de standaardwaarden tenzij anders vermeld.  

    ### <a name="table-47-information-for-completing-import-computer-information-wizard"></a>Tabel 47. Informatie over het voltooien van de Wizard computergegevens importeren  

    |Op deze wizardpagina |Voer deze handeling uit |  
    |-|-|  
    |**Bron selecteren** |Klik op **Eén computer importeren**, en klik vervolgens op **volgende**.|  
    |**Bron selecteren: Één Computer** |1.  In **computernaam**, type **CLI-01-WDG**.<br />2.  In *MAC-adres*, type ***Mac*** (waarbij *Mac* MAC-adres van de primaire-netwerkadapter voor de doelcomputer, CLI-01-WDG).<br />3.  Klik op **Volgende**.|  
    |**Bron selecteren: Voorbeeld van gegevens** |Klik op **Volgende**.|  
    |**Bron selecteren: Kies doelverzameling** |Klik op **Volgende**.|  
    |**Samenvatting** |Lees de informatie in de **Details** vak die die u hebt opgegeven tijdens het uitvoeren van de vorige wizardpagina's en klik vervolgens op **volgende**.|  
    |**Progress** |De voortgang voor het importeren van de computer wordt weergegeven.|  
    |**Bevestiging** |Klik op **Sluiten**.|  

 Zie voor meer informatie over het toevoegen van een nieuwe computer aan de sitedatabase van Configuration Manager de sectie ' voor het importeren van computergegevens voor één computer' in de sectie 'Hoe te implementeren van besturingssystemen in Configuration Manager,' in de configuratie Documentatiebibliotheek Manager, die met Configuration Manager is geïnstalleerd.  

###  <a name="CreateComputerCollectionThatIncludesTargetComputer"></a>Stap 6-2: Maak een Computerverzameling met de doelcomputer  
 In de Configuration Manager-console maakt een verzameling die de doelcomputer (WDG-CLI-01) bevat. U gebruikt deze computerverzameling later wanneer reclame van de takenreeks die eerder in het proces hebt gemaakt.  

 **Om de computerverzameling van een met de doelcomputer te maken**  

1.  Klik op **Start**, wijs **alle programma's**, en wijs vervolgens **Microsoft System Center 2012**. Wijs **Configuration Manager**, en klik vervolgens op **Configuration Manager-Console**.  

2.  Klik in de Configuration Manager-console in het navigatievenster op **activa en naleving**.  

3.  In de activa en naleving werkruimte, gaat u naar overzicht/Apparaatverzamelingen.  

4.  Klik op het lint op de **Start** tabblad, in de **maken** groep, klikt u op **Apparaatverzameling maken**.  

     De Wizard Apparaatverzameling maken wordt gestart.  

5.  Voltooi de Wizard Apparaatverzameling maken met de informatie in de tabel 48. Accepteer de standaardwaarden tenzij anders vermeld.  

    ### <a name="table-48-information-for-completing-the-create-device-collection-wizard"></a>Tabel 48. Informatie voor het voltooien van de wizard Apparaatverzameling maken  

    |**Op deze wizardpagina** |**Dit doet** |  
    |-|-|  
    |**Algemeen** |<ol><li>In **naam**, type **Microsoft Deployment – Batch 01**.</li><li>In **Opmerking**, type **Computers die moeten worden opgenomen in de eerste batch van computers die zijn geïmplementeerd**.</li><li>In **beperkte verzameling**, klikt u op **Bladeren**.<br /><br />     De **bladeren verzamelingen** dialoogvenster wordt weergegeven. Voer in het dialoogvenster door de volgende stappen uit te voeren:<br /><br /> <ol><li>In de **verzameling Bladeren** het dialoogvenster **naam**, klikt u op **alle systemen**.</li><li>Klik op **OK**.</li></ol></li><li>Klik op **Volgende**.</li></ol>|  
    |**Lidmaatschapsregels** |<ol><li>Klik op **regel toevoegen**, en klik vervolgens op **directe regel**.<br /><br />     De Wizard regel voor Direct lidmaatschap maken wordt gestart.</li><li>Voltooi de Wizard regel voor Direct lidmaatschap maken door de volgende stappen uit te voeren:<br /><br /> <ol><li>Klik op de pagina **Welkom** op **Volgende**.</li><li>Op de **zoeken naar Resources** pagina **bronklasse**, selecteer **systeembron**; in **kenmerknaam**, selecteer  **Naam**; in **waarde**, type **WDG-CLI-01**; en klik vervolgens op **volgende**.</li><li>Op de **Resources selecteren** pagina **WDG-CLI-01**, en klik vervolgens op **volgende**. **Opmerking:**          De voor het toevoegen van de doelcomputer (WDG-CLI-01) aan alle systemen kan enkele minuten duren om te voltooien. Als de CLI-01-WDG niet wordt weergegeven in de lijst, Herhaal stap b en c totdat WDGCLI01 wordt weergegeven.</li><li>Op de **samenvatting** pagina, klikt u op **volgende**.</li><li>Op de **voltooiing** pagina, klikt u op **sluiten**.</li></ol></li><li>Klik op **Volgende**.</li></ol>|  
    |**Samenvatting** |Lees de informatie in de **Details** vak die die u hebt opgegeven tijdens het uitvoeren van de vorige wizardpagina's en klik vervolgens op **volgende**.|  
    |**Progress** |De voortgang voor het maken van de apparatenverzameling wordt weergegeven.|  
    |**Voltooiing** |Klik op **Sluiten**.|  

 Zie de sectie 'Hoe te maken van verzamelingen in Configuration Manager,' in de Documentatiebibliotheek van Configuration Manager, dat geïnstalleerd is met Configuration Manager voor meer informatie.  

###  <a name="DeployTargetComputerTaskSequence"></a>Stap 6-3: Implementeer de Takenreeks van de doel-Computer  
 Implementeer de takenreeks die eerder in het proces voor de doelcomputers gemaakt in de Configuration Manager-console. De takenreeks implementeren voor de verzameling van doelcomputers die eerder in het proces hebt gemaakt.  

 **De takenreeks implementeren**  

1.  Klik op **Start**, wijs **alle programma's**, en wijs vervolgens **Microsoft System Center 2012**. Wijs **Configuration Manager**, en klik vervolgens op **Configuration Manager-Console**.  

2.  Klik in de Configuration Manager-console in het navigatievenster op **softwarebibliotheek**.  

3.  Ga in de werkruimte softwarebibliotheek naar overzicht/Operating Systems/Takenreeksen.  

4.  Klik in het voorbeeldvenster op **UDI - implementatie van Windows 8.1 doel**.  

5.  Klik op het lint op de **Start** tabblad, in de **implementatie** groep, klikt u op **implementeren**.  

     De Wizard Software implementeren wordt gestart.  

6.  Voltooi de Wizard Software implementeren met de informatie in de tabel 49. Accepteer de standaardwaarden tenzij anders vermeld.  

    ### <a name="table-49-information-for-completing-the-deploy-software-wizard"></a>Tabel 49. Informatie voor het voltooien van de Wizard Software implementeren  

    |**Op deze wizardpagina** |**Dit doet** |  
    |-|-|  
    |**Algemeen** |1.  In **verzameling**, klikt u op **Bladeren**.<br />2.  In de **verzameling Bladeren** in het dialoogvenster, klikt u op **Microsoft Deployment – Batch 01**, en klik vervolgens op **OK**.<br />3.  In **Opmerking**, type **Windows 8.1 implementeren naar de eerste batch van doelcomputers via UDI**.<br />4.  Klik op **Volgende**.|  
    |**Implementatie-instellingen** |1.  In **doel**, selecteer **beschikbaar**.<br />2.  Selecteer de **beschikbaar maken voor opstartmedia en PXE** selectievakje.<br />3.  Klik op **Volgende**.|  
    |**Implementatie-instellingen: Planning** |Klik op **Volgende**.|  
    |**Implementatie-instellingen: Gebruikerservaring** |Klik op **Volgende**.|  
    |**Implementatie-instellingen: Waarschuwingen** |Klik op **Volgende**.|  
    |**Implementatie-instellingen: Distributiepunten** |Klik op **Volgende**.|  
    |**Samenvatting** |Lees de informatie in de **Details** vak die die u hebt opgegeven tijdens het uitvoeren van de vorige wizardpagina's en klik vervolgens op **volgende**.|  
    |**Progress** |De voortgang voor het maken van de implementatie van de takenreeks wordt weergegeven.|  
    |**Voltooiing** |Klik op **Sluiten**.|  

 Zie de sectie 'Hoe te implementeren van een Takenreeks,' in de Documentatiebibliotheek van Configuration Manager, dat geïnstalleerd is met Configuration Manager voor meer informatie.  

###  <a name="StartTargetComputerwithTaskSequenceBootableMedia"></a>Stap 6-4: Start de doelcomputer met opstartbare Media voor de Takenreeks  
 Start de doelcomputer (WDG-CLI-01) met opstartbare media voor de takenreeks eerder in het proces hebt gemaakt. Dit medium wordt Windows PE gestart op de referentiecomputer en start het proces MDT. Windows 8.1 wordt aan het einde van het proces MDT geïmplementeerd op de doelcomputer.  

> [!NOTE]
>  U kunt ook de MDT-proces starten door het starten van de doelcomputer vanaf de Windows Deployment Services.  

 **Starten van de doelcomputer met opstartbare media voor de takenreeks**  

1.  CLI-01-WDG beginnen met opstartbare media voor de takenreeks eerder in het proces hebt gemaakt.  

     Windows PE wordt gestart en vervolgens de Wizard Takenreeks wordt gestart.  

2.  Voltooi de Wizard Takenreeks met de informatie in de tabel 50. Accepteer de standaardwaarden tenzij anders vermeld.  

    ### <a name="table-50-information-for-completing-the-task-sequence-wizard"></a>Tabel 50. Informatie over het voltooien van de Wizard Takenreeks  

    |**Op deze wizardpagina** |**Dit doet** |  
    |-|-|  
    |**Welkom bij de Wizard Takenreeks** |In **wachtwoord**, type  **P@ssw0rd** , en klik vervolgens op **volgende**.|  
    |**Selecteer een Takenreeks** |Selecteer in de keuzelijst **UDI - implementatie van Windows 8.1 doel**, en klik vervolgens op **volgende**.|  

     Op de juiste takenreeksstap, wordt de Wizard UDI implementatie gestart.  

3.  Voltooi de Wizard UDI implementatie met de informatie in de tabel 51. Accepteer de standaardwaarden tenzij anders vermeld.  

    ### <a name="table-51-information-for-udi-deployment-wizard"></a>Tabel 51. Informatie voor de Wizard UDI implementeren  

    |**Op deze wizardpagina** |**Dit doet** |  
    |-|-|  
    |**Welcome** |Klik op **Volgende**.|  
    |**Gebruikersgegevens** |1.  In **gebruikersnaam** type **Woodgrove Bank Chicago werknemer**.<br />2.  In **organisatie of de naam van de afdeling**, selecteer **Woodgrove Bank – Chicago**.<br />3.  Klik op **Volgende**.|  
    |**BitLocker** |Klik op **Volgende**.|  
    |**Volume** |Klik op **Volgende**.|  
    |**Doel selecteren** |Klik op **Volgende**.|  
    |**Gereedheid voor implementatie** |1.  Lees de controles van de configuratie en zorg ervoor dat de status voor alle controles zijn ingesteld op **geslaagd**.<br />2.  Klik op *Volgende*.|  
    |**Details van de nieuwe Computer** |1.  In **computernaam**, type **CLI-01-WDG**. **Opmerking:**      In scenario's voor onbekende computers, kunnen de gebruikers de computernaam wijzigen op de juiste waarde.<br />2.  In **gebruikersnaam**, type **MDT2013\Administrator**.<br />3.  In **wachtwoord** en **wachtwoord bevestigen**, type  **P@ssw0rd** .<br />4.  Klik op **Volgende**.|  
    |**Administrator-wachtwoord** |1.  In **beheerderswachtwoord** en **wachtwoord bevestigen**, type  **P@ssw0rd** .<br />2.  Klik op **Volgende**.|  
    |**Gebruikersaffiniteit apparaat** |Selecteer de **Set primaire gebruiker** selectievakje en klik vervolgens op **volgende**.|  
    |**Taal** |Klik op **Volgende**.|  
    |**Programma's installeren** |Controleer de **Microsoft Office Professional Plus 2010 – x86** selectievakje is ingeschakeld en klik vervolgens op **volgende**.|  
    |Samenvatting|Bekijk de informatie die u hebt opgegeven tijdens het voltooien van de vorige wizardpagina's en klik vervolgens op **voltooien**.|  

 **Het implementatieproces van de verwijzing naar computer met behulp van de implementatie-Workbench bewaken**  

1.  Klik op WDG-MDT-01 **Start**, en wijs vervolgens **alle programma's**. Wijs **Microsoft Deployment Toolkit**, en klik vervolgens op **implementatie-Workbench**.  

2.  In de consolestructuur van de implementatie-Workbench gaat u naar de implementatie Workbench/implementatie Shares/MDT-Implementatieshare (C:\DeploymentShare$)/Monitoring.  

3.  In het detailvenster het implementatieproces voor WDG-REF-01 te bekijken.  

4.  Klik in het deelvenster Acties periodiek op **vernieuwen**.  

     De status van het implementatieproces is bijgewerkt in het detaildeelvenster. Blijven volgen het implementatieproces totdat het proces voltooid is.  

5.  Klik in het detailvenster op **WDG-REF-01**.  

6.  Klik in het deelvenster Acties op **eigenschappen**.  

     De **WDG-REF-01-eigenschappen** in het dialoogvenster wordt weergegeven.  

7.  In de **WDG-REF-01-eigenschappen** in het dialoogvenster op de **identiteit** tabblad, de controle-informatie gegeven over het implementatieproces, zoals beschreven in de tabel 52 weergeven.  

    ### <a name="table-52-monitoring-information-about-the-deployment-process"></a>Tabel 52. Bewaking van informatie over het implementatieproces  

    |**Informatie** |**Beschrijving** |  
    |-|-|  
    |**ID** |De unieke id voor de computer wordt geïmplementeerd.|  
    |**Computernaam** |De naam van de computer wordt geïmplementeerd.|  
    |Implementatiestatus|De huidige status van de computer wordt geïmplementeerd; de status kan een van de volgende zijn:<br /><br /> -   **Met**. De takenreeks is in orde en wordt uitgevoerd.<br />-   **Kan geen**. De takenreeks is mislukt en het implementatieproces is mislukt.<br />-   **Voltooid**. De takenreeks is voltooid.<br />-   **Niet-reagerende**. De takenreeks heeft de status ervan niet bijgewerkt in de afgelopen vier uur en wordt ervan uitgegaan dat niet meer reageert.|  
    |**Stap** |De huidige takenreeksstap wordt uitgevoerd.|  
    |**Progress** |De algemene voortgang van de takenreeks wordt uitgevoerd. De voortgangsbalk geeft aan hoeveel takenreeksstappen van het totale aantal met takenreeksstappen zijn uitgevoerd.|  
    |**Start** |De tijd die het implementatieproces gestart.|  
    |**End** |De tijd die het implementatieproces is beëindigd.|  
    |**Verstreken** |Hoe lang het implementatieproces actief is geweest of duurde om uit te voeren als de implementatie is voltooid.|  
    |**Fouten** |Het aantal fouten zijn opgetreden tijdens het implementatieproces.|  
    |**Waarschuwingen** |Het aantal waarschuwingen aangetroffen tijdens het implementatieproces.|  
    |**Extern bureaublad** |Deze knop kunt u extern bureaublad verbinding te maken met de computer wordt geïmplementeerd met behulp van de functie Extern bureaublad van Windows. Deze methode wordt ervan uitgegaan dat:<br /><br /> -Het beoogde besturingssysteem wordt uitgevoerd en ondersteuning voor externe bureaublad is ingeschakeld<br />-   **mstsc.exe** zich in het pad **Opmerking:**  Deze knop wordt altijd weergegeven, maar mogelijk niet tot stand brengen van een extern bureaublad-sessiehost als de bewaakte computer wordt uitgevoerd Windows PE, installatie van het beoogde besturingssysteem niet is voltooid of beschikt niet over de functie Extern bureaublad is ingeschakeld.|  
    |**VM-verbinding** |Deze knop kunt u extern bureaublad verbinding te maken met een virtuele machine in Hyper-v wordt uitgevoerd. Deze methode wordt ervan uitgegaan dat:<br /><br /> -De implementatie wordt uitgevoerd op een virtuele machine waarop Hyper-V<br />-   **vmconnect.ex**e bevindt zich in de map %ProgramFiles%\Hyper-V **Opmerking:**  Deze knop wordt weergegeven wanneer ZTIGather.wsf detecteert dat de onderdelen voor Hyper-V-integratie worden uitgevoerd op de bewaakte computer. Anders wordt is deze knop alleen zichtbaar.|  
    |**DaRT extern beheer** |Deze knop kunt u tot stand brengen van een sessie voor extern beheer met de functie externe viewer in DaRT.<br /><br /> Deze methode wordt ervan uitgegaan dat:<br /><br /> -DaRT is geïmplementeerd op de doelcomputer en wordt momenteel uitgevoerd.<br />-   **DartRemoteViewer.exe** bevindt zich in de map %ProgramFiles%\Microsoft DaRT 7\v7 **Opmerking:**  Deze knop wordt weergegeven wanneer ZTIGather.wsf detecteert dat DaRT wordt uitgevoerd op de bewaakte computer. Anders wordt is deze knop alleen zichtbaar.|  
    |**Deze informatie om de tien seconden automatisch worden vernieuwd** |Selectievakje die bepaalt of de informatie in het dialoogvenster automatisch wordt vernieuwd. Als het selectievakje is:<br /><br /> -Geselecteerd, de gegevens worden vernieuwd elke 10 seconden<br />-Uitgeschakeld, de informatie is niet automatisch vernieuwd en moet handmatig vernieuwen met behulp van de **vernieuwen** nu knop|  
    |**Nu vernieuwen** |Deze knop wordt onmiddellijk vernieuwd voor de informatie die wordt weergegeven in het dialoogvenster.|  

8.  In de **WDG-REF-01-eigenschappen** in het dialoogvenster, klikt u op **OK**.  

9. Sluit de implementatie-Workbench.  

 **Voor het bewaken van het implementatieproces van de verwijzing naar computer met de cmdlet Get-MDTMonitorData**  

1.  Klik op WDG-MDT-01 **Start**, wijs **Systeembeheer**, en klik vervolgens op **Windows PowerShell-Modules**.  

     Hiermee opent u de opdrachtprompt van Windows PowerShell-Modules.  

2.  Maken van een Windows PowerShell-station dat gebruikmaakt van de MDT-PowerShell-provider door het uitvoeren van de [nieuw PSDrive](http://technet.microsoft.com/library/hh849829.aspx) cmdlet zoals weergegeven in het volgende voorbeeld:  

    ```  
    New-PSDrive -Name DS001 -PSProvider mdtprovider -Root d:\DeploymentShare$  
    ```  

3.  Weergeven van de MDT bewakingsproces door het uitvoeren van de **Get-MDTMonitorData** cmdlet, zoals weergegeven in het volgende voorbeeld:  

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

 Na het voltooien van het implementatieproces voor Windows 8.1 voor het eerst wordt gestart en de **Welkom** tabblad de **implementatie voltooid** in het dialoogvenster wordt weergegeven. De **Welkom** tabblad weergegeven van nuttige informatie over het installeren en contactgegevens bevat in het geval van problemen met de implementatie optreden.  

 Lees de informatie op de **implementatieoverzicht** en **toepassingen geïnstalleerd** tabbladen om te controleren of Windows 8.1-en Office Professional Plus 2010 correct zijn geïnstalleerd. Wanneer u klaar bent met het controleren van deze tabellen, klikt u op **Windows starten** Meld u aan bij Windows 8.1 voor de eerste keer.  

> [!NOTE]
>  Configuration Manager-toepassingen worden niet weergegeven op de **toepassingen geïnstalleerd** tabblad. In plaats daarvan worden ze nadat de gebruiker zich op de doelcomputer voor het eerst aanmeldt gedetecteerd.
