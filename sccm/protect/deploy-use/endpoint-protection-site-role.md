---
title: "Créer un rôle de système de site de point Endpoint Protection | Microsoft Docs"
description: "Apprenez à configurer Endpoint Protection de façon à gérer la sécurité et les programmes malveillants sur les ordinateurs clients Configuration Manager."
defintion: 
definition: 
ms.custom: na
ms.date: 02/14/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: configmgr-other
ms.tgt_pltfrm: na
ms.topic: get-started-article
ms.assetid: 0a9dc0fe-a942-40a2-bab1-7eeee4d95380
caps.latest.revision: "21"
author: NathBarn
ms.author: nathbarn
manager: angrobe
ms.openlocfilehash: 6e717bcbe5ef8c3f2efa717d0cebb9e675e7c127
ms.sourcegitcommit: 51fc48fb023f1e8d995c6c4eacfda7dbec4d0b2f
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/07/2017
---
# <a name="create-an-endpoint-protection-point-site-system-role"></a>Créer un rôle de système de site de point Endpoint Protection

*S’applique à : System Center Configuration Manager (Current Branch)*

 Pour que vous puissiez utiliser Endpoint Protection, le rôle de système de site de point Endpoint Protection doit avoir été installé. Il doit être installé sur un seul serveur de système de site et en haut de la hiérarchie sur un site d'administration centrale ou un site principal autonome.

 Utilisez l’une des procédures suivantes selon que vous voulez installer un nouveau serveur de système de site pour Endpoint Protection ou utiliser un serveur de système de site existant :
 - [Installation sur un nouveau serveur de système de site](#new-site-system-server)
 - [Installation sur un serveur de système de site existant](#existing-site-system-server)

> [!IMPORTANT]
>  Quand vous installez un point Endpoint Protection, un client Endpoint Protection est installé sur le serveur hébergeant le point Endpoint Protection. Les analyses et les services sont désactivés sur ce client pour lui permettre de coexister avec une solution existante anti-programme malveillant installée sur le serveur. Si vous activez ultérieurement ce serveur pour confier la gestion à Endpoint Protection et que vous sélectionnez l’option de suppression de solution tierce anti-programme malveillant, le produit tiers n’est pas supprimé. Vous devez désinstaller ce produit manuellement.

## <a name="new-site-system-server"></a>Nouveau serveur de système de site

1.  Dans la console Configuration Manager, cliquez sur **Administration**.

2.  Dans l'espace de travail **Administration** , développez **Configuration du site**, puis cliquez sur **Serveurs et rôles de système de site**.

3.  Sur l'onglet **Accueil** , dans le groupe **Créer** , cliquez sur **Créer un serveur de système de site**.

4.  Sur la page **Général** , spécifiez les paramètres généraux du système de site, puis cliquez sur **Suivant**.

5.  Sur la page **Sélection du rôle système** , sélectionnez **Point Endpoint Protection** dans la liste des rôles disponibles, puis cliquez sur **Suivant**.

6.  Sur la page **Endpoint Protection** , sélectionnez la case à cocher **J'accepte les termes du contrat de licence Endpoint Protection** et cliquez sur **Suivant**.

    > [!IMPORTANT]
    >  Vous ne pouvez pas utiliser Endpoint Protection dans Configuration Manager, à moins que vous acceptiez les termes du contrat de licence.

7.  Dans la page **Cloud Protection Service**, sélectionnez le niveau d’information à envoyer à Microsoft pour aider au développement de nouvelles définitions, puis cliquez sur **Suivant**.

    > [!NOTE]
    >  Cette option configure les paramètres de Cloud Protection Service (anciennement Microsoft Active Protection Service ou MAPS) utilisés par défaut. Vous pouvez ensuite configurer des paramètres personnalisés pour chaque stratégie anti-programme malveillant que vous créez. Rejoignez Cloud Protection Service pour contribuer à renforcer la protection de vos ordinateurs en fournissant à Microsoft des exemples de programmes malveillants et permettre ainsi de tenir à jour les définitions anti-programme malveillant. De plus, quand vous rejoignez Cloud Protection Service, le client Endpoint Protection peut utiliser le service de signature dynamique pour télécharger les nouvelles définitions avant leur publication sur Windows Update. Pour plus d’informations, consultez [Guide pratique pour créer et déployer des stratégies de logiciel anti-programme malveillant pour Endpoint Protection dans System Center Configuration Manager](endpoint-antimalware-policies.md).

8.  Effectuez toutes les étapes de l'Assistant.


## <a name="existing-site-system-server"></a>Serveur de système de site existant

1.  Dans la console Configuration Manager, cliquez sur **Administration**.

2.  Dans l’espace de travail **Administration**, développez **Configuration du site**, cliquez sur **Serveurs et rôles de système de site**, puis sélectionnez le serveur à utiliser pour Endpoint Protection.

3.  Sous l'onglet **Accueil** , dans le groupe **Serveur** , cliquez sur **Ajouter des rôles de système de site**.

4.  Sur la page **Général** , spécifiez les paramètres généraux du système de site, puis cliquez sur **Suivant**.

5.  Sur la page **Sélection du rôle système** , sélectionnez **Point Endpoint Protection** dans la liste des rôles disponibles, puis cliquez sur **Suivant**.

6.  Sur la page **Endpoint Protection** , sélectionnez la case à cocher **J'accepte les termes du contrat de licence Endpoint Protection** et cliquez sur **Suivant**.

    > [!IMPORTANT]
    >  Vous ne pouvez pas utiliser Endpoint Protection dans Configuration Manager, à moins que vous acceptiez les termes du contrat de licence.

7.  Dans la page **Cloud Protection Service**, sélectionnez le niveau d’information à envoyer à Microsoft pour aider au développement de nouvelles définitions, puis cliquez sur **Suivant**.

    > [!NOTE]
    >  Cette option configure les paramètres Cloud Protection Service (anciennement MAPS) utilisés par défaut. Vous pouvez configurer des paramètres personnalisés pour chaque stratégie anti-programme malveillant que vous configurez. Pour plus d’informations, consultez [Guide pratique pour créer et déployer des stratégies de logiciel anti-programme malveillant pour Endpoint Protection dans System Center Configuration Manager](endpoint-antimalware-policies.md).

8.  Effectuez toutes les étapes de l'Assistant.
