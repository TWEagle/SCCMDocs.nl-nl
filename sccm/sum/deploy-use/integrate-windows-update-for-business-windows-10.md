---
title: "Intégration à Windows Update for Business dans Windows 10 | Microsoft Docs"
description: "Utilisez Windows Update for Business pour tenir à jour les appareils Windows 10 de votre organisation connectés au service Windows Update."
keywords: 
author: dougeby
ms.author: dougeby
manager: angrobe
ms.date: 10/06/2016
ms.topic: article
ms.prod: configuration-manager
ms.service: 
ms.technology: configmgr-sum
ms.assetid: 183315fe-27bd-456f-b2c5-e8d25e05229b
ms.openlocfilehash: 26e73a69d5e6ca69e766fcf3cedd992353c92cd6
ms.sourcegitcommit: 51fc48fb023f1e8d995c6c4eacfda7dbec4d0b2f
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/07/2017
---
# <a name="integration-with-windows-update-for-business-in-windows-10"></a>Intégration avec Windows Update for Business dans Windows 10

*S’applique à : System Center Configuration Manager (Current Branch)*

Windows Update for Business (WUfB) vous permet de garantir la mise à jour des appareils Windows 10 de votre organisation avec les mécanismes de sécurité et les fonctionnalités Windows les plus récents quand ces appareils se connectent directement au service Windows Update (WU). Configuration Manager peut faire la distinction entre les ordinateurs Windows 10 qui utilisent WUfB et WSUS pour obtenir les mises à jour logicielles.  

 Certaines fonctionnalités de Configuration Manager ne sont plus disponibles quand les clients Configuration Manager sont configurés pour recevoir des mises à jour de Windows Update, notamment WUfB ou Windows Insiders :  

-   Rapports de conformité Windows Update :  

    -   Configuration Manager ne sera pas au courant des mises à jour publiées sur Windows Update. Les clients Configuration Manager configurés pour les mises à jour reçues à partir de Windows Update indiquent **inconnu** pour ces mises à jour dans la console Configuration Manager.  

    -   La résolution des problèmes liés à l’état de conformité global est difficile, car l’état **inconnu** concernait auparavant uniquement les clients qui n’avaient pas signalé leur état d’analyse à WSUS.  Maintenant, il inclut également les clients Configuration Manager qui reçoivent les mises à jour de Windows Update.  

    -   L’accès conditionnel (pour les ressources d’entreprise) basé sur l’état de conformité de mise à jour ne fonctionnera pas comme prévu pour les clients qui reçoivent des mises à jour de Windows Update, car ils ne respecteront jamais la conformité de Configuration Manager.  

    -   La conformité des mises à jour de définition fait partie des rapports de conformité de mise à jour globaux et ne fonctionnera pas non plus comme prévu.  La conformité des mises à jour de définition fait également partie de l’évaluation de l’accès conditionnel.  

-   Les rapports Endpoint Protection globaux pour Defender basés sur l’état de conformité de mise à jour retourneront des résultats incorrects en raison des données d’analyse manquantes.  

-   Configuration Manager ne pourra pas déployer les mises à jour Microsoft, telles qu’Office, Internet Explorer et Visual Studio, vers les clients qui sont connectés à WUfB pour recevoir des mises à jour.  

-   Configuration Manager ne pourra pas déployer les mises à jour tierces publiées dans WSUS et gérées par le biais de Configuration Manager vers les clients qui sont connectés à WUfB pour recevoir des mises à jour.  

-   Le déploiement de client complet Configuration Manager qui utilise l’infrastructure de mises à jour logicielles ne fonctionnera pas pour les clients qui sont connectés à WUfB pour recevoir des mises à jour.  

## <a name="identify-clients-that-use-wufb-for-windows-10-updates"></a>Identifier les clients qui utilisent WUfB pour les mises à jour de Windows 10  
 Appliquez la procédure suivante pour identifier les clients qui utilisent WUfB pour obtenir les mises à niveau et les mises à jour Windows 10, configurez ces clients pour cesser d’utiliser WSUS pour obtenir les mises à jour, et déployez un paramètre d’agent client pour désactiver le flux de travail des mises à jour logicielles pour ces clients.  

 **Conditions préalables**  

-   Clients qui exécutent Windows 10 Desktop Pro ou Windows 10 Édition Entreprise version 1511 ou ultérieure  

