---
title: Installeren van een site met behulp van de basislijn 1606 media | Microsoft-documenten
description: Installeren of een upgrade naar de LTSB voor System Center Configuration Manager.
ms.custom: na
ms.date: 05/01/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: f4f9a5fd-f573-4b99-ad93-b2c76812e922
caps.latest.revision: 0
author: Brenduns
ms.author: brenduns
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 31819a1df4e63e1114682490a9b3c3b4e5c99cfa
ms.openlocfilehash: 39653604ba5fd8e1fe9dd4d42889221d983f9bec
ms.contentlocale: nl-nl
ms.lasthandoff: 05/17/2017


---
# <a name="install-and-upgrade-with-the-version-1606-baseline-media-for-system-center-configuration-manager"></a>Installatie en upgrade met de versie 1606 basislijn media voor System Center Configuration Manager

*Van toepassing op:  System Center Configuration Manager (huidige vertakking) (op lange termijn onderhoud vertakking)*

Als u Setup vanaf de media versie 1606 basislijn voor Configuration Manager uitvoert, installeert u de vertakking langetermijndoelen onderhoud of een huidige vertakking site van System Center Configuration Manager.

De basislijn media is beschikbaar op DVD als onderdeel van Microsoft System Center 2016 of release van System Center Configuration Manager (huidige vertakking en langetermijnbeveiliging onderhoud vertakking 1606). Zie voor meer informatie over basislijn media, [basislijn en update versies](/sccm/core/servers/manage/updates#baseline-and-udpate-versions).


Wanneer u de versie 1606 basislijn media, is de site die u installeert of een upgrade uitvoert naar:
- Een *huidige vertakking site* die equivalent zijn aan een site die is eerst is geïnstalleerd met behulp van de basislijn 1511 media en vervolgens naar versie 1606 plus de 1606 hotfix rollup - KB3186654 worden bijgewerkt.
-    Een *LTSB site* dat is gelijk aan het huidige filiaal waarop versie 1606 plus de 1606 hotfix rollup - KB3186654. De basislijn media bevat al de hotfix rollup.  Maar alle functies of mogelijkheden die beschikbaar zijn met de huidige vertakking wordt weergegeven, zoals beschreven in biedt geen ondersteuning voor de LTSB [Inleiding tot de langetermijndoelen onderhoud vertakking van System Center Configuration Manager](introduction-to-the-ltsb.md).

Als u niet bekend met de verschillende vertakkingen van System Center Configuration Manager bent, raadpleegt u [welke vertakking van Configuration Manager moet ik gebruiken](which-branch-should-i-use.md).




## <a name="changes-to-setup-with-the-1606-baseline-media"></a>Wijzigingen in Setup met de basislijn 1606 media
De basislijn 1606 media bevat de volgende wijzigingen aan de instellingen voor Configuration Manager.

### <a name="branch-and-edition"></a>Vertakking en edition
Wanneer u Setup uitvoert, wordt nu weergegeven met een licentieverlening pagina waar u de vertakking van Configuration Manager, moeten worden geïnstalleerd kunt selecteren. U kunt de huidige vertakking of het LTSB als een gelicentieerde installatie, of kunt u een evaluatie-editie van de huidige vertakking als een niet-gelicentieerde installatie.

Zie voor meer informatie [volumelicenties en vertakkingen voor System Center Configuration Manager](learn-more-editions.md).

### <a name="software-assurance-expiration"></a>Software Assurance-vervaldatum
Tijdens de installatie hebt u de optie in te voeren de **Software Assurance-vervaldatum** waarde. Dit is een optionele waarde die u als een handige herinnering opgeven kunt.

> [!NOTE]
> Microsoft heeft de verloopdatum die u opgeeft en wordt deze datum niet gebruiken voor validatie van de licentie niet valideren.  In plaats daarvan kunt u dit gebruiken als een herinnering aan de vervaldatum. Dit is handig omdat Configuration Manager periodiek controleert op nieuwe software-updates die worden aangeboden online zijn en de status van uw software assurance-licentie huidige zijn moet naar in aanmerking voor het gebruik van deze aanvullende updates.    

- U kunt de date-waarde opgeven op de **productcode** pagina van de Wizard Setup wanneer u het installatieprogramma vanuit de System Center Configuration Manager-versie 1606 basislijn media uitvoert.
- U kunt ook deze datum opgeven door **eigenschappen hiërarchie** > **volumelicenties** in de Configuration Manager-console.

Zie voor meer informatie "Software Assurance overeenkomsten" in [volumelicenties en vertakkingen voor System Center Configuration Manager](learn-more-editions.md).


### <a name="additional-pre-upgrade-configurations"></a>Aanvullende configuraties die u vóór de upgrade
Voordat u een upgrade van System Center 2012 Configuration Manager naar de LTSB, moet u de volgende aanvullende stappen ondernemen als onderdeel van de controlelijst voor de upgrade.  
Verwijder de sitesysteemrollen die de LTSB biedt geen ondersteuning voor:
- Asset Intelligence-synchronisatiepunt
- Microsoft Intune-connector
- Clouddistributiepunten

Zie voor meer informatie [upgraden naar System Center Configuration Manager](/sccm/core/servers/deploy/install/upgrade-to-configuration-manager).


### <a name="new-scripted-installation-options"></a>Nieuwe scriptmethode voor installatie-opties
De versie 1606 basislijn media biedt ondersteuning voor een nieuwe sleutel voor script zonder toezicht-bestand voor scriptinstallaties van een nieuwe site op het hoogste niveau. Dit geldt voor het installeren van een nieuwe zelfstandige primaire site of een centrale beheersite als deel van het scenario voor site-uitbreiding toe te voegen.

Wanneer u een onbewaakt script gebruikt voor het installeren van een gelicentieerde vertakking, moet u de volgende sectie, sleutelnamen en waarden toevoegen aan de sectie Options van het script. U hoeft niet te gebruiken deze waarden om een script van de installatie van een evaluatie-editie van de huidige vertakking wordt weergegeven:  

 **SABranchOptions**
-     **Sleutelnaam: SAActive**
  - Waarden: 0 of 1.  
  - Details:  0 installeert een evaluatie-editie niet-gelicentieerde van huidige vertakking wordt weergegeven en 1 een gelicentieerde versie installeert.   

- **CurrentBranch**
  - Waarden: 0 of 1.  
  - Details:  0 installeert de vertakking langetermijndoelen onderhoud en 1 wordt geïnstalleerd voor de huidige vertakking.  

Bijvoorbeeld, voor het installeren van een gelicentieerde versie van de huidige vertakking zou u gebruiken:

  **Sleutelnaam: SABranchOptions**
   -    **SAActive = 1**
   - **CurrentBranch = 1**


> [!IMPORTANT]  
> **SABranchOptions** werkt alleen met de installatie van de basislijn-media. Het is niet van toepassing wanneer u Setup vanaf de CD uitvoert. Meest recente map van een site u eerder hebt geïnstalleerd met behulp van de basislijn versie 1606 media.
>
> **SABranchOptions** niet van toepassing op scriptmethode upgrades van System Center 2012 Configuration Manager en altijd resulteert in de huidige vertakking.

Zie voor meer informatie [een opdrachtregel gebruiken voor het installeren van System Center Configuration Manager-sites](/sccm/core/servers/deploy/install/use-a-command-line-to-install-sites).


## <a name="install-a-new-site"></a>Een nieuwe site installeert
Wanneer u de 1606 basislijn media naar een nieuwe site van een onderdeel installeert, gebruikt u de site planning, voorbereiding, gebruiken en installatieprocedures beschreven in de [installeren van System Center Configuration Manager-sites](/sccm/core/servers/deploy/install/installing-sites) onderwerp door het toevoegen van de volgende overwegingen voor de installatie:

- Tijdens de installatie moet u de vertakking van Configuration Manager die u wilt installeren en u kunt details opgeven voor uw Software Assurance-overeenkomst.
- Alle sites in dezelfde hiërarchie moeten dezelfde vertakking worden uitgevoerd. Een hiërarchie hebt met een mengeling van LTSB huidige vertakking op verschillende sites wordt niet ondersteund.
-    Nieuwe scriptinstallatie. Zie voor meer informatie "Nieuw script installatieopties" eerder in dit artikel.

## <a name="expand-a-stand-alone-primary-site"></a>Een zelfstandige primaire site uitbreiden
U kunt een zelfstandige primaire site die de LTSB uitvoert uitbreiden.  Het proces is niet anders is dan die voor een huidige vertakking site met een voorbehoud gebruikt:

- Bij de installatie van de nieuwe centrale beheersite moet u de installatie van de oorspronkelijke bronmedia die u gebruikt voor het installeren van de site LTSB gebruiken. Setup uit te voeren vanaf de CD. Meest recente map voor dit scenario wordt niet ondersteund.

Zie voor meer informatie over het uitbreiden van een site, "Een zelfstandige primaire site uitbreiden" in [een site met de installatiewizard installeert](/sccm/core/servers/deploy/install/use-the-setup-wizard-to-install-sites).

## <a name="upgrade-from-system-center-2012-configuration-manager"></a>Upgrade van System Center 2012 Configuration Manager
Wanneer u een van System Center 2012 Configuration Manager upgrade, de siteplanning, voorbereiding en procedures gebruiken zoals beschreven in de [upgraden naar System Center Configuration Manager](/sccm/core/servers/deploy/install/upgrade-to-configuration-manager) onderwerp, maar met het volgende gewijzigd:

**Upgrade naar de huidige vertakking wordt weergegeven:**
- Tijdens de installatie, moet u de huidige vertakking wordt weergegeven en kunt u details opgeven voor uw Software Assurance-overeenkomst.
-     Nieuwe scriptinstallatie. Zie voor meer informatie "Nieuw script installatieopties" eerder in dit artikel.

**Upgrade naar de LTSB:**  
- Extra stappen voor het volgende in de controlelijst voor de upgrade.
- Tijdens de installatie moet u de LTSB en u kunt details opgeven voor uw Software Assurance-overeenkomst.
- U kunt alleen een site waarop System Center 2012 Configuration Manager met Service Pack 2 of System Center 2012 R2 Configuration Manager met Service Pack 1 te upgraden.

### <a name="in-place-upgrade-paths-for-the-1606-baseline-media"></a>Ter plekke upgradepaden voor de media 1606 basislijn
De basislijn 1606 media kunt u de volgende upgrade naar een gelicentieerde versie van System Center Configuration Manager:
- System Center 2012 Configuration Manager met servicepack 2.
- System Center 2012 R2 Configuration Manager met servicepack 1.

U kunt deze media ook een evaluatie-editie niet-gelicentieerde van huidige vertakking bijwerken naar een volledig gelicentieerde versie van de huidige vertakking.

Dit medium biedt geen ondersteuning voor de upgrade van:
- Andere versies van System Center 2012 Configuration Manager.
- Configuration Manager 2007 of een eerdere versie.
- Een release candidate-installatie van System Center Configuration Manager.

## <a name="about-the-cdlatest-folder-and-the-ltsb"></a>Over de CD. Meest recente map en de LTSB
De volgende zijn beperkingen met betrekking tot de media die door Configuration Manager worden gemaakt in de CD. Meest recente map op de siteserver. Deze limieten gelden voor sites waarop de LTSB wordt uitgevoerd:

Media in de CD. Meest recente map wordt ondersteund voor:
- Siteherstel.
- Site-onderhoud.
- Bijkomende onderliggende primaire sites installeren.

Media in de CD. Meest recente map wordt niet ondersteund voor:  
- Een centrale beheersite installeren als onderdeel van het scenario voor site-uitbreiding.

Zie voor meer informatie [de CD. Meest recente map](/sccm/core/servers/manage/the-cd.latest-folder).

## <a name="backup-recovery-and-site-maintenance-for-the-ltsb"></a>Back-up, herstel en site-onderhoud voor de LTSB
Gebruiken om een back-up, herstellen of site-onderhoud uitvoeren op een site die de LTSB uitvoert, de richtlijnen en procedures van [back-up en herstel voor System Center Configuration Manager](/sccm/protect/understand/backup-and-recovery).  

Gebruik Configuration Manager Setup vanaf de CD. Meest recente map van de back-up van uw site LTSB.

