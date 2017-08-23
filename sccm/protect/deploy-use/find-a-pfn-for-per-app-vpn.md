---
title: "Rechercher le nom d’une famille de packages (NFP) pour un VPN par application | Microsoft Docs"
description: "Découvrez deux façons de rechercher un nom de famille de packages en vue de configurer un VPN par application."
ms.custom: na
ms.date: 10/06/2016
ms.reviewer: na
ms.suite: na
ms.prod: configuration-manager
ms.technology: configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 47118499-3d26-4c25-bfde-b129de7eaa59
caps.latest.revision: "3"
author: Nbigman
ms.author: nbigman
manager: angrobe
ms.openlocfilehash: ce50645155ecb14a82d8b982aa69c0f87dd15fbf
ms.sourcegitcommit: 51fc48fb023f1e8d995c6c4eacfda7dbec4d0b2f
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/07/2017
---
# <a name="find-a-package-family-name-pfn-for-per-app-vpn"></a>Rechercher un nom de famille de packages (NFP) pour un VPN par application

*S’applique à : System Center Configuration Manager (Current Branch)*


Il existe deux façons de rechercher un NFP en vue de configurer un VPN par application.

## <a name="find-a-pfn-for-an-app-thats-installed-on-a-windows-10-computer"></a>Rechercher un NFP pour une application installée sur un ordinateur Windows 10

Si l’application avec laquelle vous travaillez est déjà installée sur un ordinateur Windows 10, vous pouvez utiliser l’applet de commande PowerShell [Get-AppxPackage](https://technet.microsoft.com/library/hh856044.aspx) pour obtenir le NFP.

La syntaxe de Get-AppxPackage est la suivante :

` Parameter Set: __AllParameterSets`
` Get-AppxPackage [[-Name] <String> ] [[-Publisher] <String> ] [-AllUsers] [-User <String> ] [ <CommonParameters>]`

> [!NOTE]
> Vous pouvez être amené à exécuter PowerShell en tant qu’administrateur pour récupérer le NFP.

Par exemple, pour obtenir des informations sur toutes les applications universelles installées sur l’ordinateur, utilisez `Get-AppxPackage`.

Pour obtenir des informations sur une application dont vous connaissez le nom en tout ou partie, utilisez `Get-AppxPackage *<app_name>`. Comme dans cet exemple, vous pouvez utiliser un caractère générique, ce qui est particulièrement pratique si vous ne connaissez pas le nom complet de l’application. Par exemple, pour obtenir les informations pour OneNote, utilisez `Get-AppxPackage *OneNote`.


Voici les informations récupérées pour OneNote :

`Name                   : Microsoft.Office.OneNote`

`Publisher              : CN=Microsoft Corporation, O=Microsoft Corporation, L=Redmond, S=Washington, C=US`

`Architecture           : X64`

`ResourceId             :`

`Version                : 17.6769.57631.0`

`PackageFullName        : Microsoft.Office.OneNote_17.6769.57631.0_x64__8wekyb3d8bbwe`

`InstallLocation        : C:\Program Files\WindowsApps`

`\Microsoft.Office.OneNote_17.6769.57631.0_x64__8wekyb3d8bbwe`

`IsFramework            : False`

**`PackageFamilyName      : Microsoft.Office.OneNote_8wekyb3d8bbwe`**

`PublisherId            : 8wekyb3d8bbwe`



## <a name="find-a-pfn-if-the-app-is-not-installed-on-a-computer"></a>Rechercher un NFP si l’application n’est pas installée sur un ordinateur

1.  Accédez à https://www.microsoft.com/en-us/store/apps
2.  Entrez le nom de l’application dans la barre de recherche. Pour notre exemple, recherchez OneNote.
3.  Cliquez sur le lien vers l’application. Notez que l’URL à laquelle vous accédez se termine par une série de lettres. Dans notre exemple, l’URL se présente comme suit : `https://www.microsoft.com/en-us/store/apps/onenote/9wzdncrfhvjl`
4.  Sous un autre onglet, collez l’URL `https://bspmts.mp.microsoft.com/v1/public/catalog/Retail/Products/<app id>/applockerdata` en remplaçant `<app id>` par l’ID d’application que vous avez obtenu à l’étape 3 à l’adresse https://www.microsoft.com/en-us/store/apps (la série de lettres située à la fin de l’URL). Pour notre exemple OneNote, nous collerions ceci : `https://bspmts.mp.microsoft.com/v1/public/catalog/Retail/Products/9wzdncrfhvjl/applockerdata`.

Dans Edge, les informations souhaitées s’affichent d’elles-mêmes ; dans Internet Explorer, cliquez sur **Ouvrir** pour afficher les informations. La valeur de NFP figure dans la première ligne. Voici à quoi ressemblent les résultats pour notre exemple :


`{`
`  "packageFamilyName": "Microsoft.Office.OneNote_8wekyb3d8bbwe",`
`  "packageIdentityName": "Microsoft.Office.OneNote",`
`  "windowsPhoneLegacyId": "ca05b3ab-f157-450c-8c49-a1f127f5e71d",`
`  "publisherCertificateName": "CN=Microsoft Corporation, O=Microsoft Corporation, L=Redmond, S=Washington, C=US"`
`}`
