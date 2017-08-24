---
title: Vereiste controles | Microsoft Docs
description: Bekijk de beschikbare vereistencontroles voor System Center Configuration Manager. Bevat controles voor beveiligingsrechten.
ms.custom: na
ms.date: 4/17/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 6a279624-ffc9-41aa-8132-df1809708dd5
caps.latest.revision: "12"
author: Brenduns
ms.author: brenduns
manager: angrobe
ms.openlocfilehash: 14834f62ffaa8fcba5ddb7536a0b76e18b557e53
ms.sourcegitcommit: 51fc48fb023f1e8d995c6c4eacfda7dbec4d0b2f
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 08/07/2017
---
# <a name="list-of-prerequisite-checks-for-system-center-configuration-manager"></a>Lijst met vereistencontroles voor System Center Configuration Manager

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*

De volgende secties bevatten informatie over de beschikbare vereistencontroles.

Zie voor meer informatie over het gebruik van Prerequisite Checker [Prerequisite Checker](prerequisite-checker.md).  

##  <a name="BKMK_Security"></a>Controles op vereisten voor beveiligingsrechten  
De volgende tabel geeft een lijst met controles die Prerequisite Checker voor beveiligingsrechten uitvoert.

|Controle uitgevoerd|Uitleg|Ernst|Toepasbaarheid van de site|
|---|---|---|---|
|**Administrator-rechten op de centrale beheersite**|Controleert of het gebruikersaccount waarmee Setup van Configuration Manager wordt uitgevoerd heeft **beheerder** rechten op de computer van de centrale beheersite. |Fout|Primaire site|
|**Beheerrechten op de primaire site uitbreiden**|Controleert of de gebruikersaccount die de installatie uitvoert **beheerder** rechten op de zelfstandige primaire site die zal worden uitgebreid.|Fout|Centrale beheersite|
|**Beheerrechten op sitesysteem**|Controleert of het gebruikersaccount waarmee Setup van Configuration Manager wordt uitgevoerd heeft **beheerder** -rechten op de siteservercomputer. |Fout|Centrale beheersite <br>Primaire site <br>Secundaire site|
|**Beheerrechten van CAS-computer op de primaire site uitbreiden**|Controleert of het computeraccount van de centrale beheersite **beheerder** rechten op de zelfstandige primaire site die zal worden uitgebreid.|Fout|Centrale beheersite|
|**Verbinding met SQL Server op centrale beheersite**|Controleert of het gebruikersaccount dat Configuration Manager-installatie wordt uitgevoerd op de primaire site om een bestaande hiërarchie te nemen de **sysadmin** -rol op de SQL Server-exemplaar voor de centrale beheersite.|Fout|Primaire site|
|**Site server beheerrechten computeraccount**|Controleert of het computeraccount van de siteserver heeft **beheerder** -rechten op de SQL-server en computers verwijzen.|Fout|Primaire site <br>SQL Server|
|**SQL Server-communicatie tussen sitesysteem en**| Controleert of een geldige Service Principal Name (SPN) is geregistreerd in Active Directory Domain Services voor het account dat is geconfigureerd voor het uitvoeren van de SQL Server-service voor het SQL Server-exemplaar dat als host fungeert voor de Configuration Manager-sitedatabase. Er moet een geldige SPN zijn geregistreerd in Active Directory Domain Services om Kerberos-verificatie te kunnen ondersteunen.|Waarschuwing|Secundaire site <br>Beheerpunt|
|**Beveiligingsmodus SQL Server**|Controleert of SQL Server is geconfigureerd voor Windows-verificatiebeveiliging.|Waarschuwing|SQL Server|
|**SQL Server sysadmin-rechten**|Controleert of het gebruikersaccount waarmee Setup van Configuration Manager wordt uitgevoerd heeft de **sysadmin** -rol op de SQL Server-exemplaar dat is geselecteerd voor installatie van de sitedatabase. Deze controle mislukt ook wanneer het installatieprogramma geen toegang kan krijgen tot de instantie zodat de SQL Server machtigingen kan verifiëren.|Fout|SQL Server|
|**SQL Server sysadmin-rechten voor referentiesite**|Controleert of het gebruikersaccount waarmee Setup van Configuration Manager wordt uitgevoerd heeft de **sysadmin** rol op de instantie van SQL Server geselecteerd als de referentiesite-database. SQL Server **sysadmin** rolmachtigingen zijn vereist voor het wijzigen van de sitedatabase.|Fout|SQL Server|

