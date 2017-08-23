---
title: "Sécurité et confidentialité pour la gestion des applications | Documents Microsoft"
description: "Bonne pratiques de sécurité et de confidentialité pour la gestion des applications dans System Center Configuration Manager."
ms.custom: na
ms.date: 10/06/2016
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: configmgr-app
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 4d26deed-3b16-4116-b640-f618f2c20f5a
caps.latest.revision: "8"
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.openlocfilehash: 6ee99fa0c07676f004e41a50bf16d0d17604e790
ms.sourcegitcommit: 51fc48fb023f1e8d995c6c4eacfda7dbec4d0b2f
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/07/2017
---
# <a name="security-and-privacy-for-application-management-in-system-center-configuration-manager"></a>Sécurité et confidentialité pour la gestion des applications dans System Center Configuration Manager

*S’applique à : System Center Configuration Manager (Current Branch)*


##  <a name="security-best-practices-for-application-management"></a>Meilleures pratiques de sécurité pour la gestion des applications  

|Meilleure pratique de sécurité|Plus d'informations|  
|----------------------------|----------------------|  
|Configurer les points du catalogue d'applications pour utiliser des connexions HTTPS et informer les utilisateurs sur les dangers des sites Web malveillants.|Configurer le point de site Web du catalogue d'applications et le point de service Web du catalogue d'applications pour accepter des connexions HTTPS, de sorte que le serveur soit authentifié pour les utilisateurs et que les données transmises soient protégées contre la falsification et l'affichage. Aider à empêcher les attaques d'ingénierie sociale en conseillant aux utilisateurs de se connecter uniquement à des sites Web approuvés.<br /><br /> Ne pas utiliser les options de configuration de marque qui affichent le nom de votre organisation dans le catalogue des applications comme preuve d’identité quand vous n’utilisez pas HTTPS.|  
|Utiliser la séparation des rôles et installer le point de site Web du catalogue des applications et le point de service du catalogue des applications sur des serveurs distincts.|Si le point de site web du catalogue des applications est compromis, installez-le sur un serveur distinct du point de service web du catalogue des applications. Cela vous aidera à protéger les clients Configuration Manager et l’infrastructure Configuration Manager. Cela est particulièrement important si le point de site Web du catalogue d'applications accepte les connexions de clients à partir d'Internet, car cette configuration rend le serveur vulnérable aux attaques.|  
|Formez les utilisateurs à la fermeture de la fenêtre du navigateur lorsqu'ils ont terminé d'utiliser le catalogue des applications.|Si les utilisateurs naviguent jusqu'à un site Web externe dans la même fenêtre du navigateur que celle qu'ils ont utilisée pour le catalogue d'applications, le navigateur continue à utiliser les paramètres de sécurité adaptés aux sites approuvés dans l'intranet.|  
|Spécifiez manuellement l’affinité entre utilisateur et appareil au lieu de laisser les utilisateurs identifier leur appareil principal. N’activez pas la configuration basée sur l’utilisation.|Ne considérez pas comme faisant autorité les informations collectées auprès des utilisateurs ou de l’appareil. Si vous déployez un logiciel à l'aide d'une affinité entre périphérique et utilisateur non spécifiée par un utilisateur administratif approuvé, vous pourrez installer ce logiciel sur des ordinateurs et vers des utilisateurs qui ne sont pas autorisés à recevoir ce logiciel.|  
|Configurez toujours les déploiements pour télécharger du contenu à partir de points de distribution plutôt que de les exécuter à partir de points de distribution.|Quand vous configurez des déploiements pour télécharger du contenu à partir d’un point de distribution et que vous les exécutez localement, le client Configuration Manager vérifie le hachage du package après avoir téléchargé le contenu. Le client rejette le package si le hachage ne correspond pas à celui défini dans la stratégie. En comparaison, si vous configurez le déploiement pour l’exécuter directement à partir d’un point de distribution, le client Configuration Manager ne vérifie pas le hachage du package, ce qui signifie que le client Configuration Manager peut installer le logiciel qui a été falsifié.<br /><br /> Si vous devez exécuter des déploiements directement à partir de points de distribution, utilisez les autorisations NTFS minimales sur les packages sur les points de distribution, et utilisez IPSec pour sécuriser le canal de communication entre le client et les points de distribution, et entre les points de distribution et le serveur de site.|  
|N’autorisez pas les utilisateurs à interagir avec des programmes si l’option **Exécuter avec les droits d’administration** est obligatoire.|Quand vous configurez un programme, vous pouvez définir l’option **Autoriser les utilisateurs à interagir avec ce programme** pour que les utilisateurs puissent répondre aux invites nécessaires dans l’interface utilisateur. Si le programme est également configuré avec l'option **Exécuter avec les droits d'administration**, une personne malveillante devant un ordinateur exécutant le programme peut utiliser l'interface utilisateur pour élever les privilèges sur l'ordinateur client.<br /><br /> Utilisez des programmes utilisant Windows Installer pour l’installation et des privilèges élevés par utilisateur pour les déploiements de logiciels qui nécessitent des informations d’identification d’administration. Le programme d’installation doit être exécuté dans le contexte d’un utilisateur qui ne dispose pas d’informations d’identification d’administration. Les privilèges élevés par utilisateur de Windows Installer représentent la méthode la plus sûre pour déployer les applications avec cette spécification.|  
|Déterminez si les utilisateurs peuvent installer les logiciels de manière interactive à l'aide du paramètre du client **Autorisations d'installation** .|Configurez le paramètre d’appareil client **Agent ordinateur** **Autorisations d’installation** pour restreindre les types d’utilisateurs qui peuvent installer le logiciel à l’aide du catalogue des applications ou du Centre logiciel. Par exemple, créez un paramètre de client personnalisé après avoir défini **Installer les autorisations** sur **Administrateurs uniquement**. Appliquez ensuite ce paramètre du client à un regroupement de serveurs pour empêcher les utilisateurs sans autorisation d’administration d’installer des logiciels sur ces ordinateurs.|  
|Pour les appareils mobiles, déployez seulement les applications qui sont signées.|Déployez des applications d’appareil mobile seulement si leur code est signé par une autorité de certification approuvée par l’appareil mobile. Exemple :<br /><br /><ul><li>Une application d’un fournisseur, signée par une autorité de certification connue, comme VeriSign.</li><li>Une application interne que vous signez indépendamment de Configuration Manager, en utilisant votre autorité de certification interne.</li><li>Une application interne que vous signez à l’aide de Configuration Manager quand vous créez le type d’application et que vous utilisez un certificat de signature.</li></ul>|  
|Si vous signez des applications d’appareil mobile à l’aide de l’ **Assistant Création d’une application** dans Configuration Manager, sécurisez l’emplacement du fichier de certificat de signature, ainsi que le canal de communication.|Pour renforcer la protection contre l’élévation des privilèges et les attaques d’un intercepteur (man in the middle), stockez le fichier du certificat de signature dans un dossier sécurisé, et utilisez IPSec ou SMB entre les ordinateurs suivants :<br /><br /><ul><li>Ordinateur qui exécute la console Configuration Manager</li><li>L’ordinateur qui stocke le fichier de signature de certificat.</li><li>L’ordinateur qui stocke les fichiers sources de l’application.</li></ul> Vous pouvez aussi signer l’application indépendamment de Configuration Manager et avant d’exécuter l’**Assistant Création d’une application**.|  
|Mettez en œuvre des contrôles d'accès pour protéger les ordinateurs de référence.|Assurez-vous que lorsqu'un utilisateur administratif configure une méthode de détection dans un type de déploiement en naviguant vers un ordinateur de référence, cet ordinateur n'a pas été compromis.|  
|Limitez et surveillez les utilisateurs administratifs à qui sont accordés les rôles de sécurité basés sur les rôles qui sont liés à la gestion de l'application :<br /><br /><ul><li>**Administrateur d’application**</li><li>**Auteur d’application**</li><li> **Gestionnaire de déploiement d’applications**</li></ul>|Même lorsque vous configurez l'administration basée sur les rôles, les utilisateurs administratifs qui créent et déploient des applications peuvent disposer d'un nombre d'autorisations plus important que ce que vous pensez. Par exemple, des utilisateurs administratifs qui créent ou modifient une application peuvent sélectionner des applications dépendantes qui ne sont pas dans leur étendue de sécurité.|  
|Quand vous configurez des environnements virtuels Microsoft Application Virtualization (App-V), sélectionnez des applications qui ont le même niveau de confiance dans l’environnement virtuel.|Dans la mesure où des applications dans un environnement virtuel App-V peuvent partager des ressources, comme le Presse-papiers, configurez l’environnement virtuel afin que les applications sélectionnées aient le même niveau de confiance.<br /><br /> Pour plus d’informations, consultez [Créer des environnements virtuels App-V](../../apps/deploy-use/create-app-v-virtual-environments.md).|  
|Si vous déployez des applications pour les ordinateurs Mac, assurez-vous que les fichiers source proviennent d'une source fiable.|L'outil CMAppUtil ne valide pas la signature du package source, assurez-vous qu'il provient d'une source de confiance. L’outil CMAppUtil ne peut pas détecter si les fichiers ont été falsifiés.|  
|Si vous déployez des applications pour des ordinateurs Mac, sécurisez l’emplacement du fichier **.cmmac**, ainsi que le canal de communication quand vous importez ce fichier dans Configuration Manager.|Le fichier **.cmmac** qui est généré par l’outil CMAppUtil et que vous importez dans Configuration Manager n’est pas signé ou validé. Pour éviter la falsification avec ce fichier, stockez-le dans un dossier sécurisé et utilisez IPSec ou SMB entre les ordinateurs suivants :<br /><br /><ul><li>Ordinateur qui exécute la console Configuration Manager</li><li>L’ordinateur qui stocke le fichier **.cmmac**.</li></ul>.|  
|Si vous configurez un type de déploiement d'application Web, utilisez le protocole HTTPS plutôt que HTTP pour sécuriser la connexion.|Si vous déployez une application web à l’aide d’un lien HTTP au lieu d’un lien HTTPS, l’appareil peut être redirigé vers un serveur non autorisé, et les données transférées entre l’appareil et le serveur peuvent être falsifiées.|  

