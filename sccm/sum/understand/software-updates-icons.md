---
title: Pictogrammen die worden gebruikt voor software-updates | Microsoft-documenten
description: De Configuration Manager-console bevat pictogrammen die wijzen op een status voor de gesynchroniseerde update of software-updategroep.
keywords: 
author: dougeby
ms.author: dougeby
manager: angrobe
ms.date: 10/06/2016
ms.topic: article
ms.prod: configuration-manager
ms.service: 
ms.technology:
- configmgr-sum
ms.assetid: 63c5ef72-5715-4d86-85a2-71beba469fab
ms.translationtype: Machine Translation
ms.sourcegitcommit: e6cf8c799b5be2f7dbb6fadadddf702ec974ae45
ms.openlocfilehash: 04c5ccc53263b2672096b564695a636bfb28d952
ms.contentlocale: nl-nl
ms.lasthandoff: 05/17/2017


---
# <a name="icons-used-for-software-updates-in-system-center-configuration-manager"></a>Pictogrammen die worden gebruikt voor software-updates in System Center Configuration Manager

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*

Gesynchroniseerde software-updates worden weergegeven in de Configuration Manager-console en de eerste kolom voor elke software-update bevat een pictogram dat een specifieke status aangeeft. Software-updategroepen worden ook weergegeven met een pictogram dat informatie verschaft over de status van de software-updates in de groep. Deze sectie bevat informatie over de software-updatepictogrammen en de betekenis van elk pictogram.  

## <a name="icons-for-software-updates"></a>Pictogrammen voor software-updates  
 Gesynchroniseerde software-updates worden aangeduid met een van de volgende pictogrammen.  

### <a name="normal-icon"></a>Pictogram Normaal  
 ![pictogram](../media/Normal.jpg "normaal pictogram") het pictogram met de groene pijl vertegenwoordigt een normale software-update.  

 **Beschrijving:**  

 Normale software-updates zijn gesynchroniseerd en zijn beschikbaar voor software-implementatie.  

 **Operationele problemen:**  

 Er zijn geen operationele problemen.  

### <a name="expired-icon"></a>Pictogram Verlopen  
 ![pictogram](../media/Expired.jpg "verlopen pictogram") het pictogram met de zwarte X vertegenwoordigt een verlopen software-update. U kunt verlopen software-updates ook identificeren via de **verlopen** kolom voor de software-update wanneer deze wordt weergegeven in de Configuration Manager-console.  

 **Beschrijving:**  

 Verlopen software-updates konden voorheen worden geïmplementeerd op clientcomputers, maar zodra een software-update is verlopen, kunnen er geen nieuwe implementaties meer worden gemaakt voor de software-updates. Verlopen software-updates worden verwijderd van actieve implementaties en wordt niet langer beschikbaar worden gesteld aan clients.  

 **Operationele problemen:**  

 Er zijn geen operationele problemen.

### <a name="superseded-icon"></a>Pictogram Vervangen  
 ![pictogram](../media/Superseded.jpg "vervangen pictogram") het pictogram aan de gele ster. vertegenwoordigt een vervangen software-update. U kunt ook vervangen software-updates identificeren via de **vervangen** kolom voor de software-update wanneer deze wordt weergegeven in de Configuration Manager-console.  

 **Beschrijving:**  

 Vervangen software-updates zijn vervangen door de nieuwere versies van de software-update. Een software-update die een andere software-update vervangt, heeft doorgaans de volgende kenmerken:  

-   Bevordert, verbetert of voegt iets toe aan de oplossing die werd geleverd door een of meer eerder uitgebrachte software-updates.  

-   Verbetert de efficiëntie van het bestandspakket van de software-update, dat clients installeren wanneer de software-update is goedgekeurd voor installatie. Bijvoorbeeld, de vervangen software-update kan bestanden bevatten die niet langer relevant zijn voor de fix of voor de besturingssystemen die nu door de nieuwe software-update worden ondersteund. Die bestanden worden daarom niet opgenomen in het vervangende bestandspakket van de software-update.  

