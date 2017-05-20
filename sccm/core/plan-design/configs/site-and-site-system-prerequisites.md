---
title: Site-vereisten | Microsoft-documenten
description: Informatie over het configureren van een Windows-computer als een sitesysteemserver van System Center Configuration Manager.
ms.custom: na
ms.date: 1/17/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 1392797b-76cb-46b4-a3e4-8f349ccaa078
caps.latest.revision: 5
author: Brenduns
ms.author: brenduns
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 42549b98dd7f418cc3f4543198aaeb90ea8a3efd
ms.openlocfilehash: 0b1d2d619d6cdaf36cc22ef461ea1505b5cacc41
ms.contentlocale: nl-nl
ms.lasthandoff: 05/17/2017

---
# <a name="site-and-site-system-prerequisites-for-system-center-configuration-manager"></a>Site- en site-systeemvereisten voor System Center Configuration Manager

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*


 Windows-gebaseerde computers vereisen een specifieke configuraties om hun gebruik als System Center Configuration Manager-sitesysteemservers.  


 Voor sommige producten, zoals Windows Server Update Services (WSUS) voor de software-updatepunt, moet u om te verwijzen naar de productdocumentatie om te identificeren van aanvullende vereisten en beperkingen voor het gebruik van dat product. Alleen configuraties die van toepassing zijn voor gebruik met Configuration Manager rechtstreeks zijn hier opgenomen.   

