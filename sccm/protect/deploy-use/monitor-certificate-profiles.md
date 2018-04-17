---
title: Certificaatprofielen bewaken
titleSuffix: Configuration Manager
description: Informatie over het bewaken van de status van naleving van System Center Configuration Manager-certificaatprofielen.
ms.custom: na
ms.date: 10/06/2016
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 98feaa06-64b1-4e86-a122-93017c97cd4f
caps.latest.revision: 7
caps.handback.revision: 0
author: arob98
ms.author: angrobe
manager: angrobe
ms.openlocfilehash: 6b0ae2042c1c463bce53c0c1a7438cc7102cd66e
ms.sourcegitcommit: fb84bcb31d825f454785e3d9d8be669e00fe2b27
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-monitor-certificate-profiles-in-system-center-configuration-manager"></a>Certificaatprofielen in System Center Configuration Manager controleren

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*


##  <a name="view-compliance-results-in-the-configuration-manager-console"></a>Nalevingsresultaten weergeven in de Configuration Manager-Console  

Voor het bewaken van SCEP-certificaatnaleving gebruik niet de-console, in plaats daarvan, gebruikt u [rapporten](#view-compliance-results-by-using-reports). 

1.  Kies in de Configuration Manager-console **bewaking**>  **implementaties**.  

3.  Selecteer de implementatie van het certificaatprofiel van belang.  

4.  Bekijk de compatibiliteitsinformatie Samenvatting certificaat op de hoofdpagina. Voor meer informatie gedetailleerde, selecteert u het certificaatprofiel en klikt u op de **Start** tabblad, in de **implementatie** groep, kiest u **Status weergeven** openen de **Implementatiestatus** pagina.  

     De pagina **Implementatiestatus** bevat de volgende tabbladen:  

    -   **Compatibele**: Geeft de naleving van het certificaatprofiel op basis van het aantal activa dat is beïnvloed. U kunt op een regel dubbelklikken om een tijdelijk knooppunt te maken onder het knooppunt **Gebruikers** in de werkruimte **Activa en naleving** . Dit knooppunt bevat alle gebruikers die compatibel zijn met het certificaatprofiel. In het deelvenster **Activumgegevens** worden ook de gebruikers weergegeven die compatibel zijn met dit profiel. Dubbelklik op een gebruiker in de lijst voor meer informatie.  

        > [!IMPORTANT]  
        >  Een certificaatprofiel wordt niet geëvalueerd als het niet van toepassing is op een clientapparaat. Het wordt in dat geval echter wel geretourneerd als compatibel.  

    -   **Fout**: Geeft een lijst met alle fouten voor de geselecteerde certificaatprofielimplementatie op basis van het aantal activa dat is beïnvloed. U kunt dubbelklikken op een regel om een tijdelijk knooppunt te maken onder het knooppunt **Gebruikers** van de werkruimte **Activa en naleving** . Dit knooppunt bevat alle gebruikers waarvoor fouten zijn gegenereerd met dit profiel. Wanneer u een gebruiker selecteert, geeft het deelvenster **Activumgegevens** de gebruikers weer die met het geselecteerde probleem te maken krijgen. Dubbelklik op een gebruiker in de lijst moet worden weergegeven voor meer informatie.  

    -   **Niet-compatibele**: Geeft een lijst met alle niet-compatibele regels binnen het certificaatprofiel op basis van het aantal activa dat is beïnvloed. U kunt dubbelklikken op een regel om een tijdelijk knooppunt te maken onder het knooppunt **Gebruikers** van de werkruimte **Activa en naleving** . Dit knooppunt bevat alle gebruikers die niet compatibel zijn met dit profiel. Wanneer u een gebruiker selecteert, geeft het deelvenster **Activumgegevens** de gebruikers weer die met het geselecteerde probleem te maken krijgen. Dubbelklik op een gebruiker in de lijst om verdere informatie weer te geven over het probleem.  

    -   **Onbekende**: Geeft een lijst van alle gebruikers die geen compatibiliteitsstatus is gerapporteerd voor de geselecteerde certificaatprofielimplementatie samen met de huidige clientstatus van apparaten.  

5.  Op de **Implementatiestatus** controleert u gedetailleerde informatie over de naleving van het geïmplementeerde certificaatprofiel weergeven. Een tijdelijk knooppunt wordt gemaakt onder het knooppunt **Implementaties** waarmee u deze informatie snel kunt terugvinden.  

     De status van inschrijving van het certificaat wordt weergegeven als een numerieke waarde. Gebruik de volgende tabel om te begrijpen wat elke waarde betekent:  

    |Status van inschrijving|Beschrijving|  
    |-----------------------|-----------------|  
    |0x00000001|De inschrijving is voltooid en het certificaat is uitgegeven.|  
    |0x00000002|De aanvraag is verzonden en de inschrijving is in behandeling of de aanvraag is buiten band uitgegeven.|  
    |0x00000004|Inschrijving moet worden uitgesteld.|  
    |0x00000010|Er is een fout opgetreden.|  
    |0x00000020|De status van de inschrijving is onbekend.|  
    |0x00000040|De statusgegevens zijn overgeslagen. Dit kan gebeuren als een HYPERLINK "http://msdn.microsoft.com/windows/ms721572" "\l _security_certification_authority_gly" certificeringsinstantie is niet geldig of niet is geselecteerd voor bewaking.|  
    |0x00000100|Inschrijving is geweigerd.|  

##  <a name="view-compliance-results-by-using-reports"></a>Nalevingsresultaten weergeven met behulp van rapporten

 Instellingen voor naleving in System Center Configuration Manager omvatten ingebouwde rapporten die u gebruiken kunt om gegevens over certificaatprofielen te controleren. Deze rapporten hebben de rapportcategorie van **Compatibiliteit en instellingen beheren**.  

> [!IMPORTANT]  
>  U moet een jokerteken (%) gebruiken wanneer u de parameters **Apparaatfilter** en **Gebruikersfilter** gebruikt in de rapporten voor compatibiliteitsinstellingen.  

Voor het bewaken van SCEP-certificaatnaleving gebruiken deze certificaatrapporten in het rapportknooppunt **toegang tot bedrijfsbronnen**:  

 -   Geschiedenis van certificaatuitgifte  
 -   Lijst met activa met certificaten die de vervaldatum bijna hebben bereikt  
 -   Lijst met activa per certificaatuitgiftestatus  



 Zie voor meer informatie over het configureren van rapportage in System Center Configuration Manager [rapportage in System Center Configuration Manager](../../core/servers/manage/reporting.md).  
