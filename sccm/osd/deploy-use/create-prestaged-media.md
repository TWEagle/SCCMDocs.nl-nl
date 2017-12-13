---
title: Voorbereide media maken
titleSuffix: Configuration Manager
description: Voorbereide media maken in System Center Configuration Manager voor het vereenvoudigen van implementatie van Windows in verschillende scenario's.
ms.custom: na
ms.date: 04/11/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: configmgr-osd
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: ff6e7267-302a-4563-815e-cdc0d1a4b60f
caps.latest.revision: "12"
author: aczechowski
ms.author: aaroncz
manager: angrobe
ms.openlocfilehash: a26fc3daf17aefe24a46ece561fc2ceaf5284ffb
ms.sourcegitcommit: 08f9854fb6c6d21e1e923b13e38a64d0bc2bc9a4
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/12/2017
---
# <a name="create-prestaged-media-with-system-center-configuration-manager"></a>Voorbereide media maken met System Center Configuration Manager

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*

Voorbereide media in System Center Configuration Manager is een Windows Imaging Format (WIM)-bestand dat kan worden geïnstalleerd op een bare-metal computer door de fabrikant of in een zakelijk voorbereidingscentrum dat niet is verbonden met de Configuration Manager-omgeving.  
Voorbereide media bevatten de opstartinstallatiekopie die wordt gebruikt voor het starten van de doelcomputer en de installatiekopie van het besturingssysteem die op de doelcomputer wordt toegepast. U kunt ook toepassingen, pakketten en stuurprogrammapakketten opgeven die moeten worden opgenomen als onderdeel van de voorgefaseerde media. De takenreeks waarmee het besturingssysteem wordt geïmplementeerd, staat niet op de media. Voorbereide media worden toegepast op de harde schijf van een nieuwe computer voordat de computer wordt verzonden naar de eindgebruiker. Gebruik voorgefaseerde media voor de volgende implementatiescenario'voor besturingssystemen:  

-   [Een installatiekopie voor een OEM in de fabriek of een lokaal depot maken](../../osd/deploy-use/create-an-image-for-an-oem-in-factory-or-a-local-depot.md)  

-   [Een nieuwe versie van Windows op een nieuwe computer (bare-metal) installeren](install-new-windows-version-new-computer-bare-metal.md)  

-   [Windows to Go implementeren](deploy-windows-to-go.md)  

 Wanneer de computer voor het eerst wordt opgestart nadat de voorgefaseerde media zijn toegepast, wordt Windows PE gestart op de computer en wordt er verbinding gemaakt met een beheerpunt om de takenreeks te vinden waarmee het implementatieproces van het besturingssysteem wordt voltooid. U kunt ook toepassingen, pakketten en stuurprogrammapakketten opgeven die moeten worden opgenomen als onderdeel van de voorgefaseerde media. Wanneer u een takenreeks implementeert waarvoor voorbereide media worden gebruikt, controleert de wizard eerst de lokale takenreekscache op geldige inhoud. Als de inhoud niet wordt gevonden of is gewijzigd, wordt deze door de wizard gedownload vanaf het distributiepunt.  

##  <a name="BKMK_CreatePrestagedMedia"></a> Voorbereide media maken  
 Voordat u voorgefaseerde media met de wizard Takenreeksmedia maken maakt, moet u ervoor zorgen dat aan de volgende voorwaarden wordt voldaan:  

