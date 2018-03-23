---
title: Clientinstallatie-eigenschappen
titleSuffix: Configuration Manager
description: Meer informatie over de ccmsetup-opdrachtregel eigenschappen voor het installeren van Configuration Manager-client.
ms.custom: na
ms.date: 03/22/2018
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-client
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: c890fd27-7a8c-4f51-bbe2-f9908af1f42b
caps.latest.revision: ''
author: aczechowski
ms.author: aaroncz
manager: dougeby
ms.openlocfilehash: 057b078767a08574a806cb6af1cdb3812148a457
ms.sourcegitcommit: 11bf4ed40ed0cbb10500cc58bbecbd23c92bfe20
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 03/23/2018
---
# <a name="about-client-installation-properties-in-system-center-configuration-manager"></a>Over de eigenschappen van clientinstallatie in System Center Configuration Manager

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*

Gebruik de opdracht CCMSetup.exe de Configuration Manager-client te installeren. Als u deze clientinstallatie-eigenschappen op de opdrachtregel, ze het installatiegedrag wijzigen.



##  <a name="aboutCCMSetup"></a> Over CCMSetup.exe  
 De opdracht CCMSetup.exe downloadt benodigde bestanden voor het installeren van de client van een beheerpunt of een bronlocatie. Deze bestanden kunnen onder andere:  

-   De Windows Installer-pakket client.msi dat de clientsoftware wordt geïnstalleerd.  

-   Microsoft Background Intelligent Transfer Service (BITS)-installatiebestanden.  

-   Windows Installer-installatiebestanden.  

-   Updates en oplossingen voor de Configuration Manager-client.  

