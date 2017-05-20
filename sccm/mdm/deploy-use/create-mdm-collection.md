---
title: Maak een MDM-verzameling met behulp van System Center Configuration Manager | Microsoft-documenten
description: Maak een MDM-collectie met behulp van System Center Configuration Manager.
ms.custom: na
ms.date: 03/05/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-hybrid
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: d1b4337f-85e8-45e6-8bbe-9f18b49041c7
caps.latest.revision: 18
caps.handback.revision: 0
author: mtillman
ms.author: mtillman
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 2c723fe7137a95df271c3612c88805efd8fb9a77
ms.openlocfilehash: fabbcfd2d5656d4fa8cb87feffe87e17998df145
ms.contentlocale: nl-nl
ms.lasthandoff: 05/17/2017

---
# <a name="create-an-mdm-collection-with-system-center-configuration-manager-and-microsoft-intune"></a>Maak een verzameling MDM met System Center Configuration Manager en Microsoft Intune

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*

Een Gebruikersverzameling van Configuration Manager is vereist voor de gebruikers opgeven die in het beheer van apparaten kunnen inschrijven. U kunt alleen verzamelingen van gebruikers (in plaats van apparaatverzamelingen) omdat de Intune-licenties zijn toegewezen door de gebruiker.

> [!NOTE]
> Om apparaten te registreren met Intune, hoeft u geen licenties toewijzen aan gebruikers in de Office 365-portal of Azure Active Directory-portal. Met inbegrip van de gebruikers in een verzameling die gekoppeld aan het Intune-abonnement wordt (in een [later stap](configure-intune-subscription.md)) is het enige dat is vereist.

Voor testdoeleinden kunt u instellen een **directe regel** en voeg specifieke gebruikers apparaten kunnen registreren. In de Configuration Manager-console athe kiest, **activa en naleving** > **Gebruikersverzamelingen**, klikt u op de **Start** tabblad > **maken** groep en klik vervolgens op **Gebruikersverzameling maken**. U moet gebruiken voor breder distributie **regels Query** gebruikers definiëren. Zie voor meer informatie over verzamelingen, [het maken van verzamelingen](https://technet.microsoft.com/library/mt629371.aspx).

![Een Gebruikersverzameling maken voor met MDM](../media/mdm-create-user-collection.png)

> [!div class="button"]
[Volgende stap >](confirm-dns.md)

