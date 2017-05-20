---
title: Update catalogussen beheren | Microsoft-documenten
description: Software-update catalogussen beheren voor System Center Updates Publisher
ms.custom: na
ms.date: 4/29/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 887f8029-1a3a-423c-a9c1-31dc0d693386
caps.latest.revision: 1
author: Brenduns
ms.author: brenduns
manager: angrobe
robots: NOINDEX, NOFOLLOW
ms.translationtype: Machine Translation
ms.sourcegitcommit: 31819a1df4e63e1114682490a9b3c3b4e5c99cfa
ms.openlocfilehash: 7451d699e0e5e146b0538a57deca595188d113bf
ms.contentlocale: nl-nl
ms.lasthandoff: 05/17/2017

---
# <a name="manage-software-update-catalogs-in-updates-publisher"></a>Software-update catalogussen worden geïmporteerd in Updates Publisher beheren

*Van toepassing op: System Center Updates Publisher*

Gebruik de **catalogussen** **werkruimte** voor het beheren van software-update-catalogus. Dit omvat nieuwe catalogussen, bestaande catalogus-abonnementen beheren en informatie over de updates importeren uit een catalogus van de Updates Publisher-opslagplaats toe te voegen.

Software-update catalogussen bevatten informatie over de gerelateerde updates die zijn gemaakt door organisaties dan Microsoft. Andere organisaties zijn eigen organisatie en de software van derden leveranciers die hun catalogussen hebt geregistreerd bij Microsoft. Geregistreerde catalogussen van softwareleveranciers heten *catalogussen partner*. Catalogussen die u maakt en die niet zijn geregistreerd met Microsoft, worden genoemd *gebruiker* catalogussen worden geïmporteerd.

## <a name="add-software-update-catalogs"></a>Software-update catalogussen toevoegen
U moet een update-catalogus met Updates Publisher toevoegen voordat u de updates die deze bevat kunt beheren. Wanneer u een catalogus met Updates Publisher toevoegt:
-   Maakt een abonnement op die catalogus dus u kunt op updates voor deze catalogus controleren.
-   De catalogus worden toegevoegd aan een lijst in de **mijn Software Update-catalogus** venster van de **catalogussen werkruimte**.  

Informatie over elke geabonneerde catalogus is beschikbaar in de console. Informatie bevat de download-URL of locatie, de naam van het bedrijf of organisatie die de catalogus hebt gemaakt en wanneer deze het laatst ingevoerd of gewijzigd.

