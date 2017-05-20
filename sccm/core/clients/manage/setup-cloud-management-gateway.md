---
title: Instellen van Cloud Management Gateway | Microsoft-documenten
description: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 05/01/2017
ms.topic: article
ms.prod: configuration-manager
ms.service: 
ms.technology:
- configmgr-client
ms.assetid: e0ec7d66-1502-4b31-85bb-94996b1bc66f
ms.translationtype: Machine Translation
ms.sourcegitcommit: d5a6fdc9a526c4fc3a9027dcedf1dd66a6fff5a7
ms.openlocfilehash: 97e1bc6585cee0ff433da0ec0b60b9604cb7348f
ms.contentlocale: nl-nl
ms.lasthandoff: 05/17/2017

---

# <a name="set-up-cloud-management-gateway-for-configuration-manager"></a>Instellen van de cloud management gateway voor Configuration Manager

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*

Vanaf versie 1610 wordt omvat het proces voor het instellen van cloud management gateway in Configuration Manager de volgende stappen uit:

## <a name="step-1-configure-required-certificates"></a>Stap 1: Vereiste certificaten configureren

## <a name="option-1-preferred---use-the-server-authentication-certificate-from-a-public-and-globally-trusted-certificate-provider-like-verisign"></a>Optie 1 (bij voorkeur): gebruik het serververificatiecertificaat van een provider openbare en globaal vertrouwd certificaat (zoals VeriSign)

Wanneer u deze methode gebruikt, wordt automatisch het certificaat vertrouwen dat clients en u niet wilt maken van een aangepaste SSL-certificaat.

1. Een record canonieke naam (CNAME) maken in uw organisatie openbare domein name-service (DNS) een alias voor de cloud management gateway-service naar een beschrijvende naam die wordt gebruikt in het openbaar certificaat maken.
Bijvoorbeeld, Contoso hun cloud management gateway-service namen **GraniteFalls** wat in Azure **GraniteFalls.CloudApp.Net**. De DNS-beheerder maakt een nieuwe CNAME-record voor in Contoso openbare DNS-contoso.com naamruimte **GraniteFalls.Contoso.com** voor de echte hostnaam **GraniteFalls.CloudApp.net**.
2. Naast een certificaat voor serververificatie aanvragen van een openbare provider met behulp van de algemene naam (CN) van de CNAME-alias.
Contoso gebruikt bijvoorbeeld **GraniteFalls.Contoso.com** voor de algemene naam van het certificaat.
3. De cloud management gateway-service in de Configuration Manager-console met dit certificaat maken.
    - Op de **instellingen** pagina van de Wizard Cloud maken Management Gateway bij het toevoegen van het servercertificaat voor deze cloudservice (van **certificaatbestand**), de wizard wordt de hostnaam van de CN als de naam van de service-certificaat ophalen en het vervolgens toevoegen die u wilt **cloudapp.net** (of **usgovcloudapp.net** voor de cloud Azure ons overheid) als de FQDN-Service voor het maken van de service in Azure.
Bijvoorbeeld, bij het maken van de cloud management gateway bij Contoso, de hostnaam **GraniteFalls** wordt opgehaald uit het certificaat CN, zodat de werkelijke in Azure-service wordt gemaakt als **GraniteFalls.CloudApp.net**.

### <a name="option-2---create-a-custom-ssl-certificate-for-cloud-management-gateway-in-the-same-way-as-for-a-cloud-based-distribution-point"></a>Optie 2: een aangepaste SSL-certificaat voor cloud management gateway op dezelfde manier als voor een cloud-gebaseerde distributiepunt maken

U kunt een aangepaste SSL-certificaat voor cloud management gateway maken op dezelfde manier als die u dit voor een cloud-gebaseerde distributiepunt doen zou. Volg de instructies voor [het servicecertificaat voor Cloud-gebaseerde distributiepunten implementeren](/sccm/core/plan-design/network/example-deployment-of-pki-certificates) maar anders de volgende dingen doen:

- Bij het instellen van de nieuwe certificaatsjabloon, geven ** lezen ** en **inschrijven** verlenen aan de beveiligingsgroep die u voor Configuration Manager-servers instelt.
- Bij het aanvragen van het aangepaste Webservercertificaat een FQDN-naam opgeven voor de algemene naam van het certificaat die eindigen op **cloudapp.net** voor het gebruik van cloud management gateway op Azure openbare cloud of **usgovcloudapp.net** voor de overheid van de Azure-cloud.


