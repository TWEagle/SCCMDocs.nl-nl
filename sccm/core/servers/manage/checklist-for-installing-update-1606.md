---
title: "Liste de contrôle pour 1606 | Microsoft Docs"
description: "Découvrez les mesures à prendre avant d’effectuer la mise à jour de System Center Configuration Manager version 1511 ou 1602 vers la version 1606."
ms.custom: na
ms.date: 6/6/2017
ms.reviewer: na
ms.suite: na
ms.prod: configuration-manager
ms.technology: configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 75652cd2-a95a-46c5-91c1-6d43fc8e787e
caps.latest.revision: "7"
author: Brenduns
ms.author: brenduns
manager: angrobe
ms.openlocfilehash: a6bda116499845fedff0126e2890755931de85bb
ms.sourcegitcommit: 51fc48fb023f1e8d995c6c4eacfda7dbec4d0b2f
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/07/2017
---
# <a name="checklist-for-installing-update-1606-for-system-center-configuration-manager"></a>Liste de contrôle pour l’installation de la mise à jour 1606 pour System Center Configuration Manager

*S’applique à : System Center Configuration Manager (Current Branch)*

La version 1606 de la branche CB (Current Branch) de System Center Configuration Manager est une mise à jour que vous pouvez utiliser pour effectuer la mise à jour à partir de la version 1511 ou 1602.

Avant d’installer la version 1606 en tant que mise à jour, passez en revue les informations et la liste de contrôle suivantes pour connaître les mesures à prendre avant de commencer la mise à jour.

