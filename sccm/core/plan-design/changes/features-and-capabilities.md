---
title: Functies en mogelijkheden
titleSuffix: Configuration Manager
description: Meer informatie over de primaire beheerfuncties van System Center Configuration Manager.
ms.custom: na
ms.date: 12/29/2016
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 5d388399-07ca-431c-a9b2-56c69771aa87
caps.latest.revision: "18"
caps.handback.revision: "0"
author: mstewart
ms.author: mstewart
manager: angrobe
ms.openlocfilehash: a247181f4e1ec634291d09a7e30b83496139bcd3
ms.sourcegitcommit: 7fe45ff75f05f7cc03ad021db8119791abe18049
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/01/2017
---
# <a name="features-and-capabilities-of-system-center-configuration-manager"></a>Functies en mogelijkheden van System Center Configuration Manager

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*

Hieronder vindt u de primaire beheerfuncties van System Center Configuration Manager. Elke functie heeft haar eigen vereisten en de mogelijkheden die u wilt gebruiken mogelijk van invloed op het ontwerp en de implementatie van uw Configuration Manager-hiërarchie. Bijvoorbeeld, als u software implementeren op apparaten in uw hiërarchie wilt, moet u de sitesysteemrol distributiepunt installeren.  

 Zie voor meer informatie over het plannen en installeren van Configuration Manager ter ondersteuning van deze beheerfuncties in uw omgeving [voorbereiden voor System Center Configuration Manager](../../../core/plan-design/get-ready.md).  

 **Toepassingsbeheer**  

 Voorziet in een set hulpprogramma's en resources waarmee u toepassingen kunt maken, implementeren en controleren voor verschillende apparaten die u beheert. Daarnaast wordt in Configuration Manager biedt u hulpprogramma's die u helpen bij het beveiligen van uw bedrijfsgegevens in apps van gebruiker. Zie [inleiding op Toepassingsbeheer](/sccm/apps/understand/introduction-to-application-management).

 **Toegang tot bedrijfsbronnen**  

 Voorziet in een set hulpprogramma's en resources waarmee u gebruikers binnen uw organisatie toegang kunt geven tot gegevens en toepassingen van externe locaties. Deze hulpprogramma's behoren Wi-Fi-profielen VPN-profielen, certificaatprofielen en voorwaardelijke toegang tot Exchange en SharePoint online. Zie [beveiligen gegevens en site-infrastructuur met System Center Configuration Manager](../../../protect/understand/protect-data-and-site-infrastructure.md) en [toegang tot services in System Center Configuration Manager beheren](../../../protect/deploy-use/manage-access-to-services.md).  

 **Instellingen voor naleving**  

 Biedt een set hulpprogramma's en resources waarmee u kunt beoordelen, bijhouden en herstel de compatibiliteit van de configuratie van clientapparaten in de onderneming. Bovendien kunt u instellingen voor naleving configureren van een bereik aan functies en beveiligingsinstellingen op apparaten die u beheert. Zie [apparaatcompatibiliteit met System Center Configuration Manager garanderen](../../../compliance/understand/ensure-device-compliance.md).  

 **Endpoint Protection**  

 Voorziet in beheer op het gebied van beveiliging, antimalware en Windows Firewall voor computers binnen uw onderneming. Zie [Endpoint Protection in System Center Configuration Manager](../../../protect/deploy-use/endpoint-protection.md).  

 **Inventaris**  

 Biedt een set hulpprogramma's om te identificeren en activa bewaken:  

-   **Hardware-inventaris**: Verzamelt gedetailleerde informatie over de hardware van apparaten in uw onderneming. Zie [inleiding op hardware-inventarisatie in System Center Configuration Manager](../../../core/clients/manage/inventory/introduction-to-hardware-inventory.md).  

-   **Software-inventaris**: Verzamelt en rapporteert informatie over de bestanden die zijn opgeslagen op clientcomputers in uw organisatie. Zie [Inleiding tot software-inventaris in System Center Configuration Manager](../../../core/clients/manage/inventory/introduction-to-software-inventory.md).  

-   **Asset Intelligence**: Voorziet in hulpprogramma's voor het verzamelen van inventarisgegevens en het gebruik van softwarelicenties in uw onderneming te controleren. Zie [inleiding op Asset Intelligence in System Center Configuration Manager](../../../core/clients/manage/asset-intelligence/introduction-to-asset-intelligence.md).  

