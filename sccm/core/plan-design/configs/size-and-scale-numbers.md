---
title: Grootte en schaal | Microsoft-documenten
description: Identificeer het aantal sitesysteemrollen en sites die u moet voor de ondersteuning van de apparaten in uw omgeving voor System Center Configuration Manager.
ms.custom: na
ms.date: 12/30/2016
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: c5a42100-2f60-4952-b495-918025ea6559
caps.latest.revision: 4
author: Brenduns
ms.author: brenduns
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: f9c43e26758d5171a6ef56e827b4b054ebc8a5e5
ms.openlocfilehash: c7ad33339e65e6e00e88f98d6e13baceb98dae77
ms.contentlocale: nl-nl
ms.lasthandoff: 05/17/2017

---
# <a name="size-and-scale-numbers-for-system-center-configuration-manager"></a>Grootte en schaal cijfers voor System Center Configuration Manager

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*



Elke System Center Configuration Manager-implementatie heeft een maximum aantal sites, sitesysteemrollen en apparaten die kan worden ondersteund. Deze getallen zijn afhankelijk van de hiërarchiestructuur van uw (welke typen en het aantal sites u) en de sitesysteemrollen die u implementeert.  Aan de hand van de informatie in de volgende gebieden kunt u bepalen het aantal sitesysteemrollen en sites u nodig hebt om de apparaten die u verwacht te beheren met uw omgeving te ondersteunen.

Gebruik de informatie in dit onderwerp in combinatie met de informatie in de volgende artikelen:
-   [Aanbevolen hardware](../../../core/plan-design/configs/recommended-hardware.md)
-   [Ondersteunde besturingssystemen voor sitesysteemservers](../../../core/plan-design/configs/supported-operating-systems-for-site-system-servers.md)  
-   [Ondersteunde besturingssystemen voor clients en apparaten](../../../core/plan-design/configs/supported-operating-systems-for-clients-and-devices.md)
-   [Site- en site-systeemvereisten](../../../core/plan-design/configs/site-and-site-system-prerequisites.md)


De volgende ondersteuning getallen zijn gebaseerd op het gebruik van de aanbevolen hardware voor Configuration Manager en de standaardinstellingen voor alle beschikbare Configuration Manager-functies. Wanneer u niet de aanbevolen hardware gebruiken, of agressievere aangepaste instellingen (zoals actieve hardware of software-inventaris vaker dan de standaardwaarden van om de zeven dagen) gebruiken, worden de prestaties van site-systemen kan gedegradeerd en voldoet niet aan de vermelde niveaus van ondersteuning.

##  <a name="bkmk_SiteSystemScale"></a>Site-typen  
 **Centrale beheersite:**  

-   Een centrale beheersite ondersteunt maximaal 25 onderliggende primaire sites.  

**Primaire site:**  

-   Elke primaire site ondersteunt maximaal 250 secundaire sites.  

