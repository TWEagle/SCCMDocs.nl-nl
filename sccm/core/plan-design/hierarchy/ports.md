---
title: Poorten die worden gebruikt voor verbindingen
titleSuffix: Configuration Manager
description: Meer informatie over de vereiste en aanpasbare poorten die System Center Configuration Manager voor verbindingen gebruikt.
ms.custom: na
ms.date: 02/16/2018
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: c6777fb0-0754-4abf-8a1b-7639d23e9391
caps.latest.revision: 
caps.handback.revision: 
author: aczechowski
ms.author: aaroncz
manager: angrobe
ms.openlocfilehash: 8db098f69180aac3785087af6ee305b3651094e5
ms.sourcegitcommit: 1378532fac2620ddcfd31061982f344a290c2e67
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 02/20/2018
---
# <a name="ports-used-in-system-center-configuration-manager"></a>Poorten die worden gebruikt in System Center Configuration Manager

Van toepassing op: System Center Configuration Manager (huidige vertakking)*

System Center Configuration Manager is een gedistribueerd client/server-systeem. De gedistribueerde aard van Configuration Manager betekent dat verbindingen worden tussen siteservers, sitesystemen en clients gemaakt kunnen. Sommige verbindingen gebruiken poorten die zijn niet configureerbaar en sommige ondersteunen aangepaste poorten die u opgeeft. Controleer of de vereiste poorten beschikbaar als u een poortfiltertechnologie gebruikt zoals firewalls, routers, proxy-servers of IPsec gebruiken.  
    
