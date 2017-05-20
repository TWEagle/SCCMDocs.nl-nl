---
title: Websites voor site-systemen | Microsoft-documenten
description: Meer informatie over de standaardbeleidsregels en aangepaste websites voor systeemservers van sites in System Center Configuration Manager.
ms.custom: na
ms.date: 2/8/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: get-started-article
ms.assetid: 681f0893-e83b-476e-9ec0-a5dc7c9deeb6
caps.latest.revision: 15
caps.handback.revision: 0
author: Brenduns
ms.author: brenduns
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 26bbec1e8d6c53ce297689ba4390b9347229eb15
ms.openlocfilehash: 886ff3b8e867fc340c79648a57feae81653b0ccd
ms.contentlocale: nl-nl
ms.lasthandoff: 05/17/2017


---
# <a name="websites-for-site-system-servers-in-system-center-configuration-manager"></a>Websites voor sitesysteemservers in System Center Configuration Manager

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*

Verschillende sitesysteemrollen van Configuration Manager vereisen het gebruik van Microsoft Internet Information Services (IIS) en de standaard IIS-website voor het hosten site systeemservices gebruiken. Wanneer u andere webtoepassingen moet uitvoeren op de server en de instellingen zijn niet compatibel met Configuration Manager, kunt u overwegen een aangepaste website voor Configuration Manager.  

> [!TIP]  
>  Een aanbevolen beveiligingsprocedure is een speciale server voor de Configuration Manager-sitesystemen die IIS vereisen. Wanneer u andere toepassingen op een Configuration Manager sitesysteem uitvoert, vergroot u de kwetsbaarheid van de computer.  




##  <a name="BKMK_What2Know"></a>Wat u moet weten voordat u kiest voor aangepaste websites gebruiken  
 Sitesysteemrollen gebruiken standaard de **standaardwebsite** in IIS. Dit is ingesteld om automatisch wanneer de sitesysteemrol wordt geïnstalleerd. Op primaire sites kunt u in plaats daarvan echter kiezen voor het gebruik van aangepaste websites. Wanneer u aangepaste websites gebruikt, geldt het volgende:  

-   Aangepaste websites zijn ingeschakeld voor de gehele site in plaats van voor afzonderlijke sitesysteemservers of rollen.  

-   Aan primaire sites, elke computer die als voor een bijbehorende sitesysteemrol host fungeert moet worden ingesteld met een aangepaste website met de naam **SMSWEB**. Totdat u deze website maakt en van sitesysteemrollen op die computer instellen de aangepaste website te gebruiken, kunnen clients mogelijk niet communiceren met sitesysteemrollen op die computer.  

-   Omdat secundaire sites worden automatisch ingesteld op een aangepaste website gebruiken als hun bovenliggende primaire site te doen, moet u ook aangepaste websites in IIS maken op elke secundaire sitesysteemserver waarvoor IIS is ingesteld.  


  **Vereisten voor het gebruik van aangepaste websites:**  

 Voordat u de optie voor gebruik van aangepaste websites op een site inschakelt, moet u het volgende doen:  

-   Maak een aangepaste website met de naam **SMSWEB** in IIS op elke sitesysteemserver waarvoor IIS is vereist. Doe dat op de primaire site en op alle onderliggende secundaire sites.  

-   De aangepaste website instellen om te reageren op de poort die u voor communicatie van clients van Configuration Manager (client aangevraagde poort instelt).  

