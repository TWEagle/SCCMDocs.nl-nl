---
title: On-premises Mobile Device Management (MDM) | Microsoft-documenten
description: Informatie over het beheer van lokale mobiele apparaten, een oplossing voor Apparaatbeheer in System Center Configuration Manager.
ms.custom: na
ms.date: 03/05/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-hybrid
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 497c05c7-fe9f-4b88-983b-1c5b3d59308e
caps.latest.revision: 8
author: Mtillman
ms.author: mtillman
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 6424fb07802b62820b4dc78a58ab30d3b956abef
ms.openlocfilehash: 7b96c4d4d87aa150eacc5d7d20710f5d2199e48a
ms.contentlocale: nl-nl
ms.lasthandoff: 05/17/2017


---
# <a name="on-premises-mobile-device-management-mdm-in-system-center-configuration-manager"></a>On-premises mobiel Apparaatbeheer (MDM) in System Center Configuration Manager

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*

System Center Configuration Manager op\-premises beheer van mobiele apparaten is een oplossing voor Apparaatbeheer die afhankelijk zijn van de ingebouwde beheermogelijkheden van apparaatbesturingssysteem (op basis van de standaard Open Mobile Alliance Device Management of OMA-DM) tijdens het gebruik van een onderneming Configuration Manager-infrastructuur te beheren en onderhouden van de apparaten. Op\-premises beheer van mobiele apparaten vereist Microsoft Intune voor het instellen van de beheerfunctionaliteit alleen nodig voor het abonnement (en op tijdstippen om te helpen kennis van apparaten in te checken op beleidswijzigingen), maar het niet wordt gebruikt voor het beheren van apparaten of gegevens over te slaan.  

 ![Op\-lokale conceptuele](media/On-premises-conceptual.png)  

 Op\-lokale beheer van mobiele apparaten verschilt van de Microsoft Intune, die ook is afhankelijk van ingebouwde OMA-DM-mogelijkheden, maar alle van de beheerfuncties via cloudservices worden geleverd.  Op\-lokale beheer van mobiele apparaten ook verschilt van de client gebaseerde oplossing traditioneel aangeboden door Configuration Manager in die is gebaseerd op vergelijkbare enterprise-infrastructuur, maar niet afzonderlijk gebruiken clientsoftware hebt geïnstalleerd op computers en apparaten die deze beheert.  

 De volgende tabel bevat de voordelen en nadelen van op\-premises beheer van mobiele apparaten in ten opzichte van traditionele op client gebaseerde management:  

|Voordelen|Nadelen|  
|----------------|-------------------|  
|**Vereenvoudigde infrastructuur** : minder sitesysteemrollen vereist.<br /><br /> **Gemakkelijker te onderhouden** -omdat beheerfunctionaliteit ingebouwd in het besturingssysteem van het apparaat is, nieuwe versies van de clientsoftware zijn niet vereist wanneer nieuwe functies in de Configuration Manager system binnenkomen.<br /><br /> **On-premises** : alle beheertaken worden on-premises uitgevoerd en alle gegevens worden on-premises bewaard.|**Minder clientbeheerfunctionaliteit** : geen orchestration, softwaremeter, integratie van derden, takenreeksen of Software Center-ondersteuning.<br /><br /> **Beperkte ondersteuning voor apparaat** - momenteel op\-lokale beheer van mobiele apparaten ondersteunt alleen apparaten met Windows 10 en Windows 10 Mobile.|  

 De volgende onderwerpen vindt u informatie die u kunt gebruiken om te plannen, voorbereiden en apparaten registreren voor op\-premises beheer van mobiele apparaten:  

-   [On-premises beheer van mobiele apparaten in System Center Configuration Manager plannen](../plan-design/plan-on-premises-mdm.md)  

     Informatie over wat u moet overwegen bij het instellen van de Configuration Manager-infrastructuur en de planning voor de inschrijving van apparaten in op\-premises beheer van mobiele apparaten.  

-   [Voorbereidende stappen voor het On-premises mobiele apparaten beheren in System Center Configuration Manager](../get-started/preparation-steps-for-on-premises-mdm.md)  

     Meer informatie over het ophalen van de Configuration Manager system gereed voor op\-lokale beheer van mobiele apparaten door het instellen van de Microsoft Intune-abonnement, certificaten instellen voor het installeren van sitesysteemrollen en apparaatinschrijving instellen.  

-   [Apparaten registreren voor On-premises mobiele apparaten beheren in System Center Configuration Manager](../deploy-use/enroll-devices-on-premises-mdm.md)  

     Meer informatie over hoe inschrijving plaatsvindt, hoe gebruikers hun eigen apparaten kunnen inschrijven en hoe apparaten met een inschrijvingspakket bulksgewijs kunnen worden ingeschreven.  

