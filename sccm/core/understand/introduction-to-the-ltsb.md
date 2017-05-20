---
title: Inleiding tot de lange termijn onderhoud vertakking | Microsoft-documenten
description: Meer informatie over de lange termijn Servicing vertakking van System Center Configuration Manager.
ms.custom: na
ms.date: 05/01/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 694bc29f-a7fd-4e06-815a-1a9c5e9ac563
caps.latest.revision: 0
author: Brenduns
ms.author: brenduns
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: d940fd1bbf96767d44f8c55315e814be55a83897
ms.openlocfilehash: 91c1ca860069c6ebe0d20230c4620bf3f68735a2
ms.contentlocale: nl-nl
ms.lasthandoff: 05/17/2017


---
# <a name="introduction-to-the-long-term-servicing-branch-of-system-center-configuration-manager"></a>Inleiding tot de lange termijn onderhoud onderliggende items van System Center Configuration Manager

*Van toepassing op: System Center Configuration Manager (op lange termijn onderhoud vertakking)*

De langetermijndoelen onderhoud vertakking (LTSB) van System Center Configuration Manager is een afzonderlijke vertakking van Configuration Manager die is ontwikkeld als een installatie-optie beschikbaar is voor alle klanten. Het is echter de enige optie voor klanten die laten vervallen van hun Software Assurance (SA) of gelijkwaardige abonnementsrechten voor Configuration Manager.


Op basis van Configuration Manager versie 1606, heeft de LTSB functionaliteit ten opzichte van de huidige vertakking van Configuration Manager verminderd.

 > [!TIP]   
 > Als u op zoek zijn naar voor informatie over de vertakkingen van **Windows Server**, Zie [Windows Server 2016 nieuwe huidige vertakking voor bedrijven optie onderhoud]( https://blogs.technet.microsoft.com/windowsserver/2016/07/12/windows-server-2016-new-current-branch-for-business-servicing-option/).

## <a name="features-that-are-not-available-in-the-ltsb-of-configuration-manager"></a>Functies die niet beschikbaar in de LTSB van Configuration Manager
De huidige vertakking van Configuration Manager ondersteunt de volgende functionaliteit is niet beschikbaar wanneer u de LTSB:

-   In het console-updates die toevoegen van nieuwe functies en verbeteringen.
-   Ondersteuning voor nieuw uitgebrachte besturingssystemen om te gebruiken als siteservers en clients.
-   Gebruik van een Microsoft Intune-abonnement om te ondersteunen:
    -   Intune in een hybride mobile device management (MDM)-configuratie
    -   On-premises MDM
-   De Windows 10 onderhoud Dashboard en onderhoud van plan, waaronder ondersteuning voor recente Windows 10 huidige vertakking (CB) en huidige vertakking voor Business (CBB) versies.  
-   Ondersteuning voor toekomstige versies van Windows Server en Windows 10 LTSB
-   Asset Intelligence
-   Clouddistributiepunten
-   Exchange Online als een Exchange-Connector    

Hoewel ondersteuning voor deze functies is niet beschikbaar met de LTSB, sommige functies blijven zichtbaar in de Configuration Manager-console, maar kunnen niet worden geselecteerd of gebruikt.


## <a name="find-documentation-for-the-ltsb"></a>Documentatie voor de LTSB vinden
De LTSB is gebaseerd op de huidige vertakking versie 1606. Gebruik voor de productdocumentatie van de [huidige vertakking documentatie](https://docs.microsoft.com/sccm/), met waarschuwingen en de beperkingen die specifiek voor de LTSB zijn. Deze waarschuwingen en beperkingen worden geïdentificeerd in de volgende online onderwerpen:

-      [Inleiding tot de lange termijn onderhoud vertakking](introduction-to-the-ltsb.md): (In dit onderwerp)
-      [De lange termijn Servicing vertakking installeren](install-the-ltsb.md)
-      [De lange termijn Servicing vertakking bijwerken naar de huidige vertakking](convert-to-current-branch.md)
-      [Ondersteunde configuraties voor de lange termijn vertakking onderhoud](supported-configurations-for-ltsb.md)
-   [De lange termijn Servicing vertakking van Configuration Manager beheren](manage-the-ltsb.md)

Wanneer u verwijst naar de huidige vertakking documentatie voor de LTSB, wordt de informatie die betrekking hebben op versie 1606 ook toepassen op de LTSB. Functies of gegevens die geïntroduceerd met versie 1610 of hoger zijn worden niet ondersteund door de LTSB.


## <a name="licensing-overview-for-the-ltsb"></a>Overzicht van de licentiegegevens voor de LTSB   
Klanten met actieve Software Assurance (SA) in System Center Configuration Manager-licenties, of een equivalente abonnementsrechten vanaf 1 oktober 2016 hebt recht op de release van oktober 2016 1606 versie van System Center Configuration Manager. Klanten met rechten voor System Center Configuration Manager op of na 1 oktober 2016 vindt twee gelicentieerde opties tijdens de installatie: Huidige vertakking en op lange termijn onderhoud vertakking (LTSB).

Klanten die permanente rechten voor System Center Configuration Manager hebben of dat de SA of abonnement vervalt na 1 oktober dat kunnen de versie van System Center Configuration Manager LTSB die geldt op het moment van verval installeren.

[Volledige voorwaarden voor de producten die u hebt gekocht via Microsoft Volume Licensing-programma's vindt u hier](http://go.microsoft.com/fwlink/?LinkId=800052).

Zie [System Center Configuration Manager-licentieverlening en vertakkingen](learn-more-editions.md) voor meer informatie over licentieverlening voor Configuration Manager vertakkingen.

## <a name="next-steps"></a>Volgende stappen

Als u besluit dat de LTSB Configuration Manager de juiste vertakking voor uw omgeving is [installeren van een nieuwe LTSB](/sccm/core/understand/install-the-ltsb#install-a-new-site) site als onderdeel van een nieuwe hiërarchie, of [upgrade van een System Center 2012 Configuration Manager-site](/sccm/core/understand/install-the-ltsb#upgrade-from-system-center-2012-configuration-manager) en -hiërarchie.

Als u nog geen installatiemedia, Zie [System Center 2016 documentatie](https://technet.microsoft.com/system-center-docs/system-center) voor informatie over het ophalen van System Center 2016, waaronder de media die u gebruiken kunt voor het installeren van de System Center Configuration Manager LTSB.  

