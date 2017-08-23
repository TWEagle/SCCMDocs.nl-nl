---
title: "Liste de contrôle pour 1610 | System Center Configuration Manager"
description: "Découvrez les actions à entreprendre avant d’effectuer la mise à jour vers System Center Configuration Manager version 1610."
ms.custom: na
ms.date: 6/6/2017
ms.reviewer: na
ms.suite: na
ms.prod: configuration-manager
ms.technology: configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 7b411cb0-4fd1-41f2-a2f6-33738a5bde96
caps.latest.revision: "7"
author: Brenduns
ms.author: brenduns
manager: angrobe
ms.openlocfilehash: 54b243fd33ed13b8ccde48fa5e2525204455d96c
ms.sourcegitcommit: 51fc48fb023f1e8d995c6c4eacfda7dbec4d0b2f
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/07/2017
---
# <a name="checklist-for-installing-update-1610-for-system-center-configuration-manager"></a>Liste de contrôle pour l’installation de la mise à jour 1610 pour System Center Configuration Manager

*S’applique à : System Center Configuration Manager (Current Branch)*

Quand vous utilisez Current Branch de System Center Configuration Manager, vous pouvez installer la mise à jour dans la console de la version 1610 pour mettre à jour votre hiérarchie à partir de la version 1606. Si votre hiérarchie exécute la version 1511, 1602 ou 1606, vous pouvez effectuer la mise à jour vers la version 1610.

Pour obtenir la mise à jour de la version 1610, vous devez utiliser un rôle de système de site de point de connexion de service sur le site de niveau supérieur de votre hiérarchie. Cela peut être en mode en ligne ou hors connexion. Une fois que votre hiérarchie a téléchargé le package de mises à jour de Microsoft, celui-se trouve dans la console sous **Administration &gt; Vue d’ensemble &gt; Services cloud &gt; Mises à jour et maintenance**.

