---
title: "Gérer les applications iOS achetées en volume | Microsoft Docs"
description: "Déployez, gérez et suivez les licences d’applications que vous avez achetées via l’App Store iOS."
ms.custom: na
ms.date: 05/12/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: configmgr-hybrid
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 7c3b9316-247b-490b-a363-8f8553821579
caps.latest.revision: "18"
caps.handback.revision: "0"
author: mtillman
ms.author: mtillman
manager: angrobe
ms.openlocfilehash: ce706e938f558406044f7890c80bb7156c3b262b
ms.sourcegitcommit: 51fc48fb023f1e8d995c6c4eacfda7dbec4d0b2f
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/07/2017
---
# <a name="manage-volume-purchased-ios-apps-with-system-center-configuration-manager"></a>Gérer des applications iOS achetées en volume avec System Center Configuration Manager

*S’applique à : System Center Configuration Manager (Current Branch)*



 L’App Store iOS vous permet d’acheter plusieurs licences d’une application que vous souhaitez exécuter dans votre entreprise. Vous pouvez ainsi réduire les coûts d’administration liés au suivi de plusieurs copies d’applications achetées.  

 System Center Configuration Manager facilite le déploiement et la gestion des applications iOS que vous avez achetées via le programme en important les informations de licence depuis l’App Store et en gérant le nombre de licences que vous utilisez.  

## <a name="manage-volume-purchased-apps-for-ios-devices"></a>Gérer les applications pour appareils iOS achetées en volume  
 Vous achetez plusieurs licences d’applications iOS via le Programme d’achat en volume (VPP) Apple. Vous devez alors configurer un compte Apple VPP sur le site web Apple et charger le jeton Apple VPP sur Configuration Manager, ce qui offre les possibilités suivantes :  

-   Synchronisation des informations sur les achats en volume avec Configuration Manager. 
 
- Synchronisation des applications du programme d’achat en volume pour les entreprises et du programme d’achat en volume pour l’éducation d’Apple.

- Association de plusieurs jetons de programme d’achat de volume Apple à Configuration Manager.

-   Affichage des applications achetées dans la console Configuration Manager.  

-   Déploiement et surveillance de ces applications, et suivi du nombre de licences utilisées pour chaque application.  

-   Si nécessaire, Configuration Manager peut vous permettre de récupérer des licences en désinstallant les applications achetées en volume que vous avez déployées.  

## <a name="before-you-start"></a>Avant de commencer  
 Avant de commencer, vous devez vous procurer un jeton VPP auprès d’Apple et le charger sur Configuration Manager.  

-   Si vous avez précédemment utilisé un jeton VPP avec un autre produit MDM dans votre compte Apple VPP existant, vous devez en générer un nouveau pour l’utiliser avec Configuration Manager.  
-   Chaque jeton est valide pendant un an.  
-   Par défaut, Configuration Manager se synchronise avec le service Apple VPP deux fois par jour pour vérifier que vos licences sont synchronisées avec Configuration Manager.  
      Seules les modifications apportées à vos licences sont synchronisées. Cependant, une synchronisation complète est assurée une fois tous les sept jours.  
      Quand vous choisissez **Synchroniser** pour effectuer une synchronisation manuelle, celle-ci est toujours complète.  
-   Si vous avez besoin de récupérer ou restaurer votre base de données Configuration Manager, nous vous recommandons d’effectuer une synchronisation manuelle après cette opération pour être certain que vos données de licence synchronisées sont à jour.  
-   De plus, vous devez avoir importé un certificat du service de notifications Push Apple (APNs) pour pouvoir gérer des appareils iOS, ce qui inclut le déploiement d’applications. Pour plus d’informations, consultez [Configurer la gestion des appareils iOS hybride](enroll-hybrid-ios-mac.md).  
-   Configuration Manager prend en charge l’ajout de 3000 jetons VPP maximum.

À partir de System Center Configuration Manager 1702, vous pouvez désormais déployer des applications sous licence sur des appareils ainsi que des utilisateurs. En fonction de la capacité des applications à prendre en charge les licences d’appareils, une licence appropriée sera réclamée lors du déploiement, comme suit :

|||||
|-|-|-|-|
|Version de Configuration Manager|L’application prend-elle en charge les licences d’appareil ?|Type de regroupement de déploiement|Licence demandée|
|Antérieure à 1702|Oui|utilisateur|Licence utilisateur|
|Antérieure à 1702|Non|utilisateur|Licence utilisateur|
|Antérieure à 1702|Oui|Appareil|Licence utilisateur|
|Antérieure à 1702|Non|Appareil|Licence utilisateur|
|1702 et versions ultérieures|Oui|utilisateur|Licence utilisateur|
|1702 et versions ultérieures|Non|utilisateur|Licence utilisateur|
|1702 et versions ultérieures|Oui|Appareil|Licence d’appareil|
|1702 et versions ultérieures|Non|Appareil|Licence utilisateur|

## <a name="step-1---to-get-and-upload-an-apple-vpp-token"></a>Étape 1 : obtenir et charger un jeton Apple VPP  

