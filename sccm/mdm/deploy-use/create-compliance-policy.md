---
title: "Créer et déployer une stratégie de conformité d’appareil | Microsoft Docs"
description: "Apprenez à créer et déployer des stratégie de conformité d’appareil dans System Center Configuration Manager."
ms.custom: na
ms.date: 03/05/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: configmgr-hybrid
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 0fd76043-d7ee-423d-8c5f-aa7e9ed58ce0
caps.latest.revision: 
author: andredm7
ms.author: andredm
manager: angrobe
robots: noindex
ms.openlocfilehash: 6630d0170df22f46f14df241ffd8d48266c69263
ms.sourcegitcommit: 51fc48fb023f1e8d995c6c4eacfda7dbec4d0b2f
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/07/2017
---
# <a name="create-and-deploy-a-device-compliance-policy"></a>Créer et déployer une stratégie de conformité d’appareil

*S’applique à : System Center Configuration Manager (Current Branch)*


## <a name="create-a-compliance-policy"></a>Créer une stratégie de conformité

1.  Dans la console System Center Configuration Manager, choisissez **Ressources et Conformité**.

2.  Dans l'espace de travail **Ressources et Conformité**, développez **Paramètres de compatibilité**, puis choisissez **Stratégies de conformité**.

3.  Sous l'onglet **Accueil**, dans le groupe **Créer**, choisissez **Créer une stratégie de conformité**.

4.  Dans la page **Général** de l'Assistant Création d'élément de configuration, spécifiez les informations suivantes :

  * **Nom**. Affectez un nom unique à la stratégie de conformité. Vous pouvez entrer jusqu’à 256 caractères.

  * **Description**. Entrez une description qui donne un aperçu du profil VPN et permette son identification dans la console Configuration Manager. Vous pouvez entrer jusqu’à 256 caractères.

  * **Type de stratégie de conformité**. Sélectionnez le type de stratégie à créer selon que l’appareil est géré ou non par Configuration Manager. Cela s’applique à la version ou à une version ultérieure.<br /><br /> Pour les appareils gérés par Intune, optez pour les **règles de conformité applicables aux appareils gérés sans client Configuration Manager** . Cette option vous permet également de sélectionner le type de plateforme auquel appliquer cette stratégie.

  * **Gravité de la non conformité pour les rapports**. Spécifiez le niveau de gravité signalé si cette stratégie de conformité est évaluée comme non conforme. Les degrés de gravité disponibles sont les suivants :

     * **Aucun**. Les appareils qui ne respectent pas cette règle de conformité ne signalent pas la gravité d’un échec pour les rapports Configuration Manager.
     * **Informations**. Les appareils qui ne respectent pas cette règle de conformité signalent la gravité d’un échec de niveau **Informations** pour les rapports Configuration Manager.   
     * **Avertissement**. Les appareils qui ne respectent pas cette règle de conformité signalent la gravité d’un échec de niveau **Avertissement** pour les rapports Configuration Manager.
     * **Critique**. Les appareils qui ne respectent pas cette règle de conformité signalent la gravité d’un échec de niveau **Critique** pour les rapports Configuration Manager.
     * **Critique avec événement**. Les appareils qui ne respectent pas cette règle de conformité signalent la gravité d’un échec de niveau **Critique** pour les rapports Configuration Manager. Ce niveau de gravité est également enregistré comme un événement Windows dans le journal des événements des applications.      

5.  Dans la page **Plateformes prises en charge**, choisissez les plateformes d'appareils qui seront évaluées par cette stratégie de conformité, ou choisissez **Sélectionner tout** pour choisir toutes les plateformes d'appareils. Plates-formes prises en charge : Windows 7, Windows 8.1 et Windows 10 ; Windows Server 2008 R2, Windows Server 2012, Windows Server 2012 R2 et Windows Server 2016.

