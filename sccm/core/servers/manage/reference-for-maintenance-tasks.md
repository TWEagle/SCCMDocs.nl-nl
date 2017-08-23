---
title: "Référence des tâches de maintenance | Microsoft Docs"
description: "Lisez les détails de chaque tâche de maintenance de site de System Center Configuration Manager, et déterminez si ces tâches sont activées par défaut."
ms.custom: na
ms.date: 3/8/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 68dc6acd-5848-47a4-b4c1-ffa40e47890b
caps.latest.revision: "16"
caps.handback.revision: "0"
author: Brenduns
ms.author: brenduns
manager: angrobe
ms.openlocfilehash: a2d4420c2274a9b1ceb47ffd267849fdb5a55a61
ms.sourcegitcommit: 51fc48fb023f1e8d995c6c4eacfda7dbec4d0b2f
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/07/2017
---
# <a name="reference-for-maintenance-tasks-for-system-center-configuration-manager"></a>Référence des tâches de maintenance pour System Center Configuration Manager

*S’applique à : System Center Configuration Manager (Current Branch)*

Cette rubrique répertorie les détails de chaque tâche de maintenance de site de System Center Configuration Manager et spécifie les types de sites sur lesquels la tâche est disponible. Chaque entrée indique également si la tâche est activée ou non par défaut. Pour plus d’informations sur la planification et la configuration de sites pour exécuter des tâches de maintenance, consultez [Tâches de maintenance pour System Center Configuration Manager](../../../core/servers/manage/maintenance-tasks.md).  

**Serveur de site de sauvegarde** : cette tâche permet de préparer la récupération des données critiques. Vous pouvez créer une sauvegarde de vos informations critiques pour restaurer un site et la base de données Configuration Manager. Pour plus d’informations, consultez [Sauvegarde et récupération pour System Center Configuration Manager](../../../protect/understand/backup-and-recovery.md).  

-   **Site d’administration centrale** : activé    
-   **Site principal**non activé    
-   Site secondaire : non disponible  

**Vérifier le titre de l’application à l’aide des informations d’inventaire** : cette tâche permet de maintenir la cohérence entre les titres de logiciels rapportés dans l’inventaire logiciel et les titres de logiciels du catalogue Asset Intelligence. Pour plus d’informations, consultez [Présentation d’Asset Intelligence dans System Center Configuration Manager](../../../core/clients/manage/asset-intelligence/introduction-to-asset-intelligence.md).  

-   **Site d’administration centrale** : activé    
-   **Site principal**  : activé    
-   Site secondaire : non disponible  

**Remettre à zéro l’indicateur d’installation** : cette tâche permet de supprimer l’indicateur installé pour les clients qui n’envoient pas d’enregistrement de découverte par pulsations d’inventaire durant la période de **Redécouverte du client**. L’indicateur installé empêche l’installation push automatique du client sur un ordinateur pouvant disposer d’un client Configuration Manager actif.  

-   Site d’administration centrale : non disponible    
-   **Site principal**non activé    
-   Site secondaire : non disponible  

**Supprimer les anciennes données de demande d’application** : cette tâche permet de supprimer les demandes d’application anciennes de la base de données. Pour plus d’informations sur les demandes d’application, consultez [Créer et déployer une application avec System Center Configuration Manager](/sccm/apps/get-started/create-and-deploy-an-application).  

-   Site d’administration centrale : non disponible
-   **Site principal**  : activé    
-   Site secondaire : non disponible  

