---
title: Een pakket familienaam (PFN) niet vinden voor de per-app VPN | Microsoft-documenten
description: Meer informatie over de twee manieren om te zoeken, een pakket familienaam zodat u een per-app VPN-verbinding kunt.
ms.custom: na
ms.date: 10/06/2016
ms.reviewer: na
ms.suite: na
ms.prod: configuration-manager
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 47118499-3d26-4c25-bfde-b129de7eaa59
caps.latest.revision: 3
author: Nbigman
ms.author: nbigman
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: bff083fe279cd6b36a58305a5f16051ea241151e
ms.openlocfilehash: ce50645155ecb14a82d8b982aa69c0f87dd15fbf
ms.contentlocale: nl-nl
ms.lasthandoff: 05/17/2017

---
# <a name="find-a-package-family-name-pfn-for-per-app-vpn"></a>Een pakket familienaam (PFN) niet vinden voor de per-app VPN

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*


Er zijn twee manieren om te zoeken, een PFN zodat u een VPN per app kunt configureren.

## <a name="find-a-pfn-for-an-app-thats-installed-on-a-windows-10-computer"></a>Een PFN vinden voor een app die geïnstalleerd op een computer met Windows 10

Als u met werkt de-app al is geïnstalleerd op een Windows-10-computer, kunt u de [Get-AppxPackage](https://technet.microsoft.com/library/hh856044.aspx) PowerShell-cmdlet de PFN ophalen.

De syntaxis voor Get-AppxPackage is:

` Parameter Set: __AllParameterSets`
` Get-AppxPackage [[-Name] <String> ] [[-Publisher] <String> ] [-AllUsers] [-User <String> ] [ <CommonParameters>]`

> [!NOTE]
> Mogelijk moet u PowerShell ook uitvoeren als een beheerder om op te halen van de PFN

Bijvoorbeeld informatie ophalen over de universele apps geïnstalleerd op het computergebruik `Get-AppxPackage`.

Voor informatie over een app die u de naam van kent of een deel van de naam van gebruikt `Get-AppxPackage *<app_name>`. Houd rekening met het gebruik van het jokerteken, vooral nuttig zijn als u niet zeker van de volledige naam van de app bent. Gebruik bijvoorbeeld de gegevens ophalen voor OneNote `Get-AppxPackage *OneNote`.


Hier vindt u de informatie opgehaald voor OneNote:

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



## <a name="find-a-pfn-if-the-app-is-not-installed-on-a-computer"></a>Zoeken naar een PFN als de app is niet geïnstalleerd op een computer

1.    Ga naar https://www.microsoft.com/en-us/store/apps
2.    Voer de naam van de app in de zoekbalk. Zoeken naar OneNote in ons voorbeeld.
3.    Klik op de koppeling naar de app. Houd er rekening mee dat de URL die u toegang hebt tot een reeks letters aan het einde heeft. In ons voorbeeld is de URL ziet er als volgt uit:`https://www.microsoft.com/en-us/store/apps/onenote/9wzdncrfhvjl`
4.    Plak de volgende URL in een ander tabblad `https://bspmts.mp.microsoft.com/v1/public/catalog/Retail/Products/<app id>/applockerdata`, vervangt `<app id>` met de app-id die u hebt ontvangen van https://www.microsoft.com/en-us/store/apps - reeks letters aan het einde van de URL in stap 3. In ons voorbeeld voorbeeld van OneNote, zou u plakken: `https://bspmts.mp.microsoft.com/v1/public/catalog/Retail/Products/9wzdncrfhvjl/applockerdata`.

In de rand, wordt de gewenste informatie weergegeven. Klik in Internet Explorer op **Open** om de gegevens te bekijken. De waarde PFN is gegeven op de eerste lijn. Hier ziet u hoe de resultaten komen in ons voorbeeld:


`{`
`  "packageFamilyName": "Microsoft.Office.OneNote_8wekyb3d8bbwe",`
`  "packageIdentityName": "Microsoft.Office.OneNote",`
`  "windowsPhoneLegacyId": "ca05b3ab-f157-450c-8c49-a1f127f5e71d",`
`  "publisherCertificateName": "CN=Microsoft Corporation, O=Microsoft Corporation, L=Redmond, S=Washington, C=US"`
`}`