6.  Dans la page **Règles** , vous définissez une ou plusieurs règles qui définissent la configuration dont les appareils doivent disposer pour être évalués comme étant conformes. Quand vous créez une stratégie de conformité, certaines règles sont activées par défaut, mais vous pouvez les modifier ou les supprimer. Pour obtenir la liste complète de toutes les règles, consultez la section Règles de stratégie de conformité plus loin dans cette rubrique.

  > [!NOTE]  
  >  Sur les PC Windows, la version du système d’exploitation Windows 8.1 apparaît comme étant la version 6.3 au lieu de 8.1. Si la règle de la version du système d’exploitation est définie sur Windows 8.1 pour Windows, l’appareil sera signalé comme non conforme, même si l’appareil possède Windows 8.1. Assurez-vous que vous définissez la version *signalée* correcte de Windows pour les règles de version minimale et maximale du système d’exploitation. Le numéro de version doit correspondre à la version que la commande **winver** retourne. Les téléphones Windows Phone n’ont pas ce problème, car la version signalée est 8.1 comme prévu. Pour les PC Windows avec le système d’exploitation Windows 10, la version doit être définie comme étant **10.0** plus le numéro de version du système d’exploitation que la commande **winver** retourne.

7.  Dans la page **Résumé** de l'Assistant, passez en revue les paramètres que vous avez définis, puis terminez l'Assistant.

 La nouvelle stratégie apparaît sous le nœud **Stratégies de conformité** de l'espace de travail **Ressources et Conformité**.

## <a name="deploy-a-compliance-policy"></a>Déployer une stratégie de conformité

1.  Dans la console Configuration Manager, choisissez **Ressources et Conformité**.

2.  Dans l'espace de travail **Ressources et Conformité**, développez **Paramètres de compatibilité**, puis choisissez **Stratégies de conformité**.

3.  Sous l’onglet **Accueil**, dans le groupe **Déploiement**, choisissez **Déployer**.

4.  Dans la boîte de dialogue **Déployer une stratégie de conformité**, choisissez **Parcourir** pour sélectionner le regroupement d'utilisateurs pour lesquels déployer la stratégie.

     En outre, vous pouvez sélectionner des options pour générer des alertes quand la stratégie n'est pas conforme et définir le calendrier selon lequel cette stratégie sera évaluée pour la conformité.

5.  Une fois que vous avez terminé, choisissez **OK**.

## <a name="monitor-the-compliance-policy"></a>Analyser la stratégie de conformité

#### <a name="to-view-compliance-results-in-the-configuration-manager-console"></a>Pour afficher les résultats de compatibilité dans la console Configuration Manager

1.  Dans la console Configuration Manager, choisissez **Surveillance**.

2.  Dans l'espace de travail **Surveillance**, choisissez **Déploiements**.

3.  Dans la liste **Déploiements** , sélectionnez le déploiement de la stratégie de conformité dont vous souhaitez vérifier les informations de conformité.

4.  Vous pouvez consulter un résumé des informations relatives à la conformité du déploiement de la stratégie dans la page principale. Pour afficher des informations plus détaillées, sélectionnez le déploiement, puis, sous l'onglet **Accueil**, dans le groupe **Déploiement**, choisissez **Afficher l'état** pour ouvrir la page **État du déploiement**.

    La page **État du déploiement** contient les onglets suivants :

    -   **Conforme**. Affiche la conformité de la stratégie en fonction du nombre de biens affectés. Vous pouvez choisir une règle pour créer un nœud temporaire sous le nœud **Utilisateurs** ou **Périphériques** de l'espace de travail **Biens et conformité**, qui contient tous les utilisateurs ou périphériques conformes à cette règle. Le volet **Détails du bien** affiche les utilisateurs ou les appareils conformes à la stratégie. Double-cliquez sur un utilisateur ou un appareil de la liste pour afficher des informations supplémentaires.

    -   **Erreur**. Affiche une liste de toutes les erreurs pour le déploiement de stratégie sélectionné en fonction du nombre de ressources concernées. Vous pouvez choisir une règle pour créer un nœud temporaire sous le nœud **Utilisateurs** ou **Périphériques** de l'espace de travail **Biens et conformité**, qui contient tous les utilisateurs ou appareils qui ont généré des erreurs avec cette règle. Lorsque vous sélectionnez un utilisateur ou un appareil, le volet **Détails du bien** affiche les utilisateurs ou les appareils affectés par un problème. Double-cliquez sur un utilisateur ou un appareil de la liste pour afficher des informations supplémentaires sur le problème.

    -   **Non conforme**. Affiche une liste de toutes les règles non conformes au sein de la stratégie en fonction du nombre de ressources affectées. Vous pouvez choisir une règle pour créer un nœud temporaire sous le nœud **Utilisateurs** ou **Périphériques** de l'espace de travail **Biens et conformité**, qui contient tous les utilisateurs ou périphériques non conformes à cette règle. Lorsque vous sélectionnez un utilisateur ou un appareil, le volet **Détails du bien** affiche les utilisateurs ou les appareils affectés par un problème. Double-cliquez sur un utilisateur ou un appareil de la liste pour afficher d'autres informations sur le problème.

    -   **Inconnu**. Affiche une liste de tous les utilisateurs et appareils qui n’ont pas signalé leur conformité pour le déploiement de stratégie sélectionné, ainsi que l’état du client actuel des appareils.

