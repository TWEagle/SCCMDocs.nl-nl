---
title: Cloud-gebaseerde distributiepunten installeren
titleSuffix: Configuration Manager
description: Meer informatie over wat u moet doen om aan de slag met cloud-gebaseerde distributiepunten in Microsoft Azure.
ms.custom: na
ms.date: 2/8/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: bb83ac87-9914-4a35-b633-ad070031aa6e
caps.latest.revision: "7"
author: mestew
ms.author: mstewart
manager: angrobe
ms.openlocfilehash: 6471ac81718666403127c0ebcfaa19c41d3af47b
ms.sourcegitcommit: daa080cf220835f157a23e8c8e2bd2781b869bb7
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/04/2017
---
# <a name="install-cloud-based-distribution-points-in-microsoft-azure-for-system-center-configuration-manager"></a>Cloud-gebaseerde distributiepunten in Microsoft Azure voor System Center Configuration Manager installeren

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*

U kunt System Center Configuration Manager cloud-gebaseerde distributiepunten installeren in Microsoft Azure. Als u niet bekend met cloud-gebaseerde distributiepunten bent, Zie [een cloud-gebaseerd distributiepunt gebruiken](../../../../core/plan-design/hierarchy/use-a-cloud-based-distribution-point.md) voordat u doorgaat.

 Voordat u de installatie begint, zorg ervoor dat u de vereiste certificaatbestanden hebt:  

-   Een Microsoft Azure-beheercertificaat dat geëxporteerd is naar een cer-bestand en een pfx-bestand.  

-   Een Configuration Manager clouddistributiepunt-servicecertificaat dat geëxporteerd is naar een pfx-bestand.  

    > [!TIP]
    >   Zie voor meer informatie over deze certificaten de sectie voor cloud-gebaseerde distributiepunten in de [PKI-certificaatvereisten voor System Center Configuration Manager](../../../../core/plan-design/network/pki-certificate-requirements.md) onderwerp. Voor een Voorbeeldimplementatie van het clouddistributiepunt-servicecertificaat, Zie de sectie 'Het servicecertificaat voor Cloud-gebaseerde distributiepunten implementeren' in [voorbeeld van stapsgewijze implementatie van de PKI-certificaten voor System Center Configuration Manager: Windows Server 2008-certificeringsinstantie](/sccm/core/plan-design/network/example-deployment-of-pki-certificates).  


 Nadat u het cloud-gebaseerde distributiepunt installeert, Azure automatisch een GUID voor de service genereert en voegt dit samen met de DNS-achtervoegsel van **cloudapp.net**. Deze GUID moet u DNS configureren met een DNS-alias (CNAME-record). Hiermee kunt u de servicenaam die u in de Configuration Manager clouddistributiepunt-servicecertificaat op de automatisch gegenereerde GUID definieert.  

 Als u een proxywebserver gebruikt, moet u wellicht de proxy-instellingen om te kunnen communiceren met de cloudservice die als host fungeert voor het distributiepunt configureren.  

##  <a name="BKMK_ConfigWindowsAzureandInstallDP"></a>Instellen van Azure en het installeren van cloud-gebaseerde distributiepunten  
 Gebruik de volgende procedures voor het instellen van Azure voor de ondersteuning van distributiepunten en installeer het cloud-gebaseerde distributiepunt in Configuration Manager.  

### <a name="to-set-up-a-cloud-service-in-azure-for-a-distribution-point"></a>Voor het instellen van een cloudservice in Azure voor een distributiepunt  

1.  Open een webbrowser naar de Azure-portal op https://manage.windowsazure.com, en toegang tot uw account.  

2.  Klik op **gehoste Services, Opslagaccounts & CDN**, en selecteer vervolgens **Beheercertificaten**.  

3.  Met de rechtermuisknop op uw abonnement en selecteer vervolgens **certificaat toevoegen**.  

4.  Voor **certificaatbestand**, geef het .cer-bestand waarin de geëxporteerde Azure-beheercertificaat wilt gebruiken voor deze cloudservice en klik vervolgens op **OK**.  

Het beheercertificaat wordt geladen in Azure en u kunt nu een clouddistributiepunt installeren.  

