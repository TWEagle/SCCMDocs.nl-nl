---
title: Site-onderdelen
titleSuffix: Configuration Manager
description: Leer hoe u configureert Siteonderdelen om het gedrag van sitesysteemrollen en sitestatusrapportage te wijzigen.
ms.custom: na
ms.date: 10/06/2016
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: configmgr-other
ms.tgt_pltfrm: na
ms.topic: get-started-article
ms.assetid: 5fccbbeb-0faa-4943-83c2-e67db62d392d
caps.latest.revision: "9"
author: mestew
ms.author: mstewart
manager: angrobe
ms.openlocfilehash: 4c5e6d4587f79eb52e9295d2641f985520738ebe
ms.sourcegitcommit: daa080cf220835f157a23e8c8e2bd2781b869bb7
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/04/2017
---
# <a name="site-components-for-system-center-configuration-manager"></a>Siteonderdelen voor System Center Configuration Manager

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*

Op elke site System Center Configuration Manager kunt u Siteonderdelen instellen om de gedrag van sitesysteemrollen en sitestatusrapportage te wijzigen. Siteonderdeelconfiguraties van toepassing op een site en elk exemplaar van een sitesysteemrol die van toepassing zijn op de site.  

## <a name="about-site-components"></a>Siteonderdelen  
 De meeste opties voor de verschillende Siteonderdelen behoeven geen uitleg wanneer weergegeven in de Configuration Manager-console. De volgende details kunnen echter helpen bevatten uitleg over enkele van de complexere configuraties, of u rechtstreeks naar aanvullende inhoud waarin deze worden uitgelegd.  

### <a name="software-distribution"></a>Softwaredistributie  

-   **Instellingen voor inhoudsdistributie:**  U kunt instellingen waarmee u aanpassen hoe de siteserver inhoud overdraagt naar de distributiepunten opgeven. Als u de waarden voor instellingen voor gelijktijdige distributie verhoogt, kan de inhoudsdistributie meer netwerkbandbreedte gebruiken.  

