---
title: Setup-verwijzing | Microsoft-documenten
description: "Bekijk deze referentie om u te helpen bij het voorbereiden voor het installeren van een Configuration Manager-site of hiërarchie."
ms.custom: na
ms.date: 4/18/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: cdb9fb0c-0912-41e4-b427-f40620971763
caps.latest.revision: 22
author: Brenduns
ms.author: brenduns
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 761c3f58f7c57d8f87ee802da37821895062546d
ms.openlocfilehash: 739461a6cca0fd67431093524c1e8158afd80d0f
ms.contentlocale: nl-nl
ms.lasthandoff: 05/17/2017


---
# <a name="reference-for-system-center-configuration-manager-setup"></a>Documentatie voor de installatie van System Center Configuration Manager

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*

Setup van System Center Configuration Manager vindt u koppelingen naar diverse onderwerpen die worden beschreven in de volgende secties. De informatie die hier voorgesteld kunt u voorbereiden van een Configuration Manager-site of hiërarchie hebt geïnstalleerd en u voor sommige van de beslissingen die u tijdens de installatie moet worden voorbereid.  


##  <a name="bkmk_start"></a> Voordat u begint  
Voordat u nieuwe Configuration Manager-sites installeert, moet dat u de volgende informatie die kan helpen bij het instellen van de fase voor een geslaagde implementatie ontwerp hebt bekeken:  

-   [De grondbeginselen van System Center Configuration Manager](../../../../core/understand/fundamentals.md)  
-   [Plan voor System Center Configuration Manager-infrastructuur](../../../plan-design/network/configure-firewalls-ports-domains.md)  
-   [Voorbereiden voor het installeren van System Center Configuration Manager-sites](prepare-to-install-sites.md)  

##  <a name="bkmk_assess"></a> De gereedheid van de server beoordelen  
Voordat u begint met de installatie van een nieuwe site, controleert u of de siteserver en de externe sitesysteemservers die u wilt gebruiken voor de site (bijvoorbeeld de server die als host fungeert voor de sitedatabase) voldoen aan alle vereiste configuraties. Deze onderwerpen in de Documentatiebibliotheek vindt:  

-   [Ondersteunde configuraties voor System Center Configuration Manager](../../../../core/plan-design/configs/supported-configurations.md)  
-   [Prerequisite Checker](prerequisite-checker.md)  

##  <a name="bkmk_Addclients"></a> Clients voor aanvullende besturingssystemen  
U kunt clientsoftware downloaden voor Configuration Manager van het Microsoft Download Center voor de volgende besturingssystemen:  

-   Mac (Apple)  
-   UNIX  
-   Linux  

Gebruik de volgende koppelingen voor het downloaden van clients voor de versie van Configuration Manager, u gebruikt:  

-   Zie [Microsoft System Center Configuration Manager - Clients voor andere besturingssystemen](http://www.microsoft.com/download/details.aspx?id=47719)  

##  <a name="bkmk_usage"></a> Gebruiksgegevensniveaus en instellingen  
Wanneer u uw eerste System Center Configuration Manager-site installeert, Configuration Manager automatisch wordt geïnstalleerd en configureert u een nieuwe sitesysteemrol de **serviceverbindingspunt**, op de siteserver. De service connection point heeft deze standaardinstellingen:  

-   **Online** modus (de offline modus ook beschikbaar is)  
-   **Verbeterde** niveau van verzameling gegevens (twee andere gegevens verzameling niveaus, Basic en volledig, ook beschikbaar zijn)  

Wanneer de service connection point-sitesysteemrol online is, kan Microsoft automatisch diagnoses en gebruik gegevens verzamelen via het Internet. Met de gegevens die worden verzameld kunnen we:  

-   Problemen vaststellen en oplossen  
-   Onze producten en de service verbeteren  
-   Updates herkennen voor Configuration Manager die betrekking hebben op de versie van Configuration Manager die u gebruikt  

### <a name="levels-of-data-collection"></a>Niveaus van gegevensverzameling  
Verzamelen van gegevens, bevat deze drie niveaus:

-   **Basic** bevat gegevens over de installatie en upgrade, zoals het aantal sites en Configuration Manager-functies die zijn ingeschakeld. Er is geen persoonsgegevens verzonden.  

-   **Verbeterde** bevat de gegevens in de algemene instelling, plus het brengt gegevens over de hiërarchie, hoe elke functie wordt gebruikt (frequentie en duur) en verbeterde diagnostische gegevens zoals de geheugenstatus van uw server als een systeem of app crashes optreedt. Er zijn geen persoonlijke gegevens worden verzonden.  

-   **Volledige** bevat de gegevens in de instellingen voor Basic en verbeterde niveau, en ook verzendt geavanceerde diagnostische gegevens zoals systeembestanden en geheugen momentopnamen. Deze optie kan tot personen herleidbare gegevens bevatten, maar deze informatie niet gebruikt om te identificeren of contact met u op, of naar doel advertenties voor u.  

Zie voor meer informatie, inclusief de vermelding van de details die worden verzameld door elk niveau [diagnostische en gebruiksgegevens voor System Center Configuration Manager](../../../../core/plan-design/diagnostics/diagnostics-and-usage-data.md).  

De System Center Configuration Manager privacyverklaring online is, Ga naar [http://go.microsoft.com/fwlink/?LinkID=626527](http://go.microsoft.com/fwlink/?LinkID=626527).

