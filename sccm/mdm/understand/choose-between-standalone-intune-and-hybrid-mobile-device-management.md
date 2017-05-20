---
title: Kies Intune standalone of hybride MDM | Microsoft-documenten
description: Kies of u beheer van hybride mobiele apparaten met Intune en Configuration Manager implementeren of zelfstandige Intune-versie worden uitgevoerd.
ms.custom: na
ms.date: 03/05/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-hybrid
ms.tgt_pltfrm: na
ms.topic: get-started-article
ms.assetid: 73ff9bb9-e605-4b68-92a1-487684fed42d
caps.latest.revision: 10
author: Mtillman
ms.author: mtillman
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 2c723fe7137a95df271c3612c88805efd8fb9a77
ms.openlocfilehash: cbdcf686b9565c56c7a6fca6086d94d9e45f641a
ms.contentlocale: nl-nl
ms.lasthandoff: 05/17/2017

---
# <a name="choose-between-microsoft-intune-standalone-and-hybrid-mobile-device-management-with-system-center-configuration-manager"></a>Kies tussen Microsoft Intune zelfstandige en hybride beheer van mobiele apparaten met System Center Configuration Manager

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*

Een van de meeste antwoorden op veelgestelde vragen over het beheer van mobiele apparaten (MDM) met Microsoft Intune is "Moet ik Intune geïntegreerd met Configuration Manager (hybride MDM) of zelfstandige Intune-versie worden uitgevoerd in de alleen-cloudconfiguratie?" Als u wilt beantwoorden die moet u zorgvuldig vergelijken van de twee opties en overweeg updates binnenkort in vroege 2017 zelfstandige versie van Intune.

## <a name="what-is-intune-standalone"></a>Wat is een zelfstandige versie van Intune?

Zelfstandige Intune is een alleen-MDM-oplossing die omvat geen lokale bronnen en wordt beheerd met een webconsole die toegankelijk zijn vanuit overal ter wereld. Intune datacenters worden gehost in Noord-Amerika, Europa en Azië. Omdat Intune een cloudservice is, kunt u beheer van Intune kunt implementeren op uw apparaten in een relatief korte periode. U kunt desgewenst ook Intune standalone als uw organisatie is verplaatst naar de cloud.

## <a name="what-is-hybrid-mdm-with-configuration-manager"></a>Wat is de hybride MDM met Configuration Manager?

Hybride MDM is een oplossing die Intune gebruikt als het kanaal voor de levering van beleidsregels, profielen en toepassingen op apparaten, maar maakt gebruik van Configuration Manager on-premises infrastructuur voor het opslaan en beheren van inhoud en de apparaten beheren. U kunt hybride MDM als u al geïnvesteerd in Configuration Manager hebben en die u wilt uitbreiden om mobiele apparaten te beheren. Een hybride implementatie hebt u "één venster" controle, wat betekent dat u kunt de dezelfde on-premises infrastructuur en de beheerconsole dat voor het beheren van mobiele apparaten met Intune, evenals pc's en servers met de traditionele Configuration Manager-client.

## <a name="whats-coming-to-intune-standalone-in-early-2017"></a>What's coming zelfstandige versie van Intune in eerdere 2017

Als u tussen zelfstandige en hybride kiest, moet u in overweging functies die zelfstandige versie van Intune in vroege 2017 binnenkort nemen. Hybride MDM heeft vandaag diverse geavanceerde functies die in het verleden werden waarom sommige klanten hun apparaten beheren met hybride MDM in plaats van Intune standalone kiezen:

-   Programmatisch toegang (API) – beheeropties SDK en PowerShell.

-   Aangepaste reporting – aangepaste rapporten maken.

-   Op rollen gebaseerd toegangsbeheer – Beperk de toegang tot de beheerfuncties op basis van rollen.

-   Schalen: implementeren en beheren van meer dan 100.000 mobiele apparaten.

-   Door één venster – traditionele PC-clients en Intune-beheerde apparaten met behulp van dezelfde console beheren.

Als u weet vanaf vandaag uw Intune-implementatie plant en hebben een verschillende maand venster voor piloting acceptatie testen en implementeren, kunt u overwegen kiezen Intune standalone nu met dien verstande dat afkomstig is van de cloudservice updates meer functionaliteit zal bevatten. Tijdens de eerste helft van het jaar 2017 ontvangt Intune standalone updates die veel van de geavanceerde functionaliteit van een hybride implementatie met Configuration Manager bevatten. Zelfstandige Intune-versie wordt binnenkort voor het Microsoft Azure cloudplatform worden verplaatst, en met het zal hebben een verbeterde schaalbaarheid, op rollen gebaseerde toegang via de Azure Portal, aangepaste rapporten en programmatisch toegang via de API van de grafiek Azure.

U kunt overschakelen van hybride Intune zelfstandige versie of van zelfstandige hybride, maar het Help-informatie van Microsoft ondersteuning en bewerkingen vereist. Het is ook vereist inschrijvingen en alle apparaten opnieuw te registreren wanneer de management-instantie is gewijzigd.  Microsoft werkt op de switch configuraties in een toekomstige service-update-ervaring te verbeteren.