##  <a name="BKMK_Dependencies"></a>Controles van vereisten voor Configuration Manager-afhankelijkheden
De volgende tabel geeft een lijst met controles die Prerequisite Checker voor Configuration Manager-afhankelijkheden uitvoert.

|Controle uitgevoerd|Uitleg|Ernst|Toepasbaarheid van de site|
|---|---|---|---|
|**Actieve migratietoewijzingen op de primaire doelsite**|Controleert of er geen actieve migratietoewijzingen naar primaire sites zijn.|Fout|Centrale beheersite|
|**Actief Replica-Beheerpunt**|Controleert op een actieve beheerpuntreplica.|Fout|Primaire site|
|**Beheerrechten op distributiepunt**|Controleert of het gebruikersaccount dat u Setup uitvoert **beheerder** rechten heeft op het distributiepunt.|Waarschuwing|Distributiepunt|
|**Beheerrechten op beheerpunt**|Controleert of het computeraccount van de siteserver heeft **beheerder** rechten heeft op het beheerpunt en distributiepunt.|Waarschuwing|Beheerpunt|
|**Beheershare (sitesysteem)**|Hiermee wordt gecontroleerd of de vereiste beheershares aanwezig op de sitesysteemcomputer zijn.|Waarschuwing|Beheerpunt|
|**Toepassingscompatibiliteit**|Controleert of de huidige toepassingen compatibel zijn met het toepassingsschema zijn.|Waarschuwing|Centrale beheersite <br>Primaire site|
|**BITS-functionaliteit**|Controleert of Background Intelligent Transfer Service (BITS) is geïnstalleerd op de site system de beheerpuntcomputer. Wanneer deze controle mislukt, BITS is niet geïnstalleerd, de compatibility-onderdeel van de Internet Information Services (IIS) 6.0 Windows Management Instrumentation (WMI) voor IIS 7.0 is niet geïnstalleerd op de computer of op de externe IIS-host of Setup kon geen externe IIS-instellingen niet controleren omdat IIS common componenten zijn niet geïnstalleerd op de siteservercomputer.|Fout|Beheerpunt|
|**BITS is geïnstalleerd**|Verifieert dat BITS is geïnstalleerd in IIS.|Waarschuwing|Beheerpunt|
|**Hoofdlettergevoelige collatie op SQL Server**|Controleert of de installatie van SQL Server gebruikmaakt van hoofdlettergevoelige collatie, zoals SQL_Latin1_General_CP1_CI_AS.|Fout|SQL Server|
|**Controle bestaande zelfstandige primaire site op versie en sitecode**|Controleert of de primaire site die u wilt uitbreiden een zelfstandige primaire site, en dat deze dezelfde versie van Configuration Manager, maar een andere sitecode heeft dan de centrale beheersite worden geïnstalleerd.|Fout|Centrale beheersite <br>Primaire site|
|**Controleren op niet-compatibele verzamelingsverwijzingen**|Tijdens een upgrade deze controle alleen gecontroleerd of verzamelingen verwijzen naar alleen andere verzamelingen van hetzelfde type.|Fout|Centrale beheersite|  
|**Clientversie op beheerpuntcomputer**|Controleert of u het beheerpunt installeert op een computer waarop geen andere versie van de Configuration Manager-client is geïnstalleerd.|Fout|Beheerpunt|
|**Configuratie voor geheugengebruik door SQL Server**|Controleert of SQL Server is geconfigureerd voor onbeperkt geheugengebruik. Configureer een maximumlimiet voor SQL Server-geheugen.|Waarschuwing|SQL Server|
|**Vast SQL Server-exemplaar**|Controleert of een toegewezen exemplaar van de SQL-server is geconfigureerd om de Configuration Manager-sitedatabase te hosten. Als de instantie door een andere site wordt gebruikt, moet u een andere instantie voor de nieuwe site selecteren. U kunt ook de andere site verwijderen of de database verplaatsen naar een ander exemplaar voor de SQL server.|Fout|Centrale beheersite <br>Primaire site <br>Secundaire site|
|**Bestaande Configuration Manager-serveronderdelen op server**|Controleert of dat een siteserver of sitesysteemrol niet is al geïnstalleerd op de computer die is geselecteerd voor de site-installatie.|Fout|Centrale beheersite <br>Primaire site <br>Secundaire site|
|**Firewall-uitzondering voor SQL Server**|Controleert of de Windows Firewall is uitgeschakeld of of een relevante Windows Firewall-uitzondering voor SQL Server bestaat. U moet toestaan Sqlservr.exe of de vereiste TCP-poorten extern toegankelijk is. Standaard luistert SQL Server op TCP-poort 1433 en SQL Server Service Broker (SSB) maakt gebruik van TCP-poort 4022.|Fout|Centrale beheersite <br>Primaire site <br>Secundaire site <br>Beheerpunt|
|**Firewall-uitzondering voor SQL Server (zelfstandige primaire site)**|Controleert of de Windows Firewall is uitgeschakeld of of een relevante Windows Firewall-uitzondering voor SQL Server bestaat. U moet toestaan Sqlservr.exe of de vereiste TCP-poorten extern toegankelijk is. Standaard luistert SQL Server op TCP-poort 1433 en de SSB TCP-poort 4022 gebruikt.|Waarschuwing|Primaire site (alleen zelfstandig)|
|**Firewall-uitzondering voor SQL Server voor beheerpunt**|Controleert of de Windows Firewall is uitgeschakeld of of een relevante Windows Firewall-uitzondering voor SQL Server bestaat.|Waarschuwing|Beheerpunt|
|**IIS HTTPS-configuratie**|Controleert of de IIS-websitebindingen voor het HTTPS-communicatieprotocol. Wanneer u site-functies die HTTPS vereisen installeert, moet u IIS sitebindingen configureren op de gespecificeerde server met een geldige openbare-sleutelinfrastructuur (PKI)-certificaat.|Waarschuwing|-Beheerpunt <br>Distributiepunt|
|**IIS-service wordt uitgevoerd**|Controleert of dat IIS is geïnstalleerd en actief op de computer voor het installeren van het beheerpunt of distributiepunt.|Fout|-Beheerpunt <br> Distributiepunt|
|**Sortering vergelijken van uit te breiden primaire site**|Hiermee wordt gecontroleerd of de sitedatabase voor de zelfstandige primaire site die u uitbreiden wilt, dezelfde collatie heeft als de sitedatabase op de centrale beheersite.|Fout|Centrale beheersite|
|**Microsoft Remote Differential Compression (RDC)-bibliotheek geregistreerd**|Controleert of de RDC-bibliotheek is geregistreerd op de siteserver van Configuration Manager.|Fout|Centrale beheersite <br>Primaire site <br>Secundaire site|
|**Microsoft Windows Installer**|Controleert of de versie van Windows Installer. Wanneer deze controle mislukt, is niet de versie te controleren of de geïnstalleerde versie voldoet niet aan de minimumvereisten van Windows Installer 4.5.|Fout|Centrale beheersite <br>Primaire site <br>Secundaire site|
|**Microsoft XML Core Services 6.0 (MSXML60)**|Controleert of MSXML 6.0 of hoger is geïnstalleerd op de computer.|Waarschuwing|Centrale beheersite <br>Primaire site <br>Secundaire site <br>Configuration Manager-console <br>-Beheerpunt <br>Distributiepunt|
|**Minimum .NET Framework-versie voor Configuration Manager-console**|Controleert of Microsoft .NET Framework 4.0 is geïnstalleerd op de consolecomputer Configuration Manager. U kunt .NET Framework 4.0 vanaf downloaden [Microsoft Download Center](http://go.microsoft.com/fwlink/p/?LinkId=189149).|Fout|Configuration Manager-console|
|**Minimum .NET Framework-versie voor Configuration Manager-siteserver**|Controleert of .NET Framework 3.5 is geïnstalleerd op de siteserver van Configuration Manager. U kunt Microsoft .NET Framework 3.5 uit downloaden voor Windows Server 2008 [Microsoft Download Center](http://go.microsoft.com/fwlink/p/?LinkId=185604). Voor Windows Server 2008 R2 kunt u .NET Framework 3.5 inschakelen als functie binnen Server Manager.|Fout|Centrale beheersite <br>Primaire site <br>Secundaire site|
|**Minimum .NET Framework-versie voor SQL Server Express edition installatie voor secundaire Configuration Manager-site**|Controleert of .NET Framework 4.0 is geïnstalleerd op Configuration Manager secundaire sitecomputers voor het installeren van SQL Server Express.|Fout|Secundaire site|
|**Collatie bovenliggende/onderliggende database**|Hiermee wordt gecontroleerd of de sortering van de sitedatabase overeenkomt met de sortering van de database van de bovenliggende site. Alle sites binnen een hiërarchie moeten dezelfde databasecollatie gebruiken.|Fout|Primaire site <br>Secundaire site|
|**PowerShell 2.0 op siteserver**|Controleert of Windows PowerShell 2.0 of hoger is geïnstalleerd op de siteserver voor de Configuration Manager Exchange Connector. Voor meer informatie over PowerShell 2.0, zie [Artikel 968930](http://go.microsoft.com/fwlink/p/?LinkId=226450) in de Microsoft Knowledge Base.|Waarschuwing|Primaire site|
|**Primaire FQDN**|Met behulp van een volledig gekwalificeerde domeinnaam (FQDN), wordt gecontroleerd of de NetBIOS-naam van de computer overeenkomt met de lokale hostnaam (eerste label van de FQDN) van de computer.|Fout|Centrale beheersite <br>Primaire site <br>Secundaire site <br>SQL Server|
|**Externe verbinding naar WMI op secundaire Site**|Controleert of het installatieprogramma tot stand brengen van een externe verbinding naar WMI op de secundaire siteserver.|Waarschuwing|Secundaire site|
|**Vereist SQL Server-sortering**|Controleert of dat het exemplaar van SQL Server en de Configuration Manager-sitedatabase, indien geïnstalleerd, is geconfigureerd voor het gebruik van de collatie SQL_Latin1_General_CP1_CI_AS, tenzij u een Chinees besturingssysteem gebruikt en behoefte hebt aan GB18030-ondersteuning.<br><br>Zie voor meer informatie over het wijzigen van uw SQL Server-instantie en databasecollaties [instelling en het wijzigen van sorteringen](http://go.microsoft.com/fwlink/p/?LinkID=234541) in de SQL Server 2008 R2 Books Online.  Zie [Internationale ondersteuning in System Center Configuration Manager](../../../../core/plan-design/hierarchy/international-support.md) voor meer informatie over het inschakelen van GB18030-ondersteuning.|Fout|Centrale beheersite <br>Primaire site <br>Secundaire site|
|**Setup-bronmap**|Controleert of het computeraccount voor de secundaire site **lezen** NTFS-bestandssysteemmachtigingen en **lezen** machtigingen voor de Setup-bronmap en share voor delen.<br><br>**OPMERKING**: Het computeraccount van de secundaire site moet een **beheerder** gebruiker op de computer als u beheershares (bijvoorbeeld C$ en D$).|Fout|Secundaire site|
|**Bronversie installatieprogramma**|Hiermee wordt gecontroleerd of de Configuration Manager-versie in de bronmap die u hebt opgegeven voor de secundaire site-installatie, overeenkomt met de Configuration Manager-versie van de primaire site.|Fout|Secundaire site|
|**Sitecode in gebruik**|Controleert of de sitecode die u hebt opgegeven niet al in gebruik is in de Configuration Manager-hiërarchie. U moet een unieke sitecode voor deze website opgeven.|Fout|Primaire site|
|**Computer van de SMS-Provider heeft hetzelfde domein als de siteserver**|Controleert of een computer met een exemplaar van de SMS-Provider hetzelfde domein als de siteserver heeft.|Fout|SMS-provider|
|**SQL Server-editie**|Controleert of de editie van SQL Server op de site niet SQL Server Express.|Fout|SQL Server|
|**SQL Server Express op secundaire Site**|Controleert of SQL Server Express kan worden geïnstalleerd op de siteservercomputer voor een secundaire site.|Fout|Secundaire site|
|**SQL Server op de secundaire Sitecomputer**|Controleert of SQL Server is geïnstalleerd op de secundaire sitecomputer. U kunt SQL Server niet installeren op een extern sitesysteem.<br><br>**WAARSCHUWING**: Deze controle is enkel van toepassing wanneer u selecteert dat Setup een bestaande instantie van SQL Server gebruikt.|Fout|Secundaire site|
|**Geheugentoewijzing SQL Server-proces**|Verifieert dat SQL Server minimaal 8 GB geheugen voor de centrale beheersite en primaire site en een minimum van 4 GB geheugen voor de secundaire site van bewaart. Zie voor meer informatie over het instellen van een vaste hoeveelheid geheugen met behulp van SQL Server Management Studio [het instellen van een vaste hoeveelheid geheugen (SQL Server Management Studio)](http://go.microsoft.com/fwlink/p/?LinkId=233759).<br><br>**OPMERKING**: Deze controle is niet van toepassing op de SQL Server Express op een secundaire site, beperkt tot 1 GB gereserveerd geheugen is.|Waarschuwing|SQL Server|
|**Account voor uitvoering van SQL Server-service**|Controleert of het aanmeldingsaccount voor de SQL Server-service is niet een lokale gebruikersaccount of LOCAL SERVICE. U moet de SQL Server-service configureren om een geldig domeinaccount, NETWORK SERVICE of LOCAL SYSTEM te gebruiken.|Fout|Centrale beheersite <br>Primaire site <br>Secundaire site|
|**SQL Server-TCP-poort**|Controleert of TCP is ingeschakeld voor de SQL Server-exemplaar en is ingesteld voor gebruik van een statische poort.|Fout|SQL Server|
|**SQL Server-versie**|Controleert of een ondersteunde versie van SQL Server is geïnstalleerd op de databaseserver van de opgegeven site. Zie voor meer informatie [ondersteuning voor SQL Server-versies voor System Center Configuration Manager](../../../../core/plan-design/configs/support-for-sql-server-versions.md).|Fout|SQL Server|
|**Site met niet-ondersteunde besturingssysteemversie voor upgrade**|Tijdens een upgrade wordt in deze regel controleert of de sitesysteemrollen, met uitzondering van distributiepunten, zijn geïnstalleerd op computers met Windows Server 2008 of eerdere versies.<br><br>**OPMERKING**: Omdat deze controle de status van de sitesysteemrollen die zijn geïnstalleerd in Azure of voor de cloudopslag die door Microsoft Intune gebruikt wanneer u Intune met Configuration Manager integreert kan niet worden omgezet, kunt u waarschuwingen voor deze rollen als fout-positieven negeren.|Waarschuwing|Primaire site <br>Secundaire site|
|**Niet-ondersteunde sitesysteemrol 'Asset Intelligence-synchronisatiepunt' op de uitgebreide primaire site**|Controleert de Asset Intelligence-synchronisatie sitesysteemrol is niet geïnstalleerd op de zelfstandige primaire site die u uitbreidt.|Fout|Centrale beheersite|
|**Niet-ondersteunde sitesysteemrol 'Endpoint Protection-punt' op de uitgebreide primaire site**|Controleert of de sitesysteemrol Endpoint Protection niet is geïnstalleerd op de zelfstandige primaire site die u uitbreidt.|Fout|Centrale beheersite|
|**Niet-ondersteunde sitesysteemrol 'Microsoft Intune-Connector' op de uitgebreide primaire site**|Controleert of de sitesysteemrol Microsoft Intune-Connector niet is geïnstalleerd op de zelfstandige primaire site die u uitbreidt.|Fout|Centrale beheersite|
|**User State Migration Tool (USMT) is geïnstalleerd**|Controleert of het onderdeel User State Migration Tool (USMT) van Windows Assessment and Deployment Kit (ADK) voor Windows 8.1 is geïnstalleerd.|Fout|Centrale beheersite <br>Primaire site (alleen zelfstandig)|  
|**FQDN van SQL Server-Computer valideren**|Controleert of de FQDN-naam die u hebt opgegeven voor de SQL Server-computer geldig is.|Fout|SQL Server|
|**Controleer of de versie van de centrale beheersite**|Controleert of de centrale beheersite dezelfde versie van Configuration Manager.|Fout|Primaire site|
|**Siteservermachtigingen voor publiceren in Active Directory controleren**|Controleert of het computeraccount voor de siteserver heeft **volledig beheer** machtigingen voor de **System Management** container in Active Directory-domein. Zie voor meer informatie over uw opties voor het configureren van de vereiste machtigingen, [Active Directory voorbereiden voor het publiceren van site](../../../../core/plan-design/network/extend-the-active-directory-schema.md).<br><br>**OPMERKING**: U kunt deze waarschuwing negeren indien u handmatig de machtigingen hebt geverifieerd.|Waarschuwing|Centrale beheersite <br>Primaire site <br>Secundaire site|
|**Windows-hulpprogramma's geïnstalleerd**|Controleert of het onderdeel Windows-hulpprogramma's van Windows ADK voor Windows 10 is geïnstalleerd.|Fout|SMS-provider|
|**Windows-failovercluster**|Controleert of computers waarvoor een beheerpunt of distributiepunt niet deel uit van een Windows-Cluster.|Fout|Beheerpunt<br>Distributiepunt|
|**Windows voorinstallatieomgeving geïnstalleerd**|Controleert of het onderdeel Windows Preinstallation Environment van Windows ADK voor Windows 10 is geïnstalleerd.|Fout|SMS-provider|
|**Windows Remote Management (WinRM) v1.1**|Verifieert of WinRM 1.1 is geïnstalleerd op de primaire siteserver of de consolecomputer Configuration Manager om uit te voeren van de out-of-band-beheerconsole. Zie [Artikel 936059](https://support.microsoft.com/en-us/kb/936059) in de Microsoft Knowledge Base voor meer informatie over het downloaden van WinRM 1.1.|Waarschuwing|Primaire site <br>Configuration Manager-console|
|**WSUS op siteserver**|Controleert of Windows Server Update Services (WSUS) 3.0 servicepack 2 (SP2) is geïnstalleerd op de siteserver. Wanneer u een software-updatepunt op een computer die niet de siteserver gebruikt, moet u de WSUS-beheerconsole installeren op de siteserver. Zie voor meer informatie over WSUS [Windows Server Update Services](http://go.microsoft.com/fwlink/p/?LinkID=79477).|Waarschuwing|Centrale beheersite <br>Primaire site|  

##  <a name="BKMK_Requirements"></a>Controles op vereisten voor de systeemvereisten  
De volgende tabel geeft een lijst met controles die Prerequisite Checker voor systeemvereisten uitvoert.  

|Controle uitgevoerd|Uitleg|Ernst|Toepasbaarheid van de site|
|---|---|---|---|
|**Active Directory-domein controle op functioneel niveau**|Controleert of het functionele niveau van het Active Directory-domein minimaal Windows Server 2008 R2.|Waarschuwing|Centrale beheersite <br>Primaire site|
|**Controleren of de dat Server-Service wordt uitgevoerd**|Hiermee wordt gecontroleerd of de Server-Service is gestart.|Fout|Centrale beheersite <br>Primaire site <br>Secundaire site|  
|**Lidmaatschap van een domein**|Controleert of de Configuration Manager-computer lid is van een Windows-domein.|Fout|Centrale beheersite <br>Primaire site <br>Secundaire site <br>SMS-Provider <br>SQL Server|
|**Lidmaatschap van een domein**|Controleert of de Configuration Manager-computer lid is van een Windows-domein.|Waarschuwing|-Beheerpunt <br>Distributiepunt|
|**FAT-station op siteserver**|Controleert of het station is geformatteerd met FAT-bestandssysteem. Voor een betere beveiliging siteservercomponenten installeren op stations die zijn geformatteerd met het NTFS-bestandssysteem.|Waarschuwing|Primaire site|
|**Vrije schijfruimte op siteserver**|De siteservercomputer moet ten minste 15 GB vrije schijfruimte hebben voor het installeren van de siteserver. U moet een bijkomende 1 GB vrije ruimte hebben indien u de sitesysteemrol van de SMS-provider installeert op dezelfde computer.|Fout|Centrale beheersite <br>Primaire site <br>Secundaire site|
|**Opstarten in behandeling**|Controleert of een ander programma vereist dat de server opnieuw worden opgestart voordat u Setup uitvoert.|Fout|Centrale beheersite <br>Primaire site <br>Secundaire site <br>Configuration Manager-console <br>SMS-Provider <br>SQL Server. <br>-Beheerpunt <br>Distributiepunt|
|**Alleen-lezen domeincontroller**|Sitedatabaseservers en secundaire siteservers worden niet ondersteund op een alleen-lezen domeincontroller (RODC). Zie voor meer informatie [problemen bij het installeren van SQL Server op een domeincontroller](http://go.microsoft.com/fwlink/p/?LinkId=264856) in de Microsoft Knowledge Base.|Fout|Centrale beheersite <br>Primaire site <br>Secundaire site|
|**Schema-uitbreidingen**|Bepaalt of de Active Directory Domain Services-schema is uitgebreid, en zo ja, de versie van de schema-uitbreidingen die zijn gebruikt. Configuration Manager Active Directory-schema-uitbreidingen zijn niet vereist voor siteserverinstallatie, maar we raden deze volledig gebruik van alle Configuration Manager-functies. Zie voor meer informatie over de voordelen van het schema uitbreidt, [Active Directory voorbereiden voor het publiceren van site](../../../../core/plan-design/network/extend-the-active-directory-schema.md).|Waarschuwing|Centrale beheersite <br>Primaire site|
|**Lengte van de siteserver-FQDN**|Controleert de lengte van de FQDN van de siteservercomputer.|Fout|Centrale beheersite <br>Primaire site <br>Secundaire site|
|**Niet-ondersteund besturingssysteem voor Configuration Manager-console**|Verifieert dat de Configuration Manager-console kan worden geïnstalleerd op computers waarop een ondersteund besturingssysteemversie wordt uitgevoerd. Zie voor meer informatie de [ondersteunde besturingssystemen voor de System Center Configuration Manager-console](/sccm/core/plan-design/configs/supported-operating-systems-consoles).|Fout|Configuration Manager-console|
|**Versie van besturingssysteem niet-ondersteunde siteserver voor installatie**|Hiermee wordt gecontroleerd of een ondersteund besturingssysteem wordt uitgevoerd op de server. Zie voor meer informatie [ondersteunde besturingssystemen voor System Center Configuration Manager-sitesysteemservers](/sccm/core/plan-design/configs/supported-operating-systems-for-site-system-servers.md).|Fout|Centrale beheersite <br>Primaire site <br>Secundaire site <br>Configuration Manager-console <br>-Beheerpunt <br>Distributiepunt|
|**Databaseconsistentie controleren**|Vanaf versie 1602 controleert consistentie van de database.|Fout|Centrale beheersite <br>Primaire site|  