#### <a name="to-monitor-the-compliance-status-of-an-individual-device"></a>Pour surveiller l’état de conformité d’un appareil individuel

1.  Dans la console Configuration Manager, choisissez l’espace de travail **Actifs et conformité**.

2.  Choisissez **Appareils**.

3.  Cliquez avec le bouton droit sur une des colonnes pour en ajouter d’autres.

  Vous pouvez ajouter les colonnes suivantes :

  - **ID de l’appareil Azure Active Directory**.  Identificateur unique de l’appareil dans Azure Active Directory.

  - **Détails de l’erreur de conformité**.  Détails du message d’erreur en cas de problème avec le processus de bout en bout. Si cette colonne est vide, cela signifie qu’aucune erreur n’a été trouvée et que l’état de conformité a été correctement signalé.

  - **Emplacement de l’erreur de conformité**.  Plus de détails sur l’emplacement où la conformité a échoué. Si cette colonne est vide, cela signifie qu’aucune erreur n’a été trouvée et que l’état de conformité a été correctement signalé. Exemples d’emplacements où le processus de conformité est susceptible d’échouer : 
      - Client ConfigMgr
      - Point de gestion
      - Intune
      - Azure Active Directory
<br></br>
  - **Heure d’évaluation de la conformité**. Heure de la dernière vérification de la conformité.

  - **Heure définie de la conformité**. Dernière fois où la conformité a été mise à jour vers Azure Active Directory.

  - **Conformité de l’accès conditionnel**.  Indique si la machine est conforme ou non aux stratégies d’accès conditionnel.

  > [!IMPORTANT]
  > Par défaut, ces colonnes ne sont pas affichées.

#### <a name="to-view-intune-compliance-policies-charts"></a>Pour afficher les graphiques de stratégies de conformité Intune
1. À compter de la version 1610 de Configuration Manager, dans la console Configuration Manager, choisissez **Analyse**.

2. Dans l’espace de travail **Analyse**, accédez à **Vue d’ensemble** > **Paramètres de compatibilité** > **Stratégies de conformité**.

   Les graphiques suivants s’affichent :

    - **Conformité globale des appareils**. Affiche la conformité globale des appareils pour toutes les stratégies de conformité.
    - **Principales raisons de non-conformité**. Affiche les principales stratégies pour lesquelles les appareils ne sont pas conformes.

3. Choisissez une section dans l’un des deux graphiques pour afficher la liste des appareils dans cette catégorie.

#### <a name="to-view-a-health-attestation-report"></a>Pour afficher un rapport d’attestation d’intégrité

1.  À compter de la version 1602 de Configuration Manager, dans la console Configuration Manager, choisissez **Analyse**.

2.  Pour afficher un rapport de synthèse sur l’état de conformité actuel des appareils, choisissez **Sécurité**, puis **Attestation d’intégrité**.

3.  Pour afficher un rapport qui répertorie tous les appareils et tous les attributs d’attestation d’intégrité, choisissez **Sécurité**,puis **Attestation d’intégrité**.

## <a name="compliance-policy-rules"></a>Règles de stratégie de conformité
* **Demander des paramètres de mot de passe sur les appareils mobiles**. Vous pouvez forcer les utilisateurs à entrer un mot de passe avant qu'ils ne puissent accéder à leur appareil.

  **Pris en charge sur :**
    * Windows Phone 8+
    * iOS 6+
    * Android 4.0+
    * Samsung KNOX Standard 4.0+

