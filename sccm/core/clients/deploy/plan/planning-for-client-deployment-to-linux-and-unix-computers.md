---
title: Clientimplementatie op Linux en UNIX-computers plannen | Microsoft Docs
description: Plan voor clientimplementatie op Linux en UNIX-computers in System Center Configuration Manager.
ms.custom: na
ms.date: 08/30/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: configmgr-client
ms.tgt_pltfrm: na
ms.topic: get-started-article
ms.assetid: 44153689-70e8-42ad-9ae8-17ae35f6a2e3
caps.latest.revision: "9"
caps.handback.revision: "0"
author: arob98
ms.author: angrobe
manager: angrobe
ms.openlocfilehash: 488173a64c25e1e3b3e715228bdb46df9acd9e7d
ms.sourcegitcommit: f6a428a8db7145affa388f59e0ad880bdfcf17b5
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 09/14/2017
---
# <a name="planning-for-client-deployment-to-linux-and-unix-computers-in-system-center-configuration-manager"></a>Clientimplementatie op Linux- en UNIX-computers in System Center Configuration Manager plannen

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*

U kunt de System Center Configuration Manager-client installeren op computers met Linux of UNIX. Deze client is ontworpen voor servers die werken als een werkgroepcomputer, en de client ondersteunt geen interactie met aangemelde gebruikers. Nadat u de clientsoftware installeren en de client tot stand communicatie met de Configuration Manager-site brengt, beheert u de client met behulp van de Configuration Manager-console en rapporten.  

> [!NOTE]  
>  De Configuration Manager-client voor Linux en UNIX-computers biedt geen ondersteuning voor de volgende beheermogelijkheden:  
>   
>  -   Clientpushinstallatie  
> -   Implementatie van besturingssystemen  
> -   Toepassingsimplementatie; implementeer in plaats daarvan software met behulp van pakketten en programma's.  
> -   Software-inventaris  
> -   Software-updates  
> -   Instellingen voor naleving  
> -   Extern beheer  
> -   Energiebeheer  
> -   Clientcontrole en herstel van de clientstatus  
> -   Clientbeheer via internet  

 Zie voor meer informatie over de ondersteunde Linux- en UNIX-distributies en de vereiste hardware voor ondersteuning van de client voor Linux en UNIX, de sectie [Aanbevolen hardware voor System Center Configuration Manager](../../../../core/plan-design/configs/recommended-hardware.md).  

 Gebruik de informatie in dit artikel om te plannen voor het implementeren van Configuration Manager-client voor Linux en UNIX.  

##  <a name="BKMK_ClientDeployPrereqforLnU"></a>Vereisten voor de clientimplementatie op Linux en UNIX-Servers  
 Gebruik de volgende informatie om te bepalen aan welke vereisten moet worden voldaan om de client voor Linux en UNIX te implementeren.  

###  <a name="BKMK_ClientDeployExternalforLnU"></a>Afhankelijkheden extern aan Configuration Manager:  
 In de volgende tabellen worden de vereiste UNIX- en Linux-besturingssystemen en pakketafhankelijkheden beschreven.  

 **Red Hat Enterprise Linux Server versie 5.1 (Tikanga)**  

|Vereist pakket|Beschrijving|Minimale versie|  
|----------------------|-----------------|---------------------|  
|glibc|Standaardbibliotheken voor C|2.5-12|  
|Openssl|OpenSSL-bibliotheken; Secure Network Communications-protocol|0.9.8b-8.3.el5|  
|PAM|Pluggable Authentication Modules|0.99.6.2-3.14.el5|  

 **Red Hat Enterprise Linux Server versie 6**  

|Vereist pakket|Beschrijving|Minimale versie|  
|----------------------|-----------------|---------------------|  
|glibc|Standaardbibliotheken voor C|2.12-1.7|  
|Openssl|OpenSSL-bibliotheken; Secure Network Communications-protocol|1.0.0-4|  
|PAM|Pluggable Authentication Modules|1.1.1-4|  


 **Solaris 10 SPARC**  

