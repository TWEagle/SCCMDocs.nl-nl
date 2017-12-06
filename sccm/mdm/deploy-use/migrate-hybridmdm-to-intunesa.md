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
ms.openlocfilehash: 30474f6dd0216078ab1ac1f4bd9f5044f1b174f0
ms.sourcegitcommit: 8c6e9355846ff6a73c534c079e3cdae09cf13c45
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/06/2017
---
# <a name="migrate-hybrid-mdm-users-and-devices-to-intune-standalone"></a>Hybride MDM-gebruikers en apparaten migreren naar Intune standalone

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*    

Wanneer u hebt besloten dat u bent klaar om te beginnen met het migreren van hybride MDM (Intune geïntegreerd met Configuration Manager) voor een alleen-ervaring met behulp van Intune in Azure, dit is is het artikel bedoeld voor u. Als u nog steeds niet zeker weet, raadpleegt u [kiezen tussen Microsoft Intune standalone en hybride beheer van mobiele apparaten met System Center Configuration Manager](https://docs.microsoft.com/sccm/mdm/understand/choose-between-standalone-intune-and-hybrid-mobile-device-management). 

U kunt beginnen met het migreren naar Intune standalone met behulp van een gefaseerde benadering waarmee u voor het testen van een kleine subset van gebruikers en apparaten, terwijl de meeste van uw gebruikers en apparaten worden nog steeds beheerd met hybride MDM Vervolgens, nadat u Intune-functionaliteit controleren, u meer gebruikers migreren naar Intune beginnen kunt.    

De volgende onderwerpen bevatten de stappen voor uw gebruikers migreren naar Intune standalone met behulp van een gefaseerde benadering.    
  
1.  [Configuration Manager-gegevens importeren in Microsoft Intune](migrate-import-data.md)   
    Het hulpprogramma voor gegevensimport Intune verzamelt gegevens over de objecten die u in de Configuration Manager-hiërarchie selecteert, vindt u gedetailleerde informatie over de objecten die u kunt selecteren voor het importeren en informatie over waarom een object kan niet worden geïmporteerd en kunt die u importeert geselecteerde objecten in uw Microsoft Intune-tenant. Tijdens deze stap optioneel is, kan deze u veel tijd besparen door automatisering van het proces om objecten van Configuration Manager met Intune opnieuw te maken. 
2.  [Intune voorbereiden voor gebruikersmigratie van de](migrate-prepare-intune.md)    
    Geïmporteerde objecten van Configuration Manager, nieuwe objecten maken, AAD-groepen maken en worden toegewezen aan deze groepen maken, valideren installeren NDES en de Exchange-connectors, enzovoort. Wanneer u de stappen en de migratie naar de zelfstandige versie van Intune start, moet het worden transparant voor uw gebruikers.  
3.  [Wijzigen van de MDM-instantie voor specifieke gebruikers (gemengd MDM-instantie)](migrate-mixed-authority.md)    
    Een gemengde MDM-instantie in dezelfde tenant configureren met behulp van sommige gebruikers worden beheerd in Intune en terwijl alle andere apparaten blijven worden beheerd met hybride MDM (Intune geïntegreerd met Configuration Manager). U kunt testen of Intune-functionaliteit werkt zoals verwacht op het apparaat voor een kleine subset van gebruikers voordat u extra gebruikers migreren. 
4.  [Wijzigen van uw MDM-instantie zelfstandige versie van Intune](change-mdm-authority.md)     
    Wijzig uw MDM-instantie op tenantniveau uit Configuration Manager in Intune. Alle resterende gebruikers en apparaten worden gemigreerd naar de zelfstandige versie van Intune. U kunt uw MDM-instantie op tenantniveau wordt wijzigen nadat u Intune-functionaliteit in de vorige stap grondig hebt getest en hebben waarschijnlijk gemigreerd de meeste of alle gebruikers.