##  <a name="security-issues-for-application-management"></a>Problèmes de sécurité pour la gestion des applications  

-   Les utilisateurs à faibles privilèges peuvent copier des fichiers à partir du cache du client sur l'ordinateur client.  

     Les utilisateurs peuvent lire le cache du client, mais pas y écrire. Avec les autorisations de lecture, un utilisateur peut copier des fichiers d'installation d'application d'un ordinateur à un autre.  

-   Les utilisateurs avec des privilèges faibles peuvent modifier les fichiers qui enregistrent l’historique de déploiement de logiciels sur l’ordinateur client.  

     Étant donné que les informations de l’historique des applications ne sont pas protégées, un utilisateur peut modifier des fichiers qui indiquent si une application a été installée.  

-   Les packages App-V ne sont pas signés.  

     Les packages App-V dans Configuration Manager ne prennent pas en charge la signature pour vérifier que le contenu émane d’une source de confiance et qu’il n’a pas été altéré en transit. Il n’existe aucune mesure d’atténuation du risque pour ce problème de sécurité. Suivez bien la bonne pratique de sécurité consistant à télécharger le contenu à partir d’une source de confiance et d’un emplacement sécurisé.  

-   Les applications App-V publiées peuvent être installées par tous les utilisateurs sur l'ordinateur.  

     Quand une application App-V est publiée sur un ordinateur, tous les utilisateurs qui se connectent à cet ordinateur peuvent installer l’application. Cela signifie que vous ne pouvez pas limiter les utilisateurs qui peuvent installer l’application après sa publication.  

