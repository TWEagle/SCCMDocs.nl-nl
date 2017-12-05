---
title: De rol systeemopties site
titleSuffix: Configuration Manager
description: Raadpleeg dit artikel voor meer informatie over Configuration Manager-sitesysteemrollen die niet noodzakelijkerwijs spreken voor zich.
ms.custom: na
ms.date: 2/8/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 0e9f0fbd-e442-4509-a021-bfdedf2d04dd
caps.latest.revision: "5"
author: mestew
ms.author: mstewart
manager: angrobe
ms.openlocfilehash: 83fbde5fd15b1781822bcc743e2c13611ad88e0d
ms.sourcegitcommit: daa080cf220835f157a23e8c8e2bd2781b869bb7
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/04/2017
---
# <a name="configuration-options-for-site-system-roles-for-system-center-configuration-manager"></a>Configuratie-opties voor sitesysteemrollen voor System Center Configuration Manager

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*

De meeste configuratieopties voor System Center Configuration Manager-sitesysteemrollen behoeven geen uitleg of worden beschreven in de wizard of dialoogvensters over gegeven wanneer u ze configureren. De volgende secties worden de sitesysteemrollen waarvan u de instellingen kunnen bijkomende informatie vereisen.  

##  <a name="BKMK_ApplicationCatalog_Website"></a>Application Catalog-websitepunt  
 Zie voor meer informatie over het instellen van de Application Catalog-websitepunt voor de Application Catalog [plannen en configureren van Toepassingsbeheer in System Center Configuration Manager](../../../../apps/plan-design/plan-for-and-configure-application-management.md).  

 **Clientverbindingen**  

 Selecteer **HTTPS** om te gebruiken de meer beveiligde instelling en om te controleren of clients via het Internet verbinden. Deze optie vereist een PKI-certificaat op de server voor serververificatie naar clients en voor het versleutelen van gegevens via Secure Socket Layer (SSL). Zie voor meer informatie over de certificaatvereisten [PKI-certificaatvereisten voor System Center Configuration Manager](../../../../core/plan-design/network/pki-certificate-requirements.md).  

 Zie voor een Voorbeeldimplementatie van het servercertificaat en informatie over het configureren van in Internet Information Services (IIS), de *het Webservercertificaat voor Sitesystemen die IIS uitvoeren implementeren* in sectie [voorbeeld van stapsgewijze implementatie van de PKI-certificaten voor System Center Configuration Manager: Windows Server 2008-certificeringsinstantie](/sccm/core/plan-design/network/example-deployment-of-pki-certificates).  

 **Application Catalog-website toevoegen aan zone met vertrouwde sites**  

 Dit bericht geeft de waarde in de standaard clientinstellingen of de **Application Catalog-website toevoegen aan de zone Vertrouwde sites in Internet Explorer** client-instelling is momenteel ingesteld op **True** of **False**. Als u aangepaste clientinstellingen gebruikt deze instelling wilt configureren, moet u deze waarde zelf controleren.  

 Als dit sitesysteem is ingesteld voor een volledig gekwalificeerde domeinnaam (FQDN) en de website niet in de zone Vertrouwde sites in Internet Explorer is, worden gebruikers om referenties gevraagd wanneer ze verbinding met de Application Catalog maken.  

 **De naam van organisatie**  

 Voer de naam die gebruikers zien in de Application Catalog. Deze huismerkgegevens helpen gebruikers deze website als een vertrouwde bron te identificeren.  

