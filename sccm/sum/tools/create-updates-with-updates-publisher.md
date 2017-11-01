---
title: Maken van updates
titleSuffix: Configuration Manager
description: Maken en de bundel van software-updates met System Center Updates Publisher
ms.custom: na
ms.date: 4/29/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 46a1a8ac-126c-4ee6-ae09-32dfbdb83368
caps.latest.revision: "1"
author: Brenduns
ms.author: brenduns
manager: angrobe
robots: NOINDEX, NOFOLLOW
ms.openlocfilehash: 37e2d83dd463f4ffe71fa09ab68b94be980d434b
ms.sourcegitcommit: c236214b2fcc13dae7bad96d7fb33f692868191d
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/12/2017
---
# <a name="create--software-updates-and-update-bundles-with-updates-publisher"></a>Software-updates maken en updatebundels met Updates Publisher

*Van toepassing op: System Center Updates Publisher*

Met Updates Publisher kunt u de **maken bijwerken** wizard voor het maken van uw eigen updates en de **bundel maken** wizard voor het maken van bundels van updates.

Omdat deze twee wizards een vergelijkbare werkstroom hebben, wordt de procedure voor het maken van een updatebundel verwijst naar de procedure voor het maken van updates met alleen de relevante verschillen beschreven.

## <a name="use-the-create-update-wizard"></a>Gebruik de wizard Update maken
1.  Ga in de console naar **werkruimte Updates**, en klik vervolgens in de **aan de slag** deelvenster kiezen **Update** van de **Start** tabblad van het lint. Hiermee opent u de **maken bijwerken** wizard.

2.  Op de **pakket** pagina, gebruikt u de volgende informatie kunt u de update te configureren:

    -   Kies **Bladeren** de software-updatepakket dat u als een pakketbron gebruikt vinden. Geldige bronnen bevatten. MSI. MSP, of. EXE-bestanden. Updates Publisher vereist toegang tot het bestand te maken van een bestands-hash. Het hash- en de naam worden vervolgens gebruikt in de metagegevens van de update voor de update die u maakt.

    -   Geef de bronlocatie van de inhoud voor deze update. Dit is normaal gesproken de locatie waar het binaire update wordt gedownload van tijdens het publiceren naar een WSUS-server.  Als de **een lokale bron gebruiken voor het publiceren van software-update-inhoud** optie is ingeschakeld, wordt het pad is niet vereist.

        Later, wanneer de update is gepubliceerd naar een WSUS-server, downloadt Updates Publisher de binaire bestanden voor de update van de opgegeven bronlocatie.  Als geen pad is opgegeven Publisher bijwerken zoekt de [lokale bron publicatiepad](/sccm/sum/tools/updates-publisher-options#advanced) voor de update-binary.

    -   Geef de **binaire taal** van de software-update.

    -   Geef **geslaagd retourcodes**, en **geslaagd in afwachting van opnieuw opstarten codes** voor de update. Meerdere retourcodes gescheiden door komma's. U kunt retourcodes gebruiken om te bepalen wanneer de installatie van update is voltooid en wanneer opnieuw opstarten vereist zijn.

        -   Windows installer-bestanden en -patches (. MSI en. MSP-bestanden) automatisch deze waarden instellen en kan niet worden gewijzigd.

        -   Voor. EXE-updates, de standaard-codes gedefinieerd door de. EXE-bestand worden gebruikt als er geen retourcodes zijn opgegeven.

    -   Geef geen opdrachtregelargumenten die nodig zijn voor het installeren van de software-update.

        -   Windows installer-bestanden en -patches (. MSI en. MSP-bestanden) instellen automatisch deze waarden. Voor deze bestandstypen de argumenten moeten worden opgegeven als  **\[naam\]=\[waarde\]**. Bovendien alle opties die beginnen met een  **/**  (zoals **/qn**) worden niet ondersteund voor. MSI of. MSP-software-updates.

        -   Voor. EXE-updates, alle argumenten zijn ongeldig.

