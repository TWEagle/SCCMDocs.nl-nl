---
title: Functies en mogelijkheden | Microsoft-documenten
description: Meer informatie over de primaire beheerfuncties van System Center Configuration Manager.
ms.custom: na
ms.date: 12/29/2016
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 5d388399-07ca-431c-a9b2-56c69771aa87
caps.latest.revision: 18
caps.handback.revision: 0
author: Brenduns
ms.author: brenduns
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 53b27dcb5c8bb670556fe4cee9e990619a9a63e9
ms.openlocfilehash: 4691f43dccdf73936107f4635321897b9779bead
ms.contentlocale: nl-nl
ms.lasthandoff: 05/17/2017


---
# <a name="features-and-capabilities-of-system-center-configuration-manager"></a>Functies en mogelijkheden van System Center Configuration Manager

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*

Hier volgen de primaire beheerfuncties van System Center Configuration Manager. Elke functie heeft haar eigen vereisten en de mogelijkheden die u wilt gebruiken mogelijk van invloed op het ontwerp en de implementatie van de Configuration Manager-hiërarchie. Als u software implementeren op apparaten in uw hiërarchie wilt, moet u bijvoorbeeld de distributie-puntsitesysteemrol installeren.  

 Zie voor meer informatie over het plannen en installeren van Configuration Manager ter ondersteuning van deze beheerfuncties in uw omgeving [voorbereiden voor System Center Configuration Manager](../../../core/plan-design/get-ready.md).  

 **Toepassingsbeheer**  

 Voorziet in een set hulpprogramma's en resources waarmee u toepassingen kunt maken, implementeren en controleren voor verschillende apparaten die u beheert. Daarnaast wordt in Configuration Manager biedt hulpprogramma's waarmee u de gegevens van uw bedrijf in hun apps beveiligen. Zie [inleiding op Toepassingsbeheer](/sccm/apps/understand/introduction-to-application-management).

 **Toegang tot bedrijfsbronnen**  

 Voorziet in een set hulpprogramma's en resources waarmee u gebruikers binnen uw organisatie toegang kunt geven tot gegevens en toepassingen van externe locaties. Deze hulpprogramma's omvatten Wi-Fi-profielen, VPN-profielen, certificaatprofielen, en voorwaardelijke toegang tot Exchange en SharePoint online. Zie [beveiligen gegevens en site-infrastructuur met System Center Configuration Manager](../../../protect/understand/protect-data-and-site-infrastructure.md) en [toegang tot services in System Center Configuration Manager beheren](../../../protect/deploy-use/manage-access-to-services.md).  

 **Instellingen voor naleving**  

 Voorziet in een set hulpprogramma's en resources die u helpen kunnen bij het beoordelen, bijhouden en herstellen van de conformiteit van configuraties van clientapparaten binnen de onderneming. Bovendien kunt u instellingen voor naleving gebruiken voor het configureren van een bereik aan functies en beveiligingsinstellingen op apparaten die u beheert. Zie [Controleer apparaatcompatibiliteit met System Center Configuration Manager](../../../compliance/understand/ensure-device-compliance.md).  

 **Endpoint Protection**  

 Voorziet in beheer op het gebied van beveiliging, antimalware en Windows Firewall voor computers binnen uw onderneming. Zie [Endpoint Protection in System Center Configuration Manager](../../../protect/deploy-use/endpoint-protection.md).  

 **Inventarisatie**  

 Voorziet in een set hulpprogramma's kunt identificeren en controleren van de activa:  

-   **Hardware-inventaris**: Verzamelt gedetailleerde informatie over de hardware van apparaten in uw onderneming. Zie [Inleiding tot de hardware-inventaris in System Center Configuration Manager](../../../core/clients/manage/inventory/introduction-to-hardware-inventory.md).  

-   **Software-inventaris**: Verzamelt en rapporteert informatie over de bestanden die zijn opgeslagen op clientcomputers in uw organisatie. Zie [Inleiding tot software-inventaris in System Center Configuration Manager](../../../core/clients/manage/inventory/introduction-to-software-inventory.md).  

-   **Asset Intelligence**: Voorziet in hulpprogramma's voor het verzamelen van inventarisgegevens en het gebruik van softwarelicenties in uw bedrijf controleren. Zie [Inleiding tot Asset Intelligence in System Center Configuration Manager](../../../core/clients/manage/asset-intelligence/introduction-to-asset-intelligence.md).  

