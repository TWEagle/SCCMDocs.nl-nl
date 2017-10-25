---
title: Windows-Servers voorbereiden | Microsoft Docs
description: Zorg ervoor dat een computer voldoet aan vereisten voor gebruik als een siteserver of een sitesysteemserver voor System Center Configuration Manager.
ms.custom: na
ms.date: 2/14/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: configmgr-other
ms.tgt_pltfrm: na
ms.topic: get-started-article
ms.assetid: 2aca914f-641e-4bc8-98d4-bbf0a2a5276f
caps.latest.revision: "10"
caps.handback.revision: "0"
author: Brenduns
ms.author: brenduns
manager: angrobe
ms.openlocfilehash: 9b97dedb5d2be0bd2e47260033e6e4361467dc4e
ms.sourcegitcommit: 51fc48fb023f1e8d995c6c4eacfda7dbec4d0b2f
ms.translationtype: HT
ms.contentlocale: nl-NL
ms.lasthandoff: 08/07/2017
---
# <a name="prepare-windows-servers-to-support-system-center-configuration-manager"></a>Windows-servers voorbereiden voor de ondersteuning van System Center Configuration Manager

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*

Voordat u een Windows-computer als een sitesysteemserver voor System Center Configuration Manager gebruiken kunt, de computer, moet voldoen aan de vereisten voor het beoogde gebruik als siteserver of sitesysteemserver.  

-   Deze vereisten bevatten vaak een of meer Windows-onderdelen of rollen die worden ingeschakeld met behulp van de computers van Serverbeheer.  

-   De methode voor het inschakelen van Windows-onderdelen en -rollen verschilt per besturingssysteem, Raadpleeg de documentatie voor uw besturingssysteem voor gedetailleerde informatie over het instellen van het besturingssysteem die u gebruikt.  

De informatie in dit artikel biedt een overzicht van de typen Windows-configuraties die vereist zijn ter ondersteuning van Configuration Manager-sitesystemen. Zie voor configuratiedetails voor specifieke sitesysteemrollen, [Site en site-systeemvereisten](/sccm/core/plan-design/configs/site-and-site-system-prerequisites).

##  <a name="BKMK_WinFeatures"></a>Windows-onderdelen en functies  
 Wanneer u Windows-onderdelen en functies op een computer hebt ingesteld, hoeft u mogelijk opnieuw opstarten van de computer om deze configuratie te voltooien. Het is daarom een goed idee om te identificeren van computers die specifieke sitesysteemrollen hosten zullen voordat u een Configuration Manager-site of -sitesysteemserver installeert.
### <a name="features"></a>Functies  
 De volgende Windows-onderdelen zijn vereist op bepaalde sitesysteemservers en moeten worden ingesteld voordat u een sitesysteemrol op die computer installeert.  

-   **.NET framework**: Inclusief  

    -   ASP.NET  
    -   HTTP-activering  
    -   Niet-HTTP-activering  
    -   Windows Communication Foundation (WCF) Services  

    Verschillende sitesysteemrollen vereisen verschillende versies van .NET Framework.  

    Omdat de .NET Framework 4.0 of hoger is niet achterwaarts compatibel met het vervangen van 3.5 en eerdere versies, wanneer verschillende versies als vereist worden weergegeven, plant elke versie op dezelfde computer moet inschakelen.  

-   **Background Intelligent Transfer Services (BITS)**: Beheerpunten vereisen BITS (en automatisch geselecteerde opties) voor communicatie met beheerde apparaten.  

-   **BranchCache**: Distributiepunten kunnen worden ingesteld met BranchCache ter ondersteuning van clients die BranchCache gebruiken.  

-   **Gegevensontdubbeling**: Distributiepunten kunnen worden ingesteld met en profiteren van gegevensontdubbeling.  

-   **Externe differentiële compressie (RDC)**: Elke computer die als host fungeert voor een siteserver of een distributiepunt is RDC vereist.   
    RDC wordt gebruikt voor het genereren van handtekeningen van pakketten en voor het vergelijken van handtekeningen.  