3.  Op de **informatie** pagina, Geef details over de update die opgenomen zijn wanneer de update is gepubliceerd of geëxporteerd. Details bevatten gelokaliseerde eigenschappen zoals de naam van de updates (titel) en een beschrijving. Vervolgens geeft opgeeft u meer algemene informatie zoals de classificatie, leverancier, product en waar u meer informatie over de update.

     __Gelokaliseerde eigenschappen:__

    -   **Taal**: Selecteer een taal en geef vervolgens een titel en beschrijving. Vervolgens kunt u extra talen, één voor elke taal ondersteunt een eigen titel en beschrijving.

    -   **Titel**: Voer de naam van de update. Deze naam wordt weergegeven in de werkruimte Updates van de Updates Publisher-console.

    -   **Beschrijving**: Een beschrijving van de update. U kunt opnemen wat de update is geïnstalleerd en waarom en wanneer moet worden gebruikt.

     **Classificatie:** Hier volgt een algemene beschrijving voor de verschillende classificaties.

    -   **Update**: Een update voor een toepassing of bestand dat momenteel is geïnstalleerd.

    -   **Kritieke**: Een grote schaal uitgebrachte update aan voor een specifiek probleem die zijn gericht op een kritieke fout die niet gerelateerd is aan beveiliging.

    -   **Functiepakket**: Nieuwe productfuncties die zijn gedistribueerd buiten een productrelease en die gewoonlijk zijn opgenomen in de volgende productrelease.

    -   **Beveiliging**: Een grote schaal uitgebrachte update aan voor een productspecifiek probleem met betrekking tot beveiliging.

    -   **Updatepakket**: Een volledige reeks van hotfixes die samen zijn verpakt voor een gemakkelijke implementatie. Deze hotfixes omvatten beveiligingsupdates, essentiële updates, enzovoort. Een updatepakket adressen in het algemeen een specifiek gebied, zoals beveiliging of een functie van het product.

    -   **Service Pack**: Een volledige reeks van hotfixes die op een toepassing worden toegepast. Deze hotfixes omvatten beveiligingsupdates, essentiële updates, software-updates, enzovoort.

    -   **Hulpprogramma**: Geeft een hulpprogramma of onderdeel aan waarmee een of meer taken uitvoeren.

     -   **Stuurprogramma**: Een update voor stuurprogramma's.

    **Leverancier:** Geef een leverancier voor de update. U kunt de vervolgkeuzelijst gebruiken als u de waarden van updates die in de opslagplaats. Als u een leverancier opgeeft, maakt de wizard een map met die Leveranciersnaam onder **alle Software-Updates** in de **werkruimte Updates** als deze map niet bestaat. Hier volgen de Windows Server Update Services (WSUS) gereserveerde namen die kunnen niet worden ingevoerd voor updates die u maakt:
 >*   Microsoft Corporation
 >*   Microsoft
 >*   bijwerken
 >*   Software-Update
 >*   Hulpprogramma 's
 >*   Hulpprogramma
 >*   Kritiek
 >*   Essentiële Updates
 >*   Beveiliging
 >*   Beveiligingsupdates
 >*   Functiepakket
 >*   Updatepakket
 >*   Service Pack
 >*   Stuurprogramma
 >*   Stuurprogramma-Update
 >*   Bundel
 >*   De Bundelupdate

**Product**: Geef het type van het product dat de update voor. U kunt de vervolgkeuzelijst gebruiken als u de waarden van updates die in de opslagplaats. Dezelfde lijst met WSUS-gereserveerde namen die niet worden gebruikt voor **leverancier**, kan niet worden gebruikt voor **Product**.

 **URL voor meer info**: Geef de URL waar u meer informatie over deze update vindt. Moet u kleine letters voor **https** of **http** wanneer u deze URL invoert.