##  <a name="BKMK_ApplicationCatalog_WebService"></a>Application Catalog-webservicepunt  
 Zie voor meer informatie over het instellen van het Application Catalog-webservicepunt voor de Application Catalog [plannen en configureren van Toepassingsbeheer in System Center Configuration Manager](../../../../apps/plan-design/plan-for-and-configure-application-management.md).  

 **HTTPS**  

 Selecteer **HTTPS** om te verifiëren van de Application Catalog-website verwijst naar dit Application Catalog-webservicepunt.  Deze optie vereist een PKI-certificaat op servers met de Application Catalog-websitepunt voor server-verificatie en versleuteling van gegevens via SSL. Zie voor meer informatie over de certificaatvereisten [PKI-certificaatvereisten voor System Center Configuration Manager](../../../../core/plan-design/network/pki-certificate-requirements.md).  

 Zie voor een Voorbeeldimplementatie van het servercertificaat en informatie over het configureren van IIS, de *het Webservercertificaat voor Sitesystemen die IIS uitvoeren implementeren* in sectie [voorbeeld van stapsgewijze implementatie van de PKI-certificaten voor System Center Configuration Manager: Windows Server 2008-certificeringsinstantie](/sccm/core/plan-design/network/example-deployment-of-pki-certificates).  

##  <a name="BKMK_CertificateRegistrationPoint"></a>Certificaatregistratiepunt  
 Zie voor meer informatie over het instellen van het certificaatregistratiepunt [Inleiding tot certificaatprofielen](/sccm/protect/deploy-use/introduction-to-certificate-profiles).  

##  <a name="BKMK_Distribution_Point"></a>Distributiepunt  
 Zie voor meer informatie over het instellen van het distributiepunt voor inhoudimplementatie [inhoud en infrastructuur voor System Center Configuration Manager beheren](../../../../core/servers/deploy/configure/manage-content-and-content-infrastructure.md).  

 Zie voor meer informatie over het instellen van het distributiepunt voor PXE-implementaties, [PXE gebruiken om Windows te implementeren via het netwerk met System Center Configuration Manager](../../../../osd/deploy-use/use-pxe-to-deploy-windows-over-the-network.md).  

 Zie voor informatie over het instellen van het distributiepunt voor multicast-implementaties, [multicast gebruiken om Windows te implementeren via het netwerk met System Center Configuration Manager](../../../../osd/deploy-use/use-multicast-to-deploy-windows-over-the-network.md).  

 **Installeer en Configureer IIS indien vereist door Configuration Manager**  
 Selecteer deze optie om Configuration Manager installeren en instellen van IIS op het sitesysteem als deze nog niet is geïnstalleerd. IIS moet worden geïnstalleerd op alle distributiepunten en moet u deze instelling om door te gaan in de wizard.  

 **Installatieaccount sitesysteem**  
 Voor distributiepunten die zijn geïnstalleerd op een siteserver bevindt, wordt het computeraccount van de siteserver ondersteund voor gebruik als de Account voor de installatie van de Site.  

 **Een zelfondertekend certificaat maken of importeren van een PKI-certificaat**  
 Dit certificaat heeft twee doeleinden:  

1.  Hiermee verifieert het distributiepunt naar een beheerpunt voordat het distributiepunt statusberichten verzendt.  

2.  Wanneer **PXE-ondersteuning inschakelen voor clients** is geselecteerd, wordt het certificaat verzonden naar computers die een PXE-opstartbewerking uitvoeren, zodat ze verbinding met een beheerpunt tijdens de implementatie van het besturingssysteem maken kunnen.  

Wanneer uw beheerpunten in de site zijn ingesteld voor HTTP, maakt u een zelfondertekend certificaat. Wanneer uw beheerpunten zijn ingesteld voor HTTPS, moet u een PKI-clientcertificaat importeren.  

Blader naar een bestand Public Key Cryptography Standard #12 (PKCS #12) met een PKI-certificaat met de volgende vereisten voor Configuration Manager voor het importeren van het certificaat:  

-   Bedoelde gebruik moet clientverificatie omvatten.  

-   De persoonlijke sleutel moet worden ingesteld om te worden geëxporteerd.  

Er zijn geen specifieke vereisten voor de naam certificaatonderwerp of SAN Subject Alternative Name () en u kunt hetzelfde certificaat gebruiken voor meerdere distributiepunten.  

Zie voor meer informatie over de certificaatvereisten [PKI-certificaatvereisten voor System Center Configuration Manager](../../../../core/plan-design/network/pki-certificate-requirements.md). Zie voor een Voorbeeldimplementatie van dit certificaat, de *het clientcertificaat voor distributiepunten implementeren* in sectie [voorbeeld van stapsgewijze implementatie van de PKI-certificaten voor System Center Configuration Manager: Windows Server 2008-certificeringsinstantie](/sccm/core/plan-design/network/example-deployment-of-pki-certificates).  

