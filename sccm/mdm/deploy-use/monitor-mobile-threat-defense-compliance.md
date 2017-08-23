---
title: "Surveiller la conformité de la protection contre les menaces mobiles | System Center Configuration Manager"
description: "Surveiller l’état de conformité du partenaire de protection contre les menaces mobiles à partir de la console Configuration manager"
ms.custom: na
ms.date: 03/21/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 408190da-bea6-4122-9dd6-f90155040e88
caps.latest.revision: 
author: andredm7
ms.author: andredm
manager: angrobe
ms.openlocfilehash: 8edf83a0f761dfc16274ce49c3aa2b878c7fe6cd
ms.sourcegitcommit: 51fc48fb023f1e8d995c6c4eacfda7dbec4d0b2f
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/07/2017
---
# <a name="monitor-mobile-threat-defense-compliance"></a>**Surveiller la conformité de la protection contre les menaces mobiles**

*S’applique à : System Center Configuration Manager (Current Branch)*

## <a name="to-monitor-the-overall-compliance-status"></a>Pour surveiller l’état de conformité général

Pour surveiller l’état de la protection contre les menaces mobiles :

1.  Dans la console Configuration Manager, cliquez sur l’espace de travail **Surveillance**.

2.  Dans l'espace de travail **Surveillance**, cliquez sur le nœud **Sécurité**.

Vous pouvez afficher un résumé de l’état de conformité avec différents niveaux de menace, affiché dans un format graphique. Vous pouvez cliquer sur des sections individuelles des graphiques pour afficher plus d’informations, par exemple : 

- Le nombre d’appareils déclarés non conformes par plate-forme
- Les erreurs liées à l’état de conformité de l’appareil

![](http://i.imgur.com/bmPsiWk.png)

## <a name="to-monitor-the-individual-compliance-status"></a>Pour surveiller l’état de conformité individuel

Vous pouvez également afficher l’état de chaque appareil :

1.  Dans la console Configuration Manager, cliquez sur l’espace de travail **Actifs et conformité**.

2.  Cliquez sur **Appareils**.

> [!TIP] 
> Vous pouvez ajouter les colonnes **État de conformité de l’appareil** et **Niveau de menace pour l’appareil** pour afficher l’état. Par défaut, ces colonnes ne sont pas affichées.

## <a name="device-threat-protection-tab"></a>Onglet Protection contre les menaces sur les appareils

En outre, sur l’écran **Appareils**, vous pouvez sélectionner des appareils spécifiques, puis cliquer sur l’onglet **Protection contre les menaces sur les appareils** qui fournit plus de détails sur l’état de conformité de l’appareil. Vous trouverez ci-dessous les descriptions des colonnes et leurs valeurs attendues pour vous aider à analyser l’état de conformité de l’appareil.

> [!IMPORTANT] 
> L’onglet Protection contre les menaces de l’appareil s’affiche uniquement si l’appareil sélectionné est un appareil mobile.

|Nom de la colonne|Visible par défaut|Description| 
|-|-|-|
|**Description**| Oui | Plus d’informations sur les menaces fournies par le partenaire de protection contre les menaces mobiles. |
|**Heure de la dernière mise à jour**| Oui | Dernière fois où le partenaire de protection contre les menaces mobiles a envoyé des détails mis à jour sur la menace à Intune. |
|**Gravité de la menace**| Oui | La gravité de la menace est la définition d’une menace individuelle en fonction de la configuration de l’administrateur dans la console du partenaire de protection contre les menaces mobiles. Trois valeurs sont possibles : **Faible**, **Moyenne** ou **Élevée** |
|**État de la menace**| Oui | L’état actuel de la menace sur l’appareil. États possibles : **Actif**, **Résolu** ou **Ignoré :** indique que l’utilisateur a ignoré la menace sur son appareil, mais que la menace est toujours présente. |
|**Type de menace**| Oui | Type de menace pour le partenaire de protection contre les menaces mobiles. Valeurs possibles : **Application**, **Fichier** ou **OS** |
|**ID de compte AAD**| Non | L’identificateur unique Azure Active Directory. |
|**Classification**| Oui | Classification des menaces fourni par le partenaire de protection contre les menaces mobiles. Valeurs possibles : **Root Enabler, Riskware, Adware, Chargeware, DataLeak, Trojan, Worm, Virus, Exploit, Backdoor, Bot, AppDropper, ClickFraud, Spam, Spyware, SurveillanceWare, Vulnerability, Unknown, Root Jailbrake, Connectivity, TollFraud, SideloadedApp** |
|**ID d’appareil**| Non | L’ID d’objet Azure Active Directory qui représente l’appareil associé à un espace de travail avec des informations sur les menaces. |
|**ID de la menace**| Non | Identificateur unique de la menace généré par le partenaire de protection contre les menaces mobiles. L’ID de la menace est utilisé pour le suivi de la résolution. |
|**URL de la menace**| Non | Lorsqu’elle est présente, l’URL de la menace pointe vers la vue de cette menace spécifique sur la console de gestion du partenaire de protection contre les menaces mobiles. |

> [!TIP] 
> Veillez à activer les colonnes qui ne sont pas **visibles par défaut** pour plus de détails sur l’état de conformité de la protection contre les menaces mobiles pour vos appareils.