> [!NOTE]  
>  In januari 2016 verlopen ondersteuning voor .NET Framework 4.0, 4.5 en 4.5.1. Zie [Veelgestelde vragen over Microsoft .NET Framework Support Lifecycle-beleid](https://support.microsoft.com/gp/framework_faq?WT.mc_id=azurebg_email_Trans_943_NET452_Update) op support.microsoft.com voor meer informatie.  

## <a name="bkmk_generalprerewq"></a>Algemene site server-vereisten en beperkingen
**De volgende van toepassing op alle sitesysteemservers:**

-   Elke sitesysteemserver moet een 64-bits besturingssysteem gebruiken. De enige uitzondering hierop is het systeem distributiepuntsiterollen, die u op een 32-bits besturingssystemen installeren kunt.  

-   Site-systemen worden niet ondersteund op de Server Core-installaties van een besturingssysteem. Een uitzondering hierop is dat de Server Core-installaties worden ondersteund voor het systeem distributiepuntsiterollen, zonder PXE of multicast-ondersteuning.  

-   Nadat u een sitesysteemserver hebt geïnstalleerd, wordt het niet ondersteund als u wilt wijzigen:  

    -   De domeinnaam van het domein waar de computer van het sitesysteem zich bevindt (ook wel genoemd een **rename domain**).  

    -   Het domeinlidmaatschap van de computer.  

    -   De naam van de computer.  

  Als u deze wijzigen moet, moet u eerst de sitesysteemrol van de computer te verwijderen en opnieuw installeren van de rol nadat de wijziging voltooid is. Als dit invloed heeft op de site server-computer, moet u de site verwijderen en vervolgens de site opnieuw installeren nadat de wijziging voltooid is.  

-   Sitesysteemrollen worden niet ondersteund voor een exemplaar van een Windows Server-cluster. De enige uitzondering hierop is de Sitedatabaseserver.  

-   Het wordt niet ondersteund voor het opstarttype wijzigen of "Aanmelden als"-instellingen voor alle Configuration Manager-service. Als u dit doet u mogelijk te voorkomen dat belangrijke services juist worden uitgevoerd.  

##  <a name="bkmk_2012Prereq"></a>Vereisten voor Windows Server 2012 en latere besturingssystemen  
###  <a name="bkmk_2012sspreq"></a>Siteserver: centrale beheersite en primaire site  
  **Windows Server-rollen en functies:**  

-   .NET framework 3.5 SP1 (of hoger)  

-   .NET framework 4.5.2  

-   Externe differentiële compressie  

**Windows ADK:**  

-   Voordat u installeren of upgraden van een centrale beheersite of primaire site, moet u de versie van Windows Assessment and Deployment Kit (ADK) waarvoor de versie van Configuration Manager u installeren of upgraden om te installeren.  

    -   De 1511-versie van Configuration Manager vereist dat de Windows 10 RTM (10.0.10240) versie van Windows ADK.  

-   Zie voor meer informatie over deze vereiste [vereisten voor de infrastructuur voor implementatie van besturingssysteem](/sccm/osd/plan-design/infrastructure-requirements-for-operating-system-deployment).  

**Te distribueren pakket Visual C++:**  

-   Configuration Manager installeert het herdistrueerbare pakket voor Microsoft Visual C++ 2013 op elke computer die een siteserver installeert.  

-   Centrale beheersites en primaire sites moeten de x86 en x64 versies van het herdistribueerbare bestand van toepassing.  

###  <a name="bkmk_2012secpreq"></a>Siteserver: secundaire site  
**Windows Server-rollen en functies:**  

-   .NET framework 3.5 SP1 (of hoger)  

-   .NET framework 4.5.2  

-   Externe differentiële compressie  

**Te distribueren pakket Visual C++:**  

-   Configuration Manager installeert het herdistrueerbare pakket voor Microsoft Visual C++ 2013 op elke computer die een siteserver installeert.  

-   Vereisen secundaire sites alleen de x64 versie.  

**Standaardsitesysteemrollen:**  

-   Een secundaire site installeert standaard een **beheerpunt** en een **distributiepunt**.  

-   Zorg ervoor dat de secundaire siteserver voldoet aan de vereisten voor deze sitesysteemrollen.  

###  <a name="bkmk_2012dbpreq"></a>Databaseserver  
**Remote Registry-service:**  

-   U moet de Remote Registry-service op de computer die als voor de sitedatabase host fungeert inschakelen tijdens de installatie van de Configuration Manager-site.  

**SQL Server:**  

-   Voordat u een centrale beheersite of primaire site installeert, moet u een ondersteunde versie van SQL Server als host voor de sitedatabase installeren.  

-   Voordat u een secundaire site installeert, kunt u een ondersteunde versie van SQL Server installeren.  

-   Als u Configuration Manager SQL Server Express installeert als onderdeel van de secundaire site-installatie, zorg ervoor dat de computer voldoet aan de vereisten voor het uitvoeren van SQL Server Express.  

###  <a name="bkmk_2012smsprovpreq"></a>SMS-Provider server  
**Windows ADK:**  

-   De computer waarop u een exemplaar van de SMS-Provider installeert, moet de vereiste versie van Windows ADK waarvoor de versie van Configuration Manager u installeren of upgraden naar hebben.  

    -   De 1511-versie van Configuration Manager vereist dat de Windows 10 RTM (10.0.10240) versie van Windows ADK.  

-   Zie voor meer informatie over deze vereiste [vereisten voor de infrastructuur voor implementatie van besturingssysteem](/sccm/osd/plan-design/infrastructure-requirements-for-operating-system-deployment).  

###  <a name="bkmk_2012acwspreq"></a>Application Catalog-websitepunt  
**Windows Server-rollen en functies:**  

-   .NET framework 3.5 SP1 (of hoger)  

-   .NET framework 4.5.2:  

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
**Windows Server-rollen en functies:**  

-   .NET framework 3.5 SP1 (of hoger)  

-   .NET framework 4.5.2:  

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

**Het geheugen van de computer:**  

-   De computer die fungeert als host voor deze sitesysteemrol moet minimaal 5% van de computer beschikbaar geheugen vrij waarmee de sitesysteemrol voor het verwerken van aanvragen.  

-   Wanneer deze sitesysteemrol CO-locaties met een andere sitesysteemrol waarvoor deze dezelfde vereiste is, is deze geheugenvereiste voor de computer niet vergroten, maar blijft minimaal 5%.  

###  <a name="bkmk_2012AIpreq"></a>Asset Intelligence-synchronisatiepunt  
**Windows Server-rollen en functies:**  

-   .NET framework 4.5.2  

###  <a name="bkmk_2012crppreq"></a>Certificaatregistratiepunt  
**Windows Server-rollen en functies:**  

-   .NET framework 4.5.2:  

    -   HTTP-activering  

**IIS-configuratie:**  

-   Toepassingsontwikkeling:  

    -   ASP.NET 3.5 (en automatisch geselecteerde opties)  

    -   ASP.NET 4.5 (en automatisch geselecteerde opties)  

-   Compatibiliteit met IIS 6-beheer:  

    -   Compatibiliteit met IIS 6-metabase  

    -   Compatibiliteit met IIS 6 WMI  

###  <a name="bkmk_2012dppreq"></a>Distributiepunt  
**Windows Server-rollen en functies:**  

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

**Te distribueren pakket Visual C++:**  

-   Op elke computer die als host fungeert voor een distributiepunt installeert Configuration Manager het herdistrueerbare pakket voor Microsoft Visual C++ 2013.  

-   De versie die is geïnstalleerd, is afhankelijk van de computer platform (x86 of x64).  

**Microsoft Azure:**  

-   U kunt een cloudservice in Microsoft Azure gebruiken om een distributiepunt te hosten.  

**Ter ondersteuning van PXE of multicast:**  

-   Installeer en configureer de Windows Deployment Services (WDS) Windows Server-rol.  

    > [!NOTE]  
    >  WDS installeert en configureert automatisch wanneer u een distributiepunt configureert voor ondersteuning van PXE of multicast op een server met WindowsServer 2012 of later.  

> [!NOTE]  
> Systeem distributiepuntsiterollen vereist geen Background Intelligent Transfer Service (BITS). Wanneer BITS is geconfigureerd op de distributiepuntcomputer, wordt niet BITS op de distributiepuntcomputer gebruikt om het downloaden van inhoud door clients die BITS gebruiken.  

###  <a name="bkmk_2012EPPpreq"></a>Endpoint Protection-punt  
**Windows Server-rollen en functies:**  

-   .NET framework 3.5 SP1 (of hoger)  

###  <a name="bkmk_2012Enrollpreq"></a>Inschrijvingspunt  
**Windows Server-rollen en functies:**  

-   .NET framework 3.5 (of hoger)  

-   .NET framework 4.5.2:  

     Wanneer deze sitesysteemrol wordt geïnstalleerd, installeert Configuration Manager automatisch de .NET Framework 4.5.2. Deze installatie kan de server plaats in de status in behandeling opnieuw worden opgestart. Wanneer een opnieuw opstarten in behandeling is voor de .NET Framework, .NET-toepassingen mogelijk mislukken totdat er nadat de server opnieuw wordt opgestart en de installatie is voltooid.  

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

**Het geheugen van de computer:**  

-   De computer die fungeert als host voor deze sitesysteemrol moet minimaal 5% van de computer beschikbaar geheugen vrij waarmee de sitesysteemrol voor het verwerken van aanvragen.  

-   Wanneer deze sitesysteemrol CO-locaties met een andere sitesysteemrol waarvoor deze dezelfde vereiste is, is deze geheugenvereiste voor de computer niet vergroten, maar blijft minimaal 5%.  

###  <a name="bkmk_2012EnrollProxpreq"></a>Proxypunt voor inschrijving  
**Windows Server-rollen en functies:**  

-   .NET framework 3.5 (of hoger)  

-   .NET framework 4.5.2  

     Wanneer deze sitesysteemrol wordt geïnstalleerd, installeert Configuration Manager automatisch de .NET Framework 4.5.2. Deze installatie kan de server plaats in de status in behandeling opnieuw worden opgestart. Wanneer een opnieuw opstarten in behandeling is voor de .NET Framework, .NET-toepassingen mogelijk mislukken totdat er nadat de server opnieuw wordt opgestart en de installatie is voltooid.  

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

**Het geheugen van de computer:**  

-   De computer die fungeert als host voor deze sitesysteemrol moet minimaal 5% van de computer beschikbaar geheugen vrij waarmee de sitesysteemrol voor het verwerken van aanvragen.  

-   Wanneer deze sitesysteemrol CO-locaties met een andere sitesysteemrol waarvoor deze dezelfde vereiste is, is deze geheugenvereiste voor de computer niet vergroten, maar blijft minimaal 5%.  

###  <a name="bkmk_2012FSPpreq"></a>Terugvalstatuspunt  
De standaard IIS-configuratie is vereist bij de volgende toevoegingen:  

-   Compatibiliteit met IIS 6-beheer:  

    -   Compatibiliteit met IIS 6-metabase  

###  <a name="bkmk_2012MPpreq"></a>Beheerpunt  
**Windows Server-rollen en functies:**  

-   .NET framework 4.5.2  

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
**Windows Server-rollen en functies:**  

-   .NET framework 4.5.2  

**SQL Server Reporting Services:**  

-   U moet installeren en configureren van ten minste één exemplaar van SQL Server voor de ondersteuning van SQL Server Reporting Services voordat de installatie van het reporting services-punt.  

-   Het exemplaar dat u voor SQL Server Reporting Services gebruikt kunt u voor de sitedatabase gebruiken hetzelfde exemplaar zijn.  

-   Daarnaast kan het exemplaar dat u gebruikt worden gedeeld met andere System Center-producten, zolang de System Center-producten geen beperkingen voor het delen van het exemplaar van SQL Server.  

###  <a name="bkmk_SCPpreq"></a>Het service connection point  
**Windows Server-rollen en functies:**  

-   .NET framework 4.5.2  

     Wanneer deze sitesysteemrol wordt geïnstalleerd, installeert Configuration Manager automatisch de .NET Framework 4.5.2. Deze installatie kan de server plaats in de status in behandeling opnieuw worden opgestart. Wanneer een opnieuw opstarten in behandeling is voor de .NET Framework, .NET-toepassingen mogelijk mislukken totdat er nadat de server opnieuw wordt opgestart en de installatie is voltooid.  

**Te distribueren pakket Visual C++:**  

-   Op elke computer die als host fungeert voor een distributiepunt installeert Configuration Manager het herdistrueerbare pakket voor Microsoft Visual C++ 2013.  

-   De sitesysteemrol is vereist voor de x64 versie.  

###  <a name="bkmk_2012SUPpreq"></a>Software-updatepunt  
**Windows Server-rollen en functies:**  

-   .NET framework 3.5 SP1 (of hoger)  

-   .NET framework 4.5.2  

De standaard IIS-configuratie is vereist.

**Windows Server updateservices:**  

-   Voordat u een softwareupdate-punt installeert, moet u de Windows-serverrol Windows Server Update Services installeren op een computer.  

-   Zie [Software-updates plannen in System Center Configuration Manager](../../../sum/plan-design/plan-for-software-updates.md) voor meer informatie.  

### <a name="state-migration-point"></a>Statusmigratiepunt  
De standaard IIS-configuratie is vereist.  

##  <a name="bkmk_2008"></a>Vereisten voor Windows Server 2008 R2 en WindowsServer 2008  
Windows Server 2008 en Windows Server 2008 R2 nu vallen onder uitgebreide ondersteuning en zijn niet langer in algemene ondersteuning, zoals beschreven door de [Microsoft Support Lifecycle](https://support.microsoft.com/lifecycle). Zie voor meer informatie over toekomstige ondersteuning voor deze besturingssystemen als sitesysteemservers met Configuration Manager [verwijderd en afgeschaft onderdelen voor System Center Configuration Manager](../../../core/plan-design/changes/removed-and-deprecated-features.md).  

**De volgende van toepassing op alle .NET Framework-vereisten:**  

-   De volledige versie van .NET Framework installeren voordat u de sitesysteemrollen installeert. Bijvoorbeeld, Zie de [Microsoft .NET Framework 4 (zelfstandige installatieprogramma)](http://go.microsoft.com/fwlink/p/?LinkId=193048). .NET Framework 4 clientprofiel is onvoldoende voor deze vereiste.  

**De volgende van toepassing op alle Windows Communication Foundation (WCF) activering vereisten:**  

-   WCF-activering kunt u als onderdeel van de functie .NET Framework Windows op de sitesysteemserver. Voer bijvoorbeeld op Windows Server 2008 R2 het **Wizard Functies toevoegen** aanvullende functies te installeren op de server. Op de **functies selecteren** pagina uit, vouw **NET Framework 3.5.1 functies**, vouw **WCF-activering**, en vervolgens de selectievakjes voor beide **HTTP-activering** en **niet-HTTP-activering** waarmee deze opties.  

###  <a name="bkmk_2008sspreq"></a>Siteserver: centrale beheersite en primaire site  
**.NET framework:**  

-   .NET framework 3.5 SP1 (of hoger)  

-   .NET framework 4.5.2  

**Windows-functie:**  

-   Externe differentiële compressie  

**Windows ADK:**  

-   Voordat u installeren of upgraden van een centrale beheersite of primaire site, moet u de versie van Windows ADK waarvoor de versie van Configuration Manager u installeren of upgraden om te installeren.  

    -   De 1511-versie van Configuration Manager vereist dat de Windows 10 RTM (10.0.10240) versie van Windows ADK.  

-   Zie voor meer informatie over deze vereiste [vereisten voor de infrastructuur voor implementatie van besturingssysteem](/sccm/osd/plan-design/infrastructure-requirements-for-operating-system-deployment).  

**Te distribueren pakket Visual C++:**  

-   Configuration Manager installeert het herdistrueerbare pakket voor Microsoft Visual C++ 2013 op elke computer die een siteserver installeert.  

-   Centrale beheersites en primaire sites moeten de x86 en x64 versies van het herdistribueerbare bestand van toepassing.  

###  <a name="bkmk_2008secpreq"></a>Siteserver: secundaire site  
**.NET framework:**  

-   .NET framework 3.5 SP1 (of hoger)  

-   .NET framework 4.5.2  

**Te distribueren pakket Visual C++:**  

-   Configuration Manager installeert het herdistrueerbare pakket voor Microsoft Visual C++ 2013 op elke computer die een siteserver installeert.  

-   Vereisen secundaire sites alleen de x64 versie.  

**Standaardsitesysteemrollen:**  

-   Een secundaire site installeert standaard een **beheerpunt** en een **distributiepunt**.  

-   Zorg ervoor dat de secundaire siteserver voldoet aan de vereisten voor deze sitesysteemrollen.  

###  <a name="bkmk_2008dbpreq"></a>Databaseserver  
**Remote Registry-service:**  

-   U moet de Remote Registry-service op de computer die als voor de sitedatabase host fungeert inschakelen tijdens de installatie van de Configuration Manager-site.  

**SQL Server:**  

-   Voordat u een centrale beheersite of primaire site installeert, moet u een ondersteunde versie van SQL Server als host voor de sitedatabase installeren.  

-   Voordat u een secundaire site installeert, kunt u een ondersteunde versie van SQL Server installeren.  

-   Als u Configuration Manager SQL Server Express installeert als onderdeel van de secundaire site-installatie, zorg ervoor dat de computer voldoet aan de vereisten voor het uitvoeren van SQL Server Express.  

###  <a name="bkmk_2008smsprovpreq"></a>SMS-Provider server  
**Windows ADK:**  

-   De computer waarop u een exemplaar van de SMS-Provider installeert, moet de vereiste versie van Windows ADK waarvoor de versie van Configuration Manager u installeren of upgraden naar hebben.  

    -   De 1511-versie van Configuration Manager vereist dat de Windows 10 RTM (10.0.10240) versie van Windows ADK.  

-   Zie voor meer informatie over deze vereiste [vereisten voor de infrastructuur voor implementatie van besturingssysteem](/sccm/osd/plan-design/infrastructure-requirements-for-operating-system-deployment).  

###  <a name="bkmk_2008acwspreq"></a>Application Catalog-websitepunt  
**.NET framework:**  

-   .NET framework 4.5.2  

**IIS-configuratie:**

De standaard IIS-configuratie is vereist bij de volgende toevoegingen:  

-   Veelvoorkomende HTTP-functies:  

    -   Statische inhoud  

    -   Standaarddocument  

-   Toepassingsontwikkeling:  

    -   ASP.NET (en automatisch geselecteerde opties)  

         In sommige scenario's, zoals wanneer IIS is geïnstalleerd of geconfigureerd als .NET Framework 4.5.2 versie is geïnstalleerd, moet u ASP.NET versie 4.5 expliciet inschakelen. Bijvoorbeeld, op een 64-bits computer met de .NET Framework versie 4.0.30319, voer de volgende opdracht: **%windir%\Microsoft.NET\Framework64\v4.0.30319\aspnet_regiis.exe -i-inschakelen**  

-   Beveiliging:  

    -   Windows-verificatie  

-   Compatibiliteit met IIS 6-beheer:  

    -   Compatibiliteit met IIS 6-metabase  

###  <a name="bkmk_2008ACwsitepreq"></a>Application Catalog-webservicepunt  
**.NET framework:**  

-   .NET framework 3.5 SP1 (of hoger)  

-   .NET framework 4.5.2  

**Windows Communication Foundation (WCF) activation:**  

-   HTTP-activering  

-   Niet-HTTP-activering  

**IIS-configuratie:**

De standaard IIS-configuratie is vereist bij de volgende toevoegingen:  

-   Toepassingsontwikkeling:  

    -   ASP.NET (en automatisch geselecteerde opties)  

         In sommige scenario's, zoals wanneer IIS is geïnstalleerd of geconfigureerd als .NET Framework 4.5.2 versie is geïnstalleerd, moet u ASP.NET versie 4.5 expliciet inschakelen. Bijvoorbeeld, op een 64-bits computer met de .NET Framework versie 4.0.30319, voer de volgende opdracht: **%windir%\Microsoft.NET\Framework64\v4.0.30319\aspnet_regiis.exe -i-inschakelen**  

-   Compatibiliteit met IIS 6-beheer:  

    -   Compatibiliteit met IIS 6-metabase  

**Het geheugen van de computer:**  

-   De computer die fungeert als host voor deze sitesysteemrol moet minimaal 5% van de computer beschikbaar geheugen vrij waarmee de sitesysteemrol voor het verwerken van aanvragen.  

-   Wanneer deze sitesysteemrol CO-locaties met een andere sitesysteemrol waarvoor deze dezelfde vereiste is, is deze geheugenvereiste voor de computer niet vergroten, maar blijft minimaal 5%.  

###  <a name="bkmk_2008AIpreq"></a>Asset Intelligence-synchronisatiepunt  
**.NET framework:**  

-   .NET framework 4.5.2  

###  <a name="bkmk_2008crppreq"></a>Certificaatregistratiepunt  
**.NET framework:**  

-   .NET framework 4.5.2  

-   HTTP-activering  

**IIS-configuratie:**

De standaard IIS-configuratie is vereist bij de volgende toevoegingen:  

-   Compatibiliteit met IIS 6-beheer:  

    -   Compatibiliteit met IIS 6-metabase  

    -   Compatibiliteit met IIS 6 WMI  

###  <a name="bkmk_2008dppreq"></a>Distributiepunt  
**IIS-configuratie:**

U kunt de standaard IIS-configuratie of een aangepaste configuratie gebruiken. U moet de volgende opties voor IIS inschakelen voor het gebruik van een aangepaste IIS-configuratie:  

-   Toepassingsontwikkeling:  

    -   ISAPI-extensies  

-   Beveiliging:  

    -   Windows-verificatie  

-   Compatibiliteit met IIS 6-beheer:  

    -   Compatibiliteit met IIS 6-metabase  

    -   Compatibiliteit met IIS 6 WMI  

Wanneer u een aangepaste IIS-configuratie gebruikt, kunt u de opties die vereist is, zoals het volgende niet verwijderen:  

-   Veelvoorkomende HTTP-functies:  

    -   HTTP-omleiding  

-   IIS Management Scripts en hulpprogramma 's  

**Windows-functie:**  

-   Externe differentiële compressie  

**Te distribueren pakket Visual C++:**  

-   Op elke computer die als host fungeert voor een distributiepunt installeert Configuration Manager het herdistrueerbare pakket voor Microsoft Visual C++ 2013.  

-   De versie die is geïnstalleerd, is afhankelijk van de computer platform (x86 of x64).  

**Microsoft Azure:**  

-   U kunt een cloudservice in Azure gebruiken om een distributiepunt te hosten.  

**Ter ondersteuning van PXE of multicast:**  

-   Installeer en configureer de Windows Deployment Services (WDS) Windows Server-rol.  

    > [!NOTE]  
    >  WDS installeert en configureert automatisch wanneer u een distributiepunt configureert voor ondersteuning van PXE of multicast op een server met WindowsServer 2012 of later.  

> [!NOTE]  
> Systeem distributiepuntsiterollen vereist geen Background Intelligent Transfer Service (BITS). Wanneer BITS is geconfigureerd op de distributiepuntcomputer, wordt niet BITS op de distributiepuntcomputer gebruikt om het downloaden van inhoud door clients die BITS gebruiken.  


###  <a name="bkmk_2008EPPpreq"></a>Endpoint Protection-punt  
**.NET framework:**  

-   .NET framework 3.5 SP1 (of hoger)  

###  <a name="bkmk_2008Enrollpreq"></a>Inschrijvingspunt  
**.NET framework:**  

-   .NET framework 4.5.2  

     Wanneer deze sitesysteemrol wordt geïnstalleerd als de server nog niet over een ondersteunde versie van .NET Framework is geïnstalleerd, installeert Configuration Manager automatisch de .NET Framework 4.5.2. Deze installatie kan de server plaats in de status in behandeling opnieuw worden opgestart. Wanneer een opnieuw opstarten in behandeling is voor de .NET Framework, .NET-toepassingen mogelijk mislukken totdat er nadat de server opnieuw wordt opgestart en de installatie is voltooid.  

**Windows Communication Foundation (WCF) activation:**  

-   HTTP-activering  

-   Niet-HTTP-activering  

**IIS-configuratie:**

De standaard IIS-configuratie is vereist bij de volgende toevoegingen:  

-   Toepassingsontwikkeling:  

    -   ASP.NET (en automatisch geselecteerde opties)  

         In sommige scenario's, zoals wanneer IIS is geïnstalleerd of geconfigureerd als .NET Framework 4.5.2 versie is geïnstalleerd, moet u ASP.NET versie 4.5 expliciet inschakelen. Bijvoorbeeld, op een 64-bits computer met de .NET Framework versie 4.0.30319, voer de volgende opdracht: **%windir%\Microsoft.NET\Framework64\v4.0.30319\aspnet_regiis.exe -i-inschakelen**  

**Het geheugen van de computer:**  

-   De computer die fungeert als host voor deze sitesysteemrol moet minimaal 5% van de computer beschikbaar geheugen vrij waarmee de sitesysteemrol voor het verwerken van aanvragen.  

-   Wanneer deze sitesysteemrol CO-locaties met een andere sitesysteemrol waarvoor deze dezelfde vereiste is, is deze geheugenvereiste voor de computer niet vergroten, maar blijft minimaal 5%.  

###  <a name="bkmk_2008EnrollProxpreq"></a>Proxypunt voor inschrijving  
**.NET framework:**  

-   .NET framework 4.5.2  

     Wanneer deze sitesysteemrol wordt geïnstalleerd als de server nog niet over een ondersteunde versie van .NET Framework is geïnstalleerd, installeert Configuration Manager automatisch de .NET Framework 4.5.2. Deze installatie kan de server plaats in de status in behandeling opnieuw worden opgestart. Wanneer een opnieuw opstarten in behandeling is voor de .NET Framework, .NET-toepassingen mogelijk mislukken totdat er nadat de server opnieuw wordt opgestart en de installatie is voltooid.  

**Windows Communication Foundation (WCF) activation:**  

-   HTTP-activering  

-   Niet-HTTP-activering  

**IIS-configuratie:**

De standaard IIS-configuratie is vereist bij de volgende toevoegingen:  

-   Toepassingsontwikkeling:  

    -   ASP.NET (en automatisch geselecteerde opties)  

         In sommige scenario's, zoals wanneer IIS is geïnstalleerd of geconfigureerd als .NET Framework 4.5.2 versie is geïnstalleerd, moet u ASP.NET versie 4.5 expliciet inschakelen. Bijvoorbeeld, op een 64-bits computer met de .NET Framework versie 4.0.30319, voer de volgende opdracht: **%windir%\Microsoft.NET\Framework64\v4.0.30319\aspnet_regiis.exe -i-inschakelen**  

**Het geheugen van de computer:**  

-   De computer die fungeert als host voor deze sitesysteemrol moet minimaal 5% van de computer beschikbaar geheugen vrij waarmee de sitesysteemrol voor het verwerken van aanvragen.  

-   Wanneer deze sitesysteemrol CO-locaties met een andere sitesysteemrol waarvoor deze dezelfde vereiste is, is deze geheugenvereiste voor de computer niet vergroten, maar blijft minimaal 5%.  

###  <a name="bkmk_2008FSPpreq"></a>Terugvalstatuspunt  
**IIS-configuratie:**

De standaard IIS-configuratie is vereist bij de volgende toevoegingen:  

-   Compatibiliteit met IIS 6-beheer:  

    -   Compatibiliteit met IIS 6-metabase  

###  <a name="bkmk_2008MPpreq"></a>Beheerpunt  
**.NET framework:**  

-   .NET framework 4.5.2  

**IIS-configuratie:**

U kunt de standaard IIS-configuratie of een aangepaste configuratie gebruiken. Elk beheerpunt in te schakelen voor de ondersteuning van mobiele apparaten vereist de extra IIS-configuratie voor ASP.NET (en de bijbehorende automatisch geselecteerde opties).

In sommige scenario's, zoals wanneer IIS is geïnstalleerd of geconfigureerd als .NET Framework 4.5.2 versie is geïnstalleerd, moet u ASP.NET versie 4.5 expliciet inschakelen. Bijvoorbeeld, op een 64-bits computer met de .NET Framework versie 4.0.30319, voer de volgende opdracht: **%windir%\Microsoft.NET\Framework64\v4.0.30319\aspnet_regiis.exe -i-inschakelen**  


U moet de volgende opties voor IIS inschakelen voor het gebruik van een aangepaste IIS-configuratie:  

-   Toepassingsontwikkeling:  

    -   ISAPI-extensies  

-   Beveiliging:  

    -   Windows-verificatie  

-   Compatibiliteit met IIS 6-beheer:  

    -   Compatibiliteit met IIS 6-metabase  

    -   Compatibiliteit met IIS 6 WMI  


Wanneer u een aangepaste IIS-configuratie gebruikt, kunt u de opties die vereist is, zoals het volgende niet verwijderen:  

-   Veelvoorkomende HTTP-functies:  

    -   HTTP-omleiding  

-   IIS Management Scripts en hulpprogramma 's  

**Windows-functie:**  

-   BITS-serveruitbreidingen (en automatisch geselecteerde opties) of Background Intelligent Transfer Services (BITS) (en automatisch geselecteerde opties)  

###  <a name="bkmk_2008RSpoint"></a>Reporting services-punt  
**.NET framework:**  

-   .NET framework 4.5.2  

**SQL Server Reporting Services:**  

-   U moet installeren en configureren van ten minste één exemplaar van SQL Server voor de ondersteuning van SQL Server Reporting Services voordat de installatie van het reporting services-punt.  

-   Het exemplaar dat u voor SQL Server Reporting Services gebruikt kunt u voor de sitedatabase gebruiken hetzelfde exemplaar zijn.  

-   Daarnaast kan het exemplaar dat u gebruikt worden gedeeld met andere System Center-producten, zolang de System Center-producten geen beperkingen voor het delen van het exemplaar van SQL Server.  

###  <a name="bkmk_2008SCPpreq"></a>Het service connection point  
**.NET framework:**  

-   .NET framework 4.5.2  

     Wanneer deze sitesysteemrol wordt geïnstalleerd als de server nog niet over een ondersteunde versie van .NET Framework is geïnstalleerd, installeert Configuration Manager automatisch de .NET Framework 4.5.2. Deze installatie kan de server plaats in de status in behandeling opnieuw worden opgestart. Wanneer een opnieuw opstarten in behandeling is voor de .NET Framework, .NET-toepassingen mogelijk mislukken totdat er nadat de server opnieuw wordt opgestart en de installatie is voltooid.  

**Te distribueren pakket Visual C++:**  

-   Op elke computer die als host fungeert voor een distributiepunt installeert Configuration Manager het herdistrueerbare pakket voor Microsoft Visual C++ 2013.  

-   De sitesysteemrol is vereist voor de x64 versie.  

###  <a name="bkmk_2008SUPpreq"></a>Software-updatepunt  
**.NET framework:**  

-   .NET framework 3.5 SP1 (of hoger)  

-   .NET framework 4.5.2  

**IIS-configuratie:**

De standaard IIS-configuratie is vereist.  

**Windows Server updateservices:**  

-   Voordat u een softwareupdate-punt installeert, moet u de Windows Server-rol Windows Server Update Services installeren op een computer.  

-   Zie [Software-updates plannen in System Center Configuration Manager](../../../sum/plan-design/plan-for-software-updates.md) voor meer informatie.

###  <a name="bkmk_2008SMPpreq"></a>Statusmigratiepunt  
**IIS-configuratie:**

De standaard IIS-configuratie is vereist.  

