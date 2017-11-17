---
title: Beheergateway voor Cloud instellen
titleSuffix: Configuration Manager
description: 
author: arob98
ms.author: angrobe
manager: angrobe
ms.date: 09/26/2017
ms.topic: article
ms.prod: configuration-manager
ms.service: 
ms.technology: configmgr-client
ms.assetid: e0ec7d66-1502-4b31-85bb-94996b1bc66f
ms.openlocfilehash: 7463cd7199098b21843fd5b99ed284a12ff91e00
ms.sourcegitcommit: 986fc2d54f7c5fa965fd4df42f4db4ecce6b79cb
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 11/17/2017
---
# <a name="set-up-cloud-management-gateway-for-configuration-manager"></a>Instellen van de cloud management gateway voor Configuration Manager

*Van toepassing op: System Center Configuration Manager (huidige vertakking)* het proces voor het instellen van cloudgateway management in Configuration Manager bevat de volgende stappen uit:

## <a name="step-1-configure-required-certificates"></a>Stap 1: Vereiste certificaten configureren

> [!TIP]  
> Voordat u een certificaat aanvraagt, bevestig dat de naam van de gewenste Azure-domein (bijvoorbeeld GraniteFalls.CloudApp.Net) uniek is. Om dit te doen, meld u aan bij de [Microsoft Azure-portal](https://manage.windowsazure.com), klikt u op **nieuw**, selecteer **Cloudservice**, en vervolgens **aangepast maken**. In de **URL** veldtype de gewenste domeinnaam (Klik niet op het vinkje om aan te maken van de service). De portal wordt weergegeven of de domeinnaam beschikbaar is of wordt al gebruikt door een andere service.

### <a name="option-1-preferred---use-the-server-authentication-certificate-from-a-public-and-globally-trusted-certificate-provider-like-verisign"></a>Optie 1 (voorkeur): gebruik het serverauthenticatiecertificaat van een provider van openbare en globaal vertrouwd certificaat (zoals VeriSign)

Wanneer u deze methode gebruikt, clients het certificaat automatisch vertrouwen en hoeft niet te maken van een aangepaste SSL-certificaat.

1. Maak een canonieke naamrecord (CNAME) in uw organisatie openbare domeinnaamservices (DNS) voor het maken van een alias voor de cloud management gateway-service naar een beschrijvende naam die wordt gebruikt in het openbare certificaat.
Bijvoorbeeld, hun cloud management gateway-service de namen van Contoso **GraniteFalls**, die in Azure worden **GraniteFalls.CloudApp.Net**. In de Contoso openbare DNS-contoso.com naamruimte, de DNS-beheerder maakt een nieuwe CNAME-record voor **GraniteFalls.Contoso.com** voor de werkelijke hostnaam **GraniteFalls.CloudApp.net**.
2. Vervolgens een certificaat voor serververificatie aanvragen van een openbare provider met behulp van de algemene naam (CN) van de CNAME-alias.
Bijvoorbeeld Contoso maakt gebruik van **GraniteFalls.Contoso.com** voor de algemene naam van het certificaat.
3. De cloud management gateway-service in de Configuration Manager-console met dit certificaat maken.
    - Op de **instellingen** pagina van de Wizard Cloud maken Management Gateway: Wanneer u het servercertificaat voor deze cloudservice toevoegen (van **certificaatbestand**), de wizard wordt de hostnaam van de algemene naam als de servicenaam van de van het certificaat uitpakken en voeg die u wilt **cloudapp.net**(of **usgovcloudapp.net** voor het Azure US Government-cloud) als de FQDN-Service de service te maken in Azure.
Bijvoorbeeld, bij het maken van de cloud management gateway bij Contoso, de hostnaam van de **GraniteFalls** wordt opgehaald uit het certificaat CN, zodat de werkelijke service in Azure als gemaakt **GraniteFalls.CloudApp.net**.

### <a name="option-2---create-a-custom-ssl-certificate-for-cloud-management-gateway-in-the-same-way-as-for-a-cloud-based-distribution-point"></a>Optie 2: een aangepaste SSL-certificaat voor cloud-management-gateway maken op dezelfde manier als voor een cloud-gebaseerd distributiepunt

U kunt een aangepaste SSL-certificaat voor cloud-management-gateway maken op dezelfde manier als die u dit voor een cloud-gebaseerd distributiepunt doen zou. Volg de instructies voor [het servicecertificaat voor Cloud-gebaseerde distributiepunten implementeren](/sccm/core/plan-design/network/example-deployment-of-pki-certificates) maar anders de volgende dingen doen:

- Bij het aanvragen van het aangepaste Webservercertificaat bieden u een FQDN-naam voor de algemene naam van het certificaat dat met eindigt **cloudapp.net** voor het gebruik van cloud-beheergateway op Azure openbare cloud of **usgovcloudapp.net** voor de overheid van de Azure-cloud.


## <a name="step-2-export-the-client-certificates-root"></a>Stap 2: Hoofdmap van het clientcertificaat exporteren

De eenvoudigste manier om te exporteren van de hoofdmap van de clientcertificaten gebruikt op het netwerk is een certificaat op een van de domein-machines met een open en kopiëren.

> [!NOTE]
>
> Clientcertificaten zijn vereist op elke computer die u wilt beheren met cloud management gateway en wijs op de sitesysteemserver die als host fungeert voor de cloud management gateway-connector. Als u moet een certificaat toevoegen aan een van deze apparaten, Zie [implementeren van de Client-certificaat voor Windows-Computers](/sccm/core/plan-design/network/example-deployment-of-pki-certificates#BKMK_client2008_cm2012).

1.  Typ in het venster uitvoeren **mmc** en drukt u op terug.

2.  Kies in het menu bestand **module toevoegen/verwijderen...** .

3.  Kies in het dialoogvenster Add of Remove-modules **certificaten** > **toevoegen &gt;**   >  **computeraccount** > **volgende** > **lokale computer** > **voltooien**.

4.  Ga naar **certificaten** &gt; **persoonlijke** &gt; **certificaten**.

5.  Dubbelklik op het certificaat voor clientverificatie op de computer, kies het tabblad certificeringspad en dubbelklikt u op de basiscertificeringsinstantie (aan de bovenkant van het pad).

6.  Kies op het tabblad met Details **kopiëren naar bestand...** .

7.  Voltooi de Wizard Certificaat exporteren met behulp van de standaardindeling van het certificaat. Controleer de naam en locatie van het basiscertificaat dat u maakt. U moet het configureren van beheer cloudgateway in een [later stap](#step-4-set-up-cloud-management-gateway).

>[!NOTE]
>Als het clientcertificaat is uitgegeven door een onderliggende certificeringsinstantie moet u deze stap herhalen voor elk certificaat in de keten.

## <a name="step-3-upload-the-management-certificate-to-azure"></a>Stap 3: Het management-certificaat uploaden naar Azure

Een Azure-beheercertificaat is vereist voor Configuration Manager voor toegang tot de Azure-API en cloud management gateway configureert. Zie de volgende artikelen in de Azure-documentatie voor meer informatie en instructies voor het uploaden van een beheercertificaat:

- [Certificaten voor Azure Cloud Services-overzicht](https://azure.microsoft.com/documentation/articles/cloud-services-certs-create/)

- [Een Azure Management API Management-certificaat uploaden](https://azure.microsoft.com/documentation/articles/azure-api-management-certs/)

>[!IMPORTANT]
>Zorg ervoor dat de abonnements-ID die is gekoppeld aan het beheercertificaat te kopiëren. U hebt deze voor het configureren van beheer cloudgateway in de Configuration Manager-console in de [volgende stap](#step-4-set-up-cloud-management-gateway).



## <a name="step-4-set-up-cloud-management-gateway"></a>Stap 4: Beheergateway voor cloud instellen

>[!NOTE]
>In versie 1610 is cloud management gateway een voorlopige versie-functie. Als u wilt inschakelen, Zie [functies van evaluatieversies van updates gebruiken](/sccm/core/servers/manage/install-in-console-updates#bkmk_prerelease).

1. Ga in de Configuration Manager-console naar **beheer** > **Cloudservices** > **Cloud Management Gateway**.
2. Kies **Cloud Management Gateway maken**.

3. Voer uw Azure-abonnement-ID (overgenomen van de Azure-beheerportal) in de Wizard Cloud maken Management Gateway, en blader naar het certificaatbestand dat u gebruikt voor het uploaden als een Azure-beheercertificaat. Kies **volgende** en wacht enkele ogenblikken voor de console verbinding maken met Azure.

4. Vul in de aanvullende informatie in de wizard:

    - Geef de naam voor de service die wordt uitgevoerd in Azure. Servicenaam moet alleen alfanumerieke tekens en 3 tot 24 tekens lang zijn.

    - Kies de gewenste de service worden uitgevoerd in Azure-regio.

    - Geef het aantal virtuele machines die u wilt gebruiken voor de service. De standaardwaarde is 1, maar u kunt maximaal 16 virtuele machines voor de service uitvoert.

    >[!NOTE]
    >Als u een InternetProxy voor het cloudverbindingspunt management gateway gebruikt, moet u het aantal poorten op de proxy door het aantal virtuele machines die u gebruikt, beginnend bij poort 10124 verhogen.

    - Geef de persoonlijke sleutel (PFX-bestand) die u hebt geëxporteerd uit het aangepaste certificaat voor SSL.

    - Geef het basiscertificaat (en eventuele onderliggende certificaten) die zijn geëxporteerd uit het clientcertificaat. De wizard accepteert maximaal twee basiscertificaten en vier onderliggende certificaten.

    -   Geef de servicenaam dezelfde FQDN-naam die u hebt gebruikt toen u de nieuwe certificaatsjabloon gemaakt. Een van de volgende achtervoegsels voor de naam van de FQDN-service op basis van de Azure-cloud die u gebruikt, moet u opgeven:

    Azure-cloud | FQDN-voorvoegsel
    --------------|-------------
    Openbare (commercieel) cloud | . cloudapp.net    
    Cloud van de overheid | . usgovcloudapp.net

  - Schakel het selectievakje naast **certificaatintrekking Client controleren** (tenzij u uw CRL-gegevens openbaar publiceert).

  - Kies **volgende** wanneer u klaar bent.

5. Als u bewaken cloud management gateway-verkeer met een drempelwaarde 14 dagen wilt, kiest u het selectievakje in om in te schakelen drempelwaarde voor waarschuwing. Geef vervolgens de drempelwaarde en het percentage waarmee de verschillende waarschuwingsniveaus verhogen. Kies **volgende** wanneer u klaar bent.

6. Controleer de instellingen en kies **volgende**. Configuration Manager start instellen van de service. Nadat u de wizard sluit, duurt het tussen 5 tot 15 minuten voor het inrichten van de service volledig in Azure. Controleer de **Status** kolom voor het beheer van de nieuwe cloudgateway om te bepalen wanneer de service is klaar.

## <a name="step-5-configure-primary-site-for-client-certification-authentication"></a>Stap 5: Primaire site voor clientverificatie certificeringsinstantie configureren

1. Ga in de Configuration Manager-console naar **beheer** > **siteconfiguratie** > **Sites**.

2. Selecteer de primaire site voor de clients die u wilt beheren via cloud management gateway en kies **eigenschappen**.

3. Controleer op het tabblad clientcommunicatie voor de Computer van het eigenschappenvenster van de primaire site, **gebruik PKI-clientcertificaat (clientverificatie) indien beschikbaar**.

4. Zorg dat u **Clients controleren de certificaatintrekkingslijst (CRL) voor sitesystemen**. Deze optie alleen zijn vereist als u uw CRL openbaar zijn publiceren.


## <a name="step-6-add-the-cloud-management-gateway-connector-point"></a>Stap 6: Het cloud-gateway connector beheerpunt toevoegen

De cloud gateway connector beheerpunt is een nieuwe sitesysteemrol voor communicatie met de cloud management gateway. Als u wilt toevoegen op het cloud-gateway connector beheerpunt, volg de instructies in [sitesysteemrollen voor System Center Configuration Manager toevoegen](/sccm/core/servers/deploy/configure/add-site-system-roles).

## <a name="step-7-configure-roles-for-cloud-management-gateway-traffic"></a>Stap 7: Rollen voor verkeer van de cloud management gateway configureren

De laatste stap bij het instellen van de cloud management gateway is voor het configureren van de sitesysteemrollen voor het accepteren van verkeer van de cloud management gateway. Alleen de management point- and -software-update-punt functies worden ondersteund voor cloud management gateway. U configureren elke rol afzonderlijk.

1. Ga in de Configuration Manager-console naar **beheer** > **siteconfiguratie** > **Servers en sitesysteemrollen**.

2. Kies de sitesysteemserver voor de rol die u wilt configureren voor cloud management gateway-netwerkverkeer.

3. Selecteer de rol in en kies vervolgens **eigenschappen**.

4. In het eigenschappenvenster van de rol onder-clientverbindingen, schakel het selectievakje in naast **toestaan Configuration Manager-gateway cloud beheer van verkeer**, en kies vervolgens **OK**. Herhaal deze stappen voor de overige rollen. Inschakelen van de **HTTPS** optie ook als een best practice bij beveiliging wordt aanbevolen, maar is niet vereist.

## <a name="step-8-configure-clients-for-cloud-management-gateway"></a>Stap 8: Clients configureren voor cloud-beheergateway

Nadat de cloud management gateway en de sitesysteemrollen volledig zijn geconfigureerd en actief is, krijgen clients de locatie van de cloud management gateway-service automatisch op de volgende locatie-aanvraag. Clients moeten zich op het bedrijfsnetwerk naar de locatie van de cloud management gateway-service ontvangen. De polling-cyclus voor verzoeken om de locatie is om de 24 uur. Als u niet wilt wachten tot de aanvraag normaal geplande locatie, dwingt u de aanvraag door de SMS Agent Host-service (ccmexec.exe) op de computer opnieuw te starten.

Met de locatie van de cloud management gateway-service op de client is geconfigureerd, kunt u automatisch bepalen of deze zich op het intranet of Internet. Als de client contact opneemt met de domeincontroller of de on-premises beheerpunt, wordt dit gebruikt voor communicatie met Configuration Manager. Anders worden deze beschouwd als deze zich op het Internet en de locatie van de cloud management gateway-service gebruiken om te communiceren.

>[!NOTE]
> U kunt afdwingen dat de client altijd management cloudgateway ongeacht of het op het intranet of Internet gebruiken. Als u wilt doen, kunt u de volgende registersleutel instellen op de clientcomputer: \
>
> `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\CCM\Security, ClientAlwaysOnInternet = 1`

Om te controleren dat clients verbinding maken met Configuration Manager, kunt u de volgende PowerShell-opdracht uitvoeren op de clientcomputer:

`gwmi -namespace root\ccm\locationservices -class SMS_ActiveMPCandidate`

Deze opdracht geeft de beheerpunten die de client kunt contact opnemen met inbegrip van de cloud management gateway-service.

## <a name="next-steps"></a>Volgende stappen

[Clients controleren voor cloud-beheergateway](monitor-clients-cloud-management-gateway.md)
