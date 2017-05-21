---
title: Maken van updates | Microsoft-documenten
description: Maken en software-updates met System Center Updates Publisher bundelen
ms.custom: na
ms.date: 4/29/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 46a1a8ac-126c-4ee6-ae09-32dfbdb83368
caps.latest.revision: 1
author: Brenduns
ms.author: brenduns
manager: angrobe
robots: NOINDEX, NOFOLLOW
ms.translationtype: Machine Translation
ms.sourcegitcommit: 31819a1df4e63e1114682490a9b3c3b4e5c99cfa
ms.openlocfilehash: 33b188f4a9c14091429d1f49e07f1f17fbf98516
ms.contentlocale: nl-nl
ms.lasthandoff: 05/17/2017

---
# <a name="create--software-updates-and-update-bundles-with-updates-publisher"></a>Software-updates maken en bijwerken van bundels met Updates Publisher

*Van toepassing op: System Center Updates Publisher*

Met Updates Publisher kunt u de **maken bijwerken** wizard voor het maken van uw eigen updates en de **bundel maken** wizard bundels van updates maken.

Omdat deze twee wizards een vergelijkbare werkstroom hebben, wordt de procedure voor het maken van een updatebundel verwijst naar de procedure voor het maken van updates met alleen de relevante verschillen beschreven.

## <a name="use-the-create-update-wizard"></a>Gebruik de wizard maken bijwerken
1.  In de console gaat u naar **werkruimte Updates**, en klik vervolgens in de **aan de slag** deelvenster kiezen **Update** van de **Start** tabblad van het lint. Hiermee opent u de **maken bijwerken** wizard.

2.  Op de **pakket** pagina, gebruikt u de volgende informatie kunt u de update te configureren:

    -   Kies **Bladeren** vinden van de software-updatepakket dat u als een pakketbron gebruikt. Geldige bronnen bevatten. MSI. MSP, of. EXE-bestanden. Updates Publisher maakt een hash van het bestand. Het hash- en de naam worden vervolgens gebruikt in de metagegevens van de update voor de update die u maakt.

    -   Geef de bronlocatie van de inhoud voor deze update. Wanneer u een lokale kopie van de inhoud hebt, kunt u het selectievakje **gebruik van een lokale bron voor het publiceren van software-update-inhoud** gebruiken de [lokale bron publicatiepad](/sccm/sum/tools/updates-publisher-options#advanced) (en geavanceerde optie). Als deze optie niet is ingeschakeld, moet u een URL waar de update kan worden gevonden op het web. Dit pad of de URL is toegevoegd aan de metagegevens van de update.

        Later, wanneer de update wordt gepubliceerd op een WSUS-server, haalt Updates Publisher de binaire bestanden voor de update van de opgegeven bronlocatie.

    -   Geef de **binaire taal** van de software-update.

    -   Geef **geslaagd retourcodes**, en **succes in afwachting van opnieuw opstarten codes** voor de update. Scheid meerdere retourcodes met een komma. U kunt retourcodes gebruiken om te bepalen wanneer de update-installatie is voltooid en wanneer opnieuw opstarten vereist zijn.

        -   Windows installer-bestanden en patches (. MSI en. MSP-bestanden) automatisch ingesteld op deze waarden en kan niet worden gewijzigd.

        -   Voor. EXE-updates, de standaard-codes gedefinieerd door de. EXE-bestand worden gebruikt als er geen retourcodes zijn opgegeven.

    -   Geef geen opdrachtregelargumenten die nodig zijn voor het installeren van de software-update.

        -   Windows installer-bestanden en patches (. MSI en. MSP-bestanden) automatisch ingesteld op deze waarden. Voor deze bestandstypen de argumenten moeten worden opgegeven als  **\[naam\]=\[waarde\]**. Bovendien alle opties die beginnen met een  **/**  (zoals **/qn**) worden niet ondersteund voor. MSI of. MSP-software-updates.

        -   Voor. EXE-updates, alle argumenten zijn ongeldig.