4.  Op de **optionele Info** pagina, u kunt details configureren die vindt u aanvullende informatie over de update.

    -   **Bulletin-ID**: Bulletin-id's worden meestal, maar niet altijd geleverd door de leveranciers van de update.

    -   **Artikel-ID**: Als een artikel van software-update beschikbaar is, kan de artikel-ID nuttig zijn voor personen aanvullende informatie over de update te zoeken.

    -   **CVE-id's:** Overzicht van een of meer algemene beveiligingsproblemen en Exposures (CVE)-id's die informatie over de update beveiliging bieden of bundel bijwerken. Wanneer meer dan één, gebruik een puntkomma te scheiden van de CVEs zoals in dit voorbeeld: *CVE1; CVE2.*

    -   **Ondersteunings-URL:** De URL die informatie over ondersteuning voor deze update bevat een lijst indien beschikbaar. Moet u kleine letters voor **https** of **http** wanneer u deze URL invoert.

    -   **Ernst:** Stel de ernst voor deze update.

    -   **Gevolgen:** De volgende opties kunnen worden gebruikt om op te geven gevolgen:
        -   **Normaal –** gebruiken deze om aan te geven van de update vereist een standaardinstallatie procedures.
        -   **Secundaire –** gebruiken deze om aan te geven van de update vereist minimale installatieprocedures.
        -   **Exclusieve verwerkt – moet** gebruiken deze om aan te geven van de update moet zelfstandig exclusieve van andere updates worden geïnstalleerd.   <br /><br />

    -   **Gedrag voor opnieuw opstarten:** Gebruik deze informatie over het gedrag voor updates opnieuw opstarten opgeven. Deze instelling heeft geen invloed op het werkelijke gedrag van de installatie van de update.

        -   **Nooit opnieuw wordt opgestart**: Nooit levert de computer opnieuw opstarten na de installatie van de software-update.
        -   **Opnieuw opstarten is het vereist**: Altijd levert de computer opnieuw opstarten na de installatie van de software-update.
        -   **Opnieuw opstarten kan aanvragen**: Nadat de software-update is geïnstalleerd, vraagt de computer opnieuw opstarten alleen als een herstart nodig is. De gebruiker heeft de optie voor opnieuw opstarten uitstellen. Dit is de standaardwaarde. <br /><br />

5.  Op de **vereiste** pagina, geeft u de vereisten die moeten worden geïnstalleerd op een computer voordat deze update kunt installeren. Vereisten kunnen worden **detectoids** of andere updates. Detectoids worden op hoog niveau regels, zoals die de computers CPU alleen moet een 64-bits processor. Detectoids kunt ook opgeven voor specifieke updates die moeten worden geïnstalleerd voordat deze update kunt installeren.

    -   Gebruik voor betere prestaties detectoids in plaats van maken *installeerbare* en *geïnstalleerd regels* die de controle van dezelfde of een actie uitgevoerd.

    Gebruik de zoekopties voor **beschikbare software-updates en detectoids** om te zoeken naar specifieke updates of detectoids. Bijvoorbeeld zoeken op **CPU** de detectoids vinden waarmee u de installatie op basis van specifieke CPU-architectuur beperken.

    U kunt een of meer items selecteren tegelijk wilt toevoegen als een vereiste. Wanneer u vereisten toevoegt, worden de geselecteerde detectoids toegevoegd als een of meer groepen. Om in aanmerking komen voor de installatie, kan een computer moet voldoen aan de vereiste van ten minste één lid van elke groep die u configureert:

 -   Wanneer u klikt op **vereiste toevoegen** alle items die u hebt geselecteerd, worden toegevoegd aan afzonderlijke individuele, groepen. Om in aanmerking komen voor deze update, moet een computer voldoen aan de vereiste van deze groep en geven vereisten voor groepen die zijn geconfigureerd.

 -   Wanneer u klikt op **groep toevoegen,** alle items die u hebt geselecteerd worden toegevoegd aan één groep. Om in aanmerking komen voor deze update, moet een computer voldoen aan ten minste één van de vereisten van deze groep en geven vereisten voor groepen die zijn geconfigureerd.

6.  Op de **vervanging** pagina, geeft u de updates die zijn vervangen door deze update (vervangen). Wanneer deze update is gepubliceerd, Configuration Manager elke update die wordt vervangen als worden gemarkeerd **verlopen**. Clients installeert vervolgens deze update in plaats van de vervangen updates.

