---
title: Grootte en schaal
titleSuffix: Configuration Manager
description: Zoek het nummer van sitesysteemrollen en sites die u moet ondersteuning van de apparaten in uw omgeving voor System Center Configuration Manager.
ms.custom: na
ms.date: 07/24/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: c5a42100-2f60-4952-b495-918025ea6559
caps.latest.revision: "4"
author: mestew
ms.author: mstewart
manager: angrobe
ms.openlocfilehash: bda1ab737a3af5e13f180771cc17c9850165906c
ms.sourcegitcommit: daa080cf220835f157a23e8c8e2bd2781b869bb7
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/04/2017
---
# <a name="size-and-scale-numbers-for-system-center-configuration-manager"></a>Grootte en schaalgetallen voor System Center Configuration Manager

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*



Elke System Center Configuration Manager-implementatie heeft een maximum aantal sites, sitesysteemrollen en apparaten dat kan worden ondersteund. Deze getallen, is afhankelijk van de hiërarchiestructuur van uw (welke typen en het aantal sites u) en de sitesysteemrollen die u implementeert.  De informatie in de volgende gebieden kunt u het aantal sitesysteemrollen en sites die u ondersteuning van de apparaten die u verwacht moet te beheren met uw omgeving te identificeren.

Gebruik de informatie in dit onderwerp in combinatie met de informatie in de volgende artikelen:
-   [Aanbevolen hardware](../../../core/plan-design/configs/recommended-hardware.md)
-   [Ondersteunde besturingssystemen voor sitesysteemservers](../../../core/plan-design/configs/supported-operating-systems-for-site-system-servers.md)  
-   [Ondersteunde besturingssystemen voor clients en apparaten](../../../core/plan-design/configs/supported-operating-systems-for-clients-and-devices.md)
-   [Vereisten voor sites en sitesystemen](../../../core/plan-design/configs/site-and-site-system-prerequisites.md)


De volgende ondersteuning cijfers zijn gebaseerd op het gebruik van de aanbevolen hardware voor Configuration Manager en de standaardinstellingen voor alle beschikbare functies in de Configuration Manager. Wanneer u geen gebruik van de aanbevolen hardware of agressievere aangepaste instellingen (zoals actieve hardware of software-inventaris vaker dan de standaardwaarden van om de zeven dagen) gebruiken, wordt de prestaties van sitesystemen kan verminderen en voldoet niet aan de vermelde ondersteuningsniveaus.

##  <a name="bkmk_SiteSystemScale"></a>Typen sites  
 **Centrale beheersite:**  

-   Een centrale beheersite ondersteunt maximaal 25 onderliggende primaire sites.  

**Primaire site:**  

-   Elke primaire site ondersteunt maximaal 250 secundaire sites.  