|Taak|Beschrijving|  
|----------|-----------------|  
|Opstartinstallatiekopie|Overweeg het volgende met betrekking tot de opstartinstallatiekopie die u in de takenreeks gebruikt om het besturingssysteem te implementeren:<br /><br /> -De architectuur van de opstartinstallatiekopie moet geschikt is voor de architectuur van de doelcomputer. Op een x64-doelcomputer kan een x86- of x64-opstartinstallatiekopie worden opgestart en uitgevoerd. Op een x86-doelcomputer kan echter alleen een x86-opstartinstallatiekopie worden opgestart en uitgevoerd.<br />-Zorg ervoor dat de installatiekopie de netwerk- en mass storage stuurprogramma's die zijn vereist bevat voor het inrichten van de doelcomputer.|  
|Een takenreeks maken om een besturingssysteem te implementeren|Als onderdeel van de voorgefaseerde media, moet u de takenreeks voor de implemtenatie van het besturingssysteem opgeven.<br /><br /> -Zie voor de stappen voor het maken van een nieuwe takenreeks [een takenreeks maken om een besturingssysteem te installeren](../../osd/deploy-use/create-a-task-sequence-to-install-an-operating-system.md).<br />-Voor meer informatie over takenreeksen, Zie [beheren van takenreeksen om taken te automatiseren](../../osd/deploy-use/manage-task-sequences-to-automate-tasks.md).|  
|Alle aan de takenreeks gekoppeld inhoud distribueren|U moet alle inhoud die door de takenreeks is vereist naar ten minste één distributiepunt distribueren. Dit omvat de opstartinstallatiekopie, de installatiekopie van het besturingssysteem en andere gekoppelde bestanden. De wizard haalt de informatie op van het distributiepunt wanneer het de zelfstandige media creëert. U moet over het toegangsrecht **Lezen** beschikken voor de inhoudsbibliotheek op het distributiepunt.  Zie voor meer informatie [over de Inhoudsbibliotheek](../../core/plan-design/hierarchy/the-content-library.md).|  
|Harde schijf op de doelcomputer|De harde schijf van de doelcomputer moet zijn geformatteerd voordat de voorgefaseerde media op de harde schijf van de computer wordt geplaatst. Indien de harde schijf niet ingedeeld is wanneer de media toegepast wordt, zal de takenreeks die het besturingssysteem implementeert falen wanneer hij de doelcomputer probeert op te starten.|  

> [!NOTE]  
>  De Wizard Takenreeks maken Media de volgende takenreeksvariabelevoorwaarde ingesteld op de media: **_SMSTSMediaType OEMMedia =**. U kunt deze voorwaarde in uw takenreeks gebruiken.  

 Gebruik de volgende procedure om voorbereide media te maken.  

#### <a name="to-create-prestaged-media"></a>Voorbereide media maken  

1.  Klik in de Configuration Manager-console op **Softwarebibliotheek**.  

2.  Vouw **Besturingssystemen** uit in de werkruimte **Softwarebibliotheek**en klik op **Takenreeksen**.  

3.  Klik op het tabblad **Start** in de groep **Maken** op **Takenreeksmedia maken** om de wizard Takenreeksmedia maken te starten.  

4.  Geef op de pagina **Mediatype selecteren** de volgende informatie op en klik op **Volgende**.  

    -   Selecteer **Voorbereide media**.  

    -   Selecteer optioneel, indien u wenst toe te staan dat het besturingssysteem geïmplementeerd wordt zonder invoer van de gebruiker, de optie **Implementatie van het besturingssysteem zonder toezicht toestaan**. Wanneer u deze optie selecteert, wordt de gebruiker niet gevraagd naar informatie over netwerkconfiguratie of naar optionele takenreeksen. De gebruiker wordt wel nog steeds gevraagd om een wachtwoord als de media hiervoor is geconfigureerd.  

5.  Geef op de pagina **Mediabeheer** de volgende informatie op en klik op **Volgende**.  

    -   Selecteer **Dynamische media** als u wilt toestaan dat een beheerpunt media omleidt naar een ander beheerpunt op basis van de clientlocatie binnen de sitegrenzen.  

    -   Selecteer **Op site gebaseerde media** als u wilt dat de media alleen contact maken met het opgegeven beheerpunt.  

6.  Geef op de pagina **Media-eigenschappen**  de volgende informatie op en klik vervolgens op **Volgende**.  

    -   **Gemaakt door**: Geef op wie het medium is gemaakt.  

    -   **Versie**: Geef het versienummer van de media.  

    -   **Opmerking**: Geef een unieke beschrijving van wat de media wordt gebruikt.  

    -   **Mediabestand**: Geef de naam en pad van de uitvoerbestanden op. De wizard schrijft de uitvoerbestanden naar deze locatie. Bijvoorbeeld:  **\\\servername\folder\outputfile.wim**  

