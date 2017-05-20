---
title: Cloud-gebaseerde distributiepunten installeren | Microsoft-documenten
description: Informatie over wat u moet doen om te starten met behulp van cloud-gebaseerde distributiepunten in Microsoft Azure.
ms.custom: na
ms.date: 2/8/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: bb83ac87-9914-4a35-b633-ad070031aa6e
caps.latest.revision: 7
author: Brenduns
ms.author: brenduns
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: f96905f50f879b843f98cb57c8a755aa856fb381
ms.openlocfilehash: 39b35cccf78bba4e69a7de0ca3a5a8dc516201e3
ms.contentlocale: nl-nl
ms.lasthandoff: 05/17/2017

---
# <a name="install-cloud-based-distribution-points-in-microsoft-azure-for-system-center-configuration-manager"></a>Cloud-gebaseerde distributiepunten installeren in Microsoft Azure voor System Center Configuration Manager

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*

U kunt System Center Configuration Manager cloud-gebaseerde distributiepunten installeren in Microsoft Azure. Als u niet bekend met cloud-gebaseerde distributiepunten bent, Zie [een cloud-gebaseerde distributiepunt gebruiken](../../../../core/plan-design/hierarchy/use-a-cloud-based-distribution-point.md) voordat u doorgaat.

 Voordat u de installatie begint, zorg ervoor dat u de vereiste certificaatbestanden:  

-   Een Microsoft Azure-beheercertificaat dat geëxporteerd is naar een cer-bestand en een pfx-bestand.  

-   Een Configuration Manager clouddistributiepunt-servicecertificaat dat geëxporteerd is naar een .pfx-bestand.  

    > [!TIP]
    >   Voor meer informatie over deze certificaten, Zie de sectie voor cloud-gebaseerde distributiepunten in de [PKI-certificaatvereisten voor System Center Configuration Manager](../../../../core/plan-design/network/pki-certificate-requirements.md) onderwerp. Voor een Voorbeeldimplementatie van het clouddistributiepunt-servicecertificaat, Zie de sectie "Het servicecertificaat voor Cloud-gebaseerde distributiepunten implementeren" in [voorbeeld van stapsgewijze implementatie van de PKI-certificaten voor System Center Configuration Manager: Windows Server 2008-certificeringsinstantie](/sccm/core/plan-design/network/example-deployment-of-pki-certificates).  


 Nadat u het cloud-gebaseerde distributiepunt installeert, Azure automatisch een GUID voor de service genereert, en voegt dit samen met de DNS-achtervoegsel van **cloudapp.net**. Deze GUID moet u DNS configureren met een DNS-alias (CNAME-record). Hiermee kunt u de servicenaam die u in de Configuration Manager clouddistributiepunt-servicecertificaat van de automatisch gegenereerde GUID definieert.  

 Als u een proxywebserver gebruikt, moet u wellicht configureren van proxyinstellingen voor communicatie met de cloudservice die als host fungeert voor het distributiepunt.  

##  <a name="BKMK_ConfigWindowsAzureandInstallDP"></a>Instellen van Azure en het installeren van cloud-gebaseerde distributiepunten  
 Gebruik de volgende procedures voor het instellen van Azure ter ondersteuning van distributiepunten en installeer het cloud-gebaseerde distributiepunt in Configuration Manager.  

### <a name="to-set-up-a-cloud-service-in-azure-for-a-distribution-point"></a>Voor het instellen van een cloudservice in Azure voor een distributiepunt  

1.  Open een webbrowser naar de Azure-portal op https://manage.windowsazure.com, en toegang tot uw account.  

2.  Klik op **gehoste Services, Opslagaccounts & CDN**, en selecteer vervolgens **Beheercertificaten**.  

3.  Met de rechtermuisknop op uw abonnement en selecteer vervolgens **certificaat toevoegen**.  

4.  Voor **certificaatbestand**, geef het .cer-bestand met de geëxporteerde Azure management-certificaat te gebruiken voor deze cloudservice en klik vervolgens op **OK**.  

Het beheercertificaat wordt geladen in Azure en u kunt nu een clouddistributiepunt installeren.  

