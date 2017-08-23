---
title: "Prérequis des sites | Microsoft Docs"
description: "Découvrez comment configurer un ordinateur Windows comme serveur de système de site System Center Configuration Manager."
ms.custom: na
ms.date: 1/17/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 1392797b-76cb-46b4-a3e4-8f349ccaa078
caps.latest.revision: "5"
author: Brenduns
ms.author: brenduns
manager: angrobe
ms.openlocfilehash: 0b1d2d619d6cdaf36cc22ef461ea1505b5cacc41
ms.sourcegitcommit: 51fc48fb023f1e8d995c6c4eacfda7dbec4d0b2f
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/07/2017
---
# <a name="site-and-site-system-prerequisites-for-system-center-configuration-manager"></a>Prérequis des sites et systèmes de site pour System Center Configuration Manager

*S’applique à : System Center Configuration Manager (Current Branch)*


 Les ordinateurs Windows nécessitent des configurations spécifiques pour pouvoir être utilisés comme serveurs de système de site System Center Configuration Manager.  


 Dans certains cas, par exemple Windows Server Update Services (WSUS) pour le point de mise à jour logicielle, vous devez vous référer à la documentation du produit pour connaître les prérequis et limitations supplémentaires liés à son utilisation. Cet article porte uniquement sur les configurations qui s’appliquent directement à l’utilisation de Configuration Manager.   