## <a name="step-2-export-the-client-certificates-root"></a>Stap 2: Het clientcertificaat root exporteren

De eenvoudigste manier om op te halen exporteren de hoofdmap van de clientcertificaten in het netwerk gebruikt, opent u een clientcertificaat op een van de domein-machines met een en kopieert u deze.

> [!NOTE] 
>
> Clientcertificaten vereist zijn op elke computer die u wilt beheren met cloud management gateway en wijs op de sitesysteemserver die als host fungeert voor de cloud management gateway-connector. Als u toevoegen van een clientcertificaat aan elk van deze virtuele machines wilt, Zie [implementeren van het certificaat voor Windows clientcomputers](/sccm/core/plan-design/network/example-deployment-of-pki-certificates#BKMK_client2008_cm2012).

1.  Typ in het venster uitvoeren **mmc** en op Return drukt.

2.  Kies in het menu bestand **module toevoegen/verwijderen...** .

3.  Kies in het dialoogvenster Remove-modules **certificaten** > **toevoegen &gt;**   >  **computeraccount** > **volgende** > **lokale computer** > **voltooien**. 

4.  Ga naar **certificaten** &gt; **persoonlijke** &gt; **certificaten**.

5.  Dubbelklik op het certificaat voor clientverificatie op de computer, klik op het tabblad certificeringspad en dubbelklikt u op de basiscertificeringsinstantie (aan de bovenkant van het pad).

6.  Kies op het tabblad met Details **kopiëren naar bestand...** .

7.  Voltooi de Wizard Certificaat exporteren met behulp van de standaardindeling voor het certificaat. Controleer de naam en locatie van het basiscertificaat dat u maakt. U moet het configureren van de cloud management gateway in een [later stap](#step-4-set-up-cloud-management-gateway).

## <a name="step-3-upload-the-management-certificate-to-azure"></a>Stap 3: Upload het beheercerticaat naar Azure

Een Azure management-certificaat is vereist voor Configuratiebeheer voor toegang tot de Azure API en cloud management gateway configureert. Zie de volgende artikelen in de Azure-documentatie voor meer informatie en instructies voor het uploaden van een management-certificaat:

- [Overzicht van de certificaten voor Azure Cloud Services](https://azure.microsoft.com/documentation/articles/cloud-services-certs-create/)

- [Een Azure Management API Management-certificaat uploaden](https://azure.microsoft.com/documentation/articles/azure-api-management-certs/)

>[!IMPORTANT]
>Zorg ervoor dat de abonnements-ID die is gekoppeld aan het beheercertificaat te kopiëren. U moet deze gebruiken voor cloud management gateway configureren in de Configuration Manager-console in de [volgende stap](#step-4-set-up-cloud-management-gateway).

### <a name="subordinate-ca-certificates-and-azure"></a>Onderliggende CA-certificaten en Azure

Als uw certificaat is uitgegeven door een onderliggende CA (subCA) en uw enterprise PKI-infrastructuur niet op het Internet is, gebruikt u deze procedure voor het uploaden van het certificaat naar Azure. 

1. Na het instellen van een cloud management gateway, zoek de cloud management gateway-service in uw Azure-portal en gaat u naar de **certificaat** tabblad. Uw subCA certificaten er uploaden. Als u meer dan één subCA certificaat hebt, moet u ze allemaal uploaden. 
2. Zodra het certificaat is geüpload, noteer de vingerafdruk. 
3. Voeg de vingerafdruk aan sitedatabase met behulp van dit script:
    
```

    DIM serviceCName
    DIM subCAThumbprints

    ' Verify arguments
    IF WScript.Arguments.Count <> 2 THEN
    WScript.StdOut.WriteLine "Usage: CScript UpdateSubCAThumbprints.vbs <ServiceCName> <SubCA cert thumbprints, separated by ;>"
    WScript.Quit 1
    END IF

    'Get arguments
    serviceCName = WScript.Arguments.Item(0)
    subCAThumbprints = WScript.Arguments.Item(1)

    'Find SMS Provider
    WScript.StdOut.WriteLine "Searching for SMS Provider for local site..."
    SET objSMSNamespace = GetObject("winmgmts:{impersonationLevel=impersonate}!\\.\root\sms")
    SET results = objSMSNamespace.ExecQuery("SELECT * From SMS_ProviderLocation WHERE ProviderForLocalSite = true")

    'Process the results
    FOR EACH var in results
    siteCode = var.SiteCode
    NEXT

    IF siteCode = "" THEN
    WScript.StdOut.WriteLine "Failed to locate SMS provider."
    WScript.Quit 1
    END IF

    WScript.StdOut.WriteLine "SiteCode = " & siteCode 

    ' Connect to the SMS namespace
    SET objWMIService = GetObject("winmgmts:{impersonationLevel=impersonate}!\\.\root\sms\site_" & siteCode)

    'Get instance of SMS_AzureService
    DIM query
    query = "SELECT * From SMS_AzureService WHERE ServiceType = 'CloudProxyService' AND ServiceCName = '" & serviceCName & "'"
    WScript.StdOut.WriteLine "Run WQL query: " &  query
    SET objInstances = objWMIService.ExecQuery(query)

    IF IsNull(objInstances) OR (objInstances.Count = 0) THEN
    WScript.StdOut.WriteLine "Failed to get Azure_Service instance."
    WScript.Quit 1
    END IF

    FOR EACH var IN objInstances
    SET azService = var
    NEXT

    WScript.StdOut.WriteLine "Update [SubCACertThumbprint] to " & subCAThumbprints

    'Update SubCA cert thumbprints
    azService.Properties_.item("SubCACertThumbprint") = subCAThumbprints

    'Save data back to provider
    azService.Put_

    WScript.StdOut.WriteLine "[SubCACertThumbprint] is updated successfully."
```


## <a name="step-4-set-up-cloud-management-gateway"></a>Stap 4: Beheergateway cloud instellen

>[!NOTE]
>Cloud management gateway is versie 1610, een voorlopige versie-functie. Als u wilt inschakelen, Zie [gebruikmaken van de functies van updates pre-release](/sccm/core/servers/manage/install-in-console-updates#bkmk_prerelease).

1. Ga in de Configuration Manager-console naar **beheer** > **Cloudservices** > **Cloud Management Gateway**.
2. Kies **Cloud Management Gateway maken**.

3. Voer uw Azure-abonnement-ID (overgenomen van de Azure-beheerportal) in de Wizard Cloud maken Management Gateway en blader naar het certificaatbestand dat u gebruikt voor het uploaden van een Azure-beheercertificaat. Kies **volgende** en wacht enige tijd tot de console verbinding maakt met Azure.

4. Vul de aanvullende gegevens in de wizard:

    - Geef de naam voor de service die wordt uitgevoerd in Azure. Servicenaam moet alleen alfanumerieke tekens en 3 tot 24 tekens lang zijn.

    - Kies de Azure-regio die u wilt dat de service in te voeren.

    - Geef het aantal virtuele machines die u wilt gebruiken voor de service. De standaardwaarde is 1, maar u kunt maximaal 16 virtuele machines voor de service uitvoeren.

    >[!NOTE]
    >Als u een internet-proxy voor het cloud-gateway verbinding beheerpunt gebruikt, moet u het aantal poorten op de proxy verhogen door het aantal virtuele machines die u gebruikt, beginnend bij poort 10124.

    - Geef de persoonlijke sleutel (PFX-bestand) dat u hebt geëxporteerd uit het aangepaste certificaat voor SSL.

    - Geef het basiscertificaat zijn geëxporteerd uit het clientcertificaat.

    -   Geef de servicenaam dezelfde FQDN-naam die u hebt gebruikt toen u de nieuwe certificaatsjabloon gemaakt. U moet een van de volgende achtervoegsels voor de naam van de FQDN-service op basis van de Azure-cloud u opgeven:

    Azure-cloud | Voorvoegsel van de FQDN-naam
    --------------|-------------
    Serviceovereenkomstmetrieken (commercieel) | . cloudapp.net    
    Overheid van de cloud | . usgovcloudapp.net

  - Schakel het selectievakje naast **certificaatintrekking Client controleren** (tenzij u uw gegevens CRL openbaar publiceert).

  - Kies **volgende** als u klaar bent.

5. Als u bewaken cloud management gateway-verkeer met een drempelwaarde 14 dagen wilt, kiest u het selectievakje in om in te schakelen de drempelwaarde voor waarschuwing. Geef vervolgens de drempel en het percentage waarmee de verschillende waarschuwingsniveaus verhogen. Kies **volgende** als u klaar bent.

6. Controleer de instellingen en kies **volgende**. Configuration Manager start instellen van de service. Nadat u de wizard te sluiten die wordt uitgevoerd tussen 5 tot 15 minuten voor de inrichting van de service volledig in Azure. Controleer de **Status** kolom voor de nieuwe installatie cloud management gateway om te bepalen wanneer de service is klaar.

## <a name="step-5-configure-primary-site-for-client-certification-authentication"></a>Stap 5: Primaire site configureren voor verificatie van de certificeringsinstantie

1. Ga in de Configuration Manager-console naar **beheer** > **siteconfiguratie** > **Sites**.

2. Selecteer de primaire site van de clients die u wilt beheren via cloud management gateway en kies **eigenschappen**.

3. Controleer op het tabblad clientcommunicatie voor de Computer van het eigenschappenvenster van de primaire site **gebruik PKI-clientcertificaat (clientverificatie) indien beschikbaar**.

4. Zorg dat u **Clients controleren de certificaatintrekkingslijst (CRL) voor site-systemen**. Deze optie kan alleen worden vereist als u uw CRL openbaar zijn publiceren.


## <a name="step-6-add-the-cloud-management-gateway-connector-point"></a>Stap 6: Cloud-gateway-connector beheerpunt toevoegen

De cloud-gateway-connector beheerpunt is een nieuwe sitesysteemrol voor communicatie met cloud management gateway. Volg de instructies in de cloud gateway connector beheerpunt toevoegen, [sitesysteemrollen toevoegen voor System Center Configuration Manager](/sccm/core/servers/deploy/configure/add-site-system-roles).

## <a name="step-7-configure-roles-for-cloud-management-gateway-traffic"></a>Stap 7: Rollen configureert voor cloud management gateway-verkeer

De laatste stap bij het instellen van cloud management gateway is voor het configureren van de sitesysteemrollen voor het accepteren van cloud management gateway-verkeer. Alleen de beheerpunt, het distributiepunt en het software-update-punt rollen voor technische Preview 1606 worden ondersteund voor cloud management gateway. U moet elke rol afzonderlijk configureert.

1. Ga in de Configuration Manager-console naar **beheer** > **siteconfiguratie** > **Servers en sitesysteemrollen**.

2. Kies de sitesysteemserver voor de rol die u wilt configureren voor cloud management gateway-verkeer.

3. Kies de rol en kies **eigenschappen**.

4. Kies in het eigenschappenblad voor de rol, onder-clientverbindingen, **HTTPS**, schakel het selectievakje naast **toestaan Configuration Manager cloud management gateway verkeer**, en kies vervolgens **OK**. Herhaal deze stappen voor de resterende functies.

## <a name="step-8-configure-clients-for-cloud-management-gateway"></a>Stap 8: Clients configureren voor cloud management gateway

Na het beheer van cloud-gateway en de sitesysteemrollen volledig worden geconfigureerd en wordt uitgevoerd, ontvangen clients de locatie van de cloud management gateway-service automatisch op de volgende locatie-aanvraag. Clients moeten zich op het bedrijfsnetwerk naar de locatie van de cloud management gateway-service ontvangen. De polling-cyclus voor verzoeken om locatie wordt elke 24 uur. Als u niet wilt wachten tot de aanvraag normaal geplande locatie, kunt u de aanvraag forceren door de SMS Agent Host-service (ccmexec.exe) op de computer opnieuw te starten.

Met de locatie van de cloud management gateway-service op de client is geconfigureerd, kunt u automatisch bepalen of het is op het intranet of Internet. Als de client kan verbinding maken met de domeincontroller of het beheerpunt lokale deze worden gebruikt voor communicatie met Configuration Manager, anders wordt deze rekening brengen is op het Internet en gebruikt u de locatie van de cloud management gateway-service om te communiceren.

>[!NOTE]
> U kunt de client moet altijd gebruiken cloud management gateway ongeacht of deze op het intranet of Internet is afdwingen. Als u wilt doen, kunt u de volgende registersleutel op de clientcomputer instellen: \
>
> `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\CCM\Security, ClientAlwaysOnInternet = 1`

Om te bevestigen dat de client contact krijgen met Configuration Manager, kunt u de volgende PowerShell-opdracht uitvoeren op de clientcomputer:

`gwmi -namespace root\ccm\locationservices -class SMS_ActiveMPCandidate`

Deze opdracht geeft de beheerpunten die de client kan communiceren met inbegrip van de cloud management gateway-service.

## <a name="next-steps"></a>Volgende stappen

[Monitor voor clients voor cloud management gateway](monitor-clients-cloud-management-gateway.md)