|Vereist pakket|Beschrijving|Minimale versie|  
|----------------------|-----------------|---------------------|  
|Vereiste besturingssysteempatch|PAM-geheugenlek|117463-05|  
|SUNWlibC|Sun Workshop gebundelde samenstellers libC (sparc)|5.10, REV=2004.12.22|  
|SUNWlibms|Math & Microtasking-bibliotheken (Usr) (sparc)|5.10, REV=2004.11.23|  
|SUNWlibmsr|Math & Microtasking-bibliotheken (Root) (sparc)|5.10, REV=2004.11.23|  
|SUNWcslr|Core Solaris-bibliotheken (Root) (sparc)|11.10.0, REV=2005.01.21.15.53|  
|SUNWcsl|Core Solaris-bibliotheken (Root) (sparc)|11.10.0, REV=2005.01.21.15.53|  
|OpenSSL|SUNopenssl-bibliotheken (Usr)<br /><br /> Sun biedt de OpenSSL-bibliotheken voor Solaris 10 SPARC. Ze worden gebundeld met het besturingssysteem.|11.10.0,REV=2005.01.21.15.53|  
|PAM|Pluggable Authentication Modules<br /><br /> SUNWcsr, Core Solaris, (Root) (sparc)|11.10.0, REV=2005.01.21.15.53|  

 **Solaris 10 x86**  

|Vereist pakket|Beschrijving|Minimale versie|  
|----------------------|-----------------|---------------------|  
|Vereiste besturingssysteempatch|PAM-geheugenlek|117464-04|  
|SUNWlibC|Sun Workshop Compilers Bundled libC (i386)|5.10,REV=2004.12.20|  
|SUNWlibmsr|Math & Microtasking-bibliotheken (Root) (i386)|5.10, REV=2004.12.18|  
|SUNWcsl|Core Solaris, (gedeelde bibliotheken) (i386)|11.10.0,REV=2005.01.21.16.34|  
|SUNWcslr|Core Solaris-bibliotheken (Root) (i386)|11.10.0, REV=2005.01.21.16.34|  
|OpenSSL|SUNWopenssl-bibliotheken; OpenSSL-bibliotheken (Usr) (i386)|11.10.0, REV=2005.01.21.16.34|  
|PAM|Pluggable Authentication Modules<br /><br /> SUNWcsr Core Solaris, (Root)(i386)|11.10.0,REV=2005.01.21.16.34|  

 **Solaris 11 SPARC**  

|Vereist pakket|Beschrijving|Minimale versie|  
|----------------------|-----------------|---------------------|  
|SUNWlibC|Sun Workshop Compilers Bundled libC|5.11, REV=2011.04.11|  
|SUNWlibmsr|Math & Microtasking-bibliotheken (Root)|5.11, REV=2011.04.11|  
|SUNWcslr|Core Solaris-bibliotheken (Root)|11.11, REV=2009.11.11|  
|SUNWcsl|Core Solaris, (gedeelde bibliotheken)|11.11, REV=2009.11.11|  
|SUNWcsr|Core Solaris, (Root)|11.11, REV=2009.11.11|  
|SUNWopenssl-libraries|OpenSSL-bibiotheken (Usr)|11.11.0,REV=2010.05.25.01.00|  

 **Solaris 11 x86**  

|Vereist pakket|Beschrijving|Minimale versie|  
|----------------|-----------|---------------|  
|SUNWlibC|Sun Workshop Compilers Bundled libC|5.11, REV=2011.04.11|  
|SUNWlibmsr|Math & Microtasking-bibliotheken (Root)|5.11, REV=2011.04.11|  
|SUNWcslr|Core Solaris-bibliotheken (Root)|11.11, REV=2009.11.11|  
|SUNWcsl|Core Solaris, (gedeelde bibliotheken)|11.11, REV=2009.11.11|  
|SUNWcsr|Core Solaris, (Root)|11.11, REV=2009.11.11|  
|SUNWopenssl-libraries|OpenSSL-bibiotheken (Usr)|11.11.0,REV=2010.05.25.01.00|  


 **SUSE Linux Enterprise Server 10 SP1 (i586)**  