-   **Netwerktoegangsaccount:**  Zie voor meer informatie over het instellen en gebruiken het netwerktoegangsaccount [netwerktoegangsaccount](../../../../core/plan-design/hierarchy/manage-accounts-to-access-content.md#bkmk_NAA).  

### <a name="software-update-point"></a>Software-updatepunt  

-   Zie voor meer informatie over configuratieopties voor het softwareonderdeel-updatepunt [installeert een software-updatepunt](../../../../sum/get-started/install-a-software-update-point.md).  

### <a name="management-point"></a>Beheerpunt  

-   **Beheerpunten:** U kunt de site zo instellen dat er informatie over de eigen beheerpunten publiceert naar Active Directory Domain Services.  

     Configuration Manager-clients gebruiken beheerpunten te zoeken, services en site-informatie zoals lidmaatschap van grensgroepen en opties voor de selectie van PKI-certificaat vinden. Clients gebruiken ook beheerpunten andere om beheerpunten te vinden in de site, evenals de distributiepunten van waaruit software te downloaden. Beheerpunten kunnen ook clients voor site-toewijzing vervolledigen en voor het clientbeleid downloaden en clientgegevens uploaden.  

     Omdat de veiligste methode voor clients om beheerpunten te vinden in Active Directory Domain Services publiceren is, wordt doorgaans altijd selecteert u alle werkende beheerpunten publiceren naar Active Directory Domain Services. Deze servicelocatiemethode vereist echter de volgende wordt voldaan:

     - Het schema wordt uitgebreid voor Configuration Manager.
     - Er is een **System Management** container met geschikte beveiligingsmachtigingen voor de siteserver om te publiceren naar deze container.
     - De Configuration Manager-site is ingesteld om te publiceren naar Active Directory Domain Services.
     - Clients behoren tot hetzelfde Active Directory-forest als de forest de siteserver.  

     Wanneer clients op het intranet kunnen geen Active Directory Domain Services om beheerpunten te zoeken, gebruik [DNS](../../../../core/plan-design/hierarchy/understand-how-clients-find-site-resources-and-services.md#bkmk_dns) publiceren in plaats daarvan.  

 Raadpleeg voor algemene informatie over de servicelocatie [begrijpen hoe clients siteresources en -services voor System Center Configuration Manager vinden](../../../../core/plan-design/hierarchy/understand-how-clients-find-site-resources-and-services.md).  

-   **Geselecteerde intranetbeheerpunten publiceren in DNS:** Geef deze optie wanneer clients op het intranet beheerpunten van Active Directory Domain Services vinden kunnen. Ze kunnen in plaats daarvan een DNS-servicelocatiebronrecord (SRV RR) gebruiken om een beheerpunt te vinden in hun toegewezen site.  

    Configuration Manager intranetbeheerpunten publiceren naar DNS, alle volgende voorwaarden is voldaan:  

    -   Uw DNS-servers hebben een versie van BIND die 8.1.2 of hoger.  

    -   Uw DNS-servers zijn ingesteld voor automatische updates en ondersteunen servicelocatiebronrecords.  

    -   De opgegeven volledig gekwalificeerde domeinnamen (FQDN's) voor de beheerpunten in Configuration Manager hebben hostvermeldingen (A of AAA records) in DNS.  

    > [!WARNING]  
    >  Voor clients om beheerpunten die zijn gepubliceerd in DNS te zoeken, moet u de clients toewijzen aan een specifieke site (en niet automatische sitetoewijzing gebruiken). Deze clients instellen voor het gebruik van de sitecode met het domeinachtervoegsel van hun beheerpunt. Zie voor meer informatie [zoeken voor beheerpunten](/sccm/core/clients/deploy/assign-clients-to-a-site#locating-management-points) in [clients toewijzen aan een site in System Center Configuration Manager](/sccm/core/clients/deploy/assign-clients-to-a-site).  

     Als Configuration Manager-clients niet Active Directory Domain Services of DNS-server gebruiken om beheerpunten te vinden op het intranet, dan gebruiken deze [WINS](../../../../core/plan-design/hierarchy/understand-how-clients-find-site-resources-and-services.md#bkmk_wins). Het eerste beheerpunt dat voor de site is geïnstalleerd, wordt automatisch gepubliceerd naar WINS wanneer deze is ingesteld om HTTP-clientverbindingen op het intranet te aanvaarden.  

### <a name="status-reporting"></a>Statusrapportage  

-   Deze instellingen worden rechtstreeks het detailniveau dat is opgenomen in de statusrapporten van sites en clients instellen.  

### <a name="email-notification"></a>E-mailmeldingen  

-   Geef details op en het e-server zodat de Configuration Manager voor het verzenden van e-mailmeldingen voor waarschuwingen.  

### <a name="collection-membership-evaluation"></a>Evaluatie lidmaatschap verzameling  

-   Gebruik deze taak om in te stellen hoe vaak het verzamelingslidmaatschap stapsgewijs wordt geëvalueerd. Via stapsgewijze evaluatie werkt u een verzamelingslidmaatschap bij met uitsluitend nieuwe of gewijzigde bronnen.  

### <a name="edit-the-site-components-at-a-site"></a>De onderdelen van de site op een site bewerken  

Gebruik de volgende stappen uit om te bewerken van site-onderdelen:

1.  Klik in de Configuration Manager-console op **beheer** > **siteconfiguratie** > **Sites**, en selecteer vervolgens de site met site-onderdelen die u wilt configureren.  

2.  Op de **Start** tabblad, in de **instellingen** groep, klikt u op **Siteonderdelen configureren**. Selecteer vervolgens het siteonderdeel dat u wilt configureren.  

##  <a name="BKMK_ServiceMgr"></a> Configuration Manager Service Manager gebruiken om siteonderdelen te beheren  
U kunt de Configuration Manager Service Manager Configuration Manager-services beheren en weergeven van de status van alle Configuration Manager-services of werkende threads (gezamenlijk aangeduid als Configuration Manager-onderdelen). Inzicht in het volgende over Configuration Manager-onderdelen:  

-   Onderdelen kunnen worden uitgevoerd op elk sitesysteem.  

-   Onderdelen op dezelfde manier beheren van services in Windows worden beheerd. U kunt starten, stoppen, onderbreken, hervatten of opvragen van Configuration Manager-onderdelen.  

Een Configuration Manager-service wordt uitgevoerd wanneer er iets is om te doen (gewoonlijk wanneer een configuratiebestand wordt geschreven naar het postvak in van een onderdeel). Als u hebt het onderdeel dat betrokken is bij een bewerking moet identificeren, kunt u de Configuration Manager Service Manager gebruiken om verschillende services en threads te manipuleren. U kunt vervolgens de resulterende wijziging in het gedrag van Configuration Manager weergeven. U kunt bijvoorbeeld één van de Configuration Manager-services stoppen tegelijk, totdat een bepaalde respons wordt geëlimineerd. Op die manier kunt u bepalen welke service het gedrag veroorzaakt.  

> [!TIP]  
>  De volgende procedure kan worden gebruikt voor het bewerken van Configuration Manager-onderdeel-bewerking.  

### <a name="use-the-configuration-manager-service-manager"></a>De Configuration Manager Service Manager gebruiken  

1.  Klik in de Configuration Manager-console op **bewaking** >  **systeemstatus**, en klik vervolgens op **Onderdeelstatus**.  

2.  Op de **Start** tabblad, in de **onderdeel** groep, klikt u op **Start**. Selecteer vervolgens **Configuration Manager-servicebeheer**.  

3.  Wanneer het Configuration Manager-servicebeheer opent, verbindt dan met de site die u wilt beheren.  

     Als u de site die u wilt beheren, niet ziet, klik dan op **Site**, klik daarna op **Verbinden**, en geef vervolgens de naam van de siteserver van de juiste site in.  

4.  Vouw de site uit en navigeer naar **Onderdelen** of **Servers**, afhankelijk van waar de onderdelen zich bevinden die u wilt beheren.  

5.  Selecteer één of meer onderdelen in het rechterpaneel. Klik op de **onderdeel** menu, klikt u op **Query** de status van uw selectie bij te werken.  

6.  Nadat de status van het onderdeel is bijgewerkt, gebruikt u een van de vier op actie gebaseerde opties in de **onderdeel** menu van het onderdeel opnieuw te wijzigen. Nadat u een actie vraagt, moet u het onderdeel opvragen om de nieuwe status van het onderdeel weer te geven.  

7.  Sluit de Configuration Manager-servicebeheer wanneer u bent klaar voor het wijzigen van de operationele status van onderdelen.  