* **Exiger un mot de passe pour déverrouiller un appareil inactif** (mise à jour 1602). Vous pouvez forcer les utilisateurs à entrer un mot de passe pour accéder à l’appareil verrouillé.

  **Pris en charge sur :**
  * Windows Phone 8+
  * iOS 6+
  * Android 4.0+
  * Samsung KNOX Standard 4.0+

* **Minutes d’inactivité avant demande du mot de passe** (mise à jour 1602). Vous pouvez spécifier la durée d'inactivité au terme de laquelle l'utilisateur doit entrer à nouveau son mot de passe. Sélectionnez l’une des valeurs disponibles suivantes : **1 minute**, **5 minutes**, **15 minutes**, **30 minutes**, **1 heure**.

  Cette règle doit être utilisée avec l’option **Exiger un mot de passe pour déverrouiller un appareil inactif**. La valeur définie ici détermine quand l’appareil est considéré comme inactif puis est verrouillé. Si l’option **Exiger un mot de passe pour déverrouiller un appareil inactif**  est définie sur **True**, l’utilisateur doit entrer un mot de passe pour accéder à l’appareil verrouillé.

  **Pris en charge sur :**
  * Windows Phone 8+
  * Windows RT/8.1
  * iOS 6+
  * Android 4.0+
  * Samsung KNOX Standard 4.0+

* **Exiger les mises à jour automatiques** (mise à jour 1602). Vous pouvez exiger que des appareils disposant de Windows 8.1 ou version ultérieure installent automatiquement les mises à jour, et spécifier la classe de celles-ci.

  La valeur doit être définie sur **Aucun** pour empêcher l’installation automatique, sur **Recommandé** pour installer automatiquement toutes les mises à jour recommandées, ou sur **Important** pour installer uniquement les mises à jour classées comme importantes.

  **Pris en charge sur :**
  * Windows Phone 8+

* **Autoriser les mots de passe simples**. Vous pouvez autoriser les utilisateurs à créer des mots de passe simples, comme « 1234 » ou « 1111 ». Ce paramètre est désactivé par défaut.

  **Pris en charge sur :**
  * Windows Phone 8+
  * iOS 6+

* **Longueur minimale du mot de passe**. Vous pouvez spécifier le nombre minimal de chiffres ou de caractères que le mot de passe de l'utilisateur doit contenir (6 par défaut).

  **Pris en charge sur :**
  * Windows Phone 8+
  * Windows 8.1
  * iOS 6+
  * Android 4.0+
  * Samsung KNOX Standard 4.0+

  >[!NOTE]
  >Pour les appareils qui exécutent Windows et qui sont sécurisés avec un compte Microsoft, la stratégie de conformité n’est pas évaluée correctement si l’option **Longueur minimale du mot de passe** a une valeur supérieure à 8 caractères ou si l’option **Nombre minimum de jeux de caractères** a une valeur supérieure à 2.

* **Chiffrement des fichiers sur l'appareil mobile**. Vous pouvez exiger le chiffrement de l'appareil pour la connexion aux ressources. Les appareils qui exécutent Windows Phone 8 sont automatiquement chiffrés. Les appareils qui exécutent iOS sont chiffrés quand vous configurez le paramètre **Demander des paramètres de mot de passe sur les périphériques mobiles**. Ce paramètre est activé par défaut.

  **Pris en charge sur :**
  * Windows Phone 8+
  * Windows 8.1
  * iOS 6+
  * Android 4.0+
  * Samsung KNOX Standard 4.0+

* **L'appareil ne doit pas être jailbreaké ou rooté**. Si vous activez ce paramètre, les appareils jailbreakés (iOS) ou rootés (Android) ne sont pas conformes. Ce paramètre est désactivé par défaut.

  **Pris en charge sur :**
  * iOS 6+
  * Android 4.0+
  * Samsung KNOX Standard 4.0+

