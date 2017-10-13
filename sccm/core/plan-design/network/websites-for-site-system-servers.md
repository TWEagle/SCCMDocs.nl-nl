---
title: Websites voor sitesystemen | Microsoft Docs
description: Meer informatie over de standaardwebsites en aangepaste websites voor sitesysteemservers in System Center Configuration Manager.
ms.custom: na
ms.date: 2/8/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: configmgr-other
ms.tgt_pltfrm: na
ms.topic: get-started-article
ms.assetid: 681f0893-e83b-476e-9ec0-a5dc7c9deeb6
caps.latest.revision: "15"
caps.handback.revision: "0"
author: Brenduns
ms.author: brenduns
manager: angrobe
ms.openlocfilehash: 886ff3b8e867fc340c79648a57feae81653b0ccd
ms.sourcegitcommit: 51fc48fb023f1e8d995c6c4eacfda7dbec4d0b2f
ms.translationtype: HT
ms.contentlocale: nl-NL
ms.lasthandoff: 08/07/2017
---
# <a name="websites-for-site-system-servers-in-system-center-configuration-manager"></a>Websites voor sitesysteemservers in System Center Configuration Manager

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*

Verschillende sitesysteemrollen van Configuration Manager vereisen het gebruik van Microsoft Internet Information Services (IIS) en gebruiken de standaard IIS-website te hosten. Wanneer u andere webtoepassingen moet uitvoeren op de server en de instellingen zijn niet compatibel is met Configuration Manager, kunt u een aangepaste website voor Configuration Manager gebruiken.  

> [!TIP]  
>  Aanbevolen beveiligingsprocedure is een speciale server voor de Configuration Manager-sitesystemen waarvoor IIS is vereist. Wanneer u andere toepassingen op een Configuration Manager sitesysteem uitvoert, vergroot u de kwetsbaarheid voor aanvallen van die computer.  




##  <a name="BKMK_What2Know"></a>Wat u moet weten voordat u aangepaste websites gaat gebruiken  
 Sitesysteemrollen gebruiken standaard de **standaardwebsite** in IIS. Dit is ingesteld automatisch wanneer de sitesysteemrol wordt geïnstalleerd. Op primaire sites kunt u in plaats daarvan echter kiezen voor het gebruik van aangepaste websites. Wanneer u aangepaste websites gebruikt, geldt het volgende:  

-   Aangepaste websites zijn ingeschakeld voor de hele site in plaats van voor afzonderlijke sitesysteemservers of -rollen.  

-   Op primaire sites moet elke computer die als voor een bijbehorende sitesysteemrol host fungeert worden ingesteld met een aangepaste website met de naam **SMSWEB**. Totdat u deze website maakt en sitesysteemrollen op die computer instellen voor gebruik van de aangepaste website, kunnen clients mogelijk niet communiceren met sitesysteemrollen op die computer.  

-   Omdat secundaire sites worden automatisch ingesteld op een aangepaste website gebruiken wanneer hun bovenliggende primaire site om dit te doen, moet u ook aangepaste websites in IIS maken op elke secundaire sitesysteemserver waarvoor IIS is ingesteld.  


  **Vereisten voor het gebruik van aangepaste websites:**  

 Voordat u de optie voor gebruik van aangepaste websites op een site inschakelt, moet u het volgende doen:  

-   Maak een aangepaste website met de naam **SMSWEB** in IIS op elke sitesysteemserver waarvoor IIS is vereist. Doe dat op de primaire site en op alle onderliggende secundaire sites.  

-   De aangepaste website instellen om te reageren op dezelfde poort die u hebt ingesteld voor Configuration Manager-clientcommunicatie (poort voor clientaanvragen).  