### <a name="to-install-a-cloud-based-distribution-point-for-configuration-manager"></a>Voor het installeren van een cloud-gebaseerde distributiepunt voor Configuration Manager  

1.  Voltooi de stappen in de voorgaande procedure voor het instellen van een cloudservice in Azure met een beheercertificaat.  

2.  In de **beheer** werkruimte van de Configuration Manager-console, vouw **Cloudservices**, en selecteer **Clouddistributiepunten**. Op de **Start** tabblad **Clouddistributiepunt maken**.  

3.  Op de **algemene** pagina van de Wizard Cloud maken Distribution Point, stel het volgende:  

    -   Geef de **abonnements-ID** voor uw Azure-account.  

        > [!TIP]  
        >  U kunt uw Azure-abonnement-ID vinden in de Azure portal.  

    -   Geef de **beheercertificaat**. Klik op **Bladeren** opgeven van het pfx-bestand dat de geëxporteerde Azure-beheercertificaat bevat en voer vervolgens het wachtwoord voor het certificaat. Desgewenst kunt u een versie 1 .publishsettings-bestand uit Azure SDK 1.7.  

4.  Klik op **Volgende**. Configuration Manager maakt verbinding met Azure om het beheercertificaat te valideren.  

5.  Op de **instellingen** pagina en klik vervolgens op het volgende voltooien **volgende**:  

    -   Voor **regio**, selecteert u de Azure-regio waar u wilt maken van de cloudservice die als host fungeert voor dit distributiepunt.  

    -   Voor **certificaatbestand**, geef het .pfx-bestand dat het geëxporteerde certificaat voor de Configuration Manager cloud-gebaseerde distributiepuntservice bevat. Voer vervolgens het wachtwoord.  

        > [!NOTE]  
        >  De **Service FQDN** vakje wordt automatisch ingevuld vanuit de naam van de certificaathouder. In de meeste gevallen hoeft u niet te bewerken. De uitzondering hierop is als u een jokertekencertificaat in een testomgeving gebruikt. Bijvoorbeeld, in dit geval u mogelijk niet Geef de hostnaam, zodat meerdere computers met de dezelfde DNS-achtervoegsel het certificaat kunnen gebruiken. In dit scenario bevat het certificaatonderwerp een waarde gelijkaardig aan **CN =\*. contoso.com**, en Configuration Manager wordt een bericht weergegeven dat u de juiste FQDN-naam moet opgeven. Klik op **OK** om te sluiten van het bericht en voer vervolgens een specifieke naam in voor het DNS-achtervoegsel om een volledige FQDN te leveren. U kunt bijvoorbeeld toevoegen **clouddp1** om op te geven van de volledige FQDN voor de service **clouddp1.contoso.com**. De FQDN-Service moet uniek zijn in uw domein en niet overeen met elk apparaat voor het domein.  
        >   
        >  Jokertekens-certificaten worden ondersteund voor testomgevingen alleen.  

6.  Op de **waarschuwingen** pagina, opslagquota, transferquota en op welk percentage van deze quota u wilt dat Configuration Manager voor het genereren van waarschuwingen instellen. Klik op **Volgende**.  

7.  Voltooi de wizard.  

De wizard maakt een nieuwe gehoste service voor het cloud-gebaseerd distributiepunt. Nadat u de wizard sluit, kunt u de voortgang van de installatie van het cloud-gebaseerde distributiepunt in de Configuration Manager-console kunt bewaken. U kunt ook bewaken de **CloudMgr.log** -bestand op de primaire siteserver. U kunt de inrichting van de cloudservice in de Azure portal bewaken.  

> [!NOTE]  
>  Het kan tot 30 minuten voor het inrichten van een nieuw distributiepunt in Azure duren. Het volgende bericht wordt herhaald in de **CloudMgr.log** bestand totdat het opslagaccount is ingericht: **Wachten op controle als container bestaat. We controleren opnieuw over 10 seconden**. De service wordt vervolgens gemaakt en geconfigureerd.  

 U kunt identificeren dat de installatie van het cloud-gebaseerde distributiepunt is voltooid met behulp van de volgende methoden:  

