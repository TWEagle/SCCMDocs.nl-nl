---
title: Toolkit-verwijzing
titleSuffix: Microsoft Deployment Toolkit
description: 'Verwijzing naar meer informatie voor Microsoft Deployment Toolkit 2013. '
ms.date: 09/09/2016
ms.prod: configuration-manager
ms.technology: configmgr-osd
ms.topic: article
ms.assetid: ac670143-b7cd-47d0-86ed-14cb2554dfc7
author: aczechowski
ms.author: aaroncz
manager: angrobe
ms.openlocfilehash: f9bd3e2d61ca8b1eddb83fd75de62ba4a123bb7a
ms.sourcegitcommit: 645cd5a324bdd299906efa27eaca5885eafc9e9c
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 01/16/2018
---
# <a name="toolkit-reference-for-the-microsoft-deployment-toolkit"></a>Verwijzing voor de Microsoft Deployment Toolkit Toolkit
 Deze verwijzing maakt deel uit van Microsoft® Deployment Toolkit (MDT) 2013 en biedt configuratie-instellingen die u in het implementatieproces gebruiken kunt. Lees de documenten MDT 2013 *Microsoft Deployment Toolkit voorbeelden Guide* en *met behulp van de Microsoft Deployment Toolkit* voor hulp bij het aanpassen van configuratie-instellingen voor de implementatieomgeving.  

> [!NOTE]
>  In dit document, *Windows* geldt voor de besturingssystemen Windows 8.1, Windows 8, Windows 7, Windows Server® 2012 R2, Windows Server 2012 en Windows Server 2008 R2, tenzij anders vermeld. MDT biedt geen ondersteuning voor ARM-processor gebaseerde versies van Windows. Op deze manier *MDT* verwijst naar MDT 2013, tenzij anders vermeld.  

## <a name="task-sequence-steps"></a>Stappen voor takenreeksen  
 *Takenreeksen* zijn gemaakt door de Takenreekseditor en bestaan uit een gecombineerde reeks stappen die zijn ontworpen om een actie te voltooien. Takenreeksen kunnen werken op de computer opnieuw worden opgestart en kunnen worden geconfigureerd voor het automatiseren van taken op een computer zonder tussenkomst van de gebruiker. U kunt bovendien takenreeksstappen toevoegen aan een takenreeksgroep die zorgt voor een vergelijkbare takenreeksstappen bij elkaar voor betere ordening en foutcontrole.  

 Elke stap van de takenreeks een specifieke taak kunt uitvoeren, zoals valideren dat de doelcomputer geschikt is voor de implementatie-installatiekopie opslaan van gebruikersgegevens op een veilige locatie voor het implementeren van een installatiekopie naar een doelcomputer en terugzetten van de gebruikersgegevens opgeslagen. Deze takenreeksstappen worden hun taken uitvoeren met behulp van hulpprogramma's en scripts die worden geleverd met MDT of het implementatieteam. Gebruik deze verwijzing om te bepalen van de juiste takenreeksgroepen en takenreeksstappen voor het configureren van het implementatieproces en de geldige eigenschappen en opties te gebruiken.  

 De volgende informatie is beschikbaar voor elke takenreeksgroep en stap:  

-   **Naam**. De naam van de takenreeksgroep of -stap  

-   **Beschrijving**. Een beschrijving van het doel van de takenreeksgroep of stap en eventuele relevante informatie met betrekking tot de aanpassing  

-   **Eigenschappen**. Hiermee geeft de geldige configuratie-eigenschappen die u kunt opgeven voor de takenreeksgroep of de stap die definiëren hoe de taak wordt uitgevoerd  

-   **Opties**. Geeft aan dat de geldige configuratie-opties die u kunt opgeven voor de takenreeksgroep of de stap die bepalen of en wanneer de taak wordt uitgevoerd en wat wordt beschouwd als een geslaagde afsluitcode van de taak  

 Zie voor meer informatie over de Takenreekseditor [implementatie van besturingssysteem: Editor voor Takenreeksen](http://technet.microsoft.com/library/bb680396.aspx).  

###  <a name="CommonPropertiesandOptionsforTaskSequenceStepTypes"></a>Algemene eigenschappen en opties voor taaktypen Sequence stap  
 Elke takenreeksgroep en stap heeft configureerbare instellingen op de **eigenschappen** en **opties** tabbladen die gemeenschappelijk voor alle takenreeksgroepen en stappen zijn. Deze algemene instellingen worden kort beschreven in de volgende secties.  

#### <a name="common-properties"></a>Algemene eigenschappen
 Tabel 1 ziet u de instellingen die beschikbaar zijn op de **eigenschappen** tabblad van elke stap van de takenreeks. Voor meer informatie over de **eigenschappen** tabblad voor een bepaalde takenreeksstap, Zie het onderwerp dat overeenkomt met de stap verderop in deze verwijzing.  

> [!NOTE]
>  De reeks stap taaktypen hier vermeld zijn die beschikbaar in de implementatie-Workbench zijn. Aanvullende reeks stap taaktypen mogelijk beschikbaar bij het configureren van takenreeksen met behulp van Microsoft System Center 2012 R2 Configuration Manager.  

##### <a name="table-1-settings-available-on-the-properties-tab"></a>Tabel 1. Instellingen die beschikbaar zijn op het tabblad Eigenschappen  

|**Naam**|**Beschrijving**|**Groep**|**Stap**|  
|-|-|-|-|  
|**Type**|Een alleen-lezen waarde die welk takenreekstype u of de stap aangeeft. Het type worden ingesteld op een van deze waarden:<br /><br /> -Netwerkinstellingen toepassen<br /><br /> -DHCP autoriseren<br /><br /> -Netwerkinstellingen vastleggen<br /><br /> -ADDS configureren<br /><br /> -DHCP configureren<br /><br /> -DNS configureren<br /><br /> -BitLocker inschakelen<br /><br /> -Formatteren en partitioneren van de schijf<br /><br /> -Verzamelen<br /><br /> -Groep<br /><br /> -Stuurprogramma's invoeren<br /><br /> -Toepassing installeren<br /><br /> -Besturingssysteem installeren<br /><br /> -Functies en onderdelen installeren<br /><br /> -Offline installatie-Updates<br /><br /> -Herstellen van domein Join fouten<br /><br /> -Computer opnieuw opstarten<br /><br /> -Opdrachtregel uitvoeren<br /><br /> -Valideren|-|-|  
|**Naam**|Een door de gebruiker gedefinieerde naam die mag worden eenvoudige identificatie en differentiatie van de andere taak stappen.|-|-|  
|**Beschrijving**|Een door de gebruiker gedefinieerde beschrijving die u de taak sequence stap vereisten en taken gemakkelijk te begrijpen moet.|-|-|  

#### <a name="common-options"></a>Algemene opties  
 Tabel 2 ziet u de instellingen die beschikbaar op het tabblad Opties van een takenreeksstap zijn. Zie voor meer informatie over het tabblad Opties, [taak reeks opties tabblad](http://technet.microsoft.com/library/bb693661.aspx).  

##### <a name="table-2-settings-available-on-the-options-tab"></a>Tabel 2. Instellingen die beschikbaar zijn op het tabblad Opties  

|**Naam**|**Beschrijving**|**Groep**|**Stap**|  
|-|-|-|-|
|**Deze stap uitschakelen**|Selecteer deze optie uitschakelen van deze takenreeksstap.|-|-|  
|**Geslaagd-codes**|Afsluitcodes van het hulpprogramma die zijn gekoppeld aan deze takenreeksstap, die aangeven dat de stap is voltooid.||-|  
|**Doorgaan bij fout** |Selecteer deze optie om de Taaksequencer aanvullende takenreeksstappen verwerkt als een fout optreedt.|-|-|  
|**Voorwaardelijke instructies**|Een of meer voorwaarden die de uitvoering van deze takenreeksgroep of -stap beperken. Deze voorwaardelijke zijn gebaseerd op het volgende:<br /><br /> -Eigenschappen bestand<br /><br /> -Eigenschappen map<br /><br /> Versie van besturingssysteem:<br /><br /> -Is een bepaalde architectuur<br /><br /> -Een bepaalde versie is<br /><br /> -Query Windows Management Instrumentation (WMI)<br /><br /> Registerinstelling:<br /><br /> -Bestaat<br /><br /> -Bestaat niet<br /><br /> -Is gelijk aan<br /><br /> -Is niet gelijk aan<br /><br /> -Groter zijn dan<br /><br /> -Groter dan of gelijk aan<br /><br /> -Minder dan<br /><br /> -Minder dan of gelijk aan<br /><br /> -Geïnstalleerde software<br /><br /> Takenreeksvariabele:<br /><br /> -Bestaat<br /><br /> -Is gelijk aan<br /><br /> -Is niet gelijk aan<br /><br /> -Groter zijn dan<br /><br /> -Groter dan of gelijk aan<br /><br /> -Minder dan<br /><br /> -Minder dan of gelijk aan<br /><br /> Deze voorwaarden kunnen worden gegroepeerd met **als** instructies voor het testen van alle voorwaarden, elke voorwaarde of geen voorwaarde die wordt geëvalueerd als waar.|-|-|  

> [!NOTE]
>  Aanvullende voorwaardelijke instructies mogelijk beschikbaar wanneer u Configuration Manager voor het configureren van takenreeksstappen.  

###  <a name="SpecificPropertiesandSettingsforTaskSequenceStepTypes"></a>Specifieke eigenschappen en instellingen voor taaktypen Sequence stap  
 Sommige eigenschappen en de parameters van elk type takenreeks stap zijn uniek voor dat type. Elk type met unieke eigenschappen en -instellingen wordt weergegeven in de volgende secties met een unieke stap eigenschappen van takenreeks en instellingen.  

#### <a name="apply-network-settings"></a>Netwerkinstellingen toepassen  
 Deze takenreeksstap configureert u de netwerkadapter op de doelcomputer. Zie voor meer informatie over welke script bewerkstelligt deze taak en welke eigenschappen worden gebruikt, [ZTINICConfig.wsf](#ZTINICConfig.wsf).  

 De unieke eigenschappen en instellingen voor de **netwerkinstellingen toepassen** stap takenreekstype zijn:  

##### <a name="properties"></a>Eigenschappen  
|**Naam**|**Waarde**|  
|-|-|  
|**Type**|Netwerkinstellingen toepassen|  

##### <a name="settings"></a>Instellingen  
|**Naam**|**Waarde**|  
|-|-|  
|**Naam**|De naam moet worden toegewezen aan de netwerkverbinding.|  
|**Een IP-adres automatisch ophalen**|Wanneer u selecteert, worden Dynamic Host Configuration Protocol (DHCP) wordt gebruikt voor het verkrijgen van de vereiste IP (Internet Protocol) configuratie-instellingen voor de netwerkverbinding. Dit is standaard geselecteerd.|  
|**Gebruik de volgende IP-adres**|Wanneer u selecteert, kunt u opgeven dat een of meer IP-adres en subnetmasker masker combinaties naast gateways die wordt toegewezen aan de netwerkverbinding.|  
|**Een Domain Name System (DNS)-server automatisch ophalen**|Wanneer u selecteert, wordt DHCP wordt gebruikt voor het verkrijgen van de vereiste IP-configuratie-instellingen voor de netwerkverbinding. Dit is standaard geselecteerd.|  
|**Gebruik de volgende DNS-servers**|Wanneer u selecteert, kunt u opgeven dat een of meer DNS-server IP-adressen die worden toegewezen aan de netwerkverbinding.|  
|**DNS-achtervoegsel**|De DNS-achtervoegsel dat wordt toegepast op alle netwerkverbindingen die TCP/IP gebruiken.|  
|**Het adres van deze verbinding in DNS registreren**|Hiermee geeft u op dat de computer het dynamische registratie van de IP-adressen (via DNS) van deze verbinding met de volledige computernaam van deze computer probeert.|  
|**Gebruik DNS-achtervoegsel van deze verbinding in DNS-registratie**|Hiermee geeft u op of dynamische DNS-updates wordt gebruikt om de IP-adressen en de verbindingsspecifieke domeinnaam van deze verbinding te registreren.|  
|**WINS-serveradressen**|U kunt een of meer Windows Internet Naming Service (WINS)-server IP-adressen die worden toegewezen aan de netwerkverbinding opgeven.|  
|**LMHOSTS-lookup inschakelen**|Hiermee geeft u op of een bestand local area network (LAN) Manager Hosts (LMHOSTS) voor naamomzetting voor network basic input/output system (NetBIOS) wordt gebruikt.|  
|**Standaard**|Hiermee bepaalt u of deze netwerkverbinding de instelling of NetBIOS via TCP/IP (NetBT) van een DHCP-server uit te schakelen. Dit is standaard geselecteerd.|  
|**NetBIOS via TCP/IP inschakelen**|Geeft aan dat deze netwerkverbinding NetBT gebruikt en WINS.|  
|**NetBIOS via TCP/IP uitschakelen**|Hiermee geeft u op of deze netwerkverbinding geen NetBT en WINS gebruikt.|  

#### <a name="authorize-dhcp"></a>DHCP autoriseren  
 Deze takenreeksstap machtigt de doelcomputer als een DHCP-server. Voor meer informatie over welke script voert deze taak en welke eigenschappen u gebruikt, Zie [ZTIAuthorizeDHCP.wsf](#ZTIAuthorizeDHCP.wsf).  

 De unieke eigenschappen en instellingen voor de **DHCP machtigen** stap takenreekstype zijn:  

##### <a name="properties"></a>Eigenschappen  

|**Naam**|**Beschrijving**|  
|-|-|  
|**Type**|Dit type alleen-lezen wordt ingesteld op **DHCP-Server machtigen**.|  

##### <a name="settings"></a>Instellingen  
|**Naam**|**Beschrijving**|  
|-|-|  
|**Naam**|**Beschrijving**|  
|**Account**|Een gebruikersaccount dat lid is van de groep Ondernemingsadministrators moet worden gebruikt wanneer DHCP machtigen voor de doelcomputer.|  

#### <a name="capture-network-settings"></a>Netwerkinstellingen vastleggen  
 Deze takenreeksstap haalt instellingen van de netwerkadapter van de doelcomputer. Voor meer informatie over welke script voert deze taak en welke eigenschappen u gebruikt, Zie [ZTINICConfig.wsf](#ZTINICConfig.wsf).  

 De unieke eigenschappen en instellingen voor de **netwerkinstellingen vastleggen** stap takenreekstype zijn:  

##### <a name="properties"></a>Eigenschappen  
|**Naam**|**Beschrijving**|
|-|-|  
|**Naam**|**Beschrijving**|  
|**Type**|Dit type alleen-lezen wordt ingesteld op **netwerkinstellingen vastleggen**.|  

##### <a name="settings"></a>Instellingen  
|**Naam**|**Beschrijving**|  
|-|-|  
|Geen|Geen|  

#### <a name="configure-adds"></a>ADDS configureren  
 Deze takenreeksstap configureert de doelcomputer als een domeincontroller Active Directory® Domain Services (AD DS). Zie voor meer informatie over de instellingen die worden vermeld in de volgende tabellen en dat deze takenreeksstap kan configureert het Microsoft Help en ondersteuning-artikel [zonder toezicht promotie en degradatie van Windows 2000 en Windows Server 2003-domein domeincontrollers](http://support.microsoft.com/kb/223757).  

 De unieke eigenschappen en instellingen voor de **configureren VOEGT** stap takenreekstype zijn:  

##### <a name="properties"></a>Eigenschappen  
|**Naam**|**Beschrijving**|  
|-|-|  
|**Type**|Dit type alleen-lezen wordt ingesteld op **configureren VOEGT**.|  

##### <a name="settings"></a>Instellingen  
|**Naam**|**Beschrijving**|  
|-|-|  
|Maken|Hiermee geeft u de configuratie die wordt gebruikt voor het configureren van de doelcomputer. De configuratiesets zijn:<br /><br /> - **Nieuwe domain controller replica**. Hiermee maakt u een extra domeincontroller in een bestaand AD DS-domein<br /><br /> - **Nieuwe alleen-lezen domeincontroller (RODC) replica**. Hiermee maakt u een RODC<br /><br /> - **Nieuwe domein in een bestaand forest**. Hiermee maakt u een domein in een bestaand AD DS-forest<br /><br /> - **Nieuwe domeinstructuur in een bestaand forest**. Hiermee maakt u een nieuwe structuur in een bestaand AD DS-forest<br /><br /> - **Nieuwe forest**. Hiermee maakt u een nieuw AD DS-forest|  
|**De DNS-domeinnaam**|De DNS-naam van het nieuwe of bestaande domein.|  
|**NetBIOS-domeinnaam**|De NetBIOS-naam van de nieuwe onderliggende domein, onderliggende domeinstructuur of -forest dat pre-AD DS-clients gebruiken voor toegang tot het domein. Deze naam moet uniek zijn in het netwerk.|  
|**DNS-naam**|De DNS-naam van het onderliggende domein of domeinstructuur.|  
|**De brondomeincontroller voor replicatie**|De naam van de domeincontroller van waaruit de bron van AD DS op de nieuwe replica- of back-domeincontroller upgraden installaties. Als er geen waarde wordt opgegeven, wordt de dichtstbijzijnde domeincontroller van het domein wordt gerepliceerd standaard geselecteerd.|  
|**Account**|Het account dat wordt gebruikt om de configuratie wordt uitgevoerd.|  
|**Herstelwachtwoord (veilige modus)**|Het wachtwoord voor het offline Administrator-account dat wordt gebruikt in de herstelmodus van AD DS.|  
|**DNS installeren als dat niet al aanwezig zijn**|Wanneer u selecteert, wordt DNS geïnstalleerd als deze nog niet is geïnstalleerd.|  
|**Deze domeincontroller een globale catalogusserver (GC) maken**|Geeft aan of de replica wordt ook een GC-server. Wanneer u selecteert, wordt de doelcomputer worden geconfigureerd als een GC-server als de brondomeincontroller voor replicatie een GC-server.|  
|**Wachten op alleen kritieke replicatie**|Wanneer u selecteert, wordt deze instelling bepaalt u dat of alleen kritieke replicatie afkomstig is tijdens de replicatiefase van Dcpromo. Niet-kritieke replicatie hervatten wanneer de computer opnieuw wordt opgestart als domeincontroller.|  
|**Forest-functionaliteitsniveau**|Hiermee geeft u het functionele niveau voor een nieuw forest. Beschikbare opties zijn:<br /><br /> -Windows Server 2003<br /><br /> -Windows Server 2008<br /><br /> -Windows Server 2008 R2|  
|**Functionaliteitsniveau van domein**|Hiermee geeft u het functionele niveau voor een nieuw domein. Beschikbare opties zijn:<br /><br /> -Windows Server 2003<br /><br /> -Windows Server 2008<br /><br /> -Windows Server 2008 R2|  
|**Database**|Volledig gekwalificeerde, niet – Universal Naming Convention UNC-map op een harde schijf van de lokale computer die als voor de AD DS-database (NTDS.dit host fungeert). Als de map bestaat, moet deze niet leeg zijn. Als deze niet bestaat nog, wordt deze gemaakt. Vrije schijfruimte op het geselecteerde logische station moet 200 megabyte (MB) en mogelijk grote wanneer afrondingsfouten optreden en voor alle objecten in het domein. Voor de beste prestaties moet de directory zich bevinden op een speciale harde schijf.|  
|**Logboekbestanden**|Volledig gekwalificeerde, niet-UNC-map op een harde schijf op de lokale computer voor het hosten van de AD DS-logboekbestanden. Als de map bestaat, moet deze niet leeg zijn. Als deze niet bestaat nog, wordt deze gemaakt.|  
|**SYSVOL**|Volledig gekwalificeerde, niet-UNC-map op een harde schijf van de lokale computer die als host voor de AD DS System Volume (SYSVOL)-bestanden fungeert. Als de map bestaat, moet deze niet leeg zijn. Als deze niet bestaat nog, wordt deze gemaakt. De map moet zich bevinden op een partitie die is geformatteerd met het bestandssysteem NTFS versie 5.0. Voor de beste prestaties moet de directory zich bevinden op een andere fysieke schijf dan het besturingssysteem.|  
|**Sitenaam**|De waarde van een bestaande AD DS-site waarop u de nieuwe domeincontroller worden gevonden. Als u niet opgeeft, wordt er een geschikte site geselecteerd. Deze optie is alleen van toepassing op de nieuwe structuur in een nieuw forest-scenario. Voor alle andere scenario's, wordt een site geselecteerd met de huidige site en elk subnet van de configuratie van het forest.|  

#### <a name="configure-dhcp"></a>DHCP configureren  
 Deze takenreeksstap configureert u de DHCP-serverservice op de doelcomputer. Voor meer informatie over welke script voert deze taak en welke eigenschappen u gebruikt, Zie [ZTIConfigureDHCP.wsf](#ZTIConfigureDHCP.wsf).  

 De unieke eigenschappen en instellingen voor de **DHCP configureren** stap takenreekstype zijn:  

##### <a name="properties"></a>Eigenschappen  
|**Naam**|**Beschrijving**|  
|-|-|  
|**Type**|Dit type alleen-lezen wordt ingesteld op **DHCP-Server configureren**.|  

##### <a name="settings"></a>Instellingen  
|**Naam**|**Beschrijving**|  
|-|-|  
|**Naam**|DHCP configureren|  
|Details van het bereik|Deze opties zijn van toepassing op alle clientcomputers die een lease binnen dat specifieke bereik. Scope-optie waarden zijn altijd van toepassing op alle computers die een lease in een bepaald bereik, tenzij ze worden overschreven door de opties die zijn toegewezen aan de klasse of client reservering geconfigureerd.<br /><br /> Binnen de **bereik Details** instelt, kunnen de volgende onderliggende instellingen worden geconfigureerd:<br /><br /> - **De naam van het bereik**. De naam van een gebruiker te definiëren<br /><br /> - **Eerste IP-adres**. Het eerste IP-adres voor de scope<br /><br /> - **IP-eindadres**. De IP-eindadres voor het bereik<br /><br /> - **Subnetmasker**. Het subnetmasker van het clientsubnet<br /><br /> - **Leaseduur voor DHCP-clients**. De duur die de DHCP-lease geldig voor de client is<br /><br /> - **Beschrijving**. Een beschrijving van het bereik<br /><br /> - **Uitsluiten van IP-adresbereik, eerste IP-adres**. Het eerste IP-adres voor het bereik van IP-adressen op die moeten worden uitgesloten van het bereik<br /><br /> -                                 **Uitsluiten van IP-adresbereik, laatste IP-adres**. De IP-eindadres voor het bereik van IP-adressen op die moeten worden uitgesloten van het bereik<br /><br /> - **003 router**. Een lijst met IP-adressen voor routers in het clientsubnet<br /><br /> - **006 DNS-Servers**. Een lijst met IP-adressen voor DNS-naamservers die beschikbaar zijn voor de client<br /><br /> - **015 DNS-domeinnaam**. De domeinnaam die de DHCP-client gebruiken moet tijdens het omzetten van niet-gekwalificeerde domeinnamen met DNS<br /><br /> -                                 **044 WINS/NBNS Servers**. De IP-adressen voor de NetBIOS-naamservers (NBNSes) in het netwerk<br /><br /> - **046 WINS/NBT-knooppunttype**. Het clientknooppunttype configureert voor NetBT-clients<br /><br /> - **060 PXE-Client**. Het adres dat wordt gebruikt voor de bootstrap clientcode (Pre-Boot Execution Environment)|  
|Serveropties|Deze opties zijn algemeen van toepassing voor alle scopes en klassen die zijn gedefinieerd op elke DHCP-server en voor alle clients die een DHCP-server-services. Geconfigureerde server optiewaarden zijn altijd van toepassing tenzij ze worden overschreven door de opties die zijn toegewezen aan andere reservering bereik, klasse of een client.<br /><br /> Binnen de **serveropties** instelt, kunnen de volgende onderliggende instellingen worden geconfigureerd:<br /><br /> - **003 router**. Een lijst met IP-adressen voor routers in het clientsubnet<br /><br /> - **006 DNS-Servers**. Een lijst met IP-adressen voor DNS-naamservers die beschikbaar zijn voor de client<br /><br /> - **015 DNS-domeinnaam**. De domeinnaam die de DHCP-client gebruiken moet tijdens het omzetten van niet-gekwalificeerde domeinnamen met de DNS-server<br /><br /> - **044 WINS/NBNS Servers**. Geeft een lijst van de IP-adressen voor NBNSes op het netwerk<br /><br /> -                                 **046 WINS/NBT-knooppunttype**. Het clientknooppunttype configureert voor NetBT-clients<br /><br /> - **060 PXE-Client**. Het adres dat wordt gebruikt voor PXE-client-bootstrapcode|  

#### <a name="configure-dns"></a>DNS configureren  
 Deze takenreeksstap wordt DNS geconfigureerd op de doelcomputer. Voor meer informatie over welke script voert deze taak en welke eigenschappen u gebruikt, Zie [ZTIConfigureDNS.wsf](#ZTIConfigureDNS.wsf).  

 De unieke eigenschappen en instellingen voor de **DNS configureren** stap takenreekstype zijn:  

##### <a name="properties"></a>Eigenschappen  
|**Naam**|**Beschrijving**|  
|-|-|  
|**Type**|Dit type alleen-lezen wordt ingesteld op **DNS-Server configureren**.|  

##### <a name="settings"></a>Instellingen  
|**Naam**|**Beschrijving**|  
|-|-|  
|**Naam**|DNS configureren|  
|Zones|Binnen de **bereik Details** instelt, kunnen de volgende onderliggende instellingen worden geconfigureerd:<br /><br /> -                                 **Naam van de DNS-zone**. De naam van een gebruiker te definiëren<br /><br /> -Type. Het type van DNS-zone moet worden gemaakt<br /><br /> - **Replicatie**. Hiermee geeft u de replicatieschema gebruikt voor het delen van gegevens tussen DNS-servers<br /><br /> - **De bestandsnaam zone**. De zone DNS-databasebestand<br /><br /> -                                 **Dynamische updates**. Kunnen DNS-clients te registreren en de resourcerecords dynamisch bijwerken met een DNS-server wanneer er wijzigingen zijn<br /><br /> -                                 **Verlopen bronrecords opruimen**. Hiermee verwijdert u verouderde bronrecords|  
|Eigenschappen van server|De volgende instellingen in de submap zijn in de instelling van de servereigenschappen worden geconfigureerd:<br /><br /> -                                 **Recursie**. Hiermee geeft u aan dat de DNS-server geen recursie op elke query uitvoert<br /><br /> - **BIND secundaire replica's**. Hiermee bepaalt u of indeling voor snelle overdracht om over te dragen van een zone naar DNS-servers waarop oudere Berkeley Internet Name Domain (BIND)-implementaties<br /><br /> - **Laden mislukt indien ongeldige gegevens**. Hiermee geeft u dat de DNS-server moet bestanden strikt parseren<br /><br /> -                                 **Round robin inschakelen**. Hiermee geeft u dat de DNS-server moet gebruiken de round-robin mechanisme om te draaien en de volgorde een lijst met bronrecords als er bestaan meerdere bronrecords van hetzelfde type bestaat voor een query-antwoord<br /><br /> - **Netmask-ordening inschakelen**. Hiermee geeft u op of de DNS-server opnieuw bronrecords binnen dezelfde resourcerecord ingesteld in het antwoord op een query op basis van het IP-adres van de bron van de query rangschikken moet<br /><br /> - **Cache beveiligen tegen vervuiling**. Hiermee geeft u op of de DNS-server proberen zal om antwoorden te vermijden op te schonen<br /><br /> - **Naamcontrole**. Hiermee configureert u de methode naamcontrole moet worden gebruikt|  

> [!NOTE]
>  De **DNS configureren** takenreeksstap gebruikt het hulpprogramma Dnscmd, die is opgenomen in Windows-ondersteuningsprogramma's, configureren van DNS. Controleer of Windows-ondersteuningsprogramma's is geïnstalleerd voordat u de **DNS configureren** takenreeksstap.  

> [!NOTE]
>  Zie voor meer informatie over de eigenschappen van deze server [Dnscmd](http://technet.microsoft.com/library/cc772069.aspx).  

#### <a name="enable-bitlocker"></a>BitLocker inschakelen  
 Deze takenreeksstap configureert BitLocker®-stationsversleuteling op de doelcomputer. Zie voor meer informatie over dit staptype [BitLocker inschakelen](http://technet.microsoft.com/library/bb632526.aspx).  

 De unieke eigenschappen en instellingen voor de **BitLocker inschakelen** stap takenreekstype zijn:  

##### <a name="properties"></a>Eigenschappen  
|**Naam**|**Beschrijving**|  
|-|-|  
|**Type**|Dit type alleen-lezen wordt ingesteld op **BitLocker inschakelen**.|  

##### <a name="settings"></a>Instellingen  
|**Naam**|**Beschrijving**|  
|-|-|  
|**Huidig besturingssysteemstation**|Wanneer u selecteert, wordt het systeemstation worden geconfigureerd. Dit is standaard geselecteerd.|  
|**Specifiek station**|Wanneer u selecteert, wordt het opgegeven station worden geconfigureerd.|  
|**Alleen TPM**|Wanneer u selecteert, wordt de Trusted Platform Module (TPM) is vereist. Dit is standaard geselecteerd.|  
|**Alleen een opstartsleutel op USB**|Wanneer u selecteert, wordt een opstartsleutel is vereist op de gespecificeerde USB-station.|  
|**TPM en starten van de sleutel op USB**|Wanneer u selecteert, wordt de TPM is vereist naast een opstartsleutel op de gespecificeerde USB-station.|  
|**In Active Directory**|Wanneer u selecteert, wordt de herstelsleutel opgeslagen in AD DS. Dit is standaard geselecteerd.|  
|**Maak een herstelsleutel geen**|Wanneer u selecteert, wordt de herstelsleutel niet gemaakt. Gebruik deze optie wordt niet aanbevolen.|  
|**Wacht totdat BitLocker te voltooien**|Wanneer u selecteert, wordt deze stap niet voltooien totdat nadat de verwerking van alle stations van BitLocker is voltooid.|  

####  <a name="ExecuteRunbook"></a>Uitvoeren van Runbook  
 Deze takenreeksstap wordt uitgevoerd van Microsoft System Center 2012 Orchestrator-runbooks op de doelcomputer. Een Orchestrator *runbook* is de volgorde van activiteiten die acties op computers en netwerken te organiseren. In dit type takenreeks stap met MDT kunt u de Orchestrator-runbooks starten.  

> [!NOTE]
>  Deze takenreeksstap is niet opgenomen MDT taak reeks sjablonen. U moet deze takenreeksstap toevoegen aan takenreeksen die u maakt.  

 De unieke eigenschappen en instellingen voor de **Runbook uitvoeren** stap takenreekstype zijn:  

##### <a name="properties"></a>Eigenschappen  
|**Naam**|**Beschrijving**|  
|-|-|  
|**Type**|Dit type alleen-lezen wordt ingesteld op **Runbook uitvoeren**.|  
|**Naam**|De naam van de takenreeksstap die moet overeenkomen met de naam van het runbook wordt uitgevoerd.|  
|**Beschrijving**|Informatieve tekst met aanvullende informatie over de takenreeksstap|  

##### <a name="settings"></a>Instellingen  
|**Naam**|**Beschrijving**|  
|-|-|   
|**Orchestrator-Server**|Typ de URL voor de Orchestrator-webservice, waaronder de naam van de server. De Orchestrator-webservice kunt Hypertext Transfer Protocol (HTTP) of HTTP via Secure Sockets Layer (HTTPS). De Orchestrator-webservice wordt standaard ingesteld op poort 81.<br /><br /> De Orchestrator-webservice ondersteunt meerdere runbook-servers. Standaard kan een runbook uitgevoerd op een runbook-server. Een runbook kan worden geconfigureerd om op te geven welke runbook-servers moeten worden gebruikt voor het uitvoeren van het runbook.<br /><br /> Opmerking:<br /><br /> De Orchestrator-webservice ondersteunt de mogelijkheid voor het uitvoeren van een runbook op een specifiek runbook-server. Deze functie wordt niet ondersteund in MDT.<br /><br /> Geef de URL in een van de volgende indelingen:<br /><br /> - ***ServerName***. Wanneer u deze indeling gebruikt, wordt de URL wordt standaard ingesteld op:<br /><br /> `http://<servername>:81/Orchestrator2012/Orchestrator.svc`<br /><br /> - ***servernaam: poort***. Wanneer u deze indeling gebruikt, wordt de URL wordt standaard ingesteld op:<br /><br /> `http://<servername:port>/Orchestrator2012/Orchestrator.svc.`<br /><br /> -**http://*servername:port***. Wanneer u deze indeling gebruikt, wordt de URL wordt standaard ingesteld op:<br /><br /> `http://<servername:port>/Orchestrator2012/Orchestrator.svc.`<br /><br /> -**http://*servername:port***. Wanneer u deze indeling gebruikt, wordt de URL wordt standaard ingesteld op:<br /><br /> `https://<servername:port>/Orchestrator2012/Orchestrator.svc.`<br /><br /> - **http://*servernaam: poort*/Orchestrator2012/Orchestrator.svc**. Wanneer u deze indeling, MDT wordt ervan uitgegaan dat u de volledige URL opgeeft omdat de waarde op .svc eindigt.<br /><br /> -                                 **https://*servernaam: poort*/Orchestrator2012/Orchestrator.svc**. Wanneer u deze indeling, MDT wordt ervan uitgegaan dat u de volledige URL opgeeft omdat de waarde op .svc eindigt.|  
|**Runbook**|Klik op **Bladeren**, en selecteer vervolgens de naam van de Orchestrator-runbook die deze takenreeks moet worden uitgevoerd.<br /><br /> Opmerking:<br /><br /> Om te kunnen bladeren voor Orchestrator-runbooks, installeert u de [ADO.NET Data Services Update voor .NET Framework 3.5 SP1 voor Windows 7 en Windows Server 2008 R2](http://www.microsoft.com/download/details.aspx?displaylang=en&id=2343).|  
|**Automatisch bieden runbook-parameters**|Selecteer deze optie automatisch de Orchestrator runbook invoerparameter om waarden te leveren (die wordt ervan uitgegaan dat de waarden van de parameter runbook takenreeksvariabelen zijn). Bijvoorbeeld, als een runbook heeft een invoerparameter **OSDComputerName**, wordt de **OSDComputerName** waarde wordt doorgegeven aan het runbook.<br /><br /> Opmerking:<br /><br /> Deze optie werkt alleen voor de invoerparameters die geldige namen van takenreeksvariabelen zijn en geen spaties of andere speciale tekens bevatten. Hoewel spaties en andere speciale tekens worden ondersteund als namen van de Orchestrator-parameters, maar ze zijn geen geldige namen van takenreeksvariabelen. Als u waarden doorgeven aan de parameters met spaties of andere speciale tekens moet, gebruikt u de **expliciete runbookparameters opgeven** optie.<br /><br /> De andere mogelijkheid is **expliciete runbookparameters opgeven**.<br /><br /> Opmerking:<br /><br /> De waarden voor de invoerparameters van runbook met de Orchestrator-webservice worden opgemaakt als XML. Waarden die gegevens bevatten die lijkt op de gegevens in XML-indeling of wordt doorgegeven, kan fouten veroorzaken.|  
|**Expliciete runbookparameters opgeven**|Selecteer deze optie als u expliciet de Orchestrator runbook-invoerparameters.<br /><br /> U moet de volgende instellingen voor elke invoerparameter die vereist dat de Orchestrator-runbook configureren:<br /><br /> -                                 **Naam**. Dit is de naam van de invoer runbook-parameter.<br /><br /> Opmerking:<br /><br /> Als u de parameters voor een bestaande Orchestrator-runbook wijzigt, moet u opnieuw (opnieuw) bladeren voor het runbook omdat MDT worden alleen de lijst met parameters haalt bij het toevoegen van de Orchestrator-runbook in eerste instantie.<br /><br /> - **Waarde**. Dit is een constante zijn of een variabele, zoals een takenreeksvariabele of een omgevingsvariabele. Bijvoorbeeld, kunt u een waarde van **% OSDComputerName %**, waarmee wordt doorgeven dat de waarde van de **OSDComputerName** takenreeksvariabele aan de runbook-invoerparameter.|  
|**Wacht totdat het runbook te voltooien voordat u doorgaat**|Dit selectievakje bepaalt of de takenreeksstap voor het runbook wachten moet te voltooien voordat u doorgaat naar de volgende takenreeksstap.<br /><br /> Als dit selectievakje is:<br /><br /> - **Geselecteerd**, en vervolgens de takenreeksstap voor het runbook wachten moet te voltooien voordat u doorgaat naar de volgende takenreeksstap.<br /><br /> Wanneer dit selectievakje is ingeschakeld, wordt de takenreeksstap pollen van de Orchestrator-webservice voor de runbook om te voltooien. De hoeveelheid tijd tussen polls begint bij 1 seconde en vervolgens wordt verhoogd naar 2, 4, 8, 16, 32 en 64 seconden tussen de verschillende. Zodra de hoeveelheid tijd 64 seconden bereikt, de takenreeksstap voortgezet voor het pollen van elke 64 seconden.<br /><br /> - **Gewist**, en vervolgens de takenreeksstap niet totdat het runbook wachten wordt te voltooien voordat u doorgaat naar de volgende takenreeksstap.<br /><br /> Opmerking:<br /><br /> Dit selectievakje moet worden geselecteerd als het runbook output-parameters retourneert.|  

#### <a name="format-and-partition-disk"></a>Schijf formatteren en partitioneren  
 Deze taak sequence stap partities ingedeeld en geformatteerd schijven op de doelcomputer. Zie voor meer informatie over dit staptype [schijf formatteren en partitioneren](http://technet.microsoft.com/library/bb680345.aspx).  

 De unieke eigenschappen en instellingen voor de **schijf formatteren en partitioneren** stap takenreekstype zijn:  

##### <a name="properties"></a>Eigenschappen  
|**Naam**|**Beschrijving**|  
|-|-|  
|**Type**|Dit type alleen-lezen wordt ingesteld op **schijf formatteren en partitioneren**.|  

##### <a name="settings"></a>Instellingen  
|**Naam**|**Beschrijving**|  
|-|-|  
|**Schijfnummer**|Het fysieke nummer van de schijf moet worden geconfigureerd.|  
|**Schijftype**|Het type station moet worden gemaakt. Waarden zijn:<br /><br /> -                                 **Standaard (MBR)** (Master Boot Record)<br /><br /> - **GPT** ([globaal unieke id] GUID-partitietabel).<br /><br /> De standaardselectie is **standaard (MBR)**.|  
|**Volume**|Binnen de **Volume** instelt, kunnen de volgende onderliggende instellingen worden geconfigureerd:<br /><br /> -Partitie **naam**. De naam van een gebruiker te definiëren.<br /><br /> - **Type van de partitie.** Waarden verschillen per schijftype:<br /><br /> -MBR: **Primaire** alleen<br /><br /> -GPT: **Primaire**, **EFI**, of **MSR**<br /><br /> - **Gebruik een percentage van de resterende ruimte.**<br /><br /> -                                 **Grootte van een specifiek station gebruiken.** Waarden zijn in stappen van 1 MB of 1 gigabyte (GB).<br /><br /> -                                 **Maak hiervan een opstartpartitie.**<br /><br /> -                                 **Bestandssysteem.** Waarden zijn **NTFS** of **FAT32**.<br /><br /> - **Snelle formattering.** Wanneer u selecteert, wordt een snelle formattering uitgevoerd.<br /><br /> - **Variabele.** De stationsletter die is toegewezen aan deze nieuwe geconfigureerde partitie.|  

> [!NOTE]
>  Wanneer u het CustomSettings.ini-bestand op de harde schijf en partitie configuraties op te geven, worden alleen de eerste harde schijf en eerst twee partities worden geconfigureerd. Bewerk ZTIGather.xml extra harde schijven of partities wilt configureren.  

#### <a name="gather"></a>Verzamelen  
 Deze takenreeksstap verzamelt gegevens en verwerken van regels voor de doelcomputer. De unieke eigenschappen en instellingen voor de **verzamelen** stap takenreekstype zijn:  

##### <a name="properties"></a>Eigenschappen  
|**Naam**|**Beschrijving**|  
|-|-|  
|**Type**|Stel deze lezen\-alleen type **verzamelen**.|  

##### <a name="settings"></a>Instellingen  
|**Naam**|**Beschrijving**|  
|-|-|  
|**Alleen lokale gegevens verzamelen**|Wanneer geselecteerd, wordt in deze stap alleen de eigenschappen die zijn opgenomen in het bestand ZTIGather.xml verwerkt.|  
|**Lokale gegevens verzamelen en verwerken van regels**|Wanneer u selecteert, wordt deze stap verwerkt de eigenschappen in het bestand ZTIGather.xml en de eigenschappen in het bestand dat het regelbestand opgeeft. Dit is standaard geselecteerd.|  
|**Regelbestand**|De naam van het bestand regels worden verwerkt. Als dit leeg laat, wordt de takenreeksstap probeert om te zoeken en verwerken van het CustomSettings.ini-bestand.|  

> [!NOTE]
>  Deze takenreeksstap is standaard beschikbaar in System Center 2012 R2 Configuration Manager als **dynamische variabelen instellen**in de groep Algemeen.  

####  <a name="InjectDrivers"></a>Stuurprogramma's invoeren  
 Deze takenreeksstap injects stuurprogramma's die zijn geconfigureerd voor de implementatie van de doelcomputer. De unieke eigenschappen en instellingen voor de **stuurprogramma's invoeren** stap takenreekstype zijn:  

##### <a name="properties"></a>Eigenschappen  
|**Naam**|**Beschrijving**|  
|-|-|  
|**Type**|Stel deze lezen\-alleen type **stuurprogramma's invoeren**.|  

##### <a name="settings"></a>Instellingen  
|**Naam**|**Beschrijving**|  
|-|-|   
|**Alleen overeenkomende stuurprogramma's installeren**|Alleen de stuurprogramma's die de doelcomputer vereist en die overeenkomen met wat is beschikbaar in uit injects\-van\-Box stuurprogramma's|  
|**Alle stuurprogramma's installeren**|Alle stuurprogramma's worden geïnstalleerd|  
|**Selectie profiel**|Alle stuurprogramma's in het geselecteerde profiel geïnstalleerd|  

#### <a name="install-application"></a>Toepassing installeren  
 Deze takenreeksstap installeert toepassingen op de doelcomputer. Zie voor meer informatie over dit staptype [Software installeren](http://technet.microsoft.com/library/bb680842.aspx).  

 De unieke eigenschappen en instellingen voor de **toepassing installeren** stap takenreekstype zijn:  

##### <a name="properties"></a>Eigenschappen  
|**Naam**|**Beschrijving**|  
|-|-|   
|**Type**|Stel deze lezen\-alleen type **toepassing installeren**.|  

##### <a name="settings"></a>Instellingen  
|**Naam**|**Beschrijving**|  
|-|-|  
|**Meerdere toepassingen installeren**|Verplichte toepassingen installeren die de **MandatoryApplications** eigenschap is opgegeven en optionele toepassingen die de **toepassingen** eigenschap is opgegeven. Deze eigenschappen zijn geconfigureerd door regels of zijn opgegeven tijdens het gesprek implementatiewizard. Dit is standaard geselecteerd.|  
|**Installeren van één toepassing**|De specifieke toepassing te installeren. Selecteer van de toepassing in een vervolgkeuzelijst\-omlaag in de lijst die bestaat uit toepassingen die zijn geconfigureerd in het knooppunt toepassingen van de implementatie-Workbench.|  
|**Geslaagd-codes**|Een spatie\-gescheiden lijst van de toepassing installatie afsluitcodes die moeten worden gebruikt bij het bepalen van de geslaagde installatie van toepassingen.|  

#### <a name="install-operating-system"></a>Besturingssysteem installeren  
 Deze takenreeksstap installeert een besturingssysteem op de doelcomputer. MDT kunt implementeren voor Windows 8.1, Windows 8, Windows 7, Windows Server 2012 R2, Windows Server 2012 en Windows Server 2008 R2 met behulp van:  

-   **Setup.exe**. Dit is de traditionele methode gebruikt, door het uitvoeren van setup.exe vanaf de installatiemedia gestart. MDT maakt standaard gebruik van setup.exe.  

-   **ImageX.exe**. Deze methode installeert de installatiekopie van het besturingssysteem imagex.exe met behulp van de  **\/toepassen** optie. MDT maakt gebruik van deze methode wanneer de setup.exe-methode kan niet worden gebruikt \(dat wil zeggen, het terugvalt op het gebruik van imagex.exe\).  

 U kunt bepalen welke van deze methoden wordt gebruikt met behulp van de **ForceApplyFallback** eigenschap, die ook van invloed op de takenreeksen van welke besturingssystemen worden vermeld in de Wizard implementatie voor de installatiekopie van een specifieke processor-architectuur. Zie voor meer informatie de [ForceApplyFallback](#ForceApplyFallback) eigenschap.  

 De unieke eigenschappen en instellingen voor de **besturingssysteem installeren** stap takenreekstype zijn:  

##### <a name="properties"></a>Eigenschappen  
|**Naam**|**Beschrijving**|  
|-|-|   
|**Type**|Stel deze lezen\-alleen type **besturingssysteem installeren**.|  

##### <a name="settings"></a>Instellingen  
|**Naam**|**Beschrijving**|  
|-|-|   
|**Besturingssysteem installeren**|De naam van het besturingssysteem op de doelcomputer zijn geïnstalleerd. Selecteer van het besturingssysteem in een vervolgkeuzelijst\-lijst van besturingssystemen die zijn geconfigureerd in het knooppunt besturingssystemen van de implementatie-Workbench is gecompileerd.|  
|**Schijf**|De schijf waarop het besturingssysteem installeren.|  
|**Partitie**|De partitie waarop het besturingssysteem installeren.|  

####  <a name="InstallRolesandFeatures"></a>Functies en onderdelen installeren  
 Deze takenreeksstap installeert de geselecteerde rollen en functies op de doelcomputer. Voor meer informatie over welke script bewerkstelligt deze taak en de eigenschappen die worden gebruikt, Zie [ZTIOSRole.wsf](#ZTIOSRole.wsf).  

 De unieke eigenschappen en instellingen voor de **Installeer functies en onderdelen** stap takenreekstype zijn:  

##### <a name="properties"></a>Eigenschappen  
|**Naam**|**Beschrijving**|  
|-|-|  
|**Type**|Stel deze lezen\-alleen type **Installeer functies en onderdelen**.|  
|**Beschrijving**|Informatieve tekst die het doel van de takenreeksstap beschrijft.|  

##### <a name="settings"></a>Instellingen  
|**Naam**|**Beschrijving**|  
|-|-|    
|**Selecteer het besturingssysteem waarvoor de rollen worden geïnstalleerd**|Selecteer het besturingssysteem op de doelcomputer kunnen worden geïmplementeerd.|  
|**Selecteer de functies en onderdelen die moeten worden geïnstalleerd**|Selecteer een of meer functies en onderdelen voor installatie op de doelcomputer.|  

#### <a name="install-language-packs-offline"></a>Taalpakketten Offline installeren  
 Deze takenreeksstap worden updates geïnstalleerd op de installatiekopie op de doelcomputer nadat het besturingssysteem is geïmplementeerd, maar voordat het doel een computer is opnieuw opgestart. Deze updates bevatten taalpakketten. Voor meer informatie over welke script voert deze taak en welke eigenschappen u gebruikt, Zie [ZTIPatches.wsf](#ZTIPatches.wsf).  

 De unieke eigenschappen en instellingen voor de **taalpakketten Offline installeren** stap takenreekstype zijn:  

##### <a name="properties"></a>Eigenschappen  
|**Naam**|**Beschrijving**|  
|-|-|  
|**Type**|Stel deze lezen\-alleen type **Offline Updates installeren**.|  

##### <a name="settings"></a>Instellingen  
|**Naam**|**Beschrijving**|  
|-|-|  
|**Naam van het pakket**|De naam van het language pack-pakket dat moet worden toegepast op de doelcomputer|  

> [!NOTE]
>  Deze takenreeksstap is alleen geldig wanneer met behulp van MDT met Configuration Manager.  

#### <a name="install-language-packs-online"></a>Online taalpakketten installeren  
 Deze takenreeksstap installeert taalpakketten op de installatiekopie op de doelcomputer nadat het besturingssysteem is geïmplementeerd en de doelcomputer opnieuw is gestart. Voor meer informatie over welke script voert deze taak en welke eigenschappen u gebruikt, Zie [ZTILangPacksOnline.wsf](#ZTILangPacksOnline.wsf).  

 De unieke eigenschappen en instellingen voor de **Language Packs Online installeren** stap takenreekstype zijn:  

##### <a name="properties"></a>Eigenschappen  
|**Naam**|**Beschrijving**|  
|-|-|  
|**Type**|Stel deze lezen\-alleen type **Language Packs Online installeren**.|  

##### <a name="settings"></a>Instellingen  
|**Naam**|**Beschrijving**|  
|-|-|  
|**Naam van het pakket**|De naam van het language pack-pakket dat moet worden toegepast op de doelcomputer|  

> [!NOTE]
>  Deze takenreeksstap is alleen geldig wanneer met behulp van MDT met Configuration Manager.  

#### <a name="install-updates-offline"></a>Offline-Updates installeren  
 Deze takenreeksstap worden updates geïnstalleerd op de installatiekopie op de doelcomputer nadat het besturingssysteem is geïmplementeerd, maar voordat het doel een computer is opnieuw opgestart. Deze updates bevatten taalpakketten. Voor meer informatie over welke script voert deze taak en welke eigenschappen u gebruikt, Zie [ZTIPatches.wsf](#ZTIPatches.wsf).  

 De unieke eigenschappen en instellingen voor de **Offline Updates installeren** stap takenreekstype zijn:  

##### <a name="properties"></a>Eigenschappen  
|**Naam**|**Beschrijving**|  
|-|-|  
|**Type**|Stel deze lezen\-alleen type **Offline Updates installeren**.|  

##### <a name="settings"></a>Instellingen  
|**Naam**|**Beschrijving**|  
|-|-|  
|**Selectie profiel**|De naam van de selectie-profiel dat moet worden toegepast op de doelcomputer<br /><br /> Opmerking:<br /><br /> Wanneer u MDT met Configuration Manager gebruikt, geef de naam van het updatepakket dat moet worden toegepast.|  

#### <a name="recover-from-domain-join-failure"></a>Herstellen van fouten van domein koppelen  
 Deze takenreeksstap wordt gecontroleerd of de doelcomputer de lid is van een domein. De unieke eigenschappen en instellingen voor de **herstellen van fouten voor domein deelnemen aan** stap takenreekstype zijn:  

##### <a name="properties"></a>Eigenschappen  
|**Naam**|**Beschrijving**|  
|-|-|  
|**Type**|Stel deze lezen\-alleen herstellen van type **Domain Join fout**.|  

##### <a name="settings"></a>Instellingen  
|**Naam**|**Beschrijving**|  
|-|-|  
|**Automatisch herstellen**|De takenreeksstap probeert de doelcomputer koppelen aan een domein.|  
|**Handmatige herstellen**|Als de doelcomputer niet lid worden van een domein, de takenreeksstap zorgt ervoor dat de Sequencer taak onderbreken, zodat u kunt proberen de doelcomputer koppelen aan een domein.|  
|**Er is geen herstellen**|Als de doelcomputer niet aan een domein is, mislukt de takenreeks wordt uitgevoerd, stoppen van de takenreeks.|  

#### <a name="restart-computer"></a>Computer opnieuw opstarten  
 Deze takenreeksstap start opnieuw op de doelcomputer. De unieke eigenschappen en instellingen voor de **computer opnieuw opstarten** stap takenreekstype zijn:  

##### <a name="properties"></a>Eigenschappen  
|**Naam**|**Beschrijving**|  
|-|-|  
|**Type**|Stel deze lezen\-alleen type **computer opnieuw opstarten**.|  

##### <a name="settings"></a>Instellingen  
|**Naam**|**Beschrijving**|  
|-|-|  
|**Geen**|Geen|  

#### <a name="run-command-line"></a>Opdrachtregel uitvoeren  
 Deze takenreeksstap voert de opgegeven opdrachten op de doelcomputer. Zie voor meer informatie over dit staptype [opdrachtregel uitvoeren](http://technet.microsoft.com/library/bb632992.aspx).  

 De unieke eigenschappen en instellingen voor de **opdrachtregel uitvoeren** stap takenreekstype zijn:  

##### <a name="properties"></a>Eigenschappen  
|**Naam**|**Beschrijving**|  
|-|-|  
|**Type**|Stel deze lezen\-alleen type **opdrachtregel uitvoeren**.|  

##### <a name="settings"></a>Instellingen  
|**Naam**|**Beschrijving**|  
|-|-|  
|**Vanaf de opdrachtregel**|De opdrachten worden uitgevoerd wanneer deze takenreeksstap wordt verwerkt|  
|**Beginnen in**|De startmap voor de toepassing \(het pad moet een geldig pad op de doelcomputer.\)|  
|**Deze stap uitvoeren als de volgende account**|Kan worden opgegeven van de gebruikersreferenties die worden gebruikt voor het uitvoeren van de opgegeven opdracht|  
|**Account**|De referenties van de gebruiker die wordt gebruikt voor het uitvoeren van de opgegeven opdracht|  
|**Het gebruikersprofiel laden**|Wanneer u selecteert, laadt het gebruikersprofiel voor het opgegeven account|  

#### <a name="run-powershell-script"></a>PowerShell-script uitvoeren  
 Deze takenreeksstap wordt het opgegeven Windows PowerShell™ script uitgevoerd op de doelcomputer. Zie voor meer informatie over welke script bewerkstelligt deze taak en welke eigenschappen worden gebruikt, [ZTIPowerShell.wsf](#ZTIPowerShell.wsf).  

 De unieke eigenschappen en instellingen voor de **PowerShell-Script uitvoeren** stap takenreekstype zijn:  

##### <a name="properties"></a>Eigenschappen  
|**Naam**|**Beschrijving**|  
|-|-|  
|**Type**|Stel deze lezen\-alleen type **PowerShell-Script uitvoeren**.|  

##### <a name="settings"></a>Instellingen  
|**Naam**|**Beschrijving**|  
|-|-|  
|**PowerShell-script**|De Windows PowerShell-script wordt uitgevoerd als deze takenreeksstap wordt verwerkt|  
|Parameters|De parameters worden doorgegeven aan de Windows PowerShell-script. Deze parameters moeten worden opgegeven hetzelfde als wanneer u deze aan de Windows PowerShell-script vanaf een opdrachtregel toevoegt.<br /><br /> De opgegeven parameters moet alleen de parameters die het script wordt verbruikt, niet voor de Windows PowerShell-opdrachtregel.<br /><br /> Het volgende voorbeeld zou een geldige waarde voor deze instelling zijn:<br /><br /> `-MyParameter1 MyValue1 -MyParameter2 MyValue2`<br /><br /> Het volgende voorbeeld is een ongeldige waarde voor deze instelling \(vette items zijn onjuist\):<br /><br /> `-nologo -executionpolicy unrestricted -File MyScript.ps1 -MyParameter1 MyValue1 -MyParameter2 MyValue2`<br /><br /> Het vorige voorbeeld is ongeldig, omdat de waarde Windows PowerShell-opdracht bevat\-regel parameters \(  **\-nologo** en **-executionpolicy unrestricted**\).|  

> [!NOTE]
>  Deze takenreeksstap is standaard beschikbaar in System Center 2012 R2 Configuration Manager als **PowerShell-Script uitvoeren** in de groep Algemeen.  

#### <a name="set-task-sequence-variable"></a>Takenreeksvariabele instellen  
 Deze takenreeksstap wordt de opgegeven takenreeksvariabele ingesteld op de opgegeven waarde. Zie voor meer informatie over dit staptype [Takenreeksvariabele instellen](http://technet.microsoft.com/library/bb694306.aspx).  

 De unieke eigenschappen en instellingen voor de **Takenreeksvariabele instellen** stap takenreekstype zijn:  

##### <a name="properties"></a>Eigenschappen  
|**Naam**|**Beschrijving**|  
|-|-|  
|**Type**|Stel deze lezen\-alleen type **Takenreeksvariabele instellen**.|  

##### <a name="settings"></a>Instellingen  
|**Naam**|**Beschrijving**|  
|-|-|  
|**Takenreeksvariabele**|De naam van de variabele te wijzigen|  
|**Waarde**|De waarde toewijzen aan de opgegeven variabele|  

####  <a name="UninstallRolesandFeatures"></a>Functies en onderdelen verwijderen  
 Deze takenreeksstap wordt verwijderd van de geselecteerde rollen en functies van de doelcomputer. Voor meer informatie over welke script bewerkstelligt deze taak en de eigenschappen die worden gebruikt, Zie [ZTIOSRole.wsf](#ZTIOSRole.wsf).  

 De unieke eigenschappen en instellingen voor de **verwijderen van functies en onderdelen** stap takenreekstype zijn:  

##### <a name="properties"></a>Eigenschappen  
|**Naam**|**Beschrijving**|  
|-|-|  
|**Type**|Stel deze lezen\-alleen type **verwijderen van functies en onderdelen**.|  
|**Beschrijving**|Informatieve tekst die het doel van de takenreeksstap beschrijft.|  

##### <a name="settings"></a>Instellingen  
|**Naam**|**Beschrijving**|  
|-|-|  
|**Selecteer het besturingssysteem waarvoor de rollen worden geïnstalleerd**|Selecteer het besturingssysteem op de doelcomputer kunnen worden geïmplementeerd.|  
|**Selecteer de functies en onderdelen die moeten worden geïnstalleerd**|Selecteer een of meer rollen en functies voor unstallation van de doelcomputer.|  

#### <a name="validate"></a>valideren  
 Deze takenreeksstap wordt gecontroleerd of de doelcomputer voldoet aan de gespecificeerde implementatievereistevoorwaarden. De unieke eigenschappen en instellingen voor de **valideren** stap takenreekstype zijn:  

##### <a name="properties"></a>Eigenschappen  
|**Naam**|**Beschrijving**|  
|-|-|  
|**Type**|Stel deze lezen\-alleen type **valideren**.|  

##### <a name="settings"></a>Instellingen  
|**Naam**|**Beschrijving**|  
|-|-|  
|**Minimumgeheugen garanderen**|Wanneer u selecteert, wordt deze stap verifieert dat de hoeveelheid geheugen in megabytes geïnstalleerd op de doel-computer voldoet aan of groter is dan de opgegeven waarde. Dit is een standaard geselecteerd.|  
|**Minimale processorsnelheid garanderen**|Wanneer u selecteert, deze stap wordt gecontroleerd of de snelheid van de processor, in megahertz \(MHz\), geïnstalleerd in de doel-computer voldoet aan of groter is dan de opgegeven waarde. Dit is een standaard geselecteerd.|  
|**Zorg ervoor dat de grootte van de opgegeven installatiekopie past**|Wanneer u selecteert, wordt deze stap verifieert of de hoeveelheid vrije schijfruimte in MB op de doelcomputer voldoet aan de opgegeven waarde.|  
|**Zorg ervoor dat de huidige besturingssysteem worden vernieuwd**|Wanneer u selecteert, wordt deze stap controleert of dat het besturingssysteem geïnstalleerd op de doelcomputer voldoet aan de vereisten die zijn opgegeven. Dit is een standaard geselecteerd.|  

> [!NOTE]
>  Deze takenreeksstap is standaard beschikbaar in System Center 2012 R2 Configuration Manager als **gereedheid controleren** in de groep Algemeen.  

### <a name="out-of-box-task-sequence-steps"></a>Uitgaand\-van\-Takenreeksstappen vak  
 De volgende takenreeksstappen wordt verwezen door een of meer van de beschikbare taak reeks sjablonen met MDT. Elk van de volgende voorbeelden ziet u de vooraf geconfigureerde eigenschappen, parameters en opties en kan worden gebruikt als basis voor het bouwen van aangepaste takenreeksen.  

 Alleen de stap takenreekseigenschappen, parameters en opties en de bijbehorende waarden worden weergegeven in de voorbeelden.  

> [!NOTE]
>  Zie voor meer informatie over elke stap van de takenreeks, de corresponderende onderwerpen in [algemene eigenschappen en opties voor taaktypen Sequence stap](#CommonPropertiesandOptionsforTaskSequenceStepTypes) en [specifieke eigenschappen en instellingen voor de reeks stap taaktypen](#SpecificPropertiesandSettingsforTaskSequenceStepTypes).  

#### <a name="apply-network-settings"></a>Netwerkinstellingen toepassen  
 Deze takenreeksstap configureert u de netwerkadapter op de doelcomputer. Hier volgt een kort overzicht van de instellingen die laten zien hoe deze stap oorspronkelijk is geconfigureerd in een van de MDT taak reeks sjablonen. Zie voor meer informatie over welke script voert deze taak en welke eigenschappen worden gebruikt, [ZTINICConfig.wsf](#ZTINICConfig.wsf).  

 De standaardconfiguratie van de **netwerkinstellingen toepassen** takenreeksstap is:  

##### <a name="properties"></a>Eigenschappen  
|**Naam**|**Waarde**|  
|-|-|  
|**Type**|Netwerkinstellingen toepassen|  
|**Naam**|Netwerkinstellingen toepassen|  
|**Beschrijving**|Niet opgegeven|  

##### <a name="settings"></a>Instellingen  
|**Naam**|**Waarde**|  
|-|-|  
||Er zijn geen parameters zijn vooraf geconfigureerd voor deze stap. Dit zorgt ervoor dat deze stap wordt standaard voor het configureren van de netwerkadapter voor gebruik van DHCP.|  

##### <a name="options"></a>Opties  
|**Naam**|**Waarde**|  
|-|-|  
|**Deze stap uitschakelen**|Geen geselecteerd|  
|**Geslaagd-codes**|3010 0|  
|**Doorgaan bij fout**|Geen geselecteerd|  
|**Voorwaardelijke kwalificatie**|Niet opgegeven|  

> [!NOTE]
>  Als u het CustomSettings.ini-bestand voor de netwerkadapterconfiguraties opgeven, kunt u alleen de eerste netwerkadapter wordt geconfigureerd. Bewerk ZTIGather.xml voor het configureren van extra netwerkadapters.  

#### <a name="apply-patches"></a>Patches toepassen  
 Deze takenreeksstap worden updates geïnstalleerd op de installatiekopie op de doelcomputer nadat het besturingssysteem is geïmplementeerd, maar voordat het doel een computer is opnieuw opgestart. Hier volgt een kort overzicht van de instellingen die laten zien hoe deze stap oorspronkelijk is geconfigureerd in een van de MDT taak reeks sjablonen. Voor meer informatie over welke script voert deze taak en welke eigenschappen u gebruikt, Zie [ZTIPatches.wsf](#ZTIPatches.wsf).  

 De standaardconfiguratie van de **Offline Updates installeren** takenreeksstap is:  

##### <a name="properties"></a>Eigenschappen  
|**Naam**|**Waarde**|  
|-|-|  
|**Type**|Offline-Updates installeren|  
|**Naam**|Patches toepassen|  
|**Beschrijving**|Niet opgegeven|  

##### <a name="settings"></a>Instellingen  
|**Naam**|**Waarde**|  
|-|-|  
|**Selectie profiel**|De naam van het profiel wordt gebruikt bij het selecteren van de patches te installeren op de doelcomputer|  

##### <a name="options"></a>Opties  
|**Naam**|**Waarde**|  
|-|-|  
|**Deze stap uitschakelen**|Geen geselecteerd|  
|**Geslaagd-codes**|3010 0|  
|**Doorgaan bij fout**|Geen geselecteerd|  
|**Voorwaardelijke kwalificatie**|Niet opgegeven|  

#### <a name="apply-windows-pe"></a>Windows PE toepassen  
 Deze takenreeksstap wordt voorbereid voor de doelcomputer te starten in Windows Preinstallation Environment \(Windows PE\). Hier volgt een kort overzicht van de instellingen die laten zien hoe deze stap oorspronkelijk is geconfigureerd in een van de MDT taak reeks sjablonen. Voor meer informatie over welke script voert deze taak en welke eigenschappen u gebruikt, Zie [LTIApply.wsf](#LTIApply.wsf).  

 De standaardconfiguratie van de **toepassen op Windows PE** takenreeksstap is:  

##### <a name="properties"></a>Eigenschappen  
|**Naam**|**Waarde**|  
|-|-|  
|**Type**|Opdrachtregel uitvoeren|  
|**Naam**|Windows PE toepassen|  
|**Beschrijving**|Niet opgegeven|  

##### <a name="settings"></a>Instellingen  
|**Naam**|**Waarde**|  
|-|-|  
|**Vanaf de opdrachtregel**|`cscript.exe "%SCRIPTROOT%\LTIApply.wsf" /PE`|  
|**Beginnen in**|Niet opgegeven|  
|**Deze stap uitvoeren als de volgende account**|Niet opgegeven|  

##### <a name="options"></a>Opties  
|**Naam**|**Waarde**|  
|-|-|  
|**Deze stap uitschakelen**|Geen geselecteerd|  
|**Geslaagd-codes**|3010 0|  
|**Doorgaan bij fout**|Geen geselecteerd|  
|**Voorwaardelijke kwalificatie**|Niet opgegeven|  

#### <a name="backup"></a>Back-up  
 Deze takenreeksstap back-ups van de doelcomputer voordat de implementatie van het besturingssysteem wordt gestart. Hier volgt een kort overzicht van de instellingen die laten zien hoe deze stap oorspronkelijk is geconfigureerd in een van de MDT taak reeks sjablonen. Voor meer informatie over welke script voert deze taak en welke eigenschappen u gebruikt, Zie [ZTIBackup.wsf](#ZTIBackup.wsf).  

 De standaardconfiguratie van de **back-up** takenreeksstap is:  

##### <a name="properties"></a>Eigenschappen  
|**Naam**|**Waarde**|  
|-|-|  
|**Type**|Opdrachtregel uitvoeren|  
|**Naam**|Back-up|  
|**Beschrijving**|Niet opgegeven|  

##### <a name="settings"></a>Instellingen  
|**Naam**|**Waarde**|  
|-|-|  
|**Vanaf de opdrachtregel**|`cscript.exe "%SCRIPTROOT%\ZTIBackup.wsf"`|  
|**Beginnen in**|Niet opgegeven|  
|**Deze stap uitvoeren als de volgende account**|Niet opgegeven|  

##### <a name="options"></a>Opties  
|**Naam**|**Waarde**|  
|-|-|  
|**Deze stap uitschakelen**|Geen geselecteerd|  
|**Geslaagd-codes**|3010 0|  
|**Doorgaan bij fout**|Geen geselecteerd|  
|**Voorwaardelijke kwalificatie**|Niet opgegeven|  

#### <a name="capture-groups"></a>Vastleggen van groepen  
 Deze takenreeksstap wordt het lidmaatschap van lokale groepen die bestaan op de doelcomputer vastgelegd. Hier volgt een kort overzicht van de instellingen die laten zien hoe deze stap oorspronkelijk is geconfigureerd in een van de MDT taak reeks sjablonen. Voor meer informatie over welke script voert deze taak en welke eigenschappen u gebruikt, Zie [ZTIGroups.wsf](#ZTIGroups.wsf).  

 De standaardconfiguratie van de **groepen vastleggen** takenreeksstap is:  

##### <a name="properties"></a>Eigenschappen  
|**Naam**|**Waarde**|  
|-|-|  
|**Type**|Opdrachtregel uitvoeren|  
|**Naam**|Vastleggen van groepen|  
|**Beschrijving**|Niet opgegeven|  

##### <a name="settings"></a>Instellingen  
|**Naam**|**Waarde**|  
|-|-|  
|**Vanaf de opdrachtregel**|`cscript.exe "%SCRIPTROOT%\ZTIGroups.wsf" /capture`|  
|**Beginnen in**|Niet opgegeven.|  
|**Deze stap uitvoeren als de volgende account**|Niet opgegeven|  

##### <a name="options"></a>Opties  
|**Naam**|**Waarde**|  
|-|-|  
|**Deze stap uitschakelen**|Geen geselecteerd|  
|**Geslaagd-codes**|3010 0|  
|**Doorgaan bij fout**|Geen geselecteerd|  
|**Voorwaardelijke kwalificatie**|Niet opgegeven|  

#### <a name="capture-user-state"></a>Gebruikersstatus vastleggen  
 Deze takenreeksstap wordt de status van de gebruiker voor gebruikersprofielen die aanwezig zijn op de doelcomputer vastgelegd. Hier volgt een kort overzicht van de instellingen die laten zien hoe deze stap oorspronkelijk is geconfigureerd in een van de MDT taak reeks sjablonen. Zie voor meer informatie over welke script bewerkstelligt deze taak en welke eigenschappen worden gebruikt, [ZTIUserState.wsf](#ZTIUserState.wsf). Zie voor meer informatie over dit staptype [gebruikersstatus vastleggen](http://technet.microsoft.com/library/bb680924.aspx).  

 De standaardconfiguratie van de **gebruikersstatus vastleggen** takenreeksstap is:  

##### <a name="properties"></a>Eigenschappen  
|**Naam**|**Waarde**|  
|-|-|  
|**Type**|Opdrachtregel uitvoeren|  
|**Naam**|Gebruikersstatus vastleggen|  
|**Beschrijving**|Niet opgegeven|  

##### <a name="settings"></a>Instellingen  
|**Naam**|**Waarde**|  
|-|-|  
|**Vanaf de opdrachtregel**|`cscript.exe "%SCRIPTROOT%\ZTIUserState.wsf" /capture`|  
|**Beginnen in**|Niet opgegeven|  
|**Deze stap uitvoeren als de volgende account**|Niet opgegeven|  

##### <a name="options"></a>Opties  
|**Naam**|**Waarde**|  
|-|-|  
|**Deze stap uitschakelen**|Geen geselecteerd|  
|**Geslaagd-codes**|3010 0|  
|**Doorgaan bij fout**|Geen geselecteerd|  
|**Voorwaardelijke kwalificatie**|Niet opgegeven|  

#### <a name="check-bios"></a>BIOS controleren  
 Deze takenreeksstap controleert de basic invoer\/system uitvoer \(BIOS\) van de doelcomputer om ervoor te zorgen dat deze compatibel is met het besturingssysteem die u implementeert. Hier volgt een kort overzicht van de instellingen die laten zien hoe deze stap oorspronkelijk is geconfigureerd in een van de MDT taak reeks sjablonen. Zie voor meer informatie over welke script voert deze taak en welke eigenschappen worden gebruikt, [ZTIBIOSCheck.wsf](#ZTIBIOSCheck.wsf).  

 De standaardconfiguratie van de **BIOS controleren** takenreeksstap is:  

##### <a name="properties"></a>Eigenschappen  
|**Naam**|**Waarde**|  
|-|-|  
|**Type**|Opdrachtregel uitvoeren|  
|**Naam**|BIOS controleren|  
|**Beschrijving**|Niet opgegeven|  

##### <a name="settings"></a>Instellingen  
|**Naam**|**Waarde**|  
|-|-|  
|**Vanaf de opdrachtregel**|`cscript.exe "%SCRIPTROOT%\ZTIBIOSCheck.wsf"`|  
|**Beginnen in**|Niet opgegeven|  
|**Deze stap uitvoeren als de volgende account**|Niet opgegeven|  

##### <a name="options"></a>Opties  
|**Naam**|**Waarde**|  
|-|-|  
|**Deze stap uitschakelen**|Geen geselecteerd|  
|**Geslaagd-codes**|3010 0|  
|**Doorgaan bij fout**|Geen geselecteerd|  
|**Voorwaardelijke kwalificatie**|Niet opgegeven|  

#### <a name="configure"></a>Configureren  
 Deze takenreeksstap configureert het bestand Unattend.XML met de vereiste eigenschapswaarden die van toepassing zijn op het besturingssysteem die u naar de doelcomputer implementeert. Hier volgt een kort overzicht van de instellingen die laten zien hoe deze stap oorspronkelijk is geconfigureerd in een van de MDT taak reeks sjablonen. Voor meer informatie over welke script voert deze taak en welke eigenschappen u gebruikt, Zie [ZTIConfigure.wsf](#ZTIConfigure.wsf).  

 De standaardconfiguratie van de **configureren** takenreeksstap is:  

##### <a name="properties"></a>Eigenschappen  
|**Naam**|**Waarde**|  
|-|-|  
|**Type**|Opdrachtregel uitvoeren|  
|**Naam**|Configureren|  
|**Beschrijving**|Niet opgegeven|  

##### <a name="settings"></a>Instellingen  
|**Naam**|**Waarde**|  
|-|-|  
|**Vanaf de opdrachtregel**|`cscript.exe "%SCRIPTROOT%\ZTIConfigure.wsf"`|  
|**Beginnen in**|Niet opgegeven|  
|**Deze stap uitvoeren als de volgende account**|Niet opgegeven|  

##### <a name="options"></a>Opties  
|**Naam**|**Waarde**|  
|-|-|  
|**Deze stap uitschakelen**|Geen geselecteerd|  
|**Geslaagd-codes**|3010 0|  
|**Doorgaan bij fout**|Geen geselecteerd|  
|**Voorwaardelijke kwalificatie**|Niet opgegeven|  

#### <a name="copy-scripts"></a>Kopiëren van Scripts  
 Deze taak sequence stap exemplaren de implementatiescripts gebruikt tijdens de van implementatieprocessen naar een lokale harde schijf op de doelcomputer. Hier volgt een kort overzicht van de instellingen die laten zien hoe deze stap oorspronkelijk is geconfigureerd in een van de MDT taak reeks sjablonen. Voor meer informatie over welke script voert deze taak en welke eigenschappen u gebruikt, Zie [LTICopyScripts.wsf](#LTICopyScripts.wsf).  

 De standaardconfiguratie van de **kopie Scripts** takenreeksstap is:  

##### <a name="properties"></a>Eigenschappen  
|**Naam**|**Waarde**|  
|-|-|  
|**Type**|Opdrachtregel uitvoeren|  
|**Naam**|Kopiëren van Scripts|  
|**Beschrijving**|Niet opgegeven|  

##### <a name="settings"></a>Instellingen  
|**Naam**|**Waarde**|  
|-|-|  
|**Vanaf de opdrachtregel**|`cscript.exe "%SCRIPTROOT%\LTICopyScripts.wsf"`|  
|**Beginnen in**|Niet opgegeven|  
|**Deze stap uitvoeren als de volgende account**|Niet opgegeven|  

##### <a name="options"></a>Opties  
|**Naam**|**Waarde**|  
|-|-|  
|**Deze stap uitschakelen**|Geen geselecteerd|  
|**Geslaagd-codes**|3010 0|  
|**Doorgaan bij fout**|Geen geselecteerd|  
|**Voorwaardelijke kwalificatie**|Niet opgegeven|  

#### <a name="copy-sysprep-files"></a>Sysprep-bestanden kopiëren  
 Deze takenreeksstap wordt de Sysprep-bestanden naar de doelcomputer gekopieerd. Hier volgt een kort overzicht van de instellingen die laten zien hoe deze stap oorspronkelijk is geconfigureerd in een van de MDT taak reeks sjablonen. Voor meer informatie over welke script voert deze taak en welke eigenschappen u gebruikt, Zie [LTISysprep.wsf](#LTISysprep.wsf).  

 De standaardconfiguratie van de **Sysprep-bestanden kopiëren** takenreeksstap is:  

##### <a name="properties"></a>Eigenschappen  
|**Naam**|**Waarde**|  
|-|-|  
|**Type**|Opdrachtregel uitvoeren|  
|**Naam**|Sysprep-bestanden kopiëren|  
|**Beschrijving**|Niet opgegeven|  

##### <a name="settings"></a>Instellingen  
|**Naam**|**Waarde**|  
|-|-|  
|**Vanaf de opdrachtregel**|`cscript.exe "%SCRIPTROOT%\LTISysprep.wsf"`|  
|**Beginnen in**|Niet opgegeven|  
|**Deze stap uitvoeren als de volgende account**|Niet opgegeven|  

##### <a name="options"></a>Opties  
|**Naam**|**Waarde**|  
|-|-|  
|**Deze stap uitschakelen**|Geen geselecteerd|  
|**Geslaagd-codes**|3010 0|  
|**Doorgaan bij fout**|Geen geselecteerd|  
|**Voorwaardelijke kwalificatie**|Niet opgegeven|  

#### <a name="create-bitlocker-partition"></a>BitLocker-partitie maken  
 Hiermee stelt u deze takenreeksstap het **BDEInstall** eigenschap op True, die aangeeft dat BitLocker moet worden geïnstalleerd op de doelcomputer. De unieke eigenschappen en instellingen voor de **BitLocker partitie maken** stap takenreekstype zijn:  

##### <a name="properties"></a>Eigenschappen  
|**Naam**|**Waarde**|  
|-|-|   
|**Type**|Takenreeksvariabele instellen|  
|**Naam**|BitLocker-partitie maken|  
|**Beschrijving**|Geen|  

##### <a name="settings"></a>Instellingen  
|**Naam**|**Waarde**|  
|-|-|  
|**Takenreeksvariabele**|BDE installeren|  
|**Waarde**|Waar|  

##### <a name="options"></a>Opties  
|**Naam**|**Waarde**|  
|-|-|  
|**Deze stap uitschakelen**|Geen geselecteerd|  
|**Geslaagd-codes**|3010 0|  
|**Doorgaan bij fout**|Geen geselecteerd|  
|**Voorwaardelijke kwalificatie**|Niet opgegeven|  

#### <a name="create-wim"></a>WIM maken  
 Deze takenreeksstap maakt een back-up van de doelcomputer. De unieke eigenschappen en instellingen voor de **maken WIM** stap takenreekstype zijn:  

##### <a name="properties"></a>Eigenschappen  
|**Naam**|**Waarde**|  
|-|-|  
|**Type**|Opdrachtregel uitvoeren|  
|**Naam**|WIM maken|  
|**Beschrijving**|Geen|  

##### <a name="settings"></a>Instellingen  
|**Naam**|**Waarde**|  
|-|-|  
|**Vanaf de opdrachtregel**|`cscript.exe "%SCRIPTROOT%\ZTIBackup.wsf"`|  
|**Beginnen in**|Niet opgegeven|  
|**Deze stap uitvoeren als de volgende account**|Niet opgegeven|  

##### <a name="options"></a>Opties  
|**Naam**|**Waarde**|  
|-|-|  
|**Deze stap uitschakelen**|Geen geselecteerd|  
|**Geslaagd-codes**|3010 0|  
|**Doorgaan bij fout**|Geen geselecteerd|  
|**Voorwaardelijke kwalificatie**|Niet opgegeven|  

#### <a name="disable-bde-protectors"></a>BDE-Protectors uitschakelen  
 Als BitLocker is geïnstalleerd op de doelcomputer, wordt de BitLocker-protectors uitgeschakeld in deze takenreeksstap.  

 De unieke eigenschappen en instellingen voor de **BDE-Protectors uitschakelen** stap takenreekstype zijn:  

##### <a name="properties"></a>Eigenschappen  
|**Naam**|**Waarde**|  
|-|-|  
|**Type**|Opdrachtregel uitvoeren|  
|**Naam**|BDE-Protectors uitschakelen|  
|**Beschrijving**|Geen|  

##### <a name="settings"></a>Instellingen  
|**Naam**|**Waarde**|  
|-|-|  
|**Vanaf de opdrachtregel**|`cscript.exe "%SCRIPTROOT%\ZTIDisableBDEProtectors.wsf"`|  
|**Beginnen in**|Niet opgegeven|  
|**Deze stap uitvoeren als de volgende account**|Niet opgegeven|  

##### <a name="options"></a>Opties  
|**Naam**|**Waarde**|  
|-|-|  
|**Deze stap uitschakelen**|Geen geselecteerd|  
|**Geslaagd-codes**|3010 0|  
|**Doorgaan bij fout**|Geen geselecteerd|  
|**Voorwaardelijke kwalificatie**|Niet opgegeven|  

#### <a name="enable-bitlocker"></a>BitLocker inschakelen  
 Deze takenreeksstap wordt BitLocker ingeschakeld op de doelcomputer. Hier volgt een kort overzicht van de instellingen die laten zien hoe deze stap oorspronkelijk is geconfigureerd in een van de MDT taak reeks sjablonen. Zie voor meer informatie over welke script voert deze taak en welke eigenschappen worden gebruikt, [ZTIBde.wsf](#ZTIBde.wsf).  

 De standaardconfiguratie van de **BitLocker inschakelen** takenreeksstap is:  

##### <a name="properties"></a>Eigenschappen  
|**Naam**|**Waarde**|  
|-|-|  
|**Type**|BitLocker inschakelen|  
|**Naam**|BitLocker inschakelen|  
|**Beschrijving**|Geen|  

##### <a name="settings"></a>Instellingen  
|**Naam**|**Waarde**|  
|-|-|  
|**Huidig besturingssysteemstation**|Geselecteerd|  
|**Alleen TPM**|Geselecteerd|  
|**Alleen een opstartsleutel op USB**|Geen geselecteerd|  
|**TPM en starten van de sleutel op USB**|Geen geselecteerd|  
|**Specifiek station**|Geen geselecteerd|  
|**In Active Directory**|Geselecteerd|  
|**Maak een herstelsleutel geen**|Geen geselecteerd|  
|**Wacht totdat BitLocker te voltooien**|Geen geselecteerd|  

##### <a name="options"></a>Opties  
|**Naam**|**Waarde**|  
|-|-|  
|**Deze stap uitschakelen**|Geen geselecteerd|  
|**Geslaagd-codes**|3010 0|  
|**Doorgaan bij fout**|Geen geselecteerd|  
|**Voorwaardelijke kwalificatie**|**BdeInstallSuppress** is niet gelijk aan Ja|  

#### <a name="enable-oem-disk-configuration"></a>OEM-schijfconfiguratie inschakelen  
 Hiermee stelt u deze takenreeksstap het **DeploymentType**eigenschap **NEWCOMPUTER**, waarmee de doelcomputer schijf worden gepartitioneerd en geformatteerd.  

 De unieke eigenschappen en instellingen voor de **OEM schijfconfiguratie inschakelen** stap takenreekstype zijn:  

##### <a name="properties"></a>Eigenschappen  
|**Naam**|**Waarde**|  
|-|-|  
|**Type**|Takenreeksvariabele instellen |  
|**Naam**|OEM-schijfconfiguratie inschakelen|  
|**Beschrijving**|Geen|  

##### <a name="settings"></a>Instellingen  
|**Naam**|**Waarde**|  
|-|-|  
|**Takenreeksvariabele**|deploymentType|  
|**Waarde**|NEWCOMPUTER|  

##### <a name="options"></a>Opties  
|**Naam**|**Waarde**|  
|-|-|  
|**Deze stap uitschakelen**|Geen geselecteerd|  
|**Geslaagd-codes**|3010 0|  
|**Doorgaan bij fout**|Geen geselecteerd|  
|**Voorwaardelijke kwalificatie**|Niet opgegeven|  

#### <a name="end-phase"></a>Einde fase  
 Deze takenreeksstap de huidige implementatiefase wordt beëindigd en de doelcomputer opnieuw wordt opgestart. Hier volgt een kort overzicht van de instellingen die laten zien hoe deze stap oorspronkelijk is geconfigureerd in een van de MDT taak reeks sjablonen.  

 De standaardconfiguratie van de **End fase** takenreeksstap is:  

##### <a name="properties"></a>Eigenschappen  
|**Naam**|**Waarde**|  
|-|-|  
|**Type**|Computer opnieuw opstarten|  
|**Naam**|Einde fase|  
|**Beschrijving**|Niet opgegeven|  

##### <a name="settings"></a>Instellingen  
|**Naam**|**Waarde**|  
|-|-|  
|Geen|Geen|  

##### <a name="options"></a>Opties  
|**Naam**|**Waarde**|  
|-|-|  
|**Deze stap uitschakelen**|Geen geselecteerd|  
|**Geslaagd-codes**|3010 0|  
|**Doorgaan bij fout**|Geen geselecteerd|  
|**Voorwaardelijke kwalificatie**|Niet opgegeven|  

#### <a name="execute-sysprep"></a>Sysprep uitvoeren  
 Deze takenreeksstap wordt Sysprep gestart op de doelcomputer. Hier volgt een kort overzicht van de instellingen die laten zien hoe deze stap oorspronkelijk is geconfigureerd in een van de MDT taak reeks sjablonen. Zie voor meer informatie over welke script bewerkstelligt deze taak en welke eigenschappen worden gebruikt, [LTISysprep.wsf](#LTISysprep.wsf).  

 De standaardconfiguratie van de **Sysprep uitvoeren** takenreeksstap is:  

##### <a name="properties"></a>Eigenschappen  
|**Naam**|**Waarde**|  
|-|-|  
|**Type**|Opdrachtregel uitvoeren|  
|**Naam**|Sysprep uitvoeren|  
|**Beschrijving**|Geen|  

##### <a name="settings"></a>Instellingen  
|**Naam**|**Waarde**|  
|-|-|  
|**Vanaf de opdrachtregel**|`cscript.exe "%SCRIPTROOT%\LTISysprep.wsf"`|  
|**Beginnen in**|Niet opgegeven|  
|**Deze stap uitvoeren als de volgende account**|Niet opgegeven|  

##### <a name="options"></a>Opties  
|**Naam**|**Waarde**|  
|-|-|  
|**Deze stap uitschakelen**|Geen geselecteerd|  
|**Geslaagd-codes**|3010 0|  
|**Doorgaan bij fout**|Geen geselecteerd|  
|**Voorwaardelijke kwalificatie**|Niet opgegeven|  

#### <a name="force-diskpart-action"></a>Diskpart actie forceren  
 Als de C:\\oem.wsf bestand bestaat, deze takenreeksstap wordt verwijderd van de C:\\oem.wsf-bestand, waardoor de **schijf formatteren en partitioneren** takenreeksstap om uit te voeren. Hier volgt een kort overzicht van de instellingen die laten zien hoe deze stap oorspronkelijk is geconfigureerd in een van de MDT taak reeks sjablonen.  

 De standaardconfiguratie van de **Force Diskpart actie** takenreeksstap is:  

##### <a name="properties"></a>Eigenschappen  
|**Naam**|**Waarde**|  
|-|-|  
|**Type**|Opdrachtregel uitvoeren|  
|**Naam**|Diskpart actie forceren|  
|**Beschrijving**|Niet opgegeven|  

##### <a name="settings"></a>Instellingen  
|**Naam**|**Waarde**|  
|-|-|  
|**Vanaf de opdrachtregel**|`cmd.exe /c if exist c:\oem.wsf del /q c:\oem.wsf`|  
|**Beginnen in**|Niet opgegeven|  
|**Deze stap uitvoeren als de volgende account**|Niet opgegeven|  

##### <a name="options"></a>Opties  
|**Naam**|**Waarde**|  
|-|-|  
|**Deze stap uitschakelen**|Geen geselecteerd|  
|**Geslaagd-codes**|0,1|  
|**Doorgaan bij fout**|Geselecteerd|  
|**Voorwaardelijke kwalificatie**|Geen|  

#### <a name="format-and-partition-disk"></a>Schijf formatteren en partitioneren  
 Deze takenreeksstap configureert en indelingen schijfpartities op de doelcomputer. Hier volgt een kort overzicht van de instellingen die laten zien hoe deze stap oorspronkelijk is geconfigureerd in een van de MDT taak reeks sjablonen.  

 Zie voor meer informatie over welke script bewerkstelligt deze taak en welke eigenschappen worden gebruikt, [ZTIDiskpart.wsf](#ZTIDiskpart.wsf).  

 De standaardconfiguratie van de **schijf formatteren en partitioneren** takenreeksstap is:  

##### <a name="properties"></a>Eigenschappen  
|**Naam**|**Waarde**|  
|-|-|  
|**Type**|Schijf formatteren en partitioneren|  
|**Naam**|Schijf formatteren en partitioneren|  
|**Beschrijving**|Niet opgegeven|  

##### <a name="settings"></a>Instellingen  
|**Naam**|**Waarde**|  
|-|-|  
|**Schijfnummer**|0|  
|**Schijftype**|Standaard \(MBR\)|  
|**Volume**|In de Volume-instelling voor de volgende sub\-instellingen zijn geconfigureerd:<br /><br /> \-                                 **De naam van partitie**. OSDisk<br /><br /> \-**Type partitie**. Primaire<br /><br /> \-                                 **Gebruik een percentage van resterende ruimte**. Geselecteerd<br /><br /> \-                                 **De grootte van\(%\)**. 100<br /><br /> \-**Grootte van een specifiek station gebruiken**. Geen geselecteerd<br /><br /> \-                                 **Maak dit een opstartpartitie**. Geselecteerd<br /><br /> \-**Bestandssysteem**. NTFS<br /><br /> \-**Snelformatteren**. Geselecteerd<br /><br /> \-**Variabele**. Niet opgegeven|  

##### <a name="options"></a>Opties  
|**Naam**|**Waarde**|  
|-|-|  
|**Deze stap uitschakelen**|Geen geselecteerd|  
|**Geslaagd-codes**|3010 0|  
|**Doorgaan bij fout**|Geen geselecteerd|  
|**Voorwaardelijke kwalificatie**|Niet opgegeven|  

> [!NOTE]
>  Wanneer u het CustomSettings.ini-bestand op de harde schijf en partitie configuraties op te geven, worden alleen de eerste harde schijf en eerst twee partities worden geconfigureerd. Bewerk ZTIGather.xml extra harde schijven of partities wilt configureren.  

#### <a name="gather-local-only"></a>Alleen lokale verzamelen  
 Deze takenreeksstap verzamelt configuratie-instellingen voor implementatie van lokale bronnen die betrekking hebben op de doelcomputer. Hier volgt een kort overzicht van de instellingen die laten zien hoe deze stap oorspronkelijk is geconfigureerd in een van de MDT taak reeks sjablonen.  

 Zie voor meer informatie over welke script bewerkstelligt deze taak en welke eigenschappen worden gebruikt, [ZTIGather.wsf](#ZTIGather.wsf).  

 De standaardconfiguratie van de **verzamelen alleen lokale** takenreeksstap is:  

##### <a name="properties"></a>Eigenschappen  
|**Naam**|**Waarde**|  
|-|-|  
|**Type**|Verzamelen|  
|**Naam**|Alleen lokale verzamelen|  
|**Beschrijving**|Niet opgegeven|  

##### <a name="settings"></a>Instellingen  
|**Naam**|**Waarde**|  
|-|-|  
|**Alleen lokale gegevens verzamelen**|Geselecteerd|  
|**Lokale gegevens verzamelen en verwerken van regels**|Geen geselecteerd|  
|**Regelbestand**|Niet opgegeven|  

##### <a name="options"></a>Opties  
|**Naam**|**Waarde**|  
|-|-|  
|**Deze stap uitschakelen**|Geen geselecteerd|  
|**Geslaagd-codes**|3010 0|  
|**Doorgaan bij fout**|Geen geselecteerd|  
|**Voorwaardelijke kwalificatie**|Geen|  

#### <a name="generate-application-migration-file"></a>Toepassing migratie-bestand genereren  
 Deze takenreeksstap genereert het bestand ZTIAppXmlGen.xml, die een lijst met bestandskoppelingen die zijn geïnstalleerd op de doelcomputer bevat. Hier volgt een kort overzicht van de instellingen die laten zien hoe deze stap oorspronkelijk is geconfigureerd in een van de MDT taak reeks sjablonen.  

 Zie voor meer informatie over welke script bewerkstelligt deze taak en welke eigenschappen worden gebruikt, [ZTIAppXmlGen.wsf](#ZTIAppXmlGen.wsf).  

 De standaardconfiguratie van de **toepassingsmigratie genereren** takenreeksstap bestand is:  

##### <a name="properties"></a>Eigenschappen  
|**Naam**|**Waarde**|  
|-|-|  
|**Type**|Opdrachtregel uitvoeren|  
|**Naam**|Toepassing migratie-bestand genereren|  
|**Beschrijving**|Niet opgegeven|  

##### <a name="settings"></a>Instellingen  
|**Naam**|**Waarde**|  
|-|-|  
|**Vanaf de opdrachtregel**|`cscript.exe "%SCRIPTROOT%\ZTIAppXmlGen.wsf" /capture`|  
|**Beginnen in**|Niet opgegeven|  
|**Deze stap uitvoeren als de volgende account**|Niet opgegeven|  

##### <a name="options"></a>Opties  
|**Naam**|**Waarde**|  
|-|-|  
|**Deze stap uitschakelen**|Geen geselecteerd|  
|**Geslaagd-codes**|3010 0|  
|**Doorgaan bij fout**|Geen geselecteerd|  
|**Voorwaardelijke kwalificatie**|Geen|  

#### <a name="inject-drivers"></a>Stuurprogramma's invoeren  
 Deze takenreeksstap injects stuurprogramma's die zijn geconfigureerd voor de implementatie van de doelcomputer. Hier volgt een kort overzicht van de instellingen die laten zien hoe deze stap oorspronkelijk is geconfigureerd in een van de MDT taak reeks sjablonen.  

 Zie voor meer informatie over welke script bewerkstelligt deze taak en welke eigenschappen worden gebruikt, [ZTIDrivers.wsf](#ZTIDrivers.wsf).  

 De standaardconfiguratie van de **stuurprogramma's invoeren** takenreeksstap is:  

##### <a name="properties"></a>Eigenschappen  
|**Naam**|**Waarde**|  
|-|-|  
|**Type**|Stuurprogramma's invoeren|  
|**Naam**|Stuurprogramma's invoeren|  
|**Beschrijving**|Niet opgegeven|  

##### <a name="settings"></a>Instellingen  
|**Naam**|**Waarde**|  
|-|-|  
|**Alleen overeenkomende stuurprogramma's installeren**|Alleen de stuurprogramma's die vereist zijn voor de doelcomputer en overeenkomen met wat is beschikbaar in uit injects\-van\-Box stuurprogramma's|  
|**Alle stuurprogramma's installeren**|Alle stuurprogramma's injects|  
|**Selectie profiel**|Stuurprogramma's die gekoppeld aan het geselecteerde profiel zijn injects|  

##### <a name="options"></a>Opties  
|**Naam**|**Waarde**|  
|-|-|  
|**Deze stap uitschakelen**|Geen geselecteerd|  
|**Geslaagd-codes**|3010 0|  
|**Doorgaan bij fout**|Geen geselecteerd|  
|**Voorwaardelijke kwalificatie**|Niet opgegeven|  

#### <a name="install-applications"></a>Toepassingen installeren  
 Deze takenreeksstap installeert toepassingen op de doelcomputer. Hier volgt een kort overzicht van de instellingen die laten zien hoe deze stap oorspronkelijk is geconfigureerd in een van de MDT taak reeks sjablonen.  

 Zie voor meer informatie over welke script bewerkstelligt deze taak en welke eigenschappen worden gebruikt, [ZTIApplications.wsf](#ZTIApplications.wsf).  

 De standaardconfiguratie van de **toepassingen installeren** takenreeksstap is:  

##### <a name="properties"></a>Eigenschappen  
|**Naam**|**Waarde**|  
|-|-|  
|**Type**|Toepassingen installeren|  
|**Naam**|Toepassingen installeren|  
|**Beschrijving**|Niet opgegeven|  

##### <a name="settings"></a>Instellingen  
|**Naam**|**Waarde**|  
|-|-|  
|**Meerdere toepassingen installeren**|Geselecteerd|  
|**Installeren van één toepassing**|Geen geselecteerd|  

##### <a name="options"></a>Opties  
|**Naam**|**Waarde**|  
|-|-|  
|**Deze stap uitschakelen**|Geen geselecteerd|  
|**Geslaagd-codes**|3010 0|  
|**Doorgaan bij fout**|Geen geselecteerd|  
|**Voorwaardelijke kwalificatie**|Niet opgegeven|  

#### <a name="install-operating-system"></a>Besturingssysteem installeren  
 Deze takenreeksstap installeert een besturingssysteem op de doelcomputer. Hier volgt een kort overzicht van de instellingen die laten zien hoe deze stap oorspronkelijk is geconfigureerd in een van de MDT taak reeks sjablonen.  

 De standaardconfiguratie van de **besturingssysteem installeren** takenreeksstap is:  

##### <a name="properties"></a>Eigenschappen  
|**Naam**|**Waarde**|  
|-|-|  
|**Type**|Besturingssysteem installeren|  
|**Naam**|Besturingssysteem installeren|  
|**Beschrijving**|Niet opgegeven|  

##### <a name="settings"></a>Instellingen  
|**Naam**|**Waarde**|  
|-|-|  
|**Besturingssysteem installeren**|Deze waarde komt overeen met het besturingssysteem dat is geselecteerd toen de takenreeks is gemaakt.|  
|**Schijf**|De schijf waarop het besturingssysteem wordt geïnstalleerd.|  
|**Partitie**|De partitie waarop het besturingssysteem wordt geïnstalleerd.|  

##### <a name="options"></a>Opties  
|**Naam**|**Waarde**|  
|-|-|  
|**Deze stap uitschakelen**|Geen geselecteerd|  
|**Geslaagd-codes**|3010 0|  
|**Doorgaan bij fout**|Geen geselecteerd|  
|**Voorwaardelijke kwalificatie**|Niet opgegeven|  

#### <a name="next-phase"></a>Volgende fase  
 Deze takenreeksstap updates de **fase** eigenschap met de volgende fase in het implementatieproces. Hier volgt een kort overzicht van de instellingen die laten zien hoe deze stap oorspronkelijk is geconfigureerd in een van de MDT taak reeks sjablonen.  

 Zie voor meer informatie over welke script bewerkstelligt deze taak en welke eigenschappen worden gebruikt, [ZTINextPhase.wsf](#ZTINextPhase.wsf).  

 De standaardconfiguratie van de **volgende fase** takenreeksstap is:  

##### <a name="properties"></a>Eigenschappen  
|**Naam**|**Waarde**|  
|-|-|  
|**Type**|Opdrachtregel uitvoeren|  
|**Naam**|Volgende fase|  
|**Beschrijving**|Niet opgegeven|  

##### <a name="settings"></a>Instellingen  
|**Naam**|**Waarde**|  
|-|-|  
|**Vanaf de opdrachtregel**|`cscript.exe "%SCRIPTROOT%\ZTINextPhase.wsf"`|  
|**Beginnen in**|Niet opgegeven|  
|**Deze stap uitvoeren als de volgende account**|Niet opgegeven|  

##### <a name="options"></a>Opties  
|**Naam**|**Waarde**|  
|-|-|  
|**Deze stap uitschakelen**|Geen geselecteerd|  
|**Geslaagd-codes**|3010 0|  
|**Doorgaan bij fout**|Geen geselecteerd|  
|**Voorwaardelijke kwalificatie**|Niet opgegeven|  

#### <a name="post-apply-cleanup"></a>Post\-opschonen toepassen  
 Deze takenreeksstap ruimt onnodige bestanden na de installatie van een installatiekopie op de doelcomputer. Hier volgt een kort overzicht van de instellingen die laten zien hoe deze stap oorspronkelijk is geconfigureerd in een van de MDT taak reeks sjablonen.  

 Zie voor meer informatie over welke script bewerkstelligt deze taak en welke eigenschappen worden gebruikt, [LTIApply.wsf](#LTIApply.wsf).  

 De standaardconfiguratie van de **Post\-toepassen opschonen** takenreeksstap is:  

##### <a name="properties"></a>Eigenschappen  
|**Naam**|**Waarde**|  
|-|-|  
|**Type**|Opdrachtregel uitvoeren|  
|**Naam**|Post\-opschonen toepassen|  
|**Beschrijving**|Niet opgegeven|  

##### <a name="settings"></a>Instellingen  
|**Naam**|**Waarde**|  
|-|-|  
|**Vanaf de opdrachtregel**|`cscript.exe "%SCRIPTROOT%\LTIApply.wsf" /post`|  
|**Beginnen in**|Niet opgegeven|  
|**Deze stap uitvoeren als de volgende account**|Niet opgegeven|  

##### <a name="options"></a>Opties  
|**Naam**|**Waarde**|  
|-|-|  
|**Deze stap uitschakelen**|Geen geselecteerd|  
|**Geslaagd-codes**|3010 0|  
|**Doorgaan bij fout**|Geen geselecteerd|  
|**Voorwaardelijke kwalificatie**|Niet opgegeven|  

#### <a name="recover-from-domain"></a>Herstellen van domein  
 Deze takenreeksstap controleert of dat de doelcomputer is lid van een domein. Zie voor meer informatie over welke script voert deze taak en welke eigenschappen worden gebruikt, [ZTIDomainJoin.wsf](#ZTIDomainJoin.wsf).  

 De unieke eigenschappen en instellingen voor het herstellen van het type stap takenreeks domein zijn:  

##### <a name="properties"></a>Eigenschappen  
|**Naam**|**Beschrijving**|  
|-|-|  
|**Type**|Lees\-alleen type is ingesteld op herstellen tegen storingen van domein koppelen.|  

##### <a name="settings"></a>Instellingen  
|**Naam**|**Beschrijving**|  
|-|-|  
|**Automatisch herstellen**|De takenreeksstap wordt geprobeerd de doelcomputer koppelen aan een domein.|  
|**Handmatige herstellen**|Als de doelcomputer niet lid worden van een domein, de takenreeksstap, wordt de taaksequencer onderbreken, zodat de gebruiker probeert de doelcomputer koppelen aan een domein.|  
|**Er is geen herstellen**|Als de doelcomputer niet aan een domein is, mislukt de takenreeks wordt uitgevoerd, stoppen van de takenreeks.|  

#### <a name="restart-computer"></a>Computer opnieuw opstarten  
 Deze takenreeksstap start opnieuw op de doelcomputer. Hier volgt een kort overzicht van de instellingen die laten zien hoe deze stap oorspronkelijk is geconfigureerd in een van de MDT taak reeks sjablonen.  

 De standaardconfiguratie van de **computer opnieuw opstarten** takenreeksstap is:  

##### <a name="properties"></a>Eigenschappen  
|**Naam**|**Waarde**|  
|-|-|  
|**Type**|Computer opnieuw opstarten|  
|**Naam**|Computer opnieuw opstarten|  
|**Beschrijving**|Niet opgegeven|  

##### <a name="settings"></a>Instellingen  
|**Naam**|**Waarde**|  
|-|-|  
|Geen|Geen|  

##### <a name="options"></a>Opties  
|**Naam**|**Waarde**|  
|-|-|  
|**Deze stap uitschakelen**|Geen geselecteerd|  
|**Geslaagd-codes**|3010 0|  
|**Doorgaan bij fout**|Geen geselecteerd|  
|**Voorwaardelijke kwalificatie**|Niet opgegeven|  

#### <a name="restore-groups"></a>Herstellen van groepen  
 Deze takenreeksstap wordt de eerder vastgelegde lidmaatschap van lokale groepen op de doelcomputer hersteld. Hier volgt een kort overzicht van de instellingen die laten zien hoe deze stap oorspronkelijk is geconfigureerd in een van de MDT taak reeks sjablonen.  

 Zie voor meer informatie over welke script bewerkstelligt deze taak en welke eigenschappen worden gebruikt, [ZTIGroups.wsf](#ZTIGroups.wsf).  

 De standaardconfiguratie van de **herstellen groepen** takenreeksstap is:  

##### <a name="properties"></a>Eigenschappen  
|**Naam**|**Waarde**|  
|-|-|  
|**Type**|Opdrachtregel uitvoeren|  
|**Naam**|Herstellen van groepen|  
|**Beschrijving**|Niet opgegeven|  

##### <a name="settings"></a>Instellingen  
|**Naam**|**Waarde**|  
|-|-|  
|**Vanaf de opdrachtregel**|`cscript.exe "%SCRIPTROOT%\ZTIGroups.wsf" /restore`|  
|**Beginnen in**|Niet opgegeven|  
|**Deze stap uitvoeren als de volgende account**|Niet opgegeven|  

##### <a name="options"></a>Opties  
|**Naam**|**Waarde**|  
|-|-|  
|**Deze stap uitschakelen**|Geen geselecteerd|  
|**Geslaagd-codes**|3010 0|  
|**Doorgaan bij fout**|Geen geselecteerd|  
|**Voorwaardelijke kwalificatie**|Als u alle voorwaarden wordt voldaan:<br /><br /> \-**DoCapture** is niet gelijk aan Ja<br /><br /> \-                                 **DoCapture** is niet gelijk aan voorbereiden|  

####  <a name="RestoreUserState"></a>Gebruikersstatus herstellen  
 Deze takenreeksstap wordt eerder vastgelegde Gebruikersstatus op de doelcomputer hersteld. Hier volgt een kort overzicht van de instellingen die laten zien hoe deze stap oorspronkelijk is geconfigureerd in een van de MDT taak reeks sjablonen.  

 Zie voor meer informatie over welke script bewerkstelligt deze taak en welke eigenschappen worden gebruikt, [ZTIUserState.wsf](#ZTIUserState.wsf).  

 Zie voor meer informatie over dit staptype [gebruikersstatus herstellen](http://technet.microsoft.com/library/bb632881.aspx).  

 De standaardconfiguratie van de **gebruikersstatus herstellen** takenreeksstap is:  

##### <a name="properties"></a>Eigenschappen  
|**Naam**|**Waarde**|  
|-|-|  
|**Type**|Opdrachtregel uitvoeren|  
|**Naam**|Gebruikersstatus herstellen|  
|**Beschrijving**|Niet opgegeven|  

##### <a name="settings"></a>Instellingen  
|**Naam**|**Waarde**|  
|-|-|  
|**Vanaf de opdrachtregel**|`cscript.exe "%SCRIPTROOT%\ZTIUserState.wsf" /restore`|  
|**Beginnen in**|Niet opgegeven|  
|**Deze stap uitvoeren als de volgende account**|Niet opgegeven|  

##### <a name="options"></a>Opties  
|**Naam**|**Waarde**|  
|-|-|  
|**Deze stap uitschakelen**|Geen geselecteerd|  
|**Geslaagd-codes**|3010 0|  
|**Doorgaan bij fout**|Geen geselecteerd|  
|**Voorwaardelijke kwalificatie**|Als u alle voorwaarden wordt voldaan:<br /><br /> \-Als **DoCapture** is niet gelijk aan Ja<br /><br /> \-Als **DoCapture** is niet gelijk aan voorbereiden|  

#### <a name="set-image-build"></a>Image Build instellen  
 Hiermee stelt u deze takenreeksstap het **ImageBuild** eigenschap in op de waarde in **OSCurrentVersion**. Hier volgt een kort overzicht van de instellingen die laten zien hoe deze stap oorspronkelijk is geconfigureerd in een van de MDT taak reeks sjablonen.  

 De standaardconfiguratie van de **ingesteld installatiekopie bouwen** takenreeksstap is:  

##### <a name="properties"></a>Eigenschappen  
|**Naam**|**Waarde**|  
|-|-|  
|**Type**|Takenreeksvariabele instellen|  
|**Naam**|Image Build instellen|  
|**Beschrijving**|Niet opgegeven|  

##### <a name="settings"></a>Instellingen  
|**Naam**|**Waarde**|  
|-|-|  
|**Takenreeksvariabele**|**ImageBuild**|  
|**Waarde**|**% OSCurrentVersion %**|  

##### <a name="options"></a>Opties  
|**Naam**|**Waarde**|  
|-|-|  
|**Deze stap uitschakelen**|Geen geselecteerd|  
|**Geslaagd-codes**|**3010 0**|  
|**Doorgaan bij fout**|Geen geselecteerd|  
|**Voorwaardelijke kwalificatie**|Niet opgegeven|  

#### <a name="set-image-flags"></a>Stel de vlag installatiekopie  
 Hiermee stelt u deze takenreeksstap het **ImageFlags** eigenschap in op de waarde in **OSSKU**. Hier volgt een kort overzicht van de instellingen die laten zien hoe deze stap oorspronkelijk is geconfigureerd in een van de MDT taak reeks sjablonen.  

 De standaardconfiguratie van de **installatiekopie vlaggen ingesteld** takenreeksstap is:  

##### <a name="properties"></a>Eigenschappen  
|**Naam**|**Waarde**|  
|-|-|  
|**Type**|Takenreeksvariabele instellen|  
|**Naam**|Stel de vlag installatiekopie|  
|**Beschrijving**|Niet opgegeven|  

##### <a name="settings"></a>Instellingen  
|**Naam**|**Waarde**|  
|-|-|  
|**Takenreeksvariabele**|ImageFlags|  
|**Waarde**|% OSSKU %|  

##### <a name="options"></a>Opties  
|**Naam**|**Waarde**|  
|-|-|  
|**Deze stap uitschakelen**|Geen geselecteerd|  
|**Geslaagd-codes**|3010 0|  
|**Doorgaan bij fout**|Geen geselecteerd|  
|**Voorwaardelijke kwalificatie**|Niet opgegeven|  

#### <a name="tattoo"></a>Specifiek teken  
 Deze takenreeksstap tattoos de doelcomputer met identificatie- en versie-informatie. Hier volgt een kort overzicht van de instellingen die laten zien hoe deze stap oorspronkelijk is geconfigureerd in een van de MDT taak reeks sjablonen.  

 Zie voor meer informatie over welke script bewerkstelligt deze taak en welke eigenschappen worden gebruikt, [ZTITatoo.wsf](#ZTITatoo.wsf).  

 De standaardconfiguratie van de **specifiek teken** takenreeksstap is:  

##### <a name="properties"></a>Eigenschappen  
|**Naam**|**Waarde**|  
|-|-|  
|**Type**|Opdrachtregel uitvoeren|  
|**Naam**|Specifiek teken|  
|**Beschrijving**|Niet opgegeven|  

##### <a name="settings"></a>Instellingen  
|**Naam**|**Waarde**|  
|-|-|  
|**Vanaf de opdrachtregel**|`cscript.exe "%SCRIPTROOT%\ZTITatoo.wsf"`|  
|**Beginnen in**|Niet opgegeven|  
|**Deze stap uitvoeren als de volgende account**|Niet opgegeven|  

##### <a name="options"></a>Opties  
|**Naam**|**Waarde**|  
|-|-|  
|**Deze stap uitschakelen**|Geen geselecteerd|  
|**Geslaagd-codes**|3010 0|  
|**Doorgaan bij fout**|Geen geselecteerd|  
|Voorwaardelijke kwalificatie|Niet opgegeven|  

#### <a name="validate"></a>valideren  
 Deze takenreeksstap wordt gecontroleerd of de doelcomputer voldoet aan de gespecificeerde implementatievereistevoorwaarden. Hier volgt een kort overzicht van de instellingen die laten zien hoe deze stap oorspronkelijk is geconfigureerd in een van de MDT taak reeks sjablonen.  

 Zie voor meer informatie over welke script bewerkstelligt deze taak en welke eigenschappen worden gebruikt, [ZTIValidate.wsf](#ZTIValidate.wsf).  

 De standaardconfiguratie van de **valideren** takenreeksstap is:  

##### <a name="properties"></a>Eigenschappen  
|**Naam**|**Waarde**|  
|-|-|  
|**Type**|valideren|  
|**Naam**|valideren|  
|**Beschrijving**|Niet opgegeven|  

##### <a name="settings"></a>Instellingen  
|**Naam**|**Waarde**|  
|-|-|  
|**Minimumgeheugen garanderen \(MB\)**|Geselecteerd. De selector waarde is ingesteld op **768**.|  
|**Minimale processorsnelheid garanderen \(MHz\)**|Geselecteerd. De selector waarde is ingesteld op **800**.|  
|**Zorg ervoor dat de grootte van de opgegeven installatiekopie past \(MB\)**|Geen geselecteerd.|  
|**Zorg ervoor dat de huidige besturingssysteem worden vernieuwd**|Geselecteerd. De selector waarde is ingesteld op **Server** of **Client**, afhankelijk van de sjabloon die wordt gebruikt voor het maken van de takenreeks wordt uitgevoerd.|  

##### <a name="options"></a>Opties  
|**Naam**|**Waarde**|  
|-|-|  
|**Deze stap uitschakelen**|Geen geselecteerd|  
|**Geslaagd-codes**|3010 0|  
|**Doorgaan bij fout**|Geen geselecteerd|  
|**Voorwaardelijke kwalificatie**|Niet opgegeven|  

#### <a name="windows-update-pre-application-installation"></a>Windows Update \(Pre\-installatie van toepassing)  
 Deze takenreeksstap worden updates geïnstalleerd op de doelcomputer voordat de installatie van toepassingen. Hier volgt een kort overzicht van de instellingen die laten zien hoe deze stap oorspronkelijk is geconfigureerd in een van de MDT taak reeks sjablonen.  

 Zie voor meer informatie over welke script bewerkstelligt deze taak en welke eigenschappen worden gebruikt, [ZTIWindowsUpdate.wsf](#ZTIWindowsUpdate.wsf).  

 De standaardconfiguratie van de **Windows Update \(Pre\-toepassingsinstallatie\)**  takenreeksstap is:  

##### <a name="properties"></a>Eigenschappen  
|**Naam**|**Waarde**|  
|-|-|   
|**Type**|Opdrachtregel uitvoeren|  
|**Naam**|Windows Update \(Pre\-installatie van de toepassing\)|  
|**Beschrijving**|Niet opgegeven|  

##### <a name="settings"></a>Instellingen  
|**Naam**|**Waarde**|  
|-|-|  
|**Vanaf de opdrachtregel**|`cscript.exe "%SCRIPTROOT%\ZTIWindowsUpdate.wsf"`|  
|**Beginnen in**|Niet opgegeven|  
|**Deze stap uitvoeren als de volgende account**|Niet opgegeven|  

##### <a name="options"></a>Opties  
|**Naam**|**Waarde**|  
|-|-|   
|**Deze stap uitschakelen**|Geen geselecteerd|  
|**Geslaagd-codes**|3010 0|  
|**Doorgaan bij fout**|Geen geselecteerd|  
|**Voorwaardelijke kwalificatie**|Niet opgegeven|  

#### <a name="windows-update-post-application-installation"></a>Windows Update (een toepassing na installatie)  
 Deze takenreeksstap is hetzelfde als de **Windows Update (vooraf toepassingsinstallatie)** takenreeksstap.  

#### <a name="wipe-disk"></a>Schijf wissen  
 Deze takenreeksstap wordt gewist alle gegevens van de schijf met behulp de **indeling** opdracht.  

 Zie voor meer informatie over welke script bewerkstelligt deze taak en welke eigenschappen worden gebruikt, [ZTIWipeDisk.wsf](#ZTIWipeDisk.wsf).  

 De standaardconfiguratie van de **schijf wissen** takenreeksstap is:  

##### <a name="properties"></a>Eigenschappen  
|**Naam**|**Waarde**|  
|-|-|  
|**Type**|Opdrachtregel uitvoeren|  
|**Naam**|Schijf wissen|  
|**Beschrijving**|Dit wordt alleen uitgevoerd als **WipeDisk**= TRUE in CustomSettings.ini|  

##### <a name="settings"></a>Instellingen  
|**Naam**|**Waarde**|  
|-|-|  
|**Vanaf de opdrachtregel**|`cscript.exe "%SCRIPTROOT%\ZTIWipeDisk.wsf"`|  
|**Beginnen in**|Niet opgegeven|  
|**Deze stap uitvoeren als de volgende account**|Niet opgegeven|  

##### <a name="options"></a>Opties  
|**Naam**|**Waarde**|  
|-|-|  
|**Deze stap uitschakelen**|Geen geselecteerd|  
|**Geslaagd-codes**|3010 0|  
|**Doorgaan bij fout**|Geen geselecteerd|  
|**Voorwaardelijke kwalificatie**|Niet opgegeven|  

## <a name="properties"></a>Eigenschappen  
 De scripts gebruikt Lite Touch Installation (LTI) en ZTI verwijzingseigenschappen om te bepalen de processtappen en configuratie-instellingen gebruikt tijdens de implementatie. De scripts maken sommige van deze eigenschappen automatisch. Andere eigenschappen moeten worden geconfigureerd in het CustomSettings.ini-bestand. Enkele van deze eigenschappen zijn:  

-   Specifiek voor ZTI alleen  

-   Specifiek voor alleen LTI  

-   Voor gebruik in zowel ZTI en LTI  

 Gebruik deze verwijzing om te bepalen van de juiste eigenschappen te configureren en de geldige waarden voor elke eigenschap wilt opnemen.  

 De volgende informatie is opgegeven voor elke eigenschap:  

-   **Beschrijving**. Bevat een beschrijving van het doel van de eigenschap en eventuele relevante informatie met betrekking tot het aanpassen van de eigenschap.  

    > [!NOTE]
    >  Tenzij expliciet alleen opgegeven voor ZTI of LTI, is een eigenschap is ongeldig voor zowel ZTI en LTI.  

-   **Waarde en beschrijving**. Hiermee geeft u de geldige waarden voor de eigenschap en een korte beschrijving van wat elke waarde betekent worden opgegeven. (Waarden cursief duiden dat een waarde wordt vervangen, bijvoorbeeld de waarde *gebruiker1*, *Gebruiker2* geeft aan dat *gebruiker1* en *Gebruiker2* zou worden vervangen door de werkelijke naam van gebruikersaccounts.)  

-   **Voorbeeld**. Bevat een voorbeeld van een eigenschap gebruiken zoals deze wordt in het ini-bestanden weergegeven mogelijk.  

 Zie voor meer informatie over deze en andere eigenschappen van takenreeks die kunnen worden verwezen tijdens het uitvoeren van een implementatie ZTI [Operating System Deployment Takenreeksvariabelen](http://technet.microsoft.com/library/bb632442.aspx).  

 De implementatiescripts vereist doorgaans waarden in hoofdletters worden opgegeven zodat ze correct worden gelezen. Daarom gebruiken bij het opgeven van eigenschapswaarden hoofdletters.  

### <a name="property-definition"></a>Definitie van eigenschap  
 De volgende secties worden de eigenschappen die beschikbaar voor implementaties van LTI en ZTI in MDT zijn.  

> [!TIP]
>  De eigenschappen worden in alfabetische volgorde gesorteerd.  

####  <a name="\_SMSTSOrgName"></a>\_SMSTSOrgName  
 De Taaksequencer-engine weergave banner aanpassen  
|**Geconfigureerd door de eigenschap**|||**De eigenschap is van toepassing op**||  
|-|-|-|-|-|  
|BootStrap.ini|-||LTI|-|  
|CustomSettings.ini|-||||  
|MDT-DB|-||ZTI|-|  

|**Waarde**|**Beschrijving**|  
|-|-|  
|*naam*|De naam die wordt gebruikt in de banner van de Taaksequencer-engine weergeven|  

|**Voorbeeld**|  
|-|  
|`[Settings] Priority=Default  [Default] _SMSTSOrgName=Woodgrove Bank`|  

####  <a name="ADDSLogPath"></a>ADDSLogPath  
 Volledig gekwalificeerde, niet-UNC-map op een harde schijf op de lokale computer voor het hosten van de AD DS-logboekbestanden. Als de map bestaat moet leeg zijn. Als deze niet bestaat nog, wordt deze gemaakt.  

|**Geconfigureerd door de eigenschap**|||**De eigenschap is van toepassing op**||  
|-|-|-|-|-|  
|BootStrap.ini|||LTI|-|  
|CustomSettings.ini|-||||  
|MDT-DB|-||ZTI|-|  

|**Waarde**|**Beschrijving**|  
|-|-|  
|*log_path*|Volledig gekwalificeerde, niet-UNC-map op een harde schijf op de lokale computer voor het hosten van de AD DS-logboekbestanden|  

|**Voorbeeld**|
|-|   
|`[Settings] Priority=Default  [Default] ADDSLogPath=%DestinationLogicalDrive%\Windows\NTDS`|  

####  <a name="ADDSPassword"></a>ADDSPassword  
 Accountreferenties op die kunnen worden gebruikt bij het promoveren van de server tot een domeincontroller.  

|**Geconfigureerd door de eigenschap**|||**De eigenschap is van toepassing op**||  
|-|-|-|-|-|  
|BootStrap.ini|||LTI|-|  
|CustomSettings.ini|-||||  
|MDT-DB|-||ZTI|-|  

|**Waarde**|**Beschrijving**|  
|-|-|  
|*wachtwoord*|Accountreferenties op die kunnen worden gebruikt voor de promotiebewerking|  

|**Voorbeeld**|  
|-|  
|`[Settings] Priority=Default  [Default] ADDSUserName=Administrator ADDSUserDomain=WoodGroveBank ADDSPassword=<complex_password>`|  

####  <a name="ADDSUserDomain"></a>ADDSUserDomain  
 Dit is het domein van het account dat is opgegeven door **ADDSUserName** moet worden opgehaald. Als de bewerking is een nieuw forest maakt of een lidserver vanaf een back-upgrade domeincontroller helemaal is er geen standaardwaarde. Als de bewerking is voor het maken van een nieuwe structuur, wordt de standaardwaarde is dat de DNS-naam van het forest van de computer is momenteel gekoppeld aan. Als de bewerking is voor het maken van een nieuw onderliggend domein of een replica vervolgens de standaardwaarde is de DNS-naam van het domein dat de computer lid is. Als de bewerking is te degraderen van de computer en de computer een domeincontroller in een onderliggend domein is, is de standaardinstelling de DNS-naam van de bovenliggende domeinen. Als de bewerking is te degraderen van de computer en de computer een domeincontroller in een hoofddomeinstructuur is, is de standaardinstelling de DNS-naam van het forest.  

|**Geconfigureerd door de eigenschap**|||**De eigenschap is van toepassing op**||  
|-|-|-|-|-|  
|BootStrap.ini|||LTI|-|  
|CustomSettings.ini|-||||  
|MDT-DB|-||ZTI|-|  

|**Waarde**|**Beschrijving**|  
|-|-|  
|*domein*|De account van de gebruikersnaam van domein moet worden opgehaald|  

|**Voorbeeld**|  
|-|  
|`[Settings] Priority=Default  [Default] ADDSUserName=Administrator ADDSUserDomain=WoodGroveBank ADDSPassword=<complex_password>`|  

####  <a name="ADDSUserName"></a>ADDSUserName  
 Accountreferenties op die wordt gebruikt bij het promoveren van de server tot een domeincontroller.  

|**Geconfigureerd door de eigenschap**|||**De eigenschap is van toepassing op**||  
|-|-|-|-|-|  
|BootStrap.ini|||LTI|-|  
|CustomSettings.ini|-||||  
|MDT-DB|-||ZTI|-|  

|**Waarde**|**Beschrijving**|  
|-|-|  
|*gebruikersnaam*|Accountreferenties op die wordt gebruikt voor de promotiebewerking|  

|**Voorbeeld**|  
|-|  
|`[Settings] Priority=Default  [Default] ADDSUserName=Administrator ADDSUserDomain=WoodGroveBank ADDSPassword=complex_password`|  

####  <a name="Administrators"></a>Beheerders  
 Een lijst met gebruikersaccounts en groepen die worden toegevoegd aan de lokale groep Administrators op de doelcomputer. De **beheerders** eigenschap is een lijst met tekstwaarden die elke niet-lege waarde. De **beheerders** eigenschap heeft een numeriek achtervoegsel (bijvoorbeeld **Administrators001** of **Administrators002**).  

|**Geconfigureerd door de eigenschap**|||**De eigenschap is van toepassing op**||  
|-|-|-|-|-|  
|BootStrap.ini|||LTI|-|  
|CustomSettings.ini|-||||  
|MDT-DB|-||ZTI|-|  

|**Waarde**|**Beschrijving**|  
|-|-|  
|*naam*|De naam van een gebruiker of groep die moet worden toegevoegd aan de lokale groep Administrators|  

|**Voorbeeld**|  
|-|   
|`[Settings] Priority=Default  [Default] Administrators001=WOODGROVEBANK\NYC Help Desk Staff Administrators002=WOODGROVEBANK\North America East Help Desk Staff PowerUsers001=WOODGROVEBANK\User01 PowerUsers002=WOODGROVEBANK\User02`|  

####  <a name="AdminPassword"></a>AdminPassword  
 Hiermee definieert u het wachtwoord dat wordt toegewezen aan de lokale beheerdersaccount op de doelcomputer. Als niet wordt opgegeven, is het wachtwoord voorafgaand aan de implementatie van de gebruiker Administrator-account wordt gebruikt.  

|**Geconfigureerd door de eigenschap**|||**De eigenschap is van toepassing op**||  
|-|-|-|-|-|  
|BootStrap.ini|||LTI|-|  
|CustomSettings.ini|-||||  
|MDT-DB|-||ZTI|-|  

|**Waarde**|**Beschrijving**|  
|-|-|
|*admin_password*|Het wachtwoord op dat moet worden toegewezen aan het beheerdersaccount van de gebruiker op de doelcomputer|  

|**Voorbeeld**|  
|-|   
|`[Settings] Priority=Default  [Default] Administrators001=WOODGROVEBANK\NYC Help Desk Staff AdminPassword=<admin_password>`|  

####  <a name="Applications"></a>Toepassingen  
 Een lijst van de toepassing-GUID's die moeten worden geïnstalleerd op de doelcomputer. Deze toepassingen zijn opgegeven op het knooppunt toepassingen in de implementatie-Workbench. Deze GUID's worden opgeslagen in het bestand Applications.xml. De **toepassingen** eigenschap is een lijst met tekstwaarden die elke niet-lege waarde. De **toepassingen** eigenschap heeft een numeriek achtervoegsel (bijvoorbeeld **Applications001** of **Applications002**).  

|**Geconfigureerd door de eigenschap**|||**De eigenschap is van toepassing op**||  
|-|-|-|-|-|
|BootStrap.ini|||LTI|-|  
|CustomSettings.ini|-||||  
|MDT-DB|-||ZTI||  

|**Waarde**|**Beschrijving**|  
|-|-|
|*application_guid*|De GUID is opgegeven door de Implementatieworkbench voor de toepassing worden geïmplementeerd op de doelcomputer. De GUID overeenkomt met de GUID die is opgeslagen in het bestand Applications.xml toepassing.|  

|**Voorbeeld**|  
|-|  
|`[Settings] Priority=Default  [Default] Applications001={1D7DF331-47B7-472C-87B3-442597EC2F7D} Applications002={9d2b8999-5e4d-4f3d-bb05-edaaf4fe5628}`|  

####  <a name="ApplicationSuccessCodes"></a>ApplicationSuccessCodes  
 Een door spaties gescheiden lijst met foutcodes door het script ZTIApplications gebruikt om te bepalen van de geslaagde installatie van toepassingen.  

> [!NOTE]
>  Deze eigenschap is alleen van toepassing op de **toepassing installeren** task sequence staptype en wanneer **meerdere toepassingen installeert** is geselecteerd.  

|**Geconfigureerd door de eigenschap**|||**De eigenschap is van toepassing op**||  
|-|-|-|-|-|
|BootStrap.ini|||LTI|-|  
|CustomSettings.ini|-||||  
|MDT-DB|-||ZTI||  

|**Waarde**|**Beschrijving**|  
|-|-|
|*error_codes*|De foutcodes die bepalen wanneer toepassingen zijn geïnstalleerd. Standaardwaarden zijn **0** en **3010**.|  

|**Voorbeeld**|  
|-|    
|`[Settings] Priority=Default  [Default] ApplicationSuccessCodes=0 3010`|  

####  <a name="ApplyGPOPack"></a>ApplyGPOPack  
 Deze eigenschap wordt gebruikt om te bepalen of de **pakket lokaal groepsbeleidsobject toepassen** takenreeksstap wordt uitgevoerd.  

> [!NOTE]
>  De standaardwaarde voor deze eigenschap altijd voert de **pakket lokaal groepsbeleidsobject toepassen** takenreeksstap. U moet expliciet een waarde van 'Nee' om dit gedrag negeren opgeven...  

|**Geconfigureerd door de eigenschap**|||**De eigenschap is van toepassing op**||  
|-|-|-|-|-|
|BootStrap.ini|||LTI|-|  
|CustomSettings.ini|-||||  
|MDT-DB|-||ZTI||  

|**Waarde**|**Beschrijving**|  
|-|-|  
|**JA**|De **pakket lokaal groepsbeleidsobject toepassen** takenreeksstap wordt uitgevoerd. Dit is de standaardwaarde.|  
|**ER IS GEEN**|De **pakket lokaal groepsbeleidsobject toepassen** takenreeksstap wordt niet uitgevoerd.|  

|**Voorbeeld**|  
|-|  
|`[Settings] Priority=Default  [Default] ApplyGPOPack=NO`|  

####  <a name="Architecture"></a>Architectuur  
 De processorarchitectuur van de processor die momenteel wordt uitgevoerd, die niet noodzakelijkerwijs de processorarchitectuur ondersteund door de doelcomputer. Bijvoorbeeld, wanneer waarop een 32-bits – compatibel besturingssysteem op een 64-bits processor **architectuur** wordt aangegeven dat de processorarchitectuur 32-bits is.  

 Gebruik de **CapableArchitecture** eigenschap voor het identificeren van de werkelijke processorarchitectuur die ondersteuning biedt voor de doelcomputer.  

> [!NOTE]
>  Deze eigenschap wordt dynamisch ingesteld door de MDT-scripts en is niet geconfigureerd in CustomSettings.ini. Deze eigenschap behandelen als alleen-lezen. Echter, kunt u deze eigenschap binnen CustomSettings.ini, zoals wordt weergegeven in de volgende voorbeelden om te helpen bij het definiëren van de configuratie van de doelcomputer.  

|**Geconfigureerd door de eigenschap**|||**De eigenschap is van toepassing op**||  
|-|-|-|-|-|
|BootStrap.ini|||LTI|-|  
|CustomSettings.ini|||||  
|MDT-DB|||ZTI|-|  

|**Waarde**|**Beschrijving**|  
|-|-|
|**x86**|Processorarchitectuur is 32-bits.|  
|**x64**|Processorarchitectuur is 64-bits.|  

|**Voorbeeld**|  
|-|  
|Geen|  

####  <a name="AreaCode"></a>Netnummer  
 Het netnummer wordt geconfigureerd voor het besturingssysteem op de doelcomputer. Deze eigenschap kan alleen numerieke tekens. Deze waarde wordt ingevoegd in de juiste configuratie-instellingen in Unattend.xml.  

|**Geconfigureerd door de eigenschap**|||**De eigenschap is van toepassing op**||  
|-|-|-|-|-|
|BootStrap.ini|||LTI|-|  
|CustomSettings.ini|-||||  
|MDT-DB|-||ZTI|-|  

|**Waarde**|**Beschrijving**|  
|-|-|
|*netnummer*|Het netnummer waar de doelcomputer wordt geïmplementeerd|  

|**Voorbeeld**|  
|-|    
|`[Settings] Priority=Default  [Default] AreaCode=206 CountryCode=001 Dialing=TONE LongDistanceAccess=9`|  

####  <a name="AssetTag"></a>AssetTag  
 De tag activumnummer die zijn gekoppeld aan de doelcomputer. De notatie voor asset tag getallen is niet gedefinieerd. Gebruik deze eigenschap te maken van een subsectie met instellingen die zijn gericht op een specifieke computer.  

> [!NOTE]
>  Deze eigenschap wordt dynamisch ingesteld door de MDT-scripts en de waarde is ingesteld in CustomSettings.ini of de MDT-DB kan hebben. Deze eigenschap behandelen als alleen-lezen. Echter kunt u deze eigenschap binnen CustomSettings.ini of de MDT-database, zoals wordt weergegeven in de volgende voorbeelden om te helpen bij het definiëren van de configuratie van de doelcomputer.  

|**Geconfigureerd door de eigenschap**|||**De eigenschap is van toepassing op**||  
|-|-|-|-|-|
|BootStrap.ini|||LTI|-|  
|CustomSettings.ini|||||  
|MDT-DB|||ZTI|-|  

|**Waarde**|**Beschrijving**|  
|-|-|
|*asset_tag*|De indeling van de inventaristag is niet gedefinieerd en wordt bepaald door de standaard asset tag van elke organisatie.|  

|**Voorbeeld 1**|  
|-|   
|`[Settings] Priority=Default  [Default] OSDComputerName=HP-%AssetTag%`|  

|**Voorbeeld 2**|  
|-|    
|`[Settings] Priority=AssetTag, Default  [Default] OSInstall=YES  [0034034931] OSDComputerName=HPD530-1  [0034003233] OSDNEWMACHINENAME=BVMXP`|  

####  <a name="AutoConfigDNS"></a>AutoConfigDNS  
 Hiermee geeft u op of de Wizard Active Directory installeren DNS voor het nieuwe domein configureert als wordt gedetecteerd dat de DNS-protocol voor dynamische updates niet beschikbaar is.  

> [!CAUTION]
>  Waarde van deze eigenschap moet in hoofdletters worden opgegeven zodat de implementatiescripts kunnen correct worden gelezen.  

|**Geconfigureerd door de eigenschap**|||**De eigenschap is van toepassing op**||  
|-|-|-|-|-|
|BootStrap.ini|||LTI|-|  
|CustomSettings.ini|-||||  
|MDT-DB|-||ZTI|-|  

|**Waarde**|**Beschrijving**|  
|-|-|
|**JA**|Het configureren van DNS voor het nieuwe domein als de DNS-protocol voor dynamische updates niet beschikbaar|  
|**ER IS GEEN**|Biedt DNS niet configureren voor het domein|  

|**Voorbeeld**|  
|-|  
|`[Settings] Priority=Default  [Default] AutoConfigDNS=YES`|  

####  <a name="BackupDir"></a>Back-upmap  
 De map waarin de back-ups van de doelcomputer zijn opgeslagen. Deze map bestaat onder het UNC-pad dat is opgegeven in de **BackupShare** eigenschap. Als de map niet al bestaat, wordt deze automatisch gemaakt.  

|**Geconfigureerd door de eigenschap**|||**De eigenschap is van toepassing op**||  
|-|-|-|-|-|  
|BootStrap.ini|||LTI|-|  
|CustomSettings.ini|-||||  
|MDT-DB|-||ZTI|-|  

|**Waarde**|**Beschrijving**|  
|-|-|
|*Map*|De naam van de map onder de gedeelde map die is opgegeven bestaat in de **BackupShare** eigenschap|  

|**Voorbeeld**|  
|-|    
|`[Settings] Priority=Default  [Default] DoCapture=YES BackupShare=\\NYC-AM-FIL-01\Backup$ BackupDir=%OSDComputerName% BackupDrive=C:`|  

####  <a name="BackupDrive"></a>BackupDrive  
 Het station in de back-up van de doelcomputer op te nemen. Deze eigenschap wordt standaard ingesteld op het station dat 1 0 schijfpartitie bevat. Het kan ook worden ingesteld op **alle**.  

|**Geconfigureerd door de eigenschap**|||**De eigenschap is van toepassing op**||  
|-|-|-|-|-|  
|BootStrap.ini|||LTI|-|  
|CustomSettings.ini|-||||  
|MDT-DB|-||ZTI|-|  

|**Waarde**|**Beschrijving**|  
|-|-|
|*backup_drive*|De stationsletter van het station om de back-up maken|  
|**ALLE**|Back-up van alle stations op de doelcomputer|  

|**Voorbeeld**|  
|-|   
|`[Settings] Priority=Default  [Default] DoCapture=YES BackupShare=\\NYC-AM-FIL-01\Backup$ BackupDir=%OSDComputerName% BackupDrive=C:`|  

####  <a name="BackupFile"></a>Back-upbestand  
 Hiermee geeft u het WIM-bestand dat wordt gebruikt door het script ZTIBackup.wsf. Zie voor meer informatie over welke script maakt gebruik van deze eigenschap [ZTIBackup.wsf](#ZTIBackup.wsf).  

|**Geconfigureerd door de eigenschap**|||**De eigenschap is van toepassing op**||  
|-|-|-|-|-|  
|BootStrap.ini|||LTI|-|  
|CustomSettings.ini|-||||  
|MDT-DB|-||ZTI|-|  

|**Waarde**|**Beschrijving**|  
|-|-|  
|*Back-upmap*|De naam van het bestand Windows Imaging Format (WIM) worden gebruikt tijdens back up.|  

|**Voorbeeld**|  
|-|   
|`[Settings] Priority=Default  [Default] DoCapture=YES BackupShare=\\NYC-AM-FIL-01\Backup$ BackupDir=%OSDComputerName% BackupFile=%OSDComputerName%.wim`|  

####  <a name="BackupShare"></a>BackupShare  
 De gedeelde map waarin de back-ups van de doelcomputer zijn opgeslagen.  

 De referenties gebruikt voor toegang tot deze gedeelde map voor:  

-   LTI zijn de referenties zijn opgegeven in de Wizard implementatie.  

-   ZTI zijn de referenties die worden gebruikt door de Configuration Manager geavanceerde Client netwerktoegangsaccount.  

 De vereiste machtigingen voor deze share zijn als volgt:  

-   **Computers in het domein**. Toestaan dat de machtiging mappen maken/gegevens toevoegen.  

-   **Domeingebruikers**. Toestaan dat de machtiging mappen maken/gegevens toevoegen.  

-   **Maker eigenaar**. Toestaan dat de machtiging Volledig beheer.  

|**Geconfigureerd door de eigenschap**|||**De eigenschap is van toepassing op**||  
|-|-|-|-|-|  
|BootStrap.ini|||LTI|-|  
|CustomSettings.ini|-||||  
|MDT-DB|-||ZTI|-|  

|**Waarde**|**Beschrijving**|  
|-|-|
|*UNC_path*|Het UNC-pad van de gedeelde map<br /><br /> Opmerking:<br /><br /> Het UNC-pad opgegeven voor deze eigenschap moet bestaan voordat u het beoogde besturingssysteem implementeert.|  

|**Voorbeeld**|  
|-|   
|`[Settings] Priority=Default  [Default] DoCapture=YES BackupShare=\\NYC-AM-FIL-01\Backup$ BackupDir=%OSDComputerName% BackupDrive=C:`|  

####  <a name="BDEAllowAlphaNumericPin"></a>BDEAllowAlphaNumericPin  
 Deze eigenschap configureert u of BitLocker pincodes alfanumerieke waarden bevatten.  

|**Geconfigureerd door de eigenschap**|||**De eigenschap is van toepassing op**||  
|-|-|-|-|-|  
|BootStrap.ini|||LTI|-|  
|CustomSettings.ini|-||||  
|MDT-DB|-||ZTI|-|  

|**Waarde**|**Beschrijving**|  
|-|-|
|**JA**|Alfanumerieke tekens zijn toegestaan in de PINCODE.<br /><br /> Opmerking:<br /><br /> Naast deze eigenschap instelt op **Ja**, wordt de **toestaan Verbeterde pincodes voor opstarten** instelling voor Groepsbeleid moet zijn ingeschakeld.|  
|**ER IS GEEN**|Alleen numerieke tekens zijn toegestaan in de PINCODE.|  

|**Voorbeeld**|  
|-|   
|`[Settings] Priority=Default  [Default] BDEInstallSuppress=NO BDEAllowAlphaNumericPin=YES BDEDriveLetter=S: BDEDriveSize=2000 BDEInstall=TPMKey BDERecoveryKey=AD BDEKeyLocation=C:`|  

####  <a name="BDEDriveLetter"></a>BDEDriveLetter  
 De stationsletter voor de partitie die is niet versleuteld met BitLocker, ook wel bekend als de *systeemvolume*. SYSVOL is de map waarin de hardware-specifieke bestanden die nodig zijn voor het laden van Windows-computers nadat het BIOS het platform is opgestart.  

|**Geconfigureerd door de eigenschap**|||**De eigenschap is van toepassing op**||  
|-|-|-|-|-|  
|BootStrap.ini|||LTI|-|  
|CustomSettings.ini|-||||  
|MDT-DB|-||ZTI||  

|**Waarde**|**Beschrijving**|  
|-|-|  
|*stationsletter*|De letter aanduiding voor de logische schijf voor het systeemvolume (zoals S of T). De standaardwaarde is **S**.|  

|**Voorbeeld**|  
|-|  
|`[Settings] Priority=Default  [Default] BDEInstallSuppress=NO BDEDriveLetter=S: BDEDriveSize=2000 BDEInstall=TPMKey BDERecoveryKey=AD BDEKeyLocation=C:`|  

####  <a name="BDEDriveSize"></a>BDEDriveSize  
 De grootte van de systeempartitie van BitLocker. De waarde is opgegeven in megabytes. In het voorbeeld is de grootte van de BitLocker-partitie maken bijna 2 GB (2.000 MB).  

|**Geconfigureerd door de eigenschap**|||**De eigenschap is van toepassing op**||  
|-|-|-|-|-|  
|**Geconfigureerd door de eigenschap**|||**De eigenschap is van toepassing op**||  
|BootStrap.ini|||LTI|-|  
|CustomSettings.ini|-||||  
|MDT-DB|-||ZTI|-|  

|**Waarde**|**Beschrijving**|  
|-|-|
|*drive_size*|De grootte van de partitie in megabytes; de standaardgrootte zijn:<br /><br /> -Windows 7 en Windows Server 2008 R2: 300 MB|  

|**Voorbeeld**|  
|-|   
|`[Settings] Priority=Default  [Default] BDEInstallSuppress=NO BDEDriveLetter=S: BDEDriveSize=2000 BDEInstall=TPMKey BDERecoveryKey=AD BDEKeyLocation=C:`|  

####  <a name="BDEInstall"></a>BDEInstall  
 Het type van de installatie van BitLocker moet worden uitgevoerd. Beveiligen van de doelcomputer met behulp van een van de volgende methoden:  

-   Een TPM-microcontroller  

-   Een TPM en een externe opstartsleutel (met behulp van een sleutel die doorgaans wordt opgeslagen op een USB-flashstation [UFD])  

-   Een TPM en PINCODE  

-   Een externe opstartsleutel  

|**Geconfigureerd door de eigenschap**|||**De eigenschap is van toepassing op**||  
|-|-|-|-|-|  
|BootStrap.ini|||LTI|-|  
|CustomSettings.ini|-||||  
|MDT-DB|-||ZTI||  

|**Waarde**|**Beschrijving**|  
|-|-|  
|**TPM**|Beveilig de computer met TPM. De TPM is een microcontroller waarin sleutels, wachtwoorden en digitale certificaten wordt opgeslagen. De microcontroller is meestal een integraal onderdeel van het moederbord van de computer.|  
|**TPMKey**|De computer met TPM en een opstartsleutel te beschermen. Gebruik deze optie voor het maken van een opstartsleutel en op te slaan op een USB-Flashstation. De opstartsleutel moet aanwezig zijn in de poort telkens wanneer de computer wordt gestart.|  
|**TPMPin**|Beveilig de computer met TPM en een pincode. Gebruik deze optie in combinatie met de **BDEPin** eigenschap.|  
|**Sleutel**|Beveilig de computer met een externe sleutel (de herstelsleutel) die kan worden opgeslagen in een map in AD DS of afgedrukt.|  

|**Voorbeeld**|  
|-|   
|`[Settings] Priority=Default  [Default] BDEInstallSuppress=NO BDEDriveLetter=S: BDEDriveSize=2000 BDEInstall=TPMKey BDERecoveryKey=AD BDEKeyLocation=C:`|  

####  <a name="BDEInstallSuppress"></a>BDEInstallSuppress  
 Hiermee wordt aangegeven of het implementatieproces van de installatie van BitLocker moet worden overgeslagen.  

> [!CAUTION]
>  Waarde van deze eigenschap moet in hoofdletters worden opgegeven zodat de implementatiescripts deze goed kunnen lezen.  

|**Geconfigureerd door de eigenschap**|||**De eigenschap is van toepassing op**||  
|-|-|-|-|-|  
|BootStrap.ini|||LTI|-|  
|CustomSettings.ini|-||||  
|MDT-DB|-||ZTI||  

|**Waarde**|**Beschrijving**|  
|-|-|  
|**JA**|Probeer niet voor het installeren van BitLocker.|  
|**ER IS GEEN**|Probeert te installeren, BitLocker.|  

|**Voorbeeld**|  
|-|   
|`[Settings] Priority=Default  [Default] BDEInstallSuppress=YES`|  

####  <a name="BDEKeyLocation"></a>BDEKeyLocation  
 De locatie voor het opslaan van de BitLocker-herstelsleutel en de opstartsleutel.  

> [!NOTE]
>  Als deze eigenschap is geconfigureerd met behulp van de Wizard implementatie, moet de eigenschap de stationsletter van een verwisselbare schijf. Als de **SkipBitLocker** eigenschap is ingesteld op **TRUE** zodat de **opgeven van de configuratie van BitLocker** wizardpagina wordt overgeslagen, deze eigenschap kan worden ingesteld op een UNC-pad in CustomSettings.ini of in de MDT-database (MDT DB).  

|**Geconfigureerd door de eigenschap**|||**De eigenschap is van toepassing op**||  
|-|-|-|-|-|  
|BootStrap.ini|||LTI|-|  
|CustomSettings.ini|-||||  
|MDT-DB|-||ZTI||  

|**Waarde**|**Beschrijving**|  
|-|-|
|*Locatie*|Hiermee geeft u op waar de herstelsleutel worden opgeslagen; moet een UNC-pad of de stationsletter van een verwisselbare schijf. Als u niet is ingesteld, de eerst beschikbare verwisselbaar station gebruikt.|  

|**Voorbeeld**|  
|-|  
|`[Settings] Priority=Default  [Default] BDEInstallSuppress=NO BDEDriveLetter=S: BDEDriveSize=2000 BDEInstall=TPMKey BDERecoveryKey=AD BDEKeyLocation=C:`|  

####  <a name="BDEPin"></a>BDEPin  
 De PINCODE moet worden toegewezen aan de doelcomputer bij het configureren van BitLocker en de **BDEInstall** of **OSDBitLockerMode** eigenschappen zijn ingesteld op **TPMPin**.  

|**Geconfigureerd door de eigenschap**|||**De eigenschap is van toepassing op**||  
|-|-|-|-|-|  
|BootStrap.ini|||LTI|-|  
|CustomSettings.ini|-||||  
|MDT-DB|-||ZTI||  

|**Waarde**|**Beschrijving**|  
|-|-|
|*Pincode*|De PINCODE moet worden gebruikt voor BitLocker. De PINCODE mag tussen 4 en 20 tekens lang zijn.|  

|**Voorbeeld**|  
|-|   
|`[Settings] Priority=Default  [Default] BDEInstallSuppress=NO BDEDriveLetter=S: BDEDriveSize=2000 BDEInstall=TPMPin BDEPin=123456789`|  

####  <a name="BDERecoveryKey"></a>BDERecoveryKey  
 Een Boolean die aangeeft of het proces wordt een herstelsleutel voor BitLocker gemaakt. De sleutel wordt gebruikt voor het herstellen van gegevens op een volume BitLocker is versleuteld. Deze sleutel is cryptografisch gelijk is aan een opstartsleutel. Indien beschikbaar, ontsleutelt de herstelsleutel de volumehoofdsleutel (VMK) die op zijn beurt, de versleutelingssleutel voor volledig volume (FVEK ontsleutelt).  

> [!NOTE]
>  De herstelsleutel wordt opgeslagen in de opgegeven locatie in de **BDEKeyLocation** eigenschap.  

|**Geconfigureerd door de eigenschap**|||**De eigenschap is van toepassing op**||  
|-|-|-|-|-|  
|BootStrap.ini|||LTI|-|  
|CustomSettings.ini|-||||  
|MDT-DB|-||ZTI||  

|**Waarde**|**Beschrijving**|  
|-|-|
|**AD**|Een herstelsleutel wordt gemaakt.|  
|Niet opgegeven|Een herstelsleutel is niet gemaakt.|  

|**Voorbeeld**|  
|-|  
|`[Settings] Priority=Default  [Default] BDEInstallSuppress=NO BDEDriveLetter=S: BDEDriveSize=2000 BDEInstall=TPMKey BDERecoveryKey=AD BDEKeyLocation=C:`|  

####  <a name="BDEWaitForEncryption"></a>BDEWaitForEncryption  
 Hiermee geeft u het implementatieproces moet niet doorgaan totdat BitLocker het versleutelingsproces voor alle opgegeven schijven is voltooid. TRUE op te geven, kan de benodigde tijd voor het voltooien van het implementatieproces aanzienlijk verhogen.  

> [!CAUTION]
>  Waarde van deze eigenschap moet in hoofdletters worden opgegeven zodat de implementatiescripts deze goed kunnen lezen.  

|**Geconfigureerd door de eigenschap**|||**De eigenschap is van toepassing op**||  
|-|-|-|-|-|  
|BootStrap.ini|||LTI|-|  
|CustomSettings.ini|-||||  
|MDT-DB|-||ZTI||  

|**Waarde**|**Beschrijving**|  
|-|-|
|**DE WAARDE TRUE**|Hiermee geeft u op dat het implementatieproces totdat de stationsversleuteling wachten moet te voltooien.|  
|**DE WAARDE FALSE**|Hiermee geeft u op dat het implementatieproces niet totdat-stationsversleuteling wachten moet te voltooien.|  

|**Voorbeeld**|  
|-|  
|`[Settings] Priority=Default  [Default] BDEInstallSuppress=NO BDEDriveLetter=S: BDEDriveSize=2000 OSDBitLockerMode=TPMKey OSDBitLockerStartupKeyDrive=C: OSDBitLockerCreateRecoveryPassword=AD BDEWaitForEncryption=TRUE`|  

####  <a name="BitsPerPel"></a>BitsPerPel  
 Een instelling voor het weergeven van kleuren op de doelcomputer. De eigenschap mag cijfers en komt overeen met de instelling van de kwaliteit kleur. In het voorbeeld **32** 32-bits per pixel voor kleurkwaliteit aangeeft. Deze waarde wordt ingevoegd in de juiste configuratie-instellingen in Unattend.xml.  

> [!NOTE]
>  De standaardwaarden (in het bestand Unattend.xml-sjabloon) zijn horizontale resolutie van 1024 pixels, verticale resolutie van 768 pixels, 32-bits kleurdiepte en de verticale vernieuwingsfrequentie 60 Hertz (Hz).  

|**Geconfigureerd door de eigenschap**|||**De eigenschap is van toepassing op**||  
|-|-|-|-|-|  
|BootStrap.ini|||LTI|-|  
|CustomSettings.ini|-||||  
|MDT-DB|-||ZTI|-|  

|**Waarde**|**Beschrijving**|  
|-|-|  
|*bits_per_pixel*|Het aantal bits per pixel moet worden gebruikt voor kleuren. De standaardwaarde is de standaardwaarde voor het besturingssysteem wordt geïmplementeerd.|  

|**Voorbeeld**|  
|-|    
|`[Settings] Priority=Default  [Default] BitsPerPel=32 VRefresh=60 XResolution=1024 YResolution=768`|  

####  <a name="BuildID"></a>BuildID  
 Identificeert de takenreeks voor het besturingssysteem worden geïmplementeerd op de doelcomputer. U kunt de taak-ID maken op het knooppunt Takenreeksen in de implementatie-Workbench. De **BuildID** eigenschap kunt alfanumerieke tekens, afbreekstreepjes (-) en onderstrepingstekens (\_). De **BuildID** eigenschap mag niet leeg zijn of spaties bevatten.  

|**Geconfigureerd door de eigenschap**|||**De eigenschap is van toepassing op**||  
|-|-|-|-|-|  
|BootStrap.ini|||LTI|-|  
|CustomSettings.ini|-||||  
|MDT-DB|-||ZTI||  

|**Waarde**|**Beschrijving**|  
|-|-|  
|*build_id*|Id van de takenreeks besturingssysteem zoals gedefinieerd in de Workbench-implementatie voor het beoogde besturingssysteem wordt geïmplementeerd<br /><br /> Opmerking:<br /><br /> Zorg dat gebruiken de **TaskSequenceID** opgegeven in de implementatie-Workbench-gebruikersinterface (UI) en niet de GUID van de **TaskSequenceID**.|  

|**Voorbeeld**|  
|-|   
|`[Settings] Priority=Default  [Default] BuildID=BareMetal`|  

####  <a name="CapableArchitecture"></a>CapableArchitecture  
 De processorarchitectuur van de processor wordt ondersteund door de doelcomputer en niet de huidige processorarchitectuur die wordt uitgevoerd. Bijvoorbeeld, wanneer waarop een 32-bits-compatibel besturingssysteem op een 64-bits processor **CapableArchitecture** wordt aangegeven dat de processorarchitectuur 64-bits is.  

 Gebruik de **architectuur** eigenschap om te bekijken van de processorarchitectuur die momenteel wordt uitgevoerd.  

> [!NOTE]
>  Deze eigenschap wordt dynamisch ingesteld door de MDT-scripts en is niet geconfigureerd in CustomSettings.ini of de MDT-DB. Deze eigenschap behandelen als alleen-lezen.  

|**Geconfigureerd door de eigenschap**|||**De eigenschap is van toepassing op**||  
|-|-|-|-|-|  
|BootStrap.ini|||LTI|-|  
|CustomSettings.ini|||||  
|MDT-DB|||ZTI|-|  

|**Waarde**|**Beschrijving**|  
|-|-|   
|**x86**|Processorarchitectuur is 32-bits.|  
|**x64**|Processorarchitectuur is 64-bits.|  

|**Voorbeeld**|  
|-|   
|Geen|  

####  <a name="CaptureGroups"></a>CaptureGroups  
 Hiermee bepaalt u of het lidmaatschap van lokale groepen op de doelcomputer wordt vastgelegd. Lidmaatschap van deze groep is vastgelegd tijdens de fase voor het vastleggen van status en tijdens de fase voor het herstellen van status wordt teruggezet.  

> [!NOTE]
>  Waarde van deze eigenschap moet in hoofdletters worden opgegeven zodat de implementatiescripts deze goed kunnen lezen.  

|**Geconfigureerd door de eigenschap**|||**De eigenschap is van toepassing op**||  
|-|-|-|-|-|  
|BootStrap.ini|||LTI|-|  
|CustomSettings.ini|-||||  
|MDT-DB|-||ZTI|-|  

|**Waarde**|**Beschrijving**|  
|-|-|
|**ER IS GEEN**|Bevat geen informatie over het groepslidmaatschap.|  
|**ALLE**|Het lidmaatschap van alle lokale groepen op de doelcomputer vastgelegd.|  
|**JA**|Hiermee worden vastgelegd in het lidmaatschap van de beheerder en Hoofdgebruikers ingebouwde groepen en de groepen die worden vermeld in de eigenschappen van de groepen. Dit is de standaardwaarde als een andere waarde is opgegeven. (**Ja** is de gebruikelijke waarde.)|  

|**Voorbeeld**|  
|-|    
|`[Settings] Priority=Default  [Default] DeployRoot=\\NYC-AM-FIL-01\Distribution$ ResourceRoot=\\NYC-AM-FIL-01\Resource$ UDShare=\\NYC-AM-FIL-01\MigData$ CaptureGroups=YES Groups1=NYC Application Management Groups2=NYC Help Desk Users`|  

####  <a name="ChildName"></a>ChildName  
 Geeft aan of de DNS-label aan het begin van de naam van een bestaande directory-domein toevoegen bij het installeren van een onderliggend domein.  

|**Geconfigureerd door de eigenschap**|||**De eigenschap is van toepassing op**||  
|-|-|-|-|-|  
|BootStrap.ini|||LTI|-|  
|CustomSettings.ini|-||||  
|MDT-DB|-||ZTI|-|  

|**Waarde**|**Beschrijving**|  
|-|-|
|*naam*|De naam van het onderliggende domein|  

|**Voorbeeld**|  
|-|    
|`[Settings] Priority=Default  [Default] ChildName=childdom.parentdom.WoodGroveBank.com`|  

####  <a name="ComputerBackupLocation"></a>ComputerBackupLocation  
 De gedeelde netwerkmap waarin de back-up is opgeslagen. Als de doelmap niet al bestaat, wordt het automatisch gemaakt.  

> [!CAUTION]
>  Waarde van deze eigenschap moet in hoofdletters worden opgegeven zodat de implementatiescripts deze goed kunnen lezen.  

|**Geconfigureerd door de eigenschap**|||**De eigenschap is van toepassing op**||  
|-|-|-|-|-|  
|BootStrap.ini|||LTI|-|  
|CustomSettings.ini|-||||  
|MDT-DB|-||ZTI|-|  

|**Waarde**|**Beschrijving**|  
|-|-|  
|*lege*|Hetzelfde als **automatisch**.|  
|*UNC_path*|Het UNC-pad naar de gedeelde netwerkmap waarin de back-up is opgeslagen.|  
|**AUTO**|Maakt een back-up op een lokale vaste schijf als ruimte beschikbaar is. Anders wordt de back-up is opgeslagen in een netwerklocatie die is opgegeven in de **BackupShare** en **BackupDir** eigenschappen.|  
|**NETWERK**|Hiermee maakt u een back-up op een netwerklocatie die is opgegeven in **BackupShare** en **BackupDir**.|  
|**GEEN**|Kan geen back-up wordt uitgevoerd.|  

|**Voorbeeld**|  
|-|   
|`[Settings] Priority=Default  [Default] DeployRoot=\\NYC-AM-FIL-01\Distribution$ ResourceRoot=\\NYC-AM-FIL-01\Resource$ UDShare=\\NYC-AM-FIL-01\MigData$ ComputerBackupLocation=NETWORK BackupShare=\\NYC-AM-FIL-01\Backup$ BackupDir=%OSDComputerName% UDDir=%OSDComputerName% SLShare=\\NYC-AM-FIL-01\Logs$ UDProfiles=Administrator, User-01, ExtranetUser UserDataLocation=NONE`|  

####  <a name="ComputerName"></a>Computernaam  
 Deze eigenschap is afgeschaft. Gebruik **OSDComputerName** in plaats daarvan.  

|**Geconfigureerd door de eigenschap**|||**De eigenschap is van toepassing op**||  
|-|-|-|-|-|  
|BootStrap.ini|||LTI||  
|CustomSettings.ini|||||  
|MDT-DB|||ZTI||  

|**Waarde**|**Beschrijving**|  
|-|-|
|Geen|Geen|  

|**Voorbeeld**|  
|-|   
|Geen|  

####  <a name="ConfigFileName"></a>Bestandsnaam_config  
 Geeft de naam van het configuratiebestand gebruikt tijdens de OEM-implementaties.  

> [!NOTE]
>  Deze eigenschap wordt dynamisch ingesteld door de MDT-scripts en is niet geconfigureerd in CustomSettings.ini of de MDT-DB. Deze eigenschap behandelen als alleen-lezen.  

|**Geconfigureerd door de eigenschap**|||**De eigenschap is van toepassing op**||  
|-|-|-|-|-|  
|BootStrap.ini|||LTI|-|  
|CustomSettings.ini|||||  
|MDT-DB|||ZTI|-|  

|**Waarde**|**Beschrijving**|  
|-|-|
|*bestandsnaam*|Hiermee geeft u de naam van het configuratiebestand gebruikt tijdens de OEM-implementaties|  

|**Voorbeeld**|  
|-|  
|Geen|  

####  <a name="ConfigFilePackage"></a>ConfigFilePackage  
 Hiermee geeft u de pakket-ID voor het configuratiepakket gebruikt tijdens de OEM-implementaties.  

> [!NOTE]
>  Deze eigenschap wordt dynamisch ingesteld door de MDT-scripts en is niet geconfigureerd in CustomSettings.ini of de MDT-DB. Deze eigenschap behandelen als alleen-lezen.  

|**Geconfigureerd door de eigenschap**|||**De eigenschap is van toepassing op**||  
|-|-|-|-|-|  
|BootStrap.ini|||LTI|-|  
|CustomSettings.ini|||||  
|MDT-DB|||ZTI|-|  

|**Waarde**|**Beschrijving**|  
|-|-|  
|*pakket*|Hiermee geeft u de pakket-ID voor het configuratiepakket gebruikt tijdens de OEM-implementaties|  

|**Voorbeeld**|  
|-|   
|Geen|  

####  <a name="ConfirmGC"></a>ConfirmGC  
 Hiermee geeft u op of de replica ook een globale catalogus is.  

> [!CAUTION]
>  Waarde van deze eigenschap moet in hoofdletters worden opgegeven zodat de implementatiescripts deze goed kunnen lezen.  

|**Geconfigureerd door de eigenschap**|||**De eigenschap is van toepassing op**||  
|-|-|-|-|-|  
|BootStrap.ini|||LTI|-|  
|CustomSettings.ini|-||||  
|MDT-DB|-||ZTI|-|  

|**Waarde**|**Beschrijving**|  
|-|-|
|**JA**|Kan de replica een globale catalogus als de back-up een globale catalogus is.|  
|**ER IS GEEN**|Maakt geen de replica een globale catalogus.|  

|**Voorbeeld**|  
|-|   
|`[Settings] Priority=Default  [Default] ConfirmGC=YES`|  

####  <a name="CountryCode"></a>CountryCode  
 De landcode voor het besturingssysteem op de doelcomputer moet worden geconfigureerd. Deze eigenschap kan alleen numerieke tekens. Deze waarde wordt ingevoegd in de juiste configuratie-instellingen in Unattend.xml.  

|**Geconfigureerd door de eigenschap**|||**De eigenschap is van toepassing op**||  
|-|-|-|-|-|  
|BootStrap.ini|||LTI|-|  
|CustomSettings.ini|-||||  
|MDT-DB|-||ZTI|-|  

|**Waarde**|**Beschrijving**|  
|-|-|
|*country_code*|De landcode waar de doelcomputer wordt geïmplementeerd|  

|**Voorbeeld**|  
|-|  
|`[Settings] Priority=Default  [Default] AreaCode=206 CountryCode=001 Dialing=TONE LongDistanceAccess=9`|  

####  <a name="CriticalReplicationOnly"></a>CriticalReplicationOnly  
 Hiermee geeft u op of de promotiebewerking alleen kritieke replicatie uitvoert en vervolgens doorgaat, het niet-kritieke (en mogelijk langdurige)-gedeelte van de replicatie wordt overgeslagen.  

> [!CAUTION]
>  Waarde van deze eigenschap moet in hoofdletters worden opgegeven zodat de implementatiescripts deze goed kunnen lezen.  

|**Geconfigureerd door de eigenschap**|||**De eigenschap is van toepassing op**||  
|-|-|-|-|-|  
|BootStrap.ini|||LTI|-|  
|CustomSettings.ini|-||||  
|MDT-DB|-||ZTI|-|  

|**Waarde**|**Beschrijving**|  
|-|-|
|**JA**|Slaat het niet-kritieke replicatie|  
|**ER IS GEEN**|Niet-kritieke replicatie, wordt niet overgeslagen|  

|**Voorbeeld**|  
|-|    
|`[Settings] Priority=Default  [Default] CriticalReplicationOnly=YES`|  

####  <a name="CustomDriverSelectionProfile"></a>CustomDriverSelectionProfile  
 Hiermee geeft u de aangepaste selectie profiel wordt gebruikt tijdens de installatie van het stuurprogramma.  

|**Geconfigureerd door de eigenschap**|||**De eigenschap is van toepassing op**||  
|-|-|-|-|-|  
|BootStrap.ini|||LTI|\-|  
|CustomSettings.ini|\-||||  
|MDT-DB|\-||ZTI||  

|**Waarde**|**Beschrijving**|  
|-|-|  
|*profiel*|Aangepaste selectie profiel wordt gebruikt tijdens de installatie van stuurprogramma|  

|**Voorbeeld**|  
|-|    
|`[Settings] Priority=Default  [Default] CustomDriverSelectionProfile=CustomDrivers`|  

####  <a name="CustomPackageSelectionProfile"></a>CustomPackageSelectionProfile  
 Hiermee geeft u de aangepaste selectie profiel wordt gebruikt tijdens de pakketinstallatie van het.  

|**Geconfigureerd door de eigenschap**|||**De eigenschap is van toepassing op**||  
|-|-|-|-|-|  
|BootStrap.ini|||LTI|\-|  
|CustomSettings.ini|\-||||  
|MDT-DB|\-||ZTI||  

|**Waarde**|**Beschrijving**|  
|-|-|
|*profiel*|Aangepaste selectie profiel wordt gebruikt tijdens de pakketinstallatie van het|  

|**Voorbeeld**|  
|-|   
|`[Settings] Priority=Default  [Default] CustomPackageSelectionProfile=CustomPackages`|  

####  <a name="CustomWizardSelectionProfile"></a>CustomWizardSelectionProfile  
 Hiermee geeft u het aangepaste selectie profiel wordt gebruikt door de wizard voor het filteren van de weergave van verschillende items.  

|**Geconfigureerd door de eigenschap**|||**De eigenschap is van toepassing op**||  
|-|-|-|-|-|  
|BootStrap.ini|||LTI|\-|  
|CustomSettings.ini|\-||||  
|MDT-DB|\-||ZTI||  

|**Waarde**|**Beschrijving**|  
|-|-|  
|*profiel*|Profiel van de aangepaste selectie door de wizard voor het filteren van de weergave van verschillende items|  

|**Voorbeeld**|  
|-|   
|`[Settings] Priority=Default  [Default] CustomWizardSelectionProfile=CustomWizard`|  

####  <a name="Database"></a>Database  
 De eigenschap waarmee de database moet worden gebruikt voor het uitvoeren van query's eigenschapswaarden uit kolommen in de tabel die is opgegeven de **tabel** eigenschap. De database zich bevindt op de computer die is opgegeven in de **SQLServer** eigenschap. Het exemplaar van Microsoft SQL Server® op de computer is opgegeven in de **exemplaar** eigenschap.  

|**Geconfigureerd door de eigenschap**|||**De eigenschap is van toepassing op**||  
|-|-|-|-|-|  
|BootStrap.ini|\-||LTI|\-|  
|CustomSettings.ini|\-||||  
|MDT-DB|||ZTI|\-|  

|**Waarde**|**Beschrijving**|  
|-|-|
|*database*|De naam van de database moet worden gebruikt voor het uitvoeren van query's eigenschapswaarden|  

|**Voorbeeld**|  
|-|  
|`[Settings] Priority=Computers, Default  [Default] OSInstall=YES  [Computers] SQLServer=NYC-SQL-01 SQLShare=SQL$ Database=MDTDB Instance=SQLEnterprise2005 Table=Computers Parameters=SerialNumber, AssetTag ParameterCondition=OR`|  

####  <a name="DatabasePath"></a>DatabasePath  
 Hiermee geeft u de volledig gekwalificeerde, niet\-UNC-pad naar een map op de harde schijf van de doelcomputer die de domeindatabase bevat.  

|**Geconfigureerd door de eigenschap**|||**De eigenschap is van toepassing op**||  
|-|-|-|-|-|  
|BootStrap.ini|||LTI|\-|  
|CustomSettings.ini|\-||||  
|MDT-DB|\-||ZTI|\-|  

|**Waarde**|**Beschrijving**|  
|-|-|
|*pad*|Hiermee geeft u de volledig gekwalificeerde, niet\-UNC-pad naar een map op de harde schijf van de lokale computer die de domeindatabase bevat|  

|**Voorbeeld**|  
|-|  
|`[Settings] Priority=Default  [Default] DatabasePath=%DestinationLogicalDrive%\Windows\NTSD`|  

####  <a name="DBID"></a>DATABASE-ID  
 Hiermee geeft u het gebruikersaccount waarmee verbinding met de computer met SQL Server \(opgegeven door de **SQLServer** eigenschap\) met behulp van SQL Server-verificatie. De **DBPwd** eigenschap geeft u het wachtwoord voor het gebruikersaccount in de **DBID** eigenschap.  

> [!NOTE]
>  SQL Server-verificatie is niet zo veilig geïntegreerde Windows-verificatie. Geïntegreerde Windows-verificatie is de aanbevolen verificatiemethode. Met behulp van de **DBID** en **DBPwd** eigenschappen slaat de referenties in gewone tekst in het bestand CustomSettings.ini en daarom is niet beveiligd. Zie voor meer informatie over het gebruik van geïntegreerde Windows-verificatie, de [SQLShare](#SQLShare) eigenschap.  

> [!NOTE]
>  Deze eigenschap is alleen kunnen worden geconfigureerd als u handmatig de bestanden CustomSettings.ini en BootStrap.ini te bewerken.  

|**Geconfigureerd door de eigenschap**|||**De eigenschap is van toepassing op**||  
|-|-|-|-|-|  
|BootStrap.ini|\-||LTI|\-|  
|CustomSettings.ini|\-||||  
|MDT-DB|||ZTI|\-|  

|**Waarde**|**Beschrijving**|  
|-|-|
|*gebruiker\_id*|De naam van de referenties van de gebruiker gebruikt voor toegang tot de computer met SQL Server met behulp van SQL Server-verificatie|  

|**Voorbeeld**|  
|-|  
|`[Settings] Priority=Computers, Default  [Default] OSInstall=YES  [Computers] SQLServer=NYC-SQL-01 DBID=SQL_User-01 DBPwd=<complex_password> NetLib=DBNMPNTW Database=MDTDB Instance=SQLEnterprise2005 Table=Computers Parameters=SerialNumber, AssetTag ParameterCondition=OR`|  

####  <a name="DBPwd"></a>DBPwd  
 Hiermee geeft u het wachtwoord voor de gebruikersaccount die is opgegeven in de **DBID** eigenschap. De **DBID** en **DBPwd** eigenschappen van de referenties voor het uitvoeren van SQL Server-verificatie aan de computer met SQL Server bieden \(opgegeven door de **SQLServer**  eigenschap\).  

> [!NOTE]
>  SQL Server-verificatie is niet zo veilig geïntegreerde Windows-verificatie. Geïntegreerde Windows-verificatie is de aanbevolen verificatiemethode. Met behulp van de **DBID** en **DBPwd** eigenschappen slaat de referenties in gewone tekst in het bestand CustomSettings.ini en daarom is niet beveiligd. Zie voor meer informatie over het gebruik van geïntegreerde Windows-verificatie, de [SQLShare](#SQLShare) eigenschap.  

> [!NOTE]
>  Deze eigenschap is alleen kunnen worden geconfigureerd als u handmatig de bestanden CustomSettings.ini en BootStrap.ini te bewerken.  

|**Geconfigureerd door de eigenschap**|||**De eigenschap is van toepassing op**||  
|-|-|-|-|-|  
|BootStrap.ini|\-||LTI|\-|  
|CustomSettings.ini|\-||||  
|MDT-DB|||ZTI|\-|  

|**Waarde**|**Beschrijving**|  
|-|-|
|*gebruiker\_wachtwoord*|Het wachtwoord voor de referenties van de gebruiker opgegeven in de **DBID** eigenschap voor het gebruik van SQL Server-verificatie|  

|**Voorbeeld**|  
|-|    
|`[Settings] Priority=Computers, Default  [Default] OSInstall=YES  [Computers] SQLServer=NYC-SQL-01 DBID=SQL_User-01 DBPwd=<complex_password> NetLib=DBNMPNTW Database=MDTDB Instance=SQLEnterprise2005 Table=Computers Parameters=SerialNumber, AssetTag ParameterCondition=OR`|  

####  <a name="Debug"></a>Fouten opsporen  
 Hiermee bepaalt u het uitbreidingsniveau van berichten die naar de MDT-logboekbestanden geschreven. Deze eigenschap kan worden geconfigureerd om te helpen bij het oplossen van implementaties op basis van uitgebreide informatie over het implementatieproces MDT.  

 U kunt deze eigenschap instellen op basis van het script dat LiteTouch.vbs de  **\/debug: true** opdracht\-regel parameter als volgt:  

```  
cscript.exe LiteTouch.vbs /debug:true  
```  

 Nadat het script LiteTouch.vbs is gestart, de **Debug** waarde van de eigenschap is ingesteld op **TRUE**, en alle andere scripts automatisch de waarde van deze eigenschap worden gelezen en uitgebreide informatie te bieden.  

> [!NOTE]
>  Deze eigenschap wordt dynamisch ingesteld door de MDT-scripts en is niet geconfigureerd in CustomSettings.ini of in de MDT-DB. Deze eigenschap behandelen als alleen-lezen.  

|**Geconfigureerd door de eigenschap**|||**De eigenschap is van toepassing op**||  
|-|-|-|-|-|  
|BootStrap.ini|||LTI|\-|  
|CustomSettings.ini|||||  
|MDT-DB|||ZTI|\-|  

|**Waarde**|**Beschrijving**|  
|-|-|
|**DE WAARDE TRUE**|Fouten opsporen in logboekregistratie is ingeschakeld, waaronder het volgende:<br /><br /> \-Uitgebreide berichten worden geregistreerd.<br /><br /> \-Afgeschafte berichten worden geregistreerd als fouten.|  
|**DE WAARDE FALSE**|Fouten opsporen in logboekregistratie is niet ingeschakeld. Dit is de standaardwaarde.|  

|**Voorbeeld**|  
|-|   
|Geen|  

####  <a name="DefaultGateway"></a>Standaard-gateway  
 Het IP-adres van de standaardgateway wordt gebruikt door de doelcomputer. De indeling van het IP-adres geretourneerd door de eigenschap is standaard scheidingspunten\-decimale notatie, bijvoorbeeld 192.168.1.1. Gebruik deze eigenschap te maken van een subsectie met instellingen die zijn gericht op een groep computers op basis van de IP-subnetten waarop ze zich bevinden.  

> [!NOTE]
>  Deze eigenschap wordt dynamisch ingesteld door de MDT-scripts en de waarde is ingesteld in CustomSettings.ini of de MDT-DB kan hebben. Deze eigenschap behandelen als alleen-lezen. Echter kunt u deze eigenschap binnen CustomSettings.ini of de MDT-database, zoals wordt weergegeven in de volgende voorbeelden om te helpen bij het definiëren van de configuratie van de doelcomputer.  

|**Geconfigureerd door de eigenschap**|||**De eigenschap is van toepassing op**||  
|-|-|-|-|-|  
|BootStrap.ini|||LTI|\-|  
|CustomSettings.ini|||||  
|MDT-DB|||ZTI|\-|  

|**Waarde**|**Beschrijving**|  
|-|-|
|*standaard\_gateway*|Het IP-adres van de standaardgateway in de standaard met\-decimale notatie|  

|**Voorbeeld**|  
|-|   
|`[Settings] Priority=DefaultGateway, Default  [Default] OSInstall=YES  [DefaultGateway] 192.168.0.1=HOUSTON 11.1.1.11=REDMOND 172.28.20.1=REDMOND  [REDMOND] Packages001=XXX00004:Program4 Packages002=XXX00005:Program5  [HOUSTON] Packages001=XXX00006:Program6 Packages002=XXX00007:Program7 Packages003=XXX00008:Program8`|  

####  <a name="DeployDrive"></a>DeployDrive  
 De waarde die door de scripts worden gebruikt voor toegang tot bestanden en programma's uitvoeren in de implementatieshare maakt voor de implementatie-Workbench. De eigenschap retourneert de stationsletter die is toegewezen aan de **DeployRoot** eigenschap. ZTIApplications.wsf gebruikt de **DeployDrive** eigenschap bij het uitvoeren van een opdracht\-programma's met de extensie .cmd of .bat regel.  

> [!NOTE]
>  Deze eigenschap wordt dynamisch ingesteld door de MDT-scripts en is niet geconfigureerd in CustomSettings.ini of de MDT-DB. Deze eigenschap behandelen als alleen-lezen.  

|**Geconfigureerd door de eigenschap**|||**De eigenschap is van toepassing op**||  
|-|-|-|-|-|  
|BootStrap.ini|||LTI|\-|  
|CustomSettings.ini|||||  
|MDT-DB|||ZTI|\-|  

|**Waarde**|**Beschrijving**|  
|-|-|
|*station\_letter*|De aanwijzing letter voor de logische schijf waarop het beoogde besturingssysteem wordt geïnstalleerd \(zoals C of D\)|  

|**Voorbeeld**|  
|-|  
|Geen|  

####  <a name="DeploymentMethod"></a>DeploymentMethod  
 De methode die wordt gebruikt voor de implementatie (UNC-, media of Configuration Manager).  

> [!NOTE]
>  Deze eigenschap wordt dynamisch ingesteld door de MDT-scripts en is niet geconfigureerd in CustomSettings.ini of de MDT-DB. Deze eigenschap behandelen als alleen-lezen.  

> [!CAUTION]
>  Waarde van deze eigenschap moet in hoofdletters worden opgegeven zodat de implementatiescripts deze goed kunnen lezen.  

|**Geconfigureerd door de eigenschap**|||**De eigenschap is van toepassing op**||  
|-|-|-|-|-|  
|BootStrap.ini|||LTI|-|  
|CustomSettings.ini|||||  
|MDT-DB|||ZTI|-|  

|**Waarde**|**Beschrijving**|  
|-|-|  
|**UNC**|De implementatie wordt uitgevoerd op de doelcomputer via het netwerk.|  
|**Media**|De implementatie wordt uitgevoerd vanaf de lokale media (zoals DVD of harde schijf) op de doelcomputer.|  
|**SCCM**|ZTI gebruikt deze methode voor Configuration Manager.|  

|**Voorbeeld**|  
|-|   
|Geen|  

####  <a name="DeploymentType"></a>DeploymentType  
 Het type van de implementatie wordt uitgevoerd op basis van het scenario van implementatie. Voor ZTI, wordt deze eigenschap dynamisch wordt ingesteld door de MDT-scripts en is niet geconfigureerd in CustomSettings.ini. Voor LTI, kunt u de pagina in de Wizard implementatie waarvoor het implementatietype wordt geselecteerd overslaan. Bovendien kunt u het implementatietype opgeven door een van de waarden die worden vermeld onder aan het script LiteTouch.wsf als een opdrachtregeloptie wordt doorgegeven.  

> [!CAUTION]
>  Waarde van deze eigenschap moet in hoofdletters worden opgegeven zodat de implementatiescripts deze goed kunnen lezen.  

|**Geconfigureerd door de eigenschap**|||**De eigenschap is van toepassing op**||  
|-|-|-|-|-|  
|BootStrap.ini|||LTI|-|  
|CustomSettings.ini|-||||  
|MDT-DB|||ZTI|-|  

|**Waarde**|**Beschrijving**|  
|-|-|
|**NEWCOMPUTER**|De doelcomputer is een nieuwe computer die nooit een lid van het netwerk is.|  
|**VERNIEUWEN**|De doelcomputer is een bestaande computer in het netwerk waarvoor u de standaard bureaubladomgeving moeten worden geïmplementeerd.|  
|**VERVANGEN**|Een bestaande computer in het netwerk wordt vervangen door een nieuwe computer. De statusmigratiegegevens overgebracht van een bestaande computer naar een nieuwe computer.|  

|**Voorbeeld**|  
|-|  
|`[Settings] Priority=Default  [Default] DeploymentType=NEWCOMPUTER`|  

####  <a name="DeployRoot"></a>DeployRoot  
 Hiermee geeft u de UNC of lokale pad naar de map die de hoofdmap van de mapstructuur die gebruikmaakt van MDT is. Deze mapstructuur bevat configuratiebestanden, scripts, en andere mappen en bestanden die MDT worden gebruikt. De waarde van deze eigenschap is ingesteld op basis van de volgende technologieën van de MDT-implementatie:  

-   **LTI**. Deze eigenschap is het UNC-pad naar de implementatieshare die de implementatie-Workbench worden gemaakt. Gebruik deze eigenschap in een specifieke implementatie-share kiezen. De meest voorkomende gebruik van deze eigenschap is in het bestand BootStrap.ini naar een implementatieshare identificeren voordat de verbinding met de implementatieshare tot stand is gebracht. Alle mappen van andere deployment share zijn ten opzichte van deze eigenschap (zoals apparaatstuurprogramma's, taalpakketten of besturingssystemen).  

-   **ZTI**. Deze eigenschap is het lokale pad naar de map waarnaar het pakket van de MDT-bestanden worden gekopieerd. De **gebruik Toolkit pakket** takenreeksstap, wordt het pakket van de MDT-bestanden naar een lokale map op de doelcomputer gekopieerd en vervolgens automatisch stelt deze eigenschap op de lokale map.  

    > [!NOTE]
    >  Voor ZTI, wordt deze eigenschap dynamisch wordt ingesteld door de MDT-scripts en is niet geconfigureerd in CustomSettings.ini of in de MDT-database. Deze eigenschap behandelen als alleen-lezen.  

|**Geconfigureerd door de eigenschap**|||**De eigenschap is van toepassing op**||  
|-|-|-|-|-|  
|BootStrap.ini|-||LTI|-|  
|CustomSettings.ini|||||  
|MDT-DB|||ZTI|-|  

|**Waarde**|**Beschrijving**|  
|-|-|
|*pad*|De UNC of lokale pad naar de.|  

|**Voorbeeld**|  
|-|  
|`[Settings] Priority=Default  [Default] DeployRoot=\\NYC-AM-FIL-01\Distribution$ UserDataLocation=NONE`|  

####  <a name="DestinationDisk"></a>DestinationDisk  
 Nummer van de schijf die de installatiekopie wordt geïmplementeerd.  

|**Geconfigureerd door de eigenschap**|||**De eigenschap is van toepassing op**||  
|-|-|-|-|-|  
|BootStrap.ini|-||LTI|-|  
|CustomSettings.ini|-||||  
|MDT-DB|||ZTI||  

|**Waarde**|**Beschrijving**|  
|-|-|  
|*disk_number*|Het nummer van de schijf waarop de installatiekopie wordt geïmplementeerd|  

|**Voorbeeld**|  
|-|   
|`[Settings] Priority=Default  [Default] DestinationDisk=0`|  

####  <a name="DestinationLogicalDrive"></a>DestinationLogicalDrive  
 De logische schijf waarop de installatiekopie wordt geïmplementeerd.  

|**Geconfigureerd door de eigenschap**|||**De eigenschap is van toepassing op**||  
|-|-|-|-|-|  
|**Geconfigureerd door de eigenschap**|||**De eigenschap is van toepassing op**||  
|BootStrap.ini|-||LTI|-|  
|CustomSettings.ini|-||||  
|MDT-DB|||ZTI||  

|**Waarde**|**Beschrijving**|  
|-|-|   
|*logical_drive_number*|De logische schijf waarop de installatiekopie wordt geïmplementeerd|  

|**Voorbeeld 1**|  
|-|   
|`[Settings] Priority=Default  [Default] DestinationLogicalDrive=0`|  

|**Voorbeeld 2**|  
|-|  
|`[Settings] Priority=Default  [Default] DestinationLogicalDrive=0`<br /><br /> `[Settings] Priority=Default  [Default] InstallDNS=YES DomainNetBIOSName=WoodGroveBank NewDomain=Child DomainLevel=3 ForestLevel=3 NewDomainDNSName=newdom.WoodGroveBank.com ParentDomainDNSName=WoodGroveBank.com AutoConfigDNS=YES ConfirmGC=YES CriticalReplicationOnly=NO ADDSUserName=Administrator ADDSUserDomain=WoodGroveBank ADDSPassword=<complex_password> DatabasePath=%DestinationLogicalDrive%\Windows\NTDS ADDSLogPath=%DestinationLogicalDrive%\Windows\NTDS SysVolPath=%DestinationLogicalDrive%\Windows\SYSVOL SafeModeAdminPassword=<complex_password>`|  

####  <a name="DestinationPartition"></a>DestinationPartition  
 Schijfpartitie waarop de installatiekopie wordt geïmplementeerd.  

|**Geconfigureerd door de eigenschap**|||**De eigenschap is van toepassing op**||  
|-|-|-|-|-|  
|BootStrap.ini|-||LTI|-|  
|CustomSettings.ini|-||||  
|MDT-DB|||ZTI||  

|**Waarde**|**Beschrijving**|  
|-|-|  
|*partition_number*|Het nummer van de partitie waarop de installatiekopie wordt geïmplementeerd|  

|**Voorbeeld**|  
|-|  
|`[Settings] Priority=Default  [Default] DestinationPartition=1`|  

####  <a name="DHCPScopes"></a>DHCPScopes  
 Hiermee geeft u het nummer van de DHCP-scopes om te configureren.  

|**Geconfigureerd door de eigenschap**|||**De eigenschap is van toepassing op**||  
|-|-|-|-|-|  
|BootStrap.ini|||LTI|-|  
|CustomSettings.ini|-||||  
|MDT-DB|-||ZTI|-|  

|**Waarde**|**Beschrijving**|  
|-|-|   
|*scopes*|Hiermee geeft u het nummer van de DHCP-scopes configureren|  

|**Voorbeeld**|  
|-|  
|`[Settings] Priority=Default  [Default] DHCPScopes=1`|  

####  <a name="DHCPScopesxDescription"></a>DHCPScopesxDescription  
 De beschrijving van de DHCP-scope.  

> [!NOTE]
>  De *x* in de eigenschappen van deze naam is een tijdelijke aanduiding voor een op nul gebaseerde matrix met DHCP-configuraties.  

|**Geconfigureerd door de eigenschap**|||**De eigenschap is van toepassing op**||  
|-|-|-|-|-|  
|BootStrap.ini|||LTI|-|  
|CustomSettings.ini|-||||  
|MDT-DB|-||ZTI|-|  

|**Waarde**|**Beschrijving**|  
|-|-|  
|*Beschrijving*|De beschrijving van de DHCP-scope|  

|**Voorbeeld**|  
|-|  
|`[Settings] Priority=Default  [Default] DHCPScopes0Description=DHCPScope0`|  

####  <a name="DHCPScopesxEndIP"></a>DHCPScopesxEndIP  
 Hiermee geeft u het laatste IP-adres voor de DHCP-scope.  

 De *x* in de eigenschappen van deze naam is een tijdelijke aanduiding voor een op nul gebaseerde matrix met DHCP-configuraties.  

|**Geconfigureerd door de eigenschap**|||**De eigenschap is van toepassing op**||  
|-|-|-|-|-|  
|BootStrap.ini|||LTI|-|  
|CustomSettings.ini|-||||  
|MDT-DB|-||ZTI|-|  

|**Waarde**|**Beschrijving**|  
|-|-|
|*end_IP*|Hiermee geeft u het laatste IP-adres voor de DHCP-scope|  

|**Voorbeeld**|  
|-|   
|`[Settings] Priority=Default  [Default] DHCPScopes0EndIP=192.168.0.30`|  

####  <a name="DHCPScopesxExcludeEndIP"></a>DHCPScopesxExcludeEndIP  
 Hiermee geeft u het laatste IP-adres voor de uitsluiting van de DHCP-scope. IP-adressen die zijn uitgesloten van het bereik zijn niet aangeboden door de DHCP-server aan clients die leases van dit bereik.  

> [!NOTE]
>  De *x* in de eigenschappen van deze naam is een tijdelijke aanduiding voor een op nul gebaseerde matrix met DHCP-configuraties.  

|**Geconfigureerd door de eigenschap**|||**De eigenschap is van toepassing op**||  
|-|-|-|-|-|  
|BootStrap.ini|||LTI|-|  
|CustomSettings.ini|-||||  
|MDT-DB|-||ZTI|-|  

|**Waarde**|**Beschrijving**|  
|-|-|   
|*exclude_end_IP*|Hiermee geeft u het laatste IP-adres voor de uitsluiting van de DHCP-scope|  

|**Voorbeeld**|  
|-|   
|`[Settings] Priority=Default  [Default] DHCPScopes0ExcludeEndIP=192.168.0.15`|  

####  <a name="DHCPScopesxExcludeStartIP"></a>DHCPScopesxExcludeStartIP  
 Hiermee geeft u het eerste IP-adres voor de uitsluiting van de DHCP-scope. IP-adressen die zijn uitgesloten van het bereik zijn niet aangeboden door de DHCP-server aan clients die leases van dit bereik.  

> [!NOTE]
>  De *x* in de eigenschappen van deze naam is een tijdelijke aanduiding voor een op nul gebaseerde matrix met DHCP-configuraties.  

|**Geconfigureerd door de eigenschap**|||**De eigenschap is van toepassing op**||  
|-|-|-|-|-|  
|BootStrap.ini|||LTI|-|  
|CustomSettings.ini|-||||  
|MDT-DB|-||ZTI|-|  

|**Waarde**|**Beschrijving**|  
|-|-|
|*exclude_start_IP*|Hiermee geeft u het eerste IP-adres voor de uitsluiting van de DHCP-scope|  

|**Voorbeeld**|  
|-|    
|`[Settings] Priority=Default  [Default] DHCPScopes0ExcludeStartIP=192.168.0.10`|  

####  <a name="DHCPScopesxIP"></a>DHCPScopesxIP  
 Hiermee geeft u het IP-subnet van het bereik.  

 De *x* in de eigenschappen van deze naam is een tijdelijke aanduiding voor een op nul gebaseerde matrix met DHCP-configuraties.  

|**Geconfigureerd door de eigenschap**|||**De eigenschap is van toepassing op**||  
|-|-|-|-|-|  
|BootStrap.ini|||LTI|-|  
|CustomSettings.ini|-||||  
|MDT-DB|-||ZTI|-|  

|**Waarde**|**Beschrijving**|  
|-|-|
|*IP*|Hiermee geeft u het IP-subnet van het bereik|  

|**Voorbeeld**|  
|-|   
|`[Settings] Priority=Default  [Default] DHCPScopes0IP=192.168.0.0`|  

####  <a name="DHCPScopesxName"></a>DHCPScopesxName  
 De naam van een gebruiker te definiëren moet worden toegewezen aan het bereik.  

 De *x* in de eigenschappen van deze naam is een tijdelijke aanduiding voor een op nul gebaseerde matrix met DHCP-configuraties.  

|**Geconfigureerd door de eigenschap**|||**De eigenschap is van toepassing op**||  
|-|-|-|-|-|  
|BootStrap.ini|||LTI|-|  
|CustomSettings.ini|-||||  
|MDT-DB|-||ZTI|-|  

|**Waarde**|**Beschrijving**|  
|-|-|  
|*naam*|De naam van een gebruiker te definiëren moet worden toegewezen aan het bereik|  

|**Voorbeeld**|  
|-|   
|`[Settings] Priority=Default  [Default] DHCPScopes0Name=DHCPScope0`|  

####  <a name="DHCPScopesxOptionDNSDomainName"></a>DHCPScopesxOptionDNSDomainName  
 Hiermee geeft u de domeinnaam die de DHCP-client gebruiken moet tijdens het omzetten van niet-gekwalificeerde domeinnamen met de DNS-server.  

> [!NOTE]
>  De *x* in de eigenschappen van deze naam is een tijdelijke aanduiding voor een op nul gebaseerde matrix met DHCP-configuraties.  

|**Geconfigureerd door de eigenschap**|||**De eigenschap is van toepassing op**||  
|-|-|-|-|-|  
|BootStrap.ini|||LTI|-|  
|CustomSettings.ini|-||||  
|MDT-DB|-||ZTI|-|  

|**Waarde**|**Beschrijving**|  
|-|-|  
|*DNS_domeinnaam*|Hiermee geeft u de domeinnaam die de DHCP-client gebruiken moet tijdens het omzetten van niet-gekwalificeerde domeinnamen met de DNS-server|  

|**Voorbeeld**|  
|-|  
|`[Settings] Priority=Default  [Default] DHCPScopes0OptionDNSDomainName=WoodGroveBank.com`|  

####  <a name="DHCPScopesxOptionDNSServer"></a>DHCPScopesxOptionDNSServer  
 Hiermee geeft u een lijst met IP-adressen voor DNS-naamservers die beschikbaar zijn voor de client. Wanneer meer dan één server is toegewezen, wordt de client worden geïnterpreteerd en de adressen in de opgegeven volgorde worden gebruikt.  

> [!NOTE]
>  De *x* in de eigenschappen van deze naam is een tijdelijke aanduiding voor een op nul gebaseerde matrix met DHCP-configuraties.  

|**Geconfigureerd door de eigenschap**|||**De eigenschap is van toepassing op**||  
|-|-|-|-|-|  
|BootStrap.ini|||LTI|-|  
|CustomSettings.ini|-||||  
|MDT-DB|-||ZTI|-|  

|**Waarde**|**Beschrijving**|  
|-|-|
|*DNS_server*|Hiermee wordt een lijst met IP-adressen voor DNS-naamservers die beschikbaar zijn voor de client|  

|**Voorbeeld**|  
|-|   
|`[Settings] Priority=Default  [Default] DHCPScopes0OptionDNSServer=192.168.0.2`|  

####  <a name="DHCPScopesxOptionLease"></a>DHCPScopesxOptionLease  
 De duur die de DHCP-lease geldig voor de client is.  

> [!NOTE]
>  De *x* in de eigenschappen van deze naam is een tijdelijke aanduiding voor een op nul gebaseerde matrix met DHCP-configuraties.  

|**Geconfigureerd door de eigenschap**|||**De eigenschap is van toepassing op**||  
|-|-|-|-|-|  
|BootStrap.ini|||LTI|-|  
|CustomSettings.ini|-||||  
|MDT-DB|-||ZTI|-|  

|**Waarde**|**Beschrijving**|  
|-|-|  
|*lease*|De duur die de DHCP-lease geldig voor de client is|  

|**Voorbeeld**|  
|-|  
|`[Settings] Priority=Default  [Default] DHCPScopes0OptionLease=7`|  

####  <a name="DHCPScopesxOptionNBTNodeType"></a>DHCPScopesxOptionNBTNodeType  
 Hiermee geeft u het type client knooppunt NetBT-clients.  

> [!NOTE]
>  De *x* in de eigenschappen van deze naam is een tijdelijke aanduiding voor een op nul gebaseerde matrix met DHCP-configuraties.  

|**Geconfigureerd door de eigenschap**|||**De eigenschap is van toepassing op**||  
|-|-|-|-|-|  
|BootStrap.ini|||LTI|-|  
|CustomSettings.ini|-||||  
|MDT-DB|-||ZTI|-|  

|**Waarde**|**Beschrijving**|  
|-|-|
|**1**|Het knooppunttype configureert als b-knooppunt|  
|**2**|Hiermee configureert u het knooppunttype als p-knooppunt|  
|**4**|Hiermee configureert u het knooppunttype als m-knooppunt|  
|**8**|Het knooppunttype configureert als h-knooppunt|  

|**Voorbeeld**|  
|-|   
|`[Settings] Priority=Default  [Default] DHCPScopes0OptionNBTNodeType=4`|  

####  <a name="DHCPScopesxOptionPXEClient"></a>DHCPScopesxOptionPXEClient  
 Hiermee geeft u het IP-adres gebruikt voor PXE-client-bootstrapcode.  

> [!NOTE]
>  De *x* in de eigenschappen van deze naam is een tijdelijke aanduiding voor een op nul gebaseerde matrix met DHCP-configuraties.  

|**Geconfigureerd door de eigenschap**|||**De eigenschap is van toepassing op**||  
|-|-|-|-|-|  
|BootStrap.ini|||LTI|-|  
|CustomSettings.ini|-||||  
|MDT-DB|-||ZTI|-|  

|**Waarde**|**Beschrijving**|  
|-|-|   
|*PXE_client*|Hiermee geeft u het IP-adres gebruikt voor PXE-client-bootstrapcode|  

|**Voorbeeld**|  
|-|   
|`[Settings] Priority=Default  [Default] DHCPScopes0OptionPXEClient=192.168.0.252`|  

####  <a name="DHCPScopesxOptionRouter"></a>DHCPScopesxOptionRouter  
 Hiermee geeft u een lijst met IP-adressen voor routers op het subnet van de client. Wanneer meer dan één router wordt toegewezen, wordt de client worden geïnterpreteerd en de adressen in de opgegeven volgorde worden gebruikt. Deze optie wordt normaal gesproken gebruikt voor het toewijzen van een standaardgateway aan DHCP-clients in een subnet.  

> [!NOTE]
>  De *x* in de eigenschappen van deze naam is een tijdelijke aanduiding voor een op nul gebaseerde matrix met DHCP-configuraties.  

|**Geconfigureerd door de eigenschap**|||**De eigenschap is van toepassing op**||  
|-|-|-|-|-|  
|BootStrap.ini|||LTI|-|  
|CustomSettings.ini|-||||  
|MDT-DB|-||ZTI|-|  

|**Waarde**|**Beschrijving**|  
|-|-|
|*router*|Hiermee wordt een lijst met IP-adressen voor routers op het subnet van de client|  

|**Voorbeeld**|  
|-|  
|`[Settings] Priority=Default  [Default] DHCPScopes0OptionRouter=192.168.0.253`|  

####  <a name="DHCPScopesxOptionWINSServer"></a>DHCPScopesxOptionWINSServer  
 Hiermee geeft u de IP-adressen moet worden gebruikt voor NBNSes op het netwerk.  

> [!NOTE]
>  De *x* in de eigenschappen van deze naam is een tijdelijke aanduiding voor een op nul gebaseerde matrix met DHCP-configuraties  

|**Geconfigureerd door de eigenschap**|||**De eigenschap is van toepassing op**||  
|-|-|-|-|-|  
|BootStrap.ini|||LTI|-|  
|CustomSettings.ini|-||||  
|MDT-DB|-||ZTI|-|  

|**Waarde**|**Beschrijving**|  
|-|-|  
|*WINS_server*|Hiermee geeft u de IP-adressen moet worden gebruikt voor NBNSes op het netwerk|  

|**Voorbeeld**|  
|-|  
|`[Settings] Priority=Default  [Default] DHCPScopes0OptionWINSServer=192.168.0.2`|  

####  <a name="DHCPScopesxStartIP"></a>DHCPScopesxStartIP  
 Het eerste IP-adres voor het bereik van IP-adressen die moeten worden opgenomen in het bereik.  

> [!NOTE]
>  De *x* in de eigenschappen van deze naam is een tijdelijke aanduiding voor een op nul gebaseerde matrix met DHCP-configuraties.  

|**Geconfigureerd door de eigenschap**|||**De eigenschap is van toepassing op**||  
|-|-|-|-|-|  
|BootStrap.ini|||LTI|-|  
|CustomSettings.ini|-||||  
|MDT-DB|-||ZTI|-|  

|**Waarde**|**Beschrijving**|  
|-|-|  
|*start_IP*|Het eerste IP-adres voor het bereik van IP-adressen op die moeten worden uitgesloten van het bereik|  

|**Voorbeeld**|  
|-|   
|`[Settings] Priority=Default  [Default] DHCPScopes0StartIP=192.168.0.20`|  

####  <a name="DHCPScopesxSubnetMask"></a>DHCPScopesxSubnetMask  
 Hiermee geeft u het subnetmasker van het clientsubnet.  

> [!NOTE]
>  De *x* in de eigenschappen van deze naam is een tijdelijke aanduiding voor een op nul gebaseerde matrix met DHCP-configuraties.  

|**Geconfigureerd door de eigenschap**|||**De eigenschap is van toepassing op**||  
|-|-|-|-|-|  
|BootStrap.ini|||LTI|-|  
|CustomSettings.ini|-||||  
|MDT-DB|-||ZTI|-|  

|**Waarde**|**Beschrijving**|  
|-|-|  
|*subnet_mask*|Hiermee wordt het subnetmasker van de client-IP-subnet|  

|**Voorbeeld**|  
|-|   
|`[Settings] Priority=Default  [Default] DHCPScopes0SubnetMask=255.255.255.0`|  

####  <a name="DHCPServerOptionDNSDomainName"></a>DHCPServerOptionDNSDomainName  
 Hiermee geeft u het verbindingsspecifieke DNS-domeinachtervoegsel van clientcomputers.  

|**Geconfigureerd door de eigenschap**|||**De eigenschap is van toepassing op**||  
|-|-|-|-|-|    
|BootStrap.ini|||LTI|-|  
|CustomSettings.ini|-||||  
|MDT-DB|-||ZTI|-|  

|**Waarde**|**Beschrijving**|  
|-|-|   
|*DNS_domeinnaam*|Hiermee geeft u het verbindingsspecifieke DNS-domeinachtervoegsel van clientcomputers|  

|**Voorbeeld**|  
|-|    
|`[Settings] Priority=Default  [Default] DHCPServerOptionDNSDomainName=Fabrikam.com`|  

####  <a name="DHCPServerOptionDNSServer"></a>DHCPServerOptionDNSServer  
 Hiermee geeft u een lijst met IP-adressen worden gebruikt als de DNS-naamservers die beschikbaar voor de client zijn.  

|**Geconfigureerd door de eigenschap**|||**De eigenschap is van toepassing op**||  
|-|-|-|-|-|  
|BootStrap.ini|||LTI|-|  
|CustomSettings.ini|-||||  
|MDT-DB|-||ZTI|-|  

|**Waarde**|**Beschrijving**|  
|-|-|
|*DNS_server*|Hiermee wordt een lijst met IP-adressen worden gebruikt als de DNS-naamservers die beschikbaar voor de client zijn|  

|**Voorbeeld**|  
|-|   
|`[Settings] Priority=Default  [Default] DHCPServerOptionDNSServer=192.168.0.1,192.168.0.2`|  

####  <a name="DHCPServerOptionNBTNodeType"></a>DHCPServerOptionNBTNodeType  
 Hiermee geeft u het type client knooppunt NetBT-clients.  

|**Geconfigureerd door de eigenschap**|||**De eigenschap is van toepassing op**||  
|-|-|-|-|-|  
|BootStrap.ini|||LTI|-|  
|CustomSettings.ini|-||||  
|MDT-DB|-||ZTI|-|  

|**Waarde**|**Beschrijving**|  
|-|-|   
|**1**|Het knooppunttype configureert als b-knooppunt|  
|**2**|Hiermee configureert u het knooppunttype als p-knooppunt|  
|**4**|Hiermee configureert u het knooppunttype als m-knooppunt|  
|**8**|Het knooppunttype configureert als h-knooppunt|  

|**Voorbeeld**|  
|-|  
|`[Settings] Priority=Default  [Default] DHCPServerOptionNBTNodeType=4`|  

####  <a name="DHCPServerOptionPXEClient"></a>DHCPServerOptionPXEClient  
 Hiermee geeft u het IP-adres gebruikt voor PXE-client-bootstrapcode.  

|**Geconfigureerd door de eigenschap**|||**De eigenschap is van toepassing op**||  
|-|-|-|-|-|  
|BootStrap.ini|||LTI|-|  
|CustomSettings.ini|-||||  
|MDT-DB|-||ZTI|-|  

|**Waarde**|**Beschrijving**|  
|-|-|
|*PXE_client*|Hiermee geeft u het IP-adres gebruikt voor PXE-client-bootstrapcode|  

|**Voorbeeld**|  
|-|    
|`[Settings] Priority=Default  [Default] DHCPServerOptionPXEClient=192.168.0.252`|  

####  <a name="DHCPServerOptionRouter"></a>DHCPServerOptionRouter  
 Hiermee geeft u een lijst met IP-adressen voor routers op het subnet van de client. Wanneer meer dan één router wordt toegewezen, wordt de client worden geïnterpreteerd en de adressen in de opgegeven volgorde worden gebruikt. Deze optie wordt normaal gesproken gebruikt voor het toewijzen van een standaardgateway aan DHCP-clients in een subnet.  

|**Geconfigureerd door de eigenschap**|||**De eigenschap is van toepassing op**||  
|-|-|-|-|-|  
|BootStrap.ini|||LTI|-|  
|CustomSettings.ini|-||||  
|MDT-DB|-||ZTI|-|  

|**Waarde**|**Beschrijving**|  
|-|-|  
|*router*|Hiermee wordt een lijst met IP-adressen voor routers op het subnet van de client|  

|**Voorbeeld**|  
|-|   
|`[Settings] Priority=Default  [Default] DHCPServerOptionRouter=192.168.0.253`|  

####  <a name="DHCPServerOptionWINSServer"></a>DHCPServerOptionWINSServer  
 Hiermee geeft u de IP-adressen moet worden gebruikt voor NBNSes op het netwerk.  

|**Geconfigureerd door de eigenschap**|||**De eigenschap is van toepassing op**||  
|-|-|-|-|-|  
|BootStrap.ini|||LTI|-|  
|CustomSettings.ini|-||||  
|MDT-DB|-||ZTI|-|  

|**Waarde**|**Beschrijving**|  
|-|-|    
|*WINS_server*|Hiermee geeft u de IP-adressen moet worden gebruikt voor NBNSes op het netwerk|  

|**Voorbeeld**|  
|-|  
|`[Settings] Priority=Default  [Default] DHCPServerOptionWINSServer=192.168.0.2`|  

####  <a name="Dialing"></a>Nummer inspreken  
 Het type kiezen die worden ondersteund door de telephony-infrastructuur waar de doelcomputer zich bevindt. Deze waarde wordt ingevoegd in de juiste configuratie-instellingen in Unattend.xml.  

> [!CAUTION]
>  Waarde van deze eigenschap moet in hoofdletters worden opgegeven zodat de implementatiescripts deze goed kunnen lezen.  

|**Geconfigureerd door de eigenschap**|||**De eigenschap is van toepassing op**||  
|-|-|-|-|-|  
|BootStrap.ini|||LTI|-|  
|CustomSettings.ini|-||||  
|MDT-DB|-||ZTI|-|  

|**Waarde**|**Beschrijving**|  
|-|-|  
|**PULSE**|De telephony-infrastructuur ondersteunt pulse kiezen.|  
|**TOON**|De telephony-infrastructuur ondersteunt nu kiezen.|  

|**Voorbeeld**|  
|-|   
|`[Settings] Priority=Default  [Default] AreaCode=206 CountryCode=001 Dialing=TONE LongDistanceAccess=9`|  

####  <a name="DisableTaskMgr"></a>DisableTaskMgr  
 Deze eigenschap bepaalt de mogelijkheid van een gebruiker Taakbeheer starten door op CTRL + ALT + DEL te drukken. Nadat de gebruiker Taakbeheer is gestart, kan hij of zij de takenreeks LTI onderbroken tijdens het uitvoeren van het nieuwe besturingssysteem op de doelcomputer. Deze eigenschap wordt gebruikt in combinatie met de **HideShell** eigenschap en is alleen geldig wanneer de **HideShell** eigenschap is ingesteld op **Ja**.  

> [!NOTE]
>  Deze eigenschap en de **HideShell** eigenschap moet beide worden ingesteld op **Ja** om te voorkomen dat de gebruiker op CTRL + ALT + DEL te drukken en onderbreken van de LTI takenreeks.  

|**Geconfigureerd door de eigenschap**|||**De eigenschap is van toepassing op**||  
|-|-|-|-|-|  
|BootStrap.ini|||LTI|-|  
|CustomSettings.ini|-||||  
|MDT-DB|-||ZTI||  

|**Waarde**|**Beschrijving**|  
|-|-|   
|**JA**|Voorkomen dat de gebruiker kunnen worden Taakbeheer starten door op CTRL + ALT + DEL te drukken en vervolgens de takenreeks LTI te onderbreken.|  
|**ER IS GEEN**|Toestaan dat de gebruiker Taakbeheer starten door op CTRL + ALT + DEL te drukken en vervolgens de takenreeks LTI te onderbreken. Dit is de standaardwaarde.|  

|**Voorbeeld**|  
|-|  
|`[Settings] Priority=Default  [Default] DisableTaskMgr=YES HideShell=YES`|  

####  <a name="DNSServerOptionBINDSecondaries"></a>DNSServerOptionBINDSecondaries  
 Bepaalt of de indeling voor snelle overdracht gebruiken voor overdracht van een zone naar DNS-servers waarop oudere BIND-implementaties.  

 Standaard gebruiken alle Windows gebaseerde DNS-servers in een indeling voor snelle zoneoverdracht. Deze indeling maakt gebruik van compressie, en kan meerdere records per TCP-bericht tijdens de overdracht van een verbonden bevatten. Deze indeling is ook compatibel met meer recente BIND gebaseerde DNS-servers waarop versie 4.9.4 en hoger.  

> [!CAUTION]
>  Waarde van deze eigenschap moet in hoofdletters worden opgegeven zodat de implementatiescripts deze goed kunnen lezen.  

|**Geconfigureerd door de eigenschap**|||**De eigenschap is van toepassing op**||  
|-|-|-|-|-|  
|BootStrap.ini|||LTI|-|  
|CustomSettings.ini|-||||  
|MDT-DB|-||ZTI|-|  

|**Waarde**|**Beschrijving**|  
|-|-|   
|**DE WAARDE TRUE**|Kan binding secundaire replica 's|  
|**DE WAARDE FALSE**|Kan geen voor BIND secundaire replica 's|  

|**Voorbeeld**|  
|-|  
|`[Settings] Priority=Default  [Default] DNSServerOptionBINDSecondaries=TRUE`|  

####  <a name="DNSServerOptionDisableRecursion"></a>DNSServerOptionDisableRecursion  
 Hiermee wordt bepaald of de DNS-server recursie gebruikt. De DNS-Server-service is standaard ingeschakeld om recursie te gebruiken.  

> [!CAUTION]
>  Waarde van deze eigenschap moet in hoofdletters worden opgegeven zodat de implementatiescripts deze goed kunnen lezen.  

|**Geconfigureerd door de eigenschap**|||**De eigenschap is van toepassing op**||  
|-|-|-|-|-|  
|BootStrap.ini|||LTI|-|  
|CustomSettings.ini|-||||  
|MDT-DB|-||ZTI|-|  

|**Waarde**|**Beschrijving**|  
|-|-|    
|**DE WAARDE TRUE**|De recursie wordt uitgeschakeld op de DNS-server|  
|**DE WAARDE FALSE**|Hiermee recursie op de DNS-server|  

|**Voorbeeld**|  
|-|  
|`[Settings] Priority=Default  [Default] DNSServerOptionDisableRecursion=TRUE`|  

####  <a name="DNSServerOptionEnableNetmaskOrdering"></a>DNSServerOptionEnableNetmaskOrdering  
 Hiermee wordt bepaald of de DNS-server (A) adresbronrecords binnen dezelfde resourcerecord dat is ingesteld in het antwoord van de server aan een query op basis van het IP-adres van de bron van de query volgorde.  

 De DNS Server-service gebruikt standaard, lokale subnet prioriteit aan bestellen A-bronrecords.  

> [!CAUTION]
>  Waarde van deze eigenschap moet in hoofdletters worden opgegeven zodat de implementatiescripts deze goed kunnen lezen.  

|**Geconfigureerd door de eigenschap**|||**De eigenschap is van toepassing op**||  
|-|-|-|-|-|  
|BootStrap.ini|||LTI|-|  
|CustomSettings.ini|-||||  
|MDT-DB|-||ZTI|-|  

|**Waarde**|**Beschrijving**|  
|-|-|  
|**DE WAARDE TRUE**|Hiermee netmask-ordening|  
|**DE WAARDE FALSE**|Schakelt netmask-ordening|  

|**Voorbeeld**|  
|-|  
|`[Settings] Priority=Default  [Default] DNSServerOptionEnableNetmaskOrdering=TRUE`|  

####  <a name="DNSServerOptionEnableRoundRobin"></a>DNSServerOptionEnableRoundRobin  
 Hiermee wordt bepaald of de DNS-server gebruikmaakt van het mechanisme voor round-robin draaien en een lijst met bronrecords opnieuw ordenen als er bestaan meerdere bronrecords van hetzelfde type die beschikbaar zijn voor een query-antwoord.  

 De DNS Server-service gebruikt standaard round robin.  

> [!CAUTION]
>  Waarde van deze eigenschap moet in hoofdletters worden opgegeven zodat de implementatiescripts deze goed kunnen lezen.  

|**Geconfigureerd door de eigenschap**|||**De eigenschap is van toepassing op**||  
|-|-|-|-|-|  
|BootStrap.ini|||LTI|-|  
|CustomSettings.ini|-||||  
|MDT-DB|-||ZTI|-|  

|**Waarde**|**Beschrijving**|  
|-|-|  
|**DE WAARDE TRUE**|Round-robin kunt|  
|**DE WAARDE FALSE**|Round-robin uitgeschakeld|  

|**Voorbeeld**|  
|-|  
|`[Settings] Priority=Default  [Default] DNSServerOptionEnableRoundRobin=TRUE`|  

####  <a name="DNSServerOptionEnableSecureCache"></a>DNSServerOptionEnableSecureCache  
 Bepaalt of de DNS-server probeert om op te schonen antwoorden te vermijden. Deze instelling is standaard ingeschakeld. DNS-servers gebruiken standaard een antwoordoptie voor beveiligd waarmee toe te voegen niet-gerelateerde bronrecords die zijn opgenomen in een referentie-antwoord aan de cache. Alle namen die zijn toegevoegd in referral-antwoorden worden meestal in cache opgeslagen in de meeste gevallen en helpen de resolutie van de volgende DNS-query's te versnellen.  

 Met deze functie kan de server echter bepalen dat namen potentieel vervuilend of onveilig en deze vervolgens te verwijderen. De server bepaalt of de naam die wordt aangeboden in een verwijzing op basis van of het deel uitmaakt van de exacte, gerelateerde, DNS-naam domeinstructuur waarvoor de oorspronkelijke naam van de query is gemaakt in de cache.  

> [!CAUTION]
>  Waarde van deze eigenschap moet in hoofdletters worden opgegeven zodat de implementatiescripts deze goed kunnen lezen.  

|**Geconfigureerd door de eigenschap**|||**De eigenschap is van toepassing op**||  
|-|-|-|-|-|  
|BootStrap.ini|||LTI|-|  
|CustomSettings.ini|-||||  
|MDT-DB|-||ZTI|-|  

|**Waarde**|**Beschrijving**|  
|-|-|   
|**DE WAARDE TRUE**|Kan cache beveiliging|  
|**DE WAARDE FALSE**|Beveiliging in de cache wordt uitgeschakeld|  

|**Voorbeeld**|  
|-|   
|`[Settings] Priority=Default  [Default] DNSServerOptionEnableSecureCache=TRUE`|  

####  <a name="DNSServerOptionFailOnLoad"></a>DNSServerOptionFailOnLoad  
 Hiermee geeft u op dat bij het laden van een zone mislukken moet wanneer beschadigde gegevens zijn gevonden.  

> [!CAUTION]
>  Waarde van deze eigenschap moet in hoofdletters worden opgegeven zodat de implementatiescripts deze goed kunnen lezen.  

|**Geconfigureerd door de eigenschap**|||**De eigenschap is van toepassing op**||  
|-|-|-|-|-|  
|BootStrap.ini|||LTI|-|  
|CustomSettings.ini|-||||  
|MDT-DB|-||ZTI|-|  

|**Waarde**|**Beschrijving**|  
|-|-|    
|**DE WAARDE TRUE**|Schakel bij het laden is mislukt|  
|**DE WAARDE FALSE**|Schakel bij het laden is mislukt|  

|**Voorbeeld**|  
|-|   
|`[Settings] Priority=Default  [Default] DNSServerOptionFailOnLoad=TRUE`|  

####  <a name="DNSServerOptionNameCheckFlag"></a>DNSServerOptionNameCheckFlag  
 Geeft aan welke tekenstandaard wordt gebruikt bij het controleren van de DNS-namen.  

|**Geconfigureerd door de eigenschap**|||**De eigenschap is van toepassing op**||  
|-|-|-|-|-|  
|BootStrap.ini|||LTI|-|  
|CustomSettings.ini|-||||  
|MDT-DB|-||ZTI|-|  

|**Waarde**|**Beschrijving**|  
|-|-|  
|**0**|Maakt gebruik van ANSI-tekens in overeenstemming zijn met Internet Engineering Task Force (IETF) Request for Comments (RFC's). Deze waarde komt overeen met de **Strict RFC (ANSI)** selectie bij het configureren van DNS in de implementatie-Workbench.|  
|**1**|Maakt gebruik van ANSI-tekens die niet noodzakelijkerwijs voldoen aan de IETF RFC's. Deze waarde komt overeen met de **niet RFC (ANSI)** selectie bij het configureren van DNS in de implementatie-Workbench.|  
|**2**|Maakt gebruik van multibytetekens UCS Transformation Format 8 (UTF-8). Dit is de standaardinstelling. Deze waarde komt overeen met de **Multibyte (UTF-8)** selectie bij het configureren van DNS in de implementatie-Workbench.|  
|**3**|Maakt gebruik van alle tekens. Deze waarde komt overeen met de **alle namen** selectie bij het configureren van DNS in de implementatie-Workbench.|  

|**Voorbeeld**|  
|-|  
|`[Settings] Priority=Default  [Default] DNSServerOptionNameCheckFlag=2`|  

####  <a name="DNSZones"></a>DNSZones  
 Hiermee geeft u het aantal DNS-zones te configureren.  

|**Geconfigureerd door de eigenschap**|||**De eigenschap is van toepassing op**||  
|-|-|-|-|-|  
|BootStrap.ini|||LTI|-|  
|CustomSettings.ini|-||||  
|MDT-DB|-||ZTI|-|  

|**Waarde**|**Beschrijving**|  
|-|-|  
|*zones*|Hiermee geeft u het aantal DNS-zones configureren|  

|**Voorbeeld**|  
|-|  
|`[Settings] Priority=Default  [Default] DNSZones=1 DNSZones0Name=MyNewZone DNSZones0DirectoryPartition=Forest DNSZones0FileName=MyNewZone.dns DNSZones0MasterIP=192.168.0.1,192.168.0.2 DNSZones0Type=Secondary`|  

####  <a name="DNSZonesxDirectoryPartition"></a>DNSZonesxDirectoryPartition  
 Hiermee geeft u de directorypartitie op die voor het opslaan van de zone bij het configureren van secundaire of stub-zones.  

> [!NOTE]
>  De *x* in de eigenschappen van deze naam is een tijdelijke aanduiding voor een op nul gebaseerde matrix met DNS-configuraties.  

|**Geconfigureerd door de eigenschap**|||**De eigenschap is van toepassing op**||  
|-|-|-|-|-|  
|BootStrap.ini|||LTI|-|  
|CustomSettings.ini|-||||  
|MDT-DB|-||ZTI|-|  

|**Waarde**|**Beschrijving**|  
|-|-|
|**Domein**|Zonegegevens worden gerepliceerd naar alle DNS-server in de AD DS-domein|  
|**Forest**|Zonegegevens worden gerepliceerd naar alle DNS-server in de AD DS-forest|  
|**Verouderde**|Zonegegevens worden gerepliceerd naar alle domeincontrollers in het AD DS-domein|  

|**Voorbeeld**|  
|-|
|`[Settings] Priority=Default  [Default] DNSZones0DirectoryPartition=Forest`|  

####  <a name="DNSZonesxFileName"></a>DNSZonesxFileName  
 Hiermee geeft u de naam van het bestand waarin gegevens van de zone wordt opgeslagen.  

> [!NOTE]
>  De *x* in de eigenschappen van deze naam is een tijdelijke aanduiding voor een op nul gebaseerde matrix met DNS-configuraties.  

|**Geconfigureerd door de eigenschap**|||**De eigenschap is van toepassing op**||  
|-|-|-|-|-|  
|BootStrap.ini|||LTI|-|  
|CustomSettings.ini|-||||  
|MDT-DB|-||ZTI|-|  

|**Waarde**|**Beschrijving**|  
|-|-|
|*bestandsnaam*|Geeft de naam van het bestand waarin gegevens van de zone wordt opgeslagen|  

|**Voorbeeld**|  
|-|
|`[Settings] Priority=Default  [Default] DNSZones0FileName=MyNewZone.dns`|  

####  <a name="DNSZonesxMasterIP"></a>DNSZonesxMasterIP  
 Een door komma's gescheiden lijst met IP-adressen van de master-servers moet worden gebruikt door de DNS-server bij het bijwerken van de opgegeven secundaire zones. Deze eigenschap moet worden opgegeven bij het configureren van een secundaire of stub-DNS-zone.  

> [!NOTE]
>  De *x* in de eigenschappen van deze naam is een tijdelijke aanduiding voor een op nul gebaseerde matrix met DNS-configuraties.  

|**Geconfigureerd door de eigenschap**|||**De eigenschap is van toepassing op**||  
|-|-|-|-|-|  
|BootStrap.ini|||LTI|-|  
|CustomSettings.ini|-||||  
|MDT-DB|-||ZTI|-|  

|**Waarde**|**Beschrijving**|  
|-|-|
|*IP1, IP2*|Een door komma's gescheiden lijst met IP-adressen van de master-servers|  

|**Voorbeeld**|  
|-|   
|`[Settings] Priority=Default  [Default] DNSZones0MasterIP=192.168.0.1,192.168.0.2`|  

####  <a name="DNSZonesxName"></a>DNSZonesxName  
 Hiermee geeft u de naam van de zone.  

> [!NOTE]
>  De *x* in de eigenschappen van deze naam is een tijdelijke aanduiding voor een op nul gebaseerde matrix met DNS-configuraties.  

|**Geconfigureerd door de eigenschap**|||**De eigenschap is van toepassing op**||  
|-|-|-|-|-|  
|BootStrap.ini|||LTI|-|  
|CustomSettings.ini|-||||  
|MDT-DB|-||ZTI|-|  

|**Waarde**|**Beschrijving**|  
|-|-|
|*naam*|Hiermee geeft u de naam van de zone|  

|**Voorbeeld**|  
|-|  
|`[Settings] Priority=Default  [Default] DNSZones0Name=MyNewZone`|  

####  <a name="DNSZonesxScavenge"></a>DNSZonesxScavenge  
 Hiermee configureert u de primaire DNS-server om te verlopen records 'opruimen' — dat wil zeggen, om te zoeken naar de records die zijn en verwijdert u deze in de database.  

> [!NOTE]
>  De *x* in de eigenschappen van deze naam is een tijdelijke aanduiding voor een op nul gebaseerde matrix met DNS-configuraties.  

|**Geconfigureerd door de eigenschap**|||**De eigenschap is van toepassing op**||  
|-|-|-|-|-|  
|BootStrap.ini|||LTI|-|  
|CustomSettings.ini|-||||  
|MDT-DB|-||ZTI|-|  

|**Waarde**|**Beschrijving**|  
|-|-|
|**DE WAARDE TRUE**|Verlopen DNS-records voor het opruimen toestaan.|  
|**DE WAARDE FALSE**|Verlopen DNS-records voor het opruimen is niet toegestaan.|  

|**Voorbeeld**|  
|-|  
|`[Settings] Priority=Default  [Default] DNSZones0Scavenge=TRUE`|  

#### <a name="dnszonesxtype"></a>DNSZonesxType  
 Hiermee geeft u het type zone te maken.  

> [!NOTE]
>  De *x* in de eigenschappen van deze naam is een tijdelijke aanduiding voor een op nul gebaseerde matrix met DNS-configuraties.  

|**Geconfigureerd door de eigenschap**|||**De eigenschap is van toepassing op**||  
|-|-|-|-|-|  
|BootStrap.ini|||LTI|-|  
|CustomSettings.ini|-||||  
|MDT-DB|-||ZTI|-|  

|**Waarde**|**Beschrijving**|  
|-|-|
|**DSPrimary**|Hiermee maakt u een primaire zone en op te geven dat deze moet worden opgeslagen in AD DS op een DNS-server geconfigureerd als een domeincontroller|  
|**DSStub**|Maakt een stub-zone en op te geven dat deze moet worden opgeslagen in AD DS op een DNS-server geconfigureerd als een domeincontroller|  
|**Primaire**|Maakt u een primaire zone|  
|**Secundair**|Maakt u een secundaire zone|  
|**Stub**|Maakt een stub-zone|  

|**Voorbeeld**|  
|-|
|`[Settings] Priority=Default  [Default] DNSZones0Type=Secondary`|  

####  <a name="DNSZonesxUpdate"></a>DNSZonesxUpdate  
 Hiermee configureert u de primaire DNS-server om uit te voeren dynamische updates.  

> [!NOTE]
>  De *x* in de eigenschappen van deze naam is een tijdelijke aanduiding voor een op nul gebaseerde matrix met DNS-configuraties.  

|**Geconfigureerd door de eigenschap**|||**De eigenschap is van toepassing op**||  
|-|-|-|-|-|  
|BootStrap.ini|||LTI|-|  
|CustomSettings.ini|-||||  
|MDT-DB|-||ZTI|-|  

|**Waarde**|**Beschrijving**|  
|-|-|  
|**0**|Geen toestaan dynamische updates|  
|**1**|Dynamische updates toestaat|  
|**2**|Hiermee kunt beveiligde dynamische updates|  

|**Voorbeeld**|  
|-|  
|`[Settings] Priority=Default  [Default] DNSZones0Update=1`|  

####  <a name="DoCapture"></a>DoCapture  
 Geeft aan of een installatiekopie van de doelcomputer moet worden vastgelegd. Als dit het geval is, wordt Sysprep uitgevoerd op de doelcomputer om voor te bereiden voor het maken van de installatiekopie. Nadat Sysprep is uitgevoerd, een nieuw WIM-installatiekopie is gemaakt en opgeslagen in de map in de gedeelde map voor back-ups van doel aangewezen (**BackupDir** en **BackupShare**respectievelijk).  

> [!CAUTION]
>  Waarde van deze eigenschap moet in hoofdletters worden opgegeven zodat de implementatiescripts deze goed kunnen lezen.  

|**Geconfigureerd door de eigenschap**|||**De eigenschap is van toepassing op**||  
|-|-|-|-|-|  
|BootStrap.ini|||LTI|-|  
|CustomSettings.ini|-||||  
|MDT-DB|-||ZTI|-|  

|**Waarde**|**Beschrijving**|  
|-|-|
|**JA**|Kopieer de benodigde bestanden voor Sysprep uitgevoerd op de doelcomputer, Sysprep uitgevoerd op de doelcomputer en vastleggen van een WIM-installatiekopie.|  
|**ER IS GEEN**|Voer Sysprep niet op de doelcomputer en niet een WIM-installatiekopie vastlegt.|  
|**VOORBEREIDEN**|Kopieer de benodigde bestanden voor Sysprep uitgevoerd op de doelcomputer, maar niet Sysprep of andere processen installatiekopie vastleggen wordt uitgevoerd.|  
|**SYSPREP**|Kopieer de benodigde bestanden Sysprep wilt uitvoeren op de doelcomputer, Sysprep uitgevoerd op de doelcomputer, maar niet een WIM-installatiekopie vastlegt.<br /><br /> Opmerking:<br /><br /> Het voornaamste doel van deze waarde is dat het maken van een VHD met een besturingssysteem nadat Sysprep is uitgevoerd en u geen installatiekopie vast te leggen hoeft.|  

|**Voorbeeld**|  
|-|  
|`[Settings] Priority=Default  [Default] DoCapture=YES DeployRoot=\\NYC-AM-FIL-01\Distribution$ ResourceRoot=\\NYC-AM-FIL-01\Resource$ UDShare=\\NYC-AM-FIL-01\MigData$ UDDir=%OSDComputerName%`|  

####  <a name="DomainAdmin"></a>DomainAdmin  
 De referenties van de gebruiker gebruikt voor het toevoegen van de doelcomputer aan het domein dat is opgegeven in **JoinDomain**. Geef als *gebruikersnaam*.  

> [!NOTE]
>  Voor ZTI, worden de referenties die Configuration Manager gewoonlijk geeft gebruikt. Als de **DomainAdmin** eigenschap is opgegeven, de referenties in de **DomainAdmin** eigenschap overschrijven de referenties waarmee Configuration Manager.  

|**Geconfigureerd door de eigenschap**|||**De eigenschap is van toepassing op**||  
|-|-|-|-|-|  
|BootStrap.ini|||LTI|-|  
|CustomSettings.ini|-||||  
|MDT-DB|-||ZTI|-|  

|**Waarde**|**Beschrijving**|  
|-|-|
|*domeinbeheerder*|De naam van de referenties van de gebruiker|  

|**Voorbeeld**|  
|-|   
|`[Settings] Priority=Default  [Default] DomainAdmin=NYCAdmin DomainAdminDomain=WOODGROVEBANK DomainAdminPassword=<complex_password>`|  

####  <a name="DomainAdminDomain"></a>DomainAdminDomain  
 Het domein waarin de referenties van de gebruiker die zijn opgegeven in **DomainAdmin** zich bevinden.  

> [!NOTE]
>  Voor ZTI, worden de referenties die Configuration Manager gewoonlijk geeft gebruikt. Als de **DomainAdmin** eigenschap is opgegeven, de referenties in de **DomainAdmin** eigenschap overschrijven de referenties waarmee Configuration Manager.  

|**Geconfigureerd door de eigenschap**|||**De eigenschap is van toepassing op**||  
|-|-|-|-|-|  
|BootStrap.ini|||LTI|-|  
|CustomSettings.ini|-||||  
|MDT-DB|-||ZTI|-|  

|**Waarde**|**Beschrijving**|  
|-|-|
|*domain_admin_domain*|De naam van het domein waar de referenties van de gebruiker zich bevinden|  

|**Voorbeeld**|  
|-|   
|`[Settings] Priority=Default  [Default] DomainAdmin=NYCAdmin DomainAdminDomain=WOODGROVEBANK DomainAdminPassword=<complex_password>`|  

####  <a name="DomainAdminPassword"></a>DomainAdminPassword  
 Het wachtwoord voor het domein Administrator-account opgegeven in de **DomainAdmin** eigenschap in op de computer toevoegen aan het domein.  

> [!NOTE]
>  Voor ZTI, worden de referenties die Configuration Manager gewoonlijk geeft gebruikt. Als de **DomainAdmin** eigenschap is opgegeven, de referenties in de **DomainAdmin** eigenschap overschrijven de referenties waarmee Configuration Manager.  

|**Geconfigureerd door de eigenschap**|||**De eigenschap is van toepassing op**||  
|-|-|-|-|-|  
|BootStrap.ini|||LTI|-|  
|CustomSettings.ini|-||||  
|MDT-DB|-||ZTI|-|  

|**Waarde**|**Beschrijving**|  
|-|-|
|*domain_admin_password*|Het wachtwoord voor het domein Administrator-account op de doelcomputer|  

|**Voorbeeld**|  
|-|  
|`[Settings] Priority=Default  [Default] DomainAdmin=NYCAdmin DomainAdminDomain=WOODGROVEBANK DomainAdminPassword=<complex_password>`|  

####  <a name="DomainLevel"></a>DomainLevel  
 Deze vermelding geeft aan dat het functionele domeinniveau. Dit item is gebaseerd op de niveaus die in het forest voorkomen wanneer u een nieuw domein maakt in een bestaand forest.  

|**Geconfigureerd door de eigenschap**|||**De eigenschap is van toepassing op**||  
|-|-|-|-|-|  
|BootStrap.ini|||LTI|-|  
|CustomSettings.ini|-||||  
|MDT-DB|-||ZTI|-|  

|**Waarde**|**Beschrijving**|  
|-|-|  
|*Niveau*|Stelt het domeinfunctionaliteitsniveau op een van de volgende:<br /><br /> -2, WindowsServer 2003<br /><br /> -3, WindowsServer 2008<br /><br /> -4, Windows Server 2008 R2<br /><br /> -5, WindowsServer 2012|  

|**Voorbeeld**|  
|-|
|`[Settings] Priority=Default  [Default] DomainLevel=3`|  

####  <a name="DomainNetBiosName"></a>DomainNetBiosName  
 Een NetBIOS-naam toegewezen aan het nieuwe domein.  

|**Geconfigureerd door de eigenschap**|||**De eigenschap is van toepassing op**||  
|-|-|-|-|-|  
|BootStrap.ini|||LTI|-|  
|CustomSettings.ini|-||||  
|MDT-DB|-||ZTI|-|  

|**Waarde**|**Beschrijving**|  
|-|-|
|*Naam*|Een NetBIOS-naam toegewezen aan het nieuwe domein|  

|**Voorbeeld**|  
|-|
|`[Settings] Priority=Default  [Default] DomainNetBiosName=NewDom`|  

####  <a name="DomainOUs"></a>DomainOUs  
 Een lijst met AD DS organisatie-eenheden (OE's) waar de doel-computeraccount kan worden gemaakt. De **DomainOUs** eigenschap een lijst met tekstwaarden die elke niet-lege waarde. De **DomainOUs** eigenschap heeft een numeriek achtervoegsel (bijvoorbeeld **DomainOUs1** of **DomainOUs2**). De opgegeven waarden van DomainOUs worden weergegeven in de Wizard implementatie en geselecteerd door de gebruiker. De **MachineObjectOU** eigenschap wordt vervolgens worden ingesteld op de organisatie-eenheid geselecteerd.  

 Bovendien kan dezelfde functionaliteit worden geleverd door het configureren van het bestand DomainOUList.xml. De indeling van het bestand DomainOUList.xml is als volgt:  

```  
<?xml version="1.0" encoding="utf-8"?>  
<DomainOUs>  
<DomainOU>  
  OU=Computers,OU=Tellers,OU=NYC,DC=WOODGROVEBANK,DC=Com  
</DomainOU>  
<DomainOU>  
  OU=Computers,OU=Managers,OU=NYC,DC=WOODGROVEBANK,DC=Com  
</DomainOU>  
</DomainOUs>  
```  

|**Geconfigureerd door de eigenschap**|||**De eigenschap is van toepassing op**||  
|-|-|-|-|-|  
|BootStrap.ini|||LTI|-|  
|CustomSettings.ini|-||||  
|MDT-DB|||ZTI||  

|**Waarde**|**Beschrijving**|  
|-|-|
|*ORGANISATIE-EENHEID*|De organisatie-eenheid waarin de doel-computeraccount kan worden gemaakt|  

|**Voorbeeld**|  
|-|  
|`[Settings] Priority=Default  [Default] OSInstall=Y DomainOUs1=OU=Computers, OU=Tellers, OU=NYC, DC=WOODGROVEBANK, DC=Com DomainOUs2=OU=Computers, OU=Managers, OU=NYC, DC=WOODGROVEBANK, DC=Com`|  

####  <a name="DoNotCreateExtraPartition"></a>DoNotCreateExtraPartition  
 Hiermee geeft u aan implementaties van Windows 7 en Windows Server 2008 R2 wordt niet gemaakt voor de systeempartitie 300 MB.  

> [!CAUTION]
>  Waarde van deze eigenschap moet in hoofdletters worden opgegeven zodat de implementatiescripts deze goed kunnen lezen.  

|**Geconfigureerd door de eigenschap**|||**De eigenschap is van toepassing op**||  
|-|-|-|-|-|  
|BootStrap.ini|||LTI|-|  
|CustomSettings.ini|-||||  
|MDT-DB|-||ZTI||  

|**Waarde**|**Beschrijving**|  
|-|-|  
|**JA**|De aanvullende systeempartitie wordt niet gemaakt.|  
|**ER IS GEEN**|De aanvullende systeempartitie wordt gemaakt.|  

|**Voorbeeld**|  
|-|   
|`[Settings] Priority=Default  [Default] OSInstall=Y DoNotCreateExtraPartition=YES`|  

> [!NOTE]
>  Gebruik geen deze eigenschap in combinatie met eigenschappen voor het configureren van instellingen voor BitLocker.  

####  <a name="DoNotFormatAndPartition"></a>DoNotFormatAndPartition  
 Deze eigenschap wordt configureren of MDT voert een van de takenreeksstappen partitioneren en formatteren in takenreeksen die zijn gemaakt met behulp van de MDT-taaksjablonen reeks gebruikt.  

> [!CAUTION]
>  Waarde van deze eigenschap moet in hoofdletters worden opgegeven zodat de implementatiescripts deze goed kunnen lezen.  

|**Geconfigureerd door de eigenschap**|||**De eigenschap is van toepassing op**||  
|-|-|-|-|-|  
|BootStrap.ini|||LTI|-|  
|CustomSettings.ini|-||||  
|MDT-DB|-||ZTI||  

|**Waarde**|**Beschrijving**|  
|-|-|  
|**JA**|Het partitioneren en formatteren van takenreeksstappen in een takenreeks MDT worden uitgevoerd.|  
|*Een andere waarde*|Het partitioneren en formatteren van takenreeksstappen in een takenreeks MDT wordt niet uitgevoerd. Dit is de standaardwaarde.|  

|**Voorbeeld**|  
|-|
|`[Settings] Priority=Default  [Default] OSInstall=YES SkipUserData=YES USMTOfflineMigration=TRUE DoNotFormatAndPartition=YES OSDStateStorePath=\\WDG-MDT-01\StateStore$`|  

####  <a name="DriverGroup"></a>DriverGroup  
 Een lijst met tekstwaarden die wordt gekoppeld aan de out-of-box stuurprogramma's die zijn gemaakt in de implementatie-Workbench met elkaar (meestal op basis van het merk en model van een computer). Een stuurprogramma kan worden gekoppeld aan een of meer stuurprogrammagroepen. De **DriverGroup** eigenschap kunt u de stuurprogramma's in een of meer groepen worden geïmplementeerd op een doelcomputer.  

 De tekstwaarden in de lijst mag niet-lege waarde. De **DriverGroup** eigenschapswaarde heeft een numeriek achtervoegsel (bijvoorbeeld **DriverGroup001** of **DriverGroup002**). Nadat deze is gedefinieerd, is een stuurprogrammagroep gekoppeld aan een computer. Een computer kan worden gekoppeld aan meer dan één stuurprogrammagroep.  

 Bijvoorbeeld: Er zijn twee secties voor elk van de computerfabrikant [Mfgr01] en [Mfgr02]. Twee stuurprogrammagroepen zijn gedefinieerd voor de fabrikant Mfgr01: Mfgr01 Video's en Mfgr01 netwerk-stuurprogramma's. Voor de producent Mfgr02 één stuurprogrammagroep is gedefinieerd, Mfgr02 stuurprogramma's. Een stuurprogrammagroep gedeeld stuurprogramma's wordt toegepast op alle computers die zijn gevonden in de sectie [standaard].  

|**Geconfigureerd door de eigenschap**|||**De eigenschap is van toepassing op**||  
|-|-|-|-|-|  
|BootStrap.ini|||LTI|-|  
|CustomSettings.ini|-||||  
|MDT-DB|-||ZTI||  

|**Waarde**|**Beschrijving**|  
|-|-|
|*driver_group_name*|De naam van de stuurprogrammagroep is gedefinieerd in de Workbench-implementatie|  

|**Voorbeeld**|  
|-|
|`[Settings] Priority=Make, Default  [Default] DriverGroup001=Shared Drivers :: [Mfgr01] DriverGroup001=Mfgr01 Video Drivers DriverGroup002=Mfgr01 Network Drivers  [Mfgr02] DriverGroup001=Mfgr02 Drivers`|  

####  <a name="DriverInjectionMode"></a>DriverInjectionMode  
 Deze eigenschap wordt gebruikt om te bepalen van de apparaatstuurprogramma's die worden ingevoegd door de [stuurprogramma's invoeren](#InjectDrivers) takenreeksstap.  

|**Geconfigureerd door de eigenschap**|||**De eigenschap is van toepassing op**||  
|-|-|-|-|-|  
|BootStrap.ini|||LTI|-|  
|CustomSettings.ini|-||||  
|MDT-DB|-||ZTI||  

|**Waarde**|**Beschrijving**|  
|-|-|
|Auto|Alleen overeenkomende stuurprogramma's uit de selectie profiel of de map invoeren.  Dit is de werking van MDT 2008, die alle stuurprogramma's die overeenkomen met een van de plug en play (PnP)-id's op de doelcomputer injects.|  
|Alle|Alle stuurprogramma's in de map of selectie profiel invoeren.|  

|**Voorbeeld**|  
|-|   
|`[Settings] Priority=Default  [Default] DriverInjectionMode=ALL DriverSelectionProfile=Nothing DriverPaths001=\\NYC-AM-FIL-01\Drivers$ DriverPaths002=\\NYC-AM-FIL-03\WinDrvs`|  

####  <a name="DriverPaths"></a>DriverPaths  
 Een lijst met UNC-paden naar gedeelde mappen waarin aanvullende apparaatstuurprogramma's bevinden. Deze apparaatstuurprogramma's worden geïnstalleerd met het beoogde besturingssysteem op de doelcomputer. De MDT-scripts Kopieer de inhoud van deze mappen naar de map C:\Drivers op de doelcomputer. De **DriverPaths** eigenschap is een lijst met tekstwaarden die elke niet-lege waarde. De **DriverPaths** eigenschap heeft een numeriek achtervoegsel (bijvoorbeeld **DriverPaths001** of **DriverPaths002**).  

|**Geconfigureerd door de eigenschap**|||**De eigenschap is van toepassing op**||  
|-|-|-|-|-|  
|BootStrap.ini|||LTI|-|  
|CustomSettings.ini|-||||  
|MDT-DB|||ZTI||  

|**Waarde**|**Beschrijving**|  
|-|-|
|*UNC_path*|UNC-pad naar de gedeelde map op waarin de extra stuurprogramma's zich bevinden|  

|**Voorbeeld**|  
|-|
|`[Settings] Priority=Default  [Default] DriverPaths001=\\NYC-AM-FIL-01\Drivers$ DriverPaths002=\\NYC-AM-FIL-03\Win8Drvs`|  

####  <a name="DriverSelectionProfile"></a>DriverSelectionProfile  
 De profielnaam die wordt gebruikt tijdens de installatie van het stuurprogramma.  

|**Geconfigureerd door de eigenschap**|||**De eigenschap is van toepassing op**||  
|-|-|-|-|-|  
|BootStrap.ini|||LTI|-|  
|CustomSettings.ini|-||||  
|MDT-DB|-||ZTI||  

|**Waarde**|**Beschrijving**|  
|-|-|
|*Profielnaam*|Geen|  

|**Voorbeeld**|  
|-|  
|`[Settings] Priority=Default  [Default] DriverSelectionProfile=MonitorDrivers`|  

####  <a name="EventService"></a>EventService  
 De **EventService** eigenschap geeft u de URL waar de MDT monitoring-service wordt uitgevoerd. Standaard wordt met de service TCP-poort 9800 gebruikt om te communiceren. De MDT bewakingsservice verzamelt informatie over de implementatie op het implementatieproces die weergegeven in de implementatie-Workbench en met worden kan de [Get-MDTMonitorData](#Get-MDTMonitorData) cmdlet.  

|**Geconfigureerd door de eigenschap**|||**De eigenschap is van toepassing op**||  
|-|-|-|-|-|  
|BootStrap.ini|||LTI|-|  
|CustomSettings.ini|-||||  
|MDT-DB|-||ZTI|-|  

|**Waarde**|**Beschrijving**|  
|-|-|
|*url_path*|De URL moet de MDT-service te controleren.|  

|**Voorbeeld**|  
|-|   
|`[Settings] Priority=Default  [Default] EventService=http://WDG-MDT-01:9800 DeployRoot=\\NYC-AM-FIL-01\Distribution$ ResourceRoot=\\NYC-AM-FIL-01\Resource$`|  

####  <a name="EventShare"></a>EventShare  
 De **EventShare** eigenschap verwijst naar een gedeelde map op waarin de MDT record gebeurtenissen scripts.  

 Standaard wordt de gedeelde map gemaakt in C:\Events.  

|**Geconfigureerd door de eigenschap**|||**De eigenschap is van toepassing op**||  
|-|-|-|-|-|  
|BootStrap.ini|||LTI|-|  
|CustomSettings.ini|-||||  
|MDT-DB|-||ZTI|-|  

|**Waarde**|**Beschrijving**|  
|-|-|  
|*UNC_path*|Het UNC-pad naar de gedeelde map op waarin de MDT record gebeurtenissen scripts. De standaardnaam van de share is gebeurtenissen.|  

|**Voorbeeld**|  
|-|
|`[Settings] Priority=Default  [Default] EventShare=\\NYC-AM-FIL-01\Events DeployRoot=\\NYC-AM-FIL-01\Distribution$ ResourceRoot=\\NYC-AM-FIL-01\Resource$`|  

####  <a name="FinishAction"></a>FinishAction  
 Hiermee geeft u de actie moeten worden uitgevoerd wanneer een takenreeks LTI is voltooid, die na de **samenvatting** pagina in de Wizard implementatie van de wizard.  

> [!TIP]
>  Gebruik deze eigenschap in combinatie met de **SkipFinalSummary** eigenschap over te slaan de **samenvatting** wizardpagina in de Wizard implementatie en automatisch de actie uitvoeren.  

> [!CAUTION]
>  Waarde van deze eigenschap moet in hoofdletters worden opgegeven zodat de implementatiescripts deze goed kunnen lezen.  

|**Geconfigureerd door de eigenschap**|||**De eigenschap is van toepassing op**||  
|-|-|-|-|-|  
|BootStrap.ini|||LTI|-|  
|CustomSettings.ini|-||||  
|MDT-DB|-||ZTI||  

|**Waarde**|**Beschrijving**|  
|-|-|  
|*actie*|Waar *actie* is een van de volgende:<br /><br /> - **AFSLUITEN**. De doelcomputer afgesloten.<br /><br /> - **OPNIEUW OPSTARTEN**. Start opnieuw op de doelcomputer.<br /><br /> - **OPNIEUW OPSTARTEN**. Hetzelfde als **opnieuw opstarten**.<br /><br /> - **AFMELDEN**. De huidige gebruiker afmelden. Als de doelcomputer wordt Windows PE wordt uitgevoerd, wordt de doelcomputer worden gestart.<br /><br /> - **lege**. De implementatie-Wizard afsluiten zonder dat u aanvullende acties uitvoert. Dit is de standaardinstelling.|  

|**Voorbeeld**|  
|-|  
|`[Settings] Priority=Default  [Default] FinishAction=REBOOT`|  

####  <a name="ForceApplyFallback"></a>ForceApplyFallback  
 Bepaalt de methode die wordt gebruikt voor geïnstalleerde Windows:  

-   **Setup.exe**. Deze methode is de traditionele methode, gestart door het uitvoeren van setup.exe vanaf de installatiemedia. MDT maakt standaard gebruik van deze methode.  

-   ImageX.exe. Deze methode installeert de installatiekopie van het besturingssysteem imagex.exe met behulp van de **/ apply** optie. MDT maakt gebruik van deze methode wanneer de setup.exe-methode kan niet worden gebruikt (dat wil zeggen, MDT terugvalt op het gebruik van imagex.exe).  

 Naast het beheren van de methode die wordt gebruikt voor het installeren van deze besturingssystemen met deze eigenschap bepaalt welke takenreeksen besturingssysteem worden vermeld in de Wizard implementatie voor de installatiekopie van een specifieke processor-architectuur. Wanneer de waarde van deze eigenschap is ingesteld op **nooit**, alleen besturingssysteem systeemtaak reeksen die overeenkomen met de processorarchitectuur van de installatiekopie worden weergegeven. Als de waarde van deze eigenschap is ingesteld op een andere waarde of leeg is, zijn alle takenreeksen die gebruikmaken van de installatiemethode imagex.exe kunnen weergegeven, ongeacht de processorarchitectuur.  

|**Geconfigureerd door de eigenschap**|||**De eigenschap is van toepassing op**||  
|-|-|-|-|-|  
|BootStrap.ini|||LTI|-|  
|CustomSettings.ini|-||||  
|MDT-DB|-||ZTI||  

|**Waarde**|**Beschrijving**|  
|-|-|  
|**NOOIT**|MDT gebruikt altijd de methode imagex.exe indien nodig. Alleen de takenreeksen die gebruikmaken van een besturingssysteem dat overeenkomt met de installatiekopie worden weergegeven in de Wizard implementatie.|  
|Een andere waarde, met inbegrip van leeg| Elke takenreeks die ondersteuning biedt voor de methode imagex.exe wordt weergegeven in de Wizard implementatie.|  


|**Voorbeeld**|
 |-|
|`[Settings] Priority=Default  [Default] OSInstall=YES ForceApplyFallback=NEVER`|  

####  <a name="ForestLevel"></a>ForestLevel  
 Deze vermelding geeft het forestfunctionaliteitsniveau wanneer een nieuw domein in een nieuw forest is gemaakt.  

|**Geconfigureerd door de eigenschap**|||**De eigenschap is van toepassing op**||  
|-|-|-|-|-|  
|BootStrap.ini|||LTI|-|  
|CustomSettings.ini|-||||  
|MDT-DB|-||ZTI|-|  

|**Waarde**|**Beschrijving**|  
|-|-|  
|*niveau*|Stelt het domeinfunctionaliteitsniveau op een van de volgende:<br /><br /> -2, WindowsServer 2003<br /><br /> -3, WindowsServer 2008<br /><br /> -4, Windows Server 2008 R2<br /><br /> -5, WindowsServer 2012|  

|**Voorbeeld**|  
|-|  
|`[Settings] Priority=Default  [Default] ForestLevel=3`|  

####  <a name="FullName"></a>Volledige naam  
 De volledige naam van de gebruiker van de doelcomputer die is opgegeven tijdens de installatie van het besturingssysteem. Deze waarde wordt ingevoegd in de juiste configuratie-instellingen in Unattend.xml.  

> [!NOTE]
>  Deze waarde verschilt van de referenties van de gebruiker die zijn gemaakt nadat het besturingssysteem wordt geïmplementeerd. De **FullName** eigenschap informatie wordt verstrekt aan systeembeheerders over de gebruiker die de toepassingen op de doelcomputer.  

|**Geconfigureerd door de eigenschap**|||**De eigenschap is van toepassing op**||  
|-|-|-|-|-|  
|BootStrap.ini|||LTI|-|  
|CustomSettings.ini|-||||  
|MDT-DB|-||ZTI|-|  

|**Waarde**|**Beschrijving**|  
|-|-|  
|*full_name*|De volledige naam van de gebruiker van de doelcomputer|  

|**Voorbeeld**|  
|-|  
|`[Settings] Priority=MACAddress, Default Properties=CustomProperty, ApplicationInstall  [Default] CustomProperty=TRUE OrgName=Woodgrove Bank  [00:0F:20:35:DE:AC] OSDNEWMACHINENAME=HPD530-1 ApplicationInstall=Custom FullName=Woodgrove Bank User  [00:03:FF:FE:FF:FF] OSDNEWMACHINENAME=BVMXP  ApplicationInstall=Minimum FullName=Woodgrove Bank Manager`|  

####  <a name="GPOPackPath"></a>GPOPackPath  
 Deze eigenschap wordt gebruikt voor het onderdrukken van het standaardpad naar de map waarin de packs groepsbeleidsobject maken. Het pad dat is opgegeven voor deze eigenschap is ten opzichte van de map Templates\GPOPacks in een distributieshare. MDT scant automatisch een specifieke submap van deze map op basis van het besturingssysteem wordt geïmplementeerd op de doelcomputer, zoals Templates\GPOPacks\\*operating_system* (waarbij *operating_ systeem* is het besturingssysteem wordt geïmplementeerd). Tabel 3 overzicht van de ondersteunde besturingssystemen en de submappen die met elk besturingssysteem overeenkomen.  

##### <a name="table-3-windows-operating-systems-and-corresponding-gpo-pack-subfolder"></a>Tabel 3. Windows-besturingssystemen en het bijbehorende groepsbeleidsobject Pack submap  

|**Besturingssysteem**|**Groepsbeleidsobject pack submap**|  
|-|-|  
|Windows 7 met SP1|Win7SP1 MDTGPOPack|  
|Windows Server 2008 R2|WS2008R2SP1 MDTGPOPack|  

|**Geconfigureerd door de eigenschap**|||**De eigenschap is van toepassing op**||  
|-|-|-|-|-|  
|BootStrap.ini|||LTI|-|  
|CustomSettings.ini|-||||  
|MDT-DB|-||ZTI|-|  

|**Waarde**|**Beschrijving**|  
|-|-|  
|*pad*|Het pad relatief de *distribution_share*\Templates\GPOPacks map (waarbij *distribution_share* is de hoofdmap van de distributieshare. De standaardwaarde is de *distribution_share*\Templates\GPOPacks\\*operating_system* map (waarbij *operating_system* is een submap op basis van de besturingssysteemversie).<br /><br /> In het onderstaande voorbeeld MDT te gebruiken als de eigenschap GPOPackPath op een waarde van 'Win7 HighSecurity' configureert de *distribution_share*\Templates\GPOPacks\Win7-HighSecurity map als de map waar de packs GPO worden opgeslagen.|  

|**Voorbeeld**|  
|-|  
|`[Settings] Priority=Default  [Default] GPOPackPath=Win7-HighSecurity`|  

####  <a name="Groups"></a>Groepen  
 De lijst van lokale groepen op de doelcomputer waarvan het lidmaatschap wordt vastgelegd. Lidmaatschap van deze groep is vastgelegd tijdens de fase voor het vastleggen van status en tijdens de fase voor het herstellen van status wordt teruggezet. (De standaardgroepen zijn voor beheerders en Hoofdgebruikers). De **groepen** eigenschap is een lijst met tekstwaarden die elke niet-lege waarde. De **groepen** eigenschap heeft een numeriek achtervoegsel (bijvoorbeeld **Groups001** of **Groups002**).  

|**Geconfigureerd door de eigenschap**|||**De eigenschap is van toepassing op**||  
|-|-|-|-|-|  
|BootStrap.ini|||LTI|-|  
|CustomSettings.ini|-||||  
|MDT-DB|||ZTI|-|  

|**Waarde**|**Beschrijving**|  
|-|-|  
|*groepsnaam*|De naam van de lokale groep op de doelcomputer voor welke groep lidmaatschap wordt vastgelegd|  

|**Voorbeeld**|  
|-|  
|`[Settings] Priority=Default  [Default] DeployRoot=\\NYC-AM-FIL-01\Distribution$ ResourceRoot=\\NYC-AM-FIL-01\Resource$ UDShare=\\NYC-AM-FIL-01\MigData$ CaptureGroups=YES Groups001=NYC Application Management Groups002=NYC Help Desk Users`|  

####  <a name="HideShell"></a>HideShell  
 Deze eigenschap bepaalt de weergave van Windows Verkenner, terwijl de takenreeks LTI in het nieuwe besturingssysteem wordt uitgevoerd op de doelcomputer. Deze eigenschap kan worden gebruikt in combinatie met de **DisableTaskMgr** eigenschap.  

> [!NOTE]
>  Deze eigenschap kan worden gebruikt met de **DisableTaskMgr** eigenschap om te voorkomen dat gebruikers de takenreeks LTI te onderbreken. Zie voor meer informatie de [DisableTaskMgr](#DisableTaskMgr) eigenschap.  

|**Geconfigureerd door de eigenschap**|||**De eigenschap is van toepassing op**||  
|-|-|-|-|-|  
|BootStrap.ini|||LTI|-|  
|CustomSettings.ini|-||||  
|MDT-DB|-||ZTI||  

|**Waarde**|**Beschrijving**|  
|-|-|  
|**JA**|Windows Verkenner is verborgen totdat de takenreeks voltooid is.|  
|**ER IS GEEN**|Windows Verkenner is zichtbaar terwijl de takenreeks wordt uitgevoerd. Dit is de standaardwaarde.|  

|**Voorbeeld**|  
|-|  
|`[Settings] Priority=Default  [Default] DisableTaskMgr=YES HideShell=YES`|  

####  <a name="OSHome_Page"></a>OSHome_Page  
 De URL moet worden gebruikt als de startpagina Windows Internet Explorer® na de implementatie van het beoogde besturingssysteem.  

|**Geconfigureerd door de eigenschap**|||**De eigenschap is van toepassing op**||  
|-|-|-|-|-|  
|BootStrap.ini|||LTI|-|  
|CustomSettings.ini|-||||  
|MDT-DB|-||ZTI|-|  

|**Waarde**|**Beschrijving**|  
|-|-|  
|*URL*|De URL van de webpagina moet worden gebruikt als de startpagina voor Internet Explorer op de doelcomputer|  

|**Voorbeeld**|  
|-|  
|`[Settings] Priority=Default  [Default] Home_Page=http://portal.woodgrovebank.com`|  

####  <a name="HostName"></a>Hostnaam  
 De IP-hostnaam van de doelcomputer (de naam die is toegewezen aan de doelcomputer).  

> [!NOTE]
>  Dit is de computernaam van de doelcomputer en niet de NetBIOS-computernaam van de doelcomputer. De NetBIOS-computernaam kan niet korter zijn dan de naam van de computer. Deze eigenschap wordt ook dynamisch wordt ingesteld door de MDT-scripts en kan de waarde instellen in CustomSettings.ini of de MDT-database hebben. Deze eigenschap behandelen als alleen-lezen. Echter kunt u deze eigenschap binnen CustomSettings.ini of de MDT-database, zoals wordt weergegeven in de volgende voorbeelden om te helpen bij het definiëren van de configuratie van de doelcomputer.  

|**Geconfigureerd door de eigenschap**|||**De eigenschap is van toepassing op**||  
|-|-|-|-|-|  
|BootStrap.ini|||LTI|-|  
|CustomSettings.ini|||||  
|MDT-DB|||ZTI|-|  

|**Waarde**|**Beschrijving**|  
|-|-|
|*hostnaam*|Het IP-host-naam toegewezen aan de doelcomputer|  

|**Voorbeeld**|  
|-|  
|Geen|  

####  <a name="ImagePackageID"></a>ImagePackageID  
 De pakket-ID die wordt gebruikt voor het besturingssysteem te installeren tijdens de OEM-implementaties.  

> [!NOTE]
>  Deze eigenschap wordt dynamisch ingesteld door de MDT-scripts en is niet geconfigureerd in CustomSettings.ini of de MDT-DB. Deze eigenschap behandelen als alleen-lezen.  

|**Geconfigureerd door de eigenschap**|||**De eigenschap is van toepassing op**||  
|-|-|-|-|-|  
|BootStrap.ini|||LTI|-|  
|CustomSettings.ini|||||  
|MDT-DB|||ZTI|-|  

|**Waarde**|**Beschrijving**|
|-|-|  
|Geen|De pakket-ID die is gebruikt voor het besturingssysteem te installeren tijdens de OEM-implementaties|  

|**Voorbeeld**|  
|-|  
|Geen|  

####  <a name="InputLocale"></a>InputLocale  
 Een lijst met de landinstellingen te worden gebruikt met het beoogde besturingssysteem. Meer dan één landinstelling kan worden opgegeven voor het beoogde besturingssysteem. Elke landinstelling moet worden gescheiden door een puntkomma (;). Als niet wordt opgegeven, gebruikt de Wizard implementatie van de landinstelling die is geconfigureerd in de installatiekopie wordt geïmplementeerd.  

 Deze instelling in de Windows gebruiker State Migration Tool (USMT) wanneer een back-up en herstellen van informatie over de status van de gebruiker uitsluiten. De instellingen in de gebruikersstatusinformatie overschrijft anders de opgegeven waarden in de *InputLocale* eigenschap.  

|**Geconfigureerd door de eigenschap**|||**De eigenschap is van toepassing op**||  
|-|-|-|-|-|  
|BootStrap.ini|||LTI|-|  
|CustomSettings.ini|-||||  
|MDT-DB|-||ZTI|-|  

|**Waarde**|**Beschrijving**|  
|-|-|  
|*input_locale1; input_locale2*|De landinstelling voor het toetsenbord gekoppeld aan de doelcomputer|  

|**Voorbeeld**|  
|-|  
|`[Settings] Priority=Default  [Default] UserLocale=en-us InputLocale=0409:00000409;0413:00020409;0413:00000409;0409:00020409`|  

####  <a name="InstallPackageID"></a>InstallPackageID  
 De pakket-ID die wordt gebruikt voor het besturingssysteem te installeren tijdens de OEM-implementaties.  

> [!NOTE]
>  Deze eigenschap wordt dynamisch ingesteld door de MDT-scripts en is niet geconfigureerd in CustomSettings.ini of de MDT-DB. Deze eigenschap behandelen als alleen-lezen.  

|**Geconfigureerd door de eigenschap**|||**De eigenschap is van toepassing op**||  
|-|-|-|-|-|  
|BootStrap.ini|||LTI|-|  
|CustomSettings.ini|||||  
|MDT-DB|||ZTI|-|  

|**Waarde**|**Beschrijving**|  
|-|-|
|Geen|De pakket-ID die is gebruikt voor het besturingssysteem te installeren tijdens de OEM-implementaties|  

|**Voorbeeld**|  
|-|  
|Geen|  

####  <a name="Instance"></a>Exemplaar  
 Het exemplaar van SQL Server gebruikt voor het uitvoeren van query's eigenschapswaarden uit kolommen in de tabel die is opgegeven de **tabel** eigenschap. De database zich bevindt op de computer die is opgegeven in de **SQLServer** eigenschap. Het exemplaar van SQL Server op de computer is opgegeven de **exemplaar** eigenschap.  

|**Geconfigureerd door de eigenschap**|||**De eigenschap is van toepassing op**||  
|-|-|-|-|-|  
|BootStrap.ini|-||LTI|-|  
|CustomSettings.ini|-||||  
|MDT-DB|-||ZTI|-|  

|**Waarde**|**Beschrijving**|  
|-|-|
||*exemplaar*|De naam van het exemplaar van SQL Server moet worden gebruikt voor het uitvoeren van query's eigenschapswaarden|  

|**Voorbeeld**|  
|-|  
|`[Settings] Priority=Computers, Default  [Default] OSInstall=YES  [Computers] SQLServer=NYC-SQL-01 Database=MDTDB Instance=SQLEnterprise2005 Table=Computers Parameters=SerialNumber, AssetTag ParameterCondition=OR`|  

####  <a name="IPAddress"></a>IP-adres  
 Het IP-adres van de doelcomputer. De indeling van het IP-adres dat is geretourneerd door de eigenschap is standaard een decimale notatie; bijvoorbeeld 192.168.1.1. Gebruik deze eigenschap te maken van een subsectie met instellingen die zijn gericht op een specifieke doelcomputer op basis van het IP-adres.  

> [!NOTE]
>  Deze eigenschap wordt dynamisch ingesteld door de MDT-scripts en is niet geconfigureerd in CustomSettings.ini of de MDT-DB. Deze eigenschap behandelen als alleen-lezen.  

|**Geconfigureerd door de eigenschap**|||**De eigenschap is van toepassing op**||  
|-|-|-|-|-|  
|BootStrap.ini|||LTI|\-|  
|CustomSettings.ini|||||  
|MDT-DB|||ZTI|\-|  

|**Waarde**|**Beschrijving**|  
|-|-|
|*IP\_adres*|Het IP-adres van de doelcomputer in de standaard met\-decimale notatie|  

|**Voorbeeld**|  
|-|  
|Geen|  

####  <a name="IsDesktop"></a>IsDesktop  
 Geeft aan of de computer een bureaublad, is omdat de **Win32\_SystemEnclosure ChassisType** eigenschapswaarde **3**, **4**, **5** , **6**, **7**, of **15**.  

> [!NOTE]
>  Slechts één van de volgende eigenschappen wordt tegelijk waar zijn: **IsDesktop**, **IsLaptop**, **IsServer**.  

> [!NOTE]
>  Deze eigenschap wordt dynamisch ingesteld door de MDT-scripts en is niet geconfigureerd in CustomSettings.ini of de MDT-DB. Deze eigenschap behandelen als alleen-lezen.  

|**Geconfigureerd door de eigenschap**|||**De eigenschap is van toepassing op**||  
|-|-|-|-|-|  
|BootStrap.ini|||LTI|\-|  
|CustomSettings.ini|||||  
|MDT-DB|||ZTI|\-|  

|**Waarde**|**Beschrijving**|  
|-|-|
|**DE WAARDE TRUE**|De doelcomputer is een desktopcomputer.|  
|**DE WAARDE FALSE**|De doelcomputer is niet een desktopcomputer.|  

|**Voorbeeld**|  
|-|  
|Geen|  

####  <a name="IsHypervisorRunning"></a>IsHypervisorRunning  
 Geeft aan of een hypervisor aanwezig is op de doelcomputer. Deze eigenschap is ingesteld met behulp van informatie uit de **CPUID** interface.  

 Voor meer informatie over virtuele machines die is verzameld en informatie die wordt geretourneerd vanaf de **CPUID** interface, Zie de volgende eigenschappen:  

-   **IsVM**  

-   **SupportsHyperVRole**  

-   **SupportsNX**  

-   **SupportsVT**  

-   **Supports64Bit**  

-   **VMPlatform**  

> [!NOTE]
>  Deze eigenschap wordt dynamisch ingesteld door de MDT-scripts en is niet geconfigureerd in CustomSettings.ini of de MDT-DB. Deze eigenschap behandelen als alleen-lezen.  

> [!NOTE]
>  De eigenschap IsVM moet worden gebruikt om te bepalen of de doelcomputer een virtuele of fysieke machine.  

|**Geconfigureerd door de eigenschap**|||**De eigenschap is van toepassing op**||  
|-|-|-|-|-|  
|BootStrap.ini|||LTI|\-|  
|CustomSettings.ini|||||  
|MDT-DB|||ZTI|\-|  

|**Waarde**|**Beschrijving**|  
|-|-|
|**DE WAARDE TRUE**|Een hypervisor is gedetecteerd.|  
|**DE WAARDE FALSE**|Een hypervisor is niet aangetroffen.|  

|**Voorbeeld**|  
|-|  
|Geen|  

####  <a name="IsLaptop"></a>IsLaptop  
 Geeft aan of de computer een draagbare computer is omdat de **Win32\_SystemEnclosure ChassisType** eigenschapswaarde **8**, **10**, **12**, **14**, **18**, of **21**.  

> [!NOTE]
>  Slechts één van de volgende eigenschappen wordt tegelijk waar zijn: **IsDesktop**, **IsLaptop**, **IsServer**.  

> [!NOTE]
>  Deze eigenschap wordt dynamisch ingesteld door de MDT-scripts en is niet geconfigureerd in CustomSettings.ini of de MDT-DB. Deze eigenschap behandelen als alleen-lezen.  

|**Geconfigureerd door de eigenschap**|||**De eigenschap is van toepassing op**||  
|-|-|-|-|-|  
|BootStrap.ini|||LTI|\-|  
|CustomSettings.ini|||||  
|MDT-DB|||ZTI|\-|  

|**Waarde**|**Beschrijving**|  
|-|-|
|**DE WAARDE TRUE**|De doelcomputer is een draagbare computer.|  
|**DE WAARDE FALSE**|De doelcomputer is niet een draagbare computer.|  

|**Voorbeeld**|  
|-|  
|Geen|  

####  <a name="IsServer"></a>IsServer  
 Geeft aan of de computer een server, is omdat de **Win32\_SystemEnclosure ChassisType** eigenschapswaarde **23**.  

|**Geconfigureerd door de eigenschap**|||**De eigenschap is van toepassing op**||  
|-|-|-|-|-|  
|BootStrap.ini|||LTI|\-|  
|CustomSettings.ini|||||  
|MDT-DB|||ZTI|\-|  

|**Waarde**|**Beschrijving**|  
|-|-|
|**DE WAARDE TRUE**|De doelcomputer is een server.|  
|**DE WAARDE FALSE**|De doelcomputer is geen server.|  

|**Voorbeeld**|  
|-|  
|Geen|  

####  <a name="IsServerCoreOS"></a>IsServerCoreOS  
 Geeft aan of het huidige besturingssysteem uitgevoerd op de doelcomputer de Server Core-installatieoptie van het besturingssysteem Windows Server is.  

> [!NOTE]
>  Deze eigenschap wordt dynamisch ingesteld door de MDT-scripts en is niet geconfigureerd in CustomSettings.ini of de MDT-DB. Deze eigenschap behandelen als alleen-lezen.  

|**Geconfigureerd door de eigenschap**|||**De eigenschap is van toepassing op**||  
|-|-|-|-|-|  
|BootStrap.ini|||LTI|\-|  
|CustomSettings.ini|||||  
|MDT-DB|||ZTI|\-|  

|**Waarde**|**Beschrijving**|  
|-|-|
|**DE WAARDE TRUE**|Het besturingssysteem op de doelcomputer is de Server Core-installatieoptie van Windows Server.|  
|**DE WAARDE FALSE**|Het besturingssysteem op de doelcomputer is niet de Server Core-installatieoptie van Windows Server.|  

|**Voorbeeld**|  
|-|  
|Geen|  

####  <a name="IsServerOS"></a>IsServerOS  
 Geeft aan of het huidige besturingssysteem uitgevoerd op de doelcomputer een serverbesturingssysteem is.  

> [!NOTE]
>  Deze eigenschap wordt dynamisch ingesteld door de MDT-scripts en is niet geconfigureerd in CustomSettings.ini of de MDT-DB. Deze eigenschap behandelen als alleen-lezen.  

|**Geconfigureerd door de eigenschap**|||**De eigenschap is van toepassing op**||  
|-|-|-|-|-|  
|BootStrap.ini|||LTI|\-|  
|CustomSettings.ini|||||  
|MDT-DB|||ZTI|\-|  

|**Waarde**|**Beschrijving**|  
|-|-|
|**DE WAARDE TRUE**|Het besturingssysteem op de doelcomputer is een serverbesturingssysteem.|  
|**DE WAARDE FALSE**|Het besturingssysteem op de doelcomputer is niet een serverbesturingssysteem.|  

|**Voorbeeld**|  
|-|  
|Geen|  

####  <a name="IsUEFI"></a>IsUEFI  
 Hiermee geeft u op of de doelcomputer momenteel wordt uitgevoerd met Unified Extensible Firmware Interface \(UEFI\). De UEFI is een specificatie die een software-interface tussen een besturingssysteem en platform firmware definieert. UEFI is veiliger vervanging voor de oudere BIOS-firmware-interface aanwezig zijn in sommige privé-computers. Voor meer informatie over UEFI, gaat u naar [http:\/\/www.uefi.org](http://www.uefi.org).  

> [!NOTE]
>  Deze eigenschap wordt dynamisch ingesteld door de MDT-scripts en is niet geconfigureerd in CustomSettings.ini of de MDT-DB. Deze eigenschap behandelen als alleen-lezen.  

|**Geconfigureerd door de eigenschap**|||**De eigenschap is van toepassing op**||  
|-|-|-|-|-|  
|BootStrap.ini|||LTI|\-|  
|CustomSettings.ini|||||  
|MDT-DB|||ZTI|\-|  

|**Waarde**|**Beschrijving**|  
|-|-|
|**DE WAARDE TRUE**|De doelcomputer wordt momenteel uitgevoerd met UEFI.|  
|**DE WAARDE FALSE**|De doelcomputer is momenteel niet uitgevoerd met UEFI.<br /><br /> Opmerking:<br /><br /> Het is mogelijk dat de doelcomputer kan UEFI ondersteunen, maar wordt uitgevoerd in een compatibiliteitsmodus die de oudere BIOS-firmware-interface worden geëmuleerd. In dit geval de waarde van deze eigenschap wordt ingesteld op **FALSE** Hoewel UEFI ondersteuning biedt voor de doelcomputer.|  

|**Voorbeeld**|  
|-|  
|Geen|  

####  <a name="IsVM"></a>IsVM  
 Hiermee bepaalt u of de doelcomputer een virtuele machine op basis van gegevens die afkomstig zijn van de **CPUID** interface. U kunt bepalen het specifieke VM omgeving met de **VMPlatform** eigenschap.  

 Voor meer informatie over virtuele machines die is verzameld en informatie die wordt geretourneerd vanaf de **CPUID** interface, Zie de volgende eigenschappen:  

-   **IsHypervisorRunning**  

-   **SupportsHyperVRole**  

-   **SupportsNX**  

-   **SupportsVT**  

-   **Supports64Bit**  

-   **VMPlatform**  

> [!NOTE]
>  Deze eigenschap wordt dynamisch ingesteld door de MDT-scripts en is niet geconfigureerd in CustomSettings.ini of de MDT-DB. Deze eigenschap behandelen als alleen-lezen.  

|**Geconfigureerd door de eigenschap**|||**De eigenschap is van toepassing op**||  
|-|-|-|-|-|  
|BootStrap.ini|||LTI|\-|  
|CustomSettings.ini|||||  
|MDT-DB|||ZTI|\-|  

|**Waarde**|**Beschrijving**|  
|-|-|
|**DE WAARDE TRUE**|De doelcomputer is een virtuele machine.|  
|**DE WAARDE FALSE**|De doelcomputer is niet een virtuele machine.|  

|**Voorbeeld**|  
|-|  
|Geen|  

####  <a name="JoinDomain"></a>JoinDomain  
 Het domein waarvan de doelcomputer lid na het beoogde besturingssysteem wordt wordt geïmplementeerd. Dit is het domein waarin het computeraccount voor de doelcomputer is gemaakt. De **JoinDomain** eigenschap mag alfanumerieke tekens, afbreekstreepjes \( \- \), en onderstrepingstekens \( \_ \). De **JoinDomain** eigenschap mag niet leeg zijn of spaties bevatten.  

|**Geconfigureerd door de eigenschap**|||**De eigenschap is van toepassing op**||  
|-|-|-|-|-|  
|BootStrap.ini|||LTI|\-|  
|CustomSettings.ini|\-||||  
|MDT-DB|\-||ZTI|\-|  

|**Waarde**|**Beschrijving**|  
|-|-|
|*domein\_naam*|De naam van het domein waarvan de doelcomputer lid wordt|  

|**Voorbeeld**|  
|-|  
|`[Settings] Priority=Default  [Default] JoinDomain=WOODGROVEBANK MachineObjectOU=OU=Reception,OU=NYC,DC=Woodgrovebank,DC=com`|  

####  <a name="JoinWorkgroup"></a>JoinWorkgroup kan  
 De werkgroep waarvan de doelcomputer lid na het beoogde besturingssysteem wordt wordt geïmplementeerd. De **JoinWorkgroup kan** eigenschap mag alfanumerieke tekens, afbreekstreepjes \( \- \), en onderstrepingstekens \( \_ \). De **JoinWorkgroup kan** eigenschap mag niet leeg zijn of spaties bevatten.  

|**Geconfigureerd door de eigenschap**|||**De eigenschap is van toepassing op**||  
|-|-|-|-|-|  
|BootStrap.ini|||LTI|\-|  
|CustomSettings.ini|\-||||  
|MDT-DB|\-||ZTI|\-|  

|**Waarde**|**Beschrijving**|  
|-|-|
|*werkgroep\_naam*|De naam van de werkgroep waarvan de doelcomputer lid wordt|  

|**Voorbeeld**|  
|-|  
|`[Settings] Priority=Default  [Default] JoinWorkgroup=WDGV_WORKGROUP`|  

####  <a name="KeyboardLocale"></a>KeyboardLocale  
 Een lijst met de landinstellingen toetsenbord kan worden gebruikt bij het beoogde besturingssysteem. Meer dan een toetsenbord landinstelling kan worden opgegeven voor het beoogde besturingssysteem. Elke landinstelling moet worden gescheiden door puntkomma's \(;\). Als niet wordt opgegeven, gebruikt de Wizard implementatie van de landinstelling van het toetsenbord geconfigureerd in de installatiekopie wordt geïmplementeerd.  

 Deze instelling in USMT wanneer een back-up en herstellen van informatie over de status van de gebruiker uitsluiten. De instellingen in de gebruikersstatusinformatie overschrijft anders de opgegeven waarden in de **KeyboardLocale** eigenschap.  

> [!NOTE]
>  Voor deze eigenschap te laten functioneren, moet deze worden geconfigureerd in zowel CustomSettings.ini en BootStrap.ini. BootStrap.ini worden verwerkt voordat een implementatieshare (met daarin CustomSettings.ini) is geselecteerd.  

|**Geconfigureerd door de eigenschap**|||**De eigenschap is van toepassing op**||  
|-|-|-|-|-|  
|BootStrap.ini|-||LTI|-|  
|CustomSettings.ini|-||||  
|MDT-DB|-||ZTI|-|  

|**Waarde**|**Beschrijving**|  
|-|-|
|*keyboard_locale1; keyboard_locale2*|De landinstellingen van het toetsenbord gekoppeld aan de doelcomputer.<br /><br /> De waarde kan worden opgegeven in de volgende indelingen:<br /><br /> -Tekst (en-us)<br /><br /> -Hexadecimaal (: 0409: 00000409)|  

|**Voorbeeld 1**|  
|-|  
|`[Settings] Priority=Default  [Default] UserLocale=en-us KeyboardLocale=en-us`|  

|**Voorbeeld 2**|  
|-|  
|`[Settings] Priority=Default  [Default] UserLocale=en-us KeyboardLocale=0409:00000409;1809:00001809;041A:0000041A;083b:0001083b`|  

####  <a name="KeyboardLocalePE"></a>KeyboardLocalePE  
 De naam van de landinstelling toetsenbord moet worden gebruikt in Windows PE alleen.  

> [!NOTE]
>  Voor deze eigenschap te laten functioneren, moet deze worden geconfigureerd in zowel CustomSettings.ini en BootStrap.ini. BootStrap.ini worden verwerkt voordat een implementatieshare (met daarin CustomSettings.ini) is geselecteerd.  

|**Geconfigureerd door de eigenschap**|||**De eigenschap is van toepassing op**||  
|-|-|-|-|-|  
|BootStrap.ini|-||LTI|-|  
|CustomSettings.ini|-||||  
|MDT-DB|-||ZTI|-|  

|**Waarde**|**Beschrijving**|  
|-|-|
|*keyboard_locale*|De landinstellingen van het toetsenbord gekoppeld aan de doelcomputer.<br /><br /> De waarde kan worden opgegeven in de volgende indelingen:<br /><br /> -Tekst (en-us)<br /><br /> -Hexadecimaal (: 0409: 00000409)|  

|**Voorbeeld 1**|  
|-|  
|`[Settings] Priority=Default  [Default] KeyboardLocalePE=en-us`|  

|**Voorbeeld 2**|  
|-|  
|`[Settings] Priority=Default  [Default] KeyboardLocalePE=0409:00000409`|  

####  <a name="LanguagePacks"></a>LanguagePacks  
 Een lijst met de GUID's voor de taalpakketten die worden geïmplementeerd op de doelcomputer. Implementatie-Workbench bevat deze taalpakketten op het knooppunt OS-pakketten. Deze GUID's worden opgeslagen in het bestand Packages.xml. De **LanguagePacks** eigenschap heeft een numeriek achtervoegsel (bijvoorbeeld **LanguagePacks001** of **LanguagePacks002**).  

|**Geconfigureerd door de eigenschap**|||**De eigenschap is van toepassing op**||  
|-|-|-|-|-|  
|BootStrap.ini|||LTI|-|  
|CustomSettings.ini|-||||  
|MDT-DB|||ZTI||  

|**Waarde**|**Beschrijving**|  
|-|-|
|*language_pack_guid*|De GUID die de implementatie-Workbench voor de taalpakketten bevat te installeren op de doelcomputer. De GUID overeenkomt met het taalpakket dat GUID in Packages.xml opgeslagen.|  

|**Voorbeeld**|  
|-|  
|`[Settings] Priority=Default  [Default] LanguagePacks001={a1923f8d-b07b-44c7-ac1e-353b7cc4c1ad}`|  

####  <a name="LoadStateArgs"></a>LoadStateArgs  
 De argumenten doorgegeven aan de USMT Loadstate-proces. Het script ZTI Hiermee voegt u de juiste logboekregistratie, voortgang en status store-parameters. Als deze waarde niet in het bestand met instellingen opgenomen is, wordt het herstelproces van de gebruiker de status overgeslagen.  

 Als het Loadstate-proces voltooid wordt, wordt informatie over de gebruikersstatus verwijderd. Het lokale gegevensarchief wordt verplaatst naar %WINDIR%\StateStore in het geval van een Loadstate-fout (of niet-nul-retourcode) om te voorkomen dat verwijderen en om ervoor te zorgen dat er wordt geen statusinformatie van de gebruiker verbroken is.  

> [!NOTE]
>  Voeg niet een van de volgende opdrachtregelargumenten bij het configureren van deze eigenschap: **/hardlink**, **/nocompress**, **/ontsleutelen**,   **/Key**, of **/KeyFile**. De MDT-scripts wordt deze opdrachtregelargumenten toevoegen, indien van toepassing voor de huidige implementatie.  

|**Geconfigureerd door de eigenschap**|||**De eigenschap is van toepassing op**||  
|-|-|-|-|-|  
|BootStrap.ini|||LTI|-|  
|CustomSettings.ini|-||||  
|MDT-DB|-||ZTI||  

|**Waarde**|**Beschrijving**|  
|-|-|
|Argumenten|De argumenten voor de opdrachtregel doorgegeven aan Loadstate.exe.<br /><br /> De standaardargumenten dat is opgegeven door de implementatie-Workbench zijn als volgt:<br /><br /> - **/v**. Hiermee schakelt u uitgebreide uitvoer in het logboek Loadstate. De standaardwaarde is **0**. Geef een getal van 0 tot en met 15. De waarde **5** schakelt uitgebreide en statusuitvoer.<br /><br /> - **/c**. Als u opgeeft, moet Loadstate wordt nog uitgevoerd zelfs als er niet-fatale fouten. Zonder de **/c** optie Loadstate verlaat bij de eerste fout.<br /><br /> - **/LAC**. Hiermee wordt aangegeven dat als het account dat wordt gemigreerd een lokale account (niet-domein) en deze niet op de doelcomputer bestaat en vervolgens USMT het account maakt maar wordt uitgeschakeld.<br /><br /> Zie de Help van USMT-bestanden voor meer informatie over deze en andere argumenten.|  

|**Voorbeeld**|  
|-|  
|`[Settings] Priority=Default  [Default] OSInstall=YES ScanStateArgs=/v:5 /o /c LoadStateArgs=/v:5 /c /lac DeployRoot=\\NYC-AM-FIL-01\Distribution$ ResourceRoot=\\NYC-AM-FIL-01\Resource$ UDShare=\\NYC-AM-FIL-01\MigData$ UDDir=%OSDComputerName%`|  

####  <a name="Location"></a>Locatie  
 De geografische locatie van de doelcomputers. Definieert een lijst met IP-adressen die met de standaardgateways gedefinieerd voor de computers binnen dat de locatie van overeenkomen de **locatie** eigenschap. Een IP-adres voor een standaardgateway kan worden gekoppeld aan meer dan één locatie.  

 Normaal gesproken de waarde voor de **locatie** eigenschap is ingesteld door een databasequery uitvoeren op de database die wordt beheerd met behulp van de implementatie-Workbench. Implementatie-Workbench kan helpen bij het maken van de locaties die zijn gekoppeld aan de locaties eigenschapsinstellingen definiëren en vervolgens bij het configureren van CustomSettings.ini voor het uitvoeren van de databasequery voor de locatie-eigenschap en de instellingen die zijn gekoppeld aan de locaties.  

 Bijvoorbeeld, een `LocationSettings` sectie in CustomSettings.ini kunt de LocationSettings weergave in de database voor een lijst met locaties met de opgegeven waarde in een query de **standaardgateway** eigenschap in de  **Parameters** eigenschap. De query retourneert alle instellingen die zijn gekoppeld aan elke standaardgateway.  

 De scripts parseren vervolgens elke sectie die overeenkomt met de locaties in de query zijn geretourneerd. De waarde bijvoorbeeld `[Springfield]`en de sectie `[Springfield-123 Oak Street-4th Floor]` in CustomSettings.ini kan de bijbehorende locaties vertegenwoordigen. Dit is een voorbeeld van hoe een computer kunnen deel uitmaken van twee locaties. De `[Springfield]`sectie is bedoeld voor alle computers in een grotere geografische regio (een hele stad), en de `[Springfield-123 Oak Street-4th Floor]` sectie is bedoeld voor alle computers in de vierde floor op de Eikenstraat 123 in Springfield.  

|**Geconfigureerd door de eigenschap**|||**De eigenschap is van toepassing op**||  
|-|-|-|-|-|  
|BootStrap.ini|-||LTI|-|  
|CustomSettings.ini|-||||  
|MDT-DB|-||ZTI|-|  

|**Waarde**|**Beschrijving**|  
|-|-|
|*Location1,*location2|De lijst met locaties moet worden toegewezen aan een afzonderlijke computer of een groep computers|  

|**Voorbeeld**|  
|-|  
|`[Settings] Priority=LSettings, Default  [Default] UserDataLocation=AUTO DeployRoot=\\W2K3-SP1\Distribution$ OSInstall=YES ScanStateArgs=/v:15 /o /c LoadStateArgs=/v:7 /c  [LSettings] SQLServer=w2k3-sp1 Instance=MDT2010 Database=MDTDB Netlib=DBNMPNTW SQLShare=SQL$ Table=LocationSettings Parameters=DefaultGateway  [Springfield] UDDir=%OSDComputerName% UDShare=\\Springfield-FIL-01\UserData  [Springfield-123 Oak Street-4th Floor] DeployRoot=\\Springfield-BDD-01\Distribution1$`|  

####  <a name="LongDistanceAccess"></a>LongDistanceAccess  
 De cijfers kiezen voor toegang tot een buitenlijn lange afstanden kiezen. De eigenschap kan alleen cijfers bevatten. Deze waarde wordt ingevoegd in de juiste configuratie-instellingen in Unattend.xml.  

|**Geconfigureerd door de eigenschap**|||**De eigenschap is van toepassing op**||  
|-|-|-|-|-|  
|BootStrap.ini|||LTI|-|  
|CustomSettings.ini|-||||  
|MDT-DB|-||ZTI|-|  

|**Waarde**|**Beschrijving**|  
|-|-|
|*language_pack_guid*|De GUID die de implementatie-Workbench voor de taalpakketten bevat te installeren op de doelcomputer. De GUID overeenkomt met het taalpakket dat GUID in Packages.xml opgeslagen.|  

|**Voorbeeld**|  
|-|  
|`[Settings] Priority=Default  [Default] AreaCode=206 CountryCode=001 Dialing=TONE LongDistanceAccess=9`|  

####  <a name="MACAddress"></a>MAC-adres  
 Het adres access media control (MAC) laag van de primaire-netwerkadapter van de doelcomputer. De **MACAddress** eigenschap is opgenomen in de **prioriteit** dat eigenschapswaarden die specifiek zijn voor een doelcomputer kunnen worden opgegeven. Een sectie voor elke MAC-adres maken voor elk van de doel-pc (zoals `[00:0F:20:35:DE:AC]`of `[00:03:FF:FE:FF:FF]`) die computer-specifieke doelinstellingen bevatten.  

|**Geconfigureerd door de eigenschap**|||**De eigenschap is van toepassing op**||  
|-|-|-|-|-|  
|BootStrap.ini|||LTI|-|  
|CustomSettings.ini|-||||  
|MDT-DB|||ZTI|-|  

|**Waarde**|**Beschrijving**|  
|-|-|
|*Mac*|Het MAC-adres van de doelcomputer|  

|**Voorbeeld**|  
|-|  
|`[Settings] Priority=MACAddress, Default  [Default] CaptureGroups=YES Groups1=NYC Application Management Groups2=NYC Help Desk Users  [00:0F:20:35:DE:AC] OSDNEWMACHINENAME=HPD530-1  [00:03:FF:FE:FF:FF] OSDNEWMACHINENAME=BVMXP`|  

####  <a name="MachineObjectOU"></a>MachineObjectOU  
 De AD DS-OE in het doeldomein wanneer de computer voor de doelcomputer rekening wordt gemaakt.  

> [!NOTE]
>  De organisatie-eenheid die is opgegeven voor deze eigenschap moet bestaan voordat u het beoogde besturingssysteem implementeert.  

> [!NOTE]
>  Als er al een computerobject in AD DS bestaat, geven **MachineObjectOU** leidt niet tot het computerobject worden verplaatst naar de opgegeven organisatie-eenheid.  

|**Geconfigureerd door de eigenschap**|||**De eigenschap is van toepassing op**||  
|-|-|-|-|-|  
|BootStrap.ini|||LTI|-|  
|CustomSettings.ini|-||||  
|MDT-DB|-||ZTI|-|  

|**Waarde**|**Beschrijving**|  
|-|-|
|*Organisatie-eenheid\_naam*|De naam van de organisatie-eenheid waar u het computeraccount voor de doelcomputer wordt gemaakt|  

|**Voorbeeld**|  
|-|  
|`[Settings] Priority=Default  [Default] JoinDomain=WOODGROVEBANK MachineObjectOU=OU=Reception,OU=NYC,DC=Woodgrovebank,DC=com`|  

####  <a name="Make"></a>Maken  
 De fabrikant van de doelcomputer. De indeling voor **zorg** is niet gedefinieerd. Gebruik deze eigenschap voor het maken van een subsectie met instellingen die zijn gericht op een specifieke computer-fabrikant \(meestal in combinatie met de **Model** en **Product** eigenschappen\).  

> [!NOTE]
>  Deze eigenschap wordt dynamisch ingesteld door de MDT-scripts en de waarde is ingesteld in CustomSettings.ini of de MDT-DB kan hebben. Deze eigenschap behandelen als alleen-lezen. Echter kunt u deze eigenschap binnen CustomSettings.ini of de MDT-database, zoals wordt weergegeven in de volgende voorbeelden om te helpen bij het definiëren van de configuratie van de doelcomputer.  

|**Geconfigureerd door de eigenschap**|||**De eigenschap is van toepassing op**||  
|-|-|-|-|-|  
|BootStrap.ini|||LTI|\-|  
|CustomSettings.ini|||||  
|MDT-DB|||ZTI|\-|  

|**Waarde**|**Beschrijving**|  
|-|-|
|*maken*|De fabrikant van de doelcomputer|  

|**Voorbeeld**|  
|-|  
|`[Settings] Priority=Make, Default  [Default]  [Dell Computer Corporation] Subsection=Dell-%Model%  [Dell-Latitude D600] Packages001=XXX00009:Program9 Packages002=XXX0000A:Program10`|  

####  <a name="MandatoryApplications"></a>MandatoryApplications  
 Een lijst van de toepassing-GUID's die worden geïnstalleerd op de doelcomputer. Deze toepassingen zijn opgegeven op het knooppunt toepassingen in de implementatie-Workbench. De GUID's worden opgeslagen in het bestand Applications.xml. De **MandatoryApplications** eigenschap is een lijst met tekstwaarden die ieder niet kunnen worden\-lege waarde. De **MandatoryApplications** eigenschap heeft een numeriek achtervoegsel \(bijvoorbeeld **MandatoryApplications001** of **MandatoryApplications002** \).  

|**Geconfigureerd door de eigenschap**|||**De eigenschap is van toepassing op**||  
|-|-|-|-|-|  
|BootStrap.ini|||LTI|\-|  
|CustomSettings.ini|\-||||  
|MDT-DB|||ZTI|\-|  

|**Waarde**|**Beschrijving**|  
|-|-|
|*toepassing\_guid*|De GUID die is opgegeven door de Implementatieworkbench voor de toepassing worden geïmplementeerd op de doelcomputer. De GUID overeenkomt met de GUID die is opgeslagen in het bestand Applications.xml toepassing.|  

|**Voorbeeld**|  
|-|  
|`[Settings] Priority=Default  [Default] MandatoryApplications001={1D7DF331-47B7-472C-87B3-442597EC2F7D} MandatoryApplications002={9d2b8999-5e4d-4f3d-bb05-edaaf4fe5628} Administrators001=WOODGROVEBANK\NYC Help Desk Staff`|  

####  <a name="Memory"></a>Geheugen  
 De hoeveelheid geheugen die is geïnstalleerd op de doelcomputer in megabytes. De waarde bijvoorbeeld **2038** 2,038 MB geeft \(of 2 GB\) geheugen op de doelcomputer is geïnstalleerd.  

> [!NOTE]
>  Deze eigenschap wordt dynamisch ingesteld door de MDT-scripts en is niet geconfigureerd in CustomSettings.ini of de MDT-DB. Deze eigenschap behandelen als alleen-lezen.  

|**Geconfigureerd door de eigenschap**|||**De eigenschap is van toepassing op**||  
|-|-|-|-|-|  
|BootStrap.ini|||LTI|\-|  
|CustomSettings.ini|||||  
|MDT-DB|||ZTI|\-|  

|**Waarde**|**Beschrijving**|  
|-|-|
|*geheugen*|De hoeveelheid geheugen die is geïnstalleerd op de doelcomputer in MB|  

|**Voorbeeld**|  
|-|  
|Geen|  

####  <a name="Model"></a>Model  
 Het model van de doelcomputer. De indeling voor **Model** is niet gedefinieerd. Gebruik deze eigenschap voor het maken van een subsectie met instellingen die zijn gericht op een specifieke computer modelnummer voor een specifieke computer-fabrikant \(meestal in combinatie met de **zorg** en  **Product** eigenschappen\).  

> [!NOTE]
>  Deze eigenschap wordt dynamisch ingesteld door de MDT-scripts en de waarde is ingesteld in CustomSettings.ini of de MDT-DB kan hebben. Deze eigenschap behandelen als alleen-lezen. Echter kunt u deze eigenschap binnen CustomSettings.ini of de MDT-database, zoals wordt weergegeven in de volgende voorbeelden om te helpen bij het definiëren van de configuratie van de doelcomputer.  

|**Geconfigureerd door de eigenschap**|||**De eigenschap is van toepassing op**||  
|-|-|-|-|-|  
|BootStrap.ini|||LTI|\-|  
|CustomSettings.ini|||||  
|MDT-DB|||ZTI|\-|  

|**Waarde**|**Beschrijving**|  
|-|-|
|*model*|Het model van de doelcomputer|  

|**Voorbeeld**|  
|-|  
|`[Settings] Priority=Make, Default  [Default]  [Dell Computer Corporation] Subsection=Dell-%Model%  [Dell-Latitude D600] Packages001=XXX00009:Program9 Packages002=XXX0000A:Program10`|  

####  <a name="NetLib"></a>NetLib  
 Het protocol moet worden gebruikt om te communiceren met de computer waarop SQL Server is opgegeven in de **SQLServer** eigenschap.  

|**Geconfigureerd door de eigenschap**|||**De eigenschap is van toepassing op**||  
|-|-|-|-|-|  
|BootStrap.ini|\-||LTI|\-|  
|CustomSettings.ini|\-||||  
|MDT-DB|\-||ZTI|\-|  

|**Waarde**|**Beschrijving**|  
|-|-|
|**DBNMPNTW**|Het protocol named pipes gebruiken om te communiceren.|  
|**DBMSSOCN**|Gebruik van TCP\/IP-sockets om te communiceren.|  

|**Voorbeeld**|  
|-|  
|`[Settings] Priority=Computers, Default  [Default] ScanStateArgs=/v:5 /o /c LoadStateArgs=/v:5 /c /lac  [Computers] SQLServer=NYC-SQL-01 SQLShare=SQL$ NetLib=DBNMPNTW Database=MDTDB Instance=SQLEnterprise2005 Table=Computers Parameters=SerialNumber, AssetTag ParameterCondition=OR`|  

####  <a name="NewDomain"></a>NewDomain  
 Geeft het type van een nieuw domein: of een nieuw domein in een nieuw forest is de hoofdmap van een nieuwe structuur in een bestaand forest of een onderliggend element van een bestaand domein.  

|**Geconfigureerd door de eigenschap**|||**De eigenschap is van toepassing op**||  
|-|-|-|-|-|  
|BootStrap.ini|||LTI|\-|  
|CustomSettings.ini|\-||||  
|MDT-DB|\-||ZTI|\-|  

|**Waarde**|**Beschrijving**|  
|-|-|
|Onderliggende|Het nieuwe domein is een onderliggend element van een bestaand domein.|  
|Forest|Het nieuwe domein, is het eerste domein in een nieuw forest van domeinstructuren.|  
|Structuur|Het nieuwe domein, is de hoofdmap van een nieuwe structuur in een bestaand forest.|  

|**Voorbeeld**|  
|-|  
|`[Settings] Priority=Default  [Default] NewDomain=Tree`|  

####  <a name="NewDomainDNSName"></a>NewDomainDNSName  
 Hiermee geeft u de vereiste naam van een nieuwe structuur in een bestaand domein, of wanneer een nieuw forest met domeinen wordt geïnstalleerd.  

|**Geconfigureerd door de eigenschap**|||**De eigenschap is van toepassing op**||  
|-|-|-|-|-|  
|BootStrap.ini|||LTI|\-|  
|CustomSettings.ini|\-||||  
|MDT-DB|\-||ZTI|\-|  

|**Waarde**|**Beschrijving**|  
|-|-|
|*naam*|Hiermee geeft u de vereiste naam van een nieuwe structuur in een bestaand domein, of wanneer een nieuw forest met domeinen wordt geïnstalleerd|  

|**Voorbeeld**|  
|-|  
|`[Settings] Priority=Default  [Default] NewDomainDNSName=newdom.WoodGroveBank.com`|  

####  <a name="Order"></a>Volgorde  
 De sorteervolgorde voor de resultatenset van een databasequery. De resultatenset is gebaseerd op de configuratie-instellingen van de **Database**, **tabel**, **SQLServer**, **Parameters**, en **ParameterCondition** eigenschappen. Meer dan een eigenschap kan de resultaten wilt sorteren door meer dan één eigenschap worden opgegeven.  

 Bijvoorbeeld, als **volgorde\=reeks** is opgegeven in het bestand CustomSettings.ini, wordt er een **ORDER BY** sequence-component is toegevoegd aan de query. **Opgeven van Order\=zorg**, **Model** voegt een **volgorde door te maken, Model** component aan de query.  

|**Geconfigureerd door de eigenschap**|||**De eigenschap is van toepassing op**||  
|-|-|-|-|-|  
|BootStrap.ini|\-||LTI|\-|  
|CustomSettings.ini|\-||||  
|MDT-DB|||ZTI|\-|  

|**Waarde**|**Beschrijving**|  
|-|-|
|*Eigenschap1, eigenschap 2...*|Eigenschappen voor het definiëren van de sorteervolgorde voor de resultatenset \(waar *propertyn* geeft de eigenschappen in de criteria sorteren\)|  

|**Voorbeeld**|  
|-|  
|`[Settings] Priority=Computers, Default  [Default] OSInstall=YES ScanStateArgs=/v:5 /o /c LoadStateArgs=/v:5 /c /lac  [Computers] SQLServer=NYC-SQL-01 SQLShare=SQL$ NetLib=DBNMPNTW Database=MDTDB Instance=SQLEnterprise2005 Table=MakeModelSettings Parameters=SerialNumber, AssetTag ParameterCondition=OR Order=Make, Model`|  

####  <a name="OrgName"></a>OrgName  
 De naam van de organisatie die eigenaar is van de doelcomputer. Deze waarde wordt ingevoegd in de juiste configuratie-instellingen in Unattend.xml.  

|**Geconfigureerd door de eigenschap**|||**De eigenschap is van toepassing op**||  
|-|-|-|-|-|  
|BootStrap.ini|||LTI|\-|  
|CustomSettings.ini|\-||||  
|MDT-DB|\-||ZTI|\-|  

|**Waarde**|**Beschrijving**|  
|-|-|
|*organigrammen\_naam*|De naam van de organisatie die eigenaar is van de doelcomputer|  

|**Voorbeeld**|  
|-|  
|`[Settings] Priority=MACAddress, Default Properties=CustomProperty, ApplicationInstall  [Default] OSInstall=YES ScanStateArgs=/v:5 /o /c LoadStateArgs=/v:5 /c /lac UserDataLocation=NONE CustomProperty=TRUE OrgName=Woodgrove Bank  [00:0F:20:35:DE:AC] OSDNEWMACHINENAME=HPD530-1 ApplicationInstall=Custom FullName=Woodgrove Bank User  [00:03:FF:FE:FF:FF] OSDNEWMACHINENAME=BVMXP  ApplicationInstall=Minimum FullName=Woodgrove Bank Manager`|  

####  <a name="OSArchitecture"></a>OSArchitecture  
 Het processortype-architectuur voor het beoogde besturingssysteem. Deze eigenschap wordt verwezen tijdens OEM-implementaties. Geldige waarden zijn **x86** en **x64**.  

> [!NOTE]
>  Deze eigenschap wordt dynamisch ingesteld door de MDT-scripts en is niet geconfigureerd in CustomSettings.ini of de MDT-DB. Deze eigenschap behandelen als alleen-lezen.  

|**Geconfigureerd door de eigenschap**|||**De eigenschap is van toepassing op**||  
|-|-|-|-|-|  
|BootStrap.ini|||LTI|\-|  
|CustomSettings.ini|||||  
|MDT-DB|||ZTI||  

|**Waarde**|**Beschrijving**|  
|-|-|
|**x86**|Het processortype-architectuur voor het besturingssysteem is 32-bits.|  
|**x64**|Het processortype-architectuur voor het besturingssysteem is 64-bits.|  

|**Voorbeeld**|  
|-|  
|Geen|  

####  <a name="OSCurrentBuild"></a>OSCurrentBuild  
 Het buildnummer van het besturingssysteem die momenteel worden uitgevoerd.  

> [!NOTE]
>  Deze eigenschap wordt dynamisch ingesteld door de MDT-scripts en is niet geconfigureerd in CustomSettings.ini of de MDT-DB. Deze eigenschap behandelen als alleen-lezen.  

|**Geconfigureerd door de eigenschap**|||**De eigenschap is van toepassing op**||  
|-|-|-|-|-|  
|BootStrap.ini|||LTI|\-|  
|CustomSettings.ini|||||  
|MDT-DB|||ZTI|\-|  

|**Waarde**|**Beschrijving**|  
|-|-|
|**7600**|Windows 7|  
|**9600**|Windows 8.1|  

|**Voorbeeld**|  
|-|  
|Geen|  

####  <a name="OSCurrentVersion"></a>OSCurrentVersion  
 Het versienummer van het besturingssysteem die momenteel worden uitgevoerd.  

> [!NOTE]
>  Deze eigenschap wordt dynamisch ingesteld door de MDT-scripts en is niet geconfigureerd in CustomSettings.ini of de MDT-DB. Deze eigenschap behandelen als alleen-lezen.  

|**Geconfigureerd door de eigenschap**|||**De eigenschap is van toepassing op**||  
|-|-|-|-|-|  
|BootStrap.ini|||LTI|-|  
|CustomSettings.ini|||||  
|MDT-DB|||ZTI|-|  

|**Waarde**|**Beschrijving**|  
|-|-|
|*versie*|De primaire versie besturingssysteem updateversies en buildnummers (major.minor.build). 6.3.9600 vertegenwoordigen bijvoorbeeld Windows 8.1.|  

|**Voorbeeld**|  
|-|  
|Geen|  

####  <a name="OSDAdapterxDescription"></a>OSDAdapterxDescription  
 Geeft de naam van de netwerkverbinding zoals deze wordt weergegeven in het onderdeel Netwerkverbindingen van het Configuratiescherm. De naam mag tussen 0 en 255 tekens.  

 Deze eigenschap geldt alleen voor LTI. Zie voor de equivalente eigenschap voor ZTI [OSDAdapterxName](#OSDAdapterxName).  

> [!NOTE]
>  De*x*in de eigenschappen van deze naam is een tijdelijke aanduiding voor een op nul gebaseerde matrix met netwerkadapterinformatie, zoals **OSDAdapter0Description** of **OSDAdapter1Description**.  

|**Geconfigureerd door de eigenschap**|||**De eigenschap is van toepassing op**||  
|-|-|-|-|-|  
|BootStrap.ini|||LTI|-|  
|CustomSettings.ini|||||  
|MDT-DB|||ZTI||  

|**Waarde**|**Beschrijving**|  
|-|-|
|Beschrijving|De naam van de netwerkverbinding zoals deze wordt weergegeven in het onderdeel Netwerkverbindingen van het Configuratiescherm|  

|**Voorbeeld**|  
|-|  
|Geen|  

####  <a name="OSDAdapterxDNSDomain"></a>OSDAdapterxDNSDomain  
 Hiermee geeft u de DNS-naam (DNS-achtervoegsel) die wordt toegewezen aan de netwerkverbinding. Deze eigenschap geldt alleen voor ZTI. Zie voor LTI, de [OSDAdapterxDNSSuffix](#OSDAdapterxDNSSuffix) eigenschap.  

> [!NOTE]
>  De*x*in de eigenschappen van deze naam is een tijdelijke aanduiding voor een op nul gebaseerde matrix met netwerkadapterinformatie, zoals **OSDAdapter0DNSDomain** of **OSDAdapter1DNSDomain**.  

|**Geconfigureerd door de eigenschap**|||**De eigenschap is van toepassing op**||  
|-|-|-|-|-|  
|BootStrap.ini|||LTI||  
|CustomSettings.ini|-||||  
|MDT-DB|-||ZTI|-|  

|**Waarde**|**Beschrijving**|  
|-|-|
|*DNS_domeinnaam*|Een DNS-naam (DNS-achtervoegsel) die wordt toegewezen aan de netwerkverbinding|  

|**Voorbeeld**|  
|-|  
|`[Settings] Priority=Default  [Default] OSDAdapter0DNSDomain=WoodGroveBank.com`|  

####  <a name="OSDAdapterxDNSServerList"></a>OSDAdapterxDNSServerList  
 Dit is een door komma's gescheiden lijst met DNS-server IP-adressen die worden toegewezen aan de netwerkverbinding.  

> [!NOTE]
>  De*x*in de eigenschappen van deze naam is een tijdelijke aanduiding voor een op nul gebaseerde matrix met netwerkadapterinformatie, zoals **OSDAdapter0DNSServerList** of **OSDAdapter1DNSServerList** .  

|**Geconfigureerd door de eigenschap**|||**De eigenschap is van toepassing op**||  
|-|-|-|-|-|  
|BootStrap.ini|||LTI|-|  
|CustomSettings.ini|-||||  
|MDT-DB|-||ZTI|-|  

|**Waarde**|**Beschrijving**|  
|-|-|
|*DNS_servers*|Een door komma's gescheiden lijst met DNS-server IP-adressen die worden toegewezen aan de netwerkverbinding|  

|**Voorbeeld**|  
|-|  
|`[Settings] Priority=Default  [Default] OSDAdapter0DNSServerList=192.168.0.254,192.168.100.254`|  

####  <a name="OSDAdapterxDNSSuffix"></a>OSDAdapterxDNSSuffix  
 Een DNS-achtervoegsel dat wordt toegewezen aan de netwerkverbinding. Deze eigenschap geldt alleen voor LTI. Zie voor ZTI, de [OSDAdapterxDNSDomain](#OSDAdapterxDNSDomain) eigenschap.  

> [!NOTE]
>  De*x*in de eigenschappen van deze naam is een tijdelijke aanduiding voor een op nul gebaseerde matrix met netwerkadapterinformatie, zoals **OSDAdapter0DNSSuffix** of **OSDAdapter1DNSSuffix**.  

|**Geconfigureerd door de eigenschap**|||**De eigenschap is van toepassing op**||  
|-|-|-|-|-|  
|BootStrap.ini|||LTI|-|  
|CustomSettings.ini|-||||  
|MDT-DB|-||ZTI||  

|**Waarde**|**Beschrijving**|  
|-|-|
|*Dns_achtervoegsel*|Een DNS-achtervoegsel dat wordt toegewezen aan de netwerkverbinding|  

|**Voorbeeld**|  
|-|  
|`[Settings] Priority=Default  [Default] OSDAdapter0DNSSuffix= WoodGroveBank.com`|  

####  <a name="OSDAdapterxEnableDHCP"></a>OSDAdapterxEnableDHCP  
 Hiermee geeft u op of de netwerkverbinding wordt geconfigureerd via DHCP.  

> [!NOTE]
>  De*x*in de eigenschappen van deze naam is een tijdelijke aanduiding voor een op nul gebaseerde matrix met netwerkadapterinformatie, zoals **OSDAdapter0EnableDHCP** of **OSDAdapter1EnableDHCP**.  

|**Geconfigureerd door de eigenschap**|||**De eigenschap is van toepassing op**||  
|-|-|-|-|-|  
|BootStrap.ini|||LTI|-|  
|CustomSettings.ini|-||||  
|MDT-DB|-||ZTI|-|  

|**Waarde**|**Beschrijving**|  
|-|-|
|**DE WAARDE TRUE**|De netwerkverbinding wordt geconfigureerd via DHCP.|  
|**DE WAARDE FALSE**|De netwerkverbinding worden geconfigureerd met statische configuratie.|  

|**Voorbeeld**|  
|-|  
|`[Settings] Priority=Default  [Default] OSDAdapter0EnableDHCP=TRUE`|  

####  <a name="OSDAdapterxEnableDNSRegistration"></a>OSDAdapterxEnableDNSRegistration  
 Hiermee geeft u op of de DNS-registratie is ingeschakeld op de netwerkverbinding.  

> [!NOTE]
>  De*x*in de eigenschappen van deze naam is een tijdelijke aanduiding voor een op nul gebaseerde matrix met netwerkadapterinformatie, zoals **OSDAdapter0EnableDNSRegistration** of  **OSDAdapter1EnableDNSRegistration**.  

|**Geconfigureerd door de eigenschap**|||**De eigenschap is van toepassing op**||  
|-|-|-|-|-|  
|BootStrap.ini|||LTI|-|  
|CustomSettings.ini|-||||  
|MDT-DB|-||ZTI|-|  

|**Waarde**|**Beschrijving**|  
|-|-|
|**DE WAARDE TRUE**|Hiermee kunt DNS-registratie|  
|**DE WAARDE FALSE**|Schakelt de DNS-registratie|  

|**Voorbeeld**|  
|-|  
|`[Settings] Priority=Default  [Default] OSDAdapter0EnableDNSRegistration=TRUE`|  

####  <a name="OSDAdapterxEnableFullDNSRegistration"></a>OSDAdapterxEnableFullDNSRegistration  
 Hiermee geeft u op of de volledige DNS-registratie is ingeschakeld op de netwerkverbinding.  

> [!NOTE]
>  De*x*in de eigenschappen van deze naam is een tijdelijke aanduiding voor een op nul gebaseerde matrix met netwerkadapterinformatie, zoals **OSDAdapter0EnableFullDNSRegistration** of  **OSDAdapter1EnableFullDNSRegistration**.  

|**Geconfigureerd door de eigenschap**|||**De eigenschap is van toepassing op**||  
|-|-|-|-|-|  
|BootStrap.ini|||LTI|-|  
|CustomSettings.ini|-||||  
|MDT-DB|-||ZTI|-|  

|**Waarde**|**Beschrijving**|  
|-|-|
|**DE WAARDE TRUE**|Hiermee volledige DNS-registratie|  
|**DE WAARDE FALSE**|De volledige DNS-registratie wordt uitgeschakeld|  

|**Voorbeeld**|  
|-|  
|`[Settings] Priority=Default  [Default] OSDAdapter0EnableFullDNSRegistration=TRUE`|  

####  <a name="OSDAdapterxEnableLMHosts"></a>OSDAdapterxEnableLMHosts  
 Hiermee geeft u op of LMHOSTS-lookup wordt ingeschakeld op de netwerkverbinding.  

> [!NOTE]
>  De*x*in de eigenschappen van deze naam is een tijdelijke aanduiding voor een op nul gebaseerde matrix met netwerkadapterinformatie, zoals **OSDAdapter0EnableLMHosts** of **OSDAdapter1EnableLMHosts** .  

|**Geconfigureerd door de eigenschap**|||**De eigenschap is van toepassing op**||  
|-|-|-|-|-|  
|BootStrap.ini|||LTI|-|  
|CustomSettings.ini|-||||  
|MDT-DB|-||ZTI|-|  

|**Waarde**|**Beschrijving**|  
|-|-|
|**DE WAARDE TRUE**|Hiermee LMHOSTS-lookup|  
|**DE WAARDE FALSE**|LMHOSTS-lookup uitgeschakeld|  

|**Voorbeeld**|  
|-|  
|`[Settings] Priority=Default  [Default] OSDAdapter0EnableLMHosts=TRUE`|  

####  <a name="OSDAdapterxEnableIPProtocolFiltering"></a>OSDAdapterxEnableIPProtocolFiltering  
 Deze eigenschap geeft aan of de IP-protocol filtering moet worden ingeschakeld op de netwerkverbinding.  

 De*x*in de naam van deze eigenschap is een tijdelijke aanduiding voor een op nul gebaseerde matrix met netwerkgegevens adapter, zoals *OSDAdapter0EnableIPProtocolFiltering* of  **OSDAdapter1EnableIPProtocolFiltering**.  

|**Geconfigureerd door de eigenschap**|||**De eigenschap is van toepassing op**||  
|-|-|-|-|-|  
|BootStrap.ini|||LTI|\-|  
|CustomSettings.ini|\-||||  
|MDT-DB|\-||ZTI|\-|  

|**Waarde**|**Beschrijving**|  
|-|-|
|**DE WAARDE TRUE**|Kan IP-protocol filteren|  
|**DE WAARDE FALSE**|Wordt het IP-protocol filteren uitgeschakeld|  

|**Voorbeeld**|  
|-|  
|`[Settings] Priority=Default  [Default] OSDAdapter0EnableIPProtocolFiltering =TRUE`|  

####  <a name="OSDAdapterxEnableTCPFiltering"></a>OSDAdapterxEnableTCPFiltering  
 Hiermee geeft u op of TCP\/IP-filtering moet worden ingeschakeld op de netwerkverbinding. Deze eigenschap geldt alleen voor ZTI. Zie voor LTI, de [OSDAdapterxEnableTCPIPFiltering](#OSDAdapterxEnableTCPIPFiltering) eigenschap.  

> [!NOTE]
>  De*x*in deze de naam van eigenschap is een tijdelijke aanduiding voor nul\-op basis van de matrix met netwerkadapterinformatie, zoals **OSDAdapter0EnableTCPFiltering** of  **OSDAdapter1EnableTFiltering**.  

|**Geconfigureerd door de eigenschap**|||**De eigenschap is van toepassing op**||  
|-|-|-|-|-|  
|BootStrap.ini|||LTI|\-|  
|CustomSettings.ini|\-||||  
|MDT-DB|\-||ZTI|\-|  

|**Waarde**|**Beschrijving**|  
|-|-|
|**DE WAARDE TRUE**|Kan TCP\/IP-filtering|  
|**DE WAARDE FALSE**|Hiermee schakelt u TCP\/IP-filtering|  

|**Voorbeeld**|  
|-|  
|`[Settings] Priority=Default  [Default] OSDAdapter0EnableTCPFiltering=TRUE`|  

####  <a name="OSDAdapterxEnableTCPIPFiltering"></a>OSDAdapterxEnableTCPIPFiltering  
 Hiermee geeft u op of TCP\/IP-filtering moet worden ingeschakeld op de netwerkverbinding. Deze eigenschap geldt alleen voor LTI. Zie voor ZTI, de [OSDAdapterxEnableTCPFiltering](#OSDAdapterxEnableTCPFiltering) eigenschap.  

> [!NOTE]
>  De*x*in de eigenschappen van deze naam is een tijdelijke aanduiding voor nul\-op basis van de matrix met netwerkadapterinformatie, zoals **OSDAdapter0EnableTCPIPFiltering** of  **OSDAdapter1EnableTCPIPFiltering**.  

|**Geconfigureerd door de eigenschap**|||**De eigenschap is van toepassing op**||  
|-|-|-|-|-|  
|BootStrap.ini|||LTI|\-|  
|CustomSettings.ini|\-||||  
|MDT-DB|\-||ZTI||  

|**Waarde**|**Beschrijving**|  
|-|-|
|**DE WAARDE TRUE**|Kan TCP\/IP-filtering|  
|**DE WAARDE FALSE**|Hiermee schakelt u TCP\/IP-filtering|  

|**Voorbeeld**|  
|-|  
|`[Settings] Priority=Default  [Default] OSDAdapter0EnableTCPIPFiltering=TRUE`|  

####  <a name="OSDAdapterxEnableWINS"></a>OSDAdapterxEnableWINS  
 Hiermee geeft u op of WINS wordt ingeschakeld op de netwerkverbinding.  

> [!NOTE]
>  De*x*in de eigenschappen van deze naam is een tijdelijke aanduiding voor nul\-op basis van de matrix met netwerkadapterinformatie, zoals **OSDAdapter0EnableWINS** of  **OSDAdapter1EnableWINS**.  

> [!CAUTION]
>  Waarde van deze eigenschap moet in hoofdletters worden opgegeven zodat de implementatiescripts kunnen correct worden gelezen.  

|**Geconfigureerd door de eigenschap**|||**De eigenschap is van toepassing op**||  
|-|-|-|-|-|  
|BootStrap.ini|||LTI|\-|  
|CustomSettings.ini|\-||||  
|MDT-DB|\-||ZTI|\-|  

|**Waarde**|**Beschrijving**|  
|-|-|
|**DE WAARDE TRUE**|Hiermee WINS|  
|**DE WAARDE FALSE**|Hiermee schakelt WINS|  

|**Voorbeeld**|  
|-|  
|`[Settings] Priority=Default  [Default] OSDAdapter0EnableWINS=TRUE OSDAdapter0WINSServerList=192.168.0.1,192.168.100.1`|  

####  <a name="OSDAdapterxGatewayCostMetric"></a>OSDAdapterxGatewayCostMetric  
 Een komma\-gescheiden lijst met kosten metrische Gatewaywaarden opgegeven als gehele getallen of de tekenreeks "Automatisch" \(als leeg is, gebruikt u "Automatisch"\) die op de verbinding wordt geconfigureerd.  

> [!NOTE]
>  De*x*in de eigenschappen van deze naam is een tijdelijke aanduiding voor nul\-op basis van de matrix met netwerkadapterinformatie, zoals **OSDAdapter0GatewayCostMetric** of  **OSDAdapter1GatewayCostMetric**.  

|**Geconfigureerd door de eigenschap**|||**De eigenschap is van toepassing op**||  
|-|-|-|-|-|  
|BootStrap.ini|||LTI|\-|  
|CustomSettings.ini|\-||||  
|MDT-DB|\-||ZTI|\-|  

|**Waarde**|**Beschrijving**|  
|-|-|
|*kosten\_metrische gegevens*|Een komma\-gescheiden lijst met kosten metrische Gatewaywaarden|  

|**Voorbeeld**|  
|-|  
|`[Settings] Priority=Default  [Default] OSDAdapter0GatewayCostMetrics=Automatic`|  

####  <a name="OSDAdapterxGateways"></a>OSDAdapterxGateways  
 Een komma\-gescheiden lijst van gateways moet worden toegewezen aan de netwerkverbinding.  

> [!NOTE]
>  De*x*in de eigenschappen van deze naam is een tijdelijke aanduiding voor nul\-op basis van de matrix met netwerkadapterinformatie, zoals **OSDAdapter0Gateways** of  **OSDAdapter1Gateways**.  

|**Geconfigureerd door de eigenschap**|||**De eigenschap is van toepassing op**||  
|-|-|-|-|-|  
|BootStrap.ini|||LTI|\-|  
|CustomSettings.ini|\-||||  
|MDT-DB|\-||ZTI|\-|  

|**Waarde**|**Beschrijving**|  
|-|-|
|*gateways*|Een komma\-gescheiden lijst van gateways|  

|**Voorbeeld**|  
|-|  
|`[Settings] Priority=Default  [Default] OSDAdapter0Gateways=192.168.0.1,192.168.100.1`|  

####  <a name="OSDAdapterxIPAddressList"></a>OSDAdapterxIPAddressList  
 Een komma\-gescheiden lijst met IP-adressen worden toegewezen aan de netwerkverbinding.  

> [!NOTE]
>  De*x*in de eigenschappen van deze naam is een tijdelijke aanduiding voor nul\-op basis van de matrix met netwerkadapterinformatie, zoals **OSDAdapter0IPAddressList** of  **OSDAdapter1IPAddressList**.  

|**Geconfigureerd door de eigenschap**|||**De eigenschap is van toepassing op**||  
|-|-|-|-|-|  
|BootStrap.ini|||LTI|\-|  
|CustomSettings.ini|\-||||  
|MDT-DB|\-||ZTI||  

|**Waarde**|**Beschrijving**|  
|-|-|
|*IP\_adressen*|Een door komma's gescheiden lijst met IP-adressen|  

|**Voorbeeld**|  
|-|  
|`[Settings] Priority=Default  [Default] OSDAdapter0IPAddressList=192.168.0.40,192.168.100.40 OSDAdapter0SubnetMask=255.255.255.0,255.255.255.0`|  

####  <a name="OSDAdapterxIPProtocolFilterList"></a>OSDAdapterxIPProtocolFilterList  
 Een komma\-gescheiden lijst met IP-protocolfilters worden toegewezen aan de netwerkverbinding. Deze eigenschap kan worden geconfigureerd met behulp van het CustomSettings.ini-bestand of de MDT-database, maar niet de Workbench-implementatie. Als Configuration Manager is het ook worden geconfigureerd met behulp van een **netwerkinstellingen toepassen** takenreeksstap.  

> [!NOTE]
>  De*x*in de eigenschappen van deze naam is een tijdelijke aanduiding voor nul\-op basis van de matrix met netwerkadapterinformatie, zoals **OSDAdapter0IPProtocolFilterList** of  **OSDAdapter1IPProtocolFilterList**.  

|**Geconfigureerd door de eigenschap**|||**De eigenschap is van toepassing op**||  
|-|-|-|-|-|  
|BootStrap.ini|||LTI|\-|  
|CustomSettings.ini|\-||||  
|MDT-DB|\-||ZTI|\-|  

|**Waarde**|**Beschrijving**|  
|-|-|
|*protocol\_filter\_lijst*|Een komma\-gescheiden lijst met IP-protocol-filters|  

|**Voorbeeld**|  
|-|  
|`[Settings] Priority=Default  [Default] OSDAdapter0IPProtocolFilterList=a list of approved IP protocols`|  

####  <a name="OSDAdapterxMacAddress"></a>OSDAdapterxMacAddress  
 De opgegeven configuratie-instellingen aan de netwerkinterfacekaart die overeenkomt met het opgegeven MAC-adres toewijzen.  

> [!NOTE]
>  De*x*in de eigenschappen van deze naam is een tijdelijke aanduiding voor nul\-op basis van de matrix met netwerkadapterinformatie, zoals **OSDAdapter0MacAddress** of  **OSDAdapter1MacAddress**.  

|**Geconfigureerd door de eigenschap**|||**De eigenschap is van toepassing op**||  
|-|-|-|-|-|  
|BootStrap.ini|||LTI|\-|  
|CustomSettings.ini|\-||||  
|MDT-DB|\-||ZTI|\-|  

|**Waarde**|**Beschrijving**|  
|-|-|
|*MAC\_adres*|Netwerkadapter MAC-adres|  

|**Voorbeeld**|  
|-|  
|`[Settings] Priority=Default  [Default] OSDAdapter0MacAddress=00:0C:29:67:A3:6B`|  

####  <a name="OSDAdapterxName"></a>OSDAdapterxName  
 De opgegeven configuratie-instellingen toewijzen aan de netwerkadapter die overeenkomt met de opgegeven naam. Deze eigenschap geldt alleen voor ZTI. Zie voor de equivalente eigenschap voor LTI [OSDAdapterxDescription](#OSDAdapterxDescription).  

> [!NOTE]
>  De*x*in de eigenschappen van deze naam is een tijdelijke aanduiding voor nul\-op basis van de matrix met netwerkadapterinformatie, zoals **OSDAdapter0Name** of **OSDAdapter1Name**.  

|**Geconfigureerd door de eigenschap**|||**De eigenschap is van toepassing op**||  
|-|-|-|-|-|  
|BootStrap.ini|||LTI||  
|CustomSettings.ini|\-||||  
|MDT-DB|\-||ZTI|\-|  

|**Waarde**|**Beschrijving**|  
|-|-|
|*naam*|Naam van de netwerkadapter|  

|**Voorbeeld**|  
|-|  
|`[Settings] Priority=Default  [Default] OSDAdapter0Name=3Com 3C920 Integrated Fast Ethernet Controller`|  

####  <a name="OSDAdapterxSubnetMask"></a>OSDAdapterxSubnetMask  
 Een komma\-gescheiden lijst met IP-subnetmaskers moet worden toegewezen aan de netwerkverbinding.  

> [!NOTE]
>  De*x*in de eigenschappen van deze naam is een tijdelijke aanduiding voor nul\-op basis van de matrix met netwerkadapterinformatie, zoals **OSDAdapter0SubnetMask** of  **OSDAdapter1SubnetMask**.  

|**Geconfigureerd door de eigenschap**|||**De eigenschap is van toepassing op**||  
|-|-|-|-|-|  
|BootStrap.ini|||LTI|\-|  
|CustomSettings.ini|\-||||  
|MDT-DB|\-||ZTI|\-|  

|**Waarde**|**Beschrijving**|  
|-|-|
|*subnet\_maskers*|Een komma\-gescheiden lijst met IP-subnetmaskers|  

|**Voorbeeld**|  
|-|  
|`[Settings] Priority=Default  [Default] OSDAdapter0IPAddressList=192.168.0.40,192.168.100.40 OSDAdapter0SubnetMask=255.255.255.0,255.255.255.0`|  

#### <a name="osdadapterxtcpfilterportlist"></a>OSDAdapterxTCPFilterPortList  
 Een komma\-gescheiden lijst met TCP-poorten filter moet worden toegewezen aan de netwerkverbinding. Deze eigenschap kan worden geconfigureerd met behulp van het CustomSettings.ini-bestand of de MDT-database, maar niet de Workbench-implementatie. Als Configuration Manager is het ook worden geconfigureerd met behulp van een **netwerkinstellingen toepassen** takenreeksstap.  

> [!NOTE]
>  De*x*in de eigenschappen van deze naam is een tijdelijke aanduiding voor nul\-op basis van de matrix met netwerkadapterinformatie, zoals **OSDAdapter0TCPFilterPortList** of  **OSDAdapter1TCPFilterPortList**.  

|**Geconfigureerd door de eigenschap**|||**De eigenschap is van toepassing op**||  
|-|-|-|-|-|  
|BootStrap.ini|||LTI|\-|  
|CustomSettings.ini|\-||||  
|MDT-DB|\-||ZTI|\-|  

|**Waarde**|**Beschrijving**|  
|-|-|
|*poort\_lijst*|Een komma\-gescheiden lijst van TCP-\/filter-IP-poorten|  

|**Voorbeeld**|  
|-|  
|`[Settings] Priority=Default  [Default] OSDAdapter0TCPFilterPortList=a list of approved TCP ports`|  

####  <a name="OSDAdapterxTCPIPNetBiosOptions"></a>OSDAdapterxTCPIPNetBiosOptions  
 Hiermee geeft u de TCP\/NetBIOS-IP-opties worden toegewezen aan de netwerkverbinding.  

> [!NOTE]
>  De*x*in de eigenschappen van deze naam is een tijdelijke aanduiding voor nul\-op basis van de matrix met netwerkadapterinformatie, zoals **OSDAdapter0TCPIPNetBiosOptions** of  **OSDAdapter1TCPIPNetBiosOptions**.  

|**Geconfigureerd door de eigenschap**|||**De eigenschap is van toepassing op**||  
|-|-|-|-|-|  
|BootStrap.ini|||LTI|\-|  
|CustomSettings.ini|\-||||  
|MDT-DB|\-||ZTI|\-|  

|**Waarde**|**Beschrijving**|  
|-|-|
|**0**|Doorsturen via IP uitschakelen.|  
|**1**|Doorsturen via IP inschakelen.|  

|**Voorbeeld**|  
|-|  
|`[Settings] Priority=Default  [Default] OSDAdapter0TCPIPNetBiosOptions=0`|  

####  <a name="OSDAdapterxUDPFilterPortList"></a>OSDAdapterxUDPFilterPortList  
 Een komma\-gescheiden lijst met User Datagram Protocol \(UDP\) filteren poorten moet worden toegewezen aan de netwerkverbinding. Deze eigenschap kan worden geconfigureerd met behulp van het CustomSettings.ini-bestand en de MDT-database, maar niet de Workbench-implementatie. Als Configuration Manager is het ook worden geconfigureerd met behulp van een **netwerkinstellingen toepassen** takenreeksstap.  

> [!NOTE]
>  De*x*in de eigenschappen van deze naam is een tijdelijke aanduiding voor nul\-op basis van de matrix met netwerkadapterinformatie, zoals **OSDAdapter0UDPFilterPortList** of  **OSDAdapter1UDPFilterPortList**.  

|**Geconfigureerd door de eigenschap**|||**De eigenschap is van toepassing op**||  
|-|-|-|-|-|  
|BootStrap.ini|||LTI|\-|  
|CustomSettings.ini|\-||||  
|MDT-DB|\-||ZTI|\-|  

|**Waarde**|**Beschrijving**|  
|-|-|
|*poort\_lijst*|Een komma\-gescheiden lijst van filter-UDP-poorten|  

|**Voorbeeld**|  
|-|  
|`[Settings] Priority=Default  [Default] OSDAdapter0UDPFilterPortList=a list of approved UDP ports`|  

####  <a name="OSDAdapterxWINSServerList"></a>OSDAdapterxWINSServerList  
 Een twee\-element, door komma's\-gescheiden lijst met WINS-server-IP-adressen aan worden toegewezen aan de netwerkverbinding.  

> [!NOTE]
>  De*x*in de eigenschappen van deze naam is een tijdelijke aanduiding voor nul\-op basis van de matrix met netwerkadapterinformatie, zoals **OSDAdapter0WINSServerList** of  **OSDAdapter1WINSServerList**.  

|**Geconfigureerd door de eigenschap**|||**De eigenschap is van toepassing op**||  
|-|-|-|-|-|  
|BootStrap.ini|||LTI|\-|  
|CustomSettings.ini|\-||||  
|MDT-DB|\-||ZTI|\-|  

|**Waarde**|**Beschrijving**|  
|-|-|
|*WINS-\_server\_lijst*|Een komma\-gescheiden lijst met IP-adressen van WINS-server|  

|**Voorbeeld**|  
|-|  
|`[Settings] Priority=Default  [Default] OSDAdapter0EnableWINS=TRUE OSDAdapter0WINSServerList=192.168.0.1,192.168.100.1`|  

####  <a name="OSDAdapterCount"></a>OSDAdapterCount  
 Hiermee geeft u het aantal netwerkverbindingen die moeten worden geconfigureerd.  

|**Geconfigureerd door de eigenschap**|||**De eigenschap is van toepassing op**||  
|-|-|-|-|-|  
|BootStrap.ini|||LTI|\-|  
|CustomSettings.ini|\-||||  
|MDT-DB|\-||ZTI|\-|  

|**Waarde**|**Beschrijving**|  
|-|-|
|Aantal|Het aantal netwerkadapters|  

|**Voorbeeld**|  
|-|  
|`[Settings] Priority=Default  [Default] OSDAdapterCount=1 OSDAdapter0EnableDHCP=FALSE OSDAdapter0IPAddressList=192.168.0.40,192.168.100.40 OSDAdapter0SubnetMask=255.255.255.0,255.255.255.0 OSDAdapter0Gateways=192.168.0.1,192.168.100.1 OSDAdapter0EnableWINS=TRUE OSDAdapter0WINSServerList=192.168.0.1,192.168.100.1 OSDAdapter0TCPIPNetBiosOptions=0 OSDAdapter0MacAddress=00:0C:29:67:A3:6B OSDAdapter0GatewayCostMetrics=Automatic OSDAdapter0EnableTCPIPFiltering=TRUE OSDAdapter0EnableLMHosts=TRUE OSDAdapter0EnableFullDNSRegistration=TRUE OSDAdapter0EnableDNSRegistration=TRUE OSDAdapter0DNSSuffix=WoodGroveBank.com`|  

#### <a name="osdanswerfilepath"></a>OSDAnswerFilePath  
 Hiermee geeft u het pad naar het antwoordbestand moet worden gebruikt tijdens de OEM-implementaties.  

> [!NOTE]
>  Deze eigenschap wordt dynamisch ingesteld door de MDT-scripts en is niet geconfigureerd in CustomSettings.ini of de MDT-DB. Deze eigenschap behandelen als alleen-lezen.  

|**Geconfigureerd door de eigenschap**|||**De eigenschap is van toepassing op**||  
|-|-|-|-|-|  
|BootStrap.ini|||LTI|\-|  
|CustomSettings.ini|||||  
|MDT-DB|||ZTI||  

|**Waarde**|**Beschrijving**|  
|-|-|
|*bestand\_pad*|Hiermee geeft u het pad naar het antwoordbestand moet worden gebruikt tijdens de OEM-implementaties|  

|**Voorbeeld**|  
|-|  
|Geen|  

####  <a name="OSDBitLockerCreateRecoveryPassword"></a>OSDBitLockerCreateRecoveryPassword  
 Een Boolean die aangeeft of het proces wordt een herstelsleutel voor BitLocker gemaakt. De sleutel wordt gebruikt voor het herstellen van gegevens op een volume BitLocker is versleuteld. Deze sleutel is cryptografisch gelijk is aan een opstartsleutel. Indien beschikbaar, ontsleutelt de herstelsleutel de VMK die op zijn beurt, de FVEK ontsleutelt.  

> [!NOTE]
>  Waarde van deze eigenschap moet in hoofdletters worden opgegeven zodat de implementatiescripts kunnen correct worden gelezen.  

|**Geconfigureerd door de eigenschap**|||**De eigenschap is van toepassing op**||  
|-|-|-|-|-|  
|BootStrap.ini|||LTI|\-|  
|CustomSettings.ini|\-||||  
|MDT-DB|\-||ZTI|\-|  

|**Waarde**|**Beschrijving**|  
|-|-|
|**AD**|Een herstelsleutel wordt gemaakt.|  
|Niet opgegeven|Een herstelsleutel is niet gemaakt.|  

|**Voorbeeld**|  
|-|  
|`[Settings] Priority=Default  [Default] BDEInstallSuppress=NO BDEDriveLetter=S: BDEDriveSize=2000 OSDBitLockerMode=TPMKey OSDBitLockerCreateRecoveryPassword=AD OSDBitLockerStartupKeyDrive=C:`|  

####  <a name="OSDBitLockerMode"></a>OSDBitLockerMode  
 Het type van de installatie van BitLocker moet worden uitgevoerd. Beveiligen van de doelcomputer met behulp van een van de volgende methoden:  

-   Een TPM-microcontroller  

-   Een TPM en een externe opstartsleutel \(met een sleutel die doorgaans op een USB-Flashstation is opgeslagen\)  

-   Een TPM en PINCODE  

-   Een externe opstartsleutel  

|**Geconfigureerd door de eigenschap**|||**De eigenschap is van toepassing op**||  
|-|-|-|-|-|  
|BootStrap.ini|||LTI|\-|  
|CustomSettings.ini|\-||||  
|MDT-DB|\-||ZTI|\-|  

|**Waarde**|**Beschrijving**|  
|-|-|
|**TPM**|Beveilig de computer met TPM. De TPM is een microcontroller waarin sleutels, wachtwoorden en digitale certificaten wordt opgeslagen. De microcontroller is meestal een integraal onderdeel van het moederbord van de computer.|  
|**TPMKey**|De computer met TPM en een opstartsleutel te beschermen. Gebruik deze optie voor het maken van een opstartsleutel en op te slaan op een USB-Flashstation. De opstartsleutel moet aanwezig zijn in de poort telkens wanneer de computer wordt gestart.|  
|**TPMPin**|Beveilig de computer met TPM en een pincode. Gebruik deze optie in combinatie met de **BDEPin** eigenschap.<br /><br /> Opmerking:<br /><br /> Deze waarde is niet geldig bij gebruik van ZTI.|  
|**Sleutel**|Beveilig de computer met een externe sleutel \(de herstelsleutel\) die kan worden opgeslagen in een map in AD DS of afgedrukt.|  

|**Voorbeeld**|  
|-|  
|`[Settings] Priority=Default  [Default] BDEInstallSuppress=NO BDEDriveLetter=S: BDEDriveSize=2000 OSDBitLockerMode=TPM OSDBitLockerCreateRecoveryPassword=AD`|  

####  <a name="OSDBitLockerRecoveryPassword"></a>OSDBitLockerRecoveryPassword  
 In plaats van een willekeurig herstelwachtwoord te genereren gebruikt de takenreeksactie **BitLocker inschakelen** de opgegeven waarde als het herstelwachtwoord. De waarde moet een geldig numeriek BitLocker-herstelwachtwoord zijn.  

|**Geconfigureerd door de eigenschap**|||**De eigenschap is van toepassing op**||  
|-|-|-|-|-|  
|BootStrap.ini|||LTI|\-|  
|CustomSettings.ini|\-||||  
|MDT-DB|\-||ZTI|\-|  

|**Waarde**|**Beschrijving**|  
|-|-|
|*wachtwoord*|Een geldig 48\-wachtwoord cijfers|  

|**Voorbeeld**|  
|-|  
|`[Settings] Priority=Default  [Default] BDEInstallSuppress=NO BDEDriveLetter=S: BDEDriveSize=2000 OSDBitLockerMode=TPMKey OSDBitLockerCreateRecoveryPassword=AD OSDBitLockerRecoveryPassword=621280128854709621167486709731081433315062587367 OSDBitLockerStartupKeyDrive=C:`|  

####  <a name="OSDBitLockerStartupKey"></a>OSDBitLockerStartupKey  
 In plaats van een willekeurige opstartsleutel voor de sleutelbeheeroptie genereren **opstartsleutel op USB alleen**, wordt de **BitLocker inschakelen** takenreeksactie waarde gebruikt als de opstartsleutel. De waarde moet een geldige Base64\-BitLocker-opstartsleutel gecodeerd.  

|**Geconfigureerd door de eigenschap**|||**De eigenschap is van toepassing op**||  
|-|-|-|-|-|  
|BootStrap.ini|||LTI|\-|  
|CustomSettings.ini|\-||||  
|MDT-DB|\-||ZTI|\-|  

|**Waarde**|**Beschrijving**|  
|-|-|
|*opstartsleutel moet*|Base64\-BitLocker-opstartsleutel gecodeerd|  

|**Voorbeeld**|  
|-|  
|`[Settings] Priority=Default  [Default] BDEInstallSuppress=NO BDEDriveLetter=S: BDEDriveSize=2000 BDEInstall=KEY OSDBitLockerCreateRecoveryPassword=AD OSDBitLockerStartupKey=8F4922B8-2D8D-479E-B776-12629A361049`|  

####  <a name="OSDBitLockerStartupKeyDrive"></a>OSDBitLockerStartupKeyDrive  
 De locatie voor het opslaan van de BitLocker-herstelsleutel en de opstartsleutel.  

|**Geconfigureerd door de eigenschap**|||**De eigenschap is van toepassing op**||  
|-|-|-|-|-|  
|BootStrap.ini|||LTI|\-|  
|CustomSettings.ini|\-||||  
|MDT-DB|\-||ZTI|\-|  

|**Waarde**|**Beschrijving**|  
|-|-|
|*locatie*|De opslaglocatie voor de herstelsleutel en de opstartsleutel \(beide lokaal op de doelcomputer of op een UNC-die naar een gedeelde netwerkmap verwijst\)|  

|**Voorbeeld**|  
|-|  
|`[Settings] Priority=Default  [Default] BDEInstallSuppress=NO BDEDriveLetter=S: BDEDriveSize=2000 OSDBitLockerMode=TPMKey OSDBitLocker CreateRecoveryPassword=AD OSDBitLockerStartupKeyDrive=C:`|  

####  <a name="OSDBitLockerTargetDrive"></a>OSDBitLockerTargetDrive  
 Hiermee geeft u de schijf worden versleuteld. Het standaardstation is het station waarop het besturingssysteem.  

|**Geconfigureerd door de eigenschap**|||**De eigenschap is van toepassing op**||  
|-|-|-|-|-|  
|BootStrap.ini|||LTI|\-|  
|CustomSettings.ini|\-||||  
|MDT-DB|\-||ZTI|\-|  

|**Waarde**|**Beschrijving**|  
|-|-|
|*station*|Het station dat moet worden gecodeerd|  

|**Voorbeeld**|  
|-|  
|`[Settings] Priority=Default  [Default] BDEInstallSuppress=NO BDEDriveLetter=S: BDEDriveSize=2000 BDERecoveryPassword=TRUE OSDBitLockerMode=TPMKey OSDBitLockerCreateRecoveryPassword=AD OSDBitLockerTargetDrive=C:`|  

####  <a name="OSDBitLockerWaitForEncryption"></a>OSDBitLockerWaitForEncryption  
 Hiermee geeft u het implementatieproces moet niet doorgaan totdat BitLocker het versleutelingsproces voor alle opgegeven schijven is voltooid. TRUE op te geven, kan de benodigde tijd voor het voltooien van het implementatieproces aanzienlijk verhogen.  

> [!CAUTION]
>  Waarde van deze eigenschap moet in hoofdletters worden opgegeven zodat de implementatiescripts kunnen correct worden gelezen.  

|**Geconfigureerd door de eigenschap**|||**De eigenschap is van toepassing op**||  
|-|-|-|-|-|  
|BootStrap.ini|||LTI|\-|  
|CustomSettings.ini|\-||||  
|MDT-DB|\-||ZTI|\-|  

|**Waarde**|**Beschrijving**|  
|-|-|
|**DE WAARDE TRUE**|Hiermee geeft u aan dat het implementatieproces totdat de stationsversleuteling wachten moet te voltooien|  
|**DE WAARDE FALSE**|Hiermee geeft u aan dat het implementatieproces niet totdat-stationsversleuteling wachten moet te voltooien|  

|**Voorbeeld**|  
|-|  
|`[Settings] Priority=Default  [Default] BDEInstallSuppress=NO BDEDriveLetter=S: BDEDriveSize=2000 OSDBitLockerMode=TPMKey OSDBitLockerStartupKeyDrive=C: OSDBitLockerCreateRecoveryPassword=AD OSDBitLockerWaitForEncryption=TRUE`|  

####  <a name="OSDComputerName"></a>OSDComputerName  
 De nieuwe computernaam toewijzen aan de doelcomputer.  

> [!NOTE]
>  Deze eigenschap kan ook worden ingesteld binnen een takenreeks met behulp van een aangepaste **Takenreeksvariabele instellen** takenreeksstap.  

|**Geconfigureerd door de eigenschap**|||**De eigenschap is van toepassing op**||  
|-|-|-|-|-|  
|BootStrap.ini|||LTI|\-|  
|CustomSettings.ini|\-||||  
|MDT-DB|\-||ZTI|\-|  

|**Waarde**|**Beschrijving**|  
|-|-|
|*computer\_naam*|De nieuwe computernaam toewijzen aan de doelcomputer|  

|**Voorbeeld**|  
|-|  
|`[Default] OSDComputerName=%_SMSTSMachineName%`|  

####  <a name="OSDDiskAlign"></a>OSDDiskAlign  
 Deze eigenschap wordt gebruikt om een waarde voor de **uitlijnen** parameter van de **partitie primaire maken** opdracht in de **DiskPart** opdracht. De **uitlijnen** parameter wordt doorgaans gebruikt met hardware RAID Logical Unit Number \(LUN\) matrices om prestaties te verbeteren wanneer de logische eenheden \(lu's\) cilinders niet zijn uitgelijnd. De **uitlijnen** parameter wordt uitgelijnd een primaire partitie die geen cilinder uitgelijnd aan het begin van een schijf en de verschuiving naar de dichtstbijzijnde uitlijning grens afgerond. Voor meer informatie over de **uitlijnen** parameter, Zie [Create partition primaire](http://technet.microsoft.com/library/cc771243\(WS.10\).aspx).  

> [!NOTE]
>  Deze eigenschap kan worden gebruikt in combinatie met de **OSDDiskOffset** eigenschap in te stellen de **offset** parameter voor de **partitie primaire maken** opdracht in de **DiskPart** opdracht. Zie voor meer informatie de [OSDDiskOffset](#OSDDiskOffset) eigenschap.  

|**Geconfigureerd door de eigenschap**|||**De eigenschap is van toepassing op**||  
|-|-|-|-|-|  
|BootStrap.ini|||LTI|\-|  
|CustomSettings.ini|\-||||  
|MDT-DB|\-||ZTI||  

|**Waarde**|**Beschrijving**|  
|-|-|
|*uitlijning\_waarde*|Hiermee geeft u het aantal kilobytes \(KB\) vanaf het begin van de schijf naar de dichtstbijzijnde uitlijning grens.|  

|**Voorbeeld**|  
|-|  
|`[Settings] Priority=Default  [Default] OSDDiskAlign=1024 OSDDiskOffset=2048`|  

####  <a name="OSDDiskIndex"></a>OSDDiskIndex  
 Hiermee geeft u de schijfindex die wordt geconfigureerd.  

|**Geconfigureerd door de eigenschap**|||**De eigenschap is van toepassing op**||  
|-|-|-|-|-|  
|BootStrap.ini|||LTI|\-|  
|CustomSettings.ini|\-||||  
|MDT-DB|\-||ZTI|\-|  

|**Waarde**|**Beschrijving**|  
|-|-|
|*schijf\_index*|Hiermee geeft u de schijfindex die wordt geconfigureerd \(de standaardwaarde is **0**.\)|  

|**Voorbeeld**|  
|-|  
|`[Settings] Priority=Default  [Default] OSDDiskIndex=0`|  

####  <a name="OSDDiskOffset"></a>OSDDiskOffset  
 Deze eigenschap wordt gebruikt om een waarde voor de **offset** parameter van de **partitie primaire maken** opdracht in de **DiskPart** opdracht. Voor meer informatie over de **offset** parameter, Zie [Create partition primaire](http://technet.microsoft.com/library/cc771243\(WS.10\).aspx).  

 Deze eigenschap kan worden gebruikt in combinatie met de **OSDDiskAlign** eigenschap in te stellen de **uitlijnen** parameter voor de **partitie primaire maken** opdracht in de **DiskPart** opdracht. Zie voor meer informatie de [OSDDiskAlign](#OSDDiskAlign) eigenschap.  

|**Geconfigureerd door de eigenschap**|||**De eigenschap is van toepassing op**||  
|-|-|-|-|-|  
|BootStrap.ini|||LTI|\-|  
|CustomSettings.ini|\-||||  
|MDT-DB|\-||ZTI||  

|**Waarde**|**Beschrijving**|  
|-|-|
|*offset\_waarde*|Geeft de verschuiving byte waarop u wilt maken van de partitie. Voor hoofdopstartrecord \(MBR\) schijven, de offset wordt afgerond op de dichtstbijzijnde cilindergrens.|  

|**Voorbeeld**|  
|-|  
|`[Settings] Priority=Default  [Default] OSDDiskAlign=1024 OSDDiskOffset=2048`|  

####  <a name="OSDDiskPartBiosCompatibilityMode"></a>OSDDiskPartBiosCompatibilityMode  
 Deze eigenschap geeft aan of optimalisaties voor cache uitlijning wanneer u de harde schijf voor compatibiliteit met bepaalde typen BIOS.  

|**Geconfigureerd door de eigenschap**|||**De eigenschap is van toepassing op**||  
|-|-|-|-|-|  
|BootStrap.ini|||LTI|\-|  
|CustomSettings.ini|\-||||  
|MDT-DB|\-||ZTI|\-|  

|**Waarde**|**Beschrijving**|  
|-|-|
|**DE WAARDE TRUE**|Schakelt uitlijning optimalisaties in cache wanneer de vaste schijf voor compatibiliteit met bepaalde typen BIOS partitioneren|  
|**DE WAARDE FALSE**|Schakelt in cache uitlijning optimalisaties wanneer u de harde schijf voor compatibiliteit met bepaalde typen BIOS \(dit is de standaardwaarde.\)|  

|**Voorbeeld**|  
|-|  
|`[Settings] Priority=Default  [Default] OSDDiskPartBiosCompatibilityMode=TRUE`|  

####  <a name="OSDImageCreator"></a>OSDImageCreator  
 Hiermee geeft u de naam van de installatieaccount dat wordt gebruikt tijdens de OEM-implementaties.  

> [!NOTE]
>  Deze eigenschap wordt dynamisch ingesteld door de MDT-scripts en is niet geconfigureerd in CustomSettings.ini of de MDT-DB. Deze eigenschap behandelen als alleen-lezen.  

|**Geconfigureerd door de eigenschap**|||**De eigenschap is van toepassing op**||  
|-|-|-|-|-|  
|BootStrap.ini|||LTI|\-|  
|CustomSettings.ini|||||  
|MDT-DB|||ZTI|\-|  

|**Waarde**|**Beschrijving**|  
|-|-|
|*afbeelding\_Maker*|Hiermee geeft u de naam van de installatieaccount dat wordt gebruikt tijdens de OEM-implementaties|  

|**Voorbeeld**|  
|-|  
|Geen|  

####  <a name="OSDImageIndex"></a>OSDImageIndex  
 Hiermee geeft u de index van de afbeelding in het WIM-bestand. Deze eigenschap wordt verwezen tijdens OEM-implementaties.  

> [!NOTE]
>  Deze eigenschap wordt dynamisch ingesteld door de MDT-scripts en is niet geconfigureerd in CustomSettings.ini of de MDT-DB. Deze eigenschap behandelen als alleen-lezen.  

|**Geconfigureerd door de eigenschap**|||**De eigenschap is van toepassing op**||  
|-|-|-|-|-|  
|BootStrap.ini|||LTI|\-|  
|CustomSettings.ini|||||  
|MDT-DB|||ZTI|\-|  

|**Waarde**|**Beschrijving**|  
|-|-|
|*index*|Hiermee geeft u de index van de afbeelding in het WIM-bestand|  

|**Voorbeeld**|  
|-|  
|Geen|  

####  <a name="OSDImagePackageID"></a>OSDImagePackageID  
 Hiermee geeft u de pakket-ID voor de installatiekopie te installeren tijdens de OEM-implementaties.  

> [!NOTE]
>  Deze eigenschap wordt dynamisch ingesteld door de MDT-scripts en is niet geconfigureerd in CustomSettings.ini of de MDT-DB. Deze eigenschap behandelen als alleen-lezen.  

|**Geconfigureerd door de eigenschap**|||**De eigenschap is van toepassing op**||  
|-|-|-|-|-|  
|BootStrap.ini|||LTI|\-|  
|CustomSettings.ini|||||  
|MDT-DB|||ZTI|\-|  

|**Waarde**|**Beschrijving**|  
|-|-|
|*pakket\_ID*|Hiermee geeft u de pakket-ID voor de installatiekopie te installeren tijdens de OEM-implementaties|  

|**Voorbeeld**|  
|-|  
|Geen|  

####  <a name="OSDInstallEditionIndex"></a>OSDInstallEditionIndex  
 Hiermee geeft u de index van de afbeelding in het WIM-bestand. Deze eigenschap wordt verwezen tijdens OEM-implementaties.  

> [!NOTE]
>  Deze eigenschap wordt dynamisch ingesteld door de MDT-scripts en is niet geconfigureerd in CustomSettings.ini of de MDT-DB. Deze eigenschap behandelen als alleen-lezen.  

|**Geconfigureerd door de eigenschap**|||**De eigenschap is van toepassing op**||  
|-|-|-|-|-|  
|BootStrap.ini|||LTI|\-|  
|CustomSettings.ini|||||  
|MDT-DB|||ZTI|\-|  

|**Waarde**|**Beschrijving**|  
|-|-|
|*index*|Hiermee geeft u de index van de afbeelding in het WIM-bestand|  

|**Voorbeeld**|  
|-|  
|Geen|  

####  <a name="OSDInstallType"></a>OSDInstallType  
 Hiermee geeft u de installatie voor OEM-implementaties. De standaardwaarde is **Sysprep**.  

> [!NOTE]
>  Deze eigenschap wordt dynamisch ingesteld door de MDT-scripts en is niet geconfigureerd in CustomSettings.ini of de MDT-DB. Deze eigenschap behandelen als alleen-lezen.  

|**Geconfigureerd door de eigenschap**|||**De eigenschap is van toepassing op**||  
|-|-|-|-|-|  
|BootStrap.ini|||LTI|\-|  
|CustomSettings.ini|||||  
|MDT-DB|||ZTI|\-|  

|**Waarde**|**Beschrijving**|  
|-|-|
|*Installeer\_type*|Hiermee geeft u de installatie voor OEM-implementaties|  

|**Voorbeeld**|  
|-|  
|Geen|  

####  <a name="OSDisk"></a>OSDisk  
 Hiermee geeft u het station dat wordt gebruikt voor het installeren van het besturingssysteem tijdens OEM-implementaties. De standaardwaarde is **C:**.  

> [!NOTE]
>  Deze eigenschap wordt dynamisch ingesteld door de MDT-scripts en is niet geconfigureerd in CustomSettings.ini of de MDT-DB. Deze eigenschap behandelen als alleen-lezen.  

|**Geconfigureerd door de eigenschap**|||**De eigenschap is van toepassing op**||  
|-|-|-|-|-|  
|BootStrap.ini|||LTI|\-|  
|CustomSettings.ini|||||  
|MDT-DB|||ZTI|\-|  

|**Waarde**|**Beschrijving**|  
|-|-|
|*schijf*|Hiermee geeft u het station dat wordt gebruikt voor het installeren van het besturingssysteem tijdens OEM-implementaties|  

|**Voorbeeld**|  
|-|  
|Geen|  

####  <a name="OSDPartitions"></a>OSDPartitions  
 Hiermee geeft u het nummer van de gedefinieerde partities configuraties. Het maximum aantal partities die kunnen worden geconfigureerd is twee. De standaardwaarde is **geen**.  

|**Geconfigureerd door de eigenschap**|||**De eigenschap is van toepassing op**||  
|-|-|-|-|-|  
|BootStrap.ini|||LTI|\-|  
|CustomSettings.ini|\-||||  
|MDT-DB|\-||ZTI||  

|**Waarde**|**Beschrijving**|  
|-|-|
|*partities*|Hiermee geeft u het nummer van de gedefinieerde partities configuraties|  

|**Voorbeeld**|  
|-|  
|`[Settings] Priority=Default  [Default] OSDPartitions=1 OSDPartitions0Bootable=TRUE OSDPartitions0FileSystem=NTFS OSDPartitions0QuickFormat=TRUE OSDPartitions0Size=60 OSDPartitions0SizeUnits=GB OSDPartitions0Type=Primary OSDPartitions0VolumeName=OSDisk OSDPartitions0VolumeLetterVariable=NewDrive1`|  

####  <a name="OSDPartitionsxBootable"></a>OSDPartitionsxBootable  
 De partitie met de opgegeven index moet opstartbare worden ingesteld. De standaard eerste partitie opstartbaar is ingesteld.  

> [!NOTE]
>  De*x* in de eigenschappen van deze naam is een tijdelijke aanduiding voor een op nul gebaseerde matrix met partitie-configuraties.  

|**Geconfigureerd door de eigenschap**|||**De eigenschap is van toepassing op**||  
|-|-|-|-|-|  
|BootStrap.ini|||LTI|-|  
|CustomSettings.ini|-||||  
|MDT-DB|-||ZTI||  

|**Waarde**|**Beschrijving**|  
|-|-|
|**DE WAARDE TRUE**|De partitie moet worden ingesteld op opstartbare.|  
|**DE WAARDE FALSE**|Stel niet in de partitie opstartbaar.|  

|**Voorbeeld**|  
|-|  
|`[Settings] Priority=Default  [Default] OSDPartitions0Bootable=TRUE`|  

####  <a name="OSDPartitionsxFileSystem"></a>OSDPartitionsxFileSystem  
 Het type bestandssysteem voor de partitie met de opgegeven index. Geldige waarden zijn **NTFS** of **FAT32**.  

> [!NOTE]
>  De*x* in de eigenschappen van deze naam is een tijdelijke aanduiding voor een op nul gebaseerde matrix met partitie-configuraties.  

> [!CAUTION]
>  Waarde van deze eigenschap moet in hoofdletters worden opgegeven zodat de implementatiescripts kunnen correct worden gelezen.  

|**Geconfigureerd door de eigenschap**|||**De eigenschap is van toepassing op**||  
|-|-|-|-|-|  
|BootStrap.ini|||LTI|-|  
|CustomSettings.ini|-||||  
|MDT-DB|-||ZTI||  

|**Waarde**|**Beschrijving**|  
|-|-|
|*file_system*|Het type bestandssysteem voor de partitie|  

|**Voorbeeld**|  
|-|  
|`[Settings] Priority=Default  [Default] OSDPartitions0FileSystem=NTFS`|  

####  <a name="OSDPartitionsxQuickFormat"></a>OSDPartitionsxQuickFormat  
 De partitie met de opgegeven index moet snel worden geformatteerd. De standaardwaarde is **TRUE**.  

> [!NOTE]
>  De*x* in de eigenschappen van deze naam is een tijdelijke aanduiding voor een op nul gebaseerde matrix met partitie-configuraties.  

> [!CAUTION]
>  Waarde van deze eigenschap moet in hoofdletters worden opgegeven zodat de implementatiescripts kunnen correct worden gelezen.  

|**Geconfigureerd door de eigenschap**|||**De eigenschap is van toepassing op**||  
|-|-|-|-|-|  
|BootStrap.ini|||LTI|-|  
|CustomSettings.ini|-||||  
|MDT-DB|-||ZTI||  

|**Waarde**|**Beschrijving**|  
|-|-|
|**DE WAARDE TRUE**|De partitie Snelle-indeling.|  
|**DE WAARDE FALSE**|Komen niet snel-indeling de partitie.|  

|**Voorbeeld**|  
|-|  
|`[Settings] Priority=Default  [Default] OSDPartitions0QuickFormat=TRUE`|  

####  <a name="OSDPartitionsxSize"></a>OSDPartitionsxSize  
 De grootte van de partitie met de opgegeven index.  

> [!NOTE]
>  De*x* in de eigenschappen van deze naam is een tijdelijke aanduiding voor een op nul gebaseerde matrix met partitie-configuraties.  

|**Geconfigureerd door de eigenschap**|||**De eigenschap is van toepassing op**||  
|-|-|-|-|-|  
|BootStrap.ini|||LTI|-|  
|CustomSettings.ini|-||||  
|MDT-DB|-||ZTI||  

|**Waarde**|**Beschrijving**|  
|-|-|
|*Grootte*|Partitiegrootte|  

|**Voorbeeld**|  
|-|  
|`[Settings] Priority=Default  [Default] OSDPartitions0Size=60 OSDPartitions0SizeUnits=GB`|  

####  <a name="OSDPartitionsxSizeUnits"></a>OSDPartitionsxSizeUnits  
 De eenheden gebruikt bij het opgeven van de grootte van de partitie. Geldige waarden zijn **MB**, **GB**, of  **%** . De standaardwaarde is **MB**.  

> [!NOTE]
>  De*x* in de eigenschappen van deze naam is een tijdelijke aanduiding voor een op nul gebaseerde matrix met partitie-configuraties.  

|**Geconfigureerd door de eigenschap**|||**De eigenschap is van toepassing op**||  
|-|-|-|-|-|  
|BootStrap.ini|||LTI|-|  
|CustomSettings.ini|-||||  
|MDT-DB|-||ZTI||  

|**Waarde**|**Beschrijving**|  
|-|-|
|*size_units*|De eenheden gebruikt bij het opgeven van de grootte van de partitie|  

|**Voorbeeld**|  
|-|  
|`[Settings] Priority=Default  [Default] OSDPartitions0Size=60 OSDPartitions0SizeUnits=GB`|  

####  <a name="OSDPartitionsxType"></a>OSDPartitionsxType  
 Het type van de partitie worden gemaakt op de opgegeven index.  

> [!NOTE]
>  De*x* in de eigenschappen van deze naam is een tijdelijke aanduiding voor een op nul gebaseerde matrix met partitie-configuraties.  

|**Geconfigureerd door de eigenschap**|||**De eigenschap is van toepassing op**||  
|-|-|-|-|-|  
|BootStrap.ini|||LTI|-|  
|CustomSettings.ini|-||||  
|MDT-DB|-||ZTI||  

|**Waarde**|**Beschrijving**|  
|-|-|
|**Primaire**|Maak een primaire partitie. Dit is de standaardwaarde.|  
|**Logische**|Maak een logische partitie.|  
|**Uitgebreid**|Een uitgebreide partitie maken.|  

|**Voorbeeld**|  
|-|  
|`[Settings] Priority=Default  [Default] OSDPartitions0Type=Primary`|  

####  <a name="OSDPartitionsxVolumeLetterVariable"></a>OSDPartitionsxVolumeLetterVariable  
 De eigenschap die ontvangt de stationsletter die is toegewezen aan de partitie wordt beheerd.  

> [!NOTE]
>  De*x* in de eigenschappen van deze naam is een tijdelijke aanduiding voor een op nul gebaseerde matrix met partitie-configuraties.  

|**Geconfigureerd door de eigenschap**|||**De eigenschap is van toepassing op**||  
|-|-|-|-|-|  
|BootStrap.ini|||LTI|-|  
|CustomSettings.ini|-||||  
|MDT-DB|-||ZTI||  

|**Waarde**|**Beschrijving**|  
|-|-|
|*volume_letter_variable*|De naam van de variabele die wordt toegewezen de stationsletter van de partitie wordt beheerd|  

|**Voorbeeld**|  
|-|  
|`[Settings] Priority=Default  [Default] OSDPartitions0VolumeLetterVariable=NewDrive1`|  

####  <a name="OSDPartitionsxVolumeName"></a>OSDPartitionsxVolumeName  
 De naam van het volume dat wordt toegewezen aan de partitie met de opgegeven index.  

> [!NOTE]
>  De*x* in de eigenschappen van deze naam is een tijdelijke aanduiding voor een op nul gebaseerde matrix met partitie-configuraties.  

|**Geconfigureerd door de eigenschap**|||**De eigenschap is van toepassing op**||  
|-|-|-|-|-|  
|BootStrap.ini|||LTI|-|  
|CustomSettings.ini|-||||  
|MDT-DB|-||ZTI||  

|**Waarde**|**Beschrijving**|  
|-|-|
|*volumenaam*|De naam van het volume dat wordt toegewezen aan de partitie|  

|**Voorbeeld**|  
|-|  
|`[Settings] Priority=Default  [Default] OSDPartitions0VolumeName=OSDisk`|  

####  <a name="OSDPreserveDriveLetter"></a>OSDPreserveDriveLetter  
 Deze eigenschap wordt gebruikt om te bepalen of de **toepassen OS** stap van de takenreeks de stationsaanduiding in het besturingssysteem-installatiekopiebestand (WIM-bestand) wordt geïmplementeerd op de doelcomputer moet worden behouden.  

> [!NOTE]
>  Deze eigenschap mag alleen worden ingesteld in een takenreeksstap, niet in het bestand CustomSettings.ini of in de MDT-database.  

|**Geconfigureerd door de eigenschap**|||**De eigenschap is van toepassing op**||  
|-|-|-|-|-|  
|BootStrap.ini|||LTI||  
|CustomSettings.ini|||||  
|MDT-DB|||ZTI|-|  

|**Waarde**|**Beschrijving**|  
|-|-|
|**DE WAARDE TRUE**|De stationsletters in het besturingssysteem-installatiekopiebestand (WIM-bestand) en het besturingssysteem stations letters nadat de implementatie zijn identiek aan de stationsletters in het WIM-bestand.|  
|**DE WAARDE FALSE**|De stationsletters in het besturingssysteem-installatiekopiebestand (WIM-bestand) worden genegeerd, waardoor de takenreeks voor het onderdrukken van de stationsletters in het WIM-bestand.<br /><br /> Opmerking:<br /><br /> Voor MDT, moet u deze waarde altijd ingeschakeld.|  

|**Voorbeeld**|  
|-|  
|Geen|  

####  <a name="OSDStateStorePath"></a>OSDStateStorePath  
 LTI en ZTI Gebruik deze eigenschap instellen van het pad waar de statusmigratiegegevens worden opgeslagen, kan dit een UNC-pad, een lokaal pad of een relatief pad zijn.  

> [!NOTE]
>  De **OSDStateStorePath** eigenschap heeft voorrang op de [StatePath](#StatePath) of [UserDataLocation](#UserDataLocation) eigenschap wanneer deze eigenschappen ook zijn opgegeven.  

 In een Computer vervangen implementatiescenario in ZTI, de [gebruikersstatus herstellen](#RestoreUserState) takenreeksstap wordt overgeslagen als de **OSDStateStorePath** eigenschap is ingesteld op een geldige landinstelling of een UNC-pad. De tijdelijke oplossing is het instellen van de [USMTLocal](#USMTLocal) eigenschap op TRUE. In dat geval forceert ZTI UserState.wsf voor het herkennen van het pad in de [OSDStateStorePath](#OSDStateStorePath) eigenschap. Dit wordt veroorzaakt door de **Statusopslag opvragen** stap wordt overgeslagen en de vorige waarde in de **OSDStateStorePath** eigenschap te bewaren.  

 Een Computer vervangen implementatiescenario in ZTI, waarbij statusmigratiegegevens en de hele computer wordt een back-up, het bestand Backup.wim is opgeslagen in de map die is opgegeven in de **OSDStateStorePath** eigenschap. Dit wordt mogelijk veroorzaakt door te geven van de onjuiste waarde voor de [ComputerBackupLocation](#ComputerBackupLocation) eigenschap.  

 Bijvoorbeeld, het volgende CustomSettings.ini-bestand wordt het bestand Backup.wim moeten worden opgeslagen in dezelfde map opgegeven in de **OSDStateStorePath** eigenschap:  

```  
USMTLocal=True  
OSDStateStorePath=\\fs1\Share\Replace  

ComputerBackupLocation=NETWORK  
BackupShare=\\fs1\Share\ComputerBackup  
BackupDir=Client01  
```  

|**Geconfigureerd door de eigenschap**|||**De eigenschap is van toepassing op**||  
|-|-|-|-|-|  
|BootStrap.ini|||LTI|-|  
|CustomSettings.ini|-||||  
|MDT-DB|-||ZTI|-|  

|**Waarde**|**Beschrijving**|  
|-|-|
|*Pad*|Het pad waar de gebruikersstatusgegevens migratie worden opgeslagen, wat kan een UNC-pad, een lokaal pad of een relatief pad zijn|  

|**Voorbeeld**|  
|-|  
|`[Settings] Priority=Default  [Default] USMTLocal=True OSDStateStorePath=\\fs1\Share\Replace ComputerBackupLocation=\\fs1\Share\ComputerBackup\Client01`|  

####  <a name="OSDTargetSystemDrive"></a>OSDTargetSystemDrive  
 Hiermee geeft u het station waarop het besturingssysteem wordt geïnstalleerd tijdens de OEM-implementaties.  

> [!NOTE]
>  Deze eigenschap wordt dynamisch ingesteld door de MDT-scripts en is niet geconfigureerd in CustomSettings.ini of de MDT-DB. Deze eigenschap behandelen als alleen-lezen.  

|**Geconfigureerd door de eigenschap**|||**De eigenschap is van toepassing op**||  
|-|-|-|-|-|  
|BootStrap.ini|||LTI|-|  
|CustomSettings.ini|||||  
|MDT-DB|||ZTI||  

|**Waarde**|**Beschrijving**|  
|-|-|
|*systeemstation*|Hiermee geeft u het station waarop het besturingssysteem wordt geïnstalleerd tijdens de OEM-implementaties|  

|**Voorbeeld**|  
|-|  
|Geen|  

####  <a name="OSDTargetSystemRoot"></a>OSDTargetSystemRoot  
 Hiermee geeft u het installatiepad waarop het besturingssysteem wordt geïnstalleerd tijdens de OEM-implementaties.  

> [!NOTE]
>  Deze eigenschap wordt dynamisch ingesteld door de MDT-scripts en is niet geconfigureerd in CustomSettings.ini of de MDT-DB. Deze eigenschap behandelen als alleen-lezen.  

|**Geconfigureerd door de eigenschap**|||**De eigenschap is van toepassing op**||  
|-|-|-|-|-|  
|BootStrap.ini|||LTI|-|  
|CustomSettings.ini|||||  
|MDT-DB|||ZTI||  

|**Waarde**|**Beschrijving**|  
|-|-|
|*systeemhoofdmap*|Hiermee geeft u het installatiepad waarop het besturingssysteem wordt geïnstalleerd tijdens de OEM-implementaties|  

|**Voorbeeld**|  
|-|  
|Geen|  

####  <a name="OSFeatures"></a>OSFeatures  
 Een door komma's gescheiden lijst met onderdeel-id's die wordt geïnstalleerd op de doelcomputer.  

> [!NOTE]
>  Niet alle functies die worden vermeld in het bestand ServerManager.xml zijn compatibel met alle server-besturingssystemen.  

> [!CAUTION]
>  Waarde van deze eigenschap moet in hoofdletters worden opgegeven zodat de implementatiescripts kunnen correct worden gelezen.  

|**Geconfigureerd door de eigenschap**|||**De eigenschap is van toepassing op**||  
|-|-|-|-|-|  
|BootStrap.ini|||LTI|-|  
|CustomSettings.ini|-||||  
|MDT-DB|-||ZTI|-|  

|**Waarde**|**Beschrijving**|  
|-|-|
|*ID1, ID2*|De serverfuncties die moeten worden geïnstalleerd op de doelcomputer. Geldige waarden bevinden zich in de *program_files*\Microsoft Deployment Toolkit\Bin\ServerManager.xml-bestand op de MDT-server.|  

|**Voorbeeld**|  
|-|  
|`[Settings] Priority=Default  [Default] OSFeatures=CMAK,MSMQ-Multicasting,RSAT`|  

####  <a name="OSInstall"></a>OSInstall  
 Hiermee wordt aangegeven of de doelcomputer is geautoriseerd voor het beoogde besturingssysteem geïnstalleerd hebben. Als de **OSInstall** eigenschap niet wordt vermeld, de standaardwaarde is voor implementatie van besturingssystemen op doelcomputers.  

> [!CAUTION]
>  Waarde van deze eigenschap moet in hoofdletters worden opgegeven zodat de implementatiescripts kunnen correct worden gelezen.  

|**Geconfigureerd door de eigenschap**|||**De eigenschap is van toepassing op**||  
|-|-|-|-|-|  
|BootStrap.ini|||LTI|-|  
|CustomSettings.ini|-||||  
|MDT-DB|-||ZTI|-|  

|**Waarde**|**Beschrijving**|  
|-|-|
|**JA**|Implementatie van een besturingssysteem op de doelcomputer is gemachtigd. Dit is de standaardwaarde.|  
|**ER IS GEEN**|Implementatie van een besturingssysteem op de doelcomputer is niet gemachtigd.|  

|**Voorbeeld**|  
|-|  
|`[Settings] Priority=Default  [Default] OSInstall=YES`|  

####  <a name="OSRoles"></a>OSRoles  
 Een door komma's gescheiden lijst van serverfunctie-id's die wordt geïnstalleerd op de doelcomputer.  

> [!NOTE]
>  Niet alle functies zijn compatibel met alle server-besturingssystemen.  

> [!CAUTION]
>  Waarde van deze eigenschap moet in hoofdletters worden opgegeven zodat de implementatiescripts kunnen correct worden gelezen.  

|**Geconfigureerd door de eigenschap**|||**De eigenschap is van toepassing op**||  
|-|-|-|-|-|  
|BootStrap.ini|||LTI|-|  
|CustomSettings.ini|-||||  
|MDT-DB|-||ZTI|-|  

|**Waarde**|**Beschrijving**|  
|-|-|
|*ID1, ID2*|De serverrol die moet worden geïnstalleerd op de doelcomputer.|  

 Zie 'C:\Program Files\Microsoft implementatie Toolkit\Bin\ServerManager.xml' voor geldige id-waarden.  

|**Voorbeeld**|  
|-|  
|`[Settings] Priority=Default  [Default] OSRoles=ADDS`|  

####  <a name="OSRoleServices"></a>OSRoleServices  
 Een door komma's gescheiden lijst met de functieservice server voor id's die worden geïnstalleerd op de doelcomputer.  

> [!NOTE]
>  Niet alle serverfunctie service-id's zijn compatibel met alle server-besturingssystemen.  

|**Geconfigureerd door de eigenschap**|||**De eigenschap is van toepassing op**||  
|-|-|-|-|-|  
|BootStrap.ini|||LTI|-|  
|CustomSettings.ini|-||||  
|MDT-DB|-||ZTI|-|  

|**Waarde**|**Beschrijving**|  
|-|-|
|*ID*|De functieservice server die worden geïnstalleerd op de doelcomputer. De geldige waarde is:<br /><br /> - **VOEGT-Domain-Controller**|  

|**Voorbeeld**|  
|-|  
|`[Settings] Priority=Default  [Default] OSRoleServices=ADDS-Domain-Controller`|  

####  <a name="OSSKU"></a>OSSKU  
 De editie van het besturingssysteem die momenteel worden uitgevoerd. De versie van het besturingssysteem is bepaald met behulp van de **OperatingSystemSKU** eigenschap van de **Win32_OperatingSystem WMI** klasse. Voor een lijst van de versies van de **OperatingSystemSKU** eigenschap berekent, Zie de sectie 'OperatingSystemSKU,' op [Win32_OperatingSystem-klasse](http://msdn.microsoft.com/library/windows/desktop/aa394239\(v=vs.85\).aspx).  

> [!NOTE]
>  Deze eigenschap wordt dynamisch ingesteld door de MDT-scripts en is niet geconfigureerd in CustomSettings.ini of de MDT-DB. Deze eigenschap behandelen als alleen-lezen.  

|**Geconfigureerd door de eigenschap**|||**De eigenschap is van toepassing op**||  
|-|-|-|-|-|  
|BootStrap.ini|||LTI|-|  
|CustomSettings.ini|||||  
|MDT-DB|||ZTI|-|  

|**Waarde**|**Beschrijving**|  
|-|-|
|*editie*|De versie van het besturingssysteem. Bijvoorbeeld 'Bedrijven' voor een Business-editie van een besturingssysteem of 'ENTERPRISE' voor een Enterprise-editie van een besturingssysteem.|  

|**Voorbeeld**|  
|-|  
|Geen|  

####  <a name="OSVersion"></a>OSVersion  
 De versie van het besturingssysteem die momenteel worden uitgevoerd. Deze eigenschap mag alleen worden gebruikt om te detecteren als het actieve besturingssysteem Windows PE. Gebruik de [OSVersionNumber](#OSVersionNumber) eigenschap voor het detecteren van andere besturingssystemen.  

> [!NOTE]
>  Deze eigenschap wordt dynamisch ingesteld door de MDT-scripts en is niet geconfigureerd in CustomSettings.ini of de MDT-DB. Deze eigenschap behandelen als alleen-lezen.  

|**Geconfigureerd door de eigenschap**|||**De eigenschap is van toepassing op**||  
|-|-|-|-|-|  
|BootStrap.ini|||LTI|-|  
|CustomSettings.ini|||||  
|MDT-DB|||ZTI|-|  

|**Waarde**|**Beschrijving**|  
|-|-|
|**WinPE**|Windows PE|  
|**2008 R2**|Windows Server 2008 R2|  
|**Win7Client**|Windows 7|  
|**Andere**|Andere besturingssystemen dan die wordt weergegeven, met inbegrip van Windows 8 en Windows Server 2012|  

|**Voorbeeld**|  
|-|  
|Geen|  

####  <a name="OSVersionNumber"></a>OSVersionNumber  
 Het aantal primaire en secundaire versie van besturingssysteem. Deze eigenschap wordt verwezen tijdens OEM-implementaties.  

> [!NOTE]
>  Deze eigenschap wordt dynamisch ingesteld door de MDT-scripts en is niet geconfigureerd in CustomSettings.ini of de MDT-DB. Deze eigenschap behandelen als alleen-lezen.  

|**Geconfigureerd door de eigenschap**|||**De eigenschap is van toepassing op**||  
|-|-|-|-|-|  
|BootStrap.ini|||LTI|-|  
|CustomSettings.ini|||||  
|MDT-DB|||ZTI|-|  

|**Waarde**|**Beschrijving**|  
|-|-|
|*versie*|Het nummer van de primaire en secundaire versie besturingssysteem|  

|**Voorbeeld**|  
|-|  
|Geen|  

####  <a name="OverrideProductKey"></a>OverrideProductKey  
 De tekenreeks die Multiple Activation Key (MAK) moet worden toegepast na de doel-besturingssysteem wordt geïmplementeerd op de doelcomputer. De waarde die is opgegeven voor deze eigenschap wordt gebruikt door het script ZTILicensing.wsf tijdens de fase voor het herstellen van status voor de MAK van toepassing op het doelbesturingssysteem. Het script wordt ook geconfigureerd voor de installatiekopie van het volume licensing voor het gebruik van MAK-activering in plaats van de Key Management Service (KMS). Het besturingssysteem moet worden geactiveerd bij Microsoft nadat de MAK wordt toegepast. Dit wordt gebruikt wanneer de doelcomputer is geen toegang tot een server waarop KMS wordt uitgevoerd.  

|**Geconfigureerd door de eigenschap**|||**De eigenschap is van toepassing op**||  
|-|-|-|-|-|  
|BootStrap.ini|||LTI|-|  
|CustomSettings.ini|-||||  
|MDT-DB|-||ZTI|-|  

|**Waarde**|**Beschrijving**|  
|-|-|
|*MAK*|De MAK tekenreeks die moet worden opgegeven voor het beoogde besturingssysteem|  

|**Voorbeeld**|  
|-|  
|`[Settings] Priority=Default  [Default] ProductKey=AAAAA-BBBBB-CCCCC-DDDDD-EEEEE-FFFFF OverrideProductKey=AAAAA-BBBBB-CCCCC-DDDDD-EEEEE-FFFFF`|  

####  <a name="PackageGroup"></a>PackageGroup  
 Een lijst met tekstwaarden die koppelt systeempakketten werkt met elkaar (meestal op basis van het type voor het besturingssysteem). Het pakket van een besturingssysteem kan worden gekoppeld aan een of meer groepen van het pakket. De **PackageGroup** eigenschap kunt u de pakketten van het besturingssysteem in een of meer groepen worden geïmplementeerd op een doelcomputer.  

 De tekstwaarden in de lijst mag niet-lege waarde. De **PackageGroup** eigenschapswaarde heeft een numeriek achtervoegsel (bijvoorbeeld **PackageGroup001** of **PackageGroup002**). Nadat deze is gedefinieerd, is de groep van een pakket gekoppeld aan een computer. Een computer kan worden gekoppeld aan meer dan één pakket groep.  

> [!NOTE]
>  Besturingssysteem-pakketten worden gemaakt op het knooppunt OS-pakketten in de implementatie-Workbench.  

> [!NOTE]
>  De **PackageGroup** eigenschap kan worden opgegeven in de notatie *PackageGroup1 = Updates* of *PackageGroup001 = Updates*.  

|**Geconfigureerd door de eigenschap**|||**De eigenschap is van toepassing op**||  
|-|-|-|-|-|  
|BootStrap.ini|||LTI|-|  
|CustomSettings.ini|-||||  
|MDT-DB|||ZTI||  

|**Waarde**|**Beschrijving**|  
|-|-|
|*package_group_name*|Naam van de groep van het pakket moet worden geïmplementeerd op de doelcomputer|  

|**Voorbeeld**|  
|-|  
|`[Settings] Priority=Default  [Default] PackageGroup001=Updates`|  

####  <a name="Packages"></a>Pakketten  
 De lijst met Configuration Manager-pakketten worden geïmplementeerd op de doelcomputer. De **pakketten** eigenschap heeft een numeriek achtervoegsel (bijvoorbeeld Packages001 of Packages002).  

> [!NOTE]
>  De **PackageGroup** eigenschap kan worden opgegeven in de notatie *PackageGroup1 = Updates* of *PackageGroup001 = Updates*.  

|**Geconfigureerd door de eigenschap**|||**De eigenschap is van toepassing op**||  
|-|-|-|-|-|  
|BootStrap.ini|||LTI||  
|CustomSettings.ini|-||||  
|MDT-DB|-||ZTI|-|  

|**Waarde**|**Beschrijving**|  
|-|-|
|*package_id:program_name*|Naam van het pakket worden geïmplementeerd op de doelcomputer|  

|**Voorbeeld**|  
|-|  
|`[Settings] Priority=Default  [Default] Packages001=NYC00010:Install Packages002=NYC00011:Install`|  

####  <a name="PackageSelectionProfile"></a>PackageSelectionProfile  
 De profielnaam die wordt gebruikt tijdens de installatie van pakket.  

|**Geconfigureerd door de eigenschap**|||**De eigenschap is van toepassing op**||  
|-|-|-|-|-|  
|BootStrap.ini|||LTI|-|  
|CustomSettings.ini|-||||  
|MDT-DB|-||ZTI||  

|**Waarde**|**Beschrijving**|  
|-|-|
|*Profielnaam*|Profielnaam die wordt gebruikt tijdens de installatie van pakket|  

|**Voorbeeld**|  
|-|  
|`[Settings] Priority=Default  [Default] PackageSelectionProfile=CoreApplications`|  

####  <a name="Parameters"></a>Parameters  
 De parameters worden doorgegeven aan een databasequery eigenschapswaarden van kolommen in de tabel die is opgegeven retourneert in de **tabel** eigenschap. De tabel bevindt zich in de database die is opgegeven in de **Database** eigenschap op de computer die is opgegeven in de **SQLServer** eigenschap. Het exemplaar van SQL Server op de computer is opgegeven de **exemplaar** eigenschap.  

|**Geconfigureerd door de eigenschap**|||**De eigenschap is van toepassing op**||  
|-|-|-|-|-|  
|BootStrap.ini|-||LTI|-|  
|CustomSettings.ini|-||||  
|MDT-DB|||ZTI|-|  

|**Waarde**|**Beschrijving**|  
|-|-|
|*parameter1, parameter2*|De lijst met parameters die worden doorgegeven aan de databasequery|  

|**Voorbeeld**|  
|-|  
|`[Settings] Priority=Computers, Default  [Default] OSInstall=YES  [Computers] SQLServer=NYC-SQL-01 SQLShare=SQL$ Database=MDTDB Instance=SQLEnterprise2005 Table=Computers Parameters=SerialNumber, AssetTag ParameterCondition=OR`|  

####  <a name="ParameterCondition"></a>ParameterCondition  
 Geeft aan of een Booleaanse waarde en of of bewerking wordt uitgevoerd op de eigenschappen in de **Parameters** eigenschap.  

> [!CAUTION]
>  Waarde van deze eigenschap moet in hoofdletters worden opgegeven zodat de implementatiescripts kunnen correct worden gelezen.  

|**Geconfigureerd door de eigenschap**|||**De eigenschap is van toepassing op**||  
|-|-|-|-|-|  
|BootStrap.ini|-||LTI|-|  
|CustomSettings.ini|-||||  
|MDT-DB|||ZTI|-|  

|**Waarde**|**Beschrijving**|  
|-|-|
|**EN**|Een Boolean-waarde en-bewerking wordt uitgevoerd op de eigenschappen in de **Parameters** eigenschap. Alleen resultaten die overeenkomen met alle eigenschappen die zijn opgegeven in de **Parameters** eigenschap worden geretourneerd. Dit is de standaardwaarde.|  
|**OR**|Een Boolean-waarde of bewerking wordt uitgevoerd op de eigenschappen in de **Parameters** eigenschap. Resultaten die overeenkomen met een eigenschap die is opgegeven in de **Parameters** eigenschap worden geretourneerd.|  

|**Voorbeeld**|  
|-|  
|`[Settings] Priority=Computers, Default  [Default] OSInstall=YES  [Computers] SQLServer=NYC-SQL-01 SQLShare=SQL$ Database=MDTDB Instance=SQLEnterprise2005 Table=Computers Parameters=SerialNumber, AssetTag ParameterCondition=OR`|  

####  <a name="ParentDomainDNSName"></a>ParentDomainDNSName  
 Hiermee geeft u de DNS-domeinnaam van een bestaande directory-domein bij het installeren van een onderliggend domein.  

|**Geconfigureerd door de eigenschap**|||**De eigenschap is van toepassing op**||  
|-|-|-|-|-|  
|BootStrap.ini|||LTI|-|  
|CustomSettings.ini|-||||  
|MDT-DB|-||ZTI|-|  

|**Waarde**|**Beschrijving**|  
|-|-|
|*naam*|Hiermee geeft u de DNS-domeinnaam van een bestaande directory-domein bij het installeren van een onderliggend domein|  

|**Voorbeeld**|  
|-|  
|`[Settings] Priority=Default  [Default] ParentDomainDNSName=WoodGroveBank.com`|  

####  <a name="Password"></a>Wachtwoord  
 Hiermee geeft u het wachtwoord voor de naam van de gebruiker (referenties) te gebruiken voor het promoveren van de lidserver naar een domeincontroller.  

|**Geconfigureerd door de eigenschap**|||**De eigenschap is van toepassing op**||  
|-|-|-|-|-|  
|BootStrap.ini|||LTI|-|  
|CustomSettings.ini|-||||  
|MDT-DB|-||ZTI|-|  

|**Waarde**|**Beschrijving**|  
|-|-|
|*wachtwoord*|Hiermee geeft u het wachtwoord voor de naam van de gebruiker (referenties) te gebruiken voor het promoveren van de lidserver naar een domeincontroller|  

|**Voorbeeld**|  
|-|  
|`[Settings] Priority=Default  [Default] Password=<complex_password>`|  

####  <a name="Phase"></a>Fase  
 De huidige fase van het implementatieproces. De Sequencer taak maakt gebruik van deze fasen om te bepalen welke taken moeten worden voltooid.  

> [!NOTE]
>  Deze eigenschap wordt dynamisch ingesteld door de MDT-scripts en is niet geconfigureerd in CustomSettings.ini of de MDT-DB. Deze eigenschap behandelen als alleen-lezen.  

> [!CAUTION]
>  Waarde van deze eigenschap moet in hoofdletters worden opgegeven zodat de implementatiescripts kunnen correct worden gelezen.  

|**Geconfigureerd door de eigenschap**|||**De eigenschap is van toepassing op**||  
|-|-|-|-|-|  
|BootStrap.ini|||LTI|-|  
|CustomSettings.ini|||||  
|MDT-DB|||ZTI|-|  

|**Waarde**|**Beschrijving**|  
|-|-|
|**VALIDATIE**|Geeft aan dat de doelcomputer kan worden uitgevoerd van de scripts nodig zijn voor het implementatieproces.|  
|**STATECAPTURE**|Hiermee slaat u eventuele statusmigratiegegevens voordat u het doelbesturingssysteem implementeert.|  
|**PREINSTALL**|Alle taken die worden uitgevoerd (zoals het maken van nieuwe partities moeten) voordat het beoogde besturingssysteem wordt geïmplementeerd voltooit.|  
|**INSTALLEREN**|Het beoogde besturingssysteem installeert op de doelcomputer.|  
|**POSTINSTALL**|Alle taken die worden uitgevoerd moeten voordat de migratie van gebruikersstatusgegevens teruggezet voltooit. Deze taken aanpassen het beoogde besturingssysteem voordat u start de computer de eerste doeltijd (zoals het installeren van updates of het toevoegen van stuurprogramma's).|  
|**STATERESTORE**|Hiermee worden de statusmigratiegegevens opgeslagen tijdens de fase voor het vastleggen van status hersteld.|  

|**Voorbeeld**|  
|-|  
|Geen|  

####  <a name="Port"></a>Poort  
 Het nummer van de poort die moet worden gebruikt wanneer verbinding te maken met de SQL Server database-exemplaar dat wordt gebruikt voor het opvragen van de eigenschap van kolommen in de tabel die is opgegeven waarden in de **tabel** eigenschap. De database zich bevindt op de computer die is opgegeven in de **SQLServer** eigenschap. Het exemplaar van SQL Server op de computer is opgegeven de **exemplaar** eigenschap. De poort die wordt gebruikt tijdens de verbinding is opgegeven in de **poort** eigenschap.  

|**Geconfigureerd door de eigenschap**|||**De eigenschap is van toepassing op**||  
|-|-|-|-|-|  
|BootStrap.ini|-||LTI|-|  
|CustomSettings.ini|-||||  
|MDT-DB|||ZTI|-|  

|**Waarde**|**Beschrijving**|  
|-|-|
|*poort*|Het nummer van de poort die wordt gebruikt bij het verbinden met SQL Server|  

|**Voorbeeld**|  
|-|  
|`[Settings] Priority=Computers, Default  [Default] OSInstall=YES  [Computers] SQLServer=NYC-SQL-01 Database=MDTDB Instance=MDT2010 Port=1433 Table=Computers Parameters=SerialNumber, AssetTag ParameterCondition=OR`|  

####  <a name="PowerUsers"></a>PowerUsers:  
 Een lijst met gebruikersaccounts en groepen worden toegevoegd aan de lokale groep Hoofdgebruikers op de doelcomputer. De **PowerUsers:** eigenschap is een lijst met tekstwaarden die elke niet-lege waarde. De **PowerUsers:** eigenschap heeft een numeriek achtervoegsel (bijvoorbeeld **PowerUsers1** of **PowerUsers2**).  

|**Geconfigureerd door de eigenschap**|||**De eigenschap is van toepassing op**||  
|-|-|-|-|-|  
|BootStrap.ini|||LTI|-|  
|CustomSettings.ini|-||||  
|MDT-DB|-||ZTI|-|  

|**Waarde**|**Beschrijving**|  
|-|-|
|*naam*|Naam van de gebruiker of groep worden toegevoegd aan de lokale groep Hoofdgebruikers|  

|**Voorbeeld**|  
|-|  
|`[Settings] Priority=Default  [Default] Administrators001=WOODGROVEBANK\NYC Help Desk Staff PowerUsers001=WOODGROVEBANK\User01 PowerUsers002=WOODGROVEBANK\User02`|  

####  <a name="PrepareWinRE"></a>PrepareWinRE  
 Deze eigenschap geeft aan of het bestand LiteTouchPE.wim, dat Windows RE bevat en eventueel DaRT, wordt toegepast op het systeemstation als de herstelpartitie. Hiermee wordt de doelcomputer voor het gebruik van de installatiekopie LiteTouchPE.wim hersteltaken uitvoeren. DaRT kan optioneel worden opgenomen in de afbeelding waardoor DaRT herstelfuncties beschikbaar is op de doelcomputer.  

|**Geconfigureerd door de eigenschap**|||**De eigenschap is van toepassing op**||  
|-|-|-|-|-|  
|BootStrap.ini|||LTI|-|  
|CustomSettings.ini|-||||  
|MDT-DB|||ZTI||  

|**Waarde**|**Beschrijving**|  
|-|-|
|JA|Het bestand LiteTouchPE.wim, dat Windows RE bevat en eventueel DaRT, wordt toegepast op het systeemstation als de herstelpartitie.|  
|*een andere waarde*|Het bestand LiteTouchPE.wim, dat Windows RE bevat en eventueel DaRT, is niet toegepast op het systeemstation als de herstelpartitie. Dit is de standaardwaarde.|  

|**Voorbeeld**|  
|-|  
|`[Settings] Priority=Default  [Default] PrepareWinRE=YES`|  

####  <a name="Priority"></a>Prioriteit  
 De gereserveerde eigenschap die de volgorde bepaalt voor het vinden van configuratiewaarden. De **prioriteit** gereserveerde eigenschappenlijsten elke sectie moet worden gezocht en de volgorde waarin de secties worden doorzocht. Wanneer een waarde van de eigenschap wordt gevonden, het script ZTIGather.wsf afgesloten zoeken voor de eigenschap en de resterende secties niet zijn gescand voor die eigenschap.  

|**Geconfigureerd door de eigenschap**|||**De eigenschap is van toepassing op**||  
|-|-|-|-|-|  
|BootStrap.ini|-||LTI|-|  
|CustomSettings.ini|-||||  
|MDT-DB|||ZTI|-|  

|**Waarde**|**Beschrijving**|  
|-|-|
|*sectie 1, sectie2 zetten*|De secties moet worden gezocht in de volgorde waarin die ze zijn moet worden gezocht|  

|**Voorbeeld**|  
|-|  
|`[Settings] Priority=MACAddress, Default  [Default] UserDataLocation=NONE CustomProperty=TRUE  [00:0F:20:35:DE:AC] OSDNEWMACHINENAME=HPD530-1  [00:03:FF:FE:FF:FF] OSDNEWMACHINENAME=BVMXP`|  

####  <a name="ProcessorSpeed"></a>ProcessorSpeed  
 De snelheid van de processor geïnstalleerd op de doelcomputer in MHz. De waarde bijvoorbeeld **1995** geeft de processor op de doelcomputer wordt uitgevoerd bij 1,995 MHz of 2 GHz.  

> [!NOTE]
>  Deze eigenschap wordt dynamisch ingesteld door de MDT-scripts en is niet geconfigureerd in CustomSettings.ini of de MDT-DB. Deze eigenschap behandelen als alleen-lezen.  

|**Geconfigureerd door de eigenschap**|||**De eigenschap is van toepassing op**||  
|-|-|-|-|-|  
|BootStrap.ini|||LTI|-|  
|CustomSettings.ini|||||  
|MDT-DB|||ZTI|-|  

|**Waarde**|**Beschrijving**|  
|-|-|
|*processor_speed*|De snelheid van de processor op de doelcomputer in megahertz|  

|**Voorbeeld**|  
|-|  
|Geen|  

####  <a name="Product"></a>Product  
 De productnaam van de doelcomputer. Met een aantal leveranciers computer het merk en model mogelijk niet voldoende unieke identificatie van de kenmerken van een specifieke configuratie (bijvoorbeeld hyperthreaded of niet-hyperthreaded chipsets). De **Product** eigenschap kunt onderscheiden.  

 De indeling voor **Product** is niet gedefinieerd. Gebruik deze eigenschap voor het maken van een subsectie met instellingen die zijn gericht op een specifieke productnaam voor een specifieke computer modelnummer voor een specifieke computer-fabrikant (meestal in combinatie met de **zorg** en **Model** eigenschappen).  

> [!NOTE]
>  Deze eigenschap wordt dynamisch ingesteld door de MDT-scripts en is niet geconfigureerd in CustomSettings.ini of de MDT-DB. Deze eigenschap behandelen als alleen-lezen.  

|**Geconfigureerd door de eigenschap**|||**De eigenschap is van toepassing op**||  
|-|-|-|-|-|  
|BootStrap.ini|||LTI|-|  
|CustomSettings.ini|||||  
|MDT-DB|||ZTI|-|  

|**Waarde**|**Beschrijving**|  
|-|-|
|*product*|De naam van het product van de doelcomputer|  

|**Voorbeeld**|  
|-|  
|Geen|  

####  <a name="ProductKey"></a>ProductKey  
 De tekenreeks die sleutel product moet worden geconfigureerd voor de doelcomputer. Voordat het beoogde besturingssysteem wordt geïmplementeerd, wordt de opgegeven productsleutel automatisch ingevoegd in de juiste locatie in Unattend.xml.  

|**Geconfigureerd door de eigenschap**|||**De eigenschap is van toepassing op**||  
|-|-|-|-|-|  
|BootStrap.ini|||LTI|-|  
|CustomSettings.ini|-||||  
|MDT-DB|-||ZTI|-|  

|**Waarde**|**Beschrijving**|  
|-|-|
|*productcode*|De productcode op om te worden toegewezen aan de doelcomputer|  

|**Voorbeeld**|  
|-|  
|`[Settings] Priority=Default  [Default] ProductKey=AAAAA-BBBBB-CCCCC-DDDDD-EEEEE-FFFFF`|  

####  <a name="Properties"></a>Eigenschappen  
 Een gereserveerde eigenschap die een aangepaste, door de gebruiker gedefinieerde eigenschappen worden gedefinieerd. Deze door de gebruiker gedefinieerde eigenschappen bevinden zich door het script ZTIGather.wsf in het CustomSettings.ini-bestand BootStrap.ini bestand of de MDT-database. Deze eigenschappen zijn toevoegingen voor de vooraf gedefinieerde eigenschappen in MDT.  

|**Geconfigureerd door de eigenschap**|||**De eigenschap is van toepassing op**||  
|-|-|-|-|-|  
|BootStrap.ini|-||LTI|-|  
|CustomSettings.ini|-||||  
|MDT-DB|||ZTI|-|  

|**Waarde**|**Beschrijving**|  
|-|-|
|*custom_property1,*custom_property2|Aangepaste, door de gebruiker gedefinieerde eigenschappen kunnen worden omgezet|  

|**Voorbeeld**|  
|-|  
|`[Settings] Priority=MACAddress, Default Properties=CustomProperty, ApplicationInstall  [Default] OSInstall=YES ScanStateArgs=/v:5 /o /c LoadStateArgs=/v:5 /c /lac UserDataLocation=NONE CustomProperty=TRUE  [00:0F:20:35:DE:AC] OSDNEWMACHINENAME=HPD530-1 ApplicationInstall=Custom  [00:03:FF:FE:FF:FF] OSDNEWMACHINENAME=BVMXP ApplicationInstall=Minimum`|  

####  <a name="ReplicaDomainDNSName"></a>ReplicaDomainDNSName  
 Hiermee geeft u de DNS-domeinnaam van het domein om te repliceren.  

|**Geconfigureerd door de eigenschap**|||**De eigenschap is van toepassing op**||  
|-|-|-|-|-|  
|BootStrap.ini|||LTI|-|  
|CustomSettings.ini|-||||  
|MDT-DB|-||ZTI|-|  

|**Waarde**|**Beschrijving**|  
|-|-|
|*naam*|Hiermee geeft u de DNS-domeinnaam van het domein om te repliceren|  

|**Voorbeeld**|  
|-|  
|`[Settings] Priority=Default  [Default] ReplicaDomainDNSName=WoodGroveBank.com`|  

####  <a name="ReplicaOrNewDomain"></a>ReplicaOrNewDomain  
 Geeft aan of een nieuwe domeincontroller installeren als de eerste domeincontroller in een nieuwe directory-domein of om deze te installeren als een replicadomeincontroller directory service.  

|**Geconfigureerd door de eigenschap**|||**De eigenschap is van toepassing op**||  
|-|-|-|-|-|  
|BootStrap.ini|||LTI|-|  
|CustomSettings.ini|-||||  
|MDT-DB|-||ZTI|-|  

|**Waarde**|**Beschrijving**|  
|-|-|
|**Replica**|De nieuwe domeincontroller installeert als een replicadomeincontroller directory service.|  
|**Domein**|Hiermee installeert de nieuwe domeincontroller als de eerste domeincontroller in een nieuwe directory-domein. Geef de **TreeOrChild** vermelding met een geldige waarde.|  

|**Voorbeeld**|  
|-|  
|`[Settings] Priority=Default  [Default] ReplicaOrNewDomain=Domain`|  

####  <a name="ReplicationSourceDC"></a>ReplicationSourceDC  
 Geeft de volledige DNS-naam van de domeincontroller waarvan u de domeingegevens repliceert.  

|**Geconfigureerd door de eigenschap**|||**De eigenschap is van toepassing op**||  
|-|-|-|-|-|  
|BootStrap.ini|||LTI|-|  
|CustomSettings.ini|-||||  
|MDT-DB|-||ZTI|-|  

|**Waarde**|**Beschrijving**|  
|-|-|
|*naam*|Geeft de volledige DNS-naam van de domeincontroller waarvan u de domeingegevens repliceert|  

|**Voorbeeld**|  
|-|  
|`[Settings] Priority=Default  [Default] ReplicationSourceDC=dc01.WoodGroveBank.com`|  

####  <a name="ResourceDrive"></a>ResourceDrive  
 De stationsletter is toegewezen aan de **ResourceRoot** eigenschap voor de ZTIDrivers.wsf en ZTIPatches.wsf scripts gebruiken om te installeren stuurprogramma's en patches op de doelcomputer.  

> [!NOTE]
>  Deze eigenschap wordt dynamisch ingesteld door de MDT-scripts en is niet geconfigureerd in CustomSettings.ini of de MDT-DB. Deze eigenschap behandelen als alleen-lezen.  

|**Geconfigureerd door de eigenschap**|||**De eigenschap is van toepassing op**||  
|-|-|-|-|-|  
|BootStrap.ini|||LTI|-|  
|CustomSettings.ini|||||  
|MDT-DB|||ZTI|-|  

|**Waarde**|**Beschrijving**|  
|-|-|
|*stationsletter*|De aanwijzing letter voor de logische schijf met de resources|  

|**Voorbeeld**|  
|-|  
|Geen|  

####  <a name="ResourceRoot"></a>ResourceRoot  
 De waarde van deze eigenschap wordt gebruikt door de ZTIDrivers.wsf en ZTIPatches.wsf scripts voor het installeren van stuurprogramma's en patches op de doelcomputer.  

> [!NOTE]
>  Voor LTI, stelt de scripts automatisch de **ResourceRoot** eigenschap dezelfde zijn als de **DeployRoot** eigenschap. Voor ZTI, de waarden in de **DeployRoot** en **ResourceRoot** eigenschappen kunnen worden uniek zijn.  

|**Geconfigureerd door de eigenschap**|||**De eigenschap is van toepassing op**||  
|-|-|-|-|-|  
|BootStrap.ini|-||LTI|-|  
|CustomSettings.ini|-||||  
|MDT-DB|-||ZTI|-|  

|**Waarde**|**Beschrijving**|  
|-|-|
|*UNC_path*|Het UNC-pad naar de gedeelde map met de resources|  

|**Voorbeeld**|  
|-|  
|`[Settings] Priority=Default  [Default] DeployRoot=\\NYC-AM-FIL-01\Distribution$ ResourceDrive=R: ResourceRoot=\\NYC-AM-FIL-01\Resource$ UserDataLocation=NONE`|  

####  <a name="Role"></a>Rol  
 Het doel van een computer op basis van de taken die worden uitgevoerd door de gebruiker op de doelcomputer. De **rol** eigenschap een lijst met tekstwaarden die elke niet-lege waarde. De **rol** eigenschapswaarde heeft een numeriek achtervoegsel (bijvoorbeeld **Role1** of **Role2**). Als gedefinieerd, wordt een rol is gekoppeld aan een computer. Een computer kan meer dan één rol uitvoeren.  

 Normaal gesproken de waarde voor de **rol** eigenschap is ingesteld door een databasequery uitvoeren in de MDT-database. De implementatie-Workbench kan helpen bij het maken van de rol- en eigenschap instellingen die zijn gekoppeld aan de rol en vervolgens de implementatie-Workbench CustomSettings.ini om uit te voeren van de databasequery voor kunt configureren de **rol** eigenschap en de eigenschapsinstellingen die zijn gekoppeld aan de rol.  

|**Geconfigureerd door de eigenschap**|||**De eigenschap is van toepassing op**||  
|-|-|-|-|-|  
|BootStrap.ini|-||LTI|-|  
|CustomSettings.ini|-||||  
|MDT-DB|-||ZTI|-|  

|**Waarde**|**Beschrijving**|  
|-|-|
|*Rol*|De rollen worden toegewezen aan een afzonderlijke computer of een groep computers|  

|**Voorbeeld 1**|  
|-|  
|`[Settings] Priority=RoleSettings, Default  [Default] SkipCapture=NO UserDataLocation=AUTO DeployRoot=\\W2K3-SP1\Distribution$ OSInstall=YES ScanStateArgs=/v:15 /o /c LoadStateArgs=/v:7 /c  [RoleSettings] SQLServer=w2k3-sp1 Instance=MDT2010 Database=MDTDB Netlib=DBNMPNTW SQLShare=SQL_Share Table=RoleSettings Parameters=Role`|  

|**Voorbeeld 2**|  
|-|  
|`[Settings] Priority=RoleSettings, Default  [Default] SkipCapture=NO UserDataLocation=AUTO DeployRoot=\\W2K3-SP1\Distribution$ OSInstall=YES Role1=Teller Role2=Woodgrove User  [RoleSettings] SQLServer=w2k3-sp1 Instance=MDT2010 Database=MDTDB Netlib=DBNMPNTW SQLShare=SQL_Share Table=RoleSettings Parameters=Role`|  

####  <a name="SafeModeAdminPassword"></a>SafeModeAdminPassword  
 Hiermee wordt het wachtwoord voor het administrator-account bij het starten van de computer in veilige modus of een variant van de veilige modus bevindt, zoals Directory Services Restore mode.  

|**Geconfigureerd door de eigenschap**|||**De eigenschap is van toepassing op**||  
|-|-|-|-|-|  
|BootStrap.ini|||LTI|-|  
|CustomSettings.ini|-||||  
|MDT-DB|-||ZTI|-|  

|**Waarde**|**Beschrijving**|  
|-|-|
|*wachtwoord*|Hiermee wordt het wachtwoord voor het administrator-account bij het starten van de computer in veilige modus of een variant van de veilige modus bevindt, zoals Directory Services Restore mode|  

|**Voorbeeld**|  
|-|  
|`[Settings] Priority=Default  [Default] SafeModeAdminPassword=<complex_password>`|  

####  <a name="ScanStateArgs"></a>ScanStateArgs  
 Argumenten doorgegeven aan de **USMT Scanstate** proces. De scripts Scanstate.exe aanroepen en voeg vervolgens de juiste logboekregistratie, voortgang en status store-parameters. Als deze waarde niet in het bestand met instellingen opgenomen is, wordt de gebruiker staat back-upproces wordt overgeslagen.  

> [!NOTE]
>  Gebruik de **USMTMigFiles** eigenschap om op te geven van de XML-bestanden kunnen worden gebruikt door Scanstate.exe in plaats van de parameter /I in de **ScanStateArgs** eigenschap. Dit voorkomt dat het script ZTIUserState.wsf mogelijk dupliceren van dezelfde lijst met XML-bestanden.  

> [!NOTE]
>  Voeg niet een van de volgende opdrachtregelargumenten bij het configureren van deze eigenschap: **/hardlink**, **/nocompress**, **/ versleutelen**,   **/Key**, of **/KeyFile**. De MDT-scripts wordt deze opdrachtregelargumenten toevoegen, indien van toepassing voor de huidige implementatie.  

|**Geconfigureerd door de eigenschap**|||**De eigenschap is van toepassing op**||  
|-|-|-|-|-|  
|BootStrap.ini|||LTI|-|  
|CustomSettings.ini|-||||  
|MDT-DB|-||ZTI||  

|**Waarde**|**Beschrijving**|  
|-|-|
|*argumenten*|De argumenten voor de opdrachtregel doorgegeven aan Scanstate.exe.<br /><br /> De standaardargumenten dat is opgegeven door de Implementatieworkbench zijn als volgt:<br /><br /> - **/v**. Hiermee schakelt u uitgebreide uitvoer in het logboek Scanstate. De standaardwaarde is **0**. Geef een getal van 0 tot en met 15. De waarde **5** schakelt uitgebreide en statusuitvoer.<br /><br /> - **/o**. Overschrijft bestaande gegevens in het archief. Als niet wordt opgegeven, mislukt de Scanstate als het archief al gegevens bevat. Deze optie kan niet meer dan één keer worden opgegeven in een opdrachtpromptvenster.<br /><br /> -                             **/c**. Als u opgeeft, moet Scanstate wordt nog uitgevoerd zelfs als er niet-fatale fouten. Zonder de **/c** optie Scanstate verlaat bij de eerste fout.<br /><br /> Zie de Help van USMT-bestanden voor meer informatie over deze en andere argumenten.|  

|**Voorbeeld**|  
|-|  
|`[Settings] Priority=Default  [Default] ScanStateArgs=/v:5 /o /c LoadStateArgs=/v:5 /c /lac DeployRoot=\\NYC-AM-FIL-01\Distribution$ ResourceRoot=\\NYC-AM-FIL-01\Resource$ UDShare=\\NYC-AM-FIL-01\MigData$ UDDir=%OSDComputerName%`|  

####  <a name="SerialNumber"></a>Serienummer  
 Het serienummer van de doelcomputer. De indeling voor serienummers is niet gedefinieerd. Gebruik deze eigenschap te maken van een subsectie met instellingen die zijn gericht op een specifieke computer.  

> [!NOTE]
>  Deze eigenschap wordt dynamisch ingesteld door de MDT-scripts en is niet geconfigureerd in CustomSettings.ini of de MDT-DB. Deze eigenschap behandelen als alleen-lezen.  

|**Geconfigureerd door de eigenschap**|||**De eigenschap is van toepassing op**||  
|-|-|-|-|-|  
|BootStrap.ini|||LTI|-|  
|CustomSettings.ini|||||  
|MDT-DB|||ZTI|-|  

|**Waarde**|**Beschrijving**|  
|-|-|
|*serieel-getal*|De indeling van het serienummer is niet gedefinieerd en wordt bepaald door de standaard serienummer van de fabrikant van elke computer.|  

|**Voorbeeld**|  
|-|  
|Geen|  

####  <a name="SiteName"></a>Sitenaam  
 Geeft de naam van een bestaande site waarin u de nieuwe domeincontroller kunt plaatsen.  

|**Geconfigureerd door de eigenschap**|||**De eigenschap is van toepassing op**||  
|-|-|-|-|-|  
|BootStrap.ini|||LTI|-|  
|CustomSettings.ini|-||||  
|MDT-DB|-||ZTI||  

|**Waarde**|**Beschrijving**|  
|-|-|
|*naam*|Hiermee geeft u de naam van een bestaande site waarin u de nieuwe domeincontroller kunt plaatsen|  

|**Voorbeeld**|  
|-|  
|`[Settings] Priority=Default  [Default] SiteName=FirstSite`|  

####  <a name="SkipAdminAccounts"></a>SkipAdminAccounts  
 Hiermee wordt aangegeven of de **lokale beheerders** wizardpagina wordt overgeslagen.  

> [!NOTE]
>  Deze standaardwaarde voor deze eigenschap is **Ja**, wat inhoudt dat het **lokale beheerders** wizardpagina wordt overgeslagen als de standaard. Als u wilt deze wizardpagina weergeven, moet u de waarde van deze eigenschap in op specifiek ingesteld **Nee** in CustomSettings.ini of in de MDT-database.  

 Voor andere eigenschappen die moeten worden geconfigureerd wanneer deze eigenschap is ingesteld op **Ja**, Zie [bieden eigenschappen voor implementatie wizardpagina's overgeslagen](#ProvidingPropertiesforSkippedDeploymentWizardPages).  

> [!CAUTION]
>  Waarde van deze eigenschap moet in hoofdletters worden opgegeven zodat de implementatiescripts kunnen correct worden gelezen.  

|**Geconfigureerd door de eigenschap**|||**De eigenschap is van toepassing op**||  
|-|-|-|-|-|  
|BootStrap.ini|||LTI|-|  
|CustomSettings.ini|-||||  
|MDT-DB|-||ZTI||  

|**Waarde**|**Beschrijving**|  
|-|-|
|**JA**|Pagina van de wizard niet wordt weergegeven en de informatie op deze pagina is niet verzameld. Dit is de standaardwaarde.|  
|**ER IS GEEN**|Pagina van de wizard wordt weergegeven en de gegevens op deze pagina worden verzameld.|  

|**Voorbeeld**|  
|-|  
|`[Settings] Priority=Default  [Default] SkipWizard=NO SkipCapture=NO SkipAdminAccounts=NO SkipAdminPassword=NO SkipApplications=NO SkipComputerBackup=NO SkipDomainMembership=NO SkipUserData=NO SkipPackageDisplay=NO SkipLocaleSelection=NO SkipProductKey=YES`|  

####  <a name="SkipAdminPassword"></a>SkipAdminPassword  
 Hiermee wordt aangegeven of de **beheerderswachtwoord** wizardpagina wordt overgeslagen.  

 Voor andere eigenschappen die moeten worden geconfigureerd wanneer deze eigenschap is ingesteld op **Ja**, Zie [bieden eigenschappen voor implementatie wizardpagina's overgeslagen](#ProvidingPropertiesforSkippedDeploymentWizardPages).  

> [!CAUTION]
>  Waarde van deze eigenschap moet in hoofdletters worden opgegeven zodat de implementatiescripts kunnen correct worden gelezen.  

|**Geconfigureerd door de eigenschap**|||**De eigenschap is van toepassing op**||  
|-|-|-|-|-|  
|BootStrap.ini|||LTI|-|  
|CustomSettings.ini|-||||  
|MDT-DB|-||ZTI||  

|**Waarde**|**Beschrijving**|  
|-|-|
|**JA**|Pagina van de wizard niet wordt weergegeven en de informatie op deze pagina is niet verzameld.|  
|**ER IS GEEN**|Pagina van de wizard wordt weergegeven en de gegevens op deze pagina worden verzameld. Dit is de standaardwaarde.|  

|**Voorbeeld**|  
|-|  
|`[Settings] Priority=Default  [Default] SkipWizard=NO SkipCapture=NO SkipAdminPassword=YES SkipApplications=NO SkipComputerBackup=NO SkipDomainMembership=NO SkipUserData=NO SkipPackageDisplay=NO SkipLocaleSelection=NO SkipProductKey=YES`|  

####  <a name="SkipApplications"></a>SkipApplications  
 Hiermee wordt aangegeven of de **Selecteer een of meer toepassingen installeren** wizardpagina wordt overgeslagen.  

 Voor andere eigenschappen die moeten worden geconfigureerd wanneer deze eigenschap is ingesteld op **Ja**, Zie [bieden eigenschappen voor implementatie wizardpagina's overgeslagen](#ProvidingPropertiesforSkippedDeploymentWizardPages).  

> [!CAUTION]
>  Waarde van deze eigenschap moet in hoofdletters worden opgegeven zodat de implementatiescripts kunnen correct worden gelezen.  

|**Geconfigureerd door de eigenschap**|||**De eigenschap is van toepassing op**||  
|-|-|-|-|-|  
|BootStrap.ini|||LTI|-|  
|CustomSettings.ini|-||||  
|MDT-DB|-||ZTI||  

|**Waarde**|**Beschrijving**|  
|-|-|
|**JA**|Pagina van de wizard niet wordt weergegeven en de informatie op deze pagina is niet verzameld.|  
|**ER IS GEEN**|Pagina van de wizard wordt weergegeven en de gegevens op deze pagina worden verzameld. Dit is de standaardwaarde.|  

|**Voorbeeld**|  
|-|  
|`[Settings] Priority=Default  [Default] SkipWizard=NO SkipCapture=NO SkipAdminPassword=NO SkipApplications=YES SkipComputerBackup=NO SkipDomainMembership=NO SkipUserData=NO SkipPackageDisplay=NO SkipLocaleSelection=NO SkipProductKey=YES`|  

####  <a name="SkipBDDWelcome"></a>SkipBDDWelcome  
 Hiermee wordt aangegeven of de **Welkom bij de implementatie van Windows** wizardpagina wordt overgeslagen.  

 Voor andere eigenschappen die moeten worden geconfigureerd wanneer deze eigenschap is ingesteld op **Ja**, Zie [bieden eigenschappen voor implementatie wizardpagina's overgeslagen](#ProvidingPropertiesforSkippedDeploymentWizardPages).  

> [!NOTE]
>  Voor deze eigenschap in op de functie moet juist deze worden geconfigureerd in zowel CustomSettings.ini en BootStrap.ini. BootStrap.ini worden verwerkt voordat een implementatieshare (met daarin CustomSettings.ini) is geselecteerd.  

> [!CAUTION]
>  Waarde van deze eigenschap moet in hoofdletters worden opgegeven zodat de implementatiescripts kunnen correct worden gelezen.  

|**Geconfigureerd door de eigenschap**|||**De eigenschap is van toepassing op**||  
|-|-|-|-|-|  
|BootStrap.ini|-||LTI|-|  
|CustomSettings.ini|-||||  
|MDT-DB|-||ZTI||  

|**Waarde**|**Beschrijving**|  
|-|-|
|**JA**|Pagina van de wizard niet wordt weergegeven en de informatie op deze pagina is niet verzameld.|  
|**ER IS GEEN**|Pagina van de wizard wordt weergegeven en de gegevens op deze pagina worden verzameld. Dit is de standaardwaarde.|  

|**Voorbeeld**|  
|-|  
|`[Settings] Priority=Default  [Default] SkipWizard=NO SkipCapture=NO SkipAdminPassword=YES SkipApplications=NO SkipBDDWelcome=YES SkipComputerBackup=NO SkipDomainMembership=NO SkipUserData=NO SkipPackageDisplay=NO SkipLocaleSelection=NO SkipProductKey=YES`|  

####  <a name="SkipBitLocker"></a>SkipBitLocker  
 Hiermee wordt aangegeven of de **opgeven van de configuratie van BitLocker** wizardpagina wordt overgeslagen.  

 Voor andere eigenschappen die moeten worden geconfigureerd wanneer deze eigenschap is ingesteld op **Ja**, Zie [bieden eigenschappen voor implementatie wizardpagina's overgeslagen](#ProvidingPropertiesforSkippedDeploymentWizardPages).  

> [!CAUTION]
>  Waarde van deze eigenschap moet in hoofdletters worden opgegeven zodat de implementatiescripts kunnen correct worden gelezen.  

|**Geconfigureerd door de eigenschap**|||**De eigenschap is van toepassing op**||  
|-|-|-|-|-|  
|BootStrap.ini|||LTI|-|  
|CustomSettings.ini|-||||  
|MDT-DB|-||ZTI||  

|**Waarde**|**Beschrijving**|  
|-|-|
|**JA**|Pagina van de wizard niet wordt weergegeven en de informatie op deze pagina is niet verzameld.|  
|**ER IS GEEN**|Pagina van de wizard wordt weergegeven en de gegevens op deze pagina worden verzameld. Dit is de standaardwaarde.|  

|**Voorbeeld**|  
|-|  
|`[Settings] Priority=Default  [Default] SkipWizard=NO SkipCapture=NO SkipApplications=NO SkipBDDWelcome=YES SkipBitLocker=YES SkipComputerBackup=NO SkipDomainMembership=NO SkipUserData=NO SkipPackageDisplay=NO SkipLocaleSelection=NO`|  

####  <a name="SkipBuild"></a>SkipBuild  
 Hiermee wordt aangegeven of de **Selecteer een takenreeks uit te voeren op deze computer** wizardpagina wordt overgeslagen.  

 Voor andere eigenschappen die moeten worden geconfigureerd wanneer deze eigenschap is ingesteld op **Ja**, Zie [bieden eigenschappen voor implementatie wizardpagina's overgeslagen](#ProvidingPropertiesforSkippedDeploymentWizardPages).  

 Waarde van deze eigenschap moet in hoofdletters worden opgegeven zodat de implementatiescripts kunnen correct worden gelezen.  

|**Geconfigureerd door de eigenschap**|||**De eigenschap is van toepassing op**||  
|-|-|-|-|-|  
|BootStrap.ini|||LTI|-|  
|CustomSettings.ini|-||||  
|MDT-DB|-||ZTI||  

|**Waarde**|**Beschrijving**|  
|-|-|
|**JA**|Pagina van de wizard niet wordt weergegeven en de informatie op deze pagina is niet verzameld.|  
|**ER IS GEEN**|Pagina van de wizard wordt weergegeven en de gegevens op deze pagina worden verzameld. Dit is de standaardwaarde.|  

|**Voorbeeld**|  
|-|  
|`[Settings] Priority=Default  [Default] SkipWizard=NO SkipCapture=NO SkipAdminPassword=YES SkipApplications=NO SkipBDDWelcome=YES SkipBuild=YES SkipComputerBackup=NO SkipComputerName=NO SkipDomainMembership=NO SkipFinalSummary=NO SkipSummary=NO SkipUserData=NO SkipPackageDisplay=NO SkipLocaleSelection=NO`|  

####  <a name="SkipCapture"></a>SkipCapture  
 Hiermee wordt aangegeven of de **opgeven of een installatiekopie vastleggen** wizardpagina wordt overgeslagen.  

 Voor andere eigenschappen die moeten worden geconfigureerd wanneer deze eigenschap is ingesteld op **Ja**, Zie [bieden eigenschappen voor implementatie wizardpagina's overgeslagen](#ProvidingPropertiesforSkippedDeploymentWizardPages).  

> [!CAUTION]
>  Waarde van deze eigenschap moet in hoofdletters worden opgegeven zodat de implementatiescripts kunnen correct worden gelezen.  

|**Geconfigureerd door de eigenschap**|||**De eigenschap is van toepassing op**||  
|-|-|-|-|-|  
|BootStrap.ini|||LTI|-|  
|CustomSettings.ini|-||||  
|MDT-DB|-||ZTI||  

|**Waarde**|**Beschrijving**|  
|-|-|
|**JA**|De pagina van de wizard niet wordt weergegeven en de informatie op deze pagina is niet verzameld.|  
|**ER IS GEEN**|De pagina van de wizard wordt weergegeven en de gegevens op deze pagina worden verzameld. Dit is de standaardwaarde.|  

|**Voorbeeld**|  
|-|  
|`[Settings] Priority=Default  [Default] SkipWizard=NO SkipCapture=YES SkipApplications=NO SkipComputerBackup=NO SkipDomainMembership=NO SkipUserData=NO SkipPackageDisplay=NO SkipLocaleSelection=NO`|  

####  <a name="SkipComputerBackup"></a>SkipComputerBackup  
 Hiermee wordt aangegeven of de **opgeven waar een volledige computernaam back-up opslaan** wizardpagina wordt overgeslagen.  

 Voor andere eigenschappen die moeten worden geconfigureerd wanneer deze eigenschap is ingesteld op **Ja**, Zie [bieden eigenschappen voor implementatie wizardpagina's overgeslagen](#ProvidingPropertiesforSkippedDeploymentWizardPages).  

> [!CAUTION]
>  Waarde van deze eigenschap moet in hoofdletters worden opgegeven zodat de implementatiescripts kunnen correct worden gelezen.  

|**Geconfigureerd door de eigenschap**|||**De eigenschap is van toepassing op**||  
|-|-|-|-|-|  
|BootStrap.ini|||LTI|-|  
|CustomSettings.ini|-||||  
|MDT-DB|-||ZTI||  

|**Waarde**|**Beschrijving**|  
|-|-|
|**JA**|De pagina van de wizard niet wordt weergegeven en de informatie op deze pagina is niet verzameld.|  
|**ER IS GEEN**|De pagina van de wizard wordt weergegeven en de gegevens op deze pagina worden verzameld. Dit is de standaardwaarde.|  

|**Voorbeeld**|  
|-|  
|`[Settings] Priority=Default  [Default] SkipWizard=NO SkipCapture=NO SkipAdminPassword=NO SkipApplications=NO SkipComputerBackup=YES SkipDomainMembership=NO SkipUserData=NO SkipPackageDisplay=NO SkipLocaleSelection=NO`|  

####  <a name="SkipComputerName"></a>SkipComputerName  
 Hiermee wordt aangegeven of de **configureren van de computernaam** wizardpagina wordt overgeslagen.  

 Voor andere eigenschappen die moeten worden geconfigureerd wanneer deze eigenschap is ingesteld op **Ja**, Zie [bieden eigenschappen voor implementatie wizardpagina's overgeslagen](#ProvidingPropertiesforSkippedDeploymentWizardPages).  

> [!CAUTION]
>  Waarde van deze eigenschap moet in hoofdletters worden opgegeven zodat de implementatiescripts kunnen correct worden gelezen.  

|**Geconfigureerd door de eigenschap**|||**De eigenschap is van toepassing op**||  
|-|-|-|-|-|  
|BootStrap.ini|||LTI|\-|  
|CustomSettings.ini|\-||||  
|MDT-DB|\-||ZTI||  

|**Waarde**|**Beschrijving**|  
|-|-|
|**JA**|Pagina van de wizard niet wordt weergegeven en de informatie op deze pagina is niet verzameld.|  
|**ER IS GEEN**|Pagina van de wizard wordt weergegeven en de gegevens op deze pagina worden verzameld. Dit is de standaardwaarde.|  

|**Voorbeeld**|  
|-|  
|`[Settings] Priority=Default  [Default] SkipWizard=NO SkipCapture=NO SkipAdminPassword=NO SkipApplications=NO SkipComputerBackup=NO SkipComputerName=YES SkipDomainMembership=NO SkipUserData=NO SkipPackageDisplay=NO SkipLocaleSelection=NO`|  

####  <a name="SkipDomainMembership"></a>SkipDomainMembership  
 Hiermee wordt aangegeven of de **de computer toevoegen aan een domein of werkgroep** wizardpagina wordt overgeslagen.  

 Voor andere eigenschappen die moeten worden geconfigureerd wanneer deze eigenschap is ingesteld op **Ja**, Zie [bieden eigenschappen voor implementatie wizardpagina's overgeslagen](#ProvidingPropertiesforSkippedDeploymentWizardPages).  

> [!CAUTION]
>  Waarde van deze eigenschap moet in hoofdletters worden opgegeven zodat de implementatiescripts kunnen correct worden gelezen.  

|**Geconfigureerd door de eigenschap**|||**De eigenschap is van toepassing op**||  
|-|-|-|-|-|  
|BootStrap.ini|||LTI|\-|  
|CustomSettings.ini|\-||||  
|MDT-DB|\-||ZTI||  

|**Waarde**|**Beschrijving**|  
|-|-|
|**JA**|De pagina van de wizard niet wordt weergegeven en de informatie op deze pagina is niet verzameld.|  
|**ER IS GEEN**|De pagina van de wizard wordt weergegeven en de gegevens op deze pagina worden verzameld. Dit is de standaardwaarde.|  

|**Voorbeeld**|  
|-|  
|`[Settings] Priority=Default  [Default] SkipWizard=NO SkipCapture=NO SkipAdminPassword=NO SkipApplications=NO SkipComputerBackup=NO SkipUserData=NO SkipPackageDisplay=NO SkipLocaleSelection=NO SkipDomainMembership=NO`|  

####  <a name="SkipFinalSummary"></a>SkipFinalSummary  
 Hiermee wordt aangegeven of de **besturingssysteem-implementatie is voltooid** wizardpagina wordt overgeslagen.  

 Voor andere eigenschappen die moeten worden geconfigureerd wanneer deze eigenschap is ingesteld op **Ja**, Zie [bieden eigenschappen voor implementatie wizardpagina's overgeslagen](#ProvidingPropertiesforSkippedDeploymentWizardPages).  

> [!NOTE]
>  Waarde van deze eigenschap moet in hoofdletters worden opgegeven zodat de implementatiescripts kunnen correct worden gelezen.  

|**Geconfigureerd door de eigenschap**|||**De eigenschap is van toepassing op**||  
|-|-|-|-|-|  
|BootStrap.ini|||LTI|\-|  
|CustomSettings.ini|\-||||  
|MDT-DB|\-||ZTI||  

|**Waarde**|**Beschrijving**|  
|-|-|
|**JA**|De pagina van de wizard niet wordt weergegeven en de informatie op deze pagina is niet verzameld.|  
|**ER IS GEEN**|De pagina van de wizard wordt weergegeven en de gegevens op deze pagina worden verzameld. Dit is de standaardwaarde.|  

|**Voorbeeld**|  
|-|  
|`[Settings] Priority=Default  [Default] SkipWizard=NO SkipCapture=NO SkipApplications=NO SkipBDDWelcome=YES SkipComputerBackup=NO SkipComputerName=NO SkipDomainMembership=NO SkipFinalSummary=NO SkipUserData=NO SkipPackageDisplay=NO SkipLocaleSelection=NO SkipProductKey=YES`|  

####  <a name="SkipGroupSubFolders"></a>SkipGroupSubFolders  
 Standaard bij het opgeven van mappen moeten worden opgenomen bij het invoegen van stuurprogramma's, patches \(pakketten\), enzovoort, waarden zijn opgegeven als:  

```  
DriverGroup001=TopFolder\SecondFolder  
PackageGroup001=TopFolder\SecondFolder  
```  

 Dit doet, standaard ook omvatten alle sub\-mappen zich onder de 'SecondFolder." Als **SkipGroupSubFolders** is ingesteld op **Ja** in CustomSettings.ini, dit gedrag wijzigen zodat de submappen worden uitgesloten en alleen de inhoud van 'SecondFolder' wordt toegevoegd.  

 Als u wilt uitsluiten submappen wanneer overeenkomende tegen groepen zoals DriverGroup001 en PackageGroup001, stel **SkipGroupSubFolders** naar **Ja**.  

> [!CAUTION]
>  Waarde van deze eigenschap moet in hoofdletters worden opgegeven zodat de implementatiescripts kunnen correct worden gelezen.  

|**Geconfigureerd door de eigenschap**|||**De eigenschap is van toepassing op**||  
|-|-|-|-|-|  
|BootStrap.ini|||LTI|\-|  
|CustomSettings.ini|\-||||  
|MDT-DB|\-||ZTI||  

|**Waarde**|**Beschrijving**|  
|-|-|
|**JA**|Inclusief submappen niet vergelijken op basis van groepen.|  
|**ER IS GEEN**|Inclusief submappen tijdens het vergelijken op basis van groepen. Dit is de standaardinstelling.|  

|**Voorbeeld**|  
|-|  
|`[Settings] Priority=Default  [Default] SkipGroupSubFolders=NO`|  

####  <a name="SkipLocaleSelection"></a>SkipLocaleSelection  
 Hiermee wordt aangegeven of de **landinstelling selectie** wizardpagina wordt overgeslagen.  

 Voor andere eigenschappen die moeten worden geconfigureerd wanneer deze eigenschap is ingesteld op **Ja**, Zie [bieden eigenschappen voor implementatie wizardpagina's overgeslagen](#ProvidingPropertiesforSkippedDeploymentWizardPages).  

> [!CAUTION]
>  Waarde van deze eigenschap moet in hoofdletters worden opgegeven zodat de implementatiescripts kunnen correct worden gelezen.  

|**Geconfigureerd door de eigenschap**|||**De eigenschap is van toepassing op**||  
|-|-|-|-|-|  
|BootStrap.ini|||LTI|\-|  
|CustomSettings.ini|\-||||  
|MDT-DB|\-||ZTI||  

|**Waarde**|**Beschrijving**|  
|-|-|
|**JA**|De pagina van de wizard niet wordt weergegeven en de informatie op deze pagina is niet verzameld.|  
|**ER IS GEEN**|De pagina van de wizard wordt weergegeven en de gegevens op deze pagina worden verzameld. Dit is de standaardwaarde.|  

|**Voorbeeld**|  
|-|  
|`[Settings] Priority=Default  [Default] SkipWizard=NO SkipCapture=NO SkipApplications=NO SkipComputerBackup=NO SkipDomainMembership=NO SkipUserData=NO SkipPackageDisplay=NO SkipLocaleSelection=NO`|  

####  <a name="SkipPackageDisplay"></a>SkipPackageDisplay  
 Hiermee wordt aangegeven of de **pakketten** wizardpagina wordt overgeslagen.  

 Voor andere eigenschappen die moeten worden geconfigureerd wanneer deze eigenschap is ingesteld op **Ja**, Zie [bieden eigenschappen voor implementatie wizardpagina's overgeslagen](#ProvidingPropertiesforSkippedDeploymentWizardPages).  

> [!CAUTION]
>  Waarde van deze eigenschap moet in hoofdletters worden opgegeven zodat de implementatiescripts kunnen correct worden gelezen.  

|**Geconfigureerd door de eigenschap**|||**De eigenschap is van toepassing op**||  
|-|-|-|-|-|  
|BootStrap.ini|||LTI|\-|  
|CustomSettings.ini|\-||||  
|MDT-DB|\-||ZTI||  

|**Waarde**|**Beschrijving**|  
|-|-|
|**JA**|De pagina van de wizard niet wordt weergegeven en de informatie op deze pagina is niet verzameld.|  
|**ER IS GEEN**|De pagina van de wizard wordt weergegeven en de gegevens op deze pagina worden verzameld. Dit is de standaardwaarde.|  

|**Voorbeeld**|  
|-|  
|`[Settings] Priority=Default  [Default] SkipWizard=NO SkipCapture=NO SkipApplications=NO SkipComputerBackup=NO SkipDomainMembership=NO SkipUserData=NO SkipPackageDisplay=YES SkipLocaleSelection=NO`|  

####  <a name="SkipProductKey"></a>SkipProductKey  
 Hiermee wordt aangegeven of de **Geef de productcode nodig voor het installeren van dit besturingssysteem** wizardpagina wordt overgeslagen.  

 Voor andere eigenschappen die moeten worden geconfigureerd wanneer deze eigenschap is ingesteld op **Ja**, Zie [bieden eigenschappen voor implementatie wizardpagina's overgeslagen](#ProvidingPropertiesforSkippedDeploymentWizardPages).  

> [!CAUTION]
>  Waarde van deze eigenschap moet in hoofdletters worden opgegeven zodat de implementatiescripts kunnen correct worden gelezen.  

|**Geconfigureerd door de eigenschap**|||**De eigenschap is van toepassing op**||  
|-|-|-|-|-|  
|BootStrap.ini|||LTI|\-|  
|CustomSettings.ini|\-||||  
|MDT-DB|\-||ZTI||  

|**Waarde**|**Beschrijving**|  
|-|-|
|**JA**|De pagina van de wizard niet wordt weergegeven en de informatie op deze pagina is niet verzameld.|  
|**ER IS GEEN**|De pagina van de wizard wordt weergegeven en de gegevens op deze pagina worden verzameld. Dit is de standaardwaarde.|  

|**Voorbeeld**|  
|-|  
|`[Settings] Priority=Default  [Default] SkipWizard=NO SkipCapture=NO SkipAdminPassword=YES SkipApplications=NO SkipComputerBackup=NO SkipDomainMembership=NO SkipUserData=NO SkipPackageDisplay=NO SkipLocaleSelection=NO SkipProductKey=YES`|  

####  <a name="SkipRearm"></a>SkipRearm  
 Deze eigenschap wordt gebruikt om te configureren of MDT rearms de Microsoft Office 2010 25\-evaluatieperiode dag. Als Microsoft Office 2010 is vastgelegd in een aangepaste installatiekopie, ziet de gebruiker activering melding dialoogvensters onmiddellijk nadat de installatiekopie wordt geïmplementeerd in plaats van 25\-dagen na de implementatie.  

 Standaard MDT de Microsoft Office 2010 25 rearms\-dag activering respijtperiode periode wanneer het script LTISysprep.wsf wordt uitgevoerd. U kunt instellen dat de waarde van deze eigenschap in op **Ja** zodat MDT slaat de rearming van de Microsoft Office 2010 25\-evaluatieperiode dag.  

> [!CAUTION]
>  Waarde van deze eigenschap moet in hoofdletters worden opgegeven zodat de implementatiescripts kunnen correct worden gelezen.  

|**Geconfigureerd door de eigenschap**|||**De eigenschap is van toepassing op**||  
|-|-|-|-|-|  
|BootStrap.ini|||LTI|\-|  
|CustomSettings.ini|\-||||  
|MDT-DB|||ZTI||  

|**Waarde**|**Beschrijving**|  
|-|-|
|**JA**|MDT biedt niet de Microsoft Office 2010 25 rearm\-evaluatieperiode dag.|  
|**ER IS GEEN**|MDT rearms de Microsoft Office 2010 25\-evaluatieperiode dag. Dit is de standaardwaarde.|  

|**Voorbeeld**|  
|-|  
|`[Settings] Priority=Default  [Default] OSInstall=Y SkipCapture=YES SkipAdminPassword=NO SkipProductKey=YES SkipRearm=YES DoCapture=YES`|  

####  <a name="SkipRoles"></a>SkipRoles  
 Hiermee wordt aangegeven of de **functies en onderdelen** wizardpagina wordt overgeslagen.  

 Voor andere eigenschappen die moeten worden geconfigureerd wanneer deze eigenschap is ingesteld op **Ja**, Zie [bieden eigenschappen voor implementatie wizardpagina's overgeslagen](#ProvidingPropertiesforSkippedDeploymentWizardPages).  

> [!CAUTION]
>  Waarde van deze eigenschap moet in hoofdletters worden opgegeven zodat de implementatiescripts kunnen correct worden gelezen.  

|**Geconfigureerd door de eigenschap**|||**De eigenschap is van toepassing op**||  
|-|-|-|-|-|  
|BootStrap.ini|||LTI|\-|  
|CustomSettings.ini|\-||||  
|MDT-DB|\-||ZTI||  

|**Waarde**|**Beschrijving**|  
|-|-|
|**JA**|De pagina van de wizard niet wordt weergegeven en de informatie op deze pagina is niet verzameld.|  
|**ER IS GEEN**|De pagina van de wizard wordt weergegeven en de gegevens op deze pagina worden verzameld. Dit is de standaardwaarde.|  

|**Voorbeeld**|  
|-|  
|`[Settings] Priority=Default  [Default] SkipWizard=NO SkipCapture=NO SkipAdminPassword=YES SkipApplications=NO SkipBDDWelcome=YES SkipTaskSequence=Yes SkipComputerBackup=NO SkipComputerName=NO SkipDomainMembership=NO SkipFinalSummary=NO SkipRoles=YES SkipSummary=NO SkipUserData=NO SkipPackageDisplay=NO SkipLocaleSelection=NO`|  

####  <a name="SkipSummary"></a>SkipSummary  
 Hiermee wordt aangegeven of de **gereed om te beginnen** wizardpagina wordt overgeslagen.  

 Voor andere eigenschappen die moeten worden geconfigureerd wanneer deze eigenschap is ingesteld op **Ja**, Zie [bieden eigenschappen voor implementatie wizardpagina's overgeslagen](#ProvidingPropertiesforSkippedDeploymentWizardPages).  

> [!CAUTION]
>  Waarde van deze eigenschap moet in hoofdletters worden opgegeven zodat de implementatiescripts kunnen correct worden gelezen.  

|**Geconfigureerd door de eigenschap**|||**De eigenschap is van toepassing op**||  
|-|-|-|-|-|  
|BootStrap.ini|||LTI|\-|  
|CustomSettings.ini|\-||||  
|MDT-DB|\-||ZTI||  

|**Waarde**|**Beschrijving**|  
|-|-|
|**JA**|De pagina van de wizard niet wordt weergegeven en de informatie op deze pagina is niet verzameld.|  
|**ER IS GEEN**|De pagina van de wizard wordt weergegeven en de gegevens op deze pagina worden verzameld. Dit is de standaardwaarde.|  

|**Voorbeeld**|  
|-|  
|`[Settings] Priority=Default  [Default] SkipWizard=NO SkipCapture=NO SkipAdminPassword=YES SkipApplications=NO SkipBDDWelcome=YES SkipTaskSequence=Yes SkipComputerBackup=NO SkipComputerName=NO SkipDomainMembership=NO SkipFinalSummary=NO SkipSummary=NO SkipUserData=NO SkipPackageDisplay=NO SkipLocaleSelection=NO`|  

####  <a name="SkipTaskSequence"></a>SkipTaskSequence  
 Hiermee wordt aangegeven of de **Selecteer een takenreeks uit te voeren op deze computer** wizardpagina wordt overgeslagen.  

 Voor andere eigenschappen die moeten worden geconfigureerd wanneer deze eigenschap is ingesteld op **Ja**, Zie [bieden eigenschappen voor implementatie wizardpagina's overgeslagen](#ProvidingPropertiesforSkippedDeploymentWizardPages).  

> [!NOTE]
>  Geef de **SkipBuild** eigenschap bij het configureren van de Wizard implementatie om over te slaan met behulp van de implementatie-Workbench de **Selecteer een takenreeks uit te voeren op deze computer** wizardpagina.  

> [!CAUTION]
>  Waarde van deze eigenschap moet in hoofdletters worden opgegeven zodat de implementatiescripts kunnen correct worden gelezen.  

|**Geconfigureerd door de eigenschap**|||**De eigenschap is van toepassing op**||  
|-|-|-|-|-|  
|BootStrap.ini|||LTI|\-|  
|CustomSettings.ini|\-||||  
|MDT-DB|||ZTI||  

|**Waarde**|**Beschrijving**|  
|-|-|
|**JA**|De pagina van de wizard niet wordt weergegeven en de informatie op deze pagina is niet verzameld.|  
|**ER IS GEEN**|De pagina van de wizard wordt weergegeven en de gegevens op deze pagina worden verzameld. Dit is de standaardwaarde.|  

|**Voorbeeld**|  
|-|  
|`[Settings] Priority=Default  [Default] SkipWizard=NO SkipCapture=NO SkipApplications=NO SkipBDDWelcome=YES SkipTaskSequence=NO SkipComputerBackup=NO SkipComputerName=NO SkipDomainMembership=NO SkipFinalSummary=NO SkipSummary=NO SkipUserData=NO SkipPackageDisplay=NO SkipLocaleSelection=NO`|  

####  <a name="SkipTimeZone"></a>SkipTimeZone  
 Hiermee wordt aangegeven of de **Stel de tijdzone** wizardpagina wordt overgeslagen.  

 Voor andere eigenschappen die moeten worden geconfigureerd wanneer deze eigenschap is ingesteld op **Ja**, Zie [bieden eigenschappen voor implementatie wizardpagina's overgeslagen](#ProvidingPropertiesforSkippedDeploymentWizardPages).  

> [!CAUTION]
>  Waarde van deze eigenschap moet in hoofdletters worden opgegeven zodat de implementatiescripts kunnen correct worden gelezen.  

|**Geconfigureerd door de eigenschap**|||**De eigenschap is van toepassing op**||  
|-|-|-|-|-|  
|BootStrap.ini|||LTI|\-|  
|CustomSettings.ini|\-||||  
|MDT-DB|\-||ZTI||  

|**Waarde**|**Beschrijving**|  
|-|-|
|**JA**|De pagina van de wizard niet wordt weergegeven en de informatie op deze pagina is niet verzameld.|  
|**ER IS GEEN**|De pagina van de wizard wordt weergegeven en de gegevens op deze pagina worden verzameld. Dit is de standaardwaarde.|  

|**Voorbeeld**|  
|-|  
|`[Settings] Priority=Default  [Default] SkipWizard=NO SkipCapture=NO SkipAdminPassword=YES SkipApplications=NO SkipBDDWelcome=YES SkipTaskSequence=YES SkipComputerBackup=NO SkipComputerName=NO SkipDomainMembership=NO SkipFinalSummary=NO SkipSummary=NO SkipTimeZone=NO SkipUserData=NO SkipPackageDisplay=NO SkipLocaleSelection=NO`|  

####  <a name="SkipUserData"></a>SkipUserData  
 Hiermee wordt aangegeven of de **geven of om gebruikersgegevens te herstellen** en **opgeven waar u uw gegevens en instellingen opslaan** wizardpagina wordt overgeslagen.  

 Voor andere eigenschappen die moeten worden geconfigureerd wanneer deze eigenschap is ingesteld op **Ja**, Zie [bieden eigenschappen voor implementatie wizardpagina's overgeslagen](#ProvidingPropertiesforSkippedDeploymentWizardPages).  

> [!CAUTION]
>  Waarde van deze eigenschap moet in hoofdletters worden opgegeven zodat de implementatiescripts kunnen correct worden gelezen.  

|**Geconfigureerd door de eigenschap**|||**De eigenschap is van toepassing op**||  
|-|-|-|-|-|  
|BootStrap.ini|||LTI|\-|  
|CustomSettings.ini|\-||||  
|MDT-DB|\-||ZTI||  

|**Waarde**|**Beschrijving**|  
|-|-|
|**JA**|De pagina van de wizard niet wordt weergegeven en de informatie op deze pagina is niet verzameld.|  
|**ER IS GEEN**|De pagina van de wizard wordt weergegeven en de gegevens op deze pagina worden verzameld. Dit is de standaardwaarde.|  

|**Voorbeeld**|  
|-|  
|`[Settings] Priority=Default  [Default] SkipWizard=NO SkipCapture=NO SkipAdminPassword=YES SkipApplications=NO SkipComputerBackup=NO SkipDomainMembership=NO SkipUserData=NO SkipPackageDisplay=NO SkipLocaleSelection=NO SkipProductKey=YES`|  

####  <a name="SkipWizard"></a>SkipWizard  
 Hiermee wordt aangegeven of de gehele **implementatiewizard** wordt overgeslagen.  

 Voor andere eigenschappen die moeten worden geconfigureerd wanneer deze eigenschap is ingesteld op **Ja**, Zie [bieden eigenschappen voor implementatie wizardpagina's overgeslagen](#ProvidingPropertiesforSkippedDeploymentWizardPages).  

> [!CAUTION]
>  Waarde van deze eigenschap moet in hoofdletters worden opgegeven zodat de implementatiescripts kunnen correct worden gelezen.  

|**Geconfigureerd door de eigenschap**|||**De eigenschap is van toepassing op**||  
|-|-|-|-|-|  
|BootStrap.ini|||LTI|\-|  
|CustomSettings.ini|\-||||  
|MDT-DB|\-||ZTI||  

|**Waarde**|**Beschrijving**|  
|-|-|
|**JA**|De volledige wizard niet wordt weergegeven en geen van de informatie op de wizardpagina's worden verzameld.|  
|**ER IS GEEN**|De wizard wordt weergegeven en de gegevens op de ingeschakelde wizardpagina's worden verzameld. Dit is de standaardwaarde.|  

|**Voorbeeld**|  
|-|  
|`[Settings] Priority=Default  [Default] SkipWizard=YES`|  

####  <a name="SLShare"></a>SLShare  
 De gedeelde netwerkmap waarin de implementatielogboeken van de aan het einde van het implementatieproces zijn opgeslagen.  

|**Geconfigureerd door de eigenschap**|||**De eigenschap is van toepassing op**||  
|-|-|-|-|-|  
|BootStrap.ini|||LTI|\-|  
|CustomSettings.ini|\-||||  
|MDT-DB|\-||ZTI|\-|  

|**Waarde**|**Beschrijving**|  
|-|-|
|*shared_folder*|De naam van de gedeelde netwerkmap in welke script logboeken worden opgeslagen|  

|**Voorbeeld**|  
|-|  
|`[Settings] Priority=Default  [Default] DeployRoot=\\NYC-AM-FIL-01\Distribution$ ResourceRoot=\\NYC-AM-FIL-01\Resource$ UDShare=\\NYC-AM-FIL-01\MigData$ UDDir=%OSDComputerName% SLShare=\\NYC-AM-FIL-01\Logs$ UDProfiles=Administrator, User-01, ExtranetUser UserDataLocation=NONE SkipCapture=NO SkipAdminPassword=YES SkipProductKey=YES`|  

####  <a name="SLShareDynamicLogging"></a>SLShareDynamicLogging  
 De gedeelde netwerkmap in welke alle MDT logboeken tijdens de implementatie moeten worden geschreven. Dit wordt gebruikt voor geavanceerde realtime foutopsporing alleen.  

|**Geconfigureerd door de eigenschap**|||**De eigenschap is van toepassing op**||  
|-|-|-|-|-|  
|BootStrap.ini|||LTI|-|  
|CustomSettings.ini|-||||  
|MDT-DB|-||ZTI|-|  

|**Waarde**|**Beschrijving**|  
|-|-|
|*shared_folder*|De naam van de gedeelde netwerkmap in welke script logboeken worden opgeslagen|  

|**Voorbeeld**|  
|-|  
|`[Settings] Priority=Default  [Default] DeployRoot=\\NYC-AM-FIL-01\Distribution$ ResourceRoot=\\NYC-AM-FIL-01\Resource$ UDShare=\\NYC-AM-FIL-01\MigData$ UDDir=%OSDComputerName% SLShare=\\NYC-AM-FIL-01\Logs$ SLShareDynamicLogging=\\NYC-AM-FIL-01\Logs$ UDProfiles=Administrator, User-01, ExtranetUser UserDataLocation=NONE SkipCapture=NO SkipAdminPassword=YES SkipProductKey=YES`|  

####  <a name="SMSTSAssignUserMode"></a>SMSTSAssignUserMode  
 Hiermee geeft u op of de affiniteit van gebruikersapparaat (UDA) moet worden ingeschakeld en of de goedkeuring is vereist. Deze eigenschap werkt alleen met de functie UDA in Configuration Manager.  

|**Geconfigureerd door de eigenschap**|||**De eigenschap is van toepassing op**||  
|-|-|-|-|-|  
|BootStrap.ini|||LTI||  
|CustomSettings.ini|-||||  
|MDT-DB|-||ZTI|-|  

|**Waarde**|**Beschrijving**|  
|-|-|
|**Auto**|De affiniteit tussen een gebruiker en het doelapparaat tot stand is gebracht en goedkeuring wordt automatisch uitgevoerd.|  
|**In behandeling**|De affiniteit tussen een gebruiker en het doelapparaat tot stand is gebracht en goedkeuring wordt ingediend voor goedkeuring van de Configuration Manager-beheerder.|  
|**Uitschakelen**|De affiniteit tussen een gebruiker en het doelapparaat niet tot stand is gebracht.|  

|**Voorbeeld**|  
|-|  
|`[Settings] Priority=Default  [Default] SMSTSAssignUserMode=Auto SMSTSUdaUsers=Fabrikam\Ken, Fabrikam\Pilar`|  

####  <a name="SMSTSRunCommandLineUserName"></a>Basis van SMSTSRunCommandLineUserName  
 Hiermee geeft u de gebruikersnaam van de in *domein\gebruikersnaam* indeling die moet worden gebruikt met een **opdrachtregel uitvoeren** stap die is geconfigureerd om te worden uitgevoerd als een gebruiker.  

|**Geconfigureerd door de eigenschap**|||**De eigenschap is van toepassing op**||  
|-|-|-|-|-|  
|BootStrap.ini|||LTI|-|  
|CustomSettings.ini|-||||  
|MDT-DB|-||ZTI|-|  

|**Waarde**|**Beschrijving**|  
|-|-|
|*gebruikersnaam*|Hiermee geeft u de gebruikersnaam van de in die moet worden gebruikt met een **opdrachtregel uitvoeren** stap|  

|**Voorbeeld**|  
|-|  
|`[Settings] Priority=Default  [Default] SMSTSRunCommandLineUserName=Fabrikam\Ken SMSTSRunCommandLineUserPassword=<complex_password>`|  

####  <a name="SMSTSRunCommandLineUserPassword"></a>SMSTSRunCommandLineUserPassword  
 Hiermee geeft u het wachtwoord dat moet worden gebruikt met een **opdrachtregel uitvoeren** stap die is geconfigureerd om te worden uitgevoerd als een gebruiker.  

|**Geconfigureerd door de eigenschap**|||**De eigenschap is van toepassing op**||  
|-|-|-|-|-|  
|BootStrap.ini|||LTI|-|  
|CustomSettings.ini|-||||  
|MDT-DB|-||ZTI|-|  

|**Waarde**|**Beschrijving**|  
|-|-|
|*user_password*|Hiermee geeft u het wachtwoord dat moet worden gebruikt met een **opdrachtregel uitvoeren** stap|  

|**Voorbeeld**|  
|-|  
|`[Settings] Priority=Default  [Default] SMSTSRunCommandLineUserName=Fabrikam\Ken SMSTSRunCommandLineUserPassword=<complex_password>`|  

####  <a name="SMSTSUdaUsers"></a>SMSTSUdaUsers  
 Hiermee geeft u de gebruikers die de affiniteit met een specifiek apparaat met de functie UDA, die alleen beschikbaar in Configuration Manager is worden toegewezen.  

|**Geconfigureerd door de eigenschap**|||**De eigenschap is van toepassing op**||  
|-|-|-|-|-|  
|BootStrap.ini|||LTI||  
|CustomSettings.ini|-||||  
|MDT-DB|-||ZTI|-|  

|**Waarde**|**Beschrijving**|  
|-|-|
|*Gebruiker1, gebruiker2 bevat...*|De door komma's gescheiden lijst met gebruikers in *domein\gebruikersnaam* indeling die wordt toegewezen affiniteit met het doelapparaat.<br /><br /> Opmerking:<br /><br /> U kunt alleen gebruiken de NetBIOS-domeinnaam in deze waarde, zoals *Fabrikam\Ken*. U kunt de volledig gekwalificeerde domeinnaam (fabrikam.com\Ken) of de UPN-notatie gebruiken (ken@fabrikam.com).|  

|**Voorbeeld**|  
|-|  
|`[Settings] Priority=Default  [Default] SMSTSAssignUserMode=Auto SMSTSUdaUsers=Fabrikam\Ken, Fabrikam\Pilar`|  

####  <a name="SQLServer"></a>SQL Server  
 De identiteit van de computer met SQL Server die wordt uitgevoerd voor een databasequery eigenschapswaarden van kolommen in de tabel die is opgegeven retourneert in de **tabel** eigenschap. De query is gebaseerd op de parameters die zijn opgegeven de **Parameters** en **ParameterCondition** eigenschappen. Het exemplaar van SQL Server op de computer is opgegeven de **exemplaar** eigenschap.  

|**Geconfigureerd door de eigenschap**|||**De eigenschap is van toepassing op**||  
|-|-|-|-|-|  
|BootStrap.ini|-||LTI|-|  
|CustomSettings.ini|-||||  
|MDT-DB|||ZTI|-|  

|**Waarde**|**Beschrijving**|  
|-|-|
|*SQL_server*|De naam van de computer met SQL Server|  

|**Voorbeeld**|  
|-|  
|`[Settings] Priority=Computers, Default  [Default] OSInstall=YES ScanStateArgs=/v:5 /o /c LoadStateArgs=/v:5 /c /lac  [Computers] SQLServer=NYC-SQL-01 SQLShare=SQL$ Database=MDTDB Instance=SQLEnterprise2005 Table=Computers Parameters=SerialNumber, AssetTag ParameterCondition=OR`|  

####  <a name="SQLShare"></a>SQLShare  
 De naam van een gedeelde map op de computer met SQL Server (opgegeven door de **SQLServer** eigenschap). De referenties gebruikt voor verificatie worden geleverd door de **UserDomain**, **UserID**, en **UserPassword** eigenschappen (voor LTI en ZTI) of door de Configuration Manager Geavanceerde Client accountreferenties (alleen ZTI).  

> [!NOTE]
>  Deze eigenschap moet worden opgegeven om uit te voeren van geïntegreerde Windows-verificatie. Dit is de aanbevolen verificatiemethode in plaats van de **DBID** en **DBPwd** eigenschappen (die de SQL Server-verificatiemethode wordt ondersteund).  

|**Geconfigureerd door de eigenschap**|||**De eigenschap is van toepassing op**||  
|-|-|-|-|-|  
|BootStrap.ini|-||LTI|-|  
|CustomSettings.ini|-||||  
|MDT-DB|||ZTI|-|  

|**Waarde**|**Beschrijving**|  
|-|-|
|*shared_folder*|De naam van een gedeelde map op de computer met SQL Server|  

|**Voorbeeld**|  
|-|  
|`[Settings] Priority=Computers, Default Properties=MyCustomProperty  [Default] OSInstall=YES ScanStateArgs=/v:5 /o /c LoadStateArgs=/v:5 /c /lac  [Computers] SQLServer=NYC-SQL-01 SQLShare=SQL$ Database=MDTDB Instance=MDT2010 Table=Computers Parameters=SerialNumber, AssetTag ParameterCondition=OR`|  

####  <a name="StatePath"></a>StatePath  
 Deze eigenschap wordt gebruikt voor het pad waar de statusmigratiegegevens worden opgeslagen, kan dit een UNC-pad, een lokaal pad of een relatief pad zijn ingesteld. De [OSDStateStorePath](#OSDStateStorePath) eigenschap heeft voorrang op de **StatePath** of [UserDataLocation](#UserDataLocation) eigenschap wanneer deze eigenschappen ook zijn opgegeven.  

> [!NOTE]
>  Deze eigenschap wordt aangeboden voor achterwaartse compatibiliteit met eerdere versies van MDT. Gebruik de [OSDStateStorePath](#UserDataLocation) eigenschap in plaats daarvan.  

|**Geconfigureerd door de eigenschap**|||**De eigenschap is van toepassing op**||  
|-|-|-|-|-|  
|BootStrap.ini|||LTI|-|  
|CustomSettings.ini|-||||  
|MDT-DB|||ZTI||  

|**Waarde**|**Beschrijving**|  
|-|-|
|*Pad*|Het pad waar de gebruikersstatusgegevens migratie worden opgeslagen, wat kan een UNC-pad, een lokaal pad of een relatief pad zijn|  

|**Voorbeeld**|  
|-|  
|`[Settings] Priority=Default  [Default] SitePath=\\fs1\Share\Replace ComputerBackupLocation=\\fs1\Share\ComputerBackup\Client01`|  

####  <a name="StoredProcedure"></a>Opgeslagen procedure  
 De naam van de opgeslagen procedure gebruikt bij het uitvoeren van een databasequery eigenschapswaarden van kolommen in de tabel of weergave retourneert. De opgeslagen procedure bevindt zich in de database die is opgegeven in de **Database** eigenschap. De computer met SQL Server is opgegeven in de **SQLServer** eigenschap. Het exemplaar van SQL Server op de computer is opgegeven de **exemplaar** eigenschap. De naam van de opgeslagen procedure is opgegeven in de **StoredProcedure** eigenschap.  

 Voor meer informatie over het gebruik van een opgeslagen procedure voor een SQL Server-database, Zie de sectie 'Implementeren van toepassingen gebaseerd op eerdere toepassingsversies', in de MDT document *Microsoft Deployment Toolkit voorbeelden Guide*.  

|**Geconfigureerd door de eigenschap**|||**De eigenschap is van toepassing op**||  
|-|-|-|-|-|  
|BootStrap.ini|-||LTI|-|  
|CustomSettings.ini|-||||  
|MDT-DB|||ZTI|-|  

|**Waarde**|**Beschrijving**|  
|-|-|
|*stored_procedure*|De naam van de opgeslagen procedure gebruikt voor het zoeken van de SQL Server-database|  

|**Voorbeeld**|  
|-|  
|`[Settings] Priority=DynamicPackages, Default  [Default] OSInstall=YES  [DynamicPackages] SQLDefault=DB_DynamicPackages  [DB_DynamicPackages] SQLServer=SERVER1 Database=MDTDB StoredProcedure=RetrievePackages Parameters=MacAddress SQLShare=Logs Instance=MDT2013 Port=1433 Netlib=DBNMPNTW`|  

####  <a name="SupportsHyperVRole"></a>SupportsHyperVRole  
 Hiermee geeft u op of de processorbronnen op de doelcomputer de serverfunctie Hyper-V in Windows Server kunnen ondersteunen. Deze eigenschap True is als de waarde voor de volgende eigenschappen is ingesteld op **TRUE**:  

-   **SupportsNX**  

-   **SupportsVT**  

-   **Supports64Bit**  

 Elk van de vorige eigenschappen is ingesteld met behulp van informatie van de **CPUID** interface. Voor meer informatie over virtuele machines die is verzameld en informatie die wordt geretourneerd vanaf de **CPUID** interface, Zie de volgende eigenschappen:  

-   **IsHypervisorRunning**  

-   **IsVM**  

-   **SupportsNX**  

-   **SupportsVT**  

-   **Supports64Bit**  

-   **VMPlatform**  

> [!NOTE]
>  Deze eigenschap wordt dynamisch ingesteld door de MDT-scripts en is niet geconfigureerd in CustomSettings.ini of de MDT-DB. Deze eigenschap behandelen als alleen-lezen.  

|**Geconfigureerd door de eigenschap**|||**De eigenschap is van toepassing op**||  
|-|-|-|-|-|  
|BootStrap.ini|||LTI|-|  
|CustomSettings.ini|||||  
|MDT-DB|||ZTI|-|  

|**Waarde**|**Beschrijving**|  
|-|-|
|**DE WAARDE TRUE**|De processorresources van de doelcomputer kunnen de serverfunctie Hyper-V in Windows Server ondersteunen.|  
|**DE WAARDE FALSE**|De processorresources van de doelcomputer kunnen de Hyper-V-serverfunctie niet in Windows Server ondersteunen.|  

|**Voorbeeld**|  
|-|  
|Geen|  

####  <a name="SupportsNX"></a>SupportsNX  
 Hiermee geeft u op of de processorbronnen op de doelcomputer de technologie Nee uitvoeren (NX) ondersteunen. De technologie NX wordt gebruikt in de processors scheiden gebieden van geheugen voor gebruik door de opslag van processor-instructies (code) of voor de opslag van gegevens. Deze eigenschap is ingesteld met behulp van informatie uit de **CPUID** interface.  

 Voor meer informatie over virtuele machines die is verzameld en informatie die wordt geretourneerd vanaf de **CPUID** interface, Zie de volgende eigenschappen:  

-   **IsHypervisorRunning**  

-   **IsVM**  

-   **SupportsHyperVRole**  

-   **SupportsVT**  

-   **Supports64Bit**  

-   **VMPlatform**  

> [!NOTE]
>  Deze eigenschap wordt dynamisch ingesteld door de MDT-scripts en is niet geconfigureerd in CustomSettings.ini of de MDT-DB. Deze eigenschap behandelen als alleen-lezen.  

|**Geconfigureerd door de eigenschap**|||**De eigenschap is van toepassing op**||  
|-|-|-|-|-|  
|BootStrap.ini|||LTI|-|  
|CustomSettings.ini|||||  
|MDT-DB|||ZTI|-|  

|**Waarde**|**Beschrijving**|  
|-|-|
|**DE WAARDE TRUE**|De processorresources van de doelcomputer ondersteuning NX-technologie.|  
|**DE WAARDE FALSE**|De processorresources van de doelcomputer bieden geen ondersteuning voor NX-technologie.|  

|**Voorbeeld**|  
|-|  
|Geen|  

####  <a name="SupportsVT"></a>SupportsVT  
 Hiermee geeft u op of de functie Virtualization Technology (VT) wordt ondersteund door de processorbronnen op de doelcomputer. VT wordt gebruikt ter ondersteuning van de huidige gevirtualiseerde omgevingen zoals Hyper-V. Deze eigenschap is ingesteld met behulp van informatie van de CPUID-interface.  

 Zie voor meer informatie over virtuele machines die worden verzameld en informatie die wordt geretourneerd van de interface CPUID, de volgende eigenschappen:  

-   **IsHypervisorRunning**  

-   **IsVM**  

-   **SupportsHyperVRole**  

-   **SupportsNX**  

-   **Supports64Bit**  

-   **VMPlatform**  

> [!NOTE]
>  Deze eigenschap wordt dynamisch ingesteld door de MDT-scripts en is niet geconfigureerd in CustomSettings.ini of de MDT-DB. Deze eigenschap behandelen als alleen-lezen.  

|**Geconfigureerd door de eigenschap**|||**De eigenschap is van toepassing op**||  
|-|-|-|-|-|  
|BootStrap.ini|||LTI|-|  
|CustomSettings.ini|||||  
|MDT-DB|||ZTI|-|  

|**Waarde**|**Beschrijving**|  
|-|-|
|**DE WAARDE TRUE**|De processorresources van de doelcomputer ondersteuning VT-technologie.|  
|**DE WAARDE FALSE**|De processorresources van de doelcomputer bieden geen ondersteuning voor VT-technologie.|  

|**Voorbeeld**|  
|-|  
|Geen|  

####  <a name="Supports64Bit"></a>Supports64Bit  
 Hiermee geeft u op of de processorbronnen op de doelcomputer ondersteuning voor Windows 64-bits besturingssystemen. De meeste moderne virtualisatieomgevingen vereist een 64-bits processorarchitectuur. Deze eigenschap is ingesteld met behulp van informatie uit de **CPUID** interface.  

 Voor meer informatie over virtuele machines die is verzameld en informatie die wordt geretourneerd vanaf de **CPUID** interface, Zie de volgende eigenschappen:  

-   **IsHypervisorRunning**  

-   **IsVM**  

-   **SupportsHyperVRole**  

-   **SupportsNX**  

-   **SupportsVT**  

-   **VMPlatform**  

> [!NOTE]
>  Deze eigenschap wordt dynamisch ingesteld door de MDT-scripts en is niet geconfigureerd in CustomSettings.ini of de MDT-DB. Deze eigenschap behandelen als alleen-lezen.  

|**Geconfigureerd door de eigenschap**|||**De eigenschap is van toepassing op**||  
|-|-|-|-|-|  
|BootStrap.ini|||LTI|-|  
|CustomSettings.ini|||||  
|MDT-DB|||ZTI|-|  

|**Waarde**|**Beschrijving**|  
|-|-|
|**DE WAARDE TRUE**|De processorresources van de doelcomputer ondersteuning voor een Windows 64-bits besturingssysteem.|  
|**DE WAARDE FALSE**|De processorresources van de doelcomputer bieden geen ondersteuning voor een Windows 64-bits besturingssysteem.|  

|**Voorbeeld**|  
|-|  
|Geen|  

####  <a name="SysVolPath"></a>SysVolPath  
 Hiermee geeft u de volledig gekwalificeerde, niet-UNC-pad naar een map op de harde schijf van de lokale computer.  

|**Geconfigureerd door de eigenschap**|||**De eigenschap is van toepassing op**||  
|-|-|-|-|-|  
|BootStrap.ini|||LTI|-|  
|CustomSettings.ini|-||||  
|MDT-DB|-||ZTI|-|  

|**Waarde**|**Beschrijving**|  
|-|-|
|*pad*|Hiermee geeft u de volledig gekwalificeerde, niet-UNC-pad naar een map op de harde schijf van de lokale computer|  

|**Voorbeeld**|  
|-|  
|`[Settings] Priority=Default  [Default] SysVolPath=%DestinationLogicalDrive%\Windows\Sysvol`|  

####  <a name="Table"></a>Tabel  
 De naam van de tabel of weergave moet worden gebruikt bij het uitvoeren van een databasequery eigenschapswaarden van kolommen in de tabel of weergave retourneert. De query is gebaseerd op de parameters die zijn opgegeven de **Parameters** en **ParameterCondition** eigenschappen. De tabel of weergave bevindt zich in de database die is opgegeven in de **Database** eigenschap. De computer met SQL Server is opgegeven in de **SQLServer** eigenschap. Het exemplaar van SQL Server op de computer is opgegeven de **exemplaar** eigenschap.  

|**Geconfigureerd door de eigenschap**|||**De eigenschap is van toepassing op**||  
|-|-|-|-|-|  
|BootStrap.ini|-||LTI|-|  
|CustomSettings.ini|-||||  
|MDT-DB|||ZTI|-|  

|**Waarde**|**Beschrijving**|  
|-|-|
|*TABLE_NAME*|De naam van de tabel of weergave moeten worden opgevraagd voor eigenschapswaarden|  

|**Voorbeeld**|  
|-|  
|`[Settings] Priority=Computers, Default  [Default] OSInstall=YES ScanStateArgs=/v:5 /o /c LoadStateArgs=/v:5 /c /lac  [Computers] SQLServer=NYC-SQL-01 SQLShare=SQL$ Database=MDTDB Instance=MDT2010 Table=Computers Parameters=SerialNumber, AssetTag ParameterCondition=OR`|  

####  <a name="TaskSequenceID"></a>TaskSequenceID  
 Identificeert de takenreeks voor het besturingssysteem worden geïmplementeerd op de doelcomputer. De taak-ID wordt gemaakt op het knooppunt Takenreeksen in de implementatie-Workbench. De **TaskSequenceID** eigenschap kunt alfanumerieke tekens, afbreekstreepjes (-) en onderstrepingstekens (\_). De **TaskSequenceID** eigenschap mag niet leeg zijn of spaties bevatten.  

|**Geconfigureerd door de eigenschap**|||**De eigenschap is van toepassing op**||  
|-|-|-|-|-|  
|BootStrap.ini|||LTI|-|  
|CustomSettings.ini|-||||  
|MDT-DB|-||ZTI||  

|**Waarde**|**Beschrijving**|  
|-|-|
|*task_sequence_id*|Id van de takenreeks van het besturingssysteem gedefinieerd in de Workbench-implementatie voor het beoogde besturingssysteem wordt geïmplementeerd<br /><br /> Opmerking:<br /><br /> Zorg ervoor dat u de **TaskSequenceID** opgegeven in de gebruikersinterface van de Workbench-implementatie, niet de GUID van de **TaskSequenceID**.|  

|**Voorbeeld**|  
|-|  
|`[Settings] Priority=Default  [Default] TaskSequenceID=BareMetal`|  

####  <a name="TaskSequenceName"></a>TaskSequenceName  
 Hiermee geeft u de naam van de takenreeks wordt uitgevoerd.  

> [!NOTE]
>  Deze eigenschap wordt dynamisch ingesteld door de MDT-scripts en is niet geconfigureerd in CustomSettings.ini of de MDT-DB. Deze eigenschap behandelen als alleen-lezen.  

|**Geconfigureerd door de eigenschap**|||**De eigenschap is van toepassing op**||  
|-|-|-|-|-|  
|BootStrap.ini|||LTI|-|  
|CustomSettings.ini|||||  
|MDT-DB|||ZTI||  

|**Waarde**|**Beschrijving**|  
|-|-|
|*task_sequence_name*|Naam van de takenreeks wordt uitgevoerd, zoals implementeren *Windows 8.1 naar referentiecomputer*|  

|**Voorbeeld**|  
|-|  
|Geen|  

####  <a name="TaskSequenceVersion"></a>TaskSequenceVersion  
 Hiermee geeft u de versie van de takenreeks wordt uitgevoerd.  

> [!NOTE]
>  Deze eigenschap wordt dynamisch ingesteld door de MDT-scripts en is niet geconfigureerd in CustomSettings.ini of de MDT-DB. Deze eigenschap behandelen als alleen-lezen.  

|**Geconfigureerd door de eigenschap**|||**De eigenschap is van toepassing op**||  
|-|-|-|-|-|  
|BootStrap.ini|||LTI|-|  
|CustomSettings.ini|||||  
|MDT-DB|||ZTI||  

|**Waarde**|**Beschrijving**|  
|-|-|
|*task_sequence_version*|Versie van de takenreeks wordt uitgevoerd, zoals *1,00*|  

|**Voorbeeld**|  
|-|  
|Geen|  

####  <a name="TimeZoneName"></a>TimeZoneName  
 De tijdzone waarin de doelcomputer zich bevindt. Deze waarde wordt ingevoegd in de juiste configuratie-instellingen in Unattend.xml.  

|**Geconfigureerd door de eigenschap**|||**De eigenschap is van toepassing op**||  
|-|-|-|-|-|  
|BootStrap.ini|||LTI|-|  
|CustomSettings.ini|-||||  
|MDT-DB|-||ZTI|-|  

|**Waarde**|**Beschrijving**|  
|-|-|
|*time_zone_name*|De tekstwaarde die aangeeft van de tijdzone waar de doelcomputer zich bevindt|  

|**Voorbeeld**|  
|-|  
|`[Settings] Priority=Default  [Default] TimeZoneName=Pacific Standard Time DeployRoot=\\NYC-AM-FIL-01\Distribution$ ResourceRoot=\\NYC-AM-FIL-01\Resource$ UDShare=\\NYC-AM-FIL-01\MigData$ UDDir=%OSDComputerName% SLShare=\\NYC-AM-FIL-01\Logs$ UDProfiles=Administrator, User-01, ExtranetUser UserDataLocation=NONE`|  

####  <a name="ToolRoot"></a>ToolRoot  
 Hiermee geeft u het UNC-pad naar de hulpprogramma's\\*proc_arch* map (waarbij *proc_arch* is van de processorarchitectuur van het besturingssysteem die momenteel worden uitgevoerd en kunnen een waarde van **x86** of **x64**), die wordt onmiddellijk onder de hoofdmap van de mapstructuur die is opgegeven in de **DeployRoot** eigenschap. De hulpprogramma's\\*proc_arch* map bevat hulpprogramma's die MDT wordt gebruikt tijdens de implementatie.  

> [!NOTE]
>  Deze eigenschap wordt dynamisch ingesteld door de MDT-scripts en is niet geconfigureerd in CustomSettings.ini of de MDT-DB. Deze eigenschap behandelen als alleen-lezen.  

|**Geconfigureerd door de eigenschap**|||**De eigenschap is van toepassing op**||  
|-|-|-|-|-|  
|BootStrap.ini|||LTI|-|  
|CustomSettings.ini|||||  
|MDT-DB|||ZTI|-|  

|**Waarde**|**Beschrijving**|  
|-|-|
|*pad*|De UNC of lokale pad naar de hulpprogramma's\\*proc_arch* map (waarbij *proc_arch* is van de processorarchitectuur van het besturingssysteem die momenteel worden uitgevoerd en kunnen een waarde van  **x86** of **x64**) direct onder de hoofdmap van de mapstructuur die is opgegeven door de **DeployRoot** eigenschap|  

|**Voorbeeld**|  
|-|  
|Geen|  

####  <a name="TPMOwnerPassword"></a>TPMOwnerPassword  
 Het wachtwoord voor TPM (ook wel bekend als de *wachtwoord voor het beheer van TPM*) voor de eigenaar van de doelcomputer. Het wachtwoord worden opgeslagen in een bestand of opgeslagen in AD DS.  

> [!NOTE]
>  Als de TPM-eigenaar is al ingesteld of eigendom van de TPM niet is toegestaan, wordt de **TPMOwnerPassword** eigenschap wordt genegeerd. Als het wachtwoord voor TPM is vereist en de **TPMOwnerPassword** eigenschap is niet opgegeven, wordt het wachtwoord voor TPM ingesteld op het lokale Administrator-wachtwoord.  

|**Geconfigureerd door de eigenschap**|||**De eigenschap is van toepassing op**||  
|-|-|-|-|-|  
|BootStrap.ini|||LTI|-|  
|CustomSettings.ini|-||||  
|MDT-DB|-||ZTI|-|  

|**Waarde**|**Beschrijving**|  
|-|-|
|*wachtwoord*|Het wachtwoord voor TPM voor de eigenaar van de doelcomputer|  

|**Voorbeeld**|  
|-|  
|`[Settings] Priority=Default  [Default] BDEDriveLetter=S: BDEDriveSize=2000 BDEInstall=TPMKey BDERecoveryKey=TRUE BDEKeyLocation=C: TPMOwnerPassword=<complex_password> BackupShare=\\NYC-AM-FIL-01\Backup$ BackupDir=%OSDComputerName% DeployRoot=\\NYC-AM-FIL-01\Distribution$ ResourceRoot=\\NYC-AM-FIL-01\Resource$ UDShare=\\NYC-AM-FIL-01\MigData$ UDDir=%OSDComputerName%`|  

####  <a name="UDDir"></a>UDDir  
 De map waarin de gegevens van de migratie van gebruikersstatus is opgeslagen. Deze map bestaat onder de gedeelde netwerkmap opgegeven in **UDShare**.  

|**Geconfigureerd door de eigenschap**|||**De eigenschap is van toepassing op**||  
|-|-|-|-|-|  
|BootStrap.ini|||LTI|-|  
|CustomSettings.ini|-||||  
|MDT-DB|-||ZTI||  

|**Waarde**|**Beschrijving**|  
|-|-|
|*map*|De naam van de map die onder de gedeelde netwerkmap bestaat|  

|**Voorbeeld**|  
|-|  
|`[Settings] Priority=Default  [Default] DeployRoot=\\NYC-AM-FIL-01\Distribution$ ResourceRoot=\\NYC-AM-FIL-01\Resource$ UDShare=\\NYC-AM-FIL-01\MigData$ UDDir=%OSDComputerName% SLShare=\\NYC-AM-FIL-01\Logs$ UDProfiles=Administrator, User-01, ExtranetUser UserDataLocation=NONE SkipCapture=NO`|  

####  <a name="UDProfiles"></a>UDProfiles  
 Een door komma's gescheiden lijst met profielen voor gebruikers die moeten worden opgeslagen door Scanstate.exe tijdens de fase voor het vastleggen van status.  

|**Geconfigureerd door de eigenschap**|||**De eigenschap is van toepassing op**||  
|-|-|-|-|-|  
|BootStrap.ini|||LTI|-|  
|CustomSettings.ini|-||||  
|MDT-DB|-||ZTI||  

|**Waarde**|**Beschrijving**|  
|-|-|
|*user_profiles*|De lijst met gebruikersprofielen worden opgeslagen, gescheiden door komma 's|  

|**Voorbeeld**|  
|-|  
|`[Settings] Priority=Default  [Default] DeployRoot=\\NYC-AM-FIL-01\Distribution$ ResourceRoot=\\NYC-AM-FIL-01\Resource$ UDShare=\\NYC-AM-FIL-01\MigData$ UDDir=%OSDComputerName% SLShare=\\NYC-AM-FIL-01\Logs$ UDProfiles=Administrator, User-01, ExtranetUser UserDataLocation=NONE SkipCapture=NO`|  

####  <a name="UDShare"></a>UDShare  
 De netwerkshare waar de migratiegegevens Gebruikersstatus is opgeslagen.  

|**Geconfigureerd door de eigenschap**|||**De eigenschap is van toepassing op**||  
|-|-|-|-|-|  
|BootStrap.ini|||LTI|-|  
|CustomSettings.ini|-||||  
|MDT-DB|-||ZTI||  

|**Waarde**|**Beschrijving**|  
|-|-|
|*UNC_path*|Het UNC-pad naar de netwerkshare waar de migratiegegevens Gebruikersstatus is opgeslagen|  

|**Voorbeeld**|  
|-|  
|`[Settings] Priority=Default  [Default] DeployRoot=\\NYC-AM-FIL-01\Distribution$ ResourceRoot=\\NYC-AM-FIL-01\Resource$ UDShare=\\NYC-AM-FIL-01\MigData$ UDDir=%OSDComputerName% SLShare=\\NYC-AM-FIL-01\Logs$ UDProfiles=Administrator, User-01, ExtranetUser UserDataLocation=NONE SkipCapture=NO`|  

####  <a name="UILanguage"></a>UILanguage  
 De standaardtaal die gebruikt worden bij het beoogde besturingssysteem. Als niet wordt opgegeven, de **implementatiewizard** de taal die is geconfigureerd in de installatiekopie wordt geïmplementeerd.  

|**Geconfigureerd door de eigenschap**|||**De eigenschap is van toepassing op**||  
|-|-|-|-|-|  
|BootStrap.ini|||LTI|-|  
|CustomSettings.ini|-||||  
|MDT-DB|-||ZTI|-|  

|**Waarde**|**Beschrijving**|  
|-|-|
|*UI_language*|De standaardtaal voor het besturingssysteem op de doelcomputer|  

|**Voorbeeld**|  
|-|  
|`[Settings] Priority=Default  [Default] UserLocale=en-us UILanguage=en-us KeyboardLocale=0409:00000409`|  

####  <a name="UserDataLocation"></a>UserDataLocation  
 De locatie waarin USMT statusmigratiegegevens opslaat.  

> [!CAUTION]
>  Waarde van deze eigenschap moet in hoofdletters worden opgegeven zodat de implementatiescripts kunnen correct worden gelezen.  

|**Geconfigureerd door de eigenschap**|||**De eigenschap is van toepassing op**||  
|-|-|-|-|-|  
|BootStrap.ini|||LTI|-|  
|CustomSettings.ini|-||||  
|MDT-DB|-||ZTI||  

|**Waarde**|**Beschrijving**|  
|-|-|
|Lege|Als **UserDataLocation**is niet opgegeven of leeg is, wordt standaard de implementatiewizard met behulp van het gedrag van automatisch.|  
|*UNC_path*|Het UNC-pad naar de gedeelde netwerkmap waar de migratiegegevens van de gebruikersstatus is opgeslagen.|  
|**AUTO**|Als ruimte beschikbaar is, de implementatiescripts migratiegegevens van de gebruikersstatus opslaan op een lokale vaste schijf. Anders wordt de migratiegegevens van de gebruikersstatus is opgeslagen in een netwerklocatie die is opgegeven in de **UDShare** en **UDDir** eigenschappen.|  
|**NETWERK**|Migratiegegevens van de gebruikersstatus is opgeslagen in de locatie die is aangewezen door de **UDShare** en **UDDir** eigenschappen.|  
|**GEEN**|De statusmigratiegegevens worden niet opgeslagen.|  

|**Voorbeeld**|  
|-|  
|`[Settings] Priority=Default  [Default] OSInstall=YES ScanStateArgs=/v:5 /o /c LoadStateArgs=/v:5 /c /lac DoCapture=YES BackupShare=\\NYC-AM-FIL-01\Backup$ BackupDir=%OSDComputerName% UserDataLocation=NETWORK DeployRoot=\\NYC-AM-FIL-01\Distribution$ ResourceRoot=\\NYC-AM-FIL-01\Resource$ UDShare=\\NYC-AM-FIL-01\MigData$ UDDir=%OSDComputerName%`|  

####  <a name="UserDomain"></a>UserDomain  
 Het domein waarin de referenties van een gebruiker (opgegeven in de **UserID** eigenschap) zich bevinden.  

> [!NOTE]
>  Voor een volledig geautomatiseerde implementatie van de LTI, geeft deze eigenschap in CustomSettings.ini en BootStrap.ini. Echter Houd er rekening mee dat de gebruikersreferenties opslaan in deze bestanden de referenties in gewone tekst slaat en daarom niet beveiligd is.  

|**Geconfigureerd door de eigenschap**|||**De eigenschap is van toepassing op**||  
|-|-|-|-|-|  
|BootStrap.ini|-||LTI|-|  
|CustomSettings.ini|-||||  
|MDT-DB|-||ZTI||  

|**Waarde**|**Beschrijving**|  
|-|-|
|*domein*|De naam van het domein waar de referenties van de gebruiker zich bevinden|  

|**Voorbeeld**|  
|-|  
|`[Settings] Priority=Default  [Default] OSInstall=YES ScanStateArgs=/v:5 /o /c LoadStateArgs=/v:5 /c /lac DeployRoot=\\NYC-AM-FIL-01\Distribution$ ResourceRoot=\\NYC-AM-FIL-01\Resource$ UserDataLocation=NONE UserDomain=WOODGROVEBANK UserID=NYC Help Desk Staff UserPassword=<complex_password>`|  

####  <a name="UserID"></a>Gebruikers-id  
 De gebruikersreferenties voor toegang tot netwerkbronnen.  

> [!NOTE]
>  Voor een volledig geautomatiseerde implementatie van de LTI, geeft deze eigenschap in CustomSettings.ini en BootStrap.ini. Echter Houd er rekening mee dat de gebruikersreferenties opslaan in deze bestanden de referenties in gewone tekst slaat en daarom niet beveiligd is.  

|**Geconfigureerd door de eigenschap**|||**De eigenschap is van toepassing op**||  
|-|-|-|-|-|  
|BootStrap.ini|-||LTI|-|  
|CustomSettings.ini|-||||  
|MDT-DB|-||ZTI||  

|**Waarde**|**Beschrijving**|  
|-|-|
|*USER_ID*|De naam van de referenties van de gebruiker gebruikt voor toegang tot de netwerkbronnen|  

|**Voorbeeld**|  
|-|  
|`[Settings] Priority=Default  [Default] OSInstall=YES ScanStateArgs=/v:5 /o /c LoadStateArgs=/v:5 /c /lac DeployRoot=\\NYC-AM-FIL-01\Distribution$ ResourceRoot=\\NYC-AM-FIL-01\Resource$ UserDataLocation=NONE UserDomain=WOODGROVEBANK UserID=NYC-HelpDesk UserPassword=<complex_password>`|  

####  <a name="UserLocale"></a>UserLocale  
 De landinstellingen van de gebruiker moet worden gebruikt met het beoogde besturingssysteem. Als niet wordt opgegeven, de **implementatiewizard** maakt gebruik van de landinstelling die is geconfigureerd in de installatiekopie wordt geïmplementeerd.  

|**Geconfigureerd door de eigenschap**|||**De eigenschap is van toepassing op**||  
|-|-|-|-|-|  
|BootStrap.ini|||LTI|-|  
|CustomSettings.ini|-||||  
|MDT-DB|-||ZTI|-|  

|**Waarde**|**Beschrijving**|  
|-|-|
|*user_locale*|De landinstellingen voor de gebruiker op de doelcomputer. De waarde is opgegeven als een tekstwaarde (en-us).|  

|**Voorbeeld 1**|  
|-|  
|`[Settings] Priority=Default  [Default] UserLocale=en-us KeyboardLocale=0409:00000409`|  

|**Voorbeeld 2**|  
|-|  
|`[Settings] Priority=Default  [Default] UserLocale=en-us KeyboardLocale=en-us`|  

####  <a name="UserPassword"></a>UserPassword  
 Het wachtwoord voor de referenties van de gebruiker is opgegeven in de **UserID** eigenschap.  

> [!NOTE]
>  Voor een volledig geautomatiseerde implementatie van de LTI, geeft deze eigenschap in CustomSettings.ini en BootStrap.ini. Echter Houd er rekening mee dat de gebruikersreferenties opslaan in deze bestanden de referenties in gewone tekst slaat en daarom niet beveiligd is.  

|**Geconfigureerd door de eigenschap**|||**De eigenschap is van toepassing op**||  
|-|-|-|-|-|  
|BootStrap.ini|-||LTI|-|  
|CustomSettings.ini|-||||  
|MDT-DB|-||ZTI||  

|**Waarde**|**Beschrijving**|  
|-|-|
|*user_password*|Het wachtwoord voor de referenties van de gebruiker|  

|**Voorbeeld**|  
|-|  
|`[Settings] Priority=Default  [Default] UserDataLocation=NONE UserDomain=WOODGROVEBANK UserID=NYC-HelpDesk UserPassword=<complex_password>`|  

####  <a name="USMTConfigFile"></a>USMTConfigFile  
 De USMT XML-configuratiebestand dat moet worden gebruikt bij het uitvoeren van **Scanstate** en **Loadstate**.  

|**Geconfigureerd door de eigenschap**|||**De eigenschap is van toepassing op**||  
|-|-|-|-|-|  
|BootStrap.ini|||LTI|-|  
|CustomSettings.ini|-||||  
|MDT-DB|-||ZTI||  

|**Waarde**|**Beschrijving**|  
|-|-|
|*USMTConfigFile*|De naam van het XML-configuratiebestand dat moet worden gebruikt bij het uitvoeren van Scanstate.exe en Loadstate.exe|  

|**Voorbeeld**|  
|-|  
|`[Settings] Priority=Default  [Default] OSInstall=YES ScanStateArgs=/v:5 /o /c LoadStateArgs=/v:5 /c /lac DeployRoot=\\NYC-AM-FIL-01\Distribution$ ResourceRoot=\\NYC-AM-FIL-01\Resource$ UDShare=\\NYC-AM-FIL-01\MigData$ UDDir=%OSDComputerName% SLShare=\\NYC-AM-FIL-01\Logs$ USMTMigFiles1=MigApp.xml USMTMigFiles2=MigUser.xml USMTMigFiles3=MigSys.xml USMTMigFiles4=MigCustom.xml USMTConfigFile=USMTConfig.xml UserDataLocation=NONE`|  

####  <a name="USMTLocal"></a>USMTLocal  
 Deze eigenschap geeft aan of de USMT-gebruikersstatusinformatie lokaal worden opgeslagen op de doelcomputer. Deze eigenschap wordt voornamelijk gebruikt door de [ZTIUserState.wsf](#ZTIUserState.wsf) en [ZTIBackup.wsf](#ZTIBackup.wsf) scripts aangeeft dat de **Statusopslag opvragen** en **Release-status Store** takenreeksstappen voor Configuration Manager-implementaties worden overgeslagen. Zie voor meer informatie de [OSDStateStorePath](#OSDStateStorePath) eigenschap.  

> [!NOTE]
>  Deze eigenschap mag alleen worden gebruikt in het geval dat wordt beschreven in de [OSDStateStorePath](#OSDStateStorePath) eigenschap).  

|**Geconfigureerd door de eigenschap**|||**De eigenschap is van toepassing op**||  
|-|-|-|-|-|  
|BootStrap.ini|||LTI||  
|CustomSettings.ini|||||  
|MDT-DB|||ZTI|-|  

|**Waarde**|**Beschrijving**|  
|-|-|
|**DE WAARDE TRUE**|De status van USMT gebruikersgegevens lokaal wordt opgeslagen op de doelcomputer en de **Statusopslag opvragen** en **Statusopslag vrijgeven** takenreeksstappen worden overgeslagen.|  
|**DE WAARDE FALSE**|De USMT-gebruikersstatusinformatie niet lokaal is opgeslagen op de doelcomputer en de **Statusopslag opvragen** en **Statusopslag vrijgeven** takenreeksstappen worden uitgevoerd.|  

|**Voorbeeld**|  
|-|  
|`[Settings] Priority=Default  [Default] OSInstall=YES ScanStateArgs=/v:5 /o /c LoadStateArgs=/v:5 /c /lac DeployRoot=\\NYC-AM-FIL-01\Distribution$ ResourceRoot=\\NYC-AM-FIL-01\Resource$ UDShare=\\NYC-AM-FIL-01\MigData$ UDDir=%OSDComputerName% SLShare=\\NYC-AM-FIL-01\Logs$ USMTLocal=TRUE USMTMigFiles001=MigApp.xml USMTMigFiles002=MigUser.xml USMTMigFiles003=MigSys.xml USMTMigFiles004=MigCustom.xml UserDataLocation=NONE`|  

####  <a name="USMTMigFiles"></a>USMTMigFiles  
 Een lijst met bestanden in XML-indeling die door USMT (Scanstate.exe) worden gebruikt voor het identificeren van de gebruiker statusmigratie-informatie op te slaan. Als deze eigenschap niet is opgegeven, wordt het script ZTIUserState.wsf gebruikt MigApp.xml MigUser.xml en MigSys.xml. Anders ZTIUserState.wsf de bestanden expliciet waarnaar wordt verwezen in deze eigenschap gebruikt. De **USMTMigFiles** eigenschap heeft een numeriek achtervoegsel (bijvoorbeeld **USMTMigFiles001** of **USMTMigFiles002**).  

> [!NOTE]
>  Gebruik deze eigenschap om op te geven van de XML-bestanden kunnen worden gebruikt door Scanstate.exe in plaats van de **/I** parameter in de **ScanStateArgs** eigenschap. Dit voorkomt dat het script ZTIUserState.wsf mogelijk dupliceren van dezelfde lijst met XML-bestanden.  

> [!NOTE]
>  De naam van deze eigenschap kan worden opgegeven met één cijfer naamgeving volgt de namen (**USMTMigFiles1**) of drie cijfers naamgeving volgt de namen (**USMTMigFiles001**).  

|**Geconfigureerd door de eigenschap**|||**De eigenschap is van toepassing op**||  
|-|-|-|-|-|  
|BootStrap.ini|||LTI|-|  
|CustomSettings.ini|-||||  
|MDT-DB|||ZTI||  

|**Waarde**|**Beschrijving**|  
|-|-|
|*USMTMigFile*|De naam van het .xml-bestand moet worden gebruikt als invoer voor Scanstate.exe, op afzonderlijke regels. Als u niet opgeeft, wordt de standaardwaarde is MigApp.xml MigUser.xml en MigSys.xml.<br /><br /> Opmerking:<br /><br /> Als deze waarde is opgegeven, moeten de standaard-bestanden (MigApp.xml, MigUser.xml en MigSys.xml) ook worden toegevoegd aan de lijst als deze bestanden moeten worden opgenomen.|  

|**Voorbeeld**|  
|-|  
|`[Settings] Priority=Default  [Default] OSInstall=YES ScanStateArgs=/v:5 /o /c LoadStateArgs=/v:5 /c /lac DeployRoot=\\NYC-AM-FIL-01\Distribution$ ResourceRoot=\\NYC-AM-FIL-01\Resource$ UDShare=\\NYC-AM-FIL-01\MigData$ UDDir=%OSDComputerName% SLShare=\\NYC-AM-FIL-01\Logs$ USMTMigFiles001=MigApp.xml USMTMigFiles002=MigUser.xml USMTMigFiles003=MigSys.xml USMTMigFiles004=MigCustom.xml UserDataLocation=NONE`|  

####  <a name="USMTOfflineMigration"></a>USMTOfflineMigration  
 Deze eigenschap bepaalt of MDT USMT gebruikt voor het uitvoeren van een offline user state Migration Tool. In een offlinemigratie wordt de vastlegging van de uitgevoerd in Windows PE in plaats van het bestaande besturingssysteem.  

 Offlinemigratie wordt gebruikt voor USMT wordt uitgevoerd:  

-   UDI altijd, ongeacht de instelling van de **USMTOfflineMigration** eigenschap  

-   ZTI alleen voor het vernieuwen Computer MDT implementatiescenario en alleen wanneer de **USMTOfflineMigration** eigenschap is ingesteld op **'TRUE'**  

    > [!NOTE]
    >  U kunt USMT offline gebruikersstatusmigratie niet uitvoeren in de nieuwe Computer MDT implementatiescenario met behulp van ZTI.  

-   LTI voor de:  

    1.  De nieuwe Computer MDT implementatie scenario op met de **gegevens verplaatsen en instellingen** pagina in de Wizard implementatie van de wizard  

    2.  Implementatiescenario vernieuwen Computer MDT en alleen wanneer de **USMTOfflineMigration** eigenschap is ingesteld op **'TRUE'**  

 Zie voor meer informatie over het met MDT en de USMT voor het uitvoeren van een offline user state Migration Tool 'Configureren USMT Offline User State Migration Tool'.  

|**Geconfigureerd door de eigenschap**|||**De eigenschap is van toepassing op**||  
|-|-|-|-|-|  
|BootStrap.ini|||LTI|-|  
|CustomSettings.ini|-||||  
|MDT-DB|||ZTI|-|  

|**Waarde**|**Beschrijving**|  
|-|-|
|**DE WAARDE TRUE**|USMT MDT gebruikt voor het uitvoeren van een offline user state Migration Tool.|  
|*Een andere waarde*|MDT voert een offline user state Migration Tool. In plaats daarvan wordt migratie van gebruikersstatus vastgelegd in het bestaande besturingssysteem. Dit is de standaardwaarde.|  

|**Voorbeeld**|  
|-|  
|`[Settings] Priority=Default  [Default] OSInstall=YES SkipUserData=YES USMTOfflineMigration=TRUE DoNotFormatAndPartition=YES OSDStateStorePath=\\WDG-MDT-01\StateStore$`|  

####  <a name="UUID"></a>UUID  
 De universele Unique Identifier (UUID) opgeslagen in de System Management BIOS van de doelcomputer.  

 De indeling voor UUID is een waarde van 16 bytes met hexadecimale cijfers in de volgende indeling: *12345678-1234-1234-1234-123456789ABC*. Gebruik deze eigenschap te maken van een subsectie met instellingen die zijn gericht op een specifieke computer.  

> [!NOTE]
>  Deze eigenschap wordt dynamisch ingesteld door de MDT-scripts en de waarde is ingesteld in CustomSettings.ini of de MDT-DB kan hebben. Deze eigenschap behandelen als alleen-lezen. Echter kunt u deze eigenschap binnen CustomSettings.ini of de MDT-database, zoals wordt weergegeven in de volgende voorbeelden om te helpen bij het definiëren van de configuratie van de doelcomputer.  

|**Geconfigureerd door de eigenschap**|||**De eigenschap is van toepassing op**||  
|-|-|-|-|-|  
|BootStrap.ini|||LTI|-|  
|CustomSettings.ini|||||  
|MDT-DB|||ZTI|-|  

|**Waarde**|**Beschrijving**|  
|-|-|
|*UUID*|De UUID van de doelcomputer|  

|**Voorbeeld**|  
|-|  
|Geen|  

####  <a name="ValidateDomainCredentialsUNC"></a>ValidateDomainCredentialsUNC  
 Deze eigenschap wordt gebruikt om op te geven van een UNC-pad naar een gedeelde netwerkmap die wordt gebruikt voor het valideren van de referenties voor het toevoegen van de doelcomputer aan een domein. Het wordt gevalideerd referenties zijn opgegeven in de **DomainAdmin**, **DomainAdminDomain**, en **DomainAdminPassword** eigenschappen.  

> [!NOTE]
>  Zorg dat er geen andere eigenschappen in MDT de server in de map voor deze eigenschap gebruikt. Met behulp van een server die al wordt verwezen door andere eigenschappen MDT kan leiden tot onjuiste validatie van de referenties.  

|**Geconfigureerd door de eigenschap**|||**De eigenschap is van toepassing op**||  
|-|-|-|-|-|  
|BootStrap.ini|||LTI|-|  
|CustomSettings.ini|-||||  
|MDT-DB|-||ZTI||  

|**Waarde**|**Beschrijving**|  
|-|-|
|*unc_path*|Hiermee geeft u de volledig gekwalificeerde UNC-pad naar een gedeelde netwerkmap|  

|**Voorbeeld**|  
|-|  
|`[Settings] Priority=Default  [Default] ValidateDomainCredentialsUNC=\\wdg-fs-01\Source$`|  

####  <a name="VHDCreateDiffVHD"></a>VHDCreateDiffVHD  
 Deze eigenschap wordt gebruikt om de naam van een differentiërende VHD geven (ook wel bekend als een *onderliggende VHD*) bestand. Een differentiërende VHD is vergelijkbaar met een dynamisch uitbreidbare VHD, maar bevat alleen de gewijzigde schijfblokken van de bijbehorende bovenliggende VHD. De bovenliggende VHD is alleen-lezen, dus moet u de differentiërende VHD wijzigen. De differentiërende VHD-bestand wordt gemaakt in dezelfde map als de bovenliggende VHD-bestand, zodat alleen de bestandsnaam is opgegeven voor deze eigenschap. Deze eigenschap is alleen geldig voor het scenario van de nieuwe Computer MDT-implementatie.  

> [!NOTE]
>  Alle bovenliggende VHD-bestanden gemaakt door MDT worden in de VHD-map in de hoofdmap van de bovenliggende schijf opgeslagen.  

 Deze eigenschap wordt meestal ingesteld met behulp van een takenreeksstap gemaakt met behulp van de **maken van virtuele hardeschijf (VHD)** type takenreeks van de taak. U kunt de waarde overschrijven de **maken van virtuele hardeschijf (VHD)** takenreeksstap wordt ingesteld met het configureren van deze eigenschap in CustomSettings.ini.  

> [!NOTE]
>  Voor het configureren van deze eigenschap in CustomSettings.ini, u moet deze eigenschap toevoegen aan de **eigenschappen** CustomSettings.ini regel.  

 Zie voor de bijbehorende eigenschappen die worden gebruikt met VHD-bestanden:  

-   **VHDCreateFileName**  

-   **VHDCreateSizeMax**  

-   **VHDCreateSource**  

-   **VHDCreateType**  

-   **VHDDisks**  

-   **VHDInputVariable**  

-   **VHDOutputVariable**  

-   **VHDTargetDisk**  

|**Geconfigureerd door de eigenschap**|||**De eigenschap is van toepassing op**||  
|-|-|-|-|-|  
|BootStrap.ini|||LTI|-|  
|CustomSettings.ini|-||||  
|MDT-DB|||ZTI||  

|**Waarde**|**Beschrijving**|  
|-|-|
|*bestandsnaam*|Geeft de naam van de differentiërende VHD-bestand, dat zich in dezelfde map als het bovenliggende VHD-bestand<br /><br /> De differentiërende VHD-bestand kan niet dezelfde naam als de bovenliggende VHD-bestand hebben.|  
|**WILLEKEURIGE**|Genereert automatisch een willekeurige naam voor de differentiërende VHD-bestand, dat zich in dezelfde map als het bovenliggende VHD-bestand|  

|**Voorbeeld**|  
|-|  
|`[Settings] Priority=Default  [Default] VHDCreateDiffVHD=Win7Diff_C.vhd VHDInputVariable=VHDTargetDisk`|  

####  <a name="VHDCreateFileName"></a>VHDCreateFileName  
 Deze eigenschap wordt gebruikt om de naam van een VHD-bestand opgeven. Het type VHD-bestand is gebaseerd op de waarde van de **VHDCreateType** eigenschap. De eigenschap is alleen de bestandsnaam, niet het pad naar de bestandsnaam bevat en is alleen geldig voor het scenario van de nieuwe Computer MDT-implementatie.  

> [!NOTE]
>  De VHD-bestanden gemaakt door MDT worden in de VHD-map in de hoofdmap van de bovenliggende schijf opgeslagen.  

 Deze eigenschap wordt meestal ingesteld met behulp van een takenreeksstap gemaakt met behulp van de **maken van virtuele hardeschijf (VHD)** type takenreeks van de taak. U kunt de waarde overschrijven de **maken van virtuele hardeschijf (VHD)** takenreeksstap wordt ingesteld met het configureren van deze eigenschap in CustomSettings.ini.  

> [!NOTE]
>  Voor het configureren van deze eigenschap in CustomSettings.ini, u moet deze eigenschap toevoegen aan de **eigenschappen** CustomSettings.ini regel.  

 Zie voor de bijbehorende eigenschappen die worden gebruikt met VHD-bestanden:  

-   **VHDCreateDiffVHD**  

-   **VHDCreateSizeMax**  

-   **VHDCreateSource**  

-   **VHDCreateType**  

-   **VHDDisks**  

-   **VHDInputVariable**  

-   **VHDOutputVariable**  

-   **VHDTargetDisk**  

|**Geconfigureerd door de eigenschap**|||**De eigenschap is van toepassing op**||  
|-|-|-|-|-|  
|BootStrap.ini|||LTI|-|  
|CustomSettings.ini|-||||  
|MDT-DB|||ZTI||  

|**Waarde**|**Beschrijving**|  
|-|-|
|*bestandsnaam*|Geeft de naam van het VHD-bestand|  
|**WILLEKEURIGE**|Genereert automatisch een willekeurige naam voor het VHD-bestand bevindt zich in de VHD-map in de hoofdmap van het bovenliggende station|  
|Lege|Dezelfde een **willekeurige**|  

|**Voorbeeld**|  
|-|  
|`[Settings] Priority=Default  [Default] VHDCreateSizeMax=130048 VHDCreateType=EXPANDABLE VHDCreateFileName=Win7_C.vhd VHDInputVariable=VHDTargetDisk`|  

####  <a name="VHDCreateSizeMax"></a>VHDCreateSizeMax  
 Deze eigenschap wordt gebruikt voor de maximale grootte van een VHD-bestand opgeven in megabytes (MB). De grootte van het VHD-bestand tijdens het maken, is gebaseerd op het type VHD-bestand wordt gemaakt. Zie voor meer informatie de [VHDCreateType](#VHDCreateType) eigenschap. Deze eigenschap is alleen geldig voor het scenario van de nieuwe Computer MDT-implementatie.  

> [!NOTE]
>  Als deze eigenschap niet is opgegeven, is de standaardwaarde voor de maximale grootte van een VHD-bestand 90% van de beschikbare schijfruimte op de bovenliggende schijf.  

 Deze eigenschap wordt meestal ingesteld met behulp van een takenreeksstap gemaakt met behulp van de **maken van virtuele hardeschijf (VHD)** type takenreeks van de taak. U kunt de waarde overschrijven die de **maken van virtuele hardeschijf (VHD)** takenreeksstap wordt ingesteld met het configureren van deze eigenschap in CustomSettings.ini.  

> [!NOTE]
>  Voor het configureren van deze eigenschap in CustomSettings.ini, u moet deze eigenschap toevoegen aan de **eigenschappen** CustomSettings.ini regel.  

 Zie voor de bijbehorende eigenschappen die worden gebruikt met VHD-bestanden:  

-   **VHDCreateDiffVHD**  

-   **VHDCreateFileName**  

-   **VHDCreateSource**  

-   **VHDCreateType**  

-   **VHDDisks**  

-   **VHDInputVariable**  

-   **VHDOutputVariable**  

-   **VHDTargetDisk**  

|**Geconfigureerd door de eigenschap**|||**De eigenschap is van toepassing op**||  
|-|-|-|-|-|  
|BootStrap.ini|||LTI|-|  
|CustomSettings.ini|-||||  
|MDT-DB|||ZTI||  

|**Waarde**|**Beschrijving**|  
|-|-|
|*grootte*|De maximale grootte van het VHD-bestand dat is opgegeven in MB. Bijvoorbeeld: 130.048 MB is gelijk aan 127 GB. De standaardwaarde is 90% van de beschikbare schijfruimte op de bovenliggende schijf.|  

|**Voorbeeld**|  
|-|  
|`[Settings] Priority=Default  [Default] VHDCreateSizeMax=130048 VHDCreateType=FIXED VHDCreateFileName=Win7_C.vhd VHDInputVariable=VHDTargetDisk`|  

####  <a name="VHDCreateSource"></a>VHDCreateSource  
 Deze eigenschap wordt gebruikt om op te geven van de naam van een VHD-bestand dat wordt gebruikt als een sjabloon (bron) voor het maken van een nieuwe VHD-bestand. U kunt de naam van het bestand met behulp van een UNC-pad, lokaal pad, relatief pad of de bestandsnaam opgeven. Als de bestandsnaam is opgegeven, klikt u vervolgens MDT gezocht naar het VHD-bestand op de doelcomputer. Deze eigenschap is alleen geldig voor het scenario van de nieuwe Computer MDT-implementatie.  

 Deze eigenschap wordt meestal ingesteld met behulp van een takenreeksstap gemaakt met behulp van de **maken van virtuele hardeschijf (VHD)** type takenreeks van de taak. U kunt de waarde overschrijven die de **maken van virtuele hardeschijf (VHD)**takenreeksstap wordt ingesteld met het configureren van deze eigenschap in CustomSettings.ini.  

> [!NOTE]
>  Voor het configureren van deze eigenschap in CustomSettings.ini, u moet deze eigenschap toevoegen aan de **eigenschappen** CustomSettings.ini regel.  

 Zie voor de bijbehorende eigenschappen die worden gebruikt met VHD-bestanden:  

-   **VHDCreateDiffVHD**  

-   **VHDCreateFileName**  

-   **VHDCreateSizeMax**  

-   **VHDCreateType**  

-   **VHDDisks**  

-   **VHDInputVariable**  

-   **VHDOutputVariable**  

-   **VHDTargetDisk**  

|**Geconfigureerd door de eigenschap**|||**De eigenschap is van toepassing op**||  
|-|-|-|-|-|  
|BootStrap.ini|||LTI|\-|  
|CustomSettings.ini|\-||||  
|MDT-DB|||ZTI||  

|**Waarde**|**Beschrijving**|  
|-|-|
|*naam*|De bestandsnaam die kan worden opgegeven met een UNC-pad, lokaal pad, relatief pad of de bestandsnaam. Als de bestandsnaam is opgegeven, klikt u vervolgens MDT gezocht naar het VHD-bestand op de doelcomputer.|  

|**Voorbeeld**|  
|-|  
|`[Settings] Priority=Default  [Default] VHDCreateSizeMax=130048 VHDCreateSource=\\wdg-mdt-01\vhds\win7_template.vhd VHDCreateType=FIXED VHDCreateFileName=Win7_C.vhd VHDInputVariable=VHDTargetDisk`|  

####  <a name="VHDCreateType"></a>VHDCreateType  
 Deze eigenschap wordt gebruikt om op te geven van het type VHD-bestand dat is opgegeven in de **VHDCreateFileName** eigenschap en kan een van de volgende typen van de VHD-bestanden:  

-   **Vaste VHD-bestand**. Voor deze VHD-type, de grootte van de VHD die is opgegeven bij het maken van is toegewezen en wordt niet automatisch gewijzigd na het maken van. Bijvoorbeeld, als u een 24\-gigabyte \(GB\) vaste VHD-bestand, worden het bestand ongeveer 24 GB groot \(met ruimte vrij gebruikt voor de interne structuur van de VHD\) ongeacht hoeveel informatie wordt opgeslagen in het VHD-bestand.  

-   **Dynamisch uitbreidbare VHD-bestand**. Voor dit type VHD wordt slechts een kleine hoeveelheid van de grootte van de VHD die is opgegeven tijdens het maken toegewezen. Vervolgens blijft het VHD-bestand groeien zolang er meer gegevens worden opgeslagen in het. Echter kan niet het VHD-bestand groter dan de grootte die is opgegeven bij het maken van. Bijvoorbeeld, als u een 24 GB dynamisch uitbreidbare VHD maakt, moeten bij het maken van kleine. Echter als informatie wordt opgeslagen in het VHD-bestand, blijft het bestand toenemen, maar nooit overschrijden de maximale grootte van 24 GB.  

 Deze eigenschap is alleen geldig voor het scenario van de nieuwe Computer MDT-implementatie.  

> [!NOTE]
>  De maximale grootte van het VHD-bestand is opgegeven in de **VHDCreateSizeMax** eigenschap.  

 Deze eigenschap wordt meestal ingesteld met behulp van een takenreeksstap gemaakt met behulp van de **virtuele harde schijf maken \(VHD\)**  type takenreeks van de taak. U kunt de waarde overschrijven die de **virtuele harde schijf maken \(VHD\)**  takenreeksstap wordt ingesteld met het configureren van deze eigenschap in CustomSettings.ini.  

> [!NOTE]
>  Voor het configureren van deze eigenschap in CustomSettings.ini, u moet deze eigenschap toevoegen aan de **eigenschappen** CustomSettings.ini regel.  

 Zie voor de bijbehorende eigenschappen die worden gebruikt met VHD-bestanden:  

-   **VHDCreateDiffVHD**  

-   **VHDCreateFileName**  

-   **VHDCreateSizeMax**  

-   **VHDCreateSource**  

-   **VHDDisks**  

-   **VHDInputVariable**  

-   **VHDOutputVariable**  

-   **VHDTargetDisk**  

|**Geconfigureerd door de eigenschap**|||**De eigenschap is van toepassing op**||  
|-|-|-|-|-|  
|BootStrap.ini|||LTI|\-|  
|CustomSettings.ini|\-||||  
|MDT-DB|||ZTI||  

|**Waarde**|**Beschrijving**|  
|-|-|
|**UITBREIDBARE**|Maakt een vaste VHD-bestand|  
|**VASTE**|Hiermee maakt u een dynamisch uitbreidbare VHD-bestand|  

|**Voorbeeld**|  
|-|  
|`[Settings] Priority=Default  [Default] VHDCreateSizeMax=130048 VHDCreateType=EXPANDABLE VHDCreateFileName=Win7_C.vhd VHDInputVariable=VHDTargetDisk`|  

####  <a name="VHDDisks"></a>VHDDisks  
 Deze eigenschap bevat een lijst van de fysieke schijf getallen toegewezen aan de VHD-bestanden die zijn gescheiden door spaties. Elke keer dat een VHD-bestand is gemaakt, MDT wordt de schijfindex van de nieuwe schijf toegevoegd voor het gebruik van deze eigenschap de **Index** eigenschap van de **Win32\_schijfstation** WMI-klasse.  

> [!NOTE]
>  Deze eigenschap wordt dynamisch ingesteld door de MDT-scripts en is niet geconfigureerd in CustomSettings.ini of de MDT-DB. Deze eigenschap behandelen als alleen-lezen.  

 Deze eigenschap wordt meestal ingesteld met behulp van een takenreeksstap gemaakt met behulp van de **virtuele harde schijf maken \(VHD\)**  type takenreeks van de taak. U kunt de waarde overschrijven die de **virtuele harde schijf maken \(VHD\)**  takenreeksstap wordt ingesteld met het configureren van deze eigenschap in CustomSettings.ini.  

> [!NOTE]
>  Voor het configureren van deze eigenschap in CustomSettings.ini, u moet deze eigenschap toevoegen aan de **eigenschappen** CustomSettings.ini regel.  

 Zie voor de bijbehorende eigenschappen die worden gebruikt met VHD-bestanden:  

-   **VHDCreateDiffVHD**  

-   **VHDCreateFileName**  

-   **VHDCreateSizeMax**  

-   **VHDCreateSource**  

-   **VHDCreateType**  

-   **VHDInputVariable**  

-   **VHDOutputVariable**  

-   **VHDTargetDisk**  

|**Geconfigureerd door de eigenschap**|||**De eigenschap is van toepassing op**||  
|-|-|-|-|-|  
|BootStrap.ini|||LTI|\-|  
|CustomSettings.ini|\-||||  
|MDT-DB|||ZTI||  

|**Waarde**|**Beschrijving**|  
|-|-|
|*index1 index2 index3*|Een lijst van de fysieke schijf getallen toegewezen aan de VHD-bestanden, gescheiden door spaties: bijvoorbeeld *1 2 5*.|  

|**Voorbeeld**|  
|-|  
|Geen|  

####  <a name="VHDInputVariable"></a>VHDInputVariable  
 Deze eigenschap bevat een variabele met de schijf op de doelcomputer waar de VHD-bestanden worden gemaakt. MDT maakt de VHD-bestanden in de VHD-map in de hoofdmap van dit station.  

> [!NOTE]
>  Als deze eigenschap wordt weggelaten, wordt de MDT probeert te maken van de VHD-bestanden in de VHD-map in de hoofdmap van het eerste systeemstation.  

 Deze eigenschap wordt meestal ingesteld met behulp van een takenreeksstap gemaakt met behulp van de **virtuele harde schijf maken \(VHD\)**  type takenreeks van de taak. U kunt de waarde overschrijven die de **virtuele harde schijf maken \(VHD\)**  takenreeksstap wordt ingesteld met het configureren van deze eigenschap in CustomSettings.ini.  

> [!NOTE]
>  Voor het configureren van deze eigenschap in CustomSettings.ini, u moet deze eigenschap toevoegen aan de **eigenschappen** CustomSettings.ini regel.  

 Zie voor de bijbehorende eigenschappen die worden gebruikt met VHD-bestanden:  

-   **VHDCreateDiffVHD**  

-   **VHDCreateFileName**  

-   **VHDCreateSizeMax**  

-   **VHDCreateSource**  

-   **VHDCreateType**  

-   **VHDDrives**  

-   **VHDOutputVariable**  

-   **VHDTargetDisk**  

|**Geconfigureerd door de eigenschap**|||**De eigenschap is van toepassing op**||  
|-|-|-|-|-|  
|BootStrap.ini|||LTI|\-|  
|CustomSettings.ini|\-||||  
|MDT-DB|||ZTI||  

|**Waarde**|**Beschrijving**|  
|-|-|
|*variabele*|De variabele met de stationsletter op de doelcomputer waar de VHD-bestanden worden gemaakt. MDT maakt de VHD-bestanden in de VHD-map in de hoofdmap van dit station. Bijvoorbeeld, als deze eigenschap heeft een waarde van **VHDTargetDisk**, wordt de **VHDTargetDisk** eigenschap bevat de stationsletter \(zoals *H*\).|  

|**Voorbeeld**|  
|-|  
|`VHDCreateSizeMax=130048 VHDCreateType=EXPANDABLE VHDCreateFileName=Win7_C.vhd  VHDInputVariable=VHDTargetDisk`|  

####  <a name="VHDOutputVariable"></a>VHDOutputVariable  
 Deze eigenschap bevat een variabele die het aantal fysieke schijf die is toegewezen aan de zojuist gemaakte VHD-bestand bevat. Elke keer dat een VHD-bestand is gemaakt, MDT, wordt deze eigenschap ingesteld op de schijfindex van de nieuwe schijf met behulp van de **Index** eigenschap van de **Win32\_schijfstation** WMI-klasse.  

 Deze eigenschap wordt meestal ingesteld met behulp van een takenreeksstap gemaakt met behulp van de **virtuele harde schijf maken \(VHD\)**  type takenreeks van de taak. U kunt de waarde overschrijven die de **virtuele harde schijf maken \(VHD\)**  takenreeksstap wordt ingesteld met het configureren van deze eigenschap in CustomSettings.ini.  

> [!NOTE]
>  Voor het configureren van deze eigenschap in CustomSettings.ini, u moet deze eigenschap toevoegen aan de **eigenschappen** CustomSettings.ini regel.  

 Zie voor de bijbehorende eigenschappen die worden gebruikt met VHD-bestanden:  

-   **VHDCreateDiffVHD**  

-   **VHDCreateFileName**  

-   **VHDCreateSizeMax**  

-   **VHDCreateSource**  

-   **VHDCreateType**  

-   **VHDDisks**  

-   **VHDInputVariable**  

-   **VHDTargetDisk**  

|**Geconfigureerd door de eigenschap**|||**De eigenschap is van toepassing op**||  
|-|-|-|-|-|  
|BootStrap.ini|||LTI|\-|  
|CustomSettings.ini|\-||||  
|MDT-DB|||ZTI||  

|**Waarde**|**Beschrijving**|  
|-|-|
|*Variabele*|Variabele, wordt het aantal fysieke schijf is toegewezen aan de zojuist gemaakte VHD-bestand bevat. Bijvoorbeeld, als deze eigenschap heeft een waarde van **OSDDiskIndex**, wordt de **OSDDiskIndex** eigenschap bevat het aantal fysieke schijf is toegewezen aan de zojuist gemaakte VHD-bestand \(zoals *4*\).|  

|**Voorbeeld**|  
|-|  
|Geen|  

####  <a name="VHDTargetDisk"></a>VHDTargetDisk  
 Hiermee geeft u het station op de doelcomputer waar de VHD is gemaakt. Deze eigenschap later wordt verwezen de [VHDInputVariable](#VHDInputVariable) eigenschap.  

> [!NOTE]
>  Deze eigenschap wordt dynamisch ingesteld door de MDT-scripts en is niet geconfigureerd in CustomSettings.ini of de MDT-DB. Deze eigenschap behandelen als alleen-lezen.  

 Zie voor de bijbehorende eigenschappen die worden gebruikt met VHD-bestanden:  

-   **VHDCreateDiffVHD**  

-   **VHDCreateFileName**  

-   **VHDCreateSizeMax**  

-   **VHDCreateSource**  

-   **VHDCreateType**  

-   **VHDDisks**  

-   **VHDInputVariable**  

-   **VHDOutputVariable**  

|**Geconfigureerd door de eigenschap**|||**De eigenschap is van toepassing op**||  
|-|-|-|-|-|  
|BootStrap.ini|||LTI|\-|  
|CustomSettings.ini|||||  
|MDT-DB|||ZTI||  

|**Waarde**|**Beschrijving**|  
|-|-|
|*Schijf*|Hiermee geeft u het station waar de VHD is gemaakt|  

|**Voorbeeld**|  
|-|  
|Geen|  

####  <a name="VMHost"></a>VMHost  
 Geeft de naam van de Hyper\-V-host met de virtuele machine waarop MDT wordt uitgevoerd. Deze eigenschap is alleen beschikbaar wanneer de Hyper\-integratieonderdelen V zijn geïnstalleerd en actief.  

> [!NOTE]
>  Deze eigenschap wordt dynamisch ingesteld door de MDT-scripts en is niet geconfigureerd in CustomSettings.ini of de MDT-DB. Deze eigenschap behandelen als alleen-lezen.  

Tabel 4 vermeldt de Windows-besturingssystemen die MDT ondersteunt en hun bijbehorende Hyper\-integratieonderdelen V ondersteunen.  

### <a name="table-4-windows-operating-systems-and-hyper-v-integration-components-support"></a>Tabel 4. Windows-besturingssystemen en ondersteuning voor Hyper-V-integratie-onderdelen  

|**Besturingssysteem**|**Onderdelen voor Hyper-V-integratie**|  
|-|-|  
|Windows PE|Integratieonderdelen zijn niet beschikbaar.|  
|Windows 7|Standaard beschikbaar in de edities Enterprise, Ultimate en Professional.|  
|Windows Server 2008 R2|Standaard beschikbaar in alle edities.|  

|**Geconfigureerd door de eigenschap**|||**De eigenschap is van toepassing op**||  
|-|-|-|-|-|  
|BootStrap.ini|||LTI|-|  
|CustomSettings.ini|||||  
|MDT-DB|||ZTI|-|  

|**Waarde**|**Beschrijving**|  
|-|-|
|*Naam*|De naam van de Hyper-V-host met de virtuele machine waarop MDT wordt uitgevoerd|  

|**Voorbeeld**|  
|-|  
|Geen|  

####  <a name="VMName"></a>VMName  
 Geeft de naam van de virtuele machine waarop MDT wordt uitgevoerd. Deze eigenschap is alleen beschikbaar wanneer de Hyper-V-integratie-onderdelen zijn geïnstalleerd en worden uitgevoerd.  

 Tabel 5 geeft een lijst van de Windows-besturingssystemen wordt ondersteund door de MDT en hun bijbehorende integratieonderdelen Hyper-V-ondersteuning.  

> [!NOTE]
>  Deze eigenschap wordt dynamisch ingesteld door de MDT-scripts en is niet geconfigureerd in CustomSettings.ini of de MDT-DB. Deze eigenschap behandelen als alleen-lezen.  

### <a name="table-5-windows-operating-systems-and-hyper-v-integration-components-support"></a>Tabel 5. Windows-besturingssystemen en ondersteuning voor Hyper-V-integratie-onderdelen  

|**Besturingssysteem**|**Onderdelen voor Hyper-V-integratie**|  
|-|-|  
|Windows PE|Integratieonderdelen zijn niet beschikbaar.|  
|Windows 7|Standaard beschikbaar in de edities Enterprise, Ultimate en Professional.|  
|Windows Server 2008 R2|Standaard beschikbaar in alle edities.|  

|**Geconfigureerd door de eigenschap**|||**De eigenschap is van toepassing op**||  
|-|-|-|-|-|  
|BootStrap.ini|||LTI|-|  
|CustomSettings.ini|||||  
|MDT-DB|||ZTI|-|  

|**Waarde**|**Beschrijving**|  
|-|-|
|*naam*|De naam van de virtuele machine waarop MDT wordt uitgevoerd|  

|**Voorbeeld**|  
|-|  
|Geen|  

####  <a name="VMPlatform"></a>VMPlatform  
 Hiermee geeft u specifieke informatie over de virtualisatieomgeving voor de doelcomputer wanneer de doelcomputer een virtuele machine. Het VM-platform wordt bepaald met behulp van WMI.  

> [!NOTE]
>  Deze eigenschap wordt dynamisch ingesteld door de MDT-scripts en is niet geconfigureerd in CustomSettings.ini of de MDT-DB. Deze eigenschap behandelen als alleen-lezen.  

|**Geconfigureerd door de eigenschap**|||**De eigenschap is van toepassing op**||  
|-|-|-|-|-|  
|BootStrap.ini|||LTI|-|  
|CustomSettings.ini|||||  
|MDT-DB|||ZTI|-|  

|**Waarde**|**Beschrijving**|  
|-|-|
|**Hyper-V**|Hyper-V|  
|**VirtualBox**|Virtuele vak|  
|**VMware**|Virtualisatieplatform voor VMware|  
|**Xen**|Citrix Xen-Server|  

|**Voorbeeld**|  
|-|  
|Geen|  

####  <a name="VRefresh"></a>VRefresh  
 De verticale vernieuwingsfrequentie voor de monitor op de doelcomputer. De verticale vernieuwingsfrequentie is opgegeven in Hertz. In het voorbeeld wordt de waarde **60** geeft aan dat de verticale vernieuwingsfrequentie van de monitor 60 Hz. Deze waarde wordt ingevoegd in de juiste configuratie-instellingen in Unattend.xml.  

> [!NOTE]
>  De standaardwaarden (in het bestand Unattend.xml-sjabloon) zijn horizontale resolutie van 1024 pixels, verticale resolutie van 768 pixels, 32-bits kleurdiepte en 60 Hz verticale vernieuwingsfrequentie.  

|**Geconfigureerd door de eigenschap**|||**De eigenschap is van toepassing op**||  
|-|-|-|-|-|  
|BootStrap.ini|||LTI|-|  
|CustomSettings.ini|-||||  
|MDT-DB|-||ZTI|-|  

|**Waarde**|**Beschrijving**|  
|-|-|
|*refresh_rate*|De verticale vernieuwingsfrequentie voor de monitor op de doelcomputer in Hertz|  

|**Voorbeeld**|  
|-|  
|`[Settings] Priority=Default  [Default] BitsPerPel=32 VRefresh=60 XResolution=1024 YResolution=768`|  

####  <a name="VSSMaxSize"></a>VSSMaxSize  
 Deze eigenschap wordt gebruikt om een waarde voor de **maxsize** parameter van de **vssadmin vergroten of verkleinen shadowstorage** opdracht in de **Vssadmin** opdracht. De **maxsize** parameter wordt gebruikt om de maximale hoeveelheid ruimte op het doelvolume die kan worden gebruikt voor het opslaan van schaduwkopieën. Voor meer informatie over de **maxsize** parameter, Zie [Vssadmin vergroten of verkleinen shadowstorage](http://technet.microsoft.com/library/cc788050\(WS.10\).aspx).  

|**Geconfigureerd door de eigenschap**|||**De eigenschap is van toepassing op**||  
|-|-|-|-|-|  
|BootStrap.ini|||LTI|-|  
|CustomSettings.ini|-||||  
|MDT-DB|-||ZTI|-|  

|**Waarde**|**Beschrijving**|  
|-|-|
|*maxsize_value*|Hiermee geeft u de maximale hoeveelheid ruimte die kan worden gebruikt voor het opslaan van schaduwkopieën. De waarde kan worden opgegeven in bytes, of als een percentage van het doelvolume.<br /><br /> De waarde kan opgeven:<br /><br /> -De waarde moet in bytes, 300 MB of hoger en accepteer de volgende achtervoegsels: KB, MB, GB, TB, PB en EB. U kunt ook B, K, M, G, T, P, E gebruiken als achtervoegsels, bijvoorbeeld:<br /><br /> `VSSMaxSize=60G`<br /><br /> -Als percentage, het teken % als de numerieke waarde in het achtervoegsel te gebruiken, bijvoorbeeld:<br /><br /> `VSSMaxSize=20%`<br /><br /> Opmerking:<br /><br /> Als een achtervoegsel wordt niet geleverd, is het standaardachtervoegsel bytes. Bijvoorbeeld: `VSSMaxSize=1024` geeft aan dat de **VSSMaxSize** wordt ingesteld op 1024 bytes.<br /><br /> Als de waarde is ingesteld op **UNBOUNDED**, vervolgens is er geen limiet geplaatst op de hoeveelheid opslagruimte die kan worden gebruikt, bijvoorbeeld:<br /><br /> `VSSMaxSize=UNBOUNDED`|  

|**Voorbeeld**|  
|-|  
|`[Settings] Priority=Default  [Default] VSSMaxSize=25%`|  

####  <a name="WDSServer"></a>WDSServer  
 De computer met Windows Deployment Services die wordt gebruikt voor het installeren van installatiekopieën van Windows Deployment Services. De standaardwaarde is de server met Windows Deployment Services van waaruit u de installatiekopie is gestart.  

> [!NOTE]
>  Deze eigenschap wordt dynamisch ingesteld door de MDT-scripts en is niet geconfigureerd in CustomSettings.ini of de MDT-DB. Deze eigenschap behandelen als alleen-lezen.  

|**Geconfigureerd door de eigenschap**|||**De eigenschap is van toepassing op**||  
|-|-|-|-|-|  
|BootStrap.ini|||LTI|-|  
|CustomSettings.ini|||||  
|MDT-DB|||ZTI||  

|**Waarde**|**Beschrijving**|  
|-|-|
|*WDS_server*|De naam van de computer met Windows Deployment Services|  

|**Voorbeeld**|  
|-|  
|Geen|  

####  <a name="WindowsSource"></a>WindowsSource  
 Deze eigenschap wordt gebruikt om in te stellen van de locatie van de map sources\sxs in een gedeelde netwerkmap waarin de bronbestanden van het besturingssysteem van MDT. Deze eigenschap wordt gebruikt wanneer:  

-   MDT is een aangepaste takenreeks wordt uitgevoerd of implementeren van een aangepaste installatiekopie  

-   MDT installeren functies of onderdelen in Windows 8 en Windows Server 2012  

-   De computer heeft geen toegang tot het Internet  

 Als de situatie wordt beschreven in de bovenstaande lijst met opsommingstekens vindt plaats, MDT kan mogelijk geen lokaal bronbestanden van het besturingssysteem vinden en de installatie zal proberen de bestanden te downloaden vanaf Internet. Omdat de computer geen toegang tot Internet heeft, mislukt het proces. Als u deze eigenschap instelt op de juiste waarde helpt voorkomen dat dit probleem optreedt.  

|**Geconfigureerd door de eigenschap**|||**De eigenschap is van toepassing op**||  
|-|-|-|-|-|  
|BootStrap.ini|||LTI|-|  
|CustomSettings.ini|-||||  
|MDT-DB|||ZTI|-|  

|**Waarde**|**Beschrijving**|  
|-|-|
|***folder_unc***|Een UNC-pad naar de map Sources\sxs voor het besturingssysteem wordt geïmplementeerd.<br /><br /> Opmerking:<br /><br /> Het UNC-pad moet de map Sources\sxs bevatten.|  

|**Voorbeeld**|  
|-|  
|`[Settings] Priority=Default  [Default] WindowsSource=%DeployRoot%\Operating Systems\Windows 8\Sources\sxs`|  

####  <a name="WipeDisk"></a>WipeDisk  
 Hiermee geeft u op of de schijf moet worden gewist. Als **WipeDisk** TRUE, wordt het script ZTIWipeDisk.wsf wordt schoon de schijf met behulp van de **indeling** opdracht. De **indeling** opdracht is niet de meest 'veilige' manier om de schijf wissen.  

 Veilig wissen van de schijf moet worden gedaan op een manier die volgt op de Verenigde Staten Ministerie van defensie standaard 5220.22-M, waarin wordt vermeld, ' om te wissen magnetische schijven overschrijven alle locaties driemaal (eerst met een teken, tweede keer met de aanvulling en de derde tijd met een willekeurige tekenreeks). '  

 Wanneer MDT de schijf tussen, gebruikt de **indeling** opdracht met de **/P:3** overschakelen, die Hiermee geeft u **indeling** op nul alle sectoren op het volume en drie van de bewerking uit te voeren tijden. Er is geen vast te stellen de **indeling** opdracht gebruikmaakt van een bepaald teken of een willekeurig teken.  

> [!NOTE]
>  Als de schijf moet veilig worden gewist, een niet-Microsoft-beveiligde schijf wissen hulpprogramma moet worden toegevoegd aan de taak reeks met behulp van de **opdrachtregel uitvoeren** takenreeksstap.  

> [!CAUTION]
>  Waarde van deze eigenschap moet in hoofdletters worden opgegeven zodat de implementatiescripts kunnen correct worden gelezen.  

|**Geconfigureerd door de eigenschap**|||**De eigenschap is van toepassing op**||  
|-|-|-|-|-|  
|BootStrap.ini|||LTI|-|  
|CustomSettings.ini|-||||  
|MDT-DB|-||ZTI|-|  

|**Waarde**|**Beschrijving**|  
|-|-|
|**DE WAARDE TRUE**|Als **WipeDisk** is ingesteld op **TRUE**, de Win32_DiskPartition op DiskIndex 0 en 0-Index wordt geformatteerd.|  
|**DE WAARDE FALSE**|De schijf niet geformatteerd.|  

|**Voorbeeld**|  
|-|  
|`[Settings] Priority=Default  [Default] WipeDisk=TRUE`|  

####  <a name="WizardSelectionProfile"></a>WizardSelectionProfile  
 De profielnaam die wordt gebruikt door de wizard voor het filteren van de weergave van verschillende items.  

|**Geconfigureerd door de eigenschap**|||**De eigenschap is van toepassing op**||  
|-|-|-|-|-|  
|BootStrap.ini|||LTI|-|  
|CustomSettings.ini|-||||  
|MDT-DB|-||ZTI||  

|**Waarde**|**Beschrijving**|  
|-|-|
|*Profielnaam*|Profielnaam die wordt gebruikt door de wizard voor het filteren van de weergave van verschillende items|  

|**Voorbeeld**|  
|-|  
|`[Settings] Priority=Default  [Default] WizardSelectionProfile=SelectTaskSequenceOnly`|  

####  <a name="WSUSServer"></a>WSUSServer  
 Dit is de naam van de Windows Server Update Services (WSUS)-server die de doelcomputer moet worden gebruikt bij het scannen op, downloaden en installeren van updates.  

 Zie voor meer informatie over welke script maakt gebruik van deze eigenschap [ZTIWindowsUpdate.wsf](#ZTIWindowsUpdate.wsf).  

|**Geconfigureerd door de eigenschap**|||**De eigenschap is van toepassing op**||  
|-|-|-|-|-|  
|BootStrap.ini|||LTI|-|  
|CustomSettings.ini|-||||  
|MDT-DB|-||ZTI|-|  

|**Waarde**|**Beschrijving**|  
|-|-|
|*servernaam*|De naam van de WSUS-server opgegeven in de HTTP-indeling|  

|**Voorbeeld**|  
|-|  
|`[Settings] Priority=Default  [Default] WSUSServer=http://WSUSServerName[Settings] Priority=Default  [Default] WSUSServer=http://WSUSServerName`|  

####  <a name="WUMU_ExcludeKB"></a>WUMU_ExcludeKB  
 De lijst met software-updates voor Windows Update of Microsoft Update te negeren (door de bijbehorende Knowledge Base-artikelen).  

 Leden van het projectteam implementatie wilt regelmaat op de lijst met updates worden geïnstalleerd door het script ZTIWindowsUpdate.wsf om te controleren dat elke update voldoet aan de behoeften en de verwachtingen van het project. Alle updates zijn geregistreerd en worden vastgelegd in het bestand ZTIWindowsUpdate.log, dat wordt gegenereerd tijdens de implementatie. Elke update wordt de status ervan als installeren of OVERSLAAN en ziet u de update-id, de naam van de update en de QNumber die zijn gekoppeld aan elke update aangegeven. Als een update worden uitgesloten moet, kan deze update moet worden toegevoegd aan het CustomSettings.ini-bestand (voor implementaties van LTI).  

|**Geconfigureerd door de eigenschap**|||**De eigenschap is van toepassing op**||  
|-|-|-|-|-|  
|BootStrap.ini|||LTI|-|  
|CustomSettings.ini|-||||  
|MDT-DB|||ZTI||  

|**Waarde**|**Beschrijving**|  
|-|-|
|*WUMU_ExcludeKB*|De lijst met software-updates voor Windows Update of Microsoft Update te negeren door QNumber|  

|**Voorbeeld**|  
|-|  
|`[Settings] Priority=Default  [Default] WUMU_ExcludeKB1=925471`|  

#### <a name="wumuexcludeid"></a>WUMU_ExcludeID  
 De lijst met software-updates Windows Update of Microsoft Update te negeren (door de bijbehorende update-ID).  

 Leden van het projectteam implementatie wilt regelmaat op de lijst met updates worden geïnstalleerd door het script ZTIWindowsUpdate.wsf om te controleren dat elke update voldoet aan de behoeften en de verwachtingen van het project. Alle updates zijn geregistreerd en worden vastgelegd in het bestand ZTIWindowsUpdate.log, dat wordt gegenereerd tijdens de implementatie. Elke update wordt de status ervan als installeren of OVERSLAAN en ziet u de update-id, de naam van de update en de QNumber die zijn gekoppeld aan elke update aangegeven. Als een update moet worden uitgesloten, kan deze update moet worden toegevoegd aan het CustomSettings.ini-bestand (voor implementaties van LTI).  

 Als de installatie van hulpprogramma voor verwijderen van schadelijke Software moet worden uitgesloten, opzoeken van de regel in de ZTIWindowsUpdate.log die laat zien waar de update is geïdentificeerd en geïnstalleerd en selecteer vervolgens het update-id-nummer. Het update-id-nummer voor hulpprogramma voor verwijderen van schadelijke Software is bijvoorbeeld adbe6425-6560-4 d 40-9478-1e35b3cdab4f.  

|**Geconfigureerd door de eigenschap**|||**De eigenschap is van toepassing op**||  
|-|-|-|-|-|  
|BootStrap.ini|||LTI|-|  
|CustomSettings.ini|-||||  
|MDT-DB|||ZTI||  

|**Waarde**|**Beschrijving**|  
|-|-|
|*WUMU_ExcludeID*|De lijst met software-updates voor Windows Update of Microsoft Update te negeren door UpdateID getal|  

|**Voorbeeld**|  
|-|  
|`[Settings] Priority=Default  [Default] WUMU_ExcludeID1={adbe6425-6560-4d40-9478-1e35b3cdab4f}[Settings] Priority=Default  [Default] WUMU_ExcludeID1={adbe6425-6560-4d40-9478-1e35b3cdab4f}`|  

####  <a name="XResolution"></a>XResolution  
 De horizontale resolutie van de monitor op de doelcomputer, opgegeven in pixels. In het voorbeeld wordt de waarde **1024** geeft de horizontale resolutie van de monitor is 1024 pixels. Deze waarde wordt ingevoegd in de juiste configuratie-instellingen in Unattend.xml.  

> [!NOTE]
>  De standaardwaarden (in het bestand Unattend.xml-sjabloon) zijn horizontale resolutie van 1024 pixels, verticale resolutie van 768 pixels, 32-bits kleurdiepte en 60 Hz verticale vernieuwingsfrequentie.  

|**Geconfigureerd door de eigenschap**|||**De eigenschap is van toepassing op**||  
|-|-|-|-|-|  
|BootStrap.ini|||LTI|-|  
|CustomSettings.ini|-||||  
|MDT-DB|-||ZTI|-|  

|**Waarde**|**Beschrijving**|  
|-|-|
|*horizontal_resolution*|De horizontale resolutie van de monitor op de doelcomputer in pixels|  

|**Voorbeeld**|  
|-|  
|`[Settings] Priority=Default  [Default] BitsPerPel=32 VRefresh=60 XResolution=1024 YResolution=768[Settings] Priority=Default  [Default] BitsPerPel=32 VRefresh=60 XResolution=1024 YResolution=768`|  

####  <a name="YResolution"></a>YResolution  
 De verticale resolutie van de monitor op de doelcomputer, opgegeven in pixels. In het voorbeeld wordt de waarde **768** geeft de verticale resolutie van de monitor is 768 pixels. Deze waarde wordt ingevoegd in de juiste configuratie-instellingen in Unattend.xml.  

> [!NOTE]
>  De standaardwaarden (in het bestand Unattend.xml-sjabloon) zijn horizontale resolutie van 1024 pixels, verticale resolutie van 768 pixels, 32-bits kleurdiepte en 60 Hz verticale vernieuwingsfrequentie.  

|**Geconfigureerd door de eigenschap**|||**De eigenschap is van toepassing op**||  
|-|-|-|-|-|  
|BootStrap.ini|||LTI|-|  
|CustomSettings.ini|-||||  
|MDT-DB|-||ZTI|-|  

|**Waarde**|**Beschrijving**|  
|-|-|
|*vertical_resolution*|De verticale resolutie van de monitor op de doelcomputer in pixels|  

|**Voorbeeld**|  
|-|  
|`[Settings] Priority=Default  [Default] BitsPerPel=32 VRefresh=60 XResolution=1024 YResolution=768[Settings] Priority=Default  [Default] BitsPerPel=32 VRefresh=60 XResolution=1024 YResolution=768`|  

###  <a name="ProvidingPropertiesforSkippedDeploymentWizardPages"></a>Eigenschappen bieden voor implementatie van overgeslagen wizardpagina 's  
 Tabel 6 geeft een lijst van de afzonderlijke pagina's van Wizard implementatie van de eigenschap over te slaan van de bijbehorende wizardpagina en de eigenschappen die moeten worden geconfigureerd wanneer de pagina van de wizard wordt overgeslagen.  

 Als de **SkipWizard** eigenschap wordt gebruikt om alle pagina's van de Wizard implementatie overslaan, bieden alle eigenschappen in de **configureren van deze eigenschappen**kolom. Voor voorbeelden van verschillende scenario's waarbij implementatie wizardpagina's overgeslagen, Zie de sectie 'Volledig geautomatiseerd LTI implementatiescenario' in de MDT-document *Microsoft Deployment Toolkit voorbeelden Guide*.  

> [!NOTE]
>  In gevallen waar de **configuratie van deze eigenschappen** kolom leeg is, er zijn geen eigenschappen moeten worden geconfigureerd wanneer de bijbehorende wizardpagina wordt overgeslagen.  

### <a name="table-6-deployment-wizard-pages"></a>Tabel 6. Wizardpagina's voor implementatie  

|**Deze wizardpagina overslaan**|**Gebruik van deze eigenschap**|**Deze eigenschappen configureren**|  
|-|-|-|  
|**Welkom**|SkipBDDWelcome||  
|**Geef referenties op voor het verbinden met netwerkshares**|Dankzij de eigenschappen in de volgende kolom wordt overgeslagen|-Gebruikers-id<br /><br /> -UserDomain<br /><br /> -UserPassword|  
|**Takenreeks**|SkipTaskSequence|-TaskSequenceID|  
|**Computerdetails**|SkipComputerName,<br /><br /> SkipDomainMembership|-OSDComputerName<br /><br /> -JoinWorkgroup kan<br /><br /> – of –<br /><br /> -JoinDomain<br /><br /> -DomainAdmin|  
|**Gebruikersgegevens**|SkipUserData|-UDDir<br /><br /> -UDShare<br /><br /> -UserDataLocation|  
|**Verplaatsen van gegevens en instellingen**|SkipUserData|-UDDir<br /><br /> -UDShare<br /><br /> -UserDataLocation|  
|**User Data (herstel)**|SkipUserData|-UDDir<br /><br /> -UDShare<br /><br /> -UserDataLocation|  
|**Back-up**|SkipComputerBackup|-Back-upmap<br /><br /> -BackupShare<br /><br /> -ComputerBackupLocation|  
|**Productcode**|SkipProductKey|-ProductKey<br /><br /> – of –<br /><br /> -OverrideProductKey|  
|**Taalpakketten**|SkipPackageDisplay|LanguagePacks|  
|**De landinstelling en -tijd**|SkipLocaleSelection, SkipTimeZone|-KeyboardLocale<br /><br /> -UserLocale<br /><br /> -UILanguage<br /><br /> -TimeZoneName|  
|**Functies en onderdelen**|SkipRoles|-OSRoles<br /><br /> -OSRoleServices<br /><br /> -OSFeatures|  
|**Toepassingen**|SkipApplications|Toepassingen|  
|**Administrator-wachtwoord**|SkipAdminPassword|adminPassword|  
|**Lokale beheerders**|SkipAdminAccounts|-Beheerders|  
|**Installatiekopie vastleggen**|SkipCapture|-ComputerBackupLocation|  
|**BitLocker**|SkipBitLocker|-BDEDriveLetter<br /><br /> -BDEDriveSize<br /><br /> -BDEInstall<br /><br /> -BDEInstallSuppress<br /><br /> -BDERecoveryKey<br /><br /> -TPMOwnerPassword<br /><br /> -OSDBitLockerStartupKeyDrive<br /><br /> -OSDBitLockerWaitForEncryption|  
|**Gereed om te beginnen**|SkipSummary|:|  
|**Implementatie van besturingssysteem is voltooid**|SkipFinalSummary|:|  
|**Implementatie van besturingssysteem is niet voltooid**|SkipFinalSummary|:|  

##  <a name="Scripts"></a>Scripts  
 De scripts gebruikt in implementaties van LTI en ZTI verwijzingseigenschappen die bepalen de processtappen en configuratie-instellingen gebruikt tijdens de implementatie. Deze sectie gebruiken om u te helpen bij het bepalen van de juiste scripts moeten worden opgenomen in de acties en de geldige argumenten op te geven wanneer elk script wordt uitgevoerd. De volgende informatie is bedoeld voor elk script:  

-   **Naam**. Hiermee geeft u de naam van het script.  

-   **Beschrijving**. Bevat een beschrijving van het doel van het script en eventuele relevante informatie met betrekking tot script aanpassing.  

-   **Invoer**. Hiermee geeft u de bestanden die worden gebruikt voor invoer aan het script.  

-   **Uitvoer**. Hiermee geeft u de bestanden gemaakt of gewijzigd door het script.  

-   **Verwijzingen**. Geeft aan andere scripts of configuratiebestanden waarnaar wordt verwezen door het script.  

-   **Locatie**. Hiermee geeft u de map waar het script kan worden gevonden. De informatie voor de locatie in worden de volgende variabelen gebruikt:  

    -   **program_files**. Deze variabele verwijst naar de locatie van de map Program Files op de computer waarop de MDT is geïnstalleerd.  

    -   **distributie**. Deze variabele verwijst naar de locatie van de distributie-map voor de implementatieshare.  

    -   **Platform**. Deze variabele is een tijdelijke aanduiding voor het platform van het besturingssysteem (x86 of x64).  

-   **Gebruik**. Biedt de opdrachten en opties die u kunt opgeven.  

-   **Argumenten en een beschrijving**. De geldige argumenten worden opgegeven voor het script en een korte beschrijving van wat elk argument betekent aangeven.  

-   **Eigenschappen**. De eigenschappen waarnaar wordt verwezen door het script.  

###  <a name="BDD_Autorun.wsf"></a>BDD_Autorun.wsf  
 Dit script geeft een dialoogvenster waarmee wordt aangegeven door het proces MDT (zoals een opstartbare DVD of een verwisselbare harde schijf) gemaakt media voor de implementatie van de gebruiker geplaatst. Het bericht wordt weergegeven voor 15 seconden. Als er geen actie ondernomen, begint het script LiteTouch.vbs.  

 Zie het onderwerp in voor meer informatie over LiteTouch.vbs [Scripts](#Scripts).  

|**Waarde**|**Beschrijving**|  
|-|-|
|**Invoer**|**Omgevingsvariabelen**. Bevat de eigenschapswaarden, waarden voor aangepaste eigenschappen databaseverbindingen, regels voor implementatie en andere informatie vereist door de scripts voor het voltooien van het implementatieproces|  
|**Uitvoer**|Geen|  
|**Verwijzingen**|**LiteTouch.vbs**. Initieert LTI|  
|**Locatie**|*distributie*\Scripts|  
|**Gebruik**|Geen|  

#### <a name="arguments"></a>Argumenten  

|**Waarde**|**Beschrijving**|  
|-|-|
|Geen|Geen|  

#### <a name="properties"></a>Eigenschappen  

|**Naam**|**Lezen**|**Schrijven**|  
|-|-|-|  
|Geen|||  

###  <a name="BDD_Welcome_ENU.xml"></a>BDD_Welcome_ENU.XML  
 Dit XML-bestand bevat de scriptcode en HTML-indeling voor de **Welkom bij de implementatie van Windows** pagina die wordt weergegeven aan het begin van de Wizard implementatie. Dit XML-bestand wordt gelezen door Wizard.hta die wordt uitgevoerd de wizardpagina's die in dit XML-bestand zijn ingesloten.  

|**Waarde**|**Beschrijving**|  
|-|-|
|**Invoer**|Geen|  
|**Uitvoer**|Geen|  
|**Verwijzingen**|- **NICSettings_Definition_ENU.xml**. Kan de gebruiker configuratie-instellingen voor netwerkadapters bieden<br /><br /> - **Wizard.hta**. Geeft de Wizard implementatie van pagina 's<br /><br /> - **WPEUtil.exe**. Initialiseert de Windows PE en netwerkverbindingen; initieert LTI|  
|**Locatie**|*distributie*\Tools\\*platform*|  
|**Gebruik**|`mshta.exeWizard.hta BDD_Welcome_ENU.xml`|  

#### <a name="arguments"></a>Argumenten  

|**Waarde**|**Beschrijving**|  
|-|-|
|Geen|Geen|  

#### <a name="properties"></a>Eigenschappen  

|**Naam**|**Lezen**|**Schrijven**|  
|-|-|-|  
|**KeyboardLocalePE**|-||  
|**WelcomeWizardCommand**||-|  
|**WizardComplete**||-|  

###  <a name="Credentials_ENU.xml"></a>Credentials_ENU.XML  
 Dit XML-bestand bevat de scriptcode en HTML-indeling voor de **Geef referenties op voor het verbinden met netwerkshares** pagina in de Wizard implementatie van de wizard. Dit XML-bestand wordt gelezen door Wizard.hta die wordt uitgevoerd de wizardpagina's die in dit XML-bestand zijn ingesloten.  

> [!NOTE]
>  Deze pagina van de wizard wordt alleen weergegeven als er een fout opgetreden tijdens het valideren van de vooraf gedefinieerde gebruikersreferenties.  

|**Waarde**|**Beschrijving**|  
|-|-|
|**Invoer**|Geen|  
|**Uitvoer**|Geen|  
|**Verwijzingen**|**Credentials_scripts.vbs**. Bevat gebruikersfuncties referentie-ondersteuning|  
|**Locatie**|*distributie*\Scripts|  
|**Gebruik**|`mshta.exe Wizard.hta /NotWizard /definition:Credentials_ENU.xml [/ValidateAgainstDomain:domain &#124; /ValidateAgainstUNCPath:uncpath]  </DoNotSave> </LeaveShareOpen>`|  

#### <a name="arguments"></a>Argumenten  

|**Waarde**|**Beschrijving**|  
|-|-|
|Geen|Geen|  

#### <a name="properties"></a>Eigenschappen  

|**Naam**|**Lezen**|**Schrijven**|  
|-|-|-|  
|Geen|||  

###  <a name="Credentials_scripts.vbs"></a>Credentials_scripts.vbs  
 Dit script parseert de argumenten die zijn opgegeven bij het laden van het bestand Credentials_ENU.xml in de Wizard implementatie. Validatie van de gebruiker referenties worden ook uitgevoerd. Dit script wordt gelezen door het bestand Credentials_ENU.xml.  

 Zie het onderwerp in voor meer informatie over Credentials_ENU.xml [Scripts](#Scripts).  

|**Waarde**|**Beschrijving**|  
|-|-|
|**Invoer**|Geen|  
|**Uitvoer**|Gebeurtenisbericht naar deze logboekbestanden geschreven:<br /><br /> - **Credentials_scripts.log**. Logboekbestand met gebeurtenissen die worden gegenereerd door dit script<br /><br /> - **BDD.log**. Logboekbestand met gebeurtenissen die worden gegenereerd door alle MDT-scripts|  
|**Verwijzingen**|Geen|  
|**Locatie**|*distributie*\Scripts|  
|**Gebruik**|`<script language="VBScript" src="Credentials_scripts.vbs"/>`|  

#### <a name="arguments"></a>Argumenten  

|**Waarde**|**Beschrijving**|  
|-|-|
|Geen|Geen|  

#### <a name="properties"></a>Eigenschappen  

|**Naam**|**Lezen**|**Schrijven**|  
|-|-|-|  
|**UserCredentials**||-|  
|**UserDomain**|-||  

###  <a name="DeployWiz_Definition_ENU.xml"></a>DeployWiz_Definition_ENU.xml  
 Dit XML-bestand bevat de scriptcode en HTML-indeling voor elke pagina van de wizard in de Wizard implementatie. Dit bestand wordt gelezen door Wizard.hta die wordt uitgevoerd de wizardpagina's die in dit XML-bestand zijn ingesloten. Dit XML-bestand bevat de volgende wizardpagina's:  

-   **Welkom**  

-   **Geef referenties op voor het verbinden met netwerkshares**  

-   **Takenreeks**  

-   **Computerdetails**  

-   **Gebruikersgegevens**  

-   **Verplaatsen van gegevens en instellingen**  

-   **User Data (herstel)**  

-   **Back-up**  

-   **Productcode**  

-   **Taalpakketten**  

-   **De landinstelling en -tijd**  

-   **Functies en onderdelen**  

-   **Toepassingen**  

-   **Administrator-wachtwoord**  

-   **Lokale beheerders**  

-   **Installatiekopie vastleggen**  

-   **BitLocker**  

-   **Gereed om te beginnen**  

|**Waarde**|**Beschrijving**|  
|-|-|
|**Invoer**|Geen|  
|**Uitvoer**|Geen|  
|**Verwijzingen**|- **DeployWiz_Initialization.vbs**. Ondersteunende functies en subroutines gebruikt door het script bevat<br /><br /> - **DeployWiz_Validation.vbs**. Ondersteunende functies en subroutines gebruikt door het script bevat<br /><br /> - **ZTIBackup.wsf**. Hiermee maakt u een back-up van de doelcomputer<br /><br /> - **ZTIPatches.wsf**. Updates zijn geïnstalleerd (taalpakketten, beveiligingsupdates, enzovoort)<br /><br /> - **ZTIUserState.wsf**. Initialiseert de migratie van gebruikersstatus vastleggen en herstellen van gebruikersstatus op de doelcomputer|  
|**Locatie**|*distributie*\Scripts|  
|**Gebruik**|Geen|  

#### <a name="arguments"></a>Argumenten  

|**Waarde**|**Beschrijving**|  
|-|-|
|Geen|Geen|  

#### <a name="properties"></a>Eigenschappen  

|**Naam**|**Lezen**|**Schrijven**|  
|-|-|-|  
|**DeploymentMethod**|-||  
|**DeploymentType**|-||  
|**DoCapture**|-||  
|**ImageBuild**|-||  
|**ImageFlags**|-||  
|**IsBDE**|-||  
|**IsServerOS**|-||  
|**JoinDomain**|-||  
|**OSDComputerName**|-||  
|**OSVersion**|-||  
|**SkipAdminAccounts**|-||  
|**SkipAdminPassword**|-||  
|**SkipApplications**|-||  
|**SkipBitLocker**|-||  
|**SkipCapture**|-||  
|**SkipComputerBackup**|-||  
|**SkipComputerName**|-||  
|**SkipDomainMembership**|-||  
|**SkipLocaleSelection**|-||  
|**SkipPackageDisplay**|-||  
|**SkipProductKey**|-||  
|**SkipRoles**|-||  
|**SkipSummary**|-||  
|**SkipTaskSequence**|-||  
|**SkipTimeZone**|-||  
|**SkipUserData**|-||  
|**TaskSequenceTemplate**|-||  
|**UserDomain**|-||  
|**Gebruikers-id**|-||  
|**UserPassword**|-||  
|**USMTOfflineMigration**|-||  

###  <a name="DeployWiz_Initialization.vbs"></a>DeployWiz_Initialization.vbs  
 Dit script initialiseert de pagina's in de **implementatiewizard** (opgeslagen in [DeployWiz_Definition_ENU.xml](#DeployWiz_Definition_ENU.xml)). Het bevat ook functies en subroutines die de Wizard implementatie tijdens de implementatie van een LTI aanroept.  

|**Waarde**|**Beschrijving**|  
|-|-|
|**Invoer**|- **DomainOUList.xm**l. Bevat een overzicht van domain organisatie-eenheden<br /><br /> - **ListOfLanguages.xml**<br /><br /> - **LocationServer.xml**. Bevat een lijst met beschikbare implementatieshares<br /><br /> - **Omgevingsvariabelen**. Bevat de lijst met waarden van eigenschappen, aangepaste eigenschappen databaseverbindingen, regels voor implementatie en andere informatie die de scripts nodig hebt om het voltooien van het implementatieproces; de omgevingsvariabelen worden ingevuld met ZTIGather.wsf|  
|**Uitvoer**|Gebeurtenisbericht naar deze logboekbestanden geschreven:<br /><br /> - **DeployWiz_Initialization.log**. Logboekbestand met gebeurtenissen die worden gegenereerd door dit script<br /><br /> - **BDD.log**. Logboekbestand met gebeurtenissen die worden gegenereerd door alle MDT-scripts|  
|**Verwijzingen**|**ZTIApplications.wsf**. Start de installatie van toepassing|  
|**Locatie**|*distributie*\Scripts|  
|**Gebruik**|`<script language="VBScript" src="DeployWiz_Initialization.vbs"/>`|  

#### <a name="arguments"></a>Argumenten  

|**Waarde**|**Beschrijving**|  
|-|-|
|Geen|Geen|  

#### <a name="properties"></a>Eigenschappen  

|**Naam**|**Lezen**|**Schrijven**|  
|-|-|-|  
|**Architectuur**|-||  
|**Toepassingen**|-||  
|**Back-upmap**|-||  
|**Back-upbestand**|-||  
|**BackupShare**|-||  
|**BDEInstall**|-||  
|**BDEKeyLocation**|-||  
|**BDERecoveryKey**|-||  
|**BDEWaitForEncryption**|-||  
|**CapableArchitecture**|-||  
|**ComputerBackupLocation**|-||  
|**CustomWizardSelectionProfile**|-||  
|**DeploymentType**|-||  
|**DeployRoot**|-||  
|**DomainAdmin**|-||  
|**DomainAdminDomain**|-||  
|**DomainAdminPassword**|-||  
|**DomainOUs**|-||  
|**ImageBuild**|-||  
|**ImageFlags**|-||  
|**ImageLanguage**|-||  
|**ImageLanguage001**|-||  
|**ImageProcessor**|-||  
|**IsServerOS**|-||  
|**KeyboardLocale**|-||  
|**KeyboardLocale_Edit**|-||  
|**LanguagePacks**|-||  
|**LanguagePacks001**|-||  
|**LocalDeployRoot**|-||  
|**MandatoryApplications**|-||  
|**OSDComputerName**|-||  
|**OSCurrentBuild**|-||  
|**OSDBitLockerCreateRecoveryPassword**|-||  
|**OSDBitLockerMode**|-||  
|**OSDBitLockerStartupKeyDrive**|-||  
|**OSDBitLockerWaitForEncryption**|-||  
|**OSSKU**|-||  
|**OSVersion**|-||  
|**OverrideProductKey**|-||  
|**ProductKey**|-||  
|**SkipCapture**|-||  
|**SkipDomainMembership**|-||  
|**TaskSequenceID**|-||  
|**TimeZoneName**|-||  
|**TSGUID**|-||  
|**UDDir**|-||  
|**UDShare**|-||  
|**UILanguage**|-||  
|**UserDataLocation**|-||  
|**UserDomain**|-||  
|**Gebruikers-id**|-||  
|**UserLocale**|-||  
|**UserPassword**|-||  
|**WizardSelectionProfile**|-||  

###  <a name="DeployWiz_Validation.vbs"></a>DeployWiz_Validation.vbs  
 Dit script wordt geïnitialiseerd en valideert de gegevens die op de pagina's van de Wizard implementatie (opgeslagen in [DeployWiz_Definition_ENU.xml](#DeployWiz_Definition_ENU.xml)). Dit script bevat de functies en subroutines die de Wizard implementatie tijdens de implementatie van een LTI aanroept.  

|**Waarde**|**Beschrijving**|  
|-|-|
|**Invoer**|- **OperatingSystems.xml**. Bevat de lijst met besturingssystemen die beschikbaar zijn voor implementatie<br /><br /> - **Omgevingsvariabelen**. Bevat de lijst met waarden van eigenschappen, aangepaste eigenschappen databaseverbindingen, regels voor implementatie en andere informatie vereist door de scripts voor het voltooien van het implementatieproces; de omgevingsvariabelen worden ingevuld met ZTIGather.wsf|  
|**Uitvoer**|Geen|  
|**Verwijzingen**|- **Credentials_ENU.XML**. Vraagt de gebruiker om referenties op die wordt gebruikt bij het verbinding maken met netwerkbronnen<br /><br /> - **ZTIGather.wsf**. Eigenschappen en verwerken van regels moeten worden verzameld|  
|**Locatie**|*distributie*\Scripts|  
|**Gebruik**|`<script language="VBScript" src="DeployWiz_Validation.vbs"/>`|  

#### <a name="arguments"></a>Argumenten  

|**Waarde**|**Beschrijving**|  
|-|-|
|Geen|Geen|  

#### <a name="properties"></a>Eigenschappen  

|**Naam**|**Lezen**|**Schrijven**|  
|-|-|-|  
|**Architectuur**|-||  
|**DeploymentType**|-|-|  
|**DeployTemplate**||-|  
|**ImageBuild**|-||  
|**ImageProcessor**|-|-|  
|**OSVersion**|-||  
|**TaskSequenceID**||-|  
|**TSGUID**|-||  
|**UserCredentials**|-||  
|**UserDomain**||-|  
|**Gebruikers-id**||-|  
|**UserPassword**||-|  

###  <a name="LiteTouch.vbs"></a>LiteTouch.vbs  
 Dit script wordt aangeroepen door de Wizard implementatie LTI te initiëren. Het script:  

-   Hiermee verwijdert u de map C:\MININT (indien aanwezig)  

-   Controleert of de doelcomputer voldoet aan de vereisten voor het uitvoeren van de Wizard implementatie door het aanroepen van [ZTIPrereq.vbs](#ZTIPrereq.vbs)  

-   Start de Wizard implementatie door te voeren [LiteTouch.wsf](#LiteTouch.wsf)  

|**Waarde**|**Beschrijving**|  
|-|-|
|**Invoer**|Geen|  
|**Uitvoer**|Geen|  
|**Verwijzingen**|- **BDDRun.exe**<br /><br /> - **ZTIPrereq.vbs**. Gebruikt om te bepalen of de doelcomputer voldoet aan de vereisten voor het implementeren van een nieuw besturingssysteem<br /><br /> - **LiteTouch.wsf**. Het script zelf verantwoordelijk voor het beheren van de LTI-implementatieproces|  
|**Locatie**|*distributie*\Scripts|  
|**Gebruik**|`cscript LiteTouch.vbs </debug:value>`|  

#### <a name="arguments"></a>Argumenten  

|**Waarde**|**Beschrijving**|  
|-|-|
|**/ debug: * waarde***|De uitvoer van de event-berichten naar de console en tot de .log-bestanden. Als de waarde die is opgegeven in waarde is:<br /><br /> - **De waarde TRUE**, event-berichten worden verzonden naar de console en de .log-bestanden<br /><br /> - **ONWAAR**, gebeurtenis berichten worden alleen naar het .log-bestanden (dit is het gedrag wanneer het argument niet is opgegeven)|  

#### <a name="properties"></a>Eigenschappen  

|**Naam**|**Lezen**|**Schrijven**|  
|-|-|-|  
|Geen|||  

###  <a name="LiteTouch.wsf"></a>LiteTouch.wsf  
 Dit script wordt aangeroepen door [LiteTouch.vbs](#LiteTouch.vbs) en is verantwoordelijk voor het beheren van het implementatieproces LTI. Dit omvat:  

-   De implementatiewizard uitvoert voor  

-   Het implementatieproces LTI uitgevoerd met behulp van de juiste volgorde-bestand  

|**Waarde**|**Beschrijving**|  
|-|-|
|**Invoer**|-***task_sequence_file*.xml**. Bevat de taken en de volgorde van taken voor het implementatieproces LTI<br /><br /> - **Omgevingsvariabelen**. Bevat de lijst met waarden van eigenschappen, aangepaste eigenschappen databaseverbindingen, regels voor implementatie en andere informatie vereist door de scripts voor het voltooien van het implementatieproces; de omgevingsvariabelen worden ingevuld met ZTIGather.wsf|  
|**Uitvoer**|-                          **LiteTouch.log**. Logboekbestand met gebeurtenissen die dit script genereert<br /><br /> -                          **BDD.log**. Logboekbestand met gebeurtenissen die alle MDT scripts genereren|  
|**Verwijzingen**|-                          **BDD_Welcome_ENU.XML**. Geeft de Wizard implementatie **Welkom** pagina voor de implementatie van de LTI<br /><br /> -                          **DeployWiz_Definition_ENU.xml**. Geeft de Wizard implementatie van pagina's voor implementatie van de LTI<br /><br /> -                          **DiskPart.exe**. Hiermee kunt u het automatisch beheer van schijven, partities en volumes<br /><br /> -                          **LTICleanup.wsf**. Opruimen van taken worden uitgevoerd nadat de implementatie is voltooid<br /><br /> -                          **LTICopyScripts.wsf**. De implementatiescripts kopieert naar een lokale vaste schijf op de doelcomputer<br /><br /> -                          **MSHTA.exe**. HTML-toepassingshost<br /><br /> -                          **RecEnv.exe**. Als dit hulpprogramma bestaat, wordt de gebruiker gevraagd om te bepalen of de Windows Herstelomgeving starten.<br /><br /> -                          **Regsvr32.exe**. Registreert de bestanden (.exe .dll .ocx en enzovoort) met het besturingssysteem<br /><br /> -                          **Summary_Definition_ENU.XML**. Geeft de samenvatting van de resultaten voor de LTI-implementatie<br /><br /> -                          **TsmBootStrap.exe**. Taak sequence Bootstrap-hulpprogramma<br /><br /> -                          **Wizard.hta**. Geeft de Wizard implementatie van pagina 's<br /><br /> -                          **WPEUtil.exe**. Initialiseert de Windows PE en netwerkverbindingen; initieert LTI<br /><br /> -                          **ZTIGather.wsf**. Eigenschappen en verwerken van regels moeten worden verzameld<br /><br /> -                          **ZTIPrereq.vbs**. Controleert of de doelcomputer voldoet aan de vereisten voor het uitvoeren van de Wizard implementatie<br /><br /> -                          **ZTINICConfig.wsf**. Hiermee configureert u geactiveerde-netwerkadapters<br /><br /> -                          **ZTIUtility.vbs**. Ondersteunende functies en subroutines die maakt gebruik van het script bevat|  
|**Locatie**|*distributie*\Scripts|  
|**Gebruik**|`BDDRun.exe "wscript.exe <ScriptDirectory>\LiteTouch.wsf </debug:value>"`|  

#### <a name="arguments"></a>Argumenten  

|**Waarde**|**Beschrijving**|  
|-|-|
|**/ debug: * waarde***|De uitvoer van de event-berichten naar de console en tot de .log-bestanden. Als de waarde die is opgegeven in waarde is:<br /><br /> -                              **De waarde TRUE**, event-berichten worden verzonden naar de console en de .log-bestanden<br /><br /> -                              **ONWAAR**, gebeurtenis berichten worden alleen naar het .log-bestanden (dit is het gedrag wanneer het argument niet is opgegeven)|  
|**/ Starten**|Een snelkoppeling maakt in het nieuwe besturingssysteem die wordt uitgevoerd zodra de shell wordt gestart|  

#### <a name="properties"></a>Eigenschappen  

|**Naam**|**Lezen**|**Schrijven**|  
|-|-|-|  
|**_DoNotCleanLiteTouch**|-||  
|**_SMSTSPackageName**||-|  
|**AdminPassword**|-||  
|**Architectuur**|-|-|  
|**BootPE**|-|-|  
|**ComputerBackupLocation**||-|  
|**Computernaam**|-||  
|**DeployDrive**|-|-|  
|**DeploymentMethod**|-|-|  
|**DeploymentType**|-|-|  
|**DeployRoot**|-|-|  
|**DestinationLogicalDrive**||-|  
|**DomainAdmin**||-|  
|**DomainAdminDomain**||-|  
|**DomainAdminPassword**||-|  
|**FinishAction**|-||  
|**Hostnaam**|-||  
|**IsServerCoreOS**|-||  
|**JoinDomain**|-||  
|**JoinWorkgroup kan**|-|-|  
|**KeyboardLocalePE**|-||  
|**LTISuspend**|-||  
|**OSDAdapterCount**|-||  
|**OSDComputerName**|-|-|  
|**Fase**|-|-|  
|**ResourceDrive**|-|-|  
|**ResourceRoot**|-|-|  
|**RetVal**||-|  
|**SkipBDDWelcome**|-||  
|**SkipFinalSummary**|-|-|  
|**SkipWizard**|-||  
|**SMSTSLocalDataDrive**||-|  
|**TaskSequenceID**|-||  
|**TimeZoneName**||-|  
|**UserDataLocation**|-|-|  
|**UserDomain**|-||  
|**Gebruikers-id**|-||  
|**UserPassword**|-||  
|**WelcomeWizardCommand**|-||  
|**WizardComplete**|-||  

###  <a name="LTIApply.wsf"></a>LTIApply.wsf  
 Dit script is verantwoordelijk voor het installeren van een Windows PE-installatiekopie op de doelcomputer. De Windows PE-installatiekopie wordt gebruikt voor het verzamelen van informatie over de doelcomputer en de implementatietaken uitvoeren op de doelcomputer.  

|**Waarde**|**Beschrijving**|  
|-|-|
|**Invoer**|**Omgevingsvariabelen**. Bevat de eigenschapswaarden, waarden voor aangepaste eigenschappen databaseverbindingen, regels voor implementatie en andere informatie die de scripts nodig om de implementatieproces te voltooien|  
|**Uitvoer**|-                          **LTIApply.log**. Logboekbestand met gebeurtenissen die dit script genereert<br /><br /> -                          **LTIApply_wdsmcast.log**. Logboekbestand met gebeurtenissen die het hulpprogramma Wdsmcast genereert<br /><br /> -                          **BDD.log**. Logboekbestand met gebeurtenissen die alle MDT scripts genereren|  
|**Verwijzingen**|-                          **CMD.exe**. Hiermee kunt de uitvoering van de opdrachtregelprogramma 's<br /><br /> -                          **Bootsect.exe**. Een opstartsector is van toepassing op de harde schijf<br /><br /> -                          **ImageX.exe**. Een hulpprogramma dat wordt gebruikt voor het maken en beheren van de WIM-bestanden<br /><br /> -                          **ZTIBCDUtility.vbs**. Bevat hulpprogrammafuncties gebruikt bij het uitvoeren van taken Opstartbeheer<br /><br /> -                          **ZTIConfigFile.vbs**. Bevat routines voor de verwerking van XML-bestanden<br /><br /> -                          **ZTIDiskUtility.vbs**. Ondersteunende functies en subroutines die maakt gebruik van het script bevat<br /><br /> -                          **ZTIUtility.vbs**. Ondersteunende functies en subroutines die maakt gebruik van het script bevat<br /><br /> -                          **Wdsmcast.exe**. Een hulpprogramma waarmee doelcomputers deelnemen aan een multicast-overdracht|  
|**Locatie**|*distributie*\Scripts|  
|**Gebruik**|`cscript LTIApply.wsf </pe> </post> </debug:value>`|  

#### <a name="arguments"></a>Argumenten  

|**Waarde**|**Beschrijving**|  
|-|-|
|**/PE**|Gebruikt het proces voor het installeren van de Windows PE-installatiekopie op de doelcomputer|  
|**/ boeken**|Onnodige bestanden ruimt na de installatie van een installatiekopie|  
|**/ debug: * waarde***|Uitvoer van de event-berichten naar de console en tot de bestanden .log; Als de waarde die is opgegeven in waarde is:<br /><br /> -                              **De waarde TRUE**, event-berichten worden verzonden naar de console en de .log-bestanden<br /><br /> -                              **ONWAAR**, gebeurtenis berichten worden alleen naar het .log-bestanden (dit is het gedrag wanneer het argument niet is opgegeven)|  

#### <a name="properties"></a>Eigenschappen  

|**Naam**|**Lezen**|**Schrijven**|  
|-|-|-|  
|**Architectuur**|-||  
|**BootPE**||-|  
|**DeployRoot**|-||  
|**DestinationLogicalDrive**|-|-|  
|**OSGUID**|-||  
|**OSCurrentVersion**|-||  
|**OSVersion**|-||  
|**ImageBuild**|-||  
|**ImageFlags**|-||  
|**ImageProcessor**|-||  
|**ISBDE**|-||  
|**Bronpad**||-|  
|**TaskSequenceID**|-||  
|**UserDomain**|-||  
|**Gebruikers-id**|-||  
|**UserPassword**|-||  
|**WDSServer**|-||  

###  <a name="LTICleanup.wsf"></a>LTICleanup.wsf  
 Dit script Hiermee verwijdert u bestanden of configuratie-instellingen (zoals scripts, mappen, registervermeldingen of configuratie-instellingen voor automatische aanmelding) van de doelcomputer nadat het implementatieproces is voltooid.  

|**Waarde**|**Beschrijving**|  
|-|-|
|**Invoer**|**Omgevingsvariabelen**. Bevat de lijst van eigenschapswaarden, aangepaste eigenschappen databaseverbindingen, regels voor implementatie en andere informatie dat de scripts nodig om de implementatieproces te voltooien. De omgevingsvariabelen worden ingevuld met ZTIGather.wsf.|  
|**Uitvoer**|-                          **LTICleanup.log**. Logboekbestand met gebeurtenissen die dit script genereert<br /><br /> -                          **BDD.log**. Logboekbestand met gebeurtenissen die alle MDT scripts genereren|  
|**Verwijzingen**|-                          **Bootsect.exe**. Een opstartsector is van toepassing op de harde schijf<br /><br /> -                          **NET.exe**. Voert taken voor netwerkbeheer<br /><br /> -                          **RegSvr32.exe**. Registreert de bestanden (.exe .dll .ocx en enzovoort) met het besturingssysteem<br /><br /> -                          **ZTIBCDUtility.vbs**. Bevat hulpprogrammafuncties gebruikt bij het uitvoeren van taken Opstartbeheer<br /><br /> -                          **ZTIUtility.vbs**. Ondersteunende functies en subroutines die maakt gebruik van het script bevat|  
|**Locatie**|*distributie*\Scripts|  
|**Gebruik**|`cscript LTICleanup.wsf </debug:value>`|  

#### <a name="arguments"></a>Argumenten  

|**Waarde**|**Beschrijving**|  
|-|-|
|**/ debug: * waarde***|De uitvoer van de event-berichten naar de console en tot de .log-bestanden. Als de waarde die is opgegeven in waarde is:<br /><br /> -                              **De waarde TRUE**, event-berichten worden verzonden naar de console en de .log-bestanden<br /><br /> -                              **ONWAAR**, gebeurtenis berichten worden alleen naar het .log-bestanden (dit is het gedrag wanneer het argument niet is opgegeven)|  

#### <a name="properties"></a>Eigenschappen  

|**Naam**|**Lezen**|**Schrijven**|  
|-|-|-|  
|**_DoNotCleanLiteTouch**|-||  
|**DeployRoot**|-||  
|**DestinationLogicalDrive**|-||  
|**OSVersion**|-||  

###  <a name="LTICopyScripts.wsf"></a>LTICopyScripts.wsf  
 Dit script implementatiescripts aan de voor de implementatie LTI en ZTI processen naar een lokale vaste schijf op de doelcomputer gekopieerd.  

|**Waarde**|**Beschrijving**|  
|-|-|
|**Invoer**|-                          **Summary_Definition_ENU.XML**. Geeft de samenvatting van de resultaten voor de LTI-implementatie<br /><br /> -                          **Omgevingsvariabelen**. Bevat de eigenschapswaarden, waarden voor aangepaste eigenschappen databaseverbindingen, regels voor implementatie en andere informatie dat de scripts nodig om de implementatieproces te voltooien|  
|**Uitvoer**|-                          **LTICopyScripts.log**. Logboekbestand met gebeurtenissen die dit script genereert<br /><br /> -                          **BDD.log**. Logboekbestand met gebeurtenissen die alle MDT scripts genereren|  
|**Verwijzingen**|**ZTIUtility.vbs**. Ondersteunende functies en subroutines die maakt gebruik van het script bevat|  
|**Locatie**|*distributie*\Scripts|  
|**Gebruik**|`cscript LTICopyScripts.wsf </debug:value>`|  

#### <a name="arguments"></a>Argumenten  

|**Waarde**|**Beschrijving**|  
|-|-|
|**/ debug: * waarde***|De uitvoer van de event-berichten naar de console en tot de .log-bestanden. Als de waarde die is opgegeven in waarde is:<br /><br /> -                              **De waarde TRUE**, event-berichten worden verzonden naar de console en de .log-bestanden<br /><br /> -                              **ONWAAR**, gebeurtenis berichten worden alleen naar het .log-bestanden (dit is het gedrag wanneer het argument niet is opgegeven)|  

#### <a name="properties"></a>Eigenschappen  

|**Naam**|**Lezen**|**Schrijven**|  
|-|-|-|  
|Geen|||  

###  <a name="LTIGetFolder.wsf"></a>LTIGetFolder.wsf  
 Dit script geeft een dialoogvenster waarmee de gebruiker zoekopdrachten naar een map. Pad naar de geselecteerde map wordt opgeslagen in de omgevingsvariabele FOLDERPATH.  

|**Waarde**|**Beschrijving**|  
|-|-|
|**Invoer**|**Omgevingsvariabelen**. Bevat de lijst van eigenschapswaarden, aangepaste eigenschappen databaseverbindingen, regels voor implementatie en andere informatie dat de scripts nodig om de implementatieproces te voltooien. De omgevingsvariabelen worden ingevuld met ZTIGather.wsf.|  
|**Uitvoer**|Geen|  
|**Verwijzingen**|-                          **ZTIUtility.vbs**. Van ondersteuningsfuncties en subroutines die gebruikmaakt van het script bevat<br /><br /> -                          **WizUtility.vbs**. Omvat voor ondersteuningsfuncties en subroutines die gebruikmaakt van de gebruikersinterface (zoals wizardpagina's)|  
|**Locatie**|-                          *distributie*\Scripts<br /><br /> -                          *program_files*\Microsoft Deployment Toolkit\Scripts|  
|**Gebruik**|`cscript LTIGetFolder.wsf </debug:value>`|  

#### <a name="arguments"></a>Argumenten  

|**Waarde**|**Beschrijving**|  
|-|-|
|**/Debug:Value**|De uitvoer van de event-berichten naar de console en tot de .log-bestanden. Als de waarde die is opgegeven in waarde is:<br /><br /> -                              **De waarde TRUE**, event-berichten worden verzonden naar de console en de .log-bestanden<br /><br /> -                              **ONWAAR**, gebeurtenis berichten worden alleen naar het .log-bestanden (dit is het gedrag wanneer het argument niet is opgegeven)|  

#### <a name="properties"></a>Eigenschappen  

|**Naam**|**Lezen**|**Schrijven**|  
|-|-|-|  
|**DefaultFolderPath**|-||  
|**FolderPath**||-|  

###  <a name="LTIOEM.wsf"></a>LTIOEM.wsf  
 Dit script wordt gebruikt door een OEM tijdens een LTI OEM-scenario de inhoud van een media-implementatieshare kopiëren naar de doelcomputer harde schijf voorbereiden duplicatie.  

|**Waarde**|**Beschrijving**|  
|-|-|
|**Invoer**|**Omgevingsvariabelen**. Bevat de lijst van eigenschapswaarden, aangepaste eigenschappen databaseverbindingen, regels voor implementatie en andere informatie dat de scripts nodig om de implementatieproces te voltooien. De omgevingsvariabelen worden ingevuld met ZTIGather.wsf.|  
|**Uitvoer**|-                          **LTIOEM.log**. Logboekbestand met gebeurtenissen die dit script genereert<br /><br /> -                          **BDD.log**. Logboekbestand met gebeurtenissen die alle MDT scripts genereren|  
|**Verwijzingen**|-                          **RoboCopy.exe**. Hulpprogramma voor bestanden en mappen kopiëren<br /><br /> -                          **ZTIUtility.vbs**. Van ondersteuningsfuncties en subroutines die gebruikmaakt van het script bevat|  
|**Locatie**|*distributie*\Scripts|  
|**Gebruik**|`cscript LTIOEM.wsf </BITLOCKER &#124; /BDE> </debug:value>`|  

#### <a name="arguments"></a>Argumenten  

|**Waarde**|**Beschrijving**|  
|-|-|
|**/ debug: * waarde***|De uitvoer van de event-berichten naar de console en tot de .log-bestanden. Als de waarde die is opgegeven in waarde is:<br /><br /> -                              **De waarde TRUE**, event-berichten worden verzonden naar de console en de .log-bestanden<br /><br /> -                              **ONWAAR**, gebeurtenis berichten worden alleen naar het .log-bestanden (dit is het gedrag wanneer het argument niet is opgegeven)|  
|**/ BITLOCKER**|BitLocker wordt ingeschakeld|  
|**/ BDE**|BitLocker wordt ingeschakeld|  

#### <a name="properties"></a>Eigenschappen  

|**Naam**|**Lezen**|**Schrijven**|  
|-|-|-|  
|**_DoNotCleanLiteTouch**||-|  
|**DeployDrive**|-||  
|**DeployRoot**|-||  
|**TSGUID**|-||  

###  <a name="LTISuspend.wsf"></a>LTISuspend.wsf  
 Dit script wordt onderbroken een takenreeks om toe te staan handmatige taken worden uitgevoerd. Wanneer dit script wordt uitgevoerd, maakt een **Takenreeks hervatten** snelkoppeling op het bureaublad van de gebruiker waarmee de gebruiker de takenreeks opnieuw opstarten nadat alle handmatige taken zijn voltooid.  

> [!NOTE]
>  Dit script wordt alleen ondersteund in het volledige besturingssysteem.  

|**Waarde**|**Beschrijving**|  
|-|-|
|**Invoer**|**Omgevingsvariabelen**. Bevat de lijst van eigenschapswaarden, aangepaste eigenschappen databaseverbindingen, regels voor implementatie en andere informatie die de scripts nodig om de implementatieproces te voltooien. De omgevingsvariabelen worden ingevuld met ZTIGather.wsf.|  
|**Uitvoer**|-                          **LTISuspend.log**. Logboekbestand met gebeurtenissen die dit script genereert<br /><br /> -                          **BDD.log**. Logboekbestand met gebeurtenissen die alle MDT scripts genereren|  
|**Verwijzingen**|-                          **LiteTouch.wsf**. Hiermee bepaalt u het implementatieproces LTI<br /><br /> -                          **LTICopyScripts.wsf**. De implementatiescripts kopieert naar een lokale vaste schijf op de doelcomputer<br /><br /> -                          **ZTIUtility.vbs**. Van ondersteuningsfuncties en subroutines die gebruikmaakt van het script bevat|  
|**Locatie**|*distributie*\Scripts|  
|**Gebruik**|`cscript LTISuspend.wsf </debug:value>`|  

#### <a name="arguments"></a>Argumenten  

|**Waarde**|**Beschrijving**|  
|-|-|
|**/ debug: * waarde***|De uitvoer van de event-berichten naar de console en tot de .log-bestanden. Als de waarde die is opgegeven in waarde is:<br /><br /> -                              **De waarde TRUE**, event-berichten worden verzonden naar de console en de .log-bestanden<br /><br /> -                              **ONWAAR**, gebeurtenis berichten worden alleen naar het .log-bestanden (dit is het gedrag wanneer het argument niet is opgegeven)|  
|**/ Hervatten**|:|  

#### <a name="properties"></a>Eigenschappen  

|**Naam**|**Lezen**|**Schrijven**|  
|-|-|-|  
|**LTISuspend**||-|  
|**SMSTSRebootRequested**||-|  

###  <a name="LTISysprep.wsf"></a>LTISysprep.wsf  
 Dit script bereidt de doelcomputer voor het uitvoeren van Sysprep, wordt Sysprep uitgevoerd op de doelcomputer en controleert daarna of Sysprep is uitgevoerd.  

|**Waarde**|**Beschrijving**|  
|-|-|
|**Invoer**|**Omgevingsvariabelen**. Bevat de lijst van eigenschapswaarden, aangepaste eigenschappen databaseverbindingen, regels voor implementatie en andere informatie dat de scripts nodig om de implementatieproces te voltooien. De omgevingsvariabelen worden ingevuld met ZTIGather.wsf.|  
|**Uitvoer**|-                          **LTISysprep.log**. Logboekbestand met gebeurtenissen die dit script genereert<br /><br /> -                          **BDD.log**. Logboekbestand met gebeurtenissen die alle MDT scripts genereren|  
|**Verwijzingen**|-                          **Expand.exe**. Gecomprimeerde bestanden worden uitgevouwen<br /><br /> -                          **Sysprep.exe**. Duplicatie voorbereiden computers<br /><br /> -                          **ZTIConfigFile.vbs**. Bevat routines voor de verwerking van XML-bestanden<br /><br /> -                          **ZTIUtility.vbs**. Van ondersteuningsfuncties en subroutines die gebruikmaakt van het script bevat|  
|**Locatie**|*distributie*\Scripts|  
|**Gebruik**|`cscript LTISysprep.wsf </debug:value>`|  

#### <a name="arguments"></a>Argumenten  

|**Waarde**|**Beschrijving**|  
|-|-|
|**/ debug: * waarde***|De uitvoer van de event-berichten naar de console en tot de .log-bestanden. Als de waarde die is opgegeven in waarde is:<br /><br /> -                              **De waarde TRUE**, event-berichten worden verzonden naar de console en de .log-bestanden<br /><br /> -                              **ONWAAR**, gebeurtenis berichten worden alleen naar het .log-bestanden (dit is het gedrag wanneer het argument is niet opgegeven.)|  

#### <a name="properties"></a>Eigenschappen  

|**Naam**|**Lezen**|**Schrijven**|  
|-|-|-|  
|**Architectuur**|-||  
|**DeployRoot**|-||  
|**DestinationLogicalDrive**|-||  
|**DoCapture**|-||  
|**OSCurrentBuild**|-||  
|**OSDAnswerFilePath**|-||  
|**OSGUID**|-||  
|**Bronpad**|-|-|  
|**TaskSequenceID**|-||  

###  <a name="NICSettings_Definition_ENU.xml"></a>NICSettings_Definition_ENU.xml  
 Dit XML-bestand bevat de scriptcode en HTML-indeling voor de **statische IP-netwerkinstellingen configureren** pagina in de Wizard implementatie van de wizard. Tijdens de implementatie van een LTI Wizard.hta leest dit bestand en de ingesloten wizardpagina die vraagt om de vereiste netwerk adressering configuratie wordt uitgevoerd. Als er geen statische IP-adresconfiguratie wordt geleverd, wordt de implementatiescripts standaard met gebruik van DHCP voor het verkrijgen van de vereiste netwerkconfiguratie.  

|**Waarde**|**Beschrijving**|  
|-|-|
|**Invoer**|Geen|  
|**Uitvoer**|Geen|  
|**Verwijzingen**|**ZTINICUtility.vbs**. Van ondersteuningsfuncties en subroutines die gebruikmaakt van het script bevat|  
|**Locatie**|*distributie*\Scripts|  
|**Gebruik**|Geen|  

#### <a name="arguments"></a>Argumenten  

|**Waarde**|**Beschrijving**|  
|-|-|
|Geen|Geen|  

#### <a name="properties"></a>Eigenschappen  

|**Naam**|**Lezen**|**Schrijven**|  
|-|-|-|  
|**OSDAdapterxDNSServerList**||-|  
|**OSDAdapterxDNSSuffix**||-|  
|**OSDAdapterxGateways**||-|  
|**OSDAdapterxIPAddressList**||-|  
|**OSDAdapterxMacAddress**||-|  
|**OSDAdapterxSubnetMask**||-|  
|**OSDAdapterxWINSServerList**||-|  
|**OSDAdapterCount**||-|  

> [!NOTE]
>  De*x*is een tijdelijke aanduiding voor een op nul gebaseerde matrix met netwerkadapterinformatie in de namen van de eigenschappen die hierboven worden genoemd.  

###  <a name="Summary_Definition_ENU.xml"></a>Summary_Definition_ENU.XML  
 Dit XML-bestand bevat de scriptcode en HTML-indeling voor de **implementatieoverzicht** pagina in de Wizard implementatie van de wizard. Tijdens de implementatie van een LTI Wizard.hta leest dit bestand en de ingesloten wizardpagina die wordt weergegeven van de samenvatting van de resultaten voor de LTI-implementatie wordt uitgevoerd. Dit XML-bestand bevat de volgende wizardpagina's:  

-   **Geslaagde**. Kennisgeving met betrekking tot de implementatietaken voltooid  

-   **Fout**. Kennisgeving met betrekking tot de fout voor het voltooien van de implementatietaken  

|**Waarde**|**Beschrijving**|  
|-|-|
|**Invoer**|Geen|  
|**Uitvoer**|Geen|  
|**Verwijzingen**|**Summary_Scripts.vbs**. Omvat voor ondersteuningsfuncties en subroutines die de wizardpagina's die zijn ingesloten in dit XML-bestand|  
|**Locatie**|*distributie*\Scripts|  
|**Gebruik**|Geen|  

#### <a name="arguments"></a>Argumenten  

|**Waarde**|**Beschrijving**|  
|-|-|
|Geen|Geen|  

#### <a name="properties"></a>Eigenschappen  

|**Naam**|**Lezen**|**Schrijven**|  
|-|-|-|  
|**SkipFinalSummary**|-||  
|**RetVal**|-||  

###  <a name="Summary_scripts.vbs"></a>Summary_scripts.vbs  
 Dit script wordt aangeroepen door de **samenvatting** pagina van de Wizard implementatie van de wizard. Deze bevat functies en subroutines gebruikt voor initialisatie en validatie.  

|**Waarde**|**Beschrijving**|  
|-|-|
|**Invoer**|**Omgevingsvariabelen**. Bevat de eigenschapswaarden, waarden voor aangepaste eigenschappen databaseverbindingen, regels voor implementatie en andere informatie dat de scripts nodig om de implementatieproces te voltooien|  
|**Uitvoer**|Gebeurtenisbericht naar deze logboekbestanden geschreven:<br /><br /> -                          **Summary_scripts.log**. Logboekbestand met gebeurtenissen die dit script genereert<br /><br /> -                          **BDD.log**. Logboekbestand met gebeurtenissen die alle MDT scripts genereren|  
|**Verwijzingen**|Geen|  
|**Locatie**|*distributie*\Scripts|  
|**Gebruik**|`<script language="VBScript" src="Summary_Scripts.vbs"/>`|  

#### <a name="arguments"></a>Argumenten  

|**Waarde**|**Beschrijving**|  
|-|-|
|Geen|Geen|  

#### <a name="properties"></a>Eigenschappen  

|**Naam**|**Lezen**|**Schrijven**|  
|-|-|-|  
|**DeploymentType**|-||  
|**RetVal**|-||  

###  <a name="Wizard.hta"></a>Wizard.hta  
 Deze toepassing Hypertext geeft de Wizard implementatie van pagina's.  

|**Waarde**|**Beschrijving**|  
|-|-|
|**Invoer**|**Omgevingsvariabelen**. Bevat de lijst van eigenschapswaarden, aangepaste eigenschappen databaseverbindingen, regels voor implementatie en andere informatie dat de scripts nodig om de implementatieproces te voltooien. De omgevingsvariabelen worden ingevuld met ZTIGather.wsf.|  
|**Uitvoer**|-                          **Wizard.log**. Logboekbestand met gebeurtenissen die dit script genereert<br /><br /> -                          **BDD.log**. Logboekbestand met gebeurtenissen die alle MDT scripts genereren|  
|**Verwijzingen**|-                          **LTIGetFolder.wsf**. Scriptbestand dat initieert een **BrowseForFolder** in het dialoogvenster<br /><br /> -                          **ZTIConfigFile.vbs**. Bevat routines voor de verwerking van XML-bestanden<br /><br /> -                          **ZTIUtility.vbs**. Van ondersteuningsfuncties en subroutines die gebruikmaakt van het script bevat<br /><br /> -                          **WizUtility.vbs**. Van ondersteuningsfuncties en subroutines die gebruikmaakt van het script bevat|  
|**Locatie**|-                          *distributie*\Scripts<br /><br /> -                          *program_files*\Microsoft Deployment Toolkit\Scripts|  
|**Gebruik**|`mshta.exe Wizard.hta </definition:filename> </NotWizard> </debug:value>`|  

#### <a name="arguments"></a>Argumenten  

|**Waarde**|**Beschrijving**|  
|-|-|
|**/ debug: * waarde***|De uitvoer van de event-berichten naar de console en tot de .log-bestanden. Als de waarde die is opgegeven in waarde is:<br /><br /> -                              **De waarde TRUE**, event-berichten worden verzonden naar de console en de .log-bestanden<br /><br /> -                              **ONWAAR**, gebeurtenis berichten worden alleen naar het .log-bestanden (dit is het gedrag wanneer het argument is niet opgegeven.)|  
|**/ NotWizard**|Gebruikt voor het overslaan van de wizard pagina prompts|  
|**/ De definitie van: * filename***|Hiermee geeft u het XML-bestand dat moet worden geladen in de wizard|  

#### <a name="properties"></a>Eigenschappen  

|**Naam**|**Lezen**|**Schrijven**|  
|-|-|-|  
|**Definitie**|-||  
|**DefaultFolderPath**||-|  
|**FolderPath**|-||  
|**WizardComplete**||-|  

###  <a name="WizUtility.vbs"></a>WizUtility.vbs  
 Dit script bevat de functies en subroutines die de verschillende implementatiewizard scripts naar verwijzen.  

|**Waarde**|**Beschrijving**|  
|-|-|
|**Invoer**|**Omgevingsvariabelen**. Bevat de eigenschapswaarden, waarden voor aangepaste eigenschappen databaseverbindingen, regels voor implementatie en andere informatie dat de scripts nodig om de implementatieproces te voltooien|  
|**Uitvoer**|-                          **WizUtility.log**. Logboekbestand met gebeurtenissen die dit script genereert<br /><br /> -                          **BDD.log**. Logboekbestand met gebeurtenissen die alle MDT scripts genereren|  
|**Verwijzingen**|**LTIGetFolder.wsf**. Scriptbestand dat initieert een **BrowseForFolder**in het dialoogvenster|  
|**Locatie**|-                          *distributie*\Scripts<br /><br /> -                          *program_files*\Microsoft Deployment Toolkit\Scripts|  
|**Gebruik**|`<script language="VBScript" src="WizUtility.vbs"/>`|  

#### <a name="arguments"></a>Argumenten  

|**Waarde**|**Beschrijving**|  
|-|-|
|Geen|Geen|  

#### <a name="properties"></a>Eigenschappen  

|**Naam**|**Lezen**|**Schrijven**|  
|-|-|-|  
|**DefaultFolderPath**||-|  
|**DefaultDestinationDisk**|-||  
|**DefaultDestinationIsDirty**|-||  
|**DefaultDestinationPartition**|-||  
|**DeploymentType**|-||  
|**DestinationDisk**|-||  
|**FolderPath**|-||  
|**OSVersion**|-||  
|**UserDomain**|-||  
|**UserCredentials**||-|  

###  <a name="ZTIApplications.wsf"></a>ZTIApplications.wsf  
 Dit script initieert een installatie van toepassingen die zijn geconfigureerd in het knooppunt toepassingen in de implementatie-Workbench. Dit script zal niet worden geprobeerd om een toepassing te installeren die:  

-   Biedt geen ondersteuning voor de doelcomputer platformtype  

-   Biedt geen ondersteuning voor de doelcomputer processortype  

-   Heeft een vermelding verwijderen in het register, onder **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion\Uninstall**  

> [!NOTE]
>  Als de vermelde toepassing eventuele afhankelijke toepassingen die zijn gedefinieerd heeft, wordt dit script probeert te installeren die afhankelijke toepassingen voordat u de vermelde toepassing installeert.  

|**Waarde**|**Beschrijving**|  
|-|-|
|**Invoer**|**Omgevingsvariabelen**. Bevat de eigenschapswaarden, waarden voor aangepaste eigenschappen databaseverbindingen, regels voor implementatie en andere informatie dat de scripts nodig om de implementatieproces te voltooien|  
|**Uitvoer**|-                          **ZTIApplications.log**. Logboekbestand met gebeurtenissen die dit script genereert<br /><br /> -                          **BDD.log**. Logboekbestand met gebeurtenissen die alle MDT scripts genereren|  
|**Verwijzingen**|-                          **ZTIConfigFile.vbs**. Bevat routines voor de verwerking van XML-bestanden<br /><br /> -                          **ZTIUtility.vbs**. Van ondersteuningsfuncties en subroutines die gebruikmaakt van het script bevat<br /><br /> -                          **BDDRun.exe**. Hiermee voert u een opdracht die gebruikersinteractie vereist|  
|**Locatie**|*distributie*\Scripts|  
|**Gebruik**|`cscript ZTIApplications.wsf </debug:value>`|  

#### <a name="arguments"></a>Argumenten  

|**Waarde**|**Beschrijving**|  
|-|-|
|**/ debug: * waarde***|De uitvoer van de event-berichten naar de console en tot de .log-bestanden. Als de waarde die is opgegeven in waarde is:<br /><br /> -                              **De waarde TRUE**, event-berichten worden verzonden naar de console en de .log-bestanden<br /><br /> -                              **ONWAAR**, gebeurtenis berichten worden alleen naar het .log-bestanden (dit is het gedrag wanneer het argument niet is opgegeven)|  

#### <a name="properties"></a>Eigenschappen  

|**Naam**|**Lezen**|**Schrijven**|  
|-|-|-|  
|**ApplicationGUID**|-||  
|**ApplicationSuccessCodes**|-||  
|**DependentApplications**|-||  
|**DeploymentMethod**|-||  
|**InstalledApplications**|-|-|  
|**ResourceDrive**|-||  
|**ResourceRoot**|-|-|  
|**SMSTSRebootRequested**||-|  
|**SMSTSRetryRequested**||-|  

###  <a name="ZTIAppXmlGen.wsf"></a>ZTIAppXmlGen.wsf  
 Dit script genereert een XML-file—ZTIAppXmlGen.xml—to gebruik wanneer automatisch vastleggen gebruikersgegevens (documenten) die zijn gekoppeld aan de geïnstalleerde toepassingen. Dit biedt dus via de **HKEY_CLASSES_ROOT\Software\Classes** registersleutel en alle toepassingen vastlegt die:  

-   Niet zijn gekoppeld aan een van de volgende bestandsextensies: .mp3, MOV, .wma, WMV, .chm, .evt, .evtx, .exe, .com of .fon  

-   Niet zijn gekoppeld aan Microsoft Office, zoals het 2007 Office-systeem of de Microsoft Office 2003.  

-   Een geldig open handler die wordt vermeld op hebben **HKEY_CLASSES_ROOT\application\shell\open\command**  

|**Waarde**|**Beschrijving**|  
|-|-|
|**Invoer**|**Omgevingsvariabelen**. Bevat de eigenschapswaarden, waarden voor aangepaste eigenschappen databaseverbindingen, regels voor implementatie en andere informatie dat de scripts nodig om de implementatieproces te voltooien|  
|**Uitvoer**|-                          **ZTIAppXmlGen.xml**. Bevat een lijst met toepassingen die op de doelcomputer is geïnstalleerd<br /><br /> -                          **ZTIAppXmlGen.log**. Logboekbestand met gebeurtenissen die dit script genereert<br /><br /> -                          **BDD.log**. Logboekbestand met gebeurtenissen die alle MDT scripts genereren|  
|**Verwijzingen**|**ZTIUtility.vbs**. Van ondersteuningsfuncties en subroutines die gebruikmaakt van het script bevat|  
|**Locatie**|*distributie*\Scripts|  
|**Gebruik**|`cscript ZTIAppXmlGen.wsf </debug:value>`|  

#### <a name="arguments"></a>Argumenten  

|**Waarde**|**Beschrijving**|  
|-|-|
|**/ debug: * waarde***|De uitvoer van de event-berichten naar de console en tot de .log-bestanden. Als de waarde die is opgegeven in waarde is:<br /><br /> -                              **De waarde TRUE**, event-berichten worden verzonden naar de console en de .log-bestanden<br /><br /> -                              **ONWAAR**, gebeurtenis berichten worden alleen naar het .log-bestanden (dit is het gedrag wanneer het argument is niet opgegeven.)|  

#### <a name="properties"></a>Eigenschappen  

|**Naam**|**Lezen**|**Schrijven**|  
|-|-|-|  
|**DeploymentMethod**|-||  
|**DeploymentType**|-||  
|**ImageBuild**|-||  
|**OSCurrentVersion**|-||  
|**USMTMigFiles**|-|-|  

###  <a name="ZTIAuthorizeDHCP.wsf"></a>ZTIAuthorizeDHCP.wsf  
 Dit script maakt gebruik van de Netsh-hulpprogramma voor het configureren van de doelcomputer, zodat deze een geautoriseerde DHCP-server in AD DS.  

 Zie voor meer informatie over DHCP-servers autoriseren [hoe gebruik Netsh.exe autoriseren, Unauthorize en lijst DHCP-Servers in Active Directory](http://support.microsoft.com/kb/303351).  

|**Waarde**|**Beschrijving**|  
|-|-|
|**Invoer**|**Omgevingsvariabelen**. Bevat de eigenschapswaarden, waarden voor aangepaste eigenschappen databaseverbindingen, regels voor implementatie en andere informatie dat de scripts nodig om de implementatieproces te voltooien|  
|**Uitvoer**|-                          **ZTIAuthorizeDHCP.log**. Logboekbestand met gebeurtenissen die dit script genereert<br /><br /> -                          **BDD.log**. Logboekbestand met gebeurtenissen die alle MDT scripts genereren|  
|**Verwijzingen**|-                          **Netsh.exe**. Een hulpprogramma waarmee u kunt de configuratie van netwerkonderdelen automatiseren<br /><br /> -                          **ZTIUtility.vbs**. Van ondersteuningsfuncties en subroutines die gebruikmaakt van het script bevat|  
|**Locatie**|*distributie*\Scripts|  
|**Gebruik**|`cscript ZTIAuthorizeDHCP.wsf </debug:value>`|  

#### <a name="arguments"></a>Argumenten  

|**Waarde**|**Beschrijving**|  
|-|-|
|**/ debug: * waarde***|De uitvoer van de event-berichten naar de console en tot de .log-bestanden. Als de waarde die is opgegeven in waarde is:<br /><br /> -                              **De waarde TRUE**, event-berichten worden verzonden naar de console en de .log-bestanden<br /><br /> -                              **ONWAAR**, gebeurtenis berichten worden alleen naar het .log-bestanden (dit is het gedrag wanneer het argument is niet opgegeven.)|  

#### <a name="properties"></a>Eigenschappen  

|**Naam**|**Lezen**|**Schrijven**|  
|-|-|-|  
|**IP-adres**|-||  

###  <a name="ZTIBackup.wsf"></a>ZTIBackup.wsf  
 Dit script voert een back-up van de doelcomputer met het hulpprogramma ImageX. De back-up wordt opgeslagen in de opgegeven locatie in de [BackupDir](#BackupDir) en [BackupShare](#BackupShare) eigenschappen.  

|**Waarde**|**Beschrijving**|  
|-|-|
|**Invoer**|**Omgevingsvariabelen**. Bevat de eigenschapswaarden, waarden voor aangepaste eigenschappen databaseverbindingen, regels voor implementatie en andere informatie dat de scripts nodig om de implementatieproces te voltooien|  
|**Uitvoer**|-                          **ZTIBackup.log**. Logboekbestand met gebeurtenissen die dit script genereert<br /><br /> -                          **ZTIBackup_imagex.log**. Logboekbestand met gebeurtenissen die ImageX genereert<br /><br /> -                          **BDD.log**. Logboekbestand met gebeurtenissen die alle MDT scripts genereren|  
|**Verwijzingen**|-                          **ImageX.exe**. Een hulpprogramma dat wordt gebruikt voor het maken en beheren van de WIM-bestanden<br /><br /> -                          **ZTIBCDUtility.vbs**. Bevat hulpprogrammafuncties gebruikt bij het uitvoeren van taken Opstartbeheer<br /><br /> -                          **ZTIDiskUtility.vbs**. Van ondersteuningsfuncties en subroutines die gebruikmaakt van het script bevat<br /><br /> -                          **ZTIUtility.vbs**. Van ondersteuningsfuncties en subroutines die gebruikmaakt van het script bevat|  
|**Locatie**|*distributie*\Scripts|  
|**Gebruik**|`cscript ZTIBackup.wsf </debug:value>`|  

#### <a name="arguments"></a>Argumenten  

|**Waarde**|**Beschrijving**|  
|-|-|
|**/ debug: * waarde***|De uitvoer van de event-berichten naar de console en tot de .log-bestanden. Als de waarde die is opgegeven in waarde is:<br /><br /> -                              **De waarde TRUE**, event-berichten worden verzonden naar de console en de .log-bestanden<br /><br /> -                              **ONWAAR**, gebeurtenis berichten worden alleen naar het .log-bestanden (dit is het gedrag wanneer het argument niet is opgegeven)|  

#### <a name="properties"></a>Eigenschappen  

|**Naam**|**Lezen**|**Schrijven**|  
|-|-|-|  
|**Back-upmap**|-||  
|**BackupDisk**|-||  
|**BackupDrive**|-||  
|**Back-upbestand**|-||  
|**BackupPartition**|-||  
|**BackupScriptComplete**||-|  
|**BackupShare**|-||  
|**ComputerBackupLocation**|-||  
|**DeploymentMethod**|-||  
|**DeploymentType**|-||  
|**DestinationLogicalDrive**|-|-|  
|**DoCapture**|-||  
|**ImageBuild**|-||  
|**ImageFlags**|-||  
|**OSDStateStorePath**|-||  
|**Fase**|-||  
|**TaskSequenceID**|-||  
|**USMTLocal**|-||  

###  <a name="ZTIBCDUtility.vbs"></a>ZTIBCDUtility.vbs  
 Dit script bevat hulpprogrammafuncties die enkele MDT-scripts gebruiken bij het uitvoeren van taken Opstartbeheer.  

|**Waarde**|**Beschrijving**|  
|-|-|
|**Invoer**|**Omgevingsvariabelen**. Bevat de eigenschapswaarden, waarden voor aangepaste eigenschappen databaseverbindingen, regels voor implementatie en andere informatie dat de scripts nodig om de implementatieproces te voltooien|  
|**Uitvoer**|Geen|  
|**Verwijzingen**|**BCDEdit.exe**. Een hulpprogramma voor het bewerken van de configuratie voor het opstarten van Windows|  
|**Locatie**|-                          *distributie*\Scripts<br /><br /> -                          *program_files*\Microsoft Deployment Toolkit\Scripts|  
|**Gebruik**|`<script language="VBScript" src="ZTIBCDUtility.vbs"/>`|  

#### <a name="arguments"></a>Argumenten  

|**Waarde**|**Beschrijving**|  
|-|-|
|Geen|Geen|  

#### <a name="properties"></a>Eigenschappen  

|**Naam**|**Lezen**|**Schrijven**|  
|-|-|-|  
|Geen|||  

###  <a name="ZTIBde.wsf"></a>ZTIBde.wsf  
 Dit script installeert en configureert BitLocker op de doelcomputer. BitLocker-configuratie is beperkt tot de nieuwe Computer scenario's die harde schijven die zijn geconfigureerd met één partitie hebben.  

> [!NOTE]
>  Voor implementaties van ZTI en UDI de **UILanguage** eigenschap moet alleen worden ingesteld in CustomSettings.ini of in de DB MDT omdat ZTIBde.wsf probeert te lezen van de landinstellingen van de **UILanguage** eigenschap.  

|**Waarde**|**Beschrijving**|  
|-|-|
|**Invoer**|**Omgevingsvariabelen**. Bevat de eigenschapswaarden, waarden voor aangepaste eigenschappen databaseverbindingen, regels voor implementatie en andere informatie dat de scripts nodig om de implementatieproces te voltooien|  
|**Uitvoer**|-                          **ZTIBde.log**. Logboekbestand met gebeurtenissen die dit script genereert<br /><br /> -                          **ZTIBdeFix_diskpart.log**. Logboekbestand met gebeurtenissen die het hulpprogramma Diskpart genereert<br /><br /> -                          **BDD.log**. Logboekbestand met gebeurtenissen die alle MDT scripts genereren|  
|**Verwijzingen**|-                          **CMD.exe**. Hiermee kunt het uitvoeren van opdrachtregelprogramma 's<br /><br /> -                          **Defrag.exe**. De vaste schijf defragmenteert<br /><br /> -                          **DiskPart.exe**. Hulpprogramma voor het automatisch beheer van schijven, partities en volumes waarmee<br /><br /> -                          **ServerManagerCmd.exe**<br /><br /> -                          **ZTIDiskUtility.vbs**. Van ondersteuningsfuncties en subroutines die gebruikmaakt van het script bevat<br /><br /> -                          **ZTIOSRole.wsf**. Serverfuncties installeert<br /><br /> -                          **ZTIUtility.vbs**. Van ondersteuningsfuncties en subroutines die gebruikmaakt van het script bevat|  
|**Locatie**|*distributie*\Scripts|  
|**Gebruik**|`cscript ZTIBde.wsf </debug:value>`|  

#### <a name="arguments"></a>Argumenten  

|**Waarde**|**Beschrijving**|  
|-|-|
|**/ debug: * waarde***|De uitvoer van de event-berichten naar de console en tot de .log-bestanden. Als de waarde die is opgegeven in waarde is:<br /><br /> -                              **De waarde TRUE**, event-berichten worden verzonden naar de console en de .log-bestanden<br /><br /> -                              **ONWAAR**, gebeurtenis berichten worden alleen naar het .log-bestanden (dit is het gedrag wanneer het argument niet is opgegeven)|  

#### <a name="properties"></a>Eigenschappen  

|**Naam**|**Lezen**|**Schrijven**|  
|-|-|-|  
|**AdminPassword**|-||  
|**BDEDriveLetter**|-|-|  
|**BDEDriveSize**|-||  
|**BDEInstall**|-||  
|**BDEInstallSuppress**|-||  
|BDEKeyLocation|-||  
|**BDEPin**|-||  
|**BDERecoveryKey**|-||  
|**BDESecondPass**|-|-|  
|**BdeWaitForEncryption**|-||  
|**BitlockerInstalled**|-|-|  
|**DeploymentMethod**|-||  
|**ISBDE**|-||  
|**OSDBitLockerCreateRecoveryPassword**|-||  
|**OSDBitLockerMode**|-||  
|**OSDBitLockerStartupKey**|-||  
|**OSDBitLockerStartupKeyDrive**|-||  
|**OSDBitLockerTargetDrive**|-||  
|**OSDBitLockerWaitForEncryption**|-||  
|**OSCurrentBuild**|-||  
|**OSCurrentVersion**|-||  
|**OSFeatures**|-|-|  
|**OSRoles**|-|-|  
|**OSRoleServices**|-|-|  
|**OSVersion**|-||  
|**SMSTSRebootRequested**|-|-|  
|**SMSTSRetryRequested**||-|  
|**TPMOwnerPassword**|-||  

###  <a name="ZTIBIOSCheck.wsf"></a>ZTIBIOSCheck.wsf  
 Dit script controleert het BIOS op de doelcomputer en vervolgens een lijst met BIOS die incompatibel met Windows zijn kijkt. De lijst met niet-compatibele BIOS wordt opgeslagen in de [ZTIBIOSCheck.xml](#ZTIBIOSCheck.xml) bestand.  

 Als het BIOS op de doelcomputer wordt vermeld in de [ZTIBIOSCheck.xml](#ZTIBIOSCheck.xml) -bestand, en vervolgens het script retourneert een status die aangeeft van het BIOS is niet compatibel met Windows en het implementatieproces moet worden beëindigd. Zie voor informatie over het vullen van de lijst van niet-compatibele BIOS, [ZTIBIOSCheck.xml](#ZTIBIOSCheck.xml).  

|**Waarde**|**Beschrijving**|  
|-|-|
|**Invoer**|-                          **ZTIBIOSCheck.xml**. Bevat een lijst met BIOS waarvan bekend is dat niet compatibel met Windows<br /><br /> -                          **Omgevingsvariabelen**. Bevat de eigenschapswaarden, waarden voor aangepaste eigenschappen databaseverbindingen, regels voor implementatie en andere informatie dat de scripts nodig om de implementatieproces te voltooien|  
|**Uitvoer**|-                          **ZTIBIOSCheck.log**. Logboekbestand met gebeurtenissen die dit script genereert<br /><br /> -                          **BDD.log**. Logboekbestand met gebeurtenissen die alle MDT scripts genereren|  
|**Verwijzingen**|**ZTIUtility.vbs**. Van ondersteuningsfuncties en subroutines die gebruikmaakt van het script bevat|  
|**Locatie**|*distributie*\Scripts|  
|**Gebruik**|`cscript ZTIBIOSCheck.wsf </debug:value>`|  

#### <a name="arguments"></a>Argumenten  

|**Waarde**|**Beschrijving**|  
|-|-|
|**/ debug: * waarde***|De uitvoer van de event-berichten naar de console en tot de .log-bestanden. Als de waarde die is opgegeven in waarde is:<br /><br /> -                              **De waarde TRUE**, event-berichten worden verzonden naar de console en de .log-bestanden<br /><br /> -                              **ONWAAR**, gebeurtenis berichten worden alleen naar het .log-bestanden (dit is het gedrag wanneer het argument niet is opgegeven)|  

#### <a name="properties"></a>Eigenschappen  

|**Naam**|**Lezen**|**Schrijven**|  
|-|-|-|  
|Geen|||  

###  <a name="ZTICoalesce.wsf"></a>ZTICoalesce.wsf  
 Configuration Manager vereist pakketten worden genummerd sequentieel vanaf **PACKAGES001**, met geen hiaten in de numerieke volgorde. Anders, mislukt de installatie.  

 Dit script kunt u definiëren en variabelen identificatiegegevens over het programma uitvoeren met de naam, bijvoorbeeld **ComputerPackages100**, **ComputerPackages110**, of  **CollectionPackages150**. Klik, als dit script wordt uitgevoerd, Configuration Manager vindt alle variabelen die overeenkomen met een patroon (bijvoorbeeld alle namen van variabelen met de tekenreeks **pakketten**) en maakt u een lijst opeenvolgende zonder onderbrekingen, met behulp van de basisnaam  **PAKKETTEN**.  

 Bijvoorbeeld, als de volgende variabelen zijn gedefinieerd (computervariabelen, verzameling-variabelen gebruiken of in CustomSettings.ini of de MDT-database, bijvoorbeeld):  

-   **ComputerPackages100 XXX00001:Program =**  

-   **ComputerPackages110 XXX00002:Program =**  

-   **CollectionPackages150 XXX00003:Program =**  

-   **Packages001 XXX00004:Program =**  

 Nadat het script wordt uitgevoerd, is de lijst:  

-   **PACKAGES001 XXX00004:Program =**  

-   **PACKAGES002 XXX00001:Program =**  

-   **PACKAGES003 XXX00002:Program =**  

-   **PACKAGES004 XXX00003:Program =**  

 Configuration Manager zou vervolgens worden alle vier programma's uitvoeren.  

|**Waarde**|**Beschrijving**|  
|-|-|
|**Invoer**|**Omgevingsvariabelen**. Bevat de eigenschapswaarden, waarden voor aangepaste eigenschappen databaseverbindingen, regels voor implementatie en andere informatie dat de scripts nodig om de implementatieproces te voltooien|  
|**Uitvoer**|-                          **ZTICoalesce.log**. Logboekbestand met gebeurtenissen die dit script genereert<br /><br /> -                          **BDD.log**. Logboekbestand met gebeurtenissen die alle MDT scripts genereren|  
|**Verwijzingen**|**ZTIUtility.vbs**. Van ondersteuningsfuncties en subroutines die gebruikmaakt van het script bevat|  
|**Locatie**|*distributie*\Scripts|  
|**Gebruik**|`cscript ZTICoalesce.wsf </debug:value>`|  

#### <a name="arguments"></a>Argumenten  

|**Waarde**|**Beschrijving**|  
|-|-|
|**/ debug: * waarde***|De uitvoer van de event-berichten naar de console en tot de .log-bestanden. Als de waarde die is opgegeven in waarde is:<br /><br /> -                              **De waarde TRUE**, event-berichten worden verzonden naar de console en de .log-bestanden<br /><br /> -                              **ONWAAR**, gebeurtenis berichten worden alleen naar het .log-bestanden (dit is het gedrag wanneer het argument is niet opgegeven.)|  
|**/ CoalesceDigits: * waarde***|Hiermee geeft u het aantal cijfers die worden opgegeven moeten bij het maken van de nummering. Bijvoorbeeld: een waarde van:<br /><br /> -                              **2** PACKAGE03 te maken<br /><br /> -                              **3**PACKAGE003 te maken<br /><br /> De standaardwaarde als dit argument is niet opgegeven is **3**.|  

#### <a name="properties"></a>Eigenschappen  

|**Naam**|**Lezen**|**Schrijven**|  
|-|-|-|  
|**CoalescePattern**|-||  
|**CoalesceTarget**|-||  

###  <a name="ZTIConfigFile.vbs"></a>ZTIConfigFile.vbs  
 Dit script bevat algemene routines voor het verwerken van de MDT-XML-bestanden.  

|**Waarde**|**Beschrijving**|  
|-|-|
|**Invoer**|**Omgevingsvariabelen**. Bevat de eigenschapswaarden, waarden voor aangepaste eigenschappen databaseverbindingen, regels voor implementatie en andere informatie dat de scripts nodig om de implementatieproces te voltooien|  
|**Uitvoer**|-                          **ZTIConfigFile.log**. Logboekbestand met gebeurtenissen die dit script genereert<br /><br /> -                          **BDD.log**. Logboekbestand met gebeurtenissen die alle MDT scripts genereren|  
|**Verwijzingen**|NET.exe|  
|**Locatie**|*distributie*\Scripts|  
|**Gebruik**|`<script language="VBScript" src="ZTIConfigFile.vbs"/>`|  

#### <a name="arguments"></a>Argumenten  

|**Waarde**|**Beschrijving**|  
|-|-|
|Geen|Geen|  

#### <a name="properties"></a>Eigenschappen  

|**Naam**|**Lezen**|**Schrijven**|  
|-|-|-|  
|**IsSafeForWizardHTML**|-||  
|**MandatoryApplications**|-||  
|**SkipGroupSubFolders**|-||  

###  <a name="ZTIConfigure.wsf"></a>ZTIConfigure.wsf  
 Dit script configureert het bestand Unattend.XML met de eigenschapswaarden die eerder in het implementatieproces MDT opgeven. Het script configureert u het juiste bestand op basis van het besturingssysteem wordt geïmplementeerd.  

 Dit script leest het bestand ZTIConfigure.xml om te bepalen hoe het bestand Unattend.XML bijwerken met de juiste waarden die zijn opgegeven in de implementatie-eigenschappen. Het bestand ZTIConfigure.xml bevat de informatie voor het vertalen van de eigenschappen van de instellingen in het bestand Unattend.XML.  

|**Waarde**|**Beschrijving**|  
|-|-|
|**Invoer**|-                          **ZTIConfigure.xml**. Bevat een overzicht van eigenschapswaarden (opgegeven eerder in het implementatieproces) en hun bijbehorende configuratie-instellingen<br /><br /> -                          **Omgevingsvariabelen**. Bevat de eigenschapswaarden, waarden voor aangepaste eigenschappen databaseverbindingen, regels voor implementatie en andere informatie dat de scripts nodig om de implementatieproces te voltooien|  
|**Uitvoer**|-                          **ZTIConfigure.log**. Logboekbestand met gebeurtenissen die dit script genereert<br /><br /> -                          **BDD.log**. Logboekbestand met gebeurtenissen die alle MDT scripts genereren|  
|**Verwijzingen**|**ZTIUtility.vbs**. Van ondersteuningsfuncties en subroutines die gebruikmaakt van het script bevat|  
|**Locatie**|*distributie*\Scripts|  
|**Gebruik**|`cscript ZTIConfigure.wsf </debug:value>`|  

#### <a name="arguments"></a>Argumenten  

|**Waarde**|**Beschrijving**|  
|-|-|
|**/ debug: * waarde***|De uitvoer van de event-berichten naar de console en tot de .log-bestanden. Als de waarde die is opgegeven in waarde is:<br /><br /> -                              **De waarde TRUE**, event-berichten worden verzonden naar de console en de .log-bestanden<br /><br /> -                              **ONWAAR**, gebeurtenis berichten worden alleen naar het .log-bestanden (dit is het gedrag wanneer het argument is niet opgegeven.)|  

#### <a name="properties"></a>Eigenschappen  

|**Naam**|**Lezen**|**Schrijven**|  
|-|-|-|  
|**Computernaam**|-|-|  
|**DeploymentType**|-||  
|**DeploymentMethod**|-||  
|**DeployRoot**|-||  
|**DestinationLogicalDrive**|-||  
|DomainAdminDomain|-||  
|**ImageBuild**|-||  
|**OSDAnswerFilePath**|-||  
|**OSDAnswerFilePathSysprep**|-||  
|**OSDComputerName**|-||  
|**Fase**|-||  
|**TaskSequenceID**|-||  

###  <a name="ZTIConfigureADDS.wsf"></a>ZTIConfigureADDS.wsf  

|**Waarde**|**Beschrijving**|  
|-|-|
|**Invoer**|**Omgevingsvariabelen**. Bevat de eigenschapswaarden, waarden voor aangepaste eigenschappen databaseverbindingen, regels voor implementatie en andere informatie dat de scripts nodig om de implementatieproces te voltooien|  
|**Uitvoer**|-                          **ZTIConfigureADDS.log**. Logboekbestand met gebeurtenissen die dit script genereert<br /><br /> -                          **BDD.log**. Logboekbestand met gebeurtenissen die alle MDT scripts genereren|  
|**Verwijzingen**|-                          **Dcpromo.exe**. Installeren en verwijderen van AD DS<br /><br /> -                          **NET.exe**. Voert taken voor netwerkbeheer<br /><br /> -                          **ZTIUtility.vbs**. Van ondersteuningsfuncties en subroutines die gebruikmaakt van het script bevat|  
|**Locatie**|*distributie*\Scripts|  
|**Gebruik**|`cscript ZTIConfigureADDS.wsf </debug:value>`|  

#### <a name="arguments"></a>Argumenten  

|**Waarde**|**Beschrijving**|  
|-|-|
|**/ debug: * waarde***|De uitvoer van de event-berichten naar de console en tot de .log-bestanden. Als de waarde die is opgegeven in waarde is:<br /><br /> -                              **De waarde TRUE**, event-berichten worden verzonden naar de console en de .log-bestanden<br /><br /> -                              **ONWAAR**, gebeurtenis berichten worden alleen naar het .log-bestanden (dit is het gedrag wanneer het argument is niet opgegeven.)|  

#### <a name="properties"></a>Eigenschappen  

|**Naam**|**Lezen**|**Schrijven**|  
|-|-|-|  
|**ADDSLogPath**|-||  
|**ADDSPassword**|-||  
|**ADDSUserDomain**|-||  
|**ADDSUserName**|-||  
|**AutoConfigDNS**|-||  
|**ChildName**|-||  
|**ConfirmGC**|-||  
|**DatabasePath**|-||  
|**DomainLevel**|-||  
|**DomainNetBiosName**|-||  
|**ForestLevel**|-||  
|**NewDomain**|-||  
|**NewDomainDNSName**|-||  
|**OSVersion**|-||  
|**ParentDomainDNSName**|-||  
|**ReplicaOrNewDomain**|-|-|  
|**ReplicaDomainDNSName**|-||  
|**ReplicationSourceDC**|-||  
|**SafeModeAdminPassword**|-||  
|**Sitenaam**|-||  
|**SysVolPath**|-||  

###  <a name="ZTIConfigureDHCP.wsf"></a>ZTIConfigureDHCP.wsf  
 Dit script configureert DHCP op de doelcomputer.  

> [!NOTE]
>  DHCP al is geïnstalleerd op de doelcomputer voordat dit script wordt uitgevoerd.  

|**Waarde**|**Beschrijving**|  
|-|-|
|**Invoer**|**Omgevingsvariabelen**. Bevat de eigenschapswaarden, waarden voor aangepaste eigenschappen databaseverbindingen, regels voor implementatie en andere informatie dat de scripts nodig om de implementatieproces te voltooien|  
|**Uitvoer**|-                          **ZTIConfigureDHCP.log**. Logboekbestand met gebeurtenissen die dit script genereert<br /><br /> -                          **BDD.log**. Logboekbestand met gebeurtenissen die alle MDT scripts genereren|  
|**Verwijzingen**|-                          **Netsh.exe**. Een hulpprogramma waarmee de configuratie van netwerkonderdelen automatiseren<br /><br /> -                          **ZTIUtility.vbs**. Van ondersteuningsfuncties en subroutines die gebruikmaakt van het script bevat|  
|**Locatie**|*distributie*\Scripts|  
|**Gebruik**|`cscript ZTIConfigureDHCP.wsf </debug:value>`|  

#### <a name="arguments"></a>Argumenten  

|**Waarde**|**Beschrijving**|  
|-|-|
|**/ debug: * waarde***|De uitvoer van de event-berichten naar de console en tot de .log-bestanden. Als de waarde die is opgegeven in waarde is:<br /><br /> -                              **De waarde TRUE**, event-berichten worden verzonden naar de console en de .log-bestanden<br /><br /> -                              **ONWAAR**, gebeurtenis berichten worden alleen naar het .log-bestanden (dit is het gedrag wanneer het argument is niet opgegeven.)|  

#### <a name="properties"></a>Eigenschappen  

|**Naam**|**Lezen**|**Schrijven**|  
|-|-|-|  
|**DHCPScopesxDescription**|-||  
|**DHCPScopesxEndIP**|-||  
|**DHCPScopesxExcludeStartIP**|-||  
|**DHCPScopesxExcludeEndIP**|-||  
|**DHCPScopesxIP**|-||  
|**DHCPScopesxName**|-||  
|**DHCPScopesxOptionRouter**|-||  
|**DHCPScopesxOptionDNSDomainName**|-||  
|**DHCPScopesxOptionDNSServer**|-||  
|**DHCPScopesxOptionLease**|-||  
|**DHCPScopesxOptionNBTNodeType**|-||  
|**DHCPScopesxOptionPXEClient**|-||  
|**DHCPScopesxOptionWINSServer**|-||  
|**DHCPScopesxStartIP**|-||  
|**DHCPScopesxSubnetmask**|-||  
|**DHCPServerOptionDNSDomainName**|-||  
|DHCPServerOptionDNSServer|-||  
|**DHCPServerOptionNBTNodeType**|-||  
|**DHCPServerOptionPXEClient**|-||  
|**DHCPServerOptionRouter**|-||  
|**DHCPServerOptionWINSServer**|-||  

> [!NOTE]
>  De *x*in de eigenschappen die worden vermeld dit is een tijdelijke aanduiding voor een op nul gebaseerde matrix met DHCP-configuratie-informatie.  

###  <a name="ZTIConfigureDNS.wsf"></a>ZTIConfigureDNS.wsf  
 Dit script wordt DNS geconfigureerd op de doelcomputer. Het script gebruikt om de werkelijke configuratietaken uitvoeren, het hulpprogramma Dnscmd.  

 Zie voor meer informatie over Dnscmd.exe [Dnscmd overzicht](http://technet.microsoft.com/library/cc778513%28WS.10%29.aspx).  

> [!NOTE]
>  DNS al is geïnstalleerd op de doelcomputer voordat dit script wordt uitgevoerd.  

|**Waarde**|**Beschrijving**|  
|-|-|
|**Invoer**|**Omgevingsvariabelen**. Bevat de eigenschapswaarden, waarden voor aangepaste eigenschappen databaseverbindingen, regels voor implementatie en andere informatie dat de scripts nodig om de implementatieproces te voltooien|  
|**Uitvoer**|-                          **ZTIConfigureDNS.log**. Logboekbestand met gebeurtenissen die dit script genereert<br /><br /> -                          **BDD.log**. Logboekbestand met gebeurtenissen die alle MDT scripts genereren|  
|**Verwijzingen**|-                          **Dnscmd.exe**. Beheerders met DNS-beheer helpt<br /><br /> -                          **ZTIUtility.vbs**. Van ondersteuningsfuncties en subroutines die gebruikmaakt van het script bevat|  
|**Locatie**|*distributie*\Scripts|  
|**Gebruik**|`cscript ZTIConfigureDNS.wsf </debug:value>`|  

#### <a name="arguments"></a>Argumenten  

|**Waarde**|**Beschrijving**|  
|-|-|
|**/ debug: * waarde***|De uitvoer van de event-berichten naar de console en tot de .log-bestanden. Als de waarde die is opgegeven in waarde is:<br /><br /> -                              **De waarde TRUE**, event-berichten worden verzonden naar de console en de .log-bestanden<br /><br /> -                              **ONWAAR**, gebeurtenis berichten worden alleen naar het .log-bestanden (dit is het gedrag wanneer het argument is niet opgegeven.)|  

#### <a name="properties"></a>Eigenschappen  

|**Naam**|**Lezen**|**Schrijven**|  
|-|-|-|  
|**DNSServerOptionDisableRecursion**|-||  
|**DNSServerOptionBINDSecondaries**|-||  
|**DNSServerOptionFailOnLoad**|-||  
|**DNSServerOptionEnableRoundRobin**|-||  
|**DNSServerOptionEnableNetmaskOrdering**|-||  
|**DNSServerOptionEnableSecureCache**|-||  
|**DNSServerOptionNameCheckFlag**|-||  
|**DNSZonesxName**|-||  
|**DNSZonesxType**|-||  
|**DNSZonesxMasterIP**|-||  
|**DNSZonesxDirectoryPartition**|-||  
|**DNSZonesxFileName**|-||  
|**DNSZonesxScavenge**|-||  
|**DNSZonesxUpdate**|-||  

> [!NOTE]
>  De *x*in de eigenschappen die worden vermeld dit is een tijdelijke aanduiding voor een op nul gebaseerde matrix met DNS-configuratie-informatie.  

###  <a name="ZTIConnect.wsf"></a>ZTIConnect.wsf  
 Het implementatieproces MDT gebruikt dit script om te verifiëren met een server-computer (zoals een computer met SQL Server of een andere server met een gedeelde netwerkmap). Wanneer dit script wordt uitgevoerd, valideert dat een verbinding kan worden gemaakt voor de gedeelde netwerkmap opgegeven in de **/uncpath** argument.  

|**Waarde**|**Beschrijving**|  
|-|-|
|**Invoer**|**Omgevingsvariabelen**. Bevat de eigenschapswaarden, waarden voor aangepaste eigenschappen databaseverbindingen, regels voor implementatie en andere informatie dat de scripts nodig om de implementatieproces te voltooien|  
|**Uitvoer**|-                          **ZTIConnect.log**.  Logboekbestand met gebeurtenissen die dit script genereert<br /><br /> -                          **BDD.log**. Logboekbestand met gebeurtenissen die alle MDT scripts genereren|  
|**Verwijzingen**|**ZTIUtility.vbs**. Van ondersteuningsfuncties en subroutines die gebruikmaakt van het script bevat|  
|**Locatie**|*distributie*\Scripts|  
|**Gebruik**|`cscript ZTIConnect.wsf /UNCPath:<uncpath> </debug:value>`|  

#### <a name="arguments"></a>Argumenten  

|**Waarde**|**Beschrijving**|  
|-|-|
|**/UNCPath:uncpath**|Hiermee geeft u een volledig UNC-pad naar een gedeelde netwerkmap|  
|**/ debug: * waarde***|Uitvoer van de event-berichten naar de console en tot de bestanden .log; Als de waarde die is opgegeven in waarde is:<br /><br /> -                              **De waarde TRUE**, event-berichten worden verzonden naar de console en de .log-bestanden<br /><br /> -                              **ONWAAR**, gebeurtenis berichten worden alleen naar het .log-bestanden (dit is het gedrag wanneer het argument is niet opgegeven.)|  

#### <a name="properties"></a>Eigenschappen  

|**Naam**|**Lezen**|**Schrijven**|  
|-|-|-|  
|Geen|||  

###  <a name="ZTICopyLogs.wsf"></a>ZTICopyLogs.wsf  
 Kopieer de bestanden Smsts.log en BDD.log naar een submap onder de share die de **SLShare** -eigenschap geeft op. De submap wordt de naam **OSDComputerName**, **_SMSTSMachineName**, of **hostnaam** bevat.  

|**Waarde**|**Beschrijving**|  
|-|-|
|**Invoer**|**Omgevingsvariabelen**. Bevat de eigenschapswaarden, waarden voor aangepaste eigenschappen databaseverbindingen, regels voor implementatie en andere informatie dat de scripts nodig om de implementatieproces te voltooien|  
|**Uitvoer**|-                          **ZTICopyLogs.log**. Logboekbestand met gebeurtenissen die dit script genereert<br /><br /> -                          **BDD.log**. Logboekbestand met gebeurtenissen die alle MDT scripts genereren|  
|**Verwijzingen**|**ZTIUtility.vbs**. Van ondersteuningsfuncties en subroutines die gebruikmaakt van het script bevat|  
|**Locatie**|*distributie*\Scripts|  
|**Gebruik**|`cscript ZTICopyLogs.wsf </debug:value>`|  

#### <a name="arguments"></a>Argumenten  

|**Waarde**|**Beschrijving**|  
|-|-|
|**/ debug: *waarde***|De uitvoer van de event-berichten naar de console en tot de .log-bestanden. Als de waarde die is opgegeven in waarde is:<br /><br /> -                              **De waarde TRUE**, event-berichten worden verzonden naar de console en de .log-bestanden<br /><br /> -                              **ONWAAR**, gebeurtenis berichten worden alleen naar het .log-bestanden (dit is het gedrag wanneer het argument is niet opgegeven.)|  

#### <a name="properties"></a>Eigenschappen  

|**Naam**|**Lezen**|**Schrijven**|  
|-|-|-|  
|Geen|||  

###  <a name="ZTIDataAccess.vbs"></a>ZTIDataAccess.vbs  
 Dit script bevat algemene routines voor toegang tot de database.  

|**Waarde**|**Beschrijving**|  
|-|-|
|**Invoer**|**Omgevingsvariabelen**. Bevat de eigenschapswaarden, waarden voor aangepaste eigenschappen databaseverbindingen, regels voor implementatie en andere informatie dat de scripts nodig om de implementatieproces te voltooien|  
|**Uitvoer**|-                          **ZTIDataAccess.log**. Logboekbestand met gebeurtenissen die dit script genereert<br /><br /> -                          **BDD.log**. Logboekbestand met gebeurtenissen die alle MDT scripts genereren|  
|**Verwijzingen**|Geen|  
|**Locatie**|*distributie*\Scripts|  
|**Gebruik**|`<script language="VBScript" src="ZTIDataAccess.vbs"/>`|  

#### <a name="arguments"></a>Argumenten  

|**Waarde**|**Beschrijving**|  
|-|-|
|Geen|Geen|  

#### <a name="properties"></a>Eigenschappen  

|**Naam**|**Lezen**|**Schrijven**|  
|-|-|-|  
|**_SMSTSReserved1**|-||  
|**_SMSTSReserved2**|-||  
|**RulesFile**|-||  
|**UserDomain**|-|-|  
|**Gebruikers-id**|-|-|  
|**UserPassword**|-|-|  

###  <a name="ZTIDisableBDEProtectors.wsf"></a>ZTIDisableBDEProtectors.wsf  
 Als BitLocker is ingeschakeld, wordt de BitLocker-protectors geconfigureerd op het systeem onderbroken in dit script.  

|**Waarde**|**Beschrijving**|  
|-|-|
|**Invoer**|**Omgevingsvariabelen**. Bevat de eigenschapswaarden, waarden voor aangepaste eigenschappen databaseverbindingen, regels voor implementatie en andere informatie dat de scripts nodig om de implementatieproces te voltooien|  
|**Uitvoer**|-                          **ZTIDisableBDEProtectors.log**. Logboekbestand met gebeurtenissen die dit script genereert<br /><br /> -                          **BDD.log**. Logboekbestand met gebeurtenissen die alle MDT scripts genereren|  
|**Verwijzingen**|**ZTIUtility.vbs**. Van ondersteuningsfuncties en subroutines die gebruikmaakt van het script bevat|  
|**Locatie**|*distributie*\Scripts|  
|**Gebruik**|`cscript ZTIDisableBDEProtectors.wsf </debug:value>`|  

#### <a name="arguments"></a>Argumenten  

|**Waarde**|**Beschrijving**|  
|-|-|
|**/ debug: * waarde***|De uitvoer van de event-berichten naar de console en tot de .log-bestanden. Als de waarde die is opgegeven in waarde is:<br /><br /> -                              **De waarde TRUE**, event-berichten worden verzonden naar de console en de .log-bestanden<br /><br /> -                              **ONWAAR**, gebeurtenis berichten worden alleen naar het .log-bestanden (dit is het gedrag wanneer het argument is niet opgegeven.)|  

#### <a name="properties"></a>Eigenschappen  

|**Naam**|**Lezen**|**Schrijven**|  
|-|-|-|  
|**ImageBuild**|-||  
|**ISBDE**||-|  
|**OSCurrentBuild**|-||  
|**OSCurrentVersion**|-||  
|**OSVersion**|-||  

###  <a name="ZTIDiskpart.wsf"></a>ZTIDiskpart.wsf  
 Dit script maakt de schijfpartities op de doelcomputer door het aanroepen van het hulpprogramma Diskpart. De parameters gebruikt voor het configureren van de schijf worden opgegeven door de Sequencer taak of in CustomSettings.ini. ZTIDiskpart.wsf wordt voornamelijk in scenario's voor nieuwe Computer uitgevoerd. Het proces werkt als volgt:  

1.  Het implementatieproces MDT voert het ZTIDiskpart.wsf-script op basis van de stappen en de volgorde van de stappen in de Sequencer taak.  

2.  ZTIDiskpart.wsf begint het hulpprogramma Diskpart en verzendt het de vereiste configuratie-opdrachten.  

3.  ZTIDiskpart.wsf Diskpart.exe wordt uitgevoerd en biedt een txt-bestand als een parameter in opdrachtregel.  

4.  De schijf is in eerste instantie opgeschoond door te sturen Diskpart de **SCHOON** opdracht.  

5.  Als dit de eerste schijf en er is geen schijfconfiguratie is opgegeven door de Sequencer taak of in CustomSettings.ini, wordt één partitie gemaakt voor het opslaan van het besturingssysteem. Als de configuratie van een schijf is opgegeven, wordt er echter wel de schijf geconfigureerd volgens de opgegeven configuratie.  

6.  Als BitLocker is ingeschakeld, wordt er ruimte aan het einde van de eerste schijf gereserveerd.  

7.  Alle opdrachten voor indeling in de wachtrij staan totdat nadat Diskpart is voltooid. Als u niet expliciet is opgegeven door de Sequencer taak of in CustomSettings.ini, ZTIDiskpart.wsf een snelle formattering van station C met de volgende opdracht: `FORMAT C: /FS:NTFS /V:OSDisk /Q /Y`.  

8.  ZTIDiskpart.wsf kopieert de bestanden ZTIDiskpart_diskpart.log en BDD.log van de RAM-schijf terug naar de harde schijf.  

 De configuratie van de schijf van de doelcomputer door te geven van de vereiste gegevens in de Sequencer taak of in CustomSettings.ini aanpassen.  

 Zie voor meer informatie over het configureren van schijven, het document MDT *met behulp van de Microsoft Deployment Toolkit*.  

|**Waarde**|**Beschrijving**|  
|-|-|
|**Invoer**|**Omgevingsvariabelen**. Bevat de eigenschapswaarden, waarden voor aangepaste eigenschappen databaseverbindingen, regels voor implementatie en andere informatie dat de scripts nodig om de implementatieproces te voltooien|  
|**Uitvoer**|-                          **ZTIDiskpart.log**. Logboekbestand met gebeurtenissen die dit script genereert<br /><br /> -                          **BDD.log**. Logboekbestand met gebeurtenissen die alle MDT scripts genereren|  
|**Verwijzingen**|-                          **DiskPart.exe**. Hulpprogramma voor het automatisch beheer van schijven, partities en volumes waarmee<br /><br /> -                          **Format.com**. Indelingen van de harde schijf<br /><br /> -                          **ZTIDiskUtility.vbs**. Van ondersteuningsfuncties en subroutines die gebruikmaakt van het script bevat<br /><br /> -                          **ZTIUtility.vbs**. Van ondersteuningsfuncties en subroutines die gebruikmaakt van het script bevat|  
|**Locatie**|*distributie*\Scripts|  
|**Gebruik**|`cscript ZTIDiskpart.wsf </debug:value>`|  

#### <a name="arguments"></a>Argumenten  

|**Waarde**|**Beschrijving**|  
|-|-|
|**/ debug: * waarde***|De uitvoer van de event-berichten naar de console en tot de .log-bestanden. Als de waarde die is opgegeven in waarde is:<br /><br /> -                              **De waarde TRUE**, event-berichten worden verzonden naar de console en de .log-bestanden<br /><br /> -                              **ONWAAR**, gebeurtenis berichten worden alleen naar het .log-bestanden (dit is het gedrag wanneer het argument is niet opgegeven.)|  

#### <a name="properties"></a>Eigenschappen  

|**Naam**|**Lezen**|**Schrijven**|  
|-|-|-|  
|**BDEDriveLetter**|-||  
|**BDEDriveSize**|-||  
|**BDEInstall**|-||  
|**DeployDrive**|-||  
|**DeploymentType**|-||  
|**DestinationDisk**|-||  
|**DestinationLogicalDrive**||-|  
|**DoNotCreateExtraPartition**|-||  
|**ImageBuild**|-||  
|**OSDDiskIndex**|-||  
|**OSDDiskpartBiosCompatibilityMode**|-|-|  
|**OSDDiskType**|-||  
|**OSDPartitions**|-||  
|**OSDPartitionStyle**|-||  
|**SMSTSLocalDataDrive**||-|  
|**VolumeLetterVariable**|-||  

###  <a name="ZTIDiskUtility.vbs"></a>ZTIDiskUtility.vbs  
 Dit script bevat de schijf-gerelateerde functies en subroutines dat de verschillende scripts in de MDT-implementatieshare aanroep verwerken.  

|**Waarde**|**Beschrijving**|  
|-|-|
|**Invoer**|Geen|  
|**Uitvoer**|-                          **ZTIDiskUtility.log**. Logboekbestand met gebeurtenissen die dit script genereert<br /><br /> -                          **BDD.log**. Logboekbestand met gebeurtenissen die alle MDT scripts genereren|  
|**Verwijzingen**|-                          **BcdBoot.exe**. Hiermee configureert u de systeempartitie<br /><br /> -                          **DiskPart.exe**. Hulpprogramma voor het automatisch beheer van schijven, partities en volumes waarmee|  
|**Locatie**|*distributie*\Scripts|  
|**Gebruik**|`<script language="VBScript" src="ZTIDiskUtility.vbs"/>`|  

#### <a name="arguments"></a>Argumenten  

|**Waarde**|**Beschrijving**|  
|-|-|
|Geen|Geen|  

#### <a name="properties"></a>Eigenschappen  

|**Naam**|**Lezen**|**Schrijven**|  
|-|-|-|  
|**DestinationLogicalDrive**|-||  
|**UILanguage**|-|-|  

###  <a name="ZTIDomainJoin.wsf"></a>ZTIDomainJoin.wsf  
 Tijdens de implementatiefase 11statusherstelfase dit script wordt gecontroleerd of de computer is gekoppeld aan een domein wordt hersteld uit de mislukte pogingen toevoegen aan een domein.  

|**Waarde**|**Beschrijving**|  
|-|-|
|**Invoer**|**Omgevingsvariabelen**. Bevat de eigenschapswaarden, waarden voor aangepaste eigenschappen databaseverbindingen, regels voor implementatie en andere informatie dat de scripts nodig om de implementatieproces te voltooien|  
|**Uitvoer**|-                          **ZTIDomainJoin.log**. Logboekbestand met gebeurtenissen die dit script genereert<br /><br /> -                          **BDD.log**. Logboekbestand met gebeurtenissen die alle MDT scripts genereren|  
|**Verwijzingen**|-                          **LTISuspend.wsf**<br /><br /> -                          **ZTIUtility.vbs**. Van ondersteuningsfuncties en subroutines die gebruikmaakt van het script bevat|  
|**Locatie**|*distributie*\Scripts|  
|**Gebruik**|`cscript ZTIDomainJoin.wsf </debug:value>`|  

#### <a name="arguments"></a>Argumenten  

|**Waarde**|**Beschrijving**|  
|-|-|
|**/ debug: *waarde***|De uitvoer van de event-berichten naar de console en tot de .log-bestanden. Als de waarde die is opgegeven in waarde is:<br /><br /> -                              **De waarde TRUE**, event-berichten worden verzonden naar de console en de .log-bestanden<br /><br /> -                              **ONWAAR**, gebeurtenis berichten worden alleen naar het .log-bestanden (dit is het gedrag wanneer het argument is niet opgegeven.)|  
|**/ DomainErrorRecovery: *waarde***|Pogingen om de computer toevoegen aan het domein. Als de waarde die is opgegeven in waarde is:<br /><br /> -                              **AUTOMATISCHE**. Probeer het proces voor de join. Start opnieuw op en probeer het opnieuw. Dit is het standaardgedrag voor het script.<br /><br /> -                              **MISLUKKEN**. De verwerking stopt. Alle task sequence verwerking stopt.<br /><br /> -                              **HANDMATIGE**. Stoppen met het verwerken; kan de gebruiker de computer handmatig toevoegen aan het domein.|  

#### <a name="properties"></a>Eigenschappen  

|**Naam**|**Lezen**|**Schrijven**|  
|-|-|-|  
|**DomainAdmin**|-||  
|**DomainAdminDomain**|-||  
|**DomainAdminPassword**|-||  
|**DomainErrorRecovery**|-||  
|**DomainJoinAttempts**|-|-|  
|**JoinDomain**|-||  
|**JoinWorkgroup kan**|-||  
|**LTISuspend**||-|  
|**MachineObjectOU**|-||  
|**SMSTSRebootRequested**||-|  
|**SMSTSRetryRequested**||-|  

###  <a name="ZTIDrivers.wsf"></a>ZTIDrivers.wsf  
 Dit script wordt extra apparaatstuurprogramma's op de doelcomputer geïnstalleerd voordat u begint de configuratie van het besturingssysteem. Dit script leest het bestand Drivers.xml en wordt de lijst met bestanden van de apparaatstuurprogramma's in het bestand Drivers.xml (gemaakt en beheerd in het knooppunt stuurprogramma's in de implementatie-Workbench) naar de doelcomputer gekopieerd.  

|**Waarde**|**Beschrijving**|  
|-|-|
|**Invoer**|**Omgevingsvariabelen**. Bevat de eigenschapswaarden, waarden voor aangepaste eigenschappen databaseverbindingen, regels voor implementatie en andere informatie dat de scripts nodig om de implementatieproces te voltooien|  
|**Uitvoer**|-                          **PnpEnum.xml**. Bevat een lijst met alle apparaten die zijn geïnstalleerd op de doelcomputer<br /><br /> -                          **ZTIDrivers.log**. Logboekbestand met gebeurtenissen die dit script genereert<br /><br /> -                          **BDD.log**. Logboekbestand met gebeurtenissen die alle MDT scripts genereren|  
|**Verwijzingen**|-                          **Attrib.exe**. Hiermee stelt u kenmerken van bestanden en mappen<br /><br /> -                          **CMD.exe. Hiermee kunt het uitvoeren van opdrachtregelprogramma 's**<br /><br /> -                          **Microsoft.BDD.PnpEnum.exe**. Hulpprogramma voor die inventariseren Plug en Play-apparaten<br /><br /> -                          **Reg.exe**. Het consolehulpprogramma voor het lezen en wijzigen van registergegevens<br /><br /> -                          **ZTIConfigFile.vbs**. Bevat routines voor de verwerking van XML-bestanden<br /><br /> -                          **ZTIUtility.vbs**. Van ondersteuningsfuncties en subroutines die gebruikmaakt van het script bevat|  
|**Locatie**|*distributie*\Scripts|  
|**Gebruik**|`cscript ZTIDrivers.wsf </debug:value>`|  

#### <a name="arguments"></a>Argumenten  

|**Waarde**|**Beschrijving**|  
|-|-|
|**/ debug: * waarde***|De uitvoer van de event-berichten naar de console en tot de .log-bestanden. Als de waarde die is opgegeven in waarde is:<br /><br /> -                              **De waarde TRUE**, event-berichten worden verzonden naar de console en de .log-bestanden<br /><br /> -                              **ONWAAR**, gebeurtenis berichten worden alleen naar het .log-bestanden (dit is het gedrag wanneer het argument is niet opgegeven.)|  

#### <a name="properties"></a>Eigenschappen  

|**Naam**|**Lezen**|**Schrijven**|  
|-|-|-|  
|**Architectuur**|-||  
|**CustomDriverSelectionProfile**|-||  
|**DeploymentMethod**|-||  
|**DeploymentType**|-||  
|**DestinationLogicalDrive**|-|-|  
|**DoCapture**|-||  
|**DriverPaths**|-||  
|**DriverSelectionProfile**|-||  
|**ImageBuild**|-||  
|**InstallFromPath**|-||  
|**OSDAnswerFilePath**|-||  
|**OSDAnswerFilePathSysPrep**|-||  
|**OSDPlatformArch**|-||  
|**Fase**|-||  
|**ResourceRoot**|-||  

###  <a name="ZTIExecuteRunbook.wsf"></a>ZTIExecuteRunbook.wsf  
 Dit script wordt uitgevoerd van Orchestrator-runbooks op de doelcomputer. Een Orchestrator *runbook* is de volgorde van activiteiten die acties op computers en netwerken te organiseren. U kunt de Orchestrator-runbooks bij het gebruik van MDT initiëren de [Runbook uitvoeren](#ExecuteRunbook) task sequence staptype, dat op zijn beurt dit script wordt uitgevoerd.  

|**Waarde**|**Beschrijving**|  
|-|-|
|**Invoer**|Omgevingsvariabelen bevatten de eigenschapswaarden, waarden voor aangepaste eigenschappen databaseverbindingen, regels voor implementatie en andere informatie dat de scripts nodig om de implementatieproces te voltooien.|  
|**Uitvoer**|-BDD.log bevat gebeurtenissen die alle MDT scripts genereren.<br /><br /> -Geretourneerde status van het runbook is voltooid.<br /><br /> -Parameters van de runbookuitvoer geretourneerd.|  
|**Verwijzingen**|-ZTIUtility.vbs omvat voor ondersteuningsfuncties en subroutines die gebruikmaakt van het script.|  
|**Locatie**|*distributie*\Scripts|  
|**Gebruik**|`cscript ZTIExecuteRunbook.wsf </debug:value>`|  

#### <a name="arguments"></a>Argumenten  

|**Waarde**|**Beschrijving**|  
|-|-|
|**/ debug: * waarde***|De uitvoer van de event-berichten naar de console en tot de .log-bestanden. Als de waarde die is opgegeven in waarde is:<br /><br /> -                              **De waarde TRUE**, event-berichten worden verzonden naar de console en de .log-bestanden<br /><br /> -                              **ONWAAR**, gebeurtenis berichten worden alleen naar het .log-bestanden (dit is het gedrag wanneer het argument is niet opgegeven.)|  

#### <a name="properties"></a>Eigenschappen  

|**Naam**|**Lezen**|**Schrijven**|  
|-|-|-|  
|**OrchestratorServer**|-||  
|**RunbookName**|-||  
|**RunbookID**|-||  
|**RunbookParameterMode**|-||  
|**RunbookParametersxParameterID**|-||  
|**RunbookParametersxParameterValue**|-||  
|***RunbookOutputParameters***<br /><br /> Opmerking:<br /><br /> Als een runbook output-parameters retourneert, een takenreeksvariabele wordt gemaakt voor elke parameter en de retourwaarde van de parameter is toegewezen aan de takenreeksvariabele.||-|  

 Dit script maakt de takenreeksvariabelen die worden vermeld in de volgende tabel voor interne script gebruiken. Stel deze takenreeksvariabelen in CustomSettings.ini of in de MDT-database.  

|**Naam**|**Beschrijving**|  
|-|-|  
|**OrchestratorServer**|Naam van de server met Orchestrator opgegeven in **Orchestrator Server** in de [Runbook uitvoeren](#ExecuteRunbook) takenreeksstap|  
|**RunbookName**|Naam van het runbook dat is opgegeven in **Runbook** in de [Runbook uitvoeren](#ExecuteRunbook) takenreeksstap|  
|**RunbookID**|ID die is toegewezen aan het runbook op de Orchestrator-server|  
|**RunbookParametersxParameterID**|ID die is toegewezen aan een specifiek runbook-parameter op de Orchestrator-server|  
|**RunbookParametersxParameterName**|Naam toegewezen aan een specifiek runbook-parameter voor de Orchestrator-server|  
|**RunbookParametersxParameterValue**|Waarde is toegewezen aan een specifiek runbook-parameter voor de Orchestrator-server|  

###  <a name="ZTIGather.wsf"></a>ZTIGather.wsf  
 Dit script worden verzameld voor de eigenschappen en het verwerken van regels waarmee het implementatieproces. De eigenschappen en regels (ook wel bekend als *eigenschappen van lokale*) expliciet worden gedefinieerd in dit script en opgenomen in het bestand ZTIGather.xml, het CustomSettings.ini-bestand en de MDT-DB (gemaakt in de Database-knooppunt in de implementatie Workbench).  

|**Waarde**|**Beschrijving**|  
|-|-|
|**Invoer**|**Omgevingsvariabelen**. Bevat de eigenschapswaarden, waarden voor aangepaste eigenschappen databaseverbindingen, regels voor implementatie en andere informatie dat de scripts nodig om de implementatieproces te voltooien|  
|**Uitvoer**|-                          **ZTIGather.log**. Logboekbestand met gebeurtenissen die dit script genereert<br /><br /> -                          **BDD.log**. Logboekbestand met gebeurtenissen die alle MDT scripts genereren|  
|**Verwijzingen**|-                          **Wpeutil.exe**. Initialiseert de Windows PE en netwerkverbindingen; initieert LTI<br /><br /> -                          **ZTIDataAccess.vbs**. Routines voor toegang tot de database bevat<br /><br /> -                          **ZTIUtility.vbs**. Van ondersteuningsfuncties en subroutines die gebruikmaakt van het script bevat|  
|**Locatie**|*distributie*\Scripts|  
|**Gebruik**|`cscript ZTIGather.wsf </debug:value> </localonly> </inifile:ini_file_name>`|  

#### <a name="arguments"></a>Argumenten  

|**Waarde**|**Beschrijving**|  
|-|-|
|**/ debug: * waarde***|De uitvoer van de event-berichten naar de console en tot de .log-bestanden. Als de waarde die is opgegeven in waarde is:<br /><br /> -                              **De waarde TRUE**, event-berichten worden verzonden naar de console en de .log-bestanden<br /><br /> -                              **ONWAAR**, gebeurtenis berichten worden alleen naar het .log-bestanden (dit is het gedrag wanneer het argument is niet opgegeven.)|  
|**/localOnly**|Retourneert alleen de informatie over de doelcomputer en het huidige besturingssysteem is geïnstalleerd op de doelcomputer; biedt de invoer .ini-bestand niet parseren (opgegeven in de **/inifile** argument); retourneert eigenschappen en regels die zijn opgegeven in het ini-bestand<br /><br /> Als niet wordt opgegeven, retourneert het script informatie over de doelcomputer en het geïnstalleerde besturingssysteem. het ini-bestand wordt geparseerd|  
|**/INIFile:ini_file_name**|Naam en pad van de invoer .ini-bestand met de eigenschappen en regels die worden gebruikt in de implementatie processIf niet is opgegeven, het script wordt de standaardwaarde in CustomSettings.ini|  

#### <a name="properties"></a>Eigenschappen  

|**Naam**|**Lezen**|**Schrijven**|  
|-|-|-|  
|**Alle**|-|-|  

###  <a name="ZTIGroups.wsf"></a>ZTIGroups.wsf  
 Dit script vastgelegd en het lidmaatschap van de lokale groep op de doelcomputer hersteld. Dit script wordt aangeroepen met de**/capture** argument voor de back-up van het groepslidmaatschap van de doelcomputer voordat het besturingssysteem wordt geïmplementeerd. De **CaptureGroups** eigenschap bevat de lijst met groepen die script maakt een back-up. Het script wordt aangeroepen met de**/terugzetbewerking** argument voor het herstellen van het groepslidmaatschap nadat het besturingssysteem is geïmplementeerd. Wanneer u een herstelbewerking uitvoert, wordt het lidmaatschap van alle groepen die back-up gemaakt zijn wanneer het script is uitgevoerd met behulp van hersteld de **/capture** argument.  

> [!NOTE]
>  Bij het herstellen van het lidmaatschap van maakt het script geen doelservers groepen die nog niet bestaan op de doelcomputer. Daarom moet u alle vereiste groepen opnemen in de referentiecomputer bij het opbouwen van het installatiekopiebestand.  

|**Waarde**|**Beschrijving**|  
|-|-|
|**Invoer**|**Omgevingsvariabelen**. Bevat de eigenschapswaarden, waarden voor aangepaste eigenschappen databaseverbindingen, regels voor implementatie en andere informatie dat de scripts nodig om de implementatieproces te voltooien|  
|**Uitvoer**|-                          **ZTIGroups.log**. Logboekbestand met gebeurtenissen die dit script genereert<br /><br /> -                          **BDD.log**. Logboekbestand met gebeurtenissen die alle MDT scripts genereert|  
|**Verwijzingen**|**ZTIUtility.vbs**. Van ondersteuningsfuncties en subroutines die gebruikmaakt van het script bevat|  
|**Locatie**|*distributie*\Scripts|  
|**Gebruik**|`cscript ZTIGroups.wsf </debug:value> </backup> </restore>`|  

#### <a name="arguments"></a>Argumenten  

|**Waarde**|**Beschrijving**|  
|-|-|
|**/ debug: * waarde***|De uitvoer van de event-berichten naar de console en tot de .log-bestanden. Als de waarde die is opgegeven in waarde is:<br /><br /> -                              **De waarde TRUE**, event-berichten worden verzonden naar de console en de .log-bestanden<br /><br /> -                              **ONWAAR**, gebeurtenis berichten worden alleen naar het .log-bestanden (dit is het gedrag wanneer het argument is niet opgegeven.)|  
|**/ Capture**|Back-ups van het groepslidmaatschap van de lokale groepen op de doelcomputer, zoals opgegeven in de **CaptureGroups** eigenschap|  
|**/ Restore**|Het lidmaatschap van de herstelt u de lokale groepen een back-up eerder in het implementatieproces|  

#### <a name="properties"></a>Eigenschappen  

|**Naam**|**Lezen**|**Schrijven**|  
|-|-|-|  
|**CaptureGroups**|-||  
|**Groepen**|-|-|  
|Hostnaam|-||  

###  <a name="ZTILangPacksOnline.wsf"></a>ZTILangPacksOnline.wsf  
 Dit script installeert language packs voor Windows-besturingssystemen.  

|**Waarde**|**Beschrijving**|  
|-|-|
|**Invoer**|**Omgevingsvariabelen**. Bevat de eigenschapswaarden, waarden voor aangepaste eigenschappen databaseverbindingen, regels voor implementatie en andere informatie dat de scripts nodig om de implementatieproces te voltooien|  
|**Uitvoer**|-                          **ZTILangPacksOnline.log**. Logboekbestand met gebeurtenissen die dit script genereert<br /><br /> -                          **BDD.log**. Logboekbestand met gebeurtenissen die alle MDT scripts genereren|  
|**Verwijzingen**|-                          **CMD.exe**. Hiermee kunt het uitvoeren van opdrachtregelprogramma 's<br /><br /> -                          **Lpksetup.exe**. De installatie van taalpakket-hulpprogramma gebruikt voor het toevoegen of verwijderen van taalpakketten<br /><br /> -                          **ZTIUtility.vbs**. Van ondersteuningsfuncties en subroutines die gebruikmaakt van het script bevat|  
|**Locatie**|*distributie*\Scripts|  
|**Gebruik**|`cscript ZTILangPacksOnline.wsf </debug:value>`|  

#### <a name="arguments"></a>Argumenten  

|**Waarde**|**Beschrijving**|  
|-|-|
|**/ debug: * waarde***|De uitvoer van de event-berichten naar de console en tot de .log-bestanden. Als de waarde die is opgegeven in waarde is:<br /><br /> -                              **De waarde TRUE**, event-berichten worden verzonden naar de console en de .log-bestanden<br /><br /> -                              **ONWAAR**, gebeurtenis berichten worden alleen naar het .log-bestanden (dit is het gedrag wanneer het argument is niet opgegeven.)|  

#### <a name="properties"></a>Eigenschappen  

|**Naam**|**Lezen**|**Schrijven**|  
|-|-|-|  
|**Architectuur**|-||  
|**OSVersion**|-||  

###  <a name="ZTIModifyVol.wsf"></a>ZTIModifyVol.wsf  
 Dit script wijzigt een volume om in te stellen de GPT-ID en de kenmerken voor hulpprogramma volumes, dat nodig is voor het maken van Windows RE partities op computers met UEFI. Dit script moet worden aangeroepen als implementeren op computers met UEFI in deze situaties:  

-   Implementaties van LTI waar aangepaste partitiestructuren (volume) worden gemaakt, zoals het maken van vijf partitie in plaats van de standaard vier partities die zijn gemaakt voor gebruik met UEFI typicaly  

-   Alle implementaties van ZTI en UDI  

> [!NOTE]
>  Dit script is bedoeld om alleen worden aangeroepen als maken partities structuren voor gebruik met UEFI. Dit script moet niet worden aangeroepen tijdens het maken van partitiestructuren moet worden gebruikt in implementaties zonder UEFI.  

|**Waarde**|**Beschrijving**|  
|-|-|
|**Invoer**|**Omgevingsvariabelen**. Bevat de eigenschapswaarden, waarden voor aangepaste eigenschappen databaseverbindingen, regels voor implementatie en andere informatie dat de scripts nodig om de implementatieproces te voltooien|  
|**Uitvoer**|BDD.log bevat gebeurtenissen die alle MDT scripts genereren.|  
|**Verwijzingen**|ZTIUtility.vbs omvat voor ondersteuningsfuncties en subroutines die gebruikmaakt van het script.|  
|**Locatie**|*distributie*\Scripts|  
|**Gebruik**|`cscript ZTIModifyVol.wsf /UtilityVol:value </debug:value>`|  

#### <a name="arguments"></a>Argumenten  

|**Waarde**|**Beschrijving**|  
|-|-|
|**/ UtilityVol: * waarde***|Biedt de stationsletter van het volume dat moet worden geconfigureerd voor een partitie Windows RE-hulpprogramma's voor gebruik met computers met UEFI (bijvoorbeeld ' E:')|  
|**/ debug: * waarde***|De uitvoer van de event-berichten naar de console en tot de .log-bestanden. Als de waarde die is opgegeven in waarde is:<br /><br /> -                              **De waarde TRUE**, event-berichten worden verzonden naar de console en de .log-bestanden<br /><br /> -                              **ONWAAR**, gebeurtenis berichten worden alleen naar het .log-bestanden (dit is het gedrag wanneer het argument is niet opgegeven.)|  

#### <a name="properties"></a>Eigenschappen  

|**Naam**|**Lezen**|**Schrijven**|  
|-|-|-|  
|**UtilityVol**|-||  

###  <a name="ZTIMoveStateStore.wsf"></a>ZTIMoveStateStore.wsf  
 Dit script wordt verplaatst van de vastgelegde gebruikersstatus en back-upbestanden naar C:\Windows\Temp\StateStore.  

> [!NOTE]
>  Dit script wordt uitgevoerd alleen bij het implementeren van installatiekopieën van het gebruik van Configuration Manager.  

|**Waarde**|**Beschrijving**|  
|-|-|
|**Invoer**|**Omgevingsvariabelen**. Bevat de eigenschapswaarden, waarden voor aangepaste eigenschappen databaseverbindingen, regels voor implementatie en andere informatie dat de scripts nodig om de implementatieproces te voltooien|  
|**Uitvoer**|-                          **ZTIMoveStateStore.log**. Logboekbestand met gebeurtenissen die dit script genereert<br /><br /> -                          **BDD.log**. Logboekbestand met gebeurtenissen die alle MDT scripts genereren|  
|**Verwijzingen**|**ZTIUtility.vbs**. Van ondersteuningsfuncties en subroutines die gebruikmaakt van het script bevat|  
|**Locatie**|*distributie*\Scripts|  
|**Gebruik**|`cscript ZTIMoveStateStore.wsf </debug:value>`|  

#### <a name="arguments"></a>Argumenten  

|**Waarde**|**Beschrijving**|  
|-|-|
|**/ debug: * waarde***|De uitvoer van de event-berichten naar de console en tot de .log-bestanden. Als de waarde die is opgegeven in waarde is:<br /><br /> -                              **De waarde TRUE**, event-berichten worden verzonden naar de console en de .log-bestanden<br /><br /> -                              **ONWAAR**, gebeurtenis berichten worden alleen naar het .log-bestanden (dit is het gedrag wanneer het argument is niet opgegeven.)|  

#### <a name="properties"></a>Eigenschappen  

|**Naam**|**Lezen**|**Schrijven**|  
|-|-|-|  
|Geen|||  

###  <a name="ZTINextPhase.wsf"></a>ZTINextPhase.wsf  
 Dit script werkt de **fase** eigenschap met de volgende fase in het implementatieproces. De Sequencer taak maakt gebruik van deze fasen om te bepalen van de volgorde waarin elke taak moet worden uitgevoerd. De **fase** eigenschap bevat de volgende waarden:  

-   **VALIDATIE**. Vaststellen of de doelcomputer geschikt is is voor het uitvoeren van de scripts nodig zijn voor het implementatieproces.  

-   **STATECAPTURE**. Sla alle statusmigratiegegevens voordat u het doelbesturingssysteem implementeert.  

-   **PREINSTALL**. Voltooi alle taken die worden uitgevoerd (zoals het maken van nieuwe partities moeten) voordat het beoogde besturingssysteem wordt geïmplementeerd.  

-   **INSTALLEER**. Het beoogde besturingssysteem installeren op de doelcomputer.  

-   **POSTINSTALL**. Voltooi alle taken die worden uitgevoerd moeten vóór de migratie van gebruikersstatusgegevens te herstellen. Deze taken aanpassen het beoogde besturingssysteem voordat u de eerste keer na de implementatie (zoals het installeren van updates of het toevoegen van stuurprogramma's) start de doelcomputer.  

-   **STATERESTORE**. De statusmigratiegegevens opgeslagen tijdens de fase voor het vastleggen van status herstellen.  

 Voor meer informatie over de **fase** eigenschap, Zie het onderwerp in de [eigenschappen](#Properties).  

|**Waarde**|**Beschrijving**|  
|-|-|
|**Invoer**|**Omgevingsvariabelen**. Bevat de eigenschapswaarden, waarden voor aangepaste eigenschappen databaseverbindingen, regels voor implementatie en andere informatie dat de scripts nodig om de implementatieproces te voltooien|  
|**Uitvoer**|-                          **ZTINextPhase.log**. Logboekbestand met gebeurtenissen die dit script genereert<br /><br /> -                          **BDD.log**. Logboekbestand met gebeurtenissen die alle MDT scripts genereren|  
|**Verwijzingen**|**ZTIUtility.vbs**. Van ondersteuningsfuncties en subroutines die gebruikmaakt van het script bevat|  
|**Locatie**|*distributie*\Scripts|  
|**Gebruik**|`cscript ZTINextPhase.wsf </debug:value>`|  

#### <a name="arguments"></a>Argumenten  

|**Waarde**|**Beschrijving**|  
|-|-|
|**/ debug: * waarde***|De uitvoer van de event-berichten naar de console en tot de .log-bestanden. Als de waarde die is opgegeven in waarde is:<br /><br /> -                              **De waarde TRUE**, event-berichten worden verzonden naar de console en de .log-bestanden<br /><br /> -                              **ONWAAR**, gebeurtenis berichten worden alleen naar het .log-bestanden (dit is het gedrag wanneer het argument is niet opgegeven.)|  

#### <a name="properties"></a>Eigenschappen  

|**Naam**|**Lezen**|**Schrijven**|  
|-|-|-|  
|**DeploymentMethod**|-||  
|**Fase**|-|-|  

###  <a name="ZTINICConfig.wsf"></a>ZTINICConfig.wsf  
 Dit script configureert geactiveerde netwerkadapters met waarden die ZTIGather.wsf vastgelegd op basis van de eigenschappen in het CustomSettings.ini-bestand of de MDT-DB (gemaakt in de Database-knooppunt in de Workbench-implementatie).  

|**Waarde**|**Beschrijving**|  
|-|-|
|**Invoer**|**Omgevingsvariabelen**. Bevat de eigenschapswaarden, waarden voor aangepaste eigenschappen databaseverbindingen, regels voor implementatie en andere informatie dat de scripts nodig om de implementatieproces te voltooien|  
|**Uitvoer**|-                          **ZTINICConfig.log**. Logboekbestand met gebeurtenissen die dit script genereert<br /><br /> -                          **BDD.log**. Logboekbestand met gebeurtenissen die alle MDT scripts genereren|  
|**Verwijzingen**|-                          **ZTIUtility.vbs**. Van ondersteuningsfuncties en subroutines die gebruikmaakt van het script bevat<br /><br /> -                          **ZTINicUtility.vbs**. Van ondersteuningsfuncties en subroutines die gebruikmaakt van het script bevat|  
|**Locatie**|*distributie*\Scripts|  
|**Gebruik**|`cscript ZTINicConfig.wsf </debug:value> </ForceCapture> </RestoreWithinWinPE>`|  

#### <a name="arguments"></a>Argumenten  

|**Waarde**|**Beschrijving**|  
|-|-|
|**/ debug: * waarde***|De uitvoer van de event-berichten naar de console en tot de .log-bestanden. Als de waarde die is opgegeven in waarde is:<br /><br /> -                              **De waarde TRUE**, event-berichten worden verzonden naar de console en de .log-bestanden<br /><br /> -                              **ONWAAR**, gebeurtenis berichten worden alleen naar het .log-bestanden (dit is het gedrag wanneer het argument is niet opgegeven.)|  
|**/ ForceCapture**|Als er lokale netwerken adapters met statische IP-adressen die zijn opgeslagen, dit script worden vastgelegd die instellingen en slaat u ze in de lokale omgeving — bijvoorbeeld C:\MININT\SMSOSD\OSDLogs\Variables.dat. Dit script kan nuttig zijn bij het vastleggen van statische IP-instellingen voor een groot aantal computers voor automatisering.|  
|/ RestoreWithinWinPE|Wanneer wordt opgegeven, is van toepassing eventuele opgeslagen statische IP-netwerkinstellingen op de lokale computer, indien van toepassing; gebruikt voor het interne verwerken alleen.|  

#### <a name="properties"></a>Eigenschappen  

|**Naam**|**Lezen**|**Schrijven**|  
|-|-|-|  
|**DeployDrive**|-|-|  
|**DeploymentMethod**|-||  
|**DeploymentType**|-||  
|**DeployRoot**|-||  
|**OSDAdapterCount**|-|-|  
|**OSGuid**|-||  
|**OSDMigrateAdapterSettings**|-||  
|**Fase**|-||  

###  <a name="ZTINICUtility.vbs"></a>ZTINICUtility.vbs  
 Dit script bevat de netwerk-adapter gerelateerde functies en subroutines dat de verschillende scripts in de MDT-implementatieshare aanroep verwerken.  

|**Waarde**|**Beschrijving**|  
|-|-|
|**Invoer**|Geen|  
|**Uitvoer**|Geen|  
|**Verwijzingen**|-                          **CMD.exe**. Hiermee kunt het uitvoeren van opdrachtregelprogramma 's<br /><br /> -                          **Netsh.exe**. Een hulpprogramma waarmee u kunt de configuratie van netwerkonderdelen automatiseren|  
|**Locatie**|*distributie*\Scripts|  
|**Gebruik**|`<script language="VBScript" src="ZTINicUtility.vbs"/>`|  

#### <a name="arguments"></a>Argumenten  

|**Waarde**|**Beschrijving**|  
|-|-|
|Geen|Geen|  

#### <a name="properties"></a>Eigenschappen  

|**Naam**|**Lezen**|**Schrijven**|  
|-|-|-|  
|**OSDAdapter * AdapterIndexAdapterName***|-|-|  

> [!NOTE]
>  *AdapterIndex*in deze eigenschap is een tijdelijke aanduiding voor een op nul gebaseerde matrix die netwerkadapterinformatie bevat.  

###  <a name="ZTIOSRole.wsf"></a>ZTIOSRole.wsf  
 Dit script installeert serverfuncties voor doelcomputers die Windows-besturingssystemen worden uitgevoerd. Het script leest het **OSRoles**, **OSRoleServices**, en **OSFeatures** eigenschappen om te bepalen wat moet worden geïnstalleerd.  

> [!NOTE]
>  Dit script is bedoeld om te worden aangeroepen door alleen de **Installeer functies en onderdelen** en**verwijderen van functies en onderdelen** takenreeksstappen. Dit script rechtstreeks aanroepen wordt niet ondersteund.  

|**Waarde**|**Beschrijving**|  
|-|-|
|**Invoer**|**Omgevingsvariabelen**. Bevat de eigenschapswaarden, waarden voor aangepaste eigenschappen databaseverbindingen, regels voor implementatie en andere informatie dat de scripts nodig om de implementatieproces te voltooien|  
|**Uitvoer**|-                          **ZTIOSRole.log**. Logboekbestand met gebeurtenissen die dit script genereert<br /><br /> -                          **BDD.log**. Logboekbestand met gebeurtenissen die alle MDT scripts genereren|  
|**Verwijzingen**|-                          **CMD.exe**. Hiermee kunt het uitvoeren van opdrachtregelprogramma 's<br /><br /> -                          **OCSetup.exe**. Hiermee voegt u toe of verwijdert optionele Windows-onderdelen<br /><br /> -                          **ServerManagerCmd.exe**. Wordt geïnstalleerd, configureert en beheert de Windows Server-functies en onderdelen<br /><br /> -                          **Sysocmgr.exe**. Toevoegen of verwijderen van Windows-onderdelen<br /><br /> -                          **ZTIUtility.vbs**. Van ondersteuningsfuncties en subroutines die gebruikmaakt van het script bevat|  
|**Locatie**|*distributie*\Scripts|  
|**Gebruik**|`cscript ZTIOSRole.wsf </debug:value>`|  

#### <a name="arguments"></a>Argumenten  

|**Waarde**|**Beschrijving**|  
|-|-|
|**/ debug: * waarde***|De uitvoer van de event-berichten naar de console en tot de .log-bestanden. Als de waarde die is opgegeven in waarde is:<br /><br /> -                              **De waarde TRUE**, event-berichten worden verzonden naar de console en de .log-bestanden<br /><br /> -                              **ONWAAR**, gebeurtenis berichten worden alleen naar het .log-bestanden (dit is het gedrag wanneer het argument is niet opgegeven.)|  
|**Of het verwijderen**|Indien opgegeven, wordt dit argument geeft aan dat de functies en onderdelen wordt ongedaan gemaakt. Als niet wordt opgegeven, het script wordt ervan uitgegaan dat de rollen en functies worden geïnstalleerd.|  

#### <a name="properties"></a>Eigenschappen  

|**Naam**|**Lezen**|**Schrijven**|  
|-|-|-|  
|**IsServerCoreOS**|-||  
|**OSFeatures**|-||  
|**OSRoles**|-||  
|**OSRoleServices**|-||  
|**OSVersion**|-||  
|**SMSTSRebootRequested**||-|  

###  <a name="ZTIPatches.wsf"></a>ZTIPatches.wsf  
 Dit script worden updates geïnstalleerd (taalpakketten, beveiligingsupdates, enzovoort) die worden vermeld in het bestand Packages.xml. Het script eindigt zelf als de implementatie bevindt zich niet in een van de volgende statussen:  

-   **Fase** gelijk is aan **PREINSTALL**  

-   **DeploymentMethod** gelijk is aan **SCCM**  

 Het script Pkgmgr begint als **DeploymentMethod** gelijk is aan **SCCM**.  

|**Waarde**|**Beschrijving**|  
|-|-|
|**Invoer**|**Omgevingsvariabelen**. Bevat de eigenschapswaarden, waarden voor aangepaste eigenschappen databaseverbindingen, regels voor implementatie en andere informatie dat de scripts nodig om de implementatieproces te voltooien|  
|**Uitvoer**|-                          **ZTIPatches.log**. Logboekbestand met gebeurtenissen die dit script genereert<br /><br /> -                          **BDD.log**. Logboekbestand met gebeurtenissen die alle MDT scripts genereren|  
|**Verwijzingen**|-                          **Expand.exe**. Gecomprimeerde bestanden worden uitgevouwen<br /><br /> -                          **Pkgmgr.exe**. Wordt geïnstalleerd of Windows Vista offline-updates<br /><br /> -                          **ZTIConfigFile.vbs**. Bevat routines voor de verwerking van XML-bestanden<br /><br /> -                          **ZTIUtility.vbs**. Van ondersteuningsfuncties en subroutines die gebruikmaakt van het script bevat|  
|**Locatie**|*distributie*\Scripts|  
|**Gebruik**|`cscript ZTIPatches.wsf </debug:value>`|  

#### <a name="arguments"></a>Argumenten  

|**Waarde**|**Beschrijving**|  
|-|-|
|**/ debug: * waarde***|De uitvoer van de event-berichten naar de console en tot de .log-bestanden. Als de waarde die is opgegeven in waarde is:<br /><br /> -                              **De waarde TRUE**, event-berichten worden verzonden naar de console en de .log-bestanden<br /><br /> -                              **ONWAAR**, gebeurtenis berichten worden alleen naar het .log-bestanden (dit is het gedrag wanneer het argument is niet opgegeven.)|  

#### <a name="properties"></a>Eigenschappen  

|**Naam**|**Lezen**|**Schrijven**|  
|-|-|-|  
|**Architectuur**|-||  
|**CustomPackageSelectionProfile**|-||  
|**DeployRoot**|-||  
|**DeploymentMethod**|-||  
|**DeploymentType**|-||  
|**DestinationLogicalDrive**|-||  
|**LanguagePacks**|-||  
|**OSDAnswerFilePath**|-||  
|**OSDPlatformArch**|-||  
|**PackageSelectionProfile**|-||  
|**Fase**|-||  
|**ResourceRoot**|-||  

###  <a name="ZTIPowerShell.wsf"></a>ZTIPowerShell.wsf  
 Dit script wordt uitgevoerd van Windows PowerShell-script met behulp van een aangepaste host met Windows PowerShell.  

|**Waarde**|**Beschrijving**|  
|-|-|
|**Invoer**|**Omgevingsvariabelen**. Bevat de eigenschapswaarden, waarden voor aangepaste eigenschappen databaseverbindingen, regels voor implementatie en andere informatie dat de scripts nodig om de implementatieproces te voltooien|  
|**Uitvoer**|-                          **ZTIPowerShell.log**. Logboekbestand met gebeurtenissen die dit script genereert<br /><br /> -                          **BDD.log**. Logboekbestand met gebeurtenissen die alle MDT scripts genereren<br /><br /> -                          **Retourcode**. De numerieke waarde geretourneerd door de Windows PowerShell-script na voltooiing wordt de voltooiingsstatus van het script geeft.|  
|**Verwijzingen**|-                          **Microsoft.BDD.TaskSequencePSHost.exe**. Aangepaste Windows PowerShell-host gebruikt voor het uitvoeren van de Windows PowerShell-script.|  
|**Locatie**|*distributie*\Scripts|  
|**Gebruik**|`cscript ZTIPowerShell.wsf`|  

#### <a name="arguments"></a>Argumenten  

|**Waarde**|**Beschrijving**|  
|-|-|
|**Geen**||  

#### <a name="properties"></a>Eigenschappen  

|**Naam**|**Lezen**|**Schrijven**|  
|-|-|-|  
|**Geen**|||  

###  <a name="ZTIPrereq.vbs"></a>ZTIPrereq.vbs  
 Dit script wordt gecontroleerd dat de doelcomputer de vereiste software is geïnstalleerd heeft en of het functioneel is. Er zijn de controles van die het script wordt uitgevoerd:  

-   Bepalen of de versie van Windows-Script gelijk aan of groter dan de versie 5.6 is.  

-   Controleer of dat er geen fouten optreden wanneer objectverwijzingen naar instantie, Wscript.Network, Scripting.FileSystemObject MSXML2 worden geïnstantieerd. DOMDocument en de proces-omgeving.  

 Als een van de controles mislukt, een foutmelding wordt gegenereerd en het script wordt afgesloten de **ValidatePrereq** procedure.  

|**Waarde**|**Beschrijving**|  
|-|-|
|**Invoer**|Geen|  
|**Uitvoer**|Geen|  
|**Verwijzingen**|Geen|  
|**Locatie**|*distributie*\Scripts|  
|**Gebruik**|`None`|  

#### <a name="arguments"></a>Argumenten  

|**Waarde**|**Beschrijving**|  
|-|-|
|Geen|Geen|  

#### <a name="properties"></a>Eigenschappen  

|**Naam**|**Lezen**|**Schrijven**|  
|-|-|-|  
|Geen|||  

###  <a name="ZTISCCM.wsf"></a>ZTISCCM.wsf  
 Dit script initialiseert ZTI bij het implementeren met Configuration Manager. Het script voert de volgende procedure:  

1.  Als u foutopsporing is geactiveerd, maakt het script de OSD. Fouten opsporen in bestand.  

2.  Het script het configureren van deze eigenschappen:  

    -   **ScriptRoot**is ingesteld op de bovenliggende map van het script dat wordt uitgevoerd.  

    -   **DeployRoot** is ingesteld op de bovenliggende map van **ScriptRoot**.  

    -   **ResourceRoot** is ingesteld op **DeployRoot**.  

    -   **DeploySystemDrive** is ingesteld op **C:**.  

    -   **DeploymentMethod** is ingesteld op **SCCM**.  

3.  Wanneer **DeployRoot**bevat **:\\***:*  

    -   De **DeployRoot** map wordt gekopieerd naar **_SMSTSMDataPath**\WDPackage  

    -   **ScriptRoot** is ingesteld op **_SMSTSMDataPath**\WDPackage\Scripts  

    -   **DeployRoot** is ingesteld op de bovenliggende map van **ScriptRoot**  

    -   **ResourceRoot** is ingesteld op **DeployRoot**  

4.  Wanneer **fase** is **NULL**:  

    -   Als de omgevingsvariabele % SystemDrive % **X:**, klikt u vervolgens **DeploymentType**is ingesteld op **NEWCOMPUTER** en **fase** is ingesteld op **PREINSTALL**. Anders**DeploymentType** is ingesteld op **vervangen** en **fase** is ingesteld op **validatie**.  

    -   Als de **OldComputer**.tag-bestand aanwezig is op de bovenliggende map van het huidige script uitgevoerd **DeploymentType** is ingesteld op **vervangen** en **fase**is ingesteld op **validatie**. Anders**DeploymentType** is ingesteld op **vernieuwen** en **fase** is ingesteld op **validatie**.  

 Zie voor meer informatie over deze eigenschappen de corresponderende onderwerpen in [eigenschappen](#Properties).  

|**Waarde**|**Beschrijving**|  
|-|-|
|**Invoer**|**Omgevingsvariabelen**. Bevat de eigenschapswaarden, waarden voor aangepaste eigenschappen databaseverbindingen, regels voor implementatie en andere informatie dat de scripts nodig om de implementatieproces te voltooien|  
|**Uitvoer**|-                          **ZTISCCM.log**. Logboekbestand met gebeurtenissen die dit script genereert<br /><br /> -                          **BDD.log**. Logboekbestand met gebeurtenissen die alle MDT scripts genereren|  
|**Verwijzingen**|**ZTIUtility.vbs**. Van ondersteuningsfuncties en subroutines die gebruikmaakt van het script bevat|  
|**Locatie**|*distributie*\Scripts|  
|**Gebruik**|`cscript ZTISCCM.wsf </debug:value>`|  

#### <a name="arguments"></a>Argumenten  

|**Waarde**|**Beschrijving**|  
|-|-|
|**/ debug: * waarde***|De uitvoer van de event-berichten naar de console en tot de .log-bestanden. Als de waarde die is opgegeven in waarde is:<br /><br /> -                              **De waarde TRUE**, event-berichten worden verzonden naar de console en de .log-bestanden<br /><br /> -                              **ONWAAR**, gebeurtenis berichten worden alleen naar het .log-bestanden (dit is het gedrag wanneer het argument is niet opgegeven.)|  

#### <a name="properties"></a>Eigenschappen  

|**Naam**|**Lezen**|**Schrijven**|  
|-|-|-|  
|**_SMSTSMDataPath**|-||  
|**Architectuur**|-||  
|**BDDPackageID**|-|-|  
|**DeploymentMethod**|-|-|  
|**DeploymentType**|-|-|  
|**DeployRoot**|-|-|  
|**Fase**|-|-|  
|**ResourceRoot**|-|-|  
|**ScriptRoot**|-|-|  
|**ToolRoot**|-|-|  

###  <a name="ZTISetVariable.wsf"></a>ZTISetVariable.wsf  
 Dit script wordt de opgegeven globale takenreeksvariabele die overeenkomt met op de naam die is opgenomen in **VariableName** op de waarde die is opgenomen in **VariableValue**.  

|**Waarde**|**Beschrijving**|  
|-|-|
|**Invoer**|**Omgevingsvariabelen**. Bevat de eigenschapswaarden, waarden voor aangepaste eigenschappen databaseverbindingen, regels voor implementatie en andere informatie dat de scripts nodig om de implementatieproces te voltooien|  
|**Uitvoer**|-                          **ZTISetVariable.log**. Logboekbestand met gebeurtenissen die dit script genereert<br /><br /> -                          **BDD.log**. Logboekbestand met gebeurtenissen die alle MDT scripts genereren|  
|**Verwijzingen**|**ZTIUtility.vbs**. Van ondersteuningsfuncties en subroutines die gebruikmaakt van het script bevat|  
|**Locatie**|*distributie*\Scripts|  
|**Gebruik**|`cscript ZTISetVariable.wsf </debug:value>`|  

#### <a name="arguments"></a>Argumenten  

|**Waarde**|**Beschrijving**|  
|-|-|
|**/ debug: * waarde***|De uitvoer van de event-berichten naar de console en tot de .log-bestanden. Als de waarde die is opgegeven in waarde is:<br /><br /> -                              **De waarde TRUE**, event-berichten worden verzonden naar de console en de .log-bestanden<br /><br /> -                              **ONWAAR**, gebeurtenis berichten worden alleen naar het .log-bestanden (dit is het gedrag wanneer het argument is niet opgegeven.)|  

#### <a name="properties"></a>Eigenschappen  

|**Naam**|**Lezen**|**Schrijven**|  
|-|-|-|  
|**Variabelenaam**|-||  
|**VariableValue**|-||  

###  <a name="ZTITatoo.wsf"></a>ZTITatoo.wsf  
 Dit script tattoos de doelcomputer met identificatie- en versie-informatie. Het script voert de volgende procedure:  

1.  Zoek en kopieer het bestand ZTITatoo.mof naar de map %SystemRoot%\System32\Wbem. Eventuele bestaande ZTITatoo.mof die op het doel bestaat worden, verwijderd voordat u begint de kopieerbewerking.  

2.  Mofcomp.exe wordt uitgevoerd met de volgende opdracht:  

    ```  
    %SystemRoot%\System32\Wbem\Mofcomp.exe -autorecover %SystemRoot%\System32\Wbem\ZTITatoo.mof.  
    ```  

3.  Voor alle implementatiemethoden (LTI, ZTI en UDI), de details van deze implementatie zijn geschreven voor alle methoden voor het implementeren in het register op **HKEY_LOCAL_MACHINE\Software\Microsoft\Deployment 4**:  

    -   **Implementatiemethode** is ingesteld op de implementatiemethode die wordt gebruikt en kan worden ingesteld op **LTI**, **ZTI**, of **UDI**, afhankelijk van de implementatie-methode wordt uitgevoerd.  

    -   **Implementatiebron** is ingesteld op de bron voor de implementatie en kan worden ingesteld op **OEM**, **MEDIA**, of de waarde in de **DeploymentMethod** eigenschap.  

    -   **Implementatietype** is ingesteld op de **DeploymentType** eigenschap.  

    -   **Implementatie tijdstempel** is ingesteld op de huidige datum in de WMI-datumnotatie.  

    -   **Deployment Toolkit versie** is ingesteld op de **versie** eigenschap.  

4.  Voor implementaties van LTI, de details van deze implementatie zijn geschreven in het register op **HKEY_LOCAL_MACHINE\Software\Microsoft\Deployment 4**:  

    -   **Taak-ID-reeks** is ingesteld op de **TaskSequenceID**eigenschap.  

    -   **Naam van de taak** is ingesteld op de **TaskSequenceName** eigenschap.  

    -   **Task Sequence versie** is ingesteld op de **TaskSequenceVersion** eigenschap.  

5.  Voor alle implementaties van Configuration Manager (ZTI en UDI voor Configuration Manager), de details van deze implementatie zijn geschreven in het register op **HKEY_LOCAL_MACHINE\Software\Microsoft\Deployment 4**:  

    -   OSD-pakket-ID is ingesteld op de **_SMSTSPackageID** takenreeksvariabele.  

    -   **De naam van de OSD-programma** is altijd ingesteld op '**\***'.  

    -   **OSD advertentie-ID** is ingesteld op de **_SMSTSAdvertID** takenreeksvariabele.  

6.  Voor implementaties van LTI waar een installatiekopie wordt vastgelegd, de details van deze implementatie zijn geschreven in het register op **HKEY_LOCAL_MACHINE\Software\Microsoft\Deployment 4**:  

    -   **Methode vastleggen** is ingesteld op de implementatiemethode die wordt gebruikt en kan worden ingesteld op **LTI**, **ZTI**, of **UDI**, afhankelijk van de implementatie-methode wordt uitgevoerd.  

    -   **Tijdstempel vastleggen** is ingesteld op de huidige datum in de WMI-datumnotatie.  

    -   **Versie van de Toolkit vastleggen** is ingesteld op de **versie** eigenschap.  

    -   **Volgorde-ID voor taak vastleggen** is ingesteld op de **TaskSequenceID**eigenschap.  

    -   **Naam op van Takenreeks vastleggen** is ingesteld op de **TaskSequenceName** eigenschap.  

    -   **Taak Sequence versie vastleggen** is ingesteld op de **TaskSequenceVersion** eigenschap.  

7.  Voor alle Configuration Manager-implementaties (ZTI en UDI voor Configuration Manager) waarin een installatiekopie wordt vastgelegd, de details van deze implementatie zijn geschreven in het register op **HKEY_LOCAL_MACHINE\Software\Microsoft\Deployment 4** :  

    -   **De pakket-ID OSD vastleggen** is ingesteld op de **_SMSTSPackageID** takenreeksvariabele.  

    -   **Vastleggen van de naam van de OSD-programma** is altijd ingesteld op ' *** '.  

    -   **Vastleggen van OSD advertentie-ID** is ingesteld op de **_SMSTSAdvertID**takenreeksvariabele.  

    > [!NOTE]
    >  Dit script is niet ontworpen om uit te voeren op Windows PE.  

|**Waarde**|**Beschrijving**|  
|-|-|
|**Invoer**|**Omgevingsvariabelen**. Bevat de eigenschapswaarden, waarden voor aangepaste eigenschappen databaseverbindingen, regels voor implementatie en andere informatie dat de scripts nodig om de implementatieproces te voltooien|  
|**Uitvoer**|-                          **ZTITatoo.log**. Logboekbestand met gebeurtenissen die dit script genereert<br /><br /> -                          **BDD.log**. Logboekbestand met gebeurtenissen die alle MDT scripts genereren|  
|**Verwijzingen**|-                          **Mofcomp.exe**. Opdrachtregelprogramma MOF-bestand compiler<br /><br /> -                          **ZTIUtility.vbs**. Van ondersteuningsfuncties en subroutines die gebruikmaakt van het script bevat|  
|**Locatie**|*distributie*\Scripts|  
|**Gebruik**|`cscript ZTITatoo.wsf </debug:value>`|  

#### <a name="arguments"></a>Argumenten  

|**Waarde**|**Beschrijving**|  
|-|-|
|**/ debug: * waarde***|De uitvoer van de event-berichten naar de console en tot de .log-bestanden. Als de waarde die is opgegeven in waarde is:<br /><br /> -                              **De waarde TRUE**, event-berichten worden verzonden naar de console en de .log-bestanden<br /><br /> -                              **ONWAAR**, gebeurtenis berichten worden alleen naar het .log-bestanden (dit is het gedrag wanneer het argument is niet opgegeven.)|  

#### <a name="properties"></a>Eigenschappen  

|**Naam**|**Lezen**|**Schrijven**|  
|-|-|-|  
|**_SMSTSAdvertID**|-||  
|**_SMSTSPackageID**|-||  
|**_SMSTSSiteCode**|-||  
|**DeploymentMethod**|-||  
|**DeploymentType**|-||  
|**Versie**|-||  
|**TaskSequenceID**|-||  
|**TaskSequenceName**|-||  
|**TaskSequenceVersion**|-||  

###  <a name="ZTIUserState.wsf"></a>ZTIUserState.wsf  
 Dit script initialiseert de USMT voor het vastleggen en herstellen van gebruikersstatus op de doelcomputer.  

|**Waarde**|**Beschrijving**|  
|-|-|
|**Invoer**|**Omgevingsvariabelen**. Bevat de eigenschapswaarden, waarden voor aangepaste eigenschappen databaseverbindingen, regels voor implementatie en andere informatie dat de scripts nodig om de implementatieproces te voltooien|  
|**Uitvoer**|-                          **ZTIUserState.log**. Logboekbestand met gebeurtenissen die dit script genereert<br /><br /> -                          **BDD.log**. Logboekbestand met gebeurtenissen die alle MDT scripts genereren|  
|**Verwijzingen**|-                          **CMD.exe**. Hiermee kunt het uitvoeren van opdrachtregelprogramma 's<br /><br /> -                          **Loadstate.exe**. Deposito's gebruikersstatusgegevens op een doelcomputer<br /><br /> -                          **Msiexec.exe**. Beheert de installatie van het .msi-toepassingen<br /><br /> -                          **Scanstate.exe**. Gebruikersgegevens en instellingen worden verzameld<br /><br /> -                          **USMT toepassingsbestanden**<br /><br /> -                          **ZTIUtility.vbs**. Van ondersteuningsfuncties en subroutines die gebruikmaakt van het script bevat|  
|**Locatie**|*distributie*\Scripts|  
|**Gebruik**|`cscript ZTIUserState.wsf </debug:value>`|  

#### <a name="arguments"></a>Argumenten  

|**Waarde**|**Beschrijving**|  
|-|-|
|/Debug:Value|De uitvoer van de event-berichten naar de console en tot de .log-bestanden. Als de waarde die is opgegeven in waarde is:<br /><br /> -                              **De waarde TRUE**, event-berichten worden verzonden naar de console en de .log-bestanden<br /><br /> -                              **ONWAAR**, gebeurtenis berichten worden alleen naar het .log-bestanden (dit is het gedrag wanneer het argument is niet opgegeven.)|  
|**/ Vastleggen**|:|  
|**/ Schatting**|:|  
|**En maken terugzetten**|:|  

#### <a name="properties"></a>Eigenschappen  

|**Naam**|**Lezen**|**Schrijven**|  
|-|-|-|  
|**Architectuur**|-||  
|**DeploymentMethod**|-||  
|**DeploymentType**|-||  
|**DestinationLogicalDrive**|-||  
|**ImageBuild**|-||  
|**ImageSize**|-||  
|**ImageSizeMultiplier**|-||  
|**InstallFromPath**|-||  
|**IsServerOS**|-||  
|**LoadStateArgs**|-||  
|**OSCurrentVersion**|-||  
|**OSDMigrateAdditionalCaptureOptions**|-|-|  
|**OSDMigrateAdditionalRestoreOptions**|-|-|  
|**OSDPackagePath**|-||  
|**OSDStateStorePath**||-|  
|**OSVersion**|-||  
|**ScanStateArgs**|-||  
|**StatePath**|-|-|  
|**UDDir**|-||  
|**UDProfiles**|-||  
|**UDShare**|-||  
|**UserDataLocation**|-|-|  
|**USMTConfigFile**|-||  
|**USMTEstimate**|-|-|  
|**USMTLocal**||-|  
|**USMTMigFiles**|-||  

###  <a name="ZTIUtility.vbs"></a>ZTIUtility.vbs  
 Dit script bevat hulpprogrammafuncties die de meeste van de MDT-scripts gebruiken.  

|**Waarde**|**Beschrijving**|  
|-|-|
|**Invoer**|**Omgevingsvariabelen**. Bevat de eigenschapswaarden, waarden voor aangepaste eigenschappen databaseverbindingen, regels voor implementatie en andere informatie dat de scripts nodig om de implementatieproces te voltooien|  
|**Uitvoer**|Geen|  
|**Verwijzingen**|-                          **Credentials_ENU.XML**. Vraagt de gebruiker om referenties op die wordt gebruikt bij het verbinding maken met netwerkbronnen<br /><br /> -                          **IPConfig.exe**. Geeft alle huidige configuratiewaarden voor TCP/IP-netwerk en wordt vernieuwd DHCP en DNS-instellingen<br /><br /> -                          **MSHTA.exe**. HTML-toepassingshost<br /><br /> -                          **Regsvr32.exe**. Registreert de bestanden (.exe .dll .ocx en enzovoort) met het besturingssysteem<br /><br /> -                          **Xcopy.exe**. Kopieert bestanden en mappen, inclusief submappen|  
|**Locatie**|-                          *distributie*\Scripts<br /><br /> -                          *program_files*\Microsoft Deployment Toolkit\Scripts|  
|**Gebruik**|`<script language="VBScript" src="ZTIUtility.vbs"/>`|  

#### <a name="arguments"></a>Argumenten  

|**Waarde**|**Beschrijving**|  
|-|-|
|Geen|Geen|  

#### <a name="properties"></a>Eigenschappen  

|**Naam**|**Lezen**|**Schrijven**|  
|-|-|-|  
|**_SMSTSAdvertID**|-||  
|**_SMSTSCurrentActionName**|-||  
|**_SMSTSCustomProgressDialogMessage**|-||  
|**_SMSTSInstructionTableSize**|-||  
|**_SMSTSLogPath**|-||  
|**_SMSTSMachineName**|-||  
|**_SMSTSNextInstructionPointer**|-||  
|**_SMSTSOrgName**|-||  
|**_SMSTSPackageID**|-||  
|**_SMSTSPackageName**|-||  
|**_SMSTSPackagePath**|-||  
|**_SMSTSReserved1**|-||  
|**_SMSTSReserved2**|-||  
|**Architectuur**|-||  
|**AssetTag**|-||  
|**Computernaam**|-||  
|**Fouten opsporen**|-|-|  
|**DeploymentMethod**|-||  
|**DeployRoot**|-||  
|**DestinationDisk**|-|-|  
|**DestinationLogicalDrive**|-|-|  
|**DestinationPartition**|-|-|  
|**EventShare**|-||  
|**Hostnaam**|-||  
|**ImageBuild**|-|-|  
|**ImageFlags**||-|  
|**Installatiekopie_index**||-|  
|**ImageLanguage**||-|  
|**ImageProcessor**||-|  
|**ImageSize**||-|  
|**InstallFromPath**||-|  
|**JoinDomain**|-||  
|**LogPath**|-|-|  
|**MAC-adres**|-||  
|**OSCurrentVersion**|-||  
|**OSDAdvertID**|-||  
|**OSDAnswerFilePath**|-|-|  
|**OSDAnswerFilePathSysprep**|-|-|  
|**OSDComputerName**|-|-|  
|**OSDPackageID**|-||  
|**OSDPackagePath**|-||  
|**OSDTargetSystemDrive**|-||  
|**OSGUID**||-|  
|**OSSKU**|-||  
|**OSVersion**|-||  
|**Fase**|-||  
|**Processor_Architecture**|-||  
|**ResourceRoot**|-||  
|**SLShare**|-||  
|**SLShareDynamicLogging**|-||  
|**TaskSequenceID**|-||  
|**TaskSequenceName**||-|  
|**TaskSequenceVersion**||-|  
|**UDDir**|-||  
|**UDShare**|-||  
|**UserDomain**|-|-|  
|**Gebruikers-id**|-|-|  
|**UserPassword**|-|-|  
|**UUID**|-||  
|**Versie**<br /><br /> **Opmerking:** Deze variabele is een interne variabele die staat voor de versie van MDT.|-|-|  
|**WDSServer**|-||  

###  <a name="ZTIValidate.wsf"></a>ZTIValidate.wsf  
 Dit script zorgt ervoor dat het veilig voor de implementatie om door te gaan door het valideren van de voorwaarde van de doelcomputer is. De script-processen zijn:  

-   Als **DeploymentType** gelijk is aan vernieuwen en de doelcomputer is een server, het script wordt afgesloten.  

-   Als **OSInstall** bestaat en is niet gelijk aan Ja, het script wordt afgesloten.  

-   Controleer of de minimale hoeveelheid RAM-geheugen op de doelcomputer; Als dat niet het geval is, wordt het script wordt afgesloten.  

-   Controleren of de processor voldoet aan de minimale vereiste snelheid; Als dat niet het geval is, wordt het script wordt afgesloten.  

-   Controleren of de grootte van de harde schijf voldoet aan de minimale grootte vereisten; Als dat niet het geval is, wordt het script wordt afgesloten.  

-   Controleren of het besturingssysteem van de doelcomputer is geïnstalleerd op station C; Als dat niet het geval is, wordt het script wordt afgesloten.  

-   Als **DeploymentType = vernieuwen**, Controleer of het station C is niet gecomprimeerd door het uitvoeren van `Compact /u C:\`.  

|**Waarde**|**Beschrijving**|  
|-|-|
|**Invoer**|**Omgevingsvariabelen**. Bevat de eigenschapswaarden, waarden voor aangepaste eigenschappen databaseverbindingen, regels voor implementatie en andere informatie dat de scripts nodig om de implementatieproces te voltooien|  
|**Uitvoer**|-                          **ZTIValidate.log**. Logboekbestand met gebeurtenissen die dit script genereert<br /><br /> -                          **BDD.log**. Logboekbestand met gebeurtenissen die alle MDT scripts genereren|  
|**Verwijzingen**|-                          **Compact.exe**. Weergeven of wijzigen van de compressie van bestanden op partities met het NTFS-bestandssysteem<br /><br /> -                          **ZTIUtility.vbs**. Van ondersteuningsfuncties en subroutines die gebruikmaakt van het script bevat|  
|**Locatie**|*distributie*\Scripts|  
|**Gebruik**|`cscript ZTIValidate.wsf </debug:value>`|  

#### <a name="arguments"></a>Argumenten  

|**Waarde**|**Beschrijving**|  
|-|-|
|**/ debug: * waarde***|De uitvoer van de event-berichten naar de console en tot de .log-bestanden. Als de waarde die is opgegeven in waarde is:<br /><br /> -                              **De waarde TRUE**, event-berichten worden verzonden naar de console en de .log-bestanden<br /><br /> -                              **ONWAAR**, gebeurtenis berichten worden alleen naar het .log-bestanden (dit is het gedrag wanneer het argument is niet opgegeven.)|  

#### <a name="properties"></a>Eigenschappen  

|**Naam**|**Lezen**|**Schrijven**|  
|-|-|-|  
|**DeploymentType**|-||  
|**DestinationLogicalDrive**|-|-|  
|**ImageBuild**|-||  
|**ImageMemory**|-||  
|**ImageProcessorSpeed**|-||  
|**ImageSize**|-||  
|**ImageSizeMultiplier**|-||  
|**IsServerOS**|-||  
|**Geheugen**|-||  
|**OSDPackagePath**|-||  
|**OSInstall**|-||  
|**ProcessorSpeed**|-||  
|**SMSTSLocalDataDrive**||-|  
|**VerifyOS**|-||  

###  <a name="ZTIVHDCreate.wsf"></a>ZTIVHDCreate.wsf  
 Dit script wordt gebruikt voor het maken van een virtuele harde schijf (.vhd of avhd)-bestand op de doelcomputer en koppel het VHD-bestand als een schijf. Vervolgens implementeert andere delen van het implementatieproces LTI de Windows-besturingssysteem en toepassingen naar de zojuist gemaakte virtuele harde schijf. De script-processen zijn als volgt:  

-   De **Class_Initialize** methode wordt gebruikt voor het initialiseren van de **VHDInputVariable** variabele.  

-   Valideren dat **VHDCreateSource** is gedefinieerd en zoekt u het bron-VHD-bestand (indien opgegeven).  

-   Genereren van een willekeurige .vhd-bestandsnaam als **VHDCreateFilename** willekeurige gelijk is aan of ' ' (null).  

-   Controleer of de map waar het VHD-bestand (opgegeven in **VHDCreateFileName**) moet worden gemaakt.  

-   Maken van het VHD-bestand met de waarden in **VHDCreateSizePercent**, **VHDCreateSizeMax**, en **VHDCreateType**.  

-   Maak een differentiërende schijf (indien opgegeven) met de waarde in **VHDCreateDiffVHD**.  

-   Het zojuist gemaakte VHD-bestand en de optionele differentiërende schijf zijn gekoppeld.  

-   Het schijfnummer van de gekoppelde virtuele harde schijf wordt geretourneerd.  

|**Waarde**|**Beschrijving**|  
|-|-|
|**Invoer**|**Omgevingsvariabelen**. Bevat de eigenschapswaarden, waarden voor aangepaste eigenschappen databaseverbindingen, regels voor implementatie en andere informatie dat de scripts nodig om de implementatieproces te voltooien|  
|**Uitvoer**|-                          **ZTIVHDCreate.log**. Logboekbestand met gebeurtenissen die dit script genereert<br /><br /> -                          **BDD.log**. Logboekbestand met gebeurtenissen die alle MDT scripts genereren|  
|**Verwijzingen**|-                          **ZTIDiskUtility.vbs**. Ondersteunende functies en subroutines die maakt gebruik van het script bevat<br /><br /> -                          **ZTIUtility.vbs**. Van ondersteuningsfuncties en subroutines die gebruikmaakt van het script bevat|  
|**Locatie**|*distributie*\Scripts|  
|**Gebruik**|`cscript ZTIVHDCreate.wsf </debug:value>`|  

#### <a name="arguments"></a>Argumenten  

|**Waarde**|**Beschrijving**|  
|-|-|
|**/ debug: * waarde***|De uitvoer van de event-berichten naar de console en tot de .log-bestanden. Als de waarde die is opgegeven in waarde is:<br /><br /> -                              **De waarde TRUE**, event-berichten worden verzonden naar de console en de .log-bestanden<br /><br /> -                              **ONWAAR**, gebeurtenis berichten worden alleen naar het .log-bestanden (dit is het gedrag wanneer het argument is niet opgegeven.)|  

#### <a name="properties"></a>Eigenschappen  

|**Naam**|**Lezen**|**Schrijven**|  
|-|-|-|  
|**VHDCreateDiffVHD**|-||  
|**VHDCreateFileName**|-||  
|**VHDCreateSizeMax**|-||  
|**VHDCreateSource**|-||  
|**VHDCreateType**|-||  
|**VHDDisks**||-|  
|**VHDInputVariable**|-||  
|**VHDOutputVariable**|-||  

###  <a name="ZTIWindowsUpdate.wsf"></a>ZTIWindowsUpdate.wsf  
 Dit script updates gedownload en geïnstalleerd op computers in een bedrijfsnetwerk met WSUS, Windows Update of Microsoft Update gebruiken de [Windows Update Agent (WUA)](http://msdn2.microsoft.com/library/Aa387099.aspx) application programming interface (API). Standaard is deze functie is uitgeschakeld in elke takenreeks, en moet handmatig worden geactiveerd om uit te voeren.  

 In de meeste bedrijven beschikt al over de teams en infrastructuur in place zojuist bijwerken computers geïmplementeerd in het bedrijfsnetwerk. Dit proces omvat de meest recente set patches, stuurprogramma's en updates die beschikbaar zijn voor elke desktopconfiguratie volgen en bepalen welke updates moeten worden gedownload en geïnstalleerd voor elke configuratie. Als de organisatie al een tot stand gebrachte proces dit script mogelijk niet nodig. Dit script is ontworpen voor het vervullen van nodig voor implementatieteams die mogelijk niet tot stand gebrachte processen hebben, maar ervoor wilt zorgen dat doelcomputers worden bijgewerkt wanneer geïmplementeerd.  

 Dit script wordt automatisch scant de doelcomputer en downloadt een breed scala aan updates die van toepassing zijn gevonden. Een van deze zijn:  

-   Windows-servicepacks  

-   Niet-Microsoft-stuurprogramma's die op Windows Update zijn geplaatst  

-   De meest recente updates voor de hotfix  

-   Microsoft Office-updates  

-   Microsoft Exchange Server en SQL Server-updates  

-   Microsoft Visual Studio® updates  

-   Bepaalde updates niet-Microsoft-toepassing  

> [!TIP]
>  Veel hardwarefabrikanten hebben hun stuurprogramma's geplaatst voor Windows Update. Deze stuurprogramma's wordt niet langer hoeft te worden beheerd in de map Out-of-Box stuurprogramma's. Experimenteren door het verwijderen van stuurprogramma's uit de distributieshare om te zien welke zijn beschikbaar voor Windows Update. Denk eraan dat als de stuurprogramma's zijn niet opgenomen in Windows standaard niet verwijderen netwerk- of opslagstuurprogramma's, omdat het besturingssysteem wordt gebruikersinvoer vereisen.  

 MDT biedt ondersteuning voor de mogelijkheid voor het implementeren van een bijgewerkte versie van de WUA als onderdeel van de implementatie van besturingssystemen. Dit kan ervoor zorgen dat doelcomputers worden uitgevoerd met de juiste versie van de WUA wanneer ze zijn geïmplementeerd. Het helpt tevens overbodig verbinding maken met Internet en download de nieuwste versie van de WUA na de implementatie.  

 MDT kunt ook configureren voor WUA voor het verzamelen van updates op computers in het bedrijfsnetwerk met WSUS in plaats van via Internet verbinding maken met Microsoft-Updates. MDT Configureer desgewenst WUA voor het gebruik van een specifieke computer uitgevoerd met behulp van WSUS de **WSUSServer** eigenschap.  

 Zie voor meer informatie en instructies voor de implementatie WUA [Windows Update Agent installeren op clientcomputers](http://technet.microsoft.com/library/bb932139.aspx).  

 De meest recente versie van de WUA zelfstandig installatieprogramma voor:  

-   x86 versies (WindowsUpdateAgent30-x86.exe) op [http://go.microsoft.com/fwlink/?LinkID=100334](http://go.microsoft.com/fwlink/?LinkID=100334)  

-   x64 versie (WindowsUpdateAgent30-x64.exe) op [http://go.microsoft.com/fwlink/?LinkID=100335](http://go.microsoft.com/fwlink/?LinkID=100335)  

 Windows 7 en hoger bevatten de meest recente versie van de WUA, dus geen upgrade vereist is.  

 Zie voor meer informatie [bijwerken van Windows Update Agent](http://msdn2.microsoft.com/library/aa387285.aspx).  

 Wanneer in de Sequencer taak ingeschakeld, wordt dit script meerdere keren uitgevoerd in de status fase voor het herstellen van de implementatie van besturingssystemen. Eerst wordt deze uitgevoerd nadat het besturingssysteem voor de eerste keer is gestart. Zorg ervoor dat de meest recente updates en servicepacks zijn geïnstalleerd voordat de installatie van alle toepassingen die afhankelijk van specifieke updates zijn kan of servicepacks worden geïnstalleerd op de doelcomputer. Een toepassing kan bijvoorbeeld zijn afhankelijk van de nieuwste versie van Microsoft .NET Framework wordt geïnstalleerd.  

 Dit script wordt ook uitgevoerd na de installatie van toepassingen, die zorgt ervoor dat de meest recente toepassing servicepacks en updates zijn toegepast. Bijvoorbeeld, moet u dit script gebruiken om ervoor te zorgen dat de meest recente updates worden toegepast op Microsoft Office 2010 of het 2007 Office-systeem.  

 Het is mogelijk tijdens de installatie van een of meer updates, de doelcomputer moet opnieuw worden opgestart zodat de installatie van een update volledig is voltooid. Om ervoor te zorgen dat updates correct zijn geïnstalleerd, als het script wordt gedetecteerd dat de installatie van een update vereist dat de doelcomputer moet worden gestart, het script automatisch de doelcomputer opnieuw wordt opgestart en wordt hervat als aanvullende updates zijn gedetecteerd en installatie in behandeling is. Het script wordt afgesloten als er is vastgesteld dat de doelcomputer volledig up-to-date is. Een fout wordt vastgelegd als tijdens het bijwerken van de doelcomputer, heeft het script zeven mislukte pogingen om de updates te installeren en de doelcomputer nog steeds opnieuw worden opgestart.  

 Tijdens runtime voert het script uit de volgende taken:  

-   De doelcomputer voor het gebruik van een WSUS-server configureren als de **WSUSServer** -eigenschap is opgegeven.  

-   Controleer of de nieuwste versie van de WUA is geïnstalleerd op de doelcomputer.  

-   Zoeken naar de doelcomputer voor de betreffende updates die nog niet zijn geïnstalleerd en die gewoonlijk kan worden verborgen.  

-   Elke update heeft een bijbehorende **UpdateID** en **QNumber** eigenschap:  

    -   De **UpdateID** eigenschap bevindt zich in GUID-indeling, zoals *67da2176-5c57-4614-a514-33abbdd51f67*.  

    -   De **QNumber** eigenschap is een numerieke waarde, zoals *987654*.  

-   Het script vergelijkt de **UpdateID** en **KBArticle** eigenschapswaarden op de lijst met uitsluitingen opgegeven in de volgende MDT-eigenschappen:  

    -   **WUMU_ExcludeID**. Een lijst met UpdateIDs uitsluiten; een bijwerken met een **UpdateID** gevonden in deze lijst wordt niet geïnstalleerd.  

    -   **WUMU_ExcludeKB**. Een lijst met **QNumbers** uitsluiten; een bijwerken met een **QNumber** gevonden in deze lijst wordt niet geïnstalleerd.  

    -   Bovendien kunnen de updates die gebruikersinvoer vereist uitgesloten en niet is geïnstalleerd.  

-   Alle updates die moeten worden goedgekeurd van een eindgebruiker gebruiksrechtovereenkomst (EULA), worden automatisch goedgekeurd door het script. Moet u handmatig lezen en controleren van elke overeenkomst voordat u dit script uitvoert in een productieomgeving.  

-   De activiteit voor elke update wordt geschreven naar het bestand ZTIWindowsUpdate.log met de installatie of OVERSLAAN als de update is goedgekeurd voor installatie, samen met de update-id, een korte beschrijving van de update en de QNumber-reeks.  

-   Elke update wordt geïnstalleerd, wordt gedownload en geïnstalleerd in batches.  

-   De doelcomputer mogelijk meer dan één keer opnieuw opstarten tijdens de installatie van updates.  

> [!NOTE]
>  Windows Internet Explorer 7 vereist interactie van de gebruiker, zodat deze niet is geïnstalleerd met dit script.  

> [!NOTE]
>  Standaard bevatten **QNumber 925471** in de **WUMU_ExcludeKB** lijst om te voorkomen dat Windows Vista Ultimate extra taalpakketten te installeren.  

> [!NOTE]
>  Als er geen intranet bronnen beschikbaar zijn, dit script bestanden downloadt van twee Microsoft-sites: [http://update.microsoft.com/redist/wuredist.cab](http://update.microsoft.com/redist/wuredist.cab) en [http://download.windowsupdate.com/v6/windowsupdate/ Redist/standalone/muauth.cab](http://download.windowsupdate.com/v6/windowsupdate/redist/standalone/muauth.cab).  

|**Waarde**|**Beschrijving**|  
|-|-|
|**Invoer**|**Omgevingsvariabelen**. Bevat de eigenschapswaarden, waarden voor aangepaste eigenschappen databaseverbindingen, regels voor implementatie en andere informatie dat de scripts nodig om de implementatieproces te voltooien|  
|**Uitvoer**|-                          **ZTIWindowsUpdate.log**. Logboekbestand met gebeurtenissen die dit script genereert<br /><br /> -                          **BDD.log**. Logboekbestand met gebeurtenissen die alle MDT scripts genereren|  
|**Verwijzingen**|-                          **Expand.exe**. Gecomprimeerde bestanden worden uitgevouwen<br /><br /> -                          **NET.exe**. Voert taken voor netwerkbeheer<br /><br /> -                          **WindowsUpdateAgent30-x86.exe**. WUA installeert<br /><br /> -                          **WindowsUpdateAgent30-x64.exe**. WUA installeert<br /><br /> -                          **ZTIUtility.vbs**. Van ondersteuningsfuncties en subroutines die gebruikmaakt van het script bevat|  
|**Locatie**|*distributie*\Scripts|  
|**Gebruik**|`cscript ZTIWindowsUpdate.wsf </debug:value> </UpdateCommand:"<IsInstalled=0&#124;1> <IsHidden=0&#124;1>"> </Query:true&#124;false>`|  

#### <a name="arguments"></a>Argumenten  

|**Waarde**|**Beschrijving**|  
|-|-|
|**/ debug: * waarde***|De uitvoer van de event-berichten naar de console en tot de .log-bestanden. Als de waarde die is opgegeven in waarde is:<br /><br /> -                              **De waarde TRUE**, event-berichten worden verzonden naar de console en de .log-bestanden<br /><br /> -                              **ONWAAR**, gebeurtenis berichten worden alleen naar het .log-bestanden (dit is het gedrag wanneer het argument is niet opgegeven.)|  
|**/ UpdateCommand: * param***|-                              **IsInstalled**. Ingesteld op **0** aan de query voor updates die niet zijn geïnstalleerd.<br /><br /> -                              **IsHidden**. Ingesteld op **0** aan de query voor updates die zijn verborgen.|  
|**/ Query: * waarde***|-                              **De waarde True**. De query voor de vereiste updates. Downloaden en installeren van de binaire bestanden niet.<br /><br /> -                              **ONWAAR**. Zoeken naar en installeren van vereiste updates. Download en installeer de binaire bestanden.|  

> [!NOTE]
>  Als u opgeeft, **UpdateCommand** vereist ten minste één optie.  

> [!NOTE]
>  Als u de beide opties voor **UpdateCommand**, moeten worden gescheiden door *en*.  

> [!NOTE]
>  De standaardwaarde voor **UpdateCommand** is **IsInstalled = 0** en **IsHidden = 0**.  

> [!NOTE]
>  Voor meer informatie over **UpdateCommand**, Zie [IUpdateSearcher::Search methode](http://msdn.microsoft.com/library/aa386526\(VS.85\).aspx).  

#### <a name="properties"></a>Eigenschappen  

|**Naam**|**Lezen**|**Schrijven**|  
|-|-|-|  
|**Architectuur**|-||  
|**DoCapture**|-||  
|**InstalledUpdates**||-|  
|**MSIT_WU_Count**|-|-|  
|**NoAutoUpdate_Previous**|-|-|  
|**SMSTSRebootRequested**|-|-|  
|**SMSTSRetryRequested**|-|-|  
|**WSUSServer**|-||  
|**WUMU_ExcludeID**|-||  
|**WUMU_ExcludeKB**|-||  

###  <a name="ZTIWipeDisk.wsf"></a>ZTIWipeDisk.wsf  
 Dit script wordt opgemaakt harde schijf van de doelcomputer. Het script:  

-   Is afgesloten indien **WipeDisk** is niet gelijk aan **TRUE**  

-   Hiermee bepaalt u het betreffende station opmaken  

-   Indelingen van het station door aan te roepen `cmd /c format <Drive> /fs:ntfs /p:3 /Y` (waarbij `<Drive>` de stationsletter van de harde schijf worden ingedeeld)  

|**Waarde**|**Beschrijving**|  
|-|-|
|**Invoer**|**Omgevingsvariabelen**. Bevat de eigenschapswaarden, waarden voor aangepaste eigenschappen databaseverbindingen, regels voor implementatie en andere informatie dat de scripts nodig om de implementatieproces te voltooien|  
|**Uitvoer**|-                          **ZTIWipeDisk.log**. Logboekbestand met gebeurtenissen die dit script genereert<br /><br /> -                          **BDD.log**. Logboekbestand met gebeurtenissen die alle MDT scripts genereren|  
|**Verwijzingen**|-                          **CMD.exe**. Hiermee kunt het uitvoeren van opdrachtregelprogramma 's<br /><br /> -                          **Format.com**. Indelingen van de harde schijf<br /><br /> -                          **ZTIUtility.vbs**. Van ondersteuningsfuncties en subroutines die gebruikmaakt van het script bevat|  
|**Locatie**|*distributie*\Scripts|  
|**Gebruik**|`cscript ZTIWipeDisk.wsf </debug:value>`|  

#### <a name="arguments"></a>Argumenten  

|**Waarde**|**Beschrijving**|  
|-|-|
|**/ debug: * waarde***|De uitvoer van de event-berichten naar de console en tot de .log-bestanden. Als de waarde die is opgegeven in waarde is:<br /><br /> -                              **De waarde TRUE**, event-berichten worden verzonden naar de console en de .log-bestanden<br /><br /> -                              **ONWAAR**, gebeurtenis berichten worden alleen naar het .log-bestanden (dit is het gedrag wanneer het argument is niet opgegeven.)|  

#### <a name="properties"></a>Eigenschappen  

|**Naam**|**Lezen**|**Schrijven**|  
|-|-|-|  
|**WipeDisk**|-||  

##  <a name="SupportFiles"></a>Ondersteuning voor bestanden  
 De hulpprogramma's en scripts gebruikt in implementaties van LTI en ZTI verwijzen naar externe configuratiebestanden om te bepalen van de stappen en de configuratie-instellingen gebruikt tijdens de implementatie.  

 De volgende informatie is bedoeld voor elk hulpprogramma:  

-   **Naam**. Hiermee geeft u de naam van het bestand  

-   **Beschrijving**. Bevat een beschrijving van het doel van het bestand  

-   **Locatie**. Hiermee geeft u de map waar het bestand kan worden gevonden; de informatie voor de locatie in worden de volgende variabelen gebruikt:  

    -   **program_files**. Deze variabele verwijst naar de locatie van de map Program Files op de computer waarop de MDT is geïnstalleerd.  

    -   **distributie**. Deze variabele verwijst naar de locatie van de distributie-map voor de implementatieshare.  

    -   **Platform**. Deze variabele is een tijdelijke aanduiding voor het platform van het besturingssysteem (x86 of x64).  

###  <a name="ApplicationGroups.xml"></a>ApplicationGroups.xml  

> [!NOTE]
>  Dit XML-bestand wordt beheerd door MDT en hoeven niet te worden gewijzigd.  

|**Waarde**|**Beschrijving**|  
|-|-|
|**Locatie**|*distributie*\Control|  

###  <a name="Applications.xml"></a>Applications.XML  

> [!NOTE]
>  Dit XML-bestand wordt beheerd door MDT en hoeven niet te worden gewijzigd.  

|**Waarde**|**Beschrijving**|  
|-|-|
|**Locatie**|*distributie*\Control|  

###  <a name="BootStrap.ini"></a>BootStrap.ini  
 Het configuratiebestand gebruikt wanneer de doelcomputer kan geen verbinding maken met de juiste implementatieshare. Deze situatie doet zich in de nieuwe Computer en de Computer vervangen scenario's.  

|**Waarde**|**Beschrijving**|  
|-|-|
|**Locatie**|*distributie*\Control|  

###  <a name="CustomSettings.ini"></a>CustomSettings.ini  
 Het primaire configuratiebestand voor de MDT verwerkingsregels gebruikt in alle scenario's.  

|**Waarde**|**Beschrijving**|  
|-|-|
|**Locatie**|*distributie*\Control|  

###  <a name="Deploy.xml"></a>Deploy.XML  

> [!NOTE]
>  Dit XML-bestand wordt beheerd door MDT en hoeven niet te worden gewijzigd.  

|**Waarde**|**Beschrijving**|  
|-|-|
|**Locatie**|*program_files*\Microsoft Deployment Toolkit\Control|  

###  <a name="DriverGroups.xml"></a>DriverGroups.xml  

> [!NOTE]
>  Dit XML-bestand wordt beheerd door MDT en hoeven niet te worden gewijzigd.  

|**Waarde**|**Beschrijving**|  
|-|-|
|**Locatie**|*distributie*\Control|  

###  <a name="Drivers.xml"></a>Drivers.XML  

> [!NOTE]
>  Dit XML-bestand wordt beheerd door MDT en hoeven niet te worden gewijzigd.  

|**Waarde**|Beschrijving|  
|-|-|  
|**Locatie**|*distributie*\Control|  

###  <a name="LinkedDeploymentShares.xml"></a>LinkedDeploymentShares.xml  

> [!NOTE]
>  Dit XML-bestand wordt beheerd door MDT en hoeven niet te worden gewijzigd.  

|**Waarde**|**Beschrijving**|  
|-|-|
|**Locatie**|*distributie*\Scripts|  

###  <a name="ListOfLanguages.xml"></a>ListOfLanguages.xml  

> [!NOTE]
>  Dit XML-bestand wordt beheerd door MDT en hoeven niet te worden gewijzigd.  

|**Waarde**|**Beschrijving**|  
|-|-|
|**Locatie**|*distributie*\Scripts|  

###  <a name="MediaGroups.xml"></a>MediaGroups.xml  

> [!NOTE]
>  Dit XML-bestand wordt beheerd door MDT en hoeven niet te worden gewijzigd.  

|**Waarde**|**Beschrijving**|  
|-|-|
|**Locatie**|*distributie*\Scripts|  

###  <a name="Medias.xml"></a>Medias.XML  

> [!NOTE]
>  Dit XML-bestand wordt beheerd door MDT en hoeven niet te worden gewijzigd.  

|**Waarde**|**Beschrijving**|  
|-|-|
|**Locatie**|*distributie*\Scripts|  

###  <a name="OperatingSystemGroups.xml"></a>OperatingSystemGroups.xml  

> [!NOTE]
>  Dit XML-bestand wordt beheerd door MDT en hoeven niet te worden gewijzigd.  

|**Waarde**|**Beschrijving**|  
|-|-|
|**Locatie**|*distributie*\Control|  

###  <a name="OperatingSystems.xml"></a>OperatingSystems.xml  

> [!NOTE]
>  Dit XML-bestand wordt beheerd door MDT en hoeven niet te worden gewijzigd.  

|**Waarde**|**Beschrijving**|  
|-|-|
|**Locatie**|*distributie*\Control|  

###  <a name="PackageGroups.xml"></a>PackageGroups.xml  

> [!NOTE]
>  Dit XML-bestand wordt beheerd door MDT en hoeven niet te worden gewijzigd.  

|**Waarde**|**Beschrijving**|  
|-|-|
|**Locatie**|*distributie*\Control|  

###  <a name="Packages.xml"></a>Packages.XML  

> [!NOTE]
>  Dit XML-bestand wordt beheerd door MDT en hoeven niet te worden gewijzigd.  

|**Waarde**|**Beschrijving**|  
|-|-|
|**Locatie**|*distributie*\Control|  

###  <a name="SelectionProfileGroups.xml"></a>SelectionProfileGroups.xml  

> [!NOTE]
>  Dit XML-bestand wordt beheerd door MDT en hoeven niet te worden gewijzigd.  

|**Waarde**|**Beschrijving**|  
|-|-|
|**Locatie**|*distributie*\Control|  

###  <a name="SelectionProfiles.xml"></a>SelectionProfiles.xml  

> [!NOTE]
>  Dit XML-bestand wordt beheerd door MDT en hoeven niet te worden gewijzigd.  

|**Waarde**|**Beschrijving**|  
|-|-|
|**Locatie**|*distributie*\Control|  

###  <a name="ServerManager.xml"></a>ServerManager.xml  

> [!NOTE]
>  Dit XML-bestand wordt beheerd door MDT en hoeven niet te worden gewijzigd.  

|**Waarde**|**Beschrijving**|  
|-|-|
|**Locatie**|*program_files*\Microsoft Deployment Toolkit\Bin|  

###  <a name="Settings.xml"></a>Settings.XML  

> [!NOTE]
>  Dit XML-bestand wordt beheerd door MDT en hoeven niet te worden gewijzigd.  

|**Waarde**|**Beschrijving**|  
|-|-|
|**Locatie**|*distributie*\Control|  

###  <a name="TaskSequenceGroups.xml"></a>TaskSequenceGroups.xml  

> [!NOTE]
>  Dit XML-bestand wordt beheerd door MDT en hoeven niet te worden gewijzigd.  

|**Waarde**|**Beschrijving**|  
|-|-|
|**Locatie**|*distributie*\Control|  

###  <a name="TaskSequences.xml"></a>TaskSequences.xml  

> [!NOTE]
>  Dit XML-bestand wordt beheerd door MDT en hoeven niet te worden gewijzigd.  

|**Waarde**|**Beschrijving**|  
|-|-|
|**Locatie**|*distributie*\Control|  

###  <a name="TS.xml"></a>TS.xml  

> [!NOTE]
>  Dit XML-bestand wordt beheerd door MDT en hoeven niet te worden gewijzigd.  

|**Waarde**|**Beschrijving**|  
|-|-|
|**Locatie**|*distributie*\Control\\*task_sequence_id*|  

> [!NOTE]
>  *Task_sequence_id* is een tijdelijke aanduiding voor de taak-ID die is toegewezen aan elke takenreeks wanneer deze is gemaakt in het knooppunt Takenreeksen in de implementatie-Workbench.  

###  <a name="Wimscript.ini"></a>Wijzigt in Wimscript.ini  
 Dit .ini-bestand is een ImageX-configuratiebestand met de lijst met mappen en bestanden die worden uitgesloten van een installatiekopie. Hiernaar wordt verwezen door ImageX tijdens de fase voor het vastleggen van LTI.  

 Zie de sectie 'Een ImageX configuratiebestand maken,' in voor hulp bij het aanpassen van dit bestand de *Windows Preinstallation Environment (Windows PE) gebruikershandleiding*.  

|**Waarde**|**Beschrijving**|  
|-|-|
|**Locatie**|*distributie*\Tools\\*platform*|  

###  <a name="ZTIBIOSCheck.xml"></a>ZTIBIOSCheck.xml  
 Dit XML-bestand bevat metagegevens over BIOS voor doelcomputers. Dit bestand is handmatig bewerkt en kan worden gelezen door [ZTIBIOSCheck.wsf](#ZTIBIOSCheck.wsf). De benodigde gegevens extraheren uit een doelcomputer voor het maken van een vermelding in dit XML-bestand met het Microsoft Visual Basic® Scripting Edition (VBScript)-programma (ZTIBIOS_Extract_Utility.vbs) dat is ingesloten in dit XML-bestand.  

|**Waarde**|**Beschrijving**|  
|-|-|
|**Locatie**|*distributie*\Scripts|  

###  <a name="ZTIConfigure.xml"></a>ZTIConfigure.xml  
 Dit XML-bestand wordt gebruikt door de [ZTIConfigure.wsf](#ZTIConfigure.wsf) script te vertalen eigenschapswaarden (opgegeven eerder in het implementatieproces) om instellingen te configureren in het bestand Unattend.xml. Dit bestand is al aangepast zodat de juiste vertalingen en hoeven niet te worden meer gewijzigd.  

|**Waarde**|**Beschrijving**|  
|-|-|
|**Locatie**|*distributie*\Scripts|  

###  <a name="ZTIGather.xml"></a>ZTIGather.xml  

> [!NOTE]
>  Dit XML-bestand vooraf is geconfigureerd en hoeven niet te worden gewijzigd. Aangepaste eigenschappen definiëren in het CustomSettings.ini-bestand of de MDT-database.  

|**Waarde**|**Beschrijving**|  
|-|-|
|**Locatie**|*distributie*\Scripts|  

###  <a name="ZTIUserState_config.xml"></a>ZTIUserState_config.xml  
 Dit XML-bestand wordt gebruikt door de [ZTIUserState.wsf](#ZTIUserState.wsf) script als een standaard USMT-configuratiebestand. Dit bestand wordt standaard gebruikt als geen bestand aangepaste configuratie is opgegeven door de [USMTConfigFile](#USMTConfigFile) eigenschap. Zie de [bestand Config.xml](http://technet.microsoft.com/library/dd560760.aspx) onderwerp in de USMT-documentatie voor meer informatie over de syntaxis en het gebruik.  

|**Waarde**|**Beschrijving**|  
|-|-|
|**Locatie**|*distributie*\Scripts|  

###  <a name="ZTITatoo.mof"></a>ZTITatoo.mof  
 Dit MOF-bestand, geïmporteerd in de WMI-opslagplaats van de doelcomputer met Mofcomp.exe, maakt de **Microsoft_BDD_Info** WMI-klasse. Deze klasse bevat informatie met betrekking tot implementatie, zoals:  

-   DeploymentMethod  

-   deploymentType  

-   DeploymentTimestamp  

-   BuildID  

-   BuildName  

-   BuildVersion  

-   OSDPackageID  

-   OSDProgramName  

-   OSDAdvertisementID  

-   TaskSequenceID  

-   TaskSequenceName  

-   TaskSequenceVersion  

|**Waarde**|**Beschrijving**|  
|-|-|
|**Locatie**|*distributie*\Scripts|  

## <a name="utilities"></a>Hulpprogramma 's  
 De scripts die wordt gebruikt in LTI ZTI verwijzing hulpprogramma's en gespecialiseerde taken ondersteunen de stappen die wordt gebruikt tijdens de implementatie uit te voeren. Gebruik de volgende informatie om te bepalen van de juiste hulpprogramma's wilt opnemen in de acties en de geldige argumenten op te geven wanneer elk hulpprogramma uit te voeren.  

 De volgende informatie is bedoeld voor elk hulpprogramma:  

-   **Naam**. Hiermee geeft u de naam van het hulpprogramma  

-   **Beschrijving**. Bevat een beschrijving van het doel van het hulpprogramma  

-   **Locatie**. Hiermee geeft u de map waar het hulpprogramma kan worden gevonden; de informatie voor de locatie in worden de volgende variabelen gebruikt:  

    -   **program_files**. Deze variabele verwijst naar de locatie van de map Program Files op de computer waarop de MDT is geïnstalleerd.  

    -   **distributie**. Deze variabele verwijst naar de locatie van de distributie-map voor de implementatieshare.  

    -   **Platform**. Deze variabele is een tijdelijke aanduiding voor het platform van het besturingssysteem (x86 of x64).  

-   **Gebruik**. Biedt de opdrachten en opties die kunnen worden opgegeven  

-   **Argumenten en een beschrijving**. Hiermee geeft de geldige argumenten worden opgegeven voor het hulpprogramma en een korte beschrijving van wat elk argument betekent  

###  <a name="BCDBoot.exe"></a>BCDBoot.exe  
 BCDBoot is een hulpprogramma dat wordt gebruikt voor een systeempartitie snel instellen of herstel van de opstartomgeving op de systeempartitie. De systeempartitie is ingesteld door een klein aantal bestanden voor de opstartomgeving kopiëren van een geïnstalleerde Windows-installatiekopie. BCDBoot maakt ook een winkel gegevens BCD (Boot Configuration) op de systeempartitie met een nieuwe opstartvermelding waarmee Windows te starten naar de geïnstalleerde Windows-installatiekopie.  

|**Waarde**|**Beschrijving**|  
|-|-|
|**Locatie**|Opgenomen in de Windows-bronbestanden|  

#### <a name="arguments"></a>Argumenten  

|**Waarde**|**Beschrijving**|  
|-|-|
||Zie de help van de opdrachtregel die geleverd door dit hulpprogramma.|  

###  <a name="BDDRun.exe"></a>BDDRun.exe  
 Dit hulpprogramma wordt uitgevoerd als een actie door de Sequencer taak voor uitvoerbare bestanden (zoals een script of andere code) die gebruikersinteractie is vereist. De takenreeks kan niet standaard een uitvoerbaar bestand die gebruikersinteractie vereist worden uitgevoerd. Met dit hulpprogramma kunt echter de Sequencer taak uitvoeren van een uitvoerbaar bestand die gebruikersinteractie vereist.  

 Het uitvoerbare bestand die gebruikersinteractie vereist is opgegeven als een argument voor dit hulpprogramma. Dit hulpprogramma voert het uitvoerbare bestand in een opdrachtomgeving met afzonderlijke.  

> [!NOTE]
>  Dit hulpprogramma kan alleen worden gebruikt in implementaties van LTI. Implementaties van ZTI verbieden interactie met de gebruiker.  

|**Waarde**|**Beschrijving**|  
|-|-|
|**Locatie**|*distributie*\Tools\\*platform*|  
|**Gebruik**|`BDDRun.exe commandline`|  

#### <a name="arguments"></a>Argumenten  

|**Waarde**|**Beschrijving**|  
|-|-|
|*CommandLine*|De opdracht om te worden uitgevoerd die vereist gebruikersinteractie|  

> [!NOTE]
>  Plaats dubbele aanhalingstekens rond een deel van de *opdrachtregelprogramma* gedeelte van het argument dat spaties bevat. Bijvoorbeeld: `BDDRun.exe MyAppInstall.exe /destinationdir: "%ProgramFiles%\AppName"`.  

###  <a name="Bootsect.exe"></a>Bootsect.exe  
 De master boot-code voor de partities van de vaste schijf om over te schakelen tussen BOOTMGR en NTLDR Bootsect.exe-updates. Gebruik dit hulpprogramma om de opstartsector op de computer te herstellen.  

 Zie voor meer informatie over Bootsect.exe, de sectie 'Bootsect Command-Line Options' in de *Windows Preinstallation Environment (Windows PE) gebruikershandleiding*.  

|**Waarde**|**Beschrijving**|  
|-|-|
|**Locatie**|*distributie*\Tools\\*platform*|  
|**Gebruik**|`bootsect.exe /nt52 C:`|  

#### <a name="arguments"></a>Argumenten  

|**Waarde**|**Beschrijving**|  
|-|-|
|**/ Help**|Geeft de instructies voor het gebruik hier vermeld.|  
|**/ nt52**|Past de MBR-code die compatibel is met NTLDR naar **SYS**, **alle**, of *stationsletter*. Het geïnstalleerde besturingssysteem op **SYS**, **alle**, of *stationsletter* moet een eerdere versie van Windows Vista.|  
|**NT60**|Past de MBR-code die compatibel is met BOOTMGR naar **SYS**, **alle**, of *stationsletter*. Het geïnstalleerde besturingssysteem op **SYS**, **alle**, of *stationsletter* moet Windows Vista.|  
|**SYS**|De master boot-code op de systeempartitie gebruikt voor het opstarten van Windows-updates.|  
|**Alle**|De code van de master boot op alle partities-updates. **ALLE** wordt niet per se de opstartcode voor elk volume bijgewerkt. Deze optie werkt in plaats daarvan de opstartcode op volumes die kunnen worden gebruikt als Windows-opstartvolumes, met uitsluiting van de dynamische volumes niet is verbonden met een onderliggende schijfpartitie. Deze beperking is ingesteld, omdat de opstartcode moet zich bevinden in het begin van een schijfpartitie.|  
|***Stationsletter***|De master boot-code op het volume dat is gekoppeld aan deze stationsletter-updates. De code van de opstartinstallatiekopie wordt niet bijgewerkt wanneer een van beide (1) **stationsletter** is niet gekoppeld aan een volume of (2) **stationsletter** is gekoppeld aan een volume dat niet is verbonden met een onderliggende schijfpartitie.|  
|**/ Forceren**|Hiermee wordt de volumes geforceerd ontkoppeld tijdens het bijwerken van de code opstarten. Gebruik deze optie voorzichtig.|  

###  <a name="Compact.exe"></a>Compact.exe  
 Weergeven of wijzigen van de compressie van bestanden op partities met het NTFS-bestandssysteem.  

|**Waarde**|**Beschrijving**|  
|-|-|
|**Locatie**|Opgenomen in de Windows-bronbestanden|  

#### <a name="arguments"></a>Argumenten  

|**Waarde**|**Beschrijving**|  
|-|-|
|**/C**|De opgegeven bestanden comprimeren. Mappen worden gemarkeerd, zodat de bestanden worden gecomprimeerd.|  
|**/V**|De opgegeven bestanden decomprimeert. Mappen worden gemarkeerd, zodat de bestanden zullen niet worden gecomprimeerd.|  
|**/ S**|Voert de opgegeven bewerking op de bestanden in de opgegeven map en alle submappen. Standaard dir is de huidige map.|  
|**/A**|Bestanden met de verborgen of systeemkenmerken wordt weergegeven. Deze bestanden worden standaard gebruikt.|  
|**/I**|Blijft de opgegeven bewerking wordt uitgevoerd zelfs nadat er zijn fouten opgetreden. Standaard Compact.exe gestopt wanneer een fout is opgetreden.|  
|**/F**|Hiermee wordt de compress-bewerking op alle opgegeven bestanden, zelfs als die die al zijn gecomprimeerd. Standaard worden al gecomprimeerde bestanden overgeslagen.|  
|**/Q**|Rapporten alleen de meest essentiële informatie.|  
|***bestandsnaam***|Hiermee geeft u een patroon, bestand of map.|  

###  <a name="Diskpart.exe"></a>DiskPart.exe  
 DiskPart is een opdrachtinterpreter modus tekst waarmee het beheer van objecten (schijven, partities of volumes) met behulp van scripts of direct invoert in een opdrachtpromptvenster.  

 Voor meer informatie over Diskpart.exe, Zie de sectie 'Diskpart Command-Line Options' in de *Windows Preinstallation Environment (Windows PE) gebruikershandleiding*.  

|**Waarde**|**Beschrijving**|  
|-|-|
|**Locatie**|Opgenomen in de bronbestanden van de Windows PE|  

#### <a name="arguments"></a>Argumenten  

|**Waarde**|**Beschrijving**|  
|-|-|
||Zie de handleiding waarnaar wordt verwezen in de beschrijving van het hulpprogramma.|  

###  <a name="Expand.exe"></a>Expand.exe  
 Dit hulpprogramma wordt uitgevoerd om uit te breiden (extract)-bestanden van gecomprimeerde bestanden.  

|**Waarde**|**Beschrijving**|  
|-|-|
|**Locatie**|Opgenomen in de Windows-bronbestanden|  
|**Gebruik**|`Expand.exe -r wuredist.cab -F:wuRedist.xml %temp%`|  

#### <a name="arguments"></a>Argumenten  

|**Waarde**|**Beschrijving**|  
|-|-|
|**-r**|Naam gedecomprimeerde bestanden|  
|**-D**|Geeft de lijst met bestanden in de bronmap|  
|***Bron***|Bronbestand (jokertekens kunnen worden gebruikt.)|  
|**-F: * bestanden***|Naam van bestanden uit te breiden vanuit een CAB-bestand|  
|***Bestemming***|Doelbestand &#124; het opgegeven pad (**bestemming** mag een map. Als **bron** is van meerdere bestanden en **- r** niet is opgegeven, **bestemming** moet een map.)|  

###  <a name="ImageX.exe"></a>ImageX.exe  
 ImageX is een opdrachtregelprogramma waarmee OEM's en bedrijven vastleggen, wijzigen en toepassen van schijfinstallatiekopieën op basis van bestanden voor snelle implementatie. ImageX werkt met WIM-bestanden voor het kopiëren naar een netwerk of samenwerking met andere technologieën die WIM-installatiekopieën, zoals Windows Setup- en Windows Deployment Services gebruiken.  

 Zie voor meer informatie over ImageX, de sectie 'Wat is ImageX' in de *Windows Preinstallation Environment (Windows PE) gebruikershandleiding*.  

|**Waarde**|**Beschrijving**|  
|-|-|
|**Locatie**|*distributie*\Tools\\*platform*|  

#### <a name="arguments"></a>Argumenten  

|**Waarde**|**Beschrijving**|  
|-|-|
||Zie de handleiding waarnaar wordt verwezen in de beschrijving van het hulpprogramma.|  

###  <a name="Microsoft.BDD.PnpEnum.exe"></a>Microsoft.BDD.PnpEnum.exe  
 Dit hulpprogramma wordt uitgevoerd voor het inventariseren van Plug en Play-apparaten die zijn geïnstalleerd op de doelcomputer.  

|**Waarde**|**Beschrijving**|  
|-|-|
|**Locatie**|*distributie*\Tools\\*platform*|  

#### <a name="arguments"></a>Argumenten  

|**Waarde**|**Beschrijving**|  
|-|-|
|Geen|:|  

###  <a name="Mofcomp.exe"></a>Mofcomp.exe  
 Mofcomp.exe is de indeling Managed Object Format-compiler die een bestand bevat Managed Object Format-instructies en voegt de klassen en klasse-instanties die zijn gedefinieerd in het bestand naar de WMI-opslagplaats wordt geparseerd. Mofcomp.exe biedt opties voor help bij de switch gebruikt.  

|**Waarde**|**Beschrijving**|  
|-|-|
|**Locatie**|Opgenomen in de Windows-bronbestanden|  

#### <a name="arguments"></a>Argumenten  

|**Waarde**|**Beschrijving**|  
|-|-|
||Zie de help van de opdrachtregel die dit hulpprogramma voorziet.|  

###  <a name="Netsh.exe"></a>Netsh.exe  
 Netsh.exe is een opdrachtregelprogramma en scriptprogramma gebruikt om de configuratie van de netwerkonderdelen te automatiseren. Zie voor meer informatie over Netsh.exe [de Netsh-opdrachtregelprogramma](http://technet.microsoft.com/library/cc785383%28WS.10%29.aspx).  

|**Waarde**|**Beschrijving**|  
|-|-|
|**Locatie**|Opgenomen in de Windows-bronbestanden|  

#### <a name="arguments"></a>Argumenten  

|**Waarde**|**Beschrijving**|  
|-|-|
||Zie de help op de opdrachtregel die dit hulpprogramma kunt u of de informatie die is gevonden op de URL die wordt vermeld in de beschrijving van het hulpprogramma.|  

###  <a name="Reg.exe"></a>Reg.exe  
 Het hulpprogramma voor Console-register wordt gebruikt voor de registergegevens lezen en wijzigen.  

|**Waarde**|**Beschrijving**|  
|-|-|
|**Locatie**|Opgenomen in de Windows-bronbestanden|  

#### <a name="arguments"></a>Argumenten  

|**Waarde**|**Beschrijving**|  
|-|-|
||Zie de help van de opdrachtregel die dit hulpprogramma voorziet.|  

###  <a name="Regsvr32.exe"></a>Regsvr32.exe  
 Dit hulpprogramma wordt gebruikt voor het registreren van bestanden (.exe .dll .ocx en enzovoort) met het besturingssysteem.  

|**Waarde**|**Beschrijving**|  
|-|-|
|**Locatie**|Opgenomen in de Windows-bronbestanden|  

#### <a name="arguments"></a>Argumenten  

|**Waarde**|**Beschrijving**|  
|-|-|
|***bestand***|De naam van het bestand om te registreren of registratie|  
|**/ s**|Het hulpprogramma in stille modus wordt uitgevoerd|  
|**/u**|Heft de registratie van het bestand|  

###  <a name="Wpeutil.exe"></a>Wpeutil.exe  
 De Windows PE-hulpprogramma (Wpeutil) is een opdrachtregelprogramma waarmee verschillende opdrachten kunnen worden uitgevoerd in een Windows PE-sessie. Bijvoorbeeld: een beheerder kan afsluiten of opnieuw opstarten van Windows PE, activeren of deactiveren van een firewall taalinstellingen configureren en initialiseren van een netwerk. MDT gebruikt het hulpprogramma voor het initialiseren van Windows PE en netwerkverbindingen en implementaties van LTI te starten.  

 Zie voor meer informatie over Wpeutil.exe, de sectie 'Wpeutil Command-Line Options' in de *Windows Preinstallation Environment (Windows PE) gebruikershandleiding*.  

|**Waarde**|**Beschrijving**|  
|-|-|
|**Locatie**|Opgenomen in de bronbestanden van de Windows PE|  

#### <a name="arguments"></a>Argumenten  

|**Waarde**|**Beschrijving**|  
|-|-|
||Zie de handleiding waarnaar wordt verwezen in de beschrijving van het hulpprogramma.|  

## <a name="mdt-windows-powershell-cmdlets"></a>MDT Windows PowerShell-Cmdlets  
 Naast de implementatie-Workbench MDT implementatieshares, worden beheerd met behulp van Windows PowerShell-cmdlets. De MDT Windows PowerShell-cmdlets zijn opgenomen in een Windows PowerShell-module-in—Microsoft.BDD.PSSnapIn—which is opgenomen in de MDT-installatie.  

 De MDT-cmdlets moet worden uitgevoerd vanuit een Windows PowerShell-console met de MDT Windows PowerShell-module geladen. Zie voor meer informatie over het starten van een Windows PowerShell-console met de MDT Windows PowerShell-module die geladen ' bij het laden van de MDT Windows PowerShell-module '.  

 Tabel 7 ziet u de MDT Windows PowerShell-cmdlets en een korte beschrijving van elke cmdlet. Elke cmdlet wordt in een volgende sectie nader besproken.  

### <a name="table-7-mdt-windows-powershell-cmdlets"></a>Tabel 7. MDT Windows PowerShell-Cmdlets  

|**Cmdlet**|**Beschrijving**|  
|-|-|  
|[Voeg MDTPersistentDrive](#Add-MDTPersistentDrive)|Voegt een aan de lijst met MDT-implementatieshare persistent stations die kunnen worden hersteld met behulp van de [terugzetten MDTPersistentDrive](#Restore-MDTPersistentDrive) cmdlet.|  
|[Schakel MDTMonitorService](#Disable-MDTMonitorService)|Hiermee schakelt u de MDT-services controleren.|  
|[Schakel MDTMonitorService](#Enable-MDTMonitorService)|Hiermee schakelt u de MDT-services controleren.|  
|[Get-MDTDeploymentShareStatistics](#Get-MDTDeploymentShareStatistics)|Geeft de statistieken weer van een implementatieshare, waaronder het aantal entiteiten per primaire map in de implementatieshare.|  
|[Get-MDTMonitorData](#Get-MDTMonitorData)|Geeft de MDT controlegegevens verzameld voor een of meer bewaakte MTD-implementaties.|  
|[Get-MDTOperatingSystemCatalog](#Get-MDTOperatingSystemCatalog)|Retourneert de catalogus besturingssysteem voor een specifiek besturingssysteem. Als de besturingssysteem-catalogus niet bestaat of verlopen is, wordt de catalogus besturingssysteem gegenereerd.|  
|[Get-MDTPersistentDrive](#Get-MDTPersistentDrive)|Geeft een lijst met implementatieshares die kunnen worden hersteld met behulp van de [terugzetten MDTPersistentDrive](#Restore-MDTPersistentDrive) cmdlet.|  
|[Importeren MDTApplication](#Import-MDTApplication)|Hiermee importeert een toepassing in een implementatieshare.|  
|[Importeren MDTDriver](#Import-MDTDriver)|Een of meer apparaatstuurprogramma's importeert in een implementatieshare.|  
|[Importeren MDTOperatingSystem](#Import-MDTOperatingSystem)|Een of meer besturingssystemen importeert in een implementatieshare.|  
|[Importeren MDTPackage](#Import-MDTPackage)|Hiermee importeert een of meer pakketten van het besturingssysteem in een implementatieshare.|  
|[Importeren MDTTaskSequence](#Import-MDTTaskSequence)|Een takenreeks importeert in een implementatieshare.|  
|[Nieuwe MDTDatabase](#New-MDTDatabase)|Maakt of een upgrade van een MDT-DB-database die is gekoppeld aan een implementatieshare.|  
|[Verwijder MDTMonitorData](#Remove-MDTMonitorData)|Hiermee verwijdert u een of meer MDT bewaking van gegevensitems uit de verzamelde MDT het bewaken van gegevens in een implementatieshare.|  
|[Verwijder MDTPersistentDrive](#Remove-MDTPersistentDrive)|Hiermee verwijdert u een in de lijst met MDT-implementatieshare persistent Windows PowerShell-stations die kunnen worden hersteld met behulp van de [terugzetten MDTPersistentDrive](#Restore-MDTPersistentDrive) cmdlet.|  
|[Restore MDTPersistentDrive](#Restore-MDTPersistentDrive)|Hiermee maakt u een Windows PowerShell-station voor elke implementatieshare in de lijst met MDT Windows PowerShell-stations permanente.|  
|[Set-MDTMonitorData](#Set-MDTMonitorData)|Een nieuwe maken of bijwerken van een bestaand MDT bewaking gegevensitem in de verzamelde MDT bewakingsgegevens in een implementatieshare.|  
|[Test MDTDeploymentShare](#Test-MDTDeploymentShare)|Controleert of de integriteit van een implementatieshare.|  
|[Test MDTMonitorData](#Test-MDTMonitorData)|Controleert of de MDT-services controleren uitgevoerd en correct is geconfigureerd.|  
|[Update MDTDatabaseSchema](#Update-MDTDatabaseSchema)|Het databaseschema MDT DB-updates.|  
|[Update MDTDeploymentShare](#Update-MDTDeploymentShare)|Een implementatieshare-updates.|  
|[Update MDTLinkedDS](#Update-MDTLinkedDS)|Inhoud van een implementatieshare repliceert naar een share van de gekoppelde implementatie.|  
|[Update MDTMedia](#Update-MDTMedia)|Inhoud van een implementatieshare repliceert naar een implementatiemap media.|  

###  <a name="Add-MDTPersistentDrive"></a>Voeg MDTPersistentDrive  
 Deze sectie beschrijft de **toevoegen MDTPersistentDriveWindows PowerShell** cmdlet. Deze cmdlet uitvoeren vanuit een Windows PowerShell-console met de MDT-PowerShell-module geladen. Zie voor meer informatie over het starten van een Windows PowerShell-console met de MDT-PowerShell-module die geladen ' bij het laden van de MDT Windows PowerShell-module '.  

#### <a name="syntax"></a>Syntaxis  

```  
Add-MDTPersistentDrive [-Name] <String> [[-InputObject] <PSObject>] [<CommonParameters>]  
```  

#### <a name="description"></a>Beschrijving  
 Deze cmdlet wordt toegevoegd een bestaand Windows PowerShell-station gemaakt met behulp van de **MDTProvider** naar een lijst met stations die zijn opgeslagen in de implementatie-Workbench of in een Windows PowerShell-sessie met de [ Restore MDTPersistentDrive](#Restore-MDTPersistentDrive) cmdlet. Deze cmdlet wordt aangeroepen wanneer u maken of een implementatieshare in de implementatie-Workbench openen.  

> [!NOTE]
>  De lijst met vastgelegde **MDTProvider** stations wordt bewaard in een per-gebruiker op basis van het gebruikersprofiel.  

 De lijst met vastgelegde **MDTProvider** stations kunnen worden weergegeven met behulp van de **Get-MDTPersistentDrive** cmdlet.  

#### <a name="parameters"></a>Parameters  
 Deze subsectie bevat informatie over de verschillende parameters beschreven die kunnen worden gebruikt met de **toevoegen MDTPersistentDriveWindows** cmdlet.  

##### <a name="-name-string"></a>-De naam < tekenreeks\>  
 Geeft de naam van een Windows PowerShell-station gemaakt met behulp van de MDT-provider en komt overeen met een bestaande implementatieshare. De naam is gemaakt met de [nieuw PSDrive](http://technet.microsoft.com/library/dd315340.aspx) cmdlet en geven de **MDTProvider** in de *PSProvider* parameter.  

 Voor meer informatie over het maken van een nieuwe Windows PowerShell-station met de **MDTProvider** en het maken van een implementatie delen met Windows PowerShell, Zie de sectie 'Maken van een implementatie delen met behulp van Windows PowerShell' in de MDT-document *Microsoft Deployment Toolkit voorbeelden Guide*.  

|**Parameter**|**Waarde**|  
|-|-|  
|**Vereist?**|**De waarde True**|  
|**Positie?**|**2** en **met de naam**|  
|**Standaardwaarde**|Geen|  
|**Pijpleidinginvoer accepteren?**|**De waarde True** (**ByValue**)|  
|**Jokertekens accepteren?**|**De waarde False**|  

##### <a name="-inputobject-psobject"></a>-InputObject < PSObject\>  
 Deze parameter geeft u een Windows PowerShell-station-object dat eerder in het proces is gemaakt. Voer een PSObject-object, zoals een gegenereerd door de [nieuw PSDrive](http://technet.microsoft.com/library/dd315340.aspx) cmdlet.  

|**Parameter**|**Waarde**|  
|-|-|  
|**Vereist?**|**De waarde False**|  
|**Positie?**|**3** en **met de naam**|  
|**Standaardwaarde**|:|  
|**Pijpleidinginvoer accepteren?**|**De waarde True** (**ByValue**)|  
|**Jokertekens accepteren?**|**De waarde False**|  

##### <a name="commonparameters"></a>< CommonParameters\>  
 Deze cmdlet ondersteunt de volgende algemene parameters: *Uitgebreid, foutopsporing, ErrorAction,-ErrorVariable, -OutBuffer, OutVariable, WarningAction* en *WarningVariable.* Zie voor meer informatie het onderwerp 'about_CommonParameters' u openen kunt door de volgende opdracht te typen en vervolgens op ENTER:  

```  
Get-Help about_CommonParameters  
```  

#### <a name="outputs"></a>uitvoer  
 Deze cmdlet levert een **PSObject** object van het type voor het object van Windows PowerShell-station is toegevoegd aan de lijst met persistente stations.  

 Deze cmdlet levert ook een **tekenreeks** het type object als de *uitgebreid* algemene parameter is opgenomen.  

#### <a name="example-1"></a>Voorbeeld 1  

```  
Add-MDTPersistentDrive –Name DS001  
```  

##### <a name="description"></a>Beschrijving  
 In dit voorbeeld wordt de share van de implementatie met de naam van de Windows PowerShell-station van *DS001* aan de lijst met persistente stations.  

#### <a name="example-2"></a>Voorbeeld 2  

```  
$MDTPSDrive = New-PSDrive -Name "DS001" -PSProvider "MDTProvider" –Root "C:\DeploymentShare$" -Description "MDT Deployment Share" -NetworkPath \\WDG-MDT-01\DeploymentShare$ -Verbose  
Add-MDTPersistentDrive –InputObject $MDTPSDrive  
```  

##### <a name="description"></a>Beschrijving  
 In dit voorbeeld wordt de naam van de Windows PowerShell-station *DS001,* gemaakt door de [nieuw PSDrive](http://technet.microsoft.com/library/dd315340.aspx) cmdlet aan de lijst met persistente MDT tapestations met de *$MDTPSDrive* variabele.  

#### <a name="example-3"></a>Voorbeeld 3  

```  
New-PSDrive -Name "DS001" -PSProvider "MDTProvider" –Root "C:\DeploymentShare$" -Description "MDT Deployment Share" -NetworkPath \\WDG-MDT-01\DeploymentShare$ -Verbose | Add-MDTPersistentDrive –Verbose  
```  

##### <a name="description"></a>Beschrijving  
 In dit voorbeeld wordt de naam van de Windows PowerShell-station *DS001,* gemaakt door de [nieuw PSDrive](http://technet.microsoft.com/library/dd315340.aspx) cmdlet aan de lijst met persistente MDT stations door te sluizen het gemaakte object van Windows PowerShell-station aan de  **Voeg MDTPersistentDrive** cmdlet.  

###  <a name="Disable-MDTMonitorService"></a>Schakel MDTMonitorService  
 Deze sectie beschrijft de **uitschakelen MDTMonitorService** Windows PowerShell-cmdlet. Deze cmdlet uitvoeren vanuit een Windows PowerShell-console met de MDT-PowerShell-module geladen. Zie voor meer informatie over het starten van een Windows PowerShell-console met de MDT-PowerShell-module die geladen ' bij het laden van de MDT Windows PowerShell-module '.  

#### <a name="syntax"></a>Syntaxis  

```  
Disable-MDTMonitorService [<CommonParameters>]  
```  

#### <a name="description"></a>Beschrijving  
 Deze cmdlet schakelt de MDT bewaking van de service die wordt uitgevoerd op de computer waarop de MDT is geïnstalleerd. De MDT-bewakingsservice verzamelt controlegegevens die kan worden weergegeven:  

-   In het knooppunt bewaking in een share in de Implementatieworkbench-implementatie  

-   Met behulp van de [Get-MDTMonitorData](#Get-MDTMonitorData) cmdlet  

 De MDT-service controleren kan vervolgens worden ingeschakeld met de [inschakelen MDTMonitorService](#Enable-MDTMonitorService).  

 Voor meer informatie over de MDT bewaking van de service, Zie de sectie 'Monitoring MDT implementaties' in het document MDT *met behulp van de Microsoft Deployment Toolkit*.  

#### <a name="parameters"></a>Parameters  
 Deze subsectie bevat informatie over de verschillende parameters beschreven die kunnen worden gebruikt met de **uitschakelen MDTMonitorService** cmdlet.  

##### <a name="commonparameters"></a>< CommonParameters\>  
 Deze cmdlet ondersteunt de volgende algemene parameters: *Uitgebreid, foutopsporing, ErrorAction,-ErrorVariable, -OutBuffer, OutVariable, WarningAction* en *WarningVariable.* Zie voor meer informatie het onderwerp 'about_CommonParameters,' die u kunt toegankelijk is voor de volgende opdracht en druk vervolgens op ENTER:  

```  
Get-Help about_CommonParameters  
```  

#### <a name="outputs"></a>uitvoer  
 Deze cmdlet levert een **tekenreeks** het type object als de *uitgebreid* algemene parameter is opgenomen; anders wordt geen uitvoer gegenereerd.  

#### <a name="example-1"></a>Voorbeeld 1  

```  
Disable-MDTMonitorService  
```  

##### <a name="description"></a>Beschrijving  
 In dit voorbeeld wordt de bewaking van de service MDT uitgeschakeld.  

###  <a name="Enable-MDTMonitorService"></a>Schakel MDTMonitorService  
 Deze sectie beschrijft de **inschakelen MDTMonitorService** Windows PowerShell-cmdlet. Deze cmdlet uitvoeren vanuit een Windows PowerShell-console met de MDT-PowerShell-module geladen. Zie voor meer informatie over het starten van een Windows PowerShell-console met de MDT-PowerShell-module die geladen ' bij het laden van de MDT Windows PowerShell-module '.  

#### <a name="syntax"></a>Syntaxis  

```  
Enable-MDTMonitorService [-EventPort] <Int32> [-DataPort] <Int32> [<CommonParameters>]  
```  

#### <a name="description"></a>Beschrijving  
 Deze cmdlet kunt de MDT bewaking van de service die wordt uitgevoerd op de computer waarop de MDT is geïnstalleerd. De MDT-bewakingsservice verzamelt controlegegevens die kan worden weergegeven:  

-   In het knooppunt bewaking in een share in de Implementatieworkbench-implementatie.  

-   Met behulp van de [Get-MDTMonitorData](#Get-MDTMonitorData) cmdlet  

 De MDT monitoring-service kan worden uitgeschakeld met de [uitschakelen MDTMonitorService](#Disable-MDTMonitorService).  

 Voor meer informatie over de MDT bewaking van de service, Zie de sectie 'Monitoring MDT implementaties' in het document MDT *met behulp van de Microsoft Deployment Toolkit*.  

#### <a name="parameters"></a>Parameters  
 Deze subsectie bevat informatie over de verschillende parameters beschreven die kunnen worden gebruikt met de **inschakelen MDTMonitorService** cmdlet.  

##### <a name="-eventport-int32"></a>-EventPort < Int32\>  
 Deze parameter bepaalt de TCP-poort die wordt gebruikt als de gebeurtenis-poort voor de MDT-service te controleren.  

|**Parameter**|**Waarde**|  
|-|-|  
|**Vereist?**|**De waarde False**|  
|**Positie?**|**2** en **met de naam**|  
|**Standaardwaarde**|**9800**|  
|**Pijpleidinginvoer accepteren?**|**De waarde False**|  
|**Jokertekens accepteren?**|**De waarde False**|  

##### <a name="-dataport-int32"></a>-Gegevenspoort < Int32\>  
 Deze parameter bepaalt de TCP-poort die wordt gebruikt als de poort voor de MDT-service te controleren.  

|**Parameter**|**Waarde**|  
|-|-|  
|**Vereist?**|**De waarde False**|  
|**Positie?**|**3** en **met de naam**|  
|**Standaardwaarde**|**9801**|  
|**Pijpleidinginvoer accepteren?**|**De waarde False**|  
|**Jokertekens accepteren?**|**De waarde False**|  

##### <a name="commonparameters"></a>< CommonParameters\>  
 Deze cmdlet ondersteunt de volgende algemene parameters: *Uitgebreid, foutopsporing, ErrorAction,-ErrorVariable, -OutBuffer, OutVariable, WarningAction* en *WarningVariable.* Zie voor meer informatie het onderwerp 'about_CommonParameters' u openen kunt door de volgende opdracht te typen en vervolgens op ENTER:  

```  
Get-Help about_CommonParameters  
```  

#### <a name="outputs"></a>uitvoer  
 Deze cmdlet levert een **tekenreeks** het type object als de *uitgebreid* algemene parameter is opgenomen; anders wordt geen uitvoer gegenereerd.  

#### <a name="example-1"></a>Voorbeeld 1  

```  
Enable-MDTMonitorService  
```  

##### <a name="description"></a>Beschrijving  
 In dit voorbeeld wordt de bewaking van de service op de lokale computer met behulp van de standaardwaarde van MDT **9800** voor de gebeurtenis-poort en de waarde van **9801** voor de poort van de MDT-service te controleren.  

#### <a name="example-2"></a>Voorbeeld 2  

```  
Enable-MDTMonitorService –EventPort 7000 –DataPort 7001  
```  

##### <a name="description"></a>Beschrijving  
 In dit voorbeeld wordt de bewaking van de service op de lokale computer met de waarde van MDT **7000** voor de gebeurtenis-poort en de waarde van **7001** voor de poort van de MDT-service te controleren.  

###  <a name="Get-MDTDeploymentShareStatistics"></a>Get-MDTDeploymentShareStatistics  
 Deze sectie beschrijft de **Get-MDTDeploymentShareStatistics** Windows PowerShell-cmdlet. Deze cmdlet uitvoeren vanuit een Windows PowerShell-console met de MDT-PowerShell-module geladen. Zie voor meer informatie over het starten van een Windows PowerShell-console met de MDT-PowerShell-module die geladen ' bij het laden van de MDT Windows PowerShell-module '.  

#### <a name="syntax"></a>Syntaxis  

```  
Get-MDTDeploymentShareStatistics [-Path <String>] [<CommonParameters>]  
```  

#### <a name="description"></a>Beschrijving  
 Deze cmdlet de statistieken weer van de share van een implementatie op basis van het station MDTProvder die is opgegeven in de *pad* parameter. De statistieken zijn het aantal items in de opgegeven implementatieshare:  

-   Toepassingen  

-   Stuurprogramma 's  

-   Besturingssystemen  

-   Pakketten  

-   Takenreeksen  

-   Selectie profielen  

-   Gekoppelde Implementatieshares  

-   MDT-Media  

-   Computers in de MDT-database  

-   Merk en modellen in de MDT-DB  

-   Locaties in de MDT-DB  

-   Rollen in de MDT-DB  

> [!NOTE]
>  De waarden voor de statistieken die betrekking op de MDT-database hebben niet is ingevuld en altijd een waarde van nul retourneren.  

#### <a name="parameters"></a>Parameters  
 Deze subsectie bevat informatie over de verschillende parameters beschreven die kunnen worden gebruikt met de **Get-MDTDeploymentShareStatistics** cmdlet.  

##### <a name="-path-string"></a>-Path < String\>  
 Deze parameter bepaalt het MDTProvider Windows PowerShell-station voor de gewenste implementatieshare.  

> [!NOTE]
>  Als deze parameter niet is opgegeven, moet de Windows PowerShell-werkmap standaard naar een locatie binnen de gewenste MDTProvider Windows PowerShell-station.  

|**Parameter**|**Waarde**|  
|-|-|  
|**Vereist?**|**De waarde False**|  
|**Positie?**|**2** en **met de naam**|  
|**Standaardwaarde**|:|  
|**Pijpleidinginvoer accepteren?**|**De waarde False**|  
|**Jokertekens accepteren?**|**De waarde False**|  

##### <a name="commonparameters"></a>< CommonParameters\>  
 Deze cmdlet ondersteunt de volgende algemene parameters: *Uitgebreid, foutopsporing, ErrorAction,-ErrorVariable, -OutBuffer, OutVariable, WarningAction* en *WarningVariable.* Zie voor meer informatie het onderwerp 'about_CommonParameters' u openen kunt door de volgende opdracht te typen en vervolgens op ENTER:  

```  
Get-Help about_CommonParameters  
```  

#### <a name="outputs"></a>uitvoer  
 Deze cmdlet levert een **PSObject** type object dat de statistieken voor de implementatieshare bevat.  

#### <a name="example-1"></a>Voorbeeld 1  

```  
Get-MDTDeploymentShareStatistics –Path DS001:  
```  

##### <a name="description"></a>Beschrijving  
 In dit voorbeeld retourneert de statistieken van de share implementatie voor de share van de implementatie die is opgegeven in de DS001: MDTProvider Windows PowerShell-station.  

#### <a name="example-2"></a>Voorbeeld 2  

```  
cd DS001:  
Get-MDTDeploymentShareStatistics  
```  

##### <a name="description"></a>Beschrijving  
 In dit voorbeeld retourneert de statistieken van de share implementatie voor de share van de implementatie die is opgegeven in de DS001: MDTProvider Windows PowerShell-station. Gebruik de **cd** opdracht in te stellen van de werkmap voor Windows PowerShell om de DS001 te: MDTProvider Windows PowerShell-station.  

###  <a name="Get-MDTMonitorData"></a>Get-MDTMonitorData  
 Deze sectie beschrijft de **Get-MDTMonitorData** Windows PowerShell-cmdlet. Deze cmdlet uitvoeren vanuit een Windows PowerShell-console met de MDT-PowerShell-module geladen. Zie voor meer informatie over het starten van een Windows PowerShell-console met de MDT-PowerShell-module die geladen ' bij het laden van de MDT Windows PowerShell-module '.  

#### <a name="syntax"></a>Syntaxis  

```  
Get-MDTMonitorData [-Path <String>] [-ID <Nullable>] [<CommonParameters>]  
```  

#### <a name="description"></a>Beschrijving  
 Deze cmdlet wordt de bewaking van de gegevens die worden gerapporteerd aan de implementatieshare MDT die is opgegeven in de *pad* parameter. Hier volgt een voorbeeld van uitvoer van deze cmdlet:  

```  
Name               : WDG-REF-01  
PercentComplete    : 100  
Settings           :  
Warnings           : 0  
Errors             : 0  
DeploymentStatus   : 3  
StartTime          : 5/23/2012 6:45:39 PM  
EndTime            : 5/23/2012 8:46:32 PM  
ID                 : 1  
UniqueID           : 94a0830e-f2bb-421c-b1e0-6f86f9eb9fa1  
CurrentStep        : 88  
TotalSteps         : 88  
StepName           :  
LastTime           : 5/23/2012 8:46:32 PM  
DartIP             :  
DartPort           :  
DartTicket         :  
VMHost             : WDG-HOST-01  
VMName             : WDG-REF-01  
ComputerIdentities : {}  

```  

> [!NOTE]
>  Het MDTProvider Windows PowerShell-station dat u deze cmdlet verwijst naar moet bestaan voordat u deze cmdlet uitvoert.  

#### <a name="parameters"></a>Parameters  
 Deze subsectie bevat informatie over de verschillende parameters beschreven die u met gebruiken kunt de **Get - MDTMonitorData** cmdlet.  

##### <a name="-path-string"></a>-Path < String\>  
 Deze parameter bepaalt het MDTProvider Windows PowerShell-station voor de gewenste implementatieshare.  

> [!NOTE]
>  Als deze parameter niet is opgegeven, moet de Windows PowerShell-werkmap standaard naar een locatie binnen de gewenste MDTProvider Windows PowerShell-station.  

|**Parameter**|**Waarde**|  
|-|-|  
|**Vereist?**|**De waarde False**|  
|**Positie?**|**2** en **met de naam**|  
|**Standaardwaarde**|:|  
|**Pijpleidinginvoer accepteren?**|**De waarde False**|  
|**Jokertekens accepteren?**|**De waarde False**|  

##### <a name="-id-nullable"></a>-ID < NULL-waarden bevatten\>  
 Deze parameter bepaalt de specifieke id voor de implementatie van een specifieke computer. Als deze parameter niet is opgegeven, worden alle bewakingsgegevens voor implementaties in de implementatieshare weergegeven.  

|**Parameter**|**Waarde**|  
|-|-|  
|**Vereist?**|**De waarde False**|  
|**Positie?**|**3** en **met de naam**|  
|**Standaardwaarde**|:|  
|**Pijpleidinginvoer accepteren?**|**De waarde False**|  
|**Jokertekens accepteren?**|**De waarde False**|  

##### <a name="commonparameters"></a>< CommonParameters\>  
 Deze cmdlet ondersteunt de volgende algemene parameters: *Uitgebreid, foutopsporing, ErrorAction,-ErrorVariable, -OutBuffer, OutVariable, WarningAction* en *WarningVariable.* Zie voor meer informatie het onderwerp 'about_CommonParameters' u openen kunt door de volgende opdracht te typen en vervolgens op ENTER:  

```  
Get-Help about_CommonParameters  
```  

#### <a name="outputs"></a>uitvoer  
 Deze cmdlet levert een **PSObject** object van het type voor elke bewaakte computer, waarin u de bewakingsgegevens voor de computer.  

#### <a name="example-1"></a>Voorbeeld 1  

```  
Get-MDTMonitorData –Path DS001:  
```  

##### <a name="description"></a>Beschrijving  
 In dit voorbeeld retourneert de bewakingsgegevens voor alle implementaties in de share van de implementatie die is opgegeven in de DS001: MDTProvider Windows PowerShell-station.  

#### <a name="example-2"></a>Voorbeeld 2  

```  
cd DS001:  
Get-MDTMonitorData  
```  

##### <a name="description"></a>Beschrijving  
 In dit voorbeeld retourneert de bewakingsgegevens voor alle implementaties in de share van de implementatie die is opgegeven in de DS001: MDTProvider Windows PowerShell-station. Gebruik de **cd** opdracht in te stellen van de werkmap voor Windows PowerShell om de DS001 te: MDTProvider Windows PowerShell-station.  

#### <a name="example-3"></a>Voorbeeld 3  

```  
Get-MDTMonitorData –Path DS001: -ID 22  
```  

##### <a name="description"></a>Beschrijving  
 In dit voorbeeld retourneert de bewakingsgegevens voor de implementatie met de ID van 22 in de share van de implementatie die is opgegeven in de DS001: MDTProvider Windows PowerShell-station.  

###  <a name="Get-MDTOperatingSystemCatalog"></a>Get-MDTOperatingSystemCatalog  
 Deze sectie beschrijft de **Get-MDTOperatingSystemCatalog** Windows PowerShell-cmdlet. Deze cmdlet uitvoeren vanuit een Windows PowerShell-console met de MDT-PowerShell-module geladen. Zie voor meer informatie over het starten van een Windows PowerShell-console met de MDT-PowerShell-module die geladen ' bij het laden van de MDT Windows PowerShell-module '.  

#### <a name="syntax"></a>Syntaxis  

```  
Get-MDTOperatingSystemCatalog [-ImageFile] <String> [-Index] <Int32> [<CommonParameters>]  
```  

#### <a name="description"></a>Beschrijving  
 Deze cmdlet haalt of de catalogus van een besturingssysteem voor een aangepaste installatiekopie gemaakt zodat u het bijbehorende bestand Unattend.XML met behulp van Windows System Image Manager (WSIM) kan wijzigen. Als er geen catalogus besturingssysteem beschikbaar is of als het bestaande besturingssysteem-catalogus ongeldig of verlopen is, deze cmdlet genereert een nieuw besturingssysteem-catalogus.  

> [!NOTE]
>  Het proces voor het genereren van een nieuwe catalogus van het besturingssysteem kan lang duren als de aangepaste installatiekopie moet worden gekoppeld, geïnspecteerd en ontkoppeld voordat de catalogus maken van het besturingssysteem is voltooid.  

#### <a name="parameters"></a>Parameters  
 Deze subsectie bevat informatie over de verschillende parameters beschreven die kunnen worden gebruikt met de **Get-MDTOperatingSystemCatalog** cmdlet.  

##### <a name="-imagefile-string"></a>-Afbeeldingsbestand < tekenreeks\>  
 Deze parameter bepaalt de volledig gekwalificeerde pad naar het aangepaste besturingssysteem-installatiekopiebestand (WIM-bestand), inclusief de naam van het bestand van de afbeelding aangepast besturingssysteem.  

|**Parameter**|**Waarde**|  
|-|-|  
|**Vereist?**|**De waarde True**|  
|**Positie?**|**2** en **met de naam**|  
|**Standaardwaarde**|:|  
|**Pijpleidinginvoer accepteren?**|**De waarde False**|  
|**Jokertekens accepteren?**|**De waarde False**|  

##### <a name="-index-int32"></a>-Index < Int32\>  
 Deze parameter bepaalt de index van de gewenste installatiekopie binnen het besturingssysteem-installatiekopiebestand (WIM-bestand).  

|**Parameter**|**Waarde**|  
|-|-|  
|**Vereist?**|**De waarde True**|  
|**Positie?**|**3** en **met de naam**|  
|**Standaardwaarde**|:|  
|**Pijpleidinginvoer accepteren?**|**De waarde False**|  
|**Jokertekens accepteren?**|**De waarde False**|  

##### <a name="commonparameters"></a>< CommonParameters\>  
 Deze cmdlet ondersteunt de volgende algemene parameters: *Uitgebreid, foutopsporing, ErrorAction,-ErrorVariable, -OutBuffer, OutVariable, WarningAction* en *WarningVariable.* Zie voor meer informatie het onderwerp 'about_CommonParameters' u openen kunt door de volgende opdracht te typen en vervolgens op ENTER:  

```  
Get-Help about_CommonParameters  
```  

#### <a name="outputs"></a>uitvoer  
 Deze cmdlet levert een **PSObject** type-object dat het pad naar de catalogus van het besturingssysteem bevat.  

#### <a name="example-1"></a>Voorbeeld 1  

```  
Get-MDTOperatingSystemCatalog –ImageFile "DS001:\Operating Systems\Windows 8\sources\install.wim" –Index 2  
```  

##### <a name="description"></a>Beschrijving  
 In dit voorbeeld retourneert de catalogus besturingssysteem voor de installatiekopie van het besturingssysteem bij de index van 2 in het besturingssysteem de installatiekopie van bestand DS001:\Operating Systems\Windows 8\sources\install.wim.  

###  <a name="Get-MDTPersistentDrive"></a>Get-MDTPersistentDrive  
 Deze sectie beschrijft de **Get-MDTPersistentDrive** Windows PowerShell-cmdlet. Deze cmdlet uitvoeren vanuit een Windows PowerShell-console met de MDT-PowerShell-module geladen. Zie voor meer informatie over het starten van een Windows PowerShell-console met de MDT-PowerShell-module die geladen ' bij het laden van de MDT Windows PowerShell-module '.  

#### <a name="syntax"></a>Syntaxis  

```  
Get-MDTPersistentDrive [<CommonParameters>]  
```  

#### <a name="description"></a>Beschrijving  
 Deze cmdlet wordt de lijst met persistente MDT Windows PowerShell-stations. De lijst met persistente MDT Windows PowerShell-stations wordt beheerd met behulp van de [toevoegen MDTPersistentDrive](#Add-MDTPersistentDrive) en [verwijderen MDTPersistentDrive](#Remove-MDTPersistentDrive) cmdlets of de implementatie-Workbench.  

 De uitvoer van deze cmdlet bevat de volgende informatie:  

-   De naam van het Windows PowerShell-station, bijvoorbeeld DS001  

-   Pad naar map, zoals \\\WDG-MDT-01\DeploymentShare$  

 Persistente MDT Windows PowerShell-stations zijn vergelijkbaar met persistente netwerkstations.  

> [!NOTE]
>  Deze lijst met persistente MDT Windows PowerShell-stations wordt bewaard in per gebruiker en zijn opgeslagen in het gebruikersprofiel.  

#### <a name="parameters"></a>Parameters  
 Deze subsectie bevat informatie over de verschillende parameters beschreven die kunnen worden gebruikt met de **Get - MDTPersistentDrive** cmdlet.  

##### <a name="commonparameters"></a>< CommonParameters\>  
 Deze cmdlet ondersteunt de volgende algemene parameters: *Uitgebreid, foutopsporing, ErrorAction,-ErrorVariable, -OutBuffer, OutVariable, WarningAction* en *WarningVariable.* Zie voor meer informatie het onderwerp 'about_CommonParameters' u openen kunt door de volgende opdracht te typen en vervolgens op ENTER:  

```  
Get-Help about_CommonParameters  
```  

#### <a name="outputs"></a>uitvoer  
 Deze cmdlet levert een **PSObject** type object voor elke MDT persistent station die identiek is aan de **PSObject** type object dat de [nieuw PSDrive](http://technet.microsoft.com/library/dd315340.aspx) cmdlet retourneert.  

#### <a name="example-1"></a>Voorbeeld 1  

```  
Get-MDTPersistentDrive  
```  

##### <a name="description"></a>Beschrijving  
 In dit voorbeeld wordt een lijst van de MDT weergegeven vastgelegde stations.  

###  <a name="Import-MDTApplication"></a>Importeren MDTApplication  
 Deze sectie beschrijft de **importeren MDTApplication** Windows PowerShell-cmdlet. Deze cmdlet uitvoeren vanuit een Windows PowerShell-console met de MDT-PowerShell-module geladen. Zie voor meer informatie over het starten van een Windows PowerShell-console met de MDT-PowerShell-module die geladen ' bij het laden van de MDT Windows PowerShell-module '.  

#### <a name="syntax"></a>Syntaxis  

```  
Import-MDTApplication [-Path <String>] -Name <String> ApplicationSourcePath <String> -DestinationFolder <String> [-Move] [<CommonParameters>]  
```  

 – of –  

```  
Import-MDTApplication [-Path <String>] -Name <String> NoSource [<CommonParameters>]  
```  

 – of –  

```  
Import-MDTApplication [-Path <String>] -Name <String> Bundle [<CommonParameters>]  
```  

#### <a name="description"></a>Beschrijving  
 Deze cmdlet kunt u een toepassing importeren in een implementatieshare. De volgende typen kunnen worden geïmporteerd met behulp van deze cmdlet:  

-   Toepassingen met bronbestanden bevat, met behulp van de *ApplicationSourcePath*, *doelmap*, en *verplaatsen* parameters. Het eerste syntaxisvoorbeeld ziet u het gebruik van deze cmdlet voor dit type toepassing.  

-   Toepassingen zonder bronbestanden of met bronbestanden die zich bevinden op een ander netwerk gedeelde mappen met behulp van de *NoSource* parameter. Het tweede syntaxisvoorbeeld ziet u het gebruik van deze cmdlet voor dit type toepassing.  

-   Pakketten van de toepassing, die worden gebruikt om een set van gerelateerde toepassingen met behulp van de *bundel* parameter. Het laatste syntaxisvoorbeeld ziet u het gebruik van deze cmdlet voor dit type toepassing.  

#### <a name="parameters"></a>Parameters  
 Deze subsectie bevat informatie over de verschillende parameters beschreven die kunnen worden gebruikt met de **importeren MDTApplication** cmdlet.  

##### <a name="-path-string"></a>-Path < String\>  
 Deze parameter bepaalt het volledig gekwalificeerde pad naar een bestaande map waar de toepassing wordt geïmporteerd in de implementatieshare wordt geplaatst. Als de *doelmap* parameter wordt gebruikt, wordt de map die is opgegeven in de *doelmap* parameter wordt gemaakt onder de map die is opgegeven in deze parameter. Deze parameter wordt gebruikt in het gebruik van alle syntaxis voor deze cmdlet.  

> [!NOTE]
>  Als deze parameter niet is opgegeven, moet de Windows PowerShell-werkmap naar de gewenste locatie binnen de implementatieshare standaard.  

|**Parameter**|**Waarde**|  
|-|-|  
|**Vereist?**|**De waarde False**|  
|**Positie?**|**Met de naam**|  
|**Standaardwaarde**|:|  
|**Pijpleidinginvoer accepteren?**|**De waarde False**|  
|**Jokertekens accepteren?**|**De waarde False**|  

##### <a name="-name-string"></a>-De naam < tekenreeks\>  
 Deze parameter geeft de naam van de toepassing moet worden toegevoegd aan de share implementaties en moet uniek zijn binnen de implementatieshare. Deze parameter wordt gebruikt in het gebruik van alle syntaxis voor deze cmdlet.  

|**Parameter**|**Waarde**|  
|-|-|  
|**Vereist?**|**De waarde True**|  
|**Positie?**|**Met de naam**|  
|**Standaardwaarde**|:|  
|**Pijpleidinginvoer accepteren?**|**De waarde False**|  
|**Jokertekens accepteren?**|**De waarde False**|  

##### <a name="-applicationsourcepath-string"></a>-ApplicationSourcePath < tekenreeks\>  
 Deze parameter bepaalt de volledig gekwalificeerde pad naar de bronbestanden van de toepassing voor de toepassing die worden geïmporteerd in de implementatieshare. Deze parameter is alleen geldig voor gebruik in het eerste syntaxisvoorbeeld.  

|**Parameter**|**Waarde**|  
|-|-|  
|**Vereist?**|**De waarde True**|  
|**Positie?**|**Met de naam**|  
|**Standaardwaarde**|:|  
|**Pijpleidinginvoer accepteren?**|**De waarde False**|  
|**Jokertekens accepteren?**|**De waarde False**|  

##### <a name="-destinationfolder-string"></a>-Doelmap < tekenreeks\>  
 Deze parameter geeft de map in de implementatieshare waar de bronbestanden van de toepassing zullen worden geïmporteerd. Deze map wordt gemaakt onder de map die is opgegeven de *pad* parameter. Deze parameter is alleen geldig voor gebruik in het eerste syntaxisvoorbeeld.  

|**Parameter**|**Waarde**|  
|-|-|  
|**Vereist?**|**De waarde True**|  
|**Positie?**|**Met de naam**|  
|**Standaardwaarde**|:|  
|**Pijpleidinginvoer accepteren?**|**De waarde False**|  
|**Jokertekens accepteren?**|**De waarde False**|  

##### <a name="-move-switchparameter"></a>-Verplaatsen [< SwitchParameter\>]  
 Deze parameter wordt aangegeven of de bronbestanden van de toepassing moeten worden teruggezet (in plaats van overgenomen) van de map waarin de bronbestanden van de toepassing bevinden die is opgegeven in de *ApplicationSourcePath* parameter.  

 Als deze parameter is:  

-   Opgegeven, worden de bestanden worden verplaatst en de bestanden in de map die is opgegeven in de *ApplicationSourcePath* parameter zijn verwijderd  

-   Niet opgegeven, worden de bestanden worden gekopieerd en de bestanden in de map die is opgegeven in de *ApplicationSourcePath* parameter blijven behouden  

 Deze parameter is alleen geldig voor gebruik in het eerste syntaxisvoorbeeld.  

|**Parameter**|**Waarde**|  
|-|-|  
|**Vereist?**|**De waarde False**|  
|**Positie?**|**Met de naam**|  
|**Standaardwaarde**|:|  
|**Pijpleidinginvoer accepteren?**|**De waarde False**|  
|**Jokertekens accepteren?**|**De waarde False**|  

##### <a name="-nosource-switchparameter"></a>-NoSource [< SwitchParameter\>]  
 Deze parameter geeft aan dat de toepassing die het importeren van een toepassing die geen bronbestanden zijn moet worden gekopieerd. Wanneer u deze parameter gebruikt, wordt de bronbestanden van de toepassing zijn:  

-   Op een gedeelde netwerkmap, die is opgegeven in de toepassing installatie vanaf de opdrachtregel of werkende directory configuratie-instellingen  

-   Al aanwezig zijn op de installatiekopie van besturingssysteem  

 Deze parameter is alleen geldig voor gebruik in het tweede syntaxisvoorbeeld.  

|**Parameter**|**Waarde**|  
|-|-|  
|**Vereist?**|**De waarde False**|  
|**Positie?**|**Met de naam**|  
|**Standaardwaarde**|:|  
|**Pijpleidinginvoer accepteren?**|**De waarde True** (**ByValue**)|  
|**Jokertekens accepteren?**|**De waarde False**|  

##### <a name="-bundle-switchparameter"></a>-Bundel [< SwitchParameter\>]  
 Deze parameter geeft aan dat de toepassing die het importeren van een toepassing die een bundel van twee of meer toepassingen. Deze parameter is alleen geldig voor gebruik in het vorige syntaxisvoorbeeld.  

|**Parameter**|**Waarde**|  
|-|-|  
|**Vereist?**|**De waarde False**|  
|**Positie?**|**Met de naam**|  
|**Standaardwaarde**|:|  
|**Pijpleidinginvoer accepteren?**|**De waarde True** (**ByValue**)|  
|**Jokertekens accepteren?**|**De waarde False**|  

##### <a name="commonparameters"></a>< CommonParameters\>  
 Deze cmdlet ondersteunt de volgende algemene parameters: *Uitgebreid, foutopsporing, ErrorAction,-ErrorVariable, -OutBuffer, OutVariable, WarningAction* en *WarningVariable.* Zie voor meer informatie het onderwerp 'about_CommonParameters' u openen kunt door de volgende opdracht te typen en vervolgens op ENTER:  

```  
Get-Help about_CommonParameters  
```  

#### <a name="outputs"></a>uitvoer  
 Deze cmdlet levert een **PSObject** object van het type dat verwijst naar de zojuist geïmporteerde toepassing.  

#### <a name="example-1"></a>Voorbeeld 1  

```  
Import-MDTApplication -Path "DS001:\Applications" -Name "Office 2010 Professional Plus 32-bit" ApplicationSourcePath "\\WDG-MDT-01\Source$\Office2010ProPlus\x86" DestinationFolder "Office2010ProPlusx86"  
```  

##### <a name="description"></a>Beschrijving  
 Dit voorbeeld wordt een toepassing met de bronbestanden op uit de gedeelde netwerkmap op geïmporteerd \\\WDG-MDT-01\Source$\Office2010ProPlus\x86 en kopieert de bronbestanden voor DS001:\Applications\Office2010ProPlusx86 binnen de implementatieshare. De bronbestanden worden bewaard.  

#### <a name="example-2"></a>Voorbeeld 2  

```  
Import-MDTApplication -Path "DS001:\Applications" -Name "Office 2010 Professional Plus 32-bit" ApplicationSourcePath "\\WDG-MDT-01\Source$\Office2010ProPlus\x86" DestinationFolder "Office2010ProPlusx86" -Move  
```  

##### <a name="description"></a>Beschrijving  
 Dit voorbeeld wordt een toepassing met de bronbestanden op uit de gedeelde netwerkmap op geïmporteerd \\\WDG-MDT-01\Source$\Office2010ProPlus\x86 en verplaatst de bronbestanden voor DS001:\Applications\Office2010ProPlusx86 binnen de implementatieshare. De bronbestanden worden verwijderd uit de gedeelde netwerkmap op \\\WDG-MDT-01\Source$\Office2010ProPlus\x86. De naam van de toepassing *Office 2012 Professional Plus 32-bits.*  

#### <a name="example-3"></a>Voorbeeld 3  

```  
Import-MDTApplication -Path "DS001:\Applications" -Name "Office 2010 Professional Plus 32-bit" NoSource  
```  

##### <a name="description"></a>Beschrijving  
 Dit voorbeeld wordt een toepassing met de naam geïmporteerd *Office 2012 Professional Plus 32-bits* met geen bronbestanden.  

#### <a name="example-4"></a>Voorbeeld 4  

```  
Import-MDTApplication -Path "DS001:\Applications" -Name "Woodgrove Bank Core Applications" Bundle  
```  

##### <a name="description"></a>Beschrijving  
 Dit voorbeeld wordt de toepassingenbundel van een met de naam geïmporteerd *Woodgrove Bank Core toepassingen.*  

###  <a name="Import-MDTDriver"></a>Importeren MDTDriver  
 Deze sectie beschrijft de **importeren MDTDriver** Windows PowerShell-cmdlet. Deze cmdlet uitvoeren vanuit een Windows PowerShell-console met de MDT-PowerShell-module geladen. Zie voor meer informatie over het starten van een Windows PowerShell-console met de MDT-PowerShell-module die geladen ' bij het laden van de MDT Windows PowerShell-module '.  

#### <a name="syntax"></a>Syntaxis  

```  
Import-MDTDriver [-Path <String>] -SourcePath <String[]> [ImportDuplicates] [<CommonParameters>]  
```  

#### <a name="description"></a>Beschrijving  
 Deze cmdlet kunt u een of meer apparaatstuurprogramma's importeren in een implementatieshare. Deze cmdlet wordt gezocht naar apparaatstuurprogramma's die beginnen bij de map die is opgegeven de *bronpad* parameter. Deze cmdlet zoekt meerdere apparaatstuurprogramma's in die mapstructuur.  

#### <a name="parameters"></a>Parameters  
 Deze subsectie bevat informatie over de verschillende parameters beschreven die kunnen worden gebruikt met de **importeren MDTDriver** cmdlet.  

##### <a name="-path-string"></a>-Path < String\>  
 Deze parameter bepaalt het volledig gekwalificeerde pad naar een bestaande map waar het apparaatstuurprogramma wordt geïmporteerd in de implementatieshare wordt geplaatst.  

> [!NOTE]
>  Als deze parameter niet is opgegeven, moet de Windows PowerShell-werkmap standaard naar de gewenste locatie binnen de implementatieshare. Deze parameter moet worden opgegeven als de *bronpad* parameter is niet opgegeven.  

|**Parameter**|**Waarde**|  
|-|-|  
|**Vereist?**|**De waarde False**|  
|**Positie?**|**Met de naam**|  
|**Standaardwaarde**|:|  
|**Pijpleidinginvoer accepteren?**|**De waarde False**|  
|**Jokertekens accepteren?**|**De waarde False**|  

##### <a name="-sourcepath-string-"></a>-SourcePath < tekenreeks [] >  
 Deze parameter geeft een of meer volledig gekwalificeerde paden in een tekenreeksmatrix voor de bronmappen waarin de bestanden van de apparaatstuurprogramma's bevinden. Elke mapstructuur beginnen met de map die is opgegeven in deze parameter wordt gezocht naar apparaatstuurprogramma's, inclusief alle submappen en de inhoud van het CAB-bestanden in de mapstructuur.  

> [!NOTE]
>  Als deze parameter niet is opgegeven, moet de Windows PowerShell-werkmap standaard naar de map waarin de bestanden van de apparaatstuurprogramma's bevinden. Deze parameter moet worden opgegeven als de *pad* parameter is niet opgegeven.  

|**Parameter**|**Waarde**|  
|-|-|  
|**Vereist?**|**De waarde True**|  
|**Positie?**|**1** en **met de naam**|  
|**Standaardwaarde**|:|  
|**Pijpleidinginvoer accepteren?**|**De waarde False**|  
|**Jokertekens accepteren?**|**De waarde False**|  

##### <a name="-importduplicates-switchparameter"></a>-ImportDuplicates [< SwitchParameter\>]  
 Deze parameter bepaalt of deze cmdlet moet worden gebruikt voor het importeren van dubbele apparaatstuurprogramma's. Dubbele apparaatstuurprogramma's worden standaard niet geïmporteerd. Dubbele apparaatstuurprogramma's worden gedetecteerd door te berekenen een hash-waarden voor alle bestanden in de map van een apparaat-stuurprogramma. Als de berekende hash-waarde overeenkomt met een ander stuurprogramma, wordt het apparaatstuurprogramma importeren om als dubbel beschouwd.  

 Als een dubbele stuurprogramma wordt gedetecteerd en deze parameter is niet opgegeven, wordt het apparaatstuurprogramma toegevoegd en gekoppeld aan de oorspronkelijke, bestaande apparaatstuurprogramma's.  

 Als deze parameter is:  

-   Opgegeven, worden klikt u vervolgens de dubbele apparaatstuurprogramma's geïmporteerd  

-   Niet wordt opgegeven, wordt klikt u vervolgens de apparaatstuurprogramma's toegevoegd en gekoppeld aan de oorspronkelijke, bestaande apparaatstuurprogramma 's  

|**Parameter**|**Waarde**|  
|-|-|  
|**Vereist?**|**De waarde False**|  
|**Positie?**|**Met de naam**|  
|**Standaardwaarde**|:|  
|**Pijpleidinginvoer accepteren?**|**De waarde True** (**ByValue**)|  
|**Jokertekens accepteren?**|**De waarde False**|  

##### <a name="commonparameters"></a>< CommonParameters\>  
 Deze cmdlet ondersteunt de volgende algemene parameters: *Uitgebreid, foutopsporing, ErrorAction,-ErrorVariable, -OutBuffer, OutVariable, WarningAction* en *WarningVariable.* Zie voor meer informatie het onderwerp 'about_CommonParameters' u openen kunt door de volgende opdracht te typen en vervolgens op ENTER:  

```  
Get-Help about_CommonParameters  
```  

#### <a name="outputs"></a>uitvoer  
 Deze cmdlet levert een of meer **PSObject** objecten (één voor elk geïmporteerd stuurprogramma) van het type.  

#### <a name="example-1"></a>Voorbeeld 1  

```  
Import-MDTDriver -Path "DS001:\Out-of-Box Drivers" SourcePath "\\WDG-MDT-01\Source$\Drivers"  
```  

##### <a name="description"></a>Beschrijving  
 In dit voorbeeld worden alle apparaatstuurprogramma's in de structuur van de mappen met de hoofdmap van de mapstructuur op geïmporteerd \\\WDG-MDT-01\Source$\Drivers. De apparaatstuurprogramma's worden opgeslagen in de map Out-of-Box stuurprogramma's in de share van de implementatie die is toegewezen aan de DS001: MDTProvder Windows PowerShell-station. Als er dubbele apparaatstuurprogramma's worden gedetecteerd, wordt de apparaatstuurprogramma's toegevoegd en gekoppeld aan de oorspronkelijke, bestaande apparaatstuurprogramma's in de implementatieshare.  

#### <a name="example-2"></a>Voorbeeld 2  

```  
$DriverSourcePath="\\WDG-MDT-01\Source$\VendorADrivers", "\\WDG-MDT-01\Source$\VendorBDrivers"  
Import-MDTDriver -Path "DS001:\Out-of-Box Drivers" SourcePath $DriverSourcePath ImportDuplicates  
```  

##### <a name="description"></a>Beschrijving  
 In dit voorbeeld worden alle apparaatstuurprogramma's in de structuur van de mappen in de tekenreeksmatrix $DriverSourcePath opgegeven geïmporteerd. De apparaatstuurprogramma's worden opgeslagen in de map Out-of-Box stuurprogramma's in de share van de implementatie die is toegewezen aan de DS001: MDTProvder Windows PowerShell-station. Als er dubbele apparaatstuurprogramma's worden gedetecteerd, wordt de dubbele apparaatstuurprogramma's worden geïmporteerd.  

###  <a name="Import-MDTOperatingSystem"></a>Importeren MDTOperatingSystem  
 Deze sectie beschrijft de **importeren MDTOperatingSystem** Windows PowerShell-cmdlet. Deze cmdlet uitvoeren vanuit een Windows PowerShell-console met de MDT-PowerShell-module geladen. Zie voor meer informatie over het starten van een Windows PowerShell-console met de MDT-PowerShell-module die geladen ' bij het laden van de MDT Windows PowerShell-module '.  

#### <a name="syntax"></a>Syntaxis  

```  
Import-MDTOperatingSystem [-Path <String>] -SourcePath <String> [-DestinationFolder <String>] [-Move] [<CommonParameters>]  
```  

 – of –  

```  
Import-MDTOperatingSystem [-Path <String>] [DestinationFolder <String>] -SourceFile <String> [SetupPath <String>] [-Move] [<CommonParameters>]  
```  

 – of –  

```  
Import-MDTOperatingSystem [-Path <String>] -WDSServer <String> [<CommonParameters>]  
```  

#### <a name="description"></a>Beschrijving  
 Deze cmdlet importeert een besturingssysteem in een implementatieshare. De volgende typen van besturingssysteem kunnen worden geïmporteerd met behulp van deze cmdlet:  

-   Besturingssystemen vanaf de oorspronkelijke bronbestanden met behulp van de *bronpad* parameters. Het eerste syntaxisvoorbeeld illustreert het gebruik van deze cmdlet voor dit type besturingssysteem importeren.  

-   Aangepaste besturingssystemen afbeeldingsbestanden, zoals Vastleginstallatiekopieën van verwijzing computers, met behulp van de *bronbestand* parameter. Het tweede syntaxisvoorbeeld illustreert het gebruik van deze cmdlet voor dit type besturingssysteem importeren.  

-   Installatiekopieën van besturingssystemen die aanwezig in Windows Deployment Services met behulp van zijn de *WDSServer* parameter. Het laatste syntaxisvoorbeeld illustreert het gebruik van deze cmdlet voor dit type besturingssysteem importeren.  

#### <a name="parameters"></a>Parameters  
 Deze subsectie bevat informatie over de verschillende parameters beschreven die kunnen worden gebruikt met de **importeren MDTOperatingSystem** cmdlet.  

##### <a name="-path-string"></a>-Path < String\>  
 Deze parameter bepaalt het volledig gekwalificeerde pad naar een bestaande map binnen de implementatieshare waar het besturingssysteem wordt geïmporteerd wordt geplaatst. Als de *doelmap* parameter wordt gebruikt, wordt de map die is opgegeven in de *doelmap* parameter wordt gemaakt onder de map die is opgegeven in deze parameter. Deze parameter wordt gebruikt in het gebruik van alle syntaxis voor deze cmdlet.  

> [!NOTE]
>  Als deze parameter niet is opgegeven, moet de Windows PowerShell-werkmap standaard naar de gewenste locatie binnen de implementatieshare.  

|**Parameter**|**Waarde**|  
|-|-|  
|**Vereist?**|**De waarde False**|  
|**Positie?**|**Met de naam**|  
|**Standaardwaarde**|:|  
|**Pijpleidinginvoer accepteren?**|**De waarde False**|  
|**Jokertekens accepteren?**|**De waarde False**|  

##### <a name="-sourcepath-string"></a>-SourcePath < tekenreeks\>  
 Deze parameter bepaalt het volledig gekwalificeerde pad naar de bronbestanden van het besturingssysteem voor het besturingssysteem die worden geïmporteerd in de implementatieshare. Deze parameter is alleen geldig voor gebruik in het eerste syntaxisvoorbeeld.  

|**Parameter**|**Waarde**|  
|-|-|  
|**Vereist?**|**De waarde True**|  
|**Positie?**|**Met de naam**|  
|**Standaardwaarde**|:|  
|**Pijpleidinginvoer accepteren?**|**De waarde False**|  
|**Jokertekens accepteren?**|**De waarde False**|  

##### <a name="-destinationfolder-string"></a>-Doelmap < tekenreeks\>  
 Deze parameter geeft de map in de implementatieshare waarop de bronbestanden van het besturingssysteem zijn om te worden geïmporteerd. Deze map wordt gemaakt onder de map die is opgegeven de *pad* parameter. Deze parameter is alleen geldig voor gebruik in de eerste en tweede syntaxisvoorbeelden.  

|**Parameter**|**Waarde**|  
|-|-|  
|**Vereist?**|**De waarde True**|  
|**Positie?**|**Met de naam**|  
|**Standaardwaarde**|:|  
|**Pijpleidinginvoer accepteren?**|**De waarde False**|  
|**Jokertekens accepteren?**|**De waarde False**|  

##### <a name="-move-switchparameter"></a>-Verplaatsen [< SwitchParameter\>]  
 Deze parameter wordt opgegeven als de bronbestanden van het besturingssysteem moeten worden verplaatst (in plaats van overgenomen) van de map waarin de bronbestanden van het besturingssysteem bevinden die is opgegeven in de *doelmap* parameter.  

 Als deze parameter is:  

-   Opgegeven, worden de bestanden worden verplaatst en de bestanden in de map die is opgegeven in de *doelmap* parameter zijn verwijderd  

-   Niet opgegeven, worden de bestanden worden gekopieerd en de bestanden in de map die is opgegeven in de *doelmap* parameter blijven behouden  

 Deze parameter is alleen geldig voor gebruik in de eerste en tweede syntaxisvoorbeelden.  

|**Parameter**|**Waarde**|  
|-|-|  
|**Vereist?**|**De waarde False**|  
|**Positie?**|**Met de naam**|  
|**Standaardwaarde**|:|  
|**Pijpleidinginvoer accepteren?**|**De waarde False**|  
|**Jokertekens accepteren?**|**De waarde False**|  

##### <a name="-sourcefile-string"></a>-Bronbestand < tekenreeks\>  
 Deze parameter bepaalt de volledig gekwalificeerde pad naar het besturingssysteem bron WIM-bestand voor het besturingssysteem dat wordt geïmporteerd in de implementatieshare. Deze parameter is alleen geldig voor gebruik in het tweede syntaxisvoorbeeld.  

|**Parameter**|**Waarde**|  
|-|-|  
|**Vereist?**|**De waarde True**|  
|**Positie?**|**Met de naam**|  
|**Standaardwaarde**|:|  
|**Pijpleidinginvoer accepteren?**|**De waarde False**|  
|**Jokertekens accepteren?**|**De waarde False**|  

##### <a name="-setuppath-string"></a>-SetupPath < tekenreeks\>  
 Deze parameter bepaalt het volledig gekwalificeerde pad naar het setup-bestanden voor het besturingssysteem die worden geïmporteerd samen met het WIM-bestand dat is opgegeven moeten in de *bronbestand* parameter. Deze parameter is alleen geldig voor gebruik in het tweede syntaxisvoorbeeld.  

|**Parameter**|**Waarde**|  
|-|-|  
|**Vereist?**|**De waarde True**|  
|**Positie?**|**Met de naam**|  
|**Standaardwaarde**|:|  
|**Pijpleidinginvoer accepteren?**|**De waarde False**|  
|**Jokertekens accepteren?**|**De waarde False**|  

##### <a name="-wdsserver-string"></a>-WDSServer < tekenreeks\>  
 Deze parameter bepaalt de naam van de Windows Deployment Services-server waarop de bestanden van de installatiekopie van besturingssysteem moeten worden geïmporteerd bevinden. Alle operationele afbeeldingsbestanden op de Windows Deployment Services-server worden geïmporteerd in de implementatieshare. De bestanden van de installatiekopie van het besturingssysteem zijn niet gekopieerd naar de implementatieshare. In plaats daarvan bevat de implementatieshare een koppeling naar elk besturingssysteem op de Windows Deployment Services-server.  

 Deze parameter is alleen geldig voor gebruik in het vorige syntaxisvoorbeeld.  

|**Parameter**|**Waarde**|  
|-|-|  
|**Vereist?**|**De waarde False**|  
|**Positie?**|**Met de naam**|  
|**Standaardwaarde**|:|  
|**Pijpleidinginvoer accepteren?**|**De waarde False**|  
|**Jokertekens accepteren?**|**De waarde False**|  

##### <a name="commonparameters"></a>< CommonParameters\>  
 Deze cmdlet ondersteunt de volgende algemene parameters: *Uitgebreid, foutopsporing, ErrorAction,-ErrorVariable, -OutBuffer, OutVariable, WarningAction* en *WarningVariable.* Zie voor meer informatie het onderwerp 'about_CommonParameters' u openen kunt door de volgende opdracht te typen en vervolgens op ENTER:  

```  
Get-Help about_CommonParameters  
```  

#### <a name="outputs"></a>uitvoer  
 Deze cmdlet levert een of meer **PSObject** objecten (één voor elk besturingssysteem dat is geïmporteerd) van het type.  

#### <a name="example-1"></a>Voorbeeld 1  

```  
Import-MDTOperatingSystem -Path "DS001:\Operating Systems" SourcePath "\\WDGMDT01\Source$\Windows8" DestinationFolder "Windows8x64"  
```  

##### <a name="description"></a>Beschrijving  
 Dit voorbeeld wordt een besturingssysteem geïmporteerd uit de gedeelde netwerkmap op \\\WDG-MDT-01\Source$\Windows8 en kopieert de bronbestanden voor DS001:\Operating Systems\Windows8x64 binnen de implementatieshare. De bronbestanden worden bewaard.  

#### <a name="example-2"></a>Voorbeeld 2  

```  
Import-MDTOperatingSystem -Path "DS001:\Operating Systems" SourcePath "\\WDGMDT01\Source$\Windows8" DestinationFolder "Windows8x64" -Move  
```  

##### <a name="description"></a>Beschrijving  
 Dit voorbeeld wordt een besturingssysteem geïmporteerd uit de gedeelde netwerkmap op \\\WDG-MDT-01\Source$\Windows8 en kopieert de bronbestanden voor DS001:\Operating Systems\Windows8x64 binnen de implementatieshare. De bronbestanden worden verwijderd uit de gedeelde netwerkmap op \\\WDG-MDT-01\Source$\Windows8.  

#### <a name="example-3"></a>Voorbeeld 3  

```  
Import-MDTOperatingSystem -Path "DS001:\Operating Systems" DestinationFolder "Windows8x64-Reference" –SourceFile "\\WDGMDT01\Capture$\WDG-REF-01_Capture.wim"  
```  

##### <a name="description"></a>Beschrijving  
 Dit voorbeeld wordt een besturingssysteem vastgelegde, aangepaste installatiekopiebestand (WIM-bestand) geïmporteerd uit \\\WDG-MDT-01\ $\WDG-REF-01_Capture.wim vastleggen en kopieert het installatiekopiebestand naar DS001:\Operating Systems\Windows8x64-verwijzing in de share van de implementatie. Het bron-WIM-bestand wordt behouden op de gedeelde netwerkmap.  

#### <a name="example-4"></a>Voorbeeld 4  

```  
Import-MDTOperatingSystem -Path "DS001:\Operating Systems" WDSServer "WDG-WDS-01"  
```  

##### <a name="description"></a>Beschrijving  
 In dit voorbeeld importeert u alle installatiekopieën van besturingssystemen van de Windows Deployment Services-server met de naam WDS-01-WDG en maakt een koppeling naar de installatiekopie voor elk besturingssysteem in DS001:\Operating systemen binnen de implementatieshare. De bronbestanden voor het installatiekopie van besturingssysteem op de Windows Deployment Services-server worden bewaard op de Windows Deployment Services-server.  

###  <a name="Import-MDTPackage"></a>Importeren MDTPackage  
 Deze sectie beschrijft de **importeren MDTPackage** Windows PowerShell-cmdlet. Deze cmdlet uitvoeren vanuit een Windows PowerShell-console met de MDT-PowerShell-module geladen. Zie voor meer informatie over het starten van een Windows PowerShell-console met de MDT-PowerShell-module die geladen ' bij het laden van de MDT Windows PowerShell-module '.  

#### <a name="syntax"></a>Syntaxis  

```  
Import-MDTPackage [-Path <String>] [[-SourcePath] <String[]>] [<CommonParameters>]  
```  

#### <a name="description"></a>Beschrijving  
 Deze cmdlet importeert een of meer pakketten van het besturingssysteem in een implementatieshare. De typen pakketten van het besturingssysteem die kunnen worden geïmporteerd omvatten beveiligingsupdates, taalpakketten of nieuwe onderdelen. Servicepacks moeten niet worden geïmporteerd als besturingssysteempakketten als ze offline kunnen niet worden geïnstalleerd.  

#### <a name="parameters"></a>Parameters  
 Deze subsectie bevat informatie over de verschillende parameters beschreven die kunnen worden gebruikt met de **importeren MDTPackage** cmdlet.  

##### <a name="-path-string"></a>-Path < String\>  
 Deze parameter bepaalt het volledig gekwalificeerde pad naar een bestaande map binnen de implementatieshare waar de geïmporteerde besturingssysteem-pakketten wordt geplaatst.  

> [!NOTE]
>  Als deze parameter niet is opgegeven, moet de Windows PowerShell-werkmap standaard naar de gewenste locatie binnen de implementatieshare.  

|**Parameter**|**Waarde**|  
|-|-|  
|**Vereist?**|**De waarde False**|  
|**Positie?**|**Met de naam**|  
|**Standaardwaarde**|:|  
|**Pijpleidinginvoer accepteren?**|**De waarde False**|  
|**Jokertekens accepteren?**|**De waarde False**|  

##### <a name="-sourcepath-string"></a>-SourcePath < tekenreeks\>  
 Deze parameter bepaalt de volledig gekwalificeerde pad naar een mapstructuur worden gescand voor besturingssysteempakketten te importeren. De structuur van de opgegeven map worden voor cab- en MSU-bestanden gescand. De CAB-bestanden in het MSU-bestanden voor MSU-bestanden worden automatisch worden opgehaald.  

|**Parameter**|**Waarde**|  
|-|-|  
|**Vereist?**|**De waarde True**|  
|**Positie?**|**1** en **met de naam**|  
|**Standaardwaarde**|:|  
|**Pijpleidinginvoer accepteren?**|**De waarde False**|  
|**Jokertekens accepteren?**|**De waarde False**|  

##### <a name="commonparameters"></a>< CommonParameters\>  
 Deze cmdlet ondersteunt de volgende algemene parameters: *Uitgebreid, foutopsporing, ErrorAction,-ErrorVariable, -OutBuffer, OutVariable, WarningAction* en *WarningVariable.* Zie voor meer informatie het onderwerp 'about_CommonParameters' u openen kunt door de volgende opdracht te typen en vervolgens op ENTER:  

```  
Get-Help about_CommonParameters  
```  

#### <a name="outputs"></a>uitvoer  
 Deze cmdlet levert een **PSObject** object van het type die verwijst naar de zojuist geïmporteerde pakket.  

#### <a name="example-1"></a>Voorbeeld 1  

```  
Import-MDTOperatingSystem -Path "DS001:\Packages" SourcePath "\\WDGMDT01\Source$\OSPackages"  
```  

##### <a name="description"></a>Beschrijving  
 Het volgende voorbeeld wordt gedeelde netwerkmap op \\\WDG-MDT-01\Source$\OSPackages voor besturingssysteem pakketten en kopieert de bronbestanden in de map DS001:\Packages in de implementatieshare. De bronbestanden worden verwijderd uit de gedeelde netwerkmap op \\\WDG-MDT-01\Source$\OSPackages.  

###  <a name="Import-MDTTaskSequence"></a>Importeren MDTTaskSequence  
 Deze sectie beschrijft de **importeren MDTTaskSequence** Windows PowerShell-cmdlet. Deze cmdlet uitvoeren vanuit een Windows PowerShell-console met de MDT-PowerShell-module geladen. Zie voor meer informatie over het starten van een Windows PowerShell-console met de MDT-PowerShell-module die geladen ' bij het laden van de MDT Windows PowerShell-module '.  

#### <a name="syntax"></a>Syntaxis  

```  
Import-MDTTaskSequence [-Path <String>] -Template <String> -Name <String> -ID <String> [[-Comments] <String>] [[-Version] <String>] [-OperatingSystemPath <String>] [-OperatingSystem <PSObject>] [-FullName <String>] [-OrgName <String>] [-HomePage <String>] [-ProductKey <String>] [-OverrideProductKey <String>] [-AdminPassword <String>] [<CommonParameters>]  
```  

#### <a name="description"></a>Beschrijving  
 Deze cmdlet kunt u een takenreeks importeren in een implementatieshare. De zojuist geïmporteerde takenreeks worden gebaseerd op een bestaande taak sequence-sjabloon opgegeven in de *sjabloon* eigenschap.  

#### <a name="parameters"></a>Parameters  
 Deze subsectie bevat informatie over de verschillende parameters beschreven die kunnen worden gebruikt met de **importeren MDTPackage** cmdlet.  

##### <a name="-path-string"></a>-Path < String\>  
 Deze parameter bepaalt het volledig gekwalificeerde pad naar een bestaande map binnen de implementatieshare waar de takenreeks wordt geïmporteerd wordt geplaatst. Standaard worden het pad moet verwijzen naar de besturingselement-map en/of een submap van de map van het besturingselement in de implementatieshare. De waarde van de *ID* parameter wordt gebruikt voor het maken van een submap binnen het pad dat is opgegeven in deze parameter.  

> [!NOTE]
>  Als deze parameter niet is opgegeven, moet de Windows PowerShell-werkmap standaard naar de gewenste locatie binnen de implementatieshare.  

|**Parameter**|**Waarde**|  
|-|-|  
|**Vereist?**|**De waarde False**|  
|**Positie?**|**Met de naam**|  
|**Standaardwaarde**|:|  
|**Pijpleidinginvoer accepteren?**|**De waarde False**|  
|**Jokertekens accepteren?**|**De waarde False**|  

##### <a name="-template-string"></a>-Template < tekenreeks\>  
 Deze parameter bepaalt de taak sequence-sjabloon moet worden gebruikt voor het importeren van de nieuwe takenreeks. Taak reeks sjablonen zijn XML-bestanden met de takenreeksstappen voor een bepaald type takenreeks wordt uitgevoerd. Als de takenreeks sjabloon bevindt zich in:  

-   De *installation_folder*\Templates map (waarbij *installation_folder* is de map waarin u MDT is geïnstalleerd), en vervolgens alleen de naam van het .XML-bestand vereist is.  

-   Een andere map, klikt u vervolgens het volledig gekwalificeerde pad inclusief de naam van de taak sequence sjabloon .xml, is vereist.  

 Voor meer informatie over de taak sequence-sjablonen die opgenomen in MDT voor implementaties van LTI zijn, Zie de sectie 'Maak een nieuwe taak volgorde in de implementatie-Workbench' in het document MDT *met behulp van de Microsoft Deployment Toolkit*.  

|**Parameter**|**Waarde**|  
|-|-|  
|**Vereist?**|**De waarde True**|  
|**Positie?**|**1** en **met de naam**|  
|**Standaardwaarde**|:|  
|**Pijpleidinginvoer accepteren?**|**De waarde False**|  
|**Jokertekens accepteren?**|**De waarde False**|  

##### <a name="-name-string"></a>-De naam < tekenreeks\>  
 Deze parameter geeft de naam van de takenreeks moet worden geïmporteerd. De waarde van deze parameter moet uniek zijn binnen de implementatieshare.  

|**Parameter**|**Waarde**|  
|-|-|  
|**Vereist?**|**De waarde True**|  
|**Positie?**|**2** en **met de naam**|  
|**Standaardwaarde**|:|  
|**Pijpleidinginvoer accepteren?**|**De waarde False**|  
|**Jokertekens accepteren?**|**De waarde False**|  

##### <a name="-id-string"></a>-ID < tekenreeks\>  
 Deze parameter geeft de id van de takenreeks moet worden geïmporteerd. De waarde van deze parameter moet uniek zijn binnen de implementatieshare. De waarde die is toegewezen aan deze parameter moet in hoofdletters worden ingevoerd en geen spaties of speciale tekens. Deze waarde wordt gebruikt voor het maken van een submap in de map die is opgegeven in de *pad* parameter, die opgenomen in de map van het besturingselement in de implementatieshare worden moet.  

|**Parameter**|**Waarde**|  
|-|-|  
|**Vereist?**|**De waarde True**|  
|**Positie?**|**3** en **met de naam**|  
|**Standaardwaarde**|:|  
|**Pijpleidinginvoer accepteren?**|**De waarde False**|  
|**Jokertekens accepteren?**|**De waarde False**|  

##### <a name="-comments-string"></a>-Opmerkingen < tekenreeks\>  
 Deze parameter bepaalt de tekst die aanvullende, beschrijvende informatie over de takenreeks geeft moet worden geïmporteerd. Deze beschrijvende informatie is zichtbaar in de implementatie-Workbench.  

|**Parameter**|**Waarde**|  
|-|-|  
|**Vereist?**|**De waarde False**|  
|**Positie?**|**4** en **met de naam**|  
|**Standaardwaarde**|:|  
|**Pijpleidinginvoer accepteren?**|**De waarde False**|  
|**Jokertekens accepteren?**|**De waarde False**|  

##### <a name="-version-string"></a>-Versie < tekenreeks\>  
 Deze parameter bepaalt het versienummer van de takenreeks moet worden geïmporteerd. De waarde van deze parameter is alleen ter informatie en niet wordt gebruikt door MDT voor versie-gerelateerde verwerking.  

|**Parameter**|**Waarde**|  
|-|-|  
|**Vereist?**|**De waarde False**|  
|**Positie?**|**4** en **met de naam**|  
|**Standaardwaarde**|:|  
|**Pijpleidinginvoer accepteren?**|**De waarde False**|  
|**Jokertekens accepteren?**|**De waarde False**|  

##### <a name="-operatingsystempath-string"></a>-OperatingSystemPath < tekenreeks\>  
 Deze parameter bepaalt het volledig gekwalificeerde Windows PowerShell-pad naar de map in de share van de implementatie die het besturingssysteem moet worden gebruikt met deze takenreeks, zoals DS001:\Operating Systems\Windows 8 bevat. Het besturingssysteem moet al bestaan in de implementatieshare waarop de takenreeks wordt geïmporteerd.  

> [!NOTE]
>  Als u deze parameter niet opgeeft en de takenreeks moet verwijzen naar een besturingssysteem, dan moet u opgeven de *OperatingSystem* parameter.  

|**Parameter**|**Waarde**|  
|-|-|  
|**Vereist?**|**De waarde False**|  
|**Positie?**|**Met de naam**|  
|**Standaardwaarde**|:|  
|**Pijpleidinginvoer accepteren?**|**De waarde False**|  
|**Jokertekens accepteren?**|**De waarde False**|  

##### <a name="-operatingsystem-psobject"></a>-OperatingSystem < PSObject\>  
 Deze parameter bepaalt het besturingssysteem object dat moet worden gebruikt met deze takenreeks. Het besturingssysteem moet al bestaan in de implementatieshare waarop de takenreeks wordt geïmporteerd.  

 U kunt de Windows PowerShell-object voor het gebruik van een besturingssysteem ophalen de **Get-Item** cmdlet, zoals in het volgende voorbeeld:  

```  
$OS=Get-Item "DS001:\Operating Systems\Windows 8"  
```  

 Voor meer informatie over de **Get-Item** cmdlet, Zie [met de Cmdlet Get-Item](http://technet.microsoft.com/library/ee176851).  

> [!NOTE]
>  Als u deze parameter niet opgeeft en de takenreeks moet verwijzen naar een besturingssysteem, dan moet u opgeven de *OperatingSystemPath* parameter.  

|**Parameter**|**Waarde**|  
|-|-|  
|**Vereist?**|**De waarde False**|  
|**Positie?**|**Met de naam**|  
|**Standaardwaarde**|:|  
|**Pijpleidinginvoer accepteren?**|**De waarde False**|  
|**Jokertekens accepteren?**|**De waarde False**|  

##### <a name="-fullname-string"></a>-FullName < tekenreeks\>  
 Deze parameter geeft de naam van de geregistreerde eigenaar van het besturingssysteem moet worden gebruikt met deze takenreeks. Deze naam wordt opgeslagen in de **RegisteredOwner** registersleutel op **HKEY_LOCAL_MACHINE\Software\Microsoft\Windows\CurrentVersion**. De waarde van deze parameter is opgenomen in het bestand Unattend.xml worden gekoppeld aan deze takenreeksen.  

|**Parameter**|**Waarde**|  
|-|-|  
|**Vereist?**|**De waarde False**|  
|**Positie?**|**Met de naam**|  
|**Standaardwaarde**|:|  
|**Pijpleidinginvoer accepteren?**|**De waarde False**|  
|**Jokertekens accepteren?**|**De waarde False**|  

##### <a name="-orgname-string"></a>-OrgName < tekenreeks\>  
 Deze parameter geeft de naam van de organisatie voor de geregistreerde eigenaar van het besturingssysteem moet worden gebruikt met deze takenreeks. Deze naam wordt opgeslagen in de **RegisteredOrganization** registersleutel op **HKEY_LOCAL_MACHINE\Software\Microsoft\Windows\CurrentVersion**. De waarde van deze parameter is opgenomen in het bestand Unattend.xml worden gekoppeld aan deze takenreeksen.  

|**Parameter**|**Waarde**|  
|-|-|  
|**Vereist?**|**De waarde False**|  
|**Positie?**|**Met de naam**|  
|**Standaardwaarde**|:|  
|**Pijpleidinginvoer accepteren?**|**De waarde False**|  
|**Jokertekens accepteren?**|**De waarde False**|  

##### <a name="-homepage-string"></a>-Startpagina < tekenreeks\>  
 Deze parameter geeft de URL moet worden gebruikt als de startpagina in Internet Explorer. De waarde van deze parameter is opgenomen in het bestand Unattend.xml worden gekoppeld aan deze takenreeksen.  

|**Parameter**|**Waarde**|  
|-|-|  
|**Vereist?**|**De waarde False**|  
|**Positie?**|**Met de naam**|  
|**Standaardwaarde**|:|  
|**Pijpleidinginvoer accepteren?**|**De waarde False**|  
|**Jokertekens accepteren?**|**De waarde False**|  

##### <a name="-productkey-string"></a>-ProductKey < tekenreeks\>  
 Deze parameter geeft de productcode moet worden gebruikt voor het besturingssysteem moet worden gebruikt met deze takenreeks. Deze productcode is alleen geldig voor handelsversies van Windows-besturingssystemen. De waarde van deze parameter is opgenomen in het bestand Unattend.xml worden gekoppeld aan deze takenreeksen.  

> [!NOTE]
>  Als deze parameter niet is opgegeven, moet klikt u vervolgens de productcode worden opgegeven bij het implementeren van deze takenreeks in de Wizard implementatie, het CustomSettings.ini-bestand of de MDT-database.  

|**Parameter**|**Waarde**|  
|-|-|  
|**Vereist?**|**De waarde False**|  
|**Positie?**|**Met de naam**|  
|**Standaardwaarde**|:|  
|**Pijpleidinginvoer accepteren?**|**De waarde False**|  
|**Jokertekens accepteren?**|**De waarde False**|  

##### <a name="-overrideproductkey-string"></a>-OverrideProductKey < tekenreeks\>  
 Deze parameter bepaalt de MAK-sleutel moet worden gebruikt voor het besturingssysteem moet worden gebruikt met deze takenreeks. Deze productcode is alleen geldig voor volume license-versies van Windows. De waarde van deze parameter is opgenomen in het bestand Unattend.xml worden gekoppeld aan deze takenreeksen.  

> [!NOTE]
>  Als deze parameter niet is opgegeven, moet klikt u vervolgens de MAK-sleutel worden opgegeven bij het implementeren van deze takenreeks in de Wizard implementatie, het CustomSettings.ini-bestand of de MDT-database.  

|**Parameter**|**Waarde**|  
|-|-|  
|**Vereist?**|**De waarde False**|  
|**Positie?**|**Met de naam**|  
|**Standaardwaarde**|:|  
|**Pijpleidinginvoer accepteren?**|**De waarde False**|  
|**Jokertekens accepteren?**|**De waarde False**|  

##### <a name="-adminpassword-string"></a>-AdminPassword < tekenreeks\>  
 Deze parameter geeft het wachtwoord moet worden toegewezen aan de ingebouwde, lokale Administrator-account op de doelcomputer. De waarde van deze parameter is opgenomen in het bestand Unattend.xml worden gekoppeld aan deze takenreeksen.  

> [!NOTE]
>  Als deze parameter niet is opgegeven, klikt u vervolgens het wachtwoord moet worden toegewezen aan de ingebouwde, kunnen lokale Administrator-account op de doelcomputer moet worden opgegeven bij het implementeren van deze takenreeks in de Wizard implementatie, het CustomSettings.ini-bestand of de MDT-database.  

|**Parameter**|**Waarde**|  
|-|-|  
|**Vereist?**|**De waarde False**|  
|**Positie?**|**Met de naam**|  
|**Standaardwaarde**|:|  
|**Pijpleidinginvoer accepteren?**|**De waarde False**|  
|**Jokertekens accepteren?**|**De waarde False**|  

##### <a name="commonparameters"></a>< CommonParameters\>  
 Deze cmdlet ondersteunt de volgende algemene parameters: *Uitgebreid, foutopsporing, ErrorAction,-ErrorVariable, -OutBuffer, OutVariable, WarningAction* en *WarningVariable.* Zie voor meer informatie het onderwerp 'about_CommonParameters' u openen kunt door de volgende opdracht te typen en vervolgens op ENTER:  

```  
Get-Help about_CommonParameters  
```  

#### <a name="outputs"></a>uitvoer  
 Deze cmdlet levert een **PSObject** object van het type dat verwijst naar de zojuist geïmporteerde takenreeks.  

#### <a name="example-1"></a>Voorbeeld 1  

```  
Import-MDTTaskSequence -Path "DS001:\Control" –Template "Client.xml" –Name "Deploy Windows 8 to Reference Computer" –ID "WIN8REFERENCE" –Comments "Task sequence for deploying Windows 8 to the reference computer (WDG-REF-01)" –Version "1.00" –OperatingSystemPath "DS001:\Operating Systems\Windows 8_x64" –FullName "Woodgrove Bank Employee" –OrgName "Woodgrove Bank" HomePage "http://www.woodgrovebank.com"  OverrideProductKey "1234512345123451234512345" AdministratorPassword "P@ssw0rd"  
```  

##### <a name="description"></a>Beschrijving  
 Dit voorbeeld wordt een takenreeks met de naam geïmporteerd *Windows 8 implementeren naar referentiecomputer* en maakt de takenreeks in de map DS001:\Control\WIN8REFERENCE in de implementatieshare. De opmerking 'Voor de Takenreeks voor het implementeren van Windows 8 op de referentiecomputer (WDG-REF-01),' is toegewezen aan de takenreeks wordt uitgevoerd. Het versienummer van de takenreeks is ingesteld op **1,00**.  

 Het besturingssysteem die is gekoppeld aan de takenreeks bevindt zich op DS001:\Operating Systems\Windows 8_x64 in de implementatieshare. De geregistreerde eigenaar van het besturingssysteem wordt zo ingesteld dat **Woodgrove Bank werknemer**. De geregistreerde organisatienaam van het besturingssysteem wordt zo ingesteld dat **Woodgrove Bank**. De startpagina van Internet Explorer wordt hier standaard **http://www.woodgrovebank.com**. Het wachtwoord voor de lokale ingebouwde Administrator-account wordt ingesteld op een waarde van  **P@ssw0rd** . De productcode voor het besturingssysteem wordt zo ingesteld dat **1234512345123451234512345**.  

#### <a name="example-2"></a>Voorbeeld 2  

```  
$OSObject=Get-Item "DS001:\Operating Systems\Windows 8_x64"  
Import-MDTTaskSequence -Path "DS001:\Control" –Template "Client.xml" –Name "Deploy Windows 8 to Reference Computer" –ID "WIN8REFERENCE" –Comments "Task sequence for deploying Windows 8 to the reference computer (WDG-REF-01)" –Version "1.00"–OperatingSystem $OSObject –FullName "Woodgrove Bank Employee" –OrgName "Woodgrove Bank" HomePage "http://www.woodgrovebank.com"  AdministratorPassword "P@ssw0rd"  
```  

##### <a name="description"></a>Beschrijving  
 Dit voorbeeld wordt een takenreeks met de naam geïmporteerd *Windows 8 implementeren naar referentiecomputer* en maakt de takenreeks in de map DS001:\Control\WIN8REFERENCE in de implementatieshare. De opmerking 'Voor de Takenreeks voor het implementeren van Windows 8 op de referentiecomputer (WDG-REF-01),' is toegewezen aan de takenreeks wordt uitgevoerd. Het versienummer van de takenreeks is ingesteld op **1,00**.  

 Het besturingssysteem die is gekoppeld aan de takenreeks bevindt zich op DS001:\Operating Systems\Windows 8_x64 in de implementatieshare, die wordt doorgegeven met de cmdlet via de *$OSObject* variabele. De *$OSObject* variabele is ingesteld op een bestaande besturingssysteem object met behulp van de **Get-Item** cmdlet.  

 De geregistreerde eigenaar van het besturingssysteem wordt zo ingesteld dat **Woodgrove Bank werknemer**. De geregistreerde organisatienaam van het besturingssysteem wordt zo ingesteld dat **Woodgrove Bank**. De startpagina van Internet Explorer wordt hier standaard **http://www.woodgrovebank.com**. Het wachtwoord voor de lokale ingebouwde Administrator-account wordt ingesteld op een waarde van  **P@ssw0rd** . De productcode voor het besturingssysteem moet worden opgegeven bij het implementeren van deze takenreeks in de Wizard implementatie, het CustomSettings.ini-bestand of de MDT-database.  

###  <a name="New-MDTDatabase"></a>Nieuwe MDTDatabase  
 Deze sectie beschrijft de **nieuw MDTDatabase** Windows PowerShell-cmdlet. Deze cmdlet uitvoeren vanuit een Windows PowerShell-console met de MDT-PowerShell-module geladen. Zie voor meer informatie over het starten van een Windows PowerShell-console met de MDT-PowerShell-module die geladen ' bij het laden van de MDT Windows PowerShell-module '.  

#### <a name="syntax"></a>Syntaxis  

```  
New-MDTDatabase [-Path <String>] [-Force] -SQLServer <String> [-Instance <String>] [-Port <String>] [-Netlib <String>] -Database <String> [-SQLShare <String>] [<CommonParameters>]  
```  

#### <a name="description"></a>Beschrijving  
 Deze cmdlet maakt een nieuwe MDT-DB-database die is gekoppeld aan een implementatieshare. Elke implementatieshare kan worden gekoppeld aan slechts één MDT DB-database.  

#### <a name="parameters"></a>Parameters  
 Deze subsectie bevat informatie over de verschillende parameters beschreven die kunnen worden gebruikt met de **nieuw MDTDatabase** cmdlet.  

##### <a name="-path-string"></a>-Path < String\>  
 Deze parameter bepaalt het volledig gekwalificeerde pad voor Windows PowerShell voor de implementatieshare waarop de nieuwe MDT-DB-database zal worden gekoppeld is geplaatst.  

> [!NOTE]
>  Als deze parameter niet is opgegeven, moet de Windows PowerShell-werkmap standaard naar de gewenste locatie binnen de implementatieshare.  

|**Parameter**|**Waarde**|  
|-|-|  
|**Vereist?**|**De waarde False**|  
|**Positie?**|**Met de naam**|  
|**Standaardwaarde**|:|  
|**Pijpleidinginvoer accepteren?**|**De waarde False**|  
|**Jokertekens accepteren?**|**De waarde False**|  

##### <a name="-force-switchparameter"></a>-Force [< SwitchParameter\>]  
 Deze parameter wordt aangegeven dat tabellen in de MDT-database moeten opnieuw worden gemaakt als de database die is opgegeven in de *Database* parameter al bestaat. Als deze parameter is:  

-   Opgegeven, worden de tabellen in een bestaande database van de MDT zal opnieuw worden gemaakt  

-   Dit wordt weggelaten, wordt klikt u vervolgens de tabellen in een bestaande database van de MDT niet opnieuw gemaakt  

|**Parameter**|**Waarde**|  
|-|-|  
|**Vereist?**|**De waarde False**|  
|**Positie?**|**Met de naam**|  
|**Standaardwaarde**|:|  
|**Pijpleidinginvoer accepteren?**|**De waarde True** (**ByValue**)|  
|**Jokertekens accepteren?**|**De waarde False**|  

##### <a name="-sqlserver-string"></a>SQL Server - < tekenreeks\>  
 Deze parameter bepaalt de naam van de computer met SQL Server waar de nieuwe MDT-DB-database wordt gemaakt.  

|**Parameter**|**Waarde**|  
|-|-|  
|**Vereist?**|**De waarde True**|  
|**Positie?**|**Met de naam**|  
|**Standaardwaarde**|:|  
|**Pijpleidinginvoer accepteren?**|**De waarde False**|  
|**Jokertekens accepteren?**|**De waarde False**|  

##### <a name="-instance-string"></a>-Exemplaar < tekenreeks\>  
 Deze parameter bepaalt de SQL Server-exemplaar waarin de nieuwe MDT-DB-database wordt gemaakt. Als deze parameter wordt weggelaten, wordt de MDT-DB-database gemaakt in het standaardexemplaar van SQL Server.  

> [!NOTE]
>  De SQL Browser-service moet worden uitgevoerd op de computer met SQL Server voor de cmdlet om te bepalen de instantie die is opgegeven in deze parameter.  

|**Parameter**|**Waarde**|  
|-|-|  
|**Vereist?**|**De waarde False**|  
|**Positie?**|**Met de naam**|  
|**Standaardwaarde**|:|  
|**Pijpleidinginvoer accepteren?**|**De waarde False**|  
|**Jokertekens accepteren?**|**De waarde False**|  

##### <a name="-port-string"></a>-Poort < tekenreeks\>  
 Deze parameter bepaalt de TCP-poort moet worden gebruikt in de communicatie met de SQL Server-exemplaar dat is opgegeven in de *SQLServer* parameter. De standaardpoort die gebruikmaakt van SQL Server is 1433. Deze parameter opgeven wanneer SQL Server is geconfigureerd voor gebruik van een andere poort dan de standaardwaarde. De waarde van deze parameter moet overeenkomen met de poort die is geconfigureerd voor SQL Server.  

|**Parameter**|**Waarde**|  
|-|-|  
|**Vereist?**|**De waarde False**|  
|**Positie?**|**Met de naam**|  
|**Standaardwaarde**|:|  
|**Pijpleidinginvoer accepteren?**|**De waarde False**|  
|**Jokertekens accepteren?**|**De waarde False**|  

##### <a name="-netlib-string"></a>-Netlib < tekenreeks\>  
 Deze parameter geeft u de SQL-netwerkbibliotheek gebruikt in de communicatie met de SQL Server-exemplaar dat is opgegeven in de *SQLServer* parameter. De parameter kan worden ingesteld op een van de volgende waarden:  

-   **DBNMPNTW**, dat wordt gebruikt voor het opgeven van named pipes-communicatie  

-   **DBSMSOCN**, dat wordt gebruikt voor het opgeven van TCP/IP-sockets communicatie  

 Als deze parameter niet is opgegeven, wordt de netwerkbibliotheek van named pipes SQL (DBNMPNTW) gebruikt.  

|**Parameter**|**Waarde**|  
|-|-|  
|**Vereist?**|**De waarde False**|  
|**Positie?**|**Met de naam**|  
|**Standaardwaarde**|:|  
|**Pijpleidinginvoer accepteren?**|**De waarde False**|  
|**Jokertekens accepteren?**|**De waarde False**|  

##### <a name="-database-string"></a>-Database < tekenreeks\>  
 Deze parameter geeft de naam van de database worden gemaakt in de SQL Server-exemplaar dat is opgegeven in de *exemplaar* parameter op de SQL-Server die is opgegeven in de *SQLServer* parameter. De standaardlocatie en naamconventie wordt voor de database en logboekbestanden worden gebruikt bij het maken van de database.  

 Als de database die is opgegeven in deze parameter is al bestaat, wordt de database niet opnieuw gemaakt. De tabellen in de database kunnen opnieuw worden gemaakt op basis van de *Force* parameter.  

|**Parameter**|**Waarde**|  
|-|-|  
|**Vereist?**|**De waarde True**|  
|**Positie?**|**Met de naam**|  
|**Standaardwaarde**|:|  
|**Pijpleidinginvoer accepteren?**|**De waarde False**|  
|**Jokertekens accepteren?**|**De waarde False**|  

##### <a name="-sqlshare-string"></a>-SQLShare < tekenreeks\>  
 Deze parameter bepaalt de naam van een gedeelde netwerkmap op de computer waarop SQL Server wordt uitgevoerd. Deze verbinding wordt gebruikt voor verbindingen instellen met behulp van het protocol Named Pipes geïntegreerde Windows-beveiliging.  

> [!NOTE]
>  Als deze parameter niet opgenomen is, is geen beveiligde IPC$ verbinding gemaakt. Als gevolg hiervan named-pipes communicatie met SQL Server kan mislukken.  

|**Parameter**|**Waarde**|  
|-|-|  
|**Vereist?**|**De waarde False**|  
|**Positie?**|**Met de naam**|  
|**Standaardwaarde**|:|  
|**Pijpleidinginvoer accepteren?**|**De waarde False**|  
|**Jokertekens accepteren?**|**De waarde False**|  

##### <a name="commonparameters"></a>< CommonParameters\>  
 Deze cmdlet ondersteunt de volgende algemene parameters: *Uitgebreid, foutopsporing, ErrorAction,-ErrorVariable, -OutBuffer, OutVariable, WarningAction* en *WarningVariable.* Zie voor meer informatie het onderwerp 'about_CommonParameters' u openen kunt door de volgende opdracht te typen en vervolgens op ENTER:  

```  
Get-Help about_CommonParameters  
```  

#### <a name="outputs"></a>uitvoer  
 Deze cmdlet levert een **PSObject** object van het type voor de nieuwe MDT-database die is gemaakt.  

#### <a name="example-1"></a>Voorbeeld 1  

```  
New-MDTDatabase -Path "DS001:" –SQLServer "WDGSQL01" Database "MDTDB" –SQLShare "\\WDGSQL01\MDTShare$"  
```  

##### <a name="description"></a>Beschrijving  
 In dit voorbeeld maakt u een MDT-database met de naam *MDTDB* in de standaardinstantie van SQL Server op een computer met de naam *WDG-SQL-01.* Als de database al bestaat, wordt de tabellen in de bestaande database niet opnieuw gemaakt. De verbinding wordt gemaakt met behulp van de standaard SQL Server-TCP-poort en het protocol Named Pipes.  

#### <a name="example-2"></a>Voorbeeld 2  

```  
New-MDTDatabase -Path "DS001:" –Force –SQLServer "WDGSQL01" –Instance "MDTInstance" Database "MDTDB" –SQLShare "\\WDGSQL01\MDTShare$"  
```  

##### <a name="description"></a>Beschrijving  
 In dit voorbeeld maakt u een MDT-database met de naam *MDTDB* in SQL Server-exemplaar met de naam *MDTInstance* op een computer met de naam *WDG-SQL-01.* Als de database al bestaat, wordt opnieuw gemaakt in de tabellen in de bestaande database. De verbinding wordt gemaakt met behulp van de standaard SQL Server-TCP-poort en het protocol Named Pipes.  

###  <a name="Remove-MDTMonitorData"></a>Verwijder MDTMonitorData  
 Deze sectie beschrijft de **Get-MDTPersistentDrive** Windows PowerShell-cmdlet. Deze cmdlet uitvoeren vanuit een Windows PowerShell-console met de MDT-PowerShell-module geladen. Zie voor meer informatie over het starten van een Windows PowerShell-console met de MDT-PowerShell-module die geladen ' bij het laden van de MDT Windows PowerShell-module '.  

#### <a name="syntax"></a>Syntaxis  

```  
Remove-MDTMonitorData [-Path <String>] [-ID <Int32>] [<CommonParameters>]  
```  

 – of –  

```  
Remove-MDTMonitorData [-Path <String>] [-ComputerObject <PSObject>] [<CommonParameters>]  
```  

#### <a name="description"></a>Beschrijving  
 Deze cmdlet verwijdert verzamelde bewakingsgegevens van de bestaande verzamelde bewakingsgegevens in een implementatieshare. U kunt de bewakingsgegevens verwijderen door op te geven identificeren de:  

-   Id (ID) van het controle-item voor een specifieke implementatie-share. De bewaking item-id's worden automatisch gegenereerd en is toegewezen aan het artikel wanneer het item is gemaakt voor de implementatieshare. Het eerste syntaxisvoorbeeld illustreert dit gebruik.  

-   Het computerobject voor de bewaking-item in de implementatieshare. Het computerobject kan worden verkregen met behulp van de **Get-MDTMonitorData** cmdlet. Het laatste syntaxisvoorbeeld illustreert dit gebruik.  

> [!NOTE]
>  Wanneer de bewakingsgegevens is verwijderd, is er geen methode voor het herstellen van de gegevens.  

#### <a name="parameters"></a>Parameters  
 Deze subsectie bevat informatie over de verschillende parameters beschreven die kunnen worden gebruikt met de **Get - MDTMonitorData** cmdlet.  

##### <a name="-path-string"></a>-Path < String\>  
 Deze parameter bepaalt de **MDTProvider** Windows PowerShell-station voor de gewenste implementatieshare.  

> [!NOTE]
>  Als deze parameter niet is opgegeven, moet de Windows PowerShell-werkmap standaard naar een locatie binnen de gewenste MDTProvider Windows PowerShell-station.  

|**Parameter**|**Waarde**|  
|-|-|  
|**Vereist?**|**De waarde False**|  
|**Positie?**|**Met de naam**|  
|**Standaardwaarde**|:|  
|**Pijpleidinginvoer accepteren?**|**De waarde False**|  
|**Jokertekens accepteren?**|**De waarde False**|  

##### <a name="-id-nullable"></a>-ID < NULL-waarden bevatten\>  
 Deze parameter bepaalt de controle gegevensitem worden verwijderd met de id van het controle-gegevensitem. Als deze parameter niet is opgegeven, wordt de *ComputerObject* parameter moet worden opgegeven voor het identificeren van een bepaalde controle gegevensitem.  

|**Parameter**|**Waarde**|  
|-|-|  
|**Vereist?**|**De waarde False**|  
|**Positie?**|**Met de naam**|  
|**Standaardwaarde**|:|  
|**Pijpleidinginvoer accepteren?**|**De waarde True** (**ByValue**)|  
|**Jokertekens accepteren?**|**De waarde False**|  

##### <a name="-computerobject-psobject"></a>-ComputerObject < PSObject\>  
 Deze parameter bepaalt de controle gegevensitem worden verwijderd met behulp van een computerobject. Als deze parameter niet is opgegeven, wordt de *ID* parameter moet worden opgegeven voor het identificeren van een bepaalde controle gegevensitem.  

|**Parameter**|**Waarde**|  
|-|-|  
|**Vereist?**|**De waarde False**|  
|**Positie?**|**Met de naam**|  
|**Standaardwaarde**|:|  
|**Pijpleidinginvoer accepteren?**|**De waarde True** (**ByValue**)|  
|**Jokertekens accepteren?**|**De waarde False**|  

##### <a name="commonparameters"></a>< CommonParameters\>  
 Deze cmdlet ondersteunt de volgende algemene parameters: *Uitgebreid, foutopsporing, ErrorAction,-ErrorVariable, -OutBuffer, OutVariable, WarningAction* en *WarningVariable.* Zie voor meer informatie het onderwerp 'about_CommonParameters' u openen kunt door de volgende opdracht te typen en vervolgens op ENTER:  

```  
Get-Help about_CommonParameters  
```  

#### <a name="outputs"></a>uitvoer  
 Deze cmdlet kan de uitvoer een **tekenreeks** het type object als de *uitgebreid* algemene parameter is opgenomen; anders wordt geen uitvoer gegenereerd.  

#### <a name="example-1"></a>Voorbeeld 1  

```  
Remove-MDTMonitorData -Path "DS001:" -ID 3  
```  

##### <a name="description"></a>Beschrijving  
 In dit voorbeeld verwijdert u de bewaking gegevensitem met een ID die een waarde van heeft **3** delen van de implementatie in het Windows PowerShell-pad DS001:.  

#### <a name="example-2"></a>Voorbeeld 2  

```  
Remove-MDTMonitorData -ID 3  
```  

##### <a name="description"></a>Beschrijving  
 In dit voorbeeld verwijdert u de bewaking gegevensitem met een ID die een waarde van heeft **3** delen van de implementatie op het standaardpad voor Windows PowerShell.  

#### <a name="example-3"></a>Voorbeeld 3  

```  
$MonitorObject=Get-MDTMonitorData | Where-Object {$_.Name eq 'WDG-REF-01'}  
Remove-MDTMonitorData -ComputerObject $MonitorObject  
```  

##### <a name="description"></a>Beschrijving  
 In het volgende voorbeeld worden alle bewaking gegevensitem waar de naam van de computer WDG-REF-01 is verwijderd. Het object is gevonden met behulp van de **Get-MDTMonitorData** cmdlet en de **Where-Object** cmdlet. Voor meer informatie over de **Where-Object** cmdlet, Zie [met de Cmdlet Where-Object](http://technet.microsoft.com/library/ee177028.aspx).  

###  <a name="Remove-MDTPersistentDrive"></a>Verwijder MDTPersistentDrive  
 Deze sectie beschrijft de **verwijderen MDTPersistentDriveWindows** Windows PowerShell-cmdlet. Deze cmdlet uitvoeren vanuit een Windows PowerShell-console met de MDT-PowerShell-module geladen. Zie voor meer informatie over het starten van een Windows PowerShell-console met de MDT-PowerShell-module die geladen ' bij het laden van de MDT Windows PowerShell-module '.  

#### <a name="syntax"></a>Syntaxis  

```  
Remove-MDTPersistentDrive [-Name] <String> [[-InputObject] <PSObject>] [<CommonParameters>]  
```  

#### <a name="description"></a>Beschrijving  
 Deze cmdlet verwijdert u een bestaand Windows PowerShell-station gemaakt met behulp van de **MDTProvider** uit de lijst met stations die zijn opgeslagen in de implementatie-Workbench of in een Windows PowerShell-sessie met de [ Restore MDTPersistentDrive](#Restore-MDTPersistentDrive) cmdlet. Deze cmdlet wordt aangeroepen wanneer een implementatieshare is afgesloten in (verwijderd van) de implementatie-Workbench.  

> [!NOTE]
>  De lijst met vastgelegde **MDTProvider** stations wordt bewaard in een per-gebruiker op basis van het gebruikersprofiel.  

 De lijst met vastgelegde **MDTProvider** stations kunnen worden weergegeven met behulp van de **Get-MDTPersistentDrive** cmdlet. Een station MDTProvider kan worden toegevoegd aan de lijst met persistente stations met behulp van de **toevoegen MDTPersistentDrive** cmdlet.  

#### <a name="parameters"></a>Parameters  
 Deze subsectie bevat informatie over de verschillende parameters beschreven die kunnen worden gebruikt met de **toevoegen MDTPersistentDriveWindows** cmdlet.  

##### <a name="-name-string"></a>-De naam < tekenreeks\>  
 Geeft de naam van een Windows PowerShell-station gemaakt met behulp van de MDT-provider en komt overeen met een bestaande implementatieshare. De naam is gemaakt met de [nieuw PSDrive](http://technet.microsoft.com/library/dd315340.aspx) cmdlet en geven de **MDTProvider** in de *PSProvider* parameter.  

 Voor meer informatie over het maken van een nieuwe Windows PowerShell-station met de **MDTProvider** en het maken van een implementatie delen met Windows PowerShell, Zie de sectie 'Maken van een implementatie delen met behulp van Windows PowerShell' in de MDT-document *Microsoft Deployment Toolkit voorbeelden Guide*.  

|**Parameter**|**Waarde**|  
|-|-|  
|**Vereist?**|**De waarde True**|  
|**Positie?**|**1** en **met de naam**|  
|**Standaardwaarde**|**Geen**|  
|**Pijpleidinginvoer accepteren?**|**De waarde True** (**ByValue**)|  
|**Jokertekens accepteren?**|**De waarde False**|  

##### <a name="-inputobject-psobject"></a>-InputObject < PSObject\>  
 Deze parameter geeft u een Windows PowerShell-station-object dat eerder in het proces is gemaakt. Voer een **PSObject** object, zoals een gegenereerd door de [nieuw PSDrive](http://technet.microsoft.com/library/dd315340.aspx) cmdlet.  

|**Parameter**|**Waarde**|  
|-|-|  
|**Vereist?**|**De waarde False**|  
|**Positie?**|**2** en **met de naam**|  
|**Standaardwaarde**|:|  
|**Pijpleidinginvoer accepteren?**|**De waarde True** (**ByValue**)|  
|**Jokertekens accepteren?**|**De waarde False**|  

##### <a name="commonparameters"></a>< CommonParameters\>  
 Deze cmdlet ondersteunt de volgende algemene parameters: *Uitgebreid, foutopsporing, ErrorAction,-ErrorVariable, -OutBuffer, OutVariable, WarningAction* en *WarningVariable.* Zie voor meer informatie het onderwerp 'about_CommonParameters' u openen kunt door de volgende opdracht te typen en vervolgens op ENTER:  

```  
Get-Help about_CommonParameters  
```  

#### <a name="outputs"></a>uitvoer  
 Deze cmdlet biedt geen uitvoer.  

#### <a name="example-1"></a>Voorbeeld 1  

```  
Remove-MDTPersistentDrive –Name "DS001:"  
```  

##### <a name="description"></a>Beschrijving  
 In dit voorbeeld verwijdert u de share van de implementatie met de naam van de Windows PowerShell-station van *DS001* uit de lijst met persistente stations.  

#### <a name="example-2"></a>Voorbeeld 2  

```  
$MDTPSDrive = Get-PSDrive | Where-Object {$_.Root -eq "C:\DeploymentShare" -and $_.Provider -like "*MDTProvider"}   
Remove-MDTPersistentDrive –InputObject $MDTPSDrive  
```  

##### <a name="description"></a>Beschrijving  
 In het volgende voorbeeld wordt de implementatieshare op C:\DeploymentShare$ verwijderd uit de lijst met persistente stations. De **GetPSDrive** en **Where-Object** cmdlets worden gebruikt voor het retourneren van de MDT persistent Windows PowerShell-station aan de **verwijderen MDTPersistentDrive** de metdecmdlet*$MDTPSDrive* variabele. Voor meer informatie over de **Where-Object** cmdlet, Zie [met de Cmdlet Where-Object](http://technet.microsoft.com/library/ee177028.aspx). Voor meer informatie over de **Get-PSDrive** cmdlet, Zie [met de Cmdlet Get-PSDrive](http://technet.microsoft.com/library/ee176856).  

###  <a name="Restore-MDTPersistentDrive"></a>Restore MDTPersistentDrive  
 Deze sectie beschrijft de **terugzetten MDTPersistentDrive** Windows PowerShell-cmdlet. Deze cmdlet uitvoeren vanuit een Windows PowerShell-console met de MDT-PowerShell-module geladen. Zie voor meer informatie over het starten van een Windows PowerShell-console met de MDT-PowerShell-module die geladen ' bij het laden van de MDT Windows PowerShell-module '.  

#### <a name="syntax"></a>Syntaxis  

```  
Restore-MDTPersistentDrive [-Force] [<CommonParameters>]  
```  

#### <a name="description"></a>Beschrijving  
 Deze cmdlet herstelt een persistente MDT Windows PowerShell-station aan de lijst met actieve Windows PowerShell-station voor elke implementatieshare die is toegevoegd aan de lijst met persistente MDT Windows PowerShell-stations. De lijst met persistente MDT Windows PowerShell-stations wordt beheerd met behulp van de [toevoegen MDTPersistentDrive](#Add-MDTPersistentDrive) en [verwijderen MDTPersistentDrive](#Remove-MDTPersistentDrive) cmdlets of de implementatie-Workbench.  

 Deze cmdlet roept de **nieuw PSDrive** cmdlet voor het maken van een Windows PowerShell-station voor elke schijf in de MDT lijst permanente. Persistente MDT Windows PowerShell-stations zijn vergelijkbaar met persistente netwerkstations.  

> [!NOTE]
>  Deze lijst met persistente MDT Windows PowerShell-stations wordt bewaard in per gebruiker en zijn opgeslagen in het gebruikersprofiel.  

#### <a name="parameters"></a>Parameters  
 Deze subsectie bevat informatie over de verschillende parameters beschreven die kunnen worden gebruikt met de **terugzetten MDTPersistentDrive** cmdlet.  

##### <a name="-force-switchparameter"></a>-Force [< SwitchParameter\>]  
 Deze parameter bepaalt de implementatieshare moet worden bijgewerkt wanneer hersteld (indien nodig). Als deze parameter is:  

-   Opgegeven, worden de implementatieshare wordt bijgewerkt wanneer hersteld (indien nodig)  

-   Dit wordt weggelaten, zullen klikt u vervolgens implementatieshare niet worden bijgewerkt wanneer hersteld  

|**Parameter**|**Waarde**|  
|-|-|  
|**Vereist?**|**De waarde False**|  
|**Positie?**|**Met de naam**|  
|**Standaardwaarde**|:|  
|**Pijpleidinginvoer accepteren?**|**De waarde True** (**ByValue**)|  
|**Jokertekens accepteren?**|**De waarde False**|  

##### <a name="commonparameters"></a>< CommonParameters\>  
 Deze cmdlet ondersteunt de volgende algemene parameters: *Uitgebreid, foutopsporing, ErrorAction,-ErrorVariable, -OutBuffer, OutVariable, WarningAction* en *WarningVariable.* Zie voor meer informatie het onderwerp 'about_CommonParameters' u openen kunt door de volgende opdracht te typen en vervolgens op ENTER:  

```  
Get-Help about_CommonParameters  
```  

#### <a name="outputs"></a>uitvoer  
 Deze cmdlet levert een **PSObject** object van het type voor elke MDT Provider Windows PowerShell-schijf die wordt hersteld.  

#### <a name="example-1"></a>Voorbeeld 1  

```  
Get-MDTPersistentDrive  
```  

##### <a name="description"></a>Beschrijving  
 In dit voorbeeld worden teruggezet in de lijst met MDT persistent stations, door het maken van een Windows PowerShell-station met de **MDTProvider** type. De implementatieshare wordt niet bijgewerkt wanneer hersteld.  

#### <a name="example-2"></a>Voorbeeld 2  

```  
Get-MDTPersistentDrive -Force  
```  

##### <a name="description"></a>Beschrijving  
 In dit voorbeeld worden teruggezet in de lijst met MDT persistent stations, door het maken van een Windows PowerShell-station met de **MDTProvider** type. De implementatieshare wordt bijgewerkt wanneer hersteld (indien nodig).  

###  <a name="Set-MDTMonitorData"></a>Set-MDTMonitorData  
 Deze sectie beschrijft de **Get-MDTPersistentDrive** Windows PowerShell-cmdlet. Deze cmdlet uitvoeren vanuit een Windows PowerShell-console met de MDT-PowerShell-module geladen. Zie voor meer informatie over het starten van een Windows PowerShell-console met de MDT-PowerShell-module die geladen ' bij het laden van de MDT Windows PowerShell-module '.  

#### <a name="syntax"></a>Syntaxis  

```  
Set-MDTMonitorData [-Path <String>] [-ComputerObject <PSObject>] [-Settings <Hashtable>] [<CommonParameters>]  
```  

 – of –  

```  
Set-MDTMonitorData [-Path <String>] [-MacAddress <String>] [Settings <Hashtable>] [<CommonParameters>]  
```  

#### <a name="description"></a>Beschrijving  
 Deze cmdlet maakt u een nieuwe controle gegevensitem of updates van een bestaand bewaking gegevensitem, in een implementatieshare. U kunt de bewakingsgegevens verwijderen door op te geven identificeren de:  

-   Het computerobject voor de bewaking-item in de implementatieshare. Het computerobject kan worden verkregen met behulp van de **Get-MDTMonitorData** cmdlet. Het eerste syntaxisvoorbeeld illustreert dit gebruik.  

-   MAC-adres van de primaire-netwerkadapter van de controle-item voor een specifieke implementatie-share. Wanneer het item is gemaakt voor de implementatieshare, wordt het MAC-adres automatisch toegewezen aan de bewaking gegevensitem. Het laatste syntaxisvoorbeeld illustreert dit gebruik.  

> [!NOTE]
>  Wanneer de bewakingsgegevens is verwijderd, is er geen methode voor het herstellen van de gegevens.  

#### <a name="parameters"></a>Parameters  
 Deze subsectie bevat informatie over de verschillende parameters beschreven die kunnen worden gebruikt met de **Get - MDTMonitorData** cmdlet.  

##### <a name="-path-string"></a>-Path < String\>  
 Deze parameter bepaalt het MDTProvider Windows PowerShell-station voor de gewenste implementatieshare.  

> [!NOTE]
>  Als deze parameter niet is opgegeven, moet de Windows PowerShell-werkmap standaard naar een locatie binnen de gewenste MDTProvider Windows PowerShell-station.  

|**Parameter**|**Waarde**|  
|-|-|  
|**Vereist?**|**De waarde False**|  
|**Positie?**|**Met de naam**|  
|**Standaardwaarde**|:|  
|**Pijpleidinginvoer accepteren?**|**De waarde False**|  
|**Jokertekens accepteren?**|**De waarde False**|  

##### <a name="-computerobject-psobject"></a>-ComputerObject < PSObject\>  
 Deze parameter bepaalt de controle gegevensitem om te worden gemaakt of bijgewerkt met behulp van een computerobject. Als deze parameter niet is opgegeven, wordt de *MACAddress* parameter moet worden opgegeven voor het identificeren van een bepaalde controle gegevensitem.  

|**Parameter**|**Waarde**|  
|-|-|  
|**Vereist?**|**De waarde False**|  
|**Positie?**|**Met de naam**|  
|**Standaardwaarde**|:|  
|**Pijpleidinginvoer accepteren?**|**De waarde True** (**ByValue**)|  
|**Jokertekens accepteren?**|**De waarde False**|  

##### <a name="-macaddress-string"></a>-MACAddress < tekenreeks\>  
 Deze parameter bepaalt de controle gegevensitem om te worden gemaakt of bijgewerkt met het MAC-adres van de primaire-netwerkadapter van de computer die wordt bewaakt. De indeling van de MAC-adres is *xx:xx:xx:xx:xx:xx,* waar *x* is een hexadecimaal teken opgegeven in hoofdletters (indien vereist). Als deze parameter niet is opgegeven, wordt de *ComputerObject* parameter moet worden opgegeven voor het identificeren van een bepaalde controle gegevensitem.  

|**Parameter**|**Waarde**|  
|-|-|  
|**Vereist?**|**De waarde False**|  
|**Positie?**|**Met de naam**|  
|**Standaardwaarde**|:|  
|**Pijpleidinginvoer accepteren?**|**De waarde True** (**ByValue**)|  
|**Jokertekens accepteren?**|**De waarde False**|  

##### <a name="-settings-hashtable"></a>-Instellingen < hashtabel\>  
 Deze parameter bepaalt de gegevens bewakingsinstellingen voor de bewaking gegevensitem om te worden gemaakt of bijgewerkt. De indeling van de hash-tabel met deze parameter wordt opgegeven is `@{"Setting"="Value"; "Setting1"="Value1"; "Setting2"="Value2}`. Als deze parameter niet is opgegeven, wordt de bewaking gegevensitem gemaakt, maar er is geen controle-informatie wordt opgeslagen.  

 `"Setting"`worden kan elke eigenschap weergegeven in het bestand ZTIGather.xml. `Value`is een geldige waarde voor de opgegeven eigenschap in `"Setting"`.  

|**Parameter**|**Waarde**|  
|-|-|  
|**Vereist?**|**De waarde False**|  
|**Positie?**|**Met de naam**|  
|**Standaardwaarde**|:|  
|**Pijpleidinginvoer accepteren?**|**De waarde True** (**ByValue**)|  
|**Jokertekens accepteren?**|**De waarde False**|  

##### <a name="commonparameters"></a>< CommonParameters\>  
 Deze cmdlet ondersteunt de volgende algemene parameters: *Uitgebreid, foutopsporing, ErrorAction,-ErrorVariable, -OutBuffer, OutVariable, WarningAction* en *WarningVariable.* Zie voor meer informatie het onderwerp 'about_CommonParameters' u openen kunt door de volgende opdracht te typen en vervolgens op ENTER:  

```  
Get-Help about_CommonParameters  
```  

#### <a name="outputs"></a>uitvoer  
 Deze cmdlet wordt geen uitvoer gegenereerd.  

#### <a name="example-1"></a>Voorbeeld 1  

```  
$MonitorObject=Get-MDTMonitorData | Where-Object {$_.Name eq 'WDG-REF-01'}  
Set-MDTMonitorData -ComputerObject $MonitorObject Setting @{"OSDComputerName"="WDG-MDT-01";"SkipWizard"="YES"}  
```  

##### <a name="description"></a>Beschrijving  
 Dit voorbeeld wordt een controle gegevensitem waar de naam van de computer is verwijderd *WDG-REF-01.* Het object is gevonden met behulp van de **Get-MDTMonitorData** cmdlet en de **Where-Object** cmdlet. Voor meer informatie over de **Where-Object** cmdlet, Zie [met de Cmdlet Where-Object](http://technet.microsoft.com/library/ee177028.aspx). De [OSDComputerName](#OSDComputerName) eigenschap wordt geregistreerd als een waarde van **MDT-01-WDG**, en de [SkipWizard](#SkipWizard) eigenschap wordt geregistreerd als een waarde van **Ja**.  

#### <a name="example-2"></a>Voorbeeld 2  

```  
Set-MDTMonitorData -MACAddress "00:11:22:33:44:55" MonitorObject Setting @{"OSDComputerName"="WDG-MDT-01";"SkipWizard"="YES"}  
```  

##### <a name="description"></a>Beschrijving  
 In dit voorbeeld maken of bijwerken van een controle gegevensitem met een **MACAddress** die een waarde heeft van **00:11:22:33:44:55**. De [OSDComputerName](#OSDComputerName) eigenschap wordt geregistreerd als een waarde van **MDT-01-WDG**, en de [SkipWizard](#SkipWizard) eigenschap wordt geregistreerd als een waarde van **Ja**.  

###  <a name="Test-MDTDeploymentShare"></a>Test MDTDeploymentShare  
 Hoewel deze cmdlet wordt geretourneerd met behulp van de **Get-Command** cmdlet dat in de Microsoft.BDD.PSSnapIn, deze niet is geïmplementeerd.  

###  <a name="Test-MDTMonitorData"></a>Test MDTMonitorData  
 Deze sectie beschrijft de **Test MDTMonitorData** Windows PowerShell-cmdlet. Deze cmdlet uitvoeren vanuit een Windows PowerShell-console met de MDT-PowerShell-module geladen. Zie voor meer informatie over het starten van een Windows PowerShell-console met de MDT-PowerShell-module die geladen ' bij het laden van de MDT Windows PowerShell-module '.  

#### <a name="syntax"></a>Syntaxis  

```  
Test-MDTMonitorData -ServerName <String> -EventPort <Int32> -DataPort <Int32> [<CommonParameters>]  
```  

#### <a name="description"></a>Beschrijving  
 Deze cmdlet wordt gevalideerd als de MDT-service, die wordt uitgevoerd op de computer waarop de MDT is geïnstalleerd, bewaking correct ingeschakeld en worden uitgevoerd is. De MDT-bewakingsservice verzamelt controlegegevens die kan worden weergegeven:  

-   In het knooppunt bewaking in een share in de Implementatieworkbench-implementatie  

-   Met behulp van de [Get-MDTMonitorData](#Get-MDTMonitorData) cmdlet  

 De MDT monitoring-service kan worden uitgeschakeld met de [uitschakelen MDTMonitorService](#Disable-MDTMonitorService). Kan controlegegevens worden geschreven met de MDT monitoring service via de [Set MDTMonitorData](#Set-MDTMonitorData) cmdlet.  

> [!NOTE]
>  Voor deze cmdlet functie goed er moet ten minste één MDT bewaking gegevensitem in de implementatieshare. Als er geen controlegegevens MDT is vastgelegd, mislukt de implementatieshare de test.  

 Voor meer informatie over de MDT bewaking van de service, Zie de sectie 'Monitoring MDT implementaties' in het document MDT *met behulp van de Microsoft Deployment Toolkit*.  

#### <a name="parameters"></a>Parameters  
 Deze subsectie bevat informatie over de verschillende parameters beschreven die kunnen worden gebruikt met de **Test MDTMonitorData** cmdlet.  

##### <a name="-server-string"></a>-Server < tekenreeks\>  
 Hiermee geeft u de naam van de computer waarop MDT is geïnstalleerd en de MDT monitoring-service wordt uitgevoerd.  

|**Parameter**|**Waarde**|  
|-|-|  
|**Vereist?**|**De waarde True**|  
|**Positie?**|**Met de naam**|  
|**Standaardwaarde**|Geen|  
|**Pijpleidinginvoer accepteren?**|**De waarde False**|  
|**Jokertekens accepteren?**|**De waarde False**|  

##### <a name="-dataport-int32"></a>-Gegevenspoort < Int32\>  
 Deze parameter bepaalt de TCP-poort die wordt gebruikt als de poort voor de MDT-service te controleren.  

|**Parameter**|**Waarde**|  
|-|-|  
|**Vereist?**|**De waarde True**|  
|**Positie?**|**Met de naam**|  
|**Standaardwaarde**|:|  
|**Pijpleidinginvoer accepteren?**|**De waarde False**|  
|**Jokertekens accepteren?**|**De waarde False**|  

##### <a name="-eventport-int32"></a>-EventPort < Int32\>  
 Deze parameter bepaalt de TCP-poort die wordt gebruikt als de gebeurtenis-poort voor de MDT-service te controleren.  

|**Parameter**|**Waarde**|  
|-|-|  
|**Vereist?**|**De waarde True**|  
|**Positie?**|**Met de naam**|  
|**Standaardwaarde**|:|  
|**Pijpleidinginvoer accepteren?**|**De waarde False**|  
|**Jokertekens accepteren?**|**De waarde False**|  

##### <a name="commonparameters"></a>< CommonParameters\>  
 Deze cmdlet ondersteunt de volgende algemene parameters: *Uitgebreid, foutopsporing, ErrorAction,-ErrorVariable, -OutBuffer, OutVariable, WarningAction* en *WarningVariable.* Zie voor meer informatie het onderwerp 'about_CommonParameters' u openen kunt door de volgende opdracht te typen en vervolgens op ENTER:  

```  
Get-Help about_CommonParameters  
```  

#### <a name="outputs"></a>uitvoer  
 Deze cmdlet levert een Booleaanse waarde die staat voor het succes (true) of falen (ONWAAR) van de tekst.  

#### <a name="example-1"></a>Voorbeeld 1  

```  
Test-MDTMonitorData -Server "WDG-MDT-01" -DataPort "9801" EventPort "9800"  
```  

##### <a name="description"></a>Beschrijving  
 In dit voorbeeld controleert u of als de bewaking van de service op de MDT-01-WDG MDT geïnstalleerd en actief is. De cmdlet controleert of met behulp van een gegevenspoort van 9801 en een poort gebeurtenis van 9800.  

###  <a name="Update-MDTDatabaseSchema"></a>Update MDTDatabaseSchema  
 Deze sectie beschrijft de **Update MDTDatabaseSchema** Windows PowerShell-cmdlet. Deze cmdlet uitvoeren vanuit een Windows PowerShell-console met de MDT-PowerShell-module geladen. Zie voor meer informatie over het starten van een Windows PowerShell-console met de MDT-PowerShell-module die geladen ' bij het laden van de MDT Windows PowerShell-module '.  

#### <a name="syntax"></a>Syntaxis  

```  
Update-MDTDatabaseSchema -SQLServer <String> [-Instance <String>] [-Port <String>] [-Netlib <String>] -Database <String> [-SQLShare <String>] [<CommonParameters>]  
```  

#### <a name="description"></a>Beschrijving  
 Deze cmdlet een bestaande database van de MDT-DB-updates naar de nieuwste versie van het schema van de MDT-DB-database. Elke implementatieshare kan worden gekoppeld aan slechts één MDT DB-database.  

 Deze cmdlet automatisch wordt aangeroepen wanneer een implementatieshare wordt bijgewerkt, bijvoorbeeld wanneer met de [terugzetten MDTPersistentDrive](#Restore-MDTPersistentDrive) cmdlet uit met de *Force* parameter en de [ Update MDTDeploymentShare](#Update-MDTDeploymentShare) cmdlet.  

#### <a name="parameters"></a>Parameters  
 Deze subsectie bevat informatie over de verschillende parameters beschreven die kunnen worden gebruikt met de **Upgrade MDTDatabaseSchema** cmdlet.  

##### <a name="-sqlserver-string"></a>SQL Server - < tekenreeks\>  
 Deze parameter bepaalt de naam van de computer met SQL Server waar de MDT-DB-database wordt bijgewerkt.  

|**Parameter**|**Waarde**|  
|-|-|  
|**Vereist?**|**De waarde True**|  
|**Positie?**|**Met de naam**|  
|**Standaardwaarde**|:|  
|**Pijpleidinginvoer accepteren?**|**De waarde False**|  
|**Jokertekens accepteren?**|**De waarde False**|  

##### <a name="-instance-string"></a>-Exemplaar < tekenreeks\>  
 Deze parameter bepaalt de SQL Server-exemplaar waarop de MDT-DB-database moet worden bijgewerkt bestaat. Als deze parameter wordt weggelaten, klikt u vervolgens de MDT-DB-database wordt ervan uitgegaan dat het standaardexemplaar van SQL Server.  

> [!NOTE]
>  De SQL Browser-service moet worden uitgevoerd op de computer met SQL Server voor de cmdlet om te bepalen de instantie die is opgegeven in deze parameter.  

|**Parameter**|**Waarde**|  
|-|-|  
|**Vereist?**|**De waarde False**|  
|**Positie?**|**Met de naam**|  
|**Standaardwaarde**|:|  
|**Pijpleidinginvoer accepteren?**|**De waarde False**|  
|**Jokertekens accepteren?**|**De waarde False**|  

##### <a name="-port-string"></a>-Poort < tekenreeks\>  
 Deze parameter bepaalt de TCP-poort moet worden gebruikt in de communicatie met de SQL Server-exemplaar dat is opgegeven in de *SQLServer* parameter. De standaardpoort die gebruikmaakt van SQL Server is 1433. Deze parameter opgeven wanneer SQL Server is geconfigureerd voor gebruik van een andere poort dan de standaardwaarde. De waarde van deze parameter moet overeenkomen met de poort die is geconfigureerd voor SQL Server.  

|**Parameter**|**Waarde**|  
|-|-|  
|**Vereist?**|**De waarde False**|  
|**Positie?**|**Met de naam**|  
|**Standaardwaarde**|:|  
|**Pijpleidinginvoer accepteren?**|**De waarde False**|  
|**Jokertekens accepteren?**|**De waarde False**|  

##### <a name="-netlib-string"></a>-Netlib < tekenreeks\>  
 Deze parameter bepaalt de SQL-netwerkbibliotheek die wordt gebruikt in de communicatie met de SQL Server-exemplaar dat is opgegeven in de *SQLServer* parameter. De parameter kan worden ingesteld op een van de volgende waarden:  

-   **DBNMPNTW**, dat wordt gebruikt voor het opgeven van named pipes-communicatie  

-   **DBSMSOCN**, dat wordt gebruikt voor het opgeven van TCP/IP-sockets communicatie  

 Als deze parameter niet is opgegeven, de named pipes SQL netwerkbibliotheek (**DBNMPNTW**) wordt gebruikt.  

> [!NOTE]
>  De implementatie-Workbench biedt niet de optie voor het configureren van de netwerkbibliotheek SQL. De implementatie-Workbench gebruik altijd van named pipes-communicatie. De SQL-netwerkbibliotheek kan echter worden geconfigureerd in het CustomSettings.ini-bestand.  

|**Parameter**|**Waarde**|  
|-|-|  
|**Vereist?**|**De waarde False**|  
|**Positie?**|**Met de naam**|  
|**Standaardwaarde**|:|  
|**Pijpleidinginvoer accepteren?**|**De waarde False**|  
|**Jokertekens accepteren?**|**De waarde False**|  

##### <a name="-database-string"></a>-Database < tekenreeks\>  
 Deze parameter geeft de naam van de database moet worden bijgewerkt in de SQL Server-exemplaar dat is opgegeven in de *exemplaar* parameter bij de SQL Server-exemplaar dat is opgegeven in de *SQLServer* parameter.  

|**Parameter**|**Waarde**|  
|-|-|  
|**Vereist?**|**De waarde True**|  
|**Positie?**|**Met de naam**|  
|**Standaardwaarde**|:|  
|**Pijpleidinginvoer accepteren?**|**De waarde False**|  
|**Jokertekens accepteren?**|**De waarde False**|  

##### <a name="commonparameters"></a>< CommonParameters\>  
 Deze cmdlet ondersteunt de volgende algemene parameters: *Uitgebreid, foutopsporing, ErrorAction,-ErrorVariable, -OutBuffer, OutVariable, WarningAction* en *WarningVariable.* Zie voor meer informatie het onderwerp 'about_CommonParameters' u openen kunt door de volgende opdracht te typen en vervolgens op ENTER:  

```  
Get-Help about_CommonParameters  
```  

#### <a name="outputs"></a>uitvoer  
 Deze cmdlet levert een **PSObject** object van het type voor de MDT-database die is bijgewerkt. Deze cmdlet levert ook een **tekenreeks** Typ gegevens als de *uitgebreid* algemene parameter is opgenomen.  

#### <a name="example-1"></a>Voorbeeld 1  

```  
Update-MDTDatabaseSchema –SQLServer "WDGSQL01" Database "MDTDB"   
```  

##### <a name="description"></a>Beschrijving  
 In dit voorbeeld het schema voor een MDT-database met de naam bijgewerkt *MDTDB* in de standaardinstantie van SQL Server op een computer met de naam *WDG-SQL-01.* De verbinding wordt met het SQL Server-exemplaar met behulp van de standaard TCP-poort en het protocol Named Pipes worden gemaakt.  

#### <a name="example-2"></a>Voorbeeld 2  

```  
Update-MDTDatabaseSchema –SQLServer "WDGSQL01" –Instance "MDTInstance" -Port "6333" Database "MDTDB"  
```  

##### <a name="description"></a>Beschrijving  
 In dit voorbeeld het schema voor een MDT-database met de naam bijgewerkt *MDTDB* in SQL Server-exemplaar met de naam *MDTInstance* op een computer met de naam *WDG-SQL-01.* De verbinding wordt met de SQL-Server via TCP-poort 6333 en het protocol Named Pipes worden gemaakt.  

###  <a name="Update-MDTDeploymentShare"></a>Update MDTDeploymentShare  
 Deze sectie beschrijft de **Update MDTDeploymentShare** Windows PowerShell-cmdlet. Deze cmdlet uitvoeren vanuit een Windows PowerShell-console met de MDT-PowerShell-module geladen. Zie voor meer informatie over het starten van een Windows PowerShell-console met de MDT-PowerShell-module die geladen ' bij het laden van de MDT Windows PowerShell-module '.  

#### <a name="syntax"></a>Syntaxis  

```  
Update-MDTDeploymentShare [-Path <String>] [-Force] [Compress] [<CommonParameters>]  
```  

#### <a name="description"></a>Beschrijving  
 Deze cmdlet werkt een bestaande implementatieshare met de laatste bestanden van de Windows ADK. Deze cmdlet is ook bijgewerkt of worden opnieuw gegenereerd door de vereiste Windows PE-opstartinstallatiekopieën in het WIM- en ISO-bestandsindelingen.  

#### <a name="parameters"></a>Parameters  
 Deze subsectie bevat informatie over de verschillende parameters beschreven die kunnen worden gebruikt met de **Update MDTDeploymentShare** cmdlet.  

##### <a name="-path-string"></a>-Path < String\>  
 Deze parameter bepaalt het volledig gekwalificeerde pad naar een bestaande map in de implementatieshare die wordt bijgewerkt.  

> [!NOTE]
>  Als deze parameter niet is opgegeven, moet de Windows PowerShell-werkmap standaard naar de gewenste locatie binnen de implementatieshare.  

|**Parameter**|**Waarde**|  
|-|-|  
|**Vereist?**|**De waarde False**|  
|**Positie?**|**Met de naam**|  
|**Standaardwaarde**|:|  
|**Pijpleidinginvoer accepteren?**|**De waarde False**|  
|**Jokertekens accepteren?**|**De waarde False**|  

##### <a name="-force-switchparameter"></a>-Force [< SwitchParameter\>]  
 Deze parameter bepaalt of Windows PE-installatiekopieën (ISO en WIM-bestanden) voor de implementatieshare volledig opnieuw moeten worden gegenereerd. Als deze parameter is:  

-   Opgegeven, worden de cmdlet maakt een nieuwe versies van de Windows PE-opstartinstallatiekopieën. Dit proces duurt langer dan de bestaande Windows PE-opstartinstallatiekopieën te optimaliseren.  

-   Dit wordt weggelaten, klikt u vervolgens optimaliseert de cmdlet de bestaande Windows PE-opstartinstallatiekopieën. Dit proces duurt minder tijd dan het genereren van nieuwe versies van de Windows PE-opstartinstallatiekopieën. Als deze parameter wordt weggelaten, de *comprimeren* parameter kan worden gebruikt voor de grootte van de opstartinstallatiekopieën als onderdeel van de Windows PE-installatiekopie optimalisatie opstartprocedure te reduceren.  

|**Parameter**|**Waarde**|  
|-|-|  
|**Vereist?**|**De waarde False**|  
|**Positie?**|**Met de naam**|  
|**Standaardwaarde**|:|  
|**Pijpleidinginvoer accepteren?**|**De waarde True** (**ByValue**)|  
|**Jokertekens accepteren?**|**De waarde False**|  

##### <a name="-compress-switchparameter"></a>-Comprimeren [< SwitchParameter\>]  
 Deze parameter wordt aangegeven of de Windows PE-installatiekopieën (ISO en WIM-bestanden) voor de share van de implementatie moeten worden gecomprimeerd wanneer ze zijn geoptimaliseerd (zonder de *Force* parameter). Als deze parameter is:  

-   Opgegeven, worden de cmdlet worden de Windows PE-opstartinstallatiekopieën gecomprimeerd als ze zijn wordt geoptimaliseerd  

-   Dit wordt weggelaten, vervolgens de cmdlet niet wordt gecomprimeerd de Windows PE-opstartinstallatiekopieën zoals ze zijn wordt geoptimaliseerd  

> [!NOTE]
>  Deze parameter alleen moet worden opgegeven als de *Force* parameter is niet opgegeven. Als de *Force* parameter is opgenomen, nieuwe Windows PE-opstartinstallatiekopieën worden gegenereerd en naar de minimale grootte worden gecomprimeerd.  

|**Parameter**|**Waarde**|  
|-|-|  
|**Vereist?**|**De waarde False**|  
|**Positie?**|**Met de naam**|  
|**Standaardwaarde**|:|  
|**Pijpleidinginvoer accepteren?**|**De waarde True** (**ByValue**)|  
|**Jokertekens accepteren?**|**De waarde False**|  

##### <a name="commonparameters"></a>< CommonParameters\>  
 Deze cmdlet ondersteunt de volgende algemene parameters: *Uitgebreid, foutopsporing, ErrorAction,-ErrorVariable, -OutBuffer, OutVariable, WarningAction* en *WarningVariable.* Zie voor meer informatie het onderwerp 'about_CommonParameters' u openen kunt door de volgende opdracht te typen en vervolgens op ENTER:  

```  
Get-Help about_CommonParameters  
```  

#### <a name="outputs"></a>uitvoer  
 Deze cmdlet levert een **tekenreeks** type gegevens en treedt er extra **tekenreeks** Typ gegevens als de *uitgebreid* algemene parameter is opgenomen.  

#### <a name="example-1"></a>Voorbeeld 1  

```  
Update-MDTDepoymentShare   
```  

##### <a name="description"></a>Beschrijving  
 In dit voorbeeld werkt de implementatieshare bij de Windows PowerShell-werkmap. De Windows PE-opstartinstallatiekopieën wordt geoptimaliseerd. De Windows PE-opstartinstallatiekopieën worden niet gecomprimeerd.  

#### <a name="example-2"></a>Voorbeeld 2  

```  
Update-MDTDepoymentShare -Path "DS001:"  
```  

##### <a name="description"></a>Beschrijving  
 Dit voorbeeld worden de share op de MDT Windows PowerShell-station met de naam van de implementatie bijgewerkt *DS001:.* De Windows PE-opstartinstallatiekopieën wordt geoptimaliseerd. De Windows PE-opstartinstallatiekopieën worden niet gecomprimeerd.  

#### <a name="example-3"></a>Voorbeeld 3  

```  
Update-MDTDepoymentShare -Path "DS001:" -Compress  
```  

##### <a name="description"></a>Beschrijving  
 Dit voorbeeld worden de share op de MDT Windows PowerShell-station met de naam van de implementatie bijgewerkt *DS001:.* De Windows PE-opstartinstallatiekopieën wordt geoptimaliseerd. De Windows PE-opstartinstallatiekopieën worden gecomprimeerd.  

#### <a name="example-4"></a>Voorbeeld 4  

```  
Update-MDTDepoymentShare -Path "DS001:" -Force  
```  

##### <a name="description"></a>Beschrijving  
 Dit voorbeeld worden de share op de MDT Windows PowerShell-station met de naam van de implementatie bijgewerkt *DS001:.* Nieuwe versies van de Windows PE-opstartinstallatiekopieën wordt gegenereerd.  

###  <a name="Update-MDTLinkedDS"></a>Update MDTLinkedDS  
 Deze sectie beschrijft de **Update MDTLinkedDS** Windows PowerShell-cmdlet. Deze cmdlet uitvoeren vanuit een Windows PowerShell-console met de MDT-PowerShell-module geladen. Zie voor meer informatie over het starten van een Windows PowerShell-console met de MDT-PowerShell-module die geladen ' bij het laden van de MDT Windows PowerShell-module '.  

#### <a name="syntax"></a>Syntaxis  

```  
Update-MDTLinkedDS -Path <String> [<CommonParameters>]  
```  

#### <a name="description"></a>Beschrijving  
 Deze cmdlet wordt inhoud van een implementatieshare gerepliceerd naar een share van de gekoppelde implementatie met de selectie-profiel gebruikt voor het definiëren van de gekoppelde implementatieshare. De werking van replicatie wordt bepaald op basis van de configuratie-instellingen voor de gekoppelde implementatieshare.  

#### <a name="parameters"></a>Parameters  
 Deze subsectie bevat informatie over de verschillende parameters beschreven die kunnen worden gebruikt met de **Update MDTLinkedDS** cmdlet.  

##### <a name="-path-string"></a>-Path < String\>  
 Deze parameter bepaalt de volledig gekwalificeerde pad naar de share van de gekoppelde implementatie die wordt bijgewerkt.  

> [!NOTE]
>  Als deze parameter niet is opgegeven, moet de Windows PowerShell-werkmap standaard naar de gewenste locatie binnen de implementatieshare.  

|**Parameter**|**Waarde**|  
|-|-|  
|**Vereist?**|**De waarde True**|  
|**Positie?**|**Met de naam**|  
|**Standaardwaarde**|:|  
|**Pijpleidinginvoer accepteren?**|**De waarde False**|  
|**Jokertekens accepteren?**|**De waarde False**|  

##### <a name="commonparameters"></a>< CommonParameters\>  
 Deze cmdlet ondersteunt de volgende algemene parameters: *Uitgebreid, foutopsporing, ErrorAction,-ErrorVariable, -OutBuffer, OutVariable, WarningAction* en *WarningVariable.* Zie voor meer informatie het onderwerp 'about_CommonParameters' u openen kunt door de volgende opdracht te typen en vervolgens op ENTER:  

```  
Get-Help about_CommonParameters  
```  

#### <a name="outputs"></a>uitvoer  
 Deze cmdlet levert een **tekenreeks** type gegevens en treedt er extra **tekenreeks** Typ gegevens als de *uitgebreid* algemene parameter is opgenomen.  

#### <a name="example-1"></a>Voorbeeld 1  

```  
Update-MDTLinkedDS -Path "DS001:\Linked Deployment Shares\LINKED001"  
```  

##### <a name="description"></a>Beschrijving  
 In dit voorbeeld wordt inhoud van de implementatieshare gerepliceerd naar de share van de gekoppelde implementatie op de map Windows PowerShell pad DS001:\Linked implementatie Shares\LINKED001.  

###  <a name="Update-MDTMedia"></a>Update MDTMedia  
 Deze sectie beschrijft de **Update MDTMedia** Windows PowerShell-cmdlet. Deze cmdlet uitvoeren vanuit een Windows PowerShell-console met de MDT-PowerShell-module geladen. Zie voor meer informatie over het starten van een Windows PowerShell-console met de MDT-PowerShell-module die geladen ' bij het laden van de MDT Windows PowerShell-module '.  

#### <a name="syntax"></a>Syntaxis  

```  
Update-MDTMedia -Path <String> [<CommonParameters>]  
```  

#### <a name="description"></a>Beschrijving  
 Deze cmdlet wordt inhoud van een implementatieshare gerepliceerd naar een map met media voor implementatie met de selectie-profiel gebruikt voor het definiëren van de media voor implementatie. De werking van replicatie wordt bepaald op basis van de configuratie-instellingen voor de implementatiemedia.  

 Media in LTI kunt u implementaties van LTI uitsluitend vanaf lokale media uitvoeren zonder verbinding met een implementatieshare. U kunt het medium opslaan op een DVD, USB harde schijf of ander draagbaar apparaat. Nadat u de media maakt, genereren opstartbare WIM-installatiekopieën, waardoor de implementatie worden uitgevoerd vanuit een draagbaar medium zijn apparaten lokaal beschikbaar op de doelcomputer.  

#### <a name="parameters"></a>Parameters  
 Deze subsectie bevat informatie over de verschillende parameters beschreven die kunnen worden gebruikt met de **Update MDTMedia** cmdlet.  

##### <a name="-path-string"></a>-Path < String\>  
 Deze parameter bepaalt de volledig gekwalificeerde pad naar de map waarin de implementatiemedia die wordt bijgewerkt.  

> [!NOTE]
>  Als deze parameter niet is opgegeven, moet de Windows PowerShell-werkmap standaard naar de gewenste locatie binnen de implementatieshare.  

|**Parameter**|**Waarde**|  
|-|-|  
|**Vereist?**|**De waarde True**|  
|**Positie?**|**Met de naam**|  
|**Standaardwaarde**|:|  
|**Pijpleidinginvoer accepteren?**|**De waarde False**|  
|**Jokertekens accepteren?**|**De waarde False**|  

##### <a name="commonparameters"></a>< CommonParameters\>  
 Deze cmdlet ondersteunt de volgende algemene parameters: *Uitgebreid, foutopsporing, ErrorAction,-ErrorVariable, -OutBuffer, OutVariable, WarningAction* en *WarningVariable.* Zie voor meer informatie het onderwerp 'about_CommonParameters' u openen kunt door de volgende opdracht te typen en vervolgens op ENTER:  

```  
Get-Help about_CommonParameters  
```  

#### <a name="outputs"></a>uitvoer  
 Deze cmdlet levert een **tekenreeks** type gegevens en treedt er extra **tekenreeks** Typ gegevens als de *uitgebreid* algemene parameter is opgenomen.  

#### <a name="example-1"></a>Voorbeeld 1  

```  
Update-MDTMedia -Path "DS001:\Media\MEDIA001"  
```  

##### <a name="description"></a>Beschrijving  
 In dit voorbeeld wordt inhoud van de implementatieshare gerepliceerd naar de map met de media voor implementatie op de map Windows PowerShell pad DS001:\Media \MEDIA001.  

## <a name="tables-and-views-in-the-mdt-db"></a>Tabellen en weergaven in de MDT-DB  
 In MDT, veel instellingen van eigenschappen kunnen worden opgeslagen (meestal geconfigureerd in het CustomSettings.ini-bestand) in een database. De eigenschappen te configureren in een database kunt maken van een algemene CustomSettings.ini-bestand dat vereist minder wijzigingen en één CustomSettings.ini-bestand kan worden gebruikt in meer installatiekopieën (omdat het bestand algemene wordt).  

 De database in de Database-knooppunt in de implementatie-Workbench aanpassen. Met behulp van de implementatie-Workbench, kunnen de implementatie-instellingen worden geconfigureerd en opgeslagen in de tabellen.  

 Echter, query's over de informatie in de tabellen klaar bent met het gebruik van weergaven. Weergaven vereenvoudigen de query's door de resultaten uit meerdere tabellen samenvoegen. ZTIGather.wsf vraagt de weergaven die het resultaat ingesteld die de **Parameters** en **ParameterCondition** eigenschappen opgeven.  

### <a name="tables-in-the-mdt-db"></a>Tabellen in de MDT-DB  
 De volgende tabel bevat de databasetabellen die implementatie-Workbench maakt en beheert.  

|**Tabel**|**Beschrijving**|  
|-|-|  
|ComputerIdentity|Gebruikt voor het identificeren van een specifieke computer die een combinatie van de **AssetTag, UUID, serienummer**, en **MACAddress** eigenschappen. De tabel bevat een **beschrijving** kolom bieden een gebruiksvriendelijke methode met een beschrijving van de computer (meestal de naam van de computer).|  
|Beschrijvingen|Bevat beschrijvingen van alle eigenschappen die kunnen worden geconfigureerd via de database.|  
|LocationIdentity|Gebruikt voor het identificeren van geografische locaties met behulp van de **locatie** eigenschap. De waarden voor deze eigenschap worden opgeslagen in een overeenkomende kolom in de tabel.|  
|LocationIdentity_DefaultGateway|De standaardwaarden van de gateway verbindt met een locatie in de tabel LocationIdentity geïdentificeerd. Er is een een-op-veel-relatie tussen deze tabel en de tabel LocationIdentity.|  
|MakeModelIdentity|Gebruikt voor het identificeren van een specifiek merk en model van een computer met de **zorg** en **Model** eigenschappen. De waarden voor deze eigenschappen worden opgeslagen in de overeenkomstige kolommen in de tabel.|  
|PackageMapping|Gebruikt voor het koppelen van de naam die zijn gepresenteerd in het onderdeel Software in het Configuratiescherm verwijderen met een Configuration Manager-pakket en programma worden geïmplementeerd in plaats van de toepassing in software of software. Zie de sectie 'Implementeren van toepassingen gebaseerd op eerdere toepassingsversies', in de MDT-document voor meer informatie over deze tabel *Microsoft Deployment Toolkit voorbeelden Guide.*|  
|RoleIdentity|Gebruikt voor het identificeren van het doel van een computer of gebruikers van een computer met de **rol** eigenschap. De waarden voor deze eigenschap worden opgeslagen in een overeenkomende kolom in de tabel.|  
|Instellingen|De instellingen die worden toegepast op een afzonderlijke computer of een groep computers op basis van de instellingen in de locaties van Computers, rollen, en zorg identificeert en Model van de knooppunten in het knooppunt van de Database in de implementatie-Workbench.|  
|Settings_Administrators|Bevat de gebruikersaccounts worden toegevoegd aan de lokale beheerdersgroep op de doelcomputer op basis van de instellingen in de Computers, rollen, locaties en merk en Model van de knooppunten in het knooppunt van de Database in de implementatie-Workbench.|  
|Settings_Applications|Identificeert de toepassingen op de doelcomputer op basis van de instellingen in de Computers, rollen, locaties, kunnen worden geïmplementeerd en merk en Model van de knooppunten in het knooppunt van de Database in de implementatie-Workbench.|  
|Settings_Packages|De pakketten worden geïmplementeerd op de doelcomputer op basis van de instellingen in de Computers, rollen, locaties, identificeert en merk en Model van de knooppunten in het knooppunt van de Database in de implementatie-Workbench.|  
|Settings_Roles|Identificeert de functies om te worden gekoppeld aan de doelcomputer op basis van de instellingen op de Computers, locaties en merk en Model van de knooppunten in het knooppunt van de Database in de implementatie-Workbench.|  

### <a name="views-in-the-mdt-db"></a>Weergaven in de MDT-DB  
 De volgende tabel geeft een lijst van en beschrijft de databaseweergaven die worden gebruikt bij het opvragen van configuratiegegevens in de MDT-database.  

|**Weergave**|**Beschrijving**|  
|-|-|
|ComputerAdministrators|Gebruikt om alle accounts die leden van de lokale groep Administrators op de doelcomputer. De weergave is een join is van de tabellen ComputerIdentity en Settings_Administrators.|  
|ComputerApplications|Gebruikt om alle toepassingen op de doelcomputer kunnen worden geïmplementeerd. De weergave is een join is van de tabellen ComputerIdentity en Settings_Applications.|  
|ComputerPackages|Gebruikt om alle pakketten worden geïmplementeerd op de doelcomputer. De weergave is een join is van de tabellen ComputerIdentity en Settings_Packages.|  
|ComputerRoles|Gebruikt om alle rollen aan de doelcomputer worden gekoppeld. De weergave is een join is van de tabellen ComputerIdentity en Settings_Roles.|  
|ComputerSettings|Gebruikt om alle instellingen voor de doelcomputer moet worden geconfigureerd. De weergave is een join is van de tabellen ComputerIdentity en instellingen.|  
|LocationAdministrators|Gebruikt om de accounts die lid zijn van de lokale groep Administrators op de doelcomputers binnen een locatie. De weergave is een join is van de tabellen LocationIdentity, LocationIdentity_DefaultGateway en Settings_Administrators.|  
|LocationApplications|Gebruikt om de toepassingen op de doelcomputers binnen een locatie kunnen worden geïmplementeerd. De weergave is een join is van de tabellen LocationIdentity, LocationIdentity_DefaultGateway en Settings_Applications.|  
|LocationPackages|Gebruikt om de pakketten op de doelcomputers binnen een locatie kunnen worden geïmplementeerd. De weergave is een join is van de tabellen LocationIdentity, LocationIdentity_DefaultGateway en Settings_Packages.|  
|LocationRoles|Gebruikt om de rollen worden gekoppeld aan de doelcomputers binnen een locatie. De weergave is een join is van de tabellen LocationIdentity, LocationIdentity_DefaultGateway en Settings_Roles.|  
|Locaties|Gebruikt de IP-adressen vinden voor de standaardgateways binnen een locatie of voor alle locaties met een opgegeven IP-adres voor een standaardgateway. De weergave is een join is van de tabellen LocationIdentity en LocationIdentity_DefaultGateway.|  
|LocationSettings|Gebruikt om de eigenschapsinstellingen voor de doelcomputers binnen een locatie moet worden geconfigureerd. De weergave is een koppeling van de tabellen LocationIdentity, LocationIdentity_DefaultGateway en instellingen.|  
|MakeModelAdministrators|Gebruikt om alle accounts die leden van de lokale groep Administrators op de doelcomputers met een bepaalde merk en model. De weergave is een join is van de tabellen MakeModelIdentity en Settings_Administrators.|  
|MakeModelApplications|Gebruikt om alle toepassingen op de doelcomputers met een bepaalde merk en model kunnen worden geïmplementeerd. De weergave is een join is van de tabellen MakeModelIdentity en Settings_Applications.|  
|MakeModelPackages|Gebruikt om alle pakketten op de doelcomputers met een bepaalde merk en model kunnen worden geïmplementeerd. De weergave is een join is van de tabellen MakeModelIdentity en Settings_Applications.|  
|MakeModelRoles|Gebruikt om alle functies die zijn gekoppeld aan de doel-pc met een bepaalde merk en model. De weergave is een join is van de tabellen MakeModelIdentity en Settings_Roles.|  
|MakeModelSettings|Gebruikt om alle instellingen voor de doelcomputers met een bepaalde merk en model moet worden geconfigureerd. De weergave is een join is van de tabellen MakeModelIdentity en instellingen.|  
|RoleAdministrators|Gebruikt om alle accounts die leden van de lokale groep Administrators op de doelcomputers met een opgegeven rol. De weergave is een join is van de tabellen RoleIdentity en Settings_Administrators.|  
|RoleApplications|Gebruikt om alle toepassingen op de doelcomputers met een bepaalde rol kunnen worden geïmplementeerd. De weergave is een join is van de tabellen RoleIdentity en Settings_Applications.|  
|RolePackages|Gebruikt om alle pakketten op de doelcomputers met een bepaalde rol kunnen worden geïmplementeerd. De weergave is een join is van de tabellen RoleIdentity en Settings_Packages.|  
|RoleSettings|Gebruikt om alle instellingen voor de doelcomputers met een bepaalde rol moet worden geconfigureerd. De weergave is een join is van de tabellen RoleIdentity en instellingen.|  

## <a name="windows-7-feature-dependency-reference"></a>Windows 7 functie Afhankelijkheidsverwijzing  
 Tabel 8 bevat de functies van Windows 7, het bovenliggende onderdeel en alle afhankelijke onderdelen. U kunt deze informatie gebruiken om te bepalen welke functies en functies moeten worden geïnstalleerd ter ondersteuning van een specifieke functie met de [Installeer functies en onderdelen](#InstallRolesandFeatures) en [verwijderen van functies en onderdelen](#UninstallRolesandFeatures) takenreeks stappen.  

### <a name="table-8-windows-7-feature-dependency-reference"></a>Tabel 8. Windows 7 functie Afhankelijkheidsverwijzing  

|**Functie**|**Bovenliggende onderdeel**|**Afhankelijke onderdelen**|  
|-|-|-|  
|Windows Media® Center|Mediafuncties|Kan invloed hebben op andere Windows-onderdelen|  
|Windows DVD Maker|Mediafuncties|Kan invloed hebben op andere Windows-onderdelen|  
|Windows MediaPlayer|Mediafuncties|Kan invloed hebben op andere Windows-onderdelen|  
|Windows Search|n.v.t.|Kan invloed hebben op andere Windows-onderdelen|  
|Internet Explorer (amd64)|n.v.t.|Kan invloed hebben op andere Windows-onderdelen|  
|World Wide Web-services|Microsoft Internet Information Services (IIS)|-Microsoft Message Queuing (MSMQ) HTTP-ondersteuning<br /><br /> -Windows Communication Foundation (WCF) HTTP-activering|  
|Compatibiliteit met IIS 6 WMI|IIS Web beheerhulpprogramma's, compatibiliteit met IIS 6-beheer|IIS 6-scripthulpprogramma tooling|  
|Microsoft .NET-uitbreidbaarheid|IIS, de World Wide Web-services, de onderdelen voor toepassingsontwikkeling|-Microsoft ASP.NET<br /><br /> -MSMQ HTTP-ondersteuning<br /><br /> -WCF HTTP-activering|  
|Standaarddocument|IIS, de World Wide Web-services, veelvoorkomende HTTP-functies|MSMQ HTTP-ondersteuning|  
|Bladeren door mappen|IIS, de World Wide Web-services, veelvoorkomende HTTP-functies|MSMQ HTTP-ondersteuning|  
|HTTP-omleiding|IIS, de World Wide Web-services, veelvoorkomende HTTP-functies|MSMQ HTTP-ondersteuning|  
|Statische inhoud|IIS, de World Wide Web-services, veelvoorkomende HTTP-functies|-Web-based Distributed Authoring and Versioning (WebDAV) publiceren<br /><br /> -MSMQ HTTP-ondersteuning|  
|Aangepaste logboekregistratie|IIS, de World Wide Web-services, status en diagnose|MSMQ HTTP-ondersteuning|  
|HTTP-logboekregistratie|IIS, de World Wide Web-services, status en diagnose|MSMQ HTTP-ondersteuning|  
|ODBC-registratie|IIS, de World Wide Web-services, status en diagnose|MSMQ HTTP-ondersteuning|  
|Controle aanvragen|IIS, de World Wide Web-services, status en diagnose|MSMQ HTTP-ondersteuning|  
|tracering|IIS, de World Wide Web-services, status en diagnose|MSMQ HTTP-ondersteuning|  
|Compressie van statische inhoud|IIS, de World Wide Web-services, prestatiefuncties|MSMQ HTTP-ondersteuning|  
|Beveiliging|IIS, de World Wide Web-services|-Microsoft .NET uitbreidbaarheid<br /><br /> -MSMQ HTTP-ondersteuning<br /><br /> -WCF HTTP-activering|  
|Filtering aanvragen|IIS, de World Wide Web-services, beveiliging|-Microsoft .NET uitbreidbaarheid<br /><br /> -MSMQ HTTP-ondersteuning<br /><br /> -WCF HTTP-activering|  
|XPS-Viewer|n.v.t.|Kan invloed hebben op andere Windows-onderdelen|  

## <a name="udi-reference"></a>UDI verwijzing  
 Deze verwijzing bevat meer informatie over UDI en bevat onderwerpen op:  

-   UDI concepten zoals beschreven in [UDI-concepten](#UDIConcepts)  

-   OSDResults zoals beschreven in [OSDResults verwijzing](#OSDResultsReference)  

-   Gebruiker gericht App-installatieprogramma zoals beschreven in [gebruiker Centric App Installer-referentie](#UserCentricAppInstallerReference)  

-   UDI bereidt zoals beschreven in [UDI fase verwijzing](#UDIStageReference)  

-   UDI taken zoals beschreven in [UDI taak verwijzing](#UDITaskReference)  

-   UDI validatiefuncties zoals beschreven in [UDI Validator verwijzing](#UDIValidatorReference)  

-   UDI wizardpagina's zoals beschreven in [UDI Wizard Page-verwijzing](#UDIWizardPageReference)  

 Elk van deze onderwerpen waarnaar wordt verwezen in de volgende secties worden besproken.  

###  <a name="UDIConcepts"></a>UDI-concepten  
 Deze sectie bevat concepten waarmee wordt beschreven UDI, de Wizard UDI en de waarde van de Wizard UDI.  

####  <a name="DisplayName"></a>Weergavenaam  
 De weergavenaam op die wordt gebruikt voor een gebruiksvriendelijke, beschrijvende naam opgeven voor een pagina van de wizard in de tapewisselaar pagina in de ontwerpfunctie van de Wizard UDI. De weergavenaam wordt weergegeven in de blauwe tekst voor elke pagina van de wizard in de bibliotheek pagina en klik op de **Flow** tabblad in de waarde van de Wizard UDI.  

 Wanneer u een pagina aan de pagina bibliotheek toevoegt, moet u de weergavenaam opgeven. Nadat de wizard pagina toegevoegd aan de bibliotheek pagina u de weergegeven naam niet wijzigen.  

####  <a name="Flow"></a>Stroom  
 De **Flow** tabblad geeft de lijst met wizardpagina's binnen een UDI fase in de waarde van de Wizard UDI. U kunt de **Flow** tabblad aan de volgende taken uitvoeren:  

-   Een pagina van de wizard uit de bibliotheek pagina toevoegen aan een fase UDI door de pagina van de pagina bibliotheek naar de fase UDI te slepen.  

-   Een wizardpagina verwijderen uit een UDI-fase.  

-   Wijzig de volgorde van de wizardpagina's binnen een UDI-fase.  

####  <a name="PageLibrary"></a>Pagina bibliotheek  
 De pagina bibliotheek bevat alle pagina's die momenteel zijn geladen in de ontwerpfunctie van de Wizard UDI. Bij het laden van een configuratiebestand van de Wizard UDI, worden alle van de wizardpagina's gedefinieerd in het configuratiebestand naar de pagina bibliotheek weergegeven. De pagina bibliotheek bevat de wizardpagina's in alfabetische volgorde pagina typen. Elk exemplaar van een specifieke paginatype wordt vermeld onder het paginatype.  

 Bijvoorbeeld, moet u mogelijk twee verschillende **WelcomePage** wizardpagina's voor verschillende fasen. De twee **WelcomePage** wizardpagina's worden vermeld in de **WelcomePage** paginatype wizard in de bibliotheek pagina in de waarde van de Wizard UDI.  

 Bovendien is elk exemplaar van de pagina wizard in de bibliotheek pagina geeft aan hoe vaak de wizardpagina wordt gebruikt in de fase stromen. Wanneer u de muisaanwijzer op een pagina van de wizard in de bibliotheek pagina, wordt een miniatuur van de wizardpagina weergegeven samen met de fasen die die pagina bevatten.  

####  <a name="PageName"></a>Paginanaam  
 Naam van de pagina wordt gebruikt om een pagina van de wizard in de tapewisselaar pagina in de ontwerpfunctie van de Wizard UDI uniek te identificeren. De *paginanaam* is de naam van een fase UDI verwijst naar zodat de Wizard UDI weet welke wizardpagina om weer te geven in een specifieke UDI-fase. Wanneer u een pagina aan de pagina bibliotheek toevoegt, moet u de naam van de pagina opgeven. Nadat de wizard pagina toegevoegd aan de bibliotheek pagina kunt u de paginanaam wijzigen. Naam van de pagina wordt in de ontwerpfunctie van de Wizard UDI weergegeven onder aan elke pagina van de wizard in de bibliotheek pagina in kleinere, niet-vette tekst.  

####  <a name="PrestagedMediaDeployments"></a>Implementaties met voorbereide Media  
 Voorbereide media-ondersteuning is de functie voor een besturingssysteem-implementatie in Configuratiebeheer waarmee een beheerder om te kopiëren en toepassing vooraf opstartbare media en de installatiekopie van een besturingssysteem op een harde schijf voorafgaand aan de inrichting worden verwerkt. Dit werk kan netwerkverkeer verminderen en de tijd die nodig is voor het inrichtingsproces. Voorbereide media kan worden geïmplementeerd als onderdeel van het fabricageproces of aan een zakelijk voorbereidingscentrum dat niet is verbonden met de Configuration Manager-omgeving.  

 Zie de volgende bronnen voor meer informatie over implementaties met voorbereide media:  

-   [Planning voor implementaties van besturingssystemen van Media in Configuration Manager](http://technet.microsoft.com/library/hh499044.aspx)  

-   [Over Voorgefaseerde Media voor implementatie van besturingssysteem](http://technet.microsoft.com/library/gg294171.aspx)  

#### <a name="stage-group"></a>Fase groep  
 Gebruik een fase groep aan een of meer fasen in de waarde van de Wizard UDI. UDI fase groepen los betrekking hebben op MDT implementatiescenario's, maar er is geen-op-een correlatie tussen de twee.  

####  <a name="Stage"></a>Fase  
 Een *fase* is een subset van alle pagina's in het configuratiebestand van de Wizard UDI die gebruikmaakt van een scenario MDT-implementatie. Wanneer u start de Wizard UDI met behulp van de **Wizard UDI** takenreeksstap, de **/fase** parameter geeft u de fase worden uitgevoerd, waarmee op zijn beurt de set pagina's te gebruiken. U kunt een voorbeeld bekijken hoe wizardpagina's worden weergegeven in een fase door te klikken op **Preview** in de **Preview Wizard** groep op het lint. Hoewel de fase UDI is slechts één keer gedefinieerd in de Wizard UDI ontwerpfunctie, kunt u een fase UDI in meer dan één MDT implementatiescenario. De fase NewComputer kan bijvoorbeeld worden gebruikt in de nieuwe Computer MDT en vervang Computer implementatiescenario's.  

####  <a name="Task"></a>Taak  
 *UDI taken* is software die wordt uitgevoerd op een pagina van de wizard uit te voeren van specifieke functies. In sommige gevallen worden deze taken worden gebruikt om te controleren of de doelcomputer gereed is voor implementatie. Andere taken kunnen worden gebruikt om uit te voeren zoals het kopiëren van bestanden met configuration of het resultaat van de implementatiestappen.  

> [!NOTE]
>  De **volgende** knop op de wizardpagina waarin de taken worden uitgevoerd wordt uitgeschakeld als een van de taken met waarschuwing of fout voltooiingsstatus voltooien.  

 UDI bevat verschillende ingebouwde taken waarmee u kunt de meeste van de taken die nodig zijn voor implementatie uitvoeren. Zie voor meer informatie over de ingebouwde taken UDI [ingebouwde UDI taken](#BuiltinUDITasks).  

 De **Shell uitvoeren** ingebouwde UDI taak kunt u software (scripts) die kan worden gestart vanaf een opdrachtregel, zoals Visual Basic of Windows PowerShell-scripts uitvoeren. Deze functie kunt dat u taken met behulp van bekende scripttalen maken. Zie voor meer informatie [Shell uitvoeren taak](#ShellExecuteTask).  

 Als uw vereisten verder dan het uitvoeren van scripts, kunt u aangepaste UDI taken schrijven. *UDI taken* zijn dll's die zijn geschreven in C++ en implementeer de **ITask** interface. Registreren van het DLL-bestand met de bibliotheek van de Wizard UDI taak door het maken van een configuratiebestand van de Wizard UDI (.config) en plaatst deze in de *installation_folder*\Bin\Config map (waarbij *installation_ map* is de map waarin u MDT hebt geïnstalleerd). Zie voor meer informatie over het ontwikkelen van aangepaste UDI taken, de sectie 'Maken van aangepaste UDI taken', in de *Driven installatie-handleiding voor ontwikkelaars*.  

####  <a name="UDITaskSequence"></a>UDI Takenreeks  
 U maakt een UDI takenreeks met behulp van een van de volgende UDI-specifieke MDT taak reeks sjablonen, die de Wizard UDI op de juiste stap in de takenreeks wordt uitgevoerd:  

-   **Installatie door gebruikers geïnitieerde Takenreeks wordt uitgevoerd.** Deze taak sequence sjabloon wordt gebruikt voor de nieuwe Computer, Computer vernieuwen en vervang Computer MDT implementatiescenario's.  

-   **Takenreeks van de installatie door gebruikers geïnitieerde vervangen.** Deze taak sequence-sjabloon is de eerste stap in een proces in twee stappen in het implementatiescenario Computer vervangen en wordt gebruikt voor het vastleggen van gegevens van de migratie van gebruikersstatus. De tweede stap in het proces in twee stappen is de Driven installatie Takenreeks taak sequence sjabloon die u kunt de doeltoepassingen en het besturingssysteem implementeren en herstellen van de migratie van gebruikersstatusgegevens opgeslagen tijdens de eerste stap van het proces.  

 Zie de sectie 'Identificeren de UDI taak reeks sjablonen in MDT', in het document MDT voor meer informatie over de taaksjablonen van reeks UDI, *met behulp van de Microsoft Deployment Toolkit*. Zie de sectie "Identificeren UDI proces onderdelen voor implementatie", in de MDT-document voor meer informatie over deze onderdelen *met behulp van de Microsoft Deployment Toolkit*, die deel uitmaakt van de MDT.  

####  <a name="UDIWizard"></a>De Wizard UDI  
 De Wizard UDI levert de gebruikersinterface voor het verzamelen van implementatie-instellingen die de UDI-takenreeksen gebruiken. De Wizard UDI wordt gestart als onderdeel van een takenreeks UDI en verzamelt de vereiste configuratie-informatie voor het aanpassen van de implementatie van de Windows-besturingssystemen en toepassingen. De wizardpagina's lezen de configuratie-instellingen uit het configuratiebestand van de Wizard UDI die is aangepast met behulp van de waarde van de Wizard UDI.  

 De Wizard UDI wordt geïnitieerd door de **Wizard UDI** takenreeksstap in takenreeksen die zijn gemaakt met behulp van de UDI taak reeks sjablonen. De **Wizard UDI** takenreeksstap voert het script UDIWizard.wsf, die op zijn beurt de Wizard UDI (OSDSetupWizard.exe initieert). Tabel 9 ziet u de Wizard UDI opdrachtregelparameters en een korte beschrijving van elke.  

### <a name="table-9-udi-wizard-command-line-parameters"></a>Tabel 9. Opdrachtregelparameters van de Wizard UDI  

|**Parameter**|**Beschrijving**|  
|-|-|  
|**/ Preview**|Hiermee kunt u een voorbeeld van de huidige configuratie van de wizard door het inschakelen van de **volgende** knop waarmee u pagina's te verplaatsen zonder geldige invoer.|  
|**/ XML**|Geeft de naam van het configuratiebestand van de Wizard UDI. Deze parameter het script UDIWizard.wsf automatisch ingesteld op het bestand OSDSetupWizard.xml, dat is opgeslagen in de map waarin de takenreeks logboekbestanden opslaat. Deze parameter wordt standaard ingesteld op het bestand config.xml.<br /><br /> De syntaxis voor deze parameter is als volgt (waarbij `<full_path>` is het volledig gekwalificeerde pad naar het .xml-bestand, inclusief de bestandsnaam en de extensie):<br /><br /> `/xml:<full_path>`|  
|**/Stage**|Hiermee geeft u de naam van de fase UDI om uit te voeren. Deze parameter het script UDIWizard.wsf automatisch ingesteld op de juiste fase, zoals beschreven in [UDI fase verwijzing](#UDIStageReference). Deze parameter wordt standaard ingesteld op de eerste fase in het configuratiebestand van de Wizard UDI.<br /><br /> De syntaxis voor deze parameter is als volgt (waarbij `<stage_name>` is de naam van de fase worden uitgevoerd):<br /><br /> `/stage:<stage_name>`<br /><br /> Opmerking:<br /><br /> De waarde voor < stage_name > is hoofdlettergevoelig.|  
|**/ Locale**|Hiermee geeft u de gewenste taal in de Wizard UDI in de vorm van een LCID (locale identifier), die wordt vertegenwoordigd door een numerieke waarde. Zie voor een lijst van de beschikbare LCID's [landinstellingen-id's toegewezen door Microsoft](http://msdn.microsoft.com/goglobal/bb964664).<br /><br /> U zou deze lijst gebruiken om te identificeren van de taal die u wilt gebruiken, en geef vervolgens de bijbehorende LCID.<br /><br /> De syntaxis voor deze parameter is als volgt (waarbij `<locale_id>` is de numerieke waarde van het LCID moet worden gebruikt):<br /><br /> `/locale:<locale_id>`|  

####  <a name="UDIWizardApplicationConfigurationFile"></a>UDI Wizard toepassingsconfiguratiebestand  
 De **ApplicationPage** pagina van de wizard configureert u de Wizard UDI toepassingsconfiguratiebestand, houdt de lijst met software worden geïnstalleerd. Dit bestand bevat een vermelding voor elke Configuration Manager-toepassing of het programma en het pakket die zijn toegevoegd met de waarde van de Wizard UDI.  

 Dit bestand heeft dezelfde naam als het configuratiebestand van de Wizard UDI maar met de extensie .app. Bijvoorbeeld, als de naam van het configuratiebestand van de Wizard UDI *Config.xml,* wordt het bijbehorende configuratiebestand van de Wizard UDI zou *Config.xml.app.* Dit bestand is de bijbehorende naar het configuratiebestand van de Wizard UDI.  

####  <a name="UDIWizardConfigurationFile"></a>Bestand voor configuratie van de Wizard UDI  
 De Wizard UDI leest het configuratiebestand van de Wizard UDI om te bepalen van de wizardpagina's moet worden weergegeven, de volgorde van de wizardpagina's, worden alle standaardinstellingen voor besturingselementen op de wizardpagina's, en of de besturingselementen zijn ingeschakeld of uitgeschakeld. Dit bestand bevat alle configuratie-instellingen die worden weergegeven in de Wizard UDI en zijn geconfigureerd met de waarde van de Wizard UDI.  

 Een afzonderlijk configuratiebestand: het configuratiebestand van de Wizard UDI: wordt gebruikt voor het configureren van toepassingen die worden geïnstalleerd op de doelcomputer.  

####  <a name="UDIWizardDesigner"></a>De Wizard UDI  
 De waarde van de Wizard UDI is het belangrijkste instrument voor het aanpassen van wizardpagina's voor de verschillende scenario's die ondersteuning biedt voor UDI. Wijzigingen in de ontwerpfunctie van de Wizard UDI zijn opgeslagen in het configuratiebestand van de Wizard UDI en uiteindelijk wordt weergegeven in de ervaring van de gebruiker in de Wizard UDI. De gebruiker die de implementatie wordt uitgevoerd, ziet alleen de wizardpagina's in de Wizard UDI die u hebt geselecteerd en geconfigureerd met behulp van de waarde van de Wizard UDI.  

 Hoewel de Wizard UDI wordt uitgevoerd met het standaardconfiguratiebestand van de Wizard UDI, zou de wizardpagina's niet correct worden geconfigureerd. Het is raadzaam dat u de waarde van de Wizard UDI voor het configureren van de gebruikerservaring van de Wizard UDI.  

> [!NOTE]
>  Voor het uitvoeren van de waarde van de Wizard UDI, moet u de juiste rechten hebben in Configuration Manager om toegang tot objecten, zoals pakketten, toepassingen of installatiekopieën.  

####  <a name="Validator"></a>Validator  
 U UDI validatiefuncties gebruiken om ervoor te zorgen dat de juiste informatie is ingevoerd in de tekstvelden op wizardpagina's in de Wizard UDI. UDI bevat verschillende ingebouwde validatiefuncties die help uitvoeren van typische validaties van de velden die worden gebruikt voor het invoeren van tekst, zoals voorkomen dat gebruikers voeren ongeldige tekens en ervoor te zorgen dat het veld is niet leeg. Wanneer een validatie van een ongeldige waarde in het tekstvak detecteert, wordt een bericht weergegeven op de wizardpagina en de **volgende** knop blijft uitgeschakeld totdat alle ongeldige vermeldingen opgelost zijn.  

 UDI omvat ingebouwde validatiefuncties waarmee u kunt de meeste van de validatie nodig is voor implementatie uitvoeren. Zie voor meer informatie over de ingebouwde validatiefuncties UDI [ingebouwde UDI validatiefuncties](#BuiltinUDIValidators).  

 Als uw vereisten verder dan de ingebouwde UDI validatiefuncties, kunt u aangepaste UDI validatiefuncties schrijven. *UDI validatiefuncties* zijn geschreven in C++ DLL die implementeren de **IValidator** interface. Het DLL-bestand met de validatie van de Wizard UDI bibliotheek registreren door het maken van een configuratiebestand van de Wizard UDI (.config) en plaatst deze in de *installation_folder*\Bin\Config map (waarbij *installation_ map* is de map waarin u MDT hebt geïnstalleerd). Zie de sectie 'Maken van aangepaste UDI validatiefuncties', in de MDT-document voor meer informatie over het ontwikkelen van aangepaste UDI taken *Driven installatie-handleiding voor ontwikkelaars*.  

####  <a name="WizardPage"></a>Pagina van wizard  
 U kunt een wizardpagina gebruiken voor het verzamelen van configuratie-informatie in de Wizard UDI. Configureer UDI wizardpagina's met behulp van de waarde van de Wizard UDI. De configuratie-instellingen worden opgeslagen in het configuratiebestand van de Wizard UDI en worden gelezen door de wizardpagina wanneer de pagina in de Wizard UDI wordt geïnitialiseerd.  

 Wizardpagina's worden opgeslagen in de wizard pagina bibliotheek en ze kunnen worden gebruikt in een of meer UDI fasen uitgevoerd. Dit ontwerp kunt u voor het configureren van een pagina van de wizard die wordt gedeeld tussen fasen eenmaal voor alle fasen aanzienlijk verminderen de hoeveelheid moeite en de complexiteit van de wizard de paginaconfiguratie bijwerken.  

 UDI omvat ingebouwde wizardpagina's en de wizard pagina editors die meestal voldoende voor de meeste implementaties zijn. Zie voor meer informatie over de ingebouwde wizardpagina's [ingebouwde UDI wizardpagina's](#BuiltinUDIWizardPages).  

 Als uw vereisten verder dan de ingebouwde UDI wizardpagina's en de bijbehorende wizard pagina editors, kunt u aangepaste UDI wizardpagina's en wizard pagina editors schrijven. UDI wizardpagina's worden geïmplementeerd als dll-bestanden in de Wizard UDI leest. Wizard pagina editors worden gemaakt met C++ in Visual Studio.  

 Zie de sectie 'Maken van aangepaste UDI wizardpagina's ', in de MDT-document voor meer informatie over het ontwikkelen van aangepaste UDI wizardpagina's *Driven installatie-handleiding voor ontwikkelaars*.  

####  <a name="WizardPageEditor"></a>Wizard pagina-Editor  
 Een wizard-pagina-editor kunt u een wizardpagina configureren in de waarde van de Wizard UDI. Een wizard-pagina-editor werkt de wizard Configuratie-instellingen voor pagina in het configuratiebestand van de Wizard UDI; UDI bevat een ingebouwde wizard-pagina-editor voor elke pagina van de ingebouwde wizard. Zie voor meer informatie over de ingebouwde wizardpagina's en de wizard pagina editors [ingebouwde UDI wizardpagina's](#BuiltinUDIWizardPages).  

 Als uw vereisten verder dan de ingebouwde UDI wizardpagina's en de bijbehorende wizard pagina editors, kunt u aangepaste UDI wizardpagina's en wizard pagina editors schrijven. UDI wizard pagina editors worden geïmplementeerd als dll-bestanden die de waarde van de Wizard UDI leest. Maak wizardpagina editors gebruiken:  

-   [Windows Presentation Foundation](http://msdn.microsoft.com/library/ms754130.aspx) versie 4.0  

-   [Microsoft Prismabewerking](http://compositewpf.codeplex.com/) versie 4.0  

-   [Microsoft Unity Application Block](http://unity.codeplex.com/) (Unity) versie 2.1  

 Zie de sectie 'Maken van aangepaste Wizard pagina Editors', in de MDT-document voor meer informatie over het ontwikkelen van aangepaste UDI wizard pagina editors *Driven installatie-handleiding voor ontwikkelaars*.  

###  <a name="OSDResultsReference"></a>OSDResults verwijzing  
 **OSDResults** wordt een deel van UDI met de resultaten van een implementatie uitgevoerd met behulp van UDI. **OSDResults** geeft de **implementatie voltooid** in het dialoogvenster. **OSDResults** wordt weergegeven voordat Windows logon de eerste keer dat de doelcomputer wordt gestart. De gebruiker kan gebruiken **OSDResults** en de informatie in de **implementatie voltooid** in het dialoogvenster om te bepalen van de voltooiingsstatus van het implementatieproces en de configuratie van de computer vóór voor de eerste keer aanmeldt. Daarnaast biedt de informatie in **OSDResults** kan worden gebruikt voor het oplossen van problemen aangetroffen tijdens het implementatieproces.  

 U kunt sommige van de gebruikersinterface-elementen voor **OSDResults** Configuration Manager-pakket met behulp van het bestand OSDResults.exe.config, dat zich in Tools\OSDResults in de MDT bevindt-bestanden. Tabel 10 geeft een lijst van de configuratie-instellingen in het bestand OSDResults.exe.config.  

### <a name="table-10-configuration-settings-in-the-osdresultsexeconfig-file"></a>Tabel 10. Configuratie-instellingen in het bestand OSDResults.exe.config  

|**Instelling**|**Beschrijving**|  
|-|-|  
|**headerImagePath**|Deze instelling kunt u het volledig gekwalificeerde of relatieve pad opgeven naar een bmp-bestand dat wordt weergegeven in de koptekst van de **OSDResults** in het dialoogvenster.<br /><br /> De standaardwaarde voor deze instelling is als volgt:<br /><br /> `images\UDI_Wizard_Banner.bmp`|  
|**backgroundWallpaper**|Deze instelling kunt u opgeven dat het volledig gekwalificeerde of relatieve pad naar een jpg-bestand dat wordt weergegeven als de achtergrond van de **OSDResults** in het dialoogvenster.<br /><br /> De standaardwaarde voor deze instelling is als volgt:<br /><br /> `images\Wallpaper.jpg`|  
|**welcomeText**|Deze instelling kunt u de tekst die de gebruiker is geïnteresseerd en bevat informatie over het implementatieproces op te geven. Deze wordt weergegeven in de **OSDResults** in het dialoogvenster.|  
|**completedText**|Deze instelling kunt u de tekst waarmee wordt aangegeven of de implementatie voltooid is op te geven. Deze wordt weergegeven in de **OSDResults** in het dialoogvenster.|  
|**timeoutMinutes**|Deze instelling kunt u opgeven hoe lang de **OSDResults** in het dialoogvenster wordt weergegeven voordat het automatisch het Windows-aanmeldingsscherm om weer te geven. De waarde voor deze instelling is opgegeven in minuten.<br /><br /> De standaardwaarde voor deze instelling is nul (0), wat dat aangeeft de **OSDResults** in het dialoogvenster wordt weergegeven voor onbepaalde tijd totdat handmatig gesloten.|  

 Hieronder volgt het hoofdproces voor hoe de **OSDResults** functie werkt in UDI:  

1.  Een takenreeks wordt uitgevoerd op de doelcomputer.  

     De takenreeks is gebaseerd op een van de followUDI taak sequence-sjablonen:  

    -   **Gebruiker gestuurd installatie Takenreeks**. Deze taak sequence sjabloon wordt gebruikt voor de nieuwe Computer MDT, Computer vernieuwen en vervang Computer MDT implementatiescenario's.  

    -   **Door gebruikers geïnitieerde installatie vervangen Takenreeks**. Deze taak sequence-sjabloon is de eerste stap in een proces in twee stappen in het implementatiescenario MDT vervangen Computer en wordt gebruikt voor het vastleggen van gegevens van de migratie van gebruikersstatus. De tweede stap van de twee stappen is het implementatiescenario voor de nieuwe Computer MDT met behulp van de **Takenreeks gebruiker gebaseerde installatie** taak sequence sjabloon die wordt gebruikt voor het implementeren van de doeltoepassingen en het besturingssysteem en opgeslagen tijdens de eerste stap van het proces migratiegegevens van de gebruiker herstellen  

     Voor meer informatie over de:  

    -   UDI taak reeks sjablonen, Zie de sectie 'Identificeren de UDI taak reeks sjablonen in MDT', in het document MDT *met behulp van de Microsoft Deployment Toolkit*  

    -   Relatie tussen MDT implementatiescenario's en UDI fasen, Zie [UDI fase verwijzing](#UDIStageReference)  

2.  Tijdens de takenreeks, de configuratie-instellingen van de invoer van de gebruiker in de Wizard UDI en takenreeksvariabelen worden opgeslagen in de *% DEPLOYROOT %*\Tools\OSDResults map op de doelcomputer (waarbij *%D EPLOYROOT %* is de hoofdmap van de map waarin de MDT-bestanden lokaal in de cache op de doelcomputer).  

3.  In de **OSD-resultaten en Branding** groep in de takenreeks, de volgende takenreeksstappen die invloed hebben op worden uitgevoerd **OSDResults**:  

    -   **Cache OSD-resultaten.** Deze takenreeksstap kopieert de inhoud van de *% DEPLOYROOT %*\Tools\OSDResults-map naar de map %WINDIR%\UDI op de doelcomputer. Dit zorgt ervoor dat de inhoud van de map OSDResults worden vastgehouden nadat de takenreeks is voltooid.  

    -   **OSD-resultaten worden uitgevoerd.** Deze stap van de taken configureert u de doelcomputer om uit te voeren **OSDResults** de eerste keer dat de computer wordt gestart.  

4.  De doelcomputer voor het eerst wordt gestart en OSDResults.exe voorafgaand aan het Windows-aanmeldingsscherm wordt uitgevoerd.  

     De **Welkom** tabblad de **implementatie voltooid** in het dialoogvenster wordt weergegeven. De **Welkom** tabblad bevat nuttige informatie over de implementatie en neem contact op met de informatie in het geval dat problemen met de implementatie worden ontdekt.  

     Lees de informatie op de **implementatieoverzicht** en **toepassingen geïnstalleerd** tabbladen om te controleren of het besturingssysteem en toepassingen correct zijn geïnstalleerd. Wanneer u klaar bent met het controleren van deze tabellen, klikt u op **Windows starten** Meld u aan bij Windows 7 voor de eerste keer.  

    > [!NOTE]
    >  Configuration Manager-toepassingen worden niet weergegeven op de **toepassingen geïnstalleerd** tabblad. De Configuration Manager-toepassingen worden gedetecteerd nadat de gebruiker zich op de doelcomputer de eerste keer aanmeldt.  

5.  De Windows-aanmeldingsscherm wordt weergegeven en het aanmeldingsproces normaal hervat.  

     AppInstall.exe kan de eerste keer dat een gebruiker zich bij de doelcomputer aanmeldt wordt uitgevoerd. Zie voor meer informatie over dit proces [gebruikersgerichte App installatieprogramma verwijzing](#UserCentricAppInstallerReference).  

###  <a name="UserCentricAppInstallerReference"></a>Het installatieprogramma van de gebruiker gerichte App-verwijzing  
 De functie App-installatieprogramma gebruikersgerichte in UDI wordt gebruikt voor het rapporteren van alle toepassingen geïnstalleerd tijdens de implementatie UDI aan de Application Catalog-functie in Configuration Manager. De functie gebruikersgerichte App-installatieprogramma biedt u de koppeling tussen de toepassingen die ingeschakeld op de **ApplicatonPage** wizardpagina in de Wizard UDI en eventuele optionele Configuration Manager-toepassingen worden aangekondigd aan de gebruikers.  

 Zie voor meer informatie over de Application Catalog-functie in Configuration Manager [Toepassingsbeheer in Configuration Manager](http://technet.microsoft.com/library/gg699373.aspx).  

 Hier volgt het proces op hoog niveau voor de werking van de functie App-installatie in UDI:  

1.  Configuration Manager-toepassingen worden gemaakt in Configuration Manager.  

     Zie de volgende bronnen voor meer informatie over het maken en beheren van Configuration Manager-toepassingen:  

    -   [Toepassingen maken in Configuration Manager](http://technet.microsoft.com/library/gg682159.aspx)  

    -   [Bewerkingen en onderhoud voor Toepassingsbeheer in Configuration Manager](http://technet.microsoft.com/library/gg681963.aspx)  

2.  De Configuration Manager-gebruikersverzamelingen worden gemaakt en gebruikers worden toegevoegd aan de verzameling.  

     Zie de volgende bronnen voor meer informatie over het maken en beheren van verzamelingen van gebruikers en gebruikers toevoegen aan verzamelingen:  

    -   [Verzamelingen in Configuration Manager](http://technet.microsoft.com/library/gg682169.aspx)  

    -   [Verzamelingen maken in Configuration Manager](http://technet.microsoft.com/library/gg712295.aspx)  

3.  De Configuration Manager-toepassingen worden op de gebruikersverzamelingen geïmplementeerd.  

     Zie voor meer informatie over het implementeren van de toepassingen op gebruikersverzamelingen [toepassingen implementeren in Configuration Manager](http://technet.microsoft.com/library/gg682082.aspx).  

4.  De Configuration Manager-toepassingen bestaan beschikbaar is op de **ApplicatonPage** pagina van de wizard met behulp van de waarde van de Wizard UDI.  

     Voor meer informatie over het maken van Configuration Manager-toepassingen die beschikbaar is op de **ApplicatonPage** wizardpagina, Zie de sectie ' stap 5-11: Het configuratiebestand van de UDI Wizard aanpassen voor de doelcomputer', in het document MDT *introductiehandleiding voor Driven installatie*.  

5.  UDA is geconfigureerd met een van de volgende methoden:  

    -   In de Configuration Manager-console (Zie voor meer informatie over het configureren van UDA in de Configuration Manager-console [het beheren van affiniteit van gebruikersapparaat in Configuration Manager](http://technet.microsoft.com/library/gg699365.aspx).)  

    -   Op de **UDAPage** wizardpagina in de Wizard UDI (voor meer informatie over de **UDAPage** wizardpagina Zie [UDAPage](#UDAPage).)  

     Nadat UDA is geconfigureerd, worden de opgegeven gebruikersaccount de primaire gebruiker voor de doelcomputer.  

    > [!NOTE]
    >  UDA kan alleen worden geconfigureerd door UDI in de nieuwe Computer implementatiescenario. Deze kan niet worden geconfigureerd in de implementatiescenario's voor Computer vernieuwen of vervangen.  

6.  De takenreeks wordt uitgevoerd, en de gebruiker selecteert u de Configuration Manager-toepassingen op de **ApplicatonPage** wizardpagina in de Wizard UDI.  

     De Wizard UDI wordt uitgevoerd de **Wizard UDI** takenreeksstap de **Preinstall** groep van de takenreeks. Wanneer de gebruiker de Configuration Manager-toepassingen selecteert op de **ApplicatonPage** pagina van de wizard de pagina van de wizard maakt een afzonderlijke takenreeksvariabele voor elke toepassing die is geselecteerd.  

     Voor meer informatie over het selecteren van de Configuration Manager-toepassingen op de **ApplicatonPage** wizardpagina in de Wizard UDI, Zie de sectie ' stap 6-4: Start de doelcomputer met opstartbare Media voor de Takenreeks', in het document MDT *introductiehandleiding voor Driven installatie*.  

7.  De takenreeks wordt geïnstalleerd voor de Configuration Manager-toepassingen die zijn geselecteerd in de vorige stap.  

     De Configuration Manager-toepassingen worden geïnstalleerd met behulp van de volgende takenreeksstappen in de **toepassingen installeren** groep in de takenreeks:  

    -   **Lijst met twee cijfers converteren**  

    -   **Toepassing installeren**  

8.  De takenreeks voert de volgende taken in de **OSD-resultaten en Branding** groep voordat u het doelbesturingssysteem voor het eerst start:  

    -   Kopieert de gegevens die wordt gebruikt voor OSDResults.exe naar de map %WINDIR%\UDI op de doelcomputer in de **resultaten in de Cache OSD** takenreeksstap  

    -   Registreert de takenreeksvariabelen die zijn gemaakt in stap 6 voor de Configuration Manager-toepassingen in het register op de doelcomputer in de **huisstijl naar Reg** en **huisstijl naar Reg x64** takenreeksstappen  

         De variabelen voor de takenreeks taken worden opgeslagen in de volgende locatie in het register:  

         **HKEY_LOCAL_MACHINE\Software\Microsoft\MPSD\OSD**  

    -   Hiermee configureert u het doelbesturingssysteem aan OSDResults.exe automatisch uitgevoerd wanneer de computer wordt gestart voordat de Windows-aanmeldingsscherm weergegeven in de **uitvoeren OSD resultaten** takenreeksstap  

    -   Hiermee configureert u het doelbesturingssysteem aan automatisch uitvoeren AppInstall.exe wanneer een gebruiker zich aanmeldt bij de computer voor het eerst in de **uitvoeren OSD resultaten** takenreeksstap  

    -   Hiermee configureert u een taak op het doelbesturingssysteem verwijderen van de map %WINDIR%\UDI één maand uit de datum van de implementatie  

9. De doelcomputer wordt gestart en OSDResults.exe wordt uitgevoerd.  

     Zie voor meer informatie over OSDResults.exe [OSDResults verwijzing](#OSDResultsReference).  

10. Een gebruiker zich aanmeldt bij de doelcomputer en AppInstall.exe automatisch wordt gestart.  

11. AppInstall controleert of de momenteel aangemelde gebruiker een primaire gebruiker die is geconfigureerd in UDA.  

     Een *primaire gebruiker* is een gebruiker die gebruikmaakt van het apparaat regelmatig gecontroleerd en wordt beschouwd als de eigenaar of een van de eigenaars van het apparaat.  

     Als de momenteel aangemelde gebruiker:  

    -   Primaire gebruiker, AppInstall.exe stopt  

    -   Een primaire gebruiker AppInstall.exe leest vervolgens de registervermeldingen die is opgeslagen in stap 8 om te bepalen welke toepassingen zijn geïnstalleerd  

12. AppIntaller koppelt aan Configuration Manager en leest de catalogus met toepassingen met behulp van de volgende stappen uit:  

    1.  AppInstall wacht 5 minuten nadat deze is gestart om toe te staan van de Configuration Manager-beleidsregels beschikbaar.  

    2.  Na 5 minuten probeert AppInstall verbinding maken met de Application Catalog.  

    3.  Als AppInstall kan geen verbinding maken, vervolgens wacht deze enige tijd voordat u probeert opnieuw verbinding te maken.  

    4.  AppInstall verbinding probeert te maken tot vijf keer voordat u afsluit.  

     U kunt de vertraging in de time-out voor verbinding en het aantal nieuwe pogingen configureren voor AppInstall met behulp van het bestand AppInstall.exe.config, dat zich in de map Tools\OSDResults in het Configuration Manager-pakket van de MDT-bestanden bevindt. Tabel 11 geeft een lijst van de configuratie-instellingen in het bestand AppInstall.exe.config.  

### <a name="table-11-configuration-settings-in-the-appinstallexeconfig-file"></a>Tabel 11. Configuratie-instellingen in het bestand AppInstall.exe.config  

|**Instelling**|**Beschrijving**|  
|-|-|  
|**timeoutMinutes**|Deze instelling kunt u opgeven hoe lang voor AppInstall moet worden gewacht op een reactie van de Toepassingscatalogus van Configuration Manager voordat een time-out optreedt. De waarde is opgegeven in minuten. De standaardwaarde voor deze instelling is **5**.|  
|**delayTimer**|Deze instelling kunt u de tijdsduur voor AppInstall moet worden gewacht voordat de verbinding met de Configuration Manager Application Catalog opgeven. De waarde is opgegeven in minuten. De standaardwaarde voor deze instelling is **5**.|  

1.  AppInstall vergelijkt de lijst met toepassingen die zijn gedetecteerd in het register met de lijst met toepassingen die beschikbaar zijn in de Toepassingscatalogus van Configuration Manager voor de momenteel aangemelde gebruiker.  

     Als de toepassing wordt gedetecteerd in het register:  

    -   Is beschikbaar in de Application Catalog, en vervolgens AppInstall.exe toegewezen van de toepassingen en de toepassingen identificeert als bestaande zowel in het register en in de Application Catalog. Deze toepassingen wordt gebruikt in de volgende stap.  

    -   Is niet beschikbaar in de Application Catalog, en vervolgens AppInstall.exe geen een toewijzing maakt. Deze toepassingen wordt niet gebruikt in de volgende stap.  

2.  AppInstall gebruikt Configuration Manager-API's voor het initiëren van de installatie van de toegewezen toepassingen.  

     De toepassingen die worden gebruikt in deze stap zijn toegewezen in de vorige stap. Dat wil zeggen, zijn ze vermeld in het register zowel gevonden in de Application Catalog.  

3.  Als onderdeel van het installatieproces detecteert Configuration Manager of de toepassing al is geïnstalleerd.  

     Omdat de toepassing al is geïnstalleerd, wordt dat de toepassing heeft geïmplementeerd die gebruiker en de toepassing Configuration Manager-records worden weergegeven in Software Center voor die gebruiker. Configuration Manager begint beheren en controleren van de toepassing voor die gebruiker.  

4.  Na een maand, de taak gemaakt op de doelcomputer in stap 8 wordt uitgevoerd en verwijdert u de map %WINDIR%\UDI.  

     De map behouden voor 1 maand, zodat de primaire gebruikers de mogelijkheid logboek op en voer uit AppInstall.exe hebben.  

###  <a name="UDIStageReference"></a>UDI fase verwijzing  
 De MDT-implementatiescenario's gebruiken een of meer UDI [fase](#Stage). Elk stadium UDI is gebruikt in de MDT-implementatiescenario's wordt besproken in een volgende sectie in de context van het scenario van de MDT-implementatie. In sommige gevallen MDT-implementatie is slechts één fase wordt gebruikt. Meerdere fasen worden in andere situaties MDT-implementatie gebruikt in het scenario. Zie de sectie 'Identificeren implementatiescenario's ', in de MDT-document voor meer informatie over de implementatiescenario's voor MDT *met behulp van de Microsoft Deployment Toolkit.*  

 Tabel 12 geeft een lijst van de implementatiescenario's voor MDT en biedt een korte beschrijving van elk, hoe elk scenario is geselecteerd en welke fasen UDI worden gebruikt in elk implementatiescenario. MDT wordt automatisch bepaald welke implementatiescenario MDT te gebruiken op basis van de MDT taak sequence sjabloon die u gebruiken om de takenreeks te maken en hoe de takenreeks wordt gestart.  

 Elk stadium UDI is gebruikt in de MDT-implementatiescenario's wordt besproken in een volgende sectie in de context van het scenario van de MDT-implementatie. In sommige gevallen MDT-implementatie is slechts één fase wordt gebruikt. Meerdere fasen worden in andere situaties MDT-implementatie gebruikt in het scenario. Zie de sectie 'Identificeren implementatiescenario's ', in de MDT-document voor meer informatie over de implementatiescenario's voor MDT *met behulp van de Microsoft Deployment Toolkit.*  

### <a name="table-12-mdt-deployment-scenarios-and-udi-stages"></a>Tabel 12. MDT implementatiescenario's en UDI fasen  

|**Scenario**|**Beschrijving**|   
|-|-|  
|Nieuwe Computer|MDT voor UDI wordt automatisch geselecteerd voor dit scenario wanneer u:<br /><br /> -De aangekondigd takenreeks met behulp van de sjabloon Driven installatie Takenreeks taak reeks maken<br /><br /> -De takenreeks start in Windows PE met PXE-opstart taak sequence boot media of voorbereide media voor de NEWCOMPUTER. Voorbereide fase<br /><br /> Dit scenario kan worden gebruikt met traditionele implementaties of met implementaties met voorbereide media in Configuration Manager wordt ondersteund. Voer de Wizard UDI met de volgende fasen UDI ter ondersteuning van elk type implementatie:<br /><br /> - **NEWCOMPUTER-fase.** De Wizard UDI wordt uitgevoerd met dit stadium in de **Driven installatie Takenreeks** takenreeks wanneer de installatiekopie is opgeslagen op distributiepunten. Zie voor meer informatie [NEWCOMPUTER fase](#NEWCOMPUTERStage).<br /><br /> -                         **NEWCOMPUTER. Voorbereidende fase.** De Wizard UDI wordt uitgevoerd met dit stadium in de **Driven installatie Takenreeks** takenreeks wanneer de installatiekopie is opgeslagen op een lokale schijf op de doelcomputer (voorbereide). Zie voor meer informatie [NEWCOMPUTER. Fase voorbereid](#NEWCOMPUTERPrestagedStage).|  
|Computer vernieuwen|MDT voor UDI wordt automatisch geselecteerd voor dit scenario wanneer u:<br /><br /> -De aangekondigd takenreeks met behulp van de sjabloon Driven installatie Takenreeks taak reeks maken<br /><br /> -De takenreeks start in de bestaande Windows-besturingssysteem op de doelcomputer (niet in Windows PE)<br /><br /> -De Wizard UDI wordt uitgevoerd met de fase vernieuwen voor de ondersteuning van dit implementatiescenario. Zie voor meer informatie [vernieuwen fase](#REFRESHStage).|  
|Vervang de Computer|Dit scenario omvat een bestaande computer en de computer van een vervanging. Een afzonderlijke takenreeks is gemaakt en uitvoeren op elke computer, zoals beschreven in het volgende proces:<br /><br /> -                          **Op de bestaande computer.** MDT voor UDI dit gedeelte van het scenario voor het automatisch geselecteerd wanneer u:<br /><br /> -De aangekondigd takenreeks met de installatie Driven vervangen Takenreeks taak sequence-sjabloon maken<br /><br /> Start de takenreeks in de bestaande Windows-besturingssysteem op de doelcomputer (niet in Windows PE)<br /><br /> De Wizard UDI wordt uitgevoerd met de volgende fasen UDI ter ondersteuning van dit implementatiescenario:<br /><br /> - **Fase vervangen.** Deze fase wordt uitgevoerd in de bestaande Windows-besturingssysteem en configuratie-informatie van Windows wordt vastgelegd.<br /><br /> -                          **VERVANGEN. WinPE-fase.** Deze fase wordt uitgevoerd in Windows PE en voltooit het vastleggen van configuratie-informatie uit de bestaande computer — bijvoorbeeld, status migratiegegevens USMT uitgevoerd en vastleggen van de gebruiker.<br /><br /> De gebruikersstatus wordt vastgelegd op een gedeelde netwerkmap of op een lokale USB-station.<br /><br /> Voor meer informatie over het vervangen en vervangen. Fasen in WinPE, Zie [vervangen en vervangen. WinPE fasen](#REPLACEandREPLACEWinPEStages).<br /><br /> -                          **Op de computer vervanging.** Dit gedeelte van het scenario is identiek aan het scenario met een nieuwe Computer, behalve dat de gebruikersstatus die is vastgelegd in de vorige stap is hersteld. MDT voor UDI dit gedeelte van het scenario voor het automatisch geselecteerd wanneer u:<br /><br /> -De aangekondigd takenreeks met behulp van de sjabloon Driven installatie Takenreeks taak reeks maken<br /><br /> -De takenreeks start in Windows PE met PXE-opstart taak sequence boot media of voorbereide media voor de NEWCOMPUTER. Voorbereide fase.<br /><br /> Dit gedeelte van het scenario kan worden gebruikt met traditionele implementaties of met implementaties met voorbereide media in Configuration Manager wordt ondersteund. Als onderdeel van dit gedeelte van het scenario, wordt migratiegegevens van de gebruikersstatus hersteld. De Wizard UDI wordt uitgevoerd met de volgende fasen UDI ter ondersteuning van elk type implementatie:<br /><br /> -                          **NEWCOMPUTER-fase.** De Wizard UDI wordt uitgevoerd met dit stadium in de **Driven installatie Takenreeks** takenreeks wanneer de installatiekopie is opgeslagen op distributiepunten. Zie voor meer informatie [NEWCOMPUTER fase](#NEWCOMPUTERStage).<br /><br /> -                          **NEWCOMPUTER. Voorbereidende fase.** De Wizard UDI wordt uitgevoerd met dit stadium in de **Driven installatie Takenreeks** takenreeks wanneer de installatiekopie is opgeslagen op een lokale schijf op de doelcomputer (voorbereide). Zie voor meer informatie [NEWCOMPUTER. Fase voorbereid](#NEWCOMPUTERPrestagedStage).|  

#####  <a name="NEWCOMPUTERStage"></a>NEWCOMPUTER fase  
 Afbeelding 1 ziet u het gebruik van de fase NEWCOMPUTER in een takenreeks die is gemaakt met behulp van de gebruiker\-gebaseerde installatie Takenreeks taak sequence sjabloon. Het belangrijkste verschil tussen de aanroepen van de fase NEWCOMPUTER en de NEWCOMPUTER takenreeksen. Fase voorbereid is dat de takenreeks de NEWCOMPUTER aanroepen. Voorbereide fase kan niet worden uitgevoerd de **Besturingssysteeminstallatiekopie toepassen** takenreeksstap, omdat de installatiekopie van het besturingssysteem al op de doelcomputer bevindt zich.  

 ![UDI verwijzing 1](media/UDIReference1.jpg)  

 **Afbeelding SEQ afbeelding \\ \* ARABIC 1. Processtroom voor de fase NEWCOMPUTER**  

#####  <a name="NEWCOMPUTERPrestagedStage"></a>NEWCOMPUTER. Voorbereide fase  
 Afbeelding 2 ziet u de hoge\-niveau processtroom voor de NEWCOMPUTER. Fase in een takenreeks die is gemaakt met behulp van de gebruiker voorbereid\-gebaseerde installatie Takenreeks taak sequence sjabloon. Het belangrijkste verschil tussen de aanroepen van de fase NEWCOMPUTER en de NEWCOMPUTER takenreeksen. Fase voorbereid is dat de takenreeks de NEWCOMPUTER aanroepen. Voorbereide fase kan niet worden uitgevoerd de **Besturingssysteeminstallatiekopie toepassen** takenreeksstap, omdat de installatiekopie van het besturingssysteem al op de doelcomputer bevindt zich.  

 ![UDI verwijzing 2](media/UDIReference2.jpg)  

 **Afbeelding 2. Processen stroom voor de NEWCOMPUTER. Voorbereide fase**  

####  <a name="REFRESHStage"></a>Fase vernieuwen  
 Afbeelding 3 ziet u de hoge\-niveau processtroom voor de fase vernieuwen in in een takenreeks die is gemaakt met behulp van de gebruiker\-gebaseerde installatie Takenreeks taak sequence sjabloon.  

 ![UDI verwijzing 3](media/UDIReference3.jpg)  

 **Afbeelding SEQ afbeelding \\ \* ARABIC 3. Processtroom voor de fase vernieuwen**  

####  <a name="REPLACEandREPLACEWinPEStages"></a>VERVANGEN en vervangen. WinPE-fasen  
 Afbeelding 4 toont de hoge\-niveau processtroom voor de vervangen en vervangen. WinPE fasen in een takenreeks die is gemaakt met behulp van de gebruiker\-installatie vervangen Takenreeks aangestuurd taak sequence sjabloon.  

 ![UDI verwijzing 4](media/UDIReference4.jpg)  

 **Afbeelding 4. Processen stroom voor de vervangen en vervangen. WinPE-fasen**  

###  <a name="UDITaskReference"></a>UDI taak verwijzing  
 *UDI taken* is software die wordt uitgevoerd op een wizardpagina die specifieke functies uitvoeren. In sommige gevallen worden deze taken worden gebruikt om te controleren of de doelcomputer gereed is voor implementatie. Andere taken kunnen worden gebruikt om uit te voeren zoals het kopiëren van bestanden met configuration of het resultaat van de implementatiestappen.  

> [!NOTE]
>  De **volgende** knop op de wizardpagina waarin de taken worden uitgevoerd wordt uitgeschakeld als een van de taken met waarschuwing of fout voltooiingsstatus voltooien.  

 Deze naslaginformatie bevat:  

-   Een overzicht van UDI taken, zoals beschreven in [UDI taakoverzicht](#UDITaskOverview)  

-   Een beschrijving van de configuratie-instellingen voor UDI taken, zoals beschreven in [UDI taak configuratie-instellingen](#UDITaskConfigurationSettings)  

-   Een beschrijving van de ingebouwde\-in UDI validatiefuncties die worden geleverd met MDT, zoals beschreven in [ingebouwde\-in UDI taken](#BuiltinUDITasks)  

####  <a name="UDITaskOverview"></a>Overzicht van de taak UDI  
 UDI taken kunnen u software uitvoert op de doelcomputer die met het implementatieproces helpt. UDI bevat verschillende ingebouwde\-taken waarmee u algemene taken uitvoert, zoals ervoor te zorgen dat de doelcomputer wordt niet uitgevoerd op een accu werkt en is verbonden met een bekabeld netwerk in.  

 Naast de ingebouwde\-in UDI taken, kunt u aangepaste UDI taken met UDI software development kit \(SDK\). Zie voor meer informatie over het maken van aangepaste UDI taken met de SDK UDI *gebruiker\-installatiehandleiding ontwikkelaars aangestuurd*.  

####  <a name="UDITaskConfigurationSettings"></a>UDI taak configuratie-instellingen  
 U kunt taken met de waarde van de Wizard UDI beheren. U kunt taken toevoegen, verwijderen van taken en de configuratie van een taak in de waarde van de Wizard UDI bewerken. De configuratie-instellingen voor een taak in het configuratiebestand van de Wizard UDI worden opgeslagen en worden gelezen door de Wizard UDI wanneer de pagina van de wizard met de taak wordt weergegeven.  

 UTI taken zijn bepaalde configuratie-instellingen die gemeenschappelijk voor alle UDI taken, zijn zoals vermeld in de tabel 13. Voor de configuratie-instellingen die specifiek zijn voor elke taak UDI raadpleegt u de bijbehorende sectie in [ingebouwde\-in UDI taken](#BuiltinUDITasks).  

### <a name="table-13-configuration-settings-common-to-all-udi-tasks"></a>Tabel 13. Configuratie-instellingen gemeenschappelijke alle UDI taken  

|**Taak**|**Beschrijving**|  
|-|-|  
|**Bitmap-bestandsnaam**|Deze parameter bepaalt de afbeelding die wordt gebruikt om aan te geven van het taaktype.|  
|**Weergavenaam**|Hiermee geeft u de naam van de taak die wordt weergegeven op de wizardpagina wanneer de taak wordt uitgevoerd.|  
|**De waarden voor afsluiten**|Hiermee geeft u een lijst van mogelijke retourcodes voor de taak. Er bestaat een item in de lijst voor elke mogelijke retourcode.|  
|**Code foutwaarden**|Hiermee geeft u een lijst met mogelijke onverwachte uitzonderingen die u kunt tegenkomen \(veroorzaakt\) door de taak. Er bestaat een item in de lijst voor elke mogelijke uitzondering.|  

####  <a name="BuiltinUDITasks"></a>Ingebouwd\-in UDI taken  
 Tabel 14 geeft een lijst van de ingebouwde\-in UDI taken. Elk ingebouwd\-in UDI taak in een volgende sectie wordt besproken.  

### <a name="table-14-built-in-udi-tasks"></a>Tabel 14. Ingebouwd\-in UDI taken  

|**Taak**|**Beschrijving**|  
|-|-|  
|[Netstroom selectievakje](#ACPowerCheck)|Deze taak UDI wordt gebruikt om te bepalen of de doelcomputer is aangesloten op netstroom, niet uitsluitend op de accu werkt.|  
|[Toepassingsdetectie](#ApplicationDiscovery)|Deze taak UDI wordt gebruikt voor het detecteren van toepassingen die zijn geïnstalleerd op de doelcomputer.|  
|[CheckSMSFolderOnUSB](#CheckSMSFolderOnUSB)|Deze taak UDI wordt gebruikt om te bepalen of de \_SMSTaskSequence map bevindt zich op een USB-station op de doelcomputer.|  
|[Taak bestanden kopiëren](#CopyFilesTask)|Deze taak UDI wordt gebruikt om bestanden te kopiëren terwijl de Wizard UDI wordt uitgevoerd op de doelcomputer.|  
|[Shell taak uitvoeren](#ShellExecuteTask)|Deze taak UDI wordt gebruikt voor het uitvoeren van software die kan worden gestart vanaf een opdrachtregel.|  
|[Controle van bekabelde netwerken](#WiredNetworkCheck)|Deze taak UDI wordt gebruikt om te bepalen of de doelcomputer is verbonden met een bekabeld netwerk, niet verbonden met een draadloze netwerkverbinding.|  

#####  <a name="ACPowerCheck"></a>Netstroom selectievakje  
 Gebruik deze taak UDI om te bepalen of de doelcomputer op netstroom is aangesloten. Deze taak maakt gebruik van alleen die parameters die gemeenschappelijk zijn voor alle UDI taken. Zie voor meer informatie over deze parameters [UDI taak configuratie-instellingen](#UDITaskConfigurationSettings).  

 Tabel 15 bevat de fout en afsluiten codes die de **AC Power controleren** taak genereert.  

### <a name="table-15-error-and-exit-codes-for-the-ac-power-check-task"></a>Tabel 15. Fout- en afsluitcodes voor de netstroom controleren taak  

|**Afsluiten of foutcode**|**Waarde**|**Status**|  
|-|-|-|  
|Afsluiten|**0**|**Geslaagde**, wat aangeeft dat de doelcomputer is aangesloten op Netstroom zijn aangesloten|  
|Afsluiten|**\***|**Fout**, wat aangeeft dat de doelcomputer niet op netstroom is aangesloten|  

#####  <a name="ApplicationDiscovery"></a>Toepassingsdetectie  
 Gebruik deze taak UDI voor het detecteren van toepassingen die zijn geïnstalleerd op de doelcomputer.  

 Tabel 16 vindt u de parameters die de **Webtoepassingsdetectie** maakt gebruik van de taak.  

### <a name="table-16-parameters-used-by-the-application-discovery-task"></a>Tabel 16. Parameterverzameling die wordt gebruikt door de taak voor detectie van toepassing  

|**Taak**|**Beschrijving**|  
|-|-|  
|**Readcfg**|Deze parameter bepaalt het volledig gekwalificeerde of relatieve pad naar de locatie van het bestand .app met een lijst met toepassingen voor de taak te detecteren. Het bestand .app bevat de lijst met beschikbare software-items waarvan de gebruiker kan selecteren.<br /><br /> De **Webtoepassingsdetectie** taak leest het bestand .app en bepaalt of een van deze items software is geïnstalleerd. Als een software-item is geïnstalleerd, het item is toegevoegd aan het bestand dat is opgegeven in de **Writecfg** parameter.<br /><br /> Zorg ervoor dat deze parameter dezelfde locatie en naam als gebruikt de [ApplicationPage](#ApplicationPage) wizardpagina.|  
|**Writecfg**|Deze parameter bepaalt het volledig gekwalificeerde of relatieve pad naar de locatie van het .xml-bestand dat een lijst van de toepassingen die zijn gedetecteerd door de taak bevat.|  
|**Logboek**|Deze parameter bepaalt het volledig gekwalificeerde of relatieve pad naar de locatie van het logboekbestand gegenereerd door deze taak. De bestandsnaam van het logboekbestand is logbestanden AppDiscovery.log.|  

 Deze taak maakt gebruik van de parameters die gemeenschappelijk zijn voor alle UDI taken naast de parameters in de tabel 16. Zie voor meer informatie over deze algemene parameters [UDI taak configuratie-instellingen](#UDITaskConfigurationSettings).  

 Tabel 17 bevat de fout en afsluiten codes die de **Webtoepassingsdetectie** taak genereert.  

### <a name="table-17-error-and-exit-codes-for-the-application-discovery-task"></a>Tabel 17. Fout- en afsluitcodes voor de taak voor detectie van toepassing  

|**Afsluiten of foutcode**|**Waarde**|**Status en beschrijving**|  
|-|-|-|  
|Afsluiten|**0**|**Geslaagde**, wat aangeeft dat de taak met succes gescand voor toepassingen|  
|Afsluiten|**\***|**Waarschuwing**, wat aangeeft dat de toepassing detectie-engine kan niet worden uitgevoerd om onbekende reden|  
|Afsluiten|**1**|**Waarschuwing**, wat aangeeft dat de toepassing detectie-engine een of meer waarschuwingen opgetreden|  
|Afsluiten|**16777216**|**Waarschuwing**, wat aangeeft dat kritieke problemen zijn opgetreden tijdens het initialiseren van de toepassing detectie-engine|  
|Afsluiten|**33554432**|**Waarschuwing**, wat aangeeft dat kritieke problemen zijn opgetreden tijdens het verwerken van de toepassing master-lijst|  

#####  <a name="CheckSMSFolderOnUSB"></a>CheckSMSFolderOnUSB  
 Gebruik deze taak UDI om te identificeren of de \_SMSTaskSequence map bevindt zich op een USB-station op de doelcomputer. De Configuration Manager-taaksequencer worden standaard de \_SMSTaskSequence map op het station met de meeste beschikbare vrije schijfruimte. Dit kan problemen veroorzaken later in het implementatieproces als het USB-station wordt verwijderd.  

 Deze taak wordt gecontroleerd of de map bevindt zich op een USB-station en voorkomt u de implementatie doorgaat dat als is. Deze taak maakt gebruik van alleen die parameters die gemeenschappelijk zijn voor alle UDI taken. Zie voor meer informatie over deze parameters [UDI taak configuratie-instellingen](#UDITaskConfigurationSettings).  

 Als de \_SMSTaskSequence map bevindt zich op een USB-station, wordt deze taak is mislukt en wordt voorkomen dat de implementatie niet door kan gaan. U kunt dit probleem oplossen en de implementatie uitvoert, moet u de volgende stappen uitvoeren:  

1.  Moet het USB-station van de doelcomputer voordat de takenreeks wordt gestart.  

2.  Start de takenreeks.  

3.  Wacht totdat de Wizard UDI wordt gestart.  

4.  Verbinding maken met het USB-station.  

5.  Voltooi de Wizard UDI.  

 Tabel 18 bevat de fout en afsluiten codes die de **CheckSMSFolderOnUSB** taak genereert.  

### <a name="table-18-error-and-exit-codes-for-the-checksmsfolderonusb-task"></a>Tabel 18. Fout- en afsluitcodes voor de taak CheckSMSFolderOnUSB  

|**Afsluiten of foutcode**|**Waarde**|**Status**|  
|-|-|-|  
|Afsluiten|**0**|**Geslaagde**, wat aangeeft dat de \_SMSTaskSequence map bevindt zich niet op een USB-station en de implementatie te kunnen voortzetten.|  
|Afsluiten|**\***|**Fout**, wat aangeeft dat de \_SMSTaskSequence map bevindt zich op een USB-station en de implementatie kan niet worden voortgezet.|  

#####  <a name="CopyFilesTask"></a>Taak bestanden kopiëren  
 Gebruik deze taak UDI om bestanden te kopiëren terwijl de Wizard UDI wordt uitgevoerd op de doelcomputer.  

 Tabel 19 vindt u de parameters die de **bestanden kopiëren** maakt gebruik van de taak.  

### <a name="table-19-parameters-used-by-the-copy-files-task"></a>Tabel 19. Parameterverzameling die wordt gebruikt door de taak van de bestanden kopiëren  

|**Taak**|**Beschrijving**|  
|-|-|  
|**Bron**|Deze parameter bepaalt het volledig gekwalificeerde of relatieve pad naar het bronbestand met jokertekens om meerdere bestanden met behulp van een enkele taak te kopiëren.|  
|**Bestemming**|Deze parameter bepaalt het volledig gekwalificeerde of relatieve pad naar het doelbestand zonder een bestandsnaam op.|  

 Deze taak maakt gebruik van parameters die gemeenschappelijk zijn voor alle UDI taken naast de parameters in de tabel 19. Zie voor meer informatie over deze parameters [UDI taak configuratie-instellingen](#UDITaskConfigurationSettings).  

 Tabel 20 bevat de fout en afsluiten codes die de **bestanden kopiëren** taak genereert.  

### <a name="table-20-error-and-exit-codes-for-the-copy-files-task"></a>Tabel 20. Fout- en afsluitcodes voor de taak van de bestanden kopiëren  

|**Afsluiten of foutcode**|**Waarde**|**Status en beschrijving**|  
|-|-|-|  
|Afsluiten|**0**|**Geslaagde**, wat aangeeft dat het kopieerproces is mislukt|  
|Afsluiten|**\***|**Fout**, wat aangeeft dat het kopieerproces is mislukt|  
|Fout|**\-1**|**Fout**, wat aangeeft dat het kopieerproces is mislukt|  

#####  <a name="ShellExecuteTask"></a>Shell taak uitvoeren  
 Gebruik deze taak UDI software die kan worden gestart vanaf een opdrachtregel uitvoeren.  

 Tabel 21 vindt u de parameters die de **Shell uitvoeren** maakt gebruik van de taak.  

### <a name="table-21-parameters-used-by-the-shell-execute-task"></a>Tabel 21. Parameterverzameling die wordt gebruikt door de taak voor het uitvoeren van Shell  

|**Taak**|**Beschrijving**|  
|-|-|  
|**Bestandsnaam**|Deze parameter bepaalt de volledig gekwalificeerde of relatieve pad naar de opdracht voor de taak wilt uitvoeren.|  
|**Parameters**|Deze parameter geeft u de opdracht\-regel parameters die moeten worden opgegeven bij de opdracht uit te voeren.|  

 Deze taak maakt gebruik van parameters die gemeenschappelijk zijn voor alle UDI taken naast de parameters in tabel 21. Zie voor meer informatie over deze parameters [UDI taak configuratie-instellingen](#UDITaskConfigurationSettings).  

 U kunt ook aangepaste Visual Basic-scripts ontworpen om te worden uitgevoerd met de cscript.exe uitvoeren de **Shell uitvoeren** taak. Als u wilt uitvoeren in Visual Basic-scripts, kunt u de volgende stappen uitvoeren:  

1.  Typ de volgende tekst in de **Filename** parameter:  

    ```  
    %windir%\system32\cscript.exe  
    ```  

2.  De typenaam van de Visual Basic-scriptbestand \(.vbs-bestand\) in de **Parameters** parameter, met inbegrip van elke opdracht\-regel parameters voor het script.  

     Bijvoorbeeld, een Visual Basic-script uit te voeren met de naam *SelfTest.vbs* met een parameterwaarde van **Debug**, typt u het volgende \(waar *script\_pad*is het volledig gekwalificeerde pad naar het bestand SelfTest.vbs\):  

    ```  
    <script_path>\SelfTest.vbs Debug  
    ```  

 Tabel 22 bevat de algemene fout en afsluiten codes die de **Shell uitvoeren** taak genereert.  

> [!NOTE]
>  Elke specifieke taak op basis van de **Shell uitvoeren** taak heeft een unieke set van fout naar en uitgang codes. Controleer of de retourcodes voor de software die u uitvoert met behulp van deze taak.  

### <a name="table-22-common-error-and-exit-codes-for-the-shell-execute-task"></a>Tabel 22. Algemene fout- en afsluitcodes voor de Shell Execute-taak  

|**Afsluiten of foutcode**|**Waarde**|**Status en beschrijving**|  
|-|-|-|  
|Afsluiten|**0**|**Geslaagde**, wat aangeeft dat de taak voltooid is|  
|Afsluiten|**\***|**Fout**, wat aangeeft dat de taak is mislukt|  

#####  <a name="WiredNetworkCheck"></a>Controle van bekabelde netwerken  
 Gebruik deze taak UDI om te bepalen of de doelcomputer is verbonden met een bekabeld netwerk, niet via een draadloze netwerkverbinding. Deze taak wordt alleen gebruikt voor parameters die gemeenschappelijk zijn voor alle UDI taken. Zie voor meer informatie over deze parameters [UDI taak configuratie-instellingen](#UDITaskConfigurationSettings).  

 Tabel 23 bevat de algemene fout en afsluiten codes die de **bekabelde netwerk controleren** taak genereert.  

### <a name="table-23-error-and-exit-codes-for-the-wired-network-check-task"></a>Tabel 23. Fout- en afsluitcodes voor het bekabelde netwerk controleren taak  

|**Afsluiten of foutcode**|**Waarde**|**Status en beschrijving**|  
|-|-|-|  
|Afsluiten|**0**|**Geslaagde**, wat aangeeft dat de doelcomputer is verbonden met een bekabeld netwerk|  
|Afsluiten|**\***|**Fout**, wat aangeeft dat de doelcomputer niet is verbonden met een bekabeld netwerk|  

###  <a name="UDIValidatorReference"></a>UDI Validator verwijzing  
 UDI validatiefuncties worden gebruikt voor het valideren van de waarden die zijn opgegeven in de tekstvelden op de wizardpagina's. Wanneer een validatiefunctie UDI een ongeldige waarde detecteert, wordt een bericht weergegeven voor de eerste fout aan de onderkant van de wizardpagina. Het volgende foutbericht, wordt indien aanwezig, weergegeven nadat u de eerste validatiefout opgelost. Dit proces wordt voortgezet totdat alle validatiefouten zijn opgelost. De **volgende** knop blijft uitgeschakeld totdat alle validatiefouten op de wizardpagina opgelost zijn.  

 Deze naslaginformatie bevat:  

-   Een overzicht van UDI validatiefuncties, zoals beschreven in [UDI Validator overzicht](#UDIValidatorOverview)  

-   Een beschrijving van de ingebouwde\-in UDI validatiefuncties geleverd met MDT, zoals beschreven in [ingebouwde\-in UDI validatiefuncties](#BuiltinUDIValidators)  

####  <a name="UDIValidatorOverview"></a>Overzicht van de validatiefunctie UDI  
 UDI validatiefuncties worden gebruikt om ervoor te zorgen dat gebruikers de juiste gegevens in de tekstvelden op wizardpagina's in de Wizard UDI bieden. UDI bevat verschillende ingebouwde\-in validatiefuncties die help uitvoeren van typische validaties van de velden die worden gebruikt voor het invoeren van tekst, zoals voorkomen dat gebruikers voeren ongeldige tekens of ervoor zorgen dat het veld niet leeg.  

 Naast de ingebouwde\-in UDI validatiefuncties, kunt u aangepaste UDI validatiefuncties met behulp van de SDK UDI. Zie voor meer informatie over het maken van aangepaste UDI validatiefuncties met behulp van de SDK UDI het document MDT *gebruiker\-installatiehandleiding ontwikkelaars aangestuurd*.  

####  <a name="BuiltinUDIValidators"></a>Ingebouwde UDI validatiefuncties  
 Tabel 24 geeft een lijst van de ingebouwde UDI validatiefuncties. Elke ingebouwde validator wordt in een volgende sectie beschreven. Wanneer een validatie van een ongeldige waarde in het tekstvak detecteert, wordt een bericht weergegeven op de wizardpagina en de **volgende** knop blijft uitgeschakeld totdat alle ongeldige vermeldingen opgelost zijn.  

### <a name="table-24-built-in-udi-validators"></a>Tabel 24. Ingebouwde UDI validatiefuncties  

|**Validator**|**Beschrijving**|  
|-|-|  
|[%{Invalidchars/](#InvalidChars)|Deze validatiefunctie identificeert ongeldige tekens bevat die zijn ingevoerd in een lijst die u configureert.|  
|[NamedPattern](#NamedPattern)|Deze validatiefunctie zorgt ervoor dat de tekst een vooraf gedefinieerde patroon heeft.|  
|[NonEmpty](#NonEmpty)|Deze validatiefunctie wordt gebruikt om tekst in een veld is vereist.|  
|[Reguliere expressie](#RegEx)|Deze validatiefunctie kunt dat u ervoor zorgen dat de tekst die overeenkomt met een reguliere expressie die u als onderdeel van de validatiefunctie opgeeft.|  

#####  <a name="InvalidChars"></a>%{Invalidchars/  
 Deze validatiefunctie wordt voorkomen dat gebruikers bepaalde tekens invoeren. De **bericht** vak kunt u een bericht dat wordt weergegeven als het tekstveld de ongeldige tekens bevat. De **ongeldige tekens** vak kunt u de tekens die ongeldig worden beschouwd. De tekens worden ingevoerd zonder spaties ertussen.  

#####  <a name="NamedPattern"></a>NamedPattern  
 Deze validatiefunctie zorgt ervoor dat de tekst een vooraf gedefinieerde patroon heeft. De **bericht** vak kunt u een bericht dat wordt weergegeven als het tekstveld komt niet overeen met het benoemde patroon invoeren. De **patroon met de naam** vak kunt u de naam van de vooraf gedefinieerde patroon invoeren en moet **gebruikersnaam**, **ComputerName**, of **werkgroep**.  De namen zijn niet hoofdlettergevoelig.  

#####  <a name="NonEmpty"></a>NonEmpty  
 Deze validatiefunctie gebruiken om te vereisen van tekst in een veld. De **bericht** vak kunt u een bericht dat wordt weergegeven als het veld leeg is.  

#####  <a name="RegEx"></a>Reguliere expressie  
 Deze validatiefunctie kunt dat u ervoor zorgen dat de tekst die overeenkomt met een reguliere expressie die u als onderdeel van de validatiefunctie opgeeft. De **bericht** vak kunt u een bericht dat wordt weergegeven als het tekstveld komt niet overeen met de reguliere expressie invoeren. De **reguliere expressie** vak kunt u de reguliere expressie voor de validatie invoeren. Zie voor meer informatie over het bouwen van reguliere expressies voor deze validatiefunctie [TR1 reguliere expressies](http://msdn.microsoft.com/library/bb982727.aspx).  

###  <a name="UDIWizardPageReference"></a>Controle van paginaverwijzing Wizard UDI  
 Toevoegen van een UDI [wizardpagina](#WizardPage) op stadia van de [pagina bibliotheek](#PageLibrary) in de [de Wizard UDI](#UDIWizardDesigner). UDI wizardpagina's worden weergegeven de [Wizard UDI](#UDIWizard).  

 Deze naslaginformatie bevat:  

-   Een overzicht van UDI wizardpagina's, zoals beschreven in [UDI Wizard pagina overzicht](#UDIWizardPageOverview)  

-   Een beschrijving van de ingebouwde UDI wizardpagina's die worden geleverd met MDT, zoals beschreven in [ingebouwde UDI wizardpagina's](#BuiltinUDIWizardPages)  

####  <a name="UDIWizardPageOverview"></a>Overzicht van pagina Wizard UDI  
 Wizardpagina's worden weergegeven de [Wizard UDI](#UDIWizard) en verzamelen van de informatie die is vereist voor het voltooien van het implementatieproces. U maken wizardpagina's met C++ in Visual Studio. De aangepaste wizardpagina's worden geïmplementeerd als dll-bestanden in de Wizard UDI leest.  

 Elke ingebouwde pagina van de wizard UDI heeft een bijbehorende UDI [wizard pagina editor](#WizardPageEditor), waarmee u instellingen op de wizardpagina in de [de Wizard UDI](#UDIWizardDesigner).  

 Naast de ingebouwde UDI wizardpagina's kunt u aangepaste UDI wizardpagina's met de SDK UDI. Zie voor meer informatie over het maken van aangepaste UDI wizardpagina's met de SDK UDI het document MDT *Driven installatie-handleiding voor ontwikkelaars*.  

 Elke pagina van de wizard kan verwijzen naar de volgende typen variabelen:  

-   Takenreeksvariabelen  

-   Geheugenvariabelen  

-   Omgevingsvariabelen  

 U kunt verwijzen naar takenreeks en omgevingsvariabelen door de variabele procenttekens (%), met verschillende aantallen zoals *% OSDImageIndex %.* U kunt verwijst naar geheugenvariabelen met de variabele dollartekens ($), met verschillende aantallen zoals *$VolumeArchitecture$.*  

> [!NOTE]
>  Als een takenreeksvariabele en een omgevingsvariabele hebben beide dezelfde naam, en vervolgens de takenreeksvariabele voorrang op de omgevingsvariabele heeft.  

 Tabel 25 geeft een lijst van de geheugenvariabelen die zijn ingesteld wanneer de Wizard UDI wordt gestart, de beschrijving van de variabelen en of de Wizard UDI leest of schrijft de variabelen tijdens het opstarten.  

### <a name="table-25-memory-variables-set-by-the-udi-wizard-at-startup-and-their-descriptions"></a>Tabel 25. Geheugenvariabelen die zijn ingesteld door de Wizard UDI bij het opstarten en de bijbehorende beschrijvingen  

|**Variabele**|**Lezen**|**Schrijven**|  
|-|-|-|  
|**LogPath**<br /><br /> Hiermee geeft u de volledig gekwalificeerde pad naar de logboekbestanden voor de Wizard UDI. U kunt deze variabele instellen op een van de volgende waarden:<br /><br /> -De waarde in de **_SMSTSLogPath** takenreeksvariabele<br /><br /> -De waarde van de % TEMP % omgeving variabele als de **_SMSTSLogPath** takenreeksvariabele is niet ingesteld.|Nee|Ja|  
|**WizardConfigFilename**<br /><br /> Geeft de naam van het configuratiebestand van de Wizard UDI momenteel in gebruik. De **ApplicationPage** wizardpagina leest de waarde van deze variabele het bijbehorende .app-bestand waarin de lijst met toepassingen te vinden. Bijvoorbeeld, als de naam van het configuratiebestand van de Wizard UDI *config.xml,* en vervolgens de wizardpagina naar het bijbehorende .app-bestand (config.xml.app zoekt).|Nee|Ja|  

####  <a name="BuiltinUDIWizardPages"></a>Ingebouwde UDI wizardpagina 's  
 Tabel 26 geeft een lijst van de ingebouwde UDI wizardpagina's. Elke ingebouwde pagina van de wizard UDI wordt in een volgende sectie beschreven.  

### <a name="table-26-built-in-wizard-pages-and-their-descriptions"></a>Tabel 26. Ingebouwde wizardpagina's en de bijbehorende beschrijvingen  

|**Pagina van wizard**|**Beschrijving**|  
|-|-|  
|[AdminAccounts](#AdminAccounts)|Gebruik deze wizardpagina voor het instellen van het wachtwoord voor het lokale beheerdersaccount en andere gebruikers toevoegen aan de lokale groep Administrators op de doelcomputer.|  
|[ApplicationPage](#ApplicationPage)|Gebruik deze wizardpagina voor het configureren van de lijst met toepassingen die kunnen worden geïnstalleerd tijdens de installatie. Deze toepassingen kunnen opnemen toepassingen of pakketten en programma's van Configuration Manager.|  
|[BitLockerPage](#BitLockerPage)|Gebruik deze wizardpagina BitLocker-instellingen configureren voor de doelcomputer.|  
|[ComputerPage](#ComputerPage)|Gebruik deze wizardpagina voor het configureren van de computernaam van de doelcomputer, het domein of werkgroep en de referenties worden gebruikt als lid van een domein.|  
|[ConfigScanPage](#ConfigScanPage)|Gebruik deze wizardpagina UDI taken die de configuratie van de doelcomputer om te bepalen of de doelcomputer gereed is voor de implementatie van de besturingssysteemkopie scannen uitvoeren. Deze gereedheid omvat die voldoende systeembronnen heeft en ervoor te zorgen dat alle vereiste software is geïnstalleerd en correct is geconfigureerd.|  
|[LanguagePage](#LanguagePage)|Gebruik deze pagina van de wizard om te bepalen welke taalpakket moet worden geïnstalleerd, de standaardtaal voor het beoogde besturingssysteem, de landinstellingen van het toetsenbord en de tijdzone waarin de computer zich fysiek bevinden.|  
|[ProgressPage](#ProgressPage)|Gebruik deze wizardpagina UDI taken die de gebruikersstatusgegevens voor migratie van de doelcomputer vastlegt uitvoeren.|  
|[RebootPage](#RebootPage)|Gebruik deze wizardpagina melding verzenden naar de gebruiker die de doelcomputer opnieuw worden opgestart. U kunt het meldingsbericht met behulp van de waarde van de Wizard UDI configureren.|  
|[Overzichtspagina](#RebootPage)|Gebruik deze wizardpagina melding verzenden naar de gebruiker over de configuratieopties die zijn geselecteerd tijdens het uitvoeren van de Wizard UDI. De configuratie-informatie weergegeven op deze wizardpagina worden automatisch verzameld uit andere wizardpagina's. Sommige velden op andere wizardpagina's kunnen u het bijschrift (label) wordt weergegeven op deze wizardpagina met behulp van de waarde van de Wizard UDI configureren.|  
|[UDAPage](#UDAPage)|Gebruik deze wizardpagina voor het configureren van de UDA tussen de doelcomputer en een opgegeven gebruiker. Affiniteit tussen een computer en een gebruiker definiëren, kunt automatische installatie van software die is geïmplementeerd op een gebruiker. De UDA-functie is alleen beschikbaar in Configuration Manager en in het scenario voor de nieuwe Computer UDI.|  
|[UserStatePage](#UserStatePage)|Gebruik deze wizardpagina voor het configureren van de instellingen voor het vastleggen of herstellen van gegevens van de migratie van gebruikersstatus. Deze pagina van de wizard kan de gebruiker te selecteren van de locatie van de migratie van gebruikersstatus te leggen of te herstellen van gebruikersstatusgegevens voor migratie van.|  
|[VolumePage](#VolumePage)|Gebruik deze wizardpagina voor het configureren van de instellingen voor het schijfvolume op de doelcomputer waarop het besturingssysteem wordt geïmplementeerd. Deze instellingen omvatten het doelbesturingssysteem selecteren, selecteert het doelstation selecteren van een Windows-installatie en te bepalen of het doelstation worden opgemaakt als een deel van het implementatieproces.|  
|[WelcomePage](#WelcomePage)|Gebruik deze wizardpagina informatie opgeven voor de gebruiker over de Wizard UDI en het implementatieproces. U kunt het meldingsbericht met behulp van de waarde van de Wizard UDI configureren.|  

#####  <a name="AdminAccounts"></a>AdminAccounts  
 Gebruik deze wizardpagina voor het wachtwoord voor het lokale administrator-account instellen en andere gebruiker toevoegen aan de lokale groep Administrators op de doelcomputer.  

###### <a name="task-sequence-variables"></a>Takenreeksvariabelen  
 Tabel 27 bevat de **AdminAccounts** takenreeksvariabelen met de beschrijving en bepaalt of de variabele kan worden gelezen door de wizardpagina geschreven door de wizardpagina of kan worden geconfigureerd in het configuratiebestand van de Wizard UDI.  

### <a name="table-27-adminaccounts-task-sequence-variables"></a>Tabel 27. Takenreeksvariabelen AdminAccounts  

|**Variabele**|**Lezen**|**Schrijven**|**Configuratie**|  
|-|-|-|-|  
|**OSDAddAdmin**<br /><br /> Hiermee geeft u een lijst met aanvullende gebruikersnamen worden toegevoegd aan de lokale groep Administrators op de doelcomputer.|Ja|Ja|Ja|  
|**OSDLocalAdminPassword**<br /><br /> Hiermee geeft u de wachtwoorden voor het ingebouwde lokale beheerdersaccount op de doelcomputer.|Ja|Ja|Ja|  

#####  <a name="ApplicationPage"></a>ApplicationPage  
 Gebruik deze wizardpagina voor het configureren van de lijst met toepassingen die kan worden geïnstalleerd tijdens de installatie. Deze toepassingen kunnen opnemen toepassingen of pakketten en programma's van Configuration Manager.  

> [!NOTE]
>  Als toepassingen weergegeven worden uitgeschakeld, wordt de toepassing mogelijk goedkeuring door beheerder vereisen maar nog niet is goedgekeurd. Als de **goedkeuring door beheerder vereisen als gebruikers deze toepassing aanvragen** selectievakje is ingeschakeld voor de toepassing, controleert u of de toepassing is goedgekeurd. Zie voor meer informatie [toepassingen implementeren in Configuration Manager](http://technet.microsoft.com/library/gg682082.aspx).  

###### <a name="task-sequence-variables"></a>Takenreeksvariabelen  
 Geeft een lijst van tabel 28 de **ApplicationPage** takenreeksvariabelen met de beschrijving en de variabele kan worden gelezen door de wizardpagina geschreven door de wizardpagina of kan worden geconfigureerd in het configuratiebestand van de Wizard UDI.  

### <a name="table-28-applicationpage-task-sequence-variables"></a>Tabel 28. Takenreeksvariabelen ApplicationPage  

|**Variabele**|**Lezen**|**Schrijven**|**Configuratie**|  
|-|-|-|-|  
|**ApplicationBaseVariable**<br /><br /> Hiermee geeft u de naam gebruikt als basis voor de namen van takenreeksvariabelen gemaakt voor elke Configuration Manager-toepassing hebt geselecteerd op de **ApplicationPage** wizardpagina. Deze variabele is geconfigureerd met behulp van de **Software-instellingen bewerken** knop in de **instellingen bewerken** groep in het lint in de waarde van de Wizard UDI.<br /><br /> Een afzonderlijke takenreeksvariabele wordt gemaakt voor elke toepassing die op deze pagina hebt geselecteerd. De standaardwaarde voor deze variabele is **toepassingen**. Ja, bijvoorbeeld de namen van de taak takenreeksvariabelen gemaakt voor elke toepassing die op deze pagina hebt geselecteerd wordt *APPLICATIONS001, APPLICATIONS002, APPLICATIONS003,* enzovoort.|Nee|Ja|Ja|  
|**OSDApplicationList**<br /><br /> Hiermee geeft u de lijst met de toepassing-id's die in eerste instantie moet worden geselecteerd. De variabele bevat een lijst met numerieke waarden, gescheiden door puntkomma's (;).<br /><br /> De aanvraag-id's zijn gevonden in de **Id** kenmerk van de **toepassing** element in het configuratiebestand van de Wizard UDI (UDIWizard_Config.xml.app). Er is een afzonderlijke **toepassing** element voor elke toepassing die wordt weergegeven op deze wizardpagina.|Ja|Nee|Nee|  
|**OSDArchitecture**<br /><br /> Hiermee geeft u de processorarchitectuur van de doelcomputer. De **ApplicationPage** pagina van de wizard maakt gebruik van deze variabele voor het filteren van de beschikbare toepassingen wanneer de **VolumeArchitecture** geheugen variabele is niet ingesteld. Echter, als de **VolumeArchitecture** geheugen variabele is ingesteld en deze altijd voorrang op de takenreeksvariabele voor het filteren van de beschikbare toepassingen.<br /><br /> De waarde voor deze variabele kan zijn:<br /><br /> -                                      **x86**, wat aangeeft dat een 32-bits processor-architectuur<br /><br /> -                                      **AMD64**, wat aangeeft dat een 64-bits processor-architectuur|Ja|Nee|Nee|  
|**OSDBaseVariableName**<br /><br /> Hiermee geeft u de naam gebruikt als basis voor de namen van takenreeksvariabelen gemaakt voor elke Configuration Manager-pakket en programma dat is geselecteerd op de **ApplicationPage** wizardpagina. Deze variabele is geconfigureerd met behulp van de **Software-instellingen bewerken** knop in de **gedrag** groep in het lint in de waarde van de Wizard UDI.<br /><br /> Een afzonderlijke takenreeksvariabele wordt gemaakt voor elke toepassing die op deze pagina hebt geselecteerd. De standaardwaarde voor deze variabele is **PAKKETTEN**. Ja, bijvoorbeeld de namen van de taak takenreeksvariabelen gemaakt voor elke toepassing die op deze pagina hebt geselecteerd wordt *PACKAGES001, PACKAGES002, PACKAGES003,* enzovoort.|Nee|Ja|Ja|  

##### <a name="memory-variables"></a>Geheugenvariabelen  
 Geeft een lijst van tabel 29 de **ApplicationPage** geheugenvariabelen met de beschrijving en of de variabele is gelezen of door de wizardpagina geschreven.  

### <a name="table-29-applicationpage-memory-variables"></a>Tabel 29. Variabelen ApplicationPage geheugen  

|**Variabele**|**Lezen**|**Schrijven**|  
|-|-|-|  
|**VolumeArchitecture**<br /><br /> Hiermee geeft u de processorarchitectuur van de doel-besturingssysteeminstallatiekopie (of de afbeelding een 32-bits of 64-bits besturingssysteem bevat) worden geïmplementeerd. Wanneer deze pagina wordt weergegeven, wordt gecontroleerd of deze variabele is gewijzigd. Als de variabele is gewijzigd sinds de laatste keer dat de wizardpagina worden weergegeven, filtert de wizardpagina de programma's die beschikbaar zijn voor selectie op basis van de architectuur van het beoogde besturingssysteem. Bijvoorbeeld, als een 32-bits besturingssysteem wordt geïmplementeerd, wordt de wizardpagina verwijderd (filters) 64-bits toepassingen uit de lijst met beschikbare toepassingen op de wizardpagina.|Ja|Nee|  
|**WizardConfigFilename**<br /><br /> Geeft de naam van het configuratiebestand van de Wizard UDI momenteel in gebruik. Als de waarde van de **Link.Uri** setter-eigenschap is leeg, de **ApplicationPage** wizardpagina leest de waarde van deze variabele het bijbehorende .app-bestand waarin de lijst met toepassingen te vinden. Bijvoorbeeld, als de naam van het configuratiebestand van de Wizard UDI *config.xml,* en vervolgens de wizardpagina naar het bijbehorende .app-bestand (config.xml.app zoekt). Deze variabele wordt ingesteld wanneer de Wizard UDI wordt gestart.<br /><br /> De **Link.Uri** setter-eigenschap is ingesteld op de **Software-instellingen** in het dialoogvenster die kan worden geopend met behulp van de **Software-instellingen bewerken** knop in de **pagina Gedrag** groep in het lint in de waarde van de Wizard UDI.|Ja|Nee|  

#####  <a name="BitLockerPage"></a>BitLockerPage  
 Deze pagina van de wizard wordt gebruikt om BitLocker-instellingen voor de doelcomputer te configureren.  

###### <a name="task-sequence-variables"></a>Takenreeksvariabelen  
 Tabel 30 geeft een lijst van de BitLockerPage takenreeksvariabelen met een beschrijving en de variabele kan worden gelezen door de wizardpagina geschreven door de wizardpagina of kan worden geconfigureerd in het configuratiebestand van de Wizard UDI.  

### <a name="table-30-bitlockerpage-task-sequence-variables"></a>Tabel 30. Takenreeksvariabelen BitLockerPage  

|**Variabele**|**Lezen**|**Schrijven**|**Configuratie**|  
|-|-|-|-|  
|**BDEInstallSuppress**<br /><br /> Hiermee geeft u op of de installatie van BitLocker moet worden onderdrukt. Als de variabele is ingesteld op:<br /><br /> - **Ja**, wordt de **BitLocker inschakelen** selectievakje is ingeschakeld en de installatie wordt uitgevoerd<br /><br /> - **GEEN**, wordt de **BitLocker inschakelen** selectievakje is uitgeschakeld en de installatie wordt niet uitgevoerd|Ja|Ja|Ja|  
|**BDEKeyLocation**<br /><br /> Hiermee geeft u de volledig gekwalificeerde pad naar de locatie waar de BitLocker-versleutelingssleutels zijn opgeslagen, wat kan een lokale of een UNC-pad zijn. Deze variabele is ingesteld op de waarde van de **KeyLocation** setter-waarde in het configuratiebestand van de Wizard UDI voor de **BitLockerPage**. Deze variabele wordt alleen als geldig beschouwd wanneer de **OSDBitLockerMode** is ingesteld op **TPMKEY** of **sleutel**.|Nee|Ja|Nee|  
|**BDEPin**<br /><br /> Geeft de BitLocker-PINCODE-waarde als de **BitLocker inschakelen met behulp van de TPM en pincode** optie is geselecteerd.|Ja|Ja|Ja|  
|**OSDBitLockerCreateRecoveryPassword**<br /><br /> Hiermee geeft u op of een BitLocker-herstelwachtwoord moet worden opgeslagen in AD DS. Als de variabele is ingesteld op:<br /><br /> -                                      **AD**, wordt de **In Active Directory** optie is geselecteerd en de herstelsleutel worden opgeslagen in AD DS (aanbevolen)<br /><br /> - **GEEN**, wordt de **Maak geen een herstelsleutel** optie is geselecteerd en de herstelsleutels niet worden opgeslagen in AD DS (niet aanbevolen)|Nee|Ja|Nee|  
|**OSDBitLockerMode**<br /><br /> Hiermee wordt de modus moet worden gebruikt wanneer u BitLocker inschakelt op de doelcomputer. Geldige waarden zijn:<br /><br /> -                                      **TPM.** Deze waarde geeft aan dat de **BitLocker inschakelen met alleen TPM** optie is geselecteerd en dat alleen TPM worden gebruikt wanneer u BitLocker inschakelt op de doelcomputer.<br /><br /> -                                      **TPMPIN.** Deze waarde geeft aan dat de **BitLocker inschakelen met behulp van de TPM en pincode** optie is geselecteerd en dat TPM en een gebruiker opgegeven PINCODE wordt gebruikt wanneer u BitLocker inschakelt op de doelcomputer.<br /><br /> -                                      **TPMKEY.** Deze waarde geeft aan dat de **BitLocker inschakelen met behulp van de TPM en opstartsleutel** optie is geselecteerd en dat TPM en een opstartsleutel worden gebruikt wanneer u BitLocker inschakelt op de doelcomputer.<br /><br /> - **SLEUTEL.** Deze waarde geeft aan dat de **BitLocker inschakelen met behulp van een externe opstartsleutel** optie is geselecteerd en dat een externe opstartsleutel wordt gebruikt wanneer u BitLocker inschakelt op de doelcomputer.|Nee|Ja|Nee|  
|**OSDBitLockerStartupKeyDrive**<br /><br /> Hiermee geeft u de stationsletter waarin het externe BitLocker-opstartsleutel wordt opgeslagen op de doelcomputer. Deze variabele wordt alleen als geldig beschouwd wanneer **OSDBitLockerMode** is ingesteld op **TPMKEY** of **sleutel**.|Nee|Ja|Nee|  
|**OSDBitLockerWaitForEncryption**<br /><br /> Hiermee geeft u op of de takenreeks wachten moet totdat BitLocker-versleuteling is voltooid. Als de variabele is ingesteld op:<br /><br /> -                                      **Ja**, wordt de **wacht totdat BitLocker-versleuteling voltooid voor alle stations voordat u doorgaat** selectievakje is ingeschakeld en de takenreeks wacht totdat de installatie voltooid is<br /><br /> -                                      **GEEN**, wordt de **wacht totdat BitLocker-versleuteling voltooid voor alle stations voordat u doorgaat** selectievakje is uitgeschakeld en de takenreeks wacht niet totdat de installatie voltooid is|Ja|Ja|Ja|  

###### <a name="configuration-variables"></a>Configuratievariabelen voor de  
 Geeft een lijst van tabel 31 de **BitLockerPage** configuratievariabelen met een beschrijving en de variabele kan worden gelezen door de wizardpagina geschreven door de wizardpagina of kan worden geconfigureerd in het configuratiebestand van de Wizard UDI.  

### <a name="table-31-bitlockerpage-configuration-variables"></a>Tabel 31. De variabelen BitLockerPage  

|**Variabele**|**Lezen**|**Schrijven**|**Configuratie**|  
|-|-|-|-|  
|**KeyLocation**<br /><br /> Hiermee geeft u de volledig gekwalificeerde pad naar de locatie waar de BitLocker-versleutelingssleutels zijn opgeslagen, wat kan een lokale of een UNC-pad zijn. Deze configuratiewaarde gebruikt voor het instellen van de waarde van de **BDEKeyLocation** takenreeksvariabele voor de **BitLockerPage**. Deze variabele wordt alleen als geldig beschouwd wanneer **OSDBitLockerMode** is ingesteld op **TPMKEY** of **sleutel**.|Ja|Nee|Ja|  

#####  <a name="ComputerPage"></a>ComputerPage  
 Gebruik deze wizardpagina voor het configureren van de computernaam van de doelcomputer, het domein of werkgroep en de referenties die worden gebruikt bij het koppelen van een domein. Wanneer u deze pagina om de doelcomputer koppelt aan een domein configureert, wordt deze pagina van de wizard de referenties die u opgeeft voor het lidmaatschap van het domein in AD DS standaard valideren. Deze pagina van de wizard probeert vervolgens te wijzigen van een computerobject in AD DS om te controleren of de referenties van de gebruiker op deze pagina opgegeven machtigingen maken of wijzigen van het computerobject hebt. U kunt een van deze problemen kunt uitschakelen. Als u de validatie van de referenties uitschakelt, is ook de controle van machtigingen voor het maken of wijzigen van computerobjecten uitgeschakeld. Beide van deze validaties optreden wanneer de **volgende** knop wordt geklikt. Als een van de validaties er een fout optreedt, wordt een foutbericht wordt weergegeven en wordt deze pagina blijft moet worden weergegeven.  

 Hier volgt de volgorde van prioriteit voor het bepalen van de standaardnaam van de computer:  

1.  Als de **UserExistingComputerName** waarde in het configuratiebestand van de Wizard UDI is ingesteld op **TRUE**, wordt de naam van de bestaande computer gebruikt \(indien aanwezig\).  

2.  Als de **OSDComputerName** takenreeksvariabele is ingesteld, wordt de computernaam van de in deze variabele wordt gebruikt.  

3.  Als een standaardwaarde voor de naam van de computer in het configuratiebestand van de Wizard UDI is opgegeven, wordt die waarde gebruikt.  

###### <a name="task-sequence-variables"></a>Takenreeksvariabelen  
 Geeft een lijst van tabel 32 de **ComputerPage** takenreeksvariabelen met een beschrijving en de variabele kan worden gelezen door de wizardpagina geschreven door de wizardpagina of kan worden geconfigureerd in het configuratiebestand van de Wizard UDI.  

### <a name="table-32-computerpage-task-sequence-variables"></a>Tabel 32. Takenreeksvariabelen ComputerPage  

|**Variabele**|**Lezen**|**Schrijven**|**Configuratie**|  
|-|-|-|-|  
|**OSDComputerName**<br /><br /> Hiermee geeft u de naam van de doelcomputer. De waarde van deze variabele is ingesteld in de **computernaam** vak.|Ja|Ja|Ja|  
|**OSDDomainName**<br /><br /> Hiermee geeft u de naam van het domein waaraan de doelcomputer is worden toegevoegd. De waarde van deze variabele is ingesteld in de **domein** vak.|Ja|Ja|Ja|  
|**OSDDomainOUName**<br /><br /> Hiermee geeft u de naam van de organisatie-eenheid binnen het domein waaraan de computer als doelobject wordt geplaatst. De waarde van deze variabele is ingesteld in de **organisatie-eenheid** vak.|Ja|Ja|Ja|  
|**OSDJoinAccount**<br /><br /> Hiermee geeft u het gebruikersaccount dat wordt gebruikt voor het toevoegen van de doelcomputer aan het domein. De waarde voor deze variabele is ingesteld de **gebruikersnaam** vak.|Ja|Ja|Ja|  
|**OSDJoinPassword**<br /><br /> Hiermee geeft u het wachtwoord voor het gebruikersaccount dat wordt gebruikt voor het toevoegen van de doelcomputer aan het domein. De waarde voor deze variabele is ingesteld de **wachtwoord** en **wachtwoord bevestigen** vakken.|Ja|Ja|Ja|  
|**OSDNetworkJoinType**<br /><br /> Geeft aan of de doelcomputer worden toegevoegd aan een werkgroep of een domein. Als de waarde is ingesteld op:<br /><br /> \-**0**, wordt de **domein** optie is geselecteerd en de doelcomputer wordt toegevoegd aan een domein<br /><br /> \-                                      **1**, wordt de **werkgroep** optie is geselecteerd en de doelcomputer wordt gekoppeld aan een werkgroep|Nee|Ja|Nee|  
|**SMSTSAssignUsersMode**<br /><br /> Hiermee geeft u de modus voor affiniteit tussen gebruikers en configureren in Configuration Manager. Gebruik deze variabele om de werking configureren van het maken van de affiniteit tussen de doel-computer- en gebruikersaccounts in de **SMSTSUdaUsers** takenreeksvariabele. Als deze variabele niet is opgegeven voor het weergeven van deze pagina, de waarde van deze variabele is ingesteld op **in behandeling**.<br /><br /> Mogelijke waarden voor deze variabele opnemen:<br /><br /> \-                                      **Auto.** De verwerking van de affiniteit door Configuration Manager automatisch goedgekeurd.<br /><br /> \-**In behandeling.** De affiniteit verwerken van regels is goedkeuring door een Configuration Manager-beheerder vereist.<br /><br /> \-                                      **Uitgeschakeld.** De verwerking van geen affiniteit wordt uitgevoerd.|Nee|Ja|Nee|  

###### <a name="configuration-variables"></a>Configuratievariabelen voor de  
 Geeft een lijst van tabel 33 de **ComputerPage** configuratievariabelen met een beschrijving en de variabele kan worden gelezen door de wizardpagina geschreven door de wizardpagina of kan worden geconfigureerd in het configuratiebestand van de Wizard UDI.  

### <a name="table-33-computerpage-configuration-variables"></a>Tabel 33. De variabelen ComputerPage  

|**Variabele**|**Lezen**|**Schrijven**|**Configuratie**|  
|-|-|-|-|  
|**ADComputerObjectCheck**<br /><br /> Hiermee geeft u op of de **ComputerPage** wizardpagina valideert dat de opgegeven referenties hebben met de juiste machtigingen voor het wijzigen van een computerobject in AD DS voordat u doorgaat naar de volgende wizardpagina.<br /><br /> Opmerking:<br /><br /> Deze configuratie-instelling wordt genegeerd als **ADCredentialCheck** is ingesteld op **FALSE**.<br /><br /> Als de waarde is ingesteld op:<br /><br /> \-**TRUE**, wordt de **Active Directory Computer Object controleren** selectievakje is ingeschakeld in de wizard-editor in de **Join domeinreferenties** sectie in de Wizard UDI Designer en machtigingen voor het wijzigen van een computerobject voor de referenties die worden gevalideerd<br /><br /> \-**FALSE**, wordt de **Active Directory Computer Object controleren** selectievakje is uitgeschakeld in de wizard-editor in de **Join domeinreferenties** sectie in de Wizard UDI Designer en machtigingen voor het wijzigen van een computerobject voor de referenties worden niet gevalideerd.|Ja|Nee|Ja|  
|**ADCredentialCheck**<br /><br /> Hiermee geeft u op of de **ComputerPage** wizardpagina valideert de referenties voor deelname aan een domein voordat u doorgaat naar de volgende wizardpagina. Als de waarde is ingesteld op:<br /><br /> \-                                      **TRUE**, wordt de **Active Directory-referentie controle** selectievakje is ingeschakeld in de wizard-editor in de **Join domeinreferenties** sectie in de ontwerpfunctie van de Wizard UDI en referenties zijn geverifieerd<br /><br /> Als dit configuratie-instelling is ingesteld op **TRUE**, en vervolgens de referenties zijn geverifieerd, zelfs als de referentievelden zijn uitgeschakeld \(vergrendeld\).<br /><br /> \-**FALSE**, wordt de **Active Directory-referentie controle** selectievakje is uitgeschakeld in de wizard-editor in de **Join domeinreferenties** sectie in de Wizard UDI Designer en de referenties worden niet gevalideerd.<br /><br /> Als dit configuratie-instelling is ingesteld op **FALSE**, wordt de **ADComputerObjectCheck** configuratie-instelling wordt genegeerd en de validatie dat de referenties op een computer kunnen wijzigen van objecten in AD DS wordt niet uitgevoerd.|Ja|Nee|Ja|  
|**UseExistingComputerName**<br /><br /> Hiermee geeft u op of de **ComputerPage** pagina van de wizard de bestaande computernaam gebruikt op de doelcomputer als standaardwaarde voor de computernaam.<br /><br /> Opmerking:<br /><br /> Dit selectievakje is alleen relevant voor het implementatiescenario Computer vernieuwen.<br /><br /> Als de waarde is ingesteld op:<br /><br /> \-**TRUE**, wordt de **gebruik bestaande computernaam** selectievakje is ingeschakeld in de wizard-editor in de **computernaam** sectie in de Wizard UDI Designer en de bestaande computernaam wordt gebruikt als de standaardnaam van de computer voor de doelcomputer nadat het nieuwe besturingssysteem is geïmplementeerd<br /><br /> \-                                      **ONWAAR**, wordt de **gebruik bestaande computernaam** selectievakje is uitgeschakeld in de wizard-editor in de **computernaam** sectie in de Wizard UDI Designer en de naam van de bestaande computer wordt niet gebruikt als de standaardnaam van de computer voor de doelcomputer nadat het nieuwe besturingssysteem is geïmplementeerd|Ja|Nee|Ja|  

#####  <a name="ConfigScanPage"></a>ConfigScanPage  
 Gebruik deze wizardpagina UDI taken die de configuratie van de doelcomputer om te bepalen of de doelcomputer gereed is voor de implementatie van de besturingssysteemkopie scannen uitvoeren. Deze gereedheid betekent dat u voldoende systeembronnen en alle vereiste software wordt geïnstalleerd en correct is geconfigureerd. Andere taken UDI worden bovendien die verzamelen configuratie-informatie over de doelcomputer, zoals het identificeren van uitgevoerd:  

-   Hiermee wordt aangegeven of de computer is verbonden met power \(in plaats van een accu\)  

-   Hiermee wordt aangegeven of de computer is verbonden met een bekabeld netwerk \(in plaats van via een draadloze netwerkverbinding\)  

-   Alle geïnstalleerde toepassingen  

-   De geïnstalleerde printers  

#####  <a name="LanguagePage"></a>LanguagePage  
 Gebruik deze pagina van de wizard om te bepalen welke taalpakketten moeten worden geïnstalleerd, de standaardtaal voor het beoogde besturingssysteem, de landinstellingen van het toetsenbord en de tijdzone waarin de computer zich bevindt.  

###### <a name="task-sequence-variables"></a>Takenreeksvariabelen  
 Geeft een lijst van tabel 34 de **LanguagePage** takenreeksvariabelen met een beschrijving en de variabele kan worden gelezen door de wizardpagina geschreven door de wizardpagina of kan worden geconfigureerd in het configuratiebestand van de Wizard UDI.  

### <a name="table-34-languagepage-task-sequence-variables"></a>Tabel 34. Takenreeksvariabelen LanguagePage  

|**Variabele**|**Lezen**|**Schrijven**|**Configuratie**|  
|-|-|-|-|  
|**InputLocale**<br /><br /> Hiermee geeft u de landinstellingen van het beoogde besturingssysteem. De waarde van deze variabele in de **tijd en valuta indeling** vak. Als niet wordt opgegeven, worden de landinstellingen die is geconfigureerd in de installatiekopie wordt gebruikt.|Ja|Ja|Ja|  
|**KeyboardLocale**<br /><br /> Hiermee geeft u de landinstellingen van het toetsenbord van het beoogde besturingssysteem. Stel de waarde van deze variabele in de **toetsenbordindeling** vak. Als niet wordt opgegeven, wordt de landinstelling van het toetsenbord geconfigureerd in de installatiekopie wordt gebruikt.|Ja|Ja|Ja|  
|**OSDTimeZone**<br /><br /> Hiermee geeft u de tijdzone waar de doelcomputer zich fysiek bevindt. Stel de waarde van deze variabele in de **tijdzone** vak. Als niet wordt opgegeven, wordt de tijdzone die is geconfigureerd in de installatiekopie wordt gebruikt.|Ja|Ja|Ja|  
|**UILanguage**<br /><br /> Hiermee geeft u de standaardtaal moet worden gebruikt voor het beoogde besturingssysteem. Stel de waarde van deze variabele in de **te installeren taal** vak. Als niet wordt opgegeven, is de taal die is geconfigureerd in de installatiekopie wordt gebruikt.|Ja|Ja|Ja|  

#####  <a name="ProgressPage"></a>ProgressPage  
 Gebruik deze wizardpagina UDI taken die de gebruikersstatusgegevens voor migratie van de doelcomputer vastlegt uitvoeren. Deze taken omvatten:  

-   Het toepassingsbestand detectie kopiëren naar de locatie die is geselecteerd op de [UserStatePage](#UserStatePage) wizardpagina  

-   Het configuratiebestand van de printer kopiëren naar de locatie die is geselecteerd op de [UserStatePage](#UserStatePage) wizardpagina  

-   Kopiëren van de lijst met geïnstalleerde producten op de locatie die is geselecteerd op de [UserStatePage](#UserStatePage) wizardpagina  

-   De USMT uitvoeren en opslaan van de gebruiker status migratiegegevens naar de locatie die is geselecteerd op de [UserStatePage](#UserStatePage) wizardpagina  

#####  <a name="RebootPage"></a>RebootPage  
 Gebruik deze wizardpagina melding verzenden naar de gebruiker die de doelcomputer opnieuw worden opgestart. U kunt het meldingsbericht met behulp van de waarde van de Wizard UDI configureren.  

#####  <a name="SummaryPage"></a>Overzichtspagina  
 Gebruik deze wizardpagina melding verzenden naar de gebruiker over de configuratieopties die zijn geselecteerd tijdens het uitvoeren van de Wizard UDI. De configuratie-informatie weergegeven op deze wizardpagina worden automatisch verzameld uit andere wizardpagina's. Sommige velden op andere wizardpagina's kunnen u het bijschrift configureren \(label\) weergegeven op deze pagina van de wizard met behulp van de waarde van de Wizard UDI.  

#####  <a name="UDAPage"></a>UDAPage  
 Gebruik deze wizardpagina voor het configureren van de UDA tussen de doelcomputer en een opgegeven gebruiker. Een gebruiker toewijzen als de primaire gebruiker van een computer, kunt automatische installatie van software die aan deze gebruiker is geïmplementeerd. De UDA-functie is alleen beschikbaar in Configuration Manager en alleen in het implementatiescenario voor de nieuwe Computer.  

###### <a name="task-sequence-variables"></a>Takenreeksvariabelen  
 Geeft een lijst van tabel 35 de **UDAPage** takenreeksvariabelen met een beschrijving en de variabele kan worden gelezen door de wizardpagina geschreven door de wizardpagina of kan worden geconfigureerd in het configuratiebestand van de Wizard UDI.  

### <a name="table-35-udapage-task-sequence-variables"></a>Tabel 35. Takenreeksvariabelen UDAPage  

|**Variabele**|**Lezen**|**Schrijven**|**Configuratie**|  
|-|-|-|-|  
|**SMSTSAssignUsersMode**<br /><br /> Hiermee geeft u de modus voor affiniteit tussen gebruikers en configureren in Configuration Manager. Gebruik deze variabele om de werking configureren van het maken van de affiniteit tussen de doel-computer- en gebruikersaccounts in de **SMSTSUdaUsers** takenreeksvariabele. Als u deze variabele, selecteert u de **Gebruikersapparaataffiniteit gebruik** selectievakje.<br /><br /> Als de variabele is ingesteld op:<br /><br /> \-                                      **Automatische**, en vervolgens de verwerking van de affiniteit is automatisch goedgekeurd door Configuration Manager<br /><br /> \-**In behandeling**, en vervolgens de affiniteit verwerken van regels is goedkeuring door een beheerder van Configuration Manager vereist \(dit is de waarde gebruikt wanneer de **gebruik Gebruikersaffiniteit met apparaat** selectievakje geselecteerd.\)<br /><br /> \-                                      **Uitgeschakelde**, en vervolgens de verwerking van geen affiniteit wordt uitgevoerd|Nee|Ja|Nee|  
|**SMSTSUdaUsers**<br /><br /> Hiermee geeft u de gebruikers worden gekoppeld aan de doelcomputer. De **gebruikersaccount Apparaataffiniteit** deze variabele wordt ingesteld. Deze variabele kan een of meer gebruikers die zijn opgegeven en de indeling `Domain\User1, Domain\User2`.|Ja|Ja|Ja|  

#####  <a name="UserStatePage"></a>UserStatePage  
 Gebruik deze wizardpagina voor het configureren van de instellingen voor het vastleggen of herstellen van gegevens van de migratie van gebruikersstatus. Deze pagina van de wizard wordt gebruikt voor zowel migratie gegevens vastlegging van de gebruikersstatus en het terugzetten.  

 De **UserStatePage** kunt vastleggen of gegevens van de migratie van gebruikersstatus herstellen vanaf een schijf lokaal wordt gekoppeld aan de doelcomputer en een USB-station gekoppeld aan de doelcomputer of een gedeelde netwerkmap. Bovendien kunt u niet alle om gebruikersgegevens te herstellen. De code logica achter de wizardpagina maakt, wordt uitgeschakeld of selecteert automatisch op elk van de volgende opties op basis van het scenario van implementatie- en of de schijf wordt geformatteerd:  

-   **Er zijn geen gegevens terug te zetten.** Deze optie geeft aan dat er geen migratie van de gebruikersstatusgegevens terugzetten en stelt de **OSDUserStateMode** takenreeksvariabele en **UserStateMode** variabele **GeenGegevens**.  

-   **Lokale.** Deze optie geeft aan dat de migratie van de gebruikersstatusgegevens moeten worden opgeslagen op een schijf lokaal wordt gekoppeld aan de doelcomputer en wordt de **OSDUserStateMode** takenreeksvariabele en **UserStateMode** variabele **lokale**.  

-   **USB.** Deze optie geeft aan dat de migratie van de gebruikersstatusgegevens moeten worden opgeslagen op een USB-schijf lokaal wordt gekoppeld aan de doelcomputer en wordt de **OSDUserStateMode** takenreeksvariabele en **UserStateMode** variabele **USB**.  

-   **Netwerk.** Deze optie geeft aan dat de migratie van de gebruikersstatusgegevens moeten worden opgeslagen op een gedeelde netwerkmap en stelt de **OSDUserStateMode** takenreeksvariabele en **UserStateMode** variabele **Netwerk**.  

######  <a name="NEWCOMPUTERStageBehavior"></a>NEWCOMPUTER fase gedrag  
 De fase NEWCOMPUTER wordt gebruikt voor computers waarop geen statusmigratiegegevens bestaat. Het implementatiescenario voor de nieuwe Computer kan worden gebruikt als het tweede gedeelte van het implementatiescenario Computer vervangen. Als de gebruiker selecteert aan:  

-   De schijf op de doelcomputer te formatteren en vervolgens de **UserStatePage** wordt ervan uitgegaan dat er geen statusmigratiegegevens zich op de lokale harde schijf bevindt, zodat de **lokale** optie is uitgeschakeld en alle andere opties zijn ingeschakeld  

-   De schijf op de doelcomputer niet formatteren en vervolgens de **UserStatePage** wordt ervan uitgegaan dat er statusmigratiegegevens worden hersteld, en alle opties zijn uitgeschakeld, anders dan de **lokale** optie \(Met behulp van de **lokale** optie biedt een snelle methode voor het herstellen van de gebruiker migratiegegevens dan de USB-status of een gedeelde map methoden.\)  

 Tabel 36 geeft het gedrag van de opties op de wizardpagina voor de fase NEWCOMPUTER. De **indeling** kolom wordt aangegeven of de doelschijf worden ingedeeld als onderdeel van de implementatie. De andere kolommen geven aan de configuratie van de opties bij de **UserStatePage** is geladen.  

### <a name="table-36-behavior-of-options-for-the-newcomputer-stage"></a>Tabel 36. Gedrag van de opties voor de fase NEWCOMPUTER  

|**Indeling**|**GeenGegevens**|**Lokale**|**USB**|**Netwerk**|  
|-|-|-|-|-|  
|Ja|Ingeschakeld|Uitgeschakeld|Ingeschakeld|Ingeschakeld|  
|Nee|Uitgeschakeld|Geselecteerd|Uitgeschakeld|Uitgeschakeld|  

######  <a name="NewComputerPrestagedStageBehavior"></a>NewComputer.Prestaged fase gedrag  
 De NEWCOMPUTER. Voorbereide fase is gebaseerd op de voorbereide media-functie in Configuration Manager. Omdat de lokale vaste schijf nieuw is, zijn geen gebruikersgegevens voor het migreren van status moet worden teruggezet vanuit de lokale harde schijf, zodat de **lokale** optie is uitgeschakeld. Alle andere opties zijn geldig voor dit implementatiescenario en zijn ingeschakeld. Geen standaardoptie is geselecteerd.  

 Tabel 37 geeft het gedrag van de opties op de wizardpagina voor de fase NewComputer.Prestaged. De **indeling** kolom wordt aangegeven of de doelschijf worden ingedeeld als onderdeel van de implementatie. De andere kolommen geven aan de configuratie van de opties bij de **UserStatePage** is geladen.  

### <a name="table-37-behavior-of-options-for-the-newcomputerprestaged-stage"></a>Tabel 37. Gedrag van de opties voor de fase NewComputer.Prestaged  

|**Indeling**|**GeenGegevens**|**Lokale**|**USB**|**Netwerk**|  
|-|-|-|-|-|  
|N\/A|Ingeschakeld|Uitgeschakeld|Ingeschakeld|Ingeschakeld|  

######  <a name="REFRESHStageBehavior"></a>Fase gedrag vernieuwen  
 De fase vernieuwen wordt in een volledig Windows-besturingssysteem, in plaats van Windows PE gestart. Als de gebruiker selecteert aan:  

-   De schijf op de doelcomputer te formatteren en vervolgens de **UserStatePage** wordt aangenomen dat er geen statusmigratiegegevens worden hersteld, en alle opties zijn uitgeschakeld, anders dan de **GeenGegevens** optie  

-   De schijf op de doelcomputer niet formatteren en vervolgens de **UserStatePage** wordt ervan uitgegaan dat er statusmigratiegegevens worden hersteld, en alle opties zijn uitgeschakeld, anders dan de **lokale** optie \(Met behulp van de **lokale** optie biedt een snelle methode voor het herstellen van de gebruiker migratiegegevens dan de USB-status of een gedeelde map methoden.\)  

 Tabel 38 geeft het gedrag van de opties op de wizardpagina voor de fase vernieuwen. De **indeling** kolom wordt aangegeven of de doelschijf worden ingedeeld als onderdeel van de implementatie. De andere kolommen geven aan de configuratie van de opties bij de **UserStatePage** is geladen.  

### <a name="table-38-behavior-of-options-for-the-refresh-stage"></a>Tabel 38. Gedrag van de opties voor de fase vernieuwen  

|**Indeling**|**GeenGegevens**|**Lokale**|**USB**|**Netwerk**|  
|-|-|-|-|-|  
|Ja|Geselecteerd|Uitgeschakeld|Uitgeschakeld|Uitgeschakeld|  
|Nee|Uitgeschakeld|Geselecteerd|Uitgeschakeld|Uitgeschakeld|  

######  <a name="REPLACEWinPEStageBehavior"></a>VERVANGEN. WinPE-fase gedrag  
 Het vervangen. WinPE-fase worden de statusmigratiegegevens uit de bestaande vastgelegd \(oude\) computer en herstelt de statusmigratiegegevens later via een van de nieuwe Computer implementatiescenario's. Omdat twee verschillende computers zijn betrokken bij de implementatie, moet de statusmigratiegegevens worden opgeslagen op een USB-station of op een gedeelde netwerkmap. Migratie van gebruikersstatusgegevens opslaan op een lokale schijf is niet beschikbaar.  

 Tabel 39 geeft het gedrag van de opties op de wizardpagina voor het vervangen. WinPE-fase. De **indeling** kolom wordt aangegeven of de doelschijf worden ingedeeld als onderdeel van de implementatie. De andere kolommen geven aan de configuratie van de opties bij de **UserStatePage** is geladen.  

### <a name="table-39-behavior-of-options-for-the-replacewinpe-stage"></a>Tabel 39. Gedrag van de opties voor het vervangen. WinPE-fase  

|**Indeling**|**GeenGegevens**|**Lokale**|**USB**|**Netwerk**|  
|-|-|-|-|-|  
|N\/A|Uitgeschakeld|Uitgeschakeld|Ingeschakeld|Ingeschakeld|  

###### <a name="task-sequence-variables"></a>Takenreeksvariabelen  
 Geeft een lijst van tabel 40 de **UserStatePage** takenreeksvariabelen met een beschrijving en de variabele kan worden gelezen door de wizardpagina geschreven door de wizardpagina of kan worden geconfigureerd in het configuratiebestand van de Wizard UDI.  

### <a name="table-40-userstatepage-task-sequence-variables"></a>Tabel 40. Takenreeksvariabelen UserStatePage  

|**Variabele**|**Lezen**|**Schrijven**|**Configuratie**|  
|-|-|-|-|  
|**\_SMSTsInWinPE**<br /><br /> Hiermee geeft u op of de Wizard UDI wordt uitgevoerd in Windows PE. Als de variabele is ingesteld op:<br /><br /> \-**TRUE**, en vervolgens de Wizard UDI wordt uitgevoerd in Windows PE<br /><br /> \-                                      **ONWAAR**, en vervolgens de Wizard UDI wordt niet uitgevoerd in Windows PE, maar in een volledig Windows-besturingssysteem|Ja|Nee|Nee|  
|**OSDDataSourceDirectory**<br /><br /> Hiermee geeft u de map waarop migratiegegevens van de gebruikersstatus is opgeslagen.|Nee|Ja|Nee|  
|**OSDDataSourceDrive**<br /><br /> Hiermee geeft u het USB-station gebruikt voor het vastleggen en herstellen van de statusmigratiegegevens, die u selecteert in de **USB doelstation** vak. Als de variabele is ingesteld voorafgaand aan de pagina van de wizard wordt weergegeven, wordt de waarde van de variabele gebruikt als de standaardwaarde.|Ja|Ja|Nee|  
|**OSDDiskPart**<br /><br /> Hiermee geeft u op of het station geselecteerd voor de installatie van het beoogde besturingssysteem moet worden geformatteerd en gepartitioneerd. U deze variabele instellen op de [VolumePage](#VolumePage) pagina van de wizard en de code op deze wizardpagina gebruikt om te bepalen welke opties zijn geselecteerd en wordt standaard ingeschakeld. Zie voor meer informatie [UserStatePage](#UserStatePage).|Ja|Nee|Ja|  
|**OSDHardLinks**<br /><br /> Geeft aan of de migratie van gebruikersstatusgegevens te worden vastgelegd in of hersteld vanaf een lokaal station. Als de variabele is ingesteld op:<br /><br /> \-                                      **De waarde TRUE**, wordt de **lokale** optie is geselecteerd, en gegevens van de migratie van gebruikersstatus wordt vastgelegd of hersteld vanaf een lokaal station dat is gekoppeld aan de doelcomputer<br /><br /> \-**FALSE**, wordt de **lokale** optie niet is geselecteerd en er is geen statusmigratiegegevens worden vastgelegd of hersteld vanaf een lokaal station dat is gekoppeld aan de doelcomputer|Nee|Ja|Nee|  
|**OSDRestoreData**<br /><br /> Geeft aan of er gegevens worden hersteld. Als de variabele is ingesteld op:<br /><br /> \-                                      **TRUE**, wordt de **lokale**, **USB doelstation**, of **netwerk** optie is geselecteerd, en gegevens van de migratie van gebruikersstatus wordt vastgelegd of hersteld op basis van de doelcomputer<br /><br /> \-**FALSE**, wordt de **geen gegevens terug te zetten** optie is geselecteerd en er is geen migratie van gegevens van de gebruikersstatus wordt vastgelegd of hersteld op basis van de doelcomputer|Nee|Ja|Nee|  
|**OSDUserStateKey**<br /><br /> Hiermee geeft u de naam van de gebruiker gebruikt voor het beveiligen van migratiegegevens van de gebruiker. De gebruikersnaam wordt verstrekt wanneer u migratiegegevens van de gebruikersstatus wordt vastgelegd. De dezelfde gebruikersnaam en het wachtwoord moeten worden opgegeven wanneer de migratie van gegevens van de gebruikersstatus wordt hersteld. De waarde van deze variabele in de **gebruikersnaam** vak.|Ja|Ja|Ja|  
|**OSDUserStateKeyPassword**<br /><br /> Hiermee geeft u het wachtwoord voor de naam van de gebruiker gebruikt voor het beveiligen van migratiegegevens van de gebruiker. Stel de waarde van deze variabele in de **wachtwoord** en **wachtwoord bevestigen** vakken.|Ja|Ja|Ja|  
|**OSDUserStateMode**<br /><br /> Hiermee wordt de modus \(methode\) voor het vastleggen of herstellen van de migratiegegevens van de gebruiker. De waarde van deze variabele is ingesteld door de geselecteerde opties. Als de variabele is ingesteld op:<br /><br /> \-**GeenGegevens**, wordt de **geen gegevens terug te zetten** optie is geselecteerd en er is geen migratie van gegevens van de gebruikersstatus wordt vastgelegd of hersteld<br /><br /> \-**Lokale**, wordt de **lokale** optie is geselecteerd, en de statusmigratiegegevens worden vastgelegd of hersteld op basis van een lokale harde schijf op de doelcomputer<br /><br /> \-**Netwerk**, wordt de **netwerk** optie is geselecteerd, en de gebruikersstatus **migratie** gegevens worden vastgelegd op of hersteld op basis van een gedeelde netwerkmap<br /><br /> \-Wanneer gebruikt in de modus voor vastleggen, maakt deze optie in een map op basis van een hash van de gebruikersnaam en wachtwoord, zodat de identiteit van de migratie van gebruikersstatusgegevens is beveiligd. De exacte dezelfde gebruikersnaam en het wachtwoord moeten worden gebruikt bij het herstellen van de migratie van gebruikersstatusgegevens zodat de wizardpagina nauwkeurig voor de map vinden kan.<br /><br /> \-**USB**, wordt de **USB doelstation** optie is geselecteerd, en de statusmigratiegegevens worden vastgelegd op of hersteld op basis van een USB-station dat fysiek is gekoppeld aan de doelcomputer<br /><br /> \-Het gedrag van de pagina wizard voor USB-stations wordt ook beïnvloed door de **indeling**, **FormatPrompt**, en **MinimumDriveSize** variabelen.|Nee|Ja|Nee|  
|**SMSConnectNetworkFolderPath**<br /><br /> Hiermee geeft u de gedeelde netwerkmap gebruikt voor het vastleggen en herstellen van de statusmigratiegegevens, die is geselecteerd in de **netwerk** vak. De **netwerk** verschijnt een gebruiker\-beschrijvende naam voor het netwerk gedeelde map die is geconfigureerd in de **netwerkshares** vak de **netwerk keuzelijst met invoervak** gedeelte van de wizard-editor in de ontwerpfunctie van de Wizard UDI. Als de variabele is ingesteld voorafgaand aan de pagina van de wizard wordt weergegeven, wordt de waarde van de variabele gebruikt als de standaardwaarde.|Ja|Ja|Ja|  

###### <a name="memory-variables"></a>Geheugenvariabelen  
 Geeft een lijst van tabel 41 de **UserStatePage** geheugenvariabelen met een beschrijving en of de variabele is gelezen of door de wizardpagina geschreven.  

### <a name="table-41-userstatepage-memory-variables"></a>Tabel 41. Variabelen UserStatePage geheugen  

|**Variabele**|**Lezen**|**Schrijven**|  
|-|-|-|  
|**Stationsletter**<br /><br /> Hiermee geeft u de stationsletter voor het USB-station is geselecteerd in de **USB doelstation** vak op de wizardpagina. De waarde van deze variabele is de stationsletter, inclusief het achtervoegsel van de dubbele punt (:), zoals *M:.*|Nee|Ja|  
|**TargetDrive**<br /><br /> Hiermee geeft u het bijschrift wordt weergegeven de **USB doelstation** vak op de wizardpagina voor de USB-station op de doelcomputer is geselecteerd. De waarde van deze variabele is vergelijkbaar met het volgende voorbeeld:<br /><br /> `M: VendorA Ultra TD v1.0 USB Device (74.5 GB)`|Nee|Ja|  
|**UserStateMode**<br /><br /> Hiermee geeft u de optie is geselecteerd met de opties op de wizardpagina en is ingesteld op dezelfde waarde als de **OSDUserStateMode** variabele. Geldige waarden voor deze variabele zijn:<br /><br /> -                                      **GeenGegevens**, wat aangeeft dat de **geen gegevens terug te zetten** optie is geselecteerd<br /><br /> -                                      **Lokale**, wat aangeeft dat de **lokale** optie is geselecteerd<br /><br /> -                                      **USB**, wat aangeeft dat de **USB doelstation** optie is geselecteerd<br /><br /> - **Netwerk**, wat aangeeft dat de **netwerk** optie is geselecteerd|Nee|Ja|  

###### <a name="configuration-variables"></a>Configuratievariabelen voor de  
 Geeft een lijst van tabel 42 de **UserStatePage** configuratievariabelen met een beschrijving en de variabele kan worden gelezen door de wizardpagina geschreven door de wizardpagina of kan worden geconfigureerd in het configuratiebestand van de Wizard UDI.  

### <a name="table-42-userstatepage-configuration-variables"></a>Tabel 42. De variabelen UserStatePage  

|**Variabele**|**Lezen**|**Schrijven**|**Configuratie**|  
|-|-|-|-|  
|**DataSourceText**<br /><br /> Hiermee geeft u een informatief bericht zodat de gebruiker uitvoeren van de gebruikersstatus vastleggen of terugzetten over het gebruik van de wizardpagina. De waarde van deze variabele in de **instructietekst** vak de **bericht** sectie in de wizard wisselbare editor in de ontwerpfunctie van de Wizard UDI.|Ja|Nee|Ja|  
|**Indeling**<br /><br /> Hiermee geeft u op of het USB-station dat is geselecteerd voor het vastleggen van gebruikersstatus op de doelcomputer moet worden gepartitioneerd en geformatteerd voordat u gegevens van de migratie van gebruikersstatus vastlegt. De waarde van deze variabele instellen door te selecteren de **Formatteer het USB-station voordat vastleggen** selectievakje in de **USB-keuzelijst met invoervak** sectie in de wizard wisselbare editor in de ontwerpfunctie van de Wizard UDI.<br /><br /> Als de variabele is ingesteld op:<br /><br /> - **De waarde TRUE**, en vervolgens het station is geformatteerd voordat u gegevens van de migratie van gebruikersstatus vastlegt<br /><br /> -                                      **ONWAAR**, en vervolgens het station is niet geformatteerd voordat u gegevens van de migratie van gebruikersstatus vastlegt|Ja|Nee|Ja|  
|**FormatPrompt**<br /><br /> Hiermee geeft u op of de gebruiker controleren moet of het USB-station gebruikt voor het vastleggen van de statusmigratiegegevens worden geformatteerd voordat de opname worden uitgevoerd. De waarde van deze variabele instellen door te selecteren de **de gebruiker gevraagd het doelstation opmaak** selectievakje in de **USB-keuzelijst met invoervak** sectie in de wizard wisselbare editor in de ontwerpfunctie van de Wizard UDI.<br /><br /> Opmerking:<br /><br /> Deze variabele is alleen geldig als de **OSDUserStateMode** takenreeksvariabele is ingesteld op **USB**.|Ja|Nee|Ja|  
|**MinimumDriveSize**<br /><br /> Hiermee geeft u de minimale vrije schijfruimte in GB vereist voor een station beschikbaar is voor het opslaan van gegevens van de migratie van gebruikersstatus. De waarde van deze variabele fungeert als een filter, en u deze in te stellen de **station minimumformaat** tekstvak de **USB-keuzelijst met invoervak** sectie in de wizard wisselbare editor in de ontwerpfunctie van de Wizard UDI.|Ja|Nee|Ja|  
|**NetworkDrive**<br /><br /> Hiermee geeft u de stationsletter die gebruikmaakt van deze wizardpagina toewijzen aan de gedeelde netwerkmap in de **SMSConnectNetworkFolderPath** takenreeksvariabele. De gedeelde map netwerktoewijzing wordt gebruikt voor het vastleggen of herstellen van de migratiegegevens van de gebruiker. Stel de waarde van deze variabele in de **stationsletter toegewezen** vak de **netwerk keuzelijst met invoervak** sectie in de wizard wisselbare editor in de ontwerpfunctie van de Wizard UDI. De opgegeven stationsletter mag vergezeld gaan van de dubbele punt (:) na de stationsletter en niet in gebruik is op de doelcomputer. Bijvoorbeeld, als de doelcomputer station C: en D: heeft, kan vervolgens C: en D: niet worden gebruikt voor deze variabele.<br /><br /> Opmerking:<br /><br /> Deze variabele is alleen geldig als de **OSDUserStateMode** takenreeksvariabele is ingesteld op **netwerk**.|Ja|Nee|Ja|  
|**Status**<br /><br /> Hiermee geeft u op of de wizardpagina wordt gebruikt voor het vastleggen of herstellen van de migratiegegevens van de gebruiker. Stel de waarde van deze variabele in de **vastleggen of terugzetten** vak de **vastleggen/terugzetten locatie** sectie in de wizard wisselbare editor in de ontwerpfunctie van de Wizard UDI. Als de variabele is ingesteld op:<br /><br /> - **Vastleggen**, en vervolgens de wizardpagina wordt gebruikt voor het vastleggen van gegevens van de migratie van gebruikersstatus<br /><br /> -                                      **Herstellen**, en vervolgens de wizardpagina wordt gebruikt om te herstellen van gegevens van de migratie van gebruikersstatus|Ja|Nee|Ja|  

#####  <a name="VolumePage"></a>VolumePage  
 Gebruik deze wizardpagina voor het configureren van de instellingen voor het schijfvolume op de doelcomputer waarop het besturingssysteem wordt geïmplementeerd. Deze instellingen omvatten het doelbesturingssysteem selecteren, selecteert het doelstation selecteren van een Windows-installatie en te bepalen of het doelstation worden opgemaakt als een deel van het implementatieproces.  

###### <a name="task-sequence-variables"></a>Takenreeksvariabelen  
 Geeft een lijst van tabel 43 de **VolumePage** takenreeksvariabelen met een beschrijving en de variabele kan worden gelezen door de wizardpagina geschreven door de wizardpagina of kan worden geconfigureerd in het configuratiebestand van de Wizard UDI.  

### <a name="table-43-volumepage-task-sequence-variables"></a>Tabel 43. Takenreeksvariabelen VolumePage  

|**Variabele**|**Lezen**|**Schrijven**|**Configuratie**|  
|-|-|-|-|  
|**OSDDiskPart**<br /><br /> Hiermee geeft u op of het station geselecteerd voor het implementeren van het beoogde besturingssysteem op de doelcomputer moet worden gepartitioneerd en geformatteerd voordat u gegevens van de migratie van gebruikersstatus vastlegt. De waarde van deze variabele wordt ingesteld door een van de volgende selectievakjes in de wizard:<br /><br /> -                                      **Het geselecteerde volume wilt opschonen.** Dit selectievakje wordt weergegeven wanneer de Wizard UDI in een volledig Windows-besturingssysteem wordt uitgevoerd. U kunt de SMS-bericht met de **FormatFullOS** setter-eigenschap voor de wizardpagina in het configuratiebestand van de Wizard UDI.<br /><br /> -                                      **Partitioneren en formatteren schijf 0.** Dit selectievakje wordt weergegeven wanneer de Wizard UDI wordt uitgevoerd in Windows PE. U kunt de SMS-bericht met de **FormatWinPE** setter-eigenschap voor de wizardpagina in het configuratiebestand van de Wizard UDI.<br /><br /> De code logica achter het [UserStatePage](#UserStatePage) wizardpagina gebruikt deze variabele om te bepalen welke opties zijn geselecteerd en wordt standaard ingeschakeld.<br /><br /> Als de variabele is ingesteld op:<br /><br /> - **De waarde TRUE**, en vervolgens het station is gepartitioneerd en geformatteerd voordat u het doelbesturingssysteem implementeert<br /><br /> -                                      **ONWAAR**, en vervolgens het station niet is gepartitioneerd en geformatteerd voordat u het doelbesturingssysteem implementeert|Ja|Ja|Ja|  
|**OSDImageIndex**<br /><br /> Hiermee geeft u een numerieke index van de installatiekopie van het besturingssysteem in het WIM-bestand, dat is geselecteerd in de **selectie van een installatiekopie** keuzelijst met invoervak. Configureren van de lijst met mogelijke van installatiekopieën van besturingssystemen in de **selectie van een installatiekopie** vak de **waarden van de installatiekopie van keuzelijst met invoervak** lijst de **installatiekopie keuzelijst met invoervak** sectie over de  **VolumePage** wizard pagina-editor. De index van de installatiekopie is geconfigureerd als onderdeel van elke installatiekopie in de **waarden van de installatiekopie van keuzelijst met invoervak** lijst.|Ja|Ja|Ja|  
|**OSDImageName**<br /><br /> Hiermee geeft u de naam van de installatiekopie van het besturingssysteem in het WIM-bestand, dat is geselecteerd in de **selectie van een installatiekopie** vak. De lijst met mogelijke van installatiekopieën van besturingssystemen in de **selectie van een installatiekopie** keuzelijst met invoervak is geconfigureerd in de **waarden van de installatiekopie van keuzelijst met invoervak** lijst de **installatiekopie keuzelijst met invoervak** sectie op de **VolumePage** wizard pagina-editor. Naam van de installatiekopie is geconfigureerd als onderdeel van elke installatiekopie in de **waarden van de installatiekopie van keuzelijst met invoervak** lijst.|Nee|Ja|Nee|  
|**OSDTargetDrive**<br /><br /> Hiermee geeft u de stationsletter van het volume dat is geselecteerd in de **Volume** vak op de wizardpagina. De waarde van deze variabele is de stationsletter, inclusief het achtervoegsel van de dubbele punt (:), zoals *C:.*|Nee|Ja|Nee|  
|**OSDWinPEWindir**<br /><br /> Hiermee geeft u de locatie van een bestaande installatie van Windows op de doelcomputer. Stel de waarde van deze variabele in de **Windows-map** vak op de wizardpagina.|Nee|Ja|Nee|  

###### <a name="memory-variables"></a>Geheugenvariabelen  
 Geeft een lijst van tabel 44 de **VolumePage** geheugenvariabelen met een beschrijving en of de variabele is gelezen of door de wizardpagina geschreven.  

### <a name="table-44-volumepage-memory-variables"></a>Tabel 44. Variabelen VolumePage geheugen  

|**Variabele**|**Lezen**|**Schrijven**|  
|-|-|-|  
|**VolumeArchitecture**<br /><br /> Hiermee geeft u de processorarchitectuur van het besturingssysteem worden geïmplementeerd, die is geselecteerd in de **selectie van een installatiekopie** vak. De **VolumeArchitecture** wizardpagina verbruikt deze variabele om te filteren op de architectuur van toepassingen op deze pagina weergegeven. Bijvoorbeeld, als u een 32-bits besturingssysteem wordt geïmplementeerd, wordt de **VolumeArchitecture** wizardpagina verwijdert (filters) 64-bits toepassingen uit de lijst met beschikbare toepassingen.<br /><br /> Als de variabele is ingesteld op:<br /><br /> -                                      **x86**, en vervolgens een 32-bits besturingssysteem is geselecteerd<br /><br /> - **AMD64**, 64-bits besturingssysteem is geselecteerd|Nee|Ja|  

#####  <a name="WelcomePage"></a>WelcomePage  
 Gebruik deze wizardpagina informatie opgeven voor de gebruiker over de Wizard UDI en het implementatieproces. U kunt het meldingsbericht met behulp van de waarde van de Wizard UDI configureren.  

### <a name="udi-build-your-own-page-toolbox-control-reference"></a>UDI bouwen toegangsbeheer-referentiemateriaal voor uw eigen pagina werkset  
 De functie voor uw eigen pagina bouwen in UDI kunt u aangepaste wizardpagina's die u gebruiken kunt voor het verzamelen van aanvullende implementatie-informatie voor gebruik in UDI maken. U kunt aangepaste wizard's maken met de:  

-   **Bouw uw eigen functie.** Deze functie kunt u een aangepaste wizardpagina voor het verzamelen van informatie over het implementeren zonder dat u code schrijven of ontwikkelingsvaardigheden hebben te maken. Gebruik deze functie als u nodig hebt voor het verzamelen van basisinformatie zonder tussenkomst van de ervaren gebruikers. U kan bijvoorbeeld code toevoegen of aanpassen van de gebruikersinterface lettertypen met deze functie.  

-   **UDI SDK en Visual Studio**. Deze SDK gebruiken als u maken van een geavanceerde, volledig aangepaste wizardpagina in Visual Studio wilt voor het verzamelen van informatie over de implementatie. Hoewel de UDI SDK u aangepaste wizardpagina's kunt, zoals aangepaste code toevoegen of wijzigen van lettertypen, maken vereist deze methode ontwikkelingsvaardigheden.  

     Zie voor meer informatie over het maken van aangepaste wizardpagina's via de SDK UDI 'Maken van aangepaste UDI wizardpagina's ' in de *schijf van de gebruiker de installatie-handleiding voor ontwikkelaars*.  

 De functie bouwen uw eigen pagina bevat een werkset met besturingselementen die u aan uw aangepaste wizardpagina uit de werkset van uw eigen pagina bouwen, dat wordt weergegeven toevoegen kunt wanneer u de aangepaste wizardpagina weergeven op de **configureren** tabblad in de Wizard UDI Designer.  

 Tabel 45 bevat de typen besturingselementen naar uw aangepaste wizardpagina dat wordt weergegeven in afbeelding 5. Elk van deze besturingselementen wordt in een onderliggende sectie nader besproken.  

### <a name="table-45-types-of-controls-in-the-udi-build-your-own-page-toolbox"></a>Tabel 45. Typen besturingselementen in de UDI bouwen uw eigen pagina werkset  

|**Besturingselementtype**|**Beschrijving**|  
|-|-|  
|[Selectievakje besturingselement](#CheckboxControl)|Dit besturingselement kunt u selecteren of wissen van een configuratieoptie en gedraagt zich als een traditionele UI-selectievakje.|  
|[Keuzelijst met invoervak](#ComboboxControl)|Dit besturingselement kunt u een item selecteren uit een lijst met items en gedraagt zich als een vervolgkeuzelijst traditionele gebruikersinterface.|  
|[Lijnbesturingselement](#LineControl)|Dit besturingselement kunt u een horizontale lijn delen van een deel van de aangepaste wizardpagina van een andere toevoegen.|  
|[Label-besturingselement](#LabelControl)|Dit besturingselement kunt u beschrijvende, alleen-lezen tekst toevoegen aan de wizardpagina.|  
|[Beheer van keuzerondjes](#RadioControl)|Dit besturingselement kunt u een configuratieoptie selecteren uit een groep van twee of meer opties.|  
|[Bitmap-besturingselement](#BitmapControl)|Dit besturingselement kunt u een bitmapafbeelding (bmp-bestand) toevoegen aan de aangepaste wizardpagina.|  
|[TextBox-besturingselement](#TextboxControl)|Dit besturingselement kunt u tekst op de pagina wizard Aangepaste invoeren.|  

 U kunt toevoegen om een combinatie van deze besturingselementen naar uw aangepaste wizardpagina op basis van de informatie die u wilt verzamelen. Bovendien kunt u de **rasterlijnen weergeven** selectievakje in als de rasterlijnen die kunnen worden gebruikt om te helpen bij het ontwerpen van de aangepaste wizardpagina visueel weergeven of verbergen.  

 Afbeelding 5 biedt een voorbeeld van een aangepaste wizardpagina en de werkset van uw eigen pagina bouwen.  

 ![UDI verwijzing 5](media/UDIReference5.jpg)  

 **Afbeelding SEQ afbeelding \\ \* ARABIC 5. Voorbeeldpagina wizard Aangepaste**  

####  <a name="CheckboxControl"></a>Selectievakje besturingselement  
 Dit besturingselement kunt u selecteren of wissen van een configuratieoptie en gedraagt zich als een traditionele UI-selectievakje. Dit besturingselement heeft een bijbehorende label dat u gebruiken kunt om te beschrijven van het doel van het selectievakje in. De status van dit besturingselement is waar als het selectievakje is ingeschakeld en ONWAAR wanneer het selectievakje is uitgeschakeld. De status van het selectievakje wordt opgeslagen in de takenreeksvariabele die is geconfigureerd voor dit besturingselement.  

##### <a name="layout-properties"></a>Outeigenschappen van de lay  
 Eigenschappen voor de indeling gebruikt voor het configureren van de kenmerken van de gebruikersinterface van het besturingselement en zijn geconfigureerd op de **lay-out** tabblad in de waarde van de Wizard UDI. 46 tabel bevat de eigenschappen van de lay-out voor de **selectievakje** beheren en bevat een korte beschrijving van elke eigenschap  

### <a name="table-46-checkbox-control-layout-properties"></a>Tabel 46. Selectievakje besturingselementeigenschappen lay-out  

|**Eigenschap**|**Beschrijving**|  
|-|-|  
|**X**|Gebruik deze eigenschap voor het configureren van de horizontale positie van het besturingselement.|  
|**Y**|Gebruik deze eigenschap voor het configureren van de verticale positie van het besturingselement.|  
|**Label**|Gebruik deze eigenschap voor het configureren van de beschrijvende tekst die is gekoppeld aan het selectievakje in.|  
|**Breedte**|Gebruik deze eigenschap voor het configureren van de breedte van het besturingselement.<br /><br /> **Opmerking** als de tekst die is opgegeven in de **Label** eigenschap langer is dan de breedte van het besturingselement, de tekst wordt afgekapt en niet weergegeven.|  
|**Hoogte**|Gebruik deze eigenschap voor het configureren van de hoogte van het besturingselement.<br /><br /> **Opmerking** als de tekst die is opgegeven in de **Label** eigenschap groter is dan de hoogte van het besturingselement, de tekst wordt afgekapt.|  

##### <a name="settings-properties"></a>Eigenschappen van clientstatusinstellingen  
 Eigenschappen van de instellingen worden gebruikt voor het configureren van de gegevens in eerste instantie wordt weergegeven in een besturingselement (de standaardwaarde) en waar de informatie wordt verzameld van de gebruiker wordt opgeslagen. 47 tabel bevat de eigenschappen van de instellingen voor de **selectievakje** beheren en bevat een korte beschrijving van elke eigenschap.  

### <a name="table-47-checkbox-control-settings-properties"></a>Tabel 47. Selectievakje instellingen besturingselementeigenschappen  

|**Eigenschap**|**Beschrijving**|  
|-|-|  
|**Standaardwaarde**|Gebruik deze eigenschap voor het configureren van de standaardwaarde voor het besturingselement. Voor een selectievakje, is de standaardwaarde **False**.|  
|**Variabele naam op van takenreeks**|Deze eigenschap gebruiken voor het configureren van de takenreeksvariabele waar de informatie die verzameld van de gebruiker wordt opgeslagen. Als de variabele voor de takenreeks:<br /><br /> -Biedt nog niet bestaat, wordt de takenreeksvariabele gemaakt en is ingesteld op de waarde van de gebruiker biedt<br /><br /> -Bestaat al, de bestaande waarde van de takenreeksvariabele wordt overschreven met de waarde die de gebruiker|  
|**Beschrijvende weergavenaam zichtbaar in de pagina overzicht**|Gebruik deze eigenschap voor het configureren van de beschrijvende naam die wordt weergegeven op de **samenvatting** wizardpagina. Deze naam wordt gebruikt om te beschrijven van de waarde die is opgeslagen in de **variabele naam op van Takenreeks** eigenschap voor dit besturingselement.|  
|**Ontgrendeld.**|Gebruik deze eigenschap configureren of de gebruiker zich kan communiceren met het besturingselement. Het besturingselement is standaard ingeschakeld. Deze knop wordt weergegeven voor de volgende statussen:<br /><br /> - **Ontgrendeld.** Het besturingselement is ingeschakeld en gebruikers met behulp van deze gegevens kunnen opgeven.<br /><br /> -                                  **Vergrendeld.** Het besturingselement is uitgeschakeld en gebruikers hebben geen gebruik van informatie op te geven.<br /><br /> **Opmerking** als (vergrendelen) een besturingselement is uitgeschakeld, u moet de gegevens opgeven het besturingselement dat is verzameld door MDT-eigenschappen te configureren in CustomSettings.ini of in de MDT-database. Anders de benodigde informatie worden niet verzameld door de Wizard UDI en mislukt de implementatie UDI.|  

####  <a name="ComboboxControl"></a>Keuzelijst met invoervak  
 Dit besturingselement kunt u een item selecteren uit een lijst met items en gedraagt zich als een vervolgkeuzelijst traditionele gebruikersinterface. Dit besturingselement kunt u toevoegen of verwijderen van items uit de lijst en geef een overeenkomende waarde die in de takenreeksvariabele die is geconfigureerd voor dit besturingselement worden ingesteld.  

##### <a name="layout-properties"></a>Outeigenschappen van de lay  
 Eigenschappen voor de indeling gebruikt voor het configureren van de kenmerken van de gebruikersinterface van het besturingselement en zijn geconfigureerd op de **lay-out** tabblad in de waarde van de Wizard UDI. 48 tabel bevat de eigenschappen van de lay-out voor de **Combobox** beheren en bevat een korte beschrijving van elke eigenschap.  

### <a name="table-48-combobox-control-layout-properties"></a>Tabel 48. Eigenschappen voor de keuzelijst met invoervak indeling  

|**Eigenschap**|**Beschrijving**|  
|-|-|  
|**X**|Gebruik deze eigenschap voor het configureren van de horizontale positie van het besturingselement.|  
|**Y**|Gebruik deze eigenschap voor het configureren van de verticale positie van het besturingselement.|  
|**Breedte**|Gebruik deze eigenschap voor het configureren van de breedte van het besturingselement.<br /><br /> **Opmerking** als de tekst die is ingevoerd in het besturingselement langer dan de breedte van het besturingselement is, de tekst niet wordt weergegeven.|  
|**Hoogte**|Gebruik deze eigenschap voor het configureren van de hoogte van het besturingselement.<br /><br /> **Opmerking** als de tekst die is ingevoerd in het besturingselement groter dan de hoogte van het besturingselement is, de tekst wordt afgekapt.|  
|**Gegevensitems**|Gebruik deze eigenschap voor het configureren van de lijst met items van de gegevens weergegeven in het besturingselement. Elk gegevensitem heeft de volgende eigenschappen:<br /><br /> -                                  **Waarde.** De waarde die is opgeslagen in de takenreeksvariabele wanneer het gegevensitem is geselecteerd<br /><br /> -                                  **DisplayValue.** De waarde voor de gebruiker in het besturingselement weergegeven<br /><br /> U kunt het volgende doen:<br /><br /> -Gegevensitems toevoegen aan de lijst met de knop blauw plusteken onmiddellijk aan de rechterkant van de lijst met gegevensitems<br /><br /> -Gegevensitems verwijderen uit de lijst met de rode **X** knop onmiddellijk aan de rechterkant van de lijst met gegevensitems<br /><br /> **Opmerking** u kunt de volgorde van het gegevensitem in de lijst niet wijzigen nadat een item wordt toegevoegd aan de lijst. Zorg ervoor dat u de gegevensitems in de volgorde die u wilt dat ze invoeren worden weergegeven in het besturingselement.|  

##### <a name="settings-properties"></a>Eigenschappen van clientstatusinstellingen  
 Eigenschappen van de instellingen worden gebruikt voor het configureren van de gegevens die in eerste instantie wordt weergegeven in een besturingselement (de standaardwaarde) en waar de gegevens die worden verzameld van de gebruiker wordt opgeslagen. 49 tabel bevat de eigenschappen van de instellingen voor de **Combobox** beheren en bevat een korte beschrijving van elke eigenschap.  

### <a name="table-49-combobox-control-settings-properties"></a>Tabel 49. Eigenschappen van de keuzelijst met invoervak  

|**Eigenschap**|**Beschrijving**|  
|-|-|  
|**Variabele naam op van takenreeks**|Deze eigenschap gebruiken voor het configureren van de takenreeksvariabele waar de informatie die verzameld van de gebruiker wordt opgeslagen. Als de variabele voor de takenreeks:<br /><br /> -Biedt nog niet bestaat, wordt de takenreeksvariabele gemaakt en is ingesteld op de waarde van de gebruiker biedt<br /><br /> -Bestaat al, de bestaande waarde van de takenreeksvariabele wordt overschreven met de waarde die de gebruiker|  
|**Beschrijvende weergavenaam zichtbaar in de pagina overzicht**|Gebruik deze eigenschap voor het configureren van de beschrijvende naam die wordt weergegeven op de **samenvatting** wizardpagina. Deze naam wordt gebruikt om te beschrijven van de waarde die is opgeslagen in de **variabele naam op van Takenreeks** eigenschap voor dit besturingselement.|  
|**Ontgrendeld.**|Gebruik deze eigenschap configureren of de gebruiker zich kan communiceren met het besturingselement. Het besturingselement is standaard ingeschakeld. Deze knop wordt weergegeven voor de volgende statussen:<br /><br /> -                                  **Ontgrendeld.** Het besturingselement is ingeschakeld en gebruikers met behulp van deze gegevens kunnen opgeven.<br /><br /> - **Vergrendeld.** Het besturingselement is uitgeschakeld en gebruikers hebben geen gebruik van informatie op te geven.<br /><br /> **Opmerking** als (vergrendelen) een besturingselement is uitgeschakeld, u moet de gegevens opgeven het besturingselement dat is verzameld door MDT-eigenschappen te configureren in CustomSettings.ini of in de MDT-database. Anders de benodigde informatie worden niet verzameld door de Wizard UDI en mislukt de implementatie UDI.|  

####  <a name="LineControl"></a>Lijnbesturingselement  
 Dit besturingselement kunt u een horizontale lijn delen van een deel van de aangepaste wizardpagina van een andere toevoegen. Dit besturingselement verzamelt niet alle configuratiewaarden, maar in plaats daarvan wordt gebruikt voor het verbeteren van de gebruikersinterface visueel.  

##### <a name="layout-properties"></a>Outeigenschappen van de lay  
 Eigenschappen voor de indeling gebruikt voor het configureren van de kenmerken van de gebruikersinterface van het besturingselement en zijn geconfigureerd op de **lay-out** tabblad in de waarde van de Wizard UDI. 50 tabel bevat de eigenschappen van de lay-out voor de **regel** beheren en bevat een korte beschrijving van elke eigenschap.  

### <a name="table-50-line-control-layout-properties"></a>Tabel 50. Lay-out van de regeleigenschappen-besturingselement  

|**Eigenschap**|**Beschrijving**|  
|-|-|  
|**X**|Gebruik deze eigenschap voor het configureren van de horizontale positie van het besturingselement.|  
|**Y**|Gebruik deze eigenschap voor het configureren van de verticale positie van het besturingselement.|  
|**Breedte**|Gebruik deze eigenschap voor het configureren van de breedte van het besturingselement.|  
|**Hoogte**|Gebruik deze eigenschap voor het configureren van de hoogte van het besturingselement.<br /><br /> **Opmerking** verhogen van deze eigenschap niet vergroten de breedte of hoogte van de regel.|  

##### <a name="settings-properties"></a>Eigenschappen van clientstatusinstellingen  
 De **regel** besturingselement heeft geen eigenschappen instellingen.  

####  <a name="LabelControl"></a>Label-besturingselement  
 Dit besturingselement kunt u beschrijvende, alleen-lezen tekst toevoegen aan de wizardpagina. Dit besturingselement verzamelt niet alle configuratiewaarden, maar in plaats daarvan wordt gebruikt voor het verbeteren van de gebruikersinterface visueel.  

##### <a name="layout-properties"></a>Outeigenschappen van de lay  
 Eigenschappen voor de indeling gebruikt voor het configureren van de kenmerken van de gebruikersinterface van het besturingselement en zijn geconfigureerd op de **lay-out** tabblad in de waarde van de Wizard UDI. 51 tabel bevat de eigenschappen van de lay-out voor de **Label** beheren en bevat een korte beschrijving van elke eigenschap.  

### <a name="table-51-label-control-layout-properties"></a>Tabel 51. Label, besturingselementeigenschappen lay-out  

|**Eigenschap**|**Beschrijving**|  
|-|-|  
|**X**|Gebruik deze eigenschap voor het configureren van de horizontale positie van het besturingselement.|  
|**Y**|Gebruik deze eigenschap voor het configureren van de verticale positie van het besturingselement.|  
|**Label**|Gebruik deze eigenschap voor het configureren van de beschrijvende tekst die is gekoppeld aan dit besturingselement.|  
|**Breedte**|Gebruik deze eigenschap voor het configureren van de breedte van het besturingselement.<br /><br /> **Opmerking** als de tekst die is opgegeven in de **Label** eigenschap langer is dan de breedte van het besturingselement, de tekst wordt afgekapt en niet weergegeven.|  
|**Hoogte**|Gebruik deze eigenschap voor het configureren van de hoogte van het besturingselement.<br /><br /> **Opmerking** als de tekst die is opgegeven in de **Label** eigenschap groter is dan de hoogte van het besturingselement, de tekst wordt afgekapt.|  

##### <a name="settings-properties"></a>Eigenschappen van clientstatusinstellingen  
 De **Label** besturingselement heeft geen eigenschappen instellingen.  

####  <a name="RadioControl"></a>Beheer van keuzerondjes  
 Dit besturingselement kunt u een optie selecteren uit een groep van twee of meer opties. Net als bij traditionele keuzerondjes, kunt u twee of meer van deze beveiligingsmaatregelen; groeperen de gebruiker kan Selecteer vervolgens een van de opties in de groep.  

 Een unieke waarde is toegewezen aan elk keuzerondje. De waarde die is toegewezen aan de geselecteerde keuzelijst wordt opgeslagen in de takenreeksvariabele die is geconfigureerd voor dit besturingselement.  

##### <a name="layout-properties"></a>Outeigenschappen van de lay  
 Eigenschappen voor de indeling gebruikt voor het configureren van de kenmerken van de gebruikersinterface van het besturingselement en zijn geconfigureerd op de **lay-out** tabblad in de waarde van de Wizard UDI. Tabel 52 bevat de eigenschappen van de lay-out voor de **Radio** beheren en bevat een korte beschrijving van elke eigenschap.  

### <a name="table-52-radio-control-layout-properties"></a>Tabel 52. Eigenschappen van keuzerondjes besturingselement lay-out  

|**Eigenschap**|**Beschrijving**|  
|-|-|  
|**X**|Gebruik deze eigenschap voor het configureren van de horizontale positie van het besturingselement.|  
|**Y**|Gebruik deze eigenschap voor het configureren van de verticale positie van het besturingselement.|  
|**Label**|Gebruik deze eigenschap de beschrijvende tekst die is gekoppeld aan het keuzerondje configureren.|  
|**Breedte**|Gebruik deze eigenschap voor het configureren van de breedte van het besturingselement.<br /><br /> **Opmerking** als de tekst die is opgegeven in de **Label** eigenschap langer is dan de breedte van het besturingselement, de tekst wordt afgekapt en niet weergegeven.|  
|**Hoogte**|Gebruik deze eigenschap voor het configureren van de hoogte van het besturingselement.<br /><br /> **Opmerking** als de tekst die is opgegeven in de **Label** eigenschap groter is dan de hoogte van het besturingselement, de tekst wordt afgekapt.|  
|**Groep met keuzerondjes**|Gebruik deze eigenschap aan de groep twee of meer keuzerondjes. Als keuzerondjes tot dezelfde groep behoren, kan slechts één van de keuzerondjes in een groep kan worden geselecteerd.<br /><br /> Als u meerdere groepen van keuzerondjes nodig hebt, kunt u deze eigenschap voor elke betreffende groep met keuzerondjes configureren.|  
|**Waarde**|Gebruik deze eigenschap voor het configureren van de waarde die is opgeslagen in de takenreeksvariabele wanneer het keuzerondje is ingeschakeld.|  

##### <a name="settings-properties"></a>Eigenschappen van clientstatusinstellingen  
 Eigenschappen van de instellingen worden gebruikt voor het configureren van de gegevens in eerste instantie wordt weergegeven in een besturingselement (de standaardwaarde) en waar de informatie wordt verzameld van de gebruiker wordt opgeslagen. 53 tabel bevat de eigenschappen van de instellingen voor de **Radio** beheren en bevat een korte beschrijving van elke eigenschap.  

### <a name="table-53-radio-control-settings-properties"></a>53 van de tabel. Keuzerondjes instellingen besturingselementeigenschappen  

|**Eigenschap**|**Beschrijving**|  
|-|-|  
|**Standaardwaarde**|Gebruik deze eigenschap voor het configureren van de standaardwaarde voor het besturingselement. De waarde is standaard ingesteld op de besturingselement-ID.|  
|**Variabele naam op van takenreeks**|Deze eigenschap gebruiken voor het configureren van de takenreeksvariabele waar de informatie die verzameld van de gebruiker wordt opgeslagen. Als de variabele voor de takenreeks:<br /><br /> -Biedt nog niet bestaat, wordt de takenreeksvariabele gemaakt en is ingesteld op de waarde van de gebruiker biedt<br /><br /> -Bestaat al, de bestaande waarde van de takenreeksvariabele wordt overschreven met de waarde die de gebruiker|  
|**Beschrijvende weergavenaam zichtbaar in de pagina overzicht**|Gebruik deze eigenschap voor het configureren van de beschrijvende naam die wordt weergegeven op de **samenvatting** wizardpagina. Deze naam wordt gebruikt om te beschrijven van de waarde die is opgeslagen in de **variabele naam op van Takenreeks** eigenschap voor dit besturingselement.|  
|**Ontgrendeld.**|Gebruik deze eigenschap configureren of de gebruiker zich kan communiceren met het besturingselement. Het besturingselement is standaard ingeschakeld. Deze knop wordt weergegeven voor de volgende statussen:<br /><br /> -                                  **Ontgrendeld.** Het besturingselement is ingeschakeld en gebruikers met behulp van deze gegevens kunnen opgeven.<br /><br /> -                                  **Vergrendeld.** Het besturingselement is uitgeschakeld en gebruikers hebben geen gebruik van informatie op te geven.<br /><br /> **Opmerking** als (vergrendelen) een besturingselement is uitgeschakeld, u moet de gegevens opgeven het besturingselement dat is verzameld door MDT-eigenschappen te configureren in CustomSettings.ini of in de MDT-database. Anders de benodigde informatie worden niet verzameld door de Wizard UDI en mislukt de implementatie UDI.|  

####  <a name="BitmapControl"></a>Bitmap-besturingselement  
 Dit besturingselement kunt u een bitmapafbeelding (bmp-bestand) toevoegen aan de aangepaste wizardpagina. Dit besturingselement verzamelt niet alle configuratiewaarden, maar in plaats daarvan wordt gebruikt voor het verbeteren van de gebruikersinterface visueel.  

##### <a name="layout-properties"></a>Outeigenschappen van de lay  
 Eigenschappen voor de indeling gebruikt voor het configureren van de kenmerken van de gebruikersinterface van het besturingselement en zijn geconfigureerd op de **lay-out** tabblad in de waarde van de Wizard UDI. 54 tabel bevat de eigenschappen van de lay-out voor de **Bitmap** beheren en bevat een korte beschrijving van elke eigenschap.  

### <a name="table-54-bitmap-control-layout-properties"></a>Tabel 54. Bitmap besturingselementeigenschappen lay-out  

|**Eigenschap**|**Beschrijving**|  
|-|-|  
|**X**|Gebruik deze eigenschap voor het configureren van de horizontale positie van het besturingselement.|  
|**Y**|Gebruik deze eigenschap voor het configureren van de verticale positie van het besturingselement.|  
|**Breedte**|Gebruik deze eigenschap voor het configureren van de breedte van het besturingselement.<br /><br /> **Opmerking** als de afbeelding is geselecteerd in de **bron** eigenschap langer is dan de breedte van het besturingselement, de afbeelding is afgekapt.|  
|**Hoogte**|Gebruik deze eigenschap voor het configureren van de hoogte van het besturingselement.<br /><br /> **Opmerking** als de afbeelding is geselecteerd in de **bron** eigenschap groter is dan de hoogte van het besturingselement, de afbeelding is afgekapt.|  
|**Bron**|Gebruik deze eigenschap voor het configureren van de volledig gekwalificeerde pad naar het bmp-bestand, inclusief de bestandsnaam. Het pad naar het bmp-bestand is gebaseerd op de locatie van de Wizard UDI (OSDSetupWizard.exe), die zich op een van de volgende mappen (waarbij *mdt_tookit_package* is de locatie van het pakket met MDT toolkit in Configuration Manager):<br /><br /> -                                  *mdt_tookit_package*\Tools\x86<br /><br /> -                                  *mdt_tookit_package*\Tools\x64<br /><br /> Als u wilt weergeven in de afbeelding als een voorbeeldweergave van de aangepaste wizardpagina, BMP-bestand moet ook bevinden in de volgende mappen (waarbij *mdt_install_folder* is de map waarin u MDT hebt geïnstalleerd):<br /><br /> -                                  *mdt_install_folder*\Template\Distribution\Tools\x86<br /><br /> -                                  *mdt_install_folder* \Template\Distribution\Tools\x64|  

##### <a name="settings-properties"></a>Eigenschappen van clientstatusinstellingen  
 De **Bitmap** besturingselement heeft geen eigenschappen instellingen.  

####  <a name="TextboxControl"></a>TextBox-besturingselement  
 Dit besturingselement kunt u tekst op de pagina wizard Aangepaste invoeren. De tekst die in dit besturingselement getypt wordt opgeslagen in de takenreeksvariabele die is geconfigureerd voor dit besturingselement.  

##### <a name="layout-properties"></a>Outeigenschappen van de lay  
 Eigenschappen voor de indeling gebruikt voor het configureren van de kenmerken van de gebruikersinterface van het besturingselement en zijn geconfigureerd op de **lay-out** tabblad in de waarde van de Wizard UDI. 55 tabel bevat de eigenschappen van de lay-out voor de **Textbox** beheren en bevat een korte beschrijving van elke eigenschap.  

### <a name="table-55-textbox-control-layout-properties"></a>Tabel 55. Eigenschappen van besturingselement TextBox-indeling  

|**Eigenschap**|**Beschrijving**|  
|-|-|  
|**X**|Gebruik deze eigenschap voor het configureren van de horizontale positie van het besturingselement.|  
|**Y**|Gebruik deze eigenschap voor het configureren van de verticale positie van het besturingselement.|  
|**Breedte**|Gebruik deze eigenschap voor het configureren van de breedte van het besturingselement.<br /><br /> **Opmerking** als de tekst die is ingevoerd in het besturingselement langer dan de breedte van het besturingselement is, de tekst wordt afgekapt en niet weergegeven.|  
|**Hoogte**|Gebruik deze eigenschap voor het configureren van de hoogte van het besturingselement.<br /><br /> **Opmerking** als de tekst die is ingevoerd in het besturingselement groter dan de hoogte van het besturingselement is, de tekst wordt afgekapt.|  

##### <a name="settings-properties"></a>Eigenschappen van clientstatusinstellingen  
 Eigenschappen van de instellingen worden gebruikt voor het configureren van de gegevens die in eerste instantie wordt weergegeven in een besturingselement (de standaardwaarde) en waar de gegevens die worden verzameld van de gebruiker wordt opgeslagen. 56 tabel bevat de eigenschappen van de instellingen voor de **Textbox** beheren en bevat een korte beschrijving van elke eigenschap  

### <a name="table-56-textbox-control-settings-properties"></a>Tabel 56. Eigenschappen voor besturingselement TextBox  

|**Eigenschap**|**Beschrijving**|  
|-|-|  
|**Standaardwaarde**|Gebruik deze eigenschap voor het configureren van de standaardwaarde voor het besturingselement.|  
|**Variabele naam op van takenreeks**|Deze eigenschap gebruiken voor het configureren van de takenreeksvariabele waar de informatie die verzameld van de gebruiker wordt opgeslagen. Als de variabele voor de takenreeks:<br /><br /> -Biedt nog niet bestaat, wordt de takenreeksvariabele gemaakt en is ingesteld op de waarde van de gebruiker biedt<br /><br /> -Bestaat al, de bestaande waarde van de takenreeksvariabele wordt overschreven met de waarde die de gebruiker|  
|**Beschrijvende weergavenaam zichtbaar in de pagina overzicht**|Gebruik deze eigenschap voor het configureren van de beschrijvende naam die wordt weergegeven op de **samenvatting** wizardpagina. Deze naam wordt gebruikt om te beschrijven van de waarde die is opgeslagen in de **variabele naam op van Takenreeks** eigenschap voor dit besturingselement.|  
|**Lijst met validatiefuncties toegewezen aan dit besturingselement**|Deze eigenschap bevat een lijst met validatiefuncties gebruikt om te controleren of de inhoud die is opgegeven in het tekstvak.<br /><br /> U kunt het volgende doen:<br /><br /> -Validatiefuncties aan de lijst met de knop blauw plusteken onmiddellijk aan de rechterkant van de lijst met validatiefuncties toevoegen<br /><br /> -Validators bestaat in de lijst met de knop Pen onmiddellijk aan de rechterkant van de lijst met validatiefuncties bewerken<br /><br /> -Validatiefuncties verwijderen uit de lijst met de rode **X** knop onmiddellijk aan de rechterkant van de lijst met validatiefuncties|  
|**Ontgrendeld.**|Gebruik deze eigenschap configureren of de gebruiker zich kan communiceren met het besturingselement. Het besturingselement is standaard ingeschakeld. Deze knop wordt weergegeven voor de volgende statussen:<br /><br /> - **Ontgrendeld.** Het besturingselement is ingeschakeld en gebruikers met behulp van deze gegevens kunnen opgeven.<br /><br /> -                                  **Vergrendeld.** Het besturingselement is uitgeschakeld en gebruikers hebben geen gebruik van informatie op te geven.<br /><br /> Opmerking:<br /><br /> **Opmerking** als (vergrendelen) een besturingselement is uitgeschakeld, u moet de gegevens opgeven het besturingselement dat is verzameld door MDT-eigenschappen te configureren in CustomSettings.ini of in de MDT-database. Anders de benodigde informatie worden niet verzameld door de Wizard UDI en mislukt de implementatie UDI.|  

###  <a name="UDITaskSequenceVariables"></a>UDI Takenreeksvariabelen  
 De takenreeksvariabelen in deze sectie worden alleen gebruikt in implementaties van UDI (User Driven installatie). Naast deze takenreeksvariabelen, is de volgende ZTI takenreeksvariabelen worden ook gebruikt door UDI en in hun respectieve secties eerder in deze handleiding worden beschreven:  

-   [KeyboardLocale](#KeyboardLocale)  

-   [OSDComputerName](#OSDComputerName)  

-   [UILanguage](#UILanguage)  

-   [UserLocale](#UserLocale)  

####  <a name="OSDAddAdmin"></a>OSDAddAdmin  
 Deze takenreeksvariabele geeft een lijst met accounts op basis van een domein of lokale accounts moeten worden toegevoegd aan de lokale ingebouwde groep Administrators op de doelcomputer.  

|**Waarde**|**Beschrijving**|  
|-|-|
|*domain\account_name1; computer\account_name2*|De indeling van de accounts die leden van de groep Administrators op de doelcomputer in de indeling van *domein\account* en gescheiden door puntkomma's, waarbij *domein* mag de naam van een actieve Directory-domein of de naam van de doelcomputer.|  

|**Voorbeeld**|  
|-|  
|`OSDAddAdmin=domain\user01;Win7-01\LocalUser01`|  

####  <a name="OSDApplicationList"></a>OSDApplicationList  
 Deze takenreeksvariabele geeft aan welke toepassingen moeten worden geselecteerd standaard op de **Software installeren** pagina van de Setup-Wizard besturingssysteem-implementatie (OSD).  

|**Waarde**|**Beschrijving**|  
|-|-|
|*app_id1; app_id2*|Een met puntkomma's gescheiden lijst van de toepassing standaard is ingeschakeld op de **Software installeren** pagina van de Wizard Setup van besturingssysteem-implementatie (OSD); elke toepassing wordt vertegenwoordigd door een toepassings-ID en gescheiden door een puntkomma. De toepassings-ID is afgeleid van de **Id** kenmerk van elke toepassing in het bestand UDIWizard_Config.xml. In het volgende fragment uit een bestand UDIWizard_Config.xml, de Microsoft Office 2007 met SP2-toepassing heeft een **Id** kenmerk van **1**:<br /><br /> `<Application DisplayName="Office 2007 SP2" State="Disabled" Id="1">`|  

|**Voorbeeld**|  
|-|  
|`OSDApplicationList=2;3`|  

####  <a name="OSDArchitecture"></a>OSDArchitecture  
 Deze takenreeksvariabele geeft de processorarchitectuur van het beoogde besturingssysteem om te worden geïmplementeerd.  

|**Waarde**|**Beschrijving**|  
|-|-|
|x86|Het beoogde besturingssysteem is een 32-bits besturingssysteem.|  
|AMD64|Het beoogde besturingssysteem is een 64-bits besturingssysteem.|  

|**Voorbeeld**|  
|-|  
|`OSDArchitecture=amd64`|  

####  <a name="OSDBitlockerStatus"></a>OSDBitlockerStatus  
 Deze takenreeksvariabele geeft als BitLocker is ingeschakeld op de doelcomputer door BitLocker controle.  

|**Waarde**|**Beschrijving**|  
|-|-|
|**BEVEILIGD**|De doelcomputer is BitLocker ingeschakeld.|  
|Bestaat niet|Als de doelcomputer geen BitLocker is ingeschakeld, klikt u vervolgens bestaat de takenreeksvariabele niet.|  

|**Voorbeeld**|  
|-|  
|Geen|  

####  <a name="OSDDiskPart"></a>OSDDiskPart  
 Deze takenreeksvariabele geeft aan of de schijf doelpartitie moet worden ingedeeld.  

|**Waarde**|**Beschrijving**|  
|-|-|
|**DE WAARDE TRUE**|De doelpartitie schijf wordt geformatteerd.|  
|**DE WAARDE FALSE**|De doel-schijfpartitie niet geformatteerd.|  

|**Voorbeeld**|  
|-|  
|`OSDDiskPart=TRUE`|  

####  <a name="OSDDomainName"></a>OSDDomainName  
 Deze takenreeksvariabele geeft de naam van het domein waaraan de doelcomputer worden gekoppeld als de computer is geconfigureerd als lid van een domein.  

|**Waarde**|**Beschrijving**|  
|-|-|
|*domeinnaam*|De naam van het domein waaraan de doelcomputer worden gekoppeld. Als u hebt geconfigureerd de **Computer** wizardpagina in de installatiewizard besturingssysteem-implementatie (OSD) worden **achtergrond**, de waarde in deze takenreeksvariabele moet overeenkomen met de opgegeven waarden in de UDI Wizard Designer. Anders wordt wordt de pagina van de wizard weergegeven.<br /><br /> Opmerking:<br /><br /> Deze takenreeksvariabele is alleen nodig wanneer u een nieuwe computeraccount in de organisatie-eenheid maakt. Als het computeraccount al bestaat, wordt deze variabele is niet nodig.|  

|**Voorbeeld**|  
|-|  
|`OSDDomainName=domain01`|  

####  <a name="OSDDomainOUName"></a>OSDDomainOUName  
 Deze takenreeksvariabele geeft de naam van de organisatie-eenheid in het domein waaraan de computeraccount van de doel-wordt gemaakt wanneer de computer lid van een domein.  

|**Waarde**|**Beschrijving**|  
|-|-|
|*naam_organisatie-eenheid*|De naam van de organisatie-eenheid in het domein waarin het computeraccount wordt gemaakt<br /><br /> Opmerking:<br /><br /> Deze takenreeksvariabele is alleen nodig wanneer u een nieuwe computeraccount in de organisatie-eenheid maakt. Als het computeraccount al bestaat, wordt deze variabele is niet nodig.|  

|**Voorbeeld**|  
|-|  
|`OSDDomainOUName=NewDeployOU`|  

####  <a name="OSDImageIndex2"></a>OSDImageIndex  
 Deze takenreeksvariabele geeft het indexnummer van het beoogde besturingssysteem in een WIM-bestand.  

|**Waarde**|**Beschrijving**|  
|-|-|
|*indexnummer*|Het indexnummer van het doel op die begint met indexnummer van 1 voor het eerste besturingssysteem in het WIM-bestand|  

|**Voorbeeld**|  
|-|  
|`OSDImageIndex=1`|  

####  <a name="OSDImageName"></a>OSDImageName  
 Deze takenreeksvariabele geeft de naam van de installatiekopie van het besturingssysteem in het WIM-bestand dat is geselecteerd in de **selectie van een installatiekopie** vak op de [VolumePage](#VolumePage) wizardpagina. De lijst met mogelijke van installatiekopieën van besturingssystemen in de **selectie van een installatiekopie** vak is geconfigureerd in de **waarden van de installatiekopie van keuzelijst met invoervak** lijst de **installatiekopie keuzelijst met invoervak** sectie over de [ VolumePage](#VolumePage) wizard pagina-editor. Naam van de installatiekopie is geconfigureerd als onderdeel van elke installatiekopie in de **waarden van de installatiekopie van keuzelijst met invoervak** lijst.  

> [!NOTE]
>  **Opmerking** deze taken variabele is ingesteld door de [VolumePage](#VolumePage) wizard en moet niet worden geconfigureerd in het CustomSettings.ini-bestand of de MDT-database. Deze variabele taken kan echter worden gebruikt om in te stellen voorwaarden voor stappen voor takenreeksen, zoals beschreven in de sectie ' configureren UDI Taakreeksen te implementeren van verschillende besturingssystemen worden uitgevoerd ', in het document MDT *met behulp van de Microsoft Deployment Toolkit*.  

|**Waarde**|**Beschrijving**|  
|-|-|
|*naam_installatiekopie*|De naam van de installatiekopie van het besturingssysteem in het WIM-bestand dat is geselecteerd in de **selectie van een installatiekopie** vak op de [VolumePage](#VolumePage) wizardpagina|  

|**Voorbeeld**|  
|-|  
|Geen|  

####  <a name="OSDJoinAccount"></a>OSDJoinAccount  
 Deze takenreeksvariabele Hiermee geeft u het account op basis van een domein is gebruikt voor het toevoegen van de doelcomputer aan het domein dat is opgegeven in de **OSDDomainName** takenreeksvariabele. Deze takenreeksvariabele is nodig als de doelcomputer wordt toegevoegd aan een domein.  

|**Waarde**|**Beschrijving**|  
|-|-|
|*accountnaam*|De naam van het account waarmee de doelcomputer toevoegen aan het domein in de indeling van *domein\account*|  

|**Voorbeeld**|  
|-|  
|`OSDJoinAccount=domain\admin01`|  

####  <a name="OSDJoinPassword"></a>OSDJoinPassword  
 Deze takenreeksvariabele geeft het wachtwoord voor het account op basis van een domein is gebruikt voor het toevoegen van de doelcomputer aan het domein dat is opgegeven in de **OSDJoinAccount** takenreeksvariabele. Deze takenreeksvariabele is nodig als de doelcomputer wordt toegevoegd aan een domein.  

|**Waarde**|**Beschrijving**|  
|-|-|
|*wachtwoord*|Het wachtwoord van het account dat aan het domein kan worden gebruikt|  

|**Voorbeeld**|  
|-|  
|`OSDJoinPassword=P@ssw0rd10`|  

####  <a name="OSDLocalAdminPassword"></a>OSDLocalAdminPassword  
 Deze takenreeksvariabele geeft het wachtwoord voor het lokale ingebouwde beheerdersaccount op de doelcomputer.  

|**Waarde**|**Beschrijving**|  
|-|-|
|*wachtwoord*|Het wachtwoord van de lokale ingebouwde beheerdersaccount op de doelcomputer|  

|**Voorbeeld**|  
|-|  
|`OSDLocalAdminPassword=P@ssw0rd10`|  

####  <a name="OSDNetworkJoinType"></a>OSDNetworkJoinType  
 Deze takenreeksvariabele geeft aan of de doelcomputer lid wordt van een domein of werkgroep.  

|**Waarde**|**Beschrijving**|  
|-|-|
|**0**|De doelcomputer lid wordt van een domein.<br /><br /> Als u deze optie selecteert en de bijbehorende besturingssysteem-implementatie (OSD)-installatiewizard pagina te configureren **achtergrond**, u moet ook waarden opgeven voor de **OSDJoinAccount**,  **OSDJoinPassword**, **OSDDomainName**, en **OSDDomainOUName** takenreeksvariabelen dienovereenkomstig. Bovendien moet u **domein** in **standaard selectie** in het deelvenster op de **pagina Computer** in de ontwerpfunctie van de Wizard UDI.|  
|**1**|De doelcomputer lid wordt van een werkgroep.<br /><br /> Als u deze optie selecteert en de bijbehorende besturingssysteem-implementatie (OSD)-installatiewizard pagina te configureren **achtergrond**, u moet ook een waarde opgeven voor de **OSDWorkgroupName** takenreeks variabele. Bovendien moet u **werkgroep** in **standaard selectie** in het deelvenster op de **pagina Computer** in de ontwerpfunctie van de Wizard UDI.|  

|**Voorbeeld**|  
|-|  
|`OSDNetworkJoinType=0`|  

####  <a name="OSDSetupWizCancelled"></a>OSDSetupWizCancelled  
 Deze takenreeksvariabele bevat als de installatiewizard van de besturingssysteem-implementatie (OSD) is geannuleerd door de gebruiker.  

|**Waarde**|**Beschrijving**|  
|-|-|
|**DE WAARDE TRUE**|De installatiewizard van de besturingssysteem-implementatie (OSD) is geannuleerd door de gebruiker.|  
|Bestaat niet|Als de wizard niet is geannuleerd, klikt u vervolgens bestaat de takenreeksvariabele niet.|  

|**Voorbeeld**|  
|-|  
|Geen|  

####  <a name="OSDTargetDrive"></a>OSDTargetDrive  
 Deze takenreeksvariabele Hiermee geeft u het schijfvolume waarop het beoogde besturingssysteem wordt geïmplementeerd.  

|**Waarde**|**Beschrijving**|  
|-|-|
|*disk_volume*|De schijf volume aanwijzing|  

|**Voorbeeld**|  
|-|  
|`OSDTargetDrive=C:`|  

####  <a name="OSDWinPEWinDir"></a>OSDWinPEWinDir  
 Deze takenreeksvariabele geeft de map waarin het besturingssysteem Windows momenteel is geïnstalleerd op de doelcomputer.  

|**Waarde**|**Beschrijving**|  
|-|-|
|*Windows_map*|De map waarin de Windows-besturingssysteem is geïnstalleerd|  

|**Voorbeeld**|  
|-|  
|`OSDWinPEWinDir=C:\Windows`|  

####  <a name="OSDWorkgroupName"></a>OSDWorkgroupName  
 Deze takenreeksvariabele geeft de naam van de werkgroep waaraan de doelcomputer worden toegevoegd als de computer is geconfigureerd als lid van een werkgroep.  

|**Waarde**|**Beschrijving**|  
|-|-|
|*werkgroepnaam*|De naam van de werkgroep waaraan de doelcomputer worden gekoppeld|  

|**Voorbeeld**|  
|-|  
|`OSDWorkgroupName=WORKGROUP01`|  

###  <a name="OSDResultsexeconfigFileElementValues"></a>Waarden van het Element OSDResults.exe.config bestand  
 Het programma OSD-resultaten, OSDResults.exe, aan het einde van een UDI-implementatie wordt uitgevoerd en worden de resultaten van het implementatieproces weergegeven. De werking van de resultaten van de OSD-programma kan worden aangepast door het wijzigen van de waarden van het element OSDResults.exe.config-bestand. Het bestand OSDResults.exe.config wordt opgeslagen in Tools\OSDResults in de MDT-pakket in de Takenreeks wordt gebruiker station-installatie.  

####  <a name="backgroundOpacity"></a>backgroundOpacity  
 Dit XML-element configureert u de opaqueness van de achtergrondafbeelding van de achtergrond opgegeven als een percentage decimal-indeling in de **backgroundWallpaper** element.  

|**Waarde**|**Beschrijving**|  
|-|-|
|*opacity_percent*|Het percentage van de opaqueness van de **backgroundWallpaper** opgegeven element in een decimaal opgemaakte percentage — bijvoorbeeld een waarde van **0,8** 80% opaqueness aanwijst.|  

|**Voorbeeld**|  
|-|  
|`<add key="backgroundOpacity" value="0.8"/>`|  

####  <a name="backgroundWallpaper"></a>backgroundWallpaper  
 Dit XML-element bevat de bestandsnaam en het relatieve pad naar de afbeelding die wordt weergegeven als achtergrond in de **OSD resultaten** in het dialoogvenster. Het pad is ten opzichte van de map Tools\OSDResults in de MDT-pakket.  

|**Waarde**|**Beschrijving**|  
|-|-|
|*pad\\\file_name*|Bevat het relatieve pad en bestandsnaam van de achtergrondafbeelding; het pad wordt gescheiden met dubbele slashes (/ /).|  

|**Voorbeeld**|  
|-|  
|`<add key="backgroundWallpaper" value="images\\Wallpaper.jpg"/>`|  

####  <a name="completedText"></a>completedText  
 Dit XML-element bevat de tekst die wordt weergegeven in de **OSD resultaten** in het dialoogvenster wanneer de implementatie voltooid is.  

|**Waarde**|**Beschrijving**|  
|-|-|
|*tekst*|De tekst die moet worden weergegeven in de **OSD resultaten** dialoogvenster in aanhalingstekens markeert wanneer de implementatie is voltooid|  

|**Voorbeeld**|  
|-|  
|`<add key="completedText" value="Deployment Complete"/>`|  

####  <a name="headerImagePath"></a>headerImagePath  
 Dit XML-element bevat de bestandsnaam en het relatieve pad naar de afbeelding die wordt weergegeven in de koptekst van de **OSD resultaten** in het dialoogvenster. Het pad is ten opzichte van de map Tools\OSDResults in de MDT-pakket.  

|**Waarde**|**Beschrijving**|  
|-|-|
|*pad\\\file_name*|Bevat het relatieve pad en bestandsnaam van de header-afbeelding. het pad wordt gescheiden door dubbele (\\\\).|  

|**Voorbeeld**|  
|-|  
|`<add key="headerImagePath" value="images\\Windows7_h_rgb.png"/>`|  

####  <a name="timeoutMinutes"></a>timeoutMinutes  
 Dit XML-element wordt geconfigureerd hoeveel minuten de **OSD resultaat** in het dialoogvenster wordt weergegeven voordat het dialoogvenster automatisch wordt gesloten en de computer opnieuw is opgestart.  

|**Waarde**|**Beschrijving**|  
|-|-|
|*Niet-numerieke waarde*|Er wordt een dialoogvenster vak blijft geopend tot **Windows starten** wordt geklikt.|  
|*Negatieve waarde*|Er wordt een dialoogvenster vak blijft geopend tot **Windows starten** wordt geklikt.|  
|**0**|Er wordt een dialoogvenster vak blijft geopend tot **Windows starten** wordt geklikt.|  
|Decimaalteken opnemen|Er wordt een dialoogvenster vak blijft geopend tot **Windows starten** wordt geklikt.|  
|**1 - 10080**|Het aantal minuten die in het dialoogvenster wordt weergegeven, met minimaal de waarde van 1 minuut en de maximale waarde is 10080 minuten (1 week).|  

|**Voorbeeld**|  
|-|  
|`<add key="timeoutMinutes" value="30"/>`|  

####  <a name="welcomeText"></a>welcomeText  
 Dit XML-element bevat de Welkom tekst die wordt weergegeven in de **OSD resultaten** in het dialoogvenster.  

|**Waarde**|**Beschrijving**|  
|-|-|
|*welcome_text*|De Welkom tekst die moet worden weergegeven in de **OSD resultaten** dialoogvenster aanhalingstekens worden geplaatst|  

|**Voorbeeld**|  
|-|  
|`<add key="welcomeText" value="Congratulations, Windows 7 has been successfully deployed to your computer."/>`|
