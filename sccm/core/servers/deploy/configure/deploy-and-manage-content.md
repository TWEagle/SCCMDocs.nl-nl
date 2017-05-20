---
title: Inhoud implementeren | Microsoft-documenten
description: Nadat u distributiepunten voor System Center Configuration Manager, is hier hoe u kunt beginnen met inhoud op deze te implementeren.
ms.custom: na
ms.date: 10/06/2016
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: d50dcca0-4419-449d-a487-73abcadf328f
caps.latest.revision: 6
author: Brenduns
ms.author: brenduns
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 1a4a9da88caba55d9e340c7fb1f31f4e3b957f3e
ms.openlocfilehash: 36b08285ef78d0acb9ba9c44abe2d57e311d44b3
ms.contentlocale: nl-nl
ms.lasthandoff: 05/17/2017

---
# <a name="deploy-and-manage-content-for-system-center-configuration-manager"></a>Implementeren en beheren van inhoud voor System Center Configuration Manager

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*

Nadat u distributiepunten voor System Center Configuration Manager installeert, kunt u voor het implementeren van inhoud om ze te beginnen. Normaal gesproken inhoud naar distributiepunten worden verstuurd over het netwerk, maar andere opties inhoud naar de distributiepunten op te halen bestaat. Nadat inhoud naar een distributiepunt overdraagt, kunt u bijwerken, distribueren, verwijderen en die inhoud op distributiepunten valideert.  

##  <a name="bkmk_distribute"></a>Inhoud distribueren  
 Normaal gesproken distribueert u inhoud naar distributiepunten zodat deze beschikbaar zijn voor clientcomputers. (De uitzondering hierop is wanneer u de distributie van inhoud op aanvraag voor een specifieke implementatie gebruikt.)  Wanneer u inhoud distribueert, wordt Configuration Manager slaat inhoudsbestanden in een pakket en distribueert het pakket vervolgens naar het distributiepunt. Type inhoud dat u distribueren kunt, omvatten:  

-   Typen toepassingsimplementatie  

-   Pakketten  

-   Implementatiepakketten  

-   Driverpakketten  

-   Installatiekopieën van besturingssysteem  

-   Installatieprogramma's van besturingssysteem  

-   Installatiekopieën  

-   Takenreeksen  

Wanneer u een pakket maakt dat bronbestanden, zoals een toepassingstype of implementatiepakket bevat, wordt de site waarop het pakket wordt gemaakt de site-eigenaar voor de pakketinhoudsbron. Configuration Manager kopieert de bronbestanden van het bronbestandspad dat u opgeeft voor het object naar de Inhoudsbibliotheek op de siteserver die de pakketinhoudsbron bezit.  Configuration Manager repliceert vervolgens de gegevens naar extra sites. (Zie [de Inhoudsbibliotheek](../../../../core/plan-design/hierarchy/the-content-library.md) voor meer informatie hierover.)  

Gebruik de volgende procedure om inhoud naar distributiepunten te distribueren.  

#### <a name="to-distribute-content-on-distribution-points"></a>Inhoud op distributiepunten distribueren  

1.  Klik in de Configuration Manager-console op **Softwarebibliotheek**.  

2.  In de **softwarebibliotheek** werkruimte, selecteer een van de volgende stappen voor het type inhoud dat u wilt distribueren:  

    -   **Toepassingen**: Vouw **Toepassingsbeheer** > **toepassingen**, en selecteer vervolgens de toepassingen die u wilt distribueren.  

    -   **Pakketten**: Vouw **Toepassingsbeheer** >  **pakketten**, en selecteer vervolgens de pakketten die u wilt distribueren.  

    -   **Implementatiepakketten**: Vouw **Software-Updates** >  **implementatiepakketten**, en selecteer vervolgens de implementatiepakketten die u wilt distribueren.  

    -   **Stuurprogrammapakketten**: Vouw **besturingssystemen** >  **stuurprogrammapakketten**, en selecteer vervolgens de stuurprogrammapakketten die u wilt distribueren.  

    -   **Installatiekopieën van besturingssystemen**: Vouw **besturingssystemen** >  **installatiekopieën van besturingssystemen**, en selecteer vervolgens de installatiekopieën van het besturingssysteem die u wilt distribueren.  

    -   **Installatieprogramma's van besturingssysteem**: Vouw **besturingssystemen** > **installatieprogramma's van besturingssysteem**, en selecteer vervolgens de installatieprogramma's van besturingssysteem die u wilt distribueren.  

    -   **Opstartinstallatiekopieën**: Vouw **besturingssystemen** >  **opstartinstallatiekopieën**, en selecteer vervolgens de installatiekopieën die u wilt distribueren.  

    -   **Takenreeksen**: Vouw **besturingssystemen** >  **Takenreeksen**, en selecteer vervolgens de takenreeks die u wilt distribueren. Ondanks dat takenreeksen geen inhoud bevatten, zijn deze gekoppeld aan inhoudsafhankelijkheden die worden gedistribueerd.  

        > [!NOTE]  
        >  Als u de takenreeks aanpast, moet u de inhoud opnieuw distribueren.  

3.  Klik op het tabblad **Start** in de groep **Implementatie** op **Inhoud distribueren**. De Wizard inhoud distribueren wordt geopend.  

4.  Op de **algemeen** pagina, Controleer of de vermelde inhoud de inhoud die u wilt distribueren, kies of u Configuration Manager om te detecteren die zijn gekoppeld aan de geselecteerde inhoud en voeg de afhankelijkheden toe aan de distributie en klik vervolgens op **volgende**.  

    > [!NOTE]  
    >  U hebt de mogelijkheid om de **detecteren van gekoppelde inhoud herkennen en toevoegen aan deze distributie** instelling alleen voor het inhoudstype van de toepassing. Configuration Manager wordt automatisch geconfigureerd voor deze instelling voor takenreeksen en kan niet worden gewijzigd.  