> [!NOTE]  
>  Depuis janvier 2016, le support n’est plus assuré pour .NET Framework 4.0, 4.5 et 4.5.1. Pour plus d’informations, consultez [Forum Aux Questions sur la politique de support - Microsoft .NET Framework](https://support.microsoft.com/gp/framework_faq?WT.mc_id=azurebg_email_Trans_943_NET452_Update) à l’adresse support.microsoft.com.  

## <a name="bkmk_generalprerewq"></a> Configuration requise et limitations générales du serveur de site
**Ce qui suit s’applique à tous les serveurs de système de site :**

-   Chaque serveur de système de site doit utiliser un système d’exploitation 64 bits. La seule exception est le rôle de système de site du point de distribution, que vous pouvez installer sur certains systèmes d’exploitation 32 bits.  

-   Les systèmes de site ne sont pas pris en charge sur des installations minimales pour les systèmes d’exploitation suivants : Une exception à cette règle est que les installations minimales sont prises en charge pour le rôle de système de site du point de distribution, sans prise en charge de PXE ou de la multidiffusion.  

-   Une fois que vous avez installé un serveur de système de site, vous ne pouvez plus modifier les éléments suivants :  

    -   Le nom du domaine où se trouve l’ordinateur du système de site (également appelé **changement de nom de domaine**).  

    -   L’appartenance de l’ordinateur au domaine.  

    -   Nom de l’ordinateur.  

  Si vous devez modifier ces éléments, vous devez d’abord supprimer le rôle système de site sur l’ordinateur, puis réinstaller les rôles une fois la modification effectuée. Si ceci a une incidence sur l'ordinateur du serveur de site, vous devez désinstaller le site, puis le réinstaller une fois la modification effectuée.  

-   Les rôles de système de site ne sont pas pris en charge sur une instance de cluster Windows Server. La seule exception est le serveur de base de données de site.  

-   Vous ne pouvez pas modifier le type de démarrage ou les paramètres d’ouverture de session pour un service Configuration Manager. Si vous le faites, vous risquez d’empêcher des services clés de s’exécuter correctement.  

##  <a name="bkmk_2012Prereq"></a> Conditions préalables pour les systèmes d’exploitation Windows Server 2012 et versions ultérieures  
###  <a name="bkmk_2012sspreq"></a> Serveur de site : site d’administration centrale et site principal  
  **Rôles et fonctionnalités Windows Server :**  

-   .NET Framework 3.5 SP1 (ou version ultérieure)  

-   .NET Framework 4.5.2  

-   Compression différentielle à distance  

**Windows ADK :**  

-   Avant d’installer ou de mettre à niveau un site d’administration centrale ou un site principal, vous devez installer la version du Kit de déploiement et d’évaluation Windows (ADK) nécessaire pour la version de Configuration Manager que vous installez ou vers laquelle vous effectuez une mise à niveau.  

    -   La version 1511 de Configuration Manager nécessite la version Windows 10 RTM (10.0.10240) de Windows ADK.  

-   Pour plus d’informations sur cette configuration requise, consultez [Configuration requise de l’infrastructure pour le déploiement de système d’exploitation](/sccm/osd/plan-design/infrastructure-requirements-for-operating-system-deployment).  

**Redistribuable Visual C++ :**  

-   Configuration Manager installe Microsoft Visual C++ 2013 Redistributable Package sur chaque ordinateur sur lequel est installé un serveur de site.  

-   Les sites d'administration centrale et les sites principaux requièrent à la fois les versions x86 et x64 du fichier redistribuable applicable.  

###  <a name="bkmk_2012secpreq"></a> Serveur de site : site secondaire  
**Rôles et fonctionnalités Windows Server :**  

-   .NET Framework 3.5 SP1 (ou version ultérieure)  

-   .NET Framework 4.5.2  

-   Compression différentielle à distance  

**Redistribuable Visual C++ :**  

-   Configuration Manager installe Microsoft Visual C++ 2013 Redistributable Package sur chaque ordinateur sur lequel est installé un serveur de site.  

-   Les sites secondaires requièrent seulement la version x64.  

**Rôles de système de site par défaut :**  

-   Par défaut, un site secondaire installe un **point de gestion** et un **point de distribution**.  

-   Assurez-vous que le serveur de site secondaire remplit les conditions préalables pour ces rôles de système de site.  

###  <a name="bkmk_2012dbpreq"></a> Serveur de base de données  
**Service d’accès à distance au Registre :**  

-   Durant l’installation du site Configuration Manager, vous devez activer le service d’accès à distance au Registre sur l’ordinateur qui hébergera la base de données du site.  

**SQL Server :**  

-   Avant d’installer un site d’administration centrale ou un site principal, vous devez installer une version prise en charge de SQL Server pour héberger la base de données du site.  

-   Avant d’installer un site secondaire, vous pouvez installer une version prise en charge de SQL Server.  

-   Si vous souhaitez que Configuration Manager installe SQL Server Express en même temps que le site secondaire, vérifiez que l’ordinateur présente la configuration requise pour exécuter SQL Server Express.  

###  <a name="bkmk_2012smsprovpreq"></a> Serveur de fournisseur SMS  
**Windows ADK :**  

-   L’ordinateur sur lequel vous installez une instance du fournisseur SMS doit disposer de la version de Windows ADK nécessaire à la version de Configuration Manager que vous installez ou vers laquelle vous effectuez une mise à niveau.  

    -   La version 1511 de Configuration Manager nécessite la version Windows 10 RTM (10.0.10240) de Windows ADK.  

-   Pour plus d’informations sur cette configuration requise, consultez [Configuration requise de l’infrastructure pour le déploiement de système d’exploitation](/sccm/osd/plan-design/infrastructure-requirements-for-operating-system-deployment).  

###  <a name="bkmk_2012acwspreq"></a> Point du site web du catalogue des applications  
**Rôles et fonctionnalités Windows Server :**  

-   .NET Framework 3.5 SP1 (ou version ultérieure)  

-   .NET Framework 4.5.2 :  

    -   ASP.NET 4.5  

**Configuration IIS :**  

-   Fonctionnalités HTTP communes :  

    -   Document par défaut  

    -   Contenu statique  

-   Développement d'applications :  

    -   ASP.NET 3.5 (et les options sélectionnées automatiquement)  

    -   ASP.NET 4.5 (et les options sélectionnées automatiquement)  

    -   Extensibilité .NET 3.5  

    -   Extensibilité .NET 4.5  

-   Sécurité :  

    -   Authentification Windows  

-   Compatibilité avec la gestion IIS 6 :  

    -   Compatibilité avec la métabase de données IIS 6  

###  <a name="bkmk_2012ACwsitepreq"></a> Point de service web du catalogue des applications  
**Rôles et fonctionnalités Windows Server :**  

-   .NET Framework 3.5 SP1 (ou version ultérieure)  

-   .NET Framework 4.5.2 :  

    -   ASP.NET 4.5 :  

        -   Activation de HTTP (et des options sélectionnées automatiquement)  

**Configuration IIS :**  

-   Fonctionnalités HTTP communes :  

    -   Document par défaut  

-   Compatibilité avec la gestion IIS 6 :  

    -   Compatibilité avec la métabase de données IIS 6  

-   Développement d'applications :  

    -   ASP.NET 3.5 (et les options sélectionnées automatiquement)  

    -   Extensibilité .NET 3.5  

    -   ASP.NET 4.5 (et les options sélectionnées automatiquement)  

    -   Extensibilité .NET 4.5  

**Mémoire de l’ordinateur :**  

-   L’ordinateur hébergeant ce rôle de système de site doit avoir au moins 5 % de mémoire disponible pour permettre au rôle de système de site de traiter les demandes.  

-   Quand ce rôle de système de site coexiste avec un autre rôle de système de site qui a cette même exigence, la quantité de mémoire disponible requise pour l’ordinateur n’augmente pas, mais elle reste à un minimum de 5 %.  

###  <a name="bkmk_2012AIpreq"></a> Point de synchronisation Asset Intelligence  
**Rôles et fonctionnalités Windows Server :**  

-   .NET Framework 4.5.2  

###  <a name="bkmk_2012crppreq"></a> Point d’enregistrement de certificat  
**Rôles et fonctionnalités Windows Server :**  

-   .NET Framework 4.5.2 :  

    -   Activation HTTP  

**Configuration IIS :**  

-   Développement d'applications :  

    -   ASP.NET 3.5 (et les options sélectionnées automatiquement)  

    -   ASP.NET 4.5 (et les options sélectionnées automatiquement)  

-   Compatibilité avec la gestion IIS 6 :  

    -   Compatibilité avec la métabase de données IIS 6  

    -   Compatibilité WMI d'IIS 6  

###  <a name="bkmk_2012dppreq"></a> Point de distribution  
**Rôles et fonctionnalités Windows Server :**  

-   Compression différentielle à distance  

**Configuration IIS :**  

-   Développement d'applications :  

    -   Extensions ISAPI  

-   Sécurité :  

    -   Authentification Windows  

-   Compatibilité avec la gestion IIS 6 :  

    -   Compatibilité avec la métabase de données IIS 6  

    -   Compatibilité WMI d'IIS 6  

**PowerShell :**  

-   Sur Windows Server 2012 et les versions ultérieures, PowerShell 3.0 ou 4.0 est nécessaire pour pouvoir installer le point de distribution.  

**Redistribuable Visual C++ :**  

-   Configuration Manager installe Microsoft Visual C++ 2013 Redistributable Package sur chaque ordinateur hébergeant un point de distribution.  

-   La version installée dépend de la plateforme de l’ordinateur (x86 ou x64).  

**Microsoft Azure :**  

-   Pour héberger un point de distribution, vous pouvez utiliser un service cloud dans Microsoft Azure.  

**Pour prendre en charge PXE ou la multidiffusion :**  

-   Installez et configurez le rôle WDS (Windows Deployment Services) de Windows Server.  

    > [!NOTE]  
    >  WDS s’installe et se configure automatiquement quand vous configurez un point de distribution pour prendre en charge PXE ou la multidiffusion sur un serveur exécutant Windows Server 2012 ou une version ultérieure.  

> [!NOTE]  
> Le rôle de système de site du point de distribution ne nécessite pas le service de transfert intelligent en arrière-plan (BITS). Quand BITS est configuré sur l’ordinateur du point de distribution, il n’est pas utilisé pour faciliter le téléchargement de contenu par les clients qui utilisent BITS.  

###  <a name="bkmk_2012EPPpreq"></a> Point Endpoint Protection  
**Rôles et fonctionnalités Windows Server :**  

-   .NET Framework 3.5 SP1 (ou version ultérieure)  

###  <a name="bkmk_2012Enrollpreq"></a> Point d’inscription  
**Rôles et fonctionnalités Windows Server :**  

-   .NET Framework 3.5 (ou version ultérieure).  

-   .NET Framework 4.5.2 :  

     Pendant l’installation de ce rôle de système de site, Configuration Manager installe automatiquement .NET Framework 4.5.2. Cette installation peut placer le serveur dans un état d’attente redémarrage. Quand un redémarrage est en attente pour .NET Framework, il est possible que les applications .NET ne puissent pas s’exécuter tant que le serveur n’a pas redémarré et que l’installation n’est pas terminée.  

    -   Activation de HTTP (et des options sélectionnées automatiquement)  

    -   ASP.NET 4.5  


**Configuration IIS :**  

-   Fonctionnalités HTTP communes :  

    -   Document par défaut  

-   Développement d'applications :  

    -   ASP.NET 3.5 (et les options sélectionnées automatiquement)  

    -   Extensibilité .NET 3.5  

    -   ASP.NET 4.5 (et les options sélectionnées automatiquement)  

    -   .NET Extensibility 4.5  

-   Compatibilité avec la gestion IIS 6 :  

    -   Compatibilité avec la métabase de données IIS 6  

**Mémoire de l’ordinateur :**  

-   L’ordinateur hébergeant ce rôle de système de site doit avoir au moins 5 % de mémoire disponible pour permettre au rôle de système de site de traiter les demandes.  

-   Quand ce rôle de système de site coexiste avec un autre rôle de système de site qui a cette même exigence, la quantité de mémoire disponible requise pour l’ordinateur n’augmente pas, mais elle reste à un minimum de 5 %.  

###  <a name="bkmk_2012EnrollProxpreq"></a> Point proxy d’inscription  
**Rôles et fonctionnalités Windows Server :**  

-   .NET Framework 3.5 (ou version ultérieure).  

-   .NET Framework 4.5.2  

     Pendant l’installation de ce rôle de système de site, Configuration Manager installe automatiquement .NET Framework 4.5.2. Cette installation peut placer le serveur dans un état d’attente redémarrage. Quand un redémarrage est en attente pour .NET Framework, il est possible que les applications .NET ne puissent pas s’exécuter tant que le serveur n’a pas redémarré et que l’installation n’est pas terminée.  

**Configuration IIS :**  

-   Fonctionnalités HTTP communes :  

    -   Document par défaut  

    -   Contenu statique  

-   Développement d'applications :  

    -   ASP.NET 3.5 (et les options sélectionnées automatiquement)  

    -   ASP.NET 4.5 (et les options sélectionnées automatiquement)  

    -   Extensibilité .NET 3.5  

    -   Extensibilité .NET 4.5  

-   Sécurité :  

    -   Authentification Windows  

-   Compatibilité avec la gestion IIS 6 :  

    -   Compatibilité avec la métabase de données IIS 6  

**Mémoire de l’ordinateur :**  

-   L’ordinateur hébergeant ce rôle de système de site doit avoir au moins 5 % de mémoire disponible pour permettre au rôle de système de site de traiter les demandes.  

-   Quand ce rôle de système de site coexiste avec un autre rôle de système de site qui a cette même exigence, la quantité de mémoire disponible requise pour l’ordinateur n’augmente pas, mais elle reste à un minimum de 5 %.  

###  <a name="bkmk_2012FSPpreq"></a> Point d’état de secours  
La configuration IIS par défaut est nécessaire, avec les ajouts suivants :  

-   Compatibilité avec la gestion IIS 6 :  

    -   Compatibilité avec la métabase de données IIS 6  

###  <a name="bkmk_2012MPpreq"></a> Point de gestion  
**Rôles et fonctionnalités Windows Server :**  

-   .NET Framework 4.5.2  

-   Extensions du serveur BITS (et options sélectionnées automatiquement) ou services BITS (et options sélectionnées automatiquement)  

**Configuration IIS :**  

-   Développement d'applications :  

    -   Extensions ISAPI  

-   Sécurité :  

    -   Authentification Windows  

-   Compatibilité avec la gestion IIS 6 :  

    -   Compatibilité avec la métabase de données IIS 6  

    -   Compatibilité WMI d'IIS 6  

###  <a name="bkmk_2012RSpoint"></a> Point de Reporting Services  
**Rôles et fonctionnalités Windows Server :**  

-   .NET Framework 4.5.2  

**SQL Server Reporting Services :**  

-   Avant d’installer le point de Reporting Services, vous devez installer et configurer au moins une instance de SQL Server pour prendre en charge SQL Server Reporting Services.  

-   L’instance que vous utilisez pour SQL Server Reporting Services peut être la même que celle utilisée pour la base de données du site.  

-   En outre, l’instance que vous utilisez peut être partagée avec d’autres produits System Center, dès lors que ceux-ci n’ont pas de restrictions pour le partage de l’instance de SQL Server.  

###  <a name="bkmk_SCPpreq"></a> Point de connexion de service  
**Rôles et fonctionnalités Windows Server :**  

-   .NET Framework 4.5.2  

     Pendant l’installation de ce rôle de système de site, Configuration Manager installe automatiquement .NET Framework 4.5.2. Cette installation peut placer le serveur dans un état d’attente redémarrage. Quand un redémarrage est en attente pour .NET Framework, il est possible que les applications .NET ne puissent pas s’exécuter tant que le serveur n’a pas redémarré et que l’installation n’est pas terminée.  

**Redistribuable Visual C++ :**  

-   Configuration Manager installe Microsoft Visual C++ 2013 Redistributable Package sur chaque ordinateur hébergeant un point de distribution.  

-   Le rôle de système de site nécessite la version x64.  

###  <a name="bkmk_2012SUPpreq"></a> Point de mise à jour logicielle  
**Rôles et fonctionnalités Windows Server :**  

-   .NET Framework 3.5 SP1 (ou version ultérieure)  

-   .NET Framework 4.5.2  

La configuration IIS par défaut est nécessaire.

**Windows Server Update Services :**  

-   Vous devez installer le rôle Windows Server Update Services (WSUS) de Windows Server sur un ordinateur avant d’installer un point de mise à jour logicielle.  

-   Pour plus d’informations, consultez [Planifier les mises à jour logicielles dans System Center Configuration Manager](../../../sum/plan-design/plan-for-software-updates.md).  

### <a name="state-migration-point"></a>Point de migration d'état  
La configuration IIS par défaut est nécessaire.  

##  <a name="bkmk_2008"></a> Conditions préalables pour Windows Server 2008 R2 et Windows Server 2008  
Windows Server 2008 et Windows Server 2008 R2 bénéficient désormais du support étendu au lieu du support standard, comme indiqué dans la [Politique de support Microsoft](https://support.microsoft.com/lifecycle). Pour plus d’informations sur la prise en charge à venir de ces systèmes d’exploitation utilisés comme serveurs de système de site avec Configuration Manager, consultez [Fonctionnalités supprimées et déconseillées dans System Center Configuration Manager](../../../core/plan-design/changes/removed-and-deprecated-features.md).  

**Ce qui suit s’applique à toutes les conditions requises pour .NET Framework :**  

-   Installez la version complète de .NET Framework avant d’installer les rôles de système de site. Par exemple, consultez [Microsoft .NET Framework 4 (programme d’installation autonome)](http://go.microsoft.com/fwlink/p/?LinkId=193048). Le profil client .NET Framework 4 ne correspond pas à la configuration requise.  

**Ce qui suit s’applique à toutes les conditions requises pour l’activation de Windows Communication Foundation (WCF) :**  

-   Vous pouvez configurer l’activation de WCF comme faisant partie de la fonctionnalité Windows du .NET Framework sur le serveur de système de site. Par exemple, sur Windows Server 2008 R2, exécutez l’**Assistant Ajout de fonctionnalités** pour installer des fonctionnalités supplémentaires sur le serveur. Dans la page **Sélectionner les fonctionnalités**, développez **Fonctionnalités de .NET Framework 3.5.1**, développez **Activation WCF**, puis cochez les cases **Activation HTTP** et **Activation non-HTTP** pour activer ces options.  

###  <a name="bkmk_2008sspreq"></a> Serveur de site : site d’administration centrale et site principal  
**.NET Framework :**  

-   .NET Framework 3.5 SP1 (ou version ultérieure)  

-   .NET Framework 4.5.2  

**Fonctionnalité Windows :**  

-   Compression différentielle à distance  

**Windows ADK :**  

-   Avant d’installer ou de mettre à niveau un site d’administration centrale ou un site principal, vous devez installer la version de Windows ADK nécessaire pour la version de Configuration Manager que vous installez ou vers laquelle vous effectuez une mise à niveau.  

    -   La version 1511 de Configuration Manager nécessite la version Windows 10 RTM (10.0.10240) de Windows ADK.  

-   Pour plus d’informations sur cette configuration requise, consultez [Configuration requise de l’infrastructure pour le déploiement de système d’exploitation](/sccm/osd/plan-design/infrastructure-requirements-for-operating-system-deployment).  

**Redistribuable Visual C++ :**  

-   Configuration Manager installe Microsoft Visual C++ 2013 Redistributable Package sur chaque ordinateur sur lequel est installé un serveur de site.  

-   Les sites d'administration centrale et les sites principaux requièrent à la fois les versions x86 et x64 du fichier redistribuable applicable.  

###  <a name="bkmk_2008secpreq"></a> Serveur de site : site secondaire  
**.NET Framework :**  

-   .NET Framework 3.5 SP1 (ou version ultérieure)  

-   .NET Framework 4.5.2  

**Redistribuable Visual C++ :**  

-   Configuration Manager installe Microsoft Visual C++ 2013 Redistributable Package sur chaque ordinateur sur lequel est installé un serveur de site.  

-   Les sites secondaires requièrent seulement la version x64.  

**Rôles de système de site par défaut :**  

-   Par défaut, un site secondaire installe un **point de gestion** et un **point de distribution**.  

-   Assurez-vous que le serveur de site secondaire remplit les conditions préalables pour ces rôles de système de site.  

###  <a name="bkmk_2008dbpreq"></a> Serveur de base de données  
**Service d’accès à distance au Registre :**  

-   Durant l’installation du site Configuration Manager, vous devez activer le service d’accès à distance au Registre sur l’ordinateur qui hébergera la base de données du site.  

**SQL Server :**  

-   Avant d’installer un site d’administration centrale ou un site principal, vous devez installer une version prise en charge de SQL Server pour héberger la base de données du site.  

-   Avant d’installer un site secondaire, vous pouvez installer une version prise en charge de SQL Server.  

-   Si vous souhaitez que Configuration Manager installe SQL Server Express en même temps que le site secondaire, vérifiez que l’ordinateur présente la configuration requise pour exécuter SQL Server Express.  

###  <a name="bkmk_2008smsprovpreq"></a> Serveur de fournisseur SMS  
**Windows ADK :**  

-   L’ordinateur sur lequel vous installez une instance du fournisseur SMS doit disposer de la version de Windows ADK nécessaire à la version de Configuration Manager que vous installez ou vers laquelle vous effectuez une mise à niveau.  

    -   La version 1511 de Configuration Manager nécessite la version Windows 10 RTM (10.0.10240) de Windows ADK.  

-   Pour plus d’informations sur cette configuration requise, consultez [Configuration requise de l’infrastructure pour le déploiement de système d’exploitation](/sccm/osd/plan-design/infrastructure-requirements-for-operating-system-deployment).  

###  <a name="bkmk_2008acwspreq"></a> Point du site web du catalogue des applications  
**.NET Framework :**  

-   .NET Framework 4.5.2  

**Configuration IIS :**

La configuration IIS par défaut est nécessaire, avec les ajouts suivants :  

-   Fonctionnalités HTTP communes :  

    -   Contenu statique  

    -   Document par défaut  

-   Développement d'applications :  

    -   ASP.NET (et options sélectionnées automatiquement)  

         Dans certains scénarios, par exemple quand IIS est installé ou reconfiguré après l’installation de .NET Framework version 4.5.2, vous devez activer explicitement ASP.NET version 4.5. Par exemple, sur un ordinateur 64 bits exécutant .NET Framework version 4.0.30319, exécutez la commande suivante : **%windir%\Microsoft.NET\Framework64\v4.0.30319\aspnet_regiis.exe -i -enable**  

-   Sécurité :  

    -   Authentification Windows  

-   Compatibilité avec la gestion IIS 6 :  

    -   Compatibilité avec la métabase de données IIS 6  

###  <a name="bkmk_2008ACwsitepreq"></a> Point de service web du catalogue des applications  
**.NET Framework :**  

-   .NET Framework 3.5 SP1 (ou version ultérieure)  

-   .NET Framework 4.5.2  

**Activation de Windows Communication Foundation (WCF) :**  

-   Activation HTTP  

-   Activation non-HTTP  

**Configuration IIS :**

La configuration IIS par défaut est nécessaire, avec les ajouts suivants :  

-   Développement d'applications :  

    -   ASP.NET (et options sélectionnées automatiquement)  

         Dans certains scénarios, par exemple quand IIS est installé ou reconfiguré après l’installation de .NET Framework version 4.5.2, vous devez activer explicitement ASP.NET version 4.5. Par exemple, sur un ordinateur 64 bits exécutant .NET Framework version 4.0.30319, exécutez la commande suivante : **%windir%\Microsoft.NET\Framework64\v4.0.30319\aspnet_regiis.exe -i -enable**  

-   Compatibilité avec la gestion IIS 6 :  

    -   Compatibilité avec la métabase de données IIS 6  

**Mémoire de l’ordinateur :**  

-   L’ordinateur hébergeant ce rôle de système de site doit avoir au moins 5 % de mémoire disponible pour permettre au rôle de système de site de traiter les demandes.  

-   Quand ce rôle de système de site coexiste avec un autre rôle de système de site qui a cette même exigence, la quantité de mémoire disponible requise pour l’ordinateur n’augmente pas, mais elle reste à un minimum de 5 %.  

###  <a name="bkmk_2008AIpreq"></a> Point de synchronisation Asset Intelligence  
**.NET Framework :**  

-   .NET Framework 4.5.2  

###  <a name="bkmk_2008crppreq"></a> Point d’enregistrement de certificat  
**.NET Framework :**  

-   .NET Framework 4.5.2  

-   Activation HTTP  

**Configuration IIS :**

La configuration IIS par défaut est nécessaire, avec les ajouts suivants :  

-   Compatibilité avec la gestion IIS 6 :  

    -   Compatibilité avec la métabase de données IIS 6  

    -   Compatibilité WMI d'IIS 6  

###  <a name="bkmk_2008dppreq"></a> Point de distribution  
**Configuration IIS :**

Vous pouvez utiliser la configuration IIS par défaut ou une configuration personnalisée. Pour utiliser une configuration IIS personnalisée, vous devez activer les options suivantes pour IIS :  

-   Développement d'applications :  

    -   Extensions ISAPI  

-   Sécurité :  

    -   Authentification Windows  

-   Compatibilité avec la gestion IIS 6 :  

    -   Compatibilité avec la métabase de données IIS 6  

    -   Compatibilité WMI d'IIS 6  

Quand vous utilisez une configuration IIS personnalisée, vous pouvez supprimer les options qui ne sont pas nécessaires, comme les suivantes :  

-   Fonctionnalités HTTP communes :  

    -   Redirection HTTP  

-   Scripts et outils de gestion IIS  

**Fonctionnalité Windows :**  

-   Compression différentielle à distance  

**Redistribuable Visual C++ :**  

-   Configuration Manager installe Microsoft Visual C++ 2013 Redistributable Package sur chaque ordinateur hébergeant un point de distribution.  

-   La version installée dépend de la plateforme de l’ordinateur (x86 ou x64).  

**Microsoft Azure :**  

-   Pour héberger un point de distribution, vous pouvez utiliser un service cloud dans Azure.  

**Pour prendre en charge PXE ou la multidiffusion :**  

-   Installez et configurez le rôle WDS (Windows Deployment Services) de Windows Server.  

    > [!NOTE]  
    >  WDS s’installe et se configure automatiquement quand vous configurez un point de distribution pour prendre en charge PXE ou la multidiffusion sur un serveur exécutant Windows Server 2012 ou une version ultérieure.  

> [!NOTE]  
> Le rôle de système de site du point de distribution ne nécessite pas le service de transfert intelligent en arrière-plan (BITS). Quand BITS est configuré sur l’ordinateur du point de distribution, il n’est pas utilisé pour faciliter le téléchargement de contenu par les clients qui utilisent BITS.  


###  <a name="bkmk_2008EPPpreq"></a> Point Endpoint Protection  
**.NET Framework :**  

-   .NET Framework 3.5 SP1 (ou version ultérieure)  

###  <a name="bkmk_2008Enrollpreq"></a> Point d’inscription  
**.NET Framework :**  

-   .NET Framework 4.5.2  

     Si, quand ce rôle de système de site est installé, aucune version prise en charge de .NET Framework n’est installée sur le serveur, Configuration Manager installe automatiquement .NET Framework 4.5.2. Cette installation peut placer le serveur dans un état d’attente redémarrage. Quand un redémarrage est en attente pour .NET Framework, il est possible que les applications .NET ne puissent pas s’exécuter tant que le serveur n’a pas redémarré et que l’installation n’est pas terminée.  

**Activation de Windows Communication Foundation (WCF) :**  

-   Activation HTTP  

-   Activation non-HTTP  

**Configuration IIS :**

La configuration IIS par défaut est nécessaire, avec les ajouts suivants :  

-   Développement d'applications :  

    -   ASP.NET (et options sélectionnées automatiquement)  

         Dans certains scénarios, par exemple quand IIS est installé ou reconfiguré après l’installation de .NET Framework version 4.5.2, vous devez activer explicitement ASP.NET version 4.5. Par exemple, sur un ordinateur 64 bits exécutant .NET Framework version 4.0.30319, exécutez la commande suivante : **%windir%\Microsoft.NET\Framework64\v4.0.30319\aspnet_regiis.exe -i -enable**  

**Mémoire de l’ordinateur :**  

-   L’ordinateur hébergeant ce rôle de système de site doit avoir au moins 5 % de mémoire disponible pour permettre au rôle de système de site de traiter les demandes.  

-   Quand ce rôle de système de site coexiste avec un autre rôle de système de site qui a cette même exigence, la quantité de mémoire disponible requise pour l’ordinateur n’augmente pas, mais elle reste à un minimum de 5 %.  

###  <a name="bkmk_2008EnrollProxpreq"></a> Point proxy d’inscription  
**.NET Framework :**  

-   .NET Framework 4.5.2  

     Si, quand ce rôle de système de site est installé, aucune version prise en charge de .NET Framework n’est installée sur le serveur, Configuration Manager installe automatiquement .NET Framework 4.5.2. Cette installation peut placer le serveur dans un état d’attente redémarrage. Quand un redémarrage est en attente pour .NET Framework, il est possible que les applications .NET ne puissent pas s’exécuter tant que le serveur n’a pas redémarré et que l’installation n’est pas terminée.  

**Activation de Windows Communication Foundation (WCF) :**  

-   Activation HTTP  

-   Activation non-HTTP  

**Configuration IIS :**

La configuration IIS par défaut est nécessaire, avec les ajouts suivants :  

-   Développement d'applications :  

    -   ASP.NET (et options sélectionnées automatiquement)  

         Dans certains scénarios, par exemple quand IIS est installé ou reconfiguré après l’installation de .NET Framework version 4.5.2, vous devez activer explicitement ASP.NET version 4.5. Par exemple, sur un ordinateur 64 bits exécutant .NET Framework version 4.0.30319, exécutez la commande suivante : **%windir%\Microsoft.NET\Framework64\v4.0.30319\aspnet_regiis.exe -i -enable**  

**Mémoire de l’ordinateur :**  

-   L’ordinateur hébergeant ce rôle de système de site doit avoir au moins 5 % de mémoire disponible pour permettre au rôle de système de site de traiter les demandes.  

-   Quand ce rôle de système de site coexiste avec un autre rôle de système de site qui a cette même exigence, la quantité de mémoire disponible requise pour l’ordinateur n’augmente pas, mais elle reste à un minimum de 5 %.  

###  <a name="bkmk_2008FSPpreq"></a> Point d’état de secours  
**Configuration IIS :**

La configuration IIS par défaut est nécessaire, avec les ajouts suivants :  

-   Compatibilité avec la gestion IIS 6 :  

    -   Compatibilité avec la métabase de données IIS 6  

###  <a name="bkmk_2008MPpreq"></a> Point de gestion  
**.NET Framework :**  

-   .NET Framework 4.5.2  

**Configuration IIS :**

Vous pouvez utiliser la configuration IIS par défaut ou une configuration personnalisée. Chaque point de gestion que vous activez pour la prise en charge des appareils mobiles requiert une configuration d’IIS supplémentaire pour ASP.NET (et ses options sélectionnées automatiquement).

Dans certains scénarios, par exemple quand IIS est installé ou reconfiguré après l’installation de .NET Framework version 4.5.2, vous devez activer explicitement ASP.NET version 4.5. Par exemple, sur un ordinateur 64 bits exécutant .NET Framework version 4.0.30319, exécutez la commande suivante : **%windir%\Microsoft.NET\Framework64\v4.0.30319\aspnet_regiis.exe -i -enable**  


Pour utiliser une configuration IIS personnalisée, vous devez activer les options suivantes pour IIS :  

-   Développement d'applications :  

    -   Extensions ISAPI  

-   Sécurité :  

    -   Authentification Windows  

-   Compatibilité avec la gestion IIS 6 :  

    -   Compatibilité avec la métabase de données IIS 6  

    -   Compatibilité WMI d'IIS 6  


Quand vous utilisez une configuration IIS personnalisée, vous pouvez supprimer les options qui ne sont pas nécessaires, comme les suivantes :  

-   Fonctionnalités HTTP communes :  

    -   Redirection HTTP  

-   Scripts et outils de gestion IIS  

**Fonctionnalité Windows :**  

-   Extensions du serveur BITS (et options sélectionnées automatiquement) ou service de transfert intelligent en arrière-plan (BITS) (et options sélectionnées automatiquement)  

###  <a name="bkmk_2008RSpoint"></a> Point de Reporting Services  
**.NET Framework :**  

-   .NET Framework 4.5.2  

**SQL Server Reporting Services :**  

-   Avant d’installer le point de Reporting Services, vous devez installer et configurer au moins une instance de SQL Server pour prendre en charge SQL Server Reporting Services.  

-   L’instance que vous utilisez pour SQL Server Reporting Services peut être la même que celle utilisée pour la base de données du site.  

-   En outre, l’instance que vous utilisez peut être partagée avec d’autres produits System Center, dès lors que ceux-ci n’ont pas de restrictions pour le partage de l’instance de SQL Server.  

###  <a name="bkmk_2008SCPpreq"></a> Point de connexion de service  
**.NET Framework :**  

-   .NET Framework 4.5.2  

     Si, quand ce rôle de système de site est installé, aucune version prise en charge de .NET Framework n’est installée sur le serveur, Configuration Manager installe automatiquement .NET Framework 4.5.2. Cette installation peut placer le serveur dans un état d’attente redémarrage. Quand un redémarrage est en attente pour .NET Framework, il est possible que les applications .NET ne puissent pas s’exécuter tant que le serveur n’a pas redémarré et que l’installation n’est pas terminée.  

**Redistribuable Visual C++ :**  

-   Configuration Manager installe Microsoft Visual C++ 2013 Redistributable Package sur chaque ordinateur hébergeant un point de distribution.  

-   Le rôle de système de site nécessite la version x64.  

###  <a name="bkmk_2008SUPpreq"></a> Point de mise à jour logicielle  
**.NET Framework :**  

-   .NET Framework 3.5 SP1 (ou version ultérieure)  

-   .NET Framework 4.5.2  

**Configuration IIS :**

La configuration IIS par défaut est nécessaire.  

**Windows Server Update Services :**  

-   Vous devez installer le rôle Windows Server Update Services (WSUS) de Windows Server sur un ordinateur avant d’installer un point de mise à jour logicielle.  

-   Pour plus d’informations, consultez [Planifier les mises à jour logicielles dans System Center Configuration Manager](../../../sum/plan-design/plan-for-software-updates.md).

###  <a name="bkmk_2008SMPpreq"></a> Point de migration d'état  
**Configuration IIS :**

La configuration IIS par défaut est nécessaire.  
