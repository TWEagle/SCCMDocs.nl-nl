---
title: Update-catalogussen beheren | Microsoft Docs
description: Software-update-catalogussen beheren voor System Center Updates Publisher
ms.custom: na
ms.date: 4/29/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 887f8029-1a3a-423c-a9c1-31dc0d693386
caps.latest.revision: "1"
author: Brenduns
ms.author: brenduns
manager: angrobe
robots: NOINDEX, NOFOLLOW
ms.openlocfilehash: 7451d699e0e5e146b0538a57deca595188d113bf
ms.sourcegitcommit: 51fc48fb023f1e8d995c6c4eacfda7dbec4d0b2f
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 08/07/2017
---
# <a name="manage-software-update-catalogs-in-updates-publisher"></a>Software-update catalogussen in Updates Publisher beheren

*Van toepassing op: System Center Updates Publisher*

Gebruik de **catalogussen** **werkruimte** voor het beheren van software-update catalogussen. Dit omvat nieuwe catalogussen, bestaande catalogus-abonnementen beheren en informatie over de updates te importeren uit een catalogus naar de opslagplaats voor Updates Publisher toe te voegen.

Software-update catalogussen bevatten informatie over verwante updates die zijn gemaakt door organisaties dan Microsoft. Andere organisaties kunnen uw eigen organisatie en de software van derden leveranciers die hun catalogussen hebt geregistreerd bij Microsoft. Geregistreerde catalogi van softwareleveranciers heten *catalogussen partner*. Catalogussen die u maakt en die niet zijn geregistreerd bij Microsoft, worden genoemd *gebruiker* catalogussen.

## <a name="add-software-update-catalogs"></a>Software-update catalogi toevoegen
Voordat u de updates die deze bevat kunt beheren, moet u een update-catalogus toevoegen in Updates Publisher. Wanneer u een catalogus met Updates Publisher toevoegt:
-   Maakt een abonnement op die catalogus, zodat u kunt op updates voor deze catalogus controleren.
-   De catalogus toegevoegd aan een lijst aan in de **mijn Software-Update catalogussen** venster van de **catalogussen werkruimte**.  

Informatie over elke geabonneerde catalogus is beschikbaar in de console. Informatie bevat de download-URL of locatie, de naam van het bedrijf of organisatie die de catalogus hebt gemaakt en wanneer deze het laatst ingevoerd of gewijzigd.

