---
title: "Utiliser des fenêtres de maintenance | Microsoft Docs"
description: "Utilisez les regroupements et les fenêtres de maintenance pour gérer efficacement les clients dans System Center Configuration Manager."
ms.custom: na
ms.date: 02/22/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 4564ebcb-41a8-4eb0-afdb-2e1f0795cfa2
caps.latest.revision: "6"
caps.handback.revision: "0"
author: andredm7
ms.author: andredm
manager: angrobe
ms.openlocfilehash: fa67cf597c73bab47209c9b98539f97e174ae70b
ms.sourcegitcommit: 51fc48fb023f1e8d995c6c4eacfda7dbec4d0b2f
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/07/2017
---
# <a name="how-to-use-maintenance-windows-in-system-center-configuration-manager"></a>Comment utiliser les fenêtres de maintenance dans System Center Configuration Manager

*S’applique à : System Center Configuration Manager (Current Branch)*

Les fenêtres de maintenance vous permettent de définir une période de temps pendant laquelle des opérations Configuration Manager peuvent être effectuées sur un regroupement d’appareils. Vous pouvez utiliser les fenêtres de maintenance afin de vous assurer que les modifications apportées à la configuration client seront effectuées pendant des périodes qui n’affectent pas la productivité.  

 Les opérations suivantes prennent en charge les fenêtres de maintenance :  

-   Déploiements de logiciels  

-   Déploiements de mises à jour logicielles  

-   Déploiement et évaluation des paramètres de compatibilité  

-   Déploiements de système d'exploitation  

-   Déploiements de séquences de tâches  

 Configurez des fenêtres de maintenance avec une date de début, une heure de début et de fin, ainsi qu’une périodicité. La durée maximale d’une fenêtre doit être inférieure à 24 heures. Par défaut, les redémarrages de l’ordinateur dus à un déploiement ne sont pas autorisés à l’extérieur d’une fenêtre de maintenance, mais vous pouvez remplacer la valeur par défaut. Les fenêtres de maintenance affectent uniquement l’heure d’exécution du programme de déploiement ; les applications configurées pour un téléchargement et une exécution en local peuvent télécharger du contenu en dehors de la fenêtre.  

 Quand un ordinateur client est membre d’un regroupement d’appareils avec une fenêtre de maintenance, un programme de déploiement est exécuté uniquement si la durée d’exécution maximale autorisée ne dépasse pas la durée configurée pour la fenêtre. Si le programme ne peut pas être exécuté, une alerte est générée et le déploiement est de nouveau exécuté lors de la fenêtre de maintenance planifiée suivante qui dispose de suffisamment de temps.  

## <a name="using-multiple-maintenance-windows"></a>Utilisation de fenêtres de maintenance multiples  
 Quand un ordinateur client est membre de plusieurs regroupements d’appareils avec des fenêtres de maintenance, les règles suivantes s’appliquent :  

-   Si les fenêtres de maintenance ne se chevauchent pas, elles sont traitées comme deux fenêtres de maintenance indépendantes.  

-   Si les fenêtres de maintenance se chevauchent, elles sont traitées comme une seule fenêtre de maintenance englobant la période couverte par les deux fenêtres de maintenance. Par exemple, si deux fenêtres d’une heure chacune se chevauchent de 30 minutes, la durée effective de la fenêtre de maintenance est de 90 minutes.  

 Quand un utilisateur lance l’installation d’une application à partir du Centre logiciel, l’application est installée immédiatement, indépendamment de toute fenêtre de maintenance.  

 Si le déploiement d’une application avec un objectif **Obligatoire** atteint son échéance d’installation pendant les heures creuses configurées par un utilisateur dans le Centre logiciel, l’application est installée.  

### <a name="how-to-configure-maintenance-windows"></a>Comment configurer les fenêtres de maintenance  

1.  Dans la console Configuration Manager, choisissez **Ressources et Conformité**>  **Regroupements d’appareils**.  

3.  Dans la liste **Regroupements d’appareils**, sélectionnez un regroupement. Vous ne pouvez pas créer de fenêtres de maintenance pour le regroupement **Tous les systèmes** .  

4.  Sous l’onglet **Accueil**, dans le groupe **Propriétés**, choisissez **Propriétés**.  

5.  Dans l’onglet **Fenêtres de maintenance** de la boîte de dialogue **Propriétés de &lt;nom_regroupement\>**, choisissez l’icône **Nouveau**.  

6.  Renseignez la boîte de dialogue **&lt;nouveau\> Calendrier**.  

7.  Effectuez une sélection à partir de la liste déroulante **Appliquer cette planification à**.  

8.  Choisissez **OK**, puis fermez la boîte de dialogue **Propriétés de &lt;nom_regroupement\>**.  