3.  Op de **informatie** pagina, Geef details op over de update die opgenomen zijn wanneer de update is gepubliceerd of geëxporteerd. Details bevatten gelokaliseerde eigenschappen zoals updates naam en beschrijving. Vervolgens kunt opgeven u algemene informatie zoals de indeling, leverancier, product en waar u meer informatie over de update.

    ** Gelokaliseerde eigenschappen: **

    -   **Taal**: Selecteer een taal en geef een titel en beschrijving. Vervolgens kunt u extra talen, één voor elke taal ondersteunen een eigen titel en beschrijving.

    -   **Titel**: Voer de naam van de update. Deze naam wordt weergegeven in de werkruimte Updates van de Updates Publisher-console.

    -   **Beschrijving**: Een beschrijving van de update. U kunt opnemen wat de update installeert en waarom en wanneer deze eigenschap moet worden gebruikt.

  **Classificatie:** Hier volgen beschrijvingen van de algemene voor de verschillende indelingen.

  -   **Update**: Een update voor een toepassing of bestand dat momenteel wordt geïnstalleerd.

  -   **Kritieke**: Een ruim vrijgegeven update voor een specifiek probeem om een kritieke bug die niet is gekoppeld voor beveiliging.

  -   **Functiepakket**: Nieuwe productfuncties die zijn gedistribueerd buiten een productrelease en die gewoonlijk zijn opgenomen in de volgende productrelease.

  -   **Beveiliging**: Een ruim vrijgegeven update voor een probleem met de productspecifieke die gerelateerd is aan de beveiliging.

  -   **Update Rollup**: Een volledige reeks hotfixes die samen zijn verpakt voor een gemakkelijke implementatie. Deze hotfixes omvatten beveiligingsupdates, essentiële updates, enzovoort. Een updatepakket adressen in het algemeen een specifiek gebied, zoals beveiliging of een functie van het product.

  -   **Service Pack**: Een volledige reeks hotfixes die op een toepassing worden toegepast. Deze hotfixes omvatten beveiligingsupdates, essentiële updates, software-updates, enzovoort.

  -   **Hulpprogramma**: Geeft een hulpprogramma of functie die u een of meer taken uitvoeren helpt.

  -   **Stuurprogramma**: Een update voor stuurprogramma's.

 **Leverancier**: Geef een leverancier voor de update. U kunt de vervolgkeuzelijst waarden van updates die in de bibliotheek gebruiken. Wanneer u een leverancier opgeeft, maakt de wizard een map met die Leveranciersnaam onder **alle Software-Updates** in de **werkruimte Updates** als die map nog niet bestaat. Windows Server Update Services (WSUS) gereserveerde namen die niet kunnen worden ingevoerd voor updates die u maakt, zijn:
 -   Microsoft Corporation
 -   Microsoft
 -   Update
 -   Software-Update
 -   Hulpprogramma 's
 -   Hulpprogramma
 -   Kritiek
 -   Essentiële Updates
 -   Beveiliging
 -   Beveiligingsupdates
 -   Functiepakket
 -   Updatepakket
 -   Service Pack
 -   Stuurprogramma
 -   Stuurprogramma-Update
 -   Bundel
 -   De Bundelupdate  <br /><br />

 **Product**: Geef het type van het product waarvoor de update bedoeld is. U kunt de vervolgkeuzelijst waarden van updates die in de bibliotheek gebruiken. Dezelfde lijst met WSUS-gereserveerde namen die niet kunnen worden gebruikt voor **leverancier**, kan niet worden gebruikt voor **Product**.

 **URL voor meer informatie**: Geef de URL waar u meer informatie over deze update kunt vinden. U moet gebruiken kleine letters voor **https** of **http** wanneer u deze URL opgeven.

