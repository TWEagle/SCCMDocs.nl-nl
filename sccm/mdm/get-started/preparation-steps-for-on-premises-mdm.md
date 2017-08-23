---
title: "Étapes de préparation | Microsoft Docs"
description: "Préparez-vous à gérer les appareils avec la fonctionnalité de gestion des appareils mobiles locale de System Center Configuration Manager."
ms.custom: na
ms.date: 03/05/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: configmgr-hybrid
ms.tgt_pltfrm: na
ms.topic: get-started-article
ms.assetid: 1ef60106-8f31-46d6-95a6-25a6495f22c7
caps.latest.revision: "4"
author: Mtillman
ms.author: mtillman
manager: angrobe
ms.openlocfilehash: 85bdadaaaeed9a42cfa5165d2b9f0f3ef434dc03
ms.sourcegitcommit: 51fc48fb023f1e8d995c6c4eacfda7dbec4d0b2f
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/07/2017
---
# <a name="preparation-steps-for-on-premises-mobile-device-management-in-system-center-configuration-manager"></a>Étapes de préparation pour la gestion des appareils mobiles locale dans System Center Configuration Manager

*S’applique à : System Center Configuration Manager (Current Branch)*

Gérer les appareils à l’aide de la fonctionnalité de gestion des appareils mobiles locale de System Center Configuration Manager exige que l’infrastructure Configuration Manager soit configurée de telle sorte que les rôles de système de site requis (point proxy d’inscription, point d’inscription, point de gestion d’appareil et point de distribution) puissent communiquer avec les appareils mobiles à gérer sur un canal fiable.  

 Les tâches principales suivantes sont nécessaires à la préparation du système Configuration Manager à la gestion des appareils mobiles locale :  

-   [Configurer un abonnement Microsoft Intune pour la gestion des appareils mobiles locale dans System Center Configuration Manager](../../mdm/get-started/set-up-intune-subscription-on-premises-mdm.md)  

     Dans cette tâche, vous vous inscrivez à Microsoft Intune et ajoutez ensuite l’abonnement à Configuration Manager via la console Configuration Manager. Cette étape est nécessaire uniquement pour la licence. Intune n’est utilisé ni pour gérer les appareils ni pour stocker les informations de gestion. La coordination et la gestion des appareils est entièrement assurée dans votre entreprise à l’aide de l’infrastructure Configuration Manager locale.  

-   [Installer des rôles de système de site pour la gestion des appareils mobiles locale dans System Center Configuration Manager](../../mdm/get-started/install-site-system-roles-for-on-premises-mdm.md)  

     Dans cette tâche, vous installez et configurez les rôles de système de site nécessaires à la gestion des appareils avec l’infrastructure Configuration Manager locale. La fonctionnalité de gestion des appareils mobiles locale exige au minimum les rôles de système de site Point proxy d’inscription, Point d’inscription, Point de gestion d’appareil et Point de distribution.  

-   [Configurer des certificats pour les communications approuvées pour la gestion des appareils mobiles locale dans System Center Configuration Manager](../../mdm/get-started/set-up-certificates-on-premises-mdm.md)  

     Dans cette tâche, vous configurez l’infrastructure Configuration Manager locale pour autoriser les communications fiables (HTTPS) entre les appareils gérés et les serveurs hébergeant les rôles de système de site requis.  

-   [Configurer l’inscription d’appareils pour la gestion des appareils mobiles locale dans System Center Configuration Manager](../../mdm/get-started/set-up-device-enrollment-on-premises-mdm.md)  

     Dans cette tâche, vous autorisez les utilisateurs à inscrire des ordinateurs et des appareils, et vous installez le certificat racine approuvé sur les appareils (en général, ceux qui ne sont pas membres du domaine) pour autoriser les connexions HTTPS aux serveurs de système de site.  