-   Voor elke aangepaste of standaardwebsite die gebruikmaakt van een aangepaste map, plaats een kopie van de standaard documenttype die u in de hoofdmap waarin de website wordt gehost. Bijvoorbeeld: op een Windows Server 2008 R2-computer met standaardconfiguraties is **iisstart.htm** is een van de verschillende standaard documenttypen die beschikbaar zijn. U kunt dit bestand vinden in de hoofdmap van de standaardwebsite en vervolgens plaats een kopie van dit bestand (of een kopie van het gebruikte standaarddocumenttype die u gebruikt) in de hoofdmap waarin de aangepaste SMSWEB-website wordt gehost. Zie voor meer informatie over Standaarddocumenttypen [standaarddocument &lt;defaultDocument\> voor IIS](http://www.iis.net/configreference/system.webserver/defaultdocument).  

**Over de vereisten voor IIS:**
**de volgende sitesysteemrollen vereisen IIS en een website die als host voor de site systeemservices:**  

-   Application Catalog-webservicepunt  

-   Application Catalog-websitepunt  

-   Distributiepunt  

-   Inschrijvingspunt  

-   Proxypunt voor inschrijving  

-   Terugvalstatuspunt  

-   Beheerpunt  

-   Software-updatepunt  

-   Statusmigratiepunt  

Aanvullende overwegingen:  

-   Wanneer een primaire site aangepaste websites ingeschakeld heeft, clients die aan die site toegewezen zijn omgeleid om te communiceren met de aangepaste websites in plaats van de standaardwebsites op de toepasselijke sitesysteemservers  

-   Als u aangepaste websites voor een primaire site gebruiken, kunt u aangepaste websites voor alle primaire sites in uw hiërarchie om ervoor te zorgen dat clients zonder problemen binnen de hiërarchie roamen kunnen. (Bij roaming wordt een clientcomputer verplaatst naar een nieuw netwerksegment dat wordt beheerd door een andere site. Roaming kan van invloed op bronnen die een client toegang lokaal in plaats van via een WAN-verbinding tot).  

-   De SMSWEB-website sitesysteemrollen die IIS gebruiken maar geen clientverbindingen, zoals het reporting services-punt accepteren ook gebruiken in plaats van de standaardwebsite.  

-   Aangepaste websites moet u de poortnummers die verschillen van de die gebruikmaakt van de computer standaardwebsite toewijzen. Een standaardwebsite en een aangepaste website kunnen niet tegelijkertijd worden uitgevoerd als beide sites proberen dezelfde TCP/IP-poorten te gebruiken.  

-   De TCP/IP-poorten die u hebt ingesteld in IIS voor de aangepaste website moeten overeenkomen met de client aangevraagde poorten voor de site.  

## <a name="switch-between-default-and-custom-websites"></a>Schakelen tussen de standaardbeleidsregels en aangepaste websites  
Hoewel u kunt controleren of schakel het selectievakje voor het gebruik van aangepaste websites op een primaire site op elk gewenst moment (op het tabblad Algemeen van de site eigenschappen is het vak), plan zorgvuldig voordat u deze wijziging aanbrengt. Wanneer deze configuratie wordt gewijzigd, moeten alle toepasselijke sitesysteemrollen op de primaire site en de onderliggende secundaire sites verwijderen en opnieuw te installeren:  

De volgende rollen **worden automatisch opnieuw geïnstalleerd**:  

-   Beheerpunt  

-   Distributiepunt  

-   Software-updatepunt  

-   Terugvalstatuspunt  

-   Statusmigratiepunt  

De volgende rollen moeten **handmatig opnieuw worden geïnstalleerd**:  

-   Application Catalog-webservicepunt  

-   Application Catalog-websitepunt  

-   Inschrijvingspunt  

-   Proxypunt voor inschrijving  

Aanvullend:  

-   Wanneer u in de standaardwebsite een aangepaste website gebruikt, wordt in Configuration Manager de oude virtuele mappen niet verwijderen. Als u verwijderen van de bestanden die Configuration Manager gebruikt wilt, moet u de virtuele mappen onder de standaardwebsite gemaakte handmatig verwijderen.  

-   Als u de site voor het gebruik van aangepaste websites wijzigt, moeten clients die al zijn toegewezen aan de site voor het gebruik van de nieuwe client aangevraagde poorten voor aangepaste websites worden geconfigureerd. Zie [client-communicatiepoorten configureren in System Center Configuration Manager](../../../core/clients/deploy/configure-client-communication-ports.md).  

## <a name="set-up-custom-websites"></a>Aangepaste websites instellen  
De stappen voor het maken van een aangepaste website verschillen per besturingssysteem. Raadpleeg voor de exacte stappen de documentatie voor de besturingssysteemversie, maar gebruik de volgende informatie wanneer dit van toepassing is:  

-   Naam van de website moet zijn: **SMSWEB**.  

-   Bij het instellen van HTTPS, moet u een SSL-certificaat opgeven voordat u de configuratie kunt opslaan.  

-   Nadat u de aangepaste website maakt, moet u de poorten voor de aangepaste website die u gebruikt verwijderen van andere websites in IIS:  

    1.  Bewerk de **bindingen** met de andere websites die moeten de poorten die overeenkomen met de verwijderen die zijn toegewezen aan de **SMSWEB** website.  

    2.  Start de **SMSWEB** website.  

    3.  Start de service **SMS_SITE_COMPONENT_MANAGER** op de siteserver van de site opnieuw op.  

