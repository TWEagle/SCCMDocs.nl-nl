---
title: Kies Intune standalone of hybride MDM | Microsoft Docs
description: Kies of u voor het implementeren van hybride mobile device management met Intune en Configuration Manager of Intune zelfstandig worden uitgevoerd.
ms.custom: na
ms.date: 07/18/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-hybrid
ms.tgt_pltfrm: na
ms.topic: get-started-article
ms.assetid: 73ff9bb9-e605-4b68-92a1-487684fed42d
caps.latest.revision: 10
author: dougeby
ms.author: dougeby
manager: angrobe
ms.translationtype: MT
ms.sourcegitcommit: 648bc6b96aa5ccc834442a962e6d5b5125f88bb5
ms.openlocfilehash: ddb6d47e5dba4fddd6fa811d83b1bf0c91ad26f9
ms.contentlocale: nl-nl
ms.lasthandoff: 07/19/2017

---
# <a name="choose-between-microsoft-intune-standalone-and-hybrid-mobile-device-management-with-system-center-configuration-manager"></a>Kiezen tussen Microsoft Intune standalone en hybride beheer van mobiele apparaten met System Center Configuration Manager

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*

Een van de meest Veelgestelde vragen met betrekking tot beheer van mobiele apparaten (MDM) met Microsoft Intune is "Moet ik Intune integreert met Configuration Manager (hybride MDM) of Intune zelfstandig worden uitgevoerd in de alleen-cloudconfiguratie?" Als u wilt deze vraag te beantwoorden, moet u zorgvuldig de twee opties vergelijken.

## <a name="intune-standalone"></a>Zelfstandige versie van Intune
Zelfstandige Intune-versie is het aanbevolen implementatietopologie van Microsoft. Zelfstandige versie van Intune is een alleen-MDM-oplossing en wordt beheerd met behulp van een webconsole die toegankelijk is vanaf een willekeurige plaats in de hele wereld. Intune datacenters worden gehost in Noord-Amerika, Europa en Azië. Omdat Intune een cloudservice is, kunt u Intune-beheer implementeren op uw apparaten in een relatief korte periode.

Klanten zoeken in het algemeen sneller en eenvoudiger voor het implementeren van de topologie van de zelfstandige omdat er geen afhankelijkheid voor on-premises onderdelen. Intune standalone is nu op de Microsoft Azure cloud-platform en biedt veel geavanceerde functies, zoals:
- Geïntegreerde enterprise mobility management platform - een geïntegreerde cloud-platform en Administrator ervaren in Azure-portal voor Intune, Azure AD Premium en Azure Information Protection.
- Beheer van mobiele apparaten - mogelijkheden voor uitgebreide mobile device management en informatie-beveiliging.
- Schalen: implementeren en beheren van mobiele apparaten zonder dat u over schalen.
- Toegangsbeheer op basis van rollen: toegang beperken tot beheerfuncties op basis van rollen en bereiken.
- Toegang op programmeerniveau (API) - ondersteuning voor Microsoft Graph API en beheeropties SDK en PowerShell.
- Webconsole - gebaseerd op webstandaarden met ondersteuning voor de meeste moderne webbrowsers op basis van een HTML-5-console.
- Geavanceerde rapportage - de mogelijkheid om aangepaste rapporten te maken.
- Flexibiliteit - eenvoudige instellingen en snelle levering van nieuwe mogelijkheden.


## <a name="hybrid-mdm-with-configuration-manager"></a>Hybride MDM met Configuration Manager
Hybride MDM is een oplossing die mogelijkheden voor mobile device management van Intune in Configuration Manager integreert. Het maakt gebruik van Intune-beleid, profielen en toepassingen op apparaten als het kanaal levering maar maakt gebruik van Configuration Manager on-premises infrastructuur voor het beheren van inhoud en de apparaten worden beheerd. Een hybride implementatie kunt u 'één venster' bepalen.  Dit betekent dat u de dezelfde on-premises infrastructuur en de beheerconsole voor het beheren van mobiele apparaten met zowel Intune als pc's en servers met de traditionele client van Configuration Manager kunt gebruiken. U kunt een hybride MDM kiezen om de volgende redenen:  
- U wilt beheren, zowel mobiele apparaten die zijn ingeschreven bij Intune en apparaten beheerd met Configuration Manager-client vanuit dezelfde console beheerdersrechten
- Uw infrastructuur is vereist dat er meerdere NDES-servers voor de levering van het certificaat voor mobiele apparaten
- Uw infrastructuur is vereist dat er meerdere Exchange-connectors
- U vereist ondersteuning voor S/MIME-codering


## <a name="changing-the-mdm-authority-setting"></a>De MDM-instantie-instelling te wijzigen
Als u wijzigen van de instelling van de MDM-instantie wilt, kunt u deze zelf zonder contact opnemen met Microsoft Support en zonder de registratie ongedaan maken en registreren van uw bestaande beheerde apparaten. Zie voor meer informatie [wijzigen van uw MDM-instantie](/sccm/mdm/deploy-use/change-mdm-authority.md).

> [!NOTE]    
> U moet Configuration Manager versie 1610 of hoger te wijzigen van uw MDM-instantie in de zelfstandige versie van Intune hebben. Wanneer u een eerdere versie van Configuration Manager hebt, kunt u de MDM-instantie, maar het Help-informatie van Microsoft-ondersteuning en bewerkingen vereist. Ook moet u de registratie ongedaan maakt en al uw apparaten registreren nadat de MDM-instantie wordt gewijzigd.  