-   Het aantal secundaire sites per primaire site is gebaseerd op verbindingen permanente en betrouwbare verbinding wide area network (WAN). Voor locaties met minder dan 500 clients hebt, kunt u een distributiepunt in plaats van een secundaire site.  

 Zie voor informatie over het aantal clients en apparaten dat een primaire site kan ondersteunen, [clientaantallen voor sites en hiërarchieën](#bkmk_clientnumbers) in dit onderwerp.  

**Secundaire site:**  

-   Secundaire sites ondersteunen geen onderliggende sites.  



## <a name="bkmk_roles"></a>Sitesysteemrollen    


**Application Catalog-webservicepunt:**  

-   U kunt meerdere exemplaren van het Application Catalog-webservicepunt op primaire sites installeren.  

    > [!TIP]  
    >  Als een best practice, installeer het Application Catalog-websitepunt en Application Catalog-webservicepunt samen op hetzelfde sitesysteem wanneer deze services bieden aan clients die zich op het intranet.  

    -   Plannen voor verbeterde prestaties voor de ondersteuning van maximaal 50.000 clients per exemplaar.  

    -   Elk exemplaar van deze sitesysteemrol ondersteunt het maximum aantal clients die worden ondersteund door de hiërarchie.  

**Application Catalog-websitepunt:**  

-   U kunt meerdere exemplaren van de Application Catalog-websitepunt op primaire sites installeren.  

    > [!TIP]  
    >  Als een best practice, installeer het Application Catalog-websitepunt en Application Catalog-webservicepunt samen op hetzelfde sitesysteem wanneer deze services bieden aan clients die zich op het intranet.  

    -   Plannen voor verbeterde prestaties voor de ondersteuning van maximaal 50.000 clients per exemplaar.  

    -   Elk exemplaar van deze sitesysteemrol ondersteunt het maximum aantal clients die worden ondersteund door de hiërarchie.  


**Distributiepunt:**  

-   Distributiepunten per site:  

    -   Elke primaire en secundaire site ondersteunt maximaal 250 distributiepunten.  

    -   Elke primaire en secundaire site ondersteunt maximaal 2.000 aanvullende distributiepunten die zijn geconfigureerd als pull-distributiepunten. **Bijvoorbeeld**, een enkele primaire site ondersteunt 2250 distributiepunten wanneer 2000 van deze distributiepunten als pull-distributiepunten zijn geconfigureerd.  

    -   Elk distributiepunt ondersteunt verbindingen van maximaal 4.000 clients.  

    -   Een pull-distributiepunt fungeert als een client wanneer het toegang verkrijgt inhoud vanaf een brondistributiepunt tot.  

-   Elke primaire site ondersteunt een gecombineerd totaal van maximaal 5.000 distributiepunten. Dit totaal bevat alle distributiepunten op de primaire site en alle distributiepunten die deel uitmaken van de primaire site onderliggende secundaire sites.  

-   Elk distributiepunt ondersteunt een gecombineerd totaal van maximaal 10.000 pakketten en toepassingen.  

> [!WARNING]  
>  Het werkelijke aantal clients die ondersteuning voor één distributiepunt biedt, is afhankelijk van de snelheid van het netwerk en de hardwareconfiguratie van de distributiepuntcomputer.  
>   
>  Het aantal pull-distributiepunten die ondersteuning voor één brondistributiepunt biedt is ook afhankelijk van de snelheid van het netwerk en de hardwareconfiguratie van de bron voor de distributiepuntcomputer. Maar dit nummer wordt ook beïnvloed door de hoeveelheid inhoud die u hebt geïmplementeerd. Dit komt doordat, in tegenstelling tot clients die doorgaans toegang inhoud op verschillende momenten tijdens een implementatie tot, alle pull-distributiepunten inhoud aanvragen tegelijk, en alle beschikbare inhoud, niet alleen de inhoud die van toepassing, is als een client zou kunnen aanvragen. Wanneer er te veel verwerking wordt geplaatst op een brondistributiepunt, kunnen er onverwachte vertragingen in het distribueren van de inhoud naar de verwachte distributiepunten in uw omgeving.  


**Terugvalstatuspunt:**  

-   Elk terugvalstatuspunt kan maximaal 100.000 clients ondersteunen.  

**Beheerpunt:**  

-   Elke primaire site ondersteunt maximaal 15 beheerpunten.  

    > [!TIP]  
    >  Installeer geen beheerpunten op servers die via een langzame verbinding van de primaire siteserver of van de Sitedatabaseserver zijn.  

-   Elke secundaire site ondersteunt één enkel beheerpunt dat moet worden geïnstalleerd op de secundaire siteserver.  

 Zie voor informatie over het aantal clients en apparaten die ondersteuning voor een beheerpunt biedt, het [beheerpunten](#bkmk_mp) in dit onderwerp.  

**Software-updatepunt:**  

-   Een software-updatepunt dat is geïnstalleerd op de siteserver kan tot 25.000 clients ondersteunen.  

-   Een software-updatepunt dat zich op afstand van de siteserver kan maximaal 150.000 clients ondersteunen wanneer de externe computer voldoet aan de vereisten van de Windows Server Update Services (WSUS) om dit aantal clients te ondersteunen.  

-   Configuration Manager biedt geen configureren van het software-updatepunten ondersteuning zoals Network Load Balancing (NLB)-clusters. U kunt echter de Configuration Manager SDK maximaal vier software-updatepunten op een NLB-cluster configureren.  

##  <a name="bkmk_clientnumbers"></a>Clientaantallen voor sites en hiërarchieën  
 Gebruik de volgende informatie om te bepalen hoeveel clients en welke typen clients u ondersteuning biedt voor op een site of in een hiërarchie.  

###  <a name="bkmk_cas"></a>Hiërarchie met een centrale beheersite  
Een centrale beheersite ondersteunt een totaal aantal apparaten tot het aantal apparaten opgenomen voor de volgende drie groepen:  

-   700.000 desktops (computers waarop Windows, Linux en UNIX wordt uitgevoerd). Zie ook, ondersteuning voor [embedded-apparaten](#embedded).

-   25.000 apparaten met Mac en Windows CE 7.0  

-   Een van de volgende, afhankelijk van hoe uw implementatie ondersteuning biedt voor beheer van mobiele apparaten (MDM):  

    -   100.000 apparaten die u beheert via on-premises MDM  

    -   300.000 cloudapparaten  

 Bijvoorbeeld in een hiërarchie, kunt u ondersteunen 700.000 desktops, maximaal 25.000 Mac en Windows CE 7.0 en maximaal 300.000 cloudapparaten wanneer u Microsoft Intune integreert, voor een totaal 1.025.000 apparaten. Als u ondersteuning voor apparaten die worden beheerd door lokale MDM, is het totaal voor de hiërarchie 825.000 apparaten.  

> [!IMPORTANT]  
>  In een hiërarchie waarbij de centrale beheersite een Standard-editie van SQL Server gebruikt, ondersteunt de hiërarchie maximaal 50.000 desktops en apparaten. Ter ondersteuning van meer dan 50.000 desktops en apparaten, moet u een Enterprise-editie van SQL Server. Deze vereiste geldt alleen voor een centrale beheersite en niet van toepassing op een zelfstandige primaire site of een onderliggende primaire site waar de editie van SQL Server die u gebruikt de capaciteit van de site ter ondersteuning van het vermelde aantal clients niet beperkt.   


 De editie van SQL Server die wordt gebruikt op een zelfstandige primaire site beperken niet die site capaciteit voor maximaal het vermelde aantal clients ondersteunen.  


###  <a name="bkmk_chipri"></a>Onderliggende primaire site  
Elke onderliggende primaire site in een hiërarchie met een centrale beheersite ondersteunt het volgende:  

-   150.000 totaal aantal clients en apparaten die niet beperkt tot een specifieke groep of type, zolang de ondersteuning wordt niet langer zijn dan het getal dat wordt ondersteund voor de hiërarchie. Zie ook, ondersteuning voor [embedded-apparaten](#embedded).

Bijvoorbeeld: een primaire site die ondersteuning biedt voor 25.000 computers waarop Mac en Windows CE 7.0 worden uitgevoerd (omdat dit de limiet voor een hiërarchie) kan vervolgens een extra 125,000 desktopcomputers ondersteunen. Hiermee wordt het totale aantal ondersteunde apparaten tot de onderliggende primaire site het ondersteunde maximum aantal 150.000.

###  <a name="bkmk_pri"></a>Zelfstandige primaire site  
Een zelfstandige primaire site ondersteunt het volgende aantal apparaten:  

-   175.000 totaal aantal clients en apparaten, waarvan maximaal:  

    -   150.000 desktops (computers waarop Windows, Linux en UNIX wordt uitgevoerd). Zie ook, ondersteuning voor [embedded-apparaten](#embedded).

    -   25.000 apparaten met Mac en Windows CE 7.0

    -   Een van de volgende, afhankelijk van hoe uw implementatie ondersteuning biedt voor beheer van mobiele apparaten:  

        -   50.000 apparaten die u beheert via on-premises MDM  

        -   150.000 cloudapparaten  


Een zelfstandige primaire site die ondersteuning biedt voor 150.000 desktops en 10.000 Mac of Windows CE 7.0 kan bijvoorbeeld slechts 15.000 extra apparaten ondersteunen. Deze apparaten kunnen bestaan uit cloud-gebaseerde of beheerde met behulp van de lokale MDM.  

### <a name="embedded"></a>Primaire sites en Windows Embedded-apparaten
Primaire sites ondersteunen Windows Embedded-apparaten waarvoor File-Based Write Filters (FBWF) ingeschakeld. Wanneer de ingesloten apparaten geen schrijffilters zijn ingeschakeld, kan een primaire site een aantal ingesloten apparaten tot maximaal het toegestane aantal apparaten ondersteunen voor die site. Van het totale aantal apparaten dat een primaire site ondersteunt maximaal 10.000 uit deze Windows Embedded-apparaten kan zijn wanneer deze apparaten zijn geconfigureerd voor de uitzonderingen die worden vermeld in de belangrijke opmerking gevonden in de [Planning voor clientimplementatie op Windows Embedded-apparaten](/sccm/core/clients/deploy/plan/planning-for-client-deployment-to-windows-embedded-devices). Een primaire site ondersteunt slechts 3.000 Windows Embedded-apparaten waarvoor EWF is ingeschakeld en die niet zijn geconfigureerd voor de uitzonderingen.

###  <a name="bkmk_sec"></a>Secundaire sites  
Secundaire sites ondersteunen het volgende:  

-   15.000 desktops (computers waarop Windows, Linux en UNIX wordt uitgevoerd)  

###  <a name="bkmk_mp"></a>Beheerpunten  
Elk beheerpunt kan het volgende aantal apparaten ondersteunen:  

-   25.000 totaal aantal clients en apparaten, waarvan maximaal:  

    -   25.000 desktops (computers waarop Windows, Linux en UNIX wordt uitgevoerd)  

    -   Een van de volgende (niet beide):  

        -   10.000 apparaten die worden beheerd door via on-premises MDM  

        -   10.000 apparaten met Mac en Windows CE 7.0-clients
