---
title: "Fonctionnalités de Technical Preview 1602 Configuration Manager"
description: "Découvrez les fonctionnalités disponibles dans la version d’évaluation technique 1602 pour System Center Configuration Manager."
ms.custom: na
ms.date: 01/23/2017
ms.prod: configuration-manager
ms.technology: configmgr-other
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 1b9265d1-b461-47f8-b7ef-885da0fdd969
caps.latest.revision: "6"
author: Brenduns
ms.author: brenduns
manager: angrobe
robots: noindex,nofollow
ms.openlocfilehash: 2354f885aaf69683004ad78f0e1978e78fee9145
ms.sourcegitcommit: 51fc48fb023f1e8d995c6c4eacfda7dbec4d0b2f
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/07/2017
---
# <a name="capabilities-in-technical-preview-1602-for-system-center-configuration-manager"></a>Fonctionnalités de la version d’évaluation technique 1602 pour System Center Configuration Manager

*S’applique à : System Center Configuration Manager (version d’évaluation technique)*

Cet article présente les fonctionnalités qui sont disponibles dans la version d’évaluation technique 1602 pour System Center Configuration Manager. Vous pouvez installer cette version pour mettre à jour et ajouter de nouvelles fonctionnalités à votre site de version d’évaluation technique Configuration Manager. Avant d’installer cette version d’évaluation technique, passez en revue la rubrique de présentation, [Technical Preview pour System Center Configuration Manager](../../core/get-started/technical-preview.md), pour vous familiariser avec les conditions générales et les limitations d’utilisation d’une version d’évaluation technique, la mise à jour entre les versions et l’envoi de commentaires sur les fonctionnalités dans une version d’évaluation technique.  

 Vous trouverez ci-dessous les nouvelles fonctionnalités propres à cette version.  

##  <a name="BKMK_MDM"></a> Améliorations apportées à la gestion des appareils mobiles  

### <a name="ios-activation-lock"></a>Verrou d’activation iOS  
 System Center Configuration Manager peut vous aider à gérer le verrou d’activation iOS, fonctionnalité de l’application Rechercher mon iPhone pour les appareils iOS 7.1 et versions ultérieures. Le verrou d'activation est activé automatiquement quand l'application Rechercher mon iPhone est utilisée sur un appareil. Une fois qu’il est activé, l’ID et le mot de passe Apple de l’utilisateur doivent être entrés pour pouvoir :  

-   Désactiver Rechercher mon iPhone  

-   Effacer l'appareil  

-   Réactiver l'appareil  

 Configuration Manager peut demander l’état du verrou d’activation des appareils supervisés et non supervisés qui exécutent iOS 7.1 et versions ultérieures. Pour les appareils supervisés, Intune peut récupérer le code de contournement du verrou d’activation et l’émettre directement à l’appareil.  

 Pour plus d’informations, consultez [Aider à protéger les appareils iOS avec le contournement du verrou d’activation pour Configuration Manager](/sccm/mdm/deploy-use/manage-ios-activation-lock)  

##  <a name="BKMK_SC1601"></a> Améliorations apportées au Centre logiciel dans la version 1602  

### <a name="refresh-pc-machine-and-user-policy-from-software-center"></a>Actualiser la stratégie ordinateur et utilisateur du PC à partir du Centre logiciel  
 Une nouvelle option, **Stratégie de synchronisation**, a été ajoutée à la page **Options** > **Maintenance de l’ordinateur** du Centre logiciel. Elle force le PC à actualiser sa stratégie ordinateur et utilisateur Configuration Manager.  

##  <a name="BKMK_Win10Servicing"></a> Améliorations apportées à la maintenance de Windows 10  
 Dans Technical Preview 1602, nous avons ajouté les améliorations suivantes à la Maintenance de Windows 10 :  

-   Nouvelles options de filtre pour les plans de maintenance.  Vous pouvez désormais filtrer par **Langue**, **Obligatoire** et **Titre**. Seules les mises à jour qui remplissent les critères spécifiés sont ajoutées au déploiement associé.  

-   Quand vous sélectionnez la classification **Mises à niveau** pour la synchronisation des mises à jour logicielles, une boîte de dialogue d’avertissement s’affiche pour vous informer que le [correctif 3095113](https://support.microsoft.com/kb/3095113) WSUS est nécessaire pour synchroniser correctement les mises à jour logicielles et pour que la maintenance de Windows 10 fonctionne correctement.  À partir de la boîte de dialogue, vous pouvez accéder à l’article de la Base de connaissances pour obtenir le correctif logiciel.  

-   Les mises à niveau Windows 10 disponibles sont maintenant affichées uniquement dans le nœud **Maintenance de Windows 10** \ **Toutes les mises à jour Windows 10** de la console Configuration Manager. Ces mises à jour n’apparaissent plus dans le nœud **Mises à jour logicielles** \ **Toutes les mises à jour logicielles**.  

-   Les utilisateurs finaux qui démarrent un package de mise à niveau Windows 10 sont informés qu’ils vont mettre à niveau leur système d’exploitation.  
