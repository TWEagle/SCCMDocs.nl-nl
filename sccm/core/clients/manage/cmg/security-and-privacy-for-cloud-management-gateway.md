---
title: CMG beveiliging en privacy
description: Meer informatie over de richtlijnen en aanbevelingen voor beveiliging en privacy met de cloud management gateway.
author: aczechowski
ms.author: aaroncz
manager: dougeby
ms.date: 03/22/2018
ms.topic: article
ms.prod: configuration-manager
ms.technology:
- configmgr-other
ms.assetid: 7304730b-b517-4c76-aadd-4cbd157dc971
ms.openlocfilehash: a850ea32fc06718c66d117702fb0a4bf1113a74c
ms.sourcegitcommit: 11bf4ed40ed0cbb10500cc58bbecbd23c92bfe20
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 03/23/2018
---
# <a name="security-and-privacy-for-the-cloud-management-gateway"></a>Beveiliging en privacy voor de cloud-management-gateway

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*

Dit artikel bevat beveiligings- en privacy-informatie voor het hulpprogramma voor het beheer van de Configuration Manager-cloudgateway (CMG). Zie voor meer informatie [plannen voor cloud-beheergateway](/sccm/core/clients/manage/cmg/plan-cloud-management-gateway).

## <a name="cmg-security-details"></a>Informatie over de beveiliging CMG
- De CMG accepteert en beheert verbindingen van de verbindingspunten CMG. Wederzijdse SSL-verificatie met behulp van certificaten en verbinding id's wordt gebruikt.
- De CMG accepteert en stuurt de aanvragen van clients met behulp van de volgende methoden:
    - Vooraf verifieert verbindingen met wederzijdse SSL op basis van een PKI-certificaat voor clientverificatie of Azure AD. 
      - IIS op CMG VM-exemplaren wordt gecontroleerd of het certificaatpad op basis van de certificaten van vertrouwde basiscertificeringsinstanties geüpload naar de CMG.
      - IIS op de VM-instantie controleert ook of intrekken van certificaten van client, indien ingeschakeld. Zie voor meer informatie [de certificaatintrekkingslijst](#bkmk_crl).
    - Lijst met vertrouwde certificaten controleert de hoofdmap van het certificaat voor clientverificatie. Ook voert dezelfde validatie uit als het beheerpunt voor de client. Zie voor meer informatie [vermeldingen in de lijst van vertrouwde certificaten van de site bekijken](#bkmk_ctl).
    - Valideert en clientaanvragen (URL's) om te controleren als de aanvraag kan worden verwerkt door een verbindingspunt CMG filtert.  
    - Controleert de lengte van de inhoud voor elk eindpunt dat publiceren.
    - Maakt gebruik van round robin gedrag te verdelen CMG verbindingspunten in dezelfde site.
- Het verbindingspunt CMG gebruikt de volgende methoden:
    - Consistente HTTPS/TCP-verbindingen met alle VM-instanties van de CMG is gebaseerd. Het wordt gecontroleerd en deze verbindingen onderhoudt elke minuut.
    - Maakt gebruik van SSL voor wederzijdse verificatie met de CMG met behulp van certificaten.
    - Verzendt aanvragen van clients op basis van de URL-toewijzingen.
    - Verbindingsstatus van rapporten met health-servicestatus weergeven in de console.
    - Rapporten verkeer per eindpunt om de vijf minuten.

### <a name="configuration-manager-client-facing-roles"></a>Clientgerichte rollen van Configuration Manager
Het management point- and -software-updatepunt host eindpunten in IIS met serviceclientaanvragen. De CMG beschikbaar niet alle interne eindpunten. Elk eindpunt dat is gepubliceerd naar de CMG heeft een URL-toewijzing.
  - De externe URL is de client gebruikt om te communiceren met de CMG.
  - De interne URL wordt gebruikt voor het doorsturen van aanvragen naar de interne server CMG verbindingspunt.

#### <a name="url-mapping-example"></a>Voorbeeld van de URL-toewijzing
Wanneer u verkeer op een beheerpunt CMG inschakelt, maakt Configuration Manager een interne set met URL-toewijzingen voor elke beheerserver punt. Bijvoorbeeld: ccm_system, ccm_incoming, en sms_mp. De externe URL voor het eindpunt van de punt ccm_system management uitzien als volgt:  
`https://<CMG service name>/CCM_Proxy_MutualAuth/<MP Role ID>/CCM_System`  
De URL is uniek voor elk beheerpunt. Configuration Manager-client worden vervolgens de CMG ingeschakeld naam van het beheerpunt in de internet MP-lijst geplaatst. Deze naam ziet eruit als:  
`<CMG service name>/CCM_Proxy_MutualAuth/<MP Role ID>`  
De site worden automatisch alle gepubliceerde externe URL's naar de CMG geüpload. Dit gedrag kan de CMG URL-filtering doen. Alle toewijzingen van de URL repliceren naar het verbindingspunt CMG. Deze stuurt de communicatie naar interne servers op basis van de externe URL van de clientaanvraag.



## <a name="security-guidance-for-cmg"></a>Richtlijnen voor beveiliging voor CMG


<a name="bkmk_crl"></a>

### <a name="publish-the-certificate-revocation-list"></a>De certificaatintrekkingslijst uitgeven

Uw PKI-certificaatintrekkingslijst (CRL) voor clients op internet om toegang te publiceren. De service zodanig configureren dat bij het implementeren van een PKI met CMG **intrekking van clientcertificaat controleren** op het tabblad instellingen. Deze instelling configureert u de service voor het gebruik van een uitgegeven certificaatintrekkingslijst (CRL). Zie voor meer informatie [plannen voor PKI-certificaatintrekking](/sccm/core/plan-design/security/plan-for-security#BKMK_PlanningForCRLs).



<a name="bkmk_ctl"></a>

### <a name="review-entries-in-the-sites-certificate-trust-list"></a>Controleer de vermeldingen in de lijst van vertrouwde certificaten van de site
<!--503739-->
Elke Configuration Manager-site bevat een lijst met vertrouwde basiscertificeringsinstanties op de certificaatvertrouwenslijst (CTL). Weergeven en wijzigen van de lijst door te gaan naar de werkruimte beheer, vouw het knooppunt siteconfiguratie en selecteer de Sites. Selecteer een site en klikt u op eigenschappen in het lint. Overschakelen naar het tabblad communicatie clientcomputer en klik vervolgens op **ingesteld** onder de vertrouwde basiscertificeringsinstanties.
 
Gebruik een meer beperkend CTL voor een site met een CMG met behulp van PKI-clientverificatie. Clients met certificaten voor clientverificatie verleend door een vertrouwde basiscertificeringsinstantie die al op het beheerpunt bestaat worden anders wordt automatisch geaccepteerd voor clientregistratie bij de.

Deze subset biedt beheerders meer controle over beveiliging. De CTL Hiermee beperkt u de server alleen om clientcertificaten te accepteren die zijn uitgegeven door de certificeringsinstanties in de CTL. Windows wordt bijvoorbeeld geleverd met een aantal bekende van derden certificeringsinstanties (CA) certificaten, zoals VeriSign en Thawte. Standaard wordt met de computer met IIS-vertrouwensrelaties die zijn gekoppeld aan deze bekende certificeringsinstanties certificaten. Elke computer met een clientcertificaat dat is uitgegeven door deze CA's, zonder u IIS configureert met een CTL, geaccepteerd als een geldige Configuration Manager-client. Als u IIS met een CTL dat deze CA's hebt opgenomen configureert, worden clientverbindingen geweigerd als het certificaat is gekoppeld aan deze CA's. 


<!--486209-->


<!-- ## Privacy information for CMG -->


## <a name="next-steps"></a>Volgende stappen

- [Een cloudbeheergateway plannen](/sccm/core/clients/manage/cmg/plan-cloud-management-gateway)
- [Een cloudbeheergateway instellen](/sccm/core/clients/manage/cmg/setup-cloud-management-gateway)
- [Veelgestelde vragen over de cloud-management-gateway](/sccm/core/clients/manage/cmg/cloud-management-gateway-faq)
- [Certificaten voor cloud-beheergateway](/sccm/core/clients/manage/cmg/certificates-for-cloud-management-gateway)