**Dit distributiepunt inschakelen voor voorbereide inhoud**  
Schakel dit selectievakje in om het distributiepunt inschakelen voor voorbereide inhoud. Wanneer dit selectievakje is ingeschakeld, kunt u distributiegedrag instellen wanneer u inhoud distribueert. U kunt kiezen of u inhoud op het distributiepunt altijd voor te bereiden, initiële inhoud voor het pakket voor te bereiden, maar het normale inhouddistributieproces voor updates voor inhoud gebruiken, of altijd het normale inhouddistributieproces te voor de inhoud van het pakket gebruiken.  

**Grensgroepen**  
 U kunt grensgroepen naar een distributiepunt koppelen. Tijdens inhoudsimplementatie moeten clients zich in een grensgroep die is gekoppeld aan het distributiepunt te gebruiken als bronlocatie voor inhoud.
 - **Voorafgaand aan versie 1610**, kunt u controleren de **terugvalbronlocatie voor inhoud toestaan** selectievakje in als clients buiten deze grensgroepen terug te vallen en het distributiepunt gebruiken als bronlocatie voor inhoud, wanneer er geen andere distributiepunten beschikbaar zijn.
 - **Vanaf versie 1610**, u kunt niet meer configureren **terugvalbronlocatie voor inhoud toestaan**.  In plaats daarvan u relaties tussen grensgroepen die wanneer een client kunt beginnen controleren met zoeken aanvullende grensgroepen voor geldige inhoudsbron locaties hebt ingesteld.

##  <a name="BKMK_Enrollment_Point"></a>Inschrijvingspunt  
Inschrijvingspunten worden gebruikt voor het installeren van Mac-computers en apparaten die u met on-premises-beheer voor mobiele apparaten beheert inschrijven. Zie voor meer informatie de volgende onderwerpen:  

-   [Clients implementeren op Mac-computers in System Center Configuration Manager](../../../../core/clients/deploy/deploy-clients-to-macs.md)  

-   [Hoe gebruikers apparaten inschrijven met On-premises Mobile Device Management in System Center Configuration Manager](../../../../mdm/deploy-use/user-enroll-devices-on-premises-mdm.md)  

**Toegestane verbindingen**  
 De HTTPS-instelling wordt automatisch geselecteerd en vereist een PKI-certificaat op de server voor serververificatie naar het proxypunt voor inschrijving, de server te verifiëren bij de out-of-band-servicepunt en de codering van gegevens via SSL. Zie voor meer informatie over de certificaatvereisten [PKI-certificaatvereisten voor System Center Configuration Manager](../../../../core/plan-design/network/pki-certificate-requirements.md).  

 Zie voor een Voorbeeldimplementatie van het servercertificaat en informatie over het configureren van IIS, de *het Webservercertificaat voor Sitesystemen die IIS uitvoeren implementeren* in sectie [voorbeeld van stapsgewijze implementatie van de PKI-certificaten voor System Center Configuration Manager: Windows Server 2008-certificeringsinstantie](/sccm/core/plan-design/network/example-deployment-of-pki-certificates).  

##  <a name="BKMK_Enrollment_Proxy_Point"></a>Proxypunt voor inschrijving  
Zie voor meer informatie over het instellen van een proxypunt voor inschrijving voor mobiele apparaten, [hoe gebruikers apparaten inschrijven met On-premises Mobile Device Management in System Center Configuration Manager](../../../../mdm/deploy-use/user-enroll-devices-on-premises-mdm.md).  

