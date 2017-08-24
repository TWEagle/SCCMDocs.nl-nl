---
title: Configuratiegegevens importeren | Microsoft Docs
description: Configuratiegegevens importeren als deze is opgenomen in een CAB-bestand-indeling en aan de ondersteunde Service Modeling Language-schema voldoet.
ms.custom: na
ms.date: 10/06/2016
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 309b9a09-a611-4ba2-90ab-dde51582cf87
caps.latest.revision: "6"
caps.handback.revision: "0"
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.openlocfilehash: 60d0642618a3074fc50a848f1189f4d6559ca916
ms.sourcegitcommit: 51fc48fb023f1e8d995c6c4eacfda7dbec4d0b2f
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 08/07/2017
---
# <a name="import-configuration-data-with-system-center-configuration-manager"></a>Configuratiegegevens importeren met System Center Configuration Manager

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*

Naast het maken van configuratiebasislijnen en configuratie-items in de System Center Configuration Manager-console, kunt u de configuratie van gegevens als deze is opgenomen in een CAB-bestand en voldoen aan de ondersteunde schema van de Service Modeling Language (SML) importeren. U kunt configuratiegegevens van importeren:  

-   Aanbevolen configuratiegegevens (configuratiepakketten) die zijn gedownload van Microsoft of van andere sites van softwareleveranciers.  

-   De configuratiegegevens die zijn geëxporteerd uit System Center 2012 Configuration Manager en later.  

-   Configuratiegegevens die extern zijn ontworpen en die voldoet aan het SML-schema.  

 Zie [System Center 2012 Configuration Manager Configuration Pack](http://www.microsoft.com/en-us/download/details.aspx?id=30710&WT.mc_id=rss_alldownloads_all)(Engelstalig) voor een voorbeeld van een configuratiepakket waarmee u compliantie beheert voor System Center 2012 Configuration Manager-siteserverrollen.  

Wanneer u een configuratiebasislijn importeert, kunnen enkele of alle van de configuratie-items waarnaar wordt verwezen in de configuratiebasislijn ook worden opgenomen in het CAB-bestand. Configuration Manager controleert tijdens het importeren of dat alle configuratie-items waarnaar wordt verwezen in de configuratiebasislijn ook zijn opgenomen in het CAB-bestand of al aanwezig zijn in de Configuration Manager-site. Tijdens het importeren mislukt als u probeert te importeren van een configuratiebasislijn die verwijst naar de configuratiegegevens die Configuration Manager kan niet worden gevonden.  

Hieronder worden enkele andere scenario's beschreven waarin het importproces kan mislukken:  

-   De configuratiegegevens verwijzen naar configuratiegegevens die Configuration Manager kan niet in de database of in het CAB-bestand zelf vinden.  

-   De configuratiegegevens zijn al aanwezig in de Configuration Manager-database met dezelfde naam en versie van configuration data, maar de inhoudsversie wijkt af.  

-   De configuratiegegevens zijn al aanwezig in de Configuration Manager-database met dezelfde inhoudsversie, maar de hashberekening deze als afwijkend identificeert.  

-   Een nieuwere versie van de configuratiegegevens met dezelfde naam is al aanwezig of is onlangs verwijderd in de Configuration Manager-database.  

-   In een hiërarchie met meerdere sites Configuration Manager is de configuratiegegevens oorspronkelijk geïmporteerd van een bovenliggende site. U moet deze bijwerken van dezelfde site, niet een onderliggende site.  

### <a name="import-configuration-data"></a>Configuratiegegevens importeren  

1.  Klik in de Configuration Manager-console op **activa en naleving** > **configuratie-Items** of **Configuratiebasislijnen**
2.  In de **Start** tabblad, in de **maken** groep, klikt u op **configuratiegegevens importeren**.  
3.  Klik op de pagina **Bestanden selecteren** van de wizard **Configuratiegegevens importeren**op **Toevoegen**en selecteer in het dialoogvenster **Openen** de CAB-bestanden die u wilt importeren.  
4.  Selecteer de **Maak een nieuw exemplaar van de geïmporteerde configuratiebasislijnen en configuratie-items** selectievakje in als u wilt dat de geïmporteerde configuratiegegevens moeten kunnen worden bewerkt in de Configuration Manager-console.  
5.  Op de **samenvatting** controleert u de acties die moeten worden ondernomen en voltooi de wizard.  

De geïmporteerde configuratiegegevens worden weergegeven in de **instellingen voor naleving** knooppunt van de **activa en naleving** werkruimte.  