-   Quand la mise à jour est répertoriée comme **disponible**, elle est prête à être installée. Avant d’installer la version 1610, passez en revue les informations suivantes [sur l’installation de la mise à jour 1610](#about-installing-update-1610) et la [liste de contrôle](#checklist) pour connaître les configurations à effectuer avant de commencer la mise à jour.

-   Si la mise à jour s’affiche en tant que **Téléchargement en cours** et ne change pas, recherchez les erreurs dans les journaux **hman.log** et **dmpdownloader.log**.

    -   En règle générale, vous pouvez également redémarrer le service **SMS_Executive** sur le serveur de site pour relancer le téléchargement des fichiers de redistribution des mises à jour.

    -   Un autre problème courant de téléchargement se produit quand les paramètres du serveur proxy empêchent les téléchargements à partir de <http://silverlight.dlservice.microsoft.com> et <http://download.microsoft.com>.

Pour plus d’informations sur l’installation des mises à jour, consultez [Mises à jour et maintenance dans la console](/sccm/core/servers/manage/updates#a-namebkmkinconsolea-in-console-updates-and-servicing).

Pour plus d’informations sur les versions de Current Branch, consultez [Versions de base et de mise à jour](/sccm/core/servers/manage/updates#bkmk_Baselines) dans [Mises à jour pour System Center Configuration Manager](/sccm/core/servers/manage/updates).

## <a name="about-installing-update-1610"></a>À propos de l’installation de la mise à jour 1610

**Sites :**  
Vous ne pouvez installer la mise à jour 1610 que sur le site de niveau supérieur de votre hiérarchie. Cela signifie que vous lancez l’installation à partir de votre site d’administration centrale si en avez un, ou à partir de votre site principal autonome. Après l’installation de la mise à jour sur le site de niveau supérieur, les sites enfants ont le comportement de mise à jour suivant :

-   Les sites principaux enfants installent automatiquement la mise à jour quand le site d’administration centrale a fini de l’installer. Vous pouvez utiliser des fenêtres de service pour contrôler le moment auquel un site installe les mises à jour. Avant la version 1606, les fenêtres de service étaient désignées sous le nom de fenêtres de maintenance. Pour plus d’informations, consultez [Fenêtres de maintenance pour les serveurs de site](/sccm/core/servers/manage/service-windows).

-   Après que le site parent principal a installé la mise à jour, vous devez mettre à jour manuellement les sites secondaires à partir de la console Configuration Manager. La mise à jour automatique des serveurs de sites secondaires n’est pas prise en charge.

**Rôles de système de site :**  
Quand le serveur de site installe la mise à jour, les rôles de système de site installés sur le serveur de site et sur des ordinateurs distants sont automatiquement mis à jour. Par conséquent, avant d’installer la mise à jour, vérifiez que chaque serveur de système de site remplit les nouveaux prérequis pour les opérations avec la nouvelle version de mise à jour.

**Consoles Configuration Manager :**   
La première fois que vous utilisez une console Configuration Manager à l’issue de la mise à jour, vous êtes invité à mettre à jour cette console. Pour cela, vous devez exécuter le programme d’installation de Configuration Manager sur l’ordinateur hébergeant la console, puis choisir l’option de mise à jour de la console. Nous vous recommandons de ne pas retarder l’installation de la mise à jour sur la console.



## <a name="checklist"></a>Liste de contrôle

**Vérifiez que tous les sites exécutent une version prise en charge de System Center Configuration Manager** : avant de démarrer l’installation de la mise à jour 1610, chaque site dans la hiérarchie doit exécuter la même version de System Center Configuration Manager, que ce soit la version 1511, 1602 ou 1606.

**Vérifiez l’état de votre contrat Software Assurance ou des droits d’abonnement équivalents :**   
vous devez disposer d’un contrat Software Assurance actif pour installer la mise à jour 1610. Quand vous installez la version 1610, vous avez la possibilité sous l’onglet **Licences** de confirmer la **date d’expiration de Software Assurance**.

Il s’agit d’une valeur facultative que vous pouvez spécifier comme rappel pratique de la date d’expiration de votre licence qui est visible durant l’installation de mises à jour ultérieures. Si vous avez installé Configuration Manager à partir du média de base de référence de la version 1606, vous avez peut-être déjà spécifié cette valeur pendant l’installation, ou sous l’onglet **Licences** de **Paramètres de hiérarchie** après l’installation du site.

Pour plus d’informations, voir [Licences et branches pour System Center Configuration Manager](/sccm/core/understand/learn-more-editions).

**Examinez les versions installées de Microsoft .NET sur les serveurs de système de site** : quand un site installe la mise à jour 1610, Configuration Manager installe automatiquement le .NET Framework 4.5.2 sur chaque ordinateur hébergeant un des rôles de système de site suivants (si le .NET Framework 4.5 ou ultérieur n’est pas déjà installé) :

-   Point proxy d'inscription
-   Point d'inscription
-   Point de gestion
-   Point de connexion de service

Cette installation peut mettre le serveur de système de site en état d’attente de redémarrage, et signaler des erreurs sur l’Afficheur des messages d’état du composant Configuration Manager. En outre, des applications .NET sur le serveur peuvent présenter des défaillances aléatoires jusqu’au redémarrage du serveur.

Pour plus d’informations, consultez [Prérequis des sites et systèmes de site](/sccm/core/plan-design/configs/site-and-site-system-prerequisites).

**Examinez l’état du site et de la hiérarchie, et vérifiez l’absence de tout problème non résolu :** avant de mettre à jour un site, résolvez tous les problèmes opérationnels pour le serveur de site, le serveur de bases de données du site et les rôles de système de site installés sur des ordinateurs distants. Une mise à niveau de site peut échouer en raison de l’existence de problèmes opérationnels.

Pour plus d'informations, voir [Utiliser des alertes et le système d’état pour System Center Configuration Manager](/sccm/core/servers/manage/use-alerts-and-the-status-system).

**Examinez la réplication des fichiers et données entre sites :**   
vérifiez que la réplication des fichiers et bases de données entre les sites est opérationnelle et active. Des retards ou backlogs dans ces domaines peuvent perturber ou empêcher la mise à jour.
Pour la réplication de la base de données, vous pouvez utiliser l’Analyseur de lien de réplication pour faciliter la résolution des problèmes avant de commencer la mise à jour.

Pour plus d’informations, consultez [À propos de l’analyseur de lien de réplication](/sccm/core/servers/manage/monitor-hierarchy-and-replication-infrastructure#BKMK_RLA) dans la rubrique [Surveiller l’infrastructure de la hiérarchie et de la réplication dans System Center Configuration Manager](/sccm/core/servers/manage/monitor-hierarchy-and-replication-infrastructure).

**Installez toutes les mises à jour critiques applicables pour les systèmes d’exploitation sur les ordinateurs hébergeant le site, le serveur de base de données du site et les rôles de système de site distants :** avant d’installer une mise à jour pour Configuration Manager, installez toutes les mises à jour critiques pour chaque système de site concerné. Si vous installez une mise à jour qui nécessite un redémarrage, redémarrez les ordinateurs concernés avant de lancer la mise à jour Configuration Manager.

**Désactivez les réplicas de base de données pour les points de gestion au niveau des sites principaux :**   
Configuration Manager ne peut pas réussir la mise à jour d’un site principal ayant un réplica de base de données activé pour les points de gestion. Désactivez la réplication de base de données avant d’installer une mise à jour pour Configuration Manager.

Pour plus d’informations, consultez [Réplicas de base de données pour les points de gestion de System Center Configuration Manager](/sccm/core/servers/deploy/configure/database-replicas-for-management-points).

**Définissez un basculement manuel pour les groupes de disponibilité SQL Server AlwaysOn :**   
Avant d’installer les mises à jour, comme la version 1610, vérifiez que le groupe de disponibilité est défini pour un basculement manuel. Une fois le site mis à jour, vous pouvez restaurer le basculement automatique. Pour plus d’informations, consultez [SQL Server AlwaysOn pour une base de données de site](/sccm/core/servers/deploy/configure/sql-server-alwayson-for-a-highly-available-site-database).

**Reconfigurez les points de mise à jour logicielle qui utilisent l’équilibrage de la charge réseau (NLB) :**   
Configuration Manager ne peut pas mettre à jour un site qui utilise un cluster d’équilibrage de la charge réseau (NLB) pour héberger des points de mise à jour logicielle.

Si vous utilisez des clusters NLB pour les points de mise à jour logicielle, utilisez Windows PowerShell pour supprimer le cluster NLB.
Pour plus d’informations, consultez [Planifier les mises à jour logicielles dans System Center Configuration Manager](/sccm/sum/plan-design/plan-for-software-updates).

**Désactivez toutes les tâches de maintenance de site sur chaque site pendant la durée de l’installation de la mise à jour sur ce site :**   
Avant d’installer la mise à jour, désactivez toutes les tâches de maintenance de site qui peuvent s’exécuter pendant le processus de mise à jour. Cela inclut, sans toutefois s'y limiter, les tâches suivantes :

-   Serveur de site de sauvegarde
-   Supprimer les anciennes opérations du client
-   Supprimer les données de découverte anciennes

Si une tâche de maintenance de base de données du site s’exécute pendant l’installation de la mise à jour, celle-ci peut échouer. Avant de désactiver une tâche, enregistrez sa planification pour pouvoir restaurer sa configuration une fois la mise à jour installée.

Pour plus d’informations, consultez [Tâches de maintenance pour System Center Configuration Manager](/sccm/core/servers/manage/maintenance-tasks) et [Référence des tâches de maintenance pour System Center Configuration Manager](/sccm/core/servers/manage/reference-for-maintenance-tasks).

**Créez une sauvegarde de la base de données du site d’administration centrale et des sites principaux :** avant de mettre à jour un site, sauvegardez sa base de données pour être certain de disposer d’une sauvegarde correcte utilisable en cas de récupération d’urgence.

Pour plus d’informations, consultez [Sauvegarde et récupération pour System Center Configuration Manager](/sccm/protect/understand/backup-and-recovery).

<!-- Removed from update guidance 6/6/2017
**Test the database upgrade on a copy of the most recent site database backup:** 
Before you update a System Center Configuration Manager central administration site or primary site, test the site database upgrade process on a copy of the site database.

-   We recommend that you test the site database upgrade process because when you upgrade a site, the site database might be modified.

-   Although a test database upgrade is not required, it can identify problems for the upgrade before your production database is affected.

-   A failed site database upgrade can render your site database inoperable and might require a site recovery to restore functionality.

-   Although the site database is shared between sites in a hierarchy, plan to test the database at each applicable site before you upgrade that site.

-   If you use database replicas for management points at a primary site, disable replication before you create the backup of the site database.

Configuration Manager does not support the backup of secondary sites nor does it support the test upgrade of a secondary site database.

Do not run a test database upgrade on the production site database. Doing so updates the site database and could render your site inoperable. For more information, see [Step 2: Test the database upgrade before installing an update](/sccm/core/servers/manage/install-in-console-updates#bkmk_step2) from **Before you install an in-console update**.
-->

**Planifiez un test du client :**   
Quand vous installez une mise à jour qui affecte le client, vous pouvez la tester en mode préproduction avant de procéder au déploiement et à la mise à niveau de votre client actif.

Pour tirer parti de cette option, vous devez configurer votre site pour qu’il prenne en charge les mises à niveau automatiques pour la préproduction avant de commencer l’installation de la mise à jour.

Pour plus d’informations, consultez [Mettre à niveau les clients dans System Center Configuration Manager](/sccm/core/clients/manage/upgrade/upgrade-clients) et [Comment tester les mises à niveau du client dans un regroupement de préproduction dans System Center Configuration Manager](/sccm/core/clients/manage/upgrade/test-client-upgrades).

**Planifiez l’utilisation des fenêtres de service pour contrôler le moment auquel les serveurs de site installent les mises à jour :**   
Vous pouvez utiliser les fenêtres de service pour définir une période au cours de laquelle les mises à jour à un serveur de site peuvent être installées.

Cela peut vous aider à contrôler le moment où les sites au sein de votre hiérarchie installent la mise à jour. Avant la version 1606, les fenêtres de service étaient désignées sous le nom de fenêtres de maintenance. Pour plus d’informations, consultez [Fenêtres de maintenance pour les serveurs de site](/sccm/core/servers/manage/service-windows).

**Exécutez l’outil de vérification des prérequis du programme d’installation :**   
Quand la mise à jour est répertoriée dans la console comme **Disponible**, vous pouvez exécuter indépendamment l’outil de vérification des prérequis avant d’installer la mise à jour. (Quand vous installez la mise à jour sur le site, l’outil de vérification des prérequis s’exécute à nouveau.)

Pour exécuter une vérification des prérequis à partir de la console, accédez à **Administration > Vue d’ensemble > Services cloud > Mises à jour et maintenance**. Ensuite, cliquez avec le bouton droit sur **Package de mise à jour 1610 de Configuration Manager**, puis choisissez **Exécuter la vérification des prérequis**.

Pour plus d’informations sur le démarrage et la surveillance de la vérification des prérequis, consultez **Étape 3 : exécuter l’outil de vérification des prérequis avant d’installer une mise à jour** dans la rubrique [Installer des mises à jour dans la console pour System Center Configuration Manager](/sccm/core/servers/manage/install-in-console-updates).

> [!IMPORTANT]  
> Quand l’outil de vérification des prérequis s’exécute indépendamment ou dans le cadre de l’installation d’une mise à jour, le processus met à jour certains fichiers sources du produit qui sont utilisés pour les tâches de maintenance de site. Par conséquent, après l’exécution de l’outil de vérification des prérequis, mais avant l’installation de la mise à jour 1610, si vous devez effectuer une tâche de maintenance de site, exécutez **Setupwfe.exe** (programme d’installation de Configuration Manager) à partir du dossier CD.Latest sur le serveur de site.

**Mettez à jour les sites :**   
Vous êtes maintenant prêt à commencer l’installation de la mise à jour pour votre hiérarchie. Pour plus d’informations sur l’installation de la mise à jour, consultez [Installer des mises à jour dans la console](/sccm/core/servers/manage/install-in-console-updates#a-namebkmkinstalla-install-in-console-updates).

Nous vous recommandons de planifier l’installation de la mise à jour en dehors des heures de bureau normales pour chaque site, quand le processus d’installation de la mise à jour et ses actions pour réinstaller les composants du site et les rôles de système de site auront le moins d’effet sur les opérations de votre entreprise.

Pour plus d’informations, consultez [Mises à jour pour System Center Configuration Manager](/sccm/core/servers/manage/updates).
