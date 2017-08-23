---
title: "Données de diagnostic pour 1702 | System Center Configuration Manager"
description: "En savoir plus sur les niveaux de données de diagnostic et d’utilisation collectés par System Center Configuration Manager version 1702."
ms.custom: na
ms.date: 3/27/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: d43ab033-2902-4681-8716-b4b17a6df372
caps.latest.revision: "4"
author: Brenduns
ms.author: brenduns
manager: angrobe
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- hu-hu
- it-it
- ja-jp
- ko-kr
- nl-nl
- pl-pl
- pt-br
- pt-pt
- ru-ru
- sv-se
- tr-tr
- zh-cn
- zh-tw
ms.openlocfilehash: 0e1d93712150fb3d6fabc3f057711eba1194c3ad
ms.sourcegitcommit: 51fc48fb023f1e8d995c6c4eacfda7dbec4d0b2f
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/07/2017
---
# <a name="levels-of-diagnostic-usage-data-collection-for-version-1702-of-system-center-configuration-manager"></a>Niveaux de collecte des données de diagnostic et d’utilisation pour la version 1702 de System Center Configuration Manager

*S’applique à : System Center Configuration Manager (Current Branch)*

System Center Configuration Manager version 1702 collecte trois niveaux de données d’utilisation et de diagnostic : **De base**, **Étendu** et **Complet**. Par défaut, cette fonctionnalité est définie sur le niveau Étendu. Les sections suivantes fournissent des détails supplémentaires sur les données collectées par chaque niveau.

Les modifications par rapport aux versions précédentes sont indiquées par ***[Nouveau]***, ***[Mis à jour]***, ***[Supprimé]*** ou ***[Déplacé]***.


> [!IMPORTANT]
>  Configuration Manager ne collecte pas les codes des sites, les noms des sites, les adresses IP, les noms d’utilisateur ou d’ordinateur, les adresses physiques ni les adresses e-mail aux niveaux De base et Étendu. Toute collecte de ces informations au niveau Complet n’est pas intentionnelle : elles peuvent être incluses dans des informations de diagnostic avancées comme des fichiers journaux ou des instantanés de la mémoire. Microsoft n’utilisera pas ces informations pour vous identifier ou vous contacter, ni à des fins publicitaires.



##  <a name="bkmk_change"></a> Modification du niveau
 Les administrateurs qui disposent d’une étendue administrative basée sur des rôles incluant les autorisations **Modification** sur la classe d’objets **Site** peuvent modifier le niveau des données collectées dans les paramètres des données de diagnostic et d’utilisation de la console Configuration Manager.

Vous pouvez changer le niveau de collecte des données à partir de la console en accédant à **Administration** > **Vue d’ensemble** > **Configuration du site** > **Sites**. Ouvrez **Paramètres de hiérarchie**, puis sélectionnez le niveau de données que vous voulez utiliser.  



##  <a name="bkmk_level1"></a> Niveau 1 - De base
Le niveau De base comprend les données relatives à votre hiérarchie, qui sont nécessaires pour aider à améliorer votre expérience d’installation ou de mise à niveau, ainsi que des données pour aider à identifier les mises à jour Configuration Manager qui s’appliquent à votre hiérarchie.

Pour System Center Configuration Manager version 1702, ce niveau inclut les éléments suivants :

- Console d'administration :
   - Statistiques sur les connexions de la console (version, langue, référence (SKU) et architecture du système d’exploitation, mémoire système, nombre de processeurs logiques, ID du site de connexion, versions .NET installées et modules linguistiques de la console)

- Nombres de types d’application et de déploiement de base (nombre total d’applications, nombre total d’applications avec plusieurs types de déploiement, nombre total d’applications avec des dépendances, nombre total d’applications remplacées, nombre de technologies de déploiement utilisées)

- Données de la hiérarchie des sites Configuration Manager de base (liste des sites, type, version, état, nombre de clients et fuseau horaire)

- Configuration de base de données simple (processeurs, configuration du cluster et configuration des vues distribuées)

- ***[Mis à jour] *** Statistiques élémentaires de découverte (nombre de découvertes et tailles de groupe minimum/maximum/moyenne) y compris lorsque le site est entièrement exécuté avec les services Active Directory Azure.

