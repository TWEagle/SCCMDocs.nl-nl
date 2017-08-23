---
title: "Ports utilisés par Configuration Manager | Microsoft Docs"
description: "Découvrez les ports requis et personnalisables qu’utilise System Center Configuration Manager pour les connexions."
ms.custom: na
ms.date: 3/20/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: c6777fb0-0754-4abf-8a1b-7639d23e9391
caps.latest.revision: "8"
caps.handback.revision: "0"
author: Brenduns
ms.author: brenduns
manager: angrobe
ms.openlocfilehash: 78caa69e10f5d386daab1e61e484d4d134469708
ms.sourcegitcommit: 51fc48fb023f1e8d995c6c4eacfda7dbec4d0b2f
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/07/2017
---
# <a name="ports-used-in-system-center-configuration-manager"></a>Ports utilisés dans System Center Configuration Manager

*S’applique à : System Center Configuration Manager (Current Branch)*

System Center Configuration Manager est un système client/serveur distribué. Du fait de la nature distribuée de Configuration Manager, il est possible d’établir des connexions entre les serveurs de site, les systèmes de site et les clients. Certaines connexions utilisent des ports qui ne sont pas configurables et certaines prennent en charge des ports personnalisés que vous spécifiez. Si vous utilisez une technologie de filtrage de port, telle que des pare-feu, des routeurs, des serveurs proxy ou IPSec, vous devez vérifier que les ports requis sont disponibles.  