-   [Windows Update for Business](https://technet.microsoft.com/library/mt622730\(v=vs.85\).aspx) est déployé et les clients utilisent WUfB pour obtenir les mises à niveau et les mises à jour Windows 10.  

#### <a name="to-identify-clients-that-use-wufb"></a>Pour identifier les clients qui utilisent WUfB  

1.  Désactivez l’Agent Windows Update, s’il était précédemment activé, afin qu’il n’effectue pas l’analyse par rapport à WSUS.   
    La clé de Registre **HKEY_LOCAL_MACHINE\SOFTWARE\Policies\Microsoft\Windows\WindowsUpdate\AU\UseWUServer** peut être définie pour indiquer si l’ordinateur effectue l’analyse par rapport à Windows Update ou à WSUS.  Lorsque la valeur est 2, il n’effectue pas l’analyse par rapport à WSUS.  

2.  Il existe un nouvel attribut, **UseWUServer**, sous le nœud **Windows Update** dans l’Explorateur de ressources Configuration Manager.  

3.  Créez un regroupement basé sur l’attribut **UseWUServer** pour tous les ordinateurs connectés via WUFB pour les mises à jour et les mises à niveau.  

4.  Créez un paramètre d’agent du client pour désactiver le flux de travail des mises à jour logicielles et déployer le paramètre sur le regroupement d’ordinateurs connectés directement à WUFB.  

5.  Les ordinateurs qui sont gérés via WUFB affichent **Inconnu** dans l’état de conformité et ne sont pas comptabilisés dans le pourcentage de conformité global.  

## <a name="configure-windows-update-for-business-deferral-policies"></a>Configuration de Windows Update pour les stratégies d’entreprise de report d’entreprise
<!-- 1290890 -->
À compter de Configuration Manager version 1706, vous pouvez configurer des stratégies de report pour les appareils Windows 10 avec Mises à jour de fonctionnalités ou Mises à jour qualité gérés directement par Windows Update for Business. Vous pouvez gérer les stratégies de report du nouveau nœud **Stratégies Windows Update for Business** sous **Bibliothèque de logiciels** > **Maintenance de Windows 10**.

### <a name="prerequisites"></a>Conditions préalables
Les appareils Windows 10 gérés par Windows Update for Business doivent avoir une connectivité Internet.

#### <a name="to-create-a-windows-update-for-business-deferral-policy"></a>Pour créer une stratégie de report Windows Update for Business
1. Dans **Bibliothèque de logiciels** > **Maintenance de Windows 10** > **Mises à jour de Windows pour les stratégies d’entreprise**
2. Sous l’onglet **Accueil**, dans le groupe **Créer**, sélectionnez **Créer une stratégie Windows Update for Business** pour ouvrir l’assistant de création de stratégie Windows Update for Business.
3. Dans la page **Général**, indiquez un nom et une description pour la stratégie.
4. Sur la page **Stratégies de report**, choisissez de différer ou suspendre les mises à jour de fonctionnalités.    
    Les mises à jour de fonctionnalités sont généralement de nouvelles fonctionnalités pour Windows. Après avoir configuré le paramètre **Niveau de préparation de la branche**, vous pouvez définir si et pour quelle durée vous souhaitez différer la réception des fonctionnalités mises à jour après leur disponibilité auprès de Microsoft.
    - **Niveau de préparation de la branche** : définissez la branche pour laquelle l’appareil recevra les mises à jour de Windows (Current Branch ou Current Branch for Business).
    - **Période de report (jours)** : spécifiez le nombre de jours pendant lesquels les mises à jour de fonctionnalités sont différées. Vous pouvez différer la réception de ces mises à jour de fonctionnalités pendant une période de 180 jours à partir de leur publication.
    - **Suspendre le démarrage des mises à jour de fonctionnalités** : choisissez de suspendre la réception des mises à jour de fonctionnalités sur vos appareils pendant une période de 60 jours à partir du moment auquel vous suspendez les mises à jour. Une fois que le nombre maximal de jours s’est écoulé, la fonctionnalité de pause expirera automatiquement et l’appareil analysera les mises à jour de Windows pour déterminer celles qui sont applicables. Suite à cette analyse, vous pouvez à nouveau suspendre les mises à jour. Vous pouvez reprendre les mises à jour de fonctionnalités en désactivant la case à cocher.   
5. Choisissez de différer ou suspendre les mises à jour de qualité.     
    Les mises à jour de qualité sont généralement des améliorations et correctifs apportés aux fonctionnalités existantes de Windows, et sont généralement publiées le premier mardi de chaque mois, même si la publication peut être effectuée à tout moment par Microsoft. Vous pouvez définir si et pour combien de temps vous souhaitez différer la réception des mises à jour de qualité après leur disponibilité.
    - **Période de report (jours)** : spécifiez le nombre de jours pendant lesquels les mises à jour de fonctionnalités sont différées. Vous pouvez différer la réception de ces mises à jour de fonctionnalités pendant une période de 180 jours à partir de leur publication.
    - **Suspendre le démarrage des mises à jour de qualité** : choisissez de suspendre la réception des mises à jour de qualité sur vos appareils pendant une période de 35 jours à partir du moment auquel vous suspendez les mises à jour. Une fois que le nombre maximal de jours s’est écoulé, la fonctionnalité de pause expirera automatiquement et l’appareil analysera les mises à jour de Windows pour déterminer celles qui sont applicables. Suite à cette analyse, vous pouvez à nouveau suspendre les mises à jour. Vous pouvez reprendre les mises à jour de qualité en désactivant la case à cocher.
6. Sélectionnez **Installer les mises à jour à partir d’autres produits Microsoft** pour activer le paramètre de stratégie de groupe qui rend les paramètres de report applicables à Microsoft Update, ainsi qu’aux mises à jour de Windows.
7. Sélectionnez **Inclure les pilotes avec Windows Update** pour mettre à jour automatiquement les pilotes proposés avec les mises à jour de Windows. Si vous désactivez ce paramètre, les mises à jour de pilotes ne sont pas téléchargées à partir des mises à jour de Windows.
8. Terminez l'Assistant pour créer la stratégie de report.

#### <a name="to-deploy-a-windows-update-for-business-deferral-policy"></a>Pour déployer une stratégie de report Windows Update for Business
1. Dans **Bibliothèque de logiciels** > **Maintenance de Windows 10** > **Mises à jour de Windows pour les stratégies d’entreprise**
2. Sous l’onglet **Accueil** du groupe **Déploiement**, sélectionnez **Déployer la stratégie Windows Update for Business**.
3. Configurez les paramètres suivants :
    - **Stratégie de configuration à déployer** : sélectionnez la stratégie Windows Update for Business que vous souhaitez déployer.
    - **Regroupement**: cliquez sur **Parcourir** pour sélectionner le regroupement dans lequel vous souhaitez déployer la stratégie.
    - **Résoudre les règles non compatibles lorsqu’elles sont prises en charge** : sélectionnez cette option pour résoudre automatiquement toutes les règles qui ne sont pas compatibles pour Windows Management Instrumentation (WMI), le Registre, les scripts et tous les paramètres des appareils mobiles inscrits par Configuration Manager.
    - **Autoriser les corrections en dehors de la fenêtre de maintenance** : si une fenêtre de maintenance a été configurée pour le regroupement vers lequel vous déployez la stratégie, activez cette option pour laisser les paramètres de compatibilité résoudre la valeur en dehors de la fenêtre de maintenance. Pour plus d’informations sur les fenêtres de maintenance, consultez [Guide pratique pour utiliser les fenêtres de maintenance](/sccm/core/clients/manage/collections/use-maintenance-windows).
    - **Générer une alerte** : configure une alerte qui est générée si la compatibilité de la base de référence de configuration est inférieure à un pourcentage spécifié par une date et une heure spécifiques. Vous pouvez également spécifier si vous souhaitez qu'une alerte soit envoyée à System Center Operations Manager.
    - **Délai aléatoire (heures)** : spécifie un délai pour éviter un traitement excessif sur le service d’inscription d’appareils réseau. La valeur par défaut est 64 heures.
    - **Calendrier** : Spécifier le calendrier d’évaluation de la compatibilité par rapport auquel le profil déployé est évalué sur les ordinateurs clients. Il peut s'agir d'un calendrier simple ou d'un calendrier personnalisé. Lorsque l'utilisateur ouvre une session, le profil est évalué par les ordinateurs clients.
4.  Terminez l’assistant pour déployer le profil.
