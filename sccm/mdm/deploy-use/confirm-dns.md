---
title: Bevestig de vereisten voor de naam van het domein met behulp van System Center Configuration Manager | Microsoft-documenten
description: Bevestig de vereisten voor de naam van het domein met behulp van System Center Configuration Manager.
ms.custom: na
ms.date: 03/21/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-hybrid
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 522c2e82-20eb-4f38-859b-d55640b24e32
caps.latest.revision: 18
caps.handback.revision: 0
author: nathbarn
ms.author: nathbarn
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 1b9e49da1a5bbfca93fe683b82d2c0056a22cc1f
ms.openlocfilehash: 35b24294073956a6bdb14cae07705f56d31e00a9
ms.contentlocale: nl-nl
ms.lasthandoff: 05/17/2017

---
# <a name="confirm-domain-name-requirements-with-system-center-configuration-manager-and-microsoft-intune"></a>Bevestig de vereisten voor de naam van het domein met System Center Configuration Manager en Microsoft Intune

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*

Indien nodig, de volgende stappen nemen om te voldoen aan alle afhankelijkheden extern aan Configuration Manager:

1. Elke gebruiker moet een Intune-licenties zijn toegewezen om apparaten te registreren. Om te koppelen van Intune-licenties voor gebruikers, moet elke gebruiker een UPN (user Principal name) die openbaar opgelost worden kan hebben (bijvoorbeeld johndoe@contoso.com) of een andere aanmeldings-ID die is geconfigureerd in Azure Active Directory. Configureren van een andere aanmeldings-ID, kunnen gebruikers zich kunnen aanmelden met een e-mailadres, bijvoorbeeld, zelfs als hun UPN in een NetBIOS-indeling (bijvoorbeeld contoso\janjansen).

  - Als uw bedrijf openbaar omgezette UPN hanteert (dat wil zeggen johndoe@contoso.com), is er geen verdere configuratie vereist.
  - Als uw bedrijf gebruikmaakt van een niet-omgezette UPN (dat wil zeggen contoso\janjansen), moet u [een alternatieve ID in Azure Active Directory configureren](https://azure.microsoft.com/documentation/articles/active-directory-aadconnect-get-started-custom/#pages-under-the-section-sync).

2.  Implementeer en configureer Active Directory Federation Services (AD FS). (Optioneel)

     Als u een eenmalige aanmelding instelt, kunnen uw gebruikers toegang krijgen tot de services in Intune zich aanmelden met hun zakelijke referenties.

     Zie de volgende onderwerpen voor meer informatie:
    -   [Voorbereiden voor eenmalige aanmelding](http://go.microsoft.com/fwlink/?LinkID=271124)
    -   [Plannen en implementeren van AD FS 2.0 voor gebruik met eenmalige aanmelding](http://go.microsoft.com/fwlink/?LinkID=271125)

3.  Implementeer en configureer adreslijstsynchronisatie.

     Met behulp van adreslijstsynchronisatie kunt u Intune vullen met gesynchroniseerde gebruikersaccounts. De gesynchroniseerde gebruikersaccounts en beveiligingsgroepen worden toegevoegd aan Intune. Het niet inschakelen van adreslijstsynchronisatie is een veel voorkomende oorzaak voor het niet kunnen registreren van apparaten tijdens het instellen van Configuration Manager MDM met Microsoft Intune.

     Zie [Directory-integratie](http://go.microsoft.com/fwlink/?LinkID=271120) in de Active Directory-documentatiebibliotheek voor meer informatie.

4.  Optioneel, niet aanbevolen: Als u Active Directory Federation Services niet gebruikt, moet u gebruikers Microsoft Online-wachtwoorden opnieuw instellen.

     Als u AD FS niet gebruikt, moet u voor elke gebruiker een Microsoft Online-wachtwoord instellen.

> [!div class="button"]
[< Vorige stap](create-mdm-collection.md)[volgende stap >  ](configure-intune-subscription.md)

