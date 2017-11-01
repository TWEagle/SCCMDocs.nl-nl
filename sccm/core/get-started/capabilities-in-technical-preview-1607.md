---
title: Mogelijkheden van Technical Preview 1607
titleSuffix: Configuration Manager
description: Meer informatie over functies die beschikbaar zijn in de Technical Preview voor System Center Configuration Manager, versie 1607.
ms.custom: na
ms.date: 01/23/2017
ms.prod: configuration-manager
ms.technology: configmgr-other
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 2bb69547-3370-4860-96b0-7fb600c56482
caps.latest.revision: "11"
author: Brenduns
ms.author: brenduns
manager: angrobe
ms.openlocfilehash: 3967df286332a3fde7f9c0eb22167ae2889dfcd8
ms.sourcegitcommit: c236214b2fcc13dae7bad96d7fb33f692868191d
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/12/2017
---
# <a name="capabilities-in-technical-preview-1607-for-system-center-configuration-manager"></a>Mogelijkheden van Technical Preview 1607 voor System Center Configuration Manager

*Van toepassing op: System Center Configuration Manager (Technical Preview)*

Dit artikel bevat de functies die beschikbaar in de Technical Preview voor System Center Configuration Manager, versie 1607 zijn. U kunt deze versie om te werken en nieuwe mogelijkheden toevoegen aan uw Configuration Manager technical preview-site installeren.      Controleer voordat u deze versie van de technical preview installeert, de inleidende informatie [Technical Preview voor System Center Configuration Manager](../../core/get-started/technical-preview.md), om vertrouwd te raken met algemene vereisten en beperkingen voor het gebruik van een technical preview hoe bijwerken tussen versies en hoe u feedback over de functies in een technical preview.    


**Hier volgen nieuwe functies die u met deze versie kunt uitproberen.**  

## <a name="dmp_edition"></a>Verbeteringen in de Windows 10-editie-Upgradebeleid

In deze release zijn de volgende verbeteringen aangebracht in dit beleid:

* U kunt nu de editie-Upgradebeleid gebruiken met Windows 10-pc's met de Configuration Manager client naast Windows 10-computers zijn ingeschreven bij Microsoft Intune.
* U kunt Windows 10 Professional bijwerken naar een van de platforms die compatibel met uw hardware zijn in de wizard.

[Lees meer over de Windows 10-editie-Upgradebeleid](/sccm/compliance/deploy-use/upgrade-windows-version)

### <a name="try-it-out"></a>Probeer het nu!

1. Gebruik de informatie in de [bestaande editie-Upgradebeleid onderwerp](/sccm/compliance/deploy-use/upgrade-windows-version) editie-Upgradebeleid maken.
2. Dit beleid implementeren op een Windows 10-PC waarop de Configuration Manager-client wordt uitgevoerd.
Als het beleid een bepaalde Windows-computer bereikt, wordt de computer binnen twee uur opnieuw opgestart om de upgrade toe te passen. U kan niet op dit moment opnieuw opstarten onderdrukken. Zorg ervoor dat u informeren over alle gebruikers waarop u het beleid implementeert, of het beleid wordt uitgevoerd buiten de gebruikers plannen werkuren.

### <a name="known-issue-with-this-release"></a>Bekend probleem met deze release
In de Configuration Manager-clientinstellingen, ziet u mogelijk de instellingen voor **Edition Upgrade**. Deze instellingen zijn in deze release niet functioneel. Gebruik de instructies boven aan het Windows 10 naar een nieuwere versie upgraden.

## <a name="customizable-branding-for-software-center-dialogs"></a>Aanpasbare huisstijl voor Software Center-dialoogvensters

Aangepaste huisstijl voor Software Center is geïntroduceerd in versie 1602 van Configuration Manager. In Technical Preview-versie 1607 is die huisstijl nu uitgebreid naar alle bijbehorende dialoogvensters en Taakbalkmeldingen voor een consistente ervaring voor gebruikers van Software Center.

### <a name="try-it-out"></a>Probeer het nu!

Aangepaste huisstijl voor Software Center is toegepast volgens de volgende regels:

1. Als de siteserverrol van Application Catalog-website-punt is niet geïnstalleerd, wordt de Software Center de organisatienaam die is opgegeven weergegeven in de **Computeragent** clientinstelling **weergegeven organisatienaam in Software Center**. Zie voor instructies [het configureren van clientinstellingen](../../core/clients/deploy/configure-client-settings.md).

2. Als de siteserverrol van Application Catalog-website-punt is geïnstalleerd, wordt Software Center weergegeven de naam van de organisatie en de kleur die is opgegeven in de Application Catalog-website-punt eigenschappen van de siteserverrol. Zie voor meer informatie [configuratieopties voor het Application Catalog-websitepunt](../../core/servers/deploy/configure/configuration-options-for-site-system-roles.md#BKMK_ApplicationCatalog_Website).

3. Als een Microsoft Intune-abonnement is geconfigureerd en is verbonden met de Configuration Manager-omgeving, wordt Software Center weergegeven de naam van de organisatie, kleur en het bedrijfslogo opgegeven in de eigenschappen van de Intune-abonnement. Zie voor meer informatie [configureren van de Microsoft Intune-abonnement](/mdm/deploy-use/configure-intune-subscription).

## <a name="use-the-same-network-adapter-for-multiple-pxe-initiated-deployments"></a>Gebruik dezelfde netwerkadapter voor meerdere PXE geïnitieerde implementaties
In Technical Preview-versie 1607, wanneer u een Ethernet-adapter met een installatiekopie van meerdere apparaten (zoals een USB-ethernet-netwerkadapter die u voor meerdere apparaten gebruikt), kunt u een nieuwe instelling waarmee u hardware-id's voor de Ethernet-adapters opgeven. Configuration Manager negeert de hardware-id's in de lijst bij het uitvoeren van een PXE-installatie en voor de clientregistratie.

Zie voor meer informatie over dit probleem de [Configuration Manager OSD Support-teamblog](https://blogs.technet.microsoft.com/system_center_configuration_manager_operating_system_deployment_support_blog/2015/08/27/reusing-the-same-nic-for-multiple-pxe-initiated-deployments-in-system-center-configuration-manger-osd/).  

### <a name="enable-the-feature-to-manage-duplicate-hardware-identifiers"></a>De functie voor het beheren van dubbele hardware-id's inschakelen  
1. Ga in de Configuration Manager-console naar **beheer** > **overzicht** > **Cloudservices** > **Updates en onderhoud** > **functies**.
2. Selecteer in het weergavepaneel **beheren dubbele hardware-id's**.
3. Op de **Start** tabblad, in de **functies** groep, klikt u op **inschakelen**.

### <a name="add-hardware-identifiers-for-configuration-manager-to-ignore"></a>Toevoegen van hardware-id's voor Configuration Manager te negeren  
1. Ga in de Configuration Manager-console naar **beheer** > **overzicht** > **siteconfiguratie** > **Sites**.
2. Klik op **Hiërarchie-instellingen** op het tabblad **Start** , in de groep **Sites**.
3. Ga naar de **goedkeuring van Client en conflicterende Records** tabblad.
4. Klik op **toevoegen** in de **dubbele hardware-id's** sectie voor het toevoegen van nieuwe hardware-id's.
