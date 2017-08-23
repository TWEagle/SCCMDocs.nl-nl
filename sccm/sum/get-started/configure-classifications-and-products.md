---
title: "Configurer les classifications et les produits à synchroniser | Microsoft Docs"
description: "Suivez ces étapes pour configurer les classifications et les produits à synchroniser dans la console Configuration Manager."
keywords: 
author: dougeby
ms.author: dougeby
manager: angrobe
ms.date: 10/06/2016
ms.topic: article
ms.prod: configuration-manager
ms.service: 
ms.technology: configmgr-sum
ms.assetid: 5ddde4e6-d553-4182-b752-6bc8b4a26745
ms.openlocfilehash: 2da61e6e06850b36543b9fd41bd9a7d2368006fb
ms.sourcegitcommit: 51fc48fb023f1e8d995c6c4eacfda7dbec4d0b2f
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/07/2017
---
#  <a name="configure-classifications-and-products-to-synchronize"></a>Configurer les classifications et les produits à synchroniser  

*S’applique à : System Center Configuration Manager (Current Branch)*


> [!NOTE]  
>  Utilisez la procédure de cette section uniquement sur le site de niveau supérieur.  

 Les métadonnées des mises à jour logicielles sont récupérées au cours du processus de synchronisation dans Configuration Manager selon les paramètres que vous spécifiez dans les propriétés du composant du point de mise à jour logicielle. Une fois que vous avez synchronisé les mises à jour logicielles pour la première fois, ou lorsque de nouveaux produits et classifications sont disponibles, vous devez accéder aux propriétés pour sélectionner les nouveaux éléments. Pour configurer des classifications et des produits à synchroniser, procédez comme suit.  

#### <a name="to-configure-classifications-and-products-to-synchronize"></a>Pour configurer des classifications et des produits à synchroniser  

1.  Dans la console **Configuration Manager**, accédez à **Administration** > **Configuration de site** > **Sites**.

2. Sélectionnez le site d’administration centrale ou le site principal autonome.  

3.  Sur l'onglet **Accueil** dans le groupe **Paramètres** , cliquez sur **Configurer les composants de site**, puis cliquez sur **Point de mise à jour logicielle**.

4.  Sous l'onglet **Classifications** , spécifiez les classifications de mise à jour logicielle pour lesquelles vous souhaitez synchroniser les mises à jour logicielles.  

    > [!NOTE]  
    >  Chaque mise à jour logicielle fait partie d'une classification particulière qui permet d'organiser les différents types de mises à jour. Pendant le processus de synchronisation, les métadonnées des mises à jour logicielles pour les classifications spécifiées sont synchronisées. Configuration Manager vous permet de synchroniser les mises à jour logicielles avec les classifications de mise à jour suivantes :  
    >   
    > - **Mises à jour critiques** : spécifie des mises à jour distribuées en grand nombre, répondant à un problème spécifique qui concerne un bogue critique non lié à la sécurité.  
    > - **Mises à jour de définitions** : spécifie des mises à jour pour des virus ou d’autres fichiers de définition.  
    > - **Feature Packs** : spécifie de nouvelles fonctionnalités de produit, distribuées en dehors d’une version de produit et incluses généralement dans la version complète suivante du produit.  
    > - **Mises à jour de sécurité** : spécifie des mises à jour distribuées en grand nombre, répondant à un problème de sécurité spécifique à un produit.  
    > - **Service Packs** : spécifie des ensembles cumulés de correctifs rattachés à une application. Ces correctifs sont notamment des mises à jour de sécurité, des mises à jour critiques, des mises à jour logicielles, etc.  
    > - **Outils** : spécifie des utilitaires ou des fonctionnalités permettant d’effectuer une ou plusieurs tâches.  
    > - **Correctifs cumulatifs** : spécifie des ensembles cumulés de correctifs, assemblés pour faciliter leur déploiement. Ces correctifs peuvent comprendre des mises à jour de sécurité, des mises à jour critiques, des mises à jour, etc. Les correctifs cumulatifs concernent généralement un domaine particulier, tel que la sécurité ou un composant de produit.  
    > - **Mises à jour** : spécifie des mises à jour d’une application ou d’un fichier déjà installé.  
    > - **Mises à niveau** : spécifie des mises à niveau de fonctions et fonctionnalités Windows 10. Vos sites et points de mise à jour logicielle doivent exécuter au moins WSUS 4.0 avec le [correctif 3095113](https://support.microsoft.com/kb/3095113) pour obtenir la classification de **mise à niveau**.    
    >       

    > [!NOTE]    
    > À compter de Configuration Manager version 1706, vous pouvez également cocher la case **Inclure les mises à jour du microprogramme et des pilotes Microsoft Surface** pour synchroniser les pilotes Microsoft Surface. Tous les points de mise à jour logicielle doivent exécuter Windows Server 2016 pour synchroniser correctement les pilotes Surface.     
    >    
    > Cette fonctionnalité est en version préliminaire. Des fonctionnalités en préversion sont incluses dans le produit à des fins de test anticipé en environnement de production, mais ne doivent pas être considérées comme prêtes pour une utilisation en production. Vous devez activer cette fonctionnalité pour qu’elle soit disponible. Pour plus d’informations, consultez [Utiliser des fonctionnalités de préversions de mises à jour](https://docs.microsoft.com/sccm/core/servers/manage/install-in-console-updates#bkmk_prerelease).

5.  Sous l'onglet **Produits** , spécifiez les produits pour lesquels vous souhaitez synchroniser les mises à jour logicielles, puis cliquez sur **Fermer**.  

    > [!NOTE]  
    >  Les métadonnées de chaque mise à jour logicielle définissent les produits auxquels elles s'appliquent. Un produit est une édition spécifique d’un système d’exploitation ou d’une application (par exemple, Windows Server 2012). Une famille de produits est le système de d'exploitation ou l'application de base d'où sont issus les produits individuels. Par exemple, Windows est une famille de produits dont Windows Server 2012 fait partie. Vous pouvez spécifier une famille de produits ou des produits distincts au sein d'une famille de produits. Plus le nombre de produits que vous sélectionnez est important, plus la durée de synchronisation des mises à jour logicielles sera longue.  
    >   
    >  Quand des mises à jour logicielles s’appliquent à plusieurs produits et qu’au moins un de ces produits a été sélectionné pour une synchronisation, tous les autres produits apparaissent dans la console Configuration Manager, même s’ils n’ont pas été sélectionnés. Par exemple, si Windows Server 2012 est le seul système d’exploitation que vous avez sélectionné et qu’une mise à jour logicielle s’applique à Windows 8 et à Windows Server 2012, ces deux produits apparaîtront dans la console Configuration Manager.  

    > [!IMPORTANT]  
    >  Configuration Manager stocke une liste de produits et de familles de produits que vous pouvez choisir quand vous installez le point de mise à jour logicielle pour la première fois. Tant que les mises à jour logicielles ne sont pas effectuées, les produits et familles de produits publiés après la publication de Configuration Manager risquent de ne pas pouvoir être sélectionnés. La synchronisation permet de mettre à jour la liste des produits et des familles de produits pouvant être sélectionnés.  

## <a name="next-steps"></a>Étapes suivantes
Démarrez la synchronisation des mises à jour logicielles pour récupérer les mises à jour logicielles en fonction des nouveaux critères. Pour plus d’informations, consultez [Synchroniser les mises à jour logicielles](synchronize-software-updates.md).
