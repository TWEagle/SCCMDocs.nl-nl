---
title: Variabelen voor de takenreeksactie
titleSuffix: Configuration Manager
description: "Variabelen, zoals netwerk instelling variabelen, gebruiken om op te geven van configuratie-instellingen voor één stap in een takenreeks van Configuration Manager."
ms.custom: na
ms.date: 02/09/2018
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-osd
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: e2269031-0977-4f01-a274-420e00630575
caps.latest.revision: 
caps.handback.revision: 
author: aczechowski
ms.author: aaroncz
manager: dougeby
ms.openlocfilehash: 2928ecb254d08e4ed08c5e79b55e210ce25dcb61
ms.sourcegitcommit: fbde417e3c3002898bd216a7e110e725ae269893
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 02/12/2018
---
# <a name="task-sequence-action-variables-in-system-center-configuration-manager"></a>Takenreeksacties in System Center Configuration Manager

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*

Takenreeksacties geven configuratie-instellingen die worden gebruikt door één stap in een takenreeks van System Center Configuration Manager. Standaard worden de instellingen de takenreeksstap geïnitialiseerd voordat deze wordt uitgevoerd. Deze instellingen zijn beschikbaar alleen terwijl de gekoppelde takenreeksstap wordt uitgevoerd. De takenreeks wordt de variabele actiewaarde met andere woorden, toegevoegd aan de takenreeksomgeving voordat de takenreeksstap wordt uitgevoerd. De takenreeks wordt na de stap wordt uitgevoerd de waarde verwijderd uit de omgeving.  

## <a name="action-variable-example"></a>Voorbeeld actievariabele  
 U kunt bijvoorbeeld een startmap voor een opdrachtregelactie opgeven met behulp van de takenreeksstap **Opdrachtregel uitvoeren** . Deze stap omvat de eigenschap **Beginnen in** waarvan de standaardwaarde is opgeslagen in de takenreeksomgeving als de variabele **WorkingDirectory** . De omgevingsvariabele **WorkingDirectory** wordt geïnitialiseerd voordat de takenreeksactie **Opdrachtregel uitvoeren** wordt uitgevoerd. Tijdens de stap **Opdrachtregel uitvoeren** is de waarde van **WorkingDirectory** toegankelijk via de eigenschap **Beginnen in** . Nadat de stap is voltooid, de takenreeks wordt uitgevoerd, verwijdert u de waarde van de **WorkingDirectory** variabele uit de omgeving. Als de reeks een andere bevat **opdrachtregel uitvoeren** takenreeksstap, de takenreeks initialiseert een nieuw **WorkingDirectory** variabele en stelt het de eerste waarde voor de huidige stap.  

 De *standaard* waarde voor de actie van een takenreeksvariabele is aanwezig wanneer de takenreeksstap wordt uitgevoerd. Als u een *nieuwe* waarde, is beschikbaar voor meerdere stappen in de takenreeks wordt uitgevoerd. Als u een van de aanmaakmethoden voor de takenreeksvariabele gebruikt om de waarde van een ingebouwde variabele te onderdrukken, wordt de nieuwe waarde gehandhaafd in de omgeving en vervangt deze de standaardwaarde voor de overige stappen in de takenreeks. Als u bijvoorbeeld een **Takenreeksvariabele instellen** stap als de eerste stap van de takenreeks, stelt de **WorkingDirectory** variabele **C:\\**, alle **opdrachtregel uitvoeren** stap in de takenreeks maakt gebruik van de nieuwe waarde voor de beginmap.  

