---
title: Windows-Servers voorbereiden | Microsoft-documenten
description: Zorg ervoor dat een computer voldoet aan de vereisten voor gebruik als een siteserver of een sitesysteemserver voor System Center Configuration Manager.
ms.custom: na
ms.date: 2/14/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: get-started-article
ms.assetid: 2aca914f-641e-4bc8-98d4-bbf0a2a5276f
caps.latest.revision: 10
caps.handback.revision: 0
author: Brenduns
ms.author: brenduns
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: dd102603356864add4084c6881c39bebcbd635f2
ms.openlocfilehash: 9b97dedb5d2be0bd2e47260033e6e4361467dc4e
ms.contentlocale: nl-nl
ms.lasthandoff: 05/17/2017


---
# <a name="prepare-windows-servers-to-support-system-center-configuration-manager"></a>Windows-servers voorbereiden voor de ondersteuning van System Center Configuration Manager

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*

Voordat u een Windows-computer als een sitesysteemserver voor System Center Configuration Manager kunt, moet de computer voldoen aan de vereisten voor het beoogde gebruik als een siteserver of sitesysteemserver.  

-   Deze vereisten bevatten vaak een of meer Windows-onderdelen of rollen die zijn ingeschakeld met behulp van de computers Serverbeheer.  

-   Omdat de methode voor het Windows-onderdelen en functies inschakelen van de besturingssystemen verschilt, Raadpleeg de documentatie van uw besturingssysteem voor gedetailleerde informatie over het instellen van het besturingssysteem die u gebruikt.  

De informatie in dit artikel bevat een overzicht van het type Windows-configuraties die vereist zijn ter ondersteuning van Configuration Manager site-systemen. Zie voor de configuratiegegevens voor specifieke sitesysteemrollen [Site en de systeemvereisten site](/sccm/core/plan-design/configs/site-and-site-system-prerequisites).

##  <a name="BKMK_WinFeatures"></a>Windows-onderdelen en functies  
 Bij het instellen van Windows-onderdelen en functies op een computer, dient u mogelijk opnieuw opstarten van de computer om deze configuratie te voltooien. Daarom is het een goed idee om te identificeren van computers met specifieke sitesysteemrollen voordat u een Configuration Manager-site of de sitesysteemserver installeert.
### <a name="features"></a>Functies  
 De volgende Windows-onderdelen vereist zijn op bepaalde sitesysteemservers en moeten worden ingesteld voordat u een sitesysteemrol op die computer installeert.  

-   **.NET framework**: Inclusief  

    -   ASP.NET  
    -   HTTP-activering  
    -   Niet-HTTP-activering  
    -   Windows Communication Foundation (WCF)-Services  

    Verschillende sitesysteemrollen vereisen verschillende versies van .NET Framework.  

    Omdat het .NET Framework 4.0 of hoger is niet compatibel 3.5 en oudere versies te vervangen, wanneer verschillende versies zijn opgenomen als vereist, wilt inschakelen, elke versie op dezelfde computer.  

-   **Background Intelligent Transfer Services (BITS)**: Beheerpunten vereisen BITS (en automatisch geselecteerde opties) voor communicatie met beheerde apparaten.  

-   **BranchCache**: Distributiepunten kunnen met BranchCache worden ingesteld voor de ondersteuning voor clients die BranchCache gebruiken.  

-   **Gegevensontdubbeling**: Distributiepunten kunnen worden ingesteld met en profiteren van gegevensontdubbeling.  

-   **Remote Differential Compression (RDC)**: Elke computer die als host fungeert voor een siteserver of een distributiepunt vereist RDC.   
    RDC wordt gebruikt voor het genereren van handtekeningen van pakketten en voor het vergelijken van handtekeningen.  

