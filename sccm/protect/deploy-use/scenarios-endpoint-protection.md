---
title: "Scénario - Endpoint Protection protège les ordinateurs contre les programmes malveillants | Microsoft Docs"
description: "Découvrez comment implémenter Endpoint Protection dans Configuration Manager pour protéger les ordinateurs contre les attaques de programmes malveillants."
ms.custom: na
ms.date: 03/13/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 539c7a89-3c03-4571-9cb4-02d455064eeb
caps.latest.revision: "8"
author: NathBarn
ms.author: nathbarn
manager: angrobe
ms.openlocfilehash: b98684d44874ff246e4d675039c6e443aee82a62
ms.sourcegitcommit: 51fc48fb023f1e8d995c6c4eacfda7dbec4d0b2f
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/07/2017
---
# <a name="example-scenario-using-system-center-endpoint-protection-to-protect-computers-from-malware-in-system-center-configuration-manager"></a>Exemple de scénario : utilisation de System Center Endpoint Protection pour protéger des ordinateurs contre les programmes malveillants dans System Center Configuration Manager

*S’applique à : System Center Configuration Manager (Current Branch)*

Cette rubrique fournit un exemple de scénario sur la manière d’implémenter Endpoint Protection dans Configuration Manager pour protéger les ordinateurs d’une organisation contre les attaques de programmes malveillants.  

 John est l’administrateur de Configuration Manager à la Woodgrove Bank. La banque utilise actuellement System Center Endpoint Protection pour protéger les ordinateurs contre les attaques de programmes malveillants. Elle utilise également la stratégie de groupe Windows pour s’assurer que le Pare-feu Windows est activé sur tous les ordinateurs de l’entreprise et que les utilisateurs sont avertis quand il bloque un nouveau programme.  

 John est chargé de mettre à niveau le logiciel anti-programme malveillant de Woodgrove Bank vers System Center Endpoint Protection pour que la banque puisse tirer parti des fonctionnalités les plus récentes contre les programmes malveillants et qu’elle puisse gérer de manière centralisée la solution anti-programme malveillant à partir de la console Configuration Manager. Les impératifs de cette implémentation sont les suivants :  

-   Utiliser Configuration Manager pour gérer les paramètres du Pare-feu Windows qui sont gérés actuellement par la stratégie de groupe.  

-   Utiliser les mises à jour logicielles Configuration Manager pour télécharger les définitions de programmes malveillants sur les ordinateurs. Si les mises à jour logicielles ne sont pas disponibles, par exemple si l’ordinateur n’est pas connecté au réseau d’entreprise, les ordinateurs doivent télécharger les mises à jour de définitions à partir de Microsoft Update.  

-   Les ordinateurs des utilisateurs doivent effectuer une analyse rapide des programmes malveillants tous les jours. Les serveurs, quant à eux, doivent exécuter une analyse complète tous les samedis en dehors des heures de travail, à une heure du matin.  

-   Envoyer une alerte par courrier électronique chaque fois que l’un des événements suivants se produit :  

    -   Un programme malveillant est détecté sur un ordinateur.  

    -   La même menace de programme malveillant est détectée sur plus de 5 % des ordinateurs.  

    -   La même menace de programme malveillant est détectée plus de cinq fois durant une période de 24 heures.  

    -   Plus de trois différents types de programmes malveillants sont détectés durant une période de 24 heures.  

-   Désinstaller la solution anti-programme malveillant existante.  

 John effectue ensuite les étapes suivantes pour implémenter Endpoint Protection :  

##  <a name="steps-to-implement-endpoint-protection"></a>Étapes pour implémenter Endpoint Protection  