-   Vous ne pouvez pas limiter les autorisations d'installation du portail d'entreprise.  

     Bien que vous puissiez configurer un paramètre client pour limiter les autorisations d’installation, par exemple aux utilisateurs principaux d’un appareil ou aux administrateurs locaux uniquement, ce paramètre ne fonctionne pas pour le portail d’entreprise. Cela peut entraîner une élévation des privilèges car un utilisateur pourrait installer une application qu’il n’est pas autorisé à installer.  

##  Certificats <a name="BKMK_CertificatesSilverlight5"></a> pour Microsoft Silverlight 5 et mode de confiance élevée obligatoires pour le catalogue des applications  
 Les clients Configuration Manager requièrent Microsoft Silverlight 5, qui doit s’exécuter en mode de confiance élevée pour permettre aux utilisateurs d’installer des logiciels à partir du catalogue d’applications. Par défaut, les applications Silverlight s'exécutent en mode de confiance partielle pour empêcher les applications d'accéder aux données utilisateur. Configuration Manager installe automatiquement Microsoft Silverlight 5 sur les clients s’il n’est pas déjà installé. Par défaut, Configuration Manager définit le paramètre du client **Autoriser les applications Silverlight à s’exécuter en mode de confiance élevée** de l’Agent ordinateur sur **Oui**. Ce paramètre permet aux applications Silverlight signées et approuvées de demander le mode de confiance élevée.  

 Lors de l’installation du rôle de système de site du point de site web du catalogue d’applications, le client installe également un certificat de signature Microsoft dans le magasin de certificats Éditeurs approuvés de l’ordinateur sur chaque ordinateur client Configuration Manager. Ce certificat permet aux applications Silverlight signées par ce certificat de s’exécuter dans le mode de confiance élevé requis par les ordinateurs pour installer des logiciels à partir du catalogue des applications. Configuration Manager gère automatiquement ce certificat de signature. Pour assurer la continuité de service, ne supprimez ou ne déplacez pas manuellement ce certificat de signature Microsoft.  

