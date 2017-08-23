---
title: "Utiliser les données de diagnostic | Microsoft Docs"
description: "Découvrez comment Microsoft utilise les données de diagnostic et d’utilisation collectées par System Center Configuration Manager."
ms.custom: na
ms.date: 12/29/2016
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: a8021bc8-2799-41f4-83c2-e27d1242028c
caps.latest.revision: "5"
author: Brenduns
ms.author: brenduns
manager: angrobe
ms.openlocfilehash: 9864f6ba7b9a2211c99b1a5d9ebd582e01ccfeb6
ms.sourcegitcommit: 51fc48fb023f1e8d995c6c4eacfda7dbec4d0b2f
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/07/2017
---
# <a name="how-diagnostics-and-usage-data-is-used-for-system-center-configuration-manager"></a>Utilisation des données d’utilisation et de diagnostic pour System Center Configuration Manager

*S’applique à : System Center Configuration Manager (Current Branch)*

Les données de diagnostic et d’utilisation que System Center Configuration Manager collecte fournissent à Microsoft un retour d’expérience quasi immédiat sur la manière dont le produit fonctionne, et permettent d’améliorer les mises à jour ultérieures. Nous pouvons également voir des données de configuration qui nous aident à concevoir et tester les configurations qui sont en production. Exemple :  

-   Versions de Windows Server utilisées par les serveurs de site  

-   Modules linguistiques installés  

-   Différentiel du schéma SQL par rapport aux paramètres par défaut du produit  

Ces données aident l’équipe de conception à planifier les prochains tests visant à garantir la meilleure expérience possible pour les configurations les plus courantes. Les mises à jour de Configuration Manager étant publiées à un rythme plus soutenu (pour mieux prendre en charge les technologies qui évoluent rapidement, telles que Windows 10 et Microsoft Intune), ces données sont cruciales pour une adaptation rapide.  

Il est également important de savoir à quoi les données de diagnostic et d’utilisation ne sont pas utilisées. Microsoft n’utilise pas ces données pour ce qui suit :  

-   Audits de licence (par exemple, comparer l’utilisation des clients avec les contrats de licence)  

-   Audit de produits non pris en charge  

-   Publicité basée sur des données disponibles, telles que l’utilisation de fonctionnalités ou la géolocalisation (fuseau horaire)  

##  <a name="bkmk_improve"></a> Exemples de la manière dont les données de diagnostic et d’utilisation contribuent à améliorer le produit  
Microsoft utilise les données disponibles pour améliorer le produit. Voici quelques exemples :  

-   **Prise en charge révisée pour les systèmes d’exploitation serveur plus anciens :**  

     La prise en charge initiale offerte par System Center Configuration Manager (Current Branch) limitait la période de prise en charge de Windows Server 2008 R2. Après examen des données d’utilisation de clients qui avaient effectué une mise à niveau vers la version Current Branch de Configuration Manager, nous avons jugé utile de modifier et d’étendre cette période pour prendre en charge les clients qui continuaient d’utiliser ce système d’exploitation serveur pour héberger des serveurs de site et des rôles de système de site.  

-   **Vérifications de configuration requise améliorées :**  

     Sur la base des données d’utilisation, nous avons amélioré les vérifications des conditions préalables à l’installation d’une mise à jour pour supprimer des règles obsolètes, tenir compte de cas supplémentaires et, dans certains cas, résoudre automatiquement certains problèmes.  