### <a name="roles"></a>Rollen  
 De volgende Windows-rollen zijn vereist ter ondersteuning van specifieke functionaliteit, zoals software-updates en implementaties van besturingssystemen, terwijl IIS is vereist voor de meest voorkomende sitesysteemrollen.  

 -   **Network Device Enrollment Service** (onder Active Directory Certificate Services):  Deze Windows-rol is een vereiste voor het gebruiken van Certificaatprofielen in Configuration Manager.  

 -   **Webserver (IIS)**: Met inbegrip van:  
    -   Veelvoorkomende HTTP-functies >  
        -   HTTP-omleiding  
    -   Toepassingsontwikkeling >  
        -   .NET-uitbreidbaarheid  
        -   ASP.NET  
        -   ISAPI-extensies  
        -   ISAPI-filters  
    -   Beheerhulpprogramma's >  
        -   Compatibiliteit met IIS 6-beheer  
        -   Compatibiliteit met IIS 6-metabase  
        -   Compatibiliteit met IIS 6 Windows Management Instrumentation (WMI)  
    -   Beveiliging >  
        -   Filtering aanvragen  
        -   Windows-verificatie  

 De volgende sitesysteemrollen gebruiken een of meer van de vermelde IIS-configuraties:  
    -   Application Catalog-webservicepunt  
    -   Application Catalog-websitepunt  
    -   Distributiepunt  
    -   Inschrijvingspunt  
    -   Proxypunt voor inschrijving  
    -   Terugvalstatuspunt  
    -   Beheerpunt  
    -   Software-updatepunt  
    -   Statusmigratiepunt     

    De minimumversie van IIS die is vereist, is de versie die wordt meegeleverd met het besturingssysteem van de siteserver.  

    Naast deze IIS-configuraties, moet u mogelijk instellen [IIS-Aanvraagfiltering voor distributiepunten](#BKMK_IISFiltering).  

-   **Windows Deployment Services**: Deze rol wordt gebruikt bij installatie besturingssysteem.  
-   **Windows Server updateservices**: Deze rol is vereist wanneer u software-updates gaat implementeren.  

##  <a name="BKMK_IISFiltering"></a>IIS-Aanvraagfiltering voor distributiepunten  
 IIS gebruikt standaard Aanvraagfiltering verschillende bestandsnaamextensies en maplocaties tegen toegang door HTTP of HTTPS-communicatie blokkeert. Op een distributiepunt voorkomt dit dat clients downloaden van pakketten die zijn geblokkeerd uitbreidingen of maplocaties.  

 Wanneer de bronbestanden van uw pakket extensies die door uw configuratie Aanvraagfiltering in IIS zijn geblokkeerd, moet u instellen Aanvraagfiltering zodat ze. U doet dit door de [aanvraagfilteringsfunctie te bewerken](https://technet.microsoft.com/library/hh831621.aspx) in IIS-beheer op de distributiepuntcomputers.  

 De volgende bestandsnaamextensies worden door Configuration Manager ook gebruikt voor pakketten en toepassingen. Zorg ervoor dat de configuraties van Aanvraagfiltering deze bestandsextensies niet blokkeren:  

-   .PCK  
-   .PKG  
-   .STA  
-   .TAR  

Bijvoorbeeld, de bronbestanden voor een software-implementatie advies bij een map genaamd inwinnen **bin** of een bestand met de **.mdb** bestandsnaamextensie.  

-   IIS-Aanvraagfiltering blokkeert standaard de toegang tot deze elementen (**bin** wordt geblokkeerd als een verborgen Segment en **.mdb** wordt geblokkeerd als een bestandsnaamextensie).  

-   Wanneer u de standaardconfiguratie voor IIS gebruikt voor een distributiepunt, kunnen clients die gebruikmaken van BITS deze software-implementatie niet van het distributiepunt downloaden en geven zij aan dat ze op inhoud wachten.  

-   Bewerken zodat de clients downloaden deze inhoud, op elk toepasselijk distributiepunt **Aanvraagfiltering** in IIS-beheer voor toegang tot de bestandsextensies en mappen die zich in de pakketten en toepassingen die u implementeert.  

> [!IMPORTANT]  
>  Wijzigingen in aanvraagfiltering kunnen de kwetsbaarheid van de computer verhogen.  
>   
>  -   Bewerkingen die u op serverniveau maakt gelden voor alle websites op de server.  
> -   Bewerkingen die u in afzonderlijke websites aanbrengt toepassen op alleen op deze website.  
>   
>  De aanbevolen beveiligingsprocedure is het uitvoeren van Configuration Manager op een speciale webserver. Als u andere toepassingen op de webserver uitvoeren moet, gebruikt u een aangepaste website voor Configuration Manager. Zie [Websites voor sitesysteemservers in System Center Configuration Manager](../../../core/plan-design/network/websites-for-site-system-servers.md)voor informatie.  

## <a name="http-verbs"></a>HTTP-woorden
**Beheerpunten:** Om ervoor te zorgen dat clients met een beheerpunt communiceren kunnen, op de beheerpuntserver dienen dat de volgende HTTP-woorden zijn toegestaan:  
 - GET
 - POST
 - CCM_POST
 - HEAD
 - PROPFIND

**Distributiepunten:** Distributiepunten vereisen dat de volgende HTTP-woorden als toegestaan:
 - GET
 - HEAD
 - PROPFIND

Zie voor meer informatie over het configureren van Aanvraagfiltering [configureren in IIS-Aanvraagfiltering](https://technet.microsoft.com/library/hh831621.aspx#Verbs) op TechNet of gelijkaardige documentatie die geldt voor de versie van Windows-Server die als host fungeert voor uw beheerpunt.

