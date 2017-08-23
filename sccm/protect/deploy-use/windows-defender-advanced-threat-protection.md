---
title: "Protection avancée contre les menaces Windows Defender | Documents Microsoft"
description: "Découvrez comment gérer et surveiller le nouveau service Windows Defender Advanced Threat Protection (ATP) qui aide les entreprises à contrer les attaques avancées."
ms.custom: na
ms.date: 03/07/2017
ms.prod: configuration-manager
ms.technology: configmgr-other
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: a5fc033e-828e-4e45-9097-bbbd0697ebdf
caps.latest.revision: "5"
author: NathBarn
ms.author: nathbarn
manager: angrobe
ms.openlocfilehash: 6c3b67278fa587c137a29e174e277fb0f15872c8
ms.sourcegitcommit: 51fc48fb023f1e8d995c6c4eacfda7dbec4d0b2f
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/07/2017
---
# <a name="windows-defender-advanced-threat-protection"></a>Windows Defender Advanced Threat Protection

*S’applique à : System Center Configuration Manager (Current Branch)*

À compter de la version 1606 de Configuration Manager (Current Branch), Endpoint Protection facilite la gestion et la surveillance du service Windows Defender Advanced Threat Protection (ATP). Ce nouveau service aide les entreprises à détecter, analyser et contrer les attaques avancées ciblant leurs réseaux.  En savoir plus sur [Windows Defender ATP](http://aka.ms/technet-wdatp). Les stratégies Configuration Manager facilitent l’intégration et la surveillance des appareils gérés qui exécutent Windows 10 version 1607 (build 14328) ou ultérieure.

Windows Defender ATP est un service disponible dans le [Centre de sécurité Windows](https://securitycenter.windows.com). Grâce à l’ajout et au déploiement d’un fichier de configuration de l’intégration du client, Configuration Manager peut surveiller l’état du déploiement ainsi que l’intégrité de l’agent Windows Defender ATP. Windows Defender ATP est uniquement pris en charge sur les PC qui exécutent le client Configuration Manager. Ce service n’est pas disponible pour les appareils gérés à l’aide de la gestion des appareils mobiles (MDM) locale ou de la gestion MDM hybride dans Intune.

 **Conditions préalables**  

-   Abonnement au service en ligne Windows Defender Advanced Threat Protection  
-   Ordinateurs clients exécutant Windows 10 version 1607 ou ultérieure  
-   Ordinateurs clients exécutant la version 1610 de Configuration Manager ou un agent client ultérieur

## <a name="how-to-create-an-onboarding-configuration-file"></a>Créer un fichier de configuration de l’intégration  

 1.  Connectez-vous au [service en ligne Windows Defender ATP](https://securitycenter.windows.com/).   

 2.  Cliquez sur l’élément de menu **Gestion du point de terminaison**.  

 3.  Sélectionnez **System Center Configuration Manager (Current Branch) version 1606**, puis cliquez sur **Télécharger le package**.  

 4.  Téléchargez le fichier d’archive compressé (.zip) et extrayez son contenu.

> [!IMPORTANT]
> Le fichier de configuration de Windows Defender ATP contient des informations sensibles qui doivent être conservées de manière sécurisée.

## <a name="onboard-devices-for-windows-defender-atp"></a>Intégrer des appareils pour Windows Defender ATP  

1.  Dans la console Configuration Manager, accédez à **Ressources et Conformité** > **Vue d’ensemble** > **Endpoint Protection** > **Stratégies Windows Defender ATP**, puis cliquez sur **Créer une stratégie Windows Defender ATP**. L’Assistant Création d’une stratégie Windows Defender ATP s’ouvre.  

2.  Tapez un **nom** et une **description** pour la nouvelle stratégie Windows Defender ATP, puis sélectionnez **Intégration**. Cliquez sur **Suivant**.  

3.  Sélectionnez **Parcourir** pour accéder au fichier de configuration fourni par le locataire du service cloud Windows Defender ATP de votre organisation. Cliquez sur **Suivant**.  

4.  Spécifiez les exemples de fichiers collectés et partagés à partir des appareils gérés pour les besoins d’analyse.  

    -   **Aucun**   

    -   **Tous les types de fichiers**  

     Cliquez sur **Suivant**.  

5.  Passez en revue les informations de résumé et terminez l’Assistant.  

6.  Vous pouvez maintenant déployer la stratégie Windows Defender ATP sur les ordinateurs clients gérés en cliquant sur **Déployer**.  

## <a name="monitor-windows-defender-atp"></a>Surveiller Windows Defender ATP  

1.  Dans la console Configuration Manager, accédez à **Surveillance** > **Vue d’ensemble** > **Sécurité**, puis cliquez sur **Windows Defender ATP**.  

2.  Examinez le tableau de bord Protection avancée contre les menaces Windows Defender.  

    -   **État du déploiement de l’agent Windows Defender** : nombre et pourcentage d’ordinateurs clients gérés éligibles avec la stratégie Windows Defender ATP intégrée active.  

    -   **Intégrité de l’agent Windows Defender ATP** : pourcentage d’ordinateurs clients qui signalent l’état de l’agent Windows Defender ATP.  

        -   **Sain** : fonctionnement correct.  

        -   **Inactif** : aucune donnée n’a été envoyée au service durant la période.  

        -   **État de l’agent** : le service système de l’agent dans Windows n’est pas en cours d’exécution.  

        -   **Non intégré** : la stratégie a été appliquée, mais l’agent n’a pas signalé de stratégie intégrée.  


## <a name="how-to-create-and-deploy-an-offboarding-configuration-file"></a>Guide pratique pour créer et déployer un fichier de configuration de désintégration  

1.  Connectez-vous au [service en ligne Windows Defender ATP](https://securitycenter.windows.com/).   

2.  Cliquez sur l’élément de menu **Gestion du point de terminaison**.  

3.  Sélectionnez **System Center Configuration Manager (Current Branch) version 1606**, puis cliquez sur **Désintégration de point de terminaison**.  

4.  Téléchargez le fichier d’archive compressé (.zip) et extrayez son contenu. Les fichiers de désintégration sont valides pendant 30 jours.

5.  Dans la console Configuration Manager, accédez à **Ressources et Conformité** > **Vue d’ensemble** > **Endpoint Protection** > **Stratégies Windows Defender ATP**, puis cliquez sur **Créer une stratégie Windows Defender ATP**. L’Assistant Création d’une stratégie Windows Defender ATP s’ouvre.  

6.  Tapez un **Nom** et une **Description** pour la stratégie Windows Defender ATP, puis sélectionnez **Désintégration**. Cliquez sur **Suivant**.  

7.  Sélectionnez **Parcourir** pour accéder au fichier de configuration fourni par le locataire du service cloud Windows Defender ATP de votre organisation. Cliquez sur **Suivant**.  

8.  Passez en revue les informations de résumé et terminez l’Assistant.  

9.  Vous pouvez maintenant déployer la stratégie Windows Defender ATP sur les ordinateurs clients gérés en cliquant sur **Déployer**.  

> [!IMPORTANT]
> Les fichiers de configuration de Windows Defender ATP contiennent des informations sensibles qui doivent être conservées de manière sécurisée.

[Protection avancée contre les menaces Windows Defender](https://technet.microsoft.com/itpro/windows/keep-secure/windows-defender-advanced-threat-protection)

[Résoudre les problèmes liés à l’intégration de la protection avancée contre les menaces Windows Defender](https://technet.microsoft.com/itpro/windows/keep-secure/troubleshoot-onboarding-windows-defender-advanced-threat-protection)