|Vereist pakket|Beschrijving|Minimale versie|  
|----------------------|-----------------|---------------------|  
|glibc-2,4-31,30|Standaard gedeelde bibliotheek voor C|2.4-31.30|  
|OpenSSL|OpenSSL-bibliotheken; Secure Network Communications-protocol|0.90,8a-18,15|  
|PAM|Pluggable Authentication Modules|0.99.6.3-28.8|  

 **SUSE Linux Enterprise Server 11 (i586)**  

|Vereist pakket|Beschrijving|Minimale versie|  
|----------------------|-----------------|---------------------|  
|glibc-2.9-13.2|Standaard gedeelde bibliotheek voor C|2.9-13.2|  
|PAM|Pluggable Authentication Modules|pam-1.0.2-20.1|  

 **Universal Linux (Debian-pakket) Debian, Ubuntu Server**  

|Vereist pakket|Beschrijving|Minimale versie|  
|----------------------|-----------------|---------------------|  
|libc6|Standaard gedeelde bibliotheek voor C|2.3.6|  
|OpenSSL|OpenSSL-bibliotheken; Secure Network Communications-protocol|0.9.8 of 1.0|  
|PAM|Pluggable Authentication Modules|0.79-3|  

 **Universal Linux (RPM-pakket) CentOS, Oracle Linux**  

|Vereist pakket|Beschrijving|Minimale versie|  
|----------------------|-----------------|---------------------|  
|glibc|Standaard gedeelde bibliotheek voor C|2.5-12|  
|OpenSSL|OpenSSL-bibliotheken; Secure Network Communications-protocol|0.9.8 of 1.0|  
|PAM|Pluggable Authentication Modules|0.99.6.2-3.14|  


 **IBM AIX 6.1**  

|Vereist pakket|Beschrijving|Minimale versie|  
|----------------------|-----------------|---------------------|  
|Versie van het besturingssysteem|Versie van besturingssysteem|AIX 6,1, alle technologieniveaus en servicepacks|  
|xlC.rte|XL C/C++ Runtime|9.0.0.5|  
|OpenSSL/openssl.base|OpenSSL-bibliotheken; Secure Network Communications-protocol|0.9.8.4|  

 **IBM AIX 7.1 (Power)**  

|Vereist pakket|Beschrijving|Minimale versie|  
|----------------------|-----------------|---------------------|  
|Versie van het besturingssysteem|Versie van besturingssysteem|AIX 7,1, elk Technology Level en Service Pack|  
|xlC.rte|XL C/C++ Runtime||  
|OpenSSL/openssl.base|OpenSSL-bibliotheken; Secure Network Communications-protocol||  


 **HP-UX 11i v3 IA64**  

|Vereist pakket|Beschrijving|Minimale versie|  
|----------------------|-----------------|---------------------|  
|HPUX11i-OE|HP-UX Foundation-besturingsomgeving|B.110,310,0709|  
|OS-Core.MinimumRuntime.CORE-SHLIBS|Specifieke IA-ontwikkelbibliotheken|B.110,31|  
|SysMgmtMin|Hulpprogramma's voor minimale software-implementatie|B.110,310,0709|  
|SysMgmtMin.openssl|OpenSSL-bibliotheken; Secure Network Communications-protocol|A.00.09.08d.002|  
|PAM|Pluggable Authentication Modules|Op HP is PAM onderdeel van de kernonderdelen van het besturingssysteem. Er zijn geen andere afhankelijkheden.|  

 **Configuration Manager-afhankelijkheden:** De volgende tabel bevat de sitesysteemrollen die ondersteuning bieden voor Linux en UNIX-clients. Voor meer informatie over deze sitesysteemrollen, zie de sectie [De sitesysteemrollen voor System Center Configuration Manager-clients bepalen](../../../../core/clients/deploy/plan/determine-the-site-system-roles-for-clients.md).  

