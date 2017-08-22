---
title: Software-updatepunt verwijderen | Microsoft Docs
description: Volg deze procedure om de software-update-punt sitesysteemrol op een site verwijderen uit de Configuration Manager-console.
keywords: 
author: dougeby
ms.author: dougeby
manager: angrobe
ms.date: 10/06/2016
ms.topic: article
ms.prod: configuration-manager
ms.service: 
ms.technology: configmgr-sum
ms.assetid: 2486375c-d4a2-4cf2-9124-9bee02bbf173
ms.openlocfilehash: 22de02c51be3a0cd66b1be0f04b2fbdeb897858c
ms.sourcegitcommit: 51fc48fb023f1e8d995c6c4eacfda7dbec4d0b2f
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 08/07/2017
---
#  <a name="BKMK_RemoveSUP"></a> De sitesysteemrol software-updatepunt verwijderen  

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*

U kunt de software-update-punt sitesysteemrol op een site verwijderen uit de Configuration Manager-console. Het clientbeleid wordt bijgewerkt om het software-updatepunt uit de lijst te verwijderen. Wanneer u het laatste software-updatepunt van de site hebt verwijderd, bevat de lijst van software-updatepunten geen software-updatepunten en worden software-updates in feite uitgeschakeld op de site. Wanneer u meerdere software-updatepunten op een primaire site hebt en u het software-updatepunt verwijdert dat is geconfigureerd als synchronisatiebron, moet u een ander software-updatepunt op de site kiezen als nieuwe synchronisatiebron.  

> [!NOTE]  
>  Wanneer u de siterol software-updatepunt uit een sitesysteem verwijdert, dient u 15 minuten te wachten voor u de siterol software-updatepunt opnieuw installeert.  

 Gebruik de volgende procedure om een software-updatepunt te verwijderen.  

#### <a name="to-remove-the-software-update-point"></a>Het software-updatepunt verwijderen  

1.  Klik op **Beheer** in de **Configuration Manager**-console.  

2.  Vouw **Siteconfiguratie**uit in de werkruimte Beheer en klik vervolgens op **Servers en sitesysteemrollen**.  

3.  Selecteer de sitesysteemserver met het software-updatepunt dat u wilt verwijderen en selecteer in **Sitesysteemrollen** **Software-updatepunt**.  

4.  Klik op **Rol verwijderen** op het tabblad **Siterol** in de groep **Siterol**. Bevestig dat u het software-updatepunt wilt verwijderen of selecteer een nieuwe synchronisatiebron voor de andere software-updatepunten op de site.  
