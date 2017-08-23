---
title: "Gérer les fichiers d’installation rapide pour les mises à jour de Windows 10 | Microsoft Docs"
description: "Configuration Manager prend en charge les fichiers d’installation rapide pour Windows 10, permettant des téléchargements plus petits et des durées d’installation plus courtes sur les clients."
keywords: 
author: dougeby
ms.author: dougeby
manager: angrobe
ms.date: 03/24/2017
ms.topic: article
ms.prod: configuration-manager
ms.service: 
ms.technology: configmgr-sum
ms.assetid: b8d8af88-e8ac-4deb-921b-975e2d2afd80
ms.openlocfilehash: baffb5f026bd63c50f878214e71d2c9e9b8b51c2
ms.sourcegitcommit: 51fc48fb023f1e8d995c6c4eacfda7dbec4d0b2f
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/07/2017
---
# <a name="manage-express-installation-files-for-windows-10-updates"></a>Gérer les fichiers d’installation rapide pour les mises à jour de Windows 10
Depuis Configuration Manager version 1702, Configuration Manager prend en charge les fichiers d’installation rapide pour les mises à jour de Windows 10. Quand vous utilisez une version prise en charge de Windows 10, vous pouvez utiliser les paramètres Configuration Manager pour télécharger uniquement les modifications entre la mise à jour cumulative de Windows 10 du mois en cours et la mise à jour du mois précédent. Sans les fichiers d’installation rapide, Configuration Manager télécharge l’intégralité de la mise à jour cumulative de Windows 10 (notamment toutes les mises à jour des mois précédents) chaque mois. L’utilisation de fichiers d’installation rapide permet des téléchargements plus petits et des durées d’installation plus courtes sur les clients.

> [!IMPORTANT]
> Les paramètres pour la prise en charge de l’utilisation de fichiers d’installation rapide sont disponibles dans Configuration Manager 1702, mais la prise en charge du système d’exploitation est disponible dans Windows 10 version 1607 avec une mise à jour Windows Update Agent. Cette mise à jour est incluse dans les mises à jour publiées le 11 avril 2017 (Patch Tuesday). Pour plus d’informations sur ces mises à jour, consultez l’[article de support 4015217](http://support.microsoft.com/kb/4015217). Les mises à jour ultérieures s’appuieront sur l’installation rapide pour des téléchargements plus petits. Windows 10 version 1607 sans la mise à jour et les versions antérieures ne gèrent pas les fichiers d’installation rapide.


### <a name="to-enable-the-download-of-express-installation-files-for-windows-10-updates"></a>Pour activer le téléchargement des fichiers d’installation rapide pour les mises à jour de Windows 10
Pour démarrer la synchronisation des métadonnées pour les fichiers d’installation rapide Windows 10, vous devez l’activer dans les propriétés du point de mise à jour logicielle.
1.  Dans la console Configuration Manager, accédez à **Administration** > **Configuration du site** > **Sites**.
2.  Sélectionnez le site d’administration centrale ou le site principal autonome.
3.  Sur l'onglet **Accueil** dans le groupe **Paramètres** , cliquez sur **Configurer les composants de site**, puis cliquez sur **Point de mise à jour logicielle**. Sous l’onglet **Fichiers de mise à jour**, sélectionnez **Télécharger les fichiers complets de toutes les mises à jour approuvées et les fichiers d’installation rapide pour Windows 10**.

### <a name="to-enable-support-for-clients-to-download-and-install-express-installation-files"></a>Pour activer la prise en charge des clients pour télécharger et installer les fichiers d’installation rapide
Pour activer la prise en charge des fichiers d’installation rapide sur les clients, vous devez activer les fichiers d’installation rapide dans la section Mises à jour logicielles des paramètres du client. Vous créez ainsi un écouteur HTTP qui écoute les demandes de téléchargement des fichiers d’installation rapide sur le port que vous spécifiez.

> [!NOTE]    
> Il s’agit d’un port local utilisé par les clients pour écouter les demandes provenant de DO (Optimisation de la distribution) ou de BITS (Service de transfert intelligent en arrière-plan) pour télécharger le contenu rapide à partir du point de distribution. Il n’est pas nécessaire d’ouvrir ce port sur les pare-feu, car tout le trafic est sur l’ordinateur local.

Quand vous déployez les paramètres du client pour activer cette fonctionnalité sur le client, ils tentent de télécharger le delta entre la mise à jour cumulative de Windows 10 du mois en cours et la mise à jour du mois précédent (les clients doivent exécuter une version de Windows 10 qui prend en charge les fichiers d’installation rapide).
1.  Activez la prise en charge des fichiers d’installation rapide dans les propriétés du composant du point de mise à jour logicielle (procédure précédente).
2.  Dans la console Configuration Manager, accédez à **Administration** > **Paramètres du client**.
3.  Sélectionnez les paramètres du client appropriés, puis cliquez sur **Propriétés** sous l’onglet **Accueil**.
4.  Sélectionnez la page **Mises à jour logicielles** , configurez **Oui** pour le paramètre **Activer l’installation des mises à jour rapides sur les clients** et configurez le port utilisé par l’écouteur HTTP sur le client pour le paramètre **Port utilisé pour télécharger le contenu de fichiers d’installation rapide**.