|Configuration Manager-sitesysteem|Meer informatie|  
|---------------------------------------|----------------------|  
|Beheerpunt|Hoewel een beheerpunt niet vereist is voor een Configuration Manager-client voor Linux en UNIX installeert, moet u een beheerpunt wordt informatie overgedragen tussen clientcomputers en Configuration Manager-servers hebben. Zonder een beheerpunt kunt u geen clientcomputers beheren.|  
|Distributiepunt|Het distributiepunt is niet vereist voor het installeren van een Configuration Manager-client voor Linux en UNIX. De sitesysteemrol is echter wel vereist als u software naar Linux- en UNIX-servers implementeert.<br /><br /> Omdat de Configuration Manager-client voor Linux en UNIX geen ondersteuning biedt voor communicatie via SMB, moeten de distributiepunten waarnaar u de client met HTTP of HTTPS-communicatie te ondersteunen.|  
|Terugvalstatuspunt|Het terugvalstatuspunt is niet vereist voor het installeren van een Configuration Manager-client voor Linux en UNIX. Het terugvalstatuspunt kan echter computers in de Configuration Manager-site om statusberichten te zenden wanneer ze niet kunnen met een beheerpunt communiceren. Clients kunnen ook hun installatiestatus naar het terugvalstatuspunt verzenden.|  

 **Firewallvereisten**: Zorg ervoor dat firewalls niet communicatie via de poorten die u als de client aangevraagde poorten opgeeft blokkeren. De client voor Linux en UNIX communiceert rechtstreeks met beheerpunten, distributiepunten en terugvalstatuspunten.  

 Voor meer informatie over poorten op de client voor communicatie en aanvragen, zie [De client voor Linux en UNIX configureren om beheerpunten te zoeken](../../../../core/clients/deploy/deploy-clients-to-unix-and-linux-servers.md#BKMK_ConfigClientMP).  

##  <a name="BKMK_PlanningforCommunicationsforLnU"></a>Planning voor de communicatie tussen de Forest vertrouwt voor Linux en UNIX-Servers  
 Linux en UNIX-servers die u met Configuration Manager beheert werken als werkgroepclients en vereisen soortgelijke configuraties als Windows-clients die zich in een werkgroep. Voor meer informatie over communicatie van computers in werkgroepen, zie de sectie [Communicatie tussen Active Directory-forests](../../../../core/plan-design/hierarchy/communications-between-endpoints.md#Plan_Com_X-Forest) in het onderwerp [De communicatie tussen de eindpunten in System Center Configuration Manager](../../../../core/plan-design/hierarchy/communications-between-endpoints.md).  

###  <a name="BKMK_ServiceLocationforLnU"></a>Servicelocatie door de client voor Linux en UNIX  
 De taak om een sitesysteemserver te zoeken die clients van services voorzien, wordt een servicelocatie genoemd. In tegenstelling tot een Windows-client gebruikt de client voor Linux en UNIX geen Active Directory voor de servicelocatie. Configuration Manager-client voor Linux en UNIX biedt bovendien geen ondersteuning voor een clienteigenschap die het domeinachtervoegsel van een beheerpunt specificeert. In plaats daarvan leert de client over aanvullende sitesysteemservers die services aan clients leveren via een bekend beheerpunt dat u toewijst wanneer u de clientsoftware installeert.  

 Zie de sectie [Servicelocatiebepaling en hoe het toegewezen beheerpunt voor clients wordt bepaald](../../../../core/plan-design/hierarchy/understand-how-clients-find-site-resources-and-services.md#BKMK_Plan_Service_Location) in het onderwerp [Begrijpen hoe clients siteresources en -services vinden voor System Center Configuration Manager voor meer informatie over servicelocatie](../../../../core/plan-design/hierarchy/understand-how-clients-find-site-resources-and-services.md).  

##  <a name="BKMK_SecurityforLnU"></a>Planning voor beveiliging en certificaten voor Linux en UNIX-Servers  
 Voor een veilige en geverifieerde communicatie met Configuration Manager-sites communicatiemodel Configuration Manager-client voor Linux en UNIX hetzelfde gebruiken als Configuration Manager-client voor Windows.  

 Wanneer u de client voor Linux en UNIX installeert, kunt u de client een PKI-certificaat dat deze via HTTPS te communiceren met Configuration Manager-sites kan toewijzen. Als u geen PKI-certificaat toewijst, maakt de client een zelfondertekend certificaat en communiceert deze alleen via HTTP.  

 Clients die worden voorzien van een PKI-certificaat wanneer ze worden geïnstalleerd, gebruiken HTTPS om te communiceren met beheerpunten. Wanneer een client geen beheerpunt kan vinden dat HTTPS ondersteunt, wordt HTTP met het opgegeven PKI-certificaat gebruikt.  

 Als een Linux- of UNIX-client een PKI-certificaat gebruikt, hoeft u de client niet goed te keuren. Wanneer een client een zelfondertekend certificaat gebruikt, controleert u de hiërarchie-instellingen voor goedkeuring van clients in de Configuration Manager-console. Wanneer niet de goedkeuringsmethode **Alle computers automatisch goedkeuren (niet aanbevolen)** voor de client wordt gebruikt, moet u de client handmatig goedkeuren.  

 Voor meer informatie over het handmatig goedkeuren van de client, zie de sectie [Clients beheren in het knooppunt Apparaten](../../../../core/clients/manage/manage-clients.md#BKMK_ManagingClients_DevicesNode) in het onderwerp [Clients beheren in System Center Configuration Manager](../../../../core/clients/manage/manage-clients.md).  

 Zie voor meer informatie over het gebruik van certificaten in Configuration Manager [PKI-certificaatvereisten voor System Center Configuration Manager](../../../../core/plan-design/network/pki-certificate-requirements.md).  

###  <a name="BKMK_AboutCertsforLnU"></a>Over certificaten voor gebruik door Linux en UNIX-Servers  
 Configuration Manager-client voor Linux en UNIX gebruikt een zelfondertekend certificaat of een X.509 PKI-certificaat net als clients met Windows-computers. Er zijn geen wijzigingen in de PKI-vereisten voor sitesystemen van Configuration Manager bij het beheren van Linux en UNIX-clients.  

 De certificaten die u kunt voor Linux gebruiken en UNIX-clients die met sitesystemen van Configuration Manager communiceren moet de indeling van een Public Key Certificate Standard (PKCS #12) en het wachtwoord bekendmaken, zodat u dit naar de client opgeven kunt wanneer u het PKI-certificaat opgeeft.  

 Configuration Manager-client voor Linux en UNIX ondersteunt één PKI-certificaat en biedt geen ondersteuning voor meerdere certificaten. Daarom de criteria voor certificaatselectie voor u te configureren voor een Configuration Manager site is niet van toepassing.  

###  <a name="BKMK_ConfigCertsforLnU"></a>Configureren van certificaten voor Linux en UNIX-Servers  
 Voor het configureren van een Configuration Manager-client voor Linux en UNIX-servers voor het gebruik van HTTPS-communicatie, moet u de client voor het gebruik van een PKI-certificaat op het moment dat u de client installeert. U kunt een certificaat niet vóór de installatie van de clientsoftware inrichten.  

 Wanneer u een client installeert die gebruikmaakt van een PKI-certificaat, gebruikt u de opdrachtregelparameter -**UsePKICert** om de naam en locatie op te geven van een PKCS#12-bestand dat het PKI-certificaat bevat. Daarnaast moet u de opdrachtregelparameter **-certpw** gebruiken om een wachtwoord voor het certificaat op te geven.  

 Als u **-UsePKICert** niet opgeeft, genereert de client een zelfondertekend certificaat en probeert de client alleen via HTPP met de sitesysteemservers te communiceren.  

##  <a name="BKMK_NoSHA-256"></a>Doen over Linux- en UNIX-besturingssystemen die geen SHA-256 ondersteunen  
 De volgende Linux en UNIX-besturingssystemen die worden ondersteund als clients voor Configuration Manager zijn uitgebracht met versies van OpenSSL die SHA-256 niet ondersteunen:  

-   Solaris Version 10 (SPARC/x86)  


 Voor het beheren van deze besturingssystemen met Configuration Manager, moet u de Configuration Manager-client voor Linux en UNIX installeren met een opdrachtregelparameter die de client over te slaan validatie van SHA-256 instrueert. Configuration Manager-clients die worden uitgevoerd op deze besturingssysteemversies werken in een minder veilige modus dan clients die SHA-256 ondersteunen. Deze minder veilige werkmodus wordt gekenmerkt door het volgende gedrag:  

-   De siteserverhandtekening die is gekoppeld aan het beleid dat clients bij een beheerpunt aanvragen, wordt niet gevalideerd.  

-   De hash voor pakketten die clients van een distributiepunt downloaden, wordt niet gevalideerd.  

> [!IMPORTANT]  
>  Met de optie **ignoreSHA256validation** kunt u de client voor Linux- en UNIX-computers in een minder veilige modus uitvoeren. Dit is bedoeld voor gebruik op oudere platforms die geen ondersteuning voor SHA-256 bieden. Dit is een beveiligingsonderdrukking en wordt niet door Microsoft wordt aanbevolen, maar wordt ondersteund voor gebruik in een veilige en vertrouwde datacenteromgeving.  

 Wanneer de Configuration Manager-client voor Linux en UNIX wordt geïnstalleerd, controleert het installatiescript de versie van het besturingssysteem. Standaard, als de versie van het besturingssysteem wordt geïdentificeerd als een versie zonder een versie van OpenSSL met ondersteuning voor SHA-256, mislukt de installatie van de Configuration Manager-client.  

 Voor het installeren van Configuration Manager-client op Linux en UNIX-besturingssystemen die niet zijn uitgebracht met een versie van OpenSSL met ondersteuning voor SHA-256, moet u de installatieopdrachtregelparameter **ignoreSHA256validation**. Wanneer u deze opdrachtregeloptie op een toepasselijk Linux of UNIX-besturingssysteem gebruikt, wordt de Configuration Manager-client SHA-256-validatie wordt overgeslagen en wordt na de installatie, de client niet gebruikt SHA-256 om gegevens te ondertekenen met behulp van HTTP naar sitesystemen worden verzonden. Voor meer informatie over het configureren van Linux- en UNIX-clients om certificaten te gebruiken, zie [Planning voor de beveiliging van en certificaten voor Linux en UNIX-Servers](#BKMK_SecurityforLnU) in dit onderwerp. Zie de sectie [Configureer ondertekening en versleuteling](../../../../core/plan-design/security/configure-security.md#BKMK_ConfigureSigningEncryption) in het onderwerp [Beveiliging configureren in System Center Configuration Manager](../../../../core/plan-design/security/configure-security.md) voor informatie over het vereisen van SHA-256.  

> [!NOTE]  
>  De opdrachtregeloptie **ignoreSHA256validation** wordt genegeerd op computers waarop een versie van Linux en UNIX wordt uitgevoerd die is uitgebracht met versies van OpenSSL die ondersteuning voor SHA-256 bieden.  