7.  Op de **toepasselijkheid** gebruik pagina de **regeleditor** voor het definiëren van een reeks regels die bepalen of een apparaat deze update moet. (Deze pagina is vergelijkbaar met de **geïnstalleerde** pagina die erop volgt.)

    Als u wilt een nieuwe regel toevoegen, klikt u op ![Nieuwe regel](media/newrule.png). Hiermee opent u de Toepassingsregel pagina waar u regels kunt configureren.

    Typen regels die u kunt maken, zijn onder andere:

    -   **Bestand** : deze regel gebruiken om te vereisen dat een apparaat een bestand met de eigenschappen die voldoen aan een of meer criteria die u voordat u deze update opgeeft kunnen worden toegepast.

    -   **Register –** gebruik van dit type Registerdetails die aanwezig zijn moeten voordat een apparaat in aanmerking komt voor het installeren van deze update opgeven.

    -   **Systeem:** met deze regel details van systeem gebruikt om te bepalen van de toepassing. U kunt kiezen tussen een Windows-versie, een Windows-taal, de processorarchitectuur definiëren of geef een WMI-query om te identificeren van het besturingssysteem van de apparaten.

    -   **Windows Installer –** dit regeltype gebruiken om te bepalen op basis van een geïnstalleerde toepassing. MSI- of Windows Installer-patch (. MSP). U kunt ook bepalen of bepaalde onderdelen of functies zijn geïnstalleerd als onderdeel van de vereiste.

        > [!IMPORTANT]  
        > Op beheerde deices, de Windows Update Agent kan niet worden geïnstalleerd door Windows-pakketten die zijn geïnstalleerd per gebruiker detecteren. Wanneer u dit regeltype gebruikt, regels voor toepasselijkheid aanvullende, zoals versies van bestanden of registersleutelwaarden zodanig configureren dat de Windows Installer-pakket correct ongeacht basis per gebruiker of per systeem kan worden gedetecteerd.

    -   **Regel: opgeslagen** met deze optie kunt u zoeken en regels u *gemaakt in de werkruimte regels*.

        Nadat u een regel maakt, kunt u de andere pictogrammen wijzigen van de regel en als er meerdere regels, om relaties tussen deze regels te definiëren.

    Wanneer u bent gereed te maken en regels toe te voegen, klikt u op **OK** in de **Set van regel maken** in het dialoogvenster om op te slaan die set. Vervolgens kunt u maken een **nieuw** regel en voeg die toe aan de set ook.

    Wanneer er meerdere regels of regelsets toevoegen aan een update, kunt u de logische operators in de **regeleditor** vastgesteld tussen de regels en de volgorde waarin ze worden verwerkt.

8.  Op de **geïnstalleerde** gebruik pagina de **Rule Editor naar** definiëren van een reeks regels die bepalen of een apparaat de update die u configureert al is geïnstalleerd. (Deze pagina is vergelijkbaar met de **toepasselijkheid** pagina die wordt uitgevoerd op deze pagina.)

    Deze pagina van de wizard ondersteunt configureren regels met dezelfde opties en criteria als de **toepasselijkheid** pagina.

    Wanneer de wizard is voltooid, de nieuwe update is toegevoegd aan een knooppunt in de **werkruimte Updates** die wordt geïdentificeerd door de **leverancier** en **Product** naam die u voor deze update gebruikt.

## <a name="use-the-create-bundle-wizard"></a>Gebruik de wizard pakket maken
Omdat deze wizard maakt gebruik van dezelfde werkstroom als de [maken bijwerken wizard](#use-the-create-update-wizard), die werkstroom gebruiken, maar let op het volgende verschil voor bundels:

1.  U start de wizard, in de console gaat u naar **werkruimte Updates**, en selecteer vervolgens **bundel** van de **Start** tabblad van het lint.

2.  In tegenstelling tot de wizard Update maken is er geen pakketpagina bij het maken van een bundel.

3.  Op de **informatie** pagina, Geef details over de updatebundel die opgenomen zijn wanneer de update is gepubliceerd of geëxporteerd.

4.  Op de **optionele Info** pagina kunt u details met aanvullende informatie over de updatebundel. De beschikbare opties zijn hetzelfde als voor het maken van een update. Opties voor Impact en het gedrag voor opnieuw opstarten zijn echter niet beschikbaar als ze niet van toepassing op bundels.

5.  Op de **vereiste** pagina, geeft u de vereisten die op een computer moeten worden geïnstalleerd voordat dit pakket kunt installeren. Deze regels zijn hetzelfde zoals te zien voor afzonderlijke updates.

6.  Op de **vervanging** pagina, geeft u de updates die zijn vervangen door deze updatebundel (vervangen). Deze regels zijn hetzelfde zoals te zien voor afzonderlijke updates.

7.  Op de **leden** pagina als u updates toevoegen aan de updatebundel selecteren. Alleen updates die u hebt gemaakt of geïmporteerd in Updates Publisher zijn beschikbaar.

Wanneer de wizard is voltooid, de nieuwe updatebundel is toegevoegd aan een knooppunt in de **werkruimte Updates** die wordt geïdentificeerd door de **leverancier** naam die u voor de updatebundel gebruikt.