- Informations Endpoint Protection de base (versions du client de logiciel anti-programme malveillant)

- Nombre de déploiements de systèmes d’exploitation de base (images)

- Informations de serveur de système de site de base (rôles de système de site utilisés, état SSL et Internet, système d’exploitation, processeurs, ordinateur physique ou machine virtuelle)

- Schéma de base de données Configuration Manager (hachage de toutes les définitions d’objet)

- Niveau de télémétrie configuré, mode (en ligne ou hors connexion) et configuration de la mise à jour rapide

- Nombre de paramètres régionaux et de langues du client

- Nombre de versions du client Configuration Manager et de versions du système d’exploitation

- Nombre de systèmes d’exploitation des appareils gérés et stratégies définies par le connecteur Exchange

- Nombre d’appareils Windows 10 par branche et build

- Métriques de performances de base de données (informations sur le traitement de la réplication, procédures stockées SQL Server les plus utilisées par processeur et utilisation des disques)

- Types de point de distribution et de point de gestion, et informations de configuration de base (protégés, préparés, PXE, de multidiffusion, d’état SSL, points de distribution pairs/d’extraction, compatibles MDM, compatibles SSL, etc.)

- Informations d’installation :
     - Build, type d’installation, modules linguistiques, fonctionnalités que vous avez activées   

     - Utilisation en préversion, type de support de configuration, type de branche

     - Date d’expiration de Software Assurance      

     - État et erreurs du déploiement du package de mise à jour, progression du téléchargement, et erreurs liées aux prérequis     

     - Utilisation de l’anneau rapide de mise à jour

     - Version du script après mise à niveau

- Version SQL, niveau de Service Pack, édition, ID de classement et jeu de caractères     
- Statistiques de télémétrie (à l’exécution, runtime, erreurs)

- Utilisation de la découverte du réseau (activée ou désactivée)




##  <a name="bkmk_level2"></a> Niveau 2 – Étendu
Le niveau Étendu est configuré par défaut après l’installation. Ce niveau comprend les données collectées au niveau De base, ainsi que les données spécifiques aux fonctionnalités (fréquence et durée d’utilisation), les paramètres du client Configuration Manager (nom du composant, état et paramètres, comme les intervalles d’interrogation) et les informations de base sur les mises à jour logicielles.

Ce niveau est recommandé, car il fournit à Microsoft les données minimales nécessaires pour apporter des améliorations utiles dans les futures versions des produits et services. Ce niveau ne collecte pas les noms des objets (sites, utilisateurs, ordinateur ou objets), les informations sur les objets relatifs à la sécurité ni les vulnérabilités, comme le nombre de systèmes qui nécessitent des mises à jour logicielles.

Pour System Center Configuration Manager version 1702, ce niveau inclut les éléments suivants :

- **Gestion des applications :**  

   - Exigences pour les applications (le nombre de conditions prédéfinies est référencé par la technologie de déploiement)

   - Remplacement des applications, profondeur de chaîne maximale

   - Statistiques d’approbation de l’application et fréquence d’utilisation

   - ***[Mis à jour]*** Informations de déploiement d’application (utilisation de l’installation par rapport à la désinstallation, approbation requise, interaction utilisateur activée/désactivée, dépendance, remplacement et nombre d’utilisations de la fonctionnalité de comportement à l’installation)  

   - Statistiques de taille et de complexité des stratégies d’applications

   - Statistiques de demande d’application disponibles

   - ***[Nouveau]*** Informations de base de configuration pour les packages et les programmes (options de déploiement et indicateurs de programme)

   - Informations de base d’utilisation/de ciblage pour les types de déploiement utilisés au sein de l’organisation (ciblé utilisateur ou appareil, nécessaire ou disponible, et applications universelles)

   - Statistiques des groupes de limites (nombre de rapides, nombre de lents, nombre par groupe)

   - Nombre d’environnements App-V et propriétés de déploiement

   - Nombre d’applicabilités de l’application par système d’exploitation  

   - ***[Nouveau]*** Nombre d’applications référencées par une séquence de tâches

   - Nombre de packages par type  

   - Nombre de déploiements de package/programme  

   - Nombre de licences d’application Windows 10 concédées  

   - Nombre d’applications Windows Store pour Entreprises et statistiques de synchronisation (notamment un résumé des types d’applications, l’état des applications sous licence ainsi que le nombre d’applications sous licence en ligne et hors connexion)  

   - Type et durée de fenêtre de maintenance  

   - Nombre minimal/maximal/moyen de déploiements d’applications par utilisateur/appareil par période

   - ***[Nouveau]*** Codes d’erreur d’installation d’application les plus courants par technologie de déploiement

   - Options de configuration MSI et nombres

   - ***[Nouveau]*** Statistiques sur l’interaction de l’utilisateur final avec notification des déploiements de logiciels requis   

   - Utilisation et mode de création d’Universal Data Access (UDA)




