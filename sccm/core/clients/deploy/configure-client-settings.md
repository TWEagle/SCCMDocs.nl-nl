---
title: "Configurer les paramètres client | Microsoft Docs"
description: "Sélectionnez les paramètres client dans System Center Configuration Manager."
ms.custom: na
ms.date: 04/23/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: configmgr-client
ms.tgt_pltfrm: na
ms.topic: get-started-article
ms.assetid: 95e9858a-bad4-4651-9e61-2e31dc5050fa
caps.latest.revision: "5"
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.openlocfilehash: 478d562bfb7fdb3921a4278741ff096e81e6092a
ms.sourcegitcommit: 51fc48fb023f1e8d995c6c4eacfda7dbec4d0b2f
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/07/2017
---
# <a name="how-to-configure-client-settings-in-system-center-configuration-manager"></a>Guide pratique pour configurer les paramètres client dans System Center Configuration Manager

*S’applique à : System Center Configuration Manager (Current Branch)*

Vous gérez tous les paramètres client dans System Center Configuration Manager depuis **Administration** > **Paramètres client**. Modifiez les paramètres par défaut lorsque vous souhaitez configurer des paramètres pour tous les utilisateurs et appareils de la hiérarchie ne disposant pas de paramètres personnalisés. Si vous souhaitez appliquer différents paramètres à certains utilisateurs ou appareils, créez des paramètres personnalisés et déployez-les vers les regroupements.  

Pour plus d’informations sur chaque paramètre client, consultez [À propos des paramètres client dans System Center Configuration Manager](../../../core/clients/deploy/about-client-settings.md).

> [!NOTE]  
>  Vous pouvez également utiliser des éléments de configuration pour gérer des clients afin d'évaluer, de suivre et de corriger la conformité de la configuration des appareils. Pour plus d’informations, consultez [Garantir la conformité des appareils avec System Center Configuration Manager](../../../compliance/understand/ensure-device-compliance.md).  

##  <a name="configure-the-default-client-settings"></a>Configurer les paramètres client par défaut    

1.  Dans la console Configuration Manager, choisissez **Administration** > **Paramètres client** > **Paramètres client par défaut**.  

3.  Sous l’onglet **Accueil**, choisissez **Propriétés**.  

4.  Consultez et configurez les paramètres client pour chaque groupe de paramètres dans le volet de navigation.  

 Les ordinateurs client sont configurés avec ces paramètres lorsqu'ils téléchargent la stratégie client. Pour lancer une récupération de stratégie pour un seul client, consultez [Lancer une récupération de stratégie pour un client Configuration Manager](../../../core/clients/manage/manage-clients.md#BKMK_PolicyRetrieval) dans [Comment gérer les clients dans System Center Configuration Manager](../../../core/clients/manage/manage-clients.md).  

##  <a name="create-and-deploy-custom-client-settings"></a>Créer et déployer des paramètres client personnalisés  
Lorsque vous déployez ces paramètres personnalisés, ceux-ci remplacent les paramètres client par défaut. Avant de débuter cette procédure, assurez-vous que vous disposez d'un regroupement qui contient les utilisateurs ou les appareils qui nécessitent ces paramètres client personnalisés.  

1.  Dans la console Configuration Manager, cliquez sur **Administration** > **Paramètres client**.  

3.  Sous l’onglet **Accueil**, dans le groupe **Créer**, choisissez **Créer des paramètres client personnalisés**, puis choisissez une des deux options suivantes :  

    -   **Créer des paramètres d'appareil client personnalisés**  

    -   **Créer des paramètres utilisateur client personnalisés**  

4.  Spécifiez un nom et une description de l’option.  

5.  Cochez une ou plusieurs des cases qui affichent un groupe de paramètres.  

6.  Choisissez chaque groupe de paramètres dans le volet de navigation et configurez les paramètres disponibles, puis cliquez sur **OK**.   

8.  Sélectionnez le paramètre client personnalisé que vous avez créé. Sous l’onglet **Accueil**, dans le groupe **Paramètres client**, choisissez **Déployer**.  

9. Dans la boîte de dialogue **Sélectionner un regroupement**, sélectionnez le regroupement approprié, puis choisissez **OK**. Vous pouvez vérifier le regroupement sélectionné en cliquant sur l'onglet **Déploiements** du volet d'informations.  

10. Consultez l'ordre du paramètre client personnalisé que vous venez de créer. Lorsque vous disposez de plusieurs paramètres client personnalisés, ceux-ci sont appliqués en fonction de leur numéro. En cas de conflit, le paramètre dont le numéro d'ordre est le plus petit remplace les autres paramètres. Pour changer le numéro d’ordre, sous l’onglet **Accueil**, dans le groupe **Paramètres client**, cliquez sur **Déplacer l’élément vers le haut** ou **Déplacer l’élément vers le bas**.  

 Les ordinateurs client sont configurés avec ces paramètres lorsqu'ils téléchargent la stratégie client. Pour lancer une récupération de stratégie pour un seul client, consultez [Lancer une récupération de stratégie pour un client Configuration Manager](../../../core/clients/manage/manage-clients.md#BKMK_PolicyRetrieval) dans [Comment gérer les clients dans System Center Configuration Manager](../../../core/clients/manage/manage-clients.md).  

##  <a name="view-client-settings"></a>Afficher les paramètres client  
 Lorsque plusieurs paramètres client sont déployés sur le même appareil, utilisateur ou groupe d'utilisateurs, la définition des priorités et la combinaison des paramètres peuvent être complexes. Pour afficher les paramètres client :  

1.  Dans la console Configuration Manager, choisissez **Ressources et Conformité** > **Appareils** > **Utilisateurs** ou **Regroupements d’utilisateurs**.  

3.  Sélectionnez un appareil, un utilisateur ou un groupe d'utilisateurs, puis dans le groupe **Paramètres client** , sélectionnez **Paramètres résultants du client**.  

4.  Sélectionnez un paramètre client dans le volet gauche pour afficher les paramètres. Dans cette vue, les paramètres sont en lecture seule. 

    > [!NOTE]  
    >  Pour afficher les paramètres client, vous devez disposer d’un accès en lecture aux paramètres client.  

    