1.  Op de **optionele Info** pagina kunt u de details die aanvullende informatie over de update geven.

    -   **Bulletin-ID**: Bulletin-id's zijn doorgaans echter niet altijd verstrekt door de update leveranciers.

    -   **Artikel-ID**: Als een artikel voor software-update beschikbaar is, kan de artikel-ID zijn nuttig voor personen om extra informatie over de update te zoeken.

    -   **CVE-id's:** Overzicht van een of meer algemene beveiligingsproblemen en risico's (CVE)-id's die bevatten beveiligingsinformatie over de update of bundel bijwerken. Wanneer u meer dan één aanbieding, gebruik een puntkomma om elkaar te scheiden van de CVEs zoals in dit voorbeeld: *CVE1; CVE2.*

    -   **URL voor ondersteuning:** De URL die ondersteuningsinformatie voor deze update bevat de lijst als deze beschikbaar is. U moet gebruiken kleine letters voor **https** of **http** wanneer u deze URL opgeven.

    -   **Ernst:** Stel de ernst op voor deze update.

    -   **Gevolgen:** De volgende opties kunnen worden gebruikt om op te geven gevolgen:
        -   **Normaal –** dit gebruiken om aan te geven voor de update moet standaardinstallatie procedures.
        -   **Secundaire –** dit gebruiken om aan te geven voor de update moet minimaal installatieprocedures.
        -   **Exclusieve verwerkt – moet** gebruiken deze om aan te geven van de update moet worden geïnstalleerd door zichzelf exclusieve van andere updates.   <br /><br />

    -   **Gedrag voor opnieuw opstarten:** Gebruik deze informatie opgeven over het gedrag voor updates opnieuw opstarten. Deze instelling heeft geen invloed op de werkelijke gedrag van de installatie van de update.

        -   **Nooit opnieuw opgestart**: De computer voert nooit opnieuw opstarten na de installatie van de software-update.
        -   **Altijd vereist opnieuw opstarten**: De computer wordt altijd opnieuw opstarten na de installatie van de software-update uitvoert.
        -   **Opnieuw opstarten kunnen aanvragen**: De computer vraagt systeem opnieuw is opgestart na de installatie van de software-update alleen als een herstart nodig is. De gebruiker heeft de optie voor opnieuw opstarten uitstellen. Dit is de standaardwaarde. <br /><br />

2.  Op de **vereiste** pagina, geeft u de vereisten die op een computer moeten worden geïnstalleerd voordat deze update kunt installeren. De regels worden genoemd **detectoids**. Detectoids zijn op hoog niveau regels zoals die de computers CPU alleen moet een 64-bits processor. Detectoids kunt ook opgeven voor specifieke updates die moeten worden geïnstalleerd voordat deze update kunt installeren.

    -   Gebruik voor betere prestaties detectoids in plaats van het maken van *installeerbare* en *geïnstalleerd regels* die de controle van dezelfde of een actie uitvoert.

 Gebruik de zoekopties voor **beschikbare software-updates en detectoids** kunt u specifieke detectoids vinden. Bijvoorbeeld, zoekt u naar **CPU** de detectoids vinden waarmee u de installatie op basis van specifieke CPU-architectuur beperken.

 U kunt een of meer detectoids tegelijk toe te voegen als een vereiste selecteren. Als u de vereisten, worden de geselecteerde detectoids toegevoegd als een of meer groepen. Om te kwalificeren voor installatie, moet een computer voldoen aan de vereisten van ten minste één lid van elke groep die u configureert:

 -   Wanneer u klikt op **vereiste toevoegen** alle detectoids die u hebt geselecteerd zijn toegevoegd aan afzonderlijke, afzonderlijke, groepen. Om te kwalificeren voor deze update, moet een computer voldoen aan de vereiste in deze groep en doorgeven vereisten voor groepen die zijn geconfigureerd.

 -   Wanneer u klikt op **groep toevoegen,** alle detectoids die u hebt geselecteerd op een afzonderlijke groep worden toegevoegd. Om te kwalificeren voor deze update, moet een computer voldoen aan ten minste één van de vereisten van deze groep en slagen vereisten voor groepen die zijn geconfigureerd.

1.  Op de **vervanging** pagina, geeft u de updates die zijn vervangen door deze update (vervangen). Als deze update is gepubliceerd, Configuration Manager elke update die wordt vervangen als markeert **verlopen**. Clients installeert vervolgens deze update in plaats van de vervangen updates.