- **Client :**  

   - Version du client AMT (Active Management Technology)

   - Âge du BIOS en années

   - Mise à niveau automatique du client : configuration du déploiement, notamment le test du client et l’utilisation de l’exclusion (client d’interopérabilité étendue)

   - Configuration de la taille du cache du client

   - Erreurs de téléchargement de déploiement des clients

   - Statistiques d’intégrité du client et récapitulatif des problèmes principaux

   - État des actions de notification du client (nombre d’exécutions de chaque action, nombre maximal de clients ciblés et taux de réussite moyen)
   - Nombre d’installations de client à partir de chaque type d’emplacement source  

   - Nombre d’échecs d’installation de client  

   - ***[Nouveau]*** Nombre d’appareils virtualisés par Hyper-V ou Azure  

   - Nombre d’actions du Centre logiciel   

   - ***[Nouveau]*** Nombre d’appareils compatibles UEFI

   - Méthodes de déploiement utilisées pour le client et nombre de clients par méthode de déploiement

   - Liste/nombre d’agents clients activés  

   - Ancienneté du système d’exploitation en mois

   - Nombre de classes d’inventaire matériel, règles d’inventaire logiciel et règles de regroupement de fichiers

   - ***[Nouveau]*** Statistiques pour l’attestation de l’intégrité des appareils, y compris les codes d’erreur les plus courants, le nombre de serveurs locaux et le nombre d’appareils dans différents états.



- **Services cloud :**

  - Configuration et statistiques d’utilisation de la passerelle de gestion cloud

  - ***[Nouveau]*** Nombre de clients joints aux services Azure Active Directory

  - Nombre de regroupements qui sont synchronisés avec Operations Management Suite

  - Nombre de connecteurs Upgrade Analytics

  - Activation ou non du connecteur cloud Operations Management Suite




- **Regroupements :**

    - Utilisation des ID de regroupement (ne pas manquer d’ID)

    - Statistiques d’évaluation des regroupements (durée des requêtes, nombre de regroupements affectés et non affectés, nombres par type, substitution d’ID et utilisation des règles)

    - Regroupements sans déploiement




- **Paramètres de compatibilité :**  

    - Informations de la ligne de base de configuration de base (nombre, nombre de déploiements et nombre de références)  

    - Nombre d’éléments de configuration par type  

    - Nombre de déploiements qui référencent des paramètres prédéfinis (avec capture du paramètre de correction)  

    - Nombre de règles et de déploiements créés pour les paramètres personnalisés (avec capture du paramètre de correction)  
    -  Nombre de modèles SCEP (Simple Certificate Enrollment Protocol), VPN, Wi-Fi, de certificat (.pfx) et de stratégie de conformité déployés

    - Nombre de déploiements de certificat SCEP, VPN, Wi-Fi, certificat (.pfx) et stratégie de conformité par plateforme

    - Stratégie Passport for Work (créée, déployée)



- **Contenu :**  

    - Informations sur les groupes de limites (nombre de limites et de systèmes de site qui sont attribués à chaque groupe de limites)  

    - Relations de groupes de limites et configuration de secours

    - Statistiques de téléchargement du contenu client

    - Nombre de limites par type  

    - Nombre de clients du cache de pairs et statistiques d’utilisation

    - Informations sur la configuration du gestionnaire de distribution (threads, délai de nouvelle tentative, nombre de nouvelles tentatives et paramètres de point de distribution d’extraction)  

    - Informations sur la configuration des points de distribution (utilisation de BranchCache et surveillance des points de distribution)

    - Informations sur les groupes de points de distribution (nombre de packages et de points de distribution qui sont attribués à chaque groupe de points de distribution)  



