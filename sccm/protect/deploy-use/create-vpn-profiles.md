---
title: "Guide pratique pour créer des profils VPN dans System Center Configuration Manager | Microsoft Docs"
description: "Découvrez comment créer des profils VPN dans System Center Configuration Manager."
ms.custom: 
ms.date: 4/19/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: f338e4db-73b5-45ff-92f4-1b89a8ded989
caps.latest.revision: "15"
author: lleonard-msft
caps.handback.revision: "0"
ms.author: alleonar
ms.manager: angrobe
ms.openlocfilehash: 359fcfd9754fb5c81763bc44cac45376ea3ab0b8
ms.sourcegitcommit: 51fc48fb023f1e8d995c6c4eacfda7dbec4d0b2f
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/07/2017
---
# <a name="how-to-create-vpn-profiles-in-system-center-configuration-manager"></a>Comment créer des profils VPN dans System Center Configuration Manager

*S’applique à : System Center Configuration Manager (Current Branch)*

Les types de connexion disponibles pour les différentes plateformes d’appareils sont décrits dans [Profils VPN dans System Center Configuration Manager](../../protect/deploy-use/vpn-profiles.md).  

Pour les connexions VPN tierces, distribuez l’application VPN avant de déployer le profil VPN. Si vous ne déployez pas l’application, les utilisateurs sont invités à le faire quand ils tentent de se connecter au VPN. Pour découvrir comment déployer des applications, consultez [Déployer des applications avec System Center Configuration Manager](../../apps/deploy-use/deploy-applications.md).

### <a name="create-a-vpn-profile"></a>Créer un profil VPN   

1.  Dans la console Configuration Manager, choisissez **Ressources et Conformité** > **Paramètres de compatibilité** > **Accès aux ressources de l’entreprise**  > **Profils VPN**.  

3.  Sous l’onglet **Accueil**, dans le groupe **Créer**, choisissez **Créer un profil VPN**.  


1.  Renseignez la page **Général**. . Notez ce qui suit :  

    - N’utilisez pas les caractères \\/:*?&lt;>&#124;, ou le caractère espace dans le nom du profil VPN. Ces caractères ne sont pas pris en charge par le profil VPN de Windows Server.  

     -   Sélectionnez **Import an existing VPN profile item from a file** (Importer un élément de profil VPN existant à partir d’un fichier) pour importer les informations de profil VPN qui ont été exportées vers un fichier XML (Windows 8.1 et Windows RT uniquement).  

1.  Dans la page **Connexion**, spécifiez les informations suivantes :  

    -   **Type de connexion** : choisissez le type de connexion VPN. Vous pouvez choisir parmi les types de connexion dans le tableau suivant.  

    -   **Liste de serveurs** : ajoutez un nouveau serveur à utiliser pour la connexion VPN. Selon le type de connexion, vous pouvez ajouter un ou plusieurs serveurs VPN et indiquer le serveur par défaut.  

        > [!NOTE]  
        >  Les appareils qui exécutent iOS ne prennent pas en charge l'utilisation de plusieurs serveurs VPN. Si vous configurez plusieurs serveurs VPN et que vous déployez le profil VPN sur un appareil iOS, seul le serveur par défaut sera utilisé.  

     Ce tableau fournit des options pour les types de connexion. Pour plus d'informations, consultez la documentation de votre serveur VPN.

