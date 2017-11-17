---
title: Hybride MDM-gebruikers en apparaten migreren naar Intune standalone
titleSuffix: Configuration Manager
description: Informatie over het migreren van hybride MDM-gebruikers en apparaten naar Intune in Azure.
keywords: 
author: dougeby
manager: angrobe
ms.date: 09/12/2017
ms.topic: article
ms.prod: configmgr-hybrid
ms.service: 
ms.technology: 
ms.assetid: 1dd696ce-3e46-4dfa-a76d-592fe0f0320e
ms.openlocfilehash: a6e430248fdeedd310087c9a32c6d69ca1864a09
ms.sourcegitcommit: 986fc2d54f7c5fa965fd4df42f4db4ecce6b79cb
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 11/17/2017
---
# <a name="migrate-hybrid-mdm-users-and-devices-to-intune-standalone"></a>Hybride MDM-gebruikers en apparaten migreren naar Intune standalone

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*    

Wanneer u hebt besloten dat u bent klaar om te beginnen met het migreren van hybride MDM (Intune geïntegreerd met Configuration Manager) voor een alleen-ervaring met behulp van Intune in Azure, dit is is het artikel bedoeld voor u. Als u nog steeds niet zeker weet, raadpleegt u [kiezen tussen Microsoft Intune standalone en hybride beheer van mobiele apparaten met System Center Configuration Manager](https://docs.microsoft.com/sccm/mdm/understand/choose-between-standalone-intune-and-hybrid-mobile-device-management). 

U kunt beginnen met het migreren naar Intune standalone met behulp van een gefaseerde benadering waarmee u voor het testen van een kleine subset van gebruikers en apparaten, terwijl de meeste van uw gebruikers en apparaten worden nog steeds beheerd met hybride MDM Vervolgens, nadat u Intune-functionaliteit controleren, u meer gebruikers migreren naar Intune beginnen kunt.    

De volgende onderwerpen bevatten de stappen voor uw gebruikers migreren naar Intune standalone met behulp van een gefaseerde benadering.    
  
1.  [Configuration Manager-gegevens importeren in Microsoft Intune](migrate-import-data.md)   
    Het hulpprogramma voor gegevensimport Intune verzamelt gegevens over de objecten die u in de Configuration Manager-hiërarchie selecteert, vindt u gedetailleerde informatie over de objecten die u kunt selecteren voor het importeren en informatie over waarom een object kan niet worden geïmporteerd en kunt die u importeert geselecteerde objecten in uw Microsoft Intune-tenant. Tijdens deze stap optioneel is, bespaart u veel tijd door automatisering van het proces om objecten van Configuration Manager met Intune opnieuw te maken. 
2.  [Intune voorbereiden voor gebruikersmigratie van de](migrate-prepare-intune.md)    
    Geïmporteerde objecten van Configuration Manager, nieuwe objecten maken, AAD-groepen maken en worden toegewezen aan deze groepen maken, valideren installeren NDES en de Exchange-connectors, enzovoort. Wanneer u de stappen en de migratie naar de zelfstandige versie van Intune start, moet het worden transparant voor uw gebruikers.  
3.  [Wijzigen van de MDM-instantie voor specifieke gebruikers (gemengd MDM-instantie)](migrate-mixed-authority.md)    
    Een gemengde MDM-instantie in dezelfde tenant configureren met behulp van sommige gebruikers worden beheerd in Intune en terwijl alle andere apparaten blijven worden beheerd met hybride MDM (Intune geïntegreerd met Configuration Manager). U kunt testen of Intune-functionaliteit werkt zoals verwacht op het apparaat voor een kleine subset van gebruikers voordat u extra gebruikers migreren. 
4.  [Wijzigen van uw MDM-instantie zelfstandige versie van Intune](change-mdm-authority.md)     
    Wijzig uw MDM-instantie op tenantniveau uit Configuration Manager in Intune. Alle resterende gebruikers en apparaten worden gemigreerd naar de zelfstandige versie van Intune. U kunt uw MDM-instantie op tenantniveau wordt wijzigen nadat u Intune-functionaliteit in de vorige stap grondig hebt getest en hebben waarschijnlijk gemigreerd de meeste of alle gebruikers.

<!--
The following provides a typical workflow for migrating users from hybrid MDM to Intune standalone:
1.  Admin runs the Microsoft Intune Data Importer Tool, selecting which objects and assignments to import. Selected objects are imported into Intune standalone.
    1. Some objects cannot be imported because they contain settings the tool does not understand or setting that are not available in Intune standalone.
    2. Assignments are migrated. However, only if the collection an object was targeted to is based on a single Active Directory (AD) security group and the same group exists in Azure Active Directory (AAD).
    > [!Note]    
    > If you want, you can skip this step and create the objects that you want directly in Intune in the Azure portal without running the Intune Data Importer Tool. 
2.  Admin logs into the Intune on Azure portal
    1. Creates any additional objects required for their organization that were not imported by the Microsoft Intune Data Importer tool.
    2. Creates any required AAD groups and makes any additional assignments for each object to AAD groups.
    3. Installs the NDES connector on an on-premises server if using SCEP or PFX certificate deployment.
    4. Installs the Exchange connector on an on-premises server if using conditional access. 
3.  Admin ensures that all existing Intune users in their organization have an Intune license assigned to them using AAD or the Office administrator portal.
4.  Admin selects some test users to migrate to Intune standalone and removes them from the collection associated with the Intune subscription in Configuration Manager.
5.  Once removed from the collection, the user and all devices are managed by Intune in the Azure portal. Remaining users and devices continue to be managed by hybrid mobile device management in Configuration Manager. 
6.  Admin validates that things are working as expected on the device and moves more users to Intune standalone by removing them from the collection associated with the Intune subscription in Configuration Manager.
7.  Once the admin is comfortable with the functionality in Intune standalone, they can move the rest of their users and devices by switching their MDM authority to Intune standalone. This can be done by removing the Intune subscription from SCCM and choosing to change the MDM authority. Tenant level policies will be automatically migrated to Intune standalone, all objects and assignments in Intune standalone will remain, and devices will not be required to re-enroll.
-->