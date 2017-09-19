---
title: Eigenschappen van clientinstallatie | Microsoft Docs
description: Meer informatie over eigenschappen van clientinstallatie in System Center Configuration Manager.
ms.custom: na
ms.date: 01/04/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: configmgr-client
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: c890fd27-7a8c-4f51-bbe2-f9908af1f42b
caps.latest.revision: "15"
author: arob98
ms.author: angrobe
manager: angrobe
ms.openlocfilehash: 5148fe852e4d63e1cfd2d5b9c62369155dbecb89
ms.sourcegitcommit: b438515490e04fb09c82a8af642d38e9a0605178
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 09/15/2017
---
# <a name="about-client-installation-properties-in-system-center-configuration-manager"></a>Over de eigenschappen van clientinstallatie in System Center Configuration Manager

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*

Gebruik de opdracht CCMSetup.exe van System Center Configuration Manager Configuration Manager-client handmatig te installeren.  

##  <a name="aboutCCMSetup"></a> Over CCMSetup.exe  
 De opdracht CCMSetup.exe downloadt benodigde bestanden voor het installeren van de client van een beheerpunt of een bronlocatie. Deze bestanden kunnen onder andere:  

-   Het Windows Installer-pakket Client.msi dat de clientsoftware wordt geïnstalleerd.  

-   Microsoft Background Intelligent Transfer Service (BITS)-installatiebestanden.  

-   Windows Installer-installatiebestanden.  

-   Updates en oplossingen voor de Configuration Manager-client.  