> [!NOTE]  
>  Als u ondersteuning voor clients op Internet met behulp van SSL-bridging, naast Poortvereisten, kunt u wellicht ook toestaan dat sommige HTTP-woorden en -koppen bladeren door uw firewall.   

 De lijsten van poorten die volgen, worden gebruikt door Configuration Manager en bevatten geen informatie voor standaard Windows-services, zoals groepsbeleidinstellingen voor Active Directory Domain Services of Kerberos-verificatie. Voor informatie over Windows Server services en poorten, zie [Service overview and network port requirements for Windows (Service overzicht en netwerkpoortvereisten voor het Windows Server-systeem)](http://go.microsoft.com/fwlink/p/?LinkID=123652).  

##  <a name="BKMK_ConfigurablePorts"></a> Poorten die u kunt configureren  
 Configuration Manager kunt u de poorten voor de volgende communicatietypen configureren:  

-   Application Catalog-websitepunt naar Application Catalog-webservicepunt  

-   Registratie-proxypunt naar registratiepunt  

-   Client-naar-site-systemen die IIS uitvoeren  

-   Client-naarInternet (als instellingen van proxyserver)  

-   Software-updatepunt naar Internet (als instellingen van proxyserver)  

-   Software-updatepunt naar WSUS-server  

-   Siteserver met sitedatabaseserver  

-   Reporting Services-punten  

    > [!NOTE]  
    >  De poorten die gebruikt voor de reporting services-punt-sitesysteemrol worden worden geconfigureerd in SQL Server Reporting Services. Deze poorten worden vervolgens door Configuration Manager gebruikt tijdens communicaties met reporting services-punt. Zorg ervoor dat deze poorten waarmee het IP-filter informatie voor IPsec beleidslijnen of om firewalls te configureren controleren.  

Standaard wordt poort 80 van de HTTP-poort die wordt gebruikt voor client-naar-site systeemcommunicatie en de standaard HTTPS-poort is 443. Poorten voor client-naar-site systeemcommunicatie via HTTP of HTTPS kunnen worden gewijzigd tijdens setup of in de site-eigenschappen voor uw Configuration Manager-site.  

De poorten die gebruikt voor de reporting services-punt-sitesysteemrol worden worden geconfigureerd in SQL Server Reporting Services. Deze poorten worden vervolgens door Configuration Manager gebruikt tijdens communicaties met reporting services-punt. Zorg ervoor dat deze poorten controleren wanneer u bij het definiëren van de IP-filter informatie voor IPsec beleidslijnen of om firewalls te configureren.  

##  <a name="BKMK_NonConfigurablePorts"></a> Niet-configureerbare poorten  
Configuration Manager niet toe dat u voor het configureren van poorten voor de volgende communicatietypen:  

-   Site-naar-site  

-   Siteserver-naar-site-systeem  

-   Configuration Manager-console naar SMS-Provider  

-   Configuration Manager-console naar Internet  

-   Verbindingen met cloudservices, zoals Microsoft Intune en cloud-gebaseerde distributiepunten  

##  <a name="BKMK_CommunicationPorts"></a> Poorten die door Configuration Manager-clients en sitesystemen worden gebruikt  
De volgende secties detailleren de poorten die worden gebruikt voor communicatie in Configuration Manager. De pijlen in de sectietitel vertegenwoordigen de richting van de communicatie:  

-   --> Geeft aan dat één computer de communicatie start en de andere computer altijd antwoordt  

-   &lt; --> Geeft aan dat elke computer communicatie kan initiëren  

###  <a name="BKMK_PortsAI"></a> Asset Intelligence-synchronisatiepunt--> Microsoft  

|Beschrijving|UDP|TCP|  
|-----------------|---------|---------|  
|Secure Hypertext Transfer Protocol (HTTPS)|--|443|  

###  <a name="BKMK_PortsAI-to-SQL"></a> Asset Intelligence-synchronisatiepunt--> SQL Server  

|Beschrijving|UDP|TCP|  
|-----------------|---------|---------|  
|SQL via TCP|--|1433 (Zie Opmerking 2, **alternatieve poort beschikbaar**)|  

###  <a name="BKMK_PortsAppCatalogService-SQL"></a> Application Catalog-webservicepunt--> SQL Server  

|Beschrijving|UDP|TCP|  
|-----------------|---------|---------|  
|SQL via TCP|--|1433 (Zie Opmerking 2, **alternatieve poort beschikbaar**)|  

###  <a name="BKMK_PortsAppCatalogWebSitePoint_AppCatalogWebServicePoint"></a> Application Catalog-website-punt--> Application Catalog-webservicepunt  

|Beschrijving|UDP|TCP|  
|-----------------|---------|---------|  
|Hypertext Transfer Protocol (HTTP)|--|80 (Zie Opmerking 2, **alternatieve poort beschikbaar**)|  
|Secure Hypertext Transfer Protocol (HTTPS)|--|443 (Zie Opmerking 2, **alternatieve poort beschikbaar**)|  

###  <a name="BKMK_PortsClient-AppCatalogWebsitePoint"></a> Client--> Application Catalog-websitepunt  

|Beschrijving|UDP|TCP|  
|-----------------|---------|---------|  
|Hypertext Transfer Protocol (HTTP)|--|80 (Zie Opmerking 2, **alternatieve poort beschikbaar**)|  
|Secure Hypertext Transfer Protocol (HTTPS)|--|443 (Zie Opmerking 2, **alternatieve poort beschikbaar**)|  

###  <a name="BKMK_PortsClient-ClientWakeUp"></a> Client -- &gt; Client  
 Naast de poorten die worden vermeld in de volgende tabel, gebruikt wake-up proxy ook Internet Control Message Protocol (ICMP) echoaanvraagberichten van één client met een andere client wanneer ze zijn geconfigureerd voor wake-up proxy.

Deze communicatie wordt gebruikt om te bevestigen of de andere clientcomputer actief is op het netwerk. Naar ICMP wordt soms verwezen als TCP/IP-pingopdrachten. ICMP heeft geen een UDP of TCP-protocolnummer en dus niet vermeld de onderstaande tabel. Evenwel moet elke host-gebaseerde firewall op deze clientcomputers of tussenliggende netwerkapparaten binnen het subnet ICMP-verkeer toelating geven ​​voor wake-up proxy communicatie om te slagen.  

|Beschrijving|UDP|TCP|  
|-----------------|---------|---------|  
|Wake on LAN|9 (Zie Opmerking 2, **alternatieve poort beschikbaar**)|--|  
|Wake-up proxy|25536 (Zie Opmerking 2, **alternatieve poort beschikbaar**)|--|  

###  <a name="BKMK_PortsClient-PolicyModule"></a> Client -- &gt; Configuration Manager beleidsmodule (registratieservice netwerkapparaat)  

|Beschrijving|UDP|TCP|  
|-----------------|---------|---------|  
|Hypertext Transfer Protocol (HTTP)||80|  
|Secure Hypertext Transfer Protocol (HTTPS)|--|443|  

###  <a name="BKMK_PortsClient-CloudDP"></a> Client--> Cloud-gebaseerd distributiepunt  

|Beschrijving|UDP|TCP|  
|-----------------|---------|---------|  
|Secure Hypertext Transfer Protocol (HTTPS)|--|443|  

###  <a name="BKMK_PortsClient-DP"></a> Client--> Distributiepunt  

|Beschrijving|UDP|TCP|  
|-----------------|---------|---------|  
|Hypertext Transfer Protocol (HTTP)|--|80 (Zie Opmerking 2, **alternatieve poort beschikbaar**)|  
|Secure Hypertext Transfer Protocol (HTTPS)|--|443 (Zie Opmerking 2, **alternatieve poort beschikbaar**)|  

###  <a name="BKMK_PortsClient-DP2"></a> Client--> Distributiepunt is geconfigureerd voor multicast  

|Beschrijving|UDP|TCP|  
|-----------------|---------|---------|  
|Server Message Block (SMB)|--|445|  
|Multicast-protocol|63000-64000|--|  

###  <a name="BKMK_PortsClient-DP3"></a> Client--> Distributiepunt is geconfigureerd voor PXE  

|Beschrijving|UDP|TCP|  
|-----------------|---------|---------|  
|Dynamic Host Configuration Protocol (DHCP)|67 en 68|--|  
|Trivial File Transfer Protocol (TFTP)|69 (Zie opmerking 4, **Trivial FTP (TFTP) Daemon**)|--|  
|Boot Information Negotiation Layer (BINL)|4011|--|  

###  <a name="BKMK_PortsClient-FSP"></a> Client--> Terugvalstatuspunt  

|Beschrijving|UDP|TCP|  
|-----------------|---------|---------|  
|Hypertext Transfer Protocol (HTTP)|--|80 (Zie Opmerking 2, **alternatieve poort beschikbaar**)|  

###  <a name="BKMK_PortsClient-GCDC"></a> Client--> Globale catalogus-domeincontroller  
 Een Configuration Manager-client neemt geen contact op met een server voor globale catalogus wanneer hij een werkgroepcomputer is of wanneer hij geconfigureerd is voor Internet-only-communicatie.  

|Beschrijving|UDP|TCP|  
|-----------------|---------|---------|  
|Globale catalogus LDAP|--|3268|  


###  <a name="BKMK_PortsClient-MP"></a> Client--> Beheerpunt  

|Beschrijving|UDP|TCP|  
|-----------------|---------|---------|  
|Melding client (standaardcommunicatie vóór terug te vallen op HTTP of HTTPS)|--|10123 (Zie Opmerking 2, **alternatieve poort beschikbaar**)|  
|Hypertext Transfer Protocol (HTTP)|--|80 (Zie Opmerking 2, **alternatieve poort beschikbaar**)|  
|Secure Hypertext Transfer Protocol (HTTPS)|--|443 (Zie Opmerking 2, **alternatieve poort beschikbaar**)|  

###  <a name="BKMK_PortsClient-SUP"></a> Client--> Software-updatepunt  

|Beschrijving|UDP|TCP|  
|-----------------|---------|---------|  
|Hypertext Transfer Protocol (HTTP)|--|80 of 8530 (zie opmerking 3, **Windows Server-updateservices**)|  
|Secure Hypertext Transfer Protocol (HTTPS)|--|443 of 8531 (zie opmerking 3, **Windows Server-updateservices**)|  

###  <a name="BKMK_PortsClient-SMP"></a> Client--> Statusmigratiepunt  

|Beschrijving|UDP|TCP|  
|-----------------|---------|---------|  
|Hypertext Transfer Protocol (HTTP)|--|80 (Zie Opmerking 2, **alternatieve poort beschikbaar**)|  
|Secure Hypertext Transfer Protocol (HTTPS)|--|443 (Zie Opmerking 2, **alternatieve poort beschikbaar**)|  
|Server Message Block (SMB)|--|445|  

###  <a name="BKMK_PortsConsole-Client"></a> Configuration Manager-console--> Client  

|Beschrijving|UDP|TCP|  
|-----------------|---------|---------|  
|Beheer op afstand (controle)|--|2701|  
|Hulp op afstand (RDP en RTC)|--|3389|  

###  <a name="BKMK_PortsConsole-Internet"></a> Configuration Manager-console--> Internet  

|Beschrijving|UDP|TCP|  
|-----------------|---------|---------|  
|Hypertext Transfer Protocol (HTTP)|--|80|  
|Secure Hypertext Transfer Protocol (HTTPS)|--|443|

De Configuration Manager-console gebruikt toegang tot internet voor het volgende: 
- Software-updates downloaden vanaf Microsoft Update voor implementatiepakketten.
- Het item Feedback in het lint.
- Koppelingen naar documentatie binnen de console.
<!--506823-->

###  <a name="BKMK_PortsConsole-RSP"></a> Configuration Manager-console--> Reporting Services-punt  


|Beschrijving|UDP|TCP|
|-----------------|---------|---------|   
|Hypertext Transfer Protocol (HTTP)|--|80 (Zie Opmerking 2, **alternatieve poort beschikbaar**)|  
|Secure Hypertext Transfer Protocol (HTTPS)|--|443 (Zie Opmerking 2, **alternatieve poort beschikbaar**)|  

###  <a name="BKMK_PortsConsole-Site"></a> Configuration Manager-console--> siteserver  

|Beschrijving|UDP|TCP|  
|-----------------|---------|---------|  
|RPC (initiële verbinding naar WMI om providersysteem te vinden)|--|135|  

###  <a name="BKMK_PortsConsole-Provider"></a> Configuration Manager-console--> SMS-Provider  

|Beschrijving|UDP|TCP|  
|-----------------|---------|---------|  
|RPC-eindpunttoewijzer|135|135|  
|RPC|--|Dynamisch (zie opmerking 6, **Dynamische poorten**)|  

###  <a name="BKMK_PortsCertificateRegistationPoint_PolicyModule"></a> Configuration Manager-beleidsmodule (registratieservice netwerkapparaat)--> Certificaatregistratiepunt  

|Beschrijving|UDP|TCP|  
|-----------------|---------|---------|  
|Secure Hypertext Transfer Protocol (HTTPS)|--|443 (Zie Opmerking 2, **alternatieve poort beschikbaar**)|  

###  <a name="BKMK_PortsDist_MP"></a> Distributiepunt--> beheerpunt  
 Een distributiepunt communiceert met het beheerpunt in de volgende scenario's:  

-   De status van voorgefaseerde inhoud rapporteren  

-   Samenvattingsgegevens over gebruik rapporteren  

-   Inhoudsvalidatie rapporteren  

-   Voor het rapporteren van de status van pakket downloads (pull-distributiepunt)

|Beschrijving|UDP|TCP|  
|-----------------|---------|---------|  
|Hypertext Transfer Protocol (HTTP)|--|80 (Zie Opmerking 2, **alternatieve poort beschikbaar**)|  
|Secure Hypertext Transfer Protocol (HTTPS)|--|443 (Zie Opmerking 2, **alternatieve poort beschikbaar**)|  

###  <a name="BKMK_PortsEndpointProtection_Internet"></a> Endpoint Protection-punt--> Internet  

|Beschrijving|UDP|TCP|  
|-----------------|---------|---------|  
|Hypertext Transfer Protocol (HTTP)|--|80|  

###  <a name="BKMK_PortsEP-to-SQL"></a> Endpoint Protection-punt--> SQL Server  

|Beschrijving|UDP|TCP|  
|-----------------|---------|---------|  
|SQL via TCP|--|1433 (Zie Opmerking 2, **alternatieve poort beschikbaar**)|  

###  <a name="BKMK_PortsEnrollmentProxyEnrollmentPoint"></a> Proxypunt voor inschrijving--> registratiepunt  

|Beschrijving|UDP|TCP|  
|-----------------|---------|---------|  
|Secure Hypertext Transfer Protocol (HTTPS)|--|443 (Zie Opmerking 2, **alternatieve poort beschikbaar**)|  

###  <a name="BKMK_PortsEnrollmentEnrollmentSQL"></a> Registratiepunt--> SQL Server  

|Beschrijving|UDP|TCP|  
|-----------------|---------|---------|  
|SQL via TCP|--|1433 (Zie Opmerking 2, **alternatieve poort beschikbaar**)|  

###  <a name="BKMK_PortsExchangeConnectorHosted"></a> Exchange Server-Connector -- &gt; Exchange Online  

|Beschrijving|UDP|TCP|  
|-----------------|---------|---------|  
|Windows Remote Management via HTTPS|--|5986|  

###  <a name="BKMK_PortsExchangeConnectorOnPrem"></a> Exchange Server-Connector--> On-Premises Exchange Server  

|Beschrijving|UDP|TCP|  
|-----------------|---------|---------|  
|Windows Remote Management via HTTP|--|5985|  

###  <a name="BKMK_PortsMacEnrollmentProxyPoint"></a> Mac-computer--> proxypunt voor inschrijving  

|Beschrijving|UDP|TCP|  
|-----------------|---------|---------|  
|Secure Hypertext Transfer Protocol (HTTPS)|--|443|  

###  <a name="BKMK_PortsMP-DC"></a> Beheerpunt--> domeincontroller  

|Beschrijving|UDP|TCP|  
|-----------------|---------|---------|  
|Lightweight Directory Access Protocol (LDAP)|--|389|  
|Globale catalogus LDAP|--|3268|  
|RPC-eindpunttoewijzer|135|135|  
|RPC|--|Dynamisch (zie opmerking 6, **Dynamische poorten**)|  

###  <a name="BKMK_PortsMP-Site"></a> Beheerpunt &lt; --> siteserver  
 (zie opmerking 5, **Communicatie tussen de siteserver en sitesystemen**)  

|Beschrijving|UDP|TCP|  
|-----------------|---------|---------|  
|RPC-eindpunttoewijzer|--|135|  
|RPC|--|Dynamisch (zie opmerking 6, **Dynamische poorten**)|  
|Server Message Block (SMB)|--|445|  

###  <a name="BKMK_PortsMP-SQL"></a> Beheerpunt--> SQL Server  

|Beschrijving|UDP|TCP|  
|-----------------|---------|---------|  
|SQL via TCP|--|1433 (Zie Opmerking 2, **alternatieve poort beschikbaar**)|  

###  <a name="BKMK_PortsMobileDeviceClient-EnrollmentProxyPoint"></a> Mobiele apparaten--> proxypunt voor inschrijving  

|Beschrijving|UDP|TCP|  
|-----------------|---------|---------|  
|Secure Hypertext Transfer Protocol (HTTPS)|--|443|  

###  <a name="BKMK_PortsMobileDeviceClient-WindowsIntune"></a> Mobiele apparaten--> Microsoft Intune  

|Beschrijving|UDP|TCP|  
|-----------------|---------|---------|  
|Secure Hypertext Transfer Protocol (HTTPS)|--|443|  

###  <a name="BKMK_PortsRSP-SQL"></a> Reporting Services-punt--> SQL Server  

|Beschrijving|UDP|TCP|  
|-----------------|---------|---------|  
|SQL via TCP|--|1433 (Zie Opmerking 2, **alternatieve poort beschikbaar**)|  

###  <a name="BKMK_PortsIntuneConnector-WindowsIntune"></a> Serviceverbindingspunt--> Microsoft Intune  

|Beschrijving|UDP|TCP|  
|-----------------|---------|---------|  
|Secure Hypertext Transfer Protocol (HTTPS)|--|443|
Zie voor meer informatie [vereisten voor internettoegang](/sccm/core/servers/deploy/configure/about-the-service-connection-point#bkmk_urls) voor het serviceverbindingspunt wordt gehost.

###  <a name="BKMK_PortsAppCatalogWebServicePoint_SiteServer"></a> Siteserver &lt; --> Application Catalog-webservicepunt  

|Beschrijving|UDP|TCP|  
|-----------------|---------|---------|  
|Server Message Block (SMB)|--|445|  
|RPC-eindpunttoewijzer|135|135|  
|RPC|--|Dynamisch (zie opmerking 6, **Dynamische poorten**)|  

###  <a name="BKMK_PortsAppCatalogWebSitePoint_SiteServer"></a> Siteserver &lt; --> Application Catalog-websitepunt  

|Beschrijving|UDP|TCP|  
|-----------------|---------|---------|  
|Server Message Block (SMB)|--|445|  
|RPC-eindpunttoewijzer|135|135|  
|RPC|--|Dynamisch (zie opmerking 6, **Dynamische poorten**)|  

###  <a name="BKMK_PortsSite-AISP"></a> Siteserver &lt; --> Asset Intelligence-synchronisatiepunt  

|Beschrijving|UDP|TCP|  
|-----------------|---------|---------|  
|Server Message Block (SMB)|--|445|  
|RPC-eindpunttoewijzer|135|135|  
|RPC|--|Dynamisch (zie opmerking 6, **Dynamische poorten**)|  

###  <a name="BKMK_PortsSite-Client"></a> Siteserver--> Client  

|Beschrijving|UDP|TCP|  
|-----------------|---------|---------|  
|Wake on LAN|9 (Zie Opmerking 2, **alternatieve poort beschikbaar**)|--|  

###  <a name="BKMK_PortsSiteServer-CloudDP"></a> Siteserver--> Cloud-gebaseerd distributiepunt  

|Beschrijving|UDP|TCP|  
|-----------------|---------|---------|  
|Secure Hypertext Transfer Protocol (HTTPS)|--|443|  

###  <a name="BKMK_PortsSite-DP"></a> Siteserver--> distributiepunt  
 (zie opmerking 5, **Communicatie tussen de siteserver en sitesystemen**)  

|Beschrijving|UDP|TCP|  
|-----------------|---------|---------|  
|Server Message Block (SMB)|--|445|  
|RPC-eindpunttoewijzer|135|135|  
|RPC|--|Dynamisch (zie opmerking 6, **Dynamische poorten**)|  

###  <a name="BKMK_PortsSite-DC"></a> Siteserver--> domeincontroller  

|Beschrijving|UDP|TCP|  
|-----------------|---------|---------|  
|Lightweight Directory Access Protocol (LDAP)|--|389|  
|Globale catalogus LDAP|--|3268|  
|RPC-eindpunttoewijzer|135|135|  
|RPC|--|Dynamisch (zie opmerking 6, **Dynamische poorten**)|  

###  <a name="BKMK_PortsCertificateRegistrationPoint_SiteServer"></a> Siteserver &lt; --> Certificaatregistratiepunt  

|Beschrijving|UDP|TCP|  
|-----------------|---------|---------|  
|Server Message Block (SMB)|--|445|  
|RPC-eindpunttoewijzer|135|135|  
|RPC|--|Dynamisch (zie opmerking 6, **Dynamische poorten**)|  

###  <a name="BKMK_PortsEndpointProtection_SiteServer"></a> Siteserver &lt; --> Endpoint Protection-punt  

|Beschrijving|UDP|TCP|  
|-----------------|---------|---------|  
|Server Message Block (SMB)|--|445|  
|RPC-eindpunttoewijzer|135|135|  
|RPC|--|Dynamisch (zie opmerking 6, **Dynamische poorten**)|  

###  <a name="BKMK_EnrollmentPoint_SiteServer"></a> Siteserver &lt; --> registratiepunt  

|Beschrijving|UDP|TCP|  
|-----------------|---------|---------|  
|Server Message Block (SMB)|--|445|  
|RPC-eindpunttoewijzer|135|135|  
|RPC|--|Dynamisch (zie opmerking 6, **Dynamische poorten**)|  

###  <a name="BKMK_EnrollmentProxyPoint_SiteServer"></a> Siteserver &lt; --> proxypunt voor inschrijving  

|Beschrijving|UDP|TCP|  
|-----------------|---------|---------|  
|Server Message Block (SMB)|--|445|  
|RPC-eindpunttoewijzer|135|135|  
|RPC|--|Dynamisch (zie opmerking 6, **Dynamische poorten**)|  

###  <a name="BKMK_PortsSite-FSP"></a> Siteserver &lt; --> terugvalstatuspunt  
 (zie opmerking 5, **Communicatie tussen de siteserver en sitesystemen**)  

|Beschrijving|UDP|TCP|  
|-----------------|---------|---------|  
|Server Message Block (SMB)|--|445|  
|RPC-eindpunttoewijzer|135|135|  
|RPC|--|Dynamisch (zie opmerking 6, **Dynamische poorten**)|  

###  <a name="BKMK_PortSite-Internet"></a> Siteserver--> Internet  

|Beschrijving|UDP|TCP|  
|-----------------|---------|---------|  
|Hypertext Transfer Protocol (HTTP)|--|80 (Zie Opmerking 1, **proxyserverpoort**)|  

###  <a name="BKMK_PortsIssuingCA_SiteServer"></a> Siteserver &lt; --> verlenende certificeringsinstantie (CA)  
 Deze communicatie wordt gebruikt wanneer u certificaatprofielen implementeert door gebruik te maken van het certificaatregistratiepunt. De communicatie wordt niet gebruikt voor elke siteserver in de hiërarchie. In plaats daarvan wordt alleen voor de siteserver bovenaan de hiërarchie.  

|Beschrijving|UDP|TCP|  
|-----------------|---------|---------|  
|RPC-eindpunttoewijzer|135|135|  
|RPC (DCOM)|--|Dynamisch (zie opmerking 6, **Dynamische poorten**)|  

###  <a name="BKMK_PortsSite-RSP"></a> Siteserver &lt; --> Reporting services-punt  
 (zie opmerking 5, **Communicatie tussen de siteserver en sitesystemen**)  

|Beschrijving|UDP|TCP|  
|-----------------|---------|---------|  
|Server Message Block (SMB)|--|445|  
|RPC-eindpunttoewijzer|135|135|  
|RPC|--|Dynamisch (zie opmerking 6, **Dynamische poorten**)|  

###  <a name="BKMK_PortsSite-Site"></a> Siteserver &lt; --> siteserver  

|Beschrijving|UDP|TCP|  
|-----------------|---------|---------|  
|Server Message Block (SMB)|--|445|  

###  <a name="BKMK_PortsSite-SQL"></a> Siteserver--> SQL Server  

|Beschrijving|UDP|TCP|  
|-----------------|---------|---------|  
|SQL via TCP|--|1433 (Zie Opmerking 2, **alternatieve poort beschikbaar**)|  

 Tijdens de installatie van een site die gebruikmaakt van een externe SQL Server om de sitedatabase te hosten, moet u de volgende poorten tussen de siteserver en de SQL Server openen:  

|Beschrijving|UDP|TCP|  
|-----------------|---------|---------|  
|Server Message Block (SMB)|--|445|  
|RPC-eindpunttoewijzer|135|135|  
|RPC|--|Dynamisch (zie opmerking 6, **Dynamische poorten**)|  

###  <a name="BKMK_PortsSite-Provider"></a> Siteserver--> SMS-Provider  

|Beschrijving|UDP|TCP|  
|-----------------|---------|---------|  
|Server Message Block (SMB)|--|445|  
|RPC-eindpunttoewijzer|135|135|  
|RPC|--|Dynamisch (zie opmerking 6, **Dynamische poorten**)|  

###  <a name="BKMK_PortsSite-SUP"></a> Siteserver &lt; --> Software-updatepunt  
 (zie opmerking 5, **Communicatie tussen de siteserver en sitesystemen**)  

|Beschrijving|UDP|TCP|  
|-----------------|---------|---------|  
|Server Message Block (SMB)|--|445|  
|Hypertext Transfer Protocol (HTTP)|--|80 of 8530 (zie opmerking 3, **Windows Server-updateservices**)|  
|Secure Hypertext Transfer Protocol (HTTPS)|--|443 of 8531 (zie opmerking 3, **Windows Server-updateservices**)|  

###  <a name="BKMK_PortsSite-SMP"></a> Siteserver &lt; --> Statusmigratiepunt  
 (zie opmerking 5, **Communicatie tussen de siteserver en sitesystemen**)  

|Beschrijving|UDP|TCP|  
|-----------------|---------|---------|  
|Server Message Block (SMB)|--|445|  
|RPC-eindpunttoewijzer|135|135|  

###  <a name="BKMK_PortsProvider-SQL"></a> SMS-Provider -- &gt; SQL Server  

|Beschrijving|UDP|TCP|  
|-----------------|---------|---------|  
|SQL via TCP|--|1433 (Zie Opmerking 2, **alternatieve poort beschikbaar**)|  

###  <a name="BKMK_PortsSUP-Internet"></a> Software-updatepunt--> Internet  

|Beschrijving|UDP|TCP|  
|-----------------|---------|---------|  
|Hypertext Transfer Protocol (HTTP)|--|80 (Zie Opmerking 1, **proxyserverpoort**)|  

###  <a name="BKMK_PortsSUP-WSUS"></a> Software-updatepunt--> Upstream WSUS-server  

|Beschrijving|UDP|TCP|  
|-----------------|---------|---------|  
|Hypertext Transfer Protocol (HTTP)|--|80 of 8530 (zie opmerking 3, **Windows Server-updateservices**)|  
|Secure Hypertext Transfer Protocol (HTTPS)|--|443 of 8531 (zie opmerking 3, **Windows Server-updateservices**)|  

###  <a name="BKMK_PortsSQL-SQL"></a> SQL Server --&gt; SQL Server  
 Databasereplicatie tussen sites moet de SQL Server op één site om te communiceren rechtstreeks met de SQL Server op de bovenliggende of onderliggende site.  

|Beschrijving|UDP|TCP|  
|-----------------|---------|---------|  
|SQL Server service|--|1433 (Zie Opmerking 2, **alternatieve poort beschikbaar**)|  
|SQL Server Service Broker|--|4022 (Zie Opmerking 2, **alternatieve poort beschikbaar**)|  

> [!TIP]  
>  Configuration Manager is niet vereist voor de SQL Server Browser, die poort UDP 1434 gebruikt.  

###  <a name="BKMK_PortsStateMigrationPoint-to-SQL"></a> Statusmigratiepunt--> SQL Server  

|Beschrijving|UDP|TCP|  
|-----------------|---------|---------|  
|SQL via TCP|--|1433 (Zie Opmerking 2, **alternatieve poort beschikbaar**)|  



###  <a name="BKMY_PortNotes"></a> Opmerkingen voor poorten die door Configuration Manager-clients en sitesystemen worden gebruikt  

1.  **Proxy-serverpoort**: Deze poort kan niet worden geconfigureerd, maar kan worden gerouteerd via een geconfigureerde proxyserver.  

2.  **Alternatieve poort beschikbaar**: In Configuration Manager kan een alternatieve poort gedefinieerd voor deze waarde. Indien een aangepaste poort is gedefinieerd, vervang dan deze aangepaste poort wanneer u de IP-filter informatie definieert voor IPsec-beleidslijnen of om firewalls te configureren.  

3.  **Windows Server updateservices (WSUS)**: WSUS kan worden geïnstalleerd om de poorten 80/443 of poorten 8530/8531 gebruikt voor clientcommunicatie. Wanneer u WSUS in Windows Server 2012 of Windows Server 2016 uitvoert, is WSUS standaard geconfigureerd voor gebruik van poort 8530 voor HTTP en poort 8531 voor HTTPS.  

     Na de installatie, kan de poort worden gewijzigd. U moet niet hetzelfde poortnummer gebruiken over de hele sitehiërarchie.  

    -   Als de HTTP-poort 80 is, moet de HTTPS-poort 443 zijn.  

    -   Als de HTTP-poort iets anders is, moet de HTTPS-poort 1 of hoger, bijvoorbeeld 8530 en 8531.   

    > [!NOTE]  
    >  Wanneer u het software-updatepunt voor gebruik van HTTPS configureert, moet de HTTP-poort ook zijn geopend. Niet-versleutelde gegevens, zoals de gebruiksrechtovereenkomst voor specifieke updates, gebruiken de HTTP-poort.  

4.  **Trivial FTP (TFTP) Daemon**: De Trivial FTP (TFTP) Daemon-systeemservice vereist geen gebruikersnaam of wachtwoord en is een integraal onderdeel van Windows Deployment Services (WDS). De Trivial FTP Daemon service implementeert ondersteuning voor de TFTP-protocol dat wordt gedefinieerd door de volgende RFC's:  

    -   RFC 350: TFTP  

    -   RFC 2347: Uitbreiding van de optie  

    -   RFC 2348: Optie voor blokgrootte  

    -   RFC 2349: Time-opties voor interval en overdracht  

     Trivial File Transfer Protocol is ontworpen om opstartomgevingen zonder schijf te ondersteunen. TFTP Daemons luisteren op UDP-poort 69 maar antwoorden vanaf een dynamisch toegewezen hoge poort. Daarom deze poort inschakelen de TFTP-service voor het ontvangen van inkomende TFTP-aanvragen kan maar de geselecteerde server te reageren op aanvragen die afkomstig zijn niet toegestaan. U kunt de geselecteerde server te reageren op binnenkomende TFTP-aanvragen, tenzij de TFTP-server is geconfigureerd om te antwoorden vanaf poort 69 niet inschakelen.  

5.  **Communicatie tussen de siteserver en sitesystemen**: Standaard is de communicatie tussen de siteserver en sitesystemen bidirectioneel. De siteserver initieert communicatie om het sitesysteem te configureren, en dan maken de meeste sitesystemen terug verbinding naar de siteserver om statusinformatie te sturen. Reporting Service-punten en distributiepunten zenden geen statusinformatie. Als u selecteert **de siteserver moet verbinding met dit sitesysteem initiëren** op de sitesysteem-eigenschappen nadat het sitesysteem is geïnstalleerd, het sitesysteem won't starten communicatie met de siteserver. In plaats daarvan de siteserver de communicatie start en de account voor de installatie van de site gebruikt voor verificatie met de sitesysteemserver.  

6.  **Dynamische poorten**: Dynamische poorten (ook wel kortstondige poorten) gebruiken een bereik van poortnummers die gedefinieerd door de besturingssysteemversie. Voor meer informatie over de standaardpoortbereiken, zie [Service overview and network port requirements for Windows (Service overzicht en netwerk poortvereisten voor Windows)](http://go.microsoft.com/fwlink/p/?LinkId=317965).  

##  <a name="BKMK_AdditionalPorts"></a> Aanvullende lijsten met poorten  
 De volgende secties bevatten aanvullende informatie over de poorten die worden gebruikt door Configuration Manager.  

###  <a name="BKMK_ClientShares"></a> Client naar servershares  
 Clients gebruiken Server Message Block (SMB) wanneer ze verbinden met UNC shares. Bijvoorbeeld:  

-   Handmatige clientinstallatie die de CCMSetup.exe **/source:** opdrachtregel-eigenschap  

-   Endpoint Protection-clients die definitiebestanden van een UNC-pad downloaden

|Beschrijving|UDP|TCP|  
|-----------------|---------|---------|  
|Server Message Block (SMB)|--|445|  

###  <a name="BKMK_SQLPorts"></a> Verbindingen met Microsoft SQL Server  
 Voor communicatie met de SQL Server database-engine en voor intersitereplicatie kunt u de standaard SQL Server-poort gebruiken of aangepaste poorten opgeven:  

-   Gebruik van de communicatie tussen sites:  

    -   SQL Server Service Broker is standaard poort TCP 4022.  

    -   SQL Server-service, die standaard TCP-poort 1433.  

-   Intrasite-communicatie tussen de SQL Server database engine en verschillende sitesysteemrollen van Configuration Manager standaard poort TCP 1433.  

- Configuration Manager gebruikt de dezelfde poorten en protocollen om te communiceren met elke SQL-beschikbaarheidsgroep replica die de sitedatabase host als de replica een zelfstandige SQL Server-exemplaar is.

Wanneer u Azure gebruiken en de sitedatabase zich achter een interne of externe Load Balancer, het configureren van de volgende firewalluitzonderingen op elke replica en toevoegen van load-balancingregels voor de volgende poorten:
 - SQL via TCP: TCP 1433
 - SQL Server Service Broker: TCP 4022
 - Server Message Block (SMB): TCP 445
 - RPC-eindpunttoewijzer: TCP 135

> [!WARNING]  
>  Configuration Manager biedt geen ondersteuning voor dynamische poorten. Omdat SQL Server genoemde instanties standaard dynamische poorten gebruiken voor verbindingen naar de database-engine, moet u, wanneer u een genoemde instantie gebruikt, de statische poort, die u wenst te gebruiken voor intrasite-communicatie, handmatig configureren.  

 De volgende sitesysteemrollen communiceren direct met de SQL Server database:  

-   Application Catalog-webservicepunt  

-   Certificaatregistratiepuntrol  

-   Servicepunt voor inschrijving  

-   Beheerpunt  

-   Siteserver  

-   Reporting Services-punt  

-   SMS-provider  

-   SQL Server --> SQL Server  

Wanneer een SQL Server een database host voor meer dan één site, moet elke database een afzonderlijke instantie van SQL Server gebruiken, en elke instantie moet geconfigureerd zijn met een unieke set van poorten.  

Als er een firewall ingeschakeld op de computer met SQL Server, zorg ervoor dat deze is geconfigureerd om toe te staan de poorten in gebruik door uw implementatie. Configureer ook firewalls die op extra locaties op het netwerk tussen computers die met de SQL-Server communiceren zodat deze dezelfde poorten zijn.  

Zie voor een voorbeeld van hoe u SQL Server configureren voor het gebruik van een specifieke poort [hoe: Configureren van een Server om te luisteren naar een specifieke TCP-poort (SQL Server Configuration Manager)](http://go.microsoft.com/fwlink/p/?LinkID=226349) in de SQL Server TechNet-bibliotheek.  


### <a name="bkmk_discovery"> </a> Detectie en publiceren
De volgende poorten worden gebruikt voor de detectie en het publiceren van site-informatie:
 - Lightweight Directory Access Protocol (LDAP): 389
 - Globale catalogus LDAP 3268
 - RPC-eindpunttoewijzer: 135
 - RPC: Dynamisch toegewezen hoge TCP-poorten
 - TCP: 1024: 5000
 - TCP:  49152: 65535


###  <a name="BKMK_External"></a> Externe verbindingen gemaakt door Configuration Manager  
 Configuration Manager-clients of sitesystemen kunnen de volgende externe verbindingen maken:  

-   [Asset Intelligence-synchronisatiepunt-- &gt; Microsoft](#BKMK_PortsAI)  

-   [Endpoint Protection-punt-- &gt; Internet](#BKMK_PortsEndpointProtection_Internet)  

-   [Client-- &gt; globale catalogus-domeincontroller](#BKMK_PortsClient-GCDC)  

-   [Configuration Manager-console-- &gt; Internet](#BKMK_PortsConsole-Internet)  

-   [Beheerpunt-- &gt; domeincontroller](#BKMK_PortsMP-DC)  

-   [Siteserver-- &gt; domeincontroller](#BKMK_PortsSite-DC)  

-   [Siteserver &lt;  --  &gt; verlenende certificeringsinstantie (CA)](#BKMK_PortsIssuingCA_SiteServer)  

-   [Software-updatepunt-- &gt; Internet](#BKMK_PortsSUP-Internet)  

-   [Software-updatepunt-- &gt; Upstream WSUS-Server](#BKMK_PortsSUP-WSUS)  

-   [Serviceverbindingspunt-- &gt; Microsoft Intune](#BKMK_PortsIntuneConnector-WindowsIntune)  

###  <a name="BKMK_IBCMports"></a> Installatievereisten voor sitesystemen die ondersteuning bieden voor internet-clients  
 Beheerpunten en distributiepunten die ondersteuning bieden voor clients op Internet, de software-updatepunt en het terugvalstatuspunt gebruiken de volgende poorten voor installatie en herstel:  

-   Siteserver--> sitesysteem: RPC-eindpunttoewijzing via UDP en TCP-poort 135.  

-   Siteserver--> sitesysteem: RPC dynamische TCP-poorten  

-   Siteserver &lt; --> sitesysteem: Server message blocks (SMB) via TCP-poort 445

Installaties van toepassingen en pakketten op distributiepunten vereisen de volgende RPC-poorten:  

-   Siteserver--> distributiepunt: RPC-eindpunttoewijzing via UDP en TCP-poort 135

-   Siteserver--> distributiepunt: RPC dynamische TCP-poorten  

Gebruik IPsec voor verkeer tussen de siteserver en sitesystemen. Als u de dynamische poorten moet beperken die worden gebruikt met RPC, kunt u het Microsoft RPC-configuratieprogramma (rpccfg.exe) gebruiken om een beperkt aantal poorten te configureren voor deze RPC-pakketten. Zie voor meer informatie over het RPC-configuratieprogramma [RPC configureren voor het gebruik van bepaalde poorten en deze poorten helpen beveiligen met behulp van IPsec](http://go.microsoft.com/fwlink/p/?LinkId=124096).  

> [!IMPORTANT]  
>  Voordat u deze sitesystemen installeert, zorg ervoor dat de remote registry-service wordt uitgevoerd op de sitesysteemserver en dat u een installatieaccount hebt opgegeven als het sitesysteem zich in een ander Active Directory-forest zonder een vertrouwensrelatie.  

###  <a name="BKMK_PortsClientInstall"></a> Poorten die worden gebruikt door de Configuration Manager-clientinstallatie  
Welke poorten worden gebruikt tijdens de clientinstallatie is afhankelijk van de implementatiemethode van de client. Zie voor een lijst met poorten voor iedere client-implementatiemethode **poorten die worden gebruikt tijdens de clientimplementatie van de Configuration Manager-** in de [Windows Firewall- en poortinstellingen voor clients in System Center Configuration Manager](../../../core/clients/deploy/windows-firewall-and-port-settings-for-clients.md) artikel. Zie voor meer informatie over het configureren van Windows Firewall op de client voor clientinstallatie en communicatie na de installatie [Windows Firewall- en poortinstellingen voor clients in System Center Configuration Manager](../../../core/clients/deploy/windows-firewall-and-port-settings-for-clients.md).  

###  <a name="BKMK_MigrationPorts"></a> Poorten die door de migratie worden gebruikt  
De siteserver waarop migratie gebruikt diverse poorten om verbinding met toepasselijke sites in de bronhiërarchie voor het verzamelen van gegevens van de bronsites SQL Server-databases en om distributiepunten te delen.  

 Zie voor meer informatie over deze poorten de [vereiste configuraties voor migratie](../../../core/migration/prerequisites-for-migration.md#BKMK_Required_Configurations) sectie het [vereisten voor migratie in System Center Configuration Manager](../../../core/migration/prerequisites-for-migration.md) artikel.  

###  <a name="BKMK_ServerPorts"></a> Poorten die door Windows Server worden gebruikt  
 De volgende tabel bevat enkele belangrijke poorten gebruikt door Windows Server samen met hun functies. Zie [Service overview and network port requirements for Windows (Service-overzicht en netwerkpoortvereisten voor het Windows Server-systeem)](http://go.microsoft.com/fwlink/p/?LinkID=123652)voor een volledig overzicht van Windows Server-services en netwerkpoortvereisten.  

|Beschrijving|UDP|TCP|  
|-----------------|---------|---------|  
|Domain Name System (DNS)|53|53|  
|Dynamic Host Configuration Protocol (DHCP)|67 en 68|--|  
|NetBIOS-naamomzetting|137|--|  
|NetBIOS Datagram-service|138|--|  
|NetBIOS-sessieservice|--|139|  