5.  Op de **inhoud** tabblad, Controleer of de vermelde inhoud de inhoud die u wilt distribueren en klik vervolgens op **volgende**.  

    > [!NOTE]  
    >  De **inhoud** pagina wordt alleen weergegeven als de **detecteren van gekoppelde inhoud herkennen en toevoegen aan deze distributie** instelling is geselecteerd op de **algemeen** pagina van de wizard.  

6.  Op de **doel van inhoud** pagina, klikt u op **toevoegen**, kies een van de volgende en volg de bijbehorende stappen:  

    -   **Verzamelingen**: Selecteer **Gebruikersverzamelingen** of **Apparaatverzamelingen**, klikt u op de verzameling die is gekoppeld aan een of meer distributiepuntgroepen en klik vervolgens op **OK**.  

        > [!NOTE]  
        >  Alleen de verzamelingen die gekoppeld aan een distributiepuntgroep zijn worden weergegeven. Zie voor meer informatie over het koppelen van verzamelingen aan distributiepuntgroepen [distributiepuntgroepen beheren](../../../../core/servers/deploy/configure/install-and-configure-distribution-points.md#bkmk_manage) in de [installeren en configureren van distributiepunten voor System Center Configuration Manager](../../../../core/servers/deploy/configure/install-and-configure-distribution-points.md) onderwerp.  

    -   **Distributiepunt**: Selecteer een bestaand distributiepunt en klik vervolgens op **OK**. Distributiepunten die eerder inhoud hebben ontvangen, worden niet weergegeven.  

    -   **Distributiepuntgroep**: Selecteer een bestaande distributiepuntgroep en klik vervolgens op **OK**. Distributiepuntgroepen die eerder inhoud hebben ontvangen, worden niet weergegeven.  

    Wanneer u klaar bent met het toevoegen van doelen van inhoud, klikt u op **volgende**.  

7.  Op de **samenvatting** pagina, Controleer de instellingen voor de distributie voordat u doorgaat. De om inhoud te distribueren naar de geselecteerde doelen, klikt u op **volgende**.  

8.  De **voortgang** pagina wordt de voortgang van de distributie weergegeven.  

9. De **bevestiging** pagina geeft aan of de inhoud aan de punten is toegewezen. Zie voor het controleren van de distributie van inhoud [inhoud die u hebt gedistribueerd met System Center Configuration Manager controleren](../../../../core/servers/deploy/configure/monitor-content-you-have-distributed.md).  

##  <a name="bkmk_prestage"></a>Gebruik voorbereide inhoud  
 U kunt de inhoudsbestanden voor toepassingen en pakkettypen voorbereiden:  

-   In de Configuration Manager-console selecteert u de inhoud die u nodig hebt en gebruik vervolgens de **maken Wizard voorbereid inhoudsbestand** voor het maken van een gecomprimeerd, voorbereid inhoudsbestand dat de bestanden en gekoppelde metagegevens voor de inhoud die u hebt geselecteerd bevat.  

-   U kunt vervolgens de inhoud op een siteserver, secundaire site handmatig importeren of distributiepunt.  

-   Als u het voorbereide inhoudsbestand op een siteserver importeert, worden de inhoudsbestanden toegevoegd aan de Inhoudsbibliotheek op de siteserver en vervolgens geregistreerd in de siteserverdatabase.  

-   Als u het voorbereide inhoudsbestand op een distributiepunt importeert, worden de inhoudsbestanden worden toegevoegd aan de Inhoudsbibliotheek op het distributiepunt en een statusbericht verzonden naar de siteserver die de site informeert dat de inhoud beschikbaar op het distributiepunt is.  

**Beperkingen en overwegingen voor voorbereide inhoud:**  

-   **Wanneer het distributiepunt zich bevindt op de siteserver**, schakel het distributiepunt voor voorbereide inhoud niet in. Gebruik in plaats daarvan de procedure in [het voorbereiden van inhoud op een distributiepunt op een siteserver](#bkmk_dpsiteserver).  

-   **Wanneer het distributiepunt is geconfigureerd als een pull-distributiepunt**, schakel het distributiepunt voor voorbereide inhoud niet in. De configuratie voor voorbereide inhoud voor een distributiepunt schakelt de configuratie van pull-distributiepunt. Een pull-distributiepunt dat is geconfigureerd voor voorbereide inhoud heeft geen pull-inhoud van brondistributiepunt en ontvangt geen inhoud vanaf de siteserver.  

-   **De Inhoudsbibliotheek moet worden gemaakt op het distributiepunt voordat u inhoud op het distributiepunt voorbereiden kunt**. Distribueer via het netwerk ten minste één keer inhoud voordat u inhoud vooraf op het distributiepunt.  

-   **Wanneer u inhoud voorbereid voor een pakket met een lang pakketbronpad** (bijvoorbeeld meer dan 140 tekens), het opdrachtregelprogramma Extract Content mogelijk niet de inhoud voor het desbetreffende pakket naar de Inhoudsbibliotheek te pakken.  

Zie voor meer informatie over het voorbereiden van inhoudsbestanden *voorbereide inhoud* in de [beheer van netwerkbandbreedte voor inhoudsbeheer](/sccm/core/plan-design/hierarchy/manage-network-bandwidth) onderwerp.  

Gebruik de volgende secties voor het voorbereiden van inhoud.  

###  <a name="BKMK_CreatePrestagedContentFile"></a>Stap 1: Een voorbereid inhoudsbestand maken  
 U kunt een gecomprimeerd, voorbereid inhoudsbestand dat de bestanden en gekoppelde metagegevens voor de inhoud die u in de Configuration Manager-console selecteert bevat. Gebruik de volgende procedure om een voorbereid inhoudsbestand te maken.  

##### <a name="to-create-a-prestaged-content-file"></a>Een voorbereid inhoudsbestand maken  

1.  Klik in de Configuration Manager-console op **Softwarebibliotheek**.  

2.  In de **softwarebibliotheek** werkruimte, selecteer een van de volgende stappen voor het type inhoud dat u wilt voorbereiden:  

    -   **Toepassingen**: Vouw **Toepassingsbeheer**, klikt u op **toepassingen**, en selecteer vervolgens de toepassingen die u wilt voorbereiden.  

    -   **Pakketten**: Vouw **Toepassingsbeheer**, klikt u op **pakketten**, en selecteer vervolgens de pakketten die u wilt voorbereiden.  

    -   **Stuurprogrammapakketten**: Vouw **besturingssystemen**, klikt u op **stuurprogrammapakketten**, en selecteer vervolgens de stuurprogrammapakketten die u wilt voorbereiden.  

    -   **Installatiekopieën van besturingssystemen**: Vouw **besturingssystemen**, klikt u op **installatiekopieën van besturingssystemen**, en selecteer vervolgens de installatiekopieën van het besturingssysteem die u wilt voorbereiden.  

    -   **Installatieprogramma's van besturingssysteem**: Vouw **besturingssystemen**, klikt u op **installatieprogramma's van besturingssysteem**, en selecteer vervolgens de installatieprogramma's van besturingssysteem die u wilt voorbereiden.  

    -   **Opstartinstallatiekopieën**: Vouw **besturingssystemen**, klikt u op **opstartinstallatiekopieën**, en selecteer vervolgens de installatiekopieën die u wilt voorbereiden.  

    -   **Takenreeksen**: Vouw **besturingssystemen**, klikt u op **Takenreeksen**, en selecteer vervolgens de takenreeks die u wilt voorbereiden.  

3.  Op de **Start** tabblad, in de **implementatie** groep, klikt u op **voorbereid inhoudsbestand maken**. Het maken van Wizard voorbereid inhoudsbestand wordt geopend.  

    > [!NOTE]  
    >  **Voor toepassingen:** Op de **Start** tabblad, in de **toepassing** groep, klikt u op **voorbereid inhoudsbestand maken**.  
    >   
    >  **Voor pakketten:** Op de **Start** tabblad, in de &lt; *PackageName*> groep, klikt u op **voorbereid inhoudsbestand maken**.  

4.  Op de **algemeen** pagina, klikt u op **Bladeren**, kies de locatie voor het voorbereide inhoudsbestand, Geef een naam voor het bestand en klik vervolgens op **opslaan**. Dit voorbereide inhoudsbestand op primaire siteservers, secundaire siteservers of distributiepunten kunt u de inhoud en metagegevens te importeren.  

5.  Selecteer voor toepassingen **alle afhankelijkheden exporteren** om Configuration Manager detecteert en de afhankelijkheden die zijn gekoppeld aan de toepassing voor het voorbereide inhoudsbestand toevoegt. Deze instelling is standaard geselecteerd.  

6.  In **beheerderopmerkingen**Voer optionele opmerkingen in over het voorbereide inhoudsbestand en klik vervolgens op **volgende**.  

7.  Op de **inhoud** pagina, Controleer of de vermelde inhoud de inhoud die u wilt toevoegen aan het voorbereide inhoudsbestand en klik vervolgens op **volgende**.  

8.  Op de **inhoudslocaties** pagina, de distributiepunten opgeven vanaf welke u wilt ophalen van de inhoudsbestanden voor het voorbereide inhoudsbestand. U kunt meer dan één distributiepunt selecteren voor ophalen van de inhoud. De distributiepunten worden weergegeven in de sectie inhoudslocaties. De **inhoud** kolom wordt weergegeven hoeveel van de geselecteerde pakketten of toepassingen beschikbaar zijn op elk distributiepunt. Configuration Manager begint met het eerste distributiepunt in de lijst om op te halen van de geselecteerde inhoud en gaat vervolgens omlaag in de lijst om op te halen van de resterende inhoud vereist is voor het voorbereide inhoudsbestand. Klik op **omhoog verplaatsen** of **omlaag verplaatsen** om de prioriteitsvolgorde van de distributiepunten te wijzigen. Als de distributiepunten in de lijst niet alle geselecteerde inhoud bevatten, moet u distributiepunten toevoegen aan de lijst die de inhoud bevatten of de wizard afsluiten, de inhoud naar ten minste één distributiepunt distribueren en vervolgens de wizard opnieuw starten.  

9. Op de **samenvatting** pagina, om de details te bevestigen. U kunt teruggaan naar vorige pagina's en wijzigingen aanbrengen. Klik op **volgende** voor het maken van het voorbereide inhoudsbestand.  

10. De **voortgang** pagina wordt de inhoud die wordt toegevoegd aan het voorbereide inhoudsbestand weergegeven.  

11. Op de **voltooiing** pagina, Controleer of het voorbereide inhoudsbestand is gemaakt en klik vervolgens op **sluiten**.  

###  <a name="BKMK_AssignContentToDistributionPoint"></a>Stap 2: De inhoud toewijzen aan distributiepunten  
 Nadat u het inhoudsbestand hebt voorbereid, moet u de inhoud toewijzen aan distributiepunten.  

> [!NOTE]  
>  Wanneer u een voorbereid inhoudsbestand gebruikt voor het herstellen van de Inhoudsbibliotheek op een siteserver, en niet hoeven te voorbereiden van de inhoudsbestanden op een distributiepunt, kunt u deze procedure overslaan.  

 Gebruikt de volgende procedure om de inhoud van het voorbereide inhoudsbestand toewijzen aan distributiepunten.  

> [!IMPORTANT]  
>  Controleer of dat de distributiepunten die u wilt voorbereiden worden configureren als voorbereide distributiepunten of dat de inhoud wordt gedistribueerd naar de distributiepunten via het netwerk.  

##### <a name="to-assign-the-content-to-distribution-points"></a>De inhoud toewijzen aan distributiepunten  

1.  Klik in de Configuration Manager-console op **Softwarebibliotheek**.  

2.  In de **softwarebibliotheek** werkruimte, selecteer een van de volgende voor het type inhoud dat u hebt geselecteerd stappen bij het maken van het voorbereide inhoudsbestand:  

    -   **Toepassingen**: Vouw **Toepassingsbeheer**, klikt u op **toepassingen**, en selecteer vervolgens de toepassingen die u hebt voorbereid.  

    -   **Pakketten**: Vouw **Toepassingsbeheer**, klikt u op **pakketten**, en selecteer vervolgens de pakketten die u hebt voorbereid.  

    -   **Implementatiepakketten**: Vouw **Software-Updates**, klikt u op **implementatiepakketten**, en selecteer vervolgens de implementatiepakketten die u hebt voorbereid.  

    -   **Stuurprogrammapakketten**: Vouw **besturingssystemen**, klikt u op **stuurprogrammapakketten**, en selecteer vervolgens de stuurprogrammapakketten die u hebt voorbereid.  

    -   **Installatiekopieën van besturingssystemen**: Vouw **besturingssystemen**, klikt u op **installatiekopieën van besturingssystemen**, en selecteer vervolgens de installatiekopieën van besturingssystemen die u hebt voorbereid.  

    -   **Installatieprogramma's van besturingssysteem**: Vouw **besturingssystemen**, klikt u op **installatieprogramma's van besturingssysteem**, en selecteer vervolgens de installatieprogramma's van besturingssysteem die u hebt voorbereid.  

    -   **Opstartinstallatiekopieën**: Vouw **besturingssystemen**, klikt u op **opstartinstallatiekopieën**, en selecteer vervolgens de installatiekopieën die u hebt voorbereid.  

3.  Klik op het tabblad **Start** in de groep **Implementatie** op **Inhoud distribueren**. De Wizard inhoud distribueren wordt geopend.  

4.  Op de **algemeen** pagina, Controleer of de vermelde inhoud de inhoud die u hebt voorbereid, kies of u Configuration Manager om te detecteren die zijn gekoppeld aan de geselecteerde inhoud en voeg de afhankelijkheden toe aan de distributie en klik vervolgens op **volgende**.  

    > [!NOTE]  
    >  U hebt de mogelijkheid om de **detecteren van gekoppelde inhoud herkennen en toevoegen aan deze distributie** instelling alleen voor het inhoudstype van de toepassing. Configuration Manager wordt automatisch geconfigureerd voor deze instelling voor takenreeksen en kan niet worden gewijzigd.  

5.  Op de **inhoud** pagina weergegeven, Controleer of de vermelde inhoud de inhoud die u wilt distribueren en klik vervolgens op **volgende**.  

    > [!NOTE]  
    >  De **inhoud** pagina wordt alleen weergegeven als de **detecteren van gekoppelde inhoud herkennen en toevoegen aan deze distributie** instelling is geselecteerd op de **algemeen** pagina van de wizard.  

6.  Op de **doel van inhoud** pagina, klikt u op **toevoegen**, kies een van de volgende mogelijkheden voor de te voorbereiden distributiepunten en volg de bijbehorende stappen:  

    -   **Verzamelingen**: Selecteer **Gebruikersverzamelingen** of **Apparaatverzamelingen**, klikt u op de verzameling die is gekoppeld aan een of meer distributiepuntgroepen en klik vervolgens op **OK**.  

        > [!NOTE]  
        >  Alleen de verzamelingen die gekoppeld aan een distributiepuntgroep zijn worden weergegeven.  Zie voor meer informatie [distributiepuntgroepen beheren](../../../../core/servers/deploy/configure/install-and-configure-distribution-points.md#bkmk_manage) in de [installeren en configureren van distributiepunten voor System Center Configuration Manager](../../../../core/servers/deploy/configure/install-and-configure-distribution-points.md) onderwerp.  

    -   **Distributiepunt**: Selecteer een bestaand distributiepunt en klik vervolgens op **OK**. Distributiepunten die eerder inhoud hebben ontvangen, worden niet weergegeven.  

    -   **Distributiepuntgroep**: Selecteer een bestaande distributiepuntgroep en klik vervolgens op **OK**. Distributiepuntgroepen die eerder inhoud hebben ontvangen, worden niet weergegeven.  

    Wanneer u klaar bent met het toevoegen van doelen van inhoud, klikt u op **volgende**.  

7.  Op de **samenvatting** pagina, Controleer de instellingen voor de distributie voordat u doorgaat. De om inhoud te distribueren naar de geselecteerde doelen, klikt u op **volgende**.  

8.  De **voortgang** pagina wordt de voortgang van de distributie weergegeven.  

9. De **bevestiging** pagina weergegeven of de inhoud aan de distributiepunten is toegewezen. Zie voor het controleren van de distributie van inhoud [inhoud die u hebt gedistribueerd met System Center Configuration Manager controleren](../../../../core/servers/deploy/configure/monitor-content-you-have-distributed.md).  

###  <a name="BKMK_ExportContentFromPrestagedContentFile"></a>Stap 3: De inhoud van het voorbereide inhoudsbestand uitpakken  
 Nadat u het voorbereide inhoudsbestand hebt gemaakt en de inhoud aan distributiepunten toewijzen, kunt u de inhoudsbestanden naar de Inhoudsbibliotheek op een siteserver of distributiepunt uitpakken. Normaal gesproken u het voorbereide inhoudsbestand hebt gekopieerd naar een draagbaar medium zoals een USB-station of hebben inhoud media zoals DVD branden en is deze beschikbaar op de locatie van de siteserver of distributiepunt waarvoor de inhoud vereist.  

 Gebruik de volgende procedure om handmatig de inhoudsbestanden van het voorbereide inhoudsbestand via het opdrachtregelprogramma voor het uitpakken van inhoud.  

> [!IMPORTANT]  
>  Wanneer u het opdrachtregelprogramma voor het uitpakken van inhoud uitvoert, maakt het hulpprogramma een tijdelijk bestand alsof het voorbereide inhoudsbestand wordt gemaakt. Vervolgens wordt het bestand wordt gekopieerd naar de doelmap en het tijdelijke bestand wordt verwijderd. U moet voldoende schijfruimte beschikbaar voor dit tijdelijke bestand of het proces is mislukt. Het tijdelijke bestand gemaakt in de volgende locatie:  
>   
>  -   Het tijdelijke bestand is in dezelfde map die u als de doelmap voor het voorbereide inhoudsbestand opgeeft gemaakt.  

> [!IMPORTANT]  
>  De gebruiker die het opdrachtregelprogramma voor het uitpakken van inhoud uitvoert moet beschikken over **Administrator** rechten op de computer van waaruit u de voorbereide inhoud wordt uitgepakt.  

##### <a name="to-extract-the-content-files-from-the-prestaged-content-file"></a>De inhoudsbestanden ophalen uit het voorbereide inhoudsbestand  

1.  Kopieer het voorbereide inhoudsbestand naar de computer van waaruit u wilt ophalen van de inhoud.  

2.  Kopieer het opdrachtregelprogramma Extract Content van &lt; *Configmgrinstallatiepad*> \bin\\&lt;*platform*> naar de computer van waaruit u wilt ophalen van het voorbereide inhoudsbestand.  

3.  Open de opdrachtprompt en navigeer naar de maplocatie van het voorbereide inhoudsbestand en het opdrachtregelprogramma voor uitpakken van inhoud.  

    > [!NOTE]  
    >  U kunt een uitpakken of meer voorbereide inhoudsbestanden op een siteserver, secundaire siteserver of distributiepunt.  

4.  Type **extractcontent/p:**&lt;*locatie*>**\\**&lt;*PrestagedFileName*> **/S** één bestand importeren.  

     Type **extractcontent/p:**&lt;*locatie*> **/S** importeren alle voorbereide bestanden in de opgegeven map.  

     Typ bijvoorbeeld **extractcontent /P:D:\PrestagedFiles\MyPrestagedFile.pkgx /S** waar `D:\PrestagedFiles\` is de locatie `MyPrestagedFile.pkgx` is de voorbereide bestandsnaam en `/S` informeert Configuration Manager voor alleen inhoudsbestanden uitpakt bestanden die nieuwer zijn dan wat er op het distributiepunt.  

     Wanneer u het voorbereide inhoudsbestand op een siteserver pakt, de inhoudsbestanden worden toegevoegd aan de Inhoudsbibliotheek op de siteserver en vervolgens wordt de beschikbaarheid van de inhoud geregistreerd in de site server-database. Wanneer u het voorbereide inhoudsbestand op een distributiepunt exporteert, worden de inhoudsbestanden toegevoegd aan de Inhoudsbibliotheek op het distributiepunt, het distributiepunt verzend vervolgens een statusbericht naar de bovenliggende primaire siteserver en vervolgens wordt de beschikbaarheid van de inhoud geregistreerd in de sitedatabase.  

    > [!IMPORTANT]  
    >  In het volgende scenario moet u de inhoud die u hebt opgehaald uit een voorbereid inhoudsbestand wanneer de inhoud wordt bijgewerkt naar een nieuwe versie bijwerken:  
    >   
    >  1.  U maakt een voorbereid inhoudsbestand voor versie 1 van een pakket.  
    >  2.  U werkt de bronbestanden voor het pakket bij naar versie 2.  
    >  3.  U pakt het voorbereide inhoudsbestand (versie 1 van het pakket) op een distributiepunt.  
    >   
    > Het Pakketversie 2 naar het distributiepunt niet automatisch wordt verzonden door Configuration Manager. Maak een nieuw voorbereid inhoudsbestand dat de nieuwe bestandsversie bevat en vervolgens pakt u de inhoud, werkt u het distributiepunt voor het distribueren van de bestanden die zijn gewijzigd, of alle bestanden in het pakket opnieuw distribueren.  

###  <a name="bkmk_dpsiteserver"></a>Het voorbereiden van inhoud op een distributiepunt op een siteserver  
 Wanneer een distributiepunt op een siteserver is geïnstalleerd, moet u de volgende procedure gebruiken om voor te bereiden inhoud. Dit is omdat de inhoudsbestanden al in de Inhoudsbibliotheek.  

 Wanneer het distributiepunt is niet ingeschakeld voor het voorbereiden van inhoud of wanneer het distributiepunt bevindt zich niet op een siteserver bevindt, ziet de [gebruik voorbereide inhoud](#bkmk_prestage) in dit onderwerp.  

##### <a name="to-prestage-content-on-distribution-points-located-on-a-site-server"></a>Inhoud voorbereiden op distributiepunten die zich bevinden op een siteserver  

1.  Gebruik de volgende stappen uit om te controleren of het distributiepunt niet is ingeschakeld voor voorbereide inhoud.  

    1.  Klik op **Beheer**in de Configuration Manager-console.  

    2.  In de **beheer** werkruimte, klikt u op **distributiepunten**, en selecteer vervolgens het distributiepunt dat zich op de siteserver.  

    3.  Klik op **Eigenschappen** in het tabblad **Start** , in de groep **Eigenschappen**.  

    4.  Op de **algemeen** tabblad, controleert u of de **dit distributiepunt inschakelen voor voorbereide inhoud** selectievakje niet is ingeschakeld.  

2.  Het voorbereide inhoudsbestand te maken met behulp van de [stap 1: Een voorbereid inhoudsbestand maken](#BKMK_CreatePrestagedContentFile) in dit onderwerp.  

3.  De inhoud toewijzen aan het distributiepunt met behulp van de [stap 2: De inhoud toewijzen aan distributiepunten](#BKMK_AssignContentToDistributionPoint) in dit onderwerp.  

4.  Op de siteserver, moet u de inhoud van het voorbereide inhoudsbestand uitpakken met behulp van de [stap 3: De inhoud van het voorbereide inhoudsbestand uitpakken](#BKMK_ExportContentFromPrestagedContentFile) in dit onderwerp.  

    > [!NOTE]  
    >  Wanneer het distributiepunt zich op een secundaire site, Wacht minstens 10 minuten en klik vervolgens met behulp van een Configuration Manager-console die is verbonden met de bovenliggende primaire site de inhoud toewijzen aan het distributiepunt op de secundaire site.  

##  <a name="bkmk_manage"></a>De inhoud die u hebt gedistribueerd beheren  
 U hebt de volgende opties om inhoud te beheren:  
 - [Inhoud bijwerken](#update-content)
 - [Inhoud opnieuw distribueren](#redistribute-content)
 - [Inhoud verwijderen](#remove-content)
 - [inhoud valideren](#validate-content)

### <a name="update-content"></a>Inhoud bijwerken
Wanneer de locatie van het bronbestand voor een implementatie wordt bijgewerkt door het toevoegen van nieuwe of bestaande bestanden met een nieuwere versie vervangen, kunt u de inhoudsbestanden op distributiepunten bijwerken via de **distributiepunten bijwerken** of **inhoud bijwerken** actie:  
-   De inhoudsbestanden van het bronbestandspad gekopieerd naar de Inhoudsbibliotheek op de site die de pakketinhoudsbron bezit  
-   De pakketversie stapsgewijs is verhoogd  
-   Elk exemplaar van de Inhoudsbibliotheek op siteservers en op distributiepunten verwijst updates met alleen de bestanden die zijn gewijzigd  

> [!WARNING]  
>  De pakketversie voor toepassingen is altijd 1. Wanneer u de inhoud voor een toepassingsimplementatietype bijwerkt, maakt Configuration Manager een nieuwe content-ID voor het implementatietype en verwijst het pakket naar de nieuwe content-ID.  

#### <a name="to-update-content-on-distribution-points"></a>Inhoud op distributiepunten bijwerken  

1.  Klik in de Configuration Manager-console op **Softwarebibliotheek**.  

2.  In de **softwarebibliotheek** werkruimte, selecteer een van de volgende stappen voor het type inhoud dat u wilt distribueren:  

    -   **Toepassingen**: Vouw **Toepassingsbeheer** > **toepassingen**, en selecteer vervolgens de toepassingen die u wilt distribueren. Klik op de **implementatietypen** tabblad en selecteer vervolgens het implementatietype dat u wilt bijwerken.  

    -   **Pakketten**: Vouw **Toepassingsbeheer** > **pakketten**, en selecteer vervolgens de pakketten die u wilt bijwerken.  

    -   **Implementatiepakketten**: Vouw **Software-Updates** > **implementatiepakketten**, en selecteer vervolgens de implementatiepakketten die u wilt bijwerken.  

    -   **Stuurprogrammapakketten**: Vouw **besturingssystemen** > **stuurprogrammapakketten**, en selecteer vervolgens de stuurprogrammapakketten die u wilt bijwerken.  

    -   **Installatiekopieën van besturingssystemen**: Vouw **besturingssystemen** > **installatiekopieën van besturingssystemen**, en selecteer vervolgens de installatiekopieën van het besturingssysteem die u wilt bijwerken.  

    -   **Installatieprogramma's van besturingssysteem**: Vouw **besturingssystemen** > **installatieprogramma's van besturingssysteem**, en selecteer vervolgens de installatieprogramma's van besturingssysteem die u wilt bijwerken.  

    -   **Opstartinstallatiekopieën**: Vouw **besturingssystemen** >  **opstartinstallatiekopieën**, en selecteer vervolgens de installatiekopieën die u wilt bijwerken.  

3.  Op de **Start** tabblad, in de **implementatie** groep, klikt u op **distributiepunten bijwerken**, en klik vervolgens op **OK** om te bevestigen dat u wilt de inhoud bijwerken.  

    > [!NOTE]  
    >  Inhoud voor toepassingen wilt bijwerken, klikt u op de **implementatietypen** , met de rechtermuisknop op het implementatietype en klik op **inhoud bijwerken**, en klik vervolgens op **OK** om te bevestigen dat u wilt bijwerken van de inhoud.  

    > [!NOTE]  
    >  Wanneer u inhoud voor installatiekopieën bijwerkt, wordt de Wizard distributiepunt beheren geopend. Lees de informatie op de **samenvatting** pagina en voltooi de wizard de inhoud wilt bijwerken.  

### <a name="redistribute-content"></a>Inhoud opnieuw distribueren
U kunt een pakket alle wilt kopiëren van de inhoudsbestanden in het pakket naar distributiepunten opnieuw distribueren of distributie en daarbij de bestaande bestanden te overschrijven.  

 Deze bewerking gebruiken om inhoudsbestanden in het pakket te herstellen of opnieuw verzenden van inhoud wanneer de initiële distributie mislukt. U kunt een pakket opnieuw distribueren:  

-   De eigenschappen van pakket  
-   De eigenschappen van distributiepunt  
-   Eigenschappen van distributiepuntgroepen.  


#### <a name="to-redistribute-content-from-package-properties"></a>Inhoud opnieuw distribueren van de eigenschappen van pakket  

1.  Klik in de Configuration Manager-console op **Softwarebibliotheek**.  

2.  In de **softwarebibliotheek** werkruimte, selecteer een van de volgende stappen voor het type inhoud dat u wilt distribueren:  

    -   **Toepassingen**: Vouw **Toepassingsbeheer** >  **toepassingen**, en selecteer vervolgens de toepassing die u wilt distribueren.  

    -   **Pakketten**: Vouw **Toepassingsbeheer** > **pakketten**, en selecteer vervolgens het pakket dat u wilt distribueren.  

    -   **Implementatiepakketten**: Vouw **Software-Updates** >  **implementatiepakketten**, en selecteer vervolgens het implementatiepakket dat u wilt distribueren.  

    -   **Stuurprogrammapakketten**: Vouw **besturingssystemen** > **stuurprogrammapakketten**, en selecteer vervolgens het stuurprogrammapakket dat u wilt distribueren.  

    -   **Installatiekopieën van besturingssystemen**: Vouw **besturingssystemen** > **installatiekopieën van besturingssystemen**, en selecteer vervolgens de installatiekopie die u wilt distribueren.  

    -   **Installatieprogramma's van besturingssysteem**: Vouw **besturingssystemen** > **installatieprogramma's van besturingssysteem**, en selecteer vervolgens het installatieprogramma van het besturingssysteem dat u wilt distribueren.  

    -   **Opstartinstallatiekopieën**: Vouw **besturingssystemen** >  **opstartinstallatiekopieën**, en selecteer vervolgens de installatiekopie die u wilt distribueren.  

3.  Klik op **Eigenschappen** in het tabblad **Start** , in de groep **Eigenschappen**.  

4.  Klik op de **inhoudslocaties** tabblad, selecteert u het distributiepunt of distributiepuntgroep waarin u wilt distribueren de inhoud, klik op **distribueren**, en klik vervolgens op **OK**.  

#### <a name="to-redistribute-content-from-distribution-point-properties"></a>Inhoud opnieuw distribueren van de eigenschappen van distributiepunt  

1.  Klik op **Beheer**in de Configuration Manager-console.  

2.  In de **beheer** werkruimte, klikt u op **distributiepunten**, en selecteer vervolgens het distributiepunt waarin wordt gezocht naar de inhoud opnieuw distribueren.  

3.  Klik op **Eigenschappen** in het tabblad **Start** , in de groep **Eigenschappen**.  

4.  Klik op de **inhoud** tabblad, selecteer de inhoud opnieuw wilt distribueren, klik op **distribueren**, en klik vervolgens op **OK**.  

#### <a name="to-redistribute-content-from-distribution-point-group-properties"></a>Inhoud opnieuw distribueren van de eigenschappen van distributiepuntgroepen  

1.  Klik op **Beheer**in de Configuration Manager-console.  

2.  In de **beheer** werkruimte, klikt u op **Distributiepuntgroepen**, en selecteer vervolgens de distributiepuntgroep waarin u wilt distribueren van inhoud.  

3.  Klik op **Eigenschappen** in het tabblad **Start** , in de groep **Eigenschappen**.  

4.  Klik op de **inhoud** tabblad, selecteer de inhoud opnieuw wilt distribueren, klik op **distribueren**, en klik vervolgens op **OK**.  

    > [!IMPORTANT]  
    >  De inhoud van het pakket wordt opnieuw gedistribueerd naar alle distributiepunten in de distributiepuntgroep.  


#### <a name="use-the-sdk-to-force-replication-of-content"></a>Gebruik de SDK om af te dwingen de replicatie van inhoud
U kunt de **RetryContentReplication** Windows Management Instrumentation (WMI) methode voor de klasse van de Configuration Manager SDK om af te dwingen Distributiebeheer kopiëren van inhoud naar de Inhoudsbibliotheek op de bronlocatie.  

Gebruik deze methode alleen af te dwingen replicatie wanneer u inhoud opnieuw distribueren moet nadat er problemen met normale replicatie van inhoud zijn (meestal bevestigd door gebruik van het knooppunt controle van de console).   

Zie voor meer informatie over deze optie SDK [RetryContentReplication methode in klasse SMS_CM_UpdatePackages](https://msdn.microsoft.com/library/mt762092(CMSDK.16).aspx) op MSDN. Microsoft.com.

### <a name="remove-content"></a>Inhoud verwijderen
Wanneer u inhoud niet langer op uw distributiepunten vereist, kunt u de inhoudsbestanden op het distributiepunt verwijderen.  

-   De eigenschappen van pakket  
-   De eigenschappen van distributiepunt  
-   Eigenschappen van distributiepuntgroepen.  

Wanneer de inhoud gekoppeld aan een ander pakket dat naar hetzelfde distributiepunt is gedistribueerd is, kan niet u de inhoud verwijderen.  

#### <a name="to-remove-package-content-files-from-distribution-points"></a>Inhoudsbestanden voor pakketten van distributiepunten verwijderen  

1.  Klik in de Configuration Manager-console op **Softwarebibliotheek**.  

2.  In de **softwarebibliotheek** werkruimte, selecteer een van de volgende stappen voor het type inhoud dat u wilt verwijderen:  

    -   **Toepassingen**: Vouw **Toepassingsbeheer** > **toepassingen**, en selecteer vervolgens de toepassing die u wilt verwijderen.  

    -   **Pakketten**: Vouw **Toepassingsbeheer** > **pakketten**, en selecteer vervolgens het pakket dat u wilt verwijderen.  

    -   **Implementatiepakketten**: Vouw **Software-Updates** > **implementatiepakketten**, en selecteer vervolgens het implementatiepakket dat u wilt verwijderen.  

    -   **Stuurprogrammapakketten**: Vouw **besturingssystemen** > **stuurprogrammapakketten**, en selecteer vervolgens het stuurprogrammapakket dat u wilt verwijderen.  

    -   **Installatiekopieën van besturingssystemen**: Vouw **besturingssystemen** > **installatiekopieën van besturingssystemen**, en selecteer vervolgens de installatiekopie die u wilt verwijderen.  

    -   **Installatieprogramma's van besturingssysteem**: Vouw **besturingssystemen** > **installatieprogramma's van besturingssysteem**, en selecteer vervolgens het installatieprogramma van het besturingssysteem dat u wilt verwijderen.  

    -   **Opstartinstallatiekopieën**: Vouw **besturingssystemen** > **opstartinstallatiekopieën**, en selecteer vervolgens de installatiekopie die u wilt verwijderen.  

3.  Klik op **Eigenschappen** in het tabblad **Start** , in de groep **Eigenschappen**.  

4.  Klik op de **inhoudslocaties** tabblad, selecteert u het distributiepunt of distributiepuntgroep waaruit u wilt verwijderen van de inhoud, klikt u op **verwijderen**, en klik vervolgens op **OK**.  

#### <a name="to-remove-package-content-from-distribution-point-properties"></a>Pakketinhoud verwijderen via eigenschappen van distributiepunten  

1.  Klik op **Beheer**in de Configuration Manager-console.  

2.  In de **beheer** werkruimte, klikt u op **distributiepunten**, en selecteer vervolgens het distributiepunt waarin u wilt verwijderen van de inhoud.  

3.  Klik op **Eigenschappen** in het tabblad **Start** , in de groep **Eigenschappen**.  

4.  Klik op de **inhoud** tabblad, selecteer de inhoud wilt verwijderen, klikt u op **verwijderen**, en klik vervolgens op **OK**.  

#### <a name="to-remove-content-from-distribution-point-group-properties"></a>Inhoud te verwijderen van de eigenschappen van distributiepuntgroepen  

1.  Klik op **Beheer**in de Configuration Manager-console.  

2.  In de **beheer** werkruimte, klikt u op **Distributiepuntgroepen**, en selecteer vervolgens de distributiepuntgroep waarin u inhoud wilt verwijderen.  

3.  Klik op **Eigenschappen** in het tabblad **Start** , in de groep **Eigenschappen**.  

4.  Klik op de **inhoud** tabblad, selecteer de inhoud wilt verwijderen, klikt u op **verwijderen**, en klik vervolgens op **OK**.  


### <a name="validate-content"></a>Inhoud valideren
Het inhoudsvalidatieproces controleert de integriteit van inhoudsbestanden op distributiepunten. U schakelt inhoudsvalidatie op basis van een planning, of u kunt handmatig starten validatie van inhoud van de eigenschappen van distributiepunten en pakketten.  

 Wanneer de inhoudsvalidatie start, Configuration Manager controleert of de inhoudsbestanden op distributiepunten en als de bestandshash niet verwacht voor de bestanden op het distributiepunt wordt, Configuration Manager een statusbericht dat u kunt bekijken gemaakt in de **bewaking** werkruimte.  

 Zie voor meer informatie over het configureren van de planning voor inhoudsvalidatie [distributiepuntconfiguraties](../../../../core/servers/deploy/configure/install-and-configure-distribution-points.md#bkmk_configs) in de [installeren en configureren van distributiepunten voor System Center Configuration Manager](../../../../core/servers/deploy/configure/install-and-configure-distribution-points.md) onderwerp.  


#### <a name="to-initiate-content-validation-for-all-content-on-a-distribution-point"></a>Validatie van inhoud voor alle inhoud op een distributiepunt starten  

1.  Klik op **Beheer**in de Configuration Manager-console.  

2.  In de **beheer** werkruimte, klikt u op **distributiepunten**, en selecteer vervolgens het distributiepunt waarin u inhoud wilt valideren.  

3.  Klik op **Eigenschappen** in het tabblad **Start** , in de groep **Eigenschappen**.  

4.  Op de **inhoud** tabblad, selecteert u het pakket waarin u wilt valideren van de inhoud, klikt u op **valideren**, klikt u op **OK**, en klik vervolgens op **OK**. Het inhoudsvalidatieproces wordt geïnitieerd voor het pakket op het distributiepunt.  

5.  De resultaten van het inhoudvalidatieproces weergeven in de **bewaking** werkruimte Vouw **distributiestatus**, en klikt u op de **inhoudsstatus** knooppunt. De inhoud van ieder pakkettype (bijvoorbeeld, toepassing, Software-updatepakket en installatiekopie) wordt weergegeven. Zie voor meer informatie over het controleren van inhoudstatussen [inhoud die u hebt gedistribueerd met System Center Configuration Manager controleren](../../../../core/servers/deploy/configure/monitor-content-you-have-distributed.md).  

#### <a name="to-initiate-content-validation-for-a-package"></a>Validatie van inhoud voor een pakket initiëren  

1.  Klik in de Configuration Manager-console op **Softwarebibliotheek**.  

2.  In de **softwarebibliotheek** werkruimte, selecteer een van de volgende stappen voor het type inhoud dat u wilt valideren:  

    -   **Toepassingen**: Vouw **Toepassingsbeheer** > **toepassingen**, en selecteer vervolgens de toepassing die u wilt valideren.  

    -   **Pakketten**: Vouw **Toepassingsbeheer** > **pakketten**, en selecteer vervolgens het pakket dat u wilt valideren.  

    -   **Implementatiepakketten**: Vouw **Software-Updates** > **implementatiepakketten**, en selecteer vervolgens het implementatiepakket dat u wilt valideren.  

    -   **Stuurprogrammapakketten**: Vouw **besturingssystemen** > **stuurprogrammapakketten**, en selecteer vervolgens het stuurprogrammapakket dat u wilt valideren.  

    -   **Installatiekopieën van besturingssystemen**: Vouw **besturingssystemen** > **installatiekopieën van besturingssystemen**, en selecteer vervolgens de installatiekopie die u wilt valideren.  

    -   **Installatieprogramma's van besturingssysteem**: Vouw **besturingssystemen** >  **installatieprogramma's van besturingssysteem**, en selecteer vervolgens het installatieprogramma van het besturingssysteem dat u wilt valideren.  

    -   **Opstartinstallatiekopieën**: Vouw **besturingssystemen** > **opstartinstallatiekopieën**, en selecteer vervolgens de installatiekopie die u wilt voorbereiden.  

3.  Klik op **Eigenschappen** in het tabblad **Start** , in de groep **Eigenschappen**.  

4.  Op de **inhoudslocaties** tabblad, selecteert u het distributiepunt of distributiepuntgroep waarin u de inhoud, klikt u op valideren **valideren**, klikt u op **OK**, en klik vervolgens op **OK**. Het inhoudvalidatieproces wordt gestart voor de inhoud op het geselecteerde distributiepunt of distributiepuntgroep.  

5.  De resultaten van het inhoudvalidatieproces weergeven in de **bewaking** werkruimte Vouw **distributiestatus**, en klikt u op de **inhoudsstatus** knooppunt. De inhoud van ieder pakkettype (bijvoorbeeld, toepassing, Software-updatepakket en installatiekopie) wordt weergegeven. Zie voor meer informatie over het controleren van inhoudstatussen [inhoud die u hebt gedistribueerd met System Center Configuration Manager controleren](../../../../core/servers/deploy/configure/monitor-content-you-have-distributed.md).  

