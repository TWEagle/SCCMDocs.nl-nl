---
title: CMG certificaten
description: Meer informatie over de verschillende digitale certificaten voor gebruik met de cloud management gateway.
author: aczechowski
ms.author: aaroncz
manager: dougeby
ms.date: 03/22/2018
ms.topic: article
ms.prod: configuration-manager
ms.technology:
- configmgr-other
ms.assetid: 71eaa409-b955-45d6-8309-26bf3b3b0911
ms.openlocfilehash: 0e4d2add8ece7f548955064a479d9545a1fc64e1
ms.sourcegitcommit: a19e12d5c3198764901d44f4df7c60eb542e765f
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 03/28/2018
---
# <a name="certificates-for-the-cloud-management-gateway"></a>Certificaten voor de cloud-management-gateway

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*

Afhankelijk van het scenario dat u gebruikt voor het beheren van clients op het internet met de cloud management gateway (CMG), moet u een of meer digitale certificaten. Zie voor meer informatie over de verschillende scenario's, [plan voor cloud-beheergateway](/sccm/core/clients/manage/cmg/plan-cloud-management-gateway).


## <a name="cmg-server-authentication-certificate"></a>Certificaat voor serververificatie CMG

*Dit certificaat is vereist in alle scenario's.*

U kunt dit certificaat opgeven bij het maken van de CMG in de Configuration Manager-console.