### <a name="roles"></a>Rollen  
 De volgende Windows-rollen zijn vereist ter ondersteuning van specifieke functionaliteit, zoals software-updates en implementaties van besturingssystemen, terwijl IIS is vereist voor de meest voorkomende sitesysteemrollen.  

 -   **Registratieservice** (onder Active Directory certificaatservices):  Deze Windows-rol is een vereiste voor het gebruiken van Certificaatprofielen in Configuration Manager.  

 -   **Webserver (IIS)**: Inclusief:  
    -   Veelvoorkomende HTTP-functies >  
        -   HTTP-omleiding  
    -   Toepassingsontwikkeling >  
        -   .NET-uitbreidbaarheid  
        -   ASP.NET  
        -   ISAPI-extensies  
        -   ISAPI-filters  
    -   Beheerprogramma's >  
        -   Compatibiliteit met IIS 6-beheer  
        -   Compatibiliteit met IIS 6-metabase  
        -   Compatibiliteit met IIS 6 Windows Management Instrumentation (WMI)  
    -   Beveiliging >  
        -   Filtering aanvragen  
        -   Windows-verificatie  

 De volgende sitesysteemrollen zijn een of meer van de vermelde IIS-configuraties gebruiken:  
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
 IIS gebruikt standaard Aanvraagfiltering om te blokkeren verschillende bestandsnaamextensies en maplocaties tegen toegang door HTTP of HTTPS-communicatie. Op een distributiepunt wordt hiermee voorkomen dat clients pakketten downloaden die extensies of maplocaties hebben geblokkeerd.  

 Wanneer de bronbestanden van uw pakket extensies die in IIS zijn geblokkeerd door uw configuratie van de Aanvraagfiltering, moet u instellen Aanvraagfiltering zodat ze. U doet dit door de [aanvraagfilteringsfunctie te bewerken](https://technet.microsoft.com/library/hh831621.aspx) in IIS-beheer op de distributiepuntcomputers.  

 Bovendien worden de volgende bestandsnaamextensies door Configuration Manager gebruikt voor pakketten en toepassingen. Zorg ervoor dat de configuraties voor de Aanvraagfiltering volgende bestandsextensies niet blokkeren:  

-   .PCK  
-   .PKG  
-   .STA  
-   .TAR  

Bijvoorbeeld, de bronbestanden voor een software-implementatie mogelijk een map met de naam zijn **bin** of een bestand met de **.mdb** bestandsnaamextensie.  

-   Blokkeert standaard de IIS-Aanvraagfiltering de toegang tot deze elementen (**bin** wordt geblokkeerd als een verborgen Segment en **.mdb** wordt geblokkeerd als een bestandsnaamextensie).  

-   Wanneer u de standaardconfiguratie voor IIS gebruikt voor een distributiepunt, kunnen clients die gebruikmaken van BITS deze software-implementatie niet van het distributiepunt downloaden en geven zij aan dat ze op inhoud wachten.  

-   Bewerken zodat de clients deze inhoud voor elk betreffend distributiepunt downloaden **Aanvraagfiltering** in IIS-beheer voor toegang tot de bestandsextensies en mappen die zich in de pakketten en toepassingen die u implementeert.  

> [!IMPORTANT]  
>  Wijzigingen in aanvraagfiltering kunnen de kwetsbaarheid van de computer verhogen.  
>   
>  -   Wijzigingen die u op serverniveau aanbrengt gelden voor alle websites op de server.  
> -   Wijzigingen die u in de afzonderlijke websites aanbrengt gelden alleen voor die website.  
>   
>  De aanbevolen beveiligingsprocedure is het uitvoeren van Configuration Manager op een speciale webserver. Als u andere toepassingen op de webserver uitvoeren moet, gebruikt u een aangepaste website voor Configuration Manager. Zie [Websites voor sitesysteemservers in System Center Configuration Manager](../../../core/plan-design/network/websites-for-site-system-servers.md)voor informatie.  

## <a name="http-verbs"></a>HTTP-woorden
**Beheerpunten:** Om ervoor te zorgen dat clients met een beheerpunt communiceren kunnen, op de beheerpuntserver dienen dat de volgende HTTP-termen zijn toegestaan:  
 - GET
 - POST
 - CCM_POST
 - HEAD
 - PROPFIND

**Distributiepunten:** Distributiepunten vereisen dat de volgende HTTP-termen als toegestaan:
 - GET
 - HEAD
 - PROPFIND

Zie voor meer informatie over het configureren van Aanvraagfiltering [configureren in IIS-Aanvraagfiltering](https://technet.microsoft.com/library/hh831621.aspx#Verbs) op TechNet of gelijkaardige documentatie die geldt voor de versie van Windows Server die als host fungeert voor uw beheerpunt.
