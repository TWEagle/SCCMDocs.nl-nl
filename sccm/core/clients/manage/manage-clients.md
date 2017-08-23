---
title: "Gérer les clients | Microsoft Docs"
description: "Découvrez comment gérer les clients dans System Center Configuration Manager."
ms.custom: na
ms.date: 04/23/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: configmgr-client
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 3986a992-c175-4b6f-922e-fc561e3d7cb7
caps.latest.revision: "17"
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.openlocfilehash: 3a86924b2e5db3ac16eeda78b95ae6747ffd656f
ms.sourcegitcommit: 51fc48fb023f1e8d995c6c4eacfda7dbec4d0b2f
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/07/2017
---
# <a name="how-to-manage-clients-in-system-center-configuration-manager"></a>Guide pratique pour gérer les clients dans System Center Configuration Manager

*S’applique à : System Center Configuration Manager (Current Branch)*

Une fois qu’un client System Center Configuration Manager a été installé et attribué à un site Configuration Manager, l’appareil est affiché dans l’espace de travail **Ressources et Conformité** du nœud **Appareils**, ainsi que dans un ou plusieurs regroupements du nœud **Regroupements d’appareils**. Quand vous sélectionnez l’appareil ou un regroupement, vous pouvez effectuer des opérations de gestion. Toutefois, il existe d’autres manières de gérer le client, pouvant impliquer d’autres espaces de travail dans la console ou des tâches qui n’utilisent pas la console Configuration Manager.  

> [!NOTE]  
>  Il arrive qu’un client Configuration Manager installé ne s’affiche pas dans la console Configuration Manager. Ceci peut se produire si le client n’a pas encore été affecté à un site, si la console doit être actualisée ou si une appartenance au regroupement doit être mise à jour.  
>   
>  De plus, un appareil peut s’afficher dans la console quand le client Configuration Manager n’est pas installé. Ceci peut se produire si l’appareil a été découvert, mais que le client Configuration Manager n’est pas installé ni affecté. Les appareils mobiles gérés à l’aide du connecteur Exchange Server et les appareils qui sont inscrits par Microsoft Intune n’installent pas le client Configuration Manager.  
>   
>  Examinez la colonne **Client** dans la console Configuration Manager pour savoir si le client Configuration Manager est installé et si vous pouvez donc le gérer à partir de la console Configuration Manager.  

##  <a name="BKMK_ManagingClients_DevicesNode"></a> Gérer les clients à partir du nœud Appareils  

Notez que, selon le type d’appareil, certaines de ces options peuvent ne pas être disponibles.  

1.  Dans la console Configuration Manager, choisissez **Ressources et Conformité** >  **Appareils**.  

