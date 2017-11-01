---
title: Een package family name (PFN) voor VPN per app zoeken
titleSuffix: Configuration Manager
description: Meer informatie over de twee manieren om te zoeken, een package family name zodat u VPN per app kunt configureren.
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
ms.openlocfilehash: 640f44985ad45442b05f2bbf4ee1ec9c2590cba4
ms.sourcegitcommit: c236214b2fcc13dae7bad96d7fb33f692868191d
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/12/2017
---
# <a name="find-a-package-family-name-pfn-for-per-app-vpn"></a>Een package family name (PFN) voor VPN per app zoeken

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*


Er zijn twee manieren om een PFN zoeken, zodat u VPN per app kunt configureren.

## <a name="find-a-pfn-for-an-app-thats-installed-on-a-windows-10-computer"></a>Een PFN zoeken voor een app die geïnstalleerd op een computer met Windows 10

Als de app waarmee u met werkt al is geïnstalleerd op een computer met Windows 10, kunt u de [Get-AppxPackage](https://technet.microsoft.com/library/hh856044.aspx) PowerShell-cmdlet de PFN ophalen.

De syntaxis voor Get-AppxPackage is:

` Parameter Set: __AllParameterSets`
` Get-AppxPackage [[-Name] <String> ] [[-Publisher] <String> ] [-AllUsers] [-User <String> ] [ <CommonParameters>]`

> [!NOTE]
> Wellicht hebt u PowerShell als beheerder uitvoeren om op te halen van de PFN

Als u bijvoorbeeld informatie ophalen over alle universele apps die zijn geïnstalleerd op de computer gebruikt `Get-AppxPackage`.

Als u informatie over een app u de naam van weten of een deel van de naam van, gebruikt `Get-AppxPackage *<app_name>`. Let op het gebruik van het jokerteken, met name heel handig als u niet zeker van de volledige naam van de app bent. Gebruik bijvoorbeeld de info ophalen voor OneNote `Get-AppxPackage *OneNote`.


Dit is de informatie opgehaald voor OneNote:

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



## <a name="find-a-pfn-if-the-app-is-not-installed-on-a-computer"></a>Een PFN zoeken als de app is niet geïnstalleerd op een computer

1.  Ga naar https://www.microsoft.com/en-us/store/apps
2.  Voer de naam van de app in de zoekbalk. In ons voorbeeld wordt gezocht naar OneNote.
3.  Klik op de koppeling naar de app. Houd er rekening mee dat de URL die u toegang tot een reeks letters aan het einde heeft. In ons voorbeeld wordt de URL er als volgt:`https://www.microsoft.com/en-us/store/apps/onenote/9wzdncrfhvjl`
4.  Plak de volgende URL in een ander tabblad `https://bspmts.mp.microsoft.com/v1/public/catalog/Retail/Products/<app id>/applockerdata`en vervang `<app id>` met de app-id die u hebt verkregen via https://www.microsoft.com/en-us/store/apps - reeks letters aan het einde van de URL in stap 3. In ons voorbeeld voor OneNote plakt u het volgende: `https://bspmts.mp.microsoft.com/v1/public/catalog/Retail/Products/9wzdncrfhvjl/applockerdata`.

De gewenste informatie wordt in Microsoft Edge wordt weergegeven. Klik in Internet Explorer op **Open** om de informatie te bekijken. De PFN-waarde is opgegeven op de eerste regel. Hier ziet u hoe de resultaten zien er in ons voorbeeld:


`{`
`  "packageFamilyName": "Microsoft.Office.OneNote_8wekyb3d8bbwe",`
`  "packageIdentityName": "Microsoft.Office.OneNote",`
`  "windowsPhoneLegacyId": "ca05b3ab-f157-450c-8c49-a1f127f5e71d",`
`  "publisherCertificateName": "CN=Microsoft Corporation, O=Microsoft Corporation, L=Redmond, S=Washington, C=US"`
`}`
