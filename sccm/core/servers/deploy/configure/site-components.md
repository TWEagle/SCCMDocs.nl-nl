---
title: Site-onderdelen voor Configuration Manager | Microsoft-documenten
description: Leer hoe u configureert Siteonderdelen om het gedrag van sitesysteemrollen en site statusrapportage wijzigen.
ms.custom: na
ms.date: 10/06/2016
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: get-started-article
ms.assetid: 5fccbbeb-0faa-4943-83c2-e67db62d392d
caps.latest.revision: 9
author: Brenduns
ms.author: brenduns
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 1b9e49da1a5bbfca93fe683b82d2c0056a22cc1f
ms.openlocfilehash: 83550fbf0ef1f9adb0bb2c51a4f3c26a7500d352
ms.contentlocale: nl-nl
ms.lasthandoff: 05/17/2017


---
# <a name="site-components-for-system-center-configuration-manager"></a>Site-onderdelen voor System Center Configuration Manager

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*

Op elke site System Center Configuration Manager kunt u site-onderdelen instellen om het gedrag van sitesysteemrollen en statusrapportage site. Siteonderdeelconfiguraties toepassing op een site en op elk exemplaar van een bijbehorende sitesysteemrol op de site.  

## <a name="about-site-components"></a>Siteonderdelen  
 De meeste opties voor de verschillende Siteonderdelen behoeven geen uitleg ziet er in de Configuration Manager-console. Echter kunt de volgende gegevens verklaren complexere configuraties of vindt u aanvullende inhoud die ze wordt uitgelegd.  

### <a name="software-distribution"></a>Softwaredistributie  

-   **Instellingen voor het distribueren van inhoud:**  U kunt instellingen wijzigen hoe de siteserver inhoud overdraagt naar de distributiepunten opgeven. Als u de waarden voor instellingen voor gelijktijdige distributie verhoogt, kan de inhoudsdistributie meer netwerkbandbreedte gebruiken.  