2.  Op de **toepasbaarheid** pagina gebruik de **regel Editor** gedefinieerd voor een set van regels die bepalen of een apparaat deze update moet. (Deze pagina is vergelijkbaar met de **geïnstalleerde** pagina die erna komt.)

    Een nieuwe regel toevoegen, klikt u op ![Nieuwe regel](media/newrule.png). Hiermee opent u de toepasselijkheid regel pagina waar u regels kunt configureren.

    Type kunt u regels omvatten:

    -   **Bestand** : met deze regel gebruiken om te vereisen dat een apparaat beschikt over een bestand met eigenschappen die voldoen aan een of meer opgegeven criteria voordat deze update kunnen worden toegepast.

    -   **Register –** dit type gebruiken om op te geven Registerdetails die aanwezig zijn moeten voordat een apparaat, gelden deze update te installeren.

    -   **Systeem –** met deze regel details van systeem gebruikt om te bepalen van toepassing. U kunt kiezen tussen een Windows-versie, een Windows-taal, processorarchitectuur definiëren of geef een WMI-query om te identificeren van het besturingssysteem voor apparaten.

    -   **Windows Installer-** Gebruik dit regeltype om te bepalen op basis van een geïnstalleerde toepassing. MSI- of Windows Installer-patch (. MSP). U kunt ook bepalen of specifieke onderdelen of onderdelen zijn geïnstalleerd als onderdeel van de vereiste.

        > [!IMPORTANT]  
        > Op beheerde deices, de Windows Update Agent kan niet detecteren Windows installeren pakketten die per gebruiker geïnstalleerd. Wanneer u dit regeltype, aanvullende voorwaarden, zoals bestandsversies of registersleutelwaarden, zo configureren dat de Windows Installer-pakket correct ongeacht basis per gebruiker of per systeem kan worden gedetecteerd.

    -   **Regel – opgeslagen** deze optie kunt u vinden en gebruikt u regels *gemaakt in de werkruimte regels*.

        Nadat u een regel hebt gemaakt, kunt u de andere pictogrammen te wijzigen van de regel en als er meerdere regels om relaties tussen deze regels te definiëren.

 Wanneer u bent gereed maken en regels toe te voegen, klikt u op **OK** in de **maken regel instellen** in het dialoogvenster Opslaan als deze is ingesteld. U kunt dan maken een **New** regel en die ook de set toe te voegen.

 Wanneer er meerdere regels of regel toevoegen aan een update wordt ingesteld, kunt u de logische operators in de **regel Editor** vastgesteld tussen de regels en de volgorde waarin ze worden verwerkt.

1.  Op de **geïnstalleerde** pagina gebruik de **regel Editor om te** gedefinieerd voor een set regels die bepalen of een apparaat al is geïnstalleerd met de update die u configureert. (Deze pagina is vergelijkbaar met de **toepasbaarheid** pagina die deze pagina wordt voortgezet.)

    Deze pagina van de wizard configureren regels met dezelfde opties en criteria zoals ondersteunt de **toepasbaarheid** pagina.

Wanneer de wizard is voltooid, wordt de nieuwe update toegevoegd aan een knooppunt in de **werkruimte Updates** die wordt geïdentificeerd door de **leverancier** naam die u voor deze update gebruikt.

## <a name="use-the-create-bundle-wizard"></a>Gebruik de wizard pakket maken
Omdat deze wizard maakt gebruik van dezelfde workflow als de [maken bijwerken wizard](#use-the-create-update-wizard), die werkstroom gebruiken, maar let op het volgende verschil voor bundels:

1.  Start de wizard, in de console gaat u naar **werkruimte Updates**, en selecteer vervolgens **bundel** van de **Start** tabblad van het lint.

2.  In tegenstelling tot de wizard maken bijwerken is er geen pakketpagina bij het maken van een bundel.

3.  Op de **informatie** pagina, geef de details van de updatebundel die opgenomen zijn wanneer de update is gepubliceerd of geëxporteerd.

4.  Op de **optionele Info** pagina kunt u de details die aanvullende informatie over de updatebundel geven. De beschikbare opties zijn hetzelfde als die voor het maken van een update. Opties voor Impact en het gedrag voor opnieuw opstarten zijn echter niet beschikbaar omdat ze niet van toepassing op bundels.

5.  Op de **vereiste** pagina, geeft u de vereisten die op een computer moeten worden geïnstalleerd voordat dit pakket installeert. Deze regels zijn hetzelfde als voor de afzonderlijke updates gezien.

6.  Op de **vervanging** pagina, geeft u de updates die zijn vervangen door deze updatebundel (vervangen). Deze regels zijn hetzelfde als voor de afzonderlijke updates gezien.

7.  Op de **leden** pagina als u updates toevoegen aan de updatebundel selecteren. Alleen updates die u hebt gemaakt of importeren in Updates Publisher zijn beschikbaar.

Wanneer de wizard is voltooid, wordt de nieuwe updatebundel toegevoegd aan een knooppunt in de **werkruimte Updates** die wordt geïdentificeerd door de **leverancier** naam die u voor de updatebundel gebruikt.

