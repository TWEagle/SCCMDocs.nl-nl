---
title: On-premises Mobile Device Management (MDM) | Microsoft Docs
description: Meer informatie over On-premises Mobile Device Management, een oplossing voor Apparaatbeheer in System Center Configuration Manager.
ms.custom: na
ms.date: 03/05/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: configmgr-hybrid
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 497c05c7-fe9f-4b88-983b-1c5b3d59308e
caps.latest.revision: "8"
author: Mtillman
ms.author: mtillman
manager: angrobe
ms.openlocfilehash: 7b96c4d4d87aa150eacc5d7d20710f5d2199e48a
ms.sourcegitcommit: 51fc48fb023f1e8d995c6c4eacfda7dbec4d0b2f
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 08/07/2017
---
# <a name="on-premises-mobile-device-management-mdm-in-system-center-configuration-manager"></a>On-premises Mobile Device Management (MDM) in System Center Configuration Manager

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*

System Center Configuration Manager op\-premises Mobile Device Management is een oplossing voor Apparaatbeheer die afhankelijk van de ingebouwde beheermogelijkheden van besturingssystemen van apparaten (op basis van de standaard Open Mobile Alliance Device Management of OMA DM is) tijdens het gebruik van een onderneming Configuration Manager-infrastructuur te beheren en onderhouden van de apparaten. Op\-premises Mobile Device Management is vereist voor Microsoft Intune voor het instellen van de mogelijkheid tot beheer, maar alleen nodig voor het abonnement (en op tijdstippen om u te helpen kennis van apparaten in te checken op beleidswijzigingen), maar dit niet wordt gebruikt voor het beheren van apparaten of gegevens over te slaan.  

 ![Op\-premises conceptuele](media/On-premises-conceptual.png)  

 Op\-premises Mobile Device Management verschilt van de Microsoft Intune, die ook is afhankelijk van ingebouwde OMA DM-mogelijkheden, maar alle beheerfuncties worden geleverd via cloudservices.  Op\-premises Mobile Device Management verschilt ook van de client-gebaseerde beheeroplossing traditioneel door Configuration Manager worden aangeboden in dat is afhankelijk van soortgelijke ondernemingsinfrastructuur, maar niet afzonderlijk gebruikt clientsoftware hebt geïnstalleerd op de computers en apparaten beheert.  

 De volgende tabel bevat de voordelen en nadelen van op\-premises Mobile Device Management in vergelijking met traditionele op clients gebaseerde beheer:  

|Voordelen|Nadelen|  
|----------------|-------------------|  
|**Vereenvoudigde infrastructuur** : minder sitesysteemrollen vereist.<br /><br /> **Gemakkelijker te onderhouden** -omdat de beheerfunctionaliteit is ingebouwd in het besturingssysteem van het apparaat, nieuwe versies van de clientsoftware zijn niet vereist als de nieuwe functies in de Configuration Manager-systeem binnenkomen.<br /><br /> **On-premises** : alle beheertaken worden on-premises uitgevoerd en alle gegevens worden on-premises bewaard.|**Minder clientbeheerfunctionaliteit** : geen orchestration, softwaremeter, integratie van derden, takenreeksen of Software Center-ondersteuning.<br /><br /> **Beperkte Apparaatondersteuning** - momenteel aanwezig is op\-premises Mobile Device Management biedt alleen ondersteuning voor apparaten met Windows 10 en Windows 10 Mobile.|  

 De volgende onderwerpen bevatten informatie die u kunt gebruiken om te plannen, voorbereiden en -apparaten inschrijven voor op\-premises Mobile Device Management:  

-   [On-premises Mobile Device Management in System Center Configuration Manager plannen](../plan-design/plan-on-premises-mdm.md)  

     Meer informatie over wat u moet overwegen bij het instellen van de Configuration Manager-infrastructuur en planning voor apparaatinschrijving in op\-premises Mobile Device Management.  

-   [Voorbereidingsstappen voor On-premises Mobile Device Management in System Center Configuration Manager](../get-started/preparation-steps-for-on-premises-mdm.md)  

     Meer informatie over het gebruiksklaar maken van het systeem Configuration Manager op\-premises Mobile Device Management door de Microsoft Intune-abonnement in te stellen, certificaten in te stellen, sitesysteemrollen installeren en instellen van apparaatinschrijving.  

-   [Apparaten inschrijven voor On-premises Mobile Device Management in System Center Configuration Manager](../deploy-use/enroll-devices-on-premises-mdm.md)  

     Meer informatie over hoe inschrijving plaatsvindt, hoe gebruikers hun eigen apparaten kunnen inschrijven en hoe apparaten met een inschrijvingspakket bulksgewijs kunnen worden ingeschreven.  