1.  Dans la console Configuration Manager, choisissez **Administration** > **Services cloud** > **Jetons du programme d’achat en volume (VPP) Apple**.   

3.  Sous l’onglet **Accueil**, dans le groupe **Jetons du programme d’achat en volume (VPP) Apple**, choisissez **Ajouter un jeton du programme d’achat en volume (VPP) Apple**.  

4.  Dans la page **Général** de l’Assistant **Ajouter un jeton du programme d’achat en volume (VPP) Apple**, configurez les éléments suivants :   

    -   **Nom** : attribuez un nom à ce jeton tel qu’il s’affichera dans la console Configuration Manager.  

    -   **Jeton** : choisissez **Parcourir** et le jeton VPP que vous avez téléchargé sur le site web Apple.  

         Choisissez le lien **See Apple VPP account** (Afficher le compte Apple VPP) et, si ce n’est déjà fait, inscrivez-vous à un programme d’achats en volume pour les entreprises ou l’enseignement. Une fois inscrit, téléchargez le jeton Apple VPP pour votre compte.  

    -   **Description** : si vous le souhaitez, entrez une description pour faciliter l’identification du jeton VPP dans la console Configuration Manager.  

    -   **Catégories attribuées pour améliorer la recherche et le filtrage** : si vous le souhaitez, vous pouvez attribuer des catégories au jeton VPP pour faciliter sa recherche dans la console Configuration Manager.  
    -   **ID Apple** : entrez l’ID de l’adresse électronique Apple associée au jeton VPP.
    -   **Type de jeton** : sélectionnez le type de jeton VPP que vous souhaitez utiliser. Vous pouvez choisir les types de jetons **Business** et **EDU**.

5.  Choisissez **Suivant**, puis terminez l’Assistant.  

À partir du nœud **Jetons du programme d’achat en volume (VPP) Apple**, vous pouvez maintenant consulter les informations sur le jeton Apple VPP et déterminer notamment quand ont eu lieu ses dernières mise à jour et synchronisation, ainsi que sa date d’expiration.

Vous pouvez à tout moment synchroniser entièrement les données détenues par Apple à l’aide de Configuration Manager en choisissant **Synchroniser** sous l’onglet **Accueil** dans le groupe **Synchroniser**.  

## <a name="step-2---deploy-a-volume-purchased-app"></a>Étape 2 : déployer une application achetée en volume  

1.  Dans la console Configuration Manager, choisissez **Bibliothèque de logiciels** > **Gestion des applications** > **Informations de licence pour les applications du Store**.  

3.  Choisissez l’application que vous voulez déployer puis, sous l’onglet **Accueil**, dans le groupe **Créer**, choisissez **Créer une application**.
L’application Configuration Manager qui est créée contient l’application du Windows Store pour Entreprises. Vous pouvez ensuite déployer et surveiller cette application comme n’importe quelle autre application Configuration Manager.

    > [!IMPORTANT]  
    > Vous devez choisir l’objectif de déploiement **Obligatoire**. Les installations disponibles ne sont pas prises en charge actuellement.

 Quand vous déployez l’application, une licence est utilisée par chaque utilisateur, ou pour les installations d’appareils, chaque appareil qui installe l’application.  Si vous ciblez un regroupement d’appareils avec une application prenant en charge les licences d’appareils, une licence d’appareil est demandée.  Si vous ciblez un regroupement d’appareils avec une application ne prenant pas en charge les licences d’appareils, une licence d’utilisateur est demandée. 

 Lorsque vous créez une application à partir du nœud **Informations de licence pour les applications du Windows Store**, l’application est associée à des licences provenant du jeton de l’application que vous avez sélectionnée.  Par exemple, vous pouvez afficher les deux versions de la même application dans le nœud. En effet, chaque version de l’application est associée à un jeton VPP Apple distinct.  Vous pouvez ensuite créer des applications à partir de chaque jeton et les déployer séparément.

 Pour récupérer une licence, vous devez créer un déploiement de l’application avec l’action de déploiement **Désinstaller**. Vous ne pouvez pas changer l’action de déploiement dans le déploiement d’origine. La licence est récupérée une fois l’application désinstallée.  

## <a name="step-3---monitor-ios-vpp-apps"></a>Étape 3 : surveiller les applications VPP iOS  
 Le nœud **Informations de licence pour les applications du Store** de l’espace de travail **Bibliothèque de logiciels** affiche des informations sur vos applications iOS achetées en volume. Celles-ci incluent le nombre total de licences qui vous appartiennent pour chaque application ainsi que le nombre de licences qui ont été déployées. En outre, la vue indique le jeton VPP auquel l’application est associée et le type du jeton

 Vous pouvez aussi surveiller l’utilisation des licences de toutes les applications VPP que vous avez achetées à l’aide du rapport **Applications du programme d’achat en volume (VPP) Apple pour iOS avec les nombres de licences**.  

 Ce rapport affiche le nom de chaque application, ainsi que le nombre total de licences achetées, le nombre de licences disponibles et d’autres informations.  

 Pour obtenir de l’aide sur l’exécution des rapports Configuration Manager, consultez [Génération de rapports dans System Center Configuration Manager](../../core/servers/manage/reporting.md).  