7.  Geef op de pagina **Beveiliging** de volgende informatie op en klik vervolgens op **Volgende**.  

    -   Selecteer de **Schakel onbekende computerondersteuning** selectievakje in zodat de media een besturingssysteem implementeren op een computer die niet wordt beheerd door Configuration Manager. Er is geen record van deze computers in de Configuration Manager-database.  Zie voor meer informatie [voorbereiden voor onbekende computerimplementaties](../get-started/prepare-for-unknown-computer-deployments.md).  

    -   Selecteer het selectievakje **Bescherm de media met een wachtwoord** en voer een sterk wachtwoord in om de media te helpen te beschermen tegen onbevoegde toegang. Wanneer u een wachtwoord opgeeft, moet de gebruiker dat wachtwoord leveren om de voorbereide media te gebruiken.  

        > [!IMPORTANT]  
        >  Wijs, als een beste praktijk op vlak van beveiliging, altijd een wachtwoord toe om te helpen de vooraf geplaatste media te beschermen.  

    -   Selecteer **Zelfondertekend certificaat maken**voor HTTP-communicatie en geef vervolgens de begin- en verloopdatum voor het certificaat op.  

    -   Selecteer **PKI-certificaat importeren**voor HTTPS-communicatie en geef vervolgens het certificaat op dat moet worden geïmporteerd met het bijbehorende wachtwoord.  

         Zie voor meer informatie over dit clientcertificaat dat wordt gebruikt voor opstartinstallatiekopieën [PKI-certificaatvereisten](../../core/plan-design/network/pki-certificate-requirements.md).  

    -   **Affiniteit van gebruikersapparaat**: Ter ondersteuning van de gebruiker gericht beheer in Configuration Manager, moet u opgeven hoe u wilt dat de media gebruikers koppelen aan de doelcomputer. Zie voor meer informatie over hoe gebruikersapparaataffiniteit ondersteuning biedt voor implementatie van besturingssystemen, [gebruikers koppelen aan een doelcomputer](../get-started/associate-users-with-a-destination-computer.md).  

        -   Stel **Affiniteit tussen gebruikers en apparaten toestaan met automatische goedkeuring** in als u wilt dat de media gebruikers automatisch koppelen aan de doelcomputer. Deze functionaliteit is gebaseerd op de acties van de takenreeks waardoor het besturingssysteem wordt geïmplementeerd. In dit scenario brengt de takenreeks een relatie tot stand tussen de opgegeven gebruikers en de doelcomputer wanneer deze het besturingssysteem op de doelcomputer implementeert.  

        -   Stel **Affiniteit tussen gebruikers en apparaten toestaan in afwachting van goedkeuring door beheerder** in als u wilt dat de media gebruikers aan de doelcomputer koppelen nadat er goedkeuring is verleend. Deze functionaliteit is gebaseerd op het bereik van de takenreeks waardoor het besturingssysteem wordt geïmplementeerd. In dit scenario brengt de takenreeks een relatie tot stand tussen de opgegeven gebruikers en de doelcomputer, maar wordt er gewacht op goedkeuring van een gebruiker met beheerderrechten voordat het besturingssysteem wordt geïmplementeerd.  

        -   Stel **Geen affiniteit tussen gebruikers en apparaten toestaan** in als niet wilt dat de media gebruikers aan de doelcomputer koppelen. In dit scenario koppelt de takenreeks geen gebruikers aan de doelcomputer wanneer dit het besturingssysteem implementeert.  

8.  Geef op de pagina **Takenreeks** de takenreeks op die op de doelcomputer wordt uitgevoerd. De inhoud waarnaar wordt verwezen door de takenreeks wordt weergegeven in **Deze takenreeks verwijst naar de volgende inhoud**. Controleer de inhoud en klik vervolgens op **Volgende**.  

