---
title: Site-rol systeemopties | Microsoft-documenten
description: Raadpleeg dit artikel voor meer informatie over Configuration Manager-sitesysteemrollen die niet noodzakelijkerwijs geen uitleg.
ms.custom: na
ms.date: 2/8/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 0e9f0fbd-e442-4509-a021-bfdedf2d04dd
caps.latest.revision: 5
author: Brenduns
ms.author: brenduns
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: fff93794afdfa9f890b1f06d6c330d8cffc5796c
ms.openlocfilehash: b4db5d86cc0ed020ed176feb2e8f1f9dc51a2280
ms.contentlocale: nl-nl
ms.lasthandoff: 05/17/2017

---
# <a name="configuration-options-for-site-system-roles-for-system-center-configuration-manager"></a>Configuratie-opties voor sitesysteemrollen voor System Center Configuration Manager

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*

De meeste configuratieopties voor System Center Configuration Manager-sitesysteemrollen behoeven geen uitleg of worden beschreven in de wizard of dialoogvensters over gegeven wanneer u ze configureert. De volgende secties wordt uitgelegd sitesysteemrollen waarvan u de instellingen kunnen bijkomende informatie vereisen.  

##  <a name="BKMK_ApplicationCatalog_Website"></a>Application Catalog-websitepunt  
 Zie voor meer informatie over het instellen van de Application Catalog-websitepunt voor de Application Catalog [plannen en configureren van Toepassingsbeheer in System Center Configuration Manager](../../../../apps/plan-design/plan-for-and-configure-application-management.md).  

 **Clientverbindingen**  

 Selecteer **HTTPS** gebruik van de meer beveiligde instelling en om te controleren of clients via het Internet verbinden. Deze optie vereist een PKI-certificaat op de server voor serververificatie naar clients en voor het versleutelen van gegevens via Secure Socket Layer (SSL). Zie voor meer informatie over de certificaatvereisten [PKI-certificaatvereisten voor System Center Configuration Manager](../../../../core/plan-design/network/pki-certificate-requirements.md).  

 Zie voor een Voorbeeldimplementatie van het servercertificaat en informatie over hoe dit moet worden geconfigureerd in Internet Information Services (IIS), de *het webservercertificaat implementeren voor Sitesystemen die IIS uitvoeren* in sectie [voorbeeld van stapsgewijze implementatie van de PKI-certificaten voor System Center Configuration Manager: Windows Server 2008-certificeringsinstantie](/sccm/core/plan-design/network/example-deployment-of-pki-certificates).  

 **Application Catalog-website toevoegen aan zone met vertrouwde sites**  

 Dit bericht geeft de waarde in de standaard clientinstellingen of de **Application Catalog-website toevoegen aan de zone Vertrouwde sites in Internet Explorer** client-instelling is momenteel ingesteld op **waar** of **False**. Als u aangepaste clientinstellingen gebruikt deze instelling wilt configureren, moet u deze waarde zelf controleren.  

 Als dit sitesysteem is ingesteld voor een volledig gekwalificeerde domeinnaam (FQDN) en de website niet in de zone met vertrouwde sites in Internet Explorer, worden gebruikers gevraagd naar referenties wanneer ze met de Application Catalog verbinden.  

 **Organisatienaam**  

 Voer de naam die wordt weergegeven in de Application Catalog. Deze huismerkgegevens helpen gebruikers deze toepassing als een vertrouwde bron te identificeren.  