**Mobile device management met Microsoft Intune**  

 U kunt de Configuration Manager gebruiken voor het beheren van iOS, Android (inclusief Samsung KNOX Standard), Windows Phone en Windows-apparaten met behulp van de Microsoft Intune-service via Internet.

 Hoewel u de Intune-service gebruiken, worden beheertaken uitgevoerd met behulp van de service verbinding sitesysteemrol beschikbaar is via de Configuration Manager-console. Zie [hybride mobile device management (MDM) met System Center Configuration Manager en Microsoft Intune](../../../mdm/understand/hybrid-mobile-device-management.md).  

 **On-premises Mobile Device Management**  

 Inschrijven en beheren van pc's en mobiele apparaten met behulp van de lokale Configuration Manager-infrastructuur en de beheerfunctionaliteit is ingebouwd in de apparaatplatforms (in plaats van vertrouwen op een afzonderlijk geïnstalleerde Configuration Manager-client). Biedt momenteel ondersteuning voor het beheren van Windows 10 Enterprise- en Windows 10 Mobile-apparaten. Zie [mobiele apparaten beheren met on-premises infrastructuur in System Center Configuration Manager](../../../mdm/understand/manage-mobile-devices-with-on-premises-infrastructure.md).  

 **Implementatie van besturingssysteem**  

 Voorziet in een hulpprogramma voor het maken van installatiekopieën van besturingssystemen. U kunt deze installatiekopieën vervolgens gebruiken voor de besturingssystemen implementeren op computers, met gebruikmaking van de PXE-opstartbewerking of opstartbare media zoals een CD-set, DVD of USB-sticks. Houd er rekening mee dat dit van toepassing op computers die beheerd worden door Configuration Manager, evenals de niet-beheerde computers. Zie [Inleiding tot besturingssysteemimplementaties in System Center Configuration Manager](../../../osd/understand/introduction-to-operating-system-deployment.md).  

 **Energiebeheer**  

 Voorziet in een set hulpprogramma's en resources waarmee u het energieverbruik van clientcomputers in het bedrijf kunt beheren en controleren. Zie [inleiding op Energiebeheer in System Center Configuration Manager](../../../core/clients/manage/power/introduction-to-power-management.md).  

 **Query's**  

 Voorziet in een hulpprogramma voor het verkrijgen van informatie over resources in uw hiërarchie en informatie over inventarisgegevens en statusberichten. U kunt deze informatie vervolgens gebruiken voor rapportage of voor het definiëren van verzamelingen apparaten of gebruikers voor software-implementatie en configuratie-instellingen. Zie [inleiding op query's in System Center Configuration Manager](../../../core/servers/manage/introduction-to-queries.md).  

 **Profielen voor externe verbindingen**  

 Biedt een set hulpprogramma's en bronnen waarmee u kunt maken, implementeren en bewaken van de instellingen voor externe verbindingen voor apparaten in uw organisatie. Door het implementeren van deze instellingen minimaliseert u de moeite door gebruikers verbinding maken met hun computers in het bedrijfsnetwerk. Zie [werken met profielen voor externe verbindingen in System Center Configuration Manager](/sccm/compliance/deploy-use/create-remote-connection-profiles).  

 **Items voor gebruikersgegevens en profielen configuratie**  

 Gebruiker en -profielen configuratie-items in Configuration Manager bevatten instellingen die u beheren kunnen, Mapomleiding, offlinebestanden en zwervende profielen op computers met Windows 8 en hoger voor gebruikers in uw hiërarchie. Zie [werken met profielen configuration items voor gebruikersgegevens en in System Center Configuration Manager](/sccm/compliance/deploy-use/create-user-data-and-profiles-configuration-items).  

 **Beheer op afstand**  

 Biedt hulpprogramma's voor het extern beheren van clientcomputers in de Configuration Manager-console. Zie [inleiding op beheer op afstand in System Center Configuration Manager](../../../core/clients/manage/remote-control/introduction-to-remote-control.md).  

 **Rapporten**  

 Biedt een set hulpprogramma's en resources waarmee u de geavanceerde rapportagefuncties van SQL Server Reporting Services vanuit de Configuration Manager-console gebruiken. Zie [Inleiding tot rapportage in System Center Configuration Manager](../../../core/servers/manage/introduction-to-reporting.md).  

 **Softwarelicentiecontrole**  

 Voorziet in hulpprogramma's om te controleren en verzamelen van softwaregebruiksgegevens van Configuration Manager-clients. Zie [Het app-gebruik in System Center Configuration Manager controleren met softwaremeter](../../../apps/deploy-use/monitor-app-usage-with-software-metering.md).  

 **Software-updates**  

 Voorziet in een set hulpprogramma's en resources waarmee u software-updates in het bedrijf kunt maken, implementeren en controleren. Zie [Inleiding tot software-updates in System Center Configuration Manager](/sccm/sum/understand/software-updates-introduction).  