* **Le profil de messagerie doit être géré par Intune**. Lorsque vous définissez cette option sur **Oui**, l’appareil doit utiliser le profil d’e-mail déployé sur l’appareil. L’appareil est considéré comme non conforme si le profil d’e-mail n’est pas déployé sur le groupe d’utilisateurs ciblé par la stratégie de conformité.

  De même, l’appareil n’est pas conforme si l’utilisateur a déjà configuré sur l’appareil un compte e-mail qui correspond au profil d’e-mail Intune déployé sur l’appareil. Dans ce cas, Intune ne peut pas remplacer le profil configuré par l’utilisateur et ne peut donc pas le gérer. L’utilisateur peut mettre l’appareil en conformité en supprimant les paramètres d’e-mail existants, ce qui permet à Intune d’installer le profil d’e-mail géré.

  Pour plus d'informations sur les profils de messagerie, consultez [Activer l'accès à la messagerie professionnelle à l'aide de profils de messagerie avec Microsoft Intune](https://technet.microsoft.com/library/dn800672.aspx). Ce paramètre est désactivé par défaut.

  **Pris en charge sur :**
  * iOS 6+

* **Profil de messagerie**. Si l'option **Le compte de messagerie doit être géré par Intune** est sélectionnée, choisissez **Sélectionner** pour choisir le profil de messagerie qui doit gérer les appareils. Le profil de messagerie doit être présent sur l'appareil.

  **Pris en charge sur :**
  * iOS 6+

* **Système d’exploitation minimal requis**. Quand un appareil ne satisfait pas la condition de version minimale du système d’exploitation que vous spécifiez, il est signalé comme non conforme. Un lien avec des informations sur la mise à niveau s’affiche. L’utilisateur peut choisir de mettre à niveau son appareil. Une fois cette opération effectuée, il peut accéder aux ressources de l’entreprise.

  **Pris en charge sur :**
  * Windows Phone 8+
  * Windows 8.1
  * iOS 6+
  * Android 4.0+
  * Samsung KNOX Standard 4.0+

* **Version maximale autorisée du système d’exploitation**. Quand un appareil utilise une version du système d’exploitation ultérieure à celle que vous spécifiez dans la règle, l’accès aux ressources de l’entreprise est bloqué et l’utilisateur est invité à contacter son administrateur. Tant que vous n’avez pas modifié la règle pour autoriser la version du système d’exploitation, cet appareil ne peut pas être utilisé pour accéder aux ressources de l’entreprise.

  **Pris en charge sur :**
  * Windows Phone 8+
  * Windows 8.1
  * iOS 6+
  * Android 4.0+
  * Samsung KNOX Standard 4.0+