-   Werkt nieuwere versies van een product bij, of met andere woorden, is niet langer van toepassing op oudere versies of configuraties van een product. Software-updates kunnen ook andere software-updates vervangen als er wijzigingen zijn aangebracht om de taalondersteuning uit te breiden. Bijvoorbeeld, een latere revisie van een productupdate voor Microsoft Office kan de ondersteuning voor een ouder besturingssysteem verwijderen, maar kan aanvullende ondersteuning voor nieuwe talen aan de initiële release van de software-update toevoegen.  

 Op het tabblad Vervangingsregels van het dialoogvenster Eigenschappen van software-updatepuntcomponent, kunt u aangeven hoe u vervangen software-updates wilt beheren. Voor meer informatie, zie [Vervangingsregels](../plan-design/plan-for-software-updates.md#BKMK_SupersedenceRules).  

 **Operationele problemen:**  

 Indien mogelijk moet u in plaats van de vervangen software-update de vervangende software-update implementeren op clientcomputers. U kunt op het tabblad **Vervangingsinformatie** in de eigenschappen van de software-update een lijst weergeven van de software-updates die de software-update vervangen.  

### <a name="invalid-icon"></a>Pictogram Ongeldig  
 ![pictogram](../media/Invalid.jpg "ongeldig pictogram") het pictogram met de rode X vertegenwoordigt een ongeldige software-update.  

 **Beschrijving:**  

 Ongeldige software-updates bevinden zich in een actieve implementatie, maar om de een of andere reden is de inhoud (software-updatebestanden) niet beschikbaar. Hier volgen enkele scenario's waarin deze status kan zich voordoen:  

-   U kunt de software-update implementeren, maar het software-updatebestand wordt verwijderd uit het implementatiepakket en is niet meer beschikbaar.  

-   U maakt een implementatie van een software-update op een site en het implementatieobject wordt gerepliceerd naar een onderliggende site, maar het implementatiepakket wordt niet goed naar de onderliggende site gerepliceerd.  

 **Operationele problemen:**  

 Als de inhoud voor een software-update ontbreekt, kunnen clients de software-update niet installeren totdat de inhoud beschikbaar is op een distributiepunt. U kunt de inhoud opnieuw naar distributiepunten distribueren met behulp van de actie **Opnieuw distribueren** . Als er inhoud ontbreekt voor een software-update in een implementatie die is gemaakt op een bovenliggende site, moet de software-update worden gerepliceerd of opnieuw worden gedistribueerd naar de onderliggende site. Zie voor meer informatie over de herdistributie van inhoud, [beheren van de inhoud die u hebt gedistribueerd](../../core/servers/deploy/configure/deploy-and-manage-content.md#bkmk_manage).  

### <a name="metadata-only-icon"></a>Pictogram Alleen metagegevens
 ![pictogram](../media/MetadataOnly.png "alleen metagegevens pictogram") het pictogram met de blauwe pijl vertegenwoordigt een alleen-metagegevens van software-update.

 **Beschrijving:**  

 Alleen de metagegevens van software-updates zijn beschikbaar in de Configuration Manager-console voor rapportage. U kunt geen software-updates implementeren of downloaden die alleen metagegevens bevatten, omdat er geen software-updatebestand is gekoppeld aan de metagegevens van de software-updates.  

 **Operationele problemen:**  

 Software-updates met alleen metagegevens zijn beschikbaar voor rapportagedoeleinden en zijn niet bedoeld voor de implementatie van software-updates.  

## <a name="icons-for-software-update-groups"></a>Pictogrammen voor software-updategroepen  
 Software-updategroepen worden aangeduid met een van de volgende pictogrammen.  

### <a name="normal-icon"></a>Pictogram Normaal  
 ![pictogram](../media/Normal.jpg "normaal pictogram") het pictogram met de groene pijl vertegenwoordigt een groep met software-update die alleen normale software-updates bevat.  

 **Operationele problemen:**  

 Er zijn geen operationele problemen.  

### <a name="expired-icon"></a>Pictogram Verlopen  
 ![pictogram](../media/Expired.jpg "verlopen pictogram") het pictogram met de zwarte X vertegenwoordigt een groep met software-update die een of meer verlopen software-updates bevat.  

 **Operationele problemen:**  

 Indien mogelijk moeten de verlopen software-updates in de software-updategroep worden verwijderd of vervangen.  

### <a name="superseded-icon"></a>Pictogram Vervangen  
 ![pictogram](../media/Superseded.jpg "vervangen pictogram") het pictogram aan de gele ster. vertegenwoordigt een software-updategroep met een of meer vervangen software-updates.  

 **Operationele problemen:**  

 Indien mogelijk moet de vervangen software-update in de software-updategroep worden vervangen door de vervangende software-update.  

### <a name="invalid-icon"></a>Pictogram Ongeldig  
 ![pictogram](../media/Invalid.jpg "ongeldig pictogram") het pictogram met de rode X vertegenwoordigt een groep met software-update die een of meer ongeldige software-updates bevat.  

 **Operationele problemen:**  

 Als de inhoud voor een software-update ontbreekt, kunnen clients de software-update niet installeren totdat de inhoud beschikbaar is op een distributiepunt. U kunt de inhoud opnieuw naar distributiepunten distribueren met behulp van de actie **Opnieuw distribueren** . Als er inhoud ontbreekt voor een software-update in een implementatie die is gemaakt op een bovenliggende site, moet de software-update worden gerepliceerd of opnieuw worden gedistribueerd naar de onderliggende site. Zie voor meer informatie over de herdistributie van inhoud, [beheren van de inhoud die u hebt gedistribueerd](../../core/servers/deploy/configure/deploy-and-manage-content.md#bkmk_manage).  

