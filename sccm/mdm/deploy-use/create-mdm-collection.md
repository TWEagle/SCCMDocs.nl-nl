---
title: Een MDM-verzameling maken
titleSuffix: Configuration Manager
description: Een MDM-verzameling met System Center Configuration Manager maken.
ms.custom: na
ms.date: 03/05/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: configmgr-hybrid
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: d1b4337f-85e8-45e6-8bbe-9f18b49041c7
caps.latest.revision: "18"
caps.handback.revision: "0"
author: dougeby
ms.author: dougeby
manager: angrobe
ms.openlocfilehash: f8b865c48f6c69fe1cfd7221273b09f5557075e9
ms.sourcegitcommit: c236214b2fcc13dae7bad96d7fb33f692868191d
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/12/2017
---
# <a name="create-an-mdm-collection-with-system-center-configuration-manager-and-microsoft-intune"></a>Een MDM-verzameling maken met System Center Configuration Manager en Microsoft Intune

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*

Een Configuration Manager-Gebruikersverzameling is vereist voor het opgeven van de gebruikers apparaten bij het beheer registreren kunnen. Omdat Intune-licenties zijn toegewezen door de gebruiker, kunt u alleen verzamelingen van gebruikers (in plaats van apparaatverzamelingen) gebruiken.

> [!NOTE]
> Om apparaten te registreren bij Intune, hoeft u geen licenties toewijzen aan gebruikers in de Office 365-portal of Azure Active Directory-portal. In een verzameling die gekoppeld aan het Intune-abonnement wordt met inbegrip van de gebruikers (in een [later stap](configure-intune-subscription.md)), is dit is vereist.

Voor testdoeleinden kunt u instellen een **directe regel** en voeg specifieke gebruikers apparaten kunnen registreren. Kies in de Configuration Manager-console, **activa en naleving** > **Gebruikersverzamelingen**, klikt u op de **Start** tabblad > **maken** groep en klik vervolgens op **Gebruikersverzameling maken**. Voor een ruimere distributie moet u **regels Query** voor het definiëren van gebruikers. Zie voor meer informatie over verzamelingen [verzamelingen maken](https://technet.microsoft.com/library/mt629371.aspx).

![Een Gebruikersverzameling maken voor MDM](../media/mdm-create-user-collection.png)

> [!div class="button"]
[Volgende stap >](confirm-dns.md)
