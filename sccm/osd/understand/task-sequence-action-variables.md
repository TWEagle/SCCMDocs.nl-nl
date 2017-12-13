---
title: Variabelen voor de takenreeksactie
titleSuffix: Configuration Manager
description: "Variabelen, zoals netwerk instelling variabelen, gebruiken om op te geven van configuratie-instellingen voor één stap in een takenreeks van Configuration Manager."
ms.custom: na
ms.date: 10/06/2016
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: configmgr-osd
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: e2269031-0977-4f01-a274-420e00630575
caps.latest.revision: "10"
caps.handback.revision: "0"
author: aczechowski
ms.author: aaroncz
manager: angrobe
ms.openlocfilehash: da1a9b9d73a06a099b71e59cbf3621791eaed527
ms.sourcegitcommit: 08f9854fb6c6d21e1e923b13e38a64d0bc2bc9a4
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/12/2017
---
# <a name="task-sequence-action-variables-in-system-center-configuration-manager"></a>Takenreeksacties in System Center Configuration Manager

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*

Takenreeksacties geven configuratie-instellingen die worden gebruikt door één stap in een takenreeks van System Center Configuration Manager. Standaard worden de instellingen van een takenreeksstap geïnitialiseerd voordat de stap wordt uitgevoerd en zijn deze alleen beschikbaar tijdens het uitvoeren van de gekoppelde takenreeksstap. Met andere woorden: de instelling voor de takenreeksvariabele wordt toegevoegd aan de takenreeksomgeving vóór de takenreeksstap wordt uitgevoerd, en de waarde wordt verwijderd uit de takenreeksomgeving na het uitvoeren van de takenreeksstap.  

## <a name="action-variable-example"></a>Voorbeeld actievariabele  
 U kunt bijvoorbeeld een startmap voor een opdrachtregelactie opgeven met behulp van de takenreeksstap **Opdrachtregel uitvoeren** . Deze stap omvat de eigenschap **Beginnen in** waarvan de standaardwaarde is opgeslagen in de takenreeksomgeving als de variabele **WorkingDirectory** . De omgevingsvariabele **WorkingDirectory** wordt geïnitialiseerd voordat de takenreeksactie **Opdrachtregel uitvoeren** wordt uitgevoerd. Tijdens de stap **Opdrachtregel uitvoeren** is de waarde van **WorkingDirectory** toegankelijk via de eigenschap **Beginnen in** . Wanneer de takenreeksstap is voltooid, wordt de waarde van de variabele **WorkingDirectory** verwijderd uit de takenreeksomgeving. Als de reeks een ander exemplaar van de takenreeksstap **Opdrachtregel uitvoeren** bevat, wordt de nieuwe variabele **WorkingDirectory** geïnitialiseerd en ingesteld op de beginwaarde voor deze takenreeksstap.  

 Terwijl de standaardwaarde voor de instelling van een takenreeksactie aanwezig is tijdens de uitvoering van de takenreeksstap, kan elke nieuwe waarde die u instelt worden gebruikt door meerdere stappen in de reeks. Als u een van de aanmaakmethoden voor de takenreeksvariabele gebruikt om de waarde van een ingebouwde variabele te onderdrukken, wordt de nieuwe waarde gehandhaafd in de omgeving en vervangt deze de standaardwaarde voor de overige stappen in de takenreeks. In het vorige voorbeeld als een **Takenreeksvariabele instellen** stap wordt toegevoegd als de eerste stap van de takenreeks en wordt de **WorkingDirectory** omgevingsvariabele aan de waarde **C:\\**, beide **opdrachtregel uitvoeren** stappen in de takenreeks wordt de nieuwe waarde voor de beginmap gebruikt.  

## <a name="action-variables-for-task-sequence-actions"></a>Variabelen voor takenreeksacties  
 Configuration Manager-takenreeksvariabelen zijn gegroepeerd op hun bijbehorende takenreeksactie. Gebruik de volgende koppelingen voor het verzamelen van informatie over de variabelen die zijn gekoppeld aan een specifieke actie. De takenreeksvariabelen bepalen hoe de takenreeksactie werkt. De variabelen die u als invoervariabelen markeert, worden door de takenreeksactie gelezen en gebruikt. U kunt ook de actie voor het instellen van een takenreeksvariabele of het TSEnvironment COM-object gebruiken om de variabelen tijdens runtime in te stellen. Alleen de takenreeksactie markeert variabelen als uitvoervariabelen, die worden gelezen door acties die later in de takenreeks worden uitgevoerd.  

> [!NOTE]  
>  Niet alle takenreeksacties zijn gekoppeld aan een set takenreeksvariabelen. Bijvoorbeeld: hoewel er variabelen zijn gekoppeld aan de actie BitLocker inschakelen, zijn er geen variabelen gekoppeld aan de actie BitLocker uitschakelen.  

