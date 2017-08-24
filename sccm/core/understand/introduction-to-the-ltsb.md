---
title: Inleiding tot de lange termijn onderhoud vertakking | Microsoft Docs
description: Meer informatie over de lange termijn onderhoud vertakking van System Center Configuration Manager.
ms.custom: na
ms.date: 05/01/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 694bc29f-a7fd-4e06-815a-1a9c5e9ac563
caps.latest.revision: "0"
author: Brenduns
ms.author: brenduns
manager: angrobe
ms.openlocfilehash: 91c1ca860069c6ebe0d20230c4620bf3f68735a2
ms.sourcegitcommit: 51fc48fb023f1e8d995c6c4eacfda7dbec4d0b2f
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 08/07/2017
---
# <a name="introduction-to-the-long-term-servicing-branch-of-system-center-configuration-manager"></a>Inleiding tot de lange termijn onderhoud-vertakking van System Center Configuration Manager

*Van toepassing op: System Center Configuration Manager (op lange termijn onderhoud vertakking)*

De Long-Term Servicing Branch (LTSB) van System Center Configuration Manager is een afzonderlijke vertakking van Configuration Manager die is ontworpen als een installatie-optie die beschikbaar zijn voor alle klanten. Het is echter de enige optie voor klanten die laten vervallen van hun Software Assurance (SA) of gelijkwaardige abonnementsrechten voor Configuration Manager.


Op basis van Configuration Manager versie 1606, heeft de LTSB verminderde functionaliteit in vergelijking met de huidige vertakking van Configuration Manager.

 > [!TIP]   
 > Als u voor informatie over de vertakkingen van zoekt **Windows Server**, Zie [Windows Server 2016 nieuwe Current Branch for Business optie onderhoud]( https://blogs.technet.microsoft.com/windowsserver/2016/07/12/windows-server-2016-new-current-branch-for-business-servicing-option/).

## <a name="features-that-are-not-available-in-the-ltsb-of-configuration-manager"></a>Functies die niet beschikbaar in de LTSB Configuration Manager
De huidige vertakking van Configuration Manager ondersteunt de volgende functionaliteit die is niet beschikbaar wanneer u de LTSB gebruiken:

-   In de console-updates die toevoegen van nieuwe functies en verbeteringen.
-   Ondersteuning voor nieuw uitgebrachte besturingssystemen gebruiken als siteservers en clients.
-   Gebruik van een Microsoft Intune-abonnement om te ondersteunen:
    -   Intune in een hybride mobile device management (MDM)-configuratie
    -   On-premises MDM
-   De Windows 10-Onderhoudsdashboard en onderhoudsplannen, inclusief ondersteuning voor recente Windows 10 Current Branch (CB) en de huidige vertakking voor versies Business (CBB).  
-   Ondersteuning voor toekomstige versies van Windows Server en Windows 10 LTSB
-   Asset Intelligence
-   Clouddistributiepunten
-   Exchange Online als een Exchange-Connector    

Hoewel ondersteuning voor deze functies is niet beschikbaar met de LTSB, sommige functies blijven zichtbaar in de Configuration Manager-console, maar kunnen niet worden ingeschakeld of gebruikt.


## <a name="find-documentation-for-the-ltsb"></a>Documentatie voor de LTSB vinden
De LTSB is gebaseerd op de huidige vertakking versie 1606. Gebruik voor de productdocumentatie van de [Current Branch documentatie](https://docs.microsoft.com/sccm/), met aanvullende opmerkingen en beperkingen die specifiek voor de LTSB zijn. Deze aanvullende opmerkingen en beperkingen worden geïdentificeerd in de volgende onderwerpen in de onlinemodus:

-     [Inleiding tot de lange termijn onderhoud vertakking](introduction-to-the-ltsb.md): (In dit onderwerp)
-     [De lange termijn Servicing Branch installeren](install-the-ltsb.md)
-     [Upgrade van de lange termijn onderhoud vertakking naar de huidige vertakking](convert-to-current-branch.md)
-     [Ondersteunde configuraties voor de Long-Term Servicing Branch](supported-configurations-for-ltsb.md)
-   [De lange termijn onderhoud vertakking van Configuration Manager beheren](manage-the-ltsb.md)

Wanneer u verwijst naar de Current Branch-documentatie voor de LTSB, wordt de details die voor versie 1606 gelden ook toepassen op de LTSB. Functies of gegevens die geïntroduceerd in versie 1610 of hoger zijn worden niet ondersteund door de LTSB.


## <a name="licensing-overview-for-the-ltsb"></a>Licentieverlening voor de LTSB-overzicht   
Klanten met actieve Software Assurance (SA) op System Center Configuration Manager-licenties, of een equivalente abonnementsrechten vanaf 1 oktober 2016 gemachtigd de release van oktober 2016 versie 1606 van System Center Configuration Manager te gebruiken. Klanten met rechten naar System Center Configuration Manager op of na 1 oktober 2016 vindt u twee opties onder licentie na de installatie: Huidige vertakking en op lange termijn Servicing Branch (LTSB).

Klanten die eeuwigdurende rechten naar System Center Configuration Manager hebben, of waarmee SA of abonnement vervalt na 1 oktober kunnen installeren de versie van System Center Configuration Manager LTSB die is bijgewerkt op het moment van vervalt.

[Volledige bepalingen en voorwaarden voor de producten die u hebt gekocht via Microsoft Volume Licensing-programma's vindt u hier](http://go.microsoft.com/fwlink/?LinkId=800052).

Zie [System Center Configuration Manager-licentieverlening en vertakkingen](learn-more-editions.md) voor meer informatie over licentieverlening voor vertakkingen van Configuration Manager.

## <a name="next-steps"></a>Volgende stappen

Als u besluit dat de LTSB Configuration Manager de juiste vertakking voor uw omgeving is [installeren van een nieuwe LTSB](/sccm/core/understand/install-the-ltsb#install-a-new-site) site als onderdeel van een nieuwe hiërarchie of [upgrade van een System Center 2012 Configuration Manager-site](/sccm/core/understand/install-the-ltsb#upgrade-from-system-center-2012-configuration-manager) en -hiërarchie.

Als u geen installatiemedia, Zie [System Center 2016 documentatie](https://technet.microsoft.com/system-center-docs/system-center) voor informatie over het ophalen van System Center 2016, waaronder de media die u gebruiken kunt voor het installeren van de System Center Configuration Manager-LTSB.  