**Beheer van mobiele apparaten met Microsoft Intune**  

 U kunt de Configuration Manager gebruiken voor het beheren van iOS, Android (inclusief Samsung KNOX Standard), Windows Phone-en Windows-apparaten met behulp van de Microsoft Intune-service via Internet.

 Hoewel u de Intune-service, worden beheertaken voltooid met behulp van de service verbinding puntsitesysteemrol beschikbaar is via de Configuration Manager-console. Zie [hybride mobiel Apparaatbeheer (MDM) met System Center Configuration Manager en Microsoft Intune](../../../mdm/understand/hybrid-mobile-device-management.md).  

 **Beheer van mobiele apparaten on-premises**  

 Schrijft en pc's en mobiele apparaten beheert met behulp van de lokale Configuration Manager-infrastructuur en het beheer functionaliteit ingebouwd in de apparaatplatforms (en niet vertrouwen op een afzonderlijk geïnstalleerde Configuration Manager-client). Biedt momenteel ondersteuning voor het beheren van Windows 10 Enterprise- en Windows 10 Mobile-apparaten. Zie [mobiele apparaten beheren met on-premises infrastructuur in System Center Configuration Manager](../../../mdm/understand/manage-mobile-devices-with-on-premises-infrastructure.md).  

 **Implementatie van besturingssysteem**  

 Voorziet in een hulpprogramma voor het maken van installatiekopieën van besturingssystemen. U kunt deze installatiekopieën vervolgens gebruiken voor de besturingssystemen implementeren op computers, met behulp van PXE-opstartbewerking of opstartbare media zoals een CD-set, DVD of USB-sticks. Houd er rekening mee dat dit van toepassing op computers die worden beheerd door Configuration Manager, evenals de niet-beheerde computers. Zie [Inleiding tot implementatie van besturingssystemen in System Center Configuration Manager](../../../osd/understand/introduction-to-operating-system-deployment.md).  

 **Energiebeheer**  

 Voorziet in een set hulpprogramma's en resources waarmee u het energieverbruik van clientcomputers in het bedrijf kunt beheren en controleren. Zie [Inleiding tot energiebeheer in System Center Configuration Manager](../../../core/clients/manage/power/introduction-to-power-management.md).  

 **Query 's**  

 Voorziet in een hulpprogramma voor het verkrijgen van informatie over resources in uw hiërarchie en informatie over inventarisgegevens en statusberichten. U kunt deze informatie vervolgens gebruiken voor rapportage of voor het definiëren van verzamelingen apparaten of gebruikers voor software-implementatie en configuratie-instellingen. Zie [Inleiding in query's in System Center Configuration Manager](../../../core/servers/manage/introduction-to-queries.md).  

 **Profielen voor externe verbindingen**  

 Voorziet in een set hulpprogramma's en bronnen om u te maken, implementeren en controleren van instellingen voor externe verbindingen met apparaten binnen uw organisatie. Deze instellingen implementeert, kan de moeite door gebruikers verbinding maken met hun computers op het bedrijfsnetwerk. Zie [werken met profielen voor externe verbindingen in System Center Configuration Manager](/sccm/compliance/deploy-use/create-remote-connection-profiles).  

 **Items voor gebruikersgegevens en profielen configuratie**  

 Gebruiker en profielen configuratie-items in Configuration Manager bevatten instellingen die Mapomleiding, offlinebestanden en zwervende profielen op computers met Windows 8 en hoger voor gebruikers in uw hiërarchie kunt beheren. Zie [werken met profielen configuration items voor gebruikersgegevens en in System Center Configuration Manager](/sccm/compliance/deploy-use/create-user-data-and-profiles-configuration-items).  

 **Beheer op afstand**  

 Biedt hulpprogramma's voor het extern beheren van clientcomputers van Configuration Manager-console. Zie [Inleiding tot beheer op afstand in System Center Configuration Manager](../../../core/clients/manage/remote-control/introduction-to-remote-control.md).  

 **Rapportage**  

 Biedt een aantal hulpprogramma's en resources waarmee u de Geavanceerde rapportagemogelijkheden van SQL Server Reporting Services van de Configuration Manager-console gebruiken. Zie [Inleiding tot rapportage in System Center Configuration Manager](../../../core/servers/manage/introduction-to-reporting.md).  

 **Softwarelicentiecontrole**  

 Voorziet in hulpprogramma's om te controleren en verzamelen van gegevens over softwaregebruik van Configuration Manager-clients. Zie [Het app-gebruik in System Center Configuration Manager controleren met softwaremeter](../../../apps/deploy-use/monitor-app-usage-with-software-metering.md).  

 **Software-updates**  

 Voorziet in een set hulpprogramma's en resources waarmee u software-updates in het bedrijf kunt maken, implementeren en controleren. Zie [Inleiding tot software-updates in System Center Configuration Manager](/sccm/sum/understand/software-updates-introduction).  