##  <a name="BKMK_ApplicationCatalog_WebService"></a>Application Catalog-webservicepunt  
 Zie voor meer informatie over het instellen van het Application Catalog-webservicepunt voor de Application Catalog [plannen en configureren van Toepassingsbeheer in System Center Configuration Manager](../../../../apps/plan-design/plan-for-and-configure-application-management.md).  

 **HTTPS**  

 Selecteer **HTTPS** voor het verifiëren van de Application Catalog-website verwijst naar dit Application Catalog-webservicepunt.  Deze optie vereist een PKI-certificaat op servers waarop de Application Catalog-websitepunten voor serververificatie en voor versleuteling van gegevens over SSL worden uitgevoerd. Zie voor meer informatie over de certificaatvereisten [PKI-certificaatvereisten voor System Center Configuration Manager](../../../../core/plan-design/network/pki-certificate-requirements.md).  

 Zie voor een Voorbeeldimplementatie van het servercertificaat en informatie over het configureren in IIS, de *het webservercertificaat implementeren voor Sitesystemen die IIS uitvoeren* in sectie [voorbeeld van stapsgewijze implementatie van de PKI-certificaten voor System Center Configuration Manager: Windows Server 2008-certificeringsinstantie](/sccm/core/plan-design/network/example-deployment-of-pki-certificates).  

##  <a name="BKMK_CertificateRegistrationPoint"></a>Certificaatregistratiepunt  
 Zie voor meer informatie over het instellen van het certificaatregistratiepunt, [Inleiding tot certificaatprofielen](/sccm/protect/deploy-use/introduction-to-certificate-profiles).  

##  <a name="BKMK_Distribution_Point"></a>Distributiepunt  
 Zie voor meer informatie over het instellen van het distributiepunt voor inhoudimplementatie, [inhoud en -infrastructuur voor System Center Configuration Manager beheert](../../../../core/servers/deploy/configure/manage-content-and-content-infrastructure.md).  

 Zie voor meer informatie over het instellen van het distributiepunt voor PXE-implementaties, [gebruik PXE om Windows te implementeren via het netwerk met System Center Configuration Manager](../../../../osd/deploy-use/use-pxe-to-deploy-windows-over-the-network.md).  

 Zie voor informatie over het instellen van het distributiepunt voor multicast-implementaties, [gebruik multicast om Windows te implementeren via het netwerk met System Center Configuration Manager](../../../../osd/deploy-use/use-multicast-to-deploy-windows-over-the-network.md).  

 **Installeer en Configureer IIS indien vereist door Configuration Manager**  
 Selecteer deze optie om Configuration Manager installeren en instellen van IIS op het sitesysteem als dit nog niet is geïnstalleerd. IIS moet worden geïnstalleerd op alle distributiepunten en moet u deze instelling om door te gaan in de wizard.  

 **Installatieaccount sitesysteem**  
 Voor distributiepunten die op een siteserver zijn geïnstalleerd, wordt alleen het computeraccount van de siteserver ondersteund voor gebruik als het Installatieaccount.  

 **Maak een zelfondertekend certificaat of importeer een PKI-certificaat**  
 Dit certificaat heeft twee doeleinden:  

1.  Het verifieert het distributiepunt naar een beheerpunt voordat het distributiepunt statusberichten verzendt.  

2.  Wanneer **PXE-ondersteuning inschakelen voor clients** is geselecteerd, wordt het certificaat verzonden naar computers die een PXE-opstartbewerking doen zodat ze verbinding met een beheerpunt tijdens de implementatie van het besturingssysteem maken kunnen.  

Wanneer uw beheerpunten in de site zijn ingesteld voor HTTP, maakt u een zelfondertekend certificaat. Importeer een PKI-clientcertificaat wanneer uw beheerpunten zijn ingesteld voor HTTPS.  

Blader naar een Public Key Cryptography Standard #12 (PKCS #12)-bestand dat een PKI-certificaat met de volgende vereisten voor Configuration Manager heeft voor het importeren van het certificaat:  

-   Het bedoelde gebruik moet clientverificatie omvatten.  

-   De persoonlijke sleutel moet worden ingesteld om te worden geëxporteerd.  

Er zijn geen specifieke vereisten voor de naam certificaatonderwerp of SAN Subject Alternative Name (); u kunt hetzelfde certificaat gebruiken voor meerdere distributiepunten.  

Zie voor meer informatie over de certificaatvereisten [PKI-certificaatvereisten voor System Center Configuration Manager](../../../../core/plan-design/network/pki-certificate-requirements.md). Zie voor een Voorbeeldimplementatie van dit certificaat, de *het clientcertificaat voor distributiepunten implementeren* in sectie [voorbeeld van stapsgewijze implementatie van de PKI-certificaten voor System Center Configuration Manager: Windows Server 2008-certificeringsinstantie](/sccm/core/plan-design/network/example-deployment-of-pki-certificates).  

