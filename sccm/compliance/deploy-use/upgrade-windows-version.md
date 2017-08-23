---
title: "Mettre à niveau des appareils Windows vers une autre version avec Configuration Manager | Microsoft Docs"
description: "Mettez automatiquement à niveau les appareils qui exécutent Windows 10 Desktop, Windows 10 Mobile ou Windows 10 Holographique vers une autre édition avec Configuration Manager."
ms.custom: na
ms.date: 07/31/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: b0c9db74-841e-46eb-8924-957cde968bf7
caps.latest.revision: "8"
caps.handback.revision: "0"
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.openlocfilehash: cd8c644d07dab0010dc211df8ce4f2dc6e1fa7ae
ms.sourcegitcommit: 51fc48fb023f1e8d995c6c4eacfda7dbec4d0b2f
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/07/2017
---
# <a name="upgrade-windows-devices-with-the-edition-upgrade-policy-in-system-center-configuration-manager"></a>Mettre à niveau des appareils Windows avec la stratégie de mise à niveau d’édition dans System Center Configuration Manager

*S’applique à : System Center Configuration Manager (Current Branch)*


La **stratégie de mise à niveau d’édition** de System Center Configuration Manager vous permet de mettre automatiquement à niveau les appareils qui exécutent une des versions suivantes de Windows 10 vers une autre édition :

- Windows 10 Desktop
- Windows 10 Mobile
<!-- - Windows 10 Holographic -->

Les chemins de mise à niveau suivants sont pris en charge :

- De Windows 10 Professionnel vers Windows 10 Entreprise
- De Windows 10 Famille vers Windows 10 Éducation
- De Windows 10 Mobile vers Windows 10 Mobile Entreprise
<!-- - From Windows 10 Holographic Pro to Windows 10 Holographic Enterprise -->

Les appareils doivent être inscrit dans Microsoft Intune ou exécuter le logiciel client Configuration Manager. Cette stratégie n’est actuellement pas compatible avec les PC gérés par gestion MDM locale.

## <a name="before-you-start"></a>Avant de commencer  
 Avant de commencer à mettre à niveau des appareils vers la dernière version, vous avez besoin d’un des éléments suivants :  

-   Une clé de produit valide pour installer la nouvelle version de Windows sur tous les appareils que vous ciblez avec la stratégie (pour les systèmes d’exploitation d’ordinateur)  

-   Un fichier de licence de Microsoft, qui contient les informations de licence pour installer la nouvelle version de Windows sur tous les appareils que vous ciblez avec la stratégie (pour Windows 10 Mobile<!-- and Windows 10 Holographic-->).

- Pour créer et déployer ce type de stratégie, le rôle de sécurité **Administrateur complet** de Configuration Manager doit vous avoir été affecté.

## <a name="configure-the-edition-upgrade-policy"></a>Configurer la stratégie de mise à niveau d’édition  

1.  Dans la console Configuration Manager, cliquez sur **Ressources et Conformité** > **Paramètres de compatibilité** > **Mise à niveau de l'édition Windows 10**.  

3.  Sous l’onglet **Accueil** , dans le groupe **Créer** , cliquez sur **Créer une stratégie de mise à niveau d’édition**.  

4.  Cliquez sur **Créer une stratégie**.  

5.  Dans la page **Général** de l’ **Assistant Création de stratégie de mise à niveau d’édition**, spécifiez les informations suivantes :  

    -   **Nom** : entrez un nom pour la stratégie de mise à niveau d’édition.  

    -   **Description** (facultatif) : si vous le souhaitez, entrez une description pour la stratégie qui vous permet de l’identifier dans la console Intune.  

    -   **Référence pour mettre à niveau l’appareil vers** : dans la liste déroulante, sélectionnez la version de Windows 10 Desktop, <!-- Windows 10 Holographic,--> ou Windows 10 Mobile vers laquelle vous voulez mettre à niveau les appareils ciblés.  

    -   **Informations sur la licence** : sélectionnez une des options suivantes :  

        -   **Clé de produit** : entrez une clé de produit Windows 10 valide qui sera utilisée pour mettre à niveau les appareils que vous ciblez et qui exécutent des systèmes d’exploitation Windows 10 Desktop.  

            > [!NOTE]  
            >  Une fois que vous avez créé une stratégie contenant une clé de produit, vous ne pouvez plus modifier la clé de produit. La raison en est que la clé est masquée pour des raisons de sécurité. Pour changer la clé de produit, vous devez entrer à nouveau toute la clé.  

        -   **Fichier de licence** : cliquez sur **Parcourir** pour sélectionner un fichier de licence valide au format XML. Ce fichier sert à mettre à niveau les appareils ciblés qui exécutent les systèmes d’exploitation <!--Windows 10 Holographic and -->Windows 10 Mobile.  

6.  Effectuez toutes les étapes de l'Assistant.  

La nouvelle stratégie figure dans le nœud **Mise à niveau de l’édition de Windows 10** de l’espace de travail **Ressources et conformité** .  

## <a name="deploy-the-edition-upgrade-policy"></a>Déployer la stratégie de mise à niveau d’édition  

1.  Dans la console Configuration Manager, cliquez sur **Ressources et Conformité** > **Paramètres de compatibilité** > **Mise à niveau de l'édition Windows 10**.  

3.  Sélectionnez la stratégie de mise à niveau d’édition de Windows 10 que vous voulez déployer puis, dans l’onglet **Accueil** , dans le groupe **Déploiement** , cliquez sur **Déployer**.  

4.  Dans la boîte de dialogue **Déployer la mise à niveau de l’édition Windows 10**, choisissez le regroupement sur lequel vous voulez déployer la stratégie et la planification selon laquelle la stratégie doit être évaluée, puis cliquez sur **OK**. Pour les PC gérés par le client Configuration Manager, vous devez déployer la stratégie sur un regroupement d’appareils. Pour les PC inscrits dans Intune, vous pouvez déployer la stratégie sur un regroupement d’utilisateurs ou d’appareils. 



## <a name="next-steps"></a>Étapes suivantes

Quand vous analysez le déploiement que vous venez de créer à partir du nœud **Déploiements** de l’espace de travail **Analyse**, vous pouvez recevoir des erreurs qui semblent indiquer l’échec du déploiement. Par exemple :
- **Ne s’applique pas à cet appareil**
- **Échec de la conversion du type de données**

Ces erreurs ne signifient pas que le déploiement a échoué. Vérifiez que la mise à niveau a réussi sur le PC ciblé.

Une fois que la stratégie atteint un PC Windows ciblé et qu’il est évalué, celui-ci est redémarré dans les deux heures suivantes pour appliquer la mise à niveau. Assurez-vous d’informer les utilisateurs sur lesquels vous déployez la stratégie ou planifiez l’exécution de la stratégie en dehors des heures de travail des utilisateurs.
