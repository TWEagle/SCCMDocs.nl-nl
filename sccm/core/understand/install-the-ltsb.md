---
title: 'Een site met behulp van de basislijnmedia 1606 installeert '
titleSuffix: Configuration Manager
description: Installeren of upgraden naar de LTSB voor System Center Configuration Manager.
ms.custom: na
ms.date: 09/06/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: f4f9a5fd-f573-4b99-ad93-b2c76812e922
caps.latest.revision: "0"
author: aczechowski
ms.author: aaroncz
manager: angrobe
ms.openlocfilehash: 9fbb7dc1c64d82e03ba7ad3289e0939279ecf006
ms.sourcegitcommit: ca9d15dfb1c9eb47ee27ea9b5b39c9f8cdcc0748
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 01/04/2018
---
# <a name="install-and-upgrade-with-the-version-1606-baseline-media-for-system-center-configuration-manager"></a>Installatie en upgrade met de versie 1606 basislijnmedia voor System Center Configuration Manager

*Van toepassing op:  System Center Configuration Manager (huidige vertakking), (op lange termijn onderhoud vertakking)*

Wanneer u Setup vanaf de media versie 1606 basislijn voor Configuration Manager uitvoert, kunt u de vertakking Long-Term onderhoud of een site met huidige vertakking van System Center Configuration Manager installeren.