> [!NOTE]  
>  In Configuration Manager u kan niet rechtstreeks worden uitgevoerd de Client.msi-bestand.  

 CCMSetup.exe biedt [opdrachtregeleigenschappen](#ccmsetup-exe-command-line-properties) voor het aanpassen van de installatie. U kunt ook eigenschappen voor het wijzigen van het gedrag van Client.msi op de CCMSetup.exe-opdrachtregel opgeven.  

> [!IMPORTANT]  
>  CCMSetup-eigenschappen opgeven voordat u de eigenschappen voor Client.msi opgeven.  

 CCMSetup.exe en de ondersteunende bestanden bevinden zich op de siteserver van Configuration Manager in de **Client** map van de installatiemap van Configuration Manager. Deze map wordt gedeeld met het netwerk als ** &lt;Siteservernaam\>\SMS_&lt;sitecode\>\Client**.  

 Aan de opdrachtregel gebruikt de opdracht CCMSetup.exe de volgende indeling:  

 `CCMSetup.exe [<Ccmsetup properties>] [<client.msi setup properties>]`  

 Voorbeeld:  

 ' CCMSetup.exe/MP: smsmp01/Logon SMSSITECODE = S01 FSP = SMSFSP01'  

 In dit voorbeeld doet het volgende:  

-   Hiermee geeft u het beheerpunt smsmp01 om te vragen van een lijst van distributiepunten om de clientinstallatiebestanden te downloaden.  

-   Hiermee geeft u op dat de installatie moet worden stopgezet als er al een versie van de client op de computer bestaat.  

-   Geeft client.msi de instructie om de client toe te wijzen aan de sitecode S01.  

-   Hiermee ontvangt client.msi de instructie het terugvalstatuspunt SMSFP01 te gebruiken.  

> [!NOTE]  
>  Als een eigenschap spaties bevat, eromheen tussen aanhalingstekens.  


> [!IMPORTANT]  
>  Als u de Active Directory-schema voor Configuration Manager hebt uitgebreid, worden veel clientinstallatie-eigenschappen gepubliceerd in Active Directory Domain Services en automatisch gelezen door de Configuration Manager-client. Zie [About client installation properties published to Active Directory Domain Services in System Center Configuration Manager](about-client-installation-properties-published-to-active-directory-domain-services.md) (Over eigenschappen van clientinstallaties die zijn gepubliceerd naar Active Directory Domain Services in System Center Configuration Manager) voor meer informatie over de eigenschappen van de clientinstallatie die worden gepubliceerd Active Directory Domain Services.  

##  <a name="ccmsetupexe-command-line-properties"></a>Opdrachtregeleigenschappen van CCMSetup.exe  

### <a name=""></a>/?  

Opent het dialoogvenster **CCMSetup** met opdrachtregeleigenschappen voor ccmsetup.exe.  

Voorbeeld: **ccmsetup.exe /?**  

### <a name="sourceltpath"></a>/ source:&lt;pad\>  

 Hiermee geeft u de locatie van het bestand downloaden. Een lokaal of UNC-pad gebruiken. Bestanden worden gedownload met behulp van het protocol server message block (SMB).  Gebruik **/source**, de Windows-gebruikersaccount voor clientinstallatie moet leesmachtigingen hebben voor de locatie.

> [!NOTE]  
>  U kunt de **/source** eigenschap meerdere keren in een opdrachtregel van alternatieve downloadlocaties op te geven.  

 Voorbeeld: **ccmsetup.exe /source: "\\\computer\map"**  

### <a name="mpltcomputer"></a>/MP:&lt;computer\>

 Specificeert een bronbeheerpunt voor computers die u wilt verbinden, zodat ze het dichtstbijzijnde distributiepunt voor de installatiebestanden vinden kunnen. Clients downloaden de bestanden vanaf het opgegeven beheerpunt als er geen distributiepunten zijn of als computers de bestanden niet kunnen downloaden van de distributiepunten na 4 uur.  

> [!IMPORTANT]  
>  Deze eigenschap wordt gebruikt om een initieel beheerpunt voor computers om te vinden van een bron downloaden geven en een beheerpunt in eender welke site. Dit niet het *toewijzen* de client naar een beheerpunt.   

 Computers downloaden de bestanden via een HTTP- of HTTPS-verbinding, afhankelijk van de sitesysteemrolconfiguratie voor clientverbindingen. De download gebruikt BITS-beperking, indien geconfigureerd. Als alle distributiepunten en beheerpunten voor alleen HTTPS-clientverbindingen zijn geconfigureerd, moet u controleren of de clientcomputer een geldig clientcertificaat heeft.  

U kunt de **/mp** -opdrachtregeleigenschap gebruiken om meerdere beheerpunten op te geven zodat de computer, als deze niet kan verbinden met het eerste beheerpunt, verbinding probeert te maken met het volgende beheerpunt, enzovoort. Wanneer u meerdere beheerpunten opgeeft, scheidt u de waarden door puntkomma's.

Als de client verbinding maakt met een beheerpunt via HTTPS normaal gesproken moet u de FQDN-naam, niet de naam van de computer. De waarde moet overeenkomen met het beheerpunt PKI-certificaat onderwerpnaam of alternatieve onderwerpnaam. Hoewel een FQDN-naam in Configuration Manager ondersteunt het gebruik van een computernaam in het certificaat voor verbindingen op het intranet als een best practice bij beveiliging wordt aangeraden.

Voorbeeld voor wanneer u de computernaam gebruikt:`ccmsetup.exe /mp:SMSMP01`  

Voorbeeld voor wanneer u de FQDN-naam gebruikt:`ccmsetup.exe /mp:smsmp01.contoso.com`  

### <a name="retryltminutes"></a>/ opnieuw proberen:&lt;minuten\>

Het interval voor opnieuw proberen als CCMSetup.exe mislukt installatiebestanden moeten worden gedownload.  CCMSetup blijft het opnieuw proberen totdat het de limiet die is opgegeven in bereikt de **downloadtimeout** eigenschap.  

Voorbeeld: `ccmsetup.exe /retry:20`  

### <a name="noservice"></a>/noservice

Voorkomt dat CCMSetup wordt uitgevoerd als een service die de standaardeigenschap. Als CCMSetup een service uitvoert, wordt deze wordt uitgevoerd in de context van het lokale systeemaccount van de computer, die mogelijk niet over voldoende rechten voor toegang tot de benodigde netwerkbronnen voor de installatie. Met **/noservice**, CCMSetup.exe wordt uitgevoerd in de context van het gebruikersaccount dat u gebruikt om de installatie te starten. Ook als u een script gebruiken om uit te voeren CCMSetup.exe met de **/service** eigenschap, wordt CCMSetup.exe afgesloten nadat de service is gestart en mogelijk installatiegegevens niet correct.   

Voorbeeld: `ccmsetup.exe /noservice`  

### <a name="service"></a>/service

Specificeert dat CCMSetup moet worden uitgevoerd als een service die het lokale systeemaccount gebruikt.  

Voorbeeld: `ccmsetup.exe /service`  

### <a name="uninstall"></a>/uninstall

Hiermee geeft u op dat de clientsoftware moet worden verwijderd. Zie [How to manage clients in System Center Configuration Manager](../manage/manage-clients.md) (Clients beheren in System Center Configuration Manager) voor meer informatie.  

Voorbeeld: `ccmsetup.exe /uninstall`  

### <a name="logon"></a>/logon

Hiermee geeft u op dat de clientinstallatie moet worden stopgezet als een willekeurige versie van de client al is geïnstalleerd.  

Voorbeeld: `ccmsetup.exe /logon`  

### <a name="forcereboot"></a>/forcereboot

 Specificeert dat CCMSetup de clientcomputer opnieuw op te starten als dat nodig is om de installatie te voltooien moet dwingen. Als dit niet is opgegeven, wordt CCMSetup afgesloten wanneer opnieuw opstarten nodig is, klikt u vervolgens blijft na de volgende handmatig opnieuw worden gestart.  

 Voorbeeld: `CCMSetup.exe /forcereboot`  

### <a name="bitspriorityltpriority"></a>/ BITSPriority:&lt;prioriteit\>

 Specificeert de downloadprioriteit wanneer clientinstallatiebestanden worden gedownload via een HTTP-verbinding. Mogelijke waarden zijn als volgt:  

-   FOREGROUND  

-   HIGH  

-   NORMAL  

-   LOW  

 De standaardwaarde is NORMAL.  

 Voorbeeld: `ccmsetup.exe /BITSPriority:HIGH`  

### <a name="downloadtimeoutltminutes"></a>/ downloadtimeout:&lt;minuten\>

De tijdsduur in minuten over hoelang CCMSetup moet proberen te downloaden van de installatiebestanden voor het stoppen. De standaardwaarde is **1440** minuten (1 dag).  

Voorbeeld: `ccmsetup.exe /downloadtimeout:100`  

### <a name="usepkicert"></a>/UsePKICert

 Als u opgeeft, gebruikt de client een PKI-certificaat dat clientverificatie bevat, indien beschikbaar. Als een geldig certificaat kan niet worden gevonden, gebruikt de client een HTTP-verbinding en een zelfondertekend certificaat dat ook het gedrag is wanneer u deze eigenschap niet gebruikt.

> [!NOTE]  
>  In sommige scenario's u niet moet deze eigenschap opgeven wanneer u een client installeert op en nog steeds een clientcertificaat te gebruiken. Deze scenario's omvatten een client installeert met behulp van clientpush en op basis van client-installatie van software-update. U moet deze eigenschap echter opgeven wanneer u een client handmatig installeert en de eigenschap **/mp** gebruikt om een beheerpunt te specificeren dat is geconfigureerd om alleen HTTPS-clientverbindingen te accepteren. U moet deze eigenschap ook specificeren wanneer u een client installeert voor communicatie alleen via het internet, door gebruik te maken van de eigenschap CCMALWAYSINF=1 (samen met de eigenschappen voor het beheerpunt op internet en de sitecode). Zie [Overwegingen voor clientcommunicatie via internet of een niet-vertrouwd forest](../../plan-design/hierarchy/communications-between-endpoints.md#BKMK_clientspan) in [De communicatie tussen de eindpunten in System Center Configuration Manager](../../plan-design/hierarchy/communications-between-endpoints.md) voor meer informatie over clientbeheer via internet.  

 Voorbeeld: `CCMSetup.exe /UsePKICert`  

### <a name="nocrlcheck"></a>/NoCRLCheck

 Hiermee geeft u op dat een client niet de certificaatintrekkingslijst (CRL) controleren moet wanneer deze via HTTPS met PKI-certificaat communiceert.  

 Als niet wordt opgegeven, controleert de client de CRL voordat er een HTTPS-verbinding.  

 Zie [Planning voor PKI-certificaatintrekking](../../plan-design/security/plan-for-security.md#BKMK_PlanningForCRLs) in [De beveiliging plannen in System Center Configuration Manager](../../plan-design/security/plan-for-security.md) voor meer informatie over de CRL-controle voor clients.  

 Voorbeeld: `CCMSetup.exe /UsePKICert /NoCRLCheck`  

### <a name="configltconfiguration-file"></a>/ config:&lt;configuratiebestand\>

Specificeert de naam van een tekstbestand dat de clientinstallatie-eigenschappen bevat.

- Als u geen opgeeft de **/noservice** CCMSetup-eigenschap, moet dit bestand zich in de CCMSetup-map % Windir %\\Ccmsetup voor 32-bits en 64-bits besturingssystemen.
- Als u de eigenschap **/noservice** specificeert, moet dit bestand zich in dezelfde map bevinden van waaruit u CCMSetup.exe uitvoert.  

Voorbeeld: `CCMSetup.exe /config:&lt;Configuration File Name.txt\>`  

Gebruik het bestand mobileclienttemplate.tcf in de &lt;Configuration Manager-map\>\\bin\\&lt;platform\> map op de siteservercomputer om de juiste indeling. Dit bestand bevat ook de opmerkingen over de secties en hoe ze worden gebruikt. Geef de clientinstallatie-eigenschappen in de sectie [Client installeren] na de volgende tekst: **Installeer = INSTALL = ALL**.  

Invoer voor de sectie [Client installeren] Voorbeeld:`Install=INSTALL=ALL SMSSITECODE=ABC SMSCACHESIZE=100`  

### <a name="skipprereqltfilename"></a>/ skipprereq:&lt;filename\>

 Hiermee geeft u op dat CCMSetup.exe niet het opgegeven vereiste programma installeren moet wanneer de Configuration Manager-client is geïnstalleerd. Deze eigenschap ondersteunt de invoer van meerdere waarden. Gebruik de puntkomma (;) als scheidingsteken tussen elke waarde.  


 Voorbeelden: `CCMSetup.exe /skipprereq:silverlight.exe` of`CCMSetup.exe /skipprereq:dotnetfx40_client_x86_x64.exe;Silverlight.exe`  

### <a name="forceinstall"></a>/forceinstall

 Opgeven dat een bestaande client zal worden verwijderd en een nieuwe client wordt geïnstalleerd.  

### <a name="excludefeaturesltfeature"></a>/ ExcludeFeatures:&lt;functie\>

Hiermee geeft u op dat CCMSetup.exe niet het opgegeven onderdeel wordt geïnstalleerd wanneer de client is geïnstalleerd.  

Voorbeeld: `CCMSetup.exe /ExcludeFeatures:ClientUI` zal het Software Center niet installeren op de client.  

> [!NOTE]  
>  Voor deze release is **ClientUI** de enige waarde die wordt ondersteund met de eigenschap **/ExcludeFeatures** .  

##  <a name="ccmsetupReturnCodes"></a> Retourcodes van CCMSetup.exe  
 De opdracht CCMSetup.exe biedt dat de volgende retourcodes voltooid. Om op te lossen, controleert u het bestand ccmsetup.log op de clientcomputer voor context en aanvullende details over retourcodes.  

|Retourcode|Betekenis|  
|-----------------|-------------|  
|0|Geslaagd|  
|6|Fout|  
|7|Opnieuw opstarten is vereist|  
|8|Setup wordt reeds uitgevoerd|  
|9|Fout bij evaluatie van vereisten|  
|10|De hash-validatie is mislukt voor Setup-manifest|  

##  <a name="clientMsiProps"></a> Eigenschappen van client.msi  
 De volgende eigenschappen kunnen het installatiegedrag van client.msi wijzigen. Als u de clientpushinstallatie gebruikt, kunt u de eigenschappen ook opgeven in het tabblad **Client** van het dialoogvenster **Clientpushinstallatie-eigenschappen** .  

### <a name="ccmadmins"></a>CCMADMINS  

Geeft een of meerdere Windows-gebruikersaccounts of -groepen om toegang te krijgen tot clientinstellingen en beleidsregels. Dit is handig wanneer de Configuration Manager-beheerder heeft geen lokale beheerdersreferenties op de clientcomputer. Geef een lijst met accounts die worden gescheiden door puntkomma's.  

Voorbeeld: `CCMSetup.exe CCMADMINS="Domain\Account1;Domain\Group1"`  

### <a name="ccmallowsilentreboot"></a>CCMALLOWSILENTREBOOT

Hiermee geeft u op dat de computer opnieuw mag worden opgestart na de clientinstallatie, indien nodig.  

> [!IMPORTANT]  
>  De computer wordt opnieuw opgestart zonder waarschuwing zelfs als een gebruiker is aangemeld.  

Voorbeeld: **CCMSetup.exe CCMALLOWSILENTREBOOT**  

### <a name="ccmalwaysinf"></a>CCMALWAYSINF

 Stel in op 1 om op te geven dat de client altijd met internet verbinding zal maken en nooit met het intranet. Het verbindingstype van de client geeft **Altijd internet**weer.  

 Deze eigenschap moet worden gebruikt in combinatie met CCMHOSTNAME, welke de FQDN-naam van het beheerpunt op internet specificeert. Deze eigenschap moet ook worden gebruikt in combinatie met de CCMSetup-eigenschap /UsePKICert en met de sitecode.  

 Zie [Overwegingen voor clientcommunicatie via internet of een niet-vertrouwd forest](../../plan-design/hierarchy/communications-between-endpoints.md#BKMK_clientspan) in [De communicatie tussen de eindpunten in System Center Configuration Manager](../../plan-design/hierarchy/communications-between-endpoints.md) voor meer informatie over clientbeheer via internet.  

 Voorbeeld: `CCMSetup.exe /UsePKICert  CCMALWAYSINF=1 CCMHOSTNAME=SERVER3.CONTOSO.COM SMSSITECODE=ABC`  

### <a name="ccmcertissuers"></a>CCMCERTISSUERS

 Hiermee geeft u de lijst met certificaatverleners, dit is een lijst met vertrouwde certificeringsinstantie (CA) basiscertificaten dat de Configuration Manager-site vertrouwt.  

 Zie [Planning voor de selectie van PKI-clientcertificaten](../../plan-design/security/plan-for-security.md#BKMK_PlanningForClientCertificateSelection) in [De beveiliging plannen in System Center Configuration Manager](../../plan-design/security/plan-for-security.md) voor meer informatie over de lijst van certificaatverleners en over hoe clients deze lijst gebruiken tijdens het selectieproces van certificaten.  

 Dit is een hoofdlettergevoelige overeenkomst voor onderwerpattributen die zich in het basis-CA-certificaat bevinden. Attributen kunnen worden gescheiden door een komma (,) of een puntkomma (;). Er kunnen meerdere basis-CA-certificaten worden opgegeven door gebruik te maken van een scheidingsbalk. Voorbeeld:  

 `CCMCERTISSUERS=”CN=Contoso Root CA; OU=Servers; O=Contoso, Ltd; C=US &#124; CN=Litware Corporate Root CA; O=Litware, Inc.”`  

> [!TIP]  
>  Raadpleeg het bestand mobileclient.tcf in de &lt;Configuration Manager-map\>\bin\\&lt;platform\> map op de site server-computer kopiëren van de **CertificateIssuers =&lt;tekenreeks\> ** die is geconfigureerd voor de site.  

### <a name="ccmcertsel"></a>CCMCERTSEL

 Hiermee geeft u de criteria voor certificaatselectie als de client heeft meer dan één certificaat voor HTTPS-communicatie (een geldig certificaat met mogelijkheid clientverificatie tot).  

 U kunt zoeken naar een exacte overeenkomst (Gebruik **onderwerp:**) of een gedeeltelijke overeenkomst (Gebruik **SubjectStr:)** in de onderwerpnaam of alternatieve onderwerpnaam. Voorbeelden:  

 `CCMCERTSEL="Subject:computer1.contoso.com"`Hiermee zoekt u naar een certificaat met een exacte overeenkomst voor de computernaam "computer1.contoso.com" in de onderwerpnaam of alternatieve onderwerpnaam.  

 `CCMCERTSEL="SubjectStr:contoso.com"`Hiermee zoekt u naar een certificaat dat "contoso.com" in de onderwerpnaam of alternatieve naam voor onderwerp bevat.  

 U kunt ook attributen van de object-id (OID) of DN-naam gebruiken in de onderwerpnaam of alternatieve naam van het onderwerp. Bijvoorbeeld:  

 `CCMCERTSEL="SubjectAttr:2.5.4.11 = Computers"`Hiermee zoekt u naar het attribuut organisatie-eenheid uitgedrukt als een object-id en met de naam Computers.  

 `CCMCERTSEL="SubjectAttr:OU = Computers"`Hiermee zoekt u naar het attribuut organisatie-eenheid uitgedrukt als een DN-naam en met de naam Computers.  

> [!IMPORTANT]  
>  Als u het vak onderwerpnaam gebruikt de **onderwerp:** hoofdlettergevoelig, en de **SubjectStr:** is niet hoofdlettergevoelig.  
>   
>  Als u het vak alternatieve onderwerpnaam gebruikt de **onderwerp:**en de **SubjectStr:** zijn niet hoofdlettergevoelig.  

 De volledige lijst van kenmerken die u gebruikt voor certificaatselectie staat in [Ondersteunde kenmerkwaarden voor de PKI-certificaatselectiecriteria](#BKMK_attributevalues).  

 Als meer dan één certificaat overeenstemt met de zoekopdracht, en de eigenschap CCMFIRSTCERT op 1 is ingesteld, wordt het certificaat met de langste geldigheidsduur geselecteerd.  

### <a name="ccmcertstore"></a>CCMCERTSTORE

 Hiermee geeft u een andere certificaatarchiefnaam als het clientcertificaat voor HTTPS bevindt zich niet in het standaardcertificaatarchief van **persoonlijke** in het computerarchief.  

 Voorbeeld: `CCMSetup.exe /UsePKICert CCMCERTSTORE="ConfigMgr"`  

### <a name="ccmdebuglogging"></a>CCMDEBUGLOGGING

  Schakelt het logboek voor foutopsporing in. Waarden kunnen worden ingesteld op 0 (uitgeschakeld, standaardinstelling) of 1 (aan). Dit zorgt ervoor dat de client registreert informatie op laag niveau voor het oplossen van problemen. Het wordt aanbevolen het gebruik van deze eigenschap in productiesite te vermijden omdat overmatige logboekregistratie kan optreden, waardoor het moeilijk kan worden relevante informatie in de logbestanden te vinden. CCMENABLELOGGING moet ook worden ingesteld op het logboek voor foutopsporing wilt inschakelen.  

  Voorbeeld: `CCMSetup.exe CCMDEBUGLOGGING=1`  

### <a name="ccmenablelogging"></a>CCMENABLELOGGING

  Wordt standaard ingesteld op TRUE logboekregistratie in te schakelen. De logbestanden worden opgeslagen de **logboeken** map in de installatiemap van de Configuration Manager-client. Deze map is standaard % Windir%\CCM\Logs.  

  Voorbeeld: `CCMSetup.exe CCMENABLELOGGING=TRUE`  

### <a name="ccmevalinterval"></a>CCMEVALINTERVAL  

 De frequentie op waarin clientcomputers evaluatiehulpprogramma (ccmeval.exe) wordt uitgevoerd. Kan **1** naar **1440** minuten. Standaard één keer per dag wordt uitgevoerd.  

### <a name="ccmevalhour"></a>CCMEVALHOUR

 Het uur waarop het evaluatiehulpprogramma van client (ccmeval.exe) wordt uitgevoerd, tussen **0** (middernacht) en **23** (11 pm). Wordt uitgevoerd om middernacht standaard.  

### <a name="ccmfirstcert"></a>CCMFIRSTCERT

 Als dit is ingesteld op 1, specificeert deze eigenschap dat de client het PKI-certificaat met de langste geldigheidsduur moet selecteren. Deze instelling is mogelijk vereist als u netwerktoegangbeveiliging met IPsec enforcement gebruikt.  

 Voorbeeld: `CCMSetup.exe /UsePKICert CCMFIRSTCERT=1`  

### <a name="ccmhostname"></a>CCMHOSTNAME

 Geeft de FQDN van het beheerpunt op internet, als de client over het internet wordt beheerd.  

 Specificeer deze optie niet met de installatie-eigenschap SMSSITECODE=AUTO. Clients op het internet moeten rechtstreeks aan hun site op het internet worden toegewezen.  

 Voorbeeld: `CCMSetup.exe  /UsePKICert/ CCMHOSTNAME="SMSMP01.corp.contoso.com"`  

### <a name="ccmhttpport"></a>CCMHTTPPORT

 Geeft de poort die de client moet gebruiken tijdens de communicatie over HTTP met sitesysteemservers. Standaard ingesteld op poort 80.  

 Voorbeeld: `CCMSetup.exe CCMHTTPPORT=80`  

### <a name="ccmhttpsport"></a>CCMHTTPSPORT

Geeft de poort die de client moet gebruiken tijdens de communicatie over HTTPS met sitesysteemservers. Standaard ingesteld op poort 443.  

Voorbeeld: `CCMSetup.exe /UsePKICert CCMHTTPSPORT=443`  

### <a name="ccminstalldir"></a>CCMINSTALLDIR

 Identificeert de map waar de bestanden van de Configuration Manager-client worden geïnstalleerd, *% Windir %*\CCM standaard. Ongeacht waar deze bestanden worden geïnstalleerd, wordt het Ccmcore.dll-bestand altijd geïnstalleerd de *%Windir%\System32* map. Bovendien op 64-bits besturingssystemen, een kopie van het Ccmcore.dll-bestand is altijd geïnstalleerd in de *% Windir %*\SysWOW64 map ter ondersteuning van 32-bits toepassingen die gebruikmaken van de 32-bits versie van de Configuration Manager-client API's van de Configuration Manager software developer kit (SDK).  

 Voorbeeld: `CCMSetup.exe CCMINSTALLDIR="C:\ConfigMgr"`  

### <a name="ccmloglevel"></a>CCMLOGLEVEL

Hiermee geeft u het detailniveau naar Configuration Manager-logboekbestanden te schrijven. Geef een geheel getal van 0 tot 3, waarbij 0 de meest uitgebreide logboekregistratie is en 3 enkel fouten registreert. De standaardwaarde is 1.  

Voorbeeld: `CCMSetup.exe CCMLOGLEVEL=3`  

### <a name="ccmlogmaxhistory"></a>CCMLOGMAXHISTORY

Wanneer een Configuration Manager-logboekbestand 250000 bytes groot is (of de waarde gespecificeerd door de eigenschap CCMLOGMAXSIZE) bereikt, als een back-up wordt gewijzigd en er wordt een nieuw logboekbestand gemaakt.  

Deze eigenschap specificeert hoeveel eerdere versie van het logbestand moeten worden bewaard. De standaardwaarde is 1. Als de waarde op 0 is ingesteld, worden er geen oude logbestanden bewaard.  

Voorbeeld: `CCMSetup.exe CCMLOGMAXHISTORY=0`  

### <a name="ccmlogmaxsize"></a>CCMLOGMAXSIZE

De maximale logboekgrootte in bytes. Wanneer een logbestand de grootte bereikt die is gespecificeerd, krijgt het een nieuwe naam als een geschiedenisbestand en wordt er een nieuw bestand gemaakt. Deze eigenschap moet worden ingesteld op ten minste 10000 bytes. De standaardwaarde is 250000 bytes.  

Voorbeeld: `CCMSetup.exe CCMLOGMAXSIZE=300000`  

### <a name="disablesiteopt"></a>DISABLESITEOPT

 Indien ingesteld op TRUE, schakelt de mogelijkheid van eindgebruikers met beheerdersreferenties op de clientcomputer te wijzigen van de Configuration Manager toegewezen site in **Configuration Manager** in het Configuratiescherm van de client.  

 Voorbeeld: **CCMSetup.exe DISABLESITEOPT = TRUE**  

### <a name="disablecacheopt"></a>DISABLECACHEOPT

Indien ingesteld op TRUE, schakelt de mogelijkheid van eindgebruikers met beheerdersreferenties op de clientcomputer om te wijzigen van de client instellingen van de cachemap voor de Configuration Manager-client met behulp van Configuration Manager in Configuratiescherm van de clientcomputer.  

Voorbeeld: `CCMSetup.exe DISABLECACHEOPT=TRUE`  

### <a name="dnssuffix"></a>DNSSUFFIX

 Geeft een DNS-domein voor clients om beheerpunten te vinden die in DNS zijn gepubliceerd. Wanneer een beheerpunt is gevonden, informeert het de client over andere beheerpunten in de hiërarchie. Dit betekent dat het beheerpunt dat is gevonden met behulp van DNS-publishing niet afkomstig moet zijn van de site van de client, maar eender welk beheerpunt in de hiërarchie kan zijn.  

> [!NOTE]  
>  U moet deze eigenschap niet opgeven als de client in hetzelfde domein ligt als een gepubliceerd beheerpunt. In dat geval wordt het domein van de client automatisch gebruikt om DNS te zoeken voor beheerpunten.  

 Zie voor meer informatie over DNS-publicatie als servicelocatiebepalingsmethode voor Configuration Manager-clients, [Servicelocatiebepaling en hoe clients hun toegewezen beheerpunt bepaald](../../plan-design/hierarchy/understand-how-clients-find-site-resources-and-services.md#BKMK_Plan_Service_Location) in [begrijpen hoe clients siteresources en -services voor System Center Configuration Manager vinden](../../plan-design/hierarchy/understand-how-clients-find-site-resources-and-services.md) .  

> [!NOTE]  
>  DNS-publishing is standaard niet ingeschakeld in Configuration Manager.  

 Voorbeeld: `CCMSetup.exe SMSSITECODE=ABC DNSSUFFIX=contoso.com`  

### <a name="fsp"></a>FSP

Hiermee geeft u het terugvalstatuspunt dat ontvangt en verwerkt statusberichten die verzonden door de Configuration Manager-clientcomputers.  

Zie voor meer informatie over het terugvalstatuspunt [bepalen of u een terugvalstatuspunt moet](/sccm/core/clients/deploy/plan#determine-if-you-need-a-fallback-status-point).  

Voorbeeld: `CCMSetup.exe FSP=SMSFP01`  

### <a name="ignoreappvversioncheck"></a>IGNOREAPPVVERSIONCHECK

 Hiermee geeft u op dat de aanwezigheid van de minimaal vereiste versie van Microsoft Application Virtualization (App-V) niet is gecontroleerd voordat de client is geïnstalleerd.  

> [!IMPORTANT]  
>  Als u de Configuration Manager-client installeert zonder App-V te installeren, kunt u virtuele toepassingen implementeren.  

 Voorbeeld: `CCMSetup.exe IGNOREAPPVVERSIONCHECK=TRUE`  

### <a name="notifyonly"></a>NOTIFYONLY

Hiermee geeft u op dat door clientstatus zal worden gerapporteerd, maar problemen die zijn gevonden met de client niet hersteld.  

Voorbeeld: `CCMSetup.exe NOTIFYONLY=TRUE`  

Zie [De clientstatus configureren in System Center Configuration Manager](configure-client-status.md) voor meer informatie.  

### <a name="resetkeyinformation"></a>RESETKEYINFORMATION

 Als een Configuration Manager-client de foutieve vertrouwde basissleutel van Configuration Manager heeft en een vertrouwd beheerpunt voor het ontvangen van de nieuwe vertrouwde basissleutel niet kan bereiken, moet u de oude vertrouwde basissleutel handmatig verwijderen met behulp van deze eigenschap. Deze situatie kan optreden wanneer u een client van de ene sitehiërarchie naar een andere verplaatst. Deze eigenschap is van toepassing op cliënten die HTTP- en HTTPS-clientcommunicatie gebruiken.  

 Voorbeeld: `CCMSetup.exe RESETKEYINFORMATION=TRUE`  

### <a name="sitereassign"></a>SITEREASSIGN

Hiermee kunt u automatische site opnieuw toewijzen voor clientupgrades van de gebruikt in combinatie met [SMSSITECODE](#smssitecode)= AUTO.

Voorbeeld: `CCMSetup.exe SMSSITECODE=AUTO SITEREASSIGN=TRUE`

### <a name="smscachedir"></a>SMSCACHEDIR

Geeft de locatie van de cachemap van de client op de clientcomputer, die tijdelijke bestanden opslaat. De locatie is standaard *%Windir \ccmcache*.  

Voorbeeld: `CCMSetup.exe SMSCACHEDIR="C:\Temp"`  

Deze eigenschap kan worden gebruikt in combinatie met de eigenschap SMSCACHEFLAGS om te bepalen van de locatie van de cachemap client.  

Voorbeeld: `CCMSetup.exe SMSCACHEDIR=Cache SMSCACHEFLAGS=MAXDRIVE` installeert de cachemap van de client op het grootste beschikbare client-schijfstation.  

### <a name="smscacheflags"></a>SMSCACHEFLAGS

Geeft meer details over de installatie voor de cachemap van de client. U kunt SMSCACHEFLAGS-eigenschappen afzonderlijk of in combinatie, gescheiden door puntkomma's, gebruiken. Als deze eigenschap niet is gespecificeerd, wordt de cachemap van de client geïnstalleerd volgens de SMSCACHEDIR-eigenschap, wordt de map niet gecomprimeerd en wordt de waarde SMSCACHESIZE gebruikt als de grootte in MB van de map.  

Deze instelling wordt genegeerd wanneer u een upgrade uitvoert van een bestaande client.  

Eigenschappen:  

-   PERCENTDISKSPACE: Geeft de mapgrootte als een percentage van de totale schijfruimte. Als u deze eigenschap specificeert, moet u ook de eigenschap SMSCACHESIZE specificeren als de percentagewaarde om te gebruiken.  

-   PERCENTFREEDISKSPACE: Geeft de mapgrootte als een percentage van de vrije schijfruimte. Als u deze eigenschap specificeert, moet u ook de eigenschap SMSCACHESIZE specificeren als de percentagewaarde om te gebruiken. Als de schijf 10 MB vrij heeft en SMSCACHESIZE is gespecificeerd als 50, wordt de mapgrootte bijvoorbeeld ingesteld op 5 MB. U kunt deze eigenschap niet gebruiken met de eigenschap PERCENTDISKSPACE.  

-   MAXDRIVE: Hiermee geeft u op dat de map moet worden geïnstalleerd op de grootste beschikbare schijf. Deze waarde zal worden genegeerd als er een pad is gespecificeerd met de eigenschap SMSCACHEDIR.  

-   MAXDRIVESPACE: Hiermee geeft u op dat de map moet worden geïnstalleerd op het schijfstation met de meeste vrije ruimte. Deze waarde zal worden genegeerd als er een pad is gespecificeerd met de eigenschap SMSCACHEDIR.  

-   NTFSONLY: Geeft aan dat de map alleen op NTFS-stations kan worden geïnstalleerd. Deze waarde zal worden genegeerd als er een pad is gespecificeerd met de eigenschap SMSCACHEDIR.  

-   COMPRESS: Hiermee geeft u de map moet stoed gecomprimeerd.  

-   FAILIFNOSPACE: Hiermee geeft u op dat de clientsoftware moet worden verwijderd als er onvoldoende ruimte om de map te installeren.  

Voorbeeld: `CCMSetup.exe SMSCACHEFLAGS=NTFSONLY;COMPRESS`  


### <a name="smscachesize"></a>SMSCACHESIZE

> [!IMPORTANT]
> Vanaf Configuration Manager versie 1606 zijn zijn nieuwe clientinstellingen beschikbaar voor het opgeven van de grootte van de client cache. Het toevoegen van die clientinstellingen vervangt SMSCACHESIZE als client.msi-eigenschap voor het opgeven van de grootte van de clientcache. Zie de [clientinstellingen voor cachegrootte](about-client-settings.md#client-cache-settings) voor meer informatie.  

In versie 1602 en eerder wordt met SMSCACHESIZE de grootte opgegeven van de cachemap van de client in megabyte (MB) of als een percentage wanneer het wordt gebruikt met de eigenschap PERCENTDISKSPACE of PERCENTFREEDISKSPACE. Als deze eigenschap niet is ingesteld, is de map standaard maximum 5120 MB groot. De laagste waarde die u kunt opgeven, is 1 MB.  

> [!NOTE]  
>  Als een nieuw pakket dat moet worden gedownload, ervoor zou zorgen dat de map de maximumgrootte overschrijdt, en als de map niet kan worden leeggemaakt om voldoende ruimte beschikbaar te maken, mislukt de download van het pakket, en zal het programma of de toepassing niet worden uitgevoerd.  

Deze instelling wordt genegeerd wanneer u een upgrade op een bestaande client uitvoert en wanneer de client software-update downloadt.  

Voorbeeld: `CCMSetup.exe SMSCACHESIZE=100`  

> [!NOTE]  
>  Als u een client opnieuw installeert, kunt u de installatie-eigenschappen SMSCACHESIZE of SMSCACHEFLAGS niet gebruiken om de cachegrootte zodanig in te stellen dat deze kleiner is dan voorheen. Als u probeert om dit te doen, wordt uw waarde genegeerd en wordt de cachegrootte automatisch ingesteld op de grootte die het vroeger was.  

### <a name="smsconfigsource"></a>SMSCONFIGSOURCE

Hiermee geeft u de locatie en volgorde die de Configuration Manager-installatieprogramma voor configuratie-instellingen controleert. De eigenschap is een reeks die een of meerdere tekens bevat, die elk een specifieke configuratiebron definiëren. Gebruik de tekenwaarden R, P, M en U, alleen of in combinatie:  

-   R: Controleren op configuratie-instellingen in het register.  

   Zie voor meer informatie [informatie over het opslaan van eigenschappen van clientinstallatie in het register.](https://technet.microsoft.com/library/gg712298.aspx#BKMK_Provision).  

-   P: Controleren op configuratie-instellingen in de installatie-eigenschappen die is opgegeven bij de opdrachtprompt.  

-   M: Controleren op bestaande instellingen bij de upgrade van een oudere client met de Configuration Manager-clientsoftware.  

-   U: De geïnstalleerde client naar een nieuwere versie upgraden (en de toegewezen sitecode gebruiken).  

 De clientinstallatie gebruikt standaard `PU` om eerst de installatie-eigenschappen en dan de bestaande instellingen te controleren.  

 Voorbeeld: `CCMSetup.exe SMSCONFIGSOURCE=RP`  

### <a name="smsdirectorylookup"></a>SMSDIRECTORYLOOKUP

 Specificeert of de client Windows Internet Name Service (WINS) kan gebruiken om een beheerpunt te vinden dat HTTP-verbindingen aanvaardt. Clients gebruiken deze methode wanneer ze geen beheerpunt in Active Directory Domain Services of in DNS kunnen vinden.  

 Deze eigenschap heeft geen invloed op of de client WINS voor naamomzetting gebruikt.  

 U kunt twee verschillende modi voor deze eigenschap configureren:  

-   NOWINS: Dit is de veiligste instelling voor deze eigenschap en voorkomt dat clients een beheerpunt in WINS vinden.  Wanneer u deze instelling gebruikt, moeten clients een andere methode hebben om een beheerpunt op het intranet te vinden, zoals Active Directory Domain Services of met behulp van DNS-publishing.  

-   WINSSECURE (standaard): In deze modus kan een client die HTTP-communicatie gebruikt, WINS om een beheerpunt te vinden. De client moet echter een kopie van de vertrouwde basissleutel hebben voordat het een verbinding kan maken met het beheerpunt. Zie [Planning voor de vertrouwde basissleutel](../../plan-design/security/plan-for-security.md#BKMK_PlanningForRTK) in [De beveiliging plannen in System Center Configuration Manager](../../plan-design/security/plan-for-security.md) voor meer informatie.  


 Voorbeeld: `CCMSetup.exe SMSDIRECTORYLOOKUP=NOWINS`  

### <a name="smsmp"></a>SMSMP

Hiermee geeft u een initieel beheerpunt voor de Configuration Manager-client te gebruiken.  

> [!IMPORTANT]  
>  Als het beheerpunt alleen clientverbindingen over HTTPS aanvaardt, moet u de naam van het beheerpunt met https:// voorvoegsel.  

Voorbeeld: `CCMSetup.exe SMSMP=smsmp01.contoso.com`

Voorbeeld: `CCMSetup.exe SMSMP=https://smsmp01.contoso.com`  

### <a name="smspublicrootkey"></a>SMSPUBLICROOTKEY

 Hiermee geeft u de vertrouwde basissleutel van Configuration Manager wanneer het kan niet worden opgehaald uit Active Directory Domain Services. Deze eigenschap is van toepassing op cliënten die HTTP- en HTTPS-clientcommunicatie gebruiken. Zie [Planning voor de vertrouwde basissleutel](../../plan-design/security/plan-for-security.md#BKMK_PlanningForRTK) in [De beveiliging plannen in System Center Configuration Manager](../../plan-design/security/plan-for-security.md) voor meer informatie.  

 Voorbeeld: `CCMSetup.exe SMSPUBLICROOTKEY=&lt;key\>`  

### <a name="smsrootkeypath"></a>SMSROOTKEYPATH

 Gebruikt om de vertrouwde basissleutel van Configuration Manager opnieuw te installeren. Geeft het volledige pad en de bestandsnaam aan een bestand dat de vertrouwde basissleutel bevat. Deze eigenschap is van toepassing op cliënten die HTTP- en HTTPS-clientcommunicatie gebruiken. Zie [Planning voor de vertrouwde basissleutel](../../plan-design/security/plan-for-security.md#BKMK_PlanningForRTK) in [De beveiliging plannen in System Center Configuration Manager](../../plan-design/security/plan-for-security.md) voor meer informatie.  

 Voorbeeld: ' CCMSetup.exe SMSROOTKEYPATH =&lt;volledige pad en bestandsnaam\>`  

### <a name="smssigncert"></a>SMSSIGNCERT

 Geeft het volledige pad en de .cer-bestandsnaam van het geëxporteerde zelfondertekende certificaat op de siteserver.  

 Dit certificaat wordt opgeslagen in het **SMS** certificaatarchief en heeft de objectnaam **Siteserver** en de beschrijvende naam **Handtekeningcertificaat van siteserver**.  

 Voorbeeld: **CCMSetup.exe UsePKICert SMSSIGNCERT =&lt;volledig pad en de naam\>**  

### <a name="smssitecode"></a>SMSSITECODE

 Hiermee geeft u de Configuration Manager-site als u wilt toewijzen aan Configuration Manager-client. Dit kan een sitecode met drie tekens of het woord AUTO zijn. Als AUTO is gespecificeerd, of als deze eigenschap niet is gespecificeerd, probeert de client om te bepalen van de Configuration Manager site-toewijzing van Active Directory Domain Services of van een opgegeven beheerpunt. Om in te schakelen automatisch voor clientupgrades van de, moet u ook instellen [SITEREASSIGN](#sitereassign) op TRUE.    

> [!NOTE]  
>  Gebruik geen AUTO als u ook het beheerpunt op het internet specificeert (CCMHOSTNAME). In dat geval moet u de client direct toewijzen aan de site ervan.  

 Voorbeeld: `CCMSetup.exe SMSSITECODE=XZY`  

##  <a name="BKMK_attributevalues"></a> Ondersteunde kenmerkwaarden voor de selectiecriteria van PKI-certificaten  
 Configuration Manager ondersteunt de volgende kenmerkwaarden voor de selectiecriteria van PKI-certificaat:  

|OID-kenmerk|DN-naamkenmerk|Kenmerkdefinitie|  
|-------------------|----------------------------------|--------------------------|  
|0.9.2342.19200300.100.1.25|DC|Domeinonderdeel|  
|1.2.840.113549.1.9.1|E of e-mailbericht|E-mailadres|  
|2.5.4.3|CN|Algemene naam|  
|2.5.4.4|SN|Onderwerpnaam|  
|2.5.4.5|SERIENUMMER|Serienummer|  
|2.5.4.6|C|Landcode|  
|2.5.4.7|L|Plaats|  
|2.5.4.8|S of ST|Naam van staat of provincie|  
|2.5.4.9|STRAAT|Straat|  
|2.5.4.10|O|Naam van de organisatie|  
|2.5.4.11|OU|Organisatie-eenheid|  
|2.5.4.12|T of titel|Titel|  
|2.5.4.42|G of GN of voornaam|Voornaam|  
|2.5.4.43|I of initialen|Initialen|  
|2.5.29.17|(geen waarde)|Alternatieve onderwerpnaam|  