## <a name="action-variables-for-task-sequence-actions"></a>Variabelen voor takenreeksacties  
 Configuration Manager-takenreeksvariabelen zijn gegroepeerd op hun bijbehorende takenreeksactie. Gebruik de volgende koppelingen voor het verzamelen van informatie over de variabelen die zijn gekoppeld aan een specifieke actie. De takenreeksvariabelen bepalen hoe de takenreeksactie werkt. De variabelen die u als invoervariabelen markeert, worden door de takenreeksactie gelezen en gebruikt. U kunt ook de [Takenreeksvariabele instellen](task-sequence-steps.md#BKMK_SetTaskSequenceVariable) stap of het TSEnvironment COM-object in te stellen van de variabelen tijdens runtime. Alleen de takenreeksactie markeert variabelen als uitvoervariabelen. Acties die later in de takenreeks lezen deze uitvoervariabelen.  

> [!NOTE]  
>  Niet alle takenreeksacties zijn gekoppeld aan een set takenreeksvariabelen. Bijvoorbeeld: hoewel er variabelen zijn gekoppeld aan de actie BitLocker inschakelen, zijn er geen variabelen gekoppeld aan de actie BitLocker uitschakelen.  



###  <a name="BKMK_ApplyDataImage"></a>Gegevensinstallatiekopie toepassen   
 Zie voor meer informatie [gegevensinstallatiekopie toepassen](task-sequence-steps.md#BKMK_ApplyDataImage). 

#### <a name="details"></a>Details  

|Naam actievariabele|Beschrijving|  
|--------------------------|-----------------|  
|OSDDataImageIndex<br /><br /> (invoer)|Hiermee geeft u de indexwaarde op van de installatiekopie die wordt toegepast op de doelcomputer.|  
|OSDWipeDestinationPartition<br /><br /> (invoer)|Hiermee geeft u op of de bestanden op de doelpartitie worden verwijderd.<br /><br /> Geldige waarden:<br /><br /> **de waarde True** (standaard)<br /><br /> **false**|  



###  <a name="BKMK_ApplyDriverPackage"></a>Stuurprogrammapakket toepassen   
Zie voor meer informatie [stuurprogrammapakket toepassen](task-sequence-steps.md#BKMK_ApplyDriverPackage).  

#### <a name="details"></a>Details  

|Naam actievariabele|Beschrijving|  
|--------------------------|-----------------|  
|OSDApplyDriverBootCriticalContentUniqueID<br /><br /> (invoer)|Hiermee geeft u de inhoud-id op van het te installeren stuurprogramma voor massaopslagapparaten uit het stuurprogrammapakket. Als deze variabele niet is opgegeven, wordt er geen stuurprogramma voor massaopslag geïnstalleerd.|  
|OSDApplyDriverBootCriticalINFFile<br /><br /> (invoer)|Hiermee geeft u het INF-bestand op van het te installeren stuurprogramma voor massaopslag.<br /><br /> <br /><br /> Deze takenreeksvariabele is vereist als OSDApplyDriverBootCriticalContentUniqueID is ingesteld.|  
|OSDApplyDriverBootCriticalHardwareComponent<br /><br /> (invoer)|Hiermee geeft u op of een stuurprogramma voor massaopslagapparaten wordt geïnstalleerd, deze variabele moet **scsi**.<br /><br /> Deze takenreeksvariabele is vereist als OSDApplyDriverBootCriticalContentUniqueID is ingesteld.|  
|OSDApplyDriverBootCriticalID<br /><br /> (invoer)|Hiermee geeft u de essentiële opstart-id op van het te installeren stuurprogramma voor massaopslagapparaten. Deze ID wordt weergegeven de **scsi** sectie van het apparaatstuurprogramma txtsetup.oem-bestand.<br /><br /> Deze takenreeksvariabele is vereist als OSDApplyDriverBootCriticalContentUniqueID is ingesteld.|  
|OSDAllowUnsignedDriver<br /><br /> (invoer)|Hiermee kunt u configureren of Windows de installatie van niet-ondertekende apparaatstuurprogramma's toestaat. Deze takenreeksvariabele wordt niet gebruikt bij het implementeren van het besturingssysteem Windows Vista of hoger.<br /><br /> Geldige waarden:<br /><br /> **true**<br /><br /> **ONWAAR** (standaard)|  



###  <a name="BKMK_ApplyNetworkSettings"></a>Netwerkinstellingen toepassen   
 Zie voor meer informatie [netwerkinstellingen toepassen](task-sequence-steps.md#BKMK_ApplyNetworkSettings).  

#### <a name="details"></a>Details  

|Naam actievariabele|Beschrijving|  
|--------------------------|-----------------|  
|OSDAdapter<br /><br /> (invoer)|Deze takenreeksvariabele is een matrixvariabele. Elk element in de matrix staat voor de instellingen voor één netwerkadapter op de computer. Toegang tot de instellingen voor elke adapter door de naam van de matrixvariabele te combineren met de netwerkadapterindex en de naam van de eigenschap.<br /><br />Als deze stap configureert meerdere netwerkadapters, worden de eigenschappen voor de tweede netwerkadapter gedefinieerd met behulp van de index in de naam van de variabele. Bijvoorbeeld, OSDAdapter1EnableDHCP, OSDAdapter1IPAddressList, OSDAdapter1DNSDomain, OSDAdapter1WINSServerList en OSDAdapter1EnableWINS.<br /><br />Bijvoorbeeld de namen van de volgende variabelen gebruiken voor het definiëren van de eigenschappen van de eerste netwerkadapter voor deze takenreeksstap om te configureren:<br /><br /> <ul><li>**OSDAdapter0EnableDHCP**: **true** Dynamic Host Configuration Protocol (DHCP) wordt ingeschakeld voor de adapter.<br />    Deze instelling is vereist. Mogelijke waarden zijn: **De waarde True** of **False**.</li><li>**OSDAdapter0IPAddressList**: Door komma's gescheiden lijst met IP-adressen voor de adapter. Deze eigenschap wordt genegeerd, tenzij **EnableDHCP** is ingesteld op **false**.<br />    Deze instelling is vereist.</li><li>**OSDAdapter0SubnetMask**: Door komma's gescheiden lijst met subnetmaskers. Deze eigenschap wordt genegeerd, tenzij **EnableDHCP** is ingesteld op **false**.<br />    Deze instelling is vereist.</li><li>**OSDAdapter0Gateways**: Door komma's gescheiden lijst met IP-gatewayadressen. Deze eigenschap wordt genegeerd, tenzij **EnableDHCP** is ingesteld op **false**.<br />    Deze instelling is vereist.</li><li>**OSDAdapter0DNSDomain**: Domain Name System (DNS)-domein voor de adapter.</li><li>**OSDAdapter0DNSServerList**: Door komma's gescheiden lijst met DNS-servers voor de adapter.<br />    Deze instelling is vereist.</li><li>**OSDAdapter0EnableDNSRegistration**: **true** naar het IP-adres voor de adapter in DNS registreren.</li><li>**OSDAdapter0EnableFullDNSRegistration**: **true** naar het IP-adres voor de adapter in DNS registreren onder de volledige DNS-naam voor de computer.</li><li>**OSDAdapter0EnableIPProtocolFiltering**: **true** om in te schakelen van IP-protocolfiltering op de adapter.</li><li>**OSDAdapter0IPProtocolFilterList**: Door komma's gescheiden lijst met protocollen die mogen worden uitgevoerd via IP. Deze eigenschap wordt genegeerd als **EnableIPProtocolFiltering** is ingesteld op **false**.</li><li>**OSDAdapter0EnableTCPFiltering**: **true** om in te schakelen voor de adapter voor het filteren van TCP-poort.</li><li>**OSDAdapter0TCPFilterPortList**: Door komma's gescheiden lijst met poorten waaraan toegangsmachtigingen voor TCP worden toegekend. Deze eigenschap wordt genegeerd als **EnableTCPFiltering** is ingesteld op **false**.</li><li>**OSDAdapter0TcpipNetbiosOptions**: Opties voor NetBIOS via TCP/IP. Mogelijke waarden zijn als volgt:<br /><br /> <ul><li>**0**: NetBIOS-instellingen van DHCP-server gebruiken.</li><li>**1**: NetBIOS via TCP/IP inschakelen.</li><li>**2**: Schakel NetBIOS via TCP/IP.</li></ul></li><li>**OSDAdapter0EnableWINS**: **true** WINS te gebruiken voor naamomzetting.</li><li>**OSDAdapter0WINSServerList**: Door komma's gescheiden lijst met IP-adressen van WINS-server. Deze eigenschap wordt genegeerd, tenzij **EnableWINS** is ingesteld op **true**.</li><li>**OSDAdapter0MacAddress**: MAC-adres gebruikt om instellingen op fysieke netwerkadapter.</li><li>**OSDAdapter0Name**: Naam van de netwerkverbinding zoals deze wordt weergegeven in het netwerk verbindingen besturingsprogramma Configuratiescherm. De naam kan tussen 0 en 255 tekens lang zijn.</li><li>**OSDAdapter0Index**: Index van de instellingen van de netwerkadapter in de matrix van instellingen.<br /><br />     OSDAdapterCount=1<br />    OSDAdapter0EnableDHCP=FALSE<br />    OSDAdapter0IPAddressList=192.168.0.40<br />    OSDAdapter0SubnetMask=255.255.255.0<br />    OSDAdapter0Gateways=192.168.0.1<br />    OSDAdapter0DNSSuffix=contoso.com</li></ul>|  
|OSDAdapterCount<br /><br /> (invoer)|Hiermee geeft u het aantal netwerkadapters op dat op de doelcomputer is geïnstalleerd. Wanneer de waarde  van **OSDAdapterCount** is ingesteld, moeten alle configuratieopties voor elke adapter worden ingesteld. Als u bijvoorbeeld de waarde van **OSDAdapterTCPIPNetbiosOptions** instelt voor een specifieke adapter, moeten alle waarden voor die adapter ook worden geconfigureerd.<br /><br />Als deze waarde niet is opgegeven, worden alle waarden van **OSDAdapter** genegeerd.|  
|OSDDNSDomain<br /><br /> (invoer)|Hiermee geeft u de primaire DNS-server op die wordt gebruikt door de doelcomputer.|  
|OSDDomainName<br /><br /> (invoer)|Hiermee geeft u de naam op van het Windows-domein waarvan de doelcomputer lid wordt. De opgegeven waarde moet een geldige domeinnaam van Active Directory Domain Services zijn.|  
|OSDDomainOUName<br /><br /> (invoer)|Hiermee geeft u de naam in RFC 1779-indeling op van de organisatie-eenheid (OE) waarvan de doelcomputer lid wordt. Als u deze optie opgeeft, moet de waarde het volledige pad bevatten.<br /><br /> Voorbeeld:<br /><br /> **LDAP://OU=MyOu,DC=MyDom,DC=MyCompany,DC=com**|  
|OSDEnableTCPIPFiltering<br /><br /> (invoer)|Hiermee geeft u aan of TCP/IP-filtering is ingeschakeld.<br /><br /> Geldige waarden:<br /><br /> **true**<br /><br /> **ONWAAR** (standaard)|  
|OSDJoinAccount<br /><br /> (invoer)|Hiermee geeft u het netwerkaccount op dat wordt gebruikt voor het toevoegen van de doelcomputer aan een Windows-domein.|  
|OSDJoinPassword<br /><br /> (invoer)|Hiermee geeft u het netwerkwachtwoord op dat wordt gebruikt voor het toevoegen van de doelcomputer aan een Windows-domein.|  
|OSDNetworkJoinType<br /><br /> (invoer)|Hiermee geeft u aan of de doelcomputer lid wordt van een Windows-domein of een werkgroep.<br /><br /> **0** geeft aan dat de doelcomputer lid wordt van een Windows-domein. **1** geeft aan dat de computer lid wordt van een werkgroep.<br /><br /> Geldige waarden:<br /><br /> **0**<br /><br /> **1**|  
|OSDDNSSuffixSearchOrder<br /><br /> (invoer)|Hiermee geeft u de DNS-zoekvolgorde op voor de doelcomputer.|  
|OSDWorkgroupName<br /><br /> (invoer)|Hiermee geeft u de naam op van de werkgroep waarvan de doelcomputer lid wordt.<br /><br /> Deze waarde opgeven of de **OSDDomainName** waarde. De werkgroepnaam mag maximaal 32 tekens lang zijn.<br /><br /> Voorbeeld:<br /><br /> **Accounting**|  



###  <a name="BKMK_ApplyOperatingSystem"></a>Besturingssysteeminstallatiekopie toepassen   
 Zie [Installatiekopie van het besturingssysteem toepassen](task-sequence-steps.md#BKMK_ApplyOperatingSystemImage) voor meer informatie.  

#### <a name="details"></a>Details  

|Naam actievariabele|Beschrijving|  
|--------------------------|-----------------|  
|OSDConfigFileName<br /><br /> (invoer)|Hiermee geeft u de bestandsnaam van het antwoordbestand voor besturingssysteemimplementatie op dat is gekoppeld aan het implementatiepakket voor het besturingssysteem.|  
|OSDImageIndex<br /><br /> (invoer)|Hiermee geeft u de indexwaarde van de installatiekopie op uit het WIM-bestand dat wordt toegepast op de doelcomputer.|  
|OSDInstallEditionIndex<br /><br /> (invoer)|Hiermee geeft u de versie op van het besturingssysteem Windows Vista of hoger dat wordt geïnstalleerd. Als er geen versie is opgegeven, bepaalt Windows Setup welke versie te installeren met behulp van de productcode.<br /><br /> Gebruik alleen de waarde nul (0) als aan de volgende voorwaarden wordt voldaan:<br /><br /> -U installeert een ouder dan Windows Vista-besturingssysteem<br />-U installeert een volumelicentie-editie van Windows Vista of hoger en er geen productcode is opgegeven.<br /><br /> Geldige waarden:<br /><br /> **0** (standaard)|  
|OSDTargetSystemDrive (uitvoer)|Hiermee geeft u de stationsletter op van de partitie die de besturingssysteembestanden bevat.|  



###  <a name="BKMK_ApplyWindowsSettings"></a>Windows-instellingen toepassen   
 Zie voor meer informatie [Windows-instellingen toepassen](task-sequence-steps.md#BKMK_ApplyWindowsSettings).  

#### <a name="details"></a>Details  

|Naam actievariabele|Beschrijving|  
|--------------------------|-----------------|  
|OSDComputerName<br /><br /> (invoer)|Geeft de naam van de doelcomputer op.<br /><br /> Voorbeeld:<br /><br /> **%_SMSTSMachineName%** (default)|  
|OSDProductKey<br /><br /> (invoer)|Geeft de Windows-productcode op. De opgegeven waarde moet tussen 1 en 255 tekens lang zijn.|  
|OSDRegisteredUserName<br /><br /> (invoer)|Hiermee geeft u de standaard geregistreerde gebruikersnaam in het nieuwe besturingssysteem op. De opgegeven waarde moet tussen 1 en 255 tekens lang zijn.|  
|OSDRegisteredOrgName<br /><br /> (invoer)|Hiermee geeft u de standaard geregistreerde organisatienaam in het nieuwe besturingssysteem op. De opgegeven waarde moet tussen 1 en 255 tekens lang zijn.|  
|OSDTimeZone<br /><br /> (invoer)|Hiermee geeft u de standaardinstelling op voor de tijdzone die wordt gebruikt in het nieuwe besturingssysteem.|  
|OSDServerLicenseMode<br /><br /> (invoer)|Hiermee geeft u de Windows Server-licentiemodus op die wordt gebruikt.<br /><br /> Geldige waarden:<br /><br /> **PerSeat**<br /><br /> **PerServer**|  
|OSDServerLicenseConnectionLimit<br /><br /> (invoer)|Hiermee geeft u het maximumaantal toegestane verbindingen op. Het opgegeven getal moet liggen tussen 5 en 9999 verbindingen.|  
|OSDRandomAdminPassword<br /><br /> (invoer)|Hiermee geeft u een willekeurig gegenereerd wachtwoord op voor het beheerdersaccount in het nieuwe besturingssysteem. Indien ingesteld op **true**, Windows Setup schakelt het lokale beheerdersaccount op de doelcomputer. Indien ingesteld op **false**, Windows Setup schakelt het lokale beheerdersaccount op de doelcomputer en wordt de waarde van het wachtwoord ingesteld **OSDLocalAdminPassword**.<br /><br /> Geldige waarden:<br /><br /> **de waarde True** (standaard)<br /><br /> **false**|  
|OSDLocalAdminPassword<br /><br /> (invoer)|Hiermee geeft u het lokale beheerderswachtwoord op. Als u inschakelt **willekeurig wachtwoord genereren voor lokale beheerder en het account uitschakelen op alle ondersteunde platforms**, en vervolgens de stap wordt genegeerd voor deze variabele. De opgegeven waarde moet tussen 1 en 255 tekens lang zijn.|  



###  <a name="BKMK_AutoApplyDrivers"></a>Stuurprogramma's automatisch toepassen   
 Zie voor meer informatie [stuurprogramma's automatisch toepassen](task-sequence-steps.md#BKMK_AutoApplyDrivers).  

#### <a name="details"></a>Details  

|Naam actievariabele|Beschrijving|  
|--------------------------|-----------------|  
|OSDAutoApplyDriverCategoryList<br /><br /> (invoer)|Een door komma's gescheiden lijst van unieke categorie-id's uit de stuurprogrammacatalogus. De **automatisch toepassen van stuurprogramma** stap alleen rekening gehouden met de stuurprogramma's in ten minste één van de opgegeven categorieën. Deze waarde is optioneel en is niet standaard ingesteld. De beschikbare categorie-id's verkrijgen met het inventariseren van de lijst met **SMS_CategoryInstance** objecten op de site.|  
|OSDAllowUnsignedDriver<br /><br /> (invoer)|Hiermee geeft u op of Windows is geconfigureerd voor het toestaan van de installatie van niet-ondertekende stuurprogramma's. Deze takenreeksvariabele wordt niet gebruikt bij het implementeren van het besturingssysteem Windows Vista of hoger.<br /><br /> Geldige waarden:<br /><br /> **true**<br /><br /> **ONWAAR** (standaard)|  
|OSDAutoApplyDriverBestMatch<br /><br /> (invoer)|Als er meerdere apparaatstuurprogramma's in de stuurprogrammacatalogus die compatibel met een hardwareapparaat zijn, bepaalt deze variabele u de stap in te grijpen. Indien ingesteld op **true**, de stap is alleen het beste stuurprogramma geïnstalleerd. Als **false**, de stap installeert alle compatibele apparaatstuurprogramma's en Windows kiest u het beste stuurprogramma om te gebruiken.<br /><br /> Geldige waarden:<br /><br /> **de waarde True** (standaard)<br /><br /> **false**|  
|SMSTSDriverRequestConnectTimeOut|Bij het aanvragen van de stuurprogrammacatalogus, is deze variabele het aantal seconden dat de takenreeks wordt gewacht op de server HTTP-verbinding. Als de verbinding langer dan de time-outinstelling duurt, wordt de aanvraag geannuleerd door de takenreeks wordt uitgevoerd. De time-out is standaard ingesteld op **60** seconden.|  
|SMSTSDriverRequestReceiveTimeOut|Bij het aanvragen van de stuurprogrammacatalogus, wordt deze variabele het aantal seconden dat de takenreeks wordt gewacht op een antwoord is. Als de verbinding langer dan de time-outinstelling duurt, wordt de aanvraag geannuleerd door de takenreeks wordt uitgevoerd. De time-out is standaard ingesteld op **480** seconden.|
|SMSTSDriverRequestResolveTimeOut|Bij het aanvragen van de stuurprogrammacatalogus, wordt deze variabele het aantal seconden dat de takenreeks moet voor HTTP-naamomzetting wachten is. Als de verbinding langer dan de time-outinstelling duurt, wordt de aanvraag geannuleerd door de takenreeks wordt uitgevoerd. De time-out is standaard ingesteld op **60** seconden.|
|SMSTSDriverRequestSendTimeOut|Bij het verzenden van een aanvraag voor de stuurprogrammacatalogus, is deze variabele het aantal seconden dat de takenreeks moet wachten om de aanvraag te verzenden. Als de aanvraag langer dan de time-outinstelling duurt, wordt de aanvraag geannuleerd door de takenreeks wordt uitgevoerd. De time-out is standaard ingesteld op **60** seconden.|



###  <a name="BKMK_CaptureNetworkSettings"></a>Netwerkinstellingen vastleggen   
 Zie voor meer informatie [netwerkinstellingen vastleggen](task-sequence-steps.md#BKMK_CaptureNetworkSettings).  

#### <a name="details"></a>Details  

|Naam actievariabele|Beschrijving|  
|--------------------------|-----------------|  
|OSDMigrateAdapterSettings<br /><br /> (invoer)|Hiermee geeft u op of de configuratiegegevens van de netwerkadapterinstellingen (TCP/IP, DNS en WINS) worden vastgelegd.<br /><br /> Voorbeelden:<br /><br /> **de waarde True** (standaard)<br /><br /> **false**|  
|OSDMigrateNetworkMembership<br /><br /> (invoer)|Hiermee geeft u op of de gegevens van het werkgroep- of domeinlidmaatschap worden gemigreerd als onderdeel van de implementatie van het besturingssysteem.<br /><br /> Voorbeelden:<br /><br /> **de waarde True** (standaard)<br /><br /> **false**|  



###  <a name="BKMK_CaptureOperatingSystemImage"></a>Besturingssysteeminstallatiekopie vastleggen   
 Zie voor meer informatie [Besturingssysteeminstallatiekopie vastleggen](task-sequence-steps.md#BKMK_CaptureOperatingSystemImage).  

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



###  <a name="BKMK_CaptureUserState"></a>Gebruikersstatus vastleggen   
 Zie voor meer informatie [gebruikersstatus vastleggen](task-sequence-steps.md#BKMK_CaptureUserState).  

#### <a name="details"></a>Details  

|Naam actievariabele|Beschrijving|  
|--------------------------|-----------------|  
|OSDStateStorePath<br /><br /> (invoer)|De UNC of lokale padnaam van de map waarin de gebruikersstatus is opgeslagen. Geen standaardwaarde.|  
|OSDMigrateAdditionalCaptureOptions<br /><br /> (invoer)|Aanvullende user state Migration Tool (USMT) opdrachtregelopties die de takenreeks gebruikt voor het vastleggen van gebruikersstatus hulpprogramma. De stap wordt niet weergegeven voor deze instellingen in de takenreekseditor. Deze opties opgeven als een tekenreeks, die de takenreeks wordt toegevoegd aan de automatisch gegenereerde USMT-opdrachtregel.<br /><br />De met deze takenreeksvariabele opgegeven USMT-opties opties worden niet gevalideerd op juistheid voorafgaand aan uitvoering van de takenreeks.|  
|OSDMigrateMode<br /><br /> (invoer)|Hiermee kunt u de bestanden aanpassen die worden vastgelegd door USMT. Als deze variabele is ingesteld op **eenvoudige**, en vervolgens de takenreeks alleen de standaard USMT-configuratiebestanden gebruikt. Als deze variabele is ingesteld op **Geavanceerd**, en vervolgens de takenreeksvariabele OSDMigrateConfigFiles Hiermee geeft u de configuratiebestanden die USMT gebruikt.<br /><br /> Geldige waarden:<br /><br /> **Eenvoudige**<br /><br /> **Geavanceerde**|  
|OSDMigrateConfigFiles<br /><br /> (invoer)|Hiermee geeft u de configuratiebestanden op waarmee het vastleggen van gebruikersprofielen wordt beheerd. Deze variabele wordt alleen gebruikt als OSDMigrateMode is ingesteld op Geavanceerd. Deze door komma's gescheiden lijstwaarde wordt ingesteld om aangepaste gebruikersprofielmigratie uit te voeren.<br /><br /> Voorbeeld: miguser.xml,migsys.xml,migapps.xml|  
|OSDMigrateContinueOnLockedFiles<br /><br /> (invoer)|Als sommige bestanden kan niet, USMT vastleggen, kan deze variabele de gebruikersstatus vastleggen om door te gaan.<br /><br /> Geldige waarden:<br /><br /> **de waarde True** (standaard)<br /><br /> **false**|  
|OSDMigrateEnableVerboseLogging<br /><br /> (invoer)|Hiermee kunt uitgebreide logboekregistratie in voor USMT.<br /><br /> Geldige waarden:<br /><br /> **true**<br /><br /> **ONWAAR** (standaard)|  
|OSDMigrateSkipEncryptedFiles<br /><br /> (invoer)|Hiermee geeft u op of versleutelde bestanden worden vastgelegd.<br /><br /> Geldige waarden:<br /><br /> **true**<br /><br /> **ONWAAR** (standaard)|  
|_OSDMigrateUsmtPackageID<br /><br /> (invoer)|Hiermee geeft u de pakket-ID van de Configuration Manager-pakket dat de USMT-bestanden bevat. Deze variabele is vereist.|  



###  <a name="BKMK_CaptureWindowsSettings"></a>Windows-instellingen vastleggen   
 Zie voor meer informatie [Windows-instellingen vastleggen](task-sequence-steps.md#BKMK_CaptureWindowsSettings).  

#### <a name="details"></a>Details  

|Naam actievariabele|Beschrijving|  
|--------------------------|-----------------|  
|OSDMigrateComputerName<br /><br /> (invoer)|Hiermee geeft u op of de naam van de computer wordt gemigreerd.<br /><br /> Geldige waarden:<br /><br /> **de waarde True** (standaard)<br /><br /> **false**<br /><br /> Als de waarde **true**, wordt de variabele OSDComputerName ingesteld op de NetBIOS-naam van de computer.|  
|OSDComputerName<br /><br /> (uitvoer)|Ingesteld op de NetBIOS-naam van de computer. De waarde wordt alleen ingesteld als de variabele OSDMigrateComputerName is ingesteld op **true**.|  
|OSDMigrateRegistrationInfo<br /><br /> (invoer)|Hiermee geeft u op of voor de stap gebruiker-en organisatiegegevens worden gemigreerd.<br /><br /> Geldige waarden:<br /><br /> **de waarde True** (standaard)<br /><br /> **false**<br /><br /> Als de waarde **true**, wordt de variabele OSDRegisteredOrgName ingesteld op de geregistreerde organisatienaam van de computer.|  
|OSDRegisteredOrgName<br /><br /> (uitvoer)|Ingesteld op de geregistreerde organisatienaam van de computer. De waarde wordt alleen ingesteld als de variabele OSDMigrateRegistrationInfo is ingesteld op **true**.|  
|OSDMigrateTimeZone<br /><br /> (invoer)|Hiermee geeft u op of de tijdzone van de computer wordt gemigreerd.<br /><br /> Geldige waarden:<br /><br /> **de waarde True** (standaard)<br /><br /> **false**<br /><br /> Als de waarde **true**, wordt de variabele OSDTimeZone ingesteld op de tijdzone van de computer.|  
|OSDTimeZone<br /><br /> (uitvoer)|Ingesteld op de tijdzone van de computer. De waarde wordt alleen ingesteld als de variabele OSDMigrateTimeZone is ingesteld op **true**.|  



###  <a name="BKMK_ConnecttoNetworkFolder"></a>Verbinding maken met netwerkmap   
 Zie voor meer informatie [netwerkmap verbinding](task-sequence-steps.md#BKMK_ConnectToNetworkFolder).  

#### <a name="details"></a>Details  

|Naam actievariabele|Beschrijving|  
|--------------------------|-----------------|  
|SMSConnectNetworkFolderAccount<br /><br /> (invoer)|Hiermee geeft u het administrator-account dat wordt gebruikt om verbinding te maken met de netwerkshare.|  
|SMSConnectNetworkFolderDriveLetter<br /><br /> (invoer)|Hiermee geeft u de netwerkstationsletter op waarmee verbinding wordt gemaakt. Deze waarde is optioneel. Als deze niet is opgegeven, wordt de netwerkverbinding niet toegewezen aan een stationsletter. Als deze waarde wel is opgegeven, moet de waarde liggen in het bereik van D: t/m Z:. Daarnaast mag u niet X: gebruiken omdat deze stationsletter door Windows PE wordt gebruikt tijdens de Windows PE-fase.<br /><br /> Voorbeelden:<br /><br /> **D:**<br /><br /> **E:**|  
|SMSConnectNetworkFolderPassword<br /><br /> (invoer)|Hiermee geeft u het netwerkwachtwoord op dat wordt gebruikt om verbinding te maken met de netwerkshare.|  
|SMSConnectNetworkFolderPath<br /><br /> (invoer)|Hiermee geeft u het netwerkpad voor de verbinding op.<br /><br /> Voorbeeld:<br /><br /> **\\\servername\sharename**|  



###  <a name="BKMK_EnableBitLocker"></a> Enable BitLocker   
 Zie voor meer informatie [BitLocker inschakelen](task-sequence-steps.md#BKMK_EnableBitLocker).  

#### <a name="details"></a>Details  

|Naam actievariabele|Beschrijving|  
|--------------------------|-----------------|  
|OSDBitLockerRecoveryPassword<br /><br /> (invoer)|In plaats van een willekeurig herstelwachtwoord te genereren gebruikt de takenreeksactie **BitLocker inschakelen** de opgegeven waarde als het herstelwachtwoord. De waarde moet een geldig numeriek BitLocker-herstelwachtwoord zijn.|  
|OSDBitLockerStartupKey<br /><br /> (invoer)|In plaats van een willekeurige opstartsleutel voor de sleutelbeheeroptie genereren **opstartsleutel op USB alleen** de **BitLocker inschakelen** stap maakt gebruik van de Trusted Platform Module (TPM) als de opstartsleutel. De waarde moet een geldige, 256-bits BitLocker-opstartsleutel met Base64-codering zijn.|  



###  <a name="BKMK_FormatPartitionDisk"></a>Schijf formatteren en partitioneren   
 Zie voor meer informatie [schijf formatteren en partitioneren](task-sequence-steps.md#BKMK_FormatandPartitionDisk).  

#### <a name="details"></a>Details  

|Naam actievariabele|Beschrijving|  
|--------------------------|-----------------|  
|OSDDiskIndex<br /><br /> (invoer)|Hiermee geeft u het nummer van de te partitioneren fysieke schijf op.|  
|OSDDiskpartBiosCompatibilityMode<br /><br /> (invoer)|Wanneer u de harde schijf voor compatibiliteit met bepaalde typen BIOS, geeft deze variabele bepaalt u of optimalisaties voor cache uitlijning. Dit is nodig bij het implementeren van Windows XP of Windows Server 2003-besturingssystemen. Zie [Artikel 931760](http://go.microsoft.com/fwlink/?LinkId=134081) en [Artikel 931761](http://go.microsoft.com/fwlink/?LinkId=134082) in de Microsoft Knowledge Base voor meer informatie.<br /><br /> Geldige waarden:<br /><br /> **true**<br /><br /> **ONWAAR** (standaard)| 
|OSDGPTBootDisk<br /><br /> (invoer)|Geeft aan of er een EFI-partitie op een harde GPT-schijf. Deze partitie EFI-computers gebruiken als opstartschijf.<br /><br /> Geldige waarden:<br /><br /> **true**<br /><br /> **ONWAAR** (standaard)|  
|OSDPartitions<br /><br /> (invoer)|Hiermee geeft u een matrix met partitie-instellingen op. Zie het onderwerp SDK voor toegang tot matrixvariabelen in de takenreeksomgeving.<br /><br /> Deze takenreeksvariabele is een matrixvariabele. Elk element in de matrix staat voor de instellingen voor één partitie op de harde schijf. Toegang tot de instellingen die voor elke partitie zijn gedefinieerd door de naam van de matrixvariabele te combineren met het schijfpartitienummer en de naam van de eigenschap.<br /><br /> Bijvoorbeeld de namen van de volgende variabelen gebruiken voor het definiëren van de eigenschappen voor de eerste partitie die deze stap maakt u op de harde schijf:<br /><br /> - **OSDPartitions0Type**: Geeft het type van de partitie. Deze eigenschap is vereist. Geldige waarden zijn **primaire**, **Extended**, **logisch**, en **verborgen**.<br />-   **OSDPartitions0FileSystem**: Geeft het type van het bestandssysteem te gebruiken bij het opmaken van de partitie. Deze eigenschap is optioneel. Als u geen bestandssysteem opgeeft, wordt in de stap de partitie niet formatteren. Geldige waarden zijn **FAT32** en **NTFS**.<br />-   **OSDPartitions0Bootable**: Hiermee geeft u op of de partitie opstartbaar is. Deze eigenschap is vereist. Als deze waarde is ingesteld op **TRUE** voor MBR-schijven, markeert de stap vervolgens deze partitie als actief.<br />-   **OSDPartitions0QuickFormat**: Geeft het type van de indeling die wordt gebruikt. Deze eigenschap is vereist. Als deze waarde is ingesteld op **TRUE**, de stap wordt een snelle formattering uitgevoerd. Anders wordt een volledige formattering uitgevoerd door de stap.<br />-   **OSDPartitions0VolumeName**: Hiermee geeft u de naam die aan het volume wordt toegewezen wanneer deze is geformatteerd. Deze eigenschap is optioneel.<br />-   **OSDPartitions0Size**: Geeft de grootte van de partitie. Eenheden worden opgegeven met de variabele **OSDPartitions0SizeUnits** . Deze eigenschap is optioneel. Als deze eigenschap niet is opgegeven, wordt de partitie gemaakt met alle resterende vrije ruimte.<br />-   **OSDPartitions0SizeUnits**: De stap maakt gebruik van deze eenheden interpreteren de **OSDPartitions0Size** variabele. Deze eigenschap is optioneel. Geldige waarden zijn **MB** (standaard), **GB**, en **procent**.<br />-   **OSDPartitions0VolumeLetterVariable**: Wanneer deze stap maakt u partities, worden altijd de eerstvolgende beschikbare stationsletter in Windows PE gebruikt. Gebruik deze optionele eigenschap de naam van een andere takenreeksvariabele opgeven. De stap maakt gebruik van deze variabele om op te slaan van de nieuwe stationsletter voor toekomstig gebruik.<br /><br />Als u meerdere partities met deze takenreeksactie definieert, worden de eigenschappen voor de tweede partitie worden gedefinieerd met behulp van de index in de naam van de variabele. Bijvoorbeeld: **OSDPartitions1Type**, **OSDPartitions1FileSystem**, **OSDPartitions1Bootable**, **OSDPartitions1QuickFormat**, en  **OSDPartitions1VolumeName**.|  
|OSDPartitionStyle<br /><br /> (invoer)|Hiermee geeft u de partitiestijl op die moet worden gebruikt bij het partitioneren van de schijf. **MBR** geeft de partitiestijl master boot record, en **GPT** geeft de stijl GUID-partitietabel aan.<br /><br /> Geldige waarden:<br /><br /> **GPT**<br /><br /> **MBR**|  



###  <a name="BKMK_InstallApplication"></a>Toepassing installeren   
 Zie voor meer informatie [toepassing installeren](task-sequence-steps.md#BKMK_InstallApplication).  

#### <a name="details"></a>Details  

|Naam actievariabele<br /><br /> (invoer)|Beschrijving|  
|----------------------------------------|-----------------|  
| TSErrorOnWarning |Geef op of maakt de takenreeksengine een gedetecteerde waarschuwing opvat als een fout opgetreden tijdens deze stap. De taakvolgorde stelt de variabele _TSAppInstallStatus in op **waarschuwing** als een of meer toepassingen of een vereiste afhankelijkheid niet zijn geïnstalleerd omdat deze niet voldeed aan een vereiste. Als u deze variabele instelt op **True**, en de taakvolgorde stelt _TSAppInstallStatus op waarschuwing, het resultaat is een fout opgetreden. De waarde **False** is de standaardinstelling.| 
|SMSTSMPListRequestTimeoutEnabled|Gebruik deze variabele om herhaalde MPList-aanvragen voor het vernieuwen van de client als de client niet op het intranet is inschakelen. <br />Deze variabele is standaard ingesteld op **True**. Als clients zich op internet, kunt u deze variabele instellen op **False** om onnodige vertragingen te voorkomen. Deze variabele is alleen van toepassing op de takenreeksstappen Toepassing installeren en Software-updates installeren.|  
|SMSTSMPListRequestTimeout|Geef op hoeveel milliseconden lang een takenreeks wacht voordat het opnieuw probeert een toepassing te installeren nadat deze is mislukt voor het opvragen van de beheerpuntlijst van locatieservices. Standaard de takenreeks wacht **60000** milliseconden (60 seconden) voordat deze de stap opnieuw en probeert opnieuw, maximaal drie keer.|  



###  <a name="BKMK_InstallSoftwareUpdates"></a>Software-Updates installeren   
Zie voor meer informatie [Software-Updates installeren](task-sequence-steps.md#BKMK_InstallSoftwareUpdates).  

#### <a name="details"></a>Details  

|Naam actievariabele<br /><br /> (invoer)|Beschrijving|  
|----------------------------------------|-----------------|  
|SMSInstallUpdateTarget<br /><br /> (invoer)|Hiermee geeft u op of alle updates of alleen verplichte updates worden geïnstalleerd.<br /><br /> Geldige waarden:<br /><br /> **All**<br /><br /> **Verplichte**|  
|SMSTSSoftwareUpdateScanTimeout| De time-out voor de controle van de software-updates beheren tijdens deze stap. Verhoog de waarde bijvoorbeeld als u verwacht veel updates tijdens de scan dat. De standaardwaarde is **1800** seconden (30 minuten). De variabele waarde is ingesteld in seconden. |
|SMSTSWaitForSecondReboot|Deze optionele takenreeksvariabele bepaalt clientgedrag als de installatie van een software-update moet worden twee opgestart. Deze variabele voordat u deze stap uit om te voorkomen dat een takenreeks mislukt vanwege een tweede keer opnieuw opstarten van de installatie van software-update instellen.<br /><br /> Stel de waarde voor SMSTSWaitForSecondReboot in seconden op te geven hoelang de takenreeks pauzeert bij deze stap terwijl de computer opnieuw wordt opgestart. Geef voldoende tijd voor het geval er een tweede keer opnieuw opstarten is. <br />Bijvoorbeeld, als u SMSTSWaitForSecondReboot op 600 instelt, de takenreeks pauzeert 10 minuten na het opnieuw opstarten voordat u extra stappen uitvoeren. Deze variabele is handig als een enkel Software-Updates installeren takenreeksstap honderden software-updates worden geïnstalleerd.| 
|SMSTSMPListRequestTimeoutEnabled|Gebruik deze variabele om herhaalde MPList-aanvragen voor het vernieuwen van de client als de client niet op het intranet is inschakelen. <br />Deze variabele is standaard ingesteld op **True**. Als clients zich op internet, kunt u deze variabele instellen op **False** om onnodige vertragingen te voorkomen. Deze variabele is alleen van toepassing op de takenreeksstappen Toepassing installeren en Software-updates installeren.|  
|SMSTSMPListRequestTimeout|Geef op hoeveel milliseconden lang een takenreeks wacht voordat het opnieuw probeert te installeren van een software-update nadat deze is mislukt voor het opvragen van de beheerpuntlijst van locatieservices. Standaard de takenreeks wacht **60000** milliseconden (60 seconden) voordat deze de stap opnieuw en probeert opnieuw, maximaal drie keer.|  



###  <a name="BKMK_JoinDomainWorkgroup"></a>Lid worden van domein of werkgroep   
 Zie voor meer informatie [lid worden van domein of werkgroep](task-sequence-steps.md#BKMK_JoinDomainorWorkgroup).  

#### <a name="details"></a>Details  

|Naam actievariabele|Beschrijving|  
|--------------------------|-----------------|  
|OSDJoinAccount<br /><br /> (invoer)|Hiermee geeft u het account dat wordt gebruikt door de doelcomputer aan het Active Directory-domein. Deze variabele is vereist voor domeinlidmaatschap.|  
|OSDJoinDomainName<br /><br /> (invoer)|Geeft de naam van een Active Directory-domein de doelcomputer wordt toegevoegd. De lengte van de domeinnaam moet tussen 1 en 255 tekens.|  
|OSDJoinDomainOUName<br /><br /> (invoer)|Hiermee geeft u de naam in RFC 1779-indeling op van de organisatie-eenheid (OE) waarvan de doelcomputer lid wordt. Als u deze optie opgeeft, moet de waarde het volledige pad bevatten. De lengte van de OU-naam moet tussen 0 en 32.767 tekens. Deze waarde is niet ingesteld als de **OSDJoinType** variabele is ingesteld op **1** (lid worden van werkgroep).<br /><br /> Voorbeeld:<br /><br /> **LDAP://OU=MyOu,DC=MyDom,DC=MyCompany,DC=com**|  
|OSDJoinPassword<br /><br /> (invoer)|Hiermee geeft u het netwerkwachtwoord op dat gebruikmaakt van de doelcomputer aan het Active Directory-domein. Als deze variabele niet wordt onder in de takenreeksomgeving, probeert Windows Setup een leeg wachtwoord. Als de variabele **OSDJoinType** variabele is ingesteld op **0** (lid worden van domein), deze waarde is vereist.|  
|OSDJoinSkipReboot<br /><br /> (invoer)|Hiermee geeft u aan of het opnieuw opstarten van de doelcomputer wordt overgeslagen nadat deze lid is geworden van het domein of de werkgroep.<br /><br /> Geldige waarden:<br /><br /> **true**<br /><br /> **false**|  
|OSDJoinType<br /><br /> (invoer)|Hiermee geeft u aan of de doelcomputer lid wordt van een Windows-domein of een werkgroep. Als u wilt toevoegen aan de doelcomputer een Windows-domein, geef **0**. Als u wilt deelnemen aan de doelcomputer aan een werkgroep, geef **1**.<br /><br /> Geldige waarden:<br /><br /> **0**<br /><br /> **1**|  
|OSDJoinWorkgroupName<br /><br /> (invoer)|Hiermee geeft u de naam van een werkgroep waarvan de doelcomputer lid wordt. De lengte van de werkgroepnaam moet liggen tussen 1 en 32 tekens.<br /><br /> Voorbeeld:<br /><br /> **Accounting**|  



###  <a name="BKMK_PrepareWindowsCapture"></a>Windows voorbereiden voor vastleggen   
 Zie voor meer informatie [Windows voorbereiden voor vastleggen](task-sequence-steps.md#BKMK_PrepareWindowsforCapture).  

#### <a name="details"></a>Details  

|Naam actievariabele|Beschrijving|  
|--------------------------|-----------------|  
|OSDBuildStorageDriverList<br /><br /> (invoer)|Hiermee geeft u op of Sysprep een lijst met stuurprogramma voor massaopslagapparaten maakt. Deze instelling geldt alleen voor Windows XP en Windows Server 2003. Deze variabele vult de sectie [SysprepMassStorage] van het bestand sysprep.inf met informatie over alle stuurprogramma's voor massaopslag die worden ondersteund door de afbeelding die moet worden vastgelegd.<br /><br /> Geldige waarden:<br /><br /> **true**<br /><br /> **ONWAAR** (standaard)|  
|OSDKeepActivation<br /><br /> (invoer)|Hiermee geeft u op of sysprep de markering voor productactivering opnieuw instelt.<br /><br /> Geldige waarden:<br /><br /> **true**<br /><br /> **ONWAAR** (standaard)|  
|OSDTargetSystemRoot<br /><br /> (uitvoer)|Hiermee geeft u het pad op naar de Windows-map van het geïnstalleerde besturingssysteem op de referentiecomputer. Dit besturingssysteem is geverifieerd als een ondersteund besturingssysteem voor vastlegging door Configuration Manager.|  



###  <a name="BKMK_ReleaseStateStore"></a>Statusopslag vrijgeven   
 Zie voor meer informatie [Statusopslag vrijgeven](task-sequence-steps.md#BKMK_ReleaseStateStore).  

#### <a name="details"></a>Details  

|Naam actievariabele|Beschrijving|  
|--------------------------|-----------------|  
|OSDStateStorePath<br /><br /> (invoer)|De UNC of lokale padnaam naar de locatie van waaruit de gebruikersstatus wordt hersteld. Deze waarde wordt gebruikt door zowel de takenreeksactie **Gebruikerstoestand vastleggen** als de takenreeksactie **Gebruikersstatus herstellen** .|  



###  <a name="BKMK_RequestState"></a>Statusopslag opvragen   
  Zie voor meer informatie [Statusopslag vrijgeven](task-sequence-steps.md#BKMK_ReleaseStateStore).  

#### <a name="details"></a>Details  

|Naam actievariabele|Beschrijving|  
|--------------------------|-----------------|  
|OSDStateFallbackToNAA<br /><br /> (invoer)|Wanneer het computeraccount geen verbinding maken met het statusmigratiepunt, wordt deze variabele geeft aan of de takenreeks terugvalt op het gebruik van het netwerktoegangsaccount (NAA).<br /><br /> Geldige waarden:<br /><br /> **true**<br /><br /> **ONWAAR** (standaard)|  
|OSDStateSMPRetryCount<br /><br /> (invoer)|Hiermee wordt het aantal pogingen opgegeven dat met deze takenreeksstap wordt uitgevoerd om een statusmigratiepunt te zoeken voordat de stap mislukt. Het opgegeven aantal moet tussen 0 en 600 liggen.|  
|OSDStateSMPRetryTime<br /><br /> (invoer)|Hiermee geeft u het aantal seconden op dat de takenreeksstap moet wachten tussen nieuwe pogingen. Het aantal seconden mag maximaal 30 tekens zijn.|  
|OSDStateStorePath<br /><br /> (uitvoer)|Het UNC-pad naar de map op het statusmigratiepunt waar de gebruikersstatus wordt opgeslagen.|  



###  <a name="BKMK_RestartComputer"></a>Computer opnieuw opstarten   
 Zie voor meer informatie [Computer opnieuw opstarten](task-sequence-steps.md#BKMK_RestartComputer).  

#### <a name="details"></a>Details  

|Naam actievariabele|Beschrijving|  
|--------------------------|-----------------|  
|SMSRebootMessage<br /><br /> (invoer)|Hiermee geeft u het bericht op dat moet worden weergegeven voor gebruikers voordat de doelcomputer opnieuw wordt opgestart. Als deze variabele niet is ingesteld, wordt de standaardberichttekst weergegeven. Het opgegeven bericht mag maximaal 512 tekens bevatten.<br /><br /> Voorbeeld:<br /><br /> **Sla uw werk op voordat de computer opnieuw wordt opgestart.**|  
|SMSRebootTimeout<br /><br /> (invoer)|Hiermee geeft u het aantal seconden op dat de waarschuwing wordt weergegeven aan de gebruiker voordat de computer opnieuw wordt opgestart. Geef nul seconden op om aan te geven dat er geen opstartbericht wordt weergegeven.<br /><br /> Voorbeelden:<br /><br /> **0** (standaard)<br /><br />  **60**|  



###  <a name="BKMK_RestoreUserState"></a>Gebruikersstatus herstellen   
  Zie voor meer informatie [gebruikersstatus herstellen](task-sequence-steps.md#BKMK_RestoreUserState).  

#### <a name="details"></a>Details  

|Naam actievariabele|Beschrijving|  
|--------------------------|-----------------|  
|OSDStateStorePath<br /><br /> (invoer)|De UNC of lokale padnaam van de map van waaruit de gebruikersstatus wordt hersteld.|  
|OSDMigrateContinueOnRestore<br /><br /> (invoer)|Het proces blijven zelfs als sommige bestanden niet door USMT terugzetten.<br /><br /> Geldige waarden:<br /><br /> **de waarde True** (standaard)<br /><br /> **false**|  
|OSDMigrateEnableVerboseLogging<br /><br /> (invoer)|Hiermee schakelt u uitgebreide logboekregistratie in voor USMT. Deze waarde is vereist voor de actie.<br /><br /> Geldige waarden:<br /><br /> **true**<br /><br /> **ONWAAR** (standaard)|  
|OSDMigrateLocalAccounts<br /><br /> (invoer)|Hiermee geeft u op of het lokale computeraccount wordt hersteld.<br /><br /> Geldige waarden:<br /><br /> **true**<br /><br /> **ONWAAR** (standaard)|  
|OSDMigrateLocalAccountPassword<br /><br /> (invoer)|Als de **OSDMigrateLocalAccounts** variabele is 'true', moet deze variabele het wachtwoord dat is toegewezen aan alle gemigreerde lokale accounts bevatten. USMT wordt hetzelfde wachtwoord toegewezen aan alle gemigreerde lokale accounts. U kunt dit wachtwoord als tijdelijke en deze later wijzigen door een andere methode.|  
|OSDMigrateAdditionalRestoreOptions<br /><br /> (invoer)|Hiermee geeft u aanvullende status migration tool (USMT) opdrachtregelopties die worden gebruikt bij het herstellen van status van de gebruiker. De extra opties worden opgegeven in de vorm van een tekenreeks die wordt toegevoegd aan de automatisch gegenereerde USMT-opdrachtregel. De met deze takenreeksvariabele opgegeven USMT-opties opties worden niet gevalideerd op juistheid voorafgaand aan uitvoering van de takenreeks.|  
|_OSDMigrateUsmtRestorePackageID<br /><br /> (invoer)|Hiermee geeft u de pakket-ID van de Configuration Manager-pakket dat de USMT-bestanden bevat. Deze variabele is vereist.|  



###  <a name="BKMK_RunCommand"></a>Opdrachtregel uitvoeren   
  Zie voor meer informatie [opdrachtregel uitvoeren](task-sequence-steps.md#BKMK_RunCommandLine).  

#### <a name="details"></a>Details  

|Naam actievariabele|Beschrijving|  
|--------------------------|-----------------|  
|SMSTSDisableWow64Redirection<br /><br /> (invoer)|Standaard op een 64-bits besturingssysteem, de takenreeks zoekt en het programma wordt uitgevoerd op de opdrachtregel met behulp van de WOW64-bestandssysteemredirector. Dit gedrag kan de opdracht voor het vinden van 32-bits versies van besturingsssysteemprogramma's en DLL's. Deze variabele instelt op **waar** wordt het gebruik van de WOW64-bestandssysteemredirector uitgeschakeld. De opdracht vindt systeemeigen 64-bits versies van besturingsssysteemprogramma's en DLL's. Deze variabele heeft geen effect wanneer u gebruikmaakt van een 32-bits besturingssysteem.|  
|WorkingDirectory<br /><br /> (invoer)|Hiermee geeft u de beginmap voor een opdrachtregelactie op. De opgegeven mapnaam mag maximaal 255 tekens bevatten.<br /><br /> Voorbeelden:<br /><br /> -   **C:\\**<br />-   **%SystemRoot%**|  
|SMSTSRunCommandLineUserName<br /><br /> (invoer)|Hiermee geeft u het account op waarmee de opdrachtregel wordt uitgevoerd. De waarde is een tekenreeks in de indeling gebruikersnaam of domein\gebruikersnaam.|  
|SMSTSRunCommandLinePassword<br /><br /> (invoer)|Hiermee geeft u het wachtwoord op voor het account dat is opgegeven door de variabele SMSTSRunCommandLineUserName.|  



### <a name="set-dynamic-variables"></a>Dynamische variabelen instellen  
Zie voor meer informatie [dynamische variabelen instellen](task-sequence-steps.md#BKMK_SetDynamicVariables).  

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



###  <a name="BKMK_SetupWindows"></a>Windows en ConfigMgr installeren   
  Zie voor meer informatie [Windows en ConfigMgr installeren](task-sequence-steps.md#BKMK_SetupWindowsandConfigMgr).  

#### <a name="details"></a>Details  

|Naam actievariabele<br /><br /> (invoer)|Beschrijving|  
|----------------------------------------|-----------------|  
|SMSClientInstallProperties<br /><br /> (invoer)|Hiermee geeft u de eigenschappen van clientinstallatie die worden gebruikt bij het installeren van Configuration Manager-client.|  



### <a name="upgrade-operating-system"></a>Besturingssysteem bijwerken  
 Zie voor meer informatie [besturingssysteem bijwerken](task-sequence-steps.md#BKMK_UpgradeOS).  

#### <a name="details"></a>Details  

|Naam actievariabele<br /><br /> (invoer)|Beschrijving|  
|----------------------------------------|-----------------|  
|OSDSetupAdditionalUpgradeOptions<br /><br /> (invoer)|Hiermee geeft u de aanvullende opdrachtregelopties op die worden toegevoegd aan Windows Setup tijdens een upgrade van Windows 10. De takenreeks controleert niet of de opdrachtregelopties.<br /><br /> Zie voor meer informatie [opdrachtregelopties voor Windows Setup](/windows-hardware/manufacture/desktop/windows-setup-command-line-options).|  