**Dit distributiepunt inschakelen voor voorbereide inhoud**  
Schakel dit selectievakje in om het distributiepunt inschakelen voor voorbereide inhoud. Als dit selectievakje is ingeschakeld, kunt u distributiegedrag instellen wanneer u inhoud distribueert. U kunt kiezen of u altijd inhoud op het distributiepunt voor te bereiden, initiële inhoud voor het pakket voor te bereiden, maar het normale inhouddistributieproces voor updates voor inhoud gebruiken, of altijd het normale inhouddistributieproces te voor de inhoud van het pakket gebruiken.  

**Grensgroepen**  
 U kunt grensgroepen aan een distributiepunt koppelen. Tijdens inhoudsimplementatie moeten clients zich in een grensgroep die is gekoppeld aan het distributiepunt gebruiken als bronlocatie voor inhoud.
 - **Voor versie 1610**, kunt u controleren de **terugvalbronlocatie voor inhoud toestaan** selectievakje wilt toestaan dat clients buiten deze grensgroepen terug te vallen en gebruik het distributiepunt als bronlocatie voor inhoud wanneer er geen andere distributiepunten beschikbaar zijn.
 - **Vanaf versie 1610**, niet meer kunt u **terugvalbronlocatie voor inhoud toestaan**.  In plaats daarvan kunt instellen u relaties tussen grensgroepen te controleren wanneer een client om te zoeken naar aanvullende grensgroepen voor geldige inhoudsbron locaties kan beginnen.

##  <a name="BKMK_Enrollment_Point"></a>Inschrijvingspunt  
Inschrijvingspunten worden gebruikt voor het installeren van Mac-computers en apparaten die u wilt met beheer van lokale mobiele apparaten beheren te schrijven. Zie voor meer informatie de volgende onderwerpen:  

-   [Clients implementeren in Macs in System Center Configuration Manager](../../../../core/clients/deploy/deploy-clients-to-macs.md)  

-   [Hoe gebruikers apparaten inschrijven met On-premises mobiele apparaten beheren in System Center Configuration Manager](../../../../mdm/deploy-use/user-enroll-devices-on-premises-mdm.md)  

**Toegestane verbindingen**  
 De HTTPS-instelling wordt automatisch geselecteerd en vereist een PKI-certificaat op de server voor serververificatie naar het proxypunt voor inschrijving, serververificatie naar de out-of-band-servicepunt en de versleuteling van gegevens over SSL. Zie voor meer informatie over de certificaatvereisten [PKI-certificaatvereisten voor System Center Configuration Manager](../../../../core/plan-design/network/pki-certificate-requirements.md).  

 Zie voor een Voorbeeldimplementatie van het servercertificaat en informatie over het configureren in IIS, de *het webservercertificaat implementeren voor Sitesystemen die IIS uitvoeren* in sectie [voorbeeld van stapsgewijze implementatie van de PKI-certificaten voor System Center Configuration Manager: Windows Server 2008-certificeringsinstantie](/sccm/core/plan-design/network/example-deployment-of-pki-certificates).  

##  <a name="BKMK_Enrollment_Proxy_Point"></a>Proxypunt voor inschrijving  
Zie voor meer informatie over het instellen van een proxypunt voor inschrijving voor mobiele apparaten, [hoe gebruikers apparaten inschrijven met On-premises mobiele apparaten beheren in System Center Configuration Manager](../../../../mdm/deploy-use/user-enroll-devices-on-premises-mdm.md).  