-   Voor elke aangepaste of standaardwebsite die gebruikmaakt van een aangepaste map, plaats een kopie van het standaarddocumenttype dat u gebruikt in de hoofdmap waarin de website wordt gehost. Bijvoorbeeld: op een Windows Server 2008 R2-computer met standaardconfiguraties is **iisstart.htm** is een van de verschillende standaard documenttypen die beschikbaar zijn. U kunt dit bestand vinden in de hoofdmap van de standaardwebsite en plaats vervolgens een kopie van dit bestand (of een kopie van het standaarddocumenttype dat u gebruikt) in de hoofdmap waarin de aangepaste SMSWEB-website. Zie voor meer informatie over Standaarddocumenttypen [standaarddocument &lt;defaultDocument\> voor IIS](http://www.iis.net/configreference/system.webserver/defaultdocument).  

**Over de vereisten voor IIS:**
**de volgende sitesysteemrollen vereisen IIS en een website die als host voor de sitesysteemserver:**  

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

-   Wanneer een primaire site aangepaste websites zijn ingeschakeld, worden clients die zijn toegewezen aan die site omgeleid om te communiceren met de aangepaste websites in plaats van de standaardwebsites op de betreffende sitesysteemservers  

-   Als u aangepaste websites voor één primaire site gebruikt, kunt u aangepaste websites voor alle primaire sites in uw hiërarchie om ervoor te zorgen dat clients zonder problemen binnen de hiërarchie roamen kunnen. (Bij roaming wordt een clientcomputer verplaatst naar een nieuw netwerksegment dat wordt beheerd door een andere site. Roaming kan van invloed op bronnen die een client lokaal toegang in plaats van via een WAN-verbinding hebben kan).  

-   Sitesysteemrollen die IIS gebruiken maar geen clientverbindingen, zoals het reporting servicepunt accepteren gebruik van de SMSWEB-website in plaats van de standaardwebsite.  

-   Aangepaste websites moet u poortnummers toewijzen die afwijken van de door de standaardwebsite van de computer maakt gebruik van poorten. Een standaardwebsite en een aangepaste website kunnen niet tegelijkertijd worden uitgevoerd als beide sites proberen dezelfde TCP/IP-poorten te gebruiken.  

-   De TCP/IP-poorten die u hebt ingesteld in IIS voor de aangepaste website moeten overeenkomen met de client aangevraagde poorten voor de site.  

## <a name="switch-between-default-and-custom-websites"></a>Schakelen tussen standaardwebsites en aangepaste websites  
Maar u kunt controleren of schakel het selectievakje uit voor het gebruik van aangepaste websites op een primaire site op elk gewenst moment (het vak is op het tabblad Algemeen van de site eigenschappen), plan zorgvuldig voordat u deze wijziging aanbrengt. Wanneer deze configuratie wordt gewijzigd, moeten alle betreffende sitesysteemrollen op de primaire site en de onderliggende secundaire sites verwijderen en opnieuw installeren:  

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

-   Wanneer u van de standaardwebsite overschakelt naar een aangepaste website gebruikt, wordt in Configuration Manager de oude virtuele mappen niet verwijderen. Als u verwijderen van de bestanden die Configuration Manager gebruikt wilt, moet u de onder de standaardwebsite gemaakte virtuele mappen handmatig verwijderen.  

-   Als u de site voor het gebruik van aangepaste websites wijzigt, clients die al zijn toegewezen aan de site moeten vervolgens opnieuw worden geconfigureerd voor het gebruik van de nieuwe client aangevraagde poorten voor de aangepaste websites. Zie [clientcommunicatiepoorten in System Center Configuration Manager configureren](../../../core/clients/deploy/configure-client-communication-ports.md).  

## <a name="set-up-custom-websites"></a>Aangepaste websites instellen  
De stappen voor het maken van een aangepaste website verschillen per besturingssysteem. Raadpleeg voor de exacte stappen de documentatie voor de besturingssysteemversie, maar gebruik de volgende informatie wanneer dit van toepassing is:  

-   De naam van de website moet zijn: **SMSWEB**.  

-   Bij het instellen van HTTPS, moet u een SSL-certificaat opgeven voordat u de configuratie kunt opslaan.  

-   Nadat u de aangepaste website hebt gemaakt, verwijdert u de aangepaste website-poorten die u gebruikt van andere websites in IIS:  

    1.  Bewerk de **bindingen** van de andere websites om poorten die overeenkomen met de te verwijderen die zijn toegewezen aan de **SMSWEB** website.  

    2.  Start de **SMSWEB** website.  

    3.  Start de service **SMS_SITE_COMPONENT_MANAGER** op de siteserver van de site opnieuw op.  