3.  Sélectionnez un ou plusieurs appareils, puis sélectionnez une des tâches de gestion de client disponible dans le ruban ou en cliquant avec le bouton droit sur l’appareil :  

    -   **Gérer les informations relatives à l'affinité entre périphérique et utilisateur**  

         Configurez les associations entre les utilisateurs et les appareils, ce qui vous permet de déployer efficacement des logiciels sur les utilisateurs.  

         Consultez [Lier des utilisateurs et des appareils avec l’affinité entre utilisateur et appareil dans System Center Configuration Manager](../../../apps/deploy-use/link-users-and-devices-with-user-device-affinity.md)  

    -   **Ajouter l’appareil à un regroupement nouveau ou existant**  

         Ajoutez l’appareil à un regroupement avec une règle directe.  
         
    -   **Installer et réinstaller le client à l'aide de l'Assistant Installation poussée du client**  

         Installez et réinstallez le client Configuration Manager pour le réparer ou pour le reconfigurer sur les ordinateurs qui exécutent Windows. Inclut des options de configuration de site et les propriétés client.msi que vous définissez pour l’installation Push du client.  

        > [!TIP]  
        >  Vous avez le choix entre plusieurs méthodes d’installation (et de réinstallation) du client Configuration Manager. L’Assistant Installation Push du client constitue une méthode pratique d’installation du client car elle peut être exécutée depuis la console, mais cette méthode a de nombreuses dépendances et n’est pas adaptée à tous les environnements. Pour plus d’informations sur les dépendances, consultez [Configuration requise pour le déploiement de clients sur des ordinateurs Windows dans System Center Configuration Manager](../../../core/clients/deploy/prerequisites-for-deploying-clients-to-windows-computers.md). Pour plus d’informations sur les autres méthodes d’installation de clients, consultez [Méthodes d’installation de clients dans System Center Configuration Manager](../../../core/clients/deploy/plan/client-installation-methods.md).  

         Consultez [Comment installer des clients Configuration Manager à l'aide de l'installation poussée du client](../../../core/clients/deploy/deploy-clients-to-windows-computers.md#BKMK_ClientPush).  

    -   **Réaffecter le site**  

         Vous pouvez réaffecter un ou plusieurs clients, notamment des appareils mobiles gérés, à un autre site principal de la hiérarchie. Les clients peuvent être réattribués individuellement ou tous sélectionnés et réattribués en bloc à un nouveau site.  

    -   **Administrer le client à distance**  

         Vous pouvez exécuter l'Explorateur de ressources pour afficher les informations d'inventaire matériel et logiciel d'un client Windows et les administrer à distance à l'aide du contrôle à distance, de l'assistance à distance ou du Bureau à distance.  

         Consultez [Comment utiliser l’Explorateur de ressources pour afficher l’inventaire matériel dans System Center Configuration Manager](../../../core/clients/manage/inventory/use-resource-explorer-to-view-hardware-inventory.md) et [Comment utiliser l’Explorateur de ressources pour afficher l’inventaire logiciel dans System Center Configuration Manager](../../../core/clients/manage/inventory/use-resource-explorer-to-view-software-inventory.md).  

         Consultez [Comment administrer à distance un ordinateur client Windows à l’aide de System Center Configuration Manager](../../../core/clients/manage/remote-control/remotely-administer-a-windows-client-computer.md).  

    -   **Approuver un client**  

         Quand le client communique avec les systèmes de site en utilisant HTTP et un certificat autosigné, vous devez approuver ces clients pour les identifier comme ordinateurs approuvés. Par défaut, la configuration du site approuve automatiquement les clients de la même forêt Active Directory et de forêts approuvées pour vous éviter d'approuver manuellement chaque client. Toutefois, vous devez approuver manuellement les ordinateurs du groupe de travail auxquels vous faites confiance et tous les autres ordinateurs auxquels vous faites confiance, mais qui ne sont pas approuvés.  

        > [!WARNING]  
        >  Certaines fonctions de gestion peuvent fonctionner pour les clients non approuvés, mais ce scénario n’est pas pris en charge pour Configuration Manager.  

         Vous ne devez pas approuver les clients qui communiquent toujours avec les systèmes de site en utilisant le protocole HTTPS, ou les clients qui utilisent un certificat PKI quand ils communiquent avec les systèmes de site en utilisant le protocole HTTP. Ces clients établissent une relation de confiance en utilisant les certificats PKI.  

    -   **Bloquer ou débloquer un client**  

         Bloquez un client auquel vous ne faites plus confiance pour l’empêcher de recevoir la stratégie client et empêcher les systèmes de site Configuration Manager de communiquer avec lui.  

        > [!WARNING]  
        >  Le fait de bloquer un client empêche les communications entre le client et les systèmes de site Configuration Manager uniquement. Cela n’empêche pas les communications avec d’autres appareils. De plus, lorsque le client communique avec des systèmes de site à l'aide du protocole HTTP au lieu de HTTPS, certaines contraintes de sécurité se présentent.  

         Vous pouvez débloquer un client qui a été bloqué. Toutefois, après avoir débloqué un ordinateur basé sur AMT Intel configuré pour AMT lorsqu'il était bloqué, vous devez exécuter des étapes supplémentaires pour pouvoir le gérer hors bande de nouveau.  

         Consultez [Déterminer si des clients doivent être bloqués dans System Center Configuration Manager](../../../core/clients/deploy/plan/determine-whether-to-block-clients.md).  

    -   **Effacer un déploiement PXE requis**  

         Redéployez les déploiements PXE nécessaires pour l’ordinateur.  

         Consultez [Utiliser PXE pour déployer Windows sur le réseau avec System Center Configuration Manager](../../../osd/deploy-use/use-pxe-to-deploy-windows-over-the-network.md).  

    -   **Gérer les propriétés du client**  

         Vous pouvez afficher les données de découverte et les déploiements ciblés pour le client. Vous pouvez également configurer des variables qui sont utilisées par les séquences de tâches pour déployer un système d’exploitation sur l’appareil.  

    -   **Supprimer le client**  

        > [!WARNING]  
        >  Ne supprimez pas un client si vous souhaitez désinstaller le client Configuration Manager ou le supprimer d’un regroupement.  

         L’action **Supprimer** permet de supprimer manuellement l’enregistrement client de la base de données Configuration Manager. En général, cette action est utilisée dans les scénarios de résolution des problèmes. Si vous supprimez l’enregistrement client et que le client est toujours installé et communique avec Configuration Manager, la découverte par pulsations d’inventaire recrée l’enregistrement client, qui réapparaît dans la console Configuration Manager, mais sans l’historique du client ni les associations précédentes, qui sont perdus.  

        > [!NOTE]  
        >  Si vous supprimez un client d’appareil mobile inscrit par Configuration Manager, cette action révoque également le certificat PKI émis pour l’appareil mobile. Ce certificat est alors rejeté par le point de gestion, même si IIS ne vérifie pas la liste de révocation de certificats. Les certificats sur les clients hérités d'appareils mobiles ne sont pas révoqués lorsque vous supprimez ces clients.  

         Pour désinstaller le client, voir [Désinstaller le client Configuration Manager](#BKMK_UninstalClient).  

         Pour affecter le client à un nouveau site principal, consultez [Comment affecter des clients à un site dans System Center Configuration Manager](../../../core/clients/deploy/assign-clients-to-a-site.md).  

         Pour supprimer le client d'un regroupement, reconfigurez les propriétés du regroupement. Consultez [Comment gérer des regroupements dans System Center Configuration Manager](../../../core/clients/manage/collections/manage-collections.md).  

    -   **Réinitialiser un appareil mobile**  

         Vous pouvez réinitialiser les appareils mobiles qui prennent en charge la commande de réinitialisation.  

         Cette action supprime définitivement toutes les données sur l’appareil mobile, notamment les paramètres et données personnels. En général, cette action rétablit les paramètres par défaut de l'appareil mobile. Réinitialisez un appareil mobile quand vous ne lui faites plus confiance, par exemple s’il a été perdu ou volé.  

        > [!TIP]  
        >  Consultez la documentation du fabricant pour obtenir plus d’informations sur la façon dont l’appareil mobile traite les commandes de réinitialisation à distance.  

         L’appareil mobile reçoit souvent la commande de réinitialisation avec un certain délai :  

        -   Si l’appareil mobile est inscrit par Configuration Manager ou Microsoft Intune, le client reçoit la commande quand il télécharge sa stratégie client.  

        -   Si l’appareil mobile est géré par le connecteur Exchange Server, il reçoit la commande quand il se synchronise avec Exchange.  

         Vous pouvez utiliser la colonne **État de réinitialisation** pour surveiller quand l’appareil reçoit la commande de réinitialisation. Vous pouvez annuler cette commande tant que l’appareil n’a pas envoyé d’accusé de réception de la réinitialisation à Configuration Manager.  

    -   **Mettre hors service un appareil mobile**  

         L’option **Mettre hors service** est prise en charge uniquement par les appareils mobiles inscrits par Intune ou par la gestion des appareils mobiles (MDM) locale.  

         Pour plus d’informations, consultez [Protéger vos données à l’aide de la réinitialisation à distance, du verrouillage à distance ou de la réinitialisation du code d’accès avec System Center Configuration Manager](../../../mdm/deploy-use/wipe-lock-reset-devices.md).  

    -   **Modifier la propriété d’un appareil**  

         Vous pouvez modifier la propriété d’un appareil à **Entreprise** ou **Personnel** si l’appareil n’est pas joint à un domaine et qu’il n’a pas le client Configuration Manager installé.  

         Vous pouvez utiliser cette valeur dans les conditions des applications pour contrôler les déploiements, et pour contrôler la quantité de données d’inventaire collectées auprès des appareils des utilisateurs.  

        Il peut être nécessaire d’ajouter la colonne **Propriétaire de l’appareil**à la vue en à la vue en cliquant avec le bouton droit sur n’importe quel titre de colonne et en choisissant le choisissant.

         Pour plus d’informations, consultez [Gestion des appareils mobiles (MDM) hybride avec System Center Configuration Manager et Microsoft Intune](../../../mdm/understand/hybrid-mobile-device-management.md).  

##  <a name="BKMK_ManagingClients_DeviceCollectionsNode"></a> Gérer les clients à partir du nœud Regroupements d’appareils  
  Un grand nombre des tâches que vous pouvez réaliser sur un seul appareil ou sur plusieurs appareils dans le nœud **Appareils** peuvent être réalisées sur des regroupements. Ceci s’applique automatiquement l’opération à tous les appareils éligibles du regroupement. Notez que ceci génère un grand nombre de paquets réseau et augmente l’utilisation de l’UC sur le serveur de site.  

  Avant d'effectuer des tâches de gestion du client au niveau du regroupement, vous devez prendre en compte le nombre de périphériques dans le regroupement, s'ils utilisent des connexions réseau à faible bande passante, et le temps que prendra la tâche pour tous les périphériques. Une fois démarrée, vous ne pouvez pas arrêter la tâche à partir de la console.  

#### <a name="to-manage-clients-from-the-device-collections-node"></a>Pour gérer les clients à partir du nœud Regroupements de périphériques  

1.  Dans la console Configuration Manager, choisissez **Ressources et Conformité** > **Regroupements d’appareils**.  

3.  Sélectionnez un regroupement, puis sélectionnez une des tâches de gestion du client disponibles dans le ruban ou en cliquant avec le bouton droit sur le regroupement. Ces tâches de gestion de client peuvent être réalisées *uniquement* au niveau du regroupement.  

    -   **Analysez les ordinateurs pour y détecter des programmes malveillants et téléchargez des fichiers de définition de logiciel anti-programme malveillant.**  

         Consultez [Endpoint Protection dans System Center Configuration Manager](../../../protect/deploy-use/endpoint-protection.md).  

    -   **Déployez des logiciels, des lignes de base de configuration et des séquences de tâches.**  

         Consultez :  

        -   [Déployer des mises à jour logicielles dans System Center Configuration Manager](../../../sum/deploy-use/deploy-software-updates.md)  

        -   [Planifier et configurer les paramètres de conformité dans System Center Configuration Manager](../../../compliance/plan-design/plan-for-and-configure-compliance-settings.md)  

    -   **Configurez les paramètres de gestion de l'alimentation.**  

         Consultez [Comment créer et appliquer des modes de gestion de l’alimentation dans System Center Configuration Manager](../../../core/clients/manage/power/create-and-apply-power-plans.md). Les modes de gestion de l'alimentation ne peuvent être utilisés qu'avec les ordinateurs qui exécutent Windows.  

    -   **Invitez les ordinateurs à télécharger la stratégie dès que possible.**  

         Utilisez une notification de client pour inviter les clients Windows sélectionnés à télécharger la stratégie de l’ordinateur dès que possible en dehors de l’intervalle d’interrogation de stratégie du client.  

         Les tâches de notification de client s'affichent dans le nœud **Opérations du client** de l'espace de travail **Surveillance** .  

##  <a name="BKMK_ClientCache"></a> Configurer le cache du client pour les clients Configuration Manager  
Le cache du client stocke les fichiers temporaires utilisés lors de l’installation d’applications et de programmes par les clients. Les mises à jour logicielles utilisent également le cache du client, mais elles ne sont pas limitées par la taille configurée pour le cache et tenteront toujours de télécharger vers le cache. Vous pouvez configurer les paramètres du cache du client, comme la taille et l’emplacement, quand vous installez manuellement le client Configuration Manager, quand vous utilisez une installation Push du client ou après que le client a été installé.

Depuis Configuration Manager version 1606, vous pouvez spécifier la taille du dossier du cache en utilisant les paramètres client dans la console Configuration Manager.   

 L’emplacement par défaut pour le cache du client Configuration Manager est %*windir*%\ccmcache, et l’espace disque par défaut est de 5 120 Mo.  

> [!IMPORTANT]  
>  Ne chiffrez pas le dossier utilisé pour le cache du client. Configuration Manager ne peut pas télécharger du contenu vers un dossier chiffré.  

### <a name="about-client-cache"></a>À propos du cache du client  

Le client Configuration Manager télécharge le contenu pour les logiciels nécessaires dès qu’il reçoit le déploiement, mais il ne l’exécute pas avant l’heure planifiée du déploiement. À l’heure planifiée, le client Configuration Manager vérifie si le contenu est disponible dans le cache. Si le contenu est dans le cache et qu’il s’agit de la version correcte, le client utilise le contenu mis en cache. Quand la version demandée du contenu a été modifiée ou si le contenu a été supprimé pour faire de la place pour un autre package, le contenu est à nouveau téléchargé dans le cache.  

Si le client tente de télécharger du contenu pour un programme ou une application dont la taille est supérieure à celle du cache, le déploiement échoue en raison de la taille insuffisante du cache et Configuration Manager génère un message d’état (ID 10050). Si la taille du cache est augmentée par la suite, le résultat est :  

-   Pour un programme requis : le client ne retente pas automatiquement de télécharger le contenu. Vous devez redéployer le package et le programme vers le client.  
-   Pour une application demandée : le client tente automatiquement de télécharger le contenu quand il télécharge sa stratégie client.  

Si le client tente de télécharger un package dont la taille est inférieure à celle du cache, mais que le cache est plein, tous les déploiements demandés continuent leurs tentatives, jusqu’à ce que l’espace du cache soit disponible, et ce jusqu’à expiration du délai de téléchargement ou jusqu’à ce que la limite du nombre de tentatives d’accès à l’espace du cache soit atteinte. Si la taille du cache augmente ultérieurement, Configuration Manager effectue une nouvelle tentative de téléchargement du package à l’intervalle suivant. Le client tente de télécharger le contenu toutes les 4 heures jusqu'à ce qu'il atteigne 18 tentatives.  

Le contenu mis en cache n'est pas automatiquement supprimé, mais reste dans le cache pendant au moins un jour après son utilisation par le client. Si vous configurez les propriétés du package avec l'option de conserver le contenu dans le cache du client, le client ne supprime pas automatiquement le contenu du package du cache. Si l'espace du cache du client est utilisé par des packages ayant été téléchargés au cours des dernières 24 heures et que le client doit télécharger de nouveaux packages, vous pouvez augmenter la taille du cache ou choisir l'option de suppression pour supprimer le contenu conservé dans le cache.  

 Utilisez les procédures suivantes pour configurer le cache du client lors de l'installation manuelle du client, ou après avoir installé le client.  

### <a name="to-configure-the-client-cache-when-you-install-clients-by-using-manual-client-installation"></a>Pour configurer le cache du client lorsque vous installez les clients à l'aide de l'installation client manuelle  

Exécutez la commande CCMSetup.exe à partir de l'emplacement source d'installation et spécifiez les propriétés suivantes dont vous avez besoin, séparées par des espaces :  

   -   DISABLECACHEOPT  

    -   SMSCACHEDIR  

    -   SMSCACHEFLAGS  

    -   SMSCACHESIZE  

        > [!NOTE]
        > Pour la version 1606, utilisez les paramètres de taille du cache disponibles dans **Paramètres client** dans la console Configuration Manager au lieu de la propriété SMSCACHESIZE. Pour plus d’informations, consultez [Paramètres du cache client](../../../core/clients/deploy/about-client-settings.md#client-cache-settings) (Paramètres du cache du client).

Pour plus d’informations sur l’utilisation de ces propriétés de ligne de commande pour CCMSetup.exe, consultez [À propos des propriétés d’installation du client dans System Center Configuration Manager](../../../core/clients/deploy/about-client-installation-properties.md).  

### <a name="to-configure-the-client-cache-folder-when-you-install-clients-by-using-client-push-installation"></a>Pour configurer le dossier du cache du client lorsque vous installez les clients à l'aide de l'installation poussée du client  

1.  Dans la console Configuration Manager, choisissez **Administration** > **Configuration du site** > **Sites**.  

3.  Sélectionnez le site approprié et, sous l’onglet **Accueil**, dans le groupe **Paramètres**, choisissez **Paramètres d’installation du client** > **Onglet Propriétés de l’installation**.  

5.  Spécifiez les propriétés suivantes, séparées par des espaces :  

    -   DISABLECACHEOPT  

    -   SMSCACHEDIR  

    -   SMSCACHEFLAGS  

    -   SMSCACHESIZE  

        > [!NOTE]
        > Pour la version 1606, utilisez les paramètres de taille du cache disponibles dans **Paramètres client** dans la console Configuration Manager au lieu de la propriété SMSCACHESIZE. Pour plus d’informations, consultez [Paramètres du cache client](../../../core/clients/deploy/about-client-settings.md#client-cache-settings) (Paramètres du cache du client).

       Pour plus d’informations sur l’utilisation de ces propriétés de ligne de commande pour CCMSetup.exe, consultez [À propos des propriétés d’installation du client dans System Center Configuration Manager](../../../core/clients/deploy/about-client-installation-properties.md).  

### <a name="to-configure-the-client-cache-folder-on-the-client-computer"></a>Pour configurer le dossier du cache du client sur l’ordinateur client  

1.  Sur l’ordinateur client, accédez à **Configuration Manager** dans le Panneau de configuration et double-cliquez pour ouvrir les propriétés.  

2.  Sous l’onglet **Cache**, définissez les propriétés de l’espace et de l’emplacement. L'emplacement par défaut est *%windir%*\ccmcache.  

5.  Pour supprimer les fichiers dans le dossier du cache, choisissez **Supprimer les fichiers**.  

    > [!NOTE]
    > 
    > Le dossier du cache est un dossier Windows normal : vous pouvez donc automatiser la suppression du contenu du dossier à l’aide d’un script ou d’un utilitaire, ou avec l’applet de commande PowerShell `Remove-Item`. 


### <a name="to-configure-client-cache-size-in-client-settings"></a>Pour configurer la taille du cache du client dans les paramètres client

À compter de la version 1606, vous pouvez ajuster la taille du dossier du cache du client sans avoir à réinstaller le client. Pour ce faire, vous configurez la taille du cache du client dans la console Configuration Manager à l’aide des paramètres client.  

1. Dans la console Configuration Manager, accédez à **Administration** > **Paramètres client**.

2. Double-cliquez sur **Paramètres client par défaut**.
  Vous pouvez également créer des paramètres client personnalisés pour appliquer la taille du cache de manière plus sélective. Pour plus d’informations sur les paramètres client personnalisés et par défaut, consultez [Guide pratique pour configurer les paramètres client dans System Center Configuration Manager](../../../core/clients/deploy/configure-client-settings.md).

 3. Choisissez **Paramètres de cache du client** et choisissez **Oui** pour **Configurer la taille du cache du client**, puis utilisez le paramètre **Mo** ou **Pourcentage du disque**. La taille du cache est ajustée en fonction de la plus petite valeur.

     Le client Configuration Manager configurera la taille du cache avec ces paramètres lors du téléchargement de la stratégie client suivante.

##  <a name="BKMK_UninstalClient"></a> Désinstaller le client Configuration Manager  
 Vous pouvez désinstaller le client Configuration Manager d’un ordinateur Windows en exécutant **CCMSetup.exe** avec la propriété **/Uninstall**. Exécutez CCMSetup.exe sur un ordinateur individuel à partir de l'invite de commande ou déployez un package et un programme pour désinstaller le client pour un regroupement d'ordinateurs.  

> [!WARNING]  
>  Il n’est pas possible de désinstaller le client Configuration Manager depuis un appareil mobile. Si vous devez supprimer le client Configuration Manager d’un appareil mobile, vous devez le réinitialiser, ce qui supprime toutes les données présentes sur l’appareil mobile.  

#### <a name="to-uninstall-the-configuration-manager-client-from-the-command-prompt"></a>Pour désinstaller le client Configuration Manager à partir de l'invite de commande  

1.  Ouvrez une invite de commandes Windows et accédez à l'emplacement du fichier CCMSetup.exe.  

2.  Entrez **Ccmsetup.exe /uninstall**, puis appuyez sur **Entrée**.  

> [!NOTE]  
>  Le processus de désinstallation n’affiche pas de résultats à l’écran. Pour vérifier que la désinstallation du client s’est déroulée correctement, examinez le fichier journal **CCMSetup.log** dans le dossier *%windir%\ ccmsetup* de l’ordinateur client.  

##  <a name="BKMK_ConflictingRecords"></a> Gérer les enregistrements en conflit pour les clients Configuration Manager  
 Configuration Manager utilise l’ID du matériel pour tenter d’identifier les éventuels clients dupliqués et vous signale les conflits d’enregistrement qu’il trouve. Par exemple, si vous réinstallez un ordinateur, il est possible que l’ID du matériel soit le même, mais que le GUID utilisé par Configuration Manager soit différent.  

 Si Configuration Manager peut résoudre un conflit en utilisant l’authentification Windows du compte d’ordinateur ou un certificat PKI émis par une source approuvée, le conflit est résolu automatiquement. Si Configuration Manager ne peut pas résoudre le conflit, il utilise un paramètre de hiérarchie qui fusionne automatiquement les enregistrements avec le même ID de matériel qu’il a détectés (il s’agit du paramètre par défaut) ou qui vous laisse le choix de fusionner ou de bloquer les enregistrements du client, ou d’en créer d’autres. Si vous décidez de gérer manuellement les enregistrements en doublon, vous devez résoudre vous-même les enregistrements en conflit dans la console Configuration Manager.  


#### <a name="to-change-the-hierarchy-setting-for-managing-conflicting-records"></a>Pour modifier le paramètre de hiérarchie pour gérer les conflits d'enregistrement  

1.  Dans la console Configuration Manager, choisissez **Administration** > **Configuration du site** > **Sites** > **Paramètres de hiérarchie**.
2.  Sous l’onglet **Approbation client et enregistrements en conflit**, choisissez **Résoudre automatiquement les enregistrements en conflit** ou **Résoudre manuellement les enregistrements en conflit**.  

#### <a name="to-manually-resolve-conflicting-records"></a>Pour résoudre manuellement les enregistrements en conflit  

1.  Dans la console Configuration Manager, choisissez **Surveillance** > **État du système** > **Enregistrements en conflit**.  

3.  Sélectionnez un ou plusieurs enregistrements en conflit, puis choisissez **Enregistrement en conflit**.  

4.  Sélectionnez l’un des paramètres suivants :  

    -   **Fusionner** : permet de combiner le nouvel enregistrement détecté avec l’enregistrement client existant.  

    -   **Nouveau** : permet de créer un nouvel enregistrement pour l'enregistrement de client en conflit.  

    -   **Bloquer** : permet de créer un nouvel enregistrement pour l'enregistrement de client en conflit, mais le marquer comme bloqué.  

## <a name="manage-duplicate-hardware-identifiers"></a>Gérer les identificateurs de matériel dupliqués
Depuis Configuration Manager version 1610, vous pouvez fournir la liste des ID de matériel ignorés par Configuration Manager dans le cadre du démarrage PXE et de l’inscription des clients. Deux problèmes courants bénéficient de cette fonctionnalité.

1. De nombreux nouveaux appareils, comme la Surface Pro 3, ne comprennent pas de port Ethernet intégré. Une carte USB-Ethernet est généralement utilisée pour établir une connexion filaire afin de déployer le système d’exploitation. Toutefois, il s’agit souvent de cartes partagées pour des questions de coût et de facilité d’utilisation. Étant donné que l’adresse MAC de cette carte est utilisée pour identifier l’appareil, la réutilisation de cette carte nécessite l’intervention supplémentaire d’un administrateur entre chaque déploiement. Depuis la version 1610, vous pouvez exclure l’adresse MAC de cette carte pour permettre sa réutilisation dans ce scénario.
2. Tandis que l’ID SMBIOS est supposé être un identificateur de matériel unique, certains appareils spécialisés sont créés avec des ID dupliqués. La liste des ID de matériel peut également être utilisée pour résoudre ce problème, même s’il s’agit d’un scénario plus rare que l’utilisation d’une carte USB-Ethernet ci-dessus.

#### <a name="to-add-hardware-identifiers-for-configuration-manager-to-ignore"></a>Pour ajouter des identificateurs de matériel que Configuration Manager doit ignorer  
1. Dans la console Configuration Manager, accédez à **Administration** > **Vue d’ensemble** > **Configuration du site** > **Sites**.
2. Sous l’onglet **Accueil**, dans le groupe **Sites**, choisissez **Paramètres de hiérarchie**.
3. Sous l’onglet **Approbation client et enregistrements en conflit**, choisissez **Ajouter** dans la section **Identificateurs de matériel en doublon** pour ajouter de nouveaux identificateurs de matériel.

##  <a name="BKMK_PolicyRetrieval"></a> Lancer une récupération de stratégie pour un client Configuration Manager  
 Sur Windows, un client Configuration Manager télécharge sa stratégie client selon un calendrier que vous configurez comme paramètre du client. Il se peut cependant que dans certaines situations vous souhaitiez lancer une récupération de stratégie ad hoc à partir du client, par exemple dans un scénario de résolution de problème ou de test.  

Vous pouvez lancer une récupération de stratégie en utilisant :


- [Notification du client](#initiate-client-policy-retrieval-using-client-notification) 
- [L’onglet **Actions** sur le client](#manually-initiate-client-policy-retrieval-on-the-actions-tab-of-the-configuration-manager-client)
- [Un script](#manually-initiate-client-policy-retrieval-by-script)

> [!NOTE]  
>   
>  Pour plus d’informations sur la récupération des stratégies pour les clients qui exécutent Linux et UNIX, consultez [Computer policy for Linux and UNIX servers](../../../core/clients/manage/manage-clients-for-linux-and-unix-servers.md#BKMK_PolicyforLnU).  

#### <a name="initiate-client-policy-retrieval-using-client-notification"></a>Lancer une récupération de stratégie client en utilisant une notification de client  

1.  Dans la console Configuration Manager, choisissez **Ressources et Conformité** > **Regroupements de périphériques**.  

3.  Sélectionnez le regroupement d’appareils contenant les ordinateurs dont vous voulez télécharger la stratégie. Sous l’onglet **Accueil**, dans le groupe **Regroupements**, choisissez **Notification du Client** > **Télécharger la stratégie d’ordinateur**.  

    > [!NOTE]  
    >  Vous pouvez également utiliser une notification de client pour lancer la récupération de la stratégie pour un ou plusieurs périphériques sélectionnés affichés dans un nœud de regroupement temporaire sous le nœud **Périphériques** .  

#### <a name="manually-initiate-client-policy-retrieval-on-the-actions-tab-of-the-configuration-manager-client"></a>Lancer manuellement la récupération de stratégie du client sous l’onglet Actions du client Configuration Manager  

1.  Sélectionnez **Configuration Manager** dans le panneau de configuration de l'ordinateur.  

2.  Sous l’onglet **Actions**, choisissez **Récupération de stratégie ordinateur et cycle d’évaluation** pour lancer la stratégie ordinateur, puis choisissez **Exécuter maintenant**.  

4.  Cliquez sur **OK** pour confirmer la demande.  

5.  Répétez les étapes 3 et 4 pour toutes les actions dont vous avez besoin, telles que **Récupération de stratégie utilisateur et cycle d’évaluation** pour les paramètres client utilisateur.  

#### <a name="manually-initiate-client-policy-retrieval-by-script"></a>Lancer manuellement la récupération de stratégie du client par script  

1.  Ouvrez un éditeur de texte, tel que le Bloc-notes.  

2.  Copiez et insérez le code suivant dans le fichier :  

    ```  
    on error resume next  

    dim oCPAppletMgr 'Control Applet manager object.  
    dim oClientAction 'Individual client action.  
    dim oClientActions 'A collection of client actions.  

    'Get the Control Panel manager object.  
    set  oCPAppletMgr=CreateObject("CPApplet.CPAppletMgr")  
    if err.number <> 0 then  
        Wscript.echo "Couldn't create control panel application manager"  
        WScript.Quit  
    end if  

    'Get a collection of actions.  
    set oClientActions=oCPAppletMgr.GetClientActions  
    if err.number<>0 then  
        wscript.echo "Couldn't get the client actions"  
        set oCPAppletMgr=nothing  
        WScript.Quit  
    end if  

    'Display each client action name and perform it.  
    For Each oClientAction In oClientActions  

        if oClientAction.Name = "Request & Evaluate Machine Policy" then  
            wscript.echo "Performing action " + oClientAction.Name   
            oClientAction.PerformAction  
        end if  
    next  

    set oClientActions=nothing  
    set oCPAppletMgr=nothing  
    ```  

3.  Enregistrez le fichier avec une extension .vbs.  

4.  Sur l'ordinateur client, exécutez le fichier à l'aide de l'une des méthodes ci-après :  

    -   Accédez au fichier via l'Explorateur Windows et double-cliquez sur le fichier de script.  

    -   Ouvrez une invite de commandes et tapez **cscript &lt;chemin\nom_fichier.vbs>**.  

5.  Cliquez sur **OK** dans la boîte de dialogue **Environnement d’exécution de scripts WSH (Windows Script Host)**.  
