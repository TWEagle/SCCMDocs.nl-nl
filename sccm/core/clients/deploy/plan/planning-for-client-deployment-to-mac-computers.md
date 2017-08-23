---
title: "Planification du déploiement du client sur des ordinateurs Mac | Microsoft Docs"
description: "Planifiez le déploiement de clients sur des ordinateurs Mac dans System Center Configuration Manager."
ms.custom: na
ms.date: 04/23/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: configmgr-client
ms.tgt_pltfrm: na
ms.topic: get-started-article
ms.assetid: 8d15ae3f-de42-461f-a907-c43873da22d2
caps.latest.revision: "6"
caps.handback.revision: "0"
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.openlocfilehash: 75bddb41d4d1cf209fa7595c52b5a6aa831ba3dd
ms.sourcegitcommit: 51fc48fb023f1e8d995c6c4eacfda7dbec4d0b2f
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/07/2017
---
# <a name="planning-for-client-deployment-to-mac-computers-in-system-center-configuration-manager"></a>Planification du déploiement du client pour les ordinateurs Mac dans System Center Configuration Manager

*S’applique à : System Center Configuration Manager (Current Branch)*

Vous pouvez installer le client Configuration Manager sur des ordinateurs Mac qui exécutent le système d’exploitation Mac OS X et utilisent les fonctionnalités de gestion suivantes :  

-   **Inventaire matériel**  

     Vous pouvez utiliser l’inventaire matériel de Configuration Manager pour collecter des informations sur le matériel et les applications installées sur des ordinateurs Mac. Consultez ensuite ces informations dans l’Explorateur de ressources dans la console Configuration Manager et utilisez-les pour créer des regroupements, des requêtes et des rapports. Pour plus d’informations, consultez [Guide pratique pour utiliser l’Explorateur de ressources pour afficher l’inventaire matériel dans System Center Configuration Manager](../../../../core/clients/manage/inventory/use-resource-explorer-to-view-hardware-inventory.md).  

     Configuration Manager collecte les informations matérielles suivantes auprès des ordinateurs Mac :  

    -   Processeur  

    -   Système informatique  

    -   Lecteur de disque  

    -   Partition de disque  

    -   Carte réseau  

    -   Système d'exploitation  

    -   Service  

    -   Processus  

    -   Logiciel installé  

    -   Produit système informatique  

    -   Contrôleur USB  

    -   Périphérique USB  

    -   Lecteur de CD-ROM  

    -   Contrôleur vidéo  

    -   Moniteur du Bureau  

    -   Batterie portable  

    -   Mémoire physique  

    -   Imprimante  

    > [!IMPORTANT]  
    >  Vous ne pouvez pas étendre les informations matérielles collectées à partir d'ordinateurs Mac pendant un inventaire matériel.  

-   **Paramètres de compatibilité**  

     Vous pouvez utiliser les paramètres de compatibilité de Configuration Manager pour afficher la compatibilité des paramètres de préférence (.plist) Mac OS X et les corriger. Par exemple, vous pouvez appliquer des paramètres pour la page d'accueil du navigateur web Safari ou veiller à ce que le pare-feu Apple soit activé. Vous pouvez également utiliser des scripts Shell pour surveiller et corriger des paramètres dans MAC OS X.  

-   **Gestion des applications**  

     Configuration Manager peut déployer des logiciels sur les ordinateurs Mac. Vous pouvez déployer les formats logiciels suivants sur les ordinateurs Mac :  

    -   Image disque Apple (.DMG)  

    -   Fichier métapaquet (.MPKG)  

    -   Paquet d'installation Mac OS X (.PKG)  

    -   Application Mac OS X (.APP)  

 Quand vous installez le client Configuration Manager sur des ordinateurs Mac, vous ne pouvez pas utiliser les fonctionnalités de gestion suivantes prises en charge par le client Configuration Manager sur les ordinateurs Windows :  

-   Installation poussée du client  

-   Déploiement du système d'exploitation  

-   Mises à jour logicielles  

    > [!NOTE]  
    >  Vous pouvez utiliser la gestion des applications Configuration Manager pour déployer des mises à jour logicielles Mac OS X requises sur les ordinateurs Mac. En outre, vous pouvez utiliser des paramètres de conformité pour vous assurer que les ordinateurs disposent des mises à jour logicielles requises.  

-   Fenêtres de maintenance  

-   Contrôle à distance  

-   Gestion de l'alimentation  

-   Vérification et correction de l'état du client  

 Pour plus d’informations sur la manière d’installer et de configurer le client Mac Configuration Manager, consultez [Guide pratique pour déployer des clients sur des Mac dans System Center Configuration Manager](../../../../core/clients/deploy/deploy-clients-to-macs.md).
