---
title: "Créer des éléments de configuration enfants | Microsoft Docs"
description: "Créez des éléments de configuration enfants dans System Center Configuration Manager."
ms.custom: na
ms.date: 10/06/2016
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 113984fa-6150-41a1-89ed-d2a83b979732
caps.latest.revision: "5"
caps.handback.revision: "0"
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.openlocfilehash: 33d4a2d5a09af74e1d76ac9b34a42b749f5bf7ef
ms.sourcegitcommit: 51fc48fb023f1e8d995c6c4eacfda7dbec4d0b2f
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/07/2017
---
# <a name="how-to-create-child-configuration-items-in-system-center-configuration-manager"></a>Guide pratique pour créer des éléments de configuration enfants dans System Center Configuration Manager

*S’applique à : System Center Configuration Manager (Current Branch)*

Dans System Center Configuration Manager, les éléments de configuration enfants sont des copies d’éléments de configuration qui maintiennent une relation avec l’élément de configuration d’origine dans le sens où ils héritent de la configuration d’origine de l’élément de configuration parent.  

Quand vous examinez les propriétés d’un élément de configuration enfant dans la console Configuration Manager, vous ne pouvez pas modifier les objets et les paramètres hérités avec leurs critères de validation. En revanche, il vous est possible d'ajouter, puis de modifier, d'autres critères de validation pour l'élément de configuration enfant. Vous pouvez aussi ajouter de nouveaux objets et paramètres à ce dernier.
La création et la modification d’un élément de configuration enfant vise généralement à redéfinir l’élément de configuration d’origine pour l’adapter aux besoins de votre entreprise.  

> [!NOTE]  
>  Vous pouvez uniquement créer des éléments de configuration enfants à partir d’éléments de configuration du type **Ordinateurs et serveurs Windows (personnalisés)**.  

## <a name="to-create-a-child-configuration-item"></a>Pour créer un élément de configuration enfant  

1.  Dans la console Configuration Manager, cliquez sur **Ressources et Conformité** > **Paramètres de compatibilité** > **Éléments de configuration**.  

3.  Dans la liste **Éléments de configuration** , sélectionnez l’élément de configuration pour lequel vous souhaitez créer un élément de configuration enfant, puis sous l’onglet **Accueil** , dans le groupe **Élément de configuration** , cliquez sur **Créer un élément de configuration enfant**.  

4.  Sur la page **Général** de l' **Assistant Création d'élément de configuration enfant**, vous pouvez choisir une révision spécifique de l'élément de configuration parent à utiliser pour créer l'enfant. Les autres étapes de cet Assistant sont identiques à celles que vous utiliseriez pour créer un élément de configuration standard. Pour plus d’informations, consultez [Guide pratique pour créer des éléments de configuration personnalisés pour les ordinateurs et serveurs Windows](../../compliance/deploy-use/create-custom-configuration-items-for-windows-desktop-and-server-computers-managed-with-the-client.md).  

5.  Effectuez toutes les étapes de l'Assistant. Le nouvel élément de configuration enfant figure dans la liste **Éléments de configuration** .  