| &nbsp;&nbsp;Option&nbsp;&nbsp; | Plus d'informations | &nbsp;&nbsp;Type de&nbsp;connexion&nbsp;&nbsp; |  
|----------------|----------------------|---------------------|  
|**Domaine**     |Domaine d’authentification que vous souhaitez utiliser. Un domaine d'authentification est un regroupement de ressources d'authentification utilisé par le type de connexion Pulse Secure.|Pulse Secure|    
|**Rôle**        |Rôle d’utilisateur qui a accès à cette connexion. |Pulse Secure|  
|**Groupe de connexion ou domaine** |Nom du groupe de connexion ou domaine auquel vous souhaitez vous connecter.|Dell SonicWALL Mobile Connect|  
|**Empreinte digitale**  |Chaîne, par exemple « Code d’empreinte digitale Contoso », qui sera utilisée pour vérifier que le serveur VPN est digne de confiance.<br /><br /> Une empreinte digitale peut être :<br /><br /> - envoyée au client pour qu’il sache qu’il peut approuver n’importe quel serveur présentant cette même empreinte lors de la connexion ;<br /><br /> - si l’appareil n’a pas encore l’empreinte digitale, il invite l’utilisateur à approuver le serveur VPN auquel il se connecte en affichant l’empreinte digitale (l’utilisateur vérifie l’empreinte manuellement et choisit **Approuver** pour se connecter).|Check Point Mobile VPN|  
|**Envoyer tout le trafic réseau via la connexion VPN** |Si cette option n'est pas sélectionnée, vous pouvez spécifier des itinéraires supplémentaires pour la connexion (pour les types de connexion **Microsoft SSL (SSTP)**, **Microsoft Automatic**, **IKEv2**, **PPTP** et **L2TP** ). On appelle cela le tunneling VPN ou fractionné.<br /><br /> Seules les connexions au réseau d'entreprise sont envoyées via un tunnel VPN. La tunnelisation VPN n'est pas utilisée quand vous vous connectez à des ressources sur Internet. |Tout|  
|**Suffixe DNS spécifique à la connexion** |Suffixe DNS spécifique à la connexion pour la connexion.|- Microsoft SSL (SSTP)<br /><br /> - Microsoft Automatic<br /><br /> - IKEv2<br /><br /> - PPTP<br /><br /> - L2TP|  
|**Ignorer VPN en cas de connexion à un réseau Wi-Fi d'entreprise**  |La connexion VPN n’est pas utilisée quand l’appareil est connecté au réseau Wi-Fi d’entreprise.|- Cisco AnyConnect<br /><br /> - Pulse Secure<br /><br /> - Client F5 Edge<br /><br /> - Dell SonicWALL Mobile Connect<br /><br /> - Check Point Mobile VPN<br /><br /> - Microsoft SSL (SSTP)<br /><br /> - Microsoft Automatic<br /><br /> - IKEv2<br /><br /> - L2TP|  
|**Ignorer le VPN en cas de connexion à un réseau Wi-Fi domestique**  |La connexion VPN n’est pas utilisée quand l’appareil est connecté à un réseau Wi-Fi domestique.|Tout|  
|**Par VPN d'application (iOS 7 et versions ultérieures, Mac OS X 10.9 et versions ultérieures)** |Associez cette connexion VPN à une application iOS pour que la connexion s’ouvre quand l’application est exécutée. Vous pouvez associer le profil VPN à une application lors de son déploiement.|- Cisco AnyConnect<br /><br /> - Pulse Secure<br /><br /> - Client F5 Edge<br /><br /> - Dell SonicWALL Mobile Connect<br /><br /> - Check Point Mobile VPN|  
|**Code XML personnalisé (facultatif)** |Spécifiez des commandes XML personnalisées qui configurent la connexion VPN.<br /><br /> Exemples :<br /><br /> Pour **Pulse Secure**:<br /><br /> **&lt;pulse-schema><br /> &nbsp; &lt;isSingleSignOnCredential>true&lt;/isSingleSignOnCredential\><br />&lt;/pulse-schema>**<br /><br /> Pour **CheckPoint VPN Mobile**:<br /><br /> **&lt;CheckPointVPN <br /> &nbsp; port="443" name="CheckPointSelfhost" <br /> &nbsp; sso="true" <br /> &nbsp; debug="3"<br />/>**<br /><br /> Pour **Dell SonicWALL Mobile Connect**:<br /><br /> **&lt;MobileConnect\><br />&nbsp; &nbsp; &lt;Compression\>false&lt;/Compression\><br />&nbsp; &nbsp; &lt;debugLogging\>True&lt;/debugLogging\><br />&nbsp; &nbsp; &lt;packetCapture\>False&lt;/packetCapture\><br />&lt;/MobileConnect\>**<br /><br /> Pour **Client F5 Edge**:<br /><br /> **&lt;f5-vpn-conf>&lt;single-sign-on-credential>&lt;/f5-vpn-conf>**<br /><br /> Pour plus d'informations sur la façon d'écrire des commandes XML personnalisées, reportez-vous à la documentation du VPN de chaque fabricant.|- Cisco AnyConnect<br /><br /> - Pulse Secure<br /><br /> - Client F5 Edge<br /><br /> - Dell SonicWALL Mobile Connect<br /><br /> - Check Point Mobile VPN|  

> [!NOTE]  
>  Pour en savoir plus sur la création de profils VPN pour les appareils mobiles, voir [Créer des profils VPN](../../mdm/deploy-use/create-vpn-profiles.md).  

Effectuez toutes les étapes de l'Assistant. Le nouveau profil VPN figure dans le nœud **Profils VPN** dans l'espace de travail **Ressources et Conformité** .

### <a name="next-steps"></a>Étapes suivantes

- Pour les connexions VPN tierces, distribuez l’application VPN avant de déployer le profil VPN. Si vous ne déployez pas l’application, les utilisateurs sont invités à le faire quand ils tentent de se connecter au VPN. Pour découvrir comment déployer des applications, consultez [Déployer des applications avec System Center Configuration Manager](../../apps/deploy-use/deploy-applications.md).

- Déployez le profil VPN comme décrit dans [Guide pratique pour déployer des profils dans System Center Configuration Manager](deploy-wifi-vpn-email-cert-profiles.md).  