**Supprimer l’historique de téléchargement de clients anciens** : utilisez cette tâche pour supprimer les données historiques relatives à la source de téléchargement utilisée par les clients. Les informations relatives à la source du téléchargement permettent de remplir le [tableau de bord Sources de données du client](/sccm/core/servers/deploy/configure/monitor-content-you-have-distributed#client-data-sources-dashboard).  
-  Site d’administration centrale : non disponible
-    **Site principal**  - Activée
-  Site secondaire - Non disponible

**Supprimer les anciennes opérations des clients** : cette tâche permet de supprimer de la base de données de site toutes les anciennes données pour les opérations des clients. Cela comprend par exemple les données pour les notifications des clients anciennes ou ayant expiré (comme les demandes de téléchargement pour les stratégies utilisateur ou ordinateur) et pour Endpoint Protection (comme les demandes effectuées par un utilisateur administratif pour que les clients exécutent une analyse ou téléchargent des définitions mises à jour).

-   **Site d’administration centrale** : activé    
-   **Site principal**  : activé    
-   Site secondaire : non disponible  

**Supprimer historique de présence de clients anciens** : cette tâche permet de supprimer les informations d’historique sur le statut de connexion des clients, enregistrées par la notification client, qui sont antérieures à l’heure spécifiée. Pour plus d’informations sur la notification client, consultez [Comment surveiller des clients dans System Center Configuration Manager](../../../core/clients/manage/monitor-clients.md).  

-   **Site d’administration centrale** : activé   
-   **Site principal**  : activé    
-   Site secondaire : non disponible  

**Supprimer les anciennes données de trafic de la passerelle de gestion cloud** : cette tâche permet de supprimer toutes les anciennes données sur le trafic de la base de données du site qui transite via la [passerelle de gestion cloud](/sccm/core/clients/manage/plan-cloud-management-gateway). Cela inclut par exemple les données sur le nombre de demandes, le nombre total d’octets des demandes et des réponses, ainsi que le nombre de demandes ayant échoué et le nombre maximum de demandes simultanées.  
- **Site d’administration centrale** - Activée
- **Site principal**  - Activée
- Site secondaire - Non disponible


**Supprimer les fichiers collectés anciens** : cette tâche permet de supprimer de la base de données d’anciennes informations sur les fichiers collectés. Cette tâche supprime également les fichiers collectés à partir de la structure de dossier du serveur de site sur le site sélectionné. Par défaut, les cinq copies les plus récentes des fichiers collectés sont stockées sur le serveur de site dans le répertoire **Inboxes\sinv.box\FileCol**. Pour plus d’informations, consultez [Présentation de l’inventaire logiciel dans System Center Configuration Manager](/sccm/core/clients/manage/inventory/introduction-to-software-inventory).  

-   Site d’administration centrale : non disponible    
-   **Site principal**  : activé    
-   Site secondaire : non disponible  

**Supprimer les données d’associations d’ordinateurs anciennes** : cette tâche permet de supprimer de la base de données d’anciennes données d’associations d’ordinateur du déploiement de système d’exploitation. Ces informations sont utilisées dans le cadre de l'exécution de restaurations de l'état utilisateur. Pour plus d’informations sur les associations d’ordinateurs, consultez [Gérer l’état utilisateur dans System Center Configuration Manager](../../../osd/get-started/manage-user-state.md).  

-   Site d’administration centrale : non disponible    
-   **Site principal**  : activé    
-   Site secondaire : non disponible  

**Supprimer les données de détection de suppression anciennes** : cette tâche permet de supprimer de la base de données d’anciennes données ayant été créées par Extraction Views. Par défaut, Extraction Views est désactivé. Vous pouvez uniquement l’activer à l’aide du SDK Configuration Manager. Sauf si Extraction Views est activé, il n'y a pas de données à supprimer pour cette tâche.  

-   **Site d’administration centrale** : activé    
-   **Site principal**  : activé    
-   Site secondaire : non disponible  

**Supprimer l’ancien enregistrement de réinitialisation de périphérique** : cette tâche permet de supprimer de la base de données d’anciennes données d’actions de réinitialisation d’appareils mobiles. Pour plus d’informations sur la réinitialisation des appareils mobiles, consultez [Protéger les données à l’aide de la réinitialisation à distance, du verrouillage à distance ou de la réinitialisation du code d’accès en utilisant System Center Configuration Manager](/sccm/mdm/deploy-use/wipe-lock-reset-devices).  

-   Site d’administration centrale : non disponible    
-   **Site principal**  : activé    
-   Site secondaire : non disponible  

**Supprimer les anciens périphériques gérés par le connecteur du serveur Exchange Server** : cette tâche permet de supprimer d’anciennes données d’appareils mobiles gérés par le connecteur Exchange Server. Ces données sont supprimées en fonction de l’intervalle configuré pour l’option **Ignorer les appareils mobiles inactifs depuis plus de (jours)** sous l’onglet **Découverte** des propriétés du connecteur Exchange Server. Pour plus d’informations, consultez [Gérer les appareils mobiles avec System Center Configuration Manager et Exchange](../../../mdm/deploy-use/manage-mobile-devices-with-exchange-activesync.md).  

-   Site d’administration centrale : non disponible   
-   **Site principal**  : activé    
-   Site secondaire : non disponible  

**Supprimer les données de découverte anciennes** : cette tâche permet de supprimer de la base de données d’anciennes données de découverte. Ces données peuvent inclure les enregistrements résultant des méthodes de découverte par pulsations, de découverte réseau et de découverte Active Directory Domain Services (Système, Utilisateur et Groupe). Lorsque cette tâche s’exécute sur un site, les données associées à celui-ci sont supprimées, et ces modifications sont répliquées vers d’autres sites. Pour plus d'informations sur la découverte, voir [Exécuter la découverte pour System Center Configuration Manager](../../../core/servers/deploy/configure/run-discovery.md).  

-   Site d’administration centrale : non disponible    
-   **Site principal**  : activé    
-   Site secondaire : non disponible  

**Supprimer les données d’utilisation de l’ancien point de distribution** : cette tâche permet de supprimer de la base de données d’anciennes données des points de distribution ayant été stockées plus longtemps que la durée spécifiée.  

-   **Site d’administration centrale** : activé    
-   **Site principal**  : activé    
-   Site secondaire : non disponible  

**Supprimer les anciennes données de l’historique de l’état d’intégrité Endpoint Protection** : cette tâche permet de supprimer de la base de données d’anciennes informations d’état Endpoint Protection. Pour plus d’informations sur les informations d’état Endpoint Protection, consultez [Comment surveiller Endpoint Protection dans System Center Configuration Manager](../../../protect/deploy-use/monitor-endpoint-protection.md).  

-   Site d’administration centrale : non disponible    
-   **Site principal**  : activé    
-   Site secondaire : non disponible  

**Supprimer les anciens périphériques inscrits** : à compter de la mise à jour pour la version 1602, cette tâche est désactivée par défaut. Vous pouvez utiliser cette tâche pour supprimer de la base de données de site d’anciennes données concernant les appareils mobiles qui n’ont signalé aucune information au site pendant une durée spécifiée.

Cette tâche s’applique aux appareils qui sont inscrits à l’aide de Microsoft Intune (hybride) ou de la gestion des appareils mobiles locale de Configuration Manager. Pour plus d’informations sur les systèmes d’exploitation des appareils inscrits à l’aide de Configuration Manager ou d’Intune, consultez la section [Appareils mobiles inscrits par Microsoft Intune](../../../core/plan-design/configs/supported-operating-systems-for-clients-and-devices.md#mobile-devices-enrolled-by-microsoft-intune) dans [Systèmes d’exploitation pris en charge pour les clients et les appareils pour System Center Configuration Manager](../../../core/plan-design/configs/supported-operating-systems-for-clients-and-devices.md).

-   Site d’administration centrale : non disponible    
-   **Site principal**non activé    
-   Site secondaire : non disponible  

**Supprimer les historiques d’inventaire anciens** : cette tâche permet de supprimer des données d’inventaire ayant été stockées dans la base de données pendant une durée plus longue que celle spécifiée. Pour plus d’informations sur l’historique d’inventaire, consultez [Comment utiliser l’Explorateur de ressources pour afficher l’inventaire matériel dans System Center Configuration Manager](../../../core/clients/manage/inventory/use-resource-explorer-to-view-hardware-inventory.md).  

-   Site d’administration centrale : non disponible    
-   **Site principal**  : activé    
-   Site secondaire : non disponible  

**Supprimer les anciennes données de journal** : cette tâche permet de supprimer d’anciennes données de journal utilisées pour le dépannage de la base de données. Ces données ne sont pas liées à des opérations de composants Configuration Manager.  

> [!IMPORTANT]  
> Par défaut, cette tâche s'exécute quotidiennement sur chaque site. Au niveau du site d'administration centrale et des sites principaux, la tâche supprime les données datant de plus de 30 jours. Quand vous utilisez SQL Server Express sur un site secondaire, veillez à ce que cette tâche soit exécutée chaque jour et à ce qu’elle supprime bien les données inactives depuis sept jours.  

-   **Site d’administration centrale** : activé    
-   **Site principal**  : activé    
-   **Site secondaire** : activé  

**Supprimer l’historique d’anciennes tâches de notification** : cette tâche permet de supprimer de la base de données du site des informations sur des tâches de notification client quand elles n’ont pas été mises à jour pendant une période spécifiée. Pour plus d’informations sur la notification client, consultez [Tâches de déploiement du client pour System Center Configuration Manager](../../../core/clients/manage/monitor-clients.md).  

-   Site d’administration centrale : non disponible    
-   **Site principal**  : activé    
-   Site secondaire : non disponible  

**Supprimer les anciennes données de synthèse de la réplication** : cette tâche permet de supprimer de la base de données du site d’anciennes données de synthèse de la réplication quand elles n’ont pas été mises à jour pendant une période spécifiée. Pour plus d'informations, voir la section [How to monitor database replication links and replication status](../../../core/servers/manage/monitor-hierarchy-and-replication-infrastructure.md#BKMK_MonitorRepLinksAndStatuss) dans la rubrique [Monitor hierarchy and replication infrastructure in System Center Configuration Manager](../../../core/servers/manage/monitor-hierarchy-and-replication-infrastructure.md).  

-   **Site d’administration centrale** : activé    
-   **Site principal**  : activé    
-   **Site secondaire** : activé  

**Supprimer les anciens enregistrements de code secret** : utilisée sur le site de niveau supérieur de votre hiérarchie, cette tâche permet de supprimer d’anciennes données de réinitialisation de code d’accès pour des appareils Android et Windows Phone. Les données de réinitialisation de code secret sont chiffrées, mais n’incluent pas le code confidentiel des appareils. Par défaut, cette tâche est activée et supprime les données datant de plus d’un jour.  

-   **Site d’administration centrale** : activé    
-   **Site principal**  : activé    
-   Site secondaire : non disponible  

**Supprimer les anciennes données de suivi de réplication** : cette tâche permet de supprimer de la base de données d’anciennes données sur la réplication de base de données entre sites Configuration Manager. Lorsque vous modifiez la configuration de cette tâche de maintenance, la configuration s'applique à chaque site concerné de la hiérarchie. Pour plus d'informations, voir la section [How to monitor database replication links and replication status](../../../core/servers/manage/monitor-hierarchy-and-replication-infrastructure.md#BKMK_MonitorRepLinksAndStatuss) dans la rubrique [Monitor hierarchy and replication infrastructure in System Center Configuration Manager](../../../core/servers/manage/monitor-hierarchy-and-replication-infrastructure.md).  

-   **Site d’administration centrale** : activé    
-   **Site principal**  : activé    
-   **Site secondaire** : activé  

**Supprimer les données de contrôle de logiciel anciennes** : cette tâche permet de supprimer de la base de données d’anciennes données du contrôle de logiciel ayant été stockées plus longtemps que la durée spécifiée. Pour plus d’informations, consultez [Contrôle de logiciel dans System Center Configuration Manager](../../../apps/deploy-use/monitor-app-usage-with-software-metering.md).  

-   Site d’administration centrale : non disponible    
-   **Site principal**  : activé    
-   Site secondaire : non disponible  

**Supprimer les données de résumé de contrôle de logiciel anciennes** : cette tâche permet de supprimer de la base de données d’anciennes données de résumé du contrôle de logiciel ayant été stockées plus longtemps que la durée spécifiée. Pour plus d’informations, consultez [Contrôle de logiciel dans System Center Configuration Manager](../../../apps/deploy-use/monitor-app-usage-with-software-metering.md).  

-   Site d’administration centrale : non disponible    
-   **Site principal**  : activé    
-   Site secondaire : non disponible  

**Supprimer les messages d’état anciens** : cette tâche permet de supprimer de la base de données d’anciennes données de message d’état en fonction de la configuration des règles de filtre d’état. Pour plus d’informations, consultez la section « Surveiller l’état du système de Configuration Manager » dans la rubrique [Utiliser des alertes et le système d’état pour System Center Configuration Manager](../../../core/servers/manage/use-alerts-and-the-status-system.md).  

-   **Site d’administration centrale** : activé    
-   **Site principal**  : activé    
-   Site secondaire : non disponible  

**Supprimer les anciennes données de menace** : cette tâche permet de supprimer de la base de données d’anciennes données de menace Endpoint Protection ayant été stockées plus longtemps que la période spécifiée. Pour plus d’informations sur Endpoint Protection, consultez [Endpoint Protection dans System Center Configuration Manager](../../../protect/deploy-use/endpoint-protection.md).  

-   Site d’administration centrale : non disponible    
-   **Site principal**  : activé    
-   Site secondaire : non disponible  

**Supprimer les anciens ordinateurs inconnus** : cette tâche permet de supprimer de la base de données de site des informations sur des ordinateurs inconnus quand elles n’ont pas été mises à jour pendant une période spécifiée. Pour plus d’informations, consultez [Préparer les déploiements d’ordinateurs inconnus dans System Center Configuration Manager](../../../osd/get-started/prepare-for-unknown-computer-deployments.md).  

-   Site d’administration centrale : non disponible    
-   **Site principal**  : activé    
-   Site secondaire : non disponible  

**Supprimer les anciennes données d’affinité entre périphérique et utilisateur** : cette tâche permet de supprimer de la base de données d’anciennes données d’affinité entre appareil et utilisateur. Pour plus d’informations, consultez [Lier des utilisateurs et des appareils avec l’affinité entre utilisateur et appareil dans System Center Configuration Manager](../../../apps/deploy-use/link-users-and-devices-with-user-device-affinity.md).  

-   Site d’administration centrale : non disponible    
-   **Site principal**  : activé    
-   Site secondaire : non disponible  

**Supprimer les enregistrements de package d’inscription en bloc MDM expirés** : utilisez cette tâche pour supprimer les anciens certificats d’inscription en bloc et les profils correspondants après l’expiration du certificat d’inscription. Pour plus d’informations, consultez [Créer des profils de certificat](/sccm/protect/deploy-use/create-certificate-profiles).
-   **Site d’administrations centrales** : activé
-   **Site principal**  : activé
-   Site secondaire : non disponible

**Supprimer les données de découverte des clients inactifs** : cette tâche permet de supprimer de la base de données des données de découverte de clients inactifs. Les clients sont marqués comme inactifs quand le client est marqué comme obsolète et par les configurations effectuées pour l’état du client.

Cette tâche ne fonctionne que sur les ressources qui des clients Configuration Manager. Elle est différente de la tâche **Supprimer les données de découverte anciennes** qui supprime tous les anciens enregistrements de données de découverte. Lorsque cette tâche s'exécute sur un site, elle supprime les données de la base de données de tous les sites d'une hiérarchie. Pour plus d’informations, voir [Comment configurer l’état du client dans System Center Configuration Manager](../../../core/clients/deploy/configure-client-status.md).  

> [!IMPORTANT]  
> Quand elle est activée, configurez cette tâche pour qu’elle s’exécute à un intervalle plus important que celui planifié pour la **Découverte par pulsations d’inventaire**. Les clients actifs peuvent ainsi envoyer un enregistrement de type Découverte par pulsations d’inventaire pour marquer leur enregistrement de client comme actif, de sorte que cette tâche ne les supprime pas.  

-   Site d’administration centrale : non disponible    
-   **Site principal**non activé    
-   Site secondaire : non disponible  

**Supprimer les alertes obsolètes** : cette tâche permet de supprimer de la base de données des alertes expirées ayant été stockées pendant une période plus longue que celle spécifiée. Pour plus d'informations, voir [Utiliser des alertes et le système d’état pour System Center Configuration Manager](../../../core/servers/manage/use-alerts-and-the-status-system.md).  

-   **Site d’administration centrale** : activé    
-   **Site principal**  : activé    
-   Site secondaire : non disponible  

**Supprimer les données obsolètes de découverte des clients** : cette tâche permet de supprimer de la base de données des enregistrements de client obsolètes. Un enregistrement marqué comme obsolète a généralement été remplacé par un enregistrement plus récent pour le même client. L’enregistrement plus récent devient l’enregistrement actuel du client. Pour plus d'informations sur la découverte, voir [Exécuter la découverte pour System Center Configuration Manager](../../../core/servers/deploy/configure/run-discovery.md).  

> [!IMPORTANT]  
> Quand elle est activée, configurez cette tâche pour qu’elle s’exécute à un intervalle plus important que celui planifié pour la Découverte par pulsations d’inventaire. Cela permet au client d'envoyer un enregistrement de découverte par pulsations d'inventaire qui définit l'état obsolète correctement.  

-   Site d’administration centrale : non disponible    
-   **Site principal**non activé    
-   Site secondaire : non disponible  

**Supprimer les sites et sous-réseaux de découverte de forêts obsolètes** : cette tâche permet de supprimer des données de sites, de sous-réseaux et de domaines Active Directory n’ayant pas été découverts par la méthode de découverte de forêt Active Directory au cours des 30 derniers jours. Cela supprime les données de découverte, mais n’affecte pas les limites créées à partir de ces données de découverte. Pour plus d’informations, voir [Exécuter la découverte pour System Center Configuration Manager](../../../core/servers/deploy/configure/run-discovery.md).  

-   **Site d’administration centrale** : activé    
-   **Site principal**  : activé    
-   Site secondaire : non disponible  

**Supprimer les enregistrements d’état du déploiement des clients orphelins** : cette tâche permet de purger régulièrement la table qui contient les informations sur l’état du déploiement d’un client. Cette tâche nettoie les enregistrements associés aux appareils obsolètes ou désactivés.  
-   **Site d’administration centrale** : activé    
-   **Site principal**  : activé    
-   Site secondaire : non disponible

**Supprimer les révisions d’application inutilisées** : cette tâche permet de supprimer les révisions d’application qui ne sont plus référencées. Pour plus d’informations, consultez [Comment modifier et remplacer des applications dans System Center Configuration Manager](../../../apps/deploy-use/revise-and-supersede-applications.md).  

-   Site d’administration centrale : non disponible    
-   **Site principal**  : activé    
-   Site secondaire : non disponible  

**Évaluer les membres du regroupement** : vous configurez l’évaluation de l’appartenance au regroupement comme composant de site. Pour plus d'informations sur les composants de site, voir [Site components for System Center Configuration Manager](../../../core/servers/deploy/configure/site-components.md).  

-   Site d’administration centrale : non disponible    
-   **Site principal**  : activé    
-   Site secondaire : non disponible  

**Contrôler les clés** : cette tâche permet de surveiller l’intégrité des clés primaires de la base de données Configuration Manager. Une clé primaire est une colonne (ou une combinaison de colonnes) qui identifie de manière unique une ligne et la distingue des autres lignes dans une table de base données Microsoft SQL Server.  

-   **Site d’administration centrale** : activé    
-   **Site principal**  : activé    
-   Site secondaire : non disponible  

**Reconstruire les index** : cette tâche permet de reconstruire les index des bases de données Configuration Manager. Un index désigne une structure de base de données créée dans une table de base de données pour accélérer le processus d'extraction des données. Par exemple, il est souvent plus rapide d’effectuer une recherche dans une colonne indexée que dans une colonne qui ne l’est pas.

Pour des performances optimales, les index de base de données Configuration Manager sont mis à jour fréquemment pour être synchronisés avec les données changeant constamment stockées dans la base de données. Cette tâche permet de créer et de placer des index dans des colonnes de base de données uniques à moins de 50 % et de reconstruire tous les index existants conformes aux critères d'unicité des données.  

-   **Site d’administration centrale** : non activé    
-   **Site principal**non activé    
-   **Site secondaire** : non activé  

**Résumer les données du logiciel installé** : cette tâche permet de synthétiser les données de logiciels installés de plusieurs enregistrements en un seul enregistrement général. La synthèse des données permet de compresser la quantité de données stockées dans la base de données Configuration Manager. Pour plus d’informations, consultez [Présentation de l’inventaire logiciel dans System Center Configuration Manager](../../clients/manage/inventory\introduction-to-software-inventory.md).  

-   Site d’administration centrale : non disponible    
-   **Site principal**  : activé    
-   Site secondaire : non disponible  

**Résumer les données d’utilisation de fichier de contrôle de logiciel** : cette tâche permet de synthétiser les données de plusieurs enregistrements pour l’utilisation de fichier de contrôle logiciel en un seul enregistrement général. La synthèse des données permet de compresser la quantité de données stockées dans la base de données Configuration Manager.

Vous pouvez utiliser cette tâche avec la tâche **Résumer les données d’utilisation mensuelle de contrôle de logiciel** pour synthétiser les données de contrôle de logiciel et pour préserver de l’espace disque dans la base de données Configuration Manager. Pour plus d’informations, consultez [Contrôle de logiciel dans System Center Configuration Manager](../../../apps/deploy-use/monitor-app-usage-with-software-metering.md).  

-   Site d’administration centrale : non disponible    
-   **Site principal**  : activé    
-   Site secondaire : non disponible  

**Résumer les données d’utilisation mensuelle de contrôle de logiciel** : cette tâche permet de synthétiser les données de plusieurs enregistrements pour l’utilisation mensuelle du contrôle de logiciel en un seul enregistrement général. La synthèse des données permet de compresser la quantité de données stockées dans la base de données Configuration Manager.

Vous pouvez utiliser cette tâche avec la tâche **Résumer les données d’utilisation de fichier de contrôle de logiciel** pour synthétiser les données de contrôle de logiciel et pour préserver de l’espace dans la base de données Configuration Manager. Pour plus d’informations, consultez [Contrôle de logiciel dans System Center Configuration Manager](../../../apps/deploy-use/monitor-app-usage-with-software-metering.md).  

-   Site d’administration centrale : non disponible    
-   **Site principal**  : activé    
-   Site secondaire : non disponible  

**Mettre à jour le ciblage disponible de l’application** : cette tâche permet de faire en sorte que Configuration Manager recalcule le mappage des déploiements de stratégies et d’applications aux ressources dans des regroupements. Quand vous déployez une stratégie ou des applications dans un regroupement, Configuration Manager crée un mappage initial entre les objets que vous déployez et les membres du regroupement.

Ces mappages sont stockés dans une table à des fins de référence rapide. Quand l’appartenance à un regroupement change, ces mappages stockés sont mis à jour afin de refléter ces modifications. Toutefois, il est possible que ces mappages soient désynchronisés. Par exemple, si le site ne parvient pas à traiter correctement un fichier de notification, il se peut que cette modification ne soit pas reflétée dans une modification des mappages. Cette tâche actualise ce mappage en fonction de l’appartenance au regroupement actuel.  

-   Site d’administration centrale : non disponible    
-   **Site principal**  : activé    
-   Site secondaire : non disponible  

**Mettre à jour les tables du catalogue des applications** : cette tâche permet de synchroniser le cache de base de données du site web du catalogue des applications avec les dernières informations sur les applications. Lorsque vous modifiez la configuration de cette tâche de maintenance, la configuration s'applique à tous les sites principaux de la hiérarchie.  

-   Site d’administration centrale : non disponible    
-   **Site principal**  : activé    
-   Site secondaire : non disponible  
