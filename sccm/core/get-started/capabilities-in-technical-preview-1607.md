---
title: Mogelijkheden in Technical Preview 1607 Configuration Manager
description: Meer informatie over functies die beschikbaar zijn in de Technical Preview voor System Center Configuration Manager, versie 1607.
ms.custom: na
ms.date: 01/23/2017
ms.prod: configuration-manager
ms.technology:
- configmgr-other
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 2bb69547-3370-4860-96b0-7fb600c56482
caps.latest.revision: 11
author: Brenduns
ms.author: brenduns
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 1b9e49da1a5bbfca93fe683b82d2c0056a22cc1f
ms.openlocfilehash: 4717e0f8eef01501fb5b5790e855c476c1ca4590
ms.contentlocale: nl-nl
ms.lasthandoff: 05/17/2017

---
# <a name="capabilities-in-technical-preview-1607-for-system-center-configuration-manager"></a>Mogelijkheden in Technical Preview 1607 voor System Center Configuration Manager

*Van toepassing op: System Center Configuration Manager (technische Preview)*

Dit artikel worden de functies die beschikbaar in de Technical Preview voor System Center Configuration Manager, versie 1607 zijn geïntroduceerd. U kunt deze versie om te werken en nieuwe mogelijkheden toevoegen aan uw technische preview van Configuration Manager site installeren.      Voordat u deze versie van de technische preview installeert, leest u de inleidende onderwerp [Technical Preview voor System Center Configuration Manager](../../core/get-started/technical-preview.md), om meer vertrouwd raken met algemene vereisten en beperkingen voor het gebruik van een technische preview hoe tussen versies en hoe u feedback geven over de functies in een technische preview bijwerken.    


**De volgende zijn nieuwe functies die u met deze versie kunt uitproberen.**  

## <a name="dmp_edition"></a>Verbeteringen in de editie van Windows 10 bijwerken beleid

In deze release zijn de volgende verbeteringen aangebracht in dit beleid:

* U kunt de upgrade beleid edition nu gebruiken met Windows 10-computers waarop de Configuration Manager client naast Windows 10-computers zijn ingeschreven met Microsoft Intune.
* U kunt upgraden van Windows 10 Professional met een van de platforms die compatibel met de hardware zijn in de wizard.

[Meer informatie over de Windows 10 Edition Upgrade-beleid](/sccm/compliance/deploy-use/upgrade-windows-version)

### <a name="try-it-out"></a>Probeer het nu!

1. Gebruik de informatie in de [bestaande edition upgrade beleid onderwerp](/sccm/compliance/deploy-use/upgrade-windows-version) om een upgrade editie-beleid te maken.
2. Dit beleid implementeren op een Windows 10-computer waarop de Configuration Manager-client wordt uitgevoerd.
Als het beleid een bepaalde Windows-computer bereikt, wordt de computer binnen twee uur opnieuw opgestart om de upgrade toe te passen. U kan momenteel niet opnieuw opstarten onderdrukken. Zorg ervoor dat u informeren over alle gebruikers waarvoor u het beleid implementeert, of het beleid om uit te voeren buiten de gebruikers plannen werkuren.

### <a name="known-issue-with-this-release"></a>Bekend probleem in deze release
In Configuration Manager-clientinstellingen, ziet u instellingen voor **Edition Upgrade**. Deze instellingen zijn in deze release niet functioneel. Gebruik de bovenstaande instructies Windows 10 bijwerken naar een nieuwere versie.

## <a name="customizable-branding-for-software-center-dialogs"></a>Aanpasbare huisstijl voor Software Center-dialoogvensters

Aangepaste huisstijl voor het Software Center is ingevoerd in Configuration Manager versie 1602. In technische voorbeeldversie 1607 die branding nu uitgebreid tot alle bijbehorende dialoogvensters en Taakbalkmeldingen om een consistente ervaring voor gebruikers in Software Center.

### <a name="try-it-out"></a>Probeer het nu!

Aangepaste huisstijl voor het Software Center wordt toegepast volgens de volgende regels:

1. Als de Application Catalog-website-puntrol siteserver niet is geïnstalleerd, wordt de Software Center, u de naam van de organisatie opgegeven ziet in de **Computeragent** clientinstelling **weergegeven organisatienaam in Software Center**. Zie voor instructies [het configureren van clientinstellingen](../../core/clients/deploy/configure-client-settings.md).

2. Als de Application Catalog-website-puntrol siteserver is geïnstalleerd, wordt klikt u vervolgens Software Center weergegeven de naam van de organisatie en kleur die is opgegeven in de Application Catalog-website site server-roleigenschappen. Zie voor meer informatie [configuratieopties voor de Application Catalog-websitepunt](../../core/servers/deploy/configure/configuration-options-for-site-system-roles.md#BKMK_ApplicationCatalog_Website).

3. Als een Microsoft Intune-abonnement is geconfigureerd en met de Configuration Manager-omgeving verbonden, wordt klikt u vervolgens Software Center weergegeven de naam van de organisatie, kleur en het bedrijfslogo opgegeven in de eigenschappen van de Intune-abonnement. Zie voor meer informatie [configureren van de Microsoft Intune-abonnement](/mdm/deploy-use/configure-intune-subscription).

## <a name="use-the-same-network-adapter-for-multiple-pxe-initiated-deployments"></a>Gebruik dezelfde netwerkadapter voor meerdere PXE geïnitieerde implementaties
Technische Preview-versie 1607, wanneer u een Ethernet-adapter met een installatiekopie te maken meerdere apparaten (zoals een Ethernet-USB-adapter die u op meerdere apparaten gebruikt), kunt u een nieuwe instelling waarmee u hardware-id's voor de Ethernet-adapters opgeven. Configuration Manager negeert de hardware-id's in de lijst bij het uitvoeren van een PXE-installatie en voor de clientregistratie.

Zie voor meer informatie over dit probleem, de [Configuration Manager OSD Support-teamblog](https://blogs.technet.microsoft.com/system_center_configuration_manager_operating_system_deployment_support_blog/2015/08/27/reusing-the-same-nic-for-multiple-pxe-initiated-deployments-in-system-center-configuration-manger-osd/).  

### <a name="enable-the-feature-to-manage-duplicate-hardware-identifiers"></a>De functie voor het beheren van dubbele hardware-id's inschakelen  
1. Ga in de Configuration Manager-console naar **beheer** > **overzicht** > **Cloudservices** > **Updates en onderhoud** > **functies**.
2. Selecteer in het weergavepaneel **dubbele hardware-id's beheren**.
3. Op de **Start** tabblad, in de **functies** groep, klikt u op **inschakelen**.

### <a name="add-hardware-identifiers-for-configuration-manager-to-ignore"></a>Toevoegen van hardware-id's voor Configuration Manager moeten worden genegeerd  
1. Ga in de Configuration Manager-console naar **beheer** > **overzicht** > **siteconfiguratie** > **Sites**.
2. Klik op **Hiërarchie-instellingen** op het tabblad **Start** , in de groep **Sites**.
3. Ga naar de **goedkeuring van Client en conflicterende Records** tabblad.
4. Klik op **toevoegen** in de **dubbele hardware-id's** sectie toevoegen van nieuwe hardware-id's.