**Clientverbindingen**  
 De HTTPS-instelling wordt automatisch geselecteerd en vereist een PKI-certificaat op de server voor serververificatie naar mobiele apparaten en Mac-computers die zijn ingeschreven door Configuration Manager, en voor versleuteling van gegevens via Secure Sockets Layer (SSL). Zie voor meer informatie over de certificaatvereisten [PKI-certificaatvereisten voor System Center Configuration Manager](../../../../core/plan-design/network/pki-certificate-requirements.md).  

 Zie voor een Voorbeeldimplementatie van het servercertificaat en informatie over het configureren in IIS, de *het webservercertificaat implementeren voor Sitesystemen die IIS uitvoeren* in sectie [voorbeeld van stapsgewijze implementatie van de PKI-certificaten voor System Center Configuration Manager: Windows Server 2008-certificeringsinstantie](/sccm/core/plan-design/network/example-deployment-of-pki-certificates).  

##  <a name="BKMK_Fallback_Status_Point"></a>Terugvalstatuspunt  
**Aantal statusberichten** en **vertragingsinterval (in seconden)**  
Hoewel de standaardinstellingen voor deze opties (10.000 statusberichten en 3600 seconden vertragingsinterval) voldoende voor de meeste omstandigheden zijn, moet u wellicht wijzigen wanneer beide volgende voorwaarden waar zijn:  

-   Het terugvalstatuspunt accepteert alleen verbindingen van het intranet.  

-   U gebruikt het terugvalstatuspunt tijdens een clientimplementatierollout voor veel computers.  

In dit scenario kan een continue stroom van statusberichten een achterstand van statusberichten veroorzaken verbruik hoog central processing unit (CPU) op de siteserver gedurende langere tijd veroorzaken. Bovendien u ziet mogelijk ook geen actuele informatie over de clientimplementatie in Configuration Manager-console en in de clientimplementatierapporten.  

Deze instellingen voor terugvalstatuspunt zijn ontworpen om te worden ingesteld voor statusberichten die zijn gegenereerd tijdens de clientimplementatie. De instellingen zijn niet ontworpen om te worden ingesteld voor problemen met clientcommunicatie, zoals wanneer clients op het Internet geen verbinding met hun op Internet gebaseerde beheerpunt maken. Omdat het terugvalstatuspunt deze instellingen alleen op de statusberichten die zijn gegenereerd tijdens de clientimplementatie toepassen kan, niet configureert deze instellingen wanneer het terugvalstatuspunt verbindingen van het Internet accepteert.  

Elke computer die met succes de System Center 2012 Configuration Manager-client installeert verzendt de volgende vier statusberichten naar het terugvalstatuspunt:  

-   Clientimplementatie is gestart  

-   Clientimplementatie is voltooid  

-   Clienttoewijzing is gestart  

-   Clienttoewijzing is voltooid  

Computers die niet kan worden geïnstalleerd of dat de Configuration Manager-client toewijzen, verzenden bijkomende statusberichten.  

Bijvoorbeeld, als u de Configuration Manager-client naar 20.000 gebruikers implementeert, kan de implementatie 80.000 statusberichten verzenden naar het terugvalstatuspunt. Omdat de standaard beperkingsconfiguratie 10.000 statusberichten naar het terugvalstatuspunt-elke 3600 seconden (1 uur kunt) worden verzonden, kunnen statusberichten worden achterstallige op het terugvalstatuspunt. U moet ook rekening houden met de beschikbare netwerkbandbreedte tussen het terugvalstatuspunt en de siteserver en de processorsnelheid van de siteserver om veel statusberichten te verwerken.  

Houd rekening met een verhoging van het aantal statusberichten en een vermindering van vertragingsinterval ter voorkoming van deze problemen.  

Reset de beperkingswaarden voor het terugvalstatuspunt als een van de volgende voorwaarden zich voordoen:  

-   U berekent dat de huidige beperkingswaarden hoger dan nodig om te verwerken statusberichten van het terugvalstatuspunt zijn.  

-   U vindt dat de huidige beperkingsinstellingen een hoog CPU-gebruik op de siteserver.  

Wijzig de instellingen voor de beperkingsinstellingen terugvalstatuspunt niet als u de gevolgen. Bijvoorbeeld, als u de beperkingsinstellingen hoog, verhogen het CPU-gebruik op de siteserver in hoog, dit vertraagt alle sitebewerkingen.  