###  <a name="BKMK_ApplyDataImage"></a> Variabelen voor de takenreeksactie Gegevensinstallatiekopie toepassen  
 De variabelen voor deze actie geven op welke installatiekopie van een WIM-bestand wordt toegepast op de doelcomputer en of de bestanden op de doelpartitie worden verwijderd. Zie voor meer informatie over de takenreeksstap die aan deze variabelen is gekoppeld, [toepassen gegevens Takenreeksstap gegevensinstallatiekopie](task-sequence-steps.md#BKMK_ApplyDataImage).  

#### <a name="details"></a>Details  

|Naam actievariabele|Beschrijving|  
|--------------------------|-----------------|  
|OSDDataImageIndex<br /><br /> (invoer)|Hiermee geeft u de indexwaarde op van de installatiekopie die wordt toegepast op de doelcomputer.|  
|OSDWipeDestinationPartition<br /><br /> (invoer)|Hiermee geeft u op of de bestanden op de doelpartitie worden verwijderd.<br /><br /> Geldige waarden:<br /><br /> '**true** ' (standaard)<br /><br /> '**false**'|  

###  <a name="BKMK_ApplyDriverPackage"></a> Variabelen voor de takenreeksactie Stuurprogrammapakket toepassen  
 De variabelen voor deze actie geven informatie op over de installatie van stuurprogramma's voor massaopslag en bepalen of niet-ondertekende stuurprogramma's worden geïnstalleerd. Zie voor meer informatie over de takenreeksstap die aan deze variabelen is gekoppeld, [stuurprogrammapakket toepassen](task-sequence-steps.md#BKMK_ApplyDriverPackage).  

#### <a name="details"></a>Details  

|Naam actievariabele|Beschrijving|  
|--------------------------|-----------------|  
|OSDApplyDriverBootCriticalContentUniqueID<br /><br /> (invoer)|Hiermee geeft u de inhoud-id op van het te installeren stuurprogramma voor massaopslagapparaten uit het stuurprogrammapakket. Als dit niet is opgegeven, wordt er geen stuurprogramma voor massaopslag geïnstalleerd.|  
|OSDApplyDriverBootCriticalINFFile<br /><br /> (invoer)|Hiermee geeft u het INF-bestand op van het te installeren stuurprogramma voor massaopslag.<br /><br /> <br /><br /> Deze takenreeksvariabele is vereist als OSDApplyDriverBootCriticalContentUniqueID is ingesteld.|  
|OSDApplyDriverBootCriticalHardwareComponent<br /><br /> (invoer)|Hiermee geeft u op of een stuurprogramma voor massaopslagapparaten wordt geïnstalleerd, moet dit **scsi**.<br /><br /> <br /><br /> Deze takenreeksvariabele is vereist als OSDApplyDriverBootCriticalContentUniqueID is ingesteld.|  
|OSDApplyDriverBootCriticalID<br /><br /> (invoer)|Hiermee geeft u de essentiële opstart-id op van het te installeren stuurprogramma voor massaopslagapparaten. Deze ID wordt weergegeven de '**scsi**' sectie van het apparaatstuurprogramma txtsetup.oem-bestand.<br /><br /> <br /><br /> Deze takenreeksvariabele is vereist als OSDApplyDriverBootCriticalContentUniqueID is ingesteld.|  
|OSDAllowUnsignedDriver<br /><br /> (invoer)|Hiermee kunt u configureren of Windows de installatie van niet-ondertekende apparaatstuurprogramma's toestaat. Deze takenreeksvariabele wordt niet gebruikt bij het implementeren van het besturingssysteem Windows Vista of hoger.<br /><br /> Geldige waarden:<br /><br /> **true**<br /><br /> '**false** ' (standaard)|  

###  <a name="BKMK_ApplyNetworkSettings"></a> Variabelen voor de takenreeksactie Netwerkinstellingen toepassen  
 De variabelen voor deze actie geven netwerkinstellingen voor de doelcomputer op, zoals instellingen voor de netwerkadapters van de computer, domeininstellingen en werkgroepinstellingen. Zie voor meer informatie over de takenreeksstap die aan deze variabelen is gekoppeld, [stap netwerkinstellingen toepassen](task-sequence-steps.md#BKMK_ApplyNetworkSettings).  

#### <a name="details"></a>Details  

|Naam actievariabele|Beschrijving|  
|--------------------------|-----------------|  
|OSDAdapter<br /><br /> (invoer)|Deze takenreeksvariabele is een matrixvariabele. Elk element in de matrix staat voor de instellingen voor één netwerkadapter op de computer. De instellingen die zijn gedefinieerd voor elke adapter zijn toegankelijk door de naam van de matrixvariabele te combineren met de netwerkadapterindex (op basis van nul) en de naam van de eigenschap.<br /><br /> <br /><br /> Als meerdere netwerkadapters worden geconfigureerd met deze takenreeksactie, worden de eigenschappen voor de tweede netwerkadapter gedefinieerd met behulp van de index in de naam van de variabele; bijvoorbeeld, OSDAdapter1EnableDHCP, OSDAdapter1IPAddressList, OSDAdapter1DNSDomain, OSDAdapter1WINSServerList, OSDAdapter1EnableWINS, enzovoort.<br /><br /> <br /><br /> De namen van de volgende variabelen kunnen bijvoorbeeld worden gebruikt voor het definiëren van de eigenschappen voor de eerste netwerkadapter die door deze takenreeksactie wordt geconfigureerd:<br /><br /> <ul><li>**OSDAdapter0EnableDHCP** - wilt inschakelen, Dynamic Host Configuration Protocol (DHCP) voor de adapter.<br />    Deze instelling is vereist. Mogelijke waarden zijn:  Waar of ONWAAR.</li><li>**OSDAdapter0IPAddressList** -door komma's gescheiden lijst met IP-adressen voor de adapter. Deze eigenschap wordt genegeerd, tenzij **EnableDHCP** is ingesteld op **false**.<br />    Deze instelling is vereist.</li><li>**OSDAdapter0SubnetMask** -bestand met door komma's gescheiden lijst met subnetmaskers. Deze eigenschap wordt genegeerd, tenzij **EnableDHCP** is ingesteld op **false**.<br />    Deze instelling is vereist.</li><li>**OSDAdapter0Gateways** -bestand met door komma's gescheiden lijst met IP-gatewayadressen. Deze eigenschap wordt genegeerd, tenzij **EnableDHCP** is ingesteld op **false**.<br />    Deze instelling is vereist.</li><li>**OSDAdapter0DNSDomain** – DNS-domein (Domain Name System) voor de adapter.</li><li>**OSDAdapter0DNSServerList** -door komma's gescheiden lijst met DNS-servers voor de adapter.<br />    Deze instelling is vereist.</li><li>**OSDAdapter0EnableDNSRegistration** - **true** naar het IP-adres voor de adapter in DNS registreren.</li><li>**OSDAdapter0EnableFullDNSRegistration** - **true** naar het IP-adres voor de adapter in DNS registreren onder de volledige DNS-naam voor de computer.</li><li>**OSDAdapter0EnableIPProtocolFiltering** - **true** om in te schakelen van IP-protocolfiltering op de adapter.</li><li>**OSDAdapter0IPProtocolFilterList** -bestand met door komma's gescheiden lijst met protocollen mag worden uitgevoerd via IP. Deze eigenschap wordt genegeerd als **EnableIPProtocolFiltering** is ingesteld op **false**.</li><li>**OSDAdapter0EnableTCPFiltering** - **true** om in te schakelen voor de adapter voor het filteren van TCP-poort.</li><li>**OSDAdapter0TCPFilterPortList** -door komma's gescheiden lijst met poorten waaraan toegangsmachtigingen voor TCP worden toegekend. Deze eigenschap wordt genegeerd als **EnableTCPFiltering** is ingesteld op **false**.</li><li>**OSDAdapter0TcpipNetbiosOptions** -opties voor NetBIOS via TCP/IP. Mogelijke waarden zijn als volgt:<br /><br /> <ul><li>0 NetBIOS-instellingen van DHCP-server gebruiken.</li><li>1 NetBIOS inschakelen via TCP/IP.</li><li>2 NetBIOS uitschakelen via TCP/IP.</li></ul></li><li>**OSDAdapter0EnableWINS** - **true** WINS te gebruiken voor naamomzetting.</li><li>**OSDAdapter0WINSServerList** -door komma's gescheiden lijst met IP-adressen van WINS-server. Deze eigenschap wordt genegeerd, tenzij **EnableWINS** is ingesteld op **true**.</li><li>**OSDAdapter0MacAddress** -Media access controller (MAC)-adres gebruikt om instellingen op fysieke netwerkadapter.</li><li>**OSDAdapter0Name** - naam van de netwerkverbinding zoals deze wordt weergegeven in het netwerk verbindingen besturingsprogramma Configuratiescherm. De naam kan tussen 0 en 255 tekens lang zijn.</li><li>**OSDAdapter0Index** -Index van de instellingen van de netwerkadapter in de matrix van instellingen.<br /><br />     OSDAdapterCount = 1<br />    OSDAdapter0EnableDHCP = FALSE<br />    OSDAdapter0IPAddressList 192.168.0.40 =<br />    OSDAdapter0SubnetMask 255.255.255.0 =<br />    OSDAdapter0Gateways 192.168.0.1 =<br />    OSDAdapter0DNSSuffix=contoso.com</li></ul>|  
|OSDAdapterCount<br /><br /> (invoer)|Hiermee geeft u het aantal netwerkadapters op dat op de doelcomputer is geïnstalleerd. Wanneer de waarde  van **OSDAdapterCount** is ingesteld, moeten alle configuratieopties voor elke adapter worden ingesteld. Als u bijvoorbeeld de waarde van **OSDAdapterTCPIPNetbiosOptions** instelt voor een specifieke adapter, moeten alle waarden voor die adapter ook worden geconfigureerd.<br /><br /> <br /><br /> Als deze waarde niet is opgegeven, worden alle waarden van **OSDAdapter** genegeerd.|  
|OSDDNSDomain<br /><br /> (invoer)|Hiermee geeft u de primaire DNS-server op die wordt gebruikt door de doelcomputer.|  
|OSDDomainName<br /><br /> (invoer)|Hiermee geeft u de naam op van het Windows-domein waarvan de doelcomputer lid wordt. De opgegeven waarde moet een geldige domeinnaam van Active Directory Domain Services zijn.|  
|OSDDomainOUName<br /><br /> (invoer)|Hiermee geeft u de naam in RFC 1779-indeling op van de organisatie-eenheid (OE) waarvan de doelcomputer lid wordt. Als u deze optie opgeeft, moet de waarde het volledige pad bevatten.<br /><br /> Voorbeeld:<br /><br /> **LDAP://OU=MyOu,DC=MyDom,DC=MyCompany,DC=com**|  
|OSDEnableTCPIPFiltering<br /><br /> (invoer)|Hiermee geeft u aan of TCP/IP-filtering is ingeschakeld.<br /><br /> Geldige waarden:<br /><br /> **true**<br /><br /> '**false** ' (standaard)|  
|OSDJoinAccount<br /><br /> (invoer)|Hiermee geeft u het netwerkaccount op dat wordt gebruikt voor het toevoegen van de doelcomputer aan een Windows-domein.|  
|OSDJoinPassword<br /><br /> (invoer)|Hiermee geeft u het netwerkwachtwoord op dat wordt gebruikt voor het toevoegen van de doelcomputer aan een Windows-domein.|  
|OSDNetworkJoinType<br /><br /> (invoer)|Hiermee geeft u aan of de doelcomputer lid wordt van een Windows-domein of een werkgroep.<br /><br /> **0** geeft aan dat de doelcomputer lid wordt van een Windows-domein. **1** geeft aan dat de computer lid wordt van een werkgroep.<br /><br /> Geldige waarden:<br /><br /> **0**<br /><br /> **1**|  
|OSDDNSSuffixSearchOrder<br /><br /> (invoer)|Hiermee geeft u de DNS-zoekvolgorde op voor de doelcomputer.|  
|OSDWorkgroupName<br /><br /> (invoer)|Hiermee geeft u de naam op van de werkgroep waarvan de doelcomputer lid wordt.<br /><br /> U moet deze waarde of de waarde van **OSDDomainName** opgeven. De werkgroepnaam mag maximaal 32 tekens lang zijn.<br /><br /> Voorbeeld:<br /><br /> **"Accounting"**|  

###  <a name="BKMK_ApplyOperatingSystem"></a> Variabelen voor de takenreeksactie Besturingssysteeminstallatiekopie toepassen  
 De variabelen voor deze actie geven instellingen op voor het besturingssysteem dat u wilt installeren op de doelcomputer. Zie voor meer informatie over de takenreeksstap die aan deze variabelen is gekoppeld, [Besturingssysteeminstallatiekopie toepassen](task-sequence-steps.md#BKMK_ApplyOperatingSystemImage).  

#### <a name="details"></a>Details  

|Naam actievariabele|Beschrijving|  
|--------------------------|-----------------|  
|OSDConfigFileName<br /><br /> (invoer)|Hiermee geeft u de bestandsnaam van het antwoordbestand voor besturingssysteemimplementatie op dat is gekoppeld aan het implementatiepakket voor het besturingssysteem.|  
|OSDImageIndex<br /><br /> (invoer)|Hiermee geeft u de indexwaarde van de installatiekopie op uit het WIM-bestand dat wordt toegepast op de doelcomputer.|  
|OSDInstallEditionIndex<br /><br /> (invoer)|Hiermee geeft u de versie op van het besturingssysteem Windows Vista of hoger dat wordt geïnstalleerd. Als er geen versie is opgegeven, bepaalt Windows Setup welke versie wordt geïnstalleerd aan de hand van de productcode.<br /><br /> Gebruik alleen de waarde nul (0) als aan de volgende voorwaarden wordt voldaan:<br /><br /> -U installeert een ouder dan Windows Vista-besturingssysteem<br />-U installeert een volumelicentie-editie van Windows Vista of hoger en er geen productcode is opgegeven.<br /><br /> Geldige waarden:<br /><br /> **"0"** (standaard)|  
|OSDTargetSystemDrive (uitvoer)|Hiermee geeft u de stationsletter op van de partitie die de besturingssysteembestanden bevat.|  

###  <a name="BKMK_ApplyWindowsSettings"></a> Variabelen voor de takenreeksactie Windows-instellingen toepassen  
 De variabelen voor deze actie worden gegeven Windows-instellingen voor de doelcomputer op, zoals de computernaam, Windows-productcode, de geregistreerde gebruiker en organisatie, en het lokale beheerderswachtwoord. Zie voor meer informatie over de takenreeksstap die aan deze variabelen is gekoppeld, [Windows-instellingen toepassen](task-sequence-steps.md#BKMK_ApplyWindowsSettings).  

#### <a name="details"></a>Details  

|Naam actievariabele|Beschrijving|  
|--------------------------|-----------------|  
|OSDComputerName<br /><br /> (invoer)|Geeft de naam van de doelcomputer op.<br /><br /> Voorbeeld:<br /><br /> **"%_SMSTSMachineName%"** (standaard)|  
|OSDProductKey<br /><br /> (invoer)|Geeft de Windows-productcode op. De opgegeven waarde moet tussen 1 en 255 tekens lang zijn.|  
|OSDRegisteredUserName<br /><br /> (invoer)|Hiermee geeft u de standaard geregistreerde gebruikersnaam in het nieuwe besturingssysteem op. De opgegeven waarde moet tussen 1 en 255 tekens lang zijn.|  
|OSDRegisteredOrgName<br /><br /> (invoer)|Hiermee geeft u de standaard geregistreerde organisatienaam in het nieuwe besturingssysteem op. De opgegeven waarde moet tussen 1 en 255 tekens lang zijn.|  
|OSDTimeZone<br /><br /> (invoer)|Hiermee geeft u de standaardinstelling op voor de tijdzone die wordt gebruikt in het nieuwe besturingssysteem.|  
|OSDServerLicenseMode<br /><br /> (invoer)|Hiermee geeft u de Windows Server-licentiemodus op die wordt gebruikt.<br /><br /> Geldige waarden:<br /><br /> **"PerSeat"**<br /><br /> **"PerServer"**|  
|OSDServerLicenseConnectionLimit<br /><br /> (invoer)|Hiermee geeft u het maximumaantal toegestane verbindingen op. Het opgegeven getal moet liggen tussen 5 en 9999 verbindingen.|  
|OSDRandomAdminPassword<br /><br /> (invoer)|Hiermee geeft u een willekeurig gegenereerd wachtwoord op voor het beheerdersaccount in het nieuwe besturingssysteem. Indien ingesteld op **true**, het lokale beheerdersaccount wordt uitgeschakeld op de doelcomputer. Indien ingesteld op **false**, wordt het lokale beheerdersaccount ingeschakeld op de doelcomputer en de waarde van de variabele wordt toegewezen door het lokale beheerderswachtwoord **OSDLocalAdminPassword**.<br /><br /> Geldige waarden:<br /><br /> '**true** ' (standaard)<br /><br /> '**false**'|  
|OSDLocalAdminPassword<br /><br /> (invoer)|Hiermee geeft u het lokale beheerderswachtwoord op. Deze waarde wordt genegeerd als de optie **Willekeurig wachtwoord genereren voor lokale beheerder en het account uitschakelen op alle ondersteunde platforms** wordt ingeschakeld. De opgegeven waarde moet tussen 1 en 255 tekens lang zijn.|  

###  <a name="BKMK_AutoApplyDrivers"></a> Variabelen voor de takenreeksactie Stuurprogramma's automatisch toepassen  
 De variabelen voor deze actie geven op welke Windows-stuurprogramma's op de doelcomputer worden geïnstalleerd en of niet-ondertekende stuurprogramma's worden geïnstalleerd. Zie voor meer informatie over de takenreeksstap die aan deze variabelen is gekoppeld, [stuurprogramma's automatisch toepassen](task-sequence-steps.md#BKMK_AutoApplyDrivers).  

#### <a name="details"></a>Details  

|Naam actievariabele|Beschrijving|  
|--------------------------|-----------------|  
|OSDAutoApplyDriverCategoryList<br /><br /> (invoer)|Een door komma's gescheiden lijst van unieke categorie-id's uit de stuurprogrammacatalogus. Indien opgegeven, houdt de takenreeksactie **Stuurprogramma's automatisch toepassen** alleen rekening met de stuurprogramma's die in ten minste één van deze categorieën vallen bij het installeren van stuurprogramma's. Deze waarde is optioneel en is niet standaard ingesteld. De beschikbare categorie-id's kunnen worden verkregen door de lijst met **SMS_CategoryInstance** -objecten op de site te inventariseren.|  
|OSDAllowUnsignedDriver<br /><br /> (invoer)|Hiermee geeft u op of Windows is geconfigureerd voor het toestaan van de installatie van niet-ondertekende stuurprogramma's. Deze takenreeksvariabele wordt niet gebruikt bij het implementeren van het besturingssysteem Windows Vista of hoger.<br /><br /> Geldige waarden:<br /><br /> **true**<br /><br /> '**false** ' (standaard)|  
|OSDAutoApplyDriverBestMatch<br /><br /> (invoer)|Hiermee geeft u op hoe de takenreeksactie werkt als er meerdere apparaatstuurprogramma's in de stuurprogrammacatalogus zijn die compatibel met een hardwareapparaat. Indien ingesteld op **'true'**, wordt alleen het beste stuurprogramma geïnstalleerd.  Als **false**alle compatibele apparaatstuurprogramma's wordt geïnstalleerd en kiest het besturingssysteem het beste stuurprogramma om te gebruiken.<br /><br /> Geldige waarden:<br /><br /> '**true** ' (standaard)<br /><br /> '**false**'|  

###  <a name="BKMK_CaptureNetworkSettings"></a> Variabelen voor de takenreeksactie Netwerkinstellingen vastleggen  
 De variabelen voor deze actie geven op of de configuratiegegevens van de netwerkadapterinstellingen (TCP/IP, DNS en WINS) worden vastgelegd en of de gegevens van het werkgroep- of domeinlidmaatschap worden gemigreerd als onderdeel van de implementatie van het besturingssysteem. Zie voor meer informatie over de takenreeksstap die aan deze variabelen is gekoppeld, [netwerkinstellingen vastleggen](task-sequence-steps.md#BKMK_CaptureNetworkSettings).  

#### <a name="details"></a>Details  

|Naam actievariabele|Beschrijving|  
|--------------------------|-----------------|  
|OSDMigrateAdapterSettings<br /><br /> (invoer)|Hiermee geeft u op of de configuratiegegevens van de netwerkadapterinstellingen (TCP/IP, DNS en WINS) worden vastgelegd.<br /><br /> Voorbeelden:<br /><br /> '**true** ' (standaard)<br /><br /> '**false**'|  
|OSDMigrateNetworkMembership<br /><br /> (invoer)|Hiermee geeft u op of de gegevens van het werkgroep- of domeinlidmaatschap worden gemigreerd als onderdeel van de implementatie van het besturingssysteem.<br /><br /> Voorbeelden:<br /><br /> '**true** ' (standaard)<br /><br /> '**false**'|  

###  <a name="BKMK_CaptureOperatingSystemImage"></a> Variabelen voor de takenreeksactie Besturingssysteeminstallatiekopie vastleggen  
 De variabelen voor deze actie geven informatie op over de installatiekopie van het besturingssysteem die wordt vastgelegd, zoals waar de installatiekopie is opgeslagen, wie de installatiekopie heeft gemaakt en een beschrijving van de installatiekopie. Zie voor meer informatie over de takenreeksstap die aan deze variabelen is gekoppeld, [Besturingssysteeminstallatiekopie vastleggen](task-sequence-steps.md#BKMK_CaptureOperatingSystemImage).  

#### <a name="details"></a>Details  

|Naam actievariabele|Beschrijving|  
|--------------------------|-----------------|  
|OSDCaptureAccount<br /><br /> (invoer)|Hiermee geeft u de naam van een Windows-account op met machtigingen voor het opslaan van de vastgelegde installatiekopie op een netwerkshare.|  
|OSDCaptureAccountPassword<br /><br /> (invoer)|Hiermee geeft u het wachtwoord op voor het Windows-account dat wordt gebruikt voor het opslaan van de vastgelegde installatiekopie op een netwerkshare.|  
|OSDCaptureDestination<br /><br /> (invoer)|Hiermee geeft u de locatie op waar de vastgelegde installatiekopie wordt opgeslagen. De maximale lengte van de mapnaam is 255 tekens.|  
|OSDImageCreator<br /><br /> (invoer)|Optioneel. De naam van de gebruiker die de installatiekopie heeft gemaakt. Deze naam wordt opgeslagen in het WIM-bestand. De maximale lengte van de gebruikersnaam is 255 tekens.|  
|OSDImageDescription<br /><br /> (invoer)|Optioneel. Een door de gebruiker gedefinieerde beschrijving van de vastgelegde besturingssysteeminstallatiekopie. Deze beschrijving wordt opgeslagen in het WIM-bestand. De maximale lengte van de beschrijving is 255 tekens.|  
|OSDImageVersion<br /><br /> (invoer)|Een optioneel, door de gebruiker gedefinieerd versienummer om toe te wijzen aan de vastgelegde besturingssysteeminstallatiekopie. Dit versienummer wordt opgeslagen in het WIM-bestand. Deze waarde kan een combinatie van letters zijn met een maximale lengte van 32 tekens.|  
|OSDTargetSystemRoot<br /><br /> (invoer)|Hiermee geeft u het pad op naar de Windows-map van het geïnstalleerde besturingssysteem op de referentiecomputer. Dit besturingssysteem is geverifieerd als een ondersteund besturingssysteem voor vastlegging door Configuration Manager.|  

###  <a name="BKMK_CaptureUserState"></a> Variabelen voor de takenreeksactie Gebruikerstoestand vastleggen  
 De variabelen voor deze actie geven informatie op die wordt gebruikt door het Hulpprogramma voor migratie van gebruikersstatus (USMT), zoals de map waarin de gebruikersstatus is opgeslagen, opdrachtregelopties voor USMT en de configuratiebestanden waarmee het vastleggen van gebruikersprofielen wordt beheerd.  Zie voor meer informatie over de takenreeksstap die aan deze variabelen is gekoppeld, [gebruikersstatus vastleggen](task-sequence-steps.md#BKMK_CaptureUserState).  

#### <a name="details"></a>Details  

|Naam actievariabele|Beschrijving|  
|--------------------------|-----------------|  
|OSDStateStorePath<br /><br /> (invoer)|De UNC of lokale padnaam van de map waarin de gebruikersstatus is opgeslagen. Geen standaardwaarde.|  
|OSDMigrateAdditionalCaptureOptions<br /><br /> (invoer)|Hiermee geeft u een gebruiker tool (USMT) vanaf de opdrachtregel statusmigratieopties die worden gebruikt wanneer de gebruikersstatus wordt vastgelegd, maar niet worden weergegeven in de gebruikersinterface van de Configuration Manager. De extra opties worden opgegeven in de vorm van een tekenreeks die wordt toegevoegd aan de automatisch gegenereerde USMT-opdrachtregel.<br /><br /> <br /><br /> De met deze takenreeksvariabele opgegeven USMT-opties opties worden niet gevalideerd op juistheid voorafgaand aan uitvoering van de takenreeks.|  
|OSDMigrateMode<br /><br /> (invoer)|Hiermee kunt u de bestanden aanpassen die worden vastgelegd door USMT. Als deze variabele is ingesteld op 'Simple', wordt alleen de standaard USMT-configuratiebestanden gebruikt. Als deze variabele is ingesteld op 'Advanced', wordt de takenreeksvariabele OSDMigrateConfigFiles bepaald de configuratiebestanden die USMT gebruikt.<br /><br /> Geldige waarden:<br /><br /> **"Simple"**<br /><br /> **"Advanced"**|  
|OSDMigrateConfigFiles<br /><br /> (invoer)|Hiermee geeft u de configuratiebestanden op waarmee het vastleggen van gebruikersprofielen wordt beheerd. Deze variabele wordt alleen gebruikt als OSDMigrateMode is ingesteld op 'Advanced'. Deze door komma's gescheiden lijstwaarde wordt ingesteld om aangepaste gebruikersprofielmigratie uit te voeren.<br /><br /> Voorbeeld: miguser.xml,migsys.xml,migapps.xml|  
|OSDMigrateContinueOnLockedFiles<br /><br /> (invoer)|Hiermee kunt u de gebruikersstatus vastleggen als enkele bestanden niet kunnen worden vastgelegd.<br /><br /> Geldige waarden:<br /><br /> '**true** ' (standaard)<br /><br /> '**false**'|  
|OSDMigrateEnableVerboseLogging<br /><br /> (invoer)|Hiermee schakelt u uitgebreide logboekregistratie in voor USMT.<br /><br /> Geldige waarden:<br /><br /> **true**<br /><br /> '**false** ' (standaard)|  
|OSDMigrateSkipEncryptedFiles<br /><br /> (invoer)|Hiermee geeft u op of versleutelde bestanden worden vastgelegd.<br /><br /> Geldige waarden:<br /><br /> **true**<br /><br /> '**false** ' (standaard)|  
|_OSDMigrateUsmtPackageID<br /><br /> (invoer)|Hiermee geeft u de pakket-ID van de Configuration Manager-pakket dat de USMT-bestanden bevat. Deze variabele is vereist.|  

###  <a name="BKMK_CaptureWindowsSettings"></a> Variabelen voor de takenreeksactie Windows-instellingen vastleggen  
 De variabelen voor deze actie geven op of specifieke Windows-instellingen worden gemigreerd naar de doelcomputer, zoals de naam van de computer, de geregistreerde naam van de organisatie en informatie over de tijdzone. Zie voor meer informatie over de takenreeksstap die aan deze variabelen is gekoppeld, [Windows-instellingen vastleggen](task-sequence-steps.md#BKMK_CaptureWindowsSettings).  

#### <a name="details"></a>Details  

|Naam actievariabele|Beschrijving|  
|--------------------------|-----------------|  
|OSDMigrateComputerName<br /><br /> (invoer)|Hiermee geeft u op of de naam van de computer wordt gemigreerd.<br /><br /> Geldige waarden:<br /><br /> '**true** ' (standaard)<br /><br /> '**false**'<br /><br /> Als de waarde 'true' is, wordt de variabele OSDComputerName ingesteld op de NetBIOS-naam van de computer.|  
|OSDComputerName<br /><br /> (uitvoer)|Ingesteld op de NetBIOS-naam van de computer. De waarde wordt alleen ingesteld als de variabele OSDMigrateComputerName is ingesteld op 'true'.|  
|OSDMigrateRegistrationInfo<br /><br /> (invoer)|Hiermee geeft u op of de computergebruiker en organisatiegegevens worden gemigreerd.<br /><br /> Geldige waarden:<br /><br /> '**true** ' (standaard)<br /><br /> '**false**'<br /><br /> Als de waarde 'true' is, wordt de variabele OSDRegisteredOrgName ingesteld op de geregistreerde organisatienaam van de computer.|  
|OSDRegisteredOrgName<br /><br /> (uitvoer)|Ingesteld op de geregistreerde organisatienaam van de computer. De waarde wordt alleen ingesteld als de variabele OSDMigrateRegistrationInfo is ingesteld op 'true'.|  
|OSDMigrateTimeZone<br /><br /> (invoer)|Hiermee geeft u op of de tijdzone van de computer wordt gemigreerd.<br /><br /> Geldige waarden:<br /><br /> '**true** ' (standaard)<br /><br /> '**false**'<br /><br /> Als de waarde 'true', wordt de variabele OSDTimeZone ingesteld op de tijdzone van de computer.|  
|OSDTimeZone<br /><br /> (uitvoer)|Ingesteld op de tijdzone van de computer. De waarde wordt alleen ingesteld als de variabele OSDMigrateTimeZone is ingesteld op 'true'.|  

###  <a name="BKMK_ConnecttoNetworkFolder"></a> Variabelen voor de takenreeksactie Verbinding maken met netwerkmap  
 De variabelen voor deze actie geven informatie op over een map in een netwerk, zoals het gebruikte account en het wachtwoord waarmee verbinding wordt gemaakt met de netwerkmap, de stationsletter van de map en het pad naar de map. Zie voor meer informatie over de takenreeksstap die aan deze variabelen is gekoppeld, [netwerkmap verbinding](task-sequence-steps.md#BKMK_ConnectToNetworkFolder).  

#### <a name="details"></a>Details  

|Naam actievariabele|Beschrijving|  
|--------------------------|-----------------|  
|SMSConnectNetworkFolderAccount<br /><br /> (invoer)|Hiermee geeft u het administrator-account dat wordt gebruikt om verbinding te maken met de netwerkshare.|  
|SMSConnectNetworkFolderDriveLetter<br /><br /> (invoer)|Hiermee geeft u de netwerkstationsletter op waarmee verbinding wordt gemaakt. Deze waarde is optioneel. Als deze niet is opgegeven, wordt de netwerkverbinding niet toegewezen aan een stationsletter. Als deze waarde wel is opgegeven, moet de waarde liggen in het bereik van D: t/m Z:.  Daarnaast mag u niet X: gebruiken omdat deze stationsletter door Windows PE wordt gebruikt tijdens de Windows PE-fase.<br /><br /> Voorbeelden:<br /><br /> **"D:"**<br /><br /> **"E:"**|  
|SMSConnectNetworkFolderPassword<br /><br /> (invoer)|Hiermee geeft u het netwerkwachtwoord op dat wordt gebruikt om verbinding te maken met de netwerkshare.|  
|SMSConnectNetworkFolderPath<br /><br /> (invoer)|Hiermee geeft u het netwerkpad voor de verbinding op.<br /><br /> Voorbeeld:<br /><br /> **'\\\servername\sharename '**|  

###  <a name="BKMK_EnableBitLocker"></a> Variabelen voor de takenreeksactie BitLocker inschakelen  
 De variabelen voor deze actie geven de opties voor het herstelwachtwoord en de opstartsleutel op die worden gebruikt om BitLocker in te schakelen op de doelcomputer. Zie voor meer informatie over de takenreeksstap die aan deze variabelen is gekoppeld, [BitLocker inschakelen](task-sequence-steps.md#BKMK_EnableBitLocker).  

#### <a name="details"></a>Details  

|Naam actievariabele|Beschrijving|  
|--------------------------|-----------------|  
|OSDBitLockerRecoveryPassword<br /><br /> (invoer)|In plaats van een willekeurig herstelwachtwoord te genereren gebruikt de takenreeksactie **BitLocker inschakelen** de opgegeven waarde als het herstelwachtwoord. De waarde moet een geldig numeriek BitLocker-herstelwachtwoord zijn.|  
|OSDBitLockerStartupKey<br /><br /> (invoer)|In plaats van een willekeurige opstartsleutel voor de sleutelbeheeroptie genereren **opstartsleutel op USB alleen** de **BitLocker inschakelen** takenreeksactie Trusted Platform Module (TPM) gebruikt als de opstartsleutel. De waarde moet een geldige, 256-bits BitLocker-opstartsleutel met Base64-codering zijn.|  

###  <a name="BKMK_FormatPartitionDisk"></a> Variabelen voor de takenreeksactie Schijf formatteren en partitioneren  
 De variabelen voor deze actie geven informatie op voor het formatteren en partitioneren van een fysieke schijf, zoals het schijfnummer en een matrix met partitie-instellingen. Zie voor meer informatie over de takenreeksstap die aan deze variabelen is gekoppeld, [schijf formatteren en partitioneren](task-sequence-steps.md#BKMK_FormatandPartitionDisk).  

#### <a name="details"></a>Details  

|Naam actievariabele|Beschrijving|  
|--------------------------|-----------------|  
|OSDDiskIndex<br /><br /> (invoer)|Hiermee geeft u het nummer van de te partitioneren fysieke schijf op.|  
|OSDDiskpartBiosCompatibilityMode<br /><br /> (invoer)|Hiermee geeft u op of optimalisaties voor cache-uitlijning worden uitgeschakeld wanneer u de harde schijf partitioneert voor compatibiliteit met bepaalde BIOS-typen. Dit kan nodig zijn bij het implementeren van de besturingssystemen Windows XP of Windows Server 2003. Zie [Artikel 931760](http://go.microsoft.com/fwlink/?LinkId=134081) en [Artikel 931761](http://go.microsoft.com/fwlink/?LinkId=134082) in de Microsoft Knowledge Base voor meer informatie.<br /><br /> Geldige waarden:<br /><br /> **true**<br /><br /> '**false** ' (standaard)|  
|OSDGPTBootDisk<br /><br /> (invoer)|Hiermee geeft u op of u een EFI-partitie op een GPT harde schijf maakt, zodat deze kan worden gebruikt als opstartschijf op EFI-computers.<br /><br /> Geldige waarden:<br /><br /> **true**<br /><br /> '**false** ' (standaard)|  
|OSDPartitions<br /><br /> (invoer)|Hiermee geeft u een matrix met partitie-instellingen op. Zie het onderwerp SDK voor toegang tot matrixvariabelen in de takenreeksomgeving.<br /><br /> Deze takenreeksvariabele is een matrixvariabele. Elk element in de matrix staat voor de instellingen voor één partitie op de harde schijf. De instellingen die zijn gedefinieerd voor elke partitie zijn toegankelijk door de naam van de matrixvariabele te combineren met het schijfpartitienummer (op basis van nul) en de naam van de eigenschap.<br /><br /> De namen van de volgende variabelen kunnen bijvoorbeeld worden gebruikt voor het definiëren van de eigenschappen voor de eerste partitie die door deze takenreeksactie op de harde schijf wordt gemaakt:<br /><br /> - **OSDPartitions0Type** -Hiermee wordt het type van de partitie. Dit is een vereiste eigenschap. Geldige waarden zijn '**Primary**', '**Extended**', '**Logical**' en '**Hidden**'.<br />-   **OSDPartitions0FileSystem** – Dit geeft het type bestandssysteem aan dat moet worden gebruikt wanneer de partitie wordt geformatteerd. Dit is een optionele eigenschap. Als u geen bestandssysteem opgeeft, wordt de partitie niet geformatteerd. Geldige waarden zijn '**FAT32**' en '**NTFS**'.<br />-   **OSDPartitions0Bootable** – Hiermee geeft u aan of de partitie opstartbaar is. Dit is een vereiste eigenschap. Als deze waarde is ingesteld op '**true**' voor MBR-schijven, wordt deze de actieve partitie.<br />-   **OSDPartitions0QuickFormat** – Hiermee geeft u het type formattering op dat wordt gebruikt. Dit is een vereiste eigenschap. Als deze waarde is ingesteld op '**true**', wordt een snelle formattering uitgevoerd. Anders wordt een volledige formattering uitgevoerd.<br />-   **OSDPartitions0VolumeName** – Hiermee geeft u de naam op die aan het volume wordt toegewezen wanneer dit wordt geformatteerd. Dit is een optionele eigenschap.<br />-   **OSDPartitions0Size** – Hiermee geeft u de grootte van de partitie op. Eenheden worden opgegeven met de variabele **OSDPartitions0SizeUnits** . Dit is een optionele eigenschap. Als deze eigenschap niet is opgegeven, wordt de partitie gemaakt met alle resterende vrije ruimte.<br />-   **OSDPartitions0SizeUnits** – Hiermee geeft u de eenheden op die worden gebruikt bij het interpreteren van de takenreeksvariabele **OSDPartitions0Size** . Dit is een optionele eigenschap. Geldige waarden zijn '**MB**' (standaard), '**GB**' en '**Percent**'.<br />-   **OSDPartitions0VolumeLetterVariable** – Voor partities wordt altijd de eerstvolgende beschikbare stationsletter in Windows PE gebruikt wanneer deze worden gemaakt. Gebruik deze optionele eigenschap om de naam op te geven van een andere takenreeksvariabele, die wordt gebruikt voor het opslaan van de nieuwe stationsletter voor toekomstig gebruik.<br /><br /> <br /><br /> Als meerdere partities worden gedefinieerd met deze takenreeksactie, kunnen de eigenschappen voor de tweede partitie worden gedefinieerd met behulp van de index in de naam van de variabele; bijvoorbeeld, **OSDPartitions1Type**, **OSDPartitions1FileSystem**, **OSDPartitions1Bootable**, **OSDPartitions1QuickFormat**, **OSDPartitions1VolumeName,** enzovoort.|  
|OSDPartitionStyle<br /><br /> (invoer)|Hiermee geeft u de partitiestijl op die moet worden gebruikt bij het partitioneren van de schijf. '**MBR**' geeft de partitiestijl Master Boot Record aan en '**GPT**' geeft de stijl GUID-partitietabel aan.<br /><br /> Geldige waarden:<br /><br /> **"GPT"**<br /><br /> **"MBR"**|  

###  <a name="BKMK_InstallSoftwareUpdates"></a> Variabelen voor de takenreeksactie Software-updates installeren  
 De variabele voor deze actie geeft aan of alle updates of alleen verplichte updates worden geïnstalleerd. Zie voor meer informatie over de takenreeksstap die aan deze variabelen is gekoppeld, [Software-Updates installeren](task-sequence-steps.md#BKMK_InstallSoftwareUpdates).  

#### <a name="details"></a>Details  

|Naam actievariabele<br /><br /> (invoer)|Beschrijving|  
|----------------------------------------|-----------------|  
|SMSInstallUpdateTarget<br /><br /> (invoer)|Hiermee geeft u op of alle updates of alleen verplichte updates worden geïnstalleerd.<br /><br /> Geldige waarden:<br /><br /> **'All'**<br /><br /> **'Mandatory'**|  

###  <a name="BKMK_JoinDomainWorkgroup"></a> Variabelen voor de takenreeksactie Lid maken van domein of werkgroep  
 De variabelen voor deze actie geven informatie op die nodig is om de doelcomputer lid te maken van een Windows-domein of -werkgroep. Zie voor meer informatie over de takenreeksstap die aan deze variabelen is gekoppeld, [lid worden van domein of werkgroep](task-sequence-steps.md#BKMK_JoinDomainorWorkgroup).  

#### <a name="details"></a>Details  

|Naam actievariabele|Beschrijving|  
|--------------------------|-----------------|  
|OSDJoinAccount<br /><br /> (invoer)|Hiermee geeft u het account op dat wordt gebruikt door de doelcomputer om lid te worden van een Windows-domein. Deze variabele is vereist voor domeinlidmaatschap.|  
|OSDJoinDomainName<br /><br /> (invoer)|Hiermee geeft u de naam op van een Windows-domein waarvan de doelcomputer lid wordt. De lengte van de naam van het Windows-domein moet liggen tussen 1 en 255 tekens.|  
|OSDJoinDomainOUName<br /><br /> (invoer)|Hiermee geeft u de naam in RFC 1779-indeling op van de organisatie-eenheid (OE) waarvan de doelcomputer lid wordt. Als u deze optie opgeeft, moet de waarde het volledige pad bevatten. De lengte van de OU-naam van het Windows-domein moet liggen tussen 0 en 32.767 tekens. Deze waarde wordt niet ingesteld als de variabele **OSDJoinType** is ingesteld op 1 (lid worden van werkgroep).<br /><br /> Voorbeeld:<br /><br /> **LDAP://OU=MyOu,DC=MyDom,DC=MyCompany,DC=com**|  
|OSDJoinPassword<br /><br /> (invoer)|Hiermee geeft u het netwerkwachtwoord op dat wordt gebruikt door de doelcomputer om lid te worden van een Windows-domein. Als de variabele niet is opgegeven, wordt een leeg wachtwoord geprobeerd. Deze waarde is vereist als de variabele **OSDJoinType** is ingesteld op**0**(lid worden van domein).|  
|OSDJoinSkipReboot<br /><br /> (invoer)|Hiermee geeft u aan of het opnieuw opstarten van de doelcomputer wordt overgeslagen nadat deze lid is geworden van het domein of de werkgroep.<br /><br /> Geldige waarden:<br /><br /> **true**<br /><br /> '**false**'|  
|OSDJoinType<br /><br /> (invoer)|Hiermee geeft u aan of de doelcomputer lid wordt van een Windows-domein of een werkgroep. Geef**0**op om de doelcomputer lid te laten worden van een Windows-domein. Geef**1**op om de doelcomputer lid te laten worden van een werkgroep.<br /><br /> Geldige waarden:<br /><br /> **0**<br /><br /> **1**|  
|OSDJoinWorkgroupName<br /><br /> (invoer)|Hiermee geeft u de naam van een werkgroep waarvan de doelcomputer lid wordt. De lengte van de werkgroepnaam moet liggen tussen 1 en 32 tekens.<br /><br /> Voorbeeld:<br /><br /> **"Accounting"**|  

###  <a name="BKMK_PrepareWindowsCapture"></a> Variabelen voor de takenreeksactie Windows voorbereiden voor vastleggen  
 De variabelen voor deze actie geven informatie op waarmee het Windows-besturingssysteem van de doelcomputer wordt vastgelegd. Zie voor meer informatie over de takenreeksstap die aan deze variabelen is gekoppeld, [ConfigMgr-Client voorbereiden voor vastleggen](task-sequence-steps.md#BKMK_PrepareConfigMgrClientforCapture).  

#### <a name="details"></a>Details  

|Naam actievariabele|Beschrijving|  
|--------------------------|-----------------|  
|OSDBuildStorageDriverList<br /><br /> (invoer)|Hiermee geeft u op of sysprep een lijst van stuurprogramma’s voor massaopslagapparaten maakt. Deze instelling geldt alleen voor Windows XP en Windows Server 2003. De sectie [SysprepMassStorage] van het bestand sysprep.inf wordt gevuld met informatie over alle stuurprogramma's voor massaopslag die worden ondersteund door de installatiekopie die moet worden vastgelegd.<br /><br /> Geldige waarden:<br /><br /> **true**<br /><br /> '**false** ' (standaard)|  
|OSDKeepActivation<br /><br /> (invoer)|Hiermee geeft u op of sysprep de markering voor productactivering opnieuw instelt.<br /><br /> Geldige waarden:<br /><br /> **true**<br /><br /> '**false** ' (standaard)|  
|OSDTargetSystemRoot<br /><br /> (uitvoer)|Hiermee geeft u het pad op naar de Windows-map van het geïnstalleerde besturingssysteem op de referentiecomputer. Dit besturingssysteem is geverifieerd als een ondersteund besturingssysteem voor vastlegging door Configuration Manager.|  

###  <a name="BKMK_ReleaseStateStore"></a> Variabelen voor de takenreeksactie Statusopslag vrijgeven  
 De variabelen voor deze actie worden geven informatie op die wordt gebruikt om de opgeslagen gebruikersstatus vrij te geven. Zie voor meer informatie over de takenreeksstap die aan deze variabelen is gekoppeld, [Statusopslag vrijgeven](task-sequence-steps.md#BKMK_ReleaseStateStore).  

#### <a name="details"></a>Details  

|Naam actievariabele|Beschrijving|  
|--------------------------|-----------------|  
|OSDStateStorePath<br /><br /> (invoer)|De UNC of lokale padnaam naar de locatie van waaruit de gebruikersstatus wordt hersteld. Deze waarde wordt gebruikt door zowel de takenreeksactie **Gebruikerstoestand vastleggen** als de takenreeksactie **Gebruikersstatus herstellen** .|  

###  <a name="BKMK_RequestState"></a> Variabelen voor de takenreeksactie Statusopslag opvragen  
 De variabelen voor deze actie geven informatie op die wordt gebruikt om de opgeslagen gebruikersstatus op te vragen, zoals de map op het statusmigratiepunt waarin de gebruikersgegevens zijn opgeslagen. Zie voor meer informatie over de takenreeksstap die aan deze variabelen is gekoppeld, [Statusopslag vrijgeven](../../osd/understand/task-sequence-steps.md#BKMK_ReleaseStateStore).  

#### <a name="details"></a>Details  

|Naam actievariabele|Beschrijving|  
|--------------------------|-----------------|  
|OSDStateFallbackToNAA<br /><br /> (invoer)|Hiermee geeft u op of het netwerktoegangsaccount wordt gebruikt als alternatieve methode wanneer het computeraccount geen verbinding kan maken met het statusmigratiepunt.<br /><br /> Geldige waarden:<br /><br /> **true**<br /><br /> '**false** ' (standaard)|  
|OSDStateSMPRetryCount<br /><br /> (invoer)|Hiermee wordt het aantal pogingen opgegeven dat met deze takenreeksstap wordt uitgevoerd om een statusmigratiepunt te zoeken voordat de stap mislukt. Het opgegeven aantal moet tussen 0 en 600 liggen.|  
|OSDStateSMPRetryTime<br /><br /> (invoer)|Hiermee geeft u het aantal seconden op dat de takenreeksstap moet wachten tussen nieuwe pogingen. Het aantal seconden mag maximaal 30 tekens zijn.|  
|OSDStateStorePath<br /><br /> (uitvoer)|Het UNC-pad naar de map op het statusmigratiepunt waar de gebruikersstatus wordt opgeslagen.|  

###  <a name="BKMK_RestartComputer"></a> Variabelen voor de takenreeksactie Computer opnieuw opstarten  
 De variabelen voor deze actie geven informatie op die wordt gebruikt om de doelcomputer opnieuw op te starten. Zie voor meer informatie over de takenreeksstap die aan deze variabelen is gekoppeld, [Computer opnieuw opstarten](task-sequence-steps.md#BKMK_RestartComputer).  

#### <a name="details"></a>Details  

|Naam actievariabele|Beschrijving|  
|--------------------------|-----------------|  
|SMSRebootMessage<br /><br /> (invoer)|Hiermee geeft u het bericht op dat moet worden weergegeven voor gebruikers voordat de doelcomputer opnieuw wordt opgestart. Als deze variabele niet is ingesteld, wordt de standaardberichttekst weergegeven. Het opgegeven bericht mag maximaal 512 tekens bevatten.<br /><br /> Voorbeeld:<br /><br /> -'Deze computer wordt opnieuw gestart; Sla uw werk."|  
|SMSRebootTimeout<br /><br /> (invoer)|Hiermee geeft u het aantal seconden op dat de waarschuwing wordt weergegeven aan de gebruiker voordat de computer opnieuw wordt opgestart. Geef nul seconden op om aan te geven dat er geen opstartbericht wordt weergegeven.<br /><br /> Voorbeelden:<br /><br /> **"0"** (standaard)<br /><br /> **"5"**<br /><br /> **'10'**|  

###  <a name="BKMK_RestoreUserState"></a> Variabelen voor de takenreeksactie Gebruikersstatus herstellen  
 De variabelen voor deze actie geven informatie op voor het herstellen van de gebruikersstatus van de doelcomputer, zoals de padnaam van de map waaruit de gebruikersstatus wordt hersteld en of het lokale computeraccount is hersteld. Zie voor meer informatie over de takenreeksstap die aan deze variabelen is gekoppeld, [gebruikersstatus herstellen](task-sequence-steps.md#BKMK_RestoreUserState).  

#### <a name="details"></a>Details  

|Naam actievariabele|Beschrijving|  
|--------------------------|-----------------|  
|OSDStateStorePath<br /><br /> (invoer)|De UNC of lokale padnaam van de map van waaruit de gebruikersstatus wordt hersteld.|  
|OSDMigrateContinueOnRestore<br /><br /> (invoer)|Hiermee geeft u op dat het herstel van de gebruikersstatus wordt voortgezet zelfs als sommige bestanden niet kunnen worden hersteld.<br /><br /> Geldige waarden:<br /><br /> '**true** ' (standaard)<br /><br /> '**false**'|  
|OSDMigrateEnableVerboseLogging<br /><br /> (invoer)|Hiermee schakelt u uitgebreide logboekregistratie in voor USMT. Deze waarde is vereist voor de actie en moet worden ingesteld op 'true' of 'false'.<br /><br /> Geldige waarden:<br /><br /> **true**<br /><br /> '**false** ' (standaard)|  
|OSDMigrateLocalAccounts<br /><br /> (invoer)|Hiermee geeft u op of het lokale computeraccount wordt hersteld.<br /><br /> Geldige waarden:<br /><br /> **true**<br /><br /> '**false** ' (standaard)|  
|OSDMigrateLocalAccountPassword<br /><br /> (invoer)|Als de **OSDMigrateLocalAccounts** variabele is 'true', moet deze variabele het wachtwoord dat is toegewezen aan alle lokale accounts die zijn gemigreerd bevatten. Omdat het wachtwoord is toegewezen aan alle gemigreerde lokale accounts, wordt dit beschouwd als een tijdelijk wachtwoord dat later wordt gewijzigd door een andere methode dan de implementatie van besturingssysteem Configuration Manager.|  
|OSDMigrateAdditionalRestoreOptions<br /><br /> (invoer)|Hiermee geeft u aanvullende opdrachtregelopties voor USMT op die worden gebruikt bij het herstellen van de gebruikersstatus. De extra opties worden opgegeven in de vorm van een tekenreeks die wordt toegevoegd aan de automatisch gegenereerde USMT-opdrachtregel. De met deze takenreeksvariabele opgegeven USMT-opties opties worden niet gevalideerd op juistheid voorafgaand aan uitvoering van de takenreeks.|  
|_OSDMigrateUsmtRestorePackageID<br /><br /> (invoer)|Hiermee geeft u de pakket-ID van de Configuration Manager-pakket dat de USMT-bestanden bevat. Deze variabele is vereist.|  

###  <a name="BKMK_RunCommand"></a> Variabelen voor de takenreeksactie Opdrachtregel uitvoeren  
 De variabelen voor deze actie geven informatie op die wordt gebruikt om een opdracht uit te voeren vanaf de opdrachtregel, zoals de werkmap waaruit de opdracht wordt uitgevoerd. Zie voor meer informatie over de takenreeksstap die aan deze variabelen is gekoppeld, [opdrachtregel uitvoeren](task-sequence-steps.md#BKMK_RunCommandLine).  

#### <a name="details"></a>Details  

|Naam actievariabele|Beschrijving|  
|--------------------------|-----------------|  
|SMSTSDisableWow64Redirection<br /><br /> (invoer)|In een 64-bits besturingssysteem wordt het programma op de opdrachtregel standaard gezocht en uitgevoerd met behulp van de WOW64-bestandssysteemredirector, zodat 32-bits versies van programma’s en .dll-bestanden van het besturingssysteem worden gevonden. Wanneer u deze variabele op 'true' instelt, wordt het gebruik van de WOW64-bestandssysteemredirector uitgeschakeld zodat systeemeigen 64-bits versies van besturingsssysteemprogramma's en DLL's kunnen worden gevonden. Deze variabele heeft geen effect wanneer u gebruikmaakt van een 32-bits besturingssysteem.|  
|WorkingDirectory<br /><br /> (invoer)|Hiermee geeft u de beginmap voor een opdrachtregelactie op. De opgegeven mapnaam mag maximaal 255 tekens bevatten.<br /><br /> Voorbeelden:<br /><br /> -   **' C:\\'**<br />-   **"%SystemRoot%"**|  
|SMSTSRunCommandLineUserName<br /><br /> (invoer)|Hiermee geeft u het account op waarmee de opdrachtregel wordt uitgevoerd. De waarde is een tekenreeks in de indeling gebruikersnaam of domein\gebruikersnaam.|  
|SMSTSRunCommandLinePassword<br /><br /> (invoer)|Hiermee geeft u het wachtwoord op voor het account dat is opgegeven door de variabele SMSTSRunCommandLineUserName.|  

### <a name="set-dynamic-variables"></a>Dynamische variabelen instellen  
 De variabelen voor deze actie worden automatisch ingesteld wanneer u de takenreeksstap Dynamische variabelen instellen toevoegt. Zie voor meer informatie over de takenreeksstap die aan deze variabelen is gekoppeld, [dynamische variabelen instellen](task-sequence-steps.md#BKMK_SetDynamicVariables).  

#### <a name="details"></a>Details  

|Naam actievariabele<br /><br /> (invoer)|Beschrijving|  
|----------------------------------------|-----------------|  
|_SMSTSMake|Geeft het merk van de computer aan.|  
|_SMSTSModel|Geeft het model van de computer aan.|  
|_SMSTSMacAddresses|Geeft de MAC-adressen aan die door de computer worden gebruikt.|  
|_SMSTSIPAddresses|Geeft de IP-adressen aan die door de computer worden gebruikt.|  
|_SMSTSSerialNumber|Geeft het serienummer van de computer aan.|  
|_SMSTSAssetTag|Geeft de inventaristag voor de computer aan.|  
|_SMSTSUUID|Geeft de UUID van de computer aan.|  
|_SMSTSDefaultGateways|Geeft de standaardgateways aan die worden gebruikt door de computer.|  

###  <a name="BKMK_SetupWindows"></a> Variabelen voor de takenreeksactie Windows en ConfigMgr installeren  
 De variabele voor deze actie geeft de eigenschappen van clientinstallatie die worden gebruikt bij het installeren van Configuration Manager-client. Zie voor meer informatie over de takenreeksstap die aan deze variabelen is gekoppeld, [Windows en ConfigMgr installeren](task-sequence-steps.md#BKMK_SetupWindowsandConfigMgr).  

#### <a name="details"></a>Details  

|Naam actievariabele<br /><br /> (invoer)|Beschrijving|  
|----------------------------------------|-----------------|  
|SMSClientInstallProperties<br /><br /> (invoer)|Hiermee geeft u de eigenschappen van clientinstallatie die worden gebruikt bij het installeren van Configuration Manager-client.|  

### <a name="upgrade-operating-system"></a>Besturingssysteem bijwerken  
 De variabele voor deze actie geeft aanvullende opdrachtregelopties op die niet beschikbaar in de Configuration Manager console worden toegevoegd aan Setup voor een upgrade van Windows 10. Zie voor meer informatie over de takenreeksstap die aan deze variabelen is gekoppeld, [besturingssysteem bijwerken](task-sequence-steps.md#BKMK_UpgradeOS).  

#### <a name="details"></a>Details  

|Naam actievariabele<br /><br /> (invoer)|Beschrijving|  
|----------------------------------------|-----------------|  
|OSDSetupAdditionalUpgradeOptions<br /><br /> (invoer)|Hiermee geeft u de aanvullende opdrachtregelopties op die worden toegevoegd aan Setup tijdens een upgrade naar Windows 10. De opdrachtregelopties worden niet geverifieerd. Daarom moet u controleren of de optie die u invoert klopt.<br /><br /> Zie [Windows Setup-opdrachtregelopties)](https://msdn.microsoft.com/library/windows/hardware/dn938368\(v=vs.85\).aspx)voor meer informatie.|  
