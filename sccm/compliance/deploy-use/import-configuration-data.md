---
title: Configuratiegegevens importeren | Microsoft-documenten
description: Configuratiegegevens importeren als deze is opgenomen in de indeling van een CAB-bestand en de voldoet aan de ondersteunde schema Service modelleren taal.
ms.custom: na
ms.date: 10/06/2016
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 309b9a09-a611-4ba2-90ab-dde51582cf87
caps.latest.revision: 6
caps.handback.revision: 0
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: f9e939d871e95a3248d8e5d96cb73063a81fd5cf
ms.openlocfilehash: 60d0642618a3074fc50a848f1189f4d6559ca916
ms.contentlocale: nl-nl
ms.lasthandoff: 05/17/2017


---
# <a name="import-configuration-data-with-system-center-configuration-manager"></a>Configuratiegegevens importeren met System Center Configuration Manager

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*

Naast het maken van configuratiebasislijnen en configuratie-items in de System Center Configuration Manager-console, kunt u configuratie gegevens als deze is opgenomen in een CAB-bestand indeling en voldoet aan de ondersteunde schema Service Modeling Language (SML) importeren. U kunt de configuratiegegevens van importeren:  

-   Aanbevolen configuratiegegevens (configuratiepakketten) die zijn gedownload van Microsoft of van andere sites van softwareleveranciers.  

-   De configuratiegegevens die zijn geëxporteerd uit System Center 2012 Configuration Manager en later.  

-   Configuratiegegevens die extern is ontworpen en die voldoet aan het schema SML.  

 Zie [System Center 2012 Configuration Manager Configuration Pack](http://www.microsoft.com/en-us/download/details.aspx?id=30710&WT.mc_id=rss_alldownloads_all)(Engelstalig) voor een voorbeeld van een configuratiepakket waarmee u compliantie beheert voor System Center 2012 Configuration Manager-siteserverrollen.  

Wanneer u een configuratiebasislijn importeert, kunnen enkele of alle van de configuratie-items waarnaar wordt verwezen in de configuratiebasislijn ook worden opgenomen in het CAB-bestand. Configuration Manager controleert tijdens het importeren of alle van de configuratie-items waarnaar wordt verwezen in de configuratiebasislijn worden ook opgenomen in het CAB-bestand of al aanwezig zijn in de Configuration Manager-site. Tijdens het importeren mislukt als u probeert te importeren van een configuratiebasislijn die verwijst naar de configuratiegegevens die Configuration Manager is niet gevonden.  

Hieronder worden enkele andere scenario's beschreven waarin het importproces kan mislukken:  

-   De configuratiegegevens verwijst naar de configuratiegegevens die Configuration Manager kan niet in de database of in het CAB-bestand zelf vinden.  

-   De configuratiegegevens is al aanwezig in de Configuration Manager-database met dezelfde naam en versie van de configuratie-gegevens, maar de inhoudsversie verschilt.  

-   De configuratiegegevens is al aanwezig in de Configuration Manager-database met dezelfde inhoud versie, maar de berekening van de hash het identificeert als afwijkend.  

-   Een nieuwere versie van de configuratiegegevens met dezelfde naam bestaat al of is onlangs in de Configuration Manager-database verwijderd.  

-   In een sitehiërarchie met meerdere sites Configuration Manager is de configuratiegegevens oorspronkelijk geïmporteerd van een bovenliggende site. U moet deze bijwerken van dezelfde site, niet een onderliggende site.  

### <a name="import-configuration-data"></a>Configuratiegegevens importeren  

1.  Klik in de Configuration Manager-console op **activa en naleving** > **configuratie-Items** of **Configuratiebasislijnen**
2.  In de **Start** tabblad, in de **maken** groep, klikt u op **configuratiegegevens importeren**.  
3.  Klik op de pagina **Bestanden selecteren** van de wizard **Configuratiegegevens importeren**op **Toevoegen**en selecteer in het dialoogvenster **Openen** de CAB-bestanden die u wilt importeren.  
4.  Selecteer de **Maak een nieuw exemplaar van de geïmporteerde configuratiebasislijnen en configuratie-items** selectievakje in als u wilt dat de geïmporteerde configuratiegegevens worden bewerkt in de Configuration Manager-console.  
5.  Op de **samenvatting** pagina, de acties die zullen worden uitgevoerd en voltooi de wizard.  

De geïmporteerde configuratie-gegevens weergegeven in de **compatibiliteitsinstellingen** knooppunt van de **activa en naleving** werkruimte.  

