---
title: "Garantir la conformité des appareils | Microsoft Docs"
description: "Gérez la configuration et la conformité des appareils de votre organisation à l’aide de System Center Configuration Manager."
ms.custom: na
ms.date: 10/06/2016
ms.prod: configuration-manager
ms.technology: configmgr-other
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 7568c9aa-b99e-4466-bfc8-0301aa376930
caps.latest.revision: "8"
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.openlocfilehash: f7ecfe550d2e28579ea873442b2a68dc1c7c5483
ms.sourcegitcommit: 51fc48fb023f1e8d995c6c4eacfda7dbec4d0b2f
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/07/2017
---
# <a name="ensure-device-compliance-with-system-center-configuration-manager"></a>Garantir la conformité des appareils avec System Center Configuration Manager

*S’applique à : System Center Configuration Manager (Current Branch)*

Les paramètres de compatibilité dans System Center Configuration Manager vous donnent les outils et ressources nécessaires pour gérer la configuration et la conformité des appareils de votre organisation. Cela vous permet de prendre en charge les exigences de l’entreprise suivantes :  

-   Comparer la configuration des PC Windows, des ordinateurs Mac, des serveurs et des appareils mobiles que vous gérez avec les configurations recommandées que vous créez ou que vous obtenez d’autres fournisseurs  

-   Identifier les configurations d’appareil non autorisées  

-   Signaler la conformité avec les stratégies réglementaires et les stratégies de sécurité internes  

-   Identifier les failles de sécurité  

-   Fournir au personnel du support technique les informations permettant de détecter les causes probables des incidents et problèmes signalés en identifiant les configurations non conformes  

-   Corriger automatiquement certains paramètres non conformes sur les appareils mobiles  

-   Corriger la non-conformité en déployant des applications, des packages et des programmes ou bien des scripts dans un regroupement automatiquement rempli par des appareils qui indiquent leur non-conformité  


## <a name="get-started"></a>Prise en main  
 Découvrez les principes de base des paramètres de compatibilité et les tâches associées que vous pouvez effectuer.  

 [Bien démarrer avec les paramètres de compatibilité](../../compliance/get-started/get-started-with-compliance-settings.md)  

## <a name="plan-and-design"></a>Planifier et concevoir  
 Avant de commencer à manipuler les paramètres de compatibilité, assurez-vous d’avoir implémenté les conditions préalables que vous trouverez dans cette rubrique.  

 [Planifier et configurer les paramètres de compatibilité](../../compliance/plan-design/plan-for-and-configure-compliance-settings.md)  

## <a name="common-tasks"></a>Tâches courantes  
 Cette section décrit quelques scénarios courants qui vous aideront à vous familiariser avec l’utilisation des paramètres de compatibilité dans Configuration Manager.  

 [Tâches courantes de gestion de la conformité](../../compliance/plan-design/common-tasks-for-managing-compliance.md)  

## <a name="remote-connection-profiles"></a>Profils de connexion à distance  
 Ce type d’élément de configuration vous permet de configurer les PC de vos utilisateurs de sorte qu’ils se connectent à distance aux ordinateurs professionnels quand ils ne sont pas connectés au domaine ou si leurs ordinateurs personnels sont connectés via Internet.  

 [Créer des profils de connexion à distance](/sccm/compliance/deploy-use/create-remote-connection-profiles)  

## <a name="user-data-and-profiles"></a>Données et profils utilisateur  
 Ce type d’élément de configuration contient des paramètres qui peuvent gérer la redirection des dossiers, les fichiers hors connexion et les profils itinérants sur les ordinateurs qui exécutent Windows 8 et versions ultérieures pour les utilisateurs de votre hiérarchie.  

 [Créer des éléments de configuration des données et profils utilisateur](/sccm/compliance/deploy-use/create-user-data-and-profiles-configuration-items)  

## <a name="windows-edition-upgrade-policy"></a>Stratégie de mise à niveau d’édition Windows  
 La stratégie de mise à niveau d’édition vous permet de mettre automatiquement à niveau les appareils Windows 10 vers une version plus récente. Vous pouvez spécifier une clé de produit pour mettre à niveau les versions de Windows 10 Desktop ou un fichier de licence qui permet de mettre à niveau les appareils exécutant Windows 10 Mobile et Windows 10 Holographique.  

 [Mettre à niveau des appareils Windows avec la stratégie de mise à niveau d’édition](/sccm/compliance/deploy-use/upgrade-windows-version)  