9. Geef op de pagina **Opstartinstallatiekopie** de volgende informatie op en klik vervolgens op **Volgende**.  

    > [!IMPORTANT]  
    >  De architectuur van de opstartinstallatiekopie die wordt gedistribueerd moet toepasselijk zijn voor de architectuur van de doelcomputer. Op een x64-doelcomputer kan een x86- of x64-opstartinstallatiekopie worden opgestart en uitgevoerd. Op een x86-doelcomputer kan echter alleen een x86-opstartinstallatiekopie worden opgestart en uitgevoerd.  

    -   Geef in het vakje **Opstartinstallatiekopie** de opstartinstallatiekopie op om de doelcomputer op te starten. Zie voor meer informatie [opstartinstallatiekopieën beheren](../get-started/manage-boot-images.md).  

    -   Geef in het vak **Distributiepunt** het distributiepunt op waar de installatiekopie is opgeslagen. De wizard haalt de opstartinstallatiekopie op van het distributiepunt en schrijft deze naar de media.  

        > [!NOTE]  
        >  U moet over het toegangsrecht **Lezen** beschikken voor de inhoudsbibliotheek op het distributiepunt. Zie voor meer informatie [over de Inhoudsbibliotheek](../../core/plan-design/hierarchy/the-content-library.md).  

    -   Als u **Op site gebaseerde media** hebt geselecteerd op de pagina **Mediabeheer** van de wizard, geeft u in het vak **Beheerpunt** een beheerpunt op van een primaire site.  

    -   Als u **Dynamische media** hebt geselecteerd op de pagina **Mediabeheer** van de wizard, geeft u in het vak **Gekoppelde beheerpunten** de beheerpunten van de primaire site die moeten worden gebruikt en een prioriteitsvolgorde voor de eerste communicatie op.  

10. Geef op de pagina **Installatiekopieën** de volgende informatie op en klik vervolgens op **Volgende**.  

    -   Geef in het vak **Installatiekopiepakket** de installatiekopie van het besturingssysteem op. Zie voor meer informatie [installatiekopieën van besturingssystemen beheren](../get-started/manage-operating-system-images.md).  

    -   Geef, indien het pakket verschillende installatiekopieën van besturingssystemen bevat, in het vakje **Installatiekopie-index** de installatiekopie op die moet geïmplementeerd worden.  

    -   Geef in het vak **Distributiepunt** het distributiepunt op waar het pakket van de installatiekopie van het besturingssysteem is opgeslagen. De wizard haalt de opstartinstallatiekopie van het besturingssysteem op van het distributiepunt en schrijft deze naar de media.  

11. Geef op de pagina **Aanpassing** de volgende informatie op en klik vervolgens op **Volgende**.  

    -   Geef de variabelen op die de takenreeks gebruikt voor het implementeren van het besturingssyteem.  

    -   Geef eventuele prestart-opdrachten op die u wilt uitvoeren voordat de takenreeks wordt uitgevoerd. Prestart-opdrachten bestaan uit een script of een uitvoerbaar bestand dat kan communiceren met de gebruiker in Windows PE voordat de takenreeks wordt uitgevoerd om het besturingssysteem te installeren. Zie voor meer informatie over prestart-opdrachten voor media de [Prestart-opdrachten voor takenreeksmedia](../understand/prestart-commands-for-task-sequence-media.md).  

        > [!TIP]  
        >  Tijdens het maken van taak de media schrijft de takenreeks de pakket-ID en prestart-opdrachtregel, inclusief de waarde voor eventuele takenreeksvariabelen, naar het logboekbestand CreateTSMedia.log op de computer waarop de Configuration Manager-console. U kunt dit logboekbestand controleren om de waarde voor de takenreeksvariabelen te verifiëren.  

12. Voltooi de wizard.  

## <a name="next-steps"></a>Volgende stappen
[Scenario's voor het implementeren van enterprise-besturingssystemen](scenarios-to-deploy-enterprise-operating-systems.md)