> [!NOTE]  
>  In Configuration Manager u kan niet rechtstreeks worden uitgevoerd de Client.msi-bestand.  

 CCMSetup.exe biedt [opdrachtregeleigenschappen](#ccmsetup-exe-command-line-properties) voor het aanpassen van de installatie. U kunt ook eigenschappen voor het wijzigen van het gedrag van client.msi op de CCMSetup.exe-opdrachtregel opgeven.  

> [!IMPORTANT]  
>  CCMSetup-eigenschappen opgeven voordat u de eigenschappen voor client.msi opgeven.  

 CCMSetup.exe en de ondersteunende bestanden bevinden zich op de siteserver in de **Client** map van de installatiemap van Configuration Manager. Deze map wordt gedeeld met het netwerk als  **&lt;Siteservernaam\>\SMS_&lt;sitecode\>\Client**.  

 Aan de opdrachtregel gebruikt de opdracht CCMSetup.exe de volgende indeling:  

 `CCMSetup.exe [<Ccmsetup properties>] [<client.msi setup properties>]`  

 Bijvoorbeeld:  

   `CCMSetup.exe /mp:SMSMP01 /logon SMSSITECODE=S01 FSP=SMSFSP01`  

 In dit voorbeeld heeft de volgende kenmerken:  

-   Hiermee geeft u het beheerpunt smsmp01 om te vragen van een lijst van distributiepunten om de clientinstallatiebestanden te downloaden.  

-   Hiermee geeft u op dat de installatie moet worden stopgezet als er al een versie van de client op de computer bestaat.  

-   Geeft client.msi de instructie om de client toe te wijzen aan de sitecode S01.  

-   Hiermee ontvangt client.msi de instructie het terugvalstatuspunt SMSFP01 te gebruiken.  

> [!NOTE]  
>  Als een eigenschap spaties bevat, eromheen tussen aanhalingstekens.  


> [!IMPORTANT]  
>  Als u het Active Directory-schema uitgebreid voor Configuration Manager, worden veel clientinstallatie-eigenschappen in de site in Active Directory Domain Services gepubliceerd. Deze eigenschappen worden automatisch gelezen door de Configuration Manager-client. Zie voor meer informatie [over clientinstallatie-eigenschappen gepubliceerd op Active Directory Domain Services](about-client-installation-properties-published-to-active-directory-domain-services.md)  



##  <a name="ccmsetupexe-command-line-properties"></a>Opdrachtregeleigenschappen van CCMSetup.exe  

### <a name=""></a>/?  

Opent het dialoogvenster **CCMSetup** met opdrachtregeleigenschappen voor ccmsetup.exe.  

Voorbeeld: **ccmsetup.exe /?**  

### <a name="sourceltpath"></a>/ source:&lt;pad\>  

 Hiermee geeft u de locatie van het bestand downloaden. Een lokaal of UNC-pad gebruiken. Bestanden worden gedownload met behulp van het protocol server message block (SMB). Gebruik **/source**, de Windows-gebruikersaccount voor clientinstallatie moet leesmachtigingen hebben voor de locatie.

> [!NOTE]  
>  U kunt de **/source** eigenschap meer dan één keer in een opdrachtregel om op te geven alternatieve downloadlocaties.  

 Voorbeeld: **ccmsetup.exe /source: "\\\computer\map"**  

### <a name="mpltserver"></a>/MP:&lt;server\>

 Hiermee geeft u een bron beheerpunt voor computers verbinding maken met. Dit beheerpunt gebruiken om te zoeken naar het dichtstbijzijnde distributiepunt voor de installatiebestanden. Als er geen distributiepunten zijn of computers de bestanden niet kunnen uit de distributiepunten na vier uur downloaden, downloaden ze de bestanden van het opgegeven beheerpunt.  

> [!IMPORTANT]  
>  Deze eigenschap wordt gebruikt om een initieel beheerpunt voor computers om te vinden van een bron downloaden geven en een beheerpunt in eender welke site. Dit niet het geval *toewijzen* de client naar een beheerpunt.   

 Computers downloaden de bestanden via een HTTP- of HTTPS-verbinding, afhankelijk van de sitesysteemrolconfiguratie voor clientverbindingen. Als geconfigureerd, is de download gebruikt BITS-beperking. Als alle distributiepunten en beheerpunten voor alleen HTTPS-clientverbindingen zijn geconfigureerd, moet u controleren of de clientcomputer een geldig clientcertificaat heeft.  

U kunt de **/mp** opdrachtregeleigenschap om meer dan één beheerpunt te geven. Als de computer geen verbinding kan maken met het eerste beheerpunt, wordt geprobeerd het volgende gedeelte van de opgegeven lijst. Wanneer u meerdere beheerpunten opgeeft, scheidt u de waarden door puntkomma's.

Als de client verbinding maakt met een beheerpunt via HTTPS normaal gesproken moet u de FQDN-naam, niet de naam van de computer. De waarde moet overeenkomen met het beheerpunt PKI-certificaat onderwerpnaam of alternatieve onderwerpnaam. Hoewel Configuration Manager ondersteunt het gebruik van een computernaam in het certificaat voor verbindingen op het intranet, is een FQDN-naam de aanbevolen beveiligingsprocedure.

Voorbeeld voor wanneer u de computernaam gebruikt: `ccmsetup.exe /mp:SMSMP01`  

Voorbeeld voor wanneer u de FQDN-naam gebruikt: `ccmsetup.exe /mp:smsmp01.contoso.com`  

Deze eigenschap ingesteld op de URL van een cloud-management-gateway. Gebruik deze URL naar de client installeren op een apparaat op basis van het internet. Als u de waarde voor deze eigenschap, gebruikt u de volgende stappen uit:
- Maak een cloud-management-gateway.
- Open een opdrachtprompt van Windows PowerShell als beheerder op een actieve client. 
- Voer de volgende opdracht: `(Get-WmiObject -Namespace Root\Ccm\LocationServices -Class SMS_ActiveMPCandidate | Where-Object {$_.Type -eq "Internet"}).MP`
- Toevoegen van het voorvoegsel 'https://' te gebruiken met de **/mp** eigenschap.

Voorbeeld voor wanneer u de URL van de cloud management gateway gebruikt: `ccmsetup.exe /mp:https://CONTOSO.CLOUDAPP.NET/CCM_Proxy_MutualAuth/72057598037248100`

 > [!Important]
 > Wanneer het opgeven van de URL van een cloud management gateway voor de **/mp** -eigenschap moet beginnen met **https://**.


### <a name="retryltminutes"></a>/ opnieuw proberen:&lt;minuten\>

Het interval voor opnieuw proberen als CCMSetup.exe mislukt installatiebestanden moeten worden gedownload. CCMSetup blijft het opnieuw proberen totdat het de limiet die is opgegeven in bereikt de **downloadtimeout** eigenschap.  

Voorbeeld: `ccmsetup.exe /retry:20`  

### <a name="noservice"></a>/noservice

Voorkomt dat CCMSetup wordt uitgevoerd als een service die de standaardeigenschap. Als CCMSetup een service uitvoert, wordt deze wordt uitgevoerd in de context van het lokale systeemaccount van de computer. Dit account mogelijk niet voldoende rechten voor toegang tot de benodigde netwerkbronnen voor de installatie. Met **/noservice**, CCMSetup.exe wordt uitgevoerd in de context van het gebruikersaccount dat u gebruikt om de installatie te starten. Ook als u een script gebruikt voor het uitvoeren van CCMSetup.exe met de **/service** eigenschap, wordt CCMSetup.exe afgesloten nadat de service is gestart en mogelijk installatiegegevens niet correct.   

Voorbeeld: `ccmsetup.exe /noservice`  

### <a name="service"></a>/service

Specificeert dat CCMSetup moet worden uitgevoerd als een service die het lokale systeemaccount gebruikt.  

Voorbeeld: `ccmsetup.exe /service`  

### <a name="uninstall"></a>/uninstall

Hiermee geeft u op dat de clientsoftware moet worden verwijderd. Zie voor meer informatie [clients beheren](../manage/manage-clients.md).  

Voorbeeld: `ccmsetup.exe /uninstall`  

### <a name="logon"></a>/logon

Als een willekeurige versie van de client al is geïnstalleerd, wordt deze eigenschap specificeert dat de clientinstallatie moet worden gestopt.  

Voorbeeld: `ccmsetup.exe /logon`  

### <a name="forcereboot"></a>/forcereboot

 Specificeert dat CCMSetup de clientcomputer opnieuw op te starten als dat nodig is om de installatie te voltooien moet dwingen. Als deze eigenschap niet is opgegeven, wordt CCMSetup afgesloten wanneer opnieuw opstarten nodig is. Vervolgens gaat door na de volgende handmatig opnieuw worden gestart.  

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

De tijdsduur in minuten over hoelang CCMSetup probeert te downloaden van de installatiebestanden voor het stoppen. De standaardwaarde is **1440** minuten (één dag).  

Voorbeeld: `ccmsetup.exe /downloadtimeout:100`  

### <a name="usepkicert"></a>/UsePKICert

 Als u opgeeft, gebruikt de client een PKI-certificaat dat clientverificatie bevat, indien beschikbaar. Als de client kan niet een geldig certificaat gevonden, wordt een HTTP-verbinding met een zelfondertekend certificaat. Dit gedrag is hetzelfde als u deze eigenschap niet gebruikt.

> [!NOTE]  
>  In sommige scenario's, u niet moet deze eigenschap opgeven wanneer u een client installeert op en nog steeds een clientcertificaat te gebruiken. Deze scenario's omvatten een client installeert met behulp van clientpush en op basis van client-installatie van software-update. U moet deze eigenschap echter opgeven wanneer u een client handmatig installeert en de eigenschap **/mp** gebruikt om een beheerpunt te specificeren dat is geconfigureerd om alleen HTTPS-clientverbindingen te accepteren. U moet deze eigenschap ook specificeren wanneer u een client voor alleen-internet communicatie installeert. Gebruik de CCMALWAYSINF = 1 eigenschap samen met de eigenschappen voor de internet-gebaseerd beheerpunt bevindt en de sitecode. Zie voor meer informatie over clientbeheer op internet, [overwegingen voor clientcommunicatie via internet of een niet-vertrouwd forest](../../plan-design/hierarchy/communications-between-endpoints.md#BKMK_clientspan).  

 Voorbeeld: `CCMSetup.exe /UsePKICert`  

### <a name="nocrlcheck"></a>/NoCRLCheck

 Hiermee geeft u op dat een client de certificaatintrekkingslijst (CRL) niet moet controleren wanneer deze via HTTPS met PKI-certificaat communiceert.  

 Als niet wordt opgegeven, controleert de client de CRL voordat er een HTTPS-verbinding.  

 Zie voor meer informatie over client CRL-controle [Planning voor PKI-certificaatintrekking](../../plan-design/security/plan-for-security.md#BKMK_PlanningForCRLs).  

 Voorbeeld: `CCMSetup.exe /UsePKICert /NoCRLCheck`  

### <a name="configltconfiguration-file"></a>/ config:&lt;configuratiebestand\>

Geeft de naam van een tekstbestand met een lijst met clientinstallatie-eigenschappen.

- Als u geen opgeeft de **/noservice** CCMSetup-eigenschap, moet dit bestand zich in de CCMSetup-map % Windir %\\Ccmsetup voor 32-bits en 64-bits besturingssystemen.
- Als u de eigenschap **/noservice** specificeert, moet dit bestand zich in dezelfde map bevinden van waaruit u CCMSetup.exe uitvoert.  

Voorbeeld: `CCMSetup.exe /config:&lt;Configuration File Name.txt\>`  

Als u de juiste bestandsindeling, gebruikt u het bestand mobileclienttemplate.tcf in de &lt;Configuration Manager-map\>\\bin\\&lt;platform\> map op de siteserver. Dit bestand heeft ook de opmerkingen over de secties en hoe deze worden gebruikt. Geef de clientinstallatie-eigenschappen in de sectie [Client installeren] na de volgende tekst: **Installeer = INSTALL = ALL**.  

Invoer voor de sectie [Client installeren] Voorbeeld: `Install=INSTALL=ALL SMSSITECODE=ABC SMSCACHESIZE=100`  

### <a name="skipprereqltfilename"></a>/ skipprereq:&lt;filename\>

 Hiermee geeft u op dat CCMSetup.exe niet het opgegeven vereiste programma installeren moet wanneer de Configuration Manager-client installeert. Deze eigenschap ondersteunt meer dan één waarde in te voeren. Gebruik de puntkomma (;) als scheidingsteken tussen elke waarde.  


 Voorbeelden: `CCMSetup.exe /skipprereq:dotnetfx40_client_x86_x64.exe` of `CCMSetup.exe /skipprereq:dotnetfx40_client_x86_x64.exe;windowsupdateagent30_x86.exe`  

### <a name="forceinstall"></a>/forceinstall

 Geef CCMSetup.exe wordt verwijderd van een bestaande client en een nieuwe client installeert.  

### <a name="excludefeaturesltfeature"></a>/ ExcludeFeatures:&lt;functie\>

Hiermee geeft u op dat CCMSetup.exe het opgegeven onderdeel niet installeren als de client worden geïnstalleerd.  

Voorbeeld: `CCMSetup.exe /ExcludeFeatures:ClientUI` Software Center niet installeren op de client.  

> [!NOTE]  
>  **ClientUI** is de enige waarde die wordt ondersteund met de **/ExcludeFeatures** eigenschap.  



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


### <a name="aadclientappid"></a>AADCLIENTAPPID

Hiermee geeft u de client app-id van Azure Active Directory (Azure AD). De client-app is gemaakt of geïmporteerd wanneer u [Azure-services configureren](/sccm/core/servers/deploy/configure/azure-services-wizard) voor het beheer van de Cloud. Een Azure-beheerder Haal de waarde voor deze eigenschap van de Azure-portal. Zie voor meer informatie [toepassings-ID ophalen](/azure/azure-resource-manager/resource-group-create-service-principal-portal#get-application-id-and-authentication-key). Voor de **AADCLIENTAPPID** eigenschap, wordt deze toepassing-ID is voor het toepassingstype 'Systeemeigen'.

Voorbeeld: `ccmsetup.exe AADCLIENTAPPID=aa28e7f1-b88a-43cd-a2e3-f88b257c863b`


### <a name="aadresourceuri"></a>AADRESOURCEURI

Hiermee geeft u de server app-id van Azure AD. De server-app is gemaakt of geïmporteerd wanneer u [Azure-services configureren](/sccm/core/servers/deploy/configure/azure-services-wizard) voor het beheer van de Cloud. Wanneer u de server-app maakt in het dialoogvenster Server-toepassing maken, deze eigenschap is de **App ID URI**.

Een Azure-beheerder Haal de waarde voor deze eigenschap van de Azure-portal. In de **Azure Active Directory** blade vinden van de server-app onder **App registraties**. Deze app is van ' Web-app / API ' toepassingstype. Open de app, klikt u op **instellingen**, en vervolgens **eigenschappen**. Gebruik de **App ID URI** waarde voor deze AADRESOURCEURI clientinstallatie-eigenschap.

Voorbeeld: `ccmsetup.exe AADRESOURCEURI=https://contososerver`


### <a name="aadtenantid"></a>AADTENANTID

Hiermee geeft u de Azure AD-tenant-id. Deze tenant is gekoppeld aan Configuration Manager wanneer u [Azure-services configureren](/sccm/core/servers/deploy/configure/azure-services-wizard) voor het beheer van de Cloud. Als u de waarde voor deze eigenschap, gebruikt u de volgende stappen uit:
- Open een opdrachtprompt op een Windows 10-apparaat die is gekoppeld aan dezelfde Azure AD-tenant.
- Voer de volgende opdracht: `dsregcmd.exe /status`
- Zoek in de sectie status van het apparaat de **TenantId** waarde. Bijvoorbeeld: `TenantId : 607b7853-6f6f-4d5d-b3d4-811c33fdd49a`

 > [!Note]
 > Een Azure-beheerder kan ook ophalen voor deze waarde in de Azure portal. Zie voor meer informatie [tenant-ID ophalen](/azure/azure-resource-manager/resource-group-create-service-principal-portal#get-tenant-id)

Voorbeeld: `ccmsetup.exe AADTENANTID=607b7853-6f6f-4d5d-b3d4-811c33fdd49a`


### <a name="aadtenantname"></a>AADTENANTNAME

Hiermee geeft u de naam van de Azure AD-tenant. Deze tenant is gekoppeld aan Configuration Manager wanneer u [Azure-services configureren](/sccm/core/servers/deploy/configure/azure-services-wizard) voor het beheer van de Cloud. Als u de waarde voor deze eigenschap, gebruikt u de volgende stappen uit:
- Open een opdrachtprompt op een Windows 10-apparaat die is gekoppeld aan dezelfde Azure AD-tenant.
- Voer de volgende opdracht: `dsregcmd.exe /status`
- Zoek in de sectie status van het apparaat de **TenantName** waarde. Bijvoorbeeld: `TenantName : Contoso`

Voorbeeld: `ccmsetup.exe AADTENANTNAME=Contoso`


### <a name="ccmadmins"></a>CCMADMINS  

Geeft een of meerdere Windows-gebruikersaccounts of -groepen om toegang te krijgen tot clientinstellingen en beleidsregels. Deze eigenschap is handig wanneer de Configuration Manager-beheerder geen lokale beheerdersreferenties op de clientcomputer. Geef een lijst met accounts die worden gescheiden door puntkomma's.  

Voorbeeld: `CCMSetup.exe CCMADMINS="Domain\Account1;Domain\Group1"`  

### <a name="ccmallowsilentreboot"></a>CCMALLOWSILENTREBOOT

Hiermee geeft u op dat de computer opnieuw mag worden opgestart na de clientinstallatie, indien nodig.  

> [!IMPORTANT]  
>  De computer opnieuw opgestart zonder waarschuwing zelfs als een gebruiker is aangemeld.  

Voorbeeld: **CCMSetup.exe  CCMALLOWSILENTREBOOT**  

### <a name="ccmalwaysinf"></a>CCMALWAYSINF

 Ingesteld op **1** om op te geven dat de client altijd op basis van het internet is en maakt nooit verbinding met het intranet. Het verbindingstype van de client geeft **Altijd internet**weer.  

 Gebruik deze eigenschap in combinatie met CCMHOSTNAME, welke de FQDN van de internet-gebaseerd beheerpunt bevindt. Ook gebruiken met de CCMSetup-eigenschap/usepkicert en met de sitecode.  

 Zie voor meer informatie over clientbeheer op internet, [overwegingen voor clientcommunicatie via internet of een niet-vertrouwd forest](../../plan-design/hierarchy/communications-between-endpoints.md#BKMK_clientspan).  

 Voorbeeld: `CCMSetup.exe /UsePKICert  CCMALWAYSINF=1 CCMHOSTNAME=SERVER3.CONTOSO.COM SMSSITECODE=ABC`  

### <a name="ccmcertissuers"></a>CCMCERTISSUERS

 Hiermee geeft u de lijst met certificaatverleners, dit is een lijst met vertrouwde certificeringsinstantie (CA) basiscertificaten dat de Configuration Manager-site vertrouwt.  

 Zie voor meer informatie over de lijst met certificaatverleners en hoe clients deze gebruiken tijdens de certificaatselectie [Planning voor selectie van PKI-clientcertificaten](../../plan-design/security/plan-for-security.md#BKMK_PlanningForClientCertificateSelection).  

 Deze waarde is een hoofdlettergevoelige overeenkomst voor onderwerpattributen die zich in het basis-CA-certificaat. Attributen kunnen worden gescheiden door een komma (,) of een puntkomma (;). Geef meer dan een basis-CA-certificaten met behulp van een scheidingsbalk. Voorbeeld:  

 `CCMCERTISSUERS=”CN=Contoso Root CA; OU=Servers; O=Contoso, Ltd; C=US &#124; CN=Litware Corporate Root CA; O=Litware, Inc.”`  

> [!TIP]  
>  Kopiëren van de **CertificateIssuers =&lt;tekenreeks\>**  voor de site te verwijzen naar het bestand mobileclient.tcf in de &lt;Configuration Manager-map\>\bin\\ &lt;platform\> map op de siteserver.  

### <a name="ccmcertsel"></a>CCMCERTSEL

 Hiermee geeft u de criteria voor certificaatselectie als de client meer dan één certificaat voor HTTPS-communicatie heeft. Dit certificaat is een geldig certificaat met de mogelijkheid clientverificatie tot.  

 U kunt zoeken naar een exacte overeenkomst (Gebruik **onderwerp:**) of een gedeeltelijke overeenkomst (Gebruik **SubjectStr:)** in de onderwerpnaam of alternatieve onderwerpnaam. Voorbeelden:  

 `CCMCERTSEL="Subject:computer1.contoso.com"` Hiermee zoekt u naar een certificaat met een exacte overeenkomst voor de computernaam "computer1.contoso.com" in de onderwerpnaam of alternatieve onderwerpnaam.  

 `CCMCERTSEL="SubjectStr:contoso.com"` Hiermee zoekt u naar een certificaat dat "contoso.com" in de onderwerpnaam of alternatieve naam voor onderwerp bevat.  

 U kunt ook attributen van de object-id (OID) of DN-naam gebruiken in de onderwerpnaam of alternatieve naam van het onderwerp. Bijvoorbeeld:  

 `CCMCERTSEL="SubjectAttr:2.5.4.11 = Computers"` Hiermee zoekt u naar het attribuut organisatie-eenheid uitgedrukt als een object-id en met de naam Computers.  

 `CCMCERTSEL="SubjectAttr:OU = Computers"` Hiermee zoekt u naar het attribuut organisatie-eenheid uitgedrukt als een DN-naam en met de naam Computers.  

> [!IMPORTANT]  
>  Als u het vak onderwerpnaam gebruikt de **onderwerp:** hoofdlettergevoelig, en de **SubjectStr:** is niet hoofdlettergevoelig.  
>   
>  Als u het vak alternatieve onderwerpnaam gebruikt de **onderwerp:**en de **SubjectStr:** zijn niet hoofdlettergevoelig.  

 De volledige lijst met kenmerken die u voor certificaatselectie kunt gebruiken wordt vermeld in [ondersteunde kenmerkwaarden voor de selectiecriteria van PKI-certificaat](#BKMK_attributevalues).  

 Als meer dan één certificaat overeenstemt met de zoekopdracht, en de eigenschap CCMFIRSTCERT op 1 is ingesteld, wordt het certificaat met de langste geldigheidsduur geselecteerd.  

### <a name="ccmcertstore"></a>CCMCERTSTORE

 Hiermee geeft u een andere certificaatarchiefnaam als het clientcertificaat voor HTTPS bevindt zich niet in het standaardcertificaatarchief van **persoonlijke** in het computerarchief.  

 Voorbeeld: `CCMSetup.exe /UsePKICert CCMCERTSTORE="ConfigMgr"`  

### <a name="ccmdebuglogging"></a>CCMDEBUGLOGGING

  Schakelt het logboek voor foutopsporing in. Waarden kunnen worden ingesteld op 0 (uitgeschakeld, standaardinstelling) of 1 (aan). Deze eigenschap zorgt ervoor dat de client registreert informatie op laag niveau voor het oplossen van problemen. Vermijd het gebruik van deze eigenschap in productiesite als een best practice. Overmatige logboekregistratie kan optreden die mogelijk het moeilijker relevante informatie vinden in de logboekbestanden. CCMENABLELOGGING voor logboekregistratie wilt inschakelen voor foutopsporing ook worden ingesteld.  

  Voorbeeld: `CCMSetup.exe CCMDEBUGLOGGING=1`  

### <a name="ccmenablelogging"></a>CCMENABLELOGGING

  Deze eigenschap is standaard ingesteld op TRUE logboekregistratie in te schakelen. De logbestanden worden opgeslagen de **logboeken** map in de installatiemap van de Configuration Manager-client. Deze map is standaard % Windir%\CCM\Logs.  

  Voorbeeld: `CCMSetup.exe CCMENABLELOGGING=TRUE`  

### <a name="ccmevalinterval"></a>CCMEVALINTERVAL  

 De frequentie op waarin clientcomputers evaluatiehulpprogramma (ccmeval.exe) wordt uitgevoerd. Kan **1** naar **1440** minuten. Standaard één keer per dag wordt uitgevoerd.  

### <a name="ccmevalhour"></a>CCMEVALHOUR

 Het uur waarop het evaluatiehulpprogramma van client (ccmeval.exe) wordt uitgevoerd, tussen **0** (middernacht) en **23** (11 pm). Wordt uitgevoerd om middernacht standaard.  

### <a name="ccmfirstcert"></a>CCMFIRSTCERT

 Als dit is ingesteld op 1, specificeert deze eigenschap dat de client het PKI-certificaat met de langste geldigheidsduur moet selecteren. Deze instelling is mogelijk vereist als u Network Access Protection met IPsec enforcement gebruikt.  

 Voorbeeld: `CCMSetup.exe /UsePKICert CCMFIRSTCERT=1`  


### <a name="ccmhostname"></a>CCMHOSTNAME

 Als de client wordt beheerd via internet, geeft deze eigenschap geeft u de FQDN van de internet-gebaseerd beheerpunt bevindt.  

 Deze optie niet opgeven met de installatie-eigenschap smssitecode = AUTO. Clients op Internet moeten rechtstreeks worden toegewezen aan hun site op basis van het internet.  

 Voorbeeld: `CCMSetup.exe  /UsePKICert CCMHOSTNAME="SMSMP01.corp.contoso.com"`  

Deze eigenschap ingesteld op het adres van een cloud-management-gateway. Als u de waarde voor deze eigenschap, gebruikt u de volgende stappen uit:
- Maak een cloud-management-gateway.
- Open een opdrachtprompt van Windows PowerShell als beheerder op een actieve client. 
- Voer de volgende opdracht: `(Get-WmiObject -Namespace Root\Ccm\LocationServices -Class SMS_ActiveMPCandidate | Where-Object {$_.Type -eq "Internet"}).MP`
- Gebruik de geretourneerde waarde als-is met de **CCMHOSTNAME** eigenschap.

Bijvoorbeeld: `ccmsetup.exe CCMHOSTNAME=CONTOSO.CLOUDAPP.NET/CCM_Proxy_MutualAuth/72057598037248100`

 > [!Important]
 > Bij het opgeven van het adres van een cloud management gateway voor de **CCMHOSTNAME** eigenschap doen *niet* , zoals een voorvoegsel toevoegen **https://**. Dit voorvoegsel wordt alleen gebruikt met de **/mp** URL van een cloud-management-gateway.



### <a name="ccmhttpport"></a>CCMHTTPPORT

 Geeft de poort die de client moet gebruiken tijdens de communicatie over HTTP met sitesysteemservers. Standaard ingesteld op poort 80.  

 Voorbeeld: `CCMSetup.exe CCMHTTPPORT=80`  

### <a name="ccmhttpsport"></a>CCMHTTPSPORT

Geeft de poort die de client moet gebruiken tijdens de communicatie over HTTPS met sitesysteemservers. Standaard ingesteld op poort 443.  

Voorbeeld: `CCMSetup.exe /UsePKICert CCMHTTPSPORT=443`  

### <a name="ccminstalldir"></a>CCMINSTALLDIR

 Identificeert de map waar de bestanden van de Configuration Manager-client worden geïnstalleerd, *% Windir %*\CCM standaard. Ongeacht waar deze bestanden worden geïnstalleerd, wordt het Ccmcore.dll-bestand altijd geïnstalleerd de *%Windir%\System32* map. Ook op een 64-bits besturingssysteem, een kopie van het Ccmcore.dll-bestand is altijd geïnstalleerd in de *% Windir %*\SysWOW64 map. Dit bestand biedt ondersteuning voor 32-bits toepassingen die gebruikmaken van de 32-bits versie van de client-API's van de Configuration Manager-SDK.  

 Voorbeeld: `CCMSetup.exe CCMINSTALLDIR="C:\ConfigMgr"`  

### <a name="ccmloglevel"></a>CCMLOGLEVEL

Hiermee geeft u het detailniveau naar Configuration Manager-logboekbestanden te schrijven. Geef een geheel getal van 0 tot 3, waarbij 0 de meest uitgebreide logboekregistratie is en 3 enkel fouten registreert. De standaardwaarde is 1.  

Voorbeeld: `CCMSetup.exe CCMLOGLEVEL=3`  

### <a name="ccmlogmaxhistory"></a>CCMLOGMAXHISTORY

Wanneer een logbestand van de Configuration Manager de maximale grootte bereikt, wordt de client wijzigt u de naam als een back-up en wordt een nieuw logboekbestand gemaakt. De maximale grootte is 250.000 bytes, of de waarde gespecificeerd door de eigenschap CCMLOGMAXSIZE.

Deze eigenschap geeft u op hoeveel eerdere versie van het logboekbestand te houden. De standaardwaarde is 1. Als de waarde op 0 is ingesteld, worden er geen oude logbestanden bewaard.  

Voorbeeld: `CCMSetup.exe CCMLOGMAXHISTORY=0`  

### <a name="ccmlogmaxsize"></a>CCMLOGMAXSIZE

De maximale logboekgrootte in bytes. Wanneer een logbestand met de opgegeven grootte, de client wijzigt u de naam als een geschiedenisbestand en wordt een nieuw bestand gemaakt. Deze eigenschap moet worden ingesteld op ten minste 10.000 bytes. De standaardwaarde is 250.000 bytes.  

Voorbeeld: `CCMSetup.exe CCMLOGMAXSIZE=300000`  

### <a name="disablesiteopt"></a>DISABLESITEOPT

 Als u ingesteld op TRUE, deze eigenschap schakelt u de mogelijkheid van gebruikers met beheerdersrechten wijzigen van de toegewezen site in de **Configuration Manager** het Configuratiescherm.  

 Voorbeeld: **CCMSetup.exe DISABLESITEOPT=TRUE**  

### <a name="disablecacheopt"></a>DISABLECACHEOPT

Als u ingesteld op TRUE, deze eigenschap schakelt u de mogelijkheid van gebruikers met beheerdersrechten wijzigen van de clientcache map-instellingen in de **Configuration Manager** het Configuratiescherm.  

Voorbeeld: `CCMSetup.exe DISABLECACHEOPT=TRUE`  

### <a name="dnssuffix"></a>DNSSUFFIX

 Geeft een DNS-domein voor clients om beheerpunten te vinden die in DNS zijn gepubliceerd. Wanneer een beheerpunt is gevonden, informeert het de client over andere beheerpunten in de hiërarchie. Dit gedrag betekent dat het beheerpunt dat is gevonden met behulp van DNS-publishing niet afkomstig moet zijn van de site van de client, maar eender welk beheerpunt in de hiërarchie kan zijn.  

> [!NOTE]  
>  U hoeft niet te deze eigenschap opgeven als de client zich in hetzelfde domein als een gepubliceerd beheerpunt. In dat geval wordt het domein van de client automatisch gebruikt om DNS te zoeken voor beheerpunten.  

 Zie voor meer informatie over DNS-publicatie als servicelocatiebepalingsmethode voor Configuration Manager-clients, [Service locatie en hoe het toegewezen beheerpunt voor clients wordt bepaald](../../plan-design/hierarchy/understand-how-clients-find-site-resources-and-services.md#BKMK_Plan_Service_Location).  

> [!NOTE]  
>  Standaard is geen DNS-publishing in Configuration Manager ingeschakeld.  

 Voorbeeld: `CCMSetup.exe SMSSITECODE=ABC DNSSUFFIX=contoso.com`  

### <a name="fsp"></a>FSP

Hiermee geeft u het terugvalstatuspunt dat ontvangt en verwerkt statusberichten die verzonden door de Configuration Manager-clientcomputers.  

Zie voor meer informatie over het terugvalstatuspunt [bepalen of u een terugvalstatuspunt moet](/sccm/core/clients/deploy/plan/determine-the-site-system-roles-for-clients#determine-if-you-need-a-fallback-status-point).  

Voorbeeld: `CCMSetup.exe FSP=SMSFP01`  

### <a name="ignoreappvversioncheck"></a>IGNOREAPPVVERSIONCHECK

 Geeft aan dat de aanwezigheid van de minimaal vereiste versie van Microsoft Application Virtualization (App-V) niet is gecontroleerd voordat de client is geïnstalleerd.  

> [!IMPORTANT]  
>  Als u de Configuration Manager-client installeert zonder App-V te installeren, kunt u virtuele toepassingen implementeren.  

 Voorbeeld: `CCMSetup.exe IGNOREAPPVVERSIONCHECK=TRUE`  

### <a name="notifyonly"></a>NOTIFYONLY

Hiermee geeft u de client wordt gerapporteerd, maar niet gevonden gevonden problemen kunt oplossen.  

Voorbeeld: `CCMSetup.exe NOTIFYONLY=TRUE`  

Zie voor meer informatie [clientstatus configureren](configure-client-status.md).  

### <a name="resetkeyinformation"></a>RESETKEYINFORMATION

 Als een client de foutieve vertrouwde basissleutel van Configuration Manager heeft en een vertrouwd beheerpunt voor het ontvangen van de nieuwe vertrouwde basissleutel niet kan bereiken, moet u deze eigenschap gebruiken handmatig verwijderen van de oude vertrouwde basissleutel. Deze situatie kan optreden wanneer u een client van de ene sitehiërarchie naar een andere verplaatst. Deze eigenschap is van toepassing op cliënten die HTTP- en HTTPS-clientcommunicatie gebruiken.  

 Voorbeeld: `CCMSetup.exe RESETKEYINFORMATION=TRUE`  

### <a name="sitereassign"></a>SITEREASSIGN

Hiermee kunt u automatische site opnieuw toewijzen voor clientupgrades van de gebruikt in combinatie met [SMSSITECODE](#smssitecode)= AUTO.

Voorbeeld: `CCMSetup.exe SMSSITECODE=AUTO SITEREASSIGN=TRUE`

### <a name="smscachedir"></a>SMSCACHEDIR

Geeft de locatie van de cachemap van de client op de clientcomputer, die tijdelijke bestanden opslaat. De locatie is standaard *%Windir%\ccmcache*.  

Voorbeeld: `CCMSetup.exe SMSCACHEDIR="C:\Temp"`  

Deze eigenschap kan worden gebruikt in combinatie met de eigenschap SMSCACHEFLAGS om te bepalen van de locatie van de cachemap client.  

Voorbeeld: `CCMSetup.exe SMSCACHEDIR=Cache SMSCACHEFLAGS=MAXDRIVE` installeert de cachemap van de client op het grootste beschikbare client-schijfstation.  

### <a name="smscacheflags"></a>SMSCACHEFLAGS

Geeft meer details over de installatie voor de cachemap van de client. U kunt SMSCACHEFLAGS-eigenschappen afzonderlijk of in combinatie, gescheiden door puntkomma's, gebruiken. Als deze eigenschap niet is opgegeven, de cachemap van de client geïnstalleerd volgens de SMSCACHEDIR-eigenschap, de map is niet gecomprimeerd en de waarde SMSCACHESIZE gebruikt als de grootte in MB van de map.  

Deze instelling wordt genegeerd wanneer u een upgrade uitvoert van een bestaande client.  

Eigenschappen:  

-   PERCENTDISKSPACE: Geeft de mapgrootte als een percentage van de totale schijfruimte. Als u deze eigenschap specificeert, moet u ook de eigenschap SMSCACHESIZE specificeren als de percentagewaarde om te gebruiken.  

-   PERCENTFREEDISKSPACE: Geeft de mapgrootte als een percentage van de vrije schijfruimte. Als u deze eigenschap specificeert, moet u ook de eigenschap SMSCACHESIZE specificeren als de percentagewaarde om te gebruiken. Als de schijf 10 MB vrij heeft en SMSCACHESIZE is gespecificeerd als 50, wordt de mapgrootte bijvoorbeeld ingesteld op 5 MB. U kunt deze eigenschap niet gebruiken met de eigenschap PERCENTDISKSPACE.  

-   MAXDRIVE: Hiermee geeft u op dat de map moet worden geïnstalleerd op de grootste beschikbare schijf. Deze waarde wordt genegeerd als er een pad is gespecificeerd met de eigenschap SMSCACHEDIR.  

-   MAXDRIVESPACE: Hiermee geeft u op dat de map moet worden geïnstalleerd op het schijfstation met de meeste vrije ruimte. Deze waarde wordt genegeerd als er een pad is gespecificeerd met de eigenschap SMSCACHEDIR.  

-   NTFSONLY: Geeft aan dat de map alleen op NTFS-stations kan worden geïnstalleerd. Deze waarde wordt genegeerd als er een pad is gespecificeerd met de eigenschap SMSCACHEDIR.  

-   COMPRESS: Hiermee geeft u op dat de map gecomprimeerd moet worden opgeslagen.  

-   FAILIFNOSPACE: Hiermee geeft u op dat de clientsoftware moet worden verwijderd als er onvoldoende ruimte om de map te installeren.  

Voorbeeld: `CCMSetup.exe SMSCACHEFLAGS=NTFSONLY;COMPRESS`  


### <a name="smscachesize"></a>SMSCACHESIZE

> [!IMPORTANT]
> Clientinstellingen zijn beschikbaar voor het opgeven van de grootte van de cachemap client. Het toevoegen van die clientinstellingen vervangt SMSCACHESIZE als client.msi-eigenschap voor het opgeven van de grootte van de clientcache. Zie de [clientinstellingen voor cachegrootte](about-client-settings.md#client-cache-settings) voor meer informatie.  

<!-- For 1602 and earlier, SMSCACHESIZE specifies the size of the client cache folder in megabyte (MB) or as a percentage when used with the PERCENTDISKSPACE or PERCENTFREEDISKSPACE property. If this property isn't set, the folder defaults to a maximum size of 5120 MB. The lowest value that you can specify is 1 MB.  -->

> [!NOTE]  
>  Als u een nieuw pakket dat moet worden gedownload, ervoor zou zorgen dat de map de maximumgrootte overschrijdt, en als de map kan niet worden leeggemaakt om voldoende ruimte beschikbaar te stellen, het downloaden van het pakket mislukt en het programma dat of toepassing kan niet worden uitgevoerd.  

Deze instelling wordt genegeerd wanneer u een upgrade van een bestaande client uitvoert en wanneer de client downloadt software-updates.  

Voorbeeld: `CCMSetup.exe SMSCACHESIZE=100`  

> [!NOTE]  
>  Als u een client opnieuw installeert, kunt u de installatie-eigenschappen SMSCACHESIZE of SMSCACHEFLAGS niet gebruiken om in te stellen de cachegrootte is kleiner dan het vroeger was. Als u deze actie wordt uitgevoerd probeert, wordt uw waarde genegeerd. De cachegrootte automatisch ingesteld op de vorige grootte.  

### <a name="smsconfigsource"></a>SMSCONFIGSOURCE

Hiermee geeft u de locatie en volgorde die de Configuration Manager-installatieprogramma voor configuratie-instellingen controleert. De eigenschap is een tekenreeks van een of meer tekens, die elk een specifieke configuratiebron definiëren. Gebruik de tekenwaarden R, P, M en U, alleen of in combinatie:  

-   R: Controleren op configuratie-instellingen in het register.  

   Zie voor meer informatie [informatie over het opslaan van eigenschappen van clientinstallatie in het register](/sccm/core/clients/deploy/deploy-clients-to-windows-computers#BKMK_Provision).  

-   P: Controleren op configuratie-instellingen in de installatie-eigenschappen die is opgegeven bij de opdrachtprompt.  

-   M: Controleren op bestaande instellingen bij de upgrade van een oudere client met de Configuration Manager-clientsoftware.  

-   U: De geïnstalleerde client naar een nieuwere versie upgraden (en de toegewezen sitecode gebruiken).  

 De clientinstallatie gebruikt standaard `PU` om eerst de installatie-eigenschappen en dan de bestaande instellingen te controleren.  

 Voorbeeld: `CCMSetup.exe SMSCONFIGSOURCE=RP`  

### <a name="smsdirectorylookup"></a>SMSDIRECTORYLOOKUP

 Specificeert of de client Windows Internet Name Service (WINS) kan gebruiken om een beheerpunt te vinden dat HTTP-verbindingen aanvaardt. Clients gebruiken deze methode wanneer ze een beheerpunt in Active Directory Domain Services of in DNS vinden kunnen.  

 Deze eigenschap heeft geen invloed op of de client WINS voor naamomzetting gebruikt.  

 U kunt twee verschillende modi voor deze eigenschap configureren:  

-   NOWINS: Deze waarde is de veiligste instelling voor deze eigenschap en voorkomt dat clients een beheerpunt in WINS vinden. Wanneer u deze instelling gebruikt, moeten clients een andere methode hebben om een beheerpunt op het intranet te vinden, zoals Active Directory Domain Services of met behulp van DNS-publishing.  

-   WINSSECURE (standaard): In deze modus kan een client die HTTP-communicatie gebruikt, WINS om een beheerpunt te vinden. De client moet echter een kopie van de vertrouwde basissleutel hebben voordat het een verbinding kan maken met het beheerpunt. Zie voor meer informatie [Planning voor de vertrouwde basissleutel](../../plan-design/security/plan-for-security.md#BKMK_PlanningForRTK).  


 Voorbeeld: `CCMSetup.exe SMSDIRECTORYLOOKUP=NOWINS`  

### <a name="smsmp"></a>SMSMP

Hiermee geeft u een initieel beheerpunt voor de Configuration Manager-client te gebruiken.  

> [!IMPORTANT]  
>  Als het beheerpunt alleen clientverbindingen over HTTPS aanvaardt, moet u de naam van het beheerpunt met https:// voorvoegsel.  

Voorbeeld: `CCMSetup.exe SMSMP=smsmp01.contoso.com`

Voorbeeld: `CCMSetup.exe SMSMP=https://smsmp01.contoso.com`  


### <a name="smspublicrootkey"></a>SMSPUBLICROOTKEY

 Hiermee geeft u de vertrouwde basissleutel van Configuration Manager wanneer het kan niet worden opgehaald uit Active Directory Domain Services. Deze eigenschap is van toepassing op cliënten die HTTP- en HTTPS-clientcommunicatie gebruiken. Zie voor meer informatie [Planning voor de vertrouwde basissleutel](../../plan-design/security/plan-for-security.md#BKMK_PlanningForRTK).  

 Voorbeeld: `CCMSetup.exe SMSPUBLICROOTKEY=&lt;key\>`  

### <a name="smsrootkeypath"></a>SMSROOTKEYPATH

 Gebruikt om de vertrouwde basissleutel van Configuration Manager opnieuw te installeren. Geeft het volledige pad en de bestandsnaam aan een bestand dat de vertrouwde basissleutel bevat. Deze eigenschap is van toepassing op cliënten die HTTP- en HTTPS-clientcommunicatie gebruiken. Zie voor meer informatie [Planning voor de vertrouwde basissleutel](../../plan-design/security/plan-for-security.md#BKMK_PlanningForRTK).  

 Voorbeeld: ' CCMSetup.exe SMSROOTKEYPATH =&lt;volledige pad en bestandsnaam\>`  

### <a name="smssigncert"></a>SMSSIGNCERT

 Geeft het volledige pad en de .cer-bestandsnaam van het geëxporteerde zelfondertekende certificaat op de siteserver.  

 Dit certificaat wordt opgeslagen in het **SMS** certificaatarchief en heeft de objectnaam **Siteserver** en de beschrijvende naam **Handtekeningcertificaat van siteserver**.  

 Voorbeeld: **CCMSetup.exe UsePKICert SMSSIGNCERT =&lt;volledig pad en de naam\>**  

### <a name="smssitecode"></a>SMSSITECODE

 Hiermee geeft u de Configuration Manager-site om de client toewijst aan. Deze waarde kan een sitecode met drie tekens of het woord AUTO zijn. Als u automatische opgeven of u deze eigenschap niet opgeeft, probeert de client om te bepalen de sitetoewijzing van Active Directory Domain Services of van een opgegeven beheerpunt. Om in te schakelen automatisch voor clientupgrades van de, moet u ook instellen [SITEREASSIGN](#sitereassign) op TRUE.    

> [!NOTE]  
>  Gebruik geen AUTO als u ook de internet-gebaseerd beheerpunt bevindt (CCMHOSTNAME) opgeven. In dat geval moet u de client direct toewijzen aan de site ervan.  

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
