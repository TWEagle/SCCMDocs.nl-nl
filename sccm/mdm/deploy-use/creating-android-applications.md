---
title: "Créer des applications Android | Documents Microsoft"
description: "Examinez les éléments à prendre en compte quand vous créez et déployez des applications pour appareils Android."
ms.custom: na
ms.date: 07/31/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: configmgr-hybrid
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: e025c48c-1514-4ab7-836c-e0635aaa993a
caps.latest.revision: "6"
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.openlocfilehash: 3a89abc81cd70f4e499bf4e3087fd53915377c44
ms.sourcegitcommit: 51fc48fb023f1e8d995c6c4eacfda7dbec4d0b2f
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/07/2017
---
# <a name="create-android-applications-with-system-center-configuration-manager"></a>Créer des applications Android avec System Center Configuration Manager

*S’applique à : System Center Configuration Manager (Current Branch)*

Une application System Center Configuration Manager a un ou plusieurs types de déploiement. Les types de déploiement comprennent les fichiers d’installation et les informations nécessaires pour déployer des logiciels sur un appareil. Le type de déploiement contient également des règles spécifiant à quel moment et selon quelle méthode le logiciel est déployé.  

 Vous pouvez créer des applications à l'aide des méthodes suivantes :  

-   Créer automatiquement les types d'application et de déploiement en lisant les fichiers d'installation de l'application.  
-   Créer manuellement l'application, puis ajouter des types de déploiement ultérieurement.  
-   Importer une application à partir d’un fichier.  

Pour connaître les étapes requises pour créer des types de déploiement et applications Configuration Manager, voir [Démarrer l’Assistant Création d’une application](../../apps/deploy-use/create-applications.md#start-the-create-application-wizard). De plus, gardez à l’esprit les considérations suivantes quand vous créez et déployez des applications pour des appareils Android.  

## <a name="general-considerations-for-android-apps"></a>Éléments généraux à prendre en compte pour les applications Android

Configuration Manager prend en charge le déploiement des types d’applications suivants pour Android :

|Type d'appareil|Fichiers pris en charge|
|-|-|
|Android|.apk|

Les actions de déploiement suivantes sont prises en charge :

|Type d'appareil|Actions prises en charge|
|-|-|
|Android|**Disponible**, **Obligatoire** L’utilisateur doit donner son consentement pour l’installation et la désinstallation.|
|Android for Work | **Obligatoire** |

## <a name="approve-and-deploy-android-for-work-apps"></a>Approuver et déployer des applications Android for Work
En tant qu’administrateur de Configuration Manager, vous pouvez également approuver des applications sur le [site web Play for Work](https://play.google.com/work), et déployer ces applications sur des appareils Android for Work gérés.

Effectuez les étapes suivantes pour approuver des applications dans le magasin Play for Work, les synchroniser avec la console Configuration Manager et les déployer sur des appareils Android for Work gérés. Pour déployer des applications sur les profils professionnels des utilisateurs, vous devez approuver les applications dans Play for Work, puis les synchroniser avec la console Configuration Manager.

1. Ouvrez un navigateur et accédez à https://play.google.com/work.
2. Connectez-vous à l’aide du compte d’administrateur Google que vous avez lié à votre client Intune.
3. Recherchez les applications que vous souhaitez déployer dans votre environnement et choisissez **Approuver** pour chacune d’elles afin de les rendre disponibles pour Android for Work.
4. Dans la console Configuration Manager, accédez à **Administrateur** > **Vue d’ensemble** > **Services Cloud** > **Android for Work** et choisissez **Synchroniser**.
5. Patientez jusqu’à 10 minutes que les applications soient synchronisées, puis accédez à **Bibliothèque de logiciels** > **Vue d’ensemble** > **Gestion des applications** > **Informations de licence pour les applications du Store**.
6. Choisissez une application synchronisée à partir de Play for Work, puis choisissez **Créer une application**.
7. Terminez l’Assistant et choisissez **Fermer**.
8. Accédez à **Bibliothèque de logiciels** > **Vue d’ensemble** > **Gestion des applications** > **Applications**, choisissez une application Android for Work et déployez-la normalement.

Pour synchroniser des applications Play for Work avec Configuration Manager, vous devez d’abord approuver au moins une application sur le site web Play for Work.