De CMG maakt een HTTPS-service waarmee clients op internet verbinding maken. De server vereist een certificaat voor serververificatie voor het bouwen van het beveiligde kanaal. Koop een certificaat voor dit doel van een openbare provider of van uw openbare-sleutelinfrastructuur (PKI) worden uitgegeven. Zie voor meer informatie [CMG vertrouwd basiscertificaat voor clients](#cmg-trusted-root-certificate-to-clients).

 > [!TIP]
 > Dit certificaat moet een globaal unieke naam voor het identificeren van de service in Azure. Voordat u een certificaat aanvraagt, te controleren dat de naam van de gewenste Azure-domein uniek is. Bijvoorbeeld: *GraniteFalls.CloudApp.Net*. Meld u aan bij de [Microsoft Azure-portal](https://portal.azure.com). Klik op **maken van een resource**, selecteer de **Compute** categorie, klikt u vervolgens op **Cloudservice**. In de **DNS-naam** veld, typt u bijvoorbeeld het gewenste voorvoegsel *GraniteFalls*. De interface weerspiegelt of de domeinnaam beschikbaar is of wordt al gebruikt door een andere service. De service in de portal maken, gebruiken om te controleren van de beschikbaarheid van de naam van dit proces niet. 
  
 > [!NOTE]
 > Vanaf versie 1802, ondersteunt het certificaat voor serververificatie CMG jokertekens. Sommige certificeringsinstanties certificaten met een jokerteken voor de hostnaam. Bijvoorbeeld:  **\*. contoso.com**. Sommige organisaties gebruiken jokertekens-certificaten te vereenvoudigen hun PKI en verlagen de onderhoudskosten.
 <!--491233-->


### <a name="cmg-trusted-root-certificate-to-clients"></a>CMG vertrouwd basiscertificaat voor clients

Het certificaat voor serververificatie CMG moeten worden vertrouwd door clients. Er zijn twee methoden voor het uitvoeren van deze vertrouwensrelatie:
- Een certificaat van een provider van openbare en globaal vertrouwd certificaat gebruiken. Bijvoorbeeld, maar niet beperkt tot, VeriSign of Thawte. Windows-clients zijn vertrouwde basiscertificeringsinstanties (CA's) van deze providers. Met behulp van een serverauthenticatiecertificaat dat is uitgegeven door een van deze providers vertrouwen uw clients automatisch. 
- Een certificaat dat is uitgegeven door een CA voor ondernemingen van uw openbare-sleutelinfrastructuur (PKI) gebruiken. De vertrouwde basiscertificeringsinstanties toevoegen meeste enterprise PKI-implementaties aan Windows-clients. Bijvoorbeeld, met behulp van Active Directory Certificate Services met Groepsbeleid. Als u de server CMG verificatiecertificaat van een CA die uw clients niet automatisch vertrouwt verzendt, moet u het vertrouwde CA-basiscertificaat toevoegen aan clients op internet.
    - U kunt ook de Configuration Manager-certificaatprofielen voor het inrichten van certificaten gebruiken op clients. Zie voor meer informatie [Inleiding tot certificaatprofielen](/sccm/protect/deploy-use/introduction-to-certificate-profiles).

### <a name="server-authentication-certificate-issued-by-public-provider"></a>Certificaat voor serververificatie uitgegeven door een openbare provider

Wanneer u deze methode gebruikt, wordt het certificaat automatisch worden vertrouwd door clients en u hoeft niet te maken van een aangepaste certificaat. Configuration Manager maakt de service in Azure met het domein cloudapp.net. Een openbaar certificaat-provider kan geen uitgeven voor u een certificaat met deze naam. Gebruik het volgende proces voor het maken van een DNS-alias:

1. Maak een canonieke naamrecord (CNAME) in de openbare DNS-server van uw organisatie. Deze record maakt een alias voor de CMG naar een beschrijvende naam die u in het openbare certificaat gebruiken.
Bijvoorbeeld Contoso de namen van hun CMG **GraniteFalls**, die wordt **GraniteFalls.CloudApp.Net** in Azure. In de Contoso openbare DNS-contoso.com naamruimte, de DNS-beheerder maakt een nieuwe CNAME-record voor **GraniteFalls.Contoso.com** voor de werkelijke hostnaam **GraniteFalls.CloudApp.net**.
2. Een certificaat voor serververificatie aanvragen van een openbare provider met behulp van de algemene naam (CN) van de CNAME-alias.
Bijvoorbeeld Contoso maakt gebruik van **GraniteFalls.Contoso.com** voor de algemene naam van het certificaat.
3. Maak de CMG in de Configuration Manager-console met dit certificaat. Op de **instellingen** pagina van de Wizard Cloud maken Management Gateway: 
    - Wanneer u het servercertificaat voor deze cloudservice toevoegen (van **certificaatbestand**), de wizard haalt de hostnaam van de algemene naam als de servicenaam van de van het certificaat. 
    - Worden vervolgens toegevoegd die aan de hostnaam **cloudapp.net**, of **usgovcloudapp.net** voor de cloud Azure US Government als de FQDN-Service de service te maken in Azure.
    - Bijvoorbeeld, wanneer Contoso de CMG maakt, Configuration Manager haalt de hostnaam van de **GraniteFalls** van de algemene naam van het certificaat. Azure maakt de werkelijke service **GraniteFalls.CloudApp.net**.

### <a name="server-authentication-certificate-issued-from-enterprise-pki"></a>Certificaat voor serververificatie van enterprise PKI uitgegeven

Maak een aangepaste SSL-certificaat voor de CMG hetzelfde als voor een clouddistributiepunt. Volg de instructies voor [het servicecertificaat voor cloud-gebaseerde distributiepunten implementeren](/sccm/core/plan-design/network/example-deployment-of-pki-certificates#BKMK_clouddp2008_cm2012) maar anders de volgende dingen doen:

- Bij het aanvragen van het aangepaste Webservercertificaat bieden u een FQDN-naam voor de algemene naam van het certificaat. Gebruik voor het gebruik van de CMG op Azure openbare cloud, een naam die eindigt in **cloudapp.net**, of **usgovcloudapp.net** voor het Azure US Government-cloud.



## <a name="azure-management-certificate"></a>Azure-beheercertificaat

*Dit certificaat is vereist voor klassieke service-implementaties. Het is niet vereist voor implementaties van Azure Resource Manager.*

U kunt dit certificaat in de Azure-portal en opgeven bij het maken van de CMG in de Configuration Manager-console.

U maakt de CMG in Azure door de Configuration Manager serviceaansluitpunt moet eerst worden geverifieerd bij uw Azure-abonnement. Wanneer u een klassieke service-implementatie gebruikt, wordt de Azure-beheercertificaat voor deze verificatie gebruikt. Een Azure-beheerder uploadt u dit certificaat aan uw abonnement. Wanneer u de CMG in de Configuration Manager-console maakt, geeft u dit certificaat.

Zie de volgende artikelen in de Azure-documentatie voor meer informatie en instructies voor het uploaden van een beheercertificaat:

- [Cloudservices en -beheercertificaten](/azure/cloud-services/cloud-services-certs-create#what-are-management-certificates)

- [Een Azure Service Management-certificaat uploaden](/azure/azure-api-management-certs)

> [!IMPORTANT]
> Zorg ervoor dat de abonnements-ID die is gekoppeld aan het beheercertificaat te kopiëren. U deze gebruiken voor het maken van de CMG in de Configuration Manager-console.



## <a name="client-authentication-certificate"></a>Certificaat voor clientverificatie

*Dit certificaat is vereist voor internet-clients met Windows 7, Windows 8.1 en Windows 10-apparaten die niet is toegevoegd aan Azure Active Directory (Azure AD). Het ook vereist op het verbindingspunt CMG. Het is niet vereist voor Windows 10-clients die lid zijn van Azure AD.*

Dit certificaat in de clients gebruiken voor verificatie met de CMG. Windows 10-apparaten die hybride of cloud domein zijn hebben dit certificaat geen nodig omdat ze Azure AD gebruiken om te verifiëren.

Dit certificaat buiten de context van Configuration Manager inrichten. Gebruik bijvoorbeeld Active Directory Certificate Services en Groepsbeleid voor verificatie van clientcertificaten. Zie voor meer informatie [het clientcertificaat voor Windows-computers implementeren](/sccm/core/plan-design/network/example-deployment-of-pki-certificates#BKMK_client2008_cm2012).


### <a name="client-trusted-root-certificate-to-cmg"></a>Client vertrouwd basiscertificaat voor CMG

*Dit certificaat is vereist bij gebruik van certificaten voor clientverificatie. Wanneer alle clients Azure AD voor verificatie, is dit certificaat niet vereist.* 

U kunt dit certificaat opgeven bij het maken van de CMG in de Configuration Manager-console.

De CMG moet de certificaten voor clientverificatie vertrouwen. Om te realiseren deze vertrouwensrelatie, bieden de certificaatketen van vertrouwde basiscertificeringsinstanties. U kunt twee vertrouwde basis-CA's en vier tussenliggende (onderliggende) CA's opgeven. 


#### <a name="export-the-client-certificates-trusted-root"></a>Vertrouwde basiscertificeringsinstanties van het clientcertificaat exporteren

Na het uitgeven van een certificaat voor clientverificatie op een computer kunt dit proces op die computer exporteren van de vertrouwde basis.

1.  Het menu Start openen. Typ 'uitvoeren' om het venster uitvoeren te openen. Open **mmc**. 

2.  Kies in het menu bestand **module toevoegen/verwijderen...** .

3.  Selecteer in het dialoogvenster Add of Remove-modules **certificaten**, klikt u vervolgens op **toevoegen**. 
    a. Selecteer in het dialoogvenster module Certificaten **computeraccount**, klikt u vervolgens op **volgende**. 
    b. Selecteer in het dialoogvenster Computer selecteren **lokale computer**, klikt u vervolgens op **voltooien**. 
    c. Klik in het dialoogvenster Add of Remove-modules op **OK**.

4.  Vouw **certificaten**, vouw **persoonlijke**, en selecteer **certificaten**.

5.  Selecteer een certificaat waarvan beoogd doeleinde is **clientverificatie**. 
    a. Selecteer in het menu actie **Open**. 
    b. Overschakelen naar de **certificeringspad** tabblad c. Selecteer het volgende certificaat keten van, en klikt u op **certificaat weergeven**.

6.  Deze nieuwe certificaat in het dialoogvenster overschakelen naar de **Details** tabblad. Klik op **kopiëren naar bestand...** .

7.  Voltooi de Wizard Certificaat exporteren met de indeling van het certificaat standaard **DER encoded binary X.509 (. CER)**. Controleer de naam en locatie van het geëxporteerde certificaat.

8. Exporteer alle certificaten in het certificeringspad van het oorspronkelijke certificaat voor clientverificatie. Noteer welke geëxporteerde certificaten tussenliggende CA's zijn en welke vertrouwde basis-CA's.



## <a name="enable-management-point-for-https"></a>Beheerpunt inschakelen voor HTTPS

*Certificaatvereisten*
- Dit certificaat wordt in versies 1706 of 1710, wanneer het beheren van traditionele clients met on-premises identiteiten met behulp van een certificaat voor clientverificatie aanbevolen maar niet vereist.
- In versie 1710, wanneer Windows 10-clients beheren dat is gekoppeld aan Azure AD, dit certificaat is vereist voor beheerpunten. 
- Vanaf versie 1802 biedt is dit certificaat vereist in alle scenario's. Alleen de beheerpunten die u voor CMG inschakelt moet HTTPS zijn. Deze wijziging in gedrag biedt betere ondersteuning voor Azure AD-verificatie op basis van tokens. 

Dit certificaat buiten de context van Configuration Manager inrichten. Bijvoorbeeld Active Directory Certificate Services en Groepsbeleid gebruiken om uit te geven van een Webservercertificaat. Zie voor meer informatie [PKI-certificaatvereisten](/sccm/core/plan-design/network/pki-certificate-requirements) en [implementeren van het Webservercertificaat voor sitesystemen die IIS uitvoeren](/sccm/core/plan-design/network/example-deployment-of-pki-certificates#BKMK_webserver2008_cm2012).



## <a name="next-steps"></a>Volgende stappen

- [Een cloudbeheergateway instellen](/sccm/core/clients/manage/cmg/setup-cloud-management-gateway)
- [Veelgestelde vragen over de cloud-management-gateway](/sccm/core/clients/manage/cmg/cloud-management-gateway-faq)
- [Beveiliging en privacy voor cloudbeheergateway](/sccm/core/clients/manage/cmg/security-and-privacy-for-cloud-management-gateway)