De basislijnmedia is beschikbaar op de DVD als onderdeel van Microsoft System Center 2016 of release van System Center Configuration Manager (huidige vertakking en Long-Term Servicing Branch 1606). Zie voor meer informatie over basislijnmedia, [basislijn- en updateversies](/sccm/core/servers/manage/updates#baseline-and-udpate-versions).


Wanneer u de basislijnmedia versie 1606 gebruikt, is de site die u installeert of een upgrade uitvoert naar:
- Een *Current Branch site* is gelijk aan een site die is eerst geïnstalleerd met behulp van de 1511-basislijn-media en vervolgens bijgewerkt naar versie 1606 plus de 1606 hotfix rollup - KB3186654.
-   Een *LTSB site* is gelijk aan de huidige vertakking-site waarop versie 1606 plus de 1606 hotfix rollup - KB3186654. De basislijnmedia bevat al de rollup hotfix.  Maar de LTSB ondersteunt niet alle functies of mogelijkheden beschikbaar in de huidige vertakking, zoals beschreven in [Inleiding tot de Long-Term onderhoud vertakking van System Center Configuration Manager](introduction-to-the-ltsb.md).

Als u niet bekend met de andere takken van System Center Configuration Manager bent, raadpleegt u [welke vertakking van Configuration Manager moet ik gebruiken](which-branch-should-i-use.md).




## <a name="changes-to-setup-with-the-1606-baseline-media"></a>Wijzigingen in Setup met de basislijn 1606 media
De basislijnmedia 1606 introduceert de volgende wijzigingen aan de installatie voor Configuration Manager.

### <a name="branch-and-edition"></a>Vertakking en edition
Wanneer u Setup uitvoert, wordt nu weergegeven met een Licensing pagina waar u de vertakking van Configuration Manager, die moeten worden geïnstalleerd kunt selecteren. U kunt de huidige vertakking of de LTSB als een gelicentieerde installatie kiezen of u kunt een evaluatie-editie van de huidige vertakking als een niet-gelicentieerde installatie.

Zie voor meer informatie [licenties en vertakkingen voor System Center Configuration Manager](learn-more-editions.md).

### <a name="software-assurance-expiration"></a>Software Assurance verlopen
Tijdens de installatie hebt u de optie in te voeren de **vervaldatum Software Assurance** waarde. Dit is een optionele waarde die u als een handige herinnering opgeven kunt.

> [!NOTE]
> Microsoft komt niet overeen voor de vervaldatum die u invoert en maakt geen gebruik van deze datum voor het valideren van licenties.  In plaats daarvan kunt u deze als een herinnering van de vervaldatum. Dit is nuttig omdat Configuration Manager periodiek controleert op nieuwe software-updates die worden aangeboden online zijn en de licentiestatus van uw software assurance actueel zijn om in aanmerking voor het gebruik van deze aanvullende updates moet worden.    

- U kunt de date-waarde opgeven op de **productcode** pagina van de Wizard Setup wanneer u het installatieprogramma vanaf de System Center Configuration Manager versie 1606 basislijnmedia uitvoeren.
- U kunt ook deze datum opgeven door te selecteren **eigenschappen van hiërarchie-instellingen** > **Licensing** in de Configuration Manager-console.

Zie voor meer informatie 'Software Assurance overeenkomsten' in [licenties en vertakkingen voor System Center Configuration Manager](learn-more-editions.md).


### <a name="additional-pre-upgrade-configurations"></a>Aanvullende configuraties die vóór de upgrade
Voordat u een upgrade van System Center 2012 Configuration Manager en de LTSB start, moet u de volgende aanvullende stappen uitvoeren als onderdeel van de controlelijst voor de upgrade.  
De sitesysteemrollen die de LTSB biedt geen ondersteuning voor verwijderen:
- Asset Intelligence-synchronisatiepunt
- Microsoft Intune-connector
- Clouddistributiepunten

Zie voor meer informatie [upgraden naar System Center Configuration Manager](/sccm/core/servers/deploy/install/upgrade-to-configuration-manager).


### <a name="new-scripted-installation-options"></a>Nieuwe scriptmethode voor installatie-opties
De versie 1606 basislijnmedia ondersteunt een nieuwe sleutel voor script zonder toezicht-bestand voor scriptinstallaties van een nieuwe site op het hoogste niveau. Dit geldt voor het installeren van een nieuwe zelfstandige primaire site of het toevoegen van een centrale beheersite als onderdeel van het scenario voor site-uitbreiding.

Wanneer u een onbewaakt script gebruikt voor het installeren van een gelicentieerde vertakking, moet u de volgende sectie, sleutelnamen en waarden toevoegen aan de sectie Options van het script. U hoeft niet naar deze waarden gebruikt om een script van de installatie van een evaluatie-editie van de huidige vertakking:  

 **SABranchOptions**
-   **Naam sleutel: SAActive**
  - Waarden: 0 of 1.  
  - Details:  0 installeert een evaluatie-editie niet-gelicentieerde van Current Branch en 1 een gelicentieerde versie wordt geïnstalleerd.   

- **CurrentBranch**
  - Waarden: 0 of 1.  
  - Details:  0 installeert de vertakking Long-Term onderhoud en 1 wordt geïnstalleerd voor de huidige vertakking.  

Als u bijvoorbeeld voor het installeren van een gelicentieerde Current Branch-versie die u wilt gebruiken:

  **Naam sleutel: SABranchOptions**
   -    **SAActive = 1**
   - **CurrentBranch = 1**


> [!IMPORTANT]  
> **SABranchOptions** werkt alleen met de installatie van de basislijnmedia. Dit geldt niet wanneer u Setup vanaf de CD uitvoert. Meest recente map van een site u eerder hebt geïnstalleerd met behulp van de basislijnmedia versie 1606.
>
> **SABranchOptions** niet van toepassing op systeemscript upgrades van System Center 2012 Configuration Manager en altijd resulteert in de huidige vertakking.

Zie voor meer informatie [een opdrachtregel gebruiken voor het installeren van System Center Configuration Manager-sites](/sccm/core/servers/deploy/install/use-a-command-line-to-install-sites).


## <a name="install-a-new-site"></a>Een nieuwe site installeert
Wanneer u de 1606 basislijnmedia om een nieuwe site van de vertakking installeert, gebruikt u de site-planning, voorbereiding, en installatieprocedures beschreven in de [installeren van System Center Configuration Manager-sites](/sccm/core/servers/deploy/install/installing-sites) onderwerp met het toevoegen van de volgende overwegingen voor Setup:

- Tijdens de installatie moet u de vertakking van Configuration Manager die u wilt installeren en u kunt details opgeven voor uw Software Assurance-overeenkomst.
- Alle sites in dezelfde hiërarchie moeten dezelfde tak uitvoeren. Een hiërarchie hebt met een combinatie van LTSB en Current Branch op verschillende sites wordt niet ondersteund.
-   Nieuwe scriptmethode voor installatie. Zie voor meer informatie 'Nieuw script installatieopties' eerder in dit artikel.

## <a name="expand-a-stand-alone-primary-site"></a>Een zelfstandige primaire site uitbreiden
U kunt een zelfstandige primaire site waarop de LTSB uitbreiden.  Het proces is niet anders dan die voor een Current Branch-site met een voorbehoud:

- Bij het installeren van de nieuwe centrale beheersite moet u Setup uit de oorspronkelijke bronmedia die u gebruikt voor het installeren van de LTSB-site. Setup uit te voeren vanaf de CD. Meest recente map voor dit scenario wordt niet ondersteund.

Zie voor meer informatie over het uitbreiden van een site, 'Een zelfstandige primaire site uitbreiden' in [een site installeren met de Wizard Setup](/sccm/core/servers/deploy/install/use-the-setup-wizard-to-install-sites).

## <a name="upgrade-from-system-center-2012-configuration-manager"></a>Upgrade van System Center 2012 Configuration Manager
Wanneer u een van System Center 2012 Configuration Manager upgrade, gebruikt u de siteplanning, voorbereiding en procedures zoals beschreven in de [upgraden naar System Center Configuration Manager](/sccm/core/servers/deploy/install/upgrade-to-configuration-manager) onderwerp, maar met de volgende wijzigingen:

**Upgrade naar de huidige vertakking:**
- Tijdens de installatie, moet u de huidige vertakking en kunt u de details voor de overeenkomst van uw Software Assurance opgeven.
-   Nieuwe scriptmethode voor installatie. Zie voor meer informatie 'Nieuw script installatieopties' eerder in dit artikel.

**Upgrade naar de LTSB:**  
- Aanvullende stappen voor het volgende in de controlelijst voor de upgrade.
- Tijdens de installatie moet u de LTSB en kunt u de details voor de overeenkomst van uw Software Assurance opgeven.
- U kunt alleen een site waarop System Center 2012 Configuration Manager met Service Pack 1, System Center 2012 Configuration Manager met Service Pack 2, System Center 2012 R2 Configuration Manager met Service Pack 1 of System Center 2012 R2 Configuration upgraden Manager zonder service Pack.

### <a name="in-place-upgrade-paths-for-the-1606-baseline-media"></a>In-place upgradepaden voor de basislijn 1606 media
De basislijnmedia 1606 kunt u de volgende versies upgraden naar een gelicentieerde versie van System Center Configuration Manager:
- System Center 2012 R2 Configuration Manager met servicepack 1
- System Center 2012 R2 Configuration Manager zonder servicepack (hiervoor is het gebruik van de basislijnmedia voor versie 1606 die is uitgebracht op 15 December 2016 vereist.)
- System Center 2012 Configuration Manager met servicepack 2
- System Center 2012 Configuration Manager met Service Pack 1 (hiervoor is het gebruik van de basislijnmedia voor versie 1606 die is uitgebracht op 15 December 2016 vereist.)


U kunt ook dit medium een evaluatie-editie niet-gelicentieerde van Current Branch bijwerken naar een volledig gelicentieerde versie van de huidige vertakking.

Dit medium biedt geen ondersteuning voor het upgraden van:
- Andere versies van System Center 2012 Configuration Manager.
- Configuration Manager 2007 of lager.
- Een release candidate-installatie van System Center Configuration Manager.

## <a name="about-the-cdlatest-folder-and-the-ltsb"></a>Over de CD. Meest recente map en de LTSB
De volgende zijn beperkingen over het gebruik van de media die Configuration Manager in de CD maakt. Meest recente map op de siteserver. Deze limieten gelden voor sites waarop de LTSB wordt uitgevoerd:

Media in de CD. Meest recente map wordt ondersteund voor:
- Site recovery.
- Site-onderhoud.
- Extra onderliggende primaire sites installeren.

Media in de CD. Meest recente map wordt niet ondersteund voor:  
- Een centrale beheersite installeert als onderdeel van het scenario voor site-uitbreiding.

Zie voor meer informatie [de CD. Meest recente map](/sccm/core/servers/manage/the-cd.latest-folder).

## <a name="backup-recovery-and-site-maintenance-for-the-ltsb"></a>Back-up, herstel en site-onderhoud voor de LTSB
Als u wilt back-up, herstellen of site-onderhoud uitvoeren op een site waarop de LTSB, gebruiken de richtlijnen en procedures uit [back-up en herstel voor System Center Configuration Manager](/sccm/protect/understand/backup-and-recovery).  

Gebruik Configuration Manager Setup vanaf de CD. Meest recente map van de back-up van uw site LTSB.
