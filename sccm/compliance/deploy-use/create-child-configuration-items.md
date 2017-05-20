---
title: Onderliggend configuratie-items maken | Microsoft-documenten
description: Onderliggend configuratie-items maken in System Center Configuration Manager.
ms.custom: na
ms.date: 10/06/2016
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 113984fa-6150-41a1-89ed-d2a83b979732
caps.latest.revision: 5
caps.handback.revision: 0
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: f9e939d871e95a3248d8e5d96cb73063a81fd5cf
ms.openlocfilehash: 33d4a2d5a09af74e1d76ac9b34a42b749f5bf7ef
ms.contentlocale: nl-nl
ms.lasthandoff: 05/17/2017


---
# <a name="how-to-create-child-configuration-items-in-system-center-configuration-manager"></a>Het maken van onderliggend configuratie-items in System Center Configuration Manager

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*

Onderliggend configuratie-items in System Center Configuration Manager zijn kopieën van configuratie-items die een relatie met de oorspronkelijke configuratie-item behouden in dat ze de oorspronkelijke configuratie van bovenliggende configuratie-item overnemen.  

Wanneer u de eigenschappen van een onderliggend configuratie-item in de Configuration Manager-console weergeven, kunt u de overgenomen objecten en instellingen met hun validatiecriteria niet bewerken. U kunt echter wel aanvullende validatiecriteria toevoegen aan het onderliggende configuratie-item en criteria vervolgens bewerken. U kunt ook nieuwe objecten en instellingen toevoegen aan het onderliggende configuratie-item.
De gebruikelijke doel voor het maken en bewerken van een onderliggend configuratie-item is de oorspronkelijke configuratie-item om te voldoen aan uw bedrijfsvereisten verfijnen.  

> [!NOTE]  
>  U kunt alleen onderliggende configuratie-items maken van configuratie-items van het type **Windows-desktops en -servers (aangepast)**.  

## <a name="to-create-a-child-configuration-item"></a>Een onderliggend configuratie-item maken  

1.  Klik in de Configuration Manager-console op **activa en naleving** > **compatibiliteitsinstellingen** > **configuratie-Items**.  

3.  Selecteer in de lijst **Configuratie-items** het configuratie-item waarvoor u een onderliggend configuratie-item wilt maken en klik op het tabblad **Start** in de groep **Configuratie-item** op **Onderliggend configuratie-item maken**.  

4.  Op de pagina **Algemeen** van de wizard **Onderliggend configuratie-item maken**kunt u een specifieke revisie van het bovenliggende configuratie-item kiezen die moet worden gebruikt voor het maken van het onderliggende object. De andere stappen in deze wizard zijn gelijk aan de stappen die u gebruikt als u een standaardconfiguratie-item maakt. Zie voor meer informatie [het maken van aangepaste configuratie-items voor Windows desktop- en servercomputers](../../compliance/deploy-use/create-custom-configuration-items-for-windows-desktop-and-server-computers-managed-with-the-client.md).  

5.  Voltooi de wizard. Het nieuwe onderliggende configuratie-item wordt weergegeven in de lijst **Configuratie-items** .  

