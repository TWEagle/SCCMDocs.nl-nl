---
title: Vereisten voor de naam van het domein bevestigen
titleSuffix: Configuration Manager
description: Controleer de vereisten voor de naam van het domein met System Center Configuration Manager.
ms.custom: na
ms.date: 03/21/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: configmgr-hybrid
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 522c2e82-20eb-4f38-859b-d55640b24e32
caps.latest.revision: "18"
caps.handback.revision: "0"
author: arob98
ms.author: angrobe
manager: angrobe
ms.openlocfilehash: 152a93559e8587d096552da800b1b84c7bb8bd28
ms.sourcegitcommit: 1132886e07d0c0a87dcc7eeef4577dd8d8840023
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 11/01/2017
---
# <a name="confirm-domain-name-requirements-with-system-center-configuration-manager-and-microsoft-intune"></a>Bevestig de vereisten voor de naam van het domein met System Center Configuration Manager en Microsoft Intune

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*

Indien nodig, de volgende stappen uitvoeren om te voldoen aan eventuele afhankelijkheden extern aan Configuration Manager:

1. Elke gebruiker moet een Intune-licentie toegewezen aan apparaten inschrijven hebben. Om te koppelen van Intune-licenties aan gebruikers, elke gebruiker een UPN (user Principal name) die openbaar omgezet worden kan moet hebben (bijvoorbeeld johndoe@contoso.com) of een alternatieve aanmeldings-ID die is geconfigureerd in Azure Active Directory. Configureren van een alternatieve aanmeldings-ID, kunnen gebruikers zich aanmelden via een e-mailadres, bijvoorbeeld, zelfs als de UPN in een NetBIOS-indeling (bijvoorbeeld contoso\janjansen).

  - Als uw bedrijf openbaar omzetbare UPN's hanteert (dat wil zeggen johndoe@contoso.com), is geen verdere configuratie vereist.
  - Als uw bedrijf gebruikt een niet-omgezette UPN (dat wil zeggen contoso\janjansen), moet u [een alternatieve ID configureren in Azure Active Directory](https://azure.microsoft.com/documentation/articles/active-directory-aadconnect-get-started-custom/#pages-under-the-section-sync).

2.  Implementeer en configureer Active Directory Federation Services (AD FS). (Optioneel)

     Bij het instellen van eenmalige aanmelding, kunnen uw gebruikers toegang krijgen tot de services in Intune zich aanmelden met hun bedrijfsreferenties.

     Zie de volgende onderwerpen voor meer informatie:
    -   [Voorbereiden voor eenmalige aanmelding](http://go.microsoft.com/fwlink/?LinkID=271124)
    -   [Plannen en implementeren van AD FS 2.0 voor gebruik met eenmalige aanmelding](http://go.microsoft.com/fwlink/?LinkID=271125)

3.  Implementeer en configureer adreslijstsynchronisatie.

     Adreslijstsynchronisatie kunt u Intune in te vullen met gesynchroniseerde gebruikersaccounts. De gesynchroniseerde gebruikersaccounts en beveiligingsgroepen worden toegevoegd aan Intune. Het niet inschakelen van adreslijstsynchronisatie is een veel voorkomende oorzaak voor het niet kunnen registreren van apparaten tijdens het instellen van Configuration Manager MDM met Microsoft Intune.

     Zie [Directory-integratie](http://go.microsoft.com/fwlink/?LinkID=271120) in de Active Directory-documentatiebibliotheek voor meer informatie.

4.  Optioneel, niet aanbevolen: Als u Active Directory Federation Services niet gebruikt, moet u gebruikers Microsoft Online-wachtwoorden opnieuw instellen.

     Als u AD FS niet gebruikt, moet u voor elke gebruiker een Microsoft Online-wachtwoord instellen.

> [!div class="button"]
[< Vorige stap](create-mdm-collection.md)[volgende stap >  ](configure-intune-subscription.md)