-   **Network Access Account:**  Zie voor meer informatie over het instellen en gebruiken het netwerktoegangsaccount [netwerktoegangsaccount](../../../../core/plan-design/hierarchy/manage-accounts-to-access-content.md#bkmk_NAA).  

### <a name="software-update-point"></a>Software-updatepunt  

-   Zie voor meer informatie over configuratieopties voor het softwareonderdeel-updatepunt [installeert een software-updatepunt](../../../../sum/get-started/install-a-software-update-point.md).  

### <a name="management-point"></a>Beheerpunt  

-   **Beheerpunten:** U kunt de site zo instellen dat er informatie over de beheerpunten publiceren naar Active Directory Domain Services.  

     Configuration Manager-clients gebruiken beheerpunten te zoeken, services en site-informatie zoals lidmaatschap van grensgroepen en opties voor selectie van PKI-certificaten te vinden. Clients gebruiken ook beheerpunten te vinden van andere beheerpunten in de site, evenals de distributiepunten van waaruit software kan worden gedownload. Beheerpunten helpt ook clients om sitetoewijzing te voltooien en clientbeleid te downloaden en clientinformatie te uploaden.  

     Omdat de veiligste methode voor clients om beheerpunten te vinden in Active Directory Domain Services publiceren, selecteert u gewoonljik altijd alle werkende beheerpunten publiceren naar Active Directory Domain Services. Deze servicelocatiemethode vereist echter het volgende waar zijn:

     - Het schema wordt uitgebreid voor Configuration Manager.
     - Er is een **Systeembeheer** container met geschikte beveiligingsmachtigingen voor de siteserver om naar deze container te publiceren.
     - De Configuration Manager-site is ingesteld om te publiceren naar Active Directory Domain Services.
     - Clients behoren tot hetzelfde Active Directory-forest als het forest van de siteserver.  

     Wanneer clients op het intranet Active Directory Domain Services gebruiken kunnen om beheerpunten te zoeken, gebruik [DNS](../../../../core/plan-design/hierarchy/understand-how-clients-find-site-resources-and-services.md#bkmk_dns) publiceren in plaats daarvan.  

 Raadpleeg voor algemene informatie over service-locatie [begrijpen hoe clients vinden sitebronnen en services voor System Center Configuration Manager](../../../../core/plan-design/hierarchy/understand-how-clients-find-site-resources-and-services.md).  

-   **Geselecteerde intranetbeheerpunten publiceren in DNS:** Deze optie opgeven wanneer clients op het intranet beheerpunten van Active Directory Domain Services vinden kunnen. Ze kunnen in plaats daarvan een DNS-servicelocatiebronrecord (SRV RR) gebruiken om een beheerpunt te vinden in hun toegewezen site.  

    Configuration Manager kan intranetbeheerpunten naar DNS publiceren, alle volgende voorwaarden is voldaan:  

    -   Uw DNS-servers hebben een versie van BIND 8.1.2 of hoger.  

    -   Uw DNS-servers zijn ingesteld voor automatische updates en ondersteunen servicelocatiebronrecords.  

    -   De opgegeven volledig gekwalificeerde domeinnamen (FQDN) voor de beheerpunten in Configuration Manager hebben hostvermeldingen (A of AAA-records) in DNS.  

    > [!WARNING]  
    >  Clients zoeken naar beheerpunten die in DNS zijn gepubliceerd, moet u de clients toewijzen aan een specifieke site (eerder dan automatische sitetoewijzing gebruiken). Deze clients instellen voor gebruik van de sitecode met het domeinachtervoegsel van hun beheerpunt. Zie voor meer informatie [zoeken beheerpunten](/sccm/core/clients/deploy/assign-clients-to-a-site#locating-management-points) in [clients toewijzen aan een site in System Center Configuration Manager](/sccm/core/clients/deploy/assign-clients-to-a-site).  

     Als Configuration Manager-clients Active Directory Domain Services of DNS gebruiken kunnen om beheerpunten te vinden op het intranet, dan gebruiken deze [WINS](../../../../core/plan-design/hierarchy/understand-how-clients-find-site-resources-and-services.md#bkmk_wins). Het eerste beheerpunt dat voor de site is geïnstalleerd, wordt automatisch gepubliceerd naar WNS wanneer deze is ingesteld om HTTP-clientverbindingen op het intranet te aanvaarden.  

### <a name="status-reporting"></a>Statusrapportage  

-   Deze instellingen instellen rechtstreeks naar het detailniveau die is opgenomen in de statusrapporten van sites en clients.  

### <a name="email-notification"></a>E-mailmeldingen  

-   Geef details op mailaccount en e-mail server Configuration Manager voor het verzenden van e-mailmeldingen voor waarschuwingen inschakelen.  

### <a name="collection-membership-evaluation"></a>Evaluatie lidmaatschap verzameling  

-   Gebruik deze taak om in te stellen hoe vaak het verzamelingslidmaatschap stapsgewijs wordt geëvalueerd. Via stapsgewijze evaluatie werkt u een verzamelingslidmaatschap bij met uitsluitend nieuwe of gewijzigde bronnen.  

### <a name="edit-the-site-components-at-a-site"></a>De Siteonderdelen op een site bewerken  

Gebruik de volgende stappen Siteonderdelen bewerken:

1.  Klik in de Configuration Manager-console op **beheer** > **siteconfiguratie** > **Sites**, en selecteer vervolgens de site met site-onderdelen die u wilt configureren.  

2.  Op de **Start** tabblad, in de **instellingen** groep, klikt u op **Siteonderdelen configureren**. Schakel vervolgens het siteonderdeel die u wilt configureren.  

##  <a name="BKMK_ServiceMgr"></a> Configuration Manager Service Manager gebruiken om siteonderdelen te beheren  
U kunt de Service van Configuration Manager gebruiken voor het beheren van Configuration Manager-services en de status van een Configuration Manager-service of working-thread weergeven (gezamenlijk aangeduid als Configuration Manager-onderdelen). De hoogte van het volgende over Configuration Manager-onderdelen:  

-   Onderdelen kunnen worden uitgevoerd op elk sitesysteem.  

-   Onderdelen worden beheerd als dezelfde manier als u services in Windows beheert. U kunt starten, stoppen, onderbreken, hervatten of opvragen van Configuration Manager-onderdelen.  

Een Configuration Manager-service wordt uitgevoerd wanneer er iets is om te doen (gewoonlijk wanneer een configuratiebestand wordt geschreven naar Postvak in van een onderdeel). Als u hebt het onderdeel dat betrokken is bij een bewerking moet identificeren, kunt u de Service van Configuration Manager gebruiken om verschillende services en threads te manipuleren. U kunt vervolgens de resulterende wijziging weergeven in het gedrag van Configuration Manager. U kunt bijvoorbeeld een Configuration Manager-services stoppen tegelijk, tot een bepaalde respons wordt geëlimineerd. Op die manier kunt u bepalen welke service het gedrag veroorzaakt.  

> [!TIP]  
>  De volgende procedure kan worden gebruikt voor het bewerken van Configuration Manager-onderdeel-bewerking.  

### <a name="use-the-configuration-manager-service-manager"></a>De Configuration Manager-servicebeheer gebruiken  

1.  Klik in de Configuration Manager-console op **bewaking** >  **systeemstatus**, en klik vervolgens op **Onderdeelstatus**.  

2.  Op de **Start** tabblad, in de **onderdeel** groep, klikt u op **Start**. Selecteer **Configuration Manager-servicebeheer**.  

3.  Wanneer het Configuration Manager-servicebeheer opent, verbindt dan met de site die u wilt beheren.  

     Als u de site die u wilt beheren, niet ziet, klik dan op **Site**, klik daarna op **Verbinden**, en geef vervolgens de naam van de siteserver van de juiste site in.  

4.  Vouw de site uit en navigeer naar **Onderdelen** of **Servers**, afhankelijk van waar de onderdelen zich bevinden die u wilt beheren.  

5.  Selecteer één of meer onderdelen in het rechterpaneel. Klik vervolgens op de **onderdeel** menu, klikt u op **Query** de status van uw selectie bij te werken.  

6.  Nadat de status van het onderdeel is bijgewerkt, gebruikt u één van de vier op actie gebaseerde opties in de **onderdeel** menu van het onderdeel opnieuw te wijzigen. Nadat u een actie vraagt, moet u het onderdeel opvragen om de nieuwe status van het onderdeel weer te geven.  

7.  Sluit de Configuration Manager-servicebeheer wanneer u klaar voor het wijzigen van de operationele status van onderdelen.  

