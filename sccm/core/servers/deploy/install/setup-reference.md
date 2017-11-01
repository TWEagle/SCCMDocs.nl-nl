---
title: Naslaggids voor Setup
titleSuffix: Configuration Manager
description: "Bekijk deze verwijzing zodat u kunt voorbereiden voor het installeren van een Configuration Manager-site of hiërarchie."
ms.custom: na
ms.date: 4/18/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: cdb9fb0c-0912-41e4-b427-f40620971763
caps.latest.revision: "22"
author: Brenduns
ms.author: brenduns
manager: angrobe
ms.openlocfilehash: b7228da1623b5caf1679455e535e282ecf20724a
ms.sourcegitcommit: c236214b2fcc13dae7bad96d7fb33f692868191d
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/12/2017
---
# <a name="reference-for-system-center-configuration-manager-setup"></a>Documentatie voor de installatie van System Center Configuration Manager

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*

Setup van System Center Configuration Manager bevat koppelingen naar diverse onderwerpen die worden beschreven in de volgende secties. De informatie die hier voorgesteld kunt u voorbereiden voor het installeren van een Configuration Manager-site of hiërarchie, en kunt u zich voorbereiden voor een aantal beslissingen die u tijdens de installatie moet nemen.  


##  <a name="bkmk_start"></a> Voordat u begint  
Voordat u nieuwe Configuration Manager-sites installeert, zorg er dan voor dat u hebt gecontroleerd dat de volgende informatie waarmee de fase voor het ontwerp van een geslaagde implementatie instellen:  

-   [Basisprincipes van System Center Configuration Manager](../../../../core/understand/fundamentals.md)  
-   [System Center Configuration Manager-infrastructuur plannen](../../../plan-design/network/configure-firewalls-ports-domains.md)  
-   [Voorbereiden voor het installeren van System Center Configuration Manager-sites](prepare-to-install-sites.md)  

##  <a name="bkmk_assess"></a> De gereedheid van de server beoordelen  
Voordat u de installatie van een nieuwe site begint, zorg ervoor dat de siteserver en de externe sitesysteemservers die u wilt gebruiken voor de site (bijvoorbeeld: de server die als host fungeert voor de sitedatabase) voldoen aan alle vereiste configuraties. Deze onderwerpen in de Documentatiebibliotheek kunnen helpen:  

-   [Ondersteunde configuraties voor System Center Configuration Manager](../../../../core/plan-design/configs/supported-configurations.md)  
-   [Vereistencontrole](prerequisite-checker.md)  

##  <a name="bkmk_Addclients"></a> Clients voor aanvullende besturingssystemen  
U kunt clientsoftware downloaden voor Configuration Manager uit het Microsoft Download Center voor de volgende besturingssystemen:  

-   Mac (Apple)  
-   UNIX  
-   Linux  

Gebruik de volgende koppelingen voor het downloaden van clients voor de versie van Configuration Manager u gebruikt:  

-   Zie [Microsoft System Center Configuration Manager - Clients voor aanvullende besturingssystemen](http://www.microsoft.com/download/details.aspx?id=47719)  

##  <a name="bkmk_usage"></a> Gebruiksgegevensniveaus en instellingen  
Wanneer u uw eerste System Center Configuration Manager-site installeert, Configuration Manager installeert en configureert automatisch een nieuwe sitesysteemrol de **serviceaansluitpunt**, op de siteserver. Het service connection point heeft deze standaardinstellingen:  

-   **Online** modus (de offlinemodus ook beschikbaar is)  
-   **Verbeterde** verzameling gegevensniveau (twee andere gegevensverzamelingsniveaus, basis en volledig zijn ook beschikbaar)  

Wanneer de service connection point-sitesysteemrol online is, kan Microsoft automatisch diagnostische gegevens en gebruiksgegevens informatie verzamelen via Internet. Met de gegevens die worden verzameld kunnen we:  

-   Problemen vaststellen en oplossen  
-   Onze producten en de service verbeteren  
-   Updates herkennen voor Configuration Manager die betrekking hebben op de versie van Configuration Manager die u gebruikt  

### <a name="levels-of-data-collection"></a>Niveaus van gegevensverzameling  
Verzamelen van gegevens, bevat deze drie niveaus:

-   **Basic** bevat gegevens over de installatie en upgrade, zoals het aantal sites en Configuration Manager-functies zijn ingeschakeld. Er is geen persoonsgegevens verzonden.  

-   **Verbeterde** bevat de gegevens uit de niveau instelling basis én er worden gegevens over de hiërarchie verzonden, hoe elke functie wordt gebruikt (frequentie en duur) en verbeterde diagnostische informatie zoals de geheugenstatus van uw server wanneer er een systeem- of app-crash plaatsvindt. Er wordt geen persoonlijk herleidbare informatie verzonden.  

-   **Volledige** bevat de gegevens in de instellingen basis en uitgebreid, en ook verzendt geavanceerde diagnostische informatie, zoals systeembestanden en momentopnamen van het geheugen. Deze optie kan persoonlijke gegevens bevatten, maar die informatie niet gebruikt om te identificeren of contact met u, of naar doel reclame naar u.  

Zie voor meer informatie, waaronder de vermelding van de gegevens die op elk niveau worden verzameld [diagnostische gegevens en gebruiksgegevens voor System Center Configuration Manager](../../../../core/plan-design/diagnostics/diagnostics-and-usage-data.md).  

Als u wilt de System Center Configuration Manager privacyverklaring online weergeven, gaat u naar [http://go.microsoft.com/fwlink/?LinkID=626527](http://go.microsoft.com/fwlink/?LinkID=626527).