|Processus|Référence|  
|-------------|---------------|  
|John passe en revue les informations disponibles sur les principes de base de Endpoint Protection dans Configuration Manager.|Pour une vue d’ensemble de Endpoint Protection, voir [Endpoint Protection dans System Center Configuration Manager](endpoint-protection.md).|  
|John passe en revue et implémente la configuration requise pour utiliser Endpoint Protection.|Pour plus d’informations sur la configuration requise pour Endpoint Protection, voir [Planification de Endpoint Protection](../plan-design/planning-for-endpoint-protection.md).|  
|John installe le rôle de système de site Endpoint Protection sur un seul serveur de système de site, tout en haut de la hiérarchie Woodgrove Bank.|Pour plus d’informations sur l’installation du rôle de système de site Endpoint Protection, voir « Configuration requise » dans [Configurer Endpoint Protection](configure-endpoint-protection.md).|  
|John configure Configuration Manager pour utiliser un serveur SMTP pour envoyer les alertes par courrier électronique.<br /><br /> **Remarque :** vous devez configurer un serveur SMTP uniquement si vous souhaitez être averti par courrier électronique quand une alerte Endpoint Protection est générée.|Pour plus d’informations, voir [Configurer des alertes dans Endpoint Protection](endpoint-configure-alerts.md).|  
|John crée un regroupement d’appareils qui contient tous les ordinateurs et serveurs pour installer le client Endpoint Protection. Il nomme ce regroupement **Tous les ordinateurs protégés par Endpoint Protection**.<br /><br /> **Astuce :** vous ne pouvez pas configurer d'alertes pour les regroupements d'utilisateurs.|Pour plus d’informations sur la création de regroupements, voir [Guide pratique pour créer des regroupements dans System Center Configuration Manager](../../core/clients/manage/collections/create-collections.md).|  
|Il configure les alertes suivantes pour la collection : <br /><br />1) **Un programme malveillant est détecté** : John configure une gravité d'alerte **Critique**. <br /><br />2) **Le même type de programme malveillant est détecté sur un certain nombre d'ordinateurs** : John configure une gravité d'alerte **Critique** et spécifie que l'alerte est générée quand des programmes malveillants sont détectés sur plus de 5 % des ordinateurs. <br /><br />3) **Le même type de programme malveillant est fréquemment détecté sur un ordinateur dans l'intervalle spécifié** : John configure une gravité d'alerte **Critique** et spécifie que l'alerte est générée quand un programme malveillant est détecté plus de 5 fois sur une période de 24 heures. <br /><br />4) **Plusieurs types de programmes malveillants sont détectés sur le même ordinateur dans l'intervalle spécifié** : John configure une gravité d'alerte **Critique** et spécifie que l'alerte est générée quand plus de trois types de programmes malveillants sont détectés sur une période de 24 heures.<br /><br /> La valeur de **Gravité d’alerte** indique le niveau d’alerte affiché dans la console Configuration Manager et dans les alertes que John reçoit dans un e-mail.<br /><br /> Il sélectionne également l’option **Afficher ce regroupement dans le tableau de bord de Endpoint Protection** pour pouvoir surveiller les alertes dans la console Configuration Manager.|Voir « Configurer des alertes dans Endpoint Protection » dans [Configuration de Endpoint Protection dans Configuration Manager](endpoint-configure-alerts.md).|  
|John configure les mises à jour logicielles de Configuration Manager pour télécharger et déployer les mises à jour de définitions trois fois par jour à l’aide d’une règle de déploiement automatique.|Pour plus d’informations, voir « Utilisation de mises à jour logicielles de Configuration Manager pour fournir des mises à jour de définitions » dans [Configuration de Endpoint Protection dans Configuration Manager](endpoint-definitions-configmgr.md).|  
|John examine les paramètres de la stratégie de logiciel anti-programme malveillant par défaut, qui contient les paramètres de sécurité recommandés par Microsoft. Pour que les ordinateurs effectuent une analyse rapide quotidienne, il modifie les paramètres suivants :<br /><br /> 1) **Exécuter une analyse rapide quotidienne sur les ordinateurs clients** : **Oui**.<br /><br /> 2) **Heure programmée d'analyse rapide quotidienne** : **09:00**.<br /><br /> John remarque que l’option **Mises à jour distribuées par Microsoft Update** est sélectionné par défaut comme source des mises à jour de définitions. Ceci est conforme à l’exigence selon laquelle les ordinateurs doivent télécharger les définitions à partir de Microsoft Update quand ils ne peuvent pas recevoir de mises à jour logicielles de Configuration Manager.|Voir [Comment créer et déployer des stratégies anti-programme malveillant pour Endpoint Protection dans System Center Configuration Manager](endpoint-antimalware-policies.md).|  
|John crée un regroupement nommé **Serveurs Woodgrove Bank**qui contient uniquement les serveurs de Woodgrove Bank.|Voir [Comment créer des regroupements dans System Center Configuration Manager](../../core/clients/manage/collections/create-collections.md).|  
|John crée une stratégie de logiciel anti-programme malveillant personnalisée nommée **Stratégie de serveur Woodgrove Bank**. Il ajoute uniquement les paramètres pour **Analyses planifiées** et apporte les modifications suivantes :<br /><br /> **Type d’analyse**:  **Complète**<br /><br /> **Jour d’analyse**:  **Samedi**<br /><br /> **Heure de l’analyse**: **01h00**<br /><br /> **Exécuter une analyse rapide quotidienne sur les ordinateurs clients**:  **Non**.|Voir [Comment créer et déployer des stratégies anti-programme malveillant pour Endpoint Protection dans System Center Configuration Manager](endpoint-antimalware-policies.md).|  
|John déploie la stratégie de logiciel anti-programme malveillant personnalisée **Stratégie de serveur Woodgrove Bank** dans le regroupement **Serveurs Woodgrove Bank** .|Voir « Pour déployer une stratégie de logiciel anti-programme malveillant sur les ordinateurs clients » dans la rubrique [Comment créer et déployer des stratégies anti-programme malveillant pour Endpoint Protection](endpoint-antimalware-policies.md).|  
|John crée un ensemble de paramètres d’appareils clients personnalisé pour Endpoint Protection et le nomme **Paramètres Endpoint Protection Woodgrove Bank**.<br /><br /> **Remarque :** si vous ne souhaitez pas installer et activer Endpoint Protection sur tous les clients de votre hiérarchie, assurez-vous que les options **Gérer le client Endpoint Protection sur les ordinateurs clients** et **Installer le client Endpoint Protection sur les ordinateurs clients** ont toutes les deux la valeur **Non** dans les paramètres client par défaut.|Pour plus d’informations, voir [Configurer des paramètres client personnalisés pour Endpoint Protection](endpoint-protection-configure-client.md).|  
|Il configure les paramètres suivants pour Endpoint Protection :<br /><br /> **Gérer le client Endpoint Protection sur les ordinateurs clients**:  **Oui**<br /><br /> Ce paramètre et cette valeur garantissent que tout client Endpoint Protection existant qui est installé est géré par Configuration Manager.<br /><br /> **Installer le client Endpoint Protection sur les ordinateurs clients**:  **Oui**.<br /><br /> **Supprimer automatiquement le logiciel anti-programmes malveillants installé avant Endpoint Protection**:  **Oui**.<br /><br /> Ce paramètre et cette valeur sont conformes à l’exigence d’entreprise selon laquelle le logiciel anti-programme malveillant doit être supprimé avant qu’Endpoint Protection soit installé et activé.|Pour plus d’informations, voir [Configurer des paramètres client personnalisés pour Endpoint Protection](endpoint-protection-configure-client.md).|  
|John déploie les paramètres client **Paramètres Endpoint Protection Woodgrove Bank** dans le regroupement **Tous les ordinateurs protégés par Endpoint Protection**.|Voir « Configurer des paramètres client personnalisés pour Endpoint Protection » dans [Configuration de Endpoint Protection dans Configuration Manager](endpoint-antimalware-policies.md).|  
|John utilise l’Assistant Création d’une stratégie de Pare-feu Windows pour créer une stratégie en configurant les paramètres suivants pour le profil de domaine :<br /><br /> 1) **Activer le pare-feu Windows** : **Oui**<br /><br /> 2)<br />                    **Informer l’utilisateur lorsque le Pare-feu Windows bloque un nouveau programme**: **Oui**|Voir [Guide pratique pour créer et déployer des stratégies de pare-feu Windows pour Endpoint Protection dans System Center Configuration Manager](../../protect/deploy-use/create-windows-firewall-policies.md).|  
|John déploie la nouvelle stratégie de pare-feu dans le regroupement **Tous les ordinateurs protégés par Endpoint Protection** qu’il a créé précédemment.|Pour plus d'informations, voir « Pour déployer une stratégie de pare-feu Windows » dans [Comment créer et déployer des stratégies de pare-feu Windows pour Endpoint Protection dans System Center Configuration Manager](create-windows-firewall-policies.md).|  
|John utilise les tâches de gestion disponibles pour Endpoint Protection pour gérer les stratégies anti-programme malveillant et les stratégies de pare-feu Windows, pour effectuer des analyses à la demande des ordinateurs en cas de nécessité, pour forcer les ordinateurs à télécharger les dernières définitions et pour spécifier les actions supplémentaires à effectuer quand un programme malveillant est détecté.|Voir [Guide pratique pour gérer les stratégies anti-programme malveillant et les paramètres de pare-feu pour Endpoint Protection dans System Center Configuration Manager](endpoint-antimalware-firewall.md).|  
|John utilise les méthodes suivantes pour surveiller l’état de Endpoint Protection et ses actions :<br /><br /> 1) Utilisation du nœud **État Endpoint Protection** sous **Sécurité** dans l’espace de travail **Surveillance**.<br /><br /> 2) Utilisation du nœud **Endpoint Protection** dans l’espace de travail **Ressources et Conformité**.<br /><br /> 3) Utilisation des rapports Configuration Manager intégrés.|Voir [Guide pratique pour surveiller Endpoint Protection dans System Center Configuration Manager](monitor-endpoint-protection.md).|  

 John signale à son responsable que l’implémentation de Endpoint Protection a réussi, et il confirme que les ordinateurs de la Woodgrove Bank sont maintenant protégés contre les programmes malveillants conformément aux exigences spécifiées.