### <a name="to-install-a-cloud-based-distribution-point-for-configuration-manager"></a>Voor het installeren van een cloud-gebaseerde distributiepunt voor Configuration Manager  

1.  Volg de stappen in de vorige procedure voor het instellen van een cloudservice in Azure met een beheercertificaat.  

2.  In de **beheer** werkruimte van de Configuration Manager-console, vouw **Cloudservices**, en selecteer **Clouddistributiepunten**. Op de **Start** tabblad **Clouddistributiepunt maken**.  

3.  Op de **algemeen** pagina van de Wizard Cloud maken Distribution Point, stel het volgende:  

    -   Geef de **abonnements-ID** voor uw Azure-account.  

        > [!TIP]  
        >  U kunt uw Azure-abonnement-ID vinden in de Azure-portal.  

    -   Geef de **beheercertificaat**. Klik op **Bladeren** opgeven van het pfx-bestand dat de geëxporteerde Azure-beheercertificaat bevat en voer het wachtwoord voor het certificaat. Eventueel kunt u een versie 1 .publishsettings-bestand van Azure SDK 1.7.  

4.  Klik op **Volgende**. Configuration Manager maakt verbinding met Azure om het beheercertificaat te valideren.  

5.  Op de **instellingen** pagina en klik vervolgens op het volgende voltooien **volgende**:  

    -   Voor **regio**, selecteert u de Azure-regio waar u wilt maken van de cloudservice die als host fungeert voor dit distributiepunt.  

    -   Voor **certificaatbestand**, geef het .pfx-bestand dat het geëxporteerde certificaat voor de Configuration Manager cloud-gebaseerde distributiepuntservice bevat. Voer het wachtwoord.  

        > [!NOTE]  
        >  De **Service FQDN** vakje wordt automatisch ingevuld vanuit de naam van de certificaathouder. In de meeste gevallen hoeft u niet worden bewerkt. De uitzondering is als u een certificaat met jokertekens gebruikt in een testomgeving. Bijvoorbeeld, in dit geval u mogelijk niet opgeven de hostnaam, zodat meerdere computers, die hetzelfde DNS-achtervoegsel hebben hetzelfde certificaat kunnen gebruiken. In dit scenario bevat het certificaatonderwerp een waarde gelijkaardig aan **CN =\*. contoso.com**, en Configuration Manager wordt een bericht weergegeven dat u de juiste FQDN moet opgeven. Klik op **OK** om het bericht te sluiten en voer vervolgens een specifieke naam in voor het DNS-achtervoegsel om een volledige FQDN te leveren. U kunt bijvoorbeeld toevoegen **clouddp1** om op te geven van de volledige FQDN-service van **clouddp1.contoso.com**. De FQDN-Service moet uniek zijn in uw domein en niet overeenkomt met elk apparaat domein.  
        >   
        >  Certificaten jokertekens worden ondersteund voor testomgevingen die alleen.  

6.  Op de **waarschuwingen** pagina, opslagquota, transferquota en op welk percentage van deze quota u wilt dat Configuration Manager voor het genereren van waarschuwingen instellen. Klik op **Volgende**.  

7.  Voltooi de wizard.  

De wizard maakt een nieuwe gehoste service voor het cloud-gebaseerde distributiepunt. Nadat u de wizard sluit, kunt u de voortgang van de installatie van het cloud-gebaseerde distributiepunt in de Configuration Manager-console bewaken. U kunt ook bewaken de **CloudMgr.log** -bestand op de primaire siteserver. U kunt de inrichting van de cloudservice in de Azure-portal bewaken.  

> [!NOTE]  
>  Het kan tot 30 minuten duren voor de inrichting van een nieuw distributiepunt in Azure uitvoeren. Het volgende bericht wordt herhaald in de **CloudMgr.log** bestand tot de opslagaccount ingericht: **Wachten op controle als container bestaat. We controleren opnieuw over 10 seconden**. De service wordt vervolgens gemaakt en geconfigureerd.  

 U kunt identificeren dat de installatie van de cloud-gebaseerde distributiepunt is voltooid met behulp van de volgende methoden:  