-   Het aantal secundaire sites per primaire site is gebaseerd op continu verbonden en betrouwbare wide area network (WAN) verbindingen. Voor de locaties die minder dan 500 clients hebt, kunt u een distributiepunt in plaats van een secundaire site.  

 Zie voor informatie over het aantal clients en apparaten die een primaire site kan ondersteunen, [Client cijfers voor sites en hiërarchieën](#bkmk_clientnumbers) in dit onderwerp.  

**Secundaire site:**  

-   Secundaire sites ondersteunen geen onderliggende sites.  

-   Een centrale beheersite ondersteunt maximaal 25 onderliggende primaire sites.  

**Application Catalog-websitepunt:**  

-   U kunt meerdere exemplaren van de Application Catalog-websitepunt op primaire sites installeren.  

    > [!TIP]  
    >  Als een best practice installeert het Application Catalog-websitepunt en Application Catalog-webservicepunt bij elkaar op hetzelfde sitesysteem wanneer ze service leveren aan andere clients die zich op het intranet.  

    -   Plan voor verbeterde prestaties voor de ondersteuning van maximaal 50.000 clients per exemplaar.  

    -   Elk exemplaar van deze sitesysteemrol ondersteunt het maximum aantal clients die worden ondersteund door de hiërarchie.  

## <a name="bkmk_roles"></a>Sitesysteemrollen    

**Application Catalog-webservicepunt:**  

-   U kunt meerdere exemplaren van het Application Catalog-webservicepunt op primaire sites installeren.  

    > [!TIP]  
    >  Als een best practice installeert het Application Catalog-websitepunt en Application Catalog-webservicepunt bij elkaar op hetzelfde sitesysteem wanneer ze service leveren aan andere clients die zich op het intranet.  

    -   Plan voor verbeterde prestaties voor de ondersteuning van maximaal 50.000 clients per exemplaar.  

    -   Elk exemplaar van deze sitesysteemrol ondersteunt het maximum aantal clients die worden ondersteund door de hiërarchie.  

**Distributiepunt:**  

-   Distributiepunten per site:  

    -   Elke primaire en secundaire site ondersteunt maximaal 250 distributiepunten.  

    -   Elke primaire en secundaire site ondersteunt maximaal 2000 extra distributiepunten die zijn geconfigureerd als pull-distributiepunten. **Bijvoorbeeld**, een enkele primaire site ondersteunt 2250 distributiepunten wanneer 2000 van deze distributiepunten zijn geconfigureerd als pull-distributiepunten.  

    -   Elk distributiepunt ondersteunt verbindingen van maximaal 4000 clients.  

    -   Een pull-distributiepunt fungeert als een client wanneer deze toegang heeft tot inhoud vanaf een brondistributiepunt.  

-   Elke primaire site ondersteunt een totaal van maximaal 5000 distributiepunten. Totaal omvat alle distributiepunten op de primaire site en de distributiepunten die deel uitmaken van de primaire site onderliggende secundaire sites.  

-   Elk distributiepunt biedt ondersteuning voor een totaal van 10.000 pakketten en toepassingen.  

> [!WARNING]  
>  Het werkelijke aantal clients dat een distributiepunt kan ondersteunen, is afhankelijk van de snelheid van het netwerk en de hardwareconfiguratie van de distributiepuntcomputer.  
>   
>  Het aantal pull-distributiepunten die kan worden ondersteund door een brondistributiepunt op dezelfde manier hangt af van de snelheid van het netwerk en de hardwareconfiguratie van de bron voor de distributiepuntcomputer. Maar dit nummer wordt ook beïnvloed door de hoeveelheid inhoud die u hebt geïmplementeerd. Dit komt doordat in tegenstelling tot clients die doorgaans toegang inhoud op verschillende tijdstippen tijdens een implementatie tot, alle pull-distributiepunten inhoud op hetzelfde moment opvragen — en alle beschikbare inhoud, niet alleen de inhoud die is van toepassing op, zoals een client zou kunnen aanvragen. Als u te veel een verwerkingsbelasting op plaatst een brondistributiepunt, kunnen er onverwachte vertragingen bij de distributie van de inhoud naar de verwachte distributiepunten in uw omgeving.  


**Terugvalstatuspunt:**  

-   Elke terugvalstatuspunt kan tot 100.000 clients ondersteunen.  

**Beheerpunt:**  

-   Elke primaire site ondersteunt maximaal 15 beheerpunten.  

    > [!TIP]  
    >  Installeer geen beheerpunten op servers die op een langzame verbinding van de primaire siteserver of van de Sitedatabaseserver.  

-   Elke secundaire site ondersteunt een enkel beheerpunt die moet worden geïnstalleerd op de secundaire siteserver.  

 Zie voor informatie over het aantal clients en apparaten die een beheerpunt kan ondersteunen, de [beheerpunten](#bkmk_mp) in dit onderwerp.  

**Software-updatepunt:**  

-   Een software-updatepunt dat is geïnstalleerd op de siteserver kan tot 25.000 clients ondersteunen.  

-   Een software-updatepunt dat extern is van de siteserver kan maximaal 150.000 clients ondersteunen wanneer de externe computer voldoet aan de vereisten van Windows Server Update Services (WSUS) voor de ondersteuning van dit aantal clients.  

-   Standaard ondersteunt Configuration Manager geen configuratie software-updatepunten zoals clusters met Network Load Balancing (NLB). U kunt echter de Configuration Manager-SDK gebruiken voor het configureren van maximaal vier software-updatepunten op een NLB-cluster.  

##  <a name="bkmk_clientnumbers"></a>Client cijfers voor sites en hiërarchieën  
 Gebruik de volgende informatie om te bepalen hoeveel clients en welke typen clients kunt u ondersteunen op een site of in een hiërarchie.  

###  <a name="bkmk_cas"></a>Hiërarchie met een centrale beheersite  
Een centrale beheersite ondersteunt een totaal aantal apparaten met aanvullen tot maximaal het aantal apparaten die worden vermeld voor de volgende drie groepen:  

-   700.000 desktops (computers waarop Windows, Linux en UNIX wordt uitgevoerd)  

-   25.000 apparaten met Mac- en Windows CE 7.0  

-   Een van de volgende, afhankelijk van hoe uw implementatie mobiel Apparaatbeheer (MDM) ondersteunt:  

    -   100.000 apparaten die u beheert met behulp van de lokale MDM  

    -   300.000 cloud-gebaseerde apparaten  

 Bijvoorbeeld in een hiërarchie, kunt u ondersteunen 700.000 desktops, maximaal 25.000 Mac- en Windows CE 7.0 en maximaal 300.000 cloud-gebaseerde apparaten wanneer u Microsoft Intune integreert — voor een totaal van 1,025,000 apparaten. Als u apparaten die worden beheerd door MDM lokale ondersteunen, is het totaal voor de hiërarchie 825,000 apparaten.  

> [!IMPORTANT]  
>  In een hiërarchie waarbij de centrale beheersite een Standard-editie van SQL Server gebruikt, ondersteunt de hiërarchie maximaal 50.000 desktops en apparaten. De editie van SQL Server die wordt gebruikt op een zelfstandige primaire site beperkt niet capaciteit voor de ondersteuning van tot het opgegeven aantal clients die site.  


###  <a name="bkmk_chipri"></a>Onderliggende primaire site  
Elke onderliggende primaire site in een hiërarchie met een centrale beheersite ondersteunt het volgende:  

-   150.000 totaal aantal clients en apparaten die niet beperkt tot een specifieke groep of type, mits ondersteuning niet langer zijn dan het getal dat wordt ondersteund voor de hiërarchie.  

Zo kan een primaire site die ondersteuning biedt voor 25.000 computers waarop Mac- en Windows CE 7.0 wordt uitgevoerd (omdat die de limiet voor een hiërarchie) klikt u vervolgens een extra 125,000 desktopcomputers ondersteunen. Hiermee wordt het totale aantal ondersteunde apparaten maximaal ondersteunde maximum aantal van de onderliggende primaire site van 150.000.

###  <a name="bkmk_pri"></a>Zelfstandige primaire site  
Een zelfstandige primaire site ondersteunt het volgende aantal apparaten:  

-   175,000 totaal aantal clients en apparaten, niet langer zijn dan:  

    -   150.000 desktops (computers waarop Windows, Linux en UNIX wordt uitgevoerd)  

    -   25.000 apparaten met Mac- en Windows CE 7.0

    -   Een van de volgende, afhankelijk van hoe uw implementatie ondersteuning biedt voor beheer van mobiele apparaten:  

        -   50.000 apparaten die u beheert met behulp van de lokale MDM  

        -   150.000 cloud-gebaseerde apparaten  

Een zelfstandige primaire site die ondersteuning biedt voor 150.000 bureaubladen en 10.000 Mac of Windows CE 7.0 kan bijvoorbeeld alleen een extra 15.000 apparaten ondersteunen. Deze apparaten kunnen worden cloud-gebaseerde of beheerde via lokale MDM  

###  <a name="bkmk_sec"></a>Secundaire sites  
Secundaire sites ondersteunen het volgende:  

-   15.000 desktops (computers waarop Windows, Linux en UNIX wordt uitgevoerd)  

###  <a name="bkmk_mp"></a>Beheerpunten  
Elk beheerpunt kan het volgende aantal apparaten ondersteunen:  

-   25.000 totaal aantal clients en apparaten, niet langer zijn dan:  

    -   25.000 desktops (computers waarop Windows, Linux en UNIX wordt uitgevoerd)  

    -   Een van de volgende (niet beide):  

        -   10.000 apparaten die worden beheerd met behulp van de lokale MDM  

        -   10.000 apparaten met Windows CE 7.0- en Mac-clients