* **Exiger que les appareils soient signalés comme intègres**(mise à jour 1602). Vous pouvez définir une règle exigeant que les appareils Windows 10 soient signalés comme intègres dans les stratégies de conformité nouvelles ou existantes. Si vous activez ce paramètre, les appareils Windows 10 sont évalués via le service d’attestation de l’intégrité (HAS, Health Attestation Service) pour les points de données suivants :

  - **BitLocker est activé**. Quand BitLocker est activé, l’appareil peut protéger les données stockées sur le lecteur contre tout accès non autorisé, en cas de mise hors tension ou en veille prolongée du système.

   Le chiffrement de lecteur BitLocker Windows chiffre toutes les données stockées sur le volume hébergeant le système d’exploitation Windows. BitLocker utilise le Module de plateforme sécurisée (TPM) pour protéger le système d’exploitation Windows et les données utilisateur. Il contribue également à prévenir toute falsification d’un ordinateur, même si celui-ci est laissé sans assistance, perdu ou volé.
   
   Si l’ordinateur est équipé d’un TPM compatible, BitLocker utilise celui-ci pour verrouiller les clés de chiffrement qui protègent les données. Par conséquent, les clés sont inaccessibles tant que le TPM n’a pas vérifié l’état de l’ordinateur.

  - **L’intégrité du code est activée**. L’intégrité du code est une fonctionnalité qui valide l’intégrité d’un pilote ou d’un système de fichiers à chaque chargement en mémoire. L’intégrité du code détecte si un pilote ou un fichier système non signé est chargé dans le noyau. Elle détecte également si un fichier système a été modifié par un logiciel malveillant exécuté par un compte d’utilisateur disposant de privilèges d’administrateur.

  - **Le démarrage sécurisé est activé**. Lorsque le démarrage sécurisé est activé, le système est contraint de démarrer dans un état approuvé par défaut. En outre, lorsque le démarrage sécurisé est activé, les composants principaux utilisés pour démarrer la machine doivent avoir des signatures de chiffrement appropriées, approuvées par le fabricant de l’appareil. Le microprogramme UEFI vérifie cela avant de laisser la machine démarrer. Si des fichiers ont été falsifiés, avec pour effet d’annuler leur signature, le système ne démarre pas.

  - **Le logiciel anti-programme malveillant à lancement anticipé est activé**. Ce paramètre s’applique uniquement aux PC. Le logiciel anti-programme malveillant à lancement anticipé assure la protection des ordinateurs de votre réseau au démarrage et avant l’initialisation de pilotes tiers.
  
   Cette règle est désactivée par défaut.

  Pour plus d’informations sur le fonctionnement du service HAS, consultez [Health Attestation CSP](https://msdn.microsoft.com/library/dn934876.aspx)(Fournisseur de services de configuration pour l’attestation de l’intégrité).

  **Pris en charge sur :**
  * Windows 10 et Windows 10 Mobile

- **Applications qui ne peuvent pas être installées sur l’appareil**. Si les utilisateurs installent une application à partir de la liste des applications non conformes de l’administrateur, ils seront bloqués lorsqu’ils tenteront d’accéder à la messagerie de l’entreprise et à d’autres ressources de l’entreprise qui prennent en charge l’accès conditionnel. Cette règle requiert le nom de l’application et l’ID de l’application lors de l’ajout d’une application à la liste des applications non conformes définies par l’administrateur. L’éditeur de l’application peut également être ajouté, mais ce n’est pas obligatoire.

    **Pris en charge sur :**
      * iOS 6+
      * Android 4.0+
      * Samsung KNOX Standard 4.0+
<br></br>
* **Type de mot de passe requis**. Spécifie si les utilisateurs doivent créer un mot de passe de type alphanumérique ou numérique. Pour les mots de passe alphanumériques, vous spécifiez également le nombre minimal de jeux de caractères que le mot de passe doit avoir. Les quatre jeux de caractères sont : lettres minuscules, lettres majuscules, symboles et chiffres.

    **Pris en charge sur :**
    * Windows Phone 8+
    * Windows 8.1+
    * iOS 6+
<br></br>
* **Bloquer le débogage USB sur l’appareil**. Vous n’avez pas à configurer ce paramètre, car le débogage USB est déjà désactivé pour les appareils Android for Work.

    **Pris en charge sur :**
    * Android 4.0+
    * Samsung KNOX Standard 4.0+
<br></br>
* **Bloquer les applications provenant de sources inconnues**. Exiger que les appareils interdisent l’installation des applications provenant de sources inconnues. Vous n’avez pas à configurer ce paramètre, car les appareils Android for Work limitent toujours l’installation à partir de sources inconnues.

    **Pris en charge sur :**
    * Android 4.0+
    * Samsung KNOX Standard 4.0+
<br></br>
* **Exiger l’analyse des menaces sur les applications**. Ce paramètre spécifie que la fonction Vérifier les applications est activée sur l’appareil. 

    **Pris en charge sur :**
    * Android 4.2 à 4.4
    * Samsung KNOX Standard 4.0+

### <a name="find-an-app-id"></a>Trouver l’ID d’une application

L’ID d’une application est un identificateur qui identifie de façon unique l’application dans les services d’application Apple et Google. Par exemple : com.contoso.myapp. Pour rechercher un ID :

- **Android**
    - Vous trouverez l’ID de l’application dans l’URL Google Play Store utilisée pour créer l’application. Exemple d’ID de l’application : *…?id=com.companyname.appname&hl=en*

- **iOS**
    1. Dans l’URL iTunes Store, trouvez le numéro d’identification, comme celui de cet exemple : */id875948587?mt=8*

    2. Dans un navigateur web, accédez à l’URL suivante, en remplaçant le chiffre par le numéro d’identification que vous venez de trouver (dans ce cas, l’exemple précédent) : https://itunes.apple.com/lookup?id=875948587

    3. Téléchargez et ouvrez le fichier texte.
  
    4. Recherchez le texte **bundleId**.

    Exemple d’ID de l’application : "*bundleId*":"*com.companyname.appname*" 