> [!NOTE]  
>  Si vous prenez en charge les clients Internet par pontage SSL, parallèlement aux exigences de port, vous devrez peut-être également autoriser certains verbes et en-têtes HTTP pour traverser le pare-feu.   

 Les listes de ports ci-après sont utilisées par Configuration Manager et ne comportent aucune information relative aux services Windows standard, tels que les paramètres Stratégie de groupe pour les services de domaine Active Directory ou l’authentification Kerberos. Pour plus d'informations sur les ports et les services de Windows Server, voir [Vue d'ensemble des services et exigences du port réseau pour le système Windows Server](http://go.microsoft.com/fwlink/p/?LinkID=123652).  

##  <a name="BKMK_ConfigurablePorts"></a> Ports configurables  
 Configuration Manager vous permet de configurer les ports pour les types de communication suivants :  

-   Point du site web du catalogue des applications vers point de service web du catalogue des applications  

-   Point proxy d'inscription vers point d'inscription  

-   Client vers systèmes de site exécutant IIS  

-   Client à Internet (sous forme de paramètres du serveur proxy)  

-   Point de mise à jour logicielle à Internet (sous forme de paramètres du serveur proxy)  

-   Point de mise à jour logicielle à serveur WSUS  

-   Serveur de site à serveur de base de données de site  

-   Points de Reporting Services  

    > [!NOTE]  
    >  Les ports qui sont utilisés pour le rôle de système de site du point de Reporting Services sont configurés dans SQL Server Reporting Services. Ces ports sont ensuite utilisés par Configuration Manager pendant les communications à destination du point de Reporting Services. Veillez à passer en revue les ports qui définissent les informations de filtre IP pour les stratégies IPsec ou pour la configuration des pare-feu.  

Par défaut, le port HTTP utilisé pour la communication entre le client et le système de site est le port 80, et le port HTTPS par défaut est le port 443. Vous pouvez modifier les ports HTTP ou HTTPS de communication entre le client et le système de site pendant l’installation ou dans les propriétés de votre site Configuration Manager.  

Les ports qui sont utilisés pour le rôle de système de site du point de Reporting Services sont configurés dans SQL Server Reporting Services. Ces ports sont ensuite utilisés par Configuration Manager pendant les communications à destination du point de Reporting Services. Veillez à passer en revue ces ports quand vous définissez les informations de filtre IP pour les stratégies IPsec ou pour la configuration des pare-feu.  

##  <a name="BKMK_NonConfigurablePorts"></a> Ports non configurables  
Configuration Manager ne vous autorise pas à configurer des ports pour les types de communication suivants :  

-   Site à site  

-   Serveur de site à système de site  

-   Console Configuration Manager vers le fournisseur SMS  

-   Console Configuration Manager vers Internet  

-   Connexions aux services cloud tels que Microsoft Intune et les points de distribution cloud  

##  <a name="BKMK_CommunicationPorts"></a> Ports utilisés par les clients Configuration Manager et les systèmes de site  
Les sections suivantes détaillent les ports qui sont utilisés pour la communication dans Configuration Manager. Les flèches figurant dans les titres des sections indiquent le sens de la communication :  

-   -- > indique qu’un ordinateur initie la communication et que l’autre ordinateur répond toujours ;  

-   &lt; -- > indique que les deux ordinateurs peuvent initier la communication.  

###  <a name="BKMK_PortsAI"></a> Point de synchronisation Asset Intelligence -- > Microsoft  

|Description|UDP|TCP|  
|-----------------|---------|---------|  
|HTTPS (Secure Hypertext Transfer Protocol)|--|443|  

###  <a name="BKMK_PortsAI-to-SQL"></a> Point de synchronisation Asset Intelligence -- > SQL Server  

|Description|UDP|TCP|  
|-----------------|---------|---------|  
|SQL sur TCP|--|1433 (voir note 2, **autre port disponible**)|  

###  <a name="BKMK_PortsAppCatalogService-SQL"></a> Point de service Web du catalogue des applications -- > SQL Server  

|Description|UDP|TCP|  
|-----------------|---------|---------|  
|SQL sur TCP|--|1433 (voir note 2, **Autre port disponible**)|  

###  <a name="BKMK_PortsAppCatalogWebSitePoint_AppCatalogWebServicePoint"></a> Point du site Web du catalogue des applications -- > Point de service Web du catalogue des applications  

|Description|UDP|TCP|  
|-----------------|---------|---------|  
|HTTP (Hypertext Transfer Protocol)|--|80 (voir note 2, **Autre port disponible**)|  
|HTTPS (Secure Hypertext Transfer Protocol)|--|443 (voir note 2, **Autre port disponible**)|  

###  <a name="BKMK_PortsClient-AppCatalogWebsitePoint"></a> Client -- > Point du site Web du catalogue des applications  

|Description|UDP|TCP|  
|-----------------|---------|---------|  
|HTTP (Hypertext Transfer Protocol)|--|80 (voir note 2, **Autre port disponible**)|  
|HTTPS (Secure Hypertext Transfer Protocol)|--|443 (voir note 2, **Autre port disponible**)|  

###  <a name="BKMK_PortsClient-ClientWakeUp"></a> Client -- &gt; Client  
 En plus des ports répertoriés dans le tableau ci-dessous, le proxy de mise en éveil utilise également des messages de demande d’écho ICMP (Internet Control Message Protocol) d’un client à un autre, lorsque ceux-ci sont configurés pour utiliser le proxy de mise en éveil.

Cette communication permet de savoir si l'autre ordinateur client est en éveil sur le réseau. ICMP est parfois appelé commandes ping TCP/IP. ICMP ne dispose pas d'un numéro de protocole UDP ou TCP, et par conséquent, il ne figure pas dans le tableau suivant. Toutefois, les pare-feu d'hôte de ces ordinateurs clients ou les appareils réseau intervenant sur le sous-réseau doivent autoriser le trafic ICMP pour que la communication avec le proxy de mise en éveil aboutisse.  

|Description|UDP|TCP|  
|-----------------|---------|---------|  
|Éveil par appel réseau|9 (voir note 2, **Autre port disponible**)|--|  
|Proxy de mise en éveil|25536 (voir note 2, **Autre port disponible**)|--|  

###  <a name="BKMK_PortsClient-PolicyModule"></a> Client --&gt; Module de stratégie de Configuration Manager (service d'inscription d'appareils réseau)  

|Description|UDP|TCP|  
|-----------------|---------|---------|  
|HTTP (Hypertext Transfer Protocol)||80|  
|HTTPS (Secure Hypertext Transfer Protocol)|--|443|  

###  <a name="BKMK_PortsClient-CloudDP"></a> Client -- > Point de distribution cloud  

|Description|UDP|TCP|  
|-----------------|---------|---------|  
|HTTPS (Secure Hypertext Transfer Protocol)|--|443|  

###  <a name="BKMK_PortsClient-DP"></a> Client -- > Point de distribution  

|Description|UDP|TCP|  
|-----------------|---------|---------|  
|HTTP (Hypertext Transfer Protocol)|--|80 (voir note 2, **Autre port disponible**)|  
|HTTPS (Secure Hypertext Transfer Protocol)|--|443 (voir note 2, **Autre port disponible**)|  

###  <a name="BKMK_PortsClient-DP2"></a> Client -- > Point de distribution configuré pour la multidiffusion  

|Description|UDP|TCP|  
|-----------------|---------|---------|  
|SMB (Server Message Block)|--|445|  
|Protocole de multidiffusion|63000-64000|--|  

###  <a name="BKMK_PortsClient-DP3"></a> Client -- > Point de distribution configuré pour PXE  

|Description|UDP|TCP|  
|-----------------|---------|---------|  
|DHCP (Dynamic Host Configuration Protocol)|67 et 68|--|  
|TFTP (Trivial File Transfer Protocol)|69 (voir note 4, **Service Trivial FTP (TFTP)**)|--|  
|BINL (Boot Information Negotiation Layer)|4011|--|  

###  <a name="BKMK_PortsClient-FSP"></a> Client -- > Point d’état de secours  

|Description|UDP|TCP|  
|-----------------|---------|---------|  
|HTTP (Hypertext Transfer Protocol)|--|80 (voir note 2, **Autre port disponible**)|  

###  <a name="BKMK_PortsClient-GCDC"></a> Client -- > Contrôleur de domaine de catalogue global  
 Un client Configuration Manager ne contacte pas de serveur de catalogue global lorsqu'il s'agit d'un ordinateur d'un groupe de travail ou lorsqu'il est configuré pour les communications Internet uniquement.  

|Description|UDP|TCP|  
|-----------------|---------|---------|  
|LDAP de catalogue global|--|3268|  
|SSL LDAP de catalogue global|--|3269|  

###  <a name="BKMK_PortsClient-MP"></a> Client -- > Point de gestion  

|Description|UDP|TCP|  
|-----------------|---------|---------|  
|Notification du client (communication par défaut avant le basculement en HTTP ou HTTPS)|--|10123 (voir note 2, **Autre port disponible**)|  
|HTTP (Hypertext Transfer Protocol)|--|80 (voir note 2, **Autre port disponible**)|  
|HTTPS (Secure Hypertext Transfer Protocol)|--|443 (voir note 2, **Autre port disponible**)|  

###  <a name="BKMK_PortsClient-SUP"></a> Client -- > Point de mise à jour logicielle  

|Description|UDP|TCP|  
|-----------------|---------|---------|  
|HTTP (Hypertext Transfer Protocol)|--|80 ou 8530 (Voir la remarque 3, **Windows Server Update Services**)|  
|HTTPS (Secure Hypertext Transfer Protocol)|--|443 ou 8531 (Voir la remarque 3, **Windows Server Update Services**)|  

###  <a name="BKMK_PortsClient-SMP"></a> Client -- > Point de migration d’état  

|Description|UDP|TCP|  
|-----------------|---------|---------|  
|HTTP (Hypertext Transfer Protocol)|--|80 (voir note 2, **Autre port disponible**)|  
|HTTPS (Secure Hypertext Transfer Protocol)|--|443 (voir note 2, **Autre port disponible**)|  
|SMB (Server Message Block)|--|445|  

###  <a name="BKMK_PortsConsole-Client"></a> Console Configuration Manager -- > Client  

|Description|UDP|TCP|  
|-----------------|---------|---------|  
|Contrôle à distance (contrôle)|--|2701|  
|Assistance à distance (RDP et RTC)|--|3389|  

###  <a name="BKMK_PortsConsole-Internet"></a>Console Configuration Manager -- > Internet  

|Description|UDP|TCP|  
|-----------------|---------|---------|  
|HTTP (Hypertext Transfer Protocol)|--|80|  

###  <a name="BKMK_PortsConsole-RSP"></a> Console Configuration Manager -- > Point de Reporting Services  


|Description|UDP|TCP|
|-----------------|---------|---------|   
|HTTP (Hypertext Transfer Protocol)|--|80 (voir note 2, **Autre port disponible**)|  
|HTTPS (Secure Hypertext Transfer Protocol)|--|443 (voir note 2, **Autre port disponible**)|  

###  <a name="BKMK_PortsConsole-Site"></a> Console Configuration Manager -- > Serveur de site  

|Description|UDP|TCP|  
|-----------------|---------|---------|  
|RPC (connexion initiale à WMI pour localiser le système fournisseur)|--|135|  

###  <a name="BKMK_PortsConsole-Provider"></a> Console Configuration Manager -- > Fournisseur SMS  

|Description|UDP|TCP|  
|-----------------|---------|---------|  
|Mappeur de point de terminaison RPC|135|135|  
|RPC|--|DYNAMIQUE (voir la note 6, **Ports dynamiques**)|  

###  <a name="BKMK_PortsCertificateRegistationPoint_PolicyModule"></a> Module de stratégie de Configuration Manager (service d’inscription de périphériques réseau) -- > Point d’enregistrement de certificat  

|Description|UDP|TCP|  
|-----------------|---------|---------|  
|HTTPS (Secure Hypertext Transfer Protocol)|--|443 (voir note 2, **Autre port disponible**)|  

###  <a name="BKMK_PortsDist_MP"></a> Point de distribution -- > Point de gestion  
 Un point de distribution communique avec le point de gestion dans les scénarios suivants :  

-   Pour signaler l’état du contenu préparé  

-   Pour signaler les données de synthèse d'utilisation  

-   Pour signaler la validation du contenu  

-   Pour signaler l’état des téléchargements de packages (point de distribution d’extraction)

|Description|UDP|TCP|  
|-----------------|---------|---------|  
|HTTP (Hypertext Transfer Protocol)|--|80 (voir note 2, **Autre port disponible**)|  
|HTTPS (Secure Hypertext Transfer Protocol)|--|443 (voir note 2, **Autre port disponible**)|  

###  <a name="BKMK_PortsEndpointProtection_Internet"></a> Point Endpoint Protection -- > Internet  

|Description|UDP|TCP|  
|-----------------|---------|---------|  
|HTTP (Hypertext Transfer Protocol)|--|80|  

###  <a name="BKMK_PortsEP-to-SQL"></a> Point Endpoint Protection -- > SQL Server  

|Description|UDP|TCP|  
|-----------------|---------|---------|  
|SQL sur TCP|--|1433 (voir note 2, **Autre port disponible**)|  

###  <a name="BKMK_PortsEnrollmentProxyEnrollmentPoint"></a> Point proxy d’inscription -- > Point d’inscription  

|Description|UDP|TCP|  
|-----------------|---------|---------|  
|HTTPS (Secure Hypertext Transfer Protocol)|--|443 (voir note 2, **Autre port disponible**)|  

###  <a name="BKMK_PortsEnrollmentEnrollmentSQL"></a> Point d’inscription -- > SQL Server  

|Description|UDP|TCP|  
|-----------------|---------|---------|  
|SQL sur TCP|--|1433 (voir note 2, **Autre port disponible**)|  

###  <a name="BKMK_PortsExchangeConnectorHosted"></a> Connecteur du serveur Exchange Server -- &gt; Exchange Online  

|Description|UDP|TCP|  
|-----------------|---------|---------|  
|Gestion à distance de Windows via HTTPS|--|5986|  

###  <a name="BKMK_PortsExchangeConnectorOnPrem"></a> Connecteur du serveur Exchange Server -- > Serveur Exchange Server local  

|Description|UDP|TCP|  
|-----------------|---------|---------|  
|Gestion à distance de Windows via HTTP|--|5985|  

###  <a name="BKMK_PortsMacEnrollmentProxyPoint"></a> Ordinateur Mac -- > Point proxy d’inscription  

|Description|UDP|TCP|  
|-----------------|---------|---------|  
|HTTPS (Secure Hypertext Transfer Protocol)|--|443|  

###  <a name="BKMK_PortsMP-DC"></a> Point de gestion -- > Contrôleur de domaine  

|Description|UDP|TCP|  
|-----------------|---------|---------|  
|LDAP (Lightweight Directory Access Protocol)|--|389|  
|LDAP (connexion SSL [Secure Sockets Layer])|636|636|  
|LDAP de catalogue global|--|3268|  
|SSL LDAP de catalogue global|--|3269|  
|Mappeur de point de terminaison RPC|135|135|  
|RPC|--|DYNAMIQUE (voir la note 6, **Ports dynamiques**)|  

###  <a name="BKMK_PortsMP-Site"></a> Point de gestion &lt; -- > Serveur de site  
 (Voir remarque 5, **Communications entre le serveur de site et les systèmes de site**)  

|Description|UDP|TCP|  
|-----------------|---------|---------|  
|Mappeur de point de terminaison RPC|--|135|  
|RPC|--|DYNAMIQUE (voir la note 6, **Ports dynamiques**)|  
|SMB (Server Message Block)|--|445|  

###  <a name="BKMK_PortsMP-SQL"></a> Point de gestion -- > SQL Server  

|Description|UDP|TCP|  
|-----------------|---------|---------|  
|SQL sur TCP|--|1433 (voir note 2, **Autre port disponible**)|  

###  <a name="BKMK_PortsMobileDeviceClient-EnrollmentProxyPoint"></a> Appareil mobile -- > Point proxy d’inscription  

|Description|UDP|TCP|  
|-----------------|---------|---------|  
|HTTPS (Secure Hypertext Transfer Protocol)|--|443|  

###  <a name="BKMK_PortsMobileDeviceClient-WindowsIntune"></a> Appareil mobile -- > Microsoft Intune  

|Description|UDP|TCP|  
|-----------------|---------|---------|  
|HTTPS (Secure Hypertext Transfer Protocol)|--|443|  

###  <a name="BKMK_PortsRSP-SQL"></a> Point de Reporting Services -- > SQL Server  

|Description|UDP|TCP|  
|-----------------|---------|---------|  
|SQL sur TCP|--|1433 (voir note 2, **Autre port disponible**)|  

###  <a name="BKMK_PortsIntuneConnector-WindowsIntune"></a> Point de connexion de service -- > Microsoft Intune  

|Description|UDP|TCP|  
|-----------------|---------|---------|  
|HTTPS (Secure Hypertext Transfer Protocol)|--|443|
Pour plus d’informations, consultez [Conditions requises pour l’accès Internet](/sccm/core/servers/deploy/configure/about-the-service-connection-point#bkmk_urls) pour le point de connexion de service.

###  <a name="BKMK_PortsAppCatalogWebServicePoint_SiteServer"></a> Serveur de site &lt; -- > Point de service Web du catalogue des applications  

|Description|UDP|TCP|  
|-----------------|---------|---------|  
|SMB (Server Message Block)|--|445|  
|Mappeur de point de terminaison RPC|135|135|  
|RPC|--|DYNAMIQUE (voir la note 6, **Ports dynamiques**)|  

###  <a name="BKMK_PortsAppCatalogWebSitePoint_SiteServer"></a> Serveur de site &lt; -- > Point du site Web du catalogue des applications  

|Description|UDP|TCP|  
|-----------------|---------|---------|  
|SMB (Server Message Block)|--|445|  
|Mappeur de point de terminaison RPC|135|135|  
|RPC|--|DYNAMIQUE (voir la note 6, **Ports dynamiques**)|  

###  <a name="BKMK_PortsSite-AISP"></a> Serveur de site &lt; -- > Point de synchronisation Asset Intelligence  

|Description|UDP|TCP|  
|-----------------|---------|---------|  
|SMB (Server Message Block)|--|445|  
|Mappeur de point de terminaison RPC|135|135|  
|RPC|--|DYNAMIQUE (voir la note 6, **Ports dynamiques**)|  

###  <a name="BKMK_PortsSite-Client"></a> Serveur de site -- > Client  

|Description|UDP|TCP|  
|-----------------|---------|---------|  
|Éveil par appel réseau|9 (voir note 2, **Autre port disponible**)|--|  

###  <a name="BKMK_PortsSiteServer-CloudDP"></a> Serveur de site -- > Point de distribution cloud  

|Description|UDP|TCP|  
|-----------------|---------|---------|  
|HTTPS (Secure Hypertext Transfer Protocol)|--|443|  

###  <a name="BKMK_PortsSite-DP"></a> Serveur de site -- > Point de distribution  
 (Voir remarque 5, **Communications entre le serveur de site et les systèmes de site**)  

|Description|UDP|TCP|  
|-----------------|---------|---------|  
|SMB (Server Message Block)|--|445|  
|Mappeur de point de terminaison RPC|135|135|  
|RPC|--|DYNAMIQUE (voir la note 6, **Ports dynamiques**)|  

###  <a name="BKMK_PortsSite-DC"></a> Serveur de site -- > Contrôleur de domaine  

|Description|UDP|TCP|  
|-----------------|---------|---------|  
|LDAP (Lightweight Directory Access Protocol)|--|389|  
|LDAP (connexion SSL [Secure Sockets Layer])|636|636|  
|LDAP de catalogue global|--|3268|  
|SSL LDAP de catalogue global|--|3269|  
|Mappeur de point de terminaison RPC|135|135|  
|RPC|--|DYNAMIQUE (voir la note 6, **Ports dynamiques**)|  

###  <a name="BKMK_PortsCertificateRegistrationPoint_SiteServer"></a> Serveur de site &lt; -- > Point d’enregistrement de certificat  

|Description|UDP|TCP|  
|-----------------|---------|---------|  
|SMB (Server Message Block)|--|445|  
|Mappeur de point de terminaison RPC|135|135|  
|RPC|--|DYNAMIQUE (voir la note 6, **Ports dynamiques**)|  

###  <a name="BKMK_PortsEndpointProtection_SiteServer"></a> Serveur de site &lt; -- > Point Endpoint Protection  

|Description|UDP|TCP|  
|-----------------|---------|---------|  
|SMB (Server Message Block)|--|445|  
|Mappeur de point de terminaison RPC|135|135|  
|RPC|--|DYNAMIQUE (voir la note 6, **Ports dynamiques**)|  

###  <a name="BKMK_EnrollmentPoint_SiteServer"></a> Serveur de site &lt; -- > Point d’inscription  

|Description|UDP|TCP|  
|-----------------|---------|---------|  
|SMB (Server Message Block)|--|445|  
|Mappeur de point de terminaison RPC|135|135|  
|RPC|--|DYNAMIQUE (voir la note 6, **Ports dynamiques**)|  

###  <a name="BKMK_EnrollmentProxyPoint_SiteServer"></a> Serveur de site &lt; -- > Point proxy d’inscription  

|Description|UDP|TCP|  
|-----------------|---------|---------|  
|SMB (Server Message Block)|--|445|  
|Mappeur de point de terminaison RPC|135|135|  
|RPC|--|DYNAMIQUE (voir la note 6, **Ports dynamiques**)|  

###  <a name="BKMK_PortsSite-FSP"></a> Serveur de site &lt; -- > Point d’état de secours  
 (Voir remarque 5, **Communications entre le serveur de site et les systèmes de site**)  

|Description|UDP|TCP|  
|-----------------|---------|---------|  
|SMB (Server Message Block)|--|445|  
|Mappeur de point de terminaison RPC|135|135|  
|RPC|--|DYNAMIQUE (voir la note 6, **Ports dynamiques**)|  

###  <a name="BKMK_PortSite-Internet"></a> Serveur de site -- > Internet  

|Description|UDP|TCP|  
|-----------------|---------|---------|  
|HTTP (Hypertext Transfer Protocol)|--|80 (voir note 1, **Port de serveur proxy**)|  

###  <a name="BKMK_PortsIssuingCA_SiteServer"></a> Serveur de site &lt; -- > Autorité de certification (CA) émettrice  
 Cette communication est utilisée lorsque vous déployez des profils de certificat à l'aide du point d'enregistrement de certificat. La communication n’est pas utilisée pour chaque serveur de site de la hiérarchie. En fait, elle est utilisée uniquement pour le serveur de site situé en haut de la hiérarchie.  

|Description|UDP|TCP|  
|-----------------|---------|---------|  
|Mappeur de point de terminaison RPC|135|135|  
|RPC (DCOM)|--|DYNAMIQUE (voir la note 6, **Ports dynamiques**)|  

###  <a name="BKMK_PortsSite-RSP"></a> Serveur de site &lt; -- > Point de Reporting Services  
 (Voir remarque 5, **Communications entre le serveur de site et les systèmes de site**)  

|Description|UDP|TCP|  
|-----------------|---------|---------|  
|SMB (Server Message Block)|--|445|  
|Mappeur de point de terminaison RPC|135|135|  
|RPC|--|DYNAMIQUE (voir la note 6, **Ports dynamiques**)|  

###  <a name="BKMK_PortsSite-Site"></a> Serveur de site &lt; -- > Serveur de site  

|Description|UDP|TCP|  
|-----------------|---------|---------|  
|SMB (Server Message Block)|--|445|  

###  <a name="BKMK_PortsSite-SQL"></a> Serveur de site -- > SQL Server  

|Description|UDP|TCP|  
|-----------------|---------|---------|  
|SQL sur TCP|--|1433 (voir note 2, **Autre port disponible**)|  

 Lors de l’installation d’un site utilisant une instance SQL Server distante pour héberger la base de données de site, vous devez ouvrir les ports suivants entre le serveur de site et l’instance SQL Server :  

|Description|UDP|TCP|  
|-----------------|---------|---------|  
|SMB (Server Message Block)|--|445|  
|Mappeur de point de terminaison RPC|135|135|  
|RPC|--|DYNAMIQUE (voir la note 6, **Ports dynamiques**)|  

###  <a name="BKMK_PortsSite-Provider"></a> Serveur de site -- > Fournisseur SMS  

|Description|UDP|TCP|  
|-----------------|---------|---------|  
|SMB (Server Message Block)|--|445|  
|Mappeur de point de terminaison RPC|135|135|  
|RPC|--|DYNAMIQUE (voir la note 6, **Ports dynamiques**)|  

###  <a name="BKMK_PortsSite-SUP"></a> Serveur de site &lt; -- > Point de mise à jour logicielle  
 (Voir remarque 5, **Communications entre le serveur de site et les systèmes de site**)  

|Description|UDP|TCP|  
|-----------------|---------|---------|  
|SMB (Server Message Block)|--|445|  
|HTTP (Hypertext Transfer Protocol)|--|80 ou 8530 (Voir la remarque 3, **Windows Server Update Services**)|  
|HTTPS (Secure Hypertext Transfer Protocol)|--|443 ou 8531 (Voir la remarque 3, **Windows Server Update Services**)|  

###  <a name="BKMK_PortsSite-SMP"></a> Serveur de site &lt; -- > Point de migration d’état  
 (Voir remarque 5, **Communications entre le serveur de site et les systèmes de site**)  

|Description|UDP|TCP|  
|-----------------|---------|---------|  
|SMB (Server Message Block)|--|445|  
|Mappeur de point de terminaison RPC|135|135|  

###  <a name="BKMK_PortsProvider-SQL"></a> Fournisseur SMS -- &gt; SQL Server  

|Description|UDP|TCP|  
|-----------------|---------|---------|  
|SQL sur TCP|--|1433 (voir note 2, **Autre port disponible**)|  

###  <a name="BKMK_PortsSUP-Internet"></a> Point de mise à jour logicielle -- > Internet  

|Description|UDP|TCP|  
|-----------------|---------|---------|  
|HTTP (Hypertext Transfer Protocol)|--|80 (voir note 1, **Port de serveur proxy**)|  

###  <a name="BKMK_PortsSUP-WSUS"></a> Point de mise à jour logicielle -- > Serveur WSUS en amont  

|Description|UDP|TCP|  
|-----------------|---------|---------|  
|HTTP (Hypertext Transfer Protocol)|--|80 ou 8530 (Voir la remarque 3, **Windows Server Update Services**)|  
|HTTPS (Secure Hypertext Transfer Protocol)|--|443 ou 8531 (Voir la remarque 3, **Windows Server Update Services**)|  

###  <a name="BKMK_PortsSQL-SQL"></a> SQL Server --&gt; SQL Server  
 La réplication inter-sites de base de données exige que le serveur SQL Server d’un site communique directement avec le serveur SQL Server de son site parent ou enfant.  

|Description|UDP|TCP|  
|-----------------|---------|---------|  
|Service SQL Server|--|1433 (voir note 2, **Autre port disponible**)|  
|Service Broker SQL Server|--|4022 (voir note 2, **Autre port disponible**)|  

> [!TIP]  
>  Configuration Manager ne nécessite pas le navigateur SQL Server, qui utilise le port UDP 1434.  

###  <a name="BKMK_PortsStateMigrationPoint-to-SQL"></a> Point de migration d’état -- > SQL Server  

|Description|UDP|TCP|  
|-----------------|---------|---------|  
|SQL sur TCP|--|1433 (voir note 2, **Autre port disponible**)|  



###  <a name="BKMY_PortNotes"></a> Notes pour les ports utilisés par les clients Configuration Manager et les systèmes de site  

1.  **Port de serveur proxy** : ce port ne peut pas être configuré, mais il peut être routé via un serveur proxy configuré.  

2.  **Autre port disponible** : un autre port peut être défini dans Configuration Manager pour cette valeur. Si un port personnalisé a été défini, remplacez-le lorsque vous définissez les informations de filtre IP pour les stratégies IPsec ou pour configurer les pare-feu.  

3.  **Windows Server Update Services (WSUS)** : WSUS peut être installé pour utiliser les ports 80/443 ou 8530/8531 pour la communication client. Quand vous exécutez WSUS dans Windows Server 2012 ou Windows Server 2016, WSUS est configuré par défaut pour utiliser le port 8530 pour HTTP et le port 8531 pour HTTPS.  

     Ce port peut être modifié après l'installation. Vous n'avez pas à utiliser le même numéro de port dans l'ensemble de la hiérarchie du site.  

    -   Si le numéro de port HTTP est 80, le numéro de port HTTPS doit être 443.  

    -   Si le port HTTP a un autre numéro, le port HTTPS doit avoir le numéro 1 ou plus (par exemple 8530 et 8531).   

    > [!NOTE]  
    >  Quand vous configurez le point de mise à jour logicielle pour utiliser HTTPS, le port HTTP doit également être ouvert. Les données non chiffrées, telles que le CLUF pour les mises à jour spécifiques, utilisent le port HTTP.  

4.  **Service Trivial FTP (TFTP)** : le service système Trivial FTP ne nécessite pas de nom d’utilisateur ni de mot de passe, et il fait partie intégrante des services de déploiement Windows (WDS). Le service Trivial FTP met en œuvre la prise en charge du protocole TFTP qui est défini par les normes RFC suivantes :  

    -   RFC 350  : TFTP  

    -   RFC 2347 : extension d’option  

    -   RFC 2348 : option de taille de bloc  

    -   RFC 2349 : options d’intervalle de délai d’attente et de taille de transfert  

     Le protocole Trivial FTP est conçu pour prendre en charge les environnements de démarrage sans disque. Les services Trivial FTP écoutent au port UDP 69 mais répondent à partir d'un port à numéro élevé alloué de manière dynamique. Ainsi, l’activation de ce port permet au service TFTP de recevoir les demandes TFTP entrantes mais n’autorise pas le serveur sélectionné à répondre à ces demandes. Vous ne pouvez pas permettre au serveur sélectionné de répondre aux demandes TFTP entrantes, à moins que le serveur TFTP soit configuré de manière à répondre à partir du port 69.  

5.  **Communications entre le serveur de site et les systèmes de site**: par défaut, les communications entre le serveur de site et les systèmes de site sont bidirectionnelles. Le serveur de site initialise la communication pour configurer le système de site, puis la plupart des systèmes de site se connectent à leur tour au serveur de site pour envoyer des informations d'état. Les points de Reporting Services et les points de distribution n'envoient pas d'informations d'état. Si vous sélectionnez **Exiger que le serveur de site démarre les connexions vers ce système de site** dans les propriétés du système de site, après l’installation du système de site, ce dernier n’établit pas la communication vers le système de site. Au lieu de cela, le serveur de site initie la communication et utilise le compte d’installation du système de site pour l’authentification auprès du serveur de système de site.  

6.  **Ports dynamiques** : les ports dynamiques (également appelés ports éphémères) utilisent une plage de numéros de port qui est définie par la version du système d’exploitation. Pour plus d'informations sur les plages de port par défaut, voir [Vue d'ensemble des services et exigences de ports réseau pour le système Windows Server](http://go.microsoft.com/fwlink/p/?LinkId=317965).  

##  <a name="BKMK_AdditionalPorts"></a> Listes de ports supplémentaires  
 Les sections suivantes fournissent des informations supplémentaires sur les ports utilisés par Configuration Manager.  

###  <a name="BKMK_ClientShares"></a> Client vers partages serveur  
 Les clients utilisent le protocole SMB (Server Message Block) à chaque fois qu'ils se connectent à des partages UNC. Exemple :  

-   Installation manuelle du client spécifiant la propriété de ligne de commande CCMSetup.exe **/source:**  

-   Clients Endpoint Protection qui téléchargent des fichiers de définition à partir d’un chemin UNC

|Description|UDP|TCP|  
|-----------------|---------|---------|  
|SMB (Server Message Block)|--|445|  

###  <a name="BKMK_SQLPorts"></a> Connexions à Microsoft SQL Server  
 Pour la communication vers le moteur de base de données SQL Server et pour la réplication intersite, vous pouvez utiliser le port de SQL Server par défaut ou spécifier des ports personnalisés :  

-   Utilisation des communications intersites :  

    -   SQL Server Service Broker, qui utilise par défaut le port TCP 4022.  

    -   Service SQL Server, qui utilise par défaut le port TCP 1433.  

-   Les communications intrasites entre le moteur de base de données SQL Server et divers rôles de système de site Configuration Manager utilisent par défaut le port TCP 1433.  

- Configuration Manager utilise les mêmes ports et protocoles pour communiquer avec chaque réplica du groupe de disponibilité SQL qui héberge la base de données comme si le réplica était une instance SQL Server autonome.

Quand vous utilisez Azure et que la base de données de site se trouve derrière un équilibreur de charge interne ou externe, configurez les exceptions de pare-feu suivantes sur chaque réplica et ajoutez des règles d’équilibrage de charge pour les ports suivants :
 - SQL sur TCP : TCP 1433
 - SQL Server Service Broker : TCP 4022
 - Server Message Block (SMB) : TCP 445
 - Mappeur de point de terminaison RPC : TCP 135

> [!WARNING]  
>  Configuration Manager ne prend pas en charge les ports dynamiques. Étant donné que les instances nommées de SQL Server utilisent par défaut des ports dynamiques pour les connexions au moteur de base de données, lorsque vous utilisez une instance nommée, vous devez configurer manuellement le port statique que vous souhaitez utiliser pour la communication intrasite.  

 Les rôles de système de site suivants communiquent directement avec la base de données SQL Server :  

-   Point de service Web du catalogue des applications  

-   Rôle de point d'enregistrement de certificat  

-   Rôle de point d'inscription  

-   Point de gestion  

-   Serveur de site  

-   Point de Reporting Services  

-   fournisseur SMS  

-   SQL Server --> SQL Server  

Lorsqu'un SQL Server héberge une base de données provenant de plusieurs sites, chaque base de données doit utiliser une instance distincte de SQL Server, et chaque instance doit être configurée avec un ensemble de ports unique.  

Si un pare-feu est activé sur l’ordinateur SQL Server, assurez-vous qu’il est configuré pour autoriser les ports utilisés par votre déploiement. Configurez également les pare-feu situés à d’autres emplacements sur le réseau, entre les ordinateurs qui communiquent avec le serveur SQL Server, de manière à autoriser ces ports.  

Pour obtenir un exemple montrant comment configurer SQL Server pour utiliser un port spécifique, consultez [Configurer un serveur pour écouter un port TCP spécifique (Gestionnaire de configuration SQL Server)](http://go.microsoft.com/fwlink/p/?LinkID=226349) dans la bibliothèque TechNet relative à SQL Server.  


### <a name="bkmk_discovery"> </a> Découverte et publication
Les ports suivants sont utilisés pour la découverte et la publication d’informations de site :
 - LDAP (Lightweight Directory Access Protocol) : 389
 - LDAP (connexion SSL [Secure Sockets Layer]) : 636


 - LDAP de catalogue global : 3268
 - SSL LDAP de catalogue global : 3269


 - Mappeur de point de terminaison RPC : 135
 - RPC : ports TCP à numéro élevé alloués dynamiquement


 - TCP : 1024 : 5000
 - TCP :  49152 : 65535


###  <a name="BKMK_External"></a> Connexions externes effectuées par Configuration Manager  
 Les clients ou les systèmes de site Configuration Manager peuvent établir les connexions externes suivantes :  

-   [Point de synchronisation Asset Intelligence -- &gt; Microsoft](#BKMK_PortsAI)  

-   [Point Endpoint Protection -- &gt; Internet](#BKMK_PortsEndpointProtection_Internet)  

-   [Client -- &gt; Contrôleur de domaine de catalogue global](#BKMK_PortsClient-GCDC)  

-   [Console Configuration Manager -- &gt; Internet](#BKMK_PortsConsole-Internet)  

-   [Point de gestion -- &gt; Contrôleur de domaine](#BKMK_PortsMP-DC)  

-   [Serveur de site -- &gt; Contrôleur de domaine](#BKMK_PortsSite-DC)  

-   [Serveur de site &lt; -- &gt; Autorité de certification (CA) émettrice](#BKMK_PortsIssuingCA_SiteServer)  

-   [Point de mise à jour logicielle -- &gt; Internet](#BKMK_PortsSUP-Internet)  

-   [Point de mise à jour logicielle -- &gt; Serveur WSUS en amont](#BKMK_PortsSUP-WSUS)  

-   [Point de connexion de service -- &gt; Microsoft Intune](#BKMK_PortsIntuneConnector-WindowsIntune)  

###  <a name="BKMK_IBCMports"></a> Configuration requise pour les systèmes de site qui prennent en charge les clients Internet  
 Les points de gestion et les points de distribution qui prennent en charge les clients Internet, le point de mise à jour logicielle et le point d’état de secours utilisent les ports suivants pour l’installation et la réparation :  

-   Serveur de site --> Système de site : mappeur de point de terminaison RPC utilisant le port UDP et TCP 135  

-   Serveur de site --> Système de site : ports TCP RPC dynamiques  

-   Serveur de site &lt; --> Système de site : protocole SMB (Server Message Blocks) utilisant le port TCP 445

Les installations d'applications et de packages sur les points de distribution nécessitent les ports RPC suivants :  

-   Serveur de site --> Point de distribution : mappeur de point de terminaison RPC utilisant le port UDP et TCP 135

-   Serveur de site --> Point de distribution : ports TCP RPC dynamiques  

Utilisez IPsec pour sécuriser le trafic entre le serveur de site et les systèmes de site. Si vous devez restreindre les ports dynamiques utilisés par RPC, vous pouvez employer l'outil de configuration Microsoft RPC (rpccfg.exe) pour configurer une plage de ports limitée à ces paquets RPC. Pour plus d'informations sur l'outil de configuration RPC, voir [Comment configurer RPC pour qu'il utilise certains ports et comment sécuriser ces ports à l'aide d'IPsec](http://go.microsoft.com/fwlink/p/?LinkId=124096).  

> [!IMPORTANT]  
>  Avant d'installer ces systèmes de site, vérifiez que le service d'accès à distance au Registre est en cours d'exécution sur le serveur de système de site et que vous avez spécifié un compte d'installation du système de site si le système de site est situé dans une autre forêt Active Directory sans relation d'approbation.  

###  <a name="BKMK_PortsClientInstall"></a> Ports utilisés par l’installation du client Configuration Manager  
Les ports utilisés lors de l'installation du client dépendent de la méthode de déploiement du client. Pour obtenir la liste des ports utilisés pour chaque méthode de déploiement de client, consultez **Ports utilisés lors du déploiement du client de Configuration Manager** dans la rubrique [Paramètres de port et de pare-feu Windows pour les clients dans System Center Configuration Manager](../../../core/clients/deploy/windows-firewall-and-port-settings-for-clients.md). Pour plus d’informations sur la configuration du Pare-feu Windows sur le client pour l’installation du client et la communication après l’installation, consultez [Paramètres de port et de pare-feu Windows pour les clients dans System Center Configuration Manager](../../../core/clients/deploy/windows-firewall-and-port-settings-for-clients.md).  

###  <a name="BKMK_MigrationPorts"></a> Ports utilisés par la migration  
Le serveur de site qui exécute la migration utilise plusieurs ports pour se connecter aux sites applicables dans la hiérarchie source, pour recueillir des données à partir des bases de données SQL Server des sites sources et pour partager des points de distribution.  

 Pour plus d’informations sur ces ports, consultez la section [Configurations requises pour la migration](../../../core/migration/prerequisites-for-migration.md#BKMK_Required_Configurations) dans la rubrique [Prérequis de la migration dans System Center Configuration Manager](../../../core/migration/prerequisites-for-migration.md).  

###  <a name="BKMK_ServerPorts"></a> Ports utilisés par Windows Server  
 Le tableau suivant répertorie certains ports principaux utilisés par Windows Server, ainsi que leurs fonctions respectives. Pour une liste plus complète des services Windows Server et les exigences des ports réseau, voir [Vue d'ensemble des services et exigences du port réseau pour le système Windows Server](http://go.microsoft.com/fwlink/p/?LinkID=123652).  

|Description|UDP|TCP|  
|-----------------|---------|---------|  
|DNS (Domain Name System)|53|53|  
|DHCP (Dynamic Host Configuration Protocol)|67 et 68|--|  
|Résolution de noms Netbios|137|--|  
|Service de datagramme NetBIOS|138|--|  
|Service de session NETBIOS|--|139|  