- **Endpoint Protection :**  

   - Nombre de stratégies ATP (Advanced Threat Protection) (nombre de stratégies et si elles sont ou non déployées)

   - Nombre d’alertes configurées pour la fonctionnalité Endpoint Protection  

   - Nombre de regroupements sélectionnés pour être affichés dans le tableau de bord Endpoint Protection  

   - Erreurs de déploiement Endpoint Protection (nombre de codes d’erreur de déploiement de stratégie Endpoint Protection)  

   - Utilisation des stratégies du Pare-feu Windows et de logiciel anti-programme malveillant Endpoint Protection (nombre de stratégies uniques attribuées au groupe)<br /><br /> Ceci ne comprend pas d’informations sur les paramètres inclus dans la stratégie.  



- **Migration :**

  - Nombre d’objets migrés (utilisation de l’Assistant Migration)



- **Gestion des appareils mobiles (MDM) :**  

    - Nombre d’actions d’appareil mobile émises : commandes de verrouillage, de réinitialisation, de mise hors service et Synchroniser maintenant

    - Nombre de stratégies d’appareil mobile  

    - Nombre d’appareils mobiles gérés par Configuration Manager et Microsoft Intune, et méthode d’inscription (en bloc ou basée sur l’utilisateur)  

    - Nombre d’utilisateurs qui ont plusieurs appareils mobiles inscrits  

    - Statistiques et calendrier d’interrogation des appareils mobiles pour la vérification dans la durée des appareils mobiles  




- **Dépannage de Microsoft Intune :**

    - Nombre et taille des messages d’actions d’appareil (réinitialiser, mettre hors service, verrouiller), de télémétrie et de données qui sont répliqués vers Microsoft Intune

    - Nombre et taille des messages d’état, de statut, d’inventaire, RDR, DDR, UDX, d’état de locataire, POL, LOG, de certificat, CRP, de resynchronisation, CFD, RDO, BEX, ISM et de conformité qui sont téléchargés à partir de Microsoft Intune

    - Statistiques de synchronisation utilisateur complète et différentielle pour Microsoft Intune



- **Gestion des appareils mobiles (MDM) locale :**  

    - Nombre de profils et de packages d’inscription en bloc Windows 10  

    - Statistiques de réussite/échec de déploiement pour les déploiements d’applications de gestion MDM locale  




- **Déploiement du système d’exploitation :**  

    - Nombre d’images de démarrage, de pilotes, de packages de pilotes, de points de distribution en multidiffusion, de points de distribution compatibles PXE et de séquences de tâches  

    - Nombre de stratégies de mise à niveau d’édition

    - Nombre d’utilisations des étapes de séquence de tâches



- **Mises à jour du site :**

    - Versions des correctifs logiciels de Configuration Manager installés



- **Mises à jour logicielles :**  

    - Différentiels de disponibilité et d’échéance qui sont utilisés dans les règles de déploiement automatique  

    - Nombre moyen et maximal d’attributions par mise à jour  

    - Calendriers d’analyse et d’évaluation des mises à jour client  

    - Classifications qui sont synchronisées par le point de mise à jour logicielle

    - Statistiques d’application de correctifs logiciels au cluster  

    - Configuration des mises à jour rapides de Windows 10

    - Configurations qui sont utilisées pour les plans de maintenance actifs de Windows 10  

    - Nombre de mises à jour Office 365 déployées  

    - Nombre de groupes et d’attributions de mises à jour  

    - Nombre de packages de mises à jour et nombre maximal/minimal/moyen de points de distribution qui sont ciblés par les packages  

    - Nombre de mises à jour créées et déployées avec System Center Update Publisher  

    - Nombre de clients Windows 10 qui utilisent Windows Update for Business  

    - Nombre de règles de déploiement automatique qui sont liées à la synchronisation  

    - Nombre de règles de déploiement automatique qui créent de nouvelles mises à jour ou ajoutent des mises à jour à un groupe existant  

    - Nombre de règles de déploiement automatique avec plusieurs déploiements  
    - Nombre de groupes de mises à jour et nombre minimal/maximal/moyen de mises à jour par groupe  

    - Nombre de mises à jour et pourcentage de mises à jour qui sont déployées, expirées, remplacées, téléchargées et qui contiennent des CLUF  

    - Statistiques d’équilibrage de charge du point de mise à jour logicielle

    - Planification de la synchronisation du point de mise à jour logicielle  

    - Nombre total/moyen de regroupements comportant des déploiements de mises à jour logicielles et nombre maximal/moyen de mises à jour déployées  

    - Codes d’erreur d’analyse des mises à jour et nombre d’ordinateurs  

    - Versions de contenu du tableau de bord Windows 10  