**Clientverbindingen**  
 De HTTPS-instelling wordt automatisch geselecteerd en vereist een PKI-certificaat op de server voor serververificatie naar mobiele apparaten en Mac-computers die zijn ingeschreven door Configuration Manager en voor het versleutelen van gegevens via Secure Sockets Layer (SSL). Zie voor meer informatie over de certificaatvereisten [PKI-certificaatvereisten voor System Center Configuration Manager](../../../../core/plan-design/network/pki-certificate-requirements.md).  

 Zie voor een Voorbeeldimplementatie van het servercertificaat en informatie over het configureren van IIS, de *het Webservercertificaat voor Sitesystemen die IIS uitvoeren implementeren* in sectie [voorbeeld van stapsgewijze implementatie van de PKI-certificaten voor System Center Configuration Manager: Windows Server 2008-certificeringsinstantie](/sccm/core/plan-design/network/example-deployment-of-pki-certificates).  

##  <a name="BKMK_Fallback_Status_Point"></a>Terugvalstatuspunt  
**Aantal statusberichten** en **vertragingsinterval (in seconden)**  
Hoewel de standaardinstellingen voor deze opties (10.000 statusberichten en 3600 seconden voor het vertragingsinterval) voldoende zijn voor de meeste omstandigheden, moet u wellicht wijzigen wanneer beide volgende voorwaarden waar zijn:  

-   Het terugvalstatuspunt accepteert alleen verbindingen met het intranet.  

-   U gebruikt het terugvalstatuspunt tijdens een clientimplementatierollout voor veel computers.  

In dit scenario kan een continue stroom van statusberichten een achterstand van statusberichten die ervoor zorgt hoge centrale verwerkingseenheid (CPU) gebruik op de siteserver voor een langere periode dat maken. Bovendien kan er geen actuele informatie over de clientimplementatie in de Configuration Manager-console en in de clientimplementatierapporten.  

Deze instellingen voor terugvalstatuspunt zijn ontworpen om in te stellen voor statusberichten die zijn gegenereerd tijdens de clientimplementatie van de. De instellingen zijn niet ontworpen om te worden ingesteld voor problemen met clientcommunicatie, zoals wanneer clients op het Internet geen verbinding met de Internet-gebaseerd beheerpunt bevindt maken. Omdat het terugvalstatuspunt kan niet van toepassing zijn deze instellingen alleen op de statusberichten die zijn gegenereerd tijdens de clientimplementatie van de, configureer deze instellingen als het terugvalstatuspunt verbindingen van Internet aanvaardt.  

Elke computer die met succes de System Center 2012 Configuration Manager-client installeert verzendt de volgende vier statusberichten naar het terugvalstatuspunt:  

-   Clientimplementatie is gestart  

-   Clientimplementatie is voltooid  

-   Clienttoewijzing is gestart  

-   Clienttoewijzing is voltooid  

Computers die niet kan worden geïnstalleerd of dat de Configuration Manager-client toewijzen, verzenden bijkomende statusberichten.  

Bijvoorbeeld, als u de Configuration Manager-client naar 20.000 gebruikers implementeert, kan de implementatie 80.000 statusberichten verzenden naar het terugvalstatuspunt. Omdat de standaard beperkingsconfiguratie kunt 10.000 statusberichten worden verzonden naar het terugvalstatuspunt elke 3600 seconden (1 uur), kunnen de statusberichten worden achterstallige op het terugvalstatuspunt. U moet ook overwegen de beschikbare netwerkbandbreedte tussen het terugvalstatuspunt en de siteserver en de processorsnelheid van de siteserver veel statusberichten te verwerken.  

U kunt een verhoging van het aantal statusberichten en een afname in de vertragingsinterval ter voorkoming van deze problemen.  

Reset de beperkingswaarden voor het terugvalstatuspunt als een van de volgende voorwaarden is voldaan:  

-   U berekenen dat de huidige beperkingswaarden hoger dan nodig om te verwerken statusberichten van het terugvalstatuspunt zijn.  

-   U vindt dat de huidige beperkingsinstellingen een hoog CPU-gebruik op de siteserver.  

Wijzig de instellingen voor de instellingen voor terugvalstatuspunt versnelling niet tenzij u de gevolgen. Bijvoorbeeld, als u de beperkingsinstellingen hoog verhoogt, verhogen het CPU-gebruik op de siteserver, dit vertraagt alle sitebewerkingen.  