Pour plus d’informations sur les versions de base de référence, consultez [Versions de base de référence et de mise à jour](../../../core/servers/manage/updates.md#bkmk_Baselines) dans [Mises à jour pour System Center Configuration Manager](../../../core/servers/manage/updates.md).

 ## <a name="about-installing-update-1606"></a>À propos de l’installation de la mise à jour 1606

En tant que *mise à jour*, vous ne pouvez installer la version 1606 que sur le site de niveau supérieur de votre hiérarchie. Cela signifie que vous lancez l’installation à partir de votre site d’administration centrale si en avez un, ou à partir de votre site principal autonome.  

-   Les sites principaux enfants installent automatiquement la mise à jour après que le site d’administration centrale a fini de l’installer. Vous pouvez utiliser des fenêtres de service pour contrôler le moment auquel un site installe les mises à jour. Avant la version 1606, les fenêtres de service étaient désignées sous le nom de fenêtres de maintenance. Pour plus d’informations, consultez [Fenêtres de maintenance pour les serveurs de site](/sccm/core/servers/manage/service-windows).  

-   Une fois que le site parent principal a installé la mise à jour, vous devez mettre à jour manuellement les sites secondaires à partir de la console Configuration Manager. La mise à jour automatique des serveurs de sites secondaires n’est pas prise en charge.  

Quand le serveur de site installe la mise à jour, les rôles de système de site installés sur le serveur de site et sur des ordinateurs distants sont automatiquement mis à jour. Par conséquent, avant d’installer la mise à jour, vérifiez que chaque serveur de système de site remplit les nouveaux prérequis pour les opérations avec la nouvelle version de mise à jour.  

La première fois que vous utilisez une console Configuration Manager à l’issue de la mise à jour, vous êtes invité à mettre à jour cette console.  Pour cela, vous devez exécuter le programme d’installation de Configuration Manager sur l’ordinateur hébergeant la console, puis choisir l’option de mise à jour de la console. Nous vous recommandons de ne pas retarder l’installation de la mise à jour sur la console.

 **Problèmes connus pour cette mise à jour**   
  Les problèmes suivants se posent quand vous affichez l’état de l’installation du package de mise à jour :
  - Lors de la mise à jour de la version 1602 vers 1606, l’étape **Extraire la charge utile du package de mise à jour** affiche l’état **Non démarré**, même si le téléchargement est terminé.
  - Lors de la mise à jour de la version 1511 vers 1606, certaines étapes présentent l’état **Terminé**, mais n’affichent pas de valeur pour **Heure de la dernière mise à jour**.


## <a name="checklist"></a>Liste de contrôle  

 **Vérifiez que tous les sites exécutent une version prise en charge de System Center Configuration Manager** : avant de démarrer l’installation de la mise à jour 1606, chaque serveur de site dans la hiérarchie doit exécuter la même version de System Center Configuration Manager, que ce soit la version 1511 ou 1602.

 **Examinez les versions installées de Microsoft .NET sur les serveurs de système de site** : quand un site installe la mise à jour 1606, Configuration Manager installe automatiquement le .NET Framework 4.5.2 sur chaque ordinateur hébergeant un des rôles de système de site suivants (si le .NET Framework 4.5 ou ultérieur n’est pas déjà installé) :  

-   Point proxy d'inscription  

-   Point d'inscription  

-   Point de gestion  

-   Point de connexion de service  

Cette installation peut mettre le serveur de système de site en état d’attente de redémarrage, et signaler des erreurs sur l’Afficheur des messages d’état du composant Configuration Manager. En outre, des applications .NET sur le serveur peuvent présenter des défaillances aléatoires jusqu’au redémarrage du serveur.  

 Pour plus d’informations, consultez [Prérequis des sites et systèmes de site](../../../core/plan-design/configs/site-and-site-system-prerequisites.md).  

 **Examinez l’état du site et de la hiérarchie, et vérifiez l’absence de tout problème non résolu :** avant de mettre à jour un site, résolvez tous les problèmes opérationnels pour le serveur de site, le serveur de bases de données du site et les rôles de système de site installés sur des ordinateurs distants. Une mise à niveau de site peut échouer en raison de l’existence de problèmes opérationnels.

 Pour plus d'informations, voir [Utiliser des alertes et le système d’état pour System Center Configuration Manager](../../../core/servers/manage/use-alerts-and-the-status-system.md).  

 **Examinez la réplication des fichiers et données entre sites :**  vérifiez que la réplication des fichiers et bases de données entre les sites est opérationnelle et active. Des retards ou backlogs dans ces domaines peuvent perturber ou empêcher la mise à jour.    

Pour la réplication de la base de données, vous pouvez utiliser l’Analyseur de lien de réplication pour faciliter la résolution des problèmes avant de commencer la mise à jour. Pour plus d’informations, consultez [À propos de l’analyseur de lien de réplication](../../../core/servers/manage/monitor-hierarchy-and-replication-infrastructure.md#BKMK_RLA) dans la rubrique [Surveiller l’infrastructure de la hiérarchie et de la réplication dans System Center Configuration Manager](../../../core/servers/manage/monitor-hierarchy-and-replication-infrastructure.md).  

 **Installez toutes les mises à jour critiques applicables pour les systèmes d’exploitation sur les ordinateurs hébergeant le site, le serveur de base de données du site et les rôles de système de site distants :** avant d’installer une mise à jour pour Configuration Manager, installez toutes les mises à jour critiques pour chaque système de site concerné. Si vous installez une mise à jour qui nécessite un redémarrage, redémarrez les ordinateurs concernés avant d'entreprendre la mise à jour.  

 **Désactivez les réplicas de base de données pour les points de gestion sur les sites principaux :** Configuration Manager ne peut pas mettre à jour correctement un site principal ayant un réplica de base de données activé pour des points de gestion. Désactivez la réplication de base de données avant d’installer une mise à jour pour Configuration Manager.  

Pour plus d’informations, consultez [Réplicas de base de données pour les points de gestion de System Center Configuration Manager](../../../core/servers/deploy/configure/database-replicas-for-management-points.md).  

 **Définir un basculement manuel pour les groupes de disponibilité SQL Server AlwaysOn :**  
 Avant d’installer les mises à jour, comme la version 1606, vérifiez que le groupe de disponibilité est défini pour un basculement manuel. Une fois le site mis à jour, vous pouvez restaurer le basculement automatique. Pour plus d’informations, consultez [SQL Server AlwaysOn pour une base de données de site](../../../core/servers/deploy/configure/sql-server-alwayson-for-a-highly-available-site-database.md).

 **Reconfigurez les points de mise à jour logicielle qui utilisent des équilibrages de la charge réseau :** Configuration Manager ne peut pas mettre à jour un site utilisant un cluster d’équilibrage de la charge réseau (NLB) pour héberger des points de mise à jour logicielle.  

Si vous utilisez des clusters NLB pour les points de mise à jour logicielle, utilisez Windows PowerShell pour supprimer le cluster NLB.    

 Pour plus d’informations, consultez [Planifier les mises à jour logicielles dans System Center Configuration Manager](../../../sum/plan-design/plan-for-software-updates.md).  

 **Désactivez toutes les tâches de maintenance de site sur chaque site pendant la durée de l’installation de la mise à jour sur celui-ci** : avant d’installer la mise à jour, désactivez toute tâche de maintenance de site susceptible de s’exécuter pendant que le processus de mise à jour est actif. Cela inclut, sans toutefois s'y limiter, les tâches suivantes :  

-   Serveur de site de sauvegarde  

-   Supprimer les anciennes opérations du client  

-   Supprimer les données de découverte anciennes  

Si une tâche de maintenance de base de données du site s’exécute pendant l’installation de la mise à jour, celle-ci peut échouer. Avant de désactiver une tâche, enregistrez sa planification pour pouvoir restaurer sa configuration une fois la mise à jour installée.  

Pour plus d’informations, consultez [Tâches de maintenance pour System Center Configuration Manager](../../../core/servers/manage/maintenance-tasks.md) et [Référence des tâches de maintenance pour System Center Configuration Manager](../../../core/servers/manage/reference-for-maintenance-tasks.md).  

 **Créez une sauvegarde de la base de données du site d’administration centrale et des sites principaux :** avant de mettre à jour un site, sauvegardez sa base de données pour être certain de disposer d’une sauvegarde correcte utilisable en cas de récupération d’urgence.   

Pour plus d’informations, consultez [Sauvegarde et récupération pour System Center Configuration Manager](../../../protect/understand/backup-and-recovery.md).  

<!-- Removed from update guidance 6/6/2017
 **Test the database upgrade on a copy of the most recent site database backup:** Before you update a System Center Configuration Manager central administration site or primary site, test the site database upgrade process on a copy of the site database.  

-   You should test the site database upgrade process because when you upgrade a site, the site database might be modified.  

-   Although a test database upgrade is not required, it can identify problems for the upgrade before your production database is affected.  

-   A failed site database upgrade can render your site database inoperable and might require a site recovery to restore functionality.  

-   Although the site database is shared between sites in a hierarchy, plan to test the database at each applicable site before you upgrade that site.  

-   If you use database replicas for management points at a primary site, disable replication before you create the backup of the site database.  

Configuration Manager does not support the backup of secondary sites nor does it support the test upgrade of a secondary site database.   

Do not run a test database upgrade on the production site database. Doing so updates the site database and could render your site inoperable. For more information, For more information, see [Step 2: Test the database upgrade before installing an update](/sccm/core/servers/manage/install-in-console-updates#bkmk_step2) from **Before you install an in-console update**.
-->

 **Planifiez un test du client** : quand vous installez une mise à jour qui affecte le client, vous pouvez la tester en mode préproduction avant de procéder au déploiement et à la mise à niveau de tous vos clients actifs.   

 Pour tirer parti de cette option, avant de commencer l’installation de la mise à jour, vous devez configurer votre site pour qu’il prenne en charge les mises à niveau automatiques pour la préproduction. Pour plus d’informations, consultez [Mettre à niveau les clients dans System Center Configuration Manager](../../../core/clients/manage/upgrade/upgrade-clients.md) et   
[Guide pratique pour tester les mises à niveau du client dans un regroupement de préproduction dans System Center Configuration Manager](../../../core/clients/manage/upgrade/test-client-upgrades.md).  

 **Planifiez l’utilisation de fenêtres de service pour contrôler le moment où les serveurs de site installent les mises à jour :** vous pouvez utiliser les fenêtres de service pour définir une période au cours de laquelle des mises à jour peuvent être installées sur un serveur de site.

Cela peut vous aider à contrôler le moment où les sites au sein de votre hiérarchie installent la mise à jour.
Avant la version 1606, les fenêtres de service étaient désignées sous le nom de fenêtres de maintenance. Pour plus d’informations, consultez [Fenêtres de maintenance pour les serveurs de site](/sccm/core/servers/manage/service-windows).  

 **Exécutez l’outil de vérification des prérequis à l’installation** : avant d’installer la mise à jour 1606, vous pouvez exécuter l’outil de vérification des prérequis indépendamment de l’installation de la mise à jour. Quand vous installez la mise à jour sur le site, l’outil de vérification des prérequis s’exécute à nouveau.  

Pour plus d’informations, consultez **Étape 3 : exécuter l’Outil de vérification des conditions préalables avant d’installer une mise à jour** dans la rubrique [Mises à jour pour System Center Configuration Manager](../../../core/servers/manage/install-in-console-updates.md).  

> [!IMPORTANT]  
>  Quand l’outil de vérification des prérequis s’exécute indépendamment ou dans le cadre de l’installation d’une mise à jour, le processus met à jour certains fichiers sources du produit qui sont utilisés pour les tâches de maintenance de site. Par conséquent, après l’exécution de l’outil de vérification des prérequis, mais avant l’installation de la mise à jour 1606, si vous devez effectuer une tâche de maintenance de site, exécutez **Setupwfe.exe** (programme d’installation de Configuration Manager) à partir du dossier CD.Latest sur le serveur de site.  

 **Mettez à jour les sites :** vous êtes maintenant prêt à commencer l’installation de la mise à jour pour votre hiérarchie.  
  Nous vous recommandons de planifier l’installation de la mise à jour en dehors des heures de bureau normales pour chaque site, quand le processus d’installation de la mise à jour et ses actions pour réinstaller les composants du site et les rôles de système de site auront le moins d’effet sur les opérations de votre entreprise.

Pour plus d’informations, consultez [Mises à jour pour System Center Configuration Manager](../../../core/servers/manage/updates.md).  