> [!WARNING]  
>  Quand il est activé, le paramètre client **Autoriser les applications Silverlight à s’exécuter en mode de confiance élevée** permet à toutes les applications Silverlight signées par des certificats dans le magasin de certificats Éditeurs approuvés dans le magasin de l’ordinateur ou dans le magasin de l’utilisateur de s’exécuter en mode de confiance élevée. Le paramètre client ne peut pas activer le mode de confiance élevée spécifiquement pour le catalogue d’applications Configuration Manager ou pour le magasin de certificats Éditeurs approuvés dans le magasin de l’ordinateur. Si un logiciel malveillant ajoute un certificat non autorisé dans le magasin de certificats Éditeurs approuvés, par exemple, dans le magasin de l'utilisateur, un logiciel malveillant qui utilise sa propre application Silverlight peut maintenant s'exécuter également en mode de confiance élevée.  

 Le fait de configurer le paramètre client **Autoriser les applications Silverlight à s’exécuter en mode de confiance élevée** sur **Non** ne supprime pas le certificat de signature Microsoft des clients.  

 Pour plus d’informations sur les applications approuvées dans Silverlight, consultez [Applications approuvées](http://go.microsoft.com/fwlink/p/?LinkId=252842).  

##  <a name="privacy-information-for-application-management"></a>Informations de confidentialité pour la gestion d'applications  
 La gestion des applications vous permet d’exécuter n’importe quel programme, script ou application sur n’importe quel ordinateur client ou appareil mobile client dans la hiérarchie. Configuration Manager n’a aucun contrôle sur les types d’applications, de programmes ou de scripts que vous exécutez, ni sur le type d’informations qu’ils transmettent. Lors du déploiement des applications, Configuration Manager peut transmettre des informations entre les clients et les serveurs qui identifient les comptes d’appareil et de connexion.  

 Configuration Manager gère les informations d’état relatives au processus de déploiement de logiciels. Les informations d'état relatives au déploiement de logiciels ne sont pas cryptées lors de leur transmission, à moins que le client communique à l'aide de HTTPS. Les informations d'état ne sont pas stockées dans la base de données sous une forme non chiffrée.  

 L’utilisation de l’installation d’applications de Configuration Manager pour installer à distance, en mode interactif ou silencieux des logiciels sur des clients peut être soumise à des termes de contrat de licence propres à ce logiciel. Cette utilisation est distincte des termes du contrat de licence logiciel pour System Center Configuration Manager. Consultez et acceptez toujours les termes du contrat de licence logiciel avant de déployer le logiciel à l’aide de Configuration Manager.  

 Le déploiement d’application n’est pas défini par défaut et nécessite plusieurs étapes de configuration.  

 Deux fonctionnalités facultatives qui contribuent au déploiement efficace de logiciels sont l'affinité entre périphérique et utilisateur et le catalogue d'applications :  

-   L’affinité entre utilisateur et appareil associe un utilisateur à des appareils, afin qu’un administrateur Configuration Manager puisse déployer un logiciel auprès d’un utilisateur et que ce logiciel soit installé automatiquement sur le ou les ordinateurs que l’utilisateur utilise le plus souvent.  

-   Le catalogue des applications est un site web qui permet aux utilisateurs de demander l’installation de logiciels.  

 Consultez les sections suivantes pour obtenir des informations de confidentialité sur l'affinité entre périphérique et utilisateur et le catalogue d'applications.  

 Avant de configurer la gestion des applications, pensez à vos besoins en matière de confidentialité.  

##  <a name="user-device-affinity"></a>Affinité entre périphérique et utilisateur  
-  Configuration Manager peut transmettre des informations entre les clients et les systèmes de site du point de gestion. Les informations peuvent identifier le compte d’ordinateur et de connexion, ainsi que le résumé de l’utilisation pour les comptes de connexion.  
-  Les informations transmises entre le client et le serveur ne sont pas chiffrées, sauf si le point de gestion est configuré pour exiger que les clients communiquent via HTTPS.  
-  Les informations relatives à l’ordinateur et à l’utilisation du compte de connexion qui sont utilisées pour associer un utilisateur à un appareil sont enregistrées sur les ordinateurs clients, envoyées aux points de gestion, puis enregistrées dans la base de données Configuration Manager. Les informations anciennes sont supprimées de la base de données par défaut après 90 jours. Le comportement de suppression peut être configuré en définissant la tâche de maintenance de site **Supprimer les anciennes données relatives à l'affinité entre périphérique et utilisateur** .
-  Configuration Manager conserve les informations d’état relatives à l’affinité entre utilisateur et appareil. Les informations d'état ne sont pas chiffrées lors de leur transmission, sauf si les clients sont configurés pour communiquer avec des points de gestion à l'aide de HTTPS. Les informations d'état sont stockées dans la base de données sous une forme non chiffrée.  
-  Les informations sur l’ordinateur et sur l’utilisation du compte de connexion ainsi que les informations d’état ne sont pas envoyées à Microsoft.  
-  Les informations sur l’ordinateur et sur la connexion qui sont utilisées pour déterminer l’affinité entre utilisateur et appareil sont toujours activées. En outre, les utilisateurs et utilisateurs administratifs peuvent fournir des informations relatives à l'affinité entre périphérique et utilisateur.  

##  <a name="application-catalog"></a>Catalogue d'applications  
-  Le catalogue des applications permet à l’administrateur Configuration Manager de publier n’importe quel programme, script ou application exécutable par les utilisateurs. Configuration Manager n’a aucun contrôle sur les types de programmes ou de scripts publiés dans le catalogue, ni sur le type des informations qu’ils transmettent.    
-  Configuration Manager peut transmettre des informations entre les clients et les rôles de systèmes de site du catalogue des applications. Les informations peuvent identifier les comptes d’ordinateur et de connexion. Les informations transmises entre le client et les serveurs ne sont pas chiffrées, sauf si ces rôles de système de site sont configurés pour exiger que les clients se connectent à l'aide de HTTPS.  
-  Les informations sur la demande d’approbation d’application sont enregistrées dans la base de données Configuration Manager. Les demandes qui sont annulées ou refusées, ainsi que les entrées d’historique de demande correspondantes, sont supprimées par défaut après 30 jours. Le comportement de suppression peut être configuré en définissant la tâche de maintenance de site **Supprimer les anciennes données de demande d'application** . Les demandes d’approbation d’application qui sont à l’état Approuvé et En attente ne sont jamais supprimées.  
-  Les informations envoyées vers et depuis le catalogue d'applications et ne sont pas transmises à Microsoft.  
-  Le catalogue des applications n'est pas installé par défaut. Cette installation nécessite plusieurs étapes de configuration.  