Updates Publisher kan automatisch Controleer uw abonnementen voor wijzigingen telkens wanneer die deze wordt gestart. Dit is geconfigureerd als een [geavanceerde optie](/sccm/sum/tools/updates-publisher-options#advanced). Wanneer geconfigureerd, verwijst de download-URL of locatie-informatie voor het abonnement en waarschuwingen u wanneer er wijzigingen in de catalogus die zijn aangebracht sinds de laatste keer dat u deze hebt geïmporteerd in de opslagplaats naar in Updates Publisher.

Handmatig om te controleren of bijwerken van de catalogus, selecteert u de catalogus van de **Mijn catalogi van Software-Update** lijst en kies vervolgens **vernieuwen** vanuit het lint.

Naast de catalogussen toe te voegen en informatie over geabonneerde catalogussen weergeven, kunt u:
-  **Bewerken** informatie voor *gebruiker* catalogussen.
-  **Verwijder** (verwijderen) een catalogus van Updates Publisher.
-  **Importeren** updates van een catalogus in de opslagplaats voor Updates Publisher. Wanneer u updates hebt geïmporteerd, kunt u alle updates die in die catalogus importeren. Vervolgens kunt u de updates bekijken in de werkruimte Updates waar u kunt selecteren en updates publiceren naar de updateserver.

> [!NOTE]   
> Verwijderen van een catalogus van Updates Publisher resulteert in de updates in die catalogus wordt verwijderd van uw opslagplaats. Dit heeft geen invloed op de updates die u op de updateserver hebt gepubliceerd. Als updates wilt verwijderen van uw server bijwerken die niet langer in de opslagplaats, Zie [zonder software-updates verlopen](/sccm/sum/tools/updates-publisher-options#expire-unreferenced-software-updates).

## <a name="manage-update-catalogs"></a>Update-catalogussen beheren
Vindt u de lijst catalogussen die u hebt geïmporteerd in de **mijn Software-Update catalogussen** venster van de **catalogussen werkruimte**. Vanuit deze werkruimte kunt u het volgende doen:

-   **Een partner-catalogus toevoegen:** Gebruik een van de volgende nieuwe partner catalogussen vinden:

    -   Ga in de console naar **werkruimte Updates** > **overzicht**. In de **aan de slag** venster kiezen **Partner Software-Updates catalogussen toevoegen**.

    -   Ga in de console naar **catalogussen werkruimte** > **mijn catalogussen**. Kies vervolgens vanuit het lint **catalogussen toevoegen**.

-   **Een Gebruikerscatalogus toevoegen:** Ga in de console naar **catalogussen werkruimte** > **mijn catalogussen**. Kies vervolgens vanuit het lint **catalogussen toevoegen**. Naast de locatie van het CAB-bestand, moet u een Publisher, naam en beschrijving voor het identificeren van de catalogus.


-   **Controleren op updates voor catalogussen:** Selecteer een of meer catalogussen en kies vervolgens **vernieuwen** vanuit het lint.

-   **Een Gebruikerscatalogus bewerken:** Selecteer een *gebruiker* catalogus en kies vervolgens **bewerken** vanuit het lint. U kunt de gebruiker gedefinieerde eigenschappen wijzigen.

-   **Catalogi verwijderen:** Selecteer een of meer catalogussen en kies vervolgens **verwijderen** vanuit het lint. Hiermee verwijdert u de catalogus, uw abonnement en de updates uit die catalogi van uw opslagplaats Updates Publisher.

-   **Updates van een catalogus toevoegen aan uw opslagplaats**: Kies **importeren** vanuit het lint op start de **Import Catalog** wizard. Zie voor meer infomration [-updates importeren](#import-updates)

## <a name="import-updates"></a>Updates importeren
Wanneer u een catalogus importeert, voegt Manager Updates de updates vanaf die catalogus naar de opslagplaats voor Updates Publisher. Nadat updates hebt geïmporteerd, kunt u ze kunt publiceren naar de updateserver zodat ze beschikbaar zijn op beheerde apparaten.

### <a name="to-import-updates"></a>Om updates te importeren
1.  Starten de **Import Catalog** wizard kiezen **importeren** vanuit het lint in een van de volgende werkruimtes:

    -   Catalogussen werkruimte

    -   Werkruimte updates

2.  Op de **importtype** pagina, selecteert u een of meer catalogussen die u hebt toegevoegd in Updates Publisher of geef een pad naar een catalogus u nog niet hebt toegevoegd als een abonnement. Gekozen **volgende** wilt weergeven van de samenvatting en als u klaar bent, kiest u **volgende** importeren te beginnen.

3.  Op de **beveiligingswaarschuwing-validatie catalogus** venster, bekijk het certificaat van de catalogus, en als u klaar bent, hebt geselecteerd **accepteren** om de updates te importeren.

    > [!CAUTION]    
    > Updates alleen van uitgevers die u vertrouwt accepteren. Software-updates van uitgevers die geen vertrouwde kunnen toebrengen clientcomputers bij het scannen op updates.

    >  Als u een uitgever niet langer vertrouwt, verwijdert u deze uitgever uit de lijst met vertrouwde uitgevers. Voor meer informatie over catalogussen worden geaccepteerd, klikt u **Vertel Me meer** in de **beveiligingswaarschuwing-validatie catalogus** in het dialoogvenster.

    Als u altijd accepteren catalogi van een uitgever kiest, die uitgever is toegevoegd aan de [lijst met vertrouwde uitgevers](/sccm/sum/tools/updates-publisher-options#trusted-publishers). U kunt bekijken en bewerken van deze lijst als een optie voor Updates Publisher.

4.  Slaat het importeren van een update importeren wanneer de update al in de opslagplaats is en een van de volgende van toepassing is:

    -   De update is ongewijzigd ten opzichte van de laatste keer dat deze is geïmporteerd.

    -   De update is bewerkt en een nieuwe digitale hash. Het bewerken van een update wordt voorkomen dat een nieuwe update wordt de oorspronkelijke overschreven, aangezien dit wijzigingen die u hebt geïmplementeerd wilt overschrijven.

5.  Op de **bevestiging** pagina bekijkt u de resultaten importeren.

6.  Klik op **sluiten** om de wizard te voltooien. U kunt nu de updates voor deze catalogus weergeven in de werkruimte Updates.

## <a name="next-steps"></a>Volgende stappen
Wanneer u updates hebt geïmporteerd, wordt er algemene acties omvatten:
-   [Updates beheren](/sccm/sum/tools/manage-updates-with-updates-publisher) om te bundelen, toewijzen en deze update-server te implementeren.
-   [Maken van regels voor toepasselijkheid](/sccm/sum/tools/updates-publisher-applicability-rules) om te bepalen wanneer updates implementeert voor de updateserver.