-   In de Azure portal, de **implementatie** voor het clouddistributiepunt een status weer van **gereed**.  

-   In de Configuration Manager-console in de **beheer** werkruimte **Hiërarchieconfiguratie**, **Cloud** knooppunt het clouddistributiepunt een status weer van **gereed**.  

-   Configuration Manager geeft een statusbericht-ID **9409** voor het onderdeel sms_cloud_services_manager.  

##  <a name="BKMK_ConfigDNSforCloudDPs"></a>Naamomzetting voor cloud-gebaseerde distributiepunten instellen  
 Voordat clients toegang de cloud-gebaseerd distributiepunt tot, moeten ze kunnen de naam van het cloud-gebaseerde distributiepunt omzetten in een IP-adres dat wordt beheerd Azure zijn. Clients doen dit in twee fasen:  

1.  Ze wijzen de servicenaam die u opgaf met het certificaat van de Configuration Manager cloud-gebaseerde distributiepuntservice FQDN-naam van uw Azure Service. Deze FDQN-naam bevat een GUID en het DNS-achtervoegsel van **cloudapp.net**. De GUID wordt automatisch gegenereerd nadat u de cloud-gebaseerde distributiepunt installeert. Ziet u de volledige FQDN-naam in de Azure portal door te verwijzen naar de **SITE-URL** in het dashboard van de cloudservice. Een voorbeeld van een site-URL is **http://d1594d4527614a09b934d470.cloudapp.net**.  

2.  Ze zetten de FDQN van de Azure service het IP-adres dat Azure toewijst. Dit IP-adres kan ook worden geïdentificeerd in het dashboard voor de cloudservice in de Azure-portal en de naam is **publiek VIRTUEEL IP-adres (VIP)**.  

Om de servicenaam die u opgaf met het Configuration Manager clouddistributiepunt-servicecertificaat (bijvoorbeeld **clouddp1.contoso.com**) voor uw Azure-FQDN-naam (bijvoorbeeld **d1594d4527614a09b934d470.cloudapp.net**), DNS-servers op het Internet moeten beschikken over een DNS-alias (CNAME-record). Clients kunnen vervolgens de FDQN van de Azure service het IP-adres omzetten via DNS-servers op het Internet.  

##  <a name="BKMK_ConfigProxyforCloud"></a>Instellen van de proxy-instellingen voor primaire sites die cloudservices beheren  
 Wanneer u cloudservices met Configuration Manager gebruikt, is de primaire site die het cloud-gebaseerde distributiepunt beheert moet verbinding maken met de Azure-portal. De site verbinding maakt met behulp van de **System** -account van de computer van de primaire site. Deze verbinding wordt gemaakt met behulp van de standaardwebbrowser op de primaire site server-computer.  

 Op de primaire siteserver die het cloud-gebaseerde distributiepunt beheert, moet u wellicht proxy-instellingen instellen voor het inschakelen van de primaire site voor toegang tot het Internet en Azure.  

 Gebruik de volgende procedure voor het instellen van de proxy-instellingen voor de primaire siteserver in de Configuration Manager-console.  

> [!TIP]  
>  U kunt ook instellen de proxyserver wanneer u nieuwe sitesysteemrollen op de primaire siteserver met behulp van installeren de **toevoegen Wizard sitesysteemrollen**.  

#### <a name="to-set-up-proxy-settings-for-the-primary-site-server"></a>Proxy-instellingen voor de primaire server instellen  

1.  Klik op **Beheer**in de Configuration Manager-console.  

2.  Vouw **Siteconfiguratie** uit in de werkruimte **Beheer**en klik vervolgens op **Servers en sitesysteemrollen**. Selecteer vervolgens de primaire siteserver die het cloud-gebaseerde distributiepunt beheert.  

3.  In het detailvenster met de rechtermuisknop op **sitesysteem**, en klik vervolgens op **eigenschappen**.  

4.  In **Sitesysteemeigenschappen**, selecteer de **Proxy** tabblad en vervolgens de proxy-instellingen voor deze primaire siteserver instellen.  

5.  Klik op **OK** de instellingen op te slaan.  
