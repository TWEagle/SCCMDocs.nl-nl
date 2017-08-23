---
title: "Utiliser un média de démarrage pour déployer Windows sur le réseau | Microsoft Docs"
description: "Utilisez des déploiements de médias de démarrage dans System Center Configuration Manager pour déployer le système d’exploitation au démarrage de l’ordinateur de destination."
ms.custom: na
ms.date: 6/16/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: configmgr-osd
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 999b5409-7e72-48d2-8554-4d44427ce383
caps.latest.revision: "5"
author: mattbriggs
ms.author: mattbriggs
manager: angrobe
ms.openlocfilehash: 9b20e5e2a66d92038033e816e6fc701581c48a7f
ms.sourcegitcommit: 51fc48fb023f1e8d995c6c4eacfda7dbec4d0b2f
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/07/2017
---
# <a name="use-bootable-media-to-deploy-windows-over-the-network-with-system-center-configuration-manager"></a>Utiliser un média de démarrage pour déployer Windows sur le réseau avec System Center Configuration Manager

*S’applique à : System Center Configuration Manager (Current Branch)*

Vous pouvez déployer le système d’exploitation au démarrage de l’ordinateur de destination avec un déploiement de média de démarrage. Le média contient un pointeur vers la séquence de tâches, l’image de système d’exploitation et les autres contenus requis à partir du réseau. Lorsque l’ordinateur de destination démarre, il récupère les éléments référencés dans le pointeur. Avec le média de démarrage vide de contenu, vous pouvez mettre à jour la cible sans avoir à la remplacer sur le média.

Vous pouvez déployer des systèmes d’exploitation sur le réseau en utilisant la multidiffusion dans les scénarios de déploiement de système d’exploitation suivants :

-   [Actualiser un ordinateur existant avec une nouvelle version de Windows](refresh-an-existing-computer-with-a-new-version-of-windows.md)

-   [Installer une nouvelle version de Windows sur un nouvel ordinateur (système nu)](install-new-windows-version-new-computer-bare-metal.md)  

-   [Remplacer un ordinateur existant et transférer des paramètres](replace-an-existing-computer-and-transfer-settings.md)  

Effectuez les étapes de l’un des scénarios de déploiement de système d’exploitation, puis utilisez les sections suivantes pour utiliser un média de démarrage pour déployer le système d’exploitation.  

## <a name="configure-deployment-settings"></a>Configurer les paramètres de déploiement  
Quand vous utilisez un média de démarrage pour démarrer le processus de déploiement de système d’exploitation, configurez le déploiement pour rendre le système d’exploitation accessible au média. Vous pouvez configurer cette option dans la page **Paramètres de déploiement** de l’Assistant Déploiement logiciel ou sous l’onglet **Paramètres de déploiement** dans les propriétés du déploiement. Pour le paramètre **Rendre disponible aux éléments suivants** , sélectionnez l’une des options suivantes :

-   Clients, média et environnement PXE Configuration Manager

-   Média et environnement PXE uniquement

-   Média et environnement PXE uniquement (masqué)

## <a name="create-the-bootable-media"></a>Créer le média de démarrage
Vous pouvez spécifier si le média de démarrage est un disque mémoire flash USB ou un ensemble CD/DVD. L’ordinateur qui démarre le média doit prendre en charge l’option que vous choisissez comme lecteur de démarrage. Pour plus d’informations, consultez [Créer un média de démarrage](create-bootable-media.md).  

##  <a name="BKMK_Deploy"></a> Installer le système d’exploitation à partir d’un média de démarrage  
Insérez le média de démarrage dans un lecteur de démarrage sur l’ordinateur, puis mettez-le sous tension pour installer le système d’exploitation.
