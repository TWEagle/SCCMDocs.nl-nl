---
title: Sitevereisten
titleSuffix: Configuration Manager
description: Informatie over het configureren van een Windows-computer als een sitesysteemserver voor System Center Configuration Manager.
ms.custom: na
ms.date: 8/25/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 1392797b-76cb-46b4-a3e4-8f349ccaa078
caps.latest.revision: 
author: mestew
ms.author: mstewart
manager: angrobe
ms.openlocfilehash: cb1b81fc0765e6754c7dea9ce421e41fcd58a70e
ms.sourcegitcommit: b13da5ad8ffd58e3b89fa6d7170e1dec3ff130a4
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 02/01/2018
---
# <a name="site-and-site-system-prerequisites-for-system-center-configuration-manager"></a>Site- en site-systeemvereisten voor System Center Configuration Manager

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*


 Op basis van Windows-computers vereisen specifieke configuraties ter ondersteuning van hun gebruik als System Center Configuration Manager-sitesysteemservers.  

 
 Voor sommige producten, zoals Windows Server Update Services (WSUS) voor de software-updatepunt, moet u verwijzen naar de productdocumentatie om te bepalen van aanvullende vereisten en beperkingen voor het gebruik van dat product. Alleen configuraties die rechtstreeks van toepassing voor gebruik met Configuration Manager zijn hier opgenomen.   