- **Données de performances/SQL :**  

    - ***[Nouveau]*** Configuration et durée de la synthèse du site

    - Nombre des plus grandes tables de base de données  

    - Statistiques opérationnelles de découverte (nombre d’objets trouvés)

    - Types de découverte, activés et planifiés (complète, incrémentielle)

    - Informations sur les réplicas SQL AlwaysOn, utilisation et état d’intégrité

    - Problèmes de performances du suivi des modifications SQL, période de rétention et état de nettoyage automatique

    - Période de rétention du suivi des modifications SQL

    - ***[Nouveau]*** Statistiques de performances des messages d’état et de statut, y compris les types de messages les plus courants et les plus coûteux



- **Divers**

    - ***[Nouveau]*** Configuration du Point de service de l’entrepôt de données, y compris la planification de la synchronisation et le délai moyen

    - Nombre de sites avec Wake On Lan (WOL)

    - Statistiques de performances et d’utilisation des rapports  



##  <a name="bkmk_level3"></a> Niveau 3 – Complet
Le niveau Complet inclut toutes les données des niveaux De base et Étendu. Il inclut également des informations supplémentaires sur Endpoint Protection, les pourcentages de compatibilité des mises à jour et les informations de mise à jour logicielle.  Ce niveau peut également inclure des informations de diagnostic avancées, comme des fichiers système et des instantanés de la mémoire, qui peuvent inclure des informations personnelles qui existaient dans la mémoire ou les fichiers journaux au moment de la capture.

Pour System Center Configuration Manager version 1702, ce niveau inclut les éléments suivants :

- Informations sur le calendrier d’évaluation de règle de déploiement automatique

- Récapitulatif d’intégrité ATP

- Statistiques d’évaluation et d’actualisation des regroupements

- Paramètres de conformité : détails de configuration des modèles SCEP, VPN, Wi-Fi et stratégie de conformité, nombre de groupes avec des mises à jour logicielles expirées

- Pack de configuration DCM pour l’utilisation de System Center Configuration Manager

- Détails des erreurs d’installation du déploiement des clients
- Récapitulatif de l’intégrité Endpoint Protection (y compris le nombre de clients protégés, présentant un risque, inconnus et non pris en charge)

- Configuration de la stratégie Endpoint Protection

- ***[Nouveau]*** Liste des processus configurés avec le comportement à l’installation des applications

- Nombre minimal/maximal/moyen d’heures depuis la dernière analyse des mises à jour logicielles

- Nombre minimal/maximal/moyen de clients inactifs dans les regroupements de déploiements de mise à jour logicielle

- Nombre minimal/maximal/moyen de mises à jour logicielles par package

- Code de produit MSI (applications courantes que les clients déploient)

- Compatibilité globale des déploiements de mise à jour logicielle

- Nombres et codes d’erreur de déploiement de mise à jour logicielle

- Informations de déploiement de mise à jour logicielle (pourcentage de déploiements ciblés avec le client ou l’heure UTC, obligatoire/facultatif/en mode silencieux, et suppression du redémarrage)

- Produits des mises à jour logicielles synchronisés par le point de mise à jour logicielle

- Pourcentages de réussite d’analyse des mises à jour logicielles

- 50 premières unités centrales dans l’environnement

- Type de stratégies d’accès conditionnel EAS (bloquer ou mettre en quarantaine) pour les appareils gérés par Intune

- Détails des applications du Windows Store pour Entreprises (liste de non-agrégation des applications synchronisées, notamment l’ID de l’application, l’état (en ligne ou hors connexion) et le nombre total de licences achetées)