Updates Publisher kunt uw abonnementen voor wijzigingen automatisch controleren elke keer dat deze wordt gestart. Dit is geconfigureerd als een [geavanceerde optie](/sccm/sum/tools/updates-publisher-options#advanced). Wanneer u configureert, Updates Publisher wordt verwezen naar de download-URL of locatie-informatie voor het abonnement en waarschuwingen u wanneer er wijzigingen zijn in de catalogus die zijn aangebracht sinds de laatste keer dat u deze naar de opslagplaats geïmporteerd.

Om te controleren of handmatig bijwerken van de catalogus, selecteert u de catalogus van de **mijn Software Update-catalogus** lijst en kies vervolgens **vernieuwen** van het lint.

Naast catalogussen toe te voegen en informatie bekijken over geabonneerde catalogussen worden geïmporteerd, kunt u het volgende doen:
-  **Bewerken** informatie voor *gebruiker* catalogussen worden geïmporteerd.
-  **Verwijder** (verwijderen) een catalogus van Updates Publisher.
-  **Importeren** updates van een catalogus in de opslagplaats Updates Publisher. Wanneer u updates hebt geïmporteerd, kunt u alle updates die in deze catalogus importeren. U kunt vervolgens de updates weergeven in de werkruimte waarin u kunt vervolgens kiezen en updates publiceren naar de updateserver.

> [!NOTE]   
> Een catalogus verwijderen uit de Updates Publisher resulteert in de updates in deze catalogus wordt verwijderd uit uw opslagplaats. Dit heeft geen invloed op de updates die u naar de updateserver hebt gepubliceerd. Als updates wilt verwijderen van uw server bijwerken die niet langer in uw opslagplaats, Zie [zonder verwijzing software-updates verlopen](/sccm/sum/tools/updates-publisher-options#expire-unreferenced-software-updates).

## <a name="manage-update-catalogs"></a>Update catalogussen beheren
U ziet de lijst catalogussen die u hebt geïmporteerd in de **mijn Software Update-catalogus** venster van de **catalogussen werkruimte**. In deze werkruimte kunt u:

-   **Een catalogus partner toevoegen:** Gebruik een van de volgende nieuwe partner catalogussen vinden:

    -   In de console, gaat u naar **werkruimte Updates** > **overzicht**. In de **aan de slag** venster kiezen **toevoegen Partner Software-Updates catalogussen**.

    -   In de console, gaat u naar **catalogussen werkruimte** > **mijn catalogussen**. Kies vervolgens in het lint **catalogussen toevoegen**.

-   **Een Gebruikerscatalogus toevoegen:** In de console, gaat u naar **catalogussen werkruimte** > **mijn catalogussen**. Kies vervolgens in het lint **catalogussen toevoegen**. Naast de locatie van het CAB-bestand, moet u een Publisher, naam en beschrijving voor de catalogus.


-   **Controleren op updates voor catalogussen worden geïmporteerd:** Selecteer een of meer catalogussen en kies vervolgens **vernieuwen** van het lint.

-   **Een Gebruikerscatalogus bewerken:** Selecteer een *gebruiker* catalogus en kies vervolgens **bewerken** van het lint. U kunt de gebruiker gedefinieerde eigenschappen wijzigen.

-   **Verwijder catalogussen worden geïmporteerd:** Selecteer een of meer catalogussen en kies vervolgens **verwijderen** van het lint. Hiermee verwijdert u de catalogus, uw abonnement en de updates uit deze catalogussen van uw opslagplaats Updates Publisher.

-   **Updates van een catalogus toevoegen aan uw opslagplaats**: Kies **importeren** van het lint starten de **Import Catalog** wizard. Zie voor meer infomration [updates importeren](#import-updates)

## <a name="import-updates"></a>Updates importeren
Wanneer u een catalogus importeert, Updates Manager wordt de updates van die catalogus toegevoegd aan de opslagplaats Updates Publisher. Wanneer updates zijn geïmporteerd, kunt u ze kunt publiceren naar de updateserver zodat ze beschikbaar zijn voor beheerde apparaten.

### <a name="to-import-updates"></a>Updates importeren
1.  Starten de **Import Catalog** wizard kiezen **importeren** van het lint in een van de volgende werkruimtes:

    -   Catalogussen werkruimte

    -   De werkruimte updates

2.  Op de **importtype** pagina, selecteert u een of meer catalogussen die u hebt toegevoegd aan de Updates Publisher of geef een pad naar een catalogus u nog niet als een abonnement hebt toegevoegd. Gekozen **volgende** kiezen om te bekijken van de samenvatting en als u klaar bent, **volgende** de import te starten.

3.  Op de **beveiligingswaarschuwing-validatie catalogus** venster Bekijk het certificaat van de catalogus, en als u klaar bent, kiezen **accepteren** de updates importeren.

    > [!CAUTION]    
    > Updates alleen van uitgevers die u vertrouwt accepteren. Software-updates van uitgevers die geen vertrouwde kunnen toebrengen clientcomputers bij het zoeken naar updates.

    >  Als u een publisher niet langer vertrouwt, verwijdert u die uitgever uit de lijst met vertrouwde uitgevers. Ga voor meer informatie over het accepteren van catalogussen worden geïmporteerd, klikt u op **Vertel Me meer** in de **beveiligingswaarschuwing-validatie catalogus** in het dialoogvenster.

    Als u ervoor altijd accepteren catalogussen van een uitgever kiest, die uitgever is toegevoegd aan de [lijst van vertrouwde uitgevers](/sccm/sum/tools/updates-publisher-options#trusted-publishers). U kunt bekijken en bewerken van deze lijst als een optie van de Updates Publisher.

4.  Slaat het importeren van een update importeren wanneer de update al in de bibliotheek is en een van de volgende van toepassing is:

    -   De update is niet gewijzigd sinds de laatste keer dat het is geïmporteerd.

    -   De update is bewerkt en een nieuwe digitale hash heeft. Bewerken van een update wordt voorkomen dat een nieuwe update worden de oorspronkelijke overschreven omdat hierdoor wijzigingen die u hebt geïmplementeerd wilt overschrijven.

5.  Op de **bevestiging** pagina Bekijk de resultaten importeren.

6.  Klik op **sluiten** om de wizard te voltooien. U kunt nu de updates voor deze catalogus weergeven in de werkruimte Updates.

## <a name="next-steps"></a>Volgende stappen
Wanneer u updates hebt geïmporteerd, wordt de algemene acties omvatten:
-   [Beheren van updates](/sccm/sum/tools/manage-updates-with-updates-publisher) toewijzen om te bundelen, en deze implementeren in uw updateserver.
-   [Maken van regels voor toepasselijkheid](/sccm/sum/tools/updates-publisher-applicability-rules) om te bepalen wanneer updates implementeren op uw server bijwerken.