> [!NOTE]  
>  In januari 2016 is ondersteuning voor .NET Framework 4.0, 4.5 en 4.5.1 verlopen. Zie [Veelgestelde vragen over Microsoft .NET Framework Support Lifecycle-beleid](https://support.microsoft.com/gp/framework_faq?WT.mc_id=azurebg_email_Trans_943_NET452_Update) op support.microsoft.com voor meer informatie.  

## <a name="bkmk_generalprerewq"></a>Algemene site server-vereisten en beperkingen
**De volgende van toepassing op alle sitesysteemservers:**

-   Elke sitesysteemserver moet een 64-bits besturingssysteem gebruiken. De enige uitzondering hierop is de site distributiepuntrol, die u op een 32-bits besturingssystemen installeren kunt.  

-   Sitesystemen worden niet ondersteund op de Server Core-installaties van een besturingssysteem. Een uitzondering hierop is dat Server Core-installaties worden ondersteund voor de site distributiepuntrol, zonder PXE of multicast-ondersteuning.  

-   Nadat een sitesysteemserver is geïnstalleerd, wordt het niet ondersteund als u wilt wijzigen:  

    -   De domeinnaam van het domein waarin de sitesysteemcomputer zich bevindt (ook wel een **domein rename**).  

    -   Het domeinlidmaatschap van de computer.  

    -   De naam van de computer.  

  Als u deze wijzigen moet, moet u eerst de sitesysteemrol van de computer verwijderen en de functie vervolgens opnieuw installeren nadat de wijziging aangebracht is. Als dit invloed heeft op de siteservercomputer, moet u de site verwijderen en vervolgens de site opnieuw installeren nadat de wijziging aangebracht is.  

-   Sitesysteemrollen worden niet ondersteund op een exemplaar van een Windows Server-cluster. De enige uitzondering hierop is de Sitedatabaseserver.  

-   Dit wordt niet ondersteund voor het wijzigen van het opstarttype of 'Aanmelden als' instellingen voor elke Configuration Manager-service. Als u dit doet, kunt u belangrijke services niet correct uitgevoerd.  

##  <a name="bkmk_2012Prereq"></a>Vereisten voor Windows Server 2012 en latere besturingssystemen  
###  <a name="bkmk_2012sspreq"></a>Siteserver: centrale beheersite en primaire site  
  **Windows Server-functies en onderdelen:**  

-   .NET framework 3.5 SP1 (of hoger)  

-   .NET Framework 4.5.2  

-   Externe differentiële compressie  

**Windows ADK:**  

-   Voordat u installeren of upgraden van een centrale beheersite of primaire site, moet u de versie van Windows Assessment and Deployment Kit (ADK) die de versie van Configuration Manager u installeren of upgraden naar vereist. Zie [Windows 10 ADK](/sccm/core/plan-design/configs/support-for-windows-10#windows-10-adk) in de ondersteuning voor Windows 10 als een client-onderwerp.  

-   Zie voor meer informatie over deze vereiste [vereisten voor de infrastructuur voor besturingssysteemimplementatie](/sccm/osd/plan-design/infrastructure-requirements-for-operating-system-deployment).  

**Visual C++ Redistributable:**  

-   Configuration Manager installeert het herdistribueerbare pakket voor Microsoft Visual C++ 2013 op elke computer die een siteserver wordt geïnstalleerd.  

-   Centrale beheersites en primaire sites moeten de x86- en x64 versies van het betreffende herdistribueerbare bestand.  

###  <a name="bkmk_2012secpreq"></a>Siteserver: secundaire site  
**Windows Server-functies en onderdelen:**  

-   .NET framework 3.5 SP1 (of hoger)  

-   .NET Framework 4.5.2  

-   Externe differentiële compressie  

**Visual C++ Redistributable:**  

-   Configuration Manager installeert het herdistribueerbare pakket voor Microsoft Visual C++ 2013 op elke computer die een siteserver wordt geïnstalleerd.  

-   Secundaire sites is alleen de x64 vereist versie.  

**Standaardsitesysteemrollen:**  

-   Een secundaire site installeert standaard een **beheerpunt** en een **distributiepunt**.  

-   Zorg ervoor dat de secundaire siteserver voldoet aan de vereisten voor deze sitesysteemrollen.  

###  <a name="bkmk_2012dbpreq"></a>Database-server  
**Remote Registry-service:**  

-   U moet de Remote Registry-service op de computer die als voor de sitedatabase host fungeert inschakelen tijdens de installatie van de Configuration Manager-site.  

**SQL Server:**  

-   Voordat u een centrale beheersite of primaire site installeert, moet u een ondersteunde versie van SQL Server voor het hosten van de sitedatabase installeren.  

-   Voordat u een secundaire site installeert, kunt u een ondersteunde versie van SQL Server installeren.  

-   Als u ervoor kiest om Configuration Manager SQL Server Express installeert als onderdeel van de secundaire site-installatie, zorg ervoor dat de computer voldoet aan de vereisten voor het uitvoeren van SQL Server Express.  

###  <a name="bkmk_2012smsprovpreq"></a>Server SMS-Provider  
**Windows ADK:**  

-   De computer waarop u een exemplaar van de SMS-Provider installeert, moet de vereiste versie van Windows ADK die de versie van Configuration Manager u installeren of upgraden naar nodig hebben. Zie [Windows 10 ADK](/sccm/core/plan-design/configs/support-for-windows-10#windows-10-adk) in de ondersteuning voor Windows 10 als een client-onderwerp.

-   Zie voor meer informatie over deze vereiste [vereisten voor de infrastructuur voor besturingssysteemimplementatie](/sccm/osd/plan-design/infrastructure-requirements-for-operating-system-deployment).  

###  <a name="bkmk_2012acwspreq"></a>Application Catalog-websitepunt  
**Windows Server-functies en onderdelen:**  

-   .NET framework 3.5 SP1 (of hoger)  

-   .NET Framework 4.5.2:  

    -   ASP.NET 4.5  

**IIS-configuratie:**  

-   Veelvoorkomende HTTP-functies:  

    -   Standaarddocument  

    -   Statische inhoud  

-   Toepassingsontwikkeling:  

    -   ASP.NET 3.5 (en automatisch geselecteerde opties)  

    -   ASP.NET 4.5 (en automatisch geselecteerde opties)  

    -   .NET-uitbreidbaarheid 3.5  

    -   .NET-uitbreidbaarheid 4.5  

-   Beveiliging:  

    -   Windows-verificatie  

-   Compatibiliteit met IIS 6-beheer:  

    -   Compatibiliteit met IIS 6-metabase  

###  <a name="bkmk_2012ACwsitepreq"></a>Application Catalog-webservicepunt  
**Windows Server-functies en onderdelen:**  

-   .NET framework 3.5 SP1 (of hoger)  

-   .NET Framework 4.5.2:  

    -   ASP.NET 4.5:  

        -   HTTP-activering (en automatisch geselecteerde opties)  

**IIS-configuratie:**  

-   Veelvoorkomende HTTP-functies:  

    -   Standaarddocument  

-   Compatibiliteit met IIS 6-beheer:  

    -   Compatibiliteit met IIS 6-metabase  

-   Toepassingsontwikkeling:  

    -   ASP.NET 3.5 (en automatisch geselecteerde opties)  

    -   .NET-uitbreidbaarheid 3.5  

    -   ASP.NET 4.5 (en automatisch geselecteerde opties)  

    -   .NET-uitbreidbaarheid 4.5  

**Computergeheugen:**  

-   De computer die als host fungeert voor deze sitesysteemrol moet minimaal 5% van het beschikbare geheugen van de computer gratis waarmee de sitesysteemrol voor het verwerken van aanvragen hebben.  

-   Wanneer deze sitesysteemrol CO-locaties met een andere sitesysteemrol met deze zelfde vereiste is, wordt deze geheugenvereiste voor de computer niet verhogen, maar blijft minimaal 5%.  

###  <a name="bkmk_2012AIpreq"></a>Asset Intelligence-synchronisatiepunt  
**Windows Server-functies en onderdelen:**  

-   .NET Framework 4.5.2  

###  <a name="bkmk_2012crppreq"></a>Certificaatregistratiepunt  
**Windows Server-functies en onderdelen:**  

-   .NET Framework 4.5.2:  

    -   HTTP-activering  

**IIS-configuratie:**  

-   Toepassingsontwikkeling:  

    -   ASP.NET 3.5 (en automatisch geselecteerde opties)  

    -   ASP.NET 4.5 (en automatisch geselecteerde opties)  

-   Compatibiliteit met IIS 6-beheer:  

    -   Compatibiliteit met IIS 6-metabase  

    -   Compatibiliteit met IIS 6 WMI  

###  <a name="bkmk_2012dppreq"></a>Distributiepunt  
**Windows Server-functies en onderdelen:**  

-   Externe differentiële compressie  

**IIS-configuratie:**  

-   Toepassingsontwikkeling:  

    -   ISAPI-extensies  

-   Beveiliging:  

    -   Windows-verificatie  

-   Compatibiliteit met IIS 6-beheer:  

    -   Compatibiliteit met IIS 6-metabase  

    -   Compatibiliteit met IIS 6 WMI  

**PowerShell:**  

-   Op Windows Server 2012 of hoger, PowerShell 3.0 of 4.0 is vereist voordat u het distributiepunt installeert.  

**Visual C++ Redistributable:**  

-   Configuration Manager installeert het herdistribueerbare pakket voor Microsoft Visual C++ 2013 op elke computer die als host fungeert voor een distributiepunt.  

-   De versie die is geïnstalleerd, is afhankelijk van de computer platform (x86 of x64).  

**Microsoft Azure:**  

-   U kunt een cloudservice in Microsoft Azure gebruiken om een distributiepunt te hosten.  

**Ter ondersteuning van PXE of multicast:**  

-   Installeer en configureer de Windows Deployment Services (WDS) Windows Server-rol.  

    > [!NOTE]  
    >  WDS automatisch geïnstalleerd en geconfigureerd wanneer u een distributiepunt configureert voor ondersteuning van PXE of multicast op een server waarop WindowsServer 2012 of later.  

<!--sms.503672 -Clarified BITS use-->
> [!NOTE]  
> Wanneer het distributiepunt inhoud overdraagt, wordt dit gedaan met behulp van de **Background Intelligent Transfer Service** (BITS) is ingebouwd in de Windows-besturingssysteem. De distributiepuntrol nodig niet de optionele functie BITS IIS-serveruitbreiding moet worden geïnstalleerd omdat de client heeft naar deze informatie niet uploaden.  

###  <a name="bkmk_2012EPPpreq"></a>Endpoint Protection-punt  
**Windows Server-functies en onderdelen:**  

-   .NET framework 3.5 SP1 (of hoger)  

###  <a name="bkmk_2012Enrollpreq"></a>Inschrijvingspunt  
**Windows Server-functies en onderdelen:**  

-   .NET framework 3.5 (of hoger)  

-   .NET Framework 4.5.2:  

     Wanneer deze sitesysteemrol wordt geïnstalleerd, installeert Configuration Manager automatisch .NET Framework 4.5.2. Deze installatie kunt plaatsen van de server opnieuw opstarten status in behandeling. Wanneer opnieuw opstarten is in behandeling voor de .NET Framework, .NET-toepassingen mislukken pas nadat de server opnieuw is opgestart en de installatie is voltooid.  

    -   HTTP-activering (en automatisch geselecteerde opties)  

    -   ASP.NET 4.5  


**IIS-configuratie:**  

-   Veelvoorkomende HTTP-functies:  

    -   Standaarddocument  

-   Toepassingsontwikkeling:  

    -   ASP.NET 3.5 (en automatisch geselecteerde opties)  

    -   .NET-uitbreidbaarheid 3.5  

    -   ASP.NET 4.5 (en automatisch geselecteerde opties)  

    -   .NET-uitbreidbaarheid 4.5  

-   Compatibiliteit met IIS 6-beheer:  

    -   Compatibiliteit met IIS 6-metabase  

**Computergeheugen:**  

-   De computer die als host fungeert voor deze sitesysteemrol moet minimaal 5% van het beschikbare geheugen van de computer gratis waarmee de sitesysteemrol voor het verwerken van aanvragen hebben.  

-   Wanneer deze sitesysteemrol CO-locaties met een andere sitesysteemrol met deze zelfde vereiste is, wordt deze geheugenvereiste voor de computer niet verhogen, maar blijft minimaal 5%.  

###  <a name="bkmk_2012EnrollProxpreq"></a>Proxypunt voor inschrijving  
**Windows Server-functies en onderdelen:**  

-   .NET framework 3.5 (of hoger)  

-   .NET Framework 4.5.2  

     Wanneer deze sitesysteemrol wordt geïnstalleerd, installeert Configuration Manager automatisch .NET Framework 4.5.2. Deze installatie kunt plaatsen van de server opnieuw opstarten status in behandeling. Wanneer opnieuw opstarten is in behandeling voor de .NET Framework, .NET-toepassingen mislukken pas nadat de server opnieuw is opgestart en de installatie is voltooid.  

**IIS-configuratie:**  

-   Veelvoorkomende HTTP-functies:  

    -   Standaarddocument  

    -   Statische inhoud  

-   Toepassingsontwikkeling:  

    -   ASP.NET 3.5 (en automatisch geselecteerde opties)  

    -   ASP.NET 4.5 (en automatisch geselecteerde opties)  

    -   .NET-uitbreidbaarheid 3.5  

    -   .NET-uitbreidbaarheid 4.5  

-   Beveiliging:  

    -   Windows-verificatie  

-   Compatibiliteit met IIS 6-beheer:  

    -   Compatibiliteit met IIS 6-metabase  

**Computergeheugen:**  

-   De computer die als host fungeert voor deze sitesysteemrol moet minimaal 5% van het beschikbare geheugen van de computer gratis waarmee de sitesysteemrol voor het verwerken van aanvragen hebben.  

-   Wanneer deze sitesysteemrol CO-locaties met een andere sitesysteemrol met deze zelfde vereiste is, wordt deze geheugenvereiste voor de computer niet verhogen, maar blijft minimaal 5%.  

###  <a name="bkmk_2012FSPpreq"></a>Terugvalstatuspunt  
De standaard IIS-configuratie is vereist bij de volgende toevoegingen:  

-   Compatibiliteit met IIS 6-beheer:  

    -   Compatibiliteit met IIS 6-metabase  

###  <a name="bkmk_2012MPpreq"></a>Beheerpunt  
**Windows Server-functies en onderdelen:**  

-   .NET Framework 4.5.2  

-   BITS-serveruitbreidingen (en automatisch geselecteerde opties) of Background Intelligent Transfer Services (BITS) (en automatisch geselecteerde opties)  

**IIS-configuratie:**  

-   Toepassingsontwikkeling:  

    -   ISAPI-extensies  

-   Beveiliging:  

    -   Windows-verificatie  

-   Compatibiliteit met IIS 6-beheer:  

    -   Compatibiliteit met IIS 6-metabase  

    -   Compatibiliteit met IIS 6 WMI  

###  <a name="bkmk_2012RSpoint"></a>Reporting services-punt  
**Windows Server-functies en onderdelen:**  

-   .NET Framework 4.5.2  

**SQL Server Reporting Services:**  

-   U moet installeren en configureren van ten minste één exemplaar van SQL Server voor de ondersteuning van SQL Server Reporting Services voordat de installatie van het reporting services-punt.  

-   Het exemplaar dat u voor SQL Server Reporting Services gebruikt, mag hetzelfde exemplaar die u voor de sitedatabase gebruikt.  

-   Bovendien kan het exemplaar dat u gebruikt met andere System Center-producten worden gedeeld, zolang de System Center-producten geen beperkingen voor het delen van het exemplaar van SQL Server.  

###  <a name="bkmk_SCPpreq"></a>Serviceverbindingspunt  
**Windows Server-functies en onderdelen:**  

-   .NET Framework 4.5.2  

     Wanneer deze sitesysteemrol wordt geïnstalleerd, installeert Configuration Manager automatisch .NET Framework 4.5.2. Deze installatie kunt plaatsen van de server opnieuw opstarten status in behandeling. Wanneer opnieuw opstarten is in behandeling voor de .NET Framework, .NET-toepassingen mislukken pas nadat de server opnieuw is opgestart en de installatie is voltooid.  

**Visual C++ Redistributable:**  

-   Configuration Manager installeert het herdistribueerbare pakket voor Microsoft Visual C++ 2013 op elke computer die als host fungeert voor een distributiepunt.  

-   De sitesysteemrol vereist de x64 versie.  

###  <a name="bkmk_2012SUPpreq"></a>Software-updatepunt  
**Windows Server-functies en onderdelen:**  

-   .NET framework 3.5 SP1 (of hoger)  

-   .NET Framework 4.5.2  

De standaard IIS-configuratie is vereist.

**Windows Server updateservices:**  

-   Voordat u software-updatepunt installeert, moet u de Windows-serverrol Windows Server Update Services installeren op een computer.  

-   Zie [Software-updates plannen in System Center Configuration Manager](../../../sum/plan-design/plan-for-software-updates.md) voor meer informatie.  

### <a name="state-migration-point"></a>Statusmigratiepunt  
De standaard IIS-configuratie is vereist.  

##  <a name="bkmk_2008"></a>Vereisten voor Windows Server 2008 R2 en WindowsServer 2008  
Windows Server 2008 en Windows Server 2008 R2 zijn nu uitgebreide ondersteuning en zijn niet langer in het algemeen worden ondersteund, zoals beschreven in de [Microsoft Support Lifecycle](https://support.microsoft.com/lifecycle). Zie voor meer informatie over toekomstige ondersteuning voor deze besturingssystemen als sitesysteemservers met Configuration Manager [verwijderd en afgeschafte serverbesturingssystemen](/sccm/core/plan-design/changes/deprecated/removed-and-deprecated-server#deprecated-server-operating-systems).  

**De volgende van toepassing op alle .NET Framework-vereisten:**  

-   De volledige versie van .NET Framework installeren voordat u de sitesysteemrollen installeert. Zie bijvoorbeeld de [Microsoft .NET Framework 4 (zelfstandig installatieprogramma)](http://go.microsoft.com/fwlink/p/?LinkId=193048). .NET Framework 4 Client Profile is onvoldoende voor deze vereiste.  

**De volgende van toepassing op alle activeringsvereisten van Windows Communication Foundation (WCF):**  

-   U kunt de WCF-activering configureren als onderdeel van de functie .NET Framework Windows op de sitesysteemserver. Bijvoorbeeld in Windows Server 2008 R2 uitvoeren de **Wizard Functies toevoegen** aanvullende functies te installeren op de server. Op de **onderdelen selecteren** pagina uit, vouw **.NET Framework 3.5.1-onderdelen**, vouw **WCF-activering**, en schakel vervolgens de selectievakjes voor beide **HTTP-activering** en **niet-HTTP-activering** inschakelen van deze opties.  

###  <a name="bkmk_2008sspreq"></a>Siteserver: centrale beheersite en primaire site  
**.NET Framework:**  

-   .NET framework 3.5 SP1 (of hoger)  

-   .NET Framework 4.5.2  

**Windows-onderdeel:**  

-   Externe differentiële compressie  

**Windows ADK:**  

-   Voordat u installeren of upgraden van een centrale beheersite of primaire site, moet u de versie van Windows ADK die de versie van Configuration Manager u installeren of upgraden naar vereist.  Zie [Windows 10 ADK](/sccm/core/plan-design/configs/support-for-windows-10#windows-10-adk) in de ondersteuning voor Windows 10 als een client-onderwerp.  

-   Zie voor meer informatie over deze vereiste [vereisten voor de infrastructuur voor besturingssysteemimplementatie](/sccm/osd/plan-design/infrastructure-requirements-for-operating-system-deployment).  

**Visual C++ Redistributable:**  

-   Configuration Manager installeert het herdistribueerbare pakket voor Microsoft Visual C++ 2013 op elke computer die een siteserver wordt geïnstalleerd.  

-   Centrale beheersites en primaire sites moeten de x86- en x64 versies van het betreffende herdistribueerbare bestand.  

###  <a name="bkmk_2008secpreq"></a>Siteserver: secundaire site  
**.NET Framework:**  

-   .NET framework 3.5 SP1 (of hoger)  

-   .NET Framework 4.5.2  

**Visual C++ Redistributable:**  

-   Configuration Manager installeert het herdistribueerbare pakket voor Microsoft Visual C++ 2013 op elke computer die een siteserver wordt geïnstalleerd.  

-   Secundaire sites is alleen de x64 vereist versie.  

**Standaardsitesysteemrollen:**  

-   Een secundaire site installeert standaard een **beheerpunt** en een **distributiepunt**.  

-   Zorg ervoor dat de secundaire siteserver voldoet aan de vereisten voor deze sitesysteemrollen.  

###  <a name="bkmk_2008dbpreq"></a>Database-server  
**Remote Registry-service:**  

-   U moet de Remote Registry-service op de computer die als voor de sitedatabase host fungeert inschakelen tijdens de installatie van de Configuration Manager-site.  

**SQL Server:**  

-   Voordat u een centrale beheersite of primaire site installeert, moet u een ondersteunde versie van SQL Server voor het hosten van de sitedatabase installeren.  

-   Voordat u een secundaire site installeert, kunt u een ondersteunde versie van SQL Server installeren.  

-   Als u ervoor kiest om Configuration Manager SQL Server Express installeert als onderdeel van de secundaire site-installatie, zorg ervoor dat de computer voldoet aan de vereisten voor het uitvoeren van SQL Server Express.  

###  <a name="bkmk_2008smsprovpreq"></a>Server SMS-Provider  
**Windows ADK:**  

-   De computer waarop u een exemplaar van de SMS-Provider installeert, moet de vereiste versie van Windows ADK die de versie van Configuration Manager u installeren of upgraden naar nodig hebben. Zie [Windows 10 ADK](/sccm/core/plan-design/configs/support-for-windows-10#windows-10-adk) in de ondersteuning voor Windows 10 als een client-onderwerp.  

-   Zie voor meer informatie over deze vereiste [vereisten voor de infrastructuur voor besturingssysteemimplementatie](/sccm/osd/plan-design/infrastructure-requirements-for-operating-system-deployment).  

###  <a name="bkmk_2008acwspreq"></a>Application Catalog-websitepunt  
**.NET Framework:**  

-   .NET Framework 4.5.2  

**IIS-configuratie:**

De standaard IIS-configuratie is vereist bij de volgende toevoegingen:  

-   Veelvoorkomende HTTP-functies:  

    -   Statische inhoud  

    -   Standaarddocument  

-   Toepassingsontwikkeling:  

    -   ASP.NET (en automatisch geselecteerde opties)  

         In bepaalde situaties, bijvoorbeeld wanneer IIS wordt geïnstalleerd of opnieuw wordt geconfigureerd nadat .NET Framework versie 4.5.2 is geïnstalleerd, moet u ASP.NET versie 4.5 expliciet inschakelen. Voer bijvoorbeeld op een 64-bits computer met de .NET Framework versie 4.0.30319 de volgende opdracht: **%windir%\Microsoft.NET\Framework64\v4.0.30319\aspnet_regiis.exe -i-inschakelen**  

-   Beveiliging:  

    -   Windows-verificatie  

-   Compatibiliteit met IIS 6-beheer:  

    -   Compatibiliteit met IIS 6-metabase  

###  <a name="bkmk_2008ACwsitepreq"></a>Application Catalog-webservicepunt  
**.NET Framework:**  

-   .NET framework 3.5 SP1 (of hoger)  

-   .NET Framework 4.5.2  

**Activering van Windows Communication Foundation (WCF):**  

-   HTTP-activering  

-   Niet-HTTP-activering  

**IIS-configuratie:**

De standaard IIS-configuratie is vereist bij de volgende toevoegingen:  

-   Toepassingsontwikkeling:  

    -   ASP.NET (en automatisch geselecteerde opties)  

         In bepaalde situaties, bijvoorbeeld wanneer IIS wordt geïnstalleerd of opnieuw wordt geconfigureerd nadat .NET Framework versie 4.5.2 is geïnstalleerd, moet u ASP.NET versie 4.5 expliciet inschakelen. Voer bijvoorbeeld op een 64-bits computer met de .NET Framework versie 4.0.30319 de volgende opdracht: **%windir%\Microsoft.NET\Framework64\v4.0.30319\aspnet_regiis.exe -i-inschakelen**  

-   Compatibiliteit met IIS 6-beheer:  

    -   Compatibiliteit met IIS 6-metabase  

**Computergeheugen:**  

-   De computer die als host fungeert voor deze sitesysteemrol moet minimaal 5% van het beschikbare geheugen van de computer gratis waarmee de sitesysteemrol voor het verwerken van aanvragen hebben.  

-   Wanneer deze sitesysteemrol CO-locaties met een andere sitesysteemrol met deze zelfde vereiste is, wordt deze geheugenvereiste voor de computer niet verhogen, maar blijft minimaal 5%.  

###  <a name="bkmk_2008AIpreq"></a>Asset Intelligence-synchronisatiepunt  
**.NET Framework:**  

-   .NET Framework 4.5.2  

###  <a name="bkmk_2008crppreq"></a>Certificaatregistratiepunt  
**.NET Framework:**  

-   .NET Framework 4.5.2  

-   HTTP-activering  

**IIS-configuratie:**

De standaard IIS-configuratie is vereist bij de volgende toevoegingen:  

-   Compatibiliteit met IIS 6-beheer:  

    -   Compatibiliteit met IIS 6-metabase  

    -   Compatibiliteit met IIS 6 WMI  

###  <a name="bkmk_2008dppreq"></a>Distributiepunt  
**IIS-configuratie:**

U kunt de standaard IIS-configuratie of een aangepaste configuratie gebruiken. Voor het gebruik van een aangepaste configuratie voor IIS, moet u de volgende opties voor IIS inschakelen:  

-   Toepassingsontwikkeling:  

    -   ISAPI-extensies  

-   Beveiliging:  

    -   Windows-verificatie  

-   Compatibiliteit met IIS 6-beheer:  

    -   Compatibiliteit met IIS 6-metabase  

    -   Compatibiliteit met IIS 6 WMI  

Wanneer u een aangepaste configuratie voor IIS gebruikt, kunt u de opties die niet vereist, zoals de volgende verwijderen:  

-   Veelvoorkomende HTTP-functies:  

    -   HTTP-omleiding  

-   Scripts voor IIS-beheer en hulpprogramma 's  

**Windows-onderdeel:**  

-   Externe differentiële compressie  

**Visual C++ Redistributable:**  

-   Configuration Manager installeert het herdistribueerbare pakket voor Microsoft Visual C++ 2013 op elke computer die als host fungeert voor een distributiepunt.  

-   De versie die is geïnstalleerd, is afhankelijk van de computer platform (x86 of x64).  

**Microsoft Azure:**  

-   U kunt een cloudservice in Azure gebruiken om een distributiepunt te hosten.  

**Ter ondersteuning van PXE of multicast:**  

-   Installeer en configureer de Windows Deployment Services (WDS) Windows Server-rol.  

    > [!NOTE]  
    >  WDS automatisch geïnstalleerd en geconfigureerd wanneer u een distributiepunt configureert voor ondersteuning van PXE of multicast op een server waarop WindowsServer 2012 of later.  

<!--sms.503672 -Clarified BITS use-->
> [!NOTE]  
> Wanneer het distributiepunt inhoud overdraagt, wordt dit gedaan met behulp van de **Background Intelligent Transfer Service** (BITS) is ingebouwd in de Windows-besturingssysteem. De distributiepuntrol nodig niet de optionele functie BITS IIS-serveruitbreiding moet worden geïnstalleerd omdat de client heeft naar deze informatie niet uploaden.   


###  <a name="bkmk_2008EPPpreq"></a>Endpoint Protection-punt  
**.NET Framework:**  

-   .NET framework 3.5 SP1 (of hoger)  

###  <a name="bkmk_2008Enrollpreq"></a>Inschrijvingspunt  
**.NET Framework:**  

-   .NET Framework 4.5.2  

     Wanneer deze sitesysteemrol wordt geïnstalleerd, als de server nog niet over een ondersteunde versie van .NET Framework is geïnstalleerd, installeert Configuration Manager automatisch .NET Framework 4.5.2. Deze installatie kunt plaatsen van de server opnieuw opstarten status in behandeling. Wanneer opnieuw opstarten is in behandeling voor de .NET Framework, .NET-toepassingen mislukken pas nadat de server opnieuw is opgestart en de installatie is voltooid.  

**Activering van Windows Communication Foundation (WCF):**  

-   HTTP-activering  

-   Niet-HTTP-activering  

**IIS-configuratie:**

De standaard IIS-configuratie is vereist bij de volgende toevoegingen:  

-   Toepassingsontwikkeling:  

    -   ASP.NET (en automatisch geselecteerde opties)  

         In bepaalde situaties, bijvoorbeeld wanneer IIS wordt geïnstalleerd of opnieuw wordt geconfigureerd nadat .NET Framework versie 4.5.2 is geïnstalleerd, moet u ASP.NET versie 4.5 expliciet inschakelen. Voer bijvoorbeeld op een 64-bits computer met de .NET Framework versie 4.0.30319 de volgende opdracht: **%windir%\Microsoft.NET\Framework64\v4.0.30319\aspnet_regiis.exe -i-inschakelen**  

**Computergeheugen:**  

-   De computer die als host fungeert voor deze sitesysteemrol moet minimaal 5% van het beschikbare geheugen van de computer gratis waarmee de sitesysteemrol voor het verwerken van aanvragen hebben.  

-   Wanneer deze sitesysteemrol CO-locaties met een andere sitesysteemrol met deze zelfde vereiste is, wordt deze geheugenvereiste voor de computer niet verhogen, maar blijft minimaal 5%.  

###  <a name="bkmk_2008EnrollProxpreq"></a>Proxypunt voor inschrijving  
**.NET Framework:**  

-   .NET Framework 4.5.2  

     Wanneer deze sitesysteemrol wordt geïnstalleerd, als de server nog niet over een ondersteunde versie van .NET Framework is geïnstalleerd, installeert Configuration Manager automatisch .NET Framework 4.5.2. Deze installatie kunt plaatsen van de server opnieuw opstarten status in behandeling. Wanneer opnieuw opstarten is in behandeling voor de .NET Framework, .NET-toepassingen mislukken pas nadat de server opnieuw is opgestart en de installatie is voltooid.  

**Activering van Windows Communication Foundation (WCF):**  

-   HTTP-activering  

-   Niet-HTTP-activering  

**IIS-configuratie:**

De standaard IIS-configuratie is vereist bij de volgende toevoegingen:  

-   Toepassingsontwikkeling:  

    -   ASP.NET (en automatisch geselecteerde opties)  

         In bepaalde situaties, bijvoorbeeld wanneer IIS wordt geïnstalleerd of opnieuw wordt geconfigureerd nadat .NET Framework versie 4.5.2 is geïnstalleerd, moet u ASP.NET versie 4.5 expliciet inschakelen. Voer bijvoorbeeld op een 64-bits computer met de .NET Framework versie 4.0.30319 de volgende opdracht: **%windir%\Microsoft.NET\Framework64\v4.0.30319\aspnet_regiis.exe -i-inschakelen**  

**Computergeheugen:**  

-   De computer die als host fungeert voor deze sitesysteemrol moet minimaal 5% van het beschikbare geheugen van de computer gratis waarmee de sitesysteemrol voor het verwerken van aanvragen hebben.  

-   Wanneer deze sitesysteemrol CO-locaties met een andere sitesysteemrol met deze zelfde vereiste is, wordt deze geheugenvereiste voor de computer niet verhogen, maar blijft minimaal 5%.  

###  <a name="bkmk_2008FSPpreq"></a>Terugvalstatuspunt  
**IIS-configuratie:**

De standaard IIS-configuratie is vereist bij de volgende toevoegingen:  

-   Compatibiliteit met IIS 6-beheer:  

    -   Compatibiliteit met IIS 6-metabase  

###  <a name="bkmk_2008MPpreq"></a>Beheerpunt  
**.NET Framework:**  

-   .NET Framework 4.5.2  

**IIS-configuratie:**

U kunt de standaard IIS-configuratie of een aangepaste configuratie gebruiken. Elk beheerpunt dat u inschakelt voor de ondersteuning van mobiele apparaten is de aanvullende IIS-configuratie voor ASP.NET (en de bijbehorende automatisch geselecteerde opties) vereist.

In bepaalde situaties, bijvoorbeeld wanneer IIS wordt geïnstalleerd of opnieuw wordt geconfigureerd nadat .NET Framework versie 4.5.2 is geïnstalleerd, moet u ASP.NET versie 4.5 expliciet inschakelen. Voer bijvoorbeeld op een 64-bits computer met de .NET Framework versie 4.0.30319 de volgende opdracht: **%windir%\Microsoft.NET\Framework64\v4.0.30319\aspnet_regiis.exe -i-inschakelen**  


Voor het gebruik van een aangepaste configuratie voor IIS, moet u de volgende opties voor IIS inschakelen:  

-   Toepassingsontwikkeling:  

    -   ISAPI-extensies  

-   Beveiliging:  

    -   Windows-verificatie  

-   Compatibiliteit met IIS 6-beheer:  

    -   Compatibiliteit met IIS 6-metabase  

    -   Compatibiliteit met IIS 6 WMI  


Wanneer u een aangepaste configuratie voor IIS gebruikt, kunt u de opties die niet vereist, zoals de volgende verwijderen:  

-   Veelvoorkomende HTTP-functies:  

    -   HTTP-omleiding  

-   Scripts voor IIS-beheer en hulpprogramma 's  

**Windows-onderdeel:**  

-   BITS-serveruitbreidingen (en automatisch geselecteerde opties), of Background Intelligent Transfer Services (BITS) (en automatisch geselecteerde opties)  

###  <a name="bkmk_2008RSpoint"></a>Reporting services-punt  
**.NET Framework:**  

-   .NET Framework 4.5.2  

**SQL Server Reporting Services:**  

-   U moet installeren en configureren van ten minste één exemplaar van SQL Server voor de ondersteuning van SQL Server Reporting Services voordat de installatie van het reporting services-punt.  

-   Het exemplaar dat u voor SQL Server Reporting Services gebruikt, mag hetzelfde exemplaar die u voor de sitedatabase gebruikt.  

-   Bovendien kan het exemplaar dat u gebruikt met andere System Center-producten worden gedeeld, zolang de System Center-producten geen beperkingen voor het delen van het exemplaar van SQL Server.  

###  <a name="bkmk_2008SCPpreq"></a>Serviceverbindingspunt  
**.NET Framework:**  

-   .NET Framework 4.5.2  

     Wanneer deze sitesysteemrol wordt geïnstalleerd, als de server nog niet over een ondersteunde versie van .NET Framework is geïnstalleerd, installeert Configuration Manager automatisch .NET Framework 4.5.2. Deze installatie kunt plaatsen van de server opnieuw opstarten status in behandeling. Wanneer opnieuw opstarten is in behandeling voor de .NET Framework, .NET-toepassingen mislukken pas nadat de server opnieuw is opgestart en de installatie is voltooid.  

**Visual C++ Redistributable:**  

-   Configuration Manager installeert het herdistribueerbare pakket voor Microsoft Visual C++ 2013 op elke computer die als host fungeert voor een distributiepunt.  

-   De sitesysteemrol vereist de x64 versie.  

###  <a name="bkmk_2008SUPpreq"></a>Software-updatepunt  
**.NET Framework:**  

-   .NET framework 3.5 SP1 (of hoger)  

-   .NET Framework 4.5.2  

**IIS-configuratie:**

De standaard IIS-configuratie is vereist.  

**Windows Server updateservices:**  

-   Voordat u software-updatepunt installeert, moet u de Windows-serverrol Windows Server Update Services installeren op een computer.  

-   Zie [Software-updates plannen in System Center Configuration Manager](../../../sum/plan-design/plan-for-software-updates.md) voor meer informatie.

###  <a name="bkmk_2008SMPpreq"></a>Statusmigratiepunt  
**IIS-configuratie:**

De standaard IIS-configuratie is vereist.  