-   In de Azure-portal de **implementatie** voor het clouddistributiepunt een status weer van **gereed**.  

-   In de Configuration Manager-console in de **beheer** werkruimte **Hiërarchieconfiguratie**, **Cloud** knooppunt, het clouddistributiepunt een status weer van **gereed**.  

-   Configuration Manager geeft een statusbericht-ID **9409** voor het onderdeel sms_cloud_services_manager.  

##  <a name="BKMK_ConfigDNSforCloudDPs"></a>Naamomzetting voor cloud-gebaseerde distributiepunten instellen  
 Voordat clients toegang de cloud-gebaseerd distributiepunt tot, moeten ze kunnen de naam van het cloud-gebaseerde distributiepunt omzetten naar een IP-adres dat wordt beheerd Azure zijn. Clients doen dit in twee fasen:  

1.  Ze wijzen de servicenaam die u opgaf met het certificaat van de Configuration Manager cloud-gebaseerde distributiepuntservice uw Azure FQDN-naam van de service. Deze FDQN-naam bevat een GUID en het DNS-achtervoegsel van **cloudapp.net**. De GUID wordt automatisch gegenereerd nadat u het cloud-gebaseerde distributiepunt installeert. U kunt de volledige FQDN-naam in de Azure-portal zien door te verwijzen naar de **SITE-URL** in het dashboard van de cloudservice. Een voorbeeld van een site-URL is **http://d1594d4527614a09b934d470.cloudapp.net**.  

2.  Ze zetten de Azure-service omzetten naar het IP-adres dat Azure toewijst. Dit IP-adres kan ook worden geïdentificeerd in het dashboard voor de cloudservice in de Azure-portal en heet **publiek VIRTUEEL IP-adres (VIP)**.  

Om de servicenaam die u hebt opgegeven met de Configuration Manager clouddistributiepunt-servicecertificaat (bijvoorbeeld **clouddp1.contoso.com**) naar uw Azure FQDN-service (bijvoorbeeld **d1594d4527614a09b934d470.cloudapp.net**), DNS-servers op het Internet moeten beschikken over een DNS-alias (CNAME-record). Clients kunnen vervolgens de FDQN de Azure-service omzetten naar het IP-adres met behulp van DNS-servers op het Internet.  

##  <a name="BKMK_ConfigProxyforCloud"></a>Instellen van proxy-instellingen voor primaire sites die cloudservices beheren  
 Als u cloudservices met Configuration Manager, is de primaire site die het cloud-gebaseerde distributiepunt beheert moet verbinding maken met de Azure-portal. De site verbinding maakt met behulp van de **System** -account van de computer van de primaire site. Deze verbinding wordt gemaakt met behulp van de standaardwebbrowser op de servercomputer van de primaire site.  

 Op de primaire siteserver die het cloud-gebaseerde distributiepunt beheert, moet u wellicht de proxy-instellingen instellen zodat de primaire site voor toegang tot het Internet en Azure.  

 Gebruik de volgende procedure voor het instellen van proxy-instellingen voor de primaire server in de Configuration Manager-console.  

> [!TIP]  
>  U kunt ook instellen de proxyserver wanneer u nieuwe sitesysteemrollen op de primaire server met behulp van installeert de **toevoegen Wizard sitesysteemrollen**.  

#### <a name="to-set-up-proxy-settings-for-the-primary-site-server"></a>Proxy-instellingen voor de primaire server instellen  

1.  Klik op **Beheer**in de Configuration Manager-console.  

2.  Vouw **Siteconfiguratie** uit in de werkruimte **Beheer**en klik vervolgens op **Servers en sitesysteemrollen**. Selecteer vervolgens de primaire siteserver die het cloud-gebaseerde distributiepunt beheert.  

3.  In het detailvenster met de rechtermuisknop op **sitesysteem**, en klik vervolgens op **eigenschappen**.  

4.  In **Sitesysteemeigenschappen**, selecteer de **Proxy** tabblad, en vervolgens de proxy-instellingen voor deze primaire siteserver.  

5.  Klik op **OK** de instellingen op te slaan.